---
title: Lernprogramme für Mehrbenutzerfunktionen-5. Integrieren von Azure Spatial Anchor in eine gemeinsame Nutzung
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Umgebungen mit mehreren Benutzern in einer hololens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: c1b64b9d32409d61284f21ca216417ece4767d1b
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553808"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="df0a5-105">5. integrieren von Azure Spatial Anchor in eine freigegebene Darstellung</span><span class="sxs-lookup"><span data-stu-id="df0a5-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="df0a5-106">In dieser Lektion erfahren Sie, wie Sie Azure Spatial Anchor (ASA) in unsere freigegebene Erfahrung integrieren.</span><span class="sxs-lookup"><span data-stu-id="df0a5-106">In this lesson, you'll learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="df0a5-107">ASA ermöglicht es, dass mehrere zusammengestellte Geräte über einen allgemeinen Verweis verfügen, wenn ihre physische Umgebung darin besteht, virtuelle Oberflächen so zu verankern, dass alle Teilnehmer Objekte am gleichen physischen Speicherort sehen.</span><span class="sxs-lookup"><span data-stu-id="df0a5-107">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

## <a name="objectives"></a><span data-ttu-id="df0a5-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="df0a5-108">Objectives</span></span>

* <span data-ttu-id="df0a5-109">Integrieren Sie ASA in eine freigegebene Darstellung für die Ausrichtung auf mehrere Geräte.</span><span class="sxs-lookup"><span data-stu-id="df0a5-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
* <span data-ttu-id="df0a5-110">Lernen Sie die Grundlagen der Funktionsweise von ASA im Kontext einer lokalen gemeinsamen Umgebung kennen.</span><span class="sxs-lookup"><span data-stu-id="df0a5-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

## <a name="instructions"></a><span data-ttu-id="df0a5-111">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="df0a5-111">Instructions</span></span>

1. <span data-ttu-id="df0a5-112">Wählen Sie unter dem übergeordneten Element mixedrealityplayspace das vorfab tableanchor aus, und löschen Sie es.</span><span class="sxs-lookup"><span data-stu-id="df0a5-112">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. <span data-ttu-id="df0a5-114">Wechseln Sie in der Projektansicht zu Assets-> Resources-> Prefabs, und ziehen Sie das tableanchor-präfab oberhalb des sharedplayground-Objekts, um es als untergeordnetes Element festzulegen.</span><span class="sxs-lookup"><span data-stu-id="df0a5-114">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>

3. <span data-ttu-id="df0a5-115">Erweitern Sie das übergeordnete Objekt mixedrealityplayspace, das tableanchor-Objekt, und erweitern Sie auch das Schaltflächen Objekt.</span><span class="sxs-lookup"><span data-stu-id="df0a5-115">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span>

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="df0a5-117">Wählen Sie nun in der Hierarchie shareazureanchorbutton aus, und verschieben Sie Ihre Aufmerksamkeit auf den Inspektor-Bereich.</span><span class="sxs-lookup"><span data-stu-id="df0a5-117">Now in the hierarchy, select ShareAzureAnchorButton and move your attention to the Inspector panel.</span></span> <span data-ttu-id="df0a5-118">Scrollen Sie nach unten zum Dropdown Menü, das in der folgenden Abbildung dargestellt ist, wählen Sie anchormodulescript aus, und klicken Sie auf shareanchornetwork ().</span><span class="sxs-lookup"><span data-stu-id="df0a5-118">Scroll down to the drop-down menu shown in the image below, select AnchorModuleScript and click ShareAnchorNetwork().</span></span>

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="df0a5-120">Wählen Sie getazureanchorbutton aus (siehe Schritt 4), und verschieben Sie Ihre Aufmerksamkeit zurück zum Inspektor-Panel.</span><span class="sxs-lookup"><span data-stu-id="df0a5-120">Select GetAzureAnchorButton (see Step 4) and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="df0a5-121">Scrollen Sie nach unten zum Dropdown Menü, das in der folgenden Abbildung angezeigt wird, wählen Sie anchormodulescript aus, klicken Sie auf getsharedanchornetwork () und dann auf speichern.</span><span class="sxs-lookup"><span data-stu-id="df0a5-121">Scroll down to the drop-down menu displayed in the image below, select AnchorModuleScript, click GetSharedAnchorNetwork(), and save.</span></span>

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="df0a5-123">Wiederholen Sie Schritt 4, um die startazuresession ()-Funktion mit startazuresessionbutton zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="df0a5-123">Repeat step 4 to hook up the StartAzureSession () function to the StartAzureSessionButton.</span></span>

