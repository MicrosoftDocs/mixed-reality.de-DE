---
title: Übersicht über die Multimodale Interaktion
description: Übersicht über die Multimodale Interaktion
author: shengkait
ms.author: shengkait
ms.date: 04/11/2019
ms.topic: article
keywords: Gemischte Realität Blicke, Blicke Ziel ist, handelt es sich bei der Interaktion, Entwerfen
ms.openlocfilehash: c762518a224138dab248670eaef23ccb92016fce
ms.sourcegitcommit: a4a53e6772805d89a47588857e3e8fb1fd8d9710
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65469105"
---
# <a name="introducing-instinctual-interactions"></a><span data-ttu-id="da961-104">Einführung in instinctual Interaktionen</span><span class="sxs-lookup"><span data-stu-id="da961-104">Introducing instinctual interactions</span></span>
<span data-ttu-id="da961-105">Die Philosophie von einfachen, instinctual Interaktionen wird in der Microsoft Mixed Reality-Plattform Gewebe.</span><span class="sxs-lookup"><span data-stu-id="da961-105">The philosophy of simple, instinctual interactions is woven throughout the Microsoft Mixed Reality platform.</span></span>  <span data-ttu-id="da961-106">Wir haben drei Schritte aus, um sicherzustellen, dass die Anwendung-Designer und Entwickler einfache und intuitive Interaktionen für ihre Kunden bereitstellen können, erstellt.</span><span class="sxs-lookup"><span data-stu-id="da961-106">We've taken three steps to ensure that application designers and developers can provide easy and intuitive interactions for their customers.</span></span> 

<span data-ttu-id="da961-107">Erstens haben dafür gesorgt, dass unsere erstaunliche Sensoren und Eingabe-Technologie, einschließlich manuell nachverfolgen, Eye-tracking und natürlicher Sprache, in nahtlose Multimodale interaktionsmodellen kombinieren.</span><span class="sxs-lookup"><span data-stu-id="da961-107">First, we've made sure our amazing sensors and input technology, including hand tracking, eye tracking, and natural language, combine into seamless multimodal interaction models.</span></span>  <span data-ttu-id="da961-108">Basierend auf unseren Studien entwerfen und entwickeln multimodally – und nicht auf einzelner Eingaben basiert – ist der Schlüssel zum Erstellen von instinctual Funktionen.</span><span class="sxs-lookup"><span data-stu-id="da961-108">Based on our research, designing and developing multimodally -- and not based on single inputs -- is the key to creating instinctual experiences.</span></span>

<span data-ttu-id="da961-109">Als Nächstes das wissen wir viele Entwickler mehrere Zielgeräten, ob das HoloLens-2 und HoloLens bedeutet (1. Generation) oder HoloLens und VR.</span><span class="sxs-lookup"><span data-stu-id="da961-109">Secondly, we recognize that many developers target multiple devices, whether that means HoloLens 2 and HoloLens (1st gen) or HoloLens and VR.</span></span>  <span data-ttu-id="da961-110">Wir haben so gestaltet, dass unsere interaktionsmodellen, geräteübergreifendes arbeiten (auch wenn die Eingabe-Technologie auf den einzelnen Geräten variiert).</span><span class="sxs-lookup"><span data-stu-id="da961-110">So we've designed our interaction models to work across devices (even if the input technology varies on each device).</span></span>  <span data-ttu-id="da961-111">Z. B., weit Interaktion in eine Immersive Windows Kopfhörer mit einem Controller 6DOF und weit Interaktion auf einem HoloLens 2 beide verwenden, die identische visueller Hinweise und dem Muster für geräteübergreifenden Anwendungen zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="da961-111">For example, far interaction on a Windows Immersive headset with a 6DOF controller and far interaction on a HoloLens 2 both use the identical affordances and patterns, making it easy for cross-device applications.</span></span> <span data-ttu-id="da961-112">Ist nicht nur diesem praktische für Entwickler und Designer, aber natürlich erscheint für Endbenutzer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="da961-112">Not only is this convenient for developers and designers, but it feels natural to end users.</span></span> 

