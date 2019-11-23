---
title: 'Fallstudie: Erstellen von holosketch, ein räumliches Layout und eine UX-skizzieren-App für hololens'
description: Holosketch ist ein auf dem Gerät räumliches Layout und UX-skeshottool für hololens, das Sie bei der Erstellung von Holographic-Erfahrungen unterstützt.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Holosketch, hololens, Windows Mixed Reality, Sketching, App
ms.openlocfilehash: d6d22aae7709bcc1a33b142a100d1a0f9645d3cc
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436943"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a><span data-ttu-id="dd2ef-104">Fallstudie: Erstellen von holosketch, ein räumliches Layout und eine UX-skizzieren-App für hololens</span><span class="sxs-lookup"><span data-stu-id="dd2ef-104">Case study - Building HoloSketch, a spatial layout and UX sketching app for HoloLens</span></span>

<span data-ttu-id="dd2ef-105">Holosketch ist ein auf dem Gerät räumliches Layout und UX-skeshottool für hololens, das Sie bei der Erstellung von Holographic-Erfahrungen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-105">HoloSketch is an on-device spatial layout and UX sketching tool for HoloLens to help build holographic experiences.</span></span> <span data-ttu-id="dd2ef-106">Holosketch funktioniert mit einer gekoppelten Bluetooth-Tastatur und-Maus sowie mit Gesten-und Sprachbefehlen.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-106">HoloSketch works with a paired Bluetooth keyboard and mouse as well as gesture and voice commands.</span></span> <span data-ttu-id="dd2ef-107">Der Zweck von holosketch besteht darin, ein einfaches UX-Layouttool für die schnelle Visualisierung und Iterationen bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-107">The purpose of HoloSketch is to provide a simple UX layout tool for quick visualization and iteration.</span></span>

<span data-ttu-id="dd2ef-108">![holosketch: ein räumliches Layout und eine UX-skizzieren-App für hololens.](images/holosketch-image-01-640px.png)</span><span class="sxs-lookup"><span data-stu-id="dd2ef-108">![HoloSketch: A spatial layout and UX sketching app for HoloLens.](images/holosketch-image-01-640px.png)</span></span><br>
<span data-ttu-id="dd2ef-109">*Holosketch: räumliche Layout und UX-App für hololens*</span><span class="sxs-lookup"><span data-stu-id="dd2ef-109">*HoloSketch: spatial layout and UX sketching app for HoloLens*</span></span>

<span data-ttu-id="dd2ef-110">![ein einfaches UX-Layouttool für die schnelle Visualisierung und Iterationen.](images/holosketch-image-02.png)</span><span class="sxs-lookup"><span data-stu-id="dd2ef-110">![A simple UX layout tool for quick visualization and iteration.](images/holosketch-image-02.png)</span></span><br>
<span data-ttu-id="dd2ef-111">*Ein einfaches UX-Layouttool für die schnelle Visualisierung und Iterationen*</span><span class="sxs-lookup"><span data-stu-id="dd2ef-111">*A simple UX layout tool for quick visualization and iteration*</span></span>

## <a name="features"></a><span data-ttu-id="dd2ef-112">Features</span><span class="sxs-lookup"><span data-stu-id="dd2ef-112">Features</span></span>

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a><span data-ttu-id="dd2ef-113">Grundtypen für schnelles Studium und Skalierung von Prototypen</span><span class="sxs-lookup"><span data-stu-id="dd2ef-113">Primitives for quick studies and scale-prototyping</span></span>

![Verwenden primitiver Formen](images/holosketch-primitives-giphy.gif)

<span data-ttu-id="dd2ef-115">Verwenden Sie primitive Formen für schnelle und skalierbare Prototypen.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-115">Use primitive shapes for quick massing studies and scale-prototyping.</span></span>

### <a name="import-objects-through-onedrive"></a><span data-ttu-id="dd2ef-116">Importieren von Objekten über onedrive</span><span class="sxs-lookup"><span data-stu-id="dd2ef-116">Import objects through OneDrive</span></span>

![Importieren von Objekten](images/holosketch-importobjects-giphy.gif)

<span data-ttu-id="dd2ef-118">Importieren Sie PNG/JPG-Images oder 3D-b-Objekte (erfordert Verpacken in Unity) in den gemischten Reality-Raum über onedrive.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-118">Import PNG/JPG images or 3D FBX objects(requires packaging in Unity) into the mixed reality space through OneDrive.</span></span>

