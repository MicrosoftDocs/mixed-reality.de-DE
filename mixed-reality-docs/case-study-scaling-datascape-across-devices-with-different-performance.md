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
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a>Fallstudie: Skalierung Datascape auf Geräten mit unterschiedlicher Leistung

Datascape ist eine Windows Mixed Reality-Anwendung, die intern bei Microsoft entwickelten, in denen konzentrierten wir uns auf die Anzeige von Wetterdaten auf Terrain-Daten. Die Anwendung beschrieben, die einzigartige Einblicke, die Benutzer erhalten aus Erkennen von Daten in mixed Reality durch, die den Benutzer mit holographic datenvisualisierung umgibt.

Für Datascape wollten wir eine Vielzahl von Plattformen mit unterschiedlichen Hardware-Funktionen, die im Bereich von Microsoft HoloLens, immersive Headsets Windows Mixed Reality und von geringerer Leistung Behandeln von PCs mit den neuesten PCs mit High-End-GPU als Ziel. Die größte Herausforderung wurde unsere Szene in wenigen visuell ansprechend auf Geräten mit völlig anderen Grafikfunktionen rendern, während der Ausführung auf einer hohen Framerate.

Diese Fallstudie durchlaufen Sie den Prozess und die Verfahren zum Erstellen einiger unsere mehr GPU-intensiven-Systemen, die beschreiben, die Probleme, die wir festgestellt und wie wir sie gelöst.

## <a name="transparency-and-overdraw"></a>Transparenz und -Elements zu überzeichnen

Unsere wichtigsten Rendering schwierigkeiten behandelt Transparenz, da Transparenz auf einer GPU teuer sein kann.

Volumengeometrie kann zwischen Vorder-und Rückseite beim Schreiben in die Tiefenpuffer, Beenden alle zukünftigen Pixel, die sich nicht hinter diese Pixel aus, die verworfen wird gerendert werden. Dadurch wird verhindert, dass ausgeblendete Pixel Ausführen des Pixel-Shaders, der Prozess deutlich beschleunigen. Wenn die Geometrie optimal sortiert ist, wird nur einmal jedes Pixel auf dem Bildschirm gezeichnet werden.

Transparente Geometrie muss sortiert werden in den Vordergrund zurück und basiert auf der Kombination von der Ausgabe des Pixelshaders auf das aktuelle Pixel auf dem Bildschirm. Dies kann in jedem Pixel auf dem Bildschirm, das gerade gezeichnet wird mehrere Male pro Frame, bezeichnet als Elements zu überzeichnen führen.

Für HoloLens und gängige PCs, der Bildschirm kann nur gefüllt werden eine Reihe von Fällen problematisch Rendern transparent machen.

## <a name="introduction-to-datascape-scene-components"></a>Einführung in die Szene Komponenten Datascape

Wir mussten unsere Szene drei wesentliche Komponenten; **der Benutzeroberfläche der Zuordnung**, und **das Wetter**. Wir wussten früh, dass unsere Wetter Auswirkungen die GPU-Zeit, die sie abrufen kann, erforderlich wäre, damit wir absichtlich gestaltet, dass die Benutzeroberfläche und das Terrain in einer Weise, die alle überzeichnen reduzieren würde.

Es wurden mehrmals überarbeitet die Benutzeroberfläche minimieren die Menge des Elements zu überzeichnen es erzeugen. Wir bezieht, im Zweifelsfall komplexere Geometrie statt transparent der Kunst der Überlagerung übereinander für Komponenten wie leuchtendes Übersichten für Schaltflächen und Zuordnung.

Für die Karte haben wir einen benutzerdefinierten Shader, der Sie Unity-Standardfunktionen, z. B. Schatten und komplexe Beleuchtung entfernen würde ersetzt sie durch eine einfache einmalige Sun-Beleuchtungsmodell und eine benutzerdefinierte Nebel-Berechnung verwendet werden. Dies erzeugt einen einfache Pixel-Shader und GPU-Zyklen frei.

