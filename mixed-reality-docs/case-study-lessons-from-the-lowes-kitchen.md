---
title: 'Fallstudie: Lektionen aus der Lowes Küche'
description: Die HoloLens-Team möchte freigeben, einige bewährte Methoden, die von der Lowes HoloLens-Projekt abgeleitet wurden.
author: BrandonBray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Lowes, HoloLens, Küche, Fallstudie
ms.openlocfilehash: 24759f90b8b84ec19e644fb8dff44f64c3ab81d2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594164"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a><span data-ttu-id="62c98-104">Fallstudie: Lektionen aus der Lowes Küche</span><span class="sxs-lookup"><span data-stu-id="62c98-104">Case study - Lessons from the Lowe's kitchen</span></span>

<span data-ttu-id="62c98-105">Die HoloLens-Team möchte freigeben, einige bewährte Methoden, die von der Lowes HoloLens-Projekt abgeleitet wurden.</span><span class="sxs-lookup"><span data-stu-id="62c98-105">The HoloLens team wants to share some of the best practices that were derived from the Lowe's HoloLens project.</span></span> <span data-ttu-id="62c98-106">Im folgenden wird ein Video zu den Lowes HoloLens projiziert an Satyas 2016 Ignite-Keynote veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="62c98-106">Below is a video of the Lowe's HoloLens projected demonstrated at Satya's 2016 Ignite keynote.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a><span data-ttu-id="62c98-107">Die Lowe HoloLens bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="62c98-107">Lowe's HoloLens Best Practices</span></span>

<span data-ttu-id="62c98-108">Die beiden Videos werden bewährte Methoden, die von der Lowes HoloLens Pilotprojekt abgeleitet wurden, die in zwei Lowe speichern seit April 2016 wurden behandelt.</span><span class="sxs-lookup"><span data-stu-id="62c98-108">The two videos cover best practices that were derived from the Lowe's HoloLens Pilot that has been in two Lowe's stores since April 2016.</span></span> <span data-ttu-id="62c98-109">Die wichtigsten Themen sind:</span><span class="sxs-lookup"><span data-stu-id="62c98-109">The key topics are:</span></span>
* <span data-ttu-id="62c98-110">Maximieren der Leistung für ein mobiles Gerät</span><span class="sxs-lookup"><span data-stu-id="62c98-110">Maximize performance for a mobile device</span></span>
* <span data-ttu-id="62c98-111">Erstellen von UX-Methoden mit einem vollständigen holographic Rahmen (2. Talk)</span><span class="sxs-lookup"><span data-stu-id="62c98-111">Create UX methods with a full holographic frame (2nd talk)</span></span>
* <span data-ttu-id="62c98-112">Genauigkeit Ausrichtung (2. Talk)</span><span class="sxs-lookup"><span data-stu-id="62c98-112">Precision alignment (2nd talk)</span></span>
* <span data-ttu-id="62c98-113">Freigegebene holographic Erfahrungen (2. Talk)</span><span class="sxs-lookup"><span data-stu-id="62c98-113">Shared holographic experiences (2nd talk)</span></span>
* <span data-ttu-id="62c98-114">Interaktion mit Kunden (2. Talk)</span><span class="sxs-lookup"><span data-stu-id="62c98-114">Interacting with customers (2nd talk)</span></span>

## <a name="video-1"></a><span data-ttu-id="62c98-115">Video 1</span><span class="sxs-lookup"><span data-stu-id="62c98-115">Video 1</span></span>

<span data-ttu-id="62c98-116">**Maximieren der Leistung für ein mobiles Gerät** HoloLens ist ein unabhängig Gerät mit der Verarbeitung, die für die stattfinden, auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="62c98-116">**Maximize performance for a mobile device** HoloLens is an untethered device with all the processing taking place in the device.</span></span> <span data-ttu-id="62c98-117">Dies erfordert eine mobile Plattform und eine Haltung, die ähnlich wie beim Erstellen von mobiler Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="62c98-117">This requires a mobile platform and requires a mindset similar to creating mobile applications.</span></span> <span data-ttu-id="62c98-118">Microsoft empfiehlt, dass Ihre Anwendung HoloLens 60 FPS eine köstliche Erfahrung für Ihre Benutzer zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="62c98-118">Microsoft recommends that your HoloLens application maintain 60FPS to provide a delicious experience for your users.</span></span> <span data-ttu-id="62c98-119">Niedrige FPS kann instabil Hologramme dazu führen, dass.</span><span class="sxs-lookup"><span data-stu-id="62c98-119">Having low FPS can result in unstable holograms.</span></span>

