---
title: Tutorials zu Holographic Remoting am PC – 1. Erste Schritte mit Holographic Remoting am PC
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie Mixed Reality Remoting von Ihrem PC zu HoloLens 2 ausführen.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/19/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: cbbad9548abeb1b8392b99d187b5b051d5b4ddd4
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305780"
---
# <a name="1-getting-started-with-pc-holographic-remoting"></a>1. Erste Schritte mit Holographic Remoting am PC

## <a name="overview"></a>Übersicht

  Willkommen bei den HoloLens 2-Tutorials. In dieser zweiteiligen Tutorialreihe erfahren Sie, wie Sie eine Mixed Reality-Demo und eine PC-App für Holographic Remoting erstellen.

   In diesem Tutorial, [Erstellen einer Mixed Reality-Erfahrung](mr-learning-pc-holographic-remoting-01.md), erfahren Sie, wie Sie eine Mixed Reality-Erfahrung erstellen können. Es werden Benutzeroberflächenelemente, 3D-Modellbearbeitung, Modellclipping und Funktionen für Eye-Tracking veranschaulicht.

  Im zweiten Tutorial, [Erstellen einer Holographic Remoting-Anwendung](mr-learning-pc-holographic-remoting-02.md), erfahren Sie, wie Sie eine PC-App für Holographic Remoting erstellen. Stellen Sie jederzeit eine Verbindung mit HoloLens 2 her, um 3D-Inhalte in Mixed Reality visuell darzustellen.

## <a name="objectives"></a>Ziele

* Importieren von Assets und Einrichten der Szene
* Interagieren mit Hologrammen über Elemente und Schaltflächen der Benutzeroberfläche
* Konfigurieren von 3D-Objekten für das Clippingfeature
* Weitere Informationen zum Aktivieren von QuickInfos mit Eye-Tracking

## <a name="prerequisites"></a>Voraussetzungen

* Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](install-the-tools.md) ist
* Gundkenntnisse der C#-Programmierung
* Ein für die [Entwicklung konfiguriertes](using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.3.X und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform

>[UNBEDINGT EMPFOHLEN!] Durchgearbeitete Tutorialserie „Erste Schritte“ oder vorherige grundlegende Erfahrung mit Unity und MRTK

> [!IMPORTANT]
> Die empfohlene Unity-Version für diese Tutorialserie ist Unity 2019.3.X. Sie ersetzt alle Anforderungen oder Empfehlungen bezüglich der Unity-Version, die in den oben verknüpften Voraussetzungen genannt werden.

## <a name="creating-and-preparing-the-unity-project"></a>Erstellen und Vorbereiten des Unity-Projekts

In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die MRTK-Entwicklung vor.

Befolgen Sie zu diesem Zweck zunächst die Anweisungen unter [Initialisieren des Projekts und der ersten Anwendung](mr-learning-base-02.md), jedoch ohne die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihrem Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2), die die folgenden Schritte beinhalten:

