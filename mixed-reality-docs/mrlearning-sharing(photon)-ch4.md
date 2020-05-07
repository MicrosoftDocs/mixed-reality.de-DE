---
title: 'Tutorials zu Mehrbenutzerfunktionen: 5 Integrieren von Azure Spatial Anchors in eine gemeinsam genutzte Umgebung'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: c27ed7327cfe0a61f2b63e309348bdea1a535ea1
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604971"
---
# <a name="4-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="622b2-105">4. Integrieren von Azure Spatial Anchors in eine gemeinsam genutzte Umgebung</span><span class="sxs-lookup"><span data-stu-id="622b2-105">4. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="622b2-106">In diesem Tutorial erfahren Sie, wie Sie Azure Spatial Anchors (ASA) in die geteilte Benutzererfahrung integrieren.</span><span class="sxs-lookup"><span data-stu-id="622b2-106">In this tutorial, you will learn how to integrate Azure Spatial Anchors (ASA) into the shared experience.</span></span> <span data-ttu-id="622b2-107">ASA ermöglicht es, dass mehrere Geräte einen gemeinsamen Bezug auf die physische Welt nutzen, sodass sich die Benutzer gegenseitig an ihren realen physischen Standorten sehen und die gemeinsame Benutzererfahrung am gleichen Ort sehen.</span><span class="sxs-lookup"><span data-stu-id="622b2-107">ASA allows multiple devices to have a common reference to the physical world so that the users see each other in their actual physical location and see the shared experience in the same place.</span></span>

## <a name="objectives"></a><span data-ttu-id="622b2-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="622b2-108">Objectives</span></span>

* <span data-ttu-id="622b2-109">Integrieren von ASA in einer geteilten Benutzererfahrung für die Ausrichtung mehrerer Geräte.</span><span class="sxs-lookup"><span data-stu-id="622b2-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
* <span data-ttu-id="622b2-110">Erlernen der grundlegenden Funktionsweise von ASA im Kontext einer lokalen gemeinsamen Benutzererfahrung.</span><span class="sxs-lookup"><span data-stu-id="622b2-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="622b2-111">Vorbereiten der Szene</span><span class="sxs-lookup"><span data-stu-id="622b2-111">Preparing the scene</span></span>

<span data-ttu-id="622b2-112">Klappen Sie im Hierarchiefenster das **SharedPlayground**-Objekt auf, und klappen Sie dann das **TableAnchor**-Objekt auf, um dessen untergeordnete Objekte anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="622b2-112">In the Hierarchy window, expand the **SharedPlayground** object, then expand the **TableAnchor** object to expose its child objects:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-1.png)

<span data-ttu-id="622b2-114">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs**, und ziehen Sie das **Buttons**-Prefab auf das untergeordnete **TableAnchor**-Objekt im Hierarchiefenster, um es Ihrer Szene als untergeordnetes Element des TableAnchor-Objekts hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="622b2-114">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **Buttons** prefab on top of the **TableAnchor** child object in the Hierarchy window to add it to your scene as a child of the TableAnchor object:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="622b2-116">Konfigurieren der Schaltflächen zum Betreiben der Szene</span><span class="sxs-lookup"><span data-stu-id="622b2-116">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="622b2-117">In diesem Abschnitt konfigurieren Sie eine Reihe von Schaltflächenereignissen, an denen sich die Grundlagen der Verwendung von Azure Spatial Anchors zum Erreichen einer räumlichen Ausrichtung in einer gemeinsamen Benutzererfahrung zeigen lassen.</span><span class="sxs-lookup"><span data-stu-id="622b2-117">In this section, you will configure a series of button events that demonstrate the fundamentals of how Azure Spatial Anchors can be used to achieve spatial alignment in a shared experience.</span></span>

<span data-ttu-id="622b2-118">Klappen Sie im Hierarchiefenster das **Button**-Objekt auf, und wählen Sie das erste untergeordnete Schaltflächenobjekt mit dem Namen **StartAzureSession** aus:</span><span class="sxs-lookup"><span data-stu-id="622b2-118">In the Hierarchy window, expand the **Button** object and select the first child button object named **StartAzureSession**:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-1.png)

