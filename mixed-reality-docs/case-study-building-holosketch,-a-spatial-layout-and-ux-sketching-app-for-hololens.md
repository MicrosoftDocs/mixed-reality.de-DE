---
title: 'Fallstudie: Erstellen von HoloSketch, eine räumliche Layout und die UX-app für HoloLens skizzieren'
description: HoloSketch ist auf dem Gerät räumliche Layout und UX skizzieren Tool für HoloLens, um holographic Benutzeroberflächen zu erstellen.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, Windows Mixed Reality, skizzieren, app
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594280"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a><span data-ttu-id="9af30-104">Fallstudie: Erstellen von HoloSketch, eine räumliche Layout und die UX-app für HoloLens skizzieren</span><span class="sxs-lookup"><span data-stu-id="9af30-104">Case study - Building HoloSketch, a spatial layout and UX sketching app for HoloLens</span></span>

<span data-ttu-id="9af30-105">HoloSketch ist auf dem Gerät räumliche Layout und UX skizzieren Tool für HoloLens, um holographic Benutzeroberflächen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="9af30-105">HoloSketch is an on-device spatial layout and UX sketching tool for HoloLens to help build holographic experiences.</span></span> <span data-ttu-id="9af30-106">HoloSketch arbeitet mit gekoppelten Bluetooth-Tastatur und Maus als auch Gestik- und Befehle.</span><span class="sxs-lookup"><span data-stu-id="9af30-106">HoloSketch works with a paired Bluetooth keyboard and mouse as well as gesture and voice commands.</span></span> <span data-ttu-id="9af30-107">Der Zweck der HoloSketch ist ein einfaches UX-Layout-Tool für rasche visualisierungs- und Iteration bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="9af30-107">The purpose of HoloSketch is to provide a simple UX layout tool for quick visualization and iteration.</span></span>

<span data-ttu-id="9af30-108">![HoloSketch: Eine räumliche Layout und die UX-app für HoloLens skizzieren.](images/holosketch-image-01-640px.png)</span><span class="sxs-lookup"><span data-stu-id="9af30-108">![HoloSketch: A spatial layout and UX sketching app for HoloLens.](images/holosketch-image-01-640px.png)</span></span><br>
<span data-ttu-id="9af30-109">*HoloSketch: räumliche Layout und die UX-app für HoloLens skizzieren*</span><span class="sxs-lookup"><span data-stu-id="9af30-109">*HoloSketch: spatial layout and UX sketching app for HoloLens*</span></span>

<span data-ttu-id="9af30-110">![Eine einfache Benutzeroberfläche Tool "Layout" für rasche visualisierungs- und Iteration.](images/holosketch-image-02.png)</span><span class="sxs-lookup"><span data-stu-id="9af30-110">![A simple UX layout tool for quick visualization and iteration.](images/holosketch-image-02.png)</span></span><br>
<span data-ttu-id="9af30-111">*Ein einfaches UX-Layout-Tool für rasche visualisierungs- und iteration*</span><span class="sxs-lookup"><span data-stu-id="9af30-111">*A simple UX layout tool for quick visualization and iteration*</span></span>

## <a name="features"></a><span data-ttu-id="9af30-112">Features</span><span class="sxs-lookup"><span data-stu-id="9af30-112">Features</span></span>

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a><span data-ttu-id="9af30-113">-Grundtypen für die schnelle Studien und skalieren – Erstellen von Prototypen</span><span class="sxs-lookup"><span data-stu-id="9af30-113">Primitives for quick studies and scale-prototyping</span></span>

![Primitive Formen](images/holosketch-primitives-giphy.gif)

<span data-ttu-id="9af30-115">Verwenden Sie primitive-Shapes für schnelle massing Studien und skalieren – Erstellen von Prototypen.</span><span class="sxs-lookup"><span data-stu-id="9af30-115">Use primitive shapes for quick massing studies and scale-prototyping.</span></span>

### <a name="import-objects-through-onedrive"></a><span data-ttu-id="9af30-116">Importieren von Objekten über OneDrive</span><span class="sxs-lookup"><span data-stu-id="9af30-116">Import objects through OneDrive</span></span>

