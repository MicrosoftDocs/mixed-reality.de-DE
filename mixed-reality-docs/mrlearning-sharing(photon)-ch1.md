---
title: Lernen die Freigabe-Modul für HoloLens 2 MR
description: Führen Sie diesen Kurs erfahren, wie Sie mehrere Benutzer freigegebene Umgebungen innerhalb einer HoloLens-2-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 8940de029ef5c67c38f427a238f88fcab527d79d
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327764"
---
# <a name="setting-up-photon"></a><span data-ttu-id="710fd-104">Einrichten von Photon</span><span class="sxs-lookup"><span data-stu-id="710fd-104">Setting Up Photon</span></span>

<span data-ttu-id="710fd-105">In dieser Lektion lernen wir, wie Sie für die Erstellung von einer gemeinsamen Erfahrung durch das Importieren von Photon Unity Networking (WORTSPIEL) in Ihrem Unity-Projekt vorzubereiten.</span><span class="sxs-lookup"><span data-stu-id="710fd-105">In this lesson, we will learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="710fd-106">Photon ist eine von mehreren Netzwerken Optionen Mixed Reality-Entwicklern zur Verfügung, freigegebene Anwendungen zu schaffen.</span><span class="sxs-lookup"><span data-stu-id="710fd-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="710fd-107">Es wird erfahren Sie, wie ein Photon-Konto erstellen, importieren Photon und erstellen einen optionalen lokalen Server</span><span class="sxs-lookup"><span data-stu-id="710fd-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="710fd-108">Ziele:</span><span class="sxs-lookup"><span data-stu-id="710fd-108">Objectives:</span></span>

* <span data-ttu-id="710fd-109">Erfahren Sie, wie Sie Photon-Konto erstellen</span><span class="sxs-lookup"><span data-stu-id="710fd-109">Learn how to create Photon account</span></span>

* <span data-ttu-id="710fd-110">Erfahren Sie, wie nach und importieren Sie Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="710fd-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="710fd-111">Einrichten eines lokalen Photon-Servers</span><span class="sxs-lookup"><span data-stu-id="710fd-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="710fd-112">Einrichten von Photon</span><span class="sxs-lookup"><span data-stu-id="710fd-112">Setting Up Photon</span></span>

1. <span data-ttu-id="710fd-113">Richten Sie eine [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) Konto.</span><span class="sxs-lookup"><span data-stu-id="710fd-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="710fd-114">Navigieren Sie durch Klicken auf der Registrierungsseite für Photon [diesen Link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="710fd-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="710fd-115">Befolgen Sie die Anweisungen auf der Registrierungsseite aus, um das Konto zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="710fd-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

2. <span data-ttu-id="710fd-117">Sobald Sie angemeldet sind, klicken Sie auf der SDKs.</span><span class="sxs-lookup"><span data-stu-id="710fd-117">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="710fd-118">Sobald Sie auf dieser Seite sind, klicken Sie auf "Server", und stellen Sie sicher Name schon sagt, "selbst gehostet."</span><span class="sxs-lookup"><span data-stu-id="710fd-118">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="710fd-119">Scrollen Sie nach unten, und klicken Sie auf "Server", wie in der zweiten Abbildung unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="710fd-119">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module3Chapter1step2aim](images/module3chapter1step2aim.PNG)

   ![Module3Chapter1step2bim](images/module3chapter1step2bim.PNG)
   
   3. <span data-ttu-id="710fd-122">Ein Textfeld mit der Bezeichnung, angezeigt werden. dadurch "read me."</span><span class="sxs-lookup"><span data-stu-id="710fd-122">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="710fd-123">Fahren Sie fort, und Lesen Sie sie.</span><span class="sxs-lookup"><span data-stu-id="710fd-123">Go ahead and read it.</span></span> <span data-ttu-id="710fd-124">Sobald Sie fertig sind, klicken Sie auf den Link neben "DownloadSDK", um sie herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="710fd-124">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module3Chapter1step3im](images/module3chapter1step3im.PNG)

4. <span data-ttu-id="710fd-126">Doppelklicken Sie den Ordner aus, nachdem der Download abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="710fd-126">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="710fd-127">Wenn Ihre Datei-Explorer geöffnet wird, den SDK-Ordner offenzulegen, kopieren Sie den SDK-Ordner.</span><span class="sxs-lookup"><span data-stu-id="710fd-127">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="710fd-128">Der nächste Schritt wäre in der Windows-Laufwerk "c:" wechseln, und erstellen einen neuen Ordner namens "Server".</span><span class="sxs-lookup"><span data-stu-id="710fd-128">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module3Chapter1step4aim](images/module3chapter1step4aim.PNG)
   
   - <span data-ttu-id="710fd-130">Jetzt öffnen Sie den Ordner, und fügen Sie den SDK-Ordner, die, den Sie zuvor kopiert haben.</span><span class="sxs-lookup"><span data-stu-id="710fd-130">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module3Chapter1step4bim](images/module3chapter1step4bim.PNG)
   
5. <span data-ttu-id="710fd-132">Sobald dies abgeschlossen ist, öffnen Sie den SDK-Ordner, und wechseln Sie zu ", klicken Sie dann"bin_Win64,"Bereitstellen" doppelklicken und klicken Sie dann auf "Photon-Steuerelement".</span><span class="sxs-lookup"><span data-stu-id="710fd-132">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module3Chapter1step5im](images/module3chapter1step5im.PNG)

