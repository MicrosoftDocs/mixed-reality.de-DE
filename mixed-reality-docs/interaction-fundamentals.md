---
title: Kombinierte Interaktionen – Übersicht
description: Übersicht über die kombinierten Interaktionen
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Anvisieren, Zielbestimmung, Interaktion, Entwurf, Hololens, MMR, kombiniert
ms.openlocfilehash: bea205edf484a55db701e8e0d1a233234882a272
ms.sourcegitcommit: 9b6949d7cd2e67e6bde9b32aebeaeea325baa6c4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2019
ms.locfileid: "66516023"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="f2500-104">Einführung in instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="f2500-104">Introducing instinctual interactions</span></span>

<span data-ttu-id="f2500-105">Die Philosophie der einfachen, instinktiven Interaktionen ist in der gesamten Microsoft Mixed Reality-Plattform verwurzelt.</span><span class="sxs-lookup"><span data-stu-id="f2500-105">The philosophy of simple, instinctual interactions is woven throughout the Microsoft Mixed Reality platform.</span></span>  <span data-ttu-id="f2500-106">Wir haben drei Schritte unternommen, um sicherzustellen, dass Anwendungsdesigner und -entwickler ihren Kunden einfache und intuitive Interaktionen bereitstellen können.</span><span class="sxs-lookup"><span data-stu-id="f2500-106">We've taken three steps to ensure that application designers and developers can provide easy and intuitive interactions for their customers.</span></span> 

<span data-ttu-id="f2500-107">Zunächst haben wir sichergestellt, dass sich unsere beeindruckenden Sensoren und Eingabetechnologien, einschließlich Hand- und Eyetracking sowie natürlicher Sprache, zu nahtlos kombinierten Interaktionsmodellen verbinden.</span><span class="sxs-lookup"><span data-stu-id="f2500-107">First, we've made sure our amazing sensors and input technology, including hand tracking, eye tracking, and natural language, combine into seamless multimodal interaction models.</span></span>  <span data-ttu-id="f2500-108">Basierend auf unseren Studien ist das kombinierte Entwerfen und Entwickeln – und nicht die Fokussierung auf einzelne Eingaben – der Schlüssel zur Realisierung instinktiver Erfahrungen.</span><span class="sxs-lookup"><span data-stu-id="f2500-108">Based on our research, designing and developing multimodally -- and not based on single inputs -- is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="f2500-109">Zweitens haben wir erkannt, dass viele Entwickler auf mehrere Geräte ausgerichtet sind, sei es HoloLens 2 und HoloLens (1. Generation) oder HoloLens und VR.</span><span class="sxs-lookup"><span data-stu-id="f2500-109">Secondly, we recognize that many developers target multiple devices, whether that means HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  <span data-ttu-id="f2500-110">Deshalb haben wir unsere Interaktionsmodelle so konzipiert, dass sie geräteübergreifend funktionieren (auch wenn die Eingabetechnologie von Gerät zu Gerät variiert).</span><span class="sxs-lookup"><span data-stu-id="f2500-110">So we've designed our interaction models to work across devices (even if the input technology varies on each device).</span></span>  <span data-ttu-id="f2500-111">So verwenden z. B. die ferne Interaktion bei einem Windows Immersive Headset mit einem 6DOF-Controller und die ferne Interaktion bei HoloLens 2 jeweils dieselben Angebote und Muster, wodurch es sich für geräteübergreifende Anwendungen einfach gestaltet.</span><span class="sxs-lookup"><span data-stu-id="f2500-111">For example, far interaction on a Windows Immersive headset with a 6DOF controller and far interaction on a HoloLens 2 both use the identical affordances and patterns, making it easy for cross-device applications.</span></span> <span data-ttu-id="f2500-112">Dies ist nicht nur für Entwickler und Designer praktisch, sondern fühlt sich auch für den Endbenutzer natürlich an.</span><span class="sxs-lookup"><span data-stu-id="f2500-112">Not only is this convenient for developers and designers, but it feels natural to end users.</span></span> 

