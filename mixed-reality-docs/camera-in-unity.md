---
title: Kamera in Unity
description: Verwenden der Unity-Hauptkamera für die Windows Mixed Reality-Entwicklung für Holographic Rendering
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Holographic-Rendering, Holographic, immersive, Fokuspunkt, tiefen Puffer, nur Ausrichtung, Positional, undurchsichtig, transparent, Clip
ms.openlocfilehash: 1a2e66d5c028109a58ea8682668521f50158add9
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375587"
---
# <a name="camera-in-unity"></a>Kamera in Unity

Wenn Sie ein Mixed Reality-Headset durch tragen, wird es zur Mitte ihrer Holographic World. Die Unity- [Kamera](https://docs.unity3d.com/Manual/class-Camera.html) Komponente verarbeitet das stereorenderingerrendering automatisch und folgt dem Spitzen Bewegung und der Drehung, wenn in Ihrem Projekt "Virtual Reality unterstützt" mit "Windows Mixed Reality" als Gerät ausgewählt ist (im Abschnitt andere Einstellungen der Windows Store Player-Einstellungen). Dies kann in älteren Versionen von Unity als "Windows Holographic" aufgeführt werden.

Sie sollten jedoch die unten beschriebenen Kameraeinstellungen festlegen, um die visuelle Qualität und die [Stabilität des Hologramms](hologram-stability.md)vollständig zu optimieren.

>[!NOTE]
>Diese Einstellungen müssen in jeder Szene der APP auf die Kamera angewendet werden.
>
>Wenn Sie in Unity eine neue Szene erstellen, enthält diese standardmäßig ein Hauptkamera-gameobject in der Hierarchie, die die Kamera Komponente enthält, aber die unten aufgeführten Einstellungen sind nicht ordnungsgemäß angewendet.

## <a name="automatic-scene-and-camera-setup-with-mixed-reality-toolkit-v2"></a>Automatisches Einrichten von Szenen und Kameras mit Mixed Reality Toolkit v2

Befolgen Sie die [Schritt-für-Schritt](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) -Anleitung zum Hinzufügen von Mixed Reality Toolkit v2 zu Ihrem Unity-Projekt, und das Projekt wird automatisch konfiguriert.

Sie können das Projekt auch ohne mrtk manuell konfigurieren, indem Sie das Handbuch im Abschnitt unten durchführen.

## <a name="holographic-vs-immersive-headsets"></a>Holographic im Vergleich zu immersiven Headsets

Die Standardeinstellungen für die Unity-Kamera Komponente sind für herkömmliche 3D-Anwendungen vorgesehen, die einen Skybox-ähnlichen Hintergrund benötigen, da Sie nicht über eine reale Welt verfügen.

* Bei der Ausführung auf einem **[immersiven Headset](immersive-headset-hardware-details.md)** Rendern Sie alles, was dem Benutzer angezeigt wird, und Sie möchten die Skybox wahrscheinlich behalten.
* Wenn Sie jedoch auf einem **Holographic-Headset** wie [hololens](hololens-hardware-details.md)ausgeführt werden, sollte die reale Welt hinter der von der Kamera gerendert werden. Legen Sie zu diesem Zweck den Kamera Hintergrund auf "transparent" (in hololens, schwarz rendert als transparent) anstelle einer Skybox-Textur fest:
    1. Wählen Sie die Hauptkamera im Hierarchie Panel aus.
    2. Suchen Sie im Inspektor-Panel die Kamera Komponente, und ändern Sie die Dropdown Liste Flag Löschen von Skybox in voll Tonfarbe.
    3. Wählen Sie die Hintergrund Farbauswahl aus, und ändern Sie die RGBA-Werte in (0,0).

Sie können Skriptcode verwenden, um zur Laufzeit zu bestimmen, ob das Headset durch das Überprüfen von [holographicsettings. isdisplayopisch](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)durch ein immersives oder Holographic ist.

## <a name="positioning-the-camera"></a>Positionieren der Kamera

Es ist einfacher, Ihre APP zu entwerfen, wenn Sie sich die Anfangsposition des Benutzers als (X: 0, Y: 0, Z: 0) vorstellen. Da die Hauptkamera die Bewegung des Benutzers nachverfolgt, kann die Startposition des Benutzers festgelegt werden, indem die Startposition der Hauptkamera festgelegt wird.

1. Auswählen der Hauptkamera im Hierarchie Panel
2. Suchen Sie im Inspektor-Panel die Transformations Komponente, und ändern Sie die Position von (x: 0, y: 1, z:-10) in (x: 0, y: 0, z: 0).

   ![Kamera im Inspektor-Bereich in Unity](images/maincamera-350px.png)  
   *Kamera im Inspektor-Bereich in Unity*

## <a name="clip-planes"></a>Clip Flächen

Das Rendern von Inhalten zu nahe am Benutzer kann in gemischter Realität unbequem sein. Sie können die [Near-und Far-Clip-Plane](hologram-stability.md#hologram-render-distances) in der Kamera Komponente anpassen.

1. Wählen Sie die Hauptkamera im Hierarchie Panel aus.
2. Suchen Sie im Inspektor-Panel nach den Ausschneide Flächen der Kamera Komponente, und ändern Sie das Textfeld in der Nähe von 0,3 in. 85. Inhalte, die noch enger gerendert werden, können zu Benutzer Unannehmlichkeiten führen und sollten gemäß den [Richtlinien für die renderentfernungs](hologram-stability.md#hologram-render-distances)

## <a name="multiple-cameras"></a>Mehrere Kameras

Wenn in der Szene mehrere Kamerakomponenten vorhanden sind, weiß Unity, welche Kamera für das stereorendern und die Head-Nachverfolgung verwendet werden soll, indem Sie überprüft, welches gameobject das maincamera-Tag hat.

## <a name="recentering-a-seated-experience"></a>Wiedergeben eines sitzenden Erlebnisses

Wenn Sie eine Umgebung mit [sitzender Skalierung](coordinate-systems.md)entwickeln, können Sie den Welt Ursprung von Unity an der aktuellen Hauptposition des Benutzers wiederholen, indem Sie den **[XR aufrufen. Inputtracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** -Methode.

## <a name="reprojection-modes"></a>Neuprojektions Modi

Sowohl hololens als auch immersive Headsets werden jeden Frame, der von der APP gerendert wird, neu projektet, um die tatsächliche Kopfzeile des Benutzers bei der Ausgabe von Phots anzupassen.

Standardmäßig:

* **Immersive Headsets** führen eine positionelle neuprojektion durch, wobei die Hologramme für die mitediction an Position und Ausrichtung angepasst werden, wenn die APP einen tiefen Puffer für einen bestimmten Frame bereitstellt.  Wenn kein tiefen Puffer bereitgestellt wird, korrigiert das System nur die Fehleinstellungen in der Ausrichtung.
* **Holographic-Headsets** wie hololens führen eine positionelle neuprojektion durch, unabhängig davon, ob die APP ihren tiefen Puffer bereitstellt.  Eine positionelle neuprojektion ist ohne tiefen Puffer in hololens möglich, da das Rendering häufig geringer ist, wenn ein stabiler Hintergrund von der realen Welt bereitgestellt wird.

Wenn Sie wissen, dass Sie eine [Ausrichtungs bezogene](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) Umgebung mit ordnungsgemäß gesperrtem Inhalt (z. b. Videoinhalt mit 360-Grad) entwickeln, können Sie den Modus für die neuprojektion explizit so festlegen, dass Sie nur eine Ausrichtung ist, indem Sie [holographicsettings. reprojectionmode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) auf [holographikreprojectionmode. orientationonly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)festlegen.

## <a name="sharing-your-depth-buffers-with-windows"></a>Freigeben von tiefen Puffern mit Windows

Durch die Freigabe des tiefen Puffers Ihrer APP für die einzelnen Frames erhält Ihre APP einen von zwei Verb esse ungen in der – Hologramm-Stabilität, basierend auf der Art des von Ihnen Renderns:

* **Immersive Headsets** können eine Positions neuprojektion durchführen, wenn ein tiefen Puffer bereitgestellt wird. Dadurch werden die Hologramme an der Position und der Ausrichtung für die mitediction angepasst.
* **Holographic-Headsets** haben einige verschiedene Methoden. Hololens 1 wählt automatisch einen [Fokuspunkt](focus-point-in-unity.md) aus, wenn ein tiefen Puffer bereitgestellt wird. Dadurch wird die – Hologramm-Stabilität entlang der Ebene optimiert, die den meisten Inhalt überschneidet. Hololens 2 stabilisiert Inhalte mithilfe der [tiefen LSR (siehe Hinweise)](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).

So legen Sie fest, ob Ihre Unity-APP einen tiefen Puffer für Windows bereitstellt:

1. Wechseln Sie zu **Edit** > **Project Settings** > **Player** > **universelle Windows-Plattform Tab** > **XR Settings**.
2. Erweitern Sie das **Windows Mixed Reality SDK** -Element.
3. Aktivieren oder deaktivieren Sie das Kontrollkästchen **Tiefe Puffer Freigabe aktivieren** .  Dies wird standardmäßig in neuen Projekten überprüft, die seit dem Hinzufügen dieses Features zu Unity erstellt wurden, und wird standardmäßig für ältere Projekte, die aktualisiert wurden, deaktiviert.

Das Bereitstellen eines tiefen Puffers für Windows kann die visuelle Qualität verbessern, solange Windows die normalisierten pro-Pixel-tiefen Werte in ihrem tiefen Puffer mithilfe der Near-und Far-Ebenen, die Sie in Unity auf der Hauptkamera festgelegt haben, exakt wieder zu den Entfernungen in Metern zuordnen kann.  Wenn Ihr renderingwert auf typische Weise handle-Werte übergibt, sollten Sie in der Regel in Ordnung sein, obwohl die übergreifende Renderingvorgänge, die in den tiefen Puffer schreiben, während Sie bis zu vorhandenen Farbpixeln zeigen, die neuprojektion verwirren können.  Wenn Sie wissen, dass Ihre Renderingdurchläufen viele der abschließenden tiefen Pixel mit ungenauen tiefen Werten belassen, erhalten Sie wahrscheinlich eine bessere visuelle Qualität, indem Sie die Option "Tiefe Puffer Freigabe aktivieren" deaktivieren.

## <a name="see-also"></a>Siehe auch

* [Hologrammstabilität](hologram-stability.md)
* [Mixedrealitytoolkit Hauptkamera. Prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)
