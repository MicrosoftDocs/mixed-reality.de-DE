---
title: Beitragen von Anweisungen
description: Informationen zum mitwirken an der Windows Mixed Reality-Dokumentation.
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: c110b549603f42ec03fd6c0dc8df7bf70ba5ba9f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604654"
---
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a>Mitwirkung an Windows Mixed Reality-Entwicklerdokumentation

Willkommen bei der [öffentliches Repository für Windows Mixed Reality-Entwicklerdokumentation](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)! Allen Artikeln, die Sie erstellen oder Bearbeiten in diesem Repository **öffentlich sichtbar werden.** 

Windows Mixed Reality-Dokumentation befinden sich nun auf der docs.microsoft.com-Plattform, die GitHub-flavored Markdown (mit Markdig-Funktionen) verwendet. Im Wesentlichen ruft der Inhalt, die Sie, in diesem Repository bearbeiten in formatiert und stilisierte Seiten, die auf angezeigt wird, werden aktiviert https://docs.microsoft.com/windows/mixed-reality. 

Auf dieser Seite werden die grundlegenden Schritte und Richtlinien für Ihren Beitrag erläutert sowie links zu den Grundlagen von Markdown. Vielen Dank für Ihren Beitrag!

## <a name="before-you-start"></a>Bevor Sie beginnen

