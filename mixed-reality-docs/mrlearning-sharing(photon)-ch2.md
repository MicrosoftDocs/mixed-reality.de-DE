---
title: 'Tutorials zu Mehrbenutzerfunktionen: 2 Vorbereiten von Unity für die Entwicklung'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: f7ae77d6978b5da860d890bcfe5b6f7c3d4640c8
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031238"
---
# <a name="2-getting-unity-ready-for-development"></a><span data-ttu-id="40a5f-105">2. Vorbereiten von Unity für die Entwicklung</span><span class="sxs-lookup"><span data-stu-id="40a5f-105">2. Getting Unity ready for development</span></span>

<span data-ttu-id="40a5f-106">In diesem Tutorial erfahren Sie, wie Sie Unity für die Anwendungsentwicklung vorbereiten und konfigurieren, einschließlich des Importierens des Mixed Reality-Toolkits, des Konfigurierens von Buildeinstellungen und des Vorbereitens der Szene.</span><span class="sxs-lookup"><span data-stu-id="40a5f-106">In this tutorial, you will learn how to prepare and configure Unity for application development, including importing the Mixed Reality Toolkit, configuring build settings, and preparing your scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="40a5f-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="40a5f-107">Objectives</span></span>

* <span data-ttu-id="40a5f-108">Konfigurieren von Unity für die Anwendungsentwicklung</span><span class="sxs-lookup"><span data-stu-id="40a5f-108">Configure Unity for application development</span></span>
* <span data-ttu-id="40a5f-109">Importieren des Mixed Reality-Toolkits</span><span class="sxs-lookup"><span data-stu-id="40a5f-109">Import the Mixed Reality Toolkit</span></span>
* <span data-ttu-id="40a5f-110">Vorbereiten Ihrer Projektszene</span><span class="sxs-lookup"><span data-stu-id="40a5f-110">Prepare your project scene</span></span>

## <a name="instructions"></a><span data-ttu-id="40a5f-111">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="40a5f-111">Instructions</span></span>

1. <span data-ttu-id="40a5f-112">Laden Sie das Mixed Reality Toolkit Foundation-Unity-Paket herunter, und speichern Sie es, indem Sie [hier](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage) klicken.</span><span class="sxs-lookup"><span data-stu-id="40a5f-112">Download and save the Mixed Reality Toolkit Foundation unity package by clicking [here.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)</span></span>

