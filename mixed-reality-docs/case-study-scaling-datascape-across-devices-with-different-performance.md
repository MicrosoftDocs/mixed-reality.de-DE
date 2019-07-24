---
title: 'Fallstudie: Skalieren von DataSet auf Geräten mit unterschiedlicher Leistung'
description: Diese Fallstudie bietet Einblicke in die Art und Weise, wie Microsoft-Entwickler die datascape-App optimiert haben, um eine überzeugende Geräte übergreifende Darstellung mit einer Reihe von Leistungs Funktionen zu bieten
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: immersives Headset, Leistungsoptimierung, VR, Fallstudie
ms.openlocfilehash: 990a5ee6de07b6416e3150a7885220409a9c8d93
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63523390"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a><span data-ttu-id="b65dc-104">Fallstudie: Skalieren von DataSet auf Geräten mit unterschiedlicher Leistung</span><span class="sxs-lookup"><span data-stu-id="b65dc-104">Case study - Scaling Datascape across devices with different performance</span></span>

<span data-ttu-id="b65dc-105">Datascape ist eine Windows Mixed Reality-Anwendung, die intern bei Microsoft entwickelt wurde, wobei wir uns auf das Anzeigen von Wetterdaten oberhalb von Geländedaten konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="b65dc-105">Datascape is a Windows Mixed Reality application developed internally at Microsoft where we focused on displaying weather data on top of terrain data.</span></span> <span data-ttu-id="b65dc-106">Die Anwendung untersucht die eindeutigen Einblicke, die Benutzer bei der Ermittlung von Daten in gemischter Realität gewinnen, indem Sie den Benutzer mit Holographic Data-Visualisierung umgeben.</span><span class="sxs-lookup"><span data-stu-id="b65dc-106">The application explores the unique insights users gain from discovering data in mixed reality by surrounding the user with holographic data visualization.</span></span>

<span data-ttu-id="b65dc-107">Für das DataSet wollten wir eine Vielzahl von Plattformen mit unterschiedlichen Hardwarefunktionen als Ziel für Microsoft hololens und Windows Mixed Reality-immersive Headsets und von Geräten mit niedrigerer Leistung auf die neuesten PCs mit High-End-GPU ausrichten.</span><span class="sxs-lookup"><span data-stu-id="b65dc-107">For Datascape we wanted to target a variety of platforms with different hardware capabilities ranging from Microsoft HoloLens to Windows Mixed Reality immersive headsets, and from lower-powered PCs to the very latest PCs with high-end GPU.</span></span> <span data-ttu-id="b65dc-108">Die Hauptaufgabe war das Rendern unserer Szene in einem visuell ansprechenden Bereich auf Geräten mit stark unterschiedlichen Grafikfunktionen bei der Ausführung bei einer hohen Framerate.</span><span class="sxs-lookup"><span data-stu-id="b65dc-108">The main challenge was rendering our scene in a visually appealing matter on devices with wildly different graphics capabilities while executing at a high framerate.</span></span>

<span data-ttu-id="b65dc-109">Diese Fallstudie führt Sie durch den Prozess und die Verfahren, die zum Erstellen einiger unserer GPU-intensiveren Systeme verwendet werden, und beschreibt die Probleme, die wir kennengelernt haben und wie wir Sie überwunden haben.</span><span class="sxs-lookup"><span data-stu-id="b65dc-109">This case study will walk through the process and techniques used to create some of our more GPU-intensive systems, describing the problems we encountered and how we overcame them.</span></span>

## <a name="transparency-and-overdraw"></a><span data-ttu-id="b65dc-110">Transparenz und Überzeichnung</span><span class="sxs-lookup"><span data-stu-id="b65dc-110">Transparency and overdraw</span></span>

<span data-ttu-id="b65dc-111">Die wichtigsten Renderingerweiterungen, die Transparenz behandeln, da Transparenz für eine GPU aufwendig sein kann.</span><span class="sxs-lookup"><span data-stu-id="b65dc-111">Our main rendering struggles dealt with transparency, since transparency can be expensive on a GPU.</span></span>

<span data-ttu-id="b65dc-112">Eine solide Geometrie kann beim Schreiben in den tiefen Puffer in den Vordergrund gerendert werden. Dadurch wird verhindert, dass alle zukünftigen Pixel hinter diesem Pixel verworfen werden.</span><span class="sxs-lookup"><span data-stu-id="b65dc-112">Solid geometry can be rendered front to back while writing to the depth buffer, stopping any future pixels located behind that pixel from being discarded.</span></span> <span data-ttu-id="b65dc-113">Dadurch wird verhindert, dass versteckte Pixel den Pixelshader ausführen, wodurch der Prozess erheblich beschleunigt wird.</span><span class="sxs-lookup"><span data-stu-id="b65dc-113">This prevents hidden pixels from executing the pixel shader, speeding up the process significantly.</span></span> <span data-ttu-id="b65dc-114">Wenn Geometrie optimal sortiert ist, wird jedes Pixel auf dem Bildschirm nur einmal gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="b65dc-114">If geometry is sorted optimally, each pixel on the screen will be drawn only once.</span></span>

<span data-ttu-id="b65dc-115">Die transparente Geometrie muss wieder in den Vordergrund sortiert werden und basiert darauf, dass die Ausgabe des Pixelshaders mit dem aktuellen Pixel auf dem Bildschirm gemischt wird.</span><span class="sxs-lookup"><span data-stu-id="b65dc-115">Transparent geometry needs to be sorted back to front and relies on blending the output of the pixel shader to the current pixel on the screen.</span></span> <span data-ttu-id="b65dc-116">Dies kann dazu führen, dass jedes Pixel auf dem Bildschirm mehrmals pro Frame gezeichnet wird, was als overdraw bezeichnet wird.</span><span class="sxs-lookup"><span data-stu-id="b65dc-116">This can result in each pixel on the screen being drawn to multiple times per frame, referred to as overdraw.</span></span>

<span data-ttu-id="b65dc-117">Bei hololens und gängigen PCs kann der Bildschirm nur wenige Male aufgefüllt werden, sodass das transparente Rendering problematisch ist.</span><span class="sxs-lookup"><span data-stu-id="b65dc-117">For HoloLens and mainstream PCs, the screen can only be filled a handful of times, making transparent rendering problematic.</span></span>

