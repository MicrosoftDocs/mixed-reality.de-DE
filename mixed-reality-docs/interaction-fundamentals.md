---
title: Kombinierte Interaktionen – Übersicht
description: Übersicht über die kombinierten Interaktionen
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Anvisieren, Zielbestimmung, Interaktion, Entwurf, Hololens, MMR, kombiniert
ms.openlocfilehash: 3ba1a2fc46aa88c856e4cc9531382c479b3fb17a
ms.sourcegitcommit: 76a7aa6e64e114b63ace058dd6d6d662b3c9f09e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/26/2019
ms.locfileid: "68507898"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="57086-104">Einführung in instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="57086-104">Introducing instinctual interactions</span></span>

<span data-ttu-id="57086-105">Die Philosophie der einfachen, instinktiven Interaktionen ist in der gesamten Mixed Reality-Plattform verwurzelt.</span><span class="sxs-lookup"><span data-stu-id="57086-105">The philosophy of simple, instinctual interactions is interwoven throughout the Mixed Reality platform.</span></span>  <span data-ttu-id="57086-106">Wir haben drei Schritte unternommen, um sicherzustellen, dass Anwendungsdesigner und -entwickler ihren Kunden einfache und intuitive Interaktionen bereitstellen können.</span><span class="sxs-lookup"><span data-stu-id="57086-106">We've taken three steps to ensure that application designers and developers can provide their customers with easy and intuitive interactions.</span></span> 

<span data-ttu-id="57086-107">Zunächst haben wir sichergestellt, dass sich unsere Sensoren und Eingabetechnologien (die Hand- und Eyetracking sowie natürliche Spracheingabe umfassen) zu nahtlos kombinierten Interaktionsmodellen verbinden.</span><span class="sxs-lookup"><span data-stu-id="57086-107">First, we've made sure our sensors and input technologies (which includes hand and eye tracking along with natural language input) combine into seamless, multimodal interaction models.</span></span>  <span data-ttu-id="57086-108">Basierend auf unseren Studien ist das kombinierte Entwerfen und Entwickeln in einem multimodalen Framework – und nicht die Fokussierung auf einzelne Eingaben – der Schlüssel zur Realisierung instinktiver Erfahrungen.</span><span class="sxs-lookup"><span data-stu-id="57086-108">Based on our research, designing and developing within a multimodal framework, and not based on single inputs, is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="57086-109">Zweitens haben wir erkannt, dass viele Entwickler auf mehrere HoloLens-Geräte ausgerichtet sind, z. B. HoloLens 2 und HoloLens (1. Generation) oder HoloLens und VR.</span><span class="sxs-lookup"><span data-stu-id="57086-109">Second, we recognize that many developers target multiple HoloLens devices, such as HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  <span data-ttu-id="57086-110">Deshalb haben wir unsere Interaktionsmodelle so konzipiert, dass sie geräteübergreifend funktionieren, auch wenn die Eingabetechnologie von Gerät zu Gerät variiert.</span><span class="sxs-lookup"><span data-stu-id="57086-110">So we've designed our interaction models to work across devices, even if the input technology varies on each device.</span></span>  <span data-ttu-id="57086-111">So verwenden z. B. die ferne Interaktion bei einem Windows Immersive Headset mit einem 6DoF-Controller und die ferne Interaktion bei HoloLens 2 jeweils dieselben Angebote und Muster, wodurch es sich für die Entwicklung geräteübergreifender Anwendungen, die den Interaktionen der Endbenutzer ein natürliches Gefühl verleiht, einfach gestaltet.</span><span class="sxs-lookup"><span data-stu-id="57086-111">For example, far interaction on a Windows Immersive headset with a 6DoF controller and far interaction on a HoloLens 2 both use  identical affordances and patterns, making it easy for cross-device application development that provides a natural feel to end-user interactions.</span></span> 

