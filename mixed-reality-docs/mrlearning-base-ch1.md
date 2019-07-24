---
title: MR-Basislernmodul – Projektinitialisierung und erste Anwendung
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 51cfc123f7da8d25a53eecfb730f60cf10fe7377
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387786"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Initialisieren Ihres Projekts und der ersten Anwendung

In dieser ersten Lektion erfahren Sie mehr über einige der Funktionen, die das Mixed Reality Toolkit (mrtk) anbieten muss, starten Sie Ihre erste Anwendung für die hololens 2, und stellen Sie Sie auf dem Gerät bereit.

## <a name="objectives"></a>Ziele

* Optimieren von Unity für die HoloLens-Entwicklung
* Importieren von Assets und Einrichten der Szene
* Visualisierung des räumlichen Gitters, der Handgitter und des Frameratenzählers

## <a name="instructions"></a>Anweisungen

### <a name="create-new-unity-project"></a>Erstellen eines neuen Unity-Projekts

1. Starten Sie Unity.
2. Wählen Sie **Neu** aus.
![Lektion1 Kapitel1 Schritt2](images/Lesson1Chapter1Step2.JPG)
3. Geben Sie einen Projektnamen ein (z. b. "Mixedrealitybase").
![Lektion1 Kapitel1 Schritt3](images/Lesson1Chapter1Step3.JPG)
4. Geben Sie einen Speicherort zum Speichern Ihres Projekts ein.
![Lektion1 Kapitel1 Schritt4](images/Lesson1Chapter1Step4.JPG)
5. Stellen Sie sicher, dass das Projekt auf **3D** festgelegt ist.
![Lektion1 Kapitel1 Schritt5](images/Lesson1Chapter1Step5.JPG)
6. Klicken Sie auf **Projekt erstellen**.
![Lektion1 Kapitel1 Schritt6](images/Lesson1Chapter1Step6.JPG)

### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Konfigurieren des Unity-Projekts für Windows Mixed Reality

1. Öffnen Sie das Fenster Buildeinstellungen, indem Sie zu Datei > Buildeinstellungen navigieren.
![Lektion1 Kapitel4 Schritt1](images/Lesson1Chapter4Step1.JPG)
2. Wechseln Sie zu universelle Windows-Plattform, indem Sie universelle Windows-Plattform auswählen. Klicken Sie auf die Schaltfläche Plattform wechseln, um Plattformen zu wechseln Anwendungen, die auf hololens 2 ausgeführt werden, müssen universelle Windows-Plattform (UWP) kompatibel sein.
![Lektion1 Kapitel4 Schritt2](images/Lesson1Chapter4Step2.JPG)
3. Aktivieren Sie die virtuelle Realität, indem Sie im Fenster erstellen auf Player-Einstellungen klicken, und aktivieren Sie das Kontrollkästchen Virtual Reality supported unter den Einstellungen "XR" im Inspektor-Panel, wie in der folgenden Abbildung dargestellt. Beachten Sie, dass Sie möglicherweise das Fenster "Buildeinstellungen" auf den Weg ziehen müssen, um den Inspektor-Panel anzuzeigen. Das Kontrollkästchen "Virtual Reality supported" gilt auch für "Mixed Reality" und "Augmented Reality", da es sich um das Aktivieren von stereoskopischen Vision handelt (das Rendering verschiedener Bilder für jedes Auge). ![Lektion1 Kapitel4 Schritt3](images/Lesson1Chapter4Step3.JPG)
4. Vergewissern Sie sich, dass im gleichen Inspektor-Panel unter Veröffentlichungs Einstellungen das Kontrollkästchen räumliche Wahrnehmung im Abschnitt Funktionen aktiviert ist. Die räumliche Wahrnehmung ermöglicht es uns, das räumliche zuordnungsmesh auf einem Mixed Reality-Gerät (z. b. hololens 2) visuell darzustellen. Die Veröffentlichungs Einstellungen befinden sich im Inspektor-Panel, oberhalb der XR-Einstellungen und unter anderen Einstellungen.
![Lektion1 Kapitel4 Schritt4](images/Lesson1Chapter4Step4.JPG)

> HINWEIS: Obwohl es in diesem Abschnitt nicht verwendet wird, sind einige weitere gängige Funktionen, die Sie möglicherweise aktivieren möchten, das Mikrofon für Sprachbefehle und Internetclient für die Verbindung mit Diensten, die eine Netzwerkverbindung erfordern.

### <a name="import-the-mixed-reality-toolkit"></a>Importieren des Mixed Reality-Toolkits

