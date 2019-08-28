---
title: Mr und Azure 302b-benutzerdefinierte Vision
description: Machen Sie sich mit diesem Kurs vertraut, um zu erfahren, wie Sie ein Machine Learning-Modell trainieren, und verwenden Sie dann das trainierte Modell, um ähnliche Objekte in einer gemischten Realität zu erkennen.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Custom Vision, hololens, immersive, VR
ms.openlocfilehash: b173648e2e829e94e47306277bd7814a19842cae
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047209"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.

<br>

# <a name="mr-and-azure-302b-custom-vision"></a>Mr und Azure 302b: Benutzerdefinierte Vision

In diesem Kurs erfahren Sie, wie Sie benutzerdefinierte visuelle Inhalte in einem bereitgestellten Image erkennen können, indem Sie die Funktionen von Azure Custom Vision in einer Mixed Reality-Anwendung verwenden.

Mit diesem Dienst können Sie ein Machine Learning-Modell mithilfe von Objekt Images trainieren. Sie verwenden dann das trainierte Modell, um ähnliche Objekte zu erkennen, die von der Kamera Erfassung von Microsoft hololens oder einer Kamera bereitgestellt werden, die mit Ihrem PC für immersive (VR) Headsets verbunden ist.

![Kurs Ergebnis](images/AzureLabs-Lab302b-00.png)

Bei Azure Custom Vision handelt es sich um einen Microsoft Cognitive Service, der Entwicklern das Erstellen benutzerdefinierter Image Klassifizierer ermöglicht. Diese Klassifizierungen können dann mit neuen Bildern verwendet werden, um Objekte innerhalb dieses neuen Bilds zu erkennen oder zu klassifizieren. Der Dienst bietet ein einfaches, leicht zu verwendende Onlineportal, um den Prozess zu optimieren. Weitere Informationen finden Sie auf der [Seite Azure Custom Vision Service](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).

Nach Abschluss dieses Kurses verfügen Sie über eine Mixed Reality-Anwendung, die in zwei Modi arbeiten kann:

-   **Analysemodus**: Manuelles Einrichten der Custom Vision Service durch Hochladen von Bildern, Erstellen von Tags und trainieren des Dienstanbieter, um unterschiedliche Objekte (in diesem Fall Maus und Tastatur) zu erkennen. Anschließend erstellen Sie eine hololens-APP, mit der Bilder mithilfe der Kamera erfasst werden, und versuchen, diese Objekte in der realen Welt zu erkennen.

-   **Schulungs Modus**: Sie implementieren Code, der einen "Schulungs Modus" in ihrer App aktiviert. Der Trainingsmodus ermöglicht Ihnen das Erfassen von Bildern mithilfe der Kamera von hololens, das Hochladen der aufgezeichneten Images in den Dienst und das Trainieren des benutzerdefinierten Vision-Modells.

In diesem Kurs erfahren Sie, wie Sie die Ergebnisse aus dem Custom Vision Service in einer Unity-basierten Beispielanwendung erhalten. Sie müssen diese Konzepte auf eine benutzerdefinierte Anwendung anwenden, die Sie möglicherweise aufbauen.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> Mr und Azure 302b: Benutzerdefinierte Vision</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Dieser Kurs konzentriert sich in erster Linie auf hololens, aber Sie können auch das Erlernen, was Sie in diesem Kurs lernen, auf Windows Mixed Reality-(VR)-Headsets. Da immersive Headsets (VR) nicht über barrierefreie Kameras verfügen, benötigen Sie eine externe Kamera, die mit Ihrem PC verbunden ist. Wenn Sie den Kurs befolgen, finden Sie Hinweise zu allen Änderungen, die Sie möglicherweise für die Unterstützung von immersiven (VR)-Headsets verwenden müssen.

## <a name="prerequisites"></a>Erforderliche Komponenten

> [!NOTE]
> Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen. Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Juli 2018). Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](install-the-tools.md) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt werden.

Für diesen Kurs empfehlen wir die folgende Hardware und Software:

