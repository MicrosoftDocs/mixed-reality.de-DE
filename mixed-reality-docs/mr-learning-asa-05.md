---
title: 'Tutorials zu Azure Spatial Anchors: 5 Azure Spatial Anchors für Android und iOS'
description: In diesem Kurs lernen Sie, wie Sie ein Unity-Projekt mit dem Mixed Reality Toolkit und Azure Spatial Anchors unter Android und iOS bereitstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, Android, iOS
ms.localizationpriority: high
ms.openlocfilehash: 8c63204948b3e4aa3d25e5b2ca948798726f0838
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376542"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a>5. Azure Spatial Anchors für Android und iOS

In diesem Tutorial erfahren Sie, wie Sie Ihr Projekt für Android- und iOS-Geräte mithilfe von AR Foundation, dem ARCore XR-Plug-In und dem ARKit-XR-Plug-In erstellen.

## <a name="objectives"></a>Ziele

* Lernen, wie Sie ein Projekt für Android-Geräte mithilfe von Unity AR Foundation und dem ARCore XR-Plug-In erstellen
* Lernen, wie Sie ein Projekt für iOS-Geräte mithilfe von Unity AR Foundation und dem ARKit XR-Plug-In erstellen

## <a name="installing-inbuilt-unity-packages"></a>Installieren von integrierten Unity-Paketen

In diesem Abschnitt führen Sie ein Upgrade aus und installieren die folgenden integrierten Pakete:

* AR Foundation 3.1.3
* Legacy Input Helpers 2.1.4
* ARCore XR-Plug-In 3.1.3 für Android-Unterstützung
* ARKit XR-Plug-In 3.1.3 für iOS-Unterstützung

> [!CAUTION]
> Nicht alle Versionen sind mit MRTK kompatibel, und nur bestimmte Versionen funktionieren zusammen, achten Sie also darauf, genau die oben aufgeführten Versionen zu installieren.

Wählen Sie im Unity-Menü **Fenster** > **Package Manager** (Paket-Manager) aus, um das Fenster „Package Manager“ zu öffnen, wählen Sie dann **AR Foundation** > **3.1.3** aus, und klicken Sie auf die Schaltfläche **Update to 3.1.3** (Auf 3.1.3 aktualisieren), um das Paket zu aktualisieren:

![mr-learning-asa](images/mr-learning-asa/asa-05-section1-step1-1.png)

Befolgen Sie die gleiche Vorgehensweise, um bei Bedarf die verbleibenden Pakete zu installieren.

> [!NOTE]
> Wenn Sie dieses Projekt für Android entwickeln, ist es nicht erforderlich, das ARKit XR-Plug-In-Paket zu installieren. Analog dazu brauchen Sie, wenn Sie dieses Projekt für iOS entwickeln, das ARCore XR-Plug-In nicht zu installieren.

## <a name="configure-mrtk-for-ar-foundation-camera"></a>Konfigurieren des MRTK für die AR Foundation Camera

In diesem Abschnitt erfahren Sie, wie Sie das MRTK für die Bereitstellung auf einem mobilen Gerät konfigurieren.

Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt aus. Wählen Sie dann im Inspektorfenster die Registerkarte **Camera** (Kamera) aus, klonen Sie das Kameraprofil, und geben Sie ihm einen passenden Namen, beispielsweise **AzureSpatialAnchors_ARCameraProfile**:

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> Wenn Sie eine Auffrischung zum Klonen von MRTK-Profilen benötigen, lesen Sie die Anweisungen in [Konfigurieren der Mixed Reality Toolkit-Profile](mr-learning-base-03.md).

Klappen Sie bei im Inspektorfenster noch ausgewählter Registerkarte **Camera** (Kamera) die **Camera Setting Providers** (Anbieter von Kameraeinstellungen) auf, und klicken Sie auf die Schaltfläche **+ Add Camera Setting Provider** (Anbieter von Kameraeinstellungen hinzufügen). Klappen Sie dann den neu hinzugefügten **New data provider 1** (Neuer Datenanbieter 1) auf:

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-2.png)

Ändern Sie mithilfe der **Type**-Dropdownliste den Typ in **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-3.png)

Verwenden Sie bei im Hierarchiefenster noch ausgewähltem **MixedRealityToolkit**-Objekt die Schaltfläche **Add Component** (Komponente hinzufügen) im Inspektorfenster, um die folgenden Komponenten hinzuzufügen:

* AR Anchor Manager (Script)
* DisableDiagnosticsSystem (Script)

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-4.png)

> [!NOTE]
> Wenn Sie die Komponente „AR Reference Point Manager (Script)“ hinzufügen, wird die Komponente „AR Session Origin (Script)“ automatisch hinzugefügt, da sie von der Komponente „AR Reference Point Manager (Script)“ benötigt wird.

## <a name="building-your-application-to-your-android-device"></a>Erstellen Ihrer Anwendung für Ihr Android-Gerät

