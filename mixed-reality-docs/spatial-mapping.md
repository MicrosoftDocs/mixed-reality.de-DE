---
title: Räumliche Zuordnung
description: Die räumliche Zuordnung bietet eine ausführliche Darstellung realer Oberflächen in der Umgebung um die hololens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: räumliche Zuordnung, hololens, gemischte Realität, Oberflächenrekonstruktion, Mesh
ms.openlocfilehash: 2988056b5caf50a4428d39c725bfe5432867a9c0
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437457"
---
# <a name="spatial-mapping"></a>Räumliche Zuordnung

Die räumliche Zuordnung bietet eine detaillierte Darstellung der realen Oberflächen in der Umgebung in Bezug auf die hololens, sodass Entwickler eine überzeugende gemischte Realität schaffen können. Durch die Zusammenführung der realen Welt mit der virtuellen Welt kann eine Anwendung dazu führen, dass Hologramme in der Praxis erscheinen. Anwendungen können auch mit den Erwartungen von Benutzern vertraut werden, indem Sie vertraute reale Verhaltensweisen und Interaktionen bereitstellen.

<br>

>[!VIDEO https://www.youtube.com/embed/zff2aQ1RaVo]

## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Feature</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Räumliche Zuordnung</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>


## <a name="why-is-spatial-mapping-important"></a>Warum ist die räumliche Zuordnung wichtig?

Räumliche Zuordnung macht es möglich, Objekte auf realen Oberflächen zu platzieren. Dies hilft bei der Verankerung von Objekten in der Benutzer Welt und nutzt die Vorteile der tatsächlichen tiefen Hinweise. Das Verwahren von holograms auf der Grundlage von anderen holograms und realen Objekten hilft dem Benutzer zu überzeugen, dass sich diese Hologramme tatsächlich in Ihrem Bereich befinden. Hologramme, die leer sind oder sich mit dem Benutzer bewegen, werden nicht als Real angezeigt. Platzieren Sie Elemente nach Möglichkeit aus Gründen der Bequemlichkeit.

Visualisieren von Oberflächen beim platzieren oder Verschieben von holograms (Verwenden eines einfachen projizierten Rasters). Dadurch kann der Benutzer wissen, wo er seine Hologramme am besten platzieren kann. der Benutzer wird angezeigt, wenn die Stelle, an der er das – Hologramm platzieren möchte, noch nicht zugeordnet wurde. Sie können für den Benutzer "Billboard Items" hinzufügen, wenn er zu viel Winkel hat.

## <a name="conceptual-overview"></a>Konzeptionelle Übersicht

![Gitter Flächen, die einen Raum abdecken](images/SurfaceReconstruction.jpg)<br>
*Ein Beispiel für eine räumliche Zuordnung, die einen Raum abdeckt*

Die beiden primären Objekttypen, die für die räumliche Zuordnung verwendet werden, sind der räumliche Oberflächen Beobachter und die räumliche Oberfläche.

Die Anwendung stellt einem oder mehreren umgebenden Volumes die räumliche Oberfläche bereit, um die Bereiche zu definieren, in denen die Anwendung räumliche Mapping-Daten empfangen möchte. Für jedes dieser Volumes stellt die räumliche Zuordnung der Anwendung einen Satz räumlicher Oberflächen zur Verfügung.

Diese Volumes sind möglicherweise stationär (an einem bestimmten Speicherort in Bezug auf die reale Umgebung), oder Sie sind möglicherweise an die hololens angefügt (Sie verschieben, aber nicht drehen, während Sie durch die Umgebung bewegt werden). Jede räumliche Oberfläche beschreibt reale Oberflächen auf einer kleinen Menge von Speicherplatz, dargestellt als Dreiecks Gitter, das einem weltweit gesperrten [räumlichen Koordinatensystem](coordinate-systems.md)zugeordnet ist.

Da hololens neue Daten über die Umgebung sammelt und Änderungen an der Umgebung auftreten, werden räumliche Oberflächen angezeigt, verschwinden und ändern.

## <a name="spatial-mapping-vs-scene-undesranding-worldmesh"></a>Räumliche Zuordnung im Vergleich zu Szenen, die das worldmesh deinstaleren
Bei hololens 2 ist es möglich, eine statische Version der räumlichen Mapping-Daten mithilfe der [Scene Understanding SDK](scene-understanding-SDK.md) (enableworldmesh-Einstellung) abzufragen. Im folgenden finden Sie die Unterschiede zwischen zwei Möglichkeiten, auf die räumlichen Zuordnungsdaten zuzugreifen:
* Räumliche Mapping-API:
   * Begrenzter Bereich: die räumlichen Daten, die für Anwendungen in einer begrenzten Größe, die für den Benutzer zwischengespeichert ist, verfügbar sind.
   * Ermöglicht das Aktualisieren von geänderten Netzbereichen durch Ereignisse mit geringer Latenzzeit über Ereignisse, die über ein Ereignis verfügen.
   * Variable Ebene von Details, die von Dreiecken pro Kubikmeter Parameter gesteuert werden.
* Nicht aufstehendes SDK der Szene:
   * Unbegrenzter Bereich: stellt alle überprüften räumlichen Mapping-Daten im Abfrage RADIUS bereit.
   * Stellt eine statische Momentaufnahme der räumlichen Mapping-Daten bereit. Um die aktualisierten räumlichen Zuordnungsdaten zu erhalten, muss eine neue Abfrage für das gesamte Mesh ausgeführt werden.
   * Konsistente Detailebene, die von der requestedmeshlevelofdetail-Einstellung gesteuert wird.

## <a name="what-influences-spatial-mapping-quality"></a>Was beeinflusst die Qualität der räumlichen Zuordnung?

Mehrere [hier](environment-considerations-for-hololens.md)ausführliche Faktoren können die Häufigkeit und den Schweregrad dieser Fehler beeinflussen.  Allerdings sollten Sie Ihre Anwendung so entwerfen, dass der Benutzer auch bei Fehlern in den räumlichen Daten der Zuordnung seine Ziele erreichen kann.

## <a name="common-usage-scenarios"></a>Allgemeine Verwendungsszenarios

![Abbildungen allgemeiner Verwendungs Szenarien für räumliche Zuordnung: Platzierung, oksion, Physik und Navigation](images/sm-concepts-1000px.png)

### <a name="placement"></a>Platzierung

Die räumliche Zuordnung bietet Anwendungen die Möglichkeit, dem Benutzer natürliche und vertraute Formen der Interaktion darzustellen. Was könnte natürlicher sein, als wenn Sie Ihr Telefon auf den Schreibtisch bringen?

Durch die Beschränkung der Platzierung von holograms (oder allgemeiner, einer beliebigen Auswahl räumlicher Standorte) auf Oberflächen wird eine natürliche Zuordnung von 3D (Punkt in Raum) zu 2D (Punkt auf der Oberfläche) bereitstellt. Dadurch wird die Menge der Informationen verringert, die der Benutzer für die Anwendung bereitstellen muss, sodass die Interaktionen des Benutzers schneller, einfacher und präziser werden. Dies trifft vor allem dann zu, wenn es sich bei "Distance Away" nicht um eine physische Kommunikation mit anderen Personen oder Computern handelt. Wenn wir mit unserem Finger zeigen, geben wir eine Richtung, aber keinen Abstand an.

Ein wichtiger Nachteil hierbei ist Folgendes: Wenn eine Anwendung eine Entfernung von der Richtung ableitet (z. b. durch Ausführen eines Raycasts entlang der Betrachtung des Benutzers, um die nächstgelegene räumliche Oberfläche zu finden), muss dies Ergebnisse liefern, die der Benutzer zuverlässig vorhersagen kann. Andernfalls verliert der Benutzer das Steuerelement, und dies kann schnell frustrierend werden. Eine Methode, die dies unterstützt, ist die Ausführung mehrerer Raycasts anstelle von nur einer. Die Aggregat Ergebnisse sollten glatter und besser vorhersagbar und weniger anfällig für den Einfluss vorübergehender "ausreißender" Ergebnisse sein (Dies kann durch Strahlen verursacht werden, die durch kleine Löcher laufen oder kleine Bits von Geometrie erreichen, denen der Benutzer nicht bewusst ist). Aggregationen oder Glättung können auch im Laufe der Zeit ausgeführt werden. Beispielsweise können Sie die maximale Geschwindigkeit begrenzen, mit der ein – Hologramm vom Benutzer in der Entfernung variieren kann. Die Beschränkung des minimalen und maximalen Entfernungs Werts kann auch hilfreich sein, sodass das verschobene – Hologramm nicht plötzlich in den Weg geht oder zurück stürzt.

Anwendungen können auch die Form und die Richtung der Oberflächen verwenden, um die Platzierung von holograms zu steuern. Ein holografischer Stuhl sollte nicht durch Wände dringen und auch dann mit dem Boden leeren, wenn er etwas ungleich ist. Diese Art von Funktionalität basiert wahrscheinlich auf der Verwendung von Physik-Kollisionen anstelle von "Raycasts", aber es treten ähnliche Bedenken auf. Wenn das zu platzierende – Hologramm viele kleine Polygone aufweist, die sich wie die Beine auf einem Stuhl befinden, kann es sinnvoll sein, die Physik Darstellung dieser Polygone auf etwas breiteres und glatteres zu erweitern, sodass Sie mehr über räumliche Flächen ohne Wikihosting.

Im äußersten Fall kann die Benutzereingabe vollständig vereinfacht werden, und räumliche Oberflächen können verwendet werden, um eine vollständige automatische – Hologramm-Platzierung auszuführen. Beispielsweise könnte die Anwendung einen Holographic Light-Switch irgendwo auf der Wand platzieren, auf die der Benutzer klicken kann. Der gleiche Nachteil bei der Vorhersagbarkeit gilt hier doppelt. Wenn der Benutzer die Kontrolle über die – Hologramm-Platzierung erwartet, die Anwendung jedoch nicht immer holograms platziert, wo Sie erwartet werden (wenn der helle Switch irgendwo angezeigt wird, dass der Benutzer nicht erreichbar ist), ist dies ein frustrierender Vorgang. Es kann sogar schlimmer sein, eine automatische Platzierung auszuführen, bei der die Benutzer Korrektur einiger Zeit erforderlich ist. Da eine erfolgreiche automatische Platzierung *erwartet*wird, ist die manuelle Korrektur eine Belastung.

Beachten Sie außerdem, dass die Fähigkeit einer Anwendung, räumliche Oberflächen für die Platzierung zu verwenden, stark vom [Scan](spatial-mapping.md#the-environment-scanning-experience)Vorgang der Anwendung abhängt. Wenn eine Oberfläche nicht gescannt wurde, kann Sie nicht für die Platzierung verwendet werden. Es ist für die Anwendung von der Anwendung, dies für den Benutzer klar zu machen, damit Sie entweder neue Oberflächen Scannen oder einen neuen Speicherort auswählen können.

Das visuelle Feedback an den Benutzer ist bei der Platzierung von größter Wichtigkeit. Der Benutzer muss wissen, wo sich das – Hologramm in Bezug auf die nächstgelegene Oberfläche mit [Erden Effekten](spatial-mapping.md#visualization)befindet. Sie sollten verstehen, warum die Verschiebung ihres holograms eingeschränkt wird (z. b. aufgrund eines Konflikts mit einer anderen nahe gelegenen Oberfläche). Wenn Sie am aktuellen Speicherort kein – Hologramm platzieren können, sollte das visuelle Feedback den Grund dafür verdeutlichen, warum dies nicht der Fall ist. Wenn der Benutzer z. b. versucht, eine Holographic-Couch in der Wand zu platzieren, sollte sich die Teile der Couch, die sich hinter der Wand befinden, in einer wütenden Farbe durchlaufen. Wenn die Anwendung dagegen keine räumliche Oberfläche an einem Speicherort findet, an dem der Benutzer eine reale Oberfläche sehen kann, sollte die Anwendung dies klar machen. Das offensichtliche Fehlen eines Erden Effekts in diesem Bereich kann diesen Zweck erfüllen.

### <a name="occlusion"></a>Okklusion

Eine der Haupt Verwendungsmöglichkeiten räumlicher Mapping-Oberflächen besteht darin, die holograms einfach zu okzieren. Dieses einfache Verhalten hat eine große Auswirkung auf die wahrgenommene Bedeutung von holograms und hilft dabei, einen viskoen Sinn zu schaffen, der tatsächlich denselben physischen Raum wie der Benutzer hat.

Die Okklusion stellt dem Benutzer auch Informationen zur Verfügung. Wenn ein – Hologramm von einer realen Oberfläche verdeckt wird, bietet dies ein zusätzliches visuelles Feedback zum räumlichen Speicherort dieses holograms weltweit. Umgekehrt kann die Okklusion auch Informationen vom Benutzer *Einblenden* . durch das Durchlaufen von holograms hinter den Wänden kann der visuelle Cluster auf intuitive Weise reduziert werden. Um ein Hologram auszublenden oder anzuzeigen, muss der Benutzer lediglich seine Kopfzeile verschieben.

Die Okklusion kann auch verwendet werden, um die Erwartungen an eine natürliche Benutzeroberfläche basierend auf vertrauten physischen Interaktionen zu formulieren. Wenn ein – Hologramm durch eine Oberfläche verdeckt wird, liegt dies daran, dass diese Oberfläche solide ist, sodass der Benutzer erwarten kann, dass das – Hologramm *mit dieser* Oberfläche in Konflikt steht und nicht einfach durchlaufen wird.

Manchmal ist eine Okklusion von holograms nicht erwünscht. Wenn ein Benutzer in der Lage sein muss, mit einem Hologram zu interagieren, muss er in der Lage sein, ihn zu sehen, auch wenn er sich hinter einer realen Oberfläche befindet. In solchen Fällen ist es in der Regel sinnvoll, ein solches Hologramm anders zu gestalten, wenn es ausgeblendet wird (z. b. durch verringern seiner Helligkeit). Auf diese Weise wird der Benutzer in der Lage sein, das Hologramm visuell zu finden, aber es ist immer noch bewusst, dass es sich hinter etwas befindet.

### <a name="physics"></a>Mikro

Die Verwendung der Physik Simulation ist eine andere Möglichkeit, mit der räumliche Zuordnung das *vorhanden* sein von holograms im physischen Raum des Benutzers zu verstärken. Wenn meine holografische Gummikugel aus meinem Schreibtisch abspringt, auf den Boden springt und unter dem Couch verschwindet, kann es schwierig sein, zu glauben, dass Sie nicht wirklich vorhanden ist.

Die Physik-Simulation bietet auch eine Möglichkeit für eine Anwendung, natürliche und vertraute, auf der Physik basierende Interaktionen zu verwenden. Das Verschieben von Holographic-Möbeln auf der Bodenfläche ist für den Benutzer wahrscheinlich einfacher, wenn die Möbel so reagieren, als ob Sie im Boden mit der entsprechenden Trägheit und der Reibung bewegt werden würden.

Um realistisches physisches Verhalten zu generieren, müssen Sie wahrscheinlich einige [Gitter Verarbeitungs](spatial-mapping.md#mesh-processing) Vorgänge ausführen, wie z. b. das Füllen von Löchern, das Entfernen von Gleit Komma Zuordnungen und das Glätten von groben Oberflächen.

Außerdem müssen Sie Bedenken, wie sich die [scannerart](spatial-mapping.md#the-environment-scanning-experience) Ihrer Anwendung auf die Physik Simulation auswirkt. Erstens können fehlende Oberflächen nicht mit etwas kollidieren. Was geschieht, wenn der Gummi Ball in den Korridor und am Ende der bekannten Welt aufrollt? Zweitens müssen Sie entscheiden, ob Sie im Laufe der Zeit weiterhin auf Änderungen in der Umgebung reagieren werden. In einigen Fällen möchten Sie so schnell wie möglich reagieren. nehmen wir beispielsweise an, wenn der Benutzer Türen und Möbel als bewegliche Barrikaden verwendet, um sich gegen eine Tempest eingehender römischer Pfeile zu verteidigen. In anderen Fällen möchten Sie jedoch möglicherweise neue Updates ignorieren. Es ist möglicherweise plötzlich nicht so unterhaltsam, dass Ihr Holographic Sport Car um die Rennstrecke im Boden unterwegs ist.

### <a name="navigation"></a>Navigation

Anwendungen können räumliche Zuweisungs Daten verwenden, um holografischen Zeichen (oder Agents) die Möglichkeit zur Navigation in der realen Welt auf dieselbe Weise wie eine echte Person zu gewähren. Dies kann dazu beitragen, das vorhanden sein von Holographic-Zeichen zu verstärken, indem Sie auf denselben natürlichen, vertrauten Verhalten wie die des Benutzers und der Freunde beschränkt werden.

Navigationsfunktionen können auch für Benutzer nützlich sein. Nachdem eine Navigations Zuordnung in einem bestimmten Bereich erstellt wurde, kann Sie freigegeben werden, um für neue Benutzer, die mit diesem Standort nicht vertraut sind, holografische Anleitungen bereitzustellen. Diese Karte könnte so entworfen werden, dass der Datenverkehr der Fußgänger reibungslos verläuft, oder es werden Fehler an gefährlichen Standorten wie bausites vermieden.

Die wichtigsten technischen Herausforderungen bei der Implementierung der Navigations Funktionalität sind die zuverlässige Erkennung von begewaybaren Oberflächen (Menschen werden nicht auf Tabellen hin) und die ordnungsgemäße Anpassung an die Änderungen in der Umgebung (Menschen werden nicht durch geschlossene Türen durchlaufen!). Das Mesh erfordert möglicherweise einige [Verarbeitungs](spatial-mapping.md#mesh-processing) Vorgänge, bevor es für die Pfad Planung und die Navigation durch ein virtuelles Zeichen verwendet werden kann. Das Glättung des Netzes und Entfernen von Zuordnungen kann dazu beitragen, dass Zeichen nicht mehr hängen. Möglicherweise möchten Sie das Mesh auch drastisch vereinfachen, um die Pfad-und Navigations Berechnungen Ihres Zeichens zu beschleunigen. Diese Herausforderungen haben bei der Entwicklung von Videogame-Technologie viel Aufmerksamkeit geschenkt, und es gibt eine Vielzahl von Forschungsliteratur zu diesen Themen.

Beachten Sie, dass die integrierte navmesh-Funktionalität in Unity nicht mit räumlichen zuordnungsoberflächen verwendet werden kann. Dies liegt daran, dass räumliche Zustellungs Oberflächen erst bekannt sind, wenn die Anwendung gestartet wird, wohingegen navmesh-Datendateien vorab aus quellassets generiert werden müssen. Beachten Sie auch, dass das räumliche Mapping-System keine [Informationen über Oberflächen](spatial-mapping.md#the-environment-scanning-experience) bereitstellt, die sich weit entfernt von der aktuellen Position des Benutzers befinden. Daher muss die Anwendung "erinnern", wenn Sie eine Karte eines sehr großen Bereichs erstellen soll.

### <a name="visualization"></a>Visualisierung

In den meisten Fällen ist es sinnvoll, räumliche Oberflächen unsichtbar zu machen. zum Minimieren des visuellen Clutters und zum sprechen der realen Welt. Manchmal ist es jedoch sinnvoll, räumliche zuordnungsoberflächen direkt visuell darzustellen, trotz der Tatsache, dass ihre realen Gegenstücke bereits sichtbar sind.

Wenn der Benutzer z. b. versucht, ein Hologramm auf einer Oberfläche zu platzieren (z. b. eine holografische CAB-Datei), kann es hilfreich sein, das Hologramm zu "Durchsuchen", indem es einen Schatten auf die Oberfläche wirft. Dadurch erhält der Benutzer einen deutlich besseren Eindruck von der exakten physischen Nähe zwischen dem – Hologramm und der-Oberfläche. Dies ist auch ein Beispiel für die allgemeinere Vorgehensweise bei einer visuellen Vorschau einer Änderung, bevor der Benutzer einen Commit dafür durchführt.

Durch die Visualisierung von Oberflächen kann die Anwendung für den Benutzer freigegeben werden, um die Umgebung zu verstehen. Beispielsweise könnte ein Holographic Board-Spiel die horizontalen Oberflächen visualisieren, die es als "Tables" identifiziert hat, sodass der Benutzer weiß, wo er interagieren soll.

Die Visualisierung von Oberflächen kann eine nützliche Möglichkeit darstellen, um den Benutzern nahe gelegene Bereiche anzuzeigen, die in der Ansicht ausgeblendet sind. Dies könnte eine einfache Möglichkeit bieten, dem Benutzer den Zugriff auf seine Küche (und alle darin enthaltenen Hologramme) aus dem Wohnraum zu ermöglichen.

Die von der räumlichen Zuordnung bereitgestellten Oberflächen Netze sind möglicherweise nicht besonders "Clean". Daher ist es wichtig, diese entsprechend visuell darzustellen. Bei herkömmlichen Beleuchtungsberechnungen werden möglicherweise Fehler in Oberflächen normalen in visuell ablenkend hervorgehoben, während "saubere" Texturen, die auf die Oberfläche projiziert werden, dazu beitragen können, dass Sie eine mehrstufige Darstellung erhalten. Es ist auch möglich, die Gitter [Verarbeitung](spatial-mapping.md#mesh-processing) durchzuführen, um Gitter Eigenschaften zu verbessern, bevor die Oberflächen gerendert werden.

> [!NOTE]
> Hololens 2 implementiert eine neue [Szene zum Verständnis der Laufzeit](scene-understanding.md), die Entwicklern gemischter Realität eine strukturierte, hochwertige Umgebungs Darstellung bietet, die zur Vereinfachung der Implementierung von Platzierung, Okklusion, Physik und Navigation konzipiert ist.

## <a name="using-the-surface-observer"></a>Verwenden des Oberflächen Beobachters

Der Ausgangspunkt für räumliche Zuordnung ist der Oberflächen Beobachter. Der Programmablauf lautet wie folgt:
* Erstellen eines Surface Observer-Objekts
   * Geben Sie ein oder mehrere räumliche Volumes an, um die relevanten Bereiche zu definieren, in denen die Anwendung räumliche Mapping-Daten empfangen möchte. Ein räumliches Volume ist einfach eine Form, die einen Bereich des Raums definiert, z. b. eine Kugel oder ein Feld.
   * Verwenden Sie ein räumliches Volume mit einem weltweit gesperrten räumlichen Koordinatensystem, um einen festgelegten Bereich der physischen Welt zu identifizieren.
   * Verwenden Sie ein räumliches Volume, das jeden Frame mit einem vom Text gesperrten räumlichen Koordinatensystem aktualisiert hat, um einen Bereich des Bereichs zu identifizieren, der sich mit dem Benutzer verschiebt (aber nicht rotiert).
   * Diese räumlichen Volumes können zu einem späteren Zeitpunkt geändert werden, wenn sich der Status der Anwendung oder des Benutzers ändert.
* Abrufen von Informationen über räumliche Oberflächen mithilfe von Abruf oder Benachrichtigung
   * Sie können den Oberflächen Beobachter jederzeit für den Status der räumlichen Oberfläche abrufen. Alternativ dazu können Sie sich für das Ereignis "Surface Changed" des Surface Observer registrieren, das die Anwendung benachrichtigt, wenn räumliche Oberflächen geändert wurden.
   * Für ein dynamisches räumliches Volume, wie z. b. die Ansicht "Frustum" oder ein mit dem Text gesperrtes Volume, müssen Anwendungen für jeden Frame Änderungen abrufen, indem Sie den relevanten Bereich festlegen und dann den aktuellen Satz räumlicher Oberflächen abrufen.
   * Bei einem statischen Volume, z. b. einem weltweit gesperrten Cube, der einen einzelnen Raum abdeckt, können Anwendungen für das Ereignis "Oberflächen geändert" registriert werden, damit Sie benachrichtigt werden, wenn sich räumliche Oberflächen innerhalb dieses Volumes geändert haben.
* Prozess Oberflächen Änderungen
   * Iterieren Sie den bereitgestellten Satz räumlicher Oberflächen.
   * Räumliche Oberflächen als hinzugefügt, geändert oder entfernt klassifizieren.
   * Senden Sie für jede hinzugefügte oder geänderte räumliche Oberfläche ggf. eine asynchrone Anforderung an den Empfang eines aktualisierten Netzes, das den aktuellen Zustand der Oberfläche auf der gewünschten Detailebene darstellt.
* Verarbeiten Sie die asynchrone Mesh-Anforderung (Weitere Informationen finden Sie in den folgenden Abschnitten).

## <a name="mesh-caching"></a>Gitter Caching

Räumliche Oberflächen werden durch Dichte Dreiecksnetze dargestellt. Die Speicherung, das Rendering und die Verarbeitung dieser Netze kann beträchtliche Rechen-und Speicherressourcen beanspruchen. Daher sollte jede Anwendung ein Mesh-zwischen Speicherungs Schema übernehmen, das Ihren Anforderungen entspricht, um die Ressourcen zu minimieren, die für die Mesh-Verarbeitung und den Speicher verwendet werden. Mit diesem Schema soll bestimmt werden, welche Meshs beibehalten und welche verworfen werden sollen, sowie wann das Mesh für jede räumliche Oberfläche aktualisiert werden soll.

Viele der erörterten Überlegungen werden direkt darüber informiert, wie Ihre Anwendung das Mesh-Caching angehen sollte. Sie sollten berücksichtigen, wie der Benutzer die Umgebung durchläuft, welche Oberflächen benötigt werden, wenn verschiedene Oberflächen beobachtet werden und Änderungen in der Umgebung aufgezeichnet werden sollen.

Wenn das Ereignis "Surface Changed" interpretiert wird, ist die grundlegende Mesh-cachinglogik wie folgt:
* Wenn der Anwendung eine räumliche Oberflächen-ID angezeigt wird, die Sie noch nicht gesehen hat, sollte diese als neue räumliche Oberfläche behandelt werden.
* Wenn in der Anwendung eine räumliche Oberfläche mit einer bekannten ID, aber mit einer neuen Update Zeit angezeigt wird, sollte Sie als aktualisierte räumliche Oberfläche behandelt werden.
* Wenn die Anwendung keine räumliche Oberfläche mit einer bekannten ID mehr sieht, sollte diese als entfernte räumliche Oberfläche behandelt werden.

Die einzelnen Anwendungen können dann die folgenden Optionen auswählen:
* Soll für neue räumliche Oberflächen ein Mesh angefordert werden?
   * Im Allgemeinen sollte Mesh sofort für neue räumliche Oberflächen angefordert werden, die nützliche neue Informationen für den Benutzer bereitstellen können.
   * Neue räumliche Oberflächen in der Nähe und vor dem Benutzer sollten jedoch Priorität erhalten, und Ihr Mesh sollte zuerst angefordert werden.
   * Wenn das neue Mesh nicht benötigt wird, wenn die Anwendung beispielsweise permanent oder vorübergehend das zugehörige Modell der Umgebung "eingefroren" hat, sollte Sie nicht angefordert werden.
* Soll bei aktualisierten räumlichen Oberflächen Mesh angefordert werden?
   * Aktualisierte räumliche Oberflächen in der Nähe und vor dem Benutzer sollten Priorität erhalten, und Ihr Mesh sollte zuerst angefordert werden.
   * Es kann auch sinnvoll sein, neuen Oberflächen höhere Priorität zuzuweisen als aktualisierte Oberflächen, insbesondere während des Scanvorgangs.
   * Zum Begrenzen der Verarbeitungskosten möchten Anwendungen möglicherweise die Geschwindigkeit Drosseln, mit der die Aktualisierungen räumlicher Oberflächen verarbeitet werden.
   * Möglicherweise ist es möglich, zu ableiten, dass Änderungen an einer räumlichen Oberfläche geringfügig sind, z. b. wenn die Begrenzungen der Oberfläche gering sind. in diesem Fall ist das Update möglicherweise nicht wichtig genug, um es zu verarbeiten.
   * Updates für räumliche Oberflächen außerhalb der aktuellen Region des Benutzers werden möglicherweise vollständig ignoriert, aber in diesem Fall ist es möglicherweise effizienter, die räumlichen umgebenden Volumes zu ändern, die von der Oberfläche Observer verwendet werden.
* Soll für entfernte räumliche Oberflächen das Mesh verworfen werden?
   * Das Mesh sollte in der Regel sofort für entfernte räumliche Oberflächen verworfen werden, sodass die – Hologramm-Okklusion korrekt ist.
   * Wenn die Anwendung jedoch davon ausgehen kann, dass eine räumliche Oberfläche bald wieder angezeigt wird (möglicherweise basierend auf dem Design der Benutzeroberfläche), ist es möglicherweise effizienter, Sie beizubehalten, als das Mesh zu verwerfen und Sie später erneut zu erstellen.
   * Wenn die Anwendung ein umfangreiches Modell der Benutzerumgebung aufbaut, ist es möglicherweise nicht wünschenswert, alle Netze zu verwerfen. Dennoch muss die Ressourcenverwendung eingeschränkt werden, möglicherweise durch Spoolvorgänge auf den Datenträger, wenn räumliche Oberflächen ausgeblendet werden.
   * Beachten Sie, dass einige relativ seltene Ereignisse während der Generierung räumlicher Oberflächen dazu führen können, dass räumliche Oberflächen durch neue räumliche Oberflächen an einem ähnlichen Ort, aber mit unterschiedlichen IDs ersetzt werden. Folglich sollten Anwendungen, die keine entfernte Oberfläche verwerfen, nicht mehr über mehrere überlappende räumliche Oberflächen Netze verfügen, die denselben Speicherort abdecken.
* Sollte Mesh für alle anderen räumlichen Oberflächen verworfen werden?
   * Auch wenn eine räumliche Oberfläche vorhanden ist, sollte sie verworfen werden, wenn Sie für die Benutzeroberfläche nicht mehr nützlich ist. Wenn die Anwendung z. b. den Raum auf der anderen Seite eines Torys mit einem alternativen virtuellen Raum ersetzt, sind die räumlichen Flächen in diesem Raum nicht mehr von Bedeutung.

Im folgenden finden Sie eine Beispiel Strategie für das Mesh-Caching, bei der räumliche und zeitliche Bindestriche verwendet werden:
* Stellen Sie sich eine Anwendung vor, die eine Frustum-förmige räumliche Menge von Interesse verwenden möchte, die auf den Blick des Benutzers folgt, wenn Sie sich ansehen und durchlaufen.
* Eine räumliche Oberfläche kann vorübergehend von diesem Volume verschwinden, da der Benutzer nicht mehr von der Oberfläche entfernt wird oder die Schritte von ihm entfernt werden... Es wird nur ein kurzer Blick angezeigt, oder es wird ein späterer Vorgang wiederholt. In diesem Fall stellt das verwerfen und erneute Erstellen des Netzes für diese Oberfläche eine Menge redundanter Verarbeitung dar.
* Um die Anzahl der verarbeiteten Änderungen zu reduzieren, verwendet die Anwendung zwei räumliche Oberflächen Beobachter, eine in der anderen. Das größere Volume ist sphärisch und folgt dem Benutzer verzögert. Es wird nur dann verschoben, wenn dies notwendig ist, um sicherzustellen, dass das Zentrum innerhalb von 2,0 Metern des Benutzers liegt
* Neue und aktualisierte räumliche Oberflächen Netze werden immer aus dem kleineren inneren Oberflächen Beobachter verarbeitet, aber die Meshs werden zwischengespeichert, bis Sie auf dem größeren äußeren Oberflächen Beobachter verschwinden. Dadurch kann die Anwendung vermeiden, dass viele redundante Änderungen aufgrund der lokalen Benutzer Bewegung verarbeitet werden.
* Da eine räumliche Oberfläche aufgrund von nach Verfolgungs Verlusten auch temporär verschwinden kann, wird die Anwendung beim Nachverfolgen des Verlusts auch zum verwerfen entfernter räumlicher Oberflächen eingestellt.
* Im Allgemeinen sollte eine Anwendung den Kompromiss zwischen reduzierter Update Verarbeitung und erhöhter Speicherauslastung auswerten, um die ideale zwischen Speicherungs Strategie zu ermitteln.

## <a name="rendering"></a>Rendering

Es gibt drei Hauptmethoden, mit denen die Netzen für räumliche zuordnet häufig zum Rendern verwendet werden:
* Zur Oberflächen Visualisierung
   * Es ist häufig nützlich, räumliche Oberflächen direkt visuell darzustellen. Wenn Sie z. b. "Shadows" aus Objekten in räumliche Oberflächen umwandeln, kann der Benutzer nützliches visuelles Feedback bereitstellen, während Sie Hologramme auf Oberflächen platzieren.
   * Beachten Sie, dass räumliche Netze sich von der Art der Netzen unterscheiden, die von einem 3D-Künstler erstellt werden könnten. Die Dreiecks Topologie wird nicht als "Clean"-Topologie verwendet, und das Mesh wird von [verschiedenen Fehlern](spatial-mapping.md#what-influences-spatial-mapping-quality)beeinträchtigt.
   * Um eine ansprechende visuelle Ästhetik zu erstellen, können Sie daher eine gewisse [Gitter Verarbeitung](spatial-mapping.md#mesh-processing)durchführen, z. b. zum Auffüllen von Lücken oder zur Glättung von Oberflächen Normalisierungen. Möglicherweise möchten Sie auch einen Shader verwenden, um auf dem Mesh entwickelte Texturen zu projizieren, anstatt die Mesh-Topologie und normale direkt zu visualisieren.
* Zum okdieren von holograms hinter realen Oberflächen
   * Räumliche Oberflächen können in einem tiefen Durchlauf gerendert werden, der sich nur auf den [tiefen Puffer](https://msdn.microsoft.com/library/windows/desktop/bb219616(v=vs.85).aspx) auswirkt und sich nicht auf Farb Renderziele auswirkt.
   * Dadurch wird der tiefen Puffer zum okdieren von nachfolgend gerenderten holograms hinter räumlichen Oberflächen primes. Die genaue okgrams-okgramme verbessern den Sinn, dass holograms tatsächlich im physischen Raum des Benutzers vorhanden sind.
   * Um das tiefe Rendering zu aktivieren, aktualisieren Sie den Blend-Status, um [rendertargetwrite temask für alle farbrenderziele](https://msdn.microsoft.com/library/windows/desktop/hh404492(v=vs.85).aspx) auf NULL festzulegen.
* So ändern Sie die Darstellung von holograms, die von realen Oberflächen verdeckt werden
   * Normalerweise wird die gerenderte Geometrie ausgeblendet, wenn Sie verdeckt wird. Dies wird erreicht, indem die tiefen Funktion in Ihrem [Status der tiefen Schablone](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx) auf "kleiner als oder gleich" festgelegt wird, wodurch die Geometrie nur dann sichtbar ist, wenn Sie sich **näher** an der Kamera befindet als alle zuvor gerenderten Geometrie.
   * Es kann jedoch hilfreich sein, bestimmte Geometrie sichtbar zu machen, auch wenn Sie verdeckt ist, und die Darstellung zu ändern, wenn Sie als Möglichkeit zum Bereitstellen von visuellem Feedback für den Benutzer bereitgestellt wird. So kann die Anwendung z. b. den Speicherort eines Objekts anzeigen, während klar ist, dass sich hinter einer realen Oberfläche befindet.
   * Um dies zu erreichen, müssen Sie die Geometrie ein zweites Mal mit einem anderen Shader Rendering, der die gewünschte Darstellung "okded" erstellt. Bevor Sie die Geometrie zum zweiten Mal rendern, nehmen Sie zwei Änderungen an Ihrem [tiefen Schablonen Zustand](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx)vor. Legen Sie zunächst die tiefen Funktion auf "größer als oder gleich" fest, damit die Geometrie nur dann sichtbar ist, wenn Sie sich von der Kamera **weiter** entfernt als alle zuvor gerenderten Geometrie. Legen Sie für depthwrite den Wert 0 (null) fest, damit der tiefen Puffer nicht geändert wird (der tiefen Puffer sollte weiterhin die Tiefe der Geometrie darstellen, die der Kamera **am nächsten** ist).

Die [Leistung](understanding-performance-for-mixed-reality.md) ist ein wichtiger Aspekt beim Rendern von Netzen für räumliche Zuordnung. Hier finden Sie einige renderingleistungstechniken, die speziell für das Rendern räumlicher Mapping-
* Dreiecks Dichte anpassen
   * Wenn Sie räumliche Oberflächen-Netzen von Ihrem Oberflächen Beobachter anfordern, fordern Sie die niedrigste Dichte von Dreiecksnetzen an, die Ihren Anforderungen genügt.
   * Abhängig von der Entfernung der Oberfläche vom Benutzer und seiner Relevanz für die Benutzeroberfläche ist es möglicherweise sinnvoll, die Dreiecks Dichte auf einer Oberfläche zu verändern.
   * Durch das Verringern der Anzahl von Dreiecke werden die Speicherauslastung und die Vertex-Verarbeitungskosten auf der GPU reduziert, obwohl Sie sich nicht auf die Pixel Verarbeitungskosten auswirken
* Ausführen von Frustum-Berechnungen
   * Die Frustum-Erstellung überspringt Zeichnungsobjekte, die nicht angezeigt werden können, weil Sie sich außerhalb der aktuellen Anzeige "Frustum" befinden. Dadurch werden CPU-und GPU-Verarbeitungskosten reduziert.
   * Da die Erstellung pro Mesh durchgeführt wird und räumliche Oberflächen sehr groß sein können, kann das unterbrechen jedes räumlichen Oberflächen Netzes in kleinere Blöcke zu einer effizienteren Leistung führen (da weniger Offscreen-Dreiecke gerendert werden). Es gibt jedoch einen Kompromiss, welche weiteren Netzen Sie haben, desto mehr zeichnen-Aufrufe müssen Sie durchführen, was die CPU-Kosten erhöhen kann. In einem Extremfall könnte die Frustum-cullinger-Berechnungen selbst über messbare CPU-Kosten verfügen.
* Rendering-Reihenfolge anpassen
   * Räumliche Oberflächen sind tendenziell groß, da Sie die gesamte Umgebung des Benutzers darstellen. Die Pixel Verarbeitungskosten für die GPU können daher hoch sein, insbesondere in Fällen, in denen mehr als eine Ebene der sichtbaren Geometrie vorhanden ist (einschließlich räumlicher Oberflächen und anderer Hologramme). In diesem Fall verbleibt die Ebene, die dem Benutzer am nächsten ist, alle Ebenen weiter, sodass alle GPU-Zeit, die für das Rendering dieser entfernteren Schichten aufgewendet wird, verschwendet wird.
   * Um diese redundante Arbeit auf der GPU zu reduzieren, ist es hilfreich, nicht transparente Oberflächen in der Reihenfolge vor und nach hinten zu Rendering (Näheres zuerst, entfernter entfernter). Durch ' deckend ' bedeuten wir die Oberflächen, für die ' depthwrite temask ' in Ihrem [tiefen Schablonen Zustand](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx)auf einen Wert festgelegt ist. Wenn die nächstliegenden Oberflächen gerendert werden, wird der tiefen Puffer als primwert verwendet, sodass mehr entfernte Oberflächen vom Pixel Prozessor auf der GPU effizient übersprungen werden.

## <a name="mesh-processing"></a>Mesh-Verarbeitung

Eine Anwendung möchte möglicherweise [verschiedene Vorgänge](spatial-mapping.md#mesh-processing) für räumliche Oberflächen Netze durchführen, um Ihren Anforderungen gerecht zu werden. Der Index und die Scheitelpunkt Daten, die für jedes räumliche Oberflächen Mesh bereitgestellt werden, verwenden dasselbe vertraute Layout wie der [Scheitelpunkt und die Index Puffer](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) , die zum Rendern von Dreiecksnetzen in allen modernen renderingapis verwendet werden. Ein wichtiger Fakt ist jedoch, dass räumliche Zuordnungs Dreiecke eine Sortier **Reihenfolge vor dem Uhrzeigersinn**haben. Jedes Dreieck wird durch drei Scheitelpunkt Indizes im Index Puffer des Netzes dargestellt, und diese Indizes identifizieren die Scheitel Punkte des Dreiecks in einer Reihenfolge im **Uhrzeigersinn** , wenn das Dreieck von der **Vorder** Seite aus angezeigt wird. Die Vorderseite (oder außen) der räumlichen Oberflächen Netze entspricht wie erwartet der Vorderseite (Sichtbarkeit) der realen Oberflächen.

Anwendungen sollten nur Mesh-Vereinfachungen durchführen, wenn die vom Oberflächen Beobachter bereitgestellte Größe des coarst-Dreiecks nach wie vor unzureichend grob ist. diese Aufgabe ist Rechen intensiv und wird von der Laufzeit bereits ausgeführt, um die verschiedenen bereitgestellte Detailebenen.

Da jeder Oberflächen Beobachter mehrere nicht verbundene räumliche Oberflächen bereitstellen kann, möchten einige Anwendungen diese räumlichen Oberflächen Netze möglicherweise gegenseitig Ausschneiden und diese dann zusammen Schnallen. Im Allgemeinen ist der clippingschritt erforderlich, da sich nahe gelegene Netze der räumlichen Oberfläche oft leicht überlappen.

## <a name="raycasting-and-collision"></a>Raycasting und Kollision

Damit eine-Physik-API (z. b. [Havok](https://www.havok.com/)) eine Anwendung mit Raycasting-und Kollisions Funktionen für räumliche Oberflächen bereitstellt, muss die Anwendung räumliche Oberflächen Netze für die Physik-API bereitstellen. Für die Physik verwendete Meshes verfügen häufig über die folgenden Eigenschaften:
* Sie enthalten nur eine kleine Anzahl von Dreiecken. Physik Vorgänge sind Rechen intensiver als Renderingvorgänge.
* Sie sind "Wasser-eng". Oberflächen, die als solide fest gedacht sind, sollten keine kleinen Lücken enthalten. sogar Lücken zu klein, um sichtbar zu sein, können Probleme verursachen.
* Sie werden in die in die-Konstante umwandl konvertiert. Bei der Verarbeitung von Netz-und Konfigurationsobjekten sind nur wenige Polygone vorhanden, und die Verarbeitung ist weitaus Rechen effizienter als bei rohdreiecks Netzen.

Beachten Sie bei der Durchführung von Raycasts gegen räumliche Oberflächen, dass diese Oberflächen oft komplex sind und über große Formen mit wenig Details verfügen, ebenso wie Ihr Schreibtisch! Dies bedeutet, dass ein einzelner raycast oft unzureichend genug ist, um Ihnen genügend Informationen über die Form der Oberfläche und die Form des leeren Leerraums in der Nähe zu übergeben. Daher empfiehlt es sich in der Regel, viele Raycasts in einem kleinen Bereich auszuführen und die Aggregat Ergebnisse zu verwenden, um ein zuverlässigeres Verständnis der Oberfläche zu erhalten. Wenn Sie z. b. den Mittelwert von 10 Raycasts zum Steuern der – Hologramm-Platzierung auf einer Oberfläche verwenden, ergibt sich ein weitaus reibungsloseres Ergebnis, bei dem nur ein einziges raycast verwendet wird.

Bedenken Sie jedoch, dass jeder raycast hohe Rechen Kosten aufweisen kann. Abhängig von Ihrem Verwendungs Szenario sollten Sie daher die berechnungskosten zusätzlicher Raycasts (durch die jeder Frame ausgeführt wird) gegen die berechnungskosten der [Mesh-Verarbeitung](spatial-mapping.md#mesh-processing) abwägen, um Löcher in räumlichen Oberflächen zu glätten und zu entfernen (bei räumlichem Netzen werden aktualisiert.)

## <a name="the-environment-scanning-experience"></a>Umgebung zum Scannen der Umgebung

Jede Anwendung, die räumliche Zuordnung verwendet, sollte die Bereitstellung einer "Scan Darstellung" in Erwägung gezogen werden. der Prozess, durch den die Anwendung den Benutzer zum Überprüfen von Oberflächen führt, die für eine ordnungsgemäße Funktionsweise der Anwendung erforderlich sind.

![Beispiel für das Scannen](images/sr-mixedworld-140429-8pm-00068-1000px.png)<br>
*Beispiel für das Scannen*

Die Art dieser Scanfunktion kann sich je nach Anforderungen der Anwendung stark unterscheiden, aber zwei Hauptprinzipien sollten den Entwurf berücksichtigen.

Erstens **ist die klare Kommunikation mit dem Benutzer das primäre Problem**. Der Benutzer sollte immer wissen, ob die Anforderungen der Anwendung erfüllt werden. Wenn Sie nicht erfüllt werden, sollten Sie dem Benutzer sofort klar sein, warum dies der Fall ist, und Sie sollten schnell dazu führen, dass Sie die entsprechende Aktion ausführen.

Zweitens **sollten Anwendungen versuchen, ein Gleichgewicht zwischen Effizienz und Zuverlässigkeit zu erzielen**. Wenn **dies möglich ist, sollten**Anwendungen räumliche Daten automatisch analysieren, um die Benutzer Zeit zu sparen. Wenn es nicht möglich ist, dies zuverlässig zu tun, sollten Anwendungen den Benutzer stattdessen ermöglichen, der Anwendung schnell die zusätzlichen Informationen bereitzustellen, die Sie benötigt.

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
   * Dies kann den Benutzer dabei unterstützen, bestimmte Arten von [Fehlern in den räumlichen Daten](spatial-mapping.md#what-influences-spatial-mapping-quality)zu vermeiden, z. b. durch die Entfernung von Fenstern oder spiegeln.

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
* Da [Fehler](spatial-mapping.md#what-influences-spatial-mapping-quality) in den räumlichen Mapping-Daten sich stark auf die Benutzerumgebung auswirken können, empfiehlt es sich, die Anwendung in einer Vielzahl von Umgebungen zu testen.
* Nehmen Sie nicht an der Gewohnheit vor, sich immer am gleichen Ort zu testen, z. b. an Ihrem Schreibtisch. Stellen Sie sicher, dass Sie auf verschiedenen Oberflächen unterschiedlichen Positionen, Formen, Größen und Materialien testen.
* Auch wenn synthetische oder aufgezeichnete Daten für das Debuggen hilfreich sein können, werden Sie nicht auf die gleichen wenige Testfälle angewiesen. Dadurch werden möglicherweise wichtige Probleme ermittelt, die zuvor durch mehr unterschiedliche Tests abgefangen wurden.
* Es empfiehlt sich, Tests mit echten (und im Idealfall nicht gespoinierten) Benutzern durchzuführen, da Sie die hololens oder Ihre Anwendung möglicherweise nicht exakt auf die gleiche Weise wie Sie verwenden. Dies kann Ihnen vielleicht überraschen, wie sich das Verhalten, das Wissen und die Annahmen der unterschiedlichen Benutzer Verhalten.

## <a name="troubleshooting"></a>Fehlerbehebung
* Damit die Oberflächen Netzen ordnungsgemäß ausgerichtet werden, muss jedes gameobject aktiv sein, bevor es an den surfaceobeserver gesendet wird, damit das Mesh erstellt wird. Andernfalls werden die Netze in Ihrem Raum angezeigt, aber in seltsamen Winkeln gedreht.
* Das gameobject, das das Skript ausführt, das mit dem surfaceobserver kommuniziert, muss auf den Ursprung festgelegt werden. Andernfalls verfügen alle von Ihnen erstellten und an den surfaceobserver gesendeten gameobjects-Objekte, deren Netzen erstellt werden, über einen Offset, der gleich dem Offset des übergeordneten Spiel Objekts ist. Dies kann dazu führen, dass ihre Netze mehrere Meter entfernt werden, sodass es sehr schwierig ist, das zu debuggen, was passiert.

## <a name="see-also"></a>Weitere Informationen:
* [Koordinatensysteme](coordinate-systems.md)
* [Räumliche Abbildung in DirectX](spatial-mapping-in-directx.md)
* [Räumliche Abbildung in Unity](spatial-mapping-in-unity.md)
* [Szenen Verständnis](scene-understanding.md)
* [Raumabtastvisualisierung](room-scan-visualization.md)
* [Raumklangentwurf](spatial-sound-design.md)
* [Fallstudie – Schauen durch Löcher in Ihrer Realität](case-study-looking-through-holes-in-your-reality.md)
