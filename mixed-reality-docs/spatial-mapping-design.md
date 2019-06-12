---
title: Räumliche Zuordnung entwerfen
description: Effektive Verwendung von räumliche Zuordnung in HoloLens erfordert Überlegung von vielen Faktoren ab.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Surface Wiederaufbau, Netz Windows Mixed Reality, Entwurf, die räumliche Zuordnung
ms.openlocfilehash: 451213a79e1d482d64725ce750065611830beec3
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829958"
---
# <a name="spatial-mapping-design"></a>Räumliche Zuordnung entwerfen

Effektive Verwendung von räumliche Zuordnung in HoloLens erfordert Überlegung von vielen Faktoren ab.

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
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></td>
    </tr>
     <tr>
        <td>Räumliche Zuordnung entwerfen</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="why-is-spatial-mapping-important"></a>Warum ist die räumliche Zuordnung wichtig?

Räumliche Zuordnung ermöglicht es, die Objekte auf echten Oberflächen zu platzieren. Dadurch können die Anker-Objekte des Benutzers Welt und nutzt die Vorteile der realen Welt Tiefe Hinweise. Ihre Hologramme basierend auf anderen Hologramme und Objekte der realen Welt occluding hilft dabei, den Benutzer dazu verleiten, die diese Hologramme tatsächlich in seinem Bereich. Hologramme nun in Speicherplatz oder Verschieben von mit dem Benutzer wird nicht praktisch als Real. Wenn möglich, Elemente, direkt aus Annehmlichkeitsgründen.

Visualisieren Sie Flächen beim platzieren, oder verschieben Sie Hologramme (verwenden Sie ein einfaches projizierten Raster). Dadurch wird den Benutzer darüber informiert, wo sie ihre Hologramme können am besten platzieren, und dem Benutzer zeigt, wenn die Stelle, die sie versuchen, platzieren Sie den – Hologramm noch zugeordnet wurde noch nicht. Sie können "Elemente zum Benutzer hin billboard" Wenn die letztlich auf zu viele eines Winkels.

## <a name="what-influences-spatial-mapping-quality"></a>Welche Qualität für räumliche Zuordnung beeinflusst?

Um die bestmögliche benutzererfahrung bieten zu können, ist es wichtig zu verstehen, die Faktoren, die die Qualität von HoloLens die räumliche Zuordnung gesammelten betreffen.

Fehler in räumliche Zuordnungsdaten fallen in drei Kategorien unterteilt:
* **Lücken**: Real-World werden die räumliche Zuordnungsdaten fehlen.
* **Wahnvorstellungen**: Flächen befinden sich in die räumliche Zuordnung-Daten, die nicht in der realen Welt vorhanden sind.
* **Verschiebung**: Oberflächen in die räumliche Zuordnungsdaten werden aber mit realen Flächen, entweder mithilfe von Push übertragen oder herausgezogen ausgerichtet.

Die Häufigkeit und den Schweregrad dieser Fehler können von verschiedenen Faktoren beeinflusst:

* **Benutzer während der Übertragung**
   * Wie der Benutzer der Umgebung durchläuft bestimmt wie gut die Umgebung überprüft werden, damit der Benutzer möglicherweise Anweisungen erfordern, um eine gute Überprüfung zu erreichen.
   * Für die Überprüfung verwendete Kamera enthält Daten in einem 70 Grad Cone-, einem von einem Minimum von 0,8 Zähler auf ein Maximum von 3,1 Meter Abstand von der Kamera. Reale Flächen werden nur innerhalb dieser Sichtfeld überprüft. Beachten Sie, dass diese Werte können in zukünftigen Versionen geändert werden.
   * Wenn der Benutzer nie in 3.1 Zähler eines Objekts wird es nicht überprüft.
   * Wenn der Benutzer zeigt nur ein Objekt aus einer Entfernung von weniger als 0,8 Zähler werden nicht überprüft werden (Dies vermeidet, Überprüfung des Benutzers Hand).
   * Wenn der Benutzer nie nach oben aussieht (Dies ist ziemlich normal) wird die Obergrenze wahrscheinlich nicht überprüft.
   * Wenn ein Benutzer nie hinter Möbel oder eine Wand aussieht werden die Objekte, die von ihnen okkludierte nicht überprüft werden.
   * Flächen meist auf eine höhere Qualität überprüft werden, wenn sie uns anstatt in einem flachen Winkel angezeigt werden.
   * Wenn der Head-Tracking-System, der die HoloLens vorübergehend ein Fehler auftritt (die erfolgen aufgrund von Bewegung für eine schnelle, schlechter Beleuchtung, detailarmen Wände oder die Kameras behandelt immer kann), kann dies Fehler in die räumliche Zuordnungsdaten führen. Derartige Fehler werden im Laufe der Zeit korrigiert werden, da der Benutzer weiterhin bewegen, und überprüfen ihre Umgebung.

