---
title: Räumliche Zuordnung in DirectX
description: Erläutert, wie Sie räumliche Zuordnung in DirectX-Apps zu implementieren. Dies schließt eine ausführliche Erläuterung der beispielanwendung räumliche Zuordnung, die mit dem Universal Windows Platform SDK enthalten ist.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows mixed Reality, räumliche Zuordnung, Umgebung, Interaktion, Directx, Winrt, api, Beispielcode, UWP, SDK, exemplarische Vorgehensweise
ms.openlocfilehash: db3f1464158c04127e456cadd5fb633336909344
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605135"
---
# <a name="spatial-mapping-in-directx"></a>Räumliche Zuordnung in DirectX

In diesem Thema wird beschrieben, wie implementieren [räumliche Zuordnung](spatial-mapping.md) in DirectX-Apps. Dies schließt eine ausführliche Erläuterung der beispielanwendung räumliche Zuordnung, die mit dem Universal Windows Platform SDK enthalten ist.

In diesem Thema verwendet den Code aus der [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP-Codebeispiel.

>[!NOTE]
>Die Codeausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstatt C ++ 17-kompatible C++"/ WinRT", wie in der [ C++ holographic Projektvorlage](creating-a-holographic-directx-project.md).  Die Konzepte sind Entsprechung für einen C++"/ WinRT"-Projekt, aber Sie benötigen, um den Code zu übersetzen.

## <a name="directx-development-overview"></a>Übersicht über die Entwicklung von DirectX

Entwicklung von systemeigenen Anwendungen für räumliche Zuordnung verwendet, die APIs unter dem [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) Namespace. Diese APIs bieten Vollzugriff auf räumliche Mapping-Funktion direkt auf die räumliche Zuordnung APIs verfügbar gemacht werden, indem Sie analog [Unity](spatial-mapping-in-unity.md).

### <a name="perception-apis"></a>Perception-APIs

Die primären Typen für die räumliche Zuordnung Entwicklung lauten wie folgt aus:
* [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) enthält Informationen über die Flächen in anwendungsspezifische Regionen des Speicherplatzes in der Nähe der Benutzer in Form von SpatialSurfaceInfo-Objekten.
* [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) wird beschrieben, eine einzelne Zusammenführungsmechanismus räumliche Oberfläche, einschließlich einer eindeutigen ID, die umgebenden Volume und die Uhrzeit der letzten Änderung. Sie erhalten eine SpatialSurfaceMesh asynchron auf Anfrage.
* [SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) enthält Parameter, die zur Anpassung der SpatialSurfaceMesh-Objekten, die vom SpatialSurfaceInfo angefordert.
* [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) die Mesh-Daten für eine einzelne räumliche Oberfläche darstellt. Die Daten für die Vertexpositionen, Vertex Normals und Dreiecksindizes ist in SpatialSurfaceMeshBuffer Memberobjekte enthalten.
* [SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) dient als Wrapper für einen einzelnen Zugriffstyp für Mesh-Daten.

Bei der Entwicklung einer Anwendung, die mithilfe dieser APIs sieht der basic-Programm-Flow (wie in der beispielanwendung, die unten beschriebenen):
- **Richten Sie Ihre SpatialSurfaceObserver**
  - Rufen Sie ["requestaccessasync"](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), um sicherzustellen, dass der Benutzer über die Berechtigung für Ihre Anwendung zur Verwendung von Funktionen des Geräts räumliche Zuordnung erteilt hat.
  - Instanziieren Sie ein SpatialSurfaceObserver-Objekt.
  - Rufen Sie [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) Regionen des Speicherplatzes angeben, in dem Informationen zu räumlichen Flächen werden sollen. Sie können diese Regionen in Zukunft ändern, indem Sie einfach erneut aufrufen dieser Funktion. Jede Region angegeben ist, mit einem [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).
  - Registrieren Sie sich für die [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) -Ereignis, das ausgelöst wird, sobald neue Informationen zu den räumlichen Oberflächen in den Regionen Speicherplatz verfügbar sind, Sie angegeben haben.
- **Verarbeiten von Ereignissen ObservedSurfacesChanged**
  - Rufen Sie im Ereignishandler, [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) erhalten Sie eine Zuordnung von SpatialSurfaceInfo-Objekten. Mithilfe dieser Zuordnung, können Sie Ihre Einträge von der räumlichen Oberflächen aktualisieren [vorhanden sind, in der Umgebung des Benutzers](spatial-mapping.md#mesh-caching).
  - Für jedes Objekt SpatialSurfaceInfo, können Sie Abfragen [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) um zu bestimmen, die räumliche Blöcke der Oberfläche, ausgedrückt in einem [räumliche Koordinatensystem](coordinate-systems.md) Ihrer Wahl.
  - Wenn Sie Mesh für eine räumliche Fläche anfordern möchten, rufen Sie [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx). Sie können Optionen festlegen, die gewünschten Dichte der Dreiecke und das Format der zurückgegebenen Mesh Daten angeben.
- **Empfangen und Verarbeiten von Netz**
  - Jeder Aufruf von TryComputeLatestMeshAsync wird Aysnchronously geben eine SpatialSurfaceMesh-Objekt zurück.
  - Von diesem Objekt können Sie die enthaltenen SpatialSurfaceMeshBuffer-Objekte zugreifen, um Zugriff auf die Dreiecksindizes und Vertexpositionen und (falls angefordert) flächenspezifische des Mesh. Diese Daten werden in einem Format direkt kompatibel mit der [Direct3D 11-API](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) zum Rendern der Gitter verwendet.
  - Von hier aus Ihrer Anwendung optional Analyse ausführen kann oder [Verarbeitung](spatial-mapping.md#mesh-processing) Mesh Daten ein, und verwenden dieses Zugriffstokens für [Rendering](spatial-mapping.md#rendering) und physikalische Eigenschaften [feinheiten beim Raycasting und kollisionserkennung](spatial-mapping.md#raycasting-and-collision).
  - Ein wichtiges Detail zu beachten ist, müssen Sie eine Skalierung auf die Mesh-Vertexpositionen (z. B. in den Vertex-Shader, der zum Rendern der Gitter verwendet wird) anwenden, Zähler um sie aus den optimierten Ganzzahl Einheiten konvertieren in der sie in den Puffer zu gespeichert sind. Sie können diese Skalierung abrufen, durch den Aufruf [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).

### <a name="troubleshooting"></a>Problembehandlung
* Vergessen Sie nicht, Netz Vertexpositionen in Ihre Vertex-Shader, der unter Verwendung der Dezimalstellen, die vom skalieren [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)

## <a name="spatial-mapping-code-sample-walkthrough"></a>Exemplarische Vorgehensweise räumliche Zuordnung code

Die [Holographic räumliche Zuordnung](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) Codebeispiel enthält Code, der für den Einstieg in die Oberfläche Gitter in Ihre app, einschließlich der Infrastruktur zur Verwaltung von laden können und die Renderingoberfläche Gitter.

Nun führen wir durch die Oberfläche Zuordnungsfunktion DirectX-Apps hinzufügen. Sie können diesen Code zum Hinzufügen Ihrer [Windows Holographic-app-Vorlage](creating-a-holographic-directx-project.md) -Projekt, oder Sie mithilfe des Durchsuchens im oben erwähnten Beispiels nachvollziehen können. Dieses Codebeispiel basiert auf Windows Holographic-app-Vorlage.

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Richten Sie Ihre app, um die SpatialPerception-Funktion verwenden

Ihre app muss die räumliche Zuordnungsfunktion verwenden können. Dies ist erforderlich, da das räumliche Netz eine Darstellung der Umgebung des Benutzers, ist, die private Daten angesehen werden kann. Deklarieren Sie diese Funktion wird in der Datei "Package.appxmanifest" für Ihre app ein. Im Folgenden ein Beispiel:

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

Die Funktion stammt aus dem **uap2** Namespace. Um Zugriff auf diesen Namespace in Ihrem Manifest zu erhalten, fügen Sie ihn als einen *Xlmns* -Attribut in der &lt;Paket > Element. Im Folgenden ein Beispiel:

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a>Überprüfen Sie für die Unterstützung für räumliche Zuordnung-Funktion

Windows Mixed Reality unterstützt eine Vielzahl von Geräten, einschließlich Geräte, die räumliche Zuordnung nicht unterstützen. Wenn Ihre app räumliche Zuordnung können oder räumliche Zuordnung verwenden muss, um Funktionen bereitzustellen, sollten sie sicherstellen, dass räumliche Zuordnung unterstützt wird, bevor Sie versuchen, die sie verwenden überprüfen. Z. B. wenn räumliche Zuordnung Ihrer mixed Reality-app erforderlich ist, sollten sie eine entsprechende Meldung angezeigt, wenn ein Benutzer versucht, die es auf ein Gerät ohne räumliche Zuordnung ausgeführt. Oder Ihre app möglicherweise zum Rendern einer eigenen virtuellen Umgebung anstelle der Umgebung des Benutzers, gleichzeitig eine Methode, die ähnelt dem, was geschieht, wenn räumliche Zuordnung zur Verfügung standen. In jedem Fall kann diese API Ihrer app zu beachten, wenn es nicht räumliche Zuordnungsdaten abrufen und auf die geeignete Weise reagieren.

Um das aktuelle Gerät für die Unterstützung für räumliche Zuordnung überprüfen zu können, stellen Sie zunächst sicher, dass der UWP-Vertrag auf Ebene 4 oder höher ist, und rufen Sie dann die SpatialSurfaceObserver::IsSupported() aus. Hier ist wie das geht im Rahmen der [Holographic räumliche Zuordnung](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) Codebeispiel. Unterstützung wird unmittelbar vor das Anfordern des Zugriffs überprüft.

Die SpatialSurfaceObserver::IsSupported()-API steht im SDK, Version 15063 ab. Bei Bedarf neu zuweisen Sie Ihr Projekt auf die Plattformversion 15063 vor der Verwendung dieser API.

```cpp
if (m_surfaceObserver == nullptr)
   {
       using namespace Windows::Foundation::Metadata;
       if (ApiInformation::IsApiContractPresent(L"Windows.Foundation.UniversalApiContract", 4))
       {
           if (!SpatialSurfaceObserver::IsSupported())
           {
               // The current system does not have spatial mapping capability.
               // Turn off spatial mapping.
               m_spatialPerceptionAccessRequested = true;
               m_surfaceAccessAllowed = false;
           }
       }

       if (!m_spatialPerceptionAccessRequested)
       {
           /// etc ...
```

Beachten Sie, dass bei der UWP-Vertrag kleiner als Stufe 4 ist, die app fortgesetzt werden soll, als wäre die räumliche Zuordnung durchführen kann.

### <a name="request-access-to-spatial-mapping-data"></a>Anfordern des Zugriffs auf den spatial Zuordnen von Daten

Ihre app muss zum Anfordern von Berechtigungen für den Datenzugriff räumliche Zuordnung, bevor Sie versuchen, die Oberfläche Beobachter zu erstellen. Hier ist ein Beispiel anhand unserer Zuordnen von Surface-Codebeispiel, mit weiteren Details bereitgestellt weiter unten auf dieser Seite:

```cpp
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Create a surface observer.
    }
    else
    {
        // Handle spatial mapping unavailable.
    }
}
```

### <a name="create-a-surface-observer"></a>Erstellen Sie einen Beobachter Oberflächen

Die **Windows::Perception::Spatial::Surfaces** Namespace enthält die [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) -Klasse, die ein oder mehrere Volumes, die Sie angeben berücksichtigt, in einem [ SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx). Verwenden einer [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) Instanz für den Datenzugriff über die Oberfläche Mesh in Echtzeit.

Von **AppMain.h**:

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

Wie im vorherigen Abschnitt erwähnt, müssen Sie den Zugriff auf räumliche Zuordnungsdaten anfordern, bevor Ihre app verwendet werden kann. Dieser Zugriff wird automatisch auf die HoloLens gewährt.

```cpp
// The surface mapping API reads information about the user's environment. The user must
// grant permission to the app to use this capability of the Windows Mixed Reality device.
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // If status is allowed, we can create the surface observer.
        m_surfaceObserver = ref new SpatialSurfaceObserver();
```

Als Nächstes müssen Sie den Oberflächen Beobachter, um zu beobachten, ein bestimmtes umgebendes Volume zu konfigurieren. Hier stellen wir ein Dialogfeld mit der 20 x 20 x 5-Zähler, um den Ursprung des Koordinatensystems zentriert ist.

```cpp
// The surface observer can now be configured as needed.

        // In this example, we specify one area to be observed using an axis-aligned
        // bounding box 20 meters in width and 5 meters in height and centered at the
        // origin.
        SpatialBoundingBox aabb =
        {
            { 0.f,  0.f, 0.f },
            {20.f, 20.f, 5.f },
        };

        SpatialBoundingVolume^ bounds = SpatialBoundingVolume::FromBox(coordinateSystem, aabb);
        m_surfaceObserver->SetBoundingVolume(bounds);
```

Beachten Sie, dass Sie mehrere umgebende Volumes stattdessen festlegen können.

*Dies ist der Pseudocode:*

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

Es ist auch möglich, andere umgebenden Formen – z. B. eine Frustums Ansicht verwenden oder ein umgebendes Felds an, die nicht Achse ausgerichtet werden.

*Dies ist der Pseudocode:*

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

Wenn Ihre app muss etwas anders machen, wenn Surface Zuordnen von Daten nicht verfügbar ist, können Sie schreiben Code zum Antworten auf die Groß-/Kleinschreibung, in denen die [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) nicht **zulässige** – z. B. Es sind nicht zulässig auf PCs mit immersive Geräten, die angefügt werden, da diese Geräte der Hardware für räumliche Zuordnung nicht. Für diese Geräte sollten Sie stattdessen auf den spatial Informationen zu Konfiguration und Umgebung des Benutzers verlassen.

### <a name="initialize-and-update-the-surface-mesh-collection"></a>Initialisieren Sie und aktualisieren Sie die Oberfläche Mesh-Sammlung

Wenn der Beobachter Oberfläche wurde erfolgreich erstellt wurde, können Sie zum Initialisieren unserer Oberfläche Mesh-Auflistung fortfahren. Hier verwenden wir die Pull-Modell-API, um den aktuellen Satz von beobachteten Flächen sofort zu erhalten:

```cpp
auto mapContainingSurfaceCollection = m_surfaceObserver->GetObservedSurfaces();
        for (auto& pair : mapContainingSurfaceCollection)
        {
            // Store the ID and metadata for each surface.
            auto const& id = pair->Key;
            auto const& surfaceInfo = pair->Value;
            m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
        }
```

Es gibt auch ein Push-Modell, das zum Abrufen von Daten von Surface Mesh verfügbar. Sie sind kostenlos, Entwerfen Sie Ihre app nur das Pullmodell verwenden, wenn Sie auswählen, bei dem Sie Daten regelmäßig - abrufen müssen, z. B. einmal pro Frame – oder während eines bestimmten Zeitraums, z. B. während des Setups von Spielen. Wenn dies der Fall ist, ist der obige Code an, was Sie.

In unserem Codebeispiel haben wir die Verwendung beider Modelle pädagogischer Natur zu veranschaulichen. Hier, wir ein Ereignis abonnieren, die auf dem neuesten Stand Oberfläche Mesh-Daten zu erhalten, wenn das System eine Änderung erkennt.

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

Unser Beispiel ist auch auf diese Ereignisse reagieren konfiguriert. Betrachten Sie wie wir dies getan haben.

**HINWEIS:** Dies möglicherweise nicht die effizienteste Methode für Ihre app, die Mesh-Daten verarbeiten. Dieser Code wird aus Gründen der Übersichtlichkeit geschrieben und ist nicht optimiert.

Die Oberfläche Mesh-Daten werden in einer nur-Lese Zuordnung, die speichert bereitgestellt [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) -Objekte mit [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) als Schlüsselwerte.

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

Um diese Daten zu verarbeiten, geht es zuerst für die Schlüsselwerte, die nicht in der Sammlung. Informationen zur Speicherung der das in unserem Beispiel-app werden weiter unten in diesem Thema angezeigt.

```cpp
// Process surface adds and updates.
for (const auto& pair : surfaceCollection)
{
    auto id = pair->Key;
    auto surfaceInfo = pair->Value;

    if (m_meshCollection->HasSurface(id))
    {
        // Update existing surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
    else
    {
        // New surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
}
```

Wir müssen auch Oberfläche Gitter zu entfernen, die in der Entwurfsoberfläche Mesh-Sammlung sind, aber, die nicht in der Auflistung nicht mehr. Zu diesem Zweck müssen wir möchten Sie etwas Ähnliches wie das Gegenteil von was wir gerade gezeigt haben für das Hinzufügen und Aktualisieren von Gitter. Schleife in unseren app Sammlung und Prüfung, ob die **Guid** wir haben in der Auflistung ist. Wenn es sich nicht in der Auflistung ist, können wir es aus unsere entfernen.

Von der Ereignishandler in AppMain.cpp:

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

Die Implementierung des Mesh-Bereinigung in RealtimeSurfaceMeshRenderer.cpp:

```cpp
void RealtimeSurfaceMeshRenderer::PruneMeshCollection(IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection)
{
    std::lock_guard<std::mutex> guard(m_meshCollectionLock);
    std::vector<Guid> idsToRemove;

    // Remove surfaces that moved out of the culling frustum or no longer exist.
    for (const auto& pair : m_meshCollection)
    {
        const auto& id = pair.first;
        if (!surfaceCollection->HasKey(id))
        {
            idsToRemove.push_back(id);
        }
    }

    for (const auto& id : idsToRemove)
    {
        m_meshCollection.erase(id);
    }
}
```

### <a name="acquire-and-use-surface-mesh-data-buffers"></a>Abrufen und Verwenden von Surface-Netz von Datenpuffern

Die Oberfläche von meshinformationen war so einfach wie das Abrufen einer Datensammlung und die Verarbeitung der Updates für diese Sammlung. Nun, wir uns ausführlich auf, wie Sie die Daten verwenden können.

In unserem Codebeispiel haben wir die Oberfläche Netze für das Rendering zu verwenden. Dies ist ein häufiges Szenario für occluding Hologramme hinter realen Flächen. Sie können auch Rendern der Gitter oder verarbeitete Versionen zu rendern, um dem Benutzer anzuzeigen, welche Bereiche der werden Raum überprüft, bevor Sie beginnen, App- oder Spiele-Funktionalität bereitgestellt.

Im Codebeispiel wird der Prozess beim Empfang von Updates für Surface-Netz aus dem Ereignishandler, die wir im vorherigen Abschnitt beschrieben. Die wichtige Zeile des Codes in dieser Funktion ist der Aufruf zum Aktualisieren der Oberfläche *mesh*: zu diesem Zeitpunkt haben wir bereits die Mesh-Informationen verarbeitet, und Sie können die Vertex- und Daten für die Verwendung abgerufen werden, wie wir nach Bedarf.

Von RealtimeSurfaceMeshRenderer.cpp:

```cpp
void RealtimeSurfaceMeshRenderer::AddOrUpdateSurface(Guid id, SpatialSurfaceInfo^ newSurface)
{
    auto options = ref new SpatialSurfaceMeshOptions();
    options->IncludeVertexNormals = true;

    auto createMeshTask = create_task(newSurface->TryComputeLatestMeshAsync(1000, options));
    createMeshTask.then([this, id](SpatialSurfaceMesh^ mesh)
    {
        if (mesh != nullptr)
        {
            std::lock_guard<std::mutex> guard(m_meshCollectionLock);
            '''m_meshCollection[id].UpdateSurface(mesh);'''
        }
    }, task_continuation_context::use_current());
}
```

Unserem Beispielcode wurde entwickelt, damit eine Datenklasse **SurfaceMesh**, Handles Mesh Daten verarbeiten und rendern. Diese Meshes sind, was die **RealtimeSurfaceMeshRenderer** tatsächlich hält eine Zuordnung. Jeweils enthält einen Verweis auf die SpatialSurfaceMesh er stammt, und wir verwenden sie jedes Mal, die Zugriff auf die Mesh-Vertex oder Index-Puffer oder eine Transformation für das Netz abrufen müssen. Vorerst flag wir das Netz als ein Update erforderlich.

Von SurfaceMesh.cpp:

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

Beim nächsten Mesh aufgefordert wird, selbst zeichnen wird das Flag zuerst überprüft. Wenn ein Update erforderlich ist, werden die Vertex- und Indexpuffer auf der GPU aktualisiert werden.

```cpp
void SurfaceMesh::CreateDeviceDependentResources(ID3D11Device* device)
{
    m_indexCount = m_surfaceMesh->TriangleIndices->ElementCount;
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }
```

Zunächst rufen wir die Rohdaten-Puffer:

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

Klicken Sie dann erstellen Puffer, die wir Direct3D-Gerät mit den Netzdaten die HoloLens:

```cpp
CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, positions, m_vertexPositions.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, normals,   m_vertexNormals.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_INDEX_BUFFER,  indices,   m_triangleIndices.GetAddressOf());

    // Create a constant buffer to control mesh position.
    CD3D11_BUFFER_DESC constantBufferDesc(sizeof(SurfaceTransforms), D3D11_BIND_CONSTANT_BUFFER);
    DX::ThrowIfFailed(
        device->CreateBuffer(
            &constantBufferDesc,
            nullptr,
            &m_modelTransformBuffer
            )
        );

    m_loadingComplete = true;
}
```

**HINWEIS:** Die CreateDirectXBuffer-Hilfsfunktion, der im vorherigen Codeausschnitt verwendet wird finden Sie im Codebeispiel Oberfläche zuordnen: SurfaceMesh.cpp, GetDataFromIBuffer.h. Der ressourcenerstellung Gerät ist jetzt abgeschlossen, und das Netz gilt werden geladen und bereit für die Aktualisierung und zu rendern.

### <a name="update-and-render-surface-meshes"></a>Aktualisieren und zu Rendern der Entwurfsoberfläche Gitter

Unsere SurfaceMesh-Klasse verfügt über eine spezielle Update-Funktion. Jede [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) verfügt über eine eigene Transformation und in diesem Beispiel verwendet das aktuelle Koordinatensystem für unsere **SpatialStationaryReferenceFrame** , die Transformation abzurufen. Anschließend wird den Modell-Konstantenpuffer auf der GPU aktualisiert.

```cpp
void SurfaceMesh::UpdateTransform(
    ID3D11DeviceContext* context,
    SpatialCoordinateSystem^ baseCoordinateSystem
    )
{
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }

    XMMATRIX transform = XMMatrixIdentity();

    auto tryTransform = m_surfaceMesh->CoordinateSystem->TryGetTransformTo(baseCoordinateSystem);
    if (tryTransform != nullptr)
    {
        transform = XMLoadFloat4x4(&tryTransform->Value);
    }

    XMMATRIX scaleTransform = XMMatrixScalingFromVector(XMLoadFloat3(&m_surfaceMesh->VertexPositionScale));

    XMStoreFloat4x4(
        &m_constantBufferData.vertexWorldTransform,
        XMMatrixTranspose(
            scaleTransform * transform
            )
        );

    // Normals don't need to be translated.
    XMMATRIX normalTransform = transform;
    normalTransform.r[3] = XMVectorSet(0.f, 0.f, 0.f, XMVectorGetW(normalTransform.r[3]));
    XMStoreFloat4x4(
        &m_constantBufferData.normalWorldTransform,
        XMMatrixTranspose(
            normalTransform
        )
        );

    if (!m_loadingComplete)
    {
        return;
    }

    context->UpdateSubresource(
        m_modelTransformBuffer.Get(),
        0,
        NULL,
        &m_constantBufferData,
        0,
        0
        );
}
```

Wenn es Zeit, die zum Rendern der Entwurfsoberfläche Gitter ist, führen wir einige vorbereitende arbeiten, vor dem Rendern der Auflistung. Wir richten die Shader-Pipeline für die aktuelle Rendering-Konfiguration, und richten wir die Eingabe-Assembler-Stufe. Beachten Sie, dass die Hilfsklasse holographic Kamera **CameraResources.cpp** bereits eingerichtet hat den Konstantenpuffer Ansichts-und Projektionsmatrix jetzt.

Von **RealtimeSurfaceMeshRenderer::Render**:

```cpp
auto context = m_deviceResources->GetD3DDeviceContext();

context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach our vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
    );

// The constant buffer is per-mesh, and will be set as such.

if (depthOnly)
{
    // Explicitly detach the later shader stages.
    context->GSSetShader(nullptr, nullptr, 0);
    context->PSSetShader(nullptr, nullptr, 0);
}
else
{
    if (!m_usingVprtShaders)
    {
        // Attach the passthrough geometry shader.
        context->GSSetShader(
            m_geometryShader.Get(),
            nullptr,
            0
            );
    }

    // Attach our pixel shader.
    context->PSSetShader(
        m_pixelShader.Get(),
        nullptr,
        0
        );
}
```

Sobald dies geschehen ist, werden wir auf unsere Gitter Schleife und teilen Sie jeweils auf sich selbst zu zeichnen. **HINWEIS:** Dieser Beispielcode ist nicht optimiert, um jede Art von Frustums culling zu verwenden, aber Sie sollten diese Funktion in Ihrer app einschließen.

```cpp
std::lock_guard<std::mutex> guard(m_meshCollectionLock);

auto device = m_deviceResources->GetD3DDevice();

// Draw the meshes.
for (auto& pair : m_meshCollection)
{
    auto& id = pair.first;
    auto& surfaceMesh = pair.second;

    surfaceMesh.Draw(device, context, m_usingVprtShaders, isStereo);
}
```

Die einzelne Gitter sind verantwortlich für das Einrichten der Vertex- und Puffer Stride und Konstantenpuffer des Modell-Transformation. Wie bei der sich drehenden Würfels in der Windows Holographic-app-Vorlage, Rendern wir stereoskopische Puffern, die mit der Instanziierung.

Von **SurfaceMesh::Draw**:

```cpp
// The vertices are provided in {vertex, normal} format

const auto& vertexStride = m_surfaceMesh->VertexPositions->Stride;
const auto& normalStride = m_surfaceMesh->VertexNormals->Stride;

UINT strides [] = { vertexStride, normalStride };
UINT offsets [] = { 0, 0 };
ID3D11Buffer* buffers [] = { m_vertexPositions.Get(), m_vertexNormals.Get() };

context->IASetVertexBuffers(
    0,
    ARRAYSIZE(buffers),
    buffers,
    strides,
    offsets
    );

const auto& indexFormat = static_cast<DXGI_FORMAT>(m_surfaceMesh->TriangleIndices->Format);

context->IASetIndexBuffer(
    m_triangleIndices.Get(),
    indexFormat,
    0
    );

context->VSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

if (!usingVprtShaders)
{
    context->GSSetConstantBuffers(
        0,
        1,
        m_modelTransformBuffer.GetAddressOf()
        );
}

context->PSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

context->DrawIndexedInstanced(
    m_indexCount,       // Index count per instance.
    isStereo ? 2 : 1,   // Instance count.
    0,                  // Start index location.
    0,                  // Base vertex location.
    0                   // Start instance location.
    );
```

### <a name="rendering-choices-with-surface-mapping"></a>Rendern von Funktionen mit Oberfläche zuordnen

Das Zuordnen von Surface-Codebeispiel bietet verdecken nur Rendern der Entwurfsoberfläche Mesh-Daten und auf dem Bildschirm Rendern der Entwurfsoberfläche Mesh-Daten. Welchen Pfad Sie auswählen – oder beides – hängt von Ihrer Anwendung. Beide Konfigurationen in diesem Dokument erläutert.

**Rendering verdecken Puffer für die holographic Auswirkungen**

Starten Sie durch die renderzielansicht für die aktuelle virtuelle Kamera zu deaktivieren.

Von AppMain.cpp:

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

Dies ist eine "vor dem eigentlichen Rendern" übergeben. Hier erstellen wir einen Puffer verdecken, werden aufgefordert, den Mesh-Renderer zum Rendern von nur Tiefe. In dieser Konfiguration nicht wir eine renderzielansicht Anfügen und die Mesh-Renderer die Pixel-Shader-Stufe an **"nullptr"** so, dass die GPU gar nicht Pixel gezeichnet werden soll. Die Geometrie werden gerastert im Tiefenpuffer, und die Grafikpipeline wird es beendet.

```cpp
// Pre-pass rendering: Create occlusion buffer from Surface Mapping data.
context->ClearDepthStencilView(pCameraResources->GetSurfaceDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to null, and set the depth target occlusion buffer.
// We will use this same buffer as a shader resource when drawing holograms.
context->OMSetRenderTargets(0, nullptr, pCameraResources->GetSurfaceOcclusionDepthStencilView());

// The first pass is a depth-only pass that generates an occlusion buffer we can use to know which
// hologram pixels are hidden behind surfaces in the environment.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), true);
```

Wir können Hologramme zeichnen, mit einer zusätzlichen Tiefentest für Puffer verdecken Oberfläche zuordnen. In diesem Codebeispiel Rendern wir Pixel für den Cube eine andere Farbe, wenn sie sich hinter einer Fläche befinden.

Von AppMain.cpp:

```cpp
// Hologram rendering pass: Draw holographic content.
context->ClearDepthStencilView(pCameraResources->GetHologramDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target, and set the depth target drawing buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetHologramDepthStencilView());

// Render the scene objects.
// In this example, we draw a special effect that uses the occlusion buffer we generated in the
// Pre-Pass step to render holograms using X-Ray Vision when they are behind physical objects.
m_xrayCubeRenderer->Render(
    pCameraResources->IsRenderingStereoscopic(),
    pCameraResources->GetSurfaceOcclusionShaderResourceView(),
    pCameraResources->GetHologramOcclusionShaderResourceView(),
    pCameraResources->GetDepthTextureSamplerState()
    );
```

Basierend auf Code SpecialEffectPixelShader.hlsl:

```cpp
// Draw boundaries
min16int surfaceSum = GatherDepthLess(envDepthTex, uniSamp, input.pos.xy, pixelDepth, input.idx.x);

if (surfaceSum <= -maxSum)
{
    // The pixel and its neighbors are behind the surface.
    // Return the occluded 'X-ray' color.
    return min16float4(0.67f, 0.f, 0.f, 1.0f);
}
else if (surfaceSum < maxSum)
{
    // The pixel and its neighbors are a mix of in front of and behind the surface.
    // Return the silhouette edge color.
    return min16float4(1.f, 1.f, 1.f, 1.0f);
}
else
{
    // The pixel and its neighbors are all in front of the surface.
    // Return the color of the hologram.
    return min16float4(input.color, 1.0f);
}
```

**Hinweis**: Für unsere **GatherDepthLess** -Routine, finden Sie im Codebeispiel Oberfläche zuordnen: SpecialEffectPixelShader.hlsl.

**Rendering-Oberfläche Mesh-Daten auf dem Bildschirm**

Wir können auch einfach nur die Oberfläche Gitter den Puffern Stereo Anzeige zeichnen. Es wurde entschieden, zeichnen Sie die vollständige Gesichtern mit Beleuchtung, aber Sie können zum Drahtmodell zu zeichnen, verarbeiten Gitter vor dem Rendern, Anwenden einer Texturmaps und so weiter.

Unser Codebeispiel teilt, die Mesh-Renderer zum Zeichnen der Auflistung. Dieses Mal nicht wir bestanden Tiefe nur angeben, damit einen Pixel-Shader Anfügen und verwenden die Ziele, die wir angegeben, für die aktuelle virtuelle Kamera die Rendering-Pipeline abgeschlossen wird.

```cpp
// SR mesh rendering pass: Draw SR mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a>Siehe auch
* [Erstellen eines holographic DirectX-Projekts](creating-a-holographic-directx-project.md)
* [Windows.Perception.Spatial API](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
