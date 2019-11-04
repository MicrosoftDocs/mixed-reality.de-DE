---
title: 'Tutorials zu den ersten Schritten: 2. Initialisieren Ihres Projekts und der ersten Anwendung'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 3a7b25a17ed1a80834dc7029e172bc7924992b07
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438442"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Initialisieren Ihres Projekts und der ersten Anwendung

In dieser ersten Lektion erfahren Sie mehr über einige der Funktionen, die das [Mixed Reality Toolkit (mrtk)]() anbieten muss, starten Sie Ihre erste Anwendung für die hololens 2, und stellen Sie Sie auf dem Gerät bereit.

## <a name="objectives"></a>Ziele

* Optimieren von Unity für die HoloLens-Entwicklung
* Importieren von Assets und Einrichten der Szene
* Visualisierung des Netzes für räumliche Zuordnung, Hand-Meshes und des Framerate-Zählers.

## <a name="instructions"></a>Anweisungen

### <a name="create-new-unity-project"></a>Erstellen eines neuen Unity-Projekts

1. Starten Sie Unity.
2. Wählen Sie **New** aus.
![Lektion1 Kapitel1 Schritt2](images/Lesson1Chapter1Step2.JPG)
3. Geben Sie einen Projektnamen ein (z. b. "mixedrealitybase").
![Lektion1 Kapitel1 Schritt3](images/Lesson1Chapter1Step3.JPG)
4. Geben Sie einen Speicherort zum Speichern Ihres Projekts ein.
![Lektion1 Kapitel1 Schritt4](images/Lesson1Chapter1Step4.JPG)
5. Stellen Sie sicher, dass das Projekt auf **3D** festgelegt ist.
![Lektion1 Kapitel1 Schritt5](images/Lesson1Chapter1Step5.JPG)
6. Klicken Sie auf **Projekt erstellen**.
![Lektion1 Kapitel1 Schritt6](images/Lesson1Chapter1Step6.JPG)

### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Konfigurieren des Unity-Projekts für Windows Mixed Reality

1. Öffnen Sie das Fenster *Buildeinstellungen* , indem Sie zu **Datei** > **Buildeinstellungen**navigieren.
![Lektion1 Kapitel4 Schritt1](images/Lesson1Chapter4Step1.JPG)
2. Wählen Sie die *universelle Windows-Plattform* aus, und klicken Sie auf die Schaltfläche **Plattform wechseln** , um Plattformen Anwendungen, die auf hololens 2 ausgeführt werden, müssen universelle Windows-Plattform (UWP) kompatibel sein.
![Lektion1 Kapitel4 Schritt2](images/Lesson1Chapter4Step2.JPG)
3. Aktivieren Sie die virtuelle Realität durch Klicken auf die Schaltfläche **Player Einstellungen** im Fenster erstellen, und aktivieren Sie das Kontrollkästchen *Virtual Reality supported* unter den Einstellungen "XR" im Inspektor-Panel, wie in der folgenden Abbildung dargestellt. Beachten Sie, dass Sie möglicherweise das Fenster " *Buildeinstellungen* " auf den Weg ziehen müssen, um den Inspektor-Panel anzuzeigen. Das Kontrollkästchen " *Virtual Reality supported* " gilt auch für "Mixed Reality" und "Augmented Reality", da es sich um das Aktivieren von stereoskopischen Visionen (Rendering verschiedener Bilder für jedes Auge) handelt. ![Lesson1 Chapter4 Schritt 3](images/Lesson1Chapter4Step3.JPG)
4. Ändern Sie außerdem unter XR-Einstellungen den *Stereo-Renderingmodus* in *Single Pass-instanziierten*. Diese [Renderingpipeline](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) ist für hololens 2 im Allgemeinen am leistungsfähigsten. Wenn Sie an anderen leistungsfähigen Konfigurationen für Ihre Unity-Umgebung interessiert sind, befolgen Sie [diese Anweisungen](recommended-settings-for-unity.md).
![Lesson1 Chapter4 Step3b](images/Lesson1Chapter4Step3b.jpg)
5. Vergewissern Sie sich, dass im gleichen Inspektor-Panel unter *Veröffentlichungs Einstellungen*das Kontrollkästchen *räumliche Wahrnehmung* im Abschnitt Funktionen aktiviert ist. Die räumliche Wahrnehmung ermöglicht es uns, das räumliche zuordnungsmesh auf einem Mixed Reality-Gerät (z. b. hololens 2) visuell darzustellen. Die Veröffentlichungs Einstellungen befinden sich im Inspektor-Panel, oberhalb der XR-Einstellungen und unter anderen Einstellungen.
![Lektion1 Kapitel4 Schritt4](images/Lesson1Chapter4Step4.JPG)

> [!NOTE]
> Obwohl es in diesem Abschnitt nicht verwendet wird, sind einige weitere gängige Funktionen, die Sie möglicherweise aktivieren möchten, das *Mikrofon* für Sprachbefehle und *Internetclient* für die Verbindung mit Diensten, die eine Netzwerkverbindung erfordern.

