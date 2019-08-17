---
title: Entwurf für räumliche Zuordnung
description: Die effektive Verwendung der räumlichen Zuordnung in hololens erfordert sorgfältige Überlegungen zu vielen Faktoren.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Gemischte Windows-Realität, Entwurf, räumliche Zuordnung, hololens, Oberflächenrekonstruktion, Mesh
ms.openlocfilehash: 02e64727f9a23bea28e018d7c4e5a8b89c152447
ms.sourcegitcommit: 60f73ca23023c17c1da833c83d2a02f4dcc4d17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566008"
---
# <a name="spatial-mapping-design"></a>Entwurf für räumliche Zuordnung

Die effektive Verwendung der räumlichen Zuordnung in hololens erfordert sorgfältige Überlegungen zu vielen Faktoren.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Funktion</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Entwurf für räumliche Zuordnung</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="why-is-spatial-mapping-important"></a>Warum ist die räumliche Zuordnung wichtig?

Die räumliche Zuordnung ermöglicht das Platzieren von Objekten auf realen Oberflächen. Dies hilft bei der Verankerung von Objekten in der Benutzer Welt und nutzt die Vorteile der tatsächlichen tiefen Hinweise. Das Verwahren von holograms auf der Grundlage von anderen holograms und realen Objekten hilft dem Benutzer zu überzeugen, dass sich diese Hologramme tatsächlich in Ihrem Bereich befinden. Hologramme, die leer sind oder sich mit dem Benutzer bewegen, werden nicht als Real angezeigt. Platzieren Sie Elemente nach Möglichkeit aus Gründen der Bequemlichkeit.

Visualisieren von Oberflächen beim platzieren oder Verschieben von holograms (Verwenden eines einfachen projizierten Rasters). Dadurch kann der Benutzer wissen, wo er seine Hologramme am besten platzieren kann. der Benutzer wird angezeigt, wenn die Stelle, an der er das – Hologramm platzieren möchte, noch nicht zugeordnet wurde. Sie können für den Benutzer "Billboard Items" hinzufügen, wenn er zu viel Winkel hat.

## <a name="what-influences-spatial-mapping-quality"></a>Was beeinflusst die Qualität der räumlichen Zuordnung?

Mehrere [hier](environment-considerations-for-hololens.md)ausführliche Faktoren können die Häufigkeit und den Schweregrad dieser Fehler beeinflussen.  Allerdings sollten Sie Ihre Anwendung so entwerfen, dass der Benutzer auch bei Fehlern in den räumlichen Daten der Zuordnung seine Ziele erreichen kann.

## <a name="the-environment-scanning-experience"></a>Umgebung zum Scannen der Umgebung

Jede Anwendung, die räumliche Zuordnung verwendet, sollte die Bereitstellung einer "Scan Darstellung" in Erwägung gezogen werden. der Prozess, durch den die Anwendung den Benutzer zum Überprüfen von Oberflächen führt, die für eine ordnungsgemäße Funktionsweise der Anwendung erforderlich sind.

![Beispiel für das Scannen](images/sr-mixedworld-140429-8pm-00068-1000px.png)<br>
*Beispiel für das Scannen*

Die Art dieser Scanfunktion kann sich je nach Anforderungen der Anwendung stark unterscheiden, aber zwei Hauptprinzipien sollten den Entwurf berücksichtigen.

Erstens **ist die klare Kommunikation mit dem Benutzer das primäre Problem**. Der Benutzer sollte immer wissen, ob die Anforderungen der Anwendung erfüllt werden. Wenn Sie nicht erfüllt werden, sollten Sie dem Benutzer sofort klar sein, warum dies der Fall ist, und Sie sollten schnell dazu führen, dass Sie die entsprechende Aktion ausführen.

Zweitens **sollten Anwendungen versuchen, ein Gleichgewicht zwischen Effizienz und Zuverlässigkeit zu erzielen**. Wenn dies möglich ist, sollten Anwendungenräumliche Daten automatisch analysieren, um die Benutzer Zeit zu sparen. Wenn es nicht möglich ist, dies zuverlässig zu tun, sollten Anwendungen den Benutzer stattdessen ermöglichen, der Anwendung schnell die zusätzlichen Informationen bereitzustellen, die Sie benötigt.

Wenn Sie die richtige Scanfunktion entwerfen möchten, sollten Sie die folgenden Möglichkeiten für Ihre Anwendung beachten:

