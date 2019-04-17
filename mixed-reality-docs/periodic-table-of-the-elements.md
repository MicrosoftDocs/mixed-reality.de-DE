---
title: Periodisch-Tabelle der Elemente
description: Periodisch-Tabelle der Elemente ist ein Open-Source-Beispiel-app in den Microsoft gemischte Realität Entwurf Labs, erfahren Sie, wie ein Array von Objekten im 3D-Raum mit verschiedenen Surface-Typen, die mit einer objektauflistung Layout können.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, entwerfen, die Beispiel-app, die Steuerelemente
ms.openlocfilehash: ad95d2bcfd1b70d805adcceb36be0c6c29b838f0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596693"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="0c56f-104">Periodisch-Tabelle der Elemente</span><span class="sxs-lookup"><span data-stu-id="0c56f-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="0c56f-105">Dieser Artikel beschreibt ein Beispiel für eine explorative wir, in erstellt haben der [Mixed Reality Entwurf Labs](https://github.com/Microsoft/MRDesignLabs_Unity), einen Ort, in dem wir der Erkenntnisse zu teilen, und Vorschläge für mixed Reality-app-Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="0c56f-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="0c56f-106">Wenn wir neue Erkenntnisse vornehmen weiterentwickelt unser Entwurf bezogenen Artikeln und Code.</span><span class="sxs-lookup"><span data-stu-id="0c56f-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="0c56f-107">[Periodisch-Tabelle der Elemente](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) ist eine Open-Source Beispielapp von den Microsoft Mixed Reality Entwurf Labs.</span><span class="sxs-lookup"><span data-stu-id="0c56f-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="0c56f-108">Bei diesem Projekt erfahren Sie, wie ein Array von Objekten im 3D-Raum mit verschiedenen Oberflächentypen mit Layout ein  **[-objektauflistung](object-collection.md)**.</span><span class="sxs-lookup"><span data-stu-id="0c56f-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](object-collection.md)**.</span></span> <span data-ttu-id="0c56f-109">Außerdem erfahren Sie, wie es Objekte erstellen, die auf standardmäßigen Eingaben von HoloLens reagieren.</span><span class="sxs-lookup"><span data-stu-id="0c56f-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="0c56f-110">Sie können dieses Projekts Komponenten verwenden, zum Erstellen eines eigenen mixed Reality-app-Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="0c56f-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Punkt-Tabelle der Elemente-app](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a><span data-ttu-id="0c56f-112">Informationen zur app</span><span class="sxs-lookup"><span data-stu-id="0c56f-112">About the app</span></span>

<span data-ttu-id="0c56f-113">Periodisch-Tabelle der Elemente visualisiert chemischen Elemente und ihre Eigenschaften in einem 3D-Raum.</span><span class="sxs-lookup"><span data-stu-id="0c56f-113">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="0c56f-114">Es umfasst die grundlegenden Interaktionen von HoloLens wie Blicke und Air, tippen Sie auf.</span><span class="sxs-lookup"><span data-stu-id="0c56f-114">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="0c56f-115">Benutzer erhalten weitere Informationen zu den Elementen mit animierte 3D-Modellen.</span><span class="sxs-lookup"><span data-stu-id="0c56f-115">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="0c56f-116">Sie können visuell verstehen, ein Element den Electron-Shell und seine Kernstück - das Protons und Neutrons besteht.</span><span class="sxs-lookup"><span data-stu-id="0c56f-116">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="0c56f-117">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="0c56f-117">Background</span></span>

<span data-ttu-id="0c56f-118">Nach dem ersten HoloLens habe, war einer periodisch-Tabellen-app eine Idee, die ich wusste, ich zum Experimentieren mit in mixed Reality wollte.</span><span class="sxs-lookup"><span data-stu-id="0c56f-118">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="0c56f-119">Da jedes Element über viele Datenpunkte, die mit dem Text angezeigt werden verfügt, dachte ich, dass es gute fachlicher zum Untersuchen von typografischen Komposition in einem 3D-Raum wäre.</span><span class="sxs-lookup"><span data-stu-id="0c56f-119">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="0c56f-120">Wird das Element den Electron-Modell visualisieren wurde eine andere interessante Teil des Projekts.</span><span class="sxs-lookup"><span data-stu-id="0c56f-120">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="0c56f-121">Entwurf</span><span class="sxs-lookup"><span data-stu-id="0c56f-121">Design</span></span>

<span data-ttu-id="0c56f-122">Für die Standardansicht der Tabelle periodisch undenkbar ich dreidimensionalen Felder, die den Electron-Modell der einzelnen Elemente enthält.</span><span class="sxs-lookup"><span data-stu-id="0c56f-122">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="0c56f-123">Die Oberfläche des jedes Feld wäre, sodass der Benutzer eine grobe Vorstellung des Elements Volumes konnte lichtdurchlässiger.</span><span class="sxs-lookup"><span data-stu-id="0c56f-123">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="0c56f-124">Mit Blicke "und" Air-tippen kann der Benutzer eine detaillierte Ansicht der einzelnen Elemente öffnen.</span><span class="sxs-lookup"><span data-stu-id="0c56f-124">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="0c56f-125">Um den Übergang zwischen Tabelle und Detailansicht smooth und natürliche machen, war ich es vergleichbar mit der physischen Interaktion eines Felds aus, öffnen in der Praxis.</span><span class="sxs-lookup"><span data-stu-id="0c56f-125">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="0c56f-126">![Design-Sketches](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="0c56f-126">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="0c56f-127">*Entwurf einen groben Entwurf*</span><span class="sxs-lookup"><span data-stu-id="0c56f-127">*Design sketches*</span></span>

<span data-ttu-id="0c56f-128">In der Detailansicht wollte ich die Informationen der einzelnen Elemente mit beeindruckend dargestellte Text im 3D-Raum zu visualisieren.</span><span class="sxs-lookup"><span data-stu-id="0c56f-128">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="0c56f-129">Das animierte 3D Electron-Modell wird im mittleren Bereich angezeigt, und es kann aus verschiedenen Blickwinkeln angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="0c56f-129">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![Interaktion](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="0c56f-131">![Prototypen](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="0c56f-131">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="0c56f-132">*Interaktion von Prototypen*</span><span class="sxs-lookup"><span data-stu-id="0c56f-132">*Interaction prototypes*</span></span>

<span data-ttu-id="0c56f-133">Der Benutzer kann den Surface-Typ in der Luft durch Tippen auf die Schaltflächen am unteren Rand der Tabelle ändern: sie können zwischen Plane, Zylinder, Kugel und Punkt (XY) wechseln.</span><span class="sxs-lookup"><span data-stu-id="0c56f-133">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="0c56f-134">Allgemeine Steuerelemente und Muster, die in dieser app verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0c56f-134">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="0c56f-135">Es Objekt (Schaltfläche)</span><span class="sxs-lookup"><span data-stu-id="0c56f-135">Interactable object (button)</span></span>

<span data-ttu-id="0c56f-136">[Es Objekt](interactable-object.md) ist ein Objekt, das grundlegende HoloLens Eingaben reagieren kann.</span><span class="sxs-lookup"><span data-stu-id="0c56f-136">[Interactable object](interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="0c56f-137">Er wird als Prefab/Skript bereitgestellt, die einfach auf ein beliebiges Objekt angewendet werden können.</span><span class="sxs-lookup"><span data-stu-id="0c56f-137">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="0c56f-138">Sie können z. B. stellen eine Tasse Kaffee für die es in Ihrer Szene und reagieren auf Eingaben wie z. B. Blicke, tippen Sie auf, die Datennavigation und-Bearbeitung Gesten.</span><span class="sxs-lookup"><span data-stu-id="0c56f-138">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="0c56f-139">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0c56f-139">Learn more</span></span>](interactable-object.md)

![Nteractable-Objekt](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="0c56f-141">Eine objektauflistung</span><span class="sxs-lookup"><span data-stu-id="0c56f-141">Object collection</span></span>

<span data-ttu-id="0c56f-142">[-Objektauflistung](object-collection.md) ist ein Objekt, das die können Sie mehrere Objekte in verschiedenen Formen anordnen.</span><span class="sxs-lookup"><span data-stu-id="0c56f-142">[Object collection](object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="0c56f-143">Datenebene, Zylinder, Kugel und Punkt (XY) unterstützt.</span><span class="sxs-lookup"><span data-stu-id="0c56f-143">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="0c56f-144">Sie können zusätzliche Eigenschaften wie z. B. Radius, Anzahl der Zeilen und den Abstand konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="0c56f-144">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="0c56f-145">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0c56f-145">Learn more</span></span>](object-collection.md)

![Eine objektauflistung](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a><span data-ttu-id="0c56f-147">Fitbox</span><span class="sxs-lookup"><span data-stu-id="0c56f-147">Fitbox</span></span>

<span data-ttu-id="0c56f-148">In der Standardeinstellung die Hologramme platziert werden, an dem Speicherort, in denen der Benutzer gazing ist, derzeit die Anwendung wird gestartet.</span><span class="sxs-lookup"><span data-stu-id="0c56f-148">By default, holograms will be placed in the location where the user is gazing at the moment the application is launched.</span></span> <span data-ttu-id="0c56f-149">Dies führt gelegentlich zu unerwünschten Ergebnis wie z. B. Hologramme hinter einer Wand oder in der Mitte einer Tabelle platziert wird.</span><span class="sxs-lookup"><span data-stu-id="0c56f-149">This sometimes leads to unwanted result such as holograms being placed behind a wall or in the middle of a table.</span></span> <span data-ttu-id="0c56f-150">Eine Fitbox kann einen Benutzer Blicke zu verwenden, um den Speicherort zu bestimmen, in denen die Hologramm platziert werden.</span><span class="sxs-lookup"><span data-stu-id="0c56f-150">A fitbox allows a user to use gaze to determine the location where the hologram will be placed.</span></span> <span data-ttu-id="0c56f-151">Es erfolgt mit einer einfachen PNG-Bild-Textur, die problemlos mit Ihrer eigenen Images oder 3D-Objekte angepasst werden können.</span><span class="sxs-lookup"><span data-stu-id="0c56f-151">It is made with a simple PNG image texture which can be easily customized with your own images or 3D objects.</span></span>

![Fitbox](images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a><span data-ttu-id="0c56f-153">Technische Details</span><span class="sxs-lookup"><span data-stu-id="0c56f-153">Technical details</span></span>

<span data-ttu-id="0c56f-154">Finden Sie Skripts und prefabs (Vorlagen) für die Tabelle periodisch der app Elemente auf der [Mixed Reality-Design-Labs-GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span><span class="sxs-lookup"><span data-stu-id="0c56f-154">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="application-examples"></a><span data-ttu-id="0c56f-155">Beispiele für die Anwendung</span><span class="sxs-lookup"><span data-stu-id="0c56f-155">Application examples</span></span>

<span data-ttu-id="0c56f-156">Hier sind einige Ideen für das was Sie durch die Nutzung der Komponenten in diesem Projekt erstellen können.</span><span class="sxs-lookup"><span data-stu-id="0c56f-156">Here are some ideas for what you could create by leveraging the components in this project.</span></span>

### <a name="stock-data-visualization-app"></a><span data-ttu-id="0c56f-157">Vordefinierte datenvisualisierungs-app</span><span class="sxs-lookup"><span data-stu-id="0c56f-157">Stock data visualization app</span></span>

<span data-ttu-id="0c56f-158">Verwenden die gleichen Steuerelemente und das Interaktionsmodell, wie in der Tabelle periodisch des Beispiels Elemente, können Sie eine app erstellen, die Börsendaten visualisiert.</span><span class="sxs-lookup"><span data-stu-id="0c56f-158">Using the same controls and interaction model as the Periodic Table of the Elements sample, you could build an app which visualizes stock market data.</span></span> <span data-ttu-id="0c56f-159">Dieses Beispiel verwendet die Steuerung der Datensammlung Objekt, um das Layout von Aktiendaten in einer sphärischen Form.</span><span class="sxs-lookup"><span data-stu-id="0c56f-159">This example uses the Object collection control to lay out stock data in a spherical shape.</span></span> <span data-ttu-id="0c56f-160">Sie können es sich um eine Detailansicht vorstellen, wo zusätzliche Informationen zu jeder Aktie auf interessante Weise angezeigt werden kann.</span><span class="sxs-lookup"><span data-stu-id="0c56f-160">You can imagine a detail view where additional information about each stock could be displayed in an interesting way.</span></span>

![Beispiel: Finance (1 von 3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![Beispiel: Finance (2 von 3)](images/640px-periodictable-applicationexamples-finance2.jpg)

<span data-ttu-id="0c56f-163">![Beispiel: Finance (3 von 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span><span class="sxs-lookup"><span data-stu-id="0c56f-163">![Application example: Finance (3 of 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span></span><br>
<span data-ttu-id="0c56f-164">*Verdeutlicht, wie die objektauflistung, die in der Tabelle periodisch Elemente-Beispiel-App verwendet, in einer Finance-app verwendet werden kann*</span><span class="sxs-lookup"><span data-stu-id="0c56f-164">*An example of how the Object collection used in the Periodic Table of the Elements sample app could be used in a finance app*</span></span>

### <a name="sports-app"></a><span data-ttu-id="0c56f-165">Sport-app</span><span class="sxs-lookup"><span data-stu-id="0c56f-165">Sports app</span></span>

<span data-ttu-id="0c56f-166">Dies ist ein Beispiel mit objektauflistung und anderen Komponenten aus der Tabelle periodisch der Beispiel-app Elemente Sport-Daten zu visualisieren.</span><span class="sxs-lookup"><span data-stu-id="0c56f-166">This is an example of visualizing sports data using Object collection and other components from the Periodic Table of the Elements sample app.</span></span>

![Beispiel: Sport (1 von 3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![Beispiel: Sport (2 von 3)](images/640px-periodictable-applicationexamples-sports1.jpg)

<span data-ttu-id="0c56f-169">![Beispiel: Sport (3 von 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span><span class="sxs-lookup"><span data-stu-id="0c56f-169">![Application example: Sports (3 of 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span></span><br>
<span data-ttu-id="0c56f-170">*Ein Beispiel für die objektauflistung wie in der Tabelle periodisch die Beispiel-Appcould Elemente verwendet, die in einer Sport-app verwendet werden*</span><span class="sxs-lookup"><span data-stu-id="0c56f-170">*An example of how the Object collection used in the Periodic Table of the Elements sample appcould be used in a sports app*</span></span>

## <a name="about-the-author"></a><span data-ttu-id="0c56f-171">Der Autor</span><span class="sxs-lookup"><span data-stu-id="0c56f-171">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="0c56f-172"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="0c56f-172"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="0c56f-173">UX-Designer @Microsoft</span><span class="sxs-lookup"><span data-stu-id="0c56f-173">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="0c56f-174">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0c56f-174">See also</span></span>

* [<span data-ttu-id="0c56f-175">Es-Objekt</span><span class="sxs-lookup"><span data-stu-id="0c56f-175">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="0c56f-176">Eine objektauflistung</span><span class="sxs-lookup"><span data-stu-id="0c56f-176">Object collection</span></span>](object-collection.md)