### <a name="manipulate-objects"></a><span data-ttu-id="dd2ef-119">Objekte bearbeiten</span><span class="sxs-lookup"><span data-stu-id="dd2ef-119">Manipulate objects</span></span>

![Bearbeiten von Objekten](images/manipulate-objects-640px.jpg)

<span data-ttu-id="dd2ef-121">Bearbeiten Sie Objekte (verschieben/drehen/Skalieren) mit einer vertrauten 3D-Objektschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-121">Manipulate objects (move/rotate/scale) with a familiar 3D object interface.</span></span>

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a><span data-ttu-id="dd2ef-122">Bluetooth-, Maus-/Tastatur-, Gesten-und Sprachbefehle</span><span class="sxs-lookup"><span data-stu-id="dd2ef-122">Bluetooth, mouse/keyboard, gestures and voice commands</span></span>

![unterstützt Bluetooth](images/supports-bluetooth-640px.jpg)

<span data-ttu-id="dd2ef-124">Holosketch unterstützt Bluetooth-Maus/Tastatur, Gesten und Sprachbefehle.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-124">HoloSketch supports Bluetooth mouse/keyboard, gestures and voice commands.</span></span>

## <a name="background"></a><span data-ttu-id="dd2ef-125">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="dd2ef-125">Background</span></span>

### <a name="importance-of-experiencing-your-design-in-the-device"></a><span data-ttu-id="dd2ef-126">Wichtigkeit der Erfahrung des Entwurfs im Gerät</span><span class="sxs-lookup"><span data-stu-id="dd2ef-126">Importance of experiencing your design in the device</span></span>

<span data-ttu-id="dd2ef-127">Wenn Sie etwas für hololens entwerfen, ist es wichtig, dass Sie Ihr Design auf dem Gerät haben.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-127">When you design something for HoloLens, it is important to experience your design in the device.</span></span> <span data-ttu-id="dd2ef-128">Eine der größten Herausforderungen beim Mixed Reality-App-Entwurf besteht darin, dass es schwierig ist, den Sinn von Skalierbarkeit, Position und Tiefe zu erzielen, insbesondere durch herkömmliche 2D-Skizzen.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-128">One of the biggest challenges in mixed reality app design is that it is hard to get the sense of scale, position and depth, especially through traditional 2D sketches.</span></span>

### <a name="cost-of-2d-based-communication"></a><span data-ttu-id="dd2ef-129">Kosten der 2D-basierten Kommunikation</span><span class="sxs-lookup"><span data-stu-id="dd2ef-129">Cost of 2D based communication</span></span>

<span data-ttu-id="dd2ef-130">Zum effektiven kommunizieren von UX-Flows und-Szenarien für andere kann es sein, dass ein Designer viel Zeit für die Erstellung von Assets mit herkömmlichen 2D-Tools wie Illustrator, Photoshop und PowerPoint aufwenden könnte.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-130">To effectively communicate UX flows and scenarios to others, a designer may end up spending a lot of time creating assets using traditional 2D tools such as Illustrator, Photoshop and PowerPoint.</span></span> <span data-ttu-id="dd2ef-131">Diese 2D-Entwürfe erfordern häufig zusätzlichen Aufwand, Sie in 3D zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-131">These 2D designs often require additional effort to convert them it into 3D.</span></span> <span data-ttu-id="dd2ef-132">Einige Ideen gehen bei dieser Übersetzung von 2D in 3D verloren.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-132">Some ideas are lost in this translation from 2D to 3D.</span></span>

### <a name="complex-deployment-process"></a><span data-ttu-id="dd2ef-133">Komplexer Bereitstellungs Prozess</span><span class="sxs-lookup"><span data-stu-id="dd2ef-133">Complex deployment process</span></span>

