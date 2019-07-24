---
title: Fakboardingvorgang und Tag-entlang
description: Objekte mit einem Abrechnungs-Board orientieren sich stets an dem Benutzer.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, fakboardingvorgang, tagparallel
ms.openlocfilehash: e33ab0121398742b2e48553c9cbf2c1debdc6abf
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974789"
---
# <a name="billboarding-and-tag-along"></a>Fakboardingvorgang und Tag-entlang

Bei der Abrechnung handelt es sich um ein Verhaltens Konzept, das auf Objekte in gemischter Realität angewendet werden kann. Objekte mit einem Abrechnungs-Board orientieren sich stets an dem Benutzer. Dies ist insbesondere bei Text-und menuingsystemen hilfreich, bei denen statische Objekte, die in der Umgebung des Benutzers (der Welt gesperrt) platziert werden, andernfalls verdeckt oder unlesbar sind, wenn ein Benutzer sich bewegen würde.

![Hololens-Perspektive eines Menüsystems, das immer dem Benutzer zusteht](images/billboarding-fragments.gif)<br>
*Hololens-Perspektive eines Menüsystems, das immer dem Benutzer zusteht*

Objekte mit aktiviertem fakboardingvorgang können in der Benutzerumgebung frei rotiert werden. Sie können je nach Entwurfs Überlegungen auch auf eine einzelne Achse beschränkt werden. Beachten Sie, dass abgelegte Objekte möglicherweise ein-oder ausgeblendet werden, wenn Sie sich zu nahe an anderen Objekten befinden oder in hololens zu schließen. Um dies zu vermeiden, stellen Sie sich den Gesamt Speicherbedarf vor, der von einem Objekt erzeugt wird, wenn es auf der Achse gedreht wird, die für das

## <a name="what-is-a-tag-along"></a>Was ist ein Tag?

Tagparallel ist ein Verhaltens Konzept, das holograms hinzugefügt werden kann, einschließlich der Abrechnungen von Objekten. Diese Interaktion ist ein natürlicheres und freundlicheres Verfahren, um die Auswirkungen von Kopf gesperrten Inhalten zu erzielen. Ein Tag-entlang-Objekt versucht, die Ansicht des Benutzers niemals zu verlassen. Dadurch kann der Benutzer frei mit den vorgelagerten Aktionen interagieren, während die Hologramme außerhalb der direkten Ansicht angezeigt werden.

![Das hololens-Pins-Panel ist ein gutes Beispiel dafür, wie sich das Tag-entlang verhält.](images/tagalong-1000px.jpg)<br>
*Das hololens-Startmenü ist ein gutes Beispiel für das tagparallel Verhalten.*

Tagbasierte Objekte verfügen über Parameter, die die Art und Weise, wie Sie sich Verhalten, optimieren können. Der Inhalt kann von der Sicht des Benutzers wie gewünscht in die oder aus der Sicht des Benutzers gesetzt werden, während der Benutzer die Umgebung verlässt. Wenn der Benutzer sich bewegt, versucht der Inhalt, in der Peripherie des Benutzers zu bleiben, indem er an den Rand der Ansicht bewegt wird, je nachdem, wie schnell der Inhalt durch einen Benutzer verschoben wird, kann der Inhalt vorübergehend nicht mehr angezeigt werden. Wenn der Benutzer in Richtung des tagbasierten Objekts zeigt, wird es vollständig in die Ansicht integriert. Stellen Sie sich vor, dass Inhalte immer "auf einen Blick entfernt" werden, damit Benutzer niemals vergessen, welche Richtung ihr Inhalt hat.

Zusätzliche Parameter können dazu führen, dass das Tag-an-Objekt von einem Gummi Band an den Kopf des Benutzers angefügt wird. Durch die Beschleunigung oder Verlangsamung der Dämpfung wird das-Objekt gewichtet, sodass es physisch vorhanden ist. Dieses Spring Verhalten ist ein kostengünstiger, mit dem der Benutzer ein genaues mentales Modell zur Funktionsweise von Tag-Along erstellen kann. Mithilfe von Audiodaten können zusätzliche Kosten bereitgestellt werden, wenn Benutzer Objekte im tagbasierten Modus haben. Audiogeschwindigkeit sollte die Geschwindigkeit der Bewegung verstärken. eine schnelle Kopfzeile sollte einen merklicheren Soundeffekt bereitstellen, während Sie mit einer natürlichen Geschwindigkeit nur minimale Audioergebnisse aufweisen sollten.

Ebenso wie wirklich mit dem Titel gesperrter Inhalt können sich taggingobjekte als überwältigend oder übersichtlich erweisen, wenn Sie in der Ansicht des Benutzers sehr stark verschoben werden. Wenn ein Benutzer die Suche durchsucht und dann schnell anhält, werden Sie von Ihren Sinnen informiert, dass Sie angehalten wurden. Ihr Saldo informiert Sie darüber, dass ihre Kopfzeile angehalten wurde, und ihre Vision sieht, dass die Welt beendet wird. Wenn das Tag-Along jedoch weiterhin verschoben wird, wenn der Benutzer angehalten wurde, kann es seine Sinne verwirren.

## <a name="see-also"></a>Siehe auch
* [Cursor](cursors.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Komfort](comfort.md)
