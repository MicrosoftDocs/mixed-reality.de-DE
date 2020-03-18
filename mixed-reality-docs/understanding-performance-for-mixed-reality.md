---
title: Grundlegendes zur Leistung für gemischte Realität
description: Erweiterte Themen und Details zur Optimierung der Leistung für Windows Mixed Reality-apps
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Gemischte Windows-Realität, gemischte Realität, Virtual Reality, VR, Mr, Leistung, Optimierung, CPU, GPU
ms.openlocfilehash: 287b95363acff00ab7a0407475e0a419fc076611
ms.sourcegitcommit: 184227dc591ca2791f523d520555730ba1e95b5c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79479573"
---
# <a name="understanding-performance-for-mixed-reality"></a>Grundlegendes zur Leistung für gemischte Realität

Dieser Artikel ist eine Einführung in das Verständnis der Bedeutung der Leistung für ihre gemischte Reality-app.  Die Benutzer Leistung kann erheblich beeinträchtigt werden, wenn Ihre Anwendung nicht mit optimaler Framerate ausgeführt wird. Holograms werden instabil angezeigt, und die Kopf Nachverfolgung der Umgebung ist ungenau, was zu einer mangelnden Benutzerumgebung führt. Die Leistung muss als erstklassige Funktion für die Entwicklung in gemischter Realität und nicht als polnische Aufgabe angesehen werden.

Die leistungsstarken Framerate-Werte für jede Zielplattform sind unten aufgeführt.

| Plattform | Zielframe Rate |
|----------|-------------------|
| [HoloLens](hololens-hardware-details.md) | 60 FPS |
| [Windows Mixed Reality Ultra PCs](immersive-headset-hardware-details.md) | 90 fps |
| [Windows Mixed Reality-PCs](immersive-headset-hardware-details.md) | 60 FPS |

Im folgenden Framework werden bewährte Methoden zum Erreichen von Ziel Frameraten beschrieben. Wenn Sie in Unity entwickeln, sollten Sie den [Artikel Leistungs Empfehlungen für Unity](performance-recommendations-for-unity.md) lesen, um Tipps zum Messen und verbessern der Framerate in der Unity-Umgebung zu erhalten.

## <a name="understanding-performance-bottlenecks"></a>Grundlegendes zu Leistungs Engpässen

Wenn Ihre APP einen leistungsstarken Framerate hat, besteht der erste Schritt darin, zu analysieren und zu verstehen, wo Ihre Anwendung Rechen intensiv ist. Es gibt zwei primäre Prozessoren, die für die Arbeit zum Rendering Ihrer Szene verantwortlich sind: die CPU und die GPU. Jede dieser Anwendungen behandelt verschiedene Aspekte ihrer Mixed Reality-app. Es gibt drei wichtige Orte, an denen Engpässe auftreten können: 

1. **App-Thread-CPU** : dieser Thread ist für Ihre APP-Logik verantwortlich. Dies umfasst die Verarbeitung von Eingaben, Animationen, Physik und anderen APP-Logik.
2. **Thread-CPU zu GPU rentieren** : dieser Thread ist für das übermitteln der Draw-Aufrufe an die GPU verantwortlich. Wenn Ihre APP ein Objekt (z. b. einen Cube oder ein Modell) renderingfähig ist, sendet dieser Thread eine Anforderung an die GPU, um diese Vorgänge auszuführen.
3. **GPU** : Dieser Prozessor verarbeitet am häufigsten die Grafik Pipeline Ihrer Anwendung, um 3D-Daten (Modelle, Texturen usw.) in Pixel umzuwandeln. Letztendlich wird ein 2D-Image erstellt, das an den Bildschirm Ihres Geräts gesendet wird.

![Lebensdauer eines Frames](images/lifetime-of-a-frame.png)

Im Allgemeinen werden hololens-Anwendungen GPU-gebunden, aber nicht immer. Verwenden Sie die unten aufgeführten Tools und Verfahren, um zu verstehen, wo ihre jeweilige App Engpässe hat.

## <a name="how-to-analyze-your-application"></a>Analysieren der Anwendung

Es gibt viele Tools, mit denen Sie das Leistungsprofil Ihrer gemischten Reality-Anwendung verstehen können. Diese ermöglichen es Ihnen, herauszufinden, wo und warum Sie Engpässe haben, damit Sie Sie beheben können.

