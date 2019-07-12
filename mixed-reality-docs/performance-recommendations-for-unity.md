---
title: Empfehlungen zur Leistung für Unity
description: Unity-spezifische Tipps zum Verbessern der Leistung in mixed Reality-apps.
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: Grafiken, cpu, Gpu, rendering und Garbagecollection hololens
ms.openlocfilehash: b0821f07184bff8630f6b6af0d0fc461f6fcd133
ms.sourcegitcommit: 8f3ff9738397d9b9fdf4703b14b89d416f0186a5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "67843332"
---
# <a name="performance-recommendations-for-unity"></a>Empfehlungen zur Leistung für Unity

Dieser Artikel baut auf die Diskussion, die in beschriebenen [Empfehlungen zur Leistung für mixed Reality](understanding-performance-for-mixed-reality.md) aber konzentriert sich auf Erkenntnisse, die spezifisch für die Unity-Engine-Umgebung.

Es ist auch dringend empfohlen, dass Entwickler die [umgebungseinstellungen für die Unity-Artikel empfohlen](Recommended-settings-for-unity.md). Dieser Artikel enthält Inhalt, mit einigen der wichtigsten Szene Konfigurationen im Hinblick auf Leistung Mixed Reality-apps zu erstellen. Einige dieser empfohlenen Einstellungen werden auch hervorgehoben.

## <a name="how-to-profile-with-unity"></a>Wie Sie ein Profil mit Unity

Unity bietet die **[Unity-Profiler](https://docs.unity3d.com/Manual/Profiler.html)** integrierte handelt es sich hervorragend zum Sammeln von wertvollen Performance Insights für Ihre spezielle app. Auch wenn eine der Profiler im Editor ausgeführt werden kann, diese Metriken entsprechen nicht den true-Laufzeitumgebung und daher Ergebnisse aus dieser sollte verwendet werden mit Vorsicht. Es wird die für die genaue und verfolgbare Einblicke auf Gerät ausgeführte Anwendung Remote-Profil empfohlen. Darüber hinaus von Unity [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html) ist auch eine sehr leistungsfähige und Insight-Tool verwenden.

Unity bietet hervorragenden Dokumentation:
1) Herstellen einer Verbindung die [Unity-Profiler für UWP-Anwendungen per Remotezugriff](https://docs.unity3d.com/Manual/windowsstore-profiler.html)
2) Wie effektiv [Diagnostizieren von Leistungsproblemen im Zusammenhang mit der Unity-Profiler](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)

