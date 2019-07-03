---
title: Lernen die Freigabe-Modul für HoloLens 2 MR
description: Führen Sie diesen Kurs erfahren, wie Sie mehrere Benutzer freigegebene Umgebungen innerhalb einer HoloLens-2-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 80cefb36ec1944ec6f537aafcbf4b63f7f812d26
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523297"
---
#  <a name="setting-up-photon-unity-networking"></a><span data-ttu-id="a36a8-104">Photon Unity Netzwerk einrichten</span><span class="sxs-lookup"><span data-stu-id="a36a8-104">Setting up Photon Unity Networking</span></span>

<span data-ttu-id="a36a8-105">In diesem Tutorial erfahren wir, wie auf eine gemeinsame Erfahrung erstellen, durch den Import von Photon Unity Networking (WORTSPIEL) in Ihrem Unity-Projekt vorzubereiten.</span><span class="sxs-lookup"><span data-stu-id="a36a8-105">In this tutorial, we learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="a36a8-106">Photon ist eine von mehreren Netzwerken Optionen Mixed Reality-Entwicklern zur Verfügung, freigegebene Anwendungen zu schaffen.</span><span class="sxs-lookup"><span data-stu-id="a36a8-106">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="a36a8-107">Es wird erfahren Sie, wie ein Photon-Konto erstellen, importieren Photon und erstellen einen optionalen lokalen Server</span><span class="sxs-lookup"><span data-stu-id="a36a8-107">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

<span data-ttu-id="a36a8-108">Ziele:</span><span class="sxs-lookup"><span data-stu-id="a36a8-108">Objectives:</span></span>

* <span data-ttu-id="a36a8-109">Erfahren Sie, wie ein Photon-Konto erstellen</span><span class="sxs-lookup"><span data-stu-id="a36a8-109">Learn how to create a Photon account</span></span>

* <span data-ttu-id="a36a8-110">Erfahren Sie, wie nach und importieren Sie Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="a36a8-110">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="a36a8-111">Einrichten eines lokalen Photon-Servers</span><span class="sxs-lookup"><span data-stu-id="a36a8-111">Set up a local Photon server</span></span>

  

### <a name="setting-up-photon"></a><span data-ttu-id="a36a8-112">Einrichten von Photon</span><span class="sxs-lookup"><span data-stu-id="a36a8-112">Setting up Photon</span></span>

1. <span data-ttu-id="a36a8-113">Richten Sie eine [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) Konto.</span><span class="sxs-lookup"><span data-stu-id="a36a8-113">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="a36a8-114">Navigieren Sie durch Klicken auf der Registrierungsseite für Photon [diesen Link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span><span class="sxs-lookup"><span data-stu-id="a36a8-114">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="a36a8-115">Befolgen Sie die Anweisungen auf der Registrierungsseite aus, um das Konto zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="a36a8-115">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="a36a8-118">Erstellen Sie eine Anwendungs-ID durch Klicken auf das Erstellen einer neuen App-Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="a36a8-118">Create an application ID by clicking the Create a New App button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="a36a8-120">Wählen Sie aus dem Dropdownmenü unter Photon Photon WORTSPIEL.</span><span class="sxs-lookup"><span data-stu-id="a36a8-120">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="a36a8-121">Klicken Sie dann benennen Sie sie.</span><span class="sxs-lookup"><span data-stu-id="a36a8-121">Then give it a name.</span></span> <span data-ttu-id="a36a8-122">In diesem Beispiel den Namen wir HoloLensPhotonProject.</span><span class="sxs-lookup"><span data-stu-id="a36a8-122">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="a36a8-123">Sobald Sie fertig sind, klicken Sie auf die Schaltfläche "erstellen".</span><span class="sxs-lookup"><span data-stu-id="a36a8-123">Once finished, click the Create button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="a36a8-125">Sobald das geschehen ist, kehren Sie zu Ihrer Seite "Anwendungen" zurück und sollte in etwa der folgenden Abbildung.</span><span class="sxs-lookup"><span data-stu-id="a36a8-125">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="a36a8-126">Klicken Sie auf die Anwendungs-ID, und kopieren Sie ihn.</span><span class="sxs-lookup"><span data-stu-id="a36a8-126">Click on the application ID and copy it.</span></span> <span data-ttu-id="a36a8-127">Fügen Sie ist etwas, das Sie auf einfache Weise zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="a36a8-127">Paste is somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="a36a8-129">Erstellen eines neuen Unity-Projekts, und nennen Sie sie HLSharingProject aus.</span><span class="sxs-lookup"><span data-stu-id="a36a8-129">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="a36a8-130">Anweisungen dazu, wie Sie ein neues Unity-Projekt erstellen, finden Sie unter [die Basis des Moduls "Unity-Projekt erstellen" im Abschnitt](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="a36a8-130">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="a36a8-131">Nachdem das Projekt geladen wurde, klicken Sie auf der Registerkarte "Ressourcen-Store", wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="a36a8-131">Once the project loads, click on the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="a36a8-132">Klicken Sie dann in das Suchfeld in der folgenden Abbildung hervorgehoben wird, geben Sie in WORTSPIEL, und wählen die Photon WORTSPIEL-2 - FRE"Asset in den Suchergebnissen.</span><span class="sxs-lookup"><span data-stu-id="a36a8-132">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FRE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="a36a8-134">Herunterladen Sie und importieren Sie dieses Medienobjekts durch Drücken der Tasten herunterladen und importieren.</span><span class="sxs-lookup"><span data-stu-id="a36a8-134">Download and import this asset by pressing the Download and Import buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="a36a8-136">Sobald Photon der Importvorgang abgeschlossen ist, wird die Wortspiel-Assistent angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a36a8-136">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="a36a8-137">Nutzen Sie die Anwendungs-ID (die in die Zwischenablage sein sollte), in Schritt 4, und fügen Sie ihn in das App-ID-Feld aus, und drücken Sie die Schaltfläche "Setup-Projekt".</span><span class="sxs-lookup"><span data-stu-id="a36a8-137">Take the application ID (which should be in your clipboard) from step 4, and paste it into the AppID box, and press the Setup Project button.</span></span> 
<span data-ttu-id="a36a8-138">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="a36a8-138">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="a36a8-139">Nachdem die App-ID wurde erfolgreich hinzugefügt wurde, navigieren Sie zu Photon PhotonUnityNetworking -> -> Ressourcen -> PhotonServerSettings in Objekte.</span><span class="sxs-lookup"><span data-stu-id="a36a8-139">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="a36a8-140">Wählen Sie die Namenserver für die Verwendung-Option aus, und legen Sie die festen Bereich an uns oder YourPphoton-Service-Region.</span><span class="sxs-lookup"><span data-stu-id="a36a8-140">Select the Use Name Server option, and set the fixed region to US or yourPphoton service region.</span></span>

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="a36a8-142">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="a36a8-142">Congratulations</span></span>

<span data-ttu-id="a36a8-143">Sie haben erfolgreich Photon-Konto erstellt, einen lokalen Photon-Server einrichten und WORTSPIEL in Unity importiert.</span><span class="sxs-lookup"><span data-stu-id="a36a8-143">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="a36a8-144">Der nächste Schritt ist, richten Sie das Projekt, und lassen Sie Verbindungen mit anderen Benutzern, damit mehrere Benutzer Ihre Arbeit sehen können.</span><span class="sxs-lookup"><span data-stu-id="a36a8-144">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="a36a8-145">[Nächsten Lernprogramm: Vorbereitung von Unity für die Entwicklung](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="a36a8-145">[Next tutorial: Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>

