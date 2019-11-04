---
title: 'Fallstudie: Erweitern der räumlichen Mapping-Funktionen von hololens'
description: Beim Erstellen unserer ersten Apps für Microsoft hololens waren wir gespannt darauf zu sehen, wie weit wir die Grenzen der räumlichen Zuordnung auf dem Gerät Übertragung konnten.
author: jevertt
ms.author: jemccull
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, hololens, räumliche Zuordnung
ms.openlocfilehash: 5142cb383d4408b29eb17eb5ede84d19b2533dc4
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436723"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a>Fallstudie: Erweitern der räumlichen Mapping-Funktionen von hololens

Beim Erstellen unserer ersten Apps für Microsoft hololens waren wir gespannt darauf zu sehen, wie weit wir die Grenzen der räumlichen Zuordnung auf dem Gerät Übertragung konnten. Jeff evertt, ein Softwareentwickler bei Microsoft Studio, erläutert, wie eine neue Technologie entwickelt wurde, um mehr Kontrolle über die Platzierung von holograms in der realen Umgebung eines Benutzers zu erhalten.

> [!NOTE]
> Hololens 2 implementiert eine neue [Szene zum Verständnis der Laufzeit](scene-understanding.md), die Entwicklern gemischter Realität eine strukturierte, hochwertige Umgebungs Darstellung bietet, die entwickelt wurde, um die Entwicklung für Anwendungen mit hoher Ebene intuitiv zu gestalten. 

## <a name="watch-the-video"></a>Video ansehen

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a>Über räumliche Zuordnung hinaus