* **Surface-Materialien**
   * Die Materialien von realen Flächen variieren stark. Diese Auswirkungen auf die Dienstqualität räumliche Zuordnung, die Daten, da sie sich wie Infrarotlicht auswirken wiedergegeben werden.
   * Dunkel Flächen können nicht überprüft werden, bis sie näher an der Kamera, geschaltet werden, da sie weniger Licht reflektieren.
   * Einige Flächen möglicherweise so dunkel, entsprechend zu wenig Licht von jede Entfernung, gescannt werden müssen, damit sie Hole-Fehler an der Position der Oberfläche und manchmal auch hinter die Oberfläche eingeführt werden.
   * Insbesondere leuchtende Oberflächen überprüft möglicherweise nur bei der Anzeige anzunehmen, und nicht verwendet werden, wenn in einem flachen Winkel angezeigt.
   * Spiegel, können da sie illusory Spiegelungen echte Leerzeichen und Oberflächen, erstellen sowohl Loch und Hallucination Fehlern führen.

* **Szene während der Übertragung**
   * Räumliche Zuordnung passt sich schnell auf Änderungen in der Umgebung, z. B. Personen verschieben oder zu öffnen und schließen Türen an.
   * Allerdings kann räumliche Zuordnung nur anpassen, auf Änderungen in einem Bereich bei, die diesem Bereich auf die Kamera sichtbar ist, die für die Überprüfung verwendet wird.
   * Aus diesem Grund ist es möglich, dass diese Anpassung tatsächlich langsamer läuft als die Lücke oder Hallucination Fehler verursachen können.
   * Als Beispiel ein Benutzer einen Freund überprüft und dann umkehrt, während der Freund Raum verlässt. Eine "Ghost"-Darstellung des Freundes (Hallucination Fehler) wird in den Daten räumliche Zuordnung beibehalten, bis der Benutzer wieder umkehrt und erneut überprüft den Speicherplatz, in dem der Freund ständigen wurde.

* **Beleuchtung Störungen**
   * Infrarot Umgebungslichts in der Szene kann behindert scannen, z. B. sichere Sonnenlicht in einem Fenster.
   * Das Scannen von Surfaces in Ihrer Nähe, des Lichts aus Ihnen zu Verzerrungen Fehler springen können besonders leuchtende Oberflächen beeinträchtigen.
   * Unverankerte während der Ausführung Wahnvorstellungen verursachen oder durch verzögern der Anpassung an die Szene während der Übertragung möglicherweise leuchtende Oberflächen reflektieren Licht direkt wieder in die Kamera mit nahe gelegenen Stelle, beeinträchtigen.
   * Zwei HoloLens-Geräte im selben Raum sollte nicht miteinander in Konflikt Gerät, aber das Vorhandensein von mehr als fünf HoloLens-Geräten kann dazu führen, dass Störungen.

Es ist möglicherweise zu vermeiden oder Korrigieren von für einige dieser Fehler kann. Allerdings sollten Sie Ihre Anwendung entwerfen, damit, dass der Benutzer beim Erreichen ihrer Ziele auch bei Fehlern in den Daten für die räumliche Zuordnung kann.

