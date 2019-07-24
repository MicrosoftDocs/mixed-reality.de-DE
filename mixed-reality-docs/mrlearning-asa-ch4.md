---
title: Mr Learning ASA-Modul Azure Spatial Anchor on hololens 2
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
# <a name="photon-correct-me-if-im-wrong"></a><span data-ttu-id="40190-104">Photon (korrigieren, wenn ich falsch bin)</span><span class="sxs-lookup"><span data-stu-id="40190-104">Photon (correct me if I'm wrong)</span></span>

<span data-ttu-id="40190-105">In dieser Lektion</span><span class="sxs-lookup"><span data-stu-id="40190-105">In this lesson,</span></span> 

<span data-ttu-id="40190-106">Ziele</span><span class="sxs-lookup"><span data-stu-id="40190-106">Objectives:</span></span>

* <span data-ttu-id="40190-107">Weitere Informationen finden Sie unter _____________________________________________</span><span class="sxs-lookup"><span data-stu-id="40190-107">Learn how to _____________________________________________</span></span>

* <span data-ttu-id="40190-108">Weitere Informationen finden Sie unter _________________________________________________</span><span class="sxs-lookup"><span data-stu-id="40190-108">Learn how to _________________________________________________</span></span>

  

## <a name="instructions"></a><span data-ttu-id="40190-109">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="40190-109">Instructions</span></span>

### <a name="setting-up-photon"></a><span data-ttu-id="40190-110">Einrichten von PHOTON</span><span class="sxs-lookup"><span data-stu-id="40190-110">Setting Up Photon</span></span>