<span data-ttu-id="57086-112">Zwar haben wir erkannt, dass Mixed Reality (MR) Tausende von effektiven, ansprechenden und einzigartigen Interaktionen bietet, aber wir haben festgestellt, dass der bewusste Einsatz eines einzelnen umfassenden Interaktionsmodells in einer Anwendung der beste Weg ist, um sicherzustellen, dass Benutzer erfolgreich sind und ein großartiges Erlebnis haben.</span><span class="sxs-lookup"><span data-stu-id="57086-112">While we recognize that there are thousands of effective, engaging, and magical interactions possible in mixed reality (MR), we've found that intentionally employing a single interaction model, end-to-end, in an application is the best way to ensure users are successful and have a great experience.</span></span> <span data-ttu-id="57086-113">Zu diesem Zweck haben wir drei Punkte in diese Interaktionsanleitung einbezogen:</span><span class="sxs-lookup"><span data-stu-id="57086-113">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="57086-114">Diese Anleitung ist um die drei primären Interaktionsmodelle und die für jedes einzelne Modell erforderlichen Komponenten und Muster herum strukturiert.</span><span class="sxs-lookup"><span data-stu-id="57086-114">This guidance is structured around the three primary interaction models and the components and patterns required for each.</span></span>
* <span data-ttu-id="57086-115">Es wurden zusätzliche Anleitungen zu weiteren Vorteilen einbezogen, die unsere Plattform bietet.</span><span class="sxs-lookup"><span data-stu-id="57086-115">Supplemental guidance has been included about other benefits that our platform provides.</span></span>
* <span data-ttu-id="57086-116">Es wurden außerdem Anleitungen zur Auswahl des geeigneten Interaktionsmodells für Ihr Entwicklungsszenario einbezogen.</span><span class="sxs-lookup"><span data-stu-id="57086-116">Guidance has also been included to help select the appropriate interaction model for your development scenario.</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="57086-117">Kombinierte Interaktionsmodelle</span><span class="sxs-lookup"><span data-stu-id="57086-117">Multimodal interaction models</span></span>

<span data-ttu-id="57086-118">Basierend auf unseren bisherigen Studien sowie dem Feedback von Kunden haben wir festgestellt, dass drei primäre Interaktionsmodelle für die meisten Mixed Reality-Umgebungen geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="57086-118">Based on our research as well as feedback from customers, we've discovered that three primary interaction models suit the majority of mixed reality experiences.</span></span>

<span data-ttu-id="57086-119">In vielerlei Hinsicht ist das Interaktionsmodell das mentale Modell des Benutzers zur Durchführung seiner Abläufe.</span><span class="sxs-lookup"><span data-stu-id="57086-119">In many ways, the interaction model is the user's mental model for completing their flows.</span></span> <span data-ttu-id="57086-120">Jedes dieser Interaktionsmodelle ist für verschiedene Kundenanforderungen optimiert.</span><span class="sxs-lookup"><span data-stu-id="57086-120">Each of these interaction models is optimized for a set of customer needs.</span></span> <span data-ttu-id="57086-121">Jede ist praktisch, leistungsstark und kann eigenständig verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="57086-121">Each is convenient, powerful, and usable in its own right.</span></span> 

