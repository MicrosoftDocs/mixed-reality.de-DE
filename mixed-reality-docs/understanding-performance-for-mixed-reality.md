---
title: Grundlegendes zur Leistung für gemischte Realität
description: Erweiterte Themen und Details zur Optimierung der Leistung für Windows Mixed Reality-apps
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Gemischte Windows-Realität, gemischte Realität, Virtual Reality, VR, Mr, Leistung, Optimierung, CPU, GPU
ms.openlocfilehash: ce59f9023c21dc7c981a2bb97d9fbd0c57622dbf
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548841"
---
# <a name="understanding-performance-for-mixed-reality"></a>Grundlegendes zur Leistung für gemischte Realität

Dieser Artikel ist eine Einführung in die Rationalisierung der Bedeutung der Leistung für ihre gemischte Reality-app.  Die Benutzer Leistung kann erheblich beeinträchtigt werden, wenn Ihre Anwendung nicht mit optimaler Framerate ausgeführt wird. Holograms werden instabil angezeigt, und die Kopf Nachverfolgung der Umgebung ist ungenau, was zu einer mangelnden Benutzerumgebung führt. Tatsächlich muss die Leistung als First-Class-Feature für die Entwicklung gemischter Realität und nicht für eine Stabilisierung-, Ende-zu-Ende-Aufgabe angesehen werden.

Zur Überprüfung werden die leistungsstarken Framerate-Werte für jede Zielplattform unten aufgeführt.

| Platform | Zielframe Rate |
|----------|-------------------|
| [HoloLens](hololens-hardware-details.md) | 60 FPS |
| [Windows Mixed Reality Ultra PCs](immersive-headset-hardware-details.md) | 90 FPS |
| [Windows Mixed Reality-PCs](immersive-headset-hardware-details.md) | 60 FPS |

Das unten stehende Framework bietet eine allgemeine Übersicht über bewährte Methoden und Erkenntnisse zum Erreichen von Ziel Frameraten. Weitere Informationen zu den Details finden Sie im [Artikel Leistungs Empfehlungen für Unity](performance-recommendations-for-unity.md). Insbesondere wird in diesem Artikel erläutert, wie Sie die Framerate in ihrer Unity Windows Mixed Reality-App Messen und welche Schritte in der Unity-Umgebung ausgeführt werden müssen, um die Leistung zu verbessern.

## <a name="understanding-performance-bottlenecks"></a>Grundlegendes zu Leistungs Engpässen

Wenn Ihre APP einen leistungsstarken Framerate hat, besteht der erste Schritt darin, zu analysieren und zu verstehen, wo Ihre Anwendung Rechen intensiv ist. Es gibt zwei primäre Prozessoren, die für die Arbeit zum Rendering Ihrer Szene verantwortlich sind: die CPU und die GPU. Jede dieser beiden Komponenten verarbeitet verschiedene Vorgänge und Phasen ihrer Mixed Reality-app. Es gibt drei wichtige Orte, an denen Engpässe auftreten können. 

1. **App-Thread-CPU** : dieser Thread ist für Ihre APP-Logik verantwortlich. Dies umfasst die Verarbeitung von Eingaben, Animationen, Physik und anderen APP-Logik/-Zuständen.
2. **Thread-CPU zu GPU rentieren** : dieser Thread ist für das übermitteln der Draw-Aufrufe an die GPU verantwortlich. Wenn Ihre APP ein Objekt (z. b. einen Cube oder ein Modell) rendern möchte, sendet dieser Thread eine Anforderung an die GPU, die über eine für das Rendering optimierte Architektur verfügt, um diese Vorgänge auszuführen.
3. **GPU** - 
    Dieser Prozessor verarbeitet am häufigsten die Grafik Pipeline Ihrer Anwendung, um 3D-Daten (Modelle, Texturen usw.) in Pixel umzuwandeln, und erzeugt schließlich ein 2D-Bild, das an den Bildschirm Ihres Geräts gesendet wird.

![Lebensdauer eines Frames](images/lifetime-of-a-frame.png)

Im Allgemeinen werden hololens-Anwendungen an GPU gebunden. Dies gilt jedoch nicht für jede Anwendung. Daher wird empfohlen, die Tools & Techniken unten zu verwenden, um die grundlegenden Informationen für Ihre APP zu erhalten.

## <a name="how-to-analyze-your-application"></a>Analysieren der Anwendung

Es gibt viele Tools, mit denen Sie als Entwickler das Leistungsprofil Ihrer gemischten Reality-Anwendung verstehen können. Diese ermöglichen es Ihnen, sowohl für Engpässe als auch für das Debuggen zu dienen.

