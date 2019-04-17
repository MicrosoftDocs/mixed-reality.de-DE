---
title: 'Fallstudie: Verwenden von räumlichen Sound in RoboRaid'
description: Räumliche Sound ist eines der interessantesten Features von Microsoft HoloLens, eine Möglichkeit für Benutzer wahrnehmen, was zu passiert, wenn Objekte aus den uneingeschränkten Zugriff sind bereitgestellt wird.
author: mattzmsft
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, RoboRaid, räumliche sound
ms.openlocfilehash: 4bb050b4a4051c121c488ea38e150a8973bd7c04
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594537"
---
# <a name="case-study---using-spatial-sound-in-roboraid"></a>Fallstudie: Verwenden von räumlichen Sound in RoboRaid

Charles Sinex, audio Lead im Microsoft HoloLens Experience-Team und befasst sich die besonderen Herausforderungen, die beim Erstellen von audio für die er auftreten, dass [RoboRaid](https://www.microsoft.com/en-us/p/roboraid/9nblggh5fv3j), ein mixed Reality Ego-Shooter.

## <a name="the-tech"></a>Der Technologie

[Räumliche Sound](spatial-sound.md) ist eines der interessantesten Features von Microsoft HoloLens, eine Möglichkeit für Benutzer wahrnehmen, was zu passiert, wenn Objekte aus den uneingeschränkten Zugriff sind bereitgestellt wird.

Bei RoboRaid ist der offensichtlichsten und am meisten effektive räumliche Sound auf die Warnung für etwas außerhalb des Benutzers peripheren Vision des Spielers. Z. B. die Breacher kann aus einer der überprüften Wände im Raum eingeben, aber wenn Sie nicht den Speicherort mit Internetzugriff sind, in denen es eingibt, verpassen Sie es möglicherweise. Damit Sie für diese Invasion benachrichtigt werden, erfahren Sie etwas unterschiedlichen Audio aus, in der Breacher eingibt, die Sie informiert, dass Sie schnell reagieren beenden müssen.

## <a name="behind-the-scenes"></a>Im Hintergrund

Das Verfahren zum Erstellen der räumlichen Sound für HoloLens-apps ist, also die neuen und einzigartigen, und das Fehlen der vergangenen Projekten zu Referenzzwecken kann zahlreiche Head würde, wenn Sie ein Problem beim Ausführen führen. Diese Beispiele für das audio Herausforderungen konfrontiert wir hoffentlich zwar die RoboRaid machen Sie Sie für Ihre eigenen apps "audio" erstellen.

### <a name="be-mindful-of-taxing-the-cpu"></a>Achten Sie hohe Anforderungen an die CPU

Räumliche Sound kann auf der CPU relativ anspruchsvoll sein. Für eine ausgelastete Erfahrung wie RoboRaid war es entscheidend, um die Instanzen der räumlichen Sound auf unter 8 zu jedem Zeitpunkt beibehalten. Zum größten Teil, war es so einfach wie das Festlegen von des Grenzwert von Instanzen von anderen Ereignissen, audio, damit alle Instanzen, die auftreten, nachdem der Grenzwert erreicht wurde abgebrochen. Z. B. wenn drohnen erzeugen zu können, sind ihre Screams auf drei Instanzen zu jedem Zeitpunkt. Da Sie nur über vier drohnen auf einmal erstellen können, sind drei Screams ausreichend, da besteht keine Möglichkeit, die Ihr Gehirn, die mitverfolgen kann viele ähnlich klingende audio-Ereignisse. Diese setzte Ressourcen bei anderen räumlichen sound-Ereignisse, wie z. B. gegnerischen Explosionen oder Feinde dafür vorbereiten.

### <a name="rewarding-a-successful-dodge"></a>Eine erfolgreiche abwedeln belohnen

Dodging Mechanikers ist einer der wichtigsten Aspekte von Ihr Gameplay in RoboRaid sowie etwas, das wir sind der Ansicht auf die Benutzeroberfläche für HoloLens rundum einzigartigen wurde. Daher wollten wir erfolgreiche Farben stellen sehr Flexibilität für den Player. Wir haben die Doppler "whizz-von", um überzeugende Recht in einer frühen Phase der Entwicklung. Zunächst mein Plan war eine Schleife verwenden und bearbeiten sie in Echtzeit mit Lautstärke, Tonhöhe und Filter. Die Implementierung für dieses war im Begriff, die sehr kunstvollem sein, damit vor dem Ausführen eines Commits für Ressourcen, um diese tatsächlich zu erstellen wir mithilfe eines Medienobjekts mit günstig Prototyp erstellt die Doppler-Wirkung Dank der minutengenauen nur um herauszufinden, wie es fand *. Unsere talentierter Entwickler war es, damit dieses Medienobjekt whizz durch Wiedergabe würde genau 0,7 Sekunden, bevor das Projektil von der Spieler der Ear übergeben wurden wird, und die Ergebnisse der Ansicht wirklich großartig! Unnötig zu sagen, wir die komplexere Lösung ditched und implementiert den Prototyp.

** (Wenn Sie weitere Informationen zum Erstellen eines Medienobjekts audio mit dem integrierten Doppler-Effekt möchten, sehen Sie sich einen Artikel von sound-Designer namens Charles Deenan [100 Whooshes in 2 Minuten](http://designingsound.org/2010/02/charles-deenen-special-100-whooshes-in-2-minutes/).) *
<br>
![Erfolgreich abwedeln von Feinden Projektil urplötzlich der Spieler ein zufriedenstellendes whizz von Sound.](images/successful-dodge-roboraid-500px.jpg)

### <a name="ditching-ineffective-sounds"></a>Damit Sie nicht versehentlich Sounds eintauschen

Wir hatten ursprünglich Zahl hinter der Spieler sound wiedergegeben, sobald sie haben erfolgreich das gegnerische Projektil Farbkanalwert, aber wir uns entschieden, diese verschiedenen Gründen den ganzen wollten. Zunächst nicht kommt es so effektiv wie die SFX Whizz von Ihnen, die wir für die abwedeln verwendet. Der Zeit, die das Projektil eine Wand hinter Ihnen trifft, würde etwas anderes im Spiel stattgefunden haben, das würde so ziemlich viel Maske, die klingen. Zweitens schon nicht Kollisionen auf dem Boden, damit wir nicht, dass das unkontrollierte anwachsen erhalten konnte, um wiederzugeben, wenn das Projektil den Boden, statt den Wänden erreicht. Und schließlich gab es die CPU-Kosten räumliche Sound. Ihr Feind Elite Scorpion (eine, die innerhalb der Wand durchforsten kann) verfügt über einen speziellen Angriff, der CA. acht Projektile schießen. Nicht nur hat, die in der testmischung ein großer Chaos vorgenommen, es außerdem störenden knacken, da es schwer CPU erreicht wurde.

### <a name="communicating-a-hit"></a>Kommunikation von einer Trefferüberprüfung

Ein interessantes Problem, die, dem wir begegneten, das wir sind der Ansicht eindeutig für die HoloLens-Oberfläche wurde, war die Schwierigkeit effektiv Kommunikation auf die Spieler, dass sie erreicht wurde. Was eine mixed Reality auftreten erfolgreich macht, ist das Gefühl, dass die Story Sie davon betroffen sein wird. Daraus folgt, dass Sie glauben, dass SIE eine Verletzung Fremd Roboter in Ihrem eigenen Wohnzimmer Bekämpfen von mergeproblemen werden müssen.

Spieler wird nicht offensichtlich alles können, wenn sie erreicht, sodass wir einer Möglichkeit, die den Spieler tatsächlich davon überzeugen, dass etwas gefunden, die ungültige darauf happed hatte. In herkömmlichen spielen möglicherweise angezeigt, dass möglicherweise ein wenig grunt-eine Animation, die Ihnen mitteilt, Ihre Zeichen eine Trefferüberprüfung übernommen hat oder der Bildschirm kann flash, Rot und die Zeichen für Zeichen. Da solche Hinweise nicht in einer mixed Reality-Umgebung arbeiten, entschieden wir, die den visuellen Hinweis mit einem sehr langen Ton zu kombinieren, die Sie gibt an, Schaden ausgeführt zu haben. Ich einen großen Sound erstellt und machte es also in der testmischung, die sie alles, was Sie ducked deutliche. Klicken Sie dann hinzugefügt, damit sogar abheben können, wir einen kurzen Warnung Sound wie wenn nuclear Sub Auffangen wurde. 
<br>
![Wenn ein Player in RoboRaid erreicht wird Ruft, sie finden Sie unter einen visuellen Hinweis, sondern erhalten auch einen übertriebenen audiohinweis mit dem Hinweis, dass sie Schäden geworfen haben.](images/player-hit-roboraid-500px.jpg)

### <a name="getting-big-sound-from-small-speakers"></a>Abrufen von großen Sound aus kleinen Referenten

HoloLens-Lautsprecher sind kleine und einfache entsprechend die Anforderungen des Geräts, damit Sie nicht davon ausgehen können, zu hören zu viel Low-End. Ähnlich wie die Entwicklung von für Smartphones oder tragbaren Spielekonsolen, sound-Designern und Komponisten des Inhalts ihrer Audio Häufigkeit berücksichtigen. Ich immer Sounds entwerfen oder Musik mit vollständigen Frequenzbereich geschrieben werden, da steht, geteert Kopfhörer eine Option für den Benutzer ist. Jedoch ausgeführt, um Kompatibilität mit HoloLens Lautsprechern sichergestellt ist, ich einen Test gelegentlich durch Einfügen einer EQ in der Master jeder BREHM ich zufällig sein. Die EQ-Einstellung besteht ein Filter Hochpass-ca. 600 auf 700 Hz (nicht zu steile) aus, und Tiefpass-filter bei etwa 10 KB (sehr hohe). Die Sie erhalten einen Netzwerkmerkmale Überblick darüber, wie Ihre Sounds Wiedergabe auf dem Gerät ist.

Wenn Sie sich Bass Sinne Sehne Ändern Ihrer Musik gewähren verlassen, können Sie feststellen, dass es sich bei Ihrer Musik Sinne Stamm vollständig verloren gehen, wenn Sie diese Einstellung EQ anwenden. Zur Behebung des Problems, ich die "Bass", die einer Oktave höher (mit einigen umfassenden oberschwingungen) ist eine weitere Ebene hinzugefügt und kombiniert, um die Bedeutung von Stamm zurück zu erhalten. In einigen Fällen mit Verzerrung zu darzustellen, und Sie die oberschwingungen erhalten genug Häufigkeit Inhalte im oberen Bereich unseres Gehirns glauben, dass etwas darunter vornehmen. Dies ist für SFX wie Auswirkungen, Explosionen oder Sounds für spezielle Augenblicken wird "true", wie ein könner Super-Angriffe. Sie können nicht wirklich auf die Low-End, das dem Spieler einen Eindruck von Auswirkungen oder den Gewichtungsfaktor vermitteln verlassen. Wie bei Musik, dabei geholfen definitiv mit Verzerrung zu darzustellen, geben Sie ein wenig aufschlüsseln.

### <a name="making-your-audio-cues-stand-out"></a>Machen Ihre Audiohinweise abheben

Natürlich sollte jeder im Team bombastic Musik, laut Vorgabe und verrückten Explosionen; aber sie zudem soll demonstriert werden, um Voiceover oder jeder anderen Spiel geschäftskritischen Audiohinweise hören zu können.

Auf eine Konsole mit vollständigen Bereich der Frequenz müssen Sie weitere Optionen zum Frequenzen je nach Wichtigkeit des Sounds unterteilen. Für RoboRaid wurde jedoch ich die Anzahl der Bereiche von Frequenzen beschränkt, die ich von Sounds, Kurve konnte. Z. B. bei Verwendung von Tiefpass-Filter und Kurve zu viel über das obere Ende des Spektrums herausgefiltert müssen Sie nicht alles auf den Sound zurückgelassen werden, da es nicht viel Low-End ist.

Damit stellen RoboRaid sound so groß wie möglich auf dem Gerät, wir mussten den dynamischen Bereich, der die gesamte Umgebung zu senken und umfassenden Gebrauch von unterbieten, erstellen Sie eine klare Hierarchie von Bedeutung für verschiedene Arten von Sounds vorgenommen. Ich lege die unterbieten von-2-6 DB je nach Wichtigkeit. Mir persönlich gefällt nicht offensichtlich unterbieten in Spielen, damit ich habe viel Zeit, die Optimierung der ausblenden in bzw. aus Zeitplan und die Menge der Volume-Dämpfung damit verbracht. Wir richten Sie separate Bussen für räumliche Sound, nicht räumliche Sound, VO und dry Bus ohne Hall für Musik und sehr hohe Priorität, kritischen und unkritische Bussen erstellt. Die Ressourcen wurden dann fahren Sie mit ihren entsprechenden Bussen eingerichtet.

Ich hoffe, dass es Audioinhalte so viel und Dollerei auf ihren eigenen apps arbeiten, wie das Arbeiten mit RoboRaid verfügen. Ich kann nicht warten, finden Sie unter (und zu hören!) wie die talentierten Mitarbeiter außerhalb von Microsoft mit für HoloLens gestartet werden.

## <a name="do-it-yourself"></a>Es selbst tun.

Ein Trick, habe ich entdeckt, stellen Sie sicher, dass Ereignisse (z. B. Explosionen) klingt "vergrößern", wie sie den Platz ausfüllen – wurde zum Erstellen eines Medienobjekts mono, für den räumlichen Sound, auch gemischt mit einer 2D Stereo Medienobjekt in 3D wiedergegeben werden. Es einige Optimierungen, dauern, da zu viele Informationen in den Stereo Inhalten müssen die Richtung der mono Ressourcen verringern. Allerdings führt richtiges Gleichgewicht in großen Sounds, die Spieler, um den Kopf in die richtige Richtung aktivieren erhalten.

Sie können dies selbst mithilfe der nachfolgend aufgeführten Objekten audio versuchen:

**Szenario 1**
1. Herunterladen [roboraid_enemy_explo_mono.wav](images/roboraid-enemy-explo-mono.wav) und legen Sie für die Wiedergabe durch räumliche Sound und weisen sie Sie ein Ereignis.
2. Herunterladen [roboraid_enemy_explo_stereo.wav](images/roboraid-enemy-explo-stereo.wav) und für die Wiedergabe in 2D Stereo festgelegt, und weisen das gleiche Ereignis wie oben beschrieben. Da diese Objekte mit Unity normalisiert werden, Dämpfen Sie Volume der beiden Objekte, damit es nicht beschnitten.
3. Sound beide zusammen. Verschieben Sie Kopf etwa zu können, wie räumliche es klingt.

**Szenario 2**
1. Herunterladen [roboraid_enemy_explo_summed.wav](images/roboraid-enemy-explo-summed.wav) und legen Sie für die Wiedergabe durch räumliche Sound und weisen auf ein Ereignis.
2. Wiedergeben von diesem Medienobjekt selbst, und klicken Sie dann aus Szenario 1 mit dem Ereignis vergleichen.
3. Versuchen Sie es unterschiedliche Balance von mono und Stereo-Dateien.

## <a name="about-the-author"></a>Der Autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Charles Sinex" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Charles Sinex</b><br>Audio Engineer @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Siehe auch
* [Räumliche sound](spatial-sound.md)
* [RoboRaid für Microsoft HoloLens](https://www.microsoft.com/en-us/p/roboraid/9nblggh5fv3j)