2. <span data-ttu-id="40a5f-113">Klicken Sie in Unity auf das Assets-Menü, wählen Sie „Import Package“ (Paket importieren) aus, und klicken Sie dann auf „Custom Package“ (Benutzerdefiniertes Paket).</span><span class="sxs-lookup"><span data-stu-id="40a5f-113">In Unity, click the Assets menu and select Import Package, then click on Custom Package.</span></span>

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. <span data-ttu-id="40a5f-115">Wählen Sie das Unity-Paket aus, das Sie soeben über den in Schritt 1 angegebenen Link heruntergeladen haben.</span><span class="sxs-lookup"><span data-stu-id="40a5f-115">Select the Unity package you just downloaded from the link provided in step 1.</span></span> <span data-ttu-id="40a5f-116">Wenn das Popupfenster „Importieren“ in Unity angezeigt wird, klicken Sie auf die Schaltfläche „Importieren“, um mit dem Importieren des MRTK zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="40a5f-116">Once the import pop-up window appears in Unity, click the Import button to begin importing the MRTK.</span></span> <span data-ttu-id="40a5f-117">Dieser Vorgang kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="40a5f-117">This may take several minutes.</span></span>

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="40a5f-119">Das heruntergeladene Paket befindet sich in Ihrem lokalen Ordner, in dem Sie die Datei gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="40a5f-119">The downloaded package is in your local folder, where you have saved the file.</span></span> <span data-ttu-id="40a5f-120">Die Abbildung oben ist keine wahrheitsgemäße Darstellung des Speicherorts des Pakets.</span><span class="sxs-lookup"><span data-stu-id="40a5f-120">The image above does not portray where you will find the package.</span></span>

    <span data-ttu-id="40a5f-121">Nachdem das Paket importiert wurde, sollte das MRTK Project Configurator-Fenster (MRTK-Projektkonfiguration) angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="40a5f-121">After the package has been imported, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="40a5f-122">Wenn das nicht der Fall ist, öffnen Sie es, indem Sie im Unity-Menü „Mixed Reality Toolkit > Utilities > Configure Unity Project“ (Mixed Reality-Toolkit > Utilitys > Unity-Projekt konfigurieren) auswählen.</span><span class="sxs-lookup"><span data-stu-id="40a5f-122">If it does not, open it by selecting Mixed Reality Toolkit > Utilities > Configure Unity Project in the Unity menu.</span></span>

    <span data-ttu-id="40a5f-123">Erweitern Sie im MRTK Project Configurator-Fenster den Abschnitt „Modify Configurations“ (Konfigurationen ändern), deaktivieren Sie das Kontrollkästchen „Enable MSBuild for Unity“ (MSBuild für Unity aktivieren), achten Sie darauf, dass alle anderen Optionen aktiviert sind, und klicken Sie auf die Schaltfläche „Apply“ (Übernehmen), um die Einstellungen zu übernehmen.</span><span class="sxs-lookup"><span data-stu-id="40a5f-123">In the MRTK Project Configurator window, expand the Modify Configurations section, uncheck the Enable MSBuild for Unity checkbox, ensure all other options are checked, and click the Apply button to apply the settings.</span></span>

    ![Module3Chapter2note1im](images/module3chapter2note1im-missing01.png)

    > [!CAUTION]
    > <span data-ttu-id="40a5f-125">MSBuild für Unity unterstützt möglicherweise nicht alle verwenden SDKs, und die Deaktivierung nach der erstmaligen Aktivierung kann schwierig sein.</span><span class="sxs-lookup"><span data-stu-id="40a5f-125">MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="40a5f-126">Es wird daher dringend empfohlen, MSBuild für Unity nicht zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="40a5f-126">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>
    
4. <span data-ttu-id="40a5f-127">Erstellen Sie eine neue Szene.</span><span class="sxs-lookup"><span data-stu-id="40a5f-127">Create a new scene.</span></span> <span data-ttu-id="40a5f-128">Sie können hierzu auf „Datei“ klicken und „Neue Szene“ auswählen.</span><span class="sxs-lookup"><span data-stu-id="40a5f-128">This can be done by clicking File and selecting New Scene".</span></span> <span data-ttu-id="40a5f-129">Speichern Sie sie als HLSharedProjectMain.</span><span class="sxs-lookup"><span data-stu-id="40a5f-129">Save it as HLSharedProjectMain.</span></span>

5. <span data-ttu-id="40a5f-130">Klicken Sie unter Mixed Reality-Toolkit auf „Zur Szene hinzufügen und konfigurieren“.</span><span class="sxs-lookup"><span data-stu-id="40a5f-130">Under Mixed Reality Toolkit, click on Add to Scene and Configure.</span></span>

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. <span data-ttu-id="40a5f-132">Sobald das erledigt ist, wählen Sie in der Hierarchie „Mixed-Reality Toolkit (MRTK)“ aus.</span><span class="sxs-lookup"><span data-stu-id="40a5f-132">Once that is complete, select Mixed-Reality Toolkit (MRTK) from the hierarchy.</span></span> <span data-ttu-id="40a5f-133">Ändern Sie im Inspektorbereich das MRTK-Konfigurationsprofil in DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="40a5f-133">In the inspector panel, change the MRTK configuration profile to DefaultHoloLens2ConfigurationProfile.</span></span>

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima-missing01.png)

