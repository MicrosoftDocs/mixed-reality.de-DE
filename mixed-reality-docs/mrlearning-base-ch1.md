---
title: Tutorials zu den ersten Schritten – 2 Initialisieren des Projekts und der ersten Anwendung
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: d0c166f760884efab9719ecba1ff83285872e2ef
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334417"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Initialisieren des Projekts und der ersten Anwendung

## <a name="overview"></a>Übersicht

In dieser ersten Lektion lernen Sie einige der Funktionen kennen, die das <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality-Toolkit (MRTK)</a> bietet, starten Ihre erste Anwendung für das HoloLens 2-Gerät und stellen sie auf dem Gerät bereit.

## <a name="objectives"></a>Ziele

* Konfigurieren von Unity für die HoloLens-Entwicklung
* Importieren von Assets und Einrichten der Szene
* Visualisierung des Gittermodells für die Raumzuordnung, der Hand-Meshes und des Frameratenzählers

## <a name="create-new-unity-project"></a>Erstellen eines neuen Unity-Projekts

1. Starten Sie Unity.

2. Wählen Sie **Neu** aus.

    ![Lektion 1 Abschnitt 1 Schritt 2](images/mrlearning-base-ch1-1-step2.JPG)

3. Geben Sie einen Projektnamen ein (z. B. "MixedRealityBase").

    ![Lektion 1 Abschnitt 1 Schritt 3](images/mrlearning-base-ch1-1-step3.JPG)

4. Geben Sie einen Speicherort zum Speichern Ihres Projekts ein.

    ![Lektion 1 Abschnitt 1 Schritt 4](images/mrlearning-base-ch1-1-step4.JPG)

5. Stellen Sie sicher, dass das Projekt auf **3D** festgelegt ist.

    ![Lektion 1 Abschnitt 1 Schritt 5](images/mrlearning-base-ch1-1-step5.JPG)

6. Klicken Sie auf **Projekt erstellen**.

    ![Lektion 1 Abschnitt 1 Schritt 6](images/mrlearning-base-ch1-1-step6.JPG)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Konfigurieren des Unity-Projekts für Windows Mixed Reality

1. Öffnen Sie das Fenster *Buildeinstellungen*, indem Sie zu **Datei** > **Buildeinstellungen** wechseln.

    ![Lektion 1 Abschnitt 2 Schritt 1](images/mrlearning-base-ch1-2-step1.JPG)

2. Wählen Sie die *universelle Windows-Plattform* aus, und klicken Sie auf die Schaltfläche **Plattform wechseln**, um die Plattform zu wechseln. Anwendungen, die auf HoloLens 2 ausgeführt werden, müssen mit der Universellen Windows-Plattform (UWP) kompatibel sein.

    ![Lektion 1 Abschnitt 2 Schritt 2](images/mrlearning-base-ch1-2-step2.JPG)

3. Aktivieren Sie virtuelle Realität, indem Sie im Buildfenster auf die Schaltfläche **Player-Einstellungen** klicken, und aktivieren Sie dann im Inspektorbereich unter „XR-Einstellungen“ das Kontrollkästchen für die *VR-Unterstützung*, wie in der folgenden Abbildung gezeigt. Beachten Sie, dass Sie das Fenster *Buildeinstellungen* möglicherweise verschieben oder minimieren müssen, um den Inspektorbereich sehen zu können. Das Kontrollkästchen für die *VR-Unterstützung* betrifft auch Mixed Reality- und Augmented Reality-Headsets, da es sich auf die Aktivierung der stereoskopischen Funktion (Rendering unterschiedlicher Bilder für jedes Auge) bezieht.

    ![Lektion 1 Abschnitt 2 Schritt 3](images/mrlearning-base-ch1-2-step3.JPG)

4. Ändern Sie außerdem unter "XR-Einstellungen" den *Stereo Rendering Mode* (Stereo-Renderingmodus) in *Single Pass Instanced* (Einzeldurchgangs-Instanz). Diese [Renderingpipeline-Stil](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) bietet im Allgemeinen die höchste Leistung für HoloLens 2. Wenn Sie sich für weitere leistungsfähige Konfigurationen für Ihre Unity-Umgebung interessieren, befolgen Sie [diese Anweisungen](recommended-settings-for-unity.md).

    ![Lektion 1 Abschnitt 2 Schritt 4](images/mrlearning-base-ch1-2-step4.jpg)

