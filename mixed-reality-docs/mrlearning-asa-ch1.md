---
title: Tutorials zu Azure Spatial Anchor-1. Ersten Einstieg in Azure Spatial Anchor
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: b615f1135f5d2947f8f718e080ef45a3c1fcc576
ms.sourcegitcommit: 05fa75193059a2dac4b580a9eef7b6c4bb64d8d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74830848"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a>1. Einstieg in Azure Spatial Anchor

Willkommen beim zweiten Modul der hololens 2-Tutorials. Bevor Sie beginnen, stellen Sie sicher, dass alle [Voraussetzungen](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens) erfüllt sind. Wenn Sie das erste [Basismodul](mrlearning-base.md) noch nicht abgeschlossen haben, empfiehlt es sich, dieses Modul zuerst abzuschließen. Wenn Sie mit einem neuen Unity-Projekt beginnen, befolgen Sie die Schritte zum Erstellen eines neuen Projekts im [Basismodul](mrlearning-base.md). 

## <a name="objectives"></a>Ziele

* Erfahren Sie mehr über die Grundlagen der Entwicklung mit räumlichen Azure-Ankern mit hololens 2

* Erstellen, hochladen und herunterladen räumlicher Anker

## <a name="instructions"></a>Anweisungen

### <a name="downloading-and-importing-assets"></a>Herunterladen und Importieren von Assets
Bevor Sie beginnen, müssen Sie die folgenden Ressourcen herunterladen und importieren:

[Räumliche Azure-Anker v 1.1.0](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage)

[Unity. HoloLens2. GettingStarted. Tutorials. Asset. 2.1.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage)

[Unity. HoloLens2. azurespatialanchor. Tutorials. Asset. 2.1.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchor-v2.1.0.0/Unity.HoloLens2.AzureSpatialAnchor.Tutorials.Asset.2.1.0.0.unitypackage)

[Mixed Reality Toolkit Foundation-Paket 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.1.0)

1. Erstellen Sie eine neue Szene in Ihrem Projekt. Klicken Sie mit der rechten Maustaste auf den Ordner Szene, klicken Sie auf Erstellen und dann auf Szene Nennen Sie die neue Szene "asalearningmodule".

![module2chapter1step1im](images/module2chapter1step1im.PNG)

2. Doppelklicken Sie auf die Szene "asalearningmodule", um einige vordefinierte Elemente anzuzeigen, die zusammen mit der neuen Szene angezeigt werden. 
3. Konfigurieren Sie die Szene für die Entwicklung in gemischter Realität. 

![module2chapter1step3im](images/module2chapter1step3im.PNG)

> Hinweis: möglicherweise wird ein Popup Dialogfeld angezeigt, in dem Sie ein [Profil für das Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html)auswählen können. Wählen Sie das Profil mit dem Namen *DefaultHoloLens2ConfigurationProfile* aus, indem Sie darauf doppelklicken.

4. Wenn Sie eine Datei für den mrtk auswählen, wählen Sie defaultmixedrealitytoolkitconfigurationprofile aus.

> Hinweis: Wenn Sie über ein eigenes Konfigurations Profil verfügen, können Sie dieses stattdessen verwenden.
>

![module2chapter1step4im](images/module2chapter1step4im.PNG)

Die Szene ist nun für gemischte Realität konfiguriert. Stellen Sie sicher, dass Sie Ihre Szene speichern (führen Sie dies entweder mit Control/Command + S aus, oder klicken Sie auf Datei und dann auf Speichern). 

5. Importieren Sie das [Azure Spatial Anchor v 1.1.0](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v1.1.0/AzureSpatialAnchors.unitypackage) Unity-Paket, das Sie in Schritt 1 heruntergeladen haben. Klicken Sie dazu auf Assets, fahren Sie mit Paket importieren, und klicken Sie dann auf benutzerdefiniertes Paket... Ihre Computerdateien werden geöffnet. Wenn dies der Fall ist, suchen Sie nach dem Speicherort des Azure Spatial Anchor-Pakets, und wählen Sie es aus. Klicken Sie anschließend auf Öffnen.

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

Daraufhin wird ein Popup Fenster mit einer Liste von Tools und Einstellungen angezeigt, die Sie dazu auffordern, zu importieren. Wählen Sie ***alle*** verfügbaren Optionen aus, und klicken Sie dann auf importieren.

