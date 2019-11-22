---
title: Empfehlungen zur Leistung für Unity
description: Unity-spezifische Tipps zum Verbessern der Leistung mit Mixed Reality-apps.
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: Grafiken, CPU, GPU, Rendering, Garbage Collection, hololens
ms.openlocfilehash: f3fdda94c417d9f8e8980a90e8928282789e3d0f
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926871"
---
# <a name="performance-recommendations-for-unity"></a>Empfehlungen zur Leistung für Unity

Dieser Artikel baut auf der Erörterung der [Leistungs Empfehlungen für gemischtes Reality](understanding-performance-for-mixed-reality.md) auf, konzentriert sich jedoch auf die für die Unity-Engine-Umgebung spezifischen Erkenntnisse.

Es ist außerdem sehr empfehlenswert, dass Entwickler die [empfohlenen Umgebungseinstellungen für den Unity-Artikel](Recommended-settings-for-unity.md)überprüfen. In diesem Artikel werden einige der wichtigsten Szenen Konfigurationen in Bezug auf das Entwickeln leistungsfähiger gemischter Reality-apps behandelt. Einige dieser empfohlenen Einstellungen sind auch unten hervorgehoben.

## <a name="how-to-profile-with-unity"></a>So erstellen Sie ein Profil mit Unity

