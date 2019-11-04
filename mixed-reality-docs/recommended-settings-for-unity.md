---
title: Empfohlene Einstellungen für Unity
description: Unity bietet einige Verhaltensweisen, die für Mixed Reality spezifisch sind und durch Projekteinstellungen ein-und ausgeschaltet werden können.
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: Unity, Einstellungen, gemischte Realität
ms.openlocfilehash: 2f2f823fe7192bd92e038d58901cb7098d2f4d64
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438104"
---
# <a name="recommended-settings-for-unity"></a>Empfohlene Einstellungen für Unity

Unity bietet eine Reihe von Standardoptionen, die in der Regel der durchschnittliche Fall für alle Plattformen sind. Unity bietet jedoch einige Verhaltensweisen, die für Mixed Reality spezifisch sind und durch Projekteinstellungen ein-und ausgeschaltet werden können.

## <a name="performant-environment-set-up"></a>Leistungsfähiges Einrichten der Umgebung

### <a name="low-quality-settings"></a>Einstellungen mit niedriger Qualität

Es ist wichtig, die **Unity-Qualitätseinstellungen** für Ihre Umgebung so zu ändern, dass Sie **sehr niedrig**ist. Dadurch wird sichergestellt, dass Ihre Anwendung in der entsprechenden Framerate leistungsfähig ausgeführt wird. Dies ist für die hololens-Entwicklung äußerst wichtig. Für die Entwicklung auf immersiven Headsets, abhängig von den Spezifikationen des Desktops, der die VR-Darstellung ermöglicht, kann ein Framerate auch ohne die niedrigsten Qualitätsparameter erreicht werden.

In Unity 2018 LTS und höher kann die Qualitätsstufe des Projekts wie folgt festgelegt werden:

Wählen Sie unter > **Projekteinstellungen** **Bearbeiten** > > **Qualität** den **Standard** Wert aus, indem Sie auf den abwärts Pfeil auf den Wert " **sehr niedrig** Qualität" klicken.

### <a name="lighting-settings"></a>Beleuchtungseinstellungen

Ähnlich wie bei den Quality Scene-Einstellungen ist es wichtig, optimale Beleuchtungseinstellungen für ihre gemischte Reality-Anwendung festzulegen. In Unity ist die Beleuchtungs Einstellung, die in der Regel die größte Auswirkung auf die Leistung in Ihrer Szene hat, die **Globale Beleuchtung in Echtzeit**. Diese Einstellung kann deaktiviert werden, indem Sie unter **Window** > **Rendering** > **Beleuchtungseinstellungen** > **Echtzeit-Beleuchtung**wechseln.

Es gibt eine weitere Beleuchtungs Einstellung, die **Globale Beleuchtung**. Diese Einstellung kann für immersive Headsets leistungsfähige und visuell beeindruckende Ergebnisse bereitstellen, ist jedoch im Allgemeinen nicht für die hololens-Entwicklung anwendbar. Die **gebrannte globale Löschung** wird nur für statische gameobjects-Objekte berechnet, die im Allgemeinen nicht in hololens-Szenen aufgrund der Art einer unbekannten und veränderlichen Umgebung gefunden werden.

Weitere Informationen finden Sie [unter Globale Beleuchtung von Unity](https://docs.unity3d.com/Manual/GIIntro.html) . 

>[!NOTE]
> Die **Globale Beleuchtung in Echtzeit** wird **pro Szene** festgelegt, sodass Entwickler diese Eigenschaft für jede Unity-Szene in Ihrem Projekt speichern müssen.

### <a name="single-pass-instancing-rendering-path"></a>Renderingpfad für Einzelpass-Instanz

In Mixed Reality-Anwendungen wird die Szene zweimal gerendert, einmal für den Benutzer. Im Vergleich zur herkömmlichen 3D-Entwicklung verdoppelt dies effektiv den Arbeitsaufwand, der berechnet werden muss. Daher ist es wichtig, den effizientesten Renderingpfad in Unity auszuwählen, um sowohl die CPU-als auch die GPU-Zeit zu sparen. Ein Single Pass-instanziziertes Rendering optimiert die Unity-Renderingpipeline für Mixed Reality-apps. Daher wird empfohlen, diese Einstellung standardmäßig für jedes Projekt zu aktivieren.

So aktivieren Sie dieses Feature in Ihrem Unity-Projekt

1)  Öffnen Sie die **Player-XR-Einstellungen** (wechseln Sie zu **Edit** > **Project Settings** > **Player** > **XR-Einstellungen**)
2) Wählen Sie im Dropdown Menü der **Stereo Renderingmethode** die Option **Single Pass-instanziierten** aus (Kontrollkästchen**Virtual Reality supported** muss aktiviert sein).

