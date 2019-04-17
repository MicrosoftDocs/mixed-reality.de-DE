---
title: MR und Azure 309 – Application insights
description: Führen Sie diesen Kurs Informationen zum Sammeln von Analysen in Bezug auf das Benutzerverhalten innerhalb einer mixed Reality-Anwendung, die mithilfe von Azure Application Insights-Diensts.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorials, api, Application Insights, Hololens, immersive vr
ms.openlocfilehash: 838dbe38724d29f4c5987e2f6ac7a07231015c82
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604774"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

<br> 

# <a name="mr-and-azure-309-application-insights"></a>MR und Azure 309: Application insights

![Endprodukt-starten](images/AzureLabs-Lab309-00.png)

In diesem Kurs erfahren Sie zum Hinzufügen von Application Insights-Funktionen einer mixed Reality-Anwendung mithilfe der Azure Application Insights-API zum Sammeln von Analysen in Bezug auf das Benutzerverhalten.

Application Insights ist ein Microsoft-Dienst, sodass Entwickler Analysedaten aus ihren Anwendungen erfassen und verwalten sie über ein Portal leicht zu bedienende. Die Analyse kann von der Leistung, um benutzerdefinierte Informationen sein, die Sie sammeln möchten. Weitere Informationen finden Sie auf die [Application Insights-Seite](https://azure.microsoft.com/services/application-insights/).

Nach Abschluss dieses Kurses, verfügen Sie über ein mixed Reality immersive Kopfhörer Anwendung die können die folgenden Schritte ausführen:

1.  Ermöglicht dem Benutzer bestaunen und eine Szene verschieben.
2.  Lösen Sie das Senden von Analytics, um die *Application Insights-Dienst*, durch die Verwendung von Blicke und NEAR-Scene-Objekten.
3.  Die app wird auch aufrufen, auf den Dienst, Abrufen von Informationen, die am häufigsten durch den Benutzer dazu, welche wurde innerhalb der letzten 24 Stunden erreicht werden. Dieses Objekt wird dessen Farbe in Grün geändert.

In diesem Kurs erfahren Sie, wie die Ergebnisse aus den Application Insights-Dienst in eine Unity-basierten Anwendung zu erhalten. Sie werden sich entscheiden, ob Sie diese Konzepte, die Sie erstellen eine benutzerdefinierte Anwendung zuweisen.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td> MR und Azure 309: Application insights</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Während dieser Kurs in erster Linie für immersive Windows Mixed Reality (VR)-Headsets ausgerichtet ist, können Sie auch anwenden, was Sie in diesem Kurs, Microsoft HoloLens lernen. Wie Sie den Kurs halten, sehen Anmerkungen zu dieser Version auf Änderungen Sie möglicherweise zur Unterstützung von HoloLens einsetzen müssen. Wenn Sie HoloLens verwenden zu können, werden Sie einige Echo während der Sprachaufnahme feststellen.

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
- Eine Reihe von Kopfhörer mit ein eingebautes Mikrofon verfügen (wenn die Kopfhörer nicht über eine integrierte mic und die Lautsprecher verfügt)
- Zugriff auf das Internet für die Einrichtung von Azure und Abrufen von Application Insights-Daten

## <a name="before-you-start"></a>Bevor Sie beginnen

Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).