<span data-ttu-id="f2500-113">Zu guter Letzt haben wir zwar erkannt, dass Mixed Reality (MR) Tausende von effektiven, ansprechenden und einzigartigen Interaktionen bietet, aber wir haben festgestellt, dass der bewusste Einsatz eines einzelnen umfassenden Interaktionsmodells in einer Anwendung der beste Weg ist, um sicherzustellen, dass Benutzer erfolgreich sind und ein großartiges Erlebnis haben.</span><span class="sxs-lookup"><span data-stu-id="f2500-113">Lastly, while we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we have found that intentionally employing a single interaction model end to end in an application is the best way to ensure users are successful and have a great experience.</span></span>  <span data-ttu-id="f2500-114">Zu diesem Zweck haben wir drei Punkte in diese Interaktionsanleitung einbezogen:</span><span class="sxs-lookup"><span data-stu-id="f2500-114">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="f2500-115">Wir haben diese Anleitung um die drei primären Interaktionsmodelle und die für jedes einzelne Modell erforderlichen Komponenten und Muster herum strukturiert.</span><span class="sxs-lookup"><span data-stu-id="f2500-115">We've structured this guidance around the three primary interaction models and the components and patterns required for each</span></span>
* <span data-ttu-id="f2500-116">Wir haben zusätzliche Anleitungen zu weiteren Vorteilen einbezogen, die unsere Plattform bietet</span><span class="sxs-lookup"><span data-stu-id="f2500-116">We've included supplemental guidance on other benefits that our platform provides</span></span>
* <span data-ttu-id="f2500-117">Wir haben Anleitungen zur Auswahl des geeigneten Interaktionsmodells für Ihr Szenario einbezogen</span><span class="sxs-lookup"><span data-stu-id="f2500-117">We've included guidance to help select the appropriate interaction model for your scenario</span></span>

## <a name="multimodal-interaction-models"></a><span data-ttu-id="f2500-118">Kombinierte Interaktionsmodelle</span><span class="sxs-lookup"><span data-stu-id="f2500-118">Multimodal interaction models</span></span>

<span data-ttu-id="f2500-119">Basierend auf unseren bisherigen Studien und der Zusammenarbeit mit Kunden haben wir festgestellt, dass drei primäre Interaktionsmodelle für die meisten Mixed Reality-Umgebungen geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="f2500-119">Based on our research and work with customers to date, we've discovered that three primary interaction models suit the majority of mixed reality experiences.</span></span>

<span data-ttu-id="f2500-120">In vielerlei Hinsicht ist das Interaktionsmodell das mentale Modell des Benutzers zur Durchführung seiner Abläufe.</span><span class="sxs-lookup"><span data-stu-id="f2500-120">In many ways, the interaction model is the user's mental model for completing their flows.</span></span>  <span data-ttu-id="f2500-121">Jedes dieser Interaktionsmodelle ist für eine Reihe von Kundenanforderungen optimiert und ist für sich genommen benutzerfreundlich, leistungsstark und praktikabel.</span><span class="sxs-lookup"><span data-stu-id="f2500-121">Each of these interaction models is optimized for a set of customer needs, and each is convenient, powerful, and usable in its own right.</span></span> 

<span data-ttu-id="f2500-122">Das folgende Diagramm stellt eine vereinfachte Übersicht dar.</span><span class="sxs-lookup"><span data-stu-id="f2500-122">The chart below is a simplified overview.</span></span>  <span data-ttu-id="f2500-123">Ausführliche Informationen zur Verwendung der einzelnen Interaktionsmodelle sind auf den folgenden Seiten mit Bildern und Codebeispielen verknüpft.</span><span class="sxs-lookup"><span data-stu-id="f2500-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span> 

