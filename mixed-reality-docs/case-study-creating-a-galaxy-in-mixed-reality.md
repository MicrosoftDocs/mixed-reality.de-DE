---
title: 'Fallstudie: Erstellen einer Galaxie in gemischter Realität'
description: Bevor Microsoft hololens ausgeliefert wurde, fragten wir unsere Entwickler Community, welche Art von APP Ihnen einen erfahrenen internen TeamBuild für das neue Gerät bereitstellen möchte. Mehr als 5000 Ideen wurden freigegeben, und nach einer 24-stündigen Twitter-Umfrage war der Gewinner eine Idee namens "Galaxy Explorer".
author: KarimLUCCIN
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy Explorer, hololens, Windows Mixed Reality, teilen Sie Ihre Idee, Fallstudie
ms.openlocfilehash: a478eaa35144a8ee0fbeaeb43cec4b9f901890ab
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63523766"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a><span data-ttu-id="7dbb0-105">Fallstudie: Erstellen einer Galaxie in gemischter Realität</span><span class="sxs-lookup"><span data-stu-id="7dbb0-105">Case study - Creating a galaxy in mixed reality</span></span>

<span data-ttu-id="7dbb0-106">Bevor Microsoft hololens ausgeliefert wurde, fragten wir unsere Entwickler Community, welche Art von APP Ihnen einen erfahrenen internen TeamBuild für das neue Gerät bereitstellen möchte.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-106">Before Microsoft HoloLens shipped, we asked our developer community what kind of app they'd like to see an experienced internal team build for the new device.</span></span> <span data-ttu-id="7dbb0-107">Mehr als 5000 Ideen wurden freigegeben, und nach einer 24-stündigen Twitter-Umfrage war der Gewinner eine Idee namens " [Galaxy Explorer](galaxy-explorer.md)".</span><span class="sxs-lookup"><span data-stu-id="7dbb0-107">More than 5000 ideas were shared, and after a 24-hour Twitter poll, the winner was an idea called [Galaxy Explorer](galaxy-explorer.md).</span></span>

<span data-ttu-id="7dbb0-108">Andy zibits, der Kunst Leiter im Projekt und Karim Luccin, der Grafik Techniker des Teams, sprechen über den kollaborativen Aufwand zwischen Kunst und Engineering, der zur Erstellung einer exakten, interaktiven Darstellung der MILCHWEG-Galaxy in Galaxy Explorer geführt hat.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-108">Andy Zibits, the art lead on the project, and Karim Luccin, the team's graphics engineer, talk about the collaborative effort between art and engineering that led to the creation of an accurate, interactive representation of the Milky Way galaxy in Galaxy Explorer.</span></span>

## <a name="the-tech"></a><span data-ttu-id="7dbb0-109">Die Technologie</span><span class="sxs-lookup"><span data-stu-id="7dbb0-109">The Tech</span></span>

