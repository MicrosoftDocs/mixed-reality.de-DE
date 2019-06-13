---
title: MR-Basislernmodul – Projektinitialisierung und erste Anwendung
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: c5490e6a3b542a5ca677b309e5ed1171f8666fe7
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "65814010"
---
# <a name="mr-learning-base-module---project-initialization-and-first-application"></a>MR-Basislernmodul – Projektinitialisierung und erste Anwendung

In dieser ersten Lektion lernen Sie einige der Funktionen kennen, die das Mixed Reality-Toolkit bietet, starten Ihre erste Anwendung für das HoloLens 2-Gerät und stellen sie auf dem Gerät bereit.

## <a name="objectives"></a>Ziele

* Optimieren von Unity für die HoloLens-Entwicklung
* Importieren von Assets und Einrichten der Szene
* Visualisierung des räumlichen Gitters, der Handgitter und des Frameratenzählers

## <a name="instructions"></a>Anweisungen

### <a name="create-new-unity-project"></a>Erstellen eines neuen Unity-Projekts

1. Starten Sie Unity.
2. Wählen Sie **Neu** aus.
![Lektion1 Kapitel1 Schritt2](images/Lesson1Chapter1Step2.JPG)
3. Geben Sie einen Projektnamen (z. B. „MixedRealityBase“) ein.
![Lektion1 Kapitel1 Schritt3](images/Lesson1Chapter1Step3.JPG)
4. Geben Sie einen Speicherort zum Speichern Ihres Projekts ein.
![Lektion1 Kapitel1 Schritt4](images/Lesson1Chapter1Step4.JPG)
5. Stellen Sie sicher, dass das Projekt auf **3D** festgelegt ist.
![Lektion1 Kapitel1 Schritt5](images/Lesson1Chapter1Step5.JPG)
6. Klicken Sie auf **Projekt erstellen**.
![Lektion1 Kapitel1 Schritt6](images/Lesson1Chapter1Step6.JPG)

### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Konfigurieren des Unity-Projekts für Windows Mixed Reality

1. Öffnen Sie das Fenster „Buildeinstellungen“, indem Sie zu „Datei“ > „Buildeinstellungen“ wechseln.
![Lektion1 Kapitel4 Schritt1](images/Lesson1Chapter4Step1.JPG)
2. Wechseln Sie zu „Universelle Windows-Plattform“, indem Sie „Universelle Windows-Plattform“ auswählen und dann auf die Schaltfläche „Plattform wechseln“ klicken, um die Plattform zu wechseln. Bei den auf HoloLens 2 ausgeführten Apps muss es sich um Apps für Universelle Windows-Plattform (UWP) handeln.
![Lektion1 Kapitel4 Schritt2](images/Lesson1Chapter4Step2.JPG)
3. Aktivieren Sie virtuelle Realität, indem Sie im Buildfenster auf „Player-Einstellungen“ klicken, und aktivieren Sie dann im Inspektorbereich unter „XR-Einstellungen“ das Kontrollkästchen für die VR-Unterstützung wie in der folgenden Abbildung gezeigt. Beachten Sie, dass Sie das Fenster „Buildeinstellungen“ möglicherweise verschieben oder minimieren müssen, um den Inspektorbereich sehen zu können. Das Kontrollkästchen für die VR-Unterstützung gilt auch für Mixed Reality-/AR-Headsets, weil sich dies auf die Aktivierung der stereoskopischen Funktion (Rendering unterschiedlicher Bilder für jedes Auge) bezieht. ![Lektion1 Kapitel4 Schritt3](images/Lesson1Chapter4Step3.JPG)
4. Vergewissern Sie sich im gleichen Inspektorbereich, dass unter „Veröffentlichungseinstellungen“ im Abschnitt „Funktionen“ das Kontrollkästchen „Räumliche Wahrnehmung“ aktiviert ist. Die Funktion „Räumliche Wahrnehmung“ ermöglicht das Visualisieren des räumlichen Zuordnungsgitters auf einem Mixed Reality-Gerät wie HoloLens 2. Sie finden die Veröffentlichungseinstellungen im Inspektorbereich über „XR-Einstellungen“ und unter „Andere Einstellungen“.
![Lektion1 Kapitel4 Schritt4](images/Lesson1Chapter4Step4.JPG)

> HINWEIS: Obwohl in diesem Abschnitt nicht verwendet, können Sie einige weitere allgemeine Funktionen aktivieren, wie z. B. „Mikrofon“ (für Sprachbefehle) und „InternetClient“ (für das Herstellen einer Verbindung mit Diensten, die eine Netzwerkverbindung erfordern).

