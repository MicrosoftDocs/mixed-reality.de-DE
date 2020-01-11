---
title: Lernprogramme für Mehrbenutzerfunktionen-2. Vorbereiten von Unity für die Entwicklung
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Umgebungen mit mehreren Benutzern in einer hololens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 6abf4fa8fc87afc7007d6f7c76becfbd88ed7a12
ms.sourcegitcommit: 2bfe9b1af4ee2cc0d668caeccb8ebc3137cbc20b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901522"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="9adbc-105">2. Vorbereiten von Unity für die Entwicklung</span><span class="sxs-lookup"><span data-stu-id="9adbc-105">2. Getting Unity ready for development</span></span>

<span data-ttu-id="9adbc-106">In diesem Tutorial erfahren Sie, wie Sie Unity für die Anwendungsentwicklung vorbereiten und konfigurieren, einschließlich Importieren des Mixed Reality Toolkit, Konfigurieren von Buildeinstellungen und Vorbereiten der Szene.</span><span class="sxs-lookup"><span data-stu-id="9adbc-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="9adbc-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="9adbc-107">Objectives</span></span>

* <span data-ttu-id="9adbc-108">Konfigurieren von Unity für die Anwendungsentwicklung</span><span class="sxs-lookup"><span data-stu-id="9adbc-108">Configure Unity for application development</span></span>
* <span data-ttu-id="9adbc-109">Importieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="9adbc-109">Import the Mixed Reality Toolkit</span></span>
* <span data-ttu-id="9adbc-110">Vorbereiten der Projekt Szene</span><span class="sxs-lookup"><span data-stu-id="9adbc-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="9adbc-111">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="9adbc-111">Instructions</span></span>

1. <span data-ttu-id="9adbc-112">Klicken Sie hier, um das Mixed Reality Toolkit Foundation-Unity-Paket herunterzuladen und zu speichern [.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="9adbc-112">Download and save the Mixed Reality Toolkit Foundation unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span></span>

2. <span data-ttu-id="9adbc-113">Klicken Sie in Unity auf das Menü Assets, wählen Sie Paket importieren aus, und klicken Sie dann auf benutzerdefiniertes Paket.</span><span class="sxs-lookup"><span data-stu-id="9adbc-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="9adbc-115">Wählen Sie das Unity-Paket aus, das Sie soeben aus dem in Schritt 1 angegebenen Link heruntergeladen haben.</span><span class="sxs-lookup"><span data-stu-id="9adbc-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="9adbc-116">Nachdem das Popup Fenster Importieren in Unity angezeigt wird, klicken Sie auf die Schaltfläche Importieren, um mit dem Importieren von mrtk zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="9adbc-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="9adbc-117">Dieser Vorgang kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="9adbc-117">This may take several minutes.</span></span>

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="9adbc-119">Das heruntergeladene Paket befindet sich in Ihrem lokalen Ordner, in dem Sie die Datei gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="9adbc-119">The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="9adbc-120">In der Abbildung oben wird nicht dargestellt, wo Sie das Paket finden.</span><span class="sxs-lookup"><span data-stu-id="9adbc-120">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="9adbc-121">Erstellen Sie eine neue Szene.</span><span class="sxs-lookup"><span data-stu-id="9adbc-121">Create a new scene.</span></span> <span data-ttu-id="9adbc-122">Klicken Sie hierzu auf Datei, und wählen Sie neue Szene aus.</span><span class="sxs-lookup"><span data-stu-id="9adbc-122">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="9adbc-123">Speichern Sie Sie als hlsharedprojectmain.</span><span class="sxs-lookup"><span data-stu-id="9adbc-123">Save it as HLSharedProjectMain.</span></span>

    <span data-ttu-id="9adbc-124">Möglicherweise wird ein Popup Fenster angezeigt, das ähnlich wie in der folgenden Abbildung aussieht.</span><span class="sxs-lookup"><span data-stu-id="9adbc-124">You may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="9adbc-125">Klicken Sie vorerst auf Nein.</span><span class="sxs-lookup"><span data-stu-id="9adbc-125">For now, click No.</span></span>
    <span data-ttu-id="9adbc-126">![Module3Chapter2note1im](images/module3chapter2note1im.PNG)</span><span class="sxs-lookup"><span data-stu-id="9adbc-126">![Module3Chapter2note1im](images/module3chapter2note1im.PNG)</span></span>

5. <span data-ttu-id="9adbc-127">Klicken Sie unter Mixed Reality Toolkit auf zur Szene hinzufügen und konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="9adbc-127">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="9adbc-129">Sobald der Vorgang beendet ist, wird eine neue Konfigurationsdatei angezeigt, die Ihnen die Möglichkeit gibt, das Profil anzupassen.</span><span class="sxs-lookup"><span data-stu-id="9adbc-129">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span>

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima.PNG)

