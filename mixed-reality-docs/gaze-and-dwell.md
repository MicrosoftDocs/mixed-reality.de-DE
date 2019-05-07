---
title: Blicke und dwell
description: Übersicht über das Eingabemodell Blicke und dwell
author: liamartinez
ms.author: liamar
ms.date: 03/31/2019
ms.topic: article
keywords: Gemischte Realität Blicke, Dwell, Interaktion, Entwerfen
ms.openlocfilehash: a50ae948a351f5152ebb98778da9be8c08090d72
ms.sourcegitcommit: 222cba2d622b47f75949bf8af80d5c62de4dceab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2019
ms.locfileid: "64914610"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="0eb3c-104">Blicke und dwell</span><span class="sxs-lookup"><span data-stu-id="0eb3c-104">Gaze and dwell</span></span>

<span data-ttu-id="0eb3c-105">Wenn praktische Tools und Komponenten belegt sind, können die Gesten mühsam oder unmöglich sein.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span>  <span data-ttu-id="0eb3c-106">Sprachbefehle, z. B. Geste können können in bestimmten Situationen unzuverlässig ist, z. B. übermäßig laut ausgelastet sein.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-106">Voice commands, like gesture, can be situationally unreliable, for example under excessively loud conditions.</span></span>  <span data-ttu-id="0eb3c-107">Darüber hinaus Stimme, die Control-Computer ist nicht noch eine grundlegende Interaktion, jedoch ist sicherlich Datenstrom gewinnen!</span><span class="sxs-lookup"><span data-stu-id="0eb3c-107">Additionally, using voice to control computers isn't a mainstream interaction yet, but it certainly is gaining steam!</span></span>  <span data-ttu-id="0eb3c-108">Blicke Dwell bietet den meistverwendeten und einfachen Master-Mechanismus für die Arbeit Heads-Up physisch auf HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-108">Gaze dwell offers the most familiar and easy-to-master mechanism for working heads-up hands-free on HoloLens.</span></span>  <span data-ttu-id="0eb3c-109">Darüber hinaus Blicke Dwell 100-prozentige Zuverlässigkeit ist unabhängig von Rauschen Störungen noch Ruhe-Einschränkungen in der betriebsumgebung.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-109">Additionally, gaze dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="goals"></a><span data-ttu-id="0eb3c-110">Ziele</span><span class="sxs-lookup"><span data-stu-id="0eb3c-110">Goals</span></span>

<span data-ttu-id="0eb3c-111">Geben Sie einen Mechanismus für die vollständige freisprechgeräte Interaktionen, ohne per Spracheingabe.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-111">Provide a mechanism for full hands-free interactions, without using Voice.</span></span>

## <a name="design-principles"></a><span data-ttu-id="0eb3c-112">Designprinzipien</span><span class="sxs-lookup"><span data-stu-id="0eb3c-112">Design principles</span></span>

1. <span data-ttu-id="0eb3c-113">Es ist kein Blicke Waffe</span><span class="sxs-lookup"><span data-stu-id="0eb3c-113">Gaze is not a weapon</span></span>
    
    <span data-ttu-id="0eb3c-114">Blicke erfordert visuelles Feedback für die intuitive Interaktion, aber viel Feedback kann hegen auslösen.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-114">Gaze requires visual feedback for intuitive interaction, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="0eb3c-115">Das Feedback tragen, dass einen Benutzer wissen, was sie, aber keine automatische Auswahl für ihre Absichten als Ziel verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-115">The feedback should help a user know what they're targeting, but not auto-select against their intent.</span></span> <span data-ttu-id="0eb3c-116">Lesen von Text erfordert zusätzlich zu einem Benutzer Raum um die Informationen vor der Auswahl der absorb ist zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-116">Reading text requires extra consideration to provide a user room to absorb the info before selecting.</span></span>
    