### <a name="import-the-mixed-reality-toolkit"></a>Importieren des Mixed Reality-Toolkits

1. Laden Sie die neuesten Unity-Pakete für [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) herunter, und speichern Sie Sie in einem Ordner auf Ihrem PC.

2. Importieren Sie jedes der *Mixed Reality Toolkit* -Pakete. Klicken Sie zunächst auf **Assets** > **importieren** Sie > **benutzerdefiniertes Paket**. Wählen Sie eines der *Mixed Reality Toolkit* -Pakete aus, die Sie in Schritt 1 heruntergeladen haben, und öffnen Sie es, um den Import Vorgang Warten Sie einige Minuten, bis der Importvorgang startet.
    ![Lektion1 Kapitel2 Schritt2a](images/Lesson1Chapter2Step2a.JPG) ![Lektion1 Kapitel2 Schritt2b](images/Lesson1Chapter2Step2b.JPG)

3. Klicken Sie im nächsten Popup Fenster auf **importieren** , um mit dem Importieren des ausgewählten Pakets in das Unity-Projekt zu beginnen. Stellen Sie sicher, dass alle Elemente wie in der Abbildung dargestellt geprüft werden.
    ![Lesson1 chapter2 Schritt 3](images/Lesson1Chapter2Step3.JPG)
4. Wiederholen Sie die Schritte 2 und 3 für jedes heruntergeladene Paket *Mixed Reality Toolkit* -Paket.

> [!NOTE]
> Wenn ein Popup Dialogfeld mit der Aufforderung zum Anwenden der Standardeinstellungen für das Mixed Reality Toolkit angezeigt wird **, klicken Sie**auf übernehmen. Mrtk analysiert das Projekt auf fehlende Empfohlene Einstellungen beim Importieren für das automatisierte Setup.

