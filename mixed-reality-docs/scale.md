---
title: Skalieren
description: Ein wichtiger Aspekt bei der realistischen Wirkung von holografisch dargestellten Inhalten ist das möglichst genaue Nachahmen der visuellen Statistik der echten Welt.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Gemischte Windows-Realität, Stil, Entwurf
ms.openlocfilehash: eeec28fbf98cf4386a57cde4452cd3f8977d7780
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437506"
---
# <a name="scale"></a>Skalieren

Ein wichtiger Aspekt bei der realistischen Wirkung von holografisch dargestellten Inhalten ist das möglichst genaue Nachahmen der visuellen Statistik der echten Welt. Das bedeutet, so viele visuelle Hinweise wie möglich einzubeziehen, die uns (in der realen Welt) zu verstehen helfen, wo sich Objekte befinden, wie groß sie sind und woraus sie bestehen. Die Skalierung eines Objekts ist eine der wichtigsten dieser visuellen Hinweise und gibt einem Viewer einen Eindruck von der Größe eines Objekts sowie von Hinweisen zu seiner Position (insbesondere bei Objekten mit einer bekannten Größe). Außerdem wurde das Anzeigen von Objekten in einer realen Skala als eines der wichtigsten Unterschiede bei gemischter Realität im allgemeinen angesehen – etwas, das bei der bildschirmbasierten Anzeige zuvor nicht möglich war.

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a>Vorschlagen der Skalierung von Objekten und Umgebungen

Es gibt viele Möglichkeiten, die Skalierung eines Objekts vorzuschlagen, von denen einige mögliche Auswirkungen auf andere perzeptive Faktoren haben. Der Schlüssel besteht darin, die Objekte einfach in der Größe "Real" anzuzeigen und diese realistische Größe beizubehalten, wenn Benutzer sich bewegen. Dies bedeutet, dass holograms eine andere Menge an Sicht des visuellen Elements eines Benutzers in die gleiche Weise erhalten, wie es bei echten Objekten der Fall ist.

### <a name="utilize-the-distance-of-objects-as-they-are-presented-to-the-user"></a>Verwenden Sie den Abstand von Objekten, wie Sie dem Benutzer angezeigt werden.

Eine gängige Methode besteht darin, den Abstand von Objekten zu nutzen, wie Sie für den Benutzer angezeigt werden. Nehmen Sie beispielsweise an, dass Sie ein großes Familienfahrzeug vor dem Benutzer visualisieren. Wenn sich das Auto direkt davor befand, wäre es bei der Arm-Länge zu groß, damit es in das Feld des Benutzers passt. Dies würde dazu führen, dass der Benutzer seine Kopfzeile und den Hauptteil verschieben muss, um das gesamte Objekt zu verstehen. Wenn das Fahrzeug weiter entfernt wurde (im gesamten Raum), kann der Benutzer einen Eindruck von der Skalierung feststellen, indem er das gesamte Objekt in der Ansicht sehen kann, und sich dann näher an den Bereich bewegen, um Bereiche im Detail zu überprüfen.

