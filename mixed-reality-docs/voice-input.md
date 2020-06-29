---
title: Spracheingabe
description: Die Spracheingabe ist eine Kern Eingabe für hololens und Windows Mixed Reality-immersive Headsets. Voice kann für Befehle, Diktat, Cortana usw. verwendet werden.
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: GGV, Voice, Cortana, Speech, Input
ms.openlocfilehash: 37364e90aa1d8a7b607a99f4c9b830972f7f80b3
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85441827"
---
# <a name="voice-input"></a>Spracheingabe

![Spracheingabe](images/UX/UX_Hero_VoiceCommand.jpg)

Die Stimme ist eine der wichtigsten Formen der Eingabe für HoloLens. Damit können Sie ein – Hologramm direkt aufrufen, ohne [Handgesten](gaze-and-commit.md#composite-gestures)verwenden zu müssen. Die Spracheingabe kann eine natürliche Art sein, Ihre Absichten zu kommunizieren. Voice eignet sich besonders gut für die Durchführung komplexer Schnittstellen, da Benutzer mit einem Befehl die Möglichkeit haben, die Verwendung von Netz Menüs zu ermöglichen.

Die Spracheingabe wird von [derselben Engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) unterstützt, die Sprache in allen anderen _universellen Windows-apps_unterstützt. Bei hololens funktioniert die Spracherkennung immer in der in den Einstellungen konfigurierten Windows-Anzeige Sprache. 

<br>

## <a name="voice-and-gaze"></a>Sprach-und Blick

Wenn Sprachbefehle verwendet werden, wird der Cursor (Head-oder Eye) in der Regel als Ziel Ziel Mechanismus verwendet, egal ob mit einem Cursor ("Select") oder implizit, um Ihren Befehl an eine Anwendung zu leiten, die Sie sich ansehen. Hierfür ist es möglicherweise gar nicht erforderlich, einen Cursor Cursor anzuzeigen _("Weitere_Informationen" anzeigen). Natürlich benötigen einige Sprachbefehle überhaupt kein Ziel, z. b. "Gehe zu Start" oder "Hey Cortana".

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


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
        <td>Spracheingabe</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (mit Mikrofon)</td>
    </tr>
</table>

## <a name="the-select-command"></a>Der Befehl "Select"

**HoloLens (1. Generation)**

Auch wenn Sie Ihrer APP keine Sprachunterstützung hinzufügen, können Ihre Benutzer holograms aktivieren, indem Sie einfach den System Sprachbefehl "Select" sagen. Dies verhält sich wie eine [Luft](gaze-and-commit.md#composite-gestures) Abzweigung in hololens, das Drücken der Schaltfläche "auswählen" auf dem [hololens-Clicker](https://docs.microsoft.com/hololens/hololens1-clicker)oder das Drücken des Auslösers auf einem [Windows Mixed Reality Motion Controller](motion-controllers.md). Sie werden einen Sound hören und sehen, dass eine QuickInfo mit "Select" als Bestätigung angezeigt wird. "Select" wird durch einen Algorithmus für die Erkennung eines niedrigen Leistungs Worts aktiviert, sodass Sie jederzeit mit minimalen Auswirkungen auf die Akku Lebensdauer jederzeit angezeigt werden können. Dies gilt auch für Ihre Hände.

<br>

---

:::row:::
    :::column:::
        **HoloLens 2**<br><br>
        Um den "Select"-Befehl "Stimme" in hololens 2 zu verwenden, müssen Sie zuerst den Cursor Cursor zur Verwendung als Zeiger einrichten. Der Befehl zur Eingabe ist leicht zu merken, einfach "Select".<br><br>
        Um den Modus zu beenden, verwenden Sie einfach wieder die Hände, entweder durch Tippen auf eine Maustaste, eine Schaltfläche mit Ihren Fingern oder mithilfe der System Bewegung.<br>
        <br>
        *Bild: "Select", um den Voice-Befehl für die Auswahl zu verwenden*
    :::column-end:::
        :::column:::
       ![Ein Benutzer kann "Select" (auswählen) verwenden, um den Voice-Befehl für eine Auswahl zu verwenden.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="hey-cortana"></a>Hallo, Cortana

Sie können auch "Hey Cortana" sagen, um Cortana jederzeit zu erhalten. Sie müssen nicht warten, bis Sie angezeigt wird, um Ihre Frage zu stellen oder eine Anweisung zu geben, z. b. "Hey Cortana, was ist das Wetter?". als einzelner Satz. Weitere Informationen zu Cortana und den Möglichkeiten, die Sie tun können, finden Sie einfach! Sagen Sie: "Hey Cortana, was kann ich sagen?" und Sie werden eine Liste der funktionierenden und vorgeschlagenen Befehle abrufen. Wenn Sie sich bereits in der Cortana-App befinden, können Sie auch auf die **?** Symbol auf der Rand Leiste, um das gleiche Menü zu ziehen.

**Hololens-spezifische Befehle**
* Was kann ich sagen?
* "Gehe zu Start"-anstelle von " [Bloom](system-gesture.md#bloom) ", um zum [Startmenü](navigating-the-windows-mixed-reality-home.md#start-menu) zu gelangen
* "Starten <app> "
* " <app> Hier verschieben"
* "Bild nehmen"
* "Aufzeichnung starten"
* "Aufzeichnung anhalten"
* "Hand Strahl anzeigen"
* "Hand Strahl ausblenden"
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



<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a>"Weitere Informationen"<br>
        Hololens hat eine "See it"-Modell für die Spracheingabe, bei der Bezeichnungen auf Schaltflächen den Benutzern mitteilen, welche Sprachbefehle Sie auch sagen können. Wenn Sie z. b. ein App-Fenster in hololens (1st Gen) betrachten, kann ein Benutzer den Befehl "anpassen" anzeigen, der in der APP-Leiste angezeigt wird, um die Position der APP auf der ganzen Welt anzupassen.<br>
        <br>
        *Image: ein Benutzer kann den Befehl "anpassen" anzeigen, der in der APP-Leiste angezeigt wird, um die Position der APP anzupassen.*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
        ![Wenn Sie ein App-Fenster oder Hologram betrachten, kann ein Benutzer den Befehl "anpassen" anzeigen, der in der APP-Leiste angezeigt wird, um die Position der APP auf der ganzen Welt anzupassen.](images/microphone-600px.png)<br>
    :::column-end:::
:::row-end:::


<br>



:::row:::
    :::column:::
        Wenn apps diese Regel befolgen, können Benutzer leicht erkennen, was zum Steuern des Systems zu sagen ist. Um dies zu verstärken, wird bei der Betrachtung einer Schaltfläche in hololens (1st Gen) eine QuickInfo angezeigt, die nach einer Sekunde angezeigt wird, wenn die Schaltfläche sprach fähig ist, und zeigt den Befehl an, um zu sprechen, um Sie zu "drücken". Um voicemailtipps in hololens 2 anzuzeigen, zeigen Sie den sprach Cursor an, indem Sie "Select" oder "Was kann ich sagen" (siehe Abbildung). <br>
        <br>
        *Bild: "sehen Sie, dass die Befehle unter den Schaltflächen angezeigt werden.*
    :::column-end:::
        :::column:::
       ![Sehen Sie, dass die Befehle unter den Schaltflächen angezeigt werden.](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="voice-commands-for-fast-hologram-manipulation"></a>Sprachbefehle für schnelle – Hologramm-Bearbeitung

Es gibt eine Reihe von Sprachbefehlen, die Sie bei der Betrachtung eines holograms zum schnellen Ausführen von Bearbeitungsaufgaben sagen können. Diese Sprachbefehle funktionieren sowohl bei App-Fenstern als auch bei 3D-Objekten, die Sie in der Welt abgelegt haben.

**Hologram-Bearbeitungsbefehle**
* Gesicht
* Größer | Verbessern
* Geringeren

Auf hololens 2 können Sie auch natürlichere Interaktionen in Kombination mit Eye-Blick erstellen, die implizit Kontextinformationen über das, auf das Sie verweisen, bereitstellt. Sie könnten z. b. einfach ein Hologramm betrachten und dann auf "put _this_" ("put this") und _dann überprüfen_, wo Sie es platzieren möchten.
Oder Sie können sich einen Holographic-Teil auf einem komplexen Computer ansehen und sagen: "Weitere Informationen zu _diesem_".



## <a name="discovering-voice-commands"></a>Erkennen von Sprachbefehlen

Einige Befehle, wie z. b. die Befehle für die schnelle Bearbeitung, können ausgeblendet werden. Um zu erfahren, welche Befehle Sie verwenden können, schauen Sie sich das Objekt an, und sagen Sie: "Was kann ich sagen?". Eine Liste möglicher Befehle wird angezeigt. Sie können auch den Cursor Cursor verwenden, um die voicemailtipps für die einzelnen Schaltflächen anzuzeigen. 

Wenn Sie eine vollständige Liste erhalten möchten, sagen Sie einfach "alle Befehle anzeigen". 


## <a name="dictation"></a>Diktieren

Anstatt eine Typisierung mit [Luft](gaze-and-commit.md#composite-gestures)Eingaben durchführen zu können, kann es effizienter sein, Text in eine APP einzugeben. Dadurch kann die Eingabe erheblich beschleunigt werden, sodass der Benutzer weniger Aufwand hat.

![Sprach Diktat beginnt mit der Schaltfläche Mikrofon](images/micbuttonfordictation.png)<br>
*Sprach Diktat beginnt mit der Schaltfläche Mikrofon auf der Tastatur*

Jedes Mal, wenn die holografische Tastatur aktiv ist, können Sie in den Diktat Modus wechseln, anstatt einzugeben. Wählen Sie das Mikrofon auf der Seite des Texteingabe Felds aus, um loszulegen.


## <a name="adding-voice-commands-to-your-app"></a>Hinzufügen von Sprachbefehlen zu Ihrer APP

Erwägen Sie, Sprachbefehle zu jeder von Ihnen erstellten Umgebung hinzuzufügen. Die Spracheingabe ist eine leistungsstarke und komfortable Möglichkeit zur Steuerung von System und Apps. Da Benutzer mit einer Vielzahl von Dialekten und Akzenten sprechen, stellt die richtige Auswahl der Schlüsselwörter für die Spracherkennung sicher, dass die Befehle Ihrer Benutzer eindeutig interpretiert werden.

### <a name="best-practices"></a>Bewährte Methoden

Nachfolgend finden Sie einige Methoden aufgeführt, die eine reibungslose Spracherkennung ermöglichen.
* **Präzise Befehle verwenden**: Wählen Sie nach Möglichkeit Schlüsselwörter mit zwei oder mehr Silben aus. Einsilbige Wörter neigen dazu, unterschiedliche Vokallaute zu verwenden, wenn sie von Personen mit unterschiedlichen Akzenten gesprochen werden. Beispiel: "Video abspielen" ist besser als "das aktuell ausgewählte Video abspielen"
* **Verwenden eines einfachen Vokabulars** -Beispiel: "Show Note" ist besser als "Placard anzeigen"
* **Sicherstellen, dass Befehle nicht destruktiv sind**: Stellen Sie sicher, dass alle Aktionen, die von einem Spracherkennungsbefehl ausgeführt werden können, nicht destruktiv sind und leicht rückgängig gemacht werden können, falls eine andere Person, die in der Nähe des Benutzers spricht, versehentlich einen Befehl auslöst.
* **Ähnlich klingende Befehle vermeiden**: Vermeiden Sie es, mehrere Spracherkennungsbefehle zu registrieren, die sehr ähnlich klingen. Beispiel: "mehr anzeigen" und "Store anzeigen" kann sehr ähnlich klingen.
* **Registrierung der App aufheben, wenn sie nicht verwendet wird**: Wenn sich Ihre Anwendung nicht in einem Zustand befindet, in dem ein bestimmter Sprachbefehl gültig ist, sollten Sie die Registrierung der App aufheben, damit andere Befehle nicht mit diesem verwechselt werden.
* **Mit verschiedenen Akzenten testen**: Testen Sie Ihre App mit Benutzern, die unterschiedliche Akzente verwenden.
* **Konsistenz von Sprachbefehlen beibehalten**: Wenn „Zurück“ zur vorherigen Seite wechselt, übernehmen Sie dieses Verhalten in Ihren Anwendungen.
* **Verwendung von Systembefehlen vermeiden**: Die folgenden Sprachbefehle sind für das System reserviert. Diese sollten nicht von Anwendungen verwendet werden.
   * „Hey Cortana“
   * „Auswählen“
   * "Gehe zu Start"

### <a name="advantages-of-voice-input"></a>Vorteile von Spracheingaben

Die Spracheingabe ist eine natürliche Art, unsere Absichten zu kommunizieren. Voice ist besonders gut für Schnittstellen **Traversale** geeignet, da Sie Benutzern dabei helfen kann, mehrere Schritte einer Schnittstelle zu durchlaufen (ein Benutzer könnte bei der Betrachtung einer Webseite auf die Schaltfläche "zurück" klicken, anstatt auf die Schaltfläche "zurück" in der APP zu gelangen). Diese kleine Zeitersparnis wirkt sich **negativ** auf die Wahrnehmung der Benutzerfreundlichkeit durch den Benutzer aus und bietet Ihnen einen kleinen Wert für die Super Arbeit. Die Spracheingabe ist auch eine bequeme Eingabemethode, wenn unsere Arme nicht frei sind oder wir **mehrere Aufgaben gleichzeitig** erledigen. Auf Geräten, auf denen die Eingabe auf einer Tastatur schwierig ist, kann die **sprach Diktat** -Methode eine effiziente Alternative zum Eingeben von Text sein. In einigen Fällen, in denen der **Genauigkeits Bereich** für den Blick und die Bewegung eingeschränkt ist, kann Voice Ihnen helfen, die Absicht des Benutzers zu unterscheiden. 

**Vorteile der Spracheingabe für den Benutzer**
* Verkürzt den Zeitaufwand – das Endziel sollte effizienter erreicht werden.
* Minimiert den Aufwand – Aufgaben sollten flüssiger und müheloser verlaufen.
* Reduziert die kognitive Belastung – sie ist intuitiv, leicht zu erlernen und zu merken.
* Sie ist sozialverträglich – sie sollte sich in Bezug auf das Verhalten in die gesellschaftlichen Normen einfügen.
* Sie stellt eine Routine dar – die Spracheingabe kann leicht zu einem gewohnheitsmäßigen Verhalten werden.

### <a name="challenges-for-voice-input"></a>Herausforderungen bei der Spracheingabe

Obwohl die Spracheingabe für viele verschiedene Anwendungen hervorragend ist, stellt Sie auch mehrere Herausforderungen dar. Wenn Sie sowohl die Vorteile als auch die Herausforderungen von Spracheingaben verstanden haben, können App-Entwickler intelligentere Entscheidungen treffen, wie und wann Spracheingaben verwendet werden sollen und wie Sie Ihre Benutzer gut gestalten können.

**Spracheingabe für kontinuierliches Eingabe Steuer** Element Eine differenzierte Steuerung ist eine davon. Beispielsweise kann ein Benutzer sein Volume in der Musik-App ändern. Sie kann einfach "lauter" sagen, aber es ist nicht klar, wie viel lauter das System das Volume machen soll. Der Benutzer könnte sagen: "machen Sie es etwas lauter", aber "ein wenig" ist schwierig zu quantifizieren. Das Verschieben oder Skalieren von holograms mit Stimme ist ähnlich schwierig. 

**Zuverlässigkeit der Spracheingabe Erkennung** Obwohl Spracheingabe Systeme besser und besser werden, werden Sie möglicherweise fälschlicherweise einen Sprachbefehl hören und interpretieren.
Der Schlüssel besteht darin, dieser Herausforderung in Ihrer Anwendung zu begegnen, indem er dem Benutzer Feedback zur Verfügung stellt, wenn das System lauscht, und was das System verstanden hat, um Klarheit über potenzielle Probleme bei der ordnungsgemäßen Verwendung des Benutzers zu schaffen  

**Spracheingabe in freigegebenen Leerzeichen** Die Stimme ist möglicherweise nicht in den Bereichen, die Sie für andere Personen freigeben, akzeptabel.
Hier sind einige Beispiele:
* Der Benutzer möchte möglicherweise keine anderen Personen stören (z. b. in einer stillen Bibliothek oder einem freigegebenen Büro).
* Benutzer sind vielleicht nicht in der Öffentlichkeit,
* Ein Benutzer ist möglicherweise unbequem, wenn er eine persönliche oder vertrauliche Nachricht (einschließlich Kenn Wörtern) einhört, während andere Benutzer lauschen.

**Spracheingabe von eindeutigen oder unbekannten Wörtern** Probleme bei der Spracheingabe werden auch angezeigt, wenn Benutzer Wörter, die möglicherweise dem System unbekannt sind, wie z. b. Spitznamen, bestimmte slang-Wörter oder Abkürzungen, eingeben. 

**Erlernen von Sprachbefehlen** Das ultimative Ziel ist es, sich auf natürliche Weise mit Ihrem System zu Konversation, häufig verlassen sich apps jedoch auf bestimmte vordefinierte Sprachbefehle.
Eine Herausforderung, die mit einem großen Satz von Sprachbefehlen verknüpft ist, besteht darin, Sie zu unterstützen, ohne den Benutzer zu überlasten und den Benutzern zu helfen, Sie beizubehalten. 

<br>

---

### <a name="voice-feedback-states"></a>Statusangaben für Spracherkennungsfeedback

Wenn die Spracherkennung richtig angewendet wird, versteht der Benutzer, **was er sagen kann und er erhält ein eindeutiges Feedback**, das das System **ihn richtig verstanden hat**. Diese beiden Signale geben dem Benutzer das Gefühl, dass er die Spracherkennung als primäre Eingabemethode verwenden kann. Nachfolgend ist in einem Diagramm dargestellt, was mit dem Cursor geschieht, wenn die Spracheingabe erkannt wird und wie dies dem Benutzer vermittelt wird.


:::row:::
    :::column:::
       ![1. regulärer Cursor Zustand](images/voicefeedbackstates-regular.jpg)<br>
       **1. regulärer Cursor Zustand**<br>
    :::column-end:::
    :::column:::
       ![2. kommuniziert Feedback und verschwindet dann](images/voicefeedbackstates-voice.jpg)<br>
        **2. kommuniziert Feedback und verschwindet dann**<br>
    :::column-end:::
    :::column:::
       ![€. Regulärer Cursor Zustand](images/voicefeedbackstates-regular.jpg)<br>
       **3. zurück zum regulären Cursor Zustand**<br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a>Wichtige Informationen zur Spracherkennung in Mixed Reality
* Sagen Sie **„Auswählen“**, während Sie eine Schaltfläche anvisieren (Sie können dies überall verwenden, um auf eine Schaltfläche zu klicken).
* Sie können in einigen Apps den **Bezeichnungsnamen einer Schaltfläche auf der App-Leiste** sagen, um eine Aktion auszuführen. Beim Betrachten einer App kann ein Benutzer z. B. den Befehl „Entfernen“ sagen, um die App aus der Umgebung zu entfernen (das spart Zeit, da die App nicht mit der Hand angeklickt werden muss).
* Sie können initiieren, dass Cortana zuhört, indem Sie **„Hey Cortana“** sagen. Sie können ihr Fragen stellen („Hey Cortana, wie hoch ist der Eiffelturm“), sie zum Öffnen einer App auffordern („Hey Cortana, öffne Netflix“) oder ihr sagen, sie soll das Startmenü aufrufen („Hey Cortana, öffne das Startmenü“) und vieles mehr.

## <a name="common-questions-and-concerns-users-have-about-voice"></a>Häufig gestellte Fragen und Bedenken von Benutzern zur Spracheingabe
* Was kann ich sagen?
* Woher weiß ich, ob das System mich richtig verstanden hat?
   * Das System versteht meine Sprachbefehle immer wieder falsch.
   * Es reagiert nicht, wenn ich einen Sprachbefehl erteile.
* Es reagiert falsch, wenn ich einen Sprachbefehl erteile.
* Wie richte ich meine Stimme auf eine bestimmte App oder einen bestimmten App-Befehl aus?
* Kann ich Objekte per Sprachbefehl aus dem holografischen Rahmen der HoloLens bewegen?

## <a name="communication"></a>Kommunikation

Für Anwendungen, die die von hololens bereitgestellten angepassten audioeingabeverarbeitungs-Optionen nutzen möchten, ist es wichtig, die verschiedenen [audiostreamkategorien](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) zu verstehen, die Ihre APP nutzen kann. Windows 10 unterstützt mehrere verschiedene streamingkategorien, und hololens nutzt drei dieser Möglichkeiten, um die benutzerdefinierte Verarbeitung zu ermöglichen, um die Qualität der Mikrofon Audioqualität zu optimieren, die auf Sprache, Kommunikation und andere zugeschnitten ist. diese kann für Umgebungs Umgebungs audioerfassungs Szenarien (d.h. "Camcorder") verwendet werden.
* Die AudioCategory_Communications Stream-Kategorie wird für Anruf Qualität und-Erzähl Szenarien angepasst und stellt dem Client einen 16-Bit-Mono-Mono-Audiostream der Stimme des Benutzers zur Verfügung.
* Die AudioCategory_Speech Stream-Kategorie ist für die Sprach-Engine hololens (Windows) angepasst und bietet einen 16-Bit-Mono-Mono-Datenstrom der Stimme des Benutzers. Diese Kategorie kann bei Bedarf von Sprachmodulen von Drittanbietern verwendet werden.
* Die AudioCategory_Other Stream-Kategorie ist für die Audioaufzeichnung der Umgebungsumgebung angepasst und stellt dem Client einen Stereo-Audiostream mit 48 kHz 24 Bit bereit.

Die gesamte Audioverarbeitung ist Hardware beschleunigt. Dies bedeutet, dass die Features viel weniger Leistung als bei der Verarbeitung der hololens-CPU benötigen. Vermeiden Sie die Ausführung einer anderen audioeingabeverarbeitung auf der CPU, um die Akku Lebensdauer zu maximieren und die integrierte, offloaded audioeingabeverarbeitung zu nutzen.

## <a name="languages"></a>Languages

Hololens 2 [unterstützt mehrere Sprachen](https://docs.microsoft.com/hololens/hololens2-language-support). Beachten Sie, dass Sprachbefehle immer in der Anzeige Sprache des Systems ausgeführt werden, auch wenn mehrere Tastaturen installiert sind oder wenn apps versuchen, eine Spracherkennung in einer anderen Sprache zu erstellen.

## <a name="troubleshooting"></a>Problembehandlung

Wenn Sie Probleme bei der Verwendung von "Select" und "Hey Cortana" haben, versuchen Sie, zu einem ruhigeren Bereich zu wechseln, die Ursache für Rauschen zu machen oder lauter zu sprechen. Zu diesem Zeitpunkt wird die Spracherkennung in hololens speziell für systemeigene Sprecher von USA Englisch optimiert und optimiert.

Für Windows Mixed Reality Developer Edition, Version 2017, funktioniert die audioendpunkt-Verwaltungs Logik problemlos (immer), nachdem Sie sich nach der anfänglichen HMD-Verbindung beim PC-Desktop abgemeldet hat. Vor dem ersten Abmelden/in-Ereignis nach dem Durchlaufen von WMR OOBE könnte der Benutzer verschiedene Probleme mit der Audiofunktionalität aufweisen, von denen kein audiowechsel bis hin zu keinem audiowechsel stattfindet, je nachdem, wie das System vor dem ersten Herstellen einer Verbindung mit dem HMD eingerichtet wurde.

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a>Spracheingabe in mrtk (Mixed Reality Toolkit) für Unity
Mit **[mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** können Sie den Voice-Befehl problemlos für beliebige Objekte zuweisen. Verwenden Sie das **Spracheingabe Profil** von mrtk, um Ihre Schlüsselwörter zu definieren. Indem Sie das Skript " **speechinputhandler** " zuweisen, können Sie festlegen, dass jedes Objekt auf die im Spracheingabe Profil definierten Schlüsselwörter antwortet. Der speechinputhandler bietet auch eine Bezeichnung für die sprach Bestätigung, um das Vertrauen des Benutzers zu verbessern.

* [Befehl "mrtk-Voice"](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html)


---

## <a name="see-also"></a>Siehe auch
* [Anvisieren und Ausführen](gaze-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [MR-Eingabe 212: Sprache](holograms-212.md)
* [Spracheingabe in DirectX](voice-input-in-directx.md)
* [Spracheingabe in Unity](voice-input-in-unity.md)
