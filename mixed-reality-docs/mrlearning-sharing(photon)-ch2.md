---
title: Lernen die Freigabe-Modul für HoloLens 2 MR
description: Führen Sie diesen Kurs erfahren, wie Sie mehrere Benutzer freigegebene Umgebungen innerhalb einer HoloLens-2-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 957813d24de95aad52c26b4bd0f0996a60d01358
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327630"
---
# <a name="getting-unity-ready-for-development"></a><span data-ttu-id="98902-104">**Vorbereitung von Unity für die Entwicklung**</span><span class="sxs-lookup"><span data-stu-id="98902-104">**Getting Unity Ready for Development**</span></span> 

<span data-ttu-id="98902-105">In dieser Lektion erfahren wir, wie zum Vorbereiten und Konfigurieren von Unity für die Entwicklung von Apps, wie z.B. das Mixed Reality-Toolkit importieren und Konfigurieren von Buildeinstellungen unsere Szene wird vorbereitet.</span><span class="sxs-lookup"><span data-stu-id="98902-105">In this lesson, we will learn how to prepare and configure Unity for app development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

<span data-ttu-id="98902-106">Ziele:</span><span class="sxs-lookup"><span data-stu-id="98902-106">Objectives:</span></span>

- <span data-ttu-id="98902-107">Konfigurieren von Unity für app-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="98902-107">Configure Unity for app development</span></span>

- <span data-ttu-id="98902-108">Importieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="98902-108">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="98902-109">Vorbereiten Sie Ihrer Projekt-Szene</span><span class="sxs-lookup"><span data-stu-id="98902-109">Prepare your project scene</span></span>

### <a name="instructions"></a><span data-ttu-id="98902-110">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="98902-110">Instructions</span></span>

1. <span data-ttu-id="98902-111">Herunterladen und speichern Sie die Mixed Reality-Toolkit Unity-Paket, indem Sie auf [hier.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1-Refresh.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="98902-111">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1-Refresh.unitypackage)</span></span>
2. <span data-ttu-id="98902-112">Klicken Sie in Unity auf das Menü "Ressourcen" auf Wählen Sie aus "Paket importieren", und klicken Sie auf "Benutzerdefinierte Package".</span><span class="sxs-lookup"><span data-stu-id="98902-112">In Unity, click on the assets menu and select "Import Package," then click on "Custom Package."</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="98902-114">Wählen Sie das Unity-Paket, die, das Sie gerade heruntergeladen, über den Link in Schritt 1 bereitgestellt haben.</span><span class="sxs-lookup"><span data-stu-id="98902-114">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="98902-115">Wenn das Popup-Fenster Importieren in Unity angezeigt wird, klicken Sie auf die Schaltfläche "Importieren", um Import zu starten.</span><span class="sxs-lookup"><span data-stu-id="98902-115">Once the import pop-up window appears in Unity, click the import button to begin importing.</span></span> <span data-ttu-id="98902-116">Importieren die MRTK kann mehrere Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="98902-116">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="98902-118">Hinweis: Das heruntergeladene Paket werden im lokalen Ordner, in dem Sie die Datei gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="98902-118">Note: The downloaded package will be in your local folder where you have saved the file.</span></span> <span data-ttu-id="98902-119">In der Abbildung oben ist nicht darstellen, in dem Sie das Paket finden.</span><span class="sxs-lookup"><span data-stu-id="98902-119">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="98902-120">Erstellen Sie eine neue Szene (Dies kann erfolgen durch Klicken auf "File", und wählen "neue Szene").</span><span class="sxs-lookup"><span data-stu-id="98902-120">Create a new scene (this can be done by clicking "file" and selecting "new scene").</span></span> <span data-ttu-id="98902-121">Speichern Sie die Szene als "HLSharedProjectMain."</span><span class="sxs-lookup"><span data-stu-id="98902-121">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="98902-122">Hinweis: wird möglicherweise ein Popupfenster angezeigt, die in der folgenden Abbildung ähneln.</span><span class="sxs-lookup"><span data-stu-id="98902-122">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="98902-123">Jetzt klicken Sie einfach auf "No"</span><span class="sxs-lookup"><span data-stu-id="98902-123">For now, just click "No."</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="98902-125">Klicken Sie unter "Mixed Reality-Toolkit" auf "Szene hinzufügen und konfigurieren."</span><span class="sxs-lookup"><span data-stu-id="98902-125">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="98902-127">Sobald dies abgeschlossen ist, wird eine neue Konfigurationsdatei angezeigt, bietet Ihnen die Möglichkeit, die das Profil anzupassen.</span><span class="sxs-lookup"><span data-stu-id="98902-127">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="98902-128">Klicken Sie auf "kopieren und anpassen."</span><span class="sxs-lookup"><span data-stu-id="98902-128">Click "copy and customize."</span></span>

![Module3Chapter2step6im](images/module3chapter2step6im.PNG)

7. <span data-ttu-id="98902-130">Scrollen Sie nach unten, und deaktivieren Sie die Option "Diagnostics-System aktivieren", wenn Sie das Diagnosefenster ausblenden möchten.</span><span class="sxs-lookup"><span data-stu-id="98902-130">Scroll down and uncheck "enable diagnostics system" if you would like to hide the diagnostics window.</span></span> <span data-ttu-id="98902-131">Wir empfehlen die Diagnostics-Fenster, während der Entwicklung von Apps für die Leistungsüberwachung aktiviert, und sie während der Produktion oder Anwendung Demos zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="98902-131">We recommend keeping the diagnostics window enabled during app development to monitor performance, and disabling it during production or application demonstrations.</span></span>

![Module3Chapter2step7im](images/module3chapter2step7im.PNG)