Unity bietet den integrierten **[Unity-Profiler](https://docs.unity3d.com/Manual/Profiler.html)** , der eine gute Ressource ist, um wertvolle Einblicke in die Leistung Ihrer APP zu erfassen. Obwohl der Profiler im-Editor ausgeführt werden kann, stellen diese Metriken nicht die echte Laufzeitumgebung dar. Daher sollten die Ergebnisse aus diesem nicht vorsichtig verwendet werden. Es wird empfohlen, eine Remote Profilerstellung für Ihre Anwendung während der Ausführung auf dem Gerät durchführen, um präzisere und verwertbare Erkenntnisse Außerdem ist der [Frame Debugger](https://docs.unity3d.com/Manual/FrameDebugger.html) von Unity ein sehr leistungsfähiges Tool für die Verwendung.

Unity bietet eine gute Dokumentation für:
1) Herstellen einer Remote Verbindung zwischen dem [Unity-Profiler und UWP-Anwendungen](https://docs.unity3d.com/Manual/windowsstore-profiler.html)
2) Effektive [Diagnose von Leistungsproblemen mit dem Unity-Profiler](https://unity3d.com/learn/tutorials/temas/performance-optimization/diagnosing-performance-problems-using-profiler-window)

>[!NOTE]
> Beim Herstellen einer Verbindung mit dem Unity-Profiler und nach dem Hinzufügen des GPU-Profilers (siehe *Hinzufügen von Profiler* in der oberen rechten Ecke) können Sie sehen, wie viel Zeit für die CPU-& GPU in der Mitte des Profilers aufgewendet wird. Dies ermöglicht es dem Entwickler, eine kurze Näherung zu erhalten, wenn die Anwendung CPU-oder GPU-gebunden ist.
>
> ![Unity-CPU im Vergleich zu GPU](images/unity-profiler-cpu-gpu.png)

## <a name="cpu-performance-recommendations"></a>Empfehlungen zur CPU-Leistung

Der folgende Inhalt umfasst ausführlichere Leistungs Praktiken, insbesondere für die Entwicklung von Unity- C# &.

#### <a name="cache-references"></a>Cache Verweise

Es wird empfohlen, Verweise auf alle relevanten Komponenten und gameobjects bei der Initialisierung zwischenzuspeichern. Dies liegt daran, dass sich wiederholende Funktionsaufrufe, wie z. b. *[getComponent\<t > ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* , relativ zu den Arbeitsspeicher Kosten zum Speichern eines Zeigers deutlich teurer sind. Dies gilt auch für die sehr regelmäßig verwendete [Kamera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). " *Camera. Main* " verwendet tatsächlich " *[findgameobjectwithtag ()](https://docs.unity3d.com/ScriptReference/GameObject.FindGameObjectsWithTag.html)* ", unter dem Ihre Szenen Diagramme mit dem Tag *"maincamera"* nach einem Kamera Objekt durchsucht werden.

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
> "GetComponent" (Zeichenfolge) vermeiden <br/>
> Bei der Verwendung von *[getComponent ()](https://docs.unity3d.com/ScriptReference/GameObject.GetComponent.html)* gibt es eine Handvoll unterschiedlicher über Ladungen. Es ist wichtig, immer die typbasierten Implementierungen und nie die Zeichen folgen basierte Such Überladung zu verwenden. Das Suchen nach Zeichen folgen in Ihrer Szene ist deutlich teurer als die Suche nach Typ. <br/>
> Glück Komponente getComponent (Type-Typ) <br/>
> Glück T getComponent\<t > () <br/>
> Schlechtem Komponente getComponent (String) > <br/>

#### <a name="avoid-expensive-operations"></a>Vermeiden kostspieliger Vorgänge

1) **Vermeiden der Verwendung von [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/getting-started-with-linq)**

    Obwohl LINQ sehr sauber und leicht zu lesen und zu schreiben sein kann, erfordert es im allgemeinen weitaus mehr Berechnungen und besonders mehr Speicher Belegung, als den Algorithmus manuell zu schreiben.

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

    Bestimmte Unity-APIs, auch wenn Sie nützlich sind, können für die Ausführung sehr kostspielig sein. In den meisten Fällen ist das Durchsuchen des gesamten Szenen Diagramms nach einer passenden Liste von gameobjects verbunden. Diese Vorgänge können im Allgemeinen durch das Zwischenspeichern von verweisen oder das Implementieren einer Manager-Komponente für die betreffenden gameobjects vermieden werden, um die Verweise zur Laufzeit zu verfolgen.

        GameObject.SendMessage()
        GameObject.BroadcastMessage()
        UnityEngine.Object.Find()
        UnityEngine.Object.FindWithTag()
        UnityEngine.Object.FindObjectOfType()
        UnityEngine.Object.FindObjectsOfType()
        UnityEngine.Object.FindGameObjectsWithTag()
        UnityEngine.Object.FindGameObjectsWithTag()

>[!NOTE]
> *[SendMessage ()](https://docs.unity3d.com/ScriptReference/GameObject.SendMessage.html)* und *[broadcastmessage ()](https://docs.unity3d.com/ScriptReference/GameObject.BroadcastMessage.html)* sollten zu allen Kosten entfernt werden. Diese Funktionen können in der Reihenfolge von 1000 x langsamer als bei direkten Funktionsaufrufen vorliegen.

3) **Vor Boxing**

    [Boxing](https://docs.microsoft.com/dotnet/csharp/programming-guide/types/boxing-and-unboxing) ist ein Grundkonzept der C# Sprache und Laufzeit. Dabei handelt es sich um den Prozess, bei dem Werte typisierte Variablen wie char, int, bool usw. in Verweis typisierte Variablen umwickelt werden. Wenn eine Wert typisierte Variable "geschachtelt" ist, wird Sie in ein System. Object umgeschrieben, das auf dem verwalteten Heap gespeichert wird. Daher wird der Arbeitsspeicher zugeordnet, und schließlich muss der Speicherplatz verworfen werden, wenn er vom Garbage Collector verarbeitet wird. Diese Zuordnungen und Aufhebungen verursachen einen Leistungs Aufwand, und in vielen Szenarien sind Sie unnötig oder können einfach durch eine kostengünstigere Alternative ersetzt werden.

    Eine der gängigsten Formen des Boxens in der Entwicklung ist die Verwendung von [Werttypen](https://docs.microsoft.com//dotnet/csharp/programming-guide/nullable-types/), die NULL-Werte zulassen. Es ist üblich, dass Sie in der Lage sein möchten, NULL für einen Werttyp in einer Funktion zurückzugeben, insbesondere dann, wenn der Vorgang möglicherweise nicht versucht, den Wert zu erhalten. Das potenzielle Problem bei diesem Ansatz besteht darin, dass die Zuordnung jetzt auf dem Heap erfolgt und daher später eine Garbage Collection durchgeführt werden muss.

    **Beispiel für Boxing inC#**

    ```csharp
    // boolean value type is boxed into object boxedMyVar on the heap
    bool myVar = true;
    object boxedMyVar = myVar;
    ```

    **Beispiel für problematischen Boxing über Werttypen, die NULL-Werte zulassen**

    Dieser Code veranschaulicht eine Dummy-Partikel Klasse, die in einem Unity-Projekt erstellt werden kann. Ein Aufruf von `TryGetSpeed()` bewirkt, dass die Objekt Zuordnung auf dem Heap erfolgt, der zu einem späteren Zeitpunkt in den Garbage Collector aufgenommen werden muss. Dieses Beispiel ist besonders problematisch, da in einer Szene 1000 oder mehr Partikel vorhanden sein können, die jeweils zur aktuellen Geschwindigkeit aufgefordert werden. Folglich würden 1000 von Objekten zugeordnet und folglich die Zuordnung jedes Frames aufgehoben, wodurch die Leistung erheblich beeinträchtigt wird. Wenn Sie die Funktion so umschreiben, dass ein negativer Wert, wie z. b.-1, zurückgegeben wird, um einen Fehler anzugeben, wird dieses Problem vermieden, und der Arbeitsspeicher

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

Alle wiederholten Unity-Rückruf Funktionen (d. h. Update), die mehrmals pro Sekunde und/oder Frame ausgeführt werden, sollten sehr sorgfältig geschrieben werden. Alle teuren Vorgänge hier haben eine enorme und konsistente Auswirkung auf die Leistung.

1) **Leere Rückruf Funktionen**

    Obwohl der nachfolgende Code in der Anwendung unaktiviert erscheinen mag, insbesondere, da jedes Unity-Skript automatisch mit diesem Codeblock initialisiert wird, können diese leeren Rückrufe tatsächlich sehr kostspielig werden. Unity arbeitet über eine nicht verwaltete/verwaltete Code Grenze zwischen unityengine-Code und dem Anwendungscode hin und her. Der Kontextwechsel über diese Bridge ist auch dann recht aufwendig, wenn nichts ausgeführt werden muss. Dies wird besonders problematisch, wenn Ihre APP über 100 gameobjects-Objekte mit Komponenten verfügt, die sich wiederholende Unity-Rückrufe befinden.

    ```CS
    void Update()
    {
    }
    ```

>[!NOTE]
> Update () ist die häufigste Erscheinung dieses Leistungs Problems, aber andere sich wiederholende Unity-Rückrufe wie die folgenden können gleichermaßen schlecht sein, wenn Sie nicht schlechter sind: fixedupdate (), lateupdate (), onpostranender ", OnPreRender (), onrenderimage () usw. 

2) **Vorgänge, die eine einmalige Ausführung pro Frame bevorzugen**

    Die folgenden Unity-APIs sind gängige Vorgänge für viele Holographic-apps. Obwohl dies nicht immer möglich ist, können die Ergebnisse dieser Funktionen sehr häufig einmal berechnet werden, und die Ergebnisse werden in der gesamten Anwendung für einen bestimmten Frame wieder verwendet.

    a) in der Regel empfiehlt es sich, eine dedizierte Singleton-Klasse oder einen dedizierten Dienst zu verwenden, um Ihren Blick in die Szene zu verarbeiten und dieses Ergebnis dann in allen anderen Szenen Komponenten wieder zu verwenden, anstatt wiederholt und im Wesentlichen identische raycast Vorgänge durchzuführen. Zulieferern. Natürlich erfordern einige Anwendungen möglicherweise Raycasts aus unterschiedlichen Ursprüngen oder mit unterschiedlichen [layermasken](https://docs.unity3d.com/ScriptReference/LayerMask.html).

        UnityEngine.Physics.Raycast()
        UnityEngine.Physics.RaycastAll()

    b) vermeiden von getComponent ()-Vorgängen in wiederholten Unity-Rückrufen wie Update () durch zwischen [Speichern von verweisen](#cache-references) in Start () oder Awake ()

        UnityEngine.Object.GetComponent()

    c) Es empfiehlt sich, nach Möglichkeit alle Objekte bei der Initialisierung zu instanziieren und das [Objekt Pooling](#object-pooling) zu verwenden, um gameobjects während der Laufzeit der Anwendung wiederzuverwenden.

        UnityEngine.Object.Instantiate()

3) **Vermeiden von Schnittstellen und virtuellen Konstrukten**

    Das Aufrufen von Funktionsaufrufen über Schnittstellen im Vergleich zu direkten Objekten oder Aufrufen von virtuellen Funktionen kann häufig sehr viel teurer sein als die Verwendung von direkten Konstrukten oder direkten Funktionsaufrufen. Wenn die virtuelle Funktion oder Schnittstelle unnötig ist, sollte Sie entfernt werden. Die Leistungseinbußen, die für diese Ansätze erzielt werden, sind jedoch in der Regel der Kompromiss, wenn Sie die Entwicklung, die Lesbarkeit von Code und die Verwaltbarkeit des Codes vereinfachen.

    Im Allgemeinen wird empfohlen, Felder und Funktionen nicht als virtuell zu markieren, es sei denn, es gibt eine klare Annahme, dass dieser Member überschrieben werden muss. Sie sollten vor allem bei hochfrequenten Codepfade vorsichtig sein, die mehrmals pro Frame oder sogar einmal pro Frame aufgerufen werden, wie z. b. eine `UpdateUI()` Methode.

4) **Vermeiden Sie das Übergeben von Strukturen nach Wert.**

    Im Unterschied zu Klassen sind Strukturen Werttypen. Wenn Sie direkt an eine Funktion geleitet werden, werden Ihre Inhalte in eine neu erstellte-Instanz kopiert. Mit dieser Kopie werden CPU-Kosten und zusätzlicher Arbeitsspeicher im Stapel hinzugefügt. Bei kleinen Strukturen ist der Effekt in der Regel sehr minimal und somit akzeptabel. Bei Funktionen, die von jedem Frame wiederholt aufgerufen werden, sowie von Funktionen, die große Strukturen übernehmen, sollten Sie, wenn möglich, die Funktionsdefinition als Verweis übergeben. [Weitere Informationen finden Sie hier](https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method)

