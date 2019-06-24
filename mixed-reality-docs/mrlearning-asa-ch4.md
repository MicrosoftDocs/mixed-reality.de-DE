---
title: MR Learning ASA-Modul Azure räumliche Anker für HoloLens 2
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: b29f27284c352d27fb1d4d4de701a1ebc2a7cd1c
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327841"
---
# <a name="photon-correct-me-if-im-wrong"></a><span data-ttu-id="975ba-104">Photon (korrigieren mich, wenn ich falsch bin)</span><span class="sxs-lookup"><span data-stu-id="975ba-104">Photon (correct me if I'm wrong)</span></span>

<span data-ttu-id="975ba-105">In dieser Lektion</span><span class="sxs-lookup"><span data-stu-id="975ba-105">In this lesson,</span></span> 

<span data-ttu-id="975ba-106">Ziele:</span><span class="sxs-lookup"><span data-stu-id="975ba-106">Objectives:</span></span>

* <span data-ttu-id="975ba-107">Erfahren Sie, wie Sie in den ___</span><span class="sxs-lookup"><span data-stu-id="975ba-107">Learn how to _____________________________________________</span></span>

* <span data-ttu-id="975ba-108">Erfahren Sie, wie Sie in den ___</span><span class="sxs-lookup"><span data-stu-id="975ba-108">Learn how to _________________________________________________</span></span>

  

## <a name="instructions"></a><span data-ttu-id="975ba-109">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="975ba-109">Instructions</span></span>

### <a name="setting-up-photon"></a><span data-ttu-id="975ba-110">Einrichten von Photon</span><span class="sxs-lookup"><span data-stu-id="975ba-110">Setting Up Photon</span></span>

