---
title: Volumerendering
description: Volumetric-Bilder enthalten umfangreiche Informationen mit Deckkraft und Farben im gesamten Volume, die nicht einfach als Oberflächen ausgedrückt werden können. Erfahren Sie, wie Sie Volumetrische-Images effizient in Windows Mixed Reality Renderings.
author: kevinkennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: volumetribild, volumenrendering, Leistung, gemischte Realität
ms.openlocfilehash: 6dbb49c31761d4b7b9da5060d15763c3925be754
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277948"
---
# <a name="volume-rendering"></a>Volumerendering

Informationen zu medizinischen MRT-oder Engineering-Volumes finden Sie unter [Volume Rendering auf Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering). Diese "Volumetric Images" enthalten umfangreiche Informationen mit Deckkraft und farbiger Farbe im gesamten Volume, das nicht einfach als Oberflächen, wie z. b. [polygonale Netze](https://en.wikipedia.org/wiki/Polygon_mesh), ausgedrückt werden kann.

Wichtige Lösungen zum Verbessern der Leistung
1. Schlecht: naive Vorgehensweise: gesamtes Volume anzeigen, wird in der Regel zu langsam ausgeführt.
2. Gut: ausschnittsebene: nur ein einzelnes Slice des Volumes anzeigen
3. Gut: das untergeordnete Volume wird abgeschnitten: Es werden nur wenige Ebenen des Volumes angezeigt.
4. Gut: Verringern der Auflösung des volumerendering (siehe ' Mixed Resolution Scene Rendering ')

Es gibt nur eine bestimmte Menge von Informationen, die von der Anwendung auf den Bildschirm in einem bestimmten Frame übertragen werden können. Dies ist die gesamte Arbeitsspeicher Bandbreite. Außerdem erfordert jede Verarbeitung (oder ' Schattierung '), die zum Transformieren der Daten für die Präsentation erforderlich ist, Zeit. Die wichtigsten Überlegungen zum Rendern von Volumes lauten wie folgt:
* Bildschirmbreite * Bildschirmhöhe * Bildschirm-count * Volume-Layer-on-this-Pixel = Total-Volume-Samples-per Frame
* 1028 * 720 * 2 * 256 = 378961920 (100%) (vollständiges res-Volume: zu viele Beispiele)
* 1028 * 720 * 2 * 1 = 1480320 (0,3% vollständig) (dünner Slice: 1 Stichprobe pro Pixel, reibungsloses ausführen)
* 1028 * 720 * 2 * 10 = 14803200 (3,9% vollständig) (unter volumeslice: 10 Stichproben pro Pixel, läuft Recht reibungslos, sieht 3D aus)
* 200 * 200 * 2 * 256 = 20480000 (5% vollständig) (niedrigeres Volume: weniger Pixel, vollständiges Volume, sieht 3D-, aber etwas verschwommen)

## <a name="representing-3d-textures"></a>Darstellen von 3D-Texturen

Auf der CPU:

```
public struct Int3 { public int X, Y, Z; /* ... */ }
 public class VolumeHeader  {
   public readonly Int3 Size;
   public VolumeHeader(Int3 size) { this.Size = size;  }
   public int CubicToLinearIndex(Int3 index) {
     return index.X + (index.Y * (Size.X)) + (index.Z * (Size.X * Size.Y));
   }
   public Int3 LinearToCubicIndex(int linearIndex)
   {
     return new Int3((linearIndex / 1) % Size.X,
       (linearIndex / Size.X) % Size.Y,
       (linearIndex / (Size.X * Size.Y)) % Size.Z);
   }
   /* ... */
 }
 public class VolumeBuffer<T> {
   public readonly VolumeHeader Header;
   public readonly T[] DataArray;
   public T GetVoxel(Int3 pos)        {
     return this.DataArray[this.Header.CubicToLinearIndex(pos)];
   }
   public void SetVoxel(Int3 pos, T val)        {
     this.DataArray[this.Header.CubicToLinearIndex(pos)] = val;
   }
   public T this[Int3 pos] {
     get { return this.GetVoxel(pos); }
     set { this.SetVoxel(pos, value); }
   }
   /* ... */
 }
```

Auf der GPU:

```
float3 _VolBufferSize;
 int3 UnitVolumeToIntVolume(float3 coord) {
   return (int3)( coord * _VolBufferSize.xyz );
 }
 int IntVolumeToLinearIndex(int3 coord, int3 size) {
   return coord.x + ( coord.y * size.x ) + ( coord.z * ( size.x * size.y ) );
 }
 uniform StructuredBuffer<float> _VolBuffer;
 float SampleVol(float3 coord3 ) {
   int3 intIndex3 = UnitVolumeToIntVolume( coord3 );
   int index1D = IntVolumeToLinearIndex( intIndex3, _VolBufferSize.xyz);
   return __VolBuffer[index1D];
 }
```

## <a name="shading-and-gradients"></a>Schattierung und Farbverläufe

Vorgehensweise beim schattieren eines Volumes (z. b. von MRT) für eine sinnvolle Visualisierung. Die primäre Methode besteht darin, ein "Intensitäts Fenster" (min und max) zu haben, in dem Sie die Intensität anzeigen möchten, und einfach in diesen Bereich zu skalieren, um die schwarze und weiße Intensität anzuzeigen. Eine ' Color-Ramp ' kann dann auf die Werte in diesem Bereich angewendet und als Textur gespeichert werden, sodass verschiedene Teile des Intensität-Spektrums unterschiedliche Farben schattiert werden können:

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

In vielen unserer Anwendungen speichern wir unsere Volumes sowohl als rohintensität als auch als Segmentierungs Index (zum Segmentieren verschiedener Teile wie Skin und Bone). diese Segmente werden im Allgemeinen von Experten in dedizierten Tools erstellt. Dies kann mit dem oben beschriebenen Ansatz kombiniert werden, um eine andere Farbe oder sogar eine andere Farbskala für jeden Segment Index zu platzieren:

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>Volumeslicing in einem Shader

Ein hervorragend erster Schritt besteht darin, eine "Slicing Plane" zu erstellen, die sich durch das Volume bewegen kann, "Slicing" und die Überprüfungs Werte an jedem Punkt. Dabei wird davon ausgegangen, dass es einen "volumespace"-Cube gibt, der den Speicherort des Volumes im Raum der Welt darstellt, der als Verweis zum Platzieren der Punkte verwendet werden kann:

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a>Volumeablauf Verfolgung in Shadern

Gewusst wie: Verwenden der GPU zum Durchführen einer unter Laufband-Ablauf Verfolgung (durchläuft einige einige Voxels tief, dann Ebenen der Daten von hinten nach vorne):

```
float4 AlphaBlend(float4 dst, float4 src) {
   float4 res = (src * src.a) + (dst - dst * src.a);
   res.a = src.a + (dst.a - dst.a*src.a);
   return res;
 }
 float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 0.15; // depth in volume space, customize!!!
   float numLoops = 10; // can be 400 on nice PC
   float4 curColor = float4(0, 0, 0, 0);
   // Figure out front and back volume coords to walk through:
   float3 frontCoord = objPosStart;
   float3 backCoord = frontPos + (normalize(cameraPosVolSpace - objPosStart) * maxDepth);
   float3 stepCoord = (frontCoord - backCoord) / numLoops;
   float3 curCoord = backCoord;
   // Add per-pixel random offset, avoids layer aliasing:
   curCoord += stepCoord * RandomFromPositionFast(objPosStart);
   // Walk from back to front (to make front appear in-front of back):
   for (float i = 0; i < numLoops; i++) {
     float intensity = SampleVol(curCoord);
     float4 shaded = ShadeVol(intensity);
     curColor = AlphaBlend(curColor, shaded);
     curCoord += stepCoord;
   }
   return curColor;
 }
```

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos.xyz, 1));
 float4 cameraInVolSpace = mul(_WorldToVolume, float4(_WorldSpaceCameraPos.xyz, 1));
