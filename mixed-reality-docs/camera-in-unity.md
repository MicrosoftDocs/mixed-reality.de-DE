---
title: Kamera in Unity
description: Wie Sie mit Unity Main Camera für Windows Mixed Reality-Entwicklung, holographic rendern möchten
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Holotoolkit, Mixedrealitytoolkit, Mixedrealitytoolkit-Unity, holographic Rendering, holographic, immersive Fokuspunkt, Tiefenpuffer, Ausrichtung nur mit Feldern fester Breite, nicht transparenten, transparent, clip
ms.openlocfilehash: 8ea5a1f53351faab1b2863a0afac74e958b4b1a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593337"
---
# <a name="camera-in-unity"></a>Kamera in Unity

Wenn Sie einen Kopfhörer mixed Reality wear, wird es der Mitte des Ihre holographic Welt. Unity [Kamera](http://docs.unity3d.com/Manual/class-Camera.html) Komponente stereoskopische Rendering automatisch behandelt, und folgen Ihre Bewegungen und Drehung, wenn das Projekt "Virtuelle Realität unterstützt" mit "Windows Mixed Reality" ausgewählt verfügt wie das Gerät (in Abschnitt Weitere Einstellungen der Windows Store-Player-Einstellungen). Dies kann als "Windows Holographic" in älteren Versionen von Unity aufgeführt sein.

Jedoch vollständig visuelle Qualität zu optimieren und [– Hologramm Stabilität](hologram-stability.md), sollten Sie die unten beschriebenen Kameraeinstellungen festlegen.

>[!NOTE]
>Diese Einstellungen müssen auf die Kamera in jeder Szene Ihrer App angewendet werden.
>
>Standardmäßig, wenn Sie eine neue Szene in Unity erstellen enthält sie ein Main Camera "gameobject" in der Hierarchie, die die Kamera-Komponente enthält, jedoch verfügt nicht über die folgenden ordnungsgemäß angewendeten Einstellungen.

## <a name="holographic-vs-immersive-headsets"></a>Im Vergleich zu immersive Headsets holographic

Die Standardeinstellungen für die Unity-Kamera-Komponente sind für herkömmliche 3D-Anwendungen die Skybox-ähnliche Hintergrund benötigen, wie sie eine reale Welt über keine verfügen.
* Bei der Ausführung unter einem  **[immersive Kopfhörer](immersive-headset-hardware-details.md)** Sie den Rendervorgang alles, was dem Benutzer angezeigt wird und daher Sie werden wahrscheinlich die Skybox beibehalten möchten.
* Allerdings bei der Ausführung unter einem **holographic Kopfhörer** wie [HoloLens](hololens-hardware-details.md), die reale Welt sollte angezeigt werden hinter alles, was die Kamera gerendert. Zu diesem Zweck legen Sie die Kamera-Hintergrund transparent (in HoloLens, Schwarz gerendert als transparent) anstelle einer Textur Skybox:
    1. Wählen Sie die Main Camera im Bedienfeld "Hierarchie"
    2. Im Bereich mit den Inspektor finden Sie die Kamera-Komponente und der deaktivieren-Flags-Dropdownliste von Skybox in Volltonfarbe
    3. Wählen Sie die Hintergrund-Farbauswahl, und ändern Sie die RGBA-Werte (0, 0, 0, 0)

Können Sie Skriptcode zur Laufzeit bestimmen, ob die Kopfhörer immersive oder holographic anhand [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).


## <a name="positioning-the-camera"></a>Positionieren die Kamera

Es wird einfacher sein, das Layout von Ihrer app, wenn Sie sich, die Anfangsposition des Benutzers als (x vorstellen:) 0, Y: 0, Z: 0). Da die Main Camera Bewegung des Benutzers Head nachverfolgt, kann die Anfangsposition des Benutzers festgelegt werden, durch die Position der Kamera Main festlegen.
1. Wählen Sie im Bereich Hierarchie Main Camera
2. Klicken Sie im Bereich mit den Inspektor suchen Sie die Transformationskomponente, und ändern Sie die Position von (x:) 0, Y: 1, Z:-10), (x:) 0, Y: 0, Z: 0)

   ![Kamera in den Bereich der Eigenschaftenanalyse in Unity](images/maincamera-350px.png)<br>
   *Kamera in den Bereich der Eigenschaftenanalyse in Unity*