<span data-ttu-id="da961-113">Schließlich, während wir erkennen, dass es Tausende von effektiven interessanter, magische Interaktionen in MR möglich, wir haben festgestellt, absichtlich mit einer einzelnen Interaktionsmodell End-to-End in eine Anwendung ist die beste Möglichkeit, um sicherzustellen, dass Benutzer erfolgreich und haben Sie eine großartige Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="da961-113">Lastly, while we recognize that there are thousands of effective, engaging, and magical interactions possible in MR, we have found that intentionally employing a single interaction model end to end in an application is the best way to ensure users are successful and have a great experience.</span></span>  <span data-ttu-id="da961-114">Zu diesem Zweck haben wir drei Dinge in dieser Anleitung für die Interaktion mit einbezogen:</span><span class="sxs-lookup"><span data-stu-id="da961-114">To that end, we've included three things in this interaction guidance:</span></span>
* <span data-ttu-id="da961-115">Wir haben diese Anleitung für die drei interaktionsmodelle mit primären und den Komponenten und Muster, die jeweils erforderliche strukturiert.</span><span class="sxs-lookup"><span data-stu-id="da961-115">We've structured this guidance around the three primary interaction models and the components and patterns required for each</span></span>
* <span data-ttu-id="da961-116">Wir haben zusätzliche Anleitungen zu den anderen Vorteilen, die unsere Plattform bietet eingefügt.</span><span class="sxs-lookup"><span data-stu-id="da961-116">We've included supplemental guidance on other benefits that our platform provides</span></span>
* <span data-ttu-id="da961-117">Wir haben dabei helfen, wählen Sie die entsprechenden Interaktionsmodell für Ihr Szenario eingefügt.</span><span class="sxs-lookup"><span data-stu-id="da961-117">We've included guidance to help select the appropriate interaction model for your scenario</span></span>


## <a name="three-multimodal-interaction-models"></a><span data-ttu-id="da961-118">Drei interaktionsmodelle für Multimodale</span><span class="sxs-lookup"><span data-stu-id="da961-118">Three multimodal interaction models</span></span>
<span data-ttu-id="da961-119">Basierend auf unseren Untersuchungen von und Arbeiten mit Kunden, Datum, haben wir festgestellt, dass es sich bei drei primäre interaktionsmodelle die Mehrheit der Mixed Reality-Umgebungen anpassen.</span><span class="sxs-lookup"><span data-stu-id="da961-119">Based on our research and work with customers to date, we've discovered that three primary interaction models suit the majority of Mixed Reality experiences.</span></span>

<span data-ttu-id="da961-120">In vielerlei Hinsicht ist das Interaktionsmodell des Benutzers mentales Modell zum Ausführen ihrer Flows.</span><span class="sxs-lookup"><span data-stu-id="da961-120">In many ways, the interaction model  is the user's mental model for completing their flows.</span></span>  <span data-ttu-id="da961-121">Jedes dieser interaktionsmodelle ist optimiert für einen Satz von Anforderungen des Kunden, und jede ist praktisch, leistungsfähigen und eigenständig verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="da961-121">Each of these interaction models is optimized for a set of customer needs, and each is convenient, powerful, and usable in its own right.</span></span> 