<span data-ttu-id="dd2ef-134">Da gemischte Realität eine neue Canvas für uns ist, umfasst Sie viele Entwurfs Iterationen und-Testversionen und-Fehler.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-134">Since mixed reality is a new canvas for us, it involves a lot of design iteration and trial and error by its nature.</span></span> <span data-ttu-id="dd2ef-135">Für Designer, die mit Tools wie Unity und Visual Studio nicht vertraut sind, ist es nicht einfach, etwas in hololens zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-135">For designer who are not familiar with tools such as Unity and Visual Studio, it is not easy to put something together in HoloLens.</span></span> <span data-ttu-id="dd2ef-136">In der Regel müssen Sie den folgenden Prozess durchlaufen, um Ihre 2D/3D-Grafik im Gerät anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-136">Typically you have to go through the process below to see your 2D/3D artwork in the device.</span></span> <span data-ttu-id="dd2ef-137">Dies war eine große Barriere für Entwickler, die Ideen und Szenarios schnell durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-137">This was a big barrier for designers iterating on ideas and scenarios quickly.</span></span>

<span data-ttu-id="dd2ef-138">![komplexer Bereitstellungs Prozess](images/holosketch-image-03-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="dd2ef-138">![Complex deployment process](images/holosketch-image-03-1000px.png)</span></span><br>
<span data-ttu-id="dd2ef-139">*Bereitstellungs Prozess*</span><span class="sxs-lookup"><span data-stu-id="dd2ef-139">*Deployment process*</span></span>

### <a name="simplified-process-with-holosketch"></a><span data-ttu-id="dd2ef-140">Vereinfachter Prozess mit holosketch</span><span class="sxs-lookup"><span data-stu-id="dd2ef-140">Simplified process with HoloSketch</span></span>

<span data-ttu-id="dd2ef-141">Mit holosketch wollten wir diesen Prozess vereinfachen, ohne die Entwicklungs Tools und Geräte Portal Kopplung einzubeziehen.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-141">With HoloSketch, we wanted to simplify this process without involving development tools and device portal pairing.</span></span> <span data-ttu-id="dd2ef-142">Mithilfe von onedrive können Benutzer problemlos 2D/3D-Assets in hololens einfügen.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-142">Using OneDrive, users can easily put 2D/3D assets into HoloLens.</span></span>

<span data-ttu-id="dd2ef-143">![vereinfachten Prozess mit holosketch](images/holosketch-image-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="dd2ef-143">![Simplified process with HoloSketch](images/holosketch-image-04-1000px.png)</span></span><br>
<span data-ttu-id="dd2ef-144">*Vereinfachter Prozess mit holosketch*</span><span class="sxs-lookup"><span data-stu-id="dd2ef-144">*Simplified process with HoloSketch*</span></span>

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a><span data-ttu-id="dd2ef-145">Fördern von dreidimensionalen Entwurfs Gedanken und-Lösungen</span><span class="sxs-lookup"><span data-stu-id="dd2ef-145">Encouraging three-dimensional design thinking and solutions</span></span>

<span data-ttu-id="dd2ef-146">Wir dachten, dass dieses Tool Entwicklern die Möglichkeit bietet, Lösungen in einem wirklich dreidimensionalen Raum zu untersuchen und nicht in 2D stecken zu müssen.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-146">We thought this tool would give designers an opportunity to explore solutions in a truly three-dimensional space and not be stuck in 2D.</span></span> <span data-ttu-id="dd2ef-147">Sie müssen sich keine Gedanken über das Erstellen eines 3D-Hintergrunds für die Benutzeroberfläche machen, da der Hintergrund im Fall von hololens die wirkliche Welt ist.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-147">They don’t have to think about creating a 3D background for their UI since the background is the real world in the case of HoloLens.</span></span> <span data-ttu-id="dd2ef-148">Holosketch öffnet eine Methode, mit der Designer den 3D-Entwurf auf hololens problemlos untersuchen können.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-148">HoloSketch opens up a way for designers to easily explore 3D design on HoloLens.</span></span>

## <a name="get-started"></a><span data-ttu-id="dd2ef-149">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="dd2ef-149">Get Started</span></span>

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a><span data-ttu-id="dd2ef-150">Importieren von 2D-images (JPG/PNG) in holosketch</span><span class="sxs-lookup"><span data-stu-id="dd2ef-150">How to import 2D images (JPG/PNG) into HoloSketch</span></span>

* <span data-ttu-id="dd2ef-151">Laden Sie JPG/PNG-Bilder in ihren onedrive-Ordner "Documents/holosketch" hoch.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-151">Upload JPG/PNG images to your OneDrive folder ‘Documents/HoloSketch’.</span></span>
* <span data-ttu-id="dd2ef-152">Über das onedrive-Menü in holosketch können Sie das Bild auswählen und in der Umgebung platzieren.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-152">From the OneDrive menu in HoloSketch, you will be able to select and place the image in the environment.</span></span>

<span data-ttu-id="dd2ef-153">![Importieren von 2D-images](images/import-2d-images-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="dd2ef-153">![Importing 2D images](images/import-2d-images-1000px.jpg)</span></span><br>
<span data-ttu-id="dd2ef-154">*Importieren von Bildern und 3D-Objekten über onedrive*</span><span class="sxs-lookup"><span data-stu-id="dd2ef-154">*Importing images and 3D objects through OneDrive*</span></span>

### <a name="how-to-import-3d-objects-into-holosketch"></a><span data-ttu-id="dd2ef-155">Importieren von 3D-Objekten in holosketch</span><span class="sxs-lookup"><span data-stu-id="dd2ef-155">How to import 3D objects into HoloSketch</span></span>

<span data-ttu-id="dd2ef-156">Führen Sie vor dem Hochladen in ihren onedrive-Ordner die folgenden Schritte aus, um die 3D-Objekte in ein Unity-Ressourcen Bündel zu packen.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-156">Before uploading to your OneDrive folder, please follow the steps below to package your 3D objects into a Unity asset bundle.</span></span> <span data-ttu-id="dd2ef-157">Mithilfe dieses Prozesses können Sie Ihre Dateien mit dem Namen "f" und "obj" aus 3D-Software importieren, z. b. Maya, Kino 4D und Microsoft Paint 3D.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-157">Using this process you can import your FBX/OBJ files from 3D software such as Maya, Cinema 4D and Microsoft Paint 3D.</span></span>

>[!IMPORTANT]
><span data-ttu-id="dd2ef-158">Derzeit wird die Erstellung von Asset-Paketen mit Unity-Version 5.4.5 F1 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-158">Currently, asset bundle creation is supported with Unity version 5.4.5f1.</span></span>

1. <span data-ttu-id="dd2ef-159">Das Unity-Projekt ["AssetBunlder_Unity"](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity)herunterladen und öffnen.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-159">Download and open the Unity project ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span></span> <span data-ttu-id="dd2ef-160">Dieses Unity-Projekt enthält das Skript für die Bundle-Asset-Generierung.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-160">This Unity project includes the script for the bundle asset generation.</span></span>
2. <span data-ttu-id="dd2ef-161">Erstellen Sie ein neues gameobject-Objekt.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-161">Create a new GameObject.</span></span>
3. <span data-ttu-id="dd2ef-162">Benennen Sie das gameobject basierend auf dem Inhalt.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-162">Name the GameObject based on the contents.</span></span>
4. <span data-ttu-id="dd2ef-163">Klicken Sie im Inspektor-Panel auf "Komponente hinzufügen", und fügen Sie "Box Collider" hinzu.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-163">In the Inspector panel, click ‘Add Component’ and add ‘Box Collider’.</span></span> 

   ![Klicken Sie im Inspektor-Panel auf "Komponente hinzufügen", und fügen Sie "Box Collider" hinzu.](images/holosketch-10a-assetbundles-1000px.png)
   
   ![Klicken Sie im Inspektor-Panel auf "Komponente hinzufügen", und fügen Sie den #2 "Box Collider" hinzu.](images/holosketch-10b-assetbundles-1000px.png)

5. <span data-ttu-id="dd2ef-166">Importieren Sie die 3D-Datei-Datei, indem Sie Sie in das Projekt Panel ziehen.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-166">Import the 3D FBX file by dragging it into the project panel.</span></span>
6. <span data-ttu-id="dd2ef-167">Ziehen Sie das Objekt in den Bereich Hierarchie **unter dem neuen gameobject**.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-167">Drag the object into the Hierarchy panel **under your new GameObject**.</span></span>

   ![Ziehen Sie das Objekt in den Bereich Hierarchie unter dem neuen gameobject.](images/holosketch-12-assetbundles-1000px.png)

7. <span data-ttu-id="dd2ef-169">Passen Sie die Collider-Dimension an, wenn Sie nicht mit dem-Objekt identisch ist.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-169">Adjust the collider dimension if it does not match the object.</span></span> <span data-ttu-id="dd2ef-170">Drehen Sie das Objekt um die **Z-Achse**.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-170">Rotate the object to face **Z-axis**.</span></span>

   ![Passen Sie die Collider-Dimension an, wenn Sie nicht mit dem Objekt identisch ist.](images/holosketch-13-assetbundles-1000px.png)

8. <span data-ttu-id="dd2ef-172">Ziehen Sie das Objekt aus dem Bereich Hierarchie in das Projekt Panel, um **es vorzu machen**.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-172">Drag the object from the Hierarchy panel to the Project panel to **make it prefab**.</span></span>
9. <span data-ttu-id="dd2ef-173">Klicken Sie unten im Inspektor-Panel auf die Dropdown Liste, erstellen Sie einen neuen eindeutigen Namen, und weisen Sie ihn zu.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-173">On the bottom of the inspector panel, click the dropdown, create and assign a new unique name.</span></span> <span data-ttu-id="dd2ef-174">Das folgende Beispiel zeigt das Hinzufügen und Zuweisen von "brownstuhl" für den assetbundle-Namen.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-174">Below example shows adding and assigning 'brownchair' for the AssetBundle Name.</span></span> 

   ![Klicken Sie im unteren Bereich des inspektorbereichs auf die Dropdown Liste, und weisen Sie einen neuen eindeutigen Namen zu.](images/holosketch-14-assetbundles-1000px.png)

10. <span data-ttu-id="dd2ef-176">Bereiten Sie ein Miniaturbild für das Modell Objekt vor.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-176">Prepare a thumbnail image for the model object.</span></span> 
   <span data-ttu-id="dd2ef-177">![ziehen Sie ein Bild in das Projekt Panel, und weisen Sie den Namen zu, der für das Objekt verwendet wird.](images/holosketch-15-assetbundles-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="dd2ef-177">![Drag an image into the project panel and assign the name used for the object.](images/holosketch-15-assetbundles-1000px.png)</span></span>

11. <span data-ttu-id="dd2ef-178">Erstellen Sie im Ordner "Asset" des Unity-Projekts einen Ordner mit dem Namen "assetbundles".</span><span class="sxs-lookup"><span data-stu-id="dd2ef-178">Create a folder named ‘Assetbundles’ under the Unity project’s ‘Asset’ folder.</span></span>

12. <span data-ttu-id="dd2ef-179">Wählen Sie im Menü Assets die Option zum Erstellen von assetbundles aus, um die Datei zu generieren.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-179">From the Assets menu, select ‘Build AssetBundles’ to generate file.</span></span> 
   <span data-ttu-id="dd2ef-180">Wählen Sie ![im Menü Assets die Option zum Erstellen von assetbundles aus, um die Datei zu generieren.](images/holosketch-15a-assetbundles.png)</span><span class="sxs-lookup"><span data-stu-id="dd2ef-180">![From the Assets menu, select ‘Build AssetBundles’ to generate file.](images/holosketch-15a-assetbundles.png)</span></span>


13. <span data-ttu-id="dd2ef-181">**Laden Sie die generierte Datei in den Ordner/Files/Documents/HoloSketch auf onedrive hoch.**</span><span class="sxs-lookup"><span data-stu-id="dd2ef-181">**Upload the generated file to the /Files/Documents/HoloSketch folder on OneDrive.**</span></span> <span data-ttu-id="dd2ef-182">Laden Sie nur die asset_unique_name Datei hoch.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-182">Upload the asset_unique_name file only.</span></span> <span data-ttu-id="dd2ef-183">Manifestressourcen oder assetbundle-Dateien müssen nicht hochgeladen werden.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-183">You don’t need to upload manifest files or AssetBundles file.</span></span> <br>
<span data-ttu-id="dd2ef-184">![Hinzufügen von Dateien zu Dateien/Dokumenten/holosketch/Ordner](images/holosketch-onedriveupload-1000px.png)
![wird das hinzugefügte 3D-Objekt im onedrive-Menü von holosketch angezeigt](images/holosketch-14-onedriveexample-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="dd2ef-184">![Add files to Files/Documents/HoloSketch/ folder](images/holosketch-onedriveupload-1000px.png)
![You will see added 3D object in HoloSketch's OneDrive menu](images/holosketch-14-onedriveexample-1000px.jpg)</span></span>

## <a name="how-to-manipulate-the-objects"></a><span data-ttu-id="dd2ef-185">Vorgehensweise beim Bearbeiten der Objekte</span><span class="sxs-lookup"><span data-stu-id="dd2ef-185">How to manipulate the objects</span></span>

<span data-ttu-id="dd2ef-186">Holosketch unterstützt die herkömmliche Oberfläche, die häufig in 3D-Software verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-186">HoloSketch supports the traditional interface that is widely used in 3D software.</span></span> <span data-ttu-id="dd2ef-187">Sie können das Verschieben, drehen und Skalieren der Objekte mit Gesten und Maus verwenden.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-187">You can use move, rotate, scale the objects with gestures and a mouse.</span></span> <span data-ttu-id="dd2ef-188">Sie können schnell zwischen verschiedenen Modi mit Stimme oder Tastatur wechseln.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-188">You can quickly switch between different modes with voice or keyboard.</span></span>

### <a name="object-manipulation-modes"></a><span data-ttu-id="dd2ef-189">Objekt Bearbeitungsmodi</span><span class="sxs-lookup"><span data-stu-id="dd2ef-189">Object manipulation modes</span></span>

<span data-ttu-id="dd2ef-190">![, wie die Objekte bearbeitet werden](images/holosketch-image-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="dd2ef-190">![How to manipulate the objects](images/holosketch-image-06-1000px.png)</span></span><br>
<span data-ttu-id="dd2ef-191">*Vorgehensweise beim Bearbeiten der Objekte*</span><span class="sxs-lookup"><span data-stu-id="dd2ef-191">*How to manipulate the objects*</span></span>

### <a name="contextual-and-tool-belt-menus"></a><span data-ttu-id="dd2ef-192">Kontext-und toolbandmenüs</span><span class="sxs-lookup"><span data-stu-id="dd2ef-192">Contextual and Tool Belt menus</span></span>

<span data-ttu-id="dd2ef-193">**Verwenden des Kontextmenüs**</span><span class="sxs-lookup"><span data-stu-id="dd2ef-193">**Using the Contextual Menu**</span></span>

<span data-ttu-id="dd2ef-194">Doppel Tippen Sie auf, um das Kontextmenü zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-194">Double air tap to open the Contextual Menu.</span></span> 

<span data-ttu-id="dd2ef-195">Menü Elemente:</span><span class="sxs-lookup"><span data-stu-id="dd2ef-195">Menu items:</span></span>
* <span data-ttu-id="dd2ef-196">**Layoutoberfläche:** Dabei handelt es sich um ein 3D-Raster System, in dem Sie mehrere Objekte erstellen und als Gruppe verwalten können.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-196">**Layout Surface:** This is a 3D grid system where you can layout multiple objects and manage them as a group.</span></span> <span data-ttu-id="dd2ef-197">Doppel Tippen Sie auf die layoutoberfläche, um Ihr Objekte hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-197">Double air-tap on the Layout Surface to add objects to it.</span></span>
* <span data-ttu-id="dd2ef-198">**Primitive:** Verwenden Sie Cubes, Bereiche, Zylinder und Kegel zum Durchführen von Studien.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-198">**Primitives:** Use cubes, spheres, cylinders and cones for massing studies.</span></span>
* <span data-ttu-id="dd2ef-199">**Onedrive:** Öffnen Sie das onedrive-Menü, um Objekte zu importieren.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-199">**OneDrive:** Open the OneDrive menu to import objects.</span></span>
* <span data-ttu-id="dd2ef-200">**Hilfe:** Zeigt den Hilfe Bildschirm an.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-200">**Help:** Displays help screen.</span></span>

<span data-ttu-id="dd2ef-201">![Kontextmenü](images/holosketch-image-07.png)</span><span class="sxs-lookup"><span data-stu-id="dd2ef-201">![Contextual menu](images/holosketch-image-07.png)</span></span><br>
<span data-ttu-id="dd2ef-202">*Kontextmenü*</span><span class="sxs-lookup"><span data-stu-id="dd2ef-202">*Contextual menu*</span></span>

<span data-ttu-id="dd2ef-203">**Verwenden des toolbandmenüs**</span><span class="sxs-lookup"><span data-stu-id="dd2ef-203">**Using the Tool Belt Menu**</span></span>

<span data-ttu-id="dd2ef-204">Verschieben, drehen, skalieren, speichern und Laden von Szenen sind im Menüband-Menü verfügbar.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-204">Move, Rotate, Scale, Save, and Load Scene are available from the Tool Belt Menu.</span></span> 

## <a name="using-keyboard-gestures-and-voice-commands"></a><span data-ttu-id="dd2ef-205">Verwenden von Tastatur, Gesten und Sprachbefehlen</span><span class="sxs-lookup"><span data-stu-id="dd2ef-205">Using keyboard, gestures and voice commands</span></span>

<span data-ttu-id="dd2ef-206">![Tastatur, Gesten und Sprachbefehle](images/holosketch-image-08-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="dd2ef-206">![Keyboard, Gestures and Voice Commands](images/holosketch-image-08-1000px.png)</span></span><br>
<span data-ttu-id="dd2ef-207">*Tastatur-, Gesten-und Sprachbefehle*</span><span class="sxs-lookup"><span data-stu-id="dd2ef-207">*Keyboard, gestures, and voice commands*</span></span>

## <a name="download-the-app"></a><span data-ttu-id="dd2ef-208">Herunterladen der APP</span><span class="sxs-lookup"><span data-stu-id="dd2ef-208">Download the app</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><span data-ttu-id="dd2ef-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Laden Sie die holosketch-App kostenlos herunter, und installieren Sie Sie im Microsoft Store</a>
</span><span class="sxs-lookup"><span data-stu-id="dd2ef-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Download and install the HoloSketch app for free from the Microsoft Store</a>
</span></span></td>
</tr>
</table>

## <a name="known-issues"></a><span data-ttu-id="dd2ef-210">Bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="dd2ef-210">Known issues</span></span>
* <span data-ttu-id="dd2ef-211">Derzeit wird die Erstellung von Ressourcen Paketen mit **Unity-Version 5.4.5 F1** unterstützt.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-211">Currently asset bundle creation is supported with **Unity version 5.4.5f1.**</span></span>
* <span data-ttu-id="dd2ef-212">Abhängig von der Datenmenge in Ihrem onedrive wird die APP möglicherweise so angezeigt, als ob Sie beim Laden von onedrive-Inhalten angehalten wurde.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-212">Depending on the amount of data in your OneDrive, the app might appear as if it has stopped while loading OneDrive contents</span></span>
* <span data-ttu-id="dd2ef-213">Zurzeit unterstützt die Funktion "Speichern und laden" nur primitive Objekte.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-213">Currently, Save and Load feature only supports primitive objects</span></span>
* <span data-ttu-id="dd2ef-214">Text-, Ton-, Video-und Fotomenüs sind im Kontextmenü deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-214">Text, Sound, Video and Photo menus are disabled on the contextual menu</span></span>
* <span data-ttu-id="dd2ef-215">Die Wiedergabe Schaltfläche im Menüband-Menü löscht die Manipulation Gizmos</span><span class="sxs-lookup"><span data-stu-id="dd2ef-215">The Play button on the Tool Belt menu clears the manipulation gizmos</span></span>

## <a name="sharing-your-sketches"></a><span data-ttu-id="dd2ef-216">Freigeben von Skizzen</span><span class="sxs-lookup"><span data-stu-id="dd2ef-216">Sharing your sketches</span></span>

<span data-ttu-id="dd2ef-217">Sie können das Video Aufzeichnungs Feature in hololens verwenden, indem Sie "Hey Cortana, Start/stoppaufzeichnung" sagen.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-217">You can use the video recording feature in HoloLens by saying 'Hey Cortana, Start/Stop recording'.</span></span> <span data-ttu-id="dd2ef-218">Drücken Sie die Taste nach oben/unten, um ein Bild der Skizze zu machen.</span><span class="sxs-lookup"><span data-stu-id="dd2ef-218">Press the volume up/down key together to take a picture of your sketch.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="dd2ef-219">Informationen zu den Autoren</span><span class="sxs-lookup"><span data-stu-id="dd2ef-219">About the authors</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="dd2ef-220"><b>Dong-Yoon-Park</b></span><span class="sxs-lookup"><span data-stu-id="dd2ef-220"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="dd2ef-221">UX-Designer-@Microsoft</span><span class="sxs-lookup"><span data-stu-id="dd2ef-221">UX Designer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="dd2ef-222"><b>Patrick-Bring</b></span><span class="sxs-lookup"><span data-stu-id="dd2ef-222"><b>Patrick Sebring</b></span></span><br><span data-ttu-id="dd2ef-223">Entwickler @Microsoft</span><span class="sxs-lookup"><span data-stu-id="dd2ef-223">Developer @Microsoft</span></span></td>
</tr>
</table> 
