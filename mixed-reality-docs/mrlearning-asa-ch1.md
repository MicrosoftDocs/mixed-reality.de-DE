---
title: Tutorials zu Azure Spatial Anchor-1. Ersten Einstieg in Azure Spatial Anchor
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 0163b61bfbf8bd583532092581d94f63e1c2a624
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554674"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Einstieg in Azure Spatial Anchor

## <a name="overview"></a>Übersicht

Willkommen bei der zweiten Reihe der hololens 2-Tutorials. In dieser dreiteiligen tutorialreihe erfahren Sie mehr über die Grundlagen von räumlichen Azure-Ankern.

In diesem ersten Tutorial, den ersten Schritten [mit räumlichen Azure-Ankern](mrlearning-asa-ch1.md), werden die verschiedenen Schritte erläutert, die zum Starten und Beenden einer Azure-Sitzung sowie zum Erstellen, hochladen und Herunterladen von Azure-Ankern auf einem einzelnen Gerät erforderlich sind.

Im zweiten Tutorial zum [speichern, abrufen und Freigeben von räumlichen Azure-Ankern](mrlearning-asa-ch2.md)erfahren Sie, wie Sie räumliche Azure-Anker in mehreren App-Sitzungen speichern, indem Sie Anker Informationen im Speicher von hololens 2 speichern und diese Anker Informationen für eine Anker Ausrichtung mit mehreren Geräten an andere Geräte weitergeben.

Im dritten Tutorial, in dem das [Azure Spatial Anchor-Feedback angezeigt](mrlearning-asa-ch3.md)wird, erfahren Sie, wie Sie Benutzern Feedback zu Anker Ereignissen und-Status bei der Verwendung von räumlichen Azure-Ankern bereitstellen.

## <a name="objectives"></a>Ziele

* Erfahren Sie mehr über die Grundlagen der Entwicklung mit räumlichen Azure-Ankern für hololens 2
* Erstellen, hochladen und herunterladen räumlicher Anker

## <a name="prerequisites"></a>Erforderliche Komponenten

>[!TIP]
>Wenn Sie die Reihe "erste Schritte" noch nicht abgeschlossen haben, empfiehlt es sich, [diese Tutorials zuerst](mrlearning-base.md) abzuschließen.

* Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](install-the-tools.md) ist
* Windows 10 SDK (10.0.18362.0 oder höher)
* Grundlagenkenntnisse in der C#-Programmierung
* Ein für die [Entwicklung konfiguriertes](using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.2.X und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform
* Vervollständigen Sie den Abschnitt [Create a Spatial Anchor Resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) des [Schnellstarts: Erstellen einer Unity hololens-APP, die Azure Spatial](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) Anchor-Tutorial verwendet.

> [!IMPORTANT]
> Die empfohlene Unity-Version für diese Tutorialreihe ist Unity 2019.2.X. Diese übertrifft alle Versionsanforderungen oder -empfehlungen, die in den oben verlinkten Voraussetzungen angegeben sind.

## <a name="creating-the-unity-project"></a>Erstellen des Unity-Projekts
<!-- TODO: Consider renaming to 'Creating and preparing the Unity scene and project'-->

In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die mrtk-Entwicklung vor.

Befolgen Sie hierzu zunächst die Anweisungen [initialisieren Ihres Projekts und der ersten Anwendung](mrlearning-base-ch1.md), ausgenommen die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihr Gerät](mrlearning-base-ch1.md#build-your-application-to-your-device) . Hierzu gehören die folgenden Schritte:

1. [Erstellen Sie ein neues Unity-Projekt](mrlearning-base-ch1.md#create-new-unity-project) , und geben Sie ihm einen passenden Namen, z. b. *mrtk-Tutorials*.

2. [Konfigurieren des Unity-Projekts für Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [Importieren von "textmesh pro Essentials"-Ressourcen](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [Importieren des Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [Konfigurieren des Unity-Projekts für das Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [Fügen Sie der Unity-Szene das Mixed Reality Toolkit hinzu](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) , und geben Sie der Szene einen passenden Namen, z. b. *azurespatialanchor* .

Befolgen Sie dann die Anweisungen zum [Konfigurieren der Mixed Reality Toolkit-profile (Ändern der Anzeige Option räumlicher Informationen)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) , um das mrtk-Konfigurations Profil für Ihre Szene in **DefaultHoloLens2ConfigurationProfile** zu ändern und die Anzeigeoptionen für das Mesh Spatial Awareness in **Occlusion**zu ändern.

> [!CAUTION]
> Wie bereits im Abschnitt [Konfigurieren des Unity-Projekts für die Anweisungen im gemischten Reality-Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) beschrieben, wird dringend empfohlen, MSBuild für Unity nicht zu aktivieren.

## <a name="adding-inbuilt-unity-packages"></a>Hinzufügen von integrierten Unity-Paketen
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

In diesem Abschnitt Installieren Sie das in Unity integrierte AR Foundation-Paket, da es für das Azure Spatial Anchor SDK erforderlich ist, das Sie im nächsten Abschnitt Importieren werden.

Wählen Sie im Unity-Menü die Option **Window** > **Package Manager**aus:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> Es kann einige Sekunden dauern, bis das AR Foundation-Paket in der Liste angezeigt wird.

Wählen Sie im Fenster Paket-Manager die Option **AR Foundation** aus, und installieren Sie das Paket durch Klicken auf die Schaltfläche **Installieren** :

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Importieren der tutorialassets

Herunterladen und **importieren** der folgenden benutzerdefinierten Unity-Pakete **in der Reihenfolge, in der Sie aufgelistet sind**:

* [Azurespatialanchor. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (Version 2.1.1)
* [Mrtk. HoloLens2. Unity. Tutorials. Assets. GettingStarted. 2.3.0.2. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
* [Mrtk. HoloLens2. Unity. Tutorials. Assets. azurespatialanchor. 2.3.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)

> [!TIP]
> Eine Erinnerung zum Importieren eines benutzerdefinierten Unity-Pakets finden Sie in den Anweisungen zum [Importieren von Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) .

Nachdem Sie die tutorialassets importiert haben, sollte Ihr Projektfenster etwa wie folgt aussehen:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>Erstellen und Vorbereiten der Szene
<!-- TODO: Consider renaming to 'Preparing the scene' -->

In diesem Abschnitt bereiten Sie die Szene vor, indem Sie einige der Prefabs hinzufügen.

Navigieren Sie im Projektfenster zu **Assets** > **mrtk. Tutorials. azurespatialanchor** > Ordner " **Prefabs** ". Wenn Sie die STRG-Taste gedrückt halten, klicken Sie auf " **Button Parent**", " **debugWindow**", " **instructions**" und "Parameter **Anchor** ", um die vier präfabs auszuwählen:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section4-step1-1.png)

Wenn die vier präfabs noch ausgewählt sind, ziehen Sie Sie in das Hierarchie Fenster, um Sie der Szene hinzuzufügen:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section4-step1-2.png)

Um sich auf die Objekte in der Szene zu konzentrieren, können Sie auf das Objekt "Objektanchor" doppelklicken und dann wieder etwas vergrößern:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> Wenn Sie die großen Symbole in Ihrer Szene finden, z. b. die großen Symbole, die Sie nicht ablenken, können Sie diese ausblenden, indem Sie <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">die Gizmos</a> an der Position ausschalten.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Konfigurieren der Schaltflächen zum Betreiben der Szene

In diesem Abschnitt fügen Sie Skripts in die Szene ein, um eine Reihe von Schaltflächen Ereignissen zu erstellen, die die Grundlagen der Verhalten beider lokaler Anker und räumlicher Azure-Anker in einer Anwendung veranschaulichen.

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a>1. Konfigurieren der druckbaren Schaltfläche "Holo Lens 2 (Skript)"

Erweitern Sie im Fenster Hierarchie das **buttonparent** -Objekt, und wählen Sie das erste untergeordnete Objekt mit dem Namen **startazuresession**aus:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step1-1.png)

Suchen Sie im Inspektor-Fenster die **Druck Bare Schaltfläche Holo Lens 2 (Script)** , und fügen Sie dem Button-Ereignis **()** einen neuen Ereignislistener hinzu, indem Sie auf das **+** -Symbol klicken:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step1-2.png)

Wenn das startazuresession-Objekt noch im Fenster Hierarchie ausgewählt ist, klicken Sie auf-und ziehen Sie das Objekt " **Objektanker** " aus dem Fenster "Hierarchie" in das leere Feld " **None" (Objekt)** des Ereignislistener, den Sie soeben hinzugefügt haben

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step1-3.png)

Klicken Sie auf die Dropdown Liste **keine Funktion** des gleichen Ereignislistener, und wählen Sie dann **anchormodulescript** > **startazuresession ()** aus, um die startazuresession ()-Funktion als Aktion festzulegen, die ausgelöst wird, wenn die Schaltfläche gedrückte Ereignisse von dieser Schaltfläche ausgelöst wird:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a>2. Konfigurieren der interactable-Komponente (Skript)

Wenn das startazuresession-Objekt noch im Fenster Hierarchie ausgewählt ist, suchen Sie im Inspektor-Fenster die Komponente **interactable (Script)** , und wiederholen Sie den Vorgang wie in Schritt 1 oben für das **OnClick ()** -Ereignis:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a>3. Konfigurieren der verbleibenden Schaltflächen

Vervollständigen Sie für jede der verbleibenden Schaltflächen den Prozess, der in Schritt 1 und 2 oben beschrieben ist, um sowohl den **gedrückten ()** als auch den **OnClick ()** -Ereignissen Funktionen zuzuweisen:

* Weisen Sie für das **stopazuresession** -Objekt die anchormodulescript-> **stopazuresession ()** -Funktion zu.
* Weisen Sie für das Objekt " **kreateazureanchor** " die Funktion "anchormodulescript" > die Funktion "-Funktion **()** " zu,
  * Ziehen Sie dann den **para Anker** erneut in das leere Feld **None (Game Object)** .
* Weisen Sie für das **removelocalanchor** -Objekt die anchormodulescript-> **removelocalanchor ()** -Funktion zu.
  * Ziehen Sie dann den **para Anker** erneut in das leere Feld **None (Game Object)** .
* Weisen Sie für das **findazureanchor** -Objekt die anchormodulescript-> **findazureanchor ()** -Funktion zu.
* Weisen Sie für das **deleteazureanchor** -Objekt das anchormodulescript-> **deleteazureanchor ()** -Funktion zu.

### <a name="4-connect-the-scene-to-the-azure-resource"></a>4. Verbinden Sie die Szene mit der Azure-Ressource.

Wählen Sie im Fenster Hierarchie das Objekt Objektanker aus, und führen Sie im Inspektor-Fenster einen **Bildlauf** nach unten bis zur Komponente **räumlicher Anker-Manager (Skript)** aus.

Fügen Sie dann im Abschnitt **Anmelde** Informationen Ihre Konto-ID und den Schlüssel für räumliche Anker, die Sie im Rahmen der [Voraussetzungen](mrlearning-asa-ch1.md#prerequisites)für dieses Tutorial erstellt haben, in die entsprechenden Konto- **ID** und die **Kontoschlüssel** Felder für räumliche Anker ein:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Grundlegendes Verhalten von räumlichen Azure-Ankern

Nachdem Ihre Szene nun so konfiguriert wurde, dass Sie die Grundlagen von räumlichen Azure-Ankern veranschaulicht, ist es an der Zeit, die APP bereitzustellen, damit Sie Azure Spatial Anchor (erste Schritte) nutzen können.

### <a name="1-add-additional-required-capabilities"></a>1. zusätzliche erforderliche Funktionen hinzufügen

Wählen Sie im Unity-Menü **Bearbeiten** > **Projekteinstellungen...** aus, um das Fenster "Player Einstellungen" zu öffnen:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section6-step1-1.png)

Wählen Sie im Fenster Player Einstellungen die Option **Player** aus, und veröffentlichen Sie dann die **Einstellungen**:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section6-step1-2.png)

Führen Sie in den **Veröffentlichungs Einstellungen**einen Bildlauf nach unten zum Abschnitt " **Funktionen** " durch, und überprüfen Sie, ob die Funktionen " **Internetclient**", " **Mikrofon**" und " **spatialperception** ", die Sie beim Erstellen des Projekts am Anfang des Tutorials aktiviert haben, aktiviert sind. Aktivieren Sie anschließend die Funktionen " **internetclientserver**", " **privatenetworkclientserver**", " **removablestorage**" und " **Webcam** ":

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2. Stellen Sie die APP auf den hololens 2 bereit.

Räumliche Azure-Anker können nicht in Unity ausgeführt werden. Daher müssen Sie das Projekt auf Ihrem Gerät bereitstellen, um die Azure Spatial Anchor-Funktionen zu testen.

> [!TIP]
> Eine Erinnerung zum Erstellen und Bereitstellen Ihres Unity-Projekts in hololens 2 finden Sie in den Anweisungen zum [Erstellen Ihrer Anwendung auf Ihr Gerät](mrlearning-base-ch1.md#build-your-application-to-your-device) .

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3. führen Sie die APP auf den hololens 2 aus, und befolgen Sie die Anweisungen in der app.

> [!CAUTION]
> Azure Spatial Anchor verwendet das Internet zum Speichern und Laden der Anker Daten, damit sichergestellt ist, dass Ihr Gerät mit dem Internet verbunden ist.

Wenn die Anwendung auf Ihrem Gerät ausgeführt wird, befolgen Sie die Anweisungen auf dem Bildschirm, die im Tutorial zum Azure Spatial Anchor-Tutorial angezeigt werden:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a>Verankern eines Erlebnisses

In den vorherigen Abschnitten haben Sie die Grundlagen von räumlichen Azure-Ankern kennengelernt. Wir haben einen Cube verwendet, um das übergeordnete Spielobjekt mit dem angefügten Anker darzustellen und zu visualisieren. In diesem Abschnitt erfahren Sie, wie Sie eine vollständige-Funktion verankern können, indem Sie Sie als untergeordnetes Element des Objektanchor-Objekts platzieren.

### <a name="1-add-the-rocket-launcher-experience"></a>1. Hinzufügen der Funktion für das Raketenstart Programm

Navigieren Sie im Projektfenster zu den **Assets** > **mrtk. Tutorials. GettingStarted** > **Prefabs** > **RocketLauncher** -Ordner, und wählen Sie die **RocketLauncher_Complete** Prefab aus:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section7-step1-1.png)

Wenn die RocketLauncher_Complete Prefab noch ausgewählt ist, ziehen Sie Sie über das Objekt " **Objektanker** " im Hierarchie Fenster, um es als untergeordnetes Element des Objekts "objeanchor" zu erstellen:

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a>2. Neupositionieren der Funktion für das Raketenstart Programm

Positionieren, drehen und Skalieren Sie das **RocketLauncher_Complete** -Objekt in eine geeignete Skala und Ausrichtung, während Sie gleichzeitig sicherstellen, dass das Objekt " **Objektanker** " weiterhin verfügbar gemacht wird, z.b.:

* Transformations **Position** X = 0, Y = 0, Z = 3,75
* Transformations **Drehung** X = 0, Y = 90, Z = 0
* Transformations **Skala** X = 10, Y = 10, Z = 10

![mrlearning-ASA](images/mrlearning-asa/tutorial1-section7-step2-1.png)

In der Anwendung kann es sein, dass Benutzer die gesamte Benutzeroberflächen-Start Programm Darstellung neu positionieren, indem Sie den Cube verschieben.

> [!TIP]
> Es gibt eine Vielzahl von Benutzeroberflächen Abläufen für die Neupositionierung, einschließlich der Verwendung eines neu positionierenden Objekts (z. b. des in diesem Tutorial verwendeten Cubes), der Verwendung einer Schaltfläche zum Umschalten eines umgebenden Felds, das die Oberfläche umgibt, der Verwendung von Position und Drehung. Gizmos und mehr.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie die Grundlagen von räumlichen Azure-Ankern kennengelernt. Das Tutorial bot Ihnen mehrere Schaltflächen, mit denen Sie die verschiedenen erforderlichen Schritte zum Starten und Beenden einer Azure-Sitzung für räumliche Anker und zum Erstellen, hochladen und Herunterladen von räumlichen Azure-Ankern auf einem einzelnen Gerät untersuchen können.

In der nächsten Lektion erfahren Sie, wie Sie Azure-Anker-IDs für den Abruf in den hololens 2 speichern, auch nachdem die Anwendung neu gestartet wurde, und wie Anker-IDs zwischen mehreren Geräten übertragen werden, um eine räumliche Ausrichtung zu erzielen.

[Nächste Lektion: 2. speichern, abrufen und Freigeben von räumlichen Azure-Ankern](mrlearning-asa-ch2.md)
