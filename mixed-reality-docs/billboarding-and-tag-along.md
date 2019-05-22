---
title: Billboarding und tag-along
description: Objekte mit billboarding orientieren immer selbst, um die Benutzer auftreten.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality billboarding, tag-along
ms.openlocfilehash: e33ab0121398742b2e48553c9cbf2c1debdc6abf
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974789"
---
# <a name="billboarding-and-tag-along"></a>Billboarding und tag-along

Billboarding ist ein Verhalten Konzept, das in mixed Reality auf Objekte angewendet werden kann. Objekte mit billboarding orientieren immer selbst, um die Benutzer auftreten. Dies ist besonders hilfreich, mit dem Text, und Menüs-Systeme, die Platzierung von statische Objekten in der Umgebung des Benutzers (www-locked) wäre andernfalls, verdeckt oder unlesbar, wenn ein Benutzer verschieben.

![HoloLens Perspektive ein Menüsystem zeigt, die immer den Benutzer.](images/billboarding-fragments.gif)<br>
*HoloLens Perspektive ein Menüsystem zeigt, die immer den Benutzer.*

Objekte mit billboarding aktiviert, können in der Umgebung des Benutzers frei drehen. Sie können auch auf eine einzelne Achse je nach Überlegungen zum Entwurf der eingeschränkt werden. Denken Sie daran, billboarded Objekte möglicherweise beschneiden oder verdeckt selbst, wenn sie zu platziert werden in der Nähe anderer Objekte oder HoloLens, zu schließen, überprüft Sie Flächen. Denken Sie dieses Problem vermeiden, die der gesamte Speicherbedarf, dass ein Objekt erzeugen kann, wenn auf der Achse für billboarding aktiviert gedreht.

## <a name="what-is-a-tag-along"></a>Was ist eine Tag-along?

Tag-Along ist ein Verhalten Konzept, das die Hologramme, z. B. billboarded Objekte hinzugefügt werden kann. Diese Interaktion ist eine natürliche und benutzerfreundliche-Methode erzielen Sie die Auswirkungen der Head-locked Inhalt. Ein Objekt Tag-along versucht, die die Ansicht des Benutzers nie verlassen. Dadurch kann der Benutzer kostenlos mit zu interagieren, was Anfang sie während der Hologramme außerhalb ihrer direkten Ansicht auch noch zu sehen ist.

![Der HoloLens-Pins-Bereich ist ein gutes Beispiel Tag-along Verhalten](images/tagalong-1000px.jpg)<br>
*HoloLens Startmenü ist ein gutes Beispiel Tag-along-Verhalten*

Tag-Along Objekte haben die Parameter, die die Möglichkeit zu Verhalten, das optimieren können. Inhalt kann innerhalb oder außerhalb des Benutzers Zugriff wie gewünscht sein, während der Benutzer in ihrer Umgebung bewegt. Während der Benutzer wechselt, wird der Inhalt innerhalb des Benutzers Peripherie-zu bleiben, indem er auf den Rand der Ansicht mit versucht, je nach ein Benutzers wie schnell verschiebt den Inhalt vorübergehend aus der Ansicht lassen kann. Wenn der Benutzer auf das Objekt Tag-along gazes, erfolgt genauer an. Stellen Sie Inhalt wird immer "sofort einen Blick" aus, damit Benutzer welche Richtung vergessen Sie nie ihren Inhalt wird.

Zusätzliche Parameter möglich das Tag-along-Objekt, das an des Benutzers Head durch eine Gummiband angefügt werden können. Erhalten Dämpfung Beschleunigung oder Verlangsamung Gewichtung auf das Objekt, das somit mehr physisch anwesend fühlen. Dieses Verhalten Spring ist eine Unterstützung, die hilft dem Benutzer, die eine genaue Begriffsverständnis Tag-along Funktionsweise zu erstellen. Audio bietet zusätzliche visueller Hinweise für, wenn Benutzer Objekte im Tag-along-Modus. Audio, sollte die Geschwindigkeit der datenverschiebung verstärken; ein schnelles Head Turn sollte einen deutlichen Soundeffekt bereitstellen, während Schritt für Schritt eine natürliche Geschwindigkeit minimale ggf. Audioeffekte überhaupt haben sollten.

Genau wie der Inhalt wirklich von Head gesperrt können sich Tag-along Objekte überfordern oder nauseating, wenn sie völlig verschieben oder zu viel in die Ansicht des Benutzers spring erweisen. Wenn ein Benutzer sich sieht, und klicken Sie dann schnell beenden, ihren Verstand erkennen sie, dass es sich bei der sie aufgehört haben. Nach Saldo informiert sie, dass ihrem Kopf sowohl aktiviert als auch ihre Vision erkennt der ganzen Welt beenden aktivieren beendet wurde. Jedoch wenn Tag-along auf Verschieben verfolgt, wenn der Benutzer beendet wurde, können sie ihren Verstand verwechselt werden.

## <a name="see-also"></a>Siehe auch
* [Cursor](cursors.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Komfort](comfort.md)
