---
title: Lernen die Freigabe-Modul für HoloLens 2 MR
description: Führen Sie diesen Kurs erfahren, wie Sie mehrere Benutzer freigegebene Umgebungen innerhalb einer HoloLens-2-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 941bdc64ed614d5ce71f58f05585d0dfc86c3bb7
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415931"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a><span data-ttu-id="e6de0-104">Azure räumliche Anker sowie veröffentlichte Erfahrungen</span><span class="sxs-lookup"><span data-stu-id="e6de0-104">Azure Spatial Anchors and Shared Experiences</span></span>

<span data-ttu-id="e6de0-105">In dieser Lektion lernen wir, wie Sie Azure räumliche Anker (ASA) in unserem gemeinsamen Erfahrung zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="e6de0-105">In this lesson, we will learn how to integrate Azure Spatial Anchors (ASA) into our shared experience.</span></span> <span data-ttu-id="e6de0-106">ASA kann mehrere zusammengestellten Geräte ein gemeinsames Verständnis ihrer physischen Umgebung aus, um die virtuellen Verankern durchgeführter so, dass alle Teilnehmer Objekte in der gleichen physischen Ort zu haben.</span><span class="sxs-lookup"><span data-stu-id="e6de0-106">ASA allows multiple co-located devices to have a common understanding if their physical environment in order to anchor virtual experiences such that all participants see objects in the same physical place.</span></span>

<span data-ttu-id="e6de0-107">Bevor Sie mit dieser Lektion fortfahren müssen wir das ASA-Learning-Modul erfüllt werden, darunter die ASA-Grundlagen, Azure-Konto und das Erstellen von Ressourcen und andere grundlegende Gebäude-Blöcke, die erforderlich sind, bevor wir in unserem gemeinsamen Erfahrung ASA integrieren beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="e6de0-107">Before proceeding with this lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks that are required before we can integrate ASA into our shared experience.</span></span>

<span data-ttu-id="e6de0-108">Ziele:</span><span class="sxs-lookup"><span data-stu-id="e6de0-108">Objectives:</span></span>

- <span data-ttu-id="e6de0-109">Integrieren von ASA in einer gemeinsamen Erfahrung bei der Multi-Device-Ausrichtung</span><span class="sxs-lookup"><span data-stu-id="e6de0-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
- <span data-ttu-id="e6de0-110">Grundlagen der Funktionsweise von ASA im Rahmen einer gemeinsamen lokalen Erfahrung</span><span class="sxs-lookup"><span data-stu-id="e6de0-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="e6de0-111">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="e6de0-111">Instructions</span></span>

1. <span data-ttu-id="e6de0-112">Speichern Sie das Projekt aus der vorherigen Lektion (STRG + S), und nennen Sie sie "HLSharedProjectMainPart5.unity", sodass es leichter zu finden, wenn Sie ihn wieder benötigen.</span><span class="sxs-lookup"><span data-stu-id="e6de0-112">Save the project from the previous lesson (control+S) and name it "HLSharedProjectMainPart5.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="e6de0-113">Wählen Sie das Prefab TableAnchor unterhalb des übergeordneten Objekts, "MixedRealityPlayspace", und löschen Sie sie.</span><span class="sxs-lookup"><span data-stu-id="e6de0-113">Select the TableAnchor prefab underneath  the "MixedRealityPlayspace" parent object, and delete it.</span></span>

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)



3.  <span data-ttu-id="e6de0-115">Wechseln Sie in der Projektansicht zum Bestand > Ressourcen > prefabs (Vorlagen), und ziehen Sie die TableAnchor prefab über das SharedPlayground-Objekt, das ein untergeordnetes Element zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="e6de0-115">In the Project view go to Assets > Resources > Prefabs and drag the TableAnchor prefab on top of the SharedPlayground object to make it a child.</span></span>
4.  <span data-ttu-id="e6de0-116">Erweitern Sie das übergeordnete Objekt von "MixedRealityPlayspace", und klicken Sie dann auf das Objekt "TableAnchor", und auch das "Schaltflächen"-Objekt.</span><span class="sxs-lookup"><span data-stu-id="e6de0-116">Expand the "MixedRealityPlayspace" parent object, then the "TableAnchor" object, and expand the "buttons" object as well.</span></span> 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. <span data-ttu-id="e6de0-118">Wählen Sie jetzt in der Hierarchie, die "ShareAzureAnchorButton" und verschieben Sie Ihre Aufmerksamkeit auf den Bereich der Eigenschaftenanalyse.</span><span class="sxs-lookup"><span data-stu-id="e6de0-118">Now in the hierarchy, select the "ShareAzureAnchorButton" and move your attention to the inspector panel.</span></span> <span data-ttu-id="e6de0-119">Scrollen Sie im Dropdownmenü mit den in der Abbildung unten dargestellt, und wählen Sie "AnchorModuleScript", und klicken Sie auf "ShareAnchorNetework()."</span><span class="sxs-lookup"><span data-stu-id="e6de0-119">Scroll down to the dropdown menu shown in the image below, and select "AnchorModuleScript" and click on "ShareAnchorNetework()."</span></span>

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. <span data-ttu-id="e6de0-121">Ähnlich wie Schritt 4 Wählen Sie die "GetAzureAnchorButton", und verschieben Sie Ihre Aufmerksamkeit an den Bereich der Eigenschaftenanalyse.</span><span class="sxs-lookup"><span data-stu-id="e6de0-121">Much like step 4, select the "GetAzureAnchorButton" and move your attention back to the inspector panel.</span></span> <span data-ttu-id="e6de0-122">Scrollen Sie im Dropdownmenü mit den in der Abbildung unten dargestellt, und wählen Sie "AnchorModuleScript", und klicken Sie auf "GetSharedAnchorNetwork()."</span><span class="sxs-lookup"><span data-stu-id="e6de0-122">Scroll down to the dropdown menu shown in the image below, and select "AnchorModuleScript" and click on "GetSharedAnchorNetwork()."</span></span> <span data-ttu-id="e6de0-123">Klicken Sie dann zu speichern.</span><span class="sxs-lookup"><span data-stu-id="e6de0-123">Then save.</span></span>

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a><span data-ttu-id="e6de0-125">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="e6de0-125">Congratulations</span></span>

<span data-ttu-id="e6de0-126">In dieser Lektion haben Sie gelernt, wie Sie Azure leistungsfähige neue räumliche Anker zum Ausrichten von zusammengestellten Geräte in einer freigegebenen Umgebung zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="e6de0-126">In this Lesson you learned how to integrate Azure's powerful new Spatial Anchors to align co-located devices in a shared experience!</span></span> <span data-ttu-id="e6de0-127">In dieser Lektion wird auch das Modul Freigabe abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="e6de0-127">This lesson also concludes the Sharing Module.</span></span> <span data-ttu-id="e6de0-128">Wir haben gelernt, wie zum Einrichten eines neuen Photon-Kontos integrieren Photon und WORTSPIEL in einer neuen Unity-Anwendung, Profilbild und freigegebene Objekte konfigurieren und schließlich Ausrichten von mehreren Beteiligten mit ASA.</span><span class="sxs-lookup"><span data-stu-id="e6de0-128">We learned how to set up a new Photon account, integrate Photon and PUN into a new Unity application, configuring avatars and shared objects, and finally aligning multiple participants using ASA.</span></span> 