1. Laden Sie das [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage) Unity-Paket herunter, und speichern Sie es in einem Ordner auf Ihrem PC.

2. Importieren Sie das Mixed Reality-Toolkit-Paket, indem Sie auf „Assets“ > „Importieren“ > „Benutzerdefiniertes Paket“ klicken. Suchen Sie nach dem in Schritt 1 heruntergeladenen Mixed Reality-Toolkit-Paket, und öffnen Sie es, um den Importvorgang zu starten. Warten Sie einige Minuten, bis der Importvorgang startet.
    ![Lektion1 Kapitel2 Schritt2a](images/Lesson1Chapter2Step2a.JPG) ![Lektion1 Kapitel2 Schritt2b](images/Lesson1Chapter2Step2b.JPG)

3. Klicken Sie im nächsten Popup Fenster auf Importieren, um mit dem Importieren des Mixed Reality Toolkit zu beginnen. Stellen Sie sicher, dass alle Elemente wie in der Abbildung dargestellt geprüft werden. Wenn ein Popup Dialogfeld mit der Aufforderung zum Anwenden der Standardeinstellungen für das Mixed Reality Toolkit angezeigt wird, klicken Sie auf übernehmen.
    ![Lektion1 Kapitel2 Schritt3](images/Lesson1Chapter2Step3.JPG) ![Lektion1 Kapitel2 Schritt3](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Konfigurieren des Mixed Reality-Toolkits

1. Konfigurieren Sie das mrtk, indem Sie in der Menüleiste Mixed Reality Toolkit > configure auswählen. Wenn dieses Menüelement nach dem Importieren des Mixed Reality-Toolkits nicht angezeigt wird, starten Sie Unity neu.
  ![Lektion1 Kapitel3 Schritt1](images/Lesson1Chapter3Step1.JPG)

  > Hinweis: Möglicherweise wird ein Popup Dialogfeld angezeigt, in dem Sie aufgefordert werden, ein Profil für das Mixed Reality Toolkit auszuwählen. Wenn dies der Fall ist, wählen Sie OK aus, und wählen Sie das Profil mit dem Namen "defaultmixedrealitytoolkitconfigurationprofile" aus.

2. In Ihrer Szene werden aus dem mrtk mehrere neue Elemente und Änderungen vorgenommen. Speichern Sie Ihre Szene unter einem anderen Namen, indem Sie auf Datei > Speichern unter klicken und ihrer Szene einen Namen (z. b. basescene) übergeben. Sorgen Sie dafür, dass Sie Ihre Szene organisieren, indem Sie Sie im Ordner "Szenen" Ihres Projekts speichern.
  ![Lektion1 Kapitel3 Schritt2a](images/Lesson1Chapter3Step2a.JPG)
  ![Lektion1 Kapitel3 Schritt2b](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>Erstellen Ihrer Anwendung auf Ihrem Gerät

1. Wenn Sie das Fenster "Buildeinstellungen" aus den vorherigen Abschnitten geschlossen haben, öffnen Sie das Fenster "Buildeinstellungen" erneut, indem Sie zu Datei > Buildeinstellungen
    ![Lektion1 Kapitel5 Schritt1](images/Lesson1Chapter5Step1.JPG)

2. Stellen Sie sicher, dass die gewünschte Szene in den Kulissen in der Buildliste angezeigt wird, indem Sie auf die Schaltfläche offene Szenen hinzufügen klicken.

3. Klicken Sie auf die Schaltfläche „Erstellen“, um den Buildprozess zu starten.
    ![Lektion1 Kapitel5 Schritt3](images/Lesson1Chapter5Step3.JPG)

4. Erstellen und benennen Sie einen neuen Ordner für Ihre Anwendung. In der folgenden Abbildung wurde ein Ordner mit dem Namen "App" erstellt, der die Anwendung enthält. Klicken Sie auf Ordner auswählen, um mit dem Erstellen in den neu erstellten Ordner zu beginnen. Nachdem der Build abgeschlossen wurde, können Sie das Fenster mit den Buildeinstellungen in Unity schließen. 
    ![Lektion1 Kapitel5 Schritt4](images/Lesson1Chapter5Step4.JPG)

  > HINWEIS: Wenn der Vorgang fehlschlägt, wiederholen Sie den Buildvorgang, oder starten Sie Unity neu, und wiederholen Sie dann den Buildvorgang. Wenn ein Fehler angezeigt wird, z. b. "Fehler: CS0246 = der Typ-oder Namespace Name "XX" konnte nicht gefunden werden. (fehlt eine using-Direktive oder ein Assemblyverweis?). Wenn dies der Fall ist, müssen Sie möglicherweise das [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) installieren.
  >

5. Öffnen Sie nach Abschluss des Buildvorgangs den neu erstellten Ordner, der Ihre neu erstellten Anwendungsdateien enthält. Doppelklicken Sie auf die Projekt Mappe mixedrealitybase. sln oder auf den entsprechenden Namen, wenn Sie einen alternativen Namen für das Projekt verwendet haben, um die Projektmappendatei in Visual Studio zu öffnen.

  > Hinweis: Stellen Sie sicher, dass Sie den neu erstellten Ordner (d. h. den app-Ordner, wenn Sie die Benennungs Konventionen aus den vorherigen Schritten befolgen) öffnen, da es eine ähnlich benannte sln-Datei außerhalb des Ordners gibt, die nicht mit der SLN-Datei im Buildordner verwechselt werden muss. 

![Lektion1 Kapitel5 Schritt5](images/Lesson1Chapter5Step5.JPG)

  > Hinweis: Wenn Sie von Visual Studio zur Installation neuer Komponenten aufgefordert werden, nehmen Sie sich einen Moment Zeit, um zu überprüfen, ob alle erforderlichen Komponenten (wie auf der Seite [Installieren der Tools](install-the-tools.md) angegeben) installiert sind.

6. Verbinden Sie Ihre hololens 2 mit Ihrem PC. Bei diesen Anweisungen wird vorausgesetzt, dass Sie einen Test mit einem hololens 2-Gerät bereitstellen, aber Sie können auch die Bereitstellung auf dem [hololens 2-Emulator](using-the-hololens-emulator.md) oder das Erstellen eines [App-Pakets für das Sideload](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>) auswählen.

7. Stellen Sie vor dem Erstellen der App auf Ihrem Gerät sicher, dass sich das Gerät im Entwicklermodus befindet. Wenn Sie das erste Mal auf den hololens 2 bereitstellen, werden Sie möglicherweise von Visual Studio aufgefordert, ihre hololens 2 mit einer PIN zu koppeln. Folgen Sie [diesen Anweisungen](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio), wenn Sie den Entwicklermodus aktivieren oder das Gerät mit Visual Studio koppeln müssen.

8. Konfigurieren Sie Visual Studio für die Erstellung auf Ihre hololens 2, indem Sie die Releasekonfiguration und die ARM-Architektur auswählen.
    ![Lektion1 Kapitel5 Schritt8](images/Lesson1Chapter5Step8.JPG)

9. Der letzte Schritt besteht darin, auf Ihrem Gerät zu erstellen, indem Sie Debuggen > Starten ohne Debugging auswählen. Wenn Sie starten ohne Debugging auswählen, wird die Anwendung sofort bei einem erfolgreichen Build auf Ihrem Gerät gestartet, aber ohne Debuginformationen, die in Visual Studio angezeigt werden. Dies bedeutet auch, dass Sie das USB-Kabel entfernen können, während Ihre Anwendung auf Ihrem HoloLens 2-Gerät ausgeführt wird, ohne dass die Anwendung beendet wird. Sie können auch erstellen > Lösung bereitstellen, um Sie auf Ihrem Gerät bereitzustellen, ohne dass die Anwendung automatisch gestartet wird.
    ![Lektion1 Kapitel5 Schritt9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben nun Ihre erste hololens 2-Anwendung bereitgestellt. Beim durchlaufen wird ein räumliches Mesh angezeigt, das alle Oberflächen abdeckt, die von den hololens 2 wahrgenommen wurden. Darüber hinaus sollten Sie Indikatoren und Finger zur Hand Verfolgung sowie einen Frameraten Indikator sehen, um die Anwendungsleistung zu überwachen. Dies sind nur einige der grundlegenden Elemente, die standardmäßig im Mixed Reality-Toolkit enthalten sind. In den Lektionen sollten Sie weitere Inhalte und Interaktivität zu Ihrer Szene hinzufügen, damit Sie die Funktionen von hololens 2 und dem Mixed Reality Toolkit vollständig untersuchen können.

>Hinweis: Wie Sie den Frameratenzähler mithilfe eines Sprachbefehls umschalten, erfahren Sie in [Lektion 5](mrlearning-base-ch5.md).

[Nächste Lektion: Benutzeroberfläche, Handverfolgung und Konfiguration des Mixed Reality-Toolkits](mrlearning-base-ch2.md)