## <a name="introduction-to-datascape-scene-components"></a><span data-ttu-id="b65dc-118">Einführung in datascape Scene-Komponenten</span><span class="sxs-lookup"><span data-stu-id="b65dc-118">Introduction to Datascape scene components</span></span>

<span data-ttu-id="b65dc-119">Wir hatten drei Hauptkomponenten in unserer Szene. **die Benutzeroberfläche, die Karte**und **das Wetter**.</span><span class="sxs-lookup"><span data-stu-id="b65dc-119">We had three major components to our scene; **the UI, the map**, and **the weather**.</span></span> <span data-ttu-id="b65dc-120">Wir wussten schon früh, dass unsere Wettereffekte die gesamte GPU-Zeit in Anspruch nehmen würden, daher haben wir die Benutzeroberfläche und das Gelände auf eine Weise entworfen, die alle über schreibungen verringern würde.</span><span class="sxs-lookup"><span data-stu-id="b65dc-120">We knew early on that our weather effects would require all the GPU time it could get, so we purposely designed the UI and terrain in a way that would reduce any overdraw.</span></span>

<span data-ttu-id="b65dc-121">Wir haben die Benutzeroberfläche mehrmals überarbeitet, um die Menge der zu erstellenden über schreibungen zu minimieren.</span><span class="sxs-lookup"><span data-stu-id="b65dc-121">We reworked the UI several times to minimize the amount of overdraw it would produce.</span></span> <span data-ttu-id="b65dc-122">Wir haben auf der Seite komplexer Geometrie gerendet, anstatt transparente Grafiken für Komponenten wie leuchtende Schaltflächen und Karten Übersichten zu überlagern.</span><span class="sxs-lookup"><span data-stu-id="b65dc-122">We erred on the side of more complex geometry rather than overlaying transparent art on top of each other for components like glowing buttons and map overviews.</span></span>

<span data-ttu-id="b65dc-123">Für die Karte haben wir einen benutzerdefinierten Shader verwendet, der standardmäßige Unity-Features, wie z. b. Schatten und komplexe Beleuchtung, entfernt und Sie durch ein einfaches Modell mit einem Sun-Licht und eine benutzerdefinierte Nebel Berechnung ersetzt.</span><span class="sxs-lookup"><span data-stu-id="b65dc-123">For the map, we used a custom shader that would strip out standard Unity features such as shadows and complex lighting, replacing them with a simple single sun lighting model and a custom fog calculation.</span></span> <span data-ttu-id="b65dc-124">Dies führte zu einem einfachen Pixelshader und freigab GPU-Zyklen.</span><span class="sxs-lookup"><span data-stu-id="b65dc-124">This produced a simple pixel shader and free up GPU cycles.</span></span>

<span data-ttu-id="b65dc-125">Wir haben die Benutzeroberfläche und die Zuordnung zum Rendering im Budget erhalten, in dem wir abhängig von der Hardware keine Änderungen vorgenommen haben. Allerdings erwies sich die Wetter Visualisierung, insbesondere das cloudrendering, als eine größere Herausforderung.</span><span class="sxs-lookup"><span data-stu-id="b65dc-125">We managed to get both the UI and the map to rendering at budget where we did not need any changes to them depending on the hardware; however, the weather visualization, in particular the cloud rendering, proved to be more of a challenge!</span></span>

## <a name="background-on-cloud-data"></a><span data-ttu-id="b65dc-126">Hintergrundinformationen zu clouddaten</span><span class="sxs-lookup"><span data-stu-id="b65dc-126">Background on cloud data</span></span>

<span data-ttu-id="b65dc-127">Unsere clouddaten wurden von NOAA-Servern herunter http://nomads.ncep.noaa.gov/) geladen (und standen in drei unterschiedlichen 2D-Schichten, jeweils mit der oberen und unteren Höhe der Cloud, sowie der Dichte der Cloud für jede Zelle des Rasters.</span><span class="sxs-lookup"><span data-stu-id="b65dc-127">Our cloud data was downloaded from NOAA servers (http://nomads.ncep.noaa.gov/) and came to us in three distinct 2D layers, each with the top and bottom height of the cloud, as well as the density of the cloud for each cell of the grid.</span></span> <span data-ttu-id="b65dc-128">Die Daten wurden in eine Cloud-Informations Textur verarbeitet, in der jede Komponente in der roten, grünen und blauen Komponente der Textur gespeichert wurde, um den Zugriff auf die GPU zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="b65dc-128">The data got processed into a cloud info texture where each component was stored in the red, green, and blue component of the texture for easy access on the GPU.</span></span>

## <a name="geometry-clouds"></a><span data-ttu-id="b65dc-129">Geometry-Clouds</span><span class="sxs-lookup"><span data-stu-id="b65dc-129">Geometry clouds</span></span>

<span data-ttu-id="b65dc-130">Um sicherzustellen, dass unsere unterstützen Computer unsere Clouds wirklich Rendering haben, haben wir uns entschieden, mit einem Ansatz zu beginnen, der eine solide Geometrie zum Minimieren von über schreibungen verwenden würde.</span><span class="sxs-lookup"><span data-stu-id="b65dc-130">To make sure our lower-powered machines could render our clouds we decided to start with an approach that would use solid geometry to minimize overdraw.</span></span>

<span data-ttu-id="b65dc-131">Wir haben zunächst versucht, Clouds zu erzeugen, indem wir für jede Ebene ein solides Heightmap-Mesh generiert haben. dabei wird der Radius der cloudinfotextur pro Scheitelpunkt verwendet, um die Form zu generieren</span><span class="sxs-lookup"><span data-stu-id="b65dc-131">We first tried producing clouds by generating a solid heightmap mesh for each layer using the radius of the cloud info texture per vertex to generate the shape.</span></span> <span data-ttu-id="b65dc-132">Wir haben einen Geometry-Shader verwendet, um die Scheitel Punkte im oberen und unteren Bereich der Cloud zu erzeugen, die solide cloudformen erzeugen.</span><span class="sxs-lookup"><span data-stu-id="b65dc-132">We used a geometry shader to produce the vertices both at the top and the bottom of the cloud generating solid cloud shapes.</span></span> <span data-ttu-id="b65dc-133">Wir haben den Dichtewert aus der Textur verwendet, um die Cloud mit dunkleren Farben für dischere Clouds zu versehen.</span><span class="sxs-lookup"><span data-stu-id="b65dc-133">We used the density value from the texture to color the cloud with darker colors for more dense clouds.</span></span>