Beim Arbeiten an [Fragmenten](https://www.microsoft.com/p/fragments/9nblggh5ggm8) und [jungen](https://www.microsoft.com/p/young-conker/9nblggh5ggk1)den ersten spielen für hololens stellten wir fest, dass wir bei der prozeduralen Platzierung von holograms in der physischen Welt ein höheres Maß an Kenntnissen benötigten. Umgebung. Jedes Spiel verfügte über eigene spezifische Platzierungs Anforderungen: in Fragmenten wollten wir beispielsweise zwischen verschiedenen Oberflächen unterscheiden können – z. b. dem Boden oder einer Tabelle – um Hinweise an relevanten Positionen zu platzieren. Wir wollten auch in der Lage sein, Oberflächen zu identifizieren, auf denen holografische Zeichen in der Größe, z. b. ein Couch oder ein Stuhl, angeordnet werden können. Wir wollten, dass sich der zusammengesetzte und seine Angreifer in der Groß-und klein Sprache eines Players als Plattformen verwenden können.

[Asobo Studio](https://www.asobostudio.com/index.html), unser Entwicklungspartner für diese Spiele, stieß auf dieses Problem und erstellte eine Technologie, die die räumlichen Zuordnungsfunktionen von hololens erweitert. Dabei konnten wir den Raum eines Players analysieren und Oberflächen wie Wände, Tabellen, Stühle und Fußböden identifizieren. Außerdem haben wir die Möglichkeit, eine Reihe von Einschränkungen zu optimieren, um die beste Platzierung für Holographic-Objekte zu ermitteln.

## <a name="the-spatial-understanding-code"></a>Der räumliche Verständnis Code

Wir haben den ursprünglichen Code von Asobo erstellt und eine Bibliothek erstellt, die diese Technologie kapselt. Microsoft und Asobo haben nun diesen Code geöffnet und auf [mixedrealitytoolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) zur Verfügung gestellt, sodass Sie Sie in ihren eigenen Projekten verwenden können. Der gesamte Quellcode ist enthalten, sodass Sie ihn an Ihre Anforderungen anpassen und die Verbesserungen für die Community freigeben können. Der Code für den C++ Solver wurde in eine UWP-dll umschließt und Unity mit einem in [mixedrealitytoolkit enthaltenen Drop-in-Prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding)verfügbar gemacht.

Im Unity-Beispiel sind viele nützliche Abfragen enthalten, die es Ihnen ermöglichen, leere Leerzeichen auf Wänden zu finden, Objekte an der Oberfläche zu platzieren, Objekte auf der Oberfläche zu platzieren, Positionen für die Platzierung von Zeichen zu ermitteln und unzählige andere Abfragen für räumliche Abfragen durchzusetzen.

Die von hololens bereitgestellte räumliche Mappinglösung ist so konzipiert, dass Sie so generisch genug ist, dass Sie die Anforderungen der gesamten Bereiche von Problembereichen erfüllt, das räumliche Verständnis Modul wurde erstellt, um die Anforderungen von zwei bestimmten spielen zu unterstützen. Daher wird die Lösung um einen bestimmten Prozess und eine Reihe von Annahmen strukturiert:
* **Playspace mit fester Größe**: der Benutzer gibt die maximale Playspace-Größe im Init-Befehl an.
* **Einmal Scanvorgang**: der Prozess erfordert eine diskrete Scan Phase, in der der Benutzer durchläuft und den Playspace definiert. Abfragefunktionen funktionieren erst, nachdem die Überprüfung abgeschlossen wurde.
* **Benutzergesteuerte Playspace-"Zeichnung"** : während der Überprüfungsphase wird der Benutzer durch den Wiedergabe Bereich bewegt und den Wiedergabe Bereich durchsucht. Dadurch werden die Bereiche, die eingeschlossen werden sollen, tatsächlich gezeichnet. Das generierte Mesh ist wichtig, um Benutzer Feedback in dieser Phase bereitzustellen.
* **Home-oder Office-Einrichtung im Innenbereich**: die Abfragefunktionen werden um flache Oberflächen und Wände im rechten Winkel entworfen. Dies ist eine weiche Einschränkung. Während der Scan Phase wird jedoch eine primäre Achsen Analyse abgeschlossen, um das Gitter Mosaik entlang der Haupt-und der Nebenachse zu optimieren.

### <a name="room-scanning-process"></a>Raum Scanprozess

Wenn Sie das Modul für räumliche Kenntnisse laden, müssen Sie zuerst Ihren Platz überprüfen, sodass alle verwendbaren Oberflächen, – z. b. die Boden-, Ceiling-und Wände –, identifiziert und gekennzeichnet werden. Während des Scanvorgangs sehen Sie sich Ihren Raum an und zeichnen die Bereiche, die in die Überprüfung eingeschlossen werden sollen.

Das Mesh, das in dieser Phase gesehen wird, ist ein wichtiges visuelles Feedback, mit dem Benutzer wissen können, welche Teile des Raums gescannt werden. Die DLL für das Spatial Understanding-Modul speichert den Playspace intern als Raster von Voxel-Cubes mit 8 cm. Während des ersten Teils der Überprüfung wird eine Analyse der primären Komponenten abgeschlossen, um die Achsen des Raums zu ermitteln. Intern speichert Sie seinen Voxel-Bereich, der auf diese Achsen ausgerichtet ist. Ein Mesh wird ungefähr jede Sekunde generiert, indem die Isofläche aus dem Voxel-Volume extrahiert wird.

![Räumliche Zuordnung in weiß und verstehen des Playspace-Mesh in grün](images/spatial-mapping-500px.png)

Räumliche Zuordnung in weiß und verstehen des Playspace-Mesh in grün



Die enthaltene SpatialUnderstanding.cs-Datei verwaltet den Scan Phasen Prozess. Die folgenden Funktionen werden aufgerufen:
* **SpatialUnderstanding_Init**: einmal am Anfang aufgerufen.
* **GeneratePlayspace_InitScan**: gibt an, dass die scanphase beginnen soll.
* **GeneratePlayspace_UpdateScan_DynamicScan**: jeder Frame wird aufgerufen, um den Scanvorgang zu aktualisieren. Die Kameraposition und-Ausrichtung wird weitergegeben und wird für den oben beschriebenen Zeichnungsprozess von Playspace verwendet.
* **GeneratePlayspace_RequestFinish**: wird aufgerufen, um den Playspace abzuschließen. Dabei werden die Bereiche "gezeichnet" während der Überprüfungsphase verwendet, um den Playspace zu definieren und zu sperren. Die Anwendung kann während der Überprüfungsphase Statistiken Abfragen und das benutzerdefinierte Mesh zum Bereitstellen von Benutzer Feedback Abfragen.
* **Import_UnderstandingMesh**: während der Überprüfung fragt das von dem-Modul bereitgestellte **spatialverhalingcustommesh** -Verhalten und das Einverständnis der Prefab in regelmäßigen Abständen das vom Prozess generierte benutzerdefinierte Mesh ab. Außerdem wird dies nach Abschluss der Überprüfung noch einmal durchgeführt.

Der Scanvorgang, der vom **spatialunderstanding** -Verhalten gesteuert wird, ruft **initscan**auf und **aktualisiert** dann jeden Frame. Wenn die Statistik Abfrage eine angemessene Abdeckung meldet, kann der Benutzer auf " **requestfinish** " antippen, um das Ende der Scan Phase anzugeben. **Updatescan** wird weiterhin aufgerufen, bis der Rückgabewert angibt, dass die dll die Verarbeitung abgeschlossen hat.

## <a name="the-queries"></a>Die Abfragen

Nachdem die Überprüfung durchgeführt wurde, können Sie auf drei verschiedene Arten von Abfragen in der Schnittstelle zugreifen:
* **Topologieabfragen**: Hierbei handelt es sich um schnelle Abfragen, die auf der Topologie des gescannten Raums basieren.
* **Shape-Abfragen**: diese verwenden die Ergebnisse der Topologieabfragen, um horizontale Oberflächen zu suchen, die für benutzerdefinierte Formen geeignet sind, die Sie definieren.
* **Objekt Platzierungs Abfragen**: Hierbei handelt es sich um komplexere Abfragen, die den am besten geeigneten Speicherort basierend auf einem Satz von Regeln und Einschränkungen für das Objekt finden.

Zusätzlich zu den drei primären Abfragen gibt es eine Raycasting-Schnittstelle, die verwendet werden kann, um markierte Oberflächentypen abzurufen, und ein benutzerdefiniertes wasserdichtes Raum Mesh kann kopiert werden.

### <a name="topology-queries"></a>Topologieabfragen

Innerhalb der DLL übernimmt der topologiemanager die Bezeichnung der Umgebung. Wie bereits erwähnt, werden viele der Daten in Surfels gespeichert, die in einem Voxel-Volume enthalten sind. Außerdem wird die **playspaceinfos** -Struktur zum Speichern von Informationen über den Playspace verwendet, einschließlich der Welt Ausrichtung (weitere Details hierzu finden Sie unten), der Boden-und der Ceiling-Höhe.

Heuristiken werden zum Bestimmen von Boden, Ceiling und Wänden verwendet. Beispielsweise wird die größte und niedrigste horizontale Oberfläche mit einer Größe von mehr als 1 m2 als Floor betrachtet. Beachten Sie, dass der Kamerapfad während des Scanvorgangs auch in diesem Prozess verwendet wird.

Eine Teilmenge der Abfragen, die vom topologiemanager verfügbar gemacht werden, wird über die dll verfügbar gemacht. Die verfügbar gemachten Topologieabfragen lauten wie folgt:
* QueryTopology_FindPositionsOnWalls
* QueryTopology_FindLargePositionsOnWalls
* QueryTopology_FindLargestWall
* QueryTopology_FindPositionsOnFloor
* QueryTopology_FindLargestPositionsOnFloor
* QueryTopology_FindPositionsSittable

Jede der Abfragen verfügt über eine Reihe von Parametern, die für den Abfragetyp spezifisch sind. Im folgenden Beispiel gibt der Benutzer die Mindesthöhe & Breite des gewünschten Volumes, die minimale Platzierungs Höhe oberhalb der Etage und den minimalen Abstand vor dem Volume an. Alle Messungen befinden sich in Meter.




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

Jede dieser Abfragen nimmt ein vorab zugeordenes Array von **topologyresult** -Strukturen an. Der **locationcount** -Parameter gibt die Länge des übergebenen Arrays an. Der Rückgabewert meldet die Anzahl der zurückgegebenen Speicherorte. Diese Zahl ist nie größer als der übergebenen **locationcount** -Parameter.

Das **topologyresult** enthält die Mittelpunkt Position des zurückgegebenen Volumes, die Richtung (d. h. Normal) und die Dimensionen des gefundenen Speicherplatzes.




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

Beachten Sie, dass im Unity-Beispiel jede dieser Abfragen mit einer Schaltfläche im Bereich der virtuellen Benutzeroberfläche verknüpft ist. Im Beispiel werden die Parameter für jede dieser Abfragen in angemessene Werte fest codiert. Weitere Beispiele finden Sie unter *SpaceVisualizer.cs* im Beispielcode.

### <a name="shape-queries"></a>Shape-Abfragen

Innerhalb der dll verwendet der Shape Analyzer (**ShapeAnalyzer_W**) die topologieanalyse, um mit den vom benutzerdefinierten benutzerdefinierten Formen zu vergleichen. Das Unity-Beispiel verfügt über eine vordefinierte Gruppe von Formen, die im Menü Abfrage auf der Registerkarte Form angezeigt werden.

Beachten Sie, dass die Formanalyse nur auf horizontalen Oberflächen funktioniert. Eine Couch wird z. b. durch die flache Arbeitsplatz Oberfläche und den flachen oberen Rand der Couch zurückgelegt. Die Shape-Abfrage sucht nach zwei Oberflächen mit einer bestimmten Größe, Höhe und einem bestimmten Seitenbereich, wobei die beiden Oberflächen ausgerichtet und verbunden sind. Mithilfe der APIs-Terminologie sind der Couch-und der obere Rand des Couch Form Komponenten, und die Ausrichtungs Anforderungen sind Shape-Komponenten Einschränkungen.

Eine Beispiel Abfrage, die im Unity-Beispiel (**ShapeDefinition.cs**) für "sitfähige" Objekte definiert ist, lautet wie folgt:




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

Jede Shape-Abfrage wird durch einen Satz von Form Komponenten definiert, die jeweils über einen Satz von Komponenten Einschränkungen und einen Satz von Form Einschränkungen verfügen, der Abhängigkeiten zwischen den Komponenten auflistet. Dieses Beispiel enthält drei Einschränkungen in einer einzelnen Komponenten Definition und keine Formen Einschränkungen zwischen Komponenten (da nur eine Komponente vorhanden ist).

Im Gegensatz dazu hat die Form "Couch" zwei Form Komponenten und vier Form Einschränkungen. Beachten Sie, dass die Komponenten durch ihren Index in der Komponentenliste des Benutzers (0 und 1 in diesem Beispiel) identifiziert werden.




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

Wrapper Funktionen werden im Unity-Modul bereitgestellt, um eine einfache Erstellung benutzerdefinierter Formen Definitionen zu erstellen. Die vollständige Liste der Komponenten-und Shape-Einschränkungen finden Sie in **SpatialUnderstandingDll.cs** innerhalb der **shapecomponenteinschränkung** und der **shapeconstraint** -Strukturen.

![Mit dem blauen Rechteck werden die Ergebnisse der Form Abfrage "Stuhl" hervorgehoben.](images/chair-shape-query-500px.png)

Mit dem blauen Rechteck werden die Ergebnisse der Form Abfrage "Stuhl" hervorgehoben.



### <a name="object-placement-solver"></a>Objektplatzierungs-Solver

Objekt Platzierungs Abfragen können verwendet werden, um ideale Positionen im physischen Raum zu identifizieren, um die Objekte zu platzieren. Der Solver findet den Standort mit der optimalen Anpassung anhand der Objekt Regeln und Einschränkungen. Außerdem bleiben Objekt Abfragen so lange erhalten, bis das Objekt mit **Solver_RemoveObject** -oder **Solver_RemoveAllObjects** -aufrufen entfernt wird, sodass die eingeschränkte Platzierung von mehreren Objekten ermöglicht wird.

Objekt Platzierungs Abfragen bestehen aus drei Teilen: Platzierungs Typ mit Parametern, eine Liste von Regeln und eine Liste von Einschränkungen. Verwenden Sie die folgende API, um eine Abfrage auszuführen:




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
Diese Funktion nimmt einen Objektnamen, eine Platzierungs Definition und eine Liste von Regeln und Einschränkungen an. Die C# Wrapper stellen Konstruktions Hilfsfunktionen zur Verfügung, um die Erstellung von Regeln und Einschränkungen zu vereinfachen. Die Platzierungs Definition enthält den Abfragetyp – d. h. einen der folgenden:




```
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

Jeder der Platzierungs Typen hat eine Reihe von Parametern, die für den Typ eindeutig sind. Die **objectplacementdefinition** -Struktur enthält einen Satz statischer Hilfsfunktionen zum Erstellen dieser Definitionen. Wenn Sie z. b. einen Speicherort zum Platzieren eines Objekts im Boden finden möchten, können Sie die folgende Funktion verwenden: 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

Zusätzlich zum Platzierungs Typ können Sie einen Satz von Regeln und Einschränkungen bereitstellen. Regeln können nicht verletzt werden. Mögliche Platzierungs Speicherorte, die den Typ und die Regeln erfüllen, werden dann anhand des Satzes von Einschränkungen optimiert, um den optimalen Speicherort für die Platzierung auszuwählen. Alle Regeln und Einschränkungen können von den bereitgestellten statischen Erstellungs Funktionen erstellt werden. Eine Beispiel Regel und eine Einschränkungs Erstellungs Funktion finden Sie unten.




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

Die nachstehende Objekt Platzierungs Abfrage sucht nach einem Ort, an dem der Rand einer Oberfläche von anderen zuvor angehalgten Objekten und nahe der Mitte des Raums entfernt wird.




```
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

Bei erfolgreicher Ausführung wird eine **objectplacementresult** -Struktur mit der Platzierungsposition, den Dimensionen und der Ausrichtung zurückgegeben. Außerdem wird die Platzierung der internen Liste der platzierten Objekte der dll hinzugefügt. Bei nachfolgenden Platzierungs Abfragen wird dieses Objekt berücksichtigt. Die **LevelSolver.cs** -Datei im Unity-Beispiel enthält weitere Beispielabfragen.

![In den blauen Feldern wird das Ergebnis von drei Stellen in Floor-Abfragen mit der Regel "Weg von der Kameraposition" angezeigt.](images/away-from-camera-position-500px.png)

In den blauen Feldern wird das Ergebnis von drei Stellen in Floor-Abfragen mit der Regel "Weg von der Kameraposition" angezeigt.


**Chti**
* Wenn Sie den Speicherort für die Platzierung mehrerer für ein ebenenszenario oder ein Anwendungsszenario benötigtes Objekte auflösen, lösen Sie zunächst unentbehrliche und große Objekte aus, um die Wahrscheinlichkeit zu maximieren, dass ein Speicherplatz
* Die Platzierungs Reihenfolge ist wichtig. Wenn die Platzierung von Objekten nicht gefunden werden kann, versuchen Sie es mit weniger eingeschränkten Konfigurationen. Eine Reihe von Fall Back Konfigurationen ist wichtig für die Unterstützung von Funktionen in vielen Raum Konfigurationen.

### <a name="ray-casting"></a>Strahl Umwandlung

Zusätzlich zu den drei primären Abfragen kann eine Strahl Umwandlungs Schnittstelle verwendet werden, um markierte Oberflächentypen abzurufen, und ein benutzerdefiniertes, wasserdichtes Playspace-Mesh kann nach dem Scannen und Fertigstellen des Raums kopiert werden. Bezeichnungen werden intern für Oberflächen wie die Fußboden, Ceiling und Wände. Die **playspaceraycast** -Funktion nimmt einen Strahl an und gibt zurück, wenn der Strahl mit einer bekannten Oberfläche kollidiert. wenn dies der Fall ist, werden Informationen über diese Oberfläche in Form von " **raycastresult**" angezeigt. 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

Intern wird der raycast anhand der berechneten Voxel-Darstellung im 8cm-Format des Playspace berechnet. Jeder Voxel enthält einen Satz von Oberflächenelementen mit verarbeiteten Topologiedaten (auch als Surfels bezeichnet). Der Surfels, der in der überschneidenden Voxel-Zelle enthalten ist, wird verglichen und die beste Entsprechung für die Suche nach den Topologieinformationen. Diese Topologieinformationen enthalten die Bezeichnung, die in Form der **surfacetypes** -Aufzählung zurückgegeben wird, sowie den Oberflächen Bereich der überschneidenden Oberfläche.

Im Unity-Beispiel wandelt der Cursor einen Strahl in jedem Frame um. Zuerst für Unity-Kollisionen; Zweitens, mit der Welt Darstellung des Understanding-Moduls und schließlich für die Elemente der Benutzeroberfläche. In dieser Anwendung erhält die Benutzeroberfläche Priorität, dann das Verständnis Ergebnis und schließlich Unity-Kollisionen. Der **surfaketype** wird als Text neben dem Cursor gemeldet.

![Schnittmenge der raycast-ergebnisberichterstattung mit dem Boden.](images/raycast-result-500px.jpg)

Schnittmenge der raycast-ergebnisberichterstattung mit dem Boden.


## <a name="get-the-code"></a>Beziehen des Codes

Der Open Source-Code ist in [mixedrealitytoolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)verfügbar. Informieren Sie uns in den [hololens-Entwickler Foren](https://forums.hololens.com/) , wenn Sie den Code in einem Projekt verwenden. Wir können nicht warten, um zu sehen, was Sie mit Ihnen tun!

## <a name="about-the-author"></a>Informationen zum Autor

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <b>Jeff evertt</b> ist ein Software Entwicklungsleiter, der seit den frühen Tagen an hololens gearbeitet hat, von der Inkubation bis hin zur Entwicklung. Vor hololens arbeitete er an der Xbox kinect und in der Spielebranche auf einer Vielzahl von Plattformen und spielen. Jeff ist mit der Robotik, Grafik und den Dingen mit den Beleuchtung von Beleuchtung ausgestattet. Er lernt neue Dinge und arbeitet an Software, Hardware und besonders in dem Bereich, in dem sich die beiden überschneiden.</td>
</tr>
</table>



## <a name="see-also"></a>Weitere Informationen:
* [Räumliche Abbildung](spatial-mapping.md)
* [Grundlegendes zu Szenen](scene-understanding.md)
* [Raumabtastvisualisierung](room-scan-visualization.md)
* [Mixedrealitytoolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Asobo Studio: Lektionen aus der an vorderster Front der hololens-Entwicklung](https://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
