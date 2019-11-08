---
title: Instinktive Interaktionen
description: Lernen Sie die Philosophie der einfachen, instinktiven Interaktionen kennen, die in der gesamten Mixed Reality-Plattform verwurzelt ist.
author: shengkait
ms.author: shentan
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Anvisieren, Zielbestimmung, Interaktion, Entwurf, Hololens, MMR, kombiniert
ms.openlocfilehash: abd82947be08a2f6aecc4462abc34c4674abfb7a
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437973"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="3d4eb-104">Einführung in instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="3d4eb-104">Introducing instinctual interactions</span></span>

<span data-ttu-id="3d4eb-105">Die Philosophie der einfachen, instinktiven Interaktionen ist in der gesamten Mixed Reality-Plattform (MR) verwurzelt.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-105">The philosophy of simple, instinctual interactions is interwoven throughout the mixed reality (MR) platform.</span></span> <span data-ttu-id="3d4eb-106">Wir haben drei Schritte unternommen, um sicherzustellen, dass Anwendungsdesigner und -entwickler ihren Kunden einfache und intuitive Interaktionen bereitstellen können.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-106">We've taken three steps to ensure that application designers and developers can provide their customers with easy and intuitive interactions.</span></span> 

<span data-ttu-id="3d4eb-107">Zunächst haben wir sichergestellt, dass sich unsere Sensoren und Eingabetechnologien (die Hand- und Eyetracking sowie natürliche Spracheingabe umfassen) zu nahtlos kombinierten Interaktionsmodellen verbinden.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-107">First, we've made sure our sensors and input technologies (which includes hand and eye tracking along with natural language input) combine into seamless, multimodal interaction models.</span></span>  
<span data-ttu-id="3d4eb-108">Basierend auf unseren Studien ist das kombinierte Entwerfen und Entwickeln in einem multimodalen Framework – und nicht die Fokussierung auf einzelne Eingaben – der Schlüssel zur Realisierung instinktiver Erfahrungen.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-108">Based on our research, designing and developing within a multimodal framework (and not based on individual inputs) is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="3d4eb-109">Zweitens haben wir erkannt, dass viele Entwickler auf mehrere HoloLens-Geräte ausgerichtet sind, z. B. HoloLens 2 und HoloLens (1. Generation) oder HoloLens und VR.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-109">Second, we recognize that many developers target multiple HoloLens devices, such as HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  
<span data-ttu-id="3d4eb-110">Deshalb haben wir unsere Interaktionsmodelle so konzipiert, dass sie geräteübergreifend funktionieren, auch wenn die Eingabetechnologie von Gerät zu Gerät variiert.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-110">So we've designed our interaction models to work across devices, even if the input technology varies on each device.</span></span>  
<span data-ttu-id="3d4eb-111">So verwenden z. B. die ferne Interaktion bei einem Windows Immersive Headset mit einem 6DoF-Controller und die ferne Interaktion bei HoloLens 2 jeweils dieselben Angebote und Muster, was die geräteübergreifende Anwendungsentwicklung erleichtert und den Benutzerinteraktionen ein natürliches Gefühl verleiht.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-111">For example, far interaction on a Windows Immersive headset with a 6DoF controller and far interaction on a HoloLens 2 both use identical affordances and patterns, making it easy for cross-device application development and providing a natural feel to user interactions.</span></span> 