Weitere Informationen zu diesem renderingansatz finden Sie in den folgenden Artikeln von Unity.

- [Maximieren der AR-und VR-Leistung mit dem erweiterten Stereo Rendering](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [Einzelpass-Instanziierung](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

>[!NOTE]
> Ein häufiges Problem mit einem einzelnen Pass-instanziierten Rendering tritt auf, wenn Entwickler bereits über vorhandene benutzerdefinierte Shader verfügen, die nicht für die Instanziierung Nachdem Sie diese Funktion aktiviert haben, bemerken Entwickler möglicherweise, dass einige gameobjects nur in einem Blick dargestellt werden. Dies liegt daran, dass die zugeordneten benutzerdefinierten Shader nicht über die entsprechenden Eigenschaften für die Instanziierung verfügen.
>
> Informationen zum Beheben dieses Problems finden Sie unter [Single Pass Stereo Rendering for hololens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) from Unity.

### <a name="enable-depth-buffer-sharing"></a>Tiefen Puffer Freigabe aktivieren

Um eine bessere hologrammstabilität von der Wahrnehmung des Benutzers zu erzielen, empfiehlt es sich, die **Tiefe Puffer Freigabe** Eigenschaft in Unity zu aktivieren. Wenn Sie dies aktivieren, wird Unity die von Ihrer Anwendung erzeugte tiefen Zuordnung mit der Windows Mixed Reality-Plattform gemeinsam nutzen. Die Plattform wird dann in der Lage sein, die hologrammstabilität speziell für Ihre Szene zu optimieren, damit jeder Frame von Ihrer Anwendung gerendert wird.

So aktivieren Sie dieses Feature in Ihrem Unity-Projekt

1) Öffnen Sie die **Player-XR-Einstellungen** (wechseln Sie zu **Edit** > **Project Settings** > **Player** > **XR-Einstellungen**)
2) Aktivieren Sie das Kontrollkästchen zum **Aktivieren der tiefen Puffer Freigabe** unter **Virtual Reality sdchs** > **Windows Mixed Reality** -Erweiterung (Kontrollkästchen**Virtual Reality supported** muss aktiviert sein).

Außerdem wird empfohlen, unter der Einstellung **Tiefe Format** in diesem Panel eine **16-Bit-Tiefe** auszuwählen, insbesondere bei der hololens-Entwicklung. Durch die Auswahl von 16 Bit im Vergleich zu 24-Bit werden die Bandbreitenanforderungen erheblich reduziert, da weniger Daten verschoben/verarbeitet werden müssen.

Damit die Windows Mixed Reality-Plattform die – Hologramm-Stabilität optimieren kann, basiert Sie darauf, dass der tiefen Puffer genau ist und jedem gerenderten Hologramm auf dem Bildschirm entspricht. Daher ist es bei der tiefen Puffer Freigabe für wichtig, dass es beim Rendern von Farben auch die Tiefe rendert. In Unity werden die meisten nicht transparenten oder transparentcutout-Materialien standardmäßig in der Tiefe gerenden, aber transparente und Textobjekte werden im Allgemeinen nicht ausführlich gerenden, obwohl dies shaderabhängig ist usw.

Wenn Sie den [Mixed Reality Toolkit Standard-Shader](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md)verwenden, um Tiefe für transparente Objekte zu Renten:

1) Wählen Sie das transparente Material aus, das den mrtk-Standard-Shader verwendet, und öffnen Sie das Fenster Inspektor Editor.
2) Wählen Sie in der Warnung "Tiefe Puffer Freigabe" die Schaltfläche **jetzt reparieren** aus. Dies kann auch manuell erfolgen, indem der **Renderingmodus** auf **Benutzer** definiert festgelegt wird und der **Modus** **auf** **transparent** **festgelegt wird** .

