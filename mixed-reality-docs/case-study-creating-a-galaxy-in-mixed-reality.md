---
title: 'Fallstudie: Erstellen einer in mixed reality'
description: Vor Microsoft HoloLens, fragten wir unsere Entwickler-Community welche Art von app sie möchten ein erfahrener internes Team für das neue Gerät zu erstellen. Mehr als 5000 Ideen wurden freigegeben und nach einem 24-Stunden-Twitter-Abruf der Gewinner war ein Konzept namens "Galaxy-Explorer".
author: KarimLUCCIN
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy-Explorer, HoloLens, Windows Mixed Reality, Teilen Ihre Idee, Fallstudie
ms.openlocfilehash: a478eaa35144a8ee0fbeaeb43cec4b9f901890ab
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604834"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a><span data-ttu-id="7314c-105">Fallstudie: Erstellen einer in mixed reality</span><span class="sxs-lookup"><span data-stu-id="7314c-105">Case study - Creating a galaxy in mixed reality</span></span>

<span data-ttu-id="7314c-106">Vor Microsoft HoloLens, fragten wir unsere Entwickler-Community welche Art von app sie möchten ein erfahrener internes Team für das neue Gerät zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="7314c-106">Before Microsoft HoloLens shipped, we asked our developer community what kind of app they'd like to see an experienced internal team build for the new device.</span></span> <span data-ttu-id="7314c-107">Mehr als 5000 Ideen wurden freigegeben und nach einem 24-Stunden-Twitter-Abruf der Gewinner eine Idee, die aufgerufen wurde [Galaxy Explorer](galaxy-explorer.md).</span><span class="sxs-lookup"><span data-stu-id="7314c-107">More than 5000 ideas were shared, and after a 24-hour Twitter poll, the winner was an idea called [Galaxy Explorer](galaxy-explorer.md).</span></span>

<span data-ttu-id="7314c-108">Sprechen Sie Andy Zibits, den Lead Art, auf das Projekt, und Karim Luccin, des Teams Grafiken Engineer, über die gemeinsamen Initiative zwischen Kunst und entwickeln, die mit der Erstellung von eine genaue, interaktive Darstellung der Galaxy arbeiten im Galaxy-Explorer geführt hat.</span><span class="sxs-lookup"><span data-stu-id="7314c-108">Andy Zibits, the art lead on the project, and Karim Luccin, the team's graphics engineer, talk about the collaborative effort between art and engineering that led to the creation of an accurate, interactive representation of the Milky Way galaxy in Galaxy Explorer.</span></span>

## <a name="the-tech"></a><span data-ttu-id="7314c-109">Der Technologie</span><span class="sxs-lookup"><span data-stu-id="7314c-109">The Tech</span></span>