<span data-ttu-id="3d4eb-112">Wir haben zwar erkannt, dass Mixed Reality (MR) Tausende von effektiven, ansprechenden und einzigartigen Interaktionen bietet, aber wir haben festgestellt, dass der bewusste Einsatz eines einzelnen umfassenden Interaktionsmodells in einer Anwendung der beste Weg ist, um sicherzustellen, dass Benutzer erfolgreich sind und ein großartiges Erlebnis haben.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-112">While we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we've found that intentionally employing a single interaction model end-to-end in an application is the best way to ensure users are successful and have a great experience.</span></span> <span data-ttu-id="3d4eb-113">Zu diesem Zweck haben wir drei Punkte in diese Interaktionsanleitung einbezogen:</span><span class="sxs-lookup"><span data-stu-id="3d4eb-113">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="3d4eb-114">Diese Anleitung um die drei primären Interaktionsmodelle und die für jedes einzelne Modell erforderlichen Komponenten und Muster.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-114">Specific guidance around the three primary interaction models and the components and patterns required for each.</span></span>
* <span data-ttu-id="3d4eb-115">Zusätzliche Anleitungen zu weiteren Vorteilen, die unsere Plattform bietet.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-115">Supplemental guidance about other benefits that our platform provides.</span></span>
* <span data-ttu-id="3d4eb-116">Allgemeine Anleitungen zur Auswahl des geeigneten Interaktionsmodells für Ihr Entwicklungsszenario.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-116">General guidance to help select the appropriate interaction model for your development scenario.</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="3d4eb-117">Kombinierte Interaktionsmodelle</span><span class="sxs-lookup"><span data-stu-id="3d4eb-117">Multimodal interaction models</span></span>

<span data-ttu-id="3d4eb-118">Basierend auf unseren bisherigen Studien sowie dem Feedback von Kunden haben wir festgestellt, dass drei primäre Interaktionsmodelle für die meisten Mixed Reality-Umgebungen geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-118">Based on our research and feedback from customers, we've discovered that three primary interaction models suit the majority of mixed reality experiences.</span></span> <span data-ttu-id="3d4eb-119">In vielerlei Hinsicht ist das Interaktionsmodell das mentale Modell des Benutzers zur Durchführung eines Workflows.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-119">In many ways, the interaction model is the user's mental model for how to complete a workflow.</span></span> <span data-ttu-id="3d4eb-120">Jedes dieser Interaktionsmodelle ist für eine Reihe von Kundenanforderungen optimiert und ist bei richtiger Anwendung benutzerfreundlich, leistungsstark und praktikabel.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-120">Each of these interaction models is optimized for a set of customer needs and is convenient, powerful, and usable when used correctly.</span></span> 

