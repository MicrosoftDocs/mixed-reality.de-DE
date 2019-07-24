---
title: Spracheingabe
description: Die Spracheingabe ist eine Kern Eingabe für hololens und Windows Mixed Reality-immersive Headsets. Voice kann für Befehle, Diktat, Cortana usw. verwendet werden.
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: GGV, Voice, Cortana, Speech, Input
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829947"
---
# <a name="voice-input"></a>Spracheingabe

Voice ist eine der drei wichtigen Formen der Eingabe in hololens. Damit können Sie ein – Hologramm direkt aufrufen, ohne [Gesten](gestures.md)verwenden zu müssen. Sie betrachten [einfach ein](gaze.md) – Hologramm und sprechen Ihren Befehl. Die Spracheingabe kann eine natürliche Möglichkeit sein, ihre Absicht zu kommunizieren. Die Spracheingabe eignet sich besonders gut für die Durchführung komplexer Schnittstellen, da Benutzer mit einem Befehl die Möglichkeit haben, die Verwendung von Netz Menüs zu

Die Spracheingabe wird von [derselben Engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) unterstützt, die Sprache in allen anderen universellen Windows-Apps unterstützt.

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

## <a name="device-support"></a>Unterstützung von Geräten

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Funktion</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Spracheingabe</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (mit Mikrofon)</td>
    </tr>
</table>

## <a name="the-select-command"></a>Der Befehl "Select"

