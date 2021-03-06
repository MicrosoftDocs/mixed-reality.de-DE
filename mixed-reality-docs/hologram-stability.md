---
title: Hologrammstabilität
description: Die hololens stabilisieren automatisch holograms, aber es gibt Schritte, die Entwickler durchführen können, um die hologrammstabilität weiter zu verbessern.
author: thetuvix
ms.author: alexturn
ms.date: 07/08/2020
ms.topic: article
keywords: holograms, Stabilität, hololens
appliesto:
- HoloLens
ms.openlocfilehash: 4a489c923138808e3afb545097c314f354b5ad2a
ms.sourcegitcommit: 2813f5b3027d47f7c6e9772338935eeccfa2aaec
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2020
ms.locfileid: "86408208"
---
# <a name="hologram-stability"></a>Hologrammstabilität

## <a name="overview"></a>Überblick

Zum erreichen stabiler Hologramme verfügt hololens über eine integrierte Pipeline zur Bildstabilisierung. Die Stabilisierungs Pipeline funktioniert automatisch im Hintergrund, sodass Sie keine zusätzlichen Schritte ausführen müssen, um Sie zu aktivieren. Allerdings sollten Sie Techniken anwenden, die die Stabilität des Hologramms verbessern und Szenarios vermeiden, die die Stabilität verringern.

## <a name="hologram-quality-terminology"></a>Hologram Quality-Terminologie

Die Qualität von holograms ist das Ergebnis einer guten Umgebung und einer guten App-Entwicklung. Apps, die mit einer Konstanten 60 Frames pro Sekunde in einer Umgebung ausgeführt werden, in der hololens die Umgebung nachverfolgen können, stellt sicher, dass das Hologramm und das passende Koordinatensystem synchronisiert sind. Aus Sicht eines Benutzers werden holograms, die stationär sein sollen, nicht relativ zur Umgebung verschoben.