<span data-ttu-id="57086-122">Das folgende Diagramm stellt eine vereinfachte Übersicht dar.</span><span class="sxs-lookup"><span data-stu-id="57086-122">The chart below is a simplified overview.</span></span> <span data-ttu-id="57086-123">Ausführliche Informationen zur Verwendung der einzelnen Interaktionsmodelle sind auf den folgenden Seiten mit Bildern und Codebeispielen verknüpft.</span><span class="sxs-lookup"><span data-stu-id="57086-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="57086-124"><strong>Modell</strong></span><span class="sxs-lookup"><span data-stu-id="57086-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="57086-125"><strong>Beispielszenarien</strong></span><span class="sxs-lookup"><span data-stu-id="57086-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="57086-126"><strong>Eignung</strong></span><span class="sxs-lookup"><span data-stu-id="57086-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="57086-127"><strong>Hardware</strong></span><span class="sxs-lookup"><span data-stu-id="57086-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="57086-128"><a href="hands-and-tools.md">Hände und Motion-Controller</a></span><span class="sxs-lookup"><span data-stu-id="57086-128"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="57086-129">3D-Raumerlebnisse, z. B. räumliches Layout und räumlicher Entwurf, Inhaltsmanipulation oder Simulation.</span><span class="sxs-lookup"><span data-stu-id="57086-129">3D spatial experiences, such as spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="57086-130">Ideal für neue Benutzer, kombiniert mit Stimme, Eyetracking oder Anvisieren mit dem Kopf.</span><span class="sxs-lookup"><span data-stu-id="57086-130">Great for new users coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="57086-131">Niedrige Lernkurve.</span><span class="sxs-lookup"><span data-stu-id="57086-131">Low learning curve.</span></span> <span data-ttu-id="57086-132">Konsistente Benutzererfahrung für Handtracking und Controller mit 6 Freiheitsgraden.</span><span class="sxs-lookup"><span data-stu-id="57086-132">Consistent UX across hand tracking and 6DoF controllers.</span></span></td>
        <td><span data-ttu-id="57086-133">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="57086-133">HoloLens 2</span></span><br><span data-ttu-id="57086-134">Immersive Headsets</span><span class="sxs-lookup"><span data-stu-id="57086-134">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="57086-135"><a href="hands-free.md">Freihändig</a></span><span class="sxs-lookup"><span data-stu-id="57086-135"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="57086-136">Kontextbezogene Erfahrungen, bei denen die Hände eines Benutzers beschäftigt sind, z. B. praxisnahes Lernen und Wartung.</span><span class="sxs-lookup"><span data-stu-id="57086-136">Contextual experiences where a user's hands are occupied, such as on-the-job learning, and maintenance.</span></span></td>
        <td><span data-ttu-id="57086-137">Gewisser Lernaufwand erforderlich.</span><span class="sxs-lookup"><span data-stu-id="57086-137">Some learning required.</span></span> <span data-ttu-id="57086-138">Das Gerät ist gut für Stimme und natürliche Sprache geeignet, wenn die Hände nicht verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="57086-138">If hands are unavailable, the device pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="57086-139">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="57086-139">HoloLens 2</span></span><br><span data-ttu-id="57086-140">HoloLens (1. Generation)</span><span class="sxs-lookup"><span data-stu-id="57086-140">HoloLens (1st gen)</span></span><br><span data-ttu-id="57086-141">Immersive Headsets</span><span class="sxs-lookup"><span data-stu-id="57086-141">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="57086-142"><a href="gaze-and-commit.md">Anvisieren mit dem Kopf und Ausführen</a></span><span class="sxs-lookup"><span data-stu-id="57086-142"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="57086-143">Click-Through-Erfahrungen, z. B. 3D-Präsentationen, Demos.</span><span class="sxs-lookup"><span data-stu-id="57086-143">Click-through experiences, e.g. 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="57086-144">Erfordert Training für HMDs, aber nicht für mobile Geräte.</span><span class="sxs-lookup"><span data-stu-id="57086-144">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="57086-145">Ideal für verfügbare Controller.</span><span class="sxs-lookup"><span data-stu-id="57086-145">Best for accessible controllers.</span></span> <span data-ttu-id="57086-146">Ideal für HoloLens (1. Generation).</span><span class="sxs-lookup"><span data-stu-id="57086-146">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="57086-147">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="57086-147">HoloLens 2</span></span><br><span data-ttu-id="57086-148">HoloLens (1. Generation)</span><span class="sxs-lookup"><span data-stu-id="57086-148">HoloLens (1st gen)</span></span><br><span data-ttu-id="57086-149">Immersive Headsets</span><span class="sxs-lookup"><span data-stu-id="57086-149">Immersive headsets</span></span><br><span data-ttu-id="57086-150">Mobile AR</span><span class="sxs-lookup"><span data-stu-id="57086-150">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="57086-151">Die beste Möglichkeit, um sicherzustellen, dass es keine Lücken oder Unterbrechungen bei der Interaktion für Ihr Erlebnis gibt, besteht darin, der Anleitung für ein einzelnes Modell von Anfang bis Ende zu folgen.</span><span class="sxs-lookup"><span data-stu-id="57086-151">To ensure that there are no gaps or holes in the user interaction experience, it is best to follow the guidance for a single model from beginning to end.</span></span> 

<span data-ttu-id="57086-152">Um den Entwurf und die Entwicklung zu beschleunigen, haben wir ausführliche Informationen und Links zu Bildern und Codebeispielen in unsere Beschreibung der einzelnen Modelle aufgenommen.</span><span class="sxs-lookup"><span data-stu-id="57086-152">To speed up design and development, we've included detailed information and links to images and code samples within our coverage of each model.</span></span>

