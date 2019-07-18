---
title: Mr Learning Sharing Module für hololens 2
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Umgebungen mit mehreren Benutzern in einer hololens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 1ae880208e79e2e045bd5e7298db260b7f0b2232
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293628"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="8d63c-104">Räumliche Azure-Anker und gemeinsame Nutzung</span><span class="sxs-lookup"><span data-stu-id="8d63c-104">Azure Spatial Anchors and shared experiences</span></span>

<span data-ttu-id="8d63c-105">In dieser Lektion erfahren Sie, wie Sie Azure Spatial Anchor (ASA) in unsere freigegebene Erfahrung integrieren.</span><span class="sxs-lookup"><span data-stu-id="8d63c-105">In this lesson, we learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="8d63c-106">ASA ermöglicht es, dass mehrere zusammengestellte Geräte über einen allgemeinen Verweis verfügen, wenn ihre physische Umgebung darin besteht, virtuelle Oberflächen so zu verankern, dass alle Teilnehmer Objekte am gleichen physischen Speicherort sehen.</span><span class="sxs-lookup"><span data-stu-id="8d63c-106">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="8d63c-107">Bevor Sie mit dieser Lektion fortfahren, müssen wir das ASA-Lernmodul ausführen, das die ASA-Grundlagen, die Erstellung von Azure-Konten und-Ressourcen und andere grundlegende Bausteine behandelt, die erforderlich sind, bevor wir ASA in unsere freigegebene Erfahrung integrieren können.</span><span class="sxs-lookup"><span data-stu-id="8d63c-107">Before proceeding with this lesson, we'll need to complete the ASA learning module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="8d63c-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="8d63c-108">Objectives:</span></span>

- <span data-ttu-id="8d63c-109">Integrieren Sie ASA in eine freigegebene Darstellung für die Ausrichtung auf mehrere Geräte.</span><span class="sxs-lookup"><span data-stu-id="8d63c-109">Integrate ASA into a shared experience for multi-device alignment.</span></span>
- <span data-ttu-id="8d63c-110">Lernen Sie die Grundlagen der Funktionsweise von ASA im Kontext einer lokalen gemeinsamen Umgebung kennen.</span><span class="sxs-lookup"><span data-stu-id="8d63c-110">Learn the fundamentals of how ASA works in the context of a local shared experience.</span></span>

### <a name="instructions"></a><span data-ttu-id="8d63c-111">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="8d63c-111">Instructions</span></span>