<span data-ttu-id="62c98-120">Einige der wichtigsten Dinge betrachten, bei der Entwicklung für HoloLens Asset mit benutzerdefinierten Shadern Optimierung/Decimation ist (kostenlos in die [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span><span class="sxs-lookup"><span data-stu-id="62c98-120">Some of the most important things to look at when developing on HoloLens is asset optimization/decimation, using custom shaders (available for free in the [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span></span> <span data-ttu-id="62c98-121">Ein weiterer wichtiger Aspekt ist die Einzelbildrate vom Anfang des Projekts zu messen.</span><span class="sxs-lookup"><span data-stu-id="62c98-121">Another important consideration is to measure the frame rate from the very beginning of your project.</span></span> <span data-ttu-id="62c98-122">Je nach Projekt kann die Reihenfolge der Anzeige Ihrer Ressourcen auch große Mitwirkender sein</span><span class="sxs-lookup"><span data-stu-id="62c98-122">Depending on the project, the order of displaying your assets can also be a big contributor</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a><span data-ttu-id="62c98-123">Video 2</span><span class="sxs-lookup"><span data-stu-id="62c98-123">Video 2</span></span>

<span data-ttu-id="62c98-124">**Erstellen von UX-Methoden mit einem vollständigen holographic Rahmen** es ist wichtig zu verstehen, die Platzierung von Hologramme in einer physischen Welt.</span><span class="sxs-lookup"><span data-stu-id="62c98-124">**Create UX methods with a full holographic frame** It's important to understand the placement of holograms in a physical world.</span></span> <span data-ttu-id="62c98-125">Mit der Lowe sprechen wir über verschiedene UX-Methoden, die Benutzern helfen, schließen Sie Erfahrung Hologramme einrichten, während weiterhin angezeigt wird der größere Umgebung Hologramme, aus.</span><span class="sxs-lookup"><span data-stu-id="62c98-125">With Lowe's we talk about different UX methods that help users experience holograms up close while still seeing the larger environment of holograms.</span></span>

<span data-ttu-id="62c98-126">**Genauigkeit Ausrichtung** für die Lowe Szenario war es entscheidend für die Erfahrung, um die Genauigkeit der Hologramme Ausrichtung auf der physischen Küche haben.</span><span class="sxs-lookup"><span data-stu-id="62c98-126">**Precision alignment** For the Lowe's scenario, it was paramount to the experience to have precision alignment of the holograms to the physical kitchen.</span></span> <span data-ttu-id="62c98-127">Erläutert Techniken, die eine Erfahrung trägt so dazu, die Benutzer überredet, die ihrer physischen Umgebung geändert wurde.</span><span class="sxs-lookup"><span data-stu-id="62c98-127">We discuss techniques helps ensure an experience that convinces users that their physical environment has changed.</span></span>

<span data-ttu-id="62c98-128">**Freigegebene holographic Erfahrungen** koppelt sind der einfachste Weg, dass die Lowes Benutzeroberfläche verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="62c98-128">**Shared holographic experiences** Couples are the primary way that the Lowe's experience is consumed.</span></span> <span data-ttu-id="62c98-129">Eine Person kann die Arbeitsplatte ändern, und der andere Benutzer sehen die Änderungen.</span><span class="sxs-lookup"><span data-stu-id="62c98-129">One person can change the countertop and the other person will see the changes.</span></span> <span data-ttu-id="62c98-130">Wir haben Sie angerufen dieser "freigegebene Umgebungen".</span><span class="sxs-lookup"><span data-stu-id="62c98-130">We called this "shared experiences".</span></span>

<span data-ttu-id="62c98-131">**Interaktion mit Kunden** Lowes Designer eine HoloLens nicht verwenden, aber sie benötigen, um festzustellen, was die Kunden angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="62c98-131">**Interacting with customers** Lowe's designers are not using a HoloLens, but they need to see what the customers are seeing.</span></span> <span data-ttu-id="62c98-132">Wir zeigen, wie zum Erfassen, was der Kunde auf eine UWP-Anwendung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="62c98-132">We show how to capture what the customer is seeing on a UWP application.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