* **Keine Scanvorgänge**
   * Eine Anwendung funktioniert problemlos, ohne dass eine gesteuerte Überprüfung durchgeführt werden kann. Sie erfahren mehr über Oberflächen, die im Kurs der natürlichen Benutzer Bewegung beobachtet werden.
   * Eine Anwendung, die es dem Benutzer ermöglicht, auf Oberflächen mit Holographic Spray Paint zu zeichnen, benötigt z. b. wissen, dass nur die Oberflächen für den Benutzer sichtbar sind.
   * Die Umgebung wird möglicherweise bereits vollständig gescannt, wenn Sie eine solche ist, in der der Benutzer bereits viel Zeit für die Verwendung der hololens aufgewendet hat.
   * Bedenken Sie jedoch, dass für die Kamera, die von der räumlichen Zuordnung verwendet wird, nur 3.1 m vor dem Benutzer angezeigt werden kann, sodass die räumliche Zuordnung keine weiteren entfernten Oberflächen kennt, es sei denn, der Benutzer hat Sie in der Vergangenheit in der Vergangenheit beobachtet.
   * Damit der Benutzer weiß, welche Oberflächen gescannt wurden, sollte die Anwendung diesem Effekt visuelles Feedback bereitstellen, z. b. Wenn Sie virtuelle Schatten in überprüfte Oberflächen umwandeln, kann der Benutzer möglicherweise holograms auf diesen Oberflächen platzieren.
   * In diesem Fall sollten die umgebenden Volumes des räumlichen Oberflächen Beobachters jedes Frame in ein im Text gesperrtes [räumliches Koordinatensystem](coordinate-systems.md)aktualisiert werden, damit Sie dem Benutzer folgen.

* **Suchen nach einem passenden Speicherort**
   * Eine Anwendung kann für die Verwendung an einem Speicherort mit speziellen Anforderungen entworfen werden.
   * Beispielsweise ist für die Anwendung möglicherweise ein leerer Bereich um den Benutzer erforderlich, damit Sie Holographic Kung-Fu sicher üben kann.
   * Anwendungen sollten alle speziellen Anforderungen an den Benutzer übermitteln und Sie mit unbestimmtem visuellen Feedback verstärken.
   * In diesem Beispiel sollte die Anwendung den Umfang des erforderlichen leeren Bereichs visualisieren und das vorhanden sein von nicht gewünschten Objekten in dieser Zone visuell hervorheben.
   * In diesem Fall sollten die umgebenden Volumes des räumlichen Oberflächen Beobachters das weltweit gesperrte [räumliche Koordinatensystem](coordinate-systems.md) am ausgewählten Speicherort verwenden.

* **Suchen nach einer passenden Konfiguration von Oberflächen**
   * Eine Anwendung erfordert möglicherweise eine bestimmte Konfiguration von Oberflächen, z. b. zwei große, flache und gegen Wände, um eine Holographic Hall of Spiegel zu erstellen.
   * In solchen Fällen muss die Anwendung die von der räumlichen Zuordnung bereitgestellten Oberflächen analysieren, um geeignete Oberflächen zu erkennen und den Benutzer an Sie weiterzuleiten.
   * Der Benutzer sollte über eine Fall Back Option verfügen, wenn die Oberflächenanalyse der Anwendung nicht vollständig zuverlässig ist. Wenn die Anwendung z. b. fälschlicherweise eine Tür als flache Wand identifiziert, benötigt der Benutzer eine einfache Methode, um diesen Fehler zu beheben.

* **Einen Teil der Umgebung scannen**
   * Eine Anwendung möchte möglicherweise nur einen Teil der Umgebung erfassen, wie vom Benutzer gesteuert.
   * Die Anwendung scannt z. b. einen Teil eines Raums, sodass der Benutzer eine Holographic-Klassifikation für die zu verkaufenden Möbel veröffentlichen kann.
   * In diesem Fall sollte die Anwendung räumliche Mapping-Daten innerhalb der Regionen erfassen, die vom Benutzer während des Scans beobachtet werden.

