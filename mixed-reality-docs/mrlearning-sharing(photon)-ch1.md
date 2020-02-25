---
title: Lernprogramme für Mehrbenutzerfunktionen-1. Einrichten von Photon Unity-Netzwerken
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Umgebungen mit mehreren Benutzern in einer hololens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: d879144c7097d8b3873618f986b9f169e8553fa8
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553818"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="0ce0f-105">1. Einrichten der Einrichtung von Photon Unity-Netzwerken</span><span class="sxs-lookup"><span data-stu-id="0ce0f-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="0ce0f-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="0ce0f-106">Overview</span></span>

<span data-ttu-id="0ce0f-107">In diesem Tutorial erfahren Sie, wie Sie sich auf das Erstellen einer gemeinsamen Benutzeroberfläche vorbereiten, indem Sie das Photon Unity-Netzwerk (pun) in Ihr Unity-Projekt importieren.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-107">In this tutorial, you will learn how to prepare for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="0ce0f-108">Bei "Photon" handelt es sich um eine von mehreren Netzwerkoptionen, die für Mixed Reality-Entwickler zur Verfügung stehen</span><span class="sxs-lookup"><span data-stu-id="0ce0f-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="0ce0f-109">Sie erfahren, wie Sie ein Photon-Konto erstellen, ein Photon importieren und einen optionalen lokalen Server erstellen.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-109">You will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="0ce0f-110">Ziele</span><span class="sxs-lookup"><span data-stu-id="0ce0f-110">Objectives</span></span>

* <span data-ttu-id="0ce0f-111">Erfahren Sie, wie Sie ein Photon-Konto erstellen.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-111">Learn how to create a Photon account</span></span>
* <span data-ttu-id="0ce0f-112">Erfahren Sie, wie Sie das Unity-Netzwerk von Photon suchen und importieren</span><span class="sxs-lookup"><span data-stu-id="0ce0f-112">Learn how to find and import Photon Unity Networking</span></span>
* <span data-ttu-id="0ce0f-113">Einrichten eines lokalen-Photon-Servers</span><span class="sxs-lookup"><span data-stu-id="0ce0f-113">Set up a local Photon server</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0ce0f-114">Erforderliche Komponenten</span><span class="sxs-lookup"><span data-stu-id="0ce0f-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="0ce0f-115">Wenn Sie die Lernprogramme "erste Schritte" und " [Azure Spatial](mrlearning-asa-ch1.md) Anchor" noch nicht abgeschlossen haben, empfiehlt es sich, [diese Tutorials zuerst](mrlearning-base.md) abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) and [Azure Spatial Anchors started tutorials](mrlearning-asa-ch1.md) tutorial series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="0ce0f-116">Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](install-the-tools.md) ist</span><span class="sxs-lookup"><span data-stu-id="0ce0f-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="0ce0f-117">Windows 10 SDK (10.0.18362.0 oder höher)</span><span class="sxs-lookup"><span data-stu-id="0ce0f-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="0ce0f-118">Grundlagenkenntnisse in der C#-Programmierung</span><span class="sxs-lookup"><span data-stu-id="0ce0f-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="0ce0f-119">Ein für die [Entwicklung konfiguriertes](using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät</span><span class="sxs-lookup"><span data-stu-id="0ce0f-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="0ce0f-120">Die empfohlene Unity-Version für diese Tutorialreihe ist Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-120">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="0ce0f-121">Diese übertrifft alle Versionsanforderungen oder -empfehlungen, die in den oben verlinkten Voraussetzungen angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-121">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="setting-up-photon"></a><span data-ttu-id="0ce0f-122">Einrichten von PHOTON</span><span class="sxs-lookup"><span data-stu-id="0ce0f-122">Setting up Photon</span></span>

