# <a name="getting-unity-ready-for-development"></a><span data-ttu-id="3b480-101">Vorbereitung von Unity für die Entwicklung</span><span class="sxs-lookup"><span data-stu-id="3b480-101">Getting Unity ready for development</span></span> 

<span data-ttu-id="3b480-102">In diesem Tutorial haben wir Informationen zum Vorbereiten und Konfigurieren von Unity für die Entwicklung von Anwendungen, wie z.B. das Mixed Reality-Toolkit importieren und Konfigurieren von Buildeinstellungen unsere Szene wird vorbereitet.</span><span class="sxs-lookup"><span data-stu-id="3b480-102">In this tutorial, we learn how to prepare and configure Unity for applicaiton development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing our scene.</span></span>

<span data-ttu-id="3b480-103">Ziele:</span><span class="sxs-lookup"><span data-stu-id="3b480-103">Objectives:</span></span>

- <span data-ttu-id="3b480-104">Konfigurieren von Unity für die Anwendungsentwicklung</span><span class="sxs-lookup"><span data-stu-id="3b480-104">Configure Unity for applicaiton development</span></span>

- <span data-ttu-id="3b480-105">Importieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="3b480-105">Import the Mixed Reality Toolkit</span></span>

- <span data-ttu-id="3b480-106">Vorbereiten Sie Ihrer Projekt-Szene</span><span class="sxs-lookup"><span data-stu-id="3b480-106">Prepare your project scene</span></span>

### <a name="instructions"></a><span data-ttu-id="3b480-107">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="3b480-107">Instructions</span></span>

1. <span data-ttu-id="3b480-108">Herunterladen und speichern Sie die Mixed Reality-Toolkit Unity-Paket, indem Sie auf [hier.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="3b480-108">Download and save the Mixed Reality Toolkit unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)</span></span>
2. <span data-ttu-id="3b480-109">Klicken Sie auf das Menü "Assets" in Unity wählen Sie Paket importieren, und klicken Sie auf das benutzerdefinierte Paket.</span><span class="sxs-lookup"><span data-stu-id="3b480-109">In Unity, click on the assets menu and select Import Package, then click on Custom Package.</span></span>

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="3b480-111">Wählen Sie das Unity-Paket, die, das Sie gerade heruntergeladen, über den Link in Schritt 1 bereitgestellt haben.</span><span class="sxs-lookup"><span data-stu-id="3b480-111">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="3b480-112">Wenn das Popup-Fenster Importieren in Unity angezeigt wird, klicken Sie auf die Schaltfläche "Importieren", um Import zu starten.</span><span class="sxs-lookup"><span data-stu-id="3b480-112">Once the import pop-up window appears in Unity, click the Import button to begin importing.</span></span> <span data-ttu-id="3b480-113">Importieren die MRTK kann mehrere Minuten dauern.</span><span class="sxs-lookup"><span data-stu-id="3b480-113">Importing the MRTK may take several minutes.</span></span>

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> <span data-ttu-id="3b480-115">Hinweis: Das heruntergeladene Paket ist im lokalen Ordner, in dem Sie die Datei gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="3b480-115">Note: The downloaded package is in your local folder where you have saved the file.</span></span> <span data-ttu-id="3b480-116">In der Abbildung oben ist nicht darstellen, in dem Sie das Paket finden.</span><span class="sxs-lookup"><span data-stu-id="3b480-116">The image above does not portray where you will find the package.</span></span>

4. <span data-ttu-id="3b480-117">Erstellen Sie eine neue Szene.</span><span class="sxs-lookup"><span data-stu-id="3b480-117">Create a new scene.</span></span> <span data-ttu-id="3b480-118">%TDer möglich durch Klicken auf die Datei, und neue Szene auswählen").</span><span class="sxs-lookup"><span data-stu-id="3b480-118">Tthis can be done by clicking File, and selecting New Scene").</span></span> <span data-ttu-id="3b480-119">Speichern Sie die Szene HLSharedProjectMain.</span><span class="sxs-lookup"><span data-stu-id="3b480-119">Save the scene as HLSharedProjectMain.</span></span>

