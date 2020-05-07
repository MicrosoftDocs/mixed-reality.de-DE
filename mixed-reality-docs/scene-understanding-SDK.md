---
title: Scene Understanding SDK
description: Programmier Handbuch zum Scene Understanding SDK
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: Szenen Verständnis, räumliche Zuordnung, Windows Mixed Reality, Unity
ms.openlocfilehash: 3eb54f84e30b2354907204895e62accdb9ad54f9
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604951"
---
# <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="f6d39-104">Übersicht über das Szene Verständnis von SDK</span><span class="sxs-lookup"><span data-stu-id="f6d39-104">Scene understanding SDK overview</span></span>

<span data-ttu-id="f6d39-105">Das Ziel des szenarienverständnisses besteht darin, die nicht strukturierten Umgebungs Sensordaten zu transformieren, die ihr Mixed Reality-Gerät erfasst, und Sie in eine leistungsstarke, aber abstrahierte Darstellung umzuwandeln, die intuitiv und einfach zu entwickeln ist.</span><span class="sxs-lookup"><span data-stu-id="f6d39-105">The goal of Scene understanding is to transform the un-structured environment sensor data that your Mixed Reality device captures and to convert it into a powerful but abstracted representation that is intuitive and easy to develop for.</span></span> <span data-ttu-id="f6d39-106">Das SDK fungiert als Kommunikationsschicht zwischen Ihrer Anwendung und der Szene zur Laufzeit.</span><span class="sxs-lookup"><span data-stu-id="f6d39-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="f6d39-107">Sie ist darauf ausgerichtet, vorhandene standardkonstrukte wie 3D-Szenen Diagramme für 3D-Darstellungen und 2D-Rechtecke und Panels für 2D-Anwendungen zu imitieren.</span><span class="sxs-lookup"><span data-stu-id="f6d39-107">It's aimed to mimic existing standard constructs such as 3D scene graphs for 3D representations and 2D rectangles and panels for 2D applications.</span></span> <span data-ttu-id="f6d39-108">Die Konstrukte der Konstrukte verstehen sich zwar konkreten Frameworks, die Sie möglicherweise verwenden, aber im Allgemeinen ist das Framework unabhängig von der frameworkinterität eine Interoperabilität zwischen unterschiedlichen Frameworks, die mit ihr interagieren.</span><span class="sxs-lookup"><span data-stu-id="f6d39-108">While the constructs Scene Understanding mimics will map to concrete frameworks you may use, in general SceneUnderstanding is framework agnostic allowing for interop between varied frameworks that interact with it.</span></span> <span data-ttu-id="f6d39-109">Wenn das Verständnis von Szenen weiterentwickelt wird, besteht die Rolle des SDK darin, dass neue Darstellungen und Funktionen weiterhin in einem vereinheitlichten Framework verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="f6d39-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="f6d39-110">In diesem Dokument werden zunächst allgemeine Konzepte vorgestellt, die Ihnen helfen, sich mit der Entwicklungsumgebung und-Nutzung vertraut zu machen und dann eine ausführlichere Dokumentation für bestimmte Klassen und Konstrukte bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="f6d39-110">In this document we will first introduce high level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="f6d39-111">Wo erhalte ich das SDK?</span><span class="sxs-lookup"><span data-stu-id="f6d39-111">Where do I get the SDK?</span></span>

<span data-ttu-id="f6d39-112">Das sceneunderstanding SDK kann über nuget heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="f6d39-112">The SceneUnderstanding SDK is downloadable via NuGet.</span></span>

