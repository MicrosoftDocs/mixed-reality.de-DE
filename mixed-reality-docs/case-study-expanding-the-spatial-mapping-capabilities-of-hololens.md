---
title: 'Fallstudie: erweitern die räumlichen Funktionen für die Zuordnung von HoloLens'
description: Beim Erstellen von unserem ersten apps für Microsoft HoloLens konnten wir sehr daran interessiert, finden, wie weit wir die Grenzen der räumliche Zuordnung auf dem Gerät mithilfe von Push übertragen können.
author: jevertt
ms.author: jevertt
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, räumliche Zuordnung
ms.openlocfilehash: 602b629afa5900ff34c28b3a3a32725af06590b7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595754"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a>Fallstudie: erweitern die räumlichen Funktionen für die Zuordnung von HoloLens

Beim Erstellen von unserem ersten apps für Microsoft HoloLens konnten wir sehr daran interessiert, finden, wie weit wir die Grenzen der räumliche Zuordnung auf dem Gerät mithilfe von Push übertragen können. Jeff Evertt, Software Engineer bei Microsoft Studios, wird erläutert, wie eine neue Technologie entwickelt wurde, aus die Notwendigkeit zur besseren Steuerung, wie Hologramme, in die reale Umgebung des Benutzers platziert werden.

## <a name="watch-the-video"></a>Video ansehen

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a>Über die räumliche Zuordnung

