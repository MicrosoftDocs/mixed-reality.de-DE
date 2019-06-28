---
title: Lernen die Freigabe-Modul für HoloLens 2 MR
description: Führen Sie diesen Kurs erfahren, wie Sie mehrere Benutzer freigegebene Umgebungen innerhalb einer HoloLens-2-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: f612fa89db1a3f5ed34f6e0bb7062b53780f09b8
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416121"
---
# <a name="setting-up-photon"></a><span data-ttu-id="55539-104">Einrichten von Photon</span><span class="sxs-lookup"><span data-stu-id="55539-104">Setting Up Photon</span></span>

<span data-ttu-id="55539-105">In dieser Lektion lernen wir, wie Sie für die Erstellung von einer gemeinsamen Erfahrung durch das Importieren von Photon Unity Networking (WORTSPIEL) in Ihrem Unity-Projekt vorzubereiten.</span><span class="sxs-lookup"><span data-stu-id="55539-105">In this lesson, we will learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="55539-106">Photon ist eine von mehreren Netzwerken Optionen Mixed Reality-Entwicklern zur Verfügung, freigegebene Anwendungen zu schaffen.</span><span class="sxs-lookup"><span data-stu-id="55539-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="55539-107">Es wird erfahren Sie, wie ein Photon-Konto erstellen, importieren Photon und erstellen einen optionalen lokalen Server</span><span class="sxs-lookup"><span data-stu-id="55539-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="55539-108">Ziele:</span><span class="sxs-lookup"><span data-stu-id="55539-108">Objectives:</span></span>

* <span data-ttu-id="55539-109">Erfahren Sie, wie Sie Photon-Konto erstellen</span><span class="sxs-lookup"><span data-stu-id="55539-109">Learn how to create Photon account</span></span>

* <span data-ttu-id="55539-110">Erfahren Sie, wie nach und importieren Sie Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="55539-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="55539-111">Einrichten eines lokalen Photon-Servers</span><span class="sxs-lookup"><span data-stu-id="55539-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="55539-112">Einrichten von Photon</span><span class="sxs-lookup"><span data-stu-id="55539-112">Setting Up Photon</span></span>