[<span data-ttu-id="f6d39-113">Sceneunderstanding-SDK</span><span class="sxs-lookup"><span data-stu-id="f6d39-113">SceneUnderstanding SDK</span></span>](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

<span data-ttu-id="f6d39-114">**Hinweis:** die neueste Version hängt von den Vorschau Paketen ab, und Sie müssen die Vorabversion von Paketen aktivieren, um Sie anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="f6d39-114">**Note:** the latest release depends on preview packages and you will need to enable pre-release packages to see it.</span></span>

<span data-ttu-id="f6d39-115">Ab Version 0.5.2022-RC unterstützt Szenen Verständnis sprach Projektionen für c# und C++, sodass Anwendungen Anwendungen für Win32-oder UWP-Plattformen entwickeln können.</span><span class="sxs-lookup"><span data-stu-id="f6d39-115">As of version 0.5.2022-rc, Scene Understanding supports language projections for C# and C++ allowing applications to develop applications for Win32 or UWP platforms.</span></span> <span data-ttu-id="f6d39-116">Ab dieser Version unterstützt sceneunderstanding die Unterstützung von Unity im Editor, wobei der sceneobserver, der ausschließlich für die Kommunikation mit HoloLens2 verwendet wird, verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f6d39-116">As of this version, SceneUnderstanding supports unity in-editor support barring the SceneObserver which is used solely for communicating with HoloLens2.</span></span> 

<span data-ttu-id="f6d39-117">Sceneunderstanding erfordert Windows SDK-Version 18362 oder höher.</span><span class="sxs-lookup"><span data-stu-id="f6d39-117">SceneUnderstanding requires Windows SDK version 18362 or higher.</span></span> 

<span data-ttu-id="f6d39-118">Wenn Sie das SDK in einem Unity-Projekt verwenden, verwenden Sie [nuget für Unity](https://github.com/GlitchEnzo/NuGetForUnity) , um das Paket in Ihrem Projekt zu installieren.</span><span class="sxs-lookup"><span data-stu-id="f6d39-118">If you are using the SDK in a Unity project, please use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity) to install the package into your project.</span></span>

## <a name="conceptual-overview"></a><span data-ttu-id="f6d39-119">Konzeptionelle Übersicht</span><span class="sxs-lookup"><span data-stu-id="f6d39-119">Conceptual Overview</span></span>

### <a name="the-scene"></a><span data-ttu-id="f6d39-120">Die Szene</span><span class="sxs-lookup"><span data-stu-id="f6d39-120">The Scene</span></span>

<span data-ttu-id="f6d39-121">Ihr gemischtes Reality-Gerät integriert ständig Informationen zu den in Ihrer Umgebung angezeigten Informationen.</span><span class="sxs-lookup"><span data-stu-id="f6d39-121">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="f6d39-122">In der Szene werden alle diese Datenquellen verstanden und eine einzelne, zusammenhängende Abstraktion erzeugt.</span><span class="sxs-lookup"><span data-stu-id="f6d39-122">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="f6d39-123">Szenen Verständnis generiert Szenen, bei denen es sich um eine Komposition von [sceneobjects](scene-understanding-SDK.md#sceneobjects) handelt, die eine Instanz eines einzelnen Objekts darstellen (z. b. eine Wand/Ceiling/Floor). Szenen Objekte selbst sind eine Komposition von [scenecomponents](scene-understanding-SDK.md#scenecomponents) , die präziseste Teile darstellen, die dieses sceneobject bilden.</span><span class="sxs-lookup"><span data-stu-id="f6d39-123">Scene Understanding generates Scenes which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (e.g. a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents](scene-understanding-SDK.md#scenecomponents) which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="f6d39-124">Beispiele für Komponenten sind Quads und Meshes, aber in der Zukunft könnten Begrenzungs Felder, Kollisions Netze, Metadaten usw. darstellen.</span><span class="sxs-lookup"><span data-stu-id="f6d39-124">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision meshes, metadata etc...</span></span>

<span data-ttu-id="f6d39-125">Der Prozess der Umstellung der Rohdaten des Sensors in eine Szene ist ein potenziell kostspieliger Vorgang, der für sehr große Speicherplätze (~ 10X 10m) bis zu Minuten für sehr große Leerzeichen (~ 50X 50M) Sekunden in Anspruch nehmen kann und daher nicht vom Gerät ohne Anwendungsanforderung berechnet wird.</span><span class="sxs-lookup"><span data-stu-id="f6d39-125">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for very large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="f6d39-126">Stattdessen wird die Szenen Generierung von Ihrer Anwendung Bedarfs gesteuert ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="f6d39-126">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="f6d39-127">Die sceneobserver-Klasse verfügt über statische Methoden, die eine Szene berechnen oder deserialisieren können, die Sie dann auflisten/mit der Sie interagieren können.</span><span class="sxs-lookup"><span data-stu-id="f6d39-127">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="f6d39-128">Die "Compute"-Aktion wird Bedarfs gesteuert ausgeführt und wird auf der CPU ausgeführt, aber in einem separaten Prozess (dem Mixed Reality-Treiber).</span><span class="sxs-lookup"><span data-stu-id="f6d39-128">The "Compute" action is executed on-demand and executes on the CPU but in a separate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="f6d39-129">Während wir in einem anderen Prozess berechnen, werden die resultierenden Szenen Daten jedoch in der Anwendung im Scene-Objekt gespeichert und verwaltet.</span><span class="sxs-lookup"><span data-stu-id="f6d39-129">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="f6d39-130">Das folgende Diagramm veranschaulicht den Prozessfluss und zeigt Beispiele für zwei Anwendungen an, die mit der Laufzeitumgebung vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="f6d39-130">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![Prozessdiagramm](images/SU-ProcessFlow.png)

<span data-ttu-id="f6d39-132">Auf der linken Seite befindet sich ein Diagramm der Mixed Reality-Laufzeit, die immer aktiv ist und in einem eigenen Prozess ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f6d39-132">On the left hand side is a diagram of the mixed reality runtime which is always on and running in its own process.</span></span> <span data-ttu-id="f6d39-133">Diese Laufzeit ist für die Durchführung von Geräte Nachverfolgung, räumlicher Zuordnung und anderen Vorgängen zuständig, die von der Szene verstanden werden, um die Welt zu verstehen und zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="f6d39-133">This runtime is responsible for performing device tracking, spatial mapping, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="f6d39-134">Auf der rechten Seite des Diagramms zeigen wir zwei theoretische Anwendungen, die das Verständnis von Szenen nutzen.</span><span class="sxs-lookup"><span data-stu-id="f6d39-134">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="f6d39-135">Die erste Anwendung stellt mit mrtk eine Schnittstelle dar, die das Scene Understanding SDK intern verwendet, die zweite App berechnet und verwendet zwei separate Szenen Instanzen.</span><span class="sxs-lookup"><span data-stu-id="f6d39-135">The first application interfaces with MRTK which uses the Scene Understanding SDK internally, the second app computes and uses two separate scene instances.</span></span> <span data-ttu-id="f6d39-136">In allen drei Szenen in diesem Diagramm werden unterschiedliche Instanzen der Kulissen generiert. der Treiber verfolgt keinen globalen Status, der von Anwendungen gemeinsam genutzt wird, und Szenen Objekte in einer Szene werden nicht in einer anderen Szene gefunden.</span><span class="sxs-lookup"><span data-stu-id="f6d39-136">All 3 Scenes in this diagram generate distinct instances of the scenes, the driver is not tracking global state that is shared between applications and Scene Objects in one scene are not found in another.</span></span> <span data-ttu-id="f6d39-137">Das Verständnis von Szenen bietet einen Mechanismus, mit dem Sie die Zeit nachverfolgen können. Dies geschieht jedoch mithilfe des SDKs, und der Code, der diese Nachverfolgung ausführt, wird im SDK im App-Prozess ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="f6d39-137">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK and the code that performs this tracking is running in the SDK in your app's process.</span></span>

<span data-ttu-id="f6d39-138">Da jede Szene Ihre Daten im Speicherbereich Ihrer Anwendung speichert, können Sie davon ausgehen, dass alle Funktionen des Szene Objekts oder der internen Daten immer im Prozess ihrer Anwendung ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="f6d39-138">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

### <a name="layout"></a><span data-ttu-id="f6d39-139">Layout</span><span class="sxs-lookup"><span data-stu-id="f6d39-139">Layout</span></span>

<span data-ttu-id="f6d39-140">Um mit dem Verständnis von Szenen zu arbeiten, ist es möglicherweise hilfreich zu wissen, wie die Laufzeit Komponenten logisch und physisch repräsentiert.</span><span class="sxs-lookup"><span data-stu-id="f6d39-140">To work with Scene Understanding it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="f6d39-141">Die Szene stellt Daten mit einem bestimmten Layout dar, das als einfach gewählt wurde, während eine zugrunde liegende Struktur beibehalten wird, die für zukünftige Anforderungen geeignet ist, ohne dass größere Revisionen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="f6d39-141">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="f6d39-142">In der Szene werden alle Komponenten (Bausteine für alle Szene Objekte) in einer flachen Liste gespeichert, und die Hierarchie und Komposition werden durch Verweise definiert, bei denen bestimmte Komponenten auf andere verweisen.</span><span class="sxs-lookup"><span data-stu-id="f6d39-142">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="f6d39-143">Im folgenden finden Sie ein Beispiel für eine Struktur in der flachen und logischen Form.</span><span class="sxs-lookup"><span data-stu-id="f6d39-143">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="f6d39-144">Logisches Layout</span><span class="sxs-lookup"><span data-stu-id="f6d39-144">Logical Layout</span></span></th><th><span data-ttu-id="f6d39-145">Physisches Layout</span><span class="sxs-lookup"><span data-stu-id="f6d39-145">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="f6d39-146">Szene</span><span class="sxs-lookup"><span data-stu-id="f6d39-146">Scene</span></span>
  <ul>
  <li><span data-ttu-id="f6d39-147">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="f6d39-147">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="f6d39-148">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="f6d39-148">SceneMesh_1</span></span></li>
      <li><span data-ttu-id="f6d39-149">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="f6d39-149">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="f6d39-150">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="f6d39-150">SceneQuad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="f6d39-151">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="f6d39-151">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="f6d39-152">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="f6d39-152">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="f6d39-153">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="f6d39-153">SceneQuad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="f6d39-154">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="f6d39-154">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="f6d39-155">SceneMesh_3</span><span class="sxs-lookup"><span data-stu-id="f6d39-155">SceneMesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="f6d39-156">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="f6d39-156">SceneObject_1</span></span></li>
  <li><span data-ttu-id="f6d39-157">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="f6d39-157">SceneObject_2</span></span></li>
  <li><span data-ttu-id="f6d39-158">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="f6d39-158">SceneObject_3</span></span></li>
  <li><span data-ttu-id="f6d39-159">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="f6d39-159">SceneQuad_1</span></span></li>
  <li><span data-ttu-id="f6d39-160">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="f6d39-160">SceneQuad_2</span></span></li>
  <li><span data-ttu-id="f6d39-161">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="f6d39-161">SceneQuad_3</span></span></li>
  <li><span data-ttu-id="f6d39-162">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="f6d39-162">SceneMesh_1</span></span></li>
  <li><span data-ttu-id="f6d39-163">SceneMesh_2</span><span class="sxs-lookup"><span data-stu-id="f6d39-163">SceneMesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="f6d39-164">In dieser Abbildung wird der Unterschied zwischen dem physischen und dem logischen Layout der Szene hervorgehoben.</span><span class="sxs-lookup"><span data-stu-id="f6d39-164">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="f6d39-165">Auf der linken Seite sehen Sie das hierarchische Layout der Daten, die Ihre Anwendung beim Auflisten der Szene sieht.</span><span class="sxs-lookup"><span data-stu-id="f6d39-165">On the left we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="f6d39-166">Auf der rechten Seite sehen Sie, dass die Szene tatsächlich aus 12 unterschiedlichen Komponenten besteht, auf die bei Bedarf einzeln zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="f6d39-166">On the right we see that the scene is actually comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="f6d39-167">Bei der Verarbeitung einer neuen Szene erwarten wir, dass Anwendungen diese Hierarchie logisch durchlaufen. bei der Überwachung zwischen Szenen Aktualisierungen sind einige Anwendungen jedoch möglicherweise nur für bestimmte Komponenten interessant, die von zwei Szenen gemeinsam genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="f6d39-167">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

## <a name="api-overview"></a><span data-ttu-id="f6d39-168">API-Übersicht</span><span class="sxs-lookup"><span data-stu-id="f6d39-168">API overview</span></span>

<span data-ttu-id="f6d39-169">Der folgende Abschnitt enthält eine allgemeine Übersicht über die Konstrukte in der Szene.</span><span class="sxs-lookup"><span data-stu-id="f6d39-169">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="f6d39-170">In diesem Abschnitt erfahren Sie, wie Szenen dargestellt werden und für welche Komponenten die verschiedenen Komponenten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f6d39-170">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="f6d39-171">Im nächsten Abschnitt werden konkrete Codebeispiele und zusätzliche Details bereitgestellt, die in dieser Übersicht ausgeblendet sind.</span><span class="sxs-lookup"><span data-stu-id="f6d39-171">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

<span data-ttu-id="f6d39-172">Alle unten beschriebenen Typen befinden sich im- `Microsoft.MixedReality.SceneUnderstanding` Namespace.</span><span class="sxs-lookup"><span data-stu-id="f6d39-172">All of the types described below reside in the `Microsoft.MixedReality.SceneUnderstanding` namespace.</span></span>

### <a name="scenecomponents"></a><span data-ttu-id="f6d39-173">Scenecomponents</span><span class="sxs-lookup"><span data-stu-id="f6d39-173">SceneComponents</span></span>

<span data-ttu-id="f6d39-174">Nachdem Sie nun das logische Layout von Szenen verstanden haben, können wir nun das Konzept der scenecomponents und deren Verwendung zum Verfassen der Hierarchie vorstellen.</span><span class="sxs-lookup"><span data-stu-id="f6d39-174">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they are used to compose hierarchy.</span></span> <span data-ttu-id="f6d39-175">Scenecomponents sind die differenzierteren Dekompositionen in sceneunderstanding, die ein einzelnes Kernstück darstellen, z. b. ein Mesh-, ein Quad-oder ein Begrenzungsfeld.</span><span class="sxs-lookup"><span data-stu-id="f6d39-175">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, e.g. a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="f6d39-176">Scenecomponents sind Dinge, die unabhängig voneinander aktualisiert werden können und von anderen scenecomponents referenziert werden können. Daher verfügen Sie über eine einzelne globale Eigenschaft, die eine eindeutige ID für diese Art von Nachverfolgung/Verweis Mechanismus zulässt.</span><span class="sxs-lookup"><span data-stu-id="f6d39-176">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique Id, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="f6d39-177">IDs werden sowohl für die logische Komposition der Szenen Hierarchie als auch für die Objekt Persistenz verwendet (der Vorgang der Aktualisierung einer Szene relativ zu einer anderen).</span><span class="sxs-lookup"><span data-stu-id="f6d39-177">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="f6d39-178">Wenn Sie jede neu berechnete Szene als unterschiedlich behandeln und einfach alle darin enthaltenen Daten auflisten, sind die IDs größtenteils für Sie transparent.</span><span class="sxs-lookup"><span data-stu-id="f6d39-178">If you are treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="f6d39-179">Wenn Sie jedoch planen, Komponenten über mehrere Updates zu verfolgen, verwenden Sie die IDs, um scenecomponents zwischen Szene Objekten zu indizieren und zu suchen.</span><span class="sxs-lookup"><span data-stu-id="f6d39-179">However, if you are planning to track components over several updates you will use the Ids to index and find SceneComponents between Scene objects.</span></span>

### <a name="sceneobjects"></a><span data-ttu-id="f6d39-180">Sceneobjects</span><span class="sxs-lookup"><span data-stu-id="f6d39-180">SceneObjects</span></span>

<span data-ttu-id="f6d39-181">Ein sceneobject ist eine scenecomponent, die eine Instanz eines "Thing" darstellt, z. b. eine Wand, eine Fläche, eine Obergrenze usw... ausgedrückt durch ihre Kind-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="f6d39-181">A SceneObject is a SceneComponent that represents an instance of a "thing" e.g. a wall, a floor, a ceiling, etc... expressed by their Kind property.</span></span> <span data-ttu-id="f6d39-182">Sceneobjects sind geometrisch und verfügen daher über Funktionen und Eigenschaften, die ihre Position im Raum darstellen, Sie enthalten jedoch keine geometrische oder logische Struktur.</span><span class="sxs-lookup"><span data-stu-id="f6d39-182">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="f6d39-183">Stattdessen verweisen sceneobjects auf andere scenecomponents, insbesondere scenequads und scenemesches, die die unterschiedlichen Darstellungen bereitstellen, die vom System unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="f6d39-183">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads and SceneMeshes which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="f6d39-184">Wenn eine neue Szene berechnet wird, listet Ihre Anwendung wahrscheinlich die sceneobjects der Szene auf, um zu verarbeiten, was Sie interessiert.</span><span class="sxs-lookup"><span data-stu-id="f6d39-184">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="f6d39-185">Sceneobjects können eine der folgenden Möglichkeiten aufweisen:</span><span class="sxs-lookup"><span data-stu-id="f6d39-185">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="f6d39-186">Sceneobjectkind</span><span class="sxs-lookup"><span data-stu-id="f6d39-186">SceneObjectKind</span></span></th> <th><span data-ttu-id="f6d39-187">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="f6d39-187">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="f6d39-188">Hintergrund</span><span class="sxs-lookup"><span data-stu-id="f6d39-188">Background</span></span></td><td><span data-ttu-id="f6d39-189">Das sceneobject-Objekt ist bekannt, dass es sich <b>nicht</b> um eines der anderen erkannten Arten von Szenen Objekten handelt.</span><span class="sxs-lookup"><span data-stu-id="f6d39-189">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="f6d39-190">Diese Klasse sollte nicht mit unknown verwechselt werden, wenn der Hintergrund bekanntermaßen nicht "Wall/Floor/Ceiling" ist usw... Obwohl unbekannt noch nicht kategorisiert ist.</span><span class="sxs-lookup"><span data-stu-id="f6d39-190">This class should not be confused with Unknown where Background is known not to be wall/floor/ceiling etc... while unknown is not yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="f6d39-191">And</span><span class="sxs-lookup"><span data-stu-id="f6d39-191">Wall</span></span></td><td><span data-ttu-id="f6d39-192">Eine physische Wand.</span><span class="sxs-lookup"><span data-stu-id="f6d39-192">A physical wall.</span></span> <span data-ttu-id="f6d39-193">Wände werden als unveränderbare Umgebungs Strukturen angesehen.</span><span class="sxs-lookup"><span data-stu-id="f6d39-193">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="f6d39-194">Etage</span><span class="sxs-lookup"><span data-stu-id="f6d39-194">Floor</span></span></td><td><span data-ttu-id="f6d39-195">Die Ebenen sind beliebige Oberflächen, auf denen eine durchlaufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="f6d39-195">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="f6d39-196">Hinweis: die Treppe sind keine Ebenen.</span><span class="sxs-lookup"><span data-stu-id="f6d39-196">Note: stairs are not floors.</span></span> <span data-ttu-id="f6d39-197">Beachten Sie auch, dass die Fußböden eine beliebige über-und-Oberfläche voraussetzen und daher keine explizite Annahme eines Singular ist.</span><span class="sxs-lookup"><span data-stu-id="f6d39-197">Also note, that floors assume any walkable surface and therefore there is no explicit assumption of a singular floor.</span></span> <span data-ttu-id="f6d39-198">Strukturen mit mehreren Ebenen, Rampen usw... sollten alle als Floor klassifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="f6d39-198">Multi-level structures, ramps etc... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="f6d39-199">Ceiling</span><span class="sxs-lookup"><span data-stu-id="f6d39-199">Ceiling</span></span></td><td><span data-ttu-id="f6d39-200">Die Oberfläche eines Raums.</span><span class="sxs-lookup"><span data-stu-id="f6d39-200">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="f6d39-201">Plattform</span><span class="sxs-lookup"><span data-stu-id="f6d39-201">Platform</span></span></td><td><span data-ttu-id="f6d39-202">Eine große flache Oberfläche, auf der Sie holograms platzieren können.</span><span class="sxs-lookup"><span data-stu-id="f6d39-202">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="f6d39-203">Diese stellen tendenziell Tabellen, Countertops und andere große horizontale Flächen dar.</span><span class="sxs-lookup"><span data-stu-id="f6d39-203">These tend to represent tables, countertops and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="f6d39-204">World</span><span class="sxs-lookup"><span data-stu-id="f6d39-204">World</span></span></td><td><span data-ttu-id="f6d39-205">Eine reservierte Bezeichnung für geometrische Daten, die für die Bezeichnung agnostisch ist.</span><span class="sxs-lookup"><span data-stu-id="f6d39-205">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="f6d39-206">Das Mesh, das durch Festlegen des enableworldmesh-UpdateFlags generiert wird, würde als Welt klassifiziert werden.</span><span class="sxs-lookup"><span data-stu-id="f6d39-206">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="f6d39-207">Unbekannt</span><span class="sxs-lookup"><span data-stu-id="f6d39-207">Unknown</span></span></td><td><span data-ttu-id="f6d39-208">Dieses Scene-Objekt muss noch klassifiziert und zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="f6d39-208">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="f6d39-209">Dies sollte nicht mit dem Hintergrund verwechselt werden, da es sich bei diesem Objekt um beliebige Elemente handeln könnte. das System ist noch nicht mit einer ausreichend starken Klassifizierung ausgestattet.</span><span class="sxs-lookup"><span data-stu-id="f6d39-209">This should not be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

### <a name="scenemesh"></a><span data-ttu-id="f6d39-210">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="f6d39-210">SceneMesh</span></span>

<span data-ttu-id="f6d39-211">Eine scenemesh ist eine scenecomponent, die die Geometrie willkürlicher geometrischer Objekte mithilfe einer Dreiecks Liste angleicht.</span><span class="sxs-lookup"><span data-stu-id="f6d39-211">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="f6d39-212">Scenemesches werden in verschiedenen Kontexten verwendet, Sie können Komponenten der wasserdichten Zellstruktur oder als worldmesh darstellen, das das ungebundene räumliche zustrukturnetz darstellt, das der Szene zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="f6d39-212">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh which represents the unbounded spatial mapping mesh associated with the Scene.</span></span> <span data-ttu-id="f6d39-213">Die für jedes Mesh bereitgestellten Index-und Vertex-Daten verwenden dasselbe vertraute Layout wie der [Scheitelpunkt und die Index Puffer](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) , die zum Rendern von Dreiecksnetzen in allen modernen renderingapis verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f6d39-213">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="f6d39-214">Beachten Sie, dass in der Szene in der Szene 32-Bit-Indizes verwendet werden und möglicherweise für bestimmte renderingengines in Blöcke aufgeteilt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="f6d39-214">Note that in Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="winding-order-and-coordinate-systems"></a><span data-ttu-id="f6d39-215">Sortieren von Reihenfolge und Koordinatensystemen</span><span class="sxs-lookup"><span data-stu-id="f6d39-215">Winding Order and Coordinate Systems</span></span>

<span data-ttu-id="f6d39-216">Alle Netzen, die von der Szene verstanden werden, sollten in einem rechts gerichteten Koordinatensystem mithilfe der Reihenfolge im Uhrzeigersinn die Netzen zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="f6d39-216">All meshes produced by Scene Understanding are expected to return meshes in a Right-Handed coordinate system using clockwise winding order.</span></span> 

<span data-ttu-id="f6d39-217">Hinweis: Betriebssystem-Builds vor. 191105 verfügen möglicherweise über einen bekannten Fehler, bei dem "World"-Netzen in der Reihenfolge gegen den Uhrzeigersinn zurückgegeben wurden, die anschließend korrigiert wurde.</span><span class="sxs-lookup"><span data-stu-id="f6d39-217">Note: OS builds prior to .191105 may have a known bug where "World" meshes were returning in Counter-Clockwise winding order, which has subsequently been fixed.</span></span>

### <a name="scenequad"></a><span data-ttu-id="f6d39-218">Scenequad</span><span class="sxs-lookup"><span data-stu-id="f6d39-218">SceneQuad</span></span>

<span data-ttu-id="f6d39-219">Eine scenequad ist eine scenecomponent, die 2D-Oberflächen darstellt, die die 3D--Welt belegen.</span><span class="sxs-lookup"><span data-stu-id="f6d39-219">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="f6d39-220">Scenequads können ähnlich wie Arkit arplaneanchor oder Arcore-Ebenen verwendet werden, bieten jedoch eine höhere Funktionalität als 2D-canvasen, die von flachen Apps verwendet werden sollen, oder erweiterte UX.</span><span class="sxs-lookup"><span data-stu-id="f6d39-220">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="f6d39-221">2D-spezifische APIs werden für Quads bereitgestellt, mit denen die Platzierung und das Layout einfach zu verwenden sind, und die Entwicklung (mit Ausnahme des Renderings) mit Quads sollte eher dem Arbeiten mit 2D-kanvasen als 3D--Meshes ähneln.</span><span class="sxs-lookup"><span data-stu-id="f6d39-221">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

#### <a name="scenequad-shape"></a><span data-ttu-id="f6d39-222">Scenequad-Form</span><span class="sxs-lookup"><span data-stu-id="f6d39-222">SceneQuad shape</span></span>

<span data-ttu-id="f6d39-223">Scenequads definieren eine begrenzte rechteckige Oberfläche in 2D.</span><span class="sxs-lookup"><span data-stu-id="f6d39-223">SceneQuads define a bounded rectangular surface in 2d.</span></span> <span data-ttu-id="f6d39-224">Scenequads stellen jedoch Oberflächen mit beliebigen und potenziell komplexen Formen dar (z. b. eine ringförmige Tabelle). Wenn Sie die komplexe Form der Oberfläche eines viervieres darstellen möchten, können Sie die getsurfacemask-API verwenden, um die Form der Oberfläche auf einem von Ihnen bereitgestellten Bild Puffer zu Renderern.</span><span class="sxs-lookup"><span data-stu-id="f6d39-224">However, SceneQuads are representing surfaces with arbitrary and potentially complex shapes (e.g. a donut shaped table.) To represent the complex shape of the surface of a quad you may use the GetSurfaceMask API to render the shape of the surface onto an image buffer you provide.</span></span> <span data-ttu-id="f6d39-225">Wenn das sceneobject mit dem Quad auch ein Mesh hat, sollten die Gitter Dreiecke diesem gerenderten Bild entsprechen, beide stellen eine echte Geometrie der Oberfläche dar, nur in 2D-oder 3D--Koordinaten.</span><span class="sxs-lookup"><span data-stu-id="f6d39-225">If the SceneObject that has the quad also has a mesh, the mesh triangles should be equivalent to this rendered image, they both represent real geometry of the surface, just either in 2d or 3d coordinates.</span></span>

## <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="f6d39-226">Scene Understanding SDK-Details und-Referenz</span><span class="sxs-lookup"><span data-stu-id="f6d39-226">Scene understanding SDK details and reference</span></span>

<span data-ttu-id="f6d39-227">Im folgenden Abschnitt wird erläutert, wie Sie mit den Grundlagen von sceneunderstanding vertraut werden.</span><span class="sxs-lookup"><span data-stu-id="f6d39-227">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="f6d39-228">In diesem Abschnitt werden die Grundlagen erläutert. zu diesem Zeitpunkt sollten Sie über genügend Kontext verfügen, um die Beispielanwendungen zu durchsuchen und zu sehen, wie sceneunderstanding ganzheitlich genutzt wird.</span><span class="sxs-lookup"><span data-stu-id="f6d39-228">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

### <a name="initialization"></a><span data-ttu-id="f6d39-229">Initialisierung</span><span class="sxs-lookup"><span data-stu-id="f6d39-229">Initialization</span></span>

<span data-ttu-id="f6d39-230">Der erste Schritt bei der Arbeit mit sceneunderstanding besteht darin, dass Ihre Anwendung auf ein Szene Objekt verweist.</span><span class="sxs-lookup"><span data-stu-id="f6d39-230">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="f6d39-231">Dies kann auf zwei Arten erfolgen: eine Szene kann entweder vom Treiber berechnet werden, oder eine vorhandene Szene, die in der Vergangenheit berechnet wurde, kann deserialisiert werden.</span><span class="sxs-lookup"><span data-stu-id="f6d39-231">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="f6d39-232">Letzteres ist besonders nützlich für das Arbeiten mit sceneunderstanding während der Entwicklung, bei dem Anwendungen und Erfahrungen schnell ohne ein gemischtes Reality-Gerät prototypisiert werden können.</span><span class="sxs-lookup"><span data-stu-id="f6d39-232">The latter is particularly useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="f6d39-233">Szenen werden mithilfe eines sceneobserver berechnet.</span><span class="sxs-lookup"><span data-stu-id="f6d39-233">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="f6d39-234">Bevor Sie eine Szene erstellen, sollte Ihre Anwendung Ihr Gerät Abfragen, um sicherzustellen, dass Sie sceneunderstanding unterstützt, sowie den Benutzer Zugriff auf Informationen anfordern, die von sceneunderstanding benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="f6d39-234">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="f6d39-235">Wenn requestaccessasync () nicht aufgerufen wird, tritt beim Berechnen einer neuen Szene ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="f6d39-235">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="f6d39-236">Als Nächstes berechnen wir eine neue Szene, die auf dem Mixed Reality-Headset liegt und über einen Radius von 10 Metern verfügt.</span><span class="sxs-lookup"><span data-stu-id="f6d39-236">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10 meter radius.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-aka-the-pc-path"></a><span data-ttu-id="f6d39-237">Initialisierung aus Daten (auch als bezeichnet).</span><span class="sxs-lookup"><span data-stu-id="f6d39-237">Initialization from Data (aka.</span></span> <span data-ttu-id="f6d39-238">der PC-Pfad)</span><span class="sxs-lookup"><span data-stu-id="f6d39-238">the PC Path)</span></span>

<span data-ttu-id="f6d39-239">Szenen können für den direkten Verbrauch berechnet werden, Sie können jedoch auch in serialisierter Form für die spätere Verwendung berechnet werden.</span><span class="sxs-lookup"><span data-stu-id="f6d39-239">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="f6d39-240">Dies hat sich als sehr nützlich für die Entwicklung erwiesen, da Entwickler damit arbeiten können, ohne dass ein Gerät benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="f6d39-240">This has proven to be very useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="f6d39-241">Der Vorgang der Serialisierung einer Szene ist nahezu identisch mit dem berechnen, die Daten werden an Ihre Anwendung zurückgegeben, anstatt lokal vom SDK deserialisiert zu werden.</span><span class="sxs-lookup"><span data-stu-id="f6d39-241">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="f6d39-242">Sie können Sie dann selbst deserialisieren oder zur späteren Verwendung speichern.</span><span class="sxs-lookup"><span data-stu-id="f6d39-242">You may then deserialize it yourself or save it for future use.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneBlob for later
```

### <a name="sceneobject-enumeration"></a><span data-ttu-id="f6d39-243">Sceneobject-Enumeration</span><span class="sxs-lookup"><span data-stu-id="f6d39-243">SceneObject Enumeration</span></span>

<span data-ttu-id="f6d39-244">Nun, da Ihre Anwendung eine Szene hat, wird Ihre Anwendung mit sceneobjects beschäftigt und interagiert.</span><span class="sxs-lookup"><span data-stu-id="f6d39-244">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="f6d39-245">Dies erfolgt durch den Zugriff auf die **sceneobjects** -Eigenschaft:</span><span class="sxs-lookup"><span data-stu-id="f6d39-245">This is done by accessing the **SceneObjects** property:</span></span>

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-re-finding-components"></a><span data-ttu-id="f6d39-246">Komponenten Aktualisierung und-Suche</span><span class="sxs-lookup"><span data-stu-id="f6d39-246">Component update and re-finding components</span></span>

<span data-ttu-id="f6d39-247">Es gibt eine weitere Funktion, die Komponenten in der Szene abruft, die als ***findComponent***bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="f6d39-247">There is another function that retrieves components in the Scene called ***FindComponent***.</span></span> <span data-ttu-id="f6d39-248">Diese Funktion ist nützlich, wenn Überwachungs Objekte aktualisiert und in nachfolgenden Szenen gefunden werden.</span><span class="sxs-lookup"><span data-stu-id="f6d39-248">This function is useful when updating tracking objects and finding them in subsequent scenes.</span></span> <span data-ttu-id="f6d39-249">Mit dem folgenden Code wird eine neue Szene in Relation zu einer vorherigen Szene berechnet und dann die Fläche in der neuen Szene gefunden.</span><span class="sxs-lookup"><span data-stu-id="f6d39-249">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="f6d39-250">Zugreifen auf Meshes und Quads von Szenen Objekten</span><span class="sxs-lookup"><span data-stu-id="f6d39-250">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="f6d39-251">Nachdem sceneobjects gefunden wurde, möchte Ihre Anwendung wahrscheinlich auf die Daten zugreifen, die in den in den Metadaten/Meshes enthaltenen Daten enthalten sind, aus denen Sie besteht.</span><span class="sxs-lookup"><span data-stu-id="f6d39-251">Once SceneObjects have been found your application will most likely want to access the data that is contained in the quads/meshes that it is comprised of.</span></span> <span data-ttu-id="f6d39-252">Der Zugriff auf diese Daten erfolgt über die Eigenschaften " ***Quads*** " und " ***Meshes*** ".</span><span class="sxs-lookup"><span data-stu-id="f6d39-252">This data is accessed with the ***Quads*** and ***Meshes*** properties.</span></span> <span data-ttu-id="f6d39-253">Mit dem folgenden Code werden alle Quads und Netzen des Floor-Objekts aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="f6d39-253">The following code will enumerate all quads and meshes of our floor object.</span></span>

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

<span data-ttu-id="f6d39-254">Beachten Sie, dass es sich um das sceneobject-Objekt mit der Transformation handelt, die relativ zum Ursprung der Szene ist.</span><span class="sxs-lookup"><span data-stu-id="f6d39-254">Notice that it is the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="f6d39-255">Der Grund hierfür ist, dass das sceneobject-Objekt eine Instanz eines "Thing" darstellt und im Raum einstellbar ist, die Quads und die Netze stellen eine Geometrie dar, die relativ zu ihrem übergeordneten Element transformiert wird.</span><span class="sxs-lookup"><span data-stu-id="f6d39-255">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="f6d39-256">Es ist möglich, dass separate sceneobjects auf die gleichen scenemesh/scenequad scenecomponents verweisen. Außerdem ist es möglich, dass ein sceneobject-Objekt über mehr als eine scenemesh/scenequad verfügt.</span><span class="sxs-lookup"><span data-stu-id="f6d39-256">It is possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponents, and it is also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="f6d39-257">Umgang mit Transformationen</span><span class="sxs-lookup"><span data-stu-id="f6d39-257">Dealing with Transforms</span></span>

<span data-ttu-id="f6d39-258">Das Verständnis der Szene hat beim Umgang mit Transformationen einen absichtlichen Versuch unternommen, an herkömmlichen 3D-Szenen Darstellungen auszurichten.</span><span class="sxs-lookup"><span data-stu-id="f6d39-258">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="f6d39-259">Daher ist jede Szene auf ein einzelnes Koordinatensystem beschränkt, ähnlich wie die gängigsten 3D-Umwelt Darstellungen.</span><span class="sxs-lookup"><span data-stu-id="f6d39-259">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="f6d39-260">Sceneobjects stellen jeweils ihren Speicherort als Position und Ausrichtung innerhalb dieses Koordinatensystems bereit.</span><span class="sxs-lookup"><span data-stu-id="f6d39-260">SceneObjects each provide their location as a position and orientation within that coordinate system.</span></span> <span data-ttu-id="f6d39-261">Wenn Ihre Anwendung mit Szenen beschäftigt ist, die das Limit eines einzelnen Ursprungs überschreiten, können Sie sceneobjects an spatialanchor anfügen oder mehrere Szenen generieren und zusammen zusammenführen, aber aus Gründen der Einfachheit gehen wir davon aus, dass die wasserdichten Szenen in Ihrem eigenen Ursprung vorhanden sind, der durch eine durch Scene. originspatialgraphnodeid definierte NodeId lokalisiert wird.</span><span class="sxs-lookup"><span data-stu-id="f6d39-261">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene.OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="f6d39-262">Der folgende Unity-Code zeigt beispielsweise, wie Sie die Windows-perception-und Unity-APIs verwenden, um Koordinatensysteme gleich abzustimmen.</span><span class="sxs-lookup"><span data-stu-id="f6d39-262">The following Unity code, for example, shows how to use Windows Perception and Unity APIs to align coordinate systems together.</span></span> <span data-ttu-id="f6d39-263">Unter [spatialcoordinatesystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) und [spatialgraphinteroppreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) finden Sie ausführliche Informationen zu den Windows-perception-APIs und den systemeigenen [gemischten System Objekten in Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) . hier finden Sie ausführliche Informationen zum Abrufen eines spatialcoordinatesystem, das dem `.ToUnity()` Welt Ursprung von Unity entspricht `System.Numerics.Matrix4x4` , `UnityEngine.Matrix4x4`sowie der Erweiterungsmethode zum Wechseln zwischen und.</span><span class="sxs-lookup"><span data-stu-id="f6d39-263">See [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) and [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) for details on the Windows Perception APIs, and [Mixed Reality native objects in Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) for details on obtaining a SpatialCoordinateSystem that corresponds to Unity's world origin, as well as the `.ToUnity()` extension method for converting between `System.Numerics.Matrix4x4` and `UnityEngine.Matrix4x4`.</span></span>

```cs
public class SceneRootComponent : MonoBehavior
{
    public SpatialCoordinateSystem worldOrigin;
    public Scene scene;
    SpatialCoordinateSystem sceneOrigin;
    
    void Start()
    {
        // Initialize a SpatialCoordinateSystem for the scene's node in the system's Spatial Graph.
        scene.origin = SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
    }
    
    void Update()
    {
        // Try to get the current transform of the scene's spatial graph node.
        // This may not be available, e.g. when tracking has been lost.
        var sceneToWorld = sceneOrigin.TryGetTransformTo(worldOrigin);
        if (sceneToWorld.HasValue)
        {
            // Convert the transform to Unity numerics and update the game object.
            var sceneToWorldUnity = sceneToWorld.Value.ToUnity();
            this.gameObject.transform.SetPositionAndRotation(sceneToWorldUnity.GetColumn(3), sceneToWorldUnity.rotation);
        }
    }
}
```

<span data-ttu-id="f6d39-264">Jede `SceneObject` verfügt über `Position` eine `Orientation` -Eigenschaft und eine-Eigenschaft, die verwendet werden kann, um den entsprechenden Inhalt `Scene`relativ zum Ursprung der enthaltenden zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="f6d39-264">Each `SceneObject` has a `Position` and `Orientation` property which can be used to position corresponding content relative to the origin of the containing `Scene`.</span></span> <span data-ttu-id="f6d39-265">Im folgenden Beispiel wird z. b. davon ausgegangen, dass das Spiel ein untergeordnetes Element des Szenen Stamms ist, und seine lokale Position und Drehung `SceneObject`zum Ausrichten an einem bestimmten-Element zuordnet:</span><span class="sxs-lookup"><span data-stu-id="f6d39-265">For example, the following example assumes that the game is a child of the scene root, and assigns its local position and rotation to align to a given `SceneObject`:</span></span>

```cs
void SetLocalTransformFromSceneObject(GameObject gameObject, SceneObject sceneObject)
{
    gameObject.transform.localPosition = sceneObject.Position.ToUnity();
    gameObject.transform.localRotation = sceneObject.Orientation.ToUnity());
}
```

### <a name="quad"></a><span data-ttu-id="f6d39-266">Quad</span><span class="sxs-lookup"><span data-stu-id="f6d39-266">Quad</span></span>

<span data-ttu-id="f6d39-267">Die Quads wurden entwickelt, um 2D-Platzierungs Szenarios zu vereinfachen. Sie sollten sich als Erweiterungen für 2D-Canvas-UX-Elemente vorstellen.</span><span class="sxs-lookup"><span data-stu-id="f6d39-267">Quads were designed to facilitate 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="f6d39-268">Obwohl es sich bei den Quads um Komponenten von sceneobjects handelt, die in 3D gerendert werden können, werden die Quad-APIs selbst annehmen, dass die Quad-</span><span class="sxs-lookup"><span data-stu-id="f6d39-268">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="f6d39-269">Sie bieten Informationen wie Block, Form und Bereitstellen von APIs für die Platzierung.</span><span class="sxs-lookup"><span data-stu-id="f6d39-269">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="f6d39-270">Die Unterbrechungen haben rechteckige Blöcke, stellen aber beliebig geformte 2D-Oberflächen dar.</span><span class="sxs-lookup"><span data-stu-id="f6d39-270">Quads have rectangular extents, but they represent arbitrarily shaped 2D surfaces.</span></span> <span data-ttu-id="f6d39-271">Um die Platzierung auf diesen 2D-Oberflächen zu ermöglichen, die mit der 3D-Umgebung interagieren, bieten Sie Hilfsprogramme, um diese Interaktion zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="f6d39-271">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="f6d39-272">Das grundlegendes Verständnis von Szenen bietet derzeit zwei dieser Funktionen: **findcentermustplacement** und **gedecclusionmask**.</span><span class="sxs-lookup"><span data-stu-id="f6d39-272">Currently Scene Understanding provides two such functions, **FindCentermostPlacement** and **GetOcclusionMask**.</span></span> <span data-ttu-id="f6d39-273">Findcentermostplacement ist eine API auf hoher Ebene, die eine Position auf dem Quad sucht, an der ein Objekt platziert werden kann, und versucht, den optimalen Speicherort für das Objekt zu finden, das sicherstellt, dass sich das umgebende Feld auf der zugrunde liegenden Oberfläche befindet.</span><span class="sxs-lookup"><span data-stu-id="f6d39-273">FindCentermostPlacement is a high level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will reside on the underlying surface.</span></span>

<span data-ttu-id="f6d39-274">Im folgenden Beispiel wird gezeigt, wie Sie den am häufigsten ersetzbaren Speicherort suchen und ein – Hologramm für das Vierfache verankern.</span><span class="sxs-lookup"><span data-stu-id="f6d39-274">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

<span data-ttu-id="f6d39-275">Die Schritte 1-4 sind stark von Ihrem speziellen Framework/der Implementierung abhängig, die Designs sollten jedoch ähnlich sein.</span><span class="sxs-lookup"><span data-stu-id="f6d39-275">Steps 1-4 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="f6d39-276">Es ist wichtig zu beachten, dass das Vierfache eine begrenzte 2D-Ebene darstellt, die im Raum lokalisiert wird.</span><span class="sxs-lookup"><span data-stu-id="f6d39-276">It is important to note that the Quad simply represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="f6d39-277">Wenn Ihr Modul/Framework weiß, wo das Vierfache ist, und die Objekte in Relation zum Quad Hogen, werden Ihre Hologramme in Bezug auf die reale Welt ordnungsgemäß gefunden.</span><span class="sxs-lookup"><span data-stu-id="f6d39-277">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly with respect to the real world.</span></span> <span data-ttu-id="f6d39-278">Ausführlichere Informationen finden Sie in unseren Beispielen zu den Quads, in denen bestimmte Implementierungen angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="f6d39-278">For more detailed information please see our samples on quads which show specific implementations.</span></span>

### <a name="mesh"></a><span data-ttu-id="f6d39-279">Netz</span><span class="sxs-lookup"><span data-stu-id="f6d39-279">Mesh</span></span>

<span data-ttu-id="f6d39-280">Meshes stellen geometrische Darstellungen von Objekten oder Umgebungen dar.</span><span class="sxs-lookup"><span data-stu-id="f6d39-280">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="f6d39-281">Ähnlich wie bei der [räumlichen Zuordnung](spatial-mapping.md)verwendet Mesh-Index-und Vertex-Daten, die für jedes räumliche Oberflächen Mesh bereitgestellt werden, dasselbe vertraute Layout wie der Scheitelpunkt und die Index Puffer, die zum Rendern von Dreiecksnetzen in allen modernen Rendering-APIs verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f6d39-281">Much like [spatial mapping](spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="f6d39-282">Vertex-Positionen werden im Koordinatensystem von bereitgestellt `Scene`.</span><span class="sxs-lookup"><span data-stu-id="f6d39-282">Vertex positions are provided in the coordinate system of the `Scene`.</span></span> <span data-ttu-id="f6d39-283">Die spezifischen APIs, die zum Verweisen auf diese Daten verwendet werden, lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f6d39-283">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

<span data-ttu-id="f6d39-284">Der folgende Code enthält ein Beispiel für das Erstellen einer Dreiecks Liste aus der Mesh-Struktur:</span><span class="sxs-lookup"><span data-stu-id="f6d39-284">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="f6d39-285">Der Index/der Scheitelpunkt Puffer muss >= der Index/Scheitelpunkt Anzahl sein, kann aber auch willkürlich skaliert werden, um eine effiziente Wiederverwendung von Arbeitsspeicher zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="f6d39-285">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory re-use.</span></span>

## <a name="developing-with-scene-understandings"></a><span data-ttu-id="f6d39-286">Entwickeln mit Szenen Verständnissen</span><span class="sxs-lookup"><span data-stu-id="f6d39-286">Developing with scene understandings</span></span>

<span data-ttu-id="f6d39-287">An diesem Punkt sollten Sie die wichtigsten Bausteine der Szene verstehen, die Laufzeit und SDK versteht.</span><span class="sxs-lookup"><span data-stu-id="f6d39-287">At this point you should understand the core building blocks of the scene understanding runtime and SDK.</span></span> <span data-ttu-id="f6d39-288">Der größte Teil der Leistungsfähigkeit und Komplexität liegt in Zugriffs Mustern, der Interaktion mit 3D-Frameworks und Tools, die zusätzlich zu diesen APIs verfasst werden können, um erweiterte Aufgaben wie räumliche Planung, Raumanalyse, Navigation, Physik usw. auszuführen. Wir hoffen, diese Beispiele in Beispielen zu erfassen, die Sie in die richtige Richtung bringen sollten, um Ihre Szenarios zu glänzen.</span><span class="sxs-lookup"><span data-stu-id="f6d39-288">The bulk of the power and complexity lies in access patterns, interaction with 3D frameworks, and tools that can be written on top of these APIs to perform more advanced tasks like spatial planning, room analysis, navigation, physics etc. We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="f6d39-289">Wenn Beispiele/Szenarios nicht behandelt werden, informieren Sie uns, und wir versuchen, das Dokument/den Prototyp zu dokumentieren.</span><span class="sxs-lookup"><span data-stu-id="f6d39-289">If there are samples/scenarios we are not addressing, please let us know and we will try to document/prototype what you need.</span></span>

### <a name="where-can-i-get-sample-code"></a><span data-ttu-id="f6d39-290">Wo kann ich Beispielcode erhalten?</span><span class="sxs-lookup"><span data-stu-id="f6d39-290">Where can I get sample code?</span></span>

<span data-ttu-id="f6d39-291">Szeneninformationen zum Beispielcode für Unity finden Sie auf unserer Seite mit der [Unity-Beispielseite](https://github.com/sceneunderstanding-microsoft/unitysample) .</span><span class="sxs-lookup"><span data-stu-id="f6d39-291">Scene Understanding sample code for Unity can be found on our [Unity Sample Page](https://github.com/sceneunderstanding-microsoft/unitysample) page.</span></span> <span data-ttu-id="f6d39-292">Diese Anwendung ermöglicht Ihnen die Kommunikation mit Ihrem Gerät und das Rendering der verschiedenen Szenen Objekte, oder Sie können eine serialisierte Szene auf Ihren PC laden und das Verständnis von Szenen ohne Gerät ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="f6d39-292">This application will allow you to communicate with your device and render the various scene objects, or, it will allow you to load a serialized scene on your PC and allow you to experience Scene Understanding without a device.</span></span>

### <a name="where-can-i-get-sample-scenes"></a><span data-ttu-id="f6d39-293">Wo kann ich Beispiel Szenen erhalten?</span><span class="sxs-lookup"><span data-stu-id="f6d39-293">Where can I get sample scenes?</span></span>

<span data-ttu-id="f6d39-294">Wenn Sie über eine HoloLens2 verfügen, können Sie jede Szene speichern, die Sie erfasst haben, indem Sie die Ausgabe von "computeserializedasync" in der Datei speichern und Sie in ihrer eigenen Weise deserialisieren.</span><span class="sxs-lookup"><span data-stu-id="f6d39-294">If you have a HoloLens2 you can save any scene you've captured by saving the output of ComputeSerializedAsync to file and deserializing it at your own convenience.</span></span> 

<span data-ttu-id="f6d39-295">Wenn Sie nicht über ein HoloLens2-Gerät verfügen, aber mit Szenen Verständnis experimentieren möchten, müssen Sie eine vorab erfasste Szene herunterladen.</span><span class="sxs-lookup"><span data-stu-id="f6d39-295">If you do not have a HoloLens2 device but want to play with Scene Understanding you will need to download a pre-captured scene.</span></span> <span data-ttu-id="f6d39-296">Das Beispiel für Szenen Verständnis wird derzeit in serialisierten Szenen geliefert, die Sie herunterladen und in ihrer eigenen Weise verwenden können.</span><span class="sxs-lookup"><span data-stu-id="f6d39-296">The Scene Understanding sample currently ships with serialized scenes that can be downloaded and used at your own convenience.</span></span> <span data-ttu-id="f6d39-297">Sie finden Sie hier:</span><span class="sxs-lookup"><span data-stu-id="f6d39-297">You can find them here:</span></span>

[<span data-ttu-id="f6d39-298">Szenen Einblick in Beispiel Szenen</span><span class="sxs-lookup"><span data-stu-id="f6d39-298">Scene Understanding Sample Scenes</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples/tree/master/Assets/Resources/SerializedScenesForPCPath)

## <a name="see-also"></a><span data-ttu-id="f6d39-299">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="f6d39-299">See also</span></span>

* [<span data-ttu-id="f6d39-300">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="f6d39-300">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="f6d39-301">Grundlegendes zu Szenen</span><span class="sxs-lookup"><span data-stu-id="f6d39-301">Scene understanding</span></span>](scene-understanding.md)
* [<span data-ttu-id="f6d39-302">Unity-Beispiel</span><span class="sxs-lookup"><span data-stu-id="f6d39-302">Unity Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)
