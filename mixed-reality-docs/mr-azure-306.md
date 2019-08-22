---
title: Mr-und Azure 306-Streaming-Video
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie Azure Media Services in einer Mixed Reality-Anwendung implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Media Services, Streaming-Video, 360, immersive, VR
ms.openlocfilehash: e27bda2a9309f335feb0056703da492555c39fde
ms.sourcegitcommit: c4d0132ea755c861c504dad46957e791b9c705d5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2019
ms.locfileid: "69896587"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.

<br> 

# <a name="mr-and-azure-306-streaming-video"></a>Mr und Azure 306: Streaming-Video

![Endgültiges Produkt-Start](images/AzureLabs-Lab6-00.png)
![Final Product-Start](images/AzureLabs-Lab6-01.png)

In diesem Kurs erfahren Sie, wie Sie Ihre Azure Media Services mit einer Windows Mixed Reality-VR-Benutzer Verbindung verbinden, um das Streaming von 360-Grad-Videowiedergabe auf immersiven Headsets zuzulassen. 

Bei **Azure Media Services** handelt es sich um eine Sammlung von Diensten, die Ihnen Broadcast-Quality-Videostreamingdienste zur Erreichung größerer Zielgruppen auf den heute beliebtesten mobilen Geräten bietet. Weitere Informationen finden Sie auf der [Seite Azure Media Services](https://azure.microsoft.com/services/media-services).

Nachdem Sie diesen Kurs abgeschlossen haben, verfügen Sie über eine gemischte Reality-Headset-Anwendung, mit der Sie die folgenden Aktionen ausführen können:

1. Abrufen eines 360-Grad-Videos aus einer **Azure Storage**über den **Azure Media Service**.

2. Anzeigen des abgerufenen 360-Grad-Videos in einer Unity-Szene.

3. Navigieren Sie zwischen zwei Kulissen mit zwei verschiedenen Videos.

In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren. In diesem Kurs erfahren Sie, wie Sie einen Azure-Dienst in Ihr Unity-Projekt integrieren. Es ist Ihre Aufgabe, das wissen, das Sie aus diesem Kursgewinnen, zu nutzen, um ihre gemischte Reality-Anwendung zu verbessern.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> Mr und Azure 306: Streaming-Video</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Erforderliche Komponenten

> [!NOTE]
> Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen. Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Mai 2018). Sie können die neueste Software verwenden, die im [Artikel Installieren der Tools](install-the-tools.md)aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt sind.

Für diesen Kurs empfehlen wir die folgende Hardware und Software:

