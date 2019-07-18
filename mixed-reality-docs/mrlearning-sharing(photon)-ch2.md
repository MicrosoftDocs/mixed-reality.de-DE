### <a name="getting-unity-ready-for-development"></a><span data-ttu-id="63d1f-101">Vorbereiten von Unity für die Entwicklung</span><span class="sxs-lookup"><span data-stu-id="63d1f-101">Getting Unity ready for development</span></span> 


<span data-ttu-id="63d1f-102">In diesem Tutorial erfahren Sie, wie Sie Unity für die Anwendungsentwicklung vorbereiten und konfigurieren, einschließlich Importieren des Mixed Reality Toolkit, Konfigurieren von Buildeinstellungen und vorbereiten unserer Szene.</span><span class="sxs-lookup"><span data-stu-id="63d1f-102">In this tutorial, we learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

<span data-ttu-id="63d1f-103">Ziele</span><span class="sxs-lookup"><span data-stu-id="63d1f-103">Objectives:</span></span>

- <span data-ttu-id="63d1f-104">Konfigurieren von Unity für die Anwendungsentwicklung</span><span class="sxs-lookup"><span data-stu-id="63d1f-104">Configure Unity for application development</span></span>

- <span data-ttu-id="63d1f-105">Importieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="63d1f-105">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="63d1f-106">Vorbereiten der Projekt Szene</span><span class="sxs-lookup"><span data-stu-id="63d1f-106">Prepare your project scene</span></span>

### <a name="instructions"></a><span data-ttu-id="63d1f-107">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="63d1f-107">Instructions</span></span>

1. <span data-ttu-id="63d1f-108">Klicken Sie hier, um das Unity-Paket für Mixed Reality Toolkit herunterzuladen und zu speichern [.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="63d1f-108">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span></span>

2. <span data-ttu-id="63d1f-109">Klicken Sie in Unity auf das Menü Assets, und wählen Sie Paket importieren aus, und klicken Sie dann auf benutzerdefiniertes Paket.</span><span class="sxs-lookup"><span data-stu-id="63d1f-109">In Unity, click on the assets menu and select Import Package, then click on Custom Package.</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="63d1f-111">Wählen Sie das Unity-Paket aus, das Sie soeben aus dem in Schritt 1 angegebenen Link heruntergeladen haben.</span><span class="sxs-lookup"><span data-stu-id="63d1f-111">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="63d1f-112">Nachdem das Popup Fenster Importieren in Unity angezeigt wird, klicken Sie auf die Schaltfläche Importieren, um den Import Vorgang zu starten.</span><span class="sxs-lookup"><span data-stu-id="63d1f-112">Once the import pop-up window appears in Unity, click the Import button to begin importing.</span></span> <span data-ttu-id="63d1f-113">Das Importieren der mrtk kann einige Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="63d1f-113">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="63d1f-115">Hinweis: Das heruntergeladene Paket befindet sich in Ihrem lokalen Ordner, in dem Sie die Datei gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="63d1f-115">Note: The downloaded package is in your local folder where you have saved the file.</span></span> <span data-ttu-id="63d1f-116">In der Abbildung oben wird nicht dargestellt, wo Sie das Paket finden.</span><span class="sxs-lookup"><span data-stu-id="63d1f-116">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="63d1f-117">Erstellen Sie eine neue Szene.</span><span class="sxs-lookup"><span data-stu-id="63d1f-117">Create a new scene.</span></span> <span data-ttu-id="63d1f-118">Klicken Sie hierzu auf Datei und dann auf neue Szene ").</span><span class="sxs-lookup"><span data-stu-id="63d1f-118">This can be done by clicking File, and selecting New Scene").</span></span> <span data-ttu-id="63d1f-119">Speichern Sie die Szene als hlsharedprojectmain.</span><span class="sxs-lookup"><span data-stu-id="63d1f-119">Save the scene as HLSharedProjectMain.</span></span>

> <span data-ttu-id="63d1f-120">Hinweis: Sie erhalten möglicherweise ein Popup, das ähnlich wie in der folgenden Abbildung aussieht.</span><span class="sxs-lookup"><span data-stu-id="63d1f-120">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="63d1f-121">Klicken Sie vorerst auf Nein.</span><span class="sxs-lookup"><span data-stu-id="63d1f-121">For now, click No.</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="63d1f-123">Klicken Sie unter Mixed Reality Toolkit auf zur Szene hinzufügen und konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="63d1f-123">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="63d1f-125">Sobald der Vorgang beendet ist, wird eine neue Konfigurationsdatei angezeigt, die Ihnen die Möglichkeit gibt, das Profil anzupassen.</span><span class="sxs-lookup"><span data-stu-id="63d1f-125">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span> <span data-ttu-id="63d1f-126">Klicken Sie auf Kopieren und anpassen.</span><span class="sxs-lookup"><span data-stu-id="63d1f-126">Click Copy and Customize.</span></span>

