---
title: Grundlegendes zur Leistung für Mixed Reality
description: Erweiterte Themen und Informationen zum Optimieren der Leistung für Windows Mixed Reality-Apps
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, virtuelle Realität, VR, MR, Leistung, Optimierung, CPU und GPU
ms.openlocfilehash: ce59f9023c21dc7c981a2bb97d9fbd0c57622dbf
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596075"
---
# <a name="understanding-performance-for-mixed-reality"></a>Grundlegendes zur Leistung für mixed reality

Dieser Artikel ist eine Einführung in die die Bedeutung der Leistung für Ihre Mixed Reality-app zu rationalisieren.  Benutzererfahrung kann erheblich beeinträchtigt sein, wenn Ihre Anwendung nicht auf eine optimale Framerate ausgeführt wird. Hologramme instabil angezeigt, und Head nachverfolgung der Umgebung sind ungenau zu einer schlechten benutzererfahrung führt. In der Tat muss Leistung als erstklassige Feature für Mixed Reality-Entwicklung und keine Stabilisierung, Ende des Zyklus-Vorgangs berücksichtigt werden.

Für die Überprüfung werden die leistungsfähigen Framerate Werte für jede Zielplattform aufgeführt.

| Platform | Ziel-Bildfrequenz |
|----------|-------------------|
| [HoloLens](hololens-hardware-details.md) | 60 FPS |
| [Windows Mixed Reality Ultra-PCs](immersive-headset-hardware-details.md) | 90 FPS |
| [Windows Mixed Reality-PCs](immersive-headset-hardware-details.md) | 60 FPS |

Das folgende Framework bietet einen allgemeine Übersicht über bewährte Methoden und Frameraten als Ziel Kenntnisse zu erreichen. So können Sie weitere Details, sich die [Empfehlungen zur Leistung für Unity-Artikel](performance-recommendations-for-unity.md). Dieser Artikel wird insbesondere von Framerate in Ihrer Unity Windows Mixed Reality-app sowie die Schritte in der Unity-Umgebung zur Verbesserung der Leistung messen erläutert.

## <a name="understanding-performance-bottlenecks"></a>Grundlegendes zu von Leistungsengpässen

Wenn Ihre app eine dieser Framerate aufweist, ist der erste Schritt, zu analysieren und zu verstehen, in denen Ihre Anwendung rechenintensiv ist. Es gibt zwei primäre Prozessoren für die Arbeit zum Rendern der Szene verantwortlich: CPU und GPU. Diese beiden Komponenten verarbeiten unterschiedliche Vorgänge und Phasen Ihrer Mixed Reality-App. Es gibt drei wichtige Orte, wo Engpässe auftreten können. 

1. **App-Thread - CPU** -dieser Thread ist verantwortlich für die app-Logik. Dies schließt die Verarbeitung der Eingabe, Animationen, Physik und andere app-Logik/Status
2. **Thread - CPU und GPU Rendern** -dieser Thread ist verantwortlich für die Übermittlung Ihrer Draw-Aufrufe an die GPU. Wenn Ihre app um ein Objekt z. B. eines Cubes oder Modells zu rendern, sendet dieser Thread eine Anforderung an die GPU, die über eine Architektur, optimiert für das Rendering verfügt, um diese Vorgänge auszuführen.
3. **GPU** - 
    dieser Prozessor am häufigsten behandelt die Grafikpipeline der Anwendung, um Datentransformation 3D (Modelle, Texturen usw.) in Pixel und letztendlich erzielen ein 2D-Bild an den Bildschirm des Geräts übermitteln.

![Lebensdauer eines Frames](images/lifetime-of-a-frame.png)

HoloLens-Anwendungen werden in der Regel GPU begrenzt sein. Allerdings dies errichtet keine in der "true" in jeder Anwendung, und es wird daher empfohlen, die den Tools und Techniken unten verwenden, um für Ihre spezielle app basiswahrheit zu erhalten.

## <a name="how-to-analyze-your-application"></a>Gewusst wie: Analysieren der Anwendung

Es gibt viele Tools, die Ihnen als Entwickler das Leistungsprofil Ihrer Mixed Reality-Anwendung zu ermöglichen. Diese können Sie beide, in dem Sie Engpässe und wie sie selbst, um sie zu debuggen manifestieren sind haben, soll.

