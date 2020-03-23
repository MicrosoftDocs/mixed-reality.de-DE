---
title: 'Tutorials zu Mehrbenutzerfunktionen: 1 Einrichten von Photon Unity Networking'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 94068ff706e0e56ca8ec0f23beaed3a34159b777
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031330"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="ee907-105">1. Einrichten von Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="ee907-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="ee907-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="ee907-106">Overview</span></span>

<span data-ttu-id="ee907-107">In diesem Tutorial erfahren Sie, wie Sie sich auf das Erstellen einer gemeinsamen Benutzeroberfläche vorbereiten, indem Sie das Photon Unity-Netzwerk (PUN) in Ihr Unity-Projekt importieren.</span><span class="sxs-lookup"><span data-stu-id="ee907-107">In this tutorial, you will learn how to prepare for creating a shared experience by importing Photon Unity Networking (PUN) into your Unity project.</span></span> <span data-ttu-id="ee907-108">Photon ist eine von mehreren Netzwerkoptionen, die Mixed Reality-Entwicklern zum Erstellen gemeinsamer Benutzererfahrungen zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="ee907-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="ee907-109">Sie erfahren, wie Sie ein Photon-Konto erstellen, Photon importieren und einen optionalen lokalen Server erstellen.</span><span class="sxs-lookup"><span data-stu-id="ee907-109">You will learn how to create a Photon account, import Photon, and create an optional local server</span></span>

## <a name="objectives"></a><span data-ttu-id="ee907-110">Ziele</span><span class="sxs-lookup"><span data-stu-id="ee907-110">Objectives</span></span>

