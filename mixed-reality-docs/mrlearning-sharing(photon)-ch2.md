---
title: Lernprogramme für Mehrbenutzerfunktionen-2. Vorbereiten von Unity für die Entwicklung
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Umgebungen mit mehreren Benutzern in einer hololens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 6840bcc583fe3e42dcaa6f42e71098f4dbe76f4c
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334312"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="1a050-105">2. Vorbereiten von Unity für die Entwicklung</span><span class="sxs-lookup"><span data-stu-id="1a050-105">2. Getting Unity ready for development</span></span>

<span data-ttu-id="1a050-106">In diesem Tutorial erfahren Sie, wie Sie Unity für die Anwendungsentwicklung vorbereiten und konfigurieren, einschließlich Importieren des Mixed Reality Toolkit, Konfigurieren von Buildeinstellungen und Vorbereiten der Szene.</span><span class="sxs-lookup"><span data-stu-id="1a050-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="1a050-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="1a050-107">Objectives</span></span>

* <span data-ttu-id="1a050-108">Konfigurieren von Unity für die Anwendungsentwicklung</span><span class="sxs-lookup"><span data-stu-id="1a050-108">Configure Unity for application development</span></span>
* <span data-ttu-id="1a050-109">Importieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="1a050-109">Import the Mixed Reality Toolkit</span></span>
* <span data-ttu-id="1a050-110">Vorbereiten der Projekt Szene</span><span class="sxs-lookup"><span data-stu-id="1a050-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="1a050-111">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="1a050-111">Instructions</span></span>

1. <span data-ttu-id="1a050-112">Klicken Sie hier, um das Mixed Reality Toolkit Foundation-Unity-Paket herunterzuladen und zu speichern [.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="1a050-112">Download and save the Mixed Reality Toolkit Foundation unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)</span></span>

2. <span data-ttu-id="1a050-113">Klicken Sie in Unity auf das Menü Assets, wählen Sie Paket importieren aus, und klicken Sie dann auf benutzerdefiniertes Paket.</span><span class="sxs-lookup"><span data-stu-id="1a050-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="1a050-115">Wählen Sie das Unity-Paket aus, das Sie soeben aus dem in Schritt 1 angegebenen Link heruntergeladen haben.</span><span class="sxs-lookup"><span data-stu-id="1a050-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="1a050-116">Nachdem das Popup Fenster Importieren in Unity angezeigt wird, klicken Sie auf die Schaltfläche Importieren, um mit dem Importieren von mrtk zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="1a050-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="1a050-117">Dieser Vorgang kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="1a050-117">This may take several minutes.</span></span>

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="1a050-119">Das heruntergeladene Paket befindet sich in Ihrem lokalen Ordner, in dem Sie die Datei gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="1a050-119">The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="1a050-120">In der Abbildung oben wird nicht dargestellt, wo Sie das Paket finden.</span><span class="sxs-lookup"><span data-stu-id="1a050-120">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="1a050-121">Erstellen Sie eine neue Szene.</span><span class="sxs-lookup"><span data-stu-id="1a050-121">Create a new scene.</span></span> <span data-ttu-id="1a050-122">Klicken Sie hierzu auf Datei, und wählen Sie neue Szene aus.</span><span class="sxs-lookup"><span data-stu-id="1a050-122">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="1a050-123">Speichern Sie Sie als hlsharedprojectmain.</span><span class="sxs-lookup"><span data-stu-id="1a050-123">Save it as HLSharedProjectMain.</span></span>

    <span data-ttu-id="1a050-124">Möglicherweise wird ein Popup Fenster angezeigt, das ähnlich wie in der folgenden Abbildung aussieht.</span><span class="sxs-lookup"><span data-stu-id="1a050-124">You may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="1a050-125">Klicken Sie vorerst auf Nein.</span><span class="sxs-lookup"><span data-stu-id="1a050-125">For now, click No.</span></span>
    <span data-ttu-id="1a050-126">![Module3Chapter2note1im](images/module3chapter2note1im.PNG)</span><span class="sxs-lookup"><span data-stu-id="1a050-126">![Module3Chapter2note1im](images/module3chapter2note1im.PNG)</span></span>