## <a name="the-environment-scanning-experience"></a>Die Umgebung, die benutzerfreundlichkeit überprüfen

HoloLens erfährt die Flächen in ihrer Umgebung aus, wie der Benutzer diese untersucht. Im Laufe der Zeit erstellt die HoloLens ein Scan der alle Teile der Umgebung, die festgestellt wurden. Außerdem wird die Überprüfung aktualisiert, wie Änderungen in der Umgebung festgestellt werden. Diese Überprüfung wird automatisch zwischen app-Startvorgänge beibehalten.

Jede Anwendung, die räumliche Zuordnung wird verwendet, sollten das Bereitstellen einer ' Überprüfung '; der Prozess, durch den führt die Anwendung den Benutzer um Oberflächen zu scannen, die erforderlich sind, für die Anwendung ordnungsgemäß funktioniert.

![Beispiel für die Überprüfung](images/sr-mixedworld-140429-8pm-00068-1000px.png)<br>
*Beispiel für die Überprüfung*

Die Art dieser Überprüfung Erfahrung kann je nach den Anforderungen jeder Anwendung erheblich variieren, aber zwei wichtigste Prinzipien sollte den Entwurf geführt.

Erstens **klare Kommunikation mit dem Benutzer gehört primär zum Aufgabenbereich**. Der Benutzer sollte immer bekannt, ob der Anwendung erfüllt sind. Wenn sie nicht erfüllt werden, sollte es sein, die dem Benutzer sofort klar warum dies rührt daher, und sie sollten schnell die entsprechenden Maßnahmen ergreifen, geführt werden.

Zweitens **Anwendungen sollten versuchen, ein Gleichgewicht zwischen Effizienz und Zuverlässigkeit**. Wann ist das Vorgehen möglich **zuverlässig**, Anwendungen sollten automatisch Daten analysieren, räumliche Zuordnung um den Benutzerzeit zu sparen. Wenn es nicht zuverlässig vorgehen möglich ist, sollten Anwendungen stattdessen ermöglichen den Benutzer die Anwendung mit den zusätzlichen Informationen schnell bereitstellen, die erforderlichen.

Um das Recht, die Überprüfung Erfahrung gestalten, beachten Sie, welche der folgenden Möglichkeiten für Ihre Anwendung gelten:

* **Keine Überprüfung-Benutzeroberfläche**
   * Eine Anwendung kann ohne jede Überprüfung geführte perfekt ausgeführt werden; Sie erhalten Informationen zur Flächen, die im Verlauf der natürlichen Bewegung beobachtet werden.
   * Beispielsweise muss eine Anwendung, die dem Benutzer, die auf Flächen mit holographic Spraypaint zeichnen kann wissen nur die Flächen, die derzeit für den Benutzer sichtbar.
   * Die Umgebung kann vollständig bereits gescannt werden, wenn diese ist in der der Benutzer bereits viel Zeit mit der HoloLens aufgewendet hat.
   * Bedenken Sie jedoch, dass die Kamera ein, die räumliche Zuordnung nur sehen kann 3.1m vor dem Benutzer, und räumliche Zuordnung zu beliebigen mehr entfernten Flächen nicht vertraut sind, es sei denn, der Benutzer sie aus der näher Entfernung in der Vergangenheit beobachtet hat.
   * Der Benutzer verstehen, welche Flächen überprüft worden sind, die Anwendung soll visuelles Feedback zu diesem Zweck, z. B. umwandeln virtuelle Schatten auf gescannte Oberflächen kann dem Benutzer ermöglichen, Hologramme auf diese Oberflächen zu platzieren.
   * Für diesen Fall muss der räumlichen Oberfläche Beobachter umgebende Volumes aktualisiert Sie jeden Frame ein Text-gesperrt [räumliche Koordinatensystem](coordinate-systems.md), sodass sie den Benutzer folgen.