Während wir arbeiteten [Fragmente](https://www.microsoft.com/p/fragments/9nblggh5ggm8) und [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), zwei der ersten Spiele für HoloLens, wir festgestellt, dass wenn wir mit Anleitungen Platzierung Hologramme in der realen Welt ausführen, wir eine höhere Sicherheitsstufe erforderlich Kenntnisse über die Umgebung des Benutzers. Jedes Spiel musste eine eigene Anforderungen der jeweiligen Platzierung: In Fragmenten, z. B. wollten wir zwischen verschiedenen Oberflächen unterscheiden können, z. B. dem Boden oder eine Tabelle – Hinweise in Orten zu platzieren. Wir wollten auch in der Lage Oberflächen zu identifizieren, die zweifachen der Originalgröße holographic Zeichen, z. B. ein Sofa oder einen Stuhl befinden können. In Conker Young wollten wir Conker und seine Gegner ausgelöste Flächen in des Spielers Raum als Plattformen verwenden können.

[Asobo Studios](http://www.asobostudio.com/index.html), unsere Entwicklungspartner dieser Spiele, treffen Sie uns dieses Problem, und erstellt Sie eine Technologie, die die räumlichen Funktionen für die Zuordnung von HoloLens erweitert. Anhand dieser konnten wir Analysieren des Spielers Platz und Oberflächen wie z. B. Wände, Tabellen, Stühle und Stockwerken identifizieren. Auch haben wir die Möglichkeit, anhand einer Reihe von Einschränkungen, um zu bestimmen, den besten Unterbringungsort für holographic Objekte zu optimieren.

## <a name="the-spatial-understanding-code"></a>Der räumliche verstehen von code

Wir haben Asobos ursprünglichen Codes und erstellt eine Bibliothek, die diese Technologie kapselt. Microsoft und Asobo jetzt diesen Code als Open Source und auf zur Verfügung gestellt haben [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) in Ihren eigenen Projekten verwenden. Der gesamte Quellcode ist enthalten, sodass Sie an Ihre Anforderungen anpassen und Ihrer Verbesserungen mit der Community teilen. Der Code für die C++ Solver umschlossen in eine UWP-DLL und für Unity mit verfügbar gemacht wurde eine [direkter Prefab MixedRealityToolkit enthaltenen](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).

Es gibt viele nützliche Abfragen, die das Unity-Beispiel, mit denen Sie Leerzeichen Wände finden, fügen Sie Objekte aus, an der Decke oder große Speicherplätze auf dem Boden, stellen für Zeichen befindet und unzählige andere Abfragen räumlicher Grundlegendes zu identifizieren.

Zwar allgemein genug, um die Anforderungen die gesamte Palette von Problembereiche werden räumliche Zuordnung-Lösung von HoloLens ausgelegt ist, wurde das räumliche Verständnis-Modul erstellt, um die Anforderungen von zwei bestimmte Spiele zu unterstützen. Daher ist die Lösung für einen bestimmten Prozess und eine Reihe von Annahmen strukturiert:
* **Feste Größe Playspace**: Der Benutzer gibt die maximale Playspace-Größe in der Init-Aufruf.
* **Einmalige Überprüfung**: Der Prozess erfordert eine diskrete Phase, in denen der Benutzer, um führt, zu überprüfen, die Playspace definieren. Abfragefunktionen funktionieren nicht erst, nachdem die Überprüfung abgeschlossen wurde.
* **Benutzergesteuerte Playspace "Zeichnen"**: Während der Überprüfungsphase wird der Benutzer wechselt und sieht sich die Playspace, für die tatsächlich Zeichnen der Bereiche, die einbezogen werden sollen. Das generierte Netz ist wichtig, Feedback von Benutzern bereitzustellen, während dieser Phase.
* **In geschlossenen Räumen Heim- oder Setup**: Die Abfragefunktionen werden für flache Flächen und Wände rechtwinklig konzipiert. Dies ist eine weiche Einschränkung. Jedoch wird während der Überprüfungsphase, eine Analyse der primären Achse abgeschlossen, um das Netz Mosaik Haupt- und Nebenversionsnummern Achse zu optimieren.

### <a name="room-scanning-process"></a>Raum Scanningprozess

Wenn Sie das Modul räumliche Grundlegendes zu laden, das erste, was Sie tun wird Ihrem Bereich, also die verwendbaren Oberflächen zu überprüfen, wie z. B. die Floor, Ceiling und Wände – identifiziert und gekennzeichnet werden. Während des Scanvorgangs, suchen Sie Ihr Platz und "Farbe" der Bereiche, die in die Überprüfung enthalten sein sollen.

Das Netz während dieser Phase ist ein wichtiger Bestandteil von visuellem Feedback, mit dem Benutzer wissen, welche Teile des Raums gescannt werden. Die DLL für das räumliche Grundlegendes zu Modul speichert intern die Playspace als ein Raster aus 8cm Größe Voxel Cubes. Während des ersten Teils Scannen ist eine Hauptkomponente Analyse abgeschlossen, um zu bestimmen, die Achsen des Raums. Sie speichert intern Voxel Speicherplatzes ausgerichtet, diese Achsen. Ein Mesh wird ungefähr pro Sekunde generiert, mit dem Extrahieren der Isofläche aus dem Voxel Volume.

![Räumliche Zuordnung Mesh in Weiß und Verstehen von Playspace mesh in Grün](images/spatial-mapping-500px.png)

Räumliche Zuordnung Mesh in Weiß und Verstehen von Playspace mesh in Grün



Der eingebundenen Datei SpatialUnderstanding.cs verwaltet den Scanvorgang-Phase. Es ruft die folgenden Funktionen:
* **SpatialUnderstanding_Init**: Am Anfang einmal aufgerufen.
* **GeneratePlayspace_InitScan**: Gibt an, dass die Scan-Phase beginnen soll.
* **GeneratePlayspace_UpdateScan_DynamicScan**: Wird aufgerufen, jeden Frame aus, um die Suche zu aktualisieren. Die Position (Kamera) und die Ausrichtung übergeben wird, und wird für den Playspace zeichnen, oben beschriebenen Prozess verwendet.
* **GeneratePlayspace_RequestFinish**: Wird aufgerufen, um die Playspace abzuschließen. Hierbei werden die Bereiche "gezeichnet", während der Überprüfung-Phase definieren und die Playspace Sperren verwendet. Statistiken kann von die Anwendung während der Überprüfung Phase sowie Abfrage benutzerdefinierte Mesh für die Bereitstellung von Feedback von Benutzern Abfragen.
* **Import_UnderstandingMesh**: Während des Scanvorgangs, der **SpatialUnderstandingCustomMesh** Verhalten, die vom Modul bereitgestellt, und klicken Sie auf das Prefab Verständnis platziert wird vom Prozess generierten benutzerdefinierte Mesh in regelmäßigen Abständen abgefragt. Darüber hinaus dies einmal erfolgt nach der Überprüfung beendet wurde.

Der Scan Flow, hängt von der **SpatialUnderstanding** Verhaltenaufrufe **InitScan**, klicken Sie dann **UpdateScan** jeden Frame. Wenn die Abfrage Statistiken angemessenen Coverage meldet, wird der Benutzer kann Airtap aufzurufende **RequestFinish** an das Ende der Überprüfungsphase. **UpdateScan** weiterhin aufgerufen werden, bis sie die Rückgabe ist der Wert gibt an, dass die DLL die Verarbeitung abgeschlossen wurde.

## <a name="the-queries"></a>Die Abfragen

Sobald die Überprüfung abgeschlossen ist, werden Sie drei verschiedene Typen von Abfragen in der Benutzeroberfläche zugreifen:
* **Abfragen der Topologie**: Hierbei handelt es sich um schnelle Abfragen, die auf die Topologie der überprüften Raum basieren.
* **Form von Abfragen**: Diese nutzen die Ergebnisse der Abfragen Topologie zur horizontalen Oberflächen zu finden, die eine gute Übereinstimmung benutzerdefinierte Formen sind, die Sie definieren.
* **Objektabfragen für die Platzierung**: Hierbei handelt es sich um eine komplexere Abfragen, die den Fallback mit ähnlichen Speicherort basierend auf einem Satz von Regeln und Einschränkungen für das Objekt zu suchen.

Zusätzlich zu den drei primären Abfragen eine feinheiten beim Raycasting Schnittstelle, mit dem markierte Oberflächentypen abgerufen werden kann, und einem benutzerdefinierten wasserdichte Platz Mesh kopiert werden kann.

### <a name="topology-queries"></a>Abfragen der Topologie

In der DLL behandelt Topologie-Manager die Bezeichnung der Umgebung. Wie oben erwähnt, wird ein Großteil der Daten in Surfels, gespeichert, die innerhalb eines Volumes Voxel enthalten sind. Darüber hinaus die **PlaySpaceInfos** Struktur wird zum Speichern von Informationen zu den Playspace, einschließlich der Welt, Ausrichtung (Weitere Einzelheiten hierzu finden Sie nachstehend), Floor und Ceiling Höhe.

Heuristik beim Ermitteln der werden verwendet, um zu bestimmen, Floor, Ceiling und Wänden. Beispielsweise gilt die größte und niedrigste horizontale Oberfläche mit mehr als 1 m2 Oberfläche den Boden. Beachten Sie, dass der Pfad "Kamera" während des Scanvorgangs auch in diesem Prozess verwendet wird.

Eine Teilmenge der Abfragen, die von der Topologie-Manager verfügbar gemacht werden über die DLL bereitgestellt. Die verfügbar gemachten Topologie-Abfragen sind wie folgt aus:
* QueryTopology_FindPositionsOnWalls
* QueryTopology_FindLargePositionsOnWalls
* QueryTopology_FindLargestWall
* QueryTopology_FindPositionsOnFloor
* QueryTopology_FindLargestPositionsOnFloor
* QueryTopology_FindPositionsSittable

Alle Abfragen verfügt über einen Satz von Parametern, die spezifisch für den Abfragetyp. Im folgenden Beispiel gibt den Benutzer, die minimale Höhe und Breite der gewünschte Volume, minimale Platzierung Höhe über dem Boden und die Mindestmenge an sicherheitsbestätigung vor dem Volume. Alle Messungen sind in Meter.




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

Jeder dieser Abfragen akzeptiert ein vorab zugeordnete Array von **TopologyResult** Strukturen. Die **LocationCount** Parameter gibt die Länge des übergebenen Arrays an. Der Rückgabewert gibt die Anzahl der zurückgegebenen Speicherorte. Diese Zahl ist niemals größer als der übergegebenen **LocationCount** Parameter.

Die **TopologyResult** enthält die zentrierte Textposition des zurückgegebenen Volumes, die zugänglichen Richtung (d. h. normal), und die Abmessungen des Bereich gefunden.




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

Beachten Sie, dass in der Unity-Beispiel, jeder dieser Abfragen sich auf eine Schaltfläche in der virtuellen Benutzeroberflächen-Panel verknüpft ist. Das Beispiel schwer-codes die Parameter für jede dieser Abfragen für Sie geeignete Standardwerte. Finden Sie unter *SpaceVisualizer.cs* im Beispielcode Weitere Beispiele.

### <a name="shape-queries"></a>Shape-Abfragen

Innerhalb der DLL, die dem Shape-Analyzer (**ShapeAnalyzer_W**) verwendet den Topologie-Analyzer für den Abgleich von benutzerdefinierter Formen, die vom Benutzer definiert. Im Unity-Beispiel verfügt über einen vordefinierten Satz von Formen, die Sie im Abfragemenü auf der Registerkarte "Form" gezeigt werden.

Beachten Sie, dass die Form-Analyse auf nur horizontale Oberflächen funktioniert. Ein Sofa, wird z. B. durch die Flatfile-Arbeitsplatz-Oberfläche und flache Anfang den Garten wieder definiert. Shape-Abfrage sucht nach zwei Oberflächen von einer bestimmten Größe, Höhe und Aspekt-Bereich mit den beiden Oberflächen ausgerichtet und verbunden. Verwenden die APIs Terminologie, sind Sofa Sitz und dem oberen Rand am Ende den Garten shape-Komponenten und die Ausrichtung, die Anforderungen sind Form Beschränkungen hinsichtlich der Komponenten.

Eine Beispielabfrage, die in der Unity-Beispiel definiert (**ShapeDefinition.cs**) für "sittable"-Objekte wie folgt:




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

Jedes Shape-Abfrage wird definiert durch eine Reihe von Komponenten der Form, jeweils eine Reihe von Beschränkungen hinsichtlich der Komponenten und einer Reihe von Form-Einschränkungen, die Abhängigkeiten zwischen den Komponenten aufgeführt sind. Dieses Beispiel enthält drei Einschränkungen in einer einzelnen Komponente-Definition und keine Einschränkungen der Form zwischen Komponenten, (wie es nur eine Komponente ist).

Im Gegensatz dazu verfügt über die Form Sofa, zwei Shape-Komponenten und Einschränkungen für vier Form. Beachten Sie, dass Komponenten anhand ihres Indexes in der Liste der Komponenten des Benutzers (0 und 1 in diesem Beispiel) identifiziert werden.




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

Wrapperfunktionen werden zur einfachen Erstellung von Definitionen für benutzerdefinierte Form, die im Unity-Modul bereitgestellt. Die vollständige Liste der Komponente und Form-Einschränkungen finden Sie **SpatialUnderstandingDll.cs** innerhalb der **ShapeComponentConstraint** und **ShapeConstraint** Strukturen sind.

![Das blaue Rechteck hervorgehoben, die Ergebnisse der Stuhl Shape-Abfrage.](images/chair-shape-query-500px.png)

Das blaue Rechteck hervorgehoben, die Ergebnisse der Stuhl Shape-Abfrage.



### <a name="object-placement-solver"></a>Die Platzierung Solver Objekt

Objektabfragen für die Platzierung können verwendet werden, um ideal Orte im physischen Raum platzieren Ihrer Objekte zu ermitteln. Der Solver findet den Fallback mit ähnlichen Speicherort, die Objektregeln und Einschränkungen. Darüber hinaus Objektabfragen beibehalten, bis das Objekt entfernt wird, mit **Solver_RemoveObject** oder **Solver_RemoveAllObjects** aufrufen, sodass eingeschränkte Platzierung Multi-Objekts.

Platzierung von Objektabfragen bestehen aus drei Teilen: die Platzierungstyp mit Parametern, eine Liste der Regeln und eine Liste der Einschränkungen. Verwenden Sie zum Ausführen einer Abfrage, die folgende API:




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
Diese Funktion akzeptiert ein Objektname, Platzierungsdefinition und eine Liste von Regeln und Einschränkungen. Die C# Wrapper erstellen-bereitstellen-Hilfsfunktionen, damit die Regel oder Einschränkung Erstellung zu vereinfachen. Die Platzierungsdefinition enthält den Abfragetyp, d. h. eine der folgenden:




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

Alle Platzierungstypen, hat es sich um einen Satz von Parametern, die nur für den Typ. Die **ObjectPlacementDefinition** Struktur enthält eine Reihe von statischen Hilfsfunktionen für diese Definitionen zu erstellen. Um einer bestimmten Stelle ablegen ein Objekts auf dem Boden zu suchen, können Sie z. B. die folgende Funktion verwenden: 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

Zusätzlich zu die Platzierungstyp können Sie einen Satz von Regeln und Einschränkungen bereitstellen. Regeln können nicht verletzt werden. Mögliche Platzierung von Standorten, die den Typ und die Regeln erfüllen werden dann anhand des Satzes von Einschränkungen, um den Speicherort für die optimale Platzierung auszuwählen optimiert. Alle Regeln und Einschränkungen kann von den Funktionen für die angegebene statische Erstellung erstellt werden. Eine Beispiel-Regel und die Einschränkung der Konstruktorfunktion wird unten bereitgestellt.




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

Die Platzierung-Objektabfrage, die folgenden sucht nach einem Ort zu versetzen, einen Cube Hälfte Verbrauchseinheit am Rand einer Oberfläche, von anderen Objekten zuvor platzieren in der Nähe der Mitte des Raums.




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

Bei erfolgreicher Ausführung einen **ObjectPlacementResult** -Struktur mit der Platzierungsposition, die Dimensionen und die Ausrichtung wird zurückgegeben. Darüber hinaus wird die Platzierung des DLL interne Liste der platzierten Objekte hinzugefügt. Platzierung der nachfolgenden Abfragen werden dieses Objekt zu berücksichtigen. Die **LevelSolver.cs** -Datei im Unity-Beispiel enthält weitere Beispiele für Abfragen.

![Die blauen Felder zeigen das Ergebnis von drei direkt auf Floor-Abfragen mit "Weg von der Position (Kamera)" Regeln.](images/away-from-camera-position-500px.png)

Die blauen Felder zeigen das Ergebnis von drei direkt auf Floor-Abfragen mit "Weg von der Position (Kamera)" Regeln.


**Tipps:**
* Bei der Lösung für die Platzierung-Speicherort, der mehrere Objekte, die für ein Szenario Ebene oder eine Anwendung erforderlich sind, lösen Sie zuerst unerlässlich, und große Objekte, um die Wahrscheinlichkeit zu maximieren, die ein Leerzeichen befinden.
* Platzierung Reihenfolge ist wichtig. Wenn das Objekt Platzierungen nicht gefunden wird, versuchen Sie es weniger eingeschränkte Konfigurationen. Eine Reihe von Konfigurationen ist entscheidend für die Unterstützung von Funktionen in vielen Konfigurationen von Platz.

### <a name="ray-casting"></a>Chow Umwandlung

Zusätzlich zu den drei primären Abfragen kann eine Chow Umwandlung-Schnittstelle zum Abrufen von markierter Oberflächentypen verwendet werden und einem benutzerdefinierten wasserdichte Playspace Mesh kopiert werden kann, nachdem Raum überprüft und -Kundenbetreuungsteam abgewickelt, Bezeichnungen werden intern generiert für Oberflächen wie die Floor, Ceiling und Wände. Die **PlayspaceRaycast** Funktion akzeptiert ein Strahl und gibt Sie zurück, wenn der Strahl mit einer bekannten Oberfläche verursacht einen Konflikt, und wenn dies der Fall ist, Informationen, die dann in Form einer **RaycastResult**. 


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

Die Raycast wird intern für die berechnete 8 cm hoch drei Voxel Darstellung der Playspace berechnet. Jede Voxel enthält einen Satz von Surface-Elementen mit verarbeiteten Topologiedaten (auch bekannt als Surfels). Die in der Zelle überschneidungen Voxel enthaltenen Surfels verglichen werden, und die beste Übereinstimmung verwendet, um die Topologieinformationen zu suchen. Diese Topologiedaten enthalten die Bezeichnung in der Form des zurückgegebenen der **SurfaceTypes** Enum, sowie die Oberfläche der überschneidungen Oberfläche.

Im Unity-Beispiel wird der Cursor jeder Frame ein Strahl umgewandelt. Zunächst anhand von Unity-collider; Zweitens: für das Verständnis des Moduls-Welt-Darstellung; und schließlich für die Elemente der Benutzeroberfläche. In dieser Anwendung ruft ab die Benutzeroberfläche, Priorität, und klicken Sie dann das Ergebnis verstehen und schließlich von Unity-collider. Die **SurfaceType** wird als Text neben dem Cursor gemeldet.

![Raycast Ergebnisse Schnittmenge mit dem Boden.](images/raycast-result-500px.jpg)

Raycast Ergebnisse Schnittmenge mit dem Boden.


## <a name="get-the-code"></a>Code abrufen

Der Open-Source-Code ist verfügbar in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity). Lassen Sie uns auf die [HoloLens-Entwicklerforen](https://forums.hololens.com/) , wenn Sie den Code in einem Projekt verwenden. Wir können nicht warten, um festzustellen, was Sie damit tun!

## <a name="about-the-author"></a>Der Autor

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <b>Jeff Evertt</b> ist leitender Softwareentwicklung, der seit den Anfängen von Inkubation in die Entwicklung für HoloLens gearbeitet hat. Bevor Sie HoloLens arbeitete er auf der Xbox Kinect und in der Branche Spiele auf einer Vielzahl von Plattformen und Spiele. Tyge ist Leidenschaft Robotics, Grafiken und Aufgaben mit blinkenden Lichter, die akustisches Signal gesendet. Er genießt neue Dinge lernen, und arbeiten auf Software, Hardware, und zwar insbesondere in den Speicherplatz, auf denen sich die beiden überschneiden.</td>
</tr>
</table>



## <a name="see-also"></a>Siehe auch
* [Räumliche Zuordnung](spatial-mapping.md)
* [Räumliche Zuordnung entwerfen](spatial-mapping-design.md)
* [Die Überprüfung Visualisierung Platz](room-scan-visualization.md)
* [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Asobo Studio: Lektionen aus dem Front der Entwicklung für HoloLens](http://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
