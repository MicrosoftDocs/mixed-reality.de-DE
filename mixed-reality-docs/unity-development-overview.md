---
title: Übersicht über die Unity-Entwicklung
description: Erste Schritte beim Erstellen von mixed Reality-apps in Unity.
author: thetuvix
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, mixed Reality, Entwicklung, erste Schritte, neues Projekt, portieren, Funktion, Kamera, Simulation, Emulation, -Dokumentation
ms.openlocfilehash: 2cdcd5e997ab7e3f6d340377464e453a8e7c025c
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2019
ms.locfileid: "64874003"
---
# <a name="unity-development-overview"></a>Übersicht über die Unity-Entwicklung

Die schnellste Methode zum Erstellen einer [mixed Reality-app](app-views.md) ist mit [Unity](http://aka.ms/HoloLensUnity). Es wird empfohlen, Sie untersuchen die Zeit in Anspruch nehmen die [Unity-Tutorials](https://unity3d.com/learn/tutorials). Wenn Sie Ressourcen benötigen, ist Unity eine umfassende [Asset Store](https://www.assetstore.unity3d.com/). Nachdem Sie sich ein grundlegendes Verständnis von Unity erstellt haben, besuchen Sie die [Tutorials](tutorials.md) um die Einzelheiten der mixed Reality-Entwicklung mit Unity zu erfahren. Finden Sie die [Unity Mixed Reality-Foren](http://forum.unity3d.com/forums/hololens.102/) mit dem Rest der Entwicklung von mixed Reality-apps in Unity-Community beteiligen, und suchen Lösungen für Probleme, die Sie möglicherweise auftreten können.


Um zu beginnen, erstellen zunächst mixed Reality-apps mit Unity, [Installieren der Tools](install-the-tools.md). 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>Neue Unity-Projekt mit dem Mixed Reality-Toolkit 

Die einfachste Möglichkeit zum Entwickeln in Unity ist mithilfe von Mixed Reality-Toolkit. Sie können Setup mit dem Projekt automatisch, und geben Sie einen Satz von Mixed Reality-Funktionen zur Beschleunigung Ihrer Entwicklung. Sehen Sie sich [Mixed Reality-Toolkit v2](mrtk-getting-started.md) Sie weitere Informationen und erste Schritte. 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Portieren eine vorhandene Unity-app für Windows Mixed Reality

Wenn Sie ein vorhandenes Unity-Projekt, die Sie zum Windows Mixed Reality Portieren verfügen, befolgen Sie die [Leitfaden zum Portieren von Unity](porting-guides.md) für den Einstieg.

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>Konfigurieren der neues Unity-Projekt für Windows Mixed Reality

Wenn Sie ein neues Unity-Projekt erstellt, ohne Mixed Reality-Toolkit zu importieren möchten, stehen Ihnen eine kleine Gruppe von Unity-Einstellungen manuell ändern für Windows Mixed Reality, die in zwei Kategorien unterteilt müssen: pro Projekt und pro-Szene. Finden Sie hier, Schritt-für-Schritt-Anleitung für die [konfigurieren Sie die neue Unity-Projekt für Windows Mixed Reality](Configure-Unity-Project.md)

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Hinzufügen von mixed Reality-Funktionen und Eingaben

Nachdem Sie Setup MRTK V2 mit Ihrem Projekt haben oder Ihr Projekt wie oben beschrieben konfiguriert, standard Unity Spiele-Objekte (z. B. der Kamera) sind kompatibel sofort für einen **sitzen Skalierung Erfahrung**, mit die Position der Kamera aktualisiert verschiebt automatisch als Benutzer ihrem Kopf mit der ganzen Welt.

Hinzufügen von Unterstützung für Windows Mixed Reality-Features wie z. B. [räumliche Phasen](coordinate-systems.md#spatial-coordinate-systems), [Gesten, während der Übertragung Controller](gestures-and-motion-controllers-in-unity.md) oder [voice-Eingabe](voice-input-in-unity.md) wird erreicht, indem APIs direkt integriert Unity. 

Der erste Schritt sein sollte, um zu überprüfen die [auftreten Skalen](coordinate-systems.md) , die Ihre app kann als Ziel:
* Zum erstellen möchten eine **Ausrichtung nur** oder **sitzen Skalierung Erfahrung**, müssen Sie festlegen Unity den Monitortyp für Speicherplatz zum Nachverfolgen von [stationär](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Erstellen möchten eine **ständigen Skalierung** oder **Platz Skalierung Erfahrung**, müssen Sie Unity stellen Sie sicher Speicherplatz Überwachungstyp erfolgreich nastaven NA hodnotu [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* Wenn Sie zum Erstellen von suchen eine **weltweit einsetzbaren** experience auf HoloLens, ermöglichen es den Benutzern, die über 5 Meter wechseln, müssen Sie verwenden die [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) Komponente.

Alle von der wichtigsten Bausteine für mixed Reality-apps werden in Übereinstimmung mit anderen Unity-APIs verfügbar gemacht. Sie sind auch über Mixed Reality-Toolkit verfügbar.
* [Kamera](camera-in-unity.md)
* [Koordinatensysteme](coordinate-systems-in-unity.md)
* [Anvisieren](gaze-in-unity.md)
* [Gesten und Motion-Controller](gestures-and-motion-controllers-in-unity.md)
* [Spracheingabe](voice-input-in-unity.md)
* [Persistenz](persistence-in-unity.md)
* [Raumklang](spatial-sound-in-unity.md)
* [Räumliche Abbildung](spatial-mapping-in-unity.md)

Es gibt andere wichtige Features, dass viele mixed Reality-apps verwenden möchten, die werden auch für Unity-apps verfügbar gemacht werden:
* [Freigegebene Funktionen](shared-experiences-in-unity.md)
* [Ausrichtbare Kamera](locatable-camera-in-unity.md)
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
* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [MR-Grundlagen 100: Erste Schritte mit Unity](holograms-100.md)
* [Empfohlene Einstellungen für Unity](recommended-settings-for-unity.md)
* [Leistungsempfehlungen für Unity](performance-recommendations-for-unity.md)
* [Exportieren und Erstellen einer Unity-Projektmappe für Visual Studio](exporting-and-building-a-unity-visual-studio-solution.md)
* [Verwenden des Windows-Namespace mit Unity-Apps für HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Bewährte Methoden für das Arbeiten mit Unity und Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity-Wiedergabemodus](unity-play-mode.md)
* [Portieren von Führungslinien](porting-guides.md)
