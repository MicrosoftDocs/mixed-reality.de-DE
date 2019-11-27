---
title: Scene Understanding SDK
description: Programmier Handbuch zum Scene Understanding SDK
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: Szenen Verständnis, räumliche Zuordnung, Windows Mixed Reality, Unity
ms.openlocfilehash: f365b0444576e03acd8dba194d7f8f24175e7bee
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539521"
---
# <a name="scene-understanding-sdk-overview"></a>Übersicht über das Szene Verständnis von SDK

Das Ziel des szenarienverständnisses besteht darin, die nicht strukturierten Umgebungs Sensordaten zu transformieren, die ihr Mixed Reality-Gerät erfasst, und Sie in eine leistungsstarke, aber abstrahierte Darstellung umzuwandeln, die intuitiv und einfach zu entwickeln ist. Das SDK fungiert als Kommunikationsschicht zwischen Ihrer Anwendung und der Szene zur Laufzeit. Sie ist darauf ausgerichtet, vorhandene standardkonstrukte wie 3D--Szenen Diagramme für 3D--Darstellungen und 2D-Rechtecke/Panels für 2D-Anwendungen zu imitieren. Die Konstrukte der Konstrukte verstehen sich zwar konkreten Frameworks, die Sie möglicherweise verwenden, aber im Allgemeinen ist das Framework unabhängig von der frameworkinterität eine Interoperabilität zwischen unterschiedlichen Frameworks, die mit ihr interagieren. Wenn das Verständnis von Szenen weiterentwickelt wird, besteht die Rolle des SDK darin, dass neue Darstellungen und Funktionen weiterhin in einem vereinheitlichten Framework verfügbar gemacht werden. In diesem Dokument werden zunächst allgemeine Konzepte vorgestellt, die Ihnen helfen, sich mit der Entwicklungsumgebung und-Nutzung vertraut zu machen und dann eine ausführlichere Dokumentation für bestimmte Klassen und Konstrukte bereitzustellen.

## <a name="where-do-i-get-the-sdk"></a>Wo erhalte ich das SDK?

Das sceneunderstanding SDK kann über nuget heruntergeladen werden.

