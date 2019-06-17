---
title: Räumliche Zuordnung in Unity
description: Rendern, und mit der realen Welt Geometrie um Sie in Unity Konflikt zu geraten.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, räumliche Zuordnung, Renderer, "collider", Netz, Überprüfung, Komponente
ms.openlocfilehash: 8f7bad1651ab31b2e83ad9d9c8f465547fbbdc5a
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148647"
---
# <a name="spatial-mapping-in-unity"></a>Räumliche Zuordnung in Unity

In diesem Thema wird beschrieben, wie Sie mit [räumliche Zuordnung](spatial-mapping.md) in Ihrem Unity-Projekt abrufen Dreieckgitter, die die Flächen in die Welt um ein HoloLens-Gerät, für die Platzierung, verdecken, Raum Analyse und mehr darstellen.

Unity bietet vollständige Unterstützung für räumliche Zuordnung, die für Entwickler auf folgende Weise verfügbar gemacht wird:
1. Räumliche Zuordnung von Komponenten, die in der MixedRealityToolkit verfügbar, geben Sie die einen einfachen und schnellen Pfad für den Einstieg in die räumliche Zuordnung
2. Räumliche Zuordnung von Low-Level-APIs, die vollständigen gewähren steuern und höher entwickelte Anwendung spezifische Anpassung aktivieren

Um räumliche Zuordnung in Ihrer app verwenden zu können, muss die SpatialPerception-Funktion in Ihrem AppxManifest festgelegt werden.

## <a name="setting-the-spatialperception-capability"></a>Festlegen der SpatialPerception-Funktion

Damit eine app, räumliche Zuordnungsdaten zu verwenden muss die SpatialPerception-Funktion aktiviert sein.

Informationen zum Aktivieren der SpatialPerception-Funktion:
1. Öffnen Sie im Unity-Editor, der **"Player Settings"** Bereich (Bearbeiten > Projekteinstellungen > Player)
2. Klicken Sie auf die **"Windows Store"** Registerkarte
3. Erweitern Sie **"Veröffentlichungseinstellungen"** und überprüfen Sie die **"SpatialPerception"** -Funktion in der **"Funktionen"** Liste

Beachten Sie, dass wenn Sie bereits Ihr Unity-Projekt in Visual Studio-Projektmappe exportiert haben, Sie die zum Exportieren in einen neuen Ordner oder manuell müssen [legen Sie diese Funktion in die appxmanifest-Datei in Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).

Räumliche Zuordnung erfordert außerdem eine "maxversiontested", der mindestens 10.0.10586.0:
1. In Visual Studio, klicken Sie mit der rechten Maustaste auf **"Package.appxmanifest"** im Projektmappen-Explorer, und wählen **Anzeigecode**
2. Suchen Sie die Zeile anzugeben, **TargetDeviceFamily** , und ändern Sie **"maxversiontested" = "10.0.10240.0"** zu **"maxversiontested" = "10.0.10586.0"**
3. **Speichern Sie** der Datei "Package.appxmanifest".

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Erste Schritte mit Komponenten der Unity-integrierte räumliche Zuordnung

Unity bietet 2 Komponenten für die räumliche Zuordnung auf einfache Weise in Ihrer app hinzuzufügen **räumliche Zuordnung Renderer** und **räumliche Zuordnung "collider"** .

### <a name="spatial-mapping-renderer"></a>Räumliche Zuordnung Renderer

Der räumliche Zuordnung-Renderer ermöglicht die Visualisierung des Netzes räumliche Zuordnung.