1. <span data-ttu-id="40190-111">Richten Sie ein [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) -Konto ein.</span><span class="sxs-lookup"><span data-stu-id="40190-111">Set up a [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) account.</span></span> <span data-ttu-id="40190-112">Dies führt dazu, dass Ihre e-Mail beeinträchtigt wird und einige Überprüfungs Schritte durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="40190-112">Doing this will consist of imputing your email and going through some verification steps.</span></span>
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. <span data-ttu-id="40190-114">Nachdem Sie sich angemeldet haben, klicken Sie auf sdert.</span><span class="sxs-lookup"><span data-stu-id="40190-114">Once you are signed up, click on SDKs.</span></span> <span data-ttu-id="40190-115">Wenn Sie sich auf dieser Seite befinden, klicken Sie auf "Server", und stellen Sie sicher, dass Sie "selbstgeh ostet" lautet.</span><span class="sxs-lookup"><span data-stu-id="40190-115">Once you are on that page, click on "server," and make ensure it says, "self hosted."</span></span> <span data-ttu-id="40190-116">Scrollen Sie dann nach unten, und klicken Sie auf "Server", wie in der zweiten Abbildung unten gezeigt.</span><span class="sxs-lookup"><span data-stu-id="40190-116">Then scroll down and click on "server" as seen in the second image below.</span></span>

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. <span data-ttu-id="40190-119">Dadurch wird ein Textfeld mit der Bezeichnung "Read Me" angezeigt.</span><span class="sxs-lookup"><span data-stu-id="40190-119">That will cause a text box to appear labeled, "read me."</span></span> <span data-ttu-id="40190-120">Lesen Sie den Vorgang.</span><span class="sxs-lookup"><span data-stu-id="40190-120">Go ahead and read it.</span></span> <span data-ttu-id="40190-121">Wenn Sie fertig sind, klicken Sie auf den Link neben "Download SDK", um ihn herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="40190-121">Once finished, click on the link next to "downloadSDK" to download it.</span></span>


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. <span data-ttu-id="40190-123">Wenn der Download abgeschlossen ist, doppelklicken Sie auf den Ordner.</span><span class="sxs-lookup"><span data-stu-id="40190-123">Double click the folder once it finishes downloading.</span></span>  <span data-ttu-id="40190-124">Wenn der Datei-Explorer geöffnet wird und der SDK-Ordner angezeigt wird, kopieren Sie den SDK-Ordner.</span><span class="sxs-lookup"><span data-stu-id="40190-124">Once your file explorer opens revealing the SDK folder, copy the SDK folder.</span></span>
   
   - <span data-ttu-id="40190-125">Der nächste Schritt besteht darin, auf das Laufwerk "Windows C:" zu wechseln und einen neuen Ordner namens "Server" zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="40190-125">Your next step would be to go into the windows C: drive and create a new folder called 'server.'</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - <span data-ttu-id="40190-127">Öffnen Sie jetzt den Ordner, und fügen Sie den zuvor kopierten SDK-Ordner ein.</span><span class="sxs-lookup"><span data-stu-id="40190-127">Now open up the folder, and paste the SDK folder you copied earlier.</span></span>
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. <span data-ttu-id="40190-129">Öffnen Sie nach Abschluss des Vorgangs den SDK-Ordner, und navigieren Sie zu "Bereitstellen", dann "bin_Win64". Doppelklicken Sie dann auf "Photon-Steuerelement".</span><span class="sxs-lookup"><span data-stu-id="40190-129">Once that is completed, open the SDK folder and go to "deploy," then "bin_Win64," then double click on "photon control."</span></span>


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> <span data-ttu-id="40190-131">Hinweis: Wenn Sie Fragen zur IP-Adresse oder zu anderen ähnlichen Fragen haben, finden Sie die meisten Ihrer Informationen auf der Symbolleiste (wie in der Abbildung unten dargestellt).</span><span class="sxs-lookup"><span data-stu-id="40190-131">Note: If you have any questions about IP address, or any other similar questions, you can find most of your information in the toolbar (as shown in the image below).</span></span>
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. <span data-ttu-id="40190-133">Nachdem der Server eingerichtet und initiiert wurde, wechseln Sie zurück zur Website von PHOTON, und klicken Sie auf das Profil Symbol (in der Abbildung unten dargestellt), und wählen Sie "Ihre Anwendungen".</span><span class="sxs-lookup"><span data-stu-id="40190-133">Now that the server is set up and initiated, go back to the Photon website and click on the profile icon (boxed in the image below) and select "your applications."</span></span>
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. <span data-ttu-id="40190-135">Erstellen Sie eine Anwendungs-ID, indem Sie auf die Schaltfläche "neue APP erstellen" klicken.</span><span class="sxs-lookup"><span data-stu-id="40190-135">Create an application ID by clicking the "create a new app" button.</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - <span data-ttu-id="40190-137">Wählen Sie im Dropdown Menü unter "Photon Type" die Option "Photon Run" aus.</span><span class="sxs-lookup"><span data-stu-id="40190-137">Select "Photon RUN" from the dropdown menu under "photon type."</span></span> <span data-ttu-id="40190-138">Nennen Sie es dann (etwas, das Sie merken würden).</span><span class="sxs-lookup"><span data-stu-id="40190-138">Then give it a name, (something you would remember).</span></span> <span data-ttu-id="40190-139">In diesem Beispiel nennen wir es "hololersphutonproject".</span><span class="sxs-lookup"><span data-stu-id="40190-139">In this example, we named it "HoloLensPhotonProject."</span></span> <span data-ttu-id="40190-140">Wenn Sie fertig sind, klicken Sie auf "erstellen".</span><span class="sxs-lookup"><span data-stu-id="40190-140">Once finished, click "create."</span></span>

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. <span data-ttu-id="40190-142">Sobald dies erfolgt ist, kehren Sie zur Seite "Anwendungen" zurück, und es sollte etwas ähnlich der folgenden Abbildung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="40190-142">Once that is done, return to your applications page and you should see something similar to the picture below.</span></span> <span data-ttu-id="40190-143">Klicken Sie auf die APP-ID, und kopieren Sie Sie.</span><span class="sxs-lookup"><span data-stu-id="40190-143">Click on the app ID and copy it.</span></span> <span data-ttu-id="40190-144">Einfügen ist ein Ort, auf den Sie problemlos zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="40190-144">Paste is somewhere you can easily access.</span></span>  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. <span data-ttu-id="40190-146">Erstellen Sie ein neues Unity-Projekt.</span><span class="sxs-lookup"><span data-stu-id="40190-146">Create a new unity project.</span></span> <span data-ttu-id="40190-147">Öffnen Sie den Unity-Hub, und klicken Sie auf "neu".</span><span class="sxs-lookup"><span data-stu-id="40190-147">Open Unity Hub and click on "new."</span></span> <span data-ttu-id="40190-148">Nennen Sie es "hlsharingproject".</span><span class="sxs-lookup"><span data-stu-id="40190-148">Name it "HLSharingProject."</span></span> <span data-ttu-id="40190-149">Klicken Sie anschließend auf erstellen.</span><span class="sxs-lookup"><span data-stu-id="40190-149">Then click create.</span></span> 

   > <span data-ttu-id="40190-150">Nebenbei Der Ladevorgang kann bis zu 2 Minuten dauern, je nach der Geschwindigkeit Ihres Computers.</span><span class="sxs-lookup"><span data-stu-id="40190-150">note: This can take up to 2 minutes to load, based on your computer's speed.</span></span>

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> <span data-ttu-id="40190-152">Hinweis: Wählen Sie einen Ort aus, an dem das Projekt auf Ihrem Computer gespeichert werden soll, indem Sie die Option "Standort" ändern.</span><span class="sxs-lookup"><span data-stu-id="40190-152">note: pick a place to save your project in your computer by changing the "location" option.</span></span> <span data-ttu-id="40190-153">Speichern Sie Sie an einem Speicherort, den Sie merken werden und für den Sie einfachen Zugriff haben.</span><span class="sxs-lookup"><span data-stu-id="40190-153">Save it to a place you will remember and have easy access to.</span></span>

