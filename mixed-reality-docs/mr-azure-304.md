---
title: MR und Azure 304 - gesichtserkennung
description: Führen Sie diesen Kurs erfahren, wie Sie Azure-Gesichtserkennung innerhalb einer mixed Reality-Anwendung zu implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorials, api, gesichtserkennungs, Hololens, immersive Vr
ms.openlocfilehash: 6330d3e5c51d6b2cbc43ea795a3f953a5b14d6f1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596465"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

<br> 

# <a name="mr-and-azure-304-face-recognition"></a>MR und Azure 304: Gesichtserkennung

![Ergebnis der Abschluss dieses Kurses](images/AzureLabs-Lab4-00.png)

In diesem Kurs erfahren Sie das Hinzufügen von Funktionen für die Erkennung von Face einer mixed Reality-Anwendung mithilfe von Azure Cognitive Services, mit der Gesichtserkennungs-API von Microsoft.

*Gesichtserkennungs-API von Azure* ist ein Microsoft-Dienst, die Entwickler mit den fortschrittlichsten gesichtserkennungsalgorithmen, alles in der Cloud bereitstellt. Die *Gesichtserkennungs-API* verfügt über zwei Hauptfunktionen: gesichtserkennung mit Attributen und gesichtserkennungs. Dadurch können Entwickler legen Sie einfach einen Satz von Gruppen für Flächen, und klicken Sie dann Abfrage Bilder an den Dienst später senden, um zu bestimmen, zu denen ein Gesicht gehört. Weitere Informationen finden Sie auf die [Azure Gesichtserkennung Seite](https://azure.microsoft.com/services/cognitive-services/face/).

Nach Abschluss dieses Kurses, verfügen Sie über ein mixed Reality HoloLens-Anwendung, die für die folgenden Aufgaben werden können

1. Verwenden einer **tippen Geste** initiiert die Erfassung eines Abbilds mithilfe der integrierten Kamera für HoloLens. 
2. Senden Sie das erfasste Abbild der *Gesichtserkennungs-API von Azure* Service.
3. Erhalten Sie die Ergebnisse der *Gesichtserkennungs-API* Algorithmus.
4. Verwenden Sie eine einfache Benutzeroberfläche, um den Namen der übereinstimmenden Personen anzuzeigen.

Dadurch erfahren Sie, wie die Ergebnisse aus der Gesichtserkennungs-API-Dienst in Ihre Unity-basierte mixed Reality-Anwendung zu erhalten.

In Ihrer Anwendung obliegt es Ihnen, wie Sie die Ergebnisse in Ihr Design integrieren werden. Dieser Kurs erfahren Sie, wie Sie ein Azure-Dienst in Ihrem Unity-Projekt zu integrieren. Es ist Ihre Aufgabe, verwenden Sie das wissen, dass Sie aus diesem Kurs zum Verbessern Ihrer mixed Reality-Anwendung erhalten.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td> MR und Azure 304: Gesichtserkennung</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Während dieser Kurs in erster Linie für HoloLens ausgerichtet ist, können Sie auch anwenden, was Sie in diesem Kurs, Faszinierende Windows Mixed Reality (VR)-Headsets lernen. Da immersive Headsets von (VR) nicht zugegriffen werden kann, Kameras verfügen, benötigen Sie eine externe Kamera, die mit dem PC verbunden. Wie Sie den Kurs halten, sehen Anmerkungen zu dieser Version Sie auf alle Änderungen, die Sie möglicherweise zur Unterstützung von immersive Headsets von (VR) einsetzen müssen.

## <a name="prerequisites"></a>Vorraussetzungen

> [!NOTE]
> In diesem Tutorial wurde für Entwickler mit Erfahrung mit Unity entwickelt und C#. Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Mai 2018) überprüft wurde. Sie können zur Verwendung der neuesten Software, wie in der [Installieren der Tools](install-the-tools.md) Artikel, obwohl es nicht davon ausgegangen werden soll, dass die Informationen in diesem Kurs perfekt was finden Sie in der neueren Software entspricht als die unten Angaben aufgeführten .

Es wird empfohlen, die folgende Hardware und Software für diesen Kurs:

- Eine Entwicklungs-PC [kompatibel mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für immersive (VR) Kopfhörer-Entwicklung
- [Windows 10 Fall Creators Update (oder höher) mit der Entwicklermodus aktiviert ist](install-the-tools.md)
- [Das neueste Windows 10-SDK](install-the-tools.md)
- [Unity 2017.4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- Ein [immersive Windows Mixed Reality (VR)-Kopfhörer](immersive-headset-hardware-details.md) oder [Microsoft HoloLens](hololens-hardware-details.md) mit Entwicklermodus aktiviert ist
- Eine Kamera, die Verbindung mit Ihrem PC (für immersive Kopfhörer Entwicklung)
- Zugriff auf das Internet für die Einrichtung von Azure und Gesichtserkennungs-API abrufen

## <a name="before-you-start"></a>Bevor Sie beginnen

1.  Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).
2.  Richten Sie ein und Testen Sie Ihre HoloLens. Bei Bedarf Unterstützung zum Einrichten Ihrer HoloLens, [stellen Sie sicher, dass die HoloLens-Setup-Artikel finden Sie unter](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Es ist eine gute Idee, die Kalibrierung und Optimierung der Sensor ausführen, wenn Sie beginnen, eine neue HoloLens-App (manchmal ist es hilfreich, diese Aufgaben für jeden Benutzer) entwickeln. 

Um Hilfe zur Kalibrierung, befolgen Sie diese [Link zum Artikel HoloLens Kalibrierung](calibration.md#hololens).

Um Hilfe zur Optimierung der Sensor, befolgen Sie diese [Link zum Optimieren von HoloLens Sensor](sensor-tuning.md).

## <a name="chapter-1---the-azure-portal"></a>Kapitel 1: das Azure-Portal

Verwenden der *Gesichtserkennungs-API* Service in Azure müssen Sie so konfigurieren Sie eine Instanz des Diensts, der für Ihre Anwendung verfügbar gemacht werden.

1.  Melden Sie sich zunächst auf die [Azure-Portal](https://portal.azure.com). 

    > [!NOTE]
    > Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen. Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.

2.  Sobald Sie angemeldet sind, klicken Sie auf **neu** in der oberen linken Ecke, und suchen Sie nach *Gesichtserkennungs-API*, drücken Sie die **EINGABETASTE**.

    ![Suchen Sie nach gesichtserkennungs-api](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > Das Wort **neu** wurden möglicherweise durch ersetzt **erstellen Sie eine Ressource**, in neueren-Portalen.

3.  Die neue Seite bietet eine Beschreibung der *Gesichtserkennungs-API* Service. Unten links der Aufforderung, wählen die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.

    ![gesichtserkennungs-API-Informationen](images/AzureLabs-Lab4-02.png)

4.  Nachdem Sie auf geklickt haben **erstellen**:

    1. Fügen Sie dem gewünschten Namen für diese Dienstinstanz.

    2. Wählen Sie ein Abonnement.

    3. Wählen Sie der Tarif für Sie geeignet, ist dies das erste Mal erstellen eine *Gesichtserkennungs-API-Dienst*, freier-Tarif (mit dem Namen F0) für Sie verfügbar sein sollen.

    4. Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diesen Labs) unter einer allgemeinen Ressourcengruppe zu halten). 

        > Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, bitte [finden Sie im Artikel der Resource-Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Der UWP-app **Person Maker**, die Sie später verwenden, erfordert die Verwendung von "USA, Westen", Speicherort.

    6. Sie müssen auch bestätigen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.

    7. Wählen Sie **erstellen*.**

        ![Erstellen Sie gesichtserkennungs-API-Dienst](images/AzureLabs-Lab4-03.png)

5.  Nachdem Sie auf geklickt haben **erstellen*** müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.

6.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Benachrichtigung über Erstellung des Diensts](images/AzureLabs-Lab4-04.png)

7.  Klicken Sie auf die Benachrichtigungen an Ihre neue Dienstinstanz zu untersuchen.

    ![Wechseln Sie zu ressourcenbenachrichtigung](images/AzureLabs-Lab4-05.png)

8.  Wenn Sie bereit sind, klicken Sie auf **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen.

    ![Zugriff gesichtserkennungs-API-Schlüssel](images/AzureLabs-Lab4-06.png)

9.  In diesem Tutorial müssen Ihre Anwendung Aufrufe an Ihren Dienst, die durch die Verwendung Ihres Diensts Abonnement 'Key' ausgeführt wird. Von der *Schnellstart* Seite, der Ihre *Gesichtserkennungs-API* Dienst, den ersten Punkt ist 1, number, zu *nehmen Sie Ihre Schlüssel.*

10. Auf der *Service* Seite Wählen Sie entweder das blaue **Schlüssel** Hyperlink (sofern auf der Seite "Schnellstart"), oder die **Schlüssel** Link im Navigationsmenü Services (auf der linken Seite, gekennzeichnet durch die " Schlüssel "Symbol"), um Ihre Schlüssel anzuzeigen.

    > [!NOTE] 
    > Notieren Sie sich einer der Schlüssel, und schützen Sie, wie Sie es später benötigen werden.

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>Kapitel 2: verwenden die "Person Maker" UWP-Anwendung

Vergewissern Sie sich zum Herunterladen der vorgefertigten UWP-Anwendung namens [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip). Diese app ist nicht das Endprodukt für diesen Kurs, nur ein Tool, mit denen Sie Ihre Azure-Einträge, die spätere Projekt abhängig sind, wird zu erstellen.

**Person Maker** können Sie Azure-Einträge zu erstellen, die Personen und Personengruppen zugeordnet sind. Die Anwendung werden alle erforderliche Informationen in einem Format platzieren, die dann später von der FaceAPI verwendet werden kann um die Gesichter von Personen zu erkennen, die Sie hinzugefügt haben. 

> [WICHTIG] **Person Maker** verwendet einige grundlegende Einschränkungen, um sicherzustellen, dass Sie nicht die Anzahl der Aufrufe pro Minute überschritten, werden die **kostenloses Abonnement Tarif**. Der grüne Text am Anfang wird sich in Rot ändern und als "Aktiv" zu aktualisieren, wenn die Drosselung auftritt; Wenn dies der Fall ist, warten Sie einfach die Anwendung (es wird gewartet, bis sie als Nächstes fortgesetzt werden kann den Zugriff auf den gesichtserkennungs-Dienst "IN-aktiv" aktualisiert werden, wenn Sie ihn erneut verwenden können).

Diese Anwendung verwendet die *Microsoft.ProjectOxford.Face* verwenden der Gesichtserkennungs-API-Bibliotheken, die Sie die vollständige vornehmen können. Diese Bibliothek steht kostenlos als NuGet-Paket zur Verfügung. Weitere Informationen zu diesem und ähnlichen APIs [stellen Sie sicher, dass die API-Referenzartikel finden Sie unter](https://docs.microsoft.com/azure/cognitive-services/face/apireference).

> [!NOTE] 
> Hierbei handelt es sich um nur die erforderlichen Schritte, die Anweisungen dazu, wie all dies wird weiter unten in das Dokument. Die **Person Maker** app können Sie:
>
> - Erstellen Sie eine *Personengruppe*, eine Gruppe besteht aus mehreren Personen, die Sie es zuordnen möchten. Mit Ihrem Azure-Konto können Sie mehrere Personengruppen hosten.
>
> - Erstellen Sie eine *Person*, dies ist ein Mitglied der Gruppe eine Person. Jede Person hat eine Reihe von *Gesicht* Abbilder zugeordnet.
>
> -  Weisen Sie *stehen Images* zu eine *Person*, um Ihre Azure-Gesichtserkennungs-API-Dienst zur Erkennung von zuzulassen eine *Person* mit den entsprechenden *Gesicht*.
>
> -  *Train* Ihre *Azure Gesichtserkennungs-API-Dienst*.

Denken Sie daran, also um diese app zur Erkennung von Personen zu trainieren, Sie zehn (10) vergrößerte Fotos von jeder Person benötigen, die Sie zu Ihrer Person-Gruppe hinzufügen möchten. Der Windows 10-Cam-App können Sie diese Verknüpfungen gelangen. Müssen Sie sicherstellen, dass jedes Foto deaktiviert ist (vermeiden Sie Unschärfe, verdeckt oder versteht, aus dem Subjekt wird), müssen Sie das Foto im JPG- oder Png-Dateiformat mit der Größe einer Bilddatei wird nicht größer **4 MB**, und nicht weniger als **1 KB**.

> [!NOTE]
> Wenn Sie dieses Lernprogramm durcharbeiten, verwenden Sie nicht Ihre eigenen Gesicht für das Training, als wenn Sie die HoloLens auf Einfügen, Sie selbst ansehen können nicht. Verwenden Sie das Gesicht von Kollegen oder Fellow Schüler/Student ein.

Ausführung **Person Maker**:

1.  Öffnen Sie die **PersonMaker** Ordner und doppelklicken klicken Sie auf die *PersonMaker Lösung* , öffnen Sie ihn mit *Visual Studio*.

2.  Sobald die *PersonMaker Lösung* geöffnet ist, stellen Sie sicher, dass:

    1. Die *Projektmappenkonfiguration* nastaven NA hodnotu **Debuggen**.

    2. Die *Projektmappenplattform* nastaven NA hodnotu **X86**

    3. Die *Zielplattform* ist **lokalen Computer**.

    4.  Außerdem müssen Sie möglicherweise *NuGet-Pakete wiederherstellen* (mit der rechten Maustaste die *Lösung* , und wählen Sie **NuGet-Pakete wiederherstellen**).

3.  Klicken Sie auf *lokalen Computer* und die Anwendung wird gestartet. Beachten Sie, auf kleineren Bildschirmen, alle Inhalte möglicherweise nicht sichtbar, obwohl Sie weiteren unten zum Anzeigen einen Bildlauf durchführen können.

    ![Person Maker-Benutzeroberfläche](images/AzureLabs-Lab4-07.png)

4.  Fügen Sie Ihrer **Authentifizierungsschlüssel für die Azure**, der Sie enthalten soll, aus Ihrer *Gesichtserkennungs-API* innerhalb von Azure Service.

5.  Fügen Sie ein:

    1. Die *ID* Sie zuweisen möchten die *Personengruppe*. Die ID muss in Kleinbuchstaben ohne Leerzeichen sein. Notieren Sie sich diese ID an, wie sie weiter unten in Ihrem Unity-Projekt erforderlich ist.
    2. Die *Namen* Sie zuweisen möchten die *Personengruppe* (können Leerzeichen enthalten).


6.  Drücken Sie **Personengruppe erstellen** Schaltfläche. Eine bestätigungsmeldung sollte unterhalb der Schaltfläche angezeigt werden.

> [!NOTE]
> Wenn Sie einen Fehler "Zugriff verweigert" haben, überprüfen Sie den Speicherort, die, den Sie für Ihr Azure-Dienst festlegen. Wie bereits erwähnt, dient diese app für "USA, Westen".

> [!IMPORTANT]
> Sie werden feststellen, dass Sie, auch klicken können die **Abrufen einer bekannten Gruppe** Schaltfläche: sind über, wenn Sie eine Person bereits erstellt haben, Gruppe und die möchten, verwenden, anstatt ein neues erstellen. Beachten Sie, wenn Sie auf *erstellen Sie eine Gruppe von Personen* mit einer bekannten Gruppe, dies wird auch "abrufen" eine Gruppe.

7.  Fügen Sie der *Namen* von der *Person* erstellt werden soll.

    1. Klicken Sie auf die **Person erstellen** Schaltfläche.

    2. Eine bestätigungsmeldung sollte unterhalb der Schaltfläche angezeigt werden.

    3. Wenn Sie eine Person zu löschen. möchten Sie zuvor erstellt haben, können Sie den Namen in das Textfeld, und drücken Sie schreiben **Person löschen**

8.  Stellen Sie sicher, dass Sie den Speicherort des Fotos zehn (10) der Person kennen, die Sie zur Gruppe hinzufügen möchten.

9.  Drücken Sie **erstellen "und" Ordner öffnen** , öffnen Sie Windows Explorer zu dem Ordner, die die Person, die zugeordnet sind. Hinzufügen von Bildern zehn (10) im Ordner "". Diese muss der *JPG* oder *PNG* Dateiformat.

10. Klicken Sie auf **an Azure übermitteln**. Ein Zähler zeigt den Status der Übermittlung, gefolgt von einer Meldung, wenn er abgeschlossen wurde.

11. Klicken Sie nach der Zähler beendet wurde und eine bestätigungsmeldung angezeigt wurde auf **trainieren** zum Trainieren Ihres Diensts.

Sobald der Vorgang abgeschlossen wurde, können Sie in Unity zu verschieben.

## <a name="chapter-3---set-up-the-unity-project"></a>Kapitel 3: Einrichten von Unity-Projekts

Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit mixed Reality und daher ist eine gute Vorlage für andere Projekte.

1.  Open *Unity* , und klicken Sie auf **neu**. 

    ![Starten Sie die neues Unity-Projekt.](images/AzureLabs-Lab4-08.png)

2.  Sie müssen nun einen Namen für die Unity-Projekt bereitstellen. Fügen Sie **MR_FaceRecognition**. Stellen Sie sicher, dass der Projekttyp nastaven NA hodnotu **3D**. Legen Sie die **Speicherort** auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser). Klicken Sie auf **projekterstellung**.

    ![Die Details für die neue Unity-Projekt.](images/AzureLabs-Lab4-09.png)

3.  Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**. Wechseln Sie zu **Bearbeiten > Voreinstellungen** und navigieren Sie dann im neuen Fenster zu **externe Tools**. Änderung **externen Skript-Editors** zu **Visual Studio 2017**. Schließen der **Voreinstellungen** Fenster.

    ![Aktualisieren Sie die Skript-Editor-Einstellung.](images/AzureLabs-Lab4-10.png)

4.  Öffnen Sie als Nächstes **Datei > Buildeinstellungen** , und wechseln von der Plattform bereitgestellten **universelle Windows-Plattform**, durch Klicken auf die **Plattform wechseln** Schaltfläche.

    ![Fenster "Einstellungen", Switch-Plattform für die UWP zu erstellen.](images/AzureLabs-Lab4-11.png)

5.  Wechseln Sie zu **Datei > Buildeinstellungen** und stellen Sie sicher, dass:

    1. **Geräte** nastaven NA hodnotu **HoloLens**

        > Legen Sie für die immersive Headsets, **Zielgerät** zu *einem beliebigen Gerät*.

    2. **Buildtyp** nastaven NA hodnotu **D3D**
    3. **SDK** nastaven NA hodnotu **zuletzt installierte**
    4. **Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**
    5. **Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**
    6. Die Szene speichern und mit dem Build hinzugefügt werden. 

        1. Hierzu **öffnen Szenen hinzufügen**. Ein Speichern Fenster wird angezeigt.

            ![Klicken Sie auf, öffnen im Hintergrund-Schaltfläche "hinzufügen"](images/AzureLabs-Lab4-12.png)

        2. Wählen Sie die **neuer Ordner** Schaltfläche zum Erstellen eines neuen Ordners, nennen Sie sie **Szenen**.

            ![Erstellen Sie neue Ordner "Scripts"](images/AzureLabs-Lab4-13.png)

        3. Öffnen Sie den neu erstellten **Szenen** Ordner, und klicken Sie dann in der **Dateiname**: Textfeld **FaceRecScene**, drücken Sie dann die **speichern**.

            ![Geben Sie neue Szene einen Namen zu.](images/AzureLabs-Lab4-14.png)

    7. Die Einstellungen im verbleibenden *Buildeinstellungen*, sollte jetzt als Standard bleiben.

6. In der *Buildeinstellungen* Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dadurch wird den entsprechenden Bereich geöffnet, im Bereich, in dem die *Inspektor* befindet. 

    ![Öffnen der playereinstellungen.](images/AzureLabs-Lab4-15.png)

7. In diesem Bereich sind müssen einige Einstellungen überprüft werden:

    1. In der **Weitere Einstellungen** Registerkarte:

        1. **Scripting** **Laufzeitversion** muss **experimentell** (.NET 4.6 entspricht). Das Ändern dieser Eigenschaft löst eine Editor-Neustart erforderlich.
        2. **Back-End-Scripting** muss **.NET**
        3. **API-Kompatibilitätsebene** muss **.NET 4.6**

            ![Andere Einstellungen zu aktualisieren.](images/AzureLabs-Lab4-16.png)
      
    2. In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:

        - **InternetClient**
        - **Webcam**

            ![Veröffentlichungseinstellungen werden aktualisiert.](images/AzureLabs-Lab4-17.png)

    3. Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality-SDK**  hinzugefügt wird.

        ![Aktualisieren Sie die X-R-Einstellungen.](images/AzureLabs-Lab4-18.png)

8.  Im *Buildeinstellungen*, **Unity C# Projekte** nicht mehr abgeblendet ist, aktivieren Sie das Kontrollkästchen neben dieser. 
9.  Schließen Sie das Fenster "erstellen".
10. Speichern Sie Ihre Szene und das Projekt (**Datei > Speichern SZENE / FILE > Speichern Projekt**).

## <a name="chapter-4---main-camera-setup"></a>Kapitel 4: Main Camera-setup

> [!IMPORTANT]
> Wenn Sie, überspringen möchten die *Unity einrichten* -Komponente dieser Kurs, und direkt in Code fortfahren, können Sie [Herunterladen dieser .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage), und importieren Sie es in Ihr Projekt als eine [benutzerdefinierte Paket](https://docs.unity3d.com/Manual/AssetPackages.html). Beachten Sie, dass dieses Paket auch den Import von enthält der *Newtonsoft-DLL*, abgedeckte in [Kapitel 5](#chapter-5--import-the-newtonsoft.json-library). Mit diesem nicht importiert haben, können Sie weiterhin von [Kapitel 6](#chapter-6-create-the-faceanalysis-class).

1.  In der *Hierarchie* Panel, wählen Sie die **Main Camera**.

2.  Wenn ausgewählt, Sie werden auf alle Komponenten finden Sie unter den **Main Camera** in die *Inspektor Bereich*.

    1. Die **Kameraobjekt** muss den Namen **Main Camera** (Beachten Sie die Rechtschreibung!)

    2. Die Main Camera **Tag** muss festgelegt werden, um **MainCamera** (Beachten Sie die Rechtschreibung!)

    3. Stellen Sie sicher, dass die **transformieren Position** nastaven NA hodnotu **0, 0, 0**

    4. Legen Sie **Kennzeichnungen löschen** zu **Volltonfarbe**

    5. Legen Sie die **Hintergrund** Farbe der Kamera-Komponente auf **Schwarz, Alpha 0 (Hex-Code: #00000000)**

        ![Richten Sie die Kamera-Komponenten](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>Kapitel 5: Importieren der Bibliothek "newtonsoft.JSON"

> [!IMPORTANT]
> Wenn Sie in der '.unitypackage"importiert die [letzte Kapitel](#chapter-4--main-camera-setup), können Sie in diesem Kapitel überspringen.

Können Sie deserialisieren und Serialisieren von Objekten, die empfangen und an den Bot-Dienst gesendet, die Sie herunterladen müssen die *"newtonsoft.JSON"* Bibliothek. Sehen Sie eine kompatible Version, die bereits mit der richtigen Struktur der Unity-Ordner in diesem organisiert [Unity-Paketdatei](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage). 

So importieren Sie die Bibliothek:

1.  Herunterladen des Unity-Pakets.
2.  Klicken Sie auf **Assets**, **Paket importieren**, **Anpassungspaket**.

    ![Importieren der Bibliothek "newtonsoft.JSON"](images/AzureLabs-Lab4-20.png)

3.  Suchen Sie nach der Unity-Paket, das Sie heruntergeladen haben, und klicken Sie auf Öffnen.
4.  Stellen Sie sicher, dass alle Komponenten des Pakets ausgewählt werden, und klicken Sie auf **Import**.

    ![Importieren der Bibliothek "newtonsoft.JSON"](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>Kapitel 6: Erstellen Sie die FaceAnalysis-Klasse

Der Zweck der FaceAnalysis-Klasse werden die Methoden, die zum Kommunizieren mit Ihrem Azure-Face-Erkennung-Dienst zu hosten. 

- Nach dem Senden des Diensts ein Aufzeichnungsabbild, wird es analysieren sie identifizieren die Gesichter von und bestimmen, ob alle mit einer bekannten Person angehören. 
- Wenn eine bekannte Person gefunden wird, wird diese Klasse den Namen als Benutzeroberflächentext in der Szene angezeigt.

Zum Erstellen der *FaceAnalysis* Klasse:

 1. Mit der rechten Maustaste den *Ordner "Assets"* im Projektfenster befindet, klicken Sie dann auf **erstellen** > **Ordner**. Rufen Sie den Ordner **Skripts**. 

    ![Erstellen Sie die FaceAnalysis-Klasse.](images/AzureLabs-Lab4-22.png)

2.  Doppelklicken Sie auf den Ordner, der gerade erstellt haben, um ihn zu öffnen. 
3.  Mit der rechten Maustaste in den Ordner, und klicken Sie dann auf **erstellen**  >   **C# Skript**. Rufen Sie das Skript *FaceAnalysis*. 
4.  Doppelklicken Sie auf dem neuen *FaceAnalysis* Skript, um ihn mit Visual Studio 2017 zu öffnen.
5.  Geben Sie die folgenden Namespaces, die oben genannten der *FaceAnalysis* Klasse:

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  Jetzt müssen Sie alle Objekte hinzufügen, die für die deserialising verwendet werden. Diese Objekte müssen hinzugefügt werden **außerhalb** von der *FaceAnalysis* Skript (unterhalb der untere geschweifte Klammer). 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. Die *Start()* und *Update()* Methoden nicht verwendet werden, also jetzt löschen. 

8.  In der *FaceAnalysis* -Klasse verwenden, fügen Sie die folgenden Variablen:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > Ersetzen Sie die **Schlüssel** und **PersonGroupId** mit Ihrem Dienstschlüssel und die Id der Gruppe, die Sie zuvor erstellt haben.

9.  Hinzufügen der *Awake()* -Methode, die in der Klasse initialisiert, Hinzufügen der *digitale Bilder* Klasse, um die Main Camera und ruft die Methode zum Erstellen von Bezeichnung:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. Hinzufügen der *CreateLabel()* -Methode, die erstellt die *Bezeichnung* Objekt, das das Analyseergebnis anzuzeigen:

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. Hinzufügen der *DetectFacesFromImage()* und *GetImageAsByteArray()* Methode. Die erste fordert des Erkennung Gesicht, um alle möglichen Gesicht in der Abbildung übermittelten zu erkennen, während Letzteres erforderlich, um das erfasste Abbild in ein Array von Bytes zu konvertieren ist:

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. Hinzufügen der *IdentifyFaces()* -Methode, die Anforderungen der *Gesicht Anerkennung Service* zum Identifizieren von jeder bekannten Fläche, die zuvor im übermittelten Bild erkannt. Die Anforderung gibt die Id identifizierten Person jedoch nicht den Namen zurück:

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialise to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. Hinzufügen der *GetPerson()* Methode. Durch die Person bereitstellen, Id, dieser Methode und die Anforderungen für die *Gesicht Anerkennung Service* der Name der identifizierten Person zurückgegeben:

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  Denken Sie daran, **speichern** die Änderungen vor dem Wechsel zurück zu Unity-Editor.
15.  Im Unity-Editor, ziehen Sie das Skript FaceAnalysis aus dem Ordner "Scripts" im Projektpanel auf das Main Camera-Objekt in der *Hierarchie Bereich*. Die neue Skriptkomponente wird also die Main Camera hinzugefügt werden. 

![Platzieren Sie FaceAnalysis auf die Hauptkamera](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>Kapitel 7: Erstellen Sie die digitale Bilder-Klasse

Der Zweck der *digitale Bilder* Klasse wird zum Hosten der Methoden, die für die Kommunikation mit Ihrer *Azure Gesicht Anerkennung Service* auf das Bild zu analysieren, Sie erfasst werden, identifiziert Gesichter darin, und bestimmen, wenn er zu einer bekannten Person gehört. Wenn eine bekannte Person gefunden wird, wird diese Klasse den Namen als Benutzeroberflächentext in der Szene angezeigt.

Zum Erstellen der *digitale Bilder* Klasse:
 
1.  Klicken Sie auf auf die **Skripts** Ordner, die Sie zuvor erstellt haben, und klicken Sie dann auf **erstellen**,  **C# Skript**. Rufen Sie das Skript *digitale Bilder*. 
2.  Doppelklicken Sie auf dem neuen *digitale Bilder* Skript, um ihn mit Visual Studio 2017 zu öffnen.
3.  Geben Sie die folgenden Namespaces über die digitale Bilder-Klasse:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  In der *digitale Bilder* -Klasse verwenden, fügen Sie die folgenden Variablen:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  Hinzufügen der *Awake()* und *Start()* Methoden, die zum Initialisieren der Klasse und ermöglichen die HoloLens zum Erfassen des Benutzers Gesten erforderlich sind:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  Hinzufügen der *TapHandler()* die aufgerufen wird, wenn der Benutzer führt eine *Tippen Sie auf* Geste:

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  Hinzufügen der *ExecuteImageCaptureAndAnalysis()* -Methode, die Image-Erfassung beginnen, werden:

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  Fügen Sie die Handler, die aufgerufen werden, wenn der Foto-Capture-Prozess abgeschlossen wurde:

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successfull, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. Denken Sie daran, **speichern** die Änderungen vor dem Wechsel zurück zu Unity-Editor.

## <a name="chapter-8---building-the-solution"></a>Kapitel 8 – Erstellen der Projektmappe

Zur Durchführung eine gründliche Tests der Anwendung werden Sie querladen möchten sie auf Ihre HoloLens benötigen.

Vor dem Ausführen, stellen Sie sicher, dass:

-   Alle Einstellungen, die in Kapitel 3 genannten sind ordnungsgemäß festgelegt. 
-   Das Skript *FaceAnalysis* Main Camera-Objekts angefügt ist. 
-   Sowohl die **Authentication Key** und **Gruppen-Id** festgelegt wurden innerhalb der *FaceAnalysis* Skript.

A: Hierbei weisen Sie können die Projektmappe zu erstellen. Nachdem die Lösung erstellt wurde, werden Sie zum Bereitstellen der Anwendung bereit.

Um den Buildprozess zu starten:

1.  Speichern Sie die aktuelle Szene durch Klicken auf in Datei speichern.
2.  Wechseln Sie zur Datei, die Einstellungen zu erstellen, klicken Sie auf Öffnen Szenen hinzufügen.
3.  Stellen Sie sicher, dass zu Teilstrich Unity C# Projekte.

    ![Die Lösung in Visual Studio bereit.](images/AzureLabs-Lab4-24.png)

4.  Drücken Sie die Builds. Dies der Fall, wird Unity ein Datei-Explorer-Fenster geöffnet, in denen man erstellen, und wählen Sie einen Ordner zum Erstellen der app in. Erstellen Sie diesen Ordner jetzt, in der Unity-Projekt, und rufen sie die App. Drücken Sie mit den App-Ordner ausgewählt haben die Ordner auswählen. 
5.  Unity beginnt mit der Ihr Projekt, um den App-Ordner erstellen. 
6.  Nachdem Unity die erstellen (es kann einige Zeit dauern) abgeschlossen ist, an der Position des Builds ein Datei-Explorer-Fenster wird geöffnet.

    ![Die Lösung in Visual Studio bereit.](images/AzureLabs-Lab4-25.png)

7.  Öffnen Sie Ihre App-Ordner, und öffnen Sie dann die neue Projektmappe (wie oben MR_FaceRecognition.sln dargestellt).


## <a name="chapter-9---deploying-your-application"></a>Kapitel 9: Bereitstellen der Anwendung

Für HoloLens bereitstellen:

1.  Sie benötigen die IP-Adresse Ihrer HoloLens (für Remote bereitstellen), und um sicherzustellen, dass Ihre HoloLens befindet sich in **Entwicklermodus**. Gehen Sie dazu wie folgt vor:

    1. Während Ihre HoloLens steht, geteert, öffnen Sie die **Einstellungen**.
    2. Wechseln Sie zu **Netzwerk und Internet > Wi-Fi-> Erweiterte Optionen**
    3. Beachten Sie die **IPv4** Adresse.
    4. Navigieren Sie als Nächstes zurück zum **Einstellungen**, und klicken Sie dann **Update und Sicherheit > für Entwickler** 
    5. Festlegen des Entwicklermodus auf.

2.  Navigieren Sie zu Ihrem neuen Unity-Build (die *App* Ordner), und öffnen Sie die Projektmappendatei mit *Visual Studio*.
3.  In der Projektmappenkonfiguration Select **Debuggen**.
4.  Wählen Sie in der Plattform für die Projektmappe **X86**, **Remotecomputer**. 

    ![Die Lösung in Visual Studio bereit.](images/AzureLabs-Lab4-26.png)
 
5.  Wechseln Sie zu der **Menü "Build"** und klicken Sie auf **Projektmappe bereitstellen**, zum querladen der Anwendung in Ihrem HoloLens.
6.  Ihre App sollte nun in der Liste der installierten apps auf Ihre HoloLens, möchten Sie die gestartet werden, angezeigt werden.

> [!NOTE]
> Legen Sie zum Bereitstellen auf immersive Kopfhörer der **Projektmappenplattform** zu *lokalen Computer*, und legen Sie die **Konfiguration** zu *Debuggen*, mit *X86* als die **Plattform**. Klicken Sie dann bereitstellen, in der lokalen Computer, mit der **Menü "Build"**, wählen *Projektmappe bereitstellen*. 


## <a name="chapter-10---using-the-application"></a>Kapitel 10 – verwenden die Anwendung

1.  Trägt die HoloLens, um die app zu starten.
2.  Sehen Sie sich die Person, die Sie bei registriert haben, die die *Gesichtserkennungs-API*. Stellen Sie Folgendes sicher:

    -  Dieser Person ist nicht zu entfernten und deutlich sichtbar
    -  Die umgebungsbeleuchtung ist nicht zu dunkel

3.  Verwenden Sie die tippbewegung, um das Bild der Person zu erfassen.
4.  Die App auf die Analysis-Anforderung senden und Empfangen einer Antwort warten.
5.  Wenn die Person, die erfolgreich erkannt wurde, wird der Name der Person als Benutzeroberflächen-Text angezeigt.
6.  Sie können den Capture-Prozess mit der tippbewegung alle paar Sekunden wiederholen.

## <a name="your-finished-azure-face-api-application"></a>Der fertigen Azure Gesichtserkennungs-API-Anwendung

Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die den Dienst Azure-Gesichtserkennung erkennen Sie Gesichter in einem Image, und alle bekannten Gesichtern nutzt.

![Ergebnis der Abschluss dieses Kurses](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>Bonus-Übungen

### <a name="exercise-1"></a>Übung 1

Die **Gesichtserkennungs-API von Azure** ist leistungsstark genug, um bis zu 64 Gesichter in ein einzelnes Abbild zu erkennen. Erweitern Sie die Anwendung, damit sie zwei oder drei Gesichter für viele andere Personen erkennen kann.

### <a name="exercise-2"></a>Übung 2

Die **Gesichtserkennungs-API von Azure** kann darüber hinaus geben Sie alle Arten von Informationen über Bildattribute zurück. Integrieren Sie dies bei der Anwendung. Dies ist möglicherweise noch interessanter, in Kombination mit der [Emotionen-API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).