<span data-ttu-id="3d4eb-121">Das folgende Diagramm stellt eine vereinfachte Übersicht dar.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-121">The chart below is a simplified overview.</span></span> <span data-ttu-id="3d4eb-122">Ausführliche Informationen zur Verwendung der einzelnen Interaktionsmodelle sind auf den folgenden Seiten mit Bildern und Codebeispielen verknüpft.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-122">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="3d4eb-123"><strong>Modell</strong></span><span class="sxs-lookup"><span data-stu-id="3d4eb-123"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="3d4eb-124"><strong>Beispielszenarien</strong></span><span class="sxs-lookup"><span data-stu-id="3d4eb-124"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="3d4eb-125"><strong>Eignung</strong></span><span class="sxs-lookup"><span data-stu-id="3d4eb-125"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="3d4eb-126"><strong>Hardware</strong></span><span class="sxs-lookup"><span data-stu-id="3d4eb-126"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3d4eb-127"><a href="hands-and-tools.md">Hände und Motion-Controller</a></span><span class="sxs-lookup"><span data-stu-id="3d4eb-127"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="3d4eb-128">3D-Raumerlebnisse, z. B. räumliches Layout und räumlicher Entwurf, Inhaltsmanipulation oder Simulation.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-128">3D spatial experiences, such as spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="3d4eb-129">Ideal für neue Benutzer, kombiniert mit Stimme, Eyetracking oder Anvisieren mit dem Kopf.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-129">Great for new users coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="3d4eb-130">Niedrige Lernkurve.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-130">Low learning curve.</span></span> <span data-ttu-id="3d4eb-131">Konsistente Benutzererfahrung für Handtracking und Controller mit 6 Freiheitsgraden.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-131">Consistent UX across hand tracking and 6DoF controllers.</span></span></td>
        <td><span data-ttu-id="3d4eb-132">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3d4eb-132">HoloLens 2</span></span><br><span data-ttu-id="3d4eb-133">Immersive Headsets</span><span class="sxs-lookup"><span data-stu-id="3d4eb-133">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3d4eb-134"><a href="hands-free.md">Freihändig</a></span><span class="sxs-lookup"><span data-stu-id="3d4eb-134"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="3d4eb-135">Kontextbezogene Erfahrungen, bei denen die Hände eines Benutzers beschäftigt sind, z. B. praxisnahes Lernen und Wartung.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-135">Contextual experiences where a user's hands are occupied, such as on-the-job learning and maintenance.</span></span></td>
        <td><span data-ttu-id="3d4eb-136">Gewisser Lernaufwand erforderlich.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-136">Some learning required.</span></span> <span data-ttu-id="3d4eb-137">Das Gerät ist gut für Stimme und natürliche Sprache geeignet, wenn die Hände nicht verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-137">If hands are unavailable, the device pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="3d4eb-138">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3d4eb-138">HoloLens 2</span></span><br><span data-ttu-id="3d4eb-139">HoloLens (1. Generation)</span><span class="sxs-lookup"><span data-stu-id="3d4eb-139">HoloLens (1st gen)</span></span><br><span data-ttu-id="3d4eb-140">Immersive Headsets</span><span class="sxs-lookup"><span data-stu-id="3d4eb-140">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3d4eb-141"><a href="gaze-and-commit.md">Anvisieren und Ausführen</a></span><span class="sxs-lookup"><span data-stu-id="3d4eb-141"><a href="gaze-and-commit.md">Gaze and commit</a></span></span></td>
        <td><span data-ttu-id="3d4eb-142">Click-Through-Erfahrungen, z. B. 3D-Präsentationen, Demos.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-142">Click-through experiences, e.g. 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="3d4eb-143">Erfordert Training für HMDs, aber nicht für mobile Geräte.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-143">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="3d4eb-144">Ideal für verfügbare Controller.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-144">Best for accessible controllers.</span></span> <span data-ttu-id="3d4eb-145">Ideal für HoloLens (1. Generation).</span><span class="sxs-lookup"><span data-stu-id="3d4eb-145">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="3d4eb-146">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3d4eb-146">HoloLens 2</span></span><br><span data-ttu-id="3d4eb-147">HoloLens (1. Generation)</span><span class="sxs-lookup"><span data-stu-id="3d4eb-147">HoloLens (1st gen)</span></span><br><span data-ttu-id="3d4eb-148">Immersive Headsets</span><span class="sxs-lookup"><span data-stu-id="3d4eb-148">Immersive headsets</span></span><br><span data-ttu-id="3d4eb-149">Mobile AR</span><span class="sxs-lookup"><span data-stu-id="3d4eb-149">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="3d4eb-150">Die beste Möglichkeit, um sicherzustellen, dass es keine Lücken bei der Interaktion für Ihr Erlebnis gibt, besteht darin, der Anleitung für ein einzelnes Modell von Anfang bis Ende zu folgen.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-150">To ensure that there are no gaps in the user interaction experience, it is best to follow the guidance for a single model from beginning to end.</span></span>

<span data-ttu-id="3d4eb-151">Die folgenden Abschnitte führen durch die Schritte zur Auswahl und Implementierung eines dieser Interaktionsmodelle.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-151">The sections below walk through the steps for selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="3d4eb-152">Am Ende dieser Seite werden Sie unsere Anleitung zu Folgendem verstehen:</span><span class="sxs-lookup"><span data-stu-id="3d4eb-152">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="3d4eb-153">Auswählen eines Interaktionsmodells für Ihren Kunden</span><span class="sxs-lookup"><span data-stu-id="3d4eb-153">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="3d4eb-154">Implementieren des Interaktionsmodells</span><span class="sxs-lookup"><span data-stu-id="3d4eb-154">Implementing the interaction model</span></span>
* <span data-ttu-id="3d4eb-155">Wechseln zwischen Interaktionsmodellen</span><span class="sxs-lookup"><span data-stu-id="3d4eb-155">Transitioning between interaction models</span></span>
* <span data-ttu-id="3d4eb-156">Entwerfen der nächsten Schritte</span><span class="sxs-lookup"><span data-stu-id="3d4eb-156">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="3d4eb-157">Auswählen eines Interaktionsmodells für Ihren Kunden</span><span class="sxs-lookup"><span data-stu-id="3d4eb-157">Choose an interaction model for your customer</span></span>