5. Vergewissern Sie sich im gleichen Inspektorbereich, dass unter *Veröffentlichungseinstellungen* im Abschnitt „Funktionen“ das Kontrollkästchen *Räumliche Wahrnehmung* aktiviert ist. Die Funktion „Räumliche Wahrnehmung“ ermöglicht das Visualisieren des Gittermodells für die Raumzuordnung auf einem Mixed Reality-Gerät wie HoloLens 2. Sie finden die Veröffentlichungseinstellungen im Inspektorbereich oberhalb von „XR-Einstellungen“ und unterhalb von „Andere Einstellungen“.

    ![Lektion 1 Abschnitt 2 Schritt 5](images/mrlearning-base-ch1-2-step5.JPG)

    >[!NOTE]
    >Obwohl in diesem Abschnitt nicht verwendet, können Sie einige weitere allgemeine Funktionen aktivieren, wie z. B. das *Mikrofon* für Sprachbefehle und *InternetClient* für das Herstellen einer Verbindung mit Diensten, die eine Netzwerkverbindung erfordern.

## <a name="import-the-mixed-reality-toolkit"></a>Importieren des Mixed Reality-Toolkits

1. Laden Sie das Unity-Paket [Mixed Reality-Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)[Version 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) herunter, und speichern Sie es in einem Ordner auf Ihrem PC.

2. Importieren Sie das *Mixed Reality Toolkit*-Paket, das Sie im vorherigen Schritt heruntergeladen haben. Klicken Sie zunächst auf **Assets** > **Import** > **Custom Package** (Ressourcen > Importieren > Benutzerdefiniertes Paket), wählen Sie *Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage* aus, und öffnen Sie es, um den Importvorgang zu starten. Warten Sie einige Minuten bis zum Abschluss des Importvorgangs.

    ![Lektion 1 Abschnitt 3 Schritt 2a](images/mrlearning-base-ch1-3-step2a.JPG)

    ![Lektion 1 Abschnitt 3 Schritt 2b](images/mrlearning-base-ch1-3-step2b.JPG)

3. Klicken Sie im nächsten Popupfenster auf **Import** (Importieren), um mit dem Importieren des Mixed Reality-Toolkits zu beginnen. Stellen Sie sicher, dass alle Elemente aktiviert sind, wie in der Abbildung dargestellt.

    ![Lektion 1 Abschnitt 3 Schritt 3](images/mrlearning-base-ch1-3-step3.JPG)

    > [!NOTE]
    > Wenn ein Popupdialogfeld angezeigt wird, in dem Sie gefragt werden, ob die Standardeinstellungen des Mixed Reality-Toolkits übernommen werden sollen, klicken Sie auf **Übernehmen**. Das MRTK analysiert beim Import für das automatische Setup Ihr Projekt und prüft es auf fehlende empfohlene Einstellungen. Abhängig von Ihren Einstellungen sieht das Popup möglicherweise anders aus als in der Abbildung unten.

    ![Lektion 1 Abschnitt 3 Schritt 4 HINWEIS 1](images/mrlearning-base-ch1-3-step4-note1.JPG)

## <a name="configure-the-mixed-reality-toolkit"></a>Konfigurieren des Mixed Reality-Toolkits

1. Fügen Sie Ihrer aktuellen Szene das *Mixed Reality Toolkit* hinzu, indem Sie in der Menüleiste **Mixed Reality Toolkit** > **Add to Scene and Configure..** (Zu Szene hinzufügen und konfigurieren...) auswählen. Wenn dieses Menüelement nach dem Importieren des Mixed Reality-Toolkits nicht angezeigt wird, starten Sie Unity neu.

    ![Lektion 1 Abschnitt 4 Schritt 1](images/mrlearning-base-ch1-4-step1.JPG)

    > [!NOTE]
    > Möglicherweise wird ein Popupdialogfeld zum Auswählen eines [Profils für das Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html) angezeigt. Wählen Sie das Profil *DefaultHoloLens2ConfigurationProfile* aus, indem Sie darauf doppelklicken.

