---
title: 'Fallstudie: Lektionen aus der-Küche von Lowe'
description: Das hololens-Team möchte einige bewährte Methoden gemeinsam nutzen, die aus dem hololens-Projekt von Lowe abgeleitet wurden.
author: brandonbray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Lowe es, hololens, Küche, Fallstudie
ms.openlocfilehash: a6bd7a09f77fb71dc23dc640525ff250abac8f12
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278128"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a><span data-ttu-id="7dd25-104">Fallstudie: Lektionen aus der-Küche von Lowe</span><span class="sxs-lookup"><span data-stu-id="7dd25-104">Case study - Lessons from the Lowe's kitchen</span></span>

<span data-ttu-id="7dd25-105">Das hololens-Team möchte einige bewährte Methoden gemeinsam nutzen, die aus dem hololens-Projekt von Lowe abgeleitet wurden.</span><span class="sxs-lookup"><span data-stu-id="7dd25-105">The HoloLens team wants to share some of the best practices that were derived from the Lowe's HoloLens project.</span></span> <span data-ttu-id="7dd25-106">Im folgenden finden Sie ein Video der in der 2016 Ignite-Keynote von satya projizierten hololens von Lowe.</span><span class="sxs-lookup"><span data-stu-id="7dd25-106">Below is a video of the Lowe's HoloLens projected demonstrated at Satya's 2016 Ignite keynote.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a><span data-ttu-id="7dd25-107">Die bewährten Methoden von Lowe hololens</span><span class="sxs-lookup"><span data-stu-id="7dd25-107">Lowe's HoloLens Best Practices</span></span>

<span data-ttu-id="7dd25-108">In den beiden Videos werden bewährte Methoden behandelt, die aus dem hololens-Pilot Programm von Lowe abgeleitet wurden, das seit dem 2016. April in zwei Lowe-Filialen enthalten war.</span><span class="sxs-lookup"><span data-stu-id="7dd25-108">The two videos cover best practices that were derived from the Lowe's HoloLens Pilot that has been in two Lowe's stores since April 2016.</span></span> <span data-ttu-id="7dd25-109">Wichtige Themen:</span><span class="sxs-lookup"><span data-stu-id="7dd25-109">The key topics are:</span></span>
* <span data-ttu-id="7dd25-110">Maximieren der Leistung für ein mobiles Gerät</span><span class="sxs-lookup"><span data-stu-id="7dd25-110">Maximize performance for a mobile device</span></span>
* <span data-ttu-id="7dd25-111">Erstellen von UX-Methoden mit einem vollständigen Holographic-Frame (2. Gespräch)</span><span class="sxs-lookup"><span data-stu-id="7dd25-111">Create UX methods with a full holographic frame (2nd talk)</span></span>
* <span data-ttu-id="7dd25-112">Genauigkeits Ausrichtung (2. Gespräch)</span><span class="sxs-lookup"><span data-stu-id="7dd25-112">Precision alignment (2nd talk)</span></span>
* <span data-ttu-id="7dd25-113">Freigegebene holografische Oberflächen (2. Gespräch)</span><span class="sxs-lookup"><span data-stu-id="7dd25-113">Shared holographic experiences (2nd talk)</span></span>
* <span data-ttu-id="7dd25-114">Interaktion mit Kunden (2. Gespräch)</span><span class="sxs-lookup"><span data-stu-id="7dd25-114">Interacting with customers (2nd talk)</span></span>

## <a name="video-1"></a><span data-ttu-id="7dd25-115">Video 1</span><span class="sxs-lookup"><span data-stu-id="7dd25-115">Video 1</span></span>

<span data-ttu-id="7dd25-116">**Maximieren der Leistung für ein mobiles Gerät** Hololens ist ein unverbundenes Gerät, bei dem die gesamte Verarbeitung auf dem Gerät stattfindet.</span><span class="sxs-lookup"><span data-stu-id="7dd25-116">**Maximize performance for a mobile device** HoloLens is an untethered device with all the processing taking place in the device.</span></span> <span data-ttu-id="7dd25-117">Hierfür ist eine mobile Plattform erforderlich, und es wird eine Denkweise benötigt, die der Erstellung mobiler Anwendungen ähnelt.</span><span class="sxs-lookup"><span data-stu-id="7dd25-117">This requires a mobile platform and requires a mindset similar to creating mobile applications.</span></span> <span data-ttu-id="7dd25-118">Microsoft empfiehlt, dass Ihre hololens-Anwendung 60fps beibehält, um Ihren Benutzern eine köstliche Benutzerfunktion bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="7dd25-118">Microsoft recommends that your HoloLens application maintain 60FPS to provide a delicious experience for your users.</span></span> <span data-ttu-id="7dd25-119">Ein niedriges fps kann zu instabilen holograms führen.</span><span class="sxs-lookup"><span data-stu-id="7dd25-119">Having low FPS can result in unstable holograms.</span></span>