:::row:::
    :::column:::
        **[Mit diesem Verfahren wurde von Volvo ein Showroom](https://www.youtube.com/watch?v=DilzwF90vec)** für ein neues Auto erstellt, das die Skalierung des Holographic Car auf eine Weise nutzte, die für den Benutzer realistisch und intuitiv war. Die Benutzeroberflächen beginnen mit einem Hologramm des Autos für eine physische Tabelle, sodass der Benutzer die Gesamtgröße und Form des Modells verstehen kann. Zu einem späteren Zeitpunkt wächst das Auto in eine größere Skalierung (über die Größe des Geräts hinaus), aber da der Benutzer bereits einen Verweis aus dem kleineren Modell abgerufen hat, kann er auf die Features des Autos angemessen navigieren.<br>
        <br>
        *Image: Volvo Cars-Darstellung für hololens*
    :::column-end:::
        :::column:::
       ![Volvo Cars-Darstellung für hololens](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

### <a name="use-holograms-to-modify-the-users-real-space"></a>Verwenden Sie holograms, um den tatsächlichen Bereich des Benutzers zu ändern.

Eine andere Methode ist die Verwendung von holograms, um den tatsächlichen Bereich des Benutzers zu ändern, die vorhandenen Wände oder Obergrenzen durch Umgebungen zu ersetzen oder "Löcher" oder "Windows" anfügen, sodass mehrstufige Objekte den physischen Raum scheinbar "durchbrechen" können. Beispielsweise kann eine große Struktur nicht in die meisten Benutzer Räume passen, sondern durch das Platzieren eines virtuellen Himmels auf die virtuelle Oberfläche. Dadurch kann der Benutzer die Basis der virtuellen Struktur durchlaufen und einen Eindruck davon erfassen, wie er in der Praxis aussehen würde, und dann sehen, dass er sich weit über den physischen Raum des Raums hinaus erstreckt.

:::row:::
    :::column:::
        **[Minecraft entwickelte](https://minecraft.net/)** mithilfe einer ähnlichen Technik ein Konzept. Durch Hinzufügen eines virtuellen Fensters zu einer physischen Oberfläche in einem Raum werden die vorhandenen Objekte im Raum im Kontext einer erheblich größeren Umgebung platziert, die über die physischen Skalierungs Beschränkungen des Raums hinausgeht.<br>
        <br>
        *Image: minecraft Concept-Darstellung für hololens*
    :::column-end:::
        :::column:::
       ![Minecraft Concept-Darstellung für hololens](images/800px-minecraftwindow-640px.jpg)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="experimenting-with-scale"></a>Experimentieren mit der Skala

In manchen Fällen haben Designer mit der Änderung der Skala experimentieren (indem Sie die angezeigte "echte" Größe des Objekts geändert haben) und gleichzeitig eine einzelne Position des Objekts beibehalten. so kann ein Objekt ohne wirkliche Bewegung näher oder weiter in einen Viewer gelangen. Dies wurde in einigen Fällen getestet, um die Anzeige von Elementen zu beschleunigen, während gleichzeitig die möglichen Komfort Beschränkungen beim Anzeigen von virtuellen Inhalten, die näher sind als die "Zone der Bequemlichkeit", zu berücksichtigen sind.

Dadurch können einige mögliche Artefakte in der-Darstellung erstellt werden:
* Bei virtuellen Objekten, die ein Objekt mit der "bekannten" Größe des Viewers darstellen, führt das Ändern der Skala ohne Änderung der Position zu Konflikt verursachenden visuellen Hinweisen – die Augen können das Objekt in gewisser Weise aufgrund von verseh-hinweisen (siehe [Komfort](comfort.md) Weitere Informationen hierzu finden Sie in diesem Artikel, aber die Größe fungiert als monokulärer Hinweis darauf, dass das Objekt möglicherweise näher kommt. Diese Konflikt verursachenden Hinweise führen zu verwirrten Wahrnehmungen – Betrachter sehen das Objekt oft als vorhanden (aufgrund der Konstanten Tiefe), werden jedoch schnell vergrößert.
* In einigen Fällen wird die Skalierungs Änderung stattdessen als "sich abzeichtender" Hinweis betrachtet, wobei das Objekt möglicherweise nicht angezeigt wird, um die Skalierung durch einen Viewer zu ändern, aber anscheinend direkt in den Augenblick des Viewers verschoben wird (was eine unangenehme Sensation sein kann).
* Bei Vergleichs Oberflächen in der realen Welt werden solche Skalierungs Änderungen manchmal als veränderliche Position entlang mehrerer Achsen angezeigt – Objekte werden möglicherweise herabgestuft, anstatt sich näher zu bewegen (ähnlich in einer 2D-Projektion der 3D-Bewegung in einigen Fällen).
* Schließlich kann das Ändern der Skalierung für Objekte ohne bekannte Größe (z. b. beliebige Formen mit beliebigen Größen, Benutzeroberflächen Elementen usw.) funktionell als eine Möglichkeit fungieren, Änderungen in der Entfernung zu imitieren – Betrachter haben nicht so viele vorvorhandene Top-Down-Hinweise, nach denen Sie verstehen Sie die tatsächliche Größe oder den Speicherort des Objekts, sodass die Skalierung als wichtiger Hinweis verarbeitet werden kann.

<br>

---

## <a name="see-also"></a>Weitere Informationen:
* [Farbe, Licht und Materialien](color,-light-and-materials.md)
* [Typografie](typography.md)
* [Raumklangentwurf](spatial-sound-design.md)
