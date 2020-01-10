---
title: Fakboardingvorgang und Tag-entlang
description: Objekte mit einem Abrechnungs-Board orientieren sich stets an dem Benutzer.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, fakboardingvorgang, tagparallel
ms.openlocfilehash: 24c4ca8bdc3c6ea1081311102204d4a7f5a95425
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723179"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="5106c-104">Fakboardingvorgang und Tag-entlang</span><span class="sxs-lookup"><span data-stu-id="5106c-104">Billboarding and tag-along</span></span>

<br>

<img src="images/UX/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a><span data-ttu-id="5106c-105">Was ist die Abrechnung?</span><span class="sxs-lookup"><span data-stu-id="5106c-105">What is billboarding?</span></span>

<span data-ttu-id="5106c-106">Bei der Abrechnung handelt es sich um ein Verhaltens Konzept, das auf Objekte in gemischter Realität angewendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="5106c-106">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="5106c-107">Objekte mit einem Abrechnungs-Board orientieren sich stets an dem Benutzer.</span><span class="sxs-lookup"><span data-stu-id="5106c-107">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="5106c-108">Dies ist insbesondere bei Text-und menuingsystemen hilfreich, bei denen statische Objekte, die in der Umgebung des Benutzers (der Welt gesperrt) platziert werden, andernfalls verdeckt oder unlesbar sind, wenn ein Benutzer sich bewegen würde.</span><span class="sxs-lookup"><span data-stu-id="5106c-108">This is especially helpful with text and menuing systems where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable if a user were to move around.</span></span>

<span data-ttu-id="5106c-109">Objekte mit aktiviertem fakboardingvorgang können in der Benutzerumgebung frei rotiert werden.</span><span class="sxs-lookup"><span data-stu-id="5106c-109">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="5106c-110">Sie können je nach Entwurfs Überlegungen auch auf eine einzelne Achse beschränkt werden.</span><span class="sxs-lookup"><span data-stu-id="5106c-110">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="5106c-111">Beachten Sie, dass abgelegte Objekte möglicherweise ein-oder ausgeblendet werden, wenn Sie sich zu nahe an anderen Objekten befinden oder in hololens zu schließen.</span><span class="sxs-lookup"><span data-stu-id="5106c-111">Keep in mind, billboarded objects may clip or occlude themselves if they are placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="5106c-112">Um dies zu vermeiden, stellen Sie sich den Gesamt Speicherbedarf vor, der von einem Objekt erzeugt wird, wenn es auf der Achse gedreht wird, die für das</span><span class="sxs-lookup"><span data-stu-id="5106c-112">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

<br>

---
## <a name="what-is-a-tag-along"></a><span data-ttu-id="5106c-113">Was ist ein Tag?</span><span class="sxs-lookup"><span data-stu-id="5106c-113">What is a tag-along?</span></span>

<span data-ttu-id="5106c-114">Tagparallel ist ein Verhaltens Konzept, das holograms hinzugefügt werden kann.</span><span class="sxs-lookup"><span data-stu-id="5106c-114">Tag-along is a behavioral concept that can be added to holograms.</span></span> <span data-ttu-id="5106c-115">Ein Tag-entlang-Objekt versucht, in einem Bereich zu bleiben, der es dem Benutzer ermöglicht, komfortabel zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="5106c-115">A tag-along object attempts to stay in a range that allows the user to interact comfortably.</span></span>

