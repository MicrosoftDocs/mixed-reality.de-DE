---
title: MR und Azure 306 - Video-Streaming
description: Führen Sie diesen Kurs erfahren, wie Sie Azure Media Services in einer mixed Reality-Anwendung zu implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorials, api, Media Services Videostreaming, 360, immersive vr
ms.openlocfilehash: f6974ab6a72828a557649d5dc65b4e505a7484ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594020"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

<br> 

# <a name="mr-and-azure-306-streaming-video"></a>MR und Azure 306: Streaming-Videos

![Endprodukt-start](images/AzureLabs-Lab6-00.png)
![Endprodukt-starten](images/AzureLabs-Lab6-01.png)

In diesem Kurs erfahren Sie, wie Azure Media Services in eine Windows Mixed Reality-VR-Erfahrung, dass Stream-360-Grad-Videowiedergabe auf immersive Headsets verbinden. 

**Azure Media Services** sind eine Sammlung von Diensten, die Sie Videostreamingdienste in broadcastqualität streamen Videodienste auf ein größeres Publikum auf den heute gängigen Mobilgeräten erreichen kann. Weitere Informationen finden Sie auf die [Azure Media Services-Seite](https://azure.microsoft.com/services/media-services).

Nach Abschluss dieses Kurses, verfügen Sie über ein mixed Reality immersive Kopfhörer Anwendung, die für die folgenden Aufgaben werden können:

1. Abrufen von einem 360-Grad-Video von einer **Azure Storage**, über die **Azure Media Services**.

2. Zeigen Sie die abgerufenen 360-Grad-Video in einem Unity-Szene.

3. Navigieren Sie zwischen den beiden Szenen, mit zwei verschiedenen Videos.

In Ihrer Anwendung obliegt es Ihnen, wie Sie die Ergebnisse in Ihr Design integrieren werden. Dieser Kurs erfahren Sie, wie Sie ein Azure-Dienst in Ihrem Unity-Projekt zu integrieren. Es ist Ihre Aufgabe, verwenden Sie das wissen, dass Sie aus diesem Kurs zum Verbessern Ihrer mixed Reality-Anwendung erhalten.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td> MR und Azure 306: Streaming-Videos</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Vorraussetzungen

> [!NOTE]
> In diesem Tutorial wurde für Entwickler mit Erfahrung mit Unity entwickelt und C#. Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Mai 2018) überprüft wurde. Sie können zur Verwendung der neuesten Software, wie in der [installieren Sie die Tools-Artikel](install-the-tools.md), obwohl es nicht davon ausgegangen werden soll, dass die Informationen in diesem Kurs perfekt was finden Sie in der neueren Software entspricht als die unten Angaben aufgeführten .

Es wird empfohlen, die folgende Hardware und Software für diesen Kurs:

- Eine Entwicklungs-PC [kompatibel mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für immersive (VR) Kopfhörer-Entwicklung
- [Windows 10 Fall Creators Update (oder höher) mit der Entwicklermodus aktiviert ist](install-the-tools.md#installation-checklist)
- [Das neueste Windows 10-SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Ein [immersive Windows Mixed Reality (VR)-Kopfhörer](immersive-headset-hardware-details.md)
- Zugriff auf das Internet für den Abruf von Setup- und Azure
- Zwei 360-Grad-Videos in mp4-Format (finden Sie einige Videos lizenzgebührenfreie [auf dieser Downloadseite](https://www.mettle.com/360vr-master-series-free-360-downloads-page))

## <a name="before-you-start"></a>Bevor Sie beginnen

1.  Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).
2.  Richten Sie ein und Testen Sie Ihrer Mixed Reality Kopfhörer Immersive.

    > [!NOTE]
    > Sie **nicht** Motion-Controller für dieses Kurses erforderlich. Wenn Sie die Einrichtung der Immersive Kopfhörer unterstützen müssen, klicken Sie auf [Link zum Einrichten von Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a>Kapitel 1: das Azure-Portal: Erstellen des Azure-Speicherkontos

Verwenden der **Azure Storage-Dienst**, Sie benötigen zum Erstellen und Konfigurieren einer **Speicherkonto** im Azure-Portal.

1.  Melden Sie sich bei der [Azure-Portal](https://portal.azure.com).

    > [!NOTE]
    > Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen. Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.

2.  Sobald Sie angemeldet sind, klicken Sie auf **Speicherkonten** im linken Menü.

    ![Einrichtung von Azure Storage-Kontos](images/AzureLabs-Lab6-02.png)

3.  Auf der **Speicherkonten** Registerkarte, klicken Sie auf **hinzufügen**.

    ![Einrichtung von Azure Storage-Kontos](images/AzureLabs-Lab6-03.png)

4.  In der **Storage-Konto erstellen** Registerkarte:

    1.  Fügen Sie eine **Namen** für Ihr Konto bedenken, dass dieses Feld akzeptiert nur Ziffern und Kleinbuchstaben zulässig.

    2.  Für **Bereitstellungsmodell** wählen **RM**.

    3.  Für **Kontoart**Option **Speicher (Allgemein v1)**.

    4.  Für **Leistung**Option **Standard *.**

    5.  Für **Replikation** wählen **lokal redundanter Speicher (LRS)**.

    6.  Lassen Sie **sichere Übertragung erforderlich** als **deaktiviert**.

    7.  Wählen Sie eine **Abonnement**.

    8.  Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.

    9.  Bestimmen der **Speicherort** für Ihre Ressourcengruppe aus (Wenn Sie eine neue Ressourcengruppe erstellen). Der Speicherort würde idealerweise in der Region sein, in dem die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.

5.  Sie benötigen, um sicherzustellen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.

    ![Einrichtung von Azure Storage-Kontos](images/AzureLabs-Lab6-04.png)

6.  Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.

7.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Einrichtung von Azure Storage-Kontos](images/AzureLabs-Lab6-05.png)

8.  Sie müssen an diesem Punkt nicht, führen die Ressource, verschieben Sie einfach zum nächsten Kapitel zu können.

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a>Kapitel 2: das Azure-Portal: Erstellen von Media Service

Um die Azure Media Services verwenden zu können, müssen Sie so konfigurieren Sie eine Instanz des Diensts, der für Ihre Anwendung verfügbar gemacht werden (bei dem der Besitzer des Kontos muss ein Administrator sein).

1.  Klicken Sie im Azure-Portal auf **erstellen Sie eine Ressource** in der oberen linken Ecke, und suchen Sie nach **Mediendienst,** drücken Sie die **EINGABETASTE**. Die Ressource, die Sie verwenden möchten verfügt über ein Symbol "rosa"; Klicken Sie hierauf, um eine neue Seite anzuzeigen.

    ![Das Azure-Portal](images/AzureLabs-Lab6-06.png)

2.  Die neue Seite bietet eine Beschreibung der **Mediendienst**. Unten links der Aufforderung, klicken Sie auf die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.

    ![Das Azure-Portal](images/AzureLabs-Lab6-07.png)

3.  Nachdem Sie auf geklickt haben **erstellen** ein Panel wird angezeigt, in denen Sie einige Details zu Ihrem neuen Mediendienst bereitstellen müssen:

    1.  Fügen Sie Ihre bevorzugte **Kontoname** für diese Dienstinstanz.

    2.  Wählen Sie eine **Abonnement**.

    3. Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diesen Labs) unter einer allgemeinen Ressourcengruppe zu halten). 
    
    > Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, befolgen Sie diese [Link zum Azure-Ressourcengruppen verwalten](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Bestimmen der **Speicherort** für Ihre Ressourcengruppe aus (Wenn Sie eine neue Ressourcengruppe erstellen). Der Speicherort würde idealerweise in der Region sein, in dem die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.

    5.  Für die **Speicherkonto** auf die **wählen Sie bitte...**  Abschnitt, und klicken Sie dann die **Speicherkonto** Sie im letzten Abschnitt erstellt haben.

    6.  Sie müssen auch bestätigen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.

    7.  Klicken Sie auf **Erstellen**.

        ![Das Azure-Portal](images/AzureLabs-Lab6-08.png)

4.  Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.

5.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Das Azure-Portal](images/AzureLabs-Lab6-09.png)

6.  Klicken Sie auf die Benachrichtigung, um Ihre neue Dienstinstanz zu untersuchen.

    ![Das Azure-Portal](images/AzureLabs-Lab6-10.png)

7.  Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen.

8.  Klicken Sie auf der Seite der neue Media Service, innerhalb des Bereichs auf der linken Seite auf die **Assets** Link, der in der Mitte nach unten geht.

9.  Klicken Sie auf der nächsten Seite in der oberen linken Ecke der Seite auf **hochladen**.

    ![Das Azure-Portal](images/AzureLabs-Lab6-11.png)

10. Klicken Sie auf die **Ordner** Symbol, um Ihre Dateien auszuwählen, das zuerst 360 Video, das Sie streamen möchten. 
    
    > Führen Sie dies [Link zum Herunterladen von ein beispielvideo](https://vimeo.com/214401712).

    ![Das Azure-Portal](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> Lange Dateinamen verursacht möglicherweise Probleme mit dem Encoder: um sicherzustellen, dass Videos keine Probleme, daher sollten Sie mit den Namen Ihrer Videodatei verkürzen.

11. Die Statusanzeige wird grün, wenn das Video Hochladen abgeschlossen ist.

    ![Das Azure-Portal](images/AzureLabs-Lab6-13.png)

12. Klicken Sie auf der obige Text (**Yourservicename - Assets**) zum Zurückgeben der **Assets** Seite.

13. Beachten Sie, dass Ihr Video wurde erfolgreich hochgeladen wurde. Klicken Sie darauf.

    ![Das Azure-Portal](images/AzureLabs-Lab6-14.png)

14. Die Seite, der Sie zur umgeleitet werden zeigt, dass ausführliche Informationen zu Ihrem Video. In der Lage, Ihr Video zu verwenden, müssen Sie es, zu codieren, indem Sie auf, die **Encode** auf der oberen linken Ecke der Seite.

    ![Das Azure-Portal](images/AzureLabs-Lab6-15.png)

15. Ein neuer Bereich wird auf der rechten Seite angezeigt, sodass Sie zum Codieren der Optionen für die Datei können. Legen Sie die folgenden Eigenschaften (einige wird bereits standardmäßig festgelegt):

    1.  **Media Encoder-Name *Media Encoder Standard***

    2.  **Codierungsvoreinstellung *Content Adaptive Multiple Bitrate MP4***

    3.  **Auftragsname *Media Encoder Standard Verarbeitung Video1.mp4***

    4.  **Name des ausgabemedienobjekts *Video1.mp4 – Media Encoder Standard codiert***

        ![Das Azure-Portal](images/AzureLabs-Lab6-16.png)

16. Klicken Sie auf die Schaltfläche **Erstellen**.

17. Sie sehen eine Leiste mit **Codierung Auftrags hinzugefügt**, klicken Sie auf diese Leiste, und ein Bereich wird angezeigt, mit der Codierung angezeigt.

    ![Das Azure-Portal](images/AzureLabs-Lab6-17.png)

    ![Das Azure-Portal](images/AzureLabs-Lab6-18.png)

18. Warten Sie, bis der Auftrag abgeschlossen ist. Wenn dies abgeschlossen ist, können Sie den Bereich mit der "X" in der rechten oberen Bereich zu schließen.

    ![Das Azure-Portal](images/AzureLabs-Lab6-19.png)

    ![Das Azure-Portal](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > Der Zeitaufwand, hängt von der Größe Ihres Videos ab. Dieser Vorgang kann einige Zeit dauern.

19. Nun, dass die codierte Version des Videos erstellt wurde, können Sie darauf, um darauf zugegriffen werden kann veröffentlichen. Zu diesem Zweck klicken Sie auf den blauen Link **Assets** um zurück auf der Seite "Bestand" zu wechseln.

    ![Das Azure-Portal](images/AzureLabs-Lab6-21.png)

20. Sehen Sie Ihr Video zusammen mit einem anderen vom ** Ressourcentyp * Multi-Bitrate-MP4 ***.

    ![Das Azure-Portal](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > Sie möglicherweise feststellen, dass das neue Medienobjekt, zusammen mit Ihrer ersten Video *unbekannte*, und weist '0' Bytes für sie **Größe**, aktualisieren Sie das Fenster für die sie aktualisieren.

21. Klicken Sie auf diese neue Anlage.

    ![Das Azure-Portal](images/AzureLabs-Lab6-23.png)

22. Sie sehen einen ähnlichen Bereich für die, die Sie verwendet werden, bevor dies auf eine andere Ressource ist. Klicken Sie auf die **veröffentlichen** Schaltfläche am oben in der Mitte der Seite.

    ![Das Azure-Portal](images/AzureLabs-Lab6-24.png)

23. Werden Sie aufgefordert, Sie legen eine **Locator**, dies ist der Einstiegspunkt, auf die Datei/s in Ihren Ressourcen. Legen für Ihr Szenario die folgenden Eigenschaften:

    1.  **Locatortyp** > **Progressive**.

    2.  Die **Datum** und **Zeit** festgelegt, die Sie aus Ihrer aktuellen Datum, zu einem Zeitpunkt in der Zukunft (100 Jahre in diesem Fall). Lassen Sie unverändert verwenden oder ändern Sie ihn entsprechend.

    > [!NOTE]
    > Weitere Informationen zu Locators, und was Sie auswählen können, finden Sie auf die [Azure Media Services-Dokumentation](https://docs.microsoft.com/azure/media-services/media-services-concepts).

24. Am unteren Bereich, klicken Sie auf die **hinzufügen** Schaltfläche.

    ![Das Azure-Portal](images/AzureLabs-Lab6-25.png)

25. Ihr Video wurde veröffentlicht und kann mithilfe des zugehörigen Endpunkts gestreamt werden. Weiter unten die Seite ist eine **Dateien** Abschnitt. Dies ist das, wo die verschiedenen codierten Versionen Ihres Videos werden sollen. Wählen Sie die höchste mögliche Lösung eine (in der Abbildung unten sie ist die 1920 x 960-Datei), und klicken Sie dann ein Bereich auf der rechten Seite wird angezeigt. Dort sehen Sie eine **Download-URL**. Kopieren Sie diese **Endpunkt** , wie Sie es später in Ihrem Code verwenden.

    ![Das Azure-Portal](images/AzureLabs-Lab6-26.png)    

    ![Das Azure-Portal](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > Drücken Sie die **spielen** Schaltfläche, um das Video abspielen, und Testen Sie sie.

26. Sie müssen jetzt das zweite Video hochladen, das Sie in dieser Übung verwenden. Führen Sie die Schritte oben, wiederholen Sie den Vorgang für das zweite Video aus. Stellen Sie sicher, Sie kopieren das zweite **Endpunkt** auch. Verwenden Sie die folgenden [Link zum Herunterladen von einem zweiten Video](https://vimeo.com/214402865).

27. Nachdem beide Videos veröffentlicht wurden, sind Sie bereit sind, finden Sie im nächsten Kapitel.

## <a name="chapter-3---setting-up-the-unity-project"></a>Kapitel 3 – Einrichten des Unity-Projekts

Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit dem Mixed Reality und daher ist eine gute Vorlage für andere Projekte.

1.  Open **Unity** , und klicken Sie auf **neu**. 

    ![Das Azure-Portal](images/AzureLabs-Lab6-28.png)

2.  Sie müssen nun zum Bereitstellen eines Namen Unity-Projekt einfügen **MR\_360VideoStreaming.**. Stellen Sie sicher, dass der Projekttyp nastaven NA hodnotu **3D**. Legen Sie den Speicherort, an eine Position, die für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser). Klicken Sie auf **projekterstellung**.

    ![Das Azure-Portal](images/AzureLabs-Lab6-29.png)

3.  Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio.** Wechseln Sie zu ***bearbeiten* *Voreinstellungen*** und navigieren Sie dann im neuen Fenster zu **externe Tools**. Änderung **externen Skript-Editors** zu **Visual Studio 2017**. Schließen der **Voreinstellungen** Fenster.

    ![Das Azure-Portal](images/AzureLabs-Lab6-30.png)

4.  Öffnen Sie als Nächstes ***Datei* *Buildeinstellungen*** , und wechseln von der Plattform bereitgestellten **universelle Windows-Plattform**, durch Klicken auf die **Plattform wechseln** Schaltfläche.

5.  Außerdem stellen Sie sicher, dass:

    1. **Geräte** nastaven NA hodnotu **einem beliebigen Gerät.**
    
    2.  **Buildtyp** nastaven NA hodnotu **D3D.**

    3.  **SDK** nastaven NA hodnotu **zuletzt installiert.**

    4.  **Visual Studio-Version** nastaven NA hodnotu **zuletzt installiert.**

    5.  **Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer.**

    6.  Aber keine Sorge, über das Einrichten von **Szenen** jetzt, wie Sie diese später eingerichtet werden.

    7.  Die übrigen Einstellungen sollte jetzt als Standard bleiben.

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab6-31.png)

6.  In der **Buildeinstellungen** Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dadurch wird den entsprechenden Bereich geöffnet, im Bereich, in dem die **Inspektor** befindet. 

7. In diesem Bereich sind müssen einige Einstellungen überprüft werden:

    1.  In der **Weitere Einstellungen** Registerkarte:

        1.  **Scripting** **Laufzeitversion** muss **stabile** (.NET 3.5 entspricht).

        2. **Back-End-Scripting** muss **.NET.**

        3. **API-Kompatibilitätsebene** muss **.NET 4.6.**

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab6-32.png)

    2.  Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality-SDK**  hinzugefügt wird.

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab6-33.png)

    3.  In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:

        - **InternetClient**

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab6-34.png)

8.  Wenn Sie diese Änderungen vorgenommen haben, schließen Sie die **Buildeinstellungen** Fenster.

9.  Speichern Sie das Projekt **Datei* * speichern Projekt **.



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a>Kapitel 4: Importieren des InsideOutSphere Unity-Pakets

> [!IMPORTANT]
> Wenn Sie, überspringen Sie möchten die *Unity einrichten* -Komponente dieser Kurs, und direkt in Code fortsetzen, können Sie zum Herunterladen [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), importieren Sie es in Ihr Projekt als eine [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), und klicken Sie dann eine Fortsetzung **Kapitel 5**. Sie müssen immer noch ein Unity-Projekt zu erstellen.

Für diesen Kurs an, Sie ein Unity Asset-Paket herunterladen müssen, aufgerufen [ **InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).

Gewusst-wie-Import der **vstu**:

1.  Mit dem Sie Unity-Dashboard, klicken Sie auf **Assets** klicken Sie dann im Menü am oberen Rand des Bildschirms auf **Paket importieren > benutzerdefiniertes Paket**.

    ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-35.png)

2.  Verwenden Sie die Dateiauswahl zum Auswählen der **InsideOutSphere.unitypackage** packen, und klicken Sie auf **öffnen**. Eine Liste der Komponenten für dieses Medienobjekt wird Ihnen angezeigt werden. Bestätigen Sie den Import, indem Sie auf **importieren**.

    ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-36.png)

3.  Anschließend importieren, werden Sie feststellen, dass drei neue Ordner **Materialien**, **Modelle**, und **Prefabs**, wurden hinzugefügt, um Ihre **Assets**Ordner. Diese Art von Struktur ist typisch für ein Unity-Projekt.

    ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-37.png)

    1.  Öffnen der **Modelle** Ordner, und Sie sehen, die die **InsideOutSphere** Modell importiert wurde.

    2.  Innerhalb der **Materialien** Ordner Sie finden die **InsideOutSpheres** Material *lambert1*, sowie ein Material namens *ButtonMaterial*, die von der GazeButton, die in Kürze angezeigt werden, verwendet wird.

    3.  Die **prefabs (Vorlagen)** Ordner enthält die **InsideOutSphere** Prefab enthält sowohl die **InsideOutSphere** *Modell* und die  *GazeButton*.

    4.  **Es ist kein Code enthalten**, Schreiben Sie Code anhand dieses Kurses.


4.  In der **Hierarchie**, wählen die **Main Camera** Objekt aus, und aktualisieren Sie die folgenden Komponenten:

    1.  **Transform**

        1.  Position = **X**: 0, **Y**: 0, **Z**: 0.

        2. Rotation = **X**: 0, **Y**: 0, **Z**: 0.

        3. Skalierung **X**: 1, **Y**: 1, **Z**: 1.

    2.  **Kamera**

        1. **Deaktivieren Sie Flags**: Volltonfarbe entspricht.

        2.  **Clipping Planes**: In der Nähe von: 0,1, weit: 6.

            ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-38.png)

5.  Navigieren Sie zu der **Prefab** Ordner, und ziehen Sie dann die **InsideOutSphere** prefab in die **Hierarchie** Bereich.

    ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-39.png)

6.  Erweitern Sie die **InsideOutSphere** -Objekts innerhalb der **Hierarchie** durch Klicken auf den kleinen Pfeil daneben. Sie sehen eine **untergeordneten** Objekt unter dem Namen **GazeButton**. Dies wird verwendet um Szenen und somit auf Videos zu ändern.

    ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-40.png)

