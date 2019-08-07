---
title: Mr und Azure 308-Geräte übergreifende Benachrichtigungen
description: Machen Sie sich mit diesem Kurs vertraut, um zu erfahren, wie Sie Azure Notification Hubs, Azure Functions und Azure Storage und Tabellen in einer Mixed Reality-Anwendung implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Benachrichtigung, Funktionen, Tabellen, Notification Hubs, hololens, immersive, VR
ms.openlocfilehash: 3b6e930acd81c7d6e3addc107ec0da605d38cad1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694607"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a>Mr und Azure 308: Geräte übergreifende Benachrichtigungen

![Endgültiges Produkt-Start](images/AzureLabs-Lab8-00.png)

In diesem Kurs erfahren Sie, wie Sie mithilfe von Azure Notification Hubs, Azure-Tabellen und Azure Functions Notification Hubs Funktionen zu einer gemischten Reality-Anwendung hinzufügen.

**Azure Notification Hubs** ist ein Microsoft-Dienst, der es Entwicklern ermöglicht, gezielte und personalisierte Pushbenachrichtigungen an jede beliebige Plattform zu senden, die alle in der Cloud betrieben wird. Dadurch können Entwickler in Abhängigkeit vom jeweiligen Szenario mit Endbenutzern oder sogar zwischen verschiedenen Anwendungen kommunizieren. Weitere Informationen finden Sie auf der [Seite](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview) **Azure Notification Hubs** .

**Azure Functions** ist ein Microsoft-Dienst, der Entwicklern das Ausführen von kleinen Code Elementen ("Functions") in Azure ermöglicht. Dies bietet eine Möglichkeit zum Delegieren von Arbeit an die Cloud und nicht an Ihre lokale Anwendung, die viele Vorteile haben kann. **Azure Functions** unterstützt mehrere Entwicklungs Sprachen, wie\#z.\#b. C, F, Node. js, Java und PHP. Weitere Informationen finden Sie auf der [Seite](https://docs.microsoft.com/azure/azure-functions/functions-overview)Azure Functions.

**Azure-Tabellen** sind ein Microsoft-clouddienst, mit dem Entwickler strukturierte nicht-SQL-Daten in der Cloud speichern können, sodass Sie überall problemlos zugänglich sind. Der Dienst verfügt über einen Schema losen Entwurf, der die Weiterentwicklung von Tabellen nach Bedarf ermöglicht und daher sehr flexibel ist. Weitere Informationen finden Sie auf der [Seite](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) mit den Azure-Tabellen.

Nachdem Sie diesen Kurs abgeschlossen haben, verfügen Sie über eine gemischte Reality-Headset-Anwendung und eine Desktop-PC-Anwendung, die Folgendes ausführen kann:

1. Die Desktop-PC-App ermöglicht dem Benutzer das Verschieben eines Objekts im 2D-Raum (X und Y) mit der Maus.

2. Die Verschiebung von Objekten innerhalb der PC-APP wird mithilfe von JSON an die Cloud gesendet, die in Form einer Zeichenfolge mit einer Objekt-ID, einem Typ und Transformations Informationen (X-und Y-Koordinaten) enthalten ist. 

3. Die Mixed Reality-APP, die über eine identische Szene mit der Desktop-App verfügt, empfängt Benachrichtigungen bezüglich der Objekt Verschiebung aus dem Notification Hubs-Dienst (der soeben von der Desktop-PC-APP aktualisiert wurde). 

4. Wenn Sie eine Benachrichtigung erhalten, die die Objekt-ID, den Typ und die Transformations Informationen enthält, wendet die Mixed Reality-APP die empfangenen Informationen auf die eigene Szene an.

In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren. In diesem Kurs erfahren Sie, wie Sie einen Azure-Dienst in Ihr Unity-Projekt integrieren. Es ist Ihre Aufgabe, das wissen, das Sie aus diesem Kursgewinnen, zu nutzen, um ihre gemischte Reality-Anwendung zu verbessern. Dieser Kurs ist ein eigenständiges Tutorial, das sich nicht direkt mit anderen Mixed Reality-Labs befasst.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> Mr und Azure 308: Geräte übergreifende Benachrichtigungen</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Dieser Kurs konzentriert sich in erster Linie auf Windows Mixed Reality immersive (VR)-Headsets, aber Sie können auch das, was Sie in diesem Kurs lernen, auf Microsoft hololens anwenden. Wenn Sie den Kurs befolgen, finden Sie Hinweise zu allen Änderungen, die Sie möglicherweise zur Unterstützung von hololens verwenden müssen. Wenn Sie hololens verwenden, bemerken Sie möglicherweise bei der sprach Erfassung einen Echo.

## <a name="prerequisites"></a>Vorraussetzungen

> [!NOTE]
> Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen. Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Mai 2018). Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](install-the-tools.md) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt sind.

Für diesen Kurs empfehlen wir die folgende Hardware und Software:

- Einen Entwicklungs-PC, der [mit der Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for Immersive (VR)-Headset-Entwicklung kompatibel ist
- [Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus](install-the-tools.md#installation-checklist)
- [Das neueste Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Ein [Windows Mixed Reality-Headset (VR)](immersive-headset-hardware-details.md) oder [Microsoft hololens](hololens-hardware-details.md) mit aktiviertem Entwicklermodus
- Internet Zugriff für Azure-Setup und für den Zugriff auf Notification Hubs

## <a name="before-you-start"></a>Bevor Sie beginnen

- Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).
- Sie müssen der Besitzer des Microsoft-Entwickler Portals und des Anwendungs Registrierungs Portals sein. andernfalls haben Sie in [Kapitel 2](#chapter-2---retrieve-your-new-apps-credentials)keine Berechtigung für den Zugriff auf die app.

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a>Kapitel 1: Erstellen einer Anwendung im Microsoft-Entwickler Portal

Um den **Azure Notification Hubs** -Dienst zu verwenden, müssen Sie eine Anwendung im Microsoft-Entwickler Portal erstellen, da Ihre Anwendung registriert werden muss, damit Benachrichtigungen gesendet und empfangen werden können.

1.  Melden Sie sich beim [Microsoft-Entwickler Portal](https://developer.microsoft.com/dashboard)an.

    > Sie müssen sich bei Ihrem Microsoft-Konto anmelden.

2.  Klicken Sie im Dashboard auf **neue APP erstellen**.

    ![Erstellen einer APP](images/AzureLabs-Lab8-01.png)

3.  Es wird ein Popup Fenster angezeigt, in dem Sie einen Namen für die neue APP reservieren müssen. Fügen Sie im Textfeld einen entsprechenden Namen ein. Wenn der ausgewählte Name verfügbar ist, wird rechts neben dem Textfeld ein Tick angezeigt. Nachdem Sie einen verfügbaren Namen eingefügt haben, klicken Sie unten links im Popup Fenster auf die Schaltfläche **Produktname reservieren** .

    ![Umkehren eines Namens](images/AzureLabs-Lab8-02.png)

4.  Nachdem Sie die App erstellt haben, können Sie mit dem nächsten Kapitel fortfahren.

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a>Kapitel 2: Abrufen der Anmelde Informationen für neue apps

Melden Sie sich beim Anwendungs Registrierungs Portal an, auf dem die neue APP aufgelistet wird, und rufen Sie die Anmelde Informationen ab, die zum Einrichten des **Notification Hubs Dienstanbieter** im **Azure-Portal**verwendet werden.

1.  Navigieren Sie zum [Anwendungs Registrierungs Portal](http://apps.dev.microsoft.com).

    ![Anwendungs Registrierungs Portal](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > Sie müssen sich für die Anmeldung mit Ihrem Microsoft-Konto anmelden.  
    > Dabei **muss** es sich um das Microsoft-Konto handeln, das Sie im vorherigen [Kapitel](#chapter-1---create-an-application-on-the-microsoft-developer-portal)mit dem Windows Store-Entwickler Portal verwendet haben.

2.  Sie finden Ihre APP im Abschnitt " **meine Anwendungen** ". Nachdem Sie Sie gefunden haben, klicken Sie darauf, und Sie gelangen zu einer neuen Seite, die den APP-Namen und die **Registrierung**enthält.

    ![Ihre neu registrierte App](images/AzureLabs-Lab8-04.png)

3.  Scrollen Sie nach unten auf der Registrierungsseite, um den Abschnitt mit den **geheimen Anwendungen** und die **Paket-sid** für Ihre APP zu finden. Kopieren Sie beide für die Verwendung mit der Einrichtung des **Azure-Notification Hubs Dienstanbieter** im nächsten Kapitel.

    ![Anwendungs Geheimnisse](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a>Kapitel 3: Einrichten des Azure-Portals: Erstellen Notification Hubs Dienstanbieter

Nachdem Sie die Anmelde Informationen für Ihre apps abgerufen haben, müssen Sie zum Azure-Portal wechseln, in dem Sie einen Azure Notification Hubs-Dienst erstellen.

1.  Melden Sie sich beim [Azure-Portal](https://portal.azure.com)an.

    > [!NOTE] 
    > Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen. Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.

2.  Nachdem Sie angemeldet sind, klicken Sie in der oberen linken Ecke auf **neu** , suchen Sie nach **Notification Hub**, und drücken Sie die ***Eingabe***Taste.

    ![nach benachrichtigungshub suchen](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > Das Wort ***New*** wurde möglicherweise durch **Create a Resource**in neueren Portalen ersetzt.

3.  Auf der neuen Seite wird eine Beschreibung des *Notification Hubs* Dienstanbieter bereitgestellt. Wählen Sie unten links in dieser Eingabeaufforderung die Schaltfläche **Erstellen** aus, um eine Verknüpfung mit diesem Dienst zu erstellen.

    ![Benachrichtigungs-Hubs-Instanz erstellen](images/AzureLabs-Lab8-07.png)

4.  Nachdem Sie auf ***Erstellen***geklickt haben, klicken Sie auf:

    1.  Fügen Sie den gewünschten Namen für diese Dienst Instanz ein.

    2.  Geben Sie einen **Namespace** an, den Sie dieser APP zuordnen können.

    3.  Wählen Sie einen **Speicherort aus.**

    4.  Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** . Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Labs) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie unter diesem [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal). 

    5.  Wählen Sie ein entsprechendes **Abonnement**aus.

    6.  Außerdem müssen Sie bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.

    7. Wählen Sie **Erstellen** aus.

        ![Dienst Details ausfüllen](images/AzureLabs-Lab8-08.png)

5.  Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.

6.  Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Benachrichtigung](images/AzureLabs-Lab8-09.png)

7.  Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen. Sie gelangen zu ihrer neuen **Notification Hub** -Dienst Instanz.

    ![Gehe zu Ressource](images/AzureLabs-Lab8-10.png)
    
8.  Klicken Sie auf der Übersichtsseite in der Mitte der Seite auf **Windows (WNS).** Der Bereich auf der rechten Seite ändert sich, um zwei Textfelder anzuzeigen, die die **Paket-sid** und den **Sicherheitsschlüssel**benötigen, von der APP, die Sie zuvor eingerichtet haben.

    ![neu erstellter Hubs-Dienst](images/AzureLabs-Lab8-11.png)

9. Nachdem Sie die Details in die richtigen Felder kopiert haben, klicken Sie auf **Speichern**, und Sie erhalten eine Benachrichtigung, wenn der Notification Hub erfolgreich aktualisiert wurde.

    ![Sicherheitsdetails kopieren](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a>Kapitel 4: Einrichten des Azure-Portals: Erstellen eines Tabellen Dienstanbieter

Nachdem Sie Ihre Notification Hubs Dienst Instanz erstellt haben, navigieren Sie zurück zu Ihrem Azure-Portal, in dem Sie einen Azure Tables-Dienst erstellen, indem Sie eine Speicher Ressource erstellen.

1.  Wenn Sie noch nicht angemeldet sind, melden Sie sich beim [Azure-Portal](https://portal.azure.com)an.

2.  Wenn Sie angemeldet sind, klicken Sie in der oberen linken Ecke auf **neu** , suchen Sie nach **Speicherkonto**, und drücken Sie die **Eingabe**Taste.

    > [!NOTE] 
    > Das Wort ***New*** wurde möglicherweise durch **Create a Resource**in neueren Portalen ersetzt.

3.  Wählen Sie **Speicherkonto-BLOB, Datei, Tabelle, Warteschlange** aus der Liste aus.

    ![Suchen nach Speicherkonto](images/AzureLabs-Lab8-13.png)

4.  Auf der neuen Seite wird eine Beschreibung des **Speicherkonto** Dienstanbieter bereitgestellt. Wählen Sie unten links in dieser Eingabeaufforderung die Schaltfläche **Erstellen** aus, um eine Instanz dieses Dienstanbieter zu erstellen.

    ![Speicher Instanz erstellen](images/AzureLabs-Lab8-14.png)

5.  Nachdem Sie auf **Erstellen**geklickt haben, wird ein Panel angezeigt:

    1. Fügen Sie den gewünschten **Namen** für diese Dienst Instanz ein (nur Kleinbuchstaben).

    2. Klicken Sie unter **Bereitstellungs Modell**auf **Ressourcen-Manager**.

    3.  Wählen Sie unter **Kontoart**im Dropdown Menü die Option **Speicher (universell v1)** aus.

    4. Wählen Sie einen geeigneten **Speicherort**aus.
    
    5.  Wählen Sie für das Dropdown Menü **Replikation** die Option **Lesezugriff georedundanter Speicher (RA-GRS)** aus.

    6.  Klicken Sie für die **Leistung**auf **Standard**.

    7.  Wählen Sie im Abschnitt **sichere Übertragung erforderlich** die Option **deaktiviert**aus.

    8.  Wählen Sie im Dropdown Menü **Abonnement** ein entsprechendes Abonnement aus.

    9.  Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** . Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Labs) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie unter diesem [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. Lassen Sie **virtuelle Netzwerke** **deaktiviert** , wenn dies eine Option für Sie ist.

    11. Klicken Sie auf **Erstellen**.

        ![Speicher Details ausfüllen](images/AzureLabs-Lab8-15.png)

6.  Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.

7.  Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt. Klicken Sie auf die Benachrichtigungen, um die neue Dienst Instanz zu untersuchen.

    ![neue Speicher Benachrichtigung](images/AzureLabs-Lab8-16.png)

8.  Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen. Sie gelangen zur Übersichtsseite der neuen Speicherdienst Instanz.

    ![Gehe zu Ressource](images/AzureLabs-Lab8-17.PNG)

9. Klicken Sie auf der Seite Übersicht auf die Rechte Seite, und klicken Sie auf **Tabellen**.
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. Der Bereich auf der rechten Seite ändert sich, um die **Tabellen Dienst** Informationen anzuzeigen, in denen Sie eine neue Tabelle hinzufügen müssen. Klicken Sie hierzu auf die **+** **Tabellen** Schaltfläche in der linken oberen Ecke.

    ![Öffnen von Tabellen](images/AzureLabs-Lab8-19.png)

11. Es wird eine neue Seite angezeigt, auf der Sie einen **Tabellennamen**eingeben müssen. Dies ist der Name, den Sie in späteren Kapiteln verwenden, um auf die Daten in Ihrer Anwendung zu verweisen. Fügen Sie einen entsprechenden Namen ein, und klicken Sie auf **OK**

    ![neue Tabelle erstellen](images/AzureLabs-Lab8-20.png)    

12. Nachdem die neue Tabelle erstellt wurde, können Sie Sie auf der Seite **Tabellen Dienst** (unten) sehen.

    ![neue Tabelle erstellt](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a>Kapitel 5: Abschließen der Azure-Tabelle in Visual Studio

Nachdem Sie das Speicher **Dienst** -Speicherkonto eingerichtet haben, ist es an der Zeit, Daten hinzuzufügen, die zum Speichern und Abrufen von Informationen verwendet werden. Die Bearbeitung der Tabellen kann über **Visual Studio**erfolgen.

1.  Öffnen Sie **Visual Studio**.

2.  Klicken Sie im Menü auf**Cloud-Explorer** **anzeigen** > .

    ![Cloud-Explorer öffnen](images/AzureLabs-Lab8-22.png)

3.  Der **Cloud-Explorer** wird als angedocktes Element geöffnet (als "Patient", da der Ladevorgang Zeit in Anspruch nehmen kann).

    > [!NOTE] 
    > Wenn das Abonnement, das Sie zum Erstellen Ihrer *Speicher Konten* verwendet haben, nicht sichtbar ist, stellen Sie Folgendes sicher: 
    > - Sie sind beim gleichen Konto angemeldet, das Sie für das Azure-Portal verwendet haben.
    > - Wählen Sie auf der Seite "Kontoverwaltung" Ihr Abonnement aus (möglicherweise müssen Sie einen Filter aus Ihren Kontoeinstellungen anwenden):  
    >
    >   ![Abonnement suchen](images/AzureLabs-Lab8-22-5.png)

4.  Ihre Azure-Clouddienste werden angezeigt. Suchen Sie nach **Speicher Konten** , und klicken Sie auf den Pfeil auf der linken Seite, um Ihre Konten zu erweitern.

    ![Öffnen von Speicher Konten](images/AzureLabs-Lab8-23.png)

5.  Nach der Erweiterung sollte Ihr neu erstelltes **Speicherkonto** verfügbar sein. Klicken Sie auf den Pfeil links neben dem Speicher, und wählen Sie dann nach dem Erweitern der Tabelle **Tabellen** aus, und klicken Sie auf den Pfeil daneben, um die **Tabelle** anzuzeigen, die Sie im letzten Kapitel erstellt haben. Doppelklicken Sie auf die **Tabelle**.

    ![Tabelle "Scene Objects" öffnen](images/AzureLabs-Lab8-24.png)

6.  Ihre Tabelle wird in der Mitte Ihres Visual Studio-Fensters geöffnet. Klicken Sie auf das Symboltabelle **+** mit dem (plus)-Symbol.

    ![neue Tabelle hinzufügen](images/AzureLabs-Lab8-25.png)

7.  Ein Fenster wird angezeigt, in dem Sie aufgefordert werden, *Entitäten hinzuzufügen*. Sie erstellen insgesamt drei Entitäten mit jeweils mehreren Eigenschaften. Sie werden feststellen, dass *PartitionKey* und *RowKey* bereits bereitgestellt werden, da diese von der Tabelle zum Suchen Ihrer Daten verwendet werden. 

    ![Partitions-und Zeilen Schlüssel](images/AzureLabs-Lab8-26.png)

8. Aktualisieren Sie den *Wert* von **PartitionKey** und **RowKey** wie folgt (denken Sie daran, diesen Schritt für jede hinzu zufügende Zeilen Eigenschaft auszuführen, obwohl Sie den RowKey jedes Mal erhöhen):

    ![korrekte Werte hinzufügen](images/AzureLabs-Lab8-26-5.png)

9.  Klicken Sie auf **Eigenschaft hinzufügen** , um zusätzliche Daten Zeilen hinzuzufügen. Erstellen Sie die erste leere Tabelle mit der folgenden Tabelle.

10. Klicken Sie anschließend auf **OK**.

    ![Klicken Sie abschließend auf OK.](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > Stellen Sie sicher, dass Sie den **Typ** der **X**-, **Y**-und **Z**-Einträge in " **Double**" geändert haben. 

11. Sie werden feststellen, dass die Tabelle nun eine Daten Zeile enthält. Klicken Sie **+** erneut auf das Symbol (plus), um eine weitere Entität hinzuzufügen.

    ![erste Zeile](images/AzureLabs-Lab8-27-5.png)

12. Erstellen Sie eine zusätzliche Eigenschaft, und legen Sie dann die Werte der neuen Entität entsprechend den unten gezeigten fest.

    ![Cube hinzufügen](images/AzureLabs-Lab8-28.png)

13. Wiederholen Sie den letzten Schritt zum Hinzufügen einer weiteren Entität. Legen Sie die Werte für diese Entität auf die unten angezeigten Werte fest.

    ![Zylinder hinzufügen](images/AzureLabs-Lab8-29.png)

14. Die Tabelle sollte nun wie folgt aussehen.

    ![Tabelle ist fertiggestellt](images/AzureLabs-Lab8-30.png)

15. Sie haben dieses Kapitel abgeschlossen. Stellen Sie sicher, dass Sie speichern.

## <a name="chapter-6---create-an-azure-function-app"></a>Kapitel 6: Erstellen eines Azure-Funktionen-App

Erstellen Sie eine Azure-Funktionen-APP, die von der Desktop Anwendung aufgerufen wird, um den **Tabellen** Dienst zu aktualisieren und eine Benachrichtigung über den **Notification Hub**zu senden.

Zunächst müssen Sie eine Datei erstellen, die es ihrer Azure-Funktion ermöglicht, die benötigten Bibliotheken zu laden.

1.  Öffnen Sie **Notepad** (drücken Sie Windows-Taste, und geben Sie Notepad ein).

    ![Editor öffnen](images/AzureLabs-Lab8-31.png)

2.  Fügen Sie bei geöffneter Notepad die JSON-Struktur unten ein. Wenn Sie dies abgeschlossen haben, speichern Sie es auf Ihrem Desktop als " **Project. JSON**". Es ist wichtig, dass die Benennung korrekt ist: Stellen Sie sicher, dass Sie nicht über die Dateierweiterung " **. txt** " verfügt. Diese Datei definiert die Bibliotheken, die von ihrer Funktion verwendet werden, wenn Sie nuget verwendet haben, wird Sie vertraut aussehen.

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

3.  Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

4.  Wenn Sie angemeldet sind, klicken Sie in der oberen linken Ecke auf " **neu** ", und suchen Sie nach **Funktionen-App**. Drücken Sie dann die **Eingabe**Taste.

    ![nach Funktionen-App suchen](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > Das Wort **New** wurde möglicherweise durch **Create a Resource**in neueren Portalen ersetzt.

5.  Auf der neuen Seite wird eine Beschreibung des **Funktionen-App** Dienstanbieter bereitgestellt. Wählen Sie unten links in dieser Eingabeaufforderung die Schaltfläche **Erstellen** aus, um eine Verknüpfung mit diesem Dienst zu erstellen.

    ![Funktionen-app-Instanz](images/AzureLabs-Lab8-33.png)

6.  Nachdem Sie auf **Erstellen**geklickt haben, geben Sie Folgendes ein:

    1. Fügen Sie für **App-Name**den gewünschten Namen für diese Dienst Instanz ein.

    2. Wählen Sie ein **Abonnement**aus.

    3. Wählen Sie den für Sie geeigneten Tarif aus. Wenn Sie zum ersten Mal einen **Funktionen-App Dienst**erstellen, sollte Ihnen ein Free-Tarif zur Verfügung stehen.

    4. Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** . Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Labs) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie unter diesem [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Klicken Sie für **Betriebssystem**auf Windows, da dies die beabsichtigte Plattform ist.

    6. Wählen Sie einen **Hostingplan** aus (in diesem Tutorial wird ein **Verbrauchs Plan**verwendet.)

    7. Wählen Sie einen **Standort** **aus (Wählen Sie den gleichen Speicherort wie für den Speicher aus, den Sie im vorherigen Schritt erstellt haben)** .

    8. Im Abschnitt **Speicher** **müssen Sie den Speicherdienst auswählen, den Sie im vorherigen Schritt erstellt**haben.

    9. Sie benötigen keine *Application Insights* in dieser APP, sodass Sie Sie nicht mehr **Deaktivieren**können.

    10. Klicken Sie auf **Erstellen**.

        ![neue Instanz erstellen](images/AzureLabs-Lab8-34.png)

7.  Nachdem Sie auf " **Erstellen** " geklickt haben, müssen Sie warten, bis der Dienst erstellt wird. dieser Vorgang kann einige Minuten in Anspruch nehmen.

8.  Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![neue Benachrichtigung](images/AzureLabs-Lab8-35.png)

9.  Klicken Sie auf die Benachrichtigungen, um die neue Dienst Instanz zu untersuchen.

10. Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen. 

    ![Gehe zu Ressource](images/AzureLabs-Lab8-36.png)

11. Klicken Sie **+** neben *Functions*auf das Symbol (Pluszeichen), um *neu zu erstellen*.

    ![neue Funktion hinzufügen](images/AzureLabs-Lab8-37.png)

12. Im mittleren Bereich wird das Fenster für die **Funktions** Erstellung angezeigt. Ignorieren Sie die Informationen in der oberen Hälfte des Panels, und klicken Sie auf **benutzerdefinierte Funktion**, die sich am unteren Rand befindet (im blauen Bereich, wie unten gezeigt).

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab8-38.png)

13. Die neue Seite innerhalb des Fensters zeigt verschiedene Funktionstypen. Scrollen Sie nach unten, um die lila Typen anzuzeigen, und klicken Sie auf **http Put** -Element.

    ![Link "http Put"](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > Möglicherweise müssen Sie nach unten auf der Seite einen Bildlauf durchführen (dieses Bild sieht möglicherweise nicht genau aus, wenn Aktualisierungen des Azure-Portals stattfinden), suchen Sie jedoch nach einem Element mit dem Namen " *http Put*".

14. Das Fenster **http Put** wird angezeigt, in dem Sie die Funktion konfigurieren müssen (siehe unten für Image).

    1.  Wählen Sie unter **Sprache** im Dropdown Menü die Option C\#aus.

    2.  Geben Sie **unter Name** einen entsprechenden Namen ein.

    3.  Wählen Sie im Dropdown Menü **Authentifizierungs Ebene** die Option **Funktion**aus.

    4.  Für den **Tabellennamen** Abschnitt müssen Sie den genauen Namen verwenden, den Sie zuvor verwendet haben, um den **Tabellen** Dienst zu erstellen (einschließlich desselben Buchstabens).

    5.  Verwenden Sie im Abschnitt **Speicherkonto Verbindung** das Dropdown Menü, und wählen Sie dann Ihr Speicherkonto aus. Wenn dies nicht der Fall ist, klicken Sie neben dem Abschnitts Titel auf den **neuen** Link, um ein anderes Panel anzuzeigen, in dem das Speicherkonto aufgelistet werden soll.

        ![neuer Speicher](images/AzureLabs-Lab8-40.png)

15. Wenn Sie auf **Erstellen** klicken, erhalten Sie eine Benachrichtigung, dass die Einstellungen erfolgreich aktualisiert wurden.

    ![Create-Funktion](images/AzureLabs-Lab8-41.png)

16. Nachdem Sie auf **Erstellen**geklickt haben, werden Sie zum Funktions-Editor umgeleitet.

    ![Funktionscode aktualisieren](images/AzureLabs-Lab8-42.png)

17. Fügen Sie den folgenden Code in den Funktions-Editor ein (ersetzen Sie den Code in der Funktion):

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
    > Mithilfe der enthaltenen Bibliotheken empfängt die-Funktion den Namen und den Speicherort des Objekts, das in der Unity-Szene verschoben wurde C# (als ein-Objekt namens **unitygameobject**). Dieses Objekt wird dann verwendet, um die Objekt Parameter in der erstellten Tabelle zu aktualisieren. Danach ruft die Funktion den erstellten Notification Hub-Dienst auf, der alle abonnierten Anwendungen benachrichtigt.

18. Klicken Sie mit dem Code auf **Speichern**.

19. Klicken Sie anschließend auf **\<** der rechten Seite der Seite auf das Symbol (Pfeil).

    ![Uploadpanel öffnen](images/AzureLabs-Lab8-43.png)

20. Ein Panel wird von rechts nach rechts angezeigt. Klicken Sie in diesem Bereich auf **hochladen**, und ein Datei Browser wird angezeigt.

21. Navigieren Sie zu, und klicken Sie auf die Datei **Project. JSON** , die Sie **zuvor im** Editor erstellt haben, und klicken Sie dann auf die Schaltfläche **Öffnen** . Diese Datei definiert die Bibliotheken, die von ihrer Funktion verwendet werden.

    ![JSON hochladen](images/AzureLabs-Lab8-44.png)

22. Wenn die Datei hochgeladen wurde, wird Sie im Panel auf der rechten Seite angezeigt. Wenn Sie darauf klicken, wird es im **Funktions** -Editor geöffnet. Es muss **genau** wie das nächste Bild aussehen (unterschritt 23).

23. Klicken Sie dann im Bereich links unterhalb von **Functions**auf den Link **integrieren** .

    ![Integration-Funktion](images/AzureLabs-Lab8-45.png)

24. Klicken Sie auf der nächsten Seite in der oberen rechten Ecke auf erweiterter **Editor** (siehe unten).

    ![erweiterten Editor öffnen](images/AzureLabs-Lab8-46.png)

25. Eine **Function. JSON** -Datei wird im mittleren Bereich geöffnet, der durch den folgenden Code Ausschnitt ersetzt werden muss. Definiert die Funktion, die Sie entwickeln, und die Parameter, die an die Funktion übermittelt werden.

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

26. Der Editor sollte nun wie in der folgenden Abbildung aussehen:

    ![zurück zum Standard-Editor](images/AzureLabs-Lab8-47.png)

27. Sie bemerken möglicherweise, dass die Eingabeparameter, die Sie gerade eingefügt haben, nicht mit den Tabellen-und Speicher Details identisch sind und daher mit ihren Informationen aktualisiert werden müssen. Gehen Sie **hier nicht**wie folgt vor. Klicken Sie einfach auf den Link **Standard-Editor** in der oberen rechten Ecke der Seite, um zurückzukehren.

28. Klicken Sie im **Standard-Editor**unter **Eingaben**auf **Azure Table Storage (Tabelle)** . 
    
    ![Tabellen Eingaben](images/AzureLabs-Lab8-47-5.png)

29. Stellen Sie sicher, dass die folgenden Informationen mit **ihren** Informationen identisch sind, da Sie unterschiedlich sein können (es gibt eine Abbildung unterhalb der folgenden Schritte):

    1.  **Tabellenname**: der Name der Tabelle, die Sie im Azure Storage Tabellen Dienst erstellt haben.

    2.  **Speicherkonto Verbindung:** klicken Sie auf **neu**, das neben dem Dropdown Menü angezeigt wird, und rechts neben dem Fenster wird ein Panel angezeigt.

        ![neuer Speicher](images/AzureLabs-Lab8-48.png)

        1.  Wählen Sie Ihr **Speicherkonto**aus, das Sie zuvor erstellt haben, um die **Funktionen-apps** zu hosten.

        2. Sie werden feststellen, dass der Wert für die **Speicherkonto** Verbindung erstellt wurde.

        3. Stellen Sie sicher, dass Sie nach Abschluss des Vorgangs auf **Speichern** klicken.

    3.  Die Seite **Eingaben** sollte nun mit den unten aufgeführten Informationen identisch **sein** .

        ![Eingaben sind beendet](images/AzureLabs-Lab8-49.png)

30. Klicken Sie anschließend unter **Ausgaben**auf **Azure Notification Hub (Benachrichtigung)** . Stellen Sie sicher, dass die folgenden Informationen mit **ihren** Informationen übereinstimmen, da Sie unterschiedlich sein können (es gibt eine Abbildung unterhalb der folgenden Schritte):

    1.  **Notification Hub-Name**: Dies ist der Name der **Notification Hub** -Dienst Instanz, die Sie zuvor erstellt haben.

    2.  **Notification Hubs-Namespace Verbindung**: Klicken Sie auf **neu**, das neben dem Dropdown Menü angezeigt wird.

        ![Ausgaben überprüfen](images/AzureLabs-Lab8-50.png)

    3. Das **Popup-** Popup Fenster wird angezeigt (siehe Abbildung unten), in dem Sie den **Namespace** des **Benachrichtigungs-Hubs**auswählen müssen, den Sie zuvor eingerichtet haben.

    4. Wählen Sie den Namen Ihres **Notification Hubs** im Dropdown Menü in der Mitte aus.

    5.  Legen Sie das Dropdown Menü **Richtlinie** auf **defaultfullsharedaccesssignature**fest.

    6. Klicken Sie auf die Schaltfläche **auswählen** , um zurückzukehren.

        ![Ausgabe Update](images/AzureLabs-Lab8-51.png)

31.  Die Seite **Ausgaben** sollte nun mit den unten angegebenen Informationen, jedoch mit ihren Informationen, identisch **sein** . Stellen Sie sicher, dass Sie auf **Speichern**klicken.

> [!WARNING]
> *Ändern Sie den Notification Hub-Namen nicht direkt* . (Dies sollte alle mithilfe der **Erweiterter Editor**erfolgen, vorausgesetzt, Sie haben die vorherigen Schritte ordnungsgemäß befolgt.

![Abgeschlossene Ausgaben](images/AzureLabs-Lab8-50.png)

32. An diesem Punkt sollten Sie die Funktion testen, um sicherzustellen, dass Sie funktioniert. Gehen Sie dazu wie folgt vor: 

    1. Navigieren Sie noch einmal zur funktionsseite:

        ![Abgeschlossene Ausgaben](images/AzureLabs-Lab8-50-1.png)

    2. Klicken Sie auf der Seite Funktion auf die Registerkarte **Test** ganz rechts auf der Seite, um das Blatt " *Test* " zu öffnen:

        ![Abgeschlossene Ausgaben](images/AzureLabs-Lab8-50-2.png)

    3. Fügen Sie im Textfeld **Anforderungs** Text des Blatts den folgenden Code ein:

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

    4. Wenn der Testcode vorhanden ist, klicken Sie unten rechts auf die Schaltfläche **Ausführen** , und der Test wird ausgeführt. Die Ausgabe Protokolle des Tests werden im Konsolen Bereich unterhalb Ihres Funktions Codes angezeigt.

        ![Abgeschlossene Ausgaben](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > Wenn der obige Test fehlschlägt, müssen Sie überprüfen, ob Sie die obigen Schritte genau befolgt haben. Dies gilt insbesondere für die Einstellungen im Bereich **integrieren**. 

## <a name="chapter-7---set-up-desktop-unity-project"></a>Kapitel 7: Einrichten eines Desktop-Unity-Projekts

> [!IMPORTANT]
> Die Desktop Anwendung, die Sie jetzt erstellen, funktioniert **nicht** im Unity-Editor. Er muss außerhalb des Editors ausgeführt werden, und zwar nach dem Anwendungs Aufbau, mithilfe von Visual Studio (oder der bereitgestellten Anwendung). 

Im folgenden finden Sie eine typische Einrichtung für die Entwicklung mit Unity und gemischter Realität und ist daher eine gute Vorlage für andere Projekte.

Richten Sie Ihr immersives Headset mit gemischter Realität ein und testen Sie es.

> [!NOTE] 
> Für diesen Kurs benötigen Sie **keine** Bewegungs Controller. Wenn Sie Unterstützung beim Einrichten des immersiven Headsets benötigen, befolgen Sie diesen [Link zum Einrichten von Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Öffnen Sie **Unity** , und klicken Sie auf **neu**.

    ![neues Unity-Projekt](images/AzureLabs-Lab8-52.png)

2.  Sie müssen einen Unity-Projektnamen angeben und **unitydesktopnotifhub**einfügen. Stellen Sie sicher, dass Projekttyp auf **3D**festgelegt ist. Legen Sie den Speicherort auf einen geeigneten **Speicherort** fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind). Klicken Sie dann auf **Projekt erstellen**.

    ![Projekt erstellen](images/AzureLabs-Lab8-53.png)

3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist. Wechseln Sie zu**Einstellungen** **Bearbeiten** > , und navigieren Sie dann im neuen Fenster zu **externe Tools**. Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**. Schließen Sie das Fenster " **Einstellungen** ".

    ![Festlegen externer vs-Tools](images/AzureLabs-Lab8-54.png)

4.  Navigieren Sie als nächstes zu **Datei** > Buildeinstellungen, wählen Sie **universelle Windows-Plattform**aus, und klicken Sie dann auf die Schaltfläche **Plattform wechseln** , um die Auswahl zu übernehmen

    ![Plattformen wechseln](images/AzureLabs-Lab8-55.png)

5.  Stellen Sie sicher, dass in den Einstellungen für die **Datei** > **Erstellung**Folgendes angezeigt wird:

    1.  Das **Zielgerät** ist auf **ein beliebiges Gerät** festgelegt.

        > Diese Anwendung wird für Ihren Desktop verwendet, daher muss es sich um **ein beliebiges Gerät** handeln.

    2.  Der Buildtyp ist auf **D3D** festgelegt.

    3.  **SDK** ist auf **neueste installierte** Version festgelegt.

    4.  **Visual Studio-Version** ist auf **neueste installierte** Version festgelegt.

    5.  **Build und Run** sind auf **lokaler Computer** festgelegt.

    6.  In diesem Fall lohnt es sich, die Szene zu speichern und dem Build hinzuzufügen.

        1. Wählen Sie hierzu die Option **geöffnete Szenen hinzufügen**aus. Ein Fenster zum Speichern wird angezeigt.

            ![Hinzufügen offener Szenen](images/AzureLabs-Lab8-56.png)

        2. Erstellen Sie einen neuen Ordner für dieses und jede zukünftige Szene, und wählen Sie dann die Schaltfläche **neuer Ordner** aus, um einen neuen Ordner zu **erstellen.**

            ![neuer Szenen Ordner](images/AzureLabs-Lab8-57.png)

        3. Öffnen Sie den neu erstellten Ordner **Szenen** , geben Sie im Feld **Dateiname:** Text den **Text\_NH\_Desktop Scene**ein, und klicken Sie dann auf **Speichern**.

            ![neues NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  Die restlichen Einstellungen in denBuildeinstellungen sollten vorerst als Standard belassen werden.

6.  Klicken Sie im gleichen Fenster auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der **Inspektor** befindet.

7.  In diesem Bereich müssen einige Einstellungen überprüft werden:

    1.  Auf der Registerkarte **andere Einstellungen** :

        1.  Die **Skript Lauf Zeit Version** sollte **experimentell sein (.NET 4,6-Entsprechung)** .

        2. **Skript** -Back-End sollte **.net** sein

        3. **API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten

            ![4,6 NET-Version](images/AzureLabs-Lab8-59.png)

    2.  Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:

        - **Internet Client deklarieren**

            ![Internet Client Tick](images/AzureLabs-Lab8-60.png)

8.  Zurück in Buildeinstellungen: *Unity-C\# -Projekte* sind nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen neben this.

9.  Schließen Sie das Fenster mit den Buildeinstellungen.

10. Speichern Sie Ihre Szene-und Projekt **Datei** >  > , und speichern Sie das**Projekt**in der Szene.

    > [!IMPORTANT]
    > Wenn Sie die *Unity-Setup* Komponente für dieses Projekt (Desktop-App) überspringen und direkt mit dem Code fortfahren möchten, können Sie [dieses. unitypackage herunterladen](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), es als [**benutzerdefiniertes Paket**](https://docs.unity3d.com/Manual/AssetPackages.html)in Ihr Projekt importieren und dann im Kapitel fortfahren. [ 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).  Sie müssen weiterhin die Skript Komponenten hinzufügen.

## <a name="chapter-8---importing-the-dlls-in-unity"></a>Kapitel 8: Importieren der DLLs in Unity

Sie verwenden Azure Storage für Unity (das wiederum das .NET SDK für Azure nutzt). Weitere Informationen finden Sie unter diesem [Link zu Azure Storage für Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).

Zurzeit gibt es ein bekanntes Problem in Unity, das erfordert, dass Plug-ins nach dem Importieren neu konfiguriert werden. Diese Schritte (4-7 in diesem Abschnitt) werden nicht mehr benötigt, nachdem der Fehler behoben wurde.

Um das SDK in Ihr eigenes Projekt zu importieren, stellen Sie sicher, dass Sie das neueste [ **. unitypackage**](https://aka.ms/azstorage-unitysdk) von GitHub heruntergeladen haben. Gehen Sie dann wie folgt vor:

1.  Fügen Sie das **. unitypackage** zu Unity hinzu, indem Sie die Menüoption **Assets \> Import \> Package Custom Package** verwenden.

2.  Im Feld " **Unity-Paket importieren** ", das angezeigt wird, können Sie unter * **Plugin* \> * Storage * * * die Option Alles auswählen.  Deaktivieren Sie alles andere, da es für diesen Kurs nicht benötigt wird.

    ![in Paket importieren](images/AzureLabs-Lab8-61.png)

3.  Klicken Sie auf die Schaltfläche ***importieren*** , um dem Projekt die Elemente hinzuzufügen.

4.  Wechseln Sie in der Projektansicht **unter Plug** -in zum Ordner **Speicher** , und wählen Sie *nur*die folgenden Plug-ins aus:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft. WindowsAzure. Storage
    -   Newtonsoft.Json
    -   System.Spatial

![alle Plattformen deaktivieren](images/AzureLabs-Lab8-62.png)

5.  Wenn *Sie diese speziellen* Plug-Ins **ausgewählt haben,** deaktivieren Sie **eine beliebige Plattform** , deaktivieren Sie **wsaplayer** **, und klicken** Sie auf **anwenden**.

    ![Platt Form-DLLs anwenden](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > Wir markieren diese bestimmten Plug-ins, sodass Sie nur im Unity-Editor verwendet werden. Dies liegt daran, dass im WSA-Ordner verschiedene Versionen der gleichen Plug-ins vorhanden sind, die nach dem Exportieren des Projekts aus Unity verwendet werden.

6.  Wählen Sie im Ordner **Storage** -Plug-in nur die Option:

    -   Microsoft. Data. Services. Client

        !["nicht verarbeiten" für DLLs festlegen](images/AzureLabs-Lab8-64.png)

7.  Aktivieren Sie das Kontrollkästchen **nicht verarbeiten** unter **Platt Form Einstellungen** , und klicken Sie auf ***anwenden***.

    ![keine Verarbeitung anwenden](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > Wir markieren dieses Plug-in "nicht verarbeiten", da das Unity-assemblypatcher Probleme bei der Verarbeitung dieses Plug-ins hat. Das Plug-in funktioniert weiterhin, auch wenn es nicht verarbeitet wird.

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a>Kapitel 9: Erstellen der tabledescene-Klasse im Desktop Unity-Projekt

Sie müssen nun die Skripts erstellen, die den Code enthalten, um diese Anwendung auszuführen.

Das erste Skript, das Sie erstellen müssen, ist " **tabletoiscene**", das für Folgendes zuständig ist:

-   Lesen von Entitäten in der Azure-Tabelle.
-   Bestimmen Sie anhand der Tabellendaten, welche Objekte zu erzeugen sind und an welcher Position.

Das zweite Skript, das Sie erstellen müssen, ist **cloudscene**, das für Folgendes zuständig ist:

-   Registrieren des Linksklick Ereignisses, um dem Benutzer das Ziehen von Objekten in die Szene zu ermöglichen.
-   Serialisieren der Objektdaten aus dieser Unity-Szene und Senden der Daten an den Azure-Funktionen-app.

So erstellen Sie diese Klasse:

1.  Klicken Sie im Projekt Panel mit der rechten Maustaste auf den Ordner **Asset** , und **Erstellen** > Sie den**Ordner**. Benennen Sie den Ordner mit **Skripts**.

    ![Ordner für die Skripterstellung](images/AzureLabs-Lab8-66.png)

    ![Ordner zum Erstellen von Skripts 2](images/AzureLabs-Lab8-67.png)

2.  Doppelklicken Sie auf den soeben erstellten Ordner, um ihn zu öffnen.

3.  Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf **C# Skript** **Erstellen**  >  . Benennen Sie das Skript **tabledescene**.

    ![neues c#-](images/AzureLabs-Lab8-68.png)
    Skript![Umbenennen von tableumscene](images/AzureLabs-Lab8-69.png)

4.  Doppelklicken Sie auf das Skript, um es in Visual Studio 2017 zu öffnen.

5.  Fügen Sie die folgenden Namespaces hinzu:

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  Fügen Sie in der-Klasse die folgenden Variablen ein:

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
    > Ersetzen Sie den Wert **Accountname** durch den Namen Ihres Azure Storage dienstanamens und **accountkey** durch den Schlüsselwert im Azure-Portal (siehe Abbildung unten) im Azure Storage-Dienst. 
    >
    > ![Kontoschlüssel abrufen](images/AzureLabs-Lab8-70.png)

7.  Fügen Sie jetzt die Methoden **Start ()** und **Awa()** hinzu, um die-Klasse zu initialisieren.

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

8.  Fügen Sie innerhalb der **tabledescene** -Klasse die Methode hinzu, die die Werte aus der Azure-Tabelle abruft, und verwenden Sie Sie, um die entsprechenden primitiven in der Szene zu erzeugen.

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

9.  Außerhalb der **tabletoscene** -Klasse müssen Sie die Klasse definieren, die von der Anwendung verwendet wird, um die **Tabellen Entitäten**zu serialisieren und zu deserialisieren.

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

10. Stellen Sie sicher, dass Sie **Speichern** , bevor Sie zum Unity-Editor zurückkehren.

11. Klicken Sie im **Hierarchie** Panel auf die **Hauptkamera** , damit die Eigenschaften im **Inspektor**angezeigt werden.

12. Wenn der Ordner **Scripts** geöffnet ist, wählen Sie die **tabletoscene** -Skriptdatei aus, und ziehen Sie Sie auf die **Hauptkamera**. Das Ergebnis sollte wie folgt lauten:

    ![Skript zur Hauptkamera hinzufügen](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a>Kapitel 10: Erstellen der cloudscene-Klasse im Desktop Unity-Projekt

Das zweite Skript, das Sie erstellen müssen, ist **cloudscene**, das für Folgendes zuständig ist:

-   Registrieren des Linksklick Ereignisses, um dem Benutzer das Ziehen von Objekten in die Szene zu ermöglichen.

-   Serialisieren der Objektdaten aus dieser Unity-Szene und Senden der Daten an den Azure-Funktionen-app.

So erstellen Sie das zweite Skript:

1.  Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf **Erstellen**, **C\# -Skript** Benennen des Skripts für **cloudscene**
    
    ![neues c#-](images/AzureLabs-Lab8-72.png)
    Skript![Umbenennen von cloudscene](images/AzureLabs-Lab8-73.png)

2.  Fügen Sie die folgenden Namespaces hinzu:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  Fügen Sie die folgenden Variablen ein:

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

4.  Ersetzen Sie den Wert **azurefunctionendpoint** durch ihre Azure-Funktionen-App-URL im Azure-Funktionen-APP, wie in der folgenden Abbildung gezeigt:

    ![Funktions-URL für Get](images/AzureLabs-Lab8-74.png)

5.  Fügen Sie jetzt die Methoden **Start ()** und **Awa()** hinzu, um die-Klasse zu initialisieren.

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

6.  Fügen Sie in der **Update ()** -Methode den folgenden Code hinzu, der die Maus Eingaben und den Zieh Vorgang erkennt, die wiederum gameobjects in der Szene verschieben. Wenn der Benutzer ein Objekt gezogen und abgelegt hat, übergibt es den Namen und die Koordinaten des Objekts an die Methode **updatecloudscene ()** , die den Azure Funktionen-App-Dienst aufruft, der die Azure-Tabelle aktualisiert und die Benachrichtigung auslöst.

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

7.  Fügen Sie nun wie unten gezeigt die **updatecloudscene ()** -Methode hinzu:

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

8.  Speichern des Codes und zurückkehren zu Unity

9.  Ziehen Sie das **cloudscene** -Skript auf die **Hauptkamera**. 

    1. Klicken Sie im **Hierarchie** Panel auf die **Hauptkamera** , damit die Eigenschaften im **Inspektor**angezeigt werden. 

    2. Wenn der Ordner **Scripts** geöffnet ist, wählen Sie das **cloudscene** -Skript aus, und ziehen Sie es auf die **Hauptkamera**. Das Ergebnis sollte wie folgt lauten:

        > ![Ziehen Sie das cloudskript auf die Hauptkamera](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a>Kapitel 11: Erstellen des Desktop Projekts in UWP

Alles, was für den Unity-Abschnitt dieses Projekts erforderlich ist, wurde nun abgeschlossen.

1.  Navigieren Sie zu Buildeinstellungen (dateibuildeinstellungen > ).

2.  Klicken Sie im Fenster "Buildeinstellungen" auf " **Erstellen**".

    ![Projekt erstellen](images/AzureLabs-Lab8-76.png)

3.  Ein **Datei-Explorer** -Fenster wird angezeigt, in dem Sie aufgefordert werden, einen Speicherort zu erstellen. Erstellen Sie einen neuen Ordner (indem Sie in der oberen linken Ecke auf **neuer Ordner** klicken), und nennen Sie ihn " **BUILDS**".

    ![neuer Ordner für Build](images/AzureLabs-Lab8-77.png)

    1.  Öffnen Sie den Ordner neue **BUILDS** , und erstellen Sie einen weiteren Ordner (mehr als einen **neuen Ordner** ), und nennen Sie ihn " **\_NH Desktop\_App**".

        ![Ordnername NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  Wenn die **NH\_-\_Desktop-App** ausgewählt ist. Klicken Sie auf **Ordner auswählen**. Es dauert eine Minute, bis das Projekt erstellt wird.

4.  Im folgenden Build wird der **Datei-Explorer** angezeigt, in dem der Speicherort des neuen Projekts angezeigt wird. Es muss jedoch nicht geöffnet werden, da Sie das andere Unity-Projekt zunächst in den nächsten Kapiteln erstellen müssen.


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a>Kapitel 12: Einrichten des gemischten Reality-Unity-Projekts

Im folgenden finden Sie eine typische Einrichtung für die Entwicklung mit gemischter Realität und eine gute Vorlage für andere Projekte.

1.  Öffnen Sie **Unity** , und klicken Sie auf **neu**.

    ![neues Unity-Projekt](images/AzureLabs-Lab8-79.png)

2.  Sie müssen nun einen Unity-Projektnamen angeben und **unitymrnotifhub**einfügen. Stellen Sie sicher, dass Projekttyp auf **3D**festgelegt ist. Legen Sie den Speicherort auf einen geeigneten **Speicherort** fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind). Klicken Sie dann auf **Projekt erstellen**.

    ![Name unitymrnotishub](images/AzureLabs-Lab8-80.png)

3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist. Wechseln Sie zu**Einstellungen** **Bearbeiten** > , und navigieren Sie dann im neuen Fenster zu **externe Tools**. Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**. Schließen Sie das Fenster " **Einstellungen** ".

    ![externen Editor auf vs festlegen](images/AzureLabs-Lab8-81.png)

4.  Navigieren Sie als nächstes zu > dateibuildeinstellungen, und schalten Sie die Plattform auf **universelle Windows-Plattform**, indem Sie auf die Schaltfläche **Plattform wechseln** klicken.

    ![Plattformen zu UWP wechseln](images/AzureLabs-Lab8-82.png)

5.  Wechseln Sie zu > dateibuildeinstellungen, und stellen Sie Folgendes sicher:

    1.  Das **Zielgerät** ist auf **ein beliebiges Gerät** festgelegt.

        > Legen Sie für Microsoft hololens das **Zielgerät** auf *hololens*fest.

    2.  Der Buildtyp ist auf **D3D** festgelegt.

    3.  **SDK** ist auf **neueste installierte** Version festgelegt.

    4.  **Visual Studio-Version** ist auf **neueste installierte** Version festgelegt.

    5.  **Build und Run** sind auf **lokaler Computer** festgelegt.

    6.  In diesem Fall lohnt es sich, die Szene zu speichern und dem Build hinzuzufügen.

        1. Wählen Sie hierzu die Option **geöffnete Szenen hinzufügen**aus. Ein Fenster zum Speichern wird angezeigt.

            ![Hinzufügen offener Szenen](images/AzureLabs-Lab8-83.png)

        2. Erstellen Sie einen neuen Ordner für dieses und jede zukünftige Szene, und wählen Sie dann die Schaltfläche **neuer Ordner** aus, um einen neuen Ordner zu **erstellen.**

            ![neuer Szenen Ordner](images/AzureLabs-Lab8-84.png)

        3. Öffnen Sie den neu erstellten Ordner **Szenen** , geben Sie im Feld **Dateiname:** Text den **Text\_NH\_Mr Scene**ein, und klicken Sie dann auf **Speichern**.

            ![neue Szene NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  Die restlichen Einstellungen in denBuildeinstellungen sollten vorerst als Standard belassen werden.

6.  Klicken Sie im gleichen Fenster auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der **Inspektor** befindet.    

    ![Spieler Einstellungen öffnen](images/AzureLabs-Lab8-86.png)

7.  In diesem Bereich müssen einige Einstellungen überprüft werden:

    1.  Auf der Registerkarte **andere Einstellungen** :

        1.  Die **Skript Lauf Zeit Version** sollte **experimentell** sein (.NET 4,6-Entsprechung).
        2.  **Skript** -Back-End sollte ***.net*** sein
        3.  **API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten

            ![API-Kompatibilität](images/AzureLabs-Lab8-87.png)

    2.  Weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), **unterstützt Tick Virtual Reality**, wird sichergestellt, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.

        ![Aktualisieren der XR-Einstellungen](images/AzureLabs-Lab8-88.png)        

    3.  Wählen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**die folgenden Optionen aus:

        - **Internet Client deklarieren**           

            ![Internet Client Tick](images/AzureLabs-Lab8-89.png)

8.  Zurück inden Buildeinstellungen: **Unity C# -Projekte** sind nicht mehr abgeblendet: Aktivieren Sie das Kontrollkästchen neben this.

9.  Nachdem Sie diese Änderungen vorgenommen haben, schließen Sie das Fenster Buildeinstellungen.

10. Speichern Sie Ihre Szene-und Projekt **Datei** >  > , und speichern Sie das**Projekt**in der Szene.

    > [!IMPORTANT]
    > Wenn Sie die *Unity-Setup* Komponente für dieses Projekt (Mixed Reality-APP) überspringen und direkt mit dem Code fortfahren möchten, können Sie [dieses. unitypackage herunterladen](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), es als [**benutzerdefiniertes Paket**](https://docs.unity3d.com/Manual/AssetPackages.html)in das Projekt importieren und dann fortfahren [. Kapitel 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project). Sie müssen weiterhin die Skript Komponenten hinzufügen.

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a>Kapitel 13: Importieren der DLLs im Mixed Reality Unity-Projekt

Sie verwenden Azure Storage für die Unity-Bibliothek (in der das .NET SDK für Azure verwendet wird). Folgen Sie diesem [Link zur Verwendung von Azure Storage mit Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).
Zurzeit gibt es ein bekanntes Problem in Unity, das erfordert, dass Plug-ins nach dem Importieren neu konfiguriert werden. Diese Schritte (4-7 in diesem Abschnitt) werden nicht mehr benötigt, nachdem der Fehler behoben wurde.

Um das SDK in Ihr eigenes Projekt zu importieren, stellen Sie sicher, dass Sie das neueste [. unitypackage](https://aka.ms/azstorage-unitysdk)heruntergeladen haben. Gehen Sie dann wie folgt vor:

1.  Fügen Sie das von oben heruntergeladene. unitypackage mithilfe der Menüoption **Assets** > **Import Package** > **Custom Package** in Unity hinzu.

2.  Im Feld " **Unity-Paket importieren** ", das angezeigt wird, können Sie unter **Plug** > -in-**Speicher**alles auswählen.

    ![Paket importieren](images/AzureLabs-Lab8-90.png)

3.  Klicken Sie auf die Schaltfläche **importieren** , um dem Projekt die Elemente hinzuzufügen.

4.  Wechseln Sie in der Projektansicht **unter Plug** -in zum Ordner **Speicher** , und wählen Sie *nur*die folgenden Plug-ins aus:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft. WindowsAzure. Storage
    -   Newtonsoft.Json
    -   System.Spatial

    ![Plug-ins auswählen](images/AzureLabs-Lab8-91.png)

5.  Wenn *Sie diese speziellen* Plug-Ins **ausgewählt haben,** deaktivieren Sie **eine beliebige Plattform** , deaktivieren Sie **wsaplayer** **, und klicken** Sie auf **anwenden**.

    ![Platt Formänderungen anwenden](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > Sie markieren diese bestimmten Plug-ins, sodass Sie nur im Unity-Editor verwendet werden. Dies liegt daran, dass im WSA-Ordner verschiedene Versionen der gleichen Plug-ins vorhanden sind, die nach dem Exportieren des Projekts aus Unity verwendet werden.

6.  Wählen Sie im Ordner **Storage** -Plug-in nur die Option:

    -   Microsoft. Data. Services. Client

        ![Datendienst Client auswählen](images/AzureLabs-Lab8-93.png)

7.  Aktivieren Sie das Kontrollkästchen **nicht verarbeiten** unter **Platt Form Einstellungen** , und klicken Sie auf **anwenden**.

    ![nicht verarbeiten](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > Sie Markieren dieses Plug-in "nicht verarbeiten", weil das Unity-assemblypatcher Probleme beim Verarbeiten dieses Plug-ins hat. Das Plug-in funktioniert weiterhin, auch wenn es nicht verarbeitet wird.

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a>Kapitel 14: Erstellen der tabledescene-Klasse im Mixed Reality Unity-Projekt

Die **tabledescene** -Klasse ist mit der in [Kapitel 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)erläuterten identisch. Erstellen Sie dieselbe Klasse im Mixed Reality-Unity-Projekt, und befolgen Sie dabei dasselbe Verfahren, das in [Kapitel 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)erläutert wurde.

Nachdem Sie dieses Kapitel abgeschlossen haben, wird diese Klasse in beiden **Unity-Projekten** auf der Hauptkamera eingerichtet.

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a>Kapitel 15: Erstellen der notificationreceiver-Klasse im Mixed Reality Unity-Projekt

Das zweite Skript, das Sie erstellen müssen, ist " **notificationreceiver**", das für Folgendes zuständig ist:

-   Registrieren der APP beim Notification Hub bei der Initialisierung.
-   Lauschen auf Benachrichtigungen, die vom Notification Hub stammen.
-   Die Objektdaten werden aus empfangenen Benachrichtigungen deserialisiert.
-   Verschieben Sie die gameobjects in der Szene basierend auf den deserialisierten Daten.

So erstellen Sie das **notificationreceiver** -Skript:

1.  Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf **Erstellen**, **C\# -Skript** Benennen Sie das Skript mit **notificationreceiver**.

    ![neuen c#-Skript](images/AzureLabs-Lab8-95.png)
    ![Namen mit notificationreceiver erstellen](images/AzureLabs-Lab8-96.png)

2.  Doppelklicken Sie auf das Skript, um es zu öffnen.

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

4.  Fügen Sie die folgenden Variablen ein:

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

5.  Ersetzen Sie den Wert **hubname** durch ihren Notification Hub-Dienstnamen und den Wert von **hublistenendpoint** mit dem Endpunkt Wert auf der Registerkarte Zugriffsrichtlinien, dem Azure Notification Hub-Dienst, im Azure-Portal (siehe Abbildung unten).

    ![Endpunkt der Notification Hubs-Richtlinie einfügen](images/AzureLabs-Lab8-97.png)

6.  Fügen Sie jetzt die Methoden **Start ()** und **Awa()** hinzu, um die-Klasse zu initialisieren.

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

7.  Fügen Sie die **waitfornotification** -Methode hinzu, damit die APP Benachrichtigungen von der Notification Hub-Bibliothek empfangen kann, ohne den Haupt Thread zu klonen:

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

8.  Mit der folgenden Methode, **initnotificationasync ()** , wird die Anwendung bei der Initialisierung beim Notification Hub-Dienst registriert. Der Code wird auskommentiert, da Unity das Projekt nicht erstellen kann. Wenn Sie das nuget-Paket Azure Messaging in Visual Studio importieren, werden die Kommentare entfernt.

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

9.  Der folgende Handler, **Channel\_pushnotificationsend ()** , wird jedes Mal ausgelöst, wenn eine Benachrichtigung empfangen wird. Die Benachrichtigung wird deserialisiert. dabei handelt es sich um die Azure-Tabellen Entität, die in die Desktop Anwendung verschoben wurde. Anschließend wird das zugehörige gameobject in der Mr-Szene an dieselbe Position verschoben. 
    
    > [!IMPORTANT]
    > Der Code wird auskommentiert, weil der Code auf die Azure Messaging-Bibliothek verweist, die Sie nach der Erstellung des Unity-Projekts mit dem nuget-Paket-Manager in Visual Studio hinzufügen werden. Daher kann das Unity-Projekt nicht erstellt werden, es sei denn, es ist auskommentiert. Wenn Sie Ihr Projekt erstellen und dann zu Unity zurückkehren möchten, müssen Sie den Code **erneut kommentieren** .

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

10. Denken Sie daran, die Änderungen zu speichern, bevor Sie zum Unity-Editor zurückkehren.

11. Klicken Sie im **Hierarchie** Panel auf die **Hauptkamera** , damit die Eigenschaften im **Inspektor**angezeigt werden.

12. Wenn der Ordner **Scripts** geöffnet ist, wählen Sie das Skript **notificationreceiver** aus, und ziehen Sie es auf die **Hauptkamera**. Das Ergebnis sollte wie folgt lauten:

    ![Benachrichtigungs Empfänger Skript auf Kamera ziehen](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > Wenn Sie diese für Microsoft hololens entwickeln, müssen Sie die *Kamera* Komponente der **Hauptkamera**aktualisieren, um Folgendes zu tun:
    > - Flags löschen: Voll Tonfarbe
    > - Kulisse Schwarz

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a>Kapitel 16: Erstellen des Projekts für gemischte Realität in UWP

Dieses Kapitel ist mit dem Buildprozess für das vorherige Projekt identisch. Alles, was für den Unity-Abschnitt dieses Projekts erforderlich ist, ist nun abgeschlossen, sodass es an der Zeit ist, Sie aus Unity zu erstellen.

1.  Navigieren Sie zu Buildeinstellungen (dateibuildeinstellungen > ).

2.  Stellen Sie im Menü Buildeinstellungen sicher, dass **Unity C# -Projekte*** getickt sind (sodass Sie die Skripts in diesem Projekt nach dem Build bearbeiten können).

3.  Klicken Sie anschließend auf **Erstellen**.

    ![Projekt erstellen](images/AzureLabs-Lab8-99.png)

4.  Ein **Datei-Explorer** -Fenster wird angezeigt, in dem Sie aufgefordert werden, einen Speicherort zu erstellen. Erstellen Sie einen neuen Ordner (indem Sie in der oberen linken Ecke auf **neuer Ordner** klicken), und nennen Sie ihn " **BUILDS**".

    ![Ordner "Builds erstellen"](images/AzureLabs-Lab8-100.png)

    1.  Öffnen Sie den Ordner neue **BUILDS** , und erstellen Sie einen weiteren Ordner (mehr als einen **neuen Ordner** ), und nennen Sie ihn " **\_NH Mr\_App**".

        ![Ordner "NH_MR_Apps" erstellen](images/AzureLabs-Lab8-101.png)

    2.  Wenn die **App\_"\_NH Mr** " ausgewählt ist. Klicken Sie auf **Ordner auswählen**. Es dauert eine Minute, bis das Projekt erstellt wird.

5.  Nach dem Build wird ein **Datei-Explorer** -Fenster am Speicherort des neuen Projekts geöffnet.



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a>Kapitel 17: Hinzufügen von nuget-Paketen zur unitymrnotifhub-Lösung

> [!WARNING] 
> Beachten Sie Folgendes: Nachdem Sie die folgenden nuget-Pakete hinzugefügt haben (und die Auskommentierung des Codes im nächsten [Kapitel](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)aufheben), zeigt der Code, wenn er im Unity-Projekt wieder geöffnet wird, Fehler an. Wenn Sie zurückgehen und die Bearbeitung im Unity-Editor fortsetzen möchten, benötigen Sie einen Kommentar, mit dem Code erstellt wird, und entfernen Sie den Kommentar später erneut, sobald Sie sich wieder in Visual Studio befinden. 

Nachdem der gemischte Projektmappenbuild abgeschlossen wurde, navigieren Sie zu dem Projekt mit gemischter Realität, das Sie erstellt haben, und doppelklicken Sie auf die Projektmappendatei (. sln) in diesem Ordner, um die Projekt Mappe mit Visual Studio 2017 zu öffnen.
Sie müssen nun das nuget-Paket **WindowsAzure. Messaging. Managed** hinzufügen. Dabei handelt es sich um eine Bibliothek, die zum Empfangen von Benachrichtigungen vom Notification Hub verwendet wird.

So importieren Sie das nuget-Paket:

1.  Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf Ihre Projekt Mappe.

2.  Klicken Sie auf **nuget-Pakete verwalten**.

    ![nuget-Manager öffnen](images/AzureLabs-Lab8-102.png)

3.  Wählen Sie die Registerkarte ***Durchsuchen*** aus, und suchen Sie nach **WindowsAzure. Messaging. Managed**.

    ![Windows Azure-Messaging Paket suchen](images/AzureLabs-Lab8-103.png)

4.  Wählen Sie das Ergebnis aus (wie unten gezeigt), und aktivieren Sie im Fenster rechts das Kontrollkästchen neben **Project**. Dadurch wird ein Tick in das Kontrollkästchen neben **Project**und das Kontrollkästchen neben dem Projekt **Assembly-CSharp** und **unitymrnotifhub** angezeigt.

    ![alle Projekte über tacken](images/AzureLabs-Lab8-104.png)

5.  Die ursprünglich bereitgestellte Version ist **möglicherweise nicht** kompatibel mit diesem Projekt. Klicken Sie daher auf das Dropdown Menü neben **Version**, und klicken Sie auf **Version 0.1.7.9**und dann auf **Installieren**.

6.  Die Installation des nuget-Pakets ist nun abgeschlossen. Suchen Sie den kommentierten Code, den Sie in die **notificationreceiver** -Klasse eingegeben haben, und entfernen Sie die Kommentare.



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a>Kapitel 18: unitymrnotiehub-Anwendung bearbeiten, notificationreceiver-Klasse

Nachdem Sie die **nuget-Pakete**hinzugefügt haben, müssen Sie den *Kommentar* für einen Teil des Codes in der **notificationreceiver** -Klasse aufheben.

Dazu zählen:

1. Der Namespace oben:

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. Sämtlicher Code in der **initnotificationsasync ()** -Methode:

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
> Der obige Code enthält einen Kommentar darin: Stellen Sie sicher, dass Sie diesen Kommentar nicht versehentlich auskommentiert haben (da der Code nicht kompiliert wird, wenn Sie über! verfügen).

3. Und schließlich das **Channel_PushNotificationReceived** -Ereignis:

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

Wenn Sie nicht kommentiert sind, stellen Sie sicher, dass Sie speichern, und fahren Sie dann mit dem nächsten Kapitel fort.

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a>Kapitel 19: Zuordnen des Projekts für gemischte Realität zur Store-App

Nun müssen Sie das **gemischte Reality** -Projekt der Store-App zuordnen, die Sie in zu Beginn des Labs erstellt haben.

1.  Öffnen Sie die Projekt Mappe.

2.  Klicken Sie mit der rechten Maustaste auf das UWP-App-Projekt im Projektmappen-Explorer Panel, und wählen Sie dann die Option zum **Speichern**und **Zuordnen der APP zum Store..** ..

    ![Store-Zuordnung öffnen](images/AzureLabs-Lab8-105.png)

3.  Es wird ein neues Fenster **mit dem Namen "App dem Windows Store zuordnen**" angezeigt. Klicken Sie auf **Weiter**.

    ![zum nächsten Bildschirm wechseln](images/AzureLabs-Lab8-106.png)

4.  Es werden alle Anwendungen geladen, die dem Konto zugeordnet sind, das Sie angemeldet haben. Wenn Sie nicht bei Ihrem Konto angemeldet sind, können Sie sich auf dieser Seite **Anmelden** .

5.  Suchen Sie den **Namen der Store-App** , den Sie zu Beginn dieses Tutorials erstellt haben, und wählen Sie ihn aus. Klicken Sie dann auf **Weiter**.

    ![Suchen und Auswählen Ihres Speicher namens](images/AzureLabs-Lab8-107.png)

6.  Klicken Sie auf **zuordnen**.

    ![Zuordnen der APP](images/AzureLabs-Lab8-108.png)

7.  Ihre APP ist nun der Store-App **zugeordnet** . Dies ist erforderlich, um Benachrichtigungen zu aktivieren.

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a>Kapitel 20: Bereitstellen von unitymrnotiehub-und unitydesktopnotiehub-Anwendungen

Dieses Kapitel kann mit zwei Personen einfacher sein, da das Ergebnis sowohl apps, die ausgeführt werden, eine auf dem Computer Desktop und die andere in Ihrem immersiven Headset enthalten.

Die immersive Headset-App wartet auf den Empfang von Änderungen an der Szene (Positionsänderungen der lokalen gameobjects), und die Desktop-App nimmt Änderungen an Ihrer lokalen Szene vor (Positionsänderungen), die für die Mr-APP freigegeben werden. Es ist sinnvoll, zuerst die Mr-APP und anschließend die Desktop-App bereitzustellen, damit der Empfänger mit dem lauschen beginnen kann.

So stellen Sie die **unitymrnotifhub** -App auf Ihrem lokalen Computer bereit:

1.  Öffnen Sie die Projektmappendatei Ihrer **unitymrnotilohub** -app in **Visual Studio 2017**.

2.  Wählen Sieauf der Projektmappenplattform die Option **x86, lokaler Computer**aus.

3.  Wählen Sie in der Projektmappenkonfiguration **Debuggen**.

    ![Projekt Konfiguration festlegen](images/AzureLabs-Lab8-109.png)

4.  Wechseln Sie zum **Menü Erstellen** , und klicken Sie auf **Lösung** bereitstellen, um die Anwendung auf Ihren Computer zu übertragen.

5.  Ihre APP sollte nun in der Liste der installierten apps angezeigt werden, die gestartet werden können.

So stellen Sie die **unitydesktopnotifhub** -App auf dem lokalen Computer bereit:

1.  Öffnen Sie die Projektmappendatei Ihrer **unitydesktopnotilohub** -app in **Visual Studio 2017**.

2.  Wählen Sieauf der Projektmappenplattform die Option **x86, lokaler Computer**aus.

3.  Wählen Sie in der Projektmappenkonfiguration **Debuggen**.

    ![Projekt Konfiguration festlegen](images/AzureLabs-Lab8-110.png)

4.  Wechseln Sie zum **Menü Erstellen** , und klicken Sie auf **Lösung** bereitstellen, um die Anwendung auf Ihren Computer zu übertragen.

5.  Ihre APP sollte nun in der Liste der installierten apps angezeigt werden, die gestartet werden können.

6.  Starten Sie die Mixed Reality-Anwendung, gefolgt von der Desktop Anwendung.

Wenn beide Anwendungen ausgeführt werden, verschieben Sie ein Objekt in der Desktop Szene (mit der linken Maustaste). Diese Positionsänderungen werden lokal, serialisiert und an den Funktionen-App-Dienst gesendet. Der Funktionen-App-Dienst aktualisiert dann die Tabelle zusammen mit dem Notification Hub. Wenn Sie ein Update erhalten haben, sendet der Notification Hub die aktualisierten Daten direkt an alle registrierten Anwendungen (in diesem Fall die immersive Headset-APP), von der die eingehenden Daten deserialisiert und die neuen Positionsdaten auf die lokalen Objekte angewendet werden. Verschieben in Szene.


## <a name="your-finished-your-azure-notification-hubs-application"></a>Ihre Azure Notification Hubs-Anwendung ist abgeschlossen.
 
Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die den Azure Notification Hubs-Dienst nutzt und die Kommunikation zwischen Apps ermöglicht.
 
![Endprodukt-Ende](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a>Bonus Übungen

### <a name="exercise-1"></a>Übung 1

Können Sie herausfinden, wie Sie die Farbe der gameobjects ändern und diese Benachrichtigung an andere apps, die die Szene anzeigen, senden?

### <a name="exercise-2"></a>Übung 2

Können Sie die gameobjects-Bewegung zu ihrer Mr-app hinzufügen und die aktualisierte Szene in Ihrer Desktop-App sehen?
