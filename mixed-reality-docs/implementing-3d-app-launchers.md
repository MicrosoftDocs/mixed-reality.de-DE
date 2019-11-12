---
title: Implementieren von 3D-App-launchern (UWP-Apps)
description: Erfahren Sie, wie Sie 3D-App-Launcher und-Logos für Windows Mixed Reality UWP-apps und-Spiele (verteilt durch die Microsoft Store) auf hololens-und immersive-Headsets (VR) erstellen können.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, Logo, Symbol, Modellierung, Start Programm, 3D-Start Programm, Kachel, Live Cube, Deep-Link, secondarytile, Sekundär Kachel, UWP
ms.openlocfilehash: 5d18f699792760c39df4f814bde470fb9f889db7
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926770"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a><span data-ttu-id="7051d-104">Implementieren von 3D-App-launchern (UWP-Apps)</span><span class="sxs-lookup"><span data-stu-id="7051d-104">Implement 3D app launchers (UWP apps)</span></span>

> [!NOTE]
> <span data-ttu-id="7051d-105">Diese Funktion wurde als Teil des 2017 Fall Creators Updates (RS3) für immersive Headsets hinzugefügt und wird von hololens mit dem Windows 10-Update vom April 2018 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="7051d-105">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive headsets and is supported by HoloLens with the  Windows 10 April 2018 Update.</span></span> <span data-ttu-id="7051d-106">Stellen Sie sicher, dass Ihre Anwendung auf eine Version des Windows SDK ist, die größer als oder gleich 10.0.16299 auf immersiven Headsets und 10.0.17125 auf hololens ist.</span><span class="sxs-lookup"><span data-stu-id="7051d-106">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive Headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="7051d-107">Die neuesten Windows SDK finden Sie [hier](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="7051d-107">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="7051d-108">Der [Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) -Startpunkt ist der Ausgangspunkt, an dem Benutzer vor dem Starten von Anwendungen landen.</span><span class="sxs-lookup"><span data-stu-id="7051d-108">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="7051d-109">Beim Erstellen einer UWP-Anwendung für Windows Mixed Reality werden apps standardmäßig als 2D-Slate mit dem Logo Ihrer APP gestartet.</span><span class="sxs-lookup"><span data-stu-id="7051d-109">When creating a UWP application for Windows Mixed Reality, by default, apps are launched as 2D slates with their app's logo.</span></span> <span data-ttu-id="7051d-110">Beim Entwickeln von Umgebungen für Windows Mixed Reality kann optional ein 3D-Start Programm definiert werden, um das standardmäßige 2D-Start Programm für Ihre Anwendung zu überschreiben.</span><span class="sxs-lookup"><span data-stu-id="7051d-110">When developing experiences for Windows Mixed Reality, a 3D launcher can optionally be defined to override the default 2D launcher for your application.</span></span> <span data-ttu-id="7051d-111">Im Allgemeinen werden 3D-Start Programm zum Starten von immersiven Anwendungen empfohlen, die Benutzer aus der Windows Mixed Reality-Startseite ziehen, während das standardmäßige 2D-Start Programm bevorzugt wird, wenn die APP an Ort und Stelle aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="7051d-111">In general, 3D launchers are recommended for launching immersive applications that take users out of the Windows Mixed Reality home whereas the default 2D launcher is preferred when the app is activated in place.</span></span> <span data-ttu-id="7051d-112">Sie können auch einen [3D-Deep-Link (secondarytile)](#3d-deep-links-secondarytiles) als 3D-Start Programm für Inhalte innerhalb einer 2D-UWP-app erstellen.</span><span class="sxs-lookup"><span data-stu-id="7051d-112">You can also create a [3D deep link (secondaryTile)](#3d-deep-links-secondarytiles) as a 3D launcher to content within a 2D UWP app.</span></span>

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="7051d-113">Erstellung eines 3D-App-Start Programms</span><span class="sxs-lookup"><span data-stu-id="7051d-113">3D app launcher creation process</span></span>

<span data-ttu-id="7051d-114">Zum Erstellen eines 3D-App-Start Programms sind drei Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="7051d-114">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="7051d-115">Entwurf und Konzept</span><span class="sxs-lookup"><span data-stu-id="7051d-115">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="7051d-116">Modellieren und exportieren</span><span class="sxs-lookup"><span data-stu-id="7051d-116">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="7051d-117">Integration in Ihre Anwendung (dieser Artikel)</span><span class="sxs-lookup"><span data-stu-id="7051d-117">Integrating it into your application (this article)</span></span>

<span data-ttu-id="7051d-118">3D-Ressourcen, die als Launcher für Ihre Anwendung verwendet werden sollen, sollten mithilfe der [Windows Mixed Reality Authoring Guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) erstellt werden, um die Kompatibilität zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="7051d-118">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="7051d-119">Assets, die diese Erstellungs Spezifikation nicht erfüllen, werden nicht in der Windows Mixed Reality-Startseite gerendert.</span><span class="sxs-lookup"><span data-stu-id="7051d-119">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="7051d-120">Konfigurieren des 3D-Start Programms</span><span class="sxs-lookup"><span data-stu-id="7051d-120">Configuring the 3D launcher</span></span>

<span data-ttu-id="7051d-121">Wenn Sie ein neues Projekt in Visual Studio erstellen, wird eine einfache Standardkachel erstellt, die den Namen und das Logo Ihrer App anzeigt.</span><span class="sxs-lookup"><span data-stu-id="7051d-121">When you create a new project in Visual Studio, it creates a simple default tile that displays your app's name and logo.</span></span> <span data-ttu-id="7051d-122">Um diese 2D-Darstellung durch ein benutzerdefiniertes 3D-Modell zu ersetzen, bearbeiten Sie das App-Manifest der Anwendung so, dass das "mixedrealitymodel"-Element als Teil Ihrer Standard Kachel Definition enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="7051d-122">To replace this 2D representation with a custom 3D model edit the app manifest of your application to include the “MixedRealityModel” element as part of your default tile definition.</span></span> <span data-ttu-id="7051d-123">Um zum 2D-Start Programm zurückzukehren, entfernen Sie einfach die mixedrealitymodel-Definition aus dem Manifest.</span><span class="sxs-lookup"><span data-stu-id="7051d-123">To revert to the 2D launcher just remove the MixedRealityModel definition from the manifest.</span></span>

### <a name="xml"></a><span data-ttu-id="7051d-124">XML</span><span class="sxs-lookup"><span data-stu-id="7051d-124">XML</span></span>

<span data-ttu-id="7051d-125">Suchen Sie zuerst das App-Paket Manifest in Ihrem aktuellen Projekt.</span><span class="sxs-lookup"><span data-stu-id="7051d-125">First, locate the app package manifest in your current project.</span></span> <span data-ttu-id="7051d-126">Standardmäßig wird das Manifest "Package. appxmanifest" genannt.</span><span class="sxs-lookup"><span data-stu-id="7051d-126">By default, the manifest will be named Package.appxmanifest.</span></span> <span data-ttu-id="7051d-127">Wenn Sie Visual Studio verwenden, klicken Sie mit der rechten Maustaste auf das Manifest in Ihrem projektmappenviewer, und wählen Sie **Quelle anzeigen** , um den XML-Code zum Bearbeiten zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="7051d-127">If you're using Visual Studio, then right-click the manifest in your solution viewer and select **View source** to open the xml for editing.</span></span> 

<span data-ttu-id="7051d-128">Fügen Sie am Anfang des Manifests das uap5-Schema hinzu, und fügen Sie es als Ignorable-Namespace ein:</span><span class="sxs-lookup"><span data-stu-id="7051d-128">At the top of the manifest, add the uap5 schema and include it as an ignorable namespace:</span></span>

```xml
<Package xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="https://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

<span data-ttu-id="7051d-129">Geben Sie als nächstes "mixedrealitymodel" in der Standard Kachel für Ihre Anwendung an:</span><span class="sxs-lookup"><span data-stu-id="7051d-129">Next specify the "MixedRealityModel" in the default tile for your application:</span></span>

```xml
<Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="ExampleApp.App">
      <uap:VisualElements
        DisplayName="ExampleApp"
        Square150x150Logo="Assets\Logo.png"
        Square44x44Logo="Assets\SmallLogo.png"
        Description="ExampleApp"
        BackgroundColor="#464646">
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb" />
        </uap:DefaultTile>
        <uap:SplashScreen Image="Assets\SplashScreen.png" />
      </uap:VisualElements>
    </Application>
</Applications>
```

<span data-ttu-id="7051d-130">Die mixedrealitymodel-Elemente akzeptieren einen Dateipfad, der auf ein 3D-Asset verweist, das in Ihrem App-Paket gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="7051d-130">The MixedRealityModel elements accepts a file path pointing to a 3D asset stored in your app package.</span></span> <span data-ttu-id="7051d-131">Zurzeit werden nur 3D-Modelle unter Verwendung des. GLB-Datei Formats bereitgestellt, die für die [Windows Mixed Reality 3D Asset Authoring-Anweisungen](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="7051d-131">Currently only 3D models delivered using the .glb file format and authored against the [Windows Mixed Reality 3D asset authoring instructions](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) are supported.</span></span> <span data-ttu-id="7051d-132">Assets müssen im App-Paket gespeichert werden, und die Animation wird derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="7051d-132">Assets must be stored in the app package and animation is not currently supported.</span></span> <span data-ttu-id="7051d-133">Wenn der Parameter "Path" leer gelassen wird, zeigt Windows das 2D-Slate anstelle des 3D-Start Programms an.</span><span class="sxs-lookup"><span data-stu-id="7051d-133">If the “Path” parameter is left blank Windows will show the 2D slate instead of the 3D launcher.</span></span> <span data-ttu-id="7051d-134">**Hinweis:** das. GLB-Asset muss in ihren Buildeinstellungen als "Inhalt" gekennzeichnet werden, bevor Sie Ihre APP erstellen und ausführen.</span><span class="sxs-lookup"><span data-stu-id="7051d-134">**Note:** the .glb asset must be marked as "Content" in your build settings before building and running your app.</span></span>


<span data-ttu-id="7051d-135">![die. GLB-Datei im Projektmappen-Explorer auswählen und den Abschnitt Eigenschaften verwenden, um Sie in den Buildeinstellungen als "Inhalt" zu markieren](images/buildsetting-content-300px.png)</span><span class="sxs-lookup"><span data-stu-id="7051d-135">![Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings](images/buildsetting-content-300px.png)</span></span><br>
<span data-ttu-id="7051d-136">*Wählen Sie im Projektmappen-Explorer die GLB-Datei aus, und markieren Sie Sie mithilfe des Abschnitts Eigenschaften als "Inhalt" in den Buildeinstellungen.*</span><span class="sxs-lookup"><span data-stu-id="7051d-136">*Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings*</span></span>

### <a name="bounding-box"></a><span data-ttu-id="7051d-137">Begrenzungsrahmen</span><span class="sxs-lookup"><span data-stu-id="7051d-137">Bounding box</span></span>

<span data-ttu-id="7051d-138">Ein Begrenzungs Rahmen kann verwendet werden, um optional einen zusätzlichen Pufferbereich um das Objekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="7051d-138">A bounding box can be used to optionally add an additional buffer region around the object.</span></span> <span data-ttu-id="7051d-139">Das umgebende Feld wird mithilfe eines Mittelpunkts und der Blöcke angegeben, die den Abstand zwischen der Mitte des umgebenden Felds und seinen Rändern entlang der Achse angeben.</span><span class="sxs-lookup"><span data-stu-id="7051d-139">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="7051d-140">Die Einheiten für das Begrenzungsfeld können 1 Einheit = 1 Meter zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="7051d-140">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="7051d-141">Wenn kein Begrenzungsfeld angegeben wird, wird eines automatisch an das Mesh des Objekts angepasst.</span><span class="sxs-lookup"><span data-stu-id="7051d-141">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="7051d-142">Wenn das angegebene Begrenzungsfeld kleiner als das Modell ist, wird es in die Größe geändert, damit es an das Mesh angepasst ist.</span><span class="sxs-lookup"><span data-stu-id="7051d-142">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

<span data-ttu-id="7051d-143">Die Unterstützung für das Begrenzungsfeld Attribut wird mit dem Windows-Update-Update als Eigenschaft für das mixedrealitymodel-Element erreicht.</span><span class="sxs-lookup"><span data-stu-id="7051d-143">Support for the bounding box attribute will come with the Windows RS4 update as a property on the MixedRealityModel element.</span></span> <span data-ttu-id="7051d-144">Fügen Sie zum Definieren eines Begrenzungs Rahmens zuerst am oberen Rand des App-Manifests das uap6-Schema hinzu, und fügen Sie es als Ignorable Namespaces ein:</span><span class="sxs-lookup"><span data-stu-id="7051d-144">To define a bounding box first at the top of the app manifest add the uap6 schema and include it them as ignorable namespaces:</span></span>

```xml
<Package xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="https://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="https://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
<span data-ttu-id="7051d-145">Legen Sie als nächstes auf dem mixedrealitymodel die spatialboundingbox-Eigenschaft auf das Begrenzungsfeld fest:</span><span class="sxs-lookup"><span data-stu-id="7051d-145">Next, on the MixedRealityModel set the SpatialBoundingBox property to define the bounding box:</span></span> 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a><span data-ttu-id="7051d-146">Verwenden von Unity</span><span class="sxs-lookup"><span data-stu-id="7051d-146">Using Unity</span></span>

<span data-ttu-id="7051d-147">Beim Arbeiten mit Unity muss das Projekt in Visual Studio erstellt und geöffnet werden, bevor das App-Manifest bearbeitet werden kann.</span><span class="sxs-lookup"><span data-stu-id="7051d-147">When working with Unity the project must be built and opened in Visual Studio before the App Manifest can be edited.</span></span> 

>[!NOTE]
><span data-ttu-id="7051d-148">Das 3D-Start Programm muss im Manifest neu definiert werden, wenn eine neue Visual Studio-Projekt Mappe aus Unity aufgebaut und bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="7051d-148">The 3D launcher must be redefined in the manifest when building and deploying a new Visual Studio solution from Unity.</span></span>

## <a name="3d-deep-links-secondarytiles"></a><span data-ttu-id="7051d-149">3D Deep-Links (secondarytiles)</span><span class="sxs-lookup"><span data-stu-id="7051d-149">3D deep links (secondaryTiles)</span></span>

> [!NOTE]
> <span data-ttu-id="7051d-150">Diese Funktion wurde als Teil des 2017 Fall Creators Update (RS3) für immersive (VR)-Headsets und im Rahmen des Updates vom April 2018 (RS4) für hololens hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="7051d-150">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive (VR) headsets and as part of the April 2018 Update (RS4) for HoloLens.</span></span> <span data-ttu-id="7051d-151">Stellen Sie sicher, dass Ihre Anwendung auf eine Version des Windows SDK ist, das größer als oder gleich 10.0.16299 on immersive (VR)-Headsets und 10.0.17125 auf hololens ist.</span><span class="sxs-lookup"><span data-stu-id="7051d-151">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive (VR) headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="7051d-152">Die neuesten Windows SDK finden Sie [hier](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="7051d-152">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

>[!IMPORTANT]
><span data-ttu-id="7051d-153">3D-Deep-Links (secondarytiles) funktionieren nur mit 2D-UWP-apps.</span><span class="sxs-lookup"><span data-stu-id="7051d-153">3D deep links (secondaryTiles) only work with 2D UWP apps.</span></span> <span data-ttu-id="7051d-154">Sie können jedoch ein [3D-App-](implementing-3d-app-launchers.md) Startfeld erstellen, um eine exklusive App aus dem Windows Mixed Reality-Start Programm zu starten.</span><span class="sxs-lookup"><span data-stu-id="7051d-154">You can, however, create a [3D app launcher](implementing-3d-app-launchers.md) to launch an exclusive app from the Windows Mixed Reality home.</span></span>

<span data-ttu-id="7051d-155">Ihre 2D-Anwendungen können für die gemischte Windows-Realität erweitert werden, indem Sie die Möglichkeit zum Platzieren von 3D-Modellen aus Ihrer APP als tiefe Links zu Inhalten in ihrer 2D-app hinzufügen [, wie z](navigating-the-windows-mixed-reality-home.md) [. b. zwei sekundäre Kacheln](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) auf dem Windows-Start. stehen.</span><span class="sxs-lookup"><span data-stu-id="7051d-155">Your 2D applications can be enhanced for Windows Mixed Reality by adding the ability to place 3D models from your app into the [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) as deep links to content within your 2D app, just like [2D secondary tiles](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) on the Windows Start menu.</span></span> <span data-ttu-id="7051d-156">Sie können z. b. 360 °-photosphären erstellen, die direkt in eine 360 °-Foto-Viewer-App verweisen, oder Benutzern das Platzieren von 3D-Inhalten aus einer Sammlung von Objekten ermöglichen, die eine Detailseite zum Autor öffnet.</span><span class="sxs-lookup"><span data-stu-id="7051d-156">For example, you can create 360° photospheres that link directly into a 360° photo viewer app, or let users place 3D content from a collection of assets that opens a details page about the author.</span></span> <span data-ttu-id="7051d-157">Dies sind nur einige Möglichkeiten, die Funktionalität Ihrer 2D-Anwendung mit 3D-Inhalten zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="7051d-157">These are just a couple ways to expand the functionality of your 2D application with 3D content.</span></span>

### <a name="creating-a-3d-secondarytile"></a><span data-ttu-id="7051d-158">Erstellen einer 3D-"secondarytile"</span><span class="sxs-lookup"><span data-stu-id="7051d-158">Creating a 3D “secondaryTile”</span></span>

<span data-ttu-id="7051d-159">Sie können 3D-Inhalte mithilfe von "secondarytiles" aus der Anwendung platzieren, indem Sie zum Zeitpunkt der Erstellung ein gemischtes Reality-Modell definieren.</span><span class="sxs-lookup"><span data-stu-id="7051d-159">You can place 3D content from your application using “secondaryTiles” by defining a mixed reality model at creation time.</span></span> <span data-ttu-id="7051d-160">Gemischte Reality-Modelle werden erstellt, indem auf ein 3D-Medienobjekt in Ihrem App-Paket verwiesen und optional ein Begrenzungsfeld definiert wird.</span><span class="sxs-lookup"><span data-stu-id="7051d-160">Mixed reality models are created by referencing a 3D asset in your app package and optionally defining a bounding box.</span></span> 

> [!NOTE]
> <span data-ttu-id="7051d-161">Das Erstellen von "secondarytiles" aus einer exklusiven Ansicht wird derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="7051d-161">Creating “secondaryTiles” from within an exclusive view is not currently supported.</span></span>

```cs
using Windows.UI.StartScreen;
using Windows.Foundation.Numerics;
using Windows.Perception.Spatial;

// Initialize the tile
SecondaryTile tile = new SecondaryTile("myTileId")
{
    DisplayName = "My Tile",
    Arguments = "myArgs"
};

tile.VisualElements.Square150x150Logo = new Uri("ms-appx:///Assets/MyTile/Square150x150Logo.png");

//Assign 3D model (only ms-appx and ms-appdata are allowed)
TileMixedRealityModel model = tile.VisualElements.MixedRealityModel;
model.Uri = new Uri("ms-appx:///Assets/MyTile/MixedRealityModel.glb");
model.ActivationBehavior = TileMixedRealityModelActivationBehavior.Default;
model.BoundingBox = new SpatialBoundingBox
{
    Center = new Vector3 { X = 1, Y = 0, Z = 0 },
    Extents = new Vector3 { X = 3, Y = 5, Z = 4 }
};

// And place it
await tile.RequestCreateAsync();
```

### <a name="bounding-box"></a><span data-ttu-id="7051d-162">Begrenzungsrahmen</span><span class="sxs-lookup"><span data-stu-id="7051d-162">Bounding box</span></span>

<span data-ttu-id="7051d-163">Zum Hinzufügen eines zusätzlichen Puffer Bereichs um das Objekt kann ein Begrenzungs Rahmen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7051d-163">A bounding box can be used to add an additional buffer region around the object.</span></span> <span data-ttu-id="7051d-164">Das umgebende Feld wird mithilfe eines Mittelpunkts und der Blöcke angegeben, die den Abstand zwischen der Mitte des umgebenden Felds und seinen Rändern entlang der Achse angeben.</span><span class="sxs-lookup"><span data-stu-id="7051d-164">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="7051d-165">Die Einheiten für das Begrenzungsfeld können 1 Einheit = 1 Meter zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="7051d-165">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="7051d-166">Wenn kein Begrenzungsfeld angegeben wird, wird eines automatisch an das Mesh des Objekts angepasst.</span><span class="sxs-lookup"><span data-stu-id="7051d-166">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="7051d-167">Wenn das angegebene Begrenzungsfeld kleiner als das Modell ist, wird es in die Größe geändert, damit es an das Mesh angepasst ist.</span><span class="sxs-lookup"><span data-stu-id="7051d-167">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="7051d-168">Aktivierungs Verhalten</span><span class="sxs-lookup"><span data-stu-id="7051d-168">Activation behavior</span></span>

> [!NOTE]
> <span data-ttu-id="7051d-169">Diese Funktion wird ab dem Windows-Update "RS4" unterstützt.</span><span class="sxs-lookup"><span data-stu-id="7051d-169">This feature will be supported as of the Windows RS4 update.</span></span> <span data-ttu-id="7051d-170">Stellen Sie sicher, dass Ihre Anwendung auf eine Version der Windows SDK, die größer als oder gleich 10.0.17125 ist, wenn Sie beabsichtigen, dieses Feature zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="7051d-170">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.17125 if you plan to use this feature</span></span>

<span data-ttu-id="7051d-171">Sie können das Aktivierungs Verhalten für eine 3D-secondarytile definieren, um zu steuern, wie Sie reagiert, wenn ein Benutzer Sie auswählt.</span><span class="sxs-lookup"><span data-stu-id="7051d-171">You can define the activation behavior for a 3D secondaryTile to control how it reacts when a user selects it.</span></span> <span data-ttu-id="7051d-172">Dies kann verwendet werden, um 3D-Objekte in die gemischte Realität zu platzieren, die rein informativ oder dekorativ sind.</span><span class="sxs-lookup"><span data-stu-id="7051d-172">This can be used to place 3D objects in the Mixed Reality home that are purely informative or decorative.</span></span> <span data-ttu-id="7051d-173">Die folgenden Aktivierungs Verhaltenstypen werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="7051d-173">The following activation behavior types are supported:</span></span>
1. <span data-ttu-id="7051d-174">Standard: Wenn ein Benutzer die 3D-secondarytile auswählt, wird die App aktiviert.</span><span class="sxs-lookup"><span data-stu-id="7051d-174">Default: When a user selects the 3D secondaryTile the app is activated</span></span>
2. <span data-ttu-id="7051d-175">Keine: Wenn die Benutzer die 3D-secondarytile auswählen, geschieht nichts, und die APP ist nicht aktiviert.</span><span class="sxs-lookup"><span data-stu-id="7051d-175">None: When the users selects the 3D secondaryTile nothing happens and the app is not activated.</span></span>

### <a name="obtaining-and-updating-an-existing-secondarytile"></a><span data-ttu-id="7051d-176">Abrufen und Aktualisieren einer vorhandenen "secondarytile"</span><span class="sxs-lookup"><span data-stu-id="7051d-176">Obtaining and updating an existing “secondaryTile”</span></span>

<span data-ttu-id="7051d-177">Entwickler können eine Liste Ihrer vorhandenen sekundären Kacheln zurückerhalten, einschließlich der Eigenschaften, die Sie zuvor angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="7051d-177">Developers can get back a list of their existing secondary tiles, which includes the properties that they previously specified.</span></span> <span data-ttu-id="7051d-178">Sie können die Eigenschaften auch aktualisieren, indem Sie den Wert ändern und dann UpdateAsync () aufrufen.</span><span class="sxs-lookup"><span data-stu-id="7051d-178">They can also update the properties by changing the value and then calling UpdateAsync().</span></span>

```cs
// Grab the existing secondary tile
SecondaryTile tile = (await SecondaryTile.FindAllAsync()).First();

Uri updatedUri = new Uri("ms-appdata:///local/MixedRealityUpdated.glb");

// See if the model needs updating
if (!tile.VisualElements.MixedRealityModel.Uri.Equals(updatedUri))
{
    // Update it
    tile.VisualElements.MixedRealityModel.Uri = updatedUri;

    // And apply the changes
    await tile.UpdateAsync();
}
```

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a><span data-ttu-id="7051d-179">Überprüfen, ob der Benutzer in der gemischten Realität von Windows ist</span><span class="sxs-lookup"><span data-stu-id="7051d-179">Checking that the user is in Windows Mixed Reality</span></span>

<span data-ttu-id="7051d-180">3D Deep-Links (secondarytiles) können nur erstellt werden, während die Ansicht in einem Windows Mixed Reality-Headset angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="7051d-180">3D deep links (secondaryTiles) can only be created while the view is being displayed in a Windows Mixed Reality headset.</span></span> <span data-ttu-id="7051d-181">Wenn Ihre Ansicht nicht in einem Windows Mixed Reality-Headset angezeigt wird, sollten Sie diese ordnungsgemäß behandeln, indem Sie entweder den Einstiegspunkt ausblenden oder eine Fehlermeldung anzeigen.</span><span class="sxs-lookup"><span data-stu-id="7051d-181">When your view isn't being presented in a Windows Mixed Reality headset we recommend gracefully handling this by either hiding the entry point or showing an error message.</span></span> <span data-ttu-id="7051d-182">Sie können dies überprüfen, indem Sie [iscurrentviewpresentedonholographic ()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)Abfragen.</span><span class="sxs-lookup"><span data-stu-id="7051d-182">You can check this by querying [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span></span>

## <a name="tile-notifications"></a><span data-ttu-id="7051d-183">Kachelbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="7051d-183">Tile notifications</span></span>

<span data-ttu-id="7051d-184">Bei Kachel Benachrichtigungen wird das Senden eines Updates mit einem 3D-Medienobjekt derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="7051d-184">Tile notifications do not currently support sending an update with a 3D asset.</span></span> <span data-ttu-id="7051d-185">Dies bedeutet, dass Entwickler nicht die folgenden Aktionen ausführen können:</span><span class="sxs-lookup"><span data-stu-id="7051d-185">This means that developers will not be able to do the following</span></span>
* <span data-ttu-id="7051d-186">Pushbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="7051d-186">Push Notifications</span></span>
* <span data-ttu-id="7051d-187">Periodische Abruf Vorgänge</span><span class="sxs-lookup"><span data-stu-id="7051d-187">Periodic Polling</span></span>
* <span data-ttu-id="7051d-188">Geplante Benachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="7051d-188">Scheduled Notifications</span></span>

<span data-ttu-id="7051d-189">Weitere Informationen zu den anderen Kacheln Features und Attributen und deren Verwendung für 2D-Kacheln finden Sie in der [Dokumentation zu Kacheln für UWP-apps](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span><span class="sxs-lookup"><span data-stu-id="7051d-189">For more information on the other tiles features and attributes and how they are used for 2D tiles refer to the [Tiles for UWP Apps documentation](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span></span>

## <a name="see-also"></a><span data-ttu-id="7051d-190">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="7051d-190">See also</span></span>

* <span data-ttu-id="7051d-191">[Gemischtes Reality-Modell Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) mit einem 3D-App-Start Programm.</span><span class="sxs-lookup"><span data-stu-id="7051d-191">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="7051d-192">Entwurfsanleitung für 3D-App-Startprogramm</span><span class="sxs-lookup"><span data-stu-id="7051d-192">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="7051d-193">Erstellen von 3D-Modellen für die Verwendung in der Windows Mixed Reality-Startseite</span><span class="sxs-lookup"><span data-stu-id="7051d-193">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="7051d-194">Implementieren von 3D-App-launchern (Win32-Apps)</span><span class="sxs-lookup"><span data-stu-id="7051d-194">Implementing 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
* [<span data-ttu-id="7051d-195">Navigieren auf der Startseite von Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="7051d-195">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