10. <span data-ttu-id="40190-154">Nachdem das Projekt geladen wurde, klicken Sie auf den "Assets Store".</span><span class="sxs-lookup"><span data-stu-id="40190-154">Once the project loads, click on the "assets store."</span></span> <span data-ttu-id="40190-155">Geben Sie dann im Suchfeld, das in der folgenden Abbildung gezeigt wird, "pun" ein, und wählen Sie das Asset "Photon pun-2 Free" aus.</span><span class="sxs-lookup"><span data-stu-id="40190-155">Then, in the search box shown in the image below, type in "PUN" and select the "Photon PUN-2 FREE" asset.</span></span> 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. <span data-ttu-id="40190-157">Herunterladen und importieren!</span><span class="sxs-lookup"><span data-stu-id="40190-157">Download and import!</span></span>
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a><span data-ttu-id="40190-159">**Einrichten des Unity-Projekts**</span><span class="sxs-lookup"><span data-stu-id="40190-159">**Setting Up the Unity Project**</span></span> 

11. <span data-ttu-id="40190-160">Laden Sie ein neues Asset herunter, das zum Einrichten von Photon in Unity erforderlich ist, indem Sie [hier klicken.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="40190-160">download a new asset needed to set up Photon in Unity by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)</span></span>

12. <span data-ttu-id="40190-161">Klicken Sie in Unity auf das Menü Assets, und wählen Sie "Objekte importieren" aus, und klicken Sie dann auf "benutzerdefinierte Objekte".</span><span class="sxs-lookup"><span data-stu-id="40190-161">In Unity, click on the assets menu and select "import assets," then click on "custom assets."</span></span>

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. <span data-ttu-id="40190-163">Wählen Sie das Unity-Paket aus, das Sie soeben aus dem in Schritt 1 angegebenen Link heruntergeladen haben.</span><span class="sxs-lookup"><span data-stu-id="40190-163">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="40190-164">Wenn die Schaltfläche Importieren in Unity angezeigt wird, klicken Sie darauf.</span><span class="sxs-lookup"><span data-stu-id="40190-164">Once the import button appears in Unity, click it.</span></span>

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> <span data-ttu-id="40190-166">Hinweis: Wenn Sie das Paket heruntergeladen haben, finden Sie es dort, wo Sie es finden.</span><span class="sxs-lookup"><span data-stu-id="40190-166">note: wherever you downloaded the package to will be where you find it.</span></span> <span data-ttu-id="40190-167">In der Abbildung oben wird nicht dargestellt, wo Sie das Paket finden.</span><span class="sxs-lookup"><span data-stu-id="40190-167">The image above does not portray where you will find the package.</span></span>

14. <span data-ttu-id="40190-168">Erstellen Sie eine neue Szene (Dies kann mithilfe von Control/Command + N oder durch Klicken auf "Datei" und "neue Szene" erfolgen.)</span><span class="sxs-lookup"><span data-stu-id="40190-168">Create a new scene (this can be done using control/command+N or by clicking "file" and selecting "new scene.").</span></span> <span data-ttu-id="40190-169">Speichern Sie die Szene als "hlsharedprojectmain".</span><span class="sxs-lookup"><span data-stu-id="40190-169">Save the scene as "HLSharedProjectMain."</span></span>

