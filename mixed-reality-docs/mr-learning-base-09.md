---
title: 'Tutorials zu den ersten Schritten: 9. Verwenden von Sprachbefehlen'
description: In diesem Kurs erfahren Sie, wie Sie das Mixed Reality Toolkit (MRTK) verwenden, um eine Mixed Reality-Anwendung zu erstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: ed31c3b11497a0adc91b7ddc1c09b3fb4ca1c573
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305093"
---
# <a name="9-using-speech-commands"></a>9. Verwenden von Sprachbefehlen

## <a name="overview"></a>Übersicht

In diesem Tutorial erfahren Sie, wie Sie Sprachbefehle erstellen und diese global steuern. Außerdem erfahren Sie, wie Sie lokale Sprachbefehle steuern, die es erfordern, dass der Benutzer das Objekt ansieht, das den Sprachbefehl steuert.

## <a name="objectives"></a>Ziele

* Erfahren, wie Sprachbefehle erstellt werden
* Erfahren, wie Sie Sprachbefehle global und lokal gesteuert werden

## <a name="ensuring-the-microphone-capability-is-enabled"></a>Sicherstellen, dass die Mikrofonfunktion aktiviert ist

Wählen Sie im Unity-Menü „Mixed Reality Toolkit > Utilities > **Configure Unity Project**“ (Mixed Reality Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) aus, um das Fenster **MRTK Project Configurator** (MRTK-Projektkonfigurator) zu öffnen, und überprüfen Sie dann im Abschnitt **UWP Capabilities** (UWP-Funktionen), ob die Funktion **Enable Microphone Capability** (Mikrofonfunktion aktivieren) grau dargestellt wird:

![mr-learning-base](images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> Die Mikrofonfunktion hätte im Rahmen der Anweisungen zum [Übernehmen der Einstellungen des MRTK-Projektkonfigurators](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) aktiviert werden sollen, während der ursprünglichen Konfiguration des Unity-Projekts zu Beginn dieser Tutorialreihe. Sollte sie nicht aktiviert sein, achten Sie darauf, sie jetzt zu aktivieren.

## <a name="creating-speech-commands"></a>Erstellen von Sprachbefehlen

Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt und dann im Inspektorfenster die Registerkarte „MixedRealityToolkit > **Input**“ (MixedRealityToolkit > Eingabe) aus. Führen Sie dann die folgenden Schritte aus:

* Klappen Sie den Abschnitt **Speech** (Sprache) auf
* Klonen Sie das Profil **DefaultMixedRealitySpeechCommandsProfile**, und geben Sie ihm einen passenden Namen, beispielsweise _GettingStarted_MixedRealitySpeechCommandsProfile_
* Vergewissern Sie sich, dass **Start Behaviour** (Startverhalten) auf **Auto Start** (Automatischer Start) festgelegt ist

![mr-learning-base](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> Wenn Sie eine Auffrischung zum Klonen von MRTK-Profilen benötigen, lesen Sie die Anweisungen in [Konfigurieren der MRTK-Profile](mr-learning-base-03.md).

Klicken Sie im Abschnitt „Speech > **Speech Commands**“ (Sprache > Sprachbefehle) vier Mal auf die Schaltfläche **+ Add a New Speech Command** (Neuen Sprachbefehl hinzufügen), um unten in der Liste der vorhandenen Sprachbefehle einen neuen Sprachbefehl hinzuzufügen, und geben Sie dann in den **Keyword**-Feldern (Schlüsselwort) die folgenden Ausdrücke ein:

* Enable Indicator (Indikator aktivieren)
* Enable Tap to Place (Zum Platzieren tippen aktivieren)
* Enable Bounding Box (Begrenzungsrahmen aktivieren)
* Disable Bounding Box (Begrenzungsrahmen deaktivieren)

![mr-learning-base](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> Wenn Ihr Computer nicht über ein Mikrofon verfügt, können Sie den Sprachbefehlen einen Tastencode zuweisen, sodass Sie sie durch Drücken der entsprechenden Taste auslösen können.

## <a name="controlling-speech-commands"></a>Steuern von Sprachbefehlen

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** (Medienobjekte > MRTK > SDK > Features > UX > Prefabs > QuickInfo), um die QuickInfo-Prefabs zu suchen:

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-1.png)

Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf eine leere Stelle, und wählen Sie **Create Empty** (Leer erstellen) aus, um Ihrer Szene ein leeres Objekt hinzuzufügen.

Benennen Sie das Objekt **SpeechInputHandler_Global**, verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um die **SpeechInputHandler**-Komponente hinzuzufügen, und konfigurieren Sie sie dann wie folgt:

* **Deaktivieren** Sie das Kontrollkästchen **Is Focus Required** (Ist Fokus erforderlich), damit der Benutzer das Objekt nicht anblicken muss, um den Sprachbefehl mit der SpeechInputHandler-Komponente auszulösen
* Weisen Sie im Projektfenster das Prefab **SpeechConfirmation Tooltip** dem Feld **Speech Confirmation Tooltip Prefab** zu, damit dieses Prefab angezeigt wird, wenn ein Sprachbefehl erkannt wird

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-2.png)

Klicken Sie in der SpeechInputHandler-Komponente drei Mal auf das kleine **+** -Symbol, um drei Schlüsselwortelemente hinzuzufügen:

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-3.png)

Klappen Sie **Element 0** auf, und konfigurieren Sie es wie folgt:

* Geben Sie im Feld **Keyword** (Schlüsselwort) **Enable Indicator** (Indikator aktivieren) ein, um auf den Sprachbefehl „Enable Indicator“ (Indikator aktivieren) zu verweisen, den Sie im vorherigen Abschnitt erstellt haben
* Klicken Sie auf das kleine **+** -Symbol, um ein Ereignis hinzuzufügen
* Weisen Sie im Hierarchiefenster das **Indicator**-Objekt (Indikator) dem Feld **None (Object)** (Ohne (Objekt)) zu
* Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **GameObject** > **SetActive (bool)** aus, um diese Funktion als die beim Auslösen des Ereignisses auszuführende Aktion festzulegen
* Aktivieren Sie das Argumentkontrollkästchen, so dass es **aktiviert** ist

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-4.png)

Klappen Sie **Element 1** auf, und konfigurieren Sie es wie folgt:

* Geben Sie im Feld **Keyword** (Schlüsselwort) **Enable Bounding Box** (Begrenzungsrahmen aktivieren) ein, um auf den Sprachbefehl „Enable Bounding Box“ (Begrenzungsrahmen aktivieren) zu verweisen, den Sie im vorherigen Abschnitt erstellt haben
* Klicken Sie auf das kleine **+** -Symbol, um ein Ereignis hinzuzufügen
* Weisen Sie im Hierarchiefenster das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu
* Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **BoundingBox** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird
* Aktivieren Sie das Argumentkontrollkästchen, so dass es **aktiviert** ist
* Klicken Sie auf das kleine **+** -Symbol, um ein weiteres Ereignis hinzuzufügen
* Weisen Sie im Hierarchiefenster das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu
* Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **ObjectManipulator** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird
* Aktivieren Sie das Argumentkontrollkästchen, so dass es **aktiviert** ist

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-5.png)

Klappen Sie **Element 2** auf, und konfigurieren Sie es wie folgt:

* Geben Sie im Feld **Keyword** (Schlüsselwort) **Disable Bounding Box** (Begrenzungsrahmen deaktivieren) ein, um auf den Sprachbefehl „Disable Bounding Box“ (Begrenzungsrahmen deaktivieren) zu verweisen, den Sie im vorherigen Abschnitt erstellt haben
* Klicken Sie auf das kleine **+** -Symbol, um ein Ereignis hinzuzufügen
* Weisen Sie im Hierarchiefenster das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu
* Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **BoundingBox** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird
* Vergewissern Sie sich, dass das Argumentkontrollkästchen **deaktiviert** ist
* Klicken Sie auf das kleine **+** -Symbol, um ein weiteres Ereignis hinzuzufügen
* Weisen Sie im Hierarchiefenster das **RoverExplorer**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu
* Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **ObjectManipulator** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird
* Vergewissern Sie sich, dass das Argumentkontrollkästchen **deaktiviert** ist

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-6.png)

Wählen Sie im Hierarchiefenster das Objekt RoverExplorer > **RoverAssembly** aus, verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um die Komponente **SpeechInputHandler** hinzuzufügen, und konfigurieren Sie sie wie folgt:

* Vergewissern Sie sich, dass das Kontrollkästchen **Is Focus Required** (Ist Fokus erforderlich) **aktiviert** ist, damit der Benutzer das Objekt nicht anblicken muss, um den Sprachbefehl mit der SpeechInputHandler-Komponente, d. h. der RoverAssembly, auszulösen
* Weisen Sie im Projektfenster das Prefab **SpeechConfirmation Tooltip** dem Feld **Speech Confirmation Tooltip Prefab** zu, damit dieses Prefab angezeigt wird, wenn ein Sprachbefehl erkannt wird

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-7.png)

Klicken Sie in der SpeechInputHandler-Komponente auf das kleine **+** -Symbol, um ein Stichwortelement hinzuzufügen, klappen Sie das neu erstellte Element auf, und konfigurieren Sie es wie folgt:

* Geben Sie im Feld **Keyword** (Schlüsselwort) **Enable Tap to Place** (Zum Platzieren tippen aktivieren) ein, um auf den Sprachbefehl „Enable Tap to Place“ (Zum Platzieren tippen aktivieren) zu verweisen, den Sie im vorherigen Abschnitt erstellt haben
* Klicken Sie auf das kleine **+** -Symbol, um ein Ereignis hinzuzufügen
* Weisen Sie im Hierarchiefenster das Objekt selbst, d. h. das gleiche **RoverAssembly**-Objekt, dem Feld **None (Object)** (Ohne (Objekt)) zu
* Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **TapToPlace** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird
* Aktivieren Sie das Argumentkontrollkästchen, so dass es **aktiviert** ist

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie erfahren, wie Sie Sprachbefehle erstellen und diese global steuern. Außerdem haben Sie erfahren, wie Sie lokale Sprachbefehle steuern, die es erfordern, dass der Benutzer das Objekt ansieht, das den Sprachbefehl steuert.

Damit ist die Reihe der [Tutorials zu den ersten Schritten](mr-learning-base-01.md) zugleich abgeschlossen. Im Lauf dieser Tutorials haben Sie erfolgreich von Grund auf ein vollständiges Mixed Reality-Erlebnis mithilfe des MRTK erstellt.

In den beiden nächsten Tutorialreihen, den [Azure Spatial Anchors-Tutorials](mr-learning-asa-01.md) und den [Tutorials zu den Mehrbenutzerfunktionen](mr-learning-sharing-01.md), erfahren Sie zunächst, wie Sie Azure Spatial Anchors in Ihr Projekt integrieren, um das von Ihnen erstellte Rover Explorer-Erlebnis in der realen Welt zu verankern. Anschließend erfahren Sie, wie Sie Ihrem Projekt Mehrbenutzerfunktionen hinzufügen, um Benutzer- und Objektbewegungen in Echtzeit zu teilen.
