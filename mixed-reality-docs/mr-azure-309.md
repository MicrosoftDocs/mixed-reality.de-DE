---
title: Mr und Azure 309-Application Insights
description: Machen Sie sich mit diesem Kurs vertraut, um zu erfahren, wie Sie mit dem Azure-Anwendung Insights-Dienst Analysen bezüglich des Benutzer Verhaltens in einer gemischten Reality-Anwendung sammeln.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Application Insights, hololens, immersive, VR
ms.openlocfilehash: e14a32f9a38e3e8f3054d19310782f7c2d4784a1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694561"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.

<br> 

# <a name="mr-and-azure-309-application-insights"></a>Mr und Azure 309: Application Insights

![Endgültiges Produkt-Start](images/AzureLabs-Lab309-00.png)

In diesem Kurs erfahren Sie, wie Sie Application Insights Funktionen zu einer gemischten Reality-Anwendung hinzufügen, indem Sie die Azure-Anwendung Insights-API verwenden, um Analysen bezüglich des Benutzer Verhaltens zu erfassen.

Application Insights ist ein Microsoft-Dienst, der es Entwicklern ermöglicht, Analysen von Ihren Anwendungen zu sammeln und Sie über ein einfach zu verwendende Portal zu verwalten. Die Analyse kann von der Leistung bis hin zu benutzerdefinierten Informationen erfolgen, die Sie erfassen möchten. Weitere Informationen finden Sie auf der [Seite Application Insights](https://azure.microsoft.com/services/application-insights/).

Nachdem Sie diesen Kurs abgeschlossen haben, verfügen Sie über eine gemischte Reality-Headset-Anwendung, die Folgendes ausführen kann:

1.  Ermöglicht dem Benutzer das durchschauen und bewegen einer Szene.
2.  Veranlassen Sie das Senden von Analysen an den *Application Insights-Dienst*, indem Sie die Verwendung von Blick und Nähe zu in-Scene-Objekten verwenden.
3.  Die APP ruft auch auf dem Dienst auf und ruft in den letzten 24 Stunden Informationen darüber ab, welches Objekt vom Benutzer am meisten kontaktiert wurde. Dieses Objekt ändert seine Farbe in grün.

In diesem Kurs erfahren Sie, wie Sie die Ergebnisse aus dem Application Insights-Dienst in einer Unity-basierten Beispielanwendung erhalten. Sie müssen diese Konzepte auf eine benutzerdefinierte Anwendung anwenden, die Sie möglicherweise aufbauen.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> Mr und Azure 309: Application Insights</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Dieser Kurs konzentriert sich in erster Linie auf Windows Mixed Reality immersive (VR)-Headsets, aber Sie können auch das, was Sie in diesem Kurs lernen, auf Microsoft hololens anwenden. Wenn Sie den Kurs befolgen, finden Sie Hinweise zu allen Änderungen, die Sie möglicherweise zur Unterstützung von hololens verwenden müssen. Wenn Sie hololens verwenden, bemerken Sie möglicherweise bei der sprach Erfassung einen Echo.

## <a name="prerequisites"></a>Vorraussetzungen

> [!NOTE]
> Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen. Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Juli 2018). Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](install-the-tools.md) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt werden.

Für diesen Kurs empfehlen wir die folgende Hardware und Software:

