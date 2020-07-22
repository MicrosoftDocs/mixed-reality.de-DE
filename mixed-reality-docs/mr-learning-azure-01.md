---
title: Azure-Cloudtutorials – 1. Azure Cloud Services für HoloLens 2
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie verschiedene Azure-Dienste innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Azure, Mixed Reality, Unity, Tutorial, HoloLens, HoloLens 2, Azure Blob Storage, Azure Table Storage, Azure Spatial Anchor, Azure Bot Framework
ms.localizationpriority: high
ms.openlocfilehash: 649046f9416c880d6e69b544866fba60d3e43f4c
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304979"
---
# <a name="1-azure-cloud-services-for-hololens-2"></a>1. Azure Cloud Services für HoloLens 2

## <a name="overview"></a>Übersicht

Willkommen zu dieser Reihe von Tutorials, die sich darauf konzentrieren, **Azure Cloud Services** in eine **HoloLens 2** Anwendung einzubinden. In dieser fünfteiligen Tutorialserie erfahren Sie, wie Sie mehrere **Azure Cloud Services** in ein **Unity**-Projekt für **HoloLens 2** integrieren können. Mit jedem weiteren Kapitel fügen Sie neue **Azure Cloud Services** hinzu, um die Anwendungsfunktionen und die Benutzererfahrung zu erweitern, während Sie die Grundlagen jedes **Azure Cloud Service** kennenlernen.

> [!NOTE]
> Diese Tutorialserie konzentriert sich auf **HoloLens 2**, aber aufgrund des plattformübergreifenden Charakters von Unity gelten die meisten Lerninhalte auch für Desktop- und Smartphoneanwendungen.

In diesem ersten Tutorial, [Einführung in Azure Cloud Services für HoloLens 2](mr-learning-azure-01.md), erläutern Sie zunächst die Ziele der Anwendung, machen sich kurz mit den einzelnen Azure Cloud Services vertraut und richten das Unity-Projekt ein.

Im zweiten Tutorial, [Integrieren von Azure Storage](mr-learning-azure-02.md), beginnen Sie mit der Integration von Azure Storage als Persistenzlösung für die Demoanwendung, lernen die Unterschiede zwischen Blob Storage und Table Storage kennen, bereiten die benötigten Projektressourcen vor, richten die Szene ein und überprüfen die Vorgänge zum Lesen, Aktualisieren und Löschen von Daten.

Im dritten Tutorial, [Integrieren von Azure Custom Vision](mr-learning-azure-03.md), verwenden Sie Azure Custom Vision zum Trainieren und Erkennen von Bildern in der HoloLens 2-Anwendung. Das Kapitel beginnt mit dem Einrichten Ihrer eigenen Azure Custom Vision-Ressource, dem Vorbereiten der Szenekomponenten und der Umsetzung durch Trainieren und Erkennen Ihrer eigenen Bilder aus der Anwendung heraus.

Im vierten Tutorial, [Integrieren von Azure Spatial Anchors](mr-learning-azure-04.md), fahren Sie fort, indem Sie den Azure Spatial Anchors-Dienst erkunden, um Positionen zu speichern und zu finden. Sie lernen die grundlegenden Konzepte kennen, bereiten die erforderlichen Ressourcen vor, richten die Szene ein und verwenden das neue Feature in der Anwendung.

Im fünften Tutorial, [Integrieren von Azure Bot Service mit LUIS](mr-learning-azure-05.md), finalisieren Sie die vorherigen Schritte, indem Sie der Anwendung eine neue Methode für die Benutzerinteraktion zur Verfügung stellen: natürliche Sprache! Diese Funktion wird durch die Verwendung von Azure Bot Framework und Language Understanding (LUIS) umgesetzt. In diesem letzten Kapitel werden die Grundlagen von Azure Bot Service erläutert, und Sie erfahren, wie Sie den Prozess beschleunigen können, indem Sie Bot Framework Composer als codefreie Lösung verwenden. Nachdem der Bot erstellt wurde, integrieren Sie ihn in die Szene und führen ihn mit der letzten Phase der HoloLens 2-Anwendung aus.

## <a name="application-goals"></a>Anwendungsziele

