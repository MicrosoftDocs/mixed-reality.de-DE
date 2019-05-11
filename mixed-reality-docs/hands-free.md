---
title: Optimieren Ihre app für freisprechgeräte
description: Optimieren Ihre app für freisprechgeräte
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Mixed Reality, physisch, bestaunen, bestaunen Ziel ist, handelt es sich bei Interaktion, Entwurf
ms.openlocfilehash: f39a9524831161997b59be6cf89b124fa5b29c78
ms.sourcegitcommit: d6d96d552ec10cd7e6502fbbc1905432e2878325
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524330"
---
# <a name="optimizing-your-app-for-hands-free"></a><span data-ttu-id="1143d-104">Optimieren Ihre app für freisprechgeräte</span><span class="sxs-lookup"><span data-stu-id="1143d-104">Optimizing your app for hands-free</span></span>



## <a name="scenarios"></a><span data-ttu-id="1143d-105">Szenarien</span><span class="sxs-lookup"><span data-stu-id="1143d-105">Scenarios</span></span>

<span data-ttu-id="1143d-106">Wie in der [Interaktion Modellübersicht](interaction-fundamentals.md), nachdem Sie die Benutzer und ihre Ziele identifiziert haben, Fragen Sie sich, welche Herausforderungen Umwelt- oder Informationen, die sie möglicherweise konfrontiert, wenn sie zum Ausführen ihrer Aufgaben arbeiten.</span><span class="sxs-lookup"><span data-stu-id="1143d-106">As outlined in the [interaction model overview](interaction-fundamentals.md), once you have identified the users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="1143d-107">Beispielsweise müssen viele Benutzer verwenden, wenn sich ihre echten Ziele zu erreichen und schwierigkeiten bei der Interaktion mit der eine Grundlage Hands-und-Controller-Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="1143d-107">For example, many users need to use their hands to accomplish their real-world goals and will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="1143d-108">Unter Umständen einige spezifischen Szenarien:</span><span class="sxs-lookup"><span data-stu-id="1143d-108">Some specific scenarios might be:</span></span> 
* <span data-ttu-id="1143d-109">Durch eine Aufgabe, geführt werden, während Hands ausgelastet sind.</span><span class="sxs-lookup"><span data-stu-id="1143d-109">Being guided through a task, while hands are busy</span></span>
* <span data-ttu-id="1143d-110">Verweisen auf die Materialien, während Sie sich mit der ausgelastet sind.</span><span class="sxs-lookup"><span data-stu-id="1143d-110">Referencing materials while your hands are busy</span></span>
* <span data-ttu-id="1143d-111">Hand-fatigue</span><span class="sxs-lookup"><span data-stu-id="1143d-111">Hand fatigue</span></span>
* <span data-ttu-id="1143d-112">Handschuhe, die nicht überwacht werden können</span><span class="sxs-lookup"><span data-stu-id="1143d-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="1143d-113">Etwas ausführen</span><span class="sxs-lookup"><span data-stu-id="1143d-113">Carrying something</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="1143d-114">Physisch Modalitäten</span><span class="sxs-lookup"><span data-stu-id="1143d-114">Hands-free modalities</span></span>

### <a name="voice-commanding"></a><span data-ttu-id="1143d-115">Voice-Befehle</span><span class="sxs-lookup"><span data-stu-id="1143d-115">Voice commanding</span></span>

<span data-ttu-id="1143d-116">Verwenden Ihre Stimme zum Befehl und Steuerung, die eine Schnittstelle kann nicht nur ermöglicht dem Benutzer, arbeiten Handsfree, aber auch mehrere Schritte überspringen.</span><span class="sxs-lookup"><span data-stu-id="1143d-116">Using your voice to command and control an interface can not only allow the user to operate handsfree, but also skip multiple steps.</span></span> <span data-ttu-id="1143d-117">Die Verwendung dieser Modalität reichen von der Benutzer kann alle diese Schaltfläche einfach zu lesen laut aktivieren, wie finden Sie unter-It-Say-It, um die Konversation mit einem Agent, der Aufgaben für Sie ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="1143d-117">The usage of this modality can range from allowing the user to simply reading any button's name out loud to activate it, as in See-it-say-it, to conversing with an agent who can accomplish tasks for you.</span></span>