- Einen Entwicklungs-PC, der [mit der Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for Immersive (VR)-Headset-Entwicklung kompatibel ist
- [Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus](install-the-tools.md#installation-checklist)
- [Das neueste Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Ein [Windows Mixed Reality-Headset (VR)](immersive-headset-hardware-details.md) oder [Microsoft hololens](hololens-hardware-details.md) mit aktiviertem Entwicklermodus
- Eine Reihe von Kopfhörern mit einem integrierten Mikrofon (wenn das Headset nicht über eine integrierte Mic-und-sprechenden verfügt)
- Internet Zugriff für Azure-Setup und Application Insights Datenabruf

## <a name="before-you-start"></a>Bevor Sie beginnen

Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).

> [!WARNING] 
> Beachten Sie, dass die Daten, die *Application Insights* werden, Zeit in Rechnung stellen. Wenn Sie überprüfen möchten, ob der Dienst Ihre Daten empfangen hat, finden Sie in [Kapitel 14](#chapter-14---the-application-insights-service-portal)Weitere Informationen zum Navigieren im Portal.

## <a name="chapter-1---the-azure-portal"></a>Kapitel 1: Azure-Portal

Um *Application Insights*verwenden zu können, müssen Sie im Azure-Portal einen *Application Insights-Dienst* erstellen und konfigurieren.

1.  Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

    > [!NOTE]
    > Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen. Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.

2.  Wenn Sie angemeldet sind, klicken Sie in der oberen linken Ecke auf **neu** , suchen Sie nach *Application Insights*, und drücken Sie die **Eingabe**Taste.

    > [!NOTE]
    > Das Wort **New** wurde möglicherweise durch **Create a Resource**in neueren Portalen ersetzt.

    ![Azure-Portal](images/AzureLabs-Lab309-01.png)

3.  Die neue Seite auf der rechten Seite enthält eine Beschreibung des *Azure-Anwendung Insights* -Dienstanbieter. Klicken Sie unten links auf dieser Seite auf die Schaltfläche **Erstellen** , um eine Verknüpfung mit diesem Dienst zu erstellen.

    ![Azure-Portal](images/AzureLabs-Lab309-02.png)

4.  Nachdem Sie auf **Erstellen**geklickt haben, klicken Sie auf:

    1.  Fügen Sie den gewünschten **Namen** für diese Dienst Instanz ein.

    2.  Wählen Sie als **Anwendungstyp**die Option **Allgemein**aus.

    3.  Wählen Sie ein entsprechendes **Abonnement**aus.

    4.  Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** . Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Kursen) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5.  Wählen Sie einen **Speicherort**aus.

    6.  Außerdem müssen Sie bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.

    7.  Wählen Sie **Erstellen** aus.

        ![Azure-Portal](images/AzureLabs-Lab309-03.png)

5.  Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.

6.  Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Azure-Portal](images/AzureLabs-Lab309-04.png)

7.  Klicken Sie auf die Benachrichtigungen, um die neue Dienst Instanz zu untersuchen.

    ![Azure-Portal](images/AzureLabs-Lab309-05.png)

8.  Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen. Sie gelangen zu ihrer neuen *Application Insights Dienst* Instanz.

    ![Azure-Portal](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  Diese Webseite offen und leicht zugänglich zu machen, wird hier wieder häufig angezeigt, um die gesammelten Daten anzuzeigen.

    > [!IMPORTANT]
    > Zum Implementieren von Application Insights müssen drei (3) spezifische Werte verwendet werden: **Instrumentierungs Schlüssel**, **Anwendungs-ID**und **API-Schlüssel**. Unten sehen Sie, wie Sie diese Werte von Ihrem Dienst abrufen. Achten Sie darauf, diese Werte auf einer leeren *Notepad* -Seite zu notieren, da Sie Sie bald in Ihrem Code verwenden werden.

9.  Um den **Instrumentierungs Schlüssel**zu suchen, müssen Sie einen Bildlauf nach unten in der Liste der Dienstfunktionen durchführen und auf **Eigenschaften**klicken. auf der angezeigten Registerkarte wird der **Dienst Schlüssel**angezeigt.

    ![Azure-Portal](images/AzureLabs-Lab309-07.png)

10. Unter den folgenden **Eigenschaften**finden Sie den **API-Zugriff**, auf den Sie klicken müssen. Im Bereich auf der rechten Seite wird die **Anwendungs-ID** Ihrer APP bereitgestellt.

    ![Azure-Portal](images/AzureLabs-Lab309-08.png)

11. Wenn der Bereich **Anwendungs-ID** weiterhin geöffnet ist, klicken Sie auf API- **Schlüssel erstellen**. Dadurch wird der Bereich *API-Schlüssel erstellen* geöffnet.

    ![Azure-Portal](images/AzureLabs-Lab309-09.png)

12. Geben Sie im jetzt geöffneten Bereich *API-Schlüssel erstellen* eine Beschreibung ein, und klicken Sie auf **die drei Felder**.

13. Klicken Sie auf **Schlüssel generieren**. Ihr **API-Schlüssel** wird erstellt und angezeigt. 

    ![Azure-Portal](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > Dies ist der einzige Zeitpunkt, an dem der **Dienst Schlüssel** angezeigt wird. Stellen Sie also sicher, dass Sie jetzt eine Kopie erstellen.

## <a name="chapter-2---set-up-the-unity-project"></a>Kapitel 2: Einrichten des Unity-Projekts

Im folgenden finden Sie eine typische Einrichtung für die Entwicklung mit gemischter Realität und eine gute Vorlage für andere Projekte.

1.  Öffnen Sie *Unity* , und klicken Sie auf **neu**.

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-11.png)

2.  Sie müssen nun einen Unity-Projektnamen angeben und **\_\_Azure\_Application Insights**einfügen. Stellen Sie sicher, dass die *Vorlage* auf **3D**festgelegt ist. Legen Sie den Speicherort auf einen geeigneten *Speicherort* fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind). Klicken Sie dann auf **Projekt erstellen**.

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-12.png)

3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist. Wechseln Sie **zu \> Einstellungen bearbeiten** , und navigieren Sie dann im neuen Fenster zu **externe Tools**. Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**. Schließen Sie das Fenster " **Einstellungen** ".

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-13.png)