<br>
<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f2500-124"><strong>Modell</strong></span><span class="sxs-lookup"><span data-stu-id="f2500-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="f2500-125"><strong>Beispielszenarien</strong></span><span class="sxs-lookup"><span data-stu-id="f2500-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="f2500-126"><strong>Eignung</strong></span><span class="sxs-lookup"><span data-stu-id="f2500-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="f2500-127"><strong>Hardware</strong></span><span class="sxs-lookup"><span data-stu-id="f2500-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="f2500-128"><a href="hands-and-tools.md">Hände und Motion-Controller</a></span><span class="sxs-lookup"><span data-stu-id="f2500-128"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="f2500-129">3D-Raumerlebnisse, z. B. räumliches Layout und räumlicher Entwurf, Inhaltsmanipulation oder Simulation.</span><span class="sxs-lookup"><span data-stu-id="f2500-129">3D spatial experiences, e.g. spatial layout and design, content manipulation, or simulation.</span></span></td>
        <td><span data-ttu-id="f2500-130">Ideal für neue Benutzer, kombiniert mit Stimme, Eyetracking oder Anvisieren mit dem Kopf.</span><span class="sxs-lookup"><span data-stu-id="f2500-130">Great for new users, coupled with voice, eye tracking or head gaze.</span></span> <span data-ttu-id="f2500-131">Niedrige Lernkurve.</span><span class="sxs-lookup"><span data-stu-id="f2500-131">Low learning curve.</span></span> <span data-ttu-id="f2500-132">Konsistente Benutzererfahrung für Handtracking und Controller mit 6 Freiheitsgraden.</span><span class="sxs-lookup"><span data-stu-id="f2500-132">Consistent UX across hand tracking and 6 DoF controllers.</span></span></td>
        <td><span data-ttu-id="f2500-133">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f2500-133">HoloLens 2</span></span><br><span data-ttu-id="f2500-134">Immersive Headsets</span><span class="sxs-lookup"><span data-stu-id="f2500-134">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="f2500-135"><a href="hands-free.md">Freihändig</a></span><span class="sxs-lookup"><span data-stu-id="f2500-135"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="f2500-136">Kontextbezogene Erfahrungen, bei denen die Hände eines Benutzers beschäftigt sind, z. B. praxisnahes Lernen, Wartung.</span><span class="sxs-lookup"><span data-stu-id="f2500-136">Contextual experiences where a user's hands are occupied, e.g. on-the-job learning, maintenance.</span></span></td>
        <td><span data-ttu-id="f2500-137">Gewisser Lernaufwand erforderlich.</span><span class="sxs-lookup"><span data-stu-id="f2500-137">Some learning required.</span></span> <span data-ttu-id="f2500-138">Gut für Stimme und natürliche Sprache geeignet, wenn die Hände nicht verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="f2500-138">If hands are unavailable pairs well with voice and natural language.</span></span></td>
        <td><span data-ttu-id="f2500-139">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f2500-139">HoloLens 2</span></span><br><span data-ttu-id="f2500-140">HoloLens (1. Generation)</span><span class="sxs-lookup"><span data-stu-id="f2500-140">HoloLens (1st gen)</span></span><br><span data-ttu-id="f2500-141">Immersive Headsets</span><span class="sxs-lookup"><span data-stu-id="f2500-141">Immersive headsets</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="f2500-142"><a href="gaze-and-commit.md">Anvisieren mit dem Kopf und Ausführen</a></span><span class="sxs-lookup"><span data-stu-id="f2500-142"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="f2500-143">Click-Through-Erfahrungen, z. B. 3D-Präsentationen, Demos.</span><span class="sxs-lookup"><span data-stu-id="f2500-143">Click-through experiences, e.g. 3D presentations, demos.</span></span></td>
        <td><span data-ttu-id="f2500-144">Erfordert Training für HMDs, aber nicht für mobile Geräte.</span><span class="sxs-lookup"><span data-stu-id="f2500-144">Requires training on HMDs but not on mobile.</span></span> <span data-ttu-id="f2500-145">Ideal für verfügbare Controller.</span><span class="sxs-lookup"><span data-stu-id="f2500-145">Best for accessible controllers.</span></span> <span data-ttu-id="f2500-146">Ideal für HoloLens (1. Generation).</span><span class="sxs-lookup"><span data-stu-id="f2500-146">Best for HoloLens (1st gen).</span></span></td>
        <td><span data-ttu-id="f2500-147">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f2500-147">HoloLens 2</span></span><br><span data-ttu-id="f2500-148">HoloLens (1. Generation)</span><span class="sxs-lookup"><span data-stu-id="f2500-148">HoloLens (1st gen)</span></span><br><span data-ttu-id="f2500-149">Immersive Headsets</span><span class="sxs-lookup"><span data-stu-id="f2500-149">Immersive headsets</span></span><br><span data-ttu-id="f2500-150">Mobile AR</span><span class="sxs-lookup"><span data-stu-id="f2500-150">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="f2500-151">Die beste Möglichkeit, um sicherzustellen, dass es keine Lücken oder Unterbrechungen bei der Interaktion für Ihr Erlebnis gibt, besteht darin, der Anleitung für ein einzelnes Modell von Anfang bis Ende zu folgen.</span><span class="sxs-lookup"><span data-stu-id="f2500-151">The best way to ensure there are no gaps or holes in the interaction for your experience is to follow the guidance for a single model from beginning to end.</span></span> 