1. <span data-ttu-id="975ba-111">Richten Sie eine [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) Konto.</span><span class="sxs-lookup"><span data-stu-id="975ba-111">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="975ba-112">Auf diese Weise wird der imputing Ihre e-Mail-Adresse ein, und durchlaufen einige Überprüfungsschritte bestehen.</span><span class="sxs-lookup"><span data-stu-id="975ba-112">Doing this will consist of imputing your email and going through some verification steps.</span></span>
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. <span data-ttu-id="975ba-114">Sobald Sie angemeldet sind, klicken Sie auf der SDKs.</span><span class="sxs-lookup"><span data-stu-id="975ba-114">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="975ba-115">Sobald Sie auf dieser Seite sind, klicken Sie auf "Server", und stellen Sie sicher Name schon sagt, "selbst gehostet."</span><span class="sxs-lookup"><span data-stu-id="975ba-115">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="975ba-116">Scrollen Sie nach unten, und klicken Sie auf "Server", wie in der zweiten Abbildung unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="975ba-116">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. <span data-ttu-id="975ba-119">Ein Textfeld mit der Bezeichnung, angezeigt werden. dadurch "read me."</span><span class="sxs-lookup"><span data-stu-id="975ba-119">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="975ba-120">Fahren Sie fort, und Lesen Sie sie.</span><span class="sxs-lookup"><span data-stu-id="975ba-120">Go ahead and read it.</span></span> <span data-ttu-id="975ba-121">Sobald Sie fertig sind, klicken Sie auf den Link neben "DownloadSDK", um sie herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="975ba-121">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. <span data-ttu-id="975ba-123">Doppelklicken Sie den Ordner aus, nachdem der Download abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="975ba-123">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="975ba-124">Wenn Ihre Datei-Explorer geöffnet wird, den SDK-Ordner offenzulegen, kopieren Sie den SDK-Ordner.</span><span class="sxs-lookup"><span data-stu-id="975ba-124">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="975ba-125">Der nächste Schritt wäre in der Windows-Laufwerk "c:" wechseln, und erstellen einen neuen Ordner namens "Server".</span><span class="sxs-lookup"><span data-stu-id="975ba-125">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - <span data-ttu-id="975ba-127">Jetzt öffnen Sie den Ordner, und fügen Sie den SDK-Ordner, die, den Sie zuvor kopiert haben.</span><span class="sxs-lookup"><span data-stu-id="975ba-127">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. <span data-ttu-id="975ba-129">Sobald dies abgeschlossen ist, öffnen Sie den SDK-Ordner, und wechseln Sie zu ", klicken Sie dann"bin_Win64,"Bereitstellen" doppelklicken und klicken Sie dann auf "Photon-Steuerelement".</span><span class="sxs-lookup"><span data-stu-id="975ba-129">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> <span data-ttu-id="975ba-131">Hinweis: Wenn Sie Fragen zur IP-Adresse oder andere ähnlichen Fragen haben, finden die meisten Informationen auf der Symbolleiste Sie (wie in der folgenden Abbildung gezeigt).</span><span class="sxs-lookup"><span data-stu-id="975ba-131">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. <span data-ttu-id="975ba-133">Jetzt an, dass der Server eingerichtet und initiiert wird, wechseln Sie zurück zur Website Photon und klicken Sie auf das Symbol "Profil" (geschachtelt in der Abbildung unten) und wählen Sie "Ihrer Anwendungen."</span><span class="sxs-lookup"><span data-stu-id="975ba-133">Now that the server is set up and initiated, go back to the Photon website and click on the profile icon (boxed in the image below) and select "your applications."</span></span>
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. <span data-ttu-id="975ba-135">Erstellen Sie eine Anwendungs-ID, indem Sie auf die Schaltfläche "erstellen eine neue app".</span><span class="sxs-lookup"><span data-stu-id="975ba-135">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - <span data-ttu-id="975ba-137">Wählen Sie "Photon ausführen" aus dem Dropdown-Menü unter "Photon geben."</span><span class="sxs-lookup"><span data-stu-id="975ba-137">Select "Photon RUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="975ba-138">Klicken Sie dann benennen Sie es, (etwas, das Sie daran denken, würde).</span><span class="sxs-lookup"><span data-stu-id="975ba-138">Then give it a name, (something you would remember).</span></span> <span data-ttu-id="975ba-139">In diesem Beispiel mit dem Namen wir es "HoloLensPhotonProject."</span><span class="sxs-lookup"><span data-stu-id="975ba-139">In this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="975ba-140">Sobald Sie fertig sind, klicken Sie auf "erstellen".</span><span class="sxs-lookup"><span data-stu-id="975ba-140">Once finished, click "create."</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. <span data-ttu-id="975ba-142">Sobald das geschehen ist, kehren Sie zu Ihrer Seite "Anwendungen" zurück und sollte in etwa der folgenden Abbildung.</span><span class="sxs-lookup"><span data-stu-id="975ba-142">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="975ba-143">Klicken Sie auf die app-ID, und kopieren Sie ihn.</span><span class="sxs-lookup"><span data-stu-id="975ba-143">Click on the app ID and copy it.</span></span> <span data-ttu-id="975ba-144">Fügen Sie ist etwas, das Sie auf einfache Weise zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="975ba-144">Paste is somewhere you can easily access.</span></span>  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. <span data-ttu-id="975ba-146">Erstellen Sie ein neues Unity-Projekt.</span><span class="sxs-lookup"><span data-stu-id="975ba-146">Create a new unity project.</span></span> <span data-ttu-id="975ba-147">Öffnen Sie Unity-Hub, und klicken Sie auf "Neu".</span><span class="sxs-lookup"><span data-stu-id="975ba-147">Open Unity Hub and click on "new."</span></span> <span data-ttu-id="975ba-148">Nennen Sie es mit "HLSharingProject."</span><span class="sxs-lookup"><span data-stu-id="975ba-148">Name it "HLSharingProject."</span></span> <span data-ttu-id="975ba-149">Klicken Sie dann auf erstellen zu können.</span><span class="sxs-lookup"><span data-stu-id="975ba-149">Then click create.</span></span> 

   > <span data-ttu-id="975ba-150">Hinweis: Dies kann zu laden, bis zu 2 Minuten dauern, basierend auf der Geschwindigkeit des Computers.</span><span class="sxs-lookup"><span data-stu-id="975ba-150">note: This can take up to 2 minutes to load, based on your computer's speed.</span></span>

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> <span data-ttu-id="975ba-152">Hinweis: Wählen Sie einen Speicherort für Ihr Projekt auf Ihrem Computer zu speichern, indem Sie die Option "Location" ändern.</span><span class="sxs-lookup"><span data-stu-id="975ba-152">note: pick a place to save your project in your computer by changing the "location" option.</span></span> <span data-ttu-id="975ba-153">Speichern Sie es an einem Ort, den Sie werden merken und einfachen Zugriff auf.</span><span class="sxs-lookup"><span data-stu-id="975ba-153">Save it to a place you will remember and have easy access to.</span></span>

