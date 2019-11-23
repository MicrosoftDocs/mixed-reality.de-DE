---
title: Räumliche Zuordnung in Unity
description: Rendering und Konflikt mit der realen Geometrie in Unity.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, räumliche Zuordnung, Renderer, Collider, Mesh, Scannen, Komponente
ms.openlocfilehash: 452e629a877df585ffbc0a6466ffeb2588b66ecf
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438037"
---
# <a name="spatial-mapping-in-unity"></a>Räumliche Zuordnung in Unity

In diesem Thema wird beschrieben, wie die [räumliche Zuordnung](spatial-mapping.md) in Ihrem Unity-Projekt verwendet wird, und es werden Dreiecksnetze abgerufen, die die Oberflächen weltweit um ein hololens-Gerät, für Platzierung, Okklusion, Raumanalyse usw. darstellen.

Unity bietet vollständige Unterstützung für die räumliche Zuordnung, die Entwicklern auf folgende Weise zur Verfügung gestellt wird:
1. In mixedrealitytoolkit verfügbare räumliche Zuordnungskomponenten, die einen einfachen und schnellen Weg für den Einstieg in die räumliche Zuordnung bieten
2. Räumliche Mapping-APIs auf niedrigerer Ebene, die Vollzugriff bieten und eine anspruchsvollere anwendungsspezifische Anpassung ermöglichen

Um die räumliche Zuordnung in der APP zu verwenden, muss die spatialperception-Funktion in Ihrem appxmanifest festgelegt werden.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Funktion</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Räumliche Zuordnung</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="setting-the-spatialperception-capability"></a>Festlegen der spatialperception-Funktion

Damit eine APP räumliche Zuordnungs Daten verarbeiten kann, muss die spatialperception-Funktion aktiviert werden.

Aktivieren der spatialperception-Funktion:
1. Öffnen Sie im Unity-Editor den Bereich **"Player Einstellungen"** (Bearbeiten > Projekteinstellungen > Player).
2. Klicken Sie auf die Registerkarte **"Windows Store"** .
3. Erweitern Sie **"Veröffentlichungs Einstellungen"** , und überprüfen Sie die Funktion **"spatialperception"** in der Liste **"Funktionen"** .

Beachten Sie Folgendes: Wenn Sie Ihr Unity-Projekt bereits in eine Visual Studio-Projekt Mappe exportiert haben, müssen Sie entweder in einen neuen Ordner exportieren oder [Diese Funktion manuell in "appxmanifest" in Visual Studio festlegen](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).

Die räumliche Zuordnung erfordert auch ein maxversiongetestet von mindestens 10.0.10586.0:
1. Klicken Sie in Visual Studio im Projektmappen-Explorer mit der rechten Maustaste auf **Package. appxmanifest** , und wählen Sie **Code anzeigen** aus.
2. Suchen Sie die Zeile, in der **targetdevicefamily** angegeben ist, und ändern Sie **maxversiongete= "10.0.10240.0"** in **maxversiongete= "10.0.10586.0"** .
3. **Speichern** Sie die Datei "Package. appxmanifest".

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Die ersten Schritte mit den integrierten räumlichen Mapping-Komponenten von Unity

Unity bietet zwei Komponenten für das einfache Hinzufügen von räumlicher Zuordnung zu Ihrer APP, den **Renderer für räumliche** zuzuzuzuzufügende **Daten und den**

### <a name="spatial-mapping-renderer"></a>Renderer für räumliche Zuordnung

Der Renderer für räumliche Zuordnung ermöglicht die Visualisierung des diagrammdiagrammdiagrammers.