<span data-ttu-id="f2500-152">Um den Entwurf und die Entwicklung zu beschleunigen, haben wir ausführliche Informationen und Links zu Bildern und Codebeispielen in unsere Beschreibung der einzelnen Modelle aufgenommen.</span><span class="sxs-lookup"><span data-stu-id="f2500-152">To speed design and development, we've included detailed information and links to images and code samples within our coverage of each model.</span></span>

<span data-ttu-id="f2500-153">Aber zunächst führen die folgenden Abschnitte durch die Schritte zur Auswahl und Implementierung eines dieser Interaktionsmodelle.</span><span class="sxs-lookup"><span data-stu-id="f2500-153">But first, the sections below walk through the steps of selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="f2500-154">Am Ende dieser Seite werden Sie unsere Anleitung zu Folgendem verstehen:</span><span class="sxs-lookup"><span data-stu-id="f2500-154">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="f2500-155">Auswählen eines Interaktionsmodells für Ihren Kunden</span><span class="sxs-lookup"><span data-stu-id="f2500-155">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="f2500-156">Verwenden der Anleitung zum Interaktionsmodell</span><span class="sxs-lookup"><span data-stu-id="f2500-156">Using the interaction model guidance</span></span>
* <span data-ttu-id="f2500-157">Wechseln zwischen Interaktionsmodellen</span><span class="sxs-lookup"><span data-stu-id="f2500-157">Transitioning between interaction models</span></span>
* <span data-ttu-id="f2500-158">Entwerfen der nächsten Schritte</span><span class="sxs-lookup"><span data-stu-id="f2500-158">Design next steps</span></span>


## <a name="choose-an-interaction-model-for-your-customer"></a><span data-ttu-id="f2500-159">Auswählen eines Interaktionsmodells für Ihren Kunden</span><span class="sxs-lookup"><span data-stu-id="f2500-159">Choose an interaction model for your customer</span></span>


<span data-ttu-id="f2500-160">Höchstwahrscheinlich haben Entwickler und Gestalter auch bereits einige Ideen, welche Art von Interaktionen sie sich für ihre Benutzer vorstellen.</span><span class="sxs-lookup"><span data-stu-id="f2500-160">Most likely, developers and creators also already have some ideas in mind of the kinds of interaction experience they want their users to have.</span></span>
<span data-ttu-id="f2500-161">Um einen kundenorientierten Ansatz für den Entwurf zu fördern, empfehlen wir Ihnen, die folgende Anleitung zu befolgen, um das für Ihren Kunden optimierte Interaktionsmodell auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="f2500-161">To encourage a customer-focused approach to design, we recommend following the guidance below to select the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="f2500-162">Gründe zum Befolgen dieser Anleitung</span><span class="sxs-lookup"><span data-stu-id="f2500-162">Why follow this guidance?</span></span>

