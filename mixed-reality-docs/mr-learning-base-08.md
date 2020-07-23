---
title: 'Tutorials zu den ersten Schritten: 8. Verwenden von Eye Tracking'
description: In diesem Kurs erfahren Sie, wie Sie das Mixed Reality Toolkit (MRTK) verwenden, um eine Mixed Reality-Anwendung zu erstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 9a9fc7f860e6bf9c5cb3370a9c9ff11e627fe73f
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305673"
---
# <a name="8-using-eye-tracking"></a>8. Verwenden von Eye Tracking

## <a name="overview"></a>Übersicht

In diesem Tutorial erfahren Sie, wie Sie Eye Tracking für HoloLens 2 aktivieren und Objekten Eye Tracking hinzufügen, um Aktionen auszulösen, wenn der Benutzer die Objekte ansieht.

> [!NOTE]
> Wenn Sie dieses Projekt auch in HoloLens (1. Generation) bereitstellen, beachten Sie, dass Eye Tracking nur in HoloLens 2 unterstützt wird.

## <a name="objectives"></a>Ziele

* Erfahren, wie Eye Tracking für HoloLens 2 aktiviert wird
* Erfahren, wie Eye Tracking zum Auslösen von Aktionen verwendet wird

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a>Sicherstellen, dass die Eingabe durch Anvisieren mit den Augen aktiviert ist

Wählen Sie im Unity-Menü „Mixed Reality Toolkit > Utilities > **Configure Unity Project**“ (Mixed Reality Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) aus, um das Fenster **MRTK Project Configurator** (MRTK-Projektkonfigurator) zu öffnen, und überprüfen Sie dann im Abschnitt **UWP Capabilities** (UWP-Funktionen), ob die Funktion **Enable Eye Gaze Input** (Eingabe durch Anvisieren mit den Augen) grau dargestellt wird:

![mr-learning-base](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> Die Funktion zur Eingabe durch Anvisieren hätte im Rahmen der Anweisungen zum [Übernehmen der Einstellungen des MRTK-Projektkonfigurators](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) aktiviert werden sollen, während der ursprünglichen Konfiguration des Unity-Projekts zu Beginn dieser Tutorialreihe. Sollte sie nicht aktiviert sein, achten Sie darauf, sie jetzt zu aktivieren.

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>Aktivieren des Anvisierens mit den Augen im Blickanbieter

Wählen Sie im Hierarchiefenster das Objekt **MixedRealityToolkit** aus, wählen Sie dann im Inspektorfenster die Registerkarte „MixedRealityToolkit > **Input**“ aus, und führen Sie die folgenden Schritte aus:

* Klonen Sie das Profil **DefaultHoloLens2InputSystemProfile**, und geben Sie ihm einen passenden Namen, beispielsweise _GettingStarted_HoloLens2InputSystemProfile_
* Erweitern Sie den Abschnitt **Pointers** (Zeiger)
* Klonen Sie das Profil **DefaultMixedRealityPointerProfile**, und geben Sie ihm einen passenden Namen, beispielsweise _GettingStarted_MixedRealityPointerProfile_
* Suchen Sie den Abschnitt **Gaze Settings** (Blickeinstellungen), und aktivieren Sie das Kontrollkästchen **Is Eye Tracking Enabled** (Ist Eye Tracking aktiviert)

![mr-learning-base](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> Wenn Sie eine Auffrischung zum Klonen von MRTK-Profilen benötigen, lesen Sie die Anweisungen in [Konfigurieren der MRTK-Profile](mr-learning-base-03.md).

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a>Aktivieren von simuliertem Eye Tracking für den Unity-Editor

Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt aus, und navigieren Sie dann im Inspektorfenster zur Registerkarte **Input** (Eingabe). Führen Sie dann Folgendes aus:

* Klappen Sie den Abschnitt **Input Data Providers** > **Input Simulation Service** (Eingabedatenanbieter > Eingabesimulationsdienst) auf
* Klonen Sie das Profil **DefaultMixedRealityInputSimulationProfile**, und geben Sie ihm einen passenden Namen, beispielsweise _GettingStarted_MixedRealityInputSimulationProfile_
* Suchen Sie den Abschnitt **Eye Simulation** (Augensimulation), und aktivieren Sie das Kontrollkästchen **Simulate Eye Position** (Augenposition simulieren)

![mr-learning-base](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a>Hinzufügen von Eye Tracking zu Objekten

Klappen Sie im Hierarchiefenster das Objekt „RoverExplorer > **Buttons**“ (RoverExplorer > Schaltflächen) auf, klappen Sie dann für jedes der drei untergeordneten Schaltflächenobjekte das Objekt „SeeItSayItLabel > **TextMeshPro**“ auf, und wählen Sie es aus:

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-1.png)

Verwenden Sie, während die drei TextMeshPro-Objekte noch ausgewählt sind, im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um allen ausgewählten Objekten die folgenden Komponenten hinzuzufügen:

* **Box Collider**-Komponente
* **EyeTrackingTarget**-Komponente

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-2.png)

Wählen Sie im Hierarchiefenster das Objekt **Hints** > SeeItSayItLabel > **TextMeshPro** (Hinweise > SeeItSayItLabel > TextMeshPro) aus, und konfigurieren Sie dann die **EyeTrackingTarget**-Komponente wie folgt:

* Im Ereignisabschnitt **On Look At Start ()**
  * Klicken Sie auf das kleine **+** -Symbol, um ein weiteres Ereignis hinzuzufügen
  * Weisen Sie das Objekt selbst, d. h. das gleiche **TextMeshPro**-Objekt, dem Feld **None (Object)** (Ohne (Objekt)) zu
  * Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **TextMeshPro** > **float fontSize** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird
  * Legen Sie das Argument auf **0,06** fest, um den aktuellen Schriftgrad von 0,04 um 50 % zu erhöhen
* Im Ereignisabschnitt **On Look Away ()**
  * Klicken Sie auf das kleine **+** -Symbol, um ein weiteres Ereignis hinzuzufügen
  * Weisen Sie das Objekt selbst, d. h. das gleiche **TextMeshPro**-Objekt, dem Feld **None (Object)** (Ohne (Objekt)) zu
  * Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **TextMeshPro** > **float fontSize** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird
  * Legen Sie das Argument auf **0,04** fest, um den Schriftgrad wieder auf 0,04 zurückzusetzen

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-3.png)

**Wiederholen** Sie diesen Schritt für das Objekt **Explode** > SeeItSayItLabel > **TextMeshPro** (Explodieren > SeeItSayItLabel > TextMeshPro) und das Objekt **Reset** > SeeItSayItLabel > **TextMeshPro** (Zurücksetzen > SeeItSayItLabel > TextMeshPro).

Wenn Sie jetzt in den Spielmodus wechseln, dann die rechte Maustaste drücken und sie gedrückt halten, während Sie die Maus bewegen, bis der Blick auf eine der Bezeichnungen trifft, sehen Sie dass sich der Schriftgrad um 50 % vergrößert und wieder zur normalen Größe zurückkehrt, wenn Sie den Blick abwenden:

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie erfahren, wie Sie Eye Tracking für HoloLens 2 aktivieren und Objekten Eye Tracking hinzufügen, um Aktionen auszulösen, wenn der Benutzer die Objekte ansieht.

[Nächstes Tutorial: 9. Verwenden von Sprachbefehlen](mr-learning-base-09.md)