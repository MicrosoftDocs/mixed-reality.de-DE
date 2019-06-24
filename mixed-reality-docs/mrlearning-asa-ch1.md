---
title: MR Learning ASA-Modul Azure räumliche Anker für HoloLens 2
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 7843e4de014fe14d7c40b5e6d68f72ea45b4df9e
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326555"
---
# <a name="getting-started-with-azure-spatial-anchors-on-hololens-2"></a>Erste Schritte mit Azure räumliche Textmarken auf HoloLens 2

Das zweite Modul des Lernprogramms 2 HoloLens Herzlich Willkommen! Bevor Sie beginnen, stellen sicher, dass alle von der [Voraussetzungen](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) abgeschlossen sind. Wenn Sie nicht die erste abgeschlossen haben [Basismodul](mrlearning-base.md) noch, es wird dringend empfohlen, dass Sie zuerst abschließen. Wenn Sie ein neues Unity-Projekt beginnen, befolgen Sie die neuen Schritte bei der projekterstellung in das [Basismodul](mrlearning-base.md). 

## <a name="objectives"></a>Ziele

* Grundlagen der Entwicklung mit Azure räumliche Anker mit der HoloLens 2

* Erstellen, hochladen und Herunterladen von räumlichen Anker

  

## <a name="instructions"></a>Anweisungen

### <a name="downloading-and-importing-assets"></a>Herunterladen und Importieren von Assets
Bevor Sie beginnen, müssen Sie herunterladen und importieren die folgenden Ressourcen:

