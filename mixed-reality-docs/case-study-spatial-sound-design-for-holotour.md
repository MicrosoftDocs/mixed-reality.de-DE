---
title: 'Fallstudie: räumliche Entwurf für HoloTour'
description: Um eine wirklich faszinierende 3D virtuelle Tour für Microsoft HoloLens erstellen zu können, sind als Panorama-Videos und holographic Landschaften nur einen Teil der Formel.
author: JSyltebo
ms.author: jsylte
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, HoloTour, räumliche sound, Groß-/Kleinschreibung-Studie
ms.openlocfilehash: eca675534dba12dd65a20fb9d85e4df57f725288
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596339"
---
# <a name="case-study---spatial-sound-design-for-holotour"></a>Fallstudie: räumliche Entwurf für HoloTour

Um eine wirklich faszinierende 3D virtuelle Tour für Microsoft HoloLens erstellen zu können, sind als Panorama-Videos und holographic Landschaften nur einen Teil der Formel. Audio-Designer, Jason Syltebo zu wie sound kommuniziert, wurde erfasst und verarbeitet, um müssen Sie sich fühlen, als würden Sie tatsächlich in jedem der Standorte in HoloTour sind.

## <a name="the-tech"></a>Der Technologie

Die ansprechende Bilder und holographic Szenen in HoloTour angezeigten sind nur einen Teil der Erstellung einer glaubwürdig mixed Reality-Erfahrung. Während Hologramme vor einen Benutzer nur visuell angezeigt werden können die [räumliche Sound](spatial-sound.md) Feature von HoloLens kann bietet dem Benutzer eine vollständige draußen audio, um alle Richtungen ausgestrahlt, stammen.

Räumliche Sound kann uns gerne Audiohinweise an eine Richtung, in der der Benutzer zu Rate ziehen sollten, oder den Benutzer wissen, dass es weitere Hologramme, damit sie in seinem Bereich finden Sie unter. Einen Sound auch direkt an ggf. ein Hologramm anfügen Sie können und ständig aktualisiert die Richtung und Entfernung, die die Hologramm von einem Benutzer wird, damit es so scheinen, als ob der Sound direkt aus dem Objekt stammt.

Wir wollten mit HoloTour nutzen den räumlichen solider Funktionen von HoloLens zum Erstellen einer 360-Grad-ambient-Umgebung, synchronisiert mit dem Video, um die sonic Highlights in bestimmte Speicherorte anzuzeigen.

## <a name="behind-the-scenes"></a>Im Hintergrund

Wir haben HoloTour Erfahrungen von zwei verschiedenen Speicherorten erstellt: "ROME" und am Machu Picchu. Um diese Touren können authentischen und überzeugende machen möchten wir vermeiden Sie die Verwendung von generischen Sounds und stattdessen erfassen Audio direkt von den Orten, in dem wir Filmen wurden.

### <a name="capturing-the-audio"></a>Das Audio aufzeichnen

In unserem [Fallstudie zum Erfassen des visuellen Inhalts für HoloTour](case-study-capturing-and-creating-content-for-holotour.md), wir den benutzerdefinierten Entwurf entwickeln, der unsere Kamera Rig gesprochen. Es umfasste 14 GoPro Kameras, die in einem Gehäuse 3D gedruckt enthaltenen entwickelt, um die bestimmten Dimensionen von der Stativ. Wenn audioeingaben aus dieser Rig erfassen möchten, haben wir ein Quad-Mikrofon Array unterhalb der Kameras, die in einer Einheit compact 4-Kanal-Aufzeichnung eingelesen werden, die an der Basis der Stativ Sätt.: hinzugefügt. Wir haben uns entschieden, Mikrofone, die nicht nur ausgeführt gut, aber die haben eines sehr geringen Ressourcenbedarf, um die Ansicht der Kamera nicht verdeckt.

![Benutzerdefinierte Kamera und Mikrofon rig](images/camera-rig-microphones-300px.png)<br>
*Benutzerdefinierte Kamera und Mikrofon rig*

Dieses Setup erfasst Sound in unterschiedliche Richtungen aus den genauen Ort der unsere Kamera, gewähren uns genügend Informationen, um ein 3D sehen Panorama mit räumlichen Sound, die wir später noch Mal mit dem 360-Grad-Video synchronisieren könnten neu zu erstellen.

