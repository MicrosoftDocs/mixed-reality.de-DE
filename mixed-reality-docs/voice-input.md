---
title: Spracheingabe
description: Spracheingabe ist eine Core-Eingabe für HoloLens und Windows Mixed Reality immersive Headsets. Voice kann für Befehle, Cortana, Diktat und mehr verwendet werden.
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: Ggv "," Stimme "," Cortana "," Spracheingabe,
ms.openlocfilehash: 7fb5618c13ff1ed446241f744b598cfe2484ea45
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604744"
---
# <a name="voice-input"></a>Spracheingabe

Voice ist einer der drei wichtigsten Formen der Eingabe für HoloLens. Damit können Sie direkt ggf. ein Hologramm Befehl ohne verwenden [Gesten](gestures.md). Sie einfach [bestaunen](gaze.md) am ggf. ein Hologramm und den Befehl. Spracheingabe kann es sich um eine natürliche Möglichkeit zum kommunizieren Ihre Absicht sein. Voice ist besonders gut für komplexe Schnittstellen durchlaufen, da Benutzer über verschachtelte Menüs mit einem Befehl zu senken können.

Spracheingabe basiert auf der [dasselbe Modul](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) , die Spracherkennung in anderen universellen Windows-Apps unterstützt.

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Feature</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1. Generation)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td> Spracheingabe</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️ (mit Mikrofon)</td>
</tr>
</table>

## <a name="the-select-command"></a>Der Befehl "select"