<span data-ttu-id="57086-153">Die folgenden Abschnitte führen durch die Schritte zur Auswahl und Implementierung eines dieser Interaktionsmodelle.</span><span class="sxs-lookup"><span data-stu-id="57086-153">The sections below walk through the steps for selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="57086-154">Am Ende dieser Seite werden Sie unsere Anleitung zu Folgendem verstehen:</span><span class="sxs-lookup"><span data-stu-id="57086-154">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="57086-155">Auswählen eines Interaktionsmodells für Ihren Kunden</span><span class="sxs-lookup"><span data-stu-id="57086-155">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="57086-156">Verwenden der Anleitung zum Interaktionsmodell</span><span class="sxs-lookup"><span data-stu-id="57086-156">Using the interaction model guidance</span></span>
* <span data-ttu-id="57086-157">Wechseln zwischen Interaktionsmodellen</span><span class="sxs-lookup"><span data-stu-id="57086-157">Transitioning between interaction models</span></span>
* <span data-ttu-id="57086-158">Entwerfen der nächsten Schritte</span><span class="sxs-lookup"><span data-stu-id="57086-158">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="57086-159">Auswählen eines Interaktionsmodells für Ihren Kunden</span><span class="sxs-lookup"><span data-stu-id="57086-159">Choose an interaction model for your customer</span></span>


<span data-ttu-id="57086-160">In der Regel haben Entwickler und Ersteller die Arten von Interaktionen, die Ihre Kunden ausführen können, bereits durchdacht.</span><span class="sxs-lookup"><span data-stu-id="57086-160">Typically, developers and creators have thought through the types of interactions that their customers can have.</span></span> <span data-ttu-id="57086-161">Um einen kundenorientierten Ansatz für den Entwurf zu fördern, empfehlen wir Ihnen die folgende Anleitung zur Auswahl des für Ihren Kunden optimierten Interaktionsmodells.</span><span class="sxs-lookup"><span data-stu-id="57086-161">To encourage a customer-focused approach to design, we recommend the following guidance for selecting the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="57086-162">Gründe zum Befolgen dieser Anleitung</span><span class="sxs-lookup"><span data-stu-id="57086-162">Why follow this guidance?</span></span>

* <span data-ttu-id="57086-163">Unsere Interaktionsmodelle werden auf objektive und subjektive Kriterien wie physische und kognitive Leistung, Intuitivität und Erlernbarkeit getestet.</span><span class="sxs-lookup"><span data-stu-id="57086-163">Our interaction models are tested for objective and subjective criteria, such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="57086-164">Da die Interaktion unterschiedlich verläuft, können sich auch die visuellen und akustischen Angebote sowie das Objektverhalten zwischen Interaktionsmodellen unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="57086-164">Because interactions differ, visual and audio affordances and object behavior might differ between interaction models.</span></span>  
* <span data-ttu-id="57086-165">Die Kombination von Komponenten verschiedener Interaktionsmodelle birgt das Risiko konkurrierender Angebote, z. B. simultane Handstrahlen und ein Cursor zum Anvisieren mit dem Kopf, die den Benutzer überfordern und verwirren können.</span><span class="sxs-lookup"><span data-stu-id="57086-165">Combining parts of multiple interaction models creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor that can overwhelm and confuse users.</span></span>

