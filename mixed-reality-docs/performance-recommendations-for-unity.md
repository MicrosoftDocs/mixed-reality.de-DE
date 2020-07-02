---
title: Leistungsempfehlungen für Unity
description: Unity-spezifische Tipps zum Verbessern der Leistung bei Mixed Reality-Apps.
author: troy-ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: Grafik, CPU, GPU, Rendering, Garbage Collection, Hololens
ms.localizationpriority: high
ms.openlocfilehash: c6c68a6dd6e8ba59bee983e158e210aed27d2b17
ms.sourcegitcommit: 4282d92e93869e4829338bdf7d981c3ee0260bfd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85216241"
---
# <a name="performance-recommendations-for-unity"></a>Leistungsempfehlungen für Unity

Dieser Artikel baut auf der Diskussion auf, die in [Leistungsempfehlungen für Mixed Reality](understanding-performance-for-mixed-reality.md) beschrieben wird, legt den Schwerpunkt aber auf die für die Umgebung der Unity-Engine spezifischen Erkenntnisse.

## <a name="use-recommended-unity-project-settings"></a>Verwenden der empfohlenen Unity-Projekteinstellungen

Der wichtigste erste Schritt beim Optimieren der Leistung von Mixed Reality-Apps in Unity besteht darin, sicherzustellen, dass Sie die [empfohlenen Umgebungseinstellungen für Unity](recommended-settings-for-unity.md) verwenden. Der betreffende Artikel enthält Inhalte mit einigen der wichtigsten Szenenkonfigurationen zum Entwickeln leistungsfähiger Mixed Reality-Apps. Einige dieser empfohlenen Einstellungen werden unten ebenfalls hervorgehoben.

## <a name="how-to-profile-with-unity"></a>So erstellen Sie ein Profil mit Unity

Unity bietet den integrierten **[Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html)** , der eine hervorragende Ressource zum Sammeln wertvoller Einblicke zur Leistung für Ihre bestimmte App darstellt. Der Profiler kann zwar im Editor ausgeführt werden, diese Metriken stellen aber nicht die reale Laufzeitumgebung dar, daher sollten Ergebnisse aus diesen Profilerläufen umsichtig angewendet werden. Um besonders genaue und verwertbare Ergebnisse zu erhalten, empfiehlt es sich, das Profil Ihrer Anwendung remote während der Ausführung auf einem Gerät zu bestimmen. Darüber hinaus stellt der [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html) von Unity ebenfalls ein sehr leistungsstarkes Tool dar, mit dem sich Erkenntnisse gewinnen lassen.

Unity bietet eine hervorragende Dokumentation zu diesen Punkten:
1) Herstellen einer [Remoteverbindung zwischen dem Unity-Profiler und UWP-Anwendungen](https://docs.unity3d.com/Manual/windowsstore-profiler.html)
2) Effektive [Diagnose von Leistungsproblemen mit dem Unity Profiler](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)

