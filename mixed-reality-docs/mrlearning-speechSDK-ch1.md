---
title: 'Tutorials zu Azure Speech-Diensten: 1 Integrieren und Verwenden von Spracherkennung und Transkription'
description: In diesem Kurs erfahren Sie, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: a72eb808adbc14df65c55e694ea985d97f9ec24c
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79032475"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1. Integrieren und Verwenden von Spracherkennung und Transkription

## <a name="overview"></a>Übersicht


In dieser Tutorialreihe erstellen Sie eine Mixed Reality-Anwendung, die die Verwendung von Azure Speech Services mit der HoloLens 2 untersucht. Wenn Sie diese Tutorialreihe durcharbeiten, können Sie das Mikrofon Ihres Geräts verwenden, um Spracheingaben in Echtzeit in Text zu übertragen, Ihre Sprache in andere Sprachen zu übersetzen und die Funktion zur Absichtserkennung nutzen, um Sprachbefehle mithilfe von künstlicher Intelligenz zu verstehen.

## <a name="objectives"></a>Ziele

* Lernen, wie sich die Azure Speech Services in eine HoloLens 2-Anwendung integrieren lassen
* Lernen, wie die Spracherkennung zum Umwandeln in Text verwendet werden kann

## <a name="prerequisites"></a>Voraussetzungen

>[!TIP]
>Wenn Sie die Reihe [Tutorials zu den ersten Schritten](mrlearning-base.md) noch nicht abgeschlossen haben, empfiehlt es sich, zunächst diese Tutorials abzuschließen.

* Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](install-the-tools.md) ist
* Windows 10 SDK (10.0.18362.0 oder höher)
* Grundlagenkenntnisse in der C#-Programmierung
* Ein für die [Entwicklung konfiguriertes](using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.2.X und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform

> [!IMPORTANT]
> Die empfohlene Unity-Version für diese Tutorialreihe ist Unity 2019.2.X. Diese übertrifft alle Versionsanforderungen oder -empfehlungen, die in den oben verlinkten Voraussetzungen angegeben sind.

## <a name="creating-and-preparing-the-unity-project"></a>Erstellen und Vorbereiten des Unity-Projekts

In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die MRTK-Entwicklung vor.

Befolgen Sie zu diesem Zweck zunächst die Anweisungen unter [Initialisieren des Projekts und der ersten Anwendung](mrlearning-base-ch1.md), jedoch ohne die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihrem Gerät](mrlearning-base-ch1.md#build-your-application-to-your-device), die die folgenden Schritte beinhalten:

1. [Erstellen eines neuen Unity-Projekts](mrlearning-base-ch1.md#create-new-unity-project), das mit einem passenden Namen bezeichnet wird, beispielsweise *MRTK-Tutorials*

2. [Konfigurieren des Unity-Projekts für Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [Importieren von TextMesh Pro Essential-Ressourcen](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [Importieren des Mixed Reality-Toolkits](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [Konfigurieren des Unity-Projekts für das Mixed Reality-Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. [Hinzufügen des Mixed Reality-Toolkits zur Unity-Szene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit), die dann einen passenden Namen erhält, beispielsweise *AzureSpeechServices*

Befolgen Sie dann die Anweisungen unter [Konfigurieren der Mixed Reality-Toolkitprofile (Option zum Ändern der Anzeige der räumlichen Wahrnehmung)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option), um als MRTK-Konfigurationsprofil für Ihre Szene das **DefaultHoloLens2ConfigurationProfile** festzulegen, und ändern Sie die Anzeigeoptionen für das Gittermodell zur räumlichen Wahrnehmung in **Occlusion** (Verdeckung).

> [!CAUTION]
> Wie bereits in den oben verlinkten Anweisungen zum [Konfigurieren des Unity-Projekts für das Mixed Reality-Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) erwähnt, wird dringend empfohlen, MSBuild for Unity nicht zu aktivieren.

## <a name="configuring-the-speech-commands-start-behavior"></a>Konfigurieren des Startverhaltens der Sprachbefehle

Da Sie das Speech SDK für die Spracherkennung und -Transkription verwenden, müssen Sie die MRTK-Sprachbefehle so konfigurieren, dass sie die Funktionalität des Speech SDKs nicht beeinträchtigen. Um dies zu erreichen, können Sie das Startverhalten der Sprachbefehle vom automatischen Start auf manuellen Start umstellen.

Wählen Sie bei im Hierarchiefenster ausgewähltem **MixedRealityToolkit**-Objekt im Inspektorfenster die Registerkarte**Input** (Eingabe) aus, klonen Sie das **DefaultHoloLens2InputSystemProfile** und das **DefaultMixedRealitySpeechCommandsProfile**, und ändern Sie dann die Sprachbefehle **Start Behavior** (Startverhalten) in **Manual Start** (Manueller Start):

![mrlearning-speech](images/mrlearning-speech/tutorial1-section2-step1-1.png)

> [!TIP]
> Wenn Sie eine Auffrischung zum Klonen und Konfigurieren von MRTK-Profilen benötigen, lesen Sie die Anweisungen in [Konfigurieren der Mixed Reality-Toolkitprofile (Option zum Ändern der Anzeige der räumlichen Wahrnehmung)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option).

## <a name="configuring-the-capabilities"></a>Konfigurieren der Funktionen

Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen) aus, um das Fenster mit den Player-Einstellungen zu öffnen, und suchen Sie dann den Abschnitt **Player** >  **Publishing Settings** (Player > Veröffentlichungseinstellungen):

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-1.png)

Scrollen Sie in den **Publishing Settings** nach unten zum Abschnitt **Capabilities** (Funktionen), und vergewissern Sie sich, dass die Funktionen **InternetClient**, **Microphone** und **SpatialPerception**, die Sie im Rahmen der Erstellung des Projekts zu Beginn des Tutorials erstellt haben, aktiviert sind. Aktivieren Sie dann die Funktionen **InternetClientServer** und **PrivateNetworkClientServer**:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Importieren der Tutorialressourcen

Laden Sie die folgenden benutzerdefinierten Unity-Pakete herunter, und **importieren** Sie sie **in der Reihenfolge, in der sie aufgelistet sind**:

* [Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (latest version)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-speech-services-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage)

> [!TIP]
> Wenn Sie eine Auffrischung zum Importieren eines benutzerdefinierten Unity-Pakets benötigen, lesen Sie die Anweisungen unter [Importieren des Mixed Reality-Toolkits](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

Nach dem Importieren der Tutorialressourcen sollte Ihr Projektfenster ähnlich wie die folgende Abbildung aussehen:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section4-step1-1.png)

## <a name="preparing-the-scene"></a>Vorbereiten der Szene

In diesem Abschnitt bereiten Sie die Szene vor, indem Sie das Prefab für das Tutorial hinzufügen und die Komponente „Lunarcom Controller (Skript)“ konfigurieren, um Ihre Szene zu steuern.

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs**, und ziehen Sie das **Lunarcom**-Prefab auf das Hierarchiefenster, um es Ihrer Szene hinzuzufügen:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-1.png)

Verwenden Sie bei im Hierarchiefenster ausgewähltem **Lunarcom**-Objekt im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um die Komponente **Lunarcom Controller (Script)** zum Lunarcom-Objekt hinzuzufügen:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> Die Komponente „Lunarcom Controller (Script)“ ist kein Bestandteil des MRTK. Sie wurde zusammen mit den Ressourcen für dieses Tutorial zur Verfügung gestellt.

Klappen Sie das noch ausgewählte **Lunarcom**-Objekt auf, um seine untergeordneten Objekte anzuzeigen, und ziehen Sie dann das **Terminal**-Objekt auf das **Terminal**-Feld der Lunarcom Controller (Script)-Komponente:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-3.png)

Klappen Sie bei noch ausgewähltem **Lunarcom**-Objekt das Terminal-Objekt auf, um seine untergeordneten Objekte anzuzeigen, ziehen Sie dann das **ConnectionLight**-Objekt auf das **ConnectionLight**-Feld der Lunarcom Controller (Script)-Komponente und das **OutputText**-Objekt auf das **Output Text**-Feld:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-4.png)

Klappen Sie bei noch ausgewähltem **Lunarcom**-Objekt das Buttons-Objekt auf, um seine untergeordneten Objekte anzuzeigen, und klappen Sie dann im Inspektorfenster die **Buttons**-Liste auf, legen Sie seine **Size** (Größe) auf 3 fest, und ziehen Sie die Objekte **MicButton**, **SatelliteButton** und **RocketButton** auf die **Element**-Felder 0, 1 bzw. 2:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a>Verbinden des Unity-Projekts mit der Azure-Ressource

Um Azure Speech Services zu verwenden, müssen Sie eine Azure-Ressource erstellen und einen API-Schlüssel für den Speech Service abrufen. Befolgen Sie die Anweisungen unter [Speech Service kostenlos testen](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started), und notieren Sie sich Ihre Dienstregion (auch als Standort bezeichnet) und den API-Schlüssel (auch als Schlüssel1 oder Schlüssel2 bezeichnet).

Wählen Sie in Ihrem Hierarchiefenster das **Lunarcom**-Objekt aus, suchen Sie dann im Inspektorfenster den Abschnitt **Speech SDK Credentials** der **Lunarcom Controller (Script)** -Komponente, und konfigurieren Sie ihn wie folgt:

* Geben Sie im Feld **Speech Service API Key** Ihren API-Schlüssel (Schlüssel1 oder Schlüssel2) ein
* Geben Sie im Feld **Speech Service Region** Ihre Dienstregion (Standort) ein. Verwenden Sie dazu Kleinbuchstaben, und entfernen Sie alle Leerzeichen.

![mrlearning-speech](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a>Verwenden der Spracherkennung zum Transkribieren von Sprache

Wählen Sie im Hierarchiefenster das **Lunarcom**-Objekt aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um dem Lunarcom-Objekt die Komponente **Lunarcom Speech Recognizer (Script)** hinzuzufügen:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> Die Komponente „Lunarcom Speech Recognizer (Script)“ ist kein Bestandteil des MRTK. Sie wurde zusammen mit den Ressourcen für dieses Tutorial zur Verfügung gestellt.

Wenn Sie jetzt in den Spielmodus wechseln, können Sie die Spracherkennung testen, indem Sie zuerst auf die Mikrofonschaltfläche klicken.

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-2.png)

Falls Ihr Computer über ein Mikrofon verfügt, wird Ihre Sprache dann, wenn Sie etwas sagen, im Terminalbereich transkribiert:

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-3.png)


> [!CAUTION]
> Die Anwendung muss eine Verbindung mit Azure herstellen, achten Sie also darauf, dass Ihr Computer/Gerät mit dem Internet verbunden ist.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben die von Azure unterstützte Spracherkennung implementiert. Führen Sie die Anwendung auf Ihrem Gerät aus, um sicherzustellen, dass das Feature ordnungsgemäß funktioniert.

Im nächsten Tutorial erfahren Sie, wie Sie Befehle mit der Azure-Spracherkennung ausführen.

[Nächstes Tutorial: 2. Verwenden der Spracherkennung zum Ausführen von Befehlen](mrlearning-speechSDK-ch2.md)
