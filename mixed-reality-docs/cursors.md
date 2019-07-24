---
title: Cursor
description: Ein Cursor oder Indikator Ihres Ziel Vektor bietet fortlaufendes Feedback für den Benutzer, um zu verstehen, was hololens über seine Absichten versteht.
author: thetuvix
ms.author: alexturn, thgable
ms.date: 02/24/2019
ms.topic: article
keywords: Hololens (1. Gen), hololens 2, gemischte Realität, Cursor, Zielvorgabe, Blick, Gesten
ms.openlocfilehash: cdedcaffabe0f90e7956fdb19a7b85e202fcf403
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526212"
---
# <a name="cursors"></a>Cursor

> [!NOTE]
> Weitere Anleitungen sind für hololens 2 in [Kürze](index.md#news-and-notes)verfügbar.


Ein Cursor oder Indikator Ihres aktuellen Ziel Vektor bietet fortlaufendes Feedback für den Benutzer, um zu verstehen, wo hololens glaubt, dass der aktuelle Fokus zu diesem Zeitpunkt liegt. Der Cursor ermöglicht dem Benutzer das Verständnis seines aktuellen Zielpunkts und fungiert als Feedback, um anzugeben, welcher Bereich, welches Hologramm oder welcher Punkt auf die Eingabe reagiert. Dabei handelt es sich um die digitale Darstellung von, bei der das Gerät die Aufmerksamkeit des Benutzers versteht (obwohl dies möglicherweise nicht der gleiche ist wie das Ermitteln von Informationen über ihre Absichten).

Das vom Cursor bereitgestellte Feedback bietet Benutzern die Möglichkeit, zu sehen, wie das System antwortet, und verwendet dieses Signal als Feedback, um ihre Absicht an das Gerät besser zu vermitteln, und schließlich ist es sicherer, sich über ihre Interaktionen zu informieren.

## <a name="hololens-1st-gen"></a>HoloLens (1. Generation)

Die Zielsetzung von Inhalten in hololens (1. Gen) erfolgt hauptsächlich mit dem [Blick](gaze.md) Vektor (ein Strahl, der von der Position und Drehung des Kopfes gesteuert wird). Dies bietet eine direkte Eingabe für den Benutzer, der nur wenig Lehrkräfte benötigt. Benutzer haben jedoch Schwierigkeiten bei der Verwendung eines nicht markierten Mittelpunkts für die genaue Ausrichtung, sodass ein Cursor sicherstellt, dass Benutzer den Punkt kennen, auf den Sie aktuell abzielen. 


## <a name="positioning"></a>Positionierung

Im Allgemeinen sollte der Indikator in ungefähr einem 1:1-Verhältnis mit Head Movement verschoben werden. Es gibt einige Fälle, in denen der Gewinn (Vergrößerung oder abnehmender Verschiebungs Aufwand) als beabsichtigter Mechaniker verwendet werden kann. es werden jedoch Probleme für Benutzer verursacht, wenn Sie unerwartet verwendet werden. (Beachten Sie, dass für den Cursor ein kleines Bit von "lag" empfohlen wird, um Probleme mit zu vermeiden. vollständig Anzeige-gesperrter Inhalt). Am wichtigsten ist jedoch, dass Erfahrungen in der Darstellung der Cursorposition "ehrlich" sein sollten. wenn Glättung, Magnetismus, Gewinn oder andere Effekte eingeschlossen werden, sollte das System den Cursor immer noch anzeigen, wenn das System die Position hat. Effekte enthalten. Der Cursor ist das System, um dem Benutzer mitzuteilen, womit er interagieren kann, und nicht die Möglichkeit des Benutzers, dem System mitzuteilen.

Der Indikator sollte idealerweise eine Tiefe Sperre für alle Elemente erhalten, auf die der Benutzer ein Ziel haben kann. Dies kann zu einer Oberflächen Sperre führen, wenn es ein [räumliches Mapping](spatial-mapping.md) -Mesh oder eine Sperre für die Tiefe aller "unverankerten" Benutzeroberflächen Elemente gibt, um dem Benutzer zu helfen, die Interaktion mit in Echtzeit zu verstehen.

## <a name="cursor-design-principles"></a>Cursor Entwurfs Prinzipien

### <a name="always-present"></a>Immer vorhanden
* Es wird empfohlen, dass der Cursor immer vorhanden ist.
* Wenn der Benutzer den Cursor nicht finden kann, gehen diese verloren.
* Ausnahmen hierfür sind Instanzen, bei denen ein Cursor eine suboptimale Benutzer Darstellung für den Benutzer bereitstellt. Ein Beispiel hierfür ist ein Benutzer, der ein Video überwacht. Der Cursor wird an dieser Stelle nicht mehr erwünscht sein, da er sich in der Mitte des Videos ständig befindet. Hierbei handelt es sich um ein Szenario, in dem Sie den Cursor nur dann sichtbar machen können, wenn der Benutzer seine Hand anweist, eine Aktion durchführen zu müssen. Andernfalls ist Sie im Video nicht sichtbar.

### <a name="cursor-scale"></a>Cursor Skala
* Der Cursor sollte nicht größer sein als die verfügbaren Ziele, sodass Benutzer problemlos mit dem Inhalt interagieren und ihn anzeigen können.
* Abhängig von der Umgebung, die Sie erstellen, ist das Skalieren des Cursors, wie der Benutzer aussieht, auch ein wichtiger Aspekt. Wenn der Benutzer z. b. in der Umgebung weiter geht, sollte der Cursor nicht zu klein werden, sodass er verloren geht.
* Beim Skalieren des Cursors empfiehlt es sich, bei der Skalierung eine weiche Animation anzuwenden.
* Vermeiden Sie das Blockieren von Inhalt. Holograms machen das Erlebnis als unvergesslich, und der Cursor sollte nicht davon entfernt werden.

### <a name="directionless-cursor"></a>Directionless-Cursor
* Obwohl es keine Rechte Cursor Form gibt, empfiehlt es sich, eine direktionale Form wie einen "Tor" oder etwas anderes zu verwenden. Ein Cursor, der in einer Richtung zeigt (z.: ein herkömmlicher Pfeilcursor), kann den Benutzer so verwechseln, dass er immer auf diese Weise aussieht.
* Eine Ausnahme besteht darin, dass der Cursor verwendet wird, um dem Benutzer Interaktions Anweisungen mitzuteilen. Wenn z. b. Hologramme in der Windows Holographic Shell skaliert werden, schließt der Cursor temporär Pfeile ein, die den Benutzer anweisen, wie Sie seine Hand bewegen, um das Hologram zu skalieren.

### <a name="look-and-feel"></a>Aussehen und Gefühl
* Ein Ring Diagramm oder ein mit einem Tor gegeformter Cursor funktioniert für viele Anwendungen.
* Wählen Sie eine Farbe und eine Form aus, die die von Ihnen erstellten Funktionen am besten repräsentiert.
* Cursor sind besonders anfällig für die [Trennung von Farben](hologram-stability.md#color-separation).
* Ein kleiner Cursor mit ausgewogener Deckkraft sorgt dafür, dass er informativ ist, ohne die visuelle Hierarchie zu dominieren.
* Stellen Sie sich vor, dass Schatten oder Highlights hinter dem Cursor verwendet werden, da Sie Inhalte behindern und vom Zweck abweichen können.
* Cursor sollten sich an den Oberflächen in der APP ausrichten und Sie anspiegeln. Dadurch erhält der Benutzer ein Gefühl, dass das System sehen kann, wo er aussieht, aber auch, dass das System seine Umgebung kennt.
* Im Windows Holographic-Betriebssystem richtet sich der Cursor z. b. an den Oberflächen der Benutzer Welt, wodurch ein Gefühl der Kenntnis der Welt entsteht, auch wenn der Benutzer nicht direkt an einem Hologram interessiert ist.
* Sperrt den Cursor magnetisch zu einem interaktiven Element, wenn er sich innerhalb der Nähe befindet. Dadurch kann das Vertrauen verbessert werden, dass Benutzer mit diesem Element interagieren, wenn Sie eine Auswahl Aktion ausführen.

### <a name="visual-cues"></a>Visuelle Hinweise
* Es gibt zahlreiche Informationen in unserer Welt und mit holograms werden weitere Informationen hinzugefügt. Ein Cursor ist eine großartige Möglichkeit, mit dem Benutzer zu kommunizieren, was wichtig ist.
* Wenn sich Ihre Benutzeroberflächen auf ein einzelnes Hologramm konzentrieren, richtet sich der Cursor möglicherweise nur an das – Hologramm und die Form "ändern", wenn Sie dieses Hologramm betrachten. Dadurch kann der Benutzer übermittelt werden, dass es sich um ein spezielles – Hologramm handelt, und Sie können damit interagieren.
* Wenn Ihre Anwendung eine räumliche Zuordnung verwendet, könnte der Cursor jede sichtbare Oberfläche ausrichten und umarmen. Dadurch erhalten die Benutzer Feedback, dass hololens und Ihre Anwendung Ihren Speicherplatz sehen können.
* Dies trägt dazu bei, die Tatsache zu verstärken, dass holograms Real und in unserer Welt sind. Sie helfen dabei, die Lücke zwischen Real und Virtual zu überbrücken.
* Sehen Sie sich an, was der Cursor tun soll, wenn keine holograms oder Oberflächen in der Ansicht vorhanden sind. Eine Möglichkeit besteht darin, den Benutzer in einem vordefinierten Abstand vor dem Benutzer zu platzieren.

## <a name="cursor-feedback"></a>Cursor Feedback

Wie bereits erwähnt, empfiehlt es sich, den Cursor immer darzustellen, da Sie den Cursor verwenden können, um einige wichtige Informationen zu vermitteln.

### <a name="possible-actions"></a>Mögliche Aktionen
* Wenn der Benutzer mit einem – Hologramm und der Cursor sich auf diesem – Hologramm befindet, können Sie den Cursor verwenden, um mögliche Aktionen für dieses – Hologramm zu übermitteln.
* Sie können ein Symbol auf dem Cursor anzeigen, über das der Benutzer beispielsweise das Element erwerben kann, oder dieses Hologramm skalieren. Oder auch etwas so einfaches wie das – Hologramm kann angetippt werden.
* Fügen Sie dem Cursor nur dann zusätzliche Informationen hinzu, wenn er etwas für den Benutzer bedeutet. Andernfalls bemerken die Benutzer möglicherweise nicht, dass sich der Status ändert, oder Sie werden durch den Cursor verwirrt.

### <a name="input-state"></a>Eingabe Status
* Der Cursor kann verwendet werden, um den Eingabe Zustand des Benutzers anzuzeigen. Beispielsweise könnte ein Symbol angezeigt werden, das dem Benutzer mitteilt, ob das System seinen Hand Zustand sieht. Dadurch wird dem Benutzer mitgeteilt, dass die Anwendung weiß, dass der Benutzer bereit ist, Aktionen auszuführen.
* Wir könnten den Cursor auch verwenden, um dem Benutzer zu ermöglichen, dass ein Sprachbefehl verfügbar ist. Oder Sie können die Farbe des Cursors vorübergehend ändern, um dem Benutzer mitzuteilen, dass der Sprachbefehl vom System gehört.

Diese verschiedenen Cursor Zustände können auf unterschiedliche Weise implementiert werden. Sie können diese verschiedenen Zustände implementieren, indem Sie den Cursor wie einen Zustands Automat modellieren. Zum Beispiel:
* Im Leerlaufzustand wird der Standard Cursor angezeigt.
* Der Status "bereit" ist, wenn Sie festgestellt haben, dass die Benutzer die Hand in der Bereitschaft haben.
* Der Interaktions Zustand ist, wenn der Benutzer eine bestimmte Interaktion ausführt.
* Der mögliche Aktions Status ist, wenn Sie mögliche Aktionen übermitteln, die für ein Hologram ausgeführt werden können.

Sie können diese Zustände auch auf die gleiche Weise implementieren, sodass Sie unterschiedliche Kunstobjekte anzeigen können, wenn verschiedene Zustände erkannt werden.

## <a name="going-cursor-free"></a>"Cursor frei"

Das Entwerfen ohne Cursor wird nur empfohlen, wenn das Eintauchen eine wichtige Komponente einer-Funktion ist und Interaktionen, bei denen die Zielvorgabe (durchschauen und Gesten) einbezogen werden, keine hohe Genauigkeit erfordern. Das System muss die Anforderungen, die normalerweise von einem Cursor erfüllt werden, trotzdem erfüllen, um den Benutzern Kontinuierliches Feedback zum Verständnis der Zielsetzung des Systems zu bieten und Sie dabei zu unterstützen, ihre Absichten zuverlässig an das System zu übermitteln. Dies kann durch andere spürbare Zustandsänderungen erreicht werden.

## <a name="see-also"></a>Siehe auch
* [Gesten](gestures.md)
* [Anvisieren](gaze-targeting.md)
