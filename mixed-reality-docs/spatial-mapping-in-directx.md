---
title: Räumliche Zuordnung in DirectX
description: Erläutert, wie die räumliche Zuordnung in Ihrer DirectX-App implementiert wird. Dies umfasst eine ausführliche Erläuterung der Beispielanwendung für räumliche Zuordnung, die im universelle Windows-Plattform SDK enthalten ist.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, räumliche Zuordnung, Umgebung, Interaktion, DirectX, WinRT, API, Beispielcode, UWP, SDK, Exemplarische Vorgehensweise
ms.openlocfilehash: db3f1464158c04127e456cadd5fb633336909344
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63550696"
---
# <a name="spatial-mapping-in-directx"></a>Räumliche Zuordnung in DirectX

In diesem Thema wird beschrieben, wie Sie eine [räumliche Zuordnung](spatial-mapping.md) in Ihrer DirectX-App implementieren. Dies umfasst eine ausführliche Erläuterung der Beispielanwendung für räumliche Zuordnung, die im universelle Windows-Plattform SDK enthalten ist.

In diesem Thema wird Code aus dem [holographicspatialmapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) -UWP-Codebeispiel verwendet.

>[!NOTE]
>Die Code Ausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung C++von/CX anstelle von C + +17- C++kompatibler/WinRT, wie Sie in der [ C++ Holographic-Projektvorlage](creating-a-holographic-directx-project.md)verwendet werden.  Die Konzepte sind äquivalent für ein C++/WinRT-Projekt, obwohl Sie den Code übersetzen müssen.

## <a name="directx-development-overview"></a>DirectX-Entwicklungs Übersicht

Die native Anwendungsentwicklung für räumliche Zuordnung verwendet die APIs im [Windows. perception. Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) -Namespace. Diese APIs bieten vollständige Kontrolle über die Funktionalität räumlicher Mapping in einer Weise, die direkt mit den von [Unity](spatial-mapping-in-unity.md)verfügbar gemachten räumlichen Mapping-APIs vergleichbar ist.

### <a name="perception-apis"></a>Perception-APIs

Folgende primäre Typen werden für die Entwicklung räumlicher Mapping bereitgestellt:
* [Spatialsurfaceobserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) stellt Informationen zu Oberflächen in anwendungsspezifischen Bereichen des Raums in der Nähe des Benutzers in Form von spatialsurfaceinfo-Objekten bereit.
* [Spatialsurfaceinfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) beschreibt eine einzelne räumliche Oberfläche, einschließlich einer eindeutigen ID, eines umgebenden Volumes und einer Zeit der letzten Änderung. Auf Anforderung wird ein spatialsurfakemesh asynchron bereitgestellt.
* [Spatialsurfakemeshoptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) enthält Parameter, mit denen die von spatialsurfakeinfo angeforderten spatialsurfaesh-Objekte angepasst werden.
* [Spatialsurfacemesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) stellt die Mesh-Daten für eine einzelne räumliche Oberfläche dar. Die Daten für Scheitelpunkt Positionen, Scheitelpunkt normale und Dreieck Indizes sind in dem Element spatialsurfakemeschbuffer-Objekten enthalten.
* [Spatialsurfakemeschbuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) umschließt einen einzelnen Typ von Mesh-Daten.

Beim Entwickeln einer Anwendung, die diese APIs verwendet, sieht Ihr grundlegender Programmablauf wie folgt aus (wie in der unten beschriebenen Beispielanwendung gezeigt):
- **Einrichten von spatialsurfaceobserver**
  - Aufrufen von [requestaccessasync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), um sicherzustellen, dass der Benutzer die Berechtigung zum Verwenden der räumlichen Zuordnungsfunktionen des Geräts für die Anwendung erteilt hat.
  - Instanziieren Sie ein spatialsurfaceobserver-Objekt.
  - Aufrufen von [setboundingvolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) , um die Bereiche anzugeben, in denen Sie Informationen über räumliche Oberflächen benötigen. Diese Bereiche können Sie in Zukunft ändern, indem Sie diese Funktion einfach erneut aufrufen. Jede Region wird mit einem [spatialboundingvolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx)angegeben.
  - Registrieren Sie sich für das [observedsurfaceschangi-Ereignis](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) , das ausgelöst wird, wenn neue Informationen über die räumlichen Oberflächen in den von Ihnen angegebenen Bereichen des Raums verfügbar sind.