> <span data-ttu-id="40190-170">Hinweis: Sie erhalten möglicherweise ein Popup, das ähnlich wie in der folgenden Abbildung aussieht.</span><span class="sxs-lookup"><span data-stu-id="40190-170">note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="40190-171">Klicken Sie vorerst einfach auf "Nein".</span><span class="sxs-lookup"><span data-stu-id="40190-171">For now, just click "no."</span></span>
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. <span data-ttu-id="40190-173">Klicken Sie unter "Mixed Reality Toolkit" auf "zu Szene hinzufügen und konfigurieren".</span><span class="sxs-lookup"><span data-stu-id="40190-173">Under "Mixed Reality Toolkit" click on "add to scene and configure."</span></span>

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. <span data-ttu-id="40190-175">Sobald der Vorgang beendet ist, wird eine neue Konfigurationsdatei angezeigt, die Ihnen die Möglichkeit gibt, das Profil anzupassen.</span><span class="sxs-lookup"><span data-stu-id="40190-175">Once that is complete, a new configuration file will appear, giving you the choice to customize the profile.</span></span> <span data-ttu-id="40190-176">Klicken Sie auf "Kopieren und anpassen".</span><span class="sxs-lookup"><span data-stu-id="40190-176">Click "copy and customize."</span></span>

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. <span data-ttu-id="40190-178">Scrollen Sie nach unten, und deaktivieren Sie die Option "Diagnosesystem aktivieren".</span><span class="sxs-lookup"><span data-stu-id="40190-178">Scroll down and uncheck "enable diagnostics system."</span></span> <span data-ttu-id="40190-179">Dadurch wird die Einrichtung dieses Projekts vereinfacht.</span><span class="sxs-lookup"><span data-stu-id="40190-179">This will make it easier to set up this project.</span></span>

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. <span data-ttu-id="40190-181">Öffnen Sie die Buildeinstellungen (Control + Shift + B).</span><span class="sxs-lookup"><span data-stu-id="40190-181">Open the build settings (control+shift+B).</span></span> <span data-ttu-id="40190-182">Beachten Sie, dass das Programm derzeit auf der Plattform "PC, Mac und Linux Standalone" festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="40190-182">Notice that the program is currently set under the "PC, Mac and Linux standalone" platform.</span></span> <span data-ttu-id="40190-183">Legen Sie für dieses Projekt die Plattform auf "universelle Windows-Plattform" fest.</span><span class="sxs-lookup"><span data-stu-id="40190-183">For this project, set the platform to be "universal windows platform."</span></span> <span data-ttu-id="40190-184">Wählen Sie diese Option aus, und klicken Sie auf Plattform wechseln.</span><span class="sxs-lookup"><span data-stu-id="40190-184">Select it and click "switch platform."</span></span>

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. <span data-ttu-id="40190-186">Wenn Sie fertig sind, klicken Sie auf das Feld "offene Szenen hinzufügen".</span><span class="sxs-lookup"><span data-stu-id="40190-186">Once complete, click the box that says "add open scenes."</span></span> <span data-ttu-id="40190-187">Wechseln Sie nun zum Bereich Inspector, und stellen Sie sicher, dass das Kontrollkästchen rechts neben "unterstützte virtuelle Realität" (wie in der folgenden Abbildung gezeigt) aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="40190-187">Now go to the inspector panel and ensure that the check box to the right of "virtual reality supported" (as shown in the image below) is checked.</span></span> 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> <span data-ttu-id="40190-189">Nebenbei Stellen Sie außerdem sicher, dass das Kontrollkästchen neben "Szenen/hlsharedprojectmain" ebenfalls aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="40190-189">note: Also ensure that the check box next to "scenes/HLSharedProjectMain" is also checked.</span></span>

20. <span data-ttu-id="40190-190">Scrollen Sie im Inspektor-Panel unter "Veröffentlichungs Einstellungen" nach unten zu "Funktionen", und stellen Sie sicher, dass nur die folgenden Kontrollkästchen markiert sind:</span><span class="sxs-lookup"><span data-stu-id="40190-190">Under the "publishing settings" in the inspector panel scroll down to "capabilities" and ensure only the following check boxes are marked:</span></span>

- <span data-ttu-id="40190-191">Internet Client</span><span class="sxs-lookup"><span data-stu-id="40190-191">internet client</span></span>
- <span data-ttu-id="40190-192">Internet Client Server</span><span class="sxs-lookup"><span data-stu-id="40190-192">internet client server</span></span>
- <span data-ttu-id="40190-193">privater Netzwerkclient Server</span><span class="sxs-lookup"><span data-stu-id="40190-193">private network client server</span></span>
- <span data-ttu-id="40190-194">Kamera/Webcam</span><span class="sxs-lookup"><span data-stu-id="40190-194">camera/webcam</span></span>
- <span data-ttu-id="40190-195">Mikrofon</span><span class="sxs-lookup"><span data-stu-id="40190-195">microphone</span></span>