* **Suchen Sie einen geeigneten Speicherort**
   * Eine Anwendung kann für die Verwendung an einem Ort mit bestimmten Anforderungen entworfen werden.
   * Z. B. möglicherweise die Anwendung einen leeren Bereich, um den Benutzer erfordert, damit sie problemlos holographic Kung-fu üben können.
   * Anwendungen sollten die besonderen Anforderungen an den Benutzer, die im Vorfeld zu kommunizieren, und löschen visuelles Feedback zu verstärken.
   * In diesem Beispiel sollte die Anwendung das Ausmaß der erforderlichen leeren Fläche zu visualisieren und visuell markieren Sie alle unerwünschten Objekte innerhalb dieser Zone vorhanden.
   * Für diesen Fall sollte der räumlichen Oberfläche Beobachter umgebende Volumes verwenden, ein World gesperrt [räumliche Koordinatensystem](coordinate-systems.md) am ausgewählten Speicherort.

* **Suchen Sie eine geeignete Konfiguration von surfaces**
   * Eine Anwendung eine bestimmte Konfiguration von Oberflächen, z. B. zwei große flach, unter Umständen gegensätzlichen Wände zum Erstellen einer holographic Hall spiegeln.
   * In solchen Fällen muss die Anwendung zum Analysieren von der Oberflächen von räumliche Zuordnung geeignete Flächen erkennen, und weisen Sie den Benutzer für sie bereitgestellt.
   * Der Benutzer muss eine Fallbackoption verfügen, wenn die Analyse der Anwendung nicht komplett zuverlässig ist. Wenn die Anwendung fälschlicherweise einen Zugangspunkt als eine flache Lasche identifiziert, benötigt der Benutzer z. B. eine einfache Möglichkeit, diesen Fehler zu beheben.

* **Überprüfen Sie in der Umgebung**
   * Eine Anwendung sollten nur in der Umgebung, zu erfassen, wie vom Benutzer angegeben.
   * Die Anwendung scannt z. B. Teil eines Raums, damit der Benutzer eine Anzeige für Möbel holographic bereitstellen kann, die sie verkaufen möchten.
   * In diesem Fall sollte die Anwendung räumliche Zuordnung von Daten in den Regionen, die vom Benutzer während der Überprüfung der beobachteten erfassen.