2. <span data-ttu-id="0eb3c-117">Seek-Goldlöckchen Geschwindigkeit</span><span class="sxs-lookup"><span data-stu-id="0eb3c-117">Seek Goldilocks speed</span></span>
    
    <span data-ttu-id="0eb3c-118">Die Füllung Dwell haben verschiedene Zeitgeber, die basierend auf Auswirkung der Navigation – häufig verwendete Funktionen profitieren davon, in der Regel schnellere ausfüllen, während mehr Fill-Mal mehr Folgeschäden Funktionen profitieren können.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-118">The dwell fill can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="0eb3c-119">Animation-Kurven der Füllfarbe können einen Eindruck, schnellere Füllung werde, positiv beeinflussen.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-119">Animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="0eb3c-120">Berücksichtigt sind, um die Entscheidung des Benutzers aus Fast/Mittel/langsame aktivieren Geschwindigkeit Außerkraftsetzungen zu füllen.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-120">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
3. <span data-ttu-id="0eb3c-121">Sagen Sie forschungspseudocode zu Yo-yo Auswirkung</span><span class="sxs-lookup"><span data-stu-id="0eb3c-121">Say no-no to yo-yo effect</span></span>

    <span data-ttu-id="0eb3c-122">Die Yo-yo Auswirkung (auch bekannt als "nachts auf die Roxbury") ist ein unbequem Muster, die aus der bestimmten Platzierung von Inhalt und Blicke-basierten Steuerelementen auf den Markt kommen kann.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-122">The yo-yo effect (also known as "Night at the Roxbury") is an uncomfortable pattern that can emerge from certain  placement of content and gaze-based controls.</span></span> <span data-ttu-id="0eb3c-123">Eine Liste Navigationsbereich mit der Fill-Schaltfläche am unteren Rand werden z. B. eine Schleife von - Suchen nach unten länger aufhalten, Ergebnisse suchen, suchen Sie nach unten Dwell usw. ausgelöst. Dieses resultierende Muster unangenehm ist, und sollte vermieden werden, indem Sie die Navigationssteuerelemente an einem zentralen Ort, der kleiner hin und her erfordert platzieren.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-123">For example, a list nav with the fill button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="0eb3c-124">Platzierung von Dwell Schaltflächen relativ zu deren Auswirkungen wichtig für Komfort.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-124">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

## <a name="ui-patterns"></a><span data-ttu-id="0eb3c-125">UI-Muster</span><span class="sxs-lookup"><span data-stu-id="0eb3c-125">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="0eb3c-126">Hohe Auslastung Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="0eb3c-126">High frequency buttons</span></span>
    
* <span data-ttu-id="0eb3c-127">Nächste/Back-Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="0eb3c-127">Next/Back buttons</span></span>
  * <span data-ttu-id="0eb3c-128">Sehr kurze Verzögerung vor füllen (Flyover Flimmern Puffer)</span><span class="sxs-lookup"><span data-stu-id="0eb3c-128">Very short delay pre-fill (flyover flicker buffer)</span></span>
  * <span data-ttu-id="0eb3c-129">Größere Schaltflächen sind leichter zu bedienen mit Blicke</span><span class="sxs-lookup"><span data-stu-id="0eb3c-129">Larger buttons are easier to hit with gaze</span></span>
  * <span data-ttu-id="0eb3c-130">Gut, die unter die Augen Höhe behalten Sie also keinen Hinweis auf die Belastung für die Interaktion</span><span class="sxs-lookup"><span data-stu-id="0eb3c-130">Nice to keep these at eye height so no strain to interact</span></span>
  * <span data-ttu-id="0eb3c-131">Dwell Region kann größer als inaktiv Symbol zu erleichtern (zurück) zu verwenden sein.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-131">Dwell region can be larger than inactive icon to make it easier to use (BACK)</span></span>

### <a name="low-frequency-buttons"></a><span data-ttu-id="0eb3c-132">Niedrige Auslastung von Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="0eb3c-132">Low frequency buttons</span></span>
    