Auch ohne speziell Ihrer app Voice-Unterstützung hinzufügen, können Ihre Benutzer Hologramme aktivieren, einfach, indem Sie sagen, "select". Dadurch verhält sich wie ein [tippbewegung](gestures.md#air-tap) für HoloLens, drücken Sie die auswählen-Schaltfläche auf der [HoloLens Clicker](hardware-accessories.md#hololens-clicker), oder drücken auf den Trigger eine [Windows Mixed Reality-Motion-Controller](motion-controllers.md). Sie werden einen Sound hören und sehen eine QuickInfo mit "Select", die als Bestätigung angezeigt werden. "Select" von einem niedrigen Energiestatus-Schlüsselwort Erkennung-Algorithmus aktiviert ist, sodass sie immer noch mit der Hand auf Ihrer Seite zu einem beliebigen Zeitpunkt mit Auswirkungen auf die minimale Akku Leben, sagt verfügbar ist.

> [!NOTE]
> Weitere Anleitungen, die speziell für HoloLens 2 [bald](index.md#news-and-notes).

![Sagen Sie "select", um für die Auswahl den Voice-Befehl verwenden](images/kma-voice-select-00170-800px.png)<br>
*Sagen Sie "select", um für die Auswahl den Voice-Befehl verwenden*

## <a name="hey-cortana"></a>Hey Cortana

Sie können auch "Hey Cortana" zum Hochfahren von Cortana jederzeit sagen. Sie müssen nicht warten, bis sie zum Fortfahren, stellen sie Ihre Frage oder erteilen sie eine Anweisung – beispielsweise versuchen, mit dem Text angezeigt werden "Hey Cortana was das Wetter ist?" als einen einzelnen Satz. Weitere Informationen zu Cortana und was Sie tun können einfach bitten Sie ihn! Sagen Sie "Hey Cortana, was kann, ich sagen?" und sie eine Liste der Befehle funktionieren und vorgeschlagenen abgerufen werden. Wenn Sie bereits in der Cortana-app sind Sie können auch klicken die **?** Symbol in der Seitenleiste im gleichen Menü-kontoportals.

**HoloLens-Befehle**
* Was kann ich sagen?
* "Go home" oder "Gehe zu Start" - anstelle von [Bloom](gestures.md#bloom) , um erhalten [Menü "Start"](navigating-the-windows-mixed-reality-home.md#start-menu)
* "Starten <app>"
* "Verschieben <app> hier"
* "Foto"
* "Starten Sie Aufzeichnung"
* "Aufzeichnung beenden"
* "Erhöhen Sie die Helligkeit"
* "Verringern Sie die Helligkeit"
* "Erhöhen Sie die Lautstärke"
* "Decrease des Volumes"
* "Ton aus" oder "Stummschaltung aufheben"
* "Herunterfahren Sie auf dem Gerät"
* "Das Gerät neu gestartet"
* "Wechseln Sie in den Ruhezustand versetzt."
* "Wann ist es"?
* "Wie lange der Akku übrig ich habe?"
* "Rufen <contact>" (erfordert Skype für HoloLens)

## <a name="see-it-say-it"></a>"Angezeigt, das so sagen."

HoloLens verfügt über ein "angezeigt, das so sagen"-Modell für die Spracheingabe, wo Bezeichnungen auf Schaltflächen Benutzer welche Sprachbefehle auch sagen können. Beispielsweise kann in einer Direct2D-app ein Benutzer den Befehl "Anpassen" sagen, die sie in der App-Leiste anzeigen, um die Position in der Welt der app anzupassen.

![Beim Betrachten einer Direct2D-app oder ein Hologramm, kann ein Benutzer den Befehl "Anpassen" sagen die sie in der App-Leiste anzeigen, um die Position in der Welt der app anzupassen](images/microphone-600px.png)

Wenn apps mit dieser Regel befolgen, können Benutzer problemlos was an, dass das System So kontrollieren verstehen. Um dies noch beim gazing auf eine Schaltfläche zu unterstreichen, sehen Sie eine "Stimme Dwell" QuickInfo, die nach einer Sekunde tritt auf, wenn die Schaltfläche VCD- und der Befehl zeigt, um "Drücken der Taste" zu sprechen.

![Anzeigen, das so sagen Befehle werden unter den Schaltflächen angezeigt.](images/voice-seeitsayit-600px.png)<br>
*"Sehen es noch einmal"-Befehle unter den Schaltflächen angezeigt werden*

## <a name="voice-commands-for-fast-hologram-manipulation"></a>Sprachbefehle für schnelle Bearbeitung von – Hologramm

Es gibt auch eine Anzahl von Voice-Befehle können Sie beim am ggf. ein Hologramm Manipulation Aufgaben schnell gazing sagen. Diese Sprachbefehle arbeiten auf Direct2D-apps als auch für 3D-Objekte, die Sie in der Welt platziert haben.

**Befehlen – Hologramm**
* Stehen mir vor
* Größere | Zu verbessern
* Kleinere

## <a name="dictation"></a>Diktieren

Anstatt die Eingabe mit [Luft Taps](gestures.md#air-tap), Spracheingabe-kann effizienter sein, Text in eine app eingeben. Dies kann die Eingabe mit weniger Aufwand für den Benutzer erheblich beschleunigen.

![Spracheingabe-beginnt, durch Auswählen der Mikrofonschaltfläche](images/micbuttonfordictation.png)<br>
*Spracheingabe-beginnt, durch Auswählen der Mikrofonschaltfläche "auf der Tastatur*

Jedes Mal, wenn die Tastatur holographic aktiv ist, können Sie auf den Diktatmodus anstatt wechseln. Wählen Sie das Mikrofon im Zweifelsfall das Texteingabefeld für den Einstieg.

## <a name="communication"></a>Kommunikation

Für Anwendungen, die der Verarbeitungsoptionen, die von HoloLens bereitgestellte benutzerdefinierte Audioeingabe nutzen möchten, ist es wichtig zu verstehen, die verschiedenen [Audiodatenstrom Kategorien](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) Ihrer app nutzen kann. Windows 10 unterstützt verschiedene Kategorien von anderen Stream und HoloLens macht verwenden drei davon, um benutzerdefinierte Verarbeitung zum Optimieren der Qualität der Mikrofon audio speziell für die Sprache, Kommunikation und andere dem für Audio der ambient-Umgebung verwendet werden kann zu aktivieren erfassungsszenarios (d. h. "Camcorder").
* AudioCategory_Communications Stream Kategorie wird für Aufruf Qualität und erzählfluss Szenarien angepasst und stellt dem Client mit einem Mono / audio Stream mit 16 24-Bit-kHz des Benutzers Stimme
* Die Kategorie "AudioCategory_Speech Stream" ist für die spracherkennungs-Engine für HoloLens (Windows) angepasst und wird mit mono 16kHz 24-Bit-Stream des Benutzers Stimme. Diese Kategorie kann bei Bedarf durch 3rd Party Sprachmodule verwendet werden.
* AudioCategory_Other Stream Kategorie wird für die audioaufzeichnung ambient-Umgebung angepasst und stellt dem Client mit einem Stereo audio 48kHz 24-Bit-Stream.

Alle diese audio Verarbeitung ist, dass die Hardwarebeschleunigung, was bedeutet, dass die Funktionen zu leeren viel weniger Energie als wenn die gleiche Verarbeitung auf der CPU HoloLens erfolgte. Vermeiden Sie es anderen Audioeingabe, die Verarbeitung auf die CPU zum Maximieren der System Akkuverbrauch gering zu halten, und profitieren Sie von den integrierten, offloaded audio Eingabeverarbeitung.

## <a name="troubleshooting"></a>Problembehandlung

Wenn Sie alle Probleme, die mit "select" und "Hey Cortana" haben, versuchen Sie, um ruhigerer Leerzeichen und Aktivieren der Weg von der Quelle des Störungen oder sprechen lauter zu verschieben. Zu diesem Zeitpunkt ist die Spracherkennung für HoloLens optimiert und speziell für die native Lautsprecher des Englisch (USA) optimiert.

Für die Windows Mixed Reality Developer Edition-Version 2017 wird die Verwaltungslogik audio-Endpunkt (d.h. für immer) einwandfrei nach dem Abmelden und wieder in Protokollierung auf dem PC-Desktop nach der ersten HMD-Verbindung. Vor dieser ersten Anmeldung out/in-Ereignis nach dem laufenden über WMR OOBE kann der Benutzer verschiedene audio-Funktionalität Probleme, die keine Audiodaten, abhängig davon, wie das System eingerichtet wurde vor dem Herstellen einer Verbindung die HMD zum ersten Mal Wechseln zwischen ohne Audio auftreten.

## <a name="see-also"></a>Siehe auch
* [Spracheingabe in DirectX](voice-input-in-directx.md)
* [Spracheingabe in Unity](voice-input-in-unity.md)
* [MR Eingabe 212: Voice](holograms-212.md)