5. <span data-ttu-id="1a050-127">Klicken Sie unter Mixed Reality Toolkit auf zur Szene hinzufügen und konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="1a050-127">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="1a050-129">Sobald der Vorgang beendet ist, wird eine neue Konfigurationsdatei angezeigt, die Ihnen die Möglichkeit gibt, das Profil anzupassen.</span><span class="sxs-lookup"><span data-stu-id="1a050-129">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span>

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima.PNG)

7. <span data-ttu-id="1a050-131">Wählen Sie in der Hierarchie Mixed-Reality Toolkit (mrtk) aus.</span><span class="sxs-lookup"><span data-stu-id="1a050-131">Select Mixed-Reality Toolkit (MRTK) from the  hierarchy.</span></span> <span data-ttu-id="1a050-132">Suchen Sie im Inspektor-Panel nach dem Mixed Reality Toolkit-Skript, und klicken Sie auf die Schaltfläche zum Kopieren & anpassen, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="1a050-132">In the inspector panel, look for the Mixed Reality Toolkit Script and press the "Copy & Customize" button  as shown in the figure below.</span></span>  <span data-ttu-id="1a050-133">Danach wird ein Pop angezeigt, und wählen Sie im Popupmenü die Option Klonen aus.</span><span class="sxs-lookup"><span data-stu-id="1a050-133">A pop will appear after this and select clone option in the pop up menu.</span></span>

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. <span data-ttu-id="1a050-136">Scrollen Sie nach unten, und deaktivieren Sie Diagnosesystem aktivieren, wenn Sie das Diagnosefenster ausblenden möchten.</span><span class="sxs-lookup"><span data-stu-id="1a050-136">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="1a050-137">Es wird empfohlen, das Diagnosefenster während der Anwendungsentwicklung zu aktivieren, um die Leistung zu überwachen und es dann während der Produktions-oder Anwendungs Demos zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="1a050-137">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. <span data-ttu-id="1a050-139">Öffnen Sie die Buildeinstellungen, indem Sie STRG + UMSCHALT + B drücken, oder wechseln Sie zu Datei > Buildeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="1a050-139">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="1a050-140">Beachten Sie, dass das Programm derzeit unter der eigenständigen PC-, Mac-und Linux-Plattform festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="1a050-140">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="1a050-141">Legen Sie für die Entwicklung von hololens 2 die Plattform auf universelle Windows-Plattform fest.</span><span class="sxs-lookup"><span data-stu-id="1a050-141">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="1a050-142">Wählen Sie es aus, und klicken Sie auf Plattform wechseln.</span><span class="sxs-lookup"><span data-stu-id="1a050-142">Select it and click Switch Platform.</span></span>

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. <span data-ttu-id="1a050-144">Klicken Sie nach Abschluss des Vorgangs auf das Feld mit dem Namen offene Szenen hinzufügen</span><span class="sxs-lookup"><span data-stu-id="1a050-144">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="1a050-145">Wechseln Sie nun zum Inspektor-Panel, und stellen Sie sicher, dass das Kontrollkästchen rechts von Virtual Reality unterstützt wird (wie in der folgenden Abbildung dargestellt).</span><span class="sxs-lookup"><span data-stu-id="1a050-145">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="1a050-146">Stellen Sie außerdem sicher, dass das Kontrollkästchen nebenszenen/hlsharedprojectmain ebenfalls aktiviert ist, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="1a050-146">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. <span data-ttu-id="1a050-148">Scrollen Sie im Bereich Inspector im Bereich Veröffentlichungs Einstellungen nach unten zu Funktionen, und stellen Sie sicher, dass die folgenden Kontrollkästchen markiert sind:</span><span class="sxs-lookup"><span data-stu-id="1a050-148">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. <span data-ttu-id="1a050-150">Importieren Sie die aufgelisteten benutzerdefinierten Pakete:</span><span class="sxs-lookup"><span data-stu-id="1a050-150">Import the listed custom packages:</span></span>

    <span data-ttu-id="1a050-151">ein.</span><span class="sxs-lookup"><span data-stu-id="1a050-151">a.</span></span> [<span data-ttu-id="1a050-152">Unity. HoloLens2. GettingStarted. Tutorials. Asset. 2.1.0.0. unitypackage</span><span class="sxs-lookup"><span data-stu-id="1a050-152">Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage)

    <span data-ttu-id="1a050-153">b.</span><span class="sxs-lookup"><span data-stu-id="1a050-153">b.</span></span> [<span data-ttu-id="1a050-154">Unity. HoloLens2. multiuserfunktionalitäten. Tutorials. Asset. 2.1.0.0. unitypackage</span><span class="sxs-lookup"><span data-stu-id="1a050-154">Unity.HoloLens2.MultiUserCapabilities.Tutorials.Asset.2.1.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.0/Unity.HoloLens2.MultiUserCapabilities.Tutorials.Asset.2.1.0.0.unitypackage)

    >[!TIP]
    ><span data-ttu-id="1a050-155">Wenn Sie die [Tutorials zu](mrlearning-base-ch1.md)den ersten Schritten abgeschlossen haben, ist das Unity-Paket mit dem Namen _Unity. HoloLens2. GettingStarted. Tutorials. Asset. 2.1.0.0. unitypackage_ auf dem Computer gespeichert.</span><span class="sxs-lookup"><span data-stu-id="1a050-155">If you have completed the [Getting started tutorials](mrlearning-base-ch1.md), you might still have the Unity package named _Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage_ stored on your computer.</span></span> <span data-ttu-id="1a050-156">Wenn dies der Fall ist, können Sie das Herunterladen des in Schritt a aufgeführten Assets überspringen.</span><span class="sxs-lookup"><span data-stu-id="1a050-156">If so, you can skip downloading the asset listed in step a above.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

