---
title: Mr und Azure 304-Gesichtserkennung
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Gesichtserkennung, hololens, immersive, VR
ms.openlocfilehash: 23676684c2ec325f9d6f1924e7a0bad14d41f13e
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926783"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.

<br> 

# <a name="mr-and-azure-304-face-recognition"></a>Mr und Azure 304: Gesichtserkennung

![Ergebnis der Fertigstellung dieses Kurses](images/AzureLabs-Lab4-00.png)

In diesem Kurs erfahren Sie, wie Sie mithilfe von Azure Cognitive Services mit dem Microsoft-Gesichtserkennungs-API Funktionen zur Gesichtserkennung zu einer gemischten Reality-Anwendung hinzufügen.

*Azure Gesichtserkennungs-API* ist ein Microsoft-Dienst, der Entwicklern die fortschrittlichsten Gesichts Algorithmen in der Cloud bereitstellt. Der *Gesichtserkennungs-API* verfügt über zwei Hauptfunktionen: Gesichtserkennung mit Attributen und Gesichtserkennung. Dies ermöglicht es Entwicklern, einfach einen Satz von Gruppen für Gesichter festzulegen und dann Abfrage Images später an den Dienst zu senden, um zu bestimmen, wem ein Gesicht angehört. Weitere Informationen finden Sie auf der [Seite mit der Gesichtserkennung in Azure](https://azure.microsoft.com/services/cognitive-services/face/).

Nachdem Sie diesen Kurs abgeschlossen haben, verfügen Sie über eine Mixed Reality hololens-Anwendung, die Folgendes ausführen kann:

1. Verwenden Sie eine **Tap-Geste** , um die Erfassung eines Bilds mithilfe der on-Board hololens-Kamera zu initiieren. 
2. Senden Sie das erfasste Abbild an den *Azure Gesichtserkennungs-API* -Dienst.
3. Empfangen der Ergebnisse des *Gesichtserkennungs-API* Algorithmus.
4. Verwenden Sie eine einfache Benutzeroberfläche, um den Namen der übereinstimmenden Personen anzuzeigen.

Auf diese Weise erfahren Sie, wie Sie die Ergebnisse aus dem Gesichtserkennungs-API-Dienst in ihrer Unity-basierten gemischten Reality-Anwendung erhalten.

In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren. In diesem Kurs erfahren Sie, wie Sie einen Azure-Dienst in Ihr Unity-Projekt integrieren. Es ist Ihre Aufgabe, das wissen, das Sie aus diesem Kursgewinnen, zu nutzen, um ihre gemischte Reality-Anwendung zu verbessern.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> Mr und Azure 304: Gesichtserkennung</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Dieser Kurs konzentriert sich in erster Linie auf hololens, aber Sie können auch das Erlernen, was Sie in diesem Kurs lernen, auf Windows Mixed Reality-(VR)-Headsets. Da immersive Headsets (VR) nicht über barrierefreie Kameras verfügen, benötigen Sie eine externe Kamera, die mit Ihrem PC verbunden ist. Wenn Sie den Kurs befolgen, finden Sie Hinweise zu allen Änderungen, die Sie möglicherweise für die Unterstützung von immersiven (VR)-Headsets verwenden müssen.

## <a name="prerequisites"></a>Voraussetzungen

> [!NOTE]
> Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen. Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Mai 2018). Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](install-the-tools.md) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt sind.

Für diesen Kurs empfehlen wir die folgende Hardware und Software:

