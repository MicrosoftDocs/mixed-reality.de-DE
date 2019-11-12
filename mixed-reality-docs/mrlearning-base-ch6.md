---
title: Tutorials zu den ersten Schritten-7. Erstellen einer Beispielanwendung für ein Mond Modul
description: In dieser Lektion kombinieren Sie mehrere Konzepte, die Sie aus vorherigen Lektionen gelernt haben, um eine einzigartige Stichprobe zu erstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: b033e4f9a379fb1778da3d94da70262e073d141b
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926522"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="ffe08-105">7. Erstellen einer Beispielanwendung für ein Mond Modul</span><span class="sxs-lookup"><span data-stu-id="ffe08-105">7. Creating a Lunar Module sample application</span></span>

<span data-ttu-id="ffe08-106">In diesem Tutorial werden mehrere Konzepte aus früheren Lektionen kombiniert, um ein eindeutiges Beispiel zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ffe08-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="ffe08-107">Sie erfahren, wie Sie eine Anwendung für eine Mond Modul Assembly erstellen, bei der ein Benutzer überwachte Hände zum Abrufen von Mond Modul teilen und zum Anfügen eines mondmoduls verwenden muss.</span><span class="sxs-lookup"><span data-stu-id="ffe08-107">You will learn how to create a lunar module assembly application whereby a user needs to use tracked hands to pick up lunar module parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="ffe08-108">Mithilfe von druckbaren Schaltflächen können Sie Platzierungs Hinweise umschalten, die Leistung zurücksetzen und das Mond Modul in den Raum bringen!</span><span class="sxs-lookup"><span data-stu-id="ffe08-108">We use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="ffe08-109">In zukünftigen Tutorials werden wir weiterhin auf dieser Benutzer Funktionalität aufbauen, die leistungsstarke Mehrzweck-Anwendungsfälle umfasst, die räumliche Azure-Anker für räumliche Ausrichtung nutzen.</span><span class="sxs-lookup"><span data-stu-id="ffe08-109">In future tutorials, we will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="ffe08-110">Ziele</span><span class="sxs-lookup"><span data-stu-id="ffe08-110">Objectives</span></span>

- <span data-ttu-id="ffe08-111">Kombinieren mehrerer Konzepte aus früheren Lektionen, um eine einzigartige Umgebung zu schaffen</span><span class="sxs-lookup"><span data-stu-id="ffe08-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="ffe08-112">Informationen zum Umschalten von Objekten</span><span class="sxs-lookup"><span data-stu-id="ffe08-112">Learn how to toggle objects</span></span>
- <span data-ttu-id="ffe08-113">Auslösen komplexer Ereignisse über drückbare Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="ffe08-113">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="ffe08-114">Verwenden der physischen Effekte und Kräfte von Starrkörpern</span><span class="sxs-lookup"><span data-stu-id="ffe08-114">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="ffe08-115">Erkunden der Verwendung von QuickInfos</span><span class="sxs-lookup"><span data-stu-id="ffe08-115">Explore the use of tool tips</span></span>

## <a name="instructions"></a><span data-ttu-id="ffe08-116">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="ffe08-116">Instructions</span></span>

### <a name="configuring-the-lunar-module"></a><span data-ttu-id="ffe08-117">Konfigurieren der Mondlandefähre</span><span class="sxs-lookup"><span data-stu-id="ffe08-117">Configuring the Lunar Module</span></span>

