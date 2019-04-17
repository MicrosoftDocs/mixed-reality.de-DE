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
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a><span data-ttu-id="4848b-103">Mitwirkung an Windows Mixed Reality-Entwicklerdokumentation</span><span class="sxs-lookup"><span data-stu-id="4848b-103">Contributing to Windows Mixed Reality developer documentation</span></span>

<span data-ttu-id="4848b-104">Willkommen bei der [öffentliches Repository für Windows Mixed Reality-Entwicklerdokumentation](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span><span class="sxs-lookup"><span data-stu-id="4848b-104">Welcome to the [public repo for Windows Mixed Reality developer documentation](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span></span> <span data-ttu-id="4848b-105">Allen Artikeln, die Sie erstellen oder Bearbeiten in diesem Repository **öffentlich sichtbar werden.**</span><span class="sxs-lookup"><span data-stu-id="4848b-105">Any articles you create or edit in this repo **will be visible to the public.**</span></span> 

<span data-ttu-id="4848b-106">Windows Mixed Reality-Dokumentation befinden sich nun auf der docs.microsoft.com-Plattform, die GitHub-flavored Markdown (mit Markdig-Funktionen) verwendet.</span><span class="sxs-lookup"><span data-stu-id="4848b-106">Windows Mixed Reality docs are now on the docs.microsoft.com platform, which uses GitHub-flavored Markdown (with Markdig features).</span></span> <span data-ttu-id="4848b-107">Im Wesentlichen ruft der Inhalt, die Sie, in diesem Repository bearbeiten in formatiert und stilisierte Seiten, die auf angezeigt wird, werden aktiviert https://docs.microsoft.com/windows/mixed-reality.</span><span class="sxs-lookup"><span data-stu-id="4848b-107">Essentially, the content you edit in this repo gets turned into formatted and stylized pages that show up at https://docs.microsoft.com/windows/mixed-reality.</span></span> 

<span data-ttu-id="4848b-108">Auf dieser Seite werden die grundlegenden Schritte und Richtlinien für Ihren Beitrag erläutert sowie links zu den Grundlagen von Markdown.</span><span class="sxs-lookup"><span data-stu-id="4848b-108">This page covers the basic steps and guidelines for contributing, as well as links to Markdown basics.</span></span> <span data-ttu-id="4848b-109">Vielen Dank für Ihren Beitrag!</span><span class="sxs-lookup"><span data-stu-id="4848b-109">Thank you for your contribution!</span></span>

## <a name="before-you-start"></a><span data-ttu-id="4848b-110">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="4848b-110">Before you start</span></span>

<span data-ttu-id="4848b-111">Wenn Sie eine noch nicht, Sie müssen [erstellen Sie ein GitHub-Konto](https://github.com/join).</span><span class="sxs-lookup"><span data-stu-id="4848b-111">If you don't already have one, you'll need to [create a GitHub account](https://github.com/join).</span></span>

>[!NOTE]
><span data-ttu-id="4848b-112">Wenn Sie ein Microsoft-Mitarbeiter sind, verknüpfen Sie Ihre GitHub-Konto Ihrem Microsoft-Alias für die [Microsoft Open Source-Portal](https://repos.opensource.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="4848b-112">If you're a Microsoft employee, link your GitHub account to your Microsoft alias on the [Microsoft Open Source portal](https://repos.opensource.microsoft.com/).</span></span> <span data-ttu-id="4848b-113">Verknüpfen der **"Microsoft"** und **"MicrosoftDocs"** Organisationen).</span><span class="sxs-lookup"><span data-stu-id="4848b-113">Join the **"Microsoft"** and **"MicrosoftDocs"** organizations).</span></span>

<span data-ttu-id="4848b-114">Wenn Sie Ihr GitHub-Konto einrichten, empfehlen wir Ihnen ebenfalls den einschlägigen Sicherheitsvorkehrungen:</span><span class="sxs-lookup"><span data-stu-id="4848b-114">When setting up your GitHub account, we also recommend these security precautions:</span></span>
- <span data-ttu-id="4848b-115">Erstellen Sie eine [sicheres Kennwort für Ihr Github-Konto](https://github.com/settings/admin).</span><span class="sxs-lookup"><span data-stu-id="4848b-115">Create a [strong password for your Github account](https://github.com/settings/admin).</span></span>
- <span data-ttu-id="4848b-116">Aktivieren Sie [zweistufige Authentifizierung](https://github.com/settings/two_factor_authentication/configure).</span><span class="sxs-lookup"><span data-stu-id="4848b-116">Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).</span></span>
- <span data-ttu-id="4848b-117">Speichern Sie Ihre [Wiederherstellungscodes](https://github.com/settings/auth/recovery-codes) an einem sicheren Ort.</span><span class="sxs-lookup"><span data-stu-id="4848b-117">Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.</span></span>
- <span data-ttu-id="4848b-118">Aktualisieren Ihrer [öffentliche profileinstellungen](https://github.com/settings/profile).</span><span class="sxs-lookup"><span data-stu-id="4848b-118">Update your [public profile settings](https://github.com/settings/profile).</span></span>
   - <span data-ttu-id="4848b-119">Legen Sie Ihren Namen, und der Einstellung Ihrer *öffentliche e-Mail* zu *nicht Meine e-Mail-Adresse anzeigen*.</span><span class="sxs-lookup"><span data-stu-id="4848b-119">Set your name, and consider setting your *Public email* to *Don't show my email address*.</span></span>
   - <span data-ttu-id="4848b-120">Es wird empfohlen, dass Sie ein Profilbild, hochladen, wie eine Miniaturansicht auf den Dokumentationsseiten angezeigt werden soll, zu denen Sie beitragen.</span><span class="sxs-lookup"><span data-stu-id="4848b-120">We recommend you upload a profile picture, as a thumbnail will be shown on docs pages to which you contribute.</span></span>
- <span data-ttu-id="4848b-121">Wenn Sie einen Workflow über die Befehlszeile verwenden möchten, sollten Sie erwägen, [Git Credential Manager für Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) , damit Sie nicht jedes Mal Ihr Kennwort eingeben müssen, stellen Sie einen Beitrag.</span><span class="sxs-lookup"><span data-stu-id="4848b-121">If you plan to use a command line workflow, consider setting up [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) so that you don't have to enter your password each time you make a contribution.</span></span>

<span data-ttu-id="4848b-122">Ausführen dieser Schritte ist wichtig, wie das publishing System zu GitHub gebunden ist, und Sie werden als Autor oder "Mitwirkender", um jeden Artikel, die mit Ihrem GitHub-Alias aufgelistet werden.</span><span class="sxs-lookup"><span data-stu-id="4848b-122">Taking these steps is important, as the publishing system is tied to GitHub and you'll be listed as either author or contributor to each article using your GitHub alias.</span></span>

## <a name="editing-an-existing-article"></a><span data-ttu-id="4848b-123">Bearbeiten einen vorhandenen Artikel</span><span class="sxs-lookup"><span data-stu-id="4848b-123">Editing an existing article</span></span>

<span data-ttu-id="4848b-124">Verwenden Sie den folgenden Workflow, damit Updates für *einen vorhandenen Artikel* über GitHub in einem Webbrowser:</span><span class="sxs-lookup"><span data-stu-id="4848b-124">Use the following workflow to make updates to *an existing article* via GitHub in a web browser:</span></span>

1. <span data-ttu-id="4848b-125">Navigieren Sie im Artikel, die Sie im Ordner "mixed-Reality-Docs" bearbeiten möchten.</span><span class="sxs-lookup"><span data-stu-id="4848b-125">Navigate to the article you wish to edit in the "mixed-reality-docs" folder.</span></span>
2. <span data-ttu-id="4848b-126">Wählen Sie oben rechts die Schaltfläche "Bearbeiten" (Stiftsymbol).</span><span class="sxs-lookup"><span data-stu-id="4848b-126">Select the edit button (pencil icon) in the top right.</span></span> <span data-ttu-id="4848b-127">Dies wird automatisch eine verwerfbare Verzweigung aus dem Branch "master" verzweigen.</span><span class="sxs-lookup"><span data-stu-id="4848b-127">This will automatically fork a disposable branch off the 'master' branch.</span></span>

   ![Bearbeiten Sie einen Artikel an.](images/editpage.png)
3. <span data-ttu-id="4848b-129">Bearbeiten Sie den Inhalt des Artikels (finden Sie unter ["Markdown Basics"](#markdown-basics) unter Anleitung).</span><span class="sxs-lookup"><span data-stu-id="4848b-129">Edit the content of the article (see ["Markdown basics"](#markdown-basics) below for guidance).</span></span>
4. <span data-ttu-id="4848b-130">Aktualisieren Sie die Metadaten als am oberen Rand jedes Artikels relevant:</span><span class="sxs-lookup"><span data-stu-id="4848b-130">Update metadata as relevant at the top of each article:</span></span>
   * <span data-ttu-id="4848b-131">Titel: Dies ist der Titel der Seite, der im Artikel angezeigt wird, wird auf der Registerkarte "Browser" angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="4848b-131">title: This is the page title that appears in the browser tab when the article is being viewed.</span></span> <span data-ttu-id="4848b-132">Da diese für die SEO und Indizierung verwendet werden, darf nicht den Titel ändern, es sei denn, erforderlichen (wenngleich dies weniger kritisch ist, bevor Sie die öffentliche steht in der Dokumentation).</span><span class="sxs-lookup"><span data-stu-id="4848b-132">As this is used for SEO and indexing, you shouldn't change the title unless necessary (though this is less critical before documentation goes public).</span></span>
   * <span data-ttu-id="4848b-133">description: Schreiben Sie eine kurze Beschreibung des Artikels Inhalte.</span><span class="sxs-lookup"><span data-stu-id="4848b-133">description: Write a brief description of the article's content.</span></span> <span data-ttu-id="4848b-134">Diese Vorgehensweise, SEO und Ermittlung.</span><span class="sxs-lookup"><span data-stu-id="4848b-134">This aids in SEO and discovery.</span></span>
   * <span data-ttu-id="4848b-135">Autor: Wenn Sie den primären Besitzer der Seite sind, fügen Sie hier Ihren GitHub-Alias hinzu.</span><span class="sxs-lookup"><span data-stu-id="4848b-135">author: If you are the primary owner of the page, add your GitHub alias here.</span></span>
   * <span data-ttu-id="4848b-136">MS.Author: Wenn Sie den primären Besitzer der Seite sind, fügen Sie Ihr Microsoft-alias hier hinzu (Sie müssen nicht @microsoft.com, nur der Alias).</span><span class="sxs-lookup"><span data-stu-id="4848b-136">ms.author: If you are the primary owner of the page, add your Microsoft alias here (you don't need @microsoft.com, just the alias).</span></span>
   * <span data-ttu-id="4848b-137">MS.Date: Aktualisieren Sie das Datum aus, wenn Sie wichtige Inhalte hinzufügen, auf die Seite, jedoch nicht für Korrekturen, wie Informationen benötigen, Formatierung, Grammatik oder Rechtschreibung.</span><span class="sxs-lookup"><span data-stu-id="4848b-137">ms.date: Update the date if you're adding major content to the page, but not for fixes like clarification, formatting, grammar, or spelling.</span></span>
   * <span data-ttu-id="4848b-138">keywords: Schlüsselwörter bei der Suchmaschinenoptimierung (Search Engine Optimization).</span><span class="sxs-lookup"><span data-stu-id="4848b-138">keywords: Keywords aid in SEO (search engine optimization).</span></span> <span data-ttu-id="4848b-139">Hinzufügen der Schlüsselwörter, die durch ein Komma und ein Leerzeichen getrennt, die spezifisch für Ihren Artikel (aber darf kein Satzzeichen stehen nach dem letzten-Schlüsselwort in der Liste); Sie müssen nicht globalen Schlüsselwörter, die für alle Artikel gelten hinzufügen, da die an anderer Stelle verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="4848b-139">Add keywords, separated by a comma and a space, that are specific to your article (but no punctuation after the last keyword in your list); you don't need to add global keywords that apply to all articles, as those are managed elsewhere.</span></span> 
5. <span data-ttu-id="4848b-140">Wenn Sie Ihre Artikel Änderungen abgeschlossen haben, einen Bildlauf nach unten, und klicken Sie auf die **dateiänderung vorschlagen** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="4848b-140">When you've completed your article edits, scroll down and click the **Propose file change** button.</span></span>
6. <span data-ttu-id="4848b-141">Klicken Sie auf der nächsten Seite auf **Anforderung zum Erstellen eines Pull** zum Zusammenführen von dem automatisch erstellten Branch in 'Master'.</span><span class="sxs-lookup"><span data-stu-id="4848b-141">On the next page, click **Create pull request** to merge your automatically-created branch into 'master.'</span></span>
7. <span data-ttu-id="4848b-142">Wiederholen Sie die oben genannten Schritte für den nächsten Artikel, die, den Sie bearbeiten möchten.</span><span class="sxs-lookup"><span data-stu-id="4848b-142">Repeat the steps above for the next article you want to edit.</span></span>

## <a name="creating-a-new-article"></a><span data-ttu-id="4848b-143">Erstellen eines neuen Artikels</span><span class="sxs-lookup"><span data-stu-id="4848b-143">Creating a new article</span></span>

<span data-ttu-id="4848b-144">Verwenden Sie den folgenden Workflow zum *Erstellen neuer Artikel* im Repository Dokumentation über GitHub in einem Webbrowser:</span><span class="sxs-lookup"><span data-stu-id="4848b-144">Use the following workflow to *create new articles* in the documentation repo via GitHub in a web browser:</span></span>

1. <span data-ttu-id="4848b-145">Erstellen Sie eine Verzweigung aus der MicrosoftDocs/mixed-Reality-Branch "master" (mit der **Fork** Schaltfläche oben rechts).</span><span class="sxs-lookup"><span data-stu-id="4848b-145">Create a fork off the MicrosoftDocs/mixed-reality 'master' branch (using the **Fork** button in the top right).</span></span>

   ![Erstellen Sie eine Verzweigung den master-Branch.](images/forkbranch.png)
2. <span data-ttu-id="4848b-147">Klicken Sie im Ordner "mixed-Reality-Docs" auf die **neue Datei erstellen** Schaltfläche oben rechts.</span><span class="sxs-lookup"><span data-stu-id="4848b-147">In the "mixed-reality-docs" folder, click the **Create new file** button in the top right.</span></span>
3. <span data-ttu-id="4848b-148">Erstellen Sie einen Namen für den Artikel (Verwenden von Bindestrichen statt Leerzeichen und Interpunktionszeichen oder Apostrophe verwenden Sie keine), und fügen Sie ".md"</span><span class="sxs-lookup"><span data-stu-id="4848b-148">Create a page name for the article (use hyphens instead of spaces and don't use punctuation or apostrophes) and append ".md"</span></span>

   ![Benennen Sie Ihre neue Seite.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   ><span data-ttu-id="4848b-150">Stellen Sie sicher, dass Sie den neuen Artikel von innerhalb des Ordners "mixed-Reality-Docs" erstellen.</span><span class="sxs-lookup"><span data-stu-id="4848b-150">Make sure you create the new article from within the "mixed-reality-docs" folder.</span></span> <span data-ttu-id="4848b-151">Sie können dies nachprüfen, indem Sie überprüfen "/ mixed-Reality-Docs /" in der neuen Zeile der Datei-Namen.</span><span class="sxs-lookup"><span data-stu-id="4848b-151">You can confirm this by checking for "/mixed-reality-docs/" in the new file name line.</span></span>

4. <span data-ttu-id="4848b-152">Fügen Sie am oberen Rand der neuen Seite die folgenden Metadaten-Block hinzu:</span><span class="sxs-lookup"><span data-stu-id="4848b-152">At the top of your new page, add the following metadata block:</span></span>

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

5. <span data-ttu-id="4848b-153">Geben Sie die relevanten Metadatenfelder gemäß den Anweisungen in der [obigen Abschnitt](#editing-an-existing-article).</span><span class="sxs-lookup"><span data-stu-id="4848b-153">Fill in the relevant metadata fields per the instructions in the [section above](#editing-an-existing-article).</span></span>
6. <span data-ttu-id="4848b-154">Write Content Artikel mit [Markdown-Grundlagen](#markdown-basics).</span><span class="sxs-lookup"><span data-stu-id="4848b-154">Write article content using [Markdown basics](#markdown-basics).</span></span>
7. <span data-ttu-id="4848b-155">Hinzufügen einer `## See also` Abschnitt am Ende der Artikel Links zu anderen relevanten Artikeln enthalten.</span><span class="sxs-lookup"><span data-stu-id="4848b-155">Add a `## See also` section at the bottom of the article with links to other relevant articles.</span></span>
8. <span data-ttu-id="4848b-156">Klicken Sie abschließend auf **neue Commit-Datei**.</span><span class="sxs-lookup"><span data-stu-id="4848b-156">When finished, click **Commit new file**.</span></span>
9. <span data-ttu-id="4848b-157">Klicken Sie auf **neuer Pull Request** und Zusammenführen von Ihrer Verzweigung des "master"-Branch zu MicrosoftDocs/mixed-Reality 'Master' (Stellen Sie sicher, dass der Pfeil zeigt die korrekte Methode).</span><span class="sxs-lookup"><span data-stu-id="4848b-157">Click **New pull request** and merge your fork's 'master' branch into MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![Erstellen von Pull Request aus Ihrem Fork in MicrosoftDocs/mixed-reality](images/pr_to_master.PNG)

## <a name="markdown-basics"></a><span data-ttu-id="4848b-159">Grundlagen von markdown</span><span class="sxs-lookup"><span data-stu-id="4848b-159">Markdown basics</span></span>

<span data-ttu-id="4848b-160">Die folgenden Ressourcen helfen Ihnen die Informationen zum Bearbeiten der Dokumentation unter Verwendung der Markdown-Sprache zu machen:</span><span class="sxs-lookup"><span data-stu-id="4848b-160">The following resources will help you learn how to edit documentation using the Markdown language:</span></span>

- [<span data-ttu-id="4848b-161">Grundlagen von markdown</span><span class="sxs-lookup"><span data-stu-id="4848b-161">Markdown basics</span></span>](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [<span data-ttu-id="4848b-162">Markdown-at-a-Glance Verweis-poster</span><span class="sxs-lookup"><span data-stu-id="4848b-162">Markdown-at-a-glance reference poster</span></span>](images/MarkdownPoster.pdf)
- [<span data-ttu-id="4848b-163">Zusätzliche Ressourcen für das Schreiben von Markdown für docs.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="4848b-163">Additional resources for writing Markdown for docs.microsoft.com</span></span>](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a><span data-ttu-id="4848b-164">Hinzufügen von Tabellen</span><span class="sxs-lookup"><span data-stu-id="4848b-164">Adding tables</span></span>

<span data-ttu-id="4848b-165">Aufgrund der Möglichkeit docs.microsoft.com Stile Tabellen Rahmen oder benutzerdefinierte Stile keine, auch wenn Sie, Inline-CSS versuchen.</span><span class="sxs-lookup"><span data-stu-id="4848b-165">Because of the way docs.microsoft.com styles tables, they won’t have borders or custom styles, even if you try inline CSS.</span></span> <span data-ttu-id="4848b-166">Er erscheint für einen kurzen Zeitraum funktioniert, aber letztendlich wird die Plattform des Formats aus der Tabelle entfernen.</span><span class="sxs-lookup"><span data-stu-id="4848b-166">It will appear to work for a short period of time, but eventually the platform will strip the styling out of the table.</span></span> <span data-ttu-id="4848b-167">Also planen Sie voraus, und halten Sie die Tabellen einfach zu.</span><span class="sxs-lookup"><span data-stu-id="4848b-167">So plan ahead and keep your tables simple.</span></span> <span data-ttu-id="4848b-168">[Hier ist eine Website, die Markdown-Tabellen erleichtert](http://www.tablesgenerator.com/markdown_tables).</span><span class="sxs-lookup"><span data-stu-id="4848b-168">[Here’s a site that makes Markdown tables easy](http://www.tablesgenerator.com/markdown_tables).</span></span>

<span data-ttu-id="4848b-169">Die [Docs Markdown-Erweiterung für Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) macht Tabelle auch Generation einfach, bei Verwendung von [Visual Studio Code (siehe unten)](#using-visual-studio-code) so bearbeiten Sie die Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="4848b-169">The [Docs Markdown Extension for Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) also makes table generation easy if you're using [Visual Studio Code (see below)](#using-visual-studio-code) to edit the documentation.</span></span>

### <a name="adding-images"></a><span data-ttu-id="4848b-170">Hinzufügen von Bildern</span><span class="sxs-lookup"><span data-stu-id="4848b-170">Adding images</span></span>

<span data-ttu-id="4848b-171">Sie müssen Ihre Images hochladen, zu dem Ordner "mixed-Reality--Dokumentation/Bilder" im Repository, und klicken Sie dann darauf verweisen zu entsprechend in diesem Artikel.</span><span class="sxs-lookup"><span data-stu-id="4848b-171">You’ll need to upload your images to the "mixed-reality-docs/images" folder in the repo, and then reference them appropriately in the article.</span></span> <span data-ttu-id="4848b-172">Images werden automatisch angezeigt, um auf in voller Größe, was bedeutet, wenn das Image groß ist, geben sie die gesamte Breite des Artikels.</span><span class="sxs-lookup"><span data-stu-id="4848b-172">Images will automatically show up at full-size, which means if your image is large, it’ll fill the entire width of the article.</span></span> <span data-ttu-id="4848b-173">Daher empfehlen wir die bereits Ihre Images vor dem Hochladen, größenanpassung.</span><span class="sxs-lookup"><span data-stu-id="4848b-173">Thus, we recommend pre-sizing your images before uploading them.</span></span> <span data-ttu-id="4848b-174">Die empfohlene Breite liegt zwischen 600 und 700 Pixel auf, wenn Sie nach oben oder unten die Größe sollte ein dicht Screenshot oder ein Bruchteil einen Screenshot bzw. ist.</span><span class="sxs-lookup"><span data-stu-id="4848b-174">The recommended width is between 600 and 700 pixels, though you should size up or down if it’s a dense screenshot or a fraction of a screenshot, respectively.</span></span>

>[!IMPORTANT]
><span data-ttu-id="4848b-175">Sie können Bilder nur vor dem Zusammenführen in Ihr verzweigtes Repository hochladen.</span><span class="sxs-lookup"><span data-stu-id="4848b-175">You can only upload images to your forked repo before merging.</span></span> <span data-ttu-id="4848b-176">Also, wenn Sie das Hinzufügen von Bildern zu einem Artikel planen, Sie müssen [Verwenden von Visual Studio Code](#using-visual-studio-code) , die Bilder zuerst in Ihrem Fork des "Images" Ordner hinzufügen oder sicherstellen, dass Sie schon in einem Webbrowser die folgenden:</span><span class="sxs-lookup"><span data-stu-id="4848b-176">So, if you plan on adding images to an article, you'll need to [use Visual Studio Code](#using-visual-studio-code) to add the images to your fork's "images" folder first or make sure you've done the following in a web browser:</span></span>
>
>1. <span data-ttu-id="4848b-177">Verzweigt das MicrosoftDocs/mixed-Reality-Repository.</span><span class="sxs-lookup"><span data-stu-id="4848b-177">Forked the MicrosoftDocs/mixed-reality repo.</span></span>
>2. <span data-ttu-id="4848b-178">Bearbeitet die Artikel in Ihrem Fork.</span><span class="sxs-lookup"><span data-stu-id="4848b-178">Edited the article in your fork.</span></span>
>3. <span data-ttu-id="4848b-179">Hochladen der Images, die Sie in Ihren Artikel zu dem Ordner "mixed-Reality--Dokumentation/Images" in Ihrem Fork verweisen.</span><span class="sxs-lookup"><span data-stu-id="4848b-179">Uploaded the images you're referencing in your article to the "mixed-reality-docs/images" folder in your fork.</span></span>
>4. <span data-ttu-id="4848b-180">Erstellt eine **Pull-Anforderung** Ihrer Verzweigung in den "master" MicrosoftDocs/mixed-Reality-Branch zusammengeführt.</span><span class="sxs-lookup"><span data-stu-id="4848b-180">Created a **pull request** to merge your fork into the MicrosoftDocs/mixed-reality 'master' branch.</span></span>
>
><span data-ttu-id="4848b-181">Informationen zum Einrichten Ihres eigenen verzweigten Repositorys, befolgen Sie die Anweisungen für [Erstellen eines neuen Artikels](#creating-a-new-article).</span><span class="sxs-lookup"><span data-stu-id="4848b-181">To learn how to set up your own forked repo, follow the instructions for [creating a new article](#creating-a-new-article).</span></span>

## <a name="previewing-your-work"></a><span data-ttu-id="4848b-182">Anzeigen einer Vorschau der Arbeits</span><span class="sxs-lookup"><span data-stu-id="4848b-182">Previewing your work</span></span>

<span data-ttu-id="4848b-183">Während der Bearbeitung in GitHub über einen Webbrowser ein, klicken Sie auf die **Vorschau** Registerkarte am oberen Rand der Seite, um Ihre Eingaben vor dem Ausführen eines Commits für eine Vorschau anzeigen.</span><span class="sxs-lookup"><span data-stu-id="4848b-183">While editing in GitHub via a web browser, you can click the **Preview** tab near the top of the page to preview your work before committing.</span></span> 

>[!NOTE]
><span data-ttu-id="4848b-184">Vorschau Ihrer Änderungen auf review.docs.microsoft.com ist nur verfügbar für Microsoft-Mitarbeiter</span><span class="sxs-lookup"><span data-stu-id="4848b-184">Previewing your changes on review.docs.microsoft.com is only available to Microsoft employees</span></span>

<span data-ttu-id="4848b-185">Microsoft-Mitarbeiter: Nachdem Ihre Beiträge in den "master"-Branch zusammengeführt wurden, können Sie sehen, wie die Dokumentation aussehen wird, bevor Sie darin auf öffentlichen https://review.docs.microsoft.com/windows/mixed-reality?branch=master (Suchen Sie Ihren Artikel über das Inhaltsverzeichnis in der linken Spalte).</span><span class="sxs-lookup"><span data-stu-id="4848b-185">Microsoft employees: once your contributions have been merged into the 'master' branch, you can see what the documentation will look like before it goes public at https://review.docs.microsoft.com/windows/mixed-reality?branch=master (find your article using the table of contents in the left column).</span></span>

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a><span data-ttu-id="4848b-186">Bearbeiten im Browser oder mit einem desktop-Client bearbeiten</span><span class="sxs-lookup"><span data-stu-id="4848b-186">Editing in the browser vs. editing with a desktop client</span></span>

<span data-ttu-id="4848b-187">Bearbeiten im Browser ist die einfachste Möglichkeit, schnelle Änderungen vornehmen, es gibt jedoch einige Nachteile:</span><span class="sxs-lookup"><span data-stu-id="4848b-187">Editing in the browser is the easiest way to make quick changes, however, there are a few disadvantages:</span></span>

- <span data-ttu-id="4848b-188">Erhalten Sie nicht-Rechtschreibprüfung.</span><span class="sxs-lookup"><span data-stu-id="4848b-188">You don't get spell-check.</span></span>
- <span data-ttu-id="4848b-189">Erhalten Sie keine Smart Verknüpfungen zu anderen Artikeln (Sie müssen manuell des Artikels Dateiname eingeben).</span><span class="sxs-lookup"><span data-stu-id="4848b-189">You don't get any smart-linking to other articles (you have to manually type the article's filename).</span></span>
- <span data-ttu-id="4848b-190">Es kann zum Hochladen und Bilder verweisen mühsam sein.</span><span class="sxs-lookup"><span data-stu-id="4848b-190">It can be a hassle to upload and reference images.</span></span>

<span data-ttu-id="4848b-191">Wenn Sie eher nicht mit diesen Problemen umgehen sollen, müssen Sie bevorzugt mit einem desktop-Client wie [Visual Studio Code](https://code.visualstudio.com/) mit nur wenigen [hilfreiche Erweiterungen](#useful-extensions) zum mitwirken an der Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="4848b-191">If you'd rather not deal with these issues, you may prefer to use a desktop client like [Visual Studio Code](https://code.visualstudio.com/) with a couple [helpful extensions](#useful-extensions) to contribute to documentation.</span></span>

## <a name="using-visual-studio-code"></a><span data-ttu-id="4848b-192">Mithilfe von Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4848b-192">Using Visual Studio Code</span></span>

<span data-ttu-id="4848b-193">Für die Gründe aufgeführt [oben](#editing-in-the-browser-vs-editing-with-a-desktop-client), Sie bevorzugt mit einem desktop-Client so bearbeiten Sie die Dokumentation, statt einen Webbrowser.</span><span class="sxs-lookup"><span data-stu-id="4848b-193">For the reasons listed [above](#editing-in-the-browser-vs-editing-with-a-desktop-client), you may prefer using a desktop client to edit documentation instead of a web browser.</span></span> <span data-ttu-id="4848b-194">Es wird empfohlen, [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="4848b-194">We recommend using [Visual Studio Code](https://code.visualstudio.com/).</span></span>

### <a name="setup"></a><span data-ttu-id="4848b-195">Setup</span><span class="sxs-lookup"><span data-stu-id="4848b-195">Setup</span></span>

<span data-ttu-id="4848b-196">Um Visual Studio Code zum Arbeiten mit diesem Repository zu konfigurieren, gehen Sie wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="4848b-196">Follow these steps to configure Visual Studio Code to work with this repo:</span></span>

1. <span data-ttu-id="4848b-197">In einem Webbrowser:</span><span class="sxs-lookup"><span data-stu-id="4848b-197">In a web browser:</span></span>
    1. <span data-ttu-id="4848b-198">Installieren Sie [Git für Ihren PC](https://git-scm.com/downloads).</span><span class="sxs-lookup"><span data-stu-id="4848b-198">Install [Git for your PC](https://git-scm.com/downloads).</span></span>
    2. <span data-ttu-id="4848b-199">Installieren Sie [Visual Studio-Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="4848b-199">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
    3. <span data-ttu-id="4848b-200">[Erstellen Sie eine Verzweigung MicrosoftDocs/mixed-Reality](#creating-a-new-article) sofern Sie noch nicht geschehen.</span><span class="sxs-lookup"><span data-stu-id="4848b-200">[Fork MicrosoftDocs/mixed-reality](#creating-a-new-article) if you haven't already.</span></span>
    4. <span data-ttu-id="4848b-201">Klicken Sie in Ihrem Fork, **Klonen oder herunterladen** und kopieren Sie die URL.</span><span class="sxs-lookup"><span data-stu-id="4848b-201">In your fork, click **Clone or download** and copy the URL.</span></span>
2. <span data-ttu-id="4848b-202">Erstellen Sie einen lokalen Klon Ihrer Verzweigung in Visual Studio Code ein:</span><span class="sxs-lookup"><span data-stu-id="4848b-202">Create a local clone of your fork in Visual Studio Code:</span></span>
    1. <span data-ttu-id="4848b-203">Von der **Ansicht** , wählen Sie im Menü **Befehlspalette**.</span><span class="sxs-lookup"><span data-stu-id="4848b-203">From the **View** menu, select **Command Palette**.</span></span>
    2. <span data-ttu-id="4848b-204">Typ "Git:Clone."</span><span class="sxs-lookup"><span data-stu-id="4848b-204">Type "Git:Clone."</span></span>
    3. <span data-ttu-id="4848b-205">Fügen Sie die URL, die Sie gerade kopiert haben.</span><span class="sxs-lookup"><span data-stu-id="4848b-205">Paste the URL you just copied.</span></span>
    4. <span data-ttu-id="4848b-206">Wählen Sie den Speicherort zum Speichern des Klons auf Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="4848b-206">Choose where to save the clone on your PC.</span></span>
    5. <span data-ttu-id="4848b-207">Klicken Sie auf **öffnen Repository** in das Popupfenster.</span><span class="sxs-lookup"><span data-stu-id="4848b-207">Click **Open repo** in the pop-up.</span></span>

### <a name="editing-documentation"></a><span data-ttu-id="4848b-208">Bearbeiten die Dokumentation</span><span class="sxs-lookup"><span data-stu-id="4848b-208">Editing documentation</span></span>

<span data-ttu-id="4848b-209">Verwenden Sie den folgenden Workflow, um die Dokumentation mit Visual Studio Code zu ändern:</span><span class="sxs-lookup"><span data-stu-id="4848b-209">Use the following workflow to make changes to the documentation with Visual Studio Code:</span></span>

>[!NOTE]
><span data-ttu-id="4848b-210">Die Anleitung für [bearbeiten](#editing-an-existing-article) und [erstellen](#creating-a-new-article) Artikel, und die [Grundlagen der Bearbeitung von Markdown](#markdown-basics), von oben gilt, wenn auch mithilfe von Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="4848b-210">All the guidance for [editing](#editing-an-existing-article) and [creating](#creating-a-new-article) articles, and the [basics of editing Markdown](#markdown-basics), from above applies when using Visual Studio Code as well.</span></span>

1. <span data-ttu-id="4848b-211">Stellen Sie sicher, dass Ihre geklonten Verzweigung auf dem neuesten Stand mit den offiziellen-Repository ist.</span><span class="sxs-lookup"><span data-stu-id="4848b-211">Make sure your cloned fork is up-to-date with the official repo.</span></span>
   1. <span data-ttu-id="4848b-212">In einem Webbrowser, erstellen Sie einen Pull Request zum Synchronisieren der letzten Änderungen anderer Mitwirkender im MicrosoftDocs/mixed-Reality-'Master' in Ihren Fork (Stellen Sie sicher, dass der Pfeil zeigt die richtige Methode).</span><span class="sxs-lookup"><span data-stu-id="4848b-212">In a web browser, create a pull request to sync recent changes from other contributors in MicrosoftDocs/mixed-reality 'master' to your fork (make sure the arrow is pointing the right way).</span></span>
      
      ![Synchronisieren von Änderungen von MicrosoftDocs/mixed-Reality in Ihren fork](images/sync_repos.PNG)
   2. <span data-ttu-id="4848b-214">Klicken Sie in Visual Studio Code auf die Schaltfläche "Synchronisieren", um Ihre neu aktualisierte Verzweigung in den lokalen Klon zu synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="4848b-214">In Visual Studio Code, click the sync button to sync your freshly updated fork to the local clone.</span></span>
      
      ![Klicken Sie auf die Schaltfläche "Synchronisieren"](images/sync_clone.png)
2. <span data-ttu-id="4848b-216">Erstellen Sie oder bearbeiten Sie die Artikel in Ihrem geklonten Repository mithilfe von Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="4848b-216">Create or edit articles in your cloned repo using Visual Studio Code.</span></span>
   1. <span data-ttu-id="4848b-217">Bearbeiten Sie einen oder mehrere Artikel (Hinzufügen von Bildern zu Ordner "Images" bei Bedarf).</span><span class="sxs-lookup"><span data-stu-id="4848b-217">Edit one or more articles (add images to “images” folder if necessary).</span></span>
   2. <span data-ttu-id="4848b-218">**Speichern Sie** Änderungen in **Explorer**.</span><span class="sxs-lookup"><span data-stu-id="4848b-218">**Save** changes in **Explorer**.</span></span>
      
      ![Wählen Sie "Alle speichern" im Explorer](images/explorer_save.png)
   3. <span data-ttu-id="4848b-220">**Commit für alle** Änderungen in **Quellcodeverwaltung** (Schreiben von Commit-Nachricht, wenn Sie aufgefordert werden).</span><span class="sxs-lookup"><span data-stu-id="4848b-220">**Commit all** changes in **Source Control** (write commit message when prompted).</span></span>
      
      ![Wählen Sie "alle in der Quellcodeverwaltung Commit"](images/source_control_commit.png)
   4. <span data-ttu-id="4848b-222">Klicken Sie auf die **Sync** Schaltfläche für die Synchronisierung die Änderungen an der Ursprung (d.h. die Verzweigung in GitHub).</span><span class="sxs-lookup"><span data-stu-id="4848b-222">Click the **sync** button to sync your changes back to origin (your fork on GitHub).</span></span>
      
      ![Klicken Sie auf die Schaltfläche "Synchronisieren"](images/sync_back.png)
3. <span data-ttu-id="4848b-224">In einem Webbrowser erstellen Sie einen Pull Request zum Synchronisieren von Änderungen in Ihrem Fork an MicrosoftDocs/mixed-Reality 'Master' (Stellen Sie sicher, dass der Pfeil zeigt die korrekte Methode).</span><span class="sxs-lookup"><span data-stu-id="4848b-224">In a web browser, create a pull request to sync new changes in your fork back to MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![Erstellen von Pull Request aus Ihrem Fork in MicrosoftDocs/mixed-reality](images/pr_to_master.PNG)

### <a name="useful-extensions"></a><span data-ttu-id="4848b-226">Nützliche Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="4848b-226">Useful extensions</span></span>

<span data-ttu-id="4848b-227">Die folgenden Visual Studio Code-Erweiterungen sind sehr nützlich, beim Bearbeiten der Dokumentation:</span><span class="sxs-lookup"><span data-stu-id="4848b-227">The following Visual Studio Code extensions are very useful when editing documentation:</span></span>

- <span data-ttu-id="4848b-228">[Docs Markdown-Erweiterung für Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) -Verwendung **Alt + M,** , um ein Menü mit Optionen wie für die dokumenterstellung anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="4848b-228">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **Alt+M** to bring up a menu of docs authoring options like:</span></span>
   - <span data-ttu-id="4848b-229">Suchen und Referenz-Images, die Sie hochgeladen haben.</span><span class="sxs-lookup"><span data-stu-id="4848b-229">Search and reference images you've uploaded.</span></span>
   - <span data-ttu-id="4848b-230">Hinzufügen von Formatierung wie Listen, Tabellen und erläuterungen dokumentationsspezifischer wie `>[!NOTE]`.</span><span class="sxs-lookup"><span data-stu-id="4848b-230">Add formatting like lists, tables, and docs-specific call-outs like `>[!NOTE]`.</span></span>
   - <span data-ttu-id="4848b-231">Suchen Sie, und verweisen auf interne Links und Lesezeichen (Links zu bestimmten Abschnitten in einer Seite).</span><span class="sxs-lookup"><span data-stu-id="4848b-231">Search and reference internal links and bookmarks (links to specific sections within a page).</span></span>
   - <span data-ttu-id="4848b-232">Formatierungsfehler werden hervorgehoben. (der Mauszeiger über den Fehler, um mehr zu erfahren).</span><span class="sxs-lookup"><span data-stu-id="4848b-232">Formatting errors are highlighted (hover your mouse over the error to learn more).</span></span>
- <span data-ttu-id="4848b-233">[Rechtschreibprüfung Code](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) -falsch geschriebene Wörter werden unterstrichen, mit der rechten Maustaste auf ein falsch geschriebenes Wort zu ändern oder zu speichern, die dem Wörterbuch.</span><span class="sxs-lookup"><span data-stu-id="4848b-233">[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>