### <a name="import-the-mixed-reality-toolkit"></a>Importieren des Mixed Reality-Toolkits

1. Laden Sie das Unity-Paket [Mixed Reality-Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage) herunter, und speichern Sie es in einem Ordner auf Ihrem PC.

2. Importieren Sie das Mixed Reality-Toolkit-Paket, indem Sie auf „Assets“ > „Importieren“ > „Benutzerdefiniertes Paket“ klicken. Suchen Sie nach dem in Schritt 1 heruntergeladenen Mixed Reality-Toolkit-Paket, und öffnen Sie es, um den Importvorgang zu starten. Warten Sie einige Minuten, bis der Importvorgang startet.
    ![Lektion1 Kapitel2 Schritt2a](images/Lesson1Chapter2Step2a.JPG) ![Lektion1 Kapitel2 Schritt2b](images/Lesson1Chapter2Step2b.JPG)

3. Klicken Sie im nächsten Popupfenster auf „Importieren“, um mit dem Importieren des Mixed Reality-Toolkits zu beginnen. Stellen Sie sicher, dass alle Elemente aktiviert sind, wie in der Abbildung dargestellt. Wenn ein Popupdialogfeld angezeigt wird, in dem Sie gefragt werden, ob die Standardeinstellungen des Mixed Reality-Toolkits übernommen werden sollen, klicken Sie auf „Übernehmen“.
    ![Lektion1 Kapitel2 Schritt3](images/Lesson1Chapter2Step3.JPG) ![Lektion1 Kapitel2 Schritt3](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Konfigurieren des Mixed Reality-Toolkits

1. Konfigurieren Sie das Mixed Reality-Toolkit, indem Sie auf der Menüleiste die Optionen „Mixed Reality-Toolkit“ > „Konfigurieren“ auswählen. Wenn dieses Menüelement nach dem Importieren des Mixed Reality-Toolkits nicht angezeigt wird, starten Sie Unity neu.
![Lektion1 Kapitel3 Schritt1](images/Lesson1Chapter3Step1.JPG)
2. Die Szene enthält jetzt mehrere neue Elemente und Änderungen aus dem Mixed Reality-Toolkit. Speichern Sie Ihre Szene unter einem anderen Namen, indem Sie auf „Datei“ > „Speichern unter“ klicken und der Szene einen Namen (z. B. „BaseScene“) zuweisen. Organisieren Sie Ihre Szene, indem Sie sie im Ordner „Szenen“ speichern, der sich im Ordner „Assets“ Ihres Projekts befindet.
![Lektion1 Kapitel3 Schritt2a](images/Lesson1Chapter3Step2a.JPG)
![Lektion1 Kapitel3 Schritt2b](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>Erstellen Ihrer Anwendung auf Ihrem Gerät

1. Wenn Sie das Fenster „Buildeinstellungen“ aus den vorherigen Abschnitten geschlossen haben, öffnen Sie das Fenster „Buildeinstellungen“ erneut, indem Sie zu „Datei“ > „Buildeinstellungen“ wechseln.
    ![Lektion1 Kapitel5 Schritt1](images/Lesson1Chapter5Step1.JPG)

2. Stellen Sie sicher, dass die Szene, die Sie testen möchten, in der Liste „Szenen in Build“ enthalten ist, indem Sie auf die Schaltfläche „Offene Szenen hinzufügen“ klicken.

3. Klicken Sie auf die Schaltfläche „Erstellen“, um den Buildprozess zu starten.
    ![Lektion1 Kapitel5 Schritt3](images/Lesson1Chapter5Step3.JPG)

4. Erstellen und benennen Sie einen neuen Ordner für Ihre Anwendung. In der folgenden Abbildung können Sie sehen, dass ein Ordner mit dem Namen „App“ erstellt wurde, der die Anwendung enthalten soll. Klicken Sie auf „Ordner auswählen“, um mit der Erstellung im neu erstellten Ordner zu beginnen. Nach Abschluss der Erstellung (des Buildvorgangs) können Sie in Unity das Fenster „Buildeinstellungen“ schließen. 
    ![Lektion1 Kapitel5 Schritt4](images/Lesson1Chapter5Step4.JPG)

  > HINWEIS: Wenn der Vorgang fehlschlägt, wiederholen Sie den Buildvorgang, oder starten Sie Unity neu, und wiederholen Sie dann den Buildvorgang. Wenn eine Fehlermeldung wie „Fehler: CS0246 = Der Typ- oder Namespacename "XX" konnte nicht gefunden werden. (Fehlt eine Using-Direktive oder ein Assemblyverweis?)“ angezeigt wird, müssen Sie möglicherweise [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) installieren.
  >

5. Öffnen Sie nach Abschluss des Buildvorgangs den neu erstellten Ordner, der Ihre neu erstellten Anwendungsdateien enthält. Doppelklicken Sie auf die Projektmappe „MixedRealityBase.sln“ (oder auf den entsprechenden Namen, wenn Sie einen alternativen Namen für Ihr Projekt verwendet haben), um die Projektmappendatei in Visual Studio zu öffnen.

  > Hinweis: Achten Sie darauf, dass Sie den neu erstellten Ordner öffnen (also den Ordner „App“, wenn Sie die Namenskonventionen in den vorherigen Schritten befolgt haben), weil außerhalb dieses Ordners noch eine SLN-Datei mit einem ähnlichen Namen vorhanden ist, die nicht mit der SLN-Datei im Buildordner verwechselt werden darf. 

![Lektion1 Kapitel5 Schritt5](images/Lesson1Chapter5Step5.JPG)

  > Hinweis: Wenn Sie von Visual Studio zur Installation neuer Komponenten aufgefordert werden, nehmen Sie sich einen Moment Zeit, um zu überprüfen, ob alle erforderlichen Komponenten (wie auf der Seite [Installieren der Tools](install-the-tools.md) angegeben) installiert sind.

6. Schließen Sie das HoloLens 2-Gerät über das USB-Kabel an Ihren PC an. Bei diesen Lektionsanweisungen wird davon ausgegangen, dass Sie einen Test mit einem HoloLens 2-Gerät bereitstellen. Sie können die Bereitstellung aber auch auf dem [HoloLens 2-Emulator](using-the-hololens-emulator.md) vornehmen oder ein [App-Paket für das Querladen](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>) erstellen.

7. Stellen Sie vor dem Erstellen der App auf Ihrem Gerät sicher, dass sich das Gerät im Entwicklermodus befindet. Wenn das Ihre erste Bereitstellung auf dem HoloLens 2-Gerät ist, werden Sie möglicherweise von Visual Studio aufgefordert, Ihr HoloLens 2-Gerät mit einer PIN zu koppeln. Folgen Sie [diesen Anweisungen](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio), wenn Sie den Entwicklermodus aktivieren oder das Gerät mit Visual Studio koppeln müssen.

8. Konfigurieren Sie Visual Studio für die Erstellung auf Ihrem HoloLens 2-Gerät, indem Sie die Konfiguration „Release“ und die Architektur „ARM“ auswählen.
    ![Lektion1 Kapitel5 Schritt8](images/Lesson1Chapter5Step8.JPG)

9. Der letzte Schritt ist die Erstellung auf Ihrem Gerät durch Auswählen von „Debuggen“ > „Starten ohne Debuggen“. Wenn Sie „Starten ohne Debuggen" auswählen, wird die Anwendung sofort nach einem erfolgreichen Buildvorgang auf Ihrem Gerät gestartet, ohne dass jedoch Debuginformationen in Visual Studio angezeigt werden. Dies bedeutet auch, dass Sie das USB-Kabel entfernen können, während Ihre Anwendung auf Ihrem HoloLens 2-Gerät ausgeführt wird, ohne dass die Anwendung beendet wird. Sie können auch „Build“ > „Projektmappe bereitstellen“ auswählen, um die Anwendung auf Ihrem Gerät bereitzustellen, ohne dass sie automatisch gestartet wird.
    ![Lektion1 Kapitel5 Schritt9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben jetzt Ihre erste HoloLens 2-Anwendung bereitgestellt. Während Sie herumlaufen, sollten Sie ein räumliches Gitter sehen, das alle Oberflächen bedeckt, die vom HoloLens 2-Gerät erkannt wurden. Darüber hinaus sollten Sie Indikatoren auf Ihren Händen und Fingern für die Handverfolgung und einen Frameratenzähler zum Überwachen der App-Leistung sehen. Dies sind nur einige der grundlegenden Elemente, die standardmäßig im Mixed Reality-Toolkit enthalten sind. In den folgenden Lektionen fügen Sie Ihrer Szene mehr Inhalte und Interaktivität hinzu, sodass Sie alle Funktionen des HoloLens 2-Geräts und des Mixed Reality-Toolkits umfassend erkunden können.

>Hinweis: Wie Sie den Frameratenzähler mithilfe eines Sprachbefehls umschalten, erfahren Sie in [Lektion 5](mrlearning-base-ch5.md).

[Nächste Lektion: Benutzeroberfläche, Handverfolgung und Konfiguration des Mixed Reality-Toolkits](mrlearning-base-ch2.md)