> [!IMPORTANT]
> Entwickler sollten sich vor Z-kämpfen hüten, wenn Sie diese Werte zusammen mit den Einstellungen für die near/all-Ebene der Kamera ändern. Z-Kämpfe treten auf, wenn zwei gameobjects versuchen, zum gleichen Pixel zu rendern, und aufgrund von Einschränkungen bei der Genauigkeit des tiefen Puffers (d. h. z-Tiefe), Unity kann nicht erkennen, welches Objekt vor dem anderen liegt. Entwickler werden ein Flimmern zwischen zwei Spielobjekten bemerken, wenn Sie für denselben z-tiefen Wert *kämpfen* . Dies kann durch einen Wechsel zu einem 24-Bit-Tiefen Format gelöst werden, da für jedes Objekt eine größere Anzahl von Werten vorhanden ist, die für die jeweilige z-Tiefe von der Kamera berechnet werden sollen.
>
> Es wird jedoch empfohlen, insbesondere bei der hololens-Entwicklung, die Near-und Far-Ebenen der Kamera in einen kleineren Bereich zu ändern und das 16-Bit-Tiefen Format beizubehalten. Die z-Tiefe ist nicht linear dem Wertebereich entlang der nahen und fernen Kamera Flächen zugeordnet. Dies kann geändert werden, indem Sie die *Hauptkamera* in der Szene auswählen und unter **Inspektor**die Werte **in der Nähe & weit** genwergenebenenwerte ändern, um den Bereich zu reduzieren (d.h. zwischen 1000 m und 100 m oder einem anderen x-Wert usw.)

>[!IMPORTANT]
> [Unity erstellt](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) bei Verwendung des 16-Bit-Tiefen Formats keinen Schablone-Puffer. Folglich funktionieren einige Effekte der Unity-Benutzeroberfläche und andere Schablonen erforderliche Effekte nicht, es sei denn, es wird ein 24-Bit-Tiefen Format ausgewählt, das einen [8-Bit-Schablonen Puffer](https://docs.unity3d.com/Manual/SL-Stencil.html)erstellt.

### <a name="building-for-il2cpp"></a>Entwickeln für IL2CPP

Unity verfügt über veraltete Unterstützung für das .NET-Skript-Back-End und empfiehlt daher Entwicklern, **IL2CPP** für Ihre UWP-Visual Studio-Builds zu verwenden. Obwohl dies verschiedene Vorteile bietet, kann das Entwickeln Ihrer Visual Studio-Lösung aus Unity für **Il2CPP** erheblich langsamer als die alte .NET-Methode sein. Daher wird dringend empfohlen, die bewährten Methoden für die Entwicklung von **IL2CPP** zu befolgen, um die Entwicklungszeit für die Entwicklung zu sparen.

1) Nutzen Sie das inkrementelle erstellen, indem Sie Ihr Projekt jedes Mal in demselben Verzeichnis erstellen, indem Sie die vorgefertigten Dateien wieder verwenden.
2) Antischadsoftwarescans für Ihr Projekt & Buildordner deaktivieren
   - Öffnen Sie **Viren & Bedrohungsschutz** unter Ihrer Windows 10-Einstellungs-APP.
   - Wählen Sie unter **Viren & Bedrohungsschutz Einstellungen** die Option **Einstellungen verwalten** .
   - Wählen Sie im Abschnitt **Ausschlüsse** die Option **Ausschlüsse hinzufügen oder entfernen**
   - Klicken Sie auf **Ausschluss hinzufügen** , und wählen Sie den Ordner mit Ihrem Unity-Projekt Code und Buildausgaben
3) Verwenden eines SSD zum entwickeln

Weitere Informationen finden Sie im Artikel [zum Optimieren der Buildzeiten für IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) .

