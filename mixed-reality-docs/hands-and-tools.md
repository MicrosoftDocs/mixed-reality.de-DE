---
title: Hand-und Bewegungs Controller
description: Übersicht über die Interaktion von Händen und Bewegungs Controllern
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: Gemischte Realität, Hände, Bewegungs controllen, Interaktion, Entwurf
ms.openlocfilehash: b6efb0a9651cad8eee9b80bb130aa1a85b9a9941
ms.sourcegitcommit: 76a7aa6e64e114b63ace058dd6d6d662b3c9f09e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/26/2019
ms.locfileid: "68507870"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="9bcf0-104">Hand-und Bewegungs Controller</span><span class="sxs-lookup"><span data-stu-id="9bcf0-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="9bcf0-105">Szenarien</span><span class="sxs-lookup"><span data-stu-id="9bcf0-105">Scenarios</span></span>
<span data-ttu-id="9bcf0-106">Wenn Sie sich entscheiden, dieses Interaktionsmodell nach dem Lesen der [Entwurfs Richtlinien](interaction-fundamentals.md)zu übernehmen, bedeutet dies, dass Sie eine Anwendung entwickeln, die es Benutzern ermöglicht, zwei Hände für die Interaktion mit der Holographic World zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="9bcf0-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="9bcf0-107">Ihre Anwendung wird das Ziel erreichen, den BOUNDRY zwischen virtuellen und physischen zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="9bcf0-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="9bcf0-108">Einige spezifische Szenarien können wie folgt lauten:</span><span class="sxs-lookup"><span data-stu-id="9bcf0-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="9bcf0-109">Bereitstellen von Information Workers 2D-Bildschirme und Benutzeroberflächen zum Anzeigen und Steuern von Inhalten</span><span class="sxs-lookup"><span data-stu-id="9bcf0-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="9bcf0-110">Bereitstellen von Tutorials und Handbüchern zu First Line Workers in Werk Zeilen</span><span class="sxs-lookup"><span data-stu-id="9bcf0-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="9bcf0-111">Entwickeln von professionellen Tools für die Unterstützung und Ausbildung von medizinischen Fachleuten</span><span class="sxs-lookup"><span data-stu-id="9bcf0-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="9bcf0-112">Verwenden von virtuellen 3D-Objekten, um die reale Welt zu ergänzen oder eine zweite Welt zu erstellen</span><span class="sxs-lookup"><span data-stu-id="9bcf0-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="9bcf0-113">Erstellen von Location based Services und Games mit der realen Welt als Hintergrund</span><span class="sxs-lookup"><span data-stu-id="9bcf0-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="9bcf0-114">Methoden der Hands-und Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="9bcf0-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[<span data-ttu-id="9bcf0-115">Direkte Manipulation mit den Händen</span><span class="sxs-lookup"><span data-stu-id="9bcf0-115">Direct manipulation with hands</span></span>](direct-manipulation.md)
<span data-ttu-id="9bcf0-116">Dies ist eine Modalität, die die Leistungsfähigkeit nutzt, mit der Benutzer die Hologramme direkt berühren und bearbeiten können.</span><span class="sxs-lookup"><span data-stu-id="9bcf0-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="9bcf0-117">Durch das verbreiten täglicher Lebenszyklus und das Bereitstellen geeigneter visueller Visualisierungen können Benutzer die gleiche Art und Weise verwenden, um reale Objekte so zu manipulieren, dass Sie mit virtuellen Anwendungen interagieren.</span><span class="sxs-lookup"><span data-stu-id="9bcf0-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[<span data-ttu-id="9bcf0-118">Zeigen und Ausführen mit den Händen</span><span class="sxs-lookup"><span data-stu-id="9bcf0-118">Point and commit with hands</span></span>](point-and-commit.md)
<span data-ttu-id="9bcf0-119">Diese Modalität ermöglicht es Benutzern, mit holograms in einer Distanz zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="9bcf0-119">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="9bcf0-120">Sie ermöglicht es Benutzern, die Umgebung optimal zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="9bcf0-120">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="9bcf0-121">Benutzer können Hologramme an jedem beliebigen Ort platzieren und können weiterhin aus beliebigen Entfernungen auf Sie zugreifen.</span><span class="sxs-lookup"><span data-stu-id="9bcf0-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="9bcf0-122">Die mentalen Modelle und Gesten zum Steuern und manipulieren von 2D-und 3D-holograms sind stark synchron mit denen der direkten Bearbeitung.</span><span class="sxs-lookup"><span data-stu-id="9bcf0-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="9bcf0-123">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="9bcf0-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="9bcf0-124">Bewegungs Controller sind Tools, mit denen die physischen Funktionen des Benutzers erweitert werden, indem genaue Interaktionen über einen großen Bereich von Entfernungen bereitgestellt werden, wenn ein oder beide Hände verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="9bcf0-124">Motion controllers are tools that extend the user's physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="9bcf0-125">Diese Hardware Zubehör bieten Verknüpfungen zu vielen häufig verwendeten Interaktionen und bieten unterschiedliche Aktionen, die Sie für eine Reihe von Aktionen durchsuchen können.</span><span class="sxs-lookup"><span data-stu-id="9bcf0-125">These hardware accessories provide shortcuts to many commonly-used interactions and provide surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="9bcf0-126">Derzeit sind Motion-Controller nur für Windows Mixed Reality-Szenarios (WMR) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="9bcf0-126">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 

![Vergleich der Methoden des Hands-und Motion-Controllers](images/Hands-and-controllers-720px.jpg)<br>

<span data-ttu-id="9bcf0-128">*Vergleich der Methoden des Hands-und Motion-Controllers*</span><span class="sxs-lookup"><span data-stu-id="9bcf0-128">*Comparison of hands and motion controllers modalities*</span></span>

## <a name="see-also"></a><span data-ttu-id="9bcf0-129">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="9bcf0-129">See also</span></span>
* [<span data-ttu-id="9bcf0-130">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="9bcf0-130">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="9bcf0-131">Anvisieren mit dem Kopf und Verweilen</span><span class="sxs-lookup"><span data-stu-id="9bcf0-131">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="9bcf0-132">Direkte Manipulation mit den Händen</span><span class="sxs-lookup"><span data-stu-id="9bcf0-132">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="9bcf0-133">Zeigen und Ausführen mit den Händen</span><span class="sxs-lookup"><span data-stu-id="9bcf0-133">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="9bcf0-134">Freihändig</span><span class="sxs-lookup"><span data-stu-id="9bcf0-134">Hands-free</span></span>](hands-free.md)
