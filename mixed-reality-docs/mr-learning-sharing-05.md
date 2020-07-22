---
title: 'Tutorials zu Mehrbenutzerfunktionen: 5 Integrieren von Azure Spatial Anchors in eine gemeinsam genutzte Umgebung'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 79be23c9371bf90d03df0070b74f6cff3f0afafa
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305626"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="d2ee1-105">5. Integrieren von Azure Spatial Anchors in eine gemeinsam genutzte Umgebung</span><span class="sxs-lookup"><span data-stu-id="d2ee1-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="d2ee1-106">In diesem Tutorial erfahren Sie, wie Sie Azure Spatial Anchors (ASA) in die geteilte Benutzererfahrung integrieren.</span><span class="sxs-lookup"><span data-stu-id="d2ee1-106">In this tutorial, you will learn how to integrate Azure Spatial Anchors (ASA) into the shared experience.</span></span> <span data-ttu-id="d2ee1-107">ASA ermöglicht es, dass mehrere Geräte einen gemeinsamen Bezug auf die physische Welt nutzen, sodass sich die Benutzer gegenseitig an ihren realen physischen Standorten sehen und die gemeinsame Benutzererfahrung am gleichen Ort sehen.</span><span class="sxs-lookup"><span data-stu-id="d2ee1-107">ASA allows multiple devices to have a common reference to the physical world so that the users see each other in their actual physical location and see the shared experience in the same place.</span></span>

## <a name="objectives"></a><span data-ttu-id="d2ee1-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="d2ee1-108">Objectives</span></span>

* <span data-ttu-id="d2ee1-109">Integrieren von ASA in einer geteilten Benutzererfahrung für die Ausrichtung mehrerer Geräte.</span><span class="sxs-lookup"><span data-stu-id="d2ee1-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
* <span data-ttu-id="d2ee1-110">Erlernen der grundlegenden Funktionsweise von ASA im Kontext einer lokalen gemeinsamen Benutzererfahrung.</span><span class="sxs-lookup"><span data-stu-id="d2ee1-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="d2ee1-111">Vorbereiten der Szene</span><span class="sxs-lookup"><span data-stu-id="d2ee1-111">Preparing the scene</span></span>

<span data-ttu-id="d2ee1-112">Klappen Sie im Hierarchiefenster das **SharedPlayground**-Objekt auf, und klappen Sie dann das **TableAnchor**-Objekt auf, um dessen untergeordnete Objekte anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="d2ee1-112">In the Hierarchy window, expand the **SharedPlayground** object, then expand the **TableAnchor** object to expose its child objects:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section1-step1-1.png)

<span data-ttu-id="d2ee1-114">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs**, und ziehen Sie das Prefab **Buttons** auf das untergeordnete **TableAnchor**-Objekt, um es Ihrer Szene als untergeordnetes Element des TableAnchor-Objekts hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="d2ee1-114">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **Buttons** prefab onto the **TableAnchor** child object to add it to your scene as a child of the TableAnchor object:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="d2ee1-116">Konfigurieren der Schaltflächen zum Betreiben der Szene</span><span class="sxs-lookup"><span data-stu-id="d2ee1-116">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="d2ee1-117">In diesem Abschnitt konfigurieren Sie eine Reihe von Schaltflächenereignissen, an denen sich die Grundlagen der Verwendung von Azure Spatial Anchors zum Erreichen einer räumlichen Ausrichtung in einer gemeinsamen Benutzererfahrung zeigen lassen.</span><span class="sxs-lookup"><span data-stu-id="d2ee1-117">In this section, you will configure a series of button events demonstrating the fundamentals of how Azure Spatial Anchors can be used to achieve spatial alignment in a shared experience.</span></span>

<span data-ttu-id="d2ee1-118">Klappen Sie im Hierarchiefenster das **Button**-Objekt auf, und wählen Sie das erste untergeordnete Schaltflächenobjekt mit dem Namen **StartAzureSession** aus:</span><span class="sxs-lookup"><span data-stu-id="d2ee1-118">In the Hierarchy window, expand the **Button** object and select the first child button object named **StartAzureSession**:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-1.png)

