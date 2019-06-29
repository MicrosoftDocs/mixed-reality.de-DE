---
title: Lernen die Freigabe-Modul für HoloLens 2 MR
description: Führen Sie diesen Kurs erfahren, wie Sie mehrere Benutzer freigegebene Umgebungen innerhalb einer HoloLens-2-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 2a16d318c6d749bcbf6ed9db0d6cd2228a6ea06e
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465204"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="72f95-104">Azure räumliche Anker sowie veröffentlichte Erfahrungen</span><span class="sxs-lookup"><span data-stu-id="72f95-104">Azure Spatial Anchors and shared experiences</span></span>

<span data-ttu-id="72f95-105">In dieser Lektion erfahren wir, wie Azure räumliche Anker (ASA) in unserem gemeinsamen Erfahrung zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="72f95-105">In this lesson, we learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="72f95-106">ASA kann mehrere zusammengestellten Geräte eine Referenz zu häufigen haben, wenn es sich bei ihrer physischen Umgebung zu virtuellen Umgebungen Anker ist, sodass alle Teilnehmer die Objekte in der gleichen physischen Ort finden Sie unter.</span><span class="sxs-lookup"><span data-stu-id="72f95-106">ASA allows multiple co-located devices to have a common reference if their physical environment is to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="72f95-107">Bevor Sie mit dieser Lektion fortfahren müssen wir das ASA-Learning-Modul erfüllt werden, das darunter die ASA-Grundlagen, Azure-Konto und das Erstellen von Ressourcen und andere grundlegende Gebäude-Blöcke, die erforderlich sind, bevor wir in unserem gemeinsamen Erfahrung ASA integrieren beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="72f95-107">Before proceeding with this lesson, we'll need to complete the ASA learning module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="72f95-108">Ziele:</span><span class="sxs-lookup"><span data-stu-id="72f95-108">Objectives:</span></span>

- <span data-ttu-id="72f95-109">Integrieren von ASA in einer gemeinsamen Erfahrung bei der Multi-Device-Ausrichtung</span><span class="sxs-lookup"><span data-stu-id="72f95-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
- <span data-ttu-id="72f95-110">Grundlagen der Funktionsweise von ASA im Rahmen einer gemeinsamen lokalen Erfahrung</span><span class="sxs-lookup"><span data-stu-id="72f95-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="72f95-111">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="72f95-111">Instructions</span></span>

1. <span data-ttu-id="72f95-112">Speichern Sie das Projekt aus der vorherigen Lektion (STRG + S), und nennen Sie sie "HLSharedProjectMainPart5.unity", sodass es leichter zu finden, wenn Sie ihn wieder benötigen.</span><span class="sxs-lookup"><span data-stu-id="72f95-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="72f95-113">Wählen Sie das Prefab TableAnchor unterhalb des übergeordneten Objekts, MixedRealityPlayspace, und löschen Sie sie.</span><span class="sxs-lookup"><span data-stu-id="72f95-113">Select the TableAnchor prefab underneath the MixedRealityPlayspace parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)



3.  <span data-ttu-id="72f95-115">In der Projektansicht wechseln Sie zu den Ressourcen-Ressourcen > -> prefabs (Vorlagen) werden soll, und ziehen Sie das Prefab TableAnchor über das SharedPlayground-Objekt, das als untergeordnetes.</span><span class="sxs-lookup"><span data-stu-id="72f95-115">In the Project view go to Assets->Resources->Prefabs, and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="72f95-116">Erweitern Sie die MixedRealityPlayspace übergeordnete-Objekt, das TableAnchor-Objekt, und auch das Schaltflächen-Objekt.</span><span class="sxs-lookup"><span data-stu-id="72f95-116">Expand the MixedRealityPlayspace parent object, TableAnchor object, and expand the Buttons object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="72f95-118">Wählen Sie jetzt in der Hierarchie ShareAzureAnchorButton, und verschieben Sie Ihre Aufmerksamkeit auf den Zugriffsbereich Inaspector.</span><span class="sxs-lookup"><span data-stu-id="72f95-118">Now in the hierarchy, select ShareAzureAnchorButton, and move your attention to the Inaspector panel.</span></span> <span data-ttu-id="72f95-119">Scrollen Sie im Dropdown-Menü in der Abbildung unten dargestellt und wählen Sie AnchorModuleScript aus, und klicken Sie auf ShareAnchorNetework().</span><span class="sxs-lookup"><span data-stu-id="72f95-119">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript and click ShareAnchorNetework().</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="72f95-121">Wählen Sie GetAzureAnchorButton (siehe Schritt 4), und verschieben Sie Ihre Aufmerksamkeit an den Bereich der Eigenschaftenanalyse.</span><span class="sxs-lookup"><span data-stu-id="72f95-121">Select GetAzureAnchorButton (see Step 4), and move your attention back to the Inspector panel.</span></span> <span data-ttu-id="72f95-122">Scrollen Sie im Dropdown-Menü in der Abbildung unten dargestellt und wählen Sie AnchorModuleScript aus, und klicken Sie auf GetSharedAnchorNetwork(), und speichern.</span><span class="sxs-lookup"><span data-stu-id="72f95-122">Scroll down to the drop-down menu shown in the image below, and select AnchorModuleScript, and click GetSharedAnchorNetwork(), and save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a><span data-ttu-id="72f95-124">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="72f95-124">Congratulations</span></span>

<span data-ttu-id="72f95-125">In dieser Lektion haben Sie gelernt, wie Sie Azure leistungsfähige neue räumliche Anker zum Ausrichten von zusammengestellten Geräte in einer freigegebenen Umgebung zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="72f95-125">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="72f95-126">In dieser Lektion wird auch das Modul Freigabe abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="72f95-126">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="72f95-127">Wir haben gelernt, wie zum Einrichten eines neuen Photon-Kontos integrieren Photon und WORTSPIEL in einer neuen Unity-Anwendung, Profilbild und freigegebene Objekte konfigurieren und schließlich Ausrichten von mehreren Beteiligten mit ASA.</span><span class="sxs-lookup"><span data-stu-id="72f95-127">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 

