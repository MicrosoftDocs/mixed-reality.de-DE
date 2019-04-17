---
title: 'Fallstudie: Skalierung Datascape auf Geräten mit unterschiedlicher Leistung'
description: Diese Fallstudie bietet Einblick in die wie Microsoft-Entwicklern die Datascape-app, um ein überzeugendes Benutzererlebnis mit einem Bereich von Leistungsaspekten geräteübergreifend optimiert.
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: immersive Kopfhörer, Optimierung, VR, Fallstudie zur Leistung
ms.openlocfilehash: 990a5ee6de07b6416e3150a7885220409a9c8d93
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604874"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a><span data-ttu-id="e527e-104">Fallstudie: Skalierung Datascape auf Geräten mit unterschiedlicher Leistung</span><span class="sxs-lookup"><span data-stu-id="e527e-104">Case study - Scaling Datascape across devices with different performance</span></span>

<span data-ttu-id="e527e-105">Datascape ist eine Windows Mixed Reality-Anwendung, die intern bei Microsoft entwickelten, in denen konzentrierten wir uns auf die Anzeige von Wetterdaten auf Terrain-Daten.</span><span class="sxs-lookup"><span data-stu-id="e527e-105">Datascape is a Windows Mixed Reality application developed internally at Microsoft where we focused on displaying weather data on top of terrain data.</span></span> <span data-ttu-id="e527e-106">Die Anwendung beschrieben, die einzigartige Einblicke, die Benutzer erhalten aus Erkennen von Daten in mixed Reality durch, die den Benutzer mit holographic datenvisualisierung umgibt.</span><span class="sxs-lookup"><span data-stu-id="e527e-106">The application explores the unique insights users gain from discovering data in mixed reality by surrounding the user with holographic data visualization.</span></span>

<span data-ttu-id="e527e-107">Für Datascape wollten wir eine Vielzahl von Plattformen mit unterschiedlichen Hardware-Funktionen, die im Bereich von Microsoft HoloLens, immersive Headsets Windows Mixed Reality und von geringerer Leistung Behandeln von PCs mit den neuesten PCs mit High-End-GPU als Ziel.</span><span class="sxs-lookup"><span data-stu-id="e527e-107">For Datascape we wanted to target a variety of platforms with different hardware capabilities ranging from Microsoft HoloLens to Windows Mixed Reality immersive headsets, and from lower-powered PCs to the very latest PCs with high-end GPU.</span></span> <span data-ttu-id="e527e-108">Die größte Herausforderung wurde unsere Szene in wenigen visuell ansprechend auf Geräten mit völlig anderen Grafikfunktionen rendern, während der Ausführung auf einer hohen Framerate.</span><span class="sxs-lookup"><span data-stu-id="e527e-108">The main challenge was rendering our scene in a visually appealing matter on devices with wildly different graphics capabilities while executing at a high framerate.</span></span>

<span data-ttu-id="e527e-109">Diese Fallstudie durchlaufen Sie den Prozess und die Verfahren zum Erstellen einiger unsere mehr GPU-intensiven-Systemen, die beschreiben, die Probleme, die wir festgestellt und wie wir sie gelöst.</span><span class="sxs-lookup"><span data-stu-id="e527e-109">This case study will walk through the process and techniques used to create some of our more GPU-intensive systems, describing the problems we encountered and how we overcame them.</span></span>

## <a name="transparency-and-overdraw"></a><span data-ttu-id="e527e-110">Transparenz und -Elements zu überzeichnen</span><span class="sxs-lookup"><span data-stu-id="e527e-110">Transparency and overdraw</span></span>

<span data-ttu-id="e527e-111">Unsere wichtigsten Rendering schwierigkeiten behandelt Transparenz, da Transparenz auf einer GPU teuer sein kann.</span><span class="sxs-lookup"><span data-stu-id="e527e-111">Our main rendering struggles dealt with transparency, since transparency can be expensive on a GPU.</span></span>

<span data-ttu-id="e527e-112">Volumengeometrie kann zwischen Vorder-und Rückseite beim Schreiben in die Tiefenpuffer, Beenden alle zukünftigen Pixel, die sich nicht hinter diese Pixel aus, die verworfen wird gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="e527e-112">Solid geometry can be rendered front to back while writing to the depth buffer, stopping any future pixels located behind that pixel from being discarded.</span></span> <span data-ttu-id="e527e-113">Dadurch wird verhindert, dass ausgeblendete Pixel Ausführen des Pixel-Shaders, der Prozess deutlich beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="e527e-113">This prevents hidden pixels from executing the pixel shader, speeding up the process significantly.</span></span> <span data-ttu-id="e527e-114">Wenn die Geometrie optimal sortiert ist, wird nur einmal jedes Pixel auf dem Bildschirm gezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="e527e-114">If geometry is sorted optimally, each pixel on the screen will be drawn only once.</span></span>

<span data-ttu-id="e527e-115">Transparente Geometrie muss sortiert werden in den Vordergrund zurück und basiert auf der Kombination von der Ausgabe des Pixelshaders auf das aktuelle Pixel auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="e527e-115">Transparent geometry needs to be sorted back to front and relies on blending the output of the pixel shader to the current pixel on the screen.</span></span> <span data-ttu-id="e527e-116">Dies kann in jedem Pixel auf dem Bildschirm, das gerade gezeichnet wird mehrere Male pro Frame, bezeichnet als Elements zu überzeichnen führen.</span><span class="sxs-lookup"><span data-stu-id="e527e-116">This can result in each pixel on the screen being drawn to multiple times per frame, referred to as overdraw.</span></span>