#### <a name="miscellaneous"></a>Sonstiges

1) **Mikro**

    a) im Allgemeinen ist es am einfachsten, die Physik zu verbessern, indem die für die Physik und die Anzahl der Iterationen pro Sekunde aufgewendet Zeit beschränkt wird. Dadurch wird natürlich die Simulations Genauigkeit reduziert. Siehe [TimeManager](https://docs.unity3d.com/Manual/class-TimeManager.html) in Unity

    b) der Typ von Kollisionen in Unity weist stark unterschiedliche Leistungsmerkmale auf. In der folgenden Reihenfolge werden die leistungsfähigsten Kollisionen der am wenigsten leistungsfähigen Kollisionen von links nach rechts aufgeführt. Es ist am wichtigsten, Mesh-Kollisionen zu vermeiden, die wesentlich teurer als die primitiven Kollisionen sind.

        Sphere < Capsule < Box <<< Mesh (Convex) < Mesh (non-Convex)

    Weitere Informationen finden Sie unter [bewährte Methoden](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices) für die Unity-Physik

2) **Taine**

    Deaktivieren Sie die Animation im Leerlauf, indem Sie die animatorkomponente deaktivieren (die Deaktivierung des Spiel Objekts hat nicht denselben Effekt). Vermeiden Sie Entwurfsmuster, bei denen sich ein Animator in einer Schleife befindet, in der ein Wert auf dieselbe Aktion festgelegt ist. Für diese Technik gibt es einen beträchtlichen Aufwand, ohne dass die Anwendung beeinträchtigt wird. [Weitere Informationen finden Sie hier.](https://docs.unity3d.com/Manual/MecanimPeformanceandOptimization.html)

3) **Komplexe Algorithmen**

    Wenn Ihre Anwendung komplexe Algorithmen verwendet, wie z. b. umgekehrte Kinematik, Pfad Suche usw., suchen Sie nach einem einfacheren Ansatz, oder passen Sie relevante Einstellungen für Ihre Leistung an.