1. [Erstellen eines neuen Unity-Projekts](mr-learning-base-02.md#creating-the-unity-project), das mit einem passenden Namen bezeichnet wird, beispielsweise *MRTK-Tutorials*

1. [Wechseln der Buildplattform](mr-learning-base-02.md#configuring-the-unity-project)

1. [Importieren der TextMeshPro Essential-Ressourcen](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [Importieren des Mixed Reality-Toolkits](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [Konfigurieren des Unity-Projekts](mr-learning-base-02.md#configuring-the-unity-project)

1. [Erstellen und Festlegen der Szene](mr-learning-base-02.md#creating-and-configuring-the-scene) und Bezeichnen der Szene mit einem passenden Namen, z. B. **PC Holographic Remoting**

Befolgen Sie dann die Anweisungen unter [Ändern der Anzeigeoption der räumlichen Wahrnehmung](mr-learning-base-03.md#changing-the-spatial-awareness-display-option), um das **DefaultHoloLens2ConfigurationProfile** als MRTK-Konfigurationsprofil für Ihre Szene festzulegen. Legen Sie die Anzeigeoptionen für das Gittermodell für räumliche Wahrnehmung auf **Occlusion** (Verdeckung) fest.

## <a name="importing-the-tutorial-assets"></a>Importieren der Tutorialressourcen

Laden Sie [MRTK.Tutorials.PCHolographicRemoting.unitypackage](https://github.com/onginnovations/MixedRealityLearning/releases/download/pc-holographic-remoting-v2.4.0.0/MRTK.Tutorials.PCHolographicRemoting.unitypackage) herunter, und **importieren** Sie das Paket.

>[!TIP]
> Wenn Sie eine Auffrischung zum Importieren eines benutzerdefinierten Unity-Pakets benötigen, lesen Sie die Anweisungen unter [Importieren des Mixed Reality-Toolkits](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

Nach dem Importieren der Tutorialressourcen sollte Ihr Projektfenster ähnlich wie die folgende Abbildung aussehen:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section2-Step1-1.png)

## <a name="configuring-and-preparing-the-scene"></a>Konfigurieren und Vorbereiten der Szene

In diesem Abschnitt bereiten Sie die Szene vor, indem Sie einige der Tutorial-Prefabs hinzufügen.

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs**. Klicken Sie mit gedrückter STRG-Taste auf die folgenden sechs Prefabs.

* ButtonParent
* ClippingObjects
* HandSpatialMapButton
* Anweisungen
* ModelParent
* Platform

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-1.png)

Ziehen Sie diese Modelle mithilfe von Drag & Drop aus dem Ordner „prefabs“ in das **Hierarchiefenster**.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-2.png)

Um sich auf die Objekte in der Szene zu konzentrieren, können Sie auf das **ModelParent**-Objekt doppelklicken und die Ansicht dann etwas verkleinern:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-3.png)

> [!TIP]
> Wenn Sie die großen Symbole in Ihrer Szene, beispielsweise die mit großen Rahmen umgebenen 'T'-Symbole, irritierend finden, können Sie diese ausblenden, indem Sie <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">die Gizmos umschalten</a> (in die Position „Aus“).

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Konfigurieren der Schaltflächen zum Betreiben der Szene

In diesem Abschnitt fügen Sie in der Szene Skripts hinzu, um Schaltflächenereignisse zu erstellen, die die Grundlagen von Modellwechsel und Clippingfunktionalität veranschaulichen.

### <a name="1-configuring-the-interactable-script-component"></a>1. Konfigurieren der Komponente „Interactable (Script)“

Klappen Sie im Hierarchiefenster das **ButtonParent**-Objekt auf, und wählen Sie dann **NextButton** aus. Suchen Sie im Inspektor-Fenster nach der Komponente **Interactable (Script)** , und klicken Sie unter dem **OnClick ()** -Ereignis auf das Symbol **+** .

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-1.png)

Klicken Sie bei immer noch im Hierarchiefenster ausgewähltem **NextButton**-Objekt auf das **ButtonParent**-Objekt, und ziehen Sie es auf das leere **None (Object)** -Feld des Ereignislisteners, den Sie soeben hinzugefügt haben, um das ButtonParent-Objekt auf Geklickt-Ereignissen für diese Schaltfläche lauschen zu lassen:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-2.png)

Klicken Sie auf die Dropdownliste **No Function** des gleichen Ereignisses. Wählen Sie dann **ViewButtonControl** > **NextModel ()** aus, um die **NextModel ()** -Funktion als die Aktion festzulegen, die ausgelöst wird, wenn das Ereignis „Schaltfläche gedrückt“ von dieser Schaltfläche ausgelöst wird:

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-3.png)

### <a name="2-configuring-the-remaining-buttons"></a>2. Konfigurieren der verbleibenden Schaltflächen

Führen Sie für jede der verbleibenden Schaltflächen den oben beschriebenen Vorgang aus, um den **OnClick ()** -Ereignissen Funktionen zuzuweisen:

* Weisen Sie für das PreviousButton-Objekt die Funktion **ViewButtonControl**l > **PreviousModel ()** zu.

* Wählen Sie für ClippingButton die Funktion **ToggleButton** > **ToggleClipping ()** aus.

### <a name="3-configuring-the-view-button-control-script--and-toggle-button-script-components"></a>3. Konfigurieren der Komponenten „View Button Control (Script)“ und „Toggle Button (Script)“

Nun sind Ihre Schaltflächen so konfiguriert, dass Sie die Modellwechsel- und Clippingfunktionen veranschaulichen können. Es ist an der Zeit, dem Skript 3D-Modelle und die Clippingobjekte hinzuzufügen.

Wir haben sechs verschiedene 3D-Modelle zur Demonstrationszwecken bereitgestellt. Erweitern Sie das ***ModelParentobject***, um diese 3D-Modelle anzuzeigen.

Während das ButtonParent-Objekt weiterhin im Hierarchiefenster ausgewählt ist, suchen Sie im Inspektor-Fenster nach der Komponente **View Button Control (Script)** , und erweitern Sie die Variable **Models**.

Geben Sie im Feld **Size** (Größe) die Anzahl der 3D-Modelle ein, die Sie in Ihrer Szene verwenden möchten. In diesem Fall sind es sechs Modelle. Es werden Felder zum Hinzufügen neuer 3D-Modelle erstellt.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-1.png)

Verschieben Sie jedes untergeordnete Objekt des ModelParent-Objekts mithilfe von Drag & Drop in diese Felder.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-2.png)

