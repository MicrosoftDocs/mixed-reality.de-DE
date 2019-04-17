---
title: Leitfaden zum Entwerfen von 3D app-Startfeld
description: Ein-3D-app-Startfeld ist ein "physical"-Objekt in der Benutzer mixed Reality Haus, die sie auswählen können, um eine app zu starten.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Entwurf, 3D app-Startfeld, immersive Kopfhörer, live-cube
ms.openlocfilehash: 47db5bffa121c0cc11d246dc749c464e5f187270
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593645"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="4c37a-104">Leitfaden zum Entwerfen von 3D app-Startfeld</span><span class="sxs-lookup"><span data-stu-id="4c37a-104">3D app launcher design guidance</span></span>

<span data-ttu-id="4c37a-105">Wenn Sie auf einem Windows Mixed Reality immersive (VR) Kopfhörer einfügen, Sie geben Sie die Windows Mixed Reality home, als ein Haus auf ein enthaltender Alpen und Wasser Cliff visualisiert (obwohl Sie können [andere Umgebungen auswählen, und erstellen Sie eigene](add-custom-home-environments.md)).</span><span class="sxs-lookup"><span data-stu-id="4c37a-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home, visualized as a house on a cliff surrounded by mountains and water (though you can [choose other environments and even create your own](add-custom-home-environments.md)).</span></span> <span data-ttu-id="4c37a-106">Innerhalb des Bereichs dieses ist ein Benutzer home, anordnen und Organisieren Sie die 3D-Objekte und apps, die sie beliebig interessieren gewünschten kostenlos.</span><span class="sxs-lookup"><span data-stu-id="4c37a-106">Within the space of this home, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="4c37a-107">Ein **-3D-app-Startfeld** ist ein "physical"-Objekt in der Benutzer die Realität Haus, die sie auswählen können, um eine app zu starten gemischt.</span><span class="sxs-lookup"><span data-stu-id="4c37a-107">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="4c37a-108">![Beispiel: Unverankerten Bird-3D-app-Startfeld](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4c37a-108">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="4c37a-109">*Unverankerten Bird 3D-Startprogramm-Beispiel-app (fiktive app)*</span><span class="sxs-lookup"><span data-stu-id="4c37a-109">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="4c37a-110">3D app-Startprogramm-Erstellungsprozess</span><span class="sxs-lookup"><span data-stu-id="4c37a-110">3D app launcher creation process</span></span>

<span data-ttu-id="4c37a-111">Es gibt 3 Schritte zum Erstellen einer-3D-app-Startfeld:</span><span class="sxs-lookup"><span data-stu-id="4c37a-111">There are 3 steps to creating a 3D app launcher:</span></span>
1. <span data-ttu-id="4c37a-112">Entwerfen und Concepting (dieser Artikel)</span><span class="sxs-lookup"><span data-stu-id="4c37a-112">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="4c37a-113">Modellieren und exportieren</span><span class="sxs-lookup"><span data-stu-id="4c37a-113">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="4c37a-114">Die Integration in Ihre Anwendung:</span><span class="sxs-lookup"><span data-stu-id="4c37a-114">Integrating it into your application:</span></span>
    * [<span data-ttu-id="4c37a-115">UWP-Apps</span><span class="sxs-lookup"><span data-stu-id="4c37a-115">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="4c37a-116">Win32-apps</span><span class="sxs-lookup"><span data-stu-id="4c37a-116">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="4c37a-117">Entwurfskonzepte</span><span class="sxs-lookup"><span data-stu-id="4c37a-117">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="4c37a-118">Super, aber vertraut</span><span class="sxs-lookup"><span data-stu-id="4c37a-118">Fantastic yet familiar</span></span>

<span data-ttu-id="4c37a-119">Die Windows Mixed Reality-Umgebung, die Ihre app-Startfeld befindet sich in ist Teil vertraut, Teil fantastischen/SCSI-Fi an.</span><span class="sxs-lookup"><span data-stu-id="4c37a-119">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="4c37a-120">Die beste Startprogramme folgen die Regeln der Welt.</span><span class="sxs-lookup"><span data-stu-id="4c37a-120">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="4c37a-121">Stellen Sie sich wie ein Objekt vertraut, repräsentative aus Ihrer app nutzen können Biegen einige der Regeln der tatsächlichen Realität.</span><span class="sxs-lookup"><span data-stu-id="4c37a-121">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="4c37a-122">Magic-Befehl führt.</span><span class="sxs-lookup"><span data-stu-id="4c37a-122">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="4c37a-123">Intuitiv</span><span class="sxs-lookup"><span data-stu-id="4c37a-123">Intuitive</span></span>

<span data-ttu-id="4c37a-124">Wenn Sie Ihre app-Startfeld betrachten, wird dessen Zweck - zum Starten der app - sollte klar sein, und sollte nicht zu Verwirrung führen.</span><span class="sxs-lookup"><span data-stu-id="4c37a-124">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="4c37a-125">Beispielsweise werden Sie sicher, dass Ihre Startprogramm eine offensichtliche hinreichend repräsentativ für Ihre app, dass sie für einen Teil der Decor in das Cliff House verwechselt werden, wird nicht.</span><span class="sxs-lookup"><span data-stu-id="4c37a-125">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="4c37a-126">Ihre app-Startfeld soll Personen Touch/es auswählen einladen.</span><span class="sxs-lookup"><span data-stu-id="4c37a-126">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="4c37a-127">![Beispiel: Neue Notiz-3D-app-Startfeld](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4c37a-127">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="4c37a-128">*Neue Notiz 3D-Startprogramm-Beispiel-app (fiktive app)*</span><span class="sxs-lookup"><span data-stu-id="4c37a-128">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="4c37a-129">Home-Skalierung</span><span class="sxs-lookup"><span data-stu-id="4c37a-129">Home scale</span></span>

<span data-ttu-id="4c37a-130">3D app-startfeldern von befinden sich in der Cliff House und deren Standardgröße sollten Sinn für die anderen "physical" Objekte im Bereich.</span><span class="sxs-lookup"><span data-stu-id="4c37a-130">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="4c37a-131">Wenn Sie Ihre Startprogramm neben, z. B. platzieren, sollte eine Anlage Haus oder einige Möbel, kommt es Ihnen zu Hause, size-wise.</span><span class="sxs-lookup"><span data-stu-id="4c37a-131">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="4c37a-132">Ein guter Ausgangspunkt ist zu sehen, wie es unter 30 kubische Zentimeter aussieht, aber denken Sie daran, dass der Benutzer es nach oben oder unten skaliert werden können, wenn sie z. B.</span><span class="sxs-lookup"><span data-stu-id="4c37a-132">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="4c37a-133">Besitzer-fähig</span><span class="sxs-lookup"><span data-stu-id="4c37a-133">Own-able</span></span>

<span data-ttu-id="4c37a-134">Das app-Startfeld sollte wie ein Objekt sein, die eine Person sein, würde gerne in seinem Bereich verfügen.</span><span class="sxs-lookup"><span data-stu-id="4c37a-134">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="4c37a-135">Sie werden praktisch umgebenden werden selbst mit diesen, sodass das Startprogramm wie etwas funktioniert der Gedanke Benutzer war wünschenswert genug ist, lesen, und behalten Sie in der Nähe.</span><span class="sxs-lookup"><span data-stu-id="4c37a-135">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="4c37a-136">![Beispiel: Astro Warp-3D-app-Startfeld](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4c37a-136">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="4c37a-137">*Beispiel für die Astro Warp 3D app-Startprogramm (fiktive app)*</span><span class="sxs-lookup"><span data-stu-id="4c37a-137">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="4c37a-138">Erkannt</span><span class="sxs-lookup"><span data-stu-id="4c37a-138">Recognizable</span></span>

<span data-ttu-id="4c37a-139">Ihre 3D app-Startfeld sollte sofort "Ihrer app-Brand" Personen Ausdrücken anzeigen.</span><span class="sxs-lookup"><span data-stu-id="4c37a-139">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="4c37a-140">Wenn Sie ein Stern Zeichen oder ein besonders identifizierbaren Objekt in Ihrer app haben, empfehlen wir, verwenden, wie ein großer Teil des Entwurfs.</span><span class="sxs-lookup"><span data-stu-id="4c37a-140">If you have a star character or an especially identifiable object in your app, we recommend using that as a big part of your design.</span></span> <span data-ttu-id="4c37a-141">In einer Welt mixed Reality wird ein Objekt größerem Interesse von Benutzern als nur ein Logo, die allein gezeichnet.</span><span class="sxs-lookup"><span data-stu-id="4c37a-141">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="4c37a-142">Erkennbare Objekten kommunizieren Marke, schnell und deutlich.</span><span class="sxs-lookup"><span data-stu-id="4c37a-142">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="4c37a-143">Volumetrische</span><span class="sxs-lookup"><span data-stu-id="4c37a-143">Volumetric</span></span>

<span data-ttu-id="4c37a-144">Ihre app sollte mehr als nur Ihr Logo in eine flache Ebene platzieren und Aufrufen von Feierabend.</span><span class="sxs-lookup"><span data-stu-id="4c37a-144">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="4c37a-145">Ihre Startprogramm sollte wie ein aufregende, 3D, physische Objekt im Bereich für den Benutzer fühlen.</span><span class="sxs-lookup"><span data-stu-id="4c37a-145">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="4c37a-146">Ein guter Ansatz ist vorstellbar, dass Ihre app würde eine Sprechblase in die Macys Thanksgiving-Tag Schlag zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="4c37a-146">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="4c37a-147">Fragen Sie sich, würde wie Personen wirklich wow, wie sie die Straße stammt?</span><span class="sxs-lookup"><span data-stu-id="4c37a-147">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="4c37a-148">Was würde aus allen Winkeln der Anzeige hervorragend aussehen?</span><span class="sxs-lookup"><span data-stu-id="4c37a-148">What would look great from all viewing angles?</span></span>


:::row:::
    :::column:::
        ![Logo only](images/20171016-140436-mixedreality-640px.jpg)
        *Logo only*
    :::column-end:::
    :::column:::
        ![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg)
        *More recognizable with a character*
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        ![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg)
        *Flat approach, not surprisingly, feels flat*
    :::column-end:::
    :::column:::
        ![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg)
        *Volumetric approach better showcases your app*
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a><span data-ttu-id="4c37a-149">Tipps für gute 3D-Modelle</span><span class="sxs-lookup"><span data-stu-id="4c37a-149">Tips for good 3D models</span></span>

### <a name="best-practices"></a><span data-ttu-id="4c37a-150">Empfohlene Methoden</span><span class="sxs-lookup"><span data-stu-id="4c37a-150">Best practices</span></span>
* <span data-ttu-id="4c37a-151">Bei der Planung von Dimensionen für Ihre app-Startfeld Schießen Sie für ungefähr einen 30-cm-Cube ein.</span><span class="sxs-lookup"><span data-stu-id="4c37a-151">When planning dimensions for your app launcher, shoot for roughly a 30cm cube.</span></span> <span data-ttu-id="4c37a-152">Also eine 1: von 1:1-Größenverhältnis.</span><span class="sxs-lookup"><span data-stu-id="4c37a-152">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="4c37a-153">Modelle müssen weniger als 10.000 Polygone sein.</span><span class="sxs-lookup"><span data-stu-id="4c37a-153">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="4c37a-154">Weitere Informationen zum Dreieck Anzahlen und weitere Details (LODs)</span><span class="sxs-lookup"><span data-stu-id="4c37a-154">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="4c37a-155">Testen Sie auf eine immersive Kopfhörer, sofern möglich.</span><span class="sxs-lookup"><span data-stu-id="4c37a-155">Test on an immersive headset when possible.</span></span>
* <span data-ttu-id="4c37a-156">Details in die Geometrie des Modells zu erstellen, wenn möglich – verlassen Sie sich nicht auf Texturen für Details.</span><span class="sxs-lookup"><span data-stu-id="4c37a-156">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="4c37a-157">Erstellen Sie "Kate enge" geschlossen Geometrie.</span><span class="sxs-lookup"><span data-stu-id="4c37a-157">Build “water tight” closed geometry.</span></span> <span data-ttu-id="4c37a-158">Keine Lücken aufweisen, die nicht im modelliert werden.</span><span class="sxs-lookup"><span data-stu-id="4c37a-158">No holes that are not modeled in.</span></span>
* <span data-ttu-id="4c37a-159">Verwenden Sie natürliche Materialien in Ihr Objekt an.</span><span class="sxs-lookup"><span data-stu-id="4c37a-159">Use natural materials in your object.</span></span> <span data-ttu-id="4c37a-160">Stellen Sie sich vor, erstellen sie in der realen Welt.</span><span class="sxs-lookup"><span data-stu-id="4c37a-160">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="4c37a-161">Stellen Sie sicher, dass das Modell gut bei verschiedenen Abstände und Größen liest.</span><span class="sxs-lookup"><span data-stu-id="4c37a-161">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="4c37a-162">Wenn das Modell fertig ist, lesen die [Assets Richtlinien exportieren](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span><span class="sxs-lookup"><span data-stu-id="4c37a-162">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="4c37a-163">![Modell mit den feinen Details in der Textur](images/20171013-143334-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4c37a-163">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="4c37a-164">*Modell mit den feinen Details in der Textur*</span><span class="sxs-lookup"><span data-stu-id="4c37a-164">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="4c37a-165">Was Sie vermeiden sollten</span><span class="sxs-lookup"><span data-stu-id="4c37a-165">What to avoid</span></span>
* <span data-ttu-id="4c37a-166">Verwenden Sie keine Details mit hohem Kontrast oder Muster für kleine, ausgelastet und Texturen.</span><span class="sxs-lookup"><span data-stu-id="4c37a-166">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="4c37a-167">Verwenden Sie keine thin Geometrie – nicht und funktioniert auch mit einer Entfernung alias ungültig wird.</span><span class="sxs-lookup"><span data-stu-id="4c37a-167">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="4c37a-168">Teilen des Modells erweitern lassen nicht zu viel über die 1: von 1:1-Größenverhältnis.</span><span class="sxs-lookup"><span data-stu-id="4c37a-168">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="4c37a-169">Skalierungsproblemen wird erstellt.</span><span class="sxs-lookup"><span data-stu-id="4c37a-169">It will create scaling problems.</span></span>

<span data-ttu-id="4c37a-170">![Vermeiden von hohem Kontrast, kleine ausgelastet Muster](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4c37a-170">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="4c37a-171">*Vermeiden von hohem Kontrast, kleine, gebucht Muster*</span><span class="sxs-lookup"><span data-stu-id="4c37a-171">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="4c37a-172">Das Durchführen von Typ</span><span class="sxs-lookup"><span data-stu-id="4c37a-172">How to handle type</span></span>

### <a name="best-practices"></a><span data-ttu-id="4c37a-173">Empfohlene Methoden</span><span class="sxs-lookup"><span data-stu-id="4c37a-173">Best practices</span></span>
* <span data-ttu-id="4c37a-174">Es wird empfohlen, dass Ihr Typ ca. 1/3-Ihrer-app-Startfeld (oder mehr) umfasst.</span><span class="sxs-lookup"><span data-stu-id="4c37a-174">We recommend your type comprises about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="4c37a-175">Der Typ ist der wichtigste Aspekt besteht, die Benutzer eine Vorstellung, die Ihre Startprogramm tatsächlich ein Startprogramm erhalten ist, daher ist es gut ist dies ganz erhebliche.</span><span class="sxs-lookup"><span data-stu-id="4c37a-175">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s pretty substantial.</span></span>
* <span data-ttu-id="4c37a-176">Vermeiden, dass sehr breit Typ – versuchen, die sie innerhalb der Grenzen des app-startfeldern Core Dimensionen (mehr oder weniger) beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="4c37a-176">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="4c37a-177">Flatfiles kann funktionieren, aber beachten Sie, dass es zum Anzeigen von bestimmten Winkel und in bestimmten Umgebungen schwierig sein kann.</span><span class="sxs-lookup"><span data-stu-id="4c37a-177">Flat type can work, but be aware that it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="4c37a-178">Sie sollten erwägen, platzieren es ein solid Objekt oder eine Backdrop dahinter helfen.</span><span class="sxs-lookup"><span data-stu-id="4c37a-178">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="4c37a-179">Hinzufügen von Dimension in den Typ fühlt gut in 3D.</span><span class="sxs-lookup"><span data-stu-id="4c37a-179">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="4c37a-180">Schattierung die Seiten des Typs können eine andere, je dunkler Farbe für die Lesbarkeit.</span><span class="sxs-lookup"><span data-stu-id="4c37a-180">Shading the sides of the type a different, darker color can help with readability.</span></span>


:::row:::
    :::column:::
        ![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png)
        *Flat type without a backdrop can be hard to view from certain angles and in certain environments*
    :::column-end:::
    :::column:::
        ![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png)
        *Type with a built-in backdrop can work well*
    :::column-end:::
    :::column:::
        ![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg)
        *Extruded type can work well if you shade the sides*
    :::column-end:::
:::row-end:::


<span data-ttu-id="4c37a-181">**Typ-Farben, die funktionieren**</span><span class="sxs-lookup"><span data-stu-id="4c37a-181">**Type colors that work**</span></span>
* <span data-ttu-id="4c37a-182">Weiß</span><span class="sxs-lookup"><span data-stu-id="4c37a-182">White</span></span>
* <span data-ttu-id="4c37a-183">Schwarz</span><span class="sxs-lookup"><span data-stu-id="4c37a-183">Black</span></span>
* <span data-ttu-id="4c37a-184">Helle teilweise farbsättigung</span><span class="sxs-lookup"><span data-stu-id="4c37a-184">Bright semi-saturated color</span></span>

<span data-ttu-id="4c37a-185">![Geben Sie Farben, die funktionieren.](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4c37a-185">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="4c37a-186">*Typ-Farben, die funktionieren*</span><span class="sxs-lookup"><span data-stu-id="4c37a-186">*Type colors that work*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="4c37a-187">Was Sie vermeiden sollten</span><span class="sxs-lookup"><span data-stu-id="4c37a-187">What to avoid</span></span>

<span data-ttu-id="4c37a-188">**Typ-Farben, die Probleme verursachen.**</span><span class="sxs-lookup"><span data-stu-id="4c37a-188">**Type colors that cause trouble**</span></span>
* <span data-ttu-id="4c37a-189">Mid-Töne</span><span class="sxs-lookup"><span data-stu-id="4c37a-189">Mid-tones</span></span>
* <span data-ttu-id="4c37a-190">Grau</span><span class="sxs-lookup"><span data-stu-id="4c37a-190">Gray</span></span>
* <span data-ttu-id="4c37a-191">Übermäßige Sättigung Farben oder entsättigte Farben</span><span class="sxs-lookup"><span data-stu-id="4c37a-191">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="4c37a-192">![Geben Sie Farben, die Probleme verursachen.](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4c37a-192">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="4c37a-193">*Typ-Farben, die Probleme verursachen.*</span><span class="sxs-lookup"><span data-stu-id="4c37a-193">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="4c37a-194">Beleuchtung</span><span class="sxs-lookup"><span data-stu-id="4c37a-194">Lighting</span></span>

<span data-ttu-id="4c37a-195">Die Beleuchtung für Ihre app-Startfeld stammt aus der Cliff House-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="4c37a-195">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="4c37a-196">Achten Sie darauf, um Ihre Startprogramm an mehreren Stellen im gesamten Haus zu testen, damit es in Ordnung ist in Licht und Schatten.</span><span class="sxs-lookup"><span data-stu-id="4c37a-196">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="4c37a-197">Die gute Nachricht ist, Ihre Startprogramm auf ziemlich guten Zustand für die meisten Beleuchtung in der Cliff House sein soll, wenn Sie die anderen Entwurfsrichtlinien, die Sie in diesem Dokument ausgeführt haben, an.</span><span class="sxs-lookup"><span data-stu-id="4c37a-197">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in pretty good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="4c37a-198">Testen die Darstellung Ihrer Startprogramm in der verschiedenen Lichter in der Umgebung bieten gute Einstiegspunkte sind der Studio Media Raum außerhalb von überall und im Garten zurück (der konkreten Bereich mit den Rasen).</span><span class="sxs-lookup"><span data-stu-id="4c37a-198">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="4c37a-199">Ein weiterer guter Test ist, fügen Sie ihn in die halbe Licht und halbe Schatten und wie es aussieht.</span><span class="sxs-lookup"><span data-stu-id="4c37a-199">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="4c37a-200">![Stellen Sie sicher, dass Ihre Startprogramm in Licht und Schatten in Ordnung ist.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4c37a-200">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="4c37a-201">*Stellen Sie sicher, dass Ihre Startprogramm in Licht und Schatten in Ordnung ist*</span><span class="sxs-lookup"><span data-stu-id="4c37a-201">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="4c37a-202">Texturen</span><span class="sxs-lookup"><span data-stu-id="4c37a-202">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="4c37a-203">Erstellen Ihre Texturen</span><span class="sxs-lookup"><span data-stu-id="4c37a-203">Authoring your textures</span></span>

<span data-ttu-id="4c37a-204">Das End-Format, der Ihre-3D-app-Startfeld werden eine .glb-Datei, die erfolgt über die Pipeline PBR (physisch basierten Rendern).</span><span class="sxs-lookup"><span data-stu-id="4c37a-204">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="4c37a-205">Dies liegt möglicherweise eine komplizierte Prozess – jetzt ein guter Zeitpunkt, einen technischen Interpreten einsetzen, sofern Sie noch nicht geschehen ist.</span><span class="sxs-lookup"><span data-stu-id="4c37a-205">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="4c37a-206">Eine mutig DIY-er haben sich die Zeit nehmen [untersuchen und lernen Sie die PBR Terminologie](http://wiki.polycount.com/wiki/PBR) und was im Hintergrund geschieht, bevor Sie beginnen, können Sie häufige Fehler zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="4c37a-206">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](http://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="4c37a-207">![Beispiel: Neue Notiz-app](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="4c37a-207">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="4c37a-208">*Neue Notiz 3D-Startprogramm-Beispiel-app (fiktive app)*</span><span class="sxs-lookup"><span data-stu-id="4c37a-208">*Fresh Note 3D app launcher example (fictional app)*</span></span>

<span data-ttu-id="4c37a-209">**Empfohlene authoring tool**</span><span class="sxs-lookup"><span data-stu-id="4c37a-209">**Recommended authoring tool**</span></span>

<span data-ttu-id="4c37a-210">Es wird empfohlen, [Substanz übertragen](https://www.allegorithmic.com/products/substance-painter) von Allegorithmic Ihrer endgültige Datei zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="4c37a-210">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="4c37a-211">Wenn Sie nicht mit der Erstellung von PBR-Shader in Substanz übertragen, hier die vertraut sind eine [Tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span><span class="sxs-lookup"><span data-stu-id="4c37a-211">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="4c37a-212">(Alternativ [-3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), oder [Marmoset Toolbag](https://www.marmoset.co/toolbag/) würde auch funktionieren, wenn Sie mehr mit einer dieser vertraut.)</span><span class="sxs-lookup"><span data-stu-id="4c37a-212">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="4c37a-213">Empfohlene Methoden</span><span class="sxs-lookup"><span data-stu-id="4c37a-213">Best practices</span></span>

* <span data-ttu-id="4c37a-214">Wenn Ihre app-Startprogramm-Objekt für PBR erstellt wurde, sollte es ziemlich einfach, für die Umgebung Cliff House konvertieren.</span><span class="sxs-lookup"><span data-stu-id="4c37a-214">If your app launcher object was authored for PBR, it should be pretty straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="4c37a-215">Unsere Shader-Metal-Computern/Rauigkeit Workflow erwartet – die Unreal PBR Shader ist schließen anzeigte verwenden.</span><span class="sxs-lookup"><span data-stu-id="4c37a-215">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="4c37a-216">Beim Exportieren Ihre Texturen behalten die [empfohlene Größen der Textur](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) Bedenken.</span><span class="sxs-lookup"><span data-stu-id="4c37a-216">When exporting your textures keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="4c37a-217">Stellen Sie sicher, dass Sie Ihre Objekte in Echtzeit Beleuchtung erstellen – Dies bedeutet:</span><span class="sxs-lookup"><span data-stu-id="4c37a-217">Make sure to build your objects for real-time lighting — this means:</span></span>
    * <span data-ttu-id="4c37a-218">Vermeiden Sie mitgelieferten Shadows – oder gezeichnete Schatten</span><span class="sxs-lookup"><span data-stu-id="4c37a-218">Avoid baked shadows – or painted shadows</span></span>
    * <span data-ttu-id="4c37a-219">Vermeiden Sie die mitgelieferten Beleuchtung in die Texturen</span><span class="sxs-lookup"><span data-stu-id="4c37a-219">Avoid baked lighting in the textures</span></span>
    * <span data-ttu-id="4c37a-220">Verwenden Sie eine der das PBR-Material, das Erstellen von Paketen, um die richtigen Zuordnungen für unseren Shader generiert zu erhalten</span><span class="sxs-lookup"><span data-stu-id="4c37a-220">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="4c37a-221">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4c37a-221">See also</span></span>

* [<span data-ttu-id="4c37a-222">Erstellen von 3D-Modellen für die Verwendung in der mixed Reality home</span><span class="sxs-lookup"><span data-stu-id="4c37a-222">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="4c37a-223">Implementieren von 3D app-startfeldern von (UWP-apps)</span><span class="sxs-lookup"><span data-stu-id="4c37a-223">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="4c37a-224">Implementieren von 3D app-startfeldern von (Win32-apps)</span><span class="sxs-lookup"><span data-stu-id="4c37a-224">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