[Sceneunderstanding-SDK](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

**Hinweis:** die neueste Version hängt von den Vorschau Paketen ab, und Sie müssen die Vorabversion von Paketen aktivieren, um Sie anzuzeigen.

Ab Version 0.5.2022-RC unterstützt Szenen Verständnis sprach Projektionen für C# und ermöglicht C++ Anwendungen das Entwickeln von Anwendungen für Win32-oder UWP-Plattformen. Ab dieser Version unterstützt sceneunderstanding die Unterstützung von Unity im Editor, wobei der sceneobserver, der ausschließlich für die Kommunikation mit HoloLens2 verwendet wird, verwendet wird. 

Sceneunderstanding erfordert Windows SDK-Version 18362 oder höher. 

Wenn Sie das SDK in einem Unity-Projekt verwenden, verwenden Sie [nuget für Unity](https://github.com/GlitchEnzo/NuGetForUnity) , um das Paket in Ihrem Projekt zu installieren.

## <a name="conceptual-overview"></a>Konzeptionelle Übersicht

### <a name="the-scene"></a>Die Szene

Ihr gemischtes Reality-Gerät integriert ständig Informationen zu den in Ihrer Umgebung angezeigten Informationen. In der Szene werden alle diese Datenquellen verstanden und eine einzelne, zusammenhängende Abstraktion erzeugt. Szenen Verständnis generiert Szenen, bei denen es sich um eine Komposition von [sceneobjects](scene-understanding-SDK.md#sceneobjects) handelt, die eine Instanz eines einzelnen Objekts darstellen (z. b. eine Wand/Ceiling/Floor). Szenen Objekte selbst sind eine Komposition von [scenecomponents](scene-understanding-SDK.md#scenecomponents) , die präziseste Teile darstellen, die dieses sceneobject bilden. Beispiele für Komponenten sind Quads und Meshes, aber in der Zukunft könnten Begrenzungs Felder, Kollisions Netze, Metadaten usw. darstellen.

Der Prozess der Umstellung der Rohdaten des Sensors in eine Szene ist ein potenziell kostspieliger Vorgang, der für sehr große Leerzeichen (~ 10X 10m) bis zu Minuten für sehr große Leerzeichen (~ 50X 50M) Sekunden in Anspruch nehmen kann und daher nicht vom Gerät berechnet wird. Anwendungsanforderung. Stattdessen wird die Szenen Generierung von Ihrer Anwendung Bedarfs gesteuert ausgelöst. Die sceneobserver-Klasse verfügt über statische Methoden, die eine Szene berechnen oder deserialisieren können, die Sie dann auflisten/mit der Sie interagieren können. Die "Compute"-Aktion wird Bedarfs gesteuert ausgeführt und wird auf der CPU ausgeführt, aber in einem separaten Prozess (dem Mixed Reality-Treiber). Während wir in einem anderen Prozess berechnen, werden die resultierenden Szenen Daten jedoch in der Anwendung im Scene-Objekt gespeichert und verwaltet. 

Das folgende Diagramm veranschaulicht den Prozessfluss und zeigt Beispiele für zwei Anwendungen an, die mit der Laufzeitumgebung vertraut sind. 

![Prozessdiagramm](images/SU-ProcessFlow.png)

Auf der linken Seite befindet sich ein Diagramm der Mixed Reality-Laufzeit, die immer aktiv ist und in einem eigenen Prozess ausgeführt wird. Diese Laufzeit ist für die Durchführung von Geräte Nachverfolgung, räumlicher Zuordnung und anderen Vorgängen zuständig, die von der Szene verstanden werden, um die Welt zu verstehen und zu verstehen. Auf der rechten Seite des Diagramms zeigen wir zwei theoretische Anwendungen, die das Verständnis von Szenen nutzen. Die erste Anwendung stellt mit mrtk eine Schnittstelle dar, die das Scene Understanding SDK intern verwendet, die zweite App berechnet und verwendet zwei separate Szenen Instanzen. In allen drei Szenen in diesem Diagramm werden unterschiedliche Instanzen der Kulissen generiert. der Treiber verfolgt keinen globalen Status, der von Anwendungen gemeinsam genutzt wird, und Szenen Objekte in einer Szene werden nicht in einer anderen Szene gefunden. Das Verständnis von Szenen bietet einen Mechanismus, mit dem Sie die Zeit nachverfolgen können. Dies geschieht jedoch mithilfe des SDKs, und der Code, der diese Nachverfolgung ausführt, wird im SDK im App-Prozess ausgeführt.

Da jede Szene Ihre Daten im Speicherbereich Ihrer Anwendung speichert, können Sie davon ausgehen, dass alle Funktionen des Szene Objekts oder der internen Daten immer im Prozess ihrer Anwendung ausgeführt werden.

### <a name="layout"></a>Layout

Um mit dem Verständnis von Szenen zu arbeiten, ist es möglicherweise hilfreich zu wissen, wie die Laufzeit Komponenten logisch und physisch repräsentiert. Die Szene stellt Daten mit einem bestimmten Layout dar, das als einfach gewählt wurde, während eine zugrunde liegende Struktur beibehalten wird, die für zukünftige Anforderungen geeignet ist, ohne dass größere Revisionen erforderlich sind. In der Szene werden alle Komponenten (Bausteine für alle Szene Objekte) in einer flachen Liste gespeichert, und die Hierarchie und Komposition werden durch Verweise definiert, bei denen bestimmte Komponenten auf andere verweisen.

Im folgenden finden Sie ein Beispiel für eine Struktur in der flachen und logischen Form.

<table>
<tr><th>Logisches Layout</th><th>Physisches Layout</th></tr>
<tr>
<td>
<ul>
  Unfallort
  <ul>
  <li>SceneObject_1
    <ul>
      <li>SceneMesh_1</li>
      <li>SceneQuad_1</li>
      <li>SceneQuad_2</li>
    </ul>
  </li>
  <li>SceneObject_2
    <ul>
      <li>SceneQuad_1</li>
      <li>SceneQuad_3</li>
      </li></ul>
  </li>
  <li>SceneObject_3
    <ul>
      <li>SceneMesh_3</li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li>SceneObject_1</li>
  <li>SceneObject_2</li>
  <li>SceneObject_3</li>
  <li>SceneQuad_1</li>
  <li>SceneQuad_2</li>
  <li>SceneQuad_3</li>
  <li>SceneMesh_1</li>
  <li>SceneMesh_2</li>
</ul>
</td>
</tr>
</table>

In dieser Abbildung wird der Unterschied zwischen dem physischen und dem logischen Layout der Szene hervorgehoben. Auf der linken Seite sehen Sie das hierarchische Layout der Daten, die Ihre Anwendung beim Auflisten der Szene sieht. Auf der rechten Seite sehen Sie, dass die Szene tatsächlich aus 12 unterschiedlichen Komponenten besteht, auf die bei Bedarf einzeln zugegriffen werden kann. Bei der Verarbeitung einer neuen Szene erwarten wir, dass Anwendungen diese Hierarchie logisch durchlaufen. bei der Überwachung zwischen Szenen Aktualisierungen sind einige Anwendungen jedoch möglicherweise nur für bestimmte Komponenten interessant, die von zwei Szenen gemeinsam genutzt werden.

## <a name="api-overview"></a>API-Übersicht

Der folgende Abschnitt enthält eine allgemeine Übersicht über die Konstrukte in der Szene. In diesem Abschnitt erfahren Sie, wie Szenen dargestellt werden und für welche Komponenten die verschiedenen Komponenten verwendet werden. Im nächsten Abschnitt werden konkrete Codebeispiele und zusätzliche Details bereitgestellt, die in dieser Übersicht ausgeblendet sind.

Alle unten beschriebenen Typen befinden sich im `Microsoft.MixedReality.SceneUnderstanding`-Namespace.

### <a name="scenecomponents"></a>Scenecomponents

Nachdem Sie nun das logische Layout von Szenen verstanden haben, können wir nun das Konzept der scenecomponents und deren Verwendung zum Verfassen der Hierarchie vorstellen. Scenecomponents sind die differenzierteren Dekompositionen in sceneunderstanding, die ein einzelnes Kernstück darstellen, z. b. ein Mesh-, ein Quad-oder ein Begrenzungsfeld. Scenecomponents sind Dinge, die unabhängig voneinander aktualisiert werden können und von anderen scenecomponents referenziert werden können. Daher verfügen Sie über eine einzelne globale Eigenschaft, die eine eindeutige ID für diese Art von Nachverfolgung/Verweis Mechanismus zulässt. IDs werden sowohl für die logische Komposition der Szenen Hierarchie als auch für die Objekt Persistenz verwendet (der Vorgang der Aktualisierung einer Szene relativ zu einer anderen). 

Wenn Sie jede neu berechnete Szene als unterschiedlich behandeln und einfach alle darin enthaltenen Daten auflisten, sind die IDs größtenteils für Sie transparent. Wenn Sie jedoch planen, Komponenten über mehrere Updates zu verfolgen, verwenden Sie die IDs, um scenecomponents zwischen Szene Objekten zu indizieren und zu suchen.

### <a name="sceneobjects"></a>Sceneobjects

Ein sceneobject ist eine scenecomponent, die eine Instanz eines "Thing" darstellt, z. b. eine Wand, eine Fläche, eine Obergrenze usw... ausgedrückt durch ihre Kind-Eigenschaft. Sceneobjects sind geometrisch und verfügen daher über Funktionen und Eigenschaften, die ihre Position im Raum darstellen, Sie enthalten jedoch keine geometrische oder logische Struktur. Stattdessen verweisen sceneobjects auf andere scenecomponents, insbesondere scenequads und scenemesches, die die unterschiedlichen Darstellungen bereitstellen, die vom System unterstützt werden. Wenn eine neue Szene berechnet wird, listet Ihre Anwendung wahrscheinlich die sceneobjects der Szene auf, um zu verarbeiten, was Sie interessiert.

Sceneobjects können eine der folgenden Möglichkeiten aufweisen:

<table>
<tr>
<th>Sceneobjectkind</th> <th>Beschreibung</th>
</tr>
<tr><td>Hintergrund</td><td>Das sceneobject-Objekt ist bekannt, dass es sich <b>nicht</b> um eines der anderen erkannten Arten von Szenen Objekten handelt. Diese Klasse sollte nicht mit unknown verwechselt werden, wenn der Hintergrund bekanntermaßen nicht "Wall/Floor/Ceiling" ist usw... Obwohl unbekannt noch nicht kategorisiert ist.</b></td></tr>
<tr><td>And</td><td>Eine physische Wand. Wände werden als unveränderbare Umgebungs Strukturen angesehen.</td></tr>
<tr><td>Steh</td><td>Die Ebenen sind beliebige Oberflächen, auf denen eine durchlaufen werden kann. Hinweis: die Treppe sind keine Ebenen. Beachten Sie auch, dass die Fußböden eine beliebige über-und-Oberfläche voraussetzen und daher keine explizite Annahme eines Singular ist. Strukturen mit mehreren Ebenen, Rampen usw... sollten alle als Floor klassifiziert werden.</td></tr>
<tr><td>Grenze</td><td>Die Oberfläche eines Raums.</td></tr>
<tr><td>Plattform</td><td>Eine große flache Oberfläche, auf der Sie holograms platzieren können. Diese stellen tendenziell Tabellen, Countertops und andere große horizontale Flächen dar.</td></tr>
<tr><td>World</td><td>Eine reservierte Bezeichnung für geometrische Daten, die für die Bezeichnung agnostisch ist. Das Mesh, das durch Festlegen des enableworldmesh-UpdateFlags generiert wird, würde als Welt klassifiziert werden.</td></tr>
<tr><td>Unbekannt</td><td>Dieses Scene-Objekt muss noch klassifiziert und zugewiesen werden. Dies sollte nicht mit dem Hintergrund verwechselt werden, da es sich bei diesem Objekt um beliebige Elemente handeln könnte. das System ist noch nicht mit einer ausreichend starken Klassifizierung ausgestattet.</td></tr>
</tr>
</table>

### <a name="scenemesh"></a>SceneMesh

Eine scenemesh ist eine scenecomponent, die die Geometrie willkürlicher geometrischer Objekte mithilfe einer Dreiecks Liste angleicht. Scenemesches werden in verschiedenen Kontexten verwendet, Sie können Komponenten der wasserdichten Zellstruktur oder als worldmesh darstellen, das das ungebundene räumliche zustrukturnetz darstellt, das der Szene zugeordnet ist. Die für jedes Mesh bereitgestellten Index-und Vertex-Daten verwenden dasselbe vertraute Layout wie der [Scheitelpunkt und die Index Puffer](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) , die zum Rendern von Dreiecksnetzen in allen modernen renderingapis verwendet werden. Beachten Sie, dass in der Szene in der Szene 32-Bit-Indizes verwendet werden und möglicherweise für bestimmte renderingengines in Blöcke aufgeteilt werden müssen.

#### <a name="winding-order-and-coordinate-systems"></a>Sortieren von Reihenfolge und Koordinatensystemen

Alle Netzen, die von der Szene verstanden werden, sollten in einem rechts gerichteten Koordinatensystem mithilfe der Reihenfolge im Uhrzeigersinn die Netzen zurückgeben. 

Hinweis: Betriebssystem-Builds vor. 191105 verfügen möglicherweise über einen bekannten Fehler, bei dem "World"-Netzen in der Reihenfolge gegen den Uhrzeigersinn zurückgegeben wurden, die anschließend korrigiert wurde.

### <a name="scenequad"></a>Scenequad

Eine scenequad ist eine scenecomponent, die 2D-Oberflächen darstellt, die die 3D--Welt belegen. Scenequads können ähnlich wie Arkit arplaneanchor oder Arcore-Ebenen verwendet werden, bieten jedoch eine höhere Funktionalität als 2D-canvasen, die von flachen Apps verwendet werden sollen, oder erweiterte UX. 2D-spezifische APIs werden für Quads bereitgestellt, mit denen die Platzierung und das Layout einfach zu verwenden sind, und die Entwicklung (mit Ausnahme des Renderings) mit Quads sollte eher dem Arbeiten mit 2D-kanvasen als 3D--Meshes ähneln.

#### <a name="scenequad-shape"></a>Scenequad-Form

Scenequads definieren eine begrenzte rechteckige Oberfläche in 2D. Scenequads stellen jedoch Oberflächen mit beliebigen und potenziell komplexen Formen dar (z. b. eine ringförmige Tabelle). Wenn Sie die komplexe Form der Oberfläche eines viervieres darstellen möchten, können Sie die getsurfacemask-API verwenden, um die Form der Oberfläche auf einem von Ihnen bereitgestellten Bild Puffer zu Renderern. Wenn das sceneobject mit dem Quad auch ein Mesh hat, sollten die Gitter Dreiecke diesem gerenderten Bild entsprechen, beide stellen eine echte Geometrie der Oberfläche dar, nur in 2D-oder 3D--Koordinaten.

## <a name="scene-understanding-sdk-details-and-reference"></a>Scene Understanding SDK-Details und-Referenz

Im folgenden Abschnitt wird erläutert, wie Sie mit den Grundlagen von sceneunderstanding vertraut werden. In diesem Abschnitt werden die Grundlagen erläutert. zu diesem Zeitpunkt sollten Sie über genügend Kontext verfügen, um die Beispielanwendungen zu durchsuchen und zu sehen, wie sceneunderstanding ganzheitlich genutzt wird.

### <a name="initialization"></a>Initialisierung

Der erste Schritt bei der Arbeit mit sceneunderstanding besteht darin, dass Ihre Anwendung auf ein Szene Objekt verweist. Dies kann auf zwei Arten erfolgen: eine Szene kann entweder vom Treiber berechnet werden, oder eine vorhandene Szene, die in der Vergangenheit berechnet wurde, kann deserialisiert werden. Letzteres ist besonders nützlich für das Arbeiten mit sceneunderstanding während der Entwicklung, bei dem Anwendungen und Erfahrungen schnell ohne ein gemischtes Reality-Gerät prototypisiert werden können.

Szenen werden mithilfe eines sceneobserver berechnet. Bevor Sie eine Szene erstellen, sollte Ihre Anwendung Ihr Gerät Abfragen, um sicherzustellen, dass Sie sceneunderstanding unterstützt, sowie den Benutzer Zugriff auf Informationen anfordern, die von sceneunderstanding benötigt werden.

```cs
if (SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

Wenn requestaccessasync () nicht aufgerufen wird, tritt beim Berechnen einer neuen Szene ein Fehler auf. Als Nächstes berechnen wir eine neue Szene, die auf dem Mixed Reality-Headset liegt und über einen Radius von 10 Metern verfügt.

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-aka-the-pc-path"></a>Initialisierung aus Daten (auch als bezeichnet). der PC-Pfad)

Szenen können für den direkten Verbrauch berechnet werden, Sie können jedoch auch in serialisierter Form für die spätere Verwendung berechnet werden. Dies hat sich als sehr nützlich für die Entwicklung erwiesen, da Entwickler damit arbeiten können, ohne dass ein Gerät benötigt wird. Der Vorgang der Serialisierung einer Szene ist nahezu identisch mit dem berechnen, die Daten werden an Ihre Anwendung zurückgegeben, anstatt lokal vom SDK deserialisiert zu werden. Sie können Sie dann selbst deserialisieren oder zur späteren Verwendung speichern.

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneBlob for later
```

### <a name="sceneobject-enumeration"></a>Sceneobject-Enumeration

Nun, da Ihre Anwendung eine Szene hat, wird Ihre Anwendung mit sceneobjects beschäftigt und interagiert. Dies erfolgt durch den Zugriff auf die **sceneobjects** -Eigenschaft:

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-re-finding-components"></a>Komponenten Aktualisierung und-Suche

Es gibt eine weitere Funktion, die Komponenten in der Szene abruft, die als ***findComponent***bezeichnet werden. Diese Funktion ist nützlich, wenn Überwachungs Objekte aktualisiert und in nachfolgenden Szenen gefunden werden. Mit dem folgenden Code wird eine neue Szene in Relation zu einer vorherigen Szene berechnet und dann die Fläche in der neuen Szene gefunden.

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a>Zugreifen auf Meshes und Quads von Szenen Objekten

Nachdem sceneobjects gefunden wurde, möchte Ihre Anwendung wahrscheinlich auf die Daten zugreifen, die in den in den Metadaten/Meshes enthaltenen Daten enthalten sind, aus denen Sie besteht. Der Zugriff auf diese Daten erfolgt über die Eigenschaften " ***Quads*** " und " ***Meshes*** ". Mit dem folgenden Code werden alle Quads und Netzen des Floor-Objekts aufgelistet.

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

Beachten Sie, dass es sich um das sceneobject-Objekt mit der Transformation handelt, die relativ zum Ursprung der Szene ist. Der Grund hierfür ist, dass das sceneobject-Objekt eine Instanz eines "Thing" darstellt und im Raum einstellbar ist, die Quads und die Netze stellen eine Geometrie dar, die relativ zu ihrem übergeordneten Element transformiert wird. Es ist möglich, dass separate sceneobjects auf die gleichen scenemesh/scenequad scenecomponents verweisen. Außerdem ist es möglich, dass ein sceneobject-Objekt über mehr als eine scenemesh/scenequad verfügt.

### <a name="dealing-with-transforms"></a>Umgang mit Transformationen

Das Verständnis der Szene hat beim Umgang mit Transformationen einen absichtlichen Versuch unternommen, an herkömmlichen 3D-Szenen Darstellungen auszurichten. Daher ist jede Szene auf ein einzelnes Koordinatensystem beschränkt, ähnlich wie die gängigsten 3D-Umwelt Darstellungen. Sceneobjects stellen jeweils ihren Speicherort als Position und Ausrichtung innerhalb dieses Koordinatensystems bereit. Wenn Ihre Anwendung mit Szenen beschäftigt ist, die das Limit eines einzelnen Ursprungs überschreiten, können Sie sceneobjects an spatialanchor anfügen oder mehrere Szenen generieren und zusammen zusammenführen, aber aus Gründen der Einfachheit gehen wir davon aus, dass die wasserdichten Szenen eigenständig vorhanden sind. der Ursprung, der durch eine durch "Scene. originspatialgraphnodeid" definierte NodeId lokalisiert wird.

Der folgende Unity-Code zeigt beispielsweise, wie Sie die Windows-perception-und Unity-APIs verwenden, um Koordinatensysteme gleich abzustimmen. Unter [spatialcoordinatesystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) und [spatialgraphinteroppreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) finden Sie ausführliche Informationen zu den Windows-perception-APIs und den systemeigenen [gemischt-Objekten in Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) . hier finden Sie ausführliche Informationen zum Abrufen eines spatialcoordinatesystem, das den Unity- der Ursprung der Welt und die `.ToUnity()` Erweiterungsmethode für die Umstellung zwischen `System.Numerics.Matrix4x4` und `UnityEngine.Matrix4x4`.

```cs
public class SceneRootComponent : MonoBehavior
{
    public SpatialCoordinateSystem worldOrigin;
    public Scene scene;
    SpatialCoordinateSystem sceneOrigin;
    
    void Start()
    {
        // Initialize a SpatialCoordinateSystem for the scene's node in the system's Spatial Graph.
        scene.origin = SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
    }
    
    void Update()
    {
        // Try to get the current transform of the scene's spatial graph node.
        // This may not be available, e.g. when tracking has been lost.
        var sceneToWorld = sceneOrigin.TryGetTransformTo(worldOrigin);
        if (sceneToWorld.HasValue)
        {
            // Convert the transform to Unity numerics and update the game object.
            var sceneToWorldUnity = sceneToWorld.Value.ToUnity();
            this.gameObject.transform.SetPositionAndRotation(sceneToWorldUnity.GetColumn(3), sceneToWorldUnity.rotation);
        }
    }
}
```

Jede `SceneObject` verfügt über eine `Position` und `Orientation`-Eigenschaft, die verwendet werden kann, um den entsprechenden Inhalt relativ zum Ursprung der enthaltenden `Scene`zu positionieren. Im folgenden Beispiel wird z. b. davon ausgegangen, dass das Spiel ein untergeordnetes Element des Szenen Stamms ist, und seine lokale Position und Drehung zugewiesen, um Sie an einem angegebenen `SceneObject`auszurichten:

```cs
void SetLocalTransformFromSceneObject(GameObject gameObject, SceneObject sceneObject)
{
    gameObject.transform.localPosition = sceneObject.Position.ToUnity();
    gameObject.transform.localRotation = sceneObject.Orientation.ToUnity());
}
```

### <a name="quad"></a>Quad

Die Quads wurden entwickelt, um 2D-Platzierungs Szenarios zu vereinfachen. Sie sollten sich als Erweiterungen für 2D-Canvas-UX-Elemente vorstellen. Obwohl es sich bei den Quads um Komponenten von sceneobjects handelt, die in 3D gerendert werden können, werden die Quad-APIs selbst annehmen, dass die Quad- Sie bieten Informationen wie Block, Form und Bereitstellen von APIs für die Platzierung.

Die Unterbrechungen haben rechteckige Blöcke, stellen aber beliebig geformte 2D-Oberflächen dar. Um die Platzierung auf diesen 2D-Oberflächen zu ermöglichen, die mit der 3D-Umgebung interagieren, bieten Sie Hilfsprogramme, um diese Interaktion zu ermöglichen. Das grundlegendes Verständnis von Szenen bietet derzeit zwei dieser Funktionen: **findcentermustplacement** und **gedecclusionmask**. Findcentermostplacement ist eine API auf hoher Ebene, die eine Position auf dem Quad sucht, an der ein Objekt platziert werden kann, und versucht, den optimalen Speicherort für das Objekt zu finden, das sicherstellt, dass sich das umgebende Feld auf der zugrunde liegenden Oberfläche befindet.

Im folgenden Beispiel wird gezeigt, wie Sie den am häufigsten ersetzbaren Speicherort suchen und ein – Hologramm für das Vierfache verankern.

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

Die Schritte 1-4 sind stark von Ihrem speziellen Framework/der Implementierung abhängig, die Designs sollten jedoch ähnlich sein. Es ist wichtig zu beachten, dass das Vierfache eine begrenzte 2D-Ebene darstellt, die im Raum lokalisiert wird. Wenn Ihr Modul/Framework weiß, wo das Vierfache ist, und die Objekte in Relation zum Quad Hogen, werden Ihre Hologramme in Bezug auf die reale Welt ordnungsgemäß gefunden. Ausführlichere Informationen finden Sie in unseren Beispielen zu den Quads, in denen bestimmte Implementierungen angezeigt werden.

### <a name="mesh"></a>Schigen

Meshes stellen geometrische Darstellungen von Objekten oder Umgebungen dar. Ähnlich wie bei der [räumlichen Zuordnung](spatial-mapping.md)verwendet Mesh-Index-und Vertex-Daten, die für jedes räumliche Oberflächen Mesh bereitgestellt werden, dasselbe vertraute Layout wie der Scheitelpunkt und die Index Puffer, die zum Rendern von Dreiecksnetzen in allen modernen Rendering-APIs verwendet werden. Vertex-Positionen werden im Koordinatensystem der `Scene`bereitgestellt. Die spezifischen APIs, die zum Verweisen auf diese Daten verwendet werden, lauten wie folgt:

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

Der folgende Code enthält ein Beispiel für das Erstellen einer Dreiecks Liste aus der Mesh-Struktur:

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

Der Index/der Scheitelpunkt Puffer muss > = der Index/Scheitelpunkt Anzahl sein, kann aber auch willkürlich skaliert werden, um eine effiziente Wiederverwendung von Arbeitsspeicher zu ermöglichen.

## <a name="developing-with-scene-understandings"></a>Entwickeln mit Szenen Verständnissen

An diesem Punkt sollten Sie die wichtigsten Bausteine der Szene verstehen, die Laufzeit und SDK versteht. Der größte Teil der Leistungsfähigkeit und Komplexität liegt in Zugriffs Mustern, der Interaktion mit 3D-Frameworks und Tools, die zusätzlich zu diesen APIs verfasst werden können, um erweiterte Aufgaben wie räumliche Planung, Raumanalyse, Navigation, Physik usw. auszuführen. Wir hoffen, diese Beispiele in Beispielen zu erfassen, die Sie in die richtige Richtung bringen sollten, um Ihre Szenarios zu glänzen. Wenn Beispiele/Szenarios nicht behandelt werden, informieren Sie uns, und wir versuchen, das Dokument/den Prototyp zu dokumentieren.

### <a name="where-can-i-get-sample-code"></a>Wo kann ich Beispielcode erhalten?

Szeneninformationen zum Beispielcode für Unity finden Sie auf unserer Seite mit der [Unity-Beispielseite](https://github.com/sceneunderstanding-microsoft/unitysample) . Diese Anwendung ermöglicht Ihnen die Kommunikation mit Ihrem Gerät und das Rendering der verschiedenen Szenen Objekte, oder Sie können eine serialisierte Szene auf Ihren PC laden und das Verständnis von Szenen ohne Gerät ermöglichen.

### <a name="where-can-i-get-sample-scenes"></a>Wo kann ich Beispiel Szenen erhalten?

Wenn Sie über eine HoloLens2 verfügen, können Sie jede Szene speichern, die Sie erfasst haben, indem Sie die Ausgabe von "computeserializedasync" in der Datei speichern und Sie in ihrer eigenen Weise deserialisieren. 

Wenn Sie nicht über ein HoloLens2-Gerät verfügen, aber mit Szenen Verständnis experimentieren möchten, müssen Sie eine vorab erfasste Szene herunterladen. Das Beispiel für Szenen Verständnis wird derzeit in serialisierten Szenen geliefert, die Sie herunterladen und in ihrer eigenen Weise verwenden können. Sie finden Sie hier:

[Szenen Einblick in Beispiel Szenen](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

## <a name="see-also"></a>Weitere Informationen:

* [Räumliche Abbildung](spatial-mapping.md)
* [Grundlegendes zu Szenen](scene-understanding.md)
* [Unity-Beispiel](https://github.com/sceneunderstanding-microsoft/unitysample)
