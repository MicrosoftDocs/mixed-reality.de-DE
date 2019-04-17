---
title: Cursor
description: Ein Cursor oder ein Indikator für die Zielgruppenadressierung anhand bestimmter Vektor, bietet kontinuierliches Feedback für den Benutzer zu verstehen, was zu seiner Wahlabsicht HoloLens versteht.
author: thetuvix
ms.author: alexturn, thgable
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (der 1. Generation), 2 für HoloLens, Mixed Reality, Cursor, als Ziel, Blicke, Gesten
ms.openlocfilehash: cdedcaffabe0f90e7956fdb19a7b85e202fcf403
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604655"
---
# <a name="cursors"></a>Cursor

> [!NOTE]
> Weitere Anleitungen, die speziell für HoloLens 2 [bald](index.md#news-and-notes).


Ein Cursor oder ein Indikator für Ihre aktuellen für die Zielgruppenadressierung Vektor bietet kontinuierliches Feedback für den Benutzer zu verstehen, in denen HoloLens davon ausgeht, des derzeitige Fokus zu diesem Zeitpunkt. Der Cursor kann die Benutzer ihre aktuellen Ziel zu verweisen und fungiert als Feedback an welche Bereich, Hologramm oder Punkte für die Eingabe reagiert. Es ist der digitalen Darstellung, in dem das Gerät die Aufmerksamkeit des Benutzers erkennt sein (obwohl, die nicht die gleichen wie die Bestimmung der zu seiner Wahlabsicht können).

Das Feedback zur Verfügung gestellt, mit dem Cursornamen bietet Benutzern die Möglichkeit, erwarten, wie das System reagiert, verwenden Sie dieses Signal als Feedback besser ihre Absicht mit dem Gerät zu kommunizieren und letztlich Vertrauen in deren Interaktionen.

## <a name="hololens-1st-gen"></a>HoloLens (1. Generation)

Zielgruppenadressierung von Inhalten auf HoloLens (1. Generation) erfolgt in erster Linie mit der [bestaunen](gaze.md) Vektor (ein Strahl, der von der Position und Drehung des Anfangswerts gesteuert wird). Dies bietet eine Form der direkte Eingabe, für den Benutzer, der wenig Lehre benötigt. Allerdings haben Benutzer mit einem nicht markierten Datencenter von Blicke für präzise ansteuern, damit ein Cursor wird sichergestellt, dass Benutzer den Punkt kennen, den sie aktuell Anzielen. 


## <a name="positioning"></a>Positionierung

Im Allgemeinen sollten der Indikator in ungefähr einer 1:1 mit Bewegungen verschieben. Es gibt einige Fälle, in dem Gewinn (erweitern oder Verschiebung deutlich abnehmende) kann als eine absichtliche Mechanikers verwendet werden, aber es verursacht Probleme für Benutzer, wenn Sie unerwartet verwendet (Beachten Sie, dass ein kleiner Teil 'Verzögerung' für den Cursor zur Vermeidung von Problemen mit empfohlen Anzeige-locked Inhalt). Vor allem jedoch Erfahrungen muss "ehrlich" in der Darstellung der Position des Mauszeigers – Wenn Glättung Magnetismus, Gewinn, oder andere Effekte sind enthalten, das System sollte weiterhin zeigt den Cursor ganz egal, wo die Systemvariable Verständnis der Position, mit denen ist Effekte enthalten. Der Cursor des Systems können Sie ganz von dem Benutzer mitteilt, wie sie können oder nicht damit interagieren, nicht des Benutzers Möglichkeit, dass sich das System.

Der Indikator sollte idealerweise im Detail auf beliebige Elemente gesperrt werden, die den Benutzer einiges angeben kann. Dies kann bedeuten Oberfläche sperrende, sofern vorhanden [räumliche Zuordnung](spatial-mapping.md) Mesh oder Sperren in die Tiefe von beliebigen "floating" UI-Elementen, die Benutzer wissen, was können sie interagieren in Echtzeit.

## <a name="cursor-design-principles"></a>Cursor-Entwurfsprinzipien

### <a name="always-present"></a>Immer vorhanden
* Es wird empfohlen, dass der Cursor noch immer vorhanden ist.
* Wenn der Benutzer den Cursor nicht finden kann, sind sie verloren gehen.
* Ausnahmen sind Instanzen, bei denen ein Cursor mit eine nicht optimalen Erfahrung für den Benutzer bietet. Ein Beispiel ist, wenn ein Benutzer ein Video überwacht wird. Der Cursor wird an dieser Stelle nicht erwünscht, da es ständig in der Mitte des Videos ist. Dies ist ein Szenario, in dem Sie berücksichtigen können, macht des Cursors nur sichtbar, wenn der Benutzer ihre Westentasche einrichten, der angibt, des Wunschs, eine Aktion verfügt. Andernfalls ist es nicht auf das Video angezeigt.

### <a name="cursor-scale"></a>Cursor-Skalierung
* Der Cursor befinden sollte nicht größer als die verfügbaren Ziele, sodass Benutzer auf einfache Weise interagieren und den Inhalt anzeigen.
* Je nach der Erfahrung, die Sie erstellen, ist das Skalieren des Cursors, wie der Benutzer sich sieht auch ein wichtiger Aspekt. Beispielsweise, wie der Benutzer weitere Token in Ihrer Umgebung möglicherweise der Cursor sollte nicht werden zu klein, dass die verloren gehen.
* Beim Skalieren des Cursors Anwendungsbereiche eine weiche Animation, wie die Skalierung ist es ein natürliches Eindruck erhalten.
* Vermeiden Sie die Inhalte sitzt. Hologramme sind, was die benutzerfreundlichkeit ansprechender zu gestalten, und der Cursor sollte nicht die von ihnen weg.

### <a name="directionless-cursor"></a>Richtungslose cursor
* Zwar keine eine Form des richtigen Cursors ist, empfehlen wir, dass Sie eine richtungslose Form wie ein Torus oder etwas anderes verwenden. Ein Cursor, der in eine Richtung zeigt (Beispiel: eine herkömmliche Pfeilcursor) kann den Benutzer immer auf diese Weise sehen verwechseln.
* Eine Ausnahme ist, wenn den Cursor zu verwenden, um die Interaktion-Anweisung für den Benutzer zu kommunizieren. Beispielsweise enthält der Cursor Hologramme in der Shell von Windows Holographic zu skalieren, vorübergehend Pfeile, die dabei helfen, den Benutzer dazu, wie ihre Westentasche Verschieben der Hologramm skalieren.

### <a name="look-and-feel"></a>Aussehen und Verhalten
* Ein Ringdiagramm oder Torus strukturiert Cursor funktioniert für eine Vielzahl von Anwendungen.
* Wählen Sie eine Farbe und Form, die am besten auf der Benutzeroberfläche darstellt, die Sie erstellen.
* Cursor sind besonders anfällig für [Farbe Trennung](hologram-stability.md#color-separation).
* Ein kleinerer Cursor mit ausgeglichene Deckkraft sieht es immer ohne großen der visuellen Hierarchie informativ.
* Darüber im Klaren sein Shadows oder Highlights hinter den Cursor zu verwenden, kann Inhalt antidebugverhalten und von den Zweck abgelenkt werden.
* Cursor ausrichten und die Flächen in Ihrer app hug sollten, dies gibt dem Benutzer, einen Eindruck, dass das System sehen kann, in dem sie suchen, sondern auch das System ist von ihrer Umgebung beachten.
* Des Betriebssystems Windows Holographic werden die z. B. der Cursor auf die Oberflächen des Benutzers Welt, erstellen einen Eindruck der ganzen Welt wissen auch, wenn der Benutzer direkt ggf. ein Hologramm betrachten ist nicht...
* Den Cursor auf ein interaktives Element magnetisch sperren, wenn es innerhalb der Nähe. Dies kann helfen, verbessern die Gewissheit, dass das Element dieser Benutzer interagieren wird, wenn sie eine Aktion durchführen.

### <a name="visual-cues"></a>Visuelle Hinweise
* Gibt es eine Vielzahl von Informationen in unserer Welt und mit Hologramme fügen wir weitere Informationen. Ein Cursor ist eine hervorragende Möglichkeit für den Benutzer zu kommunizieren, was wichtig ist.
* Wenn Ihre Umgebung auf einem einzelnen Hologramm den Fokus besitzt, klicken Sie dann möglicherweise der Cursor richtet und hugs nur, dass – Hologramm und Änderungen Form von diesem – Hologramm sehen. Dies kann für den Benutzer übermitteln, Hologramm ist ein Sonderfall und sie können mit ihm interagieren.
* Wenn Ihre Anwendung räumliche Zuordnung verwendet wird, konnte klicken Sie dann der Cursor ausrichten und hug jede Oberfläche, die es angezeigt wird. Dadurch Feedback an die Benutzer, HoloLens und Ihre Anwendung kann der Speicherplatz.
* Diese Schritte dabei helfen, die Tatsache zu verstärken, die Hologramme echten und in unserer Welt sind. Sie können die Lücke zwischen realen und virtuellen.
* Haben Sie eine Vorstellung davon, was der Cursor ausführen soll, wenn es keine Hologramme oder Flächen in der Ansicht. Legen Sie das Element in einem zuvor festgelegten Abstand vor dem Benutzer ist eine Option.

## <a name="cursor-feedback"></a>Cursor-feedback

Wie bereits, dass es wird empfohlen erwähnt, dass der Cursor, die immer vorhanden sein, da Sie den Cursor verwenden können, um einige wichtigen Zustandsbits, Informationen zu übermitteln.

### <a name="possible-actions"></a>Mögliche Aktionen
* Der Benutzer am ggf. ein Hologramm gazing ist, und der Cursor befindet sich auf diese – Hologramm, können Sie den Cursor verwenden, mögliche Aktionen für diese – Hologramm zu übermitteln.
* Sie können ein Symbol angezeigt, für den Cursor, den der Benutzer z. B. erwerben kann, die skaliert werden, – Hologramm Element oder vielleicht. Oder sogar etwas so einfaches sein wie die Hologramm auf getippt werden kann.
* Fügen Sie zusätzliche Informationen nur für den Cursor hinzu, wenn dies etwas an den Benutzer bedeutet. Andernfalls Benutzer können entweder nicht beachten Sie, dass die Änderungen des Ansichtszustands oder Abrufen der Cursor verwechselt.

### <a name="input-state"></a>Eingabestatus
* Wir konnten den Cursor verwenden, um die Eingabe Status des Benutzers angezeigt. Beispielsweise kann ein Symbol, das dem Benutzer mitteilt, wenn das System manuell Zustand wird angezeigt. Dadurch wird dem Benutzer angewiesen, dass die Anwendung, dass der Benutzer erkennt eine Aktion bereit.
* Wir können auch den Cursor verwenden, um dem Benutzer beachten, dass es ein Sprachbefehl verfügbar ist. Oder vielleicht ändern Sie die Farbe des Cursors vorübergehend auf den Benutzer informieren, dass der Voice-Befehl durch das System gehört wurde.

Diese anderen Cursor-Status können auf unterschiedliche Weise implementiert werden. Sie können diese Zustände implementieren, durch den Cursor wie ein Zustandsautomat modellieren. Zum Beispiel:
* Im Leerlauf ist, wenn Sie den Standardcursor angezeigt.
* Status "bereit" ist, wenn Sie bereit Position des Benutzers manuell erkannt haben.
* Interaktionszustand ist, wenn der Benutzer eine bestimmte Aktivität ausgeführt wird.
* Mögliche Aktionen Zustand ist, wenn es sich bei mögliche Aktionen zu vermitteln, die für die ggf. ein Hologramm ausgeführt werden können.

Sie können auch diese Zustände Weise eine Skin-fähig implementieren, sodass andere Grafikobjekte angezeigt werden können, wenn verschiedene Zustände erkannt werden.

## <a name="going-cursor-free"></a>Also "Cursor-freies"

Entwerfen, ohne einen Cursor wird empfohlen, nur, wenn die Bedeutung von Immersion eine wichtige Komponente einer Erfahrung ist und Interaktionen (über Blicke und Bewegung) als Ziel verwendet werden, aber keine gute Genauigkeit. Das System muss weiterhin die Anforderungen erfüllen, die normalerweise von einem cursorvorbereitenden jedoch - erfüllt werden fortlaufende Feedback zum Verständnis des Systems, ihre Anwendungen für Benutzer bereitstellen und Sie besser ihre Absicht mit dem System zuverlässig kommunizieren. Dies kann über andere nennenswerte Zustandsänderungen erreicht werden.

## <a name="see-also"></a>Siehe auch
* [Gesten](gestures.md)
* [Blicke für](gaze-targeting.md)