Wenn Sie eine noch nicht, Sie müssen [erstellen Sie ein GitHub-Konto](https://github.com/join).

>[!NOTE]
>Wenn Sie ein Microsoft-Mitarbeiter sind, verknüpfen Sie Ihre GitHub-Konto Ihrem Microsoft-Alias für die [Microsoft Open Source-Portal](https://repos.opensource.microsoft.com/). Verknüpfen der **"Microsoft"** und **"MicrosoftDocs"** Organisationen).

Wenn Sie Ihr GitHub-Konto einrichten, empfehlen wir Ihnen ebenfalls den einschlägigen Sicherheitsvorkehrungen:
- Erstellen Sie eine [sicheres Kennwort für Ihr Github-Konto](https://github.com/settings/admin).
- Aktivieren Sie [zweistufige Authentifizierung](https://github.com/settings/two_factor_authentication/configure).
- Speichern Sie Ihre [Wiederherstellungscodes](https://github.com/settings/auth/recovery-codes) an einem sicheren Ort.
- Aktualisieren Ihrer [öffentliche profileinstellungen](https://github.com/settings/profile).
   - Legen Sie Ihren Namen, und der Einstellung Ihrer *öffentliche e-Mail* zu *nicht Meine e-Mail-Adresse anzeigen*.
   - Es wird empfohlen, dass Sie ein Profilbild, hochladen, wie eine Miniaturansicht auf den Dokumentationsseiten angezeigt werden soll, zu denen Sie beitragen.
- Wenn Sie einen Workflow über die Befehlszeile verwenden möchten, sollten Sie erwägen, [Git Credential Manager für Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) , damit Sie nicht jedes Mal Ihr Kennwort eingeben müssen, stellen Sie einen Beitrag.

Ausführen dieser Schritte ist wichtig, wie das publishing System zu GitHub gebunden ist, und Sie werden als Autor oder "Mitwirkender", um jeden Artikel, die mit Ihrem GitHub-Alias aufgelistet werden.

## <a name="editing-an-existing-article"></a>Bearbeiten einen vorhandenen Artikel

Verwenden Sie den folgenden Workflow, damit Updates für *einen vorhandenen Artikel* über GitHub in einem Webbrowser:

1. Navigieren Sie im Artikel, die Sie im Ordner "mixed-Reality-Docs" bearbeiten möchten.
2. Wählen Sie oben rechts die Schaltfläche "Bearbeiten" (Stiftsymbol). Dies wird automatisch eine verwerfbare Verzweigung aus dem Branch "master" verzweigen.

   ![Bearbeiten Sie einen Artikel an.](images/editpage.png)
3. Bearbeiten Sie den Inhalt des Artikels (finden Sie unter ["Markdown Basics"](#markdown-basics) unter Anleitung).
4. Aktualisieren Sie die Metadaten als am oberen Rand jedes Artikels relevant:
   * Titel: Dies ist der Titel der Seite, der im Artikel angezeigt wird, wird auf der Registerkarte "Browser" angezeigt wird. Da diese für die SEO und Indizierung verwendet werden, darf nicht den Titel ändern, es sei denn, erforderlichen (wenngleich dies weniger kritisch ist, bevor Sie die öffentliche steht in der Dokumentation).
   * description: Schreiben Sie eine kurze Beschreibung des Artikels Inhalte. Diese Vorgehensweise, SEO und Ermittlung.
   * Autor: Wenn Sie den primären Besitzer der Seite sind, fügen Sie hier Ihren GitHub-Alias hinzu.
   * MS.Author: Wenn Sie den primären Besitzer der Seite sind, fügen Sie Ihr Microsoft-alias hier hinzu (Sie müssen nicht @microsoft.com, nur der Alias).
   * MS.Date: Aktualisieren Sie das Datum aus, wenn Sie wichtige Inhalte hinzufügen, auf die Seite, jedoch nicht für Korrekturen, wie Informationen benötigen, Formatierung, Grammatik oder Rechtschreibung.
   * keywords: Schlüsselwörter bei der Suchmaschinenoptimierung (Search Engine Optimization). Hinzufügen der Schlüsselwörter, die durch ein Komma und ein Leerzeichen getrennt, die spezifisch für Ihren Artikel (aber darf kein Satzzeichen stehen nach dem letzten-Schlüsselwort in der Liste); Sie müssen nicht globalen Schlüsselwörter, die für alle Artikel gelten hinzufügen, da die an anderer Stelle verwaltet werden. 
5. Wenn Sie Ihre Artikel Änderungen abgeschlossen haben, einen Bildlauf nach unten, und klicken Sie auf die **dateiänderung vorschlagen** Schaltfläche.
6. Klicken Sie auf der nächsten Seite auf **Anforderung zum Erstellen eines Pull** zum Zusammenführen von dem automatisch erstellten Branch in 'Master'.
7. Wiederholen Sie die oben genannten Schritte für den nächsten Artikel, die, den Sie bearbeiten möchten.

## <a name="creating-a-new-article"></a>Erstellen eines neuen Artikels

Verwenden Sie den folgenden Workflow zum *Erstellen neuer Artikel* im Repository Dokumentation über GitHub in einem Webbrowser:

1. Erstellen Sie eine Verzweigung aus der MicrosoftDocs/mixed-Reality-Branch "master" (mit der **Fork** Schaltfläche oben rechts).

   ![Erstellen Sie eine Verzweigung den master-Branch.](images/forkbranch.png)
2. Klicken Sie im Ordner "mixed-Reality-Docs" auf die **neue Datei erstellen** Schaltfläche oben rechts.
3. Erstellen Sie einen Namen für den Artikel (Verwenden von Bindestrichen statt Leerzeichen und Interpunktionszeichen oder Apostrophe verwenden Sie keine), und fügen Sie ".md"

   ![Benennen Sie Ihre neue Seite.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >Stellen Sie sicher, dass Sie den neuen Artikel von innerhalb des Ordners "mixed-Reality-Docs" erstellen. Sie können dies nachprüfen, indem Sie überprüfen "/ mixed-Reality-Docs /" in der neuen Zeile der Datei-Namen.

4. Fügen Sie am oberen Rand der neuen Seite die folgenden Metadaten-Block hinzu:

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

5. Geben Sie die relevanten Metadatenfelder gemäß den Anweisungen in der [obigen Abschnitt](#editing-an-existing-article).
6. Write Content Artikel mit [Markdown-Grundlagen](#markdown-basics).
7. Hinzufügen einer `## See also` Abschnitt am Ende der Artikel Links zu anderen relevanten Artikeln enthalten.
8. Klicken Sie abschließend auf **neue Commit-Datei**.
9. Klicken Sie auf **neuer Pull Request** und Zusammenführen von Ihrer Verzweigung des "master"-Branch zu MicrosoftDocs/mixed-Reality 'Master' (Stellen Sie sicher, dass der Pfeil zeigt die korrekte Methode).

   ![Erstellen von Pull Request aus Ihrem Fork in MicrosoftDocs/mixed-reality](images/pr_to_master.PNG)

## <a name="markdown-basics"></a>Grundlagen von markdown

Die folgenden Ressourcen helfen Ihnen die Informationen zum Bearbeiten der Dokumentation unter Verwendung der Markdown-Sprache zu machen:

- [Grundlagen von markdown](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [Markdown-at-a-Glance Verweis-poster](images/MarkdownPoster.pdf)
- [Zusätzliche Ressourcen für das Schreiben von Markdown für docs.microsoft.com](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>Hinzufügen von Tabellen

Aufgrund der Möglichkeit docs.microsoft.com Stile Tabellen Rahmen oder benutzerdefinierte Stile keine, auch wenn Sie, Inline-CSS versuchen. Er erscheint für einen kurzen Zeitraum funktioniert, aber letztendlich wird die Plattform des Formats aus der Tabelle entfernen. Also planen Sie voraus, und halten Sie die Tabellen einfach zu. [Hier ist eine Website, die Markdown-Tabellen erleichtert](http://www.tablesgenerator.com/markdown_tables).

Die [Docs Markdown-Erweiterung für Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) macht Tabelle auch Generation einfach, bei Verwendung von [Visual Studio Code (siehe unten)](#using-visual-studio-code) so bearbeiten Sie die Dokumentation.

### <a name="adding-images"></a>Hinzufügen von Bildern

Sie müssen Ihre Images hochladen, zu dem Ordner "mixed-Reality--Dokumentation/Bilder" im Repository, und klicken Sie dann darauf verweisen zu entsprechend in diesem Artikel. Images werden automatisch angezeigt, um auf in voller Größe, was bedeutet, wenn das Image groß ist, geben sie die gesamte Breite des Artikels. Daher empfehlen wir die bereits Ihre Images vor dem Hochladen, größenanpassung. Die empfohlene Breite liegt zwischen 600 und 700 Pixel auf, wenn Sie nach oben oder unten die Größe sollte ein dicht Screenshot oder ein Bruchteil einen Screenshot bzw. ist.

>[!IMPORTANT]
>Sie können Bilder nur vor dem Zusammenführen in Ihr verzweigtes Repository hochladen. Also, wenn Sie das Hinzufügen von Bildern zu einem Artikel planen, Sie müssen [Verwenden von Visual Studio Code](#using-visual-studio-code) , die Bilder zuerst in Ihrem Fork des "Images" Ordner hinzufügen oder sicherstellen, dass Sie schon in einem Webbrowser die folgenden:
>
>1. Verzweigt das MicrosoftDocs/mixed-Reality-Repository.
>2. Bearbeitet die Artikel in Ihrem Fork.
>3. Hochladen der Images, die Sie in Ihren Artikel zu dem Ordner "mixed-Reality--Dokumentation/Images" in Ihrem Fork verweisen.
>4. Erstellt eine **Pull-Anforderung** Ihrer Verzweigung in den "master" MicrosoftDocs/mixed-Reality-Branch zusammengeführt.
>
>Informationen zum Einrichten Ihres eigenen verzweigten Repositorys, befolgen Sie die Anweisungen für [Erstellen eines neuen Artikels](#creating-a-new-article).

## <a name="previewing-your-work"></a>Anzeigen einer Vorschau der Arbeits

Während der Bearbeitung in GitHub über einen Webbrowser ein, klicken Sie auf die **Vorschau** Registerkarte am oberen Rand der Seite, um Ihre Eingaben vor dem Ausführen eines Commits für eine Vorschau anzeigen. 

>[!NOTE]
>Vorschau Ihrer Änderungen auf review.docs.microsoft.com ist nur verfügbar für Microsoft-Mitarbeiter

Microsoft-Mitarbeiter: Nachdem Ihre Beiträge in den "master"-Branch zusammengeführt wurden, können Sie sehen, wie die Dokumentation aussehen wird, bevor Sie darin auf öffentlichen https://review.docs.microsoft.com/windows/mixed-reality?branch=master (Suchen Sie Ihren Artikel über das Inhaltsverzeichnis in der linken Spalte).

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>Bearbeiten im Browser oder mit einem desktop-Client bearbeiten

Bearbeiten im Browser ist die einfachste Möglichkeit, schnelle Änderungen vornehmen, es gibt jedoch einige Nachteile:

- Erhalten Sie nicht-Rechtschreibprüfung.
- Erhalten Sie keine Smart Verknüpfungen zu anderen Artikeln (Sie müssen manuell des Artikels Dateiname eingeben).
- Es kann zum Hochladen und Bilder verweisen mühsam sein.

Wenn Sie eher nicht mit diesen Problemen umgehen sollen, müssen Sie bevorzugt mit einem desktop-Client wie [Visual Studio Code](https://code.visualstudio.com/) mit nur wenigen [hilfreiche Erweiterungen](#useful-extensions) zum mitwirken an der Dokumentation.

## <a name="using-visual-studio-code"></a>Mithilfe von Visual Studio Code

Für die Gründe aufgeführt [oben](#editing-in-the-browser-vs-editing-with-a-desktop-client), Sie bevorzugt mit einem desktop-Client so bearbeiten Sie die Dokumentation, statt einen Webbrowser. Es wird empfohlen, [Visual Studio Code](https://code.visualstudio.com/).

### <a name="setup"></a>Setup

Um Visual Studio Code zum Arbeiten mit diesem Repository zu konfigurieren, gehen Sie wie folgt vor:

1. In einem Webbrowser:
    1. Installieren Sie [Git für Ihren PC](https://git-scm.com/downloads).
    2. Installieren Sie [Visual Studio-Code](https://code.visualstudio.com/).
    3. [Erstellen Sie eine Verzweigung MicrosoftDocs/mixed-Reality](#creating-a-new-article) sofern Sie noch nicht geschehen.
    4. Klicken Sie in Ihrem Fork, **Klonen oder herunterladen** und kopieren Sie die URL.
2. Erstellen Sie einen lokalen Klon Ihrer Verzweigung in Visual Studio Code ein:
    1. Von der **Ansicht** , wählen Sie im Menü **Befehlspalette**.
    2. Typ "Git:Clone."
    3. Fügen Sie die URL, die Sie gerade kopiert haben.
    4. Wählen Sie den Speicherort zum Speichern des Klons auf Ihrem PC.
    5. Klicken Sie auf **öffnen Repository** in das Popupfenster.

### <a name="editing-documentation"></a>Bearbeiten die Dokumentation

Verwenden Sie den folgenden Workflow, um die Dokumentation mit Visual Studio Code zu ändern:

>[!NOTE]
>Die Anleitung für [bearbeiten](#editing-an-existing-article) und [erstellen](#creating-a-new-article) Artikel, und die [Grundlagen der Bearbeitung von Markdown](#markdown-basics), von oben gilt, wenn auch mithilfe von Visual Studio Code.

1. Stellen Sie sicher, dass Ihre geklonten Verzweigung auf dem neuesten Stand mit den offiziellen-Repository ist.
   1. In einem Webbrowser, erstellen Sie einen Pull Request zum Synchronisieren der letzten Änderungen anderer Mitwirkender im MicrosoftDocs/mixed-Reality-'Master' in Ihren Fork (Stellen Sie sicher, dass der Pfeil zeigt die richtige Methode).
      
      ![Synchronisieren von Änderungen von MicrosoftDocs/mixed-Reality in Ihren fork](images/sync_repos.PNG)
   2. Klicken Sie in Visual Studio Code auf die Schaltfläche "Synchronisieren", um Ihre neu aktualisierte Verzweigung in den lokalen Klon zu synchronisieren.
      
      ![Klicken Sie auf die Schaltfläche "Synchronisieren"](images/sync_clone.png)
2. Erstellen Sie oder bearbeiten Sie die Artikel in Ihrem geklonten Repository mithilfe von Visual Studio Code.
   1. Bearbeiten Sie einen oder mehrere Artikel (Hinzufügen von Bildern zu Ordner "Images" bei Bedarf).
   2. **Speichern Sie** Änderungen in **Explorer**.
      
      ![Wählen Sie "Alle speichern" im Explorer](images/explorer_save.png)
   3. **Commit für alle** Änderungen in **Quellcodeverwaltung** (Schreiben von Commit-Nachricht, wenn Sie aufgefordert werden).
      
      ![Wählen Sie "alle in der Quellcodeverwaltung Commit"](images/source_control_commit.png)
   4. Klicken Sie auf die **Sync** Schaltfläche für die Synchronisierung die Änderungen an der Ursprung (d.h. die Verzweigung in GitHub).
      
      ![Klicken Sie auf die Schaltfläche "Synchronisieren"](images/sync_back.png)
3. In einem Webbrowser erstellen Sie einen Pull Request zum Synchronisieren von Änderungen in Ihrem Fork an MicrosoftDocs/mixed-Reality 'Master' (Stellen Sie sicher, dass der Pfeil zeigt die korrekte Methode).

   ![Erstellen von Pull Request aus Ihrem Fork in MicrosoftDocs/mixed-reality](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>Nützliche Erweiterungen

Die folgenden Visual Studio Code-Erweiterungen sind sehr nützlich, beim Bearbeiten der Dokumentation:

- [Docs Markdown-Erweiterung für Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) -Verwendung **Alt + M,** , um ein Menü mit Optionen wie für die dokumenterstellung anzuzeigen:
   - Suchen und Referenz-Images, die Sie hochgeladen haben.
   - Hinzufügen von Formatierung wie Listen, Tabellen und erläuterungen dokumentationsspezifischer wie `>[!NOTE]`.
   - Suchen Sie, und verweisen auf interne Links und Lesezeichen (Links zu bestimmten Abschnitten in einer Seite).
   - Formatierungsfehler werden hervorgehoben. (der Mauszeiger über den Fehler, um mehr zu erfahren).
- [Rechtschreibprüfung Code](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) -falsch geschriebene Wörter werden unterstrichen, mit der rechten Maustaste auf ein falsch geschriebenes Wort zu ändern oder zu speichern, die dem Wörterbuch.