Es verwaltet zu erhalten, die sowohl für die Benutzeroberfläche als auch für die Zuordnung für das Rendern am Budget, in denen wir keine Änderungen werden abhängig von der Hardware benötigen. allerdings die Wetter-Visualisierung, insbesondere die cloudrenderingfunktionen erwies sich als eine größere Herausforderung!

## <a name="background-on-cloud-data"></a>Hintergrundinformationen zu clouddaten

Unsere clouddaten von den NOAA-Servern heruntergeladen wurde (http://nomads.ncep.noaa.gov/) und uns in drei unterschiedliche 2-Ebenen, jeweils die oberen und unteren Höhe der Cloud als auch die Dichte der Cloud für jede Zelle des Rasters. Die Verarbeitung der Daten wurde in einer Cloud-Info-Textur, in dem jede Komponente in der Rot, Grün und Blau-Komponente der Textur für den leichteren Zugriff auf die GPU gespeichert wurde.

## <a name="geometry-clouds"></a>Geometry-clouds

Um sicherzustellen, dass es sich bei unseren Computern mit geringerer Leistung behandeln u. u. unsere Clouds, die wir uns, für den Einstieg entschieden ein Ansatz, der Volumengeometrie verwenden würden, minimieren-Elements zu überzeichnen.

Wir haben zunächst versucht, Clouds erstellen, generieren Sie ein solid Heightmap-Mesh für jede Ebene, verwenden den Radius der Cloud Informationen Textur pro Vertex zum Generieren von der Form. Einen Geometrie-Shader verwendet, um die Scheitelpunkte, die sowohl auf dem oberen und unteren Rand der Cloud generieren solide Formen zu erstellen. Die Dichtewert in der Textur verwendet auf die Farbe von der Cloud mit dunklere Farben für weitere Dichte Clouds.

**Shader für die Scheitelpunkte erstellen:**

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

Wir eingeführt, eine kleine Rauschen-Muster, um weitere Details über die echten Daten zu erhalten. Round Cloud Kanten erzeugt werden, abgeschnitten wir die Pixel in der Pixel-Shader, wenn der interpolierte Radiuswert einen Schwellenwert an, in der Nähe von NULL-Werte verwerfen erreicht.

![Geometry-clouds](images/datascape-geometry-clouds-700px.jpg)

Da die Clouds Volumengeometrie sind, können sie vor dem Gelände alle kostspielig Landkarte Pixel unterhalb ausblenden, um die Framerate weiter zu verbessern gerendert werden. Diese Lösung wurde auch für alle Grafikkarten min-Spezifikation, High-End-Grafikkarten sowie für HoloLens, aufgrund der Solid Geometry Rendern Ansatz ausgeführt.

## <a name="solid-particle-clouds"></a>Solid Partikel clouds

Wir mussten jetzt eine sicherungslösung, die erzeugt einer ordentliche Darstellung unserer Cloud-Daten, jedoch wurde ein wenig unrühmliche in der Faktor "toll" und das volumetrische Verhalten, das wir für unsere High-End-Computer sollten keine vermittelt.

Im nächsten Schritt wurde die Clouds erstellen, indem Sie mit ca. 100.000 Partikel auf ein natürliches und volumetrische Einblick zu gewinnen darstellt werden.

Wenn Partikel solid bleiben und von vorne, hinten sortieren, können wir trotzdem davon profitieren Tiefe Puffer culling der Pixel hinter zuvor gerenderte Partikel, reduzieren die Überzeichnung. Darüber hinaus können wir mit einer Partikel basierende Lösung, die Menge der Partikel verwendet, um verschiedene Zielhardware ändern. Allerdings müssen alle Pixel weiterhin Tiefe getestet, dies führt zu etwas zusätzlichem Aufwand verbunden werden.

Zunächst haben wir Partikelpositionen, um den Mittelpunkt der Benutzeroberfläche beim Start erstellt. Wir verteilt die Partikel intensiver um den Mittelpunkt und weniger daher bei der Entfernung. Wir sortiert alle Partikel aus dem Center in den Hintergrund vorab, sodass die nächste Partikel zunächst gerendert werden kann.

Ein Compute-Shader würde Beispiele für die Textur Cloud Informationen, um jedes einzelne Partikel auf eine korrekte Höhe und die Farbe die Dichte der zugrunde liegenden zu positionieren.

Wir verwendeten *DrawProcedural* zum Rendern des Gevierts pro Partikel, sodass diese Partikel bleiben Sie auf der GPU überhaupt ein Timeout.

Jedes einzelne Partikel enthalten sind, eine Höhen- und eine Radius. Die Höhe wurde basierend auf den clouddaten, die in der Cloud-Info-Textur entnommen, und der Radius basiert auf der ursprünglichen Verteilung, in dem er berechnet werden würde, um den horizontalen Abstand und die nächsten benachbarten Element zu speichern. Die Quads, würden diese Daten verwenden, um orientieren sich selbst durch die Höhe Winkel geändert, damit die Benutzer sich bei horizontal darstellen würde die Höhe angezeigt werden, und wenn Benutzer sich von oben nach unten gesucht werden soll, würde der Bereich zwischen seinen Nachbarn abgedeckt werden.

![Particle Form](images/particle-shape-700px.png)

**Shader-Code zeigt die Verteilung:**

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

Da wir die Partikel Vordergrund-Hintergrund sortieren, und wir weiterhin verwendet einen Stil durchgehend Shader auf transparente Pixel Clip (nicht "Blend"), verarbeitet diese Technik überraschend viel Partikel, vermeiden kostspielige zu zeichnen, sogar auf den Computern mit geringerer Leistung behandeln.

## <a name="transparent-particle-clouds"></a>Transparente Partikel clouds

Die solid Partikel einen natürliches guten Überblick mit der Form der Clouds bereitgestellt, aber noch benötigt etwas zu verkaufen die Fluffiness Clouds. Wir entschieden, eine benutzerdefinierte Lösung für die High-End-Grafikkarten, versuchen Sie es, in dem wir Transparenz führen kann.

Diesen Schritt ausführen, wir einfach die anfängliche Sortierreihenfolge der Partikel gewechselt und den Shader Verwendung der Alphawert Texturen geändert.

![Fluffy clouds](images/fluffy-clouds-700px.jpg)

Es sahen Sie großartig jedoch erwies sich als zu groß für sogar die anspruchsvollsten Computer, da es kommt rendering jedes Pixel auf dem Bildschirm Hunderte Male!

## <a name="render-off-screen-with-lower-resolution"></a>Rendern Sie mit niedrigerer Auflösung außerhalb des Bildschirms

Um die Anzahl der Pixel gerendert wird, von der Cloud zu verringern, haben wir angefangen Rendern sie in einem Quartal Auflösung Puffer (verglichen mit dem Bildschirm) und das Endergebnis Strecken Sichern auf dem Bildschirm nach aller Partikel gezeichnet wurden, mussten. Dies gibt uns ungefähr eine 4 X Beschleunigung, aber es kam mit einigen Einschränkungen.

**Der Code für das Rendern außerhalb des Bildschirms:**

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

Zunächst verloren beim rendering in einem offscreenpuffer wir alle ausführliche Informationen über unsere wichtigsten Szene, wodurch Partikel hinter Berge Rendering über die riesige Menge.

Strecken des Puffers wurde andererseits auch Elemente an den Rändern des unsere Clouds, in dem die Änderung der Auflösung merkliche wurde. Wie wir diese Probleme gelöst, ist in den nächsten beiden Abschnitten erläutert.

## <a name="particle-depth-buffer"></a>Particle Tiefenpuffer

Damit wird die Partikel, mit die Weltgeometrie gleichzeitig vorhanden sein, in denen konnte eine Mountain oder ein Objekt Partikel dahinter abdecken, aufgefüllt wir den außerhalb des Bildschirms Puffer mit einer Tiefenpuffer, die die Geometrie der wichtigsten Szene enthält. Um solche Tiefenpuffer zu erstellen, haben wir eine zweite Kamera, nur die Volumengeometrie und Tiefe der Szene gerendert.

Wir verwendet die neue Textur klicken Sie dann in den Pixel-Shader-Clouds, um die Pixel verdeckt. Berechnet den Abstand der Geometrie hinter einem Cloud-Pixel verwendet derselben Textur. Durch diese Bereiche verwenden und diese für den Alphawert des Pixels zu übernehmen, mussten wir nun die Auswirkungen von Clouds ausgeblendet wird, wie sie in der Nähe Terrain erhalten, entfernen alle schwer Schnitte Partikel und Gelände, in denen zu erfüllen.

![Clouds in Terrain gemischt](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a>Die Ränder Schärfe

Die gestreckt von Clouds fast identisch mit die normale Größe-Clouds in der Mitte der Partikel gesucht oder wo sie überlappende, jedoch einige Elemente an den Kanten Cloud wurde gezeigt. Klicken Sie andernfalls scharfe Kanten würde unscharf angezeigt, und Alias Auswirkungen wurden eingeführt, wenn die Kamera verschoben.

Dies lösten wir mit einem einfachen Shader im Puffer außerhalb des Bildschirms, um zu bestimmen, wo große Änderungen im Gegensatz dazu (1) aufgetreten ist. Wir sollen die Pixel mit großen Änderungen in eine neue Schablone-Puffer (2). Verwendet dann den Stencilpuffer Maske sich diese Bereiche von hohem Kontrast beim Anwenden der offscreenpuffer auf dem Bildschirm, was Löcher in und um die Clouds (3).

Wir dann gerendert aller Partikel erneut in den Vollbildmodus, aber diesmal verwendet den Stencilpuffer Maske, alles die Ränder, was einen minimalen Satz von Pixeln verwendet (4). Da der Befehlspuffer für das Partikel bereits erstellt wurde, mussten wir einfach erneut auf die neue Kamera zu rendern.

![Fortschritt des rendering Cloud Kanten](images/cloud-steps-1-4-700px.jpg)

Das Ergebnis war, scharfe Kanten mit günstig Center Abschnitten der Clouds.

War dies viel schneller als Rendern alle Partikel im Vollbild, besteht immer noch eine Pixel für den Stencilpuffer testen, damit eine große Zahl von Überzeichnung weiterhin Kosten mit Kosten stammt.

## <a name="culling-particles"></a>Culling Partikel

Für unsere Effekt Wind generiert wir lange Dreieck Streifen im Compute-Shader, erstellen viele Wisps des Wind in der ganzen Welt. Während die Wind Auswirkungen nicht viel Füllrate aufgrund aus erster Hand leisten, die generiert wurde, erzeugt es vielen Hunderten oder Tausenden von Vertices, die in einer hohen Auslastung für den Vertex-Shader resultieren.

Wir eingeführt anfügen Puffer auf den Compute-Shader zum Übertragen von einer Teilmenge der Wind leisten, gezeichnet werden soll. Mit einigen einfachen Ansicht Frustums Cullingverfahren Logik im Compute-Shader können wir bestimmen, ob ein Streifen außerhalb der Kameraansicht ist und verhindern, dass er auf den Push-Puffer hinzugefügt werden. Dies reduziert die Menge der Streifen erheblich freizugeben, einige erforderlichen Zyklen in der GPU.

**Der Code veranschaulicht einen Anfügepuffer:**

*Compute-Shader:*

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

*C#Code:*

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

Wir haben versucht, mit derselben Technik für die Cloud-Partikel, auf würden sie auf den Compute-Shader zu reduzieren und nur mithilfe von Push übertragen die sichtbaren Partikel gerendert werden soll. Dieses Verfahren tatsächlich nicht uns speichern auf der GPU, da der größte Engpass Menge Pixel gerendert wird, auf dem Bildschirm und nicht die Kosten für die Scheitelpunkte berechnet wurde.

Das andere Problem mit diesem Verfahren war, dass der Append-Puffer in zufälliger Reihenfolge aufgrund seiner parallelisierten Natur des Computings die Partikel, verursacht die sortierten Partikel soll nicht sortiert sind, was zu Flimmern Cloud Partikel aufgefüllt.

Es gibt Methoden, um die Push-Puffer zu sortieren, aber die begrenzte Menge an Leistungsgewinn, die wir aus dem Partikel culling rehabilitationszentrum würde wahrscheinlich mit einer zusätzlichen Sortierung versetzt werden, damit wir uns entschieden, diese Optimierung nicht zu verfolgen.

## <a name="adaptive-rendering"></a>Adaptive rendering

Um eine stetige Framerate für eine app mit unterschiedlichen Rendern Bedingungen wie ein bewölkt Visual Studio ein klares Bild zu gewährleisten, haben wir für unsere Anwendung adaptives Rendering eingeführt.

Der erste Schritt des adaptive Rendering ist GPU zu messen. Dies haben wir durch Einfügen von benutzerdefinierten Code in den GPU-Befehlspuffer am Anfang und Ende einer gerenderte Frame, erfassen sowohl die linken und rechten-Augen-Bildschirm Zeit.

Durch das Messen Zeit die Rendern und durch Vergleichen mit unserer gewünschten-Aktualisierungsrate, die wir einen Überblick darüber hier, wie nahe wir waren, um Frames zu löschen.

Wenn in der Nähe Frames gelöscht wird, passen wir unsere rendern, um ihn schneller zu machen. Eine einfache Möglichkeit zur Anpassung der ändert der Viewportgröße des Bildschirms, erfordert weniger Pixel gerendert wird, erhalten.

Mithilfe von *UnityEngine.XR.XRSettings.renderViewportScale* das System gezielten Viewport verkleinert und gestreckt wird, das Ergebnis zurück bis zum Anpassen der Bildschirm automatisch. Eine kleine Änderung der Skalierung ist für die Weltgeometrie unauffällig und ein Skalierungsfaktor von 0,7 erfordert die Hälfte der Pixel gerendert werden soll.

![70 % skalieren, die Hälfte der Pixel](images/datascape-scaling-700px.jpg)

Wenn festgestellt wird, dass wir sind zum Löschen des Frames, die wir die Skalierung um eine feste Anzahl verringern, und erhöhen sie sichern können, wenn wir schnell genug erneut ausgeführt werden.

Während wir uns entschieden, welche Cloud-Technik, mit Grafiken Funktionen der Hardware beim Start abhängig, es möglich ist, die sie als Grundlage für die Daten aus der GPU-Messung, um zu verhindern, dass das System mit geringer Auflösung lange bleiben, aber dies wir keine Zeit haben  Um in Datascape zu untersuchen.

## <a name="final-thoughts"></a>Abschließende betrachtungen

Eine Vielzahl von Hardware ist schwierig und erfordert eine gewisse Planung.

Es wird empfohlen, dass Sie starten auf unteren-gestützte Computer so, dass vertraut mit den Problembereich und entwickeln eine sicherungslösung, die auf allen Computern ausgeführt werden. Entwerfen Sie Ihre Lösung mit Füllrate Denken Sie daran, da Pixel Ihrer wertvollsten Ressourcen sein werden. Ziel-Volumengeometrie über Transparenz.

Mit einer sicherungslösung klicken Sie dann Schichten in höhere Komplexität für high-End-Computer starten oder vielleicht einfach Auflösung sicherungslösung verbessern.

Für den ungünstigsten Fall entwerfen, und vielleicht verwenden Sie ggf. adaptives Rendering für hohe Situationen.

## <a name="about-the-authors"></a>Über die Autoren

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><b>Robert Ferrese</b><br>Anwendungsentwickler @Microsoft</td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><b>Dan Andersson</b><br>Anwendungsentwickler @Microsoft</td>
</tr>
</table>


## <a name="see-also"></a>Siehe auch
* [Grundlegendes zur Leistung für Mixed Reality](understanding-performance-for-mixed-reality.md)
* [Empfehlungen zur Leistung für Unity](performance-recommendations-for-unity.md)

 
