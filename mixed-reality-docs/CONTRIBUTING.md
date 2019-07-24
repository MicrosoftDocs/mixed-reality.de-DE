---
title: Beitragende Anweisungen
description: Erfahren Sie, wie Sie an der Windows Mixed Reality-Dokumentation mitwirken können.
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: c110b549603f42ec03fd6c0dc8df7bf70ba5ba9f
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516225"
---
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a>Beitrag zur Windows Mixed Reality-Entwicklerdokumentation

Willkommen beim [öffentlichen Repository für die Windows Mixed Reality-Entwicklerdokumentation](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)! Alle Artikel, die Sie in diesem Repository erstellen oder bearbeiten **, sind öffentlich sichtbar.** 

Windows Mixed Reality-Dokumente befinden sich jetzt auf der docs.Microsoft.com-Plattform, die das GitHub-optimierte markdown (mit markdig-Features) verwendet. Im Wesentlichen wird der Inhalt, den Sie in diesem Repository bearbeiten, in formatierte und stilisierte Seiten https://docs.microsoft.com/windows/mixed-reality umgewandelt, die unter angezeigt werden. 

Auf dieser Seite werden die grundlegenden Schritte und Richtlinien für den Beitrag sowie Links zu markdown-Grundlagen behandelt. Vielen Dank für Ihren Beitrag!

## <a name="before-you-start"></a>Bevor Sie beginnen

