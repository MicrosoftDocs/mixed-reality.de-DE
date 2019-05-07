---
title: Empfohlene Einstellungen für Unity
description: Unity bietet einige spezielle Verhaltensweisen für mixed Reality, die über projekteinstellungen umgeschaltet werden kann.
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: Unity "," Einstellungen "," mixed reality
ms.openlocfilehash: c7029f2dfaf246db9f972c7d89b46e4fb9b5f1a1
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993613"
---
# <a name="recommended-settings-for-unity"></a>Empfohlene Einstellungen für Unity

Unity bietet eine Reihe von Standardoptionen, die in der Regel im Durchschnittsfall für alle Plattformen sind. Unity bietet jedoch einige spezielle Verhaltensweisen für mixed Reality, die über projekteinstellungen umgeschaltet werden kann.

## <a name="performant-environment-set-up"></a>Leistungsstarke Umgebung einrichten

### <a name="low-quality-settings"></a>Niedrige Qualität-Einstellungen

Es ist wichtig, ändern Sie die **Unity Qualität Einstellungen** für Ihre Umgebung zu **sehr niedrig**. Dadurch wird sichergestellt, dass Ihre Anwendung performant mit der entsprechenden Framerate ausgeführt wird. Dies ist äußerst wichtig für die Entwicklung für Hololens. Für die Entwicklung immersive Headsets, abhängig von der Spezifikationen des Desktops Verbessern der Leistung der VR-Oberfläche kann eine Framerate, ohne die niedrigste Qualitaetsparameter noch erreichen. 

In Unity 2018 LTS und höher, kann Qualität des Projekts festgelegt werden:

Klicken Sie unter **bearbeiten** > **Projekteinstellungen** > **Qualität** > Festlegen der **Standard** durch Klicken auf die nach unten weisenden Pfeil, um die **sehr niedrig** Qualität

### <a name="lighting-settings"></a>Einstellungen für die Beleuchtung

Mit Quality Szene Einstellungen vergleichbar, ist es wichtig, optimale Beleuchtung-Einstellungen für Ihre Anwendung Mixed Reality festlegen. In Unity die Beleuchtung-Einstellung, die in der Regel den größten Auswirkungen auf die Leistung auf die Szene ist **Realtime globale Beleuchtung**. Dies kann dazu unter deaktiviert werden **Fenster** > **Rendern** > **Beleuchtung Einstellungen** > **in Echtzeit Globale Beleuchtung**. 

Es gibt eine andere Einstellung für die Beleuchtung, **globale Beleuchtung Dank der Minutengenauen**. Diese Einstellung bieten leistungsfähige und visuell eindrucksvolle Ergebnisse für immersive Headsets aber gilt im Allgemeinen nicht für die Entwicklung für HoloLens. **Dank der minutengenauen globale Illumniation** nur für statische "gameobjects" die nicht in der Regel in Kulissen von HoloLens aufgrund der Natur von einer unbekannten und veränderbaren Umgebung gefunden werden berechnet.

Lesen Sie [globale Beleuchtung aus Unity](https://docs.unity3d.com/Manual/GIIntro.html) für Weitere Informationen. 

>[!NOTE]
> **Globale Beleuchtung in Echtzeit** festgelegt **pro Szene** und Entwickler müssen daher diese Eigenschaft für alle Unity-Szene in ihrem Projekt speichern. 

### <a name="single-pass-instancing-rendering-path"></a>Durchlauf Instanziierung Rendering-Pfad

In Mixed Reality-Anwendungen wird die Szene und einmal für jede Eye für den Benutzer gerendert. Im Vergleich zu herkömmlichen 3D Entwicklung, dies effektiv verdoppeln Sie die Menge der Arbeit, die berechnet werden muss. Daher ist es wichtig, wählen Sie am effizientesten Rendern in Unity auf CPU- und GPU-Zeit gespeichert. Durchlauf instanziierten Rendering optimiert die Unity-Rendering-Pipeline für Mixed Reality-apps aus, und daher es wird empfohlen, diese Einstellung aktivieren, für jedes Projekt in der Standardeinstellung. 

So aktivieren Sie dieses Feature in Ihrem Unity-Projekt
1)  Open **XR Playereinstellungen** (Wechseln Sie zu **bearbeiten** > **Projekteinstellungen** > **Player**  >  **XR-Einstellungen**)
2) Wählen Sie **einzelne Instanz übergeben** aus der **Stereo-Rendering-Methode** -Dropdownmenü (**virtuelle Realität unterstützt** Kontrollkästchen muss aktiviert sein)

