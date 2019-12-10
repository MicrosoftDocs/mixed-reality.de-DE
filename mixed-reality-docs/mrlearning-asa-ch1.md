---
title: Tutorials zu Azure Spatial Anchor-1. Ersten Einstieg in Azure Spatial Anchor
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 861c42f9449fcb3cf038258af91088fc927941e5
ms.sourcegitcommit: f4812e1312c4751a22a2de56771c475b22a4ba24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2019
ms.locfileid: "74940978"
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

## <a name="prerequisites"></a>Voraussetzungen

* Erfüllen Sie die Anforderungen, die im Abschnitt " [Voraussetzungen](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#prerequisites) " des Tutorials [Schnellstart: Erstellen einer Unity hololens-APP, die Azure Spatial Anchor verwendet,](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) aufgeführt sind.
* Vervollständigen Sie den Abschnitt [Create a Spatial Anchor Resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) des [Schnellstarts: Erstellen einer Unity hololens-APP, die Azure Spatial](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) Anchor-Tutorial verwendet.
* Wenn Sie die Reihe "erste Schritte" noch nicht abgeschlossen haben, empfiehlt es sich, [diese Tutorials zuerst](mrlearning-base.md) abzuschließen.

## <a name="creating-the-unity-project"></a>Erstellen des Unity-Projekts

In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und konfigurieren es für Windows Mixed Reality.

1. Erstellen Sie ein Unity-Projekt, und geben Sie ihm einen passenden Namen, z. b. ein _Tutorial für räumliche Azure-Anker_.

2. Konfigurieren Sie das Unity-Projekt für Windows Mixed Reality.

    >[!TIP]
    >Eine Erinnerung zum Erstellen eines Unity-Projekts und zum Konfigurieren des Projekts für Windows Mixed Reality finden Sie in den Abschnitten [Erstellen eines neuen Unity](mrlearning-base-ch1.md#create-new-unity-project) -Projekts und [Konfigurieren des Unity-Projekts für Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) des Tutorials [initialisieren Ihres Projekts und der ersten Anwendung](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) , das Teil [der Reihe "](mrlearning-base.md) erste Schritte" ist.

## <a name="adding-inbuilt-unity-packages"></a>Hinzufügen von integrierten Unity-Paketen

In diesem Abschnitt fügen Sie von den Toolkits und SDKs, die Sie im Projekt verwenden werden, integrierte Unity-Ressourcen und Pakete hinzu, die benötigt werden.

1. Importieren Sie wichtige tmp-Ressourcen.

    >[!NOTE]
    >Wir fügen dieses Paket hinzu, da es für das Mixed Reality Toolkit erforderlich ist.

    Wählen Sie im Unity-Menü **Fenster** > **textmeshpro** > **importieren Sie wichtige Ressourcen für tmp**.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-2-1.1.png)

    Vergewissern Sie sich, dass im Popup Fenster des Unity-Pakets importieren zunächst alle Ressourcen ausgewählt werden, indem Sie auf die Schaltfläche **alle** klicken, und importieren Sie dann die Assets, indem Sie auf die Schaltfläche **importieren** klicken.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-2-1.2.png)

2. Installieren Sie ar Foundation.

    >[!NOTE]
    >Wir fügen dieses Paket hinzu, da es für das Azure Spatial Anchor SDK erforderlich ist.

    Wählen Sie im Unity-Menü die Option **Window** > **Package Manager**aus.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-2-2.1.png)

    Wählen Sie im Fenster Paket-Manager die Option **AR Foundation** aus, und installieren Sie das Paket durch Klicken auf die Schaltfläche **Installieren** .

    >[!IMPORTANT]
    >Es kann einige Sekunden dauern, bis das AR Foundation-Paket in der Liste angezeigt wird.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-2-2.2.png)

## <a name="importing-the-tutorial-assets"></a>Importieren der tutorialassets

In diesem Abschnitt laden Sie alle tutorialassets herunter und importieren Sie.

