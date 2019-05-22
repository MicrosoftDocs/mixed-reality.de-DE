---
title: – Hologramm Stabilität
description: HoloLens stabilisiert automatisch Hologramme, aber es gibt Schritte, die Entwickler durchführen können, um die Stabilität der – Hologramm weiter zu verbessern.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Hologramme, Stabilität, hololens
ms.openlocfilehash: b35b904e3c662c5ebd0670a98044706fe208e348
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974936"
---
# <a name="hologram-stability"></a>– Hologramm Stabilität

Um stabile Hologramme zu erreichen, hat die HoloLens eine integriertes Bild Stabilisierung-Pipeline. Die Stabilisierung Pipeline erfolgt automatisch im Hintergrund, daher gibt es keine zusätzlichen Schritte erforderlich, um ihn zu aktivieren. Allerdings sollten Entwickler führen Sie die Techniken kennen, die – Hologramm Stabilität zu verbessern und Vermeiden von Szenarien, die Stabilität zu reduzieren.

## <a name="hologram-quality-terminology"></a>Die Qualität Terminologie – Hologramm

Die Qualität der Hologramme ist das Ergebnis der gute Umgebung und gute app-Entwicklung. Apps, die eine Konstante 60 Frames pro Sekunde in einer Umgebung, in denen HoloLens die Umgebung können Sie verfolgen, erreicht werden Stellen Sie sicher, dass die Hologramm und das entsprechende Koordinatensystem synchron sind. Aus Sicht eines Benutzers wechselt Hologramme, die nicht bewegt werden sollen nicht relativ zu der Umgebung.