Die folgende Terminologie kann Ihnen helfen, wenn Sie Probleme mit der Umgebung, inkonsistente oder niedrige Renderingleistung oder etwas anderes erkennen.
* **Genau.** Nachdem das – Hologramm weltweit gesperrt und in der realen Welt platziert wurde, sollte es sich in der Umgebung befinden, in der es relativ zur umgebenden Umgebung ist, und unabhängig von der Benutzer Bewegung oder kleinen und geringfügigen Umgebungs Änderungen. Wenn ein – Hologramm später an einem unerwarteten Speicherort angezeigt wird, ist dies ein *Genauigkeits* Problem. Solche Szenarien können eintreten, wenn zwei unterschiedliche Räume identisch aussehen.
* **Jitter.** Benutzer beobachten Jitter als hohes Frequenz schütteln eines holograms, das auftreten kann, wenn die Nachverfolgung der Umgebung beeinträchtigt wird. Für Benutzer wird die [Sensor](sensor-tuning.md)Optimierung von der Lösung ausgeführt.
* **Der Judder.** Niedrige renderingfrequenzen führen zu ungleichen Bewegungs-und doppelten Bildern von holograms. Der Judder ist in holograms mit Motion besonders bemerkbar. Entwickler müssen eine [Konstante 60 fps](hologram-stability.md#frame-rate)beibehalten.
* **Inter.** Benutzern wird die Abweichung angezeigt, da ein – Hologramm von der ursprünglichen Position entfernt wird. Die Abweichung tritt auf, wenn holograms von [räumlichen Ankern](spatial-anchors.md)fern platziert werden, insbesondere in nicht vollständig zugeordneten Teilen der Umgebung. Das Erstellen von holograms in der Nähe räumlicher Anker verringert die Wahrscheinlichkeit einer Abweichung.
* **Schnell Einstieg.** Wenn ein – Hologramm gelegentlich von seinem Speicherort "springt" oder "springt". Wenn die Nachverfolgung holograms anpasst, werden die aktualisierten Kenntnisse ihrer Umgebung angepasst.
* **MME.** Wenn ein – Hologramm zu bewegen scheint, das der Bewegung des Benutzer Kopfes entspricht. Das Schwimmen tritt auf, wenn die Anwendung die [neuprojektion](hologram-stability.md#reprojection)nicht vollständig implementiert hat und die hololens nicht für den aktuellen Benutzer [abgestimmt](calibration.md) sind. Der Benutzer kann die [Kalibrierungs](calibration.md) Anwendung erneut ausführen, um das Problem zu beheben. Entwickler können die Stabilisierungs Ebene aktualisieren, um die Stabilität zu verbessern.
* **Farbtrennung.** Die Anzeige in hololens ist ein sequenzieller sequenzieller Display, bei dem die Flash-Farbkanäle von rot-grün-blau-grün bei 60 Hz angezeigt werden (einzelne Farbfelder werden unter 240 Hz angezeigt). Jedes Mal, wenn ein Benutzer ein bewegendes Hologramm mit den Augen verfolgt, werden die führenden und nachfolgenden Kanten des – Hologramm in den einzelnen Farben getrennt und erzeugen einen Regenbogeneffekt. Der Grad der Trennung hängt von der Geschwindigkeit des holograms ab. In einigen seltenen Fällen kann es bei der Betrachtung eines stationären holograms auch zu einem Regenbogeneffekt kommen, der als *[Farbtrennung](hologram-stability.md#color-separation)* bezeichnet wird.

## <a name="frame-rate"></a>Bildfrequenz

Die Framerate ist die erste Säule der – Hologramm-Stabilität. Damit holograms weltweit stabil angezeigt werden, muss für jedes Bild, das dem Benutzer präsentiert wird, das holograms an der richtigen Stelle gezeichnet werden. Die Anzeige auf hololens wird 240 mal pro Sekunde aktualisiert, wobei vier separate Farbfelder für jedes neu gerenderte Bild angezeigt werden, was zu einer Benutzer Darstellung von 60 fps (Frames pro Sekunde) führt. Um die bestmögliche Leistung zu gewährleisten, müssen Anwendungsentwickler 60 FPS verwalten. Dies bedeutet, dass alle 16 Millisekunden stets ein neues Image für das Betriebssystem bereitgestellt wird.

**60 fps** Um holograms so zu zeichnen, dass Sie sich in der realen Welt befinden, müssen hololens Bilder aus der Position des Benutzers Rendering. Da das Rendern von Bildern Zeit erfordert, prognostizieren hololens, wo sich der Benutzer befindet, wenn die Bilder in den anzeigen angezeigt werden. Dieser Vorhersagealgorithmus ist jedoch eine Näherung. Hololens verfügt über Hardware, die das gerenderte Bild anpasst, um die Diskrepanz zwischen der vorhergesagten Kopfzeile und der tatsächlichen Head-Position zu berücksichtigen. Durch die Anpassung wird das Bild, das dem Benutzer angezeigt wird, so angezeigt, als ob es vom richtigen Speicherort gerendert wird, und holograms sind stabil. Die Image Aktualisierungen funktionieren am besten mit kleinen Änderungen und können bestimmte Dinge im gerenderten Image wie Motion-Parser nicht vollständig beheben.

Durch Rendering bei 60 fps führen Sie drei Dinge aus, um stabile Hologramme zu erstellen:
1. Minimierung der Gesamt Latenz zwischen dem Rendern eines Bilds und dem Bild, das für den Benutzer sichtbar ist. In einer Engine mit einem Spiel und einem Renderthread, der in Lockstep ausgeführt wird, kann die Ausführung bei 30fps 33,3 MS zusätzlicher Latenz addieren. Durch das Reduzieren der Latenzzeit wird der Vorhersagefehler verringert
2. Dadurch wird für jedes Bild, das die Augen des Benutzers erreicht, eine konsistente Latenzzeit erzielt. Wenn Sie bei 30 fps Rendering, zeigt die Anzeige weiterhin Bilder bei 60 fps an, was bedeutet, dass dasselbe Bild zweimal in einer Zeile angezeigt wird. Der zweite Frame weist eine höhere Latenz von 16,6 ms als der erste Frame auf und muss eine deutlichere Menge an Fehlern beheben. Diese Inkonsistenzen in der Fehler Größe können unerwünschte 60 Hz-Judder auslösen.
3. Verringern des Auftretens von Vibration (Judder), die sich durch ungleichmäßige Bewegung und Doppelbilder bemerkbar macht. Eine schnellere Bewegung von Hologrammen und niedrigere Renderingraten gehen mit verstärkter Vibration einher. Wenn Sie 60 fps jederzeit verwalten möchten, können Sie den Judder für ein bestimmtes bewegliches Hologram vermeiden.

**Konsistenz der Frame Rate** Die Konsistenz der Framerate ist so wichtig wie ein hoher Rahmen pro Sekunde. Gelegentlich gelöschte Frames sind für jede Content-Rich-Anwendung unvermeidlich, und der hololens implementiert einige ausgereifte Algorithmen, um gelegentlich auftretende Fehler zu beheben. Ein ständig schwankender Framerate ist für einen Benutzer jedoch deutlich deutlicher als bei einer konsistenten Ausführung mit niedrigeren Frameraten. Beispielsweise wird eine Anwendung, die für fünf Frames reibungslos rendert (60 fps für die Dauer dieser fünf Frames) und dann jeden anderen Frame für die nächsten 10 Frames (30 fps für die Dauer dieser 10 Frames) als eine Anwendung, die konsistent mit 30 fps rendert, angezeigt.

Auf eine verwandte Anmerkung beschränkt das Betriebssystem Anwendungen auf 30 fps, wenn die [gemischte Reality-Erfassung](mixed-reality-capture.md) ausgeführt wird.

**Leistungsanalyse** Es gibt verschiedene Arten von Tools, die verwendet werden können, um die Anwendungs Frame Rate zu messen, z. b.:
* GPUView
* Visual Studio-Grafikdebugger
* Profiler, die in 3D-Engines wie Unity integriert sind

## <a name="hologram-render-distances"></a>Hologram-Rendering-Entfernungen

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

Das menschliche visuelle System integriert mehrere entfernungsabhängige Signale, wenn es ein Objekt korrigiert und fokussiert.
* [Unterkunft](https://en.wikipedia.org/wiki/Accommodation_%28eye%29) : der Schwerpunkt eines einzelnen Auges.
* [Konvergenz](https://en.wikipedia.org/wiki/Convergence_(eye)) : zwei Augen werden nach innen oder nach außen verschoben, um auf ein Objekt zu zentrieren.
* [Binbichtbild](https://en.wikipedia.org/wiki/Stereopsis) : Unterschiede zwischen der linken und der rechten Seite, die von der Entfernung eines Objekts von Ihrem Fixpunkt abhängen.
* Schattierung, relative Angular-Größe und andere monokuläre Cues (Single Eye).

Konvergenz und Unternehmen sind einzigartig, da ihre zusätzlichen Verb-Retinal-Hinweise darauf, wie sich die Augen ändern, um Objekte in unterschiedlichen Abständen zu erkennen. In natürlicher Ansicht sind Konvergenz und Unterbringung verknüpft. Wenn die Augen etwas in der Nähe angezeigt werden (z. b. ihre Nase), werden die Augen zu einem Punkt hin-und her. Wenn die Augen etwas unendlich sehen, werden die Augen parallel angezeigt, und das Auge ist unendlich. 

Benutzer, die hololens durchführen, können immer 2,0 Mio. erreichen, um ein klares Bild zu erhalten, da die hololens-Anzeige in einer optischen Entfernung von ungefähr 2,0 m vom Benutzer korrigiert wird. App-Entwickler steuern, wohin die Augen der Benutzer konvergiert werden, indem Sie Inhalte und Hologramme in verschiedenen Tiefen platzieren. Wenn Benutzer unterschiedliche Entfernungen aufnehmen und mit Ihnen zusammenführen, ist die natürliche Verknüpfung zwischen den beiden hinweisen fehlerhaft, was zu einem visuellen Unbehagen oder Müdigkeit führen kann, insbesondere wenn die Größe des Konflikts sehr groß ist. 

Die Unannehmlichkeiten aus dem Vergence--Unterbringungs Konflikt können vermieden oder minimiert werden, indem konvergierter Inhalt so nah wie möglich an 2,0 m gehalten wird (also in einer Szene mit sehr viel Tiefe, wenn möglich, die interessanten Bereiche in der Nähe von 2,0 m). Wenn Inhalte in der Nähe von 2,0 Mio. nicht platziert werden können, ist das Problem des Konflikts mit der Vergence-Unterkunft am größten, wenn der Benutzer zwischen den verschiedenen Entfernungen hin und her sucht. Anders ausgedrückt: Es ist viel besser, sich ein stationäres – Hologramm anzusehen, das 50 cm entfernt bleibt, als ein – Hologramm 50 cm zu betrachten, das sich im Laufe der Zeit von Ihnen hin und her bewegt.

Das Platzieren von Inhalten auf 2,0 m ist ebenfalls vorteilhaft, da die beiden anzeigen so konzipiert sind, dass Sie sich in dieser Entfernung vollständig überlappen Bei Bildern, die auf dieser Ebene platziert werden, werden Sie, wenn Sie sich von der Seite des Holographic Frame bewegen, von einem Bildschirm angezeigt, während Sie auf dem anderen angezeigt werden. Diese binare Rivalität kann die Tiefe Wahrnehmung der holorgam stören.

**Optimale Entfernung vom Benutzer für die Positionierung von Hologrammen**

![Optimale Entfernung vom Benutzer für die Positionierung von Hologrammen](images/distanceguiderendering-750px.png)

**Clip Flächen** Für maximalen Komfort empfehlen wir die Clipping-renderentfernung bei 85 cm, wobei der Inhalt beginnend bei 1 Mio. nicht mehr angezeigt wird. In Anwendungen, in denen holograms und Benutzer beide stationär sind, können holograms bequem in der Nähe von 50 cm angezeigt werden. In diesen Fällen sollten Anwendungen eine Ausschneide Ebene von höchstens 30 cm platzieren, und das ausblenden sollte mindestens 10 cm von der Ausschneide Ebene ausgehen. Wenn Inhalt größer als 85 cm ist, müssen Sie sicherstellen, dass die Benutzer nicht häufig von holograms näher oder weiter wechseln, oder dass holograms nicht häufig in den Benutzer gelangen, der sich nicht mehr auf den Benutzer nähert. Der Inhalt sollte so entworfen werden, dass er die Notwendigkeit einer Interaktion mit einem Wert von mehr als 85 cm vom Benutzer minimiert, aber wenn Inhalte mehr als 85 cm gerendert werden müssen, ist es eine gute Faustregel für Entwickler, Szenarios zu entwerfen, in denen Benutzer und/oder Hologramme mehr als 25% der Zeit nicht mehr in die Tiefe gehen.

**Bewährte Methoden** Wenn holograms bei 2 m nicht platziert werden können und Konflikte zwischen Konvergenz und Unterbringung nicht vermieden werden können, liegt die optimale Zone für die – Hologramm-Platzierung zwischen 1,25 m und 5 m. In jedem Fall sollten Designer Inhalte strukturieren, um Benutzern die Interaktion von 1 + m zu empfehlen (z. b. Anpassen von Inhalts Größe und Standard Platzierungs Parametern).

## <a name="reprojection"></a>Neuprojektion
Hololens führt eine ausgereifte Hardware gestützte Holographic-Stabilisierungstechnik aus, die als neuprojektion bezeichnet wird. Die neuprojektion berücksichtigt die Bewegung und Änderung der Sicht (camerapose), wenn die Szene animiert wird und der Benutzer die Kopfzeile verschiebt.  Anwendungen müssen bestimmte Aktionen ausführen, um die neuprojektion am besten zu verwenden.


Es gibt vier Haupttypen der neuprojektion.
* **Tiefen neuprojektion:**  Erzeugt die besten Ergebnisse mit dem geringsten Aufwand aus der Anwendung.  Alle Teile der gerenderten Szene werden abhängig von ihrer Entfernung zum Benutzer unabhängig voneinander stabilisiert.  Einige Renderingartefakte sind möglicherweise sichtbar, wenn eine Tiefe Tiefe von Änderungen vorliegt.  Diese Option ist nur für hololens 2 und immersive Headsets verfügbar.
* **Planare neuprojektion:**  Ermöglicht der Anwendung die genaue Steuerung der Stabilisierung.  Eine Ebene wird von der Anwendung festgelegt, und alles auf dieser Ebene ist der stabilste Teil der Szene.  Wenn ein – Hologramm von der Ebene entfernt wird, desto weniger stabil ist es.  Diese Option ist auf allen Windows-Windows-Plattformen verfügbar.
* **Automatische planare neuprojektion:**  Das System legt mithilfe der Informationen im tiefen Puffer eine Stabilisierungs Ebene fest.  Diese Option ist auf hololens-Generation 1 und hololens 2 verfügbar.
* **Keine:** Wenn die Anwendung keine Aktion ausführt, wird die planare neuprojektion mit der auf zwei Metern gesetzten Stabilisierungs Ebene in der Richtung des Kopf Anrufs des Benutzers verwendet, in der Regel die untergeordneten Ergebnisse.

Anwendungen müssen bestimmte Aktionen durchführen, um die verschiedenen Arten der neuprojektion zu aktivieren.
* **Tiefen neuprojektion:** Die Anwendung übermittelt ihren tiefen Puffer für jeden gerenderten Frame an das System.  Bei Unity wird die tiefen neuprojektion mit der Option frei gegebener **tiefen Puffer** im **Windows Mixed Reality-Einstellungs** Bereich unter **XR-Plug**-in-Verwaltung ausgeführt.  DirectX-apps CommitDirect3D11DepthBuffer-Aufrufe.  Die Anwendung sollte setfocuspoint nicht aufrufen.
* **Planare neuprojektion:** Bei jedem Frame teilen Anwendungen dem System den Speicherort einer zu stabilisierende Ebene mit.  Unity-Anwendungen nennen setfocuspointforframe und sollten den frei **gegebenen tiefen Puffer** deaktiviert haben.  DirectX-apps aufrufen setfocuspoint und sollten CommitDirect3D11DepthBuffer nicht aufrufen.
* **Automatische planare neuprojektion:** Um dies zu aktivieren, muss die Anwendung ihren tiefen Puffer an das System übermitteln, wie dies für die Tiefe neuprojektion der Fall wäre.  Bei hololens 2 muss die Anwendung dann setfocuspoint mit einem Punkt von 0 (null) für jeden Frame festlegen.  Bei hololens Generation 1 sollte die Anwendung setfocuspoint nicht aufrufen.

### <a name="choosing-reprojection-technique"></a>Auswählen der Methode zum erneuten Projektion

Stabilisierungstyp |    Immersive Headsets |    Hololens Generation 1 | HoloLens 2
--- | --- | --- | ---
Tiefen neuprojektion |    Empfohlen |   N/V |   Empfohlen<br/><br/>Unity-Anwendungen müssen Unity 2018.4.12 oder höher oder Unity 2019,3 oder höher verwenden. Verwenden Sie andernfalls die automatische planare neuprojektion.
Automatische planare neuprojektion | N/V |   Empfohlene Standardeinstellung |   Empfohlen, wenn die tiefen neuprojektion nicht die besten Ergebnisse liefert<br/><br/>Unity-Anwendungen werden für die Verwendung von Unity 2018.4.12 oder höher oder Unity 2019,3 oder höher empfohlen.  Frühere Unity-Versionen funktionieren mit leicht herabgestuften reprojektions Ergebnissen.
Planare neuprojektion |   Nicht empfohlen |   Empfohlen, wenn die automatische Planar nicht die besten Ergebnisse liefert | Verwenden Sie, wenn keine der tiefen Optionen gewünschte Ergebnisse liefert.    

### <a name="verifying-depth-is-set-correctly"></a>Überprüfen der Tiefe Festlegung der Tiefe
            
Wenn eine reprojection-Methode den tiefen Puffer verwendet, muss überprüft werden, ob der Inhalt des tiefen Puffers die gerenderte Szene der Anwendung darstellt.  Eine Reihe von Faktoren kann Probleme verursachen. Wenn z. b. eine zweite Kamera zum renderingüber Lagerungen der Benutzeroberfläche verwendet wird, werden wahrscheinlich alle detaillierten Informationen aus der eigentlichen Ansicht überschrieben.  Transparente Objekte legen oft keine Tiefe fest.  Beim Text Rendering wird standardmäßig keine Tiefe festgelegt.  Im Rendering werden sichtbare Fehler angezeigt, wenn die Tiefe nicht den gerenderten holograms entspricht.
            
Hololens 2 verfügt über eine Schnellansicht, die anzeigt, wo die Tiefe festgelegt ist und nicht festgelegt wird, die über das Geräte Portal aktiviert werden kann.  Wählen Sie auf der Registerkarte **Ansichten**  >  **Hologram-Stabilität** das Kontrollkästchen **Tiefe Visualisierung in Headset anzeigen aus** .  Bereiche, die eine Tiefe festgelegt haben, werden blau dargestellt.  Gerenderte Elemente, die keine tiefen Menge aufweisen, sind rot markiert und müssen korrigiert werden.  

> [!NOTE]
> Die Visualisierung der Tiefe wird bei der Erfassung gemischter Realität nicht angezeigt.  Er ist nur über das Gerät sichtbar.
            
Einige GPU-Anzeige Tools ermöglichen die Visualisierung des tiefen Puffers.  Anwendungsentwickler können diese Tools verwenden, um sicherzustellen, dass die Tiefe ordnungsgemäß festgelegt wird.  Weitere Informationen finden Sie in der Dokumentation zu den Tools der Anwendung.

### <a name="using-planar-reprojection"></a>Verwenden der planaren neuprojektion
> [!NOTE]
> Bei desktopsiven Desktops ist das Festlegen einer Stabilisierungs Ebene in der Regel kontraproduktiv, da Sie weniger visuelle Qualität bietet, als die Tiefe des App-tiefen Puffers für das System bereitzustellen, um eine pro-Pixel-Tiefe basierende neuprojektion zu ermöglichen. Wenn Sie nicht auf einem hololens ausgeführt werden, sollten Sie im Allgemeinen vermeiden, die Stabilisierungs Ebene festzulegen.

![Stabilisierungs Ebene für 3D-Objekte](images/stab-plane-500px.jpg)

Das Gerät versucht automatisch, diese Ebene auszuwählen, aber die Anwendung sollte dabei helfen, den Fokuspunkt in der Szene auszuwählen. Unity-apps, die auf einem hololens ausgeführt werden, sollten den besten Fokuspunkt auf der Grundlage Ihrer Szene auswählen und an [setfocuspoint ()](focus-point-in-unity.md)übergeben. Ein Beispiel für das Festlegen des Fokus Punkts in DirectX ist in der standardmäßigen drehenden Cube-Vorlage enthalten.

Unity sendet ihren tiefen Puffer an Windows, um die neuprojektion pro Pixel zu aktivieren, wenn Sie Ihre APP auf einem immersiven Headset ausführen, das mit einem Desktop-PC verbunden ist, was eine noch bessere Bildqualität bietet, ohne dass die APP explizit funktioniert. Sie sollten nur dann einen Fokuspunkt angeben, wenn die APP auf einem hololens ausgeführt wird oder die pro-Pixel-neuprojektion überschrieben wird.


```cs
// SetFocusPoint informs the system about a specific point in your scene to
// prioritize for image stabilization. The focus point is set independently
// for each holographic camera.
// You should set the focus point near the content that the user is looking at.
// In this example, we put the focus point at the center of the sample hologram,
// since that is the only hologram available for the user to focus on.
// You can also set the relative velocity and facing of that content; the sample
// hologram is at a fixed point so we only need to indicate its position.
renderingParameters.SetFocusPoint(
    currentCoordinateSystem,
    spinningCubeRenderer.Position
    );
```

Die Platzierung des Fokus Punkts hängt größtenteils davon ab, worum es sich beim – Hologramm handelt. Die APP verfügt über den Reflektionsvektor zur Referenz, und der APP-Designer weiß, welche Inhalte der Benutzer beobachten soll.

Das wichtigste, was ein Entwickler zum stabilisieren von holograms tun kann, ist das Rendering bei 60 fps. Wenn Sie unter 60 fps ablegen, wird die – Hologramm-Stabilität erheblich reduziert, was die Stabilisierung der Stabilisierungs Ebene angeht.

**Bewährte Methoden** Es gibt keine universelle Methode zum Einrichten der Stabilisierungs Ebene und ihrer App-spezifischen. Unsere Hauptempfehlung besteht darin, zu experimentieren und zu sehen, was für Ihr Szenario am besten geeignet ist. Versuchen Sie jedoch, die Stabilisierungs Ebene mit so vielen Inhalten wie möglich auszurichten, da der gesamte Inhalt auf dieser Ebene vollständig stabilisiert ist.

Beispiel:
* Wenn Sie nur planare Inhalte haben (Lesen der APP, Videowiedergabe-APP), richten Sie die Stabilisierungs Ebene mit der Ebene aus, die ihren Inhalt enthält.
* Wenn es drei kleine Bereiche gibt, die weltweit gesperrt sind, nehmen Sie die Stabilisierungs Ebene in den Mittelpunkt aller Bereiche, die sich derzeit in der Ansicht des Benutzers befinden.
* Wenn Ihre Szene Inhalte in deutlich unterschiedlichen Tiefen hat, bevorzugen Sie weitere Objekte.
* Stellen Sie sicher, dass Sie den Stabilisierungs Punkt an jedem Frame anpassen, damit er mit dem – Hologramm übereinstimmt, das der Benutzer prüft.

**Zu vermeide Dinge** Die Stabilisierungs Ebene ist ein großartiges Tool zum erreichen stabiler Hologramme, aber wenn Sie missbraucht wird, kann dies zu schwerwiegenden Bild Instabilität führen.
* Nicht "Feuer und vergessen". Sie können am Ende der Stabilisierungs Ebene hinter dem Benutzer oder an ein Objekt angefügt werden, das sich nicht mehr in der Ansicht des Benutzers befindet. Stellen Sie sicher, dass die Stabilisierungs Ebene normal gegen Kamera-vorwärts festgelegt ist (z. b.-Camera. Forward).
* Ändern Sie die Stabilisierungs Ebene nicht schnell zwischen den extremen
* Belassen Sie die Stabilisierungs Ebene nicht auf eine festgelegte Distanz/Ausrichtung.
* Nicht zulassen, dass die Stabilisierungs Ebene den Benutzer ausschneidet
* Legen Sie den Schwerpunkt Punkt nicht fest, wenn Sie auf einem Desktop-PC statt auf einem hololens ausgeführt werden, und verwenden Sie stattdessen die Tiefe pro Pixel-neuprojektion.

## <a name="color-separation"></a>Farbtrennung 

Aufgrund der Art der hololens-Anzeige kann ein Element mit dem Namen "Farbtrennung" manchmal wahrgenommen werden. Es manifestiert sich als das Bild, das in einzelne Basis Farben aufgeteilt ist (rot, grün und blau). Das Element kann vor allem sichtbar sein, wenn Sie weiße Objekte anzeigen, da Sie große Mengen von rot, grün und blau aufweisen. Es ist am deutlichsten, wenn ein Benutzer ein Hologramm visuell verfolgt, das mit hoher Geschwindigkeit über den Holographic-Frame bewegt wird. Eine andere Möglichkeit des Artefakts ist das Durchlaufen von Objekten. Wenn ein Objekt einen hohen Kontrast und/oder reine Farben (z. b. rot, grün, blau) aufweist, wird die Farbtrennung als aufwärtuping verschiedener Teile des Objekts wahrgenommen.

**Beispiel dafür, wie die Farbtrennung eines gesperrenden weißen runden Cursors aussehen könnte, wenn ein Benutzer seine Kopfzeile auf die Seite dreht:**

![Beispiel dafür, wie die Farbtrennung eines gesperrenden weißen runden Cursors aussehen könnte, wenn ein Benutzer seine Kopfzeile auf die Seite dreht.](images/colorseparationofroundwhitecursor-300px.png)

Obwohl es schwierig ist, die Trennung von Farben vollständig zu vermeiden, stehen mehrere Verfahren zur Verfügung, um das Problem zu verringern.

**Die Farbtrennung finden Sie unter:**
* -Objekte, die schnell verschoben werden, einschließlich der von einem Kopf gesperrten Objekte, z. b. des [Cursors](cursors.md).
* Objekte, die sich weitgehend von der [Stabilisierungs Ebene](hologram-stability.md#reprojection)unterliegen.

**So mildern Sie die Auswirkungen der Farbtrennung:**
* Sorgen Sie dafür, dass das Objekt den Benutzer Blick verzögert. Es sollte so aussehen, als ob es etwas Trägheit hat und an den Blick "on Springs" angefügt ist. Durch diese Vorgehensweise wird der Cursor verlangsamt (die Entfernung wird reduziert) und hinter dem wahrscheinlichen Blickpunkt des Benutzers abgelegt. Solange der Benutzer die Verschiebung seines Blicks nicht stoppt, ist es so lange sehr leicht.
* Wenn Sie ein Hologramm verschieben möchten, sollten Sie versuchen, die Verschiebungs Geschwindigkeit unter 5 Grad/Sekunde beizubehalten, wenn Sie davon ausgehen, dass der Benutzer das Ergebnis mit den Augen hat.
* Verwenden Sie *Light* anstelle von *Geometry* für den Cursor. Eine Quelle der virtuellen Beleuchtung, die an den Blick angefügt ist, wird als interaktiver Zeiger wahrgenommen, führt jedoch nicht zu einer Farbtrennung.
* Passen Sie die Stabilisierungs Ebene so an, dass Sie mit den Hologrammen identisch ist, bei denen der Benutzer die Benutzer
* Legen Sie das-Objekt rot, grün oder blau.
* Wechseln Sie zu einer unscharfen Version des Inhalts. Beispielsweise könnte ein runder weißer Cursor in eine leicht verschwommene Linie geändert werden, die in der Bewegungsrichtung ausgerichtet ist.

Wie zuvor sind das Rendering bei 60 fps und das Festlegen der Stabilisierungs Ebene die wichtigsten Techniken für die – Hologramm-Stabilität. Stellen Sie zunächst sicher, dass die Framerate den Erwartungen entspricht, wenn Sie mit einer merkbaren Farbtrennung

## <a name="see-also"></a>Siehe auch
* [Grundlegendes zur Leistung für gemischte Realität](understanding-performance-for-mixed-reality.md)
* [Farbe, Licht und Materialien](color,-light-and-materials.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Mrtk Hologram-Stabilisierung](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html)