7. <span data-ttu-id="df0a5-124">Wiederholen Sie Schritt 4, um die Funktion "" von "" in der Funktion "" des Spiels "Game Object" der Funktion zu verbinden und zu überprüfen, ob das tableanchor-Objekt dem Parameter "Game Object" der Funktion zugewiesen ist.</span><span class="sxs-lookup"><span data-stu-id="df0a5-124">Repeat step 4 to hook up the CreateAzureAnchor () function to the CreateAzureAnchorButton and verify that the TableAnchor object is assigned to the function's parameter 'Game Object' field.</span></span>

8. <span data-ttu-id="df0a5-125">Befolgen Sie die Anweisungen unter [Verbinden der Szene mit der Azure-Ressource](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) , um Ihre Azure-Dienst Anmelde Informationen für räumliche Anker hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="df0a5-125">Follow the [Connect the scene to the Azure resource](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource) instructions to add your Azure Spatial Anchors service credentials.</span></span>

9. <span data-ttu-id="df0a5-126">Um das Freigabe Modul zu testen, klicken Sie auf die Schaltfläche "Azure ASA-Sitzung starten", die die Azure-Sitzung für räumliche Anker startet, und erstellen Sie dann den Azure-Anker durch Klicken auf die Schaltfläche "Azure-Anker erstellen"</span><span class="sxs-lookup"><span data-stu-id="df0a5-126">To test the sharing module, click the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button.</span></span> <span data-ttu-id="df0a5-127">Warten Sie, bis der Azure-Anker erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="df0a5-127">Wait for the azure anchor to get created.</span></span> <span data-ttu-id="df0a5-128">Nachdem der Azure-Anker erstellt wurde, klicken Sie auf die Schaltfläche "Azure-Anker freigeben", um den erstellten Azure-Anker aus den hololens zu teilen.</span><span class="sxs-lookup"><span data-stu-id="df0a5-128">Once the azure anchor is created, click the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

10. <span data-ttu-id="df0a5-129">Um den gemeinsam genutzten Azure-Anker in einem anderen hololens zu erhalten, klicken Sie auf die "Azure ASA-Sitzung starten", um zu beginnen und zur aktuellen ASA-Sitzung zu gelangen.</span><span class="sxs-lookup"><span data-stu-id="df0a5-129">To receive the shared azure anchor in another HoloLens, click the "Start Azure ASA Session" to start and get in to the current ASA session</span></span>

11. <span data-ttu-id="df0a5-130">Klicken Sie auf die Schaltfläche "Azure-Anker erhalten", um den freigegebenen Azure-Anker aus den anderen hololens zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="df0a5-130">Click the "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

## <a name="congratulations"></a><span data-ttu-id="df0a5-131">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="df0a5-131">Congratulations</span></span>

<span data-ttu-id="df0a5-132">In dieser Lektion haben Sie gelernt, wie Sie die leistungsstarken neuen räumlichen Anker von Azure integrieren, um zusammengestellte Geräte in einer freigegebenen Erfahrung auszurichten.</span><span class="sxs-lookup"><span data-stu-id="df0a5-132">In this lesson, you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="df0a5-133">Dies schließt auch das Freigabe Modul ein.</span><span class="sxs-lookup"><span data-stu-id="df0a5-133">This also concludes the Sharing Module.</span></span> <span data-ttu-id="df0a5-134">Wir haben gelernt, wie Sie ein neues Photon-Konto einrichten, die Verwendung von Photon und pun in eine neue Unity-Anwendung, das Konfigurieren von Avatare und freigegebenen Objekten und schließlich das Ausrichten mehrerer Teilnehmer mithilfe von ASA.</span><span class="sxs-lookup"><span data-stu-id="df0a5-134">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configure avatars and shared objects, and finally align multiple participants using ASA.</span></span>
