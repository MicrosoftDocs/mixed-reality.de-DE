---
title: 'Fallstudie: Skalieren von DataSet auf Geräten mit unterschiedlicher Leistung'
description: Diese Fallstudie bietet Einblicke in die Art und Weise, wie Microsoft-Entwickler die datascape-App optimiert haben, um eine überzeugende Geräte übergreifende Darstellung mit einer Reihe von Leistungs Funktionen zu bieten
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: immersives Headset, Leistungsoptimierung, VR, Fallstudie
ms.openlocfilehash: 05f97188c81d85685540be998111ecfc47d9ef9c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436502"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a>Fallstudie: Skalieren von DataSet auf Geräten mit unterschiedlicher Leistung

Datascape ist eine Windows Mixed Reality-Anwendung, die intern bei Microsoft entwickelt wurde, wobei wir uns auf das Anzeigen von Wetterdaten oberhalb von Geländedaten konzentrieren. Die Anwendung untersucht die eindeutigen Einblicke, die Benutzer bei der Ermittlung von Daten in gemischter Realität gewinnen, indem Sie den Benutzer mit Holographic Data-Visualisierung umgeben.

Für das DataSet wollten wir eine Vielzahl von Plattformen mit unterschiedlichen Hardwarefunktionen als Ziel für Microsoft hololens und Windows Mixed Reality-immersive Headsets und von Geräten mit niedrigerer Leistung auf die neuesten PCs mit High-End-GPU ausrichten. Die Hauptaufgabe war das Rendern unserer Szene in einem visuell ansprechenden Bereich auf Geräten mit stark unterschiedlichen Grafikfunktionen bei der Ausführung bei einer hohen Framerate.

Diese Fallstudie führt Sie durch den Prozess und die Verfahren, die zum Erstellen einiger unserer GPU-intensiveren Systeme verwendet werden, und beschreibt die Probleme, die wir kennengelernt haben und wie wir Sie überwunden haben.

## <a name="transparency-and-overdraw"></a>Transparenz und Überzeichnung

Die wichtigsten Renderingerweiterungen, die Transparenz behandeln, da Transparenz für eine GPU aufwendig sein kann.

Eine solide Geometrie kann beim Schreiben in den tiefen Puffer in den Vordergrund gerendert werden. Dadurch wird verhindert, dass alle zukünftigen Pixel hinter diesem Pixel verworfen werden. Dadurch wird verhindert, dass versteckte Pixel den Pixelshader ausführen, wodurch der Prozess erheblich beschleunigt wird. Wenn Geometrie optimal sortiert ist, wird jedes Pixel auf dem Bildschirm nur einmal gezeichnet.

Die transparente Geometrie muss wieder in den Vordergrund sortiert werden und basiert darauf, dass die Ausgabe des Pixelshaders mit dem aktuellen Pixel auf dem Bildschirm gemischt wird. Dies kann dazu führen, dass jedes Pixel auf dem Bildschirm mehrmals pro Frame gezeichnet wird, was als overdraw bezeichnet wird.

Bei hololens und gängigen PCs kann der Bildschirm nur wenige Male aufgefüllt werden, sodass das transparente Rendering problematisch ist.

## <a name="introduction-to-datascape-scene-components"></a>Einführung in datascape Scene-Komponenten

Wir hatten drei Hauptkomponenten in unserer Szene. **die Benutzeroberfläche, die Karte**und **das Wetter**. Wir wussten schon früh, dass unsere Wettereffekte die gesamte GPU-Zeit in Anspruch nehmen würden, daher haben wir die Benutzeroberfläche und das Gelände auf eine Weise entworfen, die alle über schreibungen verringern würde.

Wir haben die Benutzeroberfläche mehrmals überarbeitet, um die Menge der zu erstellenden über schreibungen zu minimieren. Wir haben auf der Seite komplexer Geometrie gerendet, anstatt transparente Grafiken für Komponenten wie leuchtende Schaltflächen und Karten Übersichten zu überlagern.

Für die Karte haben wir einen benutzerdefinierten Shader verwendet, der standardmäßige Unity-Features, wie z. b. Schatten und komplexe Beleuchtung, entfernt und Sie durch ein einfaches Modell mit einem Sun-Licht und eine benutzerdefinierte Nebel Berechnung ersetzt. Dies führte zu einem einfachen Pixelshader und freigab GPU-Zyklen.