![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. <span data-ttu-id="63d1f-130">Scrollen Sie nach unten, und deaktivieren Sie Diagnosesystem aktivieren, wenn Sie das Diagnosefenster ausblenden möchten.</span><span class="sxs-lookup"><span data-stu-id="63d1f-130">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="63d1f-131">Es wird empfohlen, das Diagnosefenster während der Anwendungsentwicklung zu aktivieren, um die Leistung zu überwachen und während der Produktions-oder Anwendungs Demos zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="63d1f-131">We recommend keeping the diagnostics window enabled during application development to monitor performance, and disabling it during production or application demonstrations.</span></span> 

![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. <span data-ttu-id="63d1f-133">Öffnen Sie die Buildeinstellungen, indem Sie STRG + UMSCHALT + B drücken, oder wechseln Sie zu Datei > Buildeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="63d1f-133">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="63d1f-134">Beachten Sie, dass das Programm derzeit unter der eigenständigen PC-, Mac-und Linux-Plattform festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="63d1f-134">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="63d1f-135">Legen Sie für die Entwicklung von hololens 2 die Plattform auf universelle Windows-Plattform fest.</span><span class="sxs-lookup"><span data-stu-id="63d1f-135">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="63d1f-136">Wählen Sie es aus, und klicken Sie auf Plattform wechseln.</span><span class="sxs-lookup"><span data-stu-id="63d1f-136">Select it and click Switch Platform.</span></span>

![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. <span data-ttu-id="63d1f-138">Klicken Sie nach Abschluss des Vorgangs auf das Feld mit dem Text hinzufügen offener Szenen.</span><span class="sxs-lookup"><span data-stu-id="63d1f-138">Once complete, click the box that says Add Open Scenes.</span></span> <span data-ttu-id="63d1f-139">Wechseln Sie nun zum Inspektor-Panel, und stellen Sie sicher, dass das Kontrollkästchen rechts von Virtual Reality unterstützt wird (wie in der folgenden Abbildung dargestellt).</span><span class="sxs-lookup"><span data-stu-id="63d1f-139">Now go to the Inspector panel, and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="63d1f-140">Stellen Sie außerdem sicher, dass das Kontrollkästchen nebenszenen/hlsharedprojectmain ebenfalls aktiviert ist, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="63d1f-140">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked as shown in the image below.</span></span>

![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. <span data-ttu-id="63d1f-142">Scrollen Sie im Bereich Inspector im Bereich Veröffentlichungs Einstellungen nach unten zu Funktionen, und stellen Sie sicher, dass die folgenden Kontrollkästchen markiert sind:</span><span class="sxs-lookup"><span data-stu-id="63d1f-142">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities, and ensure the following check boxes are marked:</span></span>

![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. <span data-ttu-id="63d1f-144">Importieren Sie das benutzerdefinierte Paket namens sharingassetcollection, das [hier](https://github.com/microsoft/MixedRealityLearning/releases/tag/development) heruntergeladen werden kann.</span><span class="sxs-lookup"><span data-stu-id="63d1f-144">Import the custom package called SharingAssetCollection which can be downloaded [here.](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)</span></span>

![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. <span data-ttu-id="63d1f-146">Wechseln Sie im Projekt Panel zum Ordner Prefabs.</span><span class="sxs-lookup"><span data-stu-id="63d1f-146">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="63d1f-147">In den nächsten Schritten implementieren Sie ein paar Prefabs in der Szene.</span><span class="sxs-lookup"><span data-stu-id="63d1f-147">In next few steps you implement a few prefabs into the scene.</span></span> <span data-ttu-id="63d1f-148">Klicken Sie im Ordner Prefabs auf das Fenster Prefab, Debug, und ziehen Sie es in die Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="63d1f-148">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="63d1f-149">Wenn Sie fertig sind, speichern Sie das Projekt, indem Sie auf Datei und dann auf Speichern klicken oder STRG + S drücken.</span><span class="sxs-lookup"><span data-stu-id="63d1f-149">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > <span data-ttu-id="63d1f-151">Hinweis: Sie werden möglicherweise feststellen, dass ein Popup Fenster angezeigt wird, wenn Sie auf die vorfab klicken und Sie zu tmp Essentials auffordern.</span><span class="sxs-lookup"><span data-stu-id="63d1f-151">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="63d1f-152">Klicken Sie auf tmp Essentials nach Bedarf importieren.</span><span class="sxs-lookup"><span data-stu-id="63d1f-152">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="63d1f-153">Wenn dieses Popup Fenster angezeigt wird, müssen Sie möglicherweise die vorfab aus Ihrer Hierarchie löschen und in ihre Hierarchie ziehen, um potenzielle Text bezogene Fehler zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="63d1f-153">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
>![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="63d1f-155">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="63d1f-155">Congratulations</span></span>

<span data-ttu-id="63d1f-156">Ihr Unity-Projekt ist nun für das Photon bereit.</span><span class="sxs-lookup"><span data-stu-id="63d1f-156">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="63d1f-157">In den nächsten Tutorials bauen wir auf dieser Szene und unserem Unity-Projekt auf, um eine vollständige gemeinsame Nutzung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="63d1f-157">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="63d1f-158">[Nächstes Tutorial: Verbinden mehrerer Benutzer](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="63d1f-158">[Next tutorial: Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>