- Einen Entwicklungs-PC, der [mit der Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for Immersive (VR)-Headset-Entwicklung kompatibel ist
- [Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus](install-the-tools.md#installation-checklist)
- [Das neueste Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Ein [Windows Mixed Reality-Headset (VR)](immersive-headset-hardware-details.md)
- Internet Zugriff für Azure-Setup und Datenabruf
- 2 360-Grad-Videos im MP4-Format ( [auf dieser Downloadseite](https://www.mettle.com/360vr-master-series-free-360-downloads-page)finden Sie einige gebührenfreie Videos)

## <a name="before-you-start"></a>Bevor Sie beginnen

1.  Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).
2.  Richten Sie Ihr immersives Headset mit gemischter Realität ein und testen Sie es.

    > [!NOTE]
    > Für diesen Kurs benötigen Sie **keine** Bewegungs Controller. Wenn Sie Unterstützung beim Einrichten des immersiven Headsets benötigen, klicken Sie [auf verknüpfen, um Windows Mixed Reality einzurichten](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a>Kapitel 1: Azure-Portal: Erstellen des Azure Storage Kontos

Um den **Azure Storage-Dienst**zu verwenden, müssen Sie ein **Speicherkonto** in der Azure-Portal erstellen und konfigurieren.

1.  Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

    > [!NOTE]
    > Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen. Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.

2.  Wenn Sie angemeldet sind, klicken Sie im linken Menü auf **Speicher Konten** .

    ![Einrichten des Azure Storage Kontos](images/AzureLabs-Lab6-02.png)

3.  Klicken Sie auf der Registerkarte **Speicher Konten** auf **Hinzufügen**.

    ![Einrichten des Azure Storage Kontos](images/AzureLabs-Lab6-03.png)

4.  Auf der Registerkarte **Speicherkonto erstellen** :

    1.  Fügen Sie einen **Namen** für Ihr Konto ein. Beachten Sie, dass dieses Feld nur Zahlen und Kleinbuchstaben akzeptiert.

    2.  Wählen Sie **unter Bereitstellungs Modell** die Option **Resource Manager**aus.

    3.  Wählen Sie unter **Kontoart**die Option **Speicher (universell, Version v1)** aus.

    4.  Für **Leistung**Option **Standard*.**

    5.  Wählen Sie für **Replikation** die Option **lokal redundanter Speicher (LRS)** aus.

    6.  Lassen Sie die Option " **sichere Übertragung erforderlich** " **deaktiviert**.

    7.  Wählen Sie ein **Abonnement**aus.

    8.  Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** . Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.

    9.  Bestimmen Sie den **Speicherort** für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen). Der Speicherort wäre idealerweise in der Region, in der die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.

5.  Sie müssen bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.

    ![Einrichten des Azure Storage Kontos](images/AzureLabs-Lab6-04.png)

6.  Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.

7.  Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Einrichten des Azure Storage Kontos](images/AzureLabs-Lab6-05.png)

8.  An diesem Punkt müssen Sie die Ressource nicht befolgen, sondern einfach zum nächsten Kapitel wechseln.

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a>Kapitel 2: Azure-Portal: Erstellen des Medien Dienstanbieter

Zum Verwenden von Azure Media Service müssen Sie eine Instanz des Dienstanbieter konfigurieren, die für die Anwendung verfügbar gemacht wird (wobei der Kontoinhaber ein Administrator sein muss).

1.  Klicken Sie im Azure-Portal in der oberen linken Ecke auf **Ressource erstellen** , und suchen Sie nach **Media Service,** und drücken **Sie die Eingabe**Taste. Die gewünschte Ressource hat zurzeit ein rosa Symbol. Klicken Sie hierauf, um eine neue Seite anzuzeigen.

    ![Das Azure-Portal](images/AzureLabs-Lab6-06.png)

2.  Auf der neuen Seite wird eine Beschreibung des **Medien Dienstanbieter**bereitgestellt. Klicken Sie unten links in dieser Eingabeaufforderung auf die Schaltfläche **Erstellen** , um eine Verknüpfung mit diesem Dienst zu erstellen.

    ![Das Azure-Portal](images/AzureLabs-Lab6-07.png)

3.  Nachdem Sie auf **Erstellen** geklickt haben, wird ein Panel angezeigt, in dem Sie einige Details über den neuen Mediendienst angeben müssen:

    1.  Fügen Sie den gewünschten **Kontonamen** für diese Dienst Instanz ein.

    2.  Wählen Sie ein **Abonnement**aus.

    3. Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** . Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Labs) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern. 
    
    > Weitere Informationen zu Azure-Ressourcengruppen finden Sie unter diesem [Link zum Verwalten von Azure-Ressourcengruppen](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Bestimmen Sie den **Speicherort** für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen). Der Speicherort wäre idealerweise in der Region, in der die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.

    5.  Klicken Sie im Abschnitt **Speicherkonto** auf den Abschnitt **auswählen...** , und klicken Sie dann auf das **Speicherkonto** , das Sie im letzten Kapitel erstellt haben.

    6.  Außerdem müssen Sie bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.

    7.  Klicken Sie auf **Erstellen**.

        ![Das Azure-Portal](images/AzureLabs-Lab6-08.png)

4.  Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.

5.  Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Das Azure-Portal](images/AzureLabs-Lab6-09.png)

6.  Klicken Sie auf die Benachrichtigung, um die neue Dienst Instanz zu untersuchen.

    ![Das Azure-Portal](images/AzureLabs-Lab6-10.png)

7.  Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen.

8.  Klicken Sie auf der Seite neuer Mediendienst im linken Bereich auf den Link **Assets** , der ungefähr in der Mitte liegt.

9.  Klicken Sie auf der nächsten Seite in der oberen linken Ecke der Seite auf **hochladen**.

    ![Das Azure-Portal](images/AzureLabs-Lab6-11.png)

10. Klicken Sie auf das **Ordner** Symbol, um die Dateien zu durchsuchen, und wählen Sie das erste 360-Video aus, das Sie streamen möchten. 
    
    > Sie können diesem [Link folgen, um ein Beispiel Video herunterzuladen](https://vimeo.com/214401712).

    ![Das Azure-Portal](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> Lange Dateinamen können ein Problem mit dem Encoder verursachen: um sicherzustellen, dass Videos keine Probleme haben, sollten Sie die Länge der Video Dateinamen verkürzen.

11. Wenn der Upload des Videos abgeschlossen ist, wird die Statusleiste grün.

    ![Das Azure-Portal](images/AzureLabs-Lab6-13.png)

12. Klicken Sie auf den obigen Text (**yourservicename-Assets**), um zur Seite **Assets** zurückzukehren.

13. Sie werden feststellen, dass Ihr Video erfolgreich hochgeladen wurde. Klicken Sie darauf.

    ![Das Azure-Portal](images/AzureLabs-Lab6-14.png)

14. Auf der Seite, zu der Sie umgeleitet werden, werden ausführliche Informationen zu Ihrem Video angezeigt. Um Ihr Video verwenden zu können, müssen Sie es codieren, indem Sie auf die Schaltfläche **Codieren** oben links auf der Seite klicken.

    ![Das Azure-Portal](images/AzureLabs-Lab6-15.png)

15. Auf der rechten Seite wird ein neuer Bereich angezeigt, in dem Sie Codierungsoptionen für die Datei festlegen können. Legen Sie die folgenden Eigenschaften fest (einige werden bereits standardmäßig festgelegt):

    1.  **Media Encoder-Name *Media Encoder Standard***

    2.  **Codierungs voreingestellten *Inhalt Adaptive Multi-Bitrate-MP4***

    3.  **Auftrags Name *Media Encoder Standard Verarbeitung von video1. MP4***

    4.  **Ausgabemedien Medienobjekt Name *video1. MP4--Media Encoder Standard codiert***

        ![Das Azure-Portal](images/AzureLabs-Lab6-16.png)

16. Klicken Sie auf die Schaltfläche **Erstellen**.

17. Sie werden feststellen, dass ein Balken mit dem **hinzugefügten Codierungs Auftrag hinzugefügt**wurde. Klicken Sie auf diese Leiste, und ein Panel mit dem darin angezeigten Codierungs Fortschritt

    ![Das Azure-Portal](images/AzureLabs-Lab6-17.png)

    ![Das Azure-Portal](images/AzureLabs-Lab6-18.png)

18. Warten Sie, bis der Auftrag abgeschlossen ist. Nachdem der Vorgang abgeschlossen ist, können Sie den Bereich mit dem "X" oben rechts in diesem Panel schließen.

    ![Das Azure-Portal](images/AzureLabs-Lab6-19.png)

    ![Das Azure-Portal](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > Die Zeit, die dies dauert, hängt von der Dateigröße Ihres Videos ab. Dieser Vorgang kann einige Zeit in Anspruch nehmen.

19. Nachdem Sie nun die codierte Version des Videos erstellt haben, können Sie Sie veröffentlichen, um Sie zugänglich zu machen. Klicken Sie hierzu auf die blauen linkassets , um zur Seite Assets zurückzukehren.

    ![Das Azure-Portal](images/AzureLabs-Lab6-21.png)

20. Ihr Video wird zusammen mit einem anderen angezeigt, d. h. vom **Ressourcentyp mit _Multi-Bitrate-MP4_** .

    ![Das Azure-Portal](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > Sie werden feststellen, dass das neue Medienobjekt neben dem ersten Video *unbekannt*ist und für seine **Größe**0 Bytes aufweist. aktualisieren Sie einfach das Fenster, um es zu aktualisieren.

21. Klicken Sie auf dieses neue Asset.

    ![Das Azure-Portal](images/AzureLabs-Lab6-23.png)

22. Es wird ein ähnlicher Bereich angezeigt, den Sie zuvor verwendet haben, nur dies ist ein anderes Asset. Klicken Sie in der oberen Mitte der Seite auf die Schaltfläche **veröffentlichen** .

    ![Das Azure-Portal](images/AzureLabs-Lab6-24.png)

23. Sie werden aufgefordert, einen **Locator**(den Einstiegspunkt) auf Datei/s in ihren Assets festzulegen. Legen Sie für Ihr Szenario die folgenden Eigenschaften fest:

    1.  **Locatortyp** > **progressiv**.

    2.  Das **Datum** und die **Uhrzeit** werden von Ihrem aktuellen Datum auf eine Uhrzeit in der Zukunft (in diesem Fall 100 Jahre) festgelegt. Lassen Sie den Wert unverändert, oder ändern Sie ihn entsprechend.

    > [!NOTE]
    > Weitere Informationen zu Locators und den Optionen, die Sie auswählen können, finden Sie in der [Azure Media Services-Dokumentation](https://docs.microsoft.com/azure/media-services/media-services-concepts).

24. Klicken Sie unten in diesem Bereich auf die Schaltfläche **Hinzufügen** .

    ![Das Azure-Portal](images/AzureLabs-Lab6-25.png)

25. Ihr Video ist nun veröffentlicht und kann über seinen Endpunkt gestreamt werden. Im weiteren Verlauf der Seite befindet sich ein Abschnitt " **Dateien** ". An dieser Stelle werden die unterschiedlichen codierten Versionen Ihres Videos verwendet. Wählen Sie die höchstmögliche Auflösung aus (in der folgenden Abbildung ist die Datei 1920 x960), und dann wird ein Bereich rechts angezeigt. Dort finden Sie eine **Download-URL**. Kopieren Sie diesen **Endpunkt** , da Sie ihn später in Ihrem Code verwenden werden.

    ![Das Azure-Portal](images/AzureLabs-Lab6-26.png)    

    ![Das Azure-Portal](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > Sie können auch auf die **Wiedergabe** Schaltfläche klicken, um Ihr Video wiederzugeben und zu testen.

26. Sie müssen nun das zweite Video hochladen, das Sie in diesem Lab verwenden werden. Führen Sie die oben beschriebenen Schritte aus, und wiederholen Sie den Vorgang für das zweite Video. Stellen Sie sicher, dass Sie auch den zweiten **Endpunkt** kopieren. Verwenden Sie den folgenden [Link, um ein zweites Video herunterzuladen](https://vimeo.com/214402865).

27. Nachdem beide Videos veröffentlicht wurden, können Sie mit dem nächsten Kapitel fortfahren.

## <a name="chapter-3---setting-up-the-unity-project"></a>Kapitel 3: Einrichten des Unity-Projekts

Im folgenden finden Sie eine typische Einrichtung für die Entwicklung mit gemischter Realität und eine gute Vorlage für andere Projekte.

1.  Öffnen Sie **Unity** , und klicken Sie auf **neu**. 

    ![Das Azure-Portal](images/AzureLabs-Lab6-28.png)

2.  Sie müssen nun einen Unity-Projektnamen angeben und **Mr\_-360videostreaming einfügen.** Stellen Sie sicher, dass Projekttyp auf **3D**festgelegt ist. Legen Sie den Speicherort auf einen geeigneten Speicherort fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind). Klicken Sie dann auf **Projekt erstellen**.

    ![Das Azure-Portal](images/AzureLabs-Lab6-29.png)

3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio** festgelegt ist. Wechseln Sie zu  ***Einstellungen* bearbeiten** , und navigieren Sie dann im neuen Fenster zu **externe Tools**. Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**. Schließen Sie das Fenster " **Einstellungen** ".

    ![Das Azure-Portal](images/AzureLabs-Lab6-30.png)

4.  Navigieren Sie als nächstes zu ***dateibuildeinstellungen*** , und schalten Sie die Plattform auf **universelle Windows-Plattform**, indem Sie auf die Schaltfläche **Plattform wechseln** klicken.

5.  Stellen Sie außerdem Folgendes sicher:

    1. Das **Zielgerät** ist auf **ein beliebiges Gerät** festgelegt.
    
    2.  Der Buildtyp ist auf D3D festgelegt **.**

    3.  **SDK** ist auf **zuletzt installiert** festgelegt.

    4.  Die **Visual Studio-Version** ist auf die **neueste installierte** Version festgelegt.

    5.  **Build und Run** sind auf **lokaler Computer** festgelegt.

    6.  Machen Sie sich keine Gedanken über das Einrichten von **Szenen** , da Sie diese später festlegen werden.

    7.  Die restlichen Einstellungen sollten vorerst als Standard belassen werden.

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab6-31.png)

6.  Klicken Sie im Fenster Buildeinstellungen auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der **Inspektor** befindet. 

7. In diesem Bereich müssen einige Einstellungen überprüft werden:

    1.  Auf der Registerkarte **andere Einstellungen** :

        1.  **Skript** Erstellung Die **Lauf Zeit Version** muss **stabil** sein (.NET 3,5-Entsprechung).

        2. Das Skript für die **Skript** Erstellung sollte **.net sein.**

        3. Der **API-Kompatibilitäts Grad** sollte **.NET 4,6 lauten.**

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab6-32.png)

    2.  Weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), **unterstützt Tick Virtual Reality**, stellen Sie sicher, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab6-33.png)

    3.  Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:

        - **Internet Client deklarieren**

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab6-34.png)

8.  Nachdem Sie diese Änderungen vorgenommen haben, schließen Sie das Fenster mit den Buildeinstellungen.

9.  Speichern Sie das Projekt **Datei* *speichern Projekt**.



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a>Kapitel 4: Importieren des insideoutsphere Unity-Pakets

> [!IMPORTANT]
> Wenn Sie die *Unity-Setup* Komponente dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie dieses [. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage)herunterladen, es als [**benutzerdefiniertes Paket**](https://docs.unity3d.com/Manual/AssetPackages.html)in Ihr Projekt importieren und dann aus **Kapitel 5**fortfahren. Sie müssen dennoch ein Unity-Projekt erstellen.

Für diesen Kurs müssen Sie ein Unity-Ressourcenpaket mit dem Namen [**insideoutsphere. unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage)herunterladen.

Gewusst wie: Importieren von **vstu**:

1.  Klicken Sie oben auf dem Bildschirm mit dem Unity-Dashboard auf **Assets** , und klicken Sie dann auf **Paket > benutzerdefiniertes Paket importieren**.

    ![Importieren des insideoutsphere Unity-Pakets](images/AzureLabs-Lab6-35.png)

2.  Wählen Sie mit der Dateiauswahl das Paket **insideoutsphere. unitypackage** aus, und klicken Sie auf **Öffnen**. Eine Liste der Komponenten für dieses Asset wird angezeigt. Bestätigen Sie den Import, indem Sie auf **importieren**klicken.

    ![Importieren des insideoutsphere Unity-Pakets](images/AzureLabs-Lab6-36.png)

3.  Nachdem der Import abgeschlossen wurde, bemerken Sie, dass drei neue Ordner, **Materialien**, **Modelle**und **Prefabs**dem Ordner " **Assets** " hinzugefügt wurden. Diese Art von Ordnerstruktur ist typisch für ein Unity-Projekt.

    ![Importieren des insideoutsphere Unity-Pakets](images/AzureLabs-Lab6-37.png)

    1.  Öffnen Sie den Ordner **Modelle** , und Sie sehen, dass das **insienoutsphere** -Modell importiert wurde.

    2.  Im Ordner **Material** finden Sie das Material **insiweoutsphären** *LAMBERT1*zusammen mit einem Material namens *Button Material*, das von der Schaltfläche "Pavillon" verwendet wird, die Sie in Kürze sehen werden.

    3.  Der Ordner " **Prefabs** " enthält das **insienoutsphere** -präfab, das sowohl das **insienoutsphere** - *Modell* als auch das " *gazebutton*" enthält.

    4.  Es **ist kein Code enthalten**. Sie schreiben den Code, indem Sie diesen Kurs befolgen.


4.  Wählen Sie in der **Hierarchie**das **Hauptkamera** Objekt aus, und aktualisieren Sie die folgenden Komponenten:

    1.  **Sin**

        1.  Position = **X**: 0, **Y**: 0, **Z**: 0.

        2. Drehung = **X**: 0, **Y**: 0, **Z**: 0.

        3. Skalieren von **X**: 1, **Y**: 1, **Z**: 1.

    2.  **Kamera**

        1. **Flags löschen**: Voll Tonfarbe.

        2.  **Clipping-Ebenen**: Nahen 0,1, weit entfernt: 6.

            ![Importieren des insideoutsphere Unity-Pakets](images/AzureLabs-Lab6-38.png)

5.  Navigieren Sie zum Ordner " **Prefab** ", und ziehen Sie dann den " **insidebug outsphere** "-Prefab in den Bereich **Hierarchie** .

    ![Importieren des insideoutsphere Unity-Pakets](images/AzureLabs-Lab6-39.png)

6.  Erweitern Sie das **insideoutsphere** -Objekt in der **Hierarchie** , indem Sie auf den kleinen Pfeil daneben klicken. Darunter wird ein unter geordnetes Objekt mit dem Namen " **gazebutton**" angezeigt. Diese wird verwendet, um Szenen und somit Videos zu ändern.

    ![Importieren des insideoutsphere Unity-Pakets](images/AzureLabs-Lab6-40.png)

7.  Klicken Sie im Inspektor-Fenster auf die Transformations Komponente von **insideoutsphere**, und stellen Sie sicher, dass die folgenden Eigenschaften festgelegt sind:

    |            |    TRANSFORMATION-POSITION   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |    TRANSFORMATION-DREHUNG   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** -50        |  **Z** 0  |

    |            |     TRANSFORMIEREN: SKALIEREN     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **J** 1          |  **Z** 1  |

    ![Importieren des insideoutsphere Unity-Pakets](images/AzureLabs-Lab6-41.png)

8.  Klicken Sie auf das untergeordnete **gazebutton** -Objekt, und legen Sie die zugehörige **Transformation** wie folgt fest:

    |            |    TRANSFORMATION-POSITION   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 3,6|          **J** 1,3        |  **Z** 0  |

    |            |    TRANSFORMATION-DREHUNG   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRANSFORMIEREN: SKALIEREN     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **J** 1          |  **Z** 1  |

    ![Importieren des insideoutsphere Unity-Pakets](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a>Kapitel 5: Erstellen der Videocontroller-Klasse

Die **Videocontroller** -Klasse hostet die beiden Video Endpunkte, die zum Streamen der Inhalte aus dem Azure Media Service verwendet werden.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste in den **Ordner Asset**, der sich im **Projekt** Panel befindet, und klicken Sie auf **> Ordner erstellen**. Benennen Sie den Ordner mit **Skripts**.

    ![Erstellen der Videocontroller-Klasse](images/AzureLabs-Lab6-43.png)

    ![Erstellen der Videocontroller-Klasse](images/AzureLabs-Lab6-44.png)

2.  Doppelklicken Sie auf den Ordner " **Scripts** ", um ihn zu öffnen.

3.  Klicken Sie mit der rechten Maustaste in den Ordner, und klicken Sie dann auf **Create > C\# Script**. Benennen Sie das Skript **Videocontroller**.

    ![Erstellen der Videocontroller-Klasse](images/AzureLabs-Lab6-45.png)

4.  Doppelklicken Sie auf das neue **Videocontroller** -Skript, um es mit **Visual Studio 2017** zu öffnen.

    ![Erstellen der Videocontroller-Klasse](images/AzureLabs-Lab6-46.png)

5.  Aktualisieren Sie die Namespaces oben in der Codedatei wie folgt:

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  Geben Sie die folgenden Variablen in der **Videocontroller** -Klasse zusammen mit der **Awa()** -Methode ein:

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  Nun ist die Zeit, die Endpunkte aus ihren Azure Media Service-Videos einzugeben:

    1.  Der erste in die *video1endpoint* -Variable.
    
    2.  Der zweite in die *video2endpoint* -Variable.

    > [!WARNING]
    > Es gibt ein bekanntes Problem bei der Verwendung von *https* in Unity mit der Version 2017.4.1 F1. Wenn die Videos einen Fehler bei der Wiedergabe bereitstellen, versuchen Sie stattdessen, stattdessen "http" zu verwenden.

8.  Als nächstes muss die Methode **Start ()** bearbeitet werden. Diese Methode wird jedes Mal ausgelöst, wenn der Benutzer die Szene wechselt (folglich wird das Video gewechselt), indem er sich die Schaltfläche "Blick" ansieht.

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  Fügen Sie nach der Methode **Start ()** die *IEnumerator* -Methode **playVideo ()** ein, die verwendet wird, um Videos nahtlos zu starten (sodass kein ruckeln sichtbar ist).

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. Die letzte Methode, die Sie für diese Klasse benötigen, ist die **changescene ()** -Methode, die verwendet wird, um zwischen Szenen auszutauschen.

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > Die **changescene ()** -Methode verwendet ein praktisches\# C-Feature, das als *Bedingter Operator*bezeichnet wird. Dies ermöglicht, dass Bedingungen überprüft werden und dann basierend auf dem Ergebnis der Überprüfung zurückgegebene Werte in einer einzigen Anweisung zurückgegeben werden. [Weitere Informationen zum bedingten Operator](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator)finden Sie unter diesem Link.

11. Speichern Sie die Änderungen in Visual Studio, bevor Sie zu Unity zurückkehren.

12. Klicken Sie im Unity-Editor auf die **Videocontroller** -Klasse [from] {. Unterstreichung} der Ordner **Scripts** , und ziehen Sie Sie im **Hierarchie** Panel auf das **Hauptkamera** Objekt.

13. Klicken Sie auf die **Hauptkamera** , und sehen Sie sich den Bereich **Inspector**an. Sie werden feststellen, dass in der neu hinzugefügten Skript Komponente ein Feld mit einem leeren Wert vorhanden ist. Dies ist ein Verweis Feld, das die öffentlichen Variablen in Ihrem Code als Ziel hat.

14. Ziehen Sie das insidebug-Objekt aus dem Bereich **Hierarchie** in den **Sphere** -Slot, wie in der folgenden Abbildung dargestellt.

    ![Erstellen der Videocontroller-](images/AzureLabs-Lab6-47.png)
    Klasse![Erstellen der Videocontroller-Klasse](images/AzureLabs-Lab6-48.png)

## <a name="chapter-6---create-the-gaze-class"></a>Kapitel 6: Erstellen der "Blick"-Klasse

Diese Klasse ist für das Erstellen eines **raycast** verantwortlich, der von der **Hauptkamera**projiziert wird, um zu erkennen, welches Objekt der Benutzer untersucht. In diesem Fall muss der **raycast** ermitteln, ob der Benutzer das **gazebutton** -Objekt in der Szene prüft und ein Verhalten auslöst.

So erstellen Sie diese Klasse:

1.  Wechseln Sie zum Ordner " **Scripts** ", den Sie zuvor erstellt haben.

2.  Mit der rechten Maustaste den **Projekt** Bereich **erstellen* *C\# Script**. Benennen Sie dasSkript mit dem Namen.

3.  Doppelklicken Sie auf das neue ***Blick*** Skript, um es mit **Visual Studio 2017** zu öffnen.

4.  Stellen Sie sicher, dass sich der folgende Namespace oben im Skript befindet, und entfernen Sie alle anderen:

    ```csharp
    using UnityEngine;
    ```

5.  Fügen Sie dann die folgenden Variablen in der " **Blick** "-Klasse hinzu:

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  Der Code für die Methoden " **Awake ()** " und " **Start ()** " muss nun hinzugefügt werden.

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  Fügen Sie den folgenden Code in der **Update ()** -Methode hinzu, um ein raycast zu projizieren und den zieltreffer zu erkennen:

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  Speichern Sie die Änderungen in Visual Studio, bevor Sie zu Unity zurückkehren.

9.  Klicken und ziehen Sie die Klasse " **Blick** " aus dem Ordner Scripts auf das Hauptkamera Objekt im Bereich **Hierarchie** .

## <a name="chapter-7---setup-the-two-unity-scenes"></a>Kapitel 7: Einrichten der beiden Unity-Szenen

In diesem Kapitel wird erläutert, wie Sie die beiden Kulissen einrichten, die jeweils ein Video zum Streamen von Daten erstellen. Sie duplizieren die Szene, die Sie bereits erstellt haben, sodass Sie Sie nicht erneut einrichten müssen, obwohl Sie die neue Szene bearbeiten, sodass sich das *gazebutton* -Objekt an einem anderen Speicherort befindet und über eine andere Darstellung verfügt. Dies soll zeigen, wie Sie zwischen Szenen wechseln können.

1.  Wechseln Sie dazu zu **Datei > Szene speichern unter...** . Ein Fenster zum Speichern wird angezeigt. Klicken Sie auf die Schaltfläche **neuer Ordner** .

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-49.png)

2.  Nennen Sie den Ordner **Szenen**.

3.  Das Fenster zum **Speichern der Szene** ist weiterhin geöffnet. Öffnen Sie den neu erstellten Ordner **Szenen** .

4.  Geben Sie im Feld **Dateiname:** Text **VideoScene1**ein, und klicken Sie dann auf **Speichern**.

5.  Öffnen Sie in Unity den Ordner **Szenen** , und klicken Sie mit der linken Maustaste auf die Datei **VideoScene1** . Verwenden Sie die Tastatur, und drücken Sie **STRG + D** , um die Szene zu duplizieren.

    > [!TIP]
    > Der Befehl **Duplizieren** kann auch ausgeführt werden, indem Sie zu **Edit > Duplicate**navigieren.

6.  Unity erhöht automatisch die Namen Nummer der Szene, aber überprüfen Sie Sie trotzdem, um sicherzustellen, dass Sie mit dem zuvor eingefügten Code übereinstimmt.

    >  Sie sollten über **VideoScene1** und **VideoScene2**verfügen.

7.  Navigieren Sie in den beiden Kulissen zu **Datei >** Buildeinstellungen. Wenn das Fenster "Buildeinstellungen" geöffnet ist, ziehen Sie die Kulissen in den Bereich " **Build** ".

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > Sie können beide Szenen aus dem Ordner " **Szenen** " auswählen, indem Sie die **STRG** -Taste gedrückt halten und dann mit der linken Maustaste auf jede Szene klicken und schließlich beides ziehen.

8.  Schließen Sie das Fenster Buildeinstellungen, und doppelklicken Sie auf **VideoScene2**.

9.  Wenn die zweite Szene geöffnet ist, klicken Sie auf das untergeordnete **gazebutton** -Objekt von **insienoutsphere**, und legen Sie die Transformation wie folgt fest:

    |            |    TRANSFORMATION-POSITION   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |         **J** 1,3         | **Z** 3,6 |

    |            |    TRANSFORMATION-DREHUNG   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRANSFORMIEREN: SKALIEREN     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **J** 1          |  **Z** 1  |

10. Wenn das untergeordnete **gazebutton** -Element noch ausgewählt ist, sehen Sie sich den **Inspektor** und den **Mesh-Filter**an. Klicken Sie neben dem Feld **Mesh** Reference auf das kleine Ziel:

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-51.png)

11. Ein **Gitter** Popup Fenster auswählen wird angezeigt. Doppelklicken Sie in der Liste der **Assets**auf das **Cube** -Mesh.

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-52.png)

12. Der **Mesh-Filter** wird aktualisiert und ist jetzt ein **Cube**. Klicken Sie nun auf das **Zahnrad** Symbol neben **Sphere Collider** , und klicken Sie auf **Komponente entfernen**, um den Collider aus diesem Objekt zu löschen.

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-53.png)

