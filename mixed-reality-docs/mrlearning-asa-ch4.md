---
title: 'Tutorials zu Azure Spatial Anchors: 4 Azure Spatial Anchors für Android und iOS'
description: In diesem Tutorial erfahren Sie, wie Sie Azure Spatial Anchors in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/18/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, Kurs, HoloLens, Azure, Spatial Anchors
ms.localizationpriority: high
ms.openlocfilehash: 78fa6a2cdd29bd424ec3016a5467760063b87a14
ms.sourcegitcommit: 7011ac6fde80e5c45f04192fa1db6e1eb559e3b0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/03/2020
ms.locfileid: "84327932"
---
# <a name="4-azure-spatial-anchors-for-android-and-ios"></a>4. Azure Spatial Anchors für Android und iOS

In diesem Tutorial erfahren Sie, wie Sie Ihr Projekt für Android- und iOS-Geräte mithilfe von AR Foundation, dem ARCore XR-Plug-In und dem ARKit-XR-Plug-In erstellen.

## <a name="objectives"></a>Ziele

* Lernen, wie Sie ein Projekt für Android-Geräte mithilfe von Unity AR Foundation und dem ARCore XR-Plug-In erstellen.
* Lernen, wie Sie ein Projekt für iOS-Geräte mithilfe von Unity AR Foundation und dem ARKit XR-Plug-In erstellen.

> [!NOTE]
> Um dieses Tutorial abzuschließen, sollten Sie unbedingt Azure Spatial Anchors-Tutorials > [Erste Schritte mit Azure Spatial Anchors](mrlearning-asa-ch1.md) durchgearbeitet haben.

## <a name="adding-inbuilt-unity-packages"></a>Hinzufügen von integrierten Unity-Paketen

In diesem Abschnitt installieren Sie die Pakete für die in Unity integrierte AR Foundation, das ARCore XR-Plug-In und das ARKit XR-Plug-In zur Unterstützung von Android- und iOS-Geräten.

Achten Sie darauf, die richtige Version dieser Unity-Pakete zu installieren, wie unten aufgeführt:

* **AR Foundation 2.1.4**
* **Arcore-XR-Plug-In 2.2.0 Preview 2**
* **ARKit XR-Plug-In 2.1.1**

> [!NOTE]
> Wenn Sie dieses Projekt für Android entwickeln, ist es nicht erforderlich, das ARKit XR-Plug-In-Paket zu installieren. Analog dazu brauchen Sie, wenn Sie dieses Projekt für iOS entwickeln, das ARCore XR-Plug-In nicht zu installieren.

Wählen Sie im Unity-Menü **Window** > **Package Manager** (Fenster > Paket-Manager) aus:

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-1.png)

Es kann einige Sekunden dauern, bis alle Pakete in der Liste angezeigt werden. Sie zeigen Vorschaupakete an, indem Sie auf die Option „Advanced“ (Erweitert) klicken und dann **Show preview packages** (Vorschaupakete anzeigen) auswählen.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-2.png)

Wählen Sie im Fenster des Paket-Managers **AR Foundation** aus. Hier werden viele Versionen angezeigt, Sie müssen **Version 2.1.4** auswählen und das Paket aktualisieren, indem Sie auf die Schaltfläche **Update to 2.1.4** (Auf 2.1.4 aktualisieren) klicken:

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-3.png)

Um Android-Geräte zu unterstützen, führen Sie den gleichen Vorgang wie beim Importieren von **ARCore XR Plugin 2.2.0 Preview 2** aus.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-4.png)

Um iOS-Geräte zu unterstützen, sollten Sie das Unity-Paket **ARKit XR-Plug-In 2.1.1** aus dem Paket-Manager installieren.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-5.png)

## <a name="customize-mrtk-to-support-ar-foundation-camera"></a>Anpassen von MRTK zur Unterstützung der AR Foundation-Kamera

Passen Sie die MRTK-Einstellungen für die Unterstützung von AR Foundation an, indem Sie im Hierarchiefenster „MixedRealityToolKit“ auswählen und im Inspektorfenster auf die Schaltfläche **Clone** (Klonen) im Mixed Reality ToolKit klicken.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-1.png)

Wenn Sie auf die Schaltfläche **Clone** klicken, wird ein neues Fenster „Clone Profile“ (Profil klonen) angezeigt. Klicken Sie erneut auf die Schaltfläche **Clone**, um das **DefaultMixedRealityToolkitProfile** zu klonen.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-2.png)

Klonen Sie **Camera Profile** im Inspektorfenster entsprechend.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-3.png)

Suchen Sie im Inspektorfenster „MixedReality“, und wählen Sie die Registerkarte **Camera** aus. Erweitern Sie die Kameraeinstellungsanbieter im Inspektorfenster, und klicken Sie auf **+ Add Camera Setting Provider** (Anbieter von Kameraeinstellungen hinzufügen) > erweitern Sie **New data provider 1** (Neuer Datenanbieter 1) > wählen Sie den Typ **None** (Keiner) aus > wählen Sie **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > wählen Sie **UnityARCameraSettings** aus.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-4.png)