In diesem Abschnitt erfahren Sie, wie Sie Ihr Projekt so konfigurieren, dass es für ein Android-Gerät erstellt und auf diesem bereitgestellt wird.

Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen, und ändern Sie die Plattform dann in Android:

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> Falls Sie eine Auffrischung zum Wechseln der Buildplattform benötigen, lesen Sie die Anweisungen zum [Wechseln der Buildplattform](mr-learning-base-02.md#switching-the-build-platform).

Schließen Sie das Fenster „Build Settings“ (Buildeinstellungen).

Wählen Sie im Unity-Menü **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) aus, um das **MRTK Project Configurator**-Fenster (MRTK-Projektkonfigurator) zu öffnen, vergewissern Sie sich, dass alle Optionen ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Übernehmen**, um die Einstellungen zu übernehmen:

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-2.png)

Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen) aus, um das Fenster mit den Playereinstellungen zu öffnen, suchen Sie dann den Abschnitt **Player** >  **Other Settings** (Player > Weitere Einstellungen), wählen Sie **Vulkan** aus, und entfernen Sie die Einstellung, indem Sie auf das **„-“** -Symbol klicken:

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-3.png)

Schließen Sie das Fenster „Playereinstellungen“, und öffnen Sie das Fenster „Buildeinstellungen“ erneut.

Klicken Sie im Fenster „Buildeinstellungen“ auf die Schaltfläche **Add Open Scenes** (Geöffnete Szenen hinzufügen), um Ihre aktuelle Szene zur Liste **Scenes In Build** (Szenen im Build) hinzuzufügen. Verwenden Sie dann ein USB-Kabel, um Ihr Android-Gerät mit Ihrem Computer zu verbinden, und wählen Sie es in der Dropdownliste **Run Device** (Ausführendes Gerät) aus:

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> Wenn Ihr Gerät nicht in der Dropdownliste „Run Device“ angezeigt wird, müssen Sie möglicherweise auf die Aktualisieren-Schaltfläche neben der Dropdownliste klicken.

Klicken Sie im Fenster „Buildeinstellungen“ auf die Schaltfläche **Build And Run** (Erstellen und ausführen), um das Fenster „Build Android“ (Für Android erstellen) zu öffnen.

Wählen Sie einen geeigneten Speicherplatz zum Speichern Ihres Builds, beispielsweise _D:\MixedRealityLearning\Builds_, geben Sie dann dem APK einen passenden Namen, beispielsweise _MRTKTutorials-AzureSpatialAnchors_, und klicken Sie auf die **Speichern**-Schaltfläche, um den Buildprozess zu starten:

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
Wenn im Fenster der Unity-Konsole irgendwelche Fehler im Zusammenhang mit Android SDK-, NDK- oder JDK-Modulen angezeigt werden, müssen Sie den Unity Hub öffnen und die zugehörigen Module für die Android-Buildunterstützung installieren.

Wenn der Buildvorgang abgeschlossen ist, sollten Ihre Apps automatisch auf dem Android-Gerät geladen werden.

## <a name="building-your-application-to-your-ios-device"></a>Erstellen Ihrer Anwendung für Ihr iOS-Gerät

In diesem Abschnitt erfahren Sie, wie Sie Ihr Projekt so konfigurieren, dass es für ein iOS-Gerät erstellt und auf diesem bereitgestellt wird.

Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen, und ändern Sie die Plattform in iOS:

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> Falls Sie eine Auffrischung zum Wechseln der Buildplattform benötigen, lesen Sie die Anweisungen zum [Wechseln der Buildplattform](mr-learning-base-02.md#switching-the-build-platform).

Schließen Sie das Fenster „Build Settings“ (Buildeinstellungen).

Wählen Sie im Unity-Menü **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) aus, um das **MRTK Project Configurator**-Fenster (MRTK-Projektkonfigurator) zu öffnen, vergewissern Sie sich, dass alle Optionen ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Übernehmen**, um die Einstellungen zu übernehmen:

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-2.png)

Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen) aus, um das Fenster mit den Playereinstellungen zu öffnen, suchen Sie dann den Abschnitt **Player** >  **Other Settings** (Player > Weitere Einstellungen), und deaktivieren Sie das Kontrollkästchen **Strip Engine Code** (Engine-Code entfernen), um es zu deaktivieren:

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-3.png)

Schließen Sie das Fenster „Player Settings“ (Playereinstellungen), und öffnen Sie das Fenster **Build Settings** (Buildeinstellungen) erneut.

Klicken Sie im Fenster „Buildeinstellungen“ auf die Schaltfläche **Add Open Scenes** (Geöffnete Szenen hinzufügen), um Ihre aktuelle Szene der Liste **Scenes In Build** (Szenen im Build) hinzuzufügen:

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-4.png)

Klicken Sie im Fenster „Buildeinstellungen“ auf die Schaltfläche **Erstellen**, um das Fenster „Build iOS“ (Für iOS erstellen) zu öffnen.

Wählen Sie einen geeigneten Speicherplatz zum Speichern Ihres Xcode-Projekts, beispielsweise _D:\MixedRealityLearning\Builds_, erstellen Sie einen neuen Ordner, geben Sie ihm einen passenden Namen, beispielsweise _MRTKTutorials-AzureSpatialAnchors_, und klicken Sie dann auf die Schaltfläche **Select Folder** (Ordner auswählen), um den Buildvorgang zu starten:

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-5.png)

Wenn der Buildvorgang abgeschlossen ist, befolgen Sie die Anweisungen in [Export the Xcode project](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) (Xcode-Projekt exportieren), um Ihr Xcode-Projekt auf Ihrem iOS-Gerät bereitzustellen.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie erfahren, wie Sie Ihr Projekt für Android- und iOS-Geräte mithilfe von AR Foundation, dem ARCore XR-Plug-In und dem ARKit-XR-Plug-In erstellen.
