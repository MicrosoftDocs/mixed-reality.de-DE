---
title: 'Tutorials zu Azure Spatial Anchors: 1 Erste Schritte mit Azure Spatial Anchors'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 385b302f3a2b9ad80527387353746947d91e3aa3
ms.sourcegitcommit: 4282d92e93869e4829338bdf7d981c3ee0260bfd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85216301"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Erste Schritte mit Azure Spatial Anchors

## <a name="overview"></a>Übersicht

Willkommen bei der zweiten Reihe der HoloLens 2-Tutorials. In dieser vierteiligen Tutorialreihe lernen Sie die Grundlagen von Azure Spatial Anchors kennen.

In diesem ersten Tutorial, [Erste Schritte mit Azure Spatial Anchors](mrlearning-asa-ch1.md), erkunden Sie die verschiedenen Schritte, die zum Starten und Beenden einer Azure-Sitzung und zum Erstellen, Hochladen und Herunterladen von Azure Anchors auf einem einzelnen Gerät erforderlich sind.

Im zweiten Tutorial, [Speichern, Abrufen und Freigeben von Azure Spatial Anchors](mrlearning-asa-ch2.md), erfahren Sie, wie Sie räumliche Azure-Spatial Anchors über mehrere App-Sitzungen hinweg speichern, indem Sie Ankerinformationen im Speicher von HoloLens 2 speichern, und wie Sie diese Ankerinformationen mit anderen Geräten teilen, um eine Ankerausrichtung auf mehreren Geräten zu erreichen.

Im dritten Tutorial, [Anzeigen von Azure Spatial Anchors-Feedback](mrlearning-asa-ch3.md), lernen Sie, wie Sie beim Verwenden von Azure Spatial Anchors Feedback zu Ankerereignissen und -zuständen für Benutzer bereitstellen.

Im vierten Tutorial [Azure Spatial Anchors für Android und iOS](mrlearning-asa-ch4.md) erfahren Sie, wie Sie Ihr Projekt für Android- und iOS-Geräte erstellen und bereitstellen.

## <a name="objectives"></a>Ziele

* Erlernen der Grundlagen des Entwickelns mit Azure Spatial Anchors für HoloLens 2
* Erstellen, Hochladen und Herunterladen von Raumankern

## <a name="prerequisites"></a>Voraussetzungen

>[!TIP]
>Wenn Sie die Reihe [Tutorials zu den ersten Schritten](mrlearning-base.md) noch nicht abgeschlossen haben, empfiehlt es sich, zunächst diese Tutorials abzuschließen.

* Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](install-the-tools.md) ist
* Windows 10 SDK (10.0.18362.0 oder höher)
* Grundlagenkenntnisse in der C#-Programmierung
* Ein für die [Entwicklung konfiguriertes](using-visual-studio.md#enabling-developer-mode) HoloLens- (1. Generation) oder HoloLens 2-Gerät
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.2.X und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform
* Schließen Sie den Abschnitt [Erstellen einer Spatial Anchors-Ressource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) des [HoloLens-Schnellstart](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)-Tutorials ab.

Wenn Sie auf Android bereitstellen möchten
* Ein Android-Gerät mit <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">Entwicklerunterstützung</a> und <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore-Unterstützung</a> mit USB-Verbindung zu Ihrem Windows- oder macOS-Computer
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.2.X und hinzugefügtem Buildunterstützungsmodul für Android

Wenn Sie auf iOS bereitstellen möchten
* Ein macOS-Computer mit installierter neuester Version von <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> und <a href="https://cocoapods.org" target="_blank">CocoaPods</a>
* Ein iOS-Gerät mit <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit-Unterstützung</a> und USB-Verbindung mit Ihrem macOS-Computer
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.2.X und hinzugefügtem Buildunterstützungsmodul für iOS

> [!IMPORTANT]
> Die empfohlene Unity-Version für diese Tutorialreihe ist Unity 2019.2.X. Diese übertrifft alle Versionsanforderungen oder -empfehlungen, die in den oben verlinkten Voraussetzungen angegeben sind.

## <a name="creating-the-unity-project"></a>Erstellen des Unity-Projekts
<!-- TODO: Consider renaming to 'Creating and preparing the Unity project'-->

In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die MRTK-Entwicklung vor.

Befolgen Sie zu diesem Zweck zunächst die Anweisungen unter [Initialisieren des Projekts und der ersten Anwendung](mrlearning-base-ch1.md), jedoch ohne die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihrem Gerät](mrlearning-base-ch1.md#build-your-application-to-your-device), die die folgenden Schritte beinhalten:

1. [Erstellen eines neuen Unity-Projekts](mrlearning-base-ch1.md#create-new-unity-project), das mit einem passenden Namen bezeichnet wird, beispielsweise *MRTK-Tutorials*

2. [Konfigurieren des Unity-Projekts für Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [Importieren von TextMesh Pro Essential-Ressourcen](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [Importieren des Mixed Reality-Toolkits](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [Konfigurieren des Unity-Projekts für das Mixed Reality-Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [Hinzufügen des Mixed Reality-Toolkits zur Unity-Szene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit), die dann einen passenden Namen erhält, beispielsweise *AzureSpatialAnchors*

Befolgen Sie dann die Anweisungen unter [Konfigurieren der Mixed Reality-Toolkitprofile (Option zum Ändern der Anzeige der räumlichen Wahrnehmung)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option), um das **DefaultHoloLens2ConfigurationProfile** als MRTK-Konfigurationsprofil für Ihre Szene festzulegen, und ändern Sie die Anzeigeoptionen für das Gittermodell zur räumlichen Wahrnehmung in **Occlusion** (Verdeckung).

> [!CAUTION]
> Wie bereits in den oben verlinkten Anweisungen zum [Konfigurieren des Unity-Projekts für das Mixed Reality-Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) erwähnt, wird dringend empfohlen, MSBuild for Unity nicht zu aktivieren.

## <a name="adding-inbuilt-unity-packages"></a>Hinzufügen von integrierten Unity-Paketen
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

In diesem Abschnitt installieren Sie das integrierte Unity AR Foundation-Paket, da es vom Azure Spatial Anchors SDK benötigt wird, das Sie im nächsten Abschnitt importieren.

Wählen Sie im Unity-Menü **Window** > **Package Manager** (Fenster > Paket-Manager) aus:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> Es kann einige Sekunden dauern, bis das AR Foundation-Paket in der Liste angezeigt wird.

Wählen Sie im Paket-Manager-Fenster die Option **AR Foundation** aus, und installieren Sie das Paket, indem Sie auf die Schaltfläche **Installieren** klicken:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Importieren der Tutorialressourcen

Laden Sie die folgenden benutzerdefinierten Unity-Pakete herunter, und **importieren** Sie sie **in der Reihenfolge, in der sie aufgelistet sind**:

* [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (Version 2.1.1)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)

> [!TIP]
> Wenn Sie eine Auffrischung zum Importieren eines benutzerdefinierten Unity-Pakets benötigen, lesen Sie die Anweisungen unter [Importieren des Mixed Reality-Toolkits](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

Nach dem Importieren der Tutorialressourcen sollte Ihr Projektfenster ähnlich wie die folgende Abbildung aussehen:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a>Erstellen und Vorbereiten der Szene
<!-- TODO: Consider renaming to 'Preparing the scene' -->

In diesem Abschnitt bereiten Sie die Szene vor, indem Sie einige der Tutorial-Prefabs hinzufügen.

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs**. Klicken Sie bei gedrückter STRG-Taste auf **ButtonParent**, **DebugWindow**, **Instructions** und **ParentAnchor**, um die vier Prefabs auszuwählen:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

Ziehen Sie die vier noch ausgewählten Prefabs auf das Hierarchiefenster, um sie der Szene hinzuzufügen:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

Um sich auf die Objekte in der Szene zu konzentrieren, können Sie auf das ParentAnchor-Objekt doppelklicken und die Ansicht dann etwas verkleinern:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> Wenn Sie die großen Symbole in Ihrer Szene, beispielsweise die mit großen Rahmen umgebenen 'T'-Symbole, irritierend finden, können Sie diese ausblenden, indem Sie <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">die Gizmos umschalten</a> (in die Aus-Position).

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Konfigurieren der Schaltflächen zum Betreiben der Szene

In diesem Abschnitt fügen Sie Skripts in die Szene ein, um eine Reihe von Schaltflächenereignissen zu erstellen, mit denen die Grundlagen des Verhaltens beider lokaler Anker und der Azure Spatial Anchors in einer Anwendung veranschaulicht werden.

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a>1. Konfigurieren der Komponente „Pressable Button Holo Lens 2 (Script)“ (Drückbare Schaltfläche HoloLens 2 (Skript))

Klappen Sie im Hierarchiefenster das **ButtonParent**-Objekt auf, und wählen Sie das erste untergeordnete Objekt mit dem Namen **StartAzureSession** aus:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

Suchen Sie im Inspektorfenster die **Pressable Button Holo Lens 2 (Script)** -Komponente, und fügen Sie dem Ereignis **Button Pressed ()** einen neuen Ereignislistener hinzu, indem Sie auf das **+** -Symbol klicken:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

Klicken Sie bei immer noch im Hierarchiefenster ausgewähltem StartAzureSession-Objekt auf das **ParentAnchor**-Objekt, und ziehen Sie es auf das leere **None (Object)** -Feld des Ereignislisteners, den Sie soeben hinzugefügt haben, um das ParentAnchor-Objekt nach Gedrückt-Ereignissen für diese Schaltfläche lauschen zu lassen:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

Klicken Sie auf die **No Function**-Dropdownliste des gleichen Ereignislisteners, wählen Sie dann **AnchorModuleScript** > **StartAzureSession ()** aus, um die StartAzureSession ()-Funktion als auszulösende Aktion festzulegen, wenn „Schaltfläche gedrückt“-Ereignisse von dieser Schaltfläche gesendet werden:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a>2. Konfigurieren der Interactable (Script)-Komponente

Suchen Sie bei immer noch im Hierarchiefenster ausgewähltem StartAzureSession-Objekt im Inspektorfenster die Komponente **Interactable (Script)** , und wiederholen Sie den gleichen Prozess wie in Schritt 1 oben für das **OnClick ()** -Ereignis:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a>3. Konfigurieren der verbleibenden Schaltflächen

Führen Sie für jede der verbleibenden Schaltflächen den in Schritt 1 und 2 beschrieben Vorgang aus, um den **Button Pressed ()** - und **OnClick ()** -Ereignissen Funktionen zuzuweisen:

* Weisen Sie dem **StopAzureSession**-Objekt die AnchorModuleScript > **StopAzureSession ()** -Funktion zu.
* Weisen Sie dem **CreateAzureAnchor**-Objekt die AnchorModuleScript > **CreateAzureAnchor ()** -Funktion zu,
  * und ziehen Sie dann den **ParentAnchor** erneut auf das leere **None (Game Object)** -Feld.
* Weisen Sie dem **RemoveLocalAnchor**-Objekt die AnchorModuleScript > **RemoveLocalAnchor ()** -Funktion zu,
  * und ziehen Sie dann den **ParentAnchor** erneut auf das leere **None (Game Object)** -Feld.
* Weisen Sie dem **FindAzureAnchor**-Objekt die AnchorModuleScript > **FindAzureAnchor ()** -Funktion zu.
* Weisen Sie dem **DeleteAzureAnchor**-Objekt die AnchorModuleScript > **DeleteAzureAnchor ()** -Funktion zu.

### <a name="4-connect-the-scene-to-the-azure-resource"></a>4. Verbinden der Szene mit der Azure-Ressource

Wählen Sie im Hierarchiefenster das **ParentAnchor**-Objekt aus, und scrollen Sie im Inspektorfenster zur Komponente **Spatial Anchor Manager (Script)** herunter.

Fügen Sie dann im Abschnitt **Credentials** (Anmeldeinformationen) Ihr Raumankerkonto und den zugehörigen Schlüssel, die Sie im Rahmen der [Voraussetzungen](mrlearning-asa-ch1.md#prerequisites) dieses Tutorials erstellt haben, in die entsprechenden Felder **Spatial Anchors Account Id** und **Spatial Anchors Account Key** ein:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Testen der grundlegenden Verhaltensweisen von Azure Spatial Anchors

Jetzt, da Ihre Szene für die Veranschaulichung der Grundlagen von Azure Spatial Anchors konfiguriert ist, ist es Zeit, die App bereitzustellen, damit Sie Azure Spatial Anchors aus erster Hand erleben können.

### <a name="1-add-additional-required-capabilities"></a>1. Hinzufügen zusätzlicher erforderlicher Funktionen

Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen...) aus, um das Fenster „Player Settings“ (Playereinstellungen) zu öffnen:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

Wählen Sie im Player Settings-Fenster **Player** und dann **Publishing Settings** (Veröffentlichungseinstellungen) aus:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

Scrollen Sie in den **Publishing Settings** nach unten zum Abschnitt **Capabilities** (Funktionen), und vergewissern Sie sich, dass die Funktionen **InternetClient**, **Microphone** und **SpatialPerception**, die Sie im Rahmen der Erstellung des Projekts zu Beginn des Tutorials erstellt haben, aktiviert sind. Aktivieren Sie dann die Funktionen **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage** und **Webcam**:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2. Bereitstellen der App auf Ihrer HoloLens 2

Azure Spatial Anchors können nicht in Unity ausgeführt werden, daher müssen Sie das Projekt auf Ihrem Gerät bereitstellen, um die Azure Spatial Anchors-Funktionalität zu testen.

> [!TIP]
> Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer Anwendung auf Ihrem Gerät](mrlearning-base-ch1.md#build-your-application-to-your-device).

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3. Führen Sie die App auf Ihrer HoloLens 2 aus, und folgen Sie den Anweisungen in der App

> [!CAUTION]
> Azure Spatial Anchors verwendet das Internet zum Speichern und Laden der Ankerdaten, achten Sie also darauf, dass Ihr Gerät über eine Internetverbindung verfügt.

Wenn die Anwendung auf Ihrem Gerät ausgeführt wird, befolgen Sie die Anweisungen auf dem Bildschirm, die im Anweisungsbereich des Azure Spatial Anchor-Tutorials angezeigt werden:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a>Verankern eines Benutzererlebnisses

In den vorherigen Abschnitten haben Sie die Grundlagen von Azure Spatial Anchors kennengelernt. Wir haben einen Würfel verwendet, um das übergeordnete Spielobjekt mit dem angefügten Anker dazustellen und zu visualisieren. In diesem Abschnitt erfahren Sie, wie Sie ein gesamtes Benutzererlebnis verankern, indem Sie es als untergeordnetes Objekt des ParentAnchor-Objekts platzieren.

### <a name="1-add-the-rocket-launcher-experience"></a>1. Hinzufügen der Raketenstartbasis-Benutzererfahrung

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher**, und wählen Sie das Prefab **RocketLauncher_Complete** aus:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

Ziehen Sie das noch ausgewählte Prefab  „RocketLauncher_Complete“ auf das **ParentAnchor**-Objekt im Hierarchiefenster, um es zu einem untergeordneten Objekt des ParentAnchor-Objekts zu machen:

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a>2. Neupositionieren der Raketenstartbasis-Benutzererfahrung

Positionieren, drehen und skalieren Sie das **RocketLauncher_Complete**-Objekt auf einen passenden Maßstab und eine passende Ausrichtung, und stellen Sie zugleich sicher, dass das **ParentAnchor**-Objekt noch verfügbar ist, beispielsweise:

* **Transformationsposition** X = 0, Y = -0, Z = 3,75
* **Transformationsrotation** X = 0, Y = 90, Z = 0
* **Transformationsmaßstab** X = 10, Y = 10, Z = 10

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

In der Anwendung können die Benutzer nun die gesamte Raketenstartbasis-Benutzererfahrung neu positionieren, indem sie den Würfel bewegen.

> [!TIP]
> Es gibt eine Vielzahl von Benutzererlebnisabläufen für die Neupositionierung von Erlebnissen, einschließlich der Verwendung eines Neupositionierungsobjekts (wie des Würfels, der in diesem Tutorial verwendet wird), der Verwendung einer Schaltfläche zum Umschalten eines Begrenzungsrahmens, der das Erlebnis umgibt, der Verwendung von Gizmos für Position und Drehung und mehr.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie die Grundlagen von Azure Spatial Anchors kennengelernt. Das Tutorial hat Ihnen verschiedene Schaltflächen an die Hand gegeben, mit denen Sie die verschiedenen Schritte erkunden konnten, die zum Starten und Beenden einer Azure-Spatial Anchors-Sitzung und zum Erstellen, Hochladen und Herunterladen von Azure Anchors auf einem einzelnen Gerät erforderlich sind.

In der nächsten Lektion erfahren Sie, wie Azure Anchor-IDs für den Abruf auf Ihrer HoloLens 2 gespeichert werden, auch nach einem Neustart der Anwendung, und wie Anchor-IDs zwischen mehreren Geräten übertragen werden, um räumliche Ausrichtung zu erzielen.

[Nächste Lektion: 2. Speichern, Abrufen und Freigeben von Azure Spatial Anchors](mrlearning-asa-ch2.md)
