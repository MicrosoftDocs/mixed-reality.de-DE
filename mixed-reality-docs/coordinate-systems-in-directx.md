---
title: Koordinatensysteme im DirectX
description: Erläutert, wie mit räumlichen Windows Mixed Reality-Locators, referenzbildern, räumliche Anker und Koordinatensysteme, wie Sie mit der SpatialStage, wie Verlust der Überwachung behandelt, zum Speichern und Laden von Anker und wie für die Stabilisierung können.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Mixed Reality, räumliche Locator, räumliche Verweis-Frame, räumliche Koordinatensystem, räumliche Phase Beispiel für Code, Stabilisierung des Image, räumliche Anker, räumliche Anchor-Store, Verlust der Überwachung, exemplarische Vorgehensweise
ms.openlocfilehash: c8cdb39cbf4634edb4ed0a595381fc70f1388ce4
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605154"
---
# <a name="coordinate-systems-in-directx"></a>Koordinatensysteme im DirectX

[Koordinatensysteme](coordinate-systems.md) bilden die Basis, für die räumliche verstehen, die vom Windows Mixed Reality-APIs zur Verfügung gestellt.

Heutige sitzen, VR oder einzelne-Raum VR-Geräte einrichten, eine primäre Koordinatensystem, um ihren Speicherplatz auf dem überwachten darstellen. Windows Mixed Reality-Geräten wie HoloLens entwickelt wurden, um in großen Umgebungen nicht definiert, verwendet werden mit dem Gerät ermitteln und dessen Umgebung erlernen, wie des Benutzers führt auf. Dies ermöglicht das Gerät zur Anpassung an die ständige Verbesserung Wissen des Benutzers Räume, führt jedoch Koordinatensysteme, die ihre Beziehung untereinander über die Lebensdauer der app geändert wird. Windows Mixed Reality unterstützt ein breites Spektrum von Geräten, die im Bereich von sitzen immersive Headsets bis Welt angeschlossener referenzbildern.

>[!NOTE]
>Die Codeausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstatt C ++ 17-kompatible C++"/ WinRT", wie in der [ C++ holographic Projektvorlage](creating-a-holographic-directx-project.md).  Die Konzepte sind Entsprechung für einen C++"/ WinRT"-Projekt, aber Sie benötigen, um den Code zu übersetzen.

## <a name="spatial-coordinate-systems-in-windows"></a>Räumliche Koordinatensysteme in Windows

Der Kern-Typ verwendet, um den Grund zu echten Koordinatensysteme in Windows ist die <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>. Eine Instanz dieses Typs stellt eine beliebige Koordinatensystem und stellt eine Methode, um eine Transformationsmatrix zu erhalten, die Sie verwenden können, um zwischen zwei Koordinatensysteme ohne Verständnis der Details der einzelnen zu transformieren.

Methoden, die räumliche Informationen, dargestellt als Punkte, Strahlung oder Volumes in der Umgebung des Benutzers, zurückgeben werden einen SpatialCoordinateSystem-Parameter, um Ihnen bei das Koordinatensystem entscheiden, in dem sie besonders hilfreich für die diese Koordinaten zurückzugebenden ist, zu akzeptieren. Diese Koordinaten werden immer in Meter.

Eine SpatialCoordinateSystem hat es sich um eine dynamische Beziehung mit anderen Koordinatensysteme, einschließlich derjenigen, die die Position des Geräts darstellen. Zu jedem Zeitpunkt möglicherweise das Gerät einige Koordinatensysteme und in anderen nicht gefunden. Für die meisten Koordinatensysteme muss Ihre app bereit, um Zeiträume zu behandeln, in dem sie nicht gefunden werden können.

Ihre Anwendung sollte nicht direkt zu erstellen SpatialCoordinateSystems – stattdessen sollten sie über die Wahrnehmung-APIs genutzt werden. Es gibt drei primäre Quellen von Koordinatensysteme in den APIs Perception aller der Karte, um ein Konzept, wie in der [Koordinatensysteme](coordinate-systems.md) Seite:
* Um eine feststehende Verweisrahmen beziehen, erstellen Sie eine <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> oder erhalten Sie eine aus dem aktuellen <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.
* Erstellen Sie zum Abrufen eines räumlichen Ankers ein <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.
* Erstellen Sie zum Abrufen einer angefügten Verweisrahmen eine <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.

Alle der Koordinatensysteme zurückgegeben, die von diesen Objekten sind rechtshändige, mit + y nach + x auf der rechten Seite und + Z rückwärts. Sie können der Richtung der positiven z-Achse Punkte zeigen die Finger Ihre links oder rechts in positive X-Richtung, und wenden sie in die positive y-Richtung Denken Sie daran. Die Richtung, in die der Daumen zeigt, entweder auf Sie zu oder von Ihnen weg, ist die Richtung der positiven Z-Achse für das Koordinatensystem. Die folgende Abbildung zeigt diese zwei Koordinatensysteme.

![Linke und die Rechte Koordinatensysteme](images/left-hand-right-hand.gif)<br>
*Linke und die Rechte Koordinatensysteme*

Um in einem SpatialCoordinateSystem basierend auf die Position des ein HoloLens zu starten, verwenden Sie die <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> Klasse, um entweder eine angefügte oder stationär Verweisrahmen, zu erstellen, wie in den folgenden Abschnitten beschrieben.

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a>Platzieren Sie in der Welt mit einer räumlichen Phase Hologramme