Wenn Sie noch nicht über ein Konto verfügen, müssen Sie [ein GitHub-Konto erstellen](https://github.com/join).

>[!NOTE]
>Wenn Sie ein Microsoft-Mitarbeiter sind, verknüpfen Sie Ihr GitHub-Konto mit Ihrem Microsoft-Alias im [Open-Source-Portal von Microsoft](https://repos.opensource.microsoft.com/). Treten Sie den Organisationen **"Microsoft"** und **"microsoftdocs"** bei.)

Wenn Sie Ihr GitHub-Konto einrichten, werden auch diese Sicherheitsvorkehrungen empfohlen:
- Erstellen Sie ein sicheres [Kennwort für Ihr GitHub-Konto](https://github.com/settings/admin).
- Aktivieren Sie die [zweistufige Authentifizierung](https://github.com/settings/two_factor_authentication/configure).
- Speichern Sie Ihre [Wiederherstellungs Codes](https://github.com/settings/auth/recovery-codes) an einem sicheren Ort.
- Aktualisieren Sie die Einstellungen für das [öffentliche Profil](https://github.com/settings/profile).
   - Legen Sie Ihren Namen fest, und legen Sie fest, dass Ihre *öffentliche e-Mail* - *Adresse nicht angezeigt*werden soll.
   - Wir empfehlen Ihnen, ein Profilbild hochzuladen, da eine Miniaturansicht auf Dokumentationsseiten angezeigt wird, zu denen Sie beitragen.
- Wenn Sie beabsichtigen, einen Befehlszeilen Workflow zu verwenden, sollten Sie die Einrichtung [von git Credential Manager für Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) in Erwägung gezogen haben, damit Sie Ihr Kennwort nicht jedes Mal eingeben müssen, wenn Sie einen Beitrag leisten.

Diese Schritte sind wichtig, da das Veröffentlichungs System an GitHub gebunden ist und Sie als Autor oder Mitwirkender für jeden Artikel mithilfe Ihres GitHub-Alias aufgeführt werden.

## <a name="editing-an-existing-article"></a>Bearbeiten eines vorhandenen Artikels

Verwenden Sie den folgenden Workflow, um Updates an *einem vorhandenen Artikel* über GitHub in einem Webbrowser vorzunehmen:

1. Navigieren Sie zu dem Artikel, den Sie im Ordner "Mixed-Reality-docs" bearbeiten möchten.
2. Klicken Sie oben rechts auf die Schaltfläche Bearbeiten (Stift Symbol). Dadurch wird automatisch eine verwerfbare Verzweigung aus dem Branch "Master" verzweigt.

   ![Bearbeiten Sie einen Artikel.](images/editpage.png)
3. Bearbeiten Sie den Inhalt des Artikels (Weitere Informationen finden Sie unten unter ["Grundlagen zu markdown"](#markdown-basics) ).
4. Aktualisieren Sie die Metadaten am Anfang jedes Artikels als relevant:
   * Tel Dies ist der Seitentitel, der auf der Registerkarte Browser angezeigt wird, wenn der Artikel angezeigt wird. Da dies für SEO und Indizierung verwendet wird, sollten Sie den Titel nur dann ändern, wenn dies erforderlich ist (obwohl dies weniger kritisch ist, bevor die Dokumentation öffentlich wird).
   * description: Schreiben Sie eine kurze Beschreibung des Inhalts des Artikels. Dies hilft bei SEO und Discovery.
   * Schrift Wenn Sie der primäre Besitzer der Seite sind, fügen Sie hier Ihren GitHub-Alias hinzu.
   * ms. Autor: Wenn Sie der primäre Besitzer der Seite sind, fügen Sie hier Ihren Microsoft-Alias hinzu (Sie @microsoft.combenötigen nicht, sondern nur den Alias).
   * ms. Datum: Aktualisieren Sie das Datum, wenn Sie der Seite umfangreiche Inhalte hinzufügen, aber nicht für Korrekturen wie Erläuterungen, Formatierung, Grammatik oder Rechtschreibprüfung.
   * Keywords Schlüsselwörter unterstützen in SEO (Suchmaschinenoptimierung). Fügen Sie Schlüsselwörter, getrennt durch ein Komma und ein Leerzeichen, ein, die für den Artikel spezifisch sind (aber kein Satzzeichen nach dem letzten Schlüsselwort in der Liste). Sie müssen keine globalen Schlüsselwörter hinzufügen, die für alle Artikel gelten, da diese an anderer Stelle verwaltet werden. 
5. Wenn Sie Ihre Artikel Änderungen abgeschlossen haben, Scrollen Sie nach unten, und klicken Sie auf die Schaltfläche **Datei Änderung vorschlagen** .
6. Klicken Sie auf der nächsten Seite auf **Pull Request erstellen** , um den automatisch erstellten Branch in "Master" zusammenzuführen.
7. Wiederholen Sie die obigen Schritte für den nächsten Artikel, den Sie bearbeiten möchten.

## <a name="creating-a-new-article"></a>Erstellen eines neuen Artikels

Verwenden Sie den folgenden Workflow, um *neue Artikel* im Dokumentations Repository über GitHub in einem Webbrowser zu erstellen:

1. Erstellen Sie eine Verzweigung aus der "Master"-Verzweigung "microsoftdocs/Mixed-Reality" (mit der Schaltfläche **Fork** in der oberen rechten Ecke).

   ![Verzweigen Sie den masterb Ranch.](images/forkbranch.png)
2. Klicken Sie im Ordner "Mixed-Reality-docs" oben rechts auf die Schaltfläche **neue Datei erstellen** .
3. Erstellen Sie einen Seitennamen für den Artikel (verwenden Sie Bindestriche anstelle von Leerzeichen, verwenden Sie keine Interpunktions Zeichen oder Apostrophe), und fügen Sie ". MD" an.

   ![Benennen Sie die neue Seite.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >Stellen Sie sicher, dass Sie den neuen Artikel aus dem Ordner "Mixed-Reality-docs" erstellen. Sie können dies überprüfen, indem Sie in der Zeile neuer Dateiname nach "/Mixed-Reality-docs/" suchen.

4. Fügen Sie am oberen Rand der neuen Seite den folgenden Metadatenblock hinzu:

   ```md
   ---
   title:
   description:
   author:
   ms.author:
   ms.date:
   ms.topic: article
   keywords:
   ---
   ```

5. Füllen Sie die relevanten Metadatenfelder gemäß den Anweisungen im [obigen Abschnitt](#editing-an-existing-article)aus.
6. Schreiben Sie Artikel Inhalte mithilfe von [markdown-Grundlagen](#markdown-basics).
7. Fügen Sie `## See also` am Ende des Artikels einen Abschnitt mit Links zu anderen relevanten Artikeln hinzu.
8. Wenn Sie fertig sind, klicken Sie auf **Commit New File**.
9. Klicken Sie auf **New Pull Request** , und führen Sie den Master-Branch ihrer Verzweigung in microsoftdocs/Mixed-Reality ' Master ' aus (stellen Sie sicher, dass der Pfeil auf die richtige Weise zeigt).

   ![Erstellen von Pull Request aus Ihrem Fork in microsoftdocs/Mixed-Reality](images/pr_to_master.PNG)

## <a name="markdown-basics"></a>Markdown-Grundlagen

Die folgenden Ressourcen helfen Ihnen, zu erfahren, wie Sie die Dokumentation mit der markdown-Sprache bearbeiten:

- [Markdown-Grundlagen](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [Markdown-Referenz Poster mit einem Blick](images/MarkdownPoster.pdf)
- [Zusätzliche Ressourcen zum Schreiben von markdown für docs.Microsoft.com](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>Hinzufügen von Tabellen

Aufgrund der Art und Weise, in der docs.Microsoft.com Stile Tabellen haben, haben Sie keine Rahmen oder benutzerdefinierten Stile, auch wenn Sie das Inline-CSS ausprobieren. Es scheint für einen kurzen Zeitraum zu funktionieren, aber schließlich entfernt die Plattform das Formatieren aus der Tabelle. Planen Sie also voraus, und halten Sie die Tabellen einfach. [Im folgenden finden Sie eine Website, mit der markdown-Tabellen einfach](http://www.tablesgenerator.com/markdown_tables)werden.

Die [docs markdown-Erweiterung für Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) erleichtert auch die Tabellen Generierung, wenn Sie [Visual Studio Code (siehe unten)](#using-visual-studio-code) verwenden, um die Dokumentation zu bearbeiten.

### <a name="adding-images"></a>Hinzufügen von Bildern

Sie müssen Ihre Images in den Ordner "Mixed-Reality-docs/Images" im Repository hochladen und entsprechend im Artikel darauf verweisen. Bilder werden automatisch in voller Größe angezeigt. Dies bedeutet, dass die gesamte Breite des Artikels ausgefüllt wird, wenn das Bild groß ist. Daher wird empfohlen, die Abbilder vor dem Hochladen vorab zu dimensionieren. Die empfohlene Breite liegt zwischen 600 und 700 Pixel. Sie sollten jedoch die Größe nach oben oder unten verkleinern, wenn es sich um einen dichten Screenshot oder einen Bruchteil eines Screenshots handelt.

>[!IMPORTANT]
>Vor dem Zusammenführen können Sie nur Bilder in Ihr verzweigtes Repository hochladen. Wenn Sie also einem Artikel Bilder hinzufügen möchten, müssen Sie [Visual Studio Code verwenden](#using-visual-studio-code) , um die Bilder zunächst dem Ordner "Images" ihrer Verzweigung hinzuzufügen, oder sicherstellen, dass Sie die folgenden Schritte in einem Webbrowser ausgeführt haben:
>
>1. Verzweigt das Repository "microsoftdocs/Mixed-Reality".
>2. Der Artikel in der Verzweigung wurde bearbeitet.
>3. Die Bilder, auf die Sie verweisen, werden in Ihrem Artikel in den Ordner "Mixed-Reality-docs/Images" in ihrer Verzweigung hochgeladen.
>4. Es wurde ein **Pull Request** erstellt, um Ihre Verzweigung mit dem Branch "Master" microsoftdocs/Mixed-Reality zusammenzuführen.
>
>Um zu erfahren, wie Sie ein eigenes verzweigtes Repository einrichten, befolgen Sie die Anweisungen zum [Erstellen eines neuen Artikels](#creating-a-new-article).

## <a name="previewing-your-work"></a>Anzeigen einer Vorschau der Arbeit

Während der Bearbeitung in GitHub über einen Webbrowser können Sie auf die Registerkarte **Vorschau** am oberen Rand der Seite klicken, um die Arbeit vor dem Commit in einer Vorschau anzuzeigen. 

>[!NOTE]
>Die Vorschau der Änderungen auf Review.docs.Microsoft.com ist nur für Microsoft-Mitarbeiter verfügbar.

Microsoft-Mitarbeiter: Nachdem Ihre Beiträge in den Branch "Master" zusammengeführt wurden, können Sie sehen, wie die Dokumentation aussehen wird, bevor Sie in https://review.docs.microsoft.com/windows/mixed-reality?branch=master der Öffentlichkeit erscheint (suchen Sie nach Ihrem Artikel mithilfe des Inhaltsverzeichnisses in der linken Spalte).

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>Bearbeiten im Browser und bearbeiten mit einem Desktop Client

Das Bearbeiten im Browser ist die einfachste Möglichkeit, schnelle Änderungen vorzunehmen, es gibt jedoch einige Nachteile:

- Sie erhalten keine Rechtschreibprüfung.
- Sie erhalten keine intelligenten Verknüpfungen mit anderen Artikeln (Sie müssen den Dateinamen des Artikels manuell eingeben).
- Das Hochladen und verweisen auf Bilder kann ein Problem sein.

Wenn Sie diese Probleme nicht beheben möchten, können Sie einen Desktop Client wie [Visual Studio Code](https://code.visualstudio.com/) mit einigen [hilfreichen Erweiterungen](#useful-extensions) verwenden, um zur Dokumentation beizutragen.

## <a name="using-visual-studio-code"></a>Verwenden von Visual Studio Code

Aus den [oben](#editing-in-the-browser-vs-editing-with-a-desktop-client)aufgeführten Gründen empfiehlt es sich, anstelle eines Webbrowsers einen Desktop Client zum Bearbeiten der Dokumentation zu verwenden. Es wird empfohlen, [Visual Studio Code](https://code.visualstudio.com/)zu verwenden.

### <a name="setup"></a>Setup

Führen Sie die folgenden Schritte aus, um Visual Studio Code für die Verwendung dieses Repository zu konfigurieren:

1. In einem Webbrowser:
    1. Installieren [Sie git für Ihren PC](https://git-scm.com/downloads).
    2. Installieren Sie [Visual Studio Code](https://code.visualstudio.com/).
    3. [Verzweigung microsoftdocs/Mixed-Reality](#creating-a-new-article) , wenn Sie dies noch nicht getan haben.
    4. Klicken Sie in der Verzweigung auf **Klonen oder herunterladen** , und kopieren Sie die URL.
2. Erstellen Sie in Visual Studio Code einen lokalen Klon Ihrer Verzweigung:
    1. Wählen Sie im Menü **Ansicht** die Option **Befehls Palette**aus.
    2. Geben Sie "git: Clone" ein.
    3. Fügen Sie die URL ein, die Sie gerade kopiert haben.
    4. Wählen Sie aus, wo der Klon auf Ihrem PC gespeichert werden soll.
    5. Klicken Sie im Popup Fenster auf Repository **Öffnen** .

### <a name="editing-documentation"></a>Bearbeiten der Dokumentation

Verwenden Sie den folgenden Workflow, um Änderungen an der Dokumentation mit Visual Studio Code vorzunehmen:

>[!NOTE]
>Alle Anleitungen zum [Bearbeiten](#editing-an-existing-article) und [Erstellen](#creating-a-new-article) von Artikeln und die [Grundlagen der Bearbeitung von markdown](#markdown-basics), die oben beschrieben werden, gelten auch für die Verwendung von Visual Studio Code.

1. Stellen Sie sicher, dass Ihre geklonte Verzweigung mit dem offiziellen Repository auf dem neuesten Stand ist.
   1. Erstellen Sie in einem Webbrowser eine Pull Request, um aktuelle Änderungen von anderen Mitwirkenden in microsoftdocs/Mixed-Reality ' Master ' mit ihrer Verzweigung zu synchronisieren (stellen Sie sicher, dass der Pfeil auf die richtige Weise zeigt).
      
      ![Synchronisieren von Änderungen von microsoftdocs/Mixed-Reality mit ihrer Verzweigung](images/sync_repos.PNG)
   2. Klicken Sie in Visual Studio Code auf die Schaltfläche synchronisieren, um die neu aktualisierte Verzweigung mit dem lokalen Klon zu synchronisieren.
      
      ![Klicken Sie auf die Schaltfläche synchronisieren](images/sync_clone.png)
2. Erstellen oder bearbeiten Sie Artikel in Ihrem geklonten Repository mithilfe von Visual Studio Code.
   1. Bearbeiten von mindestens einem Artikel (Hinzufügen von Bildern zu "Bilder", falls erforderlich).
   2. **Speichern** Sie die Änderungen im **Explorer**.
      
      ![Wählen Sie im Explorer "Alle speichern" aus.](images/explorer_save.png)
   3. **Commit für alle** Änderungen in der **Quell** Code Verwaltung Commit (Schreib Commit-Nachricht bei entsprechender Aufforderung).
      
      !["Commit für alle" in der Quell Code Verwaltung auswählen](images/source_control_commit.png)
   4. Klicken Sie auf die Schaltfläche **Synchronisieren** , um Ihre Änderungen wieder mit dem Ursprung zu synchronisieren (Ihre Verzweigung auf GitHub).
      
      ![Klicken Sie auf die Schaltfläche synchronisieren](images/sync_back.png)
3. Erstellen Sie in einem Webbrowser eine Pull Request, um neue Änderungen in der Verzweigung wieder mit microsoftdocs/Mixed-Reality ' Master ' zu synchronisieren (stellen Sie sicher, dass der Pfeil auf die richtige Weise zeigt).

   ![Erstellen von Pull Request aus Ihrem Fork in microsoftdocs/Mixed-Reality](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>Nützliche Erweiterungen

Die folgenden Visual Studio Code Erweiterungen sind beim Bearbeiten der Dokumentation sehr nützlich:

- [Docs markdown-Erweiterung für Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) : Verwenden Sie **ALT + M** , um ein Menü mit Dokument Erstellungs Optionen wie den folgenden anzuzeigen:
   - Such-und Referenz Images, die Sie hochgeladen haben.
   - Fügen Sie Formatierungen wie Listen, Tabellen und docs-spezifische aufrufsouts wie `>[!NOTE]`hinzu.
   - Suchen und verweisen auf interne Links und Lesezeichen (Links zu bestimmten Abschnitten innerhalb einer Seite).
   - Formatierungs Fehler sind hervorgehoben (zeigen Sie mit der Maus auf den Fehler, um weitere Informationen zu erhalten).
- [Code Rechtschreib](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) Prüfung: falsch geschriebene Wörter werden unterstrichen. Klicken Sie mit der rechten Maustaste auf ein falsch geschriebenes Wort, um es zu ändern oder im Wörterbuch zu speichern.
