---
title: Volume-rendering
description: Volumetrische Images enthalten umfangreiche Informationen mit Deckkraft und Farbe in der gesamten das Volume, das einfach als Flächen ausgedrückt werden kann. Erfahren Sie, wie effizient volumetrische Bilder in Windows Mixed Reality gerendert.
author: KevinKennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: volumetrische Image "," Volume-Rendering "," Leistung "," mixed reality
ms.openlocfilehash: dc0e75b916ab7cc96be1eccb4ad32ac71f5b75ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596681"
---
# <a name="volume-rendering"></a>Volume-rendering

Medizinische MRI engineering Volumes, finden Sie unter [Volume Rendern auf Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering). Diese volumetrische Images enthalten umfangreiche Informationen mit Deckkraft und Farbe in der gesamten das Volume, das einfach als Oberflächen wie z. B. ausgedrückt werden kann [polygonalen Gitter](https://en.wikipedia.org/wiki/Polygon_mesh).

Wichtige Lösungen zur Verbesserung der Leistung
1. BAD: Naiver Ansatz: Zeigen Sie die gesamte Volume, in der Regel zu langsam ausgeführt wird
2. GUT: Cutting-Ebene: Anzeigen von nur einem einzelnen Slice des Volumes
3. GUT: Cutting untergeordnete Volume: Nur ein paar Ebenen des Volumes anzeigen
4. GUT: Verringern der Auflösung des Renderings Volume (siehe "Gemischten Auflösung Szenenrendering")

Es gibt nur eine bestimmte Menge an Informationen, die von der Anwendung auf dem Bildschirm in einen bestimmten Frame übertragen werden kann, dies ist die gesamte Speicherbandbreite. Verarbeitung (oder "Schattierung") erforderlich zum Transformieren von Daten für die Präsentation erfordert außerdem auch Zeit. Die wichtigsten Aspekte beim Rendering des Volumes werden als solche:
* Bildschirmbreite *-Bildschirmhöhe * Bildschirm zählen * Volume-Ebenen-auf-,-Pixel = gesamt-Volume-Beispiele-pro-Frame
* 1028 * 720 * 2 * 256 = 378961920 (100 %) (vollständige Res-Volume: zu viele Beispiele)
* 1028 * 720 * 2 * 1 = 1480320 (0,3 % voll) (thin-Slice: 1 Beispiel für eine pro Pixel, immer reibungslos ausgeführt wird)
* 1028 * 720 * 2 * 10 = 14803200 (3.9 % voll) (untergeordnete Volume Slice: 10 Stichproben pro Pixel, ziemlich immer reibungslos ausgeführt wird, sucht 3d)
* 200 * 200 * 2 * 256 = 20480000 (vollständige 5 %) (Res-Volume zu senken: weniger Pixel, vollständige Volumeverschlüsselung sieht 3d, jedoch ein wenig Blury)

## <a name="representing-3d-textures"></a>3D-Strukturen darstellt

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

## <a name="shading-and-gradients"></a>Schattierung und Farbverläufen

Wie Sie ein Volume, wie z. B. MRI, für die nützliche Visualisierung zu schattieren. Die primäre Methode ist, eine "Intensität Fenster" (min und Max), finden Sie unter Intensitäten innerhalb und in diesen Speicherplatz für die Schwarz oder weiß Intensität finden auf einfache Weise skaliert werden sollen. Einen Farbbalken kann als Textur, sodass verschiedene Teile des Spektrums Intensität schattierte Farben können klicken Sie dann auf die Werte innerhalb dieses Bereichs angewendet, und gespeichert werden:

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

In vielen unserer Anwendungen, die wir in unserer Volume speichern, sowohl eine unformatierte Intensitätswert als auch "Segmentierung Index" (wie z. B. Segmentieren von verschiedenen Teilen Skin und Knochenarbeit, diese Segmente werden in der Regel erstellt von Experten für dedizierte Tools). Dies kann mit dem Ansatz aus, um eine andere Farbe oder sogar von verschiedenen Farbbalken für jeden segmentindex zu platzieren, kombiniert werden:

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>Volume aufteilen in Slices in einem Shader

Ein wichtiger erster Schritt ist die Erstellung von einer "Aufteilen in Slices Ebene", die über das Volume verschieben können "Aufteilen in Slices es", und wie die Überprüfung an jedem Punkt Werte. Dies setzt voraus, dass eine 'VolumeSpace'-Cubes, die darstellt, in dem das Volume im Raum der Welt, die als Verweis verwendet werden kann ist, für die Platzierung der Punkte, vorhanden sind:

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a>Mengen an Ablaufverfolgungsdaten einschließen in Shader

Das Verwenden von GPUS Sie untergeordnete Mengen an Ablaufverfolgungsdaten einschließen, (führt einige Voxels deep dann Ebenen für die Daten aus Back in den Vordergrund):

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

## <a name="whole-volume-rendering"></a>Gesamte Volume-Rendering

Ändern den obigen Code untergeordnete Volume erhalten wir die folgenden Schritte ausführen:

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>Szenenrendering gemischten Auflösung

Wie Sie einen Teil der Szene mit niedriger Auflösung zu rendern, und fügen Sie sie wieder an Ort:
1. Einrichten von zwei Kameras außerhalb des Bildschirms, eine folgen jedes Auge, die alle Frames aktualisieren
2. Setup zwei mit niedriger Auflösung Renderziele (z. B. 200 x 200 einzelnen), dass die Kameras in Rendern
3. Richten Sie ein Quad, die vor dem Benutzer verschoben

Jeder Frame:
1. Zeichnet die Renderziele für jedes Auge mit niedriger Auflösung (Volumedaten, teure Shader usw.).
2. Zeichnen die Szene normalerweise als voller Auflösung (z. B. Gitter, UI usw..)
3. Zeichnen Sie ein Quad vor dem Benutzer, über der Szene und projizieren Sie die unterschiedlichen rendert auf, die.
4. Ergebnis: visual Kombination von voller Auflösung-Elementen mit niedriger Auflösung, aber mit hoher Dichte Mengen von Daten.