13. Klicken Sie bei ausgewähltem **gazebutton** auf die Schaltfläche **Komponente hinzufügen** am unteren Rand des **Inspektors**. Geben Sie im Suchfeld **Box**ein, und **Box Collider** ist eine Option. Klicken Sie auf diese Option, um dem **gazebutton** -Objekt einen **Feld-Collider** hinzuzufügen.

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-54.png)

14. Die " **gazebutton"-Schaltfläche** ist nun teilweise aktualisiert, um anders aussehen zu können. Sie erstellen nun jedoch ein neues **Material**, damit es vollständig anders aussieht und leichter als ein anderes Objekt erkannt werden kann, als das Objekt in der ersten Szene.

15. Navigieren Sie im **Projekt Panel**zum Ordner **Material** . Duplizieren Sie das Inhalts Material ( **STRG** + **D** auf der Tastatur, oder klicken Sie mit der linken Maustaste auf das **Material**, und wählen Sie dann in der Menüoption Datei **Bearbeiten** die Option **Duplizieren**aus.)

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-55.png)
    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-56.png)

16. Wählen Sie das neue **buttonmaterial** -Material (hier **Button Material 1**) aus, und klicken Sie im **Inspektor**auf das Fenster **Albedo** -Farbe. Es wird ein Popup Fenster angezeigt, in dem Sie eine andere Farbe auswählen können (Wählen Sie die gewünschten Optionen aus), und schließen Sie dann das Popup Fenster. Das Material ist eine eigene Instanz und unterscheidet sich von der ursprünglichen.

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-57.png)

