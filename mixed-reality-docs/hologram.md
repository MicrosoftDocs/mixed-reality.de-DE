---
title: Was ist ggf. ein Hologramm?
description: HoloLens können, die Sie anzeigen und interagieren mit der dreidimensionale Hologramme, Objekte, die aus Licht, und sound, die in der ganzen Welt, um Sie angezeigt.
author: beaufolsom
ms.author: befolsom
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, Hologramme, Entwurf, Interaktion
ms.openlocfilehash: 5a6cc4df764b1f92f6bea2d7d6e6effe2164e4d6
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593360"
---
# <a name="what-is-a-hologram"></a>Was ist ggf. ein Hologramm?

HoloLens ermöglicht das Erstellen **Hologramme**, Objekte des Lichts vorgenommen und sound, die angezeigt werden in die Welt um, die Sie gerade als handele es sich um echte Objekte. Hologramme Antworten auf Ihre [bestaunen](gaze.md), [Gesten](gestures.md) und [Sprachbefehle](voice-input.md), und damit interagieren können [realen Flächen](spatial-mapping.md) für Sie. Mit Hologramme können Sie digitale Objekte erstellen, die Teil der Welt sind.

<br>

>[!VIDEO https://www.youtube.com/embed/MVXH5V8MVQo]

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Feature</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1. Generation)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td> Hologramme</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

## <a name="a-hologram-is-made-of-light-and-sound"></a>Ggf. ein Hologramm erfolgt von Licht und sound

Die Hologramme, HoloLens [rendert](rendering.md) werden in der holografischen Rahmen direkt vor den Augen des Benutzers angezeigt. Hologramme hinzufügen Licht in Ihre Umgebung, was bedeutet, dass Sie sowohl das Licht aus der Anzeige und das Licht aus Ihrer Umgebung finden Sie unter. HoloLens, nicht das Licht aus den Augen entfernt, damit Hologramme durch die Farbe Schwarz gerendert werden können. Stattdessen wird eine schwarze Inhalt als transparent.

Hologramme können viele unterschiedliche Darstellungen und Verhaltensweisen aufweisen. Einige sind realistischer und solid und andere sind cartoonhaften und ethereal. Hologramme können Funktionen in Ihre Umgebung markieren, und sie können Elemente in Ihrer app-Benutzeroberfläche sein.

![Holographic Hund, die auf dem Boden durchlaufen](images/fang3-640px.jpg)

Hologramme lassen sich auch [Sounds](spatial-sound.md), die erscheint, die von einer bestimmten Position in Ihrer Umgebung kommen. Für HoloLens, klingt stammen aus zwei Referenten, die direkt über Ihre Ohren, ohne sie zu gespeichert sind. Ähnlich wie die zeigt, die Lautsprecher sind additiv, Einführung in neue Sounds ohne Blockierung die Sounds aus Ihrer Umgebung.

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>Ggf. ein Hologramm kann in der ganzen Welt oder Tag zusammen mit der Sie eingefügt werden

