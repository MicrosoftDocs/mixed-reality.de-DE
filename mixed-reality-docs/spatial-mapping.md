---
title: Räumliche Zuordnung
description: Räumliche Zuordnung bietet eine detaillierte Darstellung der echten Oberflächen in der Umgebung für die HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: räumliche Zuordnung, HoloLens, mixed Reality, Surface Wiederaufbau, Netz, sr
ms.openlocfilehash: 31abeca624512f1d5e721dbe879ca2243cf41345
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605044"
---
# <a name="spatial-mapping"></a>Räumliche Zuordnung

Räumliche Zuordnung bietet eine detaillierte Darstellung der echten Oberflächen in der Umgebung für die HoloLens, ermöglicht Entwicklern das Erstellen einer überzeugenden mixed Reality-Erfahrung. Durch das Zusammenführen der realen Welt mit der virtuellen Welt, kann eine Anwendung Hologramme echte scheinen vornehmen. Durch die Bereitstellung vertraut realen Verhaltensweisen und Interaktionen können ein Anwendungen Erwartungen der Benutzer auch alternative besser ausrichten.

<br>

>[!VIDEO https://www.youtube.com/embed/zff2aQ1RaVo]

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Feature</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1. Generation)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td> Räumliche Zuordnung</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>



## <a name="conceptual-overview"></a>Konzeptionelle Übersicht

![Mesh-Oberflächen, die für einen Raum](images/SurfaceReconstruction.jpg)<br>
*Ein Beispiel für eine räumliche Zuordnung Mesh deckt einen Raum*

Die zwei primären Objekttypen, für die räumliche Zuordnung verwendet werden "Räumlichen Oberfläche Observer" und der 'räumliche Fläche".

Die Anwendung bietet dem räumliche Oberfläche Beobachter ein oder mehrere Volumes umgebende, um die Regionen des Speicherplatzes zu definieren, in dem die Anwendung die räumliche Zuordnungsdaten empfangen möchte. Für die einzelnen Volumes stellt die räumliche Zuordnung die Anwendung mit einem Satz von räumlichen Oberflächen bereit.

Diese Volumes (in einer festen Position in Bezug auf die reale Welt) nicht bewegt werden können oder sie die HoloLens (sie verschieben, aber nicht drehen, mit der HoloLens Fortschreiten über die Umgebung) angefügt werden. Jeder räumliche Fläche wird beschrieben, reale Flächen in einer kleinen Anzahl von Leerzeichen, dargestellt als ein Dreieckgitter angefügt wird, ein World gesperrt [räumliche Koordinatensystem](coordinate-systems.md).

Neue Daten über die Umgebung erfasst, die HoloLens, und beim Auftreten von Änderungen in der Umgebung werden räumliche Flächen angezeigt, nicht mehr angezeigt, und ändern.

## <a name="common-usage-scenarios"></a>Allgemeine Verwendungsszenarien

![Abbildungen der allgemeine Verwendungsszenarien räumliche Zuordnung: Ablage "," verdecken "," Physik "und" Navigation](images/sm-concepts-1000px.png)

### <a name="placement"></a>Platzierung

Räumliche Zuordnung bietet Anwendungen die Möglichkeit bieten, natürliche und vertraute Formen der Interaktion des Benutzers; Was ist möglicherweise natürlicher wirkt als das Platzieren von Ihrem Telefons nach unten auf dem Schreibtisch?

Die Platzierung von Hologramme einschränken (oder üblicher, einer beliebigen Auswahl von räumlichen Standorten), liegen auf Oberflächen bietet eine natürliche Zuordnung von 3D (Punkt im Raum) bis 2D (zeigen Sie auf der Oberfläche). Dies reduziert die Menge an Informationen, die der Benutzer muss für die Anwendung bereitstellen, und deshalb gibt es die Interaktionen des Benutzers schneller, einfacher und präziser. Dies gilt besonders, da'sofort distance' ist nicht etwas, das wir verwendet werden, für andere Benutzer oder Computer physisch zu kommunizieren. Wenn wir mit unseren Finger zeigen, werden wir eine Richtung, aber nicht mit einer Entfernung angeben.

Ein wichtiger Vorsichtshinweis ist, die, wenn eine Anwendung die Entfernung von der Richtung ableitet (z. B. durch Ausführen einer Raycast des Benutzers Blicke Richtung des nächsten finden räumliche Oberfläche), dies muss Ergebnisse liefern, die der Benutzer zuverlässig einschätzen kann. Andernfalls verliert der Benutzer deren Sinn des Steuerelements, und dies kann schnell frustrierend werden. Eine Methode, die dabei hilft, ist zum Ausführen von mehreren Raycasts anstelle nur eines. Reibungslose und besser vorhersagbare, weniger anfällig für aus vorübergehenden "Ausreißer" Ergebnissen beeinflussen (wie durch Strahlung kleine Lücken übergeben, oder drücken kleine Teile der Geometrie an, die der Benutzer nicht bekannt ist verursacht werden kann), sollte die aggregierten Ergebnisse sein. Aggregierung oder Glättung kann auch im Laufe der Zeit ausgeführt werden; Beispielsweise können Sie die maximale Geschwindigkeit einschränken, an der ggf. ein Hologramm Entfernung des Benutzers variieren kann. Wodurch einfach die minimalen und maximalen Abstand hilft auch, damit die – Hologramm verschoben werden nicht plötzlich Weg in die Ferne fliegen oder stammen, zurück in den Benutzer abstürzt.