>[!NOTE]
> Mit der Unity-Profiler verbunden und nach dem Hinzufügen des GPU-Profilers (finden Sie unter *hinzufügen Profiler* in oberen rechten Ecke), sehen, wie viel Zeit für die CPU und GPU bzw. in der Mitte des Profilers aufgewendet wird. Dies kann der Entwickler eine schnelle Schätzung zu erhalten, wenn ihre Anwendung CPU oder GPU-gebunden ist.
>
> ![Unity CPU und GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>Empfehlungen zur CPU-Leistung

Der Inhalt weiter unten enthält weitere detaillierte Verfahren für die Leistung, insbesondere von gezielten für Unity & C# Entwicklung.

#### <a name="cache-references"></a>Cacheverweise

Es ist empfehlenswert, Cacheverweise auf alle relevanten Komponenten und "gameobjects" bei der Initialisierung. Dies ist, da die Funktionsaufrufe wiederholen, wie z. B. *[GetComponent\<T > ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* sind deutlich teurer relativ zu den Arbeitsspeicher, die Kosten um einen Zeiger zu speichern. Dies gilt auch für die sehr, regelmäßig verwendete [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html). *Camera.Main* verwendet tatsächlich nur *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* unterhalb der Prüfungsvorgänge Ihre szenengraph für ein Kameraobjekt mit sucht die *"MainCamera"*  Tag.

```CS
using UnityEngine;
using System.Collections;

public class ExampleClass : MonoBehaviour
{
    private Camera cam;
    private CustomComponent comp;

    void Start() 
    {
        cam = Camera.main;
        comp = GetComponent<CustomComponent>();
    }

    void Update()
    {
        // Good
        this.transform.position = cam.transform.position + cam.transform.forward * 10.0f;

        // Bad
        this.transform.position = Camera.main.transform.position + Camera.main.transform.forward * 10.0f;

        // Good
        comp.DoSomethingAwesome();

        // Bad
        GetComponent<CustomComponent>().DoSomethingAwesome();
    }
}
```

>[!NOTE] 
> Vermeiden Sie GetComponent(string) <br/>
> Bei Verwendung  *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* , es gibt eine Reihe verschiedener Überladungen. Es ist wichtig, immer die Implementierungen der Typ basiert, und nie die zeichenfolgenbasierte Suche Überladung zu verwenden. Suchen nach der Zeichenfolge in der Szene ist deutlich teurer als bei der Suche nach Typ. <br/>
> (Gut) Komponente GetComponent (Typ Type) <br/>
> (Gut) T GetComponent\<T >) <br/>
> (Negativen) Komponente GetComponent(string) > <br/>

#### <a name="avoid-expensive-operations"></a>Vermeiden Sie teure Vorgänge

1) **Vermeiden Sie die Verwendung von [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**

    Obwohl LINQ sehr übersichtlich und leicht zu lesen und Schreiben von sein kann, erfordert es im Allgemeinen wesentlich umfangreichere Berechnungen und insbesondere Weitere speicherbelegung als manuell den Algorithmus schreiben.

    ```CS
    // Example Code
    using System.Linq;

    List<int> data = new List<int>();
    data.Any(x => x > 10);

    var result = from x in data
                 where x > 10
                 select x;
    ```

2) **Allgemeine Unity-APIs**

    Bestimmte Unity-APIs kann zwar nützlich, zum Ausführen sehr teuer sein. Die meisten dieser umfassen Ihre gesamte szenengraph für eine passende Liste mit "gameobjects" suchen. Diese Vorgänge können durch Zwischenspeichern der Verweise oder implementieren eine Manager-Komponente für die "gameobjects" betreffende um die Verweise zur Laufzeit zu verfolgen, in der Regel vermieden werden.

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> *[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)*  und *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* unter allen Umständen gelöscht werden soll. Diese Funktionen können Größenordnung von 1000 X langsamer als direkte Funktionsaufrufe sein.

3) **Beachten Sie, dass von boxing**

    [Boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) ist ein Kernkonzept von der C# Sprach- und Runtime. Es ist der Prozess der wrapping Wert typisierte Variablen wie Char "," Int "," Bool "," usw. in der Referenz typisierte Variablen. Wenn eine Variable Wert eingegeben "geschachtelt" wird, wird es in ein System.Object verwandelt umschlossen, der auf dem verwalteten Heap gespeichert wird. Daher wird Arbeitsspeicher belegt und schließlich entfernt von der Garbage Collector verarbeitet werden müssen. Diese speicherzuordnungen und Aufhebungen fallen Kosten der Leistung in vielen Szenarios sind nicht erforderlich und können einfach durch eine kostengünstigere Alternative ersetzt werden.

#### <a name="repeating-code-paths"></a>Sich wiederholende Codepfade

Alle wiederholten Rückruffunktionen für Unity (d.h.) Update), die mehrere Male pro Sekunde ausgeführt werden, und/oder Frame sehr sorgfältig geschrieben werden soll. Hier keine aufwändigen Vorgänge werden große und konsistent auf die Leistung auswirken.

1) **Leere Rückruffunktionen**

    Obwohl der folgende Code mag harmlosen in Ihrer Anwendung, insbesondere da jeder Unity-Skript automatisch initialisiert mit diesem Codeblock ist verlassen können diese leere Rückrufe tatsächlich sehr teuer werden. Unity wird hin-und über eine nicht verwaltete/verwaltete Code-Grenze zwischen UnityEngine und Ihrer Anwendungscode ausgeführt. Über diese Brücke zum Wechseln des Kontexts ist ziemlich teuer, selbst wenn nichts ausgeführt. Dies ist besonders problematisch, wenn Ihre app Hunderte "gameobjects" mit Komponenten verfügt, die leere wiederholten Unity-Rückrufe.

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> Update() ist die häufigste Manifestation dieses Leistungsproblem zu beheben, aber andere sich wiederholende Unity-Rückrufe wie den folgenden können ebenso als fehlerhaft, wenn es nicht schlimmer sein: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage(), etc. 