<span data-ttu-id="e527e-117">Für HoloLens und gängige PCs, der Bildschirm kann nur gefüllt werden eine Reihe von Fällen problematisch Rendern transparent machen.</span><span class="sxs-lookup"><span data-stu-id="e527e-117">For HoloLens and mainstream PCs, the screen can only be filled a handful of times, making transparent rendering problematic.</span></span>

## <a name="introduction-to-datascape-scene-components"></a><span data-ttu-id="e527e-118">Einführung in die Szene Komponenten Datascape</span><span class="sxs-lookup"><span data-stu-id="e527e-118">Introduction to Datascape scene components</span></span>

<span data-ttu-id="e527e-119">Wir mussten unsere Szene drei wesentliche Komponenten; **der Benutzeroberfläche der Zuordnung**, und **das Wetter**.</span><span class="sxs-lookup"><span data-stu-id="e527e-119">We had three major components to our scene; **the UI, the map**, and **the weather**.</span></span> <span data-ttu-id="e527e-120">Wir wussten früh, dass unsere Wetter Auswirkungen die GPU-Zeit, die sie abrufen kann, erforderlich wäre, damit wir absichtlich gestaltet, dass die Benutzeroberfläche und das Terrain in einer Weise, die alle überzeichnen reduzieren würde.</span><span class="sxs-lookup"><span data-stu-id="e527e-120">We knew early on that our weather effects would require all the GPU time it could get, so we purposely designed the UI and terrain in a way that would reduce any overdraw.</span></span>

<span data-ttu-id="e527e-121">Es wurden mehrmals überarbeitet die Benutzeroberfläche minimieren die Menge des Elements zu überzeichnen es erzeugen.</span><span class="sxs-lookup"><span data-stu-id="e527e-121">We reworked the UI several times to minimize the amount of overdraw it would produce.</span></span> <span data-ttu-id="e527e-122">Wir bezieht, im Zweifelsfall komplexere Geometrie statt transparent der Kunst der Überlagerung übereinander für Komponenten wie leuchtendes Übersichten für Schaltflächen und Zuordnung.</span><span class="sxs-lookup"><span data-stu-id="e527e-122">We erred on the side of more complex geometry rather than overlaying transparent art on top of each other for components like glowing buttons and map overviews.</span></span>

<span data-ttu-id="e527e-123">Für die Karte haben wir einen benutzerdefinierten Shader, der Sie Unity-Standardfunktionen, z. B. Schatten und komplexe Beleuchtung entfernen würde ersetzt sie durch eine einfache einmalige Sun-Beleuchtungsmodell und eine benutzerdefinierte Nebel-Berechnung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e527e-123">For the map, we used a custom shader that would strip out standard Unity features such as shadows and complex lighting, replacing them with a simple single sun lighting model and a custom fog calculation.</span></span> <span data-ttu-id="e527e-124">Dies erzeugt einen einfache Pixel-Shader und GPU-Zyklen frei.</span><span class="sxs-lookup"><span data-stu-id="e527e-124">This produced a simple pixel shader and free up GPU cycles.</span></span>

<span data-ttu-id="e527e-125">Es verwaltet zu erhalten, die sowohl für die Benutzeroberfläche als auch für die Zuordnung für das Rendern am Budget, in denen wir keine Änderungen werden abhängig von der Hardware benötigen. allerdings die Wetter-Visualisierung, insbesondere die cloudrenderingfunktionen erwies sich als eine größere Herausforderung!</span><span class="sxs-lookup"><span data-stu-id="e527e-125">We managed to get both the UI and the map to rendering at budget where we did not need any changes to them depending on the hardware; however, the weather visualization, in particular the cloud rendering, proved to be more of a challenge!</span></span>

## <a name="background-on-cloud-data"></a><span data-ttu-id="e527e-126">Hintergrundinformationen zu clouddaten</span><span class="sxs-lookup"><span data-stu-id="e527e-126">Background on cloud data</span></span>