![module2chapter1step5cim](images/module2chapter1step5cim.PNG)

> Hinweis: seien Sie geduldig, es dauert einige Minuten, bis der Import Vorgang abgeschlossen ist. 

6. Importieren Sie [Unity. HoloLens2. GettingStarted. Tutorials. Asset. 2.1.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage) als nächstes. Wechseln Sie wie in Schritt 5 zu Unity, klicken Sie auf Assets, und zeigen Sie auf Import Package. Klicken Sie auf benutzerdefiniertes Paket... Die Computerdateien werden erneut angezeigt. Wechseln Sie zu dem Speicherort, an dem Sie das Basismodul-Asset Pack und wählen Sie Sie aus. Klicken Sie auf "Öffnen".

![module2chapter1step5bim](images/module2chapter1step5bim.PNG)

> Hinweis: möglicherweise sind später in diesem Modul weitere Ressourcen erforderlich. Führen Sie diese Schritte aus, um alle Objekte zu importieren, die ab diesem Punkt erwähnt werden. 

7. Importieren Sie das [ASA Module Pack 1.3.1](https://github.com/Developer-OI/MixedRealityLearning/releases/download/ASA_1.3/ASAModuleAssets_1.3.1.unitypackage), und verwenden Sie dabei die gleichen Schritte wie beim Importieren der vorherigen Pakete.

### <a name="configuring-your-scene"></a>Konfigurieren der Szene

In diesem Abschnitt fügen wir Prefabs und Skripts in die Szene ein, um eine Reihe von Schaltflächen zu erstellen, die die Grundlagen der Art und Weise darstellen, wie sich sowohl lokale Anker als auch räumliche Azure-Anker in einer Anwendung Verhalten.

8. Klicken Sie auf der Registerkarte Projekt unterhalb des Ordners Assets auf asamoduleassets. Nachdem diese Option ausgewählt wurde, werden zwei präfabs angezeigt: buttonparent und para Anker.

![module2chapter1step7im](images/module2chapter1step7im.PNG)

9. Ziehen Sie beide Prefabs in die Szene. 

![module2chapter1step8im](images/module2chapter1step8im.PNG)

Hinweis: Nachdem Sie das buttonparent-Element in der Szene hinzugefügt haben, wird ein Popup Fenster mit der Aufforderung angezeigt, tmp-Assets zu importieren. Importieren Sie "tmp Essentials". Wenn in der Szene ein großer Schriftart Text angezeigt wird, löschen Sie das buttonparent-Objekt, und fügen Sie es erneut aus dem Ordner asamoduleassets hinzu.

Hinweis: Wenn Sie die Debugprotokolle in den hololens überprüfen möchten, können Sie das debugWindow-präfab aus dem Ordner "asamoduleassets" per Drag & amp; Drop in die Szene ziehen. Fügen Sie das debugwindowmessaging-Skript im debugWindow-Inspektor-Panel an, und aktivieren Sie die Option Debugfenster aktiviert. Ziehen Sie anschließend das debugWindow-präfab per Drag & amp; Drop in das leere Feld debugtext. Sie können die Position des Debugfensters auch nach Bedarf anpassen.

10. Um die Szene zu vergrößern, doppelklicken Sie auf den übergeordneten Anker in der Hierarchie, und passen Sie die Ansicht an, um die gesamte Szene nach Bedarf anzuzeigen. Derzeit ist "arentanchor" ein farbiger Cube, der nur zu Demonstrationszwecken verwendet wird. Schließlich blenden wir den Cube aus und platzieren den Inhalt als untergeordnetes Element des para Ankers. 

11. Nun konfigurieren wir die Schaltflächen zum Betreiben der Szene. Erweitern Sie dazu die vorfab mit buttonparent, und Sie sehen mehrere beschriftete Schaltflächen, die über die pressablebutton-präfabs von mrtk erstellt werden. Erfahren Sie mehr über das Erstellen von pressablebutton aus dem [Basismodul](mrlearning-base-ch2.md). Damit diese Schaltflächen funktionieren, müssen Sie ein Ereignis hinzufügen, das ausgelöst wird, wenn der Benutzer die einzelnen Schaltflächen drückt oder auswählt. 

- Erstellen Sie für die Schaltfläche "startazuresession" ein neues Ereignis unter dem Schaltflächen-Befehl "gedrücktes Ereignis" sowie auf dem Ereignis Auslösers "bei Click". Ziehen Sie das Objekt "objeanchor" in das leere Feld, und weisen Sie die startazuresession ()-Methode aus der asamodulescript-Komponente des Objektanker-Objekts wie im folgenden Screenshot gezeigt zu.
- ![module2chapter1step10aim](images/module2chapter1step10aim.PNG)

![module2chapter1step10bim](images/module2chapter1step10bim.PNG)

![module2chapter1step10cim](images/module2chapter1step10fim.PNG)

- Erstellen Sie für die Schaltfläche stopazuresession ein neues Ereignis unter dem Schaltflächen-gedrückten Ereignis-und dem Click-Ereignis-Auslösers. Ziehen Sie das Objekt "objeanchor" in das leere Feld, und weisen Sie die stopazuresession ()-Methode aus der asamodulescript-Komponente des Objektanchor-Objekts zu.

- Erstellen Sie für die Schaltfläche mit dem Namen "" auf der Schaltfläche "kreateanchor" ein neues Ereignis mit dem Schaltflächen-und aktivierten Ereignis-Auslösers. Ziehen Sie das Objekt "objeanchor" in das leere Feld, und weisen Sie die Methode "Methode" "Methode" aus der Komponente "asamodulescript" des Objekts "Objektanchor" zu.  **Ziehen Sie anschließend den Element Ankern erneut in das nächste leere Feld "Spielobjekt".**

- Erstellen Sie für die Schaltfläche Start Suche nach Anker ein neues Ereignis unter der Schaltfläche "Ereignis-Taste drücken", und klicken Sie auf den Click-Ereignis-Auslösers. Ziehen Sie das Objekt "objeanchor" in das leere Feld, und weisen Sie die Methode "findazureanchor ()" aus der Komponente "asamodulescript" des Objektanchor-Objekts zu.

- Erstellen Sie für die Schaltfläche mit dem Namen deleteazureanchor ein neues Ereignis unter dem Schaltflächen-gedrückten Ereignis-und dem Click-Ereignis-Auslösers. Ziehen Sie das Objekt "objeanchor" in das leere Feld, und weisen Sie die deleteazureanchor ()-Methode aus der asamodulescript-Komponente des Objektanchor-Objekts zu.  

- Erstellen Sie für die Schaltfläche mit dem Namen lokalen Anker löschen ein neues Ereignis unter dem Schaltflächen-gedrückten Ereignis-und dem Click-Ereignis-auslöst. Ziehen Sie das Objekt "objeanchor" in das leere Feld, und weisen Sie die removelocalanchor ()-Methode aus der Komponente "asamodulescript" des Objekts "Objektanchor" zu. **Ziehen Sie anschließend das Objekt "objeanchor" erneut in das nächste leere Feld "Spielobjekt".**

12. Wechseln Sie zum Einrichten von Azure Spatial Anchor zum Ordner "azurespatialanchorsplugin" im Ordner "Assets", und navigieren Sie zu "examples-> Resources->" azurespatialanchorsdemoconfig "-Datei. Fügen Sie im Inspektor-Panel die Azure-Konto-ID und den Kontoschlüssel hinzu, die Sie zuvor erstellt haben. Wenn Sie diese nicht erstellt oder nicht haben, befolgen Sie die [Voraussetzungen](https://docs.microsoft.com//azure/spatial-anchors/quickstarts/get-started-unity-hololens). 

  ![module2chapter1step13im](images/module2chapter1step13im.PNG)

### <a name="build-and-demonstrate-base-application"></a>Erstellen und veranschaulichen der Basisanwendung

Nachdem Ihre Szene nun so konfiguriert wurde, dass Sie die Grundlagen der räumlichen Azure-Anker veranschaulicht, erstellen und veranschaulichen wir das grundlegende Verhalten von räumlichen Azure-Ankern. 

1. Öffnen Sie erneut das Fenster mit den Buildeinstellungen, indem Sie zu Datei > Buildeinstellungen navigieren.
    ![mrlearning-ASA-CH1-3-Schritt 1](images/mrlearning-asa-ch1-3-step1.jpg)
2. Stellen Sie sicher, dass die gewünschte Szene in den Kulissen der Buildliste angezeigt wird, indem Sie auf die Schaltfläche offene Szenen hinzufügen klicken.
3. Vergewissern Sie sich, dass die Plattform auf die universelle Windows-Plattform festgelegt ist. Wenn dies nicht der Fall ist, legen Sie den Wert auf denselben Wert fest
4. Klicken Sie auf die Schaltfläche Player Einstellungen, und wechseln Sie zu Veröffentlichungs Einstellungen. Aktivieren Sie unter "Funktionen" Folgendes: Internet, Internet Client Server, privater Netzwerkclient Server, Wechselmedien, Webcam, Mikrofon und räumliche Wahrnehmung.
5. Wechseln Sie in den gleichen Player Einstellungen zu "XR Settings", und wählen Sie die virtuelle Realität aus, die unterstützt wird.
6. Klicken Sie auf die Schaltfläche „Erstellen“, um den Buildprozess zu starten.
   ![mrlearning-ASA-CH1-3-Schritt 6](images/mrlearning-asa-ch1-3-step6.jpg)
7. Erstellen und benennen Sie einen neuen Ordner für Ihre Anwendung. In der folgenden Abbildung wurde ein Ordner mit dem Namen "App" erstellt, der die Anwendung enthält. Klicken Sie auf Ordner auswählen, um mit dem Erstellen in den neu erstellten Ordner zu beginnen. Nachdem der Build abgeschlossen wurde, schließen Sie möglicherweise das Fenster "Buildeinstellung" in Unity.

    ![mrlearning-ASA-CH1-3-STEP7](images/mrlearning-asa-ch1-3-step7.jpg)

    > Hinweis: Wenn der Build fehlschlägt, versuchen Sie es erneut, oder starten Sie Unity neu, und erstellen Sie es erneut. Wenn ein Fehler wie "Fehler: CS0246 = der Typ-oder Namespace Name" XX "nicht gefunden werden konnte (fehlt eine using-Direktive oder ein Assemblyverweis?), müssen Sie möglicherweise das [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>) installieren. 


8. Auch nach einem erfolgreichen Buildvorgang erhalten Sie möglicherweise einige Fehler, wie unten gezeigt, aber wenn der Build erfolgreich ist, können Sie Sie ignorieren und mit den nächsten Schritten fortfahren.

    ![mrlearning-ASA-CH1-3-step7B](images/mrlearning-asa-ch1-3-step7B.png)

    

9. Öffnen Sie nach Abschluss des Buildvorgangs den neu erstellten Ordner, der Ihre neu erstellten Anwendungsdateien enthält. Doppelklicken Sie auf die Projekt Mappe "mixedrealitybase. sln" oder den entsprechenden Namen, wenn Sie einen alternativen Namen für das Projekt verwendet haben, um die Projektmappendatei in Visual Studio zu öffnen.

    > Hinweis: Stellen Sie sicher, dass Sie den neu erstellten Ordner (d. h. den app-Ordner) öffnen, wenn Sie die Benennungs Konventionen aus den vorherigen Schritten befolgen, da eine ebenso benannte sln-Datei außerhalb des Ordners vorhanden ist, die nicht mit der SLN-Datei im Buildordner verwechselt werden muss.

    ![mrlearning-ASA-CH1-3-step8](images/mrlearning-asa-ch1-3-step8.jpg)

    > Hinweis: Wenn Visual Studio die Installation neuer Komponenten anfordert, stellen Sie sicher, dass alle erforderlichen Komponenten auf [der Seite "Tools installieren"](install-the-tools.md) installiert sind.


9. Schließen Sie das HoloLens 2-Gerät über das USB-Kabel an Ihren PC an. In diesen Lektion wird davon ausgegangen, dass Sie eine Test Bereitstellung mit einem hololens 2-Gerät bereitstellen. Sie können aber auch die Bereitstellung auf dem [hololens 2-Emulator](using-the-hololens-emulator.md) oder das Erstellen eines [App-Pakets für das Sideload](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>) auswählen.

10. Stellen Sie sicher, dass Sie sich im Entwicklermodus befindet, bevor Sie auf Ihr Gerät bauen. Wenn Sie das erste Mal auf den hololens 2 bereitstellen, werden Sie möglicherweise von Visual Studio aufgefordert, ihre hololens 2 mit einer PIN zu koppeln. Befolgen Sie [diese Anweisungen](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio) , wenn Sie den Entwicklermodus aktivieren oder mit Visual Studio koppeln müssen.

11. Konfigurieren Sie Visual Studio für die Erstellung auf hololens 2, indem Sie die Releasekonfiguration und die ARM-Architektur auswählen.

    ![mrlearning-ASA-CH1-3-step11](images/mrlearning-asa-ch1-3-step11.jpg)


12. Der letzte Schritt ist die Erstellung auf Ihrem Gerät durch Auswählen von „Debuggen“ > „Starten ohne Debuggen“. Wenn Sie starten ohne Debugging auswählen, wird die Anwendung sofort bei einem erfolgreichen Build auf Ihrem Gerät gestartet, ohne dass Debuginformationen in Visual Studio angezeigt werden. Dies bedeutet auch, dass Sie das USB-Kabel entfernen können, während Ihre Anwendung auf Ihrem HoloLens 2-Gerät ausgeführt wird, ohne dass die Anwendung beendet wird. Sie können auch erstellen > Lösung bereitstellen, um Sie auf Ihrem Gerät bereitzustellen, ohne dass die Anwendung automatisch gestartet wird.

    ![mrlearning-ASA-CH1-3-step12](images/mrlearning-asa-ch1-3-step12.jpg)

>Hinweis: die räumlichen Azure-Anker verwenden das Internet zum Speichern und Laden der Anker Daten. Stellen Sie daher sicher, dass Ihr Gerät mit dem Internet verbunden ist, bevor Sie die ASA-App testen.

13. Befolgen Sie die Anweisungen. 
    Wenn die Anwendung auf Ihrem Gerät ausgeführt wird, befolgen Sie die Anweisungen auf dem Bildschirm. Drücken Sie die Szenen Schaltflächen entsprechend den nachfolgenden Schritten. Wenn Sie das Debuggingfenster wie in den vorherigen Schritten beschrieben hinzugefügt haben, können Sie das Feedback der einzelnen Schaltflächen drücken und den Fortschritt einzelner Vorgänge im Zusammenhang mit den räumlichen Azure-Ankern anzeigen.

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

1. Suchen Sie nach der Prefab-vorfab "Launcher Launcher", und ziehen Sie Sie in die Hierarchie als untergeordnetes Element des-Objekts (siehe Abbildung unten).

![module2chapter1step11](images/module2chapter1step11im.PNG)

2. Positionieren Sie die Modulassembly, sodass der Cube weiterhin verfügbar gemacht wird, wie in der folgenden Abbildung dargestellt. In der Anwendung können Benutzer die gesamte Benutzerfunktion neu positionieren, indem Sie den Cube verschieben. 

![module2chapter1step12im](images/module2chapter1step12im.PNG)

> Hinweis: Es gibt eine Vielzahl von Benutzeroberflächen Abläufen für die Neupositionierung, einschließlich der Verwendung einer Schaltfläche zum Umschalten eines umgebenden Felds, das die Oberfläche umgibt, der Verwendung eines neu positionierenden Objekts (z. b. des in diesem Schritt verwendeten Cubes), der Verwendung von Position und Rotation. Gizmos und mehr.

## <a name="congratulations"></a>Herzlichen Glückwunsch!
In diesem Tutorial haben Sie die Grundlagen von räumlichen Azure-Ankern kennengelernt. In dieser Lektion haben Sie mehrere Schaltflächen zur Verfügung gestellt, mit denen Sie die verschiedenen Schritte zum Starten und Beenden einer Azure-Sitzung sowie zum Erstellen, hochladen und Herunterladen von Azure-Ankern auf einem einzelnen Gerät untersuchen können In der nächsten Lektion erfahren Sie, wie Sie Azure-Anker-IDs für den Abruf in den hololens 2 speichern, auch nachdem die Anwendung neu gestartet wurde. Während der Reihe erfahren Sie auch, wie Anker-IDs zwischen mehreren Geräten übertragen werden, um eine räumliche Ausrichtung zu erzielen und sich über freigegebene Sitzungen mit mehreren Benutzern zu informieren, die im Rahmen des Freigabe-Tutorials zur Verfügung stehen.

[Nächste Lektion: 2. speichern, abrufen und Freigeben von räumlichen Azure-Ankern](mrlearning-asa-ch2.md)

