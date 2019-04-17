---
title: Raumklang
description: Verwenden von räumlichen Sound in einer mixed Reality-Anwendung, können Sie Sounds in einem 3D-Raum convincingly zu platzieren.
author: hak0n
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: räumliche Sound, Surroundsound, 3d, Audio, 3d sound, räumliche audio
ms.openlocfilehash: ccb236a8b53e757ba632a1c7c6cb2d4f07735910
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594560"
---
# <a name="spatial-sound"></a>Raumklang

Wenn Objekte aus unsere uneingeschränkten Zugriff sind, ist eine der Möglichkeiten, die wir wahrnehmen kann, um uns herum Abläufe auf über Sound. In Windows Mixed Reality bietet das Audiomodul der sehen Anteil der mixed Reality-Erfahrung durch Simulieren von 3D Sound mithilfe von environmental Simulationen, Entfernung und Richtung. Verwenden von räumlichen Sound in einer Anwendung kann Entwickler convincingly Platzieren von Sounds in einem 3 dimensionalen Raum (Kugel) für den Benutzer. Diese Sounds werden dann erscheinen, als ob sie von echten physischen Objekten oder der mixed Reality-Hologramme in der benutzerumgebung gestellt würden. Angesichts der Tatsache, dass [Hologramme](hologram.md) Licht werden Objekte aus, und manchmal Systemsound, der sound Komponente können Sie Ground-Hologramme mehr glaubwürdig zu machen, und erstellen seine Erfahrung wird optimiert.

Obwohl Hologramme nur visuell angezeigt werden können, in denen der Benutzer die Blicke verweist, kann Ihrer app Sound stammen, aus allen Richtungen sind. oben unten, klicken Sie auf der Seite usw. Sie können dieses Feature verwenden, um ein Objekt hervorzuheben, die derzeit in der Ansicht des Benutzers möglicherweise nicht. Ein Benutzer erkennen Sounds aus, die aus einer Quelle in mixed Reality-Welt ausgehen sein. Wenn der Benutzer ruft ein Objekt an oder ruft das Objekt ab, in ihrer Nähe, erhöht z. B. das Volume auf. Auf ähnliche Weise wie die Objekte zu verschieben, um einen Benutzer (oder umgekehrt), geben die räumliche Sounds, den Eindruck, dass Sounds direkt aus dem Objekt stammen.

<br>

>[!VIDEO https://www.youtube.com/embed/PTPvx7mDon4]

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Feature</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1. Generation)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>

<td> Raumklang</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️ (mit Kopfhörer)</td>

</tr>
</table>

## <a name="simulating-the-perceived-location-and-distance-of-sounds"></a>Simulieren die wahrgenommene Speicherort und die Entfernung von Sound

Durch die Analyse wie sound erreicht bestimmt sowohl unser Ohren unseres Gehirns, den Abstand und die Richtung des Objekts den Sound ausgeben. Ein HRTF (oder Head-Related-Funktion) simuliert diese Interaktion, durch die Modellierung der Spektralansprechung, das bestimmt, wie eine Ear Sound von einem Punkt im Raum empfängt. Das räumliche Audiomodul verwendet personalisierte HRTFs, erweitern die mixed Reality-Erfahrung und simulieren von Sounds aus, die von verschiedenen Richtungen und entfernungen stammen.

<br>

>[!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

Nach links oder rechts Audio (Azimut) Hinweise stammen aus Unterschieden in der Zeit, Ton auf jede der Ear eingeht. Nach oben oder unten Hinweise stammen von spektrale Änderungen, die von der äußeren Ear-Form (Pinnae) erzeugt. Durch Festlegen, Audio, stammen kann das System die Erfahrung der Sound zu unterschiedlichen Zeiten eintreffen, um unsere Ohren simuliert werden. Beachten Sie, dass HoloLens, während Azimut Spatialization personalisiert wird, die Simulation der Erhöhung der Rechte auf einer durchschnittlichen Gruppe von Anthropometrics basiert. Daher kann die Erhöhung der Rechte Genauigkeit weniger genau als Azimut Genauigkeit sein.

Die Merkmale des Sounds ändern sich auch auf Grundlage der Umgebung, in der sie vorhanden sind. Beispielsweise bewirkt Shouting in einer Höhle Ihre Stimme zum abprallen, bis die Wände, Etagen und Obergrenzen, erstellen ein Echo. Einstellung des Raums räumliche Sound reproduziert diese Reflexionen um Sounds in einer bestimmten audio-Umgebung zu platzieren. Sie können diese Einstellung verwenden, entsprechend der tatsächlichen Speicherort für die Simulation von Sound im Raum des Benutzers zum Erstellen der audio seine Erfahrung.

## <a name="integrating-spatial-sound"></a>Die Integration von räumlichen sound

Da das allgemeine Prinzip von mixed Reality dazu dient, erden [Hologramme](hologram.md) in der realen Welt oder virtuellen Umgebung des Benutzers, die meisten Tönen Hologramme spatialized werden sollte. Für HoloLens stehen auf natürliche Weise CPU- und Arbeitsspeicherressourcen finanziellen Aspekten, jedoch können Sie bei der Verwendung von weniger als ca. 12 % der CPU (ca. 70 % einer der vier Kerne) 10.-12. räumliche sound stimmen vorhanden. Empfohlene Verwendung für räumliche sound stimmen gehören:
* Bestaunen Mischen von (Objekte, insbesondere wenn nicht aus der Sicht hervorgehoben). Wenn ggf. ein Hologramm, die Aufmerksamkeit eines Benutzers erfordert, auf diese – Hologramm einen Sound wiedergeben (z. B. eine virtuelle Hund Rinde haben). Dadurch wird den Benutzer, die – Hologramm zu suchen, wenn es nicht in der Ansicht.
* Audio Haptics (reaktiven Audio touchless Interaktionen). Beim des Benutzers manuell oder durch Bewegung Controller gibt und die Geste Frame beendet, wird z. B. wiedergeben Sie einen Sound. Oder einen Sound wiedergeben, wenn der Benutzer ggf. ein Hologramm auswählt.
* Immersion (ambient Sounds, um den Benutzer).

Es ist auch wichtig zu beachten, dass die Kombination von standard-Stereo Sounds mit räumlichen Sound kann beim Erstellen von realistischer Umgebungen effektiver sein, die Sounds aus Stereo relativ stillen, um Platz für die feinen Aspekte des räumlichen Sounds, z.B. Reflexionen (sein soll Distance Hinweise), das kann schwierig sein, in einer lauten Umgebung zu erfahren.

Windows räumliche sound-Engine unterstützt nur eine 48 KB Samplingrate für die Wiedergabe. Die meisten Middleware, wie Unity, wird automatisch Audiodateien in das unterstützte Format konvertieren, aber bei der Windows-Audio-APIs direkt verwenden, stimmen Sie das Format des Inhalts in das Format, die von den Effekt unterstützt werden.

## <a name="see-also"></a>Siehe auch
* [MR Spatial 220](holograms-220.md)
* [Räumliche Sound in Unity](spatial-sound-in-unity.md)
* [Räumliche Sound in DirectX](spatial-sound-in-directx.md)
* [Räumliche Entwurf](spatial-sound-design.md)