<span data-ttu-id="3d4eb-158">In der Regel haben Entwickler und Ersteller die Arten von Interaktionen, die Ihre Kunden ausführen können, bereits durchdacht.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-158">Typically, developers and creators have thought through the types of interactions that their customers can have.</span></span> <span data-ttu-id="3d4eb-159">Um einen kundenorientierten Ansatz für den Entwurf zu fördern, empfehlen wir Ihnen die folgende Anleitung zur Auswahl des für Ihren Kunden optimierten Interaktionsmodells.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-159">To encourage a customer-focused approach to design, we recommend the following guidance for selecting the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="3d4eb-160">Gründe zum Befolgen dieser Anleitung</span><span class="sxs-lookup"><span data-stu-id="3d4eb-160">Why follow this guidance?</span></span>

* <span data-ttu-id="3d4eb-161">Unsere Interaktionsmodelle werden auf objektive und subjektive Kriterien wie physische und kognitive Leistung, Intuitivität und Erlernbarkeit getestet.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-161">Our interaction models are tested for objective and subjective criteria, such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="3d4eb-162">Da die Interaktion unterschiedlich verläuft, können sich auch die visuellen/akustischen Angebote sowie das Objektverhalten zwischen Interaktionsmodellen unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-162">Because interactions differ, visual/audio affordances and object behavior might differ between interaction models.</span></span>  
* <span data-ttu-id="3d4eb-163">Die Kombination von Komponenten verschiedener Interaktionsmodelle birgt das Risiko konkurrierender Angebote, z. B. simultane Handstrahlen und ein Cursor zum Anvisieren mit dem Kopf.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-163">Combining parts of multiple interaction models creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor.</span></span> <span data-ttu-id="3d4eb-164">Dies kann Benutzer überfordern und verwirren.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-164">This can overwhelm and confuse users.</span></span>