<span data-ttu-id="d2ee1-120">Suchen Sie im Inspektorfenster die Komponente **Interactable (Script)** , und konfigurieren Sie das **OnClick ()** -Ereignis folgendermaßen:</span><span class="sxs-lookup"><span data-stu-id="d2ee1-120">In the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="d2ee1-121">Weisen Sie das **TableAnchor**-Objekt dem Feld **None (Object)** zu.</span><span class="sxs-lookup"><span data-stu-id="d2ee1-121">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="d2ee1-122">Wählen Sie in der Dropdownliste **No Function** die Funktion **AnchorModuleScript** > **StartAzureSession ()** aus.</span><span class="sxs-lookup"><span data-stu-id="d2ee1-122">From the **No Function** dropdown, select the **AnchorModuleScript** > **StartAzureSession ()** function</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-2.png)

<span data-ttu-id="d2ee1-124">Wählen Sie im Hierarchiefenster das zweite untergeordnete Schaltflächenobjekt mit dem Namen **CreateAzureAnchor** aus, suchen Sie dann im Inspektorfenster die Komponente **Interactable (Script)** , und konfigurieren Sie das **OnClick ()** -Ereignis in folgender Weise:</span><span class="sxs-lookup"><span data-stu-id="d2ee1-124">In the Hierarchy window, select the second child button object named **CreateAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="d2ee1-125">Weisen Sie das **TableAnchor**-Objekt dem Feld **None (Object)** zu.</span><span class="sxs-lookup"><span data-stu-id="d2ee1-125">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="d2ee1-126">Wählen Sie in der Dropdownliste **No Function** die Funktion **AnchorModuleScript** > **CreateAzureAnchor ()** aus.</span><span class="sxs-lookup"><span data-stu-id="d2ee1-126">From the **No Function** dropdown, select the **AnchorModuleScript** > **CreateAzureAnchor ()** function</span></span>
* <span data-ttu-id="d2ee1-127">Weisen Sie das **TableAnchor**-Objekt dem neuen Feld **None (Game Object)** zu, das jetzt angezeigt wird</span><span class="sxs-lookup"><span data-stu-id="d2ee1-127">To the new **None (Game Object)** field that appears, assign the **TableAnchor** object</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-3.png)

<span data-ttu-id="d2ee1-129">Wählen Sie im Hierarchiefenster das dritte untergeordnete Schaltflächenobjekt mit dem Namen **ShareAzureAnchor** aus, suchen Sie dann im Inspektorfenster die Komponente **Interactable (Script)** , und konfigurieren Sie das **OnClick ()** -Ereignis in folgender Weise:</span><span class="sxs-lookup"><span data-stu-id="d2ee1-129">In the Hierarchy window, select the third child button object named **ShareAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="d2ee1-130">Weisen Sie das **TableAnchor**-Objekt dem Feld **None (Object)** zu.</span><span class="sxs-lookup"><span data-stu-id="d2ee1-130">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="d2ee1-131">Wählen Sie in der Dropdownliste **No Function** die Funktion **SharingModuleScript** > **ShareAzureAnchor ()** aus.</span><span class="sxs-lookup"><span data-stu-id="d2ee1-131">From the **No Function** dropdown, select the **SharingModuleScript** > **ShareAzureAnchor ()** function</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-4.png)