* **Gesamten Raum Scannen**
   * Eine Anwendung erfordert möglicherweise eine Überprüfung aller Oberflächen im aktuellen Raum, einschließlich derjenigen hinter dem Benutzer.
   * Beispielsweise kann ein Spiel den Benutzer in die Rolle "gulleber" versetzen, die von Hunderten von kleinen lilliputians aus allen Richtungen fast erreicht werden kann.
   * In solchen Fällen muss die Anwendung bestimmen, wie viele der Oberflächen im aktuellen Raum bereits gescannt wurden, und den Blick des Benutzers darauf ausrichten, große Lücken zu füllen.
   * Der Schlüssel zu diesem Prozess ist das Bereitstellen von visuellem Feedback, mit dem der Benutzer klar ist, welche Oberflächen noch nicht gescannt wurden. Die Anwendung könnte z. b. einen [Entfernungs basierten Nebel](https://msdn.microsoft.com/library/windows/desktop/bb173401%28v=vs.85%29.aspx) verwenden, um Bereiche visuell hervorzuheben, die nicht von räumlichen Mapping-Flächen abgedeckt werden.

* **Erstellen Sie eine anfängliche Momentaufnahme der Umgebung.**
   * Eine Anwendung möchte möglicherweise alle Änderungen in der Umgebung ignorieren, nachdem Sie eine anfängliche "Momentaufnahme" übernommen haben.
   * Dies kann sinnvoll sein, um eine Unterbrechung von Benutzer erstellten Daten zu vermeiden, die eng mit dem ursprünglichen Zustand der Umgebung verknüpft sind.
   * In diesem Fall sollte die Anwendung eine Kopie der räumlichen Zuordnungen im ursprünglichen Zustand erstellen, sobald die Überprüfung beendet ist.
   * Anwendungen sollten weiterhin Updates für räumliche Zuordnungs Daten empfangen, wenn Hologramme weiterhin von der Umgebung ordnungsgemäß verschlossen werden.
   * Fortlaufende Updates für räumliche Zuordnungsdaten ermöglichen auch das Visualisieren von Änderungen, die aufgetreten sind, und verdeutlichen den Benutzern die Unterschiede zwischen dem früheren und dem aktuellen Zustand der Umgebung.

* **Benutzer initiierte Momentaufnahmen der Umgebung erstellen**
   * Eine Anwendung möchte möglicherweise nur auf Umgebungs Änderungen reagieren, wenn Sie vom Benutzer angewiesen werden.
   * Der Benutzer könnte z. b. mehrere 3D-"Statuen" eines Friend erstellen, indem er seine Posen in verschiedenen Augenblicken erfasst.

* **Benutzern das Ändern der Umgebung gestatten**
   * Eine Anwendung kann so entworfen werden, dass Sie in Echtzeit auf alle Änderungen in der Benutzerumgebung antwortet.
   * Der Benutzer, der einen Vorhang zeichnet, könnte z. b. "Szenen Änderung" für eine holografische Wiedergabe auf der anderen Seite auslöst.

* **Leiten Sie den Benutzer ein, um Fehler in den räumlichen Daten zu vermeiden.**
   * Eine Anwendung möchte dem Benutzer beim Scannen der Umgebung möglicherweise Anleitungen bereitstellen.
   * Dies kann den Benutzer dabei unterstützen, bestimmte Arten von [Fehlern in den räumlichen Daten](spatial-mapping-design.md#what-influences-spatial-mapping-quality)zu vermeiden, z. b. durch die Entfernung von Fenstern oder spiegeln.

Ein zusätzliches Detail, das zu beachten ist, besteht darin, dass der Bereich der räumlichen Zuordnungsdaten nicht unbegrenzt ist. Während die räumliche Zuordnung eine permanente Datenbank mit großen Leerzeichen erstellt, werden diese Daten nur für Anwendungen in einer begrenzten Größe um den Benutzer verfügbar gemacht. Wenn Sie also am Anfang eines langen Korridors beginnen und weit genug weg vom Start Weg gehen, werden die räumlichen Oberflächen am Anfang nicht mehr angezeigt. Sie können dies natürlich verringern, indem Sie diese Oberflächen in der Anwendung Zwischenspeichern, nachdem Sie aus den verfügbaren räumlichen Zuordnungsdaten verschwunden sind.

## <a name="mesh-processing"></a>Mesh-Verarbeitung

Es kann hilfreich sein, häufige Arten von Fehlern in Oberflächen zu erkennen und die räumlichen Zuordnungsdaten nach Bedarf zu filtern, zu entfernen oder zu ändern.

Beachten Sie, dass räumliche Zuordnungsdaten so wie möglich an reale Oberflächen ausgerichtet werden sollen, sodass bei jeder Verarbeitung, die Sie anwenden, ihre Oberflächen weiter von der Wahrheit entfernt werden.

Im folgenden finden Sie einige Beispiele für verschiedene Arten der Mesh-Verarbeitung, die Sie möglicherweise hilfreich finden:

* **Loch Füllung**
   * Wenn ein kleines Objekt, das aus einem dunklen Material besteht, nicht gescannt werden kann, wird eine Lücke auf der umgebenden Oberfläche hinterlassen.
   * Löcher wirken sich auf die Okklusion aus: holograms können durch ein Loch in einer vermeintlich nicht transparenten realen Oberfläche angezeigt werden.
   * Löcher wirken sich auf Raycasts aus: Wenn Sie Raycasts verwenden, um Benutzer bei der Interaktion mit Oberflächen zu unterstützen, ist es möglicherweise nicht wünschenswert, dass diese Strahlen Lücken passieren. Eine Entschärfung besteht darin, ein Bündel mehrerer Raycasts zu verwenden, die einen entsprechend großen Bereich abdecken. Auf diese Weise können Sie die Ergebnisse von "outreißer" filtern, damit das Aggregat Ergebnis auch dann gültig ist, wenn ein raycast eine kleine Lücke durchläuft. Beachten Sie jedoch, dass dieser Ansatz zu Rechen Kosten kommt.
   * Löcher wirken sich auf die Physik aus: ein Objekt, das von der Physik-Simulation gesteuert wird, kann eine Lücke im Boden ablegen und geht verloren.
   * Es ist möglich, diese Lücken im Oberflächen Mesh algorithmisch zu füllen. Sie müssen jedoch ihren Algorithmus optimieren, damit "echte Lücken" wie Windows und Doorways nicht ausgefüllt werden. Es kann schwierig sein, "echte Löcher" von "imaginären Löchern" zuverlässig zu unterscheiden, sodass Sie mit unterschiedlichen Heuristiken experimentieren müssen, wie z. b. "size" und "Boundary Shape".

* **Entfernen von halluziierung**
   * Reflektionen, helle Lichter und verschiebende Objekte können kleine "halluzationen" in Mittel Luft bewegen.
   * Halluzerungen wirken sich auf die oksion aus: halluformen können als dunkle Formen sichtbar werden, die vor und nach anderen holograms stehen.
   * Hallutrisierungen wirken sich auf Raycasts aus: Wenn Sie Raycasts verwenden, um Benutzer bei der Interaktion mit Oberflächen zu unterstützen, können diese Strahlen eine halluziierung anstelle der dahinter liegenden Oberfläche erreichen. Wie bei den Lücken besteht eine Entschärfung darin, viele Raycasts anstelle eines einzelnen raycast zu verwenden, aber auch hier werden die Rechen Kosten berechnet.
   * Hallutrisierungen wirken sich auf die Physik aus: ein Objekt, das von der Physik-Simulation gesteuert wird, kann sich gegen eine volumumeration befinden und kann nicht durch einen scheinbar unklaren Bereich des Raums wechseln.
   * Es ist möglich, solche hallumeerungen aus dem Oberflächen Mesh zu filtern. Allerdings müssen Sie, wie bei Lücken, ihren Algorithmus optimieren, sodass echte kleine Objekte wie z. b. LAMP-und türhandles nicht entfernt werden.

* **End**
   * Räumliche Zusätze können Oberflächen zurückgeben, die im Vergleich zu ihren echten Gegenstücken grob oder "laut" sind.
   * Glätte wirkt sich auf physikalische Konflikte aus: Wenn der Boden grob ist, kann ein physisch simulierter Golfball in einer geraden Linie nicht nahtlos über ihn hinweg ausgeführt werden.
   * Glätte wirkt sich auf das Rendering aus: Wenn eine Oberfläche direkt visualisiert wird, können sich grobe Oberflächen normale auf ihre Darstellung auswirken und ein "sauberes" Erscheinungsbild unterbrechen. Dies ist möglich, indem Sie die entsprechende Beleuchtung und Texturen im Shader verwenden, die zum renderende der Oberfläche verwendet werden.
   * Es ist möglich, die rautheit in einem Oberflächen Mesh zu glätten. Dadurch wird die Oberfläche jedoch möglicherweise von der entsprechenden realen Oberfläche entfernt. Die Beibehaltung einer Schluss Stimme ist wichtig, um eine genaue Hologramm-Okklusion zu erzielen und es Benutzern zu ermöglichen, präzise und vorhersagbare Interaktionen mit Holographic-Oberflächen zu erzielen
   * Wenn nur eine kosmetische Änderung erforderlich ist, kann es ausreichen, Vertex-Normale zu glätten, ohne die Scheitelpunkt Positionen zu ändern.

* **Auffinden von Ebenen**
   * Es gibt viele Analyse Formen, die eine Anwendung auf den von der räumlichen Zuordnung bereitgestellten Oberflächen ausführen kann.
   * Ein einfaches Beispiel ist die "Plane-Suche". Identifizierung von begrenzten, größtenteils planaren Bereichen von Oberflächen.
   * Planare Regionen können als holografische Arbeits Oberflächen verwendet werden, in denen Holographic-Inhalte automatisch von der Anwendung platziert werden können.
   * Planare Regionen können die Benutzeroberfläche einschränken, um Benutzer zur Interaktion mit den Oberflächen zu leiten, die Ihren Anforderungen am besten entsprechen.
   * Planare Regionen können wie in der realen Welt verwendet werden, für holografische Entsprechungen zu funktionalen Objekten, wie z. b. LCD-Bildschirmen, Tabellen oder Whiteboards.
   * Planare Regionen können Wiedergabe Bereiche definieren, die die Basis von Videogame-Ebenen bilden.
   * Planare Regionen können virtuellen Agents dabei helfen, in der realen Welt zu navigieren, indem Sie die Bereiche ermitteln, in denen echte Menschen wahrscheinlich gehen.

## <a name="prototyping-and-debugging"></a>Prototypen und Debuggen

### <a name="useful-tools"></a>Nützliche Tools
* Der [hololens-Emulator](using-the-hololens-emulator.md) kann verwendet werden, um Anwendungen mit räumlicher Zuordnung zu entwickeln, ohne auf physische hololens zuzugreifen. Sie ermöglicht es Ihnen, eine Live Sitzung auf einem hololens in einer realistischen Umgebung zu simulieren, mit allen Daten, die Ihre Anwendung normalerweise verbraucht, einschließlich hololens-Bewegung, räumlichen Koordinatensystemen und räumlichen Zuordnungs Netzen. Dies kann verwendet werden, um zuverlässige, wiederholbare Eingaben bereitzustellen, die für das Debuggen von Problemen und das Auswerten von Änderungen an Ihrem Code nützlich sein können.
* Zum reproduzieren eines Szenarios erfassen Sie räumliche Zuordnungsdaten über das Netzwerk aus einem aktiven hololens, speichern Sie Sie dann auf einem Datenträger, und verwenden Sie Sie in nachfolgenden Debugsitzungen erneut.
* Die [3D-Ansicht des Windows-Geräte Portals](using-the-windows-device-portal.md#3d-view) bietet eine Möglichkeit, alle räumlichen Oberflächen anzuzeigen, die zurzeit über das räumliche Mapping-System verfügbar sind. Dies ist eine Grundlage für den Vergleich der räumlichen Oberflächen innerhalb Ihrer Anwendung. Beispielsweise können Sie leicht erkennen, ob räumliche Oberflächen fehlen oder an der falschen Stelle angezeigt werden.

### <a name="general-prototyping-guidance"></a>Leitfaden für allgemeine Prototypen
* Da [Fehler](spatial-mapping-design.md#what-influences-spatial-mapping-quality) in den räumlichen Mapping-Daten sich stark auf die Benutzerumgebung auswirken können, empfiehlt es sich, die Anwendung in einer Vielzahl von Umgebungen zu testen.
* Nehmen Sie nicht an der Gewohnheit vor, sich immer am gleichen Ort zu testen, z. b. an Ihrem Schreibtisch. Stellen Sie sicher, dass Sie auf verschiedenen Oberflächen unterschiedlichen Positionen, Formen, Größen und Materialien testen.
* Auch wenn synthetische oder aufgezeichnete Daten für das Debuggen hilfreich sein können, werden Sie nicht auf die gleichen wenige Testfälle angewiesen. Dadurch werden möglicherweise wichtige Probleme ermittelt, die zuvor durch mehr unterschiedliche Tests abgefangen wurden.
* Es empfiehlt sich, Tests mit echten (und im Idealfall nicht gespoinierten) Benutzern durchzuführen, da Sie die hololens oder Ihre Anwendung möglicherweise nicht exakt auf die gleiche Weise wie Sie verwenden. Dies kann Ihnen vielleicht überraschen, wie sich das Verhalten, das Wissen und die Annahmen der unterschiedlichen Benutzer Verhalten.

## <a name="see-also"></a>Siehe auch
* [Raumabtastvisualisierung](room-scan-visualization.md)
* [Raumklangentwurf](spatial-sound-design.md)
* [Persistenz in Unity](persistence-in-unity.md)
