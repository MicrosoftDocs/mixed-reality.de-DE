---
title: Mr und Azure 310-Objekterkennung
description: Machen Sie sich mit diesem Kurs vertraut, um zu erfahren, wie Sie ein Machine Learning-Modell trainieren, und verwenden Sie dann das trainierte Modell, um ähnliche Objekte und ihre Position in der realen Welt aus einer gemischten Reality-Anwendung zu erkennen.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Custom Vision, Objekterkennung, gemischte Realität, Academy, Unity, Tutorial, API, hololens
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63544418"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.

# <a name="mr-and-azure-310-object-detection"></a>Mr und Azure 310: Objekterkennung

In diesem Kurs erfahren Sie, wie Sie benutzerdefinierte visuelle Inhalte und deren räumliche Position in einem bereitgestellten Image erkennen können, indem Sie Azure Custom Vision "Objekt Erkennungsfunktionen" in einer Mixed Reality-Anwendung verwenden.

Mit diesem Dienst können Sie ein Machine Learning-Modell mithilfe von Objekt Images trainieren. Anschließend verwenden Sie das trainierte Modell, um ähnliche Objekte zu erkennen und einander in der realen Welt zu erkennen, wie von der Kamera Erfassung von Microsoft hololens oder einer Kamera mit einem PC für immersive (VR)-Headsets bereitgestellt wird.

![Kurs Ergebnis](images/AzureLabs-Lab310-00.png)

**Azure-Custom Vision, Objekterkennung** ist ein Microsoft-Dienst, mit dem Entwickler benutzerdefinierte Abbild Klassifizierungen erstellen können. Diese Klassifizierungen können dann mit neuen Bildern verwendet werden, um Objekte innerhalb dieses neuen Bilds zu erkennen, indem Sie die **Feld Begrenzungen** innerhalb des Bilds selbst bereitstellen. Der Dienst bietet ein einfaches, leicht zu verwendende Onlineportal, um diesen Prozess zu optimieren. Weitere Informationen finden Sie unter den folgenden Links:

* [Azure-Custom Vision Seite](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [Limits und Kontingente](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

Nach Abschluss dieses Kurses verfügen Sie über eine Mixed Reality-Anwendung, die Folgendes ausführen kann:

1. Der Benutzer *ist in der* Lage, ein Objekt zu sehen, das Sie mithilfe des Azure-Custom Vision Service (Objekterkennung) trainiert haben. 
2. Der Benutzer verwendet die *Tap* -Geste, um ein Bild von dem zu erfassenden Bild zu erfassen.
3. Die APP sendet das Image an den Azure-Custom Vision Service.
4. Es wird eine Antwort vom Dienst angezeigt, die das Ergebnis der Erkennung als Welt Raum Text anzeigt. Dies wird durch die Verwendung der räumlichen Nachverfolgung von Microsoft hololens erreicht, um die Weltposition des erkannten Objekts zu verstehen, und dann das *Tag* zu verwenden, das den im Bild erkannten Werten zugeordnet ist, um den Bezeichnungs Text bereitzustellen.

Der Kurs umfasst auch das manuelle Hochladen von Bildern, das Erstellen von Tags und das Trainieren des Dienstanbieter, um verschiedene Objekte (im bereitgestellten Beispiel a Cup) zu erkennen, indem das *Begrenzungsfeld* innerhalb des Abbilds festgelegt wird, das Sie senden. 

> [!IMPORTANT]
> Nach der Erstellung und Verwendung der APP sollte der Entwickler zurück zum Azure-Custom Vision Service navigieren, die vom Dienst vorgenommenen Vorhersagen ermitteln und ermitteln, ob Sie richtig waren (durch Markieren von etwas, das der Dienst verpasst hat). Anpassen der *Begrenzungs Felder*). Der Dienst kann dann neu trainiert werden, wodurch die Wahrscheinlichkeit erhöht wird, dass reale Objekte erkannt werden.

In diesem Kurs erfahren Sie, wie Sie die Ergebnisse aus dem Azure-Custom Vision Service, Objekterkennung, in einer Unity-basierten Beispielanwendung erhalten. Sie müssen diese Konzepte auf eine benutzerdefinierte Anwendung anwenden, die Sie möglicherweise aufbauen.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> Mr und Azure 310: Objekterkennung</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>Vorraussetzungen

> [!NOTE]
> Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen. Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Juli 2018). Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt werden.

Für diesen Kurs empfehlen wir die folgende Hardware und Software:

- Einen Entwicklungs-PC
- [Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Das neueste Windows 10 SDK](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Unity 2017,4 LTS](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Visual Studio 2017](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- Ein [Microsoft hololens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) mit aktiviertem Entwicklermodus
- Internet Zugriff für Azure-Setup und Custom Vision Service-Abruf
-  Für jedes Objekt, das von der Custom Vision erkannt werden soll, ist eine Reihe von mindestens 15 (15) Bildern erforderlich). Wenn Sie möchten, können Sie die Images verwenden, die bereits mit diesem Kurs, [einer Reihe von Tassen](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip), bereitgestellt werden.

## <a name="before-you-start"></a>Bevor Sie beginnen