7.  Klicken Sie im Inspektor-Fenster auf die **InsideOutSphere**Transformationskomponente, stellen Sie sicher, dass die folgenden Eigenschaften festgelegt sind:

    |            |    TRANSFORM - POSITION   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |    TRANSFORM - DREHUNG   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** -50        |  **Z** 0  |

    |            |     TRANSFORM - SKALIERUNG     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-41.png)

8.  Klicken Sie auf die **GazeButton** untergeordnetes Objekt, und legen dessen **transformieren** wie folgt:

    |            |    TRANSFORM - POSITION   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 3.6|          **Y** 1.3        |  **Z** 0  |

    |            |    TRANSFORM - DREHUNG   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRANSFORM - SKALIERUNG     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

    ![Importieren des InsideOutSphere Unity-Pakets](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a>Kapitel 5 – erstellen Sie die VideoController-Klasse

Die **VideoController** Klasse hostet die beiden video Endpunkte, die zum Streamen des Inhalts aus der Azure Media Services verwendet werden.

Diese Klasse zu erstellen:

1.  Mit der rechten Maustaste den **Ordner "Assets"** befindet sich in der **Projekt** Bereich, und klicken Sie auf **erstellen > Ordner**. Nennen Sie den Ordner **Skripts**.

    ![Erstellen Sie die VideoController-Klasse](images/AzureLabs-Lab6-43.png)

    ![Erstellen Sie die VideoController-Klasse](images/AzureLabs-Lab6-44.png)

2.  Klicken Sie mit der Doppelklicken auf die **Skripts** Ordner aus, um ihn zu öffnen.

3.  Mit der rechten Maustaste in den Ordner, und klicken Sie dann **erstellen > C\# Skript**. Nennen Sie das Skript **VideoController**.

    ![Erstellen Sie die VideoController-Klasse](images/AzureLabs-Lab6-45.png)

4.  Doppelklicken Sie auf dem neuen **VideoController** Skript öffnen Sie ihn mit **Visual Studio 2017.**

    ![Erstellen Sie die VideoController-Klasse](images/AzureLabs-Lab6-46.png)

5.  Aktualisieren Sie die Namespaces am Anfang der Codedatei wie folgt:

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  Geben Sie die folgenden Variablen in der **VideoController** -Klasse ermöglicht zusammen mit den **Awake()** Methode:

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

7.  Jetzt ist die Zeit, die Endpunkte aus Ihren Azure Media Services-Videos einzugeben:

    1.  Die erste in der *video1endpoint* Variable.
    
    2.  Das zweite in der *video2endpoint* Variable.

    > [!WARNING]
    > Es ist ein bekanntes Problem mit der Verwendung von *Https* in Unity, mit der Version 2017.4.1f1. Wenn die Videos einen Fehler auf Play zur Verfügung, versuchen Sie es stattdessen mit "http".

8.  Als Nächstes die **Start()** -Methode muss bearbeitet werden. Diese Methode wird jedes Mal, wenn der Benutzer Szene (wechseln daher das Video) wechselt, indem Sie die Schaltfläche mit den bestaunen ansehen ausgelöst.

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  Nach der **Start()** -Methode, fügen Sie der **PlayVideo()** *IEnumerator* -Methode, die verwendet wird, um Videos zu starten, nahtlos (also ohne Stottern zu sehen ist).

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

10. Die letzte Methode, die für diese Klasse ist, müssen Sie die **ChangeScene()** -Methode, die zum Wechseln zwischen Szenen verwendet wird.

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > Die **ChangeScene()** -Methode verwendet eine praktische C\# Feature mit dem Namen der *Bedingungsoperator*. Dies ermöglicht die Bedingungen, die überprüft werden, und klicken Sie dann Werte zurückgegeben, auf das Ergebnis der Überprüfung in einer einzelnen Anweisung basiert. Gehen Sie folgendermaßen vor [Link Weitere Informationen zum bedingten Operator](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).

11. Speichern Sie die Änderungen in Visual Studio vor der Rückgabe in Unity.

12. Zurück in die Unity-Editor zu klicken und ziehen Sie die **VideoController** Klasse [from] {.underline} die **Skripts** Ordner, um die **Main Camera** -Objekt in der  **Hierarchie** Bereich.

13. Klicken Sie auf die **Main Camera** und sehen Sie sich die **Inspektor Bereich**. Sie werden feststellen, dass in der neu hinzugefügten Komponente, ein Feld mit einem leeren Wert vorhanden ist. Dies ist ein Verweisfeld, das auf die öffentlichen Variablen innerhalb des Codes.

14. Ziehen Sie die **InsideOutSphere** -Objekt aus der **Hierarchie Bereich** auf die **Kugel** slot, wie in der folgenden Abbildung dargestellt.

    ![Erstellen Sie die Klasse VideoController](images/AzureLabs-Lab6-47.png)
    ![erstellen Sie die VideoController-Klasse](images/AzureLabs-Lab6-48.png)

## <a name="chapter-6---create-the-gaze-class"></a>Kapitel 6: Erstellen Sie die Blicke-Klasse

Diese Klasse ist zuständig für das Erstellen einer **Raycast** Beprojected weitergeleitet wird, aus der **Main Camera**, welches Objekt erkannt, wird der Benutzer ansehen. In diesem Fall die **Raycast** benötigen, um festzustellen, ob der Benutzer ansieht der **GazeButton** Objekt in der Szene, und lösen Sie ein Verhalten.

Zum Erstellen dieser Klasse:

1.  Wechseln Sie zu der **Skripts** Ordner, die Sie zuvor erstellt haben.

2.  Mit der rechten Maustaste den **Projekt** Bereich **erstellen* * C\# Script **. Nennen Sie das Skript **bestaunen**.

3.  Doppelklicken Sie auf dem neuen ***bestaunen*** Skript öffnen Sie ihn mit **Visual Studio 2017.**

4.  Stellen Sie sicher, dass die folgende Namespace am Anfang des Skripts ist, und entfernen Sie alle anderen:

    ```csharp
    using UnityEngine;
    ```

5.  Klicken Sie dann fügen Sie die folgenden Variablen in der **bestaunen** Klasse:

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

6.  Code für die **Awake()** und **Start()** Methoden jetzt hinzugefügt werden muss.

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

7.  Fügen Sie den folgenden Code in die **Update()** Methode, um eine Raycast Projekt, und erkennen das Ziel erreicht:

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

8.  Speichern Sie die Änderungen in Visual Studio vor der Rückgabe in Unity.

9.  Klicken Sie auf, und ziehen Sie die **bestaunen** Klasse aus dem Ordner Scripts, um die Main Camera-Objekts in der **Hierarchie** Bereich.

## <a name="chapter-7---setup-the-two-unity-scenes"></a>Kapitel 7 – Setup die beiden Unity im Hintergrund

Dieses Kapitel dient zum Einrichten von der beiden Szenen, die jeder ein Video in Stream hostet. Die Szene, die Sie bereits erstellt haben, wird dupliziert werden, sodass Sie nicht benötigen diesen erneut einrichten, aber Sie Sie dann die neue Szene bearbeiten, sodass die *GazeButton* Objekt in einen anderen Speicherort und verfügt über eine andere Darstellung. Dies ist veranschaulichen, wie Sie zwischen Szenen zu ändern.

1.  Zu diesem Zweck sollen **Datei > Szene speichern als...** . Ein Speichern Fenster wird angezeigt. Klicken Sie auf die **neuer Ordner** Schaltfläche.

    ![Kapitel 7 – Setup die beiden Unity im Hintergrund](images/AzureLabs-Lab6-49.png)

2.  Nennen Sie den Ordner **Szenen**.

3.  Die **Szene speichern** Fenster werden weiterhin öffnen. Öffnen Sie den neu erstellten **Szenen** Ordner.

4.  In der **Dateiname:** Textfeld **VideoScene1**, drücken Sie dann die **speichern**.

5.  Öffnen Sie in Unity, Ihre **Szenen** Ordner, und klicken Sie auf Ihre **VideoScene1** Datei. Verwenden die Tastatur, und drücken Sie die **STRG + D** werden Sie diese Szene duplizieren

    > [!TIP]
    > Die **doppelte** Befehl kann auch ausgeführt werden, durch Navigieren zu **Bearbeiten > duplizieren**.

6.  Unity wird automatisch erhöhen Sie die Anzahl der Szene-Namen, aber es jedenfalls überprüfen, um sicherzustellen, dass sie dem zuvor eingefügten Code entspricht.

    >  Sie müssen **VideoScene1** und **VideoScene2**.

7.  Mit den beiden Szenen, wechseln Sie zu **Datei > Buildeinstellungen**. Mit der **Buildeinstellungen** Fenster geöffnet ist, ziehen Sie die Szenen, die **Szenen in Build** Abschnitt.

    ![Kapitel 7: Einrichten von den beiden Szenen mit Unity](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > Können Sie wählen Sie beide den Szenen aus Ihrer **Szenen** Ordner enthalten das **STRG** Schaltfläche, und klicken Sie dann mit der linken Maustaste jeder Szene, und zum Schluss ziehen Sie sowohl über.

8.  Schließen der **Buildeinstellungen** Fenster, und doppelklicken Sie auf **VideoScene2**.

9.  Öffnen Sie die zweite Szene, und klicken Sie auf die **GazeButton** untergeordnetes Objekt der **InsideOutSphere**, und legen Sie seine Transformation wie folgt:

    |            |    TRANSFORM - POSITION   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |         **Y** 1.3         | **Z** 3.6 |

    |            |    TRANSFORM - DREHUNG   |           |
    | :---------:| :-----------------------: | :--------:|
    |   **X** 0  |          **Y** 0          |  **Z** 0  |

    |            |     TRANSFORM - SKALIERUNG     |           |
    | :---------:| :-----------------------: | :--------:|
    |  **X** 1   |          **Y** 1          |  **Z** 1  |

10. Mit der **GazeButton** ausgewählt, und suchen am untergeordneten der **Inspektor** und die **Mesh Filter**. Klicken Sie auf das kleine Ziel neben der **Mesh** Referenzfeld:

    ![Kapitel 7: Einrichten von den beiden Szenen mit Unity](images/AzureLabs-Lab6-51.png)

11. Ein **wählen Mesh** Popupfenster wird angezeigt. Doppelklicken dem **Cube** aus der Liste der mesh **Assets**.

    ![Kapitel 7: Einrichten von den beiden Szenen mit Unity](images/AzureLabs-Lab6-52.png)

12. Die **Mesh Filter** aktualisiert, und jetzt eine **Cube**. Klicken Sie nun die **Zahnradsymbol** Symbol neben dem **Kugel "collider"** , und klicken Sie auf **Komponente entfernen**, um die "collider" von diesem Objekt zu löschen.

    ![Kapitel 7: Einrichten von den beiden Szenen mit Unity](images/AzureLabs-Lab6-53.png)

13. Mit der **GazeButton** immer noch ausgewählt ist, klicken Sie auf die **Add Component** Schaltfläche am unteren Rand der **Inspektor**. Geben Sie in das Suchfeld ein, **Feld**, und **Box-Collider** wird eine Option: Klicken Sie auf, dass zum Hinzufügen einer **Box-Collider** auf Ihre **GazeButton** Objekt .

    ![Kapitel 7: Einrichten von den beiden Szenen mit Unity](images/AzureLabs-Lab6-54.png)

14. Die **GazeButton** ist jetzt teilweise aktualisiert wird, anders, suchen jedoch jetzt erstellen Sie ein neues **Material**, damit es völlig anders aussieht, und einfacher ist zu erkennen, wie ein anderes Objekt, als die Objekt in die erste Szene.

15. Navigieren Sie zu Ihrem **Materialien** Ordner, der innerhalb der **Projektfenster**. Duplizieren der **ButtonMaterial** Material (drücken Sie die **STRG** + **D** auf der Tastatur, oder klicken Sie auf die **Material**, klicken Sie dann von der **bearbeiten** Datei Menüoption wählen **doppelte**).

    ![Kapitel 7: Einrichten von zwei Unity im Hintergrund](images/AzureLabs-Lab6-55.png)
    ![Kapitel 7: Einrichten von den beiden Szenen mit Unity](images/AzureLabs-Lab6-56.png)

16. Wählen Sie die neue **ButtonMaterial** Material (hier mit dem Namen **ButtonMaterial 1**), und innerhalb der **Inspektor**, klicken Sie auf die **Albedo** Farbe Fenster. Ein Popupfenster angezeigt wird, können Sie eine andere Farbe auswählen (Wählen Sie je nachdem, was Ihnen gefällt), klicken Sie dann das Popup zu schließen. Das Material werden ihre eigene Instanz, und mit dem Original unterscheidet.

    ![Kapitel 7: Einrichten von den beiden Szenen mit Unity](images/AzureLabs-Lab6-57.png)

17. Ziehen Sie die neue **Material** auf die **GazeButton** untergeordnete, jetzt vollständig die aussehen, aktualisieren, damit sie problemlos von der ersten im Hintergrund-Schaltfläche zu unterscheiden ist.

    ![Kapitel 7: Einrichten von den beiden Szenen mit Unity](images/AzureLabs-Lab6-58.png)

18. An diesem Punkt können Sie das Projekt im Editor testen, bevor Sie das UWP-Projekt erstellen.

    -  Drücken Sie die **spielen** Schaltfläche der **Editor** und Ihre Kopfhörer wear.

        ![Kapitel 7: Einrichten von den beiden Szenen mit Unity](images/AzureLabs-Lab6-59.png)

19. Sehen Sie sich die beiden **GazeButton** Objekte zwischen der ersten und zweiten Video wechseln.

## <a name="chapter-8---build-the-uwp-solution"></a>Kapitel 8 – erstellen Sie die UWP-Projektmappe

Nachdem Sie sichergestellt haben, dass der Editor keine Fehler aufweist, sind Sie bereit für Build.

So erstellen Sie:

1.  Speichern Sie durch Klicken auf die aktuelle Szene **Datei > Speichern**.

2.  Aktivieren Sie das Kontrollkästchen namens **Unity C\# Projekte** (Dies ist wichtig, da er kann Sie die Klassen zu bearbeiten, nachdem der Build abgeschlossen ist).

3.  Wechseln Sie zu **Datei > Buildeinstellungen**, klicken Sie auf **erstellen**.

4.  Sie werden aufgefordert werden, um den Ordner auszuwählen, in dem Sie Buildthe Lösung möchten.

5.  Erstellen Sie eine **erstellt** Ordner, und erstellen Sie einen anderen Ordner in diesem Ordner mit einem entsprechenden Namen Ihrer Wahl.

6.  Klicken Sie auf den neuen Ordner, und klicken Sie dann auf **Ordner auswählen**, also auf diesen Ordner ein, um den Build an diesem Speicherort zu beginnen.

    ![Kapitel 8 – Erstellen Sie die UWP-Projektmappe](images/AzureLabs-Lab6-60.png)
    ![Kapitel 8 – erstellen Sie die UWP-Projektmappe](images/AzureLabs-Lab6-61.png)

7.  Einmal Unity wurde (es kann einige Zeit dauern) erstellen, öffnen ein **Datei-Explorer** Fenster am Speicherort des Builds.

## <a name="chapter-9---deploy-on-local-machine"></a>Kapitel 9 – bereitstellen, auf dem lokalen Computer

Nachdem der Build abgeschlossen wurde, eine **Datei-Explorer** Fenster wird angezeigt, an der Position des Builds. Öffnen Sie den Ordner, die Sie mit dem Namen und integriert, und klicken Sie dann einen Doppelklick auf die Projektmappendatei (.sln) in diesem Ordner, um die Projektmappe mit Visual Studio 2017 geöffnet haben.

Müssen Sie nur noch tun wird Ihre app auf Ihrem Computer bereitstellen (oder *lokalen Computer*).

So stellen Sie auf dem lokalen Computer bereit:

1.  In **Visual Studio 2017**, öffnen Sie die Projektmappendatei, die gerade erstellt wurde.

2.  In der **Projektmappenplattform**Option **X86, lokalen Computer**.

3.  In der **Projektmappenkonfiguration** wählen **Debuggen**.

    ![Kapitel 9 – Bereitstellen Sie, auf dem lokalen Computer](images/AzureLabs-Lab6-62.png)

4.  Sie müssen jetzt alle Pakete der Projektmappe wiederherstellen. Mit der rechten Maustaste auf Ihre **Lösung**, und klicken Sie auf **Wiederherstellen von NuGet-Pakete für Projektmappe...**

    > [!NOTE] 
    > Dies geschieht, da die Pakete, die den erstellt Unity bereitgestellt werden soll, um die Arbeit mit Ihrem lokalen Computer verweisen müssen.

5.  Wechseln Sie zu **Menü "Build"** und klicken Sie auf **Projektmappe bereitstellen** zum querladen der Anwendung auf Ihrem Computer. Visual Studio zum ersten Mal erstellen und anschließend bereitstellen.

6.  Ihre App sollte nun in der Liste der installierten apps, die zu startenden bereit angezeigt werden.

    ![Kapitel 9 – Bereitstellen Sie, auf dem lokalen Computer](images/AzureLabs-Lab6-63.png)

Wenn Sie die Mixed Reality-Anwendung ausführen, Sie sehen werden innerhalb der **InsideOutSphere** Modell, die Sie in Ihrer app verwendet. Diese Kugel werden, in dem das Video gestreamt wird, bietet eine 360 °-Sicht auf, der den eingehenden Videostream (die für diese Art von Perspektive gedreht wurde). Führen Sie nicht überrascht sein, wenn das Video ein paar Sekunden zum Laden akzeptiert, unterliegen der verfügbaren internetgeschwindigkeit, Ihre app ist wie das Video muss abgerufen werden, und klicken Sie dann heruntergeladen, also zum Streamen in Ihrer app.
Wenn Sie bereit sind, ändern Sie im Hintergrund zu, und öffnen Sie Ihre zweite Video, indem Sie auf die rote Kugel gazing! Klicken Sie dann gerne zurück, mit dem blauen Cube in der zweiten Szene!

## <a name="your-finished-azure-media-service-application"></a>Der fertigen Anwendung für Azure Media Services
 
Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die die Azure Media Services zum Streamen von Videos mit 360 nutzt.

![Lab-Ergebnis](images/AzureLabs-Lab6-00.png)

![Lab-Ergebnis](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a>Bonus-Übungen

**Übung 1**

Es ist durchaus möglich, mit nur einer einzigen Szene auf Videos in diesem Lernprogramm ändern. Experimentieren Sie mit Ihrer Anwendung, und legen Sie ihn in einer einzigen Szene auf. Vielleicht sogar ein anderes Video zur Mischung hinzufügen.

**Übung 2**

Experimentieren Sie mit Azure und Unity, und versuchen Sie, implementieren Sie die Möglichkeit, dass die app automatisch ein Video mit einer anderen Dateigröße, je nach die Stärke des eine Internetverbindung auswählen.


