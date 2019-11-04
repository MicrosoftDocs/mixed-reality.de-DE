---
title: Lernprogramme für Mehrbenutzerfunktionen-5. Integrieren von Azure Spatial Anchor in eine gemeinsame Nutzung
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Umgebungen mit mehreren Benutzern in einer hololens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: b83c7ac39d522fc2b799591fa02608d5fc5cc930
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437571"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="d0417-105">5. integrieren von Azure Spatial Anchor in eine freigegebene Darstellung</span><span class="sxs-lookup"><span data-stu-id="d0417-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="d0417-106">In dieser Lektion erfahren Sie, wie Sie Azure Spatial Anchor (ASA) in unsere freigegebene Erfahrung integrieren.</span><span class="sxs-lookup"><span data-stu-id="d0417-106">In this lesson, we learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="d0417-107">ASA ermöglicht es, dass mehrere zusammengestellte Geräte über einen allgemeinen Verweis verfügen, wenn ihre physische Umgebung darin besteht, virtuelle Oberflächen so zu verankern, dass alle Teilnehmer Objekte am gleichen physischen Speicherort sehen.</span><span class="sxs-lookup"><span data-stu-id="d0417-107">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="d0417-108">Bevor Sie mit dieser Lektion fortfahren, müssen wir das ASA-Lernmodul ausführen, das die ASA-Grundlagen, die Erstellung von Azure-Konten und-Ressourcen und andere grundlegende Bausteine behandelt, die erforderlich sind, bevor wir ASA in unsere freigegebene Erfahrung integrieren können.</span><span class="sxs-lookup"><span data-stu-id="d0417-108">Before proceeding with this lesson, we'll need to complete the ASA learning module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="d0417-109">Ziele</span><span class="sxs-lookup"><span data-stu-id="d0417-109">Objectives:</span></span>

- <span data-ttu-id="d0417-110">Integrieren Sie ASA in eine freigegebene Darstellung für die Ausrichtung auf mehrere Geräte.</span><span class="sxs-lookup"><span data-stu-id="d0417-110">Integrate ASA into a shared experience for multi-device alignment.</span></span>
- <span data-ttu-id="d0417-111">Lernen Sie die Grundlagen der Funktionsweise von ASA im Kontext einer lokalen gemeinsamen Umgebung kennen.</span><span class="sxs-lookup"><span data-stu-id="d0417-111">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

### <a name="instructions"></a><span data-ttu-id="d0417-112">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="d0417-112">Instructions</span></span>