<span data-ttu-id="d2ee1-133">Wählen Sie im Hierarchiefenster das vierte untergeordnete Schaltflächenobjekt mit dem Namen **GetAzureAnchor** aus, suchen Sie dann im Inspektorfenster die Komponente **Interactable (Script)** , und konfigurieren Sie das **OnClick ()** -Ereignis in folgender Weise:</span><span class="sxs-lookup"><span data-stu-id="d2ee1-133">In the Hierarchy window, select the fourth child button object named **GetAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="d2ee1-134">Weisen Sie das **TableAnchor**-Objekt dem Feld **None (Object)** zu.</span><span class="sxs-lookup"><span data-stu-id="d2ee1-134">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="d2ee1-135">Wählen Sie in der Dropdownliste **No Function** die Funktion **SharingModuleScript** > **GetAzureAnchor ()** aus.</span><span class="sxs-lookup"><span data-stu-id="d2ee1-135">From the **No Function** dropdown, select the **SharingModuleScript** > **GetAzureAnchor ()** function</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="d2ee1-137">Verbinden der Szene mit der Azure-Ressource</span><span class="sxs-lookup"><span data-stu-id="d2ee1-137">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="d2ee1-138">Klappen Sie im Hierarchiefenster das **SharedPlayground**-Objekt auf, und wählen Sie das **TableAnchor**-Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="d2ee1-138">In the Hierarchy window, expand the **SharedPlayground** object and select the **TableAnchor** object.</span></span>

<span data-ttu-id="d2ee1-139">Suchen Sie im Inspektor-Fenster die Komponente **Spatial Anchor Manager (Script)** , und konfigurieren Sie den Abschnitt **Credentials** (Anmeldeinformationen) mit den Anmeldeinformationen aus dem Azure Spatial Anchors-Konto, das Sie im Rahmen der [Voraussetzungen](mr-learning-sharing-01.md#prerequisites) für diese Tutorialreihe erstellt haben:</span><span class="sxs-lookup"><span data-stu-id="d2ee1-139">In the Inspector window, locate the **Spatial Anchor Manager (Script)** component and configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-sharing-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="d2ee1-140">Fügen Sie in das Feld **Spatial Anchors Account ID** die **Konto-ID** Ihres Azure Spatial Anchors-Kontos ein</span><span class="sxs-lookup"><span data-stu-id="d2ee1-140">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="d2ee1-141">Fügen Sie in das Feld **Spatial Anchors Account Key** (Spatial Anchors-Kontoschlüssel) den primären oder sekundären **Zugriffsschlüssel** aus Ihrem Azure Spatial Anchors-Konto ein</span><span class="sxs-lookup"><span data-stu-id="d2ee1-141">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="d2ee1-143">Anstatt die Spatial Anchors-Konto-ID und den Schlüssel in der Szene festzulegen, können Sie diese Werte für das gesamte Projekt festlegen. Dies kann von Vorteil sein, wenn Sie über mehrere Szenen mit ASA verfügen.</span><span class="sxs-lookup"><span data-stu-id="d2ee1-143">Instead of setting the Spatial Anchors Account ID and Key in the scene, you can set it for your entire project, this can be advantageous if you have multiple scenes using ASA.</span></span> <span data-ttu-id="d2ee1-144">Navigieren Sie dazu im Projektfenster zur Ressource „Assets > AzureSpatialAnchors.SDK > Resources > **SpatialAnchorConfig**, und legen Sie dann die Werte im Inspektor-Fenster fest.</span><span class="sxs-lookup"><span data-stu-id="d2ee1-144">To do this, in the Project window, navigate to the Assets > AzureSpatialAnchors.SDK > Resources > **SpatialAnchorConfig** asset, then set the values in the Inspector window.</span></span>

<span data-ttu-id="d2ee1-145">Wählen Sie im Hierarchiefenster das **TableAnchor-Objekt** aus, und suchen Sie dann im Inspektor-Fenster nach der Komponente **Anchor Module (Script)** , um sie wie folgt zu konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="d2ee1-145">In the Hierarchy window, select the **TableAnchor** object, then in the Inspector window, locate the **Anchor Module (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="d2ee1-146">Ändern Sie im Feld **Public Sharing Pin** (PIN für öffentliche Freigabe) einige Ziffern, sodass die PIN für Ihr Projekt eindeutig ist.</span><span class="sxs-lookup"><span data-stu-id="d2ee1-146">In the **Public Sharing Pin** field, change a few digits, so the pin becomes unique to your project</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-2.png)

<span data-ttu-id="d2ee1-148">Vergewissern Sie sich bei noch immer ausgewähltem **TableAnchor**-Objekt im Inspektor-Fenster, dass alle Skriptkomponenten **aktiviert** sind:</span><span class="sxs-lookup"><span data-stu-id="d2ee1-148">With the **TableAnchor** object still selected, in the Inspector window, make sure all the script components are **enabled**:</span></span>

* <span data-ttu-id="d2ee1-149">Aktivieren Sie das Kontrollkästchen neben den **Spatial Anchor Manager (Script)** -Komponenten, um sie zu aktivieren</span><span class="sxs-lookup"><span data-stu-id="d2ee1-149">Check the checkbox next to the **Spatial Anchor Manager (Script)** components to enable it</span></span>
* <span data-ttu-id="d2ee1-150">Aktivieren Sie das Kontrollkästchen neben den **Anchor Module Script (Script)** -Komponenten, um sie zu aktivieren</span><span class="sxs-lookup"><span data-stu-id="d2ee1-150">Check the checkbox next to the **Anchor Module Script (Script)** components to enable it</span></span>
* <span data-ttu-id="d2ee1-151">Aktivieren Sie das Kontrollkästchen neben den **Sharing Module Script (Script)** -Komponenten, um sie zu aktivieren</span><span class="sxs-lookup"><span data-stu-id="d2ee1-151">Check the checkbox next to the **Sharing Module Script (Script)** components to enable it</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-3.png)