* <span data-ttu-id="0eb3c-133">Menü "Einstellungen" aktivieren</span><span class="sxs-lookup"><span data-stu-id="0eb3c-133">Activate settings menu</span></span>
  * <span data-ttu-id="0eb3c-134">Mehr Verzögerung vor Füllung OK (Flyover Flimmern Puffer)</span><span class="sxs-lookup"><span data-stu-id="0eb3c-134">Longer delay pre-fill okay (flyover flicker buffer)</span></span>
  * <span data-ttu-id="0eb3c-135">Versuche, diese Schaltflächen Bildschirmen häufig Cursor Wege zu halten.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-135">Try to keep these buttons out of the way of frequent cursor pathways</span></span>

* <span data-ttu-id="0eb3c-136">Bestätigungen (d. h. Überprüfung Flow, Dialogfelder)</span><span class="sxs-lookup"><span data-stu-id="0eb3c-136">Confirmations (i.e. scan flow, dialogs)</span></span>
  * <span data-ttu-id="0eb3c-137">Markierung der auf Hauptschaltfläche anzeigen</span><span class="sxs-lookup"><span data-stu-id="0eb3c-137">Show selection highlight on main button</span></span>
  * <span data-ttu-id="0eb3c-138">Anzeigen von länger aufhalten Ziel gleichzeitig Auswahl hervorheben</span><span class="sxs-lookup"><span data-stu-id="0eb3c-138">Reveal dwell target at same time as selection highlight</span></span>
  * <span data-ttu-id="0eb3c-139">Verwendung länger aufhalten Ziel im Zusammenhang mit Symbol, um die Benutzeroberfläche einfach zu halten</span><span class="sxs-lookup"><span data-stu-id="0eb3c-139">Use dwell target surrounding icon to keep interface simple</span></span>
  * <span data-ttu-id="0eb3c-140">Wichtige Entscheidung, damit keine Hervorhebung zu aktivieren, werden Dwell Ziel für eine nochmalige Überlegung Zeitraum angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-140">Important decision, so highlight doesn't activate, reveals dwell target for reconsideration time</span></span>
        
### <a name="toggle-buttons"></a><span data-ttu-id="0eb3c-141">Umschaltflächen</span><span class="sxs-lookup"><span data-stu-id="0eb3c-141">Toggle buttons</span></span>

* <span data-ttu-id="0eb3c-142">Pin</span><span class="sxs-lookup"><span data-stu-id="0eb3c-142">Pin</span></span>
  * <span data-ttu-id="0eb3c-143">Clear aktiver/inaktiver visuellen Zustand</span><span class="sxs-lookup"><span data-stu-id="0eb3c-143">Clear active/inactive visual state</span></span>
  * <span data-ttu-id="0eb3c-144">Radiale Füllung hilft Benutzer, den Fokus und natürliche Status angezeigt</span><span class="sxs-lookup"><span data-stu-id="0eb3c-144">Radial fill helps focus user and provides natural progress</span></span> 

* <span data-ttu-id="0eb3c-145">Individuelle Einstellungen</span><span class="sxs-lookup"><span data-stu-id="0eb3c-145">Individual settings</span></span>
  * <span data-ttu-id="0eb3c-146">Clear aktiven/inaktiven Status</span><span class="sxs-lookup"><span data-stu-id="0eb3c-146">Clear active/inactive states</span></span>
  * <span data-ttu-id="0eb3c-147">Länger aufhalten Sie Zielen alle auf der linken umgebenden-Symbol</span><span class="sxs-lookup"><span data-stu-id="0eb3c-147">Dwell targets all on left surrounding icon</span></span>
  * <span data-ttu-id="0eb3c-148">Dwell ausgerichtet ist, nur erscheinen, bei der Auswahl aktiv markieren</span><span class="sxs-lookup"><span data-stu-id="0eb3c-148">Dwell targets only show up when selection highlight active</span></span>
  * <span data-ttu-id="0eb3c-149">"Länger aufhalten Schieberegler" rechts für ein-und Einstellungen</span><span class="sxs-lookup"><span data-stu-id="0eb3c-149">"Dwell on slider" on right side for on/off settings</span></span>

