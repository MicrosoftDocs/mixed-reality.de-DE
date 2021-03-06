---
title: Was ist ein Hologram?
description: Hololens ermöglicht Ihnen das Anzeigen und interagieren mit dreidimensionalen holograms, Objekten aus Licht und Sound, die auf der ganzen Welt angezeigt werden.
author: beaufolsom
ms.author: befolsom
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, hololens, holograms, Design, Interaktion
ms.openlocfilehash: 5fb3aff3f59d0999676356d257b72f286a8d7adf
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435127"
---
# <a name="what-is-a-hologram"></a>Was ist ein Hologram?

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


Hololens ermöglicht Ihnen das Erstellen von **holograms**, aus Licht und Sound bestehenden Objekten, die auf der ganzen Welt angezeigt werden, genau so, als wären Sie echte Objekte. Holograms reagieren auf Ihre [Blicke](gaze-and-commit.md), [Gesten](gaze-and-commit.md#composite-gestures) und [Sprachbefehle](voice-input.md)und können mit [realen Oberflächen](spatial-mapping.md) um Sie interagieren. Mit Hologrammen können Sie digitale Objekte erstellen, die Teil Ihrer Welt sind.

<br>


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
        <td>Hologramme</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a>Ein – Hologramm besteht aus Licht und Sound.

Die Hologramme, die von [hololens](rendering.md) gerendert werden, werden im Holographic-Frame direkt vor den Augen des Benutzers angezeigt. Holograms können ihrer Welt ein Licht hinzufügen, was bedeutet, dass Sie sowohl das Licht aus der Anzeige als auch das Licht aus Ihrer Umgebung sehen. Hololens entfernt das Licht nicht aus den Augen, sodass holograms nicht mit der Farbe schwarz gerendert werden können. Der schwarze Inhalt wird stattdessen als transparent angezeigt.

Holograms können viele verschiedene Erscheinungsformen und Verhaltensweisen aufweisen. Einige sind realistisch und solide, andere sind cartoonhaften und ethereal. Holograms können Features in Ihrer Umgebung hervorheben, und Sie können Elemente in der Benutzeroberfläche Ihrer APP sein.

![Hände Bearbeitung eines holograms](images/hologram-hands-940px.jpg)

Holograms können auch [Sounds](spatial-sound.md)erstellen, die von einer bestimmten Stelle in Ihrer Umgebung ausgehen. Bei hololens stammt der Sound von zwei Referenten, die sich direkt über Ihren Ohren befinden, ohne Sie zu decken. Ähnlich wie bei den-Anzeigen sind die Referenten Additiv und stellen neue Sounds vor, ohne die Klänge in Ihrer Umgebung zu blockieren.

<br>

---

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>Ein – Hologramm kann zusammen mit Ihnen in der Welt oder im Tag platziert werden.

Wenn Sie über einen bestimmten Ort verfügen, an dem Sie ein Hologram haben möchten, können Sie ihn genau auf der ganzen Welt [platzieren](coordinate-systems.md) . Wenn Sie dieses Hologramm durchlaufen, erscheint es in Bezug auf die weltweite Umgebung stabil. Wenn Sie ein [räumliches Anker](coordinate-systems.md#spatial-anchors) verwenden, um das Objekt an die Welt zu Heften, kann sich das System sogar merken, wo Sie es verlassen haben, wenn Sie es später zurückkehren.

![Zwei Männer, die das Microsoft Dynamics 365-Layout in einem Einzelhandelsbereich verwenden](images/HLS19_retailLayoutHologram_001-940px.jpg)

Einige Hologramme folgen dem Benutzer. Diese tagbasierten holograms positionieren sich in Bezug auf den Benutzer unabhängig davon, wo Sie sich befinden. Sie können sich auch ein – Hologramm für eine Weile mit Ihnen anmelden und dann auf der Wand platzieren, sobald Sie zu einem anderen Raum gelangen.

**Empfohlene Methoden**
* In einigen Szenarien kann es sinnvoll sein, dass holograms im gesamten Szenario leicht erkennbar oder sichtbar sind. Es gibt zwei allgemeine Vorgehensweisen für diese Art der Positionierung. Wir nennen Sie **"Display-Locked"** und **"Body-Locked"** .
   * Anzeige-gesperrte Inhalte sind auf der Geräte Anzeige Positions bedingt "gesperrt". Dies ist aus verschiedenen Gründen schwierig, einschließlich eines unnatürlichen Gefühls der "clingyness", bei dem viele Benutzer frustriert sind und diese "Schütteln" möchten. Im Allgemeinen haben viele Designer besser festgestellt, dass Inhalte mit der Anzeige nicht gesperrt werden.
   * Der Body-Locked-Ansatz ist weitaus besser verzeihbar. Die Text Sperre erfolgt, wenn ein – Hologramm in den Textkörper oder den Blick Vektor des Benutzers verschoben wird, aber im 3D--Bereich um den Benutzer positioniert ist. Viele Benutzeroberflächen haben ein Verhalten bei der Text Sperrung übernommen, bei dem das – Hologramm "dem Benutzer angezeigt wird, sodass der Benutzer Ihren Text drehen und durch Leerzeichen bewegen kann, ohne das – Hologramm zu verlieren. Durch die Einbindung einer Verzögerung wird die – Hologramm-Bewegung natürlicher. Beispielsweise verwendet eine zentrale Benutzeroberfläche des Windows Holographic-Betriebssystems eine Variation von Body-Locks, die auf den Blick des Benutzers folgt, mit einer sanften, elastischen, elastischen Verzögerung, während der Benutzer den Kopf schaltet.
* Platzieren Sie das – Hologramm in einer bequemen Anzeige Distanz, die in der Regel ungefähr 1-2 Meter von der Kopfzeile entfernt ist.
* Stellen Sie eine Menge an Abweichungen für Elemente bereit, die sich ständig im Holographic-Frame befinden müssen, oder animieren Sie den Inhalt auf einer Seite der Anzeige, wenn der Benutzer seine Ansicht ändert.

**Platzieren Sie holograms in der optimalen Zone (zwischen 1,25 Mio. und 5 Mio.).**

Zwei Verbrauchseinheiten sind das beste, und die Leistung ist geringer, je näher Sie von einer Verbrauchseinheit bekommen. Bei Entfernungen, die näher als eine Verbrauchseinheit liegen, ist die Wahrscheinlichkeit, dass Hologramme, die regelmäßig ausführlich verschoben werden, eher problematisch als bei stationären holograms. Denken Sie daran, ihre Inhalte zu schließen oder zu bereinigen, wenn Sie zu geschlossen werden, um den Benutzer nicht zu einem unerwarteten Benutzer Ergebnis zu vereinigen.

![Optimale Entfernung zum Platzieren von holograms vom Benutzer.](images/distanceguiderendering-950px.png)

<br>

---


## <a name="a-hologram-interacts-with-you-and-your-world"></a>Ein – Hologramm interagiert mit Ihnen und ihrer Welt.

Holograms sind nicht nur für Light und Sound. Sie sind auch ein aktiver Teil ihrer Welt. Sehen Sie sich ein – Hologramm und eine Geste mit der Hand an, und ein – Hologramm kann Ihnen folgen. Übergeben Sie einen Sprachbefehl an ein Hologram, und lassen Sie sich Antworten.

![Gruppe von Behörden, die Microsoft hololens 2 verwenden, um an einem Wind-Farm-Entwicklungsprojekt zusammenzuarbeiten](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

Holograms ermöglichen persönliche Interaktionen, die an anderer Stelle nicht möglich sind. Da hololens weiß, wo es sich auf der Welt befindet, kann ein holografisches Zeichen Sie direkt in den Augen sehen, während Sie den Raum durchlaufen.

Ein – Hologramm kann auch mit Ihrer Umgebung interagieren. Sie können z. b. einen Holographic-Sprung-Ball oberhalb einer Tabelle platzieren. Sehen Sie sich dann mit einem [Luftbild](gaze-and-commit.md#composite-gestures)den Ball Sprung an, und machen Sie einen Sound, wenn er auf die Tabelle trifft.

Holograms können auch durch reale Objekte verdeckt werden. Ein holografisches Zeichen kann z. b. durch eine Tür und hinter einer Wand aus der Sicht laufen.

**Tipps für die Integration von holograms und der realen Welt**
* Durch Ausrichten an Gravitations Regeln ist holograms leichter zu identifizieren und besser zu glauben. Beispiel: Platzieren Sie einen Holographic Dog auf der Basis & eine Vase in der Tabelle, anstatt Sie in den Raum zu versetzen.
* Viele Designer haben festgestellt, dass Sie durch das Erstellen eines "negativen Schattens" auf der Oberfläche, auf der sich das – Hologramm befindet, eine sicherere Integration von holograms möglich macht. Dies geschieht, indem ein weicher Glanz am Ende um das Hologramm erstellt und dann der "Schatten" aus dem Glanz subtrahieren wird. Der weiche Glanz ist in das Licht aus der realen Welt integriert, und der Schatten ist das – Hologramm in der Umgebung.

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-whatever-bryou-can-dream-upbr"></a>Ein – Hologramm ist was. <br>Sie können einen Traum<br>
        Als Holographic-Entwickler haben Sie die Möglichkeit, ihre Kreativität aus 2D-Bildschirmen heraus und auf der ganzen Welt zu unterbrechen.<br><br>
        Was wird *erstellt* ?
    :::column-end:::
        :::column:::
        ![Speicher](images/spacer-20x582.png)<br>
       ![Holographic imaginärer Welt im Wohnraum](images/designoverview.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="see-also"></a>Weitere Informationen:
* [Erweitern Sie den Entwurfsprozess](case-study-expanding-the-design-process-for-mixed-reality.md)
* [Raumklang](spatial-sound.md)
* [Farbe, Licht und Materialien](color,-light-and-materials.md)