<span data-ttu-id="b65dc-134">**Shader zum Erstellen der Vertices:**</span><span class="sxs-lookup"><span data-stu-id="b65dc-134">**Shader for creating the vertices:**</span></span>

```
v2g vert (appdata v)
{
    v2g o;
    o.height = tex2Dlod(_MainTex, float4(v.uv, 0, 0)).x;
    o.vertex = v.vertex;
    return o;
}
 
g2f GetOutput(v2g input, float heightDirection)
{
    g2f ret;
    float4 newBaseVert = input.vertex;
    newBaseVert.y += input.height * heightDirection * _HeigthScale;
    ret.vertex = UnityObjectToClipPos(newBaseVert);
    ret.height = input.height;
    return ret;
}
 
[maxvertexcount(6)]
void geo(triangle v2g p[3], inout TriangleStream<g2f> triStream)
{
    float heightTotal = p[0].height + p[1].height + p[2].height;
    if (heightTotal > 0)
    {
        triStream.Append(GetOutput(p[0], 1));
        triStream.Append(GetOutput(p[1], 1));
        triStream.Append(GetOutput(p[2], 1));
 
        triStream.RestartStrip();
 
        triStream.Append(GetOutput(p[2], -1));
        triStream.Append(GetOutput(p[1], -1));
        triStream.Append(GetOutput(p[0], -1));
    }
}
fixed4 frag (g2f i) : SV_Target
{
    clip(i.height - 0.1f);
 
    float3 finalColor = lerp(_LowColor, _HighColor, i.height);
    return float4(finalColor, 1);
}
```

<span data-ttu-id="b65dc-135">Wir haben ein kleines Rauschmuster eingeführt, um weitere Details zu den echten Daten zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="b65dc-135">We introduced a small noise pattern to get more detail on top of the real data.</span></span> <span data-ttu-id="b65dc-136">Um Round-Cloud-Ränder zu erzeugen, haben wir die Pixel im Pixelshader abgeschnitten, wenn der interpoliert RADIUS-Wert einen Schwellenwert erreicht hat, um fast null-Werte zu verwerfen.</span><span class="sxs-lookup"><span data-stu-id="b65dc-136">To produce round cloud edges, we clipped the pixels in the pixel shader when the interpolated radius value hit a threshold to discard near-zero values.</span></span>

![Geometry-Clouds](images/datascape-geometry-clouds-700px.jpg)

<span data-ttu-id="b65dc-138">Da es sich bei den Clouds um eine solide Geometrie handelt, können Sie vor dem-Gelände gerendert werden, um alle teuren Karten Pixel auszublenden, um die Framerate weiter zu</span><span class="sxs-lookup"><span data-stu-id="b65dc-138">Since the clouds are solid geometry, they can be rendered before the terrain to hide any expensive map pixels underneath to further improve framerate.</span></span> <span data-ttu-id="b65dc-139">Diese Lösung wurde auf allen Grafikkarten von min-spec bis High-End-Grafikkarten sowie auf hololens aufgrund des Solid Geometry-renderingansatzes ordnungsgemäß ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="b65dc-139">This solution ran well on all graphics cards from min-spec to high-end graphics cards, as well as on HoloLens, because of the solid geometry rendering approach.</span></span>

## <a name="solid-particle-clouds"></a><span data-ttu-id="b65dc-140">Solid-Partikel-Clouds</span><span class="sxs-lookup"><span data-stu-id="b65dc-140">Solid particle clouds</span></span>

<span data-ttu-id="b65dc-141">Wir verfügten nun über eine Sicherungs Lösung, die eine angemessene Darstellung unserer clouddaten erzeugt hat, war aber ein bisschen einfach im "Wow"-Faktor und hat das volummetric-Gefühl nicht vermittelt, das wir für unsere High-End-Computer wollten.</span><span class="sxs-lookup"><span data-stu-id="b65dc-141">We now had a backup solution that produced a decent representation of our cloud data, but was a bit lackluster in the “wow” factor and did not convey the volumetric feel that we wanted for our high-end machines.</span></span>

<span data-ttu-id="b65dc-142">Der nächste Schritt besteht darin, die Clouds zu erstellen, indem Sie Sie mit ungefähr 100.000 Partikeln darstellen, um ein mehr organisches und volummetrisches aussehen zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="b65dc-142">Our next step was creating the clouds by representing them with approximately 100,000 particles to produce a more organic and volumetric look.</span></span>

<span data-ttu-id="b65dc-143">Wenn Partikel solide bleiben und vor-zu-hinten sortiert werden, können wir weiterhin von der tiefen Puffer Erstellung der Pixel hinter zuvor gerenderten Partikeln profitieren, wodurch die Überzeichnung reduziert wird.</span><span class="sxs-lookup"><span data-stu-id="b65dc-143">If particles stay solid and sort front-to-back, we can still benefit from depth buffer culling of the pixels behind previously rendered particles, reducing the overdraw.</span></span> <span data-ttu-id="b65dc-144">Mit einer Partikel basierten Lösung können wir auch die Menge der Partikel ändern, die für die unterschiedliche Hardware verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b65dc-144">Also, with a particle-based solution, we can alter the amount of particles used to target different hardware.</span></span> <span data-ttu-id="b65dc-145">Allerdings müssen alle Pixel noch tiefer getestet werden, was zu einem zusätzlichen Aufwand führt.</span><span class="sxs-lookup"><span data-stu-id="b65dc-145">However, all pixels still need to be depth tested, which results in some additional overhead.</span></span>