[Azure Spatial Anchors](https://github.com/azure/azure-spatial-anchors-samples/releases)

[MR Base Modul Ressourcenpaket](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1)

[ASA-Modul Ressourcenpaket](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_B2)

[Mixed Reality-Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

> Hinweis: Siehe Schritt 5, um spezifische Anweisungen zum Importieren der räumlichen Anker von Azure, Schritt 6 für spezifische Anweisungen für das Modul MR Base Ressourcenpaket und Schritte 3 und 4 für spezifische Anweisungen für das Mixed Reality-Toolkit.

1. Erstellen Sie eine neue Szene in Ihrem Projekt ein. Klicken Sie mit der rechten Maustaste auf Ihre Szene-Ordner, klicken Sie auf "erstellen", klicken Sie dann die Szene. Benennen Sie die neue Szene "ASALearningmodule."

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. Doppelklick zum "ASALearningmodule" finden Sie einige vordefinierte Elemente, die zusammen mit der neuen Szene angezeigt. 
3. Konfigurieren Sie die Szene für mixed Reality-Entwicklung. 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> Hinweis: Daraufhin wird ein Popupfenster, die besagt, "Sie müssen Auswählen einer Datei für das Mixed Reality-Toolkit." Durch Klicken auf "Ok" gelangen Sie mit Schritt 4 fort.

4. Wählen Sie bei der Auswahl einer Datei für das Mixed Reality-Toolkit, "DefaultMixedRealityToolkitConfigurationProfile."

   > Hinweis: Wenn Sie eigene Konfiguration Profil gerne, die stattdessen verfügen.

![module2chapter1step4im](images/module2chapter1step4im.PNG)

Jetzt ist die Szene für mixed Reality konfiguriert. Stellen Sie sicher, dass Sie Ihre Szene speichern (hierzu entweder Steuerelement / Befehl + S, oder klicken Sie auf die Datei, und klicken Sie auf Speichern). 

5. Importieren der [Azure räumliche Anker](https://github.com/azure/azure-spatial-anchors-samples/releases). Um räumliche Anker verwenden zu können, müssen Sie dieses Objekt importieren. Also, klicken Sie auf den Link oben, und klicken Sie mit der rechten Maustaste auf "AzureSpatialAnchors.unitypackage." Klicken Sie auf "Ziel speichern unter", und speichern Sie ihn auf Ihrem Computer. 

   ![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

   Klicken Sie dann, nachdem es gespeichert ist, zurück zu Unity, klicken Sie auf "Ressourcen" wechseln Sie zu "Paket importieren", klicken Sie dann auf "benutzerdefiniertes Paket..." Dateien Ihres Computers werden geöffnet. Sobald sie, suchen, in dem Sie das räumliche Anker der Azure-Paket gespeichert und wählen Sie ihn. Klicken Sie dann auf "Öffnen".

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   Jetzt wird ein Popup bietet eine Liste der Tools und Einstellungen aufgefordert werden, was zum Importieren vorhanden sein. Wählen Sie ***alle*** der verfügbaren Optionen, klicken Sie dann auf "Importieren".

   ![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

   > Hinweis: Es dauert einige Minuten, bis so importieren Sie etwas Geduld. 

   6. Import [MR Base Modul Ressourcenpaket](https://github.com/microsoft/mixedrealitylearning/releases/tag/v1.1) weiter. Ähnlich wie Schritt 5 Klicken Sie auf den Link oben, klicken Sie mit der rechten Maustaste auf "BasemoduleAssetsV1 1.unitypackage", und klicken Sie auf "Ziel speichern unter", und speichern Sie ihn auf Ihrem Computer.

   ![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

   > Tipp: Speichern Sie alle diese Ressourcen im selben Ordner, sodass sie leichter sind zu finden und haben Zugriff auf. Alles bleibt schön und organisierten.

   Genau, wie Sie Schritt 5: Wechseln Sie zurück in Unity, klicken Sie auf "Ressourcen", zeigen Sie auf "Paket importieren", und klicken Sie auf "benutzerdefiniertes Paket..." Dateien Ihres Computers sollte in diesem Fall angezeigt werden. so wechseln Sie zu, in dem Sie das Basismodul Ressourcenpaket gespeichert und wählen Sie es aus. Klicken Sie dann auf "Öffnen".

   ![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

   > Hinweis: möglicherweise werden weitere Ressourcen, die weiter unten in diesem Modul erforderlich. Um alle Ressourcen, die ab diesem Punkt erwähnt importieren, gehen Sie wie folgt vor. 

7. Importieren Sie das ASA-Modul Pack mit den gleichen Ansatz wie die vorherige Pakete importieren.

### <a name="configuring-your-scene"></a>Konfigurieren Ihrer Szene

In diesem Abschnitt werden wir hinzufügen prefabs (Vorlagen) und Skripts in der Szene, um eine Reihe von Schaltflächen zu erstellen, in denen die Grundlagen der Verhalten von sowohl räumliche Anker Azure als auch lokale Anker in einer Anwendung veranschaulicht.

7. Klicken Sie in der Registerkarte "Projekt" unter dem Ordner "Ressourcen" auf "ASAmoduleAssets." Nach dem ausgewählten sehen Sie 2 prefabs (Vorlagen), "ButtonParent" und "ParentAnchor."

![module2chapter1step7im](images/module2chapter1step7im.PNG)

8. Ziehen Sie beide die prefabs (Vorlagen) in der Szene aus. 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

9. Doppelklicken Sie auf der übergeordneten Anker auf, um es auszuwählen. Möglicherweise müssen Sie die Ansicht zum Anzeigen der gesamten Szene Ihrer Szene so passen Sie nach Bedarf anpassen.

    Machen Sie sich mit den ParentAnchor Prefab. Das spielobjekt mit dem Namen "ParentAnchor" ist derzeit einem farbigen Cube zu Demonstrationszwecken. Schließlich wird Ausblenden des Cubes und platzieren Sie unsere Inhalte als untergeordnetes Element der ParentAnchor. Diese Prefab umfasst das AzureSpatialAnchorsDemoWrapper.cs-Skript (mit dem ASA-SDK enthalten) und das ASAmoduleScript.cs-Skript (als Teil dieses Moduls enthalten) auf das ParentAnchor-Objekt. 

10. Konfigurieren Sie die Schaltflächen. Unter den Prefab ParentAnchor sehen Sie mehrere bezeichnete Schaltflächen. Diese Schaltflächen werden aus der MRTKs PressableButton prefabs (Vorlagen) erstellt. Erfahren Sie mehr über das Erstellen von Pressable Schaltflächen aus der [Basismodul](mrlearning-base-ch2.md). Fügen Sie für jede Schaltfläche ein Ereignis, das ausgelöst wird, wenn der Benutzer drückt oder die Schaltfläche entsprechend der folgenden Liste ausgewählt. 

- Erstellen Sie für die Schaltfläche mit dem Namen "StartAzureSession" ein neues Ereignis unter den Ereignistrigger "Gedrückt" als auch den Ereignistrigger "Click". Ziehen Sie das ParentAnchor-Objekt in das leere Feld ein, und weisen Sie die StartAzureSession()-Methode des Objekts ParentAnchor ASAmoduleScript Komponente.

  ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

  ![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

  ![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- Erstellen Sie für die Schaltfläche mit dem Namen "StopAzureSession" ein neues Ereignis unter den Ereignistrigger "Gedrückt" als auch den Ereignistrigger "Click". Ziehen Sie das ParentAnchor-Objekt in das leere Feld ein, und weisen Sie die StopAzureSession()-Methode des Objekts ParentAnchor ASAmoduleScript Komponente.

- Erstellen Sie für die Schaltfläche mit dem Namen "CreateAnchor" ein neues Ereignis unter den Ereignistrigger "Gedrückt" als auch den Ereignistrigger "Click". Ziehen Sie das ParentAnchor-Objekt in das leere Feld ein, und weisen Sie die CreateAzureAnchor()-Methode des Objekts ParentAnchor ASAmoduleScript Komponente.

- Erstellen Sie für die Schaltfläche mit dem Namen "Starten suchen für Anker" ein neues Ereignis unter den Ereignistrigger "Gedrückt" als auch den Ereignistrigger "Click". Ziehen Sie das ParentAnchor-Objekt in das leere Feld ein, und weisen Sie die FindAzureAnchor()-Methode des Objekts ParentAnchor ASAmoduleScript Komponente.

- Erstellen Sie für die Schaltfläche mit dem Namen "DeleteAzureAnchor" ein neues Ereignis unter den Ereignistrigger "Gedrückt" als auch den Ereignistrigger "Click". Ziehen Sie das ParentAnchor-Objekt in das leere Feld ein, und weisen Sie die DeleteAzureAnchor()-Methode des Objekts ParentAnchor ASAmoduleScript Komponente.

- Erstellen Sie für die Schaltfläche mit dem Namen "Lokaler Anker löschen" ein neues Ereignis unter den Ereignistrigger "Gedrückt" als auch den Ereignistrigger "Click". Ziehen Sie das ParentAnchor-Objekt in das leere Feld ein, und weisen Sie die RemoveLocalAnchor()-Methode des Objekts ParentAnchor ASAmoduleScript Komponente.

### <a name="build-and-demonstrate-base-application"></a>Erstellen Sie und zeigen Sie die grundlegende Anwendung

Ihrer Szene ist jetzt konfiguriert, um die Grundlagen von Azure räumliche Anker zu demonstrieren wir erstellen und führen Sie das grundlegende Verhalten von Azure räumliche Anker vor. 

1. Wenn Sie das Fenster „Buildeinstellungen“ aus den vorherigen Abschnitten geschlossen haben, öffnen Sie das Fenster „Buildeinstellungen“ erneut, indem Sie zu „Datei“ > „Buildeinstellungen“ wechseln.
    ![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)

2. Stellen Sie sicher, dass die Szene, die Sie testen möchten, in der Liste „Szenen in Build“ enthalten ist, indem Sie auf die Schaltfläche „Offene Szenen hinzufügen“ klicken.

3. Klicken Sie auf die Schaltfläche „Erstellen“, um den Buildprozess zu starten.
    ![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)

4. Erstellen und benennen Sie einen neuen Ordner für Ihre Anwendung. In der folgenden Abbildung können Sie sehen, dass ein Ordner mit dem Namen „App“ erstellt wurde, der die Anwendung enthalten soll. Klicken Sie auf „Ordner auswählen“, um mit der Erstellung im neu erstellten Ordner zu beginnen. Nach Abschluss der Erstellung (des Buildvorgangs) können Sie in Unity das Fenster „Buildeinstellungen“ schließen. 
    ![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)

  > HINWEIS: Wenn der Vorgang fehlschlägt, wiederholen Sie den Buildvorgang, oder starten Sie Unity neu, und wiederholen Sie dann den Buildvorgang. Wenn Sie eine Fehlermeldung, wie z. B. angezeigt "Fehler: CS0246 = der Zeichenkette oder Namespace-Name "XX" wurde nicht gefunden (fehlt eine using-Direktive oder ein Assemblyverweis?) ", dann Sie möglicherweise installieren müssen [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) 
  >

5. Öffnen Sie nach Abschluss des Buildvorgangs den neu erstellten Ordner, der Ihre neu erstellten Anwendungsdateien enthält. Doppelklicken Sie auf die Projektmappe „MixedRealityBase.sln“ (oder auf den entsprechenden Namen, wenn Sie einen alternativen Namen für Ihr Projekt verwendet haben), um die Projektmappendatei in Visual Studio zu öffnen.

  > Hinweis: Achten Sie darauf, dass Sie den neu erstellten Ordner öffnen (also den Ordner „App“, wenn Sie die Namenskonventionen in den vorherigen Schritten befolgt haben), weil außerhalb dieses Ordners noch eine SLN-Datei mit einem ähnlichen Namen vorhanden ist, die nicht mit der SLN-Datei im Buildordner verwechselt werden darf. 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

  > Hinweis: Wenn visual Studio aufgefordert werden, um die neuen Komponenten installieren, nehmen Sie einen Moment Zeit, um sicherzustellen, dass alle erforderlichen Komponenten installiert sind wie in bestimmten [der Seite "Installieren der Tools"](install-the-tools.md) 

6. Schließen Sie das HoloLens 2-Gerät über das USB-Kabel an Ihren PC an. Während diese Lektion-Anweisungen wird vorausgesetzt, Sie werden einen Testsatz mit einem HoloLens-2-Gerät bereitstellen werden, können Sie auch zum Bereitstellen der [Emulator für HoloLens 2](using-the-hololens-emulator.md) oder erstellen eine [app-Paket für das querladen](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. Stellen Sie vor dem Erstellen der App auf Ihrem Gerät sicher, dass sich das Gerät im Entwicklermodus befindet. Wenn das Ihre erste Bereitstellung auf dem HoloLens 2-Gerät ist, werden Sie möglicherweise von Visual Studio aufgefordert, Ihr HoloLens 2-Gerät mit einer PIN zu koppeln. Folgen Sie [diesen Anweisungen](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio), wenn Sie den Entwicklermodus aktivieren oder das Gerät mit Visual Studio koppeln müssen.

8. Konfigurieren Sie Visual Studio für die Erstellung auf Ihrem HoloLens 2-Gerät, indem Sie die Konfiguration „Release“ und die Architektur „ARM“ auswählen.
    ![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)
    
9. Der letzte Schritt ist die Erstellung auf Ihrem Gerät durch Auswählen von Debuggen > Starten ohne Debugging. Wenn Sie „Starten ohne Debuggen" auswählen, wird die Anwendung sofort nach einem erfolgreichen Buildvorgang auf Ihrem Gerät gestartet, ohne dass jedoch Debuginformationen in Visual Studio angezeigt werden. Dies bedeutet auch, dass Sie das USB-Kabel entfernen können, während Ihre Anwendung auf Ihrem HoloLens 2-Gerät ausgeführt wird, ohne dass die Anwendung beendet wird. Sie können auch „Build“ > „Projektmappe bereitstellen“ auswählen, um die Anwendung auf Ihrem Gerät bereitzustellen, ohne dass sie automatisch gestartet wird.
    ![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)
    
10. Wenn die Anwendung auf Ihrem Gerät ausgeführt wird, führen Sie die auf dem Bildschirm Anweisungen. Drücken Sie die Szene Schaltflächen für die folgenden Schritte aus.
    
    ![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. Starten Sie die Azure räumliche Anker-Sitzung.
    
    2. Verschieben Sie den Cube an einen anderen Speicherort aus.
    
    3. Speichern Sie die Azure räumliche Anker am Speicherort des Cubes.
    
    4. Beenden Sie die Azure räumliche Anker-Sitzung.
    
    5. Entfernen Sie den lokalen Anker für den Cube, die dem Benutzer ermöglichen, die den Cube zu verschieben.
    6. Verschieben Sie den Cube, die an anderer Stelle.
    
    7. Starten Sie Azure räumliche Anker-Sitzung.
    
    8. Suchen Sie Azure räumliche Anker.
    (jetzt Cube zurück an den ursprünglichen Ort gespeichert werden sollen können Sie sie bei der Erstellung des Ankers).
    9. Löschen Sie die Azure räumliche Anker.
    
    10. Azure-Sitzung zu beenden.

### <a name="anchoring-an-experience"></a>Eine Benutzeroberfläche-Verankerung

In den vorherigen Abschnitten haben Sie die Grundlagen der Azure räumliche Anker. Wir haben einen Cube verwendet, um darzustellen, und das Spiel übergeordnete-Objekt, mit dem angefügten Anker zu visualisieren. In diesem Abschnitt Sie Wiill erfahren Sie, wie eine gesamte Erfahrung verankert, indem Sie es als untergeordnetes Element des Objekts ParentAnchor platzieren. In diesem Beispiel verwenden wir die Mondkalender Modulassembly-Demo-app, die während der erstellten [Basismodul Lektion 6](mrlearning-base-ch6.md).

1. Suchen Sie nach der Prefab Mondkalender Modul Assembly abgeschlossen, und ziehen Sie es in Ihrer Hierarchie als untergeordnetes Element der AnchorParent "gameobject", wie in der folgenden Abbildung dargestellt.

   ![module2chapter1step11](images/module2chapter1step11im.PNG)

2. Positionieren Sie die Modul-Assembly-Erfahrung so, dass der Cube noch verfügbar gemacht wird, wie in der folgenden Abbildung dargestellt. In der Anwendung können Benutzer die gesamte Benutzeroberfläche neu anordnen, indem den Cube zu verschieben. 

   ![module2chapter1step12im](images/module2chapter1step12im.PNG)

   > Hinweis: Es gibt eine Vielzahl von Erfahrung benutzerflows für Umgebungen, einschließlich der Verwendung einer Schaltfläche auf Sie ein-/Ausschalten eines umgebenden Felds an, das die Benutzeroberfläche umgibt, verwenden Sie eine Umstellung der Reihenfolge Objekttyp (z. B. den Cube in diesem Schritt verwendet), der Position und Drehung Gizmos Neupositionieren , und vieles mehr.

## <a name="congratulations"></a>Herzlichen Glückwunsch!
In dieser Lektion haben Sie die Grundlagen der Azure räumliche Anker. In dieser Lektion werden Sie mit der mehrere Schaltflächen, sodass Sie untersuchen die verschiedenen erforderlichen Schritte zum Starten und Beenden einer Azure-Sitzungs, und erstellen, hochladen und Herunterladen von Azure Anker auf einem einzelnen Gerät angegeben. In der nächsten Lektion erfahren wir, wie Sie Azure Anker-IDs in Ihrem HoloLens-2 für den Abruf, speichern, auch nachdem die Anwendung neu gestartet wird. Der Reihe werden Sie erfahren außerdem, wie zum Übertragen von Anker-IDs zwischen mehreren Geräten, räumlichen Ausrichtung zu erreichen und schließlich erfahren Sie, mehrere Benutzer freigegeben Sitzungen (in Kürze im Rahmen der gemeinsamen Modul.)

[Nächste Lektion: ASA Lektion 2](mrlearning-asa-ch2.md)