1. <span data-ttu-id="55539-113">Richten Sie eine [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) Konto.</span><span class="sxs-lookup"><span data-stu-id="55539-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="55539-114">Navigieren Sie durch Klicken auf der Registrierungsseite für Photon [diesen Link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="55539-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="55539-115">Befolgen Sie die Anweisungen auf der Registrierungsseite aus, um das Konto zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="55539-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="55539-118">Erstellen Sie eine Anwendungs-ID, indem Sie auf die Schaltfläche "erstellen eine neue app".</span><span class="sxs-lookup"><span data-stu-id="55539-118">Create an application ID by clicking the "create a new app" button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="55539-120">Wählen Sie "Photon WORTSPIEL" aus dem Dropdown-Menü unter "Photon geben."</span><span class="sxs-lookup"><span data-stu-id="55539-120">Select "Photon PUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="55539-121">Klicken Sie dann benennen Sie sie, in diesem Beispiel, das wir den Namen "HoloLensPhotonProject."</span><span class="sxs-lookup"><span data-stu-id="55539-121">Then give it a name, in this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="55539-122">Sobald Sie fertig sind, klicken Sie auf die Schaltfläche "Erstellen".</span><span class="sxs-lookup"><span data-stu-id="55539-122">Once finished, click the "CREATE" button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="55539-124">Sobald das geschehen ist, kehren Sie zu Ihrer Seite "Anwendungen" zurück und sollte in etwa der folgenden Abbildung.</span><span class="sxs-lookup"><span data-stu-id="55539-124">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="55539-125">Klicken Sie auf die app-ID, und kopieren Sie ihn.</span><span class="sxs-lookup"><span data-stu-id="55539-125">Click on the app ID and copy it.</span></span> <span data-ttu-id="55539-126">Fügen Sie ist etwas, das Sie auf einfache Weise zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="55539-126">Paste is somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="55539-128">Erstellen eines neuen Unity-Projekts, und nennen Sie sie "HLSharingProject."</span><span class="sxs-lookup"><span data-stu-id="55539-128">Create a new unity project and name it "HLSharingProject."</span></span> <span data-ttu-id="55539-129">Anweisungen dazu, wie Sie ein neues Unity-Projekt erstellen, finden Sie unter [die Basis des Moduls "Unity-Projekt erstellen" im Abschnitt](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="55539-129">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="55539-130">Nachdem das Projekt geladen wurde, klicken Sie auf auf der Registerkarte "Ressourcen-Store", wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="55539-130">Once the project loads, click on the "assets store" tab, as shown in the image below.</span></span> <span data-ttu-id="55539-131">Klicken Sie dann in das Suchfeld in der folgenden Abbildung hervorgehoben wird, geben Sie in "WORTSPIEL", und wählen Sie das Medienobjekt "Photon WORTSPIEL 2 – FREE", in den Suchergebnissen.</span><span class="sxs-lookup"><span data-stu-id="55539-131">Then, in the search box highlighted in the image below, type in "PUN" and select the "Photon PUN 2 - FREE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="55539-133">Herunterladen Sie und importieren Sie dieses Medienobjekts durch Drücken die Schaltflächen "Herunterladen" und "Importieren".</span><span class="sxs-lookup"><span data-stu-id="55539-133">Download and import this asset by pressing the "Download" and "Import" buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="55539-135">Sobald Photon der Importvorgang abgeschlossen ist, wird der Assistent Wortspiel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="55539-135">Once Photon has completed the importing process, the Pun Wizard will appear.</span></span> <span data-ttu-id="55539-136">Nutzen Sie die Anwendungs-ID (die in die Zwischenablage sein sollte), in Schritt 4, und fügen Sie ihn in das App-ID-Feld, und klicken Sie auf die Schaltfläche "Setup-Projekt".</span><span class="sxs-lookup"><span data-stu-id="55539-136">Take the application ID (which should be in your clipboard) from step 4 and paste it into the AppID box and press the "Setup Project" button.</span></span> 
<span data-ttu-id="55539-137">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="55539-137">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="55539-138">Nachdem die App-ID wurde erfolgreich hinzugefügt wurde, navigieren Sie zu "Photon"->"PhotonUnityNetworking" -> "Ressourcen" -> "PhotonServerSettings" im Bestand.</span><span class="sxs-lookup"><span data-stu-id="55539-138">After successfully adding the AppID, navigate to "Photon"->"PhotonUnityNetworking" -> "Resources" ->  "PhotonServerSettings" in Assets.</span></span> <span data-ttu-id="55539-139">Wählen Sie "Mit Name-Server"-Option aus, und legen Sie die festen Bereich auf "USA" oder Ihre Photon-Service-Region.</span><span class="sxs-lookup"><span data-stu-id="55539-139">Select "Use Name Server" option and set the fixed region to "us" or your photon service region.</span></span>

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="55539-141">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="55539-141">Congratulations</span></span>

<span data-ttu-id="55539-142">Sie haben erfolgreich Photon-Konto erstellt, einen lokalen Photon-Server einrichten und WORTSPIEL in Unity importiert.</span><span class="sxs-lookup"><span data-stu-id="55539-142">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="55539-143">Der nächste Schritt ist, richten Sie das Projekt, und lassen Sie Verbindungen mit anderen Benutzern, damit mehrere Benutzer Ihre Arbeit sehen können.</span><span class="sxs-lookup"><span data-stu-id="55539-143">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="55539-144">[Nächste Lektion: Sharing(Photon) Lektion 2](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="55539-144">[Next Lesson: Sharing(Photon) Lesson 2](mrlearning-sharing(photon)-ch2.md)</span></span>