Fügen Sie bei im Inspektorfenster ausgewähltem MixedRealityToolKit-Objekt Unterstützungsskripts an, indem Sie auf die Schaltfläche **Add component** (Komponente hinzufügen) klicken, „AR Reference Point Manager“ (AR-Bezugspunkt-Manager) eingeben und das Skript auswählen.

Durch Hinzufügen des Skripts **AR Reference Point Manager** wird automatisch **AR session origin** (AR-Sitzungsursprung) im Inspektorfenster hinzugefügt. Nach dem Hinzufügen der Unterstützungsskripts sollte das Inspektorfenster wie folgt aussehen.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-5.png)

## <a name="build-an-application-to-an-android-device"></a>Erstellen einer Anwendung für ein Android-Gerät

Um diese Anwendung für Ihr Android-Gerät zu erstellen, klicken Sie oben im Fenster auf **Datei**, und wählen Sie **Buildeinstellungen** aus. Auf dem Bildschirm wird ein neues Fenster angezeigt. Wählen Sie **Android** aus, und klicken Sie auf **Switch Platform** (Plattform wechseln). Das Wechseln der Plattform nimmt einige Minuten in Anspruch. Klicken Sie nach dem Wechsel zur Android-Plattform auf **Add Open Scenes** (Offene Szenen hinzufügen), und vergewissern Sie sich, dass Ihre aktuelle Szene die einzige ausgewählte Szene in der Liste **Szenen in Build** ist.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-1.png)

Schließen Sie das Fenster **Buildeinstellungen**. Wählen Sie im Unity-Menü „Mixed Reality Toolkit“ > „Utilities“ (Hilfsprogramme) > „Configure Unity Project“ (Unity-Projekt konfigurieren) aus, und klicken Sie auf **Apply** (Übernehmen), um das Unity-Projekt für die Android-Plattform zu konfigurieren.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-2.png)

Wählen Sie im Unity-Menü **Edit** > **Project Settings** (Bearbeiten > Projekteinstellungen) aus, um das Fenster „Project Settings“ (Projekteinstellungen) zu öffnen. Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) die Registerkarte **Player** aus, erweitern Sie den Abschnitt **Other Settings** (Weitere Einstellungen), wählen Sie **Vulkan** aus, und entfernen Sie die Einstellung, indem Sie auf das Minuszeichen ( **-** ) klicken.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-3.png)

Schließen Sie das Fenster **Player Settings** (Playereinstellungen), und öffnen Sie das Fenster **Build Settings** (Buildeinstellungen) erneut. Verbinden Sie dann Ihr Android-Gerät über ein USB-Kabel mit Ihrem Computer, wählen Sie Ihr Gerät in der Dropdownliste **Build and Run on** (Erstellen und Ausführen auf) aus, und klicken Sie dann auf **Build And Run** (Erstellen und ausführen). Sie werden aufgefordert, eine APK-Datei zu speichern, der Sie einen beliebigen Namen geben können.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-4.png)

> [!NOTE]
> Wenn im Fenster der Unity-Konsole irgendwelche Fehler im Zusammenhang mit Android SDK-, NDK- und/oder JDK-Modulen angezeigt werden, müssen Sie den Unity Hub öffnen und die zugehörigen SDK-, NDK- und JDK-Module für das Modul zur Android-Buildunterstützung installieren.

Wenn der Buildvorgang abgeschlossen ist, sollten Ihre Anwendungen automatisch auf dem Android-Gerät geladen werden.

## <a name="build-an-application-to-ios-device"></a>Erstellen einer Anwendung für ein iOS-Gerät

Um diese Anwendung für Ihr iOS-Gerät zu erstellen, klicken Sie oben im Fenster auf **Datei**, und wählen Sie **Buildeinstellungen** aus. Auf dem Bildschirm wird ein neues Fenster angezeigt, wählen Sie **iOS** aus, und klicken Sie auf **Plattform wechseln**.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-1.png)

Schließen Sie das Fenster **Buildeinstellungen**. Wählen Sie im Unity-Menü „Mixed Reality Toolkit“ > „Utilities“ (Hilfsprogramme) > „Configure Unity Project“ (Unity-Projekt konfigurieren) aus, und klicken Sie auf **Apply** (Übernehmen), um das Unity-Projekt für die iOS-Plattform zu konfigurieren.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-2.png)

Um das iOS-XCode-Projekt zu erstellen, wechseln Sie zu den Buildeinstellungen, und klicken Sie auf **Build** (Erstellen).

Folgen Sie [diesem Leitfaden](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project), um zu erfahren, wie Sie dieses Projekt auf Ihrem iOS-Gerät bereitstellen.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, wie Sie Ihr Projekt für Android- und iOS-Geräte erstellen. Außerdem haben Sie gelernt, wie Sie AR Foundation, das ARCore XR-Plug-In und das ARKit XR-Plug-In verwenden, damit Ihr Projekt auf Android- und iOS-Geräten funktioniert.