* [<span data-ttu-id="1143d-118">Sprachentwurf</span><span class="sxs-lookup"><span data-stu-id="1143d-118">Voice design</span></span>](voice-design.md)


### <a name="head-gaze-and-dwell"></a><span data-ttu-id="1143d-119">Head Blicke und dwell</span><span class="sxs-lookup"><span data-stu-id="1143d-119">Head gaze and dwell</span></span>

<span data-ttu-id="1143d-120">In einigen Situationen physisch ist mit der Stimme nicht ideal oder sogar möglich.</span><span class="sxs-lookup"><span data-stu-id="1143d-120">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="1143d-121">Laut Factoryumgebungen, Datenschutz oder soziale Normen können alle Einschränkungen sein.</span><span class="sxs-lookup"><span data-stu-id="1143d-121">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="1143d-122">Die Kopfzeile bestaunen + länger aufhalten Modell kann der Benutzer die app zu navigieren, indem Sie ihre Head Vektor um zu zeigen, während die veralteten, oder auf eine Schaltfläche Einstichs wird Aktivieren der nach einem bestimmten Zeitraum (in der Regel ca. 1 Sekunde oder so).</span><span class="sxs-lookup"><span data-stu-id="1143d-122">The head gaze + dwell model allows the user to navigate the app by using their head vector to point, while lingering, or dwelling on a button will activate it after a certain amount of time (typically around 1 second or so).</span></span> 

* [<span data-ttu-id="1143d-123">Anvisieren und Verweilen</span><span class="sxs-lookup"><span data-stu-id="1143d-123">Gaze and dwell</span></span>](gaze-and-dwell.md)

## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="1143d-124">Übergang und physisch</span><span class="sxs-lookup"><span data-stu-id="1143d-124">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="1143d-125">Für diese Szenarien können Sie sich von der Interaktion mit Hologramme für Befehle und Navigation freigeben reichen von eine zwingende Voraussetzung nicht erfüllt, die beim Betrieb von End-to-End auf benutzerfreundlichkeit, die der Benutzer zu einem beliebigen Zeitpunkt in und aus der Übergang kann der app wird.</span><span class="sxs-lookup"><span data-stu-id="1143d-125">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the app, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="1143d-126">Wenn die Anforderung der app ist, dass er immer ohne Benutzereingriff, verwendet wird, ob mithilfe Dwell, Sprachbefehle, oder die einzigen Sprachbefehl, "select", und dann stellen Sie sicher, dass die entsprechenden für Unterkünfte in Ihrer Benutzeroberfläche vornehmen.</span><span class="sxs-lookup"><span data-stu-id="1143d-126">If the requirement of the app is that it will always be used hands-free, whether by using dwell, voice commands, or the single voice command, "select", then make sure to make the appropriate accomodations in your UI.</span></span> 

