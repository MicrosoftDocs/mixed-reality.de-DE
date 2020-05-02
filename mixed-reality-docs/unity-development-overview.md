---
title: Unity-Entwicklung – Übersicht
description: Erste Schritte beim Erstellen von Mixed Reality-Apps in Unity.
author: thetuvix
ms.author: kurtie
ms.date: 10/25/2018
ms.topic: article
ms.localizationpriority: high
keywords: Unity, Mixed Reality, Entwicklung, erste Schritte, neues Projekt, Portieren, Funktion, Kamera, Simulation, Emulation, Dokumentation
ms.openlocfilehash: e0fe775f5fe891416145d91e52a5a801e049c568
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "81433416"
---
# <a name="unity-development-overview"></a>Unity-Entwicklung – Übersicht

Den schnellsten Weg zum Entwickeln einer [Mixed Reality-App](app-views.md) bietet [Unity](https://unity.com). Wir empfehlen Ihnen, sich mit den [Tutorials für Unity](https://unity3d.com/learn/tutorials) vertraut zu machen. Wenn Sie Ressourcen benötigen, finden Sie diese im umfangreich ausgestatteten [Asset Store](https://www.assetstore.unity3d.com/). Nachdem Sie ein grundlegendes Verständnis von Unity erworben haben, können Sie die [Tutorials](tutorials.md) besuchen, um die Besonderheiten der Mixed Reality-Entwicklung mit Unity zu erlernen. Besuchen Sie unbedingt die [Unity Mixed Reality-Foren](https://forum.unity3d.com/forums/hololens.102/), um sich mit der Community zu befassen, die Mixed Reality-Apps in Unity entwickelt, und Lösungen für möglicherweise auftretende Probleme zu finden.

Um in das Erstellen von Mixed Reality-Apps mit Unity einzusteigen, müssen Sie im ersten Schritt [die Tools installieren](install-the-tools.md). 

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Setting-up-your-HoloLens-2-development-environment/player?format=ny]

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>Neues Unity-Projekt mit Mixed Reality-Toolkit 

Die einfachste Möglichkeit zum Entwickeln in Unity stellt das Mixed Reality Toolkit dar. Es unterstützt Sie mit der automatischen Einrichtung des Projekts und bietet eine Reihe von Mixed-Reality-Funktionen zum Beschleunigen Ihrer Entwicklung. Unter [Mixed Reality Toolkit v2](mrtk-getting-started.md) erfahren Sie mehr und erhalten Informationen für den Einstieg. 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Portieren einer vorhandenen Unity-App zu Windows Mixed Reality

Wenn Sie über ein vorhandenes Unity-Projekt verfügen, das Sie zu Windows Mixed Reality portieren möchten, folgen Sie zunächst dem [Unity porting guide](porting-guides.md) (Unity-Portierungsleitfaden).

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>Konfigurieren eines neuen Unity-Projekts für Windows Mixed Reality

Wenn Sie ein neues Unity-Projekt erstellen möchten, ohne das Mixed Reality Toolkit zu importieren, müssen einige Unity-Einstellungen manuell geändert werden, um für Windows Mixed Reality zu entwickeln. Diese gliedern sich in zwei Kategorien: projektbezogene und szenenbezogene. Hier finden Sie eine Schrittanleitung zum [Konfigurieren eines neuen Unity-Projekts für Windows Mixed Reality](Configure-Unity-Project.md).

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Hinzufügen von Mixed Reality-Funktionen und -Eingaben

Sobald Sie MRTK V2 mit Ihrem Projekt eingerichtet oder das Projekt wie oben beschrieben konfiguriert haben, leuchten sofort Unity-Standardspielobjekte (wie etwa die Kamera) auf und bieten ein **sitzendes Aktivitätserlebnis**, bei dem sich die Kameraposition automatisch aktualisiert, wenn der Benutzer seinen Kopf in der Welt bewegt.

