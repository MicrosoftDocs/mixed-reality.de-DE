---
title: Blick und Commit
description: 'Allgemeine Übersicht über das Eingabe Modell "Blick und Commit": mithilfe von "Eye" oder "Head Input".'
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Gemischte Realität, Blick, Blick auf die Ausrichtung, Interaktion, Entwurf, Eye Tracking, Head Tracking
ms.openlocfilehash: df152f6a3a6e4ae2d6c32a0c56fbb615bcfa7aa8
ms.sourcegitcommit: a5dc182da237f63f0487d40a2e11894027208b6c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2019
ms.locfileid: "73441129"
---
# <a name="gaze-and-commit"></a><span data-ttu-id="e3e50-104">Blick und Commit</span><span class="sxs-lookup"><span data-stu-id="e3e50-104">Gaze and commit</span></span>

<span data-ttu-id="e3e50-105">" _Blick" und "Commit_ " ist ein grundlegendes Eingabe Modell, das eng mit der Interaktion mit unseren Computern verknüpft ist. verwenden Sie dazu die Maus: Punkt- _& Klicken_.</span><span class="sxs-lookup"><span data-stu-id="e3e50-105">_Gaze and commit_ is a fundamental input model that is closely related with the way we're interacting with our computers using the mouse: _Point & click_.</span></span>
<span data-ttu-id="e3e50-106">Auf dieser Seite stellen wir zwei Arten von Blick Eingaben (Head-and-Eye-Eye) und verschiedene Typen von COMMIT-Aktionen vor.</span><span class="sxs-lookup"><span data-stu-id="e3e50-106">On this page, we introduce two types of gaze input (head- and eye-gaze) and different types of commit actions.</span></span> 
<span data-ttu-id="e3e50-107">Der _Blick und der Commit_ werden als ein weit reichtes Eingabe Modell mit indirekter Bearbeitung betrachtet.</span><span class="sxs-lookup"><span data-stu-id="e3e50-107">_Gaze and commit_ is considered a far input model with indirect manipulation.</span></span>
<span data-ttu-id="e3e50-108">Dies bedeutet, dass Sie am besten für die Interaktion mit Holographic-Inhalten verwendet werden kann, die nicht erreichbar sind.</span><span class="sxs-lookup"><span data-stu-id="e3e50-108">This means it is best used for interacting with holographic content that is out of reach.</span></span>

<span data-ttu-id="e3e50-109">Gemischte Reality-Headsets können die Position und Ausrichtung des Benutzer Kopfes verwenden, um den Kopf Richtung Vektor zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="e3e50-109">Mixed reality headsets can use the position and orientation of the user's head to determine their head direction vector.</span></span> <span data-ttu-id="e3e50-110">Sie können sich dies als einen Laser vorstellen, der direkt zwischen den Augen des Benutzers geradeaus zeigt.</span><span class="sxs-lookup"><span data-stu-id="e3e50-110">You can think of this as a laser that points straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="e3e50-111">Dies ist eine ziemlich grobe Annäherung hinsichtlich der Position, die der Benutzer betrachtet.</span><span class="sxs-lookup"><span data-stu-id="e3e50-111">This is a fairly coarse approximation of where the user is looking.</span></span> <span data-ttu-id="e3e50-112">Die Anwendung kann diesen Strahl mit virtuellen oder echten Objekten überschneiden und einen Cursor an dieser Stelle zeichnen, um dem Benutzer mitzuteilen, was er derzeit als Ziel verwendet.</span><span class="sxs-lookup"><span data-stu-id="e3e50-112">Your application can intersect this ray with virtual or real-world objects, and draw a cursor at that location to let the user know what they are currently targeting.</span></span>

<span data-ttu-id="e3e50-113">Zusätzlich zu den Köpfen können einige gemischte Reality-Headsets, wie hololens 2, Eye Tracking-Systeme einschließen, die einen Blick Vektor liefern.</span><span class="sxs-lookup"><span data-stu-id="e3e50-113">In addition to head gaze, some mixed reality headsets, such as HoloLens 2, include eye tracking systems that produce an eye-gaze vector.</span></span> <span data-ttu-id="e3e50-114">Dies ermöglicht eine präzisere Messung der Position, die der Benutzer betrachtet.</span><span class="sxs-lookup"><span data-stu-id="e3e50-114">This provides a fine-grained measurement of where the user is looking.</span></span> <span data-ttu-id="e3e50-115">In beiden Fällen stellt der Blick ein wichtiges Signal für die Absicht des Benutzers dar.</span><span class="sxs-lookup"><span data-stu-id="e3e50-115">In both cases, the gaze represents an important signal for the user's intent.</span></span> <span data-ttu-id="e3e50-116">Umso besser kann das System die beabsichtigten Aktionen des Benutzers interpretieren und Vorhersagen, die Benutzer Zufriedenheit nimmt zu, und die Leistung wird verbessert.</span><span class="sxs-lookup"><span data-stu-id="e3e50-116">The better the system can interpret and predict the user's intended actions, user satisfaction increases and performance improves.</span></span>

<span data-ttu-id="e3e50-117">Im folgenden finden Sie einige Beispiele für die Art und Weise, wie Sie als Entwickler mit gemischter Realität von der Kopf-oder dem Augenblick profitieren können:</span><span class="sxs-lookup"><span data-stu-id="e3e50-117">Below are a few examples for how you as a mixed reality developer can benefit from head- or eye-gaze:</span></span>
* <span data-ttu-id="e3e50-118">Ihre APP kann den Blick mit den holograms in Ihrer Szene überschneiden, um zu bestimmen, an welcher Stelle die Aufmerksamkeit des Benutzers (genauer mit dem Augenblick) liegt.</span><span class="sxs-lookup"><span data-stu-id="e3e50-118">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is (more precise with eye-gaze).</span></span>
* <span data-ttu-id="e3e50-119">Ihre APP kann Gesten und Controller-Pressen basierend auf dem Blick des Benutzers leiten, sodass der Benutzer nahtlos auf seine Hologramme zugreifen, Sie aktivieren, einlesen, Scrollen oder anderweitig interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="e3e50-119">Your app can channel gestures and controller presses based on the user's gaze, letting the user seamlessly select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="e3e50-120">Ihre APP ermöglicht dem Benutzer das Platzieren von holograms auf realen Oberflächen, indem er seinen Blick Strahl mit dem räumlichen Mapping-Gitter schneidet.</span><span class="sxs-lookup"><span data-stu-id="e3e50-120">Your app can let the user place holograms on real-world surfaces by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="e3e50-121">Ihre APP kann wissen, wenn der Benutzer *nicht* in der Richtung eines wichtigen Objekts sucht, was dazu führen kann, dass Ihre APP visuelle und Audiohinweise zum Umwandeln des Objekts erhält.</span><span class="sxs-lookup"><span data-stu-id="e3e50-121">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