Dies ist eine Liste beliebter und leistungsfähiger Tools, mit denen Sie umfassende Profil Erstellungs Informationen für Ihre Anwendung erhalten.
- [Intel Graphics Performance Analyzer](https://software.intel.com/gpa)
- [Visual Studio-Grafik-Debuggers](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [Unity-Profiler](https://docs.unity3d.com/Manual/Profiler.html)
- [Unity-Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a>Profilerstellung in einer beliebigen Umgebung

Es gibt einen einfachen Test, mit dem Sie schnell feststellen können, ob Sie in Ihrer Anwendung wahrscheinlich eine GPU-Grenze oder eine CPU-Begrenzung Wenn Sie die Auflösung der Ausgabe des Renderziels verringern, sind weniger Pixel zu berechnen und somit weniger Arbeit, die die GPU zum renderingabbild ausführen muss. Die viewportskalierung (Skalierung dynamischer Lösungen) ist die Vorgehensweise, das Bild in ein kleineres Renderziel zu rendern, und das Ausgabegerät kann angezeigt werden. Das Gerät wird aus dem kleineren Satz von Pixeln hochskalieren, um das endgültige Bild anzuzeigen.

Nach dem verringern der renderinglösung:
1) Anwendungs Framerate **erhöht**sich, dann ist die **GPU wahrscheinlich begrenzt**
1) Die Anwendungs Framerate ist **unverändert**, und Sie sind wahrscheinlich **CPU-gebunden** .

>[!NOTE]
>Unity bietet die Möglichkeit, die renderzielauflösung Ihrer Anwendung zur Laufzeit mithilfe der *[xrsettings. renderviewportscale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* -Eigenschaft problemlos zu ändern. Das endgültige Bild, das auf dem Gerät angezeigt wird, hat eine Fehlerbehebung. Die Plattform zeigt eine Stichprobe der Ausgabe mit niedrigerer Auflösung an, um ein höheres Auflösungs Bild für das Rendering in anzeigen zu erstellen. 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>So verbessern Sie Ihre Anwendung

### <a name="cpu-performance-recommendations"></a>Empfehlungen zur CPU-Leistung

Im allgemeinen umfasst die meiste Arbeit in einer gemischten Reality-Anwendung auf der CPU das Ausführen der Simulation der Szene und die Verarbeitung umfangreicher eindeutiger Anwendungslogik. Daher sind die folgenden Bereiche in der Regel für die Optimierung bestimmt.

- Animationen
- Vereinfachen der Physik
- Speicher Belegungen
- Komplexe Algorithmen (d. h. umgekehrte Kinematik, Pfad Suche)

### <a name="gpu-performance-recommendations"></a>Empfehlungen zur GPU-Leistung

#### <a name="understanding-bandwidth-vs-fill-rate"></a>Grundlegendes zur Bandbreiten Vergleich
Wenn ein Frame auf der GPU gerendert wird, wird eine Anwendung im Allgemeinen entweder durch die Arbeitsspeicher Bandbreite oder die Füllrate begrenzt.

- Die Arbeits **Speicherbandbreite** ist die Rate der Lese-und Schreibvorgänge, die die GPU aus dem Arbeitsspeicher
    - Um Bandbreiten Einschränkungen zu identifizieren, verringern Sie die Texturqualität und überprüfen, ob Framerate verbessert wurde.
    - In Unity kann dies durch Ändern der **Texturqualität** in "**Projekteinstellungen** >  **Bearbeiten** > " **[Qualitätseinstellungen](https://docs.unity3d.com/Manual/class-QualitySettings.html)** geändert werden.
- **Füllrate** bezieht sich auf den Durchsatz gerenderter Pixel, die pro Sekunde von der GPU gezeichnet werden können.
    - Um die Einschränkungen der Füllrate zu identifizieren, verringern Sie die Bildschirmauflösung, und prüfen Sie, ob Framerate verbessert wurde 
    - In Unity kann dies über die *[xrsettings. renderviewportscale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* -Eigenschaft erfolgen.

Die Speicherbandbreite umfasst in der Regel Optimierungen für
1) Verkleinern von Textur Auflösungen
2) weniger Texturen verwenden (d. h. normale, Glanz usw.)

Die Füllrate konzentriert sich hauptsächlich auf das Reduzieren der Anzahl von Vorgängen, die für ein letztes gerendertes Pixel berechnet werden müssen. Beispiele hierfür liegen häufig in der Reduzierung von
1) Anzahl der zu Rendering/zu verarbeitenden Objekte
2) Anzahl von Vorgängen pro Shader
3) Anzahl von GPU-Phasen bis zum Endergebnis (Geometry-Shader, nach Verarbeitungs Effekte usw.)
4) Anzahl der zu Rendering enden Pixel (d. h. Anzeige Auflösung)

