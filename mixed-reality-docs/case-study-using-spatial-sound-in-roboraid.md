---
title: 'Fallstudie: Verwenden von räumlichem Sound in roboraid'
description: Räumlicher Sound ist eines der interessantesten Features von Microsoft hololens und bietet Benutzern die Möglichkeit, das Problem zu erkennen, wenn die Objekte nicht mehr in der Sicht sind.
author: mattzmsft
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, hololens, roboraid, räumlicher Sound
ms.openlocfilehash: 4bb050b4a4051c121c488ea38e150a8973bd7c04
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524155"
---
# <a name="case-study---using-spatial-sound-in-roboraid"></a>Fallstudie: Verwenden von räumlichem Sound in roboraid

Charles Sinex, audioleiter im Microsoft hololens-Team, spricht über die besonderen Herausforderungen, die bei der Erstellung von Audiodaten für [roboraid](https://www.microsoft.com/en-us/p/roboraid/9nblggh5fv3j)aufgetreten sind, einem gemischten Reality First-Person-Shooter.

## <a name="the-tech"></a>Die Technologie

[Räumlicher Sound](spatial-sound.md) ist eines der interessantesten Features von Microsoft hololens und bietet Benutzern die Möglichkeit, das Problem zu erkennen, wenn die Objekte nicht mehr in der Sicht sind.

In roboraid besteht die offensichtlichste und effektivste Verwendung von räumlichem Sound darin, den Player an etwas zu warnen, das außerhalb der peripheren Vision des Benutzers stattfindet. Beispielsweise kann der breacher von einem der überprüften Wände im Raum eingeben, aber wenn Sie nicht an der Stelle sind, an der er eintritt, wird er möglicherweise übersehen. Um Sie bei dieser Invasion zu warnen, hören Sie ein unterschiedliches Audiostück, von dem aus der breacher wechselt, damit Sie wissen, dass Sie schnell reagieren müssen, um es zu verhindern.

## <a name="behind-the-scenes"></a>Im Hintergrund

Der Prozess der Erstellung räumlicher Sounds für hololens-Apps ist so neu und einzigartig, und das Fehlen früherer Projekte, die für den Verweis verwendet werden, kann zu einer großen Beeinträchtigung führen, wenn ein Problem auftritt. Hoffentlich helfen Ihnen diese Beispiele für die audioherausforderungen bei der Erstellung von roboraid bei der Erstellung von Audiodaten für Ihre eigenen apps.

### <a name="be-mindful-of-taxing-the-cpu"></a>Berücksichtigen der CPU-Auslastung

Räumlicher Sound kann auf der CPU anspruchsvoll sein. Für eine ausgelastete Umgebung wie roboraid war es wichtig, dass die Instanzen räumlicher Sounds zu einem bestimmten Zeitpunkt unter acht gehalten wurden. Größtenteils war es so einfach, das Limit von Instanzen unterschiedlicher Audioereignisse festzulegen, sodass alle Instanzen, die nach Erreichen des Limits auftreten, abgebrochen werden. Wenn beispielsweise Drohnen ausgegeben werden, sind Ihre Screams auf drei Instanzen zu einem beliebigen Zeitpunkt beschränkt. Wenn nur ungefähr vier Drohnen gleichzeitig erzeugt werden können, sind drei scremes ausreichend, da das Gehirn nicht so viele ähnlich klingende Audioereignisse verfolgen kann. Dadurch wurden Ressourcen für andere räumliche Audioereignisse freigegeben, wie z. b. feindliche Explosionen oder Feinde, die sich auf das Schießen vorbereiten

### <a name="rewarding-a-successful-dodge"></a>Belohnen eines erfolgreichen ausweichen

Der Dodging-Mechaniker ist einer der wichtigsten Aspekte des Spiels in roboraid, und auch etwas, das wir uns fühlen, war für die hololens-Umgebung wirklich einzigartig. Daher wollten wir die erfolgreichen Dodges für den Player sehr lohnend gestalten. Wir haben den Doppler "Whizz-by" ("Whizz-by") in die Entwicklung gebracht. Anfänglich war der Plan, eine Schleife zu verwenden und Sie in Echtzeit mithilfe von Volume, Tonhöhe und Filter zu manipulieren. Die Implementierung für diese Vorgehensweise war sehr aufwendig, daher haben wir vor dem Commit von Ressourcen zur eigentlichen Erstellung einen kostengünstigen Prototyp mit einem Asset erstellt, bei dem der Doppler Effekt, der in gebacken wurde Unsere begabten Entwickler haben es so gestaltet, dass dieses Whizz-by-Asset genau 0,7 Sekunden wiedergegeben würde, bevor die Projekt Kachel vom Player gereicht wird und die Ergebnisse sehr erstaunlich waren! Natürlich haben wir die komplexere Lösung unterzogen und den Prototyp implementiert.

\* * (Wenn Sie weitere Informationen über das Erstellen eines audioassets mit dem integrierten Doppler-Effekt erhalten möchten, sehen Sie sich einen Artikel von Sounddesigner Charles deeran, der [in zwei Minuten als "100 whooshes](http://designingsound.org/2010/02/charles-deenen-special-100-whooshes-in-2-minutes/)" bezeichnet wird.) *
<br>
![Durch das erfolgreiche Dodging eines "projectile" eines Feindes wird der Spieler durch einen Sound zufriedenstellend.](images/successful-dodge-roboraid-500px.jpg)

### <a name="ditching-ineffective-sounds"></a>Abrufen von ineffektiven Sounds

Ursprünglich wollten wir einen explodierenden Sound hinter dem Player abspielen, nachdem Sie den feindlichen projectile erfolgreich angedochelt haben, aber wir haben uns entschieden, dies aus verschiedenen Gründen zu verwerfen. Erstens war das nicht so effektiv wie das von SFX, das wir für den Dodge verwendet haben. Zu dem Zeitpunkt, an dem die Projekt Kachel auf eine Wand hinter Ihnen stößt, wäre im Spiel etwas anderes passiert, das den Sound ziemlich maskiert. Zweitens haben wir keine Kollision im Boden gefunden, deshalb konnten wir die Explosion nicht wiederholen, wenn die projectile anstelle der Wände auf den Fußboden prallte. Und schließlich gab es die CPU-Kosten des räumlichen Sounds. Der Elite-Skorpion (einer, der sich innerhalb der Wand durchforsten kann) hat einen besonderen Angriff, der etwa acht Projekt Kacheln durchsucht. Dies führte nicht nur zu einem großen Chaos in der Mischung, sondern führte auch zu einer sehr großen Überlastung, da die CPU zu schwierig war.

### <a name="communicating-a-hit"></a>Kommunizieren eines Treffer

Ein interessantes Problem, das wir uns für die hololens-Funktion befunden haben, war die Schwierigkeit, effektiv mit den Playern zu kommunizieren, die Sie getroffen haben. Eine gemischte Realität führt zu einer erfolgreichen Darstellung der Geschichte. Dies bedeutet, dass Sie glauben müssen, dass Sie eine fremde Roboter-Invasion in Ihrem eigenen Lebensraum bekämpfen.

Spieler fühlen sich offensichtlich nichts, wenn Sie auf Sie stoßen. Daher mussten wir eine Möglichkeit finden, den Player zu überzeugen, dass etwas schlecht war. In herkömmlichen spielen wird möglicherweise eine Animation angezeigt, mit der Sie wissen, dass Ihr Zeichen einen Treffer ausgelöst hat, oder der Bildschirm ist rot, und Ihr Zeichen ist möglicherweise ein wenig. Da diese Arten von Hinweisen nicht in gemischter Realität funktionieren, haben wir uns dazu entschieden, den visuellen Hinweis mit einem wirklich übertriebenen Sound zu kombinieren, der anzeigt, dass Sie Schaden anrichten. Ich habe einen großen Sound erstellt und ihn so hervorgehoben, dass er in der Mischung alles hervorgehoben hat. Um den Code noch weiter zu machen, haben wir eine kurze Warnmeldung mit dem Hinweis hinzugefügt, dass eine atomarische Untermenge nicht versinkt. 
<br>
![Wenn ein Player in roboraid erreicht wird, sehen Sie einen visuellen Hinweis, Sie erhalten aber auch einen übertriebenen audiohinweis, der Sie darüber informiert, dass Sie Schaden anrichten.](images/player-hit-roboraid-500px.jpg)

### <a name="getting-big-sound-from-small-speakers"></a>Holen Sie sich einen großen Sound von kleinen Referenten

Hololens-Sprecher sind klein und leicht, um den Anforderungen des Geräts gerecht zu werden, sodass Sie nicht zu viel tiefstschluss erwarten. Ähnlich wie bei der Entwicklung für Smartphones oder Hand Held Spielgeräte müssen Sounddesigner und-Komponisten den Frequenz Inhalt Ihrer Audiodaten berücksichtigen. Ich erstelle immer Sounds oder schreibe Musik mit vollständigem Frequenzbereich, da das Übertragen von Kopfhörern eine Option für die Benutzer ist. Um jedoch die Kompatibilität mit den Referenten von hololens sicherzustellen, führe ich gelegentlich einen Test durch, indem ich einen EQ in den Master einer beliebigen DAW Stelle setze, in der ich arbeite. Die EQ-Einstellung besteht aus einem High-Pass-Filter zwischen 600 und 700 Hz (nicht zu steil) und einem Tiefpass Filter bei ungefähr 10K (sehr steil). Dadurch sollte eine groben-Idee angezeigt werden, wie Ihre Sounds auf dem Gerät wiedergegeben werden.

Wenn Sie sich auf den Bass verlassen, um die Sense-Änderung in ihrer Musik zu vermitteln, werden Sie möglicherweise feststellen, dass Ihre Musik den Grund für den Stamm verliert, wenn Sie diese EQ-Einstellung anwenden. Um dieses Problem zu beheben, habe ich dem Bass eine andere Ebene hinzugefügt, die eine Oktave höher (mit einigen umfangreichen Harmonisierungen) ist, und Sie gemischt, um den Grund für den Stamm wieder zu verstehen. Manchmal wird durch die Verwendung von Verzerrung zum Einrichten der Harmonisierungen ausreichend Häufigkeits Inhalt im oberen Bereich angezeigt, damit das Gehirn der Ansicht ist, dass es etwas darunter gibt. Dies gilt für SFX, wie z. b. Auswirkungen, Explosionen oder Sounds, wie z. b. die Super-Angriffe eines Chefs. Sie können sich nicht auf das niedrige Ende verlassen, um dem Player einen Eindruck von Auswirkung oder Gewichtung zu verschaffen. Wie bei Musik wurde die Verwendung von "Verzerrung", um etwas zu erreichen, definitiv geholfen.

### <a name="making-your-audio-cues-stand-out"></a>Stellen Sie Ihre Audiohinweise bereit

Natürlich wünschte sich jede Person im Team bombastische Musik, laute Gewehre und verrückte Explosionen. Sie wollten aber auch in der Lage sein, VoiceOver oder andere Spiel kritische Audiohinweise zu hören.

Bei einem Konsolenspiel mit vollständigem Frequenzbereich haben Sie mehr Optionen, um die Häufigkeit abhängig von der Bedeutung des Sounds aufzuteilen. Für roboraid war es jedoch in der Anzahl der Häufigkeits Bereiche beschränkt, die ich aus Sounds herausfiltern konnte. Wenn Sie beispielsweise den Filter mit einem Tiefpass-Filter verwenden und sich am oberen Ende des Spektrums zu stark auslagern, haben Sie auf dem Sound nichts übrig, da es nicht allzu wenig zu niedrig ist.

Damit roboraid so groß wie das auf dem Gerät sein kann, mussten wir den dynamischen Bereich der gesamten Umgebung verringern und eine umfassende Verwendung von Ducking durchführen, indem wir eine klare Hierarchie von Wichtigkeit für verschiedene Arten von Sounds erstellt haben. Abhängig von der Wichtigkeit wird das Ducking von-2 auf-6 dB festgelegt. Ich persönlich weiß nicht, dass ich mich in spielen in spielen, also habe ich viel Zeit damit verbracht, die Einblend-/Ausgabezeit und den Umfang der volumedämpfung zu optimieren. Wir haben separate Busse für räumliche Audiodaten, nicht räumliche Sounds, VO und Dry Bus ohne Hall für Musik eingerichtet und anschließend sehr hohe, wichtige und nicht kritische Busse erstellt. Die Assets wurden dann so eingerichtet, dass Sie in die entsprechenden Busse gelangen.

Ich hoffe, dass Audiofachleute es so viel Spaß machen und mit der Arbeit an Ihren eigenen apps arbeiten, da ich mich an roboraid gearbeitet habe. Ich kann nicht abwarten (und hören!), was die talentierten Menschen außerhalb von Microsoft für hololens finden.

## <a name="do-it-yourself"></a>Selbst ausführen

Ein von mir ermittelter Trick, mit dem bestimmte Ereignisse (z. b. Explosionen) "größer" sind – wie Sie den Raum Auffüllen – bestand darin, ein Mono-Medienobjekt für den räumlichen Ton zu erstellen und es mit einem 2D-Stereo Asset zu mischen, das in 3D wiedergegeben werden sollte. Es wird eine gewisse Optimierung durchführen, da zu viele Informationen in den Stereo Inhalten die Direktionalität der Mono-Assets verringern werden. Allerdings führt das Erreichen des Saldo Recht zu sehr großen Sounds, mit denen sich die Spieler in der richtigen Richtung drehen können.

Sie können dies selbst ausprobieren, indem Sie die folgenden Audioressourcen verwenden:

**Szenario 1**
1. Laden Sie [roboraid_enemy_explo_mono. wav](images/roboraid-enemy-explo-mono.wav) herunter, und legen Sie auf Wiedergabe durch räumlichen Ton fest.
2. Laden Sie [roboraid_enemy_explo_stereo. wav](images/roboraid-enemy-explo-stereo.wav) herunter, und legen Sie auf Wiedergabe in 2D-Stereo fest, und weisen Sie dem gleichen Ereignis wie oben zu Da diese Assets in Unity normalisiert werden, können Sie die Menge beider Assets dämpfen, damit Sie nicht abruft.
3. Wiedergeben beide Sounds. Bewegen Sie sich den Kopf, um zu erfahren, wie räumliche IT klingen.

**Szenario 2**
1. Laden Sie [roboraid_enemy_explo_summed. wav](images/roboraid-enemy-explo-summed.wav) herunter, und legen Sie auf Wiedergabe durch räumlichen Ton fest, und weisen Sie einem Ereignis zu
2. Diese Ressource selbst wiedergeben und dann mit dem Ereignis aus Szenario 1 vergleichen.
3. Probieren Sie ein anderes Gleichgewicht von Mono-und Stereo Dateien aus.

## <a name="about-the-author"></a>Informationen zum Autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Charles Sinex" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Charles Sinex</b><br>Audioingenieur@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Siehe auch
* [Raumklang](spatial-sound.md)
* [Roboraid für Microsoft hololens](https://www.microsoft.com/en-us/p/roboraid/9nblggh5fv3j)