In dieser Tutorialserie erstellen Sie eine **HoloLens 2** Anwendung, mit der Objekte aus Bildern erkannt und die räumliche Position gefunden werden kann. Um einen Fachbegriff festzulegen, nennen wir diese Entitäten von nun an **nachverfolgtes Objekt**.
Der Benutzer kann ein **nachverfolgtes Objekt** erstellen, indem er entweder eine Reihe von Bildern über maschinelles Sehen und/oder eine räumliche Position zuordnet. Alle Daten müssen in der Cloud persistent gespeichert werden. Darüber hinaus werden einige Aspekte der Anwendung optional durch natürliche Spracheingaben gesteuert, die über einen Bot unterstützt werden.

### <a name="features"></a>Features

* Grundlegende Verwaltung von Daten und Bildern
* Bildtraining und -erkennung
* Speichern einer räumlichen Position sowie zugehörige Anleitungen
* Bot-Assistent, um einige Features über natürliche Sprache zu nutzen

## <a name="azure-cloud-services"></a>Azure Cloud Services

Um die erforderlichen Features für die Anwendung bereitzustellen, verwenden Sie die folgenden **Azure Cloud** Services:

### <a name="azure-storage"></a>Azure Storage

Sie verwenden [Azure Storage](https://azure.microsoft.com/services/storage/) für die Persistenzlösung. Der Dienst ermöglicht es Ihnen, Daten in einer Tabelle zu speichern und große Binärdateien wie Bilder hochzuladen.

### <a name="azure-custom-vision"></a>Azure Custom Vision

Mit [Azure Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (Teil von [Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/)) können Sie *nachverfolgten Objekten* eine Gruppe von Bildern zuordnen, ein Machine Learning-Modell für diese Gruppe trainieren und das *nachverfolgte Objekt* erkennen.

### <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

Um die Position eines *nachverfolgten Objekts* zu speichern und eine Anleitung zur Suche zu erhalten, verwenden Sie [Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/).

### <a name="azure-bot-service"></a>Azure Bot Service

Die Anwendung wird hauptsächlich durch herkömmliche Benutzeroberfläche gesteuert, sodass Sie [Azure Bot Service](https://azure.microsoft.com/services/bot-service/) verwenden, um etwas mehr Persönlichkeit hinzuzufügen und eine neue Interaktionsmethode einzuführen.

## <a name="prerequisites"></a>Voraussetzungen

>[!TIP]
>Wenn Sie die Reihe [Tutorials zu den ersten Schritten](mr-learning-base-01.md) noch nicht abgeschlossen haben, empfiehlt es sich, zunächst diese Tutorials abzuschließen.

* Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](install-the-tools.md) ist
* Windows 10 SDK (10.0.18362.0 oder höher)
* Grundlagenkenntnisse in der C#-Programmierung
* Ein für die [Entwicklung konfiguriertes](using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät
* Eine verbundene Webcam, wenn Sie über den Unity-Editor testen möchten
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.3.X und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform

> [!CAUTION]
> Die empfohlene Unity-Version für diese Tutorialreihe ist Unity 2019.3.X. Diese übertrifft alle Versionsanforderungen oder -empfehlungen, die in den oben verlinkten Voraussetzungen angegeben sind.

## <a name="creating-and-preparing-the-unity-project"></a>Erstellen und Vorbereiten des Unity-Projekts

In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die MRTK-Entwicklung vor.

Befolgen Sie zu diesem Zweck zunächst die Anweisungen unter [Initialisieren des Projekts und der ersten Anwendung](mr-learning-base-02.md), jedoch ohne die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihrem Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2), die die folgenden Schritte beinhalten:

1. [Erstellen des Unity-Projekts](mr-learning-base-02.md#creating-the-unity-project), das mit einem passenden Namen bezeichnet wird, beispielsweise *Azure-Cloudtutorials*
2. [Wechseln der Buildplattform](mr-learning-base-02.md#configuring-the-unity-project)
3. [Importieren der TextMeshPro Essential-Ressourcen](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [Importieren des Mixed Reality-Toolkits](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [Konfigurieren des Unity-Projekts](mr-learning-base-02.md#configuring-the-unity-project)
6. [Erstellen und Konfigurieren der Szene](mr-learning-base-02.md#creating-and-configuring-the-scene) und Bezeichnen der Szene mit einem passenden Namen, z. B. *AzureCloudServices*

Befolgen Sie dann die Anweisungen unter [Ändern der Anzeigeoption der räumlichen Wahrnehmung](mr-learning-base-03.md#changing-the-spatial-awareness-display-option), um das **DefaultHoloLens2ConfigurationProfile** als MRTK-Konfigurationsprofil für Ihre Szene festzulegen, und ändern Sie die Anzeigeoptionen für das Gittermodell zur räumlichen Wahrnehmung in **Occlusion** (Verdeckung).

## <a name="installing-inbuilt-unity-packages"></a>Installieren von integrierten Unity-Paketen

Wählen Sie im Unity-Menü **Fenster** > **Package Manager** (Paket-Manager) aus, um das Fenster „Package Manager“ zu öffnen, wählen Sie **AR Foundation** aus, und klicken Sie auf die Schaltfläche **Install** (Installieren), um das Paket zu installieren:

![mr-learning-azure](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> Sie installieren das AR Foundation-Paket, da es für das Azure Spatial Anchor SDK erforderlich ist, das Sie im nächsten Abschnitt importieren.

## <a name="importing-the-tutorial-assets"></a>Importieren der Tutorialressourcen

Laden Sie die folgenden benutzerdefinierten Unity-Pakete herunter, und **importieren** Sie sie **in der Reihenfolge, in der sie aufgelistet sind**:

* [Azure Storage für Unity](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureStorageForUnity.unitypackage)
* [Azure Spatial Anchors](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage)
* [MRTK.Tutorials.AzureCloudServices](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/MRTK.Tutorials.AzureCloudServices.unitypackage)

> [!TIP]
> Wenn Sie eine Auffrischung zum Importieren eines benutzerdefinierten Unity-Pakets benötigen, lesen Sie die Anweisungen unter [Importieren des Mixed Reality-Toolkits](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).

Nach dem Importieren der Tutorialressourcen sollte Ihr Projektfenster ähnlich wie die folgende Abbildung aussehen:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section4-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>Erstellen und Vorbereiten der Szene
<!-- TODO: Consider renaming to 'Preparing the scene' -->

In diesem Abschnitt bereiten Sie die Szene vor, indem Sie einige der Tutorial-Prefabs hinzufügen.

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**. Klicken Sie mit gedrückter STRG-Taste auf **SceneController**, **RootMenu** und **DataManager**, um die drei Prefabs auszuwählen:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-1.png)

**SceneController (Prefab)** enthält zwei Skripts: **SceneController (Script)** und **UnityDispatcher (Script)** . Die **SceneController**-Skriptkomponente enthält mehrere UX-Funktionen und ermöglicht die Fotoerfassungsfunktionalität, während **UnityDispatcher** eine Hilfsklasse ist, um Execute-Aktionen für den Unity-Hauptthread zuzulassen.

**RootMenu (Prefab)** ist das primäre UI-Prefab, das alle Benutzeroberflächenfenster enthält, die über verschiedene kleine Skriptkomponenten miteinander verbunden sind und den allgemeinen UX-Fluss der Anwendung steuern.

**DataManager (Prefab)** ist für die Kommunikation mit Azure Storage zuständig und wird im nächsten Tutorial ausführlicher erläutert.

Ziehen Sie die drei noch ausgewählten Prefabs nun auf das Hierarchiefenster, um sie der Szene hinzuzufügen:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-2.png)

Um sich auf die Objekte in der Szene zu konzentrieren, können Sie auf das **RootMenu**-Objekt doppelklicken und die Ansicht dann etwas verkleinern:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-3.png)

> [!TIP]
> Wenn Sie die großen Symbole in Ihrer Szene, beispielsweise die mit großen Rahmen umgebenen 'T'-Symbole, irritierend finden, können Sie diese ausblenden, indem Sie <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">die Gizmos umschalten</a> (in die Aus-Position).

## <a name="configuring-the-scene"></a>Konfigurieren der Szene

In diesem Abschnitt verbinden Sie *SceneManager*, *DataManager* und *RootMenu*, um eine funktionierende Szene zu erhalten, die für das folgende Tutorial [Integrieren von Azure Storage](mr-learning-azure-01.md) bereit ist.

### <a name="connect-the-objects"></a>Verbinden der Objekte

Wählen Sie im Hierarchiefenster das **DataManager**-Objekt aus:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-1.png)

Suchen Sie im Inspektor-Fenster die Komponente **DataManager (Script)** . Sie sehen einen leeren Slot für das Ereignis **On Data Manager Ready ()** . Ziehen Sie nun das **SceneController**-Objekt aus dem Hierarchiefenster in das **On Data Manager Ready ()** -Ereignis.

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-2.png)

Sie werden feststellen, dass das Dropdownmenü des Ereignisses aktiviert wurde. Klicken Sie auf das Dropdownmenü, navigieren Sie zu **SceneController**, und wählen Sie im Untermenü die Option **Init ()** aus:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-3.png)

Wählen Sie im Hierarchyfenster das **SceneController**-Objekt aus. Im Inspektor finden Sie dort die Komponente **SceneController (Script)** .

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-4.png)

Sie werden feststellen, dass es mehrere nicht mit Daten aufgefüllte Felder gibt. Ändern Sie dies nun. Verschieben Sie das **DataManager**-Objekt aus der Hierarchie in das Feld *Data Manager*, und verschieben Sie das **RootMenu**-GameObject aus der Hierarchie in das Feld *Main Menu* (Hauptmenü).

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-5.png)

Ihre Szene ist nun für die bevorstehenden Tutorials bereit. Vergessen Sie nicht, sie in Ihrem Projekt zu speichern.

## <a name="prepare-project-build-pipeline"></a>Vorbereiten der Projektbuildpipeline

Obwohl das Projekt noch mit Inhalt gefüllt werden muss, müssen Sie einige Vorbereitungen treffen, damit das Projekt für den Buildvorgang für **HoloLens 2** bereit ist.

### <a name="1-add-additional-required-capabilities"></a>1. Hinzufügen zusätzlicher erforderlicher Funktionen

Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen...) aus, um das Fenster „Project Settings“ (Projekteinstellungen) zu öffnen:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-1.png)

Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) die Option **Player** und dann **Publishing Settings** (Veröffentlichungseinstellungen) aus:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-2.png)