<span data-ttu-id="da961-122">Im folgenden Diagramm ist eine vereinfachte Übersicht über.</span><span class="sxs-lookup"><span data-stu-id="da961-122">The chart below is a simplified overview.</span></span>  <span data-ttu-id="da961-123">Ausführliche Informationen für die Verwendung der einzelnen Modelle für die Interaktion ist in den folgenden Seiten, Bilder und Codebeispiele verknüpft.</span><span class="sxs-lookup"><span data-stu-id="da961-123">Detailed information for using each interaction model is linked in the pages below with images and code samples.</span></span>  

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="da961-124"><strong>Modell</strong></span><span class="sxs-lookup"><span data-stu-id="da961-124"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="da961-125"><strong>Beispielszenarien</strong></span><span class="sxs-lookup"><span data-stu-id="da961-125"><strong>Example scenarios</strong></span></span></td>
        <td><span data-ttu-id="da961-126"><strong>Anpassen</strong></span><span class="sxs-lookup"><span data-stu-id="da961-126"><strong>Fit</strong></span></span></td>
        <td><span data-ttu-id="da961-127"><strong>Hardware</strong></span><span class="sxs-lookup"><span data-stu-id="da961-127"><strong>Hardware</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="da961-128"><a href="hands-and-tools.md">Praktische und tools</a></span><span class="sxs-lookup"><span data-stu-id="da961-128"><a href="hands-and-tools.md">Hands and tools</a></span></span></td>
        <td><span data-ttu-id="da961-129">3D räumliche Funktionen</span><span class="sxs-lookup"><span data-stu-id="da961-129">3D spatial experiences</span></span><br><span data-ttu-id="da961-130">z. B. räumliche Layout und Entwurf, Bearbeiten von Inhalten oder simulation</span><span class="sxs-lookup"><span data-stu-id="da961-130">e.g. spatial layout and design, content manipulation, or simulation</span></span></td>
        <td><span data-ttu-id="da961-131">Ideal für neue Benutzer</span><span class="sxs-lookup"><span data-stu-id="da961-131">Great for new users</span></span><br><span data-ttu-id="da961-132">Niedrige Lernkurve</span><span class="sxs-lookup"><span data-stu-id="da961-132">Low learning curve</span></span><br><span data-ttu-id="da961-133">In einfachen visual visueller Hinweise an die Hand geben.</span><span class="sxs-lookup"><span data-stu-id="da961-133">Grounded in easy visual affordances</span></span><br><span data-ttu-id="da961-134">Konsistente Benutzererfahrung in manuell nachverfolgen und 6 FG-Controller</span><span class="sxs-lookup"><span data-stu-id="da961-134">Consistent UX across hand tracking and 6 DoF controllers</span></span><br><span data-ttu-id="da961-135">In Kombination mit der Stimme, Eye-Tracking oder Head Blicke hervorragende</span><span class="sxs-lookup"><span data-stu-id="da961-135">Great when coupled with voice, eye tracking, or head gaze</span></span></td>
        <td><span data-ttu-id="da961-136">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="da961-136">HoloLens 2</span></span><br><span data-ttu-id="da961-137">Windows mit 6DOF Controller Immersive</span><span class="sxs-lookup"><span data-stu-id="da961-137">Windows Immersive w/ 6DOF Controllers</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="da961-138"><a href="hands-free.md">Freihändig</a></span><span class="sxs-lookup"><span data-stu-id="da961-138"><a href="hands-free.md">Hands-free</a></span></span></td>
        <td><span data-ttu-id="da961-139">Kontextbezogener Umgebungen eines Benutzers Hände, in dem z. B. für die Auftrag-learning, Wartung belegt sind</span><span class="sxs-lookup"><span data-stu-id="da961-139">Contextual experiences where a user's hands are occupied e.g. on the-job learning, maintenance</span></span></td>
        <td><span data-ttu-id="da961-140">Einige erforderlichen lernen</span><span class="sxs-lookup"><span data-stu-id="da961-140">Some learning required</span></span><br><span data-ttu-id="da961-141">Wenn die Hände nicht verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="da961-141">If hands are unavailable</span></span><br><span data-ttu-id="da961-142">Paare mit Sprach- und natürlicher Sprache</span><span class="sxs-lookup"><span data-stu-id="da961-142">pairs well with voice and natural language</span></span></td>
        <td><span data-ttu-id="da961-143">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="da961-143">HoloLens 2</span></span><br><span data-ttu-id="da961-144">HoloLens (1. Generation)</span><span class="sxs-lookup"><span data-stu-id="da961-144">HoloLens (1st gen)</span></span><br> <span data-ttu-id="da961-145">Immersive Windows</span><span class="sxs-lookup"><span data-stu-id="da961-145">Windows Immersive</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="da961-146"><a href="gaze-and-commit.md">Anvisieren mit dem Kopf und Ausführen</a></span><span class="sxs-lookup"><span data-stu-id="da961-146"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="da961-147">Per Klick hat z. B. 3D Präsentationen, demos</span><span class="sxs-lookup"><span data-stu-id="da961-147">Click-through experiences e.g. 3D presentations, demos</span></span></td>
        <td><span data-ttu-id="da961-148">Schulung für HMDs jedoch nicht für Mobile erfordert</span><span class="sxs-lookup"><span data-stu-id="da961-148">Requires training on HMDs but not on mobile</span></span><br><span data-ttu-id="da961-149">Am besten für Controller, zugegriffen werden kann</span><span class="sxs-lookup"><span data-stu-id="da961-149">Best for accessible controllers</span></span><br><span data-ttu-id="da961-150">Am besten für HoloLens (1. Generation)</span><span class="sxs-lookup"><span data-stu-id="da961-150">Best for HoloLens (1st gen)</span></span></td>
        <td><span data-ttu-id="da961-151">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="da961-151">HoloLens 2</span></span><br><span data-ttu-id="da961-152">HoloLens (1. Generation)</span><span class="sxs-lookup"><span data-stu-id="da961-152">HoloLens (1st gen)</span></span><br> <span data-ttu-id="da961-153">Immersive Windows</span><span class="sxs-lookup"><span data-stu-id="da961-153">Windows Immersive</span></span><br> <span data-ttu-id="da961-154">Mobile AR</span><span class="sxs-lookup"><span data-stu-id="da961-154">Mobile AR</span></span></td>
    </tr>