<span data-ttu-id="7dbb0-110">[Unser Team](galaxy-explorer.md#meet-the-team) besteht aus zwei Designern, drei Entwicklern, vier Künstlern, einem Producer und einem Tester – es gab sechs Wochen, eine voll funktionsfähige APP zu erstellen, die es den Benutzern ermöglicht, sich mit der Menschen Nähe und der Schönheit unserer Milchwege-Galaxy vertraut zu machen.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-110">[Our team](galaxy-explorer.md#meet-the-team) - made up of two designers, three developers, four artists, a producer, and one tester — had six weeks to build a fully functional app which would allow people to learn about and explore the vastness and beauty of our Milky Way Galaxy.</span></span>

<span data-ttu-id="7dbb0-111">Wir wollten die Fähigkeit von hololens in vollem Umfang nutzen, 3D-Objekte direkt in ihren Lebensbereich zu Rendering. Daher wollten wir eine realistische, aussehende Galaxie erstellen, in der die Benutzer in der Lage sind, die Schließung zu vergrößern und einzelne Sterne anzuzeigen .</span><span class="sxs-lookup"><span data-stu-id="7dbb0-111">We wanted to take full advantage of the ability of HoloLens to render 3D objects directly in your living space, so we decided we wanted to create a realistic looking galaxy where people would be able to zoom in close and see individual stars, each on their own trajectories.</span></span>

<span data-ttu-id="7dbb0-112">In der ersten Woche der Entwicklung haben wir einige Ziele für unsere Darstellung der Milchwege-Galaxy-Methode erreicht: Es brauchte Tiefe, Bewegung und Gefühl von "Volumetric – Full of Stars", die beim Erstellen der Form der Galaxie helfen würden.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-112">In the first week of development, we came up with a few goals for our representation of the Milky Way Galaxy: It needed to have depth, movement, and feel volumetric—full of stars that would help create the shape of the galaxy.</span></span>

<span data-ttu-id="7dbb0-113">Das Problem bei der Erstellung einer animierten Galaxie mit Milliarden von Sternen war, dass die reine Anzahl von einzelnen Elementen, die aktualisiert werden müssen, pro Frame zu groß wäre, damit hololens mithilfe der CPU animiert werden.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-113">The problem with creating an animated galaxy that had billions of stars was that the sheer number of single elements that need updating would be too big per frame for HoloLens to animate using the CPU.</span></span> <span data-ttu-id="7dbb0-114">Unsere Lösung umfasste eine komplexe Mischung aus Kunst und Wissenschaft.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-114">Our solution involved a complex mix of art and science.</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="7dbb0-115">Im Hintergrund</span><span class="sxs-lookup"><span data-stu-id="7dbb0-115">Behind the scenes</span></span>

<span data-ttu-id="7dbb0-116">Der erste Schritt besteht darin, herauszufinden, wie viele Partikel gleichzeitig dargestellt werden könnten.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-116">To allow people to explore individual stars, our first step was to figure out how many particles we could render at once.</span></span>

### <a name="rendering-particles"></a><span data-ttu-id="7dbb0-117">Rendern von Partikeln</span><span class="sxs-lookup"><span data-stu-id="7dbb0-117">Rendering particles</span></span>

<span data-ttu-id="7dbb0-118">Aktuelle CPUs eignen sich hervorragend für die Verarbeitung von seriellen Aufgaben und bis zu einem Paar paralleler Aufgaben auf einmal (abhängig von der Anzahl der Kerne). GPUs sind jedoch weitaus effektiver, wenn Tausende von Vorgängen parallel verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-118">Current CPUs are great for processing serial tasks and up to a few parallel tasks at once (depending on how many cores they have), but GPUs are much more effective at processing thousands of operations in parallel.</span></span> <span data-ttu-id="7dbb0-119">Da Sie jedoch in der Regel nicht denselben Arbeitsspeicher wie die CPU gemeinsam nutzen, kann der Datenaustausch zwischen CPU-< > GPU schnell zu einem Engpass werden.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-119">However, because they don’t usually share the same memory as the CPU, exchanging data between CPU<>GPU can quickly become a bottleneck.</span></span> <span data-ttu-id="7dbb0-120">Unsere Lösung bestand darin, eine Galaxie auf der GPU zu erstellen, die vollständig auf der GPU gelebt werden musste.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-120">Our solution was to make a galaxy on the GPU, and it had to live completely on the GPU.</span></span>

<span data-ttu-id="7dbb0-121">Wir haben Belastungstests mit Tausenden von Punkt Partikeln in verschiedenen Mustern gestartet.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-121">We started stress tests with thousands of point particles in various patterns.</span></span> <span data-ttu-id="7dbb0-122">Auf diese Art konnten wir die Galaxie auf hololens bringen, um zu sehen, was funktionierte und was nicht.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-122">This allowed us to get the galaxy on HoloLens to see what worked and what didn’t.</span></span>

### <a name="creating-the-position-of-the-stars"></a><span data-ttu-id="7dbb0-123">Erstellen der Position der Sterne</span><span class="sxs-lookup"><span data-stu-id="7dbb0-123">Creating the position of the stars</span></span>

<span data-ttu-id="7dbb0-124">Eines unserer Teammitglieder hat bereits den Code geschrieben C# , der Sterne an der ursprünglichen Position generieren würde.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-124">One of our team members had already written the C# code that would generate stars at their initial position.</span></span> <span data-ttu-id="7dbb0-125">Die Sterne befinden sich auf einer Ellipse, und ihre Position kann von ("**Cursor Offset**", " **ellipsesize**", " **Erhöhung**") beschrieben werden, wobei " **Cursor Offset** " der Winkel des Sterns entlang der Ellipse ist, " **ellipsesize** " die Dimension der Ellipse. entlang von X und Z und Erhöhung der ordnungsgemäßen Erweiterung des Stern in der Galaxy.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-125">The stars are on an ellipse and their position can be described by (**curveOffset**, **ellipseSize**, **elevation**) where **curveOffset** is the angle of the star along the ellipse, **ellipseSize** is the dimension of the ellipse along X and Z, and elevation the proper elevation of the star within the galaxy.</span></span> <span data-ttu-id="7dbb0-126">Daher können wir einen Puffer ([computebuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) erstellen, der mit jedem Star-Attribut initialisiert und an die GPU gesendet wird, wo er für den Rest der Arbeit leben würde.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-126">Thus, we can create a buffer ([Unity’s ComputeBuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) that would be initialized with each star attribute and send it on the GPU where it would live for the rest of the experience.</span></span> <span data-ttu-id="7dbb0-127">Zum Zeichnen dieses Puffers verwenden wir das [drawprozeduren von Unity](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) , das das Ausführen eines Shaders (Code auf einer GPU) für eine beliebige Gruppe von Punkten ermöglicht, ohne dass ein tatsächliches Mesh vorhanden ist, das das Galaxy darstellt:</span><span class="sxs-lookup"><span data-stu-id="7dbb0-127">To draw this buffer, we use [Unity’s DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) which allows running a shader (code on a GPU) on an arbitrary set of points without having an actual mesh that represents the galaxy:</span></span>

<span data-ttu-id="7dbb0-128">**CPU**</span><span class="sxs-lookup"><span data-stu-id="7dbb0-128">**CPU:**</span></span>




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

<span data-ttu-id="7dbb0-129">**AUSSCHALTEN**</span><span class="sxs-lookup"><span data-stu-id="7dbb0-129">**GPU:**</span></span>




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

<span data-ttu-id="7dbb0-130">Wir haben mit unformatierten zirkulären Mustern mit Tausenden von Partikeln begonnen.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-130">We started with raw circular patterns with thousands of particles.</span></span> <span data-ttu-id="7dbb0-131">Wir haben uns die erforderliche Prüfung gegeben, dass wir viele Partikel verwalten und mit leistungsfähiger Geschwindigkeit ausführen können. Wir haben uns jedoch nicht mit der Gesamtform der Galaxie zufrieden gestellt.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-131">This gave us the proof we needed that we could manage many particles AND run it at performant speeds, but we weren’t satisfied with the overall shape of the galaxy.</span></span> <span data-ttu-id="7dbb0-132">Um die Form zu verbessern, haben wir versucht, verschiedene Muster und Partikelsysteme mit Drehung zu entwickeln.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-132">To improve the shape, we attempted various patterns and particle systems with rotation.</span></span> <span data-ttu-id="7dbb0-133">Diese waren anfänglich vielversprechend, weil die Anzahl der Partikel und die Leistung konsistent waren, aber die Form nahe dem Mittelpunkt aufbrach und die Sterne ausgingen, was nicht realistisch war.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-133">These were initially promising because the number of particles and performance stayed consistent, but the shape broke down near the center and the stars were emitting outwardly which wasn't realistic.</span></span> <span data-ttu-id="7dbb0-134">Wir brauchten eine Ausgabe, mit der wir die Zeit verändern konnten, und die Partikel werden realistisch verschoben, und die Schleife wird immer näher an der Mitte der Galaxie durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-134">We needed an emission that would allow us to manipulate time and have the particles move realistically, looping ever closer to the center of the galaxy.</span></span>

![Wir haben versucht, verschiedene Muster und Partikelsysteme zu drehen, die wie folgt gedreht wurden.](images/galaxy-patterns-500px.png)

<span data-ttu-id="7dbb0-136">Wir haben versucht, verschiedene Muster und Partikelsysteme zu drehen, die wie folgt gedreht wurden.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-136">We attempted various patterns and particle systems that rotated, like these.</span></span>

<span data-ttu-id="7dbb0-137">Unser Team hat einige Untersuchungen zur Funktionsweise von Galaxien durchgeführt, und wir haben ein benutzerdefiniertes Partikelsystem speziell für die Galaxie erstellt, sodass wir die Partikel auf Ellipsen basierend auf "[Dichtewellen Theorie](https://en.wikipedia.org/wiki/Density_wave_theory)" verschieben konnten. Dies weist darauf hin, dass es sich bei den Armen einer Galaxy um Bereiche von höhere Dichte, aber in konstantem Flux, wie z. b. eine Verkehrsampel.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-137">Our team did some research about the way galaxies function and we made a custom particle system specifically for the galaxy so that we could move the particles on ellipses based on "[density wave theory](https://en.wikipedia.org/wiki/Density_wave_theory)," which theorizes that the arms of a galaxy are areas of higher density but in constant flux, like a traffic jam.</span></span> <span data-ttu-id="7dbb0-138">Es erscheint stabil und solide, aber die Sterne bewegen sich tatsächlich in den und aus den Armen, wenn Sie sich auf die jeweiligen Ellipsen bewegen.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-138">It appears stable and solid, but the stars are actually moving in and out of the arms as they move along their respective ellipses.</span></span> <span data-ttu-id="7dbb0-139">In unserem System sind die Partikel nie auf der CPU vorhanden – wir generieren die Karten und orientieren Sie alle auf der GPU, sodass das gesamte System einfach den anfänglichen Zustand und die Zeit hat.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-139">In our system, the particles never exist on the CPU—we generate the cards and orient them all on the GPU, so the whole system is simply initial state + time.</span></span> <span data-ttu-id="7dbb0-140">Dies ist wie folgt:</span><span class="sxs-lookup"><span data-stu-id="7dbb0-140">It progressed like this:</span></span>

![Fortschritt des partikelsystems mit GPU-Rendering](images/spiral-galaxy-arms-500px.jpg)

<span data-ttu-id="7dbb0-142">Fortschritt des partikelsystems mit GPU-Rendering</span><span class="sxs-lookup"><span data-stu-id="7dbb0-142">Progression of particle system with GPU rendering</span></span>


<span data-ttu-id="7dbb0-143">Sobald genügend Auslassungs Punkte hinzugefügt wurden und für die Rotation festgelegt sind, begannen die Galaxien mit der Bildung von "Arms", bei der die Bewegung von Sternen konvergiert.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-143">Once enough ellipses are added and are set to rotate, the galaxies began to form “arms” where the movement of stars converge.</span></span> <span data-ttu-id="7dbb0-144">Der Abstand der Sterne entlang der einzelnen Ellipsen Pfade hat eine gewisse Zufälligkeit eingeräumt, und jedem Stern wurde ein wenig Positions Zufälligkeit hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-144">The spacing of the stars along each elliptical path was given some randomness, and each star got a bit of positional randomness added.</span></span> <span data-ttu-id="7dbb0-145">Dadurch wurde eine viel natürlichere Verteilung der Stern Bewegung und der Arm-Form erstellt.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-145">This created a much more natural looking distribution of star movement and arm shape.</span></span> <span data-ttu-id="7dbb0-146">Schließlich haben wir die Möglichkeit hinzugefügt, die Farbe basierend auf der Entfernung vom Mittelpunkt zu steuern.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-146">Finally, we added the ability to drive color based on distance from center.</span></span>

### <a name="creating-the-motion-of-the-stars"></a><span data-ttu-id="7dbb0-147">Erstellen der Bewegung der Sterne</span><span class="sxs-lookup"><span data-stu-id="7dbb0-147">Creating the motion of the stars</span></span>

<span data-ttu-id="7dbb0-148">Um die allgemeine Stern Bewegung zu animieren, mussten wir einen konstanten Winkel für jeden Frame hinzufügen und Sterne an einer Konstanten radialen Geschwindigkeit entlang der Ellipsen bewegen.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-148">To animate the general star motion, we needed to add a constant angle for each frame and to get stars moving along their ellipses at a constant radial velocity.</span></span> <span data-ttu-id="7dbb0-149">Dies ist der Hauptgrund für die Verwendung von " **Cursor Offset**".</span><span class="sxs-lookup"><span data-stu-id="7dbb0-149">This is the primary reason for using **curveOffset**.</span></span> <span data-ttu-id="7dbb0-150">Dies ist technisch nicht korrekt, da Sterne auf den langen Seiten der Ellipsen schneller bewegt werden, aber die allgemeine Bewegung war gut.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-150">This isn’t technically correct as stars will move faster along the long sides of the ellipses, but the general motion felt good.</span></span>

![Sterne bewegen sich auf dem langen Bogen schneller, langsamer an den Rändern.](images/ellipse-movement.jpg)

<span data-ttu-id="7dbb0-152">Sterne bewegen sich auf dem langen Bogen schneller, langsamer an den Rändern.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-152">Stars move faster on the long arc, slower on the edges.</span></span>


<span data-ttu-id="7dbb0-153">Dadurch wird jeder Stern vollständig durch beschrieben ("**Cursor Offset**", " **ellipssize**", " **Erhöhung**", " **Alter**"), wobei " **Age** " eine Ansammlung der Gesamtzeit ist, die seit dem Laden der Szene vergangen ist.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-153">With that, each star is fully described by (**curveOffset**, **ellipseSize**, **elevation**, **Age**) where **Age** is an accumulation of the total time that has passed since the scene was loaded.</span></span>




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

<span data-ttu-id="7dbb0-154">Dies ermöglichte uns, Zehntausende von Sternen einmal am Anfang der Anwendung zu generieren. anschließend animierten wir eine Reihe von Sternen entlang der etablierten Kurven.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-154">This allowed us to generate tens of thousands of stars once at the start of the application, then we animated a singled set of stars along the established curves.</span></span> <span data-ttu-id="7dbb0-155">Da alles auf der GPU basiert, kann das System alle Sterne parallel zu den CPU-Kosten animieren.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-155">Since everything is on the GPU, the system can animate all the stars in parallel at no cost to the CPU.</span></span>

![Hier sehen Sie, wie es aussieht, wenn Sie weiße Quads zeichnen.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="7dbb0-157">Hier sehen Sie, wie es aussieht, wenn Sie weiße Quads zeichnen.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-157">Here’s what it looks like when drawing white quads.</span></span>



<span data-ttu-id="7dbb0-158">Um jedes Vierfache der Kamera zuzuordnen, haben wir einen Geometry-Shader verwendet, um jede Stern Position in ein 2D-Rechteck auf dem Bildschirm umzuwandeln, das die Stern Textur enthält.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-158">To make each quad face the camera, we used a geometry shader to transform each star position to a 2D rectangle on the screen that will contain our star texture.</span></span>

![Diamanten anstelle von Quads.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="7dbb0-160">Diamanten anstelle von Quads.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-160">Diamonds instead of quads.</span></span>


<span data-ttu-id="7dbb0-161">Da wir die Überschreibung (die Häufigkeit, mit der ein Pixel verarbeitet wird) so weit wie möglich einschränken wollten, haben wir unsere Quads so gedreht, dass Sie weniger überlappend haben.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-161">Because we wanted to limit the overdraw (number of times a pixel will be processed) as much as possible, we rotated our quads so that they would have less overlap.</span></span>

### <a name="adding-clouds"></a><span data-ttu-id="7dbb0-162">Hinzufügen von Clouds</span><span class="sxs-lookup"><span data-stu-id="7dbb0-162">Adding clouds</span></span>

<span data-ttu-id="7dbb0-163">Es gibt viele Möglichkeiten, ein volummetric-Gefühl mit Partikeln zu erzielen – von dem Ray, das sich innerhalb eines Volumes befindet, um so viele Partikel wie möglich zu zeichnen, um eine Cloud zu simulieren.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-163">There are many ways to get a volumetric feeling with particles—from ray marching inside of a volume to drawing as many particles as possible to simulate a cloud.</span></span> <span data-ttu-id="7dbb0-164">Die Echtzeitdarstellung von Ray war zu teuer und schwer zu erstellen, daher haben wir zuerst versucht, ein unveränderliches System mit einer Methode zum Rendern von Gesamtstrukturen in spielen zu erstellen – mit einer großen Zahl von 2D-Bildern von Bäumen, die der Kamera ausgesetzt waren.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-164">Real-time ray marching was going to be too expensive and hard to author, so we first tried building an imposter system using a method for rendering forests in games—with a lot of 2D images of trees facing the camera.</span></span> <span data-ttu-id="7dbb0-165">Wenn wir dies in einem Spiel durchführen, können Sie Strukturen von Bäumen rendern, die von einer Kamera gerendert werden, die alle Bilder speichert, und zur Laufzeit für jede Billboard-Karte das Bild auswählen, das der Ansichts Richtung entspricht.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-165">When we do this in a game, we can have textures of trees rendered from a camera that rotates around, save all those images, and at runtime for each billboard card, select the image that matches the view direction.</span></span> <span data-ttu-id="7dbb0-166">Dies funktioniert auch nicht, wenn es sich um Hologramme handelt.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-166">This doesn't work as well when the images are holograms.</span></span> <span data-ttu-id="7dbb0-167">Der Unterschied zwischen dem linken und dem rechten Auge ist, dass wir eine viel höhere Auflösung benötigen, oder es wird nur ein flach, ein Alias oder ein wiederholtes aussehen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-167">The difference between the left eye and the right eye make it so that we need a much higher resolution, or else it just looks flat, aliased, or repetitive.</span></span>

<span data-ttu-id="7dbb0-168">Bei unserem zweiten Versuch haben wir versucht, so viele Partikel wie möglich zu haben.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-168">On our second attempt, we tried having as many particles as possible.</span></span> <span data-ttu-id="7dbb0-169">Die besten visuellen Elemente wurden erzielt, als wir die Partikel Additiv gezeichnet haben, bevor Sie der Szene hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-169">The best visuals were achieved when we additively drew particles and blurred them before adding them to the scene.</span></span> <span data-ttu-id="7dbb0-170">Die typischen Probleme bei diesem Ansatz standen in Bezug darauf, wie viele Partikel zu einem einzigen Zeitpunkt gezeichnet werden konnten und wie viel Bildschirmfläche Sie abgedeckt haben, während 60 fps beibehalten werden.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-170">The typical problems with that approach were related to how many particles we could draw at a single time and how much screen area they covered while still maintaining 60fps.</span></span> <span data-ttu-id="7dbb0-171">Das resultierende Bild zu verschleiern, um dieses cloudgefühl zu erhalten, war normalerweise ein sehr kostspieliger Vorgang.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-171">Blurring the resulting image to get this cloud feeling was usually a very costly operation.</span></span>

![Ohne Textur würden die Clouds mit einer Deckkraft von 2% aussehen.](images/clouds-without-texture-300px.jpg)

<span data-ttu-id="7dbb0-173">Ohne Textur würden die Clouds mit einer Deckkraft von 2% aussehen.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-173">Without texture, this is what the clouds would look like with 2% opacity.</span></span>



<span data-ttu-id="7dbb0-174">Wenn Sie Additiv sind und viele davon haben, sind mehrere aufeinander folgende aufeinander folgende aufeinander folgende.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-174">Being additive and having a lot of them means that we would have several quads on top of each other, repeatedly shading the same pixel.</span></span> <span data-ttu-id="7dbb0-175">In der Mitte der Galaxy hat das gleiche Pixel Hunderte von aufeinander folgenden, und dies hat bei vollständigem Bildschirm enorme Kosten.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-175">In the center of the galaxy, the same pixel has hundreds of quads on top of each other and this had a huge cost when being done full screen.</span></span>

<span data-ttu-id="7dbb0-176">Das Ausführen von voll Bild Clouds und das versuchen, Sie zu verwischen, wäre eine gute Idee. Wir haben uns also entschieden, die Hardware für uns zu Unternehmen.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-176">Doing full screen clouds and trying to blur them would have been a bad idea, so instead we decided to let the hardware do the work for us.</span></span>

### <a name="a-bit-of-context-first"></a><span data-ttu-id="7dbb0-177">Ein bisschen Kontext zuerst</span><span class="sxs-lookup"><span data-stu-id="7dbb0-177">A bit of context first</span></span>

<span data-ttu-id="7dbb0-178">Bei der Verwendung von Texturen in einem Spiel entspricht die Textur Größe selten dem Bereich, in dem wir Sie verwenden möchten, aber wir können unterschiedliche Arten von Textur Filtern verwenden, um die Grafikkarte zum Interpolieren der gewünschten Farbe aus den Pixeln der Textur ([Textur Filterung](https://msdn.microsoft.com/library/dn642451.aspx)) zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-178">When using textures in a game the texture size will rarely match the area we want to use it in, but we can use different kind of texture filtering to get the graphic card to interpolate the color we want from the pixels of the texture ([Texture Filtering](https://msdn.microsoft.com/library/dn642451.aspx)).</span></span> <span data-ttu-id="7dbb0-179">Die Filterung, die uns interessiert ist [bilineare Filterung](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) die wird den Wert jedes Pixels mit dem 4 nächsten Nachbarn berechnet.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-179">The filtering that interests us is [bilinear filtering](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) which will compute the value of any pixel using the 4 nearest neighbors.</span></span>

![Ursprüngliches vor dem Filtern](images/texture-1.png)

![Ergebnis nach dem Filtern](images/texture-2.png)

<span data-ttu-id="7dbb0-182">Mit dieser Eigenschaft sehen wir, dass jedes Mal, wenn wir versuchen, eine Textur in einem Bereich doppelt so groß zu zeichnen, das Ergebnis verwirft.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-182">Using this property, we see that each time we try to draw a texture into an area twice as big, it blurs the result.</span></span>

<span data-ttu-id="7dbb0-183">Anstatt auf einen voll Bildschirm zu rendern und die kostbaren Millisekunden zu verlieren, würden wir uns auf eine kleine Version des Bildschirms rendern.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-183">Instead of rendering to a full screen and losing those precious milliseconds we could be spending on something else, we render to a tiny version of the screen.</span></span> <span data-ttu-id="7dbb0-184">Wenn Sie dann diese Textur kopieren und Sie um einen Faktor von 2 mehrmals Strecken, werden wir wieder zum voll Bildschirm zurückkehren, während wir den Inhalt des Prozesses verschleiern.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-184">Then, by copying this texture and stretching it by a factor of 2 several times, we get back to full screen while blurring the content in the process.</span></span>

![x3 hochskalieren bis vollständige Auflösung.](images/galaxy-resolutions-300px.png)

<span data-ttu-id="7dbb0-186">x3 hochskalieren bis vollständige Auflösung.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-186">x3 upscale back to full resolution.</span></span>



<span data-ttu-id="7dbb0-187">Dadurch konnten wir den cloudteil nur mit einem Bruchteil der ursprünglichen Kosten erreichen.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-187">This allowed us to get the cloud part with only a fraction of the original cost.</span></span> <span data-ttu-id="7dbb0-188">Anstatt Clouds für die vollständige Auflösung hinzuzufügen, zeichnen wir nur die 1/64-Stel der Pixel und Strecken die Textur auf die vollständige Auflösung zurück.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-188">Instead of adding clouds on the full resolution, we only paint 1/64th of the pixels and just stretch the texture back to full resolution.</span></span>

![Links, mit einer hochskalieren von 1/8 bis vollständiger Auflösung; und das Recht, mit drei hochskalieren von 2.](images/stars-upscaled-300px.jpg)

<span data-ttu-id="7dbb0-190">Links, mit einer hochskalieren von 1/8 bis vollständiger Auflösung; und das Recht, mit drei hochskalieren von 2.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-190">Left, with an upscale from 1/8th to full resolution; and right, with 3 upscale using power of 2.</span></span>


<span data-ttu-id="7dbb0-191">Beachten Sie, dass der Versuch, zwischen 1 und 64 von der Größe in eine ganze Größe zu wechseln, vollständig anders aussehen würde, da die Grafikkarte weiterhin 4 Pixel im Setup verwendet, um einen größeren Bereich zu schattieren und die Artefakte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-191">Note that trying to go from 1/64th of the size to the full size in one go would look completely different, as the graphic card would still use 4 pixels in our setup to shade a bigger area and artifacts start to appear.</span></span>

<span data-ttu-id="7dbb0-192">Wenn wir dann voll auflösende Sterne mit kleineren Karten hinzufügen, erhalten wir die vollständige Galaxy-Version:</span><span class="sxs-lookup"><span data-stu-id="7dbb0-192">Then, if we add full resolution stars with smaller cards, we get the full galaxy:</span></span>

![Fast Final result of Galaxy Rendering using Full Resolution Stars](images/full-galaxy-500px.png)

<span data-ttu-id="7dbb0-194">Nachdem wir uns auf der rechten Spur mit der Form befanden, haben wir eine Schicht von Clouds hinzugefügt, die temporären Punkte ausgetauscht, die wir in Photoshop gezeichnet haben, und einige zusätzliche Farben hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-194">Once we were on the right track with the shape, we added a layer of clouds, swapped out the temporary dots with ones we painted in Photoshop, and added some additional color.</span></span> <span data-ttu-id="7dbb0-195">Das Ergebnis war eine Milch Methode, die unsere Kunst-und Engineering-Teams sowohl gut als auch unsere Ziele für tiefe, Volumen und Bewegung –, ohne die CPU zu steuern.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-195">The result was a Milky Way Galaxy our art and engineering teams both felt good about and it met our goals of having depth, volume, and motion—all without taxing the CPU.</span></span>

![Unsere endgültige Milchwege-Galaxy in 3D.](images/final-galaxy-500px.jpg)

<span data-ttu-id="7dbb0-197">Unsere endgültige Milchwege-Galaxy in 3D.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-197">Our final Milky Way Galaxy in 3D.</span></span>


### <a name="more-to-explore"></a><span data-ttu-id="7dbb0-198">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7dbb0-198">More to explore</span></span>

<span data-ttu-id="7dbb0-199">Wir haben den Code für die Galaxy Explorer-app geöffnet und auf [GitHub](https://github.com/Microsoft/GalaxyExplorer) zur Verfügung gestellt, auf dem Entwickler aufbauen können.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-199">We've open-sourced the code for the Galaxy Explorer app and made it available on [GitHub](https://github.com/Microsoft/GalaxyExplorer) for developers to build on.</span></span>

<span data-ttu-id="7dbb0-200">Möchten Sie mehr über den Entwicklungsprozess für den Galaxy Explorer erfahren?</span><span class="sxs-lookup"><span data-stu-id="7dbb0-200">Interested in finding out more about the development process for Galaxy Explorer?</span></span> <span data-ttu-id="7dbb0-201">Sehen Sie sich alle früheren Projekt Updates auf dem [Microsoft hololens-YouTube-Kanal](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)an.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-201">Check out all our past project updates on the [Microsoft HoloLens YouTube channel](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="7dbb0-202">Informationen zu den Autoren</span><span class="sxs-lookup"><span data-stu-id="7dbb0-202">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><span data-ttu-id="7dbb0-203"><b>Karim Luccin</b> ist ein Software Entwickler und Liebhaber von visuellen Elementen.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-203"><b>Karim Luccin</b> is a Software Engineer and fancy visuals enthusiast.</span></span> <span data-ttu-id="7dbb0-204">Er war der Grafik Techniker für Galaxy Explorer.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-204">He was the Graphics Engineer for Galaxy Explorer.</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><span data-ttu-id="7dbb0-205"><b>Andy zibits</b> ist ein Kunst Leiter und Platz Liebhaber, der das 3D-Modellierungs Team für den Galaxy Explorer verwaltet und für noch mehr Partikel gekämpft hat.</span><span class="sxs-lookup"><span data-stu-id="7dbb0-205"><b>Andy Zibits</b> is an Art Lead and space enthusiast who managed the 3D modeling team for Galaxy Explorer and fought for even more particles.</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="7dbb0-206">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7dbb0-206">See also</span></span>
* [<span data-ttu-id="7dbb0-207">Galaxy Explorer auf GitHub</span><span class="sxs-lookup"><span data-stu-id="7dbb0-207">Galaxy Explorer on GitHub</span></span>](https://github.com/Microsoft/GalaxyExplorer)
* [<span data-ttu-id="7dbb0-208">Galaxy Explorer-Projektaktualisierungen auf YouTube</span><span class="sxs-lookup"><span data-stu-id="7dbb0-208">Galaxy Explorer project updates on YouTube</span></span>](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