<span data-ttu-id="7314c-110">[Unser Team](galaxy-explorer.md#meet-the-team) – der zwei Designer drei Entwickler, vier Künstler, ein Producer und einem Tester fiktives – sechs Wochen zum Erstellen einer voll funktionsfähigen app ermöglicht Personen zu lernen und entdecken Sie die Umfangs und das Schöne an unserer Galaxy arbeiten mussten.</span><span class="sxs-lookup"><span data-stu-id="7314c-110">[Our team](galaxy-explorer.md#meet-the-team) - made up of two designers, three developers, four artists, a producer, and one tester — had six weeks to build a fully functional app which would allow people to learn about and explore the vastness and beauty of our Milky Way Galaxy.</span></span>

<span data-ttu-id="7314c-111">Wir wollten die Fähigkeit von HoloLens, direkt in Ihr Platz zum wohnen, 3D-Objekte zu rendern, damit wir uns, dass wir zum Erstellen einer realistischen suchen Galaxy entschieden, wo Benutzer wären können schließen vergrößern und einzelne Sternen, jeweils in eigene herabstürzendes optimal nutzen .</span><span class="sxs-lookup"><span data-stu-id="7314c-111">We wanted to take full advantage of the ability of HoloLens to render 3D objects directly in your living space, so we decided we wanted to create a realistic looking galaxy where people would be able to zoom in close and see individual stars, each on their own trajectories.</span></span>

<span data-ttu-id="7314c-112">In der ersten Woche der Entwicklung haben wir einige Ziele für unsere Darstellung des Galaxy arbeiten: Es benötigt, um die Tiefe, Bewegung und Verhalten volumetrische verfügen – voll von Sternen, die die Form des Galaxy helfen würde.</span><span class="sxs-lookup"><span data-stu-id="7314c-112">In the first week of development, we came up with a few goals for our representation of the Milky Way Galaxy: It needed to have depth, movement, and feel volumetric—full of stars that would help create the shape of the galaxy.</span></span>

<span data-ttu-id="7314c-113">Das Problem mit dem Erstellen einer animierten Galaxy, die Milliarden von Sternen war, dass die bloße Anzahl von einzelnen Elementen, die die zu aktualisierenden pro Bild für HoloLens zum Animieren der CPU-Nutzung zu groß wäre.</span><span class="sxs-lookup"><span data-stu-id="7314c-113">The problem with creating an animated galaxy that had billions of stars was that the sheer number of single elements that need updating would be too big per frame for HoloLens to animate using the CPU.</span></span> <span data-ttu-id="7314c-114">Unsere Lösung bei der eine komplexe Mischung aus Kunst und Wissenschaft.</span><span class="sxs-lookup"><span data-stu-id="7314c-114">Our solution involved a complex mix of art and science.</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="7314c-115">Im Hintergrund</span><span class="sxs-lookup"><span data-stu-id="7314c-115">Behind the scenes</span></span>

<span data-ttu-id="7314c-116">Um Benutzer zum Durchsuchen einzelner Sterne zu ermöglichen, wurde im ersten Schritt herausfinden, wie viele Partikel, die wir auf einmal gerendert werden können.</span><span class="sxs-lookup"><span data-stu-id="7314c-116">To allow people to explore individual stars, our first step was to figure out how many particles we could render at once.</span></span>

### <a name="rendering-particles"></a><span data-ttu-id="7314c-117">Rendern von Partikel</span><span class="sxs-lookup"><span data-stu-id="7314c-117">Rendering particles</span></span>

<span data-ttu-id="7314c-118">Aktuelle CPUs eignen sich hervorragend für die Verarbeitung von serieller Aufgaben und bis zu ein paar paralleler Aufgaben auf einmal (je nachdem wie viele Kerne aufweisen), aber GPUs sind viel effektiver Tausende von Vorgänge parallel verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="7314c-118">Current CPUs are great for processing serial tasks and up to a few parallel tasks at once (depending on how many cores they have), but GPUs are much more effective at processing thousands of operations in parallel.</span></span> <span data-ttu-id="7314c-119">Aber da sie in der Regel nicht gemeinsam den gleichen Speicher wie die CPU nutzen, kann Austauschen von Daten zwischen CPU <> GPU schnell einen Engpass darstellen.</span><span class="sxs-lookup"><span data-stu-id="7314c-119">However, because they don’t usually share the same memory as the CPU, exchanging data between CPU<>GPU can quickly become a bottleneck.</span></span> <span data-ttu-id="7314c-120">Unsere Lösung bestand darin, einer auf der GPU machen, und es muss sich um vollständig live auf der GPU.</span><span class="sxs-lookup"><span data-stu-id="7314c-120">Our solution was to make a galaxy on the GPU, and it had to live completely on the GPU.</span></span>

<span data-ttu-id="7314c-121">Da fingen wir Belastungstests mit Tausenden von Punkt-Partikel in verschiedene Muster.</span><span class="sxs-lookup"><span data-stu-id="7314c-121">We started stress tests with thousands of point particles in various patterns.</span></span> <span data-ttu-id="7314c-122">Dadurch konnten wir die Galaxie für HoloLens, um festzustellen, was funktioniert und was nicht abrufen.</span><span class="sxs-lookup"><span data-stu-id="7314c-122">This allowed us to get the galaxy on HoloLens to see what worked and what didn’t.</span></span>

### <a name="creating-the-position-of-the-stars"></a><span data-ttu-id="7314c-123">Erstellen die Position der Sterne</span><span class="sxs-lookup"><span data-stu-id="7314c-123">Creating the position of the stars</span></span>

<span data-ttu-id="7314c-124">Eines unserer Teammitglieder hatte bereits geschrieben. die C# Code, der Sterne in der ursprünglichen Position generieren würden.</span><span class="sxs-lookup"><span data-stu-id="7314c-124">One of our team members had already written the C# code that would generate stars at their initial position.</span></span> <span data-ttu-id="7314c-125">Die Sternchen sind auf eine Ellipse, und ihre Position kann dadurch beschrieben werden, (**CurveOffset**, **EllipseSize**, **Erhöhung der Rechte**), in denen **CurveOffset**ist der Winkel des Sterns entlang der Ellipse **EllipseSize** ist die Dimension der Ellipse entlang der X-Achse und Z und Erhöhung der richtigen Höhenwinkel des Sterns in die Galaxie.</span><span class="sxs-lookup"><span data-stu-id="7314c-125">The stars are on an ellipse and their position can be described by (**curveOffset**, **ellipseSize**, **elevation**) where **curveOffset** is the angle of the star along the ellipse, **ellipseSize** is the dimension of the ellipse along X and Z, and elevation the proper elevation of the star within the galaxy.</span></span> <span data-ttu-id="7314c-126">Daher erstellen wir einen Puffer ([Unity ComputeBuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)), würde mit einzelnen Stern Attribute initialisiert werden und auf der GPU, in dem sie für den Rest der Benutzeroberfläche Leben würde, zu senden.</span><span class="sxs-lookup"><span data-stu-id="7314c-126">Thus, we can create a buffer ([Unity’s ComputeBuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) that would be initialized with each star attribute and send it on the GPU where it would live for the rest of the experience.</span></span> <span data-ttu-id="7314c-127">Um diesen Puffer zu zeichnen, verwenden wir [Unity DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) die auf einer beliebigen Gruppe von Punkten ermöglicht einen Shader (Code auf einer GPU) ausgeführt, ohne dass eine tatsächliche Mesh, das die Galaxie darstellt:</span><span class="sxs-lookup"><span data-stu-id="7314c-127">To draw this buffer, we use [Unity’s DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) which allows running a shader (code on a GPU) on an arbitrary set of points without having an actual mesh that represents the galaxy:</span></span>

<span data-ttu-id="7314c-128">**CPU:**</span><span class="sxs-lookup"><span data-stu-id="7314c-128">**CPU:**</span></span>




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

<span data-ttu-id="7314c-129">**GPU:**</span><span class="sxs-lookup"><span data-stu-id="7314c-129">**GPU:**</span></span>




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

<span data-ttu-id="7314c-130">Da fingen wir mit unformatierten zirkuläre Mustern mit Tausenden von Partikel.</span><span class="sxs-lookup"><span data-stu-id="7314c-130">We started with raw circular patterns with thousands of particles.</span></span> <span data-ttu-id="7314c-131">Wir erhielten dadurch den Nachweis, dass es erforderlich, dass wir viele Partikel verwalten und führen Sie es mit der Geschwindigkeit der leistungsfähig, aber wir nicht mit der Gesamtform des Galaxy zufrieden waren.</span><span class="sxs-lookup"><span data-stu-id="7314c-131">This gave us the proof we needed that we could manage many particles AND run it at performant speeds, but we weren’t satisfied with the overall shape of the galaxy.</span></span> <span data-ttu-id="7314c-132">Um die Form zu verbessern, haben wir verschiedene Muster und -Partikelsysteme mit einer Drehung von versucht.</span><span class="sxs-lookup"><span data-stu-id="7314c-132">To improve the shape, we attempted various patterns and particle systems with rotation.</span></span> <span data-ttu-id="7314c-133">Dies waren ursprünglich vielversprechend, daran, dass die Anzahl der Partikel und Leistung konsistent sind geblieben, aber die Form eingestellt in der Mitte wurde und Sterne wurden nach außen was realistischer nicht ausgeben.</span><span class="sxs-lookup"><span data-stu-id="7314c-133">These were initially promising because the number of particles and performance stayed consistent, but the shape broke down near the center and the stars were emitting outwardly which wasn't realistic.</span></span> <span data-ttu-id="7314c-134">Wir benötigten eine Ausgabe der Compilerdiagnose, die ermöglichen uns Zeit bearbeiten und die Partikel realistisch, verschieben Sie Schleifen in der Mitte des Galaxy je näher.</span><span class="sxs-lookup"><span data-stu-id="7314c-134">We needed an emission that would allow us to manipulate time and have the particles move realistically, looping ever closer to the center of the galaxy.</span></span>

![Wir haben versucht, verschiedene Muster und -Partikelsysteme, die, wie diese gedreht.](images/galaxy-patterns-500px.png)

<span data-ttu-id="7314c-136">Wir haben versucht, verschiedene Muster und -Partikelsysteme, die, wie diese gedreht.</span><span class="sxs-lookup"><span data-stu-id="7314c-136">We attempted various patterns and particle systems that rotated, like these.</span></span>

<span data-ttu-id="7314c-137">Unser Team hat ein wenig Recherche zu der Möglichkeit Galaxies-Funktion, und wir haben ein benutzerdefiniertes partikelsystem speziell für das Galaxy, damit wir die Partikel auf Grundlage von Ellipsen verschoben werden kann "[Dichte Wave Theorie](https://en.wikipedia.org/wiki/Density_wave_theory)," die theorizes, die die Arme, der eine Galaxy sind die Bereiche, in Konstanten Bewegung, z. B. einen datenverkehrsstau jedoch höhere Dichte.</span><span class="sxs-lookup"><span data-stu-id="7314c-137">Our team did some research about the way galaxies function and we made a custom particle system specifically for the galaxy so that we could move the particles on ellipses based on "[density wave theory](https://en.wikipedia.org/wiki/Density_wave_theory)," which theorizes that the arms of a galaxy are areas of higher density but in constant flux, like a traffic jam.</span></span> <span data-ttu-id="7314c-138">Stabil und solid angezeigt wird, aber die Sternchen sind tatsächlich verschieben in und aus Arms, wie sie ihre jeweiligen Ellipsen verschoben.</span><span class="sxs-lookup"><span data-stu-id="7314c-138">It appears stable and solid, but the stars are actually moving in and out of the arms as they move along their respective ellipses.</span></span> <span data-ttu-id="7314c-139">In unserem System vorhanden, der Partikel nie vorhanden sind auf der CPU – wir die Karten zu generieren und sie alle in der GPU zu orientieren, also das gesamte System einfach Ausgangszustand + Zeit.</span><span class="sxs-lookup"><span data-stu-id="7314c-139">In our system, the particles never exist on the CPU—we generate the cards and orient them all on the GPU, so the whole system is simply initial state + time.</span></span> <span data-ttu-id="7314c-140">Es fortgeschritten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="7314c-140">It progressed like this:</span></span>

![Fortschritt des partikelsystem mit GPU-rendering](images/spiral-galaxy-arms-500px.jpg)

<span data-ttu-id="7314c-142">Fortschritt des partikelsystem mit GPU-rendering</span><span class="sxs-lookup"><span data-stu-id="7314c-142">Progression of particle system with GPU rendering</span></span>


<span data-ttu-id="7314c-143">Sobald genügend Ellipsen hinzugefügt werden, und drehen festgelegt sind, seit die Galaxies Formular "Arms", in denen die Verschiebung von Sternen zusammengeführt.</span><span class="sxs-lookup"><span data-stu-id="7314c-143">Once enough ellipses are added and are set to rotate, the galaxies began to form “arms” where the movement of stars converge.</span></span> <span data-ttu-id="7314c-144">Der Abstand der Sterne entlang jeder elliptischen Pfads wurden einige Zufallszahlen zugewiesen, und jedes Sterns wurde ein wenig mit Feldern fester Breite Zufälligkeit hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="7314c-144">The spacing of the stars along each elliptical path was given some randomness, and each star got a bit of positional randomness added.</span></span> <span data-ttu-id="7314c-145">Dies erstellt eine viel natürlichere aussehende Verteilung von datenverschiebung und Arm-Sternform aus.</span><span class="sxs-lookup"><span data-stu-id="7314c-145">This created a much more natural looking distribution of star movement and arm shape.</span></span> <span data-ttu-id="7314c-146">Schließlich haben wir die Möglichkeit zum Laufwerk Farbe auf Grundlage der Entfernung vom Mittelpunkt hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="7314c-146">Finally, we added the ability to drive color based on distance from center.</span></span>

### <a name="creating-the-motion-of-the-stars"></a><span data-ttu-id="7314c-147">Erstellen die Bewegung der Sterne</span><span class="sxs-lookup"><span data-stu-id="7314c-147">Creating the motion of the stars</span></span>

<span data-ttu-id="7314c-148">Um die allgemeine Stern Bewegung zu animieren, mussten wir einen Konstanten Winkel für jeden Frame hinzufügen und die abzurufenden Sternen, die auf die Auslassungspunkte mit konstanter Geschwindigkeit radiale verschieben.</span><span class="sxs-lookup"><span data-stu-id="7314c-148">To animate the general star motion, we needed to add a constant angle for each frame and to get stars moving along their ellipses at a constant radial velocity.</span></span> <span data-ttu-id="7314c-149">Dies ist der Hauptgrund für die Verwendung von **CurveOffset**.</span><span class="sxs-lookup"><span data-stu-id="7314c-149">This is the primary reason for using **curveOffset**.</span></span> <span data-ttu-id="7314c-150">Dies ist nicht technisch korrekt, Sterne werden entlang der lange Seiten der Ellipsen schneller, aber die allgemeine Bewegung gute spürbar.</span><span class="sxs-lookup"><span data-stu-id="7314c-150">This isn’t technically correct as stars will move faster along the long sides of the ellipses, but the general motion felt good.</span></span>

![Sterne agieren Sie schneller auf lange Bogens an den Rändern langsamer.](images/ellipse-movement.jpg)

<span data-ttu-id="7314c-152">Sterne agieren Sie schneller auf lange Bogens an den Rändern langsamer.</span><span class="sxs-lookup"><span data-stu-id="7314c-152">Stars move faster on the long arc, slower on the edges.</span></span>


<span data-ttu-id="7314c-153">Mit diesem jedes Sterns vollständig von beschrieben wird (**CurveOffset**, **EllipseSize**, **Erhöhung der Rechte**, **Alter**), in denen **Alter** ist eine Ansammlung der die Gesamtzeit, die seit dem Laden der Szene vergangen ist.</span><span class="sxs-lookup"><span data-stu-id="7314c-153">With that, each star is fully described by (**curveOffset**, **ellipseSize**, **elevation**, **Age**) where **Age** is an accumulation of the total time that has passed since the scene was loaded.</span></span>




```
float3 ComputeStarPosition(StarDescriptor star)
{

  float curveOffset = star.curveOffset + Age;
  
  // this will be coded as a “sincos” on the hardware which will compute both sides
  float x = cos(curveOffset) * star.xRadii;
  float z = sin(curveOffset) * star.zRadii;
   
  return float3(x, star.elevation, z);
  
}
```

<span data-ttu-id="7314c-154">Das hat uns ermöglicht, um Zehntausende von Sternen einmal am Anfang der Anwendung zu generieren, und wir einen einzelner Satz von Sternen, die auf den eingerichteten Kurven animiert.</span><span class="sxs-lookup"><span data-stu-id="7314c-154">This allowed us to generate tens of thousands of stars once at the start of the application, then we animated a singled set of stars along the established curves.</span></span> <span data-ttu-id="7314c-155">Da alles, was auf der GPU ist, kann das System alle Sterne parallel ohne Kosten für die CPU animieren.</span><span class="sxs-lookup"><span data-stu-id="7314c-155">Since everything is on the GPU, the system can animate all the stars in parallel at no cost to the CPU.</span></span>

![Hier ist, wie es beim Zeichnen von weißen Quads aussieht.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="7314c-157">Hier ist, wie es beim Zeichnen von weißen Quads aussieht.</span><span class="sxs-lookup"><span data-stu-id="7314c-157">Here’s what it looks like when drawing white quads.</span></span>



<span data-ttu-id="7314c-158">Um jedes Gesicht Quad die Kamera zu machen, verwendet haben wir einen Geometrie-Shader, jede Stern Position in einem 2D-Rechteck auf dem Bildschirm zu transformieren, die unsere Stern Textur enthalten soll.</span><span class="sxs-lookup"><span data-stu-id="7314c-158">To make each quad face the camera, we used a geometry shader to transform each star position to a 2D rectangle on the screen that will contain our star texture.</span></span>

![Karo statt Quads.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="7314c-160">Karo statt Quads.</span><span class="sxs-lookup"><span data-stu-id="7314c-160">Diamonds instead of quads.</span></span>


<span data-ttu-id="7314c-161">Da wir die Überzeichnung (Anzahl der Male, die eine Pixel verarbeitet werden) einschränken möchten so weit wie möglich, wir gedreht unsere Quads, damit sie weniger überschneiden müssten.</span><span class="sxs-lookup"><span data-stu-id="7314c-161">Because we wanted to limit the overdraw (number of times a pixel will be processed) as much as possible, we rotated our quads so that they would have less overlap.</span></span>

### <a name="adding-clouds"></a><span data-ttu-id="7314c-162">Hinzufügen von clouds</span><span class="sxs-lookup"><span data-stu-id="7314c-162">Adding clouds</span></span>

<span data-ttu-id="7314c-163">Es gibt viele Möglichkeiten, um ein volumetrische Gefühl mit Partikel zu erhalten – von Ray marching innerhalb eines Volumes zum Zeichnen der so viele Partikel wie möglich in einer Cloud zu simulieren.</span><span class="sxs-lookup"><span data-stu-id="7314c-163">There are many ways to get a volumetric feeling with particles—from ray marching inside of a volume to drawing as many particles as possible to simulate a cloud.</span></span> <span data-ttu-id="7314c-164">Real-Time-Ray marching war im Begriff, zu teuer und schwierig zu erstellen, werden, daher wechselten wir zuerst eine stünden-System über eine Methode zur Rendering-Gesamtstrukturen in Spiele erstellen – mit einer Vielzahl von 2D-Bilder von Strukturen, die vor der Kamera.</span><span class="sxs-lookup"><span data-stu-id="7314c-164">Real-time ray marching was going to be too expensive and hard to author, so we first tried building an imposter system using a method for rendering forests in games—with a lot of 2D images of trees facing the camera.</span></span> <span data-ttu-id="7314c-165">Wenn wir dazu ein Spiel verwenden möchten, können wir Texturen von Strukturen, die über eine Kamera, die auf, speichern Sie alle diese Images und zur Laufzeit für jede Karte Billboard rotiert gerendert haben, wählen Sie das Bild, das die ansichtsrichtung entspricht.</span><span class="sxs-lookup"><span data-stu-id="7314c-165">When we do this in a game, we can have textures of trees rendered from a camera that rotates around, save all those images, and at runtime for each billboard card, select the image that matches the view direction.</span></span> <span data-ttu-id="7314c-166">Dies funktioniert auch nicht, wenn die Images Hologramme sind.</span><span class="sxs-lookup"><span data-stu-id="7314c-166">This doesn't work as well when the images are holograms.</span></span> <span data-ttu-id="7314c-167">Der Unterschied zwischen dem linken und der richtigen Auge erleichtern, damit wir eine viel höhere Auflösung benötigen, da ansonsten nur myblobstorage_storage flach, mit einem Alias versehen ist, oder sich wiederholende.</span><span class="sxs-lookup"><span data-stu-id="7314c-167">The difference between the left eye and the right eye make it so that we need a much higher resolution, or else it just looks flat, aliased, or repetitive.</span></span>

<span data-ttu-id="7314c-168">Klicken Sie auf unserer zweiten Versuch haben wir versucht, dass so viele Partikel wie möglich.</span><span class="sxs-lookup"><span data-stu-id="7314c-168">On our second attempt, we tried having as many particles as possible.</span></span> <span data-ttu-id="7314c-169">Die beste visuelle Elemente wurden erreicht, wenn wir lichtdurchlässigen Partikel Drew, und sie vor dem Hinzufügen der Szene verwischt.</span><span class="sxs-lookup"><span data-stu-id="7314c-169">The best visuals were achieved when we additively drew particles and blurred them before adding them to the scene.</span></span> <span data-ttu-id="7314c-170">Probleme mit diesem Ansatz wurden für wie viele Partikel, die wir auf ein einziges Mal zeichnen können und wie viel Bildschirmbereich sie gleichzeitig 60fps behandelt.</span><span class="sxs-lookup"><span data-stu-id="7314c-170">The typical problems with that approach were related to how many particles we could draw at a single time and how much screen area they covered while still maintaining 60fps.</span></span> <span data-ttu-id="7314c-171">Das resultierende Image rufen Sie diese Cloud sei Weichzeichner wurde in der Regel ein sehr ressourcenintensiver Vorgang.</span><span class="sxs-lookup"><span data-stu-id="7314c-171">Blurring the resulting image to get this cloud feeling was usually a very costly operation.</span></span>

![Ohne die Textur ist dies an, wie die Clouds mit 2 % Deckkraft aussehen würde.](images/clouds-without-texture-300px.jpg)

<span data-ttu-id="7314c-173">Ohne die Textur ist dies an, wie die Clouds mit 2 % Deckkraft aussehen würde.</span><span class="sxs-lookup"><span data-stu-id="7314c-173">Without texture, this is what the clouds would look like with 2% opacity.</span></span>



<span data-ttu-id="7314c-174">Additive wird und dass viele von ihnen also mehrere Quads übereinander, müssten wir wiederholt Schattierung dasselbe Pixel.</span><span class="sxs-lookup"><span data-stu-id="7314c-174">Being additive and having a lot of them means that we would have several quads on top of each other, repeatedly shading the same pixel.</span></span> <span data-ttu-id="7314c-175">In der Mitte des Galaxy dasselbe Pixel hält Hunderte von Quads bauen aufeinander auf, und dies hat enormen Kosten verbunden, wenn Vollbildmodus ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="7314c-175">In the center of the galaxy, the same pixel has hundreds of quads on top of each other and this had a huge cost when being done full screen.</span></span>

<span data-ttu-id="7314c-176">Vollbildmodus Clouds durchführen, und versuchen, diese blur hätten keine gute Idee, daher entschieden wir, die Hardware, die die Arbeit für uns leisten können.</span><span class="sxs-lookup"><span data-stu-id="7314c-176">Doing full screen clouds and trying to blur them would have been a bad idea, so instead we decided to let the hardware do the work for us.</span></span>

### <a name="a-bit-of-context-first"></a><span data-ttu-id="7314c-177">Ein bit des Kontexts zunächst</span><span class="sxs-lookup"><span data-stu-id="7314c-177">A bit of context first</span></span>

<span data-ttu-id="7314c-178">Bei Verwendung von Texturen in einem Spiel entspricht der Texturgröße selten Bereich in verwendet werden soll, jedoch können wir andere Art von texturfilterung zum Abrufen der Grafikkarte auf, um die Farbe zu interpolieren in Pixel der Textur erstellt werden sollten ([Texturfilterung<C3/>).</span><span class="sxs-lookup"><span data-stu-id="7314c-178">When using textures in a game the texture size will rarely match the area we want to use it in, but we can use different kind of texture filtering to get the graphic card to interpolate the color we want from the pixels of the texture ([Texture Filtering](https://msdn.microsoft.com/library/dn642451.aspx)).</span></span> <span data-ttu-id="7314c-179">Die Filterung, die uns interessiert ist [bilineare Filterung](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) die wird den Wert jedes Pixels mit dem 4 nächsten Nachbarn berechnet.</span><span class="sxs-lookup"><span data-stu-id="7314c-179">The filtering that interests us is [bilinear filtering](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) which will compute the value of any pixel using the 4 nearest neighbors.</span></span>

![Ursprüngliche Filtervorgang](images/texture-1.png)

![Führen Sie nach dem Filtern](images/texture-2.png)

<span data-ttu-id="7314c-182">Diese Eigenschaft verwenden, sehen wir, dass jeder Versuch, eine Textur in einem Bereich doppelt so groß, zeichnen sie das Ergebnis verwischt.</span><span class="sxs-lookup"><span data-stu-id="7314c-182">Using this property, we see that each time we try to draw a texture into an area twice as big, it blurs the result.</span></span>

<span data-ttu-id="7314c-183">Statt in den Vollbildmodus Rendern und verlieren diese wertvollen in Millisekunden, die wir auf einen anderen Ausgaben werden konnte, Rendern es auf eine kleine Version des Bildschirms aus.</span><span class="sxs-lookup"><span data-stu-id="7314c-183">Instead of rendering to a full screen and losing those precious milliseconds we could be spending on something else, we render to a tiny version of the screen.</span></span> <span data-ttu-id="7314c-184">Klicken Sie dann erhalten Sie durch Kopieren dieser Textur und Dehnen es mit einem Faktor von 2 mehrmals, Vollbildmodus und den Inhalt im Prozess Weichzeichner.</span><span class="sxs-lookup"><span data-stu-id="7314c-184">Then, by copying this texture and stretching it by a factor of 2 several times, we get back to full screen while blurring the content in the process.</span></span>

![X3 an voller Auflösung vergrößern.](images/galaxy-resolutions-300px.png)

<span data-ttu-id="7314c-186">X3 an voller Auflösung vergrößern.</span><span class="sxs-lookup"><span data-stu-id="7314c-186">x3 upscale back to full resolution.</span></span>



<span data-ttu-id="7314c-187">Dies konnten wir das Cloud-Part mit nur ein Bruchteil der Kosten der ursprünglichen abrufen.</span><span class="sxs-lookup"><span data-stu-id="7314c-187">This allowed us to get the cloud part with only a fraction of the original cost.</span></span> <span data-ttu-id="7314c-188">Anstatt zum Hinzufügen von Clouds für die vollständige Lösung, wir nur Paint 1/64. der Pixel und nur stretch die Textur an voller Auflösung.</span><span class="sxs-lookup"><span data-stu-id="7314c-188">Instead of adding clouds on the full resolution, we only paint 1/64th of the pixels and just stretch the texture back to full resolution.</span></span>

![Links, mit einem hochpreisiger von 1/8. um voller Auflösung; und mit 3, vergrößern Potenz von 2 verwenden.](images/stars-upscaled-300px.jpg)

<span data-ttu-id="7314c-190">Links, mit einem hochpreisiger von 1/8. um voller Auflösung; und mit 3, vergrößern Potenz von 2 verwenden.</span><span class="sxs-lookup"><span data-stu-id="7314c-190">Left, with an upscale from 1/8th to full resolution; and right, with 3 upscale using power of 2.</span></span>


<span data-ttu-id="7314c-191">Beachten Sie, versuchen, wechseln von 1/64. die Größe auf die vollständige Größe in einer Aktion würde ganz anders aussehen, während der Grafikkarte weiterhin 4 Pixel in diesem Setup verwenden würde, um einen größeren Bereich schattieren aus, und starten Sie die Elemente angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7314c-191">Note that trying to go from 1/64th of the size to the full size in one go would look completely different, as the graphic card would still use 4 pixels in our setup to shade a bigger area and artifacts start to appear.</span></span>

<span data-ttu-id="7314c-192">Klicken Sie dann, wenn wir voller Auflösung Sterne mit kleineren Karten hinzufügen, erhalten wir die vollständige Galaxie:</span><span class="sxs-lookup"><span data-stu-id="7314c-192">Then, if we add full resolution stars with smaller cards, we get the full galaxy:</span></span>

![In der Nähe Endergebnis Galaxy-Rendering mit voller Auflösung Sterne](images/full-galaxy-500px.png)

<span data-ttu-id="7314c-194">Nachdem wir auf dem richtigen Weg mit der Form waren, haben wir eine Ebene von Clouds, die temporäre Punkte, mit denen, die wir in Photoshop gezeichnet, die und einige zusätzliche Farbe, ausgelagert hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="7314c-194">Once we were on the right track with the shape, we added a layer of clouds, swapped out the temporary dots with ones we painted in Photoshop, and added some additional color.</span></span> <span data-ttu-id="7314c-195">Das Ergebnis war ein Galaxy arbeiten unsere moderne Entwicklungsteams beide spürbar gut gelungen ist und es unser Ziel mit Tiefe, Volumes und während der Übertragung erfüllt – ganz ohne hohe Anforderungen an die CPU.</span><span class="sxs-lookup"><span data-stu-id="7314c-195">The result was a Milky Way Galaxy our art and engineering teams both felt good about and it met our goals of having depth, volume, and motion—all without taxing the CPU.</span></span>

![Unsere letzte arbeiten Galaxy in 3D.](images/final-galaxy-500px.jpg)

<span data-ttu-id="7314c-197">Unsere letzte arbeiten Galaxy in 3D.</span><span class="sxs-lookup"><span data-stu-id="7314c-197">Our final Milky Way Galaxy in 3D.</span></span>


### <a name="more-to-explore"></a><span data-ttu-id="7314c-198">Auf die Zukunft</span><span class="sxs-lookup"><span data-stu-id="7314c-198">More to explore</span></span>

<span data-ttu-id="7314c-199">Wir haben den Code für das Galaxy-Explorer-app als Open Source und auf zur Verfügung gestellt [GitHub](https://github.com/Microsoft/GalaxyExplorer) für Entwickler erstellen.</span><span class="sxs-lookup"><span data-stu-id="7314c-199">We've open-sourced the code for the Galaxy Explorer app and made it available on [GitHub](https://github.com/Microsoft/GalaxyExplorer) for developers to build on.</span></span>

<span data-ttu-id="7314c-200">Weitere Informationen zu den Entwicklungsprozess für Galaxy Explorer herausfinden möchten?</span><span class="sxs-lookup"><span data-stu-id="7314c-200">Interested in finding out more about the development process for Galaxy Explorer?</span></span> <span data-ttu-id="7314c-201">Sehen Sie sich alle unsere letzten Projekt Updates auf die [Microsoft HoloLens YouTube-Kanal](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span><span class="sxs-lookup"><span data-stu-id="7314c-201">Check out all our past project updates on the [Microsoft HoloLens YouTube channel](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="7314c-202">Über die Autoren</span><span class="sxs-lookup"><span data-stu-id="7314c-202">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><span data-ttu-id="7314c-203"><b>Karim Luccin</b> ist Software Engineer und mit Effekten Visuals Enthusiast.</span><span class="sxs-lookup"><span data-stu-id="7314c-203"><b>Karim Luccin</b> is a Software Engineer and fancy visuals enthusiast.</span></span> <span data-ttu-id="7314c-204">Er war der Techniker Grafiken für Galaxy-Explorer.</span><span class="sxs-lookup"><span data-stu-id="7314c-204">He was the Graphics Engineer for Galaxy Explorer.</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><span data-ttu-id="7314c-205"><b>Andy Zibits</b> ist eine Art Lead und Speicherplatz Enthusiast verwaltet das Team 3D Modellierung für Galaxy-Explorer, und für noch mehr Partikel auseinander setzen.</span><span class="sxs-lookup"><span data-stu-id="7314c-205"><b>Andy Zibits</b> is an Art Lead and space enthusiast who managed the 3D modeling team for Galaxy Explorer and fought for even more particles.</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="7314c-206">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7314c-206">See also</span></span>
* [<span data-ttu-id="7314c-207">Galaxy-Explorer auf GitHub</span><span class="sxs-lookup"><span data-stu-id="7314c-207">Galaxy Explorer on GitHub</span></span>](https://github.com/Microsoft/GalaxyExplorer)
* [<span data-ttu-id="7314c-208">Galaxy Explorer projektaktualisierungen auf YouTube</span><span class="sxs-lookup"><span data-stu-id="7314c-208">Galaxy Explorer project updates on YouTube</span></span>](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