Eine der Herausforderungen bei der Kamera-Array-Audiowiedergabe ist, dass Sie die Geschwindigkeitsvorteile der, was zum Zeitpunkt der Erfassung aufgezeichnet wird. Auch wenn die videoaufzeichnung in Ordnung ist, kann die sound Erfassung problematisch sein, weil-Kamera-Audiokomponenten wie Sirenen, Flugzeugen oder hohe Winde werden. Um sicherzustellen, dass alle Elemente werden musste, die wir benötigen, verwendet haben wir eine Reihe von Stereo und mono mobile Aufzeichnung Einheiten, zum Abrufen von asynchronen, ambient-Elemente an bestimmten Punkten von Interesse an jedem Standort. Diese Erfassung ist wichtig, da es dem sound Designer die Möglichkeit bietet, bereinigen und verwendbar Inhalt zu suchen, die in der nach der Produktion verwendet werden kann, Erstellen von Interesse sind, und weitere direktionalität hinzufügen.

Jeden Tag des angegebenen Capture würde es sich um eine große Anzahl von Dateien generieren. Es war wichtig, ein System zum Nachverfolgen zu entwickeln, welche Dateien an einem bestimmten Ort oder die Kamera-Aufnahme entsprechen. Unsere Aufzeichnung Einheit nach Datum automatisch ein Name Dateien eingerichtet wurde und Take-Nummer, und wir würden sichern diese am Ende des Tages auf externe Laufwerke. Zumindest wurde als verbal Slating Anfang Audioaufnahmen wichtig, da dadurch die einfache kontextbezogene Identifizierung des Inhalts Dateinamen zu einem Problem werden sollte. Es war auch wichtig für uns, die "Camera Capture" Rig visuell Tablets, Video und Audio als separaten Medien erfasst wurden und erforderlich, um während des Post synchronisiert werden.

### <a name="editing-the-audio"></a>Bearbeiten das audio

In der nach der Erfassung Reise Studio werden, dass der erste Schritt beim Erstellen einer sehen direktionalen und immersiven-Benutzeroberfläche sehen sich die audioerfassung für den Speicherort aus, wählen Sie das beste nimmt und identifizieren alle auffällige Glanzlichter, die während der kreativ angewendet werden konnten Integration. Das audiocodierungsformat ist dann bearbeitet und bereinigt. Eine laut Auto Horn dauert eine Sekunde, und wiederholen mehrmals, können z. B. ersetzt und sich Abschnitte der stille, ambient-Audio über die gleiche Erfassung zusammengefügt werden.

Der sound-Designer kann das entsprechende Audio synchronisieren, sobald das video bearbeiten für einen Standort eingerichtet ist. An diesem Punkt haben wir mit "Camera Capture" Rig und mobile erfassen, um zu entscheiden, welche Elemente oder eine Kombination daraus, zum Erstellen einer immersiven audio-Szene funktionieren. Eine Technik, die wir für nützlich befunden bestand darin, ein audio-Editor "und" Build schnell linear mock USV zum Experimentieren mit unterschiedlichen Kombination Ideen alle sound Elemente hinzuzufügen. Wir erhielten dadurch besser formatierte Ideen, wenn es Zeit, die tatsächliche HoloTour Szenen erstellen stammt.

### <a name="assembling-the-scene"></a>Zusammenstellen der Szene

Der erste Schritt beim Erstellen einer 3D-Szene ambient ist die Erstellung einer Bett von allgemeinen ambient Schleife Hintergrundsound, die andere Features und interaktive sound Elemente in einer Szene unterstützt werden. In diesem Fall haben wir einen ganzheitlichen Ansatz für andere Implementierung-Techniken, die durch die spezifischen Anforderungen und Entwurfskriterien bestimmte Szene bestimmt. Einige Szenen möglicherweise auf die Verwendung der synchronisierten kameraerfassung indizieren, während andere erfordern möglicherweise, dass ein weitere geordneter Ansatz, der mehr fallzeile verwendet für die mehr Kino Momente in HoloTour Sounds "," interaktive Elemente "und" Music "und" Soundeffekten platziert.

Beim Indizieren bei der Verwendung der Kamera Capture Audiodaten platziert räumliche Sound-fähigen ambient audio korrekturemitter für den direktionalen Koordinaten der Kamera-Ausrichtung, so an, dass die Nord-Kamera-Ansicht von der North Mikrofon audio wiedergegeben wird, und ebenso für die anderen hauptrichtungen. Dieser Emitter werden World-gesperrt, d. h., die Benutzer kann ihrem Kopf in Bezug auf diese korrekturemitter frei aktivieren und der Sound ändert sich entsprechend effektiv Modellieren des Sounds des Ständigen an diesem Speicherort. Piazza Navona oder die Pantheon Beispiele von Szenen, die eine gute Kamera erfasst Audio Mischung anhören.