17. Ziehen Sie das neue **Material** auf das untergeordnete **gazebutton** -Element, um das Erscheinungsbild vollständig zu aktualisieren, damit es von der Schaltfläche "erste Szenen" aus leicht unterschieden werden kann.

    ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-58.png)

18. An diesem Punkt können Sie das Projekt im Editor testen, bevor Sie das UWP-Projekt entwickeln.

    -  Klicken Sie im **Editor** auf die **Wiedergabe** Schaltfläche, und tragen Sie das Headset ein.

        ![Kapitel 7: Einrichten der beiden Unity-Szenen](images/AzureLabs-Lab6-59.png)

19. Sehen Sie sich die beiden **gazebutton** -Objekte an, um zwischen dem ersten und zweiten Video zu wechseln.

## <a name="chapter-8---build-the-uwp-solution"></a>Kapitel 8: Erstellen der UWP-Lösung

Nachdem Sie sichergestellt haben, dass der Editor keine Fehler aufweist, können Sie den Build erstellen.

So erstellen Sie Folgendes:

1.  Speichern Sie die aktuelle Szene, indem Sie auf **Datei > Speichern**klicken.

2.  Aktivieren Sie das Kontrollkästchen **Unity\# -C-Projekte** . (Dies ist wichtig, da Sie die Klassen nach Abschluss des Builds bearbeiten können.)