Lesen Sie die folgenden Artikel von Unity, Weitere Informationen, die bei diesem Ansatz rendern.
- [Gewusst wie: Maximieren der Leistung von AR und VR mit erweiterten Stereo-rendering](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [Übergeben Sie Single Instancing](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> Ein verbreitetes Problem mit einzelnen Rendering Instanz übergeben tritt auf, wenn Entwickler bereits vorhandene benutzerdefinierte Shadern, die nicht für geschriebenen Instanziierung. Nach der Aktivierung dieser Option werden Entwicklern einige "gameobjects" nur das Rendering in ein Auge feststellen. Dies ist, da die zugeordneten benutzerdefinierten Shadern nicht die entsprechenden Eigenschaften für die Instanziierung.
>
> Finden Sie unter [einzelne übergeben Stereo Rendering für HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) von Unity für das dieses Problem zu beheben

### <a name="enable-depth-buffer-sharing"></a>Aktivieren Sie die Tiefe Puffer freigeben

Um eine höhere Stabilität von – Hologramm aus die Wahrnehmung des Benutzers zu erreichen, ist es wird empfohlen, aktivieren Sie die **Tiefe Puffer freigeben** -Eigenschaft in Unity. Durch Aktivieren dieser, gemeinsam Unity die Depth-Zuordnung, die von Ihrer Anwendung mit der Windows Mixed Reality-Plattform erstellt. Die Plattform wird dann – Hologramm Stabilität speziell für Ihre Szene für einen beliebigen Frame gerendert wird, indem Ihre Anwendung optimieren können.

So aktivieren Sie dieses Feature in Ihrem Unity-Projekt
1) Open **XR Playereinstellungen** (Wechseln Sie zu **bearbeiten** > **Projekteinstellungen** > **Player**  >  **XR-Einstellungen**)
2) Aktivieren Sie das Kontrollkästchen **Tiefe Puffer Freigabe aktivieren** unter **virtuelle Realität SDKs** > **Windows Mixed Reality** Erweiterung (**virtuellen Tatsächlich unterstützt** Kontrollkästchen muss aktiviert sein)

Darüber hinaus wird empfohlen, wählen Sie **Tiefe von 16-Bit-** unter der **Tiefe Format** in diesem Bereich sind besonders für die Entwicklung für Hololens festlegen. Auswählen von 16-Bit-im Vergleich zu 24-Bit-werden die Anforderungen an die Netzwerkbandbreite erheblich reduzieren, da weniger Daten verschoben oder verarbeitet werden müssen.

>[!NOTE]
> Entwickler sollten der Z-fighting beachten, wenn Sie diese Werte zusammen mit der Kamera in der Nähe/entfernte Ebene Einstellungen zu ändern. Z-Fighting tritt auf, wenn zwei "gameobjects" zum Rendern von demselben Pixel und aufgrund der Einschränkungen in der Genauigkeit der Tiefenpuffer (d.h.) Z-Detailtiefe), Unity kann nicht erkennen, welches Objekt vor dem anderen ist. Entwickler sehen ein Flimmern zwischen zwei Spielobjekte, sobald diese *bekämpfen* für den gleichen Wert für die Z-Tiefe. Dies kann gelöst werden, durch den Wechsel in 24-Bit-Depth-Format wie in eine größere Anzahl von Werten für jedes Objekt fallen, um auf die Z-Tiefe von der Kamera zu berechnen.
>
> Allerdings es wird empfohlen, vor allem für Hololens-Entwicklung, zum Ändern der Kamera in der Nähe des und Farbebenen weit stattdessen auf einen kleineren Bereich und behält dabei die Tiefe von 16-Bit-format. Die Z-Depth-nicht-linear zugeordnet ist, auf den Bereich von Werten entlang der Kamera nah und Fern Ebenen. Dies kann geändert werden, indem Sie auswählen der *Main Camera* in Ihrer Szene, und wählen Sie unter **Inspektor**, Ändern der **Naher & weit Clipping Ebene** Werte reduzieren Sie einen Adressbereich (d.h.) über 1000 m auf 100 m oder einen anderen x-Wert usw.).

### <a name="building-for-il2cpp"></a>Erstellen von für IL2CPP

Unity ist die Unterstützung für die Skripterstellung Back-End- und somit sollten Entwickler nutzen .NET veraltet **IL2CPP** für ihre UWP visual Studio erstellt wird. Obwohl dies die verschiedenen Vorteile bringt, erstellen Sie visual Studio-Projektmappe von Unity für **Il2CPP** kann erheblich langsamer als die alte .NET-Methode übergeben werden. Es wird daher dringend empfohlen, die empfohlenen Vorgehensweisen zum Erstellen von **IL2CPP** , auf die Entwicklungszeit für die Iteration zu speichern.