4.  Navigieren Sie als nächstes **zu \> dateibuildeinstellungen** , und schalten Sie die Plattform auf **universelle Windows-Plattform**, indem Sie auf die Schaltfläche **Plattform wechseln** klicken.

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-14.png)

5.  Wechseln Sie **zu \> dateibuildeinstellungen** , und stellen Sie Folgendes sicher:

    1.  Das **Zielgerät** ist auf **ein beliebiges Gerät** festgelegt.

        > Legen Sie für Microsoft hololens das **Zielgerät** auf *hololens*fest.

    2.  Der Buildtyp ist auf **D3D** festgelegt.

    3.  **SDK** ist auf **neueste installierte** Version festgelegt.

    4.  **Build und Run** sind auf **lokaler Computer** festgelegt.

    5.  Speichern Sie die Szene, und fügen Sie Sie dem Build hinzu.

        1.  Wählen Sie hierzu die Option **geöffnete Szenen hinzufügen**aus. Ein Fenster zum Speichern wird angezeigt.

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-15.png)

        2. Erstellen Sie einen neuen Ordner für dieses und jede zukünftige Szene, und klicken Sie dann auf die Schaltfläche **neuer Ordner** , um einen neuen Ordner zu **erstellen.**

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-16.png)

        3. Öffnen Sie den neu erstellten Ordner **Szenen** , geben Sie im Feld *Dateiname:* Text den Text **applicationinsightsscene**ein, und klicken Sie dann auf **Speichern**.

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-17.png)

6.  Die restlichen Einstellungen in denBuildeinstellungen sollten vorerst als Standard belassen werden.

7.  Klicken Sie im Fenster Buildeinstellungen auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der **Inspektor** befindet.

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-18.png)

8. In diesem Bereich müssen einige Einstellungen überprüft werden:

    1.  Auf der Registerkarte **andere Einstellungen** :

        1.  **Skript** Erstellung Die **Lauf Zeit Version** sollte experimentell sein **(.NET 4,6-Entsprechung)** , wodurch der Editor neu gestartet werden muss.

        2.  **Skript** -Back-End sollte **.net** sein

        3.  **API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-19.png)

    2.  Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:

        - **Internet Client deklarieren**     

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-20.png)

    3.  Weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), **unterstützt Tick Virtual Reality**, stellen Sie sicher, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-21.png)

9.  Wieder inden Buildeinstellungen ist **Unity C# -Projekte** nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen neben this.

10.  Schließen Sie das Fenster mit den Buildeinstellungen.

11.  Speichern Sie Ihre Szene und Ihr Projekt (**Datei** > **Speichern/Datei** > **speichern Projekt**).


## <a name="chapter-3---import-the-unity-package"></a>Kapitel 3: Importieren des Unity-Pakets

> [!IMPORTANT]
> Wenn Sie die *Unity-Setup* Komponenten dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie dieses [Azure-Mr-309. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage)herunterladen und es als [**benutzerdefiniertes Paket**](https://docs.unity3d.com/Manual/AssetPackages.html)in das Projekt importieren. Dies enthält auch die DLLs aus dem nächsten Kapitel. Fahren Sie nach dem Import aus [**Kapitel 6**](#chapter-6---create-the-applicationinsightstracker-class)fort.

> [!IMPORTANT]
> Um Application Insights in Unity verwenden zu können, müssen Sie die DLL für diese zusammen mit der newtonsoft-dll importieren. Zurzeit gibt es ein bekanntes Problem in Unity, das erfordert, dass Plug-ins nach dem Importieren neu konfiguriert werden. Diese Schritte (4-7 in diesem Abschnitt) werden nicht mehr benötigt, nachdem der Fehler behoben wurde.

Wenn Sie Application Insights in Ihr eigenes Projekt importieren möchten, stellen Sie sicher, dass Sie [das ". unitypackage" heruntergeladen haben, das die](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage)Plug-Ins enthält. Gehen Sie dann wie folgt vor:

1.  Fügen Sie das **. unitypackage** zu Unity hinzu, indem Sie die Menüoption **Assets \> Import \> Package Custom Package** verwenden.

2.  Vergewissern Sie sich, dass im Feld **Unity-Paket importieren** , das angezeigt wird, alles unter (und **einschließlich) Plug** -ins ausgewählt ist.

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-22.png)

3.  Klicken Sie auf die Schaltfläche **importieren** , um die Elemente Ihrem Projekt hinzuzufügen.

4.  Wechseln Sie in der Projektansicht **unter Plug** -in zum Ordner **Insights** , und wählen Sie *nur*die folgenden Plug-ins aus:

    -   Microsoft. applicationinsights

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-23.png)

5.  Wenn dieses *Plug* -in ausgewählt ist, **Stellen Sie sicher**, dass **alle Plattformen** deaktiviert **sind, und**stellen Sie sicher, dass **wsaplayer** **ebenfalls deaktiviert**ist. Hierdurch wird lediglich bestätigt, dass die Dateien ordnungsgemäß konfiguriert sind.

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > Wenn Sie die Plug-ins wie diese markieren, werden diese so konfiguriert, dass Sie nur im Unity-Editor verwendet werden. Der WSA-Ordner enthält einen anderen Satz von DLLs, die nach dem Exportieren des Projekts aus Unity verwendet werden.

6.  Im nächsten Schritt müssen Sie den Ordner " **WSA** " im Ordner " **Insights** " öffnen. Es wird eine Kopie derselben Datei angezeigt, die Sie soeben konfiguriert haben. Wählen Sie diese Datei aus, und vergewissern Sie sich dann im Inspektor, dass **alle Plattformen** deaktiviert sind. Stellen Sie dann sicher, dass **nur** **wsaplayer** **aktiviert**ist. Klicken Sie auf **Übernehmen**.

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-25.png)

7. Nun müssen Sie die **Schritte 4-6**ausführen, aber für die *newtonsoft* -Plug-ins. Sehen Sie sich den folgenden Screenshot an, um zu sehen, wie das Ergebnis aussehen sollte.

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a>Kapitel 4: Einrichten der Kamera-und Benutzer Steuerelemente

In diesem Kapitel richten Sie die Kamera und die Steuerelemente ein, um dem Benutzer zu ermöglichen, die Szene anzuzeigen und zu verschieben.

1.  Klicken Sie mit der rechten Maustaste in einen leeren Bereich im Bereich Hierarchie, und klicken Sie dann auf**leere** **Erstellen** > .

    ![Richten Sie die Kamera und die Benutzer Steuerelemente ein.](images/AzureLabs-Lab309-26.png)

2.  Benennen Sie das neue leere gameobject in das über **geordnete**Element um.

    ![Richten Sie die Kamera und die Benutzer Steuerelemente ein.](images/AzureLabs-Lab309-27.png)

3.  Klicken Sie mit der rechten Maustaste in einen leeren Bereich im Bereich Hierarchie, und klicken Sie dann auf **3D-Objekt**und dann auf **Kugel**.

4.  Benennen Sie die Kugel in den **rechten**Bereich um.

5.  Legen Sie die **Transformations Skala** der rechten Seite auf **0,1, 0,1, 0,1**

    ![Richten Sie die Kamera und die Benutzer Steuerelemente ein.](images/AzureLabs-Lab309-28.png)

6.  Entfernen Sie die **Kugel-Collider** -Komponente von der rechten Seite, indem Sie auf das **Zahnrad** in der *Kugel-Collider* -Komponente klicken, und entfernen Sie dann die **Komponente**.

    ![Richten Sie die Kamera und die Benutzer Steuerelemente ein.](images/AzureLabs-Lab309-29.png)

7.  Ziehen Sie im Hierarchie Panel die **Hauptkamera** und die **Rechte Seite** auf das über **geordnete Kamera** Objekt.

    ![Richten Sie die Kamera und die Benutzer Steuerelemente ein.](images/AzureLabs-Lab309-30.png)

8.  Legen Sie die **Transformations Position** der **Hauptkamera** und des **rechten** Objekts auf **0, 0, 0**fest.

    ![Richten Sie die Kamera und die Benutzer Steuerelemente ein.](images/AzureLabs-Lab309-31.png)

    ![Richten Sie die Kamera und die Benutzer Steuerelemente ein.](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a>Kapitel 5: Einrichten der Objekte in der Unity-Szene

Sie werden nun einige grundlegende Formen für Ihre Szene erstellen, mit denen der Benutzer interagieren kann.

1.  Klicken Sie mit der rechten Maustaste in einen leeren Bereich im *Hierarchie Panel*, und wählen Sie dann auf dem **3D-Objekt**die Option **Ebene**aus.

2.  Legen Sie die **Position** der Ebene Transformation auf **0,-1, 0**fest.

3.  Legen Sie für die Ebene **Transform Scale** den Wert **5, 1, 5**fest.

    ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-33.png)

4.  Erstellen Sie ein grundlegendes Material, das Sie mit dem **Plane** -Objekt verwenden können, damit die anderen Formen leichter zu sehen sind. Navigieren Sie zum *Projekt Panel*, klicken Sie mit der rechten Maustaste, klicken Sie dann auf **Erstellen**und dann auf **Ordner**, um einen neuen Ordner zu erstellen. Nennen Sie es **Material**.

    ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-34.png) ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-35.png)

5.  Öffnen Sie den Ordner **Material** , klicken Sie mit der rechten Maustaste auf, klicken Sie auf **Erstellen**und dann auf **Material**, um ein neues Material zu erstellen. Nennen Sie es **Blue**.

    ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-36.png) ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-37.png)

6.  Wenn das neue **blaue** Material ausgewählt ist, schauen Sie sich den *Inspektor*an, und klicken Sie auf das rechteckige Fenster neben **Albedo**. Wählen Sie eine blaue Farbe aus (die folgende Abbildung **ist eine hexadezimale Farbe: \#3592FFFF**). Nachdem Sie ausgewählt haben, klicken Sie auf die Schaltfläche Schließen.

    ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-38.png)

7.  Ziehen Sie das neue Material aus dem Ordner **Material** in die neu erstellte **Ebene**innerhalb Ihrer Szene (oder legen Sie es auf dem **Ebene** -Objekt in der *Hierarchie*ab).

    ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-39.png)

8.  Klicken Sie mit der rechten Maustaste auf einen leeren Bereich im *Hierarchie Panel*und dann auf **3D-Objekt, Kapsel**.

    -  Wenn die **Kapsel** ausgewählt ist, ändern Sie die **Transformations** *Position* in: **-10, 1, 0**.

9.  Klicken Sie mit der rechten Maustaste in einen leeren Bereich im Bereich *Hierarchie*, und klicken Sie dann auf **3D-Objekt, Cube**.

    -  Ändern Sie mit ausgewähltem **Cube** die **Transformations** *Position* in: **0, 0, 10**.

10. Klicken Sie mit der rechten Maustaste auf einen leeren Bereich im *Hierarchie Panel*und dann auf **3D-Objekt, Kugel**.

    -  Wenn die **Kugel** ausgewählt ist, ändern Sie die zugehörige **Transformations** *Position* in: **10, 0, 0**.

    ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > Bei diesen *Positions* Werten handelt es sich um *Vorschläge*. Sie können die Positionen der Objekte auf beliebige Weise festlegen, obwohl es für den Benutzer der Anwendung einfacher ist, wenn die Objekt Abstände nicht zu weit von der Kamera stammen.

11. Wenn die Anwendung ausgeführt wird, muss Sie in der Lage sein, die Objekte innerhalb der Szene zu identifizieren, um dies zu erreichen, müssen Sie gekennzeichnet werden. Wählen Sie eines der Objekte aus, und klicken Sie im *Inspektor* -Panel auf **Tag hinzufügen...** . Dadurch wird der *Inspektor* mit dem Bereich **Tags & Ebenen** ausgetauscht.

    ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-41.png)![](images/AzureLabs-Lab309-42.png)

12. Klicken Sie auf das Symbol **+ (plus)** , und geben Sie dann den Tagnamen als **objectinscene**ein.

    ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > Wenn Sie einen anderen Namen für das Tag verwenden, müssen Sie sicherstellen, dass diese Änderung auch die Skripts " *datafromanalytics*", " *objecttrigger*" und " *Gaze*" erstellt, damit Ihre Objekte in Ihrer Szene gefunden und erkannt werden.

13. Nachdem Sie das Tag erstellt haben, müssen Sie es auf alle drei Objekte anwenden. Halten Sie in der *Hierarchie*die **UMSCHALT** Taste gedrückt, und klicken Sie dann auf die **Kapsel**, den **Cube**und die **Kugel**, und klicken Sie dann im *Inspektor*auf das Dropdown Menü neben **Tag**und dann auf *objectinscene* . Tag, das Sie erstellt haben.

    ![Einrichten der Objekte in der Unity-Szene](images/AzureLabs-Lab309-44.png)![](images/AzureLabs-Lab309-45.png)

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a>Kapitel 6: Erstellen der applicationinsightstracker-Klasse

Das erste Skript, das Sie erstellen müssen, ist **applicationinsightstracker**, das für Folgendes zuständig ist:

1.  Erstellen von Ereignissen auf der Grundlage von Benutzerinteraktionen, um Azure-Anwendung Einblicke zu senden.

2. Erstellen geeigneter Ereignis Namen, abhängig von der Benutzerinteraktion.

3. Ereignisse werden an die Application Insights-Dienst Instanz übermittelt.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste im *Projekt Panel*, und **Erstellen** > Sie dann den**Ordner**. Benennen Sie den Ordner mit **Skripts**.

    ![Erstellen der applicationinsightstracker-Klasse](images/AzureLabs-Lab309-46.png)  ![Erstellen der applicationinsightstracker-Klasse](images/AzureLabs-Lab309-47.png)

2.  Doppelklicken Sie nach dem Erstellen des **Skripts** auf den Ordner, um zu öffnen. Klicken Sie dann in diesem Ordner mit der rechten Maustaste auf **C# Skript** **Erstellen**  >  . Nennen Sie das Skript **applicationinsightstracker**.

3.  Doppelklicken Sie auf das neue **applicationinsightstracker** -Skript, um es in **Visual Studio**zu öffnen.

4.  Aktualisieren Sie die Namespaces oben im Skript so, dass Sie wie folgt lauten:

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  Fügen Sie in der-Klasse die folgenden Variablen ein:

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > Legen Sie die Werte **instrumentationkey, ApplicationId und API_Key** entsprechend fest, indem Sie die *Dienst Schlüssel* aus dem Azure-Portal verwenden, wie in [Kapitel 1](#chapter-1---the-azure-portal), Schritt 9 weiter oben beschrieben.

6.  Fügen Sie dann die Methoden **Start ()** und **Awa()** hinzu, die aufgerufen werden, wenn die Klasse initialisiert:

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  Fügen Sie die Methoden hinzu, die für das Senden der von Ihrer Anwendung registrierten Ereignisse und Metriken verantwortlich sind:

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.

## <a name="chapter-7---create-the-gaze-script"></a>Kapitel 7: Erstellen des Blick Schrift Skripts

Das nächste Skript, das erstellt werden soll, ist das **Gaze** -Skript. Dieses Skript ist dafür verantwortlich, ein *raycast* zu erstellen, das von der *Hauptkamera*projiziert wird, um zu erkennen, welches Objekt der Benutzer untersucht. In diesem Fall muss der *raycast* ermitteln, ob der Benutzer ein Objekt mit dem Objekt " **objectinscene** " prüft, und dann zählen, wie lange der *Benutzer an diesem* Objekt mitnimmt.

1.  Doppelklicken Sie auf den Ordner **Skripts** , um ihn zu öffnen.

2.  Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf **C# Skript** **Erstellen**  >  . Benennen Sie das **Skript mit**dem Namen.

3.  Doppelklicken Sie auf das Skript, um es in Visual Studio zu öffnen.

4.  Ersetzen Sie den vorhandenen Code durch folgenden Code:

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  Der Code für die Methoden " **Awake ()** " und " **Start ()** " muss nun hinzugefügt werden.

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  Fügen Sie in der " **Blick** "-Klasse den folgenden Code in der **Update ()** -Methode hinzu, um ein *raycast* zu projizieren und den zieltreffer zu erkennen:

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  Fügen Sie die **resetfocusedobject ()** -Methode hinzu, um Daten an **Application Insights** zu senden, wenn der Benutzer ein Objekt betrachtet hat.

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  Sie haben **nun das Skript** Skript abgeschlossen. Speichern Sie die Änderungen in *Visual Studio* , bevor Sie zu *Unity*zurückkehren.

## <a name="chapter-8---create-the-objecttrigger-class"></a>Kapitel 8: Erstellen der objecttrigger-Klasse

Das nächste Skript, das Sie erstellen müssen, ist **objecttrigger**, das für Folgendes zuständig ist:

- Hinzufügen von Komponenten, die für die Kollision auf der Hauptkamera erforderlich sind
- Erkennen, ob sich die Kamera in der Nähe eines Objekts befindet, das als **objectinscene**gekennzeichnet ist

So erstellen Sie das Skript:

1.  Doppelklicken Sie auf den Ordner **Skripts** , um ihn zu öffnen.

2.  Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf **C# Skript** **Erstellen**  >  . Benennen Sie das Skript **objecttrigger**.

3.  Doppelklicken Sie auf das Skript, um es in Visual Studio zu öffnen. Ersetzen Sie den vorhandenen Code durch folgenden Code:

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.

## <a name="chapter-9---create-the-datafromanalytics-class"></a>Kapitel 9: Erstellen der datafromanalytics-Klasse

Sie müssen nun das **datafromanalytics** -Skript erstellen, das für Folgendes zuständig ist:

- Das Abrufen von Analysedaten über das Objekt, das von der Kamera am meisten angegangen wurde.
- Mithilfe der *Dienst Schlüssel*, die die Kommunikation mit ihrer Azure-Anwendung Insights-Dienst Instanz ermöglichen.
- Sortieren der Objekte in der Szene, je nachdem, welche die höchste Ereignis Anzahl aufweist.
- Ändern der Material Farbe des am häufigsten angenäherten Objekts in *grün*.

So erstellen Sie das Skript:

1.  Doppelklicken Sie auf den Ordner **Skripts** , um ihn zu öffnen.

2.  Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf **C# Skript** **Erstellen**  >  . Benennen Sie das Skript " **datafromanalytics**".

3.  Doppelklicken Sie auf das Skript, um es in Visual Studio zu öffnen.

4.  Fügen Sie die folgenden Namespaces ein:

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Fügen Sie im Skript Folgendes ein:

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  Fügen Sie innerhalb der **datafromanalytics** -Klasse direkt nach der **Start ()** -Methode die folgende Methode namens **fetchanalytics ()** hinzu. Diese Methode ist für das Auffüllen der Liste der Schlüssel-Wert-Paare mit einem *gameobject-Objekt* und einer Platzhalter Ereignis Anzahl verantwortlich. Anschließend wird die " **GetWebRequest ()** "-Coroutine initialisiert. Die Abfrage Struktur des aufzurufenden *Application Insights* kann in dieser Methode auch als Endpunkt der *Abfrage-URL* gefunden werden.

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  Fügen Sie direkt unterhalb der **fetchanalytics ()** -Methode eine Methode namens **GetWebRequest ()** hinzu, die einen *IEnumerator*zurückgibt. Diese Methode ist dafür verantwortlich, wie oft ein Ereignis, das einem bestimmten *gameobject*entspricht, in *Application Insights*aufgerufen wurde. Wenn alle gesendeten Abfragen zurückgegeben wurden, wird die **determinewinner ()** -Methode aufgerufen.

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readibility).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  Die nächste Methode ist " **determinewinner ()** ", die die Liste der *gameobject* -und *int* -Paare entsprechend der höchsten Ereignis Anzahl sortiert. Anschließend wird die Material Farbe dieses *gameobject* in *grün* geändert (als Feedback für die Anwendung mit der höchsten Anzahl). Dadurch wird eine Meldung mit den Analyseergebnissen angezeigt.

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  Fügen Sie die Klassenstruktur hinzu, die zum Deserialisieren des JSON-Objekts verwendet wird, das von *Application Insights*empfangen wird. Fügen Sie diese Klassen ganz unten in der **datafromanalytics** -Klassendatei **außerhalb** der Klassendefinition hinzu.

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.