![Renderer für räumliche Zuordnung in Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>Der Collider für räumliche Zuordnung

Der Collider der räumlichen Zuordnung ermöglicht die holografische Inhalts Interaktion (oder Zeichen Interaktion), wie z. b. die Physik, mit dem Mesh für räumliche Zuordnung.

![Der Collider für räumliche Zuordnung in Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>Verwenden der integrierten Komponenten für räumliche Zuordnung

Wenn Sie physische Oberflächen visualisieren und mit ihnen interagieren möchten, können Sie Ihrer APP beide Komponenten hinzufügen.

So verwenden Sie diese beiden Komponenten in ihrer Unity-App:
1. Wählen Sie ein gameobject-Objekt in der Mitte des Bereichs aus, in dem Sie räumliche Oberflächen Netze erkennen möchten.
2. **Fügen Sie** im Inspektor-Fenster Komponenten > **XR** >  ** ** der oder **räumliche Zuordnung**hinzu.

Weitere Informationen zur Verwendung dieser Komponenten finden Sie auf der <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity-Dokumentations Website</a>.

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>Über die integrierten Komponenten für räumliche Zuordnung hinausgehen

Diese Komponenten vereinfachen den Einstieg in die räumliche Zuordnung.  Wenn Sie fortfahren möchten, können Sie zwei Haupt Pfade untersuchen:
* Wenn Sie eine eigene Mesh-Verarbeitung auf niedrigerer Ebene durchführen möchten, finden Sie im Abschnitt weiter unten Informationen zur Skript-API auf niedriger Ebene.
* Informationen zu einer übergeordneten Mesh-Analyse finden Sie im Abschnitt weiter unten über die spatialunderstanding-Bibliothek in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">mixedrealitytoolkit</a>.

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>Verwenden der Unity-API für die räumliche Zuordnung auf niedriger Ebene

Wenn Sie mehr Kontrolle benötigen, als Sie von den Komponenten des Renderers für räumliche Zuordnung und der Komponenten Zuordnung für räumliche Zuordnung erhalten, können Sie die Low-Level-Skript-APIs für die räumliche Zuordnung verwenden.

**Namespace:** *unityengine. XR. WSA*<br>
**Typen**: *surfaceobserver*, *SurfaceChange*, *surfacedata*, *surfaceid*

Im folgenden finden Sie einen Überblick über den empfohlenen Ablauf für eine Anwendung, die die APIs für die räumliche Zuordnung verwendet.

### <a name="set-up-the-surfaceobservers"></a>Einrichten von "surfaceobserver (s)"

Instanziieren Sie ein surfaceobserver-Objekt für jeden Anwendungs definierten Bereich, für den Sie räumliche Mapping-Daten benötigen.

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

Geben Sie den Bereich des Speicherplatzes an, für den jedes surfaceobserver-Objektdaten bereitstellt, indem Sie entweder setvolumeassphere, setvolumeasaxisalignedbox, setvolumeasorientedbox oder setvolumeasfrustum aufrufen. Sie können den Bereich des Speicherplatzes in der Zukunft neu definieren, indem Sie einfach eine dieser Methoden aufrufen.

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

Wenn Sie surfaceobserver. Update () aufgerufen haben, müssen Sie für jede räumliche Oberfläche im Bereich von surfaceobserver einen Handler bereitstellen, für den das räumliche Zuordnungssystem über neue Informationen verfügt. Der Handler empfängt für eine räumliche Oberfläche Folgendes:

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a>Verarbeiten von Oberflächen Änderungen

Es gibt mehrere Hauptfälle, die behandelt werden müssen. Hinzugefügte & aktualisiert, die denselben Codepfad verwenden und entfernt werden können.
* In den hinzugefügten & aktualisierten Fällen im Beispiel fügen wir das gameobject-Objekt, das dieses Mesh darstellt, aus dem Wörterbuch hinzu, erstellen eine surfacedata-Struktur mit den erforderlichen Komponenten und rufen dann requestmeshdataasync auf, um das gameobject mit den Mesh-Daten aufzufüllen. Position in der Szene.
* Im entfernten Fall entfernen wir das gameobject, das dieses Mesh darstellt, aus dem Wörterbuch und zerstören es.

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects = 
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

   private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
   {
       switch (changeType)
       {
           case SurfaceChange.Added:
           case SurfaceChange.Updated:
               if (!spatialMeshObjects.ContainsKey(surfaceId))
               {
                   spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                   spatialMeshObjects[surfaceId].transform.parent = this.transform;
                   spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
               }
               GameObject target = spatialMeshObjects[surfaceId];
               SurfaceData sd = new SurfaceData(
                   //the surface id returned from the system
                   surfaceId,
                   //the mesh filter that is populated with the spatial mapping data for this mesh
                   target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                   //the world anchor used to position the spatial mapping mesh in the world
                   target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                   //the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                   target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                   //triangles per cubic meter requested for this mesh
                   1000,
                   //bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                   true
                   );

               SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
               break;
           case SurfaceChange.Removed:
               var obj = spatialMeshObjects[surfaceId];
               spatialMeshObjects.Remove(surfaceId);
               if (obj != null)
               {
                   GameObject.Destroy(obj);
               }
               break;
           default:
               break;
       }
   }
```

### <a name="handling-data-ready"></a>Verarbeiten von Daten

Der ondataready-Handler empfängt ein surfacedata-Objekt. Die in der Datei "worldanchor", "meshfilter" und "(optional) meshcollider" enthaltenen Objekte entsprechen dem aktuellen Zustand der zugeordneten räumlichen Oberfläche. Führen Sie optional eine Analyse und/oder [Verarbeitung](spatial-mapping.md#mesh-processing) der Mesh-Daten durch, indem Sie auf den Mesh-Member des meshfilter-Objekts zugreifen. Rendersie die räumliche Oberfläche mit dem aktuellen Mesh, und (optional) verwenden Sie Sie für Physik-und Raycasts. Es ist wichtig zu bestätigen, dass der Inhalt der surfacedata nicht NULL ist.

### <a name="start-processing-on-updates"></a>Verarbeitung bei Updates starten

"Surfaceobserver. Update ()" sollte bei einer Verzögerung und nicht bei jedem Frame aufgerufen werden.

```cs
void Start () {
    ...
     StartCoroutine(UpdateLoop());
}

 IEnumerator UpdateLoop()
    {
        var wait = new WaitForSeconds(2.5f);
        while(true)
        {
            surfaceObserver.Update(OnSurfaceChanged);
            yield return wait;
        }
    }
```

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a>Mesh-Analyse auf höherer Ebene: spatialunderstanding

<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">Mixedrealitytoolkit</a> ist eine Sammlung hilfreicher hilfsprogrammcodes für die Holographic-Entwicklung, die auf den Holographic Unity-APIs basiert.

### <a name="spatial-understanding"></a>Räumliche Kenntnisse

Beim Platzieren von holograms in der physischen Welt ist es häufig wünschenswert, das Gitter-und Oberflächen Flächen der räumlichen Zuordnung zu überschreiten. Wenn die Platzierung prozedurale durchgeführt wird, ist ein höheres Maß an Umwelt Kenntnissen wünschenswert. Dies erfordert in der Regel Entscheidungen hinsichtlich der Fläche "Floor", "Ceiling" und "Wände". Außerdem können Sie mit einer Reihe von Platzierungs Einschränkungen optimieren, um die begehrtesten physischen Speicherorte für Holographic-Objekte zu bestimmen.

Bei der Entwicklung von jung-und-Fragmenten stellten Asobo-Studios dieses Problem in den Kopf, um für diesen Zweck ein Raum-Solver zu entwickeln. Bei jedem dieser Spiele gab es Spiel spezifische Anforderungen, aber Sie haben die grundlegende Technologie für räumliche Daten genutzt. Die Bibliothek "holotoolkit. spatialunderstanding" kapselt diese Technologie, sodass Sie schnell leere Leerzeichen auf den Wänden finden, Objekte auf der Obergrenze platzieren, für das Zeichen platzieren und eine Vielzahl anderer Abfragen mit räumlichem Verständnis festlegen können.

Der gesamte Quellcode ist enthalten, sodass Sie ihn an Ihre Anforderungen anpassen und die Verbesserungen für die Community freigeben können. Der Code für den C++ Solver wurde in eine UWP-dll umschließt und Unity mit einem Drop in Prefab verfügbar gemacht, das in mixedrealitytoolkit enthalten ist.

### <a name="understanding-modules"></a>Grundlegendes zu Modulen

Es gibt drei primäre Schnittstellen, die vom Modul verfügbar gemacht werden: Topologie für einfache Oberflächen-und räumliche Abfragen, Form zur Objekterkennung und das objektplatzierungs-Solver für die Einschränkungs basierte Platzierung von Objekt Sätzen. Diese werden nachfolgend beschrieben. Zusätzlich zu den drei primären Modulschnittstellen kann eine Strahl Umwandlungs Schnittstelle verwendet werden, um markierte Oberflächentypen abzurufen, und ein benutzerdefiniertes, wasserdichtes Playspace-Mesh kann kopiert werden.

### <a name="ray-casting"></a>Strahl Umwandlung

Nachdem der Raum gescannt und fertiggestellt wurde, werden Bezeichnungen intern für Oberflächen, wie z. b. Boden, Ceiling und Wände, generiert. Die "playspaceraycast"-Funktion nimmt einen Strahl an und gibt zurück, wenn der Strahl mit einer bekannten Oberfläche kollidiert. wenn dies der Fall ist, werden Informationen über diese Oberfläche in Form von "raycastresult" angezeigt.

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology, 
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and 
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface, 
                    //  but vertical surface that looks like a 
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown 
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

Intern wird der raycast anhand der berechneten Voxel-Darstellung im 8cm-Format des Playspace berechnet. Jeder Voxel enthält einen Satz von Oberflächenelementen mit verarbeiteten Topologiedaten (auch als Surfels bezeichnet). Der Surfels, der in der überschneidenden Voxel-Zelle enthalten ist, wird verglichen und die beste Entsprechung für die Suche nach den Topologieinformationen. Diese Topologieinformationen enthalten die Bezeichnung, die in Form der "surfacetypes"-Aufzählung zurückgegeben wird, sowie den Oberflächen Bereich der überschneidenden Oberfläche.

Im Unity-Beispiel wandelt der Cursor einen Strahl in jedem Frame um. Zuerst für Unity-Kollisionen. Zweitens, mit der Welt Darstellung des grundlegenden Moduls. Und schließlich wieder Benutzeroberflächen Elemente. In dieser Anwendung erhält die Benutzeroberfläche Priorität, das Ergebnis des Ergebnisses und schließlich Unity-Kollisionen. Der surfaketype wird als Text neben dem Cursor gemeldet.

![Surface-Typ wird neben dem Cursor bezeichnet](images/su-raycastresults-300px.jpg)<br>
*Der Surface-Typ wird neben dem Cursor bezeichnet.*

### <a name="topology-queries"></a>Topologieabfragen

Innerhalb der DLL übernimmt der topologiemanager die Bezeichnung der Umgebung. Wie bereits erwähnt, werden viele der Daten in Surfels gespeichert, das in einem Voxel-Volume enthalten ist. Außerdem wird die "playspaceinfos"-Struktur zum Speichern von Informationen über den Playspace verwendet, einschließlich der Welt Ausrichtung (weitere Details zu diesem unten), der Etage und der Höhe des ceiling. Heuristiken werden zum Bestimmen von Boden, Ceiling und Wänden verwendet. Beispielsweise wird die größte und niedrigste horizontale Oberfläche mit einer Größe von mehr als 1 m2 als Floor betrachtet. Beachten Sie, dass der Kamerapfad während des Scanvorgangs auch in diesem Prozess verwendet wird.

Eine Teilmenge der Abfragen, die vom topologiemanager verfügbar gemacht werden, wird über die dll verfügbar gemacht. Die verfügbar gemachten Topologieabfragen lauten wie folgt.

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

Jede der Abfragen verfügt über eine Reihe von Parametern, die für den Abfragetyp spezifisch sind. Im folgenden Beispiel gibt der Benutzer die Mindesthöhe & Breite des gewünschten Volumes, die minimale Platzierungs Höhe oberhalb der Etage und den minimalen Abstand vor dem Volume an. Alle Messungen befinden sich in Meter.

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

Jede dieser Abfragen nimmt ein vorab zugeordenes Array von "topologyresult"-Strukturen an. Der "locationcount"-Parameter gibt die Länge des übergebenen Arrays an. Der Rückgabewert meldet die Anzahl der zurückgegebenen Speicherorte. Diese Zahl ist nie größer als der Wert des "locationcount"-Parameters.

"Topologyresult" enthält die Mittelpunkt Position des zurückgegebenen Volumes, die Richtung (d. h. Normal) und die Abmessungen des gefundenen Speicherplatzes.

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

Beachten Sie, dass im Unity-Beispiel jede dieser Abfragen mit einer Schaltfläche im Bereich der virtuellen Benutzeroberfläche verknüpft ist. Im Beispiel werden die Parameter für jede dieser Abfragen in angemessene Werte fest codiert. Weitere Beispiele finden Sie unter SpaceVisualizer.cs im Beispielcode.

### <a name="shape-queries"></a>Shape-Abfragen

Innerhalb der dll verwendet der Shape Analyzer ("ShapeAnalyzer_W") die topologieanalyse, um mit den vom benutzerdefinierten benutzerdefinierten Formen zu vergleichen. Das Unity-Beispiel definiert einen Satz von Formen und macht die Ergebnisse über das in-App-Abfrage Menü auf der Registerkarte Form verfügbar. Die Absicht besteht darin, dass der Benutzer seine eigenen Objektform Abfragen definieren und diese verwenden kann, je nach Bedarf von der Anwendung.

Beachten Sie, dass die Formanalyse nur auf horizontalen Oberflächen funktioniert. Eine Couch wird z. b. durch die flache Arbeitsplatz Oberfläche und den flachen oberen Rand der Couch zurückgelegt. Die Shape-Abfrage sucht nach zwei Oberflächen mit einer bestimmten Größe, Höhe und einem bestimmten Seitenbereich, wobei die beiden Oberflächen ausgerichtet und verbunden sind. Bei Verwendung der APIs-Terminologie sind der Couch-und der Back-Top Form Komponenten, und die Ausrichtungs Anforderungen sind Shape-Komponenten Einschränkungen.

Eine Beispiel Abfrage, die im Unity-Beispiel (ShapeDefinition.cs) für "sitbare" Objekte definiert ist, lautet wie folgt.

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

Jede Shape-Abfrage wird durch einen Satz von Form Komponenten definiert, die jeweils über einen Satz von Komponenten Einschränkungen und einen Satz von Form Einschränkungen verfügen, die Abhängigkeiten zwischen den Komponenten auflisten. Dieses Beispiel enthält drei Einschränkungen in einer einzelnen Komponenten Definition und keine Formen Einschränkungen zwischen Komponenten (da nur eine Komponente vorhanden ist).

Im Gegensatz dazu hat die Form "Couch" zwei Form Komponenten und vier Form Einschränkungen. Beachten Sie, dass die Komponenten durch ihren Index in der Komponentenliste des Benutzers (0 und 1 in diesem Beispiel) identifiziert werden.

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

Wrapper Funktionen werden im Unity-Modul bereitgestellt, um eine einfache Erstellung benutzerdefinierter Formen Definitionen zu erstellen. Die vollständige Liste der Komponenten-und Shape-Einschränkungen finden Sie in "SpatialUnderstandingDll.cs" innerhalb der "shapecomponenteinschränkung"-und "shapeconstraint"-Strukturen.

auf dieser Oberfläche wird ![Rechteck Form gefunden](images/su-shapequery-300px.jpg)<br>
*Die Rechteck Form wird auf dieser Oberfläche gefunden.*

### <a name="object-placement-solver"></a>Objektplatzierungs-Solver

Der objektplatzierungs-Solver kann verwendet werden, um ideale Positionen im physischen Raum zu identifizieren, um die Objekte zu platzieren. Der Solver findet den am besten geeigneten Speicherort anhand der Objekt Regeln und Einschränkungen. Außerdem bleiben Objekt Abfragen so lange erhalten, bis das Objekt mit "Solver_RemoveObject"-oder "Solver_RemoveAllObjects"-aufrufen entfernt wird, sodass die eingeschränkte Platzierung von mehreren Objekten ermöglicht wird. Die Platzierungs Abfragen von Objekten bestehen aus drei Teilen: Platzierungs Typ mit Parametern, eine Liste von Regeln und eine Liste von Einschränkungen. Verwenden Sie die folgende API, um eine Abfrage auszuführen.

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

Diese Funktion nimmt einen Objektnamen, eine Platzierungs Definition und eine Liste von Regeln und Einschränkungen an. Die C# Wrapper stellen Konstruktions Hilfsfunktionen bereit, um die Erstellung von Regeln und Einschränkungen zu vereinfachen. Die Platzierungs Definition enthält den Abfragetyp – d. h. einen der folgenden.

```cpp
public enum PlacementType
            {
                Place_OnFloor,
                Place_OnWall,
                Place_OnCeiling,
                Place_OnShape,
                Place_OnEdge,
                Place_OnFloorAndCeiling,
                Place_RandomInAir,
                Place_InMidAir,
                Place_UnderFurnitureEdge,
            };
```

Jeder der Platzierungs Typen hat eine Reihe von Parametern, die für den Typ eindeutig sind. Die "objectplacementdefinition"-Struktur enthält einen Satz statischer Hilfsfunktionen zum Erstellen dieser Definitionen. Wenn Sie z. b. einen Speicherort zum Platzieren eines Objekts im Boden finden möchten, können Sie die folgende Funktion verwenden. public static objectplacementdefinition Create_OnFloor (Vector3 halfdims) zusätzlich zum Platzierungs Typ können Sie einen Satz von Regeln und Einschränkungen bereitstellen. Regeln können nicht verletzt werden. Mögliche Platzierungs Speicherorte, die den Typ und die Regeln erfüllen, werden dann anhand des Satzes von Einschränkungen optimiert, um den optimalen Speicherort für die Platzierung auszuwählen. Alle Regeln und Einschränkungen können von den bereitgestellten statischen Erstellungs Funktionen erstellt werden. Eine Beispiel Regel und eine Einschränkungs Erstellungs Funktion finden Sie unten.

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

Die nachstehende Objekt Platzierungs Abfrage sucht nach einer Stelle, an der der Rand einer Oberfläche von anderen Objekten, die sich in der Mitte des Raums befinden, platziert wird.

```cs
List<ObjectPlacementRule> rules = 
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints = 
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f), 
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

Wenn erfolgreich, wird eine "objectplacementresult"-Struktur mit der Platzierungsposition, den Dimensionen und der Ausrichtung zurückgegeben. Außerdem wird die Platzierung der internen Liste der platzierten Objekte der dll hinzugefügt. Bei nachfolgenden Platzierungs Abfragen wird dieses Objekt berücksichtigt. Die Datei "LevelSolver.cs" im Unity-Beispiel enthält weitere Beispielabfragen.

![Ergebnisse der Objekt Platzierung](images/su-objectplacement-1000px.jpg)<br>
*Abbildung 3: die blauen Felder, die ergeben, wie sich das Ergebnis von drei Positionen im Boden von der Kamera positionsregeln entfernt hat*

Wenn Sie für den Speicherort der Platzierung mehrerer Objekte, die für ein Level-oder Anwendungsszenario erforderlich sind, lösen möchten, lösen Sie zunächst unentbehrliche und große Objekte aus, um die Wahrscheinlichkeit zu maximieren, dass ein Platz gefunden wird Die Platzierungs Reihenfolge ist wichtig. Wenn die Platzierung von Objekten nicht gefunden werden kann, versuchen Sie es mit weniger eingeschränkten Konfigurationen. Eine Reihe von Fall Back Konfigurationen ist wichtig für die Unterstützung von Funktionen in vielen Raum Konfigurationen.

### <a name="room-scanning-process"></a>Raum Scanprozess

Obwohl die von hololens bereitgestellte räumliche Mappinglösung generisch genug ist, um den Anforderungen des gesamten Bereichs von Problembereichen gerecht zu werden, wurde das räumliche grundlegendes Modul erstellt, um die Anforderungen von zwei bestimmten spielen zu unterstützen. Die Lösung ist um einen bestimmten Prozess und eine Reihe von Annahmen strukturiert, die unten zusammengefasst werden.

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

Benutzergesteuerte Playspace "Paint" – während der Überprüfungsphase bewegt der Benutzer die Wiedergabegeschwindigkeit und untersucht die Bereiche, die eingeschlossen werden sollen. Das generierte Mesh ist wichtig, um Benutzer Feedback in dieser Phase bereitzustellen. Startseite oder Office-Setup – die Abfragefunktionen werden um flache Flächen und Wände im rechten Winkel entworfen. Dies ist eine weiche Einschränkung. Während der Scan Phase wird jedoch eine primäre Achsen Analyse abgeschlossen, um das Gitter Mosaik entlang der Haupt-und der Nebenachse zu optimieren. Die enthaltene SpatialUnderstanding.cs-Datei verwaltet den Scan Phasen Prozess. Es werden die folgenden Funktionen aufgerufen.

```
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan – 
    Called each frame to update the scanning process. The camera position and 
    orientation is passed in and is used for the playspace painting process, 
    described above.

GeneratePlayspace_RequestFinish – 
    Called to finalize the playspace. This will use the areas “painted” during 
    the scan phase to define and lock the playspace. The application can query 
    statistics during the scanning phase as well as query the custom mesh for 
    providing user feedback.

Import_UnderstandingMesh – 
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by 
    the module and placed on the understanding prefab will periodically query the 
    custom mesh generated by the process. In addition, this is done once more 
    after scanning has been finalized.
```

Der Scanvorgang, der vom "spatialunderstanding"-Verhalten gesteuert wird, ruft initscan auf und aktualisiert dann jeden Frame. Wenn die Statistik Abfrage eine angemessene Abdeckung meldet, kann der Benutzer mit airtap auf requestfinish aufrufen, um das Ende der Scan Phase anzugeben. Updatescan wird weiterhin aufgerufen, bis der Rückgabewert angibt, dass die dll die Verarbeitung abgeschlossen hat.

### <a name="understanding-mesh"></a>Grundlegendes zum Mesh

Die Understanding dll speichert den Playspace intern als Raster von Voxel-Cubes mit 8 cm. Während des ersten Teils der Überprüfung wird eine Analyse der primären Komponenten abgeschlossen, um die Achsen des Raums zu ermitteln. Intern speichert Sie seinen Voxel-Bereich, der auf diese Achsen ausgerichtet ist. Ein Mesh wird ungefähr jede Sekunde generiert, indem die Isofläche aus dem Voxel-Volume extrahiert wird. 

![generierte Gitter, das aus dem Voxel-Volume erstellt wurde](images/su-custommesh.jpg)<br>
*Generiertes Mesh, das vom Voxel-Volume erstellt wurde*

## <a name="troubleshooting"></a>Problembehandlung
* Stellen Sie sicher, dass Sie die Funktion [spatialperception](#setting-the-spatialperception-capability) festgelegt haben
* Wenn die Nachverfolgung verloren geht, entfernt das nächste onsurfacechanged-Ereignis alle Meshes.

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>Räumliche Zuordnung im Mixed Reality Toolkit
Weitere Informationen zur Verwendung der räumlichen Zuordnung mit Mixed Reality Toolkit v2 finden Sie im <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Abschnitt räumliche</a> Informationen der mrtk-Dokumentation.

## <a name="see-also"></a>Weitere Informationen
* [Räumliche Daten 230: räumliche Zuordnung](holograms-230.md)
* [Koordinatensysteme](coordinate-systems.md)
* [Koordinatensysteme in Unity](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">Unityengine. meshfilter</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">Unityengine. meshcollider</a>
* <a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">Unityengine. Bounds</a>
