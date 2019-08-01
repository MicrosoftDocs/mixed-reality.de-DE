---
title: Lernprogramme für Mehrbenutzerfunktionen-1. Einrichten von Photon Unity-Netzwerken
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Umgebungen mit mehreren Benutzern in einer hololens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: acb6966ace81180e95e6a0fe447d350572f7c0dd
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701968"
---
#  <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="48a87-105">1. Einrichten von Photon Unity-Netzwerken</span><span class="sxs-lookup"><span data-stu-id="48a87-105">1. Setting up Photon Unity Networking</span></span>

<span data-ttu-id="48a87-106">In diesem Tutorial erfahren Sie, wie Sie sich für das Erstellen einer gemeinsamen Benutzeroberfläche vorbereiten, indem Sie das Photon Unity-Netzwerk (pun) in Ihr Unity-Projekt importieren.</span><span class="sxs-lookup"><span data-stu-id="48a87-106">In this tutorial, we learn how to get ready for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="48a87-107">Bei "Photon" handelt es sich um eine von mehreren Netzwerkoptionen, die für Mixed Reality-Entwickler zur Verfügung stehen</span><span class="sxs-lookup"><span data-stu-id="48a87-107">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="48a87-108">Wir erfahren, wie ein Photon-Konto erstellt, ein Photon importiert und ein optionaler lokaler Server erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="48a87-108">We we will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="48a87-109">Ziele</span><span class="sxs-lookup"><span data-stu-id="48a87-109">Objectives</span></span>

* <span data-ttu-id="48a87-110">Erfahren Sie, wie Sie ein Photon-Konto erstellen.</span><span class="sxs-lookup"><span data-stu-id="48a87-110">Learn how to create a Photon account</span></span>

* <span data-ttu-id="48a87-111">Erfahren Sie, wie Sie das Unity-Netzwerk von Photon suchen und importieren</span><span class="sxs-lookup"><span data-stu-id="48a87-111">Learn how to find and import Photon Unity Networking</span></span>

* <span data-ttu-id="48a87-112">Einrichten eines lokalen-Photon-Servers</span><span class="sxs-lookup"><span data-stu-id="48a87-112">Set up a local Photon server</span></span>

  

## <a name="setting-up-photon"></a><span data-ttu-id="48a87-113">Einrichten von PHOTON</span><span class="sxs-lookup"><span data-stu-id="48a87-113">Setting up Photon</span></span>