<span data-ttu-id="7dd25-120">Einige der wichtigsten Aspekte, die bei der Entwicklung von hololens zu beachten sind, sind die Asset-Optimierung/-Entschlüsselung mit benutzerdefinierten Shadern (kostenlos verfügbar im [hololens-Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span><span class="sxs-lookup"><span data-stu-id="7dd25-120">Some of the most important things to look at when developing on HoloLens is asset optimization/decimation, using custom shaders (available for free in the [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span></span> <span data-ttu-id="7dd25-121">Ein weiterer wichtiger Aspekt ist die Messung der Framerate von dem Anfang des Projekts.</span><span class="sxs-lookup"><span data-stu-id="7dd25-121">Another important consideration is to measure the frame rate from the very beginning of your project.</span></span> <span data-ttu-id="7dd25-122">Abhängig vom Projekt kann die Reihenfolge der Anzeige Ihrer Assets auch ein großer Mitwirkender sein.</span><span class="sxs-lookup"><span data-stu-id="7dd25-122">Depending on the project, the order of displaying your assets can also be a big contributor</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a><span data-ttu-id="7dd25-123">Video 2</span><span class="sxs-lookup"><span data-stu-id="7dd25-123">Video 2</span></span>

<span data-ttu-id="7dd25-124">**Erstellen von UX-Methoden mit einem vollständigen Holographic-Frame** Es ist wichtig, die Platzierung von holograms in einer physischen Welt zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="7dd25-124">**Create UX methods with a full holographic frame** It's important to understand the placement of holograms in a physical world.</span></span> <span data-ttu-id="7dd25-125">Mit Lowe sprechen wir über verschiedene UX-Methoden, die Benutzern dabei helfen, Hologramme zu schließen, während Sie immer noch die größere Umgebung von holograms sehen.</span><span class="sxs-lookup"><span data-stu-id="7dd25-125">With Lowe's we talk about different UX methods that help users experience holograms up close while still seeing the larger environment of holograms.</span></span>

<span data-ttu-id="7dd25-126">**Genauigkeits Ausrichtung** Für das Lowe-Szenario war es von entscheidender Bedeutung, die Genauigkeit der Hologramme an die physische Küche anzupassen.</span><span class="sxs-lookup"><span data-stu-id="7dd25-126">**Precision alignment** For the Lowe's scenario, it was paramount to the experience to have precision alignment of the holograms to the physical kitchen.</span></span> <span data-ttu-id="7dd25-127">Es wird erläutert, wie Sie eine Benutzerumgebung sicherstellen, die Benutzer überzeugt, dass sich ihre physische Umgebung geändert hat.</span><span class="sxs-lookup"><span data-stu-id="7dd25-127">We discuss techniques helps ensure an experience that convinces users that their physical environment has changed.</span></span>

<span data-ttu-id="7dd25-128">Frei **gegebene holografische Erfahrungen** Paare sind die primäre Methode, mit der die Lowe-Darstellung genutzt wird.</span><span class="sxs-lookup"><span data-stu-id="7dd25-128">**Shared holographic experiences** Couples are the primary way that the Lowe's experience is consumed.</span></span> <span data-ttu-id="7dd25-129">Eine Person kann den gegen oberen Rand ändern, und die andere Person wird die Änderungen sehen.</span><span class="sxs-lookup"><span data-stu-id="7dd25-129">One person can change the countertop and the other person will see the changes.</span></span> <span data-ttu-id="7dd25-130">Wir haben dies als "Shared Erlebnisse" bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="7dd25-130">We called this "shared experiences".</span></span>

<span data-ttu-id="7dd25-131">**Interaktion mit Kunden** Die Designer von Lowe verwenden keine hololens, aber Sie müssen sehen, was die Kunden sehen.</span><span class="sxs-lookup"><span data-stu-id="7dd25-131">**Interacting with customers** Lowe's designers are not using a HoloLens, but they need to see what the customers are seeing.</span></span> <span data-ttu-id="7dd25-132">Wir zeigen, wie der Kunde in einer UWP-Anwendung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="7dd25-132">We show how to capture what the customer is seeing on a UWP application.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