1) Nutzen von inkrementellen Buildvorgangs durch Erstellen des Projekts in das gleiche Verzeichnis jedes Mal erneut es mithilfe der vorab erstellten Dateien
2) Deaktivieren Sie die Antimalware-Software-Scans für Ihr Projekt & erstellen Ordner
   - Open **Virus- & Threat Protection** unter Ihrem Windows 10-Einstellungen-app
   - Wählen Sie **Einstellungen verwalten** unter **Virus- & Threat Protection-Einstellungen**
   - Wählen Sie **Add- oder Remove-Ausschlüsse** unter der **Ausschlüsse** Abschnitt
   - Klicken Sie auf **fügen Sie einen Ausschluss** und wählen Sie der Ordner Ihrer Unity-Projekt-Code enthalten, und erstellen
3) Verwenden Sie eine SSD für das Erstellen von

Lesen Sie [optimieren erstellen Zeiten für IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) für Weitere Informationen.

## <a name="publishing-properties"></a>Veröffentlichungseigenschaften

### <a name="holographic-splash-screen"></a>Holographic Splash-Bildschirm

HoloLens verfügt über eine Mobile-Klasse CPU und GPU, was, dass apps bedeutet laden etwas länger dauern. Während die app geladen wird, Benutzer sehen nur Schwarz, und daher sie Fragen sich vielleicht, was vor sich geht. Diese während des Ladens, versichern Sie einen holographic Splash-Bildschirm hinzufügen können.

Um der holographic Splash-Bildschirm zu wechseln:
1) Wechseln Sie zu **bearbeiten** > **Projekteinstellungen** > **Player** Seite
2) Klicken Sie auf die **Windows Store** Registerkarte, und öffnen Sie die **Splash-Image** Abschnitt
3) Wenden Sie das gewünschte Abbild unter der **Windows Holographic > Hologramm Splash** Eigenschaft.
    - Umschalten der **Unity-Begrüßungsbildschirm angezeigt** Option aktivieren oder deaktivieren Sie den Begrüßungsbildschirm der Unity mit Branding. Wenn Sie nicht über eine Unity-Pro-Lizenz verfügen, wird immer mit dem Branding des Begrüßungsbildschirms Unity angezeigt.
    - Wenn eine **Hologramm Splash** wird angewendet, wird immer angezeigt, unabhängig davon, ob das Anzeigen von Unity-Begrüßungsbildschirm Kontrollkästchen aktiviert oder deaktiviert ist. Angeben einer benutzerdefinierten holographic Splash-Image ist nur für Entwickler mit einer Unity-Pro-Lizenz verfügbar.

|  Unity-Splash-Bildschirm anzeigen  |  Holographic Splash-Image  |  Verhalten |
|----------|----------|----------|
|  Ein  |  Keine  |  Zeigen Sie Standardbegrüßungsbildschirm für Unity 5 Sekunden lang oder bis die app geladen wird, welcher Zeitraum länger ist. | 
|  Ein  |  Benutzerdefiniert  |  Zeigen Sie benutzerdefinierte Splash-Bildschirm, 5 Sekunden lang oder bis die app geladen wird, welcher Zeitraum länger ist. | 
|  Deaktiviert  |  Keine  |  Zeigen Sie transparentes Schwarz fest ("nothing"), bis die app geladen wird. | 
|  Deaktiviert  |  Benutzerdefiniert  |  Zeigen Sie benutzerdefinierte Splash-Bildschirm, 5 Sekunden lang oder bis die app geladen wird, welcher Zeitraum länger ist. | 