![Importieren von Objekten](images/holosketch-importobjects-giphy.gif)

<span data-ttu-id="9af30-118">PNG/JPG-Bilder oder FBX-3D-Objekte importieren (erfordert die paketerstellung in Unity) in den mixed Reality-Bereich über OneDrive.</span><span class="sxs-lookup"><span data-stu-id="9af30-118">Import PNG/JPG images or 3D FBX objects(requires packaging in Unity) into the mixed reality space through OneDrive.</span></span>

### <a name="manipulate-objects"></a><span data-ttu-id="9af30-119">Bearbeiten von Objekten</span><span class="sxs-lookup"><span data-stu-id="9af30-119">Manipulate objects</span></span>

![Bearbeiten von Objekten](images/manipulate-objects-640px.jpg)

<span data-ttu-id="9af30-121">Bearbeiten von Objekten (verschieben/drehen/skalieren) mit einer vertrauten 3D-Objekt-Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="9af30-121">Manipulate objects (move/rotate/scale) with a familiar 3D object interface.</span></span>

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a><span data-ttu-id="9af30-122">Bluetooth, Maus und Tastatur, Gesten und Stimme Befehle</span><span class="sxs-lookup"><span data-stu-id="9af30-122">Bluetooth, mouse/keyboard, gestures and voice commands</span></span>

![unterstützt die Bluetooth](images/supports-bluetooth-640px.jpg)

<span data-ttu-id="9af30-124">HoloSketch unterstützt Bluetooth-Tastatur oder Maus, Gesten und Sprachbefehle.</span><span class="sxs-lookup"><span data-stu-id="9af30-124">HoloSketch supports Bluetooth mouse/keyboard, gestures and voice commands.</span></span>

## <a name="background"></a><span data-ttu-id="9af30-125">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="9af30-125">Background</span></span>

### <a name="importance-of-experiencing-your-design-in-the-device"></a><span data-ttu-id="9af30-126">Wichtigkeit der auf Ihren Entwurf auf dem Gerät</span><span class="sxs-lookup"><span data-stu-id="9af30-126">Importance of experiencing your design in the device</span></span>

<span data-ttu-id="9af30-127">Wenn Sie etwas für HoloLens entwerfen, ist es wichtig, damit können Sie Ihren Entwurf auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="9af30-127">When you design something for HoloLens, it is important to experience your design in the device.</span></span> <span data-ttu-id="9af30-128">Einer der größten Herausforderungen in mixed Reality-app-Design ist, dass es schwer, um die Bedeutung von Skalierung, Position und Tiefe, insbesondere über herkömmliche 2D Skizzen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="9af30-128">One of the biggest challenges in mixed reality app design is that it is hard to get the sense of scale, position and depth, especially through traditional 2D sketches.</span></span>

### <a name="cost-of-2d-based-communication"></a><span data-ttu-id="9af30-129">Kosten für 2D-basierte Kommunikation</span><span class="sxs-lookup"><span data-stu-id="9af30-129">Cost of 2D based communication</span></span>

<span data-ttu-id="9af30-130">Um die UX-Flows und andere Szenarien effektiv kommunizieren zu können, kann ein Designer schließlich verbringen viel Zeit mit der Erstellung von Ressourcen mithilfe der herkömmlichen 2D Tools wie Illustrator, Photoshop und PowerPoint.</span><span class="sxs-lookup"><span data-stu-id="9af30-130">To effectively communicate UX flows and scenarios to others, a designer may end up spending a lot of time creating assets using traditional 2D tools such as Illustrator, Photoshop and PowerPoint.</span></span> <span data-ttu-id="9af30-131">Diese Entwürfe 2D erfordern häufig zusätzlichen Aufwand konvertieren ihn in 3D.</span><span class="sxs-lookup"><span data-stu-id="9af30-131">These 2D designs often require additional effort to convert them it into 3D.</span></span> <span data-ttu-id="9af30-132">Einige Ideen in diese Übersetzung von 2D in 3D verloren.</span><span class="sxs-lookup"><span data-stu-id="9af30-132">Some ideas are lost in this translation from 2D to 3D.</span></span>