7. <span data-ttu-id="9adbc-131">Wählen Sie in der Hierarchie Mixed-Reality Toolkit (mrtk) aus.</span><span class="sxs-lookup"><span data-stu-id="9adbc-131">Select Mixed-Reality Toolkit (MRTK) from the  hierarchy.</span></span> <span data-ttu-id="9adbc-132">Suchen Sie im Inspektor-Panel nach dem Mixed Reality Toolkit-Skript, und klicken Sie auf die Schaltfläche zum Kopieren & anpassen, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="9adbc-132">In the inspector panel, look for the Mixed Reality Toolkit Script and press the "Copy & Customize" button  as shown in the figure below.</span></span>  <span data-ttu-id="9adbc-133">Danach wird ein Pop angezeigt, und wählen Sie im Popupmenü die Option Klonen aus.</span><span class="sxs-lookup"><span data-stu-id="9adbc-133">A pop will appear after this and select clone option in the pop up menu.</span></span>

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. <span data-ttu-id="9adbc-136">Scrollen Sie nach unten, und deaktivieren Sie Diagnosesystem aktivieren, wenn Sie das Diagnosefenster ausblenden möchten.</span><span class="sxs-lookup"><span data-stu-id="9adbc-136">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="9adbc-137">Es wird empfohlen, das Diagnosefenster während der Anwendungsentwicklung zu aktivieren, um die Leistung zu überwachen und es dann während der Produktions-oder Anwendungs Demos zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="9adbc-137">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. <span data-ttu-id="9adbc-139">Öffnen Sie die Buildeinstellungen, indem Sie STRG + UMSCHALT + B drücken, oder wechseln Sie zu Datei > Buildeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="9adbc-139">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="9adbc-140">Beachten Sie, dass das Programm derzeit unter der eigenständigen PC-, Mac-und Linux-Plattform festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="9adbc-140">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="9adbc-141">Legen Sie für die Entwicklung von hololens 2 die Plattform auf universelle Windows-Plattform fest.</span><span class="sxs-lookup"><span data-stu-id="9adbc-141">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="9adbc-142">Wählen Sie es aus, und klicken Sie auf Plattform wechseln.</span><span class="sxs-lookup"><span data-stu-id="9adbc-142">Select it and click Switch Platform.</span></span>

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. <span data-ttu-id="9adbc-144">Klicken Sie nach Abschluss des Vorgangs auf das Feld mit dem Namen offene Szenen hinzufügen</span><span class="sxs-lookup"><span data-stu-id="9adbc-144">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="9adbc-145">Wechseln Sie nun zum Inspektor-Panel, und stellen Sie sicher, dass das Kontrollkästchen rechts von Virtual Reality unterstützt wird (wie in der folgenden Abbildung dargestellt).</span><span class="sxs-lookup"><span data-stu-id="9adbc-145">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="9adbc-146">Stellen Sie außerdem sicher, dass das Kontrollkästchen nebenszenen/hlsharedprojectmain ebenfalls aktiviert ist, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="9adbc-146">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. <span data-ttu-id="9adbc-148">Scrollen Sie im Bereich Inspector im Bereich Veröffentlichungs Einstellungen nach unten zu Funktionen, und stellen Sie sicher, dass die folgenden Kontrollkästchen markiert sind:</span><span class="sxs-lookup"><span data-stu-id="9adbc-148">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. <span data-ttu-id="9adbc-150">Importieren Sie die aufgelisteten benutzerdefinierten Pakete:</span><span class="sxs-lookup"><span data-stu-id="9adbc-150">Import the listed custom packages:</span></span>

    <span data-ttu-id="9adbc-151">ein.</span><span class="sxs-lookup"><span data-stu-id="9adbc-151">a.</span></span> <span data-ttu-id="9adbc-152">[Azurespatialanchor. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (Version 2.0.0)</span><span class="sxs-lookup"><span data-stu-id="9adbc-152">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (version 2.0.0)</span></span>

    <span data-ttu-id="9adbc-153">b.</span><span class="sxs-lookup"><span data-stu-id="9adbc-153">b.</span></span> [<span data-ttu-id="9adbc-154">Mrtk. HoloLens2. Unity. Tutorials. Assets. GettingStarted. 2.1.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="9adbc-154">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)

    <span data-ttu-id="9adbc-155">c.</span><span class="sxs-lookup"><span data-stu-id="9adbc-155">c.</span></span> [<span data-ttu-id="9adbc-156">Mrtk. HoloLens2. Unity. Tutorials. Assets. azurespatialanchor. 2.1.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="9adbc-156">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

    <span data-ttu-id="9adbc-157">d.</span><span class="sxs-lookup"><span data-stu-id="9adbc-157">d.</span></span> [<span data-ttu-id="9adbc-158">Mrtk. HoloLens2. Unity. Tutorials. Assets. multiuserfunktionalitäten. 2.1.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="9adbc-158">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    ><span data-ttu-id="9adbc-159">Eine Erinnerung zum Konfigurieren eines Unity-Projekts für räumliche Azure-Anker finden Sie im Tutorial zu den ersten Schritten [mit Azure Spatial](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) Anchor, das Teil der tutorialreihe für [räumliche Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) -Anker ist.</span><span class="sxs-lookup"><span data-stu-id="9adbc-159">For a reminder on how to configure a Unity project for Azure Spatial Anchors, you can refer to the [Getting started with Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial which is part of the the [Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial series.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

13. <span data-ttu-id="9adbc-161">Wechseln Sie im Projekt Panel zum Ordner Prefabs.</span><span class="sxs-lookup"><span data-stu-id="9adbc-161">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="9adbc-162">In den folgenden Schritten implementieren Sie einige Prefabs in der Szene.</span><span class="sxs-lookup"><span data-stu-id="9adbc-162">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="9adbc-163">Klicken Sie im Ordner Prefabs auf das Fenster Prefab, Debug, und ziehen Sie es in die Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="9adbc-163">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="9adbc-164">Wenn Sie fertig sind, speichern Sie das Projekt, indem Sie auf Datei und dann auf Speichern klicken oder STRG + S drücken.</span><span class="sxs-lookup"><span data-stu-id="9adbc-164">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    <span data-ttu-id="9adbc-166">Sie werden möglicherweise feststellen, dass ein Popup Fenster angezeigt wird, wenn Sie auf die vorfab klicken und Sie zu tmp Essentials auffordern.</span><span class="sxs-lookup"><span data-stu-id="9adbc-166">You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="9adbc-167">Klicken Sie auf tmp Essentials nach Bedarf importieren.</span><span class="sxs-lookup"><span data-stu-id="9adbc-167">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="9adbc-168">Wenn dieses Popup Fenster angezeigt wird, müssen Sie möglicherweise die vorfab aus Ihrer Hierarchie löschen und in ihre Hierarchie ziehen, um potenzielle Text bezogene Fehler zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="9adbc-168">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="9adbc-170">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="9adbc-170">Congratulations</span></span>

<span data-ttu-id="9adbc-171">Ihr Unity-Projekt ist nun für das Photon bereit.</span><span class="sxs-lookup"><span data-stu-id="9adbc-171">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="9adbc-172">In den nächsten Tutorials bauen wir auf dieser Szene und unserem Unity-Projekt auf, um eine vollständige gemeinsame Nutzung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="9adbc-172">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="9adbc-173">[Nächstes Tutorial: 3. Verbinden von mehreren Benutzern](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="9adbc-173">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>
