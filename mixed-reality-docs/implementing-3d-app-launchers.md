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
# <a name="implement-3d-app-launchers-uwp-apps"></a>Implementieren von 3D-App-launchern (UWP-Apps)

> [!NOTE]
> Diese Funktion wurde als Teil des 2017 Fall Creators Updates (RS3) für immersive Headsets hinzugefügt und wird von hololens mit dem Windows 10-Update vom April 2018 unterstützt. Stellen Sie sicher, dass Ihre Anwendung auf eine Version des Windows SDK ist, die größer als oder gleich 10.0.16299 auf immersiven Headsets und 10.0.17125 auf hololens ist. Die neuesten Windows SDK finden Sie [hier](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

Der [Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) -Startpunkt ist der Ausgangspunkt, an dem Benutzer vor dem Starten von Anwendungen landen. Beim Erstellen einer UWP-Anwendung für Windows Mixed Reality werden apps standardmäßig als 2D-Slate mit dem Logo Ihrer APP gestartet. Beim Entwickeln von Umgebungen für Windows Mixed Reality kann optional ein 3D-Start Programm definiert werden, um das standardmäßige 2D-Start Programm für Ihre Anwendung zu überschreiben. Im Allgemeinen werden 3D-Start Programm zum Starten von immersiven Anwendungen empfohlen, die Benutzer aus der Windows Mixed Reality-Startseite ziehen, während das standardmäßige 2D-Start Programm bevorzugt wird, wenn die APP an Ort und Stelle aktiviert wird. Sie können auch einen [3D-Deep-Link (secondarytile)](#3d-deep-links-secondarytiles) als 3D-Start Programm für Inhalte innerhalb einer 2D-UWP-app erstellen.

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>Erstellung eines 3D-App-Start Programms

Zum Erstellen eines 3D-App-Start Programms sind drei Schritte erforderlich:
1. [Entwurf und Konzept](3d-app-launcher-design-guidance.md)
2. [Modellieren und exportieren](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integration in Ihre Anwendung (dieser Artikel)

3D-Ressourcen, die als Launcher für Ihre Anwendung verwendet werden sollen, sollten mithilfe der [Windows Mixed Reality Authoring Guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) erstellt werden, um die Kompatibilität zu gewährleisten. Assets, die diese Erstellungs Spezifikation nicht erfüllen, werden nicht in der Windows Mixed Reality-Startseite gerendert.

## <a name="configuring-the-3d-launcher"></a>Konfigurieren des 3D-Start Programms

Wenn Sie ein neues Projekt in Visual Studio erstellen, wird eine einfache Standardkachel erstellt, die den Namen und das Logo Ihrer App anzeigt. Um diese 2D-Darstellung durch ein benutzerdefiniertes 3D-Modell zu ersetzen, bearbeiten Sie das App-Manifest der Anwendung so, dass das "mixedrealitymodel"-Element als Teil Ihrer Standard Kachel Definition enthalten ist. Um zum 2D-Start Programm zurückzukehren, entfernen Sie einfach die mixedrealitymodel-Definition aus dem Manifest.

### <a name="xml"></a>XML

Suchen Sie zuerst das App-Paket Manifest in Ihrem aktuellen Projekt. Standardmäßig wird das Manifest "Package. appxmanifest" genannt. Wenn Sie Visual Studio verwenden, klicken Sie mit der rechten Maustaste auf das Manifest in Ihrem projektmappenviewer, und wählen Sie **Quelle anzeigen** , um den XML-Code zum Bearbeiten zu öffnen. 

Fügen Sie am Anfang des Manifests das uap5-Schema hinzu, und fügen Sie es als Ignorable-Namespace ein:

```xml
<Package xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="https://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

Geben Sie als nächstes "mixedrealitymodel" in der Standard Kachel für Ihre Anwendung an:

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

Die mixedrealitymodel-Elemente akzeptieren einen Dateipfad, der auf ein 3D-Asset verweist, das in Ihrem App-Paket gespeichert ist. Zurzeit werden nur 3D-Modelle unter Verwendung des. GLB-Datei Formats bereitgestellt, die für die [Windows Mixed Reality 3D Asset Authoring-Anweisungen](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) erstellt wurden. Assets müssen im App-Paket gespeichert werden, und die Animation wird derzeit nicht unterstützt. Wenn der Parameter "Path" leer gelassen wird, zeigt Windows das 2D-Slate anstelle des 3D-Start Programms an. **Hinweis:** das. GLB-Asset muss in ihren Buildeinstellungen als "Inhalt" gekennzeichnet werden, bevor Sie Ihre APP erstellen und ausführen.


![die. GLB-Datei im Projektmappen-Explorer auswählen und den Abschnitt Eigenschaften verwenden, um Sie in den Buildeinstellungen als "Inhalt" zu markieren](images/buildsetting-content-300px.png)<br>
*Wählen Sie im Projektmappen-Explorer die GLB-Datei aus, und markieren Sie Sie mithilfe des Abschnitts Eigenschaften als "Inhalt" in den Buildeinstellungen.*

### <a name="bounding-box"></a>Begrenzungsrahmen

Ein Begrenzungs Rahmen kann verwendet werden, um optional einen zusätzlichen Pufferbereich um das Objekt hinzuzufügen. Das umgebende Feld wird mithilfe eines Mittelpunkts und der Blöcke angegeben, die den Abstand zwischen der Mitte des umgebenden Felds und seinen Rändern entlang der Achse angeben. Die Einheiten für das Begrenzungsfeld können 1 Einheit = 1 Meter zugeordnet werden. Wenn kein Begrenzungsfeld angegeben wird, wird eines automatisch an das Mesh des Objekts angepasst. Wenn das angegebene Begrenzungsfeld kleiner als das Modell ist, wird es in die Größe geändert, damit es an das Mesh angepasst ist.

Die Unterstützung für das Begrenzungsfeld Attribut wird mit dem Windows-Update-Update als Eigenschaft für das mixedrealitymodel-Element erreicht. Fügen Sie zum Definieren eines Begrenzungs Rahmens zuerst am oberen Rand des App-Manifests das uap6-Schema hinzu, und fügen Sie es als Ignorable Namespaces ein:

```xml
<Package xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="https://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="https://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
Legen Sie als nächstes auf dem mixedrealitymodel die spatialboundingbox-Eigenschaft auf das Begrenzungsfeld fest: 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>Verwenden von Unity

Beim Arbeiten mit Unity muss das Projekt in Visual Studio erstellt und geöffnet werden, bevor das App-Manifest bearbeitet werden kann. 

>[!NOTE]
>Das 3D-Start Programm muss im Manifest neu definiert werden, wenn eine neue Visual Studio-Projekt Mappe aus Unity aufgebaut und bereitgestellt wird.

## <a name="3d-deep-links-secondarytiles"></a>3D Deep-Links (secondarytiles)

> [!NOTE]
> Diese Funktion wurde als Teil des 2017 Fall Creators Update (RS3) für immersive (VR)-Headsets und im Rahmen des Updates vom April 2018 (RS4) für hololens hinzugefügt. Stellen Sie sicher, dass Ihre Anwendung auf eine Version des Windows SDK ist, das größer als oder gleich 10.0.16299 on immersive (VR)-Headsets und 10.0.17125 auf hololens ist. Die neuesten Windows SDK finden Sie [hier](https://developer.microsoft.com/windows/downloads/windows-10-sdk).

>[!IMPORTANT]
>3D-Deep-Links (secondarytiles) funktionieren nur mit 2D-UWP-apps. Sie können jedoch ein [3D-App-](implementing-3d-app-launchers.md) Startfeld erstellen, um eine exklusive App aus dem Windows Mixed Reality-Start Programm zu starten.

Ihre 2D-Anwendungen können für die gemischte Windows-Realität erweitert werden, indem Sie die Möglichkeit zum Platzieren von 3D-Modellen aus Ihrer APP als tiefe Links zu Inhalten in ihrer 2D-app hinzufügen [, wie z](navigating-the-windows-mixed-reality-home.md) [. b. zwei sekundäre Kacheln](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) auf dem Windows-Start. stehen. Sie können z. b. 360 °-photosphären erstellen, die direkt in eine 360 °-Foto-Viewer-App verweisen, oder Benutzern das Platzieren von 3D-Inhalten aus einer Sammlung von Objekten ermöglichen, die eine Detailseite zum Autor öffnet. Dies sind nur einige Möglichkeiten, die Funktionalität Ihrer 2D-Anwendung mit 3D-Inhalten zu erweitern.

### <a name="creating-a-3d-secondarytile"></a>Erstellen einer 3D-"secondarytile"

Sie können 3D-Inhalte mithilfe von "secondarytiles" aus der Anwendung platzieren, indem Sie zum Zeitpunkt der Erstellung ein gemischtes Reality-Modell definieren. Gemischte Reality-Modelle werden erstellt, indem auf ein 3D-Medienobjekt in Ihrem App-Paket verwiesen und optional ein Begrenzungsfeld definiert wird. 

> [!NOTE]
> Das Erstellen von "secondarytiles" aus einer exklusiven Ansicht wird derzeit nicht unterstützt.

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

Zum Hinzufügen eines zusätzlichen Puffer Bereichs um das Objekt kann ein Begrenzungs Rahmen verwendet werden. Das umgebende Feld wird mithilfe eines Mittelpunkts und der Blöcke angegeben, die den Abstand zwischen der Mitte des umgebenden Felds und seinen Rändern entlang der Achse angeben. Die Einheiten für das Begrenzungsfeld können 1 Einheit = 1 Meter zugeordnet werden. Wenn kein Begrenzungsfeld angegeben wird, wird eines automatisch an das Mesh des Objekts angepasst. Wenn das angegebene Begrenzungsfeld kleiner als das Modell ist, wird es in die Größe geändert, damit es an das Mesh angepasst ist.

### <a name="activation-behavior"></a>Aktivierungs Verhalten

> [!NOTE]
> Diese Funktion wird ab dem Windows-Update "RS4" unterstützt. Stellen Sie sicher, dass Ihre Anwendung auf eine Version der Windows SDK, die größer als oder gleich 10.0.17125 ist, wenn Sie beabsichtigen, dieses Feature zu verwenden.

Sie können das Aktivierungs Verhalten für eine 3D-secondarytile definieren, um zu steuern, wie Sie reagiert, wenn ein Benutzer Sie auswählt. Dies kann verwendet werden, um 3D-Objekte in die gemischte Realität zu platzieren, die rein informativ oder dekorativ sind. Die folgenden Aktivierungs Verhaltenstypen werden unterstützt:
1. Standard: Wenn ein Benutzer die 3D-secondarytile auswählt, wird die App aktiviert.
2. Keine: Wenn die Benutzer die 3D-secondarytile auswählen, geschieht nichts, und die APP ist nicht aktiviert.

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>Abrufen und Aktualisieren einer vorhandenen "secondarytile"

Entwickler können eine Liste Ihrer vorhandenen sekundären Kacheln zurückerhalten, einschließlich der Eigenschaften, die Sie zuvor angegeben haben. Sie können die Eigenschaften auch aktualisieren, indem Sie den Wert ändern und dann UpdateAsync () aufrufen.

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

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a>Überprüfen, ob der Benutzer in der gemischten Realität von Windows ist

3D Deep-Links (secondarytiles) können nur erstellt werden, während die Ansicht in einem Windows Mixed Reality-Headset angezeigt wird. Wenn Ihre Ansicht nicht in einem Windows Mixed Reality-Headset angezeigt wird, sollten Sie diese ordnungsgemäß behandeln, indem Sie entweder den Einstiegspunkt ausblenden oder eine Fehlermeldung anzeigen. Sie können dies überprüfen, indem Sie [iscurrentviewpresentedonholographic ()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)Abfragen.

## <a name="tile-notifications"></a>Kachelbenachrichtigungen

Bei Kachel Benachrichtigungen wird das Senden eines Updates mit einem 3D-Medienobjekt derzeit nicht unterstützt. Dies bedeutet, dass Entwickler nicht die folgenden Aktionen ausführen können:
* Pushbenachrichtigungen
* Periodische Abruf Vorgänge
* Geplante Benachrichtigungen

Weitere Informationen zu den anderen Kacheln Features und Attributen und deren Verwendung für 2D-Kacheln finden Sie in der [Dokumentation zu Kacheln für UWP-apps](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).

## <a name="see-also"></a>Weitere Informationen:

* [Gemischtes Reality-Modell Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) mit einem 3D-App-Start Programm.
* [Entwurfsanleitung für 3D-App-Startprogramm](3d-app-launcher-design-guidance.md)
* [Erstellen von 3D-Modellen für die Verwendung in der Windows Mixed Reality-Startseite](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementieren von 3D-App-launchern (Win32-Apps)](implementing-3d-app-launchers-win32.md)
* [Navigieren auf der Startseite von Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