>[!NOTE]
> Bei verbundenem Unity Profiler und nach dem Hinzufügen des GPU-Profilers (siehe dazu *Add Profiler* („Profiler hinzufügen“) in der oberen rechten Ecke) lässt sich in der Mitte des Profilers ablesen, wie viel Zeit für CPU bzw. GPU aufgewendet wird. Dadurch kann der Entwickler näherungsweise einschätzen, ob seine Anwendung CPU- oder GPU-lastig ist.
>
> ![Unity-CPU im Vergleich zu -GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>CPU-Leistungsempfehlungen

Die Inhalte unten befassen sich mit tiefgreifenden Praktiken zur Leistungsverbesserung, insbesondere für die Entwicklung mit Unity und C# bestimmt.

#### <a name="cache-references"></a>Zwischenspeichern von Verweisen

Es ist eine bewährte Methode, Verweise auf alle relevanten Komponenten und Spielobjekte bei der Initialisierung zwischenzuspeichern. Die hat den Grund, dass wiederholte Funktionsaufrufe wie etwa *[GetComponent\<T>()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* hinsichtlich des Arbeitsspeicherbedarfs erheblich teurer als das Speichern eines Zeigers sind. Dies gilt auch für das sehr gerne verwendete [Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html). *Camera.main* basiert auf der zugrundeliegenden Funktion *[FindGameObjectsWithTag()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* , die aufwändig Ihre Szenendarstellung nach einem Kameraobjekt mit dem Tag *„MainCamera“* absucht.

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
> Vermeiden von GetComponent(string) <br/>
> Beim Verwenden von *[GetComponent()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* haben Sie es mit einer handvoll verschiedener Überladungen zu tun. Es ist wichtig, immer die typbasierten Implementierungen und nie die zeichenfolgenbasierte Suchüberladung zu verwenden. Die Suche nach der Zeichenfolge in Ihrer Szene ist erheblich teurer als die Suche nach dem Typ. <br/>
> (Gut) Component GetComponent(Typ Typ) <br/>
> (Gut) T GetComponent\<T>() <br/>
> (Schlecht) Component GetComponent(string)> <br/>

#### <a name="avoid-expensive-operations"></a>Vermeiden aufwändiger Vorgänge

1) **Vermeiden Sie die Verwendung von [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**

    Zwar kann LINQ sehr sauber, leicht zu lesen und zu schreiben sein, es erfordert aber allgemein sehr viel mehr Rechenleistung und insbesondere mehr Arbeitsspeicherressourcen als das manuelle Ausschreiben der Algorithmen.

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

    Bestimmte Unity-APIs können zwar nützlich sein, sind in der Ausführung aber sehr kostspielig. Die meisten davon beinhalten das Durchsuchen Ihres gesamten Szenendarstellung nach einer Liste passender Spielobjekte. Diese Vorgänge können im Allgemeinen durch das Zwischenspeichern von Verweisen oder das Implementieren einer Manager-Komponente für die betreffenden GameObjects vermieden werden, um die Verweise zur Laufzeit zu verfolgen.

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> *[SendMessage()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* und *[BroadcastMessage()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* sollten unter allen Umständen entfernt werden. Diese Funktionen können der Größenordnung nach 1000mal langsamer als direkte Funktionsaufrufe sein.

3) **Vermeiden von Boxing**

    [Boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) ist ein Grundkonzept der C#- Sprache und ihrer Runtime. Dabei handelt es sich um den Prozess, Variablen eines Werttyps, wie etwa char, int, bool usw. mit Variablen vom Verweistyp zu umschließen. Wenn eine Variable eines Werttyps „geboxt“ ist, ist sie von einem System.Object umschlossen, das auf dem verwalteten Heap gespeichert wird. Auf diese Weise wird Speicher zugewiesen, der gegebenenfalls beim Verwerfen vom Garbage Collector verarbeitet werden muss. Diese Zuweisungen und ihre Aufhebung bringen Leistungskosten mit sich und sind in vielen Szenarien unnötig oder können leicht durch preiswertere Alternativen ersetzt werden.

    Eine der häufigsten Formen von Boxing in der Entwicklung ist die Verwendung von [Nullwerte zulassenden Typen](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/). Der Wunsch nach der Möglichkeit, null für einen Werttyp in einer Funktion zurückgeben zu können, ist gängig, insbesondere, wenn der Vorgang beim Versuch fehlschlagen kann, den Wert abzurufen. Das potenzielle Problem bei diesem Ansatz besteht darin, dass die Zuweisung jetzt auf dem Heap erfolgt und daher zu einem späteren Zeitpunkt Garbage Collection erforderlich macht.

    **Beispiel für Boxing in C#**

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

    **Beispiel für problematisches Boxing in Form von Typen, die Null-Werte zulassen**

    Dieser Code veranschaulicht eine Partikel-Dummyklasse, die sich in einem Unity-Projekt erstellen lässt. Ein Aufruf von `TryGetSpeed()` bewirkt eine Objektzuordnung auf dem Heap, die zu einem späteren Zeitpunkt Garbage Collection erforderlich macht. Dieses Beispiel ist besonders problematisch, da es leicht 1.000 oder noch weit mehr Partikel in einer Szene geben kann, von denen jedes nach seiner aktuellen Geschwindigkeit gefragt wird. Auf diese Weise würden in jedem Frame 1000e Objekte zugewiesen und deren Zuweisung entsprechend wieder aufgehoben, was die Leistung stark herabsetzen würde. Ein Umschreiben der Funktion, sodass sie einen negativen Wert wie etwa -1 zurückgibt, um einen Fehler anzuzeigen, hätte das Problem vermieden und Arbeitsspeicher auf dem Stack gehalten.

    ```csharp
        public class MyParticle
        {
            // Example of function returning nullable value type
            public int? TryGetSpeed()
            {
                // Returns current speed int value or null if fails
            }
        }
    ```

#### <a name="repeating-code-paths"></a>Wiederholte Codepfade

Alle wiederholten Unity-Rückruf-Funktionen (d. h. Update), die mehrmals pro Sekunde und/oder Frame ausgeführt werden, sollten mit großer Sorgfalt geschrieben werden. Alle aufwändigen Vorgänge an dieser Stelle haben einen sehr großen und konsistenten Einfluss auf die Leistung.

1) **Leere Rückruffunktion**

    Zwar mag der Code unten harmlos aussehen, und Sie neigen wohl dazu, ihn in Ihrer Anwendung zu belassen, vor allem, da sich jedes Unity-Skript automatisch mit diesem Codeblock initialisiert, diese leeren Rückrufe können aber tatsächlich sehr teuer werden. Unity überquert bei der Arbeit ständig in beiden Richtungen eine Grenze zwischen verwaltetem und nicht verwaltetem Code, nämlich zwischen dem Code der UnityEngine und Ihrem Anwendungscode. Der Kontextwechsel beim Überqueren dieser Grenze ist ziemlich teuer, auch dann, wenn es gar nichts auszuführen gibt. Dies wird besonders dann problematisch, wenn Ihre App über 100e von Spielobjekten verfügt, die ihrerseits wiederholte leere Unity-Rückrufe verwenden.

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> Update () ist die gängigste Form dieses Leistungsproblems, aber andere sich wiederholende Unity-Rückrufe, wie z. B. die folgenden, können genauso schlecht sein, wenn nicht gar schlechter: FixedUpdate(), LateUpdate(), OnPostRender", OnPreRender(), OnRenderImage() usw. 

2) **Vorgänge, die vorzugsweise einmal pro Frame ausgeführt werden sollten**

    Die folgenden Unity-APIs stellen gängige Vorgänge für viele Holografie-Apps dar. Es ist zwar nicht immer möglich, aber sehr oft können die Ergebnisse dieser Funktionen einmal berechnet und dann für einen bestimmten Frame im gesamten Bereich der Anwendung wiederverwendet werden.

    a) Im Allgemeinen ist es eine gute Praxis, eine dedizierte Singleton-Klasse oder einen Dienst einzusetzen, die bzw. der Ihren Raycast vom Anvisieren der Szene verarbeitet und dieses Ergebnis dann in allen anderen Szenekomponenten wiederzuverwenden, statt wiederholte und im Wesentlichen identische Raycastvorgänge für jede Komponente auszulösen. Natürlich sind in manchen Anwendungen möglicherweise Raycasts aus einem anderen Ursprung oder gegen andere [LayerMasks](https://docs.unity3d.com/ScriptReference/LayerMask.html) (Ebenenmasken) erforderlich.

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    b) Vermeiden Sie GetComponent()-Vorgänge in wiederholten Unity-Rückrufen wie Update(), indem Sie [Verweise zwischenspeichern](#cache-references): in Start() oder Awake()

        UnityEngine.Object.GetComponent()

    c) Es ist eine bewährte Methode, nach Möglichkeit alle Objekte bei der Initialisierung zu instanziieren und [Objektpooling](#object-pooling) zu verwenden, um die gesamte Laufzeit Ihrer Anwendung hindurch Spielobjekte zu recyceln und wiederzuverwenden

        UnityEngine.Object.Instantiate()

3) **Vermeiden von Schnittstellen und virtuellen Konstrukten**

    Das Aufrufen von Funktionsaufrufen über Schnittstellen im Gegensatz zu direkten Objekten oder dem Aufrufen von virtuellen Funktionen ist oftmals sehr viel kostspieliger als die Verwendung direkter Konstrukte oder direkter Funktionsaufrufe. Wenn die virtuelle Funktion oder Schnittstelle nicht benötigt wird, sollte sie entfernt werden. Der Leistungspreis für diese Ansätze spricht aber in der Regel für den Kompromiss, wenn ihre Verwendung die Zusammenarbeit bei der Entwicklung vereinfacht, die Lesebarkeit und die Wartbarkeit des Codes verbessert.

    Im Allgemeinen wird empfohlen, Felder und Funktionen nicht als virtuell zu markieren, es sei denn, es gibt eine klare Annahme, dass das betreffende Element überschrieben werden muss. Insbesondere im Umfeld stark frequentierter Codepfade, die mehrmals pro Frame oder auch nur einmal pro Frame aufgerufen werden, wie etwa eine `UpdateUI()`-Methode, sollten Sie vorsichtig sein.

4) **Vermeiden der Übergabe von Strukturen über den Wert**

    Im Gegensatz zu Klassen sind Strukturen Werttypen, und bei der direkten Übergabe an eine Funktion werden ihre Inhalte in eine neu erstellte Instanz kopiert. Diese Kopie bewirkt höhere CPU-Kosten sowie zusätzlichen Speicherbedarf auf dem Stack. Für kleine Strukturen ist der Effekt normalerweise minimal und daher akzeptabel. Bei Funktionen, die in jedem Frame wiederholt aufgerufen werden, sowie bei Funktionen, die große Strukturen akzeptieren, ändern Sie nach Möglichkeit die Funktionsdefinition, um durch Verweis zu übergeben. [Weitere Informationen finden Sie hier](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a>Verschiedenes

1) **Physische Effekte**

    a) Im Allgemeinen ist die einfachste Möglichkeit, die physischen Effekte zu verbessern, die Menge an Zeit oder die Anzahl der Iterationen pro Sekunde einzuschränken, die zu ihrer Berechnung aufgewendet wird. Dadurch wird natürlich die Genauigkeit der Simulation reduziert. Mehr dazu finden Sie unter [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) in Unity

    b) Die verschiedenen Collidertypen in Unity weisen stark unterschiedliche Leistungsmerkmale auf. Der Auftrag unten listet Collider nach ihrer Leistungsfähigkeit auf, von den leistungsfähigsten links bis zu den am wenigsten leistungsfähigen Collidern rechts. Es ist sehr wichtig, Gittermodell-Collider zu meiden, die erheblich teurer sind als die primitiven Collider.

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    Weitere Informationen finden Sie unter [Unity Physics Best Practices](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) (Bewährte Methoden für physische Effekte in Unity).