> <span data-ttu-id="3b480-120">Hinweis: wird möglicherweise ein Popupfenster angezeigt, die in der folgenden Abbildung ähneln.</span><span class="sxs-lookup"><span data-stu-id="3b480-120">Note: you may receive a pop-up that looks similar to the image below.</span></span> <span data-ttu-id="3b480-121">Jetzt klicken Sie auf Nein.</span><span class="sxs-lookup"><span data-stu-id="3b480-121">For now, click No.</span></span>
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. <span data-ttu-id="3b480-123">Klicken Sie unter dem Mixed Reality-Toolkit auf Hinzufügen, um der Szene "und" konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="3b480-123">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="3b480-125">Sobald dies abgeschlossen ist, wird eine neue Konfigurationsdatei, bietet Ihnen die Möglichkeit, die das Profil anzupassen.</span><span class="sxs-lookup"><span data-stu-id="3b480-125">Once that is complete, a new configuration file appears, giving you the choice to customize the profile.</span></span> <span data-ttu-id="3b480-126">Klicken Sie auf Kopieren und anpassen.</span><span class="sxs-lookup"><span data-stu-id="3b480-126">Click Copy and Customize.</span></span>

   ![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

   ![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

   ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. <span data-ttu-id="3b480-130">Scrollen Sie nach unten, und aktivieren Siagnostics System deaktivieren Sie, wenn Sie das Diagnosefenster ausblenden möchten.</span><span class="sxs-lookup"><span data-stu-id="3b480-130">Scroll down and uncheck Enable Siagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="3b480-131">Wir empfehlen die Diagnostics-Fenster, während der Anwendungsentwicklung für die Leistungsüberwachung aktiviert und während der Produktion oder Anwendung Demos deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="3b480-131">We recommend keeping the diagnostics window enabled during applicaiton development to monitor performance, and disabling it during production or application demonstrations.</span></span> 

   ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. <span data-ttu-id="3b480-133">Öffnen Sie die Einstellungen der Buildkonfiguration durch Drücken von STRG + UMSCHALT + B oder die Datei-Buildeinstellungen >.</span><span class="sxs-lookup"><span data-stu-id="3b480-133">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="3b480-134">Beachten Sie, dass das Programm derzeit unter der PC, Mac und Linux eigenständige Plattform festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="3b480-134">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="3b480-135">Legen Sie für die Entwicklung für HoloLens 2 die universelle Windows-Plattform-Plattform.</span><span class="sxs-lookup"><span data-stu-id="3b480-135">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="3b480-136">Wählen sie aus, und klicken Sie auf die Plattform wechseln.</span><span class="sxs-lookup"><span data-stu-id="3b480-136">Select it and click Switch Platform.</span></span>![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. <span data-ttu-id="3b480-138">Nach Abschluss des Vorgangs, klicken Sie im Feld Öffnen Szenen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="3b480-138">Once complete, click the box that says Add Open Scenes.</span></span> <span data-ttu-id="3b480-139">Nun wechseln Sie zum Bedienfeld "Inspector", und stellen Sie sicher, dass das Kontrollkästchen rechts neben virtuelle Realität unterstützt (wie in der folgenden Abbildung gezeigt) aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="3b480-139">Now go to the Inspector panel, and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="3b480-140">Stellen Sie außerdem sicher, dass Sie das Kontrollkästchen neben den Szenen/HLSharedProjectMain ebenfalls aktiviert ist, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="3b480-140">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked as shown in the image below.</span></span>![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. <span data-ttu-id="3b480-142">Wählen Sie im Abschnitt "Veröffentlichungseinstellungen" im Bereich Inspektor Funktionen scrollen, und stellen Sie sicher, dass die folgenden Kontrollkästchen markiert sind:</span><span class="sxs-lookup"><span data-stu-id="3b480-142">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities, and ensure the following check boxes are marked:</span></span>![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. <span data-ttu-id="3b480-144">Importieren Sie das benutzerdefinierte Paket namens SharingAssetCollection die heruntergeladen werden kann [hier.](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage) ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)</span><span class="sxs-lookup"><span data-stu-id="3b480-144">Import the custom package called SharingAssetCollection which can be downloaded [here.](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage)![Module3Chapter2step12im](images/module3chapter2step11im.PNG)</span></span>

12. <span data-ttu-id="3b480-145">Der Projektbereich wechseln Sie zum Ordner "Prefabs".</span><span class="sxs-lookup"><span data-stu-id="3b480-145">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="3b480-146">In den nächsten Schritten implementieren Sie ein paar prefabs (Vorlagen) in der Szene.</span><span class="sxs-lookup"><span data-stu-id="3b480-146">In next few steps you implement a few prefabs into the scene.</span></span> <span data-ttu-id="3b480-147">Klicken Sie im Ordner "Prefabs" klicken Sie auf, und ziehen Sie das Prefab, DebugWindow in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="3b480-147">In the Prefabs folder, click and drag the prefab, DebugWindow into the hierarchy.</span></span> <span data-ttu-id="3b480-148">Sobald Sie fertig sind, speichern Sie das Projekt von Clckin-Datei, und klicken Sie dann speichern Sie, oder drücken Sie STRG + S +.</span><span class="sxs-lookup"><span data-stu-id="3b480-148">Once finished, save the project by clckin File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > <span data-ttu-id="3b480-150">Hinweis: Sie werden feststellen, dass ein Popupfenster angezeigt, wenn Sie auf das Prefab klicken TMP Essentials gefragt.</span><span class="sxs-lookup"><span data-stu-id="3b480-150">Note: You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="3b480-151">Klicken Sie auf Importieren TMP Essentials, wie sie benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="3b480-151">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="3b480-152">Wenn dieses Popupfenster angezeigt wird, müssen Sie möglicherweise das Prefab in Ihrer Hierarchie zu löschen, und ziehen es erneut in Ihrer Hierarchie aus, um mögliche Fehler in Bezug auf Text zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="3b480-152">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a><span data-ttu-id="3b480-154">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="3b480-154">Congratulations</span></span>

<span data-ttu-id="3b480-155">Ihr Unity-Projekt ist jetzt für Photon bereit.</span><span class="sxs-lookup"><span data-stu-id="3b480-155">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="3b480-156">In den folgenden Tutorials erstellen wir auf diese Szene und unsere Unity-Projekt für eine umfassende freigegebenen Umgebung.</span><span class="sxs-lookup"><span data-stu-id="3b480-156">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="3b480-157">[Nächsten Lernprogramm: Verbinden von mehreren Benutzern](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="3b480-157">[Next tutorial: Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>