### <a name="complex-deployment-process"></a><span data-ttu-id="9af30-133">Komplexe Bereitstellung</span><span class="sxs-lookup"><span data-stu-id="9af30-133">Complex deployment process</span></span>

<span data-ttu-id="9af30-134">Gemischte Realität eine neuen Zeichenbereich für uns daher viel hat und der Versuch und Irrtum naturgemäß verbunden.</span><span class="sxs-lookup"><span data-stu-id="9af30-134">Since mixed reality is a new canvas for us, it involves a lot of design iteration and trial and error by its nature.</span></span> <span data-ttu-id="9af30-135">Für den Designer, die mit Tools wie z. B. Unity und Visual Studio nicht vertraut sind, ist es nicht einfach etwas in HoloLens zusammengestellt.</span><span class="sxs-lookup"><span data-stu-id="9af30-135">For designer who are not familiar with tools such as Unity and Visual Studio, it is not easy to put something together in HoloLens.</span></span> <span data-ttu-id="9af30-136">In der Regel müssen Sie das nachfolgend beschriebene Verfahren durchlaufen, um Ihre 2D-/3D-Bilder auf dem Gerät finden Sie unter.</span><span class="sxs-lookup"><span data-stu-id="9af30-136">Typically you have to go through the process below to see your 2D/3D artwork in the device.</span></span> <span data-ttu-id="9af30-137">Dies war eine große Hürde für Designer, durchlaufen schnell von Ideen und Szenarien.</span><span class="sxs-lookup"><span data-stu-id="9af30-137">This was a big barrier for designers iterating on ideas and scenarios quickly.</span></span>

