---
title: Hologram-Stabilität
description: Hololens stabilisiert holograms automatisch, aber es gibt Schritte, die Entwickler durchführen können, um die hologrammstabilität weiter zu verbessern.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: holograms, Stabilität, hololens
ms.openlocfilehash: b299df42bf02b837cb45faf5acb7a11b61f2e587
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435070"
---
# <a name="hologram-stability"></a>Hologram-Stabilität

Zum erreichen stabiler Hologramme verfügt hololens über eine integrierte Pipeline zur Bildstabilisierung. Die Stabilisierungs Pipeline funktioniert automatisch im Hintergrund, sodass keine zusätzlichen Schritte erforderlich sind, um Sie zu aktivieren. Entwickler sollten jedoch Techniken anwenden, die die Stabilität des Hologramms verbessern und Szenarios vermeiden, die die Stabilität verringern.

## <a name="hologram-quality-terminology"></a>Hologram Quality-Terminologie

Die Qualität von holograms ist das Ergebnis einer guten Umgebung und einer guten App-Entwicklung. Apps, die in einer Umgebung, in der hololens die Umgebung nachverfolgen können, eine Konstante 60 Frames pro Sekunde erreichen, stellen sicher, dass das Hologramm und das passende Koordinatensystem synchronisiert sind. Aus Sicht eines Benutzers werden holograms, die stationär sein sollen, nicht relativ zur Umgebung verschoben.