- Einen Entwicklungs-PC, der [mit der Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for Immersive (VR)-Headset-Entwicklung kompatibel ist
- [Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus](install-the-tools.md)
- [Das neueste Windows 10 SDK](install-the-tools.md)
- [Unity 2017,4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- Ein [Windows Mixed Reality-Headset (VR)](immersive-headset-hardware-details.md) oder [Microsoft hololens](hololens-hardware-details.md) mit aktiviertem Entwicklermodus
- Eine Kamera, die mit Ihrem PC verbunden ist (für die immersive Headset-Entwicklung)
- Internet Zugriff für Azure-Setup und Gesichtserkennungs-API-Abruf

## <a name="before-you-start"></a>Bevor Sie beginnen

1.  Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).
2.  Richten Sie Ihre hololens ein, und testen Sie Sie. Wenn Sie Unterstützung für die Einrichtung ihrer hololens benötigen, [besuchen Sie den Artikel zum Einrichten von hololens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Es empfiehlt sich, eine Kalibrierung und Sensor Optimierung durchzuführen, wenn Sie mit der Entwicklung einer neuen hololens-App beginnen (manchmal kann es hilfreich sein, diese Aufgaben für jeden Benutzer auszuführen). 

Hilfe zur Kalibrierung finden Sie unter diesem [Link zum Artikel zur hololens-Kalibrierung](calibration.md#hololens-2).

Hilfe zur Sensor Optimierung finden Sie unter diesem [Link zum Artikel zur Überwachung von hololens-Sensoren](sensor-tuning.md).

## <a name="chapter-1---the-azure-portal"></a>Kapitel 1: Azure-Portal

Wenn Sie den *Gesichtserkennungs-API* -Dienst in Azure verwenden möchten, müssen Sie eine Instanz des-Dienstanbieter konfigurieren, die für die Anwendung verfügbar gemacht wird.

1.  Melden Sie sich zunächst beim [Azure-Portal](https://portal.azure.com)an. 

    > [!NOTE]
    > Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen. Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.

2.  Wenn Sie angemeldet sind, klicken Sie in der oberen linken Ecke auf " **neu** ", und suchen Sie nach *Gesichtserkennungs-API*. Drücken Sie dann die **Eingabe**Taste.

    ![Suchen nach der Face-API](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > Das Wort **New** wurde möglicherweise durch **Create a Resource**in neueren Portalen ersetzt.

3.  Auf der neuen Seite wird eine Beschreibung des *Gesichtserkennungs-API* Dienstanbieter bereitgestellt. Wählen Sie unten links in dieser Eingabeaufforderung die Schaltfläche **Erstellen** aus, um eine Verknüpfung mit diesem Dienst zu erstellen.

    ![Gesichts-API-Informationen](images/AzureLabs-Lab4-02.png)

4.  Nachdem Sie auf **Erstellen**geklickt haben, klicken Sie auf:

    1. Fügen Sie den gewünschten Namen für diese Dienst Instanz ein.

    2. Wählen Sie ein Abonnement aus.

    3. Wählen Sie den für Sie geeigneten Tarif aus. Wenn Sie zum ersten Mal einen *Gesichtserkennungs-API Dienst*erstellen, sollte Ihnen ein Free-Tarif (mit dem Namen "F0") zur Verfügung stehen.

    4. Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** . Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Labs) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern. 

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Die UWP-app " **Person Maker**", die Sie später verwenden, erfordert die Verwendung von "USA, Westen" für den Standort.

    6. Außerdem müssen Sie bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.

    7. Wählen Sie **erstellen *.**

        ![Face-API-Dienst erstellen](images/AzureLabs-Lab4-03.png)

5.  Nachdem Sie auf " **Erstellen** " geklickt haben, müssen Sie warten, bis der Dienst erstellt wird. dieser Vorgang kann einige Minuten in Anspruch nehmen.

6.  Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Benachrichtigung zur Dienst Erstellung](images/AzureLabs-Lab4-04.png)

7.  Klicken Sie auf die Benachrichtigungen, um die neue Dienst Instanz zu untersuchen.

    ![zur Ressourcen Benachrichtigung wechseln](images/AzureLabs-Lab4-05.png)

8.  Wenn Sie bereit sind, klicken Sie auf die Schaltfläche **zum Ressourcen** Wechsel in der Benachrichtigung, um die neue Dienst Instanz zu untersuchen.

    ![Zugriffs Gesichts-API-Schlüssel](images/AzureLabs-Lab4-06.png)

9.  In diesem Tutorial muss Ihre Anwendung Aufrufe an den Dienst durchführen. Dies erfolgt über das Abonnement "Key" Ihres dienstanzdienstanz. Auf der Seite " *Schnellstart* " Ihres *Gesichtserkennungs-API* dienstanens ist der erste Punkt Nummer 1, um *Ihre Schlüssel zu erfassen.*

10. Wählen Sie auf der Seite *Dienst* entweder den Hyperlink Blue **Keys** (wenn auf der Seite Schnellstart) oder den Link **Schlüssel** im Navigationsmenü Dienste (auf der linken Seite, gekennzeichnet durch das Symbol "Schlüssel") aus, um Ihre Schlüssel anzuzeigen.

    > [!NOTE] 
    > Notieren Sie sich entweder einen der Schlüssel, und schützen Sie ihn, da Sie ihn später benötigen.

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>Kapitel 2: Verwenden der UWP-Anwendung "Person Maker"

Stellen Sie sicher, dass Sie die vorgefertigte UWP-Anwendung namens [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip)herunterladen. Diese APP ist nicht das Endprodukt für diesen Kurs, sondern nur ein Tool, das Sie beim Erstellen Ihrer Azure-Einträge unterstützt, auf die sich das spätere Projekt verlassen wird.

**Person Maker** ermöglicht Ihnen das Erstellen von Azure-Einträgen, die Personen und Personengruppen zugeordnet sind. Die Anwendung platziert alle benötigten Informationen in einem Format, das später von der faceapi verwendet werden kann, um die Gesichter der von Ihnen hinzugefügten Personen zu erkennen. 

> Wichtig **Person Maker** verwendet einige grundlegende Einschränkungen, um sicherzustellen, dass Sie die Anzahl von Dienst aufrufen pro Minute für die **Kostenlose Abonnement Ebene**nicht überschreiten. Der grüne Text oben ändert sich in rot und wird als "aktiv" aktualisiert, wenn eine Drosselung auftritt. Wenn dies der Fall ist, warten Sie einfach auf die Anwendung (es wird gewartet, bis der Zugriff auf den Gesichts Dienst fortgesetzt werden kann, und aktualisieren Sie ihn als "aktiv", wenn Sie ihn wieder verwenden können).

Diese Anwendung verwendet die *Microsoft. projectoxford. Face* -Bibliotheken, die es Ihnen ermöglichen, den Gesichtserkennungs-API vollständig zu nutzen. Diese Bibliothek steht als nuget-Paket kostenlos zur Verfügung. Weitere Informationen zu diesem und ähnlichen APIs [finden Sie im Artikel zur API-Referenz](https://docs.microsoft.com/azure/cognitive-services/face/apireference).

> [!NOTE] 
> Dabei handelt es sich nur um die erforderlichen Schritte. Anweisungen zum Ausführen dieser Schritte finden Sie weiter unten in diesem Dokument. Die **Person Maker** -App ermöglicht Ihnen Folgendes:
>
> - Erstellen Sie eine *Personengruppe*, die aus mehreren Personen besteht, denen Sie zugeordnet werden sollen. Mit Ihrem Azure-Konto können Sie mehrere Personengruppen hosten.
>
> - Erstellen Sie eine *Person*, die Mitglied einer Person-Gruppe ist. Jeder Person sind mehrere *Gesichts* Bilder zugeordnet.
>
> -  Weisen Sie einer *Person* *Gesichtsbilder* zu, damit Ihr Azure Gesichtserkennungs-API-Dienst eine *Person* durch das entsprechende *Gesicht*erkennen kann.
>
> -  *Trainieren* Sie Ihren *Azure Gesichtserkennungs-API-Dienst*.

Wenn Sie diese APP zum Erkennen von Benutzern Schulen möchten, benötigen Sie zehn (10) schließende Fotos für jede Person, die Sie der Person-Gruppe hinzufügen möchten. Die Windows 10-CAM-App kann Sie dabei unterstützen. Sie müssen sicherstellen, dass jedes Foto klar ist (vermeiden Sie die verwierung, verdeckt oder zu weit vom Betreff), dass das Foto im JPG-oder PNG-Dateiformat vorliegt, wobei die Bilddatei nicht größer als **4 MB**und nicht kleiner als **1 KB**ist.

> [!NOTE]
> Wenn Sie dieses Lernprogramm befolgen, sollten Sie sich nicht für das Training mit ihrer eigenen Oberfläche beschäftigen, denn wenn Sie die hololens auf dem Datenblatt platzieren, können Sie sich selbst nicht selbst ansehen. Verwenden Sie die Oberfläche eines Kollegen oder Kollegen.

**Mitarbeiter Hersteller**wird ausgeführt:

1.  Öffnen Sie den Ordner **personmaker** , und doppelklicken Sie auf die Projekt Mappe *personmaker* , um Sie in *Visual Studio*zu öffnen.

2.  Nachdem die *personmaker-Lösung* geöffnet ist, stellen Sie Folgendes sicher:

    1. Die *Projektmappenkonfiguration* ist auf **Debug**festgelegt.

    2. Die *Lösungsplattform* ist auf **x86** festgelegt.

    3. Die *Zielplattform* ist der **lokale Computer**.

    4.  Sie müssen auch *nuget-Pakete wiederherstellen* (Klicken Sie mit der rechten Maustaste auf die Projekt Mappe, und wählen Sie **nuget-Pakete wiederherstellen**).

3.  Klicken Sie auf *lokaler Computer* , und die Anwendung wird gestartet. Beachten Sie, dass auf kleineren Bildschirmen der gesamte Inhalt möglicherweise nicht sichtbar ist, Sie können jedoch einen Bildlauf nach unten durchführen, um ihn anzuzeigen.

    ![Person Maker-Benutzeroberfläche](images/AzureLabs-Lab4-07.png)

4.  Fügen Sie Ihren **Azure-Authentifizierungsschlüssel**, den Sie haben sollten, aus Ihrem *Gesichtserkennungs-API* Service in Azure ein.

5.  Setze

    1. Die *ID* , die Sie der Person- *Gruppe*zuweisen möchten. Die ID muss aus Kleinbuchstaben bestehen und darf keine Leerzeichen enthalten. Notieren Sie sich diese ID, da Sie später in Ihrem Unity-Projekt benötigt wird.
    2. Der *Name* , den Sie der Person- *Gruppe* zuweisen möchten (kann Leerzeichen enthalten).


6.  Klicken Sie auf die Schaltfläche **Personengruppe erstellen** . Unterhalb der Schaltfläche sollte eine Bestätigungsmeldung angezeigt werden.

> [!NOTE]
> Wenn Sie den Fehler "Zugriff verweigert" haben, überprüfen Sie den Speicherort, den Sie für Ihren Azure-Dienst festgelegt haben. Wie bereits erwähnt, ist diese APP für "USA, Westen" konzipiert.

> [!IMPORTANT]
> Sie werden feststellen, dass Sie auch auf die Schaltfläche " **eine bekannte Gruppe abrufen** " klicken können: Dies ist für den Fall, dass Sie bereits eine Person-Gruppe erstellt haben und diese verwenden möchten, anstatt eine neue zu erstellen. Wenn Sie auf *eine Personengruppe* mit einer bekannten Gruppe erstellen klicken, wird auch eine Gruppe abgerufen.

7.  Fügen Sie den *Namen* der *Person* ein, die Sie erstellen möchten.

    1. Klicken Sie auf die Schaltfläche **Person erstellen** .

    2. Unterhalb der Schaltfläche sollte eine Bestätigungsmeldung angezeigt werden.

    3. Wenn Sie eine Person löschen möchten, die Sie zuvor erstellt haben, können Sie den Namen in das Textfeld schreiben und **Person löschen** drücken.

8.  Stellen Sie sicher, dass Sie den Speicherort von zehn (10) Fotos der Person kennen, die Sie der Gruppe hinzufügen möchten.

9.  Klicken Sie auf **Ordner erstellen und öffnen** , um Windows-Explorer in dem Ordner zu öffnen, der der Person zugeordnet ist. Fügen Sie die zehn (10) Images im Ordner hinzu. Diese müssen ein *JPG* -oder *PNG* -Dateiformat aufweisen.

10. Klicken Sie auf über **Mitteln an Azure**. Ein Gegenstand zeigt den Status der Übermittlung an, gefolgt von einer Meldung, wenn Sie abgeschlossen wurde.

11. Nachdem der Leistungs Dienst abgeschlossen und eine Bestätigungsmeldung angezeigt wurde, klicken Sie auf " **trainieren** ", um den Dienst zu trainieren.

Nachdem der Prozess abgeschlossen wurde, können Sie in Unity wechseln.

## <a name="chapter-3---set-up-the-unity-project"></a>Kapitel 3: Einrichten des Unity-Projekts

Folgendes ist eine typische Einrichtung für die Entwicklung mit gemischter Realität und ist daher eine gute Vorlage für andere Projekte.

1.  Öffnen Sie *Unity* , und klicken Sie auf **neu**. 

    ![Starten Sie ein neues Unity-Projekt.](images/AzureLabs-Lab4-08.png)

2.  Sie müssen nun einen Unity-Projektnamen angeben. Fügen Sie **MR_FaceRecognition**ein. Stellen Sie sicher, dass Projekttyp auf **3D**festgelegt ist. Legen Sie den Speicherort auf einen geeigneten **Speicherort** fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind). Klicken Sie dann auf **Projekt erstellen**.

    ![Geben Sie Details für ein neues Unity-Projekt an.](images/AzureLabs-Lab4-09.png)

3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist. Wechseln Sie zu **Edit > Preferences (Einstellungen bearbeiten** ), und navigieren Sie dann im neuen Fenster zu **externe Tools**. Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**. Schließen Sie das Fenster " **Einstellungen** ".

    ![Skript-Editor-Einstellung aktualisieren.](images/AzureLabs-Lab4-10.png)

4.  Navigieren Sie als nächstes zu **Datei > Buildeinstellungen** , und schalten Sie die Plattform auf **universelle Windows-Plattform**, indem Sie auf die Schaltfläche **Plattform wechseln** klicken.

    ![Fenster "Buildeinstellungen", Plattform zu UWP wechseln.](images/AzureLabs-Lab4-11.png)

5.  Wechseln Sie zu **Datei > Build-Einstellungen** , und stellen Sie Folgendes sicher:

    1. **Zielgerät** ist auf **hololens** festgelegt

        > Legen Sie für die immersiven Headsets das **Zielgerät** auf *ein beliebiges Gerät*fest.

    2. Der **Buildtyp** ist auf **D3D** festgelegt.
    3. **SDK** ist auf **neueste installierte** Version festgelegt.
    4. **Visual Studio-Version** ist auf **neueste installierte** Version festgelegt.
    5. **Build und Run** sind auf **lokaler Computer** festgelegt.
    6. Speichern Sie die Szene, und fügen Sie Sie dem Build hinzu. 

        1. Wählen Sie hierzu die Option **geöffnete Szenen hinzufügen**aus. Ein Fenster zum Speichern wird angezeigt.

            ![Klicken Sie auf Schaltfläche "Open Szenen](images/AzureLabs-Lab4-12.png)

        2. Wählen Sie die Schaltfläche **neuer Ordner** aus, um einen neuen Ordner zu erstellen, und nennen Sie ihn **Szenen**.

            ![Neuen Ordner "Skripts" erstellen](images/AzureLabs-Lab4-13.png)

        3. Öffnen Sie den neu erstellten Ordner **Szenen** , und geben Sie dann im Feld **Dateiname**: Text die Zeichen **Fläche fakerecscene**ein, und klicken Sie dann auf **Speichern**.

            ![Benennen Sie neue Szene.](images/AzureLabs-Lab4-14.png)

    7. Die restlichen Einstellungen in den *Buildeinstellungen*sollten vorerst als Standard belassen werden.

6. Klicken Sie im Fenster *Buildeinstellungen* auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der *Inspektor* befindet. 

    ![Öffnen Sie die Player-Einstellungen.](images/AzureLabs-Lab4-15.png)

7. In diesem Bereich müssen einige Einstellungen überprüft werden:

    1. Auf der Registerkarte **andere Einstellungen** :

        1. Die **Skript** **Lauf Zeit Version** sollte **experimentell** sein (.NET 4,6-Entsprechung). Wenn Sie diese Änderung ändern, muss der Editor neu gestartet werden.
        2. **Skript** -Back-End sollte **.net** sein
        3. **API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten

            ![Aktualisieren Sie andere Einstellungen.](images/AzureLabs-Lab4-16.png)
      
    2. Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:

        - **Internet Client deklarieren**
        - **Webcam**

            ![Veröffentlichungs Einstellungen werden aktualisiert.](images/AzureLabs-Lab4-17.png)

    3. Weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), **unterstützt Tick Virtual Reality**, stellen Sie sicher, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.

        ![Aktualisieren Sie die X R-Einstellungen.](images/AzureLabs-Lab4-18.png)

8.  Wieder in den *Buildeinstellungen*ist **Unity C# -Projekte** nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen neben this. 
9.  Schließen Sie das Fenster mit den Buildeinstellungen.
10. Speichern Sie Ihre Szene und Ihr Projekt (**Datei > Speichern Sie Szenen/Dateien > Speichern**Sie das Projekt).

## <a name="chapter-4---main-camera-setup"></a>Kapitel 4: Einrichtung der Hauptkamera

> [!IMPORTANT]
> Wenn Sie die *Unity-Setup* Komponente dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie [dieses. unitypackage herunterladen](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)und als [benutzerdefiniertes Paket](https://docs.unity3d.com/Manual/AssetPackages.html)in das Projekt importieren. Beachten Sie, dass dieses Paket auch den Import der *newtonsoft-dll*enthält, die in [Kapitel 5](#chapter-5--import-the-newtonsoftjson-library)beschrieben wird. Mit diesem importierten Vorgang können Sie in [Kapitel 6](#chapter-6---create-the-faceanalysis-class)fortfahren.

1.  Wählen Sie im Bereich *Hierarchie* die **Hauptkamera**aus.

2.  Nachdem Sie diese Option ausgewählt haben, können Sie alle Komponenten der **Hauptkamera** im *Inspektor-Panel*sehen.

    1. Das **Kamera Objekt** muss als **Hauptkamera** benannt werden (Beachten Sie die Schreibweise).

    2. Das Hauptkamera **Kennzeichen** muss auf **maincamera** festgelegt sein (Beachten Sie die Schreibweise).

    3. Stellen Sie sicher, dass die **Transformations Position** auf **0, 0, 0** festgelegt ist.

    4. **Klartext** auf voll **Tonfarbe** festlegen

    5. Legen Sie die **Hintergrund** Farbe der Kamera Komponente auf **schwarz, Alpha 0 (Hexadezimal Code: #00000000)** fest.

        ![Einrichten von Kamerakomponenten](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>Kapitel 5 – Importieren der newtonsoft. JSON-Bibliothek

> [!IMPORTANT]
> Wenn Sie das ". unitypackage" im [letzten Kapitel](#chapter-4---main-camera-setup)importiert haben, können Sie dieses Kapitel überspringen.

Zum Deserialisieren und Serialisieren von Objekten, die empfangen und an den bot-Dienst gesendet werden, müssen Sie die *newtonsoft. JSON* -Bibliothek herunterladen. Sie werden feststellen, dass eine kompatible Version bereits mit der richtigen Unity-Ordnerstruktur in dieser [Unity-Paketdatei](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage)organisiert ist. 

So importieren Sie die Bibliothek:

1.  Laden Sie das Unity-Paket herunter.
2.  Klicken Sie auf **Assets**, **Import Package**, **Custom Package**.

    ![Importieren der Bibliothek "newtonsoft. JSON"](images/AzureLabs-Lab4-20.png)

3.  Suchen Sie nach dem Paket Unity, das Sie heruntergeladen haben, und klicken Sie auf Öffnen.
4.  Stellen Sie sicher, dass alle Komponenten des Pakets getickt sind, und klicken Sie auf **importieren**.

    ![Importieren der Bibliothek "newtonsoft. JSON"](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>Kapitel 6: Erstellen der faceanalysis-Klasse

Der Zweck der faceanalysis-Klasse besteht darin, die Methoden zu hosten, die für die Kommunikation mit Ihrem Azure-Gesichts Erkennungsdienst erforderlich sind. 

- Nachdem der Dienst ein Erfassungs Abbild gesendet hat, wird es analysiert und die Gesichter innerhalb von identifiziert, und es wird bestimmt, ob eine beliebige zu einer bekannten Person gehört. 
- Wenn eine bekannte Person gefunden wird, wird der Name dieser Klasse in der Szene als Benutzeroberflächen Text angezeigt.

So erstellen Sie die *faceanalysis* -Klasse:

 1. Klicken Sie im Projekt Panel mit der rechten Maustaste in den *Ordner Objekte* , und klicken Sie dann auf > **Ordner** **Erstellen** . Nennen Sie die Ordner **Skripts**. 

    ![Erstellen Sie die faceanalysis-Klasse.](images/AzureLabs-Lab4-22.png)

2.  Doppelklicken Sie auf den soeben erstellten Ordner, um ihn zu öffnen. 
3.  Klicken Sie mit der rechten Maustaste in den Ordner, und klicken Sie dann auf >  **C# Skript** **Erstellen** . Nennen Sie das Skript *faceanalysis*. 
4.  Doppelklicken Sie auf das neue *faceanalysis* -Skript, um es mit Visual Studio 2017 zu öffnen.
5.  Geben Sie die folgenden Namespaces oberhalb der *faceanalysis* -Klasse ein:

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  Nun müssen Sie alle-Objekte hinzufügen, die für die Deserialisierung verwendet werden. Diese Objekte müssen **außerhalb** des *faceanalysis* -Skripts hinzugefügt werden (unterhalb der unteren geschweiften Klammer). 

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
7. Die Methoden " *Start ()* " und " *Update ()* " werden nicht verwendet. löschen Sie Sie jetzt. 

8.  Fügen Sie in der *faceanalysis* -Klasse die folgenden Variablen hinzu:

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
    > Ersetzen Sie den **Schlüssel** und die **persongroupid** durch ihren Dienst Schlüssel und die ID der Gruppe, die Sie zuvor erstellt haben.

9.  Fügen Sie die *Awa()* -Methode hinzu, die die-Klasse initialisiert, indem Sie der Hauptkamera die *imagecapture* -Klasse hinzufügen und die Erstellungs Methode der Bezeichnung aufrufen:

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

10. Fügen Sie die Methode " *kreatelabel ()* " hinzu, die das *Label* -Objekt erstellt, um das Analyseergebnis anzuzeigen:

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

11. Fügen Sie die *erkenctfacesfromimage ()* -und die *getimageasbytearray ()* -Methode hinzu. Der erste fordert den Gesichts Erkennungsdienst auf, um alle möglichen Gesichter im übermittelten Abbild zu erkennen, während Letzteres erforderlich ist, um das erfasste Bild in ein Bytearray zu konvertieren:

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

12. Fügen Sie die *identifyfaces ()* -Methode hinzu, die den *Gesichts Erkennungsdienst* anfordert, alle bekannten Gesichter zu identifizieren, die zuvor im übermittelten Bild erkannt wurden. Von der Anforderung wird eine ID der identifizierten Person, jedoch nicht der Name zurückgegeben:

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

            // Serialize to Json format
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

13. Fügen Sie die *GetPerson ()* -Methode hinzu. Durch die Angabe der Person-ID fordert diese Methode dann an, dass der *Gesichts Erkennungsdienst* den Namen der identifizierten Person zurückgibt:

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

14.  Vergessen Sie nicht, die Änderungen zu **Speichern** , bevor Sie zum Unity-Editor zurückkehren.
15.  Ziehen Sie im Unity-Editor das faceanalysis-Skript aus dem Ordner Scripts im Projekt Panel auf das Hauptkamera Objekt im *Hierarchie Panel*. Die neue Skript Komponente wird der Hauptkamera so hinzugefügt. 

![Legen Sie faceanalysis auf der Hauptkamera ab.](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>Kapitel 7: Erstellen der imagecapture-Klasse

Der Zweck der *imagecapture* -Klasse besteht darin, die Methoden zu hosten, die für die Kommunikation mit Ihrem *Azure-Gesichts Erkennungsdienst* erforderlich sind, um das Abbild zu analysieren, das Sie erfassen möchten, und zu ermitteln, ob es zu einer bekannten Person gehört. Wenn eine bekannte Person gefunden wird, wird der Name dieser Klasse in der Szene als Benutzeroberflächen Text angezeigt.

So erstellen Sie die *imagecapture* -Klasse:
 
1.  Klicken Sie **mit der rechten** Maustaste in den Skript Ordner, den Sie zuvor erstellt haben, und klicken Sie dann auf **Erstellen**,  **C# Skript**. Nennen Sie das Skript *imagecapture*. 
2.  Doppelklicken Sie auf das neue *imagecapture* -Skript, um es mit Visual Studio 2017 zu öffnen.
3.  Geben Sie die folgenden Namespaces oberhalb der imagecapture-Klasse ein:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  Fügen Sie in der *imagecapture* -Klasse die folgenden Variablen hinzu:

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

5.  Fügen Sie die " *Awake ()* "-und " *Start ()* "-Methoden hinzu, die erforderlich sind, um die Klasse zu initialisieren, und die hololens die Gesten des Benutzers

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

6.  Fügen Sie den " *taphandler ()* " hinzu, der aufgerufen wird, wenn der Benutzer eine *Tap* -Geste ausführt:

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

7.  Fügen Sie die *executeimagecaptureandanalysis ()* -Methode hinzu, die den Prozess der Bild Erfassung startet:

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

8.  Fügen Sie die Handler hinzu, die aufgerufen werden, wenn der Foto Erfassungsprozess abgeschlossen wurde:

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. Vergessen Sie nicht, die Änderungen zu **Speichern** , bevor Sie zum Unity-Editor zurückkehren.

## <a name="chapter-8---building-the-solution"></a>Kapitel 8: aufbauen der Lösung

Um eine gründliche Test Ihrer Anwendung durchzuführen, müssen Sie Sie auf Ihre hololens querladen.

Bevor Sie vorgehen, stellen Sie Folgendes sicher:

-   Alle im Kapitel 3 erwähnten Einstellungen sind richtig festgelegt. 
-   Die Skript- *faceanalysis* ist an das Hauptkamera Objekt angefügt. 
-   Der Authentifizierungs **Schlüssel** und die **Gruppen-ID** wurden innerhalb des *faceanalysis* -Skripts festgelegt.

A: an dieser Stelle können Sie die Projekt Mappe erstellen. Nachdem die Lösung erstellt wurde, können Sie Ihre Anwendung bereitstellen.

So beginnen Sie den Buildprozess:

1.  Speichern Sie die aktuelle Szene, indem Sie auf Datei und dann auf Speichern klicken.
2.  Wechseln Sie zu Datei, Buildeinstellungen, und klicken Sie auf offene Szenen hinzufügen.
3.  Stellen Sie sicher, dass C# Sie Unity-Projekte teilnehmen.

    ![Stellen Sie die Lösung aus Visual Studio bereit.](images/AzureLabs-Lab4-24.png)

4.  Klicken Sie auf erstellen. Auf diese Weise startet Unity ein Datei-Explorer-Fenster, in dem Sie einen Ordner erstellen und auswählen müssen, in dem die App erstellt wird. Erstellen Sie diesen Ordner jetzt innerhalb des Unity-Projekts, und rufen Sie ihn App auf. Klicken Sie dann mit ausgewähltem app-Ordner auf Ordner auswählen. 
5.  Unity erstellt das Projekt in den app-Ordner. 
6.  Nachdem die Erstellung von Unity abgeschlossen ist (Dies kann einige Zeit in Anspruch nehmen), wird ein Datei-Explorer-Fenster am Speicherort des Builds geöffnet.

    ![Stellen Sie die Lösung aus Visual Studio bereit.](images/AzureLabs-Lab4-25.png)

7.  Öffnen Sie den app-Ordner, und öffnen Sie dann die neue Projekt Mappe (wie oben gezeigt, MR_FaceRecognition. sln).


## <a name="chapter-9---deploying-your-application"></a>Kapitel 9: Bereitstellen der Anwendung

So stellen Sie auf hololens bereit:

1.  Sie benötigen die IP-Adresse Ihrer hololens (für die Remote Bereitstellung) und, um sicherzustellen, dass sich Ihre hololens im **Entwicklermodus**befinden. Gehen Sie dazu wie folgt vor:

    1. Öffnen Sie die Einstellungen, während Sie die hololens- **Einstellungen**durch tragen.
    2. Navigieren Sie zu **Netzwerk & Internet > Wi-Fi > Erweiterte Optionen**
    3. Notieren Sie sich die **IPv4** -Adresse.
    4. Navigieren Sie als nächstes wieder zu **Einstellungen**, und aktualisieren Sie dann **& Sicherheits > für Entwickler** . 
    5. Legen Sie den Entwicklermodus auf fest.

2.  Navigieren Sie zu Ihrem neuen Unity-Build ( *App* -Ordner), und öffnen Sie die Projektmappendatei mit *Visual Studio*.
3.  Wählen Sie in der Projektmappenkonfiguration **Debuggen**.
4.  Wählen Sie auf der Projektmappenplattform die Option **x86**, **Remote Computer**aus. 

    ![Stellen Sie die Lösung aus Visual Studio bereit.](images/AzureLabs-Lab4-26.png)
 
5.  Wechseln Sie zum **Menü Erstellen** , und klicken Sie auf **Lösung**bereitstellen, um die Anwendung auf die hololens quer zuladen.
6.  Ihre APP sollte nun in der Liste der installierten apps auf Ihren hololens angezeigt werden, die bereit sind, gestartet zu werden.

> [!NOTE]
> Legen Sie für die Bereitstellung auf dem immersiven Headset die Projektmappenplattform auf *lokaler Computer*fest, und legen Sie die **Konfiguration** auf *Debuggen*und *x86* als **Plattform**fest. Stellen Sie dann auf dem lokalen Computer bereit, indem Sie im **Menü Erstellen**die Option *Lösung*bereitstellen auswählen. 


## <a name="chapter-10---using-the-application"></a>Kapitel 10: Verwenden der Anwendung

1.  Wenn Sie die hololens ausführen, starten Sie die app.
2.  Sehen Sie sich die Person an, die Sie beim *Gesichtserkennungs-API*registriert haben. Stellen Sie Folgendes sicher:

    -  Das Gesicht der Person ist nicht zu weit und klar sichtbar.
    -  Die Umgebungsbeleuchtung ist nicht zu dunkel.

3.  Verwenden Sie die Tap-Geste, um das Bild der Person zu erfassen.
4.  Warten Sie, bis die APP die Analyse Anforderung sendet und eine Antwort erhält.
5.  Wenn die Person erfolgreich erkannt wurde, wird der Name der Person als Benutzeroberflächen Text angezeigt.
6.  Sie können den Aufzeichnungsprozess mit der TAP-Geste alle paar Sekunden wiederholen.

## <a name="your-finished-azure-face-api-application"></a>Ihre fertiggestellte Azure Gesichtserkennungs-API-Anwendung

Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die den Azure-Gesichts Erkennungsdienst nutzt, um Gesichter innerhalb eines Bilds zu erkennen und bekannte Gesichter zu identifizieren.

![Ergebnis der Fertigstellung dieses Kurses](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>Bonus Übungen

### <a name="exercise-1"></a>Übung 1

Der **Azure-Gesichtserkennungs-API** ist leistungsfähig genug, um bis zu 64 Gesichter in einem einzelnen Image zu erkennen. Erweitern Sie die Anwendung so, dass Sie unter vielen anderen Personen zwei oder drei Gesichter erkennen kann.

### <a name="exercise-2"></a>Übung 2

Der **Azure-Gesichtserkennungs-API** kann auch alle Arten von Attributinformationen zurückgeben. Integrieren Sie diese in die Anwendung. Dies könnte noch interessanter sein, wenn Sie mit dem [Emotionen-API](https://azure.microsoft.com/services/cognitive-services/emotion/)kombiniert werden.