## <a name="clip-planes"></a>Clip-Ebenen

Rendern von Inhalt zu schließen, um kann der Benutzer in mixed Reality unbequem sein. Sie können anpassen, die [in der Nähe und weit beschneiden Ebenen](hologram-stability.md#hologram-render-distances) auf die Kamera-Komponente.
1. Wählen Sie die Main Camera im Bedienfeld "Hierarchie"
2. Klicken Sie im Bereich mit den Inspektor finden Sie die Kamera Komponente Clipping Planes, und ändern Sie das nahe Textfeld aus 0.3 in.85. Inhalt gerendert, noch näher zu Benutzer angefasst führen kann und sollte vermieden werden, pro der [Rendern Abstand Richtlinien](hologram-stability.md#hologram-render-distances).

## <a name="multiple-cameras"></a>Mehrere Kameras

Wenn mehrere Komponenten der Kamera in der Szene vorhanden sind, Unity weiß, welche Kamera für stereoskopische Rendering verwendet und Head Überwachung durch Überprüfen der "gameobject" verfügt über das MainCamera-Tag.

## <a name="recentering-a-seated-experience"></a>Eine sitzende Erfahrung recentering

Erstellen einer [sitzen Skalierung Erfahrung](coordinate-systems.md), können Sie verschoben Unity Welt Ursprung an aktuellen Head-Position des Benutzers durch Aufrufen der **[XR. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** Methode.

## <a name="reprojection-modes"></a>Reprojection-Modi

Sowohl HoloLens auch immersive Headsets werden jeder Frame reproject Ihrer app rendert, für alle Misprediction der tatsächlichen Head-Position des Benutzers angepasst werden, wenn Photonen ausgegeben werden.

Standardmäßig:

* **Immersive Headsets** führt Sie Positionsparameter Reprojection, Ihre Hologramme für Misprediction in Position und Ausrichtung anpassen, wenn die app einen Tiefenpuffer für einen bestimmten Frame bereitstellt.  Wenn ein Tiefenpuffer nicht angegeben wird, wird das System nur Mispredictions Ausrichtung behoben.
* **Holographic Headsets** wie HoloLens mit Feldern fester Breite Reprojection ausgeführt wird, ob die app die Tiefenpuffer oder nicht bietet.  Mit Feldern fester Breite Reprojection ist ohne Tiefenpuffern für HoloLens möglich, da Rendering häufig mit einem stabilen Hintergrund, die von der realen Welt bereitgestellt geringe Dichte aufweist.

Wenn Sie wissen, dass Sie erstellen eine [Ausrichtung ausschließlich Erfahrung](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) mit fest gesperrt Text-Inhalt (z. B. 360-Grad-Videoinhalte), können Sie explizit legen den Modus Reprojection Ausrichtung nur durch das Einrichten sein [ HolographicSettings.ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) zu [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).

## <a name="sharing-your-depth-buffers-with-windows"></a>Freigeben Ihrer Tiefenpuffern für Windows

Gemeinsame Nutzung Ihrer app Tiefenpuffer, Windows, die jeden Frame Ihrer app eine der beiden steigert – Hologramm Stabilität, basierend auf den Typ des Kopfhörer erhalten, sind Sie für Rendern:
* **Immersive Headsets** können mit Feldern fester Breite Reprojection ausführen, wenn ein Tiefenpuffer Anpassen Ihrer Hologramme für Misprediction in Position und Ausrichtung angegeben wird,.
* **Holographic Headsets** wie HoloLens automatisch auswählt, ein [konzentrieren Punkt](focus-point-in-unity.md) bei ein Tiefenpuffer angegeben ist, optimieren – Hologramm Stabilität entlang der Ebene, die den Inhalt überschneidet.

So legen Sie fest, ob es sich bei Ihrer Unity-app einen Tiefenpuffer zu Windows bereitstellt:
1. Wechseln Sie zu **bearbeiten** > **Projekteinstellungen** > **Player** > **Registerkarte für die universelle Windows-Plattform**  >  **XR-Einstellungen**.
2. Erweitern Sie die **Windows Mixed Reality SDK** Element.
3. Aktivieren oder deaktivieren Sie die **Tiefe Puffer Freigabe aktivieren** Kontrollkästchen.  Dies wird standardmäßig in neuen Projekten, die erstellt werden, da diese Funktion, um Unity hinzugefügt wurde und deaktiviert werden standardmäßig für die älteren Projekten überprüft werden, die aktualisiert wurden.

Bereitstellen von einem Tiefenpuffer für Windows kann visuelle Qualität verbessern, solange Windows genau die normalisierte pro-Pixel-Depth-Werte in Ihre Tiefenpuffer an entfernungen in Verbrauchseinheiten gemessen zuordnen können, die Nahen und Fern Ebenen, die Sie in Unity, auf die Hauptkamera festgelegt haben mit.  Wenn Ihre Render Handle Tiefe übergibt die Werte in typischen Möglichkeiten, Sie in der Regel muss in Ordnung, hier jedoch lichtdurchlässiger rendern, Schreiben der Tiefenpuffer beim mit mit vorhandenen übergibt Farbpixel können zur Verwirrung beitragen die Reprojection.  Wenn Sie wissen, dass es sich bei Ihrer Rendering-Durchläufe vieler Ihrer letzten Tiefe Pixel mit ungenauen Warteschlangenlänge hinterlässt, sind Sie wahrscheinlich eine bessere visuellen Qualität durch Deaktivieren "Tiefe Puffer Freigabe aktivieren".

## <a name="mixed-reality-toolkits-automatic-scenesetup"></a>Die automatische Szene Setup Mixed Reality-Toolkit
Beim Importieren von [MRTK releasepakete Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) oder Klonen Sie das Projekt aus der [GitHub-Repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), Sie sind dabei, ein neues Menü "Mixed Reality-Toolkit" in Unity finden. Klicken Sie im Menü "Mixed Reality Szene-Einstellungen anwenden" wird unter "Konfigurieren" im Menü angezeigt. Wenn Sie darauf klicken, wird er entfernt die Standardkamera und fügt grundlegende Komponenten - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), und [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).

![MRTK-Menü für die Szene-setup](images/MRTK_Input_Menu.png)<br>
*MRTK-Menü für die Szene-setup*

![Automatische Szene Setup in MRTK](images/MRTK_HowTo_Input1.png)<br>
*Automatische Szene Setup in MRTK*

## <a name="mixedrealitycamera-prefab"></a>MixedRealityCamera prefabs
Sie können diese aus dem Projektfenster auch manuell hinzufügen. Sie finden diese Komponenten als prefabs (Vorlagen). Bei der Suche **MixedRealityCamera**, Sie werden zwei verschiedene Kamera prefabs (Vorlagen) angezeigt. Der Unterschied besteht darin, **MixedRealityCamera** ist die Kamera nur prefab dagegen **MixedRealityCameraParent** enthält zusätzliche Komponenten für die immersive Headsets wie z. B. Teleportation, während der Übertragung Controller und Grenze.

![Kamera-Prefabs im MRTK](images/MRTK_HowTo_Input2.png)<br>
*Kamera-Prefabs im MRTK*

**MixedRealtyCamera** HoloLens und immersive Kopfhörer unterstützt. Erkennt den Gerätetyp und die Eigenschaften wie z. B. deaktivieren Flags und Skybox optimiert. Im folgenden können Sie einige nützliche Eigenschaften suchen, die können Sie z. B. benutzerdefinierte Cursor, während der Übertragung Controller-Modellen, anpassen und Floor.

![Eigenschaften für den Controller während der Übertragung, Cursor und Floor](images/MRTK_HowTo_Input3.png)<br>
*Eigenschaften für den Controller während der Übertragung, Cursor und Floor*

## <a name="see-also"></a>Siehe auch
* [– Hologramm Stabilität](hologram-stability.md)
* [MixedRealityToolkit Main Camera.prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)