Ziehen Sie das **ClippingObjects**-Objekt mithilfe von Drag & Drop aus dem Hierarchiefenster in das Feld **Clipping Object** der Komponente **Toggle Button (Script)** .
>[!NOTE]
>Bleiben Sie die ganze Zeit ausschließlich im übergeordneten Objekt der Schaltfläche.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-3.png)

Wählen Sie im Hierarchiefenster das Prefab **ClippingObjects** aus, und aktivieren Sie es im Inspektor-Fenster, um die Clippingobjekte zu aktivieren.

## <a name="configuring-the-clipping-objects-to-enable-clipping-feature"></a>Konfigurieren der Clippingobjekte, um das Clippingfeature zu aktivieren

In diesem Abschnitt fügen Sie den Renderer für untergeordnete Objekte des MarsCuriosityRover-Objekts einem einzelnen Clippingobjekt hinzu, um das Clipping des MarsCuriosityRover-Modells zu veranschaulichen.

Erweitern Sie im Hierarchiefenster das **ClippingObjects**-Objekt, um die drei unterschiedlichen Clippingobjekte verfügbar zu machen, die Sie in diesem Projekt verwenden.

Um das **ClippingSphere**-Objekt zu konfigurieren, klicken Sie darauf, und suchen Sie dann im Inspektor-Fenster nach der Komponente **Clipping Sphere (Script)** . Geben Sie die Anzahl der Renderer, die Sie für das 3D-Modell hinzufügen müssen, in das Größenfeld ein. Fügen Sie in diesem Fall 10 Renderer für untergeordnete MarsCuriosityRover-Objekte hinzu. Er werden Felder zum Hinzufügen von Renderern erstellt. Ziehen Sie untergeordnete Modellobjekte des MarsCuriosityRover-Objekts mithilfe von Drag & Drop in diese Felder.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section5-Step1-1.png)

Führen Sie den gleichen Vorgang aus, und fügen Sie den **ClippingBox**- und **ClippingPlane**-Objekten Renderer für untergeordnete Objekte von MarsCuriosityRover hinzu.

In diesem Tutorial wird nur das MarsCuriosityRover-Modell verwendet, um das Clippingfeature zu demonstrieren. Es wurden Clippingfeatures zu weiteren Modellen hinzugefügt, die Größe des Renderers wurde vergrößert, und es wurden individuelle Gittermodellrenderer hinzugefügt.

## <a name="configuring-eye-tracking-to-highlight-tooltips"></a>Konfigurieren von Eye-Tracking zum Hervorheben von QuickInfos