1. Laden Sie die Assets herunter.

    * [Azurespatialanchor. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (Version 2.0.0)
    * [Microsoft. mixedreality. Toolkit. Unity. Foundation. 2.1.0. unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)
    * [Mrtk. HoloLens2. Unity. Tutorials. Assets. GettingStarted. 2.1.0.1. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)
    * [Mrtk. HoloLens2. Unity. Tutorials. Assets. azurespatialanchor. 2.1.0.1. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

2. Importieren Sie die Objekte.

    Wählen Sie im Unity-Menü die Option **Assets** > **Paket** > **benutzerdefiniertes Paket importieren...** aus.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-3-2.1.png)

    Im Paket importieren... Popup Fenster, wählen Sie **azurespatialanchor. unitypackage** aus, und klicken Sie auf die Schaltfläche **Öffnen** .

    ![mrlearning-ASA](images/mrlearning-asa-ch1-3-2.2.png)

    Vergewissern Sie sich, dass im Popup Fenster des Unity-Pakets importieren zunächst alle Ressourcen ausgewählt werden, indem Sie auf die Schaltfläche **alle** klicken, und importieren Sie dann die Assets, indem Sie auf die Schaltfläche **importieren** klicken.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-3-2.3.png)

    Wiederholen Sie diese Schritte, um die restlichen Asset-Pakete zu importieren. Nach Abschluss des Vorgangs sollte der Ordner " **Assets** " Ihres Unity-Projekts diese Unterordner enthalten.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-3-2.4.png)

## <a name="creating-and-preparing-the-scene"></a>Erstellen und Vorbereiten der Szene

In diesem Abschnitt erstellen und bereiten Sie die Szene vor, indem Sie das Mixed Reality Toolkit und einige der Prefabs für das Tutorial hinzufügen.

1. Erstellen Sie eine neue Szene.

    Klicken Sie im Unity-Menü auf **Datei** > **neue Szene**.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-1.1.png)

    Wählen Sie im Unity-Menü **Datei** > **Speichern unter...** aus.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-1.2.png)

    Navigieren Sie im Popup Fenster Szene speichern zum Ordner **Szenen** Ihres Projekts, geben Sie Ihrer Szene einen passenden Namen, z. b. _asatutorialscene_, und speichern Sie die Szene, indem Sie auf die Schaltfläche **Speichern** klicken.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-1.3.png)

    >[!TIP]
    >Sie können die Szene beliebig speichern, solange Sie sich im Ordner "Assets" des Projekts befindet. Um Ihr Projekt jedoch weiterhin zu organisieren, empfiehlt es sich im Allgemeinen, es im Ordner "Szenen" des Projekts zu speichern.

2. Fügen Sie das Mixed Reality Toolkit hinzu.

    Wählen Sie im Unity-Menü **Mixed Reality Toolkit** aus, > **zu Szene hinzufügen und konfigurieren...** .

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-2.1.png)

    Klicken Sie im Popup Fenster mixedrealitytoolkitconfigurationprofile auswählen auf **DefaultHoloLens2ConfigurationProfile** , um es als mrtk-Konfigurations Profil für die Szene festzulegen.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-2.2.png)

    Wählen Sie im Unity-Menü **Datei** > **Speichern** aus, um die Szene zu speichern.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-2.3.png)

    >[!TIP]
    >Mit der Tastenkombination STRG + s (Command + s unter macOS) können Sie Ihre Szene schnell speichern, während Sie dieses Tutorial durcharbeiten.

3. Fügen Sie das Tutorial "Prefabs" hinzu.

    Navigieren Sie im Projekt Panel zu **Assets** > **mrtk. Tutorials. azurespatialanchor** > Ordner " **Prefabs** ". Wenn Sie die STRG-Taste gedrückt halten (command on macOS), klicken Sie auf " **buttonparent**", " **debugWindow**" und " **Parser** ", um die drei präfabs auszuwählen.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-3.1.png)

    Wenn die drei präfabs noch ausgewählt sind, ziehen Sie Sie in den Hierarchie Bereich, um Sie der Szene hinzuzufügen.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-3.2.png)

    Um sich auf die Objekte in der Szene zu konzentrieren, können Sie auf das Objekt "Objektanchor" doppelklicken und dann wieder etwas vergrößern.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-4-3.3.png)

    >[!TIP]
    >Wenn Sie die großen Symbole in Ihrer Szene finden, z. b. die großen Symbole, die Sie nicht ablenken, können Sie diese ausblenden, indem Sie <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">die Gizmos</a> an der Position ausschalten.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Konfigurieren der Schaltflächen zum Betreiben der Szene

In diesem Abschnitt fügen Sie Prefabs und Skripts in die Szene ein, um eine Reihe von Schaltflächen zu erstellen, die die Grundlagen der Art und Weise, wie sowohl lokale Anker als auch räumliche Azure-Anker sich in einer Anwendung Verhalten.