Anwendungen können auch die Form und die Richtung der Flächen Guide – Hologramm Platzierung verwenden. Eine holographic Stuhl sollte kein durch Wände eindringt und sollten sind unveränderliche mit dem Boden, auch wenn es etwas ungleichmäßigen ist. Diese Art von Funktion würde wahrscheinlich auf die Verwendung der Physik Konflikte statt nur Raycasts, gelten jedoch ähnliche Themen basieren. Wenn die – Hologramm angeordnet werden viele kleine Polygone, die bleiben verfügt, wie die "Legs" eines Stuhls, kann es sinnvoll, erweitern die physikalische Darstellung die Polygone etwas breiter und reibungslose, sodass sie mehr über räumliche Flächen ohne schieben können Erstellen von Bildschirmfotos.

An dessen Ende der Skala Benutzereingabe kann vereinfacht werden sofort vollständig aus, und räumliche Flächen können verwendet werden, vollständig automatisch – Hologramm Platzierung ausführen. Beispielsweise kann die Anwendung einen holographic Light-Switch an einer beliebigen Stelle an die Wand für den Benutzer zum Drücken platzieren. Gelten die gleichen Vorbehalte zur Vorhersagbarkeit doppelt hier; Wenn der Benutzer steuern – Hologramm Platzierung erwartet, aber die Anwendung nicht immer Hologramme platzieren ist, erwarten sie, dass (sofern die Light-Schalter an einer Stelle, die den Benutzer zu erreichen, kann nicht angezeigt), wird dies führt dazu, dass sein. Es kann tatsächlich nicht schlimmer kommen, automatische Platzierung auszuführen, die Benutzer-Korrektur erfordert ein Teil der Zeit, als die, müssen nur die Benutzer immer Platzierung selbst; ausführen Da das erfolgreiche automatische Platzierung wird *erwartet*, manuelle Korrektur scheint eine Belastung dar.