1. <span data-ttu-id="0ce0f-123">Richten Sie ein [Photon](https://dashboard.photonengine.com//Account/SignUp) -Konto ein.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-123">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="0ce0f-124">Navigieren Sie zur Anmeldeseite von PHOTON, indem Sie auf [diesen Link](https://dashboard.photonengine.com//Account/SignUp)klicken.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-124">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com//Account/SignUp).</span></span> <span data-ttu-id="0ce0f-125">Befolgen Sie die Anweisungen auf der Registrierungsseite, um das Konto zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-125">Follow the instructions on the sign-up page to create the account.</span></span>

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="0ce0f-128">Erstellen Sie eine Anwendungs-ID, indem Sie auf die Schaltfläche Neue APP erstellen klicken.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-128">Create an application ID by clicking the Create a New App button.</span></span>

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="0ce0f-130">Wählen Sie im Dropdown Menü unter "Photon Type" den Typ "Photon" aus.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-130">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="0ce0f-131">Benennen Sie dann den Namen.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-131">Then give it a name.</span></span> <span data-ttu-id="0ce0f-132">In diesem Beispiel nennen wir es hololersphutonproject.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-132">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="0ce0f-133">Klicken Sie anschließend auf die Schaltfläche erstellen.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-133">Once finished, click the Create button.</span></span>

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="0ce0f-135">Kehren Sie zur Seite "Anwendungen" zurück, und es sollte etwas ähnlich der folgenden Abbildung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-135">Return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="0ce0f-136">Klicken Sie auf die Anwendungs-ID und kopieren Sie Sie.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-136">Click the application ID and copy it.</span></span> <span data-ttu-id="0ce0f-137">Fügen Sie Sie an einer beliebigen Stelle ein.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-137">Paste it somewhere you can easily access.</span></span>  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="0ce0f-139">Erstellen Sie ein neues Unity-Projekt, und nennen Sie es hlsharingproject.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-139">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="0ce0f-140">Anweisungen zum Erstellen eines neuen Unity-Projekts finden Sie [im Abschnitt "Erstellen eines Unity-Projekts" des Basismoduls](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="0ce0f-140">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="0ce0f-141">Nachdem das Projekt geladen wurde, klicken Sie auf die Registerkarte Ressourcen Speicher, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-141">Once the project loads, click the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="0ce0f-142">Geben Sie dann im Suchfeld, das in der folgenden Abbildung hervorgehoben ist, das Wort "wortwort" ein, und wählen Sie in den Suchergebnissen das Objekt "Photon pun 2-Free" aus.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-142">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span>

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="0ce0f-144">Sie können dieses Asset durch Drücken der Schaltflächen herunterladen und importieren herunterladen und importieren.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-144">Download and import this asset by pressing the Download and Import buttons.</span></span>

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="0ce0f-146">Nachdem der Import Vorgang von Photon abgeschlossen wurde, wird der pun-Assistent angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-146">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="0ce0f-147">Verwenden Sie die Anwendungs-ID (die sich in der Zwischenablage befinden sollte) aus Schritt 4, fügen Sie Sie in das Feld AppID ein, und klicken Sie auf die Schaltfläche Projekt einrichten.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-147">Take the application ID (which should be in your clipboard) from step 4, paste it into the AppID box, and press the Setup Project button.</span></span>

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. <span data-ttu-id="0ce0f-149">Nachdem Sie die AppID erfolgreich hinzugefügt haben, navigieren Sie zu "Photon-> photonunitynetworking-> Resources->" photonserversettings "in" Assets ".</span><span class="sxs-lookup"><span data-stu-id="0ce0f-149">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="0ce0f-150">Wählen Sie die Option Namen Server verwenden aus, und legen Sie den Bereich für die festgelegte Region auf US oder Ihren Bereich für den Photonen Dienst</span><span class="sxs-lookup"><span data-stu-id="0ce0f-150">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="0ce0f-152">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="0ce0f-152">Congratulations</span></span>

<span data-ttu-id="0ce0f-153">Sie haben erfolgreich ein Photon-Konto erstellt, einen lokalen-Photon-Server eingerichtet und ein Wortspiel in Unity importiert.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-153">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="0ce0f-154">Der nächste Schritt besteht darin, das Projekt einzurichten und Verbindungen mit anderen Benutzern zuzulassen, damit mehrere Benutzer ihre Arbeit sehen können.</span><span class="sxs-lookup"><span data-stu-id="0ce0f-154">Your next step is to set up the project and allow connections with other users so that multiple users can see your work.</span></span>

<span data-ttu-id="0ce0f-155">[Nächstes Tutorial: 2. Vorbereiten von Unity für die Entwicklung](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="0ce0f-155">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>
