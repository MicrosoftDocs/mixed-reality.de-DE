---
title: Implementieren von 3D app-startfeldern von (UWP-apps)
description: 'Vorgehensweise: Erstellen von 3D app-startfeldern und Logos für die Windows Mixed Reality-UWP-apps und Spiele (verteilt über den Microsoft Store), HoloLens und immersive Headsets von (VR).'
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, Logo, Symbol, Modellierung, Startprogramm, 3D Startprogramm, Kachel, live-Cube, deep-Link, "secondarytile", sekundären Kachel, UWP
ms.openlocfilehash: 4a8d4a696ff6ef19d7332b20580f1f5ee67bf045
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604855"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a><span data-ttu-id="05f99-104">Implementieren von 3D app-startfeldern von (UWP-apps)</span><span class="sxs-lookup"><span data-stu-id="05f99-104">Implement 3D app launchers (UWP apps)</span></span>

> [!NOTE]
> <span data-ttu-id="05f99-105">Dieses Feature wurde als Teil des 2017 Fall Creators Update (RS3) für immersive Headsets hinzugefügt und wird unterstützt von HoloLens mit dem Windows 10 April 2018 aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="05f99-105">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive headsets and is supported by HoloLens with the  Windows 10 April 2018 Update.</span></span> <span data-ttu-id="05f99-106">Stellen Sie sicher, dass Ihre Anwendung eine Version des Windows SDK größer als oder gleich 10.0.16299 für immersive Headsets und 10.0.17125 für HoloLens entwickelt wird.</span><span class="sxs-lookup"><span data-stu-id="05f99-106">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive Headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="05f99-107">Sie finden das neueste Windows SDK [hier](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="05f99-107">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="05f99-108">Die [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) ist der Ausgangspunkt, in denen Benutzer weitergeleitet, vor dem Starten von Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="05f99-108">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="05f99-109">Beim Erstellen einer UWP-Anwendung für Windows Mixed Reality, standardmäßig werden apps als 2D Slate-PCs mit ihr app Logo gestartet.</span><span class="sxs-lookup"><span data-stu-id="05f99-109">When creating a UWP application for Windows Mixed Reality, by default, apps are launched as 2D slates with their app's logo.</span></span> <span data-ttu-id="05f99-110">Beim Entwickeln von Benutzeroberflächen für Windows Mixed Reality kann 3D Startprogramm optional definiert werden, um das Standard-2D-Startprogramm für Ihre Anwendung zu überschreiben.</span><span class="sxs-lookup"><span data-stu-id="05f99-110">When developing experiences for Windows Mixed Reality, a 3D launcher can optionally be defined to override the default 2D launcher for your application.</span></span> <span data-ttu-id="05f99-111">3D Startprogramme sind im Allgemeinen empfohlen, für den Start von immersiver Anwendungen, die für Benutzer, die Windows Mixed Reality Startseite zu nutzen, während das Standard-2D-Startprogramm bevorzugt wird, wenn die app direkt aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="05f99-111">In general, 3D launchers are recommended for launching immersive applications that take users out of the Windows Mixed Reality home whereas the default 2D launcher is preferred when the app is activated in place.</span></span> <span data-ttu-id="05f99-112">Sie können auch erstellen, eine [3D deep-Link ("secondarytile")](#3d-deep-links-secondarytiles) als 3D Startprogramm zu Inhalten innerhalb einer Direct2D-UWP-app.</span><span class="sxs-lookup"><span data-stu-id="05f99-112">You can also create a [3D deep link (secondaryTile)](#3d-deep-links-secondarytiles) as a 3D launcher to content within a 2D UWP app.</span></span>

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="05f99-113">3D app-Startprogramm-Erstellungsprozess</span><span class="sxs-lookup"><span data-stu-id="05f99-113">3D app launcher creation process</span></span>

<span data-ttu-id="05f99-114">Es gibt 3 Schritte zum Erstellen einer-3D-app-Startfeld:</span><span class="sxs-lookup"><span data-stu-id="05f99-114">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="05f99-115">Entwerfen und concepting</span><span class="sxs-lookup"><span data-stu-id="05f99-115">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="05f99-116">Modellieren und exportieren</span><span class="sxs-lookup"><span data-stu-id="05f99-116">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="05f99-117">Die Integration in Ihre Anwendung (in diesem Artikel)</span><span class="sxs-lookup"><span data-stu-id="05f99-117">Integrating it into your application (this article)</span></span>

<span data-ttu-id="05f99-118">3D-Objekte verwendet werden, wie mithilfe Startprogramme für Ihre Anwendung erstellt werden soll die [Windows Mixed Reality Erstellen von Richtlinien](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) um die Kompatibilität sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="05f99-118">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="05f99-119">Ressourcen, die diese Spezifikation authoring einhalten werden nicht in die Windows Mixed Reality home gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="05f99-119">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="05f99-120">Konfigurieren das Startprogramm 3D</span><span class="sxs-lookup"><span data-stu-id="05f99-120">Configuring the 3D launcher</span></span>

<span data-ttu-id="05f99-121">Wenn Sie ein neues Projekt in Visual Studio erstellen, wird eine einfache Standardkachel erstellt, die den Namen und das Logo Ihrer App anzeigt.</span><span class="sxs-lookup"><span data-stu-id="05f99-121">When you create a new project in Visual Studio, it creates a simple default tile that displays your app's name and logo.</span></span> <span data-ttu-id="05f99-122">Bearbeiten zum Ersetzen dieses 2D Darstellung mit einem benutzerdefinierten 3D-Modell der app-Manifest der Anwendung, um das Element "MixedRealityModel" als Teil Ihrer Kachel-Standarddefinition enthalten.</span><span class="sxs-lookup"><span data-stu-id="05f99-122">To replace this 2D representation with a custom 3D model edit the app manifest of your application to include the “MixedRealityModel” element as part of your default tile definition.</span></span> <span data-ttu-id="05f99-123">Um die 2D wiederherzustellen Startprogramm entfernen Sie einfach die MixedRealityModel-Definition aus dem Manifest.</span><span class="sxs-lookup"><span data-stu-id="05f99-123">To revert to the 2D launcher just remove the MixedRealityModel definition from the manifest.</span></span>

### <a name="xml"></a><span data-ttu-id="05f99-124">XML</span><span class="sxs-lookup"><span data-stu-id="05f99-124">XML</span></span>

<span data-ttu-id="05f99-125">Suchen Sie zunächst die app-Paketmanifest in Ihrem aktuellen Projekt.</span><span class="sxs-lookup"><span data-stu-id="05f99-125">First, locate the app package manifest in your current project.</span></span> <span data-ttu-id="05f99-126">Standardmäßig wird das Manifest "Package.appxmanifest" benannt.</span><span class="sxs-lookup"><span data-stu-id="05f99-126">By default, the manifest will be named Package.appxmanifest.</span></span> <span data-ttu-id="05f99-127">Wenn Sie Visual Studio verwenden, klicken Sie dann mit der rechten Maustaste in des Manifests in einem Viewer für die Projektmappe, und wählen **Quelltext anzeigen** zu den XML-Code für die Bearbeitung zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="05f99-127">If you're using Visual Studio, then right-click the manifest in your solution viewer and select **View source** to open the xml for editing.</span></span> 

<span data-ttu-id="05f99-128">Klicken Sie am oberen Rand des Manifests fügen Sie das Schema uap5, und fügen Sie es als ein ignorierbares Namespace:</span><span class="sxs-lookup"><span data-stu-id="05f99-128">At the top of the manifest, add the uap5 schema and include it as an ignorable namespace:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

<span data-ttu-id="05f99-129">Als Nächstes geben Sie die "MixedRealityModel" in der standardkachel für Ihre Anwendung:</span><span class="sxs-lookup"><span data-stu-id="05f99-129">Next specify the "MixedRealityModel" in the default tile for your application:</span></span>

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

<span data-ttu-id="05f99-130">Die Elemente MixedRealityModel akzeptiert einen Dateipfad verweist auf ein 3D-Objekt Medienobjekt im app-Paket gespeichert.</span><span class="sxs-lookup"><span data-stu-id="05f99-130">The MixedRealityModel elements accepts a file path pointing to a 3D asset stored in your app package.</span></span> <span data-ttu-id="05f99-131">Derzeit nur 3D-Modelle übermittelt das .glb Dateiformat, und erstellt anhand der [Windows Mixed Reality-3D-Asset Erstellen von Anweisungen](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="05f99-131">Currently only 3D models delivered using the .glb file format and authored against the [Windows Mixed Reality 3D asset authoring instructions](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) are supported.</span></span> <span data-ttu-id="05f99-132">Ressourcen müssen in das app-Paket gespeichert werden und die Animation wird derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="05f99-132">Assets must be stored in the app package and animation is not currently supported.</span></span> <span data-ttu-id="05f99-133">Der Parameter "Path" leer gelassen wird Windows 2D slates statt das Startprogramm 3D angezeigt.</span><span class="sxs-lookup"><span data-stu-id="05f99-133">If the “Path” parameter is left blank Windows will show the 2D slate instead of the 3D launcher.</span></span> <span data-ttu-id="05f99-134">**Hinweis:** .glb Medienobjekt muss markiert werden als "Inhalt" in den Buildeinstellungen vor dem Erstellen und Ausführen Ihrer app.</span><span class="sxs-lookup"><span data-stu-id="05f99-134">**Note:** the .glb asset must be marked as "Content" in your build settings before building and running your app.</span></span>


<span data-ttu-id="05f99-135">![Wählen Sie die .glb im Projektmappen-Explorer, und verwenden Sie den Abschnitt "Properties" als "Inhalt" in den Buildeinstellungen kennzeichnen](images/buildsetting-content-300px.png)</span><span class="sxs-lookup"><span data-stu-id="05f99-135">![Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings](images/buildsetting-content-300px.png)</span></span><br>
<span data-ttu-id="05f99-136">*Wählen Sie die .glb im Projektmappen-Explorer, und verwenden Sie den Abschnitt "Properties" als "Inhalt" in den Buildeinstellungen kennzeichnen*</span><span class="sxs-lookup"><span data-stu-id="05f99-136">*Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings*</span></span>

### <a name="bounding-box"></a><span data-ttu-id="05f99-137">Begrenzungsrahmen</span><span class="sxs-lookup"><span data-stu-id="05f99-137">Bounding box</span></span>

<span data-ttu-id="05f99-138">Ein umgebendes Feld kann verwendet werden, um optional eine zusätzlicher Puffer-Region, um das Objekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="05f99-138">A bounding box can be used to optionally add an additional buffer region around the object.</span></span> <span data-ttu-id="05f99-139">Das umgebende Feld wird angegeben, mit einem Mittelpunkt sowie von Blöcken, die den Abstand von der Mitte des umgebenden Felds an seinen Rändern an jeder Achse angeben.</span><span class="sxs-lookup"><span data-stu-id="05f99-139">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="05f99-140">Einheiten für das umgebende Feld zugeordnet werden können, auf 1 Einheit = 1 Meter Umkreis um.</span><span class="sxs-lookup"><span data-stu-id="05f99-140">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="05f99-141">Wenn ein umgebendes Feld nicht angegeben wird wird dann eine automatisch an das Netz des Objekts eingefügt werden.</span><span class="sxs-lookup"><span data-stu-id="05f99-141">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="05f99-142">Wenn das angegebene umgebende Feld kleiner ist als das Modell wird diese Größe entsprechend angepasst Mesh.</span><span class="sxs-lookup"><span data-stu-id="05f99-142">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

<span data-ttu-id="05f99-143">Unterstützung für das umgebende Feld-Attribut kommen mit dem Windows-Version RS4-Update als Eigenschaft für das Element MixedRealityModel.</span><span class="sxs-lookup"><span data-stu-id="05f99-143">Support for the bounding box attribute will come with the Windows RS4 update as a property on the MixedRealityModel element.</span></span> <span data-ttu-id="05f99-144">Zuerst definieren Sie ein umgebendes Feld am oberen Rand der app Manifest, fügen Sie das Schema uap6, und fügen Sie sie diese als ignorable-Namespaces:</span><span class="sxs-lookup"><span data-stu-id="05f99-144">To define a bounding box first at the top of the app manifest add the uap6 schema and include it them as ignorable namespaces:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
<span data-ttu-id="05f99-145">Legen Sie anschließend auf die MixedRealityModel SpatialBoundingBox Eigenschaft, die das umgebende Feld definiert:</span><span class="sxs-lookup"><span data-stu-id="05f99-145">Next, on the MixedRealityModel set the SpatialBoundingBox property to define the bounding box:</span></span> 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a><span data-ttu-id="05f99-146">Mithilfe von Unity</span><span class="sxs-lookup"><span data-stu-id="05f99-146">Using Unity</span></span>

<span data-ttu-id="05f99-147">Bei der Arbeit mit Unity wird das Projekt muss erstellt und in Visual Studio geöffnet werden, bevor App-Manifest bearbeitet werden können.</span><span class="sxs-lookup"><span data-stu-id="05f99-147">When working with Unity the project must be built and opened in Visual Studio before the App Manifest can be edited.</span></span> 

>[!NOTE]
><span data-ttu-id="05f99-148">Das Startprogramm 3D muss im Manifest beim Erstellen und Bereitstellen einer neuen Visual Studio-Projektmappe von Unity neu definiert werden.</span><span class="sxs-lookup"><span data-stu-id="05f99-148">The 3D launcher must be redefined in the manifest when building and deploying a new Visual Studio solution from Unity.</span></span>

## <a name="3d-deep-links-secondarytiles"></a><span data-ttu-id="05f99-149">3D Deep-links (SecondaryTiles)</span><span class="sxs-lookup"><span data-stu-id="05f99-149">3D deep links (secondaryTiles)</span></span>

> [!NOTE]
> <span data-ttu-id="05f99-150">Dieses Feature wurde hinzugefügt, als Teil der 2017 Fall Creators Update (RS3) für immersive Headsets von (VR) und als Teil von April 2018 Update (RS4) für HoloLens.</span><span class="sxs-lookup"><span data-stu-id="05f99-150">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive (VR) headsets and as part of the April 2018 Update (RS4) for HoloLens.</span></span> <span data-ttu-id="05f99-151">Stellen Sie sicher, dass Ihre Anwendung eine Version des Windows SDK größer als oder gleich 10.0.16299 für immersive Headsets von (VR) und 10.0.17125 für HoloLens entwickelt wird.</span><span class="sxs-lookup"><span data-stu-id="05f99-151">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive (VR) headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="05f99-152">Sie finden das neueste Windows SDK [hier](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="05f99-152">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

>[!IMPORTANT]
><span data-ttu-id="05f99-153">3D deep-Links (SecondaryTiles) funktionieren nur mit Direct2D UWP-apps.</span><span class="sxs-lookup"><span data-stu-id="05f99-153">3D deep links (secondaryTiles) only work with 2D UWP apps.</span></span> <span data-ttu-id="05f99-154">Sie können jedoch erstellen, eine [-3D-app-Startfeld](implementing-3d-app-launchers.md) um eine exklusive app über die Windows Mixed Reality home zu starten.</span><span class="sxs-lookup"><span data-stu-id="05f99-154">You can, however, create a [3D app launcher](implementing-3d-app-launchers.md) to launch an exclusive app from the Windows Mixed Reality home.</span></span>

<span data-ttu-id="05f99-155">2D Anwendungen für Windows Mixed Reality verbessert werden können, durch Hinzufügen der Funktion zum Platzieren von 3D-Modellen aus Ihrer app in der [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) als deep-Links zu Inhalten innerhalb Ihrer Direct2D-app, wie [2D sekundäre Datenbank Kacheln](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) über das Windows-Startmenü.</span><span class="sxs-lookup"><span data-stu-id="05f99-155">Your 2D applications can be enhanced for Windows Mixed Reality by adding the ability to place 3D models from your app into the [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) as deep links to content within your 2D app, just like [2D secondary tiles](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) on the Windows Start menu.</span></span> <span data-ttu-id="05f99-156">Beispielsweise können Sie 360° Photospheres erstellen, die direkt in eine 360° Foto-Viewer-app zu verknüpfen, oder lassen Sie die Benutzer-3D-Inhalte aus einer Auflistung von Ressourcen zu platzieren, die eine Detailseite zum Autor wird geöffnet.</span><span class="sxs-lookup"><span data-stu-id="05f99-156">For example, you can create 360° photospheres that link directly into a 360° photo viewer app, or let users place 3D content from a collection of assets that opens a details page about the author.</span></span> <span data-ttu-id="05f99-157">Hierbei handelt es sich um ein paar Möglichkeiten zum Erweitern der Funktionalität der Anwendung und einer 3D-Inhalt 2D.</span><span class="sxs-lookup"><span data-stu-id="05f99-157">These are just a couple ways to expand the functionality of your 2D application with 3D content.</span></span>

### <a name="creating-a-3d-secondarytile"></a><span data-ttu-id="05f99-158">Erstellen eines 3D-Spiels "SecondaryTile"</span><span class="sxs-lookup"><span data-stu-id="05f99-158">Creating a 3D “secondaryTile”</span></span>

<span data-ttu-id="05f99-159">Sie können 3D-Inhalte aus Ihrer Anwendung mithilfe von "SecondaryTiles" durch die Definition eines mixed Reality-Modells zum Zeitpunkt der Erstellung platzieren.</span><span class="sxs-lookup"><span data-stu-id="05f99-159">You can place 3D content from your application using “secondaryTiles” by defining a mixed reality model at creation time.</span></span> <span data-ttu-id="05f99-160">Mixed Reality-Modelle werden durch Verweisen auf eine 3D-Druck-Dialogfeld in Ihrem app-Paket, und definieren Sie optional ein umgebendes Feld erstellt.</span><span class="sxs-lookup"><span data-stu-id="05f99-160">Mixed reality models are created by referencing a 3D asset in your app package and optionally defining a bounding box.</span></span> 

> [!NOTE]
> <span data-ttu-id="05f99-161">Erstellen "SecondaryTiles" aus, in eine exklusive Ansicht wird derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="05f99-161">Creating “secondaryTiles” from within an exclusive view is not currently supported.</span></span>

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

### <a name="bounding-box"></a><span data-ttu-id="05f99-162">Begrenzungsrahmen</span><span class="sxs-lookup"><span data-stu-id="05f99-162">Bounding box</span></span>

<span data-ttu-id="05f99-163">Ein umgebendes Feld kann verwendet werden, um eine Region zusätzliche Puffer, um das Objekt hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="05f99-163">A bounding box can be used to add an additional buffer region around the object.</span></span> <span data-ttu-id="05f99-164">Das umgebende Feld wird angegeben, mit einem Mittelpunkt sowie von Blöcken, die den Abstand von der Mitte des umgebenden Felds an seinen Rändern an jeder Achse angeben.</span><span class="sxs-lookup"><span data-stu-id="05f99-164">The bounding box is specified using a center point and extents which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="05f99-165">Einheiten für das umgebende Feld zugeordnet werden können, auf 1 Einheit = 1 Meter Umkreis um.</span><span class="sxs-lookup"><span data-stu-id="05f99-165">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="05f99-166">Wenn ein umgebendes Feld nicht angegeben wird wird dann eine automatisch an das Netz des Objekts eingefügt werden.</span><span class="sxs-lookup"><span data-stu-id="05f99-166">If a bounding box is not provided then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="05f99-167">Wenn das angegebene umgebende Feld kleiner ist als das Modell wird diese Größe entsprechend angepasst Mesh.</span><span class="sxs-lookup"><span data-stu-id="05f99-167">If the provided bounding box is smaller than the model then it will be resized to fit the mesh.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="05f99-168">-Verhalten</span><span class="sxs-lookup"><span data-stu-id="05f99-168">Activation behavior</span></span>

> [!NOTE]
> <span data-ttu-id="05f99-169">Dieses Feature unterstützt der Windows-Version RS4-Aktualisierung.</span><span class="sxs-lookup"><span data-stu-id="05f99-169">This feature will be supported as of the Windows RS4 update.</span></span> <span data-ttu-id="05f99-170">Stellen Sie sicher, dass Ihre Anwendung eine Version des Windows SDK größer als oder gleich 10.0.17125 entwickelt wird, wenn Sie dieses Feature verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="05f99-170">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.17125 if you plan to use this feature</span></span>

<span data-ttu-id="05f99-171">Sie können definieren, dass das Verhalten für eine 3D "secondarytile" steuern, wie er reagiert, wenn einem Benutzer ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="05f99-171">You can define the activation behavior for a 3D secondaryTile to control how it reacts when a user selects it.</span></span> <span data-ttu-id="05f99-172">Dies kann verwendet werden, 3D-Objekte in der Mixed Reality home, die Purley informative oder dekorativen platziert.</span><span class="sxs-lookup"><span data-stu-id="05f99-172">This can be used to place 3D objects in the Mixed Reality home that are purley informative or decorative.</span></span> <span data-ttu-id="05f99-173">Die folgenden Arten der Aktivierung Verhalten werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="05f99-173">The following activation behavior types are supported:</span></span>
1. <span data-ttu-id="05f99-174">Standardwert: Wenn ein Benutzer 3D "secondarytile" auswählt, wird die app aktiviert</span><span class="sxs-lookup"><span data-stu-id="05f99-174">Default: When a user selects the 3D secondaryTile the app is activated</span></span>
2. <span data-ttu-id="05f99-175">None: Wenn der Benutzer auswählt, 3D, nichts passiert "secondarytile" und die app ist nicht aktiviert.</span><span class="sxs-lookup"><span data-stu-id="05f99-175">None: When the users selects the 3D secondaryTile nothing happens and the app is not activated.</span></span>

### <a name="obtaining-and-updating-an-existing-secondarytile"></a><span data-ttu-id="05f99-176">Abrufen und Aktualisieren einer vorhandenen "SecondaryTile"</span><span class="sxs-lookup"><span data-stu-id="05f99-176">Obtaining and updating an existing “secondaryTile”</span></span>

<span data-ttu-id="05f99-177">Entwickler erhalten eine Liste mit ihren vorhandenen sekundären Kacheln ist wieder enthält die Eigenschaften, die sie zuvor angegeben haben.</span><span class="sxs-lookup"><span data-stu-id="05f99-177">Developers can get back a list of their existing secondary tiles, which includes the properties that they previously specified.</span></span> <span data-ttu-id="05f99-178">Sie können auch die Eigenschaften aktualisieren, durch das Ändern des Werts und dem anschließenden Aufrufen UpdateAsync().</span><span class="sxs-lookup"><span data-stu-id="05f99-178">They can also update the properties by changing the value and then calling UpdateAsync().</span></span>

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

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a><span data-ttu-id="05f99-179">Überprüfen, dass der Benutzer in Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="05f99-179">Checking that the user is in Windows Mixed Reality</span></span>

<span data-ttu-id="05f99-180">3D deep-Links (SecondaryTiles) können nur erstellt werden, während die Ansicht in eine Windows Mixed Reality-Kopfhörer angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="05f99-180">3D deep links (secondaryTiles) can only be created while the view is being displayed in a Windows Mixed Reality headset.</span></span> <span data-ttu-id="05f99-181">Wenn die Ansicht in eine Windows Mixed Reality-Kopfhörer präsentiert wird, ist nicht empfehlen wir dies ordnungsgemäß behandeln, durch den Einstiegspunkt ausblenden oder ein Fehler angezeigt.</span><span class="sxs-lookup"><span data-stu-id="05f99-181">When your view isn't being presented in a Windows Mixed Reality headset we recommend gracefully handling this by either hiding the entry point or showing an error message.</span></span> <span data-ttu-id="05f99-182">Sie können dies überprüfen, indem Sie Abfragen [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span><span class="sxs-lookup"><span data-stu-id="05f99-182">You can check this by querying [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span></span>

## <a name="tile-notifications"></a><span data-ttu-id="05f99-183">Kachelbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="05f99-183">Tile notifications</span></span>

<span data-ttu-id="05f99-184">Tile-Benachrichtigungen unterstützt senden eine Aktualisierung mit einem 3D-Druck-Dialogfeld derzeit nicht.</span><span class="sxs-lookup"><span data-stu-id="05f99-184">Tile notifications do not currently support sending an update with a 3D asset.</span></span> <span data-ttu-id="05f99-185">Dies bedeutet, dass Entwickler nicht die folgenden Aufgaben ausführen kann</span><span class="sxs-lookup"><span data-stu-id="05f99-185">This means that developers will not be able to do the following</span></span>
* <span data-ttu-id="05f99-186">Erste Schritte mit Pushbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="05f99-186">Push Notifications</span></span>
* <span data-ttu-id="05f99-187">Regelmäßig abgerufen</span><span class="sxs-lookup"><span data-stu-id="05f99-187">Periodic Polling</span></span>
* <span data-ttu-id="05f99-188">Pushbenachrichtigungen</span><span class="sxs-lookup"><span data-stu-id="05f99-188">Scheduled Notifications</span></span>

<span data-ttu-id="05f99-189">Weitere Informationen zu den anderen Kacheln, Funktionen und Attribute und deren Verwendung für 2D Kacheln finden Sie in der [Kacheln für UWP-Apps-Dokumentation](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span><span class="sxs-lookup"><span data-stu-id="05f99-189">For more information on the other tiles features and attributes and how they are used for 2D tiles refer to the [Tiles for UWP Apps documentation](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span></span>

## <a name="see-also"></a><span data-ttu-id="05f99-190">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="05f99-190">See also</span></span>

* <span data-ttu-id="05f99-191">[Mixed Reality-modellbeispiels](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) , die eine-3D-app-Startfeld enthält.</span><span class="sxs-lookup"><span data-stu-id="05f99-191">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="05f99-192">Leitfaden zum Entwerfen von 3D app-Startfeld</span><span class="sxs-lookup"><span data-stu-id="05f99-192">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="05f99-193">Erstellen von 3D-Modellen für die Verwendung zu Hause Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="05f99-193">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="05f99-194">Implementieren von 3D app-startfeldern von (Win32-apps)</span><span class="sxs-lookup"><span data-stu-id="05f99-194">Implementing 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
* [<span data-ttu-id="05f99-195">Navigieren Sie in der Windows Mixed Reality home</span><span class="sxs-lookup"><span data-stu-id="05f99-195">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