Das Koordinatensystem für nicht transparente Windows Mixed Reality immersive Headsets erfolgt mit der statischen <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> Eigenschaft. Diese API stellt einem Koordinatensystem, Informationen über Sie, ob der Spieler sitzt oder mobile, die Grenzen eines sicheren Bereichs zum um durchlaufen werden, wenn der Player mobile ist, und ein Hinweis darauf, ob die Kopfhörer ist direktional. Es ist auch ein Ereignishandler für Updates der räumlichen Phase.

Zunächst erhalten die räumliche Phase und melden Sie sich für Updates: 

Code für **räumliche Phase-Initialisierung**

```
SpatialStageManager::SpatialStageManager(
    const std::shared_ptr<DX::DeviceResources>& deviceResources, 
    const std::shared_ptr<SceneController>& sceneController)
    : m_deviceResources(deviceResources), m_sceneController(sceneController)
{
    // Get notified when the stage is updated.
    m_spatialStageChangedEventToken = SpatialStageFrameOfReference::CurrentChanged +=
        ref new EventHandler<Object^>(std::bind(&SpatialStageManager::OnCurrentChanged, this, _1));

    // Make sure to get the current spatial stage.
    OnCurrentChanged(nullptr);
}
```

In der OnCurrentChanged-Methode sollte Ihre app die räumliche Phase überprüfen und die Player-Benutzererlebnis sorgen entsprechend aktualisieren. In diesem Beispiel bieten wir eine Visualisierung der Phase Grenze als auch die Startposition, die durch den Benutzer und die Stufe der Ansicht und des Adressbereichs Bewegung Eigenschaften angegeben. Wir auch Fallback Wenn auf unseren eigenen stationär Koordinatensystem, eine Stufe zur Verfügung gestellt werden kann.


Code für **räumliche Phase aktualisieren**

```
void SpatialStageManager::OnCurrentChanged(Object^ /*o*/)
{
    // The event notifies us that a new stage is available.
    // Get the current stage.
    m_currentStage = SpatialStageFrameOfReference::Current;

    // Clear previous content.
    m_sceneController->ClearSceneObjects();

    if (m_currentStage != nullptr)
    {
        // Obtain stage geometry.
        auto stageCoordinateSystem = m_currentStage->CoordinateSystem;
        auto boundsVertexArray = m_currentStage->TryGetMovementBounds(stageCoordinateSystem);

        // Visualize the area where the user can move around.
        std::vector<float3> boundsVertices;
        boundsVertices.resize(boundsVertexArray->Length);
        memcpy(boundsVertices.data(), boundsVertexArray->Data, boundsVertexArray->Length * sizeof(float3));
        std::vector<unsigned short> indices = TriangulatePoints(boundsVertices);
        m_stageBoundsShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(boundsVertices),
                    indices,
                    XMFLOAT3(DirectX::Colors::SeaGreen),
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageBoundsShape);

        // In this sample, we draw a visual indicator for some spatial stage properties.
        // If the view is forward-only, the indicator is a half circle pointing forward - otherwise, it
        // is a full circle.
        // If the user can walk around, the indicator is blue. If the user is seated, it is red.

        // The indicator is rendered at the origin - which is where the user declared the center of the
        // stage to be during setup - above the plane of the stage bounds object.
        float3 visibleAreaCenter = float3(0.f, 0.001f, 0.f);

        // Its shape depends on the look direction range.
        std::vector<float3> visibleAreaIndicatorVertices;
        if (m_currentStage->LookDirectionRange == SpatialLookDirectionRange::ForwardOnly)
        {
            // Half circle for forward-only look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 9, XM_PI);
        }
        else
        {
            // Full circle for omnidirectional look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 16, XM_2PI);
        }

        // Its color depends on the movement range.
        XMFLOAT3 visibleAreaColor;
        if (m_currentStage->MovementRange == SpatialMovementRange::NoMovement)
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::OrangeRed);
        }
        else
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::Aqua);
        }

        std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);

        // Visualize the look direction range.
        m_stageVisibleAreaIndicatorShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    visibleAreaColor,
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
    }
    else
    {
        // No spatial stage was found.
        // Fall back to a stationary coordinate system.
        auto locator = SpatialLocator::GetDefault();
        if (locator)
        {
            m_stationaryFrameOfReference = locator->CreateStationaryFrameOfReferenceAtCurrentLocation();

            // Render an indicator, so that we know we fell back to a mode without a stage.
            std::vector<float3> visibleAreaIndicatorVertices;
            float3 visibleAreaCenter = float3(0.f, -2.0f, 0.f);
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.125f, 16, XM_2PI);
            std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);
            m_stageVisibleAreaIndicatorShape =
                std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    XMFLOAT3(DirectX::Colors::LightSlateGray),
                    m_stationaryFrameOfReference->CoordinateSystem);
            m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
        }
    }
}
```

Der Satz von Vertices, die definieren, die Grenze für die Phase werden bereitgestellt, im Uhrzeigersinn. Die Windows Mixed Reality-Shell zeichnet einen Fence an der Grenze, sobald der Benutzer es fast erreicht wird; Möglicherweise möchten Sie den walks Bereich für Ihre eigenen Zwecke triangularize. Auf die Bühne triangularize, kann der folgende Algorithmus verwendet werden.


Code für **räumliche Phase Triangularization**