- **Prozess-observedsurfaceschge-Ereignisse**
  - Aufrufen von [getobservedoberflächen](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) in Ihrem Ereignishandler, um eine Zuordnung der spatialsurfakeinfo-Objekte zu erhalten. Mithilfe dieser Karte können Sie die Datensätze aktualisieren, in denen räumliche Oberflächen [in der Benutzerumgebung vorhanden](spatial-mapping.md#mesh-caching)sind.
  - Für jedes spatialsurfaceinfo-Objekt können Sie [trygetbounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) Abfragen, um die räumlichen Blöcke der Oberfläche zu ermitteln, die in einem [räumlichen Koordinatensystem](coordinate-systems.md) Ihrer Wahl ausgedrückt werden.
  - Wenn Sie ein Mesh für eine räumliche Oberfläche anfordern möchten, wenden Sie sich an [trycomputelatestmeshasync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx). Sie können Optionen angeben, indem Sie die gewünschte Dichte der Dreiecke und das Format der zurückgegebenen Mesh-Daten angeben.
- **Gitter empfangen und verarbeiten**
  - Jeder Aufrufen von trycomputelatestmeshasync gibt ein spatialsurfakemesh-Objekt zurück.
  - Von diesem Objekt aus können Sie auf die enthaltenen spatialsurfaeschbuffer-Objekte zugreifen, um auf die Dreiecks Indizes, die Scheitelpunkt Positionen und (falls angefordert) vertexnormale des Netzes zuzugreifen. Diese Daten befinden sich in einem Format, das direkt mit den [Direct3D 11-APIs](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) kompatibel ist, die zum Rendern von Netzen verwendet werden.
  - Von hier aus kann die Anwendung optional eine Analyse oder [Verarbeitung](spatial-mapping.md#mesh-processing) der Mesh-Daten durchführen und diese zum [Rendern](spatial-mapping.md#rendering) und zum Auftreten von physikalischer und- [Kollisionen](spatial-mapping.md#raycasting-and-collision)verwenden.
  - Ein wichtiges Detail ist, dass Sie eine Skalierung auf die mesvertexpositionen anwenden müssen (z. b. im Vertexshader, der zum Rendern der Meshes verwendet wird), um Sie von den optimierten ganzzahligen Einheiten, in denen Sie im Puffer gespeichert sind, in Meter zu konvertieren. Sie können diese Skala abrufen, indem Sie [vertexpositionscale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)aufrufen.

### <a name="troubleshooting"></a>Problembehandlung
* Vergessen Sie nicht, Mesh-Vertex-Positionen in Ihrem Vertexshader zu skalieren, indem Sie die von [spatialsurfakemesh. vertexpositionscale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx) zurückgegebene Skala verwenden.

## <a name="spatial-mapping-code-sample-walkthrough"></a>Exemplarische Vorgehensweise zum Codebeispiel für räumliche Zuordnung

Das Codebeispiel für die [holografische räumliche Zuordnung](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) enthält Code, den Sie verwenden können, um mit dem Laden von Oberflächen Netzen in Ihre APP zu beginnen, einschließlich der Infrastruktur zum Verwalten und Rendern von Oberflächen Netzen.

Nun erfahren Sie, wie Sie Ihrer DirectX-App Oberflächen Zuordnungsfunktionen hinzufügen. Sie können diesen Code dem Vorlagen Projekt für die [Windows Holographic-App](creating-a-holographic-directx-project.md) hinzufügen. Alternativ können Sie das oben erwähnte Codebeispiel durchsuchen. Dieses Codebeispiel basiert auf der Windows Holographic-App-Vorlage.

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>Einrichten Ihrer APP für die Verwendung der spatialperception-Funktion

Ihre APP muss die Funktion für räumliche Zuordnung verwenden können. Dies ist erforderlich, da das räumliche Mesh eine Darstellung der Benutzerumgebung ist, die als private Daten betrachtet werden kann. Deklarieren Sie diese Funktion in der Datei "Package. appxmanifest" für Ihre APP. Im Folgenden ein Beispiel:

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

Die Funktion stammt aus dem **uap2** -Namespace. Um Zugriff auf diesen Namespace in ihrem Manifest zu erhalten, fügen Sie ihn als *xlmns* -Attribut &lt;in das Paket >-Element ein. Im Folgenden ein Beispiel:

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a>Überprüfen der Funktions Unterstützung für räumliche Zuordnung

Windows Mixed Reality unterstützt eine große Bandbreite von Geräten, darunter Geräte, die keine räumliche Zuordnung unterstützen. Wenn Ihre APP eine räumliche Zuordnung verwenden oder eine räumliche Zuordnung verwenden muss, sollte Sie zum Bereitstellen von Funktionen überprüfen, ob die räumliche Zuordnung unterstützt wird, bevor Sie versuchen, Sie zu verwenden. Wenn z. b. eine räumliche Zuordnung für Ihre Mixed Reality-App erforderlich ist, sollte eine Meldung angezeigt werden, wenn ein Benutzer versucht, die Anwendung auf einem Gerät ohne räumliche Zuordnung durchführen zu müssen. Oder Sie können Ihre eigene virtuelle Umgebung möglicherweise anstelle der Umgebung des Benutzers Rendering, sodass Sie ein ähnliches Verhalten wie bei der Verfügbarkeit der räumlichen Zuordnung bietet. In jedem Fall ermöglicht diese API Ihrer APP, zu erkennen, wann Sie keine räumlichen Zuordnungsdaten erhält, und antwortet auf die entsprechende Weise.

Stellen Sie zunächst sicher, dass der UWP-Vertrag auf der Ebene 4 oder höher ist, und fordern Sie dann spatialsurfaceobserver:: IsSupported () an, um das aktuelle Gerät auf Unterstützung für räumliche Zuordnung zu überprüfen. Dies wird im Kontext des Code Beispiels für die [Holographic-Zuordnung für räumliche Daten](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) beschrieben. Die Unterstützung wird unmittelbar vor dem Anfordern des Zugriffs geprüft.

Die spatialsurfaceobserver:: IsSupported ()-API ist ab der SDK-Version 15063 verfügbar. Richten Sie ggf. das Projekt auf die Platt Form Version 15063 zurück, bevor Sie diese API verwenden.

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

Beachten Sie Folgendes: Wenn der UWP-Vertrag niedriger als Ebene 4 ist, sollte die APP so vorgehen, als ob das Gerät eine räumliche Zuordnung durchführen kann.

### <a name="request-access-to-spatial-mapping-data"></a>Zugriff auf räumliche Zuordnungsdaten anfordern

Ihre APP muss die Berechtigung für den Zugriff auf räumliche Zuordnungsdaten anfordern, bevor Sie versuchen, einen Oberflächen Beobachter zu erstellen. Im folgenden finden Sie ein Beispiel, das auf dem Codebeispiel für die Oberflächen Zuordnung basiert. weitere Details finden Sie weiter unten auf dieser Seite:

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

### <a name="create-a-surface-observer"></a>Erstellen eines Oberflächen Beobachters

Der **Windows::P erception:: Spatial:: Oberflächen** -Namespace enthält die [spatialsurfaceobserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) -Klasse, mit der ein oder mehrere Volumes beobachtet werden, die Sie in einem [spatialcoordinatesystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx)angeben. Verwenden Sie eine [spatialsurfaceobserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) -Instanz, um in Echtzeit auf Oberflächen Mesh-Daten zuzugreifen.

Aus **appmain. h**:

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

Wie bereits im vorherigen Abschnitt erwähnt, müssen Sie den Zugriff auf räumliche Zuordnungsdaten anfordern, bevor Sie von Ihrer APP verwendet werden können. Dieser Zugriff wird automatisch auf den hololens gewährt.

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

Als nächstes müssen Sie den Oberflächen Beobachter so konfigurieren, dass er ein bestimmtes Begrenzungs Volume beobachtet. Hier wird ein Feld mit 20 x 20 x 5 Metern betrachtet, das sich am Ursprung des Koordinatensystems befindet.

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

Beachten Sie, dass Sie stattdessen mehrere Begrenzungs Volumes festlegen können.

*Dies ist Pseudocode:*

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

Es ist auch möglich, andere umgebende Formen (z. b. eine ansichtsansicht) oder ein Begrenzungsfeld zu verwenden, das keine Achsen Ausrichtung ist.

*Dies ist Pseudocode:*

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

Wenn Ihre APP etwas anders ausführen muss, wenn keine Oberflächen Zuordnungsdaten verfügbar sind, können Sie Code schreiben, um auf den Fall zu reagieren, in dem [spatialpertionaccessstatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) nicht **zulässig** ist, z. b. auf PCs mit immersiver Verwendung nicht zulässig. Geräte, die angefügt sind, weil diese Geräte nicht über Hardware für räumliche Zuordnung verfügen. Für diese Geräte sollten Sie sich stattdessen auf die räumliche Phase stützen, um Informationen zur Umgebung und Gerätekonfiguration des Benutzers zu erhalten.

### <a name="initialize-and-update-the-surface-mesh-collection"></a>Initialisieren und Aktualisieren der Surface-Mesh-Auflistung

Wenn der Oberflächen Beobachter erfolgreich erstellt wurde, können wir mit dem Initialisieren der Oberflächen Gitter Auflistung fortfahren. Hier verwenden wir die Pull Model-API, um den aktuellen Satz von beobachteten Oberflächen sofort abzurufen:

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

Es ist auch ein Push-Modell verfügbar, um Oberflächen Mesh-Daten zu erhalten. Sie können Ihre APP so entwerfen, dass nur das Pull-Modell verwendet wird, wenn Sie sich entscheiden. in diesem Fall rufen Sie alle so oft, einmal pro Frame oder innerhalb eines bestimmten Zeitraums, z. b. während der Spiel Einrichtung, Daten ab. Wenn dies der Fall ist, ist der obige Code das, was Sie benötigen.

In unserem Codebeispiel haben wir uns entschieden, die Verwendung beider Modelle zu pädagogischen Zwecken zu veranschaulichen. Hier abonnieren wir ein Ereignis, um aktuelle Oberflächen Mesh-Daten zu erhalten, wenn das System eine Änderung erkennt.

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

Unser Codebeispiel ist auch so konfiguriert, dass auf diese Ereignisse reagiert wird. Sehen wir uns an, wie wir dies tun.

**HINWEIS:** Dies ist möglicherweise nicht die effizienteste Methode, mit der Ihre APP Mesh-Daten verarbeiten kann. Dieser Code wird aus Gründen der Übersichtlichkeit geschrieben und ist nicht optimiert.

Die Oberflächen Mesh-Daten werden in einer schreibgeschützten Zuordnung bereitgestellt, in der [spatialsurfaceinfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) -Objekte mithilfe von [Platform:: GUIDs](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) als Schlüsselwerte gespeichert werden.

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

Um diese Daten zu verarbeiten, betrachten wir zuerst die Schlüsselwerte, die nicht in unserer Sammlung sind. Weitere Informationen zum Speichern der Daten in unserer Beispiel-App finden Sie weiter unten in diesem Thema.

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

Wir müssen auch Oberflächen Netze entfernen, die in unserer Oberflächen Mesh-Auflistung enthalten sind, aber nicht mehr in der System Sammlung enthalten sind. Zu diesem Zweck müssen wir etwas tun, das dem Gegenteil ähnelt, was wir soeben zum Hinzufügen und Aktualisieren von Meshes gezeigt haben. Wir durchlaufen die Sammlung unserer APP und überprüfen, ob die **GUID** in der System Sammlung enthalten ist. Wenn er sich nicht in der System Sammlung befindet, entfernen wir ihn von uns.

Aus unserem Ereignishandler in appmain. cpp:

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

Die Implementierung des Gitter Bereinigungs in realtimesurfakemeshrenderer. cpp:

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

### <a name="acquire-and-use-surface-mesh-data-buffers"></a>Erfassen und Verwenden von Oberflächen Mesh-Daten Puffern

Das Abrufen der Oberflächen Mesh-Informationen war so einfach wie das Abrufen von Datenerfassung und das Verarbeiten von Aktualisierungen für diese Sammlung. Nun erfahren Sie, wie Sie die Daten verwenden können.

In unserem Codebeispiel haben wir uns entschieden, die Oberflächen Netze für das Rendering zu verwenden. Dies ist ein gängiges Szenario zum einleben von holograms hinter realen Oberflächen. Sie können auch die Meshes und die verarbeiteten Versionen von Ihnen darstellen, um dem Benutzer anzuzeigen, welche Bereiche des Raums gescannt werden, bevor Sie mit der Bereitstellung von APP-oder Spielfunktionen beginnen.

Das Codebeispiel startet den Prozess, wenn er Oberflächen Mesh-Aktualisierungen von dem Ereignishandler empfängt, den wir im vorherigen Abschnitt beschrieben haben. Die wichtige Codezeile in dieser Funktion ist der Aufruf zum Aktualisieren des Oberflächen *Netzes*: bisher haben wir die Mesh-Informationen bereits verarbeitet, und wir sind im Begriff, den Scheitelpunkt und die Indexdaten für die Verwendung nach Bedarf abzurufen.

Aus realtimesurfakemeshrenderer. cpp:

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

Der Beispielcode ist so konzipiert, dass eine Datenklasse, **surfacemesh**, Mesh-Datenverarbeitungs-und-Rendering behandelt. Diese Netze stellen den **realtimesurfakemeshrenderer** tatsächlich eine Karte dar. Jeder verfügt über einen Verweis auf den spatialsurfakemesh, von dem er stammt, und wir verwenden ihn immer dann, wenn wir auf den Gitter Scheitelpunkt oder Index Puffer zugreifen müssen oder eine Transformation für das Mesh abrufen müssen. Vorerst wird das Mesh als Update erforderlich gekennzeichnet.

Aus "surfakemesh. cpp":

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

Wenn das Mesh das nächste Mal aufgefordert wird, sich selbst zu zeichnen, prüft es zuerst das Flag. Wenn ein Update erforderlich ist, werden die Vertex-und Index Puffer auf der GPU aktualisiert.

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

Zunächst rufen wir die Rohdaten Puffer ab:

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

Anschließend erstellen wir Direct3D-Geräte Puffer mit den Netz Daten, die von den hololens bereitgestellt werden:

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

**HINWEIS:** Informationen zu der im vorherigen Code Ausschnitt verwendeten Hilfsfunktion "featedirectxbuffer" finden Sie im Codebeispiel für die Oberflächen Zuordnung: "Surfakemesh. cpp", "getdatafromibuffer. h". Die Geräte Ressourcen Erstellung ist nun abgeschlossen, und das Mesh wird als geladen und bereit für Update und Rendering.

### <a name="update-and-render-surface-meshes"></a>Aktualisieren und renderoberflächen-Netzen

Unsere surfacemesh-Klasse verfügt über eine spezialisierte Update-Funktion. Jede [spatialsurfaesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) hat eine eigene Transformation, und in unserem Beispiel wird das aktuelle Koordinatensystem für den **spatialstationaryreferenceframe** verwendet, um die Transformation zu erhalten. Anschließend wird der Modell Konstante Puffer auf der GPU aktualisiert.

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

Wenn es an der Zeit ist, Oberflächen Netze zu rendern, führen wir vor dem Rendern der Auflistung einige Vorbereitungsaufgaben durch. Wir richten die Shader-Pipeline für die aktuelle renderingkonfiguration ein und richten die Eingabe Assembler-Stufe ein. Beachten Sie, dass die Hilfsklasse der Holographic-Kamera " **cameraresources. cpp** " bereits den Ansichts-/Projektions Konstanten-Puffer bereits eingerichtet hat.

Aus **realtimesurfakemeshrenderer:: Rendering**:

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

Nachdem dies geschehen ist, werden wir unsere Netzen durchlaufen und jede einzelne zeichnen. **HINWEIS:** Dieser Beispielcode ist nicht für die Verwendung einer beliebigen Art von Frustum-culelt optimiert, aber Sie sollten dieses Feature in Ihre APP einschließen.

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

Die einzelnen Netzen sind für das Einrichten des Vertex-und Index Puffers, des STRIDE-und des Modell Transformations Konstanten Puffers verantwortlich. Wie bei dem spincube in der Windows Holographic-App-Vorlage werden wir mithilfe der Instanziierung zu stereoskopischen Puffern.

Von **surfakemesh::D RAW**:

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

### <a name="rendering-choices-with-surface-mapping"></a>Renderingoptionen mit Oberflächen Zuordnung

Das Codebeispiel für die Oberflächen Zuordnung bietet Code für das reine Rendering von Oberflächen Netz Daten und für das Bildschirm Rendering von Oberflächen Mesh-Daten. Der von Ihnen gewählte Pfad bzw. beides hängt von Ihrer Anwendung ab. In diesem Dokument werden beide Konfigurationen erläutert.

**Rendern von Okklusions Puffern für Holographic Effect**

Beginnen Sie, indem Sie die renderzielansicht für die aktuelle virtuelle Kamera löschen.

Aus appmain. cpp:

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

Dies ist ein "Pre-Rendering"-Durchlauf. Hier erstellen Sie einen oksions Puffer, indem Sie den Mesh-Renderer bitten, nur Tiefe zu Renderern. In dieser Konfiguration wird eine renderzielansicht nicht angefügt, und der Mesh-Renderer legt die Pixel-Shader-Stufe auf **nullptr** fest, damit die GPU keine Pixel zeichnen kann. Die Geometrie wird in den tiefen Puffer gerengt, und die Grafik Pipeline wird dort angehalten.

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

Wir können holograms mit einem zusätzlichen tiefen Test für den cloudverzeichnungs-Puffer für die Oberflächen Zuordnung zeichnen. In diesem Codebeispiel werden Pixel im Cube in einer anderen Farbe dargestellt, wenn Sie sich hinter einer Oberfläche befinden.

Aus appmain. cpp:

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

Basierend auf dem Code aus specialeffectpixelshader. HLSL:

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

**Hinweis**: Informationen zu unserer **gatherdepthless** -Routine finden Sie im Codebeispiel für die Oberflächen Zuordnung: Specialeffectpixelshader. HLSL.

**Rendern von Oberflächen Mesh-Daten für die Anzeige**

Wir können auch einfach die Oberfläche für die Stereo Anzeige Puffer zeichnen. Wir haben uns entschieden, vollständige Gesichter mit Beleuchtung zu zeichnen, aber Sie können einen Wireframe zeichnen, Netzen vor dem Rendering verarbeiten, eine Textur Map anwenden usw.

Hier weist unser Codebeispiel den Mesh-Renderer an, die Auflistung zu zeichnen. Dieses Mal geben wir keinen tiefen Durchlauf an, sondern fügen einen PixelShader an und vervollständigen die Renderingpipeline mithilfe der Ziele, die wir für die aktuelle virtuelle Kamera angegeben haben.

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
* [Erstellen eines holographischen DirectX-Projekts](creating-a-holographic-directx-project.md)
* [Windows. perception. Spatial-API](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