![Lesson1 chapter2 Schritt 3](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Konfigurieren des Mixed Reality-Toolkits

1. Fügen Sie das *Mixed Reality Toolkit* Ihrer aktuellen Szene hinzu, indem Sie **Mixed Reality Toolkit** auswählen > **zu Szene hinzufügen und konfigurieren.** in der Menüleiste. Wenn dieses Menüelement nach dem Importieren des Mixed Reality-Toolkits nicht angezeigt wird, starten Sie Unity neu.
  ![Lektion1 Kapitel3 Schritt1](images/Lesson1Chapter3Step1.JPG)

> [!NOTE]
> Möglicherweise wird ein Popup Dialogfeld angezeigt, in dem Sie aufgefordert werden, ein [Profil für das Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html)auszuwählen. Wenn dies der Fall ist, wählen Sie **OK**aus, und wählen Sie das Profil mit dem Namen *"defaultmixedrealitytoolkitconfigurationprofile"* aus.

2. Ihre Szene verfügt über mehrere neue Elemente und Änderungen. Speichern Sie Ihre Szene unter einem anderen Namen, indem Sie auf **Datei** > **Speichern**unter klicken und ihrer Szene einen Namen (z. b. *basescene*) übergeben. Sorgen Sie dafür, dass Sie Ihre Szene organisieren, indem Sie Sie *im Ordner "* *Szenen* " Ihres Projekts speichern.
  ![Lektion1 Kapitel3 Schritt2a](images/Lesson1Chapter3Step2a.JPG)
  ![Lektion1 Kapitel3 Schritt2b](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>Erstellen Ihrer Anwendung auf Ihrem Gerät

1. Wenn Sie das Fenster " *Buildeinstellungen* " aus den vorherigen Abschnitten geschlossen haben, öffnen Sie das Fenster " *Buildeinstellungen* " erneut, indem Sie zu Datei > **Buildeinstellungen**
    ![Lektion1 Kapitel5 Schritt1](images/Lesson1Chapter5Step1.JPG)

2. Stellen Sie sicher, dass die Szene, die Sie gerade erstellt haben, in den *Kulissen in* der Buildliste angezeigt wird, indem Sie auf die Schaltfläche **offene Szenen hinzufügen** klicken.

3. Drücken Sie die Schaltfläche **Erstellen** , um den Buildprozess zu starten.
    ![Lektion1 Kapitel5 Schritt3](images/Lesson1Chapter5Step3.JPG)

4. Erstellen und benennen Sie einen neuen Ordner für Ihre Anwendung. In der folgenden Abbildung wurde ein Ordner mit dem Namen "App" erstellt, der die Anwendung enthält. Klicken Sie auf **Ordner auswählen** , um mit dem Erstellen in den neu erstellten Ordner zu beginnen. Nachdem der Build abgeschlossen wurde, können Sie das Fenster mit den *Buildeinstellungen* in Unity schließen.
    ![Lektion1 Kapitel5 Schritt4](images/Lesson1Chapter5Step4.JPG)

> [!IMPORTANT]
> Wenn der Vorgang fehlschlägt, wiederholen Sie den Buildvorgang, oder starten Sie Unity neu, und wiederholen Sie dann den Buildvorgang. Wenn ein Fehler angezeigt wird, z. b. "Fehler: CS0246 = der Typ-oder Namespace Name" XX "wurde nicht gefunden (fehlt eine using-Direktive oder ein Assemblyverweis?). Wenn dies der Fall ist, müssen Sie möglicherweise das [Windows 10 SDK (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk) installieren.

5. Öffnen Sie nach Abschluss des Buildvorgangs den neu erstellten Ordner, der Ihre neu erstellten Anwendungsdateien enthält. Doppelklicken Sie auf die Projekt Mappe *mixedrealitybase. sln* oder auf den entsprechenden Namen, wenn Sie einen alternativen Namen für das Projekt verwendet haben, um die Projektmappendatei in Visual Studio zu öffnen.

> [!NOTE]
> Stellen Sie sicher, dass Sie den neu erstellten Ordner (d. h. den *App* -Ordner, wenn Sie die Benennungs Konventionen aus den vorherigen Schritten befolgen) öffnen, da es eine ähnlich benannte sln-Datei außerhalb des Ordners gibt, die nicht mit der SLN-Datei im Buildordner verwechselt werden muss. Die Ordnerstruktur sollte in etwa wie in der folgenden Abbildung aussehen.
>
> Wenn Sie von Visual Studio zur Installation neuer Komponenten aufgefordert werden, nehmen Sie sich einen Moment Zeit, um zu überprüfen, ob alle erforderlichen Komponenten (wie auf der Seite [Installieren der Tools](install-the-tools.md) angegeben) installiert sind.

![Lektion1 Kapitel5 Schritt5](images/Lesson1Chapter5Step5.JPG)

6. Verbinden Sie Ihre hololens 2 mit Ihrem PC. Bei diesen Anweisungen wird vorausgesetzt, dass Sie die Bereitstellung auf einem hololens 2-Gerät durchführen. Sie können auch die Bereitstellung auf dem [hololens 2-Emulator](using-the-hololens-emulator.md) oder das Erstellen eines [App-Pakets für das Sideload](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>) durchführen.

> [!IMPORTANT]
> Bevor Sie auf Ihr Gerät aufbauen, muss sich das Gerät im *Entwicklermodus* befinden und mit Ihrem Entwicklungs Computer gekoppelt werden. Beide Schritte können mithilfe der folgenden [Anweisungen](using-visual-studio.md) ausgeführt werden:

8. Konfigurieren Sie Visual Studio für die Erstellung auf Ihre hololens 2, indem Sie die *Release* -oder *Master* Konfiguration und die *Arm* -Architektur auswählen.
    ![Lektion1 Kapitel5 Schritt8](images/Lesson1Chapter5Step8.JPG)

9. Der letzte Schritt ist das Erstellen und bereitstellen auf Ihrem Gerät, indem Sie **Debuggen** > **Starten ohne Debugging**auswählen. Wenn Sie *Starten ohne Debugging* auswählen, wird die Anwendung sofort bei einem erfolgreichen Build auf dem Gerät gestartet, aber ohne angehängter Debugger und Informationen, die in Visual Studio angezeigt werden. Dies bedeutet auch, dass Sie das USB-Kabel entfernen können, während Ihre Anwendung auf Ihrem HoloLens 2-Gerät ausgeführt wird, ohne dass die Anwendung beendet wird.

> [!NOTE]
> Sie können auch **Erstellen** > **Lösung** bereitstellen, um Sie auf Ihrem Gerät bereitzustellen, ohne dass die Anwendung automatisch gestartet wird.

![Lesson1 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben nun Ihre erste hololens 2-Anwendung bereitgestellt. Beim durchlaufen wird ein räumliches Mapping angezeigt, das alle Oberflächen abdeckt, die von den hololens 2 wahrgenommen wurden. Darüber hinaus sollten Sie Indikatoren und Finger zur Hand Verfolgung sowie einen Frameraten Indikator sehen, um die Anwendungsleistung zu überwachen. Dies sind nur einige der grundlegenden Elemente, die standardmäßig im Mixed Reality-Toolkit enthalten sind. In den Lektionen, die Sie erhalten, beginnen Sie mit dem Hinzufügen von mehr Inhalt und Interaktivität zu Ihrer Szene, damit Sie die Funktionen von hololens 2 und dem Mixed Reality Toolkit vollständig untersuchen können.

> [!NOTE]
> In [Lektion 5](mrlearning-base-ch5.md)wird erläutert, wie Sie den Leistungs Besatz für Frameraten mithilfe eines sprach Befehls umschalten. Im Allgemeinen wird empfohlen, den visuellen Profiler während der Entwicklung jederzeit sichtbar zu machen, um zu verstehen, wann Codeänderungen möglicherweise Auswirkungen auf die Leistung haben. Die hololens 2-Anwendung sollte [kontinuierlich mit 60 fps ausgeführt](understanding-performance-for-mixed-reality.md)werden.

[Nächste Lektion: 3. Erstellen einer Benutzeroberfläche und Konfigurieren von Mixed Reality Toolkit](mrlearning-base-ch2.md)