<span data-ttu-id="b65dc-146">Zuerst haben wir die Partikel Positionen um den Mittelpunkt der Umgebung beim Start erstellt.</span><span class="sxs-lookup"><span data-stu-id="b65dc-146">First, we created particle positions around the center point of the experience at startup.</span></span> <span data-ttu-id="b65dc-147">Wir haben die Partikel um das Zentrum und weniger in der Entfernung verteilt.</span><span class="sxs-lookup"><span data-stu-id="b65dc-147">We distributed the particles more densely around the center and less so in the distance.</span></span> <span data-ttu-id="b65dc-148">Wir haben alle Partikel von der Mitte nach hinten sortiert, sodass die nächstgelegenen Partikel zuerst dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="b65dc-148">We pre-sorted all particles from the center to the back so that the closest particles would render first.</span></span>

<span data-ttu-id="b65dc-149">Ein Compute-Shader gibt eine Stichprobe der cloudinfotextur aus, um die einzelnen Partikel auf der Grundlage der Dichte an der richtigen Höhe zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="b65dc-149">A compute shader would sample the cloud info texture to position each particle at a correct height and color it based on the density.</span></span>

<span data-ttu-id="b65dc-150">Wir haben *drawprozeduren* verwendet, um ein Quad pro Partikel zu erzeugen, sodass die Partikel Daten jederzeit auf der GPU bleiben können.</span><span class="sxs-lookup"><span data-stu-id="b65dc-150">We used *DrawProcedural* to render a quad per particle allowing the particle data to stay on the GPU at all times.</span></span>

<span data-ttu-id="b65dc-151">Jedes Partikel enthielt sowohl eine Höhe als auch einen RADIUS.</span><span class="sxs-lookup"><span data-stu-id="b65dc-151">Each particle contained both a height and a radius.</span></span> <span data-ttu-id="b65dc-152">Die Höhe basiert auf den clouddaten, die aus der Cloud-Informations Textur entnommen wurden, und der RADIUS basiert auf der anfänglichen Verteilung, in der er so berechnet würde, dass er den horizontalen Abstand zum nächstgelegenen Nachbarn speichert.</span><span class="sxs-lookup"><span data-stu-id="b65dc-152">The height was based on the cloud data sampled from the cloud info texture, and the radius was based on the initial distribution where it would be calculated to store the horizontal distance to its closest neighbor.</span></span> <span data-ttu-id="b65dc-153">Die Quads würden diese Daten verwenden, um sich selbst durch die Höhe zu orientieren, sodass die Höhe, wenn Benutzer sich horizontal ansehen, angezeigt wird, und wenn sich die Benutzer von oben nach unten ansehen, wird der Bereich zwischen den Nachbarn abgedeckt.</span><span class="sxs-lookup"><span data-stu-id="b65dc-153">The quads would use this data to orient itself angled by the height so that when users look at it horizontally, the height would be shown, and when users looked at it top-down, the area between its neighbors would be covered.</span></span>

![Partikelform](images/particle-shape-700px.png)

<span data-ttu-id="b65dc-155">**Shader-Code, der die Verteilung anzeigt:**</span><span class="sxs-lookup"><span data-stu-id="b65dc-155">**Shader code showing the distribution:**</span></span>

```
ComputeBuffer cloudPointBuffer = new ComputeBuffer(6, quadPointsStride);
cloudPointBuffer.SetData(new[]
{
    new Vector2(-.5f, .5f),
    new Vector2(.5f, .5f),
    new Vector2(.5f, -.5f),
    new Vector2(.5f, -.5f),
    new Vector2(-.5f, -.5f),
    new Vector2(-.5f, .5f)
});
 
StructuredBuffer<float2> quadPoints;
StructuredBuffer<float3> particlePositions;
v2f vert(uint id : SV_VertexID, uint inst : SV_InstanceID)
{
    // Find the center of the quad, from local to world space
    float4 centerPoint = mul(unity_ObjectToWorld, float4(particlePositions[inst], 1));
 
    // Calculate y offset for each quad point
    float3 cameraForward = normalize(centerPoint - _WorldSpaceCameraPos);
    float y = dot(quadPoints[id].xy, cameraForward.xz);
 
    // Read out the particle data
    float radius = ...;
    float height = ...;
 
    // Set the position of the vert
    float4 finalPos = centerPoint + float4(quadPoints[id].x, y * height, quadPoints[id].y, 0) * radius;
    o.pos = mul(UNITY_MATRIX_VP, float4(finalPos.xyz, 1));
    o.uv = quadPoints[id].xy + 0.5;
 
    return o;
}
```

<span data-ttu-id="b65dc-156">Da wir die Partikel vor und nach hinten sortieren, und wir immer noch einen Solid-Style-Shader zum Ausschneiden (nicht Blend) transparenter Pixel verwendet haben, behandelt dieses Verfahren eine überraschende Menge an Partikeln, wodurch auch auf den Computern, die sich auf dem Computer befinden, eine aufwändige Überzeichnung vermieden wird.</span><span class="sxs-lookup"><span data-stu-id="b65dc-156">Since we sort the particles front-to-back and we still used a solid style shader to clip (not blend) transparent pixels, this technique handles a surprising amount of particles, avoiding costly over-draw even on the lower-powered machines.</span></span>

## <a name="transparent-particle-clouds"></a><span data-ttu-id="b65dc-157">Transparente Partikel Clouds</span><span class="sxs-lookup"><span data-stu-id="b65dc-157">Transparent particle clouds</span></span>

<span data-ttu-id="b65dc-158">Die Solid-Partikel bieten ein gutes, organisches Gefühl für die Form der Clouds, benötigen aber trotzdem etwas, um die fluffesme von Clouds zu verkaufen.</span><span class="sxs-lookup"><span data-stu-id="b65dc-158">The solid particles provided a good organic feel to the shape of the clouds but still needed something to sell the fluffiness of clouds.</span></span> <span data-ttu-id="b65dc-159">Wir haben uns entschieden, eine benutzerdefinierte Lösung für die High-End-Grafikkarten auszuprobieren, bei der Transparenz eingeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="b65dc-159">We decided to try a custom solution for the high-end graphics cards where we can introduce transparency.</span></span>

