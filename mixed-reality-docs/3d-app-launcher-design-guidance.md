---
title: Leitfaden zum Entwerfen von 3D-apps
description: Ein 3D-App-Startfeld ist ein "physisches" Objekt im gemischten Reality-Haus des Benutzers, das Sie auswählen können, um eine APP zu starten.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Design, 3D-App-Startfeld, immersives Headset, Live Cube
ms.openlocfilehash: ce9d242e26d67c8fe5af7ac32f4e910a15715d25
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437231"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="9ceb1-104">Leitfaden zum Entwerfen von 3D-apps</span><span class="sxs-lookup"><span data-stu-id="9ceb1-104">3D app launcher design guidance</span></span>

<span data-ttu-id="9ceb1-105">Wenn Sie ein Windows Mixed Reality immersive (VR)-Headset platzieren, können Sie die Windows Mixed Reality-Startseite eingeben und als Haus auf einer Klippe visualisieren, die von Bergen und Wasser umgeben ist (Sie können jedoch [auch andere Umgebungen auswählen und sogar eigene Umgebungen erstellen](add-custom-home-environments.md)).</span><span class="sxs-lookup"><span data-stu-id="9ceb1-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home, visualized as a house on a cliff surrounded by mountains and water (though you can [choose other environments and even create your own](add-custom-home-environments.md)).</span></span> <span data-ttu-id="9ceb1-106">Innerhalb des Raums dieses Zuhause kann ein Benutzer die 3D-Objekte und-apps, die für Sie wichtig sind, anordnen und organisieren.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-106">Within the space of this home, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="9ceb1-107">Ein **3D-App-** Startfeld ist ein "physisches" Objekt im gemischten Reality-Haus des Benutzers, das Sie auswählen können, um eine APP zu starten.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-107">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="9ceb1-108">![Beispiel: floaty Bird 3D-App-Startfeld](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="9ceb1-108">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="9ceb1-109">*Beispiel für floaty Bird 3D-App-Startfeld (fiktive APP)*</span><span class="sxs-lookup"><span data-stu-id="9ceb1-109">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="9ceb1-110">Erstellung eines 3D-App-Start Programms</span><span class="sxs-lookup"><span data-stu-id="9ceb1-110">3D app launcher creation process</span></span>