> [!WARNING] 
> Denken Sie daran, Daten, *Application Insights* Zeit in Anspruch nimmt daher etwas Geduld. Wenn Sie möchten überprüfen, ob der Dienst Ihre Daten erhalten hat, sehen Sie sich [Kapitel 14](#chapter-14---the-application-insights-service-portal), die erfahren Sie, wie im Portal navigieren.

## <a name="chapter-1---the-azure-portal"></a>Kapitel 1: das Azure-Portal

Verwendung von *Application Insights*, Sie benötigen zum Erstellen und Konfigurieren einer *Application Insights-Dienst* im Azure-Portal.

1.  Melden Sie sich bei der [Azure-Portal](https://portal.azure.com).

    > [!NOTE]
    > Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen. Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.

2.  Sobald Sie angemeldet sind, klicken Sie auf **neu** in der oberen linken Ecke, und suchen Sie nach *Application Insights*, und klicken Sie auf **EINGABETASTE**.

    > [!NOTE]
    > Das Wort **neu** wurden möglicherweise durch ersetzt **erstellen Sie eine Ressource**, in neueren-Portalen.

    ![Azure-Portal](images/AzureLabs-Lab309-01.png)

3.  Die neue Seite auf der rechten Seite bietet eine Beschreibung der *Azure Application Insights* Service. Unten links auf dieser Seite die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.

    ![Azure-Portal](images/AzureLabs-Lab309-02.png)

4.  Nachdem Sie auf geklickt haben **erstellen**:

    1.  Fügen Sie Ihre bevorzugte **Namen** für diese Dienstinstanz.

    2.  Als **Anwendungstyp**Option **allgemeine**.

    3.  Wählen Sie einen geeigneten **Abonnement**.

    4.  Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle zu bewahren, an die Azure-Dienste unter einer allgemeinen Ressourcengruppe mit einem einzelnen Projekt (z. B. z. B. diese Kurse) verknüpft ist).

        > Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, bitte [finden Sie im Artikel der Resource-Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5.  Wählen Sie eine **Speicherort**.

    6.  Sie müssen auch bestätigen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.

    7.  Wählen Sie **Erstellen** aus.

        ![Azure-Portal](images/AzureLabs-Lab309-03.png)

5.  Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.

6.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Azure-Portal](images/AzureLabs-Lab309-04.png)

7.  Klicken Sie auf die Benachrichtigungen an Ihre neue Dienstinstanz zu untersuchen.

    ![Azure-Portal](images/AzureLabs-Lab309-05.png)

8.  Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen. Sie gelangen in die neue *Application Insights-Dienst* Instanz.

    ![Azure-Portal](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  Lassen Sie die Seite geöffnet, und leicht zugänglich, Sie kommen hier häufig, um die gesammelten Daten finden Sie unter.

    > [!IMPORTANT]
    > Um Application Insights zu implementieren, müssen Sie drei (3) bestimmte Werte verwenden: **Instrumentierungsschlüssel**, **Anwendungs-ID**, und **API-Schlüssel**. Im folgenden sehen Sie, wie Sie diese Werte aus Ihrem Dienst abrufen. Achten Sie darauf, beachten Sie diese Werte auf einen leeren *Editor* Seite, da Sie bald in Ihrem Code verwendet werden.

9.  Finden der **Instrumentierungsschlüssel**, müssen Sie einen Bildlauf nach unten der Liste der Service-Funktionen, und klicken auf **Eigenschaften**, informiert, auf die Registerkarte angezeigt, die **Dienstschlüssel**.

    ![Azure-Portal](images/AzureLabs-Lab309-07.png)

10. Ein wenig unten **Eigenschaften**, finden Sie **API-Zugriff**, die Sie klicken müssen. Im Bereich rechts stellt die **Anwendungs-ID** Ihrer App.

    ![Azure-Portal](images/AzureLabs-Lab309-08.png)

11. Mit der **Anwendungs-ID** Bereich immer noch geöffnet ist, klicken Sie auf **API-Schlüssel erstellen**, wird geöffnet die *API-Schlüssel erstellen* Bereich.

    ![Azure-Portal](images/AzureLabs-Lab309-09.png)

12. In der jetzt eröffnet *API-Schlüssel erstellen* Bereich, und geben Sie eine Beschreibung und **aktivieren Sie die drei Felder**.

13. Klicken Sie auf **Schlüssel generieren**. Ihre **API-Schlüssel** wird erstellt und angezeigt. 

    ![Azure-Portal](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > Dies ist das einzige Mal Ihre **Dienstschlüssel** angezeigt wird, müssen Sie sicherstellen Sie jetzt eine Kopie der Datei vornehmen.

## <a name="chapter-2---set-up-the-unity-project"></a>Kapitel 2: Einrichten von Unity-Projekts

Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit dem mixed Reality und daher ist eine gute Vorlage für andere Projekte.

1.  Open *Unity* , und klicken Sie auf **neu**.

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-11.png)

2.  Sie müssen nun zum Bereitstellen eines Namen Unity-Projekt einfügen **MR\_Azure\_Anwendung\_Insights**. Stellen Sie sicher, dass die *Vorlage* nastaven NA hodnotu **3D**. Legen Sie die *Speicherort* auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser). Klicken Sie auf **projekterstellung**.

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-12.png)

3.  Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**. Wechseln Sie zu **bearbeiten \> Voreinstellungen** und navigieren Sie dann im neuen Fenster zu **externe Tools**. Änderung **externen Skript-Editors** zu **Visual Studio 2017**. Schließen der **Voreinstellungen** Fenster.

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-13.png)

4.  Öffnen Sie als Nächstes **Datei \> Buildeinstellungen** , und wechseln von der Plattform bereitgestellten **universelle Windows-Plattform**, durch Klicken auf die **Plattform wechseln** Schaltfläche.

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-14.png)