<span data-ttu-id="ffe08-118">In diesem Abschnitt werden die verschiedenen Komponenten vorgestellt, die zum Erstellen unserer Beispiel Funktionen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="ffe08-118">In this section, we introduce the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="ffe08-119">Fügen Sie der Basis Szene die vorfab-Assembly für das Mondmodul hinzu.</span><span class="sxs-lookup"><span data-stu-id="ffe08-119">Add the Lunar Module Assembly prefab to your base scene.</span></span> <span data-ttu-id="ffe08-120">Navigieren Sie zu diesem Zweck auf der Registerkarte Projekt zu Assets > basemoduleassets > Prefabs.</span><span class="sxs-lookup"><span data-stu-id="ffe08-120">To do this, in the Project tab navigate to Assets > BaseModuleAssets > Prefabs.</span></span> <span data-ttu-id="ffe08-121">Sie sehen zwei Prefabs für das Raketenstart Programm, ziehen Sie die Launcher_Tutorial Prefab in ihre Szene, und positionieren Sie Sie wie gewünscht.</span><span class="sxs-lookup"><span data-stu-id="ffe08-121">You will see two rocket launcher prefabs, drag the Rocket Launcher_Tutorial prefab into your scene, and position as you wish.</span></span>

    >[!NOTE]
    ><span data-ttu-id="ffe08-122">Der Launcher_Complete Prefab ist das abgeschlossene Start Programm, das als Referenz bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="ffe08-122">The Rocket Launcher_Complete prefab is the completed launcher, provided for reference.</span></span>

    ![Lektion6 Kapitel1 Schritt1im](images/Lesson6_Chapter1_step1im.PNG)

    <span data-ttu-id="ffe08-124">Wenn Sie das Launcher_Tutorial Game-Objekt in der Hierarchie erweitern und das Mond Modul Objekt weiter erweitern, finden Sie mehrere untergeordnete Objekte, die ein Material mit dem Namen "x-ray" aufweisen.</span><span class="sxs-lookup"><span data-stu-id="ffe08-124">If you expand the Rocket Launcher_Tutorial game object in your hierarchy and further expand the Lunar Module object, you find several child objects that have a material called "x-ray."</span></span> <span data-ttu-id="ffe08-125">Das "x-ray"-Material ermöglicht eine etwas durchlässiges Farbe, die als Platzierungs Hinweise für den Benutzer verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ffe08-125">The "x-ray" material allows for a slightly translucent color that will be used as placement hints for the user.</span></span> 

    ![Lesson6 Chapter1 noteaim](images/Lesson6_Chapter1_noteaim.PNG)

    <span data-ttu-id="ffe08-127">Es gibt fünf Teile für das Mond Modul, mit dem der Benutzer interagieren wird, wie in der folgenden Abbildung dargestellt:</span><span class="sxs-lookup"><span data-stu-id="ffe08-127">There are five parts to the lunar module that the user will interact with, as shown in the image below:</span></span>

    1. <span data-ttu-id="ffe08-128">Rover-Gehäuse</span><span class="sxs-lookup"><span data-stu-id="ffe08-128">The Rover Enclosure</span></span>
    2. <span data-ttu-id="ffe08-129">Treibstofftank</span><span class="sxs-lookup"><span data-stu-id="ffe08-129">The Fuel Tank</span></span>
    3. <span data-ttu-id="ffe08-130">Energiezelle</span><span class="sxs-lookup"><span data-stu-id="ffe08-130">The Energy Cell</span></span>
    4. <span data-ttu-id="ffe08-131">Andockportal</span><span class="sxs-lookup"><span data-stu-id="ffe08-131">The Docking Portal</span></span>
    5. <span data-ttu-id="ffe08-132">Externer Sensor</span><span class="sxs-lookup"><span data-stu-id="ffe08-132">The External sensor</span></span>

    ![Lektion6 Kapitel1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

    >[!NOTE]
    ><span data-ttu-id="ffe08-134">Die Spielobjektnamen, die in Ihrer Basisszenenhierarchie angezeigt werden, entsprechen nicht den Namen der Objekte in der Szene.</span><span class="sxs-lookup"><span data-stu-id="ffe08-134">The game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

2. <span data-ttu-id="ffe08-135">Fügen Sie dem lunarmodule-Spielobjekt eine Audioquelle hinzu.</span><span class="sxs-lookup"><span data-stu-id="ffe08-135">Add an audio source to the LunarModule game object.</span></span> <span data-ttu-id="ffe08-136">Stellen Sie sicher, dass das lunarmodule in ihrer Szenen Hierarchie ausgewählt ist, und klicken Sie auf Komponente hinzufügen</span><span class="sxs-lookup"><span data-stu-id="ffe08-136">Make sure the LunarModule is selected in your scene hierarchy and click Add Component.</span></span> <span data-ttu-id="ffe08-137">Suchen Sie nach Audioquelle, und fügen Sie Sie dem Spielobjekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="ffe08-137">Search for Audio Source and add it to the game object.</span></span> <span data-ttu-id="ffe08-138">Lassen Sie das Feld "Audioclip" für den Moment leer, ändern Sie die Einstellung "besondere Blend" jedoch von 0 in 1, damit räumliche Audiodaten aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="ffe08-138">Leave the AudioClip field blank for now, but change the Special Blend setting from 0 to 1 so to enable spatial audio.</span></span> <span data-ttu-id="ffe08-139">Sie verwenden diese Audioquelle, um den Start Sound zu einem späteren Zeitpunkt wiederzugeben.</span><span class="sxs-lookup"><span data-stu-id="ffe08-139">You will use this audio source to play the launching sound later.</span></span>

    ![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG)

3. <span data-ttu-id="ffe08-141">Fügen Sie die Skript-Schalter-Platzierungs Hinweise hinzu.</span><span class="sxs-lookup"><span data-stu-id="ffe08-141">Add the script Toggle Placement Hints.</span></span> <span data-ttu-id="ffe08-142">Klicken Sie auf Komponente hinzufügen, und suchen Sie nach Platzierungs Hinweisen zum Umschalten.</span><span class="sxs-lookup"><span data-stu-id="ffe08-142">Click Add Component and search for Toggle Placement Hints.</span></span> <span data-ttu-id="ffe08-143">Dabei handelt es sich um ein benutzerdefiniertes Skript, mit dem Sie die über sichtigen Hinweise (Objekte mit dem x-ray-Material) wie zuvor erwähnt aktivieren und deaktivieren können.</span><span class="sxs-lookup"><span data-stu-id="ffe08-143">This is a custom script that lets you turn on and off the translucent hints (objects with the x-ray material), as mentioned earlier.</span></span>

    ![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG)

4. <span data-ttu-id="ffe08-145">Da wir über fünf Objekte verfügen, geben Sie "5" für die Größe des Spielobjekt Arrays ein.</span><span class="sxs-lookup"><span data-stu-id="ffe08-145">Since we have five objects, type "5" for the game object array size.</span></span> <span data-ttu-id="ffe08-146">Daraufhin werden fünf neue Elemente angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ffe08-146">You will then see five new elements appear.</span></span>

    ![Lektion6 Kapitel1 Schritt4bim](images/Lesson6_Chapter1_step4bim.PNG)

    <span data-ttu-id="ffe08-148">Ziehen Sie jedes der durchlässigen Objekte in alle Felder namens (Spielobjekt).</span><span class="sxs-lookup"><span data-stu-id="ffe08-148">Drag each of the translucent objects into all the Name (Game Object) boxes.</span></span> <span data-ttu-id="ffe08-149">Ziehen Sie die folgenden Objekte aus dem Lunar-Modul in der Szene in die Objekt Array Felder, wie in der obigen Abbildung dargestellt:</span><span class="sxs-lookup"><span data-stu-id="ffe08-149">Drag the following objects from the lunar module in your scene into the object array fields as shown in the image above:</span></span>

    ![Lektion6 Kapitel1 Schritt4aim](images/Lesson6_Chapter1_step4aim.PNG)

    <span data-ttu-id="ffe08-151">Das Skript zum Umschalten der Platzierungs Hinweise ist nun konfiguriert, sodass wir Hinweise aktivieren und deaktivieren können.</span><span class="sxs-lookup"><span data-stu-id="ffe08-151">The Toggle Placement Hints script is now configured, which allows us to turn hints on and off.</span></span>

5. <span data-ttu-id="ffe08-152">Fügen Sie das Skript Launch Lunar Module hinzu.</span><span class="sxs-lookup"><span data-stu-id="ffe08-152">Add the Launch Lunar Module script.</span></span> <span data-ttu-id="ffe08-153">Klicken Sie auf die Schaltfläche Komponente hinzufügen, suchen Sie nach "Launch Lunar Module", und wählen Sie Sie aus</span><span class="sxs-lookup"><span data-stu-id="ffe08-153">Click the Add Component button, search for "launch lunar module" and select it.</span></span> <span data-ttu-id="ffe08-154">Mit diesem Skript wird das Mond Modul gestartet.</span><span class="sxs-lookup"><span data-stu-id="ffe08-154">This script launches the lunar module.</span></span> <span data-ttu-id="ffe08-155">Wenn wir auf eine konfigurierte Schaltfläche klicken, wird der festen Textkomponente des mondmoduls eine aufwärts-Force hinzugefügt, und das Modul wird aufwärts gestartet.</span><span class="sxs-lookup"><span data-stu-id="ffe08-155">When we press a configured button, it adds an upward force to the lunar module's rigid body component and causes the module to launch upwards.</span></span> <span data-ttu-id="ffe08-156">Wenn Sie sich in einem Gebäude befinden, kollidiert die Mondlandefähre möglicherweise mit Ihrem Deckengittermodell.</span><span class="sxs-lookup"><span data-stu-id="ffe08-156">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="ffe08-157">Wenn Sie sich in einem Bereich mit hohen oder gar keinen Obergrenzen befinden, wird das Mond Modul unbegrenzt in den Speicherbereich überlaufen.</span><span class="sxs-lookup"><span data-stu-id="ffe08-157">If you are in an area with high ceilings or no ceilings, the lunar module will fly into space indefinitely.</span></span>

    ![Lektion6 Kapitel1 Schritt5im](images/Lesson6_Chapter1_step5im.PNG)

6. <span data-ttu-id="ffe08-159">Passen Sie den Schub so an, dass die Mondlandefähre anmutig nach oben aufsteigt.</span><span class="sxs-lookup"><span data-stu-id="ffe08-159">Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="ffe08-160">Versuchen Sie einen Wert von 0,01.</span><span class="sxs-lookup"><span data-stu-id="ffe08-160">Try a value of 0.01.</span></span> <span data-ttu-id="ffe08-161">Lassen Sie das Feld „Rb“ leer.</span><span class="sxs-lookup"><span data-stu-id="ffe08-161">Leave the "Rb" field blank.</span></span> <span data-ttu-id="ffe08-162">RB steht für den starren Text, und dieses Feld wird während der Laufzeit automatisch aufgefüllt.</span><span class="sxs-lookup"><span data-stu-id="ffe08-162">Rb stands for Rigid body and this field will be automatically populated during runtime.</span></span>

    ![Lektion6 Kapitel1 Schritt6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a><span data-ttu-id="ffe08-164">Übersicht über die Komponenten von Mond Modulen</span><span class="sxs-lookup"><span data-stu-id="ffe08-164">Lunar Module Parts overview</span></span>

<span data-ttu-id="ffe08-165">Das übergeordnete Objekt der Mond Modul Teile ist die Sammlung der Objekte, mit denen der Benutzer interagiert.</span><span class="sxs-lookup"><span data-stu-id="ffe08-165">The Lunar Module Parts parent object is the collection of the objects that the user interacts with.</span></span> <span data-ttu-id="ffe08-166">In der folgenden Liste werden die Namen von Spielobjekten mit der Bezeichnung Namen in Klammern angegeben:</span><span class="sxs-lookup"><span data-stu-id="ffe08-166">The Game object names with scene labeled names in parentheses, are provided in the list below:</span></span>

- <span data-ttu-id="ffe08-167">Rucksack (Energie Zelle)</span><span class="sxs-lookup"><span data-stu-id="ffe08-167">Backpack (Energy Cell)</span></span>
- <span data-ttu-id="ffe08-168">Gastank (Treibstofftank)</span><span class="sxs-lookup"><span data-stu-id="ffe08-168">GasTank (Fuel Tank)</span></span>
- <span data-ttu-id="ffe08-169">TopLeftBody (Rover Enclosure) – Oberer linker Körper (Rover-Gehäuse)</span><span class="sxs-lookup"><span data-stu-id="ffe08-169">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="ffe08-170">Nose (Docking Portal) – Nase (Andockportal)</span><span class="sxs-lookup"><span data-stu-id="ffe08-170">Nose (Docking Portal)</span></span>
- <span data-ttu-id="ffe08-171">LeftTwirler (External Sensor) – Linker Drallkörper (Externer Sensor)</span><span class="sxs-lookup"><span data-stu-id="ffe08-171">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="ffe08-172">Beachten Sie, dass jedes dieser Objekte über einen Manipulations Handler verfügt, wie in Lektion 4 erläutert.</span><span class="sxs-lookup"><span data-stu-id="ffe08-172">Notice that each of these objects has a manipulation handler, as explained in Lesson 4.</span></span> <span data-ttu-id="ffe08-173">Diese Funktion ermöglicht es Benutzern, das Objekt zu erfassen und zu bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="ffe08-173">This feature enables users to grab and manipulate the object.</span></span> <span data-ttu-id="ffe08-174">Beachten Sie außerdem, dass die-Einstellung, die zwei übergebenen Manipulations Typen ist, auf verschieben und drehen festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="ffe08-174">Also note that the setting, Two Handed Manipulation Type, is set to Move and Rotate.</span></span> <span data-ttu-id="ffe08-175">Mit dieser Option kann der Benutzer das Objekt nur verschieben und seine Größe nicht ändern. Dies ist die gewünschte Funktionalität für eine assemblyanwendung.</span><span class="sxs-lookup"><span data-stu-id="ffe08-175">This option only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="ffe08-176">Außerdem ist die weite Bearbeitung deaktiviert, um nur die direkte Interaktion von Modul Teilen zuzulassen.</span><span class="sxs-lookup"><span data-stu-id="ffe08-176">In addition, Far Manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Lektion6 Kapitel2im](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="ffe08-178">Das Demoskript der Teile Assembly (siehe oben) ist das Skript, mit dem die Objekte verwaltet werden, die der Benutzer im Mond Modul vom Benutzer platziert.</span><span class="sxs-lookup"><span data-stu-id="ffe08-178">The Part Assembly Demo script (shown above) is the script that manages the objects that the user places on the lunar module by the user.</span></span>

<span data-ttu-id="ffe08-179">Das Feld Objekt zum Platzieren ist die ausgewählte Transformation, wie in der Abbildung oben gezeigt, der dem Objekt zugeordnete Rucksack/Kraftstofftank, mit dem die Verbindung hergestellt wird.</span><span class="sxs-lookup"><span data-stu-id="ffe08-179">The Object To Place field is the transform that is selected, as shown in the image above, the backpack/fuel tank associated with the object that it connects to.</span></span>

<span data-ttu-id="ffe08-180">Mit den Einstellungen für die Near Distance und far distance wird die Nähe festgelegt, zu der Teile direkt oder freigegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="ffe08-180">The Near Distance and Far Distance settings determine the proximity to which parts snap in place or can be released.</span></span> <span data-ttu-id="ffe08-181">Beispielsweise muss der Rucksack/Treibstofftank 0,1 Einheiten vom Mond Modul entfernt werden, bevor das Snap-in-Modul stattfindet.</span><span class="sxs-lookup"><span data-stu-id="ffe08-181">For example, the backpack/fuel tank needs to be 0.1 units away from the lunar module before it will snap into place.</span></span> <span data-ttu-id="ffe08-182">Die Einstellung für die weite Entfernung legt den Speicherort fest, an dem sich das Objekt befinden kann, bevor es vom Mond Modul getrennt werden kann.</span><span class="sxs-lookup"><span data-stu-id="ffe08-182">The Far Distance setting sets the location where the object can be before it can detach from the lunar module.</span></span> <span data-ttu-id="ffe08-183">In diesem Fall muss die Hand des Benutzers den Rucksack/Treibstofftank greifen und ihn 0,2 Einheiten von der Mondlandefähre wegziehen, damit er nicht wieder an seiner Position andockt.</span><span class="sxs-lookup"><span data-stu-id="ffe08-183">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="ffe08-184">Das QuickInfo-Objekt ist die QuickInfo-Bezeichnung in der Szene.</span><span class="sxs-lookup"><span data-stu-id="ffe08-184">The Tool Tip Object is the tool tip label in the scene.</span></span> <span data-ttu-id="ffe08-185">Wenn die Objekte an Ort und Stelle ausgerichtet werden, ist die Bezeichnung deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="ffe08-185">When the objects are snapped in place, the label is disabled.</span></span>

<span data-ttu-id="ffe08-186">Die Audioquelle wird automatisch gepackt.</span><span class="sxs-lookup"><span data-stu-id="ffe08-186">The Audio Source is automatically grabbed.</span></span>

### <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="ffe08-187">Konfigurieren der Schaltfläche Platzierungs Hinweise</span><span class="sxs-lookup"><span data-stu-id="ffe08-187">Configuring the Placement Hints button</span></span>

<span data-ttu-id="ffe08-188">In [Lektion 2](mrlearning-base-ch2.md)haben Sie gelernt, wie Sie Schaltflächen platzieren und konfigurieren können, um Dinge wie das Ändern der Farbe eines Elements oder das Abspielen eines Sounds beim Pushvorgang zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="ffe08-188">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when pushed.</span></span> <span data-ttu-id="ffe08-189">Wir werden diese Prinzipien weiterhin verwenden, wenn wir unsere Schaltflächen zum Umschalten von Platzierungshinweisen konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="ffe08-189">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span>

<span data-ttu-id="ffe08-190">Ziel ist es, die Schaltfläche so zu konfigurieren, dass jedes Mal, wenn der Benutzer die Schaltfläche "Platzierungs Hinweis" drückt, die Sichtbarkeit der Hinweise zur durchlässigen Platzierung schaltet.</span><span class="sxs-lookup"><span data-stu-id="ffe08-190">The goal is to configure our button so that every time the user presses the Placement hint button, it toggles the visibility of the translucent placement hints.</span></span>

1. <span data-ttu-id="ffe08-191">Verschieben Sie das Mond Modul in den leeren reinen Laufzeitbereich im Inspektor-Panel, während das Objekt Platzierungs Hinweise in der Basis Szenen Hierarchie ausgewählt wird.</span><span class="sxs-lookup"><span data-stu-id="ffe08-191">Move the lunar module to the empty Runtime Only slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span>

    ![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG)

2. <span data-ttu-id="ffe08-193">Klicken Sie auf die Dropdown Liste keine Funktion.</span><span class="sxs-lookup"><span data-stu-id="ffe08-193">Click the No Function dropdown list.</span></span> <span data-ttu-id="ffe08-194">Wechseln Sie zu "umggleplacementhints", und wählen Sie unter diesem Menü den Befehl "" "" "" "" "" "</span><span class="sxs-lookup"><span data-stu-id="ffe08-194">Go down to TogglePlacementHints and select ToggleGameObjects () under that menu.</span></span> <span data-ttu-id="ffe08-195">"Degglegameobjects ()" schaltet die Platzierungs Hinweise ein und aus, sodass Sie bei jedem Drücken der Schaltfläche sichtbar oder unsichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="ffe08-195">ToggleGameObjects() toggles the placement hints on and off so that they are visible or invisible each time the button is pressed.</span></span>

    ![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a><span data-ttu-id="ffe08-197">Konfigurieren der Schaltfläche Zurücksetzen</span><span class="sxs-lookup"><span data-stu-id="ffe08-197">Configuring the Reset button</span></span>

<span data-ttu-id="ffe08-198">Es gibt Situationen, in denen der Benutzer einen Fehler ausgibt, das Objekt versehentlich auslöst oder nur die Benutzeroberflächen zurücksetzen möchte.</span><span class="sxs-lookup"><span data-stu-id="ffe08-198">There will be situations where the user makes a mistake, accidentally throws the object away or just wants to reset the experience.</span></span> <span data-ttu-id="ffe08-199">Mit der Schaltfläche Zurücksetzen können Sie die Funktionalität neu starten.</span><span class="sxs-lookup"><span data-stu-id="ffe08-199">The Reset button adds the ability to restart the experience.</span></span>

1. <span data-ttu-id="ffe08-200">Wählen Sie die Schaltfläche Zurücksetzen.</span><span class="sxs-lookup"><span data-stu-id="ffe08-200">Select the Reset button.</span></span> <span data-ttu-id="ffe08-201">In der Basis Szene heißt der Name Reort.</span><span class="sxs-lookup"><span data-stu-id="ffe08-201">In the base scene, it’s named ResetRoundButton.</span></span>

2. <span data-ttu-id="ffe08-202">Ziehen Sie das Modul "Mond" aus der Basis Szenen Hierarchie in den leeren Slot unter der Schaltfläche "gedrückt" im Inspektor-Panel.</span><span class="sxs-lookup"><span data-stu-id="ffe08-202">Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed on the inspector panel.</span></span>

    ![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

3. <span data-ttu-id="ffe08-204">Wählen Sie das Dropdown Menü No Function aus, zeigen Sie auf launchlunarmodule, und wählen Sie dann resetmodule () aus.</span><span class="sxs-lookup"><span data-stu-id="ffe08-204">Select the No Function dropdown menu and hover over LaunchLunarModule, then select resetModule ().</span></span>

    ![Lektion6 Kapitel4 Schritt3im](images/Lesson6_Chapter4_step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="ffe08-206">Beachten Sie, dass die gameobject. broadcastmessage standardmäßig für resetplacement konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="ffe08-206">Notice that by default, the GameObject.BroadcastMessage is configured to ResetPlacement.</span></span> <span data-ttu-id="ffe08-207">Dadurch wird eine Nachricht mit dem Namen resetplacement für jedes untergeordnete Objekt des RocketLauncher_Tutorial übermittelt.</span><span class="sxs-lookup"><span data-stu-id="ffe08-207">This broadcasts a message named ResetPlacement for every child object of the RocketLauncher_Tutorial.</span></span> <span data-ttu-id="ffe08-208">Alle-Objekte, die über eine-Methode für resetplacement () verfügen, reagieren auf diese Nachricht, indem Sie die Position zurücksetzt.</span><span class="sxs-lookup"><span data-stu-id="ffe08-208">Any object that has a method for ResetPlacement() responds to that message by resetting it's position.</span></span>

### <a name="configuring-the-launch-button"></a><span data-ttu-id="ffe08-209">Konfigurieren der Schaltfläche "starten"</span><span class="sxs-lookup"><span data-stu-id="ffe08-209">Configuring the Launch button</span></span>

<span data-ttu-id="ffe08-210">In diesem Abschnitt wird erläutert, wie Sie die Schaltfläche "Start" konfigurieren, die es dem Benutzer ermöglicht, die Schaltfläche zu drücken und das Mond Modul in den Raum zu</span><span class="sxs-lookup"><span data-stu-id="ffe08-210">This section explains how to configure the Launch button, which permits the user to press the button and launch the lunar module into space.</span></span>

1. <span data-ttu-id="ffe08-211">Wählen Sie die Schaltfläche Starten aus.</span><span class="sxs-lookup"><span data-stu-id="ffe08-211">Select the Launch button.</span></span> <span data-ttu-id="ffe08-212">In der Basis Szene heißt Sie launchroundbutton.</span><span class="sxs-lookup"><span data-stu-id="ffe08-212">In the base scene, it’s called LaunchRoundButton.</span></span> <span data-ttu-id="ffe08-213">Ziehen Sie das Modul "Lunar" in den leeren Slot unter "touchende" im Inspektor-Panel.</span><span class="sxs-lookup"><span data-stu-id="ffe08-213">Drag the lunar module to the empty slot under Touch End in the Inspector panel.</span></span>

    ![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG)

2. <span data-ttu-id="ffe08-215">Wählen Sie das Dropdown Menü keine Funktion aus, zeigen Sie auf launchlunarmodule, und wählen Sie stopthruster() aus.</span><span class="sxs-lookup"><span data-stu-id="ffe08-215">Select the No Function dropdown menu and hover over LaunchLunarModule, and select StopThruster ().</span></span> <span data-ttu-id="ffe08-216">Dadurch wird gesteuert, wie viel der Benutzer an das Mond Modul übergeben möchte.</span><span class="sxs-lookup"><span data-stu-id="ffe08-216">This controls how much thrust the user wants to give to the lunar module.</span></span>

    ![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)

3. <span data-ttu-id="ffe08-218">Ziehen Sie das Modul "Mond" aus der Basis Szenen Hierarchie in den leeren Slot unter der Schaltfläche "gedrückt" im Inspektor-Panel.</span><span class="sxs-lookup"><span data-stu-id="ffe08-218">Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed in the inspector panel.</span></span>

4. <span data-ttu-id="ffe08-219">Klicken Sie auf das Dropdown Menü keine Funktion und dann auf launchlunarmodule, und wählen Sie startthruester () aus.</span><span class="sxs-lookup"><span data-stu-id="ffe08-219">Click the No function dropdown menu and then on LaunchLunarModule and select StartThruster ().</span></span>

    ![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)

5. <span data-ttu-id="ffe08-221">Fügen Sie dem Lunar-Modul Musik hinzu, damit Musik abgespielt wird, wenn die Abladung ausgeschaltet wird.</span><span class="sxs-lookup"><span data-stu-id="ffe08-221">Add music to the lunar module so that music plays when the rocket takes off.</span></span> <span data-ttu-id="ffe08-222">Ziehen Sie hierzu das Mond Modul auf den nächsten leeren Slot unter der Schaltfläche gedrückt ().</span><span class="sxs-lookup"><span data-stu-id="ffe08-222">To do this, drag the lunar module to the next empty slot under Button Pressed().</span></span>

6. <span data-ttu-id="ffe08-223">Wählen Sie das Dropdown Menü No Function aus, zeigen Sie auf audiosource, und wählen Sie playoneshot (Audioclip) aus.</span><span class="sxs-lookup"><span data-stu-id="ffe08-223">Select the No Function dropdown menu, hover over AudioSource and select PlayOneShot (AudioClip).</span></span> <span data-ttu-id="ffe08-224">Sie können jederzeit die Vielfalt der im MRTK enthaltenen Sounds erkunden.</span><span class="sxs-lookup"><span data-stu-id="ffe08-224">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="ffe08-225">In diesem Beispiel verwenden wir "MRTK_Gem".</span><span class="sxs-lookup"><span data-stu-id="ffe08-225">In this example, we'll use "MRTK_Gem."</span></span>

    ![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)

### <a name="congratulations"></a><span data-ttu-id="ffe08-227">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="ffe08-227">Congratulations</span></span>

<span data-ttu-id="ffe08-228">Sie haben diese Anwendung vollständig konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="ffe08-228">You have fully configured this application.</span></span> <span data-ttu-id="ffe08-229">Wenn Sie jetzt auf "Abspielen" klicken, können Sie das Mond Modul vollständig zusammenstellen, Hinweise umschalten, das Mond Modul starten und es erneut starten.</span><span class="sxs-lookup"><span data-stu-id="ffe08-229">Now, when you press play, you can fully assemble the lunar module, toggle hints, launch the lunar module and reset it to start again.</span></span>