<span data-ttu-id="b65dc-160">Zu diesem Zweck haben wir einfach die anfängliche Sortierreihenfolge der Partikel gewechselt und den Shader so geändert, dass die Texturen Alpha verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b65dc-160">To do this we simply switched the initial sorting order of the particles and changed the shader to use the textures alpha.</span></span>

![Flauschige Clouds](images/fluffy-clouds-700px.jpg)

<span data-ttu-id="b65dc-162">Es hat sich bewährt, aber es hat sich bewährt, auch für die schwierigsten Computer zu groß zu sein, da dies dazu führen würde, dass jedes Pixel auf dem Bildschirm hunderte Male gerendert</span><span class="sxs-lookup"><span data-stu-id="b65dc-162">It looked great but proved to be too heavy for even the toughest machines since it would result in rendering each pixel on the screen hundreds of times!</span></span>

## <a name="render-off-screen-with-lower-resolution"></a><span data-ttu-id="b65dc-163">Aus Bildschirm mit niedrigerer Auflösung Rendering</span><span class="sxs-lookup"><span data-stu-id="b65dc-163">Render off-screen with lower resolution</span></span>

<span data-ttu-id="b65dc-164">Um die Anzahl der von den Clouds gerenderten Pixel zu verringern, haben wir begonnen, Sie in einem Quartals Auflösungs Puffer (im Vergleich zum Bildschirm) zu rendern und das Endergebnis nach oben auf den Bildschirm zu Strecken, nachdem alle Partikel gezeichnet wurden.</span><span class="sxs-lookup"><span data-stu-id="b65dc-164">To reduce the number of pixels rendered by the clouds, we started rendering them in a quarter resolution buffer (compared to the screen) and stretching the end result back up onto the screen after all the particles had been drawn.</span></span> <span data-ttu-id="b65dc-165">Dadurch gab es ungefähr eine 4X-Beschleunigung, aber es wurden einige Einschränkungen erzielt.</span><span class="sxs-lookup"><span data-stu-id="b65dc-165">This gave us roughly a 4x speedup, but came with a couple of caveats.</span></span>

<span data-ttu-id="b65dc-166">**Code für das Rendern außerhalb des Bildschirms:**</span><span class="sxs-lookup"><span data-stu-id="b65dc-166">**Code for rendering off-screen:**</span></span>

```
cloudBlendingCommand = new CommandBuffer();
Camera.main.AddCommandBuffer(whenToComposite, cloudBlendingCommand);
 
cloudCamera.CopyFrom(Camera.main);
cloudCamera.rect = new Rect(0, 0, 1, 1);    //Adaptive rendering can set the main camera to a smaller rect
cloudCamera.clearFlags = CameraClearFlags.Color;
cloudCamera.backgroundColor = new Color(0, 0, 0, 1);
 
currentCloudTexture = RenderTexture.GetTemporary(Camera.main.pixelWidth / 2, Camera.main.pixelHeight / 2, 0);
cloudCamera.targetTexture = currentCloudTexture;
 
// Render clouds to the offscreen buffer
cloudCamera.Render();
cloudCamera.targetTexture = null;
 
// Blend low-res clouds to the main target
cloudBlendingCommand.Blit(currentCloudTexture, new RenderTargetIdentifier(BuiltinRenderTextureType.CurrentActive), blitMaterial);
```

<span data-ttu-id="b65dc-167">Als erstes haben wir beim Rendern in einen Offscreen-Puffer alle detaillierten Informationen aus unserer Hauptszene verloren, was dazu führt, dass hinter dem Mountain hinter dem Mountain-Rendering Partikel hinter dem Gebirge gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="b65dc-167">First, when rendering into an off-screen buffer, we lost all depth information from our main scene, resulting in particles behind mountains rendering on top of the mountain.</span></span>

<span data-ttu-id="b65dc-168">Zweitens wurden bei der Streckung des Puffers auch Artefakte an den Rändern der Clouds eingeführt, bei denen die Auflösungs Änderung spürbar war.</span><span class="sxs-lookup"><span data-stu-id="b65dc-168">Second, stretching the buffer also introduced artifacts on the edges of our clouds where the resolution change was noticeable.</span></span> <span data-ttu-id="b65dc-169">In den nächsten beiden Abschnitten wird erläutert, wie wir diese Probleme gelöst haben.</span><span class="sxs-lookup"><span data-stu-id="b65dc-169">The next two sections talk about how we resolved these issues.</span></span>

## <a name="particle-depth-buffer"></a><span data-ttu-id="b65dc-170">Partikel tiefen Puffer</span><span class="sxs-lookup"><span data-stu-id="b65dc-170">Particle depth buffer</span></span>

<span data-ttu-id="b65dc-171">Damit die Partikel zusammen mit der Welt Geometrie vorhanden sind, in der ein Berg oder ein Objekt Partikel dahinter abdecken könnte, haben wir den Offscreen-Puffer mit einem tiefen Puffer aufgefüllt, der die Geometrie der Hauptszene enthält.</span><span class="sxs-lookup"><span data-stu-id="b65dc-171">To make the particles co-exist with the world geometry where a mountain or object could cover particles behind it, we populated the off-screen buffer with a depth buffer containing the geometry of the main scene.</span></span> <span data-ttu-id="b65dc-172">Zum Erstellen eines solchen tiefen Puffers haben wir eine zweite Kamera erstellt und nur die solide Geometrie und Tiefe der Szene gerendert.</span><span class="sxs-lookup"><span data-stu-id="b65dc-172">To produce such depth buffer, we created a second camera, rendering only the solid geometry and depth of the scene.</span></span>

<span data-ttu-id="b65dc-173">Anschließend haben wir die neue Textur im Pixelshader der Clouds verwendet, um Pixel zu okzieren.</span><span class="sxs-lookup"><span data-stu-id="b65dc-173">We then used the new texture in the pixel shader of the clouds to occlude pixels.</span></span> <span data-ttu-id="b65dc-174">Wir haben dieselbe Textur verwendet, um den Abstand zur Geometrie hinter einem cloudpixel zu berechnen.</span><span class="sxs-lookup"><span data-stu-id="b65dc-174">We used the same texture to calculate the distance to the geometry behind a cloud pixel.</span></span> <span data-ttu-id="b65dc-175">Durch die Verwendung dieser Distanz und die Anwendung auf die Alpha des Pixels haben wir nun die Auswirkungen von Clouds ausgeblendet, wenn Sie sich in der Nähe des Geländes befinden, sodass alle fest Schnitte entfernt werden, bei denen Partikel und Gelände einander entsprechen.</span><span class="sxs-lookup"><span data-stu-id="b65dc-175">By using that distance and applying it to the alpha of the pixel, we now had the effect of clouds fading out as they get close to terrain, removing any hard cuts where particles and terrain meet.</span></span>