1. <span data-ttu-id="8d63c-112">Speichern Sie das Projekt aus der vorherigen Lektion (Control + S), und nennen Sie es "HLSharedProjectMainPart5. unity", damit es leichter zu finden ist, wenn Sie es erneut benötigen.</span><span class="sxs-lookup"><span data-stu-id="8d63c-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="8d63c-113">Wählen Sie unter dem übergeordneten Element mixedrealityplayspace das vorfab tableanchor aus, und löschen Sie es.</span><span class="sxs-lookup"><span data-stu-id="8d63c-113">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3.  <span data-ttu-id="8d63c-115">Wechseln Sie in der Projektansicht zu Assets-> Resources-> Prefabs, und ziehen Sie das tableanchor-präfab oberhalb des sharedplayground-Objekts, um es als untergeordnetes Element festzulegen.</span><span class="sxs-lookup"><span data-stu-id="8d63c-115">In the Project view, go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="8d63c-116">Erweitern Sie das übergeordnete Objekt mixedrealityplayspace, das tableanchor-Objekt, und erweitern Sie auch das Schaltflächen Objekt.</span><span class="sxs-lookup"><span data-stu-id="8d63c-116">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="8d63c-118">Wählen Sie nun in der Hierarchie shareazureanchorbutton aus, und verschieben Sie Ihre Aufmerksamkeit auf den Bereich "inaspector".</span><span class="sxs-lookup"><span data-stu-id="8d63c-118">Now in the hierarchy, select ShareAzureAnchorButton, and move your attention to the Inaspector panel.</span></span> <span data-ttu-id="8d63c-119">Scrollen Sie nach unten zum Dropdown Menü, das in der folgenden Abbildung dargestellt ist, und wählen Sie anchormodulescript aus, und klicken Sie auf shareanchornetework ().</span><span class="sxs-lookup"><span data-stu-id="8d63c-119">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript and click ShareAnchorNetework().</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="8d63c-121">Wählen Sie getazureanchorbutton aus (siehe Schritt 4), und verschieben Sie die Aufmerksamkeit zurück zum Inspektor-Panel.</span><span class="sxs-lookup"><span data-stu-id="8d63c-121">Select GetAzureAnchorButton (see Step 4), and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="8d63c-122">Scrollen Sie nach unten zum Dropdown Menü, das in der folgenden Abbildung dargestellt ist, und wählen Sie anchormodulescript aus, und klicken Sie auf getsharedanchornetwork () und dann auf speichern.</span><span class="sxs-lookup"><span data-stu-id="8d63c-122">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript, and click GetSharedAnchorNetwork(), and save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. <span data-ttu-id="8d63c-124">Um das Freigabe Modul zu testen, klicken Sie auf die Schaltfläche "Azure-ASA-Sitzung starten", die die Azure-Sitzung für räumliche Anker startet, und erstellen Sie dann den Azure-Anker, indem Sie auf die Schaltfläche "Azure-Anker erstellen" klicken und warten, bis der Azure-Anker erstellt wird</span><span class="sxs-lookup"><span data-stu-id="8d63c-124">To test the sharing module, click on the "Start Azure ASA Session" button which will start the azure spatial anchors session and then create the azure anchor by clicking the "Create Azure Anchor" button and wait for sometime for the azure anchor to get created.</span></span> <span data-ttu-id="8d63c-125">Nachdem der Azure-Anker erstellt wurde, klicken Sie auf die Schaltfläche "Azure-Anker freigeben", um den erstellten Azure-Anker aus den hololens zu teilen.</span><span class="sxs-lookup"><span data-stu-id="8d63c-125">Once the azure anchor is created then click on the "Share Azure Anchor" button to share the created azure anchor from the HoloLens.</span></span>

7. <span data-ttu-id="8d63c-126">Um den freigegebenen Azure-Anker in einem anderen hololens zu erhalten, klicken Sie auf "Azure ASA-Sitzung starten", um die aktuelle ASA-Sitzung zu starten, und klicken Sie auf die Schaltfläche "Get Azure Anchor", um den freigegebenen Azure-Anker aus den anderen hololens zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="8d63c-126">To recieve the shared azure anchor in another HoloLens, click on the "Start Azure ASA Session" to start and get in to the current ASA session and click on "Get Azure Anchor" button to get the shared azure anchor from the other HoloLens.</span></span>

   > <span data-ttu-id="8d63c-127">Hinweis: Alle Details der entsprechenden Aktionen auf den einzelnen Schaltflächen werden im Debugfenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8d63c-127">Note: All details of the corresponding actions on the individual buttons will be displayed in the debug window.</span></span>

## <a name="congratulations"></a><span data-ttu-id="8d63c-128">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="8d63c-128">Congratulations</span></span>

<span data-ttu-id="8d63c-129">In dieser Lektion haben Sie erfahren, wie Sie die leistungsfähigen neuen räumlichen Anker von Azure integrieren, um zusammengestellte Geräte in einer freigegebenen Erfahrung auszurichten.</span><span class="sxs-lookup"><span data-stu-id="8d63c-129">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="8d63c-130">Diese Lektion schließt auch das Freigabe Modul ein.</span><span class="sxs-lookup"><span data-stu-id="8d63c-130">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="8d63c-131">Wir haben gelernt, wie Sie ein neues Photon-Konto einrichten, die Verwendung von Photon und pun in eine neue Unity-Anwendung, das Konfigurieren von Avatare und freigegebenen Objekten und schließlich das Ausrichten mehrerer Teilnehmer mithilfe von ASA.</span><span class="sxs-lookup"><span data-stu-id="8d63c-131">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 