### <a name="list-views"></a><span data-ttu-id="0eb3c-150">Listenansichten</span><span class="sxs-lookup"><span data-stu-id="0eb3c-150">List views</span></span>

* <span data-ttu-id="0eb3c-151">Browsen Listenansicht - Guide-Dateien zu öffnen</span><span class="sxs-lookup"><span data-stu-id="0eb3c-151">Browsing list view - guide files to open</span></span>
  * <span data-ttu-id="0eb3c-152">Cursor-Highlights Zeile aus an einer beliebigen Stelle in Zeile aber Dwell beginnt nicht</span><span class="sxs-lookup"><span data-stu-id="0eb3c-152">Cursor highlights row from anywhere on row but doesn’t begin dwell</span></span>
  * <span data-ttu-id="0eb3c-153">Wenn Zeilen vom Cursor markiert ist, wird angezeigt, Dwell Ziel links</span><span class="sxs-lookup"><span data-stu-id="0eb3c-153">When row is highlighted by cursor, dwell target appears on left</span></span>
  * <span data-ttu-id="0eb3c-154">Länger aufhalten Sie Ziel immer ein Kreis auf der linken Seite des Textes in allen Listenansichten</span><span class="sxs-lookup"><span data-stu-id="0eb3c-154">Dwell target always a circle on left side of text in all list views</span></span>
  * <span data-ttu-id="0eb3c-155">Zeigen Sie nicht mehr an, dass alle Ziele auf einmal zur Vermeidung von Benutzeroberfläche länger aufhalten</span><span class="sxs-lookup"><span data-stu-id="0eb3c-155">Don't show all dwell targets at once to avoid repetitive UI</span></span>
  * <span data-ttu-id="0eb3c-156">Nutzen Sie das gleiche Muster zum Einrichten von UX-Kenntnisse</span><span class="sxs-lookup"><span data-stu-id="0eb3c-156">Re-use the same pattern to establish UX familiarity</span></span>
        
* <span data-ttu-id="0eb3c-157">Listenansicht - Hierarchie der Aufgaben/Schritte im Leitfaden durchsuchen</span><span class="sxs-lookup"><span data-stu-id="0eb3c-157">Browsing list view - hierarchy of tasks/steps in a guide</span></span>
  * <span data-ttu-id="0eb3c-158">Länger aufhalten Sie Ziel immer ein Kreis auf der linken Seite des Textes</span><span class="sxs-lookup"><span data-stu-id="0eb3c-158">Dwell target always a circle on left side of text</span></span>
  * <span data-ttu-id="0eb3c-159">Reduzieren/Erweitern länger Unterstützung aufhalten.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-159">Collapse/expand dwell affordance</span></span>
        
* <span data-ttu-id="0eb3c-160">Listenansicht Durchsuchen - Modus auswählen</span><span class="sxs-lookup"><span data-stu-id="0eb3c-160">Browsing list view - mode select</span></span>
  * <span data-ttu-id="0eb3c-161">Verwenden Sie die Muster, die über hergestellt</span><span class="sxs-lookup"><span data-stu-id="0eb3c-161">Follow patterns established above</span></span>

### <a name="contextual-buttons"></a><span data-ttu-id="0eb3c-162">Kontextbezogene Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="0eb3c-162">Contextual buttons</span></span>

* <span data-ttu-id="0eb3c-163">Ein-/3D - zeigt sich in 3D entlang Objektivdeckel in der Nähe Hologramme</span><span class="sxs-lookup"><span data-stu-id="0eb3c-163">Show/Hide 3D - shows up in 3D along tether near holograms</span></span> 
  * <span data-ttu-id="0eb3c-164">Clear aktiver/inaktiver visuellen Zustand</span><span class="sxs-lookup"><span data-stu-id="0eb3c-164">Clear active/inactive visual state</span></span>

