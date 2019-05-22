---
title: 'Fallstudie: 3 HoloStudio Benutzeroberfläche sowie die Interaktion entwerfen Erkenntnisse'
description: Entwerfen von HoloStudio UI und Interaktion Erkenntnisse
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, HoloStudio, Windows Mixed Reality
ms.openlocfilehash: e01e2ea888398e9982b56fd95f90ef0731ec6bc2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974830"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a>Fallstudie: 3 HoloStudio Benutzeroberfläche sowie die Interaktion entwerfen Erkenntnisse

[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) wurde eine der ersten Microsoft-apps für HoloLens. Aus diesem Grund mussten wir erstellen neue bewährte Methoden für 3D Benutzeroberfläche und entwerfen. Wir haben dies über viele Benutzer zu testen, Erstellen von Prototypen und Versuch und Irrtum.

Wir wissen, dass nicht jeder verfügt über die Ressourcen zur Verfügung, die diese Art der Untersuchungen durchführen, sodass wir unsere Sr. Holographic Designer Marcus Ghaly, drei Dinge freigeben haben wir gelernt, während der Entwicklung von HoloStudio zum Design von Benutzeroberfläche und Interaktion für apps für HoloLens.

## <a name="watch-the-video"></a>Video ansehen

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a>Problem #1: Benutzer möchten nicht auf ihre schöpfungen bewegen

Wir ursprünglich entworfen die Workbench im HoloStudio als eines Rechtecks, der viel wie finden Sie in der Praxis würde. Das Problem ist, dass Personen Erfahrungen, die informiert bleiben weiterhin zur Verfügung, wenn sie an einem Tisch sitzen oder vor einem Computer arbeiten, damit sie verschieben, um die Workbench waren nicht und untersuchen deren 3D Erstellung von allen Seiten.

![Der rechteckige Entwurf der Workbench in HoloStudio dissuaded Benutzer verschieben und die Erstellung von allen Seiten angezeigt.](images/rectangular-workbench-500px.jpg)

Wir hatten die Erkenntnis, zu der Workbench zu runden, sodass gab es keine "Front", oder deaktivieren Sie vorhanden, die Sie bereitstellen. Wenn wir dies getestet, gestartet plötzlich Personen, verschieben, und untersuchen ihre schöpfungen selbst.

![Zirkuläre Workbench Entwurf ermutigt Benutzer, um deren Erstellung zu durchlaufen.](images/circular-workbench-500px.jpg)

**Was wir gelernt haben**

Immer, nachzudenken, was für den Benutzer vertraut ist. Der physische Speicherplatz zu nutzen, ist ein interessantes Feature der HoloLens und etwas, das mit anderen Geräten nicht möglich.

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a>Problem #2: Modale Dialogfelder sind manchmal aus dem holographic Rahmen

In einigen Fällen kann der Benutzer in eine andere Richtung von einem Element suchen, die ihre Aufmerksamkeit in Ihrer app benötigt. Auf einem PC Sie können ein Dialogfeld nur Popupfenster einrichten, aber wenn Sie in ein Gesicht in einer Umgebung mit 3D dazu können auch wie im Dialogfeld auf ihre Weise erhält. Sie benötigen diese für die Nachricht zu lesen, aber ihre instinkthafte Verhalten besteht darin, davon zu erhalten. Diese Reaktion eignet sich hervorragend, wenn sind Sie ein Spiel, aber in ein Tool für die Arbeit, andere als ideal ist.

Nach dem Testen verschiedene Funktionen, wir schließlich ausgeglichen zur Verwendung von einem System "dachte Blase" für unsere Dialogfelder und Tendrils, die Benutzer an, wo ihre Aufmerksamkeit, in der Anwendung erforderlich ist hinzugefügt. Wir haben auch den Puls Tendrils, der einen Überblick über die direktionalität impliziert, damit Benutzer wissen, an welcher Stelle wechseln.

![Das System "Betrachtet Blase" enthalten pulsierender Tendrils, die einen Überblick über die Richtung, führt der Benutzer, in dem ihre Aufmerksamkeit benötigt wurde, in der app bereitgestellt.](images/thought-bubble-500px.jpg)

**Was wir gelernt haben**

Es ist viel schwieriger in 3D um Benutzer auf Dinge, denen sie beachten müssen. Mithilfe von Aufmerksamkeit Directors wie [räumliche Sound](spatial-sound.md)light Strahlung oder Überlegungen ausgelöst wird, kann zu führen, Benutzer erforderlich sein.

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a>Problem #3: Manchmal kann Benutzeroberfläche von anderen Hologramme blockiert werden

Es gibt Situationen, wenn ein Benutzer möchte, für die Interaktion mit ggf. ein Hologramm und die zugeordnete UI-Steuerelemente, werden jedoch blockiert, aus der Ansicht, da eine andere – Hologramm vorangestellt ist. Während wir HoloStudio entwickelten, verwendet haben wir Versuch und Irrtum ist auf eine Lösung für dieses.

![Ein UI-Steuerelement zugeordnete ggf. ein Hologramm kann blockiert werden, wenn eine andere – Hologramm zwischen ihnen und dem Benutzer steht, geteert HoloLens vorhanden ist.](images/ui-blocked-500px.jpg)

Wir haben versucht, das UI-Steuerelement näher an den Benutzer verschieben, es konnte nicht erhalten blockiert jedoch festgestellt, dass es war nicht vertraut, damit der Benutzer auf ein Steuerelement zu suchen, die beim Nähe Sie gleichzeitig Blick auf ggf. ein Hologramm, die weit entfernt wurde. Wenn Sie allerdings wir dem Benutzer das Steuerelement vor der nächsten – Hologramm verschoben, glaubten sie, wie sie aus der Hologramm getrennt wurde, die es beeinträchtigt werden soll.

Wir schließlich letztendlich ghosting von UI-Steuerelement, und legen Sie sie die gleiche Distanz vom Benutzer als Hologramm, die es verknüpft ist, damit beide verbundenen. Dadurch kann der Benutzer mit dem Steuerelement interagieren, auch wenn es verborgen wurde, ist.

![Die Lösung: wir verwaist. das UI-Steuerelement, die Interaktion mit dem Steuerelement zulässig und machte es die Verbindung mit dem – Hologramm können sie beeinträchtigt wurde.](images/ghosting-ui-500px.jpg)

**Was wir gelernt haben**

Benutzer müssen können problemlos Benutzeroberflächen-Steuerelemente zugreifen, selbst wenn sie blockiert haben, sodass Methoden, um sicherzustellen, dass Benutzer ihre Aufgaben unabhängig davon, wo ihre Hologramme in der Praxis sind abschließen können Sie herausfinden.

## <a name="about-the-author"></a>Der Autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><b>Marcus Ghaly</b><br>SR. Holographic-Designer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Siehe auch
* [Instinktive Interaktionen](interaction-fundamentals.md)

 