#### <a name="reduce-poly-count"></a>Reduzieren der polyzahl
Höhere Polygon Zahlen führen zu mehr Vorgängen für die GPU, und das Reduzieren der Anzahl von Polygonen in der Szene verringert die Zeitspanne, die für das Rendering der Geometrie gilt. Es gibt auch andere Faktoren, die bei der Schattierung der Geometrie zu berücksichtigen sind, die noch teuer sein kann, aber die Polygon Anzahl ist die Basis Metrik, um zu bestimmen, wie teuer eine Szene sein wird.

#### <a name="limit-overdraw"></a>Limit überzeichnen

Eine hohe Überschreibung tritt auf, wenn mehrere Objekte gerendert werden, aber nicht auf dem Bildschirm ausgegeben werden, da Sie von einem anderen, in der Regel engeren, nicht aufgeblendeten Objekt Stellen Sie sich vor, dass Sie eine Wand sehen, die mehrere Räume und Geometrie dahinter enthielt. Die gesamte Geometrie würde zum Rendern verarbeitet, aber nur die nicht transparente Wand muss tatsächlich gerendert werden, da Sie die Ansicht aller anderen Inhalte verbleibt. Dies führt zu verschwenderischen Vorgängen, die für die aktuelle Ansicht nicht benötigt werden.

#### <a name="shaders"></a>Shader

Shader sind kleine Programme, die auf der GPU ausgeführt werden und im Allgemeinen zwei wichtige Schritte beim Rendering bestimmen:
1) die Scheitel Punkte des Objekts, die auf dem Bildschirm gezeichnet werden sollen, und wo Sie sich auf dem Bildschirmbereich befinden (d.h. der Vertex-Shader)
    - Der Vertex-Shader wird im allgemeinen pro Scheitelpunkt für jedes gameobject-Objekt ausgeführt.
2) Farbe der Pixel (d. h. der Pixelshader)
    - Der Pixelshader wird pro Pixel für die Textur ausgeführt, die für das Gerät gerendert wird.

In der Regel führen Shader viele Transformationen und Beleuchtungsberechnungen durch. Obwohl komplexe Beleuchtungs Modelle, Schatten und andere Vorgänge tolle Ergebnisse erzeugen können, erhalten Sie auch einen Preis. Durch das Reduzieren der Anzahl von Vorgängen, die in Shader berechnet werden, kann die Gesamtarbeit, die für eine GPU pro Frame erforderlich ist, erheblich reduziert werden.

##### <a name="shader-coding-recommendations"></a>Codierungs Empfehlungen für Shader

- Verwenden Sie nach Möglichkeit die bilineare Filterung
- Neuanordnung von Ausdrücken zur Verwendung von verrückten systeminternen Funktionen, um eine Multiplikation und ein hinzufügen gleichzeitig durchzuführen
- So weit wie möglich auf der CPU vorab berechnen und als Konstanten an das Material übergeben
- **Verschieben von Vorgängen vom Pixelshader zum Vertex-Shader bevorzugen**
    - Im Allgemeinen ist die Anzahl der Scheitel Punkte < < Anzahl von Pixeln (d. h. 720p = = 921.600 Pixel, 1080p = = 2.073.600 Pixel usw.)

#### <a name="remove-gpu-stages"></a>Entfernen von GPU-Stufen
Die Auswirkungen nach der Verarbeitung können sehr kostspielig sein und die Füllrate der Anwendung im allgemeinen behindern. Dies umfasst auch Antialiasing-Techniken wie z. b. MSAA. Bei hololens empfiehlt es sich, diese Techniken vollständig zu vermeiden. Darüber hinaus sollten weitere shaderphasen wie Geometrie, Hülle und Compute-Shader möglichst vermieden werden.

## <a name="memory-recommendations"></a>Speicher Empfehlungen
Eine übermäßige Speicher Belegung & Zuordnungs Vorgängen kann negative Auswirkungen auf Ihre Holographic-Anwendung haben, was zu inkonsistenter Leistung, fixierten Frames und anderem schädlichen Verhalten führt. Es ist besonders wichtig, die Arbeitsspeicher Aspekte zu verstehen, wenn Sie in Unity entwickeln, da die Speicherverwaltung durch die Garbage Collector gesteuert wird.

#### <a name="object-pooling"></a>Objekt Pooling

Objekt Pooling ist eine gängige Methode, um die Kosten für fortlaufende Zuordnungen & die Zuordnung von Objekten zu reduzieren. Dies erfolgt durch Zuordnen eines großen Pools identischer Objekte und erneutes verwenden inaktiver, verfügbarer Instanzen aus diesem Pool, anstatt ständig Objekte im Zeitverlauf zu erzeugen und zu zerstören. Objekt Pools eignen sich hervorragend für wiederverwendbare Komponenten, die während einer APP über eine Variablen Lebensdauer verfügen.

## <a name="see-also"></a>Siehe auch
- [Leistungsempfehlungen für Unity](performance-recommendations-for-unity.md)
- [Empfohlene Einstellungen für Unity](recommended-settings-for-unity.md)