> [!NOTE]
> Darüber hinaus es kann vorteilhaft sein, besonders für Unity-Projekte mit sehr vielen Ressourcen (mit Ausnahme von Skriptdateien) oder ständig wechselnden Szenen/Ressourcen, einen [Cacheserver](https://docs.unity3d.com/Manual/CacheServer.html) einzurichten. Beim Öffnen eines Projekts speichert Unity die qualifizierenden Ressourcen in einem internen Cacheformat auf dem Entwicklercomputer. Bei Änderungen müssen die Elemente neu importiert und daher neu verarbeitet werden. Dieser Prozess kann einmal durchgeführt, in einem Cacheserver gespeichert und anschließend für andere Entwickler freigegeben werden, damit diese Zeit sparen und den erneuten Import der Änderungen nicht mehr einzeln und lokal verarbeiten müssen.

## <a name="publishing-properties"></a>Veröffentlichungs Eigenschaften

### <a name="holographic-splash-screen"></a>Holographic-Begrüßungsbildschirm

Hololens verfügt über eine CPU-und GPU-Version der mobilen Klasse, was bedeutet, dass die Auslastung von apps etwas länger dauern kann. Während die App geladen wird, sehen Benutzer nur schwarz, und Sie Fragen sich vielleicht, was passiert. Um Sie beim Laden zu überprüfen, können Sie einen Holographic-Begrüßungsbildschirm hinzufügen.

So schalten Sie den Holographic-Begrüßungsbildschirm um:

1) Wechseln Sie zu **Edit** > **Project Settings** > **Player** Page.
2) Klicken Sie auf die Registerkarte **Windows Store** , und öffnen Sie den Abschnitt Begrüßungs **Abbild** .
3) Wenden Sie das gewünschte Image unter der Eigenschaft **Windows Holographic > Holographic Splash Image** an.
    - Wenn Sie die Option **Unity-Begrüßungsbildschirm anzeigen** umschalten, wird der Begrüßungsbildschirm von Unity-Marken aktiviert oder deaktiviert. Wenn Sie nicht über eine Unity pro-Lizenz verfügen, wird immer der Bildschirm "der Unity-Marken Begrüßungs" angezeigt.
    - Wenn ein **Holographic** -Begrüßungs Bild angewendet wird, wird es immer angezeigt, unabhängig davon, ob das Kontrollkästchen Unity-Begrüßungsbildschirm anzeigen aktiviert oder deaktiviert ist. Das Angeben eines benutzerdefinierten Holographic-Begrüßungs Bilds ist nur für Entwickler mit einer Unity pro-Lizenz verfügbar.

|  Unity-Begrüßungsbildschirm anzeigen  |  Holographic-Begrüßungs Bild  |  Verhalten |
|----------|----------|----------|
|  Wischen Sie unter  |  Keine  |  Standardmäßiger Unity-Begrüßungsbildschirm für 5 Sekunden oder bis zum Laden der App anzeigen, je nachdem, welcher Zeitraum länger ist. |
|  Wischen Sie unter  |  „Benutzerdefiniert“  |  Benutzerdefinierten Begrüßungsbildschirm für 5 Sekunden oder bis zum Laden der App anzeigen, je nachdem, welcher Zeitraum länger ist. |
|  „Aus”  |  Keine  |  Zeigen Sie transparent Black (Nothing) an, bis die App geladen wird. |
|  „Aus”  |  „Benutzerdefiniert“  |  Benutzerdefinierten Begrüßungsbildschirm für 5 Sekunden oder bis zum Laden der App anzeigen, je nachdem, welcher Zeitraum länger ist. |

Weitere Informationen finden Sie in [der Dokumentation](https://docs.unity3d.com/Manual/class-PlayerSettingsSplashScreen.html) zum Begrüßungsbildschirm von Unity.

### <a name="tracking-loss"></a>Nachverfolgung von Verlusten

Ein Mixed Reality-Headset ist davon abhängig, dass die Umgebung um die IT-Umgebung herum [Gesperrte Koordinatensysteme](coordinate-systems-in-unity.md)erstellt werden kann, mit denen holograms an der Position bleiben können. Wenn sich das Headset nicht in der Welt finden kann, wird die nach *Verfolgung*des Headsets abgebrochen. In diesen Fällen funktionieren Funktionen, die von weltweit gesperrten Koordinatensystemen abhängen, wie z. b. räumliche Stufen, räumliche Anker und räumliche Zuordnung, nicht.

Wenn ein Verlust der Nachverfolgung auftritt, besteht das Standardverhalten von Unity darin, das Rendern von holograms zu stoppen, die [Spiel Schleife](https://docs.unity3d.com/Manual/ExecutionOrder.html)anzuhalten und eine Nachverfolgung verlorener Benachrichtigung anzuzeigen, die dem Benutzer angezeigt wird. Benutzerdefinierte Benachrichtigungen können auch in Form eines Abbild Verlusts bereitgestellt werden. Für apps, die von der Nachverfolgung für Ihre gesamte Darstellung abhängen, ist es ausreichend, Unity dieses Verfahren vollständig zu verarbeiten, bis die Nachverfolgung wieder hergestellt wird. Entwickler können ein benutzerdefiniertes Image bereitstellen, das beim Nachverfolgen von Verlusten angezeigt wird.

So passen Sie das Abbild der Nachverfolgung verloren:

1) Wechseln Sie zu **Edit** > **Project Settings** > **Player** Page.
2) Klicken Sie auf die Registerkarte **Windows Store** , und öffnen Sie den Abschnitt Begrüßungs **Abbild** .
3) Wenden Sie das gewünschte Image unter der Eigenschaft **Windows Holographic > Tracking Loss Image** an.