<span data-ttu-id="e527e-127">Unsere clouddaten von den NOAA-Servern heruntergeladen wurde (http://nomads.ncep.noaa.gov/) und uns in drei unterschiedliche 2-Ebenen, jeweils die oberen und unteren Höhe der Cloud als auch die Dichte der Cloud für jede Zelle des Rasters.</span><span class="sxs-lookup"><span data-stu-id="e527e-127">Our cloud data was downloaded from NOAA servers (http://nomads.ncep.noaa.gov/) and came to us in three distinct 2D layers, each with the top and bottom height of the cloud, as well as the density of the cloud for each cell of the grid.</span></span> <span data-ttu-id="e527e-128">Die Verarbeitung der Daten wurde in einer Cloud-Info-Textur, in dem jede Komponente in der Rot, Grün und Blau-Komponente der Textur für den leichteren Zugriff auf die GPU gespeichert wurde.</span><span class="sxs-lookup"><span data-stu-id="e527e-128">The data got processed into a cloud info texture where each component was stored in the red, green, and blue component of the texture for easy access on the GPU.</span></span>

## <a name="geometry-clouds"></a><span data-ttu-id="e527e-129">Geometry-clouds</span><span class="sxs-lookup"><span data-stu-id="e527e-129">Geometry clouds</span></span>

<span data-ttu-id="e527e-130">Um sicherzustellen, dass es sich bei unseren Computern mit geringerer Leistung behandeln u. u. unsere Clouds, die wir uns, für den Einstieg entschieden ein Ansatz, der Volumengeometrie verwenden würden, minimieren-Elements zu überzeichnen.</span><span class="sxs-lookup"><span data-stu-id="e527e-130">To make sure our lower-powered machines could render our clouds we decided to start with an approach that would use solid geometry to minimize overdraw.</span></span>

<span data-ttu-id="e527e-131">Wir haben zunächst versucht, Clouds erstellen, generieren Sie ein solid Heightmap-Mesh für jede Ebene, verwenden den Radius der Cloud Informationen Textur pro Vertex zum Generieren von der Form.</span><span class="sxs-lookup"><span data-stu-id="e527e-131">We first tried producing clouds by generating a solid heightmap mesh for each layer using the radius of the cloud info texture per vertex to generate the shape.</span></span> <span data-ttu-id="e527e-132">Einen Geometrie-Shader verwendet, um die Scheitelpunkte, die sowohl auf dem oberen und unteren Rand der Cloud generieren solide Formen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e527e-132">We used a geometry shader to produce the vertices both at the top and the bottom of the cloud generating solid cloud shapes.</span></span> <span data-ttu-id="e527e-133">Die Dichtewert in der Textur verwendet auf die Farbe von der Cloud mit dunklere Farben für weitere Dichte Clouds.</span><span class="sxs-lookup"><span data-stu-id="e527e-133">We used the density value from the texture to color the cloud with darker colors for more dense clouds.</span></span>

<span data-ttu-id="e527e-134">**Shader für die Scheitelpunkte erstellen:**</span><span class="sxs-lookup"><span data-stu-id="e527e-134">**Shader for creating the vertices:**</span></span>

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

<span data-ttu-id="e527e-135">Wir eingeführt, eine kleine Rauschen-Muster, um weitere Details über die echten Daten zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="e527e-135">We introduced a small noise pattern to get more detail on top of the real data.</span></span> <span data-ttu-id="e527e-136">Round Cloud Kanten erzeugt werden, abgeschnitten wir die Pixel in der Pixel-Shader, wenn der interpolierte Radiuswert einen Schwellenwert an, in der Nähe von NULL-Werte verwerfen erreicht.</span><span class="sxs-lookup"><span data-stu-id="e527e-136">To produce round cloud edges, we clipped the pixels in the pixel shader when the interpolated radius value hit a threshold to discard near-zero values.</span></span>

![Geometry-clouds](images/datascape-geometry-clouds-700px.jpg)

<span data-ttu-id="e527e-138">Da die Clouds Volumengeometrie sind, können sie vor dem Gelände alle kostspielig Landkarte Pixel unterhalb ausblenden, um die Framerate weiter zu verbessern gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="e527e-138">Since the clouds are solid geometry, they can be rendered before the terrain to hide any expensive map pixels underneath to further improve framerate.</span></span> <span data-ttu-id="e527e-139">Diese Lösung wurde auch für alle Grafikkarten min-Spezifikation, High-End-Grafikkarten sowie für HoloLens, aufgrund der Solid Geometry Rendern Ansatz ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="e527e-139">This solution ran well on all graphics cards from min-spec to high-end graphics cards, as well as on HoloLens, because of the solid geometry rendering approach.</span></span>

## <a name="solid-particle-clouds"></a><span data-ttu-id="e527e-140">Solid Partikel clouds</span><span class="sxs-lookup"><span data-stu-id="e527e-140">Solid particle clouds</span></span>

<span data-ttu-id="e527e-141">Wir mussten jetzt eine sicherungslösung, die erzeugt einer ordentliche Darstellung unserer Cloud-Daten, jedoch wurde ein wenig unrühmliche in der Faktor "toll" und das volumetrische Verhalten, das wir für unsere High-End-Computer sollten keine vermittelt.</span><span class="sxs-lookup"><span data-stu-id="e527e-141">We now had a backup solution that produced a decent representation of our cloud data, but was a bit lackluster in the “wow” factor and did not convey the volumetric feel that we wanted for our high-end machines.</span></span>

<span data-ttu-id="e527e-142">Im nächsten Schritt wurde die Clouds erstellen, indem Sie mit ca. 100.000 Partikel auf ein natürliches und volumetrische Einblick zu gewinnen darstellt werden.</span><span class="sxs-lookup"><span data-stu-id="e527e-142">Our next step was creating the clouds by representing them with approximately 100,000 particles to produce a more organic and volumetric look.</span></span>

<span data-ttu-id="e527e-143">Wenn Partikel solid bleiben und von vorne, hinten sortieren, können wir trotzdem davon profitieren Tiefe Puffer culling der Pixel hinter zuvor gerenderte Partikel, reduzieren die Überzeichnung.</span><span class="sxs-lookup"><span data-stu-id="e527e-143">If particles stay solid and sort front-to-back, we can still benefit from depth buffer culling of the pixels behind previously rendered particles, reducing the overdraw.</span></span> <span data-ttu-id="e527e-144">Darüber hinaus können wir mit einer Partikel basierende Lösung, die Menge der Partikel verwendet, um verschiedene Zielhardware ändern.</span><span class="sxs-lookup"><span data-stu-id="e527e-144">Also, with a particle-based solution, we can alter the amount of particles used to target different hardware.</span></span> <span data-ttu-id="e527e-145">Allerdings müssen alle Pixel weiterhin Tiefe getestet, dies führt zu etwas zusätzlichem Aufwand verbunden werden.</span><span class="sxs-lookup"><span data-stu-id="e527e-145">However, all pixels still need to be depth tested, which results in some additional overhead.</span></span>

<span data-ttu-id="e527e-146">Zunächst haben wir Partikelpositionen, um den Mittelpunkt der Benutzeroberfläche beim Start erstellt.</span><span class="sxs-lookup"><span data-stu-id="e527e-146">First, we created particle positions around the center point of the experience at startup.</span></span> <span data-ttu-id="e527e-147">Wir verteilt die Partikel intensiver um den Mittelpunkt und weniger daher bei der Entfernung.</span><span class="sxs-lookup"><span data-stu-id="e527e-147">We distributed the particles more densely around the center and less so in the distance.</span></span> <span data-ttu-id="e527e-148">Wir sortiert alle Partikel aus dem Center in den Hintergrund vorab, sodass die nächste Partikel zunächst gerendert werden kann.</span><span class="sxs-lookup"><span data-stu-id="e527e-148">We pre-sorted all particles from the center to the back so that the closest particles would render first.</span></span>

<span data-ttu-id="e527e-149">Ein Compute-Shader würde Beispiele für die Textur Cloud Informationen, um jedes einzelne Partikel auf eine korrekte Höhe und die Farbe die Dichte der zugrunde liegenden zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="e527e-149">A compute shader would sample the cloud info texture to position each particle at a correct height and color it based on the density.</span></span>

<span data-ttu-id="e527e-150">Wir verwendeten *DrawProcedural* zum Rendern des Gevierts pro Partikel, sodass diese Partikel bleiben Sie auf der GPU überhaupt ein Timeout.</span><span class="sxs-lookup"><span data-stu-id="e527e-150">We used *DrawProcedural* to render a quad per particle allowing the particle data to stay on the GPU at all times.</span></span>

<span data-ttu-id="e527e-151">Jedes einzelne Partikel enthalten sind, eine Höhen- und eine Radius.</span><span class="sxs-lookup"><span data-stu-id="e527e-151">Each particle contained both a height and a radius.</span></span> <span data-ttu-id="e527e-152">Die Höhe wurde basierend auf den clouddaten, die in der Cloud-Info-Textur entnommen, und der Radius basiert auf der ursprünglichen Verteilung, in dem er berechnet werden würde, um den horizontalen Abstand und die nächsten benachbarten Element zu speichern.</span><span class="sxs-lookup"><span data-stu-id="e527e-152">The height was based on the cloud data sampled from the cloud info texture, and the radius was based on the initial distribution where it would be calculated to store the horizontal distance to its closest neighbor.</span></span> <span data-ttu-id="e527e-153">Die Quads, würden diese Daten verwenden, um orientieren sich selbst durch die Höhe Winkel geändert, damit die Benutzer sich bei horizontal darstellen würde die Höhe angezeigt werden, und wenn Benutzer sich von oben nach unten gesucht werden soll, würde der Bereich zwischen seinen Nachbarn abgedeckt werden.</span><span class="sxs-lookup"><span data-stu-id="e527e-153">The quads would use this data to orient itself angled by the height so that when users look at it horizontally, the height would be shown, and when users looked at it top-down, the area between its neighbors would be covered.</span></span>

![Particle Form](images/particle-shape-700px.png)

<span data-ttu-id="e527e-155">**Shader-Code zeigt die Verteilung:**</span><span class="sxs-lookup"><span data-stu-id="e527e-155">**Shader code showing the distribution:**</span></span>

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

<span data-ttu-id="e527e-156">Da wir die Partikel Vordergrund-Hintergrund sortieren, und wir weiterhin verwendet einen Stil durchgehend Shader auf transparente Pixel Clip (nicht "Blend"), verarbeitet diese Technik überraschend viel Partikel, vermeiden kostspielige zu zeichnen, sogar auf den Computern mit geringerer Leistung behandeln.</span><span class="sxs-lookup"><span data-stu-id="e527e-156">Since we sort the particles front-to-back and we still used a solid style shader to clip (not blend) transparent pixels, this technique handles a surprising amount of particles, avoiding costly over-draw even on the lower-powered machines.</span></span>

## <a name="transparent-particle-clouds"></a><span data-ttu-id="e527e-157">Transparente Partikel clouds</span><span class="sxs-lookup"><span data-stu-id="e527e-157">Transparent particle clouds</span></span>

<span data-ttu-id="e527e-158">Die solid Partikel einen natürliches guten Überblick mit der Form der Clouds bereitgestellt, aber noch benötigt etwas zu verkaufen die Fluffiness Clouds.</span><span class="sxs-lookup"><span data-stu-id="e527e-158">The solid particles provided a good organic feel to the shape of the clouds but still needed something to sell the fluffiness of clouds.</span></span> <span data-ttu-id="e527e-159">Wir entschieden, eine benutzerdefinierte Lösung für die High-End-Grafikkarten, versuchen Sie es, in dem wir Transparenz führen kann.</span><span class="sxs-lookup"><span data-stu-id="e527e-159">We decided to try a custom solution for the high-end graphics cards where we can introduce transparency.</span></span>

<span data-ttu-id="e527e-160">Diesen Schritt ausführen, wir einfach die anfängliche Sortierreihenfolge der Partikel gewechselt und den Shader Verwendung der Alphawert Texturen geändert.</span><span class="sxs-lookup"><span data-stu-id="e527e-160">To do this we simply switched the initial sorting order of the particles and changed the shader to use the textures alpha.</span></span>

![Fluffy clouds](images/fluffy-clouds-700px.jpg)

<span data-ttu-id="e527e-162">Es sahen Sie großartig jedoch erwies sich als zu groß für sogar die anspruchsvollsten Computer, da es kommt rendering jedes Pixel auf dem Bildschirm Hunderte Male!</span><span class="sxs-lookup"><span data-stu-id="e527e-162">It looked great but proved to be too heavy for even the toughest machines since it would result in rendering each pixel on the screen hundreds of times!</span></span>

## <a name="render-off-screen-with-lower-resolution"></a><span data-ttu-id="e527e-163">Rendern Sie mit niedrigerer Auflösung außerhalb des Bildschirms</span><span class="sxs-lookup"><span data-stu-id="e527e-163">Render off-screen with lower resolution</span></span>

<span data-ttu-id="e527e-164">Um die Anzahl der Pixel gerendert wird, von der Cloud zu verringern, haben wir angefangen Rendern sie in einem Quartal Auflösung Puffer (verglichen mit dem Bildschirm) und das Endergebnis Strecken Sichern auf dem Bildschirm nach aller Partikel gezeichnet wurden, mussten.</span><span class="sxs-lookup"><span data-stu-id="e527e-164">To reduce the number of pixels rendered by the clouds, we started rendering them in a quarter resolution buffer (compared to the screen) and stretching the end result back up onto the screen after all the particles had been drawn.</span></span> <span data-ttu-id="e527e-165">Dies gibt uns ungefähr eine 4 X Beschleunigung, aber es kam mit einigen Einschränkungen.</span><span class="sxs-lookup"><span data-stu-id="e527e-165">This gave us roughly a 4x speedup, but came with a couple of caveats.</span></span>

<span data-ttu-id="e527e-166">**Der Code für das Rendern außerhalb des Bildschirms:**</span><span class="sxs-lookup"><span data-stu-id="e527e-166">**Code for rendering off-screen:**</span></span>

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

<span data-ttu-id="e527e-167">Zunächst verloren beim rendering in einem offscreenpuffer wir alle ausführliche Informationen über unsere wichtigsten Szene, wodurch Partikel hinter Berge Rendering über die riesige Menge.</span><span class="sxs-lookup"><span data-stu-id="e527e-167">First, when rendering into an off-screen buffer, we lost all depth information from our main scene, resulting in particles behind mountains rendering on top of the mountain.</span></span>

<span data-ttu-id="e527e-168">Strecken des Puffers wurde andererseits auch Elemente an den Rändern des unsere Clouds, in dem die Änderung der Auflösung merkliche wurde.</span><span class="sxs-lookup"><span data-stu-id="e527e-168">Second, stretching the buffer also introduced artifacts on the edges of our clouds where the resolution change was noticeable.</span></span> <span data-ttu-id="e527e-169">Wie wir diese Probleme gelöst, ist in den nächsten beiden Abschnitten erläutert.</span><span class="sxs-lookup"><span data-stu-id="e527e-169">The next two sections talk about how we resolved these issues.</span></span>

## <a name="particle-depth-buffer"></a><span data-ttu-id="e527e-170">Particle Tiefenpuffer</span><span class="sxs-lookup"><span data-stu-id="e527e-170">Particle depth buffer</span></span>

<span data-ttu-id="e527e-171">Damit wird die Partikel, mit die Weltgeometrie gleichzeitig vorhanden sein, in denen konnte eine Mountain oder ein Objekt Partikel dahinter abdecken, aufgefüllt wir den außerhalb des Bildschirms Puffer mit einer Tiefenpuffer, die die Geometrie der wichtigsten Szene enthält.</span><span class="sxs-lookup"><span data-stu-id="e527e-171">To make the particles co-exist with the world geometry where a mountain or object could cover particles behind it, we populated the off-screen buffer with a depth buffer containing the geometry of the main scene.</span></span> <span data-ttu-id="e527e-172">Um solche Tiefenpuffer zu erstellen, haben wir eine zweite Kamera, nur die Volumengeometrie und Tiefe der Szene gerendert.</span><span class="sxs-lookup"><span data-stu-id="e527e-172">To produce such depth buffer, we created a second camera, rendering only the solid geometry and depth of the scene.</span></span>

<span data-ttu-id="e527e-173">Wir verwendet die neue Textur klicken Sie dann in den Pixel-Shader-Clouds, um die Pixel verdeckt.</span><span class="sxs-lookup"><span data-stu-id="e527e-173">We then used the new texture in the pixel shader of the clouds to occlude pixels.</span></span> <span data-ttu-id="e527e-174">Berechnet den Abstand der Geometrie hinter einem Cloud-Pixel verwendet derselben Textur.</span><span class="sxs-lookup"><span data-stu-id="e527e-174">We used the same texture to calculate the distance to the geometry behind a cloud pixel.</span></span> <span data-ttu-id="e527e-175">Durch diese Bereiche verwenden und diese für den Alphawert des Pixels zu übernehmen, mussten wir nun die Auswirkungen von Clouds ausgeblendet wird, wie sie in der Nähe Terrain erhalten, entfernen alle schwer Schnitte Partikel und Gelände, in denen zu erfüllen.</span><span class="sxs-lookup"><span data-stu-id="e527e-175">By using that distance and applying it to the alpha of the pixel, we now had the effect of clouds fading out as they get close to terrain, removing any hard cuts where particles and terrain meet.</span></span>

![Clouds in Terrain gemischt](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a><span data-ttu-id="e527e-177">Die Ränder Schärfe</span><span class="sxs-lookup"><span data-stu-id="e527e-177">Sharpening the edges</span></span>

<span data-ttu-id="e527e-178">Die gestreckt von Clouds fast identisch mit die normale Größe-Clouds in der Mitte der Partikel gesucht oder wo sie überlappende, jedoch einige Elemente an den Kanten Cloud wurde gezeigt.</span><span class="sxs-lookup"><span data-stu-id="e527e-178">The stretched-up clouds looked almost identical to the normal size clouds at the center of the particles or where they overlapped, but showed some artifacts at the cloud edges.</span></span> <span data-ttu-id="e527e-179">Klicken Sie andernfalls scharfe Kanten würde unscharf angezeigt, und Alias Auswirkungen wurden eingeführt, wenn die Kamera verschoben.</span><span class="sxs-lookup"><span data-stu-id="e527e-179">Otherwise sharp edges would appear blurry and alias effects were introduced when the camera moved.</span></span>

<span data-ttu-id="e527e-180">Dies lösten wir mit einem einfachen Shader im Puffer außerhalb des Bildschirms, um zu bestimmen, wo große Änderungen im Gegensatz dazu (1) aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="e527e-180">We solved this by running a simple shader on the off-screen buffer to determine where big changes in contrast occurred (1).</span></span> <span data-ttu-id="e527e-181">Wir sollen die Pixel mit großen Änderungen in eine neue Schablone-Puffer (2).</span><span class="sxs-lookup"><span data-stu-id="e527e-181">We put the pixels with big changes into a new stencil buffer (2).</span></span> <span data-ttu-id="e527e-182">Verwendet dann den Stencilpuffer Maske sich diese Bereiche von hohem Kontrast beim Anwenden der offscreenpuffer auf dem Bildschirm, was Löcher in und um die Clouds (3).</span><span class="sxs-lookup"><span data-stu-id="e527e-182">We then used the stencil buffer to mask out these high contrast areas when applying the off-screen buffer back to the screen, resulting in holes in and around the clouds (3).</span></span>

<span data-ttu-id="e527e-183">Wir dann gerendert aller Partikel erneut in den Vollbildmodus, aber diesmal verwendet den Stencilpuffer Maske, alles die Ränder, was einen minimalen Satz von Pixeln verwendet (4).</span><span class="sxs-lookup"><span data-stu-id="e527e-183">We then rendered all the particles again in full-screen mode, but this time used the stencil buffer to mask out everything but the edges, resulting in a minimal set of pixels touched (4).</span></span> <span data-ttu-id="e527e-184">Da der Befehlspuffer für das Partikel bereits erstellt wurde, mussten wir einfach erneut auf die neue Kamera zu rendern.</span><span class="sxs-lookup"><span data-stu-id="e527e-184">Since the command buffer was already created for the particles, we simply had to render it again to the new camera.</span></span>

![Fortschritt des rendering Cloud Kanten](images/cloud-steps-1-4-700px.jpg)

<span data-ttu-id="e527e-186">Das Ergebnis war, scharfe Kanten mit günstig Center Abschnitten der Clouds.</span><span class="sxs-lookup"><span data-stu-id="e527e-186">The end result was sharp edges with cheap center sections of the clouds.</span></span>

<span data-ttu-id="e527e-187">War dies viel schneller als Rendern alle Partikel im Vollbild, besteht immer noch eine Pixel für den Stencilpuffer testen, damit eine große Zahl von Überzeichnung weiterhin Kosten mit Kosten stammt.</span><span class="sxs-lookup"><span data-stu-id="e527e-187">While this was much faster than rendering all particles in full screen, there is still a cost associated with testing a pixel against the stencil buffer, so a massive amount of overdraw still came with a cost.</span></span>

## <a name="culling-particles"></a><span data-ttu-id="e527e-188">Culling Partikel</span><span class="sxs-lookup"><span data-stu-id="e527e-188">Culling particles</span></span>

<span data-ttu-id="e527e-189">Für unsere Effekt Wind generiert wir lange Dreieck Streifen im Compute-Shader, erstellen viele Wisps des Wind in der ganzen Welt.</span><span class="sxs-lookup"><span data-stu-id="e527e-189">For our wind effect, we generated long triangle strips in a compute shader, creating many wisps of wind in the world.</span></span> <span data-ttu-id="e527e-190">Während die Wind Auswirkungen nicht viel Füllrate aufgrund aus erster Hand leisten, die generiert wurde, erzeugt es vielen Hunderten oder Tausenden von Vertices, die in einer hohen Auslastung für den Vertex-Shader resultieren.</span><span class="sxs-lookup"><span data-stu-id="e527e-190">While the wind effect was not heavy on fill rate due to skinny strips generated, it produced many hundreds of thousands of vertices resulting in a heavy load for the vertex shader.</span></span>

<span data-ttu-id="e527e-191">Wir eingeführt anfügen Puffer auf den Compute-Shader zum Übertragen von einer Teilmenge der Wind leisten, gezeichnet werden soll.</span><span class="sxs-lookup"><span data-stu-id="e527e-191">We introduced append buffers on the compute shader to feed a subset of the wind strips to be drawn.</span></span> <span data-ttu-id="e527e-192">Mit einigen einfachen Ansicht Frustums Cullingverfahren Logik im Compute-Shader können wir bestimmen, ob ein Streifen außerhalb der Kameraansicht ist und verhindern, dass er auf den Push-Puffer hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="e527e-192">With some simple view frustum culling logic in the compute shader, we could determine if a strip was outside of camera view and prevent it from being added to the push buffer.</span></span> <span data-ttu-id="e527e-193">Dies reduziert die Menge der Streifen erheblich freizugeben, einige erforderlichen Zyklen in der GPU.</span><span class="sxs-lookup"><span data-stu-id="e527e-193">This reduced the amount of strips significantly, freeing up some needed cycles on the GPU.</span></span>

<span data-ttu-id="e527e-194">**Der Code veranschaulicht einen Anfügepuffer:**</span><span class="sxs-lookup"><span data-stu-id="e527e-194">**Code demonstrating an append buffer:**</span></span>

<span data-ttu-id="e527e-195">*Compute-Shader:*</span><span class="sxs-lookup"><span data-stu-id="e527e-195">*Compute shader:*</span></span>

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

<span data-ttu-id="e527e-196">*C#Code:*</span><span class="sxs-lookup"><span data-stu-id="e527e-196">*C# code:*</span></span>

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

<span data-ttu-id="e527e-197">Wir haben versucht, mit derselben Technik für die Cloud-Partikel, auf würden sie auf den Compute-Shader zu reduzieren und nur mithilfe von Push übertragen die sichtbaren Partikel gerendert werden soll.</span><span class="sxs-lookup"><span data-stu-id="e527e-197">We tried using the same technique on the cloud particles, where we would cull them on the compute shader and only push the visible particles to be rendered.</span></span> <span data-ttu-id="e527e-198">Dieses Verfahren tatsächlich nicht uns speichern auf der GPU, da der größte Engpass Menge Pixel gerendert wird, auf dem Bildschirm und nicht die Kosten für die Scheitelpunkte berechnet wurde.</span><span class="sxs-lookup"><span data-stu-id="e527e-198">This technique actually did not save us much on the GPU since the biggest bottleneck was the amount pixels rendered on the screen, and not the cost of calculating the vertices.</span></span>

<span data-ttu-id="e527e-199">Das andere Problem mit diesem Verfahren war, dass der Append-Puffer in zufälliger Reihenfolge aufgrund seiner parallelisierten Natur des Computings die Partikel, verursacht die sortierten Partikel soll nicht sortiert sind, was zu Flimmern Cloud Partikel aufgefüllt.</span><span class="sxs-lookup"><span data-stu-id="e527e-199">The other problem with this technique was that the append buffer populated in random order due to its parallelized nature of computing the particles, causing the sorted particles to be un-sorted, resulting in flickering cloud particles.</span></span>

<span data-ttu-id="e527e-200">Es gibt Methoden, um die Push-Puffer zu sortieren, aber die begrenzte Menge an Leistungsgewinn, die wir aus dem Partikel culling rehabilitationszentrum würde wahrscheinlich mit einer zusätzlichen Sortierung versetzt werden, damit wir uns entschieden, diese Optimierung nicht zu verfolgen.</span><span class="sxs-lookup"><span data-stu-id="e527e-200">There are techniques to sort the push buffer, but the limited amount of performance gain we got out of culling particles would likely be offset with an additional sort, so we decided to not pursue this optimization.</span></span>

## <a name="adaptive-rendering"></a><span data-ttu-id="e527e-201">Adaptive rendering</span><span class="sxs-lookup"><span data-stu-id="e527e-201">Adaptive rendering</span></span>

<span data-ttu-id="e527e-202">Um eine stetige Framerate für eine app mit unterschiedlichen Rendern Bedingungen wie ein bewölkt Visual Studio ein klares Bild zu gewährleisten, haben wir für unsere Anwendung adaptives Rendering eingeführt.</span><span class="sxs-lookup"><span data-stu-id="e527e-202">To ensure a steady framerate on an app with varying rendering conditions like a cloudy vs a clear view, we introduced adaptive rendering to our app.</span></span>

<span data-ttu-id="e527e-203">Der erste Schritt des adaptive Rendering ist GPU zu messen.</span><span class="sxs-lookup"><span data-stu-id="e527e-203">The first step of adaptive rendering is to measure GPU.</span></span> <span data-ttu-id="e527e-204">Dies haben wir durch Einfügen von benutzerdefinierten Code in den GPU-Befehlspuffer am Anfang und Ende einer gerenderte Frame, erfassen sowohl die linken und rechten-Augen-Bildschirm Zeit.</span><span class="sxs-lookup"><span data-stu-id="e527e-204">We did this by inserting custom code into the GPU command buffer at the beginning and the end of a rendered frame, capturing both the left and right eye screen time.</span></span>

<span data-ttu-id="e527e-205">Durch das Messen Zeit die Rendern und durch Vergleichen mit unserer gewünschten-Aktualisierungsrate, die wir einen Überblick darüber hier, wie nahe wir waren, um Frames zu löschen.</span><span class="sxs-lookup"><span data-stu-id="e527e-205">By measuring the time spent rendering and comparing it to our desired refresh-rate we got a sense of how close we were to dropping frames.</span></span>

<span data-ttu-id="e527e-206">Wenn in der Nähe Frames gelöscht wird, passen wir unsere rendern, um ihn schneller zu machen.</span><span class="sxs-lookup"><span data-stu-id="e527e-206">When close to dropping frames, we adapt our rendering to make it faster.</span></span> <span data-ttu-id="e527e-207">Eine einfache Möglichkeit zur Anpassung der ändert der Viewportgröße des Bildschirms, erfordert weniger Pixel gerendert wird, erhalten.</span><span class="sxs-lookup"><span data-stu-id="e527e-207">One simple way of adapting is changing the viewport size of the screen, requiring less pixels to get rendered.</span></span>

<span data-ttu-id="e527e-208">Mithilfe von *UnityEngine.XR.XRSettings.renderViewportScale* das System gezielten Viewport verkleinert und gestreckt wird, das Ergebnis zurück bis zum Anpassen der Bildschirm automatisch.</span><span class="sxs-lookup"><span data-stu-id="e527e-208">By using *UnityEngine.XR.XRSettings.renderViewportScale* the system shrinks the targeted viewport and automatically stretches the result back up to fit the screen.</span></span> <span data-ttu-id="e527e-209">Eine kleine Änderung der Skalierung ist für die Weltgeometrie unauffällig und ein Skalierungsfaktor von 0,7 erfordert die Hälfte der Pixel gerendert werden soll.</span><span class="sxs-lookup"><span data-stu-id="e527e-209">A small change in scale is barely noticeable on world geometry, and a scale factor of 0.7 requires half the amount of pixels to be rendered.</span></span>

![70 % skalieren, die Hälfte der Pixel](images/datascape-scaling-700px.jpg)

<span data-ttu-id="e527e-211">Wenn festgestellt wird, dass wir sind zum Löschen des Frames, die wir die Skalierung um eine feste Anzahl verringern, und erhöhen sie sichern können, wenn wir schnell genug erneut ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="e527e-211">When we detect that we are about to drop frames we lower the scale by a fixed number, and increase it back when we are running fast enough again.</span></span>

<span data-ttu-id="e527e-212">Während wir uns entschieden, welche Cloud-Technik, mit Grafiken Funktionen der Hardware beim Start abhängig, es möglich ist, die sie als Grundlage für die Daten aus der GPU-Messung, um zu verhindern, dass das System mit geringer Auflösung lange bleiben, aber dies wir keine Zeit haben  Um in Datascape zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="e527e-212">While we decided what cloud technique to use based on graphics capabilities of the hardware at startup, it is possible to base it on data from the GPU measurement to prevent the system from staying at low resolution for a long time, but this is something we did not have time to explore in Datascape.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="e527e-213">Abschließende betrachtungen</span><span class="sxs-lookup"><span data-stu-id="e527e-213">Final thoughts</span></span>

<span data-ttu-id="e527e-214">Eine Vielzahl von Hardware ist schwierig und erfordert eine gewisse Planung.</span><span class="sxs-lookup"><span data-stu-id="e527e-214">Targeting a variety of hardware is challenging and requires some planning.</span></span>

<span data-ttu-id="e527e-215">Es wird empfohlen, dass Sie starten auf unteren-gestützte Computer so, dass vertraut mit den Problembereich und entwickeln eine sicherungslösung, die auf allen Computern ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="e527e-215">We recommend that you start targeting lower-powered machines to get familiar with the problem space and develop a backup solution that will run on all your machines.</span></span> <span data-ttu-id="e527e-216">Entwerfen Sie Ihre Lösung mit Füllrate Denken Sie daran, da Pixel Ihrer wertvollsten Ressourcen sein werden.</span><span class="sxs-lookup"><span data-stu-id="e527e-216">Design your solution with fill rate in mind, since pixels will be your most precious resource.</span></span> <span data-ttu-id="e527e-217">Ziel-Volumengeometrie über Transparenz.</span><span class="sxs-lookup"><span data-stu-id="e527e-217">Target solid geometry over transparency.</span></span>

<span data-ttu-id="e527e-218">Mit einer sicherungslösung klicken Sie dann Schichten in höhere Komplexität für high-End-Computer starten oder vielleicht einfach Auflösung sicherungslösung verbessern.</span><span class="sxs-lookup"><span data-stu-id="e527e-218">With a backup solution, you can then start layering in more complexity for high end machines or maybe just enhance resolution of your backup solution.</span></span>

<span data-ttu-id="e527e-219">Für den ungünstigsten Fall entwerfen, und vielleicht verwenden Sie ggf. adaptives Rendering für hohe Situationen.</span><span class="sxs-lookup"><span data-stu-id="e527e-219">Design for worst case scenarios, and maybe consider using adaptive rendering for heavy situations.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="e527e-220">Über die Autoren</span><span class="sxs-lookup"><span data-stu-id="e527e-220">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="e527e-221"><b>Robert Ferrese</b></span><span class="sxs-lookup"><span data-stu-id="e527e-221"><b>Robert Ferrese</b></span></span><br><span data-ttu-id="e527e-222">Anwendungsentwickler @Microsoft</span><span class="sxs-lookup"><span data-stu-id="e527e-222">Software engineer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="e527e-223"><b>Dan Andersson</b></span><span class="sxs-lookup"><span data-stu-id="e527e-223"><b>Dan Andersson</b></span></span><br><span data-ttu-id="e527e-224">Anwendungsentwickler @Microsoft</span><span class="sxs-lookup"><span data-stu-id="e527e-224">Software engineer @Microsoft</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="e527e-225">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e527e-225">See also</span></span>
* [<span data-ttu-id="e527e-226">Grundlegendes zur Leistung für Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="e527e-226">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="e527e-227">Empfehlungen zur Leistung für Unity</span><span class="sxs-lookup"><span data-stu-id="e527e-227">Performance Recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

 