1.  Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).
2.  Richten Sie Ihre hololens ein, und testen Sie Sie. Wenn Sie Unterstützung für die Einrichtung ihrer hololens benötigen, [besuchen Sie den Artikel zum Einrichten von hololens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Es empfiehlt sich, eine Kalibrierung und Sensor Optimierung durchzuführen, wenn Sie mit der Entwicklung einer neuen hololens-App beginnen (manchmal kann es hilfreich sein, diese Aufgaben für jeden Benutzer auszuführen). 

Hilfe zur Kalibrierung finden Sie unter diesem [Link zum Artikel zur hololens-Kalibrierung](calibration.md#hololens).

Hilfe zur Sensor Optimierung finden Sie unter diesem [Link zum Artikel zur Überwachung von hololens-Sensoren](sensor-tuning.md).

## <a name="chapter-1---the-custom-vision-portal"></a>Kapitel 1: das Custom Vision-Portal

Um das **Azure-Custom Vision Service**verwenden zu können, müssen Sie eine Instanz von der Anwendung so konfigurieren, dass Sie Ihrer Anwendung zur Verfügung gestellt wird.

1.  Navigieren [Sie zur **Custom Vision Service** Hauptseite](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).

2.  Klicken Sie auf " **Getting Started**".

    ![](images/AzureLabs-Lab310-01.png)

3.  Melden Sie sich beim Custom Vision-Portal an.

    ![](images/AzureLabs-Lab310-02.png)

4.  Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen. Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.

5.  Wenn Sie sich zum ersten Mal angemeldet haben, werden Sie im Bereich mit den *Nutzungsbedingungen* aufgefordert. Aktivieren Sie das Kontrollkästchen, um *den Bedingungen zuzustimmen*. Klicken Sie dann auf **Ich stimme**zu.

    ![](images/AzureLabs-Lab310-03.png)

6.  Nachdem Sie die Bedingungen zugestimmt haben, befinden Sie sich jetzt im Abschnitt " *Meine Projekte* ". Klicken Sie auf **Neues Projekt**.

    ![](images/AzureLabs-Lab310-04.png)

7.  Eine Registerkarte wird auf der rechten Seite angezeigt, auf der Sie aufgefordert werden, einige Felder für das Projekt anzugeben.

    1.  Fügen Sie einen Namen für Ihr Projekt ein.

    2.  Fügen Sie eine Beschreibung für das Projekt ein (**optional**).

    3.  Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** . Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Kursen) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > Wenn Sie [mehr über Azure-Ressourcengruppen erfahren möchten, navigieren Sie zu den zugehörigen](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal) Dokumenten.

    4.  Legen Sie die **Projekttypen** als **Objekterkennung (Vorschauversion)** fest.

8.  Wenn Sie fertig sind, klicken Sie auf **Projekt erstellen**, und Sie werden auf die Seite Custom Vision Service Projekt umgeleitet.


## <a name="chapter-2---training-your-custom-vision-project"></a>Kapitel 2: trainieren Ihres Custom Vision Projekts

Wenn Sie sich im Custom Vision Portal befinden, besteht das Hauptziel darin, das Projekt zu trainieren, um bestimmte Objekte in Bildern zu erkennen.

Sie benötigen mindestens 15 (15) Images für jedes Objekt, das von Ihrer Anwendung erkannt werden soll. Sie können die Bilder verwenden, die mit diesem Kurs bereitgestellt werden ([eine Reihe von Tassen](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

So trainieren Sie das Custom Vision Projekt:

1.  Klicken Sie auf **+** die Schaltfläche neben **Tags**.

    ![](images/AzureLabs-Lab310-06.png)

2.  Fügen Sie einen **Namen** für das Tag hinzu, mit dem die Bilder verknüpft werden. In diesem Beispiel verwenden wir Bilder von Tassen für die Erkennung, benennen Sie also das-Tag für this, **Cup**. Klicken Sie abschließend auf **Speichern** .

    ![](images/AzureLabs-Lab310-07.png)

3.  Sie werden feststellen, dass Ihr **Tag** hinzugefügt wurde (möglicherweise müssen Sie die Seite erneut laden, damit es angezeigt wird). 

    ![](images/AzureLabs-Lab310-08.png)

4.  Klicken Sie in der Mitte der Seite auf **Bilder hinzufügen** .

    ![](images/AzureLabs-Lab310-09.png)

5.  Klicken Sie auf **lokale Dateien durchsuchen**, und navigieren Sie zu den Images, die Sie für ein Objekt hochladen möchten, das mindestens 15 (15) ist.

    > [!TIP]
    >  Sie können mehrere Bilder gleichzeitig zum Hochladen auswählen.

    ![](images/AzureLabs-Lab310-10.png)

6.  Wenn Sie alle Images ausgewählt haben, mit denen Sie das Projekt trainieren möchten, klicken Sie auf **Dateien hochladen** . Die Dateien werden hochgeladen. Nachdem Sie den Upload bestätigt haben, klicken Sie auf **done**.

    ![](images/AzureLabs-Lab310-11.png)

7.  An diesem Punkt werden die Images hochgeladen, aber nicht markiert.

    ![](images/AzureLabs-Lab310-12.png)

8.  Verwenden Sie die Maus, um die Bilder zu markieren. Wenn Sie mit dem Mauszeiger auf das Bild zeigen, werden Sie durch eine Auswahl Markierung unterstützt, indem Sie automatisch eine Auswahl um das Objekt ziehen. Wenn dies nicht zutrifft, können Sie eigene zeichnen. Dies wird erreicht, indem Sie mit der linken Maustaste auf die Maus klicken und den Auswahlbereich auf das Objekt ziehen. 

    ![](images/AzureLabs-Lab310-13.png) 

9. Nach der Auswahl des Objekts innerhalb des Bilds wird eine kleine Aufforderung aufgefordert, das Regions- *Tag hinzuzufügen*. Wählen Sie das zuvor erstellte Tag ("Cup", im obigen Beispiel) aus, oder wenn Sie weitere Tags hinzufügen, geben Sie dieses in ein, und klicken Sie auf die Schaltfläche **+ (plus)** .

    ![](images/AzureLabs-Lab310-14.png) 

10. Um das nächste Bild zu markieren, klicken Sie auf den Pfeil rechts neben dem Blatt, oder schließen Sie das Tag-Blatt (durch Klicken auf das **X** in der oberen rechten Ecke des Blatts), und klicken Sie dann auf das nächste Bild. Wenn Sie das nächste Bild bereit haben, wiederholen Sie das gleiche Verfahren. Führen Sie diese Schritte für alle Images aus, die Sie hochgeladen haben, bis Sie alle gekennzeichnet sind. 

    > [!NOTE]
    >  Sie können mehrere Objekte im gleichen Bild auswählen, wie in der folgenden Abbildung dargestellt: 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. Wenn Sie alle markiert haben, klicken Sie auf der linken Seite des Bildschirms auf die **markierte** Schaltfläche, um die markierten Bilder anzuzeigen. 

    ![](images/AzureLabs-Lab310-16.png)

12. Sie sind jetzt bereit, ihren Dienst zu trainieren. Klicken Sie auf die Schaltfläche **trainieren** , und die erste Trainings Iterationen wird gestartet.

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. Nachdem Sie erstellt wurde, können Sie zwei Schaltflächen mit dem Namen " **default** " und die **Vorhersage-URL**anzeigen. Klicken Sie zuerst auf **Standardwert erstellen** , und klicken Sie dann auf **Vorhersage-URL**.

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > Der Endpunkt, der aus diesem bereitgestellt wird, wird auf den Wert festgelegt, welcher *iterations* Wert als Standard markiert wurde. Wenn Sie später eine neue *iterations* Zeit erstellen und diese als Standard aktualisieren, müssen Sie den Code nicht ändern.

14. Nachdem Sie auf die **Vorhersage-URL**geklickt haben *, öffnen Sie*den Editor, und kopieren Sie die **URL** (auch als **Vorhersage Endpunkt**bezeichnet) und den **Dienst Vorhersage Schlüssel**, um Sie abzurufen, wenn Sie Sie später im Code benötigen.

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Kapitel 3: Einrichten des Unity-Projekts

Folgendes ist eine typische Einrichtung für die Entwicklung mit gemischter Realität und ist daher eine gute Vorlage für andere Projekte.

1.  Öffnen Sie **Unity** , und klicken Sie auf **neu**.

    ![](images/AzureLabs-Lab310-21.png)

2.  Sie müssen nun einen Unity-Projektnamen angeben. Fügen Sie **customvisionobjerkennung**ein. Stellen Sie sicher, dass der Projekttyp auf **3D**festgelegt ist, und legen Sie den **Speicherort** auf einen passenden Wert fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind). Klicken Sie dann auf **Projekt erstellen**.

    ![](images/AzureLabs-Lab310-22.png)

3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist. Wechseln Sie zu **Einstellungen* *Bearbeiten* > * , und navigieren Sie dann im neuen Fenster zu **externe Tools**. Ändern Sie den **Editor für externe Skripts** in **Visual Studio**. Schließen Sie das Fenster " **Einstellungen** ".

    ![](images/AzureLabs-Lab310-23.png)

4.  Navigieren Sie als nächstes zu **Datei >** Buildeinstellungen, und wechseln Sie zur **Plattform** *universelle Windows-Plattform*, und klicken Sie dann auf die Schaltfläche **Plattform wechseln** .

    ![](images/AzureLabs-Lab310-24.png)

5.  Vergewissern Sie sich , dass im gleichen Fenster mit den Buildeinstellungen Folgendes festgelegt ist:

    1.  **Zielgerät** ist auf **hololens** festgelegt        
    2.  Der Buildtyp ist auf **D3D** festgelegt.
    3.  **SDK** ist auf **neueste installierte** Version festgelegt.
    4.  **Visual Studio-Version** ist auf **neueste installierte** Version festgelegt.
    5.  **Build und Run** sind auf **lokaler Computer** festgelegt.            
    6.  Die restlichen Einstellungen in denBuildeinstellungen sollten vorerst als Standard belassen werden.

        ![](images/AzureLabs-Lab310-25.png)

6.  Klicken Sie im gleichen Fenster mit den Buildeinstellungen auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der **Inspektor** befindet.

7. In diesem Bereich müssen einige Einstellungen überprüft werden:

    1.  Auf der Registerkarte **andere Einstellungen** :

        1.  Die CLR- **Lauf Zeit Version** sollte **experimentell** sein (.NET 4,6-Entsprechung), wodurch der Editor neu gestartet werden muss.

        2. Das Skript für die **Skript** Erstellung sollte **.net**sein.

        3. Der **API-Kompatibilitäts Grad** sollte **.NET 4,6**lauten.

            ![](images/AzureLabs-Lab310-26.png)

    2.  Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:

        1. **Internet Client deklarieren**

        2.  **Webcam**

        3. **Spatialperception**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  Weiter unten im Bereich können Sie in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**) die **unterstützte Tick Virtual Reality**und dann sicherstellen, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.

        ![](images/AzureLabs-Lab310-29.png)

8.  Zurück inden Buildeinstellungen: *\# Unity C-Projekte* sind nicht mehr abgeblendet: Aktivieren Sie das Kontrollkästchen neben this.

9.  Schließen Sie das Fenster mit den Buildeinstellungen.

10. Klicken Sie **im Editor**auf**Projekt Einstellungs** > **Grafik** **Bearbeiten** > .

    ![](images/AzureLabs-Lab310-30.png)

11. Im **Inspektor** -Bereich werden die *Grafikeinstellungen* geöffnet. Scrollen Sie nach unten, bis Sie ein Array mit der Bezeichnung **Always include-Shader**sehen. Fügen Sie einen Slot hinzu, indem Sie die **Größen** Variable um eins erhöhen (in diesem Beispiel war es 8, daher haben wir es 9). Ein neuer Slot wird an der letzten Position des Arrays angezeigt, wie unten dargestellt:

    ![](images/AzureLabs-Lab310-31.png)

12. Klicken Sie im Slot auf den kleinen Zielkreis neben dem Slot, um eine Liste der Shader zu öffnen. Suchen Sie nach dem Legacy-Shader " **Shaders/transparent/diffuser** ", und doppelklicken Sie darauf. 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>Kapitel 4: Importieren des Unity-Pakets "customvisionobjerkennung"

Für diesen Kurs erhalten Sie ein Unity-Ressourcenpaket mit dem Namen " **Azure-Mr-310. unitypackage**". 

> PP Alle Objekte, die von Unity unterstützt werden, einschließlich ganzer Szenen, können in eine **. unitypackage** -Datei gepackt und in andere Projekte exportiert/importiert werden. Dies ist die sicherste und effizienteste Methode zum Verschieben von Ressourcen zwischen verschiedenen Unity- **Projekten**.

Sie finden das [Azure-Mr-310-Paket, das Sie hier herunterladen müssen](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).

1.  Klicken Sie oben auf dem Bildschirm mit dem Unity-Dashboard auf **Assets** , und klicken Sie dann auf **Paket > benutzerdefiniertes Paket importieren**.

    ![](images/AzureLabs-Lab310-33.png)

2.  Wählen Sie mit der Dateiauswahl das Paket **Azure-Mr-310. unitypackage** aus, und klicken Sie auf **Öffnen**. Eine Liste der Komponenten für dieses Asset wird angezeigt. Bestätigen Sie den Import, indem Sie auf die Schaltfläche **importieren** klicken.

    ![](images/AzureLabs-Lab310-34.png)

3.  Nachdem der Import abgeschlossen wurde, werden Sie feststellen, dass dem Ordner " **Assets** " nun Ordner aus dem Paket hinzugefügt wurden. Diese Art von Ordnerstruktur ist typisch für ein Unity-Projekt.

    ![](images/AzureLabs-Lab310-35.png)

    1.  Der Material **-Ordner enthält** das Material, das vom **Cursor Cursor**verwendet wird. 

    2.  Der **Ordner Plug** -in enthält die newtonsoft-dll, die vom Code zum Deserialisieren der Webantwort des Diensts verwendet wird. Die zwei (2) verschiedenen Versionen, die im Ordner und Unterordner enthalten sind, sind erforderlich, damit die Bibliothek vom Unity-Editor und dem UWP-Build verwendet und erstellt werden kann. 

    3.  Der Ordner " **Prefabs** " enthält die in der Szene enthaltenen Prefabs. Dies sind die folgenden:

        1.  Der **gazecursor**, der Cursor, der in der Anwendung verwendet wird. Wird zusammen mit der spatialmapping-präfab verwendet, um auf der Grundlage physischer Objekte in der Szene platziert werden zu können.
        2.  Die **Bezeichnung**, die das UI-Objekt ist, das verwendet wird, um bei Bedarf das Objekttag in der Szene anzuzeigen.
        3.  Die **spatialmapping**, bei der es sich um das Objekt handelt, das es der Anwendung ermöglicht, eine virtuelle Karte mithilfe der räumlichen Nachverfolgung von Microsoft hololens zu verwenden.

    4.  Der Ordner **Szenen** , der derzeit die vorgefertigte Szene für diesen Kurs enthält.

4.  Öffnen Sie im **Projekt Panel**den Ordner **Szenen** , und doppelklicken Sie auf **objdetectionscene**, um die Szene zu laden, die Sie für diesen Kurs verwenden werden.

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  Es **ist kein Code enthalten**. Sie schreiben den Code, indem Sie diesen Kurs befolgen.

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>Kapitel 5: Erstellen der customvisionanalyser-Klasse.

An diesem Punkt können Sie Code schreiben. Sie beginnen mit der **customvisionanalyser** -Klasse.

> [!NOTE]
> Die Aufrufe an die **Custom Vision Service**, die im unten gezeigten Code vorgenommen wurden, werden mithilfe der **Custom Vision Rest-API**vorgenommen. Durch die Verwendung dieser API sehen Sie, wie Sie diese API implementieren und nutzen können (nützlich, um zu verstehen, wie Sie etwas ähnliches implementieren können). Beachten Sie, dass Microsoft ein **Custom Vision SDK** bietet, das auch zum Aufrufen des Dienstanbieter verwendet werden kann. Weitere Informationen finden Sie im [Custom Vision SDK-Artikel](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).

Diese Klasse ist für Folgendes zuständig:

- Das letzte als Bytearray erfasste Bild wird geladen.

- Das Bytearray wird zur Analyse an Ihre Azure **Custom Vision Service** -Instanz gesendet.

- Die Antwort wird als JSON-Zeichenfolge empfangen.

- Deserialisieren der Antwort und übergeben der resultierenden **Vorhersage** an die **sceneorganisator** -Klasse, um die Anzeige der Antwort zu übernehmen.

So erstellen Sie diese Klasse:

1.  Klicken Sie im **Projekt Panel**mit der rechten Maustaste in den **Ordner Asset**, und klicken Sie dann auf**Ordner** **Erstellen** > . Nennen Sie die Ordner **Skripts**.

    ![](images/AzureLabs-Lab310-37.png)

2.  Doppelklicken Sie auf den neu erstellten Ordner, um ihn zu öffnen.

3.  Klicken Sie mit der rechten Maustaste in den Ordner, und klicken Sie dann auf **\# Skript** **Erstellen** > . Benennen Sie das Skript **customvisionanalyser.**

4.  Doppelklicken Sie auf das neue **customvisionanalyser** -Skript, um es in **Visual Studio** zu öffnen.

5.  Stellen Sie sicher, dass am Anfang der Datei die folgenden Namespaces referenziert sind:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  Fügen Sie in der **customvisionanalyser** -Klasse die folgenden Variablen hinzu:

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > Stellen Sie sicher, dass Sie den **Dienst Vorhersage-Key** in die " **prätionkey** "-Variable und ihren **Vorhersage Endpunkt** in die " **prätionendpoint** "-Variable einfügen Sie [haben diese zuvor in den Editor in Kapitel 2, Schritt 14](#chapter-2---training-your-custom-vision-project)kopiert.

7.  Code für **Awa()** muss nun hinzugefügt werden, um die Instanzvariable zu initialisieren:

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  Fügen Sie die Coroutine hinzu (mit der statischen **getimageasbytearray ()** -Methode darunter), die die Ergebnisse der Analyse des Bilds erhält, die von der **imagecapture** -Klasse aufgezeichnet werden.

    > [!NOTE]
    > In der **analyseimagecapture** -Coroutine gibt es einen Aufrufen der **sceneorganisator** -Klasse, die Sie noch erstellen müssen. Deshalb sollten Sie **diese Zeilen jetzt kommentiert lassen**.

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

9. Löschen Sie die Methoden " **Start ()** " und " **Update ()** ", da Sie nicht verwendet werden. 

10.  Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio**speichern, bevor Sie zu **Unity**zurückkehren.

> [!IMPORTANT]
> Wie bereits erwähnt, machen Sie sich keine Gedanken über Code, der möglicherweise einen Fehler enthält, da Sie weitere Klassen bald bereitstellen werden, die diese beheben.

## <a name="chapter-6---create-the-customvisionobjects-class"></a>Kapitel 6: Erstellen der customvisionobjects-Klasse

Die Klasse, die Sie jetzt erstellen, ist die **customvisionobjects** -Klasse.

Dieses Skript enthält eine Reihe von Objekten, die von anderen Klassen zum Serialisieren und Deserialisieren der Aufrufe an die Custom Vision Service verwendet werden.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste in den Ordner >  **\# Skripts**, und klicken Sie dann auf Skript **Erstellen**. Nennen Sie das Skript **customvisionobjects.**

2.  Doppelklicken Sie auf das neue **customvisionobjects** -Skript, um es in **Visual Studio** zu öffnen.

3.  Stellen Sie sicher, dass am Anfang der Datei die folgenden Namespaces referenziert sind:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Löschen Sie die Methoden " **Start ()** " und " **Update ()** " innerhalb der **customvisionobjects** -Klasse. diese Klasse sollte nun leer sein.

    > [!WARNING]
    > Es ist wichtig, dass Sie die nächste Anweisung sorgfältig befolgen. Wenn Sie die neuen Klassen Deklarationen in der **customvisionobjects** -Klasse platzieren, erhalten Sie Kompilierungsfehler in [Kapitel 10](#chapter-10---create-the-imagecapture-class), in der angegeben wird, dass **analysisrootobject** und **BoundingBox** nicht gefunden werden.

5.  Fügen Sie die folgenden Klassen *außerhalb* der **customvisionobjects** -Klasse hinzu. Diese Objekte werden von der **newtonsoft** -Bibliothek verwendet, um die Antwortdaten zu serialisieren und zu deserialisieren:

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio**speichern, bevor Sie zu **Unity**zurückkehren.

## <a name="chapter-7---create-the-spatialmapping-class"></a>Kapitel 7: Erstellen der spatialmapping-Klasse

Mit dieser Klasse wird der **Collider der räumlichen Zuordnung** in der Szene so festgelegt, dass Konflikte zwischen virtuellen Objekten und echten Objekten erkannt werden können.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste in den Ordner >  **\# Skripts**, und klicken Sie dann auf Skript **Erstellen**. Nennen Sie das Skript **spatialmapping.**

2.  Doppelklicken Sie auf das neue **spatialmapping** -Skript, um es in **Visual Studio** zu öffnen.

3.  Stellen Sie sicher, dass die folgenden Namespaces oberhalb der **spatialmapping** -Klasse referenziert sind:

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  Fügen Sie dann die folgenden Variablen in der **spatialmapping** -Klasse oberhalb der **Start ()** -Methode hinzu:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  Fügen Sie die " **Awake ()** " und " **Start ()** " hinzu

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  Löschen Sie die **Update ()** -Methode.

7.  Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio**speichern, bevor Sie zu **Unity**zurückkehren.


## <a name="chapter-8---create-the-gazecursor-class"></a>Kapitel 8: Erstellen der "gazecursor"-Klasse

Diese Klasse ist für das Einrichten des Cursors an der richtigen Position in einem echten Bereich verantwortlich, indem der **spatialmappingcollider**-Wert verwendet wird, der im vorherigen Kapitel erstellt wurde.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste in den Ordner >  **\# Skripts**, und klicken Sie dann auf Skript **Erstellen**. Skript für " **gazecursor** " abrufen

2.  Doppelklicken Sie auf das neue **gazecursor** -Skript, um es in **Visual Studio** zu öffnen.

3.  Stellen Sie sicher, dass der folgende Namespace oberhalb der Klasse " **gazecursor** " referenziert ist:

    ```csharp
    using UnityEngine;
    ```

4.  Fügen Sie dann die folgende Variable in der Klasse " **gazecursor** " oberhalb der Methode " **Start ()** " ein. 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  Aktualisieren Sie die Methode " **Start ()** " mit dem folgenden Code:

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  Aktualisieren Sie die **Update ()** -Methode mit dem folgenden Code:

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > Machen Sie sich keine Sorgen, dass der Fehler für die **sceneorganisator** -Klasse nicht gefunden wird. Sie erstellen Sie im nächsten Kapitel.

7. Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio**speichern, bevor Sie zu **Unity**zurückkehren.

## <a name="chapter-9---create-the-sceneorganiser-class"></a>Kapitel 9: Erstellen der sceneorganisator-Klasse

Diese Klasse führt Folgendes aus:

-   Richten Sie die *Hauptkamera* ein, indem Sie die entsprechenden Komponenten an Sie anfügen.

-   Wenn ein Objekt erkannt wird, ist es dafür verantwortlich, seine Position in der realen Welt zu berechnen und eine **tagbezeichnung** in der Nähe des entsprechenden **Tagnamens**zu platzieren.    

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste in den Ordner >  **\# Skripts**, und klicken Sie dann auf Skript **Erstellen**. Nennen Sie das Skript **sceneorganisator**.

2.  Doppelklicken Sie auf das neue **sceneorganisator** -Skript, um es in **Visual Studio** zu öffnen.

3.  Stellen Sie sicher, dass die folgenden Namespaces oberhalb der **sceneorganisator** -Klasse referenziert sind:

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  Fügen Sie dann die folgenden Variablen in der **sceneorganisator** -Klasse oberhalb der **Start ()** -Methode hinzu:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  Löschen Sie die Methoden " **Start ()** " und " **Update ()** ".

6.  Fügen Sie unterhalb der Variablen die **Awa()** -Methode hinzu, die die Klasse initialisiert und die Szene einrichtet.

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  Fügen Sie die **placeanalysislabel ()** -Methode hinzu, die die Bezeichnung in der Szene *instanziiert* (die zu diesem Zeitpunkt für den Benutzer unsichtbar ist). Außerdem wird das Quad (auch unsichtbar) platziert, wo das Bild platziert ist, und es wird mit der realen Welt überlappt. Dies ist wichtig, da die Feld Koordinaten, die nach der Analyse vom Dienst abgerufen werden, wieder in dieses vierfache zurückgeführt werden, um die ungefähre Position des Objekts in der realen Welt zu ermitteln. 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  Fügen Sie die **finaliselabel ()** -Methode hinzu. Er ist für Folgendes zuständig:

    *   Der Bezeichnungs *Text wird* mit dem *Tag* der Vorhersage mit dem höchsten Vertrauen festgelegt.
    *   Aufrufen der Berechnung des umgebenden *Felds auf dem* Quad-Objekt, das zuvor positioniert wurde, und Platzieren der Bezeichnung in der Szene.
    *   Anpassung der Bezeichnungs Tiefe mithilfe eines Raycasts in das umgebende *Feld*, das mit dem Objekt in der realen Welt kollidieren soll.
    * Zurücksetzen des Aufzeichnungsprozesses, um dem Benutzer zu ermöglichen, ein anderes Bild zu erfassen.

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  Fügen Sie die **calculateboundingboxposition ()** -Methode hinzu, die eine Reihe von Berechnungen hostet, die erforderlich sind, um die vom Dienst abgerufenen umgebenden *Feld* Koordinaten zu übersetzen und diese proportional zum Quad neu zu erstellen.

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio**speichern, bevor Sie zu **Unity**zurückkehren.

    > [!IMPORTANT]
    > Bevor Sie fortfahren, öffnen Sie die **customvisionanalyser** -Klasse, und heben Sie die Auskommentierung der folgenden Zeilen innerhalb der **analyselastimageaufgezeichnet ()** -Methode auf:
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> Machen Sie sich keine Gedanken über die Meldung "die **imagecapture** -Klasse wurde nicht gefunden", Sie erstellen Sie im nächsten Kapitel.


## <a name="chapter-10---create-the-imagecapture-class"></a>Kapitel 10: Erstellen der imagecapture-Klasse

Die nächste Klasse, die Sie erstellen, ist die **imagecapture** -Klasse.

Diese Klasse ist für Folgendes zuständig:

*   Erfassen eines Bilds mithilfe der hololens-Kamera und speichern im *App* -Ordner.
*   Behandlung von *Tap* -Gesten vom Benutzer.

So erstellen Sie diese Klasse:

1.  Wechseln Sie zum Ordner " **Scripts** ", den Sie zuvor erstellt haben.

2.  Klicken Sie mit der rechten Maustaste in den Ordner, und klicken Sie dann auf **\# Skript** **Erstellen** > . Benennen Sie das Skript mit **imagecapture**.

3.  Doppelklicken Sie auf das neue **imagecapture** -Skript, um es in **Visual Studio** zu öffnen.

4.  Ersetzen Sie die Namespaces am Anfang der Datei durch Folgendes:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  Fügen Sie dann die folgenden Variablen in der **imagecapture** -Klasse oberhalb der **Start ()** -Methode hinzu:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  Der Code für die Methoden " **Awake ()** " und " **Start ()** " muss nun hinzugefügt werden:

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  Implementieren Sie einen Handler, der aufgerufen wird, wenn eine Tap-Geste auftritt:

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > Wenn der Cursor **grün**ist, bedeutet dies, dass die Kamera verfügbar ist, um das Bild zu übernehmen. Wenn der Cursor **rot**ist, bedeutet dies, dass die Kamera ausgelastet ist.

8.  Fügen Sie die Methode hinzu, die die Anwendung verwendet, um den Bild Aufzeichnungsprozess zu starten und das Image zu speichern:

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });
        }
    ```

9.  Fügen Sie die Handler hinzu, die aufgerufen werden, wenn das Foto aufgezeichnet wurde und für die Analyse bereit ist. Das Ergebnis wird dann zur Analyse an **customvisionanalyser** weitergegeben.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio**speichern, bevor Sie zu **Unity**zurückkehren.

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>Kapitel 11: Einrichten der Skripts in der Szene

Nachdem Sie den gesamten für dieses Projekt erforderlichen Code geschrieben haben, können Sie nun die Skripts in der Szene und in den Prefabs einrichten, damit Sie ordnungsgemäß Verhalten.

1.  Wählen Sie im **Unity-Editor**im Bereich **Hierarchie**die **Hauptkamera**aus.
2.  Klicken Sie **im Inspektor-Panel**mit ausgewählter **Hauptkamera** auf **Komponente hinzufügen**, suchen Sie nach **sceneorganisator** -Skript, und doppelklicken Sie darauf, um es hinzuzufügen.

    ![](images/AzureLabs-Lab310-38.png)

3.  Öffnen Sie im **Projekt Panel**den Ordner " **Prefabs**", und ziehen Sie die **Bezeichnung** "Prefab" in das Eingabefeld für das leere Verweis Ziel der *Bezeichnung* , das Sie der *Hauptkamera*soeben hinzugefügt haben, wie in dargestellt. Das folgende Bild:

    ![](images/AzureLabs-Lab310-39.png)

4.  Wählen Sie im Bereich **Hierarchie**das untergeordnete Element **gazecursor** der **Hauptkamera**aus.
5.  Klicken Sie **im Inspektor-Panel**mit ausgewähltem **gazecursor** auf **Komponente hinzufügen**, suchen Sie nach dem **gazecursor** -Skript, und doppelklicken Sie darauf, um es hinzuzufügen.

    ![](images/AzureLabs-Lab310-40.png)

6.  Wählen Sie im Bereich **Hierarchie**das untergeordnete **spatialmapping** -Element der **Hauptkamera**aus.
7.  Klicken Sie **im Inspektor-Panel**bei ausgewähltem **spatialmapping** auf **Komponente hinzufügen**, suchen Sie nach dem **spatialmapping** -Skript, und doppelklicken Sie darauf, um es hinzuzufügen.

    ![](images/AzureLabs-Lab310-41.png)

Die übrigen Skripts, die Sie nicht festgelegt haben, werden während der Laufzeit vom Code im **sceneorganisator** -Skript hinzugefügt.

## <a name="chapter-12---before-building"></a>Kapitel 12: vor dem Aufbau

Wenn Sie Ihre Anwendung gründlich testen möchten, müssen Sie Sie per querladen auf Ihre Microsoft hololens anwenden.

Bevor Sie vorgehen, stellen Sie Folgendes sicher:

-  Alle im [Kapitel 3](#chapter-3---set-up-the-unity-project) erwähnten Einstellungen sind richtig festgelegt.
- Das Skript **sceneorganisator** ist an das **Hauptkamera** Objekt angefügt.
- Das Skript " **gazecursor** " ist an das Objekt " **gazecursor** " angefügt.
- Das Skript **spatialmapping** ist an das **spatialmapping** -Objekt angefügt.
- In [Kapitel 5](#chapter-5---create-the-customvisionanalyser-class), Schritt 6:

    - Stellen Sie sicher, dass Sie den **Dienst Vorhersage Schlüssel** in die " **prätionkey** "-Variable einfügen.
    - Sie haben ihren **Vorhersage Endpunkt** in die " **vorhertionendpoint** "-Klasse eingefügt.

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>Kapitel 13: Erstellen der UWP-Lösung und querladen der Anwendung

Sie können nun Ihre Anwendung als UWP-Lösung erstellen, die Sie auf den Microsoft hololens bereitstellen können. So beginnen Sie den Buildprozess:

1.  Wechseln Sie zu **Datei >** Buildeinstellungen.

2.  Teil Strich **Unity\# -C-Projekte**.

3.  Klicken Sie auf **offene Szenen hinzufügen**. Dadurch wird dem Build die aktuell geöffnete Szene hinzugefügt.

    ![](images/AzureLabs-Lab310-42.png)

4.  Klicken Sie auf **Erstellen**. Unity startet ein *Datei-Explorer* -Fenster, in dem Sie einen Ordner erstellen und auswählen müssen, in dem die App erstellt wird. Erstellen Sie diesen Ordner jetzt, und nennen Sie ihn " **App**". Klicken Sie dann mit ausgewähltem **App** -Ordner auf **Ordner auswählen**.

5.  Unity startet das Projekt in den **App** -Ordner.

6.  Nachdem die Erstellung von Unity abgeschlossen ist (Dies kann einige Zeit in Anspruch nehmen), wird ein **Datei-Explorer** -Fenster am Speicherort des Builds geöffnet (überprüfen Sie die Taskleiste, da Sie möglicherweise nicht immer über Ihrem Fenster angezeigt wird, sondern Sie über das Hinzufügen eines neuen Fensters benachrichtigt).

7.  Zum Bereitstellen von auf Microsoft hololens benötigen Sie die IP-Adresse dieses Geräts (für die Remote Bereitstellung) und, um sicherzustellen, dass der **Entwicklermodus** ebenfalls festgelegt ist. Gehen Sie dazu wie folgt vor:

    1.  Öffnen Sie die Einstellungen, während Sie die hololens- **Einstellungen**durch tragen.

    2.  Navigieren Sie zu **Netzwerk &**  > erweiterte**Wi-Fi** > -**Optionen** für das Internet.

    3.  Notieren Sie sich die **IPv4** -Adresse.

    4.  Navigieren Sie als nächstes wieder zu **Einstellungen**, und aktualisieren Sie die **& Sicherheit** > **für Entwickler** .

    5.  Legen Sie den **Entwicklermodus** *auf*fest.

8.  Navigieren Sie zu Ihrem neuen Unity-Build ( **App** -Ordner), und öffnen Sie die Projektmappendatei mit **Visual Studio**.

9.  Wählen Sie in der Projektmappenkonfiguration **Debuggen**.

10. Wählen Sie auf der Projektmappenplattform die Option **x86, Remote Computer**aus. Sie werden aufgefordert, die **IP-Adresse** eines Remote Geräts (in diesem Fall die von Ihnen notierten Microsoft hololens) einzufügen.

    ![](images/AzureLabs-Lab310-43.png)

11. Wechseln Sie zum Menü **Erstellen** , und klicken Sie auf **Lösung** bereitstellen, um die Anwendung auf die hololens quer zuladen.

12. Ihre APP sollte nun in der Liste der installierten apps auf Ihren Microsoft hololens angezeigt werden, die bereit sind, gestartet zu werden!

### <a name="to-use-the-application"></a>So verwenden Sie die Anwendung:

* Sehen Sie sich ein Objekt an, das Sie mit Ihrer **Azure-Custom Vision Service trainiert haben, Objekterkennung**, und verwenden Sie die **Tap-Geste**.
* Wenn das Objekt erfolgreich erkannt wird, wird ein Text der *Bezeichnung* "World-Space" mit dem Tagnamen angezeigt.

> [!IMPORTANT]
> Jedes Mal, wenn Sie ein Foto erfassen und an den Dienst senden, können Sie zur Dienst Seite zurückkehren und den Dienst mit den neu aufgezeichneten Images neu trainieren. Zu Beginn müssen Sie wahrscheinlich auch die *Begrenzungs Felder* korrigieren, um präziser zu werden und den Dienst erneut zu trainieren.

> [!NOTE]
> Der Bezeichnungs Text wird möglicherweise nicht in der Nähe des Objekts angezeigt, wenn die Microsoft hololens-Sensoren und/oder die spatialtrackingcomponent in Unity die entsprechenden Kollisionen relativ zu den realen Objekten nicht platzieren. Versuchen Sie, die Anwendung auf einer anderen Oberfläche zu verwenden, wenn dies der Fall ist.

## <a name="your-custom-vision-object-detection-application"></a>Ihre Custom Vision, Objekt Erkennungs Anwendung

Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die das Azure-Custom Vision, Objekterkennungs-API nutzt, das ein Objekt aus einem Image erkennen kann, und dann eine ungefähre Position für dieses Objekt im 3D-Raum bereitstellen.

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>Bonus Übungen

### <a name="exercise-1"></a>Übung 1

Wenn Sie der Text Bezeichnung hinzufügen, verwenden Sie einen semitransparenten Cube, um das echte Objekt in einem umgebenden 3D- *Feld*zu schließen.

### <a name="exercise-2"></a>Übung 2

Trainieren Sie Ihre Custom Vision Service, um weitere Objekte zu erkennen.

### <a name="exercise-3"></a>Übung 3

Spielen Sie einen Sound wieder, wenn ein Objekt erkannt wird.

### <a name="exercise-4"></a>Übung 4

Verwenden Sie die API zum erneuten trainieren Ihres diensmit denselben Images, die von Ihrer APP analysiert werden, um den Dienst genauer zu gestalten (führen Sie sowohl Vorhersagen als auch Schulungen gleichzeitig aus).