8. <span data-ttu-id="98902-133">Öffnen Sie die Buildeinstellungen durch Drücken von STRG + UMSCHALT + B oder die Datei > Buildeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="98902-133">Open the build settings by pressing control+shift+B or going to File>Build Settings.</span></span> <span data-ttu-id="98902-134">Beachten Sie, dass das Programm derzeit unter der Plattform "PC, Mac und Linux-eigenständig" festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="98902-134">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="98902-135">Legen Sie für die Entwicklung für HoloLens 2 die Plattform, die "universelle Windows-Plattform."</span><span class="sxs-lookup"><span data-stu-id="98902-135">For HoloLens 2 development, set the platform to be "Universal Windows Platform."</span></span> <span data-ttu-id="98902-136">Wählen Sie sie aus, und klicken Sie auf "switch Platform".</span><span class="sxs-lookup"><span data-stu-id="98902-136">Select it and click "switch platform."</span></span>

   ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

   9. <span data-ttu-id="98902-138">Sobald der Vorgang abgeschlossen ist, klicken Sie auf das Kontrollkästchen "open Szenen hinzufügen".</span><span class="sxs-lookup"><span data-stu-id="98902-138">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="98902-139">Kehren Sie jetzt den Inspektor-Zugriffsbereich und sicherstellen, dass das Kontrollkästchen rechts neben "virtual Reality unterstützt" (wie in der folgenden Abbildung gezeigt) aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="98902-139">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> <span data-ttu-id="98902-140">Stellen Sie außerdem sicher, dass Sie das Kontrollkästchen neben "Szenen/HLSharedProjectMain" ebenfalls aktiviert ist, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="98902-140">Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked, as shown in the image below.</span></span>

   ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

   10. <span data-ttu-id="98902-142">Unter "Publishing Settings" im Abschnitt der Inspektor Bereich Scrollen Sie zu "Funktionen", und stellen Sie sicher, dass die folgenden Kontrollkästchen markiert sind:</span><span class="sxs-lookup"><span data-stu-id="98902-142">Under the "Publishing Settings" section in the inspector panel scroll down to "Capabilities" and ensure the following check boxes are marked:</span></span>
    - <span data-ttu-id="98902-143">Internetclient</span><span class="sxs-lookup"><span data-stu-id="98902-143">internet client</span></span>
       
       - <span data-ttu-id="98902-144">IIS-Client-server</span><span class="sxs-lookup"><span data-stu-id="98902-144">internet client server</span></span>
       
       - <span data-ttu-id="98902-145">VPN-Client-server</span><span class="sxs-lookup"><span data-stu-id="98902-145">private network client server</span></span>
   
       - <span data-ttu-id="98902-146">camera/webcam</span><span class="sxs-lookup"><span data-stu-id="98902-146">camera/webcam</span></span>

       - <span data-ttu-id="98902-147">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="98902-147">microphone</span></span>
   
   11. <span data-ttu-id="98902-148">Importieren Sie das benutzerdefinierte Paket "Lektion 2: komplettes" heruntergeladen werden, können hier aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="98902-148">Import the custom package called "Lesson2" which can be downloaded here.</span></span> <span data-ttu-id="98902-149">TODO: Geben Sie die Verknüpfung mit ressourcenpaket.</span><span class="sxs-lookup"><span data-stu-id="98902-149">TODO: Provide link to asset pack.</span></span>
   
   ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)
   
   12. <span data-ttu-id="98902-151">Im Projektfenster, wechseln Sie nun zum Ordner "Prefabs", da in den nächsten Schritten Sie einige prefabs (Vorlagen) in der Szene implementieren werden.</span><span class="sxs-lookup"><span data-stu-id="98902-151">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="98902-152">Klicken Sie im Ordner "Prefabs" klicken Sie, und ziehen Sie das Prefab, "DebugWindow" in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="98902-152">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="98902-153">Sobald Sie fertig sind, speichern Sie das Projekt (klicken Sie auf die Datei, klicken Sie dann speichern, oder drücken Sie STRG + S)</span><span class="sxs-lookup"><span data-stu-id="98902-153">Once finished, save the project (click file, then save, or press control+S)</span></span>
   
       ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)
   
   > <span data-ttu-id="98902-155">Hinweis: Sie werden feststellen, dass ein Popupfenster angezeigt, wenn Sie auf das Prefab klicken TMP Essentials gefragt.</span><span class="sxs-lookup"><span data-stu-id="98902-155">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="98902-156">Klicken Sie auf "Import TMP Essentials", da sie benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="98902-156">Click "Import TMP Essentials" as they will be needed.</span></span> <span data-ttu-id="98902-157">Wenn dieses Popupfenster angezeigt wird, müssen Sie möglicherweise das Prefab in Ihrer Hierarchie zu löschen, und ziehen es erneut in Ihrer Hierarchie aus, um mögliche Fehler in Bezug auf Text zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="98902-157">If this pop-up appears, you may need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="98902-159">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="98902-159">Congratulations</span></span>

<span data-ttu-id="98902-160">Ihr Unity-Projekt ist jetzt für Photon bereit!</span><span class="sxs-lookup"><span data-stu-id="98902-160">Your Unity Project is now ready for Photon!</span></span> <span data-ttu-id="98902-161">In den nächsten Lektionen erstellen wir auf diese Szene und unsere Unity-Projekt für eine umfassende freigegebenen Umgebung.</span><span class="sxs-lookup"><span data-stu-id="98902-161">In the coming lessons, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="98902-162">[Nächste Lektion: Sharing(Photon) Lektion 3](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="98902-162">[Next Lesson: Sharing(Photon) Lesson 3](mrlearning-sharing(photon)-ch3.md)</span></span>