<br>


## <a name="device-support"></a><span data-ttu-id="e3e50-122">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="e3e50-122">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="e3e50-123"><strong>Eingabemodell</strong></span><span class="sxs-lookup"><span data-stu-id="e3e50-123"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="e3e50-124"><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="e3e50-124"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="e3e50-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="e3e50-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="e3e50-126"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="e3e50-126"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="e3e50-127">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="e3e50-127">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="e3e50-128">✔️ Empfohlen</span><span class="sxs-lookup"><span data-stu-id="e3e50-128">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="e3e50-129">✔️ Empfohlen (dritte Auswahl – <a href="interaction-fundamentals.md">Siehe andere Optionen</a>)</span><span class="sxs-lookup"><span data-stu-id="e3e50-129">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="e3e50-130">➕ Alternative Option</span><span class="sxs-lookup"><span data-stu-id="e3e50-130">➕ Alternate option</span></span></td>
    </tr>
         <tr>
        <td><span data-ttu-id="e3e50-131">Anvisieren mit den Augen und Ausführen</span><span class="sxs-lookup"><span data-stu-id="e3e50-131">Eye-gaze and commit</span></span></td>
        <td><span data-ttu-id="e3e50-132">❌ nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="e3e50-132">❌ Not available</span></span></td>
        <td><span data-ttu-id="e3e50-133">✔️ Empfohlen (dritte Auswahl – <a href="interaction-fundamentals.md">Siehe andere Optionen</a>)</span><span class="sxs-lookup"><span data-stu-id="e3e50-133">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="e3e50-134">❌ nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="e3e50-134">❌ Not available</span></span></td>
    </tr>
</table>


## <a name="gaze"></a><span data-ttu-id="e3e50-135">Anvisieren</span><span class="sxs-lookup"><span data-stu-id="e3e50-135">Gaze</span></span>

### <a name="eye--or-head-gaze"></a><span data-ttu-id="e3e50-136">Augen-oder Haupt Blick?</span><span class="sxs-lookup"><span data-stu-id="e3e50-136">Eye- or head-gaze?</span></span>
<span data-ttu-id="e3e50-137">Es gibt verschiedene Aspekte, die Sie berücksichtigen sollten, wenn Sie sich mit der Frage befassen, ob Sie das Eingabe Modell "Augenblick und Commit" oder "Head-Gaze und Commit" verwenden sollten.</span><span class="sxs-lookup"><span data-stu-id="e3e50-137">There are several considerations to take into account when faced with the question whether you should use the "eye-gaze and commit" or "head-gaze and commit" input model.</span></span> <span data-ttu-id="e3e50-138">Wenn Sie für ein immersives Headset oder für hololens (1st Gen) entwickeln, ist die Wahl einfach: Head-Blick und Commit.</span><span class="sxs-lookup"><span data-stu-id="e3e50-138">If you're developing for an immersive headset or for HoloLens (1st gen) then the choice is simple: Head-gaze and commit.</span></span> <span data-ttu-id="e3e50-139">Wenn Sie für hololens 2 entwickeln, ist die Auswahl etwas schwieriger. aus diesem Grund ist es wichtig, die Vorteile und Herausforderungen zu verstehen, die in den einzelnen Komponenten enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="e3e50-139">If you're developing for HoloLens 2, the choice becomes a little harder which is why it's important to understand the advantages and challenges that come with each of them.</span></span>
<span data-ttu-id="e3e50-140">Wir haben einige umfassende pro-und-con in der nachfolgenden Tabelle kompiliert, um die Zielvorgabe für das Ziel zu vergleichen.</span><span class="sxs-lookup"><span data-stu-id="e3e50-140">We compiled some broad pro's and con's in the table below to contrast head- vs. eye-gaze targeting.</span></span> <span data-ttu-id="e3e50-141">Dieser Vorgang ist weit von der Fertigstellung entfernt, und wir empfehlen, dass Sie hier mehr über die Ausrichtung des Augenblicks erfahren:</span><span class="sxs-lookup"><span data-stu-id="e3e50-141">This is far from complete and we suggest learning more about eye-gaze targeting in mixed reality here:</span></span>
* <span data-ttu-id="e3e50-142">[Eye Tracking on hololens 2](eye-tracking.md): Allgemeine Einführung in unsere neue Funktion für die Augen Verfolgung auf hololens 2, einschließlich einiger Entwickler Anleitungen.</span><span class="sxs-lookup"><span data-stu-id="e3e50-142">[Eye tracking on HoloLens 2](eye-tracking.md): General introduction of our new eye tracking capability on HoloLens 2 including some developer guidance.</span></span> 
* <span data-ttu-id="e3e50-143">[Interaktion](eye-gaze-interaction.md)mit Blick auf das Auge: Entwurfs Überlegungen und Empfehlungen bei der Planung der Verwendung von Eye Tracking als Eingabe.</span><span class="sxs-lookup"><span data-stu-id="e3e50-143">[Eye-gaze interaction](eye-gaze-interaction.md): Design considerations and recommendations when planning to use eye tracking as an input.</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><span data-ttu-id="e3e50-144"><strong>Ziel Ausrichtung</strong></span><span class="sxs-lookup"><span data-stu-id="e3e50-144"><strong>Eye-gaze targeting</strong></span></span></td>
        <td><span data-ttu-id="e3e50-145"><strong>Head-Blick-Ziel</strong></span><span class="sxs-lookup"><span data-stu-id="e3e50-145"><strong>Head-gaze targeting</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="e3e50-146">Schnelle!</span><span class="sxs-lookup"><span data-stu-id="e3e50-146">Fast!</span></span></td>
        <td><span data-ttu-id="e3e50-147">Voran</span><span class="sxs-lookup"><span data-stu-id="e3e50-147">Slower</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="e3e50-148">Niedriger Aufwand (kaum Text Bewegungen notwendig)</span><span class="sxs-lookup"><span data-stu-id="e3e50-148">Low effort (barely any body movements necessary)</span></span></td>
        <td><span data-ttu-id="e3e50-149">Mögliche Unannehmlichkeiten (z. b. Hals Belastung)</span><span class="sxs-lookup"><span data-stu-id="e3e50-149">Can be fatiguing - Possible discomfort (e.g., neck strain)</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="e3e50-150">Erfordert keinen Cursor, aber es wird ein feines Feedback empfohlen.</span><span class="sxs-lookup"><span data-stu-id="e3e50-150">Does not require a cursor, but subtle feedback is recommended</span></span></td>
        <td><span data-ttu-id="e3e50-151">Erfordert, dass ein Cursor angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e3e50-151">Requires to show a cursor</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="e3e50-152">Keine Smooth Eye-Bewegungen – z. b. nicht gut zum Zeichnen</span><span class="sxs-lookup"><span data-stu-id="e3e50-152">No smooth eye movements – e.g., not good for drawing</span></span></td>
        <td><span data-ttu-id="e3e50-153">Kontrollierter und expliziter</span><span class="sxs-lookup"><span data-stu-id="e3e50-153">More controlled and explicit</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="e3e50-154">Schwierig für sehr kleine Ziele (z. b. kleine Schaltflächen oder Weblinks)</span><span class="sxs-lookup"><span data-stu-id="e3e50-154">Difficult for very small targets (e.g., tiny buttons or weblinks)</span></span></td>
        <td><span data-ttu-id="e3e50-155">Zuverlässiges!</span><span class="sxs-lookup"><span data-stu-id="e3e50-155">Reliable!</span></span> <span data-ttu-id="e3e50-156">Großartiger Fallback!</span><span class="sxs-lookup"><span data-stu-id="e3e50-156">Great fallback!</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="e3e50-157">...</span><span class="sxs-lookup"><span data-stu-id="e3e50-157">...</span></span></td>
        <td><span data-ttu-id="e3e50-158">...</span><span class="sxs-lookup"><span data-stu-id="e3e50-158">...</span></span></td>
    </tr>