### <a name="pivots"></a><span data-ttu-id="0eb3c-165">Pivots</span><span class="sxs-lookup"><span data-stu-id="0eb3c-165">Pivots</span></span>

* <span data-ttu-id="0eb3c-166">Liste der zuletzt Choice-oder All-Handbücher</span><span class="sxs-lookup"><span data-stu-id="0eb3c-166">Recent/All guides list</span></span>
  * <span data-ttu-id="0eb3c-167">Geben Sie die UI-Unterstützung, die verbleibt, um anzugeben, welcher Registerkarte aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-167">Fill the UI affordance that remains to indicate which tab is active</span></span>
  * <span data-ttu-id="0eb3c-168">Für kurze Worts Pivots ausgewählt haben wir auf das Dwell Ziel-Muster zu verzichten</span><span class="sxs-lookup"><span data-stu-id="0eb3c-168">For short single word pivots, we elected to forego the dwell target pattern</span></span>
  * <span data-ttu-id="0eb3c-169">Wir sitzungsauthentifizierungsmodul bevorzugt die vereinfachte Schnittstelle eine andere 2 Kreis Ziele und eine größere Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="0eb3c-169">We favored the simplified interface over another 2 circle targets and a wider UI</span></span>
  * <span data-ttu-id="0eb3c-170">In diesem Fall werden die Wörter kurz genug, dass eine Verzögerung genügend bequem vor dem Ausfüllen bereitstellt</span><span class="sxs-lookup"><span data-stu-id="0eb3c-170">In our case, the words are short enough that a delay provides enough comfort before filling</span></span>


## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="0eb3c-171">UX-Richtlinien und bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="0eb3c-171">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="0eb3c-172">Zielgrößen</span><span class="sxs-lookup"><span data-stu-id="0eb3c-172">Target sizes</span></span>

  * <span data-ttu-id="0eb3c-173">Minimale Größe des Pin-Symbol: 6cm im Raum der Welt in Unity 30 MRUs (30cm @ 2m)</span><span class="sxs-lookup"><span data-stu-id="0eb3c-173">Pin icon minimum size: 6cm in world space in Unity, 30 MRUs ( 30cm @ 2m)</span></span>
  * <span data-ttu-id="0eb3c-174">Gibt die Ziele, die "magnetisiert" oder "dauerhaft" überhaupt?</span><span class="sxs-lookup"><span data-stu-id="0eb3c-174">Are the targets "magnetized" or "sticky" at all?</span></span> <span data-ttu-id="0eb3c-175">(d. h. bestaunen Cursor Glättung)</span><span class="sxs-lookup"><span data-stu-id="0eb3c-175">(i.e. gaze cursor smoothing)</span></span>

### <a name="animation"></a><span data-ttu-id="0eb3c-176">Animation</span><span class="sxs-lookup"><span data-stu-id="0eb3c-176">Animation</span></span>

  * <span data-ttu-id="0eb3c-177">Verzögerung vor Dwell visual Trigger .5sec</span><span class="sxs-lookup"><span data-stu-id="0eb3c-177">Delay before dwell visual triggers .5sec</span></span>
  * <span data-ttu-id="0eb3c-178">Dauer der Dwell Visual 1,2 s</span><span class="sxs-lookup"><span data-stu-id="0eb3c-178">Duration of dwell visual 1.2sec</span></span>
  * <span data-ttu-id="0eb3c-179">Die Kurve für Animation?</span><span class="sxs-lookup"><span data-stu-id="0eb3c-179">Curve on animation?</span></span>