## <a name="trying-the-experience-with-spatial-alignment"></a><span data-ttu-id="d2ee1-153">Ausprobieren der Benutzererfahrung mit räumlicher Ausrichtung</span><span class="sxs-lookup"><span data-stu-id="d2ee1-153">Trying the experience with spatial alignment</span></span>

> [!NOTE]
> <span data-ttu-id="d2ee1-154">Azure Spatial Anchors können nicht in Unity ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="d2ee1-154">Azure Spatial Anchors can not run in Unity.</span></span> <span data-ttu-id="d2ee1-155">Um die Funktionalität der Azure Spatial Anchors zu testen, müssen Sie das Projekt daher auf mindestens zwei Geräten bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="d2ee1-155">Consequently, to test the Azure Spatial Anchors functionality, you need to deploy the project to a minimum of two devices.</span></span>

<span data-ttu-id="d2ee1-156">Wenn Sie das Unity-Projekt jetzt erstellen und es auf zwei Geräten bereitstellen, können Sie räumliche Ausrichtung zwischen den Geräten erreichen, indem Sie die Azure Anchor-ID teilen.</span><span class="sxs-lookup"><span data-stu-id="d2ee1-156">If you now build and deploy the Unity project to two devices, you can achieve spatial alignment between the devices by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="d2ee1-157">Um das zu Testen, können Sie diese Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="d2ee1-157">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="d2ee1-158">Auf Gerät 1: **Starten Sie die App** (der Rover-Explorer wird instanziiert und auf dem Tisch positioniert)</span><span class="sxs-lookup"><span data-stu-id="d2ee1-158">On device 1: **Start the app** (the Rover Explorer is instantiated and placed on the table)</span></span>
2. <span data-ttu-id="d2ee1-159">Auf Gerät 2: **Starten Sie die App** (beide Benutzer sehen den Tisch mit dem Rover-Explorer, der Tisch wird jedoch nicht am gleichen Ort dargestellt und die Benutzeravatare werden nicht dort angezeigt, wo sich die Benutzer befinden)</span><span class="sxs-lookup"><span data-stu-id="d2ee1-159">On device 2: **Start the app** (both users see the table with the Rover Explorer, but the table does not appear in the same place, and the user avatars do not appear where the users are)</span></span>
3. <span data-ttu-id="d2ee1-160">Auf Gerät 1: Drücken Sie die Schaltfläche **Start Azure Session** (Azure-Sitzung starten)</span><span class="sxs-lookup"><span data-stu-id="d2ee1-160">On device 1: Press the **Start Azure Session** button</span></span>
4. <span data-ttu-id="d2ee1-161">Auf Gerät 1: Drücken Sie die Schaltfläche **Create Azure Anchor** (Azure Anchor erstellen; erstellt einen Anker am Speicherort des TableAnchor-Objekts und speichert die Ankerinformationen in der Azure-Ressource).</span><span class="sxs-lookup"><span data-stu-id="d2ee1-161">On device 1: Press the **Create Azure Anchor** button (creates anchor at the location of the TableAnchor object and stores the anchor information in the Azure resource).</span></span>
5. <span data-ttu-id="d2ee1-162">Auf Gerät 1: Drücken Sie die Schaltfläche **Share Azure Anchor** (Azure Anchor teilen; teilt die Anker-ID in Echtzeit mit anderen Benutzern)</span><span class="sxs-lookup"><span data-stu-id="d2ee1-162">On device 1: Press the **Share Azure Anchor** button (shares the anchor ID with other users in real-time)</span></span>
6. <span data-ttu-id="d2ee1-163">Auf Gerät 2: Drücken Sie die Schaltfläche **Start Azure Session** (Azure-Sitzung starten)</span><span class="sxs-lookup"><span data-stu-id="d2ee1-163">On device 2: Press the **Start Azure Session** button</span></span>
7. <span data-ttu-id="d2ee1-164">Auf Gerät 2: Drücken Sie die Schaltfläche **Get Azure Anchor** (Azure Anchor abrufen) (stellt eine Verbindung mit der Azure-Ressource her, um die Ankerinformationen für die freigegebene Anker-ID abzurufen, und verschiebt dann das TableAnchor-Objekt an den Speicherort, an dem der Anker mit dem Gerät 1 erstellt wurde)</span><span class="sxs-lookup"><span data-stu-id="d2ee1-164">On device 2: Press the **Get Azure Anchor** button (connects to the Azure resource to retrieve the anchor information for the shared anchor ID, then moves the TableAnchor object to the location where the anchor was created with the device 1)</span></span>

