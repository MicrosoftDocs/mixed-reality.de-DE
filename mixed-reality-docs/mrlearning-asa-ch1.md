---
title: Mr Learning ASA-Modul Azure Spatial Anchor on hololens 2
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 391e797ad9cc8933b057366ab47a3f453c68723e
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485771"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Ersten Einstieg in Azure Spatial Anchor

Willkommen beim zweiten Modul der hololens 2-Tutorials. Bevor Sie beginnen, stellen Sie sicher, dass alle [Voraussetzungen](https://docs.microsoft.com/en-us/azure/spatial-anchors/quickstarts/get-started-unity-hololens) erfüllt sind. Wenn Sie das erste [Basismodul](mrlearning-base.md) noch nicht abgeschlossen haben, empfiehlt es sich, dieses Modul zuerst abzuschließen. Wenn Sie mit einem neuen Unity-Projekt beginnen, befolgen Sie die Schritte zum Erstellen eines neuen Projekts im [Basismodul](mrlearning-base.md). 

## <a name="objectives"></a>Ziele

* Erfahren Sie mehr über die Grundlagen der Entwicklung mit räumlichen Azure-Ankern mit hololens 2

* Erstellen, hochladen und herunterladen räumlicher Anker

## <a name="instructions"></a>Anweisungen

### <a name="downloading-and-importing-assets"></a>Herunterladen und Importieren von Assets
Bevor Sie beginnen, müssen Sie die folgenden Ressourcen herunterladen und importieren:

[Azure Spatial Anchors](https://github.com/azure/azure-spatial-anchors-samples/releases)

[Asset Pack für die Mr-Basismodule](https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2)

[Assetpaket des ASA-Moduls](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_1.1)

[Mixed Reality-Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/)

> Hinweis: In Schritt 5 finden Sie spezifische Anweisungen zum Importieren von Azure Spatial Anchor (Schritt 6) für spezifische Anweisungen zum Azure-Basismodul Asset Pack und die Schritte 3 bis 4 für spezifische Anweisungen zum Mixed Reality Toolkit (MRKT).

1. Erstellen Sie eine neue Szene in Ihrem Projekt. Klicken Sie mit der rechten Maustaste auf den Ordner Szene, klicken Sie auf Erstellen und dann auf Nennen Sie die neue Szene asalearningmodule.

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. Doppelklicken Sie auf asalearningmodule, um anzuzeigen, dass einige vordefinierte Elemente zusammen mit der neuen Szene angezeigt werden. 
3. Konfigurieren Sie die Szene für die Entwicklung in gemischter Realität. 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> Hinweis: Es wird ein Popup Fenster angezeigt, das besagt, dass Sie eine Datei für das Mixed Reality Toolkit auswählen müssen. Wenn Sie auf OK klicken, gelangen Sie zu Schritt 4.

4. Wenn Sie eine Datei für den mrtk auswählen, wählen Sie defaultmixedrealitytoolkitconfigurationprofile aus.

> Hinweis: Wenn Sie über ein eigenes Konfigurations Profil verfügen, können Sie dieses stattdessen verwenden.

![module2chapter1step4im](images/module2chapter1step4im.PNG)

Die Szene ist nun für gemischte Realität konfiguriert. Stellen Sie sicher, dass Sie Ihre Szene speichern (führen Sie dies entweder mit Control/Command + S aus, oder klicken Sie auf Datei, und klicken Sie dann auf Speichern). 

5. Importieren Sie die [räumlichen Azure-Anker](https://github.com/azure/azure-spatial-anchors-samples/releases). Um räumliche Anker verwenden zu können, müssen Sie dieses Asset importieren. Klicken Sie auf den Link oben, und klicken Sie mit der rechten Maustaste auf "azurespatialanchor. unitypackage". Klicken Sie auf Ziel speichern unter, und speichern Sie es auf Ihrem Computer. 

![module2chapter1step5aim](images/module2chapter1step5aim.PNG)

Wechseln Sie nach dem Speichern zurück in Unity, klicken Sie auf Assets, und klicken Sie dann auf Import Package. Klicken Sie dann auf benutzerdefiniertes Paket... Ihre Computerdateien werden geöffnet. Wenn dies der Fall ist, suchen Sie nach dem Speicherort des Azure Spatial Anchor-Pakets, und wählen Sie es aus. Klicken Sie anschließend auf Öffnen.

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

Daraufhin wird ein Popup Fenster mit einer Liste von Tools und Einstellungen angezeigt, und Sie werden gefragt, welche Informationen importiert werden müssen. Wählen Sie ***alle*** verfügbaren Optionen aus, und klicken Sie dann auf importieren.

![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

> Hinweis: Seien Sie geduldig, es dauert einige Minuten, bis der Import Vorgang abgeschlossen ist. 

6. Importieren Sie als nächstes [Mr Base Module https://github.com/microsoft/MixedRealityLearning/releases/tag/1.2) Asset Pack]. Klicken Sie ähnlich wie in Schritt 5 auf den obigen Link. Klicken Sie dann mit der rechten Maustaste auf BasemoduleAssetsV1 1. unitypackag, und klicken Sie auf Ziel speichern unter, und speichern Sie es auf Ihrem Computer.

![module2chapter1step6aim](images/module2chapter1step6aim.PNG)

> Tipp: Speichern Sie alle diese Objekte im gleichen Ordner, damit Sie leichter zu finden sind und auf Sie zugreifen können. Es bleibt alles schön und organisiert.

Gehen Sie wie in Schritt 5 zurück zu Unity, klicken Sie auf Assets, und zeigen Sie auf Import Package. Klicken Sie auf benutzerdefiniertes Paket... Die Computerdateien werden erneut angezeigt. Wechseln Sie zu dem Speicherort, an dem Sie das Basismodul-Asset Pack und wählen Sie Sie aus. Klicken Sie auf "Öffnen".

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

> Hinweis: Möglicherweise werden später in diesem Modul weitere Ressourcen benötigt. Führen Sie diese Schritte aus, um alle Objekte zu importieren, die ab diesem Punkt erwähnt werden. 

7. Importieren Sie das [ASA Module Pack](https://github.com/microsoft/MixedRealityLearning/releases/tag/ASA_1.1) mit dem gleichen Ansatz wie beim Importieren der vorherigen Pakete.

### <a name="configuring-your-scene"></a>Konfigurieren der Szene

In diesem Abschnitt fügen wir Prefabs und Skripts in die Szene ein, um eine Reihe von Schaltflächen zu erstellen, die die Grundlagen der Art und Weise darstellen, wie sich sowohl lokale Anker als auch räumliche Azure-Anker in einer Anwendung Verhalten.

8. Klicken Sie auf der Registerkarte Projekt unterhalb des Ordners Assets auf asamoduleassets. Nachdem Sie diese Option ausgewählt haben, werden Ihnen zwei Vorabinformationen angezeigt: Buttonparent und para Anker.

![module2chapter1step7im](images/module2chapter1step7im.PNG)

9. Ziehen Sie beide Prefabs in die Szene. 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

10. Doppelklicken Sie auf den übergeordneten Anker, um ihn auszuwählen. Möglicherweise müssen Sie Ihre Ansicht anpassen, um die gesamte Szene anzuzeigen. Passen Sie Ihre Szene nach Bedarf an.

Machen Sie sich mit der vorfab-vorfab vertraut. Derzeit ist das Game-Objekt mit dem Namen "", "", "", "". Schließlich blenden wir den Cube aus und platzieren den Inhalt als untergeordnetes Element des Parametern "Parser". Diese vorfab umfasst das AzureSpatialAnchorsDemoWrapper.cs-Skript (das im ASA SDK enthalten ist) und das ASAmoduleScript.cs-Skript, das als Teil dieses Moduls für das Objekt "objeanchor" enthalten ist. 

11. Konfigurieren von Schaltflächen. Beachten Sie unter der Schaltfläche buttonparent eine Reihe beschriftete Schaltflächen. Diese Schaltflächen werden aus den Prefabs von mrtk erstellt. Erfahren Sie mehr über das Erstellen von druckbaren Schaltflächen aus dem [Basismodul](mrlearning-base-ch2.md). Fügen Sie für jede Schaltfläche ein Ereignis hinzu, das ausgelöst wird, wenn der Benutzer die Schaltfläche entsprechend der nachstehenden Liste drückt oder auswählt. 

- Erstellen Sie für die Schaltfläche "startazuresession" ein neues Ereignis unter dem Ereignis auslösenden Ereignis-und dem On-Click-Ereignis-Auslösers. Ziehen Sie das Objekt "objeanchor" in das leere Feld, und weisen Sie die startazuresession ()-Methode aus der asamodulescript-Komponente des Objektanchor-Objekts zu.

![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- Erstellen Sie für den Schaltflächen Namen stopazuresession ein neues Ereignis unter dem Ereignis auslösenden Ereignis-und dem Click-Ereignis-auslöst. Ziehen Sie das Objekt "objeanchor" in das leere Feld, und weisen Sie die stopazuresession ()-Methode aus der asamodulescript-Komponente des Objektanchor-Objekts zu.

- Erstellen Sie für die Schaltfläche mit dem Namen "kreateanchor" ein neues Ereignis unter dem gedrückten Ereignis-und aktivierten Ereignis-Auslösers. Ziehen Sie das Objekt "objeanchor" in das leere Feld, und weisen Sie die Methode "Methode" "Methode" aus der Komponente "asamodulescript" des Objekts "Objektanchor" zu.

- Erstellen Sie für die Schaltfläche mit dem Namen nach Anker suchen, erstellen Sie ein neues Ereignis unter der Schaltfläche "Presse" und dem Ereignis Auslösers "bei Click". Ziehen Sie das Objekt "objeanchor" in das leere Feld, und weisen Sie die Methode "findazureanchor ()" aus der Komponente "asamodulescript" des Objekts "Objektanchor" zu.

- Erstellen Sie für die Schaltfläche mit dem Namen deleteazureanchor ein neues Ereignis unter dem gedrückten Ereignis-und aktivierten Ereignis-Auslösers. Ziehen Sie das Objekt "objeanchor" in das leere Feld, und weisen Sie die deleteazureanchor ()-Methode aus der asamodulescript-Komponente des Objektanchor-Objekts zu.

- Erstellen Sie für die Schaltfläche "lokalen Anker löschen" ein neues Ereignis unter dem gedrückten Ereignis-und aktivierten Ereignis-Auslösers. Ziehen Sie das Objekt "objeanchor" in das leere Feld, und weisen Sie die removelocalanchor ()-Methode aus der Komponente "asamodulescript" des Objekts "Objektanchor" zu.

### <a name="build-and-demonstrate-base-application"></a>Erstellen und veranschaulichen der Basisanwendung

Nachdem Ihre Szene nun so konfiguriert wurde, dass Sie die Grundlagen der räumlichen Azure-Anker veranschaulicht, erstellen und veranschaulichen wir das grundlegende Verhalten von räumlichen Azure-Ankern. 

1. Wenn Sie das Fenster „Buildeinstellungen“ aus den vorherigen Abschnitten geschlossen haben, öffnen Sie das Fenster „Buildeinstellungen“ erneut, indem Sie zu „Datei“ > „Buildeinstellungen“ wechseln.
![Lesson1Chapter5Step1](images/Lesson1Chapter5Step1.JPG)

2. Stellen Sie sicher, dass die gewünschte Szene in den Kulissen in der Buildliste angezeigt wird, indem Sie auf die Schaltfläche offene Szenen hinzufügen klicken.

3. Klicken Sie auf die Schaltfläche „Erstellen“, um den Buildprozess zu starten.
![Lesson1Chapter5Step3](images/Lesson1Chapter5Step3.JPG)

4. Erstellen und benennen Sie einen neuen Ordner für Ihre Anwendung. In der folgenden Abbildung wurde ein Ordner mit dem Namen "App" erstellt, der die Anwendung enthält. Klicken Sie auf Ordner auswählen, um mit dem Erstellen in den neu erstellten Ordner zu beginnen. Nachdem der Build abgeschlossen wurde, schließen Sie möglicherweise das Fenster "Buildeinstellung" in Unity. 
![Lesson1Chapter5Step4](images/Lesson1Chapter5Step4.JPG)

  > HINWEIS: Wenn der Vorgang fehlschlägt, wiederholen Sie den Buildvorgang, oder starten Sie Unity neu, und wiederholen Sie dann den Buildvorgang. Wenn ein Fehler angezeigt wird, z. b. "Fehler: CS0246 = der Kette-oder Namespace Name "XX" konnte nicht gefunden werden. (fehlt eine using-Direktive oder ein Assemblyverweis?). Möglicherweise müssen Sie das [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) installieren. 
  >

5. Öffnen Sie nach Abschluss des Buildvorgangs den neu erstellten Ordner, der Ihre neu erstellten Anwendungsdateien enthält. Doppelklicken Sie auf die Projekt Mappe "mixedrealitybase. sln" oder den entsprechenden Namen. Wenn Sie einen alternativen Namen für das Projekt verwendet haben, um die Projektmappendatei in Visual Studio zu öffnen.

  > Hinweis: Stellen Sie sicher, dass Sie den neu erstellten Ordner (d. h. den app-Ordner) öffnen, wenn Sie die Benennungs Konventionen aus den vorherigen Schritten befolgen, weil eine ähnlich benannte sln-Datei außerhalb des Ordners vorhanden ist, die nicht mit der SLN-Datei im Buildordner verwechselt werden soll. 

![Lesson1Chapter5Step5](images/Lesson1Chapter5Step5.JPG)

> Hinweis: Wenn Sie von Visual Studio aufgefordert werden, neue Komponenten zu installieren, nehmen Sie sich einen Moment Zeit, um sicherzustellen, dass alle erforderlichen Komponenten auf [der Seite "Tools installieren"](install-the-tools.md) installiert sind. 

6. Schließen Sie das HoloLens 2-Gerät über das USB-Kabel an Ihren PC an. In diesen Lektion wird davon ausgegangen, dass Sie eine Test Bereitstellung mit einem hololens 2-Gerät bereitstellen. Sie können aber auch die Bereitstellung auf dem [hololens 2-Emulator](using-the-hololens-emulator.md) oder das Erstellen eines [App-Pakets für das Sideload](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>) auswählen.

7. Stellen Sie vor dem Erstellen der App auf Ihrem Gerät sicher, dass sich das Gerät im Entwicklermodus befindet. Wenn das Ihre erste Bereitstellung auf dem HoloLens 2-Gerät ist, werden Sie möglicherweise von Visual Studio aufgefordert, Ihr HoloLens 2-Gerät mit einer PIN zu koppeln. Befolgen Sie [diese Anweisungen](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) , wenn Sie den Entwicklermodus aktivieren oder mit Visual Studio koppeln müssen.

8. Konfigurieren Sie Visual Studio für die Erstellung auf Ihre hololens 2, indem Sie die Releasekonfiguration und die RM-Architektur auswählen.
![Lesson1Chapter5Step8](images/Lesson1Chapter5Step8.JPG)
   
9. Der letzte Schritt besteht darin, auf Ihrem Gerät zu erstellen, indem Sie Debuggen > Starten ohne Debugging auswählen. Wenn Sie starten ohne Debugging auswählen, wird die Anwendung sofort auf Ihrem Gerät gestartet, wenn in Visual Studio erfolgreiche ithout-Debuginformationen für das Build angezeigt werden. Dies bedeutet auch, dass Sie das USB-Kabel entfernen können, während Ihre Anwendung auf Ihrem HoloLens 2-Gerät ausgeführt wird, ohne dass die Anwendung beendet wird. Sie können auch erstellen > Lösung bereitstellen, um Sie auf Ihrem Gerät bereitzustellen, ohne dass die Anwendung automatisch gestartet wird.
![Lesson1Chapter5Step9](images/Lesson1Chapter5Step9.JPG)
   
10. Befolgen Sie die Anweisungen. Wenn die Anwendung auf Ihrem Gerät ausgeführt wird, befolgen Sie die Anweisungen auf dem Bildschirm. Drücken Sie die Szenen Schaltflächen entsprechend den nachfolgenden Schritten.

![module2chapter1step10eim](images/module2chapter1step10eim.PNG)
    
    1. Starten Sie die Sitzung für räumliche Anker.
    
    2. Verschieben Sie den Cube an einen anderen Speicherort.
    
    3. Speichern Sie die räumlichen Azure-Anker am Speicherort des Cubes.
    
    4. Stoppt die Azure-Sitzung für räumliche Anker.
    
    5. Entfernen Sie den lokalen Anker des Cubes, damit der Benutzer den Cube verschieben kann.
    
    6. Verschieben Sie den Cube an eine andere Stelle.
    
    7. Starten Sie die Azure-Sitzung für räumliche Anker.
    
    8. Suchen von räumlichen Azure-Ankern. 
    Wechseln Sie zurück zum ursprünglichen Speicherort, den Sie beim Erstellen des Ankers abgelegt haben.
    
    9. Löschen Sie den räumlichen Azure-Anker.
    
    10. Beendet die Azure-Sitzung.

### <a name="anchoring-an-experience"></a>Verankern eines Erlebnisses

In den vorherigen Abschnitten haben Sie die Grundlagen von räumlichen Azure-Ankern kennengelernt. Wir haben einen Cube verwendet, um das übergeordnete Spielobjekt mit dem angefügten Anker darzustellen und zu visualisieren. In diesem Abschnitt erfahren Sie, wie Sie eine vollständige-Funktion verankern können, indem Sie Sie als untergeordnetes Element des Objektanchor-Objekts platzieren. In diesem Beispiel verwenden wir die "Lunar Module Assembly Demonstration"-Anwendung, die während der [grundlegenden Modul Lektion 6](mrlearning-base-ch6.md)erstellt wurde.

1. Suchen Sie nach der Assembly für das mondmodulmodul Complete Prefab, und ziehen Sie diese als untergeordnetes Element des anchorparent-gameobject, wie in der folgenden Abbildung dargestellt.

![module2chapter1step11](images/module2chapter1step11im.PNG)

2. Positionieren Sie die Modulassembly, sodass der Cube weiterhin verfügbar gemacht wird, wie in der folgenden Abbildung dargestellt. In der Anwendung können Benutzer die gesamte Benutzerfunktion neu positionieren, indem Sie den Cube verschieben. 

![module2chapter1step12im](images/module2chapter1step12im.PNG)

> Hinweis: Es gibt eine Vielzahl von Benutzeroberflächen Abläufen für die Neupositionierung, einschließlich der Verwendung einer Schaltfläche, um ein umgebendes Feld zu wechseln, das das Erlebnis umgibt, der Verwendung eines neu positionierenden Objekts (z. b. des in diesem Schritt verwendeten Cubes), der Verwendung der Position und Drehung Gizmos. und mehr.

## <a name="congratulations"></a>Herzlichen Glückwunsch!
In diesem Tutorial haben Sie die Grundlagen von räumlichen Azure-Ankern kennengelernt. In diesem Abschnitt wurden mehrere Schaltflächen zur Verfügung gestellt, mit denen Sie die verschiedenen erforderlichen Schritte zum Starten und Beenden einer Azure-Sitzung und zum Erstellen, hochladen und Herunterladen von Azure-Ankern auf einem einzelnen Gerät untersuchen können. In der nächsten Lektion erfahren Sie, wie Sie Azure-Anker-IDs für den Abruf in den hololens 2 speichern, auch nachdem die Anwendung neu gestartet wurde. Während der Reihe erfahren Sie auch, wie Anker-IDs zwischen mehreren Geräten übertragen werden, um eine räumliche Ausrichtung zu erreichen, und erfahren mehr über freigegebene Sitzungen mit mehreren Benutzern, die im Rahmen der Freigabe des Tutorials demnächst erläutert werden.

[Nächste Lektion: 2. Speichern, Abrufen und Freigeben von Azure Spatial Anchors](mrlearning-asa-ch2.md)