> <span data-ttu-id="710fd-134">Hinweis: Wenn Sie Fragen zur IP-Adresse oder andere ähnlichen Fragen haben, finden die meisten Informationen auf der Symbolleiste Sie (wie in der folgenden Abbildung gezeigt).</span><span class="sxs-lookup"><span data-stu-id="710fd-134">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module3Chapter1noteim](images/module3chapter1noteim.PNG)

6. <span data-ttu-id="710fd-136">Nun, dass der Server eingerichtet und initiiert wird, wechseln Sie zurück zur Website Photon und stellen Sie sicher, dass Sie immer noch angemeldet sind (oder wieder anmelden, wenn Sie nicht sind.) Klicken Sie auf das Symbol "Profil" (geschachtelt in der oberen rechten Ecke von der Abbildung unten), und wählen Sie "Ihrer Anwendungen."</span><span class="sxs-lookup"><span data-stu-id="710fd-136">Now that the server is set up and initiated, go back to the Photon website and ensure that you are still signed in (or sign back in, if you are not.) Click on the profile icon (boxed in the top right corner of the image below) and select "your applications."</span></span>
   

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

7. <span data-ttu-id="710fd-138">Erstellen Sie eine Anwendungs-ID, indem Sie auf die Schaltfläche "erstellen eine neue app".</span><span class="sxs-lookup"><span data-stu-id="710fd-138">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

   - <span data-ttu-id="710fd-140">Wählen Sie "Photon WORTSPIEL" aus dem Dropdown-Menü unter "Photon geben."</span><span class="sxs-lookup"><span data-stu-id="710fd-140">Select "Photon PUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="710fd-141">Klicken Sie dann benennen Sie sie, in diesem Beispiel, das wir den Namen "HoloLensPhotonProject."</span><span class="sxs-lookup"><span data-stu-id="710fd-141">Then give it a name, in this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="710fd-142">Sobald Sie fertig sind, klicken Sie auf die Schaltfläche "Erstellen".</span><span class="sxs-lookup"><span data-stu-id="710fd-142">Once finished, click the "CREATE" button.</span></span>

   ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

8. <span data-ttu-id="710fd-144">Sobald das geschehen ist, kehren Sie zu Ihrer Seite "Anwendungen" zurück und sollte in etwa der folgenden Abbildung.</span><span class="sxs-lookup"><span data-stu-id="710fd-144">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="710fd-145">Klicken Sie auf die app-ID, und kopieren Sie ihn.</span><span class="sxs-lookup"><span data-stu-id="710fd-145">Click on the app ID and copy it.</span></span> <span data-ttu-id="710fd-146">Fügen Sie ist etwas, das Sie auf einfache Weise zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="710fd-146">Paste is somewhere you can easily access.</span></span>  
   

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

9. <span data-ttu-id="710fd-148">Erstellen eines neuen Unity-Projekts, und nennen Sie sie "HLSharingProject."</span><span class="sxs-lookup"><span data-stu-id="710fd-148">Create a new unity project and name it "HLSharingProject."</span></span> <span data-ttu-id="710fd-149">Anweisungen dazu, wie Sie ein neues Unity-Projekt erstellen, finden Sie unter [die Basis des Moduls "Unity-Projekt erstellen" im Abschnitt](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="710fd-149">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 


10. <span data-ttu-id="710fd-150">Nachdem das Projekt geladen wurde, klicken Sie auf auf der Registerkarte "Ressourcen-Store", wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="710fd-150">Once the project loads, click on the "assets store" tab, as shown in the image below.</span></span> <span data-ttu-id="710fd-151">Klicken Sie dann in das Suchfeld in der folgenden Abbildung hervorgehoben wird, geben Sie in "WORTSPIEL", und wählen Sie das "Photon WORTSPIEL-2-FREE"-Objekt in den Suchergebnissen.</span><span class="sxs-lookup"><span data-stu-id="710fd-151">Then, in the search box highlighted in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset from the search results.</span></span> 

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)
    
    11. <span data-ttu-id="710fd-153">Herunterladen Sie und importieren Sie dieses Medienobjekts durch Drücken die Schaltflächen "Herunterladen" und "Importieren".</span><span class="sxs-lookup"><span data-stu-id="710fd-153">Download and import this asset by pressing the "Download" and "Import" buttons.</span></span>
    
    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

## <a name="congratulations"></a><span data-ttu-id="710fd-155">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="710fd-155">Congratulations</span></span>

<span data-ttu-id="710fd-156">Sie haben erfolgreich Photon-Konto erstellt, einen lokalen Photon-Server einrichten und WORTSPIEL in Unity importiert.</span><span class="sxs-lookup"><span data-stu-id="710fd-156">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="710fd-157">Der nächste Schritt ist, richten Sie das Projekt, und lassen Sie Verbindungen mit anderen Benutzern, damit mehrere Benutzer Ihre Arbeit sehen können.</span><span class="sxs-lookup"><span data-stu-id="710fd-157">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="710fd-158">[Nächste Lektion: Sharing(Photon) Lektion 2](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="710fd-158">[Next Lesson: Sharing(Photon) Lesson 2](mrlearning-sharing(photon)-ch2.md)</span></span>

