---
title: Übersicht über die Unity-Entwicklung
description: Erste Schritte beim Erstellen von mixed Reality-apps in Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, mixed Reality, Entwicklung, erste Schritte, neues Projekt, portieren, Funktion, Kamera, Simulation, Emulation, -Dokumentation
ms.openlocfilehash: fc40ef4eae31cf22f640be2666c5af3afb717ff3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604545"
---
# <a name="unity-development-overview"></a>Übersicht über die Unity-Entwicklung

Die schnellste Methode zum Erstellen einer [mixed Reality-app](app-views.md) ist mit [Unity](http://aka.ms/HoloLensUnity). Es wird empfohlen, Sie untersuchen die Zeit in Anspruch nehmen die [Unity-Tutorials](https://unity3d.com/learn/tutorials). Wenn Sie Ressourcen benötigen, ist Unity eine umfassende [Asset Store](https://www.assetstore.unity3d.com/). Nachdem Sie sich ein grundlegendes Verständnis von Unity erstellt haben, besuchen Sie die [Mixed Reality Academy](academy.md) um die Einzelheiten der mixed Reality-Entwicklung mit Unity zu erfahren. Finden Sie die [Unity Mixed Reality-Foren](http://forum.unity3d.com/forums/hololens.102/) mit dem Rest der Entwicklung von mixed Reality-apps in Unity-Community beteiligen, und suchen Lösungen für Probleme, die Sie möglicherweise auftreten können.

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Portieren eine vorhandene Unity-app für Windows Mixed Reality

Wenn Sie ein vorhandenes Unity-Projekt, die Sie zum Windows Mixed Reality Portieren verfügen, befolgen Sie die [Leitfaden zum Portieren von Unity](porting-guides.md) für den Einstieg.

## <a name="configuring-a-new-unity-project-for-windows-mixed-reality"></a>Konfigurieren ein neues Unity-Projekt für die Windows Mixed Reality

Um zu beginnen, erstellen zunächst mixed Reality-apps mit Unity, [Installieren der Tools](install-the-tools.md). Wenn Sie Windows Mixed Reality immersive Headsets anstelle von HoloLens verwenden werden müssen, benötigen Sie eine spezielle Version von Unity für jetzt.

Wenn Sie ein neues Unity-Projekt gerade erstellt haben, stehen Ihnen eine kleine Gruppe von Unity-Einstellungen so ändern Sie für Windows Mixed Reality, die in zwei Kategorien unterteilt müssen: pro Projekt und pro-Szene.

### <a name="per-project-settings"></a>Einstellungen pro Projekt

Um Windows Mixed Reality Ziel festzulegen, müssen Sie zuerst Ihr Unity-Projekt als universelle Windows-Plattform-app exportieren festlegen:
1. Wählen Sie **Datei > Buildeinstellungen...**
2. Wählen Sie **universelle Windows-Plattform** in die Plattform aus, und klicken Sie auf **Plattform wechseln**
3. Legen Sie **SDK** zu **universelle 10**
4. Legen Sie **Zielgerät** zu **einem beliebigen Gerät** zur Unterstützung einer immersive Headsets aus, oder wechseln Sie zur **HoloLens**
5. Legen Sie **Buildtyp** zu **D3D**
6. Legen Sie **UWP SDK** zu **zuletzt installierte**

Klicken Sie dann müssen wir wissen, dass die app aus, es versucht wird, exportieren, zu erstellen, sollten Unity können eine [immersive Ansicht](app-views.md) anstelle einer 2D-Ansicht. Zu diesem Zweck aktivieren "Virtuelle Realität unterstützt":
1. Von der **Buildeinstellungen...**  geöffnete Fenster **Playereinstellungen...**
2. Wählen Sie die **Einstellungen für die universelle Windows-Plattform** Registerkarte
3. Erweitern Sie die **XR-Einstellungen** Gruppe
4. In der **XR-Einstellungen** aktivieren Sie im Abschnitt der **virtuelle Realität unterstützt** Kontrollkästchen zum Hinzufügen der **Virtual Reality-Geräte** Liste.
5. In der **XR-Einstellungen** gruppieren, überprüfen Sie, ob **"Windows Mixed Reality"** wird als ein unterstütztes Gerät aufgeführt. (Dies kann als "Windows Holographic" in älteren Versionen von Unity angezeigt)

Ihre app kann nun grundlegende holographic Rendering und räumliche Eingabe erfolgen. Um weiter gehen und bestimmte Funktionen nutzen, muss Ihre app die entsprechenden Funktionen im Manifest deklariert werden. Die manifest-Deklarationen können in Unity vorgenommen werden, damit sie in jedem nachfolgenden Projektexport enthalten sind. Die Einstellung finden Sie im **Playereinstellungen > Einstellungen für die universelle Windows-Plattform > Veröffentlichungseinstellungen > Funktionen**. Die entsprechenden Funktionen für die Aktivierung von häufig verwendeten Unity-APIs für Mixed Reality sind:

|  Funktion  |  APIs, die Funktion erfordern | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (Zugriff auf [räumliche Zuordnung](spatial-mapping.md) Gitter für HoloLens)&mdash;*keine Funktion, die für allgemeine räumliche nachverfolgung von den Kopfhörer erforderlich sind* | 
|  WebCam  |  PhotoCapture und VideoCapture | 
|  PicturesLibrary / "videoslibrary"  |  PhotoCapture oder VideoCapture, bzw. (bei den aufgezeichneten Inhalt zu speichern) | 
|  Mikrofon  |  VideoCapture (wenn Audio erfassen), DictationRecognizer, GrammarRecognizer und KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (und mit der Unity-Profiler) | 

**Einstellungen für die Qualität von Unity**

![Einstellungen für die Qualität von Unity](images/unityqualitysettings-350px.png)<br>
*Einstellungen für die Qualität von Unity*

HoloLens verfügt über eine GPU-Mobile-Klasse. Wenn Ihre app HoloLens ausgelegt ist, sollten Sie die Qualität-Einstellungen für schnellste Leistung optimiert, um sicherzustellen, dass wir die vollständige Framerate verwalten:
1. Wählen Sie **Bearbeiten > Projekteinstellungen > Qualität**
2. Wählen Sie die **Dropdownliste** unter der **Windows Store** Logo, und wählen **schnellste**. Wissen Sie, dass die Einstellung ist ordnungsgemäß angewendet, wenn das Feld in der Windows Store-Spalte und **schnellste** Zeile wird grün angezeigt.

### <a name="per-scene-settings"></a>Pro-Szene-Einstellungen

**Unity-Kameraeinstellungen**

![Unity-Kameraeinstellungen](images/unitycamerasettings.png)<br>
*Unity-Kameraeinstellungen*

Nachdem Sie das Kontrollkästchen "Virtuelle Realität unterstützt" aktiviert die [Unity Kamera](camera-in-unity.md) führt [head-nachverfolgung und stereoskopische Rendering](rendering.md). Es ist nicht erforderlich, es mit einer benutzerdefinierten Kamera dazu ersetzen.

Wenn Ihre app speziell HoloLens ausgelegt ist, haben Sie einige Einstellungen, die geändert werden, um die für das Gerät die transparent angezeigt, und zu optimieren, damit Ihre app durch, die physische Welt angezeigt werden müssen:
1. In der **Hierarchie**, wählen die **Main Camera**
2. In der **Inspektor** legen Sie die Transformation **Position** zu **0, 0, 0** sodass gestartet wird, der Speicherort des Anfangswerts Benutzer auf den Ursprung der Unity-Welt.
3. Änderung **Kennzeichnungen löschen** zu **Volltonfarbe**.
4. Ändern der **Hintergrund** Farbe **RGBA 0,0,0,0**. Schwarz, die als Transparenz HoloLens gerendert werden.
5. Änderung **Clipping Planes - nahezu** auf die [HoloLens empfohlen](camera-in-unity.md#clip-planes) 0,85 (Meter).

Wenn Sie zu löschen und erstellen eine neue Kamera, stellen Sie sicher, dass Ihre Kamera **markierter** als **MainCamera**.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Hinzufügen von mixed Reality-Funktionen und Eingaben

Nachdem Sie Ihr Projekt wie oben beschrieben konfiguriert haben, standard Unity Spiele-Objekte (z. B. der Kamera) sind kompatibel sofort für eine **sitzen Skalierung Erfahrung**, mit die Position der Kamera automatisch aktualisiert, als der Benutzer verschoben Ihrem Kopf mit der ganzen Welt.

Hinzufügen von Unterstützung für Windows Mixed Reality-Features wie z. B. [räumliche Phasen](coordinate-systems.md#spatial-coordinate-systems), [Gesten, während der Übertragung Controller](gestures-and-motion-controllers-in-unity.md) oder [voice-Eingabe](voice-input-in-unity.md) wird erreicht, indem APIs direkt integriert Unity.

Der erste Schritt sein sollte, um zu überprüfen die [auftreten Skalen](coordinate-systems.md) , die Ihre app kann als Ziel:
* Zum erstellen möchten eine **Ausrichtung nur** oder **sitzen Skalierung Erfahrung**, müssen Sie festlegen Unity den Monitortyp für Speicherplatz zum Nachverfolgen von [stationär](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Erstellen möchten eine **ständigen Skalierung** oder **Platz Skalierung Erfahrung**, müssen Sie Unity stellen Sie sicher Speicherplatz Überwachungstyp erfolgreich nastaven NA hodnotu [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Wenn Sie zum Erstellen von suchen eine **weltweit einsetzbaren** experience auf HoloLens, ermöglichen es den Benutzern, die über 5 Meter wechseln, müssen Sie verwenden die [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) Komponente.

Alle von der wichtigsten Bausteine für mixed Reality-apps werden in Übereinstimmung mit anderen Unity-APIs zur Verfügung gestellt:
* [Kamera](camera-in-unity.md)
* [Koordinatensysteme](coordinate-systems-in-unity.md)
* [Blicke](gaze-in-unity.md)
* [Gesten und Motion-Controller](gestures-and-motion-controllers-in-unity.md)
* [Spracheingabe](voice-input-in-unity.md)
* [Persistenz](persistence-in-unity.md)
* [Räumliche sound](spatial-sound-in-unity.md)
* [Räumliche Zuordnung](spatial-mapping-in-unity.md)

Es gibt andere wichtige Features, dass viele mixed Reality-apps verwenden möchten, die werden auch für Unity-apps verfügbar gemacht werden:
* [Freigegebene Funktionen](shared-experiences-in-unity.md)
* [Gebietsschemabezogene Kamera](locatable-camera-in-unity.md)
* [Fokuspunkt](focus-point-in-unity.md)
* [Verlust der Überwachung](tracking-loss-in-unity.md)
* [Tastatur](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>Ausführen Ihres Unity-Projekts auf einem echten oder simulierten Gerät

Nachdem Sie Ihr holographic Unity-Projekt bereit, um zu testen haben, ist der nächste Schritt zu [exportieren, und Erstellen von Unity Visual Studio-Projektmappe](exporting-and-building-a-unity-visual-studio-solution.md).

Der Visual Studio-Lösung verfügen können Sie Ihrer app in einem der drei Arten ausführen entweder eine echte oder simulierte Gerät:
* [Bereitstellen Sie in einer echten immersive Kopfhörer HoloLens oder Windows Mixed Reality](using-visual-studio.md)
* [Bereitstellen Sie mit dem Emulator für HoloLens](using-the-hololens-emulator.md)
* [Bereitstellen Sie in Windows Mixed Reality immersive Kopfhörer simulator](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Unity-Dokumentation

Zusätzlich zu dieser Dokumentation verfügbar im Windows Dev Center installiert die Unity Dokumentation für Windows Mixed Reality-Funktionen zusammen mit der Unity-Editor. Unity angegeben, dass die Dokumentation über zwei separate Abschnitte enthält:
1. **Unity-skriptreferenz**
    * In diesem Abschnitt der Dokumentation enthält die Details der Skripting-API, die Unity bietet.
    * Verfügbar im Unity-Editor über **Hilfe > Skriptreferenz**
2. **Unity-Leitfaden**
    * Dieses Handbuch soll erfahren, wie Sie Unity aus "einfach" zu erweiterten Techniken zu verwenden.
    * Verfügbar im Unity-Editor über **Hilfe > manuell**

## <a name="see-also"></a>Siehe auch
* [MR Basics 100: Erste Schritte mit Unity](holograms-100.md)
* [Empfohlene Einstellungen für Unity](recommended-settings-for-unity.md)
* [Empfehlungen zur Leistung für Unity](performance-recommendations-for-unity.md)
* [Exportieren und Erstellen von Unity Visual Studio-Projektmappe](exporting-and-building-a-unity-visual-studio-solution.md)
* [Mithilfe des Windows-Namespaces mit Unity-apps für HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Bewährte Methoden für die Arbeit mit Unity und Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity-Spielmodus](unity-play-mode.md)
* [Portieren von Führungslinien](porting-guides.md)
