---
title: MR-Learning-Basis-Modul – Projektinitialisierung und der ersten Anwendung
description: Führen Sie diesen Kurs erfahren, wie Sie Azure-Gesichtserkennung innerhalb einer mixed Reality-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: Gemischte Realität, Unity, Tutorial, hololens
ms.openlocfilehash: c5490e6a3b542a5ca677b309e5ed1171f8666fe7
ms.sourcegitcommit: b5bad4eeb5cdd0c2a7b639442656c306e8b5853b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65814010"
---
# <a name="mr-learning-base-module---project-initialization-and-first-application"></a>MR-Learning-Basis-Modul – Projektinitialisierung und der ersten Anwendung

In dieser ersten Lektion werden erfahren Sie, einige der Funktionen, die das Mixed Reality-Toolkit bietet, starten Ihre erste Anwendung für die HoloLens-2, und es auf dem Gerät bereitstellen.

## <a name="objectives"></a>Ziele

* Optimieren von Unity für die Entwicklung für HoloLens.
* Importieren von Objekten aus, und richten Sie die Szene.
* Visualisierung der räumlichen Mesh Hand Gitter und den Zähler für die Framerate.

## <a name="instructions"></a>Anweisungen

### <a name="create-new-unity-project"></a>Erstellen der neues Unity-Projekt

1. Starten Sie Unity.
2. Wählen Sie **New** aus.
![Lektion 1 Chapter1 Schritt 2](images/Lesson1Chapter1Step2.JPG)
3. Geben Sie einen Projektnamen ein (z.B.) "MixedRealityBase").
![Lektion 1 Chapter1 Schritt 3](images/Lesson1Chapter1Step3.JPG)
4. Geben Sie einen Speicherort zum Speichern des Projekts ein.
![Lektion 1 Chapter1 Schritt 4](images/Lesson1Chapter1Step4.JPG)
5. Stellen Sie sicher, dass das Projekt nastaven NA hodnotu **3D**.
![Lektion 1 Chapter1 Schritt 5](images/Lesson1Chapter1Step5.JPG)
6. Klicken Sie auf **erstellen Projekt**.
![Lektion 1 Chapter1 Schritt 6](images/Lesson1Chapter1Step6.JPG)

### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Konfigurieren des Unity-Projekts für Windows Mixed Reality

1. Öffnen Sie das Fenster "Build", indem Sie die Datei > Buildeinstellungen.
![Lektion 1 Kapitel4 Schritt 1](images/Lesson1Chapter4Step1.JPG)
2. Wechseln Sie zu "Universal Windows Platform", durch Auswählen von "Universal Windows Platform", und klicken Sie dann auf die Schaltfläche mit den "Plattform wechseln", um die Plattformen zu wechseln. Apps für HoloLens 2 sind erforderlich, um universelle Windows-Plattform (UWP) werden.
![Lektion 1 Kapitel4 Schritt 2](images/Lesson1Chapter4Step2.JPG)
3. Aktivieren Sie virtuelle Realität, durch Klicken auf die Player-Einstellungen im Fenster zu erstellen, und aktivieren Sie dann im Inspektor Bereich das Kontrollkästchen "Virtuelle Realität unterstützt" unter "XR-Einstellungen" wie in der folgenden Abbildung dargestellt. Bitte beachten Sie, dass Sie möglicherweise das Fenster von "Buildeinstellungen" aus dem Weg zu ziehen, um den Bereich der Eigenschaftenanalyse finden Sie unter. Das Kontrollkästchen "Virtuelle Realität unterstützt" gilt auch für Mixed Reality / AR Headsets, da dies bezieht sich auf die Aktivierung der stereoskopische Vision (Rendering verschiedene Bilder für jedes Auge.) ![Lektion 1 Kapitel4 Schritt 3](images/Lesson1Chapter4Step3.JPG)
4. Überprüfen Sie, dass das Kontrollkästchen "Räumliche Wahrnehmung" im Abschnitt mit Funktionen, können Sie auch unter "Einstellungen" Veröffentlichen aktiviert ist, im gleichen Bereich Inspector. Räumliche Wahrnehmung ermöglicht uns, die räumliche Zuordnung Mesh auf ein mixed Reality-Gerät, z.B. die HoloLens-2 zu visualisieren. Veröffentlichungseinstellungen werden in den Inspektor im Bereich mit über "XR-Einstellungen" und unter "Andere Einstellungen." gefunden.
![Lektion 1 Kapitel4 Schritt 4](images/Lesson1Chapter4Step4.JPG)