<span data-ttu-id="1143d-127">Wenn sich der Zielbenutzer von Hand zu physisch am nach eigenem Ermessen wechseln können muss, ist es wichtig, diese Prinzipien berücksichtigen:</span><span class="sxs-lookup"><span data-stu-id="1143d-127">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take these principles into account:</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="1143d-128">Wird davon ausgegangen Sie, dass der Benutzer bereits in den Modus, der sie wechseln möchten.</span><span class="sxs-lookup"><span data-stu-id="1143d-128">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="1143d-129">Z. B. wenn der Benutzer am Herstellerstandort ist, einen video Verweis auf ihr Hololens, überwachen und entscheidet, um ein Schraubenschlüsselsymbol zu übernehmen, um zu arbeiten, möchte in den meisten Fällen sie mit der Arbeit in Handsfree ohne versetzt, das Schraubenschlüsselsymbol drücken eine Schaltfläche beginnen.</span><span class="sxs-lookup"><span data-stu-id="1143d-129">For instance, if your user is on the factory floor, watching a video reference on her Hololens, and decides to pick up a wrench to start working, she most likely would like to begin working in handsfree without having to put down the wrench to press a button.</span></span> <span data-ttu-id="1143d-130">Sie sollten eine Voice-Sitzung mit einem Voice-Befehl aufrufen, werden für bereits sichtbare Benutzeroberfläche auf Dwell beginnen länger aufhalten Lage sein, oder z. B. das Wort "select".</span><span class="sxs-lookup"><span data-stu-id="1143d-130">She should be able to invoke a voice session with a voice command, dwell on already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="1143d-131">Der Benutzer muss die Möglichkeit, verfügen:</span><span class="sxs-lookup"><span data-stu-id="1143d-131">The user should have the ability to:</span></span> 
* <span data-ttu-id="1143d-132">Wechseln Sie zur Handsfree beim handsfree</span><span class="sxs-lookup"><span data-stu-id="1143d-132">Switch to handsfree while handsfree</span></span>
* <span data-ttu-id="1143d-133">Wechseln Sie zur Hand, mit der Hand</span><span class="sxs-lookup"><span data-stu-id="1143d-133">Switch to hands with your hands</span></span>
* <span data-ttu-id="1143d-134">Wechseln Sie zu dem Controller mithilfe eines Controllers</span><span class="sxs-lookup"><span data-stu-id="1143d-134">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="1143d-135">Erstellen Sie redundante Möglichkeiten, die für einen Moduswechsel</span><span class="sxs-lookup"><span data-stu-id="1143d-135">Create redundant ways to switch modes</span></span>
<span data-ttu-id="1143d-136">Während das vorherrschende Prinzip bei Zugriff ist, ist der zweite über die Verfügbarkeit.</span><span class="sxs-lookup"><span data-stu-id="1143d-136">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="1143d-137">Es sollten nur keine einzelne Möglichkeit für den Übergang in einen Modus.</span><span class="sxs-lookup"><span data-stu-id="1143d-137">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="1143d-138">Einige Beispiele für würde folgendermaßen lauten:</span><span class="sxs-lookup"><span data-stu-id="1143d-138">Some examples would be:</span></span> 
* <span data-ttu-id="1143d-139">Eine Schaltfläche, um die sprachliche Interaktionen zu beginnen</span><span class="sxs-lookup"><span data-stu-id="1143d-139">A button to begin voice interactions</span></span>
* <span data-ttu-id="1143d-140">Einen Sprachbefehl für den Übergang zur Verwendung von Blicke + dwell</span><span class="sxs-lookup"><span data-stu-id="1143d-140">A voice command to transition to using gaze + dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="1143d-141">Fügen Sie ein wenig vom Drama hinzu.</span><span class="sxs-lookup"><span data-stu-id="1143d-141">Add a dash of drama</span></span>
<span data-ttu-id="1143d-142">Einen Moduswechsel ist sehr aufwendig – es ist wichtig, die auftreten, wenn diese Übergänge, die, dass sie sich einen expliziten, sogar erhebliche-Switch, damit der Benutzer wissen, was passiert ist.</span><span class="sxs-lookup"><span data-stu-id="1143d-142">A mode switch is a big deal -- it is important that when these transitions happen, that they be an explicit, even dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="1143d-143">Checkliste für die benutzerfreundlichkeit</span><span class="sxs-lookup"><span data-stu-id="1143d-143">Usability checklist</span></span>