<span data-ttu-id="622b2-120">Suchen Sie im Inspektorfenster die Komponente **Interactable (Script)** , und konfigurieren Sie das **OnClick ()** -Ereignis folgendermaßen:</span><span class="sxs-lookup"><span data-stu-id="622b2-120">In the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="622b2-121">Weisen Sie das **TableAnchor**-Objekt dem Feld **None (Object)** zu</span><span class="sxs-lookup"><span data-stu-id="622b2-121">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="622b2-122">Wählen Sie in der Dropdownliste **No Function** die Funktion **AnchorModuleScript** > **StartAzureSession ()** aus</span><span class="sxs-lookup"><span data-stu-id="622b2-122">From **No Function** dropdown, select the **AnchorModuleScript** > **StartAzureSession ()** function</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-2.png)

<span data-ttu-id="622b2-124">Wählen Sie im Hierarchiefenster das zweite untergeordnete Schaltflächenobjekt mit dem Namen **CreateAzureAnchor** aus, suchen Sie dann im Inspektorfenster die Komponente **Interactable (Script)** , und konfigurieren Sie das **OnClick ()** -Ereignis in folgender Weise:</span><span class="sxs-lookup"><span data-stu-id="622b2-124">In the Hierarchy window, select the second child button object named **CreateAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="622b2-125">Weisen Sie das **TableAnchor**-Objekt dem Feld **None (Object)** zu</span><span class="sxs-lookup"><span data-stu-id="622b2-125">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="622b2-126">Wählen Sie in der Dropdownliste **No Function** die Funktion **AnchorModuleScript** > **CreateAzureAnchor ()** aus</span><span class="sxs-lookup"><span data-stu-id="622b2-126">From **No Function** dropdown, select the **AnchorModuleScript** > **CreateAzureAnchor ()** function</span></span>
* <span data-ttu-id="622b2-127">Weisen Sie das **TableAnchor**-Objekt dem neuen Feld **None (Game Object)** zu, das jetzt angezeigt wird</span><span class="sxs-lookup"><span data-stu-id="622b2-127">To the new **None (Game Object)** field that appears, assign the **TableAnchor** object</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-3.png)

<span data-ttu-id="622b2-129">Wählen Sie im Hierarchiefenster das dritte untergeordnete Schaltflächenobjekt mit dem Namen **ShareAzureAnchor** aus, suchen Sie dann im Inspektorfenster die Komponente **Interactable (Script)** , und konfigurieren Sie das **OnClick ()** -Ereignis in folgender Weise:</span><span class="sxs-lookup"><span data-stu-id="622b2-129">In the Hierarchy window, select the third child button object named **ShareAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="622b2-130">Weisen Sie das **TableAnchor**-Objekt dem Feld **None (Object)** zu</span><span class="sxs-lookup"><span data-stu-id="622b2-130">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="622b2-131">Wählen Sie in der Dropdownliste **No Function** die Funktion **SharingModuleScript** > **ShareAzureAnchor ()** aus</span><span class="sxs-lookup"><span data-stu-id="622b2-131">From **No Function** dropdown, select the **SharingModuleScript** > **ShareAzureAnchor ()** function</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-4.png)

