---
title: Fallstudie-3 holostudio UI und Interaktionen Design Erkenntnisse
description: Entwicklungs-und Interaktions Entwurfs Lernelemente von holostudio
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: Hololens, holostudio, gemischte Windows-Realität
ms.openlocfilehash: e01e2ea888398e9982b56fd95f90ef0731ec6bc2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974830"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a>Fallstudie-3 holostudio UI und Interaktionen Design Erkenntnisse

[Holostudio](https://www.youtube.com/watch?v=BRIJG0x_We8) war eine der ersten Microsoft-Apps für hololens. Aus diesem Grund mussten wir neue bewährte Methoden für die 3D-Benutzeroberfläche und den Interaktions Entwurf erstellen. Wir haben dies durch eine Vielzahl von Benutzer Tests, Prototypen und Test-und Fehler Tests durchgeführt.

Wir wissen, dass nicht jeder Benutzer über die zur Verfügung stehenden Ressourcen verfügt, um diese Art von Untersuchungen durchzuführen. daher hatten wir unseren SR. Holographic Designer, Marcus Ghaly, drei Dinge, die wir bei der Entwicklung von holostudio kennengelernt haben, über UI-und Interaktions Entwürfe für hololens-apps.

## <a name="watch-the-video"></a>Video ansehen

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a>Problem #1: Personen wollten sich nicht um ihre Schöpfungen bewegen.

Wir haben die Workbench ursprünglich in holostudio als Rechteck entworfen, ähnlich wie Sie es in der realen Welt finden. Das Problem besteht darin, dass die Benutzer über die Lebensdauer einer Erfahrung verfügen, die Sie darüber informiert, dass Sie immer noch unterwegs sind, wenn Sie sich an einem Computer befinden oder vor einem Computer arbeiten, sodass Sie nicht in der Workbench unterwegs waren und Ihre 3D-Erstellung auf allen Seiten untersucht.

![Der rechteckige Entwurf der Workbench in holostudio hat Benutzern den Umstieg auf die Entwicklung von allen Seiten durchgeführt.](images/rectangular-workbench-500px.jpg)

Wir hatten die Einblicke, um die Workbench zu runden, sodass es keine "Front"-oder Clear-Position gab, die Sie positionieren sollten. Als wir dies getestet haben, begannen plötzlich Benutzer, ihre eigenen Schöpfungen zu erkunden.

![Der zirkuläre Workbench-Entwurf hat die Benutzer dazu ermutigt, sich ganz auf ihre Schöpfungen zu bewegen.](images/circular-workbench-500px.jpg)

**Was wir gelernt haben**

Denken Sie immer daran, was für den Benutzer von Bedeutung ist. Der physische Speicherplatz zu nutzen, ist ein interessantes Feature von hololens und etwas, das Sie mit anderen Geräten nicht erledigen können.

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a>Problem #2: Modale Dialoge sind manchmal aus dem Holographic-Frame heraus.

Manchmal kann der Benutzer in einer anderen Richtung als etwas sehen, das seine Aufmerksamkeit in Ihrer APP benötigt. Auf einem PC können Sie einfach ein Dialogfeld einklappen, aber wenn Sie dies in einer 3D-Umgebung auf einem anderen Element tun, kann es so aussehen, als ob das Dialogfeld in den Weg kommt. Sie benötigen Sie, um die Nachricht zu lesen, aber Ihr Instinkt besteht darin, die Nachricht zu erhalten. Diese Reaktion ist großartig, wenn Sie ein Spiel spielen, aber in einem Tool, das für die Arbeit entwickelt wurde, ist es weniger als ideal.

Nachdem wir einige unterschiedliche Dinge ausprobiert haben, haben wir uns schließlich mit der Verwendung eines "gedankenblasen"-Systems für unsere Dialoge und der hinzugefügten tendrils befasst, die Benutzer nachvollziehen können, wo Ihre Aufmerksamkeit in unserer Anwendung benötigt wird. Wir haben auch den "tendrils"-Impuls erstellt, der einen Sinn der Direktionalität impliziert, damit die Benutzer wissen, wo Sie unterwegs sind.

![Das System "Thought Blase" enthielt pulsierender-tendrils, das eine Vorstellung von Richtung bot, sodass Benutzer in der APP an der Stelle waren, an der Ihre Aufmerksamkeit notwendig war.](images/thought-bubble-500px.jpg)

**Was wir gelernt haben**

Es ist in 3D viel schwieriger, Benutzer an Dinge zu warnen, auf die Sie achten müssen. Mithilfe von Aufmerksamkeits Leitern, wie z. b. [räumlichem Sound](spatial-sound.md), Lichtstrahlen oder gedankenblasen, können Benutzer dazu führen, wo Sie sich befinden müssen.

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a>Problem #3: Manchmal kann die Benutzeroberfläche durch andere Hologramme blockiert werden.

Es gibt Zeiten, in denen ein Benutzer mit einem – Hologramm und den zugehörigen UI-Steuerelementen interagieren möchte, die jedoch nicht in der Ansicht angezeigt werden, da ein anderes – Hologramm vorhanden ist. Während der Entwicklung von holostudio haben wir Test-und Fehlerinformationen verwendet, um zu einer Lösung zu gelangen.

![Ein UI-Steuerelement, das einem – Hologramm zugeordnet ist, kann blockiert werden, wenn zwischen dem Benutzer und dem Benutzer hololens ein anderes – Hologramm vorhanden ist.](images/ui-blocked-500px.jpg)

Wir haben versucht, das UI-Steuerelement näher an den Benutzer zu verschieben, sodass es nicht blockiert werden konnte, aber es war nicht gut, dass der Benutzer sich ein Steuerelement ansehen konnte, das sich in Ihrer Nähe befand, gleichzeitig ein – Hologramm, das weit entfernt war. Wenn wir jedoch das Steuerelement vor dem nächstgelegenen – Hologramm an den Benutzer verschoben haben, haben Sie das Gefühl, dass es von dem – Hologramm getrennt wurde, das beeinträchtigt werden sollte.

Schließlich haben wir das UI-Steuerelement in die gleiche Entfernung versetzt wie das – Hologramm, dem es zugeordnet ist, sodass beide miteinander verbunden sind. Dies ermöglicht es dem Benutzer, mit dem Steuerelement zu interagieren, auch wenn es verdeckt ist.

![Die Lösung: Wir haben das UI-Steuerelement gehosttet, das sowohl eine Interaktion mit dem Steuerelement ermöglichte als auch eine Verbindung mit dem – Hologramm hergestellt hat, das es beeinflusst hat.](images/ghosting-ui-500px.jpg)

**Was wir gelernt haben**

Benutzer müssen problemlos auf UI-Steuerelemente zugreifen können, selbst wenn Sie blockiert wurden. Daher sollten Sie Methoden ermitteln, um sicherzustellen, dass Benutzer ihre Aufgaben unabhängig davon, wo sich Ihre Hologramme in der realen Welt befinden, ausführen können.

## <a name="about-the-author"></a>Informationen zum Autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><b>Marcus Ghaly</b><br>SR. Holographic-Designer@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Siehe auch
* [Instinktive Interaktionen](interaction-fundamentals.md)

 