3.  Wechseln Sie zu **Datei >** Buildeinstellungen, und klicken Sie auf **Erstellen**.

4.  Sie werden aufgefordert, den Ordner auszuwählen, in dem die Projekt Mappe erstellt werden soll.

5.  Erstellen Sie einen Ordner **BUILDS** , und erstellen Sie in diesem Ordner einen anderen Ordner mit einem entsprechenden Namen Ihrer Wahl.

6.  Klicken Sie auf den neuen Ordner, und klicken Sie dann auf **Ordner auswählen**, um diesen Ordner auszuwählen, um den Build an diesem Speicherort zu starten.

    ![Kapitel 8: Erstellen der UWP-Lösung](images/AzureLabs-Lab6-60.png)
    ![, Kapitel 8: Erstellen der UWP-Lösung](images/AzureLabs-Lab6-61.png)

7.  Nachdem die Erstellung von Unity abgeschlossen ist (Dies kann einige Zeit in Anspruch nehmen), wird ein **Datei-Explorer** -Fenster am Speicherort des Builds geöffnet.

## <a name="chapter-9---deploy-on-local-machine"></a>Kapitel 9: Bereitstellung auf lokalem Computer

Nachdem der Build abgeschlossen wurde, wird ein **Datei-Explorer** -Fenster am Speicherort des Builds angezeigt. Öffnen Sie den Ordner, den Sie benannt und erstellt haben, und doppelklicken Sie dann auf die Projektmappendatei (. sln) in diesem Ordner, um die Projekt Mappe mit Visual Studio 2017 zu öffnen.