13. <span data-ttu-id="1a050-158">Wechseln Sie im Projekt Panel zum Ordner Prefabs.</span><span class="sxs-lookup"><span data-stu-id="1a050-158">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="1a050-159">In den folgenden Schritten implementieren Sie einige Prefabs in der Szene.</span><span class="sxs-lookup"><span data-stu-id="1a050-159">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="1a050-160">Klicken Sie im Ordner Prefabs auf das Fenster Prefab, Debug, und ziehen Sie es in die Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="1a050-160">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="1a050-161">Wenn Sie fertig sind, speichern Sie das Projekt, indem Sie auf Datei und dann auf Speichern klicken oder STRG + S drücken.</span><span class="sxs-lookup"><span data-stu-id="1a050-161">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    <span data-ttu-id="1a050-163">Sie werden möglicherweise feststellen, dass ein Popup Fenster angezeigt wird, wenn Sie auf die vorfab klicken und Sie zu tmp Essentials auffordern.</span><span class="sxs-lookup"><span data-stu-id="1a050-163">You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="1a050-164">Klicken Sie auf tmp Essentials nach Bedarf importieren.</span><span class="sxs-lookup"><span data-stu-id="1a050-164">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="1a050-165">Wenn dieses Popup Fenster angezeigt wird, müssen Sie möglicherweise die vorfab aus Ihrer Hierarchie löschen und in ihre Hierarchie ziehen, um potenzielle Text bezogene Fehler zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="1a050-165">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="1a050-167">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="1a050-167">Congratulations</span></span>

<span data-ttu-id="1a050-168">Ihr Unity-Projekt ist nun für das Photon bereit.</span><span class="sxs-lookup"><span data-stu-id="1a050-168">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="1a050-169">In den nächsten Tutorials bauen wir auf dieser Szene und unserem Unity-Projekt auf, um eine vollständige gemeinsame Nutzung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="1a050-169">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="1a050-170">[Nächstes Tutorial: 3. Verbinden von mehreren Benutzern](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="1a050-170">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>
