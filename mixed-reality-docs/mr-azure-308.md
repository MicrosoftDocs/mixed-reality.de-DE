---
title: MR und Azure-308 - Geräteübergreifende Benachrichtigungen
description: Führen Sie diesen Kurs erfahren, wie Sie Azure Notification Hubs, Azure Functions und Azure Storage und Tabellen innerhalb einer mixed Reality-Anwendung zu implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorial, api, Notification, Funktionen, Tabellen, benachrichtigungshubs, Hololens, immersive vr
ms.openlocfilehash: ed56c936a0498b6e0ac804da15a2c6ec98239d0c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604784"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a>MR und Azure-308: Geräteübergreifende Benachrichtigungen

![Endprodukt-starten](images/AzureLabs-Lab8-00.png)

In diesem Kurs lernen Sie, wie eine mixed Reality-Anwendung mit Azure Notification Hubs, Azure-Tabellen und Azure Functions Notification Hubs-Funktionen hinzugefügt werden.

**Azure Notification Hubs** ist ein Microsoft-Dienst, wodurch Entwicklern, gezielte und personalisierte Pushbenachrichtigungen an jede Plattform, die alle Rahmen in der Cloud zu senden. Diese kann effektiv ermöglichen es Entwicklern, für die Kommunikation mit dem Endbenutzer, oder Sie können auch die Kommunikation zwischen verschiedenen Anwendungen, je nach Szenario. Weitere Informationen finden Sie auf die **Azure Notification Hubs** [Seite](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).

**Azure Functions** ist ein Microsoft-Dienst, die Entwickler kleine Teile des Codes ausgeführt werden kann, "Funktionen", in Azure. Dadurch wird eine Möglichkeit zum Delegieren der Arbeit an Ihrer lokalen Anwendung, die viele Vorteile haben kann, anstatt die Cloud. **Azure Functions** unterstützt verschiedene Entwicklungssprachen, darunter C\#, F\#, Node.js, Java und PHP. Weitere Informationen finden Sie auf die **Azure Functions** [Seite](https://docs.microsoft.com/azure/azure-functions/functions-overview).

