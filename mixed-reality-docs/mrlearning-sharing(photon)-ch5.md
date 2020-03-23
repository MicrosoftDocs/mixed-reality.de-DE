---
title: 'Tutorials zu Mehrbenutzerfunktionen: 5 Integrieren von Azure Spatial Anchors in eine gemeinsam genutzte Umgebung'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 7fb8cd03b2f3739037dee38786493bfd9012f6ce
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031687"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="b4bbc-105">5. Integrieren von Azure Spatial Anchors in eine gemeinsam genutzte Umgebung</span><span class="sxs-lookup"><span data-stu-id="b4bbc-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="b4bbc-106">In dieser Lektion erfahren Sie, wie Sie Azure Spatial Anchors (ASA) in unsere freigegebene Benutzererfahrung integrieren.</span><span class="sxs-lookup"><span data-stu-id="b4bbc-106">In this lesson, you'll learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="b4bbc-107">ASA ermöglicht es, dass mehrere Geräte in einem gemeinsamen Bereich eine gemeinsame Referenz verwenden, wenn in ihrer physischen Umgebung virtuelle Benutzererfahrungen verankert sind, sodass alle Teilnehmer Objekte am gleichen physischen Ort sehen.</span><span class="sxs-lookup"><span data-stu-id="b4bbc-107">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

## <a name="objectives"></a><span data-ttu-id="b4bbc-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="b4bbc-108">Objectives</span></span>

* <span data-ttu-id="b4bbc-109">Integrieren von ASA in einer freigegebenen Benutzererfahrung für die Ausrichtung mehrerer Geräte.</span><span class="sxs-lookup"><span data-stu-id="b4bbc-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
* <span data-ttu-id="b4bbc-110">Erlernen der grundlegenden Funktionsweise von ASA im Kontext einer lokalen gemeinsamen Umgebung.</span><span class="sxs-lookup"><span data-stu-id="b4bbc-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

## <a name="instructions"></a><span data-ttu-id="b4bbc-111">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="b4bbc-111">Instructions</span></span>

1. <span data-ttu-id="b4bbc-112">Wählen Sie unter dem übergeordneten Objekt MixedRealityPlayspace das TableAnchor-Prefab aus, und löschen Sie es.</span><span class="sxs-lookup"><span data-stu-id="b4bbc-112">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. <span data-ttu-id="b4bbc-114">Wechseln Sie in der Projektansicht zu „Assets > Resources > Prefabs“, und ziehen Sie das TableAnchor-Prefab auf das SharedPlayground-Objekt, um es zu einem untergeordneten Objekt zu machen.</span><span class="sxs-lookup"><span data-stu-id="b4bbc-114">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>

3. <span data-ttu-id="b4bbc-115">Klappen Sie das übergeordnete MixedRealityPlayspace-Objekt, das TableAnchor-Objekt und auch das Buttons-Objekt auf.</span><span class="sxs-lookup"><span data-stu-id="b4bbc-115">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span>

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="b4bbc-117">Wählen Sie nun in der Hierarchie ShareAzureAnchorButton aus, und verlegen Sie Ihre Aufmerksamkeit auf den Inspektorbereich.</span><span class="sxs-lookup"><span data-stu-id="b4bbc-117">Now in the hierarchy, select ShareAzureAnchorButton and move your attention to the Inspector panel.</span></span> <span data-ttu-id="b4bbc-118">Scrollen Sie nach unten zum Dropdownmenü, das im Bild unten angezeigt wird, wählen Sie AnchorModuleScript aus, und klicken Sie auf ShareAnchorNetwork().</span><span class="sxs-lookup"><span data-stu-id="b4bbc-118">Scroll down to the drop-down menu shown in the image below, select AnchorModuleScript and click ShareAnchorNetwork().</span></span>

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="b4bbc-120">Wählen Sie GetAzureAnchorButton aus (siehe Schritt 4), und verlegen Sie Ihre Aufmerksamkeit wieder auf den Inspektorbereich.</span><span class="sxs-lookup"><span data-stu-id="b4bbc-120">Select GetAzureAnchorButton (see Step 4) and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="b4bbc-121">Scrollen Sie nach unten zum Dropdownmenü, das im Bild unten angezeigt wird, wählen Sie AnchorModuleScript aus, klicken Sie auf ShareAnchorNetwork(), und speichern Sie.</span><span class="sxs-lookup"><span data-stu-id="b4bbc-121">Scroll down to the drop-down menu displayed in the image below, select AnchorModuleScript, click GetSharedAnchorNetwork(), and save.</span></span>

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="b4bbc-123">Wiederholen Sie Schritt 4, um die StartAzureSession ()-Funktion in StartAzureSessionButton einzuhängen.</span><span class="sxs-lookup"><span data-stu-id="b4bbc-123">Repeat step 4 to hook up the StartAzureSession () function to the StartAzureSessionButton.</span></span>