Das einzige, was Sie tun müssen, ist die Bereitstellung Ihrer APP auf Ihrem Computer (oder auf dem *lokalen*Computer).

Zum Bereitstellen auf dem lokalen Computer:

1.  Öffnen Sie in **Visual Studio 2017**die soeben erstellte Projektmappendatei.

2.  Wählen Sieauf der Projektmappenplattform die Option **x86, lokaler Computer**aus.

3.  Wählen Sie in der Projektmappenkonfiguration **Debuggen**.

    ![Kapitel 9: Bereitstellung auf lokalem Computer](images/AzureLabs-Lab6-62.png)

4.  Sie müssen nun alle Pakete in der Projekt Mappe wiederherstellen. Klicken Sie mit der rechtenMaustaste auf Ihre Projekt Mappe, und klicken Sie auf **nuget-Pakete für Projekt Mappe wiederherstellen.**

    > [!NOTE] 
    > Dies geschieht, da die Pakete, die von Unity erstellt werden, für die Arbeit mit Ihren lokalen Computer verweisen verwendet werden müssen.

5.  Wechseln Sie zum **Menü Erstellen** , und klicken Sie auf **Lösung** bereitstellen, um die Anwendung auf Ihren Computer zu übertragen. Visual Studio erstellt zunächst eine Anwendung und stellt Sie dann bereit.