<span data-ttu-id="57086-166">Hier folgen einige Beispiele dazu, wie Angebote und Verhaltensweisen für die einzelnen Interaktionsmodelle optimiert werden.</span><span class="sxs-lookup"><span data-stu-id="57086-166">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="57086-167">Neue Benutzer haben häufig ähnliche Fragen, z. B. „Woher weiß ich, dass das System funktioniert?“, „Woher weiß ich, über welche Möglichkeiten ich verfüge?“ und „Woher weiß ich, ob es verstanden hat, was ich gerade getan habe?“.</span><span class="sxs-lookup"><span data-stu-id="57086-167">We often see new users have similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="57086-168"><strong>Modell</strong></span><span class="sxs-lookup"><span data-stu-id="57086-168"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="57086-169"><strong>Woher weiß ich, dass es funktioniert?</strong></span><span class="sxs-lookup"><span data-stu-id="57086-169"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="57086-170"><strong>Woher weiß ich, über welche Möglichkeiten ich verfüge?</strong></span><span class="sxs-lookup"><span data-stu-id="57086-170"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="57086-171"><strong>Woher weiß ich, was ich gerade getan habe?</strong></span><span class="sxs-lookup"><span data-stu-id="57086-171"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="57086-172"><a href="hands-and-tools.md">Hände und Motion-Controller</a></span><span class="sxs-lookup"><span data-stu-id="57086-172"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="57086-173">Ich sehe ein Handgittermodell, ich sehe ein Fingerspitzenangebot oder Hand-/Controllerstrahlen.</span><span class="sxs-lookup"><span data-stu-id="57086-173">I see a hand mesh, I see a fingertip affordance or hand/controller rays.</span></span></td>
        <td><span data-ttu-id="57086-174">Es werden greifbare Ziehpunkte oder ein Begrenzungsrahmen angezeigt, wenn die Hand sich in der Nähe des Objekts befindet.</span><span class="sxs-lookup"><span data-stu-id="57086-174">I see grabbable handles or a bounding box appears when my hand is near an object.</span></span></td>
        <td><span data-ttu-id="57086-175">Ich höre Töne und sehe Animationen beim Greifen und Loslassen.</span><span class="sxs-lookup"><span data-stu-id="57086-175">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="57086-176"><a href="gaze-and-commit.md">Anvisieren mit dem Kopf und Ausführen</a></span><span class="sxs-lookup"><span data-stu-id="57086-176"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="57086-177">Ich sehe einen Cursor in der Mitte meines Sichtfelds.</span><span class="sxs-lookup"><span data-stu-id="57086-177">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="57086-178">Der Cursor zum Anvisieren mit dem Kopf wechselt den Zustand, wenn er sich über bestimmten Objekten befindet.</span><span class="sxs-lookup"><span data-stu-id="57086-178">The head-gaze cursor changes state when it's over certain objects.</span></span></td>
        <td><span data-ttu-id="57086-179">Ich sehe/höre beim Agieren visuelle und akustische Bestätigungen.</span><span class="sxs-lookup"><span data-stu-id="57086-179">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="57086-180"><a href="hands-free.md">Freihändig (Anvisieren mit dem Kopf und Verweilen)</a></span><span class="sxs-lookup"><span data-stu-id="57086-180"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="57086-181">Ich sehe einen Cursor in der Mitte meines Sichtfelds.</span><span class="sxs-lookup"><span data-stu-id="57086-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="57086-182">Ich sehe eine Statusanzeige, wenn ich über einem interaktionsfähigen Objekt verweile.</span><span class="sxs-lookup"><span data-stu-id="57086-182">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="57086-183">Ich sehe/höre beim Agieren visuelle und akustische Bestätigungen.</span><span class="sxs-lookup"><span data-stu-id="57086-183">I see/hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="57086-184"><a href="hands-free.md">Freihändig (Sprachbefehle)</a></span><span class="sxs-lookup"><span data-stu-id="57086-184"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="57086-185">Ich sehe eine Anzeige zur Spracherkennung und Untertitel, die zeigen, was das System gehört hat.</span><span class="sxs-lookup"><span data-stu-id="57086-185">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="57086-186">Ich erhalte Sprachansagen und Hinweise.</span><span class="sxs-lookup"><span data-stu-id="57086-186">I get voice prompts and hints.</span></span> <span data-ttu-id="57086-187">Wenn ich Folgendes sage: Was kann ich sagen?</span><span class="sxs-lookup"><span data-stu-id="57086-187">When I say: "What can I say?"</span></span> <span data-ttu-id="57086-188">Ich sehe ein Feedback.</span><span class="sxs-lookup"><span data-stu-id="57086-188">I see feedback.</span></span></td>
        <td><span data-ttu-id="57086-189">Ich sehe/höre visuelle und akustische Bestätigungen, wenn ich einen Befehl erteile, oder erhalte bei Bedarf die Benutzerumgebung zur Mehrdeutigkeitsvermeidung.</span><span class="sxs-lookup"><span data-stu-id="57086-189">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="57086-190">Nachfolgend sind die Fragen aufgeführt, die Teams (gemäß unserer Erfahrung) bei der Auswahl eines Interaktionsmodells geholfen haben:</span><span class="sxs-lookup"><span data-stu-id="57086-190">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="57086-191">Q:  Möchten meine Benutzer Hologramme berühren und präzise holografische Eingriffe durchführen?</span><span class="sxs-lookup"><span data-stu-id="57086-191">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="57086-192">A:  In diesem Fall sollten Sie das Interaktionsmodell für Hände und Motion-Controller für die Präzisionszielbestimmung und für Eingriffe mit Händen oder Motion-Controllern ausprobieren.</span><span class="sxs-lookup"><span data-stu-id="57086-192">A:  If so, check out the Hands and motion controllers interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="57086-193">Q:  Müssen meine Benutzer für reale Aufgaben die Hände frei haben?</span><span class="sxs-lookup"><span data-stu-id="57086-193">Q:  Do my users need to keep their hands free for real-world tasks?</span></span><br><br>
