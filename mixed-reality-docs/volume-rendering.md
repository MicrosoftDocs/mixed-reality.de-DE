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
# <a name="volume-rendering"></a><span data-ttu-id="4ef90-105">Volume-rendering</span><span class="sxs-lookup"><span data-stu-id="4ef90-105">Volume rendering</span></span>

<span data-ttu-id="4ef90-106">Medizinische MRI engineering Volumes, finden Sie unter [Volume Rendern auf Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering).</span><span class="sxs-lookup"><span data-stu-id="4ef90-106">For medical MRI or engineering volumes, see [Volume Rendering on Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering).</span></span> <span data-ttu-id="4ef90-107">Diese volumetrische Images enthalten umfangreiche Informationen mit Deckkraft und Farbe in der gesamten das Volume, das einfach als Oberflächen wie z. B. ausgedrückt werden kann [polygonalen Gitter](https://en.wikipedia.org/wiki/Polygon_mesh).</span><span class="sxs-lookup"><span data-stu-id="4ef90-107">These 'volumetric images' contain rich information with opacity and color throughout the volume that cannot be easily expressed as surfaces such as [polygonal meshes](https://en.wikipedia.org/wiki/Polygon_mesh).</span></span>

<span data-ttu-id="4ef90-108">Wichtige Lösungen zur Verbesserung der Leistung</span><span class="sxs-lookup"><span data-stu-id="4ef90-108">Key solutions to improve performance</span></span>
1. <span data-ttu-id="4ef90-109">BAD: Naiver Ansatz: Zeigen Sie die gesamte Volume, in der Regel zu langsam ausgeführt wird</span><span class="sxs-lookup"><span data-stu-id="4ef90-109">BAD: Naïve Approach: Show Whole Volume, generally runs too slowly</span></span>
2. <span data-ttu-id="4ef90-110">GUT: Cutting-Ebene: Anzeigen von nur einem einzelnen Slice des Volumes</span><span class="sxs-lookup"><span data-stu-id="4ef90-110">GOOD: Cutting Plane: Show only a single slice of the volume</span></span>
3. <span data-ttu-id="4ef90-111">GUT: Cutting untergeordnete Volume: Nur ein paar Ebenen des Volumes anzeigen</span><span class="sxs-lookup"><span data-stu-id="4ef90-111">GOOD: Cutting Sub-Volume: Show only a few layers of the volume</span></span>
4. <span data-ttu-id="4ef90-112">GUT: Verringern der Auflösung des Renderings Volume (siehe "Gemischten Auflösung Szenenrendering")</span><span class="sxs-lookup"><span data-stu-id="4ef90-112">GOOD: Lower the resolution of the volume rendering (see 'Mixed Resolution Scene Rendering')</span></span>

<span data-ttu-id="4ef90-113">Es gibt nur eine bestimmte Menge an Informationen, die von der Anwendung auf dem Bildschirm in einen bestimmten Frame übertragen werden kann, dies ist die gesamte Speicherbandbreite.</span><span class="sxs-lookup"><span data-stu-id="4ef90-113">There is only a certain amount of information that can be transferred from the application to the screen in any particular frame, this is the total memory bandwidth.</span></span> <span data-ttu-id="4ef90-114">Verarbeitung (oder "Schattierung") erforderlich zum Transformieren von Daten für die Präsentation erfordert außerdem auch Zeit.</span><span class="sxs-lookup"><span data-stu-id="4ef90-114">Also any processing (or 'shading') required to transform that data for presentation also requires time.</span></span> <span data-ttu-id="4ef90-115">Die wichtigsten Aspekte beim Rendering des Volumes werden als solche:</span><span class="sxs-lookup"><span data-stu-id="4ef90-115">The primary considerations when doing volume rendering are as such:</span></span>
* <span data-ttu-id="4ef90-116">Bildschirmbreite \*-Bildschirmhöhe \* Bildschirm zählen \* Volume-Ebenen-auf-,-Pixel = gesamt-Volume-Beispiele-pro-Frame</span><span class="sxs-lookup"><span data-stu-id="4ef90-116">Screen-Width \* Screen-Height \* Screen-Count \* Volume-Layers-On-That-Pixel = Total-Volume-Samples-Per-Frame</span></span>
* <span data-ttu-id="4ef90-117">1028 \* 720 \* 2 \* 256 = 378961920 (100 %) (vollständige Res-Volume: zu viele Beispiele)</span><span class="sxs-lookup"><span data-stu-id="4ef90-117">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (full res volume: too many samples)</span></span>
* <span data-ttu-id="4ef90-118">1028 \* 720 \* 2 \* 1 = 1480320 (0,3 % voll) (thin-Slice: 1 Beispiel für eine pro Pixel, immer reibungslos ausgeführt wird)</span><span class="sxs-lookup"><span data-stu-id="4ef90-118">1028 \* 720 \* 2 \* 1 = 1480320 (0.3% of full) (thin slice: 1 sample per pixel, runs smoothly)</span></span>
* <span data-ttu-id="4ef90-119">1028 \* 720 \* 2 \* 10 = 14803200 (3.9 % voll) (untergeordnete Volume Slice: 10 Stichproben pro Pixel, ziemlich immer reibungslos ausgeführt wird, sucht 3d)</span><span class="sxs-lookup"><span data-stu-id="4ef90-119">1028 \* 720 \* 2 \* 10 = 14803200 (3.9% of full) (sub-volume slice: 10 samples per pixel, runs fairly smoothly, looks 3d)</span></span>
* <span data-ttu-id="4ef90-120">200 \* 200 \* 2 \* 256 = 20480000 (vollständige 5 %) (Res-Volume zu senken: weniger Pixel, vollständige Volumeverschlüsselung sieht 3d, jedoch ein wenig Blury)</span><span class="sxs-lookup"><span data-stu-id="4ef90-120">200 \* 200 \* 2 \* 256 = 20480000 (5% of full) (lower res volume: fewer pixels, full volume, looks 3d but a bit blury)</span></span>

## <a name="representing-3d-textures"></a><span data-ttu-id="4ef90-121">3D-Strukturen darstellt</span><span class="sxs-lookup"><span data-stu-id="4ef90-121">Representing 3D Textures</span></span>

<span data-ttu-id="4ef90-122">Auf der CPU:</span><span class="sxs-lookup"><span data-stu-id="4ef90-122">On the CPU:</span></span>

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

<span data-ttu-id="4ef90-123">Auf der GPU:</span><span class="sxs-lookup"><span data-stu-id="4ef90-123">On the GPU:</span></span>

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

## <a name="shading-and-gradients"></a><span data-ttu-id="4ef90-124">Schattierung und Farbverläufen</span><span class="sxs-lookup"><span data-stu-id="4ef90-124">Shading and Gradients</span></span>

<span data-ttu-id="4ef90-125">Wie Sie ein Volume, wie z. B. MRI, für die nützliche Visualisierung zu schattieren.</span><span class="sxs-lookup"><span data-stu-id="4ef90-125">How to shade an volume, such as MRI, for useful visualization.</span></span> <span data-ttu-id="4ef90-126">Die primäre Methode ist, eine "Intensität Fenster" (min und Max), finden Sie unter Intensitäten innerhalb und in diesen Speicherplatz für die Schwarz oder weiß Intensität finden auf einfache Weise skaliert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="4ef90-126">The primary method is to have an 'intensity window' (a min and max) that you want to see intensities within, and simply scale into that space to see the black and white intensity.</span></span> <span data-ttu-id="4ef90-127">Einen Farbbalken kann als Textur, sodass verschiedene Teile des Spektrums Intensität schattierte Farben können klicken Sie dann auf die Werte innerhalb dieses Bereichs angewendet, und gespeichert werden:</span><span class="sxs-lookup"><span data-stu-id="4ef90-127">A 'color ramp' can then be applied to the values within that range, and stored as a texture, so that different parts of the intensity spectrum can be shaded different colors:</span></span>

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

<span data-ttu-id="4ef90-128">In vielen unserer Anwendungen, die wir in unserer Volume speichern, sowohl eine unformatierte Intensitätswert als auch "Segmentierung Index" (wie z. B. Segmentieren von verschiedenen Teilen Skin und Knochenarbeit, diese Segmente werden in der Regel erstellt von Experten für dedizierte Tools).</span><span class="sxs-lookup"><span data-stu-id="4ef90-128">In many our applications we store in our volume both a raw intensity value and a 'segmentation index' (to segment different parts such as skin and bone, these segments are generally created by experts in dedicated tools).</span></span> <span data-ttu-id="4ef90-129">Dies kann mit dem Ansatz aus, um eine andere Farbe oder sogar von verschiedenen Farbbalken für jeden segmentindex zu platzieren, kombiniert werden:</span><span class="sxs-lookup"><span data-stu-id="4ef90-129">This can be combined with the approach above to put a different color, or even different color ramp for each segment index:</span></span>

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a><span data-ttu-id="4ef90-130">Volume aufteilen in Slices in einem Shader</span><span class="sxs-lookup"><span data-stu-id="4ef90-130">Volume Slicing in a Shader</span></span>

<span data-ttu-id="4ef90-131">Ein wichtiger erster Schritt ist die Erstellung von einer "Aufteilen in Slices Ebene", die über das Volume verschieben können "Aufteilen in Slices es", und wie die Überprüfung an jedem Punkt Werte.</span><span class="sxs-lookup"><span data-stu-id="4ef90-131">A great first step is to create a "slicing plane" that can move through the volume, 'slicing it', and how the scan values at each point.</span></span> <span data-ttu-id="4ef90-132">Dies setzt voraus, dass eine 'VolumeSpace'-Cubes, die darstellt, in dem das Volume im Raum der Welt, die als Verweis verwendet werden kann ist, für die Platzierung der Punkte, vorhanden sind:</span><span class="sxs-lookup"><span data-stu-id="4ef90-132">This assumes that there is a 'VolumeSpace' cube, which represents where the volume is in world space, that can be used as a reference for placing the points:</span></span>

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a><span data-ttu-id="4ef90-133">Mengen an Ablaufverfolgungsdaten einschließen in Shader</span><span class="sxs-lookup"><span data-stu-id="4ef90-133">Volume Tracing in Shaders</span></span>

<span data-ttu-id="4ef90-134">Das Verwenden von GPUS Sie untergeordnete Mengen an Ablaufverfolgungsdaten einschließen, (führt einige Voxels deep dann Ebenen für die Daten aus Back in den Vordergrund):</span><span class="sxs-lookup"><span data-stu-id="4ef90-134">How to use the GPU to do sub-volume tracing (walks a few voxels deep then layers on the data from back to front):</span></span>

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

## <a name="whole-volume-rendering"></a><span data-ttu-id="4ef90-135">Gesamte Volume-Rendering</span><span class="sxs-lookup"><span data-stu-id="4ef90-135">Whole Volume Rendering</span></span>

<span data-ttu-id="4ef90-136">Ändern den obigen Code untergeordnete Volume erhalten wir die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="4ef90-136">Modifying the sub-volume code above we get:</span></span>

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a><span data-ttu-id="4ef90-137">Szenenrendering gemischten Auflösung</span><span class="sxs-lookup"><span data-stu-id="4ef90-137">Mixed Resolution Scene Rendering</span></span>

<span data-ttu-id="4ef90-138">Wie Sie einen Teil der Szene mit niedriger Auflösung zu rendern, und fügen Sie sie wieder an Ort:</span><span class="sxs-lookup"><span data-stu-id="4ef90-138">How to render a part of the scene with a low resolution and put it back in place:</span></span>
1. <span data-ttu-id="4ef90-139">Einrichten von zwei Kameras außerhalb des Bildschirms, eine folgen jedes Auge, die alle Frames aktualisieren</span><span class="sxs-lookup"><span data-stu-id="4ef90-139">Setup two off-screen cameras, one to follow each eye that update each frame</span></span>
2. <span data-ttu-id="4ef90-140">Setup zwei mit niedriger Auflösung Renderziele (z. B. 200 x 200 einzelnen), dass die Kameras in Rendern</span><span class="sxs-lookup"><span data-stu-id="4ef90-140">Setup two low-resolution render targets (say 200x200 each), that the cameras render into</span></span>
3. <span data-ttu-id="4ef90-141">Richten Sie ein Quad, die vor dem Benutzer verschoben</span><span class="sxs-lookup"><span data-stu-id="4ef90-141">Setup a quad that moves in front of the user</span></span>

<span data-ttu-id="4ef90-142">Jeder Frame:</span><span class="sxs-lookup"><span data-stu-id="4ef90-142">Each Frame:</span></span>
1. <span data-ttu-id="4ef90-143">Zeichnet die Renderziele für jedes Auge mit niedriger Auflösung (Volumedaten, teure Shader usw.).</span><span class="sxs-lookup"><span data-stu-id="4ef90-143">Draw the render targets for each eye at low-resolution (volume data, expensive shaders, etc.)</span></span>
2. <span data-ttu-id="4ef90-144">Zeichnen die Szene normalerweise als voller Auflösung (z. B. Gitter, UI usw..)</span><span class="sxs-lookup"><span data-stu-id="4ef90-144">Draw the scene normally as full resolution (meshes, UI, etc.)</span></span>
3. <span data-ttu-id="4ef90-145">Zeichnen Sie ein Quad vor dem Benutzer, über der Szene und projizieren Sie die unterschiedlichen rendert auf, die.</span><span class="sxs-lookup"><span data-stu-id="4ef90-145">Draw a quad in front of the user, over the scene, and project the low-res renders onto that.</span></span>
4. <span data-ttu-id="4ef90-146">Ergebnis: visual Kombination von voller Auflösung-Elementen mit niedriger Auflösung, aber mit hoher Dichte Mengen von Daten.</span><span class="sxs-lookup"><span data-stu-id="4ef90-146">Result: visual combination of full-resolution elements with low-resolution but high-density volume data.</span></span>
