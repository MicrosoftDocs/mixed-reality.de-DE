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
# <a name="implement-3d-app-launchers-uwp-apps"></a>Implementieren von 3D app-startfeldern von (UWP-apps)

> [!NOTE]
> Dieses Feature wurde als Teil des 2017 Fall Creators Update (RS3) für immersive Headsets hinzugefügt und wird unterstützt von HoloLens mit dem Windows 10 April 2018 aktualisieren. Stellen Sie sicher, dass Ihre Anwendung eine Version des Windows SDK größer als oder gleich 10.0.16299 für immersive Headsets und 10.0.17125 für HoloLens entwickelt wird. Sie finden das neueste Windows SDK [hier](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

Die [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) ist der Ausgangspunkt, in denen Benutzer weitergeleitet, vor dem Starten von Anwendungen. Beim Erstellen einer UWP-Anwendung für Windows Mixed Reality, standardmäßig werden apps als 2D Slate-PCs mit ihr app Logo gestartet. Beim Entwickeln von Benutzeroberflächen für Windows Mixed Reality kann 3D Startprogramm optional definiert werden, um das Standard-2D-Startprogramm für Ihre Anwendung zu überschreiben. 3D Startprogramme sind im Allgemeinen empfohlen, für den Start von immersiver Anwendungen, die für Benutzer, die Windows Mixed Reality Startseite zu nutzen, während das Standard-2D-Startprogramm bevorzugt wird, wenn die app direkt aktiviert ist. Sie können auch erstellen, eine [3D deep-Link ("secondarytile")](#3d-deep-links-secondarytiles) als 3D Startprogramm zu Inhalten innerhalb einer Direct2D-UWP-app.

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>3D app-Startprogramm-Erstellungsprozess

Es gibt 3 Schritte zum Erstellen einer-3D-app-Startfeld:
1. [Entwerfen und concepting](3d-app-launcher-design-guidance.md)
2. [Modellieren und exportieren](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Die Integration in Ihre Anwendung (in diesem Artikel)

3D-Objekte verwendet werden, wie mithilfe Startprogramme für Ihre Anwendung erstellt werden soll die [Windows Mixed Reality Erstellen von Richtlinien](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) um die Kompatibilität sicherzustellen. Ressourcen, die diese Spezifikation authoring einhalten werden nicht in die Windows Mixed Reality home gerendert werden.

## <a name="configuring-the-3d-launcher"></a>Konfigurieren das Startprogramm 3D

Wenn Sie ein neues Projekt in Visual Studio erstellen, wird eine einfache Standardkachel erstellt, die den Namen und das Logo Ihrer App anzeigt. Bearbeiten zum Ersetzen dieses 2D Darstellung mit einem benutzerdefinierten 3D-Modell der app-Manifest der Anwendung, um das Element "MixedRealityModel" als Teil Ihrer Kachel-Standarddefinition enthalten. Um die 2D wiederherzustellen Startprogramm entfernen Sie einfach die MixedRealityModel-Definition aus dem Manifest.

### <a name="xml"></a>XML

Suchen Sie zunächst die app-Paketmanifest in Ihrem aktuellen Projekt. Standardmäßig wird das Manifest "Package.appxmanifest" benannt. Wenn Sie Visual Studio verwenden, klicken Sie dann mit der rechten Maustaste in des Manifests in einem Viewer für die Projektmappe, und wählen **Quelltext anzeigen** zu den XML-Code für die Bearbeitung zu öffnen. 

Klicken Sie am oberen Rand des Manifests fügen Sie das Schema uap5, und fügen Sie es als ein ignorierbares Namespace:

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

Als Nächstes geben Sie die "MixedRealityModel" in der standardkachel für Ihre Anwendung:

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

Die Elemente MixedRealityModel akzeptiert einen Dateipfad verweist auf ein 3D-Objekt Medienobjekt im app-Paket gespeichert. Derzeit nur 3D-Modelle übermittelt das .glb Dateiformat, und erstellt anhand der [Windows Mixed Reality-3D-Asset Erstellen von Anweisungen](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) werden unterstützt. Ressourcen müssen in das app-Paket gespeichert werden und die Animation wird derzeit nicht unterstützt. Der Parameter "Path" leer gelassen wird Windows 2D slates statt das Startprogramm 3D angezeigt. **Hinweis:** .glb Medienobjekt muss markiert werden als "Inhalt" in den Buildeinstellungen vor dem Erstellen und Ausführen Ihrer app.


![Wählen Sie die .glb im Projektmappen-Explorer, und verwenden Sie den Abschnitt "Properties" als "Inhalt" in den Buildeinstellungen kennzeichnen](images/buildsetting-content-300px.png)<br>
*Wählen Sie die .glb im Projektmappen-Explorer, und verwenden Sie den Abschnitt "Properties" als "Inhalt" in den Buildeinstellungen kennzeichnen*

### <a name="bounding-box"></a>Begrenzungsrahmen

Ein umgebendes Feld kann verwendet werden, um optional eine zusätzlicher Puffer-Region, um das Objekt hinzuzufügen. Das umgebende Feld wird angegeben, mit einem Mittelpunkt sowie von Blöcken, die den Abstand von der Mitte des umgebenden Felds an seinen Rändern an jeder Achse angeben. Einheiten für das umgebende Feld zugeordnet werden können, auf 1 Einheit = 1 Meter Umkreis um. Wenn ein umgebendes Feld nicht angegeben wird wird dann eine automatisch an das Netz des Objekts eingefügt werden. Wenn das angegebene umgebende Feld kleiner ist als das Modell wird diese Größe entsprechend angepasst Mesh.

Unterstützung für das umgebende Feld-Attribut kommen mit dem Windows-Version RS4-Update als Eigenschaft für das Element MixedRealityModel. Zuerst definieren Sie ein umgebendes Feld am oberen Rand der app Manifest, fügen Sie das Schema uap6, und fügen Sie sie diese als ignorable-Namespaces:

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
Legen Sie anschließend auf die MixedRealityModel SpatialBoundingBox Eigenschaft, die das umgebende Feld definiert: 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>Mithilfe von Unity

Bei der Arbeit mit Unity wird das Projekt muss erstellt und in Visual Studio geöffnet werden, bevor App-Manifest bearbeitet werden können. 

>[!NOTE]
>Das Startprogramm 3D muss im Manifest beim Erstellen und Bereitstellen einer neuen Visual Studio-Projektmappe von Unity neu definiert werden.

## <a name="3d-deep-links-secondarytiles"></a>3D Deep-links (SecondaryTiles)

> [!NOTE]
> Dieses Feature wurde hinzugefügt, als Teil der 2017 Fall Creators Update (RS3) für immersive Headsets von (VR) und als Teil von April 2018 Update (RS4) für HoloLens. Stellen Sie sicher, dass Ihre Anwendung eine Version des Windows SDK größer als oder gleich 10.0.16299 für immersive Headsets von (VR) und 10.0.17125 für HoloLens entwickelt wird. Sie finden das neueste Windows SDK [hier](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

>[!IMPORTANT]
>3D deep-Links (SecondaryTiles) funktionieren nur mit Direct2D UWP-apps. Sie können jedoch erstellen, eine [-3D-app-Startfeld](implementing-3d-app-launchers.md) um eine exklusive app über die Windows Mixed Reality home zu starten.

2D Anwendungen für Windows Mixed Reality verbessert werden können, durch Hinzufügen der Funktion zum Platzieren von 3D-Modellen aus Ihrer app in der [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) als deep-Links zu Inhalten innerhalb Ihrer Direct2D-app, wie [2D sekundäre Datenbank Kacheln](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) über das Windows-Startmenü. Beispielsweise können Sie 360° Photospheres erstellen, die direkt in eine 360° Foto-Viewer-app zu verknüpfen, oder lassen Sie die Benutzer-3D-Inhalte aus einer Auflistung von Ressourcen zu platzieren, die eine Detailseite zum Autor wird geöffnet. Hierbei handelt es sich um ein paar Möglichkeiten zum Erweitern der Funktionalität der Anwendung und einer 3D-Inhalt 2D.

### <a name="creating-a-3d-secondarytile"></a>Erstellen eines 3D-Spiels "SecondaryTile"

Sie können 3D-Inhalte aus Ihrer Anwendung mithilfe von "SecondaryTiles" durch die Definition eines mixed Reality-Modells zum Zeitpunkt der Erstellung platzieren. Mixed Reality-Modelle werden durch Verweisen auf eine 3D-Druck-Dialogfeld in Ihrem app-Paket, und definieren Sie optional ein umgebendes Feld erstellt. 

> [!NOTE]
> Erstellen "SecondaryTiles" aus, in eine exklusive Ansicht wird derzeit nicht unterstützt.

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

### <a name="bounding-box"></a>Begrenzungsrahmen

Ein umgebendes Feld kann verwendet werden, um eine Region zusätzliche Puffer, um das Objekt hinzuzufügen. Das umgebende Feld wird angegeben, mit einem Mittelpunkt sowie von Blöcken, die den Abstand von der Mitte des umgebenden Felds an seinen Rändern an jeder Achse angeben. Einheiten für das umgebende Feld zugeordnet werden können, auf 1 Einheit = 1 Meter Umkreis um. Wenn ein umgebendes Feld nicht angegeben wird wird dann eine automatisch an das Netz des Objekts eingefügt werden. Wenn das angegebene umgebende Feld kleiner ist als das Modell wird diese Größe entsprechend angepasst Mesh.

### <a name="activation-behavior"></a>-Verhalten

> [!NOTE]
> Dieses Feature unterstützt der Windows-Version RS4-Aktualisierung. Stellen Sie sicher, dass Ihre Anwendung eine Version des Windows SDK größer als oder gleich 10.0.17125 entwickelt wird, wenn Sie dieses Feature verwenden möchten.

Sie können definieren, dass das Verhalten für eine 3D "secondarytile" steuern, wie er reagiert, wenn einem Benutzer ausgewählt. Dies kann verwendet werden, 3D-Objekte in der Mixed Reality home, die Purley informative oder dekorativen platziert. Die folgenden Arten der Aktivierung Verhalten werden unterstützt:
1. Standardwert: Wenn ein Benutzer 3D "secondarytile" auswählt, wird die app aktiviert
2. None: Wenn der Benutzer auswählt, 3D, nichts passiert "secondarytile" und die app ist nicht aktiviert.

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>Abrufen und Aktualisieren einer vorhandenen "SecondaryTile"

Entwickler erhalten eine Liste mit ihren vorhandenen sekundären Kacheln ist wieder enthält die Eigenschaften, die sie zuvor angegeben haben. Sie können auch die Eigenschaften aktualisieren, durch das Ändern des Werts und dem anschließenden Aufrufen UpdateAsync().

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

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a>Überprüfen, dass der Benutzer in Windows Mixed Reality

3D deep-Links (SecondaryTiles) können nur erstellt werden, während die Ansicht in eine Windows Mixed Reality-Kopfhörer angezeigt wird. Wenn die Ansicht in eine Windows Mixed Reality-Kopfhörer präsentiert wird, ist nicht empfehlen wir dies ordnungsgemäß behandeln, durch den Einstiegspunkt ausblenden oder ein Fehler angezeigt. Sie können dies überprüfen, indem Sie Abfragen [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).

## <a name="tile-notifications"></a>Kachelbenachrichtigungen

Tile-Benachrichtigungen unterstützt senden eine Aktualisierung mit einem 3D-Druck-Dialogfeld derzeit nicht. Dies bedeutet, dass Entwickler nicht die folgenden Aufgaben ausführen kann
* Erste Schritte mit Pushbenachrichtigungen
* Regelmäßig abgerufen
* Pushbenachrichtigungen

Weitere Informationen zu den anderen Kacheln, Funktionen und Attribute und deren Verwendung für 2D Kacheln finden Sie in der [Kacheln für UWP-Apps-Dokumentation](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).

## <a name="see-also"></a>Siehe auch

* [Mixed Reality-modellbeispiels](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) , die eine-3D-app-Startfeld enthält.
* [Leitfaden zum Entwerfen von 3D app-Startfeld](3d-app-launcher-design-guidance.md)
* [Erstellen von 3D-Modellen für die Verwendung zu Hause Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementieren von 3D app-startfeldern von (Win32-apps)](implementing-3d-app-launchers-win32.md)
* [Navigieren Sie in der Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md)