<span data-ttu-id="3d4eb-165">Hier folgen einige Beispiele dazu, wie Angebote und Verhaltensweisen für die einzelnen Interaktionsmodelle optimiert werden.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-165">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span> <span data-ttu-id="3d4eb-166">Neue Benutzer haben häufig ähnliche Fragen, z. B. _„Woher weiß ich, dass das System funktioniert?“_ , _„Woher weiß ich, über welche Möglichkeiten ich verfüge?“_ und _„Woher weiß ich, ob es verstanden hat, was ich gerade getan habe?“_ .</span><span class="sxs-lookup"><span data-stu-id="3d4eb-166">We often see new users have similar questions, such as _"how do I know the system is working"_, _"how do I know what I can do"_, and _"how do I know if it understood what I just did?"_</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="3d4eb-167"><strong>Modell</strong></span><span class="sxs-lookup"><span data-stu-id="3d4eb-167"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="3d4eb-168"><strong>Woher weiß ich, dass es funktioniert?</strong></span><span class="sxs-lookup"><span data-stu-id="3d4eb-168"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="3d4eb-169"><strong>Woher weiß ich, über welche Möglichkeiten ich verfüge?</strong></span><span class="sxs-lookup"><span data-stu-id="3d4eb-169"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="3d4eb-170"><strong>Woher weiß ich, was ich gerade getan habe?</strong></span><span class="sxs-lookup"><span data-stu-id="3d4eb-170"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3d4eb-171"><a href="hands-and-tools.md">Hände und Motion-Controller</a></span><span class="sxs-lookup"><span data-stu-id="3d4eb-171"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="3d4eb-172">Ich sehe ein Handgittermodell, ein Fingerspitzenangebot oder Hand-/Controllerstrahlen.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-172">I see a hand mesh, a fingertip affordance, or hand/controller rays.</span></span></td>
        <td><span data-ttu-id="3d4eb-173">Es werden greifbare Ziehpunkte oder ein Begrenzungsrahmen angezeigt, wenn die Hand sich in der Nähe des Objekts befindet.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-173">I see grabbable handles, or a bounding box appears when my hand is near an object.</span></span></td>
        <td><span data-ttu-id="3d4eb-174">Ich höre Töne und sehe Animationen beim Greifen und Loslassen.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-174">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3d4eb-175"><a href="gaze-and-commit.md">Anvisieren mit dem Kopf und Ausführen</a></span><span class="sxs-lookup"><span data-stu-id="3d4eb-175"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="3d4eb-176">Ich sehe einen Cursor in der Mitte meines Sichtfelds.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-176">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="3d4eb-177">Der Cursor wechselt den Zustand, wenn er sich über bestimmten Objekten befindet.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-177">The cursor changes state when it's over certain objects.</span></span></td>
        <td><span data-ttu-id="3d4eb-178">Ich sehe/höre beim Agieren visuelle und akustische Bestätigungen.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-178">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="3d4eb-179"><a href="hands-free.md">Freihändig (Anvisieren mit dem Kopf und Verweilen)</a></span><span class="sxs-lookup"><span data-stu-id="3d4eb-179"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="3d4eb-180">Ich sehe einen Cursor in der Mitte meines Sichtfelds.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-180">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="3d4eb-181">Ich sehe eine Statusanzeige, wenn ich über einem interaktionsfähigen Objekt verweile.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-181">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="3d4eb-182">Ich sehe/höre beim Agieren visuelle und akustische Bestätigungen.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-182">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="3d4eb-183"><a href="hands-free.md">Freihändig (Sprachbefehle)</a></span><span class="sxs-lookup"><span data-stu-id="3d4eb-183"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="3d4eb-184">Ich sehe eine Anzeige zur Spracherkennung und Untertitel, die zeigen, was das System gehört hat.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-184">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="3d4eb-185">Ich erhalte Sprachansagen und Hinweise.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-185">I get voice prompts and hints.</span></span> <span data-ttu-id="3d4eb-186">Wenn ich Folgendes sage: Was kann ich sagen?</span><span class="sxs-lookup"><span data-stu-id="3d4eb-186">When I say: "What can I say?"</span></span> <span data-ttu-id="3d4eb-187">Ich sehe ein Feedback.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-187">I see feedback.</span></span></td>
        <td><span data-ttu-id="3d4eb-188">Ich sehe/höre visuelle und akustische Bestätigungen, wenn ich einen Befehl erteile, oder erhalte bei Bedarf die Benutzerumgebung zur Mehrdeutigkeitsvermeidung.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-188">I see/hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="3d4eb-189">Nachfolgend sind Fragen aufgeführt, die Teams (gemäß unserer Erfahrung) bei der Auswahl eines Interaktionsmodells geholfen haben:</span><span class="sxs-lookup"><span data-stu-id="3d4eb-189">Below are questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="3d4eb-190">Q:  Möchten meine Benutzer Hologramme berühren und präzise holografische Eingriffe durchführen?</span><span class="sxs-lookup"><span data-stu-id="3d4eb-190">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="3d4eb-191">A:  In diesem Fall sollten Sie das Interaktionsmodell für Hände und Motion-Controller für die Präzisionszielbestimmung und für Eingriffe ausprobieren.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-191">A:  If so, check out the Hands and motion controllers interaction model for precision targeting and manipulation.</span></span>
 