Wenn Sie Probleme mit der Umgebung, inkonsistent oder niedriger-Rendering-Sätze oder andere Probleme bei der app angezeigt, die folgende Terminologie Identifizieren des Problems hilfreich sind.
* **Genauigkeit.** Nach der Hologramm World-gesperrt ist, und in der realen Welt platziert, sollte diese Einstellung beizubehalten, in dem sie, relativ zu der Umgebung unabhängig vom Benutzer während der Übertragung oder Änderungen in kleinen und mit geringer Dichte abgelegt wurde. Wenn Sie ggf. ein Hologramm später in eine unerwartete Position angezeigt wird, ist es ein *Genauigkeit* Problem. Solche Szenarien möglich, wenn zwei unterschiedliche Räume identisch aussehen.
* **Jitter.** Benutzer, die dies als hohe Auslastung von ggf. ein Hologramm Schütteln beobachten. Dies kann passieren, wenn die nachverfolgung der Umgebung beeinträchtigt wird. Für Benutzer, die Projektmappe ausgeführt wird [Sensor Optimierung](sensor-tuning.md).
* **Judder.** Niedrige Rendering Frequenzen führen ungleichmäßige während der Übertragung und doppelte Images Hologramme. Dies ist vor allem dann bemerkbar in Hologramme mit während der Übertragung. Entwickler müssen zum Verwalten einer [Konstanten 60 FPS](hologram-stability.md#frame-rate).
* **Abweichen.** Benutzer sehen diese wie – Hologramm angezeigt wird, um Abkehr von, in dem sie ursprünglich abgelegt wurde. Dies geschieht, wenn Hologramme von weit entfernt befinden [räumliche Anker](spatial-anchors.md), besonders in Teilen der Umgebung, die nicht vollständig zugeordnet wurden. Hologramme in der Nähe räumliche Anker erstellen, verringert die Wahrscheinlichkeit, dass abweichungen.
* **Jumpiness.** Wenn ein Hologramm "wird" oder "springt" Weg sie den Speicherort von Zeit zu Zeit. Dies kann auftreten, wie die nachverfolgung Hologramme aktualisierte Verständnis Ihrer Umgebung entsprechend angepasst wird.
* **Schwimmen.** Wenn angezeigt wird ggf. ein Hologramm, sway, die die Bewegung des Benutzers Head entspricht. Dieses Problem tritt bei Hologramme nicht auf sind die [Stabilisierung Ebene](hologram-stability.md#stabilization-plane), und wenn die HoloLens nicht [kalibriert](calibration.md) für den aktuellen Benutzer. Benutzer kann erneut ausführen, die [Kalibrierung](calibration.md) Anwendung für dieses Problem zu beheben. Entwickler können die Ebene der Stabilisierung zur weiteren Verbesserung der Stabilität aktualisieren.
* **Farbliche Trennung.** Die Anzeige in HoloLens sind einer sequenziellen Anzeige der Farbe, die flash der Rot-Grün-Blau-Grün-Kanal bei 60Hz (einzelne Farbe, die Felder an 240 Hz angezeigt werden). Wenn ein Benutzer einen gleitenden Hologramm mit seinem Augen nachverfolgt, trennen Sie in ihren zugehörigen Farben, erzeugen einen Effekt Rainbow, Hologramm die führenden und nachgestellten Rand an. Das Maß an Trennung ist abhängig von der Geschwindigkeit des Hologramm. In einigen seltenen Fällen Verschieben von Anwendungen in einen Effekt Rainbow Head schnell beim Blick auf ein stationär Hologramm führen kann. Dies wird als bezeichnet  *[Farbe Trennung](hologram-stability.md#color-separation)*.

## <a name="frame-rate"></a>Bildfrequenz

Framerate ist die erste Säule des – Hologramm Stabilität. Für Hologramme stabile in der ganzen Welt angezeigt werden müssen jedes Image, das dem Benutzer angezeigten der Hologramme in der richtigen Stelle gezeichnet. Zeigt die HoloLens aktualisieren 240 Mal pro Sekunde, mit vier separate Farbe Felder jeweils neu gerendert Image, was zu einer Verwendung von 60 FPS (Frames pro Sekunde). Um die beste Möglichkeit bereit, müssen Anwendungsentwickler 60 FPS beibehalten, den konsistent alle 16 Millisekunden stellt einem neuen Abbild des Betriebssystems mit übersetzt.

**60 FPS** um Hologramme, sehen Sie, wie sie in der realen Welt sitzen zu zeichnen, HoloLens, die zum Rendern von Bildern aus Position des Benutzers benötigt. Da Bildrendering Zeit dauert, sagt HoloLens, wo eines Benutzers Head werden sollen, wenn im zeigt die Bilder angezeigt werden. Dieser Vorhersagealgorithmus ist eine Näherung. HoloLens hat es sich um Hardware, der das gerenderte Bild-Konto für die Abweichung zwischen den vorhergesagten Head und der tatsächlichen Head Position angepasst wird. Dies ermöglicht, sieht das Bild des Benutzers, angezeigt werden, als wenn er, aus dem korrekten Speicherort gerendert wurde, und Hologramme stabil. Das Image aktualisiert Arbeit am besten mit kleinen Änderungen, und bestimmte Dinge in das gerenderte Bild wie Motion-Parallax nicht vollständig behoben werden.

Durch das Rendern mit 60 FPS machen Sie drei Schritte, um stabile Hologramme zu machen:
1. Minimieren die gesamtlatenz zwischen rendern, ein Bild und dieses Image wird den Benutzer sichtbar. In ein Modul mit einem Spiel Thread und einen Renderthread kann das Ausführen im Gleichschritt, 30 FPS mit 33.3ms zusätzliche Latenz hinzufügen. Durch Verringern der Latenz, Dies verringert die Vorhersagefehler und – Hologramm Stabilität erhöht.
2. Somit, sodass jedes Bild des Benutzers Augen erreicht haben, einen konsistenten Betrag an Wartezeit. Wenn Sie mit 30 fps rendern, wird die Anzeige immer noch Bilder mit 60 FPS. Dies bedeutet, dass das gleiche Image zweimal in einer Zeile angezeigt wird. Der zweite Frame müssen 16.6ms längere Wartezeiten als der erste frame und muss eine ausgeprägter Menge an Fehler zu beheben. Diese Inkonsistenz in der Größenordnung von Fehler kann dazu führen, dass unerwünschte 60 hz Judder.
3. Reduzieren die Darstellung der Judder, ist die durch ungleichmäßige während der Übertragung und doppelten Bildern gekennzeichnet. Schneller – Hologramm während der Übertragung und niedrigere Render Raten zugeordnet deutlicher judder. Aus diesem Grund trägt wollen 60 FPS zu pflegen Zeiten Judder für einen bestimmten verschieben – Hologramm zu vermeiden.

**Framerate Konsistenz** Frame Rate Konsistenz ist ebenso wichtig wie eine hohe Frames pro Sekunde. Gelegentlich gelöscht werden für jede Anwendung umfangreicher unvermeidlich, und die HoloLens implementiert einige hoch entwickelten Algorithmus zur Wiederherstellung nach gelegentlicher Störungen. Allerdings ist eine ständig wechselnde Framerate viel deutlicher zu einem Benutzer als bei der Ausführung konsistent zu den niedrigeren Tarifen von Frames. Beispielsweise wird eine Anwendung, die rendert reibungslos für 5 Frames (60 FPS für die Dauer dieser 5 Frames) und legt dann jedes anderen Frames für die nächsten 10 Frames (30 FPS für die Dauer dieser 10 Frames) mehr als eine Anwendung instabil diesen so konsistent angezeigt rendert auf 30 BpS.

In diesem Zusammenhang, das Betriebssystem wird Anwendungen auf 30 BpS Drosselung bei [mixed Reality-Erfassung](mixed-reality-capture.md) ausgeführt wird.

**Informationen zur Leistungsanalyse** stehen eine Vielzahl von Tools, mit denen die Framerate der Anwendung wie z. B. Vergleichstests werden können:
* GPUView
* Visual Studio Grafik-Debugger
* Profiler-3D-Engines wie z. B. Unity integriert

## <a name="hologram-render-distances"></a>Die Render entfernungen – Hologramm

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

Das interaktive visual System integriert mehrere abhängige Abstand Signale fixates und konzentriert sich auf ein Objekt.
* [Unterkunft](https://en.wikipedia.org/wiki/Accommodation_%28eye%29) -den Fokus der einzelnen Ausschau.
* [Konvergenz](https://en.wikipedia.org/wiki/Convergence_(eye)) – zwei Augen nach innen verschoben oder nach außen, um den Mittelpunkt eines Objekts festzulegen.
* [Fernglas Vision](https://en.wikipedia.org/wiki/Stereopsis) -Unterschiede zwischen den linken und rechten Eye-Bildern, die Entfernung eines Objekts, von Fixation Point abhängig sind.
* Schattierung, relative angular-Größe und andere Hinweise monokularen (einzelne Eye).

Konvergenz und Unterbringung sind eindeutig, da sie sehr Beispiel Hinweise, die im Zusammenhang sind mit der die Augen wie zu ändern, um Objekte auf verschiedenen Abstände wahrnehmen. In natürliche anzeigen, sind die Konvergenz und Unterbringung verknüpft. Wenn die Augen etwas in der Nähe (z. B. Ihre Nase) anzeigen wird die Augen überschreiten und zu einem Zeitpunkt Near aufzunehmen. Wenn anzeigen etwas die Augen auf unendlich, wenn die Augen parallele sind und vom Auge gilt für unendlich. Benutzern steht, geteert HoloLens werden immer berücksichtigen, auf 2.0m zu verwalten, ein klares Bild, da die HoloLens zeigt sind in einer optischen Abstand ungefähr 2.0m von der Benutzer fest. App-Entwickler-Steuerelement, in denen Benutzer Augen konvergieren, durch die Platzierung von Inhalt und Hologramme in verschiedenen Ebenen. Wenn Benutzer ermöglichen und zu anderen Abständen zusammengeführt, die natürliche Verknüpfung zwischen den beiden Hinweise sind fehlerhaft und kann dies zu visual angefasst oder Ermüdung, insbesondere, wenn die Größe des Konflikts groß ist. Angefasst aus den Vergence-Unterbringung Konflikt vermieden oder minimiert werden, da der Inhalt, der Benutzer auf 2.0 m möglichst nahe zusammengeführt werden kann (d. h. in einer Szene mit viel Tiefe setzen, die Bereiche von Interesse sind, in der Nähe von 2,0 m, wenn möglich). Wenn der Inhalt kann nicht platziert werden ist nahezu 2.0 m angefasst aus den Konflikt Vergence-Unterkunft größten angezeigt, wenn Benutzer die hin und her zwischen verschiedenen Abstände bestaunen. Das heißt, ist es viel besser vertraut sind, betrachten Sie ein stationär Hologramm, die 50 cm entfernt als, sehen Sie sich ggf. ein Hologramm 50 cm sofort bleibt, das sich im Laufe der Zeit auf und von Ihnen weg bewegt.

Platzieren von Inhalt an 2.0m ist auch vorteilhaft, da die zwei zeigt entwickelt wurden, um auf die Entfernung vollständig überlappen. Images, die aus dieser Ebene platziert werden wie sie außerhalb des Frames, holographic verschoben werden sie von einer Anzeige befinden, auf dem anderen sichtbaren werden ausgeblendet. Diese Fernglas Rivalry kann für die Wahrnehmung der Tiefe von der Hologramm störend sein.

**Optimale Abstand zur Platzierung von Hologramme des Benutzers**

![Optimale Abstand zur Platzierung von Hologramme des Benutzers](images/distanceguiderendering-750px.png)

**Schneiden Sie Ebenen** für optimalen Komfort Clipping Render Abstand am 85 cm mit Fadeout von Inhalten, die beginnend bei 1 Mio. empfohlen. In Anwendungen, in denen Hologramme und Benutzer beide stationär Hologramme sind, können angezeigt werden, problemlos als near als 50cm. Klicken Sie in diesen Fällen Anwendungen sollten eine vorderen Clippingebene nicht näher als 30cm platzieren, und ausblenden, sollten mindestens 10cm Weg von der vorderen Clippingebene beginnen. Jedes Mal, wenn der Inhalt ist als 85cm, es wichtig ist, stellen Sie sicher, dass Benutzer häufig nicht näher oder weiter Hologramme verschieben oder Hologramme nicht häufig näher oder weiter Weg der Benutzer verschieben, wie diese Fälle sind die häufigsten Ursachen angefasst aus, der Vergence-Unterbringung-Konflikt. Inhalte sollten so entworfen werden, dass die senken den Aufwand für die Interaktion näher als 85cm vom Benutzer, aber wenn der Inhalt gerendert werden muss näher als 85cm eine gute Faustregel für Entwickler ist, um Szenarien zu entwerfen, in denen Benutzer und/oder Hologramme nicht mehr als 25 % von t ausführlich verschieben er Zeit.

**Bewährte Methoden** Wenn Hologramme können nicht auf 2 m platziert werden und Konflikte zwischen Konvergenz und beeinflusst nicht vermieden werden, ist die optimale Zone für die Platzierung von – Hologramm 1,25 m bis 5 m. In jedem Fall sollte Designer Struktur Inhalt empfehlen Benutzern die Interaktion von 1 + m entfernt (z. B. Inhaltsgröße anpassen und die Positionierungsparameter des Standard).

## <a name="stabilization-plane"></a>Stabilisierung-Ebene
> [!NOTE]
> Für desktop immersive Headsets ist das einer Ebene für die Stabilisierung in der Regel kontraproduktiv, da sie weniger visuelle Qualität als die Bereitstellung Ihrer app Tiefenpuffer für das System für das Aktivieren von pro-Pixel-Depth-basierte Reprojection bietet. Wenn auf eine HoloLens ausgeführt wird, sollten Sie in der Regel, die Stabilisierung-Ebene festlegen.

HoloLens führt eine anspruchsvolle hardwareunterstützte holographic Stabilisierung-Methode. Dies erfolgt zum größten Teil automatisch und während der Übertragung und Änderung der Sicht (CameraPose) zusammen, animiert die Szene und der Benutzer richtet ihren Köpfen. Eine einzelne Ebene, die Stabilisierung-Ebene aufgerufen wird ausgewählt, um diese Stabilisierung zu maximieren. Während einige Stabilisierung alle Hologramme in der Szene angezeigt wird, erhalten Hologramme in der Ebene der Stabilisierung der Stabilisierung maximale Hardware.

![Stabilisierung-Ebene für 3D-Objekte](images/stab-plane-500px.jpg)

Das Gerät wird automatisch versuchen, auf dieser Ebene, aber die Anwendung kann durch Auswählen der Fokuspunkt in der Szene in diesem Prozess unterstützen. Unity-apps, die unter einem HoloLens sollten auswählen, die am besten zeigen basierend auf Ihrer Szene zu konzentrieren, und übergeben es in [SetFocusPoint()](focus-point-in-unity.md). Ein Beispiel zum Festlegen der Fokuspunkt in DirectX ist in der Standardvorlage für rotierenden Cube enthalten.

Beachten Sie, dass beim Ausführen Ihrer Unity-app auf eine immersive Kopfhörer, die mit einem desktop-PC verbundenen Unity übermittelt, Ihre Tiefenpuffer, Windows, die pro-Pixel-Reprojection, zu dem in der Regel besseren Bildqualität ohne explizite von der app enthalten sind. Wenn Sie einen Schwerpunkt,, die die pro-Pixel-Reprojection außer Kraft setzt bereitstellen, sollte also nur möchten bei der Ausführung Ihrer app auf einem HoloLens.




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

Platzierung der Fokuspunkt hängt zum größten Teil der Hologramm ansehen. Die app verfügt über die Blicke Vektor zu Referenzzwecken und der app-Designer weiß, welche Inhalte sie den Benutzer, das überwacht werden soll.

Einzelne sehr wichtig, wie ein Entwickler kann Hologramme stabilisieren ist zum Rendern mit 60 FPS. Das Ablegen unterhalb 60 FPS werden – Hologramm Stabilität, unabhängig von der Stabilisierung Ebene Optimierung erheblich reduzieren.

**Bewährte Methoden** es gibt keine universelle Möglichkeit zum Einrichten der Stabilisierung-Ebene und app-spezifisch ist, bleiben kann, damit die wichtigsten Empfehlung ist, und beobachten, was am besten für Ihre Szenarien ist. Versuchen Sie jedoch die Stabilisierung-Ebene mit so viel Inhalt möglichst ausgerichtet werden, da sämtliche Inhalte stehen auf dieser Ebene perfekt stabilisiert ist.

Zum Beispiel:
* Wenn Sie nur planare Inhalt (Lesen-app, Videowiedergabe app), die die Stabilisierung-Ebene mit der Ebene ausrichten haben hat, Ihre Inhalte.
* Treten 3 kleine Kugeln, die World-gesperrt sind, stellen Sie die Stabilisierung-Ebene, "Ausschneiden", jedoch alle die Kugeln zentriert, die in die Ansicht des Benutzers aktuell sind.
* Wenn die Szene Inhalt in grundlegend andere Ebenen enthält, bevorzugt weitere Objekte.
* Stellen Sie sicher, dass den Stabilisierung Punkt anpassen, die jedes Einzelbild an mit der Hologramm des Benutzers ausgewertet wird

**Dinge, die** die Stabilisierung-Ebene ist eine gute Tool, um stabile Hologramme, aber wenn missbraucht werden sie erzielen kann dazu führen, schwerwiegende Image Systeminstabilität zur Folge.
* Nicht von "fire and forget", da Sie am Ende können die snapshotisolierung Verwaltungsebene hinter der Benutzer oder an ein Objekt, das nicht mehr in die Ansicht des Benutzers ist angefügt. Stellen Sie sicher, dass die Stabilisierung-Ebene, die normale entgegengesetzten Kamera Weiterleitung (z. B. - camera.forward) festgelegt ist
* Ändern Sie nicht schnell an der Stabilisierung-Ebene hin und her zwischen den extremen
* Lassen Sie nicht die Stabilisierung-Ebene, die auf einem festen Abstand/Ausrichtung festgelegt
* Lassen Sie nicht die Stabilisierung-Ebene, die über die Benutzerkontoeigenschaften Ausschneiden
* Nicht den Fokuspunkt festgelegt, wenn auf einem Desktop-PC, anstatt eine HoloLens ausgeführt, und verwenden Sie stattdessen auf pro-Pixel-Depth-basierte Reprojection.

## <a name="color-separation"></a>Farbliche Trennung 

Aufgrund der Art der HoloLens angezeigt werden soll kann manchmal ein Element namens "Color: Trennung" angesehen werden. Sie manifestiert sich als das Bild, das die Aufteilung in einzelne Grundfarben – Rot, Grün und Blau. Das Element kann vor allem angezeigt werden, weiß Objekte angezeigt, da sie große Mengen von Rot, Grün und Blau aufweisen. Es ist am deutlichsten, wenn ein Benutzer ggf. ein Hologramm visuell verfolgt nach, die über den holographic Frame mit hoher Geschwindigkeit bewegt wird. Eine weitere Möglichkeit, die das Artefakt manifest kann ist Verzerren von/Verformung von Objekten. Wenn ein Objekt, hohen Kontrast verfügt und/oder reine Farben (Rot, Grün, Blau), farbliche Trennung wird als verzerren verschiedener Teile des Objekts von wahrgenommen werden.

**Welche Trennung der Farbe eines Head-locked weißen round Beispiel könnte wie folgt aussehen, wie ein Benutzer ihren Köpfen auf der Seite dreht:**

![Welche Trennung der Farbe eines Head-locked weißen round Beispiel könnte wie folgt aussehen, wie ein Benutzer ihren Köpfen auf der Seite dreht.](images/colorseparationofroundwhitecursor-300px.png)

Obwohl es schwierig, eine farbliche Trennung vollständig zu vermeiden ist, gibt es verschiedene Techniken zur Verfügung, um es zu verringern.

**Farbe Trennung kann für angezeigt werden:**
* Objekte, die schnell verschieben, einschließlich der Head-locked-Objekte wie z. B. die [Cursor](cursors.md).
* Objekte, die im Wesentlichen weit von der [Stabilisierung Ebene](hologram-stability.md#stabilization-plane).

**Um die Auswirkungen der Trennung Farbe Dämpfen:**
* Stellen Sie das Objekt des Benutzers Blicke lag. Es sollte angezeigt werden, als ob er verfügt über einige Trägheit und die Blicke "on Federn" angefügt ist. Dies verlangsamt wird den Cursor (Trennung Entfernung verringert) und hinter der Benutzer wahrscheinlich Blicke eingefügt. Solange es schnell entdeckt einrichten, wenn der Benutzer beendet die Blicke Verschiebung fühlt es ganz natürlich.
* Wenn Sie ggf. ein Hologramm verschieben möchten, sollten Sie Bewegung Geschwindigkeit unter 5 Grad pro Sekunde zu halten, wenn sich abzeichnet, dass der Benutzer mit ihren Augen Wirklichkeit folgen soll.
* Verwendung *Licht* anstelle von *Geometrie* für den Cursor. Eine Quelle für virtuelle Beleuchtung, die an die Blicke angefügt wird als interaktiver Zeiger wahrgenommen werden, aber es verursacht keine Farbe Trennung.
* Anpassen der Stabilisierung-Ebene, um die Hologramme übereinstimmen, denen der Benutzer am gazing ist.
* Stellen Sie das Objekt Rot, Grün oder Blau.
* Wechseln Sie zu einem weichgezeichnete Version des Inhalts. Beispielsweise kann ein round-weißer-Cursor Änderung zu einer etwas verschwommen Zeile in die Richtung der Bewegung ausgerichtet sein.

Wie zuvor Rendern mit 60 FPS und Festlegen der Stabilisierung-Ebene die wichtigsten Techniken – Hologramm Stabilität sind. Wenn merkliche farbliche Trennung, stellen Sie zunächst sicher, dass die Framerate Erwartungen erfüllt.

## <a name="see-also"></a>Siehe auch
* [Grundlegendes zur Leistung für Mixed Reality](understanding-performance-for-mixed-reality.md)
* [Farbe, Licht und Materialien](color,-light-and-materials.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)