* **Überprüfen Sie den gesamten Raum**
   * Eine Anwendung kann eine Überprüfung aller Flächen im aktuellen Raum, einschließlich der hinter dem Benutzer erfordern.
   * Z. B. festlegen ein Spiels kann die Benutzer in der Rolle des Gulliver, unter Siege aus Hunderten von kleinen Lilliputians annähert, die aus allen Richtungen.
   * In solchen Fällen müssen die Anwendung zu bestimmen, wie viele der Flächen, die in der aktuellen Platz wurden bereits gescannt und die Weiterleitung des Benutzers Blicke um bedeutende Lücken zu füllen.
   * Dieser Prozess stellt visuelles Feedback bereit, das eindeutig, auf dem Benutzer ermöglicht die Flächen noch nicht überprüft wurden. Die Anwendung können z. B. [Abstand-basierten Nebel](https://msdn.microsoft.com/library/windows/desktop/bb173401%28v=vs.85%29.aspx) Regionen visuell zu markieren, die nicht durch räumliche Zuordnung Flächen abgedeckt sind.

* **Eine anfängliche Momentaufnahme der Umgebung**
   * Eine Anwendung sollten alle Änderungen in der Umgebung unter Berücksichtigung der anfängliche 'Snapshot' ignoriert werden sollen.
   * Dies eignet sich möglicherweise um eine Unterbrechung der benutzererstellte Daten zu vermeiden, die auf den Ausgangszustand der Umgebung, eng gekoppelt ist.
   * In diesem Fall sollte die Anwendung eine Kopie der Daten räumliche Zuordnung in seinen ursprünglichen Zustand vornehmen, nachdem die Überprüfung abgeschlossen ist.
   * Anwendungen müssen weiterhin Updates räumliche Zuordnungsdaten empfangen, wenn Hologramme sind immer noch von der Umgebung ordnungsgemäß okkludierte werden.
   * Kontinuierliche Updates räumliche Zuordnungsdaten können auch alle Änderungen, die aufgetreten sind, Klärung, die dem Benutzer die Unterschiede zwischen früheren und aktuellen Status der Umgebung visualisieren.

* **Vom Benutzer initiierte Momentaufnahmen der Umgebung**
   * Eine Anwendung kann nur auf, wenn Sie durch den Benutzer dazu auf umgebungsänderungen reagieren möchten.
   * Beispielsweise kann der Benutzer mehrere 3D "Statuen" von einem Freund erstellen, durch das Erfassen ihrer ist in verschiedenen Situationen Werbebotschaften.

* **Ermöglicht dem Benutzer, die Umgebung zu ändern**
   * Eine Anwendung kann so entworfen werden, reagieren, dass Änderungen in Echtzeit in der Umgebung des Benutzers vorgenommen.
   * Beispielsweise kann der Benutzer eine Kulissen Zeichnen "Szene ändern" für eine holographic, die stattfinden, auf der anderen Seite Play auslösen.

* **Führen Sie den Benutzer zur Vermeidung von Fehlern in den Daten für die räumliche Zuordnung**
   * Eine Anwendung kann die Anleitungen für den Benutzer bereitstellen, während sie ihre Umgebung scannen möchten.
   * Damit kann den Benutzer nicht bestimmte Arten von [Fehler in den Daten für die räumliche Zuordnung](spatial-mapping-design.md#what-influences-spatial-mapping-quality), z. B. durch von sunlit Windows- oder Spiegel bleiben.

Eine weitere Details zu beachten ist, dass die "Range" räumliche Zuordnung Daten nicht unbegrenzt ist. Dabei wird die räumliche Zuordnung eine dauerhafte Datenbank mit großen Speicherplätze erstellt werden kann, ist es nur Daten für Anwendungen verfügbar, in eine Blase begrenzte Größe für den Benutzer. Also, wenn Sie am Anfang einer langen Gang und Walk weit weg von Anfang starten, und dann schließlich wieder an den Anfang die räumlichen Flächen werden ausgeblendet. Sie können natürlich entgegenzuwirken diese Oberflächen in Ihrer Anwendung zwischenspeichern, nachdem sie aus den verfügbaren räumliche Zuordnungsdaten verschwunden sind.

## <a name="mesh-processing"></a>Mesh-Verarbeitung

Es kann hilfreich sein, um allgemeine Arten von Fehlern in Flächen zu erkennen und zu filtern, entfernen oder ändern die räumliche Zuordnungsdaten nach Bedarf.

Beachten Sie die räumliche Zuordnung, die Daten als treuen wie möglich zu echten Flächen werden soll, sodass verarbeiten Sie Risiken, die Verschiebung von der Flächen das Gegenteil ist' ' anwenden.

Hier sind einige Beispiele verschiedener Arten von Gitter zu verarbeiten, nützlich sein können:

* **Lücke füllen**
   * Wenn ein kleines Objekt, aus der ein dunkles Material nicht überprüfen, verbleibt es eine Lücke in der umgebenden Oberfläche.
   * Lücken beeinflussen verdecken: Hologramme "durch" eine Lücke in eine angeblich nicht transparente realen Oberfläche angezeigt werden können.
   * Lücken beeinflussen Raycasts: Wenn Sie für Benutzer interagieren mit Flächen Raycasts verwenden, ist es möglicherweise nicht wünschenswert, dass diese Strahlung Löcher passieren. Eine Lösung ist eine Zusammenstellung von mehreren Raycasts für einer Region geeigneter Größe zu verwenden. Dadurch können Sie zum Filtern von Ergebnissen "Ausreißer", sodass auch, wenn eine kleine Öffnung einer Raycast durchläuft das aggregierte Ergebnis immer noch gültig sein soll. Bedenken Sie jedoch, dass dieser Ansatz zu rechenleistung Kosten hat.
   * Lücken Auswirkungen Physik Konflikte auf: ein Objekt, das durch die Physiksimulation gesteuert durch eine Lücke in der Boden löschen und unterbrochen werden kann.
   * Es ist möglich, um solche Lücken in der Entwurfsoberfläche Mesh algorithmisch zu füllen. Allerdings müssen Sie einen Algorithmus zu optimieren, sodass "echten Löcher", wie z. B. Windows und Doorways nicht ausgefüllt werden. Kann es auch schwierig, "real Lücken" aus "imaginären Löcher" zuverlässig zu unterscheiden sein, daher Sie zum Experimentieren mit anderen Heuristik beim Ermitteln, wie z. B. "Size müssen" und "Form" Grenze "".

* **Hallucination entfernen**
   * Reflexionen, Lichtern und das Verschieben von Objekten können kleine veraltete "Wahnvorstellungen" floating hüpfen lassen.
   * Wahnvorstellungen beeinflussen verdecken: Wahnvorstellungen können als dunkle Formen verschieben vor und andere Hologramme occluding angezeigt werden.
   * Wahnvorstellungen beeinflussen Raycasts: Wenn Sie den Raycasts verwenden, können Benutzer mit Flächen interagieren, konnte diese Strahlung eine Hallucination anstelle der Oberfläche des zugrunde liegenden erreicht. Wie bei Löcher, eine Lösung ist die Verwendung von vielen Raycasts anstelle einer einzelnen Raycast, aber erneut dies rechenleistung Kosten kommen.
   * Wahnvorstellungen beeinflussen die Physik Konflikte: ein Objekt, das durch die Physiksimulation gesteuert für eine Hallucination unterbrochen werden kann und nicht über einen Bereich scheinbar clear Speicherplatz verschieben.
   * Es ist möglich, die solche Wahnvorstellungen Oberfläche Mesh zu filtern. Aber wie bei Löcher, müssen Sie einen Algorithmus zu optimieren, damit, echte kleine, z. B. Lamp-steht Objekte und die Tür Handles werden nicht entfernt.

* **Glättung**
   * Räumliche Zuordnung kann Flächen zurückgeben, die raue oder "noisy" im Vergleich zu ihren realen Entsprechungen zu sein scheinen.
   * Einfachheit wirkt sich auf die Physik Konflikte: ist der Boden grobe, ein Ball physisch simulierten Golf kann kein Rollback reibungslos über die sie in einer geraden Linie.
   * Einfachheit wirkt sich auf Rendering: Wenn Sie eine Fläche, die direkt in der sichtbar gemacht wird, grobe Oberflächennormale wirken sich auf die Darstellung und einen Blick "bereinigen" unterbrechen können. Es ist möglich, verringern diese mit entsprechenden Beleuchtung und Texturen in der Shader, der zum Rendern der Entwurfsoberfläche verwendet wird.
   * Es ist möglich, Rauigkeit in einem Surface-Mesh zu glätten. Allerdings kann dies die Oberfläche von der entsprechenden realen Oberfläche übertragen. Verwalten eine schließende-Entsprechung ist wichtig, um genaue – Hologramm verdecken zu erzeugen, und Benutzer, präzise und vorhersagbare Interaktionen mit holographic Flächen zu erreichen.
   * Wenn nur eine oberflächliche erforderlich ist, kann es ausreichen, um den Vertex Normals smooth ohne Vertexpositionen sein.

* **Ebene suchen**
   * Es gibt viele Formen der Analyse, die eine Anwendung auf den Flächen, die räumliche Zuordnung gebotenen ausführen möchten.
   * Ein einfaches Beispiel ist 'Suchen von Verwaltungsebene'; Identifizieren gebundene, vor allem planare Bereiche von Oberflächen.
   * Planare Regionen können als holographic Arbeit-Flächen Regionen verwendet werden, in denen holographic Inhalt automatisch von der Anwendung platziert werden kann.
   * Planare Regionen können einschränken, die Benutzeroberfläche, unterstützen die Benutzer für die Interaktion mit den Oberflächen, am besten ihren Anforderungen entsprechend.
   * Planare Regionen können wie in der realen Welt für holographic Gegenstücke zu Funktionsobjekten z. B. LCD-Bildschirme, Tabellen oder Whiteboards verwendet werden.
   * Planare Regionen können Play Bereiche, bildet die Basis der Videogame Ebenen definieren.
   * Planare Regionen können virtuellen Agents die realen Welt navigieren, indem Sie identifizieren, die Bereiche der Boden, die echte Menschen wahrscheinlich auf durchlaufen hilfreich sein.

## <a name="prototyping-and-debugging"></a>Erstellen von Prototypen und Debuggen

### <a name="useful-tools"></a>Nützliche tools
* Die [Emulator für HoloLens](using-the-hololens-emulator.md) zum Entwickeln von Anwendungen, die räumliche Zuordnung ohne Zugriff auf eine physische HoloLens mit verwendet werden können. Sie können eine live-Sitzung auf einem HoloLens in einer realistischen Umgebung zu simulieren, mit dem alle Daten Ihrer Anwendung würde normalerweise nutzen, einschließlich HoloLens während der Übertragung, räumliche Koordinatensysteme und räumliche Zuordnung Gitter. Dies kann verwendet werden, zuverlässigen und wiederholbaren-Eingabe bereitstellen, das für das Debuggen von Problemen, und Evaluieren von Änderungen an Ihrem Code hilfreich sein können.
* Um eine Szenarien zu reproduzieren, räumliche Zuordnung Datenerfassung über das Netzwerk mit einer live HoloLens, und dann speichern, um auf den Datenträger und in nachfolgenden Debugsitzungen wiederzuverwenden.
* Die [Windows Device Portal 3D-Ansicht](using-the-windows-device-portal.md#3d-view) bietet eine Möglichkeit, alle der räumlichen Flächen, die derzeit verfügbaren über das System für die räumliche Zuordnung anzuzeigen. Dies bietet eine Grundlage des Vergleichs an, für die räumlichen Flächen in Ihrer Anwendung; Beispielsweise können Sie leicht erkennen, wenn alle räumlichen Flächen fehlen oder in der falschen Stelle angezeigt wird sind.

### <a name="general-prototyping-guidance"></a>Allgemeine Prototyping-Anleitungen
* Da [Fehler](spatial-mapping-design.md#what-influences-spatial-mapping-quality) in der Zuordnung des räumlichen Daten stark beeinträchtigen die Erfahrung des Benutzers, es wird empfohlen, dass Sie Ihre Anwendung in einer Vielzahl von Umgebungen testen.
* Gefangen Sie nicht abrufen gewöhnlich Tests immer am gleichen Speicherort, z. B. an Ihrem Schreibtisch auf. Stellen Sie sicher, dass auf verschiedenen Oberflächen von verschiedenen Positionen, Formen, Größen und Materialien zu testen.
* Entsprechend synthetische oder die aufgezeichnete Daten können beim Debuggen hilfreich sein, werden Sie nicht auch die gleichen einige Testfälle abhängig. Dies kann eine Verzögerung finden wichtige Probleme, die mehrere verschiedene Tests früher abgefangen wird.
* Es ist eine gute Idee, führen Sie Tests mit realen (und idealerweise nicht betreuten)-Benutzer, da sie nicht die HoloLens oder die Anwendung auf genau die gleiche Weise verwenden können, die Sie ausführen. In der Tat können vielleicht überrascht es Sie wie divergente geweckt Verhalten, wissen und Annahmen!

## <a name="see-also"></a>Siehe auch
* [Raumabtastvisualisierung](room-scan-visualization.md)
* [Raumklangentwurf](spatial-sound-design.md)
* [Persistenz in Unity](persistence-in-unity.md)