1. Konfigurieren Sie die Druck Bare Schaltfläche Holo Lens 2 (Skript).

    Erweitern Sie im Hierarchie Panel das **buttonparent** -Objekt, und wählen Sie das erste untergeordnete Objekt mit dem Namen **startazuresession**aus.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-1.1.png)

    Scrollen Sie im Inspektor-Panel nach unten zur **druckbaren Schaltfläche Holo Lens 2 (Script)** , und fügen Sie einen neuen Ereignislistener zum **gedrückten Ereignis ()** hinzu, indem Sie auf das **+** -Symbol klicken.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-1.2.png)

    Wenn das startazuresession-Objekt im Hierarchie Panel noch ausgewählt ist, klicken Sie auf-und ziehen Sie das Objekt " **Objektanker** " aus dem Hierarchie Panel in das leere Feld " **None" (Objekt)** des Ereignislistener, den Sie soeben hinzugefügt haben, um das Objekt "Objektanchor" über diese Schaltfläche zu lauschen.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-1.3.png)

    Klicken Sie auf die Dropdown Liste **keine Funktion** des gleichen Ereignislistener, und wählen Sie dann **anchormodulescript** > **startazuresession ()** aus, um die startazuresession ()-Funktion als Aktion festzulegen, die ausgelöst wird, wenn die Schaltfläche gedrückte Ereignisse von dieser Schaltfläche ausgelöst werden.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-1.4.png)

2. Konfigurieren Sie die interactable-Komponente (Skript).

    Wenn das startazuresession-Objekt im Bereich Hierarchie weiterhin ausgewählt ist, Scrollen Sie im Inspektor-Panel nach unten zur Komponente **interactable (Script)** , und wiederholen Sie den gleichen Prozess wie in Schritt 1 oben für das **OnClick ()** -Ereignis.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-2.1.png)

3. Konfigurieren der verbleibenden Schaltflächen

    Schließen Sie für jede der verbleibenden Schaltflächen den in Schritt 1 und 2 beschriebenen Prozess ab, um sowohl den Schaltflächen gedrückten () als auch dem OnClick ()-Ereignis Funktionen zuzuweisen:

    * Weisen Sie für das **stopazuresession** -Objekt die **stopazuresession ()** -Funktion zu.
    * Weisen Sie für **das Objekt "das Objekt** " "die Funktion" "die Funktion" Funktion " **()** zu, und ziehen Sie dann die **Komponente" ankeranchor** "erneut in das leere Feld" **None "(Spielobjekt)** .
    * Weisen Sie für das **nach Anker Objekt gesuchte** die **findazureanchor ()** -Funktion zu.
    * Weisen Sie für das **Azure Anchor** -Objekt löschen die **deleteazureanchor ()** -Funktion zu.
    * Weisen Sie für das Objekt **lokalen Anker löschen** die **removelocalanchor ()** -Funktion zu, und ziehen Sie dann den Objektanchor erneut in das leere Feld **None (Game Object)** .

4. Verbinden der Szene mit der Azure-Ressource

    Wählen Sie im Bereich Hierarchie das Objekt **Objektanker** aus, und Scrollen Sie im Inspektor-Panel nach unten zur Komponente **räumlicher Anker-Manager (Skript)** .

    Fügen Sie dann im Abschnitt **Anmelde** Informationen Ihre Konto-ID und den Schlüssel für räumliche Anker in die entsprechenden Kontoschlüssel Felder **Konto-ID** und **räumlichkeits** Felder des räumlichen Ankern ein.

    >[!NOTE]
    >Sie haben Ihre Konto-ID und den Schlüssel für räumliche Anker im Rahmen der [Voraussetzungen](mrlearning-asa-ch1.md#prerequisites)dieses Tutorials erstellt.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-5-4.1.png)

    >[!CAUTION]
    >Stellen Sie sicher, dass Sie Ihre Szene speichern.

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Grundlegendes Verhalten von räumlichen Azure-Ankern

Nachdem Ihre Szene nun so konfiguriert wurde, dass Sie die Grundlagen von räumlichen Azure-Ankern veranschaulicht, ist es an der Zeit, die APP bereitzustellen, damit Sie Azure Spatial Anchor (erste Schritte) nutzen können.

1. Fügen Sie zusätzliche erforderliche Funktionen hinzu.

    Wählen Sie im Unity-Menü **Bearbeiten** > **Projekteinstellungen...** aus, um das Fenster mit den Player Einstellungen zu öffnen.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-6-1.1.png)

    Wählen Sie im Bereich Player Einstellungen die Option **Player** und dann **Veröffentlichungs Einstellungen**aus.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-6-1.2.png)

    Führen Sie in den **Veröffentlichungs Einstellungen**einen Bildlauf nach unten zum Abschnitt **Funktionen** durch, und überprüfen Sie, ob **spatialperception**, das Sie beim Erstellen des Projekts am Anfang des Tutorials aktiviert haben, aktiviert ist. Anschließend wurden die Funktionen **Internetclient**, **internetclientserver**, **privatenetworkclientserver**, **removablestorage**, **Webcam**und **Mikrofon** aktiviert.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-6-1.3.png)