<span data-ttu-id="9af30-138">![Komplexe Bereitstellung](images/holosketch-image-03-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="9af30-138">![Complex deployment process](images/holosketch-image-03-1000px.png)</span></span><br>
<span data-ttu-id="9af30-139">*Bereitstellungsprozess*</span><span class="sxs-lookup"><span data-stu-id="9af30-139">*Deployment process*</span></span>

### <a name="simplified-process-with-holosketch"></a><span data-ttu-id="9af30-140">Vereinfachter Prozess mit HoloSketch</span><span class="sxs-lookup"><span data-stu-id="9af30-140">Simplified process with HoloSketch</span></span>

<span data-ttu-id="9af30-141">Wir wollten mit HoloSketch diesen Prozess zu vereinfachen, ohne die Einbeziehung von Entwicklungstools und Device Portal Kopplung.</span><span class="sxs-lookup"><span data-stu-id="9af30-141">With HoloSketch, we wanted to simplify this process without involving development tools and device portal pairing.</span></span> <span data-ttu-id="9af30-142">OneDrive zu verwenden, können Benutzer problemlos 2D-/3D-Assets in HoloLens versetzen.</span><span class="sxs-lookup"><span data-stu-id="9af30-142">Using OneDrive, users can easily put 2D/3D assets into HoloLens.</span></span>

<span data-ttu-id="9af30-143">![Vereinfachter Prozess mit HoloSketch](images/holosketch-image-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="9af30-143">![Simplified process with HoloSketch](images/holosketch-image-04-1000px.png)</span></span><br>
<span data-ttu-id="9af30-144">*Vereinfachter Prozess mit HoloSketch*</span><span class="sxs-lookup"><span data-stu-id="9af30-144">*Simplified process with HoloSketch*</span></span>

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a><span data-ttu-id="9af30-145">Ermutigend dreidimensionalen Design-Überlegungen und Lösungen</span><span class="sxs-lookup"><span data-stu-id="9af30-145">Encouraging three-dimensional design thinking and solutions</span></span>

<span data-ttu-id="9af30-146">Wir dachten, dass dieses Tool Designer erhalten Gelegenheit, zu entdecken Sie Lösungen in einem tatsächlich dreidimensionalen Raum und nicht in 2D unterbrochen werden.</span><span class="sxs-lookup"><span data-stu-id="9af30-146">We thought this tool would give designers an opportunity to explore solutions in a truly three-dimensional space and not be stuck in 2D.</span></span> <span data-ttu-id="9af30-147">Sie müssen überlegen, 3D Hintergrund für ihre Benutzeroberfläche erstellen, da der Hintergrund der realen Welt im Fall von Hololens ist.</span><span class="sxs-lookup"><span data-stu-id="9af30-147">They don’t have to think about creating a 3D background for their UI since the background is the real world in the case of Hololens.</span></span> <span data-ttu-id="9af30-148">HoloSketch wird eine Möglichkeit, sich dann 3D Entwurf für Hololens-Designer geöffnet.</span><span class="sxs-lookup"><span data-stu-id="9af30-148">HoloSketch opens up a way for designers to easily explore 3D design on Hololens.</span></span>

## <a name="get-started"></a><span data-ttu-id="9af30-149">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="9af30-149">Get Started</span></span>

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a><span data-ttu-id="9af30-150">Vorgehensweise beim Importieren von 2D-Bilder JPG-/PNG-() in HoloSketch</span><span class="sxs-lookup"><span data-stu-id="9af30-150">How to import 2D images (JPG/PNG) into HoloSketch</span></span>

* <span data-ttu-id="9af30-151">JPG-/PNG-Bilder in Ihrem OneDrive-Ordner "Dokumente/HoloSketch" hochladen.</span><span class="sxs-lookup"><span data-stu-id="9af30-151">Upload JPG/PNG images to your OneDrive folder ‘Documents/HoloSketch’.</span></span>
* <span data-ttu-id="9af30-152">Wählen Sie im Menü "OneDrive" in HoloSketch werden Sie auswählen, und übertragen Sie das Abbild in der Umgebung.</span><span class="sxs-lookup"><span data-stu-id="9af30-152">From the OneDrive menu in HoloSketch, you will be able to select and place the image in the environment.</span></span>

<span data-ttu-id="9af30-153">![Importieren von 2D-Bilder](images/import-2d-images-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="9af30-153">![Importing 2D images](images/import-2d-images-1000px.jpg)</span></span><br>
<span data-ttu-id="9af30-154">*Importieren von Images und 3D-Objekte über OneDrive*</span><span class="sxs-lookup"><span data-stu-id="9af30-154">*Importing images and 3D objects through OneDrive*</span></span>

### <a name="how-to-import-3d-objects-into-holosketch"></a><span data-ttu-id="9af30-155">Vorgehensweise beim Importieren von 3D-Objekten in HoloSketch</span><span class="sxs-lookup"><span data-stu-id="9af30-155">How to import 3D objects into HoloSketch</span></span>

<span data-ttu-id="9af30-156">Befolgen Sie bevor Sie in Ihrem OneDrive-Ordner hochladen die folgenden Schritte zum Packen Ihrer 3D-Objekte in einem Unity Asset Bündel.</span><span class="sxs-lookup"><span data-stu-id="9af30-156">Before uploading to your OneDrive folder, please follow the steps below to package your 3D objects into a Unity asset bundle.</span></span> <span data-ttu-id="9af30-157">Mit diesem Prozess können Sie Ihre FBX/OBJ-Dateien von 3D Software, z. B. Maya, Kino 4D und Microsoft Paint 3D importieren.</span><span class="sxs-lookup"><span data-stu-id="9af30-157">Using this process you can import your FBX/OBJ files from 3D software such as Maya, Cinema 4D and Microsoft Paint 3D.</span></span>

>[!IMPORTANT]
><span data-ttu-id="9af30-158">Derzeit wird die medienobjekterstellung-Bundle mit Unity Version 5.4.5f1 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9af30-158">Currently, asset bundle creation is supported with Unity version 5.4.5f1.</span></span>

1. <span data-ttu-id="9af30-159">Herunterladen und öffnen Sie das Unity-Projekt ["AssetBunlder_Unity"](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span><span class="sxs-lookup"><span data-stu-id="9af30-159">Download and open the Unity project ['AssetBunlder_Unity'](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity).</span></span> <span data-ttu-id="9af30-160">Dieses Unity-Projekt enthält das Skript für die Generierung der Bundle-Asset an.</span><span class="sxs-lookup"><span data-stu-id="9af30-160">This Unity project includes the script for the bundle asset generation.</span></span>
2. <span data-ttu-id="9af30-161">Erstellen Sie einen neuen "gameobject".</span><span class="sxs-lookup"><span data-stu-id="9af30-161">Create a new GameObject.</span></span>
3. <span data-ttu-id="9af30-162">Der Name der basierend auf dem Inhalt "gameobject".</span><span class="sxs-lookup"><span data-stu-id="9af30-162">Name the GameObject based on the contents.</span></span>
4. <span data-ttu-id="9af30-163">Klicken Sie im Bereich mit den Inspektor klicken Sie auf "Komponente hinzufügen", und fügen Sie "Box-Collider" hinzu.</span><span class="sxs-lookup"><span data-stu-id="9af30-163">In the Inspector panel, click ‘Add Component’ and add ‘Box Collider’.</span></span> 

   ![Klicken Sie im Bereich mit den Inspektor klicken Sie auf "Komponente hinzufügen", und fügen Sie "Box-Collider" hinzu](images/holosketch-10a-assetbundles-1000px.png)
   
   ![Klicken Sie in den Inspektor-Bereich klicken Sie auf "Komponente hinzufügen", und fügen Sie 'Box-Collider' #2](images/holosketch-10b-assetbundles-1000px.png)

5. <span data-ttu-id="9af30-166">Importieren Sie FBX-3D-Datei, indem Sie in den Projektbereich ziehen.</span><span class="sxs-lookup"><span data-stu-id="9af30-166">Import the 3D FBX file by dragging it into the project panel.</span></span>
6. <span data-ttu-id="9af30-167">Ziehen Sie das Objekt in den Bereich für die Hierarchie **unter Ihrer neuen "gameobject"**.</span><span class="sxs-lookup"><span data-stu-id="9af30-167">Drag the object into the Hierarchy panel **under your new GameObject**.</span></span>

   ![Ziehen Sie das Objekt in den Bereich der Hierarchie unter Ihrem neuen "gameobject"](images/holosketch-12-assetbundles-1000px.png)

7. <span data-ttu-id="9af30-169">Passen Sie die Dimension "collider" aus, wenn sie nicht das Objekt entspricht.</span><span class="sxs-lookup"><span data-stu-id="9af30-169">Adjust the collider dimension if it does not match the object.</span></span> <span data-ttu-id="9af30-170">Drehen Sie das Objekt, das auftreten **z-Achse**.</span><span class="sxs-lookup"><span data-stu-id="9af30-170">Rotate the object to face **Z-axis**.</span></span>

   ![Passen Sie "collider" Dimension aus, wenn sie nicht das Objekt entspricht.](images/holosketch-13-assetbundles-1000px.png)

8. <span data-ttu-id="9af30-172">Ziehen Sie das Objekt aus dem Bereich der Hierarchie, in das Projektfenster, **erleichtern prefab**.</span><span class="sxs-lookup"><span data-stu-id="9af30-172">Drag the object from the Hierarchy panel to the Project panel to **make it prefab**.</span></span>
9. <span data-ttu-id="9af30-173">Klicken Sie unten im Inspektor-Bereich klicken Sie auf die Dropdownliste, erstellen Sie, und weisen Sie einen neuen eindeutigen Namen.</span><span class="sxs-lookup"><span data-stu-id="9af30-173">On the bottom of the inspector panel, click the dropdown, create and assign a new unique name.</span></span> <span data-ttu-id="9af30-174">Folgende Beispiel zeigt, hinzufügen und Zuweisen von 'Brownchair' für den AssetBundle-Namen.</span><span class="sxs-lookup"><span data-stu-id="9af30-174">Below example shows adding and assigning 'brownchair' for the AssetBundle Name.</span></span> 

   ![Am unteren Rand der Inspektor-Bereich klicken Sie auf die Dropdownliste, und weisen Sie einen neuen eindeutigen Namen.](images/holosketch-14-assetbundles-1000px.png)

10. <span data-ttu-id="9af30-176">Bereiten Sie ein Miniaturbild für das Modellobjekt vor.</span><span class="sxs-lookup"><span data-stu-id="9af30-176">Prepare a thumbnail image for the model object.</span></span> 
   <span data-ttu-id="9af30-177">![Ziehen Sie ein Bild in der Projektbereich, und weisen Sie den Namen für das Objekt.](images/holosketch-15-assetbundles-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="9af30-177">![Drag an image into the project panel and assign the name used for the object.](images/holosketch-15-assetbundles-1000px.png)</span></span>

11. <span data-ttu-id="9af30-178">Erstellen Sie einen Ordner namens "Assetbundles" Ordner "Asset" des Unity-Projekts.</span><span class="sxs-lookup"><span data-stu-id="9af30-178">Create a folder named ‘Assetbundles’ under the Unity project’s ‘Asset’ folder.</span></span>

12. <span data-ttu-id="9af30-179">Wählen Sie im Menü Assets "AssetBundles erstellen", um die Datei zu generieren.</span><span class="sxs-lookup"><span data-stu-id="9af30-179">From the Assets menu, select ‘Build AssetBundles’ to generate file.</span></span> 
   <span data-ttu-id="9af30-180">![Wählen Sie im Menü Assets "AssetBundles erstellen", um die Datei zu generieren.](images/holosketch-15a-assetbundles.png)</span><span class="sxs-lookup"><span data-stu-id="9af30-180">![From the Assets menu, select ‘Build AssetBundles’ to generate file.](images/holosketch-15a-assetbundles.png)</span></span>


13. <span data-ttu-id="9af30-181">**Hochladen Sie die generierte Datei wird in den /Files/Documents/HoloSketch-Ordner in OneDrive.**</span><span class="sxs-lookup"><span data-stu-id="9af30-181">**Upload the generated file to the /Files/Documents/HoloSketch folder on OneDrive.**</span></span> <span data-ttu-id="9af30-182">Laden Sie nur die Asset_unique_name-Datei hoch.</span><span class="sxs-lookup"><span data-stu-id="9af30-182">Upload the asset_unique_name file only.</span></span> <span data-ttu-id="9af30-183">Sie müssen nicht Manifestdateien oder AssetBundles-Datei hochladen.</span><span class="sxs-lookup"><span data-stu-id="9af30-183">You don’t need to upload manifest files or AssetBundles file.</span></span> <br>
<span data-ttu-id="9af30-184">![Hinzufügen von Dateien, Dateien/Dokumente/HoloSketch/Ordner](images/holosketch-onedriveupload-1000px.png)
![hinzugefügten 3D-Objekt in HoloSketchs OneDrive-Menü wird angezeigt](images/holosketch-14-onedriveexample-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="9af30-184">![Add files to Files/Documents/HoloSketch/ folder](images/holosketch-onedriveupload-1000px.png)
![You will see added 3D object in HoloSketch's OneDrive menu](images/holosketch-14-onedriveexample-1000px.jpg)</span></span>

## <a name="how-to-manipulate-the-objects"></a><span data-ttu-id="9af30-185">Wie Sie die Objekte bearbeiten</span><span class="sxs-lookup"><span data-stu-id="9af30-185">How to manipulate the objects</span></span>

<span data-ttu-id="9af30-186">HoloSketch unterstützt die herkömmliche-Schnittstelle, die häufig verwendet wird, in 3D Software.</span><span class="sxs-lookup"><span data-stu-id="9af30-186">HoloSketch supports the traditional interface that is widely used in 3D software.</span></span> <span data-ttu-id="9af30-187">Sie können verschieben, drehen, Skalieren die Objekte mit Gesten und eine Maus.</span><span class="sxs-lookup"><span data-stu-id="9af30-187">You can use move, rotate, scale the objects with gestures and a mouse.</span></span> <span data-ttu-id="9af30-188">Sie können schnell zwischen verschiedenen Modi mit Sprach- oder Tastatur wechseln.</span><span class="sxs-lookup"><span data-stu-id="9af30-188">You can quickly switch between different modes with voice or keyboard.</span></span>

### <a name="object-manipulation-modes"></a><span data-ttu-id="9af30-189">Modi zum Bearbeiten von Objekt</span><span class="sxs-lookup"><span data-stu-id="9af30-189">Object manipulation modes</span></span>

<span data-ttu-id="9af30-190">![Wie Sie die Objekte bearbeiten](images/holosketch-image-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="9af30-190">![How to manipulate the objects](images/holosketch-image-06-1000px.png)</span></span><br>
<span data-ttu-id="9af30-191">*Wie Sie die Objekte bearbeiten*</span><span class="sxs-lookup"><span data-stu-id="9af30-191">*How to manipulate the objects*</span></span>

### <a name="contextual-and-tool-belt-menus"></a><span data-ttu-id="9af30-192">Menüs Kontext- und Toolsammlung</span><span class="sxs-lookup"><span data-stu-id="9af30-192">Contextual and Tool Belt menus</span></span>

<span data-ttu-id="9af30-193">**Verwenden im Kontextmenü**</span><span class="sxs-lookup"><span data-stu-id="9af30-193">**Using the Contextual Menu**</span></span>

<span data-ttu-id="9af30-194">Doppelte Tippen Sie auf die über das Kontextmenü zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="9af30-194">Double air tap to open the Contextual Menu.</span></span> 

<span data-ttu-id="9af30-195">Menüelemente:</span><span class="sxs-lookup"><span data-stu-id="9af30-195">Menu items:</span></span>
* <span data-ttu-id="9af30-196">**Layout-Oberfläche:** Dies ist eine 3D-Rastersystem, können Sie das Layout mehrerer Objekte und diese als Gruppe verwalten.</span><span class="sxs-lookup"><span data-stu-id="9af30-196">**Layout Surface:** This is a 3D grid system where you can layout multiple objects and manage them as a group.</span></span> <span data-ttu-id="9af30-197">Double-tippbewegung auf der Layout-Oberfläche, um diese Objekte hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="9af30-197">Double air-tap on the Layout Surface to add objects to it.</span></span>
* <span data-ttu-id="9af30-198">**Primitive Typen:** Verwenden Sie Cubes, die Kugeln, Touren und Kegel für massing Studien.</span><span class="sxs-lookup"><span data-stu-id="9af30-198">**Primitives:** Use cubes, spheres, cylinders and cones for massing studies.</span></span>
* <span data-ttu-id="9af30-199">**OneDrive:** Öffnen Sie die OneDrive-Menü zum Importieren von Objekten.</span><span class="sxs-lookup"><span data-stu-id="9af30-199">**OneDrive:** Open the OneDrive menu to import objects.</span></span>
* <span data-ttu-id="9af30-200">**Hilfe:** Zeigt Hilfe an.</span><span class="sxs-lookup"><span data-stu-id="9af30-200">**Help:** Displays help screen.</span></span>

<span data-ttu-id="9af30-201">![Kontextmenü](images/holosketch-image-07.png)</span><span class="sxs-lookup"><span data-stu-id="9af30-201">![Contextual menu](images/holosketch-image-07.png)</span></span><br>
<span data-ttu-id="9af30-202">*Kontextmenü*</span><span class="sxs-lookup"><span data-stu-id="9af30-202">*Contextual menu*</span></span>

<span data-ttu-id="9af30-203">**Verwenden das Tool Belt-Menü**</span><span class="sxs-lookup"><span data-stu-id="9af30-203">**Using the Tool Belt Menu**</span></span>

<span data-ttu-id="9af30-204">Verschieben, drehen, skalieren, speichern und Laden Szene im Tool Belt-Menü verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="9af30-204">Move, Rotate, Scale, Save, and Load Scene are available from the Tool Belt Menu.</span></span> 

## <a name="using-keyboard-gestures-and-voice-commands"></a><span data-ttu-id="9af30-205">Mithilfe der Tastatur, Gesten und Sprachbefehle</span><span class="sxs-lookup"><span data-stu-id="9af30-205">Using keyboard, gestures and voice commands</span></span>

<span data-ttu-id="9af30-206">![Tastatur, Gesten und Sprachbefehle](images/holosketch-image-08-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="9af30-206">![Keyboard, Gestures and Voice Commands](images/holosketch-image-08-1000px.png)</span></span><br>
<span data-ttu-id="9af30-207">*Tastatur, Gesten und Sprachbefehle*</span><span class="sxs-lookup"><span data-stu-id="9af30-207">*Keyboard, gestures, and voice commands*</span></span>

## <a name="download-the-app"></a><span data-ttu-id="9af30-208">Die app herunterladen</span><span class="sxs-lookup"><span data-stu-id="9af30-208">Download the app</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><span data-ttu-id="9af30-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Herunterladen Sie und installieren Sie die app HoloSketch kostenlos aus dem Microsoft Store</a>
</span><span class="sxs-lookup"><span data-stu-id="9af30-209"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Download and install the HoloSketch app for free from the Microsoft Store</a>
</span></span></td>
</tr>
</table>

## <a name="known-issues"></a><span data-ttu-id="9af30-210">Bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="9af30-210">Known issues</span></span>
* <span data-ttu-id="9af30-211">Erstellung von Medienobjekten Bundle wird derzeit unterstützt, mit **Unity Version 5.4.5f1.**</span><span class="sxs-lookup"><span data-stu-id="9af30-211">Currently asset bundle creation is supported with **Unity version 5.4.5f1.**</span></span>
* <span data-ttu-id="9af30-212">Abhängig von der Menge der Daten in Ihrem OneDrive kann die app angezeigt, als ob er, beim Laden der OneDrive-Inhalt beendet wurde</span><span class="sxs-lookup"><span data-stu-id="9af30-212">Depending on the amount of data in your OneDrive, the app might appear as if it has stopped while loading OneDrive contents</span></span>
* <span data-ttu-id="9af30-213">Speichern Sie derzeit und Last-Funktion unterstützt nur primitive Objekte</span><span class="sxs-lookup"><span data-stu-id="9af30-213">Currently, Save and Load feature only supports primitive objects</span></span>
* <span data-ttu-id="9af30-214">Text, Audio-, Video- und Foto-Menüs sind im Kontextmenü deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="9af30-214">Text, Sound, Video and Photo menus are disabled on the contextual menu</span></span>
* <span data-ttu-id="9af30-215">Die entsprechende Schaltfläche, auf das Menü "Toolsammlung" löscht die Manipulation gizmos</span><span class="sxs-lookup"><span data-stu-id="9af30-215">The Play button on the Tool Belt menu clears the manipulation gizmos</span></span>

## <a name="sharing-your-sketches"></a><span data-ttu-id="9af30-216">Freigeben Ihrer Skizzen</span><span class="sxs-lookup"><span data-stu-id="9af30-216">Sharing your sketches</span></span>

<span data-ttu-id="9af30-217">Sie können die videoaufzeichnung-Funktion in HoloLens verwenden, indem mit dem Text "Hey Cortana, Aufnahme starten/beenden".</span><span class="sxs-lookup"><span data-stu-id="9af30-217">You can use the video recording feature in HoloLens by saying 'Hey Cortana, Start/Stop recording'.</span></span> <span data-ttu-id="9af30-218">Drücken Sie die Volume-Schlüssel zusammen, um einen Überblick über Ihre Sketch werden nach oben/unten aus.</span><span class="sxs-lookup"><span data-stu-id="9af30-218">Press the volume up/down key together to take a picture of your sketch.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="9af30-219">Über die Autoren</span><span class="sxs-lookup"><span data-stu-id="9af30-219">About the authors</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="9af30-220"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="9af30-220"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="9af30-221">UX-Designer @Microsoft</span><span class="sxs-lookup"><span data-stu-id="9af30-221">UX Designer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="9af30-222"><b>Patrick Sebring</b></span><span class="sxs-lookup"><span data-stu-id="9af30-222"><b>Patrick Sebring</b></span></span><br><span data-ttu-id="9af30-223">Entwickler @Microsoft</span><span class="sxs-lookup"><span data-stu-id="9af30-223">Developer @Microsoft</span></span></td>
</tr>
</table> 