Ein anderer Ansatz bei der Wiedergabe einer Schleife Stereo Umgebung zusammen mit räumlichen sound korrekturemitter platziert, in der Szene einmalige Soundwiedergabe, die im Hinblick auf die Lautstärke, Tonhöhe und Trigger Häufigkeit unterbrochen wird. Dadurch wird eine Umgebung mit einer erweiterten Eindruck von direktionalität erstellt. In Aguas Calientes können z. B. Sie hören Sie sich wie jeder Quadranten des der Panorama für bestimmte korrekturemitter verfügt, die absichtlich markieren Sie bestimmte Bereiche des Geography, aber zusammenarbeiten, um eine allgemeine immersive Umgebung zu erstellen.

## <a name="tips-and-tricks"></a>Tipps und tricks

Wenn Sie sind zusammenstellen audio für eine Szene, stehen einige zusätzlichen Methoden Sie weitere direktionalität und Eintauchen, markieren voll ausgelastet sound räumlichen Funktionen von HoloLens können. Wir haben eine Liste mit einigen unten bereitgestellt – diese beim nächsten Versuch HoloTour lauschen.
* **Suchen Sie Ziele**: Hierbei handelt es sich um Sounds aus, die ausgelöst wird, nur wenn Sie einem bestimmten Objekt bzw. einen Bereich des Frames, holographic betrachten. Beispielsweise wird in Richtung der Cafe Street-Seite in der "ROME" Piazza Navona suchen leicht die Klängen einer ausgelasteten Restaurant ausgelöst.
* **Lokale Vision**: Die Reise untersuchen zwar HoloTour enthält bestimmte Beats die Tour, in dem Leitfaden zum Dank der Unterstützung durch Hologramme, ein Thema ausführliche. Z. B. platziert hallenden Audio während der Bereitstellung von der Pantheon auflöst, um die Oculus anzuzeigen, wie ein 3D-Objekt korrekturemitter von innen von der Pantheon den Benutzer zum Durchsuchen des Modells inneren fördert.
* **Erweiterte direktionalität**: In vielen Szenen haben wir Sounds in verschiedene Möglichkeiten, die direktionalität hinzuzufügen. In der Szene Pantheon wurde z. B. der Sound der Jungbrunnen platziert wie eine separate korrekturemitter nah an den Benutzer, damit sie auch einen Eindruck von "sonic Parallax" abgerufen werden konnte, wie sie auf der Play-Speicherplatz durchlaufen. In der Peru Salinas de Maras Szene wurden die einzelnen Perspektive einige kleine Streams als separate korrekturemitter So erstellen Sie eine seine Ambiente-Umgebung, um den Benutzer mit der Authentizität Sounds von diesem Speicherort platziert.
* **Spline-Emitter**: Dieser spezielle räumliche sound Emitter verschiebt in einem 3D-Bereich relativ zu die visuelle Position des Objekts, das es angefügt ist. Ein Beispiel hierfür ist der Zug in am Machu Picchu, in dem wir ein Spline-Emitter verwendet, um gewisser unterschiedliche direktionalität und Bewegung zu geben.
* **Musik und SFX**: Bestimmte Aspekte der HoloTour, die einen Ansatz mehr stilisierten oder Kino darstellen werden – Musik und Sound Effekte verwenden, um die emotionaler Auswirkungen bereitstellen. In der Schlacht Gladiator am Ende der Tour "ROME" wurden Spezialeffekte wie Whooshes oder Stingers verwendet, um die helfen, Stärken Sie die Auswirkungen von Bezeichnungen in Szenen angezeigt werden.

## <a name="about-the-author"></a>Der Autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Jason Syltebo" width="60" height="60" src="images/syltebo.png"></td>
<td style="border-style: none"><b>Jason Syltebo</b><br>Audio-Designer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Siehe auch
* [Räumliche sound](spatial-sound.md)
* [Räumliche Entwurf](spatial-sound-design.md)
* [Räumliche Sound in Unity](spatial-sound-in-unity.md)
* [MR Spatial 220](holograms-220.md)
* [Video: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)

 