Wenn Sie einem bestimmten Standort haben, Sie ggf. ein Hologramm möchten, können Sie [platzieren](coordinate-systems.md) anschließend genau in der ganzen Welt. Wie Sie auf diese – Hologramm durchlaufen, wird es stabilen, Bezug auf der ganzen Welt, um Sie herum angezeigt. Bei Verwendung einer [räumliche Anker](coordinate-systems.md#spatial-anchors) um dieses Objekt ordnungsgemäß auf der ganzen Welt anzuheften, das System kann noch erinnern, wo Sie sie angehalten, wenn Sie später zurückkehren.

![Holographic erstellen Maquette auf eine Tabelle](images/image5-640px.png)

Einige Hologramme folgen Sie dem Benutzer stattdessen. Diese Tag-along Hologramme positionieren selbst relativ zu dem Benutzer, unabhängig davon, wo sie führen. Sie können auch auswählen, ggf. ein Hologramm, mit der Sie eine Weile und legen Sie es an der Wand Nachdem Sie auf einem anderen Raum erhalten.

**Empfohlene Methoden**
* Einige Szenarien möglicherweise gefordert wird, dass Hologramme leicht auffindbar oder über die Umgebung sichtbar bleiben. Es gibt zwei allgemeine Ansätze für diese Art der Positionierung. Wir nennen diese **"Anzeige gesperrt"** und **"Text-gesperrt"**.
   * Inhalt Anzeige gesperrt ist Objektmethode für die Anzeige des Geräts "gesperrt". Dies ist schwierig, eine Reihe von Gründen, einschließlich einer unnatürlichen Gefühl der "Clingyness", die viele Benutzer frustriert macht und möchten "er umzusteigen." Im Allgemeinen haben viele Designer es besser, Inhalte anzeigen-Sperren zu vermeiden gefunden.
   * Der Text-locked-Ansatz ist weitaus forgivable. Text-Sperren ist ggf. ein Hologramm des Benutzers Text oder Blicke Vektor angeschlossen ist, aber es befindet sich im 3D-Raum rund um den Benutzer. Viele Erfahrungen haben ein Text mit gesperrten Verhalten übernommen, in denen die Hologramm "die Benutzer-Blicke, wodurch den Benutzer zum Drehen von Hauptteil verwenden, und durchlaufen Sie Speicherplatz ohne Verlust der – Hologramm folgt". Integrieren eine Verzögerung können das – Hologramm verschieben, können Sie natürliche. Einige wichtige UI des Betriebssystems Windows Holographic verwendet z. B. eine Variante, auf die Text-Sperre, die Blicke des Benutzers, mit einer Verzögerung umfassend, elastisches folgt, während der Benutzer ihren Köpfen aktiviert.
* Platzieren Sie den – Hologramm an eine vertraut die Entfernung in der Regel ca. 1 bis 2 Meter Weg von der Spitze.
* Geben Sie einen Anteil der Abweichung für Elemente, die müssen ständig in der holografischen Frame oder sollten Sie Ihre Inhalte auf einer Seite der Anzeige animieren, wenn der Benutzer, die der Sicht ändert.

**Platzieren Sie Hologramme in der optimalen Zone - 1,25 m bis 5 Min.**

Zwei Verbrauchseinheiten ist optimal, und die Benutzeroberfläche wird kommt, desto näher kommen Sie ein Messgerät beeinträchtigt. Zu Abstände umso als ein Messgerät sind Hologramme, die regelmäßig im Detail verschieben eher als feststehend Hologramme problematisch sein. Betrachten Sie ordnungsgemäß Abschneiden oder Ihr Inhalt eingeblendet, wenn es zu schließen, damit nicht den Benutzer in eine unerwartete Erfahrung jar erhält.

![Optimale Abstand zur Platzierung von Hologramme des Benutzers.](images/distanceguiderendering-640px.png)

## <a name="a-hologram-interacts-with-you-and-your-world"></a>Ggf. ein Hologramm interagiert mit Ihnen und Ihren world

Hologramme werden nicht nur über Licht und Sound. Sie können außerdem einen aktiven Teil des Ihre Welt. Blicke – Hologramm und Geste mit der Hand, und befolgen Sie ggf. ein Hologramm starten kann. Geben einen Sprachbefehl, ggf. ein Hologramm und sie können Antworten.

![Holographic Motorcycle-Entwurf, die auf einem echten Motorcycle Text eingefügt](images/image8-640px.png)

Hologramme können persönliche Interaktionen, die nicht an anderer Stelle möglich ist. Da die HoloLens weiß, wo es in der Welt ist, sehen ein holographic Zeichen Sie direkt in den Augen, wie Sie im Raum geführt.

Ggf. ein Hologramm kann auch mit Ihrer Umgebung interagieren. Beispielsweise können Sie einen holographic hüpfenden Ball oberhalb der Tabelle platzieren. Klicken Sie dann mit einem [tippbewegung](gestures.md#air-tap), sehen Sie sich den Ball springt, und stellen sound, wenn er in der Tabelle erreicht.

Hologramme können auch von realen Objekten okkludierte sein. Ein holographic Zeichen durchlaufen beispielsweise über eine Tür und hinter einer Wand, Ihnen verborgen.

**Tipps für die Integration von Hologramme und der realen Welt**
* Ausrichten von Schwerpunkte Regeln macht Hologramme, leichter verständlich und mehr glaubwürdig. Beispiel: Ein holographic Hund auf dem Boden und eine Vase, für die Tabelle zu platzieren, statt Sie Gleitkommazahl im Bereich.
* Viele Designer gefunden, dass sie sogar noch believably Hologramme integrieren können, erstellen Sie einen 'negativen Schatten"auf der Oberfläche, die die Hologramm befindet. Dazu erstellen einen vorläufigen Schein auf den Boden rund um die Hologramm und den "Schatten" aus der Leuchteffekt subtrahiert wird. Der weiche Leuchteffekt integriert das Licht aus der realen Welt, und der Schatten nicht wegen der Hologramm in der Umgebung.

## <a name="a-hologram-is-whatever-you-dream-up"></a>Ist ggf. ein Hologramm, was auch immer Sie umsetzen

Als Entwickler holographic müssen Sie die Möglichkeit, die aus 2D-Bildschirme und in die Welt um Sie Ihrer Kreativität freien Lauf zu unterbrechen. Welche *Sie* erstellen?

![Holographic imaginären Welt im Wohnzimmer](images/designoverview.jpg)

## <a name="see-also"></a>Siehe auch
* [Räumliche sound](spatial-sound.md)
* [Farbe, helle und Materialien](color,-light-and-materials.md)
