---
title: Übersicht über Unity-Entwicklung
description: Beginnen Sie mit dem Aufbau gemischter Reality-apps in Unity.
author: thetuvix
ms.author: kurtie
ms.date: 10/25/2018
ms.topic: article
keywords: Unity, gemischte Realität, Entwicklung, Einstieg, neues Projekt, portieren, Funktion, Kamera, Simulation, Emulation, Dokumentation
ms.openlocfilehash: b78afb0cf6557ec9b61a029e2d557debbd0b6b46
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437372"
---
# <a name="unity-development-overview"></a>Übersicht über Unity-Entwicklung

Der schnellste Weg zum Entwickeln einer [mixed reality-app](app-views.md) besteht in [Unity](https://unity.com). Wir empfehlen Ihnen, sich mit den Lernprogrammen für [Unity](https://unity3d.com/learn/tutorials)vertraut zu machen. Wenn Sie Assets benötigen, verfügt Unity über einen umfassenden [Asset Store](https://www.assetstore.unity3d.com/). Nachdem Sie ein grundlegendes Verständnis von Unity erstellt haben, können Sie die Lernprogramme aufrufen [, um sich mit den Besonderheiten](tutorials.md) der Mixed Reality-Entwicklung mit Unity vertraut zu machen. Stellen Sie sicher, dass Sie die Unity-Foren in der [gemischten Realität](https://forum.unity3d.com/forums/hololens.102/) besuchen, um sich mit der restlichen Community zu befassen, die gemischte Reality-apps in Unity aufbaut und Lösungen für Probleme finden kann, die möglicherweise auftreten

Installieren Sie zunächst [die Tools](install-the-tools.md), um mit der Einführung von Mixed Reality-apps zu beginnen. 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>Neues Unity-Projekt mit Mixed Reality Toolkit 

Die einfachste Möglichkeit zur Entwicklung von Unity ist das Mixed Reality Toolkit. Auf diese Weise können Sie das Projekt automatisch einrichten und eine Reihe gemischter Reality-Funktionen bereitstellen, um Ihre Entwicklung zu beschleunigen. Weitere Informationen und den Einstieg finden Sie unter [Mixed Reality Toolkit v2](mrtk-getting-started.md) . 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Portieren einer vorhandenen Unity-App auf Windows Mixed Reality

Wenn Sie über ein vorhandenes Unity-Projekt verfügen, das Sie auf Windows Mixed Reality portieren, befolgen Sie die Anleitung zum Einstieg in die [Unity-Portierung](porting-guides.md) .

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>Konfigurieren eines neuen Unity-Projekts für Windows Mixed Reality

Wenn Sie ein neues Unity-Projekt erstellen möchten, ohne Mixed Reality Toolkit zu importieren, gibt es eine kleine Sammlung von Unity-Einstellungen, die Sie manuell für Windows Mixed Reality ändern müssen. Diese werden in zwei Kategorien unterteilt: pro Projekt und pro Szene. Eine Schritt-für-Schritt-Anleitung zum [Konfigurieren eines neuen Unity-Projekts für Windows Mixed Reality](Configure-Unity-Project.md) finden Sie hier.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>Hinzufügen gemischter Reality-Funktionen und-Eingaben

Wenn Sie mrtk v2 mit Ihrem Projekt eingerichtet haben oder Ihr Projekt wie oben beschrieben konfiguriert haben, werden standardmäßige Unity-Spielobjekte (z. b. die Kamera) sofort für eine **skalierte**Benutzeroberfläche aktualisiert, wobei die Position der Kamera automatisch aktualisiert wird. der Benutzer wechselt in die Welt.

Das Hinzufügen von Unterstützung für Windows Mixed Reality-Features, z. b. [räumliche Stufen](coordinate-systems.md#spatial-coordinate-systems), [Gesten, Bewegungs Controller](gestures-and-motion-controllers-in-unity.md) oder [Spracheingaben](voice-input-in-unity.md) , wird mithilfe der direkt in Unity erstellten APIs erreicht. 

Überprüfen Sie zunächst die [Skalierungs](coordinate-systems.md) Möglichkeiten, die ihre applicatioin als Ziel haben können:
* Wenn Sie **nur eine Orientierung** oder eine **Skalierung**mit fester Größe erstellen möchten, müssen Sie den Überwachungsbereich von Unity auf " [stationär](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)" festlegen.
* Wenn **Sie eine Skalierungs-oder** **Raum Skalierungs**Oberfläche erstellen möchten, müssen Sie sicherstellen, dass der nach verfolgungsbereich von Unity erfolgreich auf " [roomscale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)" festgelegt ist.
* Wenn Sie eine **Welt weite** Umgebung auf hololens aufbauen möchten, die Benutzern das Roaming über 5 Meter ermöglicht, müssen Sie die [worldanchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) -Komponente verwenden.

Alle Kern Bausteine für gemischte Reality-Anwendungen werden auf eine Weise verfügbar gemacht, die mit anderen Unity-APIs konsistent ist. Sie sind auch über das Mixed Reality Toolkit verfügbar.
* [Kamera](camera-in-unity.md)
* [Koordinatensysteme](coordinate-systems-in-unity.md)
* [Anvisieren](gaze-in-unity.md)
* [Gesten und Bewegungs Controller](gestures-and-motion-controllers-in-unity.md)
* [Spracheingabe](voice-input-in-unity.md)
* [Persistenz](persistence-in-unity.md)
* [Raumklang](spatial-sound-in-unity.md)
* [Räumliche Abbildung](spatial-mapping-in-unity.md)

Es gibt noch weitere wichtige Features, die viele gemischte Reality-Anwendungen verwenden möchten, die auch für Unity-apps verfügbar gemacht werden:
* [Freigegebene Erfahrungen](shared-experiences-in-unity.md)
* [Ausrichtbare Kamera](locatable-camera-in-unity.md)
* [Fokuspunkt](focus-point-in-unity.md)
* [Nachverfolgung von Verlusten](tracking-loss-in-unity.md)
* [Tastatur](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>Ausführen Ihres Unity-Projekts auf einem echten oder simulierten Gerät

Nachdem Sie Ihr Holographic-Unity-Projekt zum Testen vorbereitet haben, ist der nächste Schritt das [exportieren und Erstellen einer Unity-Visual Studio-](exporting-and-building-a-unity-visual-studio-solution.md)Projekt Mappe.

Mit dieser vs-Lösung können Sie die Anwendung dann auf eine von drei Arten ausführen, indem Sie entweder ein reales oder ein simuliertes Gerät verwenden:
* [Bereitstellen in einem echten hololens oder Windows Mixed Reality-immersives Headset](using-visual-studio.md)
* [Bereitstellen auf dem hololens-Emulator](using-the-hololens-emulator.md)
* [Bereitstellen für den Windows Mixed Reality-immersiven Headset-Simulator](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Unity-Dokumentation

Zusätzlich zu dieser Dokumentation, die auf docs.Microsoft.com verfügbar ist, installiert Unity zusätzlich zum Unity-Editor die Dokumentation für die Windows Mixed Reality-Funktionalität. Die bereitgestellte Unity-Dokumentation enthält zwei separate Abschnitte:
1. **Unity-Skript Referenz**
    * Dieser Abschnitt der Dokumentation enthält Details zur Skript-API, die von Unity bereitstellt wird.
    * Zugriff über den Unity-Editor über **Hilfe > Skript Referenz**
2. **Unity-Handbuch**
    * Dieses Handbuch soll Ihnen helfen, die Verwendung von Unity von grundlegenden bis zu erweiterten Techniken zu erlernen.
    * Zugriff über den Unity-Editor über **Hilfe > manuell**

## <a name="see-also"></a>Weitere Informationen:
* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [Grundlagen 100: Einstieg in Unity](holograms-100.md)
* [Empfohlene Einstellungen für Unity](recommended-settings-for-unity.md)
* [Leistungsempfehlungen für Unity](performance-recommendations-for-unity.md)
* [Exportieren und Erstellen einer Unity-Projektmappe für Visual Studio](exporting-and-building-a-unity-visual-studio-solution.md)
* [Verwenden des Windows-Namespace mit Unity-Apps für HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Bewährte Methoden für das Arbeiten mit Unity und Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity-Wiedergabemodus](unity-play-mode.md)
* [Portieren von Führungslinien](porting-guides.md)