* <span data-ttu-id="ee907-111">Erlernen des Erstellens eines Photon-Kontos</span><span class="sxs-lookup"><span data-stu-id="ee907-111">Learn how to create a Photon account</span></span>
* <span data-ttu-id="ee907-112">Erfahren, wie Photon Unity Networking gesucht und importiert wird</span><span class="sxs-lookup"><span data-stu-id="ee907-112">Learn how to find and import Photon Unity Networking</span></span>
* <span data-ttu-id="ee907-113">Einrichten eines lokalen Photon-Servers</span><span class="sxs-lookup"><span data-stu-id="ee907-113">Set up a local Photon server</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ee907-114">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="ee907-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="ee907-115">Wenn Sie die Tutorialreihen [Tutorials zu den ersten Schritten](mrlearning-base.md) und [Einstieg in Azure Spatial Anchors](mrlearning-asa-ch1.md) noch nicht abgeschlossen haben, empfiehlt es sich, zunächst diese Tutorials abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="ee907-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) and [Azure Spatial Anchors started tutorials](mrlearning-asa-ch1.md) tutorial series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="ee907-116">Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](install-the-tools.md) ist</span><span class="sxs-lookup"><span data-stu-id="ee907-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="ee907-117">Windows 10 SDK (10.0.18362.0 oder höher)</span><span class="sxs-lookup"><span data-stu-id="ee907-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="ee907-118">Grundlagenkenntnisse in der C#-Programmierung</span><span class="sxs-lookup"><span data-stu-id="ee907-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="ee907-119">Ein für die [Entwicklung konfiguriertes](using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät</span><span class="sxs-lookup"><span data-stu-id="ee907-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>

>[!IMPORTANT]
> <span data-ttu-id="ee907-120">Die empfohlene Unity-Version für diese Tutorialreihe ist Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="ee907-120">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="ee907-121">Diese übertrifft alle Versionsanforderungen oder -empfehlungen, die in den oben verlinkten Voraussetzungen angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="ee907-121">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="setting-up-photon"></a><span data-ttu-id="ee907-122">Einrichten von Photon</span><span class="sxs-lookup"><span data-stu-id="ee907-122">Setting up Photon</span></span>

1. <span data-ttu-id="ee907-123">Richten Sie ein [Photon](https://dashboard.photonengine.com//Account/SignUp)-Konto ein.</span><span class="sxs-lookup"><span data-stu-id="ee907-123">Set up a [Photon](https://dashboard.photonengine.com//Account/SignUp) account.</span></span> <span data-ttu-id="ee907-124">Navigieren Sie über [diesen Link](https://dashboard.photonengine.com//Account/SignUp) zur Registrierungsseite von Photon.</span><span class="sxs-lookup"><span data-stu-id="ee907-124">Navigate to the Photon Sign-up page by clicking on [this link](https://dashboard.photonengine.com//Account/SignUp).</span></span> <span data-ttu-id="ee907-125">Befolgen Sie die Anweisungen auf der Registrierungsseite, um das Konto zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ee907-125">Follow the instructions on the sign-up page to create the account.</span></span>

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. <span data-ttu-id="ee907-128">Erstellen Sie eine Anwendungs-ID, indem Sie auf die Schaltfläche „Create a New App“ (Neue App erstellen) klicken.</span><span class="sxs-lookup"><span data-stu-id="ee907-128">Create an application ID by clicking the Create a New App button.</span></span>

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. <span data-ttu-id="ee907-130">Wählen Sie im Dropdownmenü unter „Photon Type“ das Element „Photon PUN“ aus.</span><span class="sxs-lookup"><span data-stu-id="ee907-130">Select Photon PUN from the dropdown menu under Photon Type.</span></span> <span data-ttu-id="ee907-131">Geben Sie ihm dann einen Namen.</span><span class="sxs-lookup"><span data-stu-id="ee907-131">Then give it a name.</span></span> <span data-ttu-id="ee907-132">In diesem Beispiel haben wir es „HoloLensPhotonProject“ benannt.</span><span class="sxs-lookup"><span data-stu-id="ee907-132">In this example, we named it HoloLensPhotonProject.</span></span> <span data-ttu-id="ee907-133">Wenn Sie damit fertig sind, klicken Sie auf die Erstellen-Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="ee907-133">Once finished, click the Create button.</span></span>

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. <span data-ttu-id="ee907-135">Wenn Sie zu Ihrer Anwendungsseite zurückkehren, sollten Sie etwas ähnlich der Abbildung unten sehen.</span><span class="sxs-lookup"><span data-stu-id="ee907-135">Return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="ee907-136">Klicken Sie auf die Anwendungs-ID, und kopieren Sie sie.</span><span class="sxs-lookup"><span data-stu-id="ee907-136">Click the application ID and copy it.</span></span> <span data-ttu-id="ee907-137">Fügen Sie sie an einem beliebigen Ort ein, auf den Sie leicht zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="ee907-137">Paste it somewhere you can easily access.</span></span>  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. <span data-ttu-id="ee907-139">Erstellen Sie ein neues Unity-Projekt, und benennen Sie es HLSharingProject.</span><span class="sxs-lookup"><span data-stu-id="ee907-139">Create a new unity project and name it HLSharingProject.</span></span> <span data-ttu-id="ee907-140">Anweisungen zum Erstellen eines neuen Unity-Projekts finden Sie im [Abschnitt „Unity-Projekt erstellen“ des Basismoduls](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span><span class="sxs-lookup"><span data-stu-id="ee907-140">For instructions on how to create a new Unity project, please refer to [the Base Module's "Create Unity Project" section](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project).</span></span> 

6. <span data-ttu-id="ee907-141">Nachdem das Projekt geladen wurde, klicken Sie auf die Registerkarte „Assets Store“, wie in der Abbildung unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="ee907-141">Once the project loads, click the Assets Store tab, as shown in the image below.</span></span> <span data-ttu-id="ee907-142">Geben Sie dann im Suchfeld, das in der Abbildung unten hervorgehoben ist, „PUN“ ein, und wählen Sie in den Suchergebnissen die Ressource „Photon PUN 2 - FREE“ aus.</span><span class="sxs-lookup"><span data-stu-id="ee907-142">Then, in the search box highlighted in the image below, type in PUN, and select the Photon PUN 2 - FREE" asset from the search results.</span></span>

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. <span data-ttu-id="ee907-144">Sie können diese Ressource durch Drücken der Schaltflächen „Herunterladen“ und „Importieren“ herunterladen und importieren.</span><span class="sxs-lookup"><span data-stu-id="ee907-144">Download and import this asset by pressing the Download and Import buttons.</span></span>

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. <span data-ttu-id="ee907-146">Nachdem Photon den Importvorgang abgeschlossen hat, wird der PUN-Assistent angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ee907-146">Once Photon has completed the importing process, the Pun Wizard appears.</span></span> <span data-ttu-id="ee907-147">Nehmen Sie die Anwendungs-ID aus Schritt 4 (die sich in Ihrer Zwischenablage befinden sollte), fügen Sie sie in das AppID-Feld ein, und drücken Sie die Schaltfläche „Setup Project“ (Projekt einrichten).</span><span class="sxs-lookup"><span data-stu-id="ee907-147">Take the application ID (which should be in your clipboard) from step 4, paste it into the AppID box, and press the Setup Project button.</span></span>

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. <span data-ttu-id="ee907-149">Nach erfolgreichem Hinzufügen der AppID navigieren Sie in „Assets“ zu „Photon > PhotonUnityNetworking > Resources > PhotonServerSettings“.</span><span class="sxs-lookup"><span data-stu-id="ee907-149">After successfully adding the AppID, navigate to Photon->PhotonUnityNetworking ->Resources->PhotonServerSettings in Assets.</span></span> <span data-ttu-id="ee907-150">Wählen Sie die Option „Use Name Server“ (Namensserver verwenden) aus, und legen Sie die feste Region auf US oder auf die Region Ihres Photon-Diensts fest.</span><span class="sxs-lookup"><span data-stu-id="ee907-150">Select the Use Name Server option, and set the fixed region to US or your photon service region.</span></span>

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a><span data-ttu-id="ee907-152">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="ee907-152">Congratulations</span></span>

<span data-ttu-id="ee907-153">Sie haben erfolgreich ein Photon-Konto erstellt, einen lokalen Photon-Server eingerichtet und PUN in Unity importiert.</span><span class="sxs-lookup"><span data-stu-id="ee907-153">You have successfully created a Photon account, set up a local Photon server, and imported PUN into Unity.</span></span> <span data-ttu-id="ee907-154">Der nächste Schritt besteht darin, das Projekt einzurichten und Verbindungen mit anderen Benutzern zuzulassen, damit mehrere Benutzer Ihre Arbeit sehen können.</span><span class="sxs-lookup"><span data-stu-id="ee907-154">Your next step is to set up the project and allow connections with other users so that multiple users can see your work.</span></span>

<span data-ttu-id="ee907-155">[Nächstes Tutorial: 2. Vorbereiten von Unity für die Entwicklung](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="ee907-155">[Next tutorial: 2. Getting Unity ready for development](mrlearning-sharing(photon)-ch2.md)</span></span>