Wenn Umgebungs Probleme, inkonsistente oder niedrige renderingraten oder andere APP-Probleme angezeigt werden, ist die folgende Terminologie hilfreich, um das Problem zu identifizieren.
* **Genau.** Sobald das – Hologramm weltweit gesperrt und in der realen Welt platziert wurde, sollte es sich an der Stelle befinden, an der es platziert wurde, relativ zur umgebenden Umgebung, unabhängig von der Benutzer Bewegung oder kleinen und geringfügigen Umgebungs Änderungen. Wenn ein – Hologramm später an einem unerwarteten Speicherort angezeigt wird, ist dies ein *Genauigkeits* Problem. Solche Szenarien können eintreten, wenn zwei unterschiedliche Räume identisch aussehen.
* **Jitter.** Benutzer beobachten dies als hohes Frequenz schütteln eines holograms. Dies kann vorkommen, wenn die Nachverfolgung der Umgebung beeinträchtigt wird. Für Benutzer wird die [Sensor](sensor-tuning.md)Optimierung von der Lösung ausgeführt.
* **Der Judder.** Niedrige renderingfrequenzen führen zu ungleichen Bewegungs-und doppelten Bildern von holograms. Dies ist besonders in holograms mit Motion spürbar. Entwickler müssen eine [Konstante 60 fps](hologram-stability.md#frame-rate)beibehalten.
* **Inter.** Benutzer sehen, dass das – Hologramm anscheinend von der Stelle entfernt wird, an der Sie ursprünglich platziert wurde. Dies geschieht, wenn holograms von [räumlichen Ankern](spatial-anchors.md)fern platziert werden, insbesondere in Teilen der Umgebung, die nicht vollständig zugeordnet wurden. Das Erstellen von holograms in der Nähe räumlicher Anker verringert die Wahrscheinlichkeit einer Abweichung.
* **Schnell Einstieg.** Wenn ein – Hologramm-"Pops" oder "springt" von seiner Position gelegentlich Weg ist. Dies kann auftreten, wenn die Nachverfolgung holograms anpasst, um das aktualisierte Verständnis Ihrer Umgebung abzugleichen.
* **MME.** Wenn ein – Hologramm zu bewegen scheint, das der Bewegung des Benutzer Kopfes entspricht. Dies tritt auf, wenn die Anwendung die [neuprojektion](hologram-stability.md#reprojection)nicht vollständig implementiert hat und die hololens nicht für den aktuellen Benutzer [kalibriert](calibration.md) sind. Der Benutzer kann die [Kalibrierungs](calibration.md) Anwendung erneut ausführen, um dieses Problem zu beheben. Entwickler können die Stabilisierungs Ebene aktualisieren, um die Stabilität zu verbessern.
* **Farbtrennung.** Die Anzeige in hololens ist eine Farb sequenzielle Anzeige, bei der die Farbe der roten grün-grün-blau-grün bei 60Hz angezeigt wird (einzelne Farbfelder werden bei 240 Hz angezeigt). Jedes Mal, wenn ein Benutzer ein bewegendes – Hologramm mit seinen Augen verfolgt, werden die führenden und nachfolgenden Kanten des holograms in den einzelnen Farben getrennt und erzeugen einen Regenbogeneffekt. Der Grad der Trennung hängt von der Geschwindigkeit des holograms ab. In einigen seltenen Fällen kann es auch zu einem Regenbogeneffekt kommen, wenn Sie sich bei der Betrachtung eines stationären holograms schnell bewegen. Dies wird als *[Farbtrennung](hologram-stability.md#color-separation)* bezeichnet.

## <a name="frame-rate"></a>Bildfrequenz

Die Framerate ist die erste Säule der – Hologramm-Stabilität. Damit holograms weltweit stabil angezeigt werden, muss für jedes Bild, das dem Benutzer präsentiert wird, das holograms an der richtigen Stelle gezeichnet werden. Die Anzeige auf hololens wird 240 mal pro Sekunde aktualisiert, wobei vier separate Farbfelder für jedes neu gerenderte Bild angezeigt werden, was zu einer Benutzer Darstellung von 60 fps (Frames pro Sekunde) führt. Um die bestmögliche Leistung zu gewährleisten, müssen Anwendungsentwickler 60 FPS verwalten. Dies bedeutet, dass alle 16 Millisekunden stets ein neues Image für das Betriebssystem bereitgestellt wird.

**60 fps** Um holograms so zu zeichnen, dass Sie sich in der realen Welt befinden, müssen hololens Bilder aus der Position des Benutzers Rendering. Da das Rendern von Bildern Zeit erfordert, prognostizieren hololens, wo sich der Benutzer befindet, wenn die Bilder in den anzeigen angezeigt werden. Dieser Vorhersagealgorithmus ist eine Näherung. Hololens verfügt über Hardware, die das gerenderte Bild anpasst, um die Diskrepanz zwischen der vorhergesagten Kopfzeile und der tatsächlichen Head-Position zu berücksichtigen. Dadurch wird das Bild, das dem Benutzer angezeigt wird, so angezeigt, als wäre es vom richtigen Speicherort gerendert worden, und holograms fühlen sich stabil. Die Image Aktualisierungen funktionieren am besten mit kleinen Änderungen und können bestimmte Dinge im gerenderten Image wie Motion-Parser nicht vollständig beheben.

Durch Rendering bei 60 fps führen Sie drei Dinge aus, um stabile Hologramme zu erstellen:
1. Minimierung der Gesamt Latenz zwischen dem Rendern eines Bilds und dem Bild, das für den Benutzer sichtbar ist. In einer Engine mit einem Spiel Thread und einem Renderthread, der in Lockstep ausgeführt wird, kann die Ausführung mit 30fps eine zusätzliche Wartezeit von 33,3 MS addieren. Durch die Reduzierung der Latenzzeit wird der Vorhersagefehler verringert, und die hologrammstabilität wird erhöht.
2. Dadurch wird für jedes Bild, das die Augen des Benutzers erreicht, eine konsistente Latenzzeit erzielt. Wenn Sie bei 30fps Rendering, zeigt die Anzeige weiterhin Bilder bei 60 fps an. Dies bedeutet, dass dasselbe Bild zweimal in einer Zeile angezeigt wird. Der zweite Frame weist eine höhere Latenz von 16,6 ms als der erste Frame auf und muss eine deutlichere Menge an Fehlern beheben. Diese Inkonsistenz in der Fehler Größe kann zu unerwünschten 60Hz-Judder führen.
3. Die Darstellung des Judder wird verringert, was durch ungleichmäßige Bewegung und doppelte Bilder gekennzeichnet ist. Eine schnellere – Hologramm-Bewegung und niedrigere Rendering-Raten sind mit deutlicheren Judder verknüpft. Daher wird die Verwendung von 60 fps zu allen Zeitpunkten helfen, den Judder für ein bestimmtes bewegliches Hologram zu vermeiden.

**Konsistenz der Frame Rate** Die Konsistenz der Framerate ist so wichtig wie ein hoher Rahmen pro Sekunde. Gelegentlich gelöschte Frames sind für jede Content-Rich-Anwendung unvermeidlich, und der hololens implementiert einige ausgereifte Algorithmen, um gelegentlich auftretende Fehler zu beheben. Ein ständig schwankender Framerate ist für einen Benutzer jedoch deutlich deutlicher als bei einer konsistenten Ausführung mit niedrigeren Frameraten. Beispielsweise wird eine Anwendung, die für 5 Frames reibungslos rendert (60 fps für die Dauer dieser 5 Frames) und dann jeden anderen Frame für die nächsten 10 Frames (30 fps für die Dauer dieser 10 Frames) als eine Anwendung, die konsistent wird bei 30 fps gerendert.

Bei einem verwandten Hinweis drosselt das Betriebssystem Anwendungen auf bis zu 30 fps, wenn die [gemischte Reality-Erfassung](mixed-reality-capture.md) ausgeführt wird.

**Leistungsanalyse** Es gibt eine Reihe von Tools, die verwendet werden können, um die Anwendungs Frame Rate zu messen, wie z. b.:
* GPUView
* Visual Studio-Grafik Debugger
* Profiler, die in 3D-Engines wie Unity integriert sind

## <a name="hologram-render-distances"></a>Hologram-Rendering-Entfernungen

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

Das menschliche visuelle System integriert mehrere entfernungsabhängige Signale, wenn es ein Objekt korrigiert und fokussiert.
* [Unterkunft](https://en.wikipedia.org/wiki/Accommodation_%28eye%29) : der Schwerpunkt eines einzelnen Auges.
* [Konvergenz](https://en.wikipedia.org/wiki/Convergence_(eye)) : zwei Augen werden nach innen oder nach außen verschoben, um auf ein Objekt zu zentrieren.
* [Binbichtbild](https://en.wikipedia.org/wiki/Stereopsis) : Unterschiede zwischen der linken und der rechten Seite, die von der Entfernung eines Objekts von Ihrem Fixpunkt abhängen.
* Schattierung, relative Angular-Größe und andere monokuläre Cues (Single Eye).

Konvergenz und Unternehmen sind eindeutig, da es sich um zusätzliche Netzhaut Hinweise handelt, die sich darauf beziehen, wie sich die Augen ändern, um Objekte in unterschiedlichen Abständen zu erkennen In natürlicher Ansicht sind Konvergenz und Unterbringung verknüpft. Wenn die Augen etwas in der Nähe (z. b. ihre Nase) angezeigt werden, überschreiten die Augen die Augen und können zu einem nahe Punkt Wenn die Augen etwas unendlich sehen, werden die Augen parallel angezeigt, und das Auge ist unendlich. Benutzer, die hololens durchführen, unterstützen immer 2.0 m, um ein klares Bild zu erhalten, da die hololens-Anzeige in einer optischen Entfernung von ungefähr 2,0 m vom Benutzer entfernt wird. App-Entwickler steuern, wohin die Augen der Benutzer konvergiert werden, indem Sie Inhalte und Hologramme in verschiedenen Tiefen platzieren. Wenn Benutzer unterschiedliche Entfernungen aufnehmen und mit Ihnen zusammenführen, ist die natürliche Verknüpfung zwischen den beiden hinweisen beschädigt, und dies kann zu einem visuellen Unbehagen oder Müdigkeit führen, insbesondere wenn die Größe des Konflikts sehr groß ist. Die Unannehmlichkeiten aus dem Vergence--Unterbringungs Konflikt können vermieden oder minimiert werden, indem Inhalte, die von Benutzern konvergiert werden, so nah wie möglich an 2.0 m aufbewahrt werden (d.h. in einer Szene mit vielen tiefen, wenn möglich, die relevanten Bereiche in der Nähe von 2.0 m). Wenn Inhalt nicht in der Nähe von 2.0 m-Unbehagen aus dem Vergence--Unterbringungs Konflikt platziert werden kann, ist es am größten, wenn der Benutzer sich zwischen verschiedenen Entfernungen hin-und her Anders ausgedrückt: Es ist viel besser, sich ein stationäres – Hologramm anzusehen, das 50 cm entfernt wird, als ein – Hologramm 50cm zu betrachten, das sich im Laufe der Zeit von Ihnen hin und her bewegt.

Das Platzieren von Inhalten auf 2.0 m ist ebenfalls vorteilhaft, da die beiden anzeigen so konzipiert sind, dass Sie sich in dieser Entfernung vollständig überlappen Bei Bildern, die auf dieser Ebene abgelegt werden, werden Sie bei der Verschiebung von der Seite des Holographic Frame aus einer Anzeige verschwinden, während Sie auf der anderen angezeigt werden. Diese binare Rivalität kann die Tiefe Wahrnehmung des holograms stören.

**Optimale Entfernung zum Platzieren von holograms vom Benutzer**

![Optimale Entfernung zum Platzieren von holograms vom Benutzer](images/distanceguiderendering-750px.png)

**Clip Flächen** Für einen maximalen Komfort empfiehlt es sich, den Ausschneide-renderabstand bei 85 cm mit dem faout-Inhalt beginnend bei 1 Mio. zu verringern. In Anwendungen, in denen holograms und Benutzer beide stationär sind, können Sie bequem so nah wie 50 cm angezeigt werden. In diesen Fällen sollten Anwendungen eine Ausschneide Ebene nicht oberhalb von 30cm platzieren, und das ausblenden sollte mindestens 10 cm von der Ausschneide Ebene ausgehen. Wenn Inhalt größer als 85 cm ist, muss sichergestellt werden, dass die Benutzer nicht häufig von holograms näher oder weiter gehen oder dass holograms nicht häufig in den Benutzer gelangen, da diese Situationen am wahrscheinlichsten von der Vergence-Unterbringungs Konflikt. Der Inhalt sollte so entworfen werden, dass er die Notwendigkeit einer Interaktion mit einem Wert von 85 cm vom Benutzer minimiert, aber wenn Inhalt vor dem 85 cm gerendert werden muss, ist es sinnvoll, Szenarios zu entwerfen, in denen Benutzer und/oder holograms nicht mehr als 25% von t verschieben. Uhrzeit.

**Bewährte Methoden** Wenn holograms bei 2 m nicht platziert werden können und Konflikte zwischen Konvergenz und Unterbringung nicht vermieden werden können, liegt die optimale Zone für die – Hologramm-Platzierung zwischen 1,25 m und 5 m. In jedem Fall sollten Designer Inhalte strukturieren, um Benutzern die Interaktion von 1 + m zu empfehlen (z. b. Anpassen von Inhalts Größe und Standard Platzierungs Parametern).

## <a name="reprojection"></a>Neuprojektion
Hololens führt eine ausgereifte Hardware gestützte Holographic-Stabilisierungstechnik aus, die als neuprojektion bezeichnet wird. Dies berücksichtigt die Bewegung und Änderung der Perspektive (camerapose), wenn die Szene animiert und der Benutzer den Kopf bewegt.  Anwendungen müssen bestimmte Aktionen ausführen, um die neuprojektion am besten zu verwenden.


Es gibt vier Haupttypen der neuprojektion.
* **Tiefen neuprojektion:**  Dies führt zu den besten Ergebnissen mit dem geringsten Aufwand aus der Anwendung.  Alle Teile der gerenderten Szene werden abhängig von ihrer Entfernung zum Benutzer unabhängig voneinander stabilisiert.  Einige Renderingartefakte sind möglicherweise sichtbar, wenn eine Tiefe Tiefe von Änderungen vorliegt.  Diese Option ist nur für hololens 2 und immersive Headsets verfügbar.
* **Planare neuprojektion:**  Dies ermöglicht der Anwendung die genaue Steuerung der Stabilisierung.  Eine Ebene wird von der Anwendung festgelegt, und alles auf dieser Ebene ist der stabilste Teil der Szene.  Wenn ein – Hologramm von der Ebene entfernt wird, desto weniger stabil ist es.  Diese Option ist auf allen Windows-Windows-Plattformen verfügbar.
* **Automatische planare neuprojektion:**  Das System legt mithilfe der Informationen im tiefen Puffer eine Stabilisierungs Ebene fest.  Diese Option ist auf hololens-Generation 1 und hololens 2 verfügbar.
* **Keine:** Wenn die Anwendung keine Aktion ausführt, wird die planare neuprojektion mit der auf zwei Metern gesetzten Stabilisierungs Ebene in der Richtung des Haupt Anblicks des Benutzers verwendet.  Dies führt in der Regel zu untergeordneten Ergebnissen.

Anwendungen müssen bestimmte Aktionen durchführen, um die verschiedenen Arten der neuprojektion zu aktivieren.
* **Tiefen neuprojektion:** Die Anwendung übermittelt ihren tiefen Puffer für jeden gerenderten Frame an das System.  Bei Unity erfolgt dies mit der Option "Tiefe Puffer Freigabe aktivieren" im Bereich "Player Einstellungen".  DirectX-apps CommitDirect3D11DepthBuffer-Aufrufe.  Die Anwendung sollte setfocuspoint nicht aufrufen.
* **Planare neuprojektion:** Bei jedem Frame teilen Anwendungen dem System den Speicherort einer zu stabilisierende Ebene mit.  Unity-Anwendungen können setfocuspointforframe aufrufen und müssen die Option "Tiefe Puffer Freigabe aktivieren" deaktiviert haben.  DirectX-apps aufrufen setfocuspoint und sollten CommitDirect3D11DepthBuffer nicht aufrufen.
* **Automatische planare neuprojektion:** Um dies zu ermöglichen, muss die Anwendung ihren tiefen Puffer an das System übermitteln, wie dies bei der tiefen neuprojektion der Fall wäre.  Bei hololens 2 muss die Anwendung dann setfocuspoint mit einem Punkt von 0 (null) für jeden Frame festlegen.  Bei hololens Generation 1 sollte die Anwendung setfocuspoint nicht aufrufen.

### <a name="choosing-reprojection-technique"></a>Auswählen der Methode zum erneuten Projektion

Stabilisierungstyp |    Immersive Headsets |    Hololens Generation 1 | HoloLens 2
--- | --- | --- | ---
Tiefen neuprojektion |    Empfohlen |   n. v. |   Empfohlen<br/><br/>Unity-Anwendungen müssen Unity 2018.4.12 oder höher oder Unity 2019,3 oder höher verwenden. Verwenden Sie andernfalls die automatische planare neuprojektion.
Automatische planare neuprojektion | n. v. |   Empfohlene Standardeinstellung |   Empfohlen, wenn die tiefen neuprojektion nicht die besten Ergebnisse liefert.<br/><br/>Unity-Anwendungen werden für die Verwendung von Unity 2018.4.12 oder höher oder Unity 2019,3 oder höher empfohlen.  Frühere Unity-Versionen funktionieren mit leicht herabgestuften reprojektions Ergebnissen.
Planare neuprojektion |   Nicht empfohlen |   Empfohlen, wenn die automatische Planar nicht die besten Ergebnisse liefert |    Verwenden Sie, wenn keine der tiefen Optionen gewünschte Ergebnisse liefert.    

### <a name="verifying-depth-is-set-correctly"></a>Überprüfen der Tiefe Festlegung der Tiefe
            
Wenn eine reprojection-Methode den tiefen Puffer verwendet, muss sichergestellt werden, dass der Inhalt des tiefen Puffers die gerenderte Szene der Anwendung darstellt.  Eine Reihe von Faktoren kann Probleme verursachen.  Wenn eine zweite Kamera zum Renderingvorgang verwendet wird, beispielsweise Überlagerungen der Benutzeroberfläche, werden wahrscheinlich alle detaillierten Informationen aus der tatsächlichen Ansicht überschrieben.  Transparente Objekte legen oft keine Tiefe fest.  Bei einigen Text Rendering wird standardmäßig keine Tiefe festgelegt.  Im Rendering werden sichtbare Fehler angezeigt, wenn die Tiefe nicht den gerenderten holograms entspricht.
            
Hololens 2 verfügt über eine Schnellansicht, die anzeigt, wo die Tiefe ist und nicht festgelegt wird.  Aktivieren Sie diese Option über das Geräte Portal.  Wählen Sie auf der Registerkarte **Ansichten** > **Hologram-Stabilität** das Kontrollkästchen **Tiefe Visualisierung in Headset anzeigen aus** .  Bereiche, die eine Tiefe festgelegt haben, werden blau dargestellt.  Gerenderte Dinge, die keine tiefen Menge aufweisen, sind rot und müssen daher behoben werden.  Beachten Sie, dass die Visualisierung der Tiefe bei der Erfassung gemischter Realität nicht angezeigt wird.  Er ist nur über das Gerät sichtbar.
            
Einige GPU-Anzeige Tools ermöglichen die Visualisierung des tiefen Puffers.  Anwendungsentwickler können diese Tools verwenden, um sicherzustellen, dass die Tiefe ordnungsgemäß festgelegt wird.  Weitere Informationen finden Sie in der Dokumentation zu den Tools der Anwendung.

### <a name="using-planar-reprojection"></a>Verwenden der planaren neuprojektion
> [!NOTE]
> Bei desktopsiven Desktops ist das Festlegen einer Stabilisierungs Ebene in der Regel kontraproduktiv, da Sie weniger visuelle Qualität bietet, als die Tiefe des App-tiefen Puffers für das System bereitzustellen, um eine pro-Pixel-Tiefe basierende neuprojektion zu ermöglichen. Wenn Sie nicht auf einem hololens ausgeführt werden, sollten Sie im Allgemeinen vermeiden, die Stabilisierungs Ebene festzulegen.

![Stabilisierungs Ebene für 3D-Objekte](images/stab-plane-500px.jpg)

Das Gerät versucht automatisch, diese Ebene auszuwählen, aber die Anwendung sollte bei diesem Vorgang helfen, indem der Fokuspunkt in der Szene ausgewählt wird. Unity-apps, die auf einem hololens ausgeführt werden, sollten den besten Punkt auswählen, der auf Ihrer Szene basiert, und diesen an [setfocuspoint ()](focus-point-in-unity.md)übergeben. Ein Beispiel für das Festlegen des Fokus Punkts in DirectX ist in der standardmäßigen drehenden Cube-Vorlage enthalten.

Beachten Sie Folgendes: Wenn Ihre Unity-App auf einem immersiven Headset ausgeführt wird, das mit einem Desktop-PC verbunden ist, sendet Unity ihren tiefen Puffer an Windows, um die neuprojektion pro Pixel zu aktivieren, was in der Regel eine noch bessere Bildqualität ohne explizite Arbeit durch die APP bereitstellt. Wenn Sie einen Schwerpunkt Punkt angeben, wird die neuprojektion pro Pixel überschrieben. Sie sollten dies nur tun, wenn Ihre APP in einem hololens ausgeführt wird.




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

Die Platzierung des Fokus Punkts hängt größtenteils vom – Hologramm ab, das Sie prüft. Die APP verfügt über den Reflektionsvektor zur Referenz, und der APP-Designer weiß, welche Inhalte der Benutzer beobachten soll.

Das wichtigste, was ein Entwickler zum stabilisieren von holograms tun kann, ist das Rendering bei 60 fps. Wenn Sie unter 60 fps ablegen, wird die – Hologramm-Stabilität erheblich reduziert, unabhängig von der Stabilisierung der Stabilisierungs Ebene.

**Bewährte Methoden** Es gibt keine universelle Methode zum Einrichten der Stabilisierungs Ebene, und Sie ist APP-spezifisch. Daher besteht die wichtigste Empfehlung darin, zu experimentieren und zu sehen, was für Ihre Szenarien am besten geeignet ist. Versuchen Sie jedoch, die Stabilisierungs Ebene mit so vielen Inhalten wie möglich auszurichten, da der gesamte Inhalt auf dieser Ebene vollständig stabilisiert ist.

Zum Beispiel:
* Wenn Sie nur planare Inhalte haben (Lesen der APP, Videowiedergabe-APP), richten Sie die Stabilisierungs Ebene mit der Ebene aus, die ihren Inhalt enthält.
* Wenn es drei kleine Bereiche gibt, die weltweit gesperrt sind, nehmen Sie die Stabilisierungs Ebene in den Mittelpunkt aller Bereiche, die sich derzeit in der Ansicht des Benutzers befinden.
* Wenn Ihre Szene Inhalte in deutlich unterschiedlichen Tiefen hat, bevorzugen Sie weitere Objekte.
* Stellen Sie sicher, dass Sie den Stabilisierungs Punkt an jedem Frame anpassen, damit er mit dem – Hologramm übereinstimmt, das der Benutzer prüft.

**Zu vermeide Dinge** Die Stabilisierungs Ebene ist ein großartiges Tool zum erreichen stabiler Hologramme, aber wenn Sie missbraucht wird, kann dies zu schwerwiegenden Bild Instabilität führen.
* Nicht "auslösen und vergessen", da Sie die Stabilisierungs Ebene hinter dem Benutzer oder an ein Objekt anhängen können, das sich nicht mehr in der Ansicht des Benutzers befindet. Stellen Sie sicher, dass die Stabilisierungs Ebene normal gegen Kamera-vorwärts (z. b. "Kamera. vorwärts") eingestellt ist.
* Ändern Sie die Stabilisierungs Ebene nicht schnell zwischen den extremen
* Belassen Sie die Stabilisierungs Ebene nicht auf eine festgelegte Distanz/Ausrichtung.
* Nicht zulassen, dass die Stabilisierungs Ebene den Benutzer ausschneidet
* Legen Sie den Schwerpunkt Punkt nicht fest, wenn Sie auf einem Desktop-PC statt auf einem hololens ausgeführt werden, und verwenden Sie stattdessen die Tiefe pro Pixel-neuprojektion.

## <a name="color-separation"></a>Farbtrennung 

Aufgrund der Art der hololens-Anzeige kann ein Element mit dem Namen "Farbtrennung" manchmal wahrgenommen werden. Es manifestiert sich als Bild, das in einzelne Basis Farben (rot, grün und blau) aufgeteilt ist. Das Element kann vor allem sichtbar sein, wenn Sie weiße Objekte anzeigen, da Sie große Mengen von rot, grün und blau aufweisen. Es ist am deutlichsten, wenn ein Benutzer ein – Hologramm visuell verfolgt, das mit hoher Geschwindigkeit über den Holographic-Frame bewegt wird. Eine andere Möglichkeit des Artefakts ist das Durchlaufen von Objekten. Wenn ein Objekt einen hohen Kontrast und/oder reine Farben (rot, grün, blau) aufweist, wird die Farbtrennung als aufwärtuping verschiedener Teile des Objekts wahrgenommen.

**Beispiel dafür, wie die Farbtrennung eines gesperrenden weißen runden Cursors aussehen könnte, wenn ein Benutzer seine Kopfzeile auf die Seite dreht:**

![Beispiel dafür, wie die Farbtrennung eines gesperrenden weißen runden Cursors aussehen könnte, wenn ein Benutzer seine Kopfzeile auf die Seite dreht.](images/colorseparationofroundwhitecursor-300px.png)

Obwohl es schwierig ist, die Trennung von Farben vollständig zu vermeiden, stehen mehrere Verfahren zur Verfügung, um das Problem zu verringern.

**Die Farbtrennung finden Sie unter:**
* -Objekte, die schnell verschoben werden, einschließlich der von einem Kopf gesperrten Objekte, z. b. des [Cursors](cursors.md).
* Objekte, die sich weitgehend von der [Stabilisierungs Ebene](hologram-stability.md#reprojection)unterliegen.

**So mildern Sie die Auswirkungen der Farbtrennung:**
* Sorgen Sie dafür, dass das Objekt den Benutzer Blick verzögert. Es sollte so aussehen, als ob es etwas Trägheit hat und an den Blick "on Springs" angefügt ist. Dadurch wird der Cursor verlangsamt (die Distanz wird reduziert), und er wird hinter dem wahrscheinlichen Blickpunkt des Benutzers abgelegt. Solange der Benutzer die Verschiebung seines Blicks nicht stoppt, ist es ganz natürlich.
* Wenn Sie ein Hologramm verschieben möchten, sollten Sie versuchen, die Verschiebungs Geschwindigkeit unter 5 Grad/Sekunde beizubehalten, wenn Sie davon ausgehen, dass der Benutzer ihm die Augen folgt.
* Verwenden Sie *Light* anstelle von *Geometry* für den Cursor. Eine Quelle der virtuellen Beleuchtung, die an den Blick angefügt ist, wird als interaktiver Zeiger wahrgenommen, bewirkt aber keine Farbtrennung.
* Passen Sie die Stabilisierungs Ebene so an, dass Sie mit den Hologrammen identisch ist, bei denen der Benutzer die Benutzer
* Legen Sie das-Objekt rot, grün oder blau.
* Wechseln Sie zu einer unscharfen Version des Inhalts. Beispielsweise könnte ein runder weißer Cursor in eine etwas verschwommene Linie geändert werden, die in der Bewegungsrichtung ausgerichtet ist.

Wie zuvor sind das Rendering bei 60 fps und das Festlegen der Stabilisierungs Ebene die wichtigsten Techniken für die – Hologramm-Stabilität. Stellen Sie zunächst sicher, dass die Framerate den Erwartungen entspricht, wenn Sie mit einer merkbaren Farbtrennung

## <a name="see-also"></a>Weitere Informationen:
* [Grundlegendes zur Leistung für gemischte Realität](understanding-performance-for-mixed-reality.md)
* [Farbe, Licht und Materialien](color,-light-and-materials.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Mrtk Hologram-Stabilisierung](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html)