Dies ist eine Liste der beliebten und leistungsstarken Tools, um detaillierte Informationen für die profilerstellung für Ihre Anwendung zu erhalten.
- [Intel Grafiken Performance Analyzer](https://software.intel.com/gpa)
- [Visual Studio Grafik-Debugger](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [Unity-Profiler](https://docs.unity3d.com/Manual/Profiler.html)
- [Unity-Frame-Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a>Wie in jeder Umgebung ein Profil erstellen

Es gibt einen einfachen Test können Sie schnell feststellen, wenn Sie wahrscheinlich GPU begrenzt oder CPU, die in Ihrer Anwendung begrenzt. Wenn Sie die Auflösung der renderzielausgabe verringern, es gibt weniger Pixel berechnen, und daher weniger Arbeit die GPU ausgeführt werden, um ein Bild zu rendern muss. Viewport Skalierung (dynamische Auflösung-Skalierung) wird die Vorgehensweise zum Rendern des Bilds in eine kleinere Renderziel und dann Ihr Gerät anzeigen kann. Das Gerät wird nach-oben-aus dem kleineren Satz von Pixeln, um Ihr endgültiges Image anzuzeigen-Beispiel.

Nach Verringern der Rendering-Lösung, wenn:
1) Anwendung Framerate **erhöht**, sind Sie wahrscheinlich **GPU begrenzt.**
1) Anwendung Framerate **unverändert**, sind Sie wahrscheinlich **CPU-gebunden**

>[!NOTE]
>Unity bietet die Möglichkeit, mühelos die Render-zielauflösung des Ihrer Anwendung zur Laufzeit durch Ändern der *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* Eigenschaft. Das endgültige Bild angezeigt, auf dem Gerät wurde eine feste Auflösung. Die Plattform wird der niedrigeren Auflösung, erstellen Sie ein Bild mit höherer Auflösung für das Rendern auf zeigt die Ausgabe Stichproben. 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>Wie Sie Ihre Anwendung zu verbessern.

### <a name="cpu-performance-recommendations"></a>Empfehlungen zur CPU-Leistung

Im Allgemeinen umfasst die meisten Aufgaben in einer mixed Reality-Anwendung auf der CPU, Ausführen der "Simulations" der Szene und Verarbeiten von umfangreichen eindeutige Anwendungs-Logik. Daher gelten die folgenden Bereiche in der Regel für die Optimierung.

- Animationen
- Vereinfachen Sie die Physik
- Speicherbelegung
- Komplexe Algorithmen (d.h.) Inverse Kinematik, Auffinden von Pfad)

### <a name="gpu-performance-recommendations"></a>Empfehlungen zur GPU-Leistung

#### <a name="understanding-bandwidth-vs-fill-rate"></a>Grundlegendes zu Bandbreitenrate Vs Füllung
Beim Rendern von eines Frames auf der GPU, ist eine Anwendung in der Regel entweder die von Bandbreite oder Fill-Rate des Speichers begrenzt.

- **Speicherbandbreite** ist die Rate der Lesevorgänge, und schreibt die GPU Aktualisierungsoption aus dem Arbeitsspeicher
    - Um Beschränkungen der Netzwerkbandbreite zu identifizieren, reduzieren Sie die Texturqualität, und überprüfen Sie, ob die Framerate verbessert.
    - In Unity, dies ist möglich durch Ändern **Texturqualität** in **bearbeiten** > **Projekteinstellungen**  >   **[ Einstellungen von Quality](https://docs.unity3d.com/Manual/class-QualitySettings.html)**.
- **Geben Sie die Rate** bezieht sich auf den Durchsatz der gerenderten Pixel, die pro Sekunde von der GPU gezeichnet werden können.
    - Um Füllung Rate Einschränkungen zu identifizieren, verringern Sie die Bildschirmauflösung, und überprüfen Sie, ob die Framerate verbessert. 
    - In Unity, dies kann erfolgen über die *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* Eigenschaft

Speicherbandbreite umfasst in der Regel entweder Optimierungen
1) Verringern Sie die Textur-Lösungen
2) Verwenden Sie weniger Texturen (d.h.) Normals, glänzende, usw.)

Füllrate konzentriert sich hauptsächlich auf die Reduzierung der Anzahl von Vorgängen, die für die endgültige gerenderte Pixel berechnet werden müssen. Beispiele hierfür fallen häufig reduzieren
1) Anzahl von Objekten, die Render-Vorgangs
2) Anzahl von Vorgängen pro shader
3) Anzahl der GPU-Phasen, um das endgültige Ergebnis (Geometrieshader Nachbearbeitung Effekte, usw.)
4) Anzahl der Pixel, rendern (d.h.) Auflösung)

#### <a name="reduce-poly-count"></a>Reduzieren Sie Poly-Anzahl
Höhere Polygon zählt führen mehr Vorgänge für die GPU ein, und Verringern der Anzahl von Polygonen in Ihrer Szene reduziert die Zeitspanne, Geometrie gerendert. Andere Faktoren beteiligt sind ebenfalls Schattierung die Geometrie an, die weiterhin teuer sein kann, aber Polygonzahl ist die grundlegende Metrik festlegen, welche Kosten eine Szene werden gerendert.

