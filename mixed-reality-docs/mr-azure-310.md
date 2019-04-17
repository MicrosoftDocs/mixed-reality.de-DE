---
title: 'MR und Azure-310: Erkennung von Objekten'
description: Führen Sie diesen Kurs Informationen zum Trainieren von Machine Learning-Modell, und klicken Sie dann verwenden Sie das trainierte Modell, um ähnliche Objekte und ihre Position in der realen Welt von innerhalb einer mixed Reality-Anwendung zu erkennen.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, benutzerdefiniertes maschinelles sehen, objekterkennung, mixed Reality, Academy, Unity, Tutorials, api, hololens
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593285"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

# <a name="mr-and-azure-310-object-detection"></a>Mr und Azure-310: Erkennung von Objekten

In diesem Kurs erfahren Sie, wie zur Erkennung von benutzerdefinierten visuellen Inhalt und die räumliche Position in einem bereitgestellten Image mithilfe von Azure Custom Vision "Objekt" Erkennungsfunktionen in einer mixed Reality-Anwendung.

Dieser Dienst ermöglicht Ihnen zum Trainieren von Machine Learning-Modellen mithilfe von Objekt-Images. Anschließend verwenden Sie das trainierte Modell ähnlicher Objekte zu erkennen und Ungefährer ihren Standort in der realen Welt, gemäß Bereitstellung durch die Kamera-Aufnahme von Microsoft HoloLens oder Anschließen einer Kamera auf einem PC für immersive Headsets von (VR).

![Kurs Ergebnis](images/AzureLabs-Lab310-00.png)

**Azure Custom Vision, Objekterkennung** ist ein Microsoft-Service dem Entwickler benutzerdefinierte bildklassifizierungen erstellen können. Diese Klassifizierungen können dann mit neuen Images verwendet werden, um Objekte innerhalb dieses Image, zu erkennen, durch die Bereitstellung **Begrenzungsrahmen** im Abbild. Der Dienst bietet eine einfache, benutzerfreundliche, online-Portal, um diesen Prozess optimieren. Weitere Informationen finden Sie auf den folgenden Links:

* [Seite "Azure Custom Vision"](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [Einschränkungen und Kontingenten](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

Nach Abschluss dieses Kurses verfügen Sie über ein mixed Reality-Anwendung die können die folgenden Schritte ausführen:

1. Der Benutzer kann *bestaunen* auf ein Objekt, das sie trainiert haben, mit der Azure Custom Vision Service, Erkennung von Objekten. 
2. Der Benutzer verwendet die *Tippen Sie auf* Geste zum Erfassen eines Images für die sie betrachten.
3. Die app wird das Bild an der Azure Custom Vision Service senden.
4. Es werden eine Antwort aus dem Dienst, der das Ergebnis der Erkennung als Raum Text angezeigt wird. Dies wird durch die Nutzung der Microsoft HoloLens räumliche nachverfolgen, als eine Möglichkeit, verstehen die World-Position des erkannten-Objekts, und klicken Sie dann mithilfe der *Tag* zugeordnet, was in der Abbildung zu erkannt wird Geben Sie den Text der Bezeichnung.

Der Kurs behandelt auch manuell Hochladen von Images, Tags erstellen und Trainieren den Dienst zur Erkennung von anderen Objekte (im bereitgestellten Beispiel einer Tasse), durch Festlegen der *Grenze im* innerhalb des Bilds, das Sie übermitteln. 

> [!IMPORTANT]
> Nach der Erstellung und Verwendung der app, der Entwickler sollte navigieren Sie zurück zum Azure Custom Vision Service, die vom Dienst getroffenen Vorhersagen zu identifizieren und zu bestimmen, ob sie richtig oder nicht waren (durch Tags nichts des Diensts nicht teilnehmen konnten, und Anpassen der *umgebende Felder*). Der Dienst kann dann neu trainiert werden müssen die erhöht der Wahrscheinlichkeit, dass sie die Objekte der realen Welt erkennen.

In diesem Kurs erfahren Sie, wie die Ergebnisse aus der Azure Custom Vision Service, Erkennung von Objekten, in eine Unity-basierten Anwendung zu erhalten. Sie werden sich entscheiden, ob Sie diese Konzepte, die Sie erstellen eine benutzerdefinierte Anwendung zuweisen.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td> MR und Azure-310: Erkennung von Objekten</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>Vorraussetzungen

> [!NOTE]
> In diesem Tutorial wurde für Entwickler mit Erfahrung mit Unity entwickelt und C#. Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Juli 2018) überprüft wurde. Sie können zur Verwendung der neuesten Software, wie in der [Installieren der Tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) Artikel, obwohl es nicht davon ausgegangen werden soll, dass die Informationen in diesem Kurs perfekt entspricht was finden Sie in der neueren Software als aufgeführt ist unten.

Es wird empfohlen, die folgende Hardware und Software für diesen Kurs:

- Eine Entwicklungs-PC
- [Windows 10 Fall Creators Update (oder höher) mit der Entwicklermodus aktiviert ist](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Das neueste Windows 10-SDK](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Unity 2017.4 LTS](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Visual Studio 2017](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- Ein [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) mit Entwicklermodus aktiviert ist
- Zugriff auf das Internet für die Einrichtung von Azure und Custom Vision Service abrufen
-  Eine Reihe von Bildern mindestens fünfzehn (15) sind erforderlich) für jedes Objekt, das Custom Vision erkennen soll. Wenn Sie möchten, können Sie die mit diesem Kurs bereits bereitgestellten Images, [eine Reihe von Cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

## <a name="before-you-start"></a>Bevor Sie beginnen

1.  Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).
2.  Richten Sie ein und Testen Sie Ihre HoloLens. Bei Bedarf Unterstützung zum Einrichten Ihrer HoloLens, [stellen Sie sicher, dass die HoloLens-Setup-Artikel finden Sie unter](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Es ist eine gute Idee, die Kalibrierung und Optimierung der Sensor ausführen, wenn Sie beginnen, eine neue HoloLens-App (manchmal ist es hilfreich, diese Aufgaben für jeden Benutzer) entwickeln. 

Um Hilfe zur Kalibrierung, befolgen Sie diese [Link zum Artikel HoloLens Kalibrierung](calibration.md#hololens).

Um Hilfe zur Optimierung der Sensor, befolgen Sie diese [Link zum Optimieren von HoloLens Sensor](sensor-tuning.md).

## <a name="chapter-1---the-custom-vision-portal"></a>Kapitel 1: das Portal für benutzerdefiniertes maschinelles sehen

Verwenden der **Azure Custom Vision Service**, müssen Sie so konfigurieren Sie eine Instanz davon für Ihre Anwendung verfügbar gemacht werden.

1.  Navigieren Sie [auf die **Custom Vision Service** Hauptseite](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).

2.  Klicken Sie auf **Einstieg**.

    ![](images/AzureLabs-Lab310-01.png)

3.  Melden Sie sich an das Portal für benutzerdefiniertes maschinelles sehen.

    ![](images/AzureLabs-Lab310-02.png)

4.  Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen. Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.

5.  Nachdem Sie sich zum ersten Mal angemeldet sind, Sie werden aufgefordert, mit der *Vertragsbedingungen* Bereich. Klicken Sie auf das Kontrollkästchen, um *stimmen Sie den Bedingungen*. Klicken Sie dann auf **ich stimme zu**.

    ![](images/AzureLabs-Lab310-03.png)

6.  Die Begriffe zugestimmt haben, Sie sind jetzt in der *Meine Projekte* Abschnitt. Klicken Sie auf **neues Projekt**.

    ![](images/AzureLabs-Lab310-04.png)

7.  Eine Registerkarte wird auf der rechten Seite angezeigt, wodurch Sie angeben, einige Felder für das Projekt angefordert wird.

    1.  Fügen Sie einen Namen für Ihr Projekt

    2.  Fügen Sie eine Beschreibung für Ihr Projekt (**Optional**)

    3.  Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diese Kurse) unter einer allgemeinen Ressourcengruppe zu halten).

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > Wenn Sie möchten [erfahren Sie mehr über Azure-Ressourcengruppen, navigieren Sie zu den zugeordneten Dokumenten](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4.  Legen Sie die **Projekttypen** als **Objekterkennung (Vorschau)**.

8.  Sobald Sie fertig sind, klicken Sie auf **projekterstellung**, und Sie gelangen auf der Projektseite Custom Vision Service.


## <a name="chapter-2---training-your-custom-vision-project"></a>Kapitel 2 – trainieren Ihr Projekt Custom Vision

Einmal ist im Custom Vision-Portal Ihr Hauptziel zum Trainieren des Projekts für bestimmte Objekte in Bildern zu erkennen.

Für jedes Objekt, das Sie Ihre Anwendung erkennen möchten, benötigen Sie die Bilder mindestens fünfzehn (15). Sie können die in diesem Kurs bereitgestellten Images ([eine Reihe von Cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

Um Ihr Projekt Custom Vision zu trainieren:

1.  Klicken Sie auf die **+** neben **Tags**.

    ![](images/AzureLabs-Lab310-06.png)

2.  Hinzufügen einer **Namen** für den Tag, das verwendet wird, um Ihre Images mit zuordnen. In diesem Beispiel verwenden wir die Bilder der Cups für die Erkennung, damit das Tag für diese, mit dem Namen **Cup**. Klicken Sie auf **speichern** wenn fertig gestellt.

    ![](images/AzureLabs-Lab310-07.png)

3.  Sie sehen Ihre **Tag** hinzugefügt wurde (möglicherweise müssen Sie Ihrer Seite angezeigt werden neu laden). 

    ![](images/AzureLabs-Lab310-08.png)

4.  Klicken Sie auf **Hinzufügen von Bildern** in der Mitte der Seite.

    ![](images/AzureLabs-Lab310-09.png)

5.  Klicken Sie auf **lokale Dateien durchsuchen**, und navigieren Sie zu den Images, die Sie für ein Objekt, wobei das mindestens 15 (15) hochladen möchten.

    > [!TIP]
    >  Sie können mehrere Images zu einem Zeitpunkt, zum Hochladen auswählen.

    ![](images/AzureLabs-Lab310-10.png)

6.  Drücken Sie **Hochladen von Dateien** Nachdem Sie alle Bilder ausgewählt haben, möchten das Projekt zu trainieren. Hochladen beginnt die Dateien. Nachdem Sie die Bestätigung für das Hochladen haben, klicken Sie auf **Fertig**.

    ![](images/AzureLabs-Lab310-11.png)

7.  An diesem Punkt sind Ihre Images hochgeladen, aber nicht mit Tags versehen.

    ![](images/AzureLabs-Lab310-12.png)

8.  Um Ihre Images markieren möchten, verwenden Sie die Maus aus. Wie Sie auf das Bild zeigen, wird eine Markierung für die Auswahl Sie unterstützen, indem Sie einen Auswahlbereich für das Objekt automatisch zu zeichnen. Wenn sie nicht genau ist, können Sie Ihre eigenen zeichnen. Dies erfolgt durch Klicken auf die Maus enthält, und ziehen den Auswahlbereich um das Objekt enthält. 

    ![](images/AzureLabs-Lab310-13.png) 

9. Eine kleine Eingabeaufforderung fragt nach der Auswahl Ihres Objekts innerhalb des Bilds Sie *Region-Tag hinzufügen*. Wählen Sie Ihre zuvor erstellten Tags (im obigen Beispiel "Cup"), oder wenn Sie weitere Tags hinzufügen, geben Sie, dass in, und klicken Sie auf die **+ (plus)** Schaltfläche.

    ![](images/AzureLabs-Lab310-14.png) 

10. Um die nächste Abbildung zu markieren, können Sie klicken Sie auf den Pfeil rechts neben dem Blatt ", oder schließen Sie das Blatt" Tags "(durch Klicken auf die **X** in der oberen rechten Ecke auf dem Blatt) und klicken Sie dann auf der nächsten Abbildung. Nachdem Sie die nächste Abbildung bereit haben, wiederholen Sie das gleiche Verfahren. Dies gilt für alle Images, die Sie hochgeladen haben, bis sie alle mit Tags versehen sind. 

    > [!NOTE]
    >  Sie können mehrere Objekte auswählen, in dem gleichen Image, wie die folgende Abbildung: 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. Nachdem Sie alle gekennzeichnet haben, klicken Sie auf die **markierten** Schaltfläche auf der linken Seite des Bildschirms, um die markierte Bilder anzuzeigen. 

    ![](images/AzureLabs-Lab310-16.png)

12. Sie können nun zum Trainieren Ihres Diensts. Klicken Sie auf die **Train** Schaltfläche und die erste Iteration der Schulung beginnt.

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. Nachdem es erstellt wurde, werden Sie zwei Schaltflächen angezeigt werden **Standard** und **Vorhersage URL**. Klicken Sie auf **Standard** zuerst, klicken Sie dann auf auf **Vorhersage URL**.

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > Der Endpunkt, der aus diesem bereitgestellt werden, je nachdem, was je nastaven *Iteration* als Standard gekennzeichnet wurde. Also, wenn Sie später einen neuen vornehmen *Iteration* und als Standard zu aktualisieren, müssen Sie nicht zum Ändern Ihres Codes.

14. Nachdem Sie auf geklickt haben **Vorhersage URL**öffnen *Editor*, und kopieren und Einfügen der **URL** (so genannte Ihre **Vorhersage-Endpunkt**) und die **Vorhersage-Dienstschlüssel**, sodass Sie sie bei Bedarf später im Code abrufen können.

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Kapitel 3: Einrichten von Unity-Projekts

Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit mixed Reality und daher ist eine gute Vorlage für andere Projekte.

1.  Open **Unity** , und klicken Sie auf **neu**.

    ![](images/AzureLabs-Lab310-21.png)

2.  Sie müssen jetzt einen Unity-Projektnamen angeben. Fügen Sie **CustomVisionObjDetection**. Stellen Sie sicher, dass der Projekttyp nastaven NA hodnotu **3D**, und legen Sie die **Speicherort** auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser). Klicken Sie auf **projekterstellung**.

    ![](images/AzureLabs-Lab310-22.png)

3.  Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**. Wechseln Sie zu **bearbeiten* > *Voreinstellungen** und navigieren Sie dann im neuen Fenster zu **externe Tools**. Änderung **externen Skript-Editors** zu **Visual Studio**. Schließen der **Voreinstellungen** Fenster.

    ![](images/AzureLabs-Lab310-23.png)

4.  Navigieren Sie anschließend auf **Datei > Buildeinstellungen** , und wechseln Sie die **Plattform** zu *universelle Windows-Plattform*, und klicken Sie dann auf die **-Plattformwechseln** Schaltfläche.

    ![](images/AzureLabs-Lab310-24.png)

5.  In der gleichen **Buildeinstellungen** Fenster legen Sie Folgendes fest:

    1.  **Geräte** nastaven NA hodnotu **HoloLens**        
    2.  **Buildtyp** nastaven NA hodnotu **D3D**
    3.  **SDK** nastaven NA hodnotu **zuletzt installierte**
    4.  **Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**
    5.  **Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**            
    6.  Die Einstellungen im verbleibenden **Buildeinstellungen**, sollte jetzt als Standard bleiben.

        ![](images/AzureLabs-Lab310-25.png)

6.  In der gleichen **Buildeinstellungen** Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dies wird im entsprechenden Bereich geöffnet, im Bereich, in dem die **Inspector** befindet.

7. In diesem Bereich sind müssen einige Einstellungen überprüft werden:

    1.  In der **Weitere Einstellungen** Registerkarte:

        1.  **Scripting Runtime Version** muss **experimentell** (.NET 4.6 entspricht), löst der Editor neu starten müssen.

        2. **Back-End-Scripting** muss **.NET**.

        3. **API-Kompatibilitätsebene** muss **.NET 4.6**.

            ![](images/AzureLabs-Lab310-26.png)

    2.  In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:

        1. **InternetClient**

        2.  **Webcam**

        3. **SpatialPerception**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, dann stellen Sie sicher, dass die **gemischten Windows Realität SDK** hinzugefügt wird.

        ![](images/AzureLabs-Lab310-29.png)

8.  Im **Buildeinstellungen**, *Unity C\# Projekte* ist nicht mehr abgeblendet: Aktivieren Sie das Kontrollkästchen neben dieser.

9.  Schließen der **Buildeinstellungen** Fenster.

10. In der **Editor**, klicken Sie auf **bearbeiten** > **Projekteinstellungen** > **Grafiken**.

    ![](images/AzureLabs-Lab310-30.png)

11. In der **Inspektor Bereich** der *für Grafiken* geöffnet werden. Scrollen Sie nach unten, bis Sie sehen, dass ein Array namens **immer enthalten Shader**. Slot hinzufügen, indem Sie erhöhen die **Größe** Variable, indem Sie eine (in diesem Beispiel 8 vorlag, daher haben wir es 9). Ein neuer Slot wird in der letzten Position des Arrays angezeigt, wie unten dargestellt:

    ![](images/AzureLabs-Lab310-31.png)

12. Klicken Sie auf den Slot auf den kleinen Kreis neben den Slot aus, um eine Liste von Shadern öffnen. Suchen Sie nach der **Legacy Shader/Transparent / "Diffus"** Shader und doppelklicken Sie darauf. 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>Kapitel 4: Importieren des CustomVisionObjDetection Unity-Pakets

Für diesen Kurs ein Unity Asset-Paket bereitgestellt wird aufgerufen, **Azure-MR-310.unitypackage**. 

> [TIPP] Alle Objekte, die von Unity, einschließlich der gesamte Szenen unterstützt können verpackt werden, in einem **.unitypackage** -Datei, und exportiert / importiert, die in anderen Projekten. Dies ist die sicherste und effizienteste, Möglichkeit zum Verschieben von Ressourcen zwischen verschiedenen **Unity-Projekte**.

Sie finden die [Azure-MR-310-Paket, das Sie hier herunterladen müssen](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).

1.  Mit dem Sie Unity-Dashboard, klicken Sie auf **Assets** klicken Sie dann im Menü am oberen Rand des Bildschirms auf **Paket importieren > benutzerdefiniertes Paket**.

    ![](images/AzureLabs-Lab310-33.png)

2.  Verwenden Sie die Dateiauswahl zum Auswählen der **Azure-MR-310.unitypackage** packen, und klicken Sie auf **öffnen**. Eine Liste der Komponenten für dieses Medienobjekt wird Ihnen angezeigt werden. Bestätigen Sie den Import, indem Sie auf die **importieren** Schaltfläche.

    ![](images/AzureLabs-Lab310-34.png)

3.  Wenn es abgeschlossen ist, importieren, werden Sie sehen, dass die Ordner aus dem Paket jetzt hinzugefügt wurden Ihre **Assets** Ordner. Diese Art von Struktur ist typisch für ein Unity-Projekt.

    ![](images/AzureLabs-Lab310-35.png)

    1.  Die **Materialien** Ordner enthält das Material verwendet wird, durch die **bestaunen Cursor**. 

    2.  Die **-Plug-Ins** Ordner enthält die Newtonsoft-DLL, die vom Code verwendet werden, um die Web-Antwort des Diensts zu deserialisieren. Die zwei (2) sind unterschiedliche Versionen enthalten, die in den Ordner und Unterordner, erforderlich, damit die Bibliothek von Unity-Editor und der UWP-Build erstellt und verwendet werden kann. 

    3.  Die **Prefabs** Ordner enthält die prefabs (Vorlagen) in der Szene enthalten sind. Dies sind:

        1.  Die **GazeCursor**, den Cursor in der Anwendung verwendet. Funktioniert zusammen mit den SpatialMapping Prefab in der Szene auf physische Objekte platziert werden können.
        2.  Die **Bezeichnung**, die das UI-Objekt, das zum Anzeigen der Object-Tag in der Szene, bei Bedarf verwendet wird.
        3.  Die **SpatialMapping**, die das Objekt, das die Anwendung verwenden kann, erstellen eine virtuelle Zuordnung mithilfe der Microsoft HoloLens räumliche nachverfolgung.

    4.  Die **Szenen** Ordner mit dem derzeit die vorab erstellte Szene für diesen Kurs.

4.  Öffnen der **Szenen** Ordner, in der **Projektbereich**, und doppelklicken Sie auf die **ObjDetectionScene**, um die Szene laden, die Sie für diesen Kurs verwenden.

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  **Es ist kein Code enthalten**, Schreiben Sie Code anhand dieses Kurses.

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>Kapitel 5 – erstellen Sie die CustomVisionAnalyser-Klasse.

An diesem Punkt können Sie Code schreiben. Beginnen Sie mit der **CustomVisionAnalyser** Klasse.

> [!NOTE]
> Die Aufrufe an die **Custom Vision Service**, in den folgenden Code vorgenommen wurden, erfolgen mithilfe der **Custom Vision-REST-API**. Durch die Verwendung dieser, erfahren Sie, wie zu implementieren und Verwenden dieser API (nützlich, um zu verstehen, wie etwa selbst implementiert). Darüber im Klaren sein, dass Microsoft bietet eine **Custom Vision SDK** , auch für Aufrufe an den Dienst verwendet werden kann. Weitere Informationen finden Sie auf die [Custom Vision SDK Artikel](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).

Diese Klasse ist zuständig für:

- Laden das neueste Image als ein Array von Bytes erfasst.

- Das Bytearray an Azure senden **Custom Vision Service** Instanz für die Analyse.

- Empfangen der Antwort als JSON-Zeichenfolge.

- Die Antwort zu deserialisieren, und übergeben die resultierenden **Vorhersage** auf die **SceneOrganiser** -Klasse, die kümmern wird wie die Antwort angezeigt werden soll.

Diese Klasse zu erstellen:

1.  Mit der rechten Maustaste den **Ordner "Assets"** befindet sich in der **Projektfenster**, klicken Sie dann auf **erstellen** > **Ordner**. Rufen Sie den Ordner **Skripts**.

    ![](images/AzureLabs-Lab310-37.png)

2.  Doppelklicken Sie auf den neu erstellten Ordner, um ihn zu öffnen.

3.  Mit der rechten Maustaste in den Ordner, und klicken Sie dann **erstellen** > **C\# Skript**. Nennen Sie das Skript **CustomVisionAnalyser.**

4.  Doppelklicken Sie auf die neue **CustomVisionAnalyser** Skript öffnen Sie ihn mit **Visual Studio.**

5.  Stellen Sie sicher, dass Sie die folgenden Namespaces am Anfang der Datei verwiesen haben:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  In der **CustomVisionAnalyser** -Klasse verwenden, fügen Sie die folgenden Variablen:

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
    > Stellen Sie sicher, dass Sie Einfügen Ihrer **Vorhersage-Dienstschlüssel** in die **PredictionKey** Variable und Ihr **Vorhersage-Endpoint** in die **PredictionEndpoint**  Variable. Sie kopiert haben, diese [Editor früher in Kapitel 2, Schritt 14](#chapter-2---training-your-custom-vision-project).

7.  Code für **Awake()** muss nun hinzugefügt werden, um die Instanz-Variable zu initialisieren:

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

8.  Fügen Sie die Coroutine (mit der statischen **GetImageAsByteArray()** Methode darunter), die erhalten die Ergebnisse der Analyse des Bilds von erfasst die **digitale Bilder** Klasse.

    > [!NOTE]
    > In der **AnalyseImageCapture** Coroutine, erfolgt ein Aufruf von der **SceneOrganiser** -Klasse, die Sie noch erstellen werden. Aus diesem Grund **lassen Sie diese Zeilen jetzt kommentiert**.

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

9. Löschen der **Start()** und **Update()** Methoden, wie sie nicht verwendet werden. 

10.  Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio**, vor der Rückgabe an **Unity**.

> [!IMPORTANT]
> Wie bereits erwähnt, aber keine Sorge, über Code, die einen Fehler, angezeigt werden kann, wie Sie weitere Klassen bald angeben werden, die diese behoben werden.

## <a name="chapter-6---create-the-customvisionobjects-class"></a>Kapitel 6: Erstellen Sie die CustomVisionObjects-Klasse

Die Klasse, die Sie erstellen nun ist die **CustomVisionObjects** Klasse.

Dieses Skript enthält eine Reihe von Objekten, die von anderen Klassen zum Serialisieren und Deserialisieren der Aufrufe für den Custom Vision Service verwendet.

Diese Klasse zu erstellen:

1.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie dann auf **erstellen** > **C\# Skript**. Rufen Sie das Skript **CustomVisionObjects.**

2.  Doppelklicken Sie auf die neue **CustomVisionObjects** Skript öffnen Sie ihn mit **Visual Studio.**

3.  Stellen Sie sicher, dass Sie die folgenden Namespaces am Anfang der Datei verwiesen haben:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Löschen der **Start()** und **Update()** Methoden innerhalb der **CustomVisionObjects** -Klasse, diese Klasse sollte jetzt leer sein.

    > [!WARNING]
    > Es ist wichtig, dass Sie sorgfältig die nächste Anweisung ausführen. Wenn Sie die neue Klassendeklarationen in Ablegen der **CustomVisionObjects** -Klasse, Sie erhalten Kompilierungsfehler in [Kapitel 10](#chapter-10---create-the-imagecapture-class), mit der Nachricht, **AnalysisRootObject** und  **BoundingBox** wurden nicht gefunden.

5.  Fügen Sie die folgenden Klassen *außerhalb* der **CustomVisionObjects** Klasse. Diese Objekte werden verwendet, durch die **Newtonsoft** Bibliothek zum Serialisieren und Deserialisieren die Antwortdaten werden:

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

6.  Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio**, vor der Rückgabe an **Unity**.

## <a name="chapter-7---create-the-spatialmapping-class"></a>Kapitel 7: Erstellen Sie die SpatialMapping-Klasse

Diese Klasse wird festgelegt. die **räumliche Zuordnung "collider"** in der Szene, um Konflikte zwischen virtuellen und echte Objekten erkennen können.

Diese Klasse zu erstellen:

1.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie dann auf **erstellen** > **C\# Skript**. Rufen Sie das Skript **SpatialMapping.**

2.  Doppelklicken Sie auf die neue **SpatialMapping** Skript öffnen Sie ihn mit **Visual Studio.**

3.  Stellen Sie sicher, dass die folgenden Namespaces, die oben genannten der **SpatialMapping** Klasse:

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  Fügen Sie dann die folgenden Variablen in der **SpatialMapping** Klasse, über die **Start()** Methode:

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

5.  Hinzufügen der **Awake()** und **Start()**:

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

6.  Löschen der **Update()** Methode.

7.  Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio**, vor der Rückgabe an **Unity**.


## <a name="chapter-8---create-the-gazecursor-class"></a>Kapitel 8 – erstellen Sie die GazeCursor-Klasse

Diese Klasse ist zuständig für das Einrichten des Cursors am korrekten Ort im realen Bereich dafür können Sie von der **SpatialMappingCollider**, in dem vorhergehenden Kapitel erstellt haben.

Diese Klasse zu erstellen:

1.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie dann auf **erstellen** > **C\# Skript**. Rufen Sie das Skript **GazeCursor**

2.  Doppelklicken Sie auf die neue **GazeCursor** Skript öffnen Sie ihn mit **Visual Studio.**

3.  Stellen Sie sicher, dass Sie den folgenden Namespace, der oben genannten der **GazeCursor** Klasse:

    ```csharp
    using UnityEngine;
    ```

4.  Dann fügen die folgende Variable innerhalb der **GazeCursor** Klasse, über die **Start()** Methode. 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  Update der **Start()** Methode durch den folgenden Code:

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

6.  Update der **Update()** Methode durch den folgenden Code:

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
    > Aber keine Sorge, über den Fehler für die **SceneOrganiser** Klasse nicht gefunden wird, erstellen Sie ihn im nächsten Kapitel.

7. Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio**, vor der Rückgabe an **Unity**.

## <a name="chapter-9---create-the-sceneorganiser-class"></a>Kapitel 9 – erstellen Sie die SceneOrganiser-Klasse

Diese Klasse führt Folgendes aus:

-   Einrichten der *Main Camera* durch Anfügen der entsprechenden Komponenten zu.

-   Wenn ein Objekt erkannt wird, ist sie werden verantwortlich für die Berechnung von seiner Position in der realen Welt und den Ort einer **Tag-Bezeichnung** es mit dem entsprechenden in der Nähe **Tagnamen**.    

Diese Klasse zu erstellen:

1.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie dann auf **erstellen** > **C\# Skript**. Nennen Sie das Skript **SceneOrganiser**.

2.  Doppelklicken Sie auf die neue **SceneOrganiser** Skript öffnen Sie ihn mit **Visual Studio.**

3.  Stellen Sie sicher, dass die folgenden Namespaces, die oben genannten der **SceneOrganiser** Klasse:

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  Klicken Sie dann fügen Sie die folgenden Variablen in der **SceneOrganiser** Klasse, über die **Start()** Methode:

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

5.  Löschen der **Start()** und **Update()** Methoden.

6.  Fügen Sie unterhalb der Variablen, die **Awake()** -Methode, die Initialisieren der Klasse und der Szene eingerichtet wird.

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

7.  Hinzufügen der **PlaceAnalysisLabel()** -Methode, die wird *Instantiate* die Bezeichnung in der Szene (was an diesem Punkt für den Benutzer unsichtbar ist). Es wird auch die Quad (auch nicht sichtbar), in dem das Bild wird gespeichert und überschneidet sich mit der realen Welt. Dies ist wichtig, da die Koordinaten des Felds aus dem Dienst abgerufen werden, nach der Analyse wird zurück in diese Quad bestimmt die ungefähre Position des Objekts in der realen Welt verfolgt. 

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

8.  Hinzufügen der **FinaliseLabel()** Methode. Er ist verantwortlich für:

    *   Festlegen der *Bezeichnung* Text mit der *Tag* der Vorhersage mit der höchsten Sicherheit.
    *   Die Berechnung von Aufrufen der *umgebende Feld* auf das Vierfache Objekt, das zuvor positioniert und die Bezeichnung in der Szene platzieren.
    *   Anpassen der Bezeichnung Tiefe mithilfe einer Raycast für die *umgebende Feld*, die für das Objekt in der realen Welt in Konflikt stehen sollten.
    * Zurücksetzen des Capture-Prozess, um dem Benutzer ermöglichen, ein anderes Bild zu erfassen.

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

9.  Hinzufügen der **CalculateBoundingBoxPosition()** -Methode, die eine Anzahl von Berechnungen, die zum Übersetzen hostet die *umgebende Feld* Koordinaten aus dem Dienst abgerufen und neu erstellen proportional in der Quad.

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

10. Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio**, vor der Rückgabe an **Unity**.

    > [!IMPORTANT]
    > Bevor Sie fortfahren, öffnen Sie die **CustomVisionAnalyser** -Klasse, und innerhalb der **AnalyseLastImageCaptured()** -Methode, *heben Sie die auskommentierung* die folgenden Zeilen:
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
> Führen Sie sich keine Gedanken über die **digitale Bilder** Klasse 'konnte nicht gefunden werden kann'-Nachricht, erstellen Sie ihn im nächsten Kapitel.


## <a name="chapter-10---create-the-imagecapture-class"></a>Kapitel 10 – erstellen Sie die digitale Bilder-Klasse

Die nächste Klasse, die Sie erstellen wollen ist die **digitale Bilder** Klasse.

Diese Klasse ist zuständig für:

*   Erfassen eines Abbilds verwenden der Kamera HoloLens und speichern ihn in das *App* Ordner.
*   Behandeln von *Tippen Sie auf* Bewegungen des Benutzers.

Diese Klasse zu erstellen:

1.  Wechseln Sie zu der **Skripts** Ordner, die Sie zuvor erstellt haben.

2.  Mit der rechten Maustaste in den Ordner, und klicken Sie dann **erstellen** > **C\# Skript**. Nennen Sie das Skript **digitale Bilder**.

3.  Doppelklicken Sie auf die neue **digitale Bilder** Skript öffnen Sie ihn mit **Visual Studio.**

4.  Ersetzen Sie die Namespaces am Anfang der Datei durch Folgendes:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  Klicken Sie dann fügen Sie die folgenden Variablen in der **digitale Bilder** Klasse, über die **Start()** Methode:

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

6.  Code für **Awake()** und **Start()** Methoden jetzt hinzugefügt werden muss:

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

7.  Implementieren Sie einen Handler, der aufgerufen wird, wenn eine Tap-Bewegung erfolgt:

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
    > Wenn der Cursor befindet sich **Grün**, bedeutet dies, dass die Kamera verfügbar ist, wird das Bild. Wenn der Cursor befindet sich **roten**, bedeutet dies, dass die Kamera ausgelastet.

8.  Fügen Sie die Methode, die die Anwendung verwendet wird, starten den Prozess der abbilderfassung aus, und speichern Sie das Abbild hinzu:

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

9.  Fügen Sie die Handler, die aufgerufen werden, wenn das Foto aufgezeichnet wurde und wann es analysiert werden kann. Das Ergebnis wird dann zum Übergeben der **CustomVisionAnalyser** für die Analyse.

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

10. Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio**, vor der Rückgabe an **Unity**.

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>Kapitel 11: die Skripts in der Szene einrichten

Nun, da Sie alle für dieses Projekt erforderlichen Code geschrieben haben, ist an der Zeit, um die Skripts in der Szene, und klicken Sie auf den prefabs (Vorlagen für ordnungsgemäß Verhalten) einzurichten.

1.  In der **Unity-Editor**in die **Hierarchie Bereich**, wählen die **Main Camera**.
2.  In der **Inspektor Bereich**, mit der **Main Camera** ausgewählt haben, klicken Sie auf **Add Component**, suchen Sie nach **SceneOrganiser** Skript und Doppelklicken Sie auf, um sie hinzuzufügen.

    ![](images/AzureLabs-Lab310-38.png)

3.  In der **Projektfenster**öffnen die **Ordner "Prefabs"**, ziehen Sie die **Bezeichnung** prefab in die *Bezeichnung* leere Verweisziel Geben Sie im Bereich der **SceneOrganiser** -Skript, das Sie gerade hinzugefügt haben die *Main Camera*, wie in der folgenden Abbildung gezeigt:

    ![](images/AzureLabs-Lab310-39.png)

4.  In der **Hierarchie Bereich**, wählen die **GazeCursor** untergeordnetes Element von der **Main Camera**.
5.  In der **Inspektor Bereich**, mit der **GazeCursor** ausgewählt haben, klicken Sie auf **Add Component**, suchen Sie nach **GazeCursor** Skript und Doppelklicken Sie auf, um sie hinzuzufügen.

    ![](images/AzureLabs-Lab310-40.png)

6.  Auch hier gilt die **Hierarchie Bereich**, wählen die **SpatialMapping** untergeordnetes Element von der **Main Camera**.
7.  In der **Inspektor Bereich**, mit der **SpatialMapping** ausgewählt haben, klicken Sie auf **Add Component**, suchen Sie nach **SpatialMapping** Skript und doppelklicken Sie darauf, um es hinzuzufügen.

    ![](images/AzureLabs-Lab310-41.png)

Die verbleibenden Skripts, die Sie haben keine Gruppe wird hinzugefügt werden, indem der Code in die **SceneOrganiser** Skript während der Laufzeit.

## <a name="chapter-12---before-building"></a>Kapitel 12 – vor dem Erstellen

Zur Durchführung einer gründliche Tests Ihrer Anwendung werden Sie querladen möchten sie auf Ihre Microsoft HoloLens benötigen.

Vor dem Ausführen, stellen Sie sicher, dass:

-  Alle Einstellungen, die bereits erwähnt, der [Kapitel 3](#chapter-3---set-up-the-unity-project) ordnungsgemäß festgelegt sind.
- Das Skript **SceneOrganiser** angefügt ist die **Main Camera** Objekt.
- Das Skript **GazeCursor** angefügt ist die **GazeCursor** Objekt.
- Das Skript **SpatialMapping** angefügt ist die **SpatialMapping** Objekt.
- In [Kapitel 5](#chapter-5---create-the-customvisionanalyser-class), Schritt 6:

    - Stellen Sie sicher, Sie fügen Ihre **Dienstschlüssel für die Vorhersage** in die **PredictionKey** Variable.
    - Sie eingefügt haben Ihre **Endpunkt der Vorhersage** in die **PredictionEndpoint** Klasse.

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>Kapitel 13 – erstellen Sie die UWP-Projektmappe, und Laden Ihre Anwendung

Sie können nun möchten Sie die Anwendung als UWP-Lösung zu erstellen, die Sie an den Microsoft HoloLens bereitstellen können. Um den Buildprozess zu starten:

1.  Wechseln Sie zu **Datei > Buildeinstellungen**.

2.  Teilstriche **Unity C\# Projekte**.

3.  Klicken Sie auf **Hinzufügen von Open Szenen**. Dadurch wird die derzeit geöffnete Szene mit dem Build hinzugefügt.

    ![](images/AzureLabs-Lab310-42.png)

4.  Klicken Sie auf **Erstellen**. Unity startet eine *Datei-Explorer* Fenster, in denen man erstellen, und wählen Sie einen Ordner zum Erstellen der app in. Erstellen Sie jetzt auf diesen Ordner, und nennen Sie es **App**. Klicken Sie dann mit der **App** Ordner ausgewählt haben, klicken Sie auf **Ordner auswählen**.

5.  Erstellen Ihres Projekts zu Unity beginnt die **App** Ordner.

6.  Einmal Unity wurde (es kann einige Zeit dauern) erstellen, öffnen ein **Datei-Explorer** Fenster am Speicherort des Builds (Überprüfen Sie Ihre Taskleiste aus, wie es unter Umständen nicht immer über Ihre Windows angezeigt und Sie über das Hinzufügen eines neuen benachrichtigt Fenster ").

7.  Um sich bei Microsoft HoloLens bereitzustellen, benötigen Sie die IP-Adresse des Geräts (für Remote bereitstellen), und um außerdem sicherzustellen, dass es hat **Entwicklermodus** festgelegt. Gehen Sie dazu wie folgt vor:

    1.  Während Ihre HoloLens steht, geteert, öffnen Sie die **Einstellungen**.

    2.  Wechseln Sie zu **Netzwerk und Internet** > **Wi-Fi** > **erweiterte Optionen**

    3.  Beachten Sie die **IPv4** Adresse.

    4.  Navigieren Sie als Nächstes zurück zum **Einstellungen**, und klicken Sie dann **Update und Sicherheit** > **für Entwickler**

    5.  Legen Sie **Entwicklermodus** *auf*.

8.  Navigieren Sie zu Ihrem neuen Unity-Build (die **App** Ordner), und öffnen Sie die Projektmappendatei mit **Visual Studio**.

9.  In der Projektmappenkonfiguration Select **Debuggen**.

10. Wählen Sie in der Plattform für die Projektmappe **X86, Remotecomputer**. Werden Sie aufgefordert, fügen Sie der **IP-Adresse** von einem Remotegerät (die Microsoft HoloLens, in diesem Fall, den Sie notiert haben).

    ![](images/AzureLabs-Lab310-43.png)

11. Wechseln Sie zu der **erstellen** Menü, und klicken Sie auf **Projektmappe bereitstellen** zum querladen der Anwendung in Ihrem HoloLens.

12. Ihre app sollte nun in der Liste der installierten apps auf Ihre Microsoft HoloLens, möchten Sie die gestartet werden, angezeigt werden.

### <a name="to-use-the-application"></a>Die Anwendung zu verwenden:

* Sehen Sie sich ein Objekt, das mit dem Sie trainiert haben Ihre **Azure Custom Vision Service, Objekterkennung**, und verwenden Sie die **tippen**.
* Wenn das Objekt erfolgreich erkannt wird, einen Raum *Bezeichnungstext* wird mit den Namen des Tags angezeigt.

> [!IMPORTANT]
> Jedes Mal, wenn Sie ein Foto zu erfassen und an den Dienst senden, können Sie wechseln Sie zurück zu der Seite des Diensts und Trainieren den Dienst mit den neu aufgenommenen Bildern. Zu Beginn, wahrscheinlich werden Sie müssen auch korrigieren der *umgebende Felder* genauer sein und den Dienst erneut zu trainieren.

> [!NOTE]
> Der Text der Bezeichnung platziert möglicherweise nicht in der Nähe des Objekts angezeigt, wenn der Microsoft HoloLens-Sensor und/oder die SpatialTrackingComponent in Unity ein Fehler auftritt, platzieren Sie den entsprechenden collider, relativ zu der realen Welt-Objekten. Versuchen Sie, die die Anwendung auf einer anderen Oberfläche verwenden, wenn dies der Fall ist.

## <a name="your-custom-vision-object-detection-application"></a>Ihre Custom Vision, Objekterkennung-Anwendung

Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die Azure Custom Vision, Detection-API-Objekt, das ein Objekt aus einem Bild erkennen können, und geben Sie eine ungefähre Position für das Objekt im 3D-Raum, nutzt.

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>Bonus-Übungen

### <a name="exercise-1"></a>Übung 1

Hinzufügen, das die Textbezeichnung einen semitransparente Cube verwenden, um das eigentliche Objekt in ein 3D-Diagrammlayout zu umschließen *umgebende Feld*.

### <a name="exercise-2"></a>Übung 2

Schulen Sie Ihre Custom Vision Service, weitere Objekte zu erkennen.

### <a name="exercise-3"></a>Übung 3

Wiedergeben Sie Sound, wenn ein Objekt erkannt wird.

### <a name="exercise-4"></a>Übung 4

Verwenden Sie die API des Diensts mit der gleichen Images erneut zu trainieren Ihrer app analysiert, also um den Dienst mehr Genauigkeit zu gewährleisten (sowohl Vorhersagen und Trainieren gleichzeitig ausgeführt werden).