### <a name="visual-feedback"></a><span data-ttu-id="0eb3c-180">Visuelles Feedback</span><span class="sxs-lookup"><span data-stu-id="0eb3c-180">Visual feedback</span></span>

  * <span data-ttu-id="0eb3c-181">Radiale Füllen von Blicke Start Cursorposition</span><span class="sxs-lookup"><span data-stu-id="0eb3c-181">Radial fill from gaze cursor start location</span></span>
  * <span data-ttu-id="0eb3c-182">Immer radiale Füllung aus der Mitte der Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-182">Always radial fill from center of button.</span></span> <span data-ttu-id="0eb3c-183">Eine konsistente Antwort ist weniger verwirrend, als alle anderen Anweisungen für verschiedene Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-183">A consistent response is less confusing than all different directions on different buttons.</span></span> 
    * <span data-ttu-id="0eb3c-184">Mit dieser Regel kann jedoch für den direktionalen Interaktionen (z. B. Nav nach-oben/nach unten/links/rechts, usw.) unterbrochen werden.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-184">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="0eb3c-185">Z. B. rechts Anleitungen wird eine Ausnahme auf die nächste/BACK verlassene gefüllt.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-185">For example, Guides makes an exception on NEXT/BACK being left right fills.</span></span>
    * <span data-ttu-id="0eb3c-186">Betrachten Sie Invertieren von radialen Füllen von außerhalb (bei off umschalten) aus.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-186">Consider inverting radial fill from outside (if toggling off).</span></span> <span data-ttu-id="0eb3c-187">Die inverse Eindruck, eine Schaltfläche ist ein praktisches visual Muster zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="0eb3c-187">THe inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="0eb3c-188">Schrittweise Anzeige von</span><span class="sxs-lookup"><span data-stu-id="0eb3c-188">Progressive Disclosure</span></span>

 * <span data-ttu-id="0eb3c-189">Schrittweise Anzeige von bedeutet, dass das Ziel Dwell Hervorhebung (z. B. in einem Listensteuerelement) angezeigt wird</span><span class="sxs-lookup"><span data-stu-id="0eb3c-189">Progressive disclosure means that the dwell target is revealed on highlight (e.g., in a list control)</span></span>
 * <span data-ttu-id="0eb3c-190">Highlights von Text-Leiste mit Spotlight anzuzeigen auf Blicke an einer beliebigen Stelle auf text</span><span class="sxs-lookup"><span data-stu-id="0eb3c-190">Text bar highlights with spotlight reveal on gaze anywhere on text</span></span>
 * <span data-ttu-id="0eb3c-191">Blicke Füllung Ziel wird immer angezeigt, auf der linken Seite, jedoch nur für das Element der Liste die hervorgehoben ist</span><span class="sxs-lookup"><span data-stu-id="0eb3c-191">Gaze fill target appears always on left, but only for the list item which is highlighted</span></span>
 * <span data-ttu-id="0eb3c-192">Versuchen Sie es, um zu vermeiden, dass alle Dwell Ziele auf jederzeit aufgrund eines wiederholten Aussehen des gestapelten Kreise</span><span class="sxs-lookup"><span data-stu-id="0eb3c-192">Try to avoid having all dwell targets on at all times due to repetitive look of stacked circles</span></span>
 
 ## <a name="see-also"></a><span data-ttu-id="0eb3c-193">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0eb3c-193">See also</span></span>
* [<span data-ttu-id="0eb3c-194">Direkte Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="0eb3c-194">Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="0eb3c-195">Punkt- und commit</span><span class="sxs-lookup"><span data-stu-id="0eb3c-195">Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="0eb3c-196">Interaktionsgrundlagen</span><span class="sxs-lookup"><span data-stu-id="0eb3c-196">Interaction fundamentals</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="0eb3c-197">Head-Blicke und commit</span><span class="sxs-lookup"><span data-stu-id="0eb3c-197">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="0eb3c-198">Blicke und Sprache</span><span class="sxs-lookup"><span data-stu-id="0eb3c-198">Gaze and voice</span></span>](voice-design.md)