Lesen Sie [Unity Begrüßungsbildschirm Dokumentation](https://docs.unity3d.com/Manual/class-PlayerSettingsSplashScreen.html) für Weitere Informationen.

### <a name="tracking-loss"></a>Verlust der Überwachung

Sehen die Umgebung aus, um es zum Erstellen, ein Mixed Reality-Kopfhörer hängt [Koordinatensysteme World-locked](coordinate-systems-in-unity.md), mit denen Hologramme beibehalten. Wenn die Kopfhörer kann nicht sich selbst in der ganzen Welt zu finden ist, wird die Kopfhörer bewirken, haben *verloren nachverfolgung*. In diesen Fällen Funktionalität, die abhängig von der Welt gesperrt Koordinatensysteme, z. B. räumliche Phasen, die räumliche Anker und die räumliche Zuordnung, funktionieren nicht.

Bei einem Verlust der Überwachung wird ist Unity-Standardverhalten, der Rendering-Hologramme beenden, Anhalten der [spielschleife](http://docs.unity3d.com/Manual/ExecutionOrder.html), und Anzeigen eines Überwachungsprofils, bequem verloren gegangen Benachrichtigung folgt die Blicke Benutzer. Benutzerdefinierte Benachrichtigungen können auch angegeben werden, in Form eines Überwachungsdatensatzes Verlust Image. Für apps, die von der Überwachung für ihre gesamte Umgebung abhängen, ist es ausreichend, um Abhilfe vollständig, bis Sie wieder auf die nachverfolgung ist Unity zu ermöglichen. Entwickler können angezeigt werden, während der nachverfolgung der Verlust ein benutzerdefiniertes Images angeben. 

Verloren gegangen Bild, um die Überwachung anzupassen:
1) Wechseln Sie zu **bearbeiten** > **Projekteinstellungen** > **Player** Seite
2) Klicken Sie auf die **Windows Store** Registerkarte, und öffnen Sie die **Splash-Image** Abschnitt
3) Wenden Sie das gewünschte Abbild unter der **Windows Holographic > nachverfolgung Verlust Image** Eigenschaft.

#### <a name="opt-out-of-automatic-pause"></a>Melden Sie sich für das automatische anhalten

Einige apps erfordern ggf. keine nachverfolgung (z. B. [Ausrichtung nur apps](coordinate-systems-in-unity.md) wie der 360-Grad-video-Viewer) oder müssen weiterhin ohne Unterbrechung bei der nachverfolgung Verarbeitung geht verloren. In diesen Fällen können der standardmäßigen Verlust Nachverfolgungsverhalten apps deaktivieren. Entwickler, die diese Option wählen sind verantwortlich für das Ausblenden von bzw. deaktivieren alle Objekte, die in einem Überwachungsprofil-Loss-Szenario nicht ordnungsgemäß gerendert wird. In den meisten Fällen werden nur der Inhalt, der empfohlen wird, werden in diesem Fall Text gesperrt Inhalt Rendern rund um die Hauptkamera zentriert.

Automatische Pause-Verhalten zu deaktivieren:
1) Wechseln Sie zu **bearbeiten** > **Projekteinstellungen** > **Player** Seite
2) Klicken Sie auf die **Windows Store** Registerkarte, und öffnen Sie die **Splash-Image** Abschnitt
3) Ändern der **Windows Holographic > auf nachverfolgung Verlust anhalten "und" Bild anzeigen** Kontrollkästchen.

#### <a name="tracking-loss-events"></a>Nachverfolgen von Ereignissen von Verlust

Um benutzerdefiniertes Verhalten definiert, bei der nachverfolgung verloren geht, behandeln Sie die globale [Verlust Nachverfolgungsereignisse](tracking-loss-in-unity.md).

### <a name="capabilities"></a>Funktionen

Für eine app bestimmte Funktionen nutzen müssen sie die entsprechenden Funktionen in seinem Manifest deklarieren. Die manifest-Deklarationen können in Unity vorgenommen werden, damit sie in jedem nachfolgenden Projektexport enthalten sind. 

Funktionen können für ein Mixed Reality-Anwendung aktiviert werden:
1) Wechseln Sie zu **bearbeiten** > **Projekteinstellungen** > **Player** Seite
2) Klicken Sie auf die **Windows Store** Registerkarte, und öffnen Sie die **Veröffentlichungseinstellungen** aus, und suchen Sie nach der **Funktionen** Liste

Die entsprechenden Funktionen für die Aktivierung der häufig verwendeten APIs für Holographic apps sind:
<br>

|  Funktion  |  APIs, die Funktion erfordern |
|----------|----------|
|  SpatialPerception  |  SurfaceObserver | 
|  WebCam  |  PhotoCapture und VideoCapture | 
|  PicturesLibrary / "videoslibrary"  |  PhotoCapture oder VideoCapture, bzw. (bei den aufgezeichneten Inhalt zu speichern) | 
|  Mikrofon  |  VideoCapture (wenn Audio erfassen), DictationRecognizer, GrammarRecognizer und KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (und mit der Unity-Profiler) | 

## <a name="see-also"></a>Siehe auch
* [Unity-Entwicklung – Übersicht](unity-development-overview.md)
* [Understaing-Leistung für Mixed Reality](understanding-performance-for-mixed-reality.md)
* [Leistungsempfehlungen für Unity](performance-recommendations-for-unity.md)