## <a name="chapter-10---create-the-movement-class"></a>Kapitel 10: Erstellen der Bewegungs Klasse

Das **Verschiebungs Skript ist** das nächste Skript, das Sie erstellen müssen. Er ist für Folgendes zuständig:

- Verschieben der Hauptkamera entsprechend der Richtung, in der die Kamera aussieht.
- Hinzufügen aller anderen Skripts zu Scene-Objekten.

So erstellen Sie das Skript:

1.  Doppelklicken Sie auf den Ordner **Skripts** , um ihn zu öffnen.

2.  Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf **C# Skript** **Erstellen**  >  . Benennen Sie das **Skript.**

3.  Doppelklicken Sie auf das Skript, um es in *Visual Studio*zu öffnen.

4.  Ersetzen Sie den vorhandenen Code durch folgenden Code:

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  Fügen Sie innerhalb der **Movement** -Klasse *unter* der leeren **Update ()** -Methode die folgenden Methoden ein, die dem Benutzer die Verwendung des Hand Controllers zum Verschieben im virtuellen Bereich ermöglichen:

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  Fügen Sie schließlich den Methoden aufrufin der **Update ()** -Methode hinzu.

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.

## <a name="chapter-11---setting-up-the-scripts-references"></a>Kapitel 11: Einrichten der Skripts Verweise

In diesem Kapitel müssen Sie das **Bewegungs** Skript auf der über **geordneten Kamera** platzieren und dessen Verweis Ziele festlegen. Dieses Skript behandelt dann das Platzieren der anderen Skripts, wenn Sie es benötigen.

1.  Ziehen Sie im Ordner "Skripts" im *Projekt Panel*das **Bewegungs** Skript in das über **geordnete Kamera** Objekt, das sich im Bereich *Hierarchie*befindet.

    ![Einrichten der Skripts Verweise in der Unity-Szene](images/AzureLabs-Lab309-48.png)