> HINWEIS: In diesem Abschnitt nicht verwendet wird, enthalten einige allgemeine Funktionen, die Sie aktivieren möchten, können Mikrofon (für Sprachbefehle) und InternetClient (für die Verbindung mit den Diensten, die eine Netzwerkverbindung erforderlich ist)

### <a name="import-the-mixed-reality-toolkit"></a>Importieren Sie die Mixed Reality-Toolkit

1. Herunterladen der [Mixed Reality-Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage) Unity-Paket, und speichern Sie es in einem Ordner auf Ihrem PC.

2. Importieren Sie das Mixed Reality-Toolkit-Paket durch Klicken auf die Assets > Importieren > benutzerdefiniertes Paket. Suchen Sie das in Schritt 1 heruntergeladene Mixed Reality-Toolkit-Paket aus, und öffnen Sie sie um den Importvorgang zu starten. Warten Sie einige Minuten, bis der Importvorgang an.
    ![Lektion 1 Chapter2 Step2a](images/Lesson1Chapter2Step2a.JPG) ![Lektion 1 Chapter2 Step2b](images/Lesson1Chapter2Step2b.JPG)

3. Klicken Sie im nächsten Popup-Fenster auf "Importieren", um zu beginnen, importieren das Mixed Reality-Toolkit. Stellen Sie sicher, dass alle Elemente aktiviert sind, wie in der Abbildung dargestellt. Wenn Sie ein Popup-Dialogfeld aufgefordert, die zum Anwenden der Einstellungen der Standardrichtlinie für Mixed Reality-Toolkit angezeigt wird, klicken Sie auf "Übernehmen".
    ![Lektion 1 Chapter2 Schritt 3](images/Lesson1Chapter2Step3.JPG) ![Lektion 1 Chapter2 Schritt 3](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Konfigurieren des Toolkits Mixed Reality

1. Konfigurieren des gemischten Toolkits durch Auswahl aus der Menüleiste Mixed Reality-Toolkit > konfigurieren. Wenn Sie dieses Menüelement nicht nach dem Importieren des Toolkits mixed Reality angezeigt wird, starten Sie Unity neu.
![Lektion 1 Chapter3 Schritt 1](images/Lesson1Chapter3Step1.JPG)
2. Die Szene wird nun mehrere neue Elemente und Änderungen aus dem Mixed Reality-Toolkit enthalten. Durch Klicken auf die Datei zu Ihrer Szene unter einem anderen Namen speichern > Speichern unter, und geben Sie Ihre Szene einen Namen, z. B. BaseScene. Halten Sie Ihre Szene organisiert, indem Sie sie in den Ordner "Szenen" im Ordner "Assets" Ihres Projekts zu speichern.
![Lektion 1 Chapter3 Step2a](images/Lesson1Chapter3Step2a.JPG)
![Lektion 1 Chapter3 Step2b](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>Erstellen Sie Ihre Anwendung auf Ihrem Gerät

1. Wenn Sie das Fenster "erstellen" aus den vorherigen Abschnitten geschlossen haben, öffnen Sie das Einstellungsfenster für den Build erneut dazu auf die Datei > Buildeinstellungen.
    ![Lektion 1 Chapter5 Schritt 1](images/Lesson1Chapter5Step1.JPG)

2. Stellen Sie sicher, dass die Szene, die Sie testen möchten in der Liste "Szenen in Build" ist, indem Sie auf die Schaltfläche "Open Szenen hinzufügen" auf.

3. Drücken Sie die Schaltfläche "Build", um den Build zu starten.
    ![Lektion 1 Chapter5 Schritt 3](images/Lesson1Chapter5Step3.JPG)

4. Erstellen Sie und benennen Sie einen neuen Ordner für Ihre Anwendung. In der Abbildung unten, einen Ordner mit dem Namen wurde "App" erstellt, um die Anwendung enthalten. Klicken Sie auf "Ordner auswählen", um das Gebäude, um den neu erstellten Ordner zu beginnen. Nachdem der Build abgeschlossen wurde, können Sie das Fenster "Buildeinstellungen" in Unity zu schließen. 
    ![Lektion 1 Chapter5 Schritt 4](images/Lesson1Chapter5Step4.JPG)

  > HINWEIS: Wenn der Buildvorgang fehlschlägt, versuchen Sie es erneut erstellen oder Neustarten von Unity und erneut erstellen. Wenn Sie eine Fehlermeldung, wie z. B. angezeigt "Fehler: CS0246 = Name Typ- oder Namespacename "XX" wurde nicht gefunden (fehlt eine using-Direktive oder ein Assemblyverweis?) ", dann Sie möglicherweise installieren müssen [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)
  >

5. Nachdem der Build abgeschlossen ist, öffnen Sie den neu erstellten Ordner, die Ihre neu erstellte Anwendungsdateien enthält. Klicken Sie mit der Doppelklicken auf die Projektmappe "MixedRealityBase.sln" (oder dem entsprechenden Namen ein, wenn Sie einen alternativen Namen für Ihr Projekt verwendet haben) auf die Projektmappendatei in Visual Studio zu öffnen.

  > Hinweis: Achten Sie darauf, dass Sie zum Öffnen des neu erstellten Ordners (d. h. die "App" Ordner, wenn Sie die Benennungskonventionen aus den vorherigen Schritten folgen), wird eine entsprechend benannten sln-Datei, Ordner, die nicht zu verwechseln mit der SLN-Datei im Ordner "Build" vorhanden sein. 

![Lektion 1 Chapter5 Schritt 5](images/Lesson1Chapter5Step5.JPG)

  > Hinweis: Wenn Visual Studio fordert Sie zur Installation neuer Komponenten, nehmen Sie einen Moment Zeit, um sicherzustellen, dass alle erforderliche Komponenten, als installiert sind im angegebenen [der Seite "Installieren der Tools"](install-the-tools.md)

6. Schließen Sie Ihre HoloLens 2 an Ihrem PC über das USB-Kabel an. Während diese Lektion-Anweisungen wird vorausgesetzt, Sie werden einen Testsatz mit einem HoloLens-2-Gerät bereitstellen werden, können Sie auch zum Bereitstellen der [Emulator für HoloLens 2](using-the-hololens-emulator.md) oder erstellen eine [app-Paket für das querladen](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. Stellen Sie vor dem Erstellen der App auf Ihrem Gerät sicher, dass das Gerät im Entwicklermodus befindet. Ist dies zum ersten Mal die HoloLens-2. bereitstellen, kann Sie von Visual Studio aufgefordert, Ihre HoloLens 2 mit einer Pin zu koppeln. Führen Sie [diese Anweisungen](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) Wenn müssen Sie den Entwicklermodus aktivieren oder mit Visual Studio koppeln.

8. Konfigurieren von Visual Studio zum Erstellen von auf Ihrer HoloLens 2 durch Auswählen der "Release"-Konfiguration und die Architektur "ARM".
    ![Lektion 1 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)

9. Der letzte Schritt ist die Erstellung auf Ihrem Gerät durch Auswählen von Debuggen > Starten ohne Debugging. Auswählen von "Starten ohne Debugging" bewirkt, dass die Anwendung sofort auf Ihrem Gerät nach einem erfolgreichen Build, jedoch ohne Debugging-Informationen, die in Visual Studio angezeigt werden. Dies bedeutet auch, dass Sie das USB-Kabel nicht getrennt werden können, während die Anwendung auf Ihrem HoloLens 2 ausgeführt wird, ohne die Anwendung beenden zu müssen. Sie können auch auswählen, erstellen > Projektmappe bereitstellen, um auf Ihrem Gerät bereitstellen, ohne die Anwendung automatisch gestartet.
    ![Lektion 1 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben nun Ihre erste HoloLens-2-Anwendung nun bereitgestellt. Wie Sie in Schritt für Schritt, sehen Sie eine räumliche Mesh alle Oberflächen abzudecken, die durch die HoloLens-2 erkannt wurde, haben. Darüber hinaus sollte Indikatoren auf Ihre Hände und die Finger für manuell nachverfolgen und einen Frame Rate-Zähler für die Überwachung auf die Leistung der app angezeigt werden. Dies sind nur einige der grundlegenden Komponenten implementiert, standardmäßig mit dem Mixed Reality-Toolkit enthalten. Beginnen Sie in den Lektionen werden mehr Inhalte und Interaktivität zu Ihrer Szene, hinzufügen, sodass Sie vollständig auf die Funktionen des die HoloLens-2 und das Mixed Reality-Toolkit untersuchen können.

>Hinweis: Sie werden beschrieben, wie zum Umschalten der Indikator Frame mit einem Befehl Voice in [Lektion 5](mrlearning-base-ch5.md)

[Nächste Lektion: Die Benutzeroberfläche manuell nachverfolgen und Mixed Reality-Toolkit-Konfiguration](mrlearning-base-ch2.md)