7. <span data-ttu-id="b4bbc-124">Wiederholen Sie Schritt 4, um die CreateAzureAnchor ()-Funktion in CreateAzureAnchorButton einzuhängen, und überprüfen Sie, ob das TableAnchor-Objekt dem Parameterfeld ‚Game Object‘ der Funktion zugewiesen ist.</span><span class="sxs-lookup"><span data-stu-id="b4bbc-124">Repeat step 4 to hook up the CreateAzureAnchor () function to the CreateAzureAnchorButton and verify that the TableAnchor object is assigned to the function's parameter 'Game Object' field.</span></span>

8. <span data-ttu-id="b4bbc-125">Befolgen Sie die Anweisungen unter [Verbinden der Szene mit der Azure-Ressource](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource), um Ihre Dienstanmeldeinformationen für Azure Spatial Anchors hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="b4bbc-125">Follow the [Connect the scene to the Azure resource](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) instructions to add your Azure Spatial Anchors service credentials.</span></span>

9. <span data-ttu-id="b4bbc-126">Um das Freigabemodul zu testen, klicken Sie auf die Schaltfläche „Start Azure ASA Session“ (Azure ASA-Sitzung starten), wodurch die Azure Spatial Anchors-Sitzung gestartet wird, und erstellen Sie dann den Azure-Anker, indem Sie auf die Schaltfläche „Create Azure Anchor“ (Azure Anchor erstellen) klicken.</span><span class="sxs-lookup"><span data-stu-id="b4bbc-126">To test the sharing module, click the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button.</span></span> <span data-ttu-id="b4bbc-127">Warten Sie, bis der Azure-Anker erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="b4bbc-127">Wait for the azure anchor to get created.</span></span> <span data-ttu-id="b4bbc-128">Nachdem der Azure-Anker erstellt wurde, klicken Sie auf die Schaltfläche „Share Azure Anchor“ (Azure Anchor freigeben), um den erstellten Azure-Anker aus der HoloLens zu teilen.</span><span class="sxs-lookup"><span data-stu-id="b4bbc-128">Once the azure anchor is created, click the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

10. <span data-ttu-id="b4bbc-129">Um den freigegebenen Azure Anchor in einer weiteren HoloLens zu empfangen, klicken Sie auf „Start Azure ASA Session“ (Azure ASA-Sitzung starten), um zu starten und zur aktuellen ASA-Sitzung zu gelangen</span><span class="sxs-lookup"><span data-stu-id="b4bbc-129">To receive the shared azure anchor in another HoloLens, click the "Start Azure ASA Session" to start and get in to the current ASA session</span></span>

11. <span data-ttu-id="b4bbc-130">Klicken Sie auf die Schaltfläche „Get Azure Anchor“, um den freigegebenen Azure Anchor aus der anderen HoloLens abzurufen.</span><span class="sxs-lookup"><span data-stu-id="b4bbc-130">Click the "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

## <a name="congratulations"></a><span data-ttu-id="b4bbc-131">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="b4bbc-131">Congratulations</span></span>

<span data-ttu-id="b4bbc-132">In dieser Lektion haben Sie gelernt, wie Sie die leistungsstarken neuen Spatial Anchors von Azure integrieren, um Geräte in einem gemeinsamen Bereich in einer gemeinsamen Erfahrung auszurichten.</span><span class="sxs-lookup"><span data-stu-id="b4bbc-132">In this lesson, you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="b4bbc-133">Damit ist das Freigabemodul abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="b4bbc-133">This also concludes the Sharing Module.</span></span> <span data-ttu-id="b4bbc-134">Wir haben gelernt, wie ein neues Photon-Konto einrichtet wird, wie Photon und PUN in eine neue Unity-Anwendung integriert werden, Avatare und geteilte Objekte konfiguriert und schließlich mehrere Teilnehmer mithilfe von ASA ausgerichtet werden.</span><span class="sxs-lookup"><span data-stu-id="b4bbc-134">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configure avatars and shared objects, and finally align multiple participants using ASA.</span></span>