Im folgenden finden Sie einige gängige Tools, mit denen Sie umfassende Profil Erstellungs Informationen für Ihre Anwendung erhalten
- [Intel Graphics Performance Analyzer](https://software.intel.com/gpa)
- [Visual Studio-Grafik-Debuggers](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [Unity-Profiler](https://docs.unity3d.com/Manual/Profiler.html)
- [Unity-Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a>Profilerstellung in einer beliebigen Umgebung

Eine Möglichkeit, um zu bestimmen, ob Sie in Ihrer Anwendung GPU-gebunden oder CPU-gebunden sind, besteht darin, die Auflösung der Ausgabe des Renderziels zu verringern. Wenn Sie die Anzahl der zu berechnenden Pixel verringern, wird die GPU-Auslastung dadurch reduziert. Das Gerät wird in eine kleinere Textur und dann up-Sample angezeigt, um das endgültige Bild anzuzeigen.

Nach dem verringern der renderinglösung:
1) Die Anwendungs Framerate **nimmt**zu, Sie sind wahrscheinlich **an GPU gebunden** .
1) Die Anwendungs Framerate ist **unverändert**, und Sie sind wahrscheinlich **CPU-gebunden** .

>[!NOTE]
>Unity bietet die Möglichkeit, die renderzielauflösung Ihrer Anwendung zur Laufzeit mithilfe der *[xrsettings. renderviewportscale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* -Eigenschaft problemlos zu ändern. Das endgültige Bild, das auf dem Gerät angezeigt wird, hat eine Fehlerbehebung. Die Plattform zeigt eine Stichprobe der Ausgabe mit niedrigerer Auflösung an, um ein höheres Auflösungs Bild für das Rendering in anzeigen zu erstellen. 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>So verbessern Sie Ihre Anwendung

### <a name="cpu-performance-recommendations"></a>Empfehlungen zur CPU-Leistung

Im allgemeinen umfasst die meiste Arbeit in einer gemischten Reality-Anwendung auf der CPU das Ausführen der Simulation der Szene und die Verarbeitung der Anwendungslogik. Die folgenden Bereiche sind in der Regel für die Optimierung bestimmt:

- Animationen
- Mikro
- Speicher Belegungen
- Komplexe Algorithmen (d. h. umgekehrte Kinematik, Pfad Suche)

### <a name="gpu-performance-recommendations"></a>Empfehlungen zur GPU-Leistung

#### <a name="understanding-bandwidth-vs-fill-rate"></a>Grundlegendes zur Bandbreite im Vergleich zu Füll Raten
Wenn ein Frame auf der GPU gerendert wird, wird eine Anwendung im Allgemeinen entweder durch die Arbeitsspeicher Bandbreite oder die Füllrate gebunden.

- Die Arbeits **Speicherbandbreite** ist die Rate der Lese-und Schreibvorgänge, die die GPU aus dem Arbeitsspeicher
    - Um Bandbreiten Einschränkungen zu identifizieren, verringern Sie die Texturqualität, und prüfen Sie, ob die Framerate verbessert wurde.
    - In Unity kann dies durch Ändern der **Texturqualität** in **Edit** > **Project Settings** >  **[Quality Settings](https://docs.unity3d.com/Manual/class-QualitySettings.html)** erreicht werden.
- **Füllrate** bezieht sich auf die Pixel, die pro Sekunde von der GPU gezeichnet werden können.
    - Um die Einschränkungen der Füllrate zu identifizieren, verringern Sie die Bildschirmauflösung, und prüfen Sie, ob Framerate verbessert wurde 
    - In Unity kann dies über die *[xrsettings. renderviewportscale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* -Eigenschaft erfolgen.

Die Speicherbandbreite umfasst in der Regel Optimierungen für:
1) Verkleinern von Textur Auflösungen
2) Verwenden Sie weniger Texturen (normale, Glanz usw.).

Die Füllrate konzentriert sich auf die Reduzierung der Anzahl von Vorgängen, die für ein letztes gerendertes Pixel berechnet werden müssen. Dies schließt Folgendes ein:
1) Anzahl der zu Rendering/zu verarbeitenden Objekte
2) Anzahl von Vorgängen pro Shader
3) Anzahl von GPU-Phasen bis zum Endergebnis (Geometry-Shader, nach Verarbeitungs Effekte usw.)
4) Anzahl der zu Rendering enden Pixel (Anzeige Auflösung)

#### <a name="reduce-polygon-count"></a>Reduzieren der Polygon Anzahl