</table>
<br>

<span data-ttu-id="da961-155">Die beste Möglichkeit, um sicherzustellen, dass keine Lücken oder Lücken bei der Interaktion für Ihre Umgebung ist, die Anleitung für ein einzelnes Modell von Anfang bis Ende zu befolgen.</span><span class="sxs-lookup"><span data-stu-id="da961-155">The best way to ensure there are no gaps or holes in the interaction for your experience is to follow the guidance for a single model from beginning to end.</span></span> 

<span data-ttu-id="da961-156">Um den Entwurf und Entwicklung zu beschleunigen, haben wir ausführliche Informationen und Links zu Bildern und Codebeispiele in unsere Abdeckung jedes Modells eingefügt.</span><span class="sxs-lookup"><span data-stu-id="da961-156">To speed design and development, we've included detailed information and links to images and code samples within our coverage of each model.</span></span>

<span data-ttu-id="da961-157">Aber zuerst die Schritte zum auswählen und Implementieren eines dieser interaktionsmodelle in den folgenden Abschnitten erläutert.</span><span class="sxs-lookup"><span data-stu-id="da961-157">But first, the sections below walk through the steps of selecting and implementing one of these interaction models.</span></span>  
 
### <a name="by-the-end-of-this-page-you-will-understand-our-guidance-on"></a><span data-ttu-id="da961-158">Am Ende dieser Seite wissen Sie, unsere Leitfäden auf:</span><span class="sxs-lookup"><span data-stu-id="da961-158">By the end of this page, you will understand our guidance on:</span></span>
 
* <span data-ttu-id="da961-159">Auswählen einer Interaktionsmodell für Ihre Kunden</span><span class="sxs-lookup"><span data-stu-id="da961-159">Choosing an interaction model for your customer</span></span>
* <span data-ttu-id="da961-160">Mithilfe der Interaktion Modell Anleitungen</span><span class="sxs-lookup"><span data-stu-id="da961-160">Using the interaction model guidance</span></span>
* <span data-ttu-id="da961-161">Übergang zwischen interaktionsmodelle</span><span class="sxs-lookup"><span data-stu-id="da961-161">Transitioning between interaction models</span></span>
* <span data-ttu-id="da961-162">Entwurf der nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="da961-162">Design next steps</span></span>

## <a name="choosing-an-interaction-model-for-your-customer"></a><span data-ttu-id="da961-163">Auswählen einer Interaktionsmodell für Ihre Kunden</span><span class="sxs-lookup"><span data-stu-id="da961-163">Choosing an interaction model for your customer</span></span>

<span data-ttu-id="da961-164">In den meisten Fällen Entwickler und Ersteller verfügen bereits über einige Ideen Beachten Sie die Art der Interaktion geboten, die sie für ihre Benutzer möchten.</span><span class="sxs-lookup"><span data-stu-id="da961-164">Most likely, developers and creators already have some ideas in mind of the kinds of interaction experience they want for their users.</span></span>
<span data-ttu-id="da961-165">Um einen Kunden bezogener Ansatz zum Entwerfen, zu fördern, empfehlen wir, gemäß der Anleitung unten das Interaktionsmodell auswählen, das für Ihre Kunden optimiert ist.</span><span class="sxs-lookup"><span data-stu-id="da961-165">To encourage a customer-focused approach to design, we recommend following the guidance below to select the interaction model that's optimized for your customer.</span></span>

### <a name="why-follow-this-guidance"></a><span data-ttu-id="da961-166">Befolgen diese Anweisungen, warum?</span><span class="sxs-lookup"><span data-stu-id="da961-166">Why follow this guidance?</span></span>