2) **Vorgänge bevorzugt ausgeführt wird, einmal pro Frame**

    Die folgenden Unity-APIs sind allgemeine Vorgänge für viele Apps, Holographic. Zwar nicht immer möglich, die Ergebnisse dieser Funktionen können sehr häufig einmal berechnet werden, und die Ergebnisse, die erneut für die Anwendung für einen bestimmten Frame verwendet werden.

    (a) im Allgemeinen ist es empfiehlt sich, eine dedizierte Singleton-Klasse oder ein Dienst zum Verarbeiten Ihrer Blicke Raycast in der Szene, und verwenden Sie dann erneut dieses Ergebnis in allen anderen Szene Komponenten, anstatt Sie wiederholte und im Wesentlichen identisch Raycast-Vorgänge von jedem Komponente. Natürlich können einige Anwendungen erfordern Raycasts verschiedener Herkunft oder für verschiedene [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html).

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    (b) vermeiden Sie GetComponent() Vorgänge im wiederholten Unity-Rückrufe wie Update() von [Zwischenspeichern Verweise](#cache-references) Start() oder Awake()

        UnityEngine.Object.GetComponent()

    (c) Es wird empfohlen, alle Objekte, wenn möglich, Initialisierung und Verwendung instanziiert [Objektpooling](#object-pooling) wiederverwenden, und verwenden "gameobjects" erneut in der gesamten Laufzeit der Anwendung

        UnityEngine.Object.Instantiate()

3) **Schnittstellen und virtuelle Konstrukte zu vermeiden**

    Aufrufen von Funktionsaufrufe über Schnittstellen Vs Verzeichnisobjekte oder das Aufrufen von virtuellen Funktionen können oft viel teurer als die Verwendung direkter Konstrukte oder direkte Funktionsaufrufe sein. Wenn die virtuelle Funktion oder die Schnittstelle nicht erforderlich ist, sollte er entfernt werden. Diese Ansätze für die Beeinträchtigung der serverleistung sind jedoch im Allgemeinen sollte einen Kompromiss Wenn nutzen diese Entwicklung Zusammenarbeit, Lesbarkeit des Codes und codeverwaltbarkeit von vereinfacht. 

4) **Vermeiden Sie nach Wert übergeben von Strukturen**

    Im Gegensatz zu Klassen Strukturen sind Werttypen, und wenn direkt an eine Funktion übergeben, deren Inhalt in eine neu erstellte Instanz kopiert. Diese Kopie wird die CPU-Kosten sowie zusätzlichen Arbeitsspeicher auf dem Stapel hinzugefügt. Bei kleinen Strukturen ist der Effekt in der Regel nur sehr geringe und somit akzeptabel. Allerdings für Funktionen wiederholt jedes Bild aufgerufen, als auch für Funktionen mit großer Strukturen ggf. Ändern der Definition der Funktion zur Übergabe als Verweis. [Hier erfahren Sie mehr](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a>Sonstiges

1) **Physik**

    (a) in der Regel ist einfachste Möglichkeit zur Verbesserung der Physik die Zeitspanne, die auf physikalische Eigenschaften oder die Anzahl der Iterationen, die pro Sekunde beschränken. Natürlich verringert das Simulation Genauigkeit. Finden Sie unter [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) in Unity

    (b) der Typ der collider in Unity haben häufig unterschiedliche Leistungsmerkmale. Die folgenden Reihenfolge aufgeführt, die meisten leistungsfähigen collider, mindestens leistungsfähigen collider von links nach rechts. Es ist am wichtigsten Collider Mesh zu vermeiden, die beträchtlich teurer als die primitiven collider sind.

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    Finden Sie unter [bewährte Methoden für Unity Physik](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) für Weitere Informationen

