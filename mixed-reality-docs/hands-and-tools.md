---
title: Praktische und Motion-Controller
description: Übersicht über die praktische und Interaktion der Motion-Controller
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: Mixed Reality, praktische, während der Übertragung Controlles, Interaktion, Entwerfen
ms.openlocfilehash: b13efadd111ca970abe625221fb8045644822c37
ms.sourcegitcommit: b5bad4eeb5cdd0c2a7b639442656c306e8b5853b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65813983"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="6f6ab-104">Praktische und Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="6f6ab-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="6f6ab-105">Szenarien</span><span class="sxs-lookup"><span data-stu-id="6f6ab-105">Scenarios</span></span>
<span data-ttu-id="6f6ab-106">Möchten Sie Sie nach dem Lesen dieses Interaktionsmodells zu übernehmen die [Entwurfsrichtlinien](interaction-fundamentals.md), dies bedeutet, dass Sie eine Anwendung, die benutzerregistrierung zwei Händen zu verwenden, für die Interaktion mit der holographic Welt entwickeln.</span><span class="sxs-lookup"><span data-stu-id="6f6ab-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="6f6ab-107">Die Anwendung wird das Ziel des Entfernens der ist zwischen virtuellen und physischen zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="6f6ab-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="6f6ab-108">Unter Umständen einige spezifischen Szenarien:</span><span class="sxs-lookup"><span data-stu-id="6f6ab-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="6f6ab-109">Bereitstellen von Informationen Worker 2D virtuellen Bildschirme und Benutzeroberflächen zum Anzeigen und Steuern von Inhalt</span><span class="sxs-lookup"><span data-stu-id="6f6ab-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="6f6ab-110">Bereitstellen von ersten Zeile-Worker-Lernprogramme und Anleitungen in den Zeilen der Factory-assembly</span><span class="sxs-lookup"><span data-stu-id="6f6ab-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="6f6ab-111">Entwickeln von professionellen Tools für die Unterstützung und Schulung von medizinischen-Experten</span><span class="sxs-lookup"><span data-stu-id="6f6ab-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="6f6ab-112">Virtuelle 3D-Objekte verwenden, die reale Welt zu ergänzen oder erstellen eine zweite Welt</span><span class="sxs-lookup"><span data-stu-id="6f6ab-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="6f6ab-113">Speicherort basiert, Dienste und Spiele mit der realen Welt als Hintergrund</span><span class="sxs-lookup"><span data-stu-id="6f6ab-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="6f6ab-114">Praktische und während der Übertragung Controller Modalitäten</span><span class="sxs-lookup"><span data-stu-id="6f6ab-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[<span data-ttu-id="6f6ab-115">Direkte Manipulation mit den Händen</span><span class="sxs-lookup"><span data-stu-id="6f6ab-115">Direct manipulation with hands</span></span>](direct-manipulation.md)
<span data-ttu-id="6f6ab-116">Dies ist eine Modalität geschieht durch Nutzung der Hand, mit denen Benutzer berührt und die Hologramme direkt bearbeiten können.</span><span class="sxs-lookup"><span data-stu-id="6f6ab-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="6f6ab-117">Durch Leaveraging tagtäglich hat und Bereitstellung richtigen visual visueller Hinweise, Benutzer können die gleiche Weise für die Bearbeitung von realen Objekten zu verwenden, um mit virtuellen interagieren.</span><span class="sxs-lookup"><span data-stu-id="6f6ab-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[<span data-ttu-id="6f6ab-118">Zeigen und Ausführen mit den Händen</span><span class="sxs-lookup"><span data-stu-id="6f6ab-118">Point and commit with hands</span></span>](point-and-commit.md)
<span data-ttu-id="6f6ab-119">Dieser Modalität ermöglicht Benutzern die Interaktion mit Hologramme in einem Abstand.</span><span class="sxs-lookup"><span data-stu-id="6f6ab-119">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="6f6ab-120">Sie können Benutzer die beste Umgebung zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="6f6ab-120">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="6f6ab-121">Benutzer Hologramme können an einer beliebigen Stelle platzieren, und können weiterhin greifen sie von jedem entfernungen.</span><span class="sxs-lookup"><span data-stu-id="6f6ab-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="6f6ab-122">Die mentalen Modelle und Gesten für die Steuerung und Bearbeiten von 2D- und 3D-Spiele Hologramme hoch synchron sind mit denen der direkten Bearbeitung.</span><span class="sxs-lookup"><span data-stu-id="6f6ab-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="6f6ab-123">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="6f6ab-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="6f6ab-124">Während der Übertragung Controller sind Tools, die physische Kapazität des Benutzers zu erweitern, indem Sie präzise Interaktionen über eine große Auswahl von entfernungen bereitstellen, bei der Verwendung von einem oder beiden Hände.</span><span class="sxs-lookup"><span data-stu-id="6f6ab-124">Motion controllers are tools that extend the users' physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="6f6ab-125">Diese Hardwarezubehör bieten Verknüpfungen zu viele häufig verwendete Interaktionen und bietet surefooted, praktisch Feedback für eine Vielzahl von Aktionen.</span><span class="sxs-lookup"><span data-stu-id="6f6ab-125">These hardware accessories provide shortcuts to many commonly-used interactions and gives surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="6f6ab-126">Motion-Controller sind derzeit nur für WMR Szenarien verfügbar.</span><span class="sxs-lookup"><span data-stu-id="6f6ab-126">Currently, motion controllers are only available for WMR scenarios.</span></span> 

![](images/Hands-and-controllers-720px.jpg)<br>

## <a name="see-also"></a><span data-ttu-id="6f6ab-127">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="6f6ab-127">See also</span></span>
* [<span data-ttu-id="6f6ab-128">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="6f6ab-128">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="6f6ab-129">Direkte Bearbeitung (in der Nähe von Hand-Aktivität)</span><span class="sxs-lookup"><span data-stu-id="6f6ab-129">Direct manipulation (Near hand interaction)</span></span>](direct-manipulation.md)
* [<span data-ttu-id="6f6ab-130">Punkt- und Commit (weit Hand Interaktion)</span><span class="sxs-lookup"><span data-stu-id="6f6ab-130">Point and commit (Far hand interaction)</span></span>](point-and-commit.md)
* [<span data-ttu-id="6f6ab-131">Freihändig</span><span class="sxs-lookup"><span data-stu-id="6f6ab-131">Hands-free</span></span>](hands-free.md)
* [<span data-ttu-id="6f6ab-132">Anvisieren und Verweilen</span><span class="sxs-lookup"><span data-stu-id="6f6ab-132">Gaze and dwell</span></span>](gaze-targeting.md)