2) **Animationen**

    Deaktivieren Sie Leerlaufanimationen, indem Sie die Animatorkomponente deaktivieren (das Deaktivieren des Spielobjekts hat nicht die gleiche Wirkung). Vermeiden Sie Entwurfsmuster, bei denen ein Animator in einer Schleife sitzt und einen Wert ständig erneut festlegt. Diese Technik verursacht beträchtlichen Mehraufwand ohne positiven Effekt auf die Anwendung. [Weitere Informationen finden Sie hier.](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **Komplexe Algorithmen**

    Wenn Ihre Anwendung komplexe Algorithmen verwendet, wie z. B. inverse Kinematik, Pfadsuche usw., suchen Sie nach einem einfacheren Ansatz, oder passen Sie relevante Einstellungen leistungsbezogen an.

## <a name="cpu-to-gpu-performance-recommendations"></a>CPU- im Vergleich mit GPU-Leistungsempfehlungen

Im Allgemeinen lässt sich das Leistungsverhältnis zwischen CPU und GPU auf die **Zeichenaufrufe** reduzieren, die an die Grafikkarte übermittelt werden. Um die Leistung zu verbessern, müssen Zeichenaufrufe strategisch **a) verringert** oder **b) neu strukturiert** werden, um optimale Ergebnisse zu erzielen. Da Zeichenaufrufe ihrerseits ressourcenintensiv sind, bewirkt ihre Verringerung auch eine Verringerung der insgesamt aufzuwendenden Arbeit. Ferner werden durch Statuswechsel zwischen Zeichenaufrufen aufwändige Schritte zur Validierung und Übersetzung im Grafiktreiber erforderlich, daher kann eine Neustrukturierung der Zeichenaufrufe Ihrer Anwendung mit dem Ziel, die Statuswechsel (d. h. verschiedene Materialien usw.) zu verringern, die Leistung steigern.