<span data-ttu-id="57086-194">A:  In diesem Fall sollten Sie sich das Interaktionsmodell „Freihändig“ ansehen, das durch blick- und sprachbasierte Interaktionen eine großartige freihändige Umgebung bietet.</span><span class="sxs-lookup"><span data-stu-id="57086-194">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="57086-195">Q:  Haben meine Benutzer Zeit, Interaktionen für meine MR-Anwendung zu erlernen, oder sind Interaktionen mit einer möglichst geringen Lernkurve erforderlich?</span><span class="sxs-lookup"><span data-stu-id="57086-195">Q:  Do my users have time to learn interactions for my MR application or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="57086-196">A:  Wir empfehlen das Modell für Hände und Motion-Controller für die niedrigste Lernkurve und intuitivste Interaktion, sofern die Benutzer ihre Hände zur Interaktion nutzen können.</span><span class="sxs-lookup"><span data-stu-id="57086-196">A:  We recommend the Hands and motion controllers model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="57086-197">Q:  Verwenden meine Benutzer Motion-Controller zum Zeigen und Bearbeiten?</span><span class="sxs-lookup"><span data-stu-id="57086-197">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="57086-198">A:  Das Modell für Hände und Motion-Controller enthält alle Anleitungen für ein großartiges Erlebnis mit den Motion-Controllern.</span><span class="sxs-lookup"><span data-stu-id="57086-198">A:  The Hands and motion controllers model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="57086-199">Q:  Verwenden meine Benutzer einen Controller für Barrierefreiheit oder einen herkömmlichen Bluetooth-Controller, z. B. ein Klick-Gerät?</span><span class="sxs-lookup"><span data-stu-id="57086-199">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="57086-200">A:  Wir empfehlen das Modell „Anvisieren mit dem Kopf und Ausführen“ für alle nicht nachverfolgten Controller.</span><span class="sxs-lookup"><span data-stu-id="57086-200">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span> <span data-ttu-id="57086-201">Es wurde für Benutzer entwickelt, um ein ganzheitliches Erlebnis mit einem einfachen Mechanismus für „Anvisieren und Ausführen“ zu durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="57086-201">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanism.</span></span> 
 