2.  <span data-ttu-id="3d4eb-192">Q:  Müssen meine Benutzer für reale Aufgaben die Hände frei haben?</span><span class="sxs-lookup"><span data-stu-id="3d4eb-192">Q:  Do my users need to keep their hands free for real-world tasks?</span></span><br><br>
<span data-ttu-id="3d4eb-193">A:  In diesem Fall sollten Sie sich das Interaktionsmodell „Freihändig“ ansehen, das durch blick- und sprachbasierte Interaktionen eine großartige freihändige Umgebung bietet.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-193">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="3d4eb-194">Q:  Haben meine Benutzer Zeit, Interaktionen für meine MR-Anwendung zu erlernen, oder sind Interaktionen mit einer möglichst geringen Lernkurve erforderlich?</span><span class="sxs-lookup"><span data-stu-id="3d4eb-194">Q:  Do my users have time to learn interactions for my MR application or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="3d4eb-195">A:  Wir empfehlen das Modell für Hände und Motion-Controller für die niedrigste Lernkurve und intuitivste Interaktion, sofern die Benutzer ihre Hände zur Interaktion nutzen können.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-195">A:  For the lowest learning curve and most intuitive interactions, we recommend the Hands and motion controllers model, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="3d4eb-196">Q:  Verwenden meine Benutzer Motion-Controller zum Zeigen und Bearbeiten?</span><span class="sxs-lookup"><span data-stu-id="3d4eb-196">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="3d4eb-197">A:  Das Modell für Hände und Motion-Controller enthält alle Anleitungen für ein großartiges Erlebnis mit den Motion-Controllern.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-197">A:  The Hands and motion controllers model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="3d4eb-198">Q:  Verwenden meine Benutzer einen Controller für Barrierefreiheit oder einen herkömmlichen Bluetooth-Controller, z. B. ein Klick-Gerät?</span><span class="sxs-lookup"><span data-stu-id="3d4eb-198">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="3d4eb-199">A:  Wir empfehlen das Modell „Anvisieren mit dem Kopf und Ausführen“ für alle nicht nachverfolgten Controller.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-199">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span> <span data-ttu-id="3d4eb-200">Es wurde für Benutzer entwickelt, um ein ganzheitliches Erlebnis mit einem einfachen Mechanismus für „Anvisieren und Ausführen“ zu durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-200">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanism.</span></span> 
 