- Einen Entwicklungs-PC, der [mit der Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for Immersive (VR)-Headset-Entwicklung kompatibel ist
- [Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus](install-the-tools.md#installation-checklist)
- [Das neueste Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Ein [Windows Mixed Reality-Headset (VR)](immersive-headset-hardware-details.md) oder [Microsoft hololens](hololens-hardware-details.md) mit aktiviertem Entwicklermodus
- Eine Kamera, die mit Ihrem PC verbunden ist (für die immersive Headset-Entwicklung)
- Internet Zugriff für den Azure-Setup-und Custom Vision-API-Abruf
- Für jedes Objekt, das von der Custom Vision Service erkannt werden soll, wird eine Reihe von mindestens fünf (10) Bildern empfohlen. Wenn Sie möchten, können Sie [die Images verwenden, die bereits mit diesem Kurs bereitgestellt werden (Computermaus und Tastatur) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).

## <a name="before-you-start"></a>Bevor Sie beginnen

1.  Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).
2.  Richten Sie Ihre hololens ein, und testen Sie Sie. Wenn Sie Unterstützung für die Einrichtung ihrer hololens benötigen, [besuchen Sie den Artikel zum Einrichten von hololens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Es empfiehlt sich, eine Kalibrierung und Sensor Optimierung durchzuführen, wenn Sie mit der Entwicklung einer neuen hololens-App beginnen (manchmal kann es hilfreich sein, diese Aufgaben für jeden Benutzer auszuführen). 

Hilfe zur Kalibrierung finden Sie unter diesem [Link zum Artikel zur hololens-Kalibrierung](calibration.md#hololens-2).

Hilfe zur Sensor Optimierung finden Sie unter diesem [Link zum Artikel zur Überwachung von hololens-Sensoren](sensor-tuning.md).

## <a name="chapter-1---the-custom-vision-service-portal"></a>Kapitel 1: das Custom Vision Service-Portal

Um die *Custom Vision Service* in Azure verwenden zu können, müssen Sie eine Instanz des-Dienstanbieter konfigurieren, die für die Anwendung verfügbar gemacht wird.

1.  [Navigieren Sie zunächst zur *Custom Vision Service* Hauptseite](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).

2.  Klicken Sie auf die Schaltfläche **Get Started** .

    ![](images/AzureLabs-Lab302b-01.png)

3.  Melden Sie sich beim *Custom Vision Service* -Portal an.

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen. Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.

4.  Wenn Sie sich zum ersten Mal angemeldet haben, werden Sie im Bereich mit den *Nutzungsbedingungen* aufgefordert. Aktivieren Sie das Kontrollkästchen, um den Bedingungen zuzustimmen. Klicken Sie dann auf **Ich stimme**zu.

    ![](images/AzureLabs-Lab302b-03.png)

5.  Nachdem Sie die Bedingungen zugestimmt haben, werden Sie zum Abschnitt " *Projekte* " im Portal navigiert. Klicken Sie auf **Neues Projekt**.

    ![](images/AzureLabs-Lab302b-04.png)

6.  Eine Registerkarte wird auf der rechten Seite angezeigt, auf der Sie aufgefordert werden, einige Felder für das Projekt anzugeben.

    1.  Fügen Sie einen *Namen* für das Projekt ein.

    2.  Fügen Sie eine *Beschreibung* für das Projekt ein (*optional*).

    3.  Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue *Ressourcengruppe* . Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Kursen) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.

    4. Festlegen der *Projekttypen* auf **Klassifizierung**
    
    5. Legen Sie die *Domänen* als **Allgemein**fest.

        ![](images/AzureLabs-Lab302b-05.png)

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

7.  Wenn Sie fertig sind, klicken Sie auf **Projekt erstellen**. Sie werden auf die Seite Custom Vision Service, Projekt, umgeleitet.

## <a name="chapter-2---training-your-custom-vision-project"></a>Kapitel 2: trainieren Ihres Custom Vision Projekts

Wenn Sie sich im Custom Vision Portal befinden, besteht das Hauptziel darin, das Projekt zu trainieren, um bestimmte Objekte in Bildern zu erkennen. Sie benötigen mindestens fünf (5) Images, obwohl zehn (10) für jedes Objekt bevorzugt werden, das Ihre Anwendung erkennen soll. [Sie können die Bilder verwenden, die mit diesem Kurs bereitgestellt werden (Computermaus und Tastatur)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip). 

So trainieren Sie das Custom Vision Service Projekt:

1.  Klicken Sie auf **+** die Schaltfläche neben **Tags.**

    ![](images/AzureLabs-Lab302b-06.png)

2.  Fügen Sie den **Namen** des Objekts hinzu, das Sie erkennen möchten. Klicken Sie auf **Speichern**.

    ![](images/AzureLabs-Lab302b-07.png)

3.  Sie werden feststellen, dass Ihr **Tag** hinzugefügt wurde (möglicherweise müssen Sie die Seite erneut laden, damit es angezeigt wird). Aktivieren Sie das Kontrollkästchen neben dem neuen Tag, wenn es nicht bereits aktiviert ist.

    ![](images/AzureLabs-Lab302b-08.png)

4.  Klicken Sie in der Mitte der Seite auf **Bilder hinzufügen** .

    ![](images/AzureLabs-Lab302b-09.png)

5.  Klicken Sie auf **lokale Dateien durchsuchen**, suchen Sie, und wählen Sie dann die Images aus, die Sie hochladen möchten, mit dem Minimalwert fünf (5). Denken Sie daran, dass alle diese Images das Objekt enthalten sollten, das Sie trainieren.

    > [!NOTE]
    >  Sie können mehrere Bilder gleichzeitig zum Hochladen auswählen.

6.  Wenn Sie die Bilder auf der Registerkarte sehen können, wählen Sie im Feld **Meine Tags** das entsprechende Tag aus.

    ![](images/AzureLabs-Lab302b-10.png)

7.  Klicken Sie auf **Dateien hochladen**. Die Dateien werden hochgeladen. Nachdem Sie den Upload bestätigt haben, klicken Sie auf **done**.

    ![](images/AzureLabs-Lab302b-11.png)

8.  Wiederholen Sie den Vorgang, um ein neues **Tag** mit dem Namen **Tastatur** zu erstellen, und laden Sie die entsprechenden Fotos dafür hoch. Wenn Sie die neuen Tags erstellt haben, **Deaktivieren** Sie die *Maus* , um das Fenster *Bilder hinzufügen* anzuzeigen.

9.  Nachdem Sie beide Tags eingerichtet haben, klicken Sie auf **trainieren**, und die erste Trainings Iterationen wird erstellt.

    ![](images/AzureLabs-Lab302b-12.png)

10. Nachdem Sie erstellt wurde, können Sie zwei Schaltflächen mit dem Namen " **default** " und die **Vorhersage-URL**anzeigen. Klicken Sie zuerst auf **Standardwert erstellen** , und klicken Sie dann auf **Vorhersage-URL**.

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > Die Endpunkt-URL, die von diesem bereitgestellt wird, wird auf den Wert festgelegt, welcher *iterations* Wert als Standard markiert wurde. Wenn Sie später eine neue *iterations* Zeit erstellen und diese als Standard aktualisieren, müssen Sie den Code nicht ändern.

11. Nachdem Sie auf die *Vorhersage-URL*geklickt haben, öffnen Sie *Notepad*, kopieren Sie die **URL** und den **Vorhersage Schlüssel**, und fügen Sie Sie ein, damit Sie Sie später im Code abrufen können.

    ![](images/AzureLabs-Lab302b-14.png)

12. Klicken Sie rechts oben auf dem Bildschirm auf das **Zahnrad** Symbol.

    ![](images/AzureLabs-Lab302b-15.png)

13. Kopieren Sie den **Trainings Schlüssel** , und fügen Sieihn zur späteren Verwendung in einen Editor ein.

    ![](images/AzureLabs-Lab302b-16.png)

14. Kopieren Sie auch die **Projekt-ID**, und fügen Sie Sie zur späteren Verwendung in die *Notepad* -Datei ein.

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Kapitel 3: Einrichten des Unity-Projekts

Folgendes ist eine typische Einrichtung für die Entwicklung mit gemischter Realität und ist daher eine gute Vorlage für andere Projekte.

1.  Öffnen Sie *Unity* , und klicken Sie auf **neu**.

    ![](images/AzureLabs-Lab302b-17.png)

2.  Sie müssen nun einen Unity-Projektnamen angeben. Fügen Sie **azurecustomvision ein.** Stellen Sie sicher, dass die Projektvorlage auf **3D**festgelegt ist. Legen Sie den Speicherort auf einen geeigneten **Speicherort** fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind). Klicken Sie dann auf **Projekt erstellen**.

    ![](images/AzureLabs-Lab302b-18.png)

3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist. Wechseln Sie zu **Einstellungen* *Bearbeiten* > * , und navigieren Sie dann im neuen Fenster zu **externe Tools**. Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**. Schließen Sie das Fenster " **Einstellungen** ".

    ![](images/AzureLabs-Lab302b-19.png)

4.  Navigieren Sie als nächstes zu **Datei >** Buildeinstellungen, wählen Sie **universelle Windows-Plattform**aus, und klicken Sie dann auf die Schaltfläche **Plattform wechseln** , um Ihre Auswahl zu übernehmen

    ![](images/AzureLabs-Lab302b-20.png)

5.  In **Datei >** Buildeinstellungen, und stellen Sie Folgendes sicher:

    1.  **Zielgerät** ist auf **hololens** festgelegt

        > Legen Sie für die immersiven Headsets das **Zielgerät** auf *ein beliebiges Gerät*fest.
        
    2.  Der Buildtyp ist auf **D3D** festgelegt.
    3.  **SDK** ist auf **neueste installierte** Version festgelegt.
    4.  **Visual Studio-Version** ist auf **neueste installierte** Version festgelegt.
    5.  **Build und Run** sind auf **lokaler Computer** festgelegt.
    6.  Speichern Sie die Szene, und fügen Sie Sie dem Build hinzu. 

        1. Wählen Sie hierzu die Option **geöffnete Szenen hinzufügen**aus. Ein Fenster zum Speichern wird angezeigt.

            ![](images/AzureLabs-Lab302b-21.png)

        2. Erstellen Sie einen neuen Ordner für dieses und jede zukünftige Szene, und wählen Sie dann die Schaltfläche **neuer Ordner** aus, um einen neuen Ordner zuerstellen.

            ![](images/AzureLabs-Lab302b-22.png)

        3. Öffnen Sie den neu erstellten Ordner **Szenen** , geben Sie im Feld *Dateiname:* Text den Text **customvisionscene**ein, und klicken Sie dann auf **Speichern**.

            ![](images/AzureLabs-Lab302b-23.png)

            > Beachten Sie, dass Sie Ihre Unity-Szenen im Ordner " *Assets* " speichern müssen, da Sie dem Unity-Projekt zugeordnet werden müssen. Das Erstellen eines Szenen Ordners (und anderer ähnlicher Ordner) ist eine typische Methode zum Strukturieren eines Unity-Projekts.
            
    7.  Die restlichen Einstellungen in denBuildeinstellungen sollten vorerst als Standard belassen werden.

        ![](images/AzureLabs-Lab302b-24.png)

6.  Klicken Sie im Fenster Buildeinstellungen auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der *Inspektor* befindet.

7. In diesem Bereich müssen einige Einstellungen überprüft werden:

    1.  Auf der Registerkarte **andere Einstellungen** :

        1.  Die CLR- **Lauf Zeit Version** sollte **experimentell sein (.NET 4,6-Entsprechung)** , wodurch der Editor neu gestartet werden muss.

        2. **Skript** -Back-End sollte **.net** sein

        3. **API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten

        ![](images/AzureLabs-Lab302b-25.png)

    2.  Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:

        1. **Internet Client deklarieren**

        2.  **Webcam**

        3. **Tritt**

        ![](images/AzureLabs-Lab302b-26.png)

    3.  Weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), **unterstützt Tick Virtual Reality**, stellen Sie sicher, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.

    ![](images/AzureLabs-Lab302b-27.png)

8.  Zurück in Buildeinstellungen: *Unity-C\# -Projekte* sind nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen neben this.

9.  Schließen Sie das Fenster mit den Buildeinstellungen.

10.  Speichern Sie Ihre Szene und Ihr Projekt (**Datei > Speichern Sie Szenen/Dateien > Speichern**Sie das Projekt).


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a>Kapitel 4: Importieren der newtonsoft-dll in Unity

> [!IMPORTANT]
> Wenn Sie die *Unity-Setup* Komponente dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie dieses [Azure-Mr-302b. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage)herunterladen, es als [**benutzerdefiniertes Paket**](https://docs.unity3d.com/Manual/AssetPackages.html)in Ihr Projekt importieren und dann aus [Kapitel 6 fortfahren. ](#chapter-6---create-the-customvisionanalyser-class).

Für diesen Kurs muss die **newtonsoft** -Bibliothek verwendet werden, die Sie Ihren Assets als dll hinzufügen können. Das Paket, das [Diese Bibliothek enthält, kann von diesem Link heruntergeladen werden](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).
Verwenden Sie das Unity-Paket, das in diesem Kurs verwendet wurde, um die newtonsoft-Bibliothek in Ihr Projekt zu importieren.

1.  Fügen Sie das *. unitypackage* zu Unity hinzu, indem Sie die Menüoption **Assets* > *Import* *Package* > *Custom* *Package** verwenden.

2.  Vergewissern Sie sich, dass im Feld **Unity-Paket importieren** , das angezeigt wird, alles unter (und einschließlich) Plug-ins ausgewählt ist.

    ![](images/AzureLabs-Lab302b-28.png)

3.  Klicken Sie auf die Schaltfläche **importieren** , um dem Projekt die Elemente hinzuzufügen.

4.  Wechseln Sie in der Projektansicht in den Ordner **Newton Soft** unter Plug-in, und wählen Sie das *Newton Soft. JSON-Plug*-in aus.

    ![](images/AzureLabs-Lab302b-29.png)

5.  Vergewissern Sie sich, dass dieOption " *newtonsoft. JSON* " ausgewähltist, und stellen Sie sicher, dass **alle Plattformen** deaktiviert sind. Stellen Sie dann sicher, dass **wsaplayer** ebenfalls deaktiviert ist. Dies dient nur zur Bestätigung, dass die Dateien ordnungsgemäß konfiguriert sind.

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > Wenn Sie diese Plug-ins markieren, werden Sie nur im Unity-Editor verwendet. Im WSA-Ordner gibt es eine andere Gruppe, die verwendet wird, nachdem das Projekt aus Unity exportiert wurde.

6.  Als nächstes müssen Sie den Ordner " **WSA** " im Ordner " **newtonsoft** " öffnen. Es wird eine Kopie derselben Datei angezeigt, die Sie soeben konfiguriert haben. Wählen Sie die Datei aus, und vergewissern Sie sich dann im Inspektor, dass
    -   **Jede Plattform** ist deaktiviert. 
    -   **nur** **Wsaplayer** ist **aktiviert**
    -   "Nicht **verarbeiten** " ist **aktiviert**

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a>Kapitel 5: Kamera Einrichtung

1.  Wählen Sie im Bereich Hierarchie die *Hauptkamera*aus.

2.  Nachdem Sie diese Option ausgewählt haben, können Sie alle Komponenten der *Hauptkamera* im *Inspektor-Panel*sehen.

    1.  Das *Kamera* Objekt muss als **Hauptkamera** benannt werden (Beachten Sie die Schreibweise).

    2.  Das Hauptkamera **Kennzeichen** muss auf **maincamera** festgelegt sein (Beachten Sie die Schreibweise).

    3.  Stellen Sie sicher, dass die **Transformations Position** auf **0, 0, 0** festgelegt ist.

    4.  Legen Sie **klar Flags** auf voll Tonfarbe fest (diese Einstellung wird für immersives Headset ignoriert).

    5.  Legen Sie die **Hintergrund** Farbe der Kamera Komponente auf **schwarz, Alpha 0 (Hexadezimal Code: #00000000)** fest (Dies wird für das immersive Headset ignoriert).

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a>Kapitel 6: Erstellen der customvisionanalyser-Klasse.

An diesem Punkt können Sie Code schreiben.

Sie beginnen mit der *customvisionanalyser* -Klasse.

> [!NOTE]
> Die Aufrufe der **Custom Vision Service** , die im unten gezeigten Code vorgenommen wurden, werden mithilfe der **Custom Vision Rest-API**vorgenommen. Durch die Verwendung dieser API sehen Sie, wie Sie diese API implementieren und nutzen können (nützlich, um zu verstehen, wie Sie etwas ähnliches implementieren können). Beachten Sie, dass Microsoft ein **Custom Vision Service SDK** bietet, das auch zum Aufrufen des Dienstanbieter verwendet werden kann. Weitere Informationen finden Sie im [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) -Artikel.

Diese Klasse ist für Folgendes zuständig:

-   Das letzte als Bytearray erfasste Bild wird geladen.

-   Das Bytearray wird zur Analyse an Ihre Azure *Custom Vision Service* -Instanz gesendet.

-   Die Antwort wird als JSON-Zeichenfolge empfangen.

-   Deserialisieren der Antwort und übergeben der resultierenden *Vorhersage* an die *sceneorganisator* -Klasse, um die Anzeige der Antwort zu übernehmen.

So erstellen Sie diese Klasse:

1.  Klicken Sie im *Projekt Panel*mit der rechten Maustaste in den *Ordner Asset* , und klicken Sie dann auf **> Ordner erstellen**. Nennen Sie die Ordner **Skripts**.

    ![](images/AzureLabs-Lab302b-33.png)

2.  Doppelklicken Sie auf den soeben erstellten Ordner, um ihn zu öffnen.

3.  Klicken Sie mit der rechten Maustaste in den Ordner, und klicken Sie dann auf **\# Skript** **Erstellen** > . Benennen Sie das Skript *customvisionanalyser*.

4.  Doppelklicken Sie auf das neue *customvisionanalyser* -Skript, um es in **Visual Studio**zu öffnen.

5.  Aktualisieren Sie die Namespaces am Anfang der Datei so, dass Sie den folgenden entsprechen:

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  Fügen Sie in der *customvisionanalyser* -Klasse die folgenden Variablen hinzu:

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > Stellen Sie sicher, dass Sie den **Vorhersage Schlüssel** in die " **prätionkey** "-Variable und den **Vorhersage Endpunkt** in die " **prätionendpoint** "-Variable Sie haben diese zuvor im Kurs in *Notepad* kopiert.

7.  Code für **Awa()** muss nun hinzugefügt werden, um die Instanzvariable zu initialisieren:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  Löschen Sie die Methoden " **Start ()** " und " **Update ()** ".

9.  Fügen Sie als nächstes die Coroutine hinzu (mit der statischen **getimageasbytearray ()** -Methode darunter), die die Ergebnisse der Analyse des Bilds erhält, das von der *imagecapture* -Klasse erfasst wird.

    > [!NOTE]
    > In der **analyseimagecapture** -Coroutine gibt es einen Aufrufen der *sceneorganisator* -Klasse, die Sie noch erstellen müssen. Deshalb sollten Sie **diese Zeilen jetzt kommentiert lassen**.

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
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

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
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

10.  Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio** speichern, bevor Sie zu **Unity**zurückkehren.

## <a name="chapter-7---create-the-customvisionobjects-class"></a>Kapitel 7: Erstellen der customvisionobjects-Klasse

Die Klasse, die Sie jetzt erstellen, ist die *customvisionobjects* -Klasse.

Dieses Skript enthält eine Reihe von Objekten, die von anderen Klassen zum Serialisieren und Deserialisieren der Aufrufe an die *Custom Vision Service*verwendet werden.

> [!WARNING]
> Beachten Sie, dass Sie den Endpunkt beachten, den die Custom Vision Service bereitstellt, da die folgende JSON-Struktur für die Arbeit mit [*Custom Vision Vorhersage v 2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290)eingerichtet wurde. Wenn Sie über eine andere Version verfügen, müssen Sie möglicherweise die folgende Struktur aktualisieren.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste in den Ordner >  **\# Skripts**, und klicken Sie dann auf Skript **Erstellen**. Nennen Sie das Skript *customvisionobjects*.

2.  Doppelklicken Sie auf das neue **customvisionobjects** -Skript, um es in **Visual Studio**zu öffnen.

3.  Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Löschen Sie die Methoden " **Start ()** " und " **Update ()** " in der Klasse " *customvisionobjects* ". Diese Klasse sollte nun leer sein.

5.  Fügen Sie die folgenden Klassen **außerhalb** der *customvisionobjects* -Klasse hinzu. Diese Objekte werden von der *newtonsoft* -Bibliothek verwendet, um die Antwortdaten zu serialisieren und zu deserialisieren:

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
    /// JSON of Images submitted
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
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a>Kapitel 8: Erstellen der voicerecognizer-Klasse

Diese Klasse erkennt die Spracheingabe des Benutzers.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste in den Ordner >  **\# Skripts**, und klicken Sie dann auf Skript **Erstellen**. Nennen Sie das Skript *voicerecognizer*.

2.  Doppelklicken Sie auf das neue **voicerecognizer** -Skript, um es in **Visual Studio**zu öffnen.

3.  Fügen Sie die folgenden Namespaces oberhalb der *voicerecognizer* -Klasse hinzu:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  Fügen Sie dann die folgenden Variablen in der *voicerecognizer* -Klasse oberhalb der *Start ()* -Methode hinzu:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  Fügen Sie die Methoden " **Awa()** " und " **Start ()** " hinzu, bei denen die Benutzer Schlüsselwörter so eingerichtet werden, dass Sie beim Zuordnen eines Tags zu einem Bild erkannt werden:

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
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  Löschen Sie die **Update ()** -Methode.

7.  Fügen Sie den folgenden Handler hinzu, der immer dann aufgerufen wird, wenn die Spracheingabe erkannt wird:

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio** speichern, bevor Sie zu **Unity**zurückkehren.

> [!NOTE]
> Machen Sie sich keine Sorgen um Code, der möglicherweise einen Fehler enthält, da Sie bald weitere Klassen bereitstellen werden, die diese beheben.

## <a name="chapter-9---create-the-customvisiontrainer-class"></a>Kapitel 9: Erstellen der customvisiontrainer-Klasse

Diese Klasse verkettet eine Reihe von webaufrufen, um die *Custom Vision Service*zu trainieren. Jeder-Befehl wird direkt oberhalb des Codes ausführlich erläutert.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste in den Ordner >  **\# Skripts**, und klicken Sie dann auf Skript **Erstellen**. Nennen Sie das Skript *customvisiontrainer*.

2.  Doppelklicken Sie auf das neue *customvisiontrainer* -Skript, um es in **Visual Studio**zu öffnen.

3.  Fügen Sie die folgenden Namespaces oberhalb der *customvisiontrainer* -Klasse hinzu:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Fügen Sie dann die folgenden Variablen in der *customvisiontrainer* -Klasse oberhalb der **Start ()** -Methode hinzu. 

    > [!NOTE]
    > Die hier verwendete Schulungs-URL wird in der Dokumentation zum *Custom Vision Training 1,2* bereitgestellt und hat eine Struktur von: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/  
    > Weitere Informationen finden Sie in der [*Referenz-API zu Custom Vision Training v 1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).

    > [!WARNING]
    > Beachten Sie, dass Sie den Endpunkt beachten, den der Custom Vision Service für den Trainingsmodus bereitstellt, da die JSON-Struktur (innerhalb der **customvisionobjects** -Klasse) für die Arbeit mit [*Custom Vision Training v 1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f)eingerichtet wurde. Wenn Sie über eine andere Version verfügen, müssen Sie möglicherweise die Struktur der *Objekte* aktualisieren.

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > Stellen Sie sicher, dass Sie den Wert für den **Dienst Schlüssel** (Trainings Schlüssel) und den **Projekt-ID** -Wert hinzufügen, den Sie zuvor notiert haben. Dies sind die Werte, die Sie [zuvor im Portal im Kurs erfasst haben (Kapitel 2, Schritt 10)](#chapter-2---training-your-custom-vision-project).

5.  Fügen Sie die folgenden Methoden " **Start ()** " und " **Awa()** " hinzu. Diese Methoden werden bei der Initialisierung aufgerufen und enthalten den Aufruf, um die Benutzeroberfläche einzurichten:

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
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  Löschen Sie die **Update ()** -Methode. Diese Klasse wird nicht benötigt.

7.  Fügen Sie die **requesttagselection ()** -Methode hinzu. Diese Methode ist die erste, die aufgerufen wird, wenn ein Abbild aufgezeichnet und auf dem Gerät gespeichert wird. es kann nun an die *Custom Vision Service*übermittelt werden, um es zu trainieren. Diese Methode zeigt in der Trainings Benutzeroberfläche eine Reihe von Schlüsselwörtern an, mit denen der Benutzer das erfasste Bild markieren kann. Außerdem wird die *voicerecognizer* -Klasse darauf aufmerksam, dass Sie mit dem lauschen an den Benutzer für die Spracheingabe beginnt.

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  Fügen Sie die **verifytag ()** -Methode hinzu. Diese Methode empfängt die von der **voicerecognizer** -Klasse erkannte Spracheingabe und überprüft deren Gültigkeit und beginnt dann mit dem Trainings Vorgang.

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  Fügen Sie die **subentschärmagefortraining ()** -Methode hinzu. Mit dieser Methode wird der Custom Vision Service trainingprozess gestartet. Der erste Schritt besteht darin, die **Tag-ID** aus dem Dienst abzurufen, der der überprüften Spracheingabe des Benutzers zugeordnet ist. Die **Tag-ID** wird dann zusammen mit dem Bild hochgeladen.

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. Fügen Sie die Methode **traincustomvisionproject ()** hinzu. Nachdem das Bild übermittelt und markiert wurde, wird diese Methode aufgerufen. Es wird eine neue Iterations Vorlage erstellt, die mit allen vorherigen Bildern, die an den Dienst gesendet werden, sowie dem soeben hochgeladenen Image trainiert wird. Nachdem das Training abgeschlossen ist, ruft diese Methode eine Methode auf, um die neu erstellte **iterations** Eigenschaft als **Standard**festzulegen, sodass der Endpunkt, den Sie für die Analyse verwenden, die letzte trainierte Iterations Methode ist.

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. Fügen Sie die **setdefaultiterations ()** -Methode hinzu. Mit dieser Methode wird die zuvor erstellte und trainierte Iterations Methode als *Standard*festgelegt. Nachdem dieser Vorgang abgeschlossen ist, muss diese Methode die vorherige Iterationen löschen, die im Dienst vorhanden sind. Zum Zeitpunkt der Erstellung dieses Kurses gibt es eine Beschränkung von maximal zehn (10) Iterationen, die gleichzeitig im Dienst vorhanden sein dürfen.

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. Fügen Sie die **deletepreviousiterations ()** -Methode hinzu. Diese Methode findet und löscht die vorherige nicht standardmäßige Iterationen:

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. Die letzte Methode, die dieser Klasse hinzugefügt werden soll, ist die **getimageasbytearray ()** -Methode, die für die Webaufrufe verwendet wird, um das in ein Bytearray erfasste Bild zu konvertieren.

    ```csharp
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

14. Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio** speichern, bevor Sie zu **Unity**zurückkehren.

## <a name="chapter-10---create-the-sceneorganiser-class"></a>Kapitel 10: Erstellen der sceneorganisator-Klasse

Diese Klasse führt Folgendes aus:

-   Erstellen Sie ein **Cursor** Objekt, das an die Hauptkamera angehängt werden soll.

-   Erstellen Sie ein Bezeichnungs Objekt, das angezeigt wird, wenn der Dienst die Objekte der realen Welt erkennt.

-   Richten Sie die Hauptkamera ein, indem Sie die entsprechenden Komponenten an Sie anfügen.

-   Wenn Sie sich im **Analysemodus**befinden, können Sie die Bezeichnungen zur Laufzeit im entsprechenden Raum relativ zur Position der Hauptkamera erzeugen und die vom Custom Vision Service empfangenen Daten anzeigen.

-   Erzeugen Sie im **Trainingsmodus**die Benutzeroberfläche, auf der die verschiedenen Phasen des Trainingsprozesses angezeigt werden.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste in den Ordner >  **\# Skripts**, und klicken Sie dann auf Skript **Erstellen**. Nennen Sie das Skript *sceneorganisator*.

2.  Doppelklicken Sie auf das neue *sceneorganisator* -Skript, um es in **Visual Studio**zu öffnen.

3.  Sie benötigen nur einen Namespace, und entfernen Sie die anderen aus der *sceneorganisator* -Klasse:

    ```csharp
    using UnityEngine;
    ```

4.  Fügen Sie dann die folgenden Variablen in der *sceneorganisator* -Klasse oberhalb der **Start ()** -Methode hinzu:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  Löschen Sie die Methoden " **Start ()** " und " **Update ()** ".

6.  Fügen Sie direkt unterhalb der Variablen die **Awa()** -Methode hinzu, die die Klasse initialisiert und die Szene einrichtet.

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  Fügen Sie nun die Methode " **samatecameracursor ()** " hinzu, die den Hauptkamera Cursor erstellt und positioniert, sowie die Methode "Methode **()** ", die das Objekt " **Analyse Bezeichnung** " erstellt.

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. Fügen Sie die **setcamerastatus ()** -Methode hinzu, die Nachrichten verarbeitet, die für das textnetz vorgesehen sind, das den Status der Kamera bereitstellt.

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. Fügen Sie die Methoden **placeanalysislabel ()** und **settagstolastlabel ()** hinzu, die die Daten der Custom Vision Service in der Szene erzeugen und anzeigen.

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. Fügen Sie abschließend die Methode " **itatetrainingui ()** " hinzu, die die Benutzeroberfläche erzeugt, die die verschiedenen Phasen des Trainingsprozesses anzeigt, wenn sich die Anwendung im Trainingsmodus befindet. Diese Methode wird auch zum Erstellen des Kamera Status Objekts verwendet.

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio** speichern, bevor Sie zu **Unity**zurückkehren.

> [!IMPORTANT]
> Bevor Sie fortfahren, öffnen Sie die **customvisionanalyser** -Klasse, und heben Sie die Auskommentierung der folgenden Zeilen innerhalb der **analyselastimageaufgezeichnet ()** -Methode auf:
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a>Kapitel 11: Erstellen der imagecapture-Klasse

Die nächste Klasse, die Sie erstellen, ist die *imagecapture* -Klasse.

Diese Klasse ist für Folgendes zuständig:

-   Erfassen eines Bilds mithilfe der hololens-Kamera und speichern im *App* -Ordner.

-   Behandlung von TAP-Gesten vom Benutzer.

-   Beibehalten des Enumerationswerts, der bestimmt, ob die Anwendung im *Analyse* Modus oder im *Trainings* Modus ausgeführt wird.

So erstellen Sie diese Klasse:

1.  Wechseln Sie zum Ordner " **Scripts** ", den Sie zuvor erstellt haben.

2.  Klicken Sie mit der rechten Maustaste in den Ordner, und klicken Sie dann auf **Create > C\# Script**. Benennen Sie das Skript mit *imagecapture*.

3.  Doppelklicken Sie auf das neue **imagecapture** -Skript, um es in **Visual Studio**zu öffnen.

4.  Ersetzen Sie die Namespaces am Anfang der Datei durch Folgendes:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  Fügen Sie dann die folgenden Variablen in der *imagecapture* -Klasse oberhalb der **Start ()** -Methode hinzu:

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
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

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

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
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

            // Subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  Implementieren Sie einen Handler, der aufgerufen wird, wenn eine Tap-Geste auftritt.

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > Im *Analyse* Modus fungiert die **taphandler** -Methode als Switch zum Starten oder Abbrechen der Foto Erfassungs Schleife.
    >
    > Im *Trainings* Modus wird ein Bild von der Kamera aufgezeichnet.
    >
    > Wenn der Cursor grün ist, bedeutet dies, dass die Kamera verfügbar ist, um das Bild zu übernehmen.
    >
    > Wenn der Cursor rot ist, bedeutet dies, dass die Kamera ausgelastet ist.

8.  Fügen Sie die Methode hinzu, die die Anwendung verwendet, um den Bild Aufzeichnungsprozess zu starten und das Bild zu speichern.

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
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

9.  Fügen Sie die Handler hinzu, die aufgerufen werden, wenn das Foto aufgezeichnet wurde und für die Analyse bereit ist. Das Ergebnis wird dann in Abhängigkeit vom Modus, für den der Code festgelegt ist, an *customvisionanalyser* oder *customvisiontrainer* weitergeleitet.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio** speichern, bevor Sie zu **Unity**zurückkehren.

11. Nachdem alle Skripts abgeschlossen sind, wechseln Sie zurück zum Unity-Editor, und klicken Sie dann auf die Klasse **sceneorganisator** aus dem Ordner **Scripts** auf das **Hauptkamera** Objekt im Bereich *Hierarchie*.

## <a name="chapter-12---before-building"></a>Kapitel 12: vor dem Aufbau

Um eine gründliche Test Ihrer Anwendung durchzuführen, müssen Sie Sie auf Ihre hololens querladen.

Bevor Sie vorgehen, stellen Sie Folgendes sicher:

- Alle in [Kapitel 2](#chapter-2---training-your-custom-vision-project) erwähnten Einstellungen sind richtig festgelegt.

- Alle Felder in der **Hauptkamera**, Inspektor Panel, sind ordnungsgemäß zugewiesen.

- Das Skript **sceneorganisator** ist an das **Hauptkamera** Objekt angefügt.

- Stellen Sie sicher, dass Sie den **Vorhersage Schlüssel** in die Variable " **vorhersag Schlüssel** " einfügen.

- Sie haben den **Vorhersage Endpunkt** in die " **prätionendpoint** "-Variable eingefügt.

- Sie haben ihren **Trainings Schlüssel** in die Variable " **trainingkey** " der Klasse " *customvisiontrainer* " eingefügt.

- Sie haben Ihre **Projekt-ID** in die **ProjectId** -Variable der *customvisiontrainer* -Klasse eingefügt.

## <a name="chapter-13---build-and-sideload-your-application"></a>Kapitel 13: Erstellen und querladen der Anwendung

So beginnen Sie den Buildprozess:

1.  Wechseln Sie zu **Datei >** Buildeinstellungen.

2.  Teil Strich **Unity\# -C-Projekte**.

3.  Klicken Sie auf **Erstellen**. Unity startet ein **Datei-Explorer** -Fenster, in dem Sie einen Ordner erstellen und auswählen müssen, in dem die App erstellt wird. Erstellen Sie diesen Ordner jetzt, und nennen Sie ihn " **App**". Klicken Sie dann mit ausgewähltem **App** -Ordner auf **Ordner auswählen**.

4.  Unity startet das Projekt in den **App** -Ordner.

5.  Nachdem die Erstellung von Unity abgeschlossen ist (Dies kann einige Zeit in Anspruch nehmen), wird ein **Datei-Explorer** -Fenster am Speicherort des Builds geöffnet (überprüfen Sie die Taskleiste, da Sie möglicherweise nicht immer über Ihrem Fenster angezeigt wird, sondern Sie über das Hinzufügen eines neuen Fensters benachrichtigt).

So stellen Sie auf hololens bereit:

1.  Sie benötigen die IP-Adresse Ihrer hololens (für die Remote Bereitstellung) und, um sicherzustellen, dass sich Ihre hololens im **Entwicklermodus**befinden. Gehen Sie dazu wie folgt vor:

    1.  Öffnen Sie die Einstellungen, während Sie die hololens- **Einstellungen**durch tragen.

    2.  Navigieren Sie zu **Netzwerk &**  > erweiterte**Wi-Fi** > -**Optionen** für das Internet.

    3.  Notieren Sie sich die **IPv4** -Adresse.

    4.  Navigieren Sie als nächstes wieder zu **Einstellungen**, und aktualisieren Sie die **& Sicherheit** > **für Entwickler** .

    5.  Legen Sie **den Entwicklermodus auf**fest.

2.  Navigieren Sie zu Ihrem neuen Unity-Build ( **App** -Ordner), und öffnen Sie die Projektmappendatei mit **Visual Studio**.

3.  Wählen Sie in der Projektmappenkonfiguration **Debuggen**.

4.  Wählen Sieauf der Projektmappenplattform die Option **x86, Remote Computer**aus. Sie werden aufgefordert, die **IP-Adresse** eines Remote Geräts (in diesem Fall die hololens) einzufügen, die Sie notiert haben.

    ![](images/AzureLabs-Lab302b-34.png)

5. Wechseln Sie zum Menü **Erstellen** , und klicken Sie auf **Lösung** bereitstellen, um die Anwendung auf die hololens quer zuladen.

6. Ihre APP sollte nun in der Liste der installierten apps auf Ihren hololens angezeigt werden, die bereit sind, gestartet zu werden.

> [!NOTE]
> Legen Sie für die Bereitstellung auf dem immersiven Headset die Projektmappenplattform auf *lokaler Computer*fest, und legen Sie die **Konfiguration** auf *Debuggen*und *x86* als **Plattform**fest. Stellen Sie dann auf dem lokalen Computer bereit, und wählen Sie dann ProjektMappe bereitstellen aus. 

## <a name="to-use-the-application"></a>So verwenden Sie die Anwendung:

Um die APP-Funktionalität zwischen *Trainings* Modus und *Vorhersage* Modus zu wechseln, müssen Sie die **appmode** -Variable aktualisieren, die sich in der " **Awa()** "-Methode innerhalb der *imagecapture* -Klasse befindet.

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
oder
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

Im *Trainings* Modus:

- Sehen Sie sich **Maus** oder **Tastatur** an, und verwenden Sie die **Tap-Geste**.

- Als nächstes wird Text angezeigt, in dem Sie aufgefordert werden, ein Tag anzugeben.

- Sagen Sie entweder **Maus** oder **Tastatur**.


Im *Vorhersage* Modus:

- Betrachten Sie ein Objekt, und verwenden Sie die **Tap-Geste**.

- Es wird Text angezeigt, der das erkannte Objekt mit der höchsten Wahrscheinlichkeit (normalisiert) bereitstellt.

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a>Kapitel 14: auswerten und verbessern des Custom Vision Modells

Um den Dienst genauer zu gestalten, müssen Sie das Modell, das für die Vorhersage verwendet wird, weiter trainieren. Dies erfolgt über die Verwendung der neuen Anwendung mit den *Trainings* -und *Vorhersage* Modi, bei denen letztere das Portal besuchen muss, was in diesem Kapitel behandelt wird. Bereiten Sie Ihr Portal mehrmals vor, um das Modell kontinuierlich zu verbessern.

1. Wechseln Sie erneut in Ihr Azure Custom Vision-Portal, und wählen Sie die Registerkarte *Vorhersagen* aus, sobald Sie in Ihrem Projekt sind (in der oberen Mitte der Seite):

    ![](images/AzureLabs-Lab302b-35.png)

2. Alle Images, die während der Ausführung Ihrer Anwendung an den Dienst gesendet wurden, werden angezeigt. Wenn Sie mit dem Mauszeiger auf die Bilder zeigen, erhalten Sie die Vorhersagen, die für das Image erstellt wurden:

    ![](images/AzureLabs-Lab302b-36.png)

3. Wählen Sie eines der Images aus, um es zu öffnen. Sobald das Bild geöffnet ist, werden die Vorhersagen für dieses Bild auf der rechten Seite angezeigt. Wenn die Vorhersagen richtig waren und Sie dieses Bild dem Schulungs Modell Ihres dienstanders hinzufügen möchten, klicken Sie auf das Eingabefeld " *Meine Tags* ", und wählen Sie das Tag aus, das Sie zuordnen möchten. Wenn Sie fertig sind, klicken Sie unten rechts auf die Schaltfläche *Speichern und schließen* , und fahren Sie mit dem nächsten Bild fort.

    ![](images/AzureLabs-Lab302b-37.png)

4. Wenn Sie wieder zum Bild Raster zurückkehren, werden Sie feststellen, dass die Bilder, denen Sie Tags hinzugefügt haben (und gespeichert), entfernt werden. Wenn Sie Bilder suchen, für die Sie nicht über das markierte Element verfügen, können Sie Sie löschen, indem Sie auf den Tick dieses Bilds klicken (kann dies für mehrere Bilder tun) und dann in der oberen rechten Ecke der Raster Seite auf *Löschen* klicken. Im folgenden Popup Fenster können Sie auf *Ja, löschen* oder *Nein*klicken, um den Löschvorgang zu bestätigen bzw. abzubrechen. 

    ![](images/AzureLabs-Lab302b-38.png)

5. Wenn Sie den Vorgang fortsetzen möchten, klicken Sie oben rechts auf die grüne Schaltfläche " *Train* ". Ihr Dienstmodell wird mit allen Images trainiert, die Sie jetzt bereitgestellt haben (wodurch es präziser wird). Wenn das Training vollständig ist, klicken Sie erneut auf die Schaltfläche *Standard erstellen* , damit Ihre *Vorhersage-URL* weiterhin die aktuellste Iterationen des Dienes verwendet.

    ![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)

## <a name="your-finished-custom-vision-api-application"></a>Ihre fertiggestellte Custom Vision-API-Anwendung

Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die die Azure-Custom Vision-API nutzt, um reale Objekte zu erkennen, das Dienstmodell zu trainieren und sich über das gesehene Vertrauen zu zeigen.

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a>Bonus Übungen

### <a name="exercise-1"></a>Übung 1

Trainieren Sie Ihre **Custom Vision Service** , um weitere Objekte zu erkennen.

### <a name="exercise-2"></a>Übung 2

Um zu erfahren, was Sie gelernt haben, führen Sie die folgenden Übungen aus:

Spielen Sie einen Sound wieder, wenn ein Objekt erkannt wird.

### <a name="exercise-3"></a>Übung 3

Verwenden Sie die API zum erneuten trainieren Ihres diensmit denselben Images, die von Ihrer APP analysiert werden, um den Dienst genauer zu gestalten (führen Sie sowohl Vorhersagen als auch Schulungen gleichzeitig aus).