10. <span data-ttu-id="975ba-154">Nachdem das Projekt geladen wurde, klicken Sie auf der "Assets"Speicher.</span><span class="sxs-lookup"><span data-stu-id="975ba-154">Once the project loads, click on the "assets store."</span></span> <span data-ttu-id="975ba-155">Klicken Sie dann in das Suchfeld in der folgenden Abbildung gezeigt, geben Sie in "WORTSPIEL", und wählen Sie das Medienobjekt "Photon WORTSPIEL-2-frei".</span><span class="sxs-lookup"><span data-stu-id="975ba-155">Then, in the search box shown in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset.</span></span> 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. <span data-ttu-id="975ba-157">Herunterladen und importieren.</span><span class="sxs-lookup"><span data-stu-id="975ba-157">Download and import!</span></span>
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a><span data-ttu-id="975ba-159">**Einrichten des Unity-Projekts**</span><span class="sxs-lookup"><span data-stu-id="975ba-159">**Setting Up the Unity Project**</span></span> 

11. <span data-ttu-id="975ba-160">Laden Sie ein neues Medienobjekt erforderlich, um Photon in Unity einrichten, indem Sie auf [hier.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="975ba-160">download a new asset needed to set up Photon in Unity by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span></span>

12. <span data-ttu-id="975ba-161">Klicken Sie in Unity auf das Menü "Assets" "Importieren Assets" Wählen Sie aus, und klicken Sie auf "benutzerdefinierte Ressourcen."</span><span class="sxs-lookup"><span data-stu-id="975ba-161">In Unity, click on the assets menu and select "import assets," then click on "custom assets."</span></span>

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. <span data-ttu-id="975ba-163">Wählen Sie das Unity-Paket, die, das Sie gerade heruntergeladen, über den Link in Schritt 1 bereitgestellt haben.</span><span class="sxs-lookup"><span data-stu-id="975ba-163">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="975ba-164">Wenn die Schaltfläche "Importieren" in Unity angezeigt wird, klicken Sie darauf.</span><span class="sxs-lookup"><span data-stu-id="975ba-164">Once the import button appears in Unity, click it.</span></span>

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> <span data-ttu-id="975ba-166">Hinweis: ganz egal, wo Sie das Paket heruntergeladen werden, wo Sie ihn finden.</span><span class="sxs-lookup"><span data-stu-id="975ba-166">note: wherever you downloaded the package to will be where you find it.</span></span> <span data-ttu-id="975ba-167">In der Abbildung oben ist nicht darstellen, in dem Sie das Paket finden.</span><span class="sxs-lookup"><span data-stu-id="975ba-167">The image above does not portray where you will find the package.</span></span>

14. <span data-ttu-id="975ba-168">Erstellen Sie eine neue Szene (Dies kann sein, mithilfe des Steuerelements / Befehl + N oder durch Klicken auf "file", und wählen "neue Szene.").</span><span class="sxs-lookup"><span data-stu-id="975ba-168">Create a new scene (this can be done using control/command+N or by clicking "file" and selecting "new scene.").</span></span> <span data-ttu-id="975ba-169">Speichern Sie die Szene als "HLSharedProjectMain."</span><span class="sxs-lookup"><span data-stu-id="975ba-169">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="975ba-170">Hinweis: erhalten Sie möglicherweise ein Popupfenster, das in der folgenden Abbildung ähneln.</span><span class="sxs-lookup"><span data-stu-id="975ba-170">note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="975ba-171">Jetzt klicken Sie einfach auf "Nein" festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="975ba-171">For now, just click "no."</span></span>
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. <span data-ttu-id="975ba-173">Klicken Sie unter "Mixed Reality-Toolkit" auf "Szene hinzufügen und konfigurieren."</span><span class="sxs-lookup"><span data-stu-id="975ba-173">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. <span data-ttu-id="975ba-175">Sobald dies abgeschlossen ist, wird eine neue Konfigurationsdatei angezeigt, bietet Ihnen die Möglichkeit, die das Profil anzupassen.</span><span class="sxs-lookup"><span data-stu-id="975ba-175">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="975ba-176">Klicken Sie auf "kopieren und anpassen."</span><span class="sxs-lookup"><span data-stu-id="975ba-176">Click "copy and customize."</span></span>

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. <span data-ttu-id="975ba-178">Scrollen Sie nach unten, und deaktivieren Sie die Option "Diagnostics-System aktivieren".</span><span class="sxs-lookup"><span data-stu-id="975ba-178">Scroll down and uncheck "enable diagnostics system."</span></span> <span data-ttu-id="975ba-179">Dies wird zum Einrichten dieses Projekts erleichtern.</span><span class="sxs-lookup"><span data-stu-id="975ba-179">This will make it easier to set up this project.</span></span>

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. <span data-ttu-id="975ba-181">Öffnen Sie die Buildeinstellungen (STRG + UMSCHALTTASTE + B).</span><span class="sxs-lookup"><span data-stu-id="975ba-181">Open the build settings (control+shift+B).</span></span> <span data-ttu-id="975ba-182">Beachten Sie, dass das Programm derzeit unter der Plattform "PC, Mac und Linux-eigenständig" festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="975ba-182">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="975ba-183">Legen Sie für dieses Projekt die Plattform "universelle Windows-Plattform" sein.</span><span class="sxs-lookup"><span data-stu-id="975ba-183">For this project, set the platform to be "universal windows platform."</span></span> <span data-ttu-id="975ba-184">Wählen Sie sie aus, und klicken Sie auf "switch Platform".</span><span class="sxs-lookup"><span data-stu-id="975ba-184">Select it and click "switch platform."</span></span>

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. <span data-ttu-id="975ba-186">Sobald der Vorgang abgeschlossen ist, klicken Sie auf das Kontrollkästchen "open Szenen hinzufügen".</span><span class="sxs-lookup"><span data-stu-id="975ba-186">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="975ba-187">Kehren Sie jetzt den Inspektor-Zugriffsbereich und sicherstellen, dass das Kontrollkästchen rechts neben "virtual Reality unterstützt" (wie in der folgenden Abbildung gezeigt) aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="975ba-187">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> <span data-ttu-id="975ba-189">Hinweis: Stellen Sie außerdem sicher, dass Sie das Kontrollkästchen neben "Szenen/HLSharedProjectMain" ebenfalls aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="975ba-189">note: Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked.</span></span>

20. <span data-ttu-id="975ba-190">Klicken Sie unter "veröffentlichungseinstellungen" im Bereich Inspektor scrollen "Funktionen", und stellen Sie sicher, es werden nur die folgenden Kontrollkästchen markiert:</span><span class="sxs-lookup"><span data-stu-id="975ba-190">Under the "publishing settings" in the inspector panel scroll down to "capabilities" and ensure only the following check boxes are marked:</span></span>

- <span data-ttu-id="975ba-191">Internetclient</span><span class="sxs-lookup"><span data-stu-id="975ba-191">internet client</span></span>
- <span data-ttu-id="975ba-192">IIS-Client-server</span><span class="sxs-lookup"><span data-stu-id="975ba-192">internet client server</span></span>
- <span data-ttu-id="975ba-193">VPN-Client-server</span><span class="sxs-lookup"><span data-stu-id="975ba-193">private network client server</span></span>
- <span data-ttu-id="975ba-194">camera/webcam</span><span class="sxs-lookup"><span data-stu-id="975ba-194">camera/webcam</span></span>
- <span data-ttu-id="975ba-195">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="975ba-195">microphone</span></span>

21. <span data-ttu-id="975ba-196">Schritt 12, wie wäre der nächste Schritt, importieren ein anderes benutzerdefiniertes Paket namens "Lektion 2: komplettes" das [Hier] heruntergeladen werden kann [lesson2.unitypackage Link hier einfügen] Importieren Sie das Paket an.</span><span class="sxs-lookup"><span data-stu-id="975ba-196">Just like step 12, the next step would be to import another custom package called "Lesson2" which can be downloaded [here.][lesson2.unitypackage link goes here] Import that package.</span></span>

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. <span data-ttu-id="975ba-198">Im Projektfenster, wechseln Sie nun zum Ordner "Prefabs", da in den nächsten Schritten Sie einige prefabs (Vorlagen) in der Szene implementieren werden.</span><span class="sxs-lookup"><span data-stu-id="975ba-198">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="975ba-199">Klicken Sie im Ordner "Prefabs" klicken Sie, und ziehen Sie das Prefab, "DebugWindow" in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="975ba-199">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="975ba-200">Sobald Sie fertig sind, speichern Sie das Projekt (klicken Sie auf Datei, klicken Sie dann speichern, oder STRG + S)</span><span class="sxs-lookup"><span data-stu-id="975ba-200">Once finished, save the project (click file, then save, or control+S)</span></span>

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> <span data-ttu-id="975ba-202">Hinweis: Sie werden feststellen, dass ein Popupfenster angezeigt, wenn Sie auf das Prefab klicken TMP Essentials gefragt.</span><span class="sxs-lookup"><span data-stu-id="975ba-202">note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="975ba-203">Klicken Sie auf "Import TMP Essentials", da sie benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="975ba-203">Click "Import TMP Essentials" as they will be needed.</span></span>
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a><span data-ttu-id="975ba-205">**Verbinden von mehreren Benutzern**</span><span class="sxs-lookup"><span data-stu-id="975ba-205">**Connecting Multiple Users**</span></span>

23. <span data-ttu-id="975ba-206">Wie in Schritt 22, im Ordner "Prefabs" im Projektfenster, besteht der nächste Schritt, um Drag & drop die Prefab "NetworkLobby" in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="975ba-206">Like step 22, in the "prefabs" folder in the project panel, the next step is to drag and drop the "NetworkLobby" prefab in to the hierarchy.</span></span> 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. <span data-ttu-id="975ba-208">Wenn Sie den übergeordneten-Prefab "NetworkLobby," öffnen, sehen Sie ein untergeordnetes Element prefab, "NetworkRoom."</span><span class="sxs-lookup"><span data-stu-id="975ba-208">When you open up the parent prefab, "NetworkLobby," you should see a child prefab, "NetworkRoom."</span></span> <span data-ttu-id="975ba-209">Klicken Sie mit der sie ausgewählt haben wechseln Sie in den Bereich der Eigenschaftenanalyse, und klicken Sie auf "Komponente hinzufügen" aus.</span><span class="sxs-lookup"><span data-stu-id="975ba-209">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="975ba-210">Suchen Sie nach "PhotonView", und fügen Sie die Komponente.</span><span class="sxs-lookup"><span data-stu-id="975ba-210">Search for "PhotonView" and add the component.</span></span>

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. <span data-ttu-id="975ba-212">Erstellen Sie ein neues, leeres game-Objekt, in der Hierarchie (Rechtsklick in der Hierarchie, und wählen Sie "leere").</span><span class="sxs-lookup"><span data-stu-id="975ba-212">Create a new empty game object in the hierarchy (right click in the hierarchy and select "empty").</span></span> <span data-ttu-id="975ba-213">Stellen Sie sicher, die Positionierung festgelegt ist, auf X = 0, y = 0, Z = 0, und nennen Sie das Objekt "PhotonUser."</span><span class="sxs-lookup"><span data-stu-id="975ba-213">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a><span data-ttu-id="975ba-215">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="975ba-215">Congratulations</span></span>