<span data-ttu-id="622b2-133">Wählen Sie im Hierarchiefenster das vierte untergeordnete Schaltflächenobjekt mit dem Namen **GetAzureAnchor** aus, suchen Sie dann im Inspektorfenster die Komponente **Interactable (Script)** , und konfigurieren Sie das **OnClick ()** -Ereignis in folgender Weise:</span><span class="sxs-lookup"><span data-stu-id="622b2-133">In the Hierarchy window, select the forth child button object named **GetAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="622b2-134">Weisen Sie das **TableAnchor**-Objekt dem Feld **None (Object)** zu</span><span class="sxs-lookup"><span data-stu-id="622b2-134">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="622b2-135">Wählen Sie in der Dropdownliste **No Function** die Funktion **SharingModuleScript** > **GetAzureAnchor ()** aus</span><span class="sxs-lookup"><span data-stu-id="622b2-135">From **No Function** dropdown, select the **SharingModuleScript** > **GetAzureAnchor ()** function</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="622b2-137">Verbinden der Szene mit der Azure-Ressource</span><span class="sxs-lookup"><span data-stu-id="622b2-137">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="622b2-138">Klappen Sie im Hierarchiefenster das **SharedPlayground**-Objekt auf, und wählen Sie das **TableAnchor**-Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="622b2-138">In the Hierarchy window, expand the **SharedPlayground** object and select the **TableAnchor** object.</span></span> <span data-ttu-id="622b2-139">Suchen Sie dann im Inspektorfenster die Komponente **Spatial Anchor Manager (Script)** , und konfigurieren Sie den Abschnitt **Credentials** (Anmeldeinformationen) mit den Anmeldeinformationen aus dem Azure Spatial Anchors-Konto, das Sie im Rahmen der [Voraussetzungen](mrlearning-sharing(photon)-ch1.md#prerequisites) für diese Tutorialreihe erstellt haben:</span><span class="sxs-lookup"><span data-stu-id="622b2-139">Then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component and configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mrlearning-sharing(photon)-ch1.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="622b2-140">Fügen Sie in das Feld **Spatial Anchors Account ID** die **Konto-ID** Ihres Azure Spatial Anchors-Kontos ein</span><span class="sxs-lookup"><span data-stu-id="622b2-140">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="622b2-141">Fügen Sie in das Feld **Spatial Anchors Account Key** (Spatial Anchors-Kontoschlüssel) den primären oder sekundären **Zugriffsschlüssel** aus Ihrem Azure Spatial Anchors-Konto ein</span><span class="sxs-lookup"><span data-stu-id="622b2-141">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-1.png)

<span data-ttu-id="622b2-143">Vergewissern Sie sich bei noch immer ausgewähltem **TableAnchor**-Objekt im Inspektorfenster, dass alle Skriptkomponenten aktiviert sind:</span><span class="sxs-lookup"><span data-stu-id="622b2-143">With the **TableAnchor** object still selected, in the Inspector window, make sure all the script components are enabled:</span></span>

* <span data-ttu-id="622b2-144">Aktivieren Sie das Kontrollkästchen neben den **Spatial Anchor Manager (Script)** -Komponenten, um sie zu aktivieren</span><span class="sxs-lookup"><span data-stu-id="622b2-144">Check the checkbox next to the **Spatial Anchor Manager (Script)** components to enable it</span></span>
* <span data-ttu-id="622b2-145">Aktivieren Sie das Kontrollkästchen neben den **Anchor Module Script (Script)** -Komponenten, um sie zu aktivieren</span><span class="sxs-lookup"><span data-stu-id="622b2-145">Check the checkbox next to the **Anchor Module Script (Script)** components to enable it</span></span>
* <span data-ttu-id="622b2-146">Aktivieren Sie das Kontrollkästchen neben den **Sharing Module Script (Script)** -Komponenten, um sie zu aktivieren</span><span class="sxs-lookup"><span data-stu-id="622b2-146">Check the checkbox next to the **Sharing Module Script (Script)** components to enable it</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-2.png)

## <a name="trying-the-experience-with-spatial-alignment"></a><span data-ttu-id="622b2-148">Ausprobieren der Benutzererfahrung mit räumlicher Ausrichtung</span><span class="sxs-lookup"><span data-stu-id="622b2-148">Trying the experience with spatial alignment</span></span>

> [!NOTE]
> <span data-ttu-id="622b2-149">Azure Spatial Anchors können nicht in Unity ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="622b2-149">Azure Spatial Anchors can not run in Unity.</span></span> <span data-ttu-id="622b2-150">Um die Funktionalität der Azure Spatial Anchors zu testen, müssen Sie das Projekt daher auf mindestens zwei HoloLens-Geräten bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="622b2-150">Consequently, to test the Azure Spatial Anchors functionality, you need to deploy the project to a minimum of two HoloLens devices.</span></span>

