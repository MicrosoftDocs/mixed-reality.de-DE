---
title: MR und Azure 302b - Custom vision
description: Führen Sie diesen Kurs Informationen zum Trainieren von Machine Learning-Modell, und klicken Sie dann verwenden Sie das trainierte Modell zur Erkennung von ähnlicher Objekte innerhalb einer mixed Reality-Anwendung.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorials, api, benutzerdefiniertes maschinelles sehen, Hololens, immersive vr
ms.openlocfilehash: e6e9782a8d559af660dc4765556f1e926c5360b1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594225"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

<br>

# <a name="mr-and-azure-302b-custom-vision"></a>MR und Azure 302b: Benutzerdefiniertes maschinelles sehen

In diesem Kurs erfahren Sie erkennen der benutzerdefinierten visuellen Inhalt in einem bereitgestellten Image mithilfe von Azure Custom Vision-Funktionen in einer mixed Reality-Anwendung.

Dieser Dienst ermöglicht Ihnen zum Trainieren von Machine Learning-Modellen mithilfe von Objekt-Images. Dann werden das trainierte Modell können Sie erkennen ähnliche Objekte, gemäß Bereitstellung durch die Kamera-Aufnahme von Microsoft HoloLens oder eine Kamera, die mit Ihrem PC für immersive Headsets von (VR) verbunden sind.

![Kurs Ergebnis](images/AzureLabs-Lab302b-00.png)

Azure Custom Vision ist ein Microsoft Cognitive der Dienst Entwicklern ermöglicht, benutzerdefinierte bildklassifizierungen zu erstellen. Diese Klassifizierungen können dann mit neuen Images zur Erkennung von verwendet werden, oder klassifizieren, Objekte innerhalb dieses Image. Der Dienst bietet eine einfache, benutzerfreundliche, online-Portal, um den Prozess zu optimieren. Weitere Informationen finden Sie auf die [Azure Custom Vision Service Seite](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).

Nach Abschluss dieses Kurses verfügen Sie über ein mixed Reality-Anwendung die in zwei Modi arbeiten:

-   **Analysemodus**: Einrichten der Custom Vision Service manuell durch Hochladen von Images, Tags erstellen und Trainieren den Dienst zur Erkennung von verschiedenen Objekten (in diesem Fall Maus und Tastatur). Sie erstellen dann eine HoloLens-app, die Erfassen von Abbildern, die Verwendung der Kamera, und versuchen, diese Objekte in der realen Welt erkennen.

-   **Trainieren Modus**: Implementieren Sie Code, mit denen ein "Training-Modus" in Ihrer app. Der Testmodus können Sie zum Erfassen von Abbildern verwenden die HoloLens Kamera, die erfassten Abbilder in den Dienst hochgeladen und Trainieren des Modells für benutzerdefiniertes maschinelles sehen.

In diesem Kurs erfahren Sie, wie die Ergebnisse in eine Unity-basierte Anwendung aus der Custom Vision Service zu erhalten. Sie werden sich entscheiden, ob Sie diese Konzepte, die Sie erstellen eine benutzerdefinierte Anwendung zuweisen.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td> MR und Azure 302b: Benutzerdefiniertes maschinelles sehen</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Während dieser Kurs in erster Linie für HoloLens ausgerichtet ist, können Sie auch anwenden, was Sie in diesem Kurs, Faszinierende Windows Mixed Reality (VR)-Headsets lernen. Da immersive Headsets von (VR) nicht zugegriffen werden kann, Kameras verfügen, benötigen Sie eine externe Kamera, die mit dem PC verbunden. Wie Sie den Kurs halten, sehen Anmerkungen zu dieser Version Sie auf alle Änderungen, die Sie möglicherweise zur Unterstützung von immersive Headsets von (VR) einsetzen müssen.

## <a name="prerequisites"></a>Vorraussetzungen

> [!NOTE]
> In diesem Tutorial wurde für Entwickler mit Erfahrung mit Unity entwickelt und C#. Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Juli 2018) überprüft wurde. Sie können zur Verwendung der neuesten Software, wie in der [Installieren der Tools](install-the-tools.md) Artikel, obwohl es nicht davon ausgegangen werden soll, dass die Informationen in diesem Kurs perfekt entspricht was finden Sie in der neueren Software als aufgeführt ist unten.

Es wird empfohlen, die folgende Hardware und Software für diesen Kurs:

- Eine Entwicklungs-PC [kompatibel mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für immersive (VR) Kopfhörer-Entwicklung
- [Windows 10 Fall Creators Update (oder höher) mit der Entwicklermodus aktiviert ist](install-the-tools.md#installation-checklist)
- [Das neueste Windows 10-SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Ein [immersive Windows Mixed Reality (VR)-Kopfhörer](immersive-headset-hardware-details.md) oder [Microsoft HoloLens](hololens-hardware-details.md) mit Entwicklermodus aktiviert ist
- Eine Kamera, die Verbindung mit Ihrem PC (für immersive Kopfhörer Entwicklung)
- Zugriff auf das Internet für die Einrichtung von Azure und Datenabruf für benutzerdefiniertes maschinelles sehen-API
- Eine Reihe von mindestens fünf (5) Bildern (zehn (10) empfohlen) für jedes Objekt, das Sie mit der Custom Vision Service erkennen möchten. Wenn Sie möchten, können Sie [die bereits in diesem Kurs (Computermaus und Tastatur) bereitgestellten Images ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).

## <a name="before-you-start"></a>Bevor Sie beginnen

1.  Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).
2.  Richten Sie ein und Testen Sie Ihre HoloLens. Bei Bedarf Unterstützung zum Einrichten Ihrer HoloLens, [stellen Sie sicher, dass die HoloLens-Setup-Artikel finden Sie unter](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Es ist eine gute Idee, die Kalibrierung und Optimierung der Sensor ausführen, wenn Sie beginnen, eine neue HoloLens-app (manchmal ist es hilfreich, diese Aufgaben für jeden Benutzer) entwickeln. 

Um Hilfe zur Kalibrierung, befolgen Sie diese [Link zum Artikel HoloLens Kalibrierung](calibration.md#hololens).

Um Hilfe zur Optimierung der Sensor, befolgen Sie diese [Link zum Optimieren von HoloLens Sensor](sensor-tuning.md).

## <a name="chapter-1---the-custom-vision-service-portal"></a>Kapitel 1: das Custom Vision Service-Portal

Verwenden der *Custom Vision Service* in Azure müssen Sie so konfigurieren Sie eine Instanz des Diensts, der für Ihre Anwendung verfügbar gemacht werden.

1.  Zuerst [navigieren Sie zu der *Custom Vision Service* Hauptseite](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).

2.  Klicken Sie auf die **Einstieg** Schaltfläche.

    ![](images/AzureLabs-Lab302b-01.png)

3.  Melden Sie sich bei der *Custom Vision Service* Portal.

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen. Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.

4.  Nachdem Sie sich zum ersten Mal angemeldet sind, Sie werden aufgefordert, mit der *Vertragsbedingungen* Bereich. Klicken Sie auf das Kontrollkästchen, um den Bedingungen zustimmen. Klicken Sie dann auf **ich stimme zu**.

    ![](images/AzureLabs-Lab302b-03.png)

5.  Die Begriffe zugestimmt haben, Sie werden navigiert werden, die *Projekte* -Abschnitt des Portals. Klicken Sie auf **neues Projekt**.

    ![](images/AzureLabs-Lab302b-04.png)

6.  Eine Registerkarte wird auf der rechten Seite angezeigt, wodurch Sie angeben, einige Felder für das Projekt angefordert wird.

    1.  Fügen Sie eine *Namen* für Ihr Projekt.

    2.  Fügen Sie eine *Beschreibung* für Ihr Projekt (*optional*).

    3.  Wählen Sie eine *Ressourcengruppe* oder ein neues erstellen. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle zu bewahren, an die Azure-Dienste unter einer allgemeinen Ressourcengruppe mit einem einzelnen Projekt (z. B. z. B. diese Kurse) verknüpft ist).

    4. Legen Sie die *Projekttypen* zu **Klassifizierung**
    
    5. Legen Sie die *Domänen* als **allgemeine**.

        ![](images/AzureLabs-Lab302b-05.png)

        > Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, bitte [finden Sie im Artikel der Resource-Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

7.  Sobald Sie fertig sind, klicken Sie auf **projekterstellung**, Sie zu dem Custom Vision Service, Projekt – Seite umgeleitet werden.

## <a name="chapter-2---training-your-custom-vision-project"></a>Kapitel 2 – trainieren Ihr Projekt Custom Vision

Einmal ist im Custom Vision-Portal Ihr Hauptziel zum Trainieren des Projekts für bestimmte Objekte in Bildern zu erkennen. Sie benötigen mindestens fünf (5) Bilder, obwohl zehn (10) wird empfohlen, für jedes Objekt, das Ihre Anwendung erkennen soll. [Sie können die in diesem Kurs (Computermaus und Tastatur) bereitgestellten Images](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip). 

Trainieren Sie Ihr Projekt Custom Vision Service:

1.  Klicken Sie auf die **+** neben **Tags.**

    ![](images/AzureLabs-Lab302b-06.png)

2.  Hinzufügen der **Namen** des Objekts, die Sie erkennen möchten. Klicken Sie auf **speichern**.

    ![](images/AzureLabs-Lab302b-07.png)

3.  Sie sehen Ihre **Tag** hinzugefügt wurde (möglicherweise müssen Sie Ihrer Seite angezeigt werden neu laden). Aktivieren Sie das Kontrollkästchen neben Ihr neues Tag, wenn er noch nicht aktiviert ist.

    ![](images/AzureLabs-Lab302b-08.png)

4.  Klicken Sie auf **Hinzufügen von Abbildern** in der Mitte der Seite.

    ![](images/AzureLabs-Lab302b-09.png)

5.  Klicken Sie auf **lokale Dateien durchsuchen**, und suchen, und wählen Sie dann, die Bilder, Sie möchten, und die minimale hochladen, fünf (5). Denken Sie daran, dass alle diese Images auf das Objekt enthalten sollte, die Sie trainieren werden.

    > [!NOTE]
    >  Sie können mehrere Images zu einem Zeitpunkt, zum Hochladen auswählen.

6.  Nachdem Sie die Bilder auf der Registerkarte sehen können, wählen Sie das entsprechende Tag in die **Meine Tags** Feld.

    ![](images/AzureLabs-Lab302b-10.png)

7.  Klicken Sie auf **Hochladen von Dateien**. Hochladen beginnt die Dateien. Nachdem Sie die Bestätigung für das Hochladen haben, klicken Sie auf **Fertig**.

    ![](images/AzureLabs-Lab302b-11.png)

8.  Wiederholen Sie den gleichen Prozess zum Erstellen eines neuen **Tag** mit dem Namen **Tastatur** und die entsprechenden Fotos dafür hochladen. Stellen Sie sicher, dass **deaktivieren** *Maus* nach dem Erstellen der neuen Tags, zum Anzeigen der *Hinzufügen von Bildern* Fenster.

9.  Sobald Sie beide Tags eingerichtet haben, klicken Sie auf **Train**, und die erste Iteration von Schulungen mit der Erstellung.

    ![](images/AzureLabs-Lab302b-12.png)

10. Nachdem es erstellt wurde, werden Sie zwei Schaltflächen angezeigt werden **Standard** und **Vorhersage URL**. Klicken Sie auf **Standard** zuerst, klicken Sie dann auf auf **Vorhersage URL**.

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > Die Endpunkt-URL, die von diesem bereitgestellt wird, je nachdem, was je nastaven *Iteration* als Standard gekennzeichnet wurde. Also, wenn Sie später einen neuen vornehmen *Iteration* und als Standard zu aktualisieren, müssen Sie nicht zum Ändern Ihres Codes.

11. Sobald Sie auf geklickt haben *Vorhersage URL*öffnen *Editor*, und kopieren und Einfügen der **URL** und **Vorhersage-Schlüssel**, damit können Sie bei Bedarf später im Code abrufen.

    ![](images/AzureLabs-Lab302b-14.png)

12. Klicken Sie auf die **Zahnrad** am oberen rechten Rand des Bildschirms.

    ![](images/AzureLabs-Lab302b-15.png)

13. Kopieren der **Training Schlüssel** , und fügen Sie ihn in eine *Editor*, für die spätere Verwendung.

    ![](images/AzureLabs-Lab302b-16.png)

14. Kopieren Sie außerdem Ihre **Projekt-Id**, und außerdem fügen Sie ihn in Ihre *Editor* -Datei für die spätere Verwendung.

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Kapitel 3: Einrichten von Unity-Projekts

Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit mixed Reality und daher ist eine gute Vorlage für andere Projekte.

1.  Open *Unity* , und klicken Sie auf **neu**.

    ![](images/AzureLabs-Lab302b-17.png)

2.  Sie müssen jetzt einen Unity-Projektnamen angeben. Fügen Sie **AzureCustomVision.** Stellen Sie sicher, dass die Projektvorlage nastaven NA hodnotu **3D**. Legen Sie die **Speicherort** auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser). Klicken Sie auf **projekterstellung**.

    ![](images/AzureLabs-Lab302b-18.png)

3.  Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**. Wechseln Sie zu **bearbeiten* > *Voreinstellungen** und navigieren Sie dann im neuen Fenster zu **externe Tools**. Änderung **externen Skript-Editors** zu **Visual Studio 2017**. Schließen der **Voreinstellungen** Fenster.

    ![](images/AzureLabs-Lab302b-19.png)

4.  Öffnen Sie als Nächstes **Datei > Buildeinstellungen** , und wählen Sie **universelle Windows-Plattform**, klicken Sie dann auf die **Plattform wechseln** Schaltfläche, um Ihre Auswahl anzuwenden.

    ![](images/AzureLabs-Lab302b-20.png)

5.  In der **Datei > Buildeinstellungen** und stellen Sie sicher, dass:

    1.  **Geräte** nastaven NA hodnotu **Hololens**

        > Legen Sie für die immersive Headsets, **Zielgerät** zu *einem beliebigen Gerät*.
        
    2.  **Buildtyp** nastaven NA hodnotu **D3D**
    3.  **SDK** nastaven NA hodnotu **zuletzt installierte**
    4.  **Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**
    5.  **Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**
    6.  Die Szene speichern und mit dem Build hinzugefügt werden. 

        1. Hierzu **öffnen Szenen hinzufügen**. Ein Speichern Fenster wird angezeigt.

            ![](images/AzureLabs-Lab302b-21.png)

        2. Erstellen einen neuen Ordner für, und alle zukünftigen, Szene, klicken Sie dann auf die **neuer Ordner** Schaltfläche zum Erstellen eines neuen Ordners, nennen Sie sie **Szenen**.

            ![](images/AzureLabs-Lab302b-22.png)

        3. Öffnen Sie den neu erstellten **Szenen** Ordner, und klicken Sie dann in der *Dateiname:* Textfeld **CustomVisionScene**, klicken Sie dann auf **speichern**.

            ![](images/AzureLabs-Lab302b-23.png)

            > Beachten Sie, speichern Sie Ihre Unity-Szenen in den *Assets* Ordner, wie sie mit der Unity-Projekt verbunden sein müssen. Erstellen den Ordner im Hintergrund (und andere ähnliche Ordner), wird eine typische Möglichkeit Strukturieren eines Unity-Projekts ist.
            
    7.  Die Einstellungen im verbleibenden *Buildeinstellungen*, sollte jetzt als Standard bleiben.

        ![](images/AzureLabs-Lab302b-24.png)

6.  In der *Buildeinstellungen* Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dadurch wird den entsprechenden Bereich geöffnet, im Bereich, in dem die *Inspektor* befindet.

7. In diesem Bereich sind müssen einige Einstellungen überprüft werden:

    1.  In der **Weitere Einstellungen** Registerkarte:

        1.  **Scripting Runtime Version** muss **experimentell (.NET 4.6 Äquivalent)**, löst der Editor neu starten müssen.

        2. **Back-End-Scripting** muss **.NET**

        3. **API-Kompatibilitätsebene** muss **.NET 4.6**

        ![](images/AzureLabs-Lab302b-25.png)

    2.  In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:

        1. **InternetClient**

        2.  **Webcam**

        3. **Microphone**

        ![](images/AzureLabs-Lab302b-26.png)

    3.  Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality-SDK**  hinzugefügt wird.

    ![](images/AzureLabs-Lab302b-27.png)

8.  Im *Buildeinstellungen* *Unity C\# Projekte* nicht mehr abgeblendet ist, aktivieren Sie das Kontrollkästchen neben dieser.

9.  Schließen Sie das Fenster "erstellen".

10.  Speichern Sie Ihre Szene und das Projekt (**Datei > SZENE speichern / FILE > Projekt speichern**).


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a>Kapitel 4: importieren die Newtonsoft-DLL in Unity

> [!IMPORTANT]
> Wenn Sie, überspringen Sie möchten die *Unity einrichten* -Komponente dieser Kurs, und direkt in Code fortsetzen, können Sie zum Herunterladen [Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), importieren Sie es in Ihr Projekt als eine [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), und klicken Sie dann eine Fortsetzung [Kapitel 6](#chapter-6---create-the-customvisionanalyser-class).

Dieser Kurs erfordert die Verwendung der **Newtonsoft** -Bibliothek, die Sie als eine DLL-Datei mit Ihren Ressourcen hinzufügen können. Das Paket mit [dieser Bibliothek heruntergeladen werden kann, über diesen Link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).
Um die Newtonsoft-Bibliothek in Ihr Projekt zu importieren, verwenden Sie das Unity-Paket, das in diesem Kurs stammt.

1.  Hinzufügen der *.unitypackage* in Unity mithilfe der **Assets* > *Import* *Paket*  >  *Benutzerdefinierte* *Paket** Option des Menüs.

2.  In der **Unity-Paket importieren** , ruft Sie Vergewissern Sie sich, alles, was unter (und einschließlich) **-Plug-Ins** ausgewählt ist.

    ![](images/AzureLabs-Lab302b-28.png)

3.  Klicken Sie auf die **Import** , um die Elemente zu Ihrem Projekt hinzuzufügen.

4.  Wechseln Sie zu der **Newtonsoft** Unterordner **-Plug-Ins** im Projekt anzeigen, und wählen die *"newtonsoft.JSON"-Plug-Ins*.

    ![](images/AzureLabs-Lab302b-29.png)

5.  Mit der *"newtonsoft.JSON"-Plug-Ins* ausgewählt haben, stellen sicher, dass **Any Platform** ist **deaktiviert**, klicken Sie dann sicher, dass **WSAPlayer** ist auch **deaktiviert**, klicken Sie dann auf **übernehmen**. Dies ist, um sich zu vergewissern, dass die Dateien richtig konfiguriert sind.

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > Markieren diese-Plug-Ins konfiguriert sie nur im Unity-Editor verwendet werden. Es gibt ein anderen Satz von ihnen im Ordner "WSA" das verwendet werden soll, nachdem das Projekt aus Unity exportiert werden.

6.  Als Nächstes müssen Sie zum Öffnen der **WSA** Ordner, der innerhalb der **Newtonsoft** Ordner. Daraufhin wird eine Kopie der gleichen Datei, die Sie gerade konfiguriert haben. Wählen Sie die Datei, und klicken Sie dann im Inspector sicher, dass
    -   **Jede Plattform** ist **deaktiviert** 
    -   **nur** **WSAPlayer** ist **aktiviert**
    -   **Nicht verarbeiten** ist **aktiviert**

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a>Kapitel 5 – kamerasetup

1.  Wählen Sie im Bereich mit den-Hierarchie der *Main Camera*.

2.  Wenn ausgewählt, Sie werden auf alle Komponenten finden Sie unter den *Main Camera* in die *Inspektor Bereich*.

    1.  Die *Kamera* Objekt muss den Namen **Main Camera** (Beachten Sie die Rechtschreibung!)

    2.  Die Main Camera **Tag** muss festgelegt werden, um **MainCamera** (Beachten Sie die Rechtschreibung!)

    3.  Stellen Sie sicher, dass die **transformieren Position** nastaven NA hodnotu **0, 0, 0**

    4.  Legen Sie **löschen Flags** zu **Volltonfarbe** (ignorieren Sie dies für immersive Kopfhörer).

    5.  Legen Sie die **Hintergrund** Farbe der Kamera Komponente **Schwarz, Alpha 0 (Hex-Code: #00000000)** (ignorieren Sie dies für immersive Kopfhörer).

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a>Kapitel 6: Erstellen Sie die CustomVisionAnalyser-Klasse.

An diesem Punkt können Sie Code schreiben.

Beginnen Sie mit der *CustomVisionAnalyser* Klasse.

> [!NOTE]
> Die Aufrufe an die **Custom Vision Service** vorgenommen werden, in dem gezeigten Code unten erfolgen mithilfe der **Custom Vision-REST-API**. Durch die Verwendung dieser, erfahren Sie, wie zu implementieren und Verwenden dieser API (nützlich, um zu verstehen, wie etwa selbst implementiert). Denken Sie, dass Microsoft bietet eine **Custom Vision Service SDK** , auch für Aufrufe an den Dienst verwendet werden kann. Weitere Informationen finden Sie auf die [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) Artikel.

Diese Klasse ist zuständig für:

-   Laden das neueste Image als ein Array von Bytes erfasst.

-   Das Bytearray an Azure senden *Custom Vision Service* Instanz für die Analyse.

-   Empfangen der Antwort als JSON-Zeichenfolge.

-   Die Antwort zu deserialisieren, und übergeben die resultierenden *Vorhersage* auf die *SceneOrganiser* -Klasse, die kümmern wird wie die Antwort angezeigt werden soll.

Diese Klasse zu erstellen:

1.  Mit der rechten Maustaste den *Ordner "Assets"* befindet sich in der *Projektfenster*, klicken Sie dann auf **erstellen > Ordner**. Rufen Sie den Ordner **Skripts**.

    ![](images/AzureLabs-Lab302b-33.png)

2.  Doppelklicken Sie auf den Ordner, der gerade erstellt haben, um ihn zu öffnen.

3.  Mit der rechten Maustaste in den Ordner, und klicken Sie dann **erstellen** > **C\# Skript**. Nennen Sie das Skript *CustomVisionAnalyser*.

4.  Doppelklicken Sie auf die neue *CustomVisionAnalyser* Skript öffnen Sie ihn mit **Visual Studio**.

5.  Aktualisieren Sie die Namespaces am Anfang der Datei mit folgendem übereinstimmt:

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  In der *CustomVisionAnalyser* -Klasse verwenden, fügen Sie die folgenden Variablen:

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
    > Stellen Sie sicher, dass Sie Einfügen Ihrer **Vorhersage Schlüssel** in die **PredictionKey** Variable und Ihr **Endpunkt der Vorhersage** in die **PredictionEndpoint** Variable. Sie kopiert haben, diese *Editor* weiter oben in diesem Kurs.

7.  Code für **Awake()** muss nun hinzugefügt werden, um die Instanz-Variable zu initialisieren:

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

8.  Löschen Sie die Methoden **Start()** und **Update()**.

9.  Fügen Sie als Nächstes die Coroutine (mit der statischen **GetImageAsByteArray()** Methode darunter), die erhalten die Ergebnisse der Analyse des Bilds von erfasst die *digitale Bilder* Klasse.

    > [!NOTE]
    > In der **AnalyseImageCapture** Coroutine, erfolgt ein Aufruf von der *SceneOrganiser* -Klasse, die Sie noch erstellen werden. Aus diesem Grund **lassen Sie diese Zeilen jetzt kommentiert**.

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

10.  Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio** vor der Rückgabe an **Unity**.

## <a name="chapter-7---create-the-customvisionobjects-class"></a>Kapitel 7: Erstellen Sie die CustomVisionObjects-Klasse

Die Klasse, die Sie erstellen nun ist die *CustomVisionObjects* Klasse.

Dieses Skript enthält eine Reihe von Objekten, die von anderen Klassen verwendet werden, zum Serialisieren und Deserialisieren der Aufrufe an die *Custom Vision Service*.

> [!WARNING]
> Es ist wichtig, dass Sie den Endpunkt, die Ihnen notieren, als von der Custom Vision Service bietet die folgenden JSON-Code Struktur eingerichtet wurde, arbeiten mit [ *Custom Vision Vorhersage v2. 0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290). Wenn Sie eine andere Version haben, müssen Sie möglicherweise zum Aktualisieren der folgenden Struktur.

Diese Klasse zu erstellen:

1.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie dann auf **erstellen** > **C\# Skript**. Rufen Sie das Skript *CustomVisionObjects*.

2.  Doppelklicken Sie auf die neue **CustomVisionObjects** Skript öffnen Sie ihn mit **Visual Studio**.

3.  Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Löschen der **Start()** und **Update()** Methoden innerhalb der *CustomVisionObjects* Klasse; diese Klasse sollte jetzt leer sein.

5.  Fügen Sie die folgenden Klassen **außerhalb** der *CustomVisionObjects* Klasse. Diese Objekte werden verwendet, durch die *Newtonsoft* Bibliothek zum Serialisieren und Deserialisieren die Antwortdaten werden:

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

## <a name="chapter-8---create-the-voicerecognizer-class"></a>Kapitel 8 – erstellen Sie die VoiceRecognizer-Klasse

Diese Klasse erkennt die Spracheingabe des Benutzers.

Diese Klasse zu erstellen:

1.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie dann auf **erstellen** > **C\# Skript**. Rufen Sie das Skript *VoiceRecognizer*.

2.  Doppelklicken Sie auf die neue **VoiceRecognizer** Skript öffnen Sie ihn mit **Visual Studio**.

3.  Fügen Sie die folgenden Namespaces, die oben genannten der *VoiceRecognizer* Klasse:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  Klicken Sie dann fügen Sie die folgenden Variablen in der *VoiceRecognizer* Klasse, über die *Start()* Methode:

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

5.  Hinzufügen der **Awake()** und **Start()** Methoden, von denen letzterer, nach dem Benutzer festgelegt wird *Schlüsselwörter* erkannt werden, wenn Sie ein Tag zu einem Bild zu verknüpfen:

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

6.  Löschen der **Update()** Methode.

7.  Fügen Sie den folgenden Ereignishandler, der aufgerufen wird, wenn Sie Spracheingabe erkannt wird:

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

8.  Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio** vor der Rückgabe an **Unity**.

> [!NOTE]
> Aber keine Sorge, über Code, die einen Fehler, angezeigt werden kann, wie Sie bald weitere Klassen bereitstellen möchten, die diese behoben werden.

## <a name="chapter-9---create-the-customvisiontrainer-class"></a>Kapitel 9 – erstellen Sie die CustomVisionTrainer-Klasse

Diese Klasse wird eine Reihe von Web-Aufrufe zum Trainieren Verketten der *Custom Vision Service*. Jeder Aufruf werden direkt über den Code ausführlich erläutert.

Diese Klasse zu erstellen:

1.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie dann auf **erstellen** > **C\# Skript**. Rufen Sie das Skript *CustomVisionTrainer*.

2.  Doppelklicken Sie auf die neue *CustomVisionTrainer* Skript öffnen Sie ihn mit **Visual Studio**.

3.  Fügen Sie die folgenden Namespaces, die oben genannten der *CustomVisionTrainer* Klasse:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Klicken Sie dann fügen Sie die folgenden Variablen in der *CustomVisionTrainer* Klasse, über die **Start()** Methode. 

    > [!NOTE]
    > Die hier verwendete Training-URL finden Sie in der *Custom Vision Training 1.2* Dokumentation und verfügt über eine Struktur von: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/  
    > Weitere Informationen finden Sie auf die [ *Custom Vision Training v1. 2-Referenz zur API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).

    > [!WARNING]
    > Es ist wichtig, dass Sie den Endpunkt notieren, die der Custom Vision Service Sie für den Testmodus, wie die JSON-Struktur verwendet bereitstellt (innerhalb der **CustomVisionObjects** Klasse) eingerichtet wurde, arbeiten mit [  *Custom Vision Training v1. 2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f). Wenn Sie eine andere Version haben, müssen Sie möglicherweise zum Aktualisieren der *Objekte* Struktur.

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
    > Stellen Sie sicher, dass Sie beim Hinzufügen Ihrer **Dienstschlüssel** (Training Schlüsselwert) und **Projekt-Id** Wert, der Sie notiert vorherigen; Dies sind die Werte Sie [gesammelt, die über das Portal weiter oben in der Kurs ( Kapitel 2, Schritt 10 oder höher)](#chapter-2---training-your-custom-vision-oroject).

5.  Fügen Sie die folgenden **Start()** und **Awake()** Methoden. Diese Methoden werden während der Initialisierung aufgerufen und den Aufruf zum Einrichten der Benutzeroberflächenautomatisierungs nicht enthalten:

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

6.  Löschen der **Update()** Methode. Diese Klasse wird dies nicht erforderlich.

7.  Hinzufügen der **RequestTagSelection()** Methode. Diese Methode ist das erste, die aufgerufen werden, wenn ein Image erfasst und im Gerät gespeichert wurden und ist nun bereit für die Übermittlung an die *Custom Vision Service*, um es zu trainieren. Diese Methode zeigt im Training-Benutzeroberfläche einen Satz von Schlüsselwörtern, mit denen der Benutzer das Image zu kennzeichnen, das aufgezeichnet wurden. Sie erhalten ebenfalls eine Warnung der *VoiceRecognizer* Klasse, die überwacht, die dem Benutzer für die Spracheingabe.

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  Hinzufügen der **VerifyTag()** Methode. Diese Methode erhält die Spracheingabe erkannt werden, indem die **VoiceRecognizer** Klasse und seine Gültigkeit zu überprüfen und damit beginnen, den Training.

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

9.  Hinzufügen der **SubmitImageForTraining()** Methode. Diese Methode wird der Trainingsprozess Custom Vision Service gestartet. Der erste Schritt ist zum Abrufen der **Transponder-Id** aus dem Dienst, das das überprüfte Spracheingabe des Benutzers zugeordnet ist. Die **Transponder-Id** wird dann zusammen mit dem Bild hochgeladen werden.

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

10. Hinzufügen der **TrainCustomVisionProject()** Methode. Nachdem das Image übermittelt und markiert wurde, wird diese Methode aufgerufen werden. Erstellen sie eine neue Iteration, die mit all den vorherigen Abbildern, die an den Dienst und das Bild übermittelt trainiert werden gerade hochgeladen haben. Nachdem das Training abgeschlossen wurde, ruft diese Methode eine Methode, um die neu erstellte festzulegen **Iteration** als **Standard**, sodass der Endpunkt, die Sie für die Analyse verwenden der aktuellen Iteration trainierten sind.

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

11. Hinzufügen der **SetDefaultIteration()** Methode. Dieser Methode wird festgelegt, die zuvor erstellte und trainierte Iteration als *Standard*. Nach Abschluss müssen dieser Methode Sie die vorhergehenden Iteration im Dienst vorhandene zu löschen. Zum Zeitpunkt des Schreibens von diesem Kurs ist es maximal eine maximale Anzahl zehn (10) von Iterationen gleichzeitig im Dienst vorhanden sein können.

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

12. Hinzufügen der **DeletePreviousIteration()** Methode. Diese Methode wird suchen und Löschen von der vorhergehenden Iteration für nicht standardmäßige:

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

13. Die letzte Methode in dieser Klasse hinzufügen ist die **GetImageAsByteArray()** Methode, die auf die Webserviceaufrufe verwendet, um das Bild erfasst in ein Bytearray zu konvertieren.

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

14. Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio** vor der Rückgabe an **Unity**.

## <a name="chapter-10---create-the-sceneorganiser-class"></a>Kapitel 10 – erstellen Sie die SceneOrganiser-Klasse

Diese Klasse führt Folgendes aus:

-   Erstellen Sie eine **Cursor** bis zur Kamera Main anzufügendes Objekt.

-   Erstellen Sie eine **Bezeichnung** -Objekt, das angezeigt wird, wenn der Dienst die reale Objekte erkennt.

-   Richten Sie die Main Camera aus, indem Sie die entsprechenden Komponenten anfügen, zu.

-   Im **Analysemodus**, erzeugen die Bezeichnungen zur Laufzeit in die entsprechenden Raum relativ zur Position der Kamera, Main und Anzeigen der Daten, die von der Custom Vision Service erhalten.

-   Im **Testmodus**, erzeugen Sie die Benutzeroberfläche, die die verschiedenen Phasen des trainingsprozesses angezeigt wird.

Diese Klasse zu erstellen:

1.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie dann auf **erstellen** > **C\# Skript**. Nennen Sie das Skript *SceneOrganiser*.

2.  Doppelklicken Sie auf die neue *SceneOrganiser* Skript öffnen Sie ihn mit **Visual Studio**.

3.  Sie benötigen nur einen Namespace, entfernen Sie die anderen oben die *SceneOrganiser* Klasse:

    ```csharp
    using UnityEngine;
    ```

4.  Klicken Sie dann fügen Sie die folgenden Variablen in der *SceneOrganiser* Klasse, über die **Start()** Methode:

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

5.  Löschen der **Start()** und **Update()** Methoden.

6.  Fügen Sie direkt unterhalb der Variablen, die **Awake()** -Methode, die Initialisieren der Klasse und der Szene eingerichtet wird.

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

7.  Jetzt hinzufügen der **CreateCameraCursor()** Methode, die erstellt und platziert den Cursor Main Camera und **CreateLabel()** -Methode, die erstellt die **Analysis Bezeichnung** Objekt .

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

8. Hinzufügen der **SetCameraStatus()** -Methode, die Nachrichten für die Bereitstellung des Status der Kamera Mesh Text behandelt.

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

9. Hinzufügen der **PlaceAnalysisLabel()** und **SetTagsToLastLabel()** -Methoden, die erzeugt werden, und zeigen die Daten aus der Custom Vision Service, in der Szene.

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

10. Abschließend fügen die **CreateTrainingUI()** -Methode, die erzeugt wird die Benutzeroberfläche, die mehrere Phasen des trainingsprozesses angezeigt, wenn die Anwendung im Training-Modus befindet. Diese Methode wird auch ein Showcase werden, um die Kamera-Status-Objekt zu erstellen.

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

11. Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio** vor der Rückgabe an **Unity**.

> [!IMPORTANT]
> Bevor Sie fortfahren, öffnen Sie die **CustomVisionAnalyser** -Klasse, und innerhalb der **AnalyseLastImageCaptured()** -Methode, *heben Sie die auskommentierung* die folgenden Zeilen:
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a>Kapitel 11: Erstellen Sie die digitale Bilder-Klasse

Die nächste Klasse, die Sie erstellen wollen ist die *digitale Bilder* Klasse.

Diese Klasse ist zuständig für:

-   Erfassen eines Abbilds verwenden der Kamera HoloLens und speichern ihn in das *App* Ordner.

-   Behandeln von Tap-Gesten des Benutzers.

-   Verwalten der *Enum* -Wert, der bestimmt, ob die Anwendung, im ausgeführt wird *Analysis* Modus oder *Training* Modus.

Diese Klasse zu erstellen:

1.  Wechseln Sie zu der **Skripts** Ordner, die Sie zuvor erstellt haben.

2.  Mit der rechten Maustaste in den Ordner, und klicken Sie dann **erstellen > C\# Skript**. Nennen Sie das Skript *digitale Bilder*.

3.  Doppelklicken Sie auf die neue **digitale Bilder** Skript öffnen Sie ihn mit **Visual Studio**.

4.  Ersetzen Sie die Namespaces am Anfang der Datei durch Folgendes:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  Klicken Sie dann fügen Sie die folgenden Variablen in der *digitale Bilder* Klasse, über die **Start()** Methode:

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

6.  Code für **Awake()** und **Start()** Methoden jetzt hinzugefügt werden muss:

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

7.  Implementieren Sie einen Handler, der aufgerufen wird, wenn eine Tap-Bewegung erfolgt.

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
    > In *Analysis* -Modus die **TapHandler** Methode fungiert als Option zum Starten oder Beenden der Schleife Capture Photo.
    >
    > In *Training* Modus, es wird ein Image von der Kamera.
    >
    > Wenn der Cursor grün ist, bedeutet dies, dass die Kamera verfügbar ist, wird das Bild ist.
    >
    > Wenn der Cursor Rot ist, bedeutet dies, dass die Kamera ausgelastet ist.

8.  Fügen Sie die Methode, die die Anwendung verwendet wird, starten den Prozess der abbilderfassung aus, und speichern Sie das Abbild hinzu.

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

9.  Fügen Sie die Handler, die aufgerufen werden, wenn das Foto aufgezeichnet wurde und wann es analysiert werden kann. Das Ergebnis wird dann zum Übergeben der *CustomVisionAnalyser* oder *CustomVisionTrainer* je nach verwendetem Modus der Code auf festgelegt ist.

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

10. Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio** vor der Rückgabe an **Unity**.

11. Nun, dass alle Skripts abgeschlossen haben, wechseln Sie zurück im Unity-Editor, und ziehen dann die **SceneOrganiser** -Klasse aus der **Skripts** Ordner, um die **Main Camera** -Objekt in der *Hierarchie Bereich*.

## <a name="chapter-12---before-building"></a>Kapitel 12 – vor dem Erstellen

Zur Durchführung eine gründliche Tests der Anwendung werden Sie querladen möchten sie auf Ihre HoloLens benötigen.

Vor dem Ausführen, stellen Sie sicher, dass:

- Alle Einstellungen, die bereits erwähnt, der [Kapitel 2](#chapter-2---training-your-custom-vision-project) ordnungsgemäß festgelegt sind.

- Alle Felder in der **Main Camera**, im Bereich "Inspector" ordnungsgemäß zugewiesen sind.

- Das Skript **SceneOrganiser** angefügt ist die **Main Camera** Objekt.

- Stellen Sie sicher, Sie fügen Ihre **Vorhersage Schlüssel** in die **PredictionKey** Variable.

- Sie eingefügt haben Ihre **Endpunkt der Vorhersage** in die **PredictionEndpoint** Variable.

- Sie eingefügt haben Ihre **Training Schlüssel** in die **TrainingKey** Variablen, der die *CustomVisionTrainer* Klasse.

- Sie eingefügt haben Ihre **Projekt-ID** in die **ProjectId** Variablen, der die *CustomVisionTrainer* Klasse.

## <a name="chapter-13---build-and-sideload-your-application"></a>Kapitel 13 – Build herunter, und Laden Ihrer Anwendung

Um zu beginnen die *erstellen* Prozess:

1.  Wechseln Sie zu **Datei > Buildeinstellungen**.

2.  Teilstriche **Unity C\# Projekte**.

3.  Klicken Sie auf **Erstellen**. Unity startet eine **Datei-Explorer** Fenster, in denen man erstellen, und wählen Sie einen Ordner zum Erstellen der app in. Erstellen Sie jetzt auf diesen Ordner, und nennen Sie es **App**. Klicken Sie dann mit der **App** Ordner ausgewählt haben, klicken Sie auf **Ordner auswählen**.

4.  Erstellen Ihres Projekts zu Unity beginnt die **App** Ordner.

5.  Einmal Unity wurde (es kann einige Zeit dauern) erstellen, öffnen ein **Datei-Explorer** Fenster am Speicherort des Builds (Überprüfen Sie Ihre Taskleiste aus, wie es unter Umständen nicht immer über Ihre Windows angezeigt und Sie über das Hinzufügen eines neuen benachrichtigt Fenster ").

Für HoloLens bereitstellen:

1.  Sie benötigen die IP-Adresse Ihrer HoloLens (für Remote bereitstellen), und um sicherzustellen, dass Ihre HoloLens befindet sich in **Entwicklermodus**. Gehen Sie dazu wie folgt vor:

    1.  Während Ihre HoloLens steht, geteert, öffnen Sie die **Einstellungen**.

    2.  Wechseln Sie zu **Netzwerk und Internet** > **Wi-Fi** > **erweiterte Optionen**

    3.  Beachten Sie die **IPv4** Adresse.

    4.  Navigieren Sie als Nächstes zurück zum **Einstellungen**, und klicken Sie dann **Update und Sicherheit** > **für Entwickler**

    5.  Legen Sie **Entwicklermodus auf**.

2.  Navigieren Sie zu Ihrem neuen Unity-Build (die **App** Ordner), und öffnen Sie die Projektmappendatei mit **Visual Studio**.

3.  In der *Projektmappenkonfiguration* wählen **Debuggen**.

4.  In der *Projektmappenplattform*Option **X86, Remotecomputer**. Werden Sie aufgefordert, fügen Sie der **IP-Adresse** von einem Remotegerät (die HoloLens, in diesem Fall, den Sie notiert haben).

    ![](images/AzureLabs-Lab302b-34.png)

5. Wechseln Sie zu **erstellen** Menü, und klicken Sie auf **Projektmappe bereitstellen** zum querladen der Anwendung in Ihrem HoloLens.

6. Ihre app sollte nun in der Liste der installierten apps auf Ihre HoloLens, möchten Sie die gestartet werden, angezeigt werden.

> [!NOTE]
> Legen Sie zum Bereitstellen auf immersive Kopfhörer der **Projektmappenplattform** zu *lokalen Computer*, und legen Sie die **Konfiguration** zu *Debuggen*, mit *X86* als die **Plattform**. Klicken Sie dann bereitstellen, in der lokalen Computer, mit der **erstellen** Menüelement auswählen *Projektmappe bereitstellen*. 

## <a name="to-use-the-application"></a>Die Anwendung zu verwenden:

So wechseln Sie die app-Funktionalität zwischen *Training* Modus und *Vorhersage* Modus Sie zum aktualisieren müssen der **AppMode** Variablen, befindet sich in der **Awake()** Methode befindet sich innerhalb der *digitale Bilder* Klasse.

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
oder
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

In *Training* Modus:

- Sehen Sie sich **Maus** oder **Tastatur** und verwenden Sie die **tippen**.

- Als Nächstes wird Text angezeigt werden Sie aufgefordert werden, geben Sie ein Tag.

- Angenommen, eine **Maus** oder **Tastatur**.


In *Vorhersage* Modus:

- Ein Objekt, und verwenden Sie die **tippen**.

- Text wird angezeigt, die das Objekt erkannt, mit der höchsten Wahrscheinlichkeit (Dies wird normalisiert) bereitstellt.

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a>Kapitel 14 – bewerten und verbessern Ihre Custom Vision-Modell

Um den Dienst mehr Genauigkeit zu gewährleisten, müssen Sie zum Trainieren des Modells für die Vorhersage verwendet weiterhin. Dies erfolgt durch die Verwendung Ihrer neuen Anwendung und mit der *Training* und *Vorhersage* Modi, mit der zweiten müssen im Portal finden Sie auf die ist, was in diesem Kapitel behandelt wird. Bereiten Sie Ihr Portal oft noch einmal, um Ihr Modell kontinuierlich zu verbessern.

1. Navigieren Sie zu Ihrem Azure Custom Vision-Portal erneut, und wählen Sie nach der Sie in Ihrem Projekt sind, die *Vorhersagen* Registerkarte (von oben in der Mitte der Seite):

    ![](images/AzureLabs-Lab302b-35.png)

2. Sie sehen alle Images, die an den Dienst gesendet wurden, während die Anwendung ausgeführt wurde. Wenn Sie über die Bilder zeigen, werden sie Sie mit den Vorhersagen bereitstellen, die für das Bild vorgenommen wurden:

    ![](images/AzureLabs-Lab302b-36.png)

3. Wählen Sie eine Ihrer Images, um ihn zu öffnen. Sobald geöffnet ist, wird der Vorhersagefehler für das Bild auf der rechten Seite angezeigt. Wenn Sie die Vorhersagen korrekt waren, und Sie möchten dieses Image Ihres Diensts trainingsmodell hinzufügen, klicken Sie auf die *Meine Tags* Eingabefeld ein, und wählen Sie das Tag, das Sie zuordnen möchten. Wenn Sie fertig sind, klicken Sie auf die *speichern und schließen Sie* Schaltfläche unten rechts, und fahren Sie mit der nächsten Abbildung fort.

    ![](images/AzureLabs-Lab302b-37.png)

4. Sobald Sie sich an das Raster der Images sind, werden Sie feststellen, dass die Bilder, die Sie Tags hinzugefügt (und gespeichert haben), entfernt werden. Wenn keine Bilder Sie Sie denken müssen sich nicht auf Ihr markierte Element enthaltenen finden, können Sie sie löschen, klicken Sie auf der Teilstriche auf diesem Image (hierzu können für verschiedene Images zu finden), und klicken Sie dann auf *löschen* in der oberen rechten Ecke der Rasterseite. Klicken Sie auf das Popupfenster, das folgt, Sie können auf eine *Ja, löschen Sie* oder *keine*, um den Löschvorgang zu bestätigen, oder brechen Sie den Befehl ein, bzw. 

    ![](images/AzureLabs-Lab302b-38.png)

5. Wenn Sie fortfahren möchten, klicken Sie auf die grüne *Train* Schaltfläche oben rechts. Mit all den Abbildern, die Sie nun bereitgestellt haben (wodurch sie genauere wird), wird Ihr Dienstmodell trainiert werden. Nachdem das Training abgeschlossen ist, stellen Sie sicher, auf die *Standard* , Schaltfläche, damit Ihre *Vorhersage URL* weiterhin die aktuelle Iteration des Diensts verwendet.

    ![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)

## <a name="your-finished-custom-vision-api-application"></a>Der fertigen Anwendung für benutzerdefiniertes maschinelles sehen-API

Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die nutzt Azure benutzerdefiniertes maschinelles sehen-API zum Erkennen von realen Objekten, das Dienst-Modell zu trainieren und Anzeigen von Gewissheit wie wir gesehen haben.

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a>Bonus-Übungen

### <a name="exercise-1"></a>Übung 1

Trainieren Ihrer **Custom Vision Service** , weitere Objekte zu erkennen.

### <a name="exercise-2"></a>Übung 2

Als Möglichkeit erweitern, was Sie gelernt haben führen Sie die folgenden Übungen:

Wiedergeben Sie Sound, wenn ein Objekt erkannt wird.

### <a name="exercise-3"></a>Übung 3

Verwenden Sie die API des Diensts mit der gleichen Images erneut zu trainieren Ihrer app analysiert, also um den Dienst mehr Genauigkeit zu gewährleisten (sowohl Vorhersagen und Trainieren gleichzeitig ausgeführt werden).