2) **Animationen**

    Deaktivieren Sie im Leerlauf Animationen durch das Deaktivieren der Animator-Komponente (deaktivieren das spielobjekt muss nicht die gleiche Auswirkung). Vermeiden Sie Entwurfsmuster, in denen ein Animator in einer Schleife, die eine Einstellung auf die gleiche Sache befindet. Es gibt viel Aufwand für dieses Verfahren hat keine Auswirkungen auf die Anwendung aus. [Hier erfahren Sie mehr.](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **Komplexe Algorithmen**

    Wenn Ihre Anwendung komplexe Algorithmen, z. B. inverse Kinematik, Pfad suchen usw. verwendet wird, suchen Sie, um einen einfacheren Ansatz suchen, oder passen die relevante Einstellungen für die Leistung

## <a name="cpu-to-gpu-performance-recommendations"></a>Empfehlungen zur CPU, GPU Leistung

Im Allgemeinen CPU-zu-GPU-Leistung wird nach unten, um die **zeichnen-Befehlen** an der Grafikkarte übermittelt. Zur Verbesserung der Leistung Draw-Aufrufe müssen strategisch **(a) reduziert** oder **(b) umstrukturiert** für optimale Ergebnisse zu erzielen. Da zeichnen-Befehlen selbst ressourcenintensiv sind, werden insgesamt Arbeitsaufwand reduzieren verringert. Darüber hinaus Status Änderungen zwischen zeichnen-Befehlen ist erforderlich, teure Validierung und Übersetzung Schritte des Grafiktreibers und daher Umstrukturierung von Ihrer Anwendung zeichnen-Befehlen zum Einschränken von Änderungen des Ansichtszustands (d.h.) andere Materialien, usw.) kann die Leistung gesteigert.

Unity ist einen großartiger Artikel, der bietet einer Übersicht über die und Batchverarbeitung Draw-Aufrufe Ihrer eigenen Plattform behandelt.
- [Unity zeichnen Aufruf Batchverarbeitung](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a>Durchlauf instanziierten rendering

Übergeben der einzelnen Instanced Rendering in Unity ermöglicht Draw-Aufrufe für jedes Auge auf einem instanziierten Draw-Aufruf reduziert werden sollen. Aufgrund der Cachekohärenz zwischen zwei zeichnen-Befehlen gibt es auch in der GPU sowie einige leistungsverbesserungen.

So aktivieren Sie dieses Feature in Ihrem Unity-Projekt
1)  Open **XR Playereinstellungen** (Wechseln Sie zu **bearbeiten** > **Projekteinstellungen** > **Player**  >  **XR-Einstellungen**)
2) Wählen Sie **einzelne Instanz übergeben** aus der **Stereo-Rendering-Methode** -Dropdownmenü (**virtuelle Realität unterstützt** Kontrollkästchen muss aktiviert sein)

Lesen Sie die folgenden Artikeln aus Unity Informationen bei diesem Ansatz rendern.
- [Gewusst wie: Maximieren der Leistung von AR und VR mit erweiterten Stereo-rendering](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [Übergeben Sie Single Instancing](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> Ein verbreitetes Problem mit einzelnen Rendering Instanz übergeben tritt auf, wenn Entwickler bereits vorhandene benutzerdefinierte Shadern, die nicht für geschriebenen Instanziierung. Nach der Aktivierung dieser Option werden Entwicklern einige "gameobjects" nur das Rendering in ein Auge feststellen. Dies ist, da die zugeordneten benutzerdefinierten Shadern nicht die entsprechenden Eigenschaften für die Instanziierung.
>
> Finden Sie unter [einzelne übergeben Stereo Rendering für HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) von Unity für das dieses Problem zu beheben

#### <a name="static-batching"></a>Statische Batchverarbeitung

Unity kann batch viele statische Objekte, um die Draw-Aufrufe an die GPU zu reduzieren. Statische Batchverarbeitung eignet sich für die meisten [Renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) Objekte in Unity, **1) Geben Sie die gleiche Material** und **(2) sind alle markierten als *statische***  () Wählen Sie ein Objekt in Unity, und klicken Sie auf das Kontrollkästchen in der oberen rechten des Inspektors). "Gameobjects" markiert, als *statische* kann nicht in Ihrer Anwendung Common Language Runtime verschoben werden. Daher kann statische Batchverarbeitung schwierig sein, auf HoloLens nutzen, in denen praktisch jedes Objekt platziert werden, verschoben, skalierte usw. muss. Für immersive Headsets statische Batchverarbeitung kann deutlich reduzieren, zeichnen-Befehlen und somit die Leistung verbessern.

Lesen *statische Batchverarbeitung* unter [zeichnen Batchverarbeitung aufrufen, in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) Weitere Details.

#### <a name="dynamic-batching"></a>Dynamische Batchverarbeitung

Da dies problematisch ist, um Objekte markieren ist *statische* für die Entwicklung für HoloLens, dynamische Batchverarbeitung möglich ein großartiges Tool, um dies zu kompensieren fehlen, für die Funktion. Es ist natürlich können auch auf auch immersive Headsets nützlich sein. Dynamische Batchverarbeitung in Unity kann schwierig sein, jedoch zu aktivieren, da "gameobjects" muss **(a) Freigabe der gleichen Material** und **(b) eine lange Liste von anderen Kriterien zu erfüllen**.