## <a name="cpu-to-gpu-performance-recommendations"></a>Empfehlungen zur CPU-zu-GPU-Leistung

Im Allgemeinen kommt die CPU-zu-GPU-Leistung auf die **Zeichnen-Aufrufe** an, die an die Grafikkarte übermittelt werden. Um die Leistung zu verbessern, müssen Draw-Aufrufe strategisch **a) reduziert** oder **b) umstrukturiert** werden, um optimale Ergebnisse zu erzielen. Da zeichnen-Aufrufe selbst ressourcenintensiv sind, verringern Sie dadurch die insgesamt erforderliche Arbeit. Außerdem erfordert die Zustandsänderung zwischen zeichnen-aufrufen kostspielige Validierungs-und Übersetzungsschritte im Grafiktreiber und somit die Umstrukturierung der Draw-Aufrufe Ihrer Anwendung, um Zustandsänderungen einzuschränken (d. h. verschiedene Materialien usw.) können die Leistung steigern.

Unity bietet einen großartigen Artikel, der einen Überblick über die Batch Verarbeitung von Draw-aufrufen für Ihre Plattform bietet.
- [Batch Verarbeitung von Unity-zeichnen-aufrufen](https://docs.unity3d.com/Manual/DrawCallBatching.html)

#### <a name="single-pass-instanced-rendering"></a>Single Pass-instanziziertes Rendering

Bei einem Single Pass-instanziierten Rendering in Unity können zeichnen-Aufrufe für jedes Auge auf einen instanziierten Draw-Aufruf reduziert werden. Aufgrund der Cache Kohärenz zwischen zwei Draw-aufrufen gibt es auch eine gewisse Leistungsverbesserung bei der GPU.

So aktivieren Sie dieses Feature in Ihrem Unity-Projekt
1)  Öffnen Sie die **Player-XR-Einstellungen** (wechseln Sie zu **Edit** > **Project Settings** > **Player** > **XR-Einstellungen**)
2) Wählen Sie im Dropdown Menü der **Stereo Renderingmethode** die Option **Single Pass-instanziierten** aus (Kontrollkästchen**Virtual Reality supported** muss aktiviert sein).