* <span data-ttu-id="da961-167">Die interaktionsmodelle sind für Ziel und subjektive Kriterien wie z. B. physische und kognitive Zeit-und Intuition und Learnability getestet.</span><span class="sxs-lookup"><span data-stu-id="da961-167">Our interaction models are tested for objective and subjective criteria such as physical and cognitive effort, intuitiveness, and learnability.</span></span> 
* <span data-ttu-id="da961-168">Da Interaktion abweicht, können zwischen den interaktionsmodellen auch SEH- und visueller Hinweise und Objektverhalten abweichen.</span><span class="sxs-lookup"><span data-stu-id="da961-168">Because interaction differs, visual and audio affordances and object behavior may also differ between the interaction models.</span></span>  
* <span data-ttu-id="da961-169">Kombinieren Teile des interaktionsmodelle wird das Risiko von konkurrierenden visueller Hinweise, wie z. B. gleichzeitige Hand Strahlung und einen Cursor Blicke zu entlasten und die Benutzer erstellt.</span><span class="sxs-lookup"><span data-stu-id="da961-169">Combining parts of multiple interaction models together creates the risk of competing affordances, such as simultaneous hand rays and a gaze cursor, which overwhelm and confuse users.</span></span>

<span data-ttu-id="da961-170">Hier sind einige Beispiele für wie visueller Hinweise und Verhaltensweisen für die einzelnen Interaktionsmodell optimiert sind.</span><span class="sxs-lookup"><span data-stu-id="da961-170">Here are some examples of how affordances and behaviors are optimized for each interaction model.</span></span>  <span data-ttu-id="da961-171">Wir häufig finden Sie unter neuen Benutzer als ähnliche Fragen, wie z. B. "Wie erfahre ich, das System arbeitet, wie erfahre ich, was kann ich tun, und wie weiß ich, wenn es verstanden gerade getan?"</span><span class="sxs-lookup"><span data-stu-id="da961-171">We often see new users as similar questions, such as "how do I know the system is working, how do I know what I can do, and how do I know if it understood what I just did?"</span></span>

<br>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="da961-172"><strong>Modell</strong></span><span class="sxs-lookup"><span data-stu-id="da961-172"><strong>Model</strong></span></span></td>
        <td><span data-ttu-id="da961-173"><strong>Wie erfahre ich, es funktioniert?</strong></span><span class="sxs-lookup"><span data-stu-id="da961-173"><strong>How do I know it's working?</strong></span></span></td>
        <td><span data-ttu-id="da961-174"><strong>Wie weiß ich, was kann ich tun?</strong></span><span class="sxs-lookup"><span data-stu-id="da961-174"><strong>How do I know what I can do?</strong></span></span></td>
        <td><span data-ttu-id="da961-175"><strong>Wie weiß ich, was gerade demonstriert hat?</strong></span><span class="sxs-lookup"><span data-stu-id="da961-175"><strong>How do I know what I just did?</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="da961-176"><a href="hands-and-tools.md">Praktische und tools</a></span><span class="sxs-lookup"><span data-stu-id="da961-176"><a href="hands-and-tools.md">Hands and tools</a></span></span></td>
        <td><span data-ttu-id="da961-177">Ich sehe, dass eine Hand mesh, ich sehe eine fingertippen Unterstützung oder manuell / Controller Strahlung.</span><span class="sxs-lookup"><span data-stu-id="da961-177">I see a hand mesh, I see a fingertip affordance or hand/ controller rays.</span></span></td>
        <td><span data-ttu-id="da961-178">Ich sehe grabbable Handles oder eines umgebenden Felds angezeigt werden, wenn meine Hand in der Nähe befindet.</span><span class="sxs-lookup"><span data-stu-id="da961-178">I see grabbable handles or a bounding box appear when my hand is near.</span></span></td>
        <td><span data-ttu-id="da961-179">Ich Töne hörbar hören und sehen Sie Animationen auf Ziehpunkte und Version.</span><span class="sxs-lookup"><span data-stu-id="da961-179">I hear audible tones and see animations on grab and release.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="da961-180"><a href="gaze-and-commit.md">Anvisieren mit dem Kopf und Ausführen</a></span><span class="sxs-lookup"><span data-stu-id="da961-180"><a href="gaze-and-commit.md">Head-gaze and commit</a></span></span></td>
        <td><span data-ttu-id="da961-181">Ich sehe es sich um einen Cursor in der Mitte der meine Sichtfeld.</span><span class="sxs-lookup"><span data-stu-id="da961-181">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="da961-182">Der Cursor Blicke ändert, Status, wenn Sie über bestimmte Objekte.</span><span class="sxs-lookup"><span data-stu-id="da961-182">The gaze cursor changes state when over certain objects.</span></span></td>
        <td><span data-ttu-id="da961-183">Ich finden Sie unter bzw. visual und akustische Bestätigungen zu hören, wenn Aktionen ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="da961-183">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>   
    <tr>
        <td><span data-ttu-id="da961-184"><a href="hands-free.md">Physisch (Blicke und Dwell)</a></span><span class="sxs-lookup"><span data-stu-id="da961-184"><a href="hands-free.md">Hands-free (Gaze and dwell)</a></span></span></td>
        <td><span data-ttu-id="da961-185">Ich sehe es sich um einen Cursor in der Mitte der meine Sichtfeld.</span><span class="sxs-lookup"><span data-stu-id="da961-185">I see a cursor in the center of my field of view.</span></span></td>
        <td><span data-ttu-id="da961-186">Ich sehe eine Statusanzeige eingeblendet, wenn ich auf ein Objekt es länger aufhalten.</span><span class="sxs-lookup"><span data-stu-id="da961-186">I see a progress indicator when I dwell on an interactable object.</span></span></td>
        <td><span data-ttu-id="da961-187">Ich finden Sie unter bzw. visual und akustische Bestätigungen zu hören, wenn Aktionen ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="da961-187">I see/ hear visual and audible confirmations when I take action.</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="da961-188"><a href="hands-free.md">Physisch (Voice-Befehle)</a></span><span class="sxs-lookup"><span data-stu-id="da961-188"><a href="hands-free.md">Hands-free (Voice commanding)</a></span></span></td>
        <td><span data-ttu-id="da961-189">Ich sehe ein Indikator überwacht und Untertiteln für Hörgeschädigte, die zeigen, was das System gehört.</span><span class="sxs-lookup"><span data-stu-id="da961-189">I see a listening indicator and captions that show what the system heard.</span></span></td>
        <td><span data-ttu-id="da961-190">Erhalte ich Sprachansagen und Hinweise.</span><span class="sxs-lookup"><span data-stu-id="da961-190">I get voice prompts and hints.</span></span>  <span data-ttu-id="da961-191">Wenn ich sage "Was ich sagen können?"</span><span class="sxs-lookup"><span data-stu-id="da961-191">When I say "what can I say?"</span></span> <span data-ttu-id="da961-192">Ich sehe Feedback.</span><span class="sxs-lookup"><span data-stu-id="da961-192">I see feedback.</span></span></td>
        <td><span data-ttu-id="da961-193">Ich finden Sie unter bzw. visual und akustische Bestätigungen zu hören, wenn ich einen Befehl erhalten, oder rufen zur mehrdeutigkeitsvermeidung UX bei Bedarf.</span><span class="sxs-lookup"><span data-stu-id="da961-193">I see/ hear visual and audible confirmations when I give a command, or get disambiguation UX when needed.</span></span></a></td>
    </tr>