21. <span data-ttu-id="40190-196">Ebenso wie bei Schritt 12 wäre der nächste Schritt das Importieren eines weiteren benutzerdefinierten Pakets namens "Lesson2", das hier heruntergeladen werden kann. [Lesson2. unitypackage-Link hier einfügen] Importieren Sie das Paket.</span><span class="sxs-lookup"><span data-stu-id="40190-196">Just like step 12, the next step would be to import another custom package called "Lesson2" which can be downloaded [here.][lesson2.unitypackage link goes here] Import that package.</span></span>

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. <span data-ttu-id="40190-198">Wechseln Sie nun im Projekt Panel zum Ordner "Prefabs", denn in den nächsten Schritten werden Sie einige Prefabs in der Szene implementieren.</span><span class="sxs-lookup"><span data-stu-id="40190-198">Now, in the project panel, go to the "prefabs" folder, since in next few steps you will be implementing a few prefabs into the scene.</span></span> <span data-ttu-id="40190-199">Klicken Sie im Ordner "Prefabs" auf die Prefab-"debugWindow"-Komponente, und ziehen Sie Sie in die Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="40190-199">In the "prefabs" folder, click and drag the prefab, "DebugWindow" into the hierarchy.</span></span> <span data-ttu-id="40190-200">Wenn Sie fertig sind, speichern Sie das Projekt (Klicken Sie auf Datei, dann auf Speichern oder auf + S).</span><span class="sxs-lookup"><span data-stu-id="40190-200">Once finished, save the project (click file, then save, or control+S)</span></span>

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> <span data-ttu-id="40190-202">Nebenbei Sie werden möglicherweise feststellen, dass ein Popup Fenster angezeigt wird, wenn Sie auf die vorfab klicken und Sie zu tmp Essentials auffordern.</span><span class="sxs-lookup"><span data-stu-id="40190-202">note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="40190-203">Klicken Sie auf "tmp Essentials importieren", wenn Sie benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="40190-203">Click "Import TMP Essentials" as they will be needed.</span></span>
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a><span data-ttu-id="40190-205">**Verbinden von mehreren Benutzern**</span><span class="sxs-lookup"><span data-stu-id="40190-205">**Connecting Multiple Users**</span></span>

23. <span data-ttu-id="40190-206">Der nächste Schritt besteht im Ordner "Prefabs" im Projekt Panel darin, die vorfab "networklobby" per Drag & amp; Drop in die Hierarchie zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="40190-206">Like step 22, in the "prefabs" folder in the project panel, the next step is to drag and drop the "NetworkLobby" prefab in to the hierarchy.</span></span> 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. <span data-ttu-id="40190-208">Wenn Sie die übergeordnete Prefab "networklobby" öffnen, sollte eine untergeordnete vorfab angezeigt werden, "Network Room".</span><span class="sxs-lookup"><span data-stu-id="40190-208">When you open up the parent prefab, "NetworkLobby," you should see a child prefab, "NetworkRoom."</span></span> <span data-ttu-id="40190-209">Wenn diese Option ausgewählt ist, wechseln Sie im Inspektor-Panel, und klicken Sie auf "Komponente hinzufügen".</span><span class="sxs-lookup"><span data-stu-id="40190-209">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="40190-210">Suchen Sie nach "photonview", und fügen Sie die Komponente hinzu.</span><span class="sxs-lookup"><span data-stu-id="40190-210">Search for "PhotonView" and add the component.</span></span>

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. <span data-ttu-id="40190-212">Erstellen Sie ein neues leeres Spielobjekt in der Hierarchie (Klicken Sie mit der rechten Maustaste in die Hierarchie, und wählen Sie "Empty"</span><span class="sxs-lookup"><span data-stu-id="40190-212">Create a new empty game object in the hierarchy (right click in the hierarchy and select "empty").</span></span> <span data-ttu-id="40190-213">Stellen Sie sicher, dass die Positionierung auf x = 0, y = 0, z = 0 festgelegt ist, und benennen Sie das Objekt "photonuser".</span><span class="sxs-lookup"><span data-stu-id="40190-213">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a><span data-ttu-id="40190-215">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="40190-215">Congratulations</span></span>