* <span data-ttu-id="f2500-163">Unsere Interaktionsmodelle werden auf objektive und subjektive Kriterien wie physische und kognitive Leistung, Intuitivität und Erlernbarkeit getestet.</span><span class="sxs-lookup"><span data-stu-id="f2500-163">Our interaction models are tested for objective and subjective criteria such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="f2500-164">Da die Interaktion unterschiedlich verläuft, können sich auch die visuellen und akustischen Angebote sowie das Objektverhalten zwischen den Interaktionsmodellen unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="f2500-164">Because interaction differs, visual and audio affordances and object behavior may also differ between the interaction models.</span></span>  
* <span data-ttu-id="f2500-165">Die Kombination von Komponenten verschiedener Interaktionsmodelle birgt das Risiko konkurrierender Angebote, z. B. simultane Handlichtstrahlen und ein Cursor zum Anvisieren mit dem Kopf, die den Benutzer überfordern und verwirren können.</span><span class="sxs-lookup"><span data-stu-id="f2500-165">Combining parts of multiple interaction models together creates the risk of competing affordances, such as simultaneous hand rays and a head-gaze cursor, which can overwhelm and confuse users.</span></span>

<span data-ttu-id="f2500-166">Hier folgen einige Beispiele dazu, wie Angebote und Verhaltensweisen für die einzelnen Interaktionsmodelle optimiert werden.</span><span class="sxs-lookup"><span data-stu-id="f2500-166">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="f2500-167">Neue Benutzer haben häufig ähnliche Fragen, z. B. „Woher weiß ich, dass das System funktioniert?“, „Woher weiß ich, über welche Möglichkeiten ich verfüge?“ und „Woher weiß ich, ob es verstanden hat, was ich gerade getan habe?“.</span><span class="sxs-lookup"><span data-stu-id="f2500-167">We often see new users have similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f2500-168"><strong>Modell</strong></span><span class="sxs-lookup"><span data-stu-id="f2500-168"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="f2500-169"><strong>Woher weiß ich, dass es funktioniert?</strong></span><span class="sxs-lookup"><span data-stu-id="f2500-169"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="f2500-170"><strong>Woher weiß ich, über welche Möglichkeiten ich verfüge?</strong></span><span class="sxs-lookup"><span data-stu-id="f2500-170"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="f2500-171"><strong>Woher weiß ich, was ich gerade getan habe?</strong></span><span class="sxs-lookup"><span data-stu-id="f2500-171"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="f2500-172"><a href="hands-and-tools.md">Hände und Motion-Controller</a></span><span class="sxs-lookup"><span data-stu-id="f2500-172"><a href="hands-and-tools.md">Hands and motion controllers</a></span></span></td>
        <td><span data-ttu-id="f2500-173">Ich sehe ein Handgittermodell, ich sehe ein Fingerspitzenangebot oder Hand-/Controllerlichtstrahlen.</span><span class="sxs-lookup"><span data-stu-id="f2500-173">I see a hand mesh, I see a fingertip affordance or hand/ controller rays.</span></span></td>
        <td><span data-ttu-id="f2500-174">Es werden greifbare Ziehpunkte oder ein Begrenzungsrahmen angezeigt, wenn meine Hand in der Nähe ist.</span><span class="sxs-lookup"><span data-stu-id="f2500-174">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="f2500-175">Ich höre Töne und sehe Animationen beim Greifen und Loslassen.</span><span class="sxs-lookup"><span data-stu-id="f2500-175">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="f2500-176"><a href="gaze-and-commit.md">Anvisieren mit dem Kopf und Ausführen</a></span><span class="sxs-lookup"><span data-stu-id="f2500-176"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="f2500-177">Ich sehe einen Cursor in der Mitte meines Sichtfelds.</span><span class="sxs-lookup"><span data-stu-id="f2500-177">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="f2500-178">Der Cursor zum Anvisieren mit dem Kopf wechselt den Zustand, wenn er sich über bestimmten Objekten befindet.</span><span class="sxs-lookup"><span data-stu-id="f2500-178">The head-gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="f2500-179">Ich sehe/höre beim Agieren visuelle und akustische Bestätigungen.</span><span class="sxs-lookup"><span data-stu-id="f2500-179">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="f2500-180"><a href="hands-free.md">Freihändig (Anvisieren mit dem Kopf und Verweilen)</a></span><span class="sxs-lookup"><span data-stu-id="f2500-180"><a href="hands-free.md">Hands-free (Head-gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="f2500-181">Ich sehe einen Cursor in der Mitte meines Sichtfelds.</span><span class="sxs-lookup"><span data-stu-id="f2500-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="f2500-182">Ich sehe eine Statusanzeige, wenn ich über einem interaktionsfähigen Objekt verweile.</span><span class="sxs-lookup"><span data-stu-id="f2500-182">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="f2500-183">Ich sehe/höre beim Agieren visuelle und akustische Bestätigungen.</span><span class="sxs-lookup"><span data-stu-id="f2500-183">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="f2500-184"><a href="hands-free.md">Freihändig (Sprachbefehle)</a></span><span class="sxs-lookup"><span data-stu-id="f2500-184"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="f2500-185">Ich sehe eine Anzeige zur Spracherkennung und Untertitel, die zeigen, was das System gehört hat.</span><span class="sxs-lookup"><span data-stu-id="f2500-185">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="f2500-186">Ich erhalte Sprachansagen und Hinweise.</span><span class="sxs-lookup"><span data-stu-id="f2500-186">I get voice prompts and hints.</span></span>  <span data-ttu-id="f2500-187">Wenn ich sage: „Was kann ich sagen?“</span><span class="sxs-lookup"><span data-stu-id="f2500-187">When I say "what can I say?"</span></span> <span data-ttu-id="f2500-188">Ich sehe ein Feedback.</span><span class="sxs-lookup"><span data-stu-id="f2500-188">I see feedback.</span></span></td>
        <td><span data-ttu-id="f2500-189">Ich sehe/höre visuelle und akustische Bestätigungen, wenn ich einen Befehl erteile, oder erhalte bei Bedarf die Benutzerumgebung zur Mehrdeutigkeitsvermeidung.</span><span class="sxs-lookup"><span data-stu-id="f2500-189">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="f2500-190">Nachfolgend sind die Fragen aufgeführt, die Teams (gemäß unserer Erfahrung) bei der Auswahl eines Interaktionsmodells geholfen haben:</span><span class="sxs-lookup"><span data-stu-id="f2500-190">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="f2500-191">Q:  Möchten meine Benutzer Hologramme berühren und präzise holografische Eingriffe durchführen?</span><span class="sxs-lookup"><span data-stu-id="f2500-191">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span><br><br>
<span data-ttu-id="f2500-192">A:  In diesem Fall sollten Sie das Interaktionsmodell für Hände und Tools für die Präzisionszielbestimmung und für Eingriffe mit Händen oder Motion-Controllern ausprobieren.</span><span class="sxs-lookup"><span data-stu-id="f2500-192">A:  If so, check out the Hands and tools interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="f2500-193">Q:  Müssen meine Benutzer für reale Aufgaben die Hände frei haben?</span><span class="sxs-lookup"><span data-stu-id="f2500-193">Q:  Do my users need to keep their hands free, for real-world tasks?</span></span><br><br>
<span data-ttu-id="f2500-194">A:  In diesem Fall sollten Sie sich das Interaktionsmodell „Freihändig“ ansehen, das durch blick- und sprachbasierte Interaktionen eine großartige freihändige Umgebung bietet.</span><span class="sxs-lookup"><span data-stu-id="f2500-194">A:  If so, take a look at the Hands-free interaction model, which provides a great hands-free experience through gaze- and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="f2500-195">Q:  Haben meine Benutzer Zeit, Interaktionen für meine Mixed Reality-Anwendung zu erlernen, oder sind Interaktionen mit einer möglichst geringen Lernkurve erforderlich?</span><span class="sxs-lookup"><span data-stu-id="f2500-195">Q:  Do my users have time to learn interactions for my mixed reality application, or do they need the interactions with the lowest learning curve possible?</span></span><br><br>
<span data-ttu-id="f2500-196">A:  Wir empfehlen das Modell für Hände und Tools für die niedrigste Lernkurve und intuitivste Interaktion, sofern die Benutzer ihre Hände zur Interaktion nutzen können.</span><span class="sxs-lookup"><span data-stu-id="f2500-196">A:  We recommend the Hands and Tools model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="f2500-197">Q:  Verwenden meine Benutzer Motion-Controller zum Zeigen und Bearbeiten?</span><span class="sxs-lookup"><span data-stu-id="f2500-197">Q:  Do my users use motion controllers for pointing and manipulation?</span></span><br><br>
<span data-ttu-id="f2500-198">A:  Das Modell für Hände und Tools enthält alle Anleitungen für ein großartiges Erlebnis mit den Motion-Controllern.</span><span class="sxs-lookup"><span data-stu-id="f2500-198">A:  The Hands and tools model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="f2500-199">Q:  Verwenden meine Benutzer einen Controller für Barrierefreiheit oder einen herkömmlichen Bluetooth-Controller, z. B. ein Klick-Gerät?</span><span class="sxs-lookup"><span data-stu-id="f2500-199">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span><br><br>
<span data-ttu-id="f2500-200">A:  Wir empfehlen das Modell „Anvisieren mit dem Kopf und Ausführen“ für alle nicht nachverfolgten Controller.</span><span class="sxs-lookup"><span data-stu-id="f2500-200">A:  We recommend the Head-gaze and Commit model for all non-tracked controllers.</span></span>  <span data-ttu-id="f2500-201">Es wurde für Benutzer entwickelt, um ein ganzheitliches Erlebnis mit einem einfachen Mechanismus für „Anvisieren und Ausführen“ zu durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="f2500-201">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanic.</span></span> 
 
6.  <span data-ttu-id="f2500-202">Q: Können meine Benutzer in einer Umgebung nur durch „Durchklicken“ voranschreiten (z. B. wie bei einer 3D-Diashow), anstatt durch kompakte Layouts von Steuerelementen der Benutzeroberfläche zu navigieren?</span><span class="sxs-lookup"><span data-stu-id="f2500-202">Q: Do my users only progress through an experience by "clicking through" (for example in a 3d slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span><br><br>
<span data-ttu-id="f2500-203">A:  Wenn Benutzer nicht viele Komponenten einer Benutzeroberfläche steuern müssen, bietet „Anvisieren mit dem Kopf und Ausführen“ eine erlernbare Option, bei der sich Benutzer nicht um die Zielbestimmung kümmern müssen.</span><span class="sxs-lookup"><span data-stu-id="f2500-203">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="f2500-204">Q:  Verwenden meine Benutzer sowohl HoloLens (1. Generation) als auch HoloLens 2/Windows Immersive (VR-Headsets)?</span><span class="sxs-lookup"><span data-stu-id="f2500-204">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/ Windows Immersive (VR headsets)</span></span><br><br>
<span data-ttu-id="f2500-205">A:  Da „Anvisieren mit dem Kopf und Ausführen“ das Interaktionsmodell für HoloLens (1. Generation) ist, empfehlen wir Entwicklern, die HoloLens (1. Generation) unterstützen, „Anvisieren mit dem Kopf und Ausführen“ nur alle Features oder Modi zu verwenden, die Benutzer auf einem HoloLens-Headset (1. Generation) erleben können.</span><span class="sxs-lookup"><span data-stu-id="f2500-205">A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users may experience on a HoloLens (1st gen) headset.</span></span>  <span data-ttu-id="f2500-206">Weitere Informationen zur Erstellung einer großartigen Umgebung für mehrere HoloLens-Generationen finden Sie nachfolgend unter *Wechseln zwischen Interaktionsmodellen*.</span><span class="sxs-lookup"><span data-stu-id="f2500-206">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="f2500-207">Q: Wie sieht es für generell mobile Benutzer (die einen großen Raum einnehmen oder sich zwischen verschiedenen Räumen bewegen) gegenüber Benutzern aus, die dazu neigen, in einem einzelnen Raum zu arbeiten?</span><span class="sxs-lookup"><span data-stu-id="f2500-207">Q: What about for users who are generally mobile (covering a large space or moving between spaces), versus users who tend to work in a single space?</span></span><br><br>
<span data-ttu-id="f2500-208">A:  Für diese Benutzer ist jedes der Interaktionsmodelle geeignet.</span><span class="sxs-lookup"><span data-stu-id="f2500-208">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="f2500-209">Weitere Anleitungen zum App-Design sind [bald verfügbar](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="f2500-209">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transition-interaction-models"></a><span data-ttu-id="f2500-210">Wechseln zwischen Interaktionsmodellen</span><span class="sxs-lookup"><span data-stu-id="f2500-210">Transition interaction models</span></span>
<span data-ttu-id="f2500-211">Es kann auch vorkommen, dass Ihre Anwendungsfälle die Verwendung mehrerer Interaktionsmodelle erfordern.</span><span class="sxs-lookup"><span data-stu-id="f2500-211">There are also cases where your use cases may require that utilizing more than one interaction model.</span></span>  <span data-ttu-id="f2500-212">Beim „Erstellungsablauf“ Ihrer App wird z. B. das Interaktionsmodell „Hände und Motion-Controller“ verwendet, aber Sie möchten einen Freihandmodus für Außendiensttechniker verwenden.</span><span class="sxs-lookup"><span data-stu-id="f2500-212">For example, your app's "creation flow" utilizes the Hands and motion controllers interaction model, but you want to employ a Hands-free mode for field technicians.</span></span>  

<span data-ttu-id="f2500-213">Wenn Ihre Umgebung mehrere Interaktionsmodelle erfordert, können viele Endbenutzer Schwierigkeiten beim Übergang von einem Modell zum anderen haben – insbesondere Benutzer, die noch nicht mit Mixed Reality vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="f2500-213">If your experience does require multiple interaction models, we've found that many end users may encounter difficulty transitioning from one model to another -- especially users who are new to mixed reality.</span></span>

> [!Note]
> <span data-ttu-id="f2500-214">Um Designern und Entwicklern bei Entscheidungen zu unterstützen, die sich bei Mixed Reality als schwierig erweisen können, arbeiten wir an weiteren Anleitungen für die Verwendung mehrerer Interaktionsmodelle.</span><span class="sxs-lookup"><span data-stu-id="f2500-214">To help guide designers and developers through choices that can be difficult in MR, we're working on more guidance for using multiple interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="f2500-215">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f2500-215">See also</span></span>
* [<span data-ttu-id="f2500-216">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="f2500-216">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="f2500-217">Anvisieren mit dem Kopf und Verweilen</span><span class="sxs-lookup"><span data-stu-id="f2500-217">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="f2500-218">Direkte Manipulation mit den Händen</span><span class="sxs-lookup"><span data-stu-id="f2500-218">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="f2500-219">Zeigen und Ausführen mit den Händen</span><span class="sxs-lookup"><span data-stu-id="f2500-219">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="f2500-220">Gesten</span><span class="sxs-lookup"><span data-stu-id="f2500-220">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="f2500-221">Sprachbefehle</span><span class="sxs-lookup"><span data-stu-id="f2500-221">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="f2500-222">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="f2500-222">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="f2500-223">Raumklangentwurf</span><span class="sxs-lookup"><span data-stu-id="f2500-223">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="f2500-224">Gestaltung von räumlicher Abbildung</span><span class="sxs-lookup"><span data-stu-id="f2500-224">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="f2500-225">Komfort</span><span class="sxs-lookup"><span data-stu-id="f2500-225">Comfort</span></span>](comfort.md)