</table>

<span data-ttu-id="e3e50-159">Unabhängig davon, ob Sie den Kopf-oder Augenblick für das Eingabe Modell für den Blick und das Commit verwenden, gibt es unterschiedliche Sätze von Entwurfs Einschränkungen, die separat in den Artikeln für den [Augenblick und den Commit](gaze-and-commit-eyes.md) und den [Haupt-und Commit](gaze-and-commit-head.md) -Artikel behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="e3e50-159">Whether you use head-gaze or eye-gaze for your gaze-and-commit input model comes with different sets of design constraints, which will be covered separately in the [eye-gaze and commit](gaze-and-commit-eyes.md) and [head-gaze and commit](gaze-and-commit-head.md) articles.</span></span>

<br>

---

### <a name="cursor"></a><span data-ttu-id="e3e50-160">Cursor</span><span class="sxs-lookup"><span data-stu-id="e3e50-160">Cursor</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="e3e50-161">Für den Kopf Blick sollten die meisten apps einen [Cursor](cursors.md) (oder einen anderen Auditory/visuellen Hinweis) verwenden, um dem Benutzer die Gewissheit zu verschaffen, mit welchem Element er interagiert.</span><span class="sxs-lookup"><span data-stu-id="e3e50-161">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="e3e50-162">In der Regel positionieren Sie diesen Cursor in der Welt, in der der Head-Blick Strahl zuerst ein Objekt schneidet, das ein Hologramm oder eine reale Oberfläche sein kann.</span><span class="sxs-lookup"><span data-stu-id="e3e50-162">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span><br>
        <br>
        <span data-ttu-id="e3e50-163">Für den Augenblick empfiehlt es sich im allgemeinen *nicht* , einen Cursor anzuzeigen, da dies für den Benutzer schnell ablenkend und lästig werden kann.</span><span class="sxs-lookup"><span data-stu-id="e3e50-163">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="e3e50-164">Markieren Sie stattdessen visuelle Ziele, oder verwenden Sie einen sehr schwachen Augen Cursor, um sicherzustellen, womit der Benutzer interagieren soll.</span><span class="sxs-lookup"><span data-stu-id="e3e50-164">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="e3e50-165">Weitere Informationen finden Sie in unserem [Entwurfs Leit Faden für die Augen basierte Eingabe](eye-tracking.md) auf hololens 2.</span><span class="sxs-lookup"><span data-stu-id="e3e50-165">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="e3e50-166">![einen visuellen Beispiel Cursor zum Anzeigen von Blick](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="e3e50-166">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
       <span data-ttu-id="e3e50-167">*Bild: ein visueller Beispiel Cursor zum Anzeigen des Blicks*</span><span class="sxs-lookup"><span data-stu-id="e3e50-167">*Image: An example visual cursor to show gaze*</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a><span data-ttu-id="e3e50-168">Ausführen</span><span class="sxs-lookup"><span data-stu-id="e3e50-168">Commit</span></span>
<span data-ttu-id="e3e50-169">Nachdem Sie über verschiedene Möglichkeiten zum _betrachten_ eines Ziels gesprochen haben, sprechen wir etwas über den _Commit_ -Teil im _Blick und Commit_.</span><span class="sxs-lookup"><span data-stu-id="e3e50-169">After talking about different ways to _gaze_ at a target, let's talk a bit more about the _commit_ part in _gaze and commit_.</span></span>
<span data-ttu-id="e3e50-170">Nachdem ein Objekt oder ein UI-Element als Ziel verwendet wurde, kann der Benutzer mit einer sekundären Eingabe interagieren oder darauf klicken.</span><span class="sxs-lookup"><span data-stu-id="e3e50-170">After targeting an object or UI element, the user can interact or click on it using a secondary input.</span></span> <span data-ttu-id="e3e50-171">Dies wird als Commit-Schritt des Eingabe Modells bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="e3e50-171">This is known as the commit step of the input model.</span></span> 

<span data-ttu-id="e3e50-172">Die folgenden Methoden zum Ausführen werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="e3e50-172">The following commit methods are supported:</span></span>
- <span data-ttu-id="e3e50-173">Tippen Sie auf die Handbewegung (d. h., machen Sie Ihre Hand vor Ihnen, und bringen Sie Ihren Index Finger und Thumb)</span><span class="sxs-lookup"><span data-stu-id="e3e50-173">Air tap hand gesture (i.e., raise your hand in front of you and bring together your index finger and thumb)</span></span>
- <span data-ttu-id="e3e50-174">Sagen _Sie "Select"_ oder einen der Ziel Sprachbefehle</span><span class="sxs-lookup"><span data-stu-id="e3e50-174">Say _"select"_ or one of the targeted voice commands</span></span>
- <span data-ttu-id="e3e50-175">Eine einzelne Schaltfläche auf einem [hololens-Clicker](hardware-accessories.md#hololens-clicker) drücken</span><span class="sxs-lookup"><span data-stu-id="e3e50-175">Press a single button on a [HoloLens Clicker](hardware-accessories.md#hololens-clicker)</span></span>
- <span data-ttu-id="e3e50-176">Schaltfläche "A" auf einem Xbox Gamepad drücken</span><span class="sxs-lookup"><span data-stu-id="e3e50-176">Press the 'A' button on an Xbox gamepad</span></span>
- <span data-ttu-id="e3e50-177">Schaltfläche "A" auf einem adaptiven Xbox-Controller drücken</span><span class="sxs-lookup"><span data-stu-id="e3e50-177">Press the 'A' button on an Xbox adaptive controller</span></span>

### <a name="gaze-and-air-tap-gesture"></a><span data-ttu-id="e3e50-178">Bewegung für Blick und Luft tippen</span><span class="sxs-lookup"><span data-stu-id="e3e50-178">Gaze and air tap gesture</span></span>
<span data-ttu-id="e3e50-179">„In die Luft tippen“ ist eine Tippbewegung mit aufrecht gehaltener Hand</span><span class="sxs-lookup"><span data-stu-id="e3e50-179">Air tap is a tapping gesture with the hand held upright.</span></span> <span data-ttu-id="e3e50-180">Um eine Luft Abzweigung auszuführen, erhöhen Sie den Finger des Indexes an die bereite Position, und drücken Sie dann mit dem Ziehpunkt.</span><span class="sxs-lookup"><span data-stu-id="e3e50-180">To perform an air tap, raise your index finger to the ready position, then pinch with your thumb, and raise your index finger back up to release.</span></span> <span data-ttu-id="e3e50-181">Bei hololens (1. Generation) ist Air Tap die häufigste sekundäre Eingabe.</span><span class="sxs-lookup"><span data-stu-id="e3e50-181">On HoloLens (1st gen), air tap is the most common secondary input.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="e3e50-182">![Finger in der Ready-Position](images/readyandpress-ready.jpg)</span><span class="sxs-lookup"><span data-stu-id="e3e50-182">![Finger in the ready position](images/readyandpress-ready.jpg)</span></span><br>
       <span data-ttu-id="e3e50-183">**Finger an der Ready-Position**</span><span class="sxs-lookup"><span data-stu-id="e3e50-183">**Finger in the ready position**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="e3e50-184">![drücken Sie den Finger nach unten, um auf](images/readyandpress-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="e3e50-184">![Press finger down to tap or click](images/readyandpress-press.jpg)</span></span><br>
        <span data-ttu-id="e3e50-185">**Drücken Sie die nach-unten-Taste, um auf**</span><span class="sxs-lookup"><span data-stu-id="e3e50-185">**Press finger down to tap or click**</span></span><br>
    :::column-end:::
:::row-end:::


<span data-ttu-id="e3e50-186">Air Tap ist auch auf hololens 2 verfügbar.</span><span class="sxs-lookup"><span data-stu-id="e3e50-186">Air tap is also available on HoloLens 2.</span></span> <span data-ttu-id="e3e50-187">Es wurde von der ursprünglichen Version gelockert.</span><span class="sxs-lookup"><span data-stu-id="e3e50-187">It has been relaxed from the original version.</span></span> <span data-ttu-id="e3e50-188">Fast alle Arten von Pinches werden jetzt unterstützt, solange die Hand gleich ist und weiterhin ist.</span><span class="sxs-lookup"><span data-stu-id="e3e50-188">Nearly all types of pinches are now supported as long as the hand is upright and holding still.</span></span> <span data-ttu-id="e3e50-189">Dadurch kann der Benutzer die Geste viel einfacher erlernen und ausführen.</span><span class="sxs-lookup"><span data-stu-id="e3e50-189">This makes it much easier for users to learn and perform the gesture.</span></span> <span data-ttu-id="e3e50-190">Diese neue Luftlinie ersetzt die alte durch dieselbe API, sodass vorhandene Anwendungen das neue Verhalten automatisch nach der Neukompilierung für hololens 2 aufweisen.</span><span class="sxs-lookup"><span data-stu-id="e3e50-190">This new air tap replaces the old one through the same API, so existing applications will have the new behavior automatically after recompiling for HoloLens 2.</span></span>

<br>

---

### <a name="gaze-and-select-voice-command"></a><span data-ttu-id="e3e50-191">"Stimme" und "Select"-Befehl</span><span class="sxs-lookup"><span data-stu-id="e3e50-191">Gaze and "Select" voice command</span></span>
<span data-ttu-id="e3e50-192">Voice-Befehle sind eine der primären Interaktions Methoden in gemischter Realität.</span><span class="sxs-lookup"><span data-stu-id="e3e50-192">Voice commanding is one of the primary interaction methods in mixed reality.</span></span> <span data-ttu-id="e3e50-193">Es bietet einen sehr leistungsfähigen, kostenlosen Mechanismus zur Steuerung des Systems.</span><span class="sxs-lookup"><span data-stu-id="e3e50-193">It provides a very powerful hands-free mechanism to control the system.</span></span> <span data-ttu-id="e3e50-194">Es gibt verschiedene Typen von sprach Interaktions Modellen:</span><span class="sxs-lookup"><span data-stu-id="e3e50-194">There are different types of voice interaction models:</span></span>

- <span data-ttu-id="e3e50-195">Der generische SELECT-Befehl, der eine Klick-oder einen Commit als sekundäre Eingabe ausführt.</span><span class="sxs-lookup"><span data-stu-id="e3e50-195">The generic "Select" command that performs a click actuation or commit as a secondary input.</span></span>
- <span data-ttu-id="e3e50-196">Objekt Befehle (z. b. "Close" oder "make it Bigger") führen eine Aktion als sekundäre Eingabe aus und führen Sie aus.</span><span class="sxs-lookup"><span data-stu-id="e3e50-196">Object commands (e.g., "Close" or "Make it bigger") perform and commit to an action as a secondary input.</span></span>
- <span data-ttu-id="e3e50-197">Für globale Befehle (z. b. "Gehe zu Start") ist kein Ziel erforderlich.</span><span class="sxs-lookup"><span data-stu-id="e3e50-197">Global commands (e.g., "Go to start") don't require a target.</span></span>
- <span data-ttu-id="e3e50-198">Benutzeroberflächen für die Konversation oder Entitäten wie Cortana verfügen über eine künstliche Ki-Sprache.</span><span class="sxs-lookup"><span data-stu-id="e3e50-198">Conversation user interfaces or entities like Cortana have an AI natural language capability.</span></span>
- <span data-ttu-id="e3e50-199">Benutzerdefinierte Sprachbefehle</span><span class="sxs-lookup"><span data-stu-id="e3e50-199">Custom voice commands</span></span>

<span data-ttu-id="e3e50-200">Weitere Informationen sowie eine umfassende Liste der verfügbaren Sprachbefehle und deren Verwendung finden Sie in unserer [sprach befehlsanleitung](voice-design.md) .</span><span class="sxs-lookup"><span data-stu-id="e3e50-200">To find out more details as well as a comprehensive list of available voice commands and how to use them, check out our [voice commanding](voice-design.md) guidance.</span></span>

<br>

---


### <a name="gaze-and-hololens-clicker"></a><span data-ttu-id="e3e50-201">Blick und hololens Clicker</span><span class="sxs-lookup"><span data-stu-id="e3e50-201">Gaze and HoloLens Clicker</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="e3e50-202">Der hololens-Clicker ist das erste Peripheriegerät, das speziell für hololens erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="e3e50-202">The HoloLens Clicker is the first peripheral device built specifically for HoloLens.</span></span> <span data-ttu-id="e3e50-203">Es ist in der Entwicklungs Edition hololens (1st Gen) enthalten.</span><span class="sxs-lookup"><span data-stu-id="e3e50-203">It is included with HoloLens (1st gen) Development Edition.</span></span> <span data-ttu-id="e3e50-204">Der hololens-Clicker ermöglicht dem Benutzer das Klicken mit minimaler Handbewegung und das Commit als sekundäre Eingabe.</span><span class="sxs-lookup"><span data-stu-id="e3e50-204">The HoloLens Clicker lets a user click with minimal hand motion, and commit as a secondary input.</span></span> <span data-ttu-id="e3e50-205">Der hololens-Clicker stellt mithilfe von Bluetooth Low Energy (btle) eine Verbindung mit hololens (1 St Gen) oder hololens 2 her.</span><span class="sxs-lookup"><span data-stu-id="e3e50-205">The HoloLens Clicker connects to HoloLens (1st gen) or HoloLens 2 using Bluetooth Low Energy (BTLE).</span></span><br>
        <br>
        [<span data-ttu-id="e3e50-206">Weitere Informationen und Anweisungen zum Koppeln des Geräts</span><span class="sxs-lookup"><span data-stu-id="e3e50-206">More information and instructions to pair the device</span></span>](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="e3e50-207">*Image: hololens Clicker*</span><span class="sxs-lookup"><span data-stu-id="e3e50-207">*Image: HoloLens Clicker*</span></span>
    :::column-end:::
        :::column:::
       ![Hololens Clicker](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a><span data-ttu-id="e3e50-209">Blick und Xbox Wireless Controller</span><span class="sxs-lookup"><span data-stu-id="e3e50-209">Gaze and Xbox Wireless Controller</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="e3e50-210">Der Xbox Wireless-Controller führt mit der Schaltfläche "a" eine Klick-und eine sekundäre Eingabe durch.</span><span class="sxs-lookup"><span data-stu-id="e3e50-210">The Xbox Wireless Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="e3e50-211">Das Gerät ist einem Standardsatz von Aktionen zugeordnet, die beim Navigieren und Steuern des Systems helfen.</span><span class="sxs-lookup"><span data-stu-id="e3e50-211">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="e3e50-212">Wenn Sie den Controller anpassen möchten, verwenden Sie die Xbox Accessories-Anwendung, um Ihren Xbox Wireless-Controller zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="e3e50-212">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Wireless Controller.</span></span><br>
        <br>
        [<span data-ttu-id="e3e50-213">Koppeln eines Xbox-Controllers mit Ihrem PC</span><span class="sxs-lookup"><span data-stu-id="e3e50-213">How to pair an Xbox controller with your PC</span></span>](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="e3e50-214">*Bild: Xbox Wireless Controller*</span><span class="sxs-lookup"><span data-stu-id="e3e50-214">*Image: Xbox Wireless Controller*</span></span>
    :::column-end:::
        :::column:::
       ![Xbox Wireless Controller](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a><span data-ttu-id="e3e50-216">Blick und adaptiver Xbox-Controller</span><span class="sxs-lookup"><span data-stu-id="e3e50-216">Gaze and Xbox Adaptive Controller</span></span>
<span data-ttu-id="e3e50-217">Der Xbox Adaptive Controller ist in erster Linie für die Bedürfnisse von Spielern mit eingeschränkter Mobilität konzipiert und stellt einen einheitlichen Hub für Geräte dar, mit denen gemischte Realität leichter zugänglich gemacht werden kann.</span><span class="sxs-lookup"><span data-stu-id="e3e50-217">Designed primarily to meet the needs of gamers with limited mobility, the Xbox Adaptive Controller is a unified hub for devices that helps make mixed reality more accessible.</span></span>

<span data-ttu-id="e3e50-218">Der Xbox Adaptive Controller führt mit der Schaltfläche "a" eine Klick-und eine sekundäre Eingabe durch.</span><span class="sxs-lookup"><span data-stu-id="e3e50-218">The Xbox Adaptive Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="e3e50-219">Das Gerät ist einem Standardsatz von Aktionen zugeordnet, die beim Navigieren und Steuern des Systems helfen.</span><span class="sxs-lookup"><span data-stu-id="e3e50-219">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="e3e50-220">Wenn Sie den Controller anpassen möchten, verwenden Sie die Xbox Accessories-Anwendung, um den adaptiven Xbox-Controller zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="e3e50-220">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Adaptive Controller.</span></span>

<span data-ttu-id="e3e50-221">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span><span class="sxs-lookup"><span data-stu-id="e3e50-221">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span></span><br>
<span data-ttu-id="e3e50-222">*Xbox Adaptive Controller*</span><span class="sxs-lookup"><span data-stu-id="e3e50-222">*Xbox Adaptive Controller*</span></span>

<span data-ttu-id="e3e50-223">Verbinden Sie externe Geräte, wie z. b. Switches, Schaltflächen, bereit Stellungen und Joystick, um eine benutzerdefinierte Controller-benutzerdefinierte Controller Darstellung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e3e50-223">Connect external devices such as switches, buttons, mounts, and joysticks to create a custom controller experience that is uniquely yours.</span></span> <span data-ttu-id="e3e50-224">Schaltflächen-, fingerstick-und triggereingaben werden mit Hilfsgeräten gesteuert, die über 3.5 mm-und USB-Ports verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="e3e50-224">Button, thumbstick, and trigger inputs are controlled with assistive devices connected through 3.5mm jacks and USB ports.</span></span>

<span data-ttu-id="e3e50-225">![Xbox Adaptive Controller-Anschlüsse](images/xbox-adaptive-controller-ports.jpg)</span><span class="sxs-lookup"><span data-stu-id="e3e50-225">![Xbox Adaptive Controller ports](images/xbox-adaptive-controller-ports.jpg)</span></span><br>
<span data-ttu-id="e3e50-226">*Xbox Adaptive Controller-Anschlüsse*</span><span class="sxs-lookup"><span data-stu-id="e3e50-226">*Xbox Adaptive Controller ports*</span></span>

[<span data-ttu-id="e3e50-227">Anweisungen zum Koppeln des Geräts</span><span class="sxs-lookup"><span data-stu-id="e3e50-227">Instructions to pair the device</span></span>](hardware-accessories.md#pairing-bluetooth-accessories)

<span data-ttu-id="e3e50-228"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Weitere Informationen, die auf der Xbox-Website verfügbar sind</a></span><span class="sxs-lookup"><span data-stu-id="e3e50-228"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>More info available on the Xbox site</a></span></span>

<br>

---

## <a name="composite-gestures"></a><span data-ttu-id="e3e50-229">Zusammengesetzte Gesten</span><span class="sxs-lookup"><span data-stu-id="e3e50-229">Composite gestures</span></span>

### <a name="air-tap"></a><span data-ttu-id="e3e50-230">In die Luft tippen</span><span class="sxs-lookup"><span data-stu-id="e3e50-230">Air tap</span></span>
<span data-ttu-id="e3e50-231">Die Tap-Bewegung (und die anderen Gesten unten) reagiert nur auf eine bestimmte Abzweigung.</span><span class="sxs-lookup"><span data-stu-id="e3e50-231">The air tap gesture (as well as the other gestures below) reacts only to a specific tap.</span></span> <span data-ttu-id="e3e50-232">Um andere Abzweigungen zu erkennen, wie z. b. Menu oder grasp, muss Ihre Anwendung direkt die Interaktionen auf niedrigerer Ebene verwenden, die im obigen Abschnitt mit zwei wichtigen Komponenten Gesten beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="e3e50-232">To detect other taps, such as Menu or Grasp, your application must directly use the lower-level interactions described in the two key component gestures section above.</span></span>

### <a name="tap-and-hold"></a><span data-ttu-id="e3e50-233">Tippen und halten Sie</span><span class="sxs-lookup"><span data-stu-id="e3e50-233">Tap and hold</span></span>
<span data-ttu-id="e3e50-234">„Halten“ bedeutet einfach, die Position mit dem Finger nach unten beim „In die Luft tippen“ beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="e3e50-234">Hold is simply maintaining the downward finger position of the air tap.</span></span> <span data-ttu-id="e3e50-235">Die Kombination aus Luft tippen und halten ermöglicht eine Vielzahl komplexer "klicken und ziehen"-Interaktionen, wenn Sie mit Arm-Bewegung kombiniert werden, wie z. b. das Auswählen eines Objekts, anstatt es zu aktivieren oder um sekundäre Interaktionen wie das zeigen eines Kontextmenüs zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="e3e50-235">The combination of air tap and hold allows for a variety of more complex "click and drag" interactions when combined with arm movement such as picking up an object instead of activating it or mousedown secondary interactions such as showing a context menu.</span></span>
<span data-ttu-id="e3e50-236">Bei der Gestaltung dieser Geste sollte jedoch mit Bedacht vorgegangen werden, da die Benutzer dazu neigen können, ihre Handhaltungen im Laufe einer längeren Geste zu entspannen.</span><span class="sxs-lookup"><span data-stu-id="e3e50-236">Caution should be used when designing for this gesture however, as users can be prone to relaxing their hand postures during the course of any extended gesture.</span></span>

### <a name="manipulation"></a><span data-ttu-id="e3e50-237">Manipulation</span><span class="sxs-lookup"><span data-stu-id="e3e50-237">Manipulation</span></span>
<span data-ttu-id="e3e50-238">Manipulations Gesten können zum Verschieben, Ändern der Größe oder Drehen eines holograms verwendet werden, wenn das – Hologramm 1:1 auf die Handbewegungen des Benutzers reagieren soll.</span><span class="sxs-lookup"><span data-stu-id="e3e50-238">Manipulation gestures can be used to move, resize, or rotate a hologram when you want the hologram to react 1:1 to the user's hand movements.</span></span> <span data-ttu-id="e3e50-239">Eine Verwendungsmöglichkeit für solche 1:1-Bewegungen ist es, den Benutzer in der Umgebung zeichnen oder malen zu lassen.</span><span class="sxs-lookup"><span data-stu-id="e3e50-239">One use for such 1:1 movements is to let the user draw or paint in the world.</span></span>
<span data-ttu-id="e3e50-240">Die anfängliche Zielbestimmung für eine Manipulationsgeste sollte durch Anvisieren oder Zeigen erfolgen.</span><span class="sxs-lookup"><span data-stu-id="e3e50-240">The initial targeting for a manipulation gesture should be done by gaze or pointing.</span></span> <span data-ttu-id="e3e50-241">Wenn Tap und Hold gestartet werden, wird jede Bearbeitung des Objekts von Handbewegungen behandelt, sodass der Benutzer bei der Bearbeitung nicht mehr suchen kann.</span><span class="sxs-lookup"><span data-stu-id="e3e50-241">Once the tap and hold starts, any manipulation of the object is handled by hand movements, freeing the user to look around while they manipulate.</span></span>

### <a name="navigation"></a><span data-ttu-id="e3e50-242">Navigation</span><span class="sxs-lookup"><span data-stu-id="e3e50-242">Navigation</span></span>
<span data-ttu-id="e3e50-243">Navigationsgesten funktionieren wie ein virtueller Joystick und können zur Navigation in Widgets der Benutzeroberfläche, z. B. Radialmenüs, verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e3e50-243">Navigation gestures operate like a virtual joystick, and can be used to navigate UI widgets, such as radial menus.</span></span> <span data-ttu-id="e3e50-244">Sie tippen und halten, um die Geste zu starten, und bewegen dann Ihre Hand in einem normalisierten 3D-Würfel, der um die erste Betätigung herum angeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="e3e50-244">You tap and hold to start the gesture and then move your hand within a normalized 3D cube, centered around the initial press.</span></span> <span data-ttu-id="e3e50-245">Sie können Ihre Hand entlang der X-, Y- oder Z-Achse zwischen einem Wert von -1 bis 1 bewegen, wobei 0 der Ausgangspunkt ist.</span><span class="sxs-lookup"><span data-stu-id="e3e50-245">You can move your hand along the X, Y or Z axis from a value of -1 to 1, with 0 being the starting point.</span></span>
<span data-ttu-id="e3e50-246">Mithilfe der Navigation können geschwindigkeitsbasierte kontinuierliche Gesten zum Scrollen oder Zoomen erstellt werden, ähnlich dem Scrollen bei einer 2D-Benutzeroberfläche durch Klicken mit der mittleren Maustaste und anschließendes Bewegen der Maus nach oben und unten.</span><span class="sxs-lookup"><span data-stu-id="e3e50-246">Navigation can be used to build velocity-based continuous scrolling or zooming gestures, similar to scrolling a 2D UI by clicking the middle mouse button and then moving the mouse up and down.</span></span>

<span data-ttu-id="e3e50-247">Navigation mit Rails bezieht sich auf die Fähigkeit, Bewegungen auf einer bestimmten Achse zu erkennen, bis ein bestimmter Schwellenwert auf dieser Achse erreicht wird.</span><span class="sxs-lookup"><span data-stu-id="e3e50-247">Navigation with rails refers to the ability of recognizing movements in certain axis until a certain threshold is reached on that axis.</span></span> <span data-ttu-id="e3e50-248">Dies ist nur nützlich, wenn die Bewegung in mehr als einer Achse durch den Entwickler in einer Anwendung aktiviert ist, z. b. Wenn eine Anwendung so konfiguriert ist, dass Navigations Gesten über die x-, Y-Achse, aber auch die x-Achse mit Rails erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="e3e50-248">This is only useful when movement in more than one axis is enabled in an application by the developer, such as if an application is configured to recognize navigation gestures across X, Y axis but also specified X axis with rails.</span></span> <span data-ttu-id="e3e50-249">In diesem Fall erkennt das System Handbewegungen über die x-Achse, solange Sie auf der x-Achse innerhalb eines imaginären Rails (Handbuchs) bleiben, wenn die Handbewegung auch auf der Y-Achse auftritt.</span><span class="sxs-lookup"><span data-stu-id="e3e50-249">In this case the system will recognize hand movements across X axis as long as they remain within an imaginary rails (guide) on the X axis, if hand movement also occurs on the Y axis.</span></span>

<span data-ttu-id="e3e50-250">Innerhalb von 2D-Apps können Benutzer mit vertikalen Navigationsgesten innerhalb der App scrollen, zoomen oder ziehen.</span><span class="sxs-lookup"><span data-stu-id="e3e50-250">Within 2D apps, users can use vertical navigation gestures to scroll, zoom, or drag inside the app.</span></span> <span data-ttu-id="e3e50-251">Dadurch werden virtuelle Fingerberührungen in der App eingeführt, um Gesten für die Toucheingabe desselben Typs zu simulieren.</span><span class="sxs-lookup"><span data-stu-id="e3e50-251">This injects virtual finger touches to the app to simulate touch gestures of the same type.</span></span> <span data-ttu-id="e3e50-252">Benutzer können auswählen, welche dieser Aktionen durchgeführt werden, indem Sie zwischen den Tools auf der Leiste oberhalb der Anwendung wechseln, indem Sie entweder die Schaltfläche auswählen oder die Option "< Scrollmodus/Drag & Zoom > Tools" verwenden.</span><span class="sxs-lookup"><span data-stu-id="e3e50-252">Users can select which of these actions take place by toggling between the tools on the bar above the application, either by selecting the button or saying '<Scroll/Drag/Zoom> Tool'.</span></span>

[<span data-ttu-id="e3e50-253">Weitere Informationen zu zusammengesetzten Gesten</span><span class="sxs-lookup"><span data-stu-id="e3e50-253">More info on composite gestures</span></span>](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a><span data-ttu-id="e3e50-254">Gestenerkennung</span><span class="sxs-lookup"><span data-stu-id="e3e50-254">Gesture recognizers</span></span>

<span data-ttu-id="e3e50-255">Ein Vorteil bei der Verwendung der Gestenerkennung besteht darin, dass Sie eine Gestenerkennung nur für die Gesten konfigurieren können, die das derzeit zielgerichtete – Hologramm annehmen kann.</span><span class="sxs-lookup"><span data-stu-id="e3e50-255">One benefit of using gesture recognition is that you can configure a gesture recognizer only for the gestures the currently targeted hologram can accept.</span></span> <span data-ttu-id="e3e50-256">Die Plattform ist nur bei Bedarf eindeutig, um die unterstützten Gesten unterscheiden zu können.</span><span class="sxs-lookup"><span data-stu-id="e3e50-256">The platform only does disambiguation as necessary to distinguish those particular supported gestures.</span></span> <span data-ttu-id="e3e50-257">Auf diese Weise kann ein – Hologramm, das nur Air Tap unterstützt, jede Zeitspanne zwischen dem Drücken und dem Release akzeptieren, während ein – Hologramm, das sowohl Tap als auch Hold unterstützt, die Abzweigung nach dem Schwellenwert für die Aufbewahrungszeit auf einen Halt herauf Stufen kann.</span><span class="sxs-lookup"><span data-stu-id="e3e50-257">In this way, a hologram that just supports air tap can accept any length of time between press and release, while a hologram that supports both tap and hold can promote the tap to a hold after the hold time threshold.</span></span>

## <a name="hand-recognition"></a><span data-ttu-id="e3e50-258">Handerkennung</span><span class="sxs-lookup"><span data-stu-id="e3e50-258">Hand recognition</span></span>
<span data-ttu-id="e3e50-259">HoloLens erkennt Handgesten, indem die Position einer oder beider Hände, die für das Gerät sichtbar sind, verfolgt wird.</span><span class="sxs-lookup"><span data-stu-id="e3e50-259">HoloLens recognizes hand gestures by tracking the position of either or both hands that are visible to the device.</span></span> <span data-ttu-id="e3e50-260">HoloLens erkennt Hände, wenn sie sich entweder im Bereitschaftszustand (Handrücken mit nach oben gerichtetem Zeigefinger zu Ihnen gewandt) oder im gedrückten Zustand (Handrücken mit nach unten gerichtetem Zeigefinger zu Ihnen gewandt) befinden.</span><span class="sxs-lookup"><span data-stu-id="e3e50-260">HoloLens sees hands when they are in either the ready state (back of the hand facing you with index finger up) or the pressed state (back of the hand facing you with the index finger down).</span></span> <span data-ttu-id="e3e50-261">Wenn sich die Hände in anderen Posen befinden, werden Sie von hololens ignoriert.</span><span class="sxs-lookup"><span data-stu-id="e3e50-261">When hands are in other poses, HoloLens ignores them.</span></span>
<span data-ttu-id="e3e50-262">Für jede Hand, die hololens erkennt, können Sie ohne Ausrichtung und gedrücktem Zustand auf seine Position zugreifen.</span><span class="sxs-lookup"><span data-stu-id="e3e50-262">For each hand that HoloLens detects, you can access its position without orientation and its pressed state.</span></span> <span data-ttu-id="e3e50-263">Wenn sich die Hand dem Rand des Gestenrahmens nähert, erhalten Sie auch einen Richtungsvektor, den Sie dem Benutzer zeigen können, damit er weiß, wie er seine Hand bewegen muss, um sie dorthin zurückzubringen, wo sie von HoloLens erkannt werden kann.</span><span class="sxs-lookup"><span data-stu-id="e3e50-263">As the hand nears the edge of the gesture frame, you're also provided with a direction vector, which you can show to the user so they know how to move their hand to get it back where HoloLens can see it.</span></span>

## <a name="gesture-frame"></a><span data-ttu-id="e3e50-264">Gestenrahmen</span><span class="sxs-lookup"><span data-stu-id="e3e50-264">Gesture frame</span></span>
<span data-ttu-id="e3e50-265">Für Gesten in hololens muss sich die Hand innerhalb eines Gesten Rahmens befinden, der sich in einem Bereich befindet, der von der Bewegung zur Gesten Messung von der Nase bis zur Taille und von der Schulter aus angezeigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="e3e50-265">For gestures on HoloLens, the hand must be within a gesture frame, in a range that the gesture-sensing cameras can see appropriately,  from nose to waist and between the shoulders.</span></span> <span data-ttu-id="e3e50-266">Benutzer müssen in diesem Bereich geschult werden, um den Erfolg der Aktion und ihren eigenen Komfort zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="e3e50-266">Users need to be trained on this area of recognition both for success of action and for their own comfort.</span></span> <span data-ttu-id="e3e50-267">Viele Benutzer werden anfänglich davon ausgehen, dass sich der Gesten Rahmen in der Ansicht über hololens befinden muss</span><span class="sxs-lookup"><span data-stu-id="e3e50-267">Many users will initially assume that the gesture frame must be within their view through HoloLens, and hold their arms up uncomfortably in order to interact.</span></span> <span data-ttu-id="e3e50-268">Wenn Sie das hololens-Clicker verwenden, ist es nicht erforderlich, dass sich die Hände innerhalb des Gesten Rahmens befinden.</span><span class="sxs-lookup"><span data-stu-id="e3e50-268">When using the HoloLens Clicker, it's not necessary for hands to be within the gesture frame.</span></span>

<span data-ttu-id="e3e50-269">Im Fall von fortlaufenden Gesten besteht das Risiko, dass Benutzer ihre Hände außerhalb des Gesten Rahmens bewegen, während Sie sich in der Mitte der Bewegung befinden, wenn Sie z. b. ein Holographic-Objekt verschieben und das gewünschte Ergebnis verlieren.</span><span class="sxs-lookup"><span data-stu-id="e3e50-269">In the case of continuous gestures in particular, there is some risk of users moving their hands outside of the gesture frame while in mid-gesture when moving a holographic object, for example, and losing their intended outcome.</span></span>

<span data-ttu-id="e3e50-270">Sie sollten die folgenden drei Aspekte berücksichtigen:</span><span class="sxs-lookup"><span data-stu-id="e3e50-270">There are three things that you should consider:</span></span>

- <span data-ttu-id="e3e50-271">Benutzer Bildung für das vorhanden sein und die ungefähren Grenzen des Gesten Rahmens.</span><span class="sxs-lookup"><span data-stu-id="e3e50-271">User education on the gesture frame's existence and approximate boundaries.</span></span> <span data-ttu-id="e3e50-272">Dies wird während der hololens-Einrichtung vermittelt.</span><span class="sxs-lookup"><span data-stu-id="e3e50-272">This is taught during HoloLens setup.</span></span>

- <span data-ttu-id="e3e50-273">Benachrichtigen von Benutzern, wenn ihre Gesten die Gesten Rahmen Begrenzungen innerhalb einer Anwendung nähern oder unterbrechen, bis zu dem Ausmaß, in dem eine verlorene Bewegung zu unerwünschten Ergebnissen führt.</span><span class="sxs-lookup"><span data-stu-id="e3e50-273">Notifying users when their gestures are nearing or breaking the gesture frame boundaries within an application to the degree that a lost gesture leads to undesired outcomes.</span></span> <span data-ttu-id="e3e50-274">Research hat die Hauptqualitäten eines solchen Benachrichtigungs Systems aufgezeigt.</span><span class="sxs-lookup"><span data-stu-id="e3e50-274">Research has shown the key qualities of such a notification system.</span></span> <span data-ttu-id="e3e50-275">Die hololens-Shell stellt ein gutes Beispiel für diese Art von Benachrichtigung dar: Visual, auf dem zentralen Cursor, der die Richtung angibt, in der der Begrenzungs Übergang stattfindet.</span><span class="sxs-lookup"><span data-stu-id="e3e50-275">The HoloLens shell provides a good example of this type of notification--visual, on the central cursor, indicating the direction in which boundary crossing is taking place.</span></span>

- <span data-ttu-id="e3e50-276">Die Folgen des Überschreitens der Begrenzungen des Gestenrahmens sollten minimiert werden.</span><span class="sxs-lookup"><span data-stu-id="e3e50-276">Consequences of breaking the gesture frame boundaries should be minimized.</span></span> <span data-ttu-id="e3e50-277">Im Allgemeinen bedeutet dies, dass das Ergebnis einer Geste an der Grenze angehalten und nicht umgekehrt werden soll.</span><span class="sxs-lookup"><span data-stu-id="e3e50-277">In general, this means that the outcome of a gesture should be stopped at the boundary, and not reversed.</span></span> <span data-ttu-id="e3e50-278">Wenn ein Benutzer beispielsweise ein Holographic-Objekt über einen Raum verschiebt, sollte die Bewegung angehalten werden, wenn der Gesten Rahmen verletzt wird und nicht an den Ausgangspunkt zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="e3e50-278">For example, if a user is moving some holographic object across a room, the movement should stop when the gesture frame is breached, and not returned to the starting point.</span></span> <span data-ttu-id="e3e50-279">Der Benutzer kann einige Frustrationen erkennen, aber die Grenzen vielleicht besser verstehen und nicht jedes Mal die vollständigen beabsichtigten Aktionen neu starten.</span><span class="sxs-lookup"><span data-stu-id="e3e50-279">The user might experience some frustration, but might more quickly understand the boundaries, and not have to restart their full intended actions each time.</span></span>



## <a name="see-also"></a><span data-ttu-id="e3e50-280">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="e3e50-280">See also</span></span>
* [<span data-ttu-id="e3e50-281">Eye-basierte Interaktion</span><span class="sxs-lookup"><span data-stu-id="e3e50-281">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="e3e50-282">Augen Verfolgung auf hololens 2</span><span class="sxs-lookup"><span data-stu-id="e3e50-282">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="e3e50-283">Anvisieren und Verweilen</span><span class="sxs-lookup"><span data-stu-id="e3e50-283">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="e3e50-284">Bearbeitung von Hand direkt</span><span class="sxs-lookup"><span data-stu-id="e3e50-284">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="e3e50-285">Handgesten</span><span class="sxs-lookup"><span data-stu-id="e3e50-285">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="e3e50-286">"Hand Punkt" und "Commit"</span><span class="sxs-lookup"><span data-stu-id="e3e50-286">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="e3e50-287">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="e3e50-287">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="e3e50-288">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="e3e50-288">Voice input</span></span>](voice-input.md)