6.  <span data-ttu-id="57086-202">Q: Können meine Benutzer in einer Umgebung nur durch „Durchklicken“ voranschreiten (z. B. wie bei einer 3D-Diashow), anstatt durch kompakte Layouts von Steuerelementen der Benutzeroberfläche zu navigieren?</span><span class="sxs-lookup"><span data-stu-id="57086-202">Q: Do my users only progress through an experience by "clicking through" (for example in a 3D slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="57086-203">A:  Wenn Benutzer nicht viele Komponenten einer Benutzeroberfläche steuern müssen, bietet „Anvisieren mit dem Kopf und Ausführen“ eine erlernbare Option, bei der sich Benutzer nicht um die Zielbestimmung kümmern müssen.</span><span class="sxs-lookup"><span data-stu-id="57086-203">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="57086-204">Q:  Verwenden meine Benutzer sowohl HoloLens (1. Generation) als auch HoloLens 2/Immersive Windows Mixed Reality-Headsets (VR)?</span><span class="sxs-lookup"><span data-stu-id="57086-204">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/Windows Mixed Reality immersive headsets (VR)?</span></span><br><br>
<span data-ttu-id="57086-205">A:  Da „Anvisieren mit dem Kopf und Ausführen“ das Interaktionsmodell für HoloLens (1. Generation) ist, empfehlen wir Entwicklern, die HoloLens (1. Generation) unterstützen, „Anvisieren mit dem Kopf und Ausführen“ nur alle Features oder Modi zu verwenden, die Benutzer auf einem HoloLens-Headset (1. Generation) erleben können.</span><span class="sxs-lookup"><span data-stu-id="57086-205">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users will experience on a HoloLens (1st gen) headset.</span></span> <span data-ttu-id="57086-206">Weitere Informationen zur Erstellung einer großartigen Umgebung für mehrere HoloLens-Generationen finden Sie nachfolgend unter *Wechseln zwischen Interaktionsmodellen*.</span><span class="sxs-lookup"><span data-stu-id="57086-206">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="57086-207">Q: Wie sieht es mit generell mobilen Benutzern, die einen großen Raum einnehmen oder sich zwischen verschiedenen Räumen bewegen, gegenüber Benutzern aus, die dazu neigen, in einem einzelnen Raum zu arbeiten?</span><span class="sxs-lookup"><span data-stu-id="57086-207">Q: What about users who are generally mobile, covering a large space or moving between spaces, versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="57086-208">A:  Für diese Benutzer ist jedes der Interaktionsmodelle geeignet.</span><span class="sxs-lookup"><span data-stu-id="57086-208">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="57086-209">Weitere Anleitungen zum App-Design sind [bald verfügbar](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="57086-209">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transitioning-interaction-models"></a><span data-ttu-id="57086-210">Wechseln zwischen Interaktionsmodellen</span><span class="sxs-lookup"><span data-stu-id="57086-210">Transitioning interaction models</span></span>
<span data-ttu-id="57086-211">Es kann auch vorkommen, dass Ihre Anwendungsfälle die Verwendung mehrerer Interaktionsmodelle erfordern.</span><span class="sxs-lookup"><span data-stu-id="57086-211">There are also use cases that might require utilizing more than one interaction model.</span></span> <span data-ttu-id="57086-212">Beim „Erstellungsablauf“ Ihrer Anwendung wird z. B. das Interaktionsmodell „Hände und Motion-Controller“ verwendet, aber Sie möchten einen Freihandmodus für Außendiensttechniker verwenden.</span><span class="sxs-lookup"><span data-stu-id="57086-212">For example, your application's creation flow utilizes the Hands and motion controllers interaction model, but you want to employ a hands-free mode for field technicians.</span></span>  

<span data-ttu-id="57086-213">Wenn Ihre Umgebung mehrere Interaktionsmodelle erfordert, sollten Sie daran denken, dass viele Endbenutzer Schwierigkeiten beim Übergang von einem Modell zum anderen haben können – insbesondere Benutzer, die noch nicht mit Mixed Reality vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="57086-213">If your experience does require multiple interaction models, keep in mind that many end users might encounter difficulty when transitioning from one model to another--especially for users who are new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="57086-214">Wir arbeiten ständig an weiteren Anleitungen, die Entwicklern und Designern zur Verfügung stehen werden und sie über das Wie, Wann und Warum für den Einsatz mehrerer MR-Interaktionsmodelle informieren sollen.</span><span class="sxs-lookup"><span data-stu-id="57086-214">We're constantly working on more guidance that will be available to developers and designers, informing them about the how, when, and why for using multiple MR interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="57086-215">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="57086-215">See also</span></span>
* [<span data-ttu-id="57086-216">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="57086-216">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="57086-217">Anvisieren mit dem Kopf und Verweilen</span><span class="sxs-lookup"><span data-stu-id="57086-217">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="57086-218">Direkte Manipulation mit den Händen</span><span class="sxs-lookup"><span data-stu-id="57086-218">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="57086-219">Zeigen und Ausführen mit den Händen</span><span class="sxs-lookup"><span data-stu-id="57086-219">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="57086-220">Gesten</span><span class="sxs-lookup"><span data-stu-id="57086-220">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="57086-221">Sprachbefehle</span><span class="sxs-lookup"><span data-stu-id="57086-221">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="57086-222">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="57086-222">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="57086-223">Raumklangentwurf</span><span class="sxs-lookup"><span data-stu-id="57086-223">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="57086-224">Gestaltung von räumlicher Abbildung</span><span class="sxs-lookup"><span data-stu-id="57086-224">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="57086-225">Komfort</span><span class="sxs-lookup"><span data-stu-id="57086-225">Comfort</span></span>](comfort.md)