Das Hinzufügen von Unterstützung für Windows Mixed Reality-Funktionen, wie etwa [Raumbühnen](coordinate-systems.md#spatial-coordinate-systems), [Gesten, Motion Controller](gestures-and-motion-controllers-in-unity.md) oder [Spracheingabe](voice-input-in-unity.md) wird mithilfe von APIs erreicht, die direkt in Unity integriert sind. 

Überprüfen Sie zunächst die Optionen für den [Erlebnismaßstab](coordinate-systems.md), auf die Ihre Anwendung abzielen kann:
* Wenn Sie lediglich ein **nur zur Orientierung** gedachtes oder ein **sitzendes Aktivitätserlebnis** erstellen möchten, müssen Sie den Typ der Raumnachverfolgung von Unity auf [Stationary](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) (Stationär) festlegen.
* Wenn Sie ein **stehendes Aktivitätserlebnis** oder ein **Raumaktivitätserlebnis** erstellen möchten, müssen Sie darauf achten, dass der Typ der Raumnachverfolgung von Unity erfolgreich auf [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience) (Raummaßstab) festgelegt wurde.
* Wenn Sie ein **Weltaktivitätserlebnis** auf HoloLens erstellen möchten, mit dem die Benutzer sich in einem Bereich jenseits von 5 Metern bewegen können, müssen Sie die Komponente [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) (Weltanker) verwenden.

Alle Hauptbausteine für Mixed Reality-Anwendungen werden in einer Weise verfügbar gemacht, die mit anderen Unity-APIs konsistent ist. Sie sind ebenfalls über das Mixed Reality Toolkit verfügbar.
* [Kamera](camera-in-unity.md)
* [Koordinatensysteme](coordinate-systems-in-unity.md)
* [Anvisieren](gaze-in-unity.md)
* [Gesten und Motion-Controller](gestures-and-motion-controllers-in-unity.md)
* [Spracheingabe](voice-input-in-unity.md)
* [Persistenz](persistence-in-unity.md)
* [Raumklang](spatial-sound-in-unity.md)
* [Räumliche Abbildung](spatial-mapping-in-unity.md)

Es gibt noch weitere Schlüsselfunktionen, deren Einsatz in vielen Mixed Reality-Anwendungen sinnvoll ist, die Unity-Apps ebenfalls zur Verfügung stehen:
* [Gemeinsame Erfahrung](shared-experiences-in-unity.md)
* [Ausrichtbare Kamera](locatable-camera-in-unity.md)
* [Fokuspunkt](focus-point-in-unity.md)
* [Verlust der Nachverfolgung](tracking-loss-in-unity.md)
* [Tastatur](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>Ausführen Ihres Unity-Projekts auf einem realen oder simulierten Gerät

Sobald Sie Ihr Unity-Holografieprojekt bis zur Testreife gebracht haben, besteht der nächste Schritt im [Exportieren und Erstellen einer Unity Visual Studio-Projektmappe](exporting-and-building-a-unity-visual-studio-solution.md).

Mit dieser VS-Projektmappe können Sie Ihre Anwendung dann auf eine von drei Weisen ausführen und dazu wahlweise ein reales oder ein simuliertes Gerät verwenden:
* [Bereitstellen auf einer realen HoloLens oder einem immersiven Windows Mixed Reality-Headset](using-visual-studio.md)
* [Bereitstellen auf dem HoloLens-Emulator](using-the-hololens-emulator.md)
* [Bereitstellen auf dem Simulator für immersive Windows Mixed Reality-Headsets](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Unity-Dokumentation

Über diese Dokumentation hinaus, die auf docs.microsoft.com verfügbar ist, installiert Unity Dokumentation für Windows Mixed Reality-Funktionen zusammen mit dem Unity-Editor. Die von Unity bereitgestellte Dokumentation umfasst zwei separate Abschnitte:
1. **Unity-Skriptreferenz**
    * Dieser Abschnitt der Dokumentation behandelt die Skripterstellungs-API von Unity im Detail.
    * Auf sie kann im den Unity-Editor über **Hilfe > Skriptreferenz** zugegriffen werden.
2. **Unity-Handbuch**
    * Dieses Handbuch soll Ihnen helfen, die Verwendung von Unity zu erlernen, von grundlegenden bis zu erweiterten Techniken.
    * Sie können darauf im Unity-Editor über **Hilfe > Handbuch** zugreifen.

## <a name="see-also"></a>Siehe auch
* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [MR-Grundlagen 100: Erste Schritte mit Unity](holograms-100.md)
* [Empfohlene Einstellungen für Unity](recommended-settings-for-unity.md)
* [Leistungsempfehlungen für Unity](performance-recommendations-for-unity.md)
* [Exportieren und Erstellen einer Unity-Projektmappe für Visual Studio](exporting-and-building-a-unity-visual-studio-solution.md)
* [Verwenden des Windows-Namespace mit Unity-Apps für HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Bewährte Methoden für das Arbeiten mit Unity und Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity-Wiedergabemodus](unity-play-mode.md)
* [Portierungsleitfäden](porting-guides.md)