```
std::vector<unsigned short> SpatialStageManager::TriangulatePoints(std::vector<float3> const& vertices)
{
    size_t const& vertexCount = vertices.size();

    // Segments of the shape are removed as they are triangularized.
    std::vector<bool> vertexRemoved;
    vertexRemoved.resize(vertexCount, false);
    unsigned int vertexRemovedCount = 0;

    // Indices are used to define triangles.
    std::vector<unsigned short> indices;

    // Decompose into convex segments.
    unsigned short currentVertex = 0;
    while (vertexRemovedCount < (vertexCount - 2))
    {
        // Get next triangle:
        // Start with the current vertex.
        unsigned short index1 = currentVertex;

        // Get the next available vertex.
        unsigned short index2 = index1 + 1;

        // This cycles to the next available index.
        auto CycleIndex = [=](unsigned short indexToCycle, unsigned short stopIndex)
        {
            // Make sure the index does not exceed bounds.
            if (indexToCycle >= unsigned short(vertexCount))
            {
                indexToCycle -= unsigned short(vertexCount);
            }

            while (vertexRemoved[indexToCycle])
            {
                // If the vertex is removed, go to the next available one.
                ++indexToCycle;

                // Make sure the index does not exceed bounds.
                if (indexToCycle >= unsigned short(vertexCount))
                {
                    indexToCycle -= unsigned short(vertexCount);
                }

                // Prevent cycling all the way around.
                // Should not be needed, as we limit with the vertex count.
                if (indexToCycle == stopIndex)
                {
                    break;
                }
            }

            return indexToCycle;
        };
        index2 = CycleIndex(index2, index1);

        // Get the next available vertex after that.
        unsigned short index3 = index2 + 1;
        index3 = CycleIndex(index3, index1);

        // Vertices that may define a triangle inside the 2D shape.
        auto& v1 = vertices[index1];
        auto& v2 = vertices[index2];
        auto& v3 = vertices[index3];

        // If the projection of the first segment (in clockwise order) onto the second segment is 
        // positive, we know that the clockwise angle is less than 180 degrees, which tells us 
        // that the triangle formed by the two segments is contained within the bounding shape.
        auto v2ToV1 = v1 - v2;
        auto v2ToV3 = v3 - v2;
        float3 normalToV2ToV3 = { -v2ToV3.z, 0.f, v2ToV3.x };
        float projectionOntoNormal = dot(v2ToV1, normalToV2ToV3);
        if (projectionOntoNormal >= 0)
        {
            // Triangle is contained within the 2D shape.

            // Remove peak vertex from the list.
            vertexRemoved[index2] = true;
            ++vertexRemovedCount;

            // Create the triangle.
            indices.push_back(index1);
            indices.push_back(index2);
            indices.push_back(index3);

            // Continue on to the next outer triangle.
            currentVertex = index3;
        }
        else
        {
            // Triangle is a cavity in the 2D shape.
            // The next triangle starts at the inside corner.
            currentVertex = index2;
        }
    }

    indices.shrink_to_fit();
    return indices;
}
```

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a>Platzieren Sie in der Welt über eine feststehende Verweisrahmen Hologramme