#### <a name="opt-out-of-automatic-pause"></a>Automatische Pause beenden

Einige apps erfordern möglicherweise keine Nachverfolgung (z. b. nur für die [Ausrichtung](coordinate-systems-in-unity.md) , z. b. Video-Viewer mit 360-Grad) oder müssen möglicherweise ununterbrochen verarbeitet werden, während die Nachverfolgung verloren geht In diesen Fällen können apps den Standard Verlust des nach Verfolgungs Verhaltens ablehnen. Entwickler, die diese Option auswählen, sind dafür verantwortlich, Objekte zu verbergen bzw. zu deaktivieren, die in einem nach Verfolgungs Verlust-Szenario nicht ordnungsgemäß dargestellt werden. In den meisten Fällen ist der einzige Inhalt, der in diesem Fall zum Rendering empfohlen wird, in einem Text mit gesperrtem Inhalt, der sich um die Hauptkamera dreht.

So beenden Sie das automatische anhalten:

1) Wechseln Sie zu **Edit** > **Project Settings** > **Player** Page.
2) Klicken Sie auf die Registerkarte **Windows Store** , und öffnen Sie den Abschnitt Begrüßungs **Abbild** .
3) Ändern Sie das Kontrollkästchen **Windows Holographic > on Tracking Loss Pause and Show Image** .

#### <a name="tracking-loss-events"></a>Nachverfolgen von Verlustereignissen

Um benutzerdefiniertes Verhalten zu definieren, wenn die Nachverfolgung verloren geht, behandeln Sie die Ereignisse der globalen nach [Verfolgung](tracking-loss-in-unity.md)

### <a name="capabilities"></a>Funktionen

Damit eine APP bestimmte Funktionen nutzen kann, müssen Sie die entsprechenden Funktionen in ihrem Manifest deklarieren. Die Manifest-Deklarationen können in Unity erstellt werden, sodass Sie in jedem nachfolgenden Projekt Export enthalten sind.

Funktionen können für eine gemischte Reality-Anwendung wie folgt aktiviert werden:

1) Wechseln Sie zu **Edit** > **Project Settings** > **Player** Page.
2) Klicken Sie auf die Registerkarte **Windows Store** , öffnen Sie den Abschnitt **Veröffentlichungs Einstellungen** , und suchen Sie nach der Liste der **Funktionen** .

Die folgenden Funktionen zum Aktivieren der häufig verwendeten APIs für Holographic-apps sind verfügbar:
<br>

|  Funktion  |  APIs, die Funktionen erfordern |
|----------|----------|
|  Spatialperception  |  Surfaceobserver |
|  Webcam  |  Photocapture und Videocapture |
|  Pictureslibrary/videoslibrary  |  Photocapture oder Videocapture bzw. (beim Speichern des erfassten Inhalts) |
|  Mikrofon  |  Videocapture (bei der Erfassung von Audiodaten), "diktationerkenzer", "grammarerkenzer" und "keywordrecognizer" |
|  Internet Client deklarieren  |  "Diktationerkenzer" (und für die Verwendung des Unity-Profilers) |

## <a name="see-also"></a>Weitere Informationen:

* [Unity-Entwicklung – Übersicht](unity-development-overview.md)
* [Grundlegendes zur Leistung für Mixed Reality](understanding-performance-for-mixed-reality.md)
* [Leistungsempfehlungen für Unity](performance-recommendations-for-unity.md)