2.  Klicken Sie auf die über **geordnete Kamera**. Ziehen Sie im Bereich *Hierarchie*das **Rechte** Objekt aus dem Bereich *Hierarchie* in das Verweis Ziel, **Controller**, im *Inspektor-Panel*. Legen Sie die **Benutzer Geschwindigkeit** auf **5**fest, wie in der folgenden Abbildung dargestellt.

    ![Einrichten der Skripts Verweise in der Unity-Szene](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a>Kapitel 12: Erstellen des Unity-Projekts

Alles, was für den Unity-Abschnitt dieses Projekts erforderlich ist, ist nun abgeschlossen, sodass es an der Zeit ist, Sie aus Unity zu erstellen.

1.  Navigieren Siezu den Buildeinstellungen (dateibuildeinstellungen > ).

2.  Klicken Sie im Fenster "Buildeinstellungen" auf " **Erstellen**".

    ![Erstellen des Unity-Projekts in der UWP-Lösung](images/AzureLabs-Lab309-50.png)

3.  Ein **Datei-Explorer** -Fenster wird angezeigt, in dem Sie aufgefordert werden, einen Speicherort für den Build zu erhalten. Erstellen Sie einen neuen Ordner (indem Sie in der oberen linken Ecke auf **neuer Ordner** klicken), und nennen Sie ihn " **BUILDS**".

    ![Erstellen des Unity-Projekts in der UWP-Lösung](images/AzureLabs-Lab309-51.png)

    1.  Öffnen Sie den Ordner neue **BUILDS** , und erstellen Sie einen weiteren Ordner (mehr als einen **neuen Ordner** ), und **\_benennen\_Sie\_ihn mit Azure Application Insights**.

        ![Erstellen des Unity-Projekts in der UWP-Lösung](images/AzureLabs-Lab309-52.png)

    2.  Klicken Sie bei ausgewähltem Ordner " **\_\_AzureApplicationInsights" auf Ordner auswählen.\_** Es dauert eine Minute, bis das Projekt erstellt wird.

4.  Im folgenden *Build*wird der **Datei-Explorer** angezeigt, in dem der Speicherort des neuen Projekts angezeigt wird.

## <a name="chapter-13---deploy-mr_azure_application_insights-app-to-your-machine"></a>Kapitel 13: Bereitstellen der MR_Azure_Application_Insights-App auf Ihrem Computer

So stellen Sie **die\_Azure\_Application\_Insights** -App auf Ihrem lokalen Computer bereit:

1.  Öffnen Sie die Projektmappendatei Ihrer **\_Azure\_\_Application Insights** -app in **Visual Studio**.

2.  Wählen Sieauf der Projektmappenplattform die Option **x86, lokaler Computer**aus.

3.  Wählen Sie in der Projektmappenkonfiguration **Debuggen**.

    ![Erstellen des Unity-Projekts in der UWP-Lösung](images/AzureLabs-Lab309-53.png)

4.  Wechseln Sie zum **Menü Erstellen** , und klicken Sie auf **Lösung** bereitstellen, um die Anwendung auf Ihren Computer zu übertragen.

5.  Ihre APP sollte nun in der Liste der installierten apps angezeigt werden, die gestartet werden können.

6. Starten Sie die Mixed Reality-Anwendung.

7. Bewegen Sie sich um die Szene, sehen Sie sich die Objekte an, und sehen Sie sich diese an, wenn der *Azure Insight-Dienst* genügend Ereignisdaten gesammelt hat, legt er das Objekt fest, das am höchsten grün ist.

> [!IMPORTANT] 
> Die durchschnittliche Wartezeit für die vom Dienst zu erfassenden *Ereignisse und Metriken* dauert etwa 15 Minuten, in manchen Fällen kann es jedoch bis zu einer Stunde dauern.

## <a name="chapter-14---the-application-insights-service-portal"></a>Kapitel 14: das Application Insights Service-Portal

Nachdem Sie die Szene gewechselt und mit mehreren Objekten zusammengeführt haben, können Sie die im *Application Insights Service* -Portal gesammelten Daten sehen.

1.  Wechseln Sie zurück zu Ihrem Application Insights Service-Portal.

2.  Klicken Sie auf *Metrik-Explorer*.

    ![Überprüfen der gesammelten Daten](images/AzureLabs-Lab309-54.png)

3.  Es wird auf einer Registerkarte geöffnet, die das Diagramm enthält, das die *Ereignisse und Metriken* für Ihre Anwendung darstellt. Wie bereits erwähnt, kann es einige Zeit dauern (bis zu 1 Stunde), bis die Daten im Diagramm angezeigt werden.

    ![Überprüfen der gesammelten Daten](images/AzureLabs-Lab309-55.png)

4.  Klicken Sie auf die *Ereignis Leiste* in der *Gesamtanzahl der Ereignisse* nach Anwendungs Version, um eine detaillierte Aufschlüsselung der Ereignisse mit ihren Namen anzuzeigen.

    ![Überprüfen der gesammelten Daten](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a>Ihre Application Insights Service-Anwendung wurde beendet.

Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die den Application Insights-Dienst nutzt, um die Aktivität des Benutzers in Ihrer APP zu überwachen.

![Kurs Ergebnis](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a>Bonus Übungen

**Übung 1**

Versuchen Sie, die objectinscene-Objekte zu erstellen, anstatt Sie manuell zu erstellen, und legen Sie Ihre Koordinaten auf der Ebene innerhalb Ihrer Skripts fest. Auf diese Weise könnten Sie Azure das am häufigsten verwendete Objekt (aus Blick auf das Ergebnis oder die Near-Ergebnisse) Fragen und ein *zusätzliches* von diesen Objekten erzeugen.

**Übung 2**

Sortieren Sie Ihre Application Insights Ergebnisse nach Zeit, damit Sie die relevantesten Daten erhalten, und implementieren Sie diese zeitsensiblen Daten in der Anwendung.