7. <span data-ttu-id="40a5f-135">Wählen Sie in der Hierarchie „Mixed Reality-Toolkit (MRTK)“ aus.</span><span class="sxs-lookup"><span data-stu-id="40a5f-135">Select Mixed-Reality Toolkit (MRTK) from the  hierarchy.</span></span> <span data-ttu-id="40a5f-136">Suchen Sie im Inspektorbereich nach dem Mixed Reality-Toolkitskript, und wählen Sie die Schaltfläche „Copy & Customize“ (Kopieren und anpassen) aus, wie in der Abbildung unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="40a5f-136">In the inspector panel, look for the Mixed Reality Toolkit Script and press the "Copy & Customize" button  as shown in the figure below.</span></span>  <span data-ttu-id="40a5f-137">Darauf hin wird ein Pop angezeigt, und Sie können im Popupmenü eine Klonoption auswählen.</span><span class="sxs-lookup"><span data-stu-id="40a5f-137">A pop will appear after this and select clone option in the pop up menu.</span></span>

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. <span data-ttu-id="40a5f-140">Scrollen Sie nach unten, und deaktivieren Sie „Enable Diagnostics-System“, wenn Sie das Diagnosefenster ausblenden möchten.</span><span class="sxs-lookup"><span data-stu-id="40a5f-140">Scroll down and uncheck Enable Diagnostics system if you want to hide the diagnostics window.</span></span> <span data-ttu-id="40a5f-141">Wir empfehlen, das Diagnosefenster während der Anwendungsentwicklung aktiviert zu lassen, um die Leistung zu überwachen, und es anschließend im Produktionsbetrieb oder bei Demos der Anwendung zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="40a5f-141">We recommend keeping the diagnostics window enabled during application development to monitor performance, and then disabling it during production or application demonstrations.</span></span> 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. <span data-ttu-id="40a5f-143">Öffnen Sie die Buildeinstellungen, indem Sie STRG+UMSCHALT+B drücken oder zu „Datei > Buildeinstellungen“ wechseln.</span><span class="sxs-lookup"><span data-stu-id="40a5f-143">Open the build settings by pressing control+shift+B or going to File->Build Settings.</span></span> <span data-ttu-id="40a5f-144">Beachten Sie, dass das Programm derzeit unter der eigenständigen PC-, Mac- und Linux-Plattform konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="40a5f-144">Notice that the program is currently set under the PC, Mac and Linux standalone platform.</span></span> <span data-ttu-id="40a5f-145">Legen Sie für die HoloLens 2-Entwicklung die Plattform auf Universelle Windows-Plattform fest.</span><span class="sxs-lookup"><span data-stu-id="40a5f-145">For HoloLens 2 development, set the platform to be Universal Windows Platform.</span></span> <span data-ttu-id="40a5f-146">Wählen Sie sie aus, und klicken Sie auf „Switch Platform“ (Plattform wechseln).</span><span class="sxs-lookup"><span data-stu-id="40a5f-146">Select it and click Switch Platform.</span></span>

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. <span data-ttu-id="40a5f-148">Klicken Sie nach Abschluss des Vorgangs auf das Feld mit der Bezeichnung „Add Open Scenes“ (Offene Szenen hinzufügen).</span><span class="sxs-lookup"><span data-stu-id="40a5f-148">Once complete, click the box called Add Open Scenes.</span></span> <span data-ttu-id="40a5f-149">Navigieren Sie jetzt zum Inspektorbereich, und vergewissern Sie sich, dass das Kontrollkästchen rechts neben „Virtual Reality Supported“ (Virtual Reality unterstützt) aktiviert ist (wie in der Abbildung unten dargestellt).</span><span class="sxs-lookup"><span data-stu-id="40a5f-149">Now go to the Inspector panel and ensure that the check box to the right of Virtual Reality Supported (as shown in the image below) is checked.</span></span> <span data-ttu-id="40a5f-150">Stellen Sie ferner sicher, dass das Kontrollkästchen neben „scenes/HLSharedProjectMain“ ebenfalls aktiviert ist, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="40a5f-150">Also ensure that the check box next to scenes/HLSharedProjectMain is also checked, as shown in the image below.</span></span>

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. <span data-ttu-id="40a5f-152">Scrollen Sie im Abschnitt „Publishing Settings“ (Veröffentlichungseinstellungen) nach unten bis zu „Capabilities“ (Funktionen), und stellen Sie sicher, dass die folgenden Kontrollkästchen aktiviert sind:</span><span class="sxs-lookup"><span data-stu-id="40a5f-152">Under the Publishing Settings section in the Inspector panel, scroll down to Capabilities and ensure the following check boxes are marked:</span></span>

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. <span data-ttu-id="40a5f-154">Importieren Sie die aufgelisteten benutzerdefinierten Pakete:</span><span class="sxs-lookup"><span data-stu-id="40a5f-154">Import the listed custom packages:</span></span>

    * <span data-ttu-id="40a5f-155">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (Version 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="40a5f-155">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
    * [<span data-ttu-id="40a5f-156">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="40a5f-156">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * [<span data-ttu-id="40a5f-157">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="40a5f-157">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)
    * [<span data-ttu-id="40a5f-158">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="40a5f-158">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    ><span data-ttu-id="40a5f-159">Wenn Sie eine Auffrischung zum Konfigurieren eines Unity-Projekts für Azure Spatial Anchors benötigen, lesen Sie das Tutorial [Erste Schritte mit Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1), das Teil der [Azure Spatial Anchor](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1)-Tutorialreihe ist.</span><span class="sxs-lookup"><span data-stu-id="40a5f-159">For a reminder on how to configure a Unity project for Azure Spatial Anchors, you can refer to the [Getting started with Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial which is part of the the [Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) tutorial series.</span></span>


13. <span data-ttu-id="40a5f-160">Wechseln Sie im Projektbereich zum Ordner „Prefabs“.</span><span class="sxs-lookup"><span data-stu-id="40a5f-160">In the Project panel, go to the Prefabs folder.</span></span> <span data-ttu-id="40a5f-161">In den folgenden Schritten implementieren Sie einige Prefabs in der Szene.</span><span class="sxs-lookup"><span data-stu-id="40a5f-161">In the following steps, you will implement a few prefabs into the scene.</span></span> <span data-ttu-id="40a5f-162">Klicken Sie im Ordner „Prefabs“ auf das Fenster „Prefab, Debug“, und ziehen Sie es in die Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="40a5f-162">In the Prefabs folder, click and drag the prefab, Debug Window into the hierarchy.</span></span> <span data-ttu-id="40a5f-163">Nachdem Sie dies abgeschlossen haben, speichern Sie das Projekt, indem Sie auf „Datei“ klicken, und speichern Sie dann, oder drücken Sie STRG+S.</span><span class="sxs-lookup"><span data-stu-id="40a5f-163">Once finished, save the project by clicking File, then Save or press Control+S.</span></span>

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    <span data-ttu-id="40a5f-165">Möglicherweise wird ein Popup angezeigt, wenn Sie auf das Prefab klicken, das TMP Essentials anfragt.</span><span class="sxs-lookup"><span data-stu-id="40a5f-165">You may notice a pop-up appear as you click on the prefab, asking you about TMP Essentials.</span></span> <span data-ttu-id="40a5f-166">Klicken Sie in diesem Fall auf „Import TMP Essentials“, da diese erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="40a5f-166">Click Import TMP Essentials as they are needed.</span></span> <span data-ttu-id="40a5f-167">Wenn dieses Popup angezeigt wird, müssen Sie möglicherweise das Prefab aus Ihrer Hierarchie löschen und es erneut in Ihre Hierarchie ziehen, um mögliche Fehler im Zusammenhang mit Text zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="40a5f-167">If this pop-up appears, you might need to delete the prefab from your hierarchy and re-drag it into your hierarchy to avoid potential text-related errors.</span></span>

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="40a5f-169">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="40a5f-169">Congratulations</span></span>

<span data-ttu-id="40a5f-170">Ihr Unity-Projekt ist jetzt für Photon bereit.</span><span class="sxs-lookup"><span data-stu-id="40a5f-170">Your Unity Project is now ready for Photon.</span></span> <span data-ttu-id="40a5f-171">In den nächsten Tutorials bauen wir auf dieser Szene und unserem Unity-Projekt auf, mit dem Ziel einer vollständigen gemeinsamen Benutzererfahrung.</span><span class="sxs-lookup"><span data-stu-id="40a5f-171">In the coming tutorials, we'll build upon this scene and our Unity project towards a full shared experience.</span></span>

<span data-ttu-id="40a5f-172">[Nächstes Tutorial: 3. Verbinden mehrerer Benutzer](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="40a5f-172">[Next tutorial: 3. Connecting multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>
