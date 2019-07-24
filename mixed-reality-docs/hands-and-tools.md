---
title: Hand-und Bewegungs Controller
description: Übersicht über die Interaktion von Händen und Bewegungs Controllern
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: Gemischte Realität, Hände, Bewegungs controllen, Interaktion, Entwurf
ms.openlocfilehash: d0e54c71ab42a09f2f9c6063a85441b98e729af1
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039167"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="77e8f-104">Hand-und Bewegungs Controller</span><span class="sxs-lookup"><span data-stu-id="77e8f-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="77e8f-105">Szenarien</span><span class="sxs-lookup"><span data-stu-id="77e8f-105">Scenarios</span></span>
<span data-ttu-id="77e8f-106">Wenn Sie sich entscheiden, dieses Interaktionsmodell nach dem Lesen der [Entwurfs Richtlinien](interaction-fundamentals.md)zu übernehmen, bedeutet dies, dass Sie eine Anwendung entwickeln, die es Benutzern ermöglicht, zwei Hände für die Interaktion mit der Holographic World zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="77e8f-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="77e8f-107">Ihre Anwendung wird das Ziel erreichen, den BOUNDRY zwischen virtuellen und physischen zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="77e8f-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="77e8f-108">Einige spezifische Szenarien können wie folgt lauten:</span><span class="sxs-lookup"><span data-stu-id="77e8f-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="77e8f-109">Bereitstellen von Information Workers 2D-Bildschirme und Benutzeroberflächen zum Anzeigen und Steuern von Inhalten</span><span class="sxs-lookup"><span data-stu-id="77e8f-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="77e8f-110">Bereitstellen von Tutorials und Handbüchern zu First Line Workers in Werk Zeilen</span><span class="sxs-lookup"><span data-stu-id="77e8f-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="77e8f-111">Entwickeln von professionellen Tools für die Unterstützung und Ausbildung von medizinischen Fachleuten</span><span class="sxs-lookup"><span data-stu-id="77e8f-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="77e8f-112">Verwenden von virtuellen 3D-Objekten, um die reale Welt zu ergänzen oder eine zweite Welt zu erstellen</span><span class="sxs-lookup"><span data-stu-id="77e8f-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="77e8f-113">Erstellen von Location based Services und Games mit der realen Welt als Hintergrund</span><span class="sxs-lookup"><span data-stu-id="77e8f-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="77e8f-114">Methoden der Hands-und Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="77e8f-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[<span data-ttu-id="77e8f-115">Direkte Manipulation mit den Händen</span><span class="sxs-lookup"><span data-stu-id="77e8f-115">Direct manipulation with hands</span></span>](direct-manipulation.md)
<span data-ttu-id="77e8f-116">Dies ist eine Modalität, die die Leistungsfähigkeit nutzt, mit der Benutzer die Hologramme direkt berühren und bearbeiten können.</span><span class="sxs-lookup"><span data-stu-id="77e8f-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="77e8f-117">Durch das verbreiten täglicher Lebenszyklus und das Bereitstellen geeigneter visueller Visualisierungen können Benutzer die gleiche Art und Weise verwenden, um reale Objekte so zu manipulieren, dass Sie mit virtuellen Anwendungen interagieren.</span><span class="sxs-lookup"><span data-stu-id="77e8f-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[<span data-ttu-id="77e8f-118">Zeigen und Ausführen mit den Händen</span><span class="sxs-lookup"><span data-stu-id="77e8f-118">Point and commit with hands</span></span>](point-and-commit.md)
<span data-ttu-id="77e8f-119">Diese Modalität ermöglicht es Benutzern, mit holograms in einer Distanz zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="77e8f-119">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="77e8f-120">Sie ermöglicht es Benutzern, die Umgebung optimal zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="77e8f-120">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="77e8f-121">Benutzer können Hologramme an jedem beliebigen Ort platzieren und können weiterhin aus beliebigen Entfernungen auf Sie zugreifen.</span><span class="sxs-lookup"><span data-stu-id="77e8f-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="77e8f-122">Die mentalen Modelle und Gesten zum Steuern und manipulieren von 2D-und 3D-holograms sind stark synchron mit denen der direkten Bearbeitung.</span><span class="sxs-lookup"><span data-stu-id="77e8f-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="77e8f-123">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="77e8f-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="77e8f-124">Bewegungs Controller sind Tools, mit denen die physischen Funktionen der Benutzer erweitert werden, indem präzise Interaktionen über einen großen Bereich von Entfernungen bereitgestellt werden, wenn ein oder beide Hände verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="77e8f-124">Motion controllers are tools that extend the users' physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="77e8f-125">Diese Hardware Zubehör bietet Verknüpfungen zu vielen häufig verwendeten Interaktionen und bietet ein untergeordnetes, taktiles Feedback für eine Reihe von Aktionen.</span><span class="sxs-lookup"><span data-stu-id="77e8f-125">These hardware accessories provide shortcuts to many commonly-used interactions and gives surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="77e8f-126">Derzeit sind Motion-Controller nur für WMR-Szenarien verfügbar.</span><span class="sxs-lookup"><span data-stu-id="77e8f-126">Currently, motion controllers are only available for WMR scenarios.</span></span> 

![](images/Hands-and-controllers-720px.jpg)<br>

## <a name="see-also"></a><span data-ttu-id="77e8f-127">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="77e8f-127">See also</span></span>
* [<span data-ttu-id="77e8f-128">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="77e8f-128">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="77e8f-129">Anvisieren mit dem Kopf und Verweilen</span><span class="sxs-lookup"><span data-stu-id="77e8f-129">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="77e8f-130">Direkte Manipulation mit den Händen</span><span class="sxs-lookup"><span data-stu-id="77e8f-130">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="77e8f-131">Zeigen und Ausführen mit den Händen</span><span class="sxs-lookup"><span data-stu-id="77e8f-131">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="77e8f-132">Freihändig</span><span class="sxs-lookup"><span data-stu-id="77e8f-132">Hands-free</span></span>](hands-free.md)