<span data-ttu-id="622b2-151">Wenn Sie das Unity-Projekt jetzt erstellen und es auf zwei HoloLens-Geräten bereitstellen, können Sie räumliche Ausrichtung zwischen den Geräten erreichen, indem Sie die Azure Anchor-ID teilen.</span><span class="sxs-lookup"><span data-stu-id="622b2-151">If you now build and deploy the Unity project to two HoloLens devices, you can achieve spatial alignment between the devices by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="622b2-152">Um das zu Testen, können Sie diese Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="622b2-152">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="622b2-153">Auf HoloLens-Gerät 1: **Starten Sie die Anwendung** (die Raketenstartbasis wird instanziiert und auf dem Tisch positioniert)</span><span class="sxs-lookup"><span data-stu-id="622b2-153">On HoloLens device 1: **Start the application** (the Rocket Launcher is instantiated and placed on the table)</span></span>
2. <span data-ttu-id="622b2-154">Auf HoloLens-Gerät 2: **Starten Sie die Anwendung** (beide Benutzer sehen den Tisch mit der Raketenstartbasis, der Tisch wird jedoch nicht am gleichen Ort dargestellt und die Benutzeravatare werden nicht dort angezeigt, wo sich die Benutzer befinden)</span><span class="sxs-lookup"><span data-stu-id="622b2-154">On HoloLens device 2: **Start the application** (both users see the table with the Rocket Launcher, however, the table does not appear in the same place and the user avatars do not appear where the users are)</span></span>
3. <span data-ttu-id="622b2-155">Auf HoloLens-Gerät 1: Drücken Sie die Schaltfläche **Start Azure Session** (Azure-Sitzung starten)</span><span class="sxs-lookup"><span data-stu-id="622b2-155">On HoloLens device 1: Press the **Start Azure Session** button</span></span>
4. <span data-ttu-id="622b2-156">Auf HoloLens-Gerät 1: Drücken Sie die Schaltfläche **Create Azure Anchor** (Azure Anchor erstellen; erstellt einen Anker am Speicherort des TableAnchor-Objekts und speichert die Ankerinformationen in der Azure-Ressource).</span><span class="sxs-lookup"><span data-stu-id="622b2-156">On HoloLens device 1: Press the **Create Azure Anchor** button (creates anchor at the location of the TableAnchor object and stores the anchor information in the Azure resource).</span></span>
5. <span data-ttu-id="622b2-157">Auf HoloLens-Gerät 1: Drücken Sie die Schaltfläche **Share Azure Anchor** (Azure Anchor teilen; teilt die Anker-ID in Echtzeit mit anderen Benutzern)</span><span class="sxs-lookup"><span data-stu-id="622b2-157">On HoloLens device 1: Press the **Share Azure Anchor** button (shares the anchor ID with other users in real-time)</span></span>
6. <span data-ttu-id="622b2-158">Auf HoloLens-Gerät 2: Drücken Sie die Schaltfläche **Start Azure Session** (Azure-Sitzung starten)</span><span class="sxs-lookup"><span data-stu-id="622b2-158">On HoloLens device 2: Press the **Start Azure Session** button</span></span>
7. <span data-ttu-id="622b2-159">Auf HoloLens-Gerät 2: Drücken Sie die Schaltfläche **Get Azure Anchor** (Azure Anchor abrufen; stellt eine Verbindung mit der Azure-Ressource her, um die Ankerinformationen für die freigegebene Anker-ID abzurufen, und verschiebt dann das TableAnchor-Objekt an den Speicherort, an dem der Anker mit dem HoloLens-Gerät 1 erstellt wurde)</span><span class="sxs-lookup"><span data-stu-id="622b2-159">On HoloLens device 2: Press the **Get Azure Anchor** button (connects to the Azure resource to retrieve the anchor information for the shared anchor ID, then moves the TableAnchor object to the location where the anchor was created with the HoloLens device 1)</span></span>

## <a name="congratulations"></a><span data-ttu-id="622b2-160">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="622b2-160">Congratulations</span></span>

<span data-ttu-id="622b2-161">In diesem Tutorial haben Sie gelernt, wie Sie die leistungsstarken Spatial Anchors von Azure integrieren, um Geräte in einer gemeinsamen Benutzererfahrung auszurichten.</span><span class="sxs-lookup"><span data-stu-id="622b2-161">In this tutorial, you learned how to integrate Azure's powerful Spatial Anchors to align devices in a shared experience.</span></span> <span data-ttu-id="622b2-162">Dieses Tutorial bildet zugleich den Abschluss der Tutorialreihe, in der Sie gelernt haben, wie ein neues Photon-Konto und eine neue Photon-Anwendung einrichtet werden, wie Photon und PUN in eine Unity-Anwendung integriert werden, Benutzeravatare und geteilte Objekte konfiguriert und schließlich mehrere Teilnehmer mithilfe von ASA ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="622b2-162">This also concludes this tutorial series where you have learned how to set up a Photon account and application, integrate Photon and PUN into a Unity application, configure user avatars and shared objects, and finally align multiple participants using ASA.</span></span>