Selbst wenn Sie Ihrer APP keine Sprachunterstützung hinzufügen, können Ihre Benutzer Hologramme einfach durch das sagen von "Select" aktivieren. Dies verhält sich wie eine [Luft](gestures.md#air-tap) Abzweigung in hololens, das Drücken der Schaltfläche "auswählen" auf dem [hololens-Clicker](hardware-accessories.md#hololens-clicker)oder das Drücken des Auslösers auf einem [Windows Mixed Reality Motion Controller](motion-controllers.md). Sie werden einen Sound hören und sehen, dass eine QuickInfo mit "Select" als Bestätigung angezeigt wird. "Select" wird durch einen Algorithmus für die Erkennung eines niedrigen Leistungs Worts aktiviert, sodass Sie jederzeit mit minimalen Auswirkungen auf die Akku Lebensdauer jederzeit angezeigt werden können. Dies gilt auch für Ihre Hände.

> [!NOTE]
> Weitere Anleitungen sind für hololens 2 in [Kürze](index.md#news-and-notes)verfügbar.

!["Select" (auswählen), um den Sprachbefehl zur Auswahl zu verwenden](images/kma-voice-select-00170-800px.png)<br>
*"Select" (auswählen), um den Sprachbefehl zur Auswahl zu verwenden*

## <a name="hey-cortana"></a>Hallo, Cortana

Sie können auch "Hey Cortana" sagen, um Cortana jederzeit zu erhalten. Sie müssen nicht warten, bis Sie angezeigt wird, um Ihre Frage zu stellen oder eine Anweisung zu geben, z. b. "Hey Cortana What es Weather?". als einzelner Satz. Weitere Informationen zu Cortana und den Möglichkeiten, die Sie tun können, finden Sie einfach! Sagen Sie "Hallo Cortana was kann ich sagen?" und Sie werden eine Liste der funktionierenden und vorgeschlagenen Befehle abrufen. Wenn Sie sich bereits in der Cortana-App befinden, können Sie auch auf die **?** Symbol auf der Rand Leiste, um das gleiche Menü zu ziehen.

**Hololens-spezifische Befehle**
* Was kann ich sagen?
* "Go Home" oder "Gehe zu Start"-anstelle von " [Bloom](gestures.md#bloom) ", um zum [Startmenü](navigating-the-windows-mixed-reality-home.md#start-menu) zu gelangen
* "Starten <app>"
* "Hier <app> verschieben"
* "Bild nehmen"
* "Aufzeichnung starten"
* "Aufzeichnung anhalten"
* "Erhöhen der Helligkeit"
* "Die Helligkeit verringern"
* "Volume vergrößern"
* "Volume verkleinern"
* "Stumm schalten" oder "unstumm schalten"
* "Gerät Herunterfahren"
* "Gerät neu starten"
* "Gehe zu Standbymodus"
* "Welche Zeit ist es?"
* "Wie viel Akku habe ich verbleiben?"
* "Anrufen <contact>" (erfordert Skype für hololens)

## <a name="see-it-say-it"></a>"Weitere Informationen"

Hololens hat eine "See it"-Modell für die Spracheingabe, bei der Bezeichnungen auf Schaltflächen den Benutzern mitteilen, welche Sprachbefehle Sie auch sagen können. Wenn Sie z. b. eine 2D-App betrachten, kann ein Benutzer den Befehl "anpassen" anzeigen, der in der APP-Leiste angezeigt wird, um die Position der APP auf der ganzen Welt anzupassen.

![Wenn Sie sich eine 2D-APP oder ein Hologram ansehen, kann ein Benutzer den Befehl "anpassen" anzeigen, der in der APP-Leiste angezeigt wird, um die Position der APP auf der ganzen Welt anzupassen.](images/microphone-600px.png)

Wenn apps diese Regel befolgen, können Benutzer leicht erkennen, was zum Steuern des Systems zu sagen ist. Um dies zu verstärken, sehen Sie die QuickInfo, die nach einer Sekunde angezeigt wird, wenn die Schaltfläche sprach fähig ist, und zeigt den Befehl an, um zu sprechen, um die Schaltfläche zu "drücken".

![Sehen Sie, dass die Befehle unter den Schaltflächen angezeigt werden.](images/voice-seeitsayit-600px.png)<br>
*"Sehen Sie, dass die Befehle unter den Schaltflächen angezeigt werden.*

## <a name="voice-commands-for-fast-hologram-manipulation"></a>Sprachbefehle für schnelle Hologram-Bearbeitung

Es gibt auch eine Reihe von Sprachbefehlen, die Sie bei der Betrachtung eines holograms zum schnellen Ausführen von Bearbeitungsaufgaben sagen können. Diese Sprachbefehle funktionieren sowohl für 2D-Apps als auch für 3D-Objekte, die Sie in der Welt abgelegt haben.

**Hologram-Bearbeitungsbefehle**
* Gesicht
* Größer | Verbessern
* Geringeren

## <a name="dictation"></a>Diktieren

Anstatt eine Typisierung mit [Luft](gestures.md#air-tap)Eingaben durchführen zu können, kann es effizienter sein, Text in eine APP einzugeben. Dadurch kann die Eingabe erheblich beschleunigt werden, sodass der Benutzer weniger Aufwand hat.

![Sprach Diktat beginnt mit der Schaltfläche Mikrofon](images/micbuttonfordictation.png)<br>
*Sprach Diktat beginnt mit der Schaltfläche Mikrofon auf der Tastatur*

Jedes Mal, wenn die holografische Tastatur aktiv ist, können Sie in den Diktat Modus wechseln, anstatt einzugeben. Wählen Sie das Mikrofon auf der Seite des Texteingabe Felds aus, um loszulegen.

## <a name="communication"></a>Kommunikation

Für Anwendungen, die die von hololens bereitgestellten angepassten audioeingabeverarbeitungs-Optionen nutzen möchten, ist es wichtig, die verschiedenen [audiostreamkategorien](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) zu verstehen, die Ihre APP nutzen kann. Windows 10 unterstützt mehrere verschiedene streamkategorien, und hololens nutzt drei dieser Möglichkeiten, um die benutzerdefinierte Verarbeitung zur Optimierung der Mikrofon Audioqualität zu optimieren, die auf Sprache, Kommunikation und andere zugeschnitten ist und für Umgebungs Umgebungs Audiodaten verwendet werden kann. Erfassungs Szenarien (d.h. "Camcorder").
* Die Kategorie AudioCategory_Communications Stream ist für die Sprach-und Erzähl Szenarios angepasst und stellt dem Client einen 16-Bit-Mono-Mono-Audiostream der Stimme des Benutzers zur Verfügung.
* Die Kategorie AudioCategory_Speech Stream ist für die Sprach-Engine hololens (Windows) angepasst und bietet einen 16-Bit-Mono-Mono-Datenstrom der Stimme des Benutzers. Diese Kategorie kann bei Bedarf von Sprachmodulen von Drittanbietern verwendet werden.
* Die AudioCategory_Other Stream-Kategorie ist für die Audioaufzeichnung in Umgebungs Umgebungen angepasst und stellt dem Client einen Stereo-Audiostream mit 48 kHz 24 Bit bereit.

Die gesamte Audioverarbeitung ist Hardware beschleunigt. Dies bedeutet, dass die Features viel weniger Leistung als bei der Verarbeitung der hololens-CPU benötigen. Vermeiden Sie die Ausführung einer anderen audioeingabeverarbeitung auf der CPU, um die Akku Lebensdauer zu maximieren und die integrierte, offloaded audioeingabeverarbeitung zu nutzen.

## <a name="troubleshooting"></a>Problembehandlung

Wenn Sie Probleme bei der Verwendung von "Select" und "Hey Cortana" haben, versuchen Sie, zu einem ruhigeren Bereich zu wechseln, die Ursache für Rauschen zu machen oder lauter zu sprechen. Zu diesem Zeitpunkt wird die Spracherkennung in hololens speziell für systemeigene Sprecher von USA Englisch optimiert und optimiert.

Für Windows Mixed Reality Developer Edition, Version 2017, funktioniert die audioendpunkt-Verwaltungs Logik problemlos (immer), nachdem Sie sich nach der anfänglichen HMD-Verbindung beim PC-Desktop abgemeldet hat. Vor dem ersten Abmelden/in-Ereignis nach dem Durchlaufen von WMR OOBE könnte der Benutzer verschiedene Probleme mit der Audiofunktionalität aufweisen, von denen kein audiowechsel bis hin zu keinem audiowechsel stattfindet, je nachdem, wie das System vor dem ersten Herstellen einer Verbindung mit dem HMD eingerichtet wurde.

## <a name="see-also"></a>Siehe auch
* [Spracheingabe in DirectX](voice-input-in-directx.md)
* [Spracheingabe in Unity](voice-input-in-unity.md)
* [MR-Eingabe 212: Sprache](holograms-212.md)