Weitere Informationen zu diesem renderingansatz finden Sie in den folgenden Artikeln von Unity.
- [Maximieren der AR-und VR-Leistung mit dem erweiterten Stereo Rendering](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [Einzelpass-Instanziierung](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> Ein häufiges Problem mit einem einzelnen Pass-instanziierten Rendering tritt auf, wenn Entwickler bereits über vorhandene benutzerdefinierte Shader verfügen, die nicht für die Instanziierung Nachdem Sie diese Funktion aktiviert haben, bemerken Entwickler möglicherweise, dass einige gameobjects nur in einem Blick dargestellt werden. Dies liegt daran, dass die zugeordneten benutzerdefinierten Shader nicht über die entsprechenden Eigenschaften für die Instanziierung verfügen.
>
> Informationen zum Beheben dieses Problems finden Sie unter [Single Pass Stereo Rendering for hololens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) from Unity.

#### <a name="static-batching"></a>Statische Batch Verarbeitung

Unity kann viele statische Objekte in Batches erstellen, um Draw-Aufrufe an die GPU zu verringern. Die statische Batchverarbeitung funktioniert für die meisten [Renderer](https://docs.unity3d.com/ScriptReference/Renderer.html)-Objekte in Unity, die **dasselbe Material aufweisen** und **als *Static* markiert sind**. (Wählen Sie ein Objekt in Unity aus, und klicken Sie auf das Kontrollkästchen in der oberen rechten Ecke des Inspektors.) Gameobjects, die als *statisch* gekennzeichnet sind, können nicht während der Laufzeit der Anwendung verschoben werden. Daher kann es schwierig sein, die statische Batch Verarbeitung auf hololens zu nutzen, bei dem praktisch jedes Objekt platziert, verschoben, skaliert usw. werden muss. Bei immersiven Headsets kann die statische Batch Verarbeitung zeichnen-Aufrufe drastisch reduzieren und somit die Leistung verbessern.

Ausführlichere Informationen *finden Sie unter* [Batch Verarbeitung in der Batch Verarbeitung in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) .

#### <a name="dynamic-batching"></a>Dynamische Batch Verarbeitung

Da das Markieren von Objekten als *statisch* für die Entwicklung von hololens problematisch ist, kann die dynamische Batch Verarbeitung ein hervorragend Tool sein, um diese fehlende Funktion auszugleichen. Natürlich kann es auch für immersive Headsets nützlich sein. Die dynamische Batch Verarbeitung in Unity kann schwierig sein, um dies zu ermöglichen, weil gameobjects eine aufweisen muss **) dasselbe Material gemeinsam** verwenden und **b) eine lange Liste anderer Kriterien erfüllen**.

Lesen Sie die *dynamische Batch* Verarbeitung unter [Zeichnen von zeichnen-aufrufen in Unity](https://docs.unity3d.com/Manual/DrawCallBatching.html) für die vollständige Liste. In den meisten Fällen werden gameobjects ungültig, damit Sie in einem Batch zusammengefasst werden, da die zugeordneten Mesh-Daten nicht mehr als 300 Scheitel Punkte aufweisen können.

#### <a name="other-techniques"></a>Weitere Verfahren

Die Batch Verarbeitung kann nur auftreten, wenn mehrere gameobjects dasselbe Material gemeinsam verwenden können. Dies wird in der Regel dadurch blockiert, dass gameobjects eine eindeutige Textur für das jeweilige Material aufweisen muss. Es ist üblich, Texturen in eine große Textur zu kombinieren, eine Methode, die als [Textur](https://en.wikipedia.org/wiki/Texture_atlas)Nachweis bezeichnet wird.

Außerdem ist es in der Regel besser, nach Möglichkeit und vernünftig Nachrichten in einem gameobject zu kombinieren. Jeder Renderer in Unity verfügt über einen zugeordneten zeichnen-Befehl (en) im Vergleich zum Senden eines kombinierten Netzes unter einem Renderer.

>[!NOTE]
> Wenn Sie die Eigenschaften von Renderer. Material zur Laufzeit ändern, wird eine Kopie des Materials erstellt und somit die Batch Verarbeitung möglicherweise unterbrechen. Verwenden Sie Renderer. sharedmaterial, um freigegebene Materialeigenschaften über gameobjects zu ändern.

## <a name="gpu-performance-recommendations"></a>Empfehlungen zur GPU-Leistung

Weitere Informationen zum [Optimieren des Grafik Rendering in Unity](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games)

### <a name="optimize-depth-buffer-sharing"></a>Optimieren der tiefen Puffer Freigabe

Im Allgemeinen wird empfohlen, die **Tiefe Puffer Freigabe** unter den Einstellungen von " **Player XR** " zu aktivieren, um die [Stabilität von – Hologramm](Hologram-stability.md)zu optimieren Beim Aktivieren der tiefen basierten neuprojektion mit dieser Einstellung wird jedoch empfohlen, anstelle des **24-Bit-Tiefen**Formats ein **16-Bit-Tiefen Format** auszuwählen. Durch die 16-Bit-Tiefen Puffer wird die Bandbreite (und damit auch die Stromversorgung) drastisch verringert, die dem tiefen Puffer Datenverkehr zugeordnet Dies kann ein großer Gewinn sowohl bei der Energie Reduzierung als auch bei der Leistungsverbesserung sein. Es gibt jedoch zwei mögliche negative Ergebnisse, wenn Sie ein *16-Bit-Tiefen Format*verwenden.

**Z-kämpfen**

Die Genauigkeit der reduzierten tiefen Bereiche bewirkt, dass [z-Kämpfe](https://en.wikipedia.org/wiki/Z-fighting) mit einem 16-Bit-Wert als 24-Bit wahrscheinlicher werden. Um diese Artefakte zu vermeiden, ändern Sie die Near-und Far-Clip-Ebenen der [Unity-Kamera](https://docs.unity3d.com/Manual/class-Camera.html) , um die geringere Genauigkeit zu berücksichtigen. Bei hololens-basierten Anwendungen kann die mittlere Ausschneide Ebene von 50 Mio. anstelle des Unity-Standardwerts von 1000 Millionen in der Regel alle z-Kämpfe eliminieren.

**Deaktivierter Schablonen Puffer**

Wenn Unity eine [rendertextur mit 16-Bit-Tiefe](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html)erstellt, wird kein Schablonen Puffer erstellt. Durch die Auswahl des 24-Bit-Tiefen Formats pro Unity-Dokumentation wird ein 24-Bit-z-Puffer und ein [8-Bit-Schablone](https://docs.unity3d.com/Manual/SL-Stencil.html) erstellt (wenn 32-Bit auf dem Gerät anwendbar ist, was im Allgemeinen der Fall ist, z. b. hololens).

### <a name="avoid-full-screen-effects"></a>Vermeiden von vollbildeffekten

Techniken, die auf dem Vollbildmodus ausgeführt werden, können sehr aufwendig sein, da die Reihenfolge der Größe in jedem Frame Millionen von Vorgängen ist. Daher wird empfohlen, [nach Verarbeitungs Effekten](https://docs.unity3d.com/Manual/PostProcessingOverview.html) wie Antialiasing, Blüte und mehr zu vermeiden.

### <a name="optimal-lighting-settings"></a>Optimale Beleuchtungseinstellungen

Die [globale Echtzeitbeleuchtung](https://docs.unity3d.com/Manual/GIIntro.html) in Unity kann ausstehende visuelle Ergebnisse bereitstellen, beinhaltet jedoch sehr teure Beleuchtungsberechnungen. Es wird empfohlen, die globale Echtzeitbeleuchtung für jede Unity-Szenen Datei über **Fenster** > **Rendering** > **Beleuchtungseinstellungen** zu deaktivieren > die **Globale Beleuchtung in Echtzeit**zu deaktivieren.

Außerdem wird empfohlen, alle Schatten Umwandlungen zu deaktivieren, da diese auch teure GPU-Pässe zu einer Unity-Szene hinzufügen. Schatten können pro Licht deaktiviert werden, können aber auch über Qualitätseinstellungen ganzheitlich gesteuert werden.

**Bearbeiten** Sie > **Projekteinstellungen**, und wählen Sie dann die Kategorie **Qualität** aus, > Wählen Sie für die UWP-Plattform **niedrige Qualität** aus. Sie können auch die **Shadows** -Eigenschaft so festlegen, dass **Schatten deaktiviert**werden.

### <a name="reduce-poly-count"></a>Reduzieren der polyzahl

Die Polygon Anzahl wird in der Regel durch
1) Entfernen von Objekten aus einer Szene
2) Assetdezigierung, die die Anzahl von Polygonen für ein bestimmtes Mesh reduziert
3) Implementieren eines [Lod-Systems (Level of Detail)](https://docs.unity3d.com/Manual/LevelOfDetail.html) in Ihre Anwendung, das entfernte Objekte mit niedrigerer Polygon Version derselben Geometrie rendert

### <a name="understanding-shaders-in-unity"></a>Grundlegendes zu Shadern in Unity

Eine einfache Näherung zum Vergleichen von Shadern in der Leistung besteht darin, die durchschnittliche Anzahl der Vorgänge zu identifizieren, die jeweils zur Laufzeit ausgeführt werden. Dies kann in Unity problemlos erfolgen.

1) Wählen Sie Ihr shaderasset aus, oder wählen Sie ein Material aus, und wählen Sie dann in der oberen rechten Ecke des Inspektorfensters das Zahnrad Symbol und dann **"Shader auswählen"** aus.

    ![Shader in Unity auswählen](images/Select-shader-unity.png)
2) Wenn das Shader-Medienobjekt ausgewählt ist, klicken Sie im Inspektor-Fenster auf die Schaltfläche **"Code kompilieren und anzeigen"** .

    ![Kompilieren von Shader-Code in Unity](images/compile-shader-code-unity.PNG)

3) Suchen Sie nach dem Kompilieren in den Ergebnissen nach dem Statistik Abschnitt, wobei die Anzahl der verschiedenen Vorgänge sowohl für den Scheitelpunkt als auch für den Pixelshader angezeigt wird (Hinweis: Pixel-Shader werden oft auch als fragmentshader bezeichnet).

    ![Unity-Standard-Shader-Vorgänge](images/unity-standard-shader-compilation.png)

#### <a name="optimize-pixel-shaders"></a>Optimieren von Pixel-Shadern

Wenn Sie die kompilierten statistischen Ergebnisse mithilfe der obigen Methode betrachten, führt der [fragmentshader](https://en.wikipedia.org/wiki/Shader#Pixel_shaders) im Durchschnitt im Allgemeinen mehr Vorgänge aus als der [Vertex-Shader](https://en.wikipedia.org/wiki/Shader#Vertex_shaders) . Der fragmentshader, auch als Pixelshader bezeichnet, wird pro Pixel auf der Bildschirmausgabe ausgeführt, während der Vertexshader nur pro Scheitelpunkt aller auf dem Bildschirm gezeichneten Netzen ausgeführt wird. 

Daher weisen nicht nur fragmentshader aufgrund der Beleuchtungsberechnungen mehr Anweisungen als Vertex-Shader auf. fragmentshader werden fast immer auf einem größeren Dataset ausgeführt. Wenn die Bildschirmausgabe z. b. ein 2K-und 2K-Bild ist, kann der fragmentshader 2000 * 2.000 = 4 Millionen Mal ausgeführt werden. Wenn zwei Augen gerendert werden, verdoppelt sich diese Zahl, da zwei Bildschirme vorhanden sind. Wenn eine gemischte Reality-Anwendung über mehrere Durchgänge, voll Bild Vorgänge nach der Verarbeitung oder das Rendern mehrerer Netze auf das gleiche Pixel verfügt, erhöht sich diese Anzahl erheblich. 

Daher kann das Reduzieren der Anzahl von Vorgängen im fragmentshader im allgemeinen weitaus größere Leistungssteigerungen gegenüber Optimierungen im Vertexshader bieten.

#### <a name="unity-standard-shader-alternatives"></a>Unity-Standard-Shader-Alternativen

Anstatt ein physisch basiertes Rendering (PBR) oder einen anderen hochwertigen Shader zu verwenden, sollten Sie einen leistungsfähigsten und kostengünstigeren Shader nutzen. Das [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity) stellt den [mrtk-Standard-Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) bereit, der für Projekte mit gemischter Realität optimiert wurde.

Unity bietet auch eine nicht beleuchtete, vertexlit, diffuse und andere vereinfachte Shader-Optionen, die im Vergleich zum Unity-Standard-Shader erheblich schneller sind. Ausführlichere Informationen finden Sie [unter Nutzung und Leistung integrierter Shader](https://docs.unity3d.com/Manual/shader-Performance.html) .

#### <a name="shader-preloading"></a>Shader-vorab laden

Verwenden Sie das *Vorladen von Shader* und andere Tricks, um die [Shader-Ladezeit](https://docs.unity3d.com/Manual/OptimizingShaderLoadTime.html)zu optimieren. Das Vorladen von Shader bedeutet insbesondere, dass Sie aufgrund der Laufzeit-Shader-Kompilierung keine Treffer anzeigen können.

### <a name="limit-overdraw"></a>Limit überzeichnen

In Unity kann eine Überzeichnung für Ihre Szene angezeigt werden, indem Sie das [**Zeichnungsmodus-Menü**](https://docs.unity3d.com/Manual/ViewModes.html) in der oberen linken Ecke der **Szene Ansicht** umschalten und **überzeichnen**auswählen.

Im Allgemeinen kann die Überschreibung durch die Erstellung von Objekten vor dem Senden an die GPU verringert werden. Unity bietet ausführliche Informationen zum Implementieren von [Okklusions Berechnungen](https://docs.unity3d.com/Manual/OcclusionCulling.html) für die Engine.

## <a name="memory-recommendations"></a>Speicher Empfehlungen

Eine übermäßige Speicher Belegung & Zuordnungs Vorgängen kann negative Auswirkungen auf Ihre Holographic-Anwendung haben, was zu inkonsistenter Leistung, fixierten Frames und anderem schädlichen Verhalten führt. Es ist besonders wichtig, die Arbeitsspeicher Aspekte zu verstehen, wenn Sie in Unity entwickeln, da die Speicherverwaltung durch die Garbage Collector gesteuert wird.

#### <a name="garbage-collection"></a>Garbage Collection

Holographic apps verlieren die Verarbeitung der COMPUTE-Zeit auf die Garbage Collector (GC), wenn die GC aktiviert ist, um Objekte zu analysieren, die während der Ausführung nicht mehr im Gültigkeitsbereich sind, und der Arbeitsspeicher freigegeben werden muss, damit Sie wieder verwendet werden können. Konstante Zuordnungen und Zuordnungen erfordern im Allgemeinen, dass die Garbage Collector häufiger ausgeführt werden, wodurch Leistung und Benutzer Leistung beeinträchtigt werden.

Unity hat eine hervorragende Seite bereitgestellt, auf der ausführlich erläutert wird, wie die Garbage Collector funktioniert und wie Sie in Bezug auf die Speicherverwaltung effizienterer Code schreiben können.
- [Optimieren von Garbage Collection in Unity-spielen](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)

Eine der gängigsten Methoden, die zu einer übermäßigen Garbage Collection führt, besteht darin, keine Verweise auf Komponenten und Klassen in der Unity-Entwicklung zwischenzuspeichern. Alle Verweise sollten während des Starts () oder in "Awake ()" aufgezeichnet und in späteren Funktionen wie "Update ()" oder "lateupdate ()" wieder verwendet werden.

Weitere Quick Infos:
- Verwenden der [StringBuilder](https://docs.microsoft.com/dotnet/api/system.text.stringbuilder?view=netframework-4.7.2) C# -Klasse zum dynamischen Erstellen komplexer Zeichen folgen zur Laufzeit
- Entfernen Sie Aufrufe von Debug. log (), wenn Sie nicht mehr benötigt werden, da Sie immer noch in allen Buildversionen einer app ausgeführt werden.
- Wenn Ihre Holographic-app in der Regel viel Speicher erfordert, sollten Sie beim Laden von Phasen (z. b. beim Anzeigen eines Lade-oder Übergangs Bildschirms [ _**) System. GC. Collect () aufrufen.**_ ](https://docs.microsoft.com/dotnet/api/system.gc.collect?view=netframework-4.7.2)

#### <a name="object-pooling"></a>Objekt Pooling

Objekt Pooling ist eine gängige Methode, um die Kosten für fortlaufende Zuordnungen & die Zuordnung von Objekten zu reduzieren. Dies erfolgt durch Zuordnen eines großen Pools identischer Objekte und erneutes verwenden inaktiver, verfügbarer Instanzen aus diesem Pool, anstatt ständig Objekte im Zeitverlauf zu erzeugen und zu zerstören. Objekt Pools eignen sich hervorragend für wiederverwendbare Komponenten, die während einer APP über eine Variablen Lebensdauer verfügen.

- [Tutorial zum Objektpooling in Unity](https://unity3d.com/learn/tutorials/topics/scripting/object-pooling) 

## <a name="startup-performance"></a>Startleistung

Sie sollten die app in einer kleineren Szene starten und dann *[scenemanager. loadsceneasync](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.LoadSceneAsync.html)* verwenden, um den Rest der Szene zu laden. Dadurch kann Ihre APP so schnell wie möglich einen interaktiven Zustand erreichen. Beachten Sie, dass es möglicherweise zu einer großen CPU-Spitze kommt, während die neue Szene aktiviert wird, und dass sich jeder gerenderte Inhalt möglicherweise in den Ruhezustand versetzt. Eine Möglichkeit, dieses Problem zu umgehen, besteht darin, die AsyncOperation. allowsceneactivation-Eigenschaft in der zu ladenden Szene auf "false" festzulegen, die Szene zu laden, den Bildschirm in schwarz zu löschen und dann auf "true" festzulegen, um die Szenen Aktivierung abzuschließen.

Beachten Sie, dass beim Laden der Startszene der Holographic-Begrüßungsbildschirm für den Benutzer angezeigt wird.

## <a name="see-also"></a>Weitere Informationen
- [Optimieren des Grafik Rendering in Unity-spielen](https://unity3d.com/learn/tutorials/temas/performance-optimization/optimizing-graphics-rendering-unity-games?playlist=44069)
- [Optimieren von Garbage Collection in Unity-spielen](https://unity3d.com/learn/tutorials/topics/performance-optimization/optimizing-garbage-collection-unity-games?playlist=44069)
- [Bewährte Methoden für die Physik [Unity]](https://unity3d.com/learn/tutorials/topics/physics/physics-best-practices)
- [Optimieren von Skripts [Unity]](https://docs.unity3d.com/Manual/MobileOptimizationPracticalScriptingOptimizations.html)