```

```
// In the pixel shader:
 float4 color = volTraceSubVolume( volSpace, cameraInVolSpace );
```

## <a name="whole-volume-rendering"></a>Gesamtes volumenrendering

Wenn Sie den obigen Code des untergeordneten Volumes ändern, erhalten wir Folgendes:

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>Rendern von gemischten Auflösungs Szenen

Gewusst wie: Rendering eines Teils der Szene mit niedriger Auflösung und Zurücksetzen der Szene:
1. Richten Sie zwei Off-Screen-Kameras ein, um jedes Auge zu verfolgen, das jeden Frame aktualisiert.
2. Einrichten von zwei Renderingzielen mit niedriger Auflösung (d. h. 200 x 200), die von den Kameras dargestellt werden
3. Einrichten eines Quad, das sich vor dem Benutzer bewegt

Jeder Frame:
1. Zeichnen Sie die Renderziele für jedes Auge bei niedriger Auflösung (Volumedaten, teure Shaders usw.).
2. Zeichnen Sie die Szene normal als vollständige Auflösung (Meshes, UI usw.).
3. Zeichnen Sie einen Quad vor dem Benutzer, über die Szene, und projizieren Sie die auf diese
4. Ergebnis: visuelle Kombination von Elementen mit vollständiger Auflösung mit geringer Auflösung, aber Volumedaten mit hoher Dichte