</table>

### <a name="below-are-the-questions-that-weve-found-help-teams-select-an-interaction-model"></a><span data-ttu-id="da961-194">Im folgenden finden Sie Fragen, die wir Hilfe Teams wählen ein Interaktionsmodell gefunden haben:</span><span class="sxs-lookup"><span data-stu-id="da961-194">Below are the questions that we've found help teams select an interaction model:</span></span>
 
1.  <span data-ttu-id="da961-195">Q:  Möchten meine Benutzer Hologramme touch und holographic Manipulationen mit einfacher Genauigkeit ausführen?</span><span class="sxs-lookup"><span data-stu-id="da961-195">Q:  Do my users want to touch holograms and perform precision holographic manipulations?</span></span>
<span data-ttu-id="da961-196">A:  Wenn dies der Fall ist, checken Sie das Interaktionsmodell Hände und Tools für die Genauigkeit als Ziel und-Bearbeitung in die Hände oder während der Übertragung Controller aus.</span><span class="sxs-lookup"><span data-stu-id="da961-196">A:  If so, check out the Hands and Tools interaction model for precision targeting and manipulation with hands or motion controllers.</span></span>
 
2.  <span data-ttu-id="da961-197">Q:  Müssen meine Benutzer, wenn sich kostenlos, für wirklichkeitsgetreue Aufgaben zu halten?</span><span class="sxs-lookup"><span data-stu-id="da961-197">Q:  Do my users need to keep their hands free, for real-world tasks?</span></span>
<span data-ttu-id="da961-198">A:  Wenn dies der Fall ist, sehen Sie sich das Interaktionsmodell Hands-Free, das physisch rundum durch Interaktionen Blicke und sprachbasierten bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="da961-198">A:  If so, take a look at the Hands-Free interaction model, which provides a great hands-free experience through gaze- and voice-based interactions.</span></span>
 