Scrollen Sie in den **Publishing Settings** nach unten zum Abschnitt **Capabilities** (Funktionen), und vergewissern Sie sich, dass die Funktionen **InternetClient**, **Microphone** und **SpatialPerception**, die Sie im Rahmen der Erstellung des Projekts zu Beginn des Tutorials erstellt haben, aktiviert sind. Aktivieren Sie dann die Funktionen **InternetClientServer**, **PrivateNetworkClientServer** und **Webcam**:

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2. Bereitstellen der App auf Ihrer HoloLens 2

Nicht alle Funktionen, die Sie in dieser Tutorialreihe verwenden werden, können innerhalb des Unity-Editors ausgeführt werden. Dies bedeutet, dass Sie mit der Bereitstellung der Anwendung auf Ihrem HoloLens 2-Gerät vertraut sein müssen.

> [!TIP]
> Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie in den Tutorials mit den ersten Schritten die Anweisungen unter [Erstellen Ihrer Anwendung auf Ihrem Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3. Führen Sie die App auf Ihrer HoloLens 2 aus, und folgen Sie den Anweisungen in der App

> [!CAUTION]
> Alle Azure-Dienste verwenden das Internet. Stellen Sie daher sicher, dass Ihr Gerät mit dem Internet verbunden ist.

Wenn die Anwendung auf Ihrem Gerät ausgeführt wird, stimmen Sie dem Zugriff auf die folgenden angeforderten Funktionen zu:

* Mikrofon
* Kamera

Diese Funktionen sind für Dienste wie *Chat Bot* und *Custom Vision* erforderlich, damit diese ordnungsgemäß funktionieren.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial wurde Ihnen die Tutorialreihe vorgestellt, Sie haben erfahren, welche Funktionen Sie implementieren und wie **Azure Cloud** Services an die Realisierung Ihrer *HoloLens  2*-Anwendung anknüpfen. Sie haben dem Projekt die erforderlichen Komponenten hinzugefügt und die Szene für diese Tutorialreihe vorbereitet.

In der nächsten Lektion verwenden Sie Azure Storage als cloudbasierte Persistenzlösung zum Speichern von Daten und Bildern.

[Nächstes Tutorial: 2. Integrieren von Azure Storage](mr-learning-azure-02.md)