Unity bietet einen hervorragenden Artikel, der einen Überblick hierzu gibt und tief in die Batchverarbeitung von Zeichenaufrufen für die Unity-Plattform einsteigt.
- [Batchverarbeitung von Unity-Zeichenaufrufen](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a>Single-Pass-Instanzrendering

Single-Pass-Instanzrendering in Unity ermöglicht es, die Zeichenaufrufe für jedes Auge auf einen instanziierten Zeichenaufruf zu reduzieren. Aufgrund der Cachekohärenz zwischen zwei Zeichenaufrufen kommt es hier auch zu einer gewissen Leistungsverbesserung bei der GPU.

Aktivieren dieser Funktion in Ihrem Unity-Projekt
1)  Öffnen Sie die **Player XR Settings** (Player XR-Einstellungen) (navigieren Sie zu **Edit** > **Project Settings** > **Player** > **XR Settings** („Bearbeiten > Projekteinstellungen > Player > XR-Einstellungen))
2) Wählen Sie im Dropdownmenü **Stereo Rendering Method** (Stereo-Renderingmethode) **Single Pass Instanced** (Single-Pass-Instanz) aus (das Kontrollkästchen **Virtual Reality Supported** (Virtuelle Realität unterstützt) muss aktiviert sein)

Details zu diesem Renderingansatz finden Sie in den folgenden Artikeln von Unity.
- [How to maximize AR and VR performance with advanced stereo rendering](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/) (Maximieren der AR- und VR-Leistung mit erweitertem Stereorendering)
- [Single Pass Instancing](https://docs.unity3d.com/Manual/SinglePassInstancing.html) (Single-Pass-Instanziierung) 

>[!NOTE]
> Ein häufiges Problem beim Single-Pass-Instanzrendering tritt auf, wenn Entwickler bereits vorhandene benutzerdefinierte Shader einsetzen, die noch nicht für die Instanziierung geschrieben wurden. Nach dem Aktivieren dieses Features stellen die Entwickler möglicherweise fest, dass manche Spielobjekte nur für ein Auge gerendert werden. Dies hat den Grund, dass die zugeordneten benutzerdefinierten Shader nicht die geeigneten Eigenschaften für die Instanziierung aufweisen.
>
> Informationen zum Beheben dieses Problems finden Sie unter [Single Pass Stereo Rendering for HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) (Single-Pass-Stereorendering für HoloLens) von Unity

#### <a name="static-batching"></a>Statische Batchverarbeitung

Unity kann viele statische Objekte als Batch verarbeiten, um die Zeichenaufrufe an die GPU zu verringern. Die statische Batchverarbeitung funktioniert für die meisten [Rendererobjekte](https://docs.unity3d.com/ScriptReference/Renderer.html) in Unity, die **1) das Material gemeinsam haben** und **2) alle als *Static*** gekennzeichnet sind (Wählen Sie ein Objekt in Unity aus, und klicken Sie auf das Kontrollkästchen in der oberen rechten Ecke des Inspektors). GameObjects, die als *Static* gekennzeichnet sind, können nicht durch die Runtime Ihrer Anwendung bewegt werden. Daher kann es schwierig sein, statische Batchverarbeitung für HoloLens zu nutzen, bei der praktisch jedes Objekt platziert, bewegt, skaliert usw. werden muss. Bei immersiven Headsets kann statische Batchverarbeitung die Anzahl der Zeichenaufrufe drastisch reduzieren und die Leistung so verbessern.

Weitere Details erfahren Sie unter *Static Batching* (Statische Batchverarbeitung) unter [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) (Batchverarbeitung von Zeichenaufrufen in Unity).

#### <a name="dynamic-batching"></a>Dynamische Batchverarbeitung

Da es in der HoloLens-Entwicklung problematisch ist, Objekte als *Static* zu kennzeichnen, kann dynamische Batchverarbeitung ein hervorragendes Mittel darstellen, das Fehlen dieser Funktion zu kompensieren. Natürlich kann es auch bei immersiven Headsets nützlich sein. Die dynamische Batchverarbeitung in Unity kann aber schwierig zu aktivieren sein, da die GameObjects **a) das gleiche Material verwenden** und **b) eine lange Liste weiterer Kriterien erfüllen** müssen.

