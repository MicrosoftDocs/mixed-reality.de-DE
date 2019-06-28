---
title: MR Learning ASA-Modul Azure räumliche Anker für HoloLens 2
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: c120d22f955d366042bbcb9ac73eaa4f13dc20e9
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415276"
---
# <a name="getting-started-with-azure-spatial-anchors-on-hololens-2"></a>Erste Schritte mit Azure räumliche Anker für HoloLens 2

Willkommen Sie beim Lernprogramm 2 HoloLens für das zweite Modul. Bevor Sie beginnen, stellen sicher, dass alle von der [Voraussetzungen](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) abgeschlossen sind. Wenn Sie nicht die erste abgeschlossen haben [Basismodul](mrlearning-base.md) noch, wird empfohlen, dass Sie das Modul zuerst durchführen. Wenn Sie ein neues Unity-Projekt beginnen, befolgen Sie die neuen Schritte bei der projekterstellung in das [Basismodul](mrlearning-base.md). 

## <a name="objectives"></a>Ziele

* Grundlagen der Entwicklung mit Azure räumliche Anker mit der HoloLens 2

* Erstellen, hochladen und Herunterladen von räumlichen Anker

  

## <a name="instructions"></a>Anweisungen

### <a name="downloading-and-importing-assets"></a>Herunterladen und Importieren von assets
Laden Sie bevor Sie beginnen, und importieren Sie die folgenden Ressourcen:

[Azure Spatial Anchors](https://github.com/azure/azure-spatial-anchors-samples/releases)

[MR Base Modul Ressourcenpaket](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)

[ASA-Modul Ressourcenpaket](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_B2)

[Mixed Reality-Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

> Hinweis: Spezifische Anweisungen zum Importieren von räumlichen Anker von Azure, Schritt 6 spezifische Anweisungen für das Modul MR Base Ressourcenpaket und Schritte 3 und 4, um spezifische Anweisungen für Mixed Reality Toolkit (MRKT) finden Sie unter Schritt 5.

1. Erstellen Sie eine neue Szene in Ihrem Projekt ein. Klicken Sie mit der rechten Maustaste auf Ihre Szene-Ordner, klicken Sie auf "Erstellen", und klicken Sie dann auf Szene. Der Name der neuen Szene ASALearningmodule.

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. Doppelklicken Sie ASALearningmodule um einige vordefinierte Elemente, die zusammen mit der neuen Szene angezeigt werden, finden Sie unter. 
3. Konfigurieren Sie die Szene für mixed Reality-Entwicklung. 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> Hinweis: Daraufhin wird ein Popupfenster, die besagt, "Sie müssen Auswählen einer Datei für das Mixed Reality-Toolkit." Klicken Sie auf Ok klicken, gelangen Sie zu Schritt 4.

4. Bei der Auswahl einer Datei für die MRTK wählen Sie aus, DefaultMixedRealityToolkitConfigurationProfile.

   > Hinweis: Wenn Sie Ihre eigenen Profils verfügen, sollten Sie gerne, stattdessen verwenden.

![module2chapter1step4im](images/module2chapter1step4im.PNG)

Jetzt ist die Szene für mixed Reality konfiguriert. Stellen Sie sicher, dass Sie Ihre Szene speichern (hierzu entweder Steuerelement / Befehl + S oder klicken Sie auf die Datei, klicken Sie dann auf Speichern). 

5. Importieren der [Azure räumliche Anker](https://github.com/azure/azure-spatial-anchors-samples/releases). Um räumliche Anker verwenden zu können, müssen Sie dieses Objekt importieren. Klicken Sie auf den Link oben, und klicken Sie mit der rechten Maustaste auf AzureSpatialAnchors.unitypackage. Klicken Sie auf dem Ziel speichern unter, und speichern Sie es auf Ihrem Computer. 

   ![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

   Nachdem es gespeichert wurde, wechseln Sie zurück in Unity, klicken Sie auf Ressourcen, zum Paket importieren ausfallen. Klicken Sie dann auf benutzerdefiniertes Paket... Dateien Ihres Computers werden geöffnet. Wenn Sie diese ist, suchen, in dem Sie das räumliche Anker der Azure-Paket gespeichert, und wählen es. Klicken Sie dann auf Öffnen.

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   Ein Popupfenster wird eingeblendet, Providingg eine Liste der Tools und Einstellungen und gefragt, was Sie zu importieren. Wählen Sie ***alle*** der verfügbaren Optionen, klicken Sie auf importieren.

   ![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

   > Hinweis: Geduld, dauert es einige Minuten, bis zu importieren. 

   6. Import [MR Base Modul Ressourcenpaket](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1) weiter. Klicken Sie auf den Link oben viel wie in Schritt 5. Klicken Sie dann BasemoduleAssetsV1 1.unitypackag, mit der rechten Maustaste und klicken Sie auf Ziel speichern unter, und speichern Sie es auf Ihrem Computer.

   ![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

   > Tipp: Speichern Sie alle diese Ressourcen im selben Ordner, sodass sie leichter sind zu finden und haben Zugriff auf. Er hält alles schön und organisiert.

   Nur wie in Schritt 5 wechseln Sie zurück, Unity, klicken Sie auf Objekte und zeigen Sie auf Paket importieren. Klicken Sie auf benutzerdefiniertes Paket... Dateien Ihres Computers werden erneut angezeigt. Wechseln Sie zu, in dem Sie das Basismodul Ressourcenpaket gespeichert. und es auswählen. Klicken Sie auf "Öffnen".

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   > Hinweis: Es gibt möglicherweise weitere Ressourcen, die weiter unten in diesem Modul erforderlich. Um alle Ressourcen, die ab diesem Punkt erwähnt importieren, gehen Sie wie folgt vor. 
                                                                                                                                                                                                                    
7. Importieren Sie die ASA-Modul-Bestätigung, die mit den gleichen Ansatz wie die vorherige Pakete importieren.

### <a name="configuring-your-scene"></a>Konfigurieren Ihrer Szene

In diesem Abschnitt werden wir prefabs (Vorlagen) und Skripts hinzufügen, in der Szene, um eine Reihe von Schaltflächen zu erstellen, in denen die Grundlagen der Verhalten von sowohl räumliche Anker Azure als auch lokale Anker in einer Anwendung veranschaulicht.

7. Die Registerkarte "Projekt" unter dem Ordner "Assets" klicken Sie auf ASAmoduleAssets. Nachdem Sie ausgewählt haben, sehen Sie zwei prefabs (Vorlagen): ButtonParent und ParentAnchor.

![module2chapter1step7im](images/module2chapter1step7im.PNG)

8. Ziehen Sie die beiden prefabs (Vorlagen) in der Szene. 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

9. Doppelklicken Sie auf der übergeordneten Anker auf, um es auszuwählen. Möglicherweise müssen Sie Ihre Ansicht, um die gesamte Szene anpassen. Passen Sie Ihre Szene nach Bedarf.

    Machen Sie sich mit den ParentAnchor Prefab. Derzeit ist das spielobjekt mit dem Namen ParentAnchor, einen farbigen Cube zu Demonstrationszwecken. Schließlich wir ", ll, blenden Sie den Cube, und platzieren Sie unsere Inhalte als untergeordnetes Element der ParentAnchor. Diese Prefab umfasst das AzureSpatialAnchorsDemoWrapper.cs-Skript (mit dem ASA-SDK enthalten) und das ASAmoduleScript.cs-Skript, das als Teil dieses Modul mit dem ParentAnchor-Objekt enthalten. 

10. Konfigurieren Sie die Schaltflächen. Beachten Sie in das Prefab ParentAnchor mehrere bezeichnete Schaltflächen aus. Diese Schaltflächen werden aus der MRTKs PressableButton prefabs (Vorlagen) erstellt. Erfahren Sie mehr über das Erstellen von Pressable Schaltflächen aus der [Basismodul](mrlearning-base-ch2.md). Fügen Sie für jede Schaltfläche ein Ereignis, das ausgelöst wird, wenn der Benutzer drückt oder die Schaltfläche entsprechend der folgenden Liste ausgewählt. 

- Erstellen Sie für die Schaltfläche mit dem Namen StartAzureSession ein neues Ereignis unter den Ereignistrigger gedrückt als auch den Ereignistrigger klicken Sie auf. Ziehen Sie das ParentAnchor-Objekt in das leere Feld ein, und weisen Sie die StartAzureSession()-Methode des Objekts ParentAnchor ASAmoduleScript Komponente.

  ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

  ![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

  ![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- Erstellen Sie für den Namen der Schaltfläche, StopAzureSession ein neues Ereignis unter den Ereignistrigger gedrückt als auch den Ereignistrigger klicken Sie auf. Ziehen Sie das ParentAnchor-Objekt in das leere Feld ein, und weisen Sie die StopAzureSession()-Methode des Objekts ParentAnchor ASAmoduleScript Komponente.

- Erstellen Sie für die Schaltfläche mit dem Namen CreateAnchor ein neues Ereignis unter den Ereignistrigger gedrückt als auch den Ereignistrigger klicken Sie auf. Ziehen Sie das ParentAnchor-Objekt in das leere Feld ein, und weisen Sie die CreateAzureAnchor()-Methode des Objekts ParentAnchor ASAmoduleScript Komponente.

- Erstellen ein neues Ereignis unter der Schaltfläche gedrückt haben, für die Schaltfläche mit dem Namen, starten Sie möchten für Anker,"Event-Trigger als auch den Ereignistrigger klicken Sie auf. Ziehen Sie das ParentAnchor-Objekt in das leere Feld ein, und weisen Sie die FindAzureAnchor()-Methode des Objekts ParentAnchor ASAmoduleScript Komponente.

- Erstellen Sie für die Schaltfläche mit dem Namen DeleteAzureAnchor ein neues Ereignis unter den Ereignistrigger gedrückt als auch den Ereignistrigger klicken Sie auf. Ziehen Sie das ParentAnchor-Objekt in das leere Feld ein, und weisen Sie die DeleteAzureAnchor()-Methode des Objekts ParentAnchor ASAmoduleScript Komponente.

- Erstellen Sie für die Schaltfläche mit dem Namen, löschen Sie lokale Anker ein neues Ereignis unter den Ereignistrigger gedrückt als auch den Ereignistrigger klicken Sie auf. Ziehen Sie das ParentAnchor-Objekt in das leere Feld ein, und weisen Sie die RemoveLocalAnchor()-Methode des Objekts ParentAnchor ASAmoduleScript Komponente.

### <a name="build-and-demonstrate-base-application"></a>Erstellen Sie und zeigen Sie die Basis-Anwendung

Ihrer Szene ist jetzt konfiguriert, um die Grundlagen von Azure räumliche Anker zu demonstrieren wir erstellen und führen Sie das grundlegende Verhalten von Azure räumliche Anker vor. 

1. Wenn Sie das Fenster „Buildeinstellungen“ aus den vorherigen Abschnitten geschlossen haben, öffnen Sie das Fenster „Buildeinstellungen“ erneut, indem Sie zu „Datei“ > „Buildeinstellungen“ wechseln.
    ![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)

2. Stellen Sie sicher, dass die Szene, die Sie testen möchten Szenen in Build-Liste wird durch Klicken auf die Schaltfläche "Open Szenen hinzufügen".

3. Klicken Sie auf die Schaltfläche „Erstellen“, um den Buildprozess zu starten.
    ![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)

4. Erstellen und benennen Sie einen neuen Ordner für Ihre Anwendung. In der folgenden Abbildung wurde ein Ordner mit dem Namen App erstellt, um die Anwendung enthalten. Klicken Sie auf Ordner auswählen, um das Gebäude, um den neu erstellten Ordner zu beginnen. Nachdem der Build abgeschlossen wurde, können Sie die Einstellung erstellen schließen"Fenster in Unity. 
    ![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)

  > HINWEIS: Wenn der Vorgang fehlschlägt, wiederholen Sie den Buildvorgang, oder starten Sie Unity neu, und wiederholen Sie dann den Buildvorgang. Wenn Sie eine Fehlermeldung, wie z. B. angezeigt "Fehler: CS0246 = der Zeichenkette oder Namespace-Name "XX" wurde nicht gefunden (fehlt eine using-Direktive oder ein Assemblyverweis?). Sie müssen möglicherweise installieren [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) 
  >

5. Öffnen Sie nach Abschluss des Buildvorgangs den neu erstellten Ordner, der Ihre neu erstellten Anwendungsdateien enthält. Doppelklicken Sie in der the"MixedRealityBase.sln-Projektmappe oder dem entsprechenden Namen. Wenn Sie einen alternativen Namen für Ihr Projekt verwendet, um die Projektmappendatei in Visual Studio zu öffnen.

  > Hinweis: Achten Sie darauf, öffnen Sie den neu erstellten Ordner (d. h. den App-Ordner, wenn die Benennungskonventionen in den vorherigen Schritten folgen, werden eine entsprechend benannten sln-Datei, Ordner, die nicht zu verwechseln mit der SLN-Datei im Ordner "Build", da. 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

  > Hinweis: Wenn Visual Studio aufgefordert werden, um die neuen Komponenten installieren, nehmen Sie einen Moment Zeit, um sicherzustellen, dass alle erforderlichen Komponenten installiert sind wie in bestimmten [der Seite "Installieren der Tools"](install-the-tools.md) 

6. Schließen Sie das HoloLens 2-Gerät über das USB-Kabel an Ihren PC an. Während diese Lektion-Anweisungen wird vorausgesetzt, Sie werden einen Testsatz mit einem HoloLens-2-Gerät bereitstellen werden, können Sie auch zum Bereitstellen der [Emulator für HoloLens 2](using-the-hololens-emulator.md) oder erstellen eine [app-Paket für das querladen](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. Stellen Sie vor dem Erstellen der App auf Ihrem Gerät sicher, dass sich das Gerät im Entwicklermodus befindet. Wenn das Ihre erste Bereitstellung auf dem HoloLens 2-Gerät ist, werden Sie möglicherweise von Visual Studio aufgefordert, Ihr HoloLens 2-Gerät mit einer PIN zu koppeln. Führen Sie [diese Anweisungen](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) Wenn müssen Sie den Entwicklermodus aktivieren oder mit Visual Studio koppeln.

8. Konfigurieren von Visual Studio zum Erstellen von auf Ihrer HoloLens 2 durch Auswählen der Releasekonfiguration und der Architektur "RM".
    ![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)
   
9. Der letzte Schritt ist die Erstellung auf Ihrem Gerät durch Auswählen von Debuggen > Starten ohne Debugging. Auswählen von Starten ohne Debuggen, wird die Anwendung sofort auf Ihrem Gerät auf einen erfolgreichen Build Ithout Debugging-Informationen in Visual Studio angezeigt werden. Dies bedeutet auch, dass Sie das USB-Kabel entfernen können, während Ihre Anwendung auf Ihrem HoloLens 2-Gerät ausgeführt wird, ohne dass die Anwendung beendet wird. Sie können auch auswählen, erstellen > Projektmappe bereitstellen, um auf Ihrem Gerät bereitstellen, ohne die Anwendung automatisch gestartet.
    ![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)
    
10. gemäß den Anweisungen. Wenn die Anwendung auf Ihrem Gerät ausgeführt wird, führen Sie die auf dem Bildschirm Anweisungen. Drücken Sie die Szene Schaltflächen für die folgenden Schritte aus.
    
    ![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. Starten Sie die räumlichen Anker-Sitzung.
    
    2. Verschieben Sie den Cube an einen anderen Speicherort aus.
    
    3. Speichern Sie die Azure räumliche Anker am Speicherort des Cubes.
    
    4. Beenden Sie die Azure räumliche Anker-Sitzung.
    
    5. Entfernen Sie den lokalen Anker für den Cube, die dem Benutzer ermöglichen, die den Cube zu verschieben.
    6. Verschieben Sie den Cube, die an anderer Stelle.
    
    7. Starten Sie Azure räumliche Anker-Sitzung.
    
    8. Azure räumliche Aachors zu finden. 
    
    e, die Sie an der ursprünglichen Stelle Sie zurückkehren sollte platzieren Sie es bei der Erstellung des Ankers).
    9. Löschen Sie die Azure räumliche Anker.
    
    10. Azure-Sitzung zu beenden.

### <a name="anchoring-an-experience"></a>Eine Benutzeroberfläche-Verankerung

In den vorherigen Abschnitten haben Sie die Grundlagen der Azure räumliche Anker. Wir haben einen Cube verwendet, um darzustellen, und das Spiel übergeordnete-Objekt, mit dem angefügten Anker zu visualisieren. In diesem Abschnitt erfahren Sie, wie eine gesamte Erfahrung verankert, indem Sie es als untergeordnetes Element des Objekts ParentAnchor platzieren. In diesem Beispiel verwenden wir das Modul Mondkalender Assembly-beispielanwendung, die während der erstellten [Basismodul Lektion 6](mrlearning-base-ch6.md).

1. Suchen Sie nach der Prefab Mondkalender Modul Assembly abgeschlossen, und ziehen Sie es in Ihrer Hierarchie als untergeordnetes Element der AnchorParent "gameobject" wie in der folgenden Abbildung dargestellt.

   ![module2chapter1step11](images/module2chapter1step11im.PNG)

2. Position der Assembly des Moduls auftreten, damit der Cube noch verfügbar gemacht wird, wie in der folgenden Abbildung dargestellt. In der Anwendung können Benutzer die gesamte Benutzeroberfläche neu anordnen, indem den Cube zu verschieben. 

   ![module2chapter1step12im](images/module2chapter1step12im.PNG)

   > Hinweis: Es gibt eine Vielzahl von Erfahrung benutzerflows für Umgebungen, einschließlich der Verwendung einer Schaltfläche auf Sie ein-/Ausschalten eines umgebenden Felds an, das die Benutzeroberfläche umgibt, verwenden Sie eine Umstellung der Reihenfolge Objekttyp (z. B. den Cube in diesem Schritt verwendet), der Position und Drehung Gizmos Neupositionieren , und vieles mehr.

## <a name="congratulations"></a>Herzlichen Glückwunsch!
In dieser Lektion haben Sie die Grundlagen der Azure räumliche Anker. Diese Esson angegeben, dass Sie mehrere Schaltflächen, mit denen Sie die verschiedenen erforderlichen Schritte zum Starten und Beenden einer Azure-Sitzungs, und erstellen, hochladen und Herunterladen von Azure Anker auf einem einzelnen Gerät untersuchen. In der nächsten Lektion erfahren wir, wie Sie Azure Anker-IDs in Ihrem HoloLens-2 für den Abruf, speichern, auch nachdem die Anwendung neu gestartet wird. Während der Reihe erfahren Sie, auch zur Übertragung der Anker-IDs zwischen mehreren Geräten räumlichen Ausrichtung zu erreichen, und erfahren Sie mehr über mehrere Benutzer freigegeben Sitzungen (in Kürze im Rahmen der gemeinsamen Modul.)

[Nächste Lektion: ASA Lektion 2](mrlearning-asa-ch2.md)