5.  Wechseln Sie zu **Datei \> Buildeinstellungen** und stellen Sie sicher, dass:

    1.  **Geräte** nastaven NA hodnotu **jedes Gerät**

        > Legen Sie für die Microsoft HoloLens **Zielgerät** zu *HoloLens*.

    2.  **Buildtyp** nastaven NA hodnotu **D3D**

    3.  **SDK** nastaven NA hodnotu **zuletzt installierte**

    4.  **Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**

    5.  Die Szene speichern und mit dem Build hinzugefügt werden.

        1.  Hierzu **öffnen Szenen hinzufügen**. Ein Speichern Fenster wird angezeigt.

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-15.png)

        2. Erstellen Sie einen neuen Ordner für dieses und alle zukünftigen Szene, und klicken Sie dann die **neuer Ordner** Schaltfläche zum Erstellen eines neuen Ordners, nennen Sie sie **Szenen**.

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-16.png)

        3. Öffnen Sie den neu erstellten **Szenen** Ordner, und klicken Sie dann in der *Dateiname:* Textfeld **ApplicationInsightsScene**, klicken Sie dann auf **Speichern**.

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-17.png)

6.  Die Einstellungen im verbleibenden **Buildeinstellungen**, sollte jetzt als Standard bleiben.

7.  In der **Buildeinstellungen** Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dadurch wird den entsprechenden Bereich geöffnet, im Bereich, in dem die **Inspektor** befindet.

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-18.png)

8. In diesem Bereich sind müssen einige Einstellungen überprüft werden:

    1.  In der **Weitere Einstellungen** Registerkarte:

        1.  **Scripting** **Laufzeitversion** muss **experimentell (.NET 4.6 Äquivalent)**, löst der Editor neu starten müssen.

        2.  **Back-End-Scripting** muss **.NET**

        3.  **API-Kompatibilitätsebene** muss **.NET 4.6**

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-19.png)

    2.  In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:

        - **InternetClient**     

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-20.png)

    3.  Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality SDK** hinzugefügt wird.

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab309-21.png)

9.  Im **Buildeinstellungen**, **Unity C\# Projekte** nicht mehr abgeblendet ist, aktivieren Sie das Kontrollkästchen neben dieser.

10.  Schließen Sie das Fenster "erstellen".

11.  Speichern Sie Ihre Szene und das Projekt (**Datei > Speichern SZENE / FILE > Speichern Projekt**).


## <a name="chapter-3---import-the-unity-package"></a>Kapitel 3: Importieren des Unity-Pakets

> [!IMPORTANT]
> Wenn Sie, überspringen möchten die *Unity einrichten* Komponenten dieser Kurs, und direkt in Code fortsetzen, können Sie zum Herunterladen [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), importieren Sie es in Ihr Projekt als eine [ **Anpassungspaket**](https://docs.unity3d.com/Manual/AssetPackages.html). Dies wird auch die DLLs aus dem nächsten Kapitel enthalten. Ist eine Fortsetzung nach dem Import, [ **Kapitel 6**](#chapter-6---create-the-applicationinsightstracker-class).

> [!IMPORTANT]
> Um Application Insights in Unity verwenden zu können, müssen Sie die DLL, und die Newtonsoft-DLL zu importieren. Es befindet sich derzeit ein bekanntes Problem in Unity-Plug-Ins neu konfiguriert werden, nach dem Import erfordert. Diese Schritte (4 bis 7 in diesem Abschnitt) ist nicht mehr erforderlich, nachdem der Fehler behoben wurde.

Um Application Insights in Ihrem eigenen Projekt zu importieren, stellen Sie sicher, dass [heruntergeladen haben die ".unitypackage", die Plug-Ins mit](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage). Führen Sie anschließend folgende Schritte aus:

1.  Hinzufügen der **.unitypackage** in Unity mithilfe der **Assets \> Paket importieren \> Custom Package** Option des Menüs.

2.  In der **Unity-Paket importieren** , ruft Sie Vergewissern Sie sich, alles, was unter (und einschließlich) **-Plug-Ins** ausgewählt ist.

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-22.png)

3.  Klicken Sie auf die **Import** , um die Elemente zu Ihrem Projekt hinzuzufügen.

4.  Wechseln Sie zu der **Insights** Unterordner **-Plug-Ins** im Projekt anzuzeigen, und wählen Sie die folgenden Plug-Ins *nur*:

    -   Microsoft.ApplicationInsights

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-23.png)

5.  Mit diesem *-Plug-Ins* ausgewählt haben, stellen sicher, dass **Any Platform** ist **deaktiviert**, klicken Sie dann sicher, dass **WSAPlayer** auch  **unchecked**, klicken Sie dann auf **übernehmen**. Dies ist, um sich zu vergewissern, dass die Dateien richtig konfiguriert sind.

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > Markieren die Plug-Ins wie folgt, konfiguriert sie nur im Unity-Editor verwendet werden. Es gibt ein anderen Satz von DLLs im Ordner "WSA" das verwendet werden soll, nachdem das Projekt aus Unity exportiert werden.