Die vollständige Liste finden Sie unter *Dynamic Batching* (Dynamische Batchverarbeitung) unter [Draw Call Batching in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) (Batchverarbeitung von Zeichenaufrufen in Unity). In den meisten Fällen wird die dynamische Batchverarbeitung von GameObjects ungültig, da die zugeordneten Gittermodelldaten nicht mehr als 300 Scheitelpunkte umfassen dürfen.

#### <a name="other-techniques"></a>Andere Verfahren

Batchverarbeitung kann nur erfolgen, wenn mehrere GameObjects gemeinsam dasselbe Material verwenden können. Normalerweise steht dem das Erfordernis gegenüber, dass GameObjects eine eindeutige Textur für ihr jeweiliges Material besitzen müssen. Es ist üblich, Texturen in einer großen Textur zusammenzufassen, eine Methode, die als [Texture Atlasing](https://en.wikipedia.org/wiki/Texture_atlas) bezeichnet wird.

Darüber hinaus ist es im allgemeinen vorzuziehen, Gittermodelle zu einem GameObject zu kombinieren, wo es möglich und vernünftig ist. Für jeden Renderer in Unity ist eine bestimmte Anzahl Zeichenaufrufe im Vergleich mit dem Übermitteln eines kombinierten Gittermodells unter einem Renderer typisch.

>[!NOTE]
> Beim Ändern von Eigenschaften von „Renderer.material“ zur Laufzeit wird eine Kopie des Materials erstellt, was die Batchverarbeitung möglicherweise unmöglich macht. Verwenden Sie Renderer.sharedMaterial, um die mehreren GameObjects gemeinsamen Materialeigenschaften zu ändern.

## <a name="gpu-performance-recommendations"></a>GPU-Leistungsempfehlungen

Weitere Informationen zum [Optimieren des Grafikrenderings in Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)

### <a name="optimize-depth-buffer-sharing"></a>Optimieren der gemeinsamen Nutzung des Tiefenpuffers

Im Allgemeinen wird empfohlen, in den **Player XR-Einstellungen** die **Gemeinsame Nutzung des Tiefenpuffers** zu aktivieren, um die [Hologrammstabilität](Hologram-stability.md) zu optimieren. Wenn die tiefenbasierte Neuprojektion in der Spätphase mit dieser Einstellung aktiviert wird, wird die Wahl des **16-Bit-Tiefenformats** anstelle des **24-Bit-Tiefenformats** empfohlen. Die 16-Bit-Tiefenpuffer reduzieren die Bandbreite (und somit die erforderliche Leistung), die mit dem Tiefenpuffer-Datenverkehr einhergeht, drastisch. Dies kann sowohl für den Stromverbrauch als auch für die Leistungsverbesserung ein großer Gewinn sein. Allerdings gibt es zwei mögliche negative Ergebnisse durch Einsatz des *16-Bit-Tiefenformats*.

**Z-Fighting**

Die verringerte Genauigkeit des Tiefenbereichs erhöht die Wahrscheinlichkeit von [Z-Fighting](https://en.wikipedia.org/wiki/Z-fighting) bei 16-Bit im Vergleich mit 24-Bit. Um diese Artefakte zu vermeiden, ändern Sie die Clippingebenen der [Unity-Kamera](https://docs.unity3d.com/Manual/class-Camera.html) für nah und fern, um der geringeren Genauigkeit Rechnung zu tragen. In HoloLens-basierten Anwendungen kann eine Clippingebene von 50 m anstelle des Unity-Standardwerts von 1000 m im Allgemeinen jegliches Z-Fighting beseitigen.

**Deaktivierter Schablonenpuffer**

Wenn Unity eine [Rendertextur mit 16-Bit Tiefe](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) erstellt, wird kein Schablonenpuffer erstellt. Beim Auswählen eines Formats mit 24-Bit Tiefe wird gemäß der Unity-Dokumentation ein 24-Bit-Z-Puffer erstellt sowie ein [8-Bit-Schablonenpuffer] (https://docs.unity3d.com/Manual/SL-Stencil.html) (wenn 32-Bit auf einem Gerät möglich sind, was aber allgemein der Fall ist, etwa bei HoloLens).

### <a name="avoid-full-screen-effects"></a>Vermeiden von Vollbildeffekten

Techniken, die im Vollbildmodus arbeiten, können ziemlich teuer sein, da sie die Größenordnung von Millionen von Vorgängen pro Frame erreichen. Daher wird empfohlen, [Effekte der Nachbearbeitung](https://docs.unity3d.com/Manual/PostProcessingOverview.html) wie Antialiasing, Blooming und mehr zu vermeiden.

### <a name="optimal-lighting-settings"></a>Optimale Beleuchtungseinstellungen

Die [globale Beleuchtung in Echtzeit](https://docs.unity3d.com/Manual/GIIntro.html) in Unity kann herausragende visuelle Ergebnisse produzieren, bringt jedoch ziemlich umfangreiche Beleuchtungsberechnungen mit sich. Es wird empfohlen, die globale Beleuchtung in Echtzeit für jede Unity-Szenendatei mit dieser Einstellung zu deaktivieren: **Window** > **Rendering** > **Lighting Settings** > Uncheck **Real-time Global Illumination** (Fenster > Rendering > Beleuchtungseinstellungen > Globale Beleuchtung in Echtzeit deaktivieren).

Ferner wird empfohlen, jede Art von Schattenwurf zu deaktivieren, da dieser ebenfalls teure GPU-Durchgänge für eine Unity-Szene mit sich bringt. Schatten können durch Licht deaktiviert werden, lassen sich über die Qualitätseinstellungen aber auch im Ganzen steuern.

**Edit** > **Project Settings** (Bearbeiten > Projekteinstellungen), wählen Sie dann die Kategorie **Quality** (Qualität) aus > wählen Sie **Low Quality** (Niedrige Qualität) für die UWP-Plattform. Sie können auch einfach die **Shadows**-Eigenschaft (Schatten) auf **Disable Shadows** (Schatten deaktivieren) festlegen.

Es empfiehlt sich, für Ihre Modelle in Unity „Baked Lighting“ (vorab gerenderte Lichtdetails) zu verwenden.

### <a name="reduce-poly-count"></a>Reduzieren der Polygonanzahl

Das Reduzieren der Polygonanzahl wird normalerweise durch eins dieser Verfahren erreicht
1) Entfernen von Objekten aus einer Szene
2) Starke Herabsetzung der Medienobjekte, wodurch sich die Anzahl der Polygone für ein bestimmtes Gittermodell reduziert
3) Implementieren eines [Level of Detail (LOD) System](https://docs.unity3d.com/Manual/LevelOfDetail.html) (Detailstufensystems) in Ihrer Anwendung, bei der weit entfernte Objekte mit einer aus weniger Polygonen bestehenden Version der gleichen Geometrie gerendert werden

### <a name="understanding-shaders-in-unity"></a>Grundlegendes zu Shadern in Unity

Eine einfache Annäherung für den Leistungsvergleich von Shadern besteht darin, die durchschnittliche Anzahl der Vorgänge zu bestimmen, die jeder zur Laufzeit ausführt. Dies kann in Unity sehr einfach erfolgen.

1) Wählen Sie Ihr Shadermedienobjekt oder ein Material aus, und wählen Sie dann in der oberen rechten Ecke des Inspektorfensters das Zahnradsymbol aus, gefolgt von **„Select Shader“** (Shader auswählen)

    ![Auswählen eines Shaders in Unity](images/Select-shader-unity.png)
2) Klicken Sie bei ausgewähltem Shadermedienobjekt auf die Schaltfläche **„Compile and show code“** (Compilieren und Code anzeigen) unter dem Inspektorfenster

    ![Kompilieren von Shadercode in Unity](images/compile-shader-code-unity.PNG)

3) Suchen Sie nach dem Compilieren nach dem Statistikabschnitt in den Ergebnissen mit der Anzahl der verschiedenen Vorgänge sowohl für den Vertex- als auch für den Pixelshader (Hinweis: Pixelshader werden auch häufig als Fragmentshader bezeichnet)

    ![Standardshadervorgänge in Unity](images/unity-standard-shader-compilation.png)