![Räumliche Zuordnung-Renderer in Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>Räumliche Zuordnung "collider"

Die räumliche Zuordnung "collider" holographic Inhalt (oder Zeichen) ermöglicht Interaktion mit dem Netz räumliche Zuordnung, wie z. B. Physik.

![Räumliche Zuordnung "collider" in Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>Verwenden die Komponenten für die integrierte räumliche Zuordnung

Sie können beide Komponenten zu Ihrer app hinzufügen, wenn Sie sowohl visualisieren und physische interagieren möchten.

So verwenden Sie diese beiden Komponenten in Ihrer Unity-app
1. Wählen Sie ein "gameobject" in der Mitte des Bereichs, in dem Sie räumliche Oberfläche Gitter erkennen möchten.
2. Im Inspektor-Fenster **Add Component** > **XR** > **räumliche Zuordnung "collider"**  oder **räumlich Zuordnung Renderer**.

Finden Sie weitere Informationen zur Verwendung dieser Komponenten unter den <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity-Dokumentationswebsite</a>.

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>Darum geht, über die Komponenten für die integrierte räumliche Zuordnung

Diese Komponenten erleichtern die Drag & Drop einfach zum Einstieg in die räumliche Zuordnung.  Wenn Sie fortfahren möchten, gibt es zwei Hauptmethoden, um zu untersuchen:
* Um Ihre eigene Low-Level-Mesh-Verarbeitung durchführen zu können, finden Sie im Abschnitt auf niedriger Ebene räumliche Zuordnung zum Skript zur API.
* Um auf höherer Ebene Mesh-Analyse durchzuführen, finden Sie im Abschnitt über die Bibliothek SpatialUnderstanding in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>Der Low-Level Unity räumliche Zuordnung-API

Wenn Sie mehr Kontrolle benötigen, als Sie von den Komponenten räumliche Zuordnung-Renderer und räumliche Zuordnung "collider" erhalten, können Sie die Low-Level, räumliche Zuordnung Skript APIs verwenden.

**Namespace:** *UnityEngine.XR.WSA*<br>
**Typen**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*

Im folgenden finden einen Überblick über die vorgeschlagenen Flow für eine Anwendung, die räumliche Zuordnung APIs verwendet.

### <a name="set-up-the-surfaceobservers"></a>Richten Sie die SurfaceObserver(s)

Instanziieren Sie ein SurfaceObserver-Objekt für jede Region anwendungsdefinierte des Speicherplatzes, der Sie räumliche Zuordnung von Daten für benötigen.

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

Geben Sie die Region des Speicherplatzes, der jedes Objekt SurfaceObserver Daten für die durch Aufrufen von entweder SetVolumeAsSphere SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox oder SetVolumeAsFrustum bereitstellt. Sie können die Region des Speicherplatzes in der Zukunft neu definieren, durch den Aufruf einer der folgenden Methoden einfach erneut aus.

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

Wenn Sie SurfaceObserver.Update() aufrufen, müssen Sie einen Handler für jede räumliche Fläche in der SurfaceObservers Region des Speicherplatzes bereitstellen, die das räumliche Zuordnung System neue Informationen für. Der Handler empfängt, für eine räumliche Oberfläche:

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a>Behandeln von Surface-Änderungen

Es gibt mehrere main Fälle zu behandeln. Hinzugefügt und aktualisiert die gleich verwenden kann, codieren, Pfad "und" entfernt.
* In den Fällen hinzugefügte und aktualisierte im Beispiel wir hinzufügen oder abrufen, das "gameobject" ein, diese aus dem Wörterbuch mesh, erstellen eine SurfaceData-Struktur mit der erforderlichen Komponenten, und rufen Sie dann RequestMeshDataAsync zum Auffüllen der "gameobject" mit den Daten des Mesh, und Positionieren Sie in der Szene.
* Im Fall entfernt, wenn wir das dieses Mesh darstellt, aus dem Wörterbuch "gameobject" zu entfernen und zerstören sie.

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

### <a name="handling-data-ready"></a>Behandlung von Daten bereit

Der OnDataReady Handler empfängt ein SurfaceData-Objekt. Die WorldAnchor, MeshFilter und (optional) MeshCollider die darin enthaltenen Objekte repräsentieren den aktuellen Status der zugehörigen räumliche Oberfläche. Führen Sie optional eine Analyse und/oder [Verarbeitung](spatial-mapping.md#mesh-processing) der Daten durch den Zugriff auf die Mesh-Member des Objekts MeshFilter Mesh. Die räumliche Oberfläche mit dem aktuellen Netz zu rendern, und (optional) für Physik Kollisionen und Raycasts verwenden. Es ist wichtig, um sicherzustellen, dass der Inhalt der SurfaceData nicht null sind.

### <a name="start-processing-on-updates"></a>Starten von updates

SurfaceObserver.Update() sollte auf eine Verzögerung, die nicht für jedes Bild aufgerufen werden.

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

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a>Mesh-Analyse auf höherer Ebene: SpatialUnderstanding

Die <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> ist eine Sammlung von hilfreich dienstprogrammcodes für holographic Entwicklung, die auf die holographic Unity-APIs basieren.

### <a name="spatial-understanding"></a>Räumliche verstehen

Beim Platzieren von Hologramme in der realen Welt ist es oft wünschenswert, wechseln über die räumliche Zuordnung mesh und Ebenen Oberfläche. Bei der Platzierung Prozedural abgeschlossen ist, ist ein höheres Maß an die Umwelt Verständnis wünschenswert. Dies erfordert normalerweise, Entscheidungen darüber, was Floor, Ceiling und Wänden ist. Darüber hinaus die Möglichkeit, für einen Satz von platzierungseinschränkungen zum Festlegen der am häufigsten gewünscht physischen Standorten für holographic Objekte zu optimieren.

Bei der Entwicklung von Young Conker und Fragmente konfrontiert Asobo Studios diese Problem Head-Datei auf einem Solver Raum zu diesem Zweck entwickeln. Für jede dieser Spiele spielen bestimmte Anforderungen wurde, aber sie räumliche Verständnis kerntechnologie freigegeben. Die HoloToolkit.SpatialUnderstanding Bibliothek kapselt diese Technologie ermöglicht, dass Sie schnell suchen Leerzeichen an den Wänden, direkten-Objekten, auf die Obergrenze identifizieren platziert für Zeichen, das sich befinden und unzählige andere räumliche Grundlegendes zu Abfragen.

Alle des Quellcodes enthalten ist, können Sie es an Ihre Anforderungen anpassen und Ihrer Verbesserungen mit der Community teilen. Der Code für die C++ Solver umschlossen in eine Dll für UWP und Unity mit einen Abfall der MixedRealityToolkit enthaltenen Prefab verfügbar gemacht wurde.

### <a name="understanding-modules"></a>Grundlegendes zur-Module

Es gibt drei primäre Schnittstellen, die vom Modul offengelegte: Topologie für einfache Oberfläche und räumliche Abfragen, Form für die objekterkennung und der Solver Objekt Platzierung für die Platzierung Objektsätze Einschränkung basierend. Jedes davon wird unten beschrieben. Zusätzlich zu den drei primäre Modulschnittstellen eine Chow Umwandlung-Schnittstelle kann verwendet werden, um die markierte Oberfläche Typen abzurufen, und einem benutzerdefinierten wasserdichte Playspace Mesh werden sollen.

### <a name="ray-casting"></a>Chow Umwandlung

Nachdem Raum gescannt und abgeschlossen wurde, werden die Bezeichnungen für Oberflächen wie die Floor, Ceiling und Wände intern generiert. Der "PlayspaceRaycast"-Funktion nimmt ein Strahl und gibt zurück, wenn der Strahl mit einer bekannten Oberfläche verursacht einen Konflikt, und wenn dies der Fall, die Informationen, die dann in Form einer "RaycastResult".

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

Die Raycast wird intern für die berechnete 8 cm hoch drei Voxel Darstellung der Playspace berechnet. Jede Voxel enthält einen Satz von Surface-Elementen mit verarbeiteten Topologiedaten (auch bekannt als Surfels). Die in der Zelle überschneidungen Voxel enthaltenen Surfels verglichen werden, und die beste Übereinstimmung verwendet, um die Topologieinformationen zu suchen. Diese Topologiedaten enthalten die Bezeichnung in Form von der Enumeration "SurfaceTypes" als auch die Oberfläche der überschneidungen Oberfläche zurückgegeben.

Im Unity-Beispiel wird der Cursor jeder Frame ein Strahl umgewandelt. Zunächst anhand von Unity-collider. Zweitens: für das Verständnis des Moduls-Welt-Darstellung. Und schließlich erneut UI-Elementen. In dieser Anwendung UI ruft Priorität ab, als Nächstes das Ergebnis verstehen und die Unity-collider. Die SurfaceType wird als Text neben dem Cursor gemeldet.

![Surface-Typ wird neben dem Cursor bezeichnet.](images/su-raycastresults-300px.jpg)<br>
*Surface-Typ wird neben dem Cursor bezeichnet.*

### <a name="topology-queries"></a>Abfragen der Topologie

In der DLL behandelt Topologie-Manager die Bezeichnung der Umgebung. Wie bereits erwähnt, wird ein Großteil der Daten in Surfels, ein Volume Voxel enthaltenen gespeichert. Darüber hinaus wird die Struktur "PlaySpaceInfos" zum Speichern von Informationen zu den Playspace, einschließlich der Welt, Ausrichtung (Weitere Einzelheiten hierzu finden Sie nachstehend), Floor und Ceiling Höhe. Heuristik beim Ermitteln der werden verwendet, um zu bestimmen, Floor, Ceiling und Wänden. Beispielsweise gilt die größte und niedrigste horizontale Oberfläche mit mehr als 1 m2 Oberfläche den Boden. Beachten Sie, dass der Pfad "Kamera" während des Scanvorgangs auch in diesem Prozess verwendet wird.

Eine Teilmenge der Abfragen, die von der Topologie-Manager verfügbar gemacht werden über die Dll bereitgestellt. Die verfügbar gemachten Topologie-Abfragen sind wie folgt aus.

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

Alle Abfragen verfügt über einen Satz von Parametern, die spezifisch für den Abfragetyp. Im folgenden Beispiel gibt den Benutzer, die minimale Höhe und Breite der gewünschte Volume, minimale Platzierung Höhe über dem Boden und die Mindestmenge an sicherheitsbestätigung vor dem Volume. Alle Messungen sind in Meter.

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

Jeder dieser Abfragen akzeptiert ein vorab zugeordnete Array von "TopologyResult"-Strukturen. Der Parameter "LocationCount" gibt die Länge des übergebenen Arrays an. Der Rückgabewert gibt die Anzahl der zurückgegebenen Speicherorte. Diese Zahl ist niemals größer als der übergebene Parameter für "LocationCount".

Die "TopologyResult" enthält die zentrierte Textposition des zurückgegebenen Volumes, die zugänglichen Richtung (d. h. normal), und die Abmessungen des Bereich gefunden.

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

Beachten Sie, dass in der Unity-Beispiel, jeder dieser Abfragen sich auf eine Schaltfläche in der virtuellen Benutzeroberflächen-Panel verknüpft ist. Das Beispiel schwer-codes die Parameter für jede dieser Abfragen für Sie geeignete Standardwerte. Der Beispielcode für weitere Beispiele finden Sie in SpaceVisualizer.cs.

### <a name="shape-queries"></a>Shape-Abfragen

Innerhalb der Dll verwendet der Shape-Analyzer ("ShapeAnalyzer_W") den Topologie-Analyzer für den Abgleich von benutzerdefinierter Formen, die vom Benutzer definiert. Im Unity-Beispiel definiert einen Satz von Formen und stellt die Ergebnisse, über das Abfragemenü mit in-app-, auf die Registerkarte "Form". Die Absicht ist, dass der Benutzer kann eigene Form Objektabfragen zu definieren, und stellen diese bei Bedarf von ihrer Anwendung verwenden.

Beachten Sie, dass die Form-Analyse auf nur horizontale Oberflächen funktioniert. Ein Sofa, wird z. B. durch die Flatfile-Arbeitsplatz-Oberfläche und flache Anfang den Garten wieder definiert. Shape-Abfrage sucht nach zwei Oberflächen von einer bestimmten Größe, Höhe und Aspekt-Bereich mit den beiden Oberflächen ausgerichtet und verbunden. Verwenden die APIs Terminologie, im Sofa Arbeitsplatz und Back sind Shape-Komponenten, und der ausrichtungsanforderungen werden Beschränkungen hinsichtlich der Form Komponenten.

Eine Beispielabfrage, die in der Unity-Beispiel (ShapeDefinition.cs), "sittable" Objekte definiert, lautet wie folgt:

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

Jedes Shape-Abfrage wird definiert, indem eine Reihe von Form-Komponenten, jeweils eine Reihe von Beschränkungen hinsichtlich der Komponenten und einer Reihe von Form-Einschränkungen das Auflisten von Abhängigkeiten zwischen den Komponenten. Dieses Beispiel enthält drei Einschränkungen in einer einzelnen Komponente-Definition und keine Einschränkungen der Form zwischen Komponenten, (wie es nur eine Komponente ist).

Im Gegensatz dazu verfügt über die Form Sofa, zwei Shape-Komponenten und Einschränkungen für vier Form. Beachten Sie, dass Komponenten anhand ihres Indexes in der Liste der Komponenten des Benutzers (0 und 1 in diesem Beispiel) identifiziert werden.

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

Wrapperfunktionen werden zur einfachen Erstellung von Definitionen für benutzerdefinierte Form, die im Unity-Modul bereitgestellt. Die vollständige Liste der Komponente und Form-Einschränkungen finden Sie in "SpatialUnderstandingDll.cs" in der "ShapeComponentConstraint" und "ShapeConstraint" Strukturen.

![Rechteckige Form wird auf dieser Oberfläche gefunden.](images/su-shapequery-300px.jpg)<br>
*Rechteckige Form wird auf dieser Oberfläche gefunden.*

### <a name="object-placement-solver"></a>Die Platzierung Solver Objekt

Der Objekt-Solver Platzierung kann verwendet werden, um ideal Orte im physischen Raum platzieren Ihrer Objekte zu ermitteln. Der Solver findet, dass die besten Speicherort, der die Objektregeln und Einschränkungen entsprechen. Darüber hinaus beibehalten Objektabfragen, bis das Objekt, mit "Solver_RemoveObject entfernt wird" oder "Solver_RemoveAllObjects" aufrufen, sodass Platzierung Multi-Objekts eingeschränkte. Platzierung Objects-Abfragen bestehen aus drei Teilen: die Platzierungstyp mit Parametern, eine Liste der Regeln und eine Liste der Einschränkungen. Verwenden Sie zum Ausführen einer Abfrage, die folgende API ein.

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

Diese Funktion akzeptiert ein Objektname, Platzierungsdefinition und eine Liste von Regeln und Einschränkungen. Die C# Wrapper Konstruktion Stellt Hilfsfunktionen bereit, um die Regel oder Einschränkung Erstellung zu vereinfachen. Die Platzierungsdefinition enthält den Abfragetyp – d. h. eine der folgenden.

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

Alle Platzierungstypen, hat es sich um einen Satz von Parametern, die nur für den Typ. Die Struktur "ObjectPlacementDefinition" enthält einen Satz von statischen Hilfsfunktionen für diese Definitionen zu erstellen. Um einer bestimmten Stelle ablegen ein Objekts auf dem Boden zu suchen, können Sie z. B. die folgende Funktion verwenden. Öffentliche statische ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) neben die Platzierungstyp, können Sie einen Satz von Regeln und Einschränkungen bereitstellen. Regeln können nicht verletzt werden. Mögliche Platzierung von Standorten, die den Typ und die Regeln zu erfüllen sind klicken Sie dann mit einem Satz an Einschränkungen optimiert, um den Speicherort für die optimale Platzierung auszuwählen. Alle Regeln und Einschränkungen kann von den Funktionen für die angegebene statische Erstellung erstellt werden. Eine Beispiel-Regel und die Einschränkung der Konstruktorfunktion wird unten bereitgestellt.

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

Die unter-Objekt für eine Umgebung zum Einfügen eines Cubes Hälfte Verbrauchseinheit am Rand einer Oberfläche, von anderen Objekten zuvor platzieren und in der Nähe der Mitte des Raums Platzierung Abfrage sucht.

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

Bei Erfolg wird eine "ObjectPlacementResult"-Struktur, die mit der Platzierung, Dimensionen und die Ausrichtung zurückgegeben. Darüber hinaus wird die Platzierung des Dll interne Liste der platzierten Objekte hinzugefügt. Platzierung der nachfolgenden Abfragen werden dieses Objekt zu berücksichtigen. Die Datei "LevelSolver.cs" in der Unity-Beispiel enthält weitere Beispiele für Abfragen.

![Ergebnisse der objektplatzierung](images/su-objectplacement-1000px.jpg)<br>
*Abbildung 3: Die blauen Felder wie das Ergebnis von drei Ort auf Floor mit Abfragen, von der Kamera Position Regeln*

Bei der Lösung für die Platzierung-Speicherort, der mehrere Objekte, die für ein Szenario Ebene oder eine Anwendung erforderlich sind, lösen Sie zuerst unverzichtbaren und große Objekte zur Maximierung der der Wahrscheinlichkeit, die ein Leerzeichen befinden. Platzierung Reihenfolge ist wichtig. Wenn das Objekt Platzierungen nicht gefunden wird, versuchen Sie es weniger eingeschränkte Konfigurationen. Eine Reihe von Konfigurationen ist entscheidend für die Unterstützung von Funktionen in vielen Konfigurationen von Platz.

### <a name="room-scanning-process"></a>Raum Scanningprozess

Zwar allgemein genug, um die Anforderungen die gesamte Palette von Problembereiche werden räumliche Zuordnung-Lösung durch die HoloLens ausgelegt ist, wurde das räumliche Verständnis-Modul erstellt, um die Anforderungen von zwei bestimmte Spiele zu unterstützen. Seine Lösung basiert auf einem bestimmten Prozess und eine Reihe von Annahmen, die im folgenden zusammengefasst.

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

Benutzergesteuerte Playspace "Zeichnen" – während der Überprüfungsphase, der Benutzer wechselt und sieht sich der Wiedergabe der Bedingungen, für die tatsächlich Zeichnen der Bereiche, die einbezogen werden sollen. Das generierte Netz ist wichtig, Feedback von Benutzern bereitzustellen, während dieser Phase. In geschlossenen Räumen home oder das Office-setup – der Abfrage, die Funktionen für flache Flächen und Wände rechtwinklig konzipiert sind. Dies ist eine weiche Einschränkung. Jedoch wird während der Überprüfungsphase, eine Analyse der primären Achse abgeschlossen, um das Netz Mosaik Haupt- und Nebenversionsnummern Achse zu optimieren. Der eingebundenen Datei SpatialUnderstanding.cs verwaltet den Scanvorgang-Phase. Sie ruft die folgenden Funktionen.

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

Scan Datenfluss durch das Verhalten "SpatialUnderstanding" gesteuert ruft InitScan, und klicken Sie dann auf UpdateScan jeden Frame. Wenn die Abfrage Statistiken angemessenen Coverage meldet, darf der Benutzer auf Airtap RequestFinish, um anzugeben, das Ende der Überprüfungsphase aufrufen. UpdateScan weiterhin aufgerufen werden, bis sie die Rückgabe ist der Wert gibt an, dass die Dll die Verarbeitung abgeschlossen wurde.

### <a name="understanding-mesh"></a>Grundlegendes zu Netz

Grundlegendes zur Dll speichert intern die Playspace als ein Raster aus 8cm Größe Voxel Cubes. Während des ersten Teils Scannen ist eine Hauptkomponente Analyse abgeschlossen, um zu bestimmen, die Achsen des Raums. Sie speichert intern Voxel Speicherplatzes ausgerichtet, diese Achsen. Ein Mesh wird ungefähr pro Sekunde generiert, mit dem Extrahieren der Isofläche aus dem Voxel Volume. 

![Generierte Mesh erstellt, von dem Volume voxel](images/su-custommesh.jpg)<br>
*Generierte Mesh erstellt, von dem Volume voxel*

## <a name="troubleshooting"></a>Problembehandlung
* Stellen Sie sicher, die Sie festgelegt haben die [SpatialPerception](#setting-the-spatialperception-capability) Funktion
* Bei der nachverfolgung verloren geht, wird das nächste OnSurfaceChanged Ereignis alle Gitter entfernt.

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>Räumliche Zuordnung in Mixed Reality-Toolkit
Weitere Informationen zur Verwendung von räumliche Zuordnung mit Mixed Reality-Toolkit v2 finden Sie unter den <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">räumliche Awareness Abschnitt</a> MRTK Dokumenten.

## <a name="see-also"></a>Siehe auch
* [MR räumlich 230: Räumliche Abbildung](holograms-230.md)
* [Koordinatensysteme](coordinate-systems.md)
* [Koordinatensysteme in Unity](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>
* <a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a>
* <a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a>
* <a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a>