<span data-ttu-id="1143d-144">**Möglich der Benutzer alles und jedes physisch, End-to-End-alles?**</span><span class="sxs-lookup"><span data-stu-id="1143d-144">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="1143d-145">Jede interactible zugänglich physisch sein sollen</span><span class="sxs-lookup"><span data-stu-id="1143d-145">Every interactible should be accessible hands-free</span></span>
* <span data-ttu-id="1143d-146">Stellen Sie sicher, dass ein Ersatz für alle benutzerdefinierten stiftbewegungen, z. B. Ändern der Größe, platzieren, Kundenkarte, tippen usw. vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="1143d-146">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="1143d-147">Stellen Sie sicher, dass der Benutzer davon überzeugt Steuerelement der Benutzeroberfläche vorhanden, Platzierung, Ausführlichkeit jederzeit verfügt</span><span class="sxs-lookup"><span data-stu-id="1143d-147">Ensure that the user has confident control of UI presence, placement, verbosity at all times</span></span>
    * <span data-ttu-id="1143d-148">Abrufen von UI aus dem Weg</span><span class="sxs-lookup"><span data-stu-id="1143d-148">Getting UI out of the way</span></span>
    * <span data-ttu-id="1143d-149">Behandeln von Benutzeroberfläche, die außerhalb des Sichtfelds (Blickfeld) liegt</span><span class="sxs-lookup"><span data-stu-id="1143d-149">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="1143d-150">Wie viel angezeigt, wobei bei</span><span class="sxs-lookup"><span data-stu-id="1143d-150">How much I see, where, when</span></span>

<span data-ttu-id="1143d-151">**Sind die Mechanismen der Interaktion eines und Kopplung mit dem richtigen visueller Hinweise werden?**</span><span class="sxs-lookup"><span data-stu-id="1143d-151">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="1143d-152">Der Benutzer ist versteht...</span><span class="sxs-lookup"><span data-stu-id="1143d-152">Does the user understand ...</span></span>
* <span data-ttu-id="1143d-153">... Modus sind sie in?</span><span class="sxs-lookup"><span data-stu-id="1143d-153">... What mode they are in?</span></span>
* <span data-ttu-id="1143d-154">... Welche Möglichkeiten sie in diesem Modus?</span><span class="sxs-lookup"><span data-stu-id="1143d-154">... What they can do in this mode?</span></span>
* <span data-ttu-id="1143d-155">... Was ist der aktuelle Zustand?</span><span class="sxs-lookup"><span data-stu-id="1143d-155">... What is the current state?</span></span>
* <span data-ttu-id="1143d-156">... Wie können sie sich wechseln?</span><span class="sxs-lookup"><span data-stu-id="1143d-156">... How they can transition out?</span></span>
    
<span data-ttu-id="1143d-157">**Ist die Benutzeroberfläche für freisprechgeräte optimiert?**</span><span class="sxs-lookup"><span data-stu-id="1143d-157">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="1143d-158">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="1143d-158">Ex.</span></span> <span data-ttu-id="1143d-159">Dwell visueller Hinweise sind nicht in typischen 2D Muster integriert</span><span class="sxs-lookup"><span data-stu-id="1143d-159">Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="1143d-160">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="1143d-160">Ex.</span></span> <span data-ttu-id="1143d-161">Für die Zielgruppenadressierung von Voice ist besser mit Hervorhebung von Objekt</span><span class="sxs-lookup"><span data-stu-id="1143d-161">Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="1143d-162">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="1143d-162">Ex.</span></span> <span data-ttu-id="1143d-163">Sprachliche Interaktionen sind besser mit Beschriftungen, die aktiviert werden müssen</span><span class="sxs-lookup"><span data-stu-id="1143d-163">Voice interactions are better with captions that have to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="1143d-164">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1143d-164">See also</span></span>
* [<span data-ttu-id="1143d-165">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="1143d-165">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="1143d-166">Direkte Manipulation</span><span class="sxs-lookup"><span data-stu-id="1143d-166">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="1143d-167">Zeigen und Ausführen</span><span class="sxs-lookup"><span data-stu-id="1143d-167">Point and commit</span></span>](point-and-commit.md)