6.  Ihre APP sollte nun in der Liste der installierten apps angezeigt werden, die gestartet werden können.

    ![Kapitel 9: Bereitstellung auf lokalem Computer](images/AzureLabs-Lab6-63.png)

Wenn Sie die Mixed Reality-Anwendung ausführen, befinden Sie sich innerhalb des **insidebug** -Modells, das Sie in Ihrer APP verwendet haben. Diese Kugel wird an den Speicherort des Videos gestreamt und bietet eine 360-Grad-Ansicht des eingehenden Videos (für diese Art von Perspektive gefilmt). Seien Sie nicht überrascht, wenn das Laden des Videos einige Sekunden dauert, Ihre APP ihrer verfügbaren Internet Geschwindigkeit unterliegt, da das Video abgerufen und dann heruntergeladen werden muss, damit Sie in Ihre APP streamen können.
Wenn Sie bereit sind, können Sie Szenen ändern und das zweite Video öffnen, indem Sie die rote Kugel ansehen! Dann können Sie mit dem blauen Cube in der zweiten Szene wieder zurückkehren.

## <a name="your-finished-azure-media-service-application"></a>Ihre fertige Azure Media Service-Anwendung
 
Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die den Azure Media Service zum Streamen von 360-Videos nutzt.

![Lab-Ergebnis](images/AzureLabs-Lab6-00.png)

![Lab-Ergebnis](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a>Bonus Übungen

**Übung 1**

Es ist durchaus möglich, nur eine einzige Szene zu verwenden, um Videos in diesem Tutorial zu ändern. Experimentieren Sie mit Ihrer Anwendung, und machen Sie Sie in einer einzigen Szene. Fügen Sie der Mischung vielleicht sogar ein weiteres Video hinzu.

**Übung 2**

Experimentieren Sie mit Azure und Unity, und versuchen Sie, die Fähigkeit der APP zu implementieren, automatisch ein Video mit einer anderen Dateigröße auszuwählen, abhängig von der Stärke einer Internet Verbindung.