1. <span data-ttu-id="48a87-114">Richten Sie ein [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) -Konto ein.</span><span class="sxs-lookup"><span data-stu-id="48a87-114">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="48a87-115">Navigieren Sie zur Anmeldeseite von PHOTON, indem Sie auf [diesen Link](https://dashboard.photonengine.com/en-US/Account/SignUp)klicken.</span><span class="sxs-lookup"><span data-stu-id="48a87-115">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com/en-US/Account/SignUp).</span></span> <span data-ttu-id="48a87-116">Befolgen Sie die Anweisungen auf der Registrierungsseite, um das Konto zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="48a87-116">Follow the instructions on the sign-up page to create the account.</span></span> 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="48a87-119">Erstellen Sie eine Anwendungs-ID, indem Sie auf die Schaltfläche Neue APP erstellen klicken.</span><span class="sxs-lookup"><span data-stu-id="48a87-119">Create an application ID by clicking the Create a New App button.</span></span>

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="48a87-121">Wählen Sie im Dropdown Menü unter "Photon Type" den Typ "Photon" aus.</span><span class="sxs-lookup"><span data-stu-id="48a87-121">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="48a87-122">Benennen Sie dann den Namen.</span><span class="sxs-lookup"><span data-stu-id="48a87-122">Then give it a name.</span></span> <span data-ttu-id="48a87-123">In diesem Beispiel nennen wir es hololersphutonproject.</span><span class="sxs-lookup"><span data-stu-id="48a87-123">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="48a87-124">Klicken Sie anschließend auf die Schaltfläche erstellen.</span><span class="sxs-lookup"><span data-stu-id="48a87-124">Once finished, click the Create button.</span></span>

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="48a87-126">Sobald dies erfolgt ist, kehren Sie zur Seite "Anwendungen" zurück, und es sollte etwas ähnlich der folgenden Abbildung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="48a87-126">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="48a87-127">Klicken Sie auf die Anwendungs-ID, und kopieren Sie Sie.</span><span class="sxs-lookup"><span data-stu-id="48a87-127">Click on the application ID and copy it.</span></span> <span data-ttu-id="48a87-128">Fügen Sie Sie an einer beliebigen Stelle ein.</span><span class="sxs-lookup"><span data-stu-id="48a87-128">Paste it somewhere you can easily access.</span></span>  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="48a87-130">Erstellen Sie ein neues Unity-Projekt, und nennen Sie es hlsharingproject.</span><span class="sxs-lookup"><span data-stu-id="48a87-130">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="48a87-131">Anweisungen zum Erstellen eines neuen Unity-Projekts finden Sie [im Abschnitt "Erstellen eines Unity-Projekts" des Basismoduls](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="48a87-131">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="48a87-132">Nachdem das Projekt geladen wurde, klicken Sie auf die Registerkarte Ressourcen Speicher, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="48a87-132">Once the project loads, click on the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="48a87-133">Geben Sie dann im Suchfeld, das in der folgenden Abbildung hervorgehoben ist, das Wort "wortwort" ein, und wählen Sie in den Suchergebnissen das Objekt "Photon pun 2-Free" aus.</span><span class="sxs-lookup"><span data-stu-id="48a87-133">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span> 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="48a87-135">Sie können dieses Asset durch Drücken der Schaltflächen herunterladen und importieren herunterladen und importieren.</span><span class="sxs-lookup"><span data-stu-id="48a87-135">Download and import this asset by pressing the Download and Import buttons.</span></span>

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="48a87-137">Nachdem der Import Vorgang von Photon abgeschlossen wurde, wird der pun-Assistent angezeigt.</span><span class="sxs-lookup"><span data-stu-id="48a87-137">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="48a87-138">Verwenden Sie die Anwendungs-ID (die sich in der Zwischenablage befinden sollte) aus Schritt 4, und fügen Sie Sie in das Feld "AppID" ein, und klicken Sie auf die Schaltfläche Projekt einrichten.</span><span class="sxs-lookup"><span data-stu-id="48a87-138">Take the application ID (which should be in your clipboard) from step 4, and paste it into the AppID box, and press the Setup Project button.</span></span> 
<span data-ttu-id="48a87-139">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span><span class="sxs-lookup"><span data-stu-id="48a87-139">![module3chapter1step12im](images/module3chapter1step12im.PNG)</span></span>

9. <span data-ttu-id="48a87-140">Nachdem Sie die AppID erfolgreich hinzugefügt haben, navigieren Sie zu "Photon-> photonunitynetworking-> Resources->" photonserversettings "in" Assets ".</span><span class="sxs-lookup"><span data-stu-id="48a87-140">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="48a87-141">Wählen Sie die Option Namen Server verwenden aus, und legen Sie den Bereich für die festgelegte Region auf US oder Ihren Bereich für den Photonen Dienst</span><span class="sxs-lookup"><span data-stu-id="48a87-141">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="48a87-143">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="48a87-143">Congratulations</span></span>

<span data-ttu-id="48a87-144">Sie haben erfolgreich ein Photon-Konto erstellt, einen lokalen-Photon-Server eingerichtet und ein Wortspiel in Unity importiert.</span><span class="sxs-lookup"><span data-stu-id="48a87-144">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="48a87-145">Der nächste Schritt besteht darin, das Projekt einzurichten und dann Verbindungen mit anderen Benutzern zuzulassen, damit mehrere Benutzer ihre Arbeit sehen können.</span><span class="sxs-lookup"><span data-stu-id="48a87-145">Your next step is to set up the project and then allow connections with other users so that multiple users can see your work.</span></span> 

<span data-ttu-id="48a87-146">[Nächstes Tutorial: 2. Vorbereiten von Unity für die Entwicklung](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="48a87-146">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>