Beachten Sie auch, dass die Fähigkeit einer Anwendung zur Verwendung von räumlicher Oberflächen für die Platzierung stark von der Anwendung abhängig ist [Scannen Erfahrung](spatial-mapping-design.md#the-environment-scanning-experience). Wenn eine Oberfläche nicht gescannt wurde, kann es für die Platzierung verwendet werden. Es ist Aufgabe der Anwendung, die dies deutlich für den Benutzer zu machen, damit er entweder unterstützen können, überprüfen die neue Flächen aus, oder wählen Sie einen neuen Speicherort.

Visuelles Feedback an den Benutzer ist von größter Wichtigkeit, während der Platzierung. Der Benutzer muss wissen, wo die Hologramm in Bezug auf die nächste Oberfläche mit [Erdung Effekte](spatial-mapping.md#visualization). Sie sollten wissen, warum das Verschieben von ihren – Hologramm (z. B. aufgrund von Konflikt mit einem anderen in der Nähe Oberfläche) eingeschränkt wird. Wenn sie ggf. ein Hologramm in der aktuellen Position einfügen können, sollten visuelles Feedback verdeutlichen, warum nicht vornehmen. Z. B. wenn der Benutzer versucht, platzieren Sie hängen ein holographic Sofa Hälfte in die Wand, und klicken Sie dann die Teile der Sofa, die hinter den Zaun sind verärgert farblich pulsate sollten. Oder umgekehrt, wenn die Anwendung eine räumliche Oberfläche an einem Ort nicht finden können, in denen der Benutzer eine reale Oberfläche sehen können, klicken Sie dann die Anwendung muss dies deutlich machen. Das fehlen offensichtliche einen Effekt sollen in diesem Bereich kann dieses Ziel erreichen.

### <a name="occlusion"></a>Okklusion

Eine der hauptsächlichen Verwendungsformen räumliche Zuordnung Flächen ist einfach Hologramme verdeckt. Dieses einfache Verhalten hat enorme Auswirkungen auf die wahrgenommene für eine realistischere Darstellung Hologramme, die beim Erzeugen eines stellen, die den gleichen physischen Bereich wie der Benutzer wirklich darstellen.

Verdecken enthält außerdem Informationen für den Benutzer; ggf. ein Hologramm angezeigt wird, die von einer realen Oberfläche okkludierte werden, bieten sich zusätzliches von visuellem Feedback, die räumliche Position der dieser – Hologramm, in der ganzen Welt. Im Gegensatz dazu verdecken kann auch sinnvoll *ausblenden* Informationen vom Benutzer; occluding Hologramme hinter Wände können visuelle Überfrachtung intuitive Weise zu reduzieren. Um ggf. ein Hologramm anzuzeigen oder auszublenden, muss der Benutzer lediglich ihren Köpfen zu verschieben.

Verdecken kann auch verwendet werden, um die Erwartungen an einer natürlichen Benutzeroberfläche basierend auf vertrauten physischen Interaktionen vorzubereiten; Wenn durch eine Fläche, die ggf. ein Hologramm ist okkludierte ist da, die dann bei solid handelt, also der Benutzer sollte erwarten, dass ein Hologramm *in Konflikt stehen* , Entwurfsoberfläche, und nicht einfach durch ihn durchlaufen.

In einigen Fällen ist verdecken von Hologramme nicht erwünscht. Wenn ein Benutzer benötigt, um ggf. ein Hologramm interagieren zu können, müssen sie - angezeigt, auch wenn er sich hinter einer echten Oberfläche befindet. In solchen Fällen sinnvoll es in der Regel um solche ggf. ein Hologramm anders gerendert werden, wenn es okkludierte ist (z. B. durch das Reduzieren der Helligkeit). Auf diese Weise der Benutzer kann die Hologramm visuell zu suchen, aber sie werden weiterhin in der Beachten Sie, dass er sich hinter der etwas befindet.

### <a name="physics"></a>Physik

Die Verwendung der Physiksimulation ist eine andere Art, in die räumliche Zuordnung verwendet werden, kann um zu erzwingen die *Anwesenheit* von Hologramme im physischen Raum des Benutzers. Wenn meine holographic Gummiball realistisch gesehen wird die aus meinem Schreibtisch, über dem Boden springt und nicht mehr angezeigt, unter dem Sofa wird, ist es möglicherweise schwierig für mich zu glauben, dass sie nicht wirklich vorhanden ist.

Physiksimulation bietet auch die Möglichkeit, eine Anwendung natürliche und vertraute Physik-basierte Interaktionen zu verwenden. Beim Verschieben eines holographic Möbel, um auf dem Boden wird wahrscheinlich einfacher sein, für den Benutzer, wenn die Möbel reagiert, als ob er über dem Boden, mit dem entsprechenden Trägheit und Reibung gleitend wurden.

Um realistische physikalische Verhalten zu generieren, Sie müssen wahrscheinlich einige ausführen [mesh Verarbeitung](spatial-mapping.md#mesh-processing) wie füllen Lücken, Entfernen von Gleitkomma-Wahnvorstellungen und Glättung Allgemeines Flächen.

Sie müssen auch beachten wie Ihrer Anwendungsverzeichnis [Scannen Erfahrung](spatial-mapping-design.md#the-environment-scanning-experience) wirkt sich auf die Physiksimulation. Zuerst wird nicht fehlen Flächen mit in Konflikt stehen; Was geschieht, wenn die Gummiball off wird die Gang und am Ende der Welt bekannt? Als Nächstes müssen Sie entscheiden, ob Sie fortgesetzt werden, um auf Änderungen in der Umgebung im Laufe der Zeit zu reagieren. In einigen Fällen möchten Sie so schnell wie möglich Antworten; Nehmen wir an, wenn der Benutzer als verschiebbar Barrikaden in Verteidigung gegen eine Tempest eingehende Roman Pfeile Türen und Möbel verwendet wird. In anderen Fällen sollten, Sie in neuen Updates zu ignorieren; einbringen Ihrer holographic Sportwagen rund um die Oval auf Ihre Boden plötzlich möglicherweise nicht so unterhaltsam, wenn möchte, dass Ihr Hund in der Mitte der Spur befinden.

### <a name="navigation"></a>Navigation

Räumliche Zuordnungsdaten können Anwendungen holographic Zeichen (oder -Agents) gewähren die Möglichkeit, die reale Welt auf die gleiche Weise wie eine Person zu navigieren. Dies kann helfen, das Vorhandensein von holographic Zeichen zu verstärken, indem sie auf den gleichen Satz von natürlichen, vertrauten Verhalten wie die der Benutzer und ihre Freunde zu beschränken.

Navigationsfunktionen können auch nützlich sein. Sobald eine Zuordnung für die Navigation in einem bestimmten Gebiet erstellt wurde, konnte er gemeinsam genutzt werden, um holographic erfahren Sie, wie neue Benutzer nicht vertraut mit diesem Speicherort bereitzustellen. Diese Zuordnung kann entworfen werden, um dafür zu sorgen, dass einfache "Datenflüsse" reibungslos oder um Störungen in gefährlicher Speicherorten wie dem Baustellen zu vermeiden.

Die wichtigsten technischen Herausforderungen bei der Implementierung der Navigationsfunktion verfügbar werden zuverlässige Erkennung von walks Oberflächen (Menschen nicht für Tabellen führen!) und ordnungsgemäßen Anpassung an Änderungen in der Umgebung (Menschen nicht Türen durchlaufen!). Das Netz möglicherweise einige [Verarbeitung](spatial-mapping.md#mesh-processing) , bevor er für die Pfad-Planung und Navigation von einem virtuellen Zeichen verwendet werden kann. Mesh-Glättung, und Entfernen von Wahnvorstellungen können hängen zunehmend Zeichen zu vermeiden. Möglicherweise möchten Sie auch das Gitter erheblich zu vereinfachen, um den Pfad des Zeichens-Planung und Berechnungen, die Navigation zu beschleunigen. Dieser Herausforderungen viel Aufmerksamkeit erhalten haben, bei der Entwicklung von Videogame-Technologie, und es gibt eine Fülle von verfügbaren Forschungsliteratur zu diesen Themen.

Beachten Sie, dass die integrierten NavMesh-Funktionalität in Unity mit räumliche Zuordnung Oberflächen verwendet werden kann. Dies ist, da die räumliche Zuordnung Oberflächen nicht bekannt sind, bis die Anwendung gestartet wird, während NavMesh Datendateien aus der Quelle Assets vorab generiert werden müssen. Beachten Sie, dass vom System für die räumliche Zuordnung nicht bereitgestellt werden [Informationen sehr weit entfernt Flächen](spatial-mapping-design.md#the-environment-scanning-experience) aus der aktuellen Position des Benutzers. Daher muss die Anwendung "Flächen selbst Denken Sie daran", wenn es ist, erstellen eine Übersicht über eine sehr große Fläche.

### <a name="visualization"></a>Visualisierung

In den meisten Fällen ist es angebracht, für die räumliche Oberflächen nicht sichtbar sein. um visuelle Überfrachtung zu minimieren, und lassen die tatsächlichen Welt sprechen für sich selbst. Allerdings ist es manchmal sinnvoll, die räumliche Zuordnung Flächen direkt, trotz der Tatsache zu visualisieren, dass ihre realen Entsprechungen bereits sichtbar sind.

Z. B. wenn der Benutzer versucht, platzieren Sie ggf. ein Hologramm auf einer Oberfläche (platzieren holographic CAB-Datei an die Wand, z. B..) Es kann hilfreich sein, "Hologramm erden" durch einen Schatten auf die Oberfläche. Dadurch wird dem Benutzer einen viel klarer Eindruck von der exakte physische Nähe zwischen den – Hologramm und der Fläche. Dies ist auch ein Beispiel für die allgemeine Vorgehensweise visuell eine Änderung "Vorschau", bevor der Benutzer, ein Commit ausgeführt.

Durch die Visualisierung der Flächen, kann die Anwendung ihr Verständnis von der Umgebung mit dem Benutzer freigeben. Beispielsweise kann ein holographic Brettspiel das horizontale bietet, die sie als "Tabellen", identifiziert hat visualisieren, damit der Benutzer weiß, wo sie gespeichert werden sollen, interagieren.

Visualisieren von Flächen werden eine gute Möglichkeit, die dem Benutzer in der Nähe Leerzeichen angezeigt wird, die in der Ansicht ausgeblendet sind. Dies könnte eine einfache Möglichkeit zum Erteilen der Zugriffsrechte für die Küche (und alle seine enthaltenen Hologramme) aus ihren Wohnzimmer bereitstellen.

Die räumliche Zuordnung gebotenen Oberfläche Gitter möglicherweise nicht besonders "bereinigen". Daher ist es wichtig, um sie entsprechend visuell darzustellen. Herkömmliche lichtberechnungen möglicherweise Fehler im Oberflächennormale auf eine Weise visuell ablenken markieren, während "bereinigen" auf der Oberfläche projizierte Texturen helfen können, um es einen besseren Überblick über Ihre aussehen zu verleihen. Es ist auch möglich, führen Sie [mesh Verarbeitung](spatial-mapping.md#mesh-processing) Mesh-Eigenschaften zu verbessern, bevor die Oberflächen gerendert werden.

## <a name="using-the-surface-observer"></a>Mithilfe des Entwurfsoberflächen Beobachters

Der Ausgangspunkt für die räumliche Zuordnung ist der Oberfläche Beobachter. Programmablauf lautet wie folgt aus:
* Erstellen Sie ein Surface Observer-Objekt
   * Geben Sie ein oder mehrere räumliche Volumes, um die interessante Bereiche zu definieren, in dem die Anwendung die räumliche Zuordnungsdaten empfangen möchte. Ein räumlicher Volume ist einfach eine Form, die einen Bereich von Leerzeichen, z. B. eine Kugel oder ein Feld definieren.
   * Verwenden Sie eine räumliche Volume mit einem World-locked räumliche Koordinatensystem, um einen festen Bereich der physischen Welt zu identifizieren.
   * Verwenden Sie einen räumlichen Volume aktualisiert jeder frame mit einem Text-locked räumliche Koordinatensystem, einen Bereich des zu identifizieren, die verschoben wird (aber wird nicht gedreht) mit dem Benutzer.
   * Diese räumliche Volumes können später zu einem beliebigen Zeitpunkt, der Status der Anwendung oder Änderung durch den Benutzer geändert werden.
* Verwenden Sie abrufen oder eine Benachrichtigung zum Abrufen von Informationen zu räumlichen Oberflächen
   * Sie können "den Entwurfsoberflächen Beobachter für räumliche Oberfläche Status zu einem beliebigen Zeitpunkt abrufen". Alternativ können Sie für den Surface Beobachter "Flächen geändert" Ereignis registrieren, die Anwendung benachrichtigt, wenn räumliche Flächen geändert wurden.
   * Anwendungen müssen für ein dynamisches Volume räumliche an, wie z. B. die Frustums Ansicht oder einem Text-locked Volume für jeden Frame Abruf von Änderungen durch Festlegen des relevanten Bereichs, und klicken Sie dann Abrufen des aktuellen Satzes von räumlichen Flächen.
   * Für einen statischen Datenträger, z. B. eine World-locked Cube zu einem einzigen Raum können Anwendungen registrieren, für das Ereignis "Flächen geändert" benachrichtigt, wenn räumliche Flächen, die innerhalb dieses Volume möglicherweise geändert wurde.
* Verarbeiten von Flächen Änderungen
   * Durchlaufen Sie die räumliche Oberflächen zur Verfügung gestellten Satz an.
   * Klassifizieren Sie räumliche Oberflächen als hinzugefügt, geändert oder entfernt.
   * Senden Sie für jede hinzugefügte oder geänderte räumliche Fläche ggf. eine asynchrone Anforderung zum Empfangen von aktualisierten Mesh, das die Fläche des aktuellen Status auf die gewünschte Detailebene darstellt.
* Verarbeiten der Anforderung asynchroner Netz (mehr Details in den folgenden Abschnitten).

## <a name="mesh-caching"></a>Mesh-Caching

Räumliche Flächen werden durch dichten Dreieckgitter dargestellt. Speichern von, rendern und verarbeiten diese Gitter können erhebliche Ressourcen für COMPUTE und Speicher nutzen. Daher sollte jede Anwendung ein Netz Cache-Schema für ihre Anforderungen, um die für die Mesh-Verarbeitung und Speicherung verwendeten Ressourcen zu minimieren übernehmen. Dieses Schema sollten ermitteln, die Gitter beibehalten werden sollen, verwerfen, sowie wann das Netz für jede räumliche Fläche aktualisiert.

Viele Überlegungen behandelt, es werden direkt informieren, wie Ihre Anwendung Zwischenspeichern Mesh Ansatz für die. Sie sollten erwägen, wie der Benutzer der Umgebung durchläuft, die Flächen erforderlich sind, bei verschiedene Oberflächen beobachtet werden werden und wenn Änderungen in der Umgebung erfasst werden sollen.

Beim Interpretieren der "Flächen" ein Änderungsereignis von der Oberfläche Beobachter bereitgestellt, ist die grundlegende Logik für das Zwischenspeichern Mesh wie folgt:
* Wenn die Anwendung eine räumliche Surface-ID, die es erkennt bisher nicht erkannt wurde, sollten sie dies als eine neue räumliche Oberfläche behandeln.
* Wenn die Anwendung eine räumliche Oberfläche mit einer bekannten ID sieht, jedoch mit der neuen Updates, sollten sie dies als eine aktualisierte räumliche Oberfläche behandeln.
* Wenn die Anwendung nicht mehr eine räumliche Oberfläche mit einer bekannten ID sieht, sollten sie dies als entfernter räumlicher Oberfläche behandeln.

Es obliegt an jede Anwendung, klicken Sie dann die folgenden Entscheidungen treffen:
* Für neue räumliche Flächen sollten Mesh werden angefordert?
   * Netz sollte in der Regel sofort für neue räumliche Flächen angefordert werden, die nützliche neue Informationen für den Benutzer bereitstellen kann.
   * Jedoch neue räumliche Flächen, die in der Nähe und vor dem Benutzer sollte die Priorität eingeräumt werden aus, und ihre Mesh sollten zunächst angefordert werden.
   * Wenn das neue Netz nicht erforderlich, wenn z. B. die Anwendung dauerhaftes oder temporäres 'das Modell der Umgebung fixiert hat', sollten sie nicht angefordert.
* Für die aktualisierten räumliche Oberflächen sollten Mesh werden angefordert?
   * Aktualisierte räumliche Flächen, die in der Nähe und vor dem Benutzer Priorität zugewiesen werden soll, und ihre Mesh sollten zunächst angefordert werden.
   * Es kann auch entsprechende neue Oberflächen als Oberflächen, vor allem bei der Überprüfung Umgebung aktualisiert höheren Priorität zugewiesen sein.
   * Um Verarbeitungskosten beschränken möchten, sollten Anwendungen, die Rate zu drosseln, an der sie Updates für räumliche Flächen verarbeiten.
   * Möglicherweise folgern, dass Änderungen an einer räumlichen Oberfläche kleinere, z. B. sind Wenn die Begrenzungen der Oberfläche klein ist, sind in diesem Fall das Update wichtig genug sind, den Prozess möglicherweise nicht möglich.
   * Updates für räumliche Oberflächen außerhalb des aktuellen Bereichs von Interesse des Benutzers können komplett ignoriert werden, obwohl in diesem Fall sehr viel effizienter, räumliche umgebende Volumes in die Verwendung durch den Surface Beobachter ändern sein kann.
* Für entfernter räumlicher Flächen sollten Mesh werden verworfen?
   * Im Allgemeinen sollten Mesh sofort für entfernter räumlicher Flächen verworfen werden, sodass – Hologramm verdecken richtig bleibt.
   * Jedoch verfügt die Anwendung Grund zur Annahme eine räumliche Oberfläche wird wieder angezeigt, in Kürze (möglicherweise je nach den Entwurf der benutzererfahrung), möglicherweise sehr viel effizienter, legen sie als zum Verwerfen der Netz aus, und es später noch Mal neu erstellen.
   * Wenn die Anwendung ein umfangreicher Modell für die Umgebung des Benutzers erstellt, sollten sie keine Gitter zu verwerfen. Sie müssen dennoch ressourcennutzung jedoch möglicherweise von Gitter Einreihen in die Warteschlange, auf dem Datenträger zu beschränken, wie räumliche Oberflächen nicht mehr angezeigt.
   * Beachten Sie, dass einige relativ selten Ereignisse während der räumlichen Oberfläche Generierung räumliche Flächen durch neue räumliche Oberflächen in einem ähnlichen Standort jedoch mit unterschiedlichen IDs ersetzt werden können. Folglich Anwendungen, die nicht zu eine entfernte Oberfläche verwerfen nicht bis Ende sich mit mehreren hoch überlappende räumliche Oberfläche Netzen für am gleichen Speicherort achten müssen.
* Mesh für alle anderen räumlichen Flächen verworfen werden sollen?
   * Auch während einer räumlichen Oberfläche vorhanden ist, wenn es nicht mehr nützlich, um die benutzererfahrung ist, wird sie verworfen werden soll. Beispielsweise erforderlich ersetzt die Anwendung"der Platz auf der anderen Seite der einen Zugangspunkt mit einem anderen virtuellen Bereich', klicken Sie dann die räumlichen Flächen in diesem Raum nicht mehr.

Hier ist ein Beispiel Mesh cachingstrategie, räumlichen und zeitlichen Hysterese verwenden:
* Erwägen Sie eine Anwendung für die Verwendung einer Frustums geformten, räumliche Volumes von Interesse sind, die des Benutzers Blicke folgt, da sie sich mit der Registerkarte und dann aus.
* Eine räumliche Oberfläche verschwindet möglicherweise vorübergehend von diesem Volume einfach, da der Benutzer, Weg von der Oberfläche sieht, oder um Schritte davon weiter... nur für zurück sehen oder verschiebt näher erneut einen Moment Zeit später noch mal. In diesem Fall stellt verworfen und neu erstellen Mesh für diese Oberfläche viele redundante dar.
* Um die Anzahl der verarbeiteten Änderungen zu reduzieren, verwendet die Anwendung zwei räumliche Oberfläche Observer-Objekte, eine solche in einer anderen. Das größere Volume ist sphärischen und gilt für den Benutzer "verzögert"; Er verschiebt Sie nur bei Bedarf, um sicherzustellen, dass die Centre in 2.0 Meter des Benutzers.
* Neue und aktualisierte räumliche Oberfläche Gitter werden immer von der kleineren innere Oberfläche Beobachter verarbeitet, aber Gitter werden zwischengespeichert, bis sie von der größeren Beobachter für das äußere Oberfläche nicht mehr angezeigt. Dadurch kann es sich um die Anwendung aus, um zu vermeiden, viele redundante Änderungen aufgrund des lokalen Benutzers Bewegung zu verarbeiten.
* Da eine räumliche Oberfläche auch vorübergehend ausblenden möglicherweise aufgrund von Verlust nachverfolgung verzögert die Anwendung auch verwerfen entfernte räumliche Flächen während der nachverfolgung von Datenverlust.
* Im Allgemeinen sollte eine Anwendung den Kompromiss zwischen Verarbeitung von reduzierten Aktualisierungen und erhöhter speicherauslastung, um zu bestimmen, die ideale cachingstrategie überprüfen.

## <a name="rendering"></a>Rendering

Es gibt drei Hauptmethoden, die in der räumliche Zuordnung Gitter neigen dazu, für das Rendering verwendet werden:
* Für die Oberfläche der Visualisierung
   * Es ist häufig nützlich, um die räumliche Flächen direkt zu visualisieren. Beispielsweise können Umwandlung "Shadows" von Objekten, auf den spatial Flächen hilfreich visuelles Feedback an den Benutzer beim Platzieren von Hologramme auf Oberflächen.
   * Dabei ist zu beachten ist, dass räumliche Gitter, um die Art der Gitter, die ein 3D Interpreten erstellen kann. Die Topologie Dreieck werden nicht als "bereinigen" als Menschen erstellten Topologie und Mesh wird Leiden [verschiedene Fehler](spatial-mapping-design.md#what-influences-spatial-mapping-quality).
   * Um eine ansprechende visuelle Ästhetik zu erstellen, Sie können daher einige ausführen möchten [mesh Verarbeitung](spatial-mapping.md#mesh-processing), z. B. Fill Lücken oder smooth Oberflächennormale. Möglicherweise möchten Sie auch einen Shader Projekt Interpreten konzipierte Texturen in Ihrem Mesh statt direkt auf die Visualisierung Mesh-Topologie und Normals verwenden.
* Für occluding Hologramme hinter realen Oberflächen
   * Räumliche Oberflächen gerendert werden können in einem nur-Depth-Durchlauf der wirkt sich nur auf die [Tiefenpuffer](https://msdn.microsoft.com/library/windows/desktop/bb219616(v=vs.85).aspx) und wirkt sich nicht auf die Farbe renderzielen.
   * Dies weist den Tiefenpuffer, um anschließend gerendert Hologramme hinter räumliche Flächen verdeckt. Genaue verdecken von Hologramme erweitert insofern Hologramme wirklich in den Raum des Benutzers vorhanden ist.
   * Um nur tiefe-Rendering zu aktivieren, aktualisieren Sie Ihre Blend-Status, Festlegen der [RenderTargetWriteMask](https://msdn.microsoft.com/library/windows/desktop/hh404492(v=vs.85).aspx) Renderziele 0 (null) für alle Farben.
* Zum Ändern der Darstellung von Hologramme okkludierte von realen Oberflächen
   * Normalerweise gerenderte Geometrie wird ausgeblendet, wenn es okkludierte ist. Dies wird erreicht, indem die Depth-Funktion Ihrer [Status der tiefenschablone](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx) auf "kleiner als oder gleich", der bewirkt, dass die Geometrie angezeigt werden, bei denen es nur ist **näher** bis zur Kamera als alle bereits gerendert Geometrie.
   * Allerdings kann es hilfreich sein, halten Sie bestimmte Geometrie sichtbar, selbst wenn es okkludierte ist, und klicken Sie zum Ändern der Darstellung, wenn Sie als eine Möglichkeit zum Bereitstellen von visuellem Feedback an den Benutzer okkludiert. Dies ermöglicht beispielsweise die Anwendung so, dass der Benutzer den Speicherort eines Objekts während deutlich, dass vornehmen hinter einer echten-Oberfläche.
   * Rendern Sie die Geometrie zu diesem Zweck ein zweites Mal mit einen anderen Shader, der die gewünschte 'occluded' Darstellung erstellt. Stellen Sie vor dem Rendern der geometriepunktwerts zum zweiten Mal, zwei Änderungen an Ihrer [Status der tiefenschablone](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx). Legen Sie zunächst die tiefenfunktion auf "größer als oder gleich", damit die Geometrie angezeigt werden, wo es nur ist **Weiter** von der Kamera als alle zuvor gerenderte Geometrie. Die DepthWriteMask andererseits auf 0 (null), festgelegt wird, sodass der Tiefenpuffer nicht geändert wird (der Tiefenpuffer sollten weiterhin die Tiefe der Geometrie darstellen **nächstgelegenen** bis zur Kamera).

[Leistung](understanding-performance-for-mixed-reality.md) ist ein wichtiger Aspekt, beim Rendern der Gitter für räumliche Zuordnung. Hier sind einige Techniken der Rendering-Leistung für das Rendern der Gitter für räumliche Zuordnung spezifisch:
* Passen Sie Dreieck Dichte
   * Beim anfordernden räumliche Fläche aus Ihrem Surface Beobachter z. B. Gitter, fordern Sie die niedrigste Dichte an Dreieckgitter, die für Ihre Anforderungen ausreicht.
   * Es möglicherweise sinnvoll, Dreieck-Dichte auf einer Oberfläche von Surface-Basis, abhängig von der Oberfläche der Entfernung des Benutzers, variieren und ihrer Relevanz für die benutzerfreundlichkeit.
   * Verringern Dreieck Anzahl reduziert speicherauslastung und Vertex-Verarbeitungskosten in der GPU, obwohl es nicht pixelverarbeitung Kosten auswirkt.
* Führen Sie Frustums culling
   * Frustums culling überspringt Zeichnungsobjekte, die nicht sichtbar ist, da sie außerhalb der aktuellen Anzeige Frustums sind. Dies reduziert die Kosten für die Verarbeitung von CPU- und GPU.
   * Da culling auf einer pro-Mesh-Basis erfolgt und räumliche Flächen groß sein können, wichtige jedes räumlichen Oberfläche Gitter in kleinere Blöcke in eine effizientere culling möglicherweise (werden also weniger außerhalb des Bildschirms Dreiecke dargestellt werden). Es gibt jedoch ein Kompromiss, die Weitere Gitter, was man, weitere zeichnen, die Sie treffen müssen, die CPU-Kosten erhöhen können. In Extremfällen kann die Berechnungen selbst culling Frustums sogar messbare CPU-Kosten aufweisen.
* Anpassen von Rendering-Reihenfolge
   * Räumliche Flächen tendenziell groß sein, da sie die gesamte benutzerumgebung Umschließung darstellen. Pixel, die Verarbeitung von Kosten auf der GPU möglich so hoch sein, insbesondere in Fällen, wenn mehr als einer Ebene Geometry-Instanz angezeigt (einschließlich räumliche Flächen und andere Hologramme) vorhanden ist. In diesem Fall wird die Ebene am ehesten entsprechen der Benutzer alle Ebenen weiter, occluding werden also GPU Zeit Rendern dieser mehr entfernten Stufen verschwendet wird.
   * Um diese redundanter Arbeitsschritte auf dem GPU zu reduzieren, ist es hilfreich, um nicht transparente Oberflächen in der Reihenfolge von vorne nach hinten zu rendern (näher zu erste, mehr entfernte diejenigen letzte). Von "deckend" meinen wir Flächen, die für die die DepthWriteMask, zu einem in festgelegt ist Ihr [Status der tiefenschablone](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx). Wenn die nächsten Oberflächen gerendert werden, werden sie den Tiefenpuffer vorzubereiten, damit mehr entfernte Flächen auf der GPU effizienter vom Prozessor Pixel übersprungen werden.

## <a name="mesh-processing"></a>Mesh-Verarbeitung

Eine Anwendung ausführen möchten [verschiedene Vorgänge](spatial-mapping.md#mesh-processing) auf räumliche Oberfläche Gitter, an die individuellen Anforderungen anzupassen. Die Index- und Vertexdaten Daten, die im Lieferumfang jedes räumlichen Oberfläche Gitter verwendet das gleiche vertraute Layout wie die [Vertex- und Indexpuffer](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) , die für das Rendern von Dreieckgitter in allen modernen-Rendering-APIs verwendet werden. Eine wichtige Tatsache zu berücksichtigen ist jedoch, dass die räumliche Zuordnung Dreiecke haben eine **Front Uhrzeigersinn Wicklung Reihenfolge**. Jedes Dreiecks wird durch drei Vertex Indizes des Gitters Indexpuffer dargestellt, und diese Indizes erkennt die dreieckvertices in einer **im Uhrzeigersinn** Reihenfolge, wenn das Dreieck angezeigt wird, aus der **Front** Seite. Im Vordergrund Seite (oder außerhalb) von räumlichen Oberfläche Netzen entspricht, wie auf die Vorderseite der realen Welt Flächen (sichtbar gewünscht).

Anwendungen sollten nur ausführen, Mesh-Vereinfachung, ob die gröbsten Dreieck Dichte, die von der Oberfläche Beobachter bereitgestellten weiterhin unzureichend grob gehalten ist diese Arbeit sehr viel rechenleistung beanspruchen und von der Laufzeit zum Generieren der verschiedenen bereits ausgeführt wird Detailebenen wird bereitgestellt.

Da jede Oberfläche Beobachter mehrere unverbundene räumliche Flächen bereitstellen kann, einige Anwendungen möglicherweise möchten Sie diese räumliche clip-Oberfläche, Gitter für jede andere, klicken Sie dann Reißverschluss sie zusammen. Im Allgemeinen ist der Clipping-Schritt erforderlich ist, wie in der Nähe räumliche Oberfläche Gitter häufig etwas überlappen.

## <a name="raycasting-and-collision"></a>Feinheiten beim Raycasting und Kollisionserkennung

In der Reihenfolge für eine Physik-API (z. B. [Havok](http://www.havok.com/)) um eine Anwendung mit den feinheiten beim Raycasting und kollisionserkennung Funktionen für räumliche Oberflächen zu gewährleisten, muss die Anwendung bereitstellen, räumliche Oberfläche vernetzt werden, um die Physik-API. Gitter, die häufig für Physik verwendet haben, die folgenden Eigenschaften:
* Sie enthalten nur kleine Anzahl von Dreiecken. Physik-Vorgänge sind mehr als Renderingvorgänge rechenintensiv.
* Sie sind "Water – strenge". Flächen, die als solid müssen nicht kleine aufweisen; sogar Löcher zu klein angezeigt werden, können Probleme verursachen.
* Sie werden in konvexe Schälkleie konvertiert. Konvexe Schälkleie haben einige Polygone und frei von Lücken, und sie sind viel besser rechnerisch effizient verarbeiten als unformatierte Dreieck Gitter.

Bei der Durchführung Raycasts für räumliche Oberflächen, beachten Sie, dass diese Oberflächen häufig komplex sind, wie überladen Formen unübersichtliche kleinen Details - nur vollständige Helpdesk! Dies bedeutet, dass eine einzelne Raycast häufig nicht ausreichend, um Sie genügend Informationen zur Form der Fläche und die Form der freie Speicherplatz in der Nähe erteilen. Es ist daher in der Regel eine gute Idee, viele Raycasts in einem kleinen Bereich durchzuführen und die aggregierten Ergebnisse zu verwenden, um einen Überblick über die Oberfläche des zuverlässiger abgeleitet werden. Z. B. ergibt Guide – Hologramm Platzierung auf einer Oberfläche mit den Mittelwert der 10 Raycasts weit reibungslose und weniger "ganz nervös" Ergebnis mit nur einem einzigen Raycast.

Allerdings beachten Sie, dass jede Raycast hohe rechenleistung Kosten verwenden kann. Also je nach Nutzungsszenario Sie sollten eine Abstimmung zwischen Rechenaufwand für zusätzliche Raycasts (jedes Einzelbild ausgeführt) für den Rechenaufwand für [mesh-Verarbeitung](spatial-mapping.md#mesh-processing) zu glätten und Entfernen von Lücken in räumlichen Oberflächen ( ausgeführt, wenn räumliche Gitter aktualisiert werden).

## <a name="troubleshooting"></a>Problembehandlung
* Damit für die Oberfläche Gitter ordnungsgemäß ausgerichtete werden kann muss jede "gameobject" aktiv sein, bevor sie an der SurfaceObeserver gesendet werden, die Gitter erstellt haben. Andernfalls werden die Gitter in Ihrem Bereich jedoch gedreht merkwürdige Winkel angezeigt.
* Das "gameobject", das führt das Skript, mit das kommuniziert mit dem SurfaceObserver muss an den Ursprung festgelegt werden. Andernfalls müssen alle "gameobjects", die Sie erstellen und Senden an der SurfaceObserver, damit ihre Gitter erstellt einen Offset, der gleich dem Offset des übergeordneten Objekts Spiel. Dadurch können Ihre Gitter, mehrere Zähler sofort wodurch es schwierig zu debuggen, was vor sich geht angezeigt werden.

## <a name="see-also"></a>Siehe auch
* [Koordinatensysteme](coordinate-systems.md)
* [Räumliche Zuordnung in DirectX](spatial-mapping-in-directx.md)
* [Räumliche Zuordnung in Unity](spatial-mapping-in-unity.md)
* [Räumliche Zuordnung entwerfen](spatial-mapping-design.md)
* [Fallstudie: Lücken in der Realität ansehen](case-study-looking-through-holes-in-your-reality.md)