<span data-ttu-id="5106c-116">![das hololens-Pins-Panel ist ein gutes Beispiel dafür, wie sich Tag-entlang verhält](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="5106c-116">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="5106c-117">*Das hololens-Startmenü ist ein gutes Beispiel für das tagparallel Verhalten.*</span><span class="sxs-lookup"><span data-stu-id="5106c-117">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="5106c-118">Tagbasierte Objekte verfügen über Parameter, die die Art und Weise, wie Sie sich Verhalten, optimieren können.</span><span class="sxs-lookup"><span data-stu-id="5106c-118">Tag-along objects have parameters which can fine-tune the way they behave.</span></span> <span data-ttu-id="5106c-119">Der Inhalt kann von der Sicht des Benutzers wie gewünscht in die oder aus der Sicht des Benutzers gesetzt werden, während der Benutzer die Umgebung verlässt.</span><span class="sxs-lookup"><span data-stu-id="5106c-119">Content can be in or out of the user’s line of sight as desired while the user moves around their environment.</span></span> <span data-ttu-id="5106c-120">Wenn der Benutzer sich bewegt, versucht der Inhalt, in der Peripherie des Benutzers zu bleiben, indem er an den Rand der Ansicht bewegt wird, je nachdem, wie schnell der Inhalt durch einen Benutzer verschoben wird, kann der Inhalt vorübergehend nicht mehr angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="5106c-120">As the user moves, the content will attempt to stay within the user’s periphery by sliding towards the edge of the view, depending on how quickly a user moves may leave the content temporarily out of view.</span></span> <span data-ttu-id="5106c-121">Wenn der Benutzer in Richtung des tagbasierten Objekts zeigt, wird es vollständig in die Ansicht integriert.</span><span class="sxs-lookup"><span data-stu-id="5106c-121">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="5106c-122">Stellen Sie sich vor, dass Inhalte immer "auf einen Blick entfernt" werden, damit Benutzer niemals vergessen, welche Richtung ihr Inhalt hat.</span><span class="sxs-lookup"><span data-stu-id="5106c-122">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="5106c-123">Zusätzliche Parameter können dazu führen, dass das Tag-an-Objekt von einem Gummi Band an den Kopf des Benutzers angefügt wird.</span><span class="sxs-lookup"><span data-stu-id="5106c-123">Additional parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="5106c-124">Durch die Beschleunigung oder Verlangsamung der Dämpfung wird das-Objekt gewichtet, sodass es physisch vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="5106c-124">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="5106c-125">Dieses Spring Verhalten ist ein kostengünstiger, mit dem der Benutzer ein genaues mentales Modell zur Funktionsweise von Tag-Along erstellen kann.</span><span class="sxs-lookup"><span data-stu-id="5106c-125">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="5106c-126">Mithilfe von Audiodaten können zusätzliche Kosten bereitgestellt werden, wenn Benutzer Objekte im tagbasierten Modus haben.</span><span class="sxs-lookup"><span data-stu-id="5106c-126">Audio helps provide additional affordances for when users have objects in tag-along mode.</span></span> <span data-ttu-id="5106c-127">Audiogeschwindigkeit sollte die Geschwindigkeit der Bewegung verstärken. eine schnelle Kopfzeile sollte einen merklicheren Soundeffekt bereitstellen, während Sie mit einer natürlichen Geschwindigkeit nur minimale Audioergebnisse aufweisen sollten.</span><span class="sxs-lookup"><span data-stu-id="5106c-127">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect while walking at a natural speed should have minimal audio if any effects at all.</span></span>

<span data-ttu-id="5106c-128">Ebenso wie wirklich mit dem Titel gesperrter Inhalt können sich taggingobjekte als überwältigend oder übersichtlich erweisen, wenn Sie in der Ansicht des Benutzers sehr stark verschoben werden.</span><span class="sxs-lookup"><span data-stu-id="5106c-128">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="5106c-129">Wenn ein Benutzer die Suche durchsucht und dann schnell anhält, werden Sie von Ihren Sinnen informiert, dass Sie angehalten wurden.</span><span class="sxs-lookup"><span data-stu-id="5106c-129">As a user looks around and then quickly stop, their senses tell them they have stopped.</span></span> <span data-ttu-id="5106c-130">Ihr Saldo informiert Sie darüber, dass ihre Kopfzeile angehalten wurde, und ihre Vision sieht, dass die Welt beendet wird.</span><span class="sxs-lookup"><span data-stu-id="5106c-130">Their balance informs them that their head has stopped turning as well as their vision sees the world stop turning.</span></span> <span data-ttu-id="5106c-131">Wenn das Tag-Along jedoch weiterhin verschoben wird, wenn der Benutzer angehalten wurde, kann es seine Sinne verwirren.</span><span class="sxs-lookup"><span data-stu-id="5106c-131">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="5106c-132">Fakboardingvorgang und tagparallel in mrtk (Mixed Reality Toolkit) für Unity</span><span class="sxs-lookup"><span data-stu-id="5106c-132">Billboarding and Tag-along in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="5106c-133">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** stellt Skripts für das fakboardingverhalten und das tagbasierte Verhalten bereit.</span><span class="sxs-lookup"><span data-stu-id="5106c-133">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts for the Billboarding and tag-along behavior.</span></span> <span data-ttu-id="5106c-134">Weisen Sie das Billboard.cs-Skript einfach einem beliebigen Objekt zu, um das Abrechnungs Verhalten hinzuzufügen, und machen Sie das Objekt immer auf dem Bild</span><span class="sxs-lookup"><span data-stu-id="5106c-134">Simply assign the Billboard.cs script onto any object to add billboarding behavior and make the object always face you.</span></span> <span data-ttu-id="5106c-135">Verwenden Sie das RadialView.cs-Skript, um das tagbasierte Verhalten hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="5106c-135">To add tag-along behavior, use the RadialView.cs script.</span></span> <span data-ttu-id="5106c-136">Sie können verschiedene Optionen wie z. b. lerping-Zeit, Entfernung und Grad anpassen.</span><span class="sxs-lookup"><span data-stu-id="5106c-136">You can adjust various options such as lerping time, distance, and degree.</span></span>

* [<span data-ttu-id="5106c-137">-Solver der mrtk-radialen Ansicht</span><span class="sxs-lookup"><span data-stu-id="5106c-137">MRTK - Radial View Solver</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html#radialview)
* [<span data-ttu-id="5106c-138">Mrtk-Billboard-Skript</span><span class="sxs-lookup"><span data-stu-id="5106c-138">MRTK - Billboard script</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a><span data-ttu-id="5106c-139">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="5106c-139">See also</span></span>

* [<span data-ttu-id="5106c-140">Cursor</span><span class="sxs-lookup"><span data-stu-id="5106c-140">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="5106c-141">Handstrahl</span><span class="sxs-lookup"><span data-stu-id="5106c-141">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="5106c-142">Button</span><span class="sxs-lookup"><span data-stu-id="5106c-142">Button</span></span>](button.md)
* [<span data-ttu-id="5106c-143">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="5106c-143">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="5106c-144">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="5106c-144">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="5106c-145">Manipulation</span><span class="sxs-lookup"><span data-stu-id="5106c-145">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="5106c-146">Handmenü</span><span class="sxs-lookup"><span data-stu-id="5106c-146">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="5106c-147">Nähemenü</span><span class="sxs-lookup"><span data-stu-id="5106c-147">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="5106c-148">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="5106c-148">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="5106c-149">Sprachbefehl</span><span class="sxs-lookup"><span data-stu-id="5106c-149">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="5106c-150">Tastatur</span><span class="sxs-lookup"><span data-stu-id="5106c-150">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="5106c-151">QuickInfo</span><span class="sxs-lookup"><span data-stu-id="5106c-151">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="5106c-152">Filmklappe</span><span class="sxs-lookup"><span data-stu-id="5106c-152">Slate</span></span>](slate.md)
* [<span data-ttu-id="5106c-153">Schieberegler</span><span class="sxs-lookup"><span data-stu-id="5106c-153">Slider</span></span>](slider.md)
* [<span data-ttu-id="5106c-154">Shader</span><span class="sxs-lookup"><span data-stu-id="5106c-154">Shader</span></span>](shader.md)
* [<span data-ttu-id="5106c-155">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="5106c-155">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="5106c-156">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="5106c-156">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="5106c-157">Oberflächenmagnetismus</span><span class="sxs-lookup"><span data-stu-id="5106c-157">Surface magnetism</span></span>](surface-magnetism.md)