Wir haben die Benutzeroberfläche und die Zuordnung zum Rendering im Budget erhalten, in dem wir abhängig von der Hardware keine Änderungen vorgenommen haben. Allerdings erwies sich die Wetter Visualisierung, insbesondere das cloudrendering, als eine größere Herausforderung.

## <a name="background-on-cloud-data"></a>Hintergrundinformationen zu clouddaten

Unsere clouddaten wurden von NOAA-Servern heruntergeladen (https://nomads.ncep.noaa.gov/) und kamen in drei unterschiedlichen 2D-Schichten, jeweils mit der oberen und unteren Höhe der Cloud, sowie der Dichte der Cloud für jede Zelle des Rasters. Die Daten wurden in eine Cloud-Informations Textur verarbeitet, in der jede Komponente in der roten, grünen und blauen Komponente der Textur gespeichert wurde, um den Zugriff auf die GPU zu vereinfachen.

## <a name="geometry-clouds"></a>Geometry-Clouds

Um sicherzustellen, dass unsere unterstützen Computer unsere Clouds wirklich Rendering haben, haben wir uns entschieden, mit einem Ansatz zu beginnen, der eine solide Geometrie zum Minimieren von über schreibungen verwenden würde.

Wir haben zunächst versucht, Clouds zu erzeugen, indem wir für jede Ebene ein solides Heightmap-Mesh generiert haben. dabei wird der Radius der cloudinfotextur pro Scheitelpunkt verwendet, um die Form zu generieren Wir haben einen Geometry-Shader verwendet, um die Scheitel Punkte im oberen und unteren Bereich der Cloud zu erzeugen, die solide cloudformen erzeugen. Wir haben den Dichtewert aus der Textur verwendet, um die Cloud mit dunkleren Farben für dischere Clouds zu versehen.

**Shader zum Erstellen der Vertices:**

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

Wir haben ein kleines Rauschmuster eingeführt, um weitere Details zu den echten Daten zu erhalten. Um Round-Cloud-Ränder zu erzeugen, haben wir die Pixel im Pixelshader abgeschnitten, wenn der interpoliert RADIUS-Wert einen Schwellenwert erreicht hat, um fast null-Werte zu verwerfen.

![Geometry-Clouds](images/datascape-geometry-clouds-700px.jpg)

Da es sich bei den Clouds um eine solide Geometrie handelt, können Sie vor dem-Gelände gerendert werden, um alle teuren Karten Pixel auszublenden, um die Framerate weiter zu Diese Lösung wurde auf allen Grafikkarten von min-spec bis High-End-Grafikkarten sowie auf hololens aufgrund des Solid Geometry-renderingansatzes ordnungsgemäß ausgeführt.

## <a name="solid-particle-clouds"></a>Solid-Partikel-Clouds

Wir verfügten nun über eine Sicherungs Lösung, die eine angemessene Darstellung unserer clouddaten erzeugt hat, war aber ein bisschen einfach im "Wow"-Faktor und hat das volummetric-Gefühl nicht vermittelt, das wir für unsere High-End-Computer wollten.

Der nächste Schritt besteht darin, die Clouds zu erstellen, indem Sie Sie mit ungefähr 100.000 Partikeln darstellen, um ein mehr organisches und volummetrisches aussehen zu erzeugen.

Wenn Partikel solide bleiben und vor-zu-hinten sortiert werden, können wir weiterhin von der tiefen Puffer Erstellung der Pixel hinter zuvor gerenderten Partikeln profitieren, wodurch die Überzeichnung reduziert wird. Mit einer Partikel basierten Lösung können wir auch die Menge der Partikel ändern, die für die unterschiedliche Hardware verwendet werden. Allerdings müssen alle Pixel noch tiefer getestet werden, was zu einem zusätzlichen Aufwand führt.

Zuerst haben wir die Partikel Positionen um den Mittelpunkt der Umgebung beim Start erstellt. Wir haben die Partikel um das Zentrum und weniger in der Entfernung verteilt. Wir haben alle Partikel von der Mitte nach hinten sortiert, sodass die nächstgelegenen Partikel zuerst dargestellt werden.

Ein Compute-Shader gibt eine Stichprobe der cloudinfotextur aus, um die einzelnen Partikel auf der Grundlage der Dichte an der richtigen Höhe zu positionieren.

Wir haben *drawprozeduren* verwendet, um ein Quad pro Partikel zu erzeugen, sodass die Partikel Daten jederzeit auf der GPU bleiben können.

Jedes Partikel enthielt sowohl eine Höhe als auch einen RADIUS. Die Höhe basiert auf den clouddaten, die aus der Cloud-Informations Textur entnommen wurden, und der RADIUS basiert auf der anfänglichen Verteilung, in der er so berechnet würde, dass er den horizontalen Abstand zum nächstgelegenen Nachbarn speichert. Die Quads würden diese Daten verwenden, um sich selbst durch die Höhe zu orientieren, sodass die Höhe, wenn Benutzer sich horizontal ansehen, angezeigt wird, und wenn sich die Benutzer von oben nach unten ansehen, wird der Bereich zwischen den Nachbarn abgedeckt.

![Partikelform](images/particle-shape-700px.png)

**Shader-Code, der die Verteilung anzeigt:**

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

Da wir die Partikel vor und nach hinten sortieren, und wir immer noch einen Solid-Style-Shader zum Ausschneiden (nicht Blend) transparenter Pixel verwendet haben, behandelt dieses Verfahren eine überraschende Menge an Partikeln, wodurch auch auf den Computern, die sich auf dem Computer befinden, eine aufwändige Überzeichnung vermieden wird.

## <a name="transparent-particle-clouds"></a>Transparente Partikel Clouds

Die Solid-Partikel bieten ein gutes, organisches Gefühl für die Form der Clouds, benötigen aber trotzdem etwas, um die fluffesme von Clouds zu verkaufen. Wir haben uns entschieden, eine benutzerdefinierte Lösung für die High-End-Grafikkarten auszuprobieren, bei der Transparenz eingeführt werden kann.

Zu diesem Zweck haben wir einfach die anfängliche Sortierreihenfolge der Partikel gewechselt und den Shader so geändert, dass die Texturen Alpha verwendet werden.

![Flauschige Clouds](images/fluffy-clouds-700px.jpg)

Es hat sich bewährt, aber es hat sich bewährt, auch für die schwierigsten Computer zu groß zu sein, da dies dazu führen würde, dass jedes Pixel auf dem Bildschirm hunderte Male gerendert

## <a name="render-off-screen-with-lower-resolution"></a>Aus Bildschirm mit niedrigerer Auflösung Rendering

Um die Anzahl der von den Clouds gerenderten Pixel zu verringern, haben wir begonnen, Sie in einem Quartals Auflösungs Puffer (im Vergleich zum Bildschirm) zu rendern und das Endergebnis nach oben auf den Bildschirm zu Strecken, nachdem alle Partikel gezeichnet wurden. Dadurch gab es ungefähr eine 4X-Beschleunigung, aber es wurden einige Einschränkungen erzielt.

**Code für das Rendern außerhalb des Bildschirms:**

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

Als erstes haben wir beim Rendern in einen Offscreen-Puffer alle detaillierten Informationen aus unserer Hauptszene verloren, was dazu führt, dass hinter dem Mountain hinter dem Mountain-Rendering Partikel hinter dem Gebirge gerendert werden.

Zweitens wurden bei der Streckung des Puffers auch Artefakte an den Rändern der Clouds eingeführt, bei denen die Auflösungs Änderung spürbar war. In den nächsten beiden Abschnitten wird erläutert, wie wir diese Probleme gelöst haben.

## <a name="particle-depth-buffer"></a>Partikel tiefen Puffer

Damit die Partikel zusammen mit der Welt Geometrie vorhanden sind, in der ein Berg oder ein Objekt Partikel dahinter abdecken könnte, haben wir den Offscreen-Puffer mit einem tiefen Puffer aufgefüllt, der die Geometrie der Hauptszene enthält. Zum Erstellen eines solchen tiefen Puffers haben wir eine zweite Kamera erstellt und nur die solide Geometrie und Tiefe der Szene gerendert.

Anschließend haben wir die neue Textur im Pixelshader der Clouds verwendet, um Pixel zu okzieren. Wir haben dieselbe Textur verwendet, um den Abstand zur Geometrie hinter einem cloudpixel zu berechnen. Durch die Verwendung dieser Distanz und die Anwendung auf die Alpha des Pixels haben wir nun die Auswirkungen von Clouds ausgeblendet, wenn Sie sich in der Nähe des Geländes befinden, sodass alle fest Schnitte entfernt werden, bei denen Partikel und Gelände einander entsprechen.

![In das Gelände gemischte Clouds](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a>Schärfen der Kanten

Die gestreckten Clouds sahen fast identisch mit den Clouds der normalen Größe in der Mitte der Partikel oder wo Sie sich überlappen, haben jedoch einige Artefakte an den cloudrändern gezeigt. Andernfalls würden Spitzen Ränder verschwommen erscheinen, und beim Verschieben der Kamera wurden Alias Effekte eingeführt.

Wir haben dies gelöst, indem wir einen einfachen Shader auf dem Offscreen-Puffer ausgeführt haben, um zu ermitteln, an welcher Stelle große Änderungen aufgetreten sind (1). Wir legen die Pixel mit großen Änderungen in einen neuen Schablonen Puffer (2) ab. Anschließend haben wir den Schablonen Puffer verwendet, um diese hohen Kontrast Bereiche zu maskieren, wenn Sie den Bildschirm Puffer auf den Bildschirm zurücksetzen, was zu Lücken in und um die Clouds führt (3).

Anschließend haben wir alle Partikel wieder im Vollbildmodus gerendert, aber dieses Mal hat der Schablonen Puffer verwendet, um alles außer den Rändern zu maskieren, was zu einem minimalen Satz von Pixeln geführt hat (4). Da der Befehls Puffer bereits für die Partikel erstellt wurde, mussten wir ihn einfach erneut auf der neuen Kamera darstellen.

![Fortschritt beim Rendern von cloudrändern](images/cloud-steps-1-4-700px.jpg)

Das Endergebnis war eine Spitze von Spitzen mit den günstigen Mittelpunkten der Clouds.

Obwohl dies viel schneller war, als alle Partikel im Vollbildmodus zu rendern, gibt es weiterhin Kosten, die mit dem Testen eines Pixels gegen den Schablonen Puffer verbunden sind, sodass eine große Menge an über schreibungen weiterhin Kosten verursacht.

## <a name="culling-particles"></a>Berechnen von Partikeln

Für den Windeffekt haben wir lange Dreiecks Streifen in einem Compute-Shader generiert, wodurch viele Wisps von Wind weltweit erstellt wurden. Obwohl die Füllrate aufgrund der generierten Dinge-Striche nicht stark ausgelastet war, wurden viele Hunderttausende von Scheitel Punkten erzeugt, was zu einer hohen Auslastung für den Vertexshader führte.

Wir haben anfügen-Puffer im COMPUTE-Shader eingeführt, um eine Teilmenge der zu zeichnungsenden Wind Striche zu übertragen. Mit einer einfachen Ansichts Logik für die Logik der Logik im COMPUTE-Shader könnten wir feststellen, ob sich ein Strip außerhalb der Kameraansicht befunden hat, und verhindern, dass er dem Push-Puffer hinzugefügt wird. Dadurch wurde die Menge der Bänder erheblich reduziert, sodass einige benötigte Zyklen auf der GPU freigegeben wurden.

**Code, der einen anfügen-Puffer veranschaulicht:**

*Compute-Shader:*

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

*C#Ordnung*

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

Wir haben versucht, die gleiche Technik für die cloudpartikel zu verwenden, bei denen wir Sie im COMPUTE-Shader aufschieben und nur die sichtbaren Partikel per Push über die gerendert werden. Dieses Verfahren hat uns in der GPU nicht viel gespart, weil der größte Engpass die auf dem Bildschirm gerenderten Menge Pixel und nicht die Kosten für die Berechnung der Scheitel Punkte war.

Das andere Problem bei dieser Technik war, dass der Anfügen-Puffer in zufälliger Reihenfolge aufgefüllt wurde, weil er die Partikel parallelisiert hat, was dazu führte, dass die sortierten Partikel nicht sortiert wurden, was zu einem Flimmern von cloudpartikeln führte.

Es gibt Techniken zum Sortieren des Push-Puffers, aber die begrenzte Menge an Leistungsvorteilen, die wir nicht mit der Verwendung von culelt haben, wäre wahrscheinlich mit einer zusätzlichen Sortierung ausgeglichen, daher haben wir entschieden, diese Optimierung nicht zu verfolgen.

## <a name="adaptive-rendering"></a>Adaptive Rendering

Um eine stetige Framerate für eine APP zu gewährleisten, die unterschiedliche renderingbedingungen wie z. b. eine bewölkt und eine klare Ansicht hat, haben wir das adaptive Rendering unserer App

Der erste Schritt beim adaptiven Rendering ist das Messen der GPU. Hierzu haben wir benutzerdefinierten Code am Anfang und am Ende eines gerenderten Frames in den GPU-Befehls Puffer eingefügt, wobei sowohl der linke als auch der Rechte Bildschirm Zeitpunkt erfasst werden.

Durch Messen der Zeit, die für das Rendern und vergleichen mit der gewünschten Aktualisierungsrate aufgewendet wurde, haben wir einen Eindruck davon bekommen, wie nah das Ablegen der Rahmen ist.

Wenn Sie in der Nähe von Frames ablegen, wird unser Rendering angepasst, um es schneller zu machen. Eine einfache Möglichkeit zur Anpassung ist das Ändern der Viewportgröße des Bildschirms, sodass weniger Pixel gerendert werden müssen.

Durch die Verwendung von *unityengine. XR. xrsettings. renderviewportscale* verkleinert das System den zielviewport und dehnt das Ergebnis automatisch auf den Bildschirm aus. Eine kleine Größenänderung ist in der Welt Geometrie kaum bemerkbar, und für den Skalierungsfaktor 0,7 ist die Hälfte der zu rendernden Pixel erforderlich.

![70% Skalierung, halbe Pixel](images/datascape-scaling-700px.jpg)

Wenn wir feststellen, dass wir im Begriff sind, Frames abzulegen, verringern wir die Skalierung um eine festgelegte Zahl und erhöhen Sie wieder, wenn wir schneller genug ausgeführt werden.

Wir haben entschieden, welches cloudverfahren auf der Grundlage von Grafikfunktionen der Hardware beim Start verwendet werden soll. es ist jedoch möglich, es auf Daten aus der GPU-Messung zu basieren, um zu verhindern, dass das System lange Zeit mit niedriger Auflösung bleibt, aber dies ist nicht der Fall.  zum Durchsuchen von Daten im DataSet.

## <a name="final-thoughts"></a>Abschließende Gedanken

Die Ausrichtung auf eine Vielzahl von Hardware ist schwierig und erfordert einige Planungsaufwand.

Es wird empfohlen, dass Sie mit den Ziel Computern beginnen, sich mit dem Problem Raum vertraut zu machen und eine Sicherungs Lösung zu entwickeln, die auf allen Computern ausgeführt wird. Entwerfen Sie Ihre Lösung mit der Füllrate im Hinterkopf, da Pixel ihre äußerst wertvolle Ressource sein wird. Ziel-Solid Geometry über Transparenz.

Mit einer Sicherungs Lösung können Sie die ebenenkomplexität für High-End-Computer erhöhen oder einfach die Lösung ihrer Sicherungs Lösung optimieren.

Entwerfen Sie für den schlimmsten Fallszenarien, und verwenden Sie ggf. das adaptive Rendering für große Situationen.

## <a name="about-the-authors"></a>Informationen zu den Autoren

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><b>Robert ferrese</b><br>Software Entwickler @Microsoft</td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><b>Dan Andersson</b><br>Software Entwickler @Microsoft</td>
</tr>
</table>


## <a name="see-also"></a>Weitere Informationen:
* [Grundlegendes zur Leistung für gemischte Realität](understanding-performance-for-mixed-reality.md)
* [Empfehlungen zur Leistung für Unity](performance-recommendations-for-unity.md)

 