6.  Als Nächstes müssen Sie zum Öffnen der **WSA** Ordner, der innerhalb der **Insights** Ordner. Daraufhin wird eine Kopie der gleichen Datei, die Sie gerade konfiguriert haben. Wählen Sie diese Datei, und klicken Sie dann im Inspector sicher, dass **Any Platform** ist **deaktiviert**, klicken Sie dann sicher, dass **nur** **WSAPlayer** ist**überprüft**. Klicken Sie auf **Übernehmen**.

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-25.png)

7. Sie müssen jetzt folgen **Schritte 4 bis 6**, aber für die *Newtonsoft* -Plug-Ins stattdessen. Finden Sie unter den folgenden Screenshot für das Ergebnis sollte folgendermaßen aussehen.

    ![Importieren des Unity-Pakets](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a>Kapitel 4: Einrichten der Kamera und Benutzer Steuerelemente

In diesem Kapitel richten Sie die Kamera und die Steuerelemente, damit Benutzer anzeigen und in der Szene verschieben.

1.  Mit der rechten Maustaste in einen leeren Bereich im Bereich Hierarchie, klicken Sie dann auf **erstellen > leere**.

    ![Richten Sie die Kamera und die Benutzersteuerelemente](images/AzureLabs-Lab309-26.png)

2.  Benennen Sie die neue leere "gameobject" zu **Kamera übergeordneten**.

    ![Richten Sie die Kamera und die Benutzersteuerelemente](images/AzureLabs-Lab309-27.png)

3.  Mit der rechten Maustaste in einen leeren Bereich im Bereich Hierarchie, klicken Sie dann auf **3D-Objekt**, klicken Sie dann auf **Kugel**.

4.  Benennen Sie die Kugel **rechten**.

5.  Legen Sie die **transformieren Skalierung** auf der rechten Hand **0,1, 0,1, 0,1**

    ![Richten Sie die Kamera und die Benutzersteuerelemente](images/AzureLabs-Lab309-28.png)

6.  Entfernen der **Kugel "collider"** -Komponente aus der rechten Seite durch Klicken auf die **Zahnradsymbol** in die *Kugel "collider"* -Komponente, und klicken Sie dann **Komponente entfernen** .

    ![Richten Sie die Kamera und die Benutzersteuerelemente](images/AzureLabs-Lab309-29.png)

7.  In den Bereich der Hierarchie ziehen Sie die **Main Camera** und **rechten** Objekte ablegen der **Kamera übergeordneten** Objekt.

    ![Richten Sie die Kamera und die Benutzersteuerelemente](images/AzureLabs-Lab309-30.png)

8.  Legen Sie die **transformieren Position** beider der **Main Camera** und die **rechten** -Objekt **0, 0, 0**.

    ![Richten Sie die Kamera und die Benutzersteuerelemente](images/AzureLabs-Lab309-31.png)

    ![Richten Sie die Kamera und die Benutzersteuerelemente](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a>Kapitel 5: Einrichten der Objekte in der Unity-Szene

Sie werden nun einige grundlegenden Formen für Ihre Szene erstellen, mit denen der Benutzer interagieren kann.

1.  Mit der rechten Maustaste in einen leeren Bereich in der *Hierarchie Bereich*, klicken Sie dann auf **3D-Objekt**, und wählen Sie dann **Ebene**.

2.  Legen Sie die Ebene **transformieren Position** zu **0, -1, 0**.

3.  Legen Sie die Ebene **transformieren Skalierung** zu **5, 1, 5**.

    ![Richten Sie die Objekte in der Unity-Szene](images/AzureLabs-Lab309-33.png)

4.  Erstellen Sie eine grundlegende Material für die Verwendung mit Ihrem **Ebene** Objekt, sodass die anderen Formen leichter zu erkennen sind. Navigieren Sie zu Ihrem *Projektfenster*, mit der rechten Maustaste, klicken Sie dann **erstellen**, gefolgt von **Ordner**, um einen neuen Ordner zu erstellen. Nennen Sie sie **Materialien**.

    ![Richten Sie die Objekte in der Unity-Szene](images/AzureLabs-Lab309-34.png) ![Richten Sie die Objekte in der Unity-Szene](images/AzureLabs-Lab309-35.png)

5.  Öffnen der **Materialien** Ordner, und dann mit der rechten Maustaste, klicken Sie auf **erstellen**, klicken Sie dann **Material**, um ein neues Material zu erstellen. Nennen Sie sie **blaue**.

    ![Richten Sie die Objekte in der Unity-Szene](images/AzureLabs-Lab309-36.png) ![Richten Sie die Objekte in der Unity-Szene](images/AzureLabs-Lab309-37.png)

6.  Mit dem neuen **blaue** Material ausgewählt haben, suchen auf der *Inspektor*, und klicken Sie auf das rechteckfenster zusammen mit **Albedo**. Wählen Sie eine blaue Farbe (die einen der folgenden Abbildung ist **Hexadezimalfarbe: \#3592FFFF**). Klicken Sie auf die Schaltfläche "Schließen", nachdem Sie ausgewählt haben.

    ![Richten Sie die Objekte in der Unity-Szene](images/AzureLabs-Lab309-38.png)

7.  Ziehen Sie Ihr neue Material aus der **Materialien** Ordner auf den neu erstellten **Ebene**, innerhalb der Szene (oder legen Sie diese auf die **Ebene** -Objekts innerhalb der  *Hierarchie*).

    ![Richten Sie die Objekte in der Unity-Szene](images/AzureLabs-Lab309-39.png)

8.  Mit der rechten Maustaste in einen leeren Bereich in der *Hierarchie Bereich*, klicken Sie dann auf **3D-Objekt, Capsule**.

    -  Mit der **Capsule** ausgewählt haben, Ändern seiner **transformieren** *Position* auf: **-10, 1, 0**.

9.  Mit der rechten Maustaste in einen leeren Bereich in der *Hierarchie Bereich*, klicken Sie dann auf **3D-Objekt, Cube**.

    -  Mit der **Cube** ausgewählt haben, Ändern seiner **transformieren** *Position* auf: **0, 0, 10**.

10. Mit der rechten Maustaste in einen leeren Bereich in der *Hierarchie Bereich*, klicken Sie dann auf **3D-Objekt, Kugel**.

    -  Mit der **Kugel** ausgewählt haben, Ändern seiner **transformieren** *Position* auf: **10, 0, 0**.

    ![Richten Sie die Objekte in der Unity-Szene](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > Diese *Position* Werte *Vorschläge*. Sie können sich die Positionen der Objekte, was auch immer Sie möchten, festlegen, aber es einfacher, für den Benutzer der Anwendung, ist wenn die Objekte in Abständen nicht zu weit von der Kamera sind.

11. Wenn Ihre Anwendung ausgeführt wird, muss es zum Identifizieren der Objekte in der Szene, um dies zu erreichen können, müssen sie gekennzeichnet werden. Wählen Sie eines der Objekte, und klicken Sie in der *Inspektor* auf **Tag hinzufügen...** , dem Austauschen wird die *Inspektor* mit der **Tags und Ebenen** Bereich.

    ![Richten Sie die Objekte in der Unity-Szene](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)

12. Klicken Sie auf die **+ (plus)** symbol, und geben Sie den Namen des Tags als **ObjectInScene**.

    ![Richten Sie die Objekte in der Unity-Szene](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > Wenn Sie einen anderen Namen für Ihr Tag verwenden, müssen Sie sicherstellen, diese Änderung auch die *DataFromAnalytics*, *ObjectTrigger*, und *bestaunen*, später, Skripts, damit Ihre Objekte gefunden, und erkannt werden, innerhalb der Szene.

13. Mit dem Tag, der erstellt wird müssen Sie jetzt diese auf alle drei der Objekte anwenden. Von der *Hierarchie*, enthalten die **UMSCHALT** Schlüssel, und klicken Sie dann die **Capsule**, **Cube**, und **Kugel**, Objekte, klicken Sie dann in der *Inspektor*, klicken Sie auf das Dropdownmenü neben **Tag**, klicken Sie dann auf die *ObjectInScene* markieren Sie Sie erstellt haben.

    ![Richten Sie die Objekte in der Unity-Szene](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a>Kapitel 6: Erstellen Sie die ApplicationInsightsTracker-Klasse

Ist das erste Skript, das Sie erstellen müssen **ApplicationInsightsTracker**, die für verantwortlich ist:

1.  Erstellen von Ereignissen, die basierend auf Benutzerinteraktionen zum Übermitteln an Azure Application Insights.

2. Erstellen die entsprechenden Ereignisnamen, je nach Benutzerinteraktion.

3. Übermitteln von Ereignissen an die Application Insights-Dienst-Instanz.

Diese Klasse zu erstellen:

1.  Mit der rechten Maustaste den *Projekt Bereich*, klicken Sie dann **erstellen > Ordner**. Nennen Sie den Ordner **Skripts**.

    ![Erstellen Sie die ApplicationInsightsTracker-Klasse](images/AzureLabs-Lab309-46.png)  ![Erstellen Sie die ApplicationInsightsTracker-Klasse](images/AzureLabs-Lab309-47.png)

2.  Mit der **Skripts** Ordner erstellt haben, doppelklicken Sie darauf, um zu öffnen. Klicken Sie dann in diesem Ordner mit der rechten Maustaste, **erstellen > C\# Skript**. Nennen Sie das Skript **ApplicationInsightsTracker**.

3.  Doppelklicken Sie auf die neue **ApplicationInsightsTracker** Skript öffnen Sie ihn mit **Visual Studio**.

4.  Aktualisieren Sie die Namespaces am Anfang des Skripts werden wie folgt:

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  Fügen Sie in der Klasse die folgenden Variablen:

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
    > Legen Sie die **InstrumentationKey "," ApplicationId und "api_key"** Werte entsprechend mithilfe der *Dienstschlüssel* über das Azure-Verwaltungsportal, wie im [Kapitel 1](#chapter-1---the-azure-portal), Schritt 9 oder höher.

6.  Fügen Sie dann die **Start()** und **Awake()** -Methoden, die aufgerufen werden, wenn die Klasse initialisiert:

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

7.  Fügen Sie die Methoden, die verantwortlich für das Senden der Ereignisse und Metriken, die von der Anwendung registriert:

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

8.  Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.

## <a name="chapter-7---create-the-gaze-script"></a>Kapitel 7: Erstellen Sie das Skript für die Blicke

Ist das nächste Skript zum Erstellen der **bestaunen** Skript. Dieses Skript ist verantwortlich für das Erstellen einer *Raycast* , projiziert weiterleiten aus der *Main Camera*, welches Objekt erkannt, wird der Benutzer ansehen. In diesem Fall die *Raycast* benötigen, um festzustellen, ob der Benutzer auf ein Objekt mit sieht die **ObjectInScene** markieren, und wie langen den Benutzer zählen *gazes* auf dieses Objekt.

1.  Doppelklicken Sie auf die **Skripts** Ordner, um ihn zu öffnen.

2.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen** > **C\# Skript**. Nennen Sie das Skript **bestaunen**.

3.  Doppelklicken Sie auf das Skript aus, um ihn mit Visual Studio zu öffnen.

4.  Ersetzen Sie den vorhandenen Code durch Folgendes:

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

5.  Code für die **Awake()** und **Start()** Methoden jetzt hinzugefügt werden muss.

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

6.  In der **bestaunen** -Klasse verwenden, fügen Sie den folgenden Code in die **Update()** Methode, um das Projekt ein *Raycast* und erkennen Sie das Ziel erreicht:

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

7.  Hinzufügen der **ResetFocusedObject()** Methode zum Senden von Daten zu **Application Insights** Wenn der Benutzer auf ein Objekt gesucht wurde.

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

8.  Sie haben jetzt die **bestaunen** Skript. Speichern Sie die Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.

## <a name="chapter-8---create-the-objecttrigger-class"></a>Kapitel 8 – erstellen Sie die ObjectTrigger-Klasse

Ist das nächste Skript, das Sie erstellen müssen **ObjectTrigger**, die für verantwortlich ist:

- Hinzufügen von Komponenten, die Kollision bis zur Kamera Main erforderlich sind.
- Ermitteln, ob die Kamera in der Nähe eines Objekts als ist **ObjectInScene**.

So erstellen Sie das Skript:

1.  Doppelklicken Sie auf die **Skripts** Ordner, um ihn zu öffnen.

2.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen** **C\# > Skript**. Nennen Sie das Skript **ObjectTrigger**.

3.  Doppelklicken Sie auf das Skript aus, um ihn mit Visual Studio zu öffnen. Ersetzen Sie den vorhandenen Code durch Folgendes:

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

4.  Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.

## <a name="chapter-9---create-the-datafromanalytics-class"></a>Kapitel 9 – erstellen Sie die DataFromAnalytics-Klasse

Sie müssen nun zum Erstellen der **DataFromAnalytics** Skripts, die dafür verantwortlich ist:

- Beim Abrufen von Analytics-Daten darüber, welche Objekt von der Kamera die erreicht wurden hat.
- Mithilfe der *Dienstschlüssel*, die mit Ihrer Instanz von Azure Application Insights-Dienst zulassen.
- Sortieren die Objekte in der Szene, die höchste Anzahl von Ereignissen, nach denen hat.
- Farbänderungen Material, das am häufigsten approached-Objekt zu *Grün*.

So erstellen Sie das Skript:

1.  Doppelklicken Sie auf die **Skripts** Ordner, um ihn zu öffnen.

2.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen** **C\# > Skript**. Nennen Sie das Skript **DataFromAnalytics**.

3.  Doppelklicken Sie auf das Skript aus, um ihn mit Visual Studio zu öffnen.

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

5.  Fügen Sie innerhalb des Skripts die folgenden Schritte aus:

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

6.  In der **DataFromAnalytics** Klasse, die nach der rechten Maustaste die **Start()** -Methode, fügen Sie die folgende Methode wird aufgerufen, **FetchAnalytics()**. Diese Methode ist verantwortlich für das Auffüllen der Liste der Schlüssel-/Wertpaaren, mit einem *"gameobject"* und eine Anzahl der Platzhalter-Ereignis. Klicken Sie dann initialisiert die **GetWebRequest()** Coroutine. Die Abfragestruktur des Aufrufs von *Application Insights* können innerhalb dieser Methode finden Sie auch, wie die *Abfrage-URL* Endpunkt.

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

7.  Direkt unterhalb der **FetchAnalytics()** -Methode, fügen Sie eine Methode namens **GetWebRequest()**, gibt ein *IEnumerator*. Diese Methode ist verantwortlich für die Anforderung an, wie oft ein Ereignis, das mit einem bestimmten entspricht *"gameobject"*, aufgerufen wurde in *Application Insights*. Wenn alle gesendeten Abfragen zurückgegeben, die **DetermineWinner()** Methode wird aufgerufen.

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

8.  Die nächste Methode ist **DetermineWinner()**, sortiert die Liste der *"gameobject"* und *Int* -Paare, anhand der höchsten Anzahl von Ereignissen. Er ändert dann die Material Farbe, *"gameobject"* zu *Grün* (als Feedback, damit es mit der höchsten Anzahl). Dadurch werden eine Meldung mit den Ergebnissen der Analyse angezeigt.

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

9.  Fügen Sie die Klassenstruktur, der verwendet wird, deserialisiert das JSON-Objekt, das Empfangen von *Application Insights*. Fügen Sie diese Klassen am Ende Ihrer **DataFromAnalytics** -Klassendatei **außerhalb** der Definition der Klasse.

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

10. Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.

## <a name="chapter-10---create-the-movement-class"></a>Kapitel 10 – erstellen Sie die Bewegung-Klasse

Die **Bewegung** Skript ist das nächste Skript, das Sie erstellen müssen. Er ist verantwortlich für:

- Verschieben die Main Camera entsprechend der Richtung der Kamera sucht in Richtung.
- Alle anderen Skripts und szeneobjekte hinzugefügt.

So erstellen Sie das Skript:

1.  Doppelklicken Sie auf die **Skripts** Ordner, um ihn zu öffnen.

2.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen** > **C\# Skript**. Nennen Sie das Skript **Bewegung**.

3.  Doppelklicken Sie auf das Skript mit öffnen *Visual Studio*.

4.  Ersetzen Sie den vorhandenen Code durch Folgendes:

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

5.  In der **Bewegung** -Klasse, *unten* die leere **Update()** -Methode, fügen Sie die folgenden Methoden, die der Benutzer auf den Hand-Controller verwenden, um im virtuellen Raum zu verschieben:

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

6.  Fügen Sie schließlich den Aufruf der Methode innerhalb der **Update()** Methode.

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.

## <a name="chapter-11---setting-up-the-scripts-references"></a>Kapitel 11: Festlegen der Verweise auf die Skripts

In diesem Kapitel es erforderlich, die **Datenverschiebung** Skript auf die **Kamera übergeordneten** und legen Sie Ziele Verweis. Dieses Skript behandelt platzieren den anderen Skripts, in denen sie sein müssen.

1.  Aus der **Skripts** Ordner in der *Projektfenster*, ziehen Sie die **Bewegung** Skript aus, um die **Kamera übergeordneten** Objekt befindet sich in der  *Hierarchie-Bereich*.

    ![Die Skripts verweisen in der Unity-Szene einrichten](images/AzureLabs-Lab309-48.png)

2.  Klicken Sie auf die **Kamera übergeordneten**. In der *Hierarchie Bereich*, ziehen Sie die **rechten** -Objekt aus der *Hierarchie Bereich* mit dem Verweisziel **Controller**in der *Inspektor Bereich*. Legen Sie die **Benutzer Geschwindigkeit** zu **5**, wie in der folgenden Abbildung dargestellt.

    ![Die Skripts verweisen in der Unity-Szene einrichten](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a>Kapitel 12: Erstellen Sie das Unity-Projekt

Alles, was Sie für den Unity-Abschnitt, der dieses Projekt wurde jetzt abgeschlossen daher ist es Zeit für die Erstellung von Unity.

1.  Navigieren Sie zu **Buildeinstellungen**, **(Datei > Buildeinstellungen...)** .

2.  Von der **Buildeinstellungen** Fenster, klicken Sie auf **erstellen**.

    ![Erstellen Sie das Unity-Projekt mit UWP-Lösung](images/AzureLabs-Lab309-50.png)

3.  Ein **Datei-Explorer** Fenster werden Popupfenster, dem Sie aufgefordert werden, eines Speicherorts für den Build. Erstellen Sie einen neuen Ordner (indem Sie auf **neuer Ordner** in der oberen linken Ecke), und nennen Sie sie **erstellt**.

    ![Erstellen Sie das Unity-Projekt mit UWP-Lösung](images/AzureLabs-Lab309-51.png)

    1.  Öffnen Sie die neue **erstellt** Ordner, und erstellen Sie einen anderen Ordner (mit **neuer Ordner** einmal), und nennen Sie sie **MR\_Azure\_Anwendung\_ Insights**.

        ![Erstellen Sie das Unity-Projekt mit UWP-Lösung](images/AzureLabs-Lab309-52.png)

    2.  Mit der **MR\_Azure\_Anwendung\_Insights** Ordner ausgewählt haben, klicken Sie auf **Ordner auswählen**. Das Projekt wird eine Minute erstellen dauern.

4.  Folgende *erstellen*, **Datei-Explorer** wird angezeigt, die Sie den Standort des neuen Projekts.

## <a name="chapter-13---deploy-mrazureapplicationinsights-app-to-your-machine"></a>Kapitel 13 – MR_Azure_Application_Insights-app auf Ihrem Computer bereitstellen

Zum Bereitstellen der **MR\_Azure\_Anwendung\_Insights** -app auf Ihrem lokalen Computer:

1.  Öffnen Sie die Projektmappendatei, die von Ihrem **MR\_Azure\_Anwendung\_Insights** -app in **Visual Studio**.

2.  In der **Projektmappenplattform**Option **X86, lokalen Computer**.

3.  In der **Projektmappenkonfiguration** wählen **Debuggen**.

    ![Erstellen Sie das Unity-Projekt mit UWP-Lösung](images/AzureLabs-Lab309-53.png)

4.  Wechseln Sie zu **Menü "Build"** und klicken Sie auf **Projektmappe bereitstellen** zum querladen der Anwendung auf Ihrem Computer.

5.  Ihre app sollte nun in der Liste der installierten apps, die zu startenden bereit angezeigt werden.

6. Starten Sie die mixed Reality-Anwendung.

7. Verschieben der Szene annähert, die Objekte aus, und betrachten, wenn die *Azure Insights-Dienst* wurden genügend Ereignisdaten erfasst, die sie legt das Objekt, das die meisten in Grün erreicht wurde, hat.

> [!IMPORTANT] 
> Während die durchschnittliche Wartezeit für die *Ereignisse und Metriken* dauert ca. 15 Minuten vom Dienst erfasst werden, in einigen Fällen kann es bis zu einer Stunde dauern.

## <a name="chapter-14---the-application-insights-service-portal"></a>Kapitel 14: das Application Insights-Dienst-portal

Nachdem Sie in der Szene gewechselt haben und auf mehrere Objekte gazed Sie die Datensammlung sehen in der *Application Insights-Dienst* Portal.

1.  Wechseln Sie zurück zu Ihrem Application Insights-Dienst-Portal.

2.  Klicken Sie auf *Metrik-Explorer*.

    ![Sehen Sie gesammelte Daten](images/AzureLabs-Lab309-54.png)

3.  Es wird geöffnet, auf einer Registerkarte mit dem Diagramm die darstellen der *Ereignisse und Metriken* im Zusammenhang mit Ihrer Anwendung. Wie bereits erwähnt, dauert es einige Zeit (bis zu 1 Stunde) für die Daten, die im Diagramm angezeigt werden

    ![Sehen Sie gesammelte Daten](images/AzureLabs-Lab309-55.png)

4.  Klicken Sie auf die *Ereignisse Leiste* in die *Gesamtanzahl von Ereignissen* von Version der Anwendung, um eine detaillierte Aufschlüsselung der Ereignisse mit ihren Namen anzuzeigen.

    ![Sehen Sie gesammelte Daten](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a>Ihre fertige Ihrer Anwendung Application Insights-Dienst

Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die Application Insights-Diensts zum Überwachen der Aktivität des Benutzers in Ihrer app nutzt.

![Kurs Ergebnis](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a>Bonus-Übungen

**Übung 1**

Versuchen Sie es erstellen, anstatt manuell erstellen, die ObjectInScene Objekte aus, und legen Sie die Koordinaten in der Ebene in Ihren Skripts. Auf diese Weise können Sie Fragen Azure welches der am häufigsten verwendete Objekt (entweder aus Blicke oder NEAR-Ergebnissen) wurde, und erzeugen eine *zusätzliche* eines dieser Objekte.

**Übung 2**

Sortieren Sie die Application Insights-Ergebnisse bis zu Zeitpunkt, damit Sie die relevantesten Daten abzurufen, und dieser Uhrzeit sensiblen Daten in Ihrer Anwendung implementieren.