Höhere Polygon Zahlen führen zu weiteren Vorgängen für die GPU. Wenn Sie [die Anzahl von Polygonen](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) in der Szene verringern, wird die Rendering-Zeit reduziert. Beim schattieren der Geometrie gibt es weitere Faktoren, die teuer sein können, aber die Polygon Anzahl ist die einfachste Metrik, um zu bestimmen, wie teuer eine Szene sein wird.

#### <a name="limit-overdraw"></a>Limit überzeichnen

Ein hoher Alphablendings tritt auf, wenn mehrere Objekte gerendert, jedoch nicht auf dem Bildschirm angezeigt werden, da Sie durch ein okding Objekt ausgeblendet werden. Stellen Sie sich vor, eine Wand mit Objekten dahinter zu betrachten. Die gesamte Geometrie würde zum Rendern verarbeitet, aber nur die nicht transparente Wand muss gerendert werden. Dies führt zu unnötigen Vorgängen.

#### <a name="shaders"></a>Shader

Shader sind kleine Programme, die auf der GPU ausgeführt werden und zwei wichtige Schritte zum Rendern ausführen:
1) Bestimmen, welche Scheitel Punkte gezeichnet werden sollen und wo Sie sich im Bildschirmbereich befinden (der Vertexshader)
    - Der Vertex-Shader wird in der Regel pro Scheitelpunkt für jedes Mesh ausgeführt.
2) Bestimmen der Farbe jedes Pixels (Pixelshader)
    - Der Pixelshader wird pro Pixel ausgeführt, das von der Geometrie in der Textur gerendert wird.

In der Regel führen Shader viele Transformationen und Beleuchtungsberechnungen durch. Obwohl komplexe Beleuchtungs Modelle, Schatten und andere Vorgänge tolle Ergebnisse erzeugen können, erhalten Sie auch einen Preis. Durch das Reduzieren der Anzahl von Vorgängen, die in Shadern berechnet werden, kann die für die GPU pro Frame benötigte Arbeit erheblich reduziert werden.

##### <a name="shader-coding-recommendations"></a>Codierungs Empfehlungen für Shader

- Verwenden der bilinearen Filterung, wann immer möglich
- Neuanordnung von Ausdrücken zur Verwendung von verrückten systeminternen Funktionen, um eine Multiplikation und ein hinzufügen gleichzeitig durchzuführen
- So weit wie möglich auf der CPU vorab berechnen und als Konstanten an das Material übergeben
- **Verschieben von Vorgängen vom Pixelshader zum Vertex-Shader bevorzugen**
    - Im Allgemeinen ist die Anzahl der Scheitel Punkte wesentlich kleiner als die Anzahl der Pixel (720p beträgt 921.600 Pixel, 1080p beträgt 2.073.600 Pixel usw.).

#### <a name="remove-gpu-stages"></a>Entfernen von GPU-Stufen

Nach Verarbeitungs Effekte können sehr teuer sein und die Füllrate Ihrer Anwendung erhöhen. Dies schließt Antialiasing-Techniken wie z. b. MSAA ein. Bei hololens empfiehlt es sich, diese Techniken vollständig zu vermeiden, sowie weitere shaderphasen wie Geometrie, Hülle und Compute-Shader.

## <a name="memory-recommendations"></a>Speicher Empfehlungen

Übermäßig hohe Speicher Belegungs-und Aufteilungs Vorgänge können zu inkonsistenter Leistung, fixierten Frames und anderem schädlichen Verhalten führen. Es ist besonders wichtig, die Arbeitsspeicher Aspekte bei der Entwicklung in Unity zu verstehen, da die Speicherverwaltung durch die Garbage Collector gesteuert wird.

#### <a name="object-pooling"></a>Objekt Pooling

Objekt Pooling ist ein gängiges Verfahren, um die Kosten von kontinuierlichen Zuordnungen und Aufhebungen von Objekten zu verringern. Dies erfolgt durch Zuordnen eines großen Pools identischer Objekte und erneutes verwenden inaktiver, verfügbarer Instanzen aus diesem Pool, anstatt ständig Objekte im Zeitverlauf zu erzeugen und zu zerstören. Objekt Pools eignen sich hervorragend für wiederverwendbare Komponenten, die während einer APP über eine Variablen Lebensdauer verfügen.

## <a name="see-also"></a>Siehe auch
- [Leistungsempfehlungen für Unity](performance-recommendations-for-unity.md)
- [Empfohlene Einstellungen für Unity](recommended-settings-for-unity.md)
- [Optimieren von 3D-Modellen](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [Bewährte Methoden zum umrechnen und Optimieren von Echt Zeit 3D-Modellen](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/best-practices)