3.  <span data-ttu-id="da961-199">Q:  Haben meine Benutzer noch Zeit, um Interaktionen für meine mixed Reality-Anwendung zu erfahren, oder benötigen sie die Interaktionen mit der niedrigsten Lernkurve möglich?</span><span class="sxs-lookup"><span data-stu-id="da961-199">Q:  Do my users have time to learn interactions for my mixed reality application, or do they need the interactions with the lowest learning curve possible?</span></span>
<span data-ttu-id="da961-200">A:  Das Modell Hände und Tools für die niedrigste Lernkurve und die intuitivste Interaktionen, wird empfohlen, solange der Benutzer sich für die Interaktion verwenden können.</span><span class="sxs-lookup"><span data-stu-id="da961-200">A:  We recommend the Hands and Tools model for the lowest learning curve and most intuitive interactions, as long as users are able to use their hands for interaction.</span></span>
 
4.  <span data-ttu-id="da961-201">Q:  Werden meine Benutzer während der Übertragung Controller für verweist und-Bearbeitung verwendet?</span><span class="sxs-lookup"><span data-stu-id="da961-201">Q:  Do my users use motion controllers for pointing and manipulation?</span></span>
<span data-ttu-id="da961-202">A:  Das praktische und Tools umfasst alle Anleitungen für die Erfahrung mit der Motion-Controller.</span><span class="sxs-lookup"><span data-stu-id="da961-202">A:  The Hands and Tools model includes all guidance for a great experience with motion controllers.</span></span>
 
5.  <span data-ttu-id="da961-203">Q:  Verwenden meine Benutzer einen Zugriff auf Controller oder eine allgemeine Bluetooth-Controller, z. B. eine Clicker?</span><span class="sxs-lookup"><span data-stu-id="da961-203">Q:  Do my users use an accessibility controller or a common Bluetooth controller, such as a clicker?</span></span>
<span data-ttu-id="da961-204">A:  Es wird empfohlen, das Head-Blicke und Commit-Modell für alle Controller im nicht nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="da961-204">A:  We recommend the Head-gaze and commit model for all non-tracked controllers.</span></span>  <span data-ttu-id="da961-205">Es wurde entwickelt, damit der Benutzer eine gesamte Erfahrung mit einer einfachen "" Target "und" Commit "Mechanikers durchlaufen kann.</span><span class="sxs-lookup"><span data-stu-id="da961-205">It's designed to allow a user to traverse an entire experience with a simple "target and commit" mechanic.</span></span> 
 
6.  <span data-ttu-id="da961-206">Q: Status meine Benutzer nur über eine Benutzeroberfläche von "bei der Betrachtung" (z. B. in einer 3d Diaschau-ähnliche Umgebung), im Gegensatz zu dichten Layouts von UI-Steuerelementen zu navigieren?</span><span class="sxs-lookup"><span data-stu-id="da961-206">Q: Do my users only progress through an experience by "clicking through" (for example in a 3d slideshow-like environment), as opposed to navigating dense layouts of UI controls?</span></span>
<span data-ttu-id="da961-207">A:  Wenn Benutzer nicht um einen Großteil der Benutzeroberfläche steuern müssen, bietet Head-Blicke und Commit eine learnable Option, in dem Benutzer keine Zielgruppenadressierung kümmern.</span><span class="sxs-lookup"><span data-stu-id="da961-207">A:  If users do not need to control a lot of UI, Head-gaze and commit offers a learnable option where users do not have to worry about targeting.</span></span> 
 
7.  <span data-ttu-id="da961-208">Q:  Meine Benutzer verwenden Sie beide HoloLens (1. Generation) und HoloLens 2 / Immersive Windows (VR Headsets) A:  Da Head-Blicke und Commit ist das Interaktionsmodell für HoloLens (der 1. Generation), es wird empfohlen, die Entwickler, die HoloLens unterstützt (1. Generation) Head-Blicke verwenden und einen commit für alle Features oder Modi, die Benutzer auf eine HoloLens auftreten können (der 1. Generation) Kopfhörer.</span><span class="sxs-lookup"><span data-stu-id="da961-208">Q:  Do my users use both HoloLens (1st gen) and HoloLens 2/ Windows Immersive (VR headsets) A:  Since Head-gaze and commit is the interaction model for HoloLens (1st gen), we recommend that creators who support HoloLens (1st gen) use Head-gaze and commit for any features or modes that users may experience on a HoloLens (1st gen) headset.</span></span>  <span data-ttu-id="da961-209">Finden Sie im nächsten Abschnitt unten auf *Übergang interaktionsmodelle* ausführliche Informationen zum Erstellen einer überzeugenden Umgebung für mehrere Generationen von HoloLens.</span><span class="sxs-lookup"><span data-stu-id="da961-209">Please see the next section below on *Transitioning interaction models* for details on making a great experience for multiple HoloLens generations.</span></span>
 