2. Ihre Szene verfügt nun über mehrere neue Elemente und Änderungen. Speichern Sie Ihre Szene unter einem anderen Namen, indem Sie auf **Datei** > **Speichern unter...** klicken, und geben Sie der Szene einen Namen, beispielsweise *Basisszene*. Ordnen Sie Ihre Szene ein, indem Sie sie im Ordner *Scenes* (Szenen) im Ordner *Assets* (Ressourcen) Ihres Projekts speichern.

    ![Lektion 1 Abschnitt 4 Schritt 2a](images/mrlearning-base-ch1-4-step2a.JPG)

    ![Lektion 1 Abschnitt 4 Schritt 2b](images/mrlearning-base-ch1-4-step2b.JPG)

## <a name="build-your-application-to-your-device"></a>Erstellen Ihrer Anwendung auf Ihrem Gerät

1. Wenn Sie das Fenster *Buildeinstellungen* aus den vorherigen Abschnitten geschlossen haben, öffnen Sie das Fenster *Buildeinstellungen* erneut, indem Sie zu **Datei** > **Buildeinstellungen** wechseln.

    ![Lektion 1 Abschnitt 5 Schritt 1](images/mrlearning-base-ch1-5-step1.JPG)

2. Achten Sie darauf, dass Ihre soeben erstellte Szene in der Liste *Scenes in Build* (Szenen im Build) enthalten ist, indem Sie auf die Schaltfläche **Add Open Scenes** (Geöffnete Szenen hinzufügen) klicken, während die Szene in Unity geöffnet ist.

3. Klicken Sie auf die Schaltfläche **Build** (Erstellen), um den Buildprozess zu starten.

    ![Lektion 1 Abschnitt 5 Schritt 3](images/mrlearning-base-ch1-5-step3.JPG)