#### <a name="optimize-pixel-shaders"></a>Optimieren von Pixelshadern

Beim Blick auf die compilierten Statistikergebnisse unter Verwendung der Methode oben zeigt sich, dass der [Fragmentshader](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) im Mittel mehr Vorgänge als der [Vertexshader](https://en.wikipedia.org/wiki/Shader#Vertex_shaders) ausführt. Der Fragmentshader, auch als Pixelshader bezeichnet, wird pro Pixel der Bildschirmausgabe ausgeführt, während der Vertexshader nur pro Scheitelpunkt aller Gittermodelle ausgeführt wird, die auf dem Bildschirm gezeichnet werden. 

Daher weisen Fragmentshader aufgrund der vielen Beleuchtungsberechnungen nicht nur mehr Anweisungen auf, sie werden auch fast immer auf einem größeren Dataset ausgeführt. Wenn die Bildschirmausgabe beispielsweise ein Bild mit 2.000 mal 2.000 Pixeln ist, kann der Fragmentshader 2.000*2.000 = 4.000.000 Mal ausgeführt werden. Wenn zwei Augen gerendert werden, verdoppelt sich diese Zahl, da zwei Bildschirme vorhanden sind. Wenn eine Mixed Reality-Anwendung mehrere Durchgänge, Nachbearbeitungseffekte im Vollbildmodus und/oder Rendering mehrerer Gittermodelle für das gleiche Pixel aufweist, erhöht sich diese Zahl dramatisch. 

Daher können mit dem Verringern der Zahl der Vorgänge im Fragmentshader im Allgemeinen viel größere Leistungssteigerungen als durch Optimierungen im Vertexshader erreicht werden.

#### <a name="unity-standard-shader-alternatives"></a>Alternativen zu den Unity-Standardshadern

Anstatt ein physikalisch basiertes Rendering (PBR) oder einen anderen hochwertigen Shader zu verwenden, sollten Sie einen leistungsfähigeren und kostengünstigeren Shader nutzen. Im [Mixed Reality-Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) steht der [MRTK-Standardshader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) bereit, der für Mixed Reality-Projekte optimiert wurde.

Unity bietet darüber hinaus unlit (nicht beleuchtet), vertex lit (nach Scheitelpunkten beleuchtet), diffuse (diffus), und weitere vereinfachte Shaderoptionen, die im Vergleich erheblich schneller arbeiten als der Unity-Standardshader. Detailliertere Informationen finden Sie unter [Usage and Performance of Built-in Shaders](https://docs.unity3d.com/Manual/shader-Performance.html) (Verwendung und Leistung der integrierten Shader).

#### <a name="shader-preloading"></a>Vorabladen der Shader

Verwenden Sie *Vorabladen der Shader* und andere Tricks, um die [Shaderladezeiten](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html) zu optimieren. Insbesondere bedeutet Vorabladen der Shader, dass kein Hängen aufgrund von Shadercompilierung zur Laufzeit sichtbar wird.

### <a name="limit-overdraw"></a>Einschränken des Überzeichnens

In Unity kann Überzeichnung für eine Szene angezeigt werden, indem ein Wert im [**Zeichenmodusmenü**](https://docs.unity3d.com/Manual/ViewModes.html) in der oberen linken Ecke der **Szenenansicht** auf **Overdraw** (Überzeichnung) umgeschaltet wird.

Im Allgemeinen kann Überzeichnung durch rechtzeitiges Culling (Entfernen der Rückseiten) von Objekten abgemildert werden, bevor sie an die GPU gesendet werden. Unity bietet ausführliche Informationen zum Implementieren von [Occlusion Culling](https://docs.unity3d.com/Manual/OcclusionCulling.html) (Verdeckungs-Culling) für ihre Engine.

## <a name="memory-recommendations"></a>Empfehlungen zum Arbeitsspeicher

Exzessive Zuweisungsvorgänge von Arbeitsspeicher und deren Aufhebung können in Ihrer Holografieanwendung negative Effekte zeigen, die zu inkonsistenter Leistung, eingefrorenen Frames und anderem abträglichem Verhalten führen. Das Verstehen der Arbeitsspeicheraspekte ist beim Entwickeln in Unity besonders wichtig, da die Arbeitsspeicherverwaltung vom Garbage Collector gesteuert wird.

#### <a name="garbage-collection"></a>Garbage Collection

Holografie-Apps verlieren Prozessorzeit an den Garbage Collector (GC), wenn der GC aktiviert wird, um Objekte zu analysieren, die sich während der Ausführung nicht mehr im Bereich befinden und deren Arbeitsspeicher freigegeben werden muss, damit er für die Wiederverwendung zur Verfügung steht. Ständiges Zuweisen und Freigeben macht häufigere Läufe des Garbage Collectors erforderlich, was Leistung und Benutzererfahrung beeinträchtigt.

Unity hat eine hervorragende Seite zur Verfügung gestellt, auf der die Arbeitsweise des Garbage Collectors detailliert beschrieben ist und Tipps zum Schreiben von – im Hinblick auf die Speicherverwaltung – effizienterem Code gegeben werden.
- [Optimieren der Garbage Collection in Unity-Spielen](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

Eine der gängigsten Methoden, die zu einer übermäßigen Garbage Collection führt, besteht darin, in der Unity-Entwicklung keine Verweise auf Komponenten und Klassen zwischenzuspeichern. Alle Verweise sollten während Start() oder Awake() erfasst und in späteren Funktionen wie Update() oder LateUpdate() wiederverwendet werden.

Weitere schnelle Tipps:
- Verwenden Sie die [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2)-Klasse von C#, um dynamisch zur Laufzeit komplexe Zeichenfolgen zu generieren
- Entfernen Sie Aufrufe von Debug.Log(), wenn sie nicht mehr erforderlich sind, da sie in allen Buildversionen einer App trotzdem noch ausgeführt werden
- Wenn Ihre Holografie-App allgemein viel Arbeitsspeicher erfordert, erwägen Sie das Aufrufen von [_**System.GC.Collect()**_](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2) in Ladephasen etwa beim Anzeigen eines Lade- oder Übergangsbildschirms

#### <a name="object-pooling"></a>Objektpooling

Objektpooling ist eine gängige Methode, um die Kosten für fortlaufende Zuordnungen von Objekten und deren Aufhebung zu reduzieren. Dies erfolgt durch Zuordnen eines großen Pools identischer Objekte und Wiederverwendung inaktiver, verfügbarer Instanzen aus diesem Pool, statt im Lauf der Zeit ständig neue Objekte zu erstellen und zu entfernen. Objektpools eignen sich hervorragend für wiederverwendbare Komponenten, die im Rahmen einer App eine variable Lebensdauer haben.

- [Tutorial zum Objektpooling in Unity](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>Startleistung

Sie sollten erwägen, Ihre App mit einer kleineren Szene zu starten und dann *[SceneManager.LoadSceneAsync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* zu verwenden, um den Rest der Szene zu laden. Dadurch kann Ihre App so schnell wie möglich in einen interaktiven Zustand gelangen. Beachten Sie, dass es beim Aktivieren der neuen Szene zu einer großen CPU-Spitze kommen kann, und dass alle gerenderten Inhalte möglicherweise stockend oder hängend ausgeführt werden. Eine Möglichkeit, dies zu umgehen, besteht darin, die AsyncOperation.allowSceneActivation-Eigenschaft für die zu ladende Szene auf „false“ festzulegen, das Laden der Szene abzuwarten, den Bildschirm auf schwarz zu setzen und den Wert der Eigenschaft dann wieder auf „true“ festzulegen, um die Szenenaktivierung abzuschließen.

Beachten Sie, dass während des Ladens der Startszene für den Benutzer der holografische Begrüßungsbildschirm angezeigt wird.

## <a name="see-also"></a>Siehe auch
- [Optimieren des Grafikrenderings in Unity-Spielen](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [Optimieren der Garbage Collection in Unity-Spielen](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- [Bewährte Methoden für die Physische Effekte [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)
- [Optimieren von Skripts [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)