8.  <span data-ttu-id="da961-210">Q: Wie sieht es für Benutzer, die in der Regel mobile (deckt einen großen Speicherplatz oder Verschieben zwischen Leerzeichen), sind im Vergleich zu Benutzer, die in der Regel in einem einzelnen Leerzeichen arbeiten?</span><span class="sxs-lookup"><span data-stu-id="da961-210">Q: What about for users who are generally mobile (covering a large space or moving between spaces), versus users who tend to work in a single space?</span></span>  
<span data-ttu-id="da961-211">A:  Keines der interaktionsmodelle funktioniert für diese Benutzer.</span><span class="sxs-lookup"><span data-stu-id="da961-211">A:  Any of the interaction models will work for these users.</span></span>  

> [!NOTE]
> <span data-ttu-id="da961-212">Weitere Anleitungen, die speziell für app-Design [bald](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="da961-212">More guidance specific to app design [coming soon](index.md#news-and-notes).</span></span>


## <a name="transition-interaction-models"></a><span data-ttu-id="da961-213">Übergang von interaktionsmodellen</span><span class="sxs-lookup"><span data-stu-id="da961-213">Transition interaction models</span></span>
<span data-ttu-id="da961-214">Es gibt auch Fälle, in dem Ihre Anwendungsfälle, die Nutzung von mehr als ein Interaktionsmodell möglicherweise erfordern.</span><span class="sxs-lookup"><span data-stu-id="da961-214">There are also cases where your use cases may require that utilizing more than one interaction model.</span></span>  <span data-ttu-id="da961-215">Z. B. Erstellung Ihrer app "Datenfluss" nutzt das Interaktionsmodell Hände und Tools, aber Sie einen Modus physisch für Außendiensttechniker verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="da961-215">For example, your app's "creation flow" utilizes the Hands and tools interaction model, but you want to employ a Hands-free mode for field technicians.</span></span>  

<span data-ttu-id="da961-216">Wenn Ihre Umgebung interaktionsmodelle erforderlich ist, haben wir festgestellt, dass es sich bei viele Endbenutzer um einen Übergang aus einem Modell in ein anderes – insbesondere Benutzer gedacht, die MR schwierigkeiten auftreten können.</span><span class="sxs-lookup"><span data-stu-id="da961-216">If your experience does require multiple interaction models, we've found that many end users may encounter difficulty transitioning from one model to another -- especially end users who are new to MR.</span></span>

> [!Note]
> <span data-ttu-id="da961-217">Damit können die Anleitung-Designern und Entwicklern über Optionen, die in MR schwierig sein können, arbeiten wir an weitere Anleitungen zur Verwendung von interaktionsmodelle.</span><span class="sxs-lookup"><span data-stu-id="da961-217">To help guide designers and developers through choices that can be difficult in MR, we're working on more guidance for using multiple interaction models.</span></span>
 

## <a name="see-also"></a><span data-ttu-id="da961-218">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="da961-218">See also</span></span>
* [<span data-ttu-id="da961-219">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="da961-219">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="da961-220">Direkte Manipulation</span><span class="sxs-lookup"><span data-stu-id="da961-220">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="da961-221">Zeigen und Ausführen</span><span class="sxs-lookup"><span data-stu-id="da961-221">Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="da961-222">Anvisieren</span><span class="sxs-lookup"><span data-stu-id="da961-222">Gaze targeting</span></span>](gaze-targeting.md)
* [<span data-ttu-id="da961-223">Gesten</span><span class="sxs-lookup"><span data-stu-id="da961-223">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="da961-224">Sprachentwurf</span><span class="sxs-lookup"><span data-stu-id="da961-224">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="da961-225">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="da961-225">Motion controllers</span></span>](motion-controllers.md)
* [<span data-ttu-id="da961-226">Raumklangentwurf</span><span class="sxs-lookup"><span data-stu-id="da961-226">Spatial sound design</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="da961-227">Gestaltung von räumlicher Abbildung</span><span class="sxs-lookup"><span data-stu-id="da961-227">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="da961-228">Komfort</span><span class="sxs-lookup"><span data-stu-id="da961-228">Comfort</span></span>](comfort.md)