1. <span data-ttu-id="d0417-113">Speichern Sie das Projekt aus der vorherigen Lektion (Control + S), und nennen Sie es "HLSharedProjectMainPart5. unity", damit es leichter zu finden ist, wenn Sie es erneut benötigen.</span><span class="sxs-lookup"><span data-stu-id="d0417-113">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="d0417-114">Wählen Sie unter dem übergeordneten Element mixedrealityplayspace das vorfab tableanchor aus, und löschen Sie es.</span><span class="sxs-lookup"><span data-stu-id="d0417-114">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3.  <span data-ttu-id="d0417-116">Wechseln Sie in der Projektansicht zu Assets-> Resources-> Prefabs, und ziehen Sie das tableanchor-präfab oberhalb des sharedplayground-Objekts, um es als untergeordnetes Element festzulegen.</span><span class="sxs-lookup"><span data-stu-id="d0417-116">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="d0417-117">Erweitern Sie das übergeordnete Objekt mixedrealityplayspace, das tableanchor-Objekt, und erweitern Sie auch das Schaltflächen Objekt.</span><span class="sxs-lookup"><span data-stu-id="d0417-117">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="d0417-119">Wählen Sie nun in der Hierarchie shareazureanchorbutton aus, und verschieben Sie Ihre Aufmerksamkeit auf den Bereich "inaspector".</span><span class="sxs-lookup"><span data-stu-id="d0417-119">Now in the hierarchy, select ShareAzureAnchorButton and move your attention to the Inaspector panel.</span></span> <span data-ttu-id="d0417-120">Scrollen Sie nach unten zum Dropdown Menü, das in der folgenden Abbildung dargestellt ist, wählen Sie anchormodulescript aus, und klicken Sie auf shareanchornetework ().</span><span class="sxs-lookup"><span data-stu-id="d0417-120">Scroll down to the drop-down menu shown in the image below, select AnchorModuleScript and click ShareAnchorNetework().</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="d0417-122">Wählen Sie getazureanchorbutton aus (siehe Schritt 4), und verschieben Sie Ihre Aufmerksamkeit zurück zum Inspektor-Panel.</span><span class="sxs-lookup"><span data-stu-id="d0417-122">Select GetAzureAnchorButton (see Step 4) and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="d0417-123">Scrollen Sie nach unten zum Dropdown Menü, das in der folgenden Abbildung dargestellt ist, und wählen Sie anchormodulescript aus, und klicken Sie auf getsharedanchornetwork () und dann auf speichern.</span><span class="sxs-lookup"><span data-stu-id="d0417-123">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript, and click GetSharedAnchorNetwork(), and save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="d0417-125">Um das Freigabe Modul zu testen, klicken Sie auf die Schaltfläche "Azure ASA-Sitzung starten", die die Azure-Sitzung für räumliche Anker startet, und erstellen Sie dann den Azure-Anker durch Klicken auf die Schaltfläche "Azure-Anker erstellen"</span><span class="sxs-lookup"><span data-stu-id="d0417-125">To test the sharing module, click the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button.</span></span> <span data-ttu-id="d0417-126">Warten Sie, bis der Azure-Anker erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="d0417-126">Wait for the azure anchor to get created.</span></span> <span data-ttu-id="d0417-127">Nachdem der Azure-Anker erstellt wurde, klicken Sie auf die Schaltfläche "Azure-Anker freigeben", um den erstellten Azure-Anker aus den hololens zu teilen.</span><span class="sxs-lookup"><span data-stu-id="d0417-127">Once the azure anchor is created, click the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

7. <span data-ttu-id="d0417-128">Um den gemeinsam genutzten Azure-Anker in einem anderen hololens zu erhalten, klicken Sie auf die "Azure ASA-Sitzung starten", um zu beginnen und zur aktuellen ASA-Sitzung zu gelangen.</span><span class="sxs-lookup"><span data-stu-id="d0417-128">To recieve the shared azure anchor in another HoloLens, click the "Start Azure ASA Session" to start and get in to the current ASA session</span></span>

8. <span data-ttu-id="d0417-129">Klicken Sie auf die Schaltfläche "Azure-Anker erhalten", um den freigegebenen Azure-Anker aus den anderen hololens zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="d0417-129">Click the "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

   > <span data-ttu-id="d0417-130">Hinweis: alle Details der entsprechenden Aktionen auf den einzelnen Schaltflächen werden im Fenster "Debuggen" angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d0417-130">Note: All details of the corresponding actions on the individual buttons will be displayed in the debug window.</span></span>

## <a name="congratulations"></a><span data-ttu-id="d0417-131">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="d0417-131">Congratulations</span></span>

<span data-ttu-id="d0417-132">In dieser Lektion haben Sie erfahren, wie Sie die leistungsfähigen neuen räumlichen Anker von Azure integrieren, um zusammengestellte Geräte in einer freigegebenen Erfahrung auszurichten.</span><span class="sxs-lookup"><span data-stu-id="d0417-132">In this lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="d0417-133">Dies schließt auch das Freigabe Modul ein.</span><span class="sxs-lookup"><span data-stu-id="d0417-133">This also concludes the Sharing Module.</span></span> <span data-ttu-id="d0417-134">Wir haben gelernt, wie Sie ein neues Photon-Konto einrichten, die Verwendung von Photon und pun in eine neue Unity-Anwendung, das Konfigurieren von Avatare und freigegebenen Objekten und schließlich das Ausrichten mehrerer Teilnehmer mithilfe von ASA.</span><span class="sxs-lookup"><span data-stu-id="d0417-134">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configure avatars and shared objects, and finally align multiple participants using ASA.</span></span> 