Lesen *dynamische Batchverarbeitung* unter [zeichnen Batchverarbeitung aufrufen, in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) für die vollständige Liste. "Gameobjects" werden in den meisten Fällen können nicht dynamisch zusammengefasst werden, da die zugeordnete Netzdaten nicht mehr als 300 Vertices werden können.

#### <a name="other-techniques"></a>andere Techniken

Batchverarbeitung kann nur auftreten, wenn mehrere "gameobjects" auf das gleiche Material freigeben können. In der Regel wird dies durch die Notwendigkeit, "gameobjects", damit eine eindeutige Struktur für ihre jeweiligen Material blockiert werden. Es ist üblich, Texturen in einer großen Textur, eine Methode, die als bekannt kombinieren [Textur Atlasing](https://en.wikipedia.org/wiki/Texture_atlas).

Darüber hinaus ist es in der Regel besser, als die Gitter in einem "gameobject" zu kombinieren, soweit dies möglich und sinnvoll. Jeder Renderer in Unity hat es verfügt über zugeordnete Draw API-Aufruf(e) im Vergleich zu einem kombinierten Mesh unter einem Renderer übermitteln. 

>[!NOTE]
> Ändern der Eigenschaften eines Renderer.material zur Laufzeit erstellt eine Kopie des Materials und somit zu schwerwiegenden Fehlern führen Batchverarbeitung. Verwenden Sie Renderer.sharedMaterial, um freigegebene Material-Eigenschaften für "gameobjects" zu ändern.

## <a name="gpu-performance-recommendations"></a>Empfehlungen zur GPU-Leistung

Erfahren Sie mehr über [Grafiken Renderingoptimierung in Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games) 

### <a name="optimize-depth-buffer-sharing"></a>Optimieren Sie die Tiefe Puffer freigeben

Es wird allgemein empfohlen, aktivieren **Tiefe Puffer freigeben** unter **XR Playereinstellungen** Optimierung [– Hologramm Stabilität](Hologram-stability.md). Wenn Tiefe basierende spät Phase Reprojection mit dieser Einstellung jedoch aktivieren, es wird empfohlen, wählen Sie **Tiefe von 16-Bit-Format** anstelle von **24-Bit-Tiefe Format**. Die Tiefe von 16-Bit-Puffer wird drastisch reduziert die Bandbreite (und somit power) Tiefe Puffer Datenverkehr zugeordnet. Dies kann ein großer Strom Gewinn, aber gilt nur für Umgebungen mit einem kleinen Tiefe Bereich als [Z-fighting](https://en.wikipedia.org/wiki/Z-fighting) werden eher mit 16-Bit-als 24-Bit-auftreten. Um diese Artefakte zu vermeiden, ändern Sie die in der Nähe/hinteren Ebenen des der [Unity Kamera](https://docs.unity3d.com/Manual/class-Camera.html) der geringeren Genauigkeit berücksichtigen. Für HoloLens-basierte Anwendungen kann eine hinteren Clippingebene von 50 Millionen anstelle des standardmäßigen Unity 1000m in der Regel alle Z-fighting vermeiden.

### <a name="reduce-poly-count"></a>Reduzieren Sie Poly-Anzahl

Polygonzahl wird in der Regel entweder reduziert.
1) Entfernen von Objekten aus einer Szene
2) Asset-Decimation dadurch die Anzahl von Polygonen, die für einen bestimmten Netz
3) Implementieren einer [Ebene von Details (LOD) System](https://docs.unity3d.com/Manual/LevelOfDetail.html) in Ihre Anwendung das weit entfernt Objekte mit niedrigerer-Polygon-Version der gleichen Geometrie gerendert wird

### <a name="understanding-shaders-in-unity"></a>Grundlegendes zu Shader in Unity

Eine einfache Annäherung, Shadern in Bezug auf Leistung verglichen werden soll. ist, identifizieren Sie die durchschnittliche Anzahl der einzelnen Vorgänge zur Laufzeit ausgeführt wird. Dies kann problemlos in Unity erfolgen.

1) Wählen Sie Ihr Medienobjekt Shader Material, und anschließend oben rechts im Inspektorfenster, wählen Sie das Zahnradsymbol und dann **"Shader auswählen"**

    ![Wählen Sie in Unity shader](images/Select-shader-unity.png)