4. Erstellen und benennen Sie einen neuen Ordner für Ihre Anwendung. In der folgenden Abbildung können Sie sehen, dass ein Ordner mit dem Namen „App“ erstellt wurde, der die Anwendung enthalten soll. Klicken Sie auf **Select Folder** (Ordner auswählen), um mit der Erstellung im neu erstellten Ordner zu beginnen. Nach Abschluss der Erstellung (des Buildvorgangs) können Sie das Fenster *Build Settings* (Buildeinstellungen) in Unity schließen.

    ![Lektion 1 Abschnitt 5 Schritt 4](images/mrlearning-base-ch1-5-step4.JPG)

    >[!IMPORTANT]
    >Wenn der Vorgang fehlschlägt, wiederholen Sie den Buildvorgang, oder starten Sie Unity neu, und wiederholen Sie dann den Buildvorgang. Eventuell wird ein Fehler angezeigt, z. B. "Fehler: CS0246 = Der Typ- oder Namespacename 'XX' konnte nicht gefunden werden. (Fehlt eine Using-Anweisung oder ein Assemblyverweis?)" In diesem Fall müssen Sie möglicherweise das [Windows 10 SDK (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk) installieren.

5. Öffnen Sie nach Abschluss des Buildvorgangs den neu erstellten Ordner, der Ihre neu erstellten Anwendungsdateien enthält. Doppelklicken Sie auf die Projektmappe *MixedRealityBase.sln* (oder auf den entsprechenden Namen, wenn Sie einen alternativen Namen für Ihr Projekt verwendet haben), um die Projektmappendatei in Visual Studio zu öffnen.

    >[!NOTE]
    >Achten Sie darauf, dass Sie den neu erstellten Ordner öffnen (also den Ordner *App*, wenn Sie die Namenskonventionen in den vorherigen Schritten befolgt haben), weil außerhalb dieses Ordners noch eine SLN-Datei mit einem ähnlichen Namen vorhanden ist, die nicht mit der SLN-Datei im Buildordner verwechselt werden darf. Die Ordnerstruktur sollte ähnlich wie in dieser Abbildung aussehen:
    >
    >Wenn Sie von Visual Studio zur Installation neuer Komponenten aufgefordert werden, nehmen Sie sich einen Moment Zeit, um zu überprüfen, ob alle erforderlichen Komponenten (wie auf der Seite [Installieren der Tools](install-the-tools.md) angegeben) installiert sind.

    ![Lektion 1 Abschnitt 5 Schritt 5](images/mrlearning-base-ch1-5-step5.JPG)

6. Verbinden Sie Ihre HoloLens 2 mit Ihrem PC. Bei diesen Anweisungen wird davon ausgegangen, dass Sie auf einem HoloLens 2-Gerät bereitstellen. Sie können die Bereitstellung aber auch auf dem [HoloLens 2-Emulator](using-the-hololens-emulator.md) vornehmen oder ein [App-Paket für das Querladen](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>) erstellen.

    >[!IMPORTANT]
    >Bevor Sie den Build für Ihr Gerät erstellen, muss das Gerät in den *Entwicklermodus* versetzt und mit Ihrem Entwicklungscomputer gekoppelt werden. Sie können beide Schritte ausführen, indem Sie [diese Anweisungen](using-visual-studio.md) befolgen.

7. Konfigurieren Sie Visual Studio für die Erstellung auf Ihrem HoloLens 2-Gerät, indem Sie die Konfiguration *Release* oder *Master*, die Architektur *ARM* und das Ziel *Device* (Gerät) auswählen.

    ![Lektion 1 Abschnitt 5 Schritt 8](images/mrlearning-base-ch1-5-step7.JPG)

8. Der letzte Schritt ist die Erstellung und Bereitstellung auf Ihrem Gerät durch Auswählen von **Debuggen** > **Starten ohne Debuggen**. Wenn Sie *Starten ohne Debuggen* auswählen, wird die Anwendung sofort nach einem erfolgreichen Buildvorgang auf Ihrem Gerät gestartet, ohne dass jedoch der Debugger gestartet und Debuginformationen in Visual Studio angezeigt werden. Dies bedeutet auch, dass Sie das USB-Kabel entfernen können, während Ihre Anwendung auf Ihrem HoloLens 2-Gerät ausgeführt wird, ohne dass die Anwendung beendet wird.

    > [!NOTE]
    > Sie können auch **Build** > **Projektmappe bereitstellen** auswählen, um die Anwendung auf Ihrem Gerät bereitzustellen, ohne dass sie automatisch gestartet wird.

    ![Lektion 1 Abschnitt 5 Schritt 9](images/mrlearning-base-ch1-5-step8.JPG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben jetzt Ihre erste HoloLens 2-Anwendung bereitgestellt. Während Sie sich in ihr bewegen, sollten Sie ein Gittermodell für die Raumzuordnung sehen, das alle Oberflächen bedeckt, die von der HoloLens 2 erkannt wurden. Darüber hinaus sollten Sie Indikatoren auf Ihren Händen und Fingern für die Handverfolgung und einen Frameratenzähler zum Überwachen der Anwendungsleistung sehen. Dies sind nur einige der grundlegenden Elemente, die standardmäßig im Mixed Reality-Toolkit enthalten sind. In den folgenden Lektionen fügen Sie Ihrer Szene mehr Inhalte und Interaktivität hinzu, sodass Sie alle Funktionen der HoloLens 2 und des Mixed Reality-Toolkits umfassend erkunden können.

> [!NOTE]
> Möglicherweise bemerken Sie in der App den Visual Profiler. In [Lektion 5](mrlearning-base-ch5.md) erfahren Sie, wie Sie den Frameratenzähler mithilfe eines Sprachbefehls umschalten. Im Allgemeinen empfiehlt es sich, den Visual Profiler während der Entwicklung stets eingeblendet zu lassen, damit Sie nachvollziehen können, wenn sich Codeänderungen auf die Leistung auswirken. HoloLens 2-Anwendungen sollten [durchgängig bei 60 FPS ausgeführt werden](understanding-performance-for-mixed-reality.md).

[Nächste Lektion: 3. Erstellen der Benutzeroberfläche und Konfigurieren des Mixed Reality-Toolkits](mrlearning-base-ch2.md)