<span data-ttu-id="9ceb1-111">Zum Erstellen eines 3D-App-Start Programms sind drei Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="9ceb1-111">There are 3 steps to creating a 3D app launcher:</span></span>
1. <span data-ttu-id="9ceb1-112">Entwerfen und entwerfen (dieser Artikel)</span><span class="sxs-lookup"><span data-stu-id="9ceb1-112">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="9ceb1-113">Modellieren und exportieren</span><span class="sxs-lookup"><span data-stu-id="9ceb1-113">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="9ceb1-114">Integration in Ihre Anwendung:</span><span class="sxs-lookup"><span data-stu-id="9ceb1-114">Integrating it into your application:</span></span>
    * [<span data-ttu-id="9ceb1-115">UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="9ceb1-115">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="9ceb1-116">Win32-apps</span><span class="sxs-lookup"><span data-stu-id="9ceb1-116">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="9ceb1-117">Entwurfskonzepte</span><span class="sxs-lookup"><span data-stu-id="9ceb1-117">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="9ceb1-118">Fantastisch, aber schon vertraut</span><span class="sxs-lookup"><span data-stu-id="9ceb1-118">Fantastic yet familiar</span></span>

<span data-ttu-id="9ceb1-119">Die Windows Mixed Reality-Umgebung, in der sich Ihr App-Startfeld befindet, ist Teil vertraut, Teil fantastisch/Sci-Fi.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-119">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="9ceb1-120">Die besten Launcher befolgen die Regeln dieser Welt.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-120">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="9ceb1-121">Stellen Sie sich vor, wie Sie ein vertrautes, repräsentatives Objekt von Ihrer APP aus erstellen, aber einige der Regeln der tatsächlichen Realität übernehmen können.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-121">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="9ceb1-122">Magic führt dazu.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-122">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="9ceb1-123">Intuitiven</span><span class="sxs-lookup"><span data-stu-id="9ceb1-123">Intuitive</span></span>

<span data-ttu-id="9ceb1-124">Wenn Sie sich Ihr App-Startfeld ansehen, sollte der Zweck zum Starten Ihrer APP offensichtlich sein und keine Verwirrung verursachen.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-124">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="9ceb1-125">Stellen Sie sich z. b. vor, dass Ihr Start Programm ein offensichtlich-genug repräsentativ für Ihre APP ist, dass Sie nicht mit einem Teil der Einrichtung im Klippe-Haus verwechselt wird.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-125">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="9ceb1-126">Ihr App-Start Programm sollte Personen einladen, Sie zu berühren bzw. auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-126">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="9ceb1-127">![Beispiel: neues Hinweis 3D-App-Startfeld](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="9ceb1-127">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="9ceb1-128">*Neues Hinweis Beispiel für 3D-App-Start Programm (fiktive APP)*</span><span class="sxs-lookup"><span data-stu-id="9ceb1-128">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="9ceb1-129">Start Skala</span><span class="sxs-lookup"><span data-stu-id="9ceb1-129">Home scale</span></span>

<span data-ttu-id="9ceb1-130">3D-App-Launcher Leben im Klippe-Haus, und ihre Standardgröße sollte mit den anderen "physischen" Objekten im Raum Sinn machen.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-130">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="9ceb1-131">Wenn Sie das Start Programm anordnen, beispielsweise eine Hausanlage oder einige Möbel, sollte es sich in der eigenen Größe fühlen.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-131">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="9ceb1-132">Ein guter Ausgangspunkt ist, zu sehen, wie es 30 Kubikzentimeter aussieht, aber denken Sie daran, dass Benutzer es bei Bedarf zentral hoch-oder Herunterskalieren können.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-132">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="9ceb1-133">Eigen fähig</span><span class="sxs-lookup"><span data-stu-id="9ceb1-133">Own-able</span></span>

<span data-ttu-id="9ceb1-134">Das App-Start Programm sollte sich wie ein Objekt erweisen, das eine Person im Raum haben würde.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-134">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="9ceb1-135">Sie werden sich praktisch durch diese Dinge umgeben, sodass das Start Programm so aussehen sollte, wie etwas, was der Benutzer als wünschenswert erachtet hat</span><span class="sxs-lookup"><span data-stu-id="9ceb1-135">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="9ceb1-136">![Beispiel: Astro Warp 3D-App-Startfeld](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="9ceb1-136">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="9ceb1-137">*Beispiel für ein Beispiel für die Astro Warp 3D-app (fiktive APP)*</span><span class="sxs-lookup"><span data-stu-id="9ceb1-137">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="9ceb1-138">Unerkannt</span><span class="sxs-lookup"><span data-stu-id="9ceb1-138">Recognizable</span></span>

<span data-ttu-id="9ceb1-139">Ihr 3D-App-Startfeld sollte den Benutzern, die Sie sehen, umgehend die "Marke Ihrer APP" ausdrücken.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-139">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="9ceb1-140">Wenn Sie ein Sternzeichen oder ein besonders identifizierbares Objekt in Ihrer APP haben, empfiehlt es sich, dieses als einen großen Teil des Entwurfs zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-140">If you have a star character or an especially identifiable object in your app, we recommend using that as a big part of your design.</span></span> <span data-ttu-id="9ceb1-141">In einer Mixed Reality-Welt zeichnet ein Objekt von Benutzern mehr Interesse als nur ein Logo allein.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-141">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="9ceb1-142">Erkennbare Objekte kommunizieren schnell und eindeutig.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-142">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="9ceb1-143">Volumetrische</span><span class="sxs-lookup"><span data-stu-id="9ceb1-143">Volumetric</span></span>

<span data-ttu-id="9ceb1-144">Ihre APP verdient mehr als nur Ihr Logo auf eine flache Ebene zu bringen und Sie täglich Aufrufs.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-144">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="9ceb1-145">Das Start Programm sollte sich wie ein spannendes, 3D-Objekt im Bereich des Benutzers fühlen.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-145">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="9ceb1-146">Eine gute Vorgehensweise besteht darin, sich zu vorstellen, dass Ihre APP in der Tages Parade der Macy-Tage eine Sprechblase enthalten würde.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-146">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="9ceb1-147">Fragen Sie sich, was wirklich Menschen ist, die sich in der Straße befinden?</span><span class="sxs-lookup"><span data-stu-id="9ceb1-147">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="9ceb1-148">Was ist für alle Anzeige Winkel großartig?</span><span class="sxs-lookup"><span data-stu-id="9ceb1-148">What would look great from all viewing angles?</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="9ceb1-149">![Logo nur](images/20171016-140436-mixedreality-640px.jpg) *Logo*</span><span class="sxs-lookup"><span data-stu-id="9ceb1-149">![Logo only](images/20171016-140436-mixedreality-640px.jpg) *Logo only*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="9ceb1-150">![mit einem Zeichen besser erkennbar](images/20171016-140557-mixedreality-640px.jpg) *mit einem Zeichen besser erkennbar*</span><span class="sxs-lookup"><span data-stu-id="9ceb1-150">![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg) *More recognizable with a character*</span></span>
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        <span data-ttu-id="9ceb1-151">![flachen Ansatz, nicht überraschend, ist ein flacher](images/20171016-155101-mixedreality-640px.jpg) *flacher Ansatz, nicht überraschend, ist flach* .</span><span class="sxs-lookup"><span data-stu-id="9ceb1-151">![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg) *Flat approach, not surprisingly, feels flat*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="9ceb1-152">![Volumetric-Ansatz stellt Ihre APP besser dar](images/20171016-161407-mixedreality-640px.jpg) *volumetriansatz Ihre APP besser präsentiert* .</span><span class="sxs-lookup"><span data-stu-id="9ceb1-152">![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg) *Volumetric approach better showcases your app*</span></span>
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a><span data-ttu-id="9ceb1-153">Tipps für gute 3D-Modelle</span><span class="sxs-lookup"><span data-stu-id="9ceb1-153">Tips for good 3D models</span></span>

### <a name="best-practices"></a><span data-ttu-id="9ceb1-154">Bewährte Verfahren</span><span class="sxs-lookup"><span data-stu-id="9ceb1-154">Best practices</span></span>
* <span data-ttu-id="9ceb1-155">Wenn Sie Dimensionen für das App-Start Programm planen, sollten Sie ungefähr einen 30cm-Cube durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-155">When planning dimensions for your app launcher, shoot for roughly a 30cm cube.</span></span> <span data-ttu-id="9ceb1-156">Also ein Größenverhältnis von 1:1:1.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-156">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="9ceb1-157">Modelle müssen unter 10.000 Polygone liegen.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-157">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="9ceb1-158">Weitere Informationen zu Dreiecks Zählungen und Ebenen der Details (LODs)</span><span class="sxs-lookup"><span data-stu-id="9ceb1-158">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="9ceb1-159">Testen Sie nach Möglichkeit ein immersives Headset.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-159">Test on an immersive headset when possible.</span></span>
* <span data-ttu-id="9ceb1-160">Builddetails in der Geometrie des Modells, soweit möglich – verlassen Sie sich nicht auf Texturen.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-160">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="9ceb1-161">Erstellen einer "wasserdichten" geschlossenen Geometrie.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-161">Build “water tight” closed geometry.</span></span> <span data-ttu-id="9ceb1-162">Keine Lücken, die nicht in modelliert werden.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-162">No holes that are not modeled in.</span></span>
* <span data-ttu-id="9ceb1-163">Verwenden Sie natürliche Materialien in Ihrem Objekt.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-163">Use natural materials in your object.</span></span> <span data-ttu-id="9ceb1-164">Stellen Sie sich vor, Sie erstellen Sie in der Praxis.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-164">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="9ceb1-165">Stellen Sie sicher, dass Ihr Modell in unterschiedlichen Entfernungen und Größen gut funktioniert.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-165">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="9ceb1-166">Wenn Ihr Modell einsatzbereit ist, lesen Sie die [Richtlinien zum Exportieren von Assets](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span><span class="sxs-lookup"><span data-stu-id="9ceb1-166">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="9ceb1-167">![Modell mit geringfügigen Details in der Textur](images/20171013-143334-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="9ceb1-167">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="9ceb1-168">*Modell mit geringfügigen Details in der Textur*</span><span class="sxs-lookup"><span data-stu-id="9ceb1-168">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="9ceb1-169">Was Sie vermeiden sollten</span><span class="sxs-lookup"><span data-stu-id="9ceb1-169">What to avoid</span></span>
* <span data-ttu-id="9ceb1-170">Verwenden Sie keine kontrastreichen Details oder kleine, ausgelastete Muster und Texturen.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-170">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="9ceb1-171">Verwenden Sie Thin Geometry nicht – es funktioniert nicht gut in einer Entfernung und ist falsch.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-171">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="9ceb1-172">Lassen Sie Teile des Modells nicht zu viel über das Größenverhältnis von 1:1:1 hinaus erweitern.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-172">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="9ceb1-173">Es werden Skalierungsprobleme entstehen.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-173">It will create scaling problems.</span></span>

<span data-ttu-id="9ceb1-174">![vermeiden Sie Muster mit hohem Kontrast und wenig ausgelastet](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="9ceb1-174">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="9ceb1-175">*Vermeiden Sie große Kontraste, kleine, ausgelastete Muster*</span><span class="sxs-lookup"><span data-stu-id="9ceb1-175">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="9ceb1-176">Vorgehensweise beim Behandeln von Typen</span><span class="sxs-lookup"><span data-stu-id="9ceb1-176">How to handle type</span></span>

### <a name="best-practices"></a><span data-ttu-id="9ceb1-177">Bewährte Verfahren</span><span class="sxs-lookup"><span data-stu-id="9ceb1-177">Best practices</span></span>
* <span data-ttu-id="9ceb1-178">Es wird empfohlen, dass Ihr Typ ungefähr 1/3 ihres App-Start Programms umfasst (oder mehr).</span><span class="sxs-lookup"><span data-stu-id="9ceb1-178">We recommend your type comprises about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="9ceb1-179">Der Typ ist das wichtigste, das den Benutzern eine Vorstellung gibt, dass es sich bei Ihrem Start Programm tatsächlich um ein Start Programm handelt, sodass es sehr schön ist.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-179">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s pretty substantial.</span></span>
* <span data-ttu-id="9ceb1-180">Vermeiden Sie einen Super weiten Typ – versuchen Sie, ihn innerhalb der Grenzen der Kerndimensionen der App-Launcher (mehr oder weniger) zu halten.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-180">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="9ceb1-181">Der flattype kann funktionieren, aber beachten Sie, dass er in bestimmten Winkeln und in bestimmten Umgebungen schwer zu erkennen ist.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-181">Flat type can work, but be aware that it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="9ceb1-182">Möglicherweise sollten Sie ein solides Objekt oder einen Hintergrund dahinter ablegen, um dies zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-182">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="9ceb1-183">Das Hinzufügen von Dimensionen zu Ihrem Typ ist in 3D gut.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-183">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="9ceb1-184">Das Schattieren der Seiten des Typs unterscheidet sich durch die Lesbarkeit.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-184">Shading the sides of the type a different, darker color can help with readability.</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="9ceb1-185">![flattype ohne einen Hintergrund kann in bestimmten Winkeln und in bestimmten Umgebungen schwer zu finden sein](images/flattype-640px.png) *flacher Typ ohne Hintergrund kann in bestimmten Winkeln und in bestimmten Umgebungen schwer zu sehen sein* .</span><span class="sxs-lookup"><span data-stu-id="9ceb1-185">![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png) *Flat type without a backdrop can be hard to view from certain angles and in certain environments*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="9ceb1-186">![Typ mit einem integrierten Hintergrund kann gut funktionieren](images/flattypeandbkg-640px.png) *Typ mit einem integrierten Hintergrund kann gut funktionieren* .</span><span class="sxs-lookup"><span data-stu-id="9ceb1-186">![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png) *Type with a built-in backdrop can work well*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="9ceb1-187">Wenn Sie die Seiten schattieren, ![der Typ "extrudiert" gut funktioniert,](images/20171016-160221-mixedreality-640px.jpg) der *Typ "extrudiert" gut funktionieren, wenn Sie die Seiten schattieren*</span><span class="sxs-lookup"><span data-stu-id="9ceb1-187">![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg) *Extruded type can work well if you shade the sides*</span></span>
    :::column-end:::
:::row-end:::


<span data-ttu-id="9ceb1-188">**Typfarben, die funktionieren**</span><span class="sxs-lookup"><span data-stu-id="9ceb1-188">**Type colors that work**</span></span>
* <span data-ttu-id="9ceb1-189">Weisse</span><span class="sxs-lookup"><span data-stu-id="9ceb1-189">White</span></span>
* <span data-ttu-id="9ceb1-190">Box</span><span class="sxs-lookup"><span data-stu-id="9ceb1-190">Black</span></span>
* <span data-ttu-id="9ceb1-191">Helle halb satte Farbe</span><span class="sxs-lookup"><span data-stu-id="9ceb1-191">Bright semi-saturated color</span></span>

<span data-ttu-id="9ceb1-192">![typfarben, die funktionieren.](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="9ceb1-192">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="9ceb1-193">*Typfarben, die funktionieren*</span><span class="sxs-lookup"><span data-stu-id="9ceb1-193">*Type colors that work*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="9ceb1-194">Was Sie vermeiden sollten</span><span class="sxs-lookup"><span data-stu-id="9ceb1-194">What to avoid</span></span>

<span data-ttu-id="9ceb1-195">**Typfarben, die Probleme verursachen**</span><span class="sxs-lookup"><span data-stu-id="9ceb1-195">**Type colors that cause trouble**</span></span>
* <span data-ttu-id="9ceb1-196">Mitteltöne</span><span class="sxs-lookup"><span data-stu-id="9ceb1-196">Mid-tones</span></span>
* <span data-ttu-id="9ceb1-197">grau</span><span class="sxs-lookup"><span data-stu-id="9ceb1-197">Gray</span></span>
* <span data-ttu-id="9ceb1-198">Über satte Farben oder nicht satte Farben</span><span class="sxs-lookup"><span data-stu-id="9ceb1-198">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="9ceb1-199">![typfarben, die Probleme verursachen.](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="9ceb1-199">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="9ceb1-200">*Typfarben, die Probleme verursachen*</span><span class="sxs-lookup"><span data-stu-id="9ceb1-200">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="9ceb1-201">Beleuchtung</span><span class="sxs-lookup"><span data-stu-id="9ceb1-201">Lighting</span></span>

<span data-ttu-id="9ceb1-202">Die Beleuchtung für das App-Start Programm stammt aus der Umgebung "Klippe House".</span><span class="sxs-lookup"><span data-stu-id="9ceb1-202">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="9ceb1-203">Stellen Sie sicher, dass Sie das Start Programm an mehreren Stellen im ganzen Haus testen, damit es in Licht und Schatten gut aussieht.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-203">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="9ceb1-204">Die gute Nachricht ist, dass Sie, wenn Sie den anderen Entwurfs Leit Faden in diesem Dokument befolgt haben, das Start Programm in einer ziemlich guten Form für die meisten Beleuchtung im Klippe-Haus aufweisen sollten.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-204">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in pretty good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="9ceb1-205">Ein guter Ausgangspunkt, um zu testen, wie das Start Programm in den verschiedenen Lichtern in der Umgebung aussieht, sind Studio, der Medienraum, an einer beliebigen Stelle außerhalb und auf der Rückseite (der konkrete Bereich mit dem Rasen).</span><span class="sxs-lookup"><span data-stu-id="9ceb1-205">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="9ceb1-206">Ein weiterer guter Test besteht darin, den halblicht-und Halbschatten zu platzieren und zu sehen, wie er aussieht.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-206">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="9ceb1-207">![stellen Sie sicher, dass das Start Programm sowohl in Beleuchtung als auch in Schatten angezeigt wird.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="9ceb1-207">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="9ceb1-208">*Stellen Sie sicher, dass das Start Programm in Licht und Schatten gut aussieht*</span><span class="sxs-lookup"><span data-stu-id="9ceb1-208">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="9ceb1-209">Texturierung</span><span class="sxs-lookup"><span data-stu-id="9ceb1-209">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="9ceb1-210">Erstellen von Texturen</span><span class="sxs-lookup"><span data-stu-id="9ceb1-210">Authoring your textures</span></span>

<span data-ttu-id="9ceb1-211">Das Endformat des 3D-App-Start Programms ist eine. GLB-Datei, die mithilfe der PBR-Pipeline (physisch basiertes Rendering) erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-211">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="9ceb1-212">Dies kann ein kniffliger Prozess sein. jetzt ist es ein guter Zeitpunkt, einen technischen Künstler zu verwenden, wenn Sie dies noch nicht getan haben.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-212">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="9ceb1-213">Wenn Sie ein mutiger DIY sind und sich die Zeit nehmen, sich mit der [PBR-Terminologie](https://wiki.polycount.com/wiki/PBR) vertraut zu machen und zu erfahren, was im Hintergrund passiert, bevor Sie beginnen, können Sie häufige Fehler vermeiden.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-213">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](https://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="9ceb1-214">![Beispiel: App für neue Notiz](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="9ceb1-214">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="9ceb1-215">*Neues Hinweis Beispiel für 3D-App-Start Programm (fiktive APP)*</span><span class="sxs-lookup"><span data-stu-id="9ceb1-215">*Fresh Note 3D app launcher example (fictional app)*</span></span>

<span data-ttu-id="9ceb1-216">**Empfohlenes Authoring Tool**</span><span class="sxs-lookup"><span data-stu-id="9ceb1-216">**Recommended authoring tool**</span></span>

<span data-ttu-id="9ceb1-217">Es wird empfohlen, den [Substanz Maler](https://www.allegorithmic.com/products/substance-painter) von allethmic zu verwenden, um Ihre endgültige Datei zu verfassen.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-217">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="9ceb1-218">Wenn Sie nicht mit der Erstellung von PBR-Shadern in der Inhalts Malerin vertraut sind, finden Sie hier ein [Tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span><span class="sxs-lookup"><span data-stu-id="9ceb1-218">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="9ceb1-219">(Alternativ kann [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/)oder [marthset](https://www.marmoset.co/toolbag/) auch verwendet werden, wenn Sie mit einer der beiden vertraut sind.)</span><span class="sxs-lookup"><span data-stu-id="9ceb1-219">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="9ceb1-220">Bewährte Verfahren</span><span class="sxs-lookup"><span data-stu-id="9ceb1-220">Best practices</span></span>

* <span data-ttu-id="9ceb1-221">Wenn das App-Start Programmobjekt für PBR erstellt wurde, sollte es recht einfach sein, es für die Umgebung "Klippe" zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-221">If your app launcher object was authored for PBR, it should be pretty straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="9ceb1-222">Unser Shader erwartet einen Metal/roughness-Workflow – der Unreal PBR-Shader ist ein schließende Fax.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-222">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="9ceb1-223">Wenn Sie Ihre Texturen exportieren, sollten Sie die [empfohlenen Textur Größen](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-223">When exporting your textures keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="9ceb1-224">Stellen Sie sicher, dass Sie die Objekte für die Echtzeitbeleuchtung erstellen – Dies bedeutet Folgendes:</span><span class="sxs-lookup"><span data-stu-id="9ceb1-224">Make sure to build your objects for real-time lighting — this means:</span></span>
    * <span data-ttu-id="9ceb1-225">Vermeiden gebackener Schatten – oder gezeichnete Schatten</span><span class="sxs-lookup"><span data-stu-id="9ceb1-225">Avoid baked shadows – or painted shadows</span></span>
    * <span data-ttu-id="9ceb1-226">Vermeiden Sie eine gebackenes Beleuchtung in den Texturen</span><span class="sxs-lookup"><span data-stu-id="9ceb1-226">Avoid baked lighting in the textures</span></span>
    * <span data-ttu-id="9ceb1-227">Verwenden Sie eines der Pakete zur Erstellung von PBR-Materialien, um die richtigen Zuordnungen für den Shader zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="9ceb1-227">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="9ceb1-228">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="9ceb1-228">See also</span></span>

* [<span data-ttu-id="9ceb1-229">Erstellen von 3D-Modellen für die Verwendung in der Mixed Reality-Startseite</span><span class="sxs-lookup"><span data-stu-id="9ceb1-229">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="9ceb1-230">Implementieren von 3D-App-Startprogrammen (UWP-Apps)</span><span class="sxs-lookup"><span data-stu-id="9ceb1-230">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="9ceb1-231">Implementieren von 3D-App-Startprogrammen (Win32-Apps)</span><span class="sxs-lookup"><span data-stu-id="9ceb1-231">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