**Azure-Tabellen** wird ein Microsoft-Cloud-Dienst, der Entwickler strukturierte nicht-SQL-Daten in der Cloud speichern zu können, so problemlos eine beliebige Stelle. Der Dienst in Kombination mit ein schemalosen Design, sodass für die Entwicklung von Tabellen, bei Bedarf bietet und somit ist sehr flexibel. Weitere Informationen finden Sie auf die **Azure-Tabellen** [Seite](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

Nach Abschluss dieses Kurses, haben Sie eine mixed Reality immersive Kopfhörer-Anwendung, und eine Desktop-PC-Anwendung, die für die folgenden Aufgaben werden können:

1. Die app von Desktop-PC kann sich der Benutzer zum Verschieben eines Objekts in einem 2D-Bereich (X und Y), mit der Maus.

2. Das Verschieben von Objekten innerhalb der PC-app in die Cloud mithilfe von JSON, die in Form einer Zeichenfolge, enthält die Objekt-ID, Typ, gesendet und Transformieren von Informationen (X- und Y-Koordinaten). 

3. Mixed Reality-app, die eine identische Szene an die desktop-app verfügt, erhalten Benachrichtigungen in Bezug auf die Bewegung des Objekts, von Notification Hubs-Dienst (die gerade von der Desktop-PC-app aktualisiert wurde). 

4. Nach dem Empfang einer benachrichtigungs, die die Objekt-ID, Typ und Transformationsinformationen enthält, wird der mixed Reality-app die empfangene Informationen gelten für eine eigene Szene.

In Ihrer Anwendung obliegt es Ihnen, wie Sie die Ergebnisse in Ihr Design integrieren werden. Dieser Kurs erfahren Sie, wie Sie ein Azure-Dienst in Ihrem Unity-Projekt zu integrieren. Es ist Ihre Aufgabe, verwenden Sie das wissen, dass Sie aus diesem Kurs zum Verbessern Ihrer mixed Reality-Anwendung erhalten. Dieser Kurs ist eine eigenständige Tutorials, das aller anderen Mixed Reality-Labs nicht direkt betroffen sind.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td> MR und Azure-308: Geräteübergreifende Benachrichtigungen</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Während dieser Kurs in erster Linie für immersive Windows Mixed Reality (VR)-Headsets ausgerichtet ist, können Sie auch anwenden, was Sie in diesem Kurs, Microsoft HoloLens lernen. Wie Sie den Kurs halten, sehen Anmerkungen zu dieser Version auf Änderungen Sie möglicherweise zur Unterstützung von HoloLens einsetzen müssen. Wenn Sie HoloLens verwenden zu können, werden Sie einige Echo während der Sprachaufnahme feststellen.

## <a name="prerequisites"></a>Vorraussetzungen

> [!NOTE]
> In diesem Tutorial wurde für Entwickler mit Erfahrung mit Unity entwickelt und C#. Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Mai 2018) überprüft wurde. Sie können zur Verwendung der neuesten Software, wie in der [Installieren der Tools](install-the-tools.md) Artikel, obwohl es nicht davon ausgegangen werden soll, dass die Informationen in diesem Kurs perfekt was finden Sie in der neueren Software entspricht als die unten Angaben aufgeführten .

Es wird empfohlen, die folgende Hardware und Software für diesen Kurs:

- Eine Entwicklungs-PC [kompatibel mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für immersive (VR) Kopfhörer-Entwicklung
- [Windows 10 Fall Creators Update (oder höher) mit der Entwicklermodus aktiviert ist](install-the-tools.md#installation-checklist)
- [Das neueste Windows 10-SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Ein [immersive Windows Mixed Reality (VR)-Kopfhörer](immersive-headset-hardware-details.md) oder [Microsoft HoloLens](hololens-hardware-details.md) mit Entwicklermodus aktiviert ist
- Zugriff auf das Internet für die Einrichtung von Azure und den Zugriff auf Notification Hubs

## <a name="before-you-start"></a>Bevor Sie beginnen

- Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).
- Sie müssen den Besitzer für Ihr Microsoft-Entwicklerportal und Ihre App-Registrierungsportal sein, andernfalls müssen Sie nicht über die Berechtigung zum Zugriff auf die app im [Kapitel 2](#chapter-2---retrieve-your-new-apps-credentials).

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a>Kapitel 1: Erstellen einer Anwendung im Microsoft Developer-Portal

Verwenden der **Azure Notification Hubs** -Dienst Sie benötigen zum Erstellen einer Anwendung im Microsoft Developer-Portal, wie Ihre Anwendung registriert werden, sodass gesendet und Empfangen von Benachrichtigungen werden können, benötigen.

1.  Melden Sie sich bei der [Microsoft-Entwicklerportal](https://developer.microsoft.com/dashboard).

    > Sie müssen bei Ihrem Microsoft Account anmelden.

2.  Klicken Sie auf dem Dashboard auf **Erstellen einer neuen app**.

    ![Erstellen einer app](images/AzureLabs-Lab8-01.png)

3.  Ein Popupfenster wird angezeigt, in dem Sie einen Namen für Ihre neue app reservieren möchten. Fügen Sie im Textfeld einen passenden Namen; Wenn der ausgewählte Name verfügbar ist, wird ein Tick rechts neben dem Textfeld angezeigt. Nachdem Sie einen verfügbaren Namen eingefügt haben, klicken Sie auf die **Produktname reservieren** Schaltfläche unten links auf der das Popup.

    ![ein Name der Reverse-](images/AzureLabs-Lab8-02.png)

4.  Während die app nun erstellt ist sind Sie bereit sind, finden Sie im nächsten Kapitel.

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a>Kapitel 2: Ihre neuen apps-Anmeldeinformationen abrufen

Melden Sie sich bei der App-Registrierungsportal, in dem Ihre neue app aufgeführt, und rufen Sie die Anmeldeinformationen, die für Setup verwendet werden, werden die **Notification Hubs-Dienst** innerhalb der **Azure-Portal**.

1.  Navigieren Sie zu der [App-Registrierungsportal](http://apps.dev.microsoft.com).

    ![App-registrierungsportal](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > Sie müssen Ihr Microsoft Account, die Anmeldung verwenden.  
    > Dies **müssen** werden von der Microsoft-Account mit denen Sie in der vorherigen [Kapitel](#chapter-1---create-an-application-on-the-microsoft-developer-portal), mit dem Windows Store Developer-Portal.

2.  Sehen Sie Ihre app unter der **meiner Anwendungen** Abschnitt. Wenn Sie ihn gefunden haben, klicken Sie darauf, und Sie gelangen zu einer neuen Seite, die die app verfügt über Name und **Registrierung**.

    ![Ihre neu registrierte app](images/AzureLabs-Lab8-04.png)

3.  Führen Sie einen Bildlauf nach unten der Registrierungsseite finden Ihre **Anwendungsgeheimnisse** Abschnitt und der **Paket-SID** für Ihre app. Kopieren Sie beide für die Verwendung bei der Einrichtung der **Azure Notification Hubs-Dienst** im nächsten Kapitel.

    ![geheimer Anwendungsschlüssel](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a>Kapitel 3: Einrichten von Azure-Portal: Erstellen von Notification Hubs-Dienst

Mit Ihren apps-Anmeldeinformationen abgerufen, Sie müssen zum Azure-Portal zu wechseln, in dem Sie eine Azure Notification Hubs-Dienst erstellen.

1.  Melden Sie sich bei der [Azure-Portal](https://portal.azure.com).

    > [!NOTE] 
    > Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen. Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.

2.  Sobald Sie angemeldet sind, klicken Sie auf **neu** in der oberen linken Ecke, und suchen Sie nach **Benachrichtigungs-Hub**, und klicken Sie auf ***EINGABETASTE***.

    ![Suchen Sie nach der benachrichtigungs-hub](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > Das Wort ***neu*** wurden möglicherweise durch ersetzt **erstellen Sie eine Ressource**, in neueren-Portalen.

3.  Die neue Seite bietet eine Beschreibung der *Notification Hubs* Service. Unten links der Aufforderung, wählen die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.

    ![Erstellen von Notification Hubs-Instanz](images/AzureLabs-Lab8-07.png)

4.  Nachdem Sie auf geklickt haben ***erstellen***:

    1.  Fügen Sie dem gewünschten Namen für diese Dienstinstanz.

    2.  Geben Sie einen **Namespace** die Sie dieser app zugeordnet werden können.

    3.  Wählen Sie eine **Speicherort.**

    4.  Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diesen Labs) unter einer allgemeinen Ressourcengruppe zu halten).

        > Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, befolgen Sie diese [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal). 

    5.  Wählen Sie einen geeigneten **Abonnement**.

    6.  Sie müssen auch bestätigen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.

    7. Wählen Sie **Erstellen** aus.

        ![Geben Sie-Dienstdetails](images/AzureLabs-Lab8-08.png)

5.  Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.

6.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Benachrichtigung](images/AzureLabs-Lab8-09.png)

7.  Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen. Sie gelangen in die neue **Benachrichtigungs-Hub** Dienstinstanz.

    ![zu Ressource wechseln](images/AzureLabs-Lab8-10.png)
    
8.  Klicken Sie auf der Seite "Übersicht", in der Mitte der Seite, auf **Windows (WNS).** Der Bereich auf der rechten Seite ändert sich in zeigen zwei Textfelder, die erforderlich sind Ihre **Paket-SID** und **Sicherheitsschlüssel**, aus der app, die Sie zuvor eingerichtet haben.

    ![neu erstellte Hubs-Dienst](images/AzureLabs-Lab8-11.png)

9. Nachdem Sie die Details in die richtigen Felder kopiert haben, klicken Sie auf **speichern**, und Sie erhalten eine Benachrichtigung auf, wenn es sich bei den Notification Hub erfolgreich aktualisiert wurde.

    ![Notieren Sie sich die Informationen zur Sicherheit](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a>Kapitel 4: Einrichten von Azure-Portal: Erstellen der Tabellendienst

Nach dem Erstellen Ihrer Instanz von Notification Hubs-Dienst an, navigieren Sie zurück zu Ihrem Azure-Portal, in dem Sie ein Azure-Tabellen-Dienst durch Erstellen einer Speicherressource erstellen.

1.  Wenn nicht bereits angemeldet, melden Sie sich bei der [Azure-Portal](https://portal.azure.com).

2.  Sobald Sie angemeldet sind, klicken Sie auf **neu** in der oberen linken Ecke, und suchen Sie nach **Speicherkonto**, und klicken Sie auf **EINGABETASTE**.

    > [!NOTE] 
    > Das Wort ***neu*** wurden möglicherweise durch ersetzt **erstellen Sie eine Ressource**, in neueren-Portalen.

3.  Wählen Sie **Speicherkonto – Blob, Datei, Tabelle, Warteschlange** aus der Liste.

    ![Suchen Sie nach dem Storage-Konto](images/AzureLabs-Lab8-13.png)

4.  Die neue Seite bietet eine Beschreibung der **Speicherkonto** Service. Unten links der Aufforderung, wählen die **erstellen** Schaltfläche, um eine Instanz dieses Diensts zu erstellen.

    ![Storage-Instanz erstellen](images/AzureLabs-Lab8-14.png)

5.  Nachdem Sie auf geklickt haben **erstellen**, wird ein Panel angezeigt:

    1. Fügen Sie Ihre bevorzugte **Namen** für diese Dienstinstanz (müssen Kleinbuchstaben sein).

    2. Für **Bereitstellungsmodell**, klicken Sie auf **RM**.

    3.  Für **Kontoart**, wählen Sie im Dropdownmenü mit **Speicher (Allgemein v1)**.

    4. Wählen Sie einen geeigneten **Speicherort**.
    
    5.  Für die **Replikation** wählen Sie im Dropdownmenü **Read-Access-georedundanter Speicher (RA-GRS)**.

    6.  Für **Leistung**, klicken Sie auf **Standard**.

    7.  In der **sichere Übertragung erforderlich** wählen Sie im Abschnitt **deaktiviert**.

    8.  Von der **Abonnement** im Dropdownmenü ein entsprechendes Abonnement auswählen.

    9.  Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diesen Labs) unter einer allgemeinen Ressourcengruppe zu halten).

        > Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, befolgen Sie diese [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. Lassen Sie **virtuelle Netzwerke** als **deaktiviert** ist dies eine Option für Sie.

    11. Klicken Sie auf **Erstellen**.

        ![Geben Sie im Storage-details](images/AzureLabs-Lab8-15.png)

6.  Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.

7.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt. Klicken Sie auf die Benachrichtigungen an Ihre neue Dienstinstanz zu untersuchen.

    ![neue Speicher-Benachrichtigung](images/AzureLabs-Lab8-16.png)

8.  Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen. Sie werden auf Ihre neue Übersichtsseite für den Speicherdienst Instanz weitergeleitet.

    ![zu Ressource wechseln](images/AzureLabs-Lab8-17.PNG)

9. Klicken Sie auf der Seite "Übersicht" auf der rechten Seite auf **Tabellen**.
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. Der Bereich auf der rechten Seite wird geändert, um anzugeben der **Tabellendienst** Informationen, bei dem Sie eine neue Tabelle hinzufügen möchten. Durch Klicken auf die **+** **Tabelle** Schaltfläche auf der linken oberen Ecke.

    ![Öffnen von Tabellen](images/AzureLabs-Lab8-19.png)

11. Eine neue Seite wird angezeigt, in dem Sie eingeben müssen, eine **Tabellenname**. Dies ist der Name, den Sie verwenden, um auf die Daten in Ihrer Anwendung in späteren Kapiteln verweisen. Fügen Sie einen geeigneten Namen ein, und klicken Sie auf **OK**.

    ![Erstellen einer neuen Tabelle](images/AzureLabs-Lab8-20.png)    

12. Sobald die neue Tabelle erstellt wurde, Sie werden in finden Sie unter den **Tabellendienst** Seite (unten).

    ![neue Tabelle](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a>Kapitel 5: Abschließen der Azure-Tabelle in Visual Studio

Nachdem Ihre **Tabellendienst** Storage-Konto eingerichtet haben, ist es Zeit zum Hinzufügen von Daten, die zum Speichern und Abrufen von Informationen verwendet wird. Die Bearbeitung Ihrer Tabellen kann über erfolgen **Visual Studio**.

1.  Open **Visual Studio**.

2.  Klicken Sie im Menü auf **Ansicht > Cloud-Explorer**.

    ![Öffnen Sie den Cloud-explorer](images/AzureLabs-Lab8-22.png)

3.  Die **Cloud-Explorer** öffnet als angedockte Element (Geduld, Laden von Zeit in Anspruch).

    > [!NOTE] 
    > Wenn das Abonnement, das Sie zum Erstellen verwendet Ihre *Speicherkonten* ist nicht sichtbar ist, sicherzustellen, dass Sie: 
    > - Angemeldet um dasselbe Konto wie diejenige aus, die Sie für das Azure-Portal verwendet.
    > - Ihr Abonnement aus der Konto-Verwaltungsseite (möglicherweise müssen einen Filter aus den Einstellungen Ihres Kontos anwenden) ausgewählt:  
    >
    >   ![Suchen Sie nach Abonnement](images/AzureLabs-Lab8-22-5.png)

4.  Ihre Azure-Cloud-Dienste werden angezeigt. Suchen **Speicherkonten** , und klicken Sie auf den Pfeil auf der linken Seite, um Ihre Konten zu erweitern.

    ![Öffnen Sie Storage-Konten](images/AzureLabs-Lab8-23.png)

5.  Nach der Kategorie erweitert ist, das neu erstellte **Speicherkonto** verfügbar sein sollen. Klicken Sie auf den Pfeil auf der linken Seite des Speichers, und klicken Sie dann nach, die erweitert wird, finden **Tabellen** , und klicken Sie auf den Pfeil neben der, dass zum Anzeigen der **Tabelle** Sie im letzten Abschnitt erstellt haben. Klicken Sie mit der Doppelklicken auf Ihre **Tabelle**.

    ![Öffnen Sie die Tabelle der Szene-Objekte](images/AzureLabs-Lab8-24.png)

6.  Die Tabelle wird in der Mitte des Ihrer Visual Studio-Fenster geöffnet. Klicken Sie auf das Tabellensymbol "mit der **+** (plus) auf.

    ![neue Tabelle hinzufügen](images/AzureLabs-Lab8-25.png)

7.  Ein Fenster wird aufgefordert wird angezeigt, Sie *Entität hinzufügen*. Sie erstellen drei Entitäten insgesamt, jeweils mit mehreren Eigenschaften. Sie werden feststellen, dass *PartitionKey* und *RowKey* werden soll, bereits bereitgestellt ist, als diese von der Tabelle verwendet werden, um Ihre Daten zu finden. 

    ![Partitions-und zeilenschlüssels](images/AzureLabs-Lab8-26.png)

8. Update der *Wert* von der **PartitionKey** und **RowKey** wie folgt (Beachten Sie hierzu für jede Zeile Eigenschaft Sie hinzugefügt haben, jedoch jedes Mal erhöht RowKey):

    ![Fügen Sie die richtigen Werte](images/AzureLabs-Lab8-26-5.png)

9.  Klicken Sie auf **Eigenschaft hinzufügen** zum Hinzufügen von zusätzlicher Zeilen von Daten. Stellen Sie Ihre erste leere Tabelle entspricht der folgenden Tabelle.

10. Klicken Sie anschließend auf **OK**.

    ![Klicken Sie auf ok, wenn fertig](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > Stellen Sie sicher, dass Sie geändert haben die **Typ** von der **X**, **Y**, und **Z**, Einträge **doppelte**. 

11. Beachten Sie, dass die Tabelle jetzt über eine Zeile mit Daten verfügt. Klicken Sie auf die **+** (Pluszeichen) erneut aus, um eine andere Entität hinzufügen.

    ![erste Zeile](images/AzureLabs-Lab8-27-5.png)

12. Erstellen Sie eine zusätzliche Eigenschaft, und legen Sie dann die Werte der neuen Entität mit den unten dargestellten übereinstimmen.

    ![Hinzufügen von Cubes](images/AzureLabs-Lab8-28.png)

13. Wiederholen Sie den letzten Schritt zum Hinzufügen einer anderen Entität. Legen Sie die Werte für diese Entität unten dargestellt ein.

    ![Hinzufügen von Zylinder](images/AzureLabs-Lab8-29.png)

14. Die Tabelle sollte jetzt wie folgt aussehen.

    ![Tabelle](images/AzureLabs-Lab8-30.png)

15. In diesem Kapitel wurde abgeschlossen. Stellen Sie sicher zu speichern.

## <a name="chapter-6---create-an-azure-function-app"></a>Kapitel 6: erstellen eine Azure-Funktions-App

Erstellen Sie eine Azure-Funktionen-App, die aufgerufen wird, von der Desktop-Anwendung zum Aktualisieren der **Tabelle** Dienst, und senden eine Benachrichtigung über die **Benachrichtigungs-Hub**.

Zunächst müssen Sie eine Datei zu erstellen, mit dem Ihre Azure-Funktion, die Bibliotheken zu laden, die Sie benötigen.

1.  Open **Editor** (drücken Sie Windows-Taste und geben Sie Notepad).

    ![Öffnen Sie Editor](images/AzureLabs-Lab8-31.png)

2.  Legen Sie mit dem Editor öffnen die folgende JSON-Struktur, in es. Sobald Sie dies getan haben, speichern Sie es auf Ihrem Desktop als **"Project.JSON"**. Es ist wichtig, dass die Benennung korrekt ist: Stellen Sie sicher, es ist **keine txt** Dateierweiterung. Diese Datei definiert die Bibliotheken, die Ihre Funktion verwenden, die Wenn Sie die vertraut wird NuGet verwendet haben.

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  Melden Sie sich bei der [Azure-Portal](https://portal.azure.com).

4.  Sobald Sie angemeldet sind, klicken Sie auf **neu** in der oberen linken Ecke, und suchen Sie nach **Funktions-App**, drücken Sie die **EINGABETASTE**.

    ![Suchen Sie nach der Funktions-app](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > Das Wort **neu** wurden möglicherweise durch ersetzt **erstellen Sie eine Ressource**, in neueren-Portalen.

5.  Die neue Seite bietet eine Beschreibung der **Funktions-App** Service. Unten links der Aufforderung, wählen die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.

    ![Funktionen-app-Instanz](images/AzureLabs-Lab8-33.png)

6.  Nachdem Sie auf geklickt haben **erstellen**, geben Sie Folgendes:

    1. Für **Anwendungsnamen**, fügen Sie dem gewünschten Namen für diese Dienstinstanz.

    2. Wählen Sie eine **Abonnement**.

    3. Wählen Sie der Tarif für Sie geeignet, ist dies das erste Mal erstellen eine **-Funktion von App Service**, freier-Tarif für Sie verfügbar sein sollen.

    4. Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diesen Labs) unter einer allgemeinen Ressourcengruppe zu halten).

        > Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, befolgen Sie diese [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Für **OS**, Windows, klicken Sie auf, da dies die angezielte Plattform ist.

    6. Wählen Sie eine **Hostingplan** (in diesem Tutorial verwendet ein **Verbrauchstarif**.

    7. Wählen Sie eine **Speicherort** **(Wählen Sie im vorherigen Schritt am gleichen Speicherort wie der Speicher, die Sie erstellt haben)**

    8. Für die **Storage** Abschnitt **müssen Sie den Storage-Dienst, die Sie im vorherigen Schritt erstellt haben, auswählen**.

    9. Sie müssen keine *Application Insights* in dieser app können daher gerne bleibt bestehen **aus**.

    10. Klicken Sie auf **Erstellen**.

        ![neue Instanz erstellen](images/AzureLabs-Lab8-34.png)

7.  Nachdem Sie auf geklickt haben **erstellen** müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.

8.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Neue Benachrichtigung](images/AzureLabs-Lab8-35.png)

9.  Klicken Sie auf die Benachrichtigungen an Ihre neue Dienstinstanz zu untersuchen.

10. Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen. 

    ![zu Ressource wechseln](images/AzureLabs-Lab8-36.png)

11. Klicken Sie auf die **+** (Pluszeichen) Symbol neben dem *Funktionen*zu *neu erstellen*.

    ![Fügen Sie neue Funktion](images/AzureLabs-Lab8-37.png)

12. Klicken Sie im mittleren Bereich der **Funktion** Erstellung-Fenster wird angezeigt. Ignorieren Sie die Informationen in der oberen Hälfte des Bereichs, und klicken Sie auf **benutzerdefinierte Funktion**, befindet sich im unteren Bereich (im blauen Bereich, wie unten gezeigt).

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab8-38.png)

13. Die neue Seite im Fenster zeigt die verschiedenen Funktionstypen. Scrollen Sie nach unten, um die lilafarbenen Typen anzuzeigen, und klicken Sie auf **HTTP PUT** Element.

    ![HTTP put-link](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > Sie müssen möglicherweise weitere den nach unten scrollen der Seite (und dieses Image kann nicht genau gleich aussehen, wenn Updates für Azure-Portal ausgeführt wurden), allerdings möchten Sie für ein Element namens *HTTP PUT*.

14. Die **HTTP PUT** Fenster angezeigt wird, müssen Sie die Funktion (siehe unten für Image) konfigurieren.

    1.  Für **Sprache** wählen Sie im Dropdownmenü mit C\#.

    2.  Für **Namen** Geben Sie einen geeigneten Namen.

    3.  In der **Authentifizierungsebene** wählen Sie im Dropdownmenü **Funktion**.

    4.  Für die **Tabellenname** Abschnitt müssen Sie den genauen Namen verwenden Sie zum Erstellen Ihrer **Tabelle** Dienst wurden (einschließlich der gleichen Groß-/Kleinschreibung).

    5.  In der **speicherkontoverbindung** Abschnitt mithilfe des Dropdownmenüs und dann Ihr Speicherkonto aus. Wenn es ist nicht vorhanden, klicken Sie auf die **neu** links neben dem Abschnittstitel, um einen anderen Bereich anzuzeigen, in dem Ihr Speicherkonto aufgelistet werden soll.

        ![mit neuem Speicher](images/AzureLabs-Lab8-40.png)

15. Klicken Sie auf **erstellen** und Sie erhalten eine Benachrichtigung, dass Ihre Einstellungen wurden erfolgreich aktualisiert.

    ![Funktion erstellen](images/AzureLabs-Lab8-41.png)

16. Nach dem Klicken auf **erstellen**, gelangen Sie auf der Funktions-Editor.

    ![Aktualisieren von Funktionscode](images/AzureLabs-Lab8-42.png)

17. Fügen Sie den folgenden Code in der Funktions-Editor (ersetzen Sie den Code in der Funktion):

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > Verwenden den enthaltenen Bibliotheken, die Funktion erhält den Namen und Speicherort des Objekts, das verschoben wurde in der Unity-Szene (als eine C# Objekt, mit dem Namen **UnityGameObject**). Dieses Objekt wird dann verwendet, um die Objektparameter in der erstellten Tabelle zu aktualisieren. Anschluss Ruft die Funktion mit dem erstellten Notification Hub-Dienst, alle abonnierte Anwendungen darüber informiert.

18. Mit diesem Code, klicken Sie auf **speichern**.

19. Klicken Sie anschließend die **\<** Symbol auf der rechten Seite der Seite (Pfeil).

    ![Open-Upload-Bereich](images/AzureLabs-Lab8-43.png)

20. Ein Panel wird in der rechten Seite schieben. In diesem Bereich, klicken Sie auf **hochladen**, und einen Dateibrowser wird angezeigt.

21. Navigieren Sie zu, und klicken Sie auf, die **"Project.JSON"** -Datei, die Sie in erstellt haben **Editor** zuvor, und klicken Sie dann auf die **öffnen** Schaltfläche. Diese Datei definiert die Bibliotheken, die Ihre Funktion verwendet werden.

    ![Hochladen von json](images/AzureLabs-Lab8-44.png)

22. Wenn die Datei hochgeladen wurde, wird es im Bereich auf der rechten Seite angezeigt. Klicken sie auf, öffnen sie in der **Funktion** Editor. Es muss aussehen **genau** identisch mit der nächsten Abbildung (unter Schritt 23).

23. Klicken Sie dann im Bereich auf der linken Seite unter **Funktionen**, klicken Sie auf die **integrieren** Link.

    ![Integrieren der Funktion](images/AzureLabs-Lab8-45.png)

24. Klicken Sie auf der nächsten Seite in der oberen rechten Ecke auf **erweiterter Editor** (wie folgt).

    ![erweiterten Editor öffnen](images/AzureLabs-Lab8-46.png)

25. Ein **"Function.JSON"** Datei wird im mittleren Bereich, der durch den folgenden Codeausschnitt ersetzt werden muss, geöffnet werden. Definiert die Funktion, die Sie erstellen und die Parameter an die Funktion übergeben.

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. Als Editor sollte jetzt wie folgt aussehen:

    ![zurück zum standard-editor](images/AzureLabs-Lab8-47.png)

27. Sie werden feststellen, die Eingabeparameter, die Sie gerade eingefügt haben, entsprechen möglicherweise nicht die Details Ihres Tabellen- und, und aus diesem Grund müssen mit Ihren Informationen aktualisiert werden. **Verwenden Sie keine hier**, wie sie als Nächstes abgedeckt wird. Klicken Sie einfach auf die **Standardeditor** Link in der oberen rechten Ecke der Seite, um zurückzukehren.

28. In der **Standardeditor**, klicken Sie auf **Azure Table Storage (Tabelle)** unter **Eingaben**. 
    
    ![Eingaben für Tabellen](images/AzureLabs-Lab8-47-5.png)

29. Stellen Sie sicher die folgende Übereinstimmung zu **Ihre** Informationen, wie sie verschieden sein können (es gibt ein Bild auf die folgenden Schritte aus):

    1.  **Tabellenname**: der Name der Tabelle, die Sie in Ihrem Azure Storage Tables-Dienst erstellt.

    2.  **Speicherkontoverbindung:** klicken Sie auf **neue**, die zusammen mit dem Dropdown-Menü angezeigt wird und ein Bereich wird angezeigt, die den rechten Rand des Fensters.

        ![mit neuem Speicher](images/AzureLabs-Lab8-48.png)

        1.  Wählen Sie Ihre **Speicherkonto**, die Sie zuvor erstellt haben, auf dem Host die **Funktions-Apps.**

        2. Sie werden feststellen, dass die **Speicherkonto** Verbindung-Wert erstellt wurde.

        3. Achten Sie darauf, drücken die **speichern** sobald Sie fertig sind.

    3.  Die **Eingaben** Seite sollte jetzt übereinstimmen. die unten zeigt **Ihre** Informationen.

        ![Ausführen von Eingaben](images/AzureLabs-Lab8-49.png)

30. Klicken Sie anschließend **Azure Notification Hub (Benachrichtigung)** – unter **Ausgaben**. Stellen Sie sicher, die folgenden zugeordnet sind **Ihre** Informationen, wie sie verschieden sein können (es gibt ein Bild auf die folgenden Schritte aus):

    1.  **Notification Hub-Namen**: Dies ist der Name der Ihrer **Benachrichtigungs-Hub** Service-Instanz, die Sie zuvor erstellt haben.

    2.  **Namespaceverbindung für Notification Hubs**: Klicken Sie auf **neue**, die zusammen mit dem Dropdown-Menü angezeigt wird.

        ![Überprüfen Sie die Ausgaben](images/AzureLabs-Lab8-50.png)

    3. Die **Verbindung** Popupfenster wird angezeigt (siehe Abbildung unten), müssen Sie wählen die **Namespace** von der **Benachrichtigungs-Hub**, die Sie zuvor eingerichtet haben.

    4. Wählen Sie Ihre **Benachrichtigungs-Hub** Name aus dem mittleren Dropdownmenü aus.

    5.  Legen Sie die **Richtlinie** Dropdownmenü **DefaultFullSharedAccessSignature**.

    6. Klicken Sie auf die **wählen** Schaltfläche, um zurückzukehren.

        ![Ausgabe aktualisieren](images/AzureLabs-Lab8-51.png)

31.  Die **Ausgaben** Seite sollte jetzt entsprechen die im folgenden, jedoch mit **Ihre** Informationen stattdessen. Achten Sie darauf, drücken die **speichern**.

> [!WARNING]
> *Bearbeiten Sie den Notification Hub-Namen nicht direkt* (Dies sollte alle erfolgen mithilfe der **Erweiterter Editor**, sofern Sie die vorherigen Schritte richtig befolgt.

![Ausgaben abgeschlossen](images/AzureLabs-Lab8-50.png)

32. An diesem Punkt sollten Sie testen die Funktion, um sicherzustellen, dass sie funktioniert. Gehen Sie dazu wie folgt vor: 

    1. Navigieren Sie zu der Seite "Funktion" einmal an:

        ![Ausgaben abgeschlossen](images/AzureLabs-Lab8-50-1.png)

    2. Klicken Sie auf der Seite "Funktion" auf die **Test** Registerkarte ganz rechts neben der Seite zu öffnen der *Test* Blatt:

        ![Ausgaben abgeschlossen](images/AzureLabs-Lab8-50-2.png)

    3. In der **Anforderungstext** Textfeld auf dem Blatt, fügen Sie den folgenden Code:

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. Der Testcode vorhanden, und klicken Sie auf die **ausführen** Schaltfläche unten rechts, und der Test ausgeführt wird. Die Ausgabeprotokolle des Tests werden im Konsolenfensterbereich unter Ihrem Funktionscode angezeigt.

        ![Ausgaben abgeschlossen](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > Wenn der oben genannten Test fehlschlägt, benötigen Sie überprüfen, dass Sie die oben genannten Schritte genau befolgt haben vor allem die Einstellungen in der **integrieren Bereich**. 

## <a name="chapter-7---set-up-desktop-unity-project"></a>Kapitel 7: Einrichten von Unity-Projekt für Desktop

> [!IMPORTANT]
> Die Desktopanwendung, mit der Sie jetzt erstellen, **nicht** im Unity-Editor arbeiten. Es muss außerhalb des Editors, und befolgen die Erstellung von der Anwendung mithilfe von Visual Studio (oder die bereitgestellte Anwendung) ausgeführt werden. 

Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit Unity und mixed Reality und daher ist eine gute Vorlage für andere Projekte.

Richten Sie ein und Testen Sie Ihrer mixed Reality immersive Kopfhörer.

> [!NOTE] 
> Sie **nicht** Motion-Controller für dieses Kurses erforderlich. Wenn Sie die Einrichtung der immersive Kopfhörer unterstützen müssen, befolgen Sie diese [Link zum Einrichten von Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Open **Unity** , und klicken Sie auf **neu**.

    ![Neues Unity-Projekt](images/AzureLabs-Lab8-52.png)

2.  Sie benötigen, geben Sie einen Namen für die Unity-Projekt, das Einfügen **UnityDesktopNotifHub**. Stellen Sie sicher, dass der Projekttyp nastaven NA hodnotu **3D**. Legen Sie die **Speicherort** auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser). Klicken Sie auf **projekterstellung**.

    ![Projekt erstellen](images/AzureLabs-Lab8-53.png)

3.  Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**. Wechseln Sie zu **Bearbeiten > Voreinstellungen** und navigieren Sie dann im neuen Fenster zu **externe Tools**. Änderung **externen Skript-Editors** zu **Visual Studio 2017**. Schließen der **Voreinstellungen** Fenster.

    ![externe Satz Visual Studio-tools](images/AzureLabs-Lab8-54.png)

4.  Öffnen Sie als Nächstes **Datei > Buildeinstellungen** , und wählen Sie **universelle Windows-Plattform**, klicken Sie dann auf die **Plattform wechseln** Schaltfläche, um Ihre Auswahl anzuwenden.

    ![Plattform wechseln](images/AzureLabs-Lab8-55.png)

5.  In der **Datei > Buildeinstellungen**, stellen Sie sicher, dass:

    1.  **Geräte** nastaven NA hodnotu **einem beliebigen Gerät**

        > Diese Anwendung für den Desktop, muss daher **einem beliebigen Gerät**

    2.  **Buildtyp** nastaven NA hodnotu **D3D**

    3.  **SDK** nastaven NA hodnotu **zuletzt installierte**

    4.  **Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**

    5.  **Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**

    6.  Hier lohnt sich die Szene speichern und mit dem Build hinzufügen.

        1. Hierzu **öffnen Szenen hinzufügen**. Ein Speichern Fenster wird angezeigt.

            ![Hinzufügen von öffnen-Szenen](images/AzureLabs-Lab8-56.png)

        2. Erstellen einen neuen Ordner für, und alle zukünftigen, Szene, klicken Sie dann auf die **neuer Ordner** Schaltfläche zum Erstellen eines neuen Ordners, nennen Sie sie **Szenen**.

            ![neuen Ordner "Szenen"](images/AzureLabs-Lab8-57.png)

        3. Öffnen Sie den neu erstellten **Szenen** Ordner, und klicken Sie dann in der **Dateiname:** Textfeld **Notification Hub\_Desktop\_Szene**, drücken Sie dann die **Speichern**.

            ![neue NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  Die Einstellungen im verbleibenden **Buildeinstellungen**, sollte jetzt als Standard bleiben.

6.  Klicken Sie in demselben Fenster auf die **Playereinstellungen** Schaltfläche Dies öffnet den entsprechenden Bereich im Bereich, in dem die **Inspektor** befindet.

7.  In diesem Bereich sind müssen einige Einstellungen überprüft werden:

    1.  In der **Weitere Einstellungen** Registerkarte:

        1.  **Scripting Runtime Version** muss **experimentell (.NET 4.6 Äquivalent)**

        2. **Back-End-Scripting** muss **.NET**

        3. **API-Kompatibilitätsebene** muss **.NET 4.6**

            ![net-Version 4.6](images/AzureLabs-Lab8-59.png)

    2.  In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:

        - **InternetClient**

            ![Takt-Internetclient](images/AzureLabs-Lab8-60.png)

8.  Im **Buildeinstellungen** *Unity C\# Projekte* nicht mehr abgeblendet ist, aktivieren Sie das Kontrollkästchen neben dieser.

9.  Schließen der **Buildeinstellungen** Fenster.

10. Speichern Sie Ihre Szene und das Projekt **Datei > Szene speichern* / * Datei > Speichern Projekt **.

    > [!IMPORTANT]
    > Wenn Sie, überspringen möchten die *Unity einrichten* Komponente für dieses Projekt (Desktop-App), weiterhin direkt in Code, und Sie gerne [Herunterladen dieser .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), importieren Sie es in Ihr Projekt als eine [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), und klicken Sie dann eine Fortsetzung [Kapitel 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).  Sie müssen weiterhin die Skriptkomponenten hinzufügen.

## <a name="chapter-8---importing-the-dlls-in-unity"></a>Kapitel 8 – Importieren von die DLLs in Unity

Verwenden Sie Azure Storage für Unity (die wiederum nutzt das .net SDK für Azure). Weitere Informationen führen Sie diesen [Link zu Azure Storage für Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).

Es befindet sich derzeit ein bekanntes Problem in Unity-Plug-Ins neu konfiguriert werden, nach dem Import erfordert. Diese Schritte (4 bis 7 in diesem Abschnitt) ist nicht mehr erforderlich, nachdem der Fehler behoben wurde.

Um das SDK in Ihr eigenes Projekt zu importieren, stellen Sie sicher, dass Sie heruntergeladen haben, die neueste Version [ **.unitypackage** ](https://aka.ms/azstorage-unitysdk) aus GitHub. Führen Sie anschließend folgende Schritte aus:

1.  Hinzufügen der **.unitypackage** in Unity mithilfe der **Assets \> Paket importieren \> Custom Package** Option des Menüs.

2.  In der **Unity-Paket importieren** Feld angezeigt, alles unter können Sie auswählen ***-Plug-Ins* \> * Storage ***.  Deaktivieren Sie alles andere, da sie für diesen Kurs nicht benötigt wird.

    ![Paket importieren](images/AzureLabs-Lab8-61.png)

3.  Klicken Sie auf die ***Import*** , um die Elemente zu Ihrem Projekt hinzuzufügen.

4.  Wechseln Sie zu der **Storage** Unterordner **-Plug-Ins** im Projekt anzuzeigen, und wählen Sie die folgenden Plug-Ins *nur*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

![Deaktivieren Sie jede Plattform](images/AzureLabs-Lab8-62.png)

5.  Mit *bestimmte Plug-Ins* ausgewählt, **deaktivieren** **Any Platform** und **deaktivieren** **WSAPlayer** Klicken Sie dann auf **übernehmen**.

    ![Anwenden von Plattform-dlls](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > Wir markieren diese bestimmten Plug-Ins, die nur im Unity-Editor verwendet werden. Dies ist, da es gibt verschiedene Versionen der gleichen Plug-Ins in das WSA-Ordner, der verwendet wird und nachdem das Projekt aus Unity exportiert werden.

6.  In der **Storage** -Plug-in-Ordner, wählen Sie nur:

    -   Microsoft.Data.Services.Client

        ![Gruppe nicht für DLL-Dateien verarbeiten](images/AzureLabs-Lab8-64.png)

7.  Überprüfen Sie die **Don't Prozess** Feld **Plattformeinstellungen** , und klicken Sie auf ***übernehmen***.

    ![keine Verarbeitung anwenden](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > Wir werden dieses Plug-in "Nicht verarbeiten", markieren, da die Unity-Assembly-Patcher schwierigkeiten beim Verarbeiten dieses Plug-in ist. Das Plug-in funktioniert weiterhin, auch wenn sie nicht verarbeitet wurde.

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a>Kapitel 9 – erstellen Sie die TableToScene-Klasse in der Desktop Unity-Projekt

Nun müssen Sie die Skripts, die den Code zum Ausführen dieser Anwendung zu erstellen.

Ist das erste Skript, das Sie erstellen müssen **TableToScene**, die für verantwortlich ist:

-   Lesen von Entitäten innerhalb der Azure-Tabelle.
-   Die Daten dieser Tabelle, bestimmen, welche Objekte zu erzeugen, und an welcher Position.

Ist das zweite Skript, das Sie erstellen müssen **CloudScene**, die für verantwortlich ist:

-   Registrieren das Ereignis klicken, um dem Benutzer ermöglichen, Objekte in der Szene ziehen.
-   Serialisieren von Daten des Objekts, von diese Unity-Szene, und sie an der Azure-Funktions-App senden.

Diese Klasse zu erstellen:

1.  Mit der rechten Maustaste den **Asset** Ordner befindet sich im Projektfenster **erstellen > Ordner**. Nennen Sie den Ordner **Skripts**.

    ![Erstellen Sie Ordner "Scripts"](images/AzureLabs-Lab8-66.png)

    ![Erstellen Sie Ordner "Scripts" 2](images/AzureLabs-Lab8-67.png)

2.  Doppelklicken Sie auf den Ordner, der gerade erstellt haben, um ihn zu öffnen.

3.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen** **C\# Skript**. Nennen Sie das Skript **TableToScene**.

    ![neue c#-Skript](images/AzureLabs-Lab8-68.png)
    ![TableToScene umbenennen](images/AzureLabs-Lab8-69.png)

4.  Doppelklicken Sie auf das Skript aus, um sie in Visual Studio 2017 öffnen.

5.  Fügen Sie die folgenden Namespaces hinzu:

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  Fügen Sie innerhalb der Klasse die folgenden Variablen:

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > Ersetzen der **AccountName** Wert durch den Namen Ihres Azure Storage-Dienst und **AccountKey** Wert mit dem Schlüsselwert finden Sie in den Azure Storage-Dienst im Azure-Portal (siehe Abbildung unten). 
    >
    > ![Abrufen des kontoschlüssels](images/AzureLabs-Lab8-70.png)

7.  Fügen Sie nun die **Start()** und **Awake()** Methoden zum Initialisieren der Klasse.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  In der **TableToScene** Klasse, fügen Sie die Methode, die die Werte aus der Azure-Tabelle abrufen und diese verwenden, um die entsprechenden primitiven in der Szene zu erzeugen.

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  Außerhalb der **TableToScene** -Klasse, müssen Sie die Klasse, die zum Serialisieren und Deserialisieren von der Anwendung verwendeten definieren die **Tabellenentitäten**.

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. Stellen Sie sicher, dass Sie **speichern** vor dem Wechsel zurück zu Unity-Editor.

11. Klicken Sie auf die **Main Camera** aus der **Hierarchie** Bereich, sodass seine Eigenschaften im angezeigt werden die **Inspektor**.

12. Mit der **Skripts** Ordner geöffnet ist, wählen Sie das Skript **TableToScene Datei** und ziehen Sie es auf die **Main Camera**. Das Ergebnis sollte wie folgt:

    ![Hauptkamera Skript hinzugefügt](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a>Kapitel 10 – erstellen Sie die CloudScene-Klasse in der Unity-Projekt für Desktop

Ist das zweite Skript, das Sie erstellen müssen **CloudScene**, die für verantwortlich ist:

-   Registrieren das Ereignis klicken, um dem Benutzer ermöglichen, Objekte in der Szene ziehen.

-   Serialisieren von Daten des Objekts, von diese Unity-Szene, und sie an der Azure-Funktions-App senden.

So erstellen Sie das zweite Skript:

1.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen**, **C\# Skript**. Nennen Sie das Skript **CloudScene**
    
    ![neue c#-Skript](images/AzureLabs-Lab8-72.png)
    ![CloudScene umbenennen](images/AzureLabs-Lab8-73.png)

2.  Fügen Sie die folgenden Namespaces hinzu:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  Fügen Sie die folgenden Variablen:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  Ersetzen der **AzureFunctionEndpoint** Wert mit Ihrem Azure-Funktion-App-URL finden Sie in der Azure-Funktion App Service im Azure-Portal, wie in der folgenden Abbildung gezeigt:

    ![Funktions-URL abrufen](images/AzureLabs-Lab8-74.png)

5.  Fügen Sie nun die **Start()** und **Awake()** Methoden zum Initialisieren der Klasse.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  In der **Update()** -Methode, fügen Sie folgenden Code, mit denen erkannt wird, die Mauseingabe und ziehen Sie, die wiederum "gameobjects" in der Szene verschoben wird. Wenn der Benutzer verfügt über Drag & Drop ein Objekt, es werden die Namen und die Koordinaten des Objekts an die Methode übergeben **UpdateCloudScene()**, ruft die den Azure-Funktions-App-Dienst, das die Azure-Tabelle und der Trigger aktualisiert die die Benachrichtigung.

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  Fügen Sie nun die **UpdateCloudScene()** Methode, wie unten gezeigt:

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  Speichern Sie den Code und zurück zu Unity

9.  Ziehen Sie die **CloudScene** Skript auf die **Main Camera**. 

    1. Klicken Sie auf die **Main Camera** aus der **Hierarchie** Bereich, sodass seine Eigenschaften im angezeigt werden die **Inspektor**. 

    2. Mit der **Skripts** geöffnet ist, wählen die **CloudScene** Skript, und ziehen Sie es auf die **Main Camera**. Das Ergebnis sollte wie folgt:

        > ![Ziehen Sie Cloud-Skript auf Hauptkamera](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a>Kapitel 11: Erstellen Sie das Desktopprojekt UWP

Alles, was Sie für den Unity-Abschnitt, der dieses Projekt wurde jetzt abgeschlossen.

1.  Navigieren Sie zu **Buildeinstellungen** (**Datei > Buildeinstellungen**).

2.  Von der **Buildeinstellungen** Fenster, klicken Sie auf **erstellen**.

    ![Buildprojekt](images/AzureLabs-Lab8-76.png)

3.  Ein **Datei-Explorer** Fenster wird Popup, dem Sie einen Speicherort für den Build aufgefordert werden. Erstellen Sie einen neuen Ordner (indem Sie auf **neuer Ordner** in der oberen linken Ecke), und nennen Sie sie **erstellt**.

    ![neuen Ordner für build](images/AzureLabs-Lab8-77.png)

    1.  Öffnen Sie die neue **erstellt** Ordner, und erstellen Sie einen anderen Ordner (mit **neuer Ordner** einmal), und nennen Sie sie **NH\_Desktop\_App**.

        ![Name des Ordners NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  Mit der **NH\_Desktop\_App** ausgewählten. Klicken Sie auf **wählen Sie Ordner**. Das Projekt wird eine Minute erstellen dauern.

4.  Nach Build **Datei-Explorer** wird angezeigt, die Sie den Standort des neuen Projekts. Nicht erforderlich, um sie zu öffnen, aber wie müssen Sie die andere erstellt Unity Projekt zuerst in den nächsten Kapiteln werden soll.


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a>Kapitel 12: Einrichten von Mixed Reality Unity-Projekt

Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit dem mixed Reality und daher ist eine gute Vorlage für andere Projekte.

1.  Open **Unity** , und klicken Sie auf **neu**.

    ![Neues Unity-Projekt](images/AzureLabs-Lab8-79.png)

2.  Sie müssen nun zum Bereitstellen eines Namen Unity-Projekt einfügen **UnityMRNotifHub**. Stellen Sie sicher, dass der Projekttyp nastaven NA hodnotu **3D**. Legen Sie die **Speicherort** auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser). Klicken Sie auf **projekterstellung**.

    ![name UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**. Wechseln Sie zu **Bearbeiten > Voreinstellungen** und navigieren Sie dann im neuen Fenster zu **externe Tools**. Änderung **externen Skript-Editors** zu **Visual Studio 2017**. Schließen der **Voreinstellungen** Fenster.

    ![externe-Editors in VS](images/AzureLabs-Lab8-81.png)

4.  Öffnen Sie als Nächstes **Datei > Buildeinstellungen** , und wechseln von der Plattform bereitgestellten **universelle Windows-Plattform**, durch Klicken auf die **Plattform wechseln** Schaltfläche.

    ![Plattform für die UWP wechseln](images/AzureLabs-Lab8-82.png)

5.  Wechseln Sie zu **Datei > Buildeinstellungen** und stellen Sie sicher, dass:

    1.  **Geräte** nastaven NA hodnotu **einem beliebigen Gerät**

        > Legen Sie für die Microsoft HoloLens **Zielgerät** zu *HoloLens*.

    2.  **Buildtyp** nastaven NA hodnotu **D3D**

    3.  **SDK** nastaven NA hodnotu **zuletzt installierte**

    4.  **Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**

    5.  **Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**

    6.  Hier lohnt sich die Szene speichern und mit dem Build hinzufügen.

        1. Hierzu **öffnen Szenen hinzufügen**. Ein Speichern Fenster wird angezeigt.

            ![Hinzufügen von öffnen-Szenen](images/AzureLabs-Lab8-83.png)

        2. Erstellen einen neuen Ordner für, und alle zukünftigen, Szene, klicken Sie dann auf die **neuer Ordner** Schaltfläche zum Erstellen eines neuen Ordners, nennen Sie sie **Szenen**.

            ![neuen Ordner "Szenen"](images/AzureLabs-Lab8-84.png)

        3. Öffnen Sie den neu erstellten **Szenen** Ordner, und klicken Sie dann in der **Dateiname:** Textfeld **NH\_MR\_Szene**, drücken Sie dann die  **Speichern Sie**.

            ![neue Szene - NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  Die Einstellungen im verbleibenden **Buildeinstellungen**, sollte jetzt als Standard bleiben.

6.  Klicken Sie in demselben Fenster auf die **Playereinstellungen** Schaltfläche Dies öffnet den entsprechenden Bereich im Bereich, in dem die **Inspektor** befindet.    

    ![Öffnen der playereinstellungen](images/AzureLabs-Lab8-86.png)

7.  In diesem Bereich sind müssen einige Einstellungen überprüft werden:

    1.  In der **Weitere Einstellungen** Registerkarte:

        1.  **Scripting Runtime Version** muss **experimentell** (.NET 4.6 Äquivalent)
        2.  **Back-End-Scripting** muss ***.NET***
        3.  **API-Kompatibilitätsebene** muss **.NET 4.6**

            ![API-Kompatibilität](images/AzureLabs-Lab8-87.png)

    2.  Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality-SDK**  wird hinzugefügt

        ![Aktualisieren der Xr-Einstellungen](images/AzureLabs-Lab8-88.png)        

    3.  In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, prüfen:

        - **InternetClient**           

            ![Takt-Internetclient](images/AzureLabs-Lab8-89.png)

8.  Im **Buildeinstellungen** *Unity C\# Projekte* ist nicht mehr abgeblendet: Aktivieren Sie das Kontrollkästchen neben dieser.

9.  Schließen Sie mit diesen Änderungen durchgeführt, und das Build Settings-Fenster.

10. Speichern Sie Ihre Szene und das Projekt **Datei* *Szene speichern*/ *Datei* * speichern Projekt **.

    > [!IMPORTANT]
    > Wenn Sie, überspringen möchten der *Unity einrichten* für dieses Projekt (mixed Reality-App)-Komponente weiterhin direkt in Code, und Sie gerne [Herunterladen dieser .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), importieren Sie es in Ihr Projekt als eine [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), und klicken Sie dann eine Fortsetzung [Kapitel 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project). Sie müssen weiterhin die Skriptkomponenten hinzufügen.

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a>Kapitel 13 – Importieren von die DLLs im Unity-Projekts Mixed Reality

Sie werden Azure Storage für Unity-Bibliothek verwenden (das das .net SDK für Azure verwendet wird). Führen Sie dies [Link zur Verwendung von Azure Storage mit Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).
Es befindet sich derzeit ein bekanntes Problem in Unity-Plug-Ins neu konfiguriert werden, nach dem Import erfordert. Diese Schritte (4 bis 7 in diesem Abschnitt) ist nicht mehr erforderlich, nachdem der Fehler behoben wurde.

Um das SDK in Ihr eigenes Projekt zu importieren, stellen Sie sicher, dass Sie heruntergeladen haben, die neueste Version [.unitypackage](https://aka.ms/azstorage-unitysdk). Führen Sie anschließend folgende Schritte aus:

1.  Hinzufügen der .unitypackage, die Sie aus den oben genannten, in Unity mithilfe heruntergeladen der **Assets > Paket importieren > benutzerdefiniertes Paket** Option des Menüs.

2.  In der **Unity-Paket importieren** Feld angezeigt, alles unter können Sie auswählen **-Plug-in > Speicher**.

    ![Paket importieren](images/AzureLabs-Lab8-90.png)

3.  Klicken Sie auf die **Import** , um die Elemente zu Ihrem Projekt hinzuzufügen.

4.  Wechseln Sie zu der **Storage** Unterordner **-Plug-Ins** im Projekt anzuzeigen, und wählen Sie die folgenden Plug-Ins *nur*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

    ![Wählen Sie-Plug-Ins](images/AzureLabs-Lab8-91.png)

5.  Mit *bestimmte Plug-Ins* ausgewählt, **deaktivieren** **Any Platform** und **deaktivieren** **WSAPlayer** Klicken Sie dann auf **übernehmen**.

    ![Anwenden von plattformänderungen](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > Markieren Sie diese bestimmten Plug-Ins, die nur im Unity-Editor verwendet werden. Dies ist, da es gibt verschiedene Versionen der gleichen Plug-Ins in das WSA-Ordner, der verwendet wird und nachdem das Projekt aus Unity exportiert werden.

6.  In der **Storage** -Plug-in-Ordner, wählen Sie nur:

    -   Microsoft.Data.Services.Client

        ![Data Services-Client auswählen](images/AzureLabs-Lab8-93.png)

7.  Überprüfen Sie die **Don't Prozess** Feld **Plattformeinstellungen** , und klicken Sie auf **übernehmen**.

    ![nicht verarbeiten](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > Sie werden dieses Plug-in "Nicht verarbeiten" markieren, da die Unity-Assembly-Patcher schwierigkeiten beim Verarbeiten dieses Plug-in ist. Das Plug-in funktioniert weiterhin, auch wenn es nicht verarbeitet ist.

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a>Kapitel 14: Erstellen der TableToScene-Klasse in mixed Reality Unity-Projekts

Die **TableToScene** Klasse ist identisch mit dem im erläutert [Kapitel 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project). Erstellen Sie die gleiche Klasse in gemischten Unity-Projekt die gleichen Schritte, in erläutert Wirklichkeit [Kapitel 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).

Nachdem Sie in diesem Kapitel, beide haben Ihre **Unity-Projekte** wird diese Klasse, die auf den Main Camera eingerichtet haben.

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a>Kapitel 15: Erstellen der NotificationReceiver-Klasse in Mixed Reality Unity-Projekts

Ist das zweite Skript, das Sie erstellen müssen **NotificationReceiver**, die für verantwortlich ist:

-   Beim Registrieren der app beim Notification Hub bei der Initialisierung.
-   Von den Notification Hub-Benachrichtigungen überwacht.
-   Deserialisiert die Daten des Objekts aus dem empfangenen Benachrichtigungen an.
-   Verschieben Sie die "gameobjects" in der Szene, basierend auf den deserialisierten Daten.

Zum Erstellen der **NotificationReceiver** Skript:

1.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen**, **C\# Skript**. Nennen Sie das Skript **NotificationReceiver**.

    ![Erstellen Sie neue c#-Skript](images/AzureLabs-Lab8-95.png)
    ![NotificationReceiver Namen](images/AzureLabs-Lab8-96.png)

2.  Doppelklicken Sie auf das Skript aus, um ihn zu öffnen.

3.  Fügen Sie die folgenden Namespaces hinzu:

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  Fügen Sie die folgenden Variablen:

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  Ersetzen der **HubName** Wert durch den Namen Ihres Notification Hubs-Dienst und **HubListenEndpoint** Wert mit den Endpunktwert finden Sie in der Registerkarte "Zugriffsrichtlinien" Azure Notification Hubs-Dienst, in der Azure-Portal (siehe Abbildung unten).

    ![Einfügen von Notification Hubs-Richtlinie-Endpunkt](images/AzureLabs-Lab8-97.png)

6.  Fügen Sie nun die **Start()** und **Awake()** Methoden zum Initialisieren der Klasse.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  Hinzufügen der **WaitForNotification** Methode, um die app Benachrichtigungen aus der Bibliothek der Notification Hub empfangen werden, ohne mit den Hauptthread ein Konflikt besteht zuzulassen:

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  Die folgende Methode, **InitNotificationAsync()**, registrieren Sie die Anwendung wird mit dem Notification Hub-Dienst bei der Initialisierung. Der Code ist auskommentiert, wie Unity nicht zum Erstellen des Projekts kann. Sie werden die Kommentare entfernen, wenn Sie das Azure-Messaging-Nuget-Paket in Visual Studio importieren.

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  Der folgende Handler, **Kanal\_PushNotificationReceived()**, wird jedes Mal, wenn eine Benachrichtigung empfangen wird ausgelöst. Es wird die Benachrichtigung Deserialisieren der wird die Azure Table Storage-Entität, die auf die Desktop-Anwendung verschoben wurden, und klicken Sie dann das entsprechende "gameobject" in der Szene MR an dieselbe Position verschieben. 
    
    > [!IMPORTANT]
    > Der Code ist auskommentiert, da der Code die Azure-Messaging-Bibliothek verweist, die Sie nach dem Erstellen des Nuget-Paket-Managers in Visual Studio mit Unity-Projekts hinzufügen. Daher wird das Unity-Projekt nicht erstellen, können es sei denn, er ist auskommentiert ist. Beachten Sie, sollten Sie Ihr Projekt erstellen und anschließend zu Unity zurückgeben möchten, müssen Sie **wieder mit Kommentaren versehen** dieses Codes.

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. Denken Sie daran, um die Änderungen zu speichern, vor dem Wechsel zurück zu Unity-Editor.

11. Klicken Sie auf die **Main Camera** aus der **Hierarchie** Bereich, sodass seine Eigenschaften im angezeigt werden die **Inspektor**.

12. Mit der **Skripts** geöffnet ist, wählen die **NotificationReceiver** Skript, und ziehen Sie es auf die **Main Camera**. Das Ergebnis sollte wie folgt:

    ![Ziehen Sie Empfänger Benachrichtigungsskript an Kamera](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > Wenn Sie dies für die Microsoft HoloLens entwickeln, müssen Sie zum Aktualisieren der **Main Camera**des *Kamera* -Komponente, damit:
    > - Flags zu löschen: Volltonfarbe
    > - Hintergrund: Schwarz

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a>Kapitel 16 – erstellen Sie das Mixed Reality-Projekt auf UWP

In diesem Kapitel ist identisch mit der Prozess für das vorherige Projekt zu erstellen. Alles, was Sie für den Unity-Abschnitt, der dieses Projekt wurde jetzt abgeschlossen daher ist es Zeit für die Erstellung von Unity.

1.  Navigieren Sie zu **Buildeinstellungen** ( **Datei > Buildeinstellungen...**  ).

2.  Von der **Buildeinstellungen** Menü, stellen Sie sicher **Unity C# Projekte*** ist (sodass Sie so bearbeiten Sie die Skripts in diesem Projekt nach dem Build).

3.  Nachdem dies geschehen ist, klicken Sie auf **erstellen**.

    ![Buildprojekt](images/AzureLabs-Lab8-99.png)

4.  Ein **Datei-Explorer** Fenster wird Popup, dem Sie einen Speicherort für den Build aufgefordert werden. Erstellen Sie einen neuen Ordner (indem Sie auf **neuer Ordner** in der oberen linken Ecke), und nennen Sie sie **erstellt**.

    ![Erstellen Sie Ordner "Builds"](images/AzureLabs-Lab8-100.png)

    1.  Öffnen Sie die neue **erstellt** Ordner, und erstellen Sie einen anderen Ordner (mit **neuer Ordner** einmal), und nennen Sie sie **NH\_MR\_App**.

        ![Erstellen Sie NH_MR_Apps-Ordner](images/AzureLabs-Lab8-101.png)

    2.  Mit der **NH\_MR\_App** ausgewählten. Klicken Sie auf **wählen Sie Ordner**. Das Projekt wird eine Minute erstellen dauern.

5.  Folgen den Build, eine **Datei-Explorer** Fenster wird geöffnet, an der Position des neuen Projekts.



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a>Kapitel 17: Hinzufügen von NuGet-Pakete der Projektmappe UnityMRNotifHub

> [!WARNING] 
> Bitte denken Sie daran, dass sobald Sie die folgenden NuGet-Pakete hinzufügen (und entfernen Sie den Code in den nächsten [Kapitel](#chapter-18---edit-unitymrnotifhub-application,-notificationreciever-class)), der Code, wenn in der Unity-Projekt erneut geöffnet werden Fehler angezeigt. Wenn Sie möchten, wechseln zurück und weiter im Unity-Editor bearbeiten, müssen Sie Errosome Code kommentieren, und klicken Sie dann kommentieren es später noch Mal, wenn Sie in Visual Studio sind. 

Sobald der mixed Reality-Build abgeschlossen wurde, navigieren Sie zu dem mixed Reality-Projekt, das Sie erstellt, und doppelklicken auf die Projektmappendatei (.sln) in diesem Ordner, um die Projektmappe mit Visual Studio 2017 geöffnet.
Sie müssen sich jetzt hinzufügen der **WindowsAzure.Messaging.managed** NuGet-Paket; Dies ist eine Bibliothek, die zum Empfangen von Benachrichtigungen vom Notification Hub verwendet wird.

So importieren Sie das NuGet-Paket:

1.  In der **Projektmappen-Explorer**, klicken Sie mit der rechten Maustaste auf die Projektmappe

2.  Klicken Sie auf **NuGet-Pakete verwalten**.

    ![Öffnen Sie den Nuget-manager](images/AzureLabs-Lab8-102.png)

3.  Wählen Sie die ***Durchsuchen*** Registerkarte und suchen Sie nach **WindowsAzure.Messaging.managed**.

    ![Windows Azure-messaging-Paket zu finden](images/AzureLabs-Lab8-103.png)

4.  Wählen Sie das Ergebnis (wie unten gezeigt), und wählen Sie im Fenster auf der rechten Seite das Kontrollkästchen neben **Projekt**. Dies wird setzen einen Teilstrich in das Kontrollkästchen neben **Projekt**, sowie das Kontrollkästchen neben der **Assembly-CSharp** und **UnityMRNotifHub** Projekt.

    ![Aktivieren Sie alle Projekte](images/AzureLabs-Lab8-104.png)

5.  Die ursprünglich bereitgestellte Version **möglicherweise nicht** mit diesem Projekt kompatibel sein. Aus diesem Grund, klicken Sie auf das Dropdownmenü neben **Version**, und klicken Sie auf **Version 0.1.7.9**, klicken Sie dann auf **installieren**.

6.  Installieren das NuGet-Paket ist jetzt beendet. Suchen Sie den kommentierten Code, der Sie eingegeben, in haben der **NotificationReceiver** Klasse, und die Kommentare entfernen...



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a>Kapitel 18 – bearbeiten UnityMRNotifHub-Anwendung, NotificationReceiver-Klasse

Folgende hinzugefügt haben die **NuGet-Pakete**, müssen Sie *auskommentierung* Teil des Codes in der **NotificationReceiver** Klasse.

Dazu zählen:

1. Der Namespace am Anfang:

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. Sämtlichen Code innerhalb der **InitNotificationsAsync()** Methode:

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> Der obige Code enthält einen Kommentar: Stellen Sie sicher, dass Sie nicht versehentlich haben *unkommentierten* , der Kommentar (wie der Code nicht kompiliert, wenn man!).

3. Und schließlich die **Channel_PushNotificationReceived** Ereignis:

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

Mit diesen auskommentiert werden können stellen Sie sicher, dass Sie speichern, und fahren Sie mit der im nächsten Kapitel.

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a>Kapitel 19: Ordnen Sie die mixed Reality-Projekt auf die Store-app

Sie müssen jetzt Zuordnen der **mixed Reality** Projekt, um die Store-App, die Sie am Anfang des Labs in erstellt.

1.  Öffnen Sie die Projektmappe.

2.  Klicken Sie mit der rechten Maustaste auf die UWP-app-Projekt im Projektmappen-Explorer-Bereich, der zum Aufrufen **Store**, und **App mit dem Store verknüpfen...** .

    ![Öffnen Sie die Store-Verknüpfung](images/AzureLabs-Lab8-105.png)

3.  Ein neues Fenster wird angezeigt namens **zuordnen Ihrer Anwendung die Windows Store**. Klicken Sie auf **Weiter**.

    ![Wechseln Sie zum nächsten Bildschirm](images/AzureLabs-Lab8-106.png)

4.  Es lädt alle Anwendungen, die das Konto, das Sie sich angemeldet haben zugeordnet. Wenn Sie nicht mit Ihrem Konto angemeldet sind, können Sie **anmelden** auf dieser Seite.

5.  Suchen der **Store-App-Namen** , die Sie zu Beginn dieses Tutorials erstellt, und wählen Sie ihn. Klicken Sie dann auf **Weiter**.

    ![Suchen Sie, und wählen Sie Ihren Store-Namen](images/AzureLabs-Lab8-107.png)

6.  Klicken Sie auf **zuordnen**.

    ![Verknüpfen Sie die app](images/AzureLabs-Lab8-108.png)

7.  Ihre App ist nun **zugeordnete** mit der Store-App. Dies ist zum Aktivieren von Benachrichtigungen erforderlich.

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a>Kapitel 20: UnityMRNotifHub und UnityDesktopNotifHub Anwendungen bereitstellen

In diesem Kapitel kann einfacher, mit zwei Personen sein, wie das Ergebnis enthält sowohl apps, die ausgeführt wird, eine Ausführung auf Ihrem Desktop-Computer und der andere in Ihrem immersive Kopfhörer.

Die immersive Kopfhörer app wartet darauf, um Änderungen an der Szene (Position ändert sich von der lokalen "gameobjects") zu erhalten, und die Desktop-app wird werden Änderungen an ihren lokalen Szene (Position ändert), die an die MR app gemeinsam genutzt werden. Es sinnvoll, die app MR zuerst bereitstellen gefolgt von der Desktop-app, sodass der Empfänger lauscht beginnen kann.

Zum Bereitstellen der **UnityMRNotifHub** -app auf Ihrem lokalen Computer:

1.  Öffnen Sie die Projektmappendatei, die von Ihrem **UnityMRNotifHub** -app in **Visual Studio 2017**.

2.  In der **Projektmappenplattform**Option **X86, lokalen Computer**.

3.  In der **Projektmappenkonfiguration** wählen **Debuggen**.

    ![Set-Projektkonfiguration](images/AzureLabs-Lab8-109.png)

4.  Wechseln Sie zu **Menü "Build"** und klicken Sie auf **Projektmappe bereitstellen** zum querladen der Anwendung auf Ihrem Computer.

5.  Ihre App sollte nun in der Liste der installierten apps, die zu startenden bereit angezeigt werden.

Zum Bereitstellen der **UnityDesktopNotifHub** -app auf dem lokalen Computer:

1.  Öffnen Sie die Projektmappendatei, die von Ihrem **UnityDesktopNotifHub** -app in **Visual Studio 2017**.

2.  In der **Projektmappenplattform**Option **X86, lokalen Computer**.

3.  In der **Projektmappenkonfiguration** wählen **Debuggen**.

    ![Set-Projektkonfiguration](images/AzureLabs-Lab8-110.png)

4.  Wechseln Sie zu **Menü "Build"** und klicken Sie auf **Projektmappe bereitstellen** zum querladen der Anwendung auf Ihrem Computer.

5.  Ihre App sollte nun in der Liste der installierten apps, die zu startenden bereit angezeigt werden.

6.  Starten Sie die mixed Reality-Anwendung, und anschließend die Desktop-Anwendung.

Verschieben Sie mit beiden Anwendungen, die ausgeführt wird ein Objekt in der desktop Szene (mit der linken Maustaste). Diese Änderungen mit Feldern fester Breite werden lokal vorgenommen, serialisiert und an den Funktions-App-Dienst gesendet werden. Der Funktions-App-Dienst wird dann in der Tabelle zusammen mit dem Notification Hub aktualisieren. Müssen wurde ein Update, sendet Notification Hub aktualisierte die Daten direkt an alle registrierten Anwendungen (in diesem Fall die immersive Kopfhörer-app), die dann die eingehenden Daten zu deserialisieren, und die neuen mit Feldern fester Breite Daten auf die lokalen Objekte anwenden, Verschieben sie in der Szene.


## <a name="your-finished-your-azure-notification-hubs-application"></a>Ihre beendet die Anwendung für Azure Notification Hubs
 
Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die den Azure Notification Hubs-Dienst nutzt, und ermöglichen die Kommunikation zwischen apps.
 
![Endprodukt-Ende](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a>Bonus-Übungen

### <a name="exercise-1"></a>Übung 1

Können Sie werden verwendet, wie Sie die Farbe der "gameobjects" ändern, und senden diese Benachrichtigung an andere apps, die die Szene anzeigen?

### <a name="exercise-2"></a>Übung 2

Können Sie Ihre app MR Verschiebung von der "gameobjects" hinzu, und finden Sie in Ihrer desktop-app unter der Szene aktualisiert?