6.  <span data-ttu-id="3d4eb-201">Q: Können meine Benutzer in einer Umgebung nur durch „Durchklicken“ voranschreiten (z. B. wie bei einer 3D-Diashow), anstatt durch kompakte Layouts von Steuerelementen der Benutzeroberfläche zu navigieren?</span><span class="sxs-lookup"><span data-stu-id="3d4eb-201">Q: Do my users only progress through an experience by "clicking through" (for example in a 3D slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="3d4eb-202">A:  Wenn Benutzer nicht viele Komponenten einer Benutzeroberfläche steuern müssen, bietet „Anvisieren mit dem Kopf und Ausführen“ eine erlernbare Option, bei der sich Benutzer nicht um die Zielbestimmung kümmern müssen.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-202">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="3d4eb-203">Q:  Verwenden meine Benutzer sowohl HoloLens (1. Generation) als auch HoloLens 2/Immersive Windows Mixed Reality-Headsets (VR)?</span><span class="sxs-lookup"><span data-stu-id="3d4eb-203">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/Windows Mixed Reality immersive headsets (VR)?</span></span><br><br>
<span data-ttu-id="3d4eb-204">A:  Da „Anvisieren mit dem Kopf und Ausführen“ das Interaktionsmodell für HoloLens (1. Generation) ist, empfehlen wir Entwicklern, die HoloLens (1. Generation) unterstützen, „Anvisieren mit dem Kopf und Ausführen“ nur alle Features oder Modi zu verwenden, die Benutzer auf einem HoloLens-Headset (1. Generation) erleben können.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-204">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users will experience on a HoloLens (1st gen) headset.</span></span> <span data-ttu-id="3d4eb-205">Weitere Informationen zur Erstellung einer großartigen Umgebung für mehrere HoloLens-Generationen finden Sie nachfolgend unter *Wechseln zwischen Interaktionsmodellen*.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-205">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="3d4eb-206">Q: Wie sieht es mit generell mobilen Benutzern, die einen großen Raum einnehmen oder sich zwischen verschiedenen Räumen bewegen, gegenüber Benutzern aus, die dazu neigen, in einem einzelnen Raum zu arbeiten?</span><span class="sxs-lookup"><span data-stu-id="3d4eb-206">Q: What about users who are generally mobile, covering a large space or moving between spaces, versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="3d4eb-207">A:  Für diese Benutzer ist jedes der Interaktionsmodelle geeignet.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-207">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="3d4eb-208">Weitere Anleitungen zum App-Design sind [bald verfügbar](news.md).</span><span class="sxs-lookup"><span data-stu-id="3d4eb-208">More guidance specific to app design [coming soon](news.md).</span></span>


## <a name="transitioning-interaction-models"></a><span data-ttu-id="3d4eb-209">Wechseln zwischen Interaktionsmodellen</span><span class="sxs-lookup"><span data-stu-id="3d4eb-209">Transitioning interaction models</span></span>
<span data-ttu-id="3d4eb-210">Es kann auch vorkommen, dass Ihre Anwendungsfälle die Verwendung mehrerer Interaktionsmodelle erfordern.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-210">There are also use cases that might require utilizing more than one interaction model.</span></span> <span data-ttu-id="3d4eb-211">Beim „Erstellungsablauf“ Ihrer Anwendung wird z. B. das Interaktionsmodell _„Hände und Motion-Controller“_ verwendet, aber Sie möchten einen Freihandmodus für Außendiensttechniker verwenden.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-211">For example, your application's creation flow utilizes the _"hands and motion controllers"_ interaction model, but you want to employ a hands-free mode for field technicians.</span></span>
<span data-ttu-id="3d4eb-212">Wenn Ihre Umgebung mehrere Interaktionsmodelle erfordert, sollten Sie daran denken, dass viele Benutzer Schwierigkeiten beim Übergang von einem Modell zum anderen haben können – insbesondere Benutzer, die noch nicht mit Mixed Reality vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-212">If your experience does require multiple interaction models, please keep in mind that many users might encounter difficulty when transitioning from one model to another, especially users who are new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="3d4eb-213">Wir arbeiten ständig an weiteren Anleitungen, die Entwicklern und Designern zur Verfügung stehen werden und sie über das Wie, Wann und Warum für den Einsatz mehrerer MR-Interaktionsmodelle informieren sollen.</span><span class="sxs-lookup"><span data-stu-id="3d4eb-213">We're constantly working on more guidance that will be available to developers and designers, informing them about the how, when, and why for using multiple MR interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="3d4eb-214">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3d4eb-214">See also</span></span>
* [<span data-ttu-id="3d4eb-215">Komfort</span><span class="sxs-lookup"><span data-stu-id="3d4eb-215">Comfort</span></span>](comfort.md)
* [<span data-ttu-id="3d4eb-216">Augenbasierte Interaktion</span><span class="sxs-lookup"><span data-stu-id="3d4eb-216">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="3d4eb-217">Blickverfolgung auf HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3d4eb-217">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="3d4eb-218">Anvisieren und Ausführen</span><span class="sxs-lookup"><span data-stu-id="3d4eb-218">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="3d4eb-219">Anvisieren und Verweilen</span><span class="sxs-lookup"><span data-stu-id="3d4eb-219">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="3d4eb-220">Hände – Direkte Manipulation</span><span class="sxs-lookup"><span data-stu-id="3d4eb-220">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="3d4eb-221">Hände – Gesten</span><span class="sxs-lookup"><span data-stu-id="3d4eb-221">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="3d4eb-222">Hände – Zeigen und Ausführen</span><span class="sxs-lookup"><span data-stu-id="3d4eb-222">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="3d4eb-223">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="3d4eb-223">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="3d4eb-224">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="3d4eb-224">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="3d4eb-225">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="3d4eb-225">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="3d4eb-226">Raumklangentwurf</span><span class="sxs-lookup"><span data-stu-id="3d4eb-226">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="3d4eb-227">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="3d4eb-227">Voice input</span></span>](voice-input.md)