> [!TIP]
> <span data-ttu-id="d2ee1-165">Wenn Sie keinen Zugriff auf zwei HoloLens-Geräte haben, können Sie die Anweisungen unter [Erstellen von Azure Spatial Anchors für mobile Geräte](mr-learning-asa-05.md) befolgen, um das Projekt auf Ihrem mobilen Gerät bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="d2ee1-165">If you don't have access to two HoloLens devices, you may follow the [Building Azure Spatial Anchors for mobile devices](mr-learning-asa-05.md) to deploy the project to your mobile device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="d2ee1-166">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="d2ee1-166">Congratulations</span></span>

<span data-ttu-id="d2ee1-167">In diesem Tutorial haben Sie gelernt, wie Sie die leistungsstarken Spatial Anchors von Azure integrieren, um Geräte in einer gemeinsamen Benutzererfahrung auszurichten.</span><span class="sxs-lookup"><span data-stu-id="d2ee1-167">In this tutorial, you learned how to integrate Azure's powerful Spatial Anchors to align devices in a shared experience.</span></span>

<span data-ttu-id="d2ee1-168">Dieses Tutorial bildet zugleich den Abschluss der Tutorialreihe, in der Sie gelernt haben, wie ein Photon-Konto eingerichtet, eine PUN-Anwendung erstellt und PUN in das Unity-Projekt integriert wird und Benutzeravatare und geteilte Objekte konfiguriert und schließlich mehrere Teilnehmer mithilfe von Azure Spatial Anchors ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="d2ee1-168">This also concludes this tutorial series where you learned how to set up a Photon account, create a PUN app, integrate PUN into the Unity project, configure user avatars and shared objects, and finally align multiple participants using Azure Spatial Anchors.</span></span>
