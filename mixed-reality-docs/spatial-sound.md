---
title: Raumklang
description: Durch die Verwendung von räumlichem Sound in einer Mixed Reality-Anwendung können Sie Klänge in einem 3D-Raum überzeugend platzieren.
author: hak0n
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: räumlicher Sound, Umschließungs Sound, 3D--Audio, 3D--Ton, räumliche Audiodaten
ms.openlocfilehash: 31ec8f88a060127daab9bf3afc970457ec7c90a3
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437395"
---
# <a name="spatial-sound"></a>Raumklang

Wenn sich Objekte nicht mehr in der Sicht befinden, ist eine der Methoden, mit denen wir uns beschäftigen können, was wir tun. In Windows Mixed Reality bietet die Audioengine die Audiowiedergabe-Komponente der gemischten Realität, indem 3D-Sound mithilfe von Richtungs-, Entfernungs-und Umgebungs Simulationen simuliert werden. Die Verwendung von räumlichem Sound in einer Anwendung ermöglicht Entwicklern das überzeugend Platzieren von Sounds in einem dreidimensionalen Raum (Kugel), der sich alle um den Benutzer dreht. Diese Sounds erscheinen dann so, als wären Sie von echten physischen Objekten oder den Mixed Reality holograms in der Benutzerumgebung. Da [holograms](hologram.md) Objekte sind, die aus hellen und manchmal klingen, unterstützt die Audiokomponente das Grundlagen von holograms, sodass Sie leichter zu glauben sind und eine immersive Darstellung schaffen.

Obwohl holograms nur visuell angezeigt werden können, wenn der Benutzer den Blick zeigt, kann der Sound Ihrer APP aus allen Richtungen stammen. oberhalb von, hinter, auf der Seite, usw. Mit dieser Funktion können Sie auf ein Objekt aufmerksam machen, das sich derzeit nicht in der Ansicht des Benutzers befindet. Ein Benutzer kann Sounds erkennen, die aus einer Quelle in der gemischten Realität stammen. Wenn der Benutzer z. b. näher an einem Objekt geht oder das Objekt näher an ihn gelangt, wächst das Volume. Ebenso, wenn Objekte sich um einen Benutzer bewegen oder umgekehrt, stellen räumliche Klänge die Illusion dar, dass Sounds direkt aus dem Objekt stammen.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

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
        <td>Raumklang</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (mit Kopfhörern)</td>
    </tr>
</table>

## <a name="simulating-the-perceived-location-and-distance-of-sounds"></a>Simulieren der wahrgenommenen Position und der Entfernung von Sounds

Durch die Analyse, wie Sound sowohl unsere Ohren erreicht, bestimmt unser Gehirn den Abstand und die Richtung des Objekts, das den Sound ausgibt. Ein HRTF (oder Head-Related Transfer Function) simuliert diese Interaktion, indem die spektrale Antwort modelliert wird, die bestimmt, wie ein Ohr den Sound von einem Punkt im Raum empfängt. Die räumliche Audioengine verwendet personalisierte HRTFs, um die gemischte Realität zu erweitern und Klänge zu simulieren, die aus verschiedenen Richtungen und Entfernungen stammen.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Die "Left"-oder "Right Audio"-Cues (Azimuth) stammen aus den Unterschieden in der Zeit, die bei jedem Ohr Die nach-oben-und nach-unten-Hinweise stammen aus den von der äußeren Ohrform (pinnae) erzeugten Spektral Änderungen. Durch die Festlegung, woher die Audiodaten stammen, kann das System die Darstellung der Klänge simulieren, die zu unterschiedlichen Zeiten an den Ohren ankommen. Beachten Sie, dass bei hololens, während die Azimuth-Spatialisierung personalisiert ist, die Simulation der Rechte Erweiterung auf einem durchschnittlichen Satz von Anthropometrie basiert. Daher ist die Genauigkeit der Rechte Erweiterung möglicherweise weniger genau als die Azimuth-Genauigkeit.

Die Merkmale von Sounds ändern sich auch basierend auf der Umgebung, in der Sie vorhanden sind. Beispielsweise bewirkt das Auslösen in einer-Höhle, dass Ihre Stimme von den Wänden, den Flächen und den Obergrenzen abspringt, was einen Echo Effekt erzeugt. Die Raummodell Einstellung räumlicher Sound erzeugt diese Reflektionen, um Klänge in einer bestimmten Audioumgebung zu platzieren. Sie können diese Einstellung verwenden, um den tatsächlichen Speicherort des Benutzers für die Simulation von Sounds in diesem Bereich abzugleichen, um eine immersive Audiodarstellung zu erzielen.

## <a name="integrating-spatial-sound"></a>Integrieren von räumlichem Sound

Da das allgemeine Prinzip der gemischten Realität darin besteht, [Hologramme](hologram.md) in der physischen Welt oder der virtuellen Umgebung des Benutzers zu finden, sollten die meisten Sounds von holograms räumlich verteilt werden. Bei hololens gibt es natürlich Überlegungen zur CPU-und Arbeitsspeicher Planung, aber Sie können hier 10-12 räumliche audiostimmen verwenden, wenn Sie weniger als ungefähr 12% der CPU verwenden (~ 70% der vier Kerne). Empfohlene Verwendung für räumliche Ton Stimmen:
* Betrachtung von Blickwinkeln (Hervorhebung von Objekten, insbesondere, wenn Sie nicht angezeigt werden). Wenn ein – Hologramm ein Eingreifen des Benutzers erfordert, spielen Sie einen Sound für dieses – Hologramm (z. b. eine virtuelle hunderinde). Dadurch kann der Benutzer das – Hologramm finden, wenn es nicht in der Ansicht angezeigt wird.
* Audiohaptik (reaktives Audiomaterial für touchlose Interaktionen). Geben Sie z. b. einen Sound wieder, wenn der Hand-oder Bewegungs Controller des Benutzers den Gesten Rahmen betritt und verlässt. Oder geben Sie einen Sound wieder, wenn der Benutzer ein Hologram auswählt.
* Eintauchen (Ambient-Sounds für den Benutzer).

Es ist auch wichtig zu beachten, dass die Kombination von standardstereo-Sounds mit räumlichem Sound bei der Erstellung realistischer Umgebungen effektiv sein kann. die Stereo Klänge sollten jedoch relativ leise sein, um Platz für die feinen Aspekte räumlicher Töne zu schaffen, wie z. b. Reflexionen ( Entfernungs Hinweise), die in einer lärmenden Umgebung schwer zu hören sein können.

Die räumliche Sound-Engine von Windows unterstützt nur eine 48.000-Stichprobenrate für die Wiedergabe. Die meisten Middleware (z. b. unity) konvertiert Audiodateien automatisch in das unterstützte Format. Wenn Sie jedoch direkt Windows-Audio-APIs verwenden, müssen Sie das Format des Inhalts mit dem vom Effekt unterstützten Format vergleichen.

## <a name="see-also"></a>Weitere Informationen:
* [Räumliche Daten 220](holograms-220.md)
* [Raumklang in Unity](spatial-sound-in-unity.md)
* [Raumklang in DirectX](spatial-sound-in-directx.md)
* [Raumklangentwurf](spatial-sound-design.md)