Die [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) Klasse stellt einen Rahmen zu verweisen, die [stationär bleibt](coordinate-systems.md#stationary-frame-of-reference) relativ zur Umgebung des Benutzers, als der Benutzer verschiebt. Diese Referenz priorisiert Keeping Koordinaten in der Nähe des Geräts stabil. Eine wichtige Verwendung einer SpatialStationaryFrameOfReference ist, fungiert als den zugrunde liegenden globales Koordinatensystem in eine Rendering-Engine beim Rendern von Hologramme.

Verwenden Sie zum Abrufen einer SpatialStationaryFrameOfReference der [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) -Klasse, und rufen [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).

Aus dem Windows Holographic Code der app-Vorlage:

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* Stationär referenzbildern sollen eine Fallback mit ähnlichen Zeichen die Position relativ zu den gesamten Speicherplatz bereitzustellen. Einzelne Positionen innerhalb dieses Rahmens Verweis können leicht abweichen. Dies ist normal, da es sich bei das Gerät mehr über die Umgebung erfährt.
* Wenn die präzise Platzierung von einzelnen Hologramme erforderlich ist, eine SpatialAnchor sollte verwendet werden, um das Verankern Sie die einzelnen Hologramm an eine Position in der realen Welt – z. B. einem Punkt der Benutzer gibt an, dass besonders interessant sein. Anker Positionen werden nicht abweichen, aber können korrigiert werden; der Anker wird verwendet, die korrigierte Position, die in den nächsten Frame gestartet wird, nachdem die Korrektur erfolgt ist.

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a>Platzieren Sie in der Welt mit räumlichen Anker Hologramme

[Räumliche Anker](coordinate-systems.md#spatial-anchors) sind eine hervorragende Möglichkeit, Hologramme an einer bestimmten Position in der Praxis zu platzieren, mit dem System sicherstellen des Ankers bleibt an seiner Stelle im Laufe der Zeit. In diesem Thema wird erläutert, wie zum Erstellen und verwenden einen Anker und Arbeiten mit Daten der Anker.

Sie können eine SpatialAnchor auf eine beliebige Position und die Ausrichtung innerhalb der SpatialCoordinateSystem Ihrer Wahl erstellen. Das Gerät muss in der Lage, dieses Koordinatensystem im Moment zu suchen, und das System muss, nicht die maximale Anzahl von räumlichen Anker erreicht haben.

Nach der Definition, passt das Koordinatensystem des eine SpatialAnchor kontinuierlich um die genaue Position und die Ausrichtung die erste Position des beizubehalten. Klicken Sie dann können diese SpatialAnchor Hologramme gerendert werden, die in der Umgebung des Benutzers, an dieser Position festen angezeigt wird.

Die Auswirkungen der Anpassungen, die den Anker beibehalten werden als Abstand von der Anker steigt verstärkt. Aus diesem Grund sollten Sie Wiedergabe des Inhalts relativ zum Anker, die mehr als ca. 3 Messgeräten, Anker des Ursprungs ist.

Die [Koordinatensystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) -Eigenschaft ruft die einem Koordinatensystem, mit dem Sie den Inhalt relativ zum Anker, mit Übergängen angewendet, wenn das Gerät die genauen Verankerungsposition passt zu platzieren.

Verwenden der [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) -Eigenschaft und dem entsprechenden [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) Ereignis, um diese Anpassungen selbst zu verwalten.

### <a name="persist-and-share-spatial-anchors"></a>Speichern und Freigeben von räumlichen Anker

Sie können eine SpatialAnchor lokal mithilfe von beibehalten der [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) Klasse, und klicken Sie dann wieder in einer zukünftigen app-Sitzung auf dem gleichen HoloLens-Gerät herunterladen.

Mithilfe von <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure räumliche Anker</a>, Sie können einen dauerhafte Anker erstellen, aus einer lokalen SpatialAnchor, die Ihre app über mehrere HoloLens, iOS und Android-Geräte suchen kann.  Anhand der einen allgemeine räumlichen Anker auf mehreren Geräten, kann jeder Benutzer Inhalt gerendert wird, relativ zu diesem-Anker wird in demselben physischen Standort finden Sie unter.  Dadurch können freigegebene ein Nutzererlebnis in Echtzeit.

Können Sie auch <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure räumliche Anker</a> für asynchrone – Hologramm Persistenz für HoloLens, IOS- und Android-Geräte.  Freigeben einer permanenten räumliche cloudankers, können mehrere Geräte das gleiche persistente – Hologramm im Laufe der Zeit beobachten, auch wenn diese Geräte nicht zur gleichen Zeit zusammen vorhanden sind.

Zunächst erstellen freigegebene Umgebungen in Ihrer app HoloLens, testen Sie die 5 Minuten <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure räumliche Anker HoloLens Schnellstart</a>.

Sobald Sie mit Azure räumliche Anker die betriebsbereit sind, können Sie dann <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">erstellen, und suchen Sie die Anker auf HoloLens</a>.  Exemplarische Vorgehensweisen sind verfügbar für <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android und iOS</a> , aktivieren Sie die gleichen Anker auf allen Geräten gemeinsam nutzen.

### <a name="create-spatialanchors-for-holographic-content"></a>SpatialAnchors für holographic Inhalt erstellen

Für dieses Codebeispiel wurde geändert, die Windows Holographic-app-Vorlage zum Erstellen verankert, wenn die **Pressed** Geste erkannt wird. Der Cube wird dann während des Renderings am Anker platziert.

Da mehrere Anker, die von der Hilfsklasse unterstützt werden, platzieren wir können beliebig viele Cubes sollten in diesem Codebeispiel wird mit!

Beachten Sie, dass die IDs für verankert sind, die Sie in Ihrer app zu steuern. In diesem Beispiel haben wir ein Benennungsschema erstellt, die sequenziellen basierend auf der Anzahl der Anker, die derzeit in der app-Sammlung von Anker gespeichert.

```
   // Check for new input state since the last frame.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   if (pointerState != nullptr)
   {
       // Try to get the pointer pose relative to the SpatialStationaryReferenceFrame.
       SpatialPointerPose^ pointerPose = pointerState->TryGetPointerPose(currentCoordinateSystem);
       if (pointerPose != nullptr)
       {
           // When a Pressed gesture is detected, the anchor will be created two meters in front of the user.

           // Get the gaze direction relative to the given coordinate system.
           const float3 headPosition = pointerPose->Head->Position;
           const float3 headDirection = pointerPose->Head->ForwardDirection;

           // The anchor position in the StationaryReferenceFrame.
           static const float distanceFromUser = 2.0f; // meters
           const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

           // Create the anchor at position.
           SpatialAnchor^ anchor = SpatialAnchor::TryCreateRelativeTo(currentCoordinateSystem, gazeAtTwoMeters);

           if ((anchor != nullptr) && (m_spatialAnchorHelper != nullptr))
           {
               // In this example, we store the anchor in an IMap.
               auto anchorMap = m_spatialAnchorHelper->GetAnchorMap();

               // Create an identifier for the anchor.
               String^ id = ref new String(L"HolographicSpatialAnchorStoreSample_Anchor") + anchorMap->Size;

               anchorMap->Insert(id->ToString(), anchor);
           }
       }
   }
```

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a>Asynchron geladen und zwischengespeichert, die SpatialAnchorStore

Sehen wir, wie eine SampleSpatialAnchorHelper-Klasse schreiben, die dabei hilft, behandeln diese Persistenz, einschließlich:
* Speichern eine Auflistung von im Speicher Anker, indiziert, durch einen Platform:: String-Schlüssel.
* Laden über die Systemvariable SpatialAnchorStore Anker, der getrennt von der lokalen Auflistung im Arbeitsspeicher bleibt.
* Die lokale in-Memory-Auflistung der Anker an die SpatialAnchorStore werden bei die app wählt, dazu gespeichert.

So speichern Sie [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) Objekte in der [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).

Beim Starten der-Klasse, fordern wir die SpatialAnchorStore asynchron. Dies umfasst die System-e/a, wie die API den Premium-Speicher lädt, und diese API ist asynchron umgewandelt, sodass die e/a nicht blockierend ist.

```
   // Request the spatial anchor store, which is the WinRT object that will accept the imported anchor data.
   return create_task(SpatialAnchorManager::RequestStoreAsync())
       .then([](task<SpatialAnchorStore^> previousTask)
   {
       std::shared_ptr<SampleSpatialAnchorHelper> newHelper = nullptr;

       try
       {
           SpatialAnchorStore^ anchorStore = previousTask.get();

           // Once the SpatialAnchorStore has been loaded by the system, we can create our helper class.

           // Using "new" to access private constructor
           newHelper = std::shared_ptr<SampleSpatialAnchorHelper>(new SampleSpatialAnchorHelper(anchorStore));

           // Now we can load anchors from the store.
           newHelper->LoadFromAnchorStore();
       }
       catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while loading the anchor store: ") +
               exception->Message->Data() +
               L"\n"
               );
       }

       // Return the initialized class instance.
       return newHelper;
   });
```

Sie werden eine SpatialAnchorStore erhalten, die Sie verwenden können, um die Anker zu speichern. Dies ist ein IMapView, die Schlüsselwerte zuordnet, die Zeichenfolgen mit den Datenwerten, die SpatialAnchors sind. In unserem Beispielcode speichern wir diese in einer privaten Klassenmembervariablen, die über eine öffentliche Funktion unserer Helper-Klasse zugegriffen werden kann.

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
>Vergessen Sie nicht zum Einbinden der Suspend/Resume-Ereignisse speichern und laden den Premium-Speicher.

```
   void HolographicSpatialAnchorStoreSampleMain::SaveAppState()
   {
       // For example, store information in the SpatialAnchorStore.
       if (m_spatialAnchorHelper != nullptr)
       {
           m_spatialAnchorHelper->TrySaveToAnchorStore();
       }
   }
```

```
   void HolographicSpatialAnchorStoreSampleMain::LoadAppState()
   {
       // For example, load information from the SpatialAnchorStore.
       LoadAnchorStore();
   }
```

### <a name="save-content-to-the-anchor-store"></a>Speichern von Inhalt in den Premium-Speicher

Wenn das System Ihre app anhält, müssen Sie Ihre räumlichen Anker in den Premium-Speicher zu speichern. Außerdem können Sie Anker zu anderen Zeiten, in den Premium-Speicher zu speichern wie finden Sie für die Implementierung von Ihrer app erforderlich sein.

Wenn Sie versuchen, die in-Memory-Anker der SpatialAnchorStore speichern möchten, können Sie Ihre Sammlung durchlaufen und versuchen, jeweils zu speichern.

```
   // TrySaveToAnchorStore: Stores all anchors from memory into the app's anchor store.
   //
   // For each anchor in memory, this function tries to store it in the app's AnchorStore. The operation will fail if
   // the anchor store already has an anchor by that name.
   //
   bool SampleSpatialAnchorHelper::TrySaveToAnchorStore()
   {
       // This function returns true if all the anchors in the in-memory collection are saved to the anchor
       // store. If zero anchors are in the in-memory collection, we will still return true because the
       // condition has been met.
       bool success = true;

       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           for each (auto& pair in m_anchorMap)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;

               // Try to save the anchors.
               if (!m_anchorStore->TrySave(id, anchor))
               {
                   // This may indicate the anchor ID is taken, or the anchor limit is reached for the app.
                   success=false;
               }
           }
       }

       return success;
   }
```

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a>Laden Sie Inhalt aus dem Premium-Speicher, wenn die app fortgesetzt wird.

Wenn Ihre app fortgesetzt wird, oder zu einer anderen Zeit, die für Ihre app Implementaiton erforderlich sind, können Sie Anker wiederherstellen, die zuvor in der AnchorStore gespeichert wurden, durch die Übertragung von der Premium-Shop IMapView auf Ihre eigene in-Memory-Datenbank über SpatialAnchors.

Zum Wiederherstellen von Anker aus der SpatialAnchorStore wiederherstellen Sie, die Sie interessiert, eine eigene in-Memory-Auflistung.

Sie benötigen Ihre eigene in-Memory-Datenbank über SpatialAnchors; eine Möglichkeit, Zeichenfolgen, die Sie erstellen die SpatialAnchors zugeordnet werden soll. In unserem Beispielcode, die zum Speichern von der Anker ein Windows::Foundation::Collections::IMap verwenden wählen wir die erleichtert Ihnen den gleichen Wert für Schlüssel und die Daten für die SpatialAnchorStore zu verwenden.

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
>Ein Anker, der wiederhergestellt wird möglicherweise nicht sofort auffindbaren werden. Es kann z. B. ein Anker, die in einem separaten Raum oder in einer anderen Builderstellung vollständig sein. Anker, die aus der AnchorStore abgerufenen sollten für Locatability getestet werden, vor der Verwendung.

<br>

>[!NOTE]
>In diesem Beispielcode rufen wir alle Textmarken, aus der AnchorStore. Dies ist nicht erforderlich; Ihre app kann genauso gut auswählen eine bestimmte Teilmenge der Anker mit der Zeichenfolge fest, die für Ihre Implementierung von Bedeutung sind.

```
   // LoadFromAnchorStore: Loads all anchors from the app's anchor store into memory.
   //
   // The anchors are stored in memory using an IMap, which stores anchors using a string identifier. Any string can be used as
   // the identifier; it can have meaning to the app, such as "Game_Leve1_CouchAnchor," or it can be a GUID that is generated
   // by the app.
   //
   void SampleSpatialAnchorHelper::LoadFromAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Get all saved anchors.
           auto anchorMapView = m_anchorStore->GetAllSavedAnchors();
           for each (auto const& pair in anchorMapView)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;
               m_anchorMap->Insert(id, anchor);
           }
       }
   }
```

### <a name="clear-the-anchor-store-when-needed"></a>Deaktivieren Sie der Anker-Store, bei Bedarf

In einigen Fällen müssen Sie app-Status löschen und neue Daten zu schreiben. Hier ist, woher die [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).

Verwenden unsere Hilfsklasse, ist es fast nicht erforderlich, um die Funktion Clear zu umschließen. Wählen wir dazu in unserem Beispiel für die Implementierung, da unsere Hilfsklasse, die Verantwortung vorliegt für die SpatialAnchorStore-Instanz besitzt.

```
   // ClearAnchorStore: Clears the AnchorStore for the app.
   //
   // This function clears the AnchorStore. It has no effect on the anchors stored in memory.
   //
   void SampleSpatialAnchorHelper::ClearAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Clear all anchors from the store.
           m_anchorStore->Clear();
       }
   }
```

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a>Beispiel: Im Zusammenhang Koordinatensysteme Anker mit unbewegtem Verweis Frame Koordinatensysteme

Angenommen, Sie einen Anker haben und um etwas in Ihrer Ankers Koordinatensystem mit der SpatialStationaryReferenceFrame zu verknüpfen, die Sie bereits für die meisten anderen Inhalte verwenden möchten. Sie können [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) um eine Transformation aus Koordinatensystem des Ankers mit der der Rahmen eines stationären Zustands Verweis zu erhalten:

```
   // In this code snippet, someAnchor is a SpatialAnchor^ that has been initialized and is valid in the current environment.
   float4x4 anchorSpaceToCurrentCoordinateSystem;
   SpatialCoordinateSystem^ anchorSpace = someAnchor->CoordinateSystem;
   const auto tryTransform = anchorSpace->TryGetTransformTo(currentCoordinateSystem);
   if (tryTransform != nullptr)
   {
       anchorSpaceToCurrentCoordinateSystem = tryTransform->Value;
   }
```

Dieser Prozess ist nützlich, gibt es zwei Möglichkeiten:
1. Sie erfahren Sie, wenn die beiden Frames verweisen können relativ zu anderen, verstanden werden und;
2. Wenn dies der Fall ist, bietet Ihnen eine Transformation, um direkt aus einem Koordinatensystem in den anderen zu wechseln.

Mit diesen Informationen müssen Sie einen Überblick über die räumlichen Beziehung zwischen Objekten zwischen den zwei referenzbildern.

Für das Rendering erhalten häufig eine bessere Ergebnisse Sie durch Gruppierung von Objekten, die gemäß ihrer ursprünglichen Verweis Rahmen oder den Ankerpunkt. Führen Sie einen separaten zeichnen Durchlauf für jede Gruppe ein. Die Ansicht-Matrizen sind für Objekte mit Model-Transformationen, die erstellt werden, zunächst mit den gleichen Koordinatensystem präziser.

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a>Verwenden ein Gerät angeschlossen Verweisrahmen Hologramme erstellen

Es gibt Situationen zum Rendern ggf. ein Hologramm, [bleibt weiterhin verbunden](coordinate-systems.md#attached-frame-of-reference) auf den Standort eines Geräts, z. B. einen Bereich mit dem Debuggen von Informationen oder eine informative Meldung, wenn das Gerät nur die Ausrichtung zu bestimmen und nicht seine Position im Raum. Zu diesem Zweck verwenden wir eine angefügte Verweisrahmen.

Die SpatialLocatorAttachedFrameOfReference-Klasse definiert die Koordinatensysteme sind relativ zu dem Gerät anstatt in der Praxis. Dieser Frame verfügt über eine feste Überschrift relativ zur Umgebung des Benutzers, bei denen es zeigt in Richtung der Benutzer wurde als Verweis Frames erstellt wurde. Von nun an sind alle Ausrichtungen, die in dieser Referenz relativ zu dieser Überschrift behoben, auch wenn der Benutzer das Gerät dreht.

Für HoloLens befindet sich der Ursprung des Koordinatensystems des Frames im Zentrum der Drehung der Benutzer des Benutzers, damit die Position von Head-Rotation nicht beeinträchtigt wird. Ihre app kann einen Offset relativ zu diesem Zeitpunkt zum Positionieren der Hologramme vor dem Benutzer geben.

Um eine SpatialLocatorAttachedFrameOfReference zu erhalten, verwenden Sie die SpatialLocator-Klasse, und rufen Sie CreateAttachedFrameOfReferenceAtCurrentHeading aus.

Beachten Sie, dass dies für die gesamte Palette von Windows Mixed Reality-Geräte gilt.

### <a name="use-a-reference-frame-attached-to-the-device"></a>Verwenden Sie einen Verweis Frame des Geräts

Diese Abschnitte sprechen wir in die Windows Holographic app-Vorlage Änderungen, um ein Gerät angeschlossen Verweisrahmen mithilfe dieser API zu aktivieren. Beachten Sie, dass diese "angefügten" Hologram wird zusammen mit unbewegtem oder verankerten Hologramme kann ebenfalls verwendet werden, wenn das Gerät vorübergehend nicht seine Position in der ganzen Welt zu finden ist.

Zunächst haben wir die Vorlage, um eine SpatialLocatorAttachedFrameOfReference anstelle einer SpatialStationaryFrameOfReference Speichern geändert:

Von **HolographicTagAlongSampleMain.h**:

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

Von **HolographicTagAlongSampleMain.cpp**:

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

Während der Aktualisierung erhalten wir jetzt das Koordinatensystem auf den Zeitstempel aus mit der Vorhersage Frame abgerufen.

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a>Abrufen Sie einer räumlichen Zeiger Haltung und folgen des Benutzers Blicke

Wir möchten unsere Beispiel – Hologramm des Benutzers befolgen [bestaunen](gaze.md), ähnlich wie die holographic Shell des Benutzers Blicke folgen kann. Dafür müssen wir die SpatialPointerPose aus dem gleichen Zeitstempel erhalten.

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

Diese SpatialPointerPose verfügt über die erforderlichen Informationen zum Positionieren der Hologramm gemäß der [aktuelle Überschrift des Benutzers](gaze,-gestures,-and-motion-controllers-in-directx.md).

Aus Gründen der Benutzerkomfort verwenden wir die linearen Interpolation ("Lerp") zum Glätten von der Änderung an der Position, dass sie über einen Zeitraum erfolgt. Dies ist für den Benutzer komfortabler als die Hologramm, die Blicke sperren. Lerping, die die Tag-along – Hologramm Position auch die Hologramm zu stabilisieren, durch die Verschiebung Dämpfung ermöglicht; Wenn noch nicht diese Dämpfung, würde dem Benutzer angezeigt, die – Hologramm jitter aufgrund betrachtet was normalerweise nicht wahrnehmbar Bewegungen von des Benutzers Head werden.

From **StationaryQuadRenderer::PositionHologram**:

```
   const float& dtime = static_cast<float>(timer.GetElapsedSeconds());

   if (pointerPose != nullptr)
   {
       // Get the gaze direction relative to the given coordinate system.
       const float3 headPosition  = pointerPose->Head->Position;
       const float3 headDirection = pointerPose->Head->ForwardDirection;

       // The tag-along hologram follows a point 2.0m in front of the user's gaze direction.
       static const float distanceFromUser = 2.0f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

       // Lerp the position, to keep the hologram comfortably stable.
       auto lerpedPosition = lerp(m_position, gazeAtTwoMeters, dtime * c_lerpRate);

       // This will be used as the translation component of the hologram's
       // model transform.
       SetPosition(lerpedPosition);
   }
```

>[!NOTE]
>Im Fall von einem Bereich zum Debuggen angezeigt werden kann können Sie auswählen, um die – Hologramm deaktivieren, klicken Sie auf der Seite, damit sie nicht die Ansicht antidebugverhalten ist ein wenig neu zu positionieren. Hier ist ein Beispiel, wie Sie dies tun können.

For **StationaryQuadRenderer::PositionHologram**:

```
       // If you're making a debug view, you might not want the tag-along to be directly in the
       // center of your field of view. Use this code to position the hologram to the right of
       // the user's gaze direction.
       /*
       const float3 offset = float3(0.13f, 0.0f, 0.f);
       static const float distanceFromUser = 2.2f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * (headDirection + offset));
       */
```

### <a name="rotate-the-hologram-to-face-the-camera"></a>Drehen Sie den – Hologramm, um die Kamera auftreten

Es ist nicht ausreichend, einfach die – Hologramm, positionieren Sie in diesem Fall wird ein Quad; Wir müssen auch drehen, das Objekt, um die Benutzer auftreten. Beachten Sie, dass durch diese Drehung im Raum der Welt stattfindet, da es sich bei dieser Art von billboarding Hologramm, die als Teil der Umgebung des Benutzers bleiben können. Anzeigeraum billboarding ist nicht so vertraut, da die Hologramm für die displayausrichtung gesperrt wird; In diesem Fall müssten Sie auch interpoliert zwischen dem linken und rechten Ansicht Matrizen zum Anzeigebereich Billboard Transformation zu erhalten, die nicht Stereo Rendering unterbricht. Drehen wir hier auf der X- und Z-Achse auf der Benutzer ein.

From **StationaryQuadRenderer::Update**:

```
   // Seconds elapsed since previous frame.
   const float& dTime = static_cast<float>(timer.GetElapsedSeconds());

   // Create a direction normal from the hologram's position to the origin of person space.
   // This is the z-axis rotation.
   XMVECTOR facingNormal = XMVector3Normalize(-XMLoadFloat3(&m_position));

   // Rotate the x-axis around the y-axis.
   // This is a 90-degree angle from the normal, in the xz-plane.
   // This is the x-axis rotation.
   XMVECTOR xAxisRotation = XMVector3Normalize(XMVectorSet(XMVectorGetZ(facingNormal), 0.f, -XMVectorGetX(facingNormal), 0.f));

   // Create a third normal to satisfy the conditions of a rotation matrix.
   // The cross product  of the other two normals is at a 90-degree angle to
   // both normals. (Normalize the cross product to avoid floating-point math
   // errors.)
   // Note how the cross product will never be a zero-matrix because the two normals
   // are always at a 90-degree angle from one another.
   XMVECTOR yAxisRotation = XMVector3Normalize(XMVector3Cross(facingNormal, xAxisRotation));

   // Construct the 4x4 rotation matrix.

   // Rotate the quad to face the user.
   XMMATRIX rotationMatrix = XMMATRIX(
       xAxisRotation,
       yAxisRotation,
       facingNormal,
       XMVectorSet(0.f, 0.f, 0.f, 1.f)
       );

   // Position the quad.
   const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

   // The view and projection matrices are provided by the system; they are associated
   // with holographic cameras, and updated on a per-camera basis.
   // Here, we provide the model transform for the sample hologram. The model transform
   // matrix is transposed to prepare it for the shader.
   XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(rotationMatrix * modelTranslation));
```

### <a name="render-the-attached-hologram"></a>Rendern Sie die angefügte – Hologramm

In diesem Beispiel wählen wir auch zum Rendern in das Koordinatensystem der SpatialLocatorAttachedReferenceFrame Hologramm, in dem wir die Hologramm positioniert ist. (Wenn wir uns entschieden hätten gerendert wird, verwenden ein anderes Koordinatensystem, müssten wir, eine Transformation von Koordinatensystem des Frames Gerät angeschlossenen Verweis auf dieses Koordinatensystem abzurufen).

From **HolographicTagAlongSampleMain::Render**:

```
   // The view and projection matrices for each holographic camera will change
   // every frame. This function refreshes the data in the constant buffer for
   // the holographic camera indicated by cameraPose.
   pCameraResources->UpdateViewProjectionBuffer(
       m_deviceResources,
       cameraPose,
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp)
       );
```

Das ist alles! Der – Hologramm wird nun "eine Position 2 Zähler vor des Benutzers Blicke Richtung auswerten".

>[!NOTE]
>In diesem Beispiel lädt auch zusätzliche Inhalte – finden Sie unter StationaryQuadRenderer.cpp.

## <a name="handling-tracking-loss"></a>Behandeln von Datenverlust nachverfolgen

Wenn das Gerät in der ganzen Welt finden kann, hat die app "Verlust der Überwachung". Windows Mixed Reality-apps muss in der Lage, solche Unterbrechungen für das mit Feldern fester Breite Tracking-System zu verarbeiten. Diese Störungen können beobachtet werden, und Antworten erstellt, mit dem LocatabilityChanged-Ereignis auf dem standardmäßigen SpatialLocator.

Von **AppMain::SetHolographicSpace:**

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

Wenn Ihre app ein LocatabilityChanged-Ereignis empfängt, können sie Verhalten je nach Bedarf ändern. Z. B. in den Zustand "PositionalTrackingInhibited" Ihre app Anhalten des normalen Betriebs und Rendern einer [Tag-along – Hologramm](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) , die zeigt, dass eine Warnmeldung an.

Im Lieferumfang von Windows Holographic-app-Vorlage ist eines LocatabilityChanged-Handlers, die bereits für Sie erstellt haben. Standardmäßig zeigt er eine Warnung in der Debugkonsole, wenn mit Feldern fester Breite Überwachung nicht verfügbar ist. Sie können Code, die diesem Handler eine Antwort angeben, nach Bedarf aus Ihrer app hinzufügen.

Von **AppMain.cpp:**

```
   void HolographicApp1Main::OnLocatabilityChanged(SpatialLocator^ sender, Object^ args)
   {
       switch (sender->Locatability)
       {
       case SpatialLocatability::Unavailable:
           // Holograms cannot be rendered.
           {
               String^ message = L"Warning! Positional tracking is " +
                                           sender->Locatability.ToString() + L".\n";
               OutputDebugStringW(message->Data());
           }
           break;

       // In the following three cases, it is still possible to place holograms using a
       // SpatialLocatorAttachedFrameOfReference.
       case SpatialLocatability::PositionalTrackingActivating:
           // The system is preparing to use positional tracking.

       case SpatialLocatability::OrientationOnly:
           // Positional tracking has not been activated.

       case SpatialLocatability::PositionalTrackingInhibited:
           // Positional tracking is temporarily inhibited. User action may be required
           // in order to restore positional tracking.
           break;

       case SpatialLocatability::PositionalTrackingActive:
           // Positional tracking is active. World-locked content can be rendered.
           break;
       }
   }
```

## <a name="spatial-mapping"></a>Räumliche Zuordnung

Die [räumliche Zuordnung](spatial-mapping-in-directx.md) APIs stellen mithilfe der Koordinatensysteme Modell Transformationen für Surface Gitter abgerufen werden.

## <a name="see-also"></a>Siehe auch
* [Koordinatensysteme](coordinate-systems.md)
* [Räumliche Anker](spatial-anchors.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure räumliche Anker</a>
* [Blicke, Gesten und während der Übertragung von Controllern in DirectX](gaze,-gestures,-and-motion-controllers-in-directx.md)
* [Räumliche Zuordnung in DirectX](spatial-mapping-in-directx.md)