#### <a name="limit-overdraw"></a>Limit-Elements zu überzeichnen

High-Elements zu überzeichnen tritt auf, wenn mehrere Objekte gerendert werden, aber nicht auf dem Bildschirm ausgegeben, da sie von einem anderen, in der Regel genauer, occluding Objekt ausgeblendet sind. Stellen Sie sich, eine Wand, die mehrere Räume "und" Geometry dahinter ansehen. Alle der Geometry-Instanz für das Rendering verarbeitet werden, aber nur die nicht transparente Wand tatsächlich gerendert werden, wie sie die Ansicht von allen anderen Inhalten occludes muss. Dies führt zu einer Verschwendung Vorgänge, die nicht für die aktuelle Ansicht benötigt werden.

#### <a name="shaders"></a>Shader

Shader sind kleine Programme, die auf der GPU ausgeführt, und ermitteln in der Regel zwei wichtige Schritte beim Rendern:
1) Scheitelpunkten des Objekts die Ziehfeld gezeichnet werden soll, auf dem Bildschirm und, wo sie im Bildschirmbereich (d.h.) sind. der Vertex-Shader)
    - Der Vertex-Shader wird pro Vertex in der Regel für jede "gameobject" ausgeführt werden.
2) Was Sie Farbe, die die Pixel (d.h.) die Pixel-Shader)
    - Der Pixel-Shader wird pro Pixel für die Textur, die für Gerät vorhanden gerendert wird ausgeführt.

Führen in der Regel Shader auf, viele Transformationen und Beleuchtung. Obwohl komplexe beleuchtungsmodelle, Schatten und andere Vorgänge fantastische Ergebnisse generieren können, sind sie auch mit einem Preis. Verringern der Anzahl von Vorgängen, die im Shader berechnet, kann die gesamte Arbeit, die von einer GPU pro Frame ausgeführt werden musste erheblich reduzieren.

##### <a name="shader-coding-recommendations"></a>Shader-Codierung von Empfehlungen

- Verwenden Sie möglichst bilineare Filterung
- Ordnen Sie Ausdrücke erstellen, um die MAD systeminternen Funktionen zu verwenden, um eine Multiply und eines "Add" zur gleichen Zeit durchführen
- Vorauszuberechnen Sie so weit wie möglich auf der CPU, und übergeben Sie als Konstanten für das material
- **Verschieben von Vorgängen aus dem Pixel-Shader in den Vertex-Shader bevorzugen**
    - Im Allgemeinen die Anzahl der Scheitelpunkte << Anzahl von Pixeln (d.h.) 720p 921,600 Pixel 1080p == == 2,073,600 Pixel, usw.)

#### <a name="remove-gpu-stages"></a>Entfernen Sie die GPU-Phasen
Nachbearbeitung Auswirkungen kann sehr speicherintensiv sein und in der Regel behindern die Füllrate Ihrer Anwendung. Dies umfasst auch die Anti-Aliasing-Techniken wie z. B. MSAA. Für HoloLens wird empfohlen, diese Techniken vollständig zu vermeiden. Darüber hinaus sollten zusätzliche Shader-Phasen wie Geometrie, Hülle und Compute-Shadern nach Möglichkeit vermieden werden.

## <a name="memory-recommendations"></a>Speicherempfehlungen
Eine übermäßige Speicheroperationen Zuordnung und Aufhebung der Zuordnung haben nachteilige Auswirkungen auf Ihre holographic Anwendung, was zu inkonsistenten Leistung, fixierte Frames und anderes Verhalten gleichzeitiger Aufrufe nachteilig auswirken. Es ist besonders wichtig, Überlegungen zum Arbeitsspeicher zu, bei der Entwicklung in Unity, da die Verwaltung des Arbeitsspeichers durch den Garbage Collector gesteuert wird.

#### <a name="object-pooling"></a>Objektpooling

Objektpooling ist ein beliebtes Verfahren, um die Kosten continuous speicherbelegungen und Aufhebungen von Objekten zu reduzieren. Dies erfolgt, indem Sie eine große Gruppe von identischen Objekte zuordnen und neu inaktive, verfügbare Instanzen aus diesem Pool anstatt ständig erstellen und Zerstören von Objekten im Laufe der Zeit. Objektpools eignen sich hervorragend für aktionsentwicklung Komponenten, die die Lebensdauer der Variablen während einer app haben.

## <a name="see-also"></a>Siehe auch
- [Empfehlungen zur Leistung für Unity](performance-recommendations-for-unity.md)
- [Empfohlene Einstellungen für Unity](recommended-settings-for-unity.md)