![In das Gelände gemischte Clouds](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a><span data-ttu-id="b65dc-177">Schärfen der Kanten</span><span class="sxs-lookup"><span data-stu-id="b65dc-177">Sharpening the edges</span></span>

<span data-ttu-id="b65dc-178">Die gestreckten Clouds sahen fast identisch mit den Clouds der normalen Größe in der Mitte der Partikel oder wo Sie sich überlappen, haben jedoch einige Artefakte an den cloudrändern gezeigt.</span><span class="sxs-lookup"><span data-stu-id="b65dc-178">The stretched-up clouds looked almost identical to the normal size clouds at the center of the particles or where they overlapped, but showed some artifacts at the cloud edges.</span></span> <span data-ttu-id="b65dc-179">Andernfalls würden Spitzen Ränder verschwommen erscheinen, und beim Verschieben der Kamera wurden Alias Effekte eingeführt.</span><span class="sxs-lookup"><span data-stu-id="b65dc-179">Otherwise sharp edges would appear blurry and alias effects were introduced when the camera moved.</span></span>

<span data-ttu-id="b65dc-180">Wir haben dies gelöst, indem wir einen einfachen Shader auf dem Offscreen-Puffer ausgeführt haben, um zu ermitteln, an welcher Stelle große Änderungen aufgetreten sind (1).</span><span class="sxs-lookup"><span data-stu-id="b65dc-180">We solved this by running a simple shader on the off-screen buffer to determine where big changes in contrast occurred (1).</span></span> <span data-ttu-id="b65dc-181">Wir legen die Pixel mit großen Änderungen in einen neuen Schablonen Puffer (2) ab.</span><span class="sxs-lookup"><span data-stu-id="b65dc-181">We put the pixels with big changes into a new stencil buffer (2).</span></span> <span data-ttu-id="b65dc-182">Anschließend haben wir den Schablonen Puffer verwendet, um diese hohen Kontrast Bereiche zu maskieren, wenn Sie den Bildschirm Puffer auf den Bildschirm zurücksetzen, was zu Lücken in und um die Clouds führt (3).</span><span class="sxs-lookup"><span data-stu-id="b65dc-182">We then used the stencil buffer to mask out these high contrast areas when applying the off-screen buffer back to the screen, resulting in holes in and around the clouds (3).</span></span>

<span data-ttu-id="b65dc-183">Anschließend haben wir alle Partikel wieder im Vollbildmodus gerendert, aber dieses Mal hat der Schablonen Puffer verwendet, um alles außer den Rändern zu maskieren, was zu einem minimalen Satz von Pixeln geführt hat (4).</span><span class="sxs-lookup"><span data-stu-id="b65dc-183">We then rendered all the particles again in full-screen mode, but this time used the stencil buffer to mask out everything but the edges, resulting in a minimal set of pixels touched (4).</span></span> <span data-ttu-id="b65dc-184">Da der Befehls Puffer bereits für die Partikel erstellt wurde, mussten wir ihn einfach erneut auf der neuen Kamera darstellen.</span><span class="sxs-lookup"><span data-stu-id="b65dc-184">Since the command buffer was already created for the particles, we simply had to render it again to the new camera.</span></span>

![Fortschritt beim Rendern von cloudrändern](images/cloud-steps-1-4-700px.jpg)

<span data-ttu-id="b65dc-186">Das Endergebnis war eine Spitze von Spitzen mit den günstigen Mittelpunkten der Clouds.</span><span class="sxs-lookup"><span data-stu-id="b65dc-186">The end result was sharp edges with cheap center sections of the clouds.</span></span>

<span data-ttu-id="b65dc-187">Obwohl dies viel schneller war, als alle Partikel im Vollbildmodus zu rendern, gibt es weiterhin Kosten, die mit dem Testen eines Pixels gegen den Schablonen Puffer verbunden sind, sodass eine große Menge an über schreibungen weiterhin Kosten verursacht.</span><span class="sxs-lookup"><span data-stu-id="b65dc-187">While this was much faster than rendering all particles in full screen, there is still a cost associated with testing a pixel against the stencil buffer, so a massive amount of overdraw still came with a cost.</span></span>

## <a name="culling-particles"></a><span data-ttu-id="b65dc-188">Berechnen von Partikeln</span><span class="sxs-lookup"><span data-stu-id="b65dc-188">Culling particles</span></span>

<span data-ttu-id="b65dc-189">Für den Windeffekt haben wir lange Dreiecks Streifen in einem Compute-Shader generiert, wodurch viele Wisps von Wind weltweit erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="b65dc-189">For our wind effect, we generated long triangle strips in a compute shader, creating many wisps of wind in the world.</span></span> <span data-ttu-id="b65dc-190">Obwohl die Füllrate aufgrund der generierten Dinge-Striche nicht stark ausgelastet war, wurden viele Hunderttausende von Scheitel Punkten erzeugt, was zu einer hohen Auslastung für den Vertexshader führte.</span><span class="sxs-lookup"><span data-stu-id="b65dc-190">While the wind effect was not heavy on fill rate due to skinny strips generated, it produced many hundreds of thousands of vertices resulting in a heavy load for the vertex shader.</span></span>

<span data-ttu-id="b65dc-191">Wir haben anfügen-Puffer im COMPUTE-Shader eingeführt, um eine Teilmenge der zu zeichnungsenden Wind Striche zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="b65dc-191">We introduced append buffers on the compute shader to feed a subset of the wind strips to be drawn.</span></span> <span data-ttu-id="b65dc-192">Mit einer einfachen Ansichts Logik für die Logik der Logik im COMPUTE-Shader könnten wir feststellen, ob sich ein Strip außerhalb der Kameraansicht befunden hat, und verhindern, dass er dem Push-Puffer hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="b65dc-192">With some simple view frustum culling logic in the compute shader, we could determine if a strip was outside of camera view and prevent it from being added to the push buffer.</span></span> <span data-ttu-id="b65dc-193">Dadurch wurde die Menge der Bänder erheblich reduziert, sodass einige benötigte Zyklen auf der GPU freigegeben wurden.</span><span class="sxs-lookup"><span data-stu-id="b65dc-193">This reduced the amount of strips significantly, freeing up some needed cycles on the GPU.</span></span>

<span data-ttu-id="b65dc-194">**Code, der einen anfügen-Puffer veranschaulicht:**</span><span class="sxs-lookup"><span data-stu-id="b65dc-194">**Code demonstrating an append buffer:**</span></span>

<span data-ttu-id="b65dc-195">*Compute-Shader:*</span><span class="sxs-lookup"><span data-stu-id="b65dc-195">*Compute shader:*</span></span>

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

<span data-ttu-id="b65dc-196">*C#Ordnung*</span><span class="sxs-lookup"><span data-stu-id="b65dc-196">*C# code:*</span></span>

```
protected void Awake() 
{
    // Create an append buffer, setting the maximum size and the contents stride length
    culledParticlesIdxBuffer = new ComputeBuffer(ParticleCount, sizeof(int), ComputeBufferType.Append);
 
    // Set up Args Buffer for Draw Procedural Indirect
    argsBuffer = new ComputeBuffer(4, sizeof(int), ComputeBufferType.IndirectArguments);
    argsBuffer.SetData(new int[] { DataVertCount, 0, 0, 0 });
}
 
protected void Update()
{
    // Reset the append buffer, and dispatch the compute shader normally
    culledParticlesIdxBuffer.SetCounterValue(0);
 
    computer.Dispatch(...)
 
    // Copy the append buffer count into the args buffer used by the Draw Procedural Indirect call
    ComputeBuffer.CopyCount(culledParticlesIdxBuffer, argsBuffer, dstOffset: 1);
    ribbonRenderCommand.DrawProceduralIndirect(Matrix4x4.identity, renderMaterial, 0, MeshTopology.Triangles, dataBuffer);
}
```

<span data-ttu-id="b65dc-197">Wir haben versucht, die gleiche Technik für die cloudpartikel zu verwenden, bei denen wir Sie im COMPUTE-Shader aufschieben und nur die sichtbaren Partikel per Push über die gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="b65dc-197">We tried using the same technique on the cloud particles, where we would cull them on the compute shader and only push the visible particles to be rendered.</span></span> <span data-ttu-id="b65dc-198">Dieses Verfahren hat uns in der GPU nicht viel gespart, weil der größte Engpass die auf dem Bildschirm gerenderten Menge Pixel und nicht die Kosten für die Berechnung der Scheitel Punkte war.</span><span class="sxs-lookup"><span data-stu-id="b65dc-198">This technique actually did not save us much on the GPU since the biggest bottleneck was the amount pixels rendered on the screen, and not the cost of calculating the vertices.</span></span>

<span data-ttu-id="b65dc-199">Das andere Problem bei dieser Technik war, dass der Anfügen-Puffer in zufälliger Reihenfolge aufgefüllt wurde, weil er die Partikel parallelisiert hat, was dazu führte, dass die sortierten Partikel nicht sortiert wurden, was zu einem Flimmern von cloudpartikeln führte.</span><span class="sxs-lookup"><span data-stu-id="b65dc-199">The other problem with this technique was that the append buffer populated in random order due to its parallelized nature of computing the particles, causing the sorted particles to be un-sorted, resulting in flickering cloud particles.</span></span>

<span data-ttu-id="b65dc-200">Es gibt Techniken zum Sortieren des Push-Puffers, aber die begrenzte Menge an Leistungsvorteilen, die wir nicht mit der Verwendung von culelt haben, wäre wahrscheinlich mit einer zusätzlichen Sortierung ausgeglichen, daher haben wir entschieden, diese Optimierung nicht zu verfolgen.</span><span class="sxs-lookup"><span data-stu-id="b65dc-200">There are techniques to sort the push buffer, but the limited amount of performance gain we got out of culling particles would likely be offset with an additional sort, so we decided to not pursue this optimization.</span></span>

## <a name="adaptive-rendering"></a><span data-ttu-id="b65dc-201">Adaptive Rendering</span><span class="sxs-lookup"><span data-stu-id="b65dc-201">Adaptive rendering</span></span>

<span data-ttu-id="b65dc-202">Um eine stetige Framerate für eine APP zu gewährleisten, die unterschiedliche renderingbedingungen wie z. b. eine bewölkt und eine klare Ansicht hat, haben wir das adaptive Rendering unserer App</span><span class="sxs-lookup"><span data-stu-id="b65dc-202">To ensure a steady framerate on an app with varying rendering conditions like a cloudy vs a clear view, we introduced adaptive rendering to our app.</span></span>

<span data-ttu-id="b65dc-203">Der erste Schritt beim adaptiven Rendering ist das Messen der GPU.</span><span class="sxs-lookup"><span data-stu-id="b65dc-203">The first step of adaptive rendering is to measure GPU.</span></span> <span data-ttu-id="b65dc-204">Hierzu haben wir benutzerdefinierten Code am Anfang und am Ende eines gerenderten Frames in den GPU-Befehls Puffer eingefügt, wobei sowohl der linke als auch der Rechte Bildschirm Zeitpunkt erfasst werden.</span><span class="sxs-lookup"><span data-stu-id="b65dc-204">We did this by inserting custom code into the GPU command buffer at the beginning and the end of a rendered frame, capturing both the left and right eye screen time.</span></span>

<span data-ttu-id="b65dc-205">Durch Messen der Zeit, die für das Rendern und vergleichen mit der gewünschten Aktualisierungsrate aufgewendet wurde, haben wir einen Eindruck davon bekommen, wie nah das Ablegen der Rahmen ist.</span><span class="sxs-lookup"><span data-stu-id="b65dc-205">By measuring the time spent rendering and comparing it to our desired refresh-rate we got a sense of how close we were to dropping frames.</span></span>

<span data-ttu-id="b65dc-206">Wenn Sie in der Nähe von Frames ablegen, wird unser Rendering angepasst, um es schneller zu machen.</span><span class="sxs-lookup"><span data-stu-id="b65dc-206">When close to dropping frames, we adapt our rendering to make it faster.</span></span> <span data-ttu-id="b65dc-207">Eine einfache Möglichkeit zur Anpassung ist das Ändern der Viewportgröße des Bildschirms, sodass weniger Pixel gerendert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="b65dc-207">One simple way of adapting is changing the viewport size of the screen, requiring less pixels to get rendered.</span></span>

<span data-ttu-id="b65dc-208">Durch die Verwendung von *unityengine. XR. xrsettings. renderviewportscale* verkleinert das System den zielviewport und dehnt das Ergebnis automatisch auf den Bildschirm aus.</span><span class="sxs-lookup"><span data-stu-id="b65dc-208">By using *UnityEngine.XR.XRSettings.renderViewportScale* the system shrinks the targeted viewport and automatically stretches the result back up to fit the screen.</span></span> <span data-ttu-id="b65dc-209">Eine kleine Größenänderung ist in der Welt Geometrie kaum bemerkbar, und für den Skalierungsfaktor 0,7 ist die Hälfte der zu rendernden Pixel erforderlich.</span><span class="sxs-lookup"><span data-stu-id="b65dc-209">A small change in scale is barely noticeable on world geometry, and a scale factor of 0.7 requires half the amount of pixels to be rendered.</span></span>

![70% Skalierung, halbe Pixel](images/datascape-scaling-700px.jpg)

<span data-ttu-id="b65dc-211">Wenn wir feststellen, dass wir im Begriff sind, Frames abzulegen, verringern wir die Skalierung um eine festgelegte Zahl und erhöhen Sie wieder, wenn wir schneller genug ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="b65dc-211">When we detect that we are about to drop frames we lower the scale by a fixed number, and increase it back when we are running fast enough again.</span></span>

<span data-ttu-id="b65dc-212">Wir haben entschieden, welches cloudverfahren auf der Grundlage von Grafikfunktionen der Hardware beim Start verwendet werden soll. es ist jedoch möglich, es auf Daten aus der GPU-Messung zu basieren, um zu verhindern, dass das System lange Zeit mit niedriger Auflösung bleibt, aber dies ist nicht der Fall.  zum Durchsuchen von Daten im DataSet.</span><span class="sxs-lookup"><span data-stu-id="b65dc-212">While we decided what cloud technique to use based on graphics capabilities of the hardware at startup, it is possible to base it on data from the GPU measurement to prevent the system from staying at low resolution for a long time, but this is something we did not have time to explore in Datascape.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="b65dc-213">Abschließende Gedanken</span><span class="sxs-lookup"><span data-stu-id="b65dc-213">Final thoughts</span></span>

<span data-ttu-id="b65dc-214">Die Ausrichtung auf eine Vielzahl von Hardware ist schwierig und erfordert einige Planungsaufwand.</span><span class="sxs-lookup"><span data-stu-id="b65dc-214">Targeting a variety of hardware is challenging and requires some planning.</span></span>

<span data-ttu-id="b65dc-215">Es wird empfohlen, dass Sie mit den Ziel Computern beginnen, sich mit dem Problem Raum vertraut zu machen und eine Sicherungs Lösung zu entwickeln, die auf allen Computern ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b65dc-215">We recommend that you start targeting lower-powered machines to get familiar with the problem space and develop a backup solution that will run on all your machines.</span></span> <span data-ttu-id="b65dc-216">Entwerfen Sie Ihre Lösung mit der Füllrate im Hinterkopf, da Pixel ihre äußerst wertvolle Ressource sein wird.</span><span class="sxs-lookup"><span data-stu-id="b65dc-216">Design your solution with fill rate in mind, since pixels will be your most precious resource.</span></span> <span data-ttu-id="b65dc-217">Ziel-Solid Geometry über Transparenz.</span><span class="sxs-lookup"><span data-stu-id="b65dc-217">Target solid geometry over transparency.</span></span>

<span data-ttu-id="b65dc-218">Mit einer Sicherungs Lösung können Sie die ebenenkomplexität für High-End-Computer erhöhen oder einfach die Lösung ihrer Sicherungs Lösung optimieren.</span><span class="sxs-lookup"><span data-stu-id="b65dc-218">With a backup solution, you can then start layering in more complexity for high end machines or maybe just enhance resolution of your backup solution.</span></span>

<span data-ttu-id="b65dc-219">Entwerfen Sie für den schlimmsten Fallszenarien, und verwenden Sie ggf. das adaptive Rendering für große Situationen.</span><span class="sxs-lookup"><span data-stu-id="b65dc-219">Design for worst case scenarios, and maybe consider using adaptive rendering for heavy situations.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="b65dc-220">Informationen zu den Autoren</span><span class="sxs-lookup"><span data-stu-id="b65dc-220">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="b65dc-221"><b>Robert ferrese</b></span><span class="sxs-lookup"><span data-stu-id="b65dc-221"><b>Robert Ferrese</b></span></span><br><span data-ttu-id="b65dc-222">Anwendungsentwickler@Microsoft</span><span class="sxs-lookup"><span data-stu-id="b65dc-222">Software engineer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="b65dc-223"><b>Dan Andersson</b></span><span class="sxs-lookup"><span data-stu-id="b65dc-223"><b>Dan Andersson</b></span></span><br><span data-ttu-id="b65dc-224">Anwendungsentwickler@Microsoft</span><span class="sxs-lookup"><span data-stu-id="b65dc-224">Software engineer @Microsoft</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="b65dc-225">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b65dc-225">See also</span></span>
* [<span data-ttu-id="b65dc-226">Grundlegendes zur Leistung für gemischte Realität</span><span class="sxs-lookup"><span data-stu-id="b65dc-226">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="b65dc-227">Empfehlungen zur Leistung für Unity</span><span class="sxs-lookup"><span data-stu-id="b65dc-227">Performance Recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

 