2) Der Shader-Ressource ausgewählt haben, und klicken Sie auf die **"Kompilieren und Code anzeigen"** Schaltfläche unter Inspektor-Fenster

    ![Kompilieren von Shadercode in Unity](images/compile-shader-code-unity.PNG)

3) Nach dem Kompilieren, suchen Sie nach dem Abschnitt in den Ergebnissen und die Anzahl der verschiedenen Vorgänge für den Scheitelpunkt und den Pixel-Shader (Hinweis: Pixel-Shader werden häufig auch als Fragment Shader bezeichnet)

    ![Unity-Standard-Shader-Vorgänge](images/unity-standard-shader-compilation.png)

#### <a name="optmize-pixel-shaders"></a>Optmize-Pixel-Shader

Betrachten die kompilierten Statistik Ergebnisse mithilfe der oben genannten Methode die [fragment Shader](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) führt im Allgemeinen mehr Vorgänge als die [Vertex-Shader](https://en.wikipedia.org/wiki/Shader#Vertex_shaders) durchschnittlich. Pro Pixel auf dem Bildschirm ausgegeben werden, während der Vertex-Shader nur ausgeführte pro-Vertex von allen Netzen, die gerade auf dem Bildschirm gezeichnet wird, wird die fragmentshader, auch bekannt als der Pixel-Shader, ausgeführt. 

Daher nicht nur die Fragment-Shader verfügen mehrere Anweisungen als Vertex-Shader da alle beleuchtungsberechnungen, die Fragment-Shader auf ein größeres Dataset fast immer ausgeführt werden. Z. B. wenn auf dem Bildschirm eine 2 k 2 k-Image ist, klicken Sie dann die fragmentshader erhalten ausgeführt, 2, 000 * 2, 000 = 4,000,000 Zeiten. Wenn zwei Augen zu rendern, wird diese Zahl verdoppelt, da es sich um zwei Bildschirme. Verfügt eine mixed Reality-Anwendung, mehrere übergibt, Vollbild-Nachbearbeitung Effekte oder mehrere Gitter hinzuzufügen, um dasselbe Pixel zu rendern, wird diese Anzahl deutlich steigern. 

Aus diesem Grund erhalten reduziert die Anzahl der Vorgänge im fragmentshader in der Regel sehr viel größere Leistungssteigerungen über Optimierungen in den Vertex-Shader.

#### <a name="unity-standard-shader-alternatives"></a>Unity-Standard-Shader-alternativen

Anstatt ein physisch basierend Rendering (PBR) oder andere Shader qualitativ hochwertige, sehen Sie sich ein leistungsfähiger nutzen und kostengünstiger Shader. Die [Mixed Reality-Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) bietet die [MRTK standard-Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) , die für mixed Reality-Projekten optimiert wurde.

Unity bietet auch eine Unbeleuchtete, Vertex leuchtet, diffusen und andere vereinfachten Shader-Optionen, die erheblich schneller verglichen werden, an dem Unity-Standard-Shader. Finden Sie unter [Nutzung und Leistung des integrierten Shader](https://docs.unity3d.com/Manual/shader-Performance.html) detailliertere Informationen.

#### <a name="shader-preloading"></a>Vorabladen von Shader

Verwendung *Shader Vorabladen* und andere Tricks zur Optimierung [Shader Ladezeit](http://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html). Das bedeutet insbesondere, Shader Vorabladen, dass Sie nicht sehen, dass Probleme aufgrund von Shader-Runtime-Kompilierung.

### <a name="limit-overdraw"></a>Limit-Elements zu überzeichnen

In Unity, kann eine anzeigen-Elements zu überzeichnen für ihre Szene durch Umschalten der [ **zeichnen Modus im Menü** ](https://docs.unity3d.com/Manual/ViewModes.html) in der oberen linken Ecke des der **Szenenansicht** , und wählen **Alphablendings** .

Im Allgemeinen-Elements zu überzeichnen umgehen, indem die Auslese Objekte voraus, bevor sie an die GPU gesendet werden. Unity bietet Details zur Implementierung von [verschiedenen Culling](https://docs.unity3d.com/Manual/OcclusionCulling.html) für ihre-Engine.

## <a name="memory-recommendations"></a>Speicherempfehlungen

Eine übermäßige Speicheroperationen Zuordnung und Aufhebung der Zuordnung haben nachteilige Auswirkungen auf Ihre holographic Anwendung, was zu inkonsistenten Leistung, fixierte Frames und anderes Verhalten gleichzeitiger Aufrufe nachteilig auswirken. Es ist besonders wichtig, Überlegungen zum Arbeitsspeicher zu, bei der Entwicklung in Unity, da die Verwaltung des Arbeitsspeichers durch den Garbage Collector gesteuert wird.

#### <a name="garbage-collection"></a>Die automatische speicherbereinigung

Holographic apps werden Compute-Verarbeitungszeit der Garbage Collector (GC) verlieren, wenn der Garbage Collector aktiviert wird, um Objekte analysieren, die während der Ausführung nicht mehr im Gültigkeitsbereich befinden und deren Speicher muss freigegeben werden, damit es für die erneute Verwendung zur Verfügung gestellt werden kann. Zuordnungen von Konstanten und Aufhebung von Zuordnungen benötigen daher beeinträchtigt die Leistung und benutzerfreundlichkeit eine häufigere Ausführung der Garbage Collector in der Regel.

Unity stellt eine ausgezeichnete Seite, die im Detail erläutert die Funktionsweise von der Garbage Collector und Tipps, effizienter Code im Hinblick auf die Verwaltung des Arbeitsspeichers zu schreiben.
- [Optimieren der Garbagecollection im Unity-Spiele](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

Eines der am häufigsten verwendeten Praktiken, die auf eine übermäßige Garbagecollection führt das Verweise auf Komponenten und Klassen in der Unity-Entwicklung ist nicht zwischenspeichern. Alle Verweise während Start() oder Awake() aufgezeichnet, und in späteren Funktionen z. B. Update() oder LateUpdate() erneut verwendet werden soll.

Weitere Tipps:
- Verwenden der ["StringBuilder"](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# Klasse, um komplexe Zeichenfolgen zur Laufzeit dynamisch erstellen
- Entfernen Sie Aufrufe von Debug.Log() wird nicht mehr benötigt wird, während der Ausführung immer noch in der alle Build-Versionen einer App
- Wenn Ihre holographic app in der Regel viel Arbeitsspeicher benötigt, sollten Sie aufrufen [ _**System.GC.Collect()**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) während der Ladephase wie z. B. bei einem laden oder Transition-Bildschirm

#### <a name="object-pooling"></a>Objektpooling

Objektpooling ist ein beliebtes Verfahren, um die Kosten continuous speicherbelegungen und Aufhebungen von Objekten zu reduzieren. Dies erfolgt, indem Sie eine große Gruppe von identischen Objekte zuordnen und neu inaktive, verfügbare Instanzen aus diesem Pool anstatt ständig erstellen und Zerstören von Objekten im Laufe der Zeit. Objektpools eignen sich hervorragend für aktionsentwicklung Komponenten, die die Lebensdauer der Variablen während einer app haben.

- [Objektpooling-Lernprogramm in Unity](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>Startleistung

Berücksichtigen Sie Starten Ihrer app mit einer kleineren Szene, und klicken Sie dann mithilfe von *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* um den Rest der Szene zu laden. Dies ermöglicht Ihrer app, um einen interaktiven Zustands so schnell wie möglich zu erhalten. Beachten Sie, die es einer großen CPU-Spitze möglicherweise während die neue Szene aktiviert wird und alle gerenderten Inhalt ruckartig wiedergegeben werden kann oder Haken sein. Eine Möglichkeit zur Umgehung dieses Problems ist die AsyncOperation.allowSceneActivation-Eigenschaft auf "false" festlegen, in dem Bereich, der geladen wird, warten Sie, bis die Szene laden, deaktivieren Sie den Bildschirm auf Schwarz festgelegt, und legen Sie dann auf "true", zum Abschließen der Aktivierung der Szene zurück.

Denken Sie daran, dass beim Laden der startszene beim der holographic Splash-Bildschirm für den Benutzer angezeigt wird.

## <a name="see-also"></a>Siehe auch
- [Optimieren der Grafik-Rendering in Unity-Spiele](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [Optimieren der Garbagecollection im Unity-Spiele](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- [Physik bewährte Methoden [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)
- [Optimieren von Skripts [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)