In diesem Abschnitt wird erläutert, wie Sie Eye-Tracking in Ihrem Projekt aktivieren. Beispielsweise implementieren Sie eine Funktionalität zum Hervorheben von QuickInfos, die an die Teile von MarsCuriosityRover angefügt sind, während Sie sich diese ansehen. Sie werden ausgeblendet, wenn Sie sie nicht mehr ansehen.

### <a name="1-identify-target-objects-and-associated-tooltips"></a>1. Identifizieren Sie Zielobjekte und zugehörige QuickInfos.

Wählen Sie im Hierarchiefenster das ModelParent-Objekt aus. Erweitern Sie ***MarsCuriosity > Rover***, um fünf Hauptbestandteile von MarsCuriosityRover zu ermitteln: **POI-Camera**, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer**, **POI-RUHF Antenna**.

* Beachten Sie die fünf entsprechenden QuickInfo-Objekte, die mit MarsCuriosityRover-Teilen im Hierarchiefenster verknüpft sind. 
* Sie konfigurieren diese Objekte so, dass sie hervorgehoben werden, wenn Sie sich die MarsCuriosityRover-Teile ansehen.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step1-1.png)

### <a name="2-implement-while-looking-at-target-----on-look-away--events"></a>2. Implementierung von While Looking At Target ()- und On Look Away ()-Ereignissen

Wählen Sie im Hierarchiefenster das ***POI-Camera***-Objekt aus. Suchen Sie im Inspektor-Fenster nach der Komponente **Eye Tracking Target (Script)** , und konfigurieren Sie die **While Looking At Target ()**  & **On Look Away ()** -Ereignisse wie folgt:

* Weisen Sie dem Feld **None (Object)** das **POI-Camera ToolTip**-Objekt zu.
* Wählen Sie in der Dropdownliste **No Function** des **While Looking At Target ()** -Ereignisses **GameObject** > **SetActive (bool)** aus. Aktivieren Sie das **Kontrollkästchen** darunter, um die QuickInfo als Aktion hervorzuheben, die ausgelöst wird, wenn Sie das Zielobjekt betrachten.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-1.png)

* Führen Sie den gleichen Vorgang aus, und klicken Sie auf die Dropdownliste **No Function** des **On Look Away ()** -Ereignislisteners. Wählen Sie dann **GameObject** > **SetActive(bool**) aus, und lassen Sie das **Kontrollkästchen** leer, um die QuickInfo als Aktion auszublenden, die ausgelöst wird, wenn Sie vom Zielobjekt wegschauen.

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-2.png)

Führen Sie den gleichen Vorgang aus, und weisen Sie entsprechende QuickInfo-Objekte denselben **MarsCuriosityRover**-Teilen für **While Looking At Target ()**  & **On Look Away ()** -Ereignisse zu.

Um Eye-Tracking zu aktivieren, befolgen Sie diese [Richtlinien](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, eine Mixed Reality-Erfahrung zu entwickeln, die Benutzeroberflächenelemente, 3D-Modellbearbeitung, Modellclipping und Funktionen für Eye-Tracking zeigt. In diesem Tutorial wurden NextButton und PreviousButton vorgestellt, mit denen Sie die Erfahrung des 3D-Modellbetrachters untersuchen können. Mit ClippingObjectButton haben Sie die Möglichkeit, Clippingobjekte zu aktivieren und das Clippingfeature zu erleben. Das Tutorial hat Ihnen auch ein Element für Eye-Tracking vorgestellt, mit dem Sie die QuickInfos in der Darstellung hervorheben können.

In der nächsten Lektion erfahren Sie, wie Sie eine Anwendung für Holographic Remoting für den PC erstellen, um HoloLens 2 zu einem beliebigen Zeitpunkt zu verbinden. Auf diese Weise können Sie 3D-Inhalte in Mixed Reality visualisieren.

[Nächste Lektion: 2. Erstellen einer Anwendung für Holographic Remoting](mr-learning-pc-holographic-remoting-02.md)