2. Stellen Sie die APP auf den hololens 2 bereit.

    >[!TIP]
    >Eine Erinnerung zum Erstellen und Bereitstellen Ihres Unity-Projekts in hololens 2 finden Sie in den Abschnitten Erstellen der [Anwendung auf Ihren Geräten](mrlearning-base-ch1.md#build-your-application-to-your-device) des Tutorials [initialisieren Ihres Projekts und der ersten Anwendung](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) , die Teil der Reihe erste Schritte mit [Tutorials](mrlearning-base.md) ist.

3. Führen Sie die APP aus, und befolgen Sie die Anweisungen in der app.

    >[!CAUTION]
    >Azure Spatial Anchor verwendet das Internet zum Speichern und Laden der Anker Daten, damit sichergestellt ist, dass Ihr Gerät mit dem Internet verbunden ist.

    Wenn die Anwendung auf Ihrem Gerät ausgeführt wird, befolgen Sie die Anweisungen auf dem Bildschirm, die im **Azure Spatial Anchor Module instructions** -Panel angezeigt werden.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-6-3.1.png)

## <a name="anchoring-an-experience"></a>Verankern eines Erlebnisses

In den vorherigen Abschnitten haben Sie die Grundlagen von räumlichen Azure-Ankern kennengelernt. Wir haben einen Cube verwendet, um das übergeordnete Spielobjekt mit dem angefügten Anker darzustellen und zu visualisieren. In diesem Abschnitt erfahren Sie, wie Sie eine vollständige-Funktion verankern können, indem Sie Sie als untergeordnetes Element des Objektanchor-Objekts platzieren.

1. Fügen Sie das Launcher-Start Programm hinzu.

    Navigieren Sie im Projekt Panel zu **Assets** > **mrtk. Tutorials. GettingStarted** > Ordner " **Prefabs** ", und wählen Sie die **Launcher_Complete** vorfab aus.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-7-1.1.png)

    Ziehen Sie bei aktivierter aufruppe Launcher_Complete die Option "Prefab" auf das Objekt " **Objektanchor** " im Hierarchie Panel, um es zu einem untergeordneten Element des Objekts "Objekt Anker" zu machen.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-7-1.2.png)

2. Positionieren Sie das Launcher-Start Programm neu.

    Verschieben Sie das Modul mit dem **Launcher_Complete** Objekt, damit das **Objekt (der** Cube) noch verfügbar gemacht wird.

    ![mrlearning-ASA](images/mrlearning-asa-ch1-7-2.1.png)

    In der Anwendung kann es sein, dass Benutzer die gesamte Benutzeroberflächen-Start Programm Darstellung neu positionieren, indem Sie den Cube verschieben.

    >[!TIP]
    >Es gibt eine Vielzahl von Benutzeroberflächen Abläufen für die Neupositionierung, einschließlich der Verwendung eines neu positionierenden Objekts (z. b. des in diesem Tutorial verwendeten Cubes), der Verwendung einer Schaltfläche zum Umschalten eines umgebenden Felds, das die Oberfläche umgibt, der Verwendung von Position und Drehung. Gizmos und mehr.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie die Grundlagen von räumlichen Azure-Ankern kennengelernt. In dieser Lektion haben Sie mehrere Schaltflächen zur Verfügung gestellt, mit denen Sie die verschiedenen Schritte zum Starten und Beenden einer Azure-Sitzung sowie zum Erstellen, hochladen und Herunterladen von Azure-Ankern auf einem einzelnen Gerät untersuchen können

In der nächsten Lektion erfahren Sie, wie Sie Azure-Anker-IDs für den Abruf in den hololens 2 speichern, auch nachdem die Anwendung neu gestartet wurde, und wie Anker-IDs zwischen mehreren Geräten übertragen werden, um eine räumliche Ausrichtung zu erzielen.

[Nächste Lektion: 2. speichern, abrufen und Freigeben von räumlichen Azure-Ankern](mrlearning-asa-ch2.md)
