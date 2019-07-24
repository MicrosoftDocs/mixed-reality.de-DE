---
title: Räumlicher Ton-220-Ton
description: Befolgen Sie diese Codierungs Exemplarische Vorgehensweise mit Unity, Visual Studio und hololens, um die Details der räumlichen audiokonzepte zu erlernen.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, Tutorial, räumlicher Sound
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526911"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.

<br>

# <a name="mr-spatial-220-spatial-sound"></a>Räumliche Daten 220: Raumklang

[Räumlicher Sound](spatial-sound.md) atmet Leben in holograms und bietet Ihnen die Präsenz in unserer Welt. Holograms bestehen aus Licht und Ton, und wenn Sie Ihre Hologramme nicht vergessen, kann räumlicher Sound Ihnen helfen, Sie zu finden. Der räumliche Sound ist nicht mit dem typischen Sound vergleichbar, den Sie im Radio hören würden, es handelt sich um Sound, der in 3D-Raum positioniert ist. Mit räumlichem Sound können Sie holograms so gestalten, wie Sie sich hinter ihnen befinden, oder auch auf Ihrem Kopf! In diesem Kurs werden Sie wie folgt vorgehen:

* Konfigurieren Sie Ihre Entwicklungsumgebung für die Verwendung von Microsoft Spatial Sound.
* Verwenden Sie räumliche Töne, um Interaktionen zu verbessern.
* Verwenden Sie räumliche Sounds in Verbindung mit räumlicher Zuordnung.
* Informieren Sie sich über die bewährten Vorgehensweisen zum Entwerfen und mischen
* Verwenden Sie Sound, um besondere Effekte zu verbessern und den Benutzer in die gemischte Realität zu bringen.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>Räumliche Daten 220: Raumklang</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Bevor Sie beginnen

### <a name="prerequisites"></a>Vorraussetzungen

* Ein Windows 10-PC, der mit den richtigen [installierten Tools](install-the-tools.md)konfiguriert ist.
* Einige Grund C# Legende Programmiermöglichkeiten.
* Sie sollten die [Grundlagen von 101](holograms-101.md)abgeschlossen haben.
* Ein hololens-Gerät, das [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode)ist.

### <a name="project-files"></a>Projektdateien

* Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) , die für das Projekt erforderlich sind. Erfordert Unity 2017,2 oder höher.
  * Wenn Sie weiterhin Unity 5,6-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip). Diese Version ist möglicherweise nicht mehr auf dem neuesten Stand.
  * Wenn Sie weiterhin Unity 5,5-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip). Diese Version ist möglicherweise nicht mehr auf dem neuesten Stand.
  * Wenn Sie weiterhin Unity 5,4-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip). Diese Version ist möglicherweise nicht mehr auf dem neuesten Stand.
* Deinstallieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht zugänglichen Speicherort.

>[!NOTE]
>Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).

### <a name="errata-and-notes"></a>Errata und Notizen

* "Enable nur eigenen Code" muss in Visual Studio unter "Extras-> Optionen" deaktiviert*werden (>* Debuggen, um Breakpoints im Code zu erreichen.

## <a name="chapter-1---unity-setup"></a>Kapitel 1: Einrichtung von Unity

### <a name="objectives"></a>Ziele

* Ändern Sie die Sound Konfiguration von Unity, sodass Sie Microsoft Spatial Sound verwendet.
* Hinzufügen eines 3D-Sounds zu einem Objekt in Unity.

### <a name="instructions"></a>Anweisungen

* Starten Sie Unity.
* Wählen Sie **Öffnen**aus.
* Navigieren Sie zu Ihrem Desktop, und suchen Sie den Ordner, den Sie zuvor nicht archiviert haben.
* Klicken Sie auf den Ordner **starting\decibel** , und klicken Sie dann auf die Schaltfläche **Ordner auswählen** .
* Warten Sie, bis das Projekt in Unity geladen wurde.
* Öffnen Sie im **Projekt** Panel **scenes\decibel.unity**.
* Erweitern Sie im Bereich **Hierarchie** den Knoten **hologrammcollection** , und wählen Sie **P0LY**aus.
* Erweitern Sie im Inspektor den Eintrag **audiosource** , und beachten Sie, dass kein **spatialize** -Kontrollkästchen vorhanden ist.

Standardmäßig lädt Unity kein spatializer-Plug-in. Mit den folgenden Schritten wird räumlicher Sound im Projekt aktiviert.

* Wechseln Sie im oberen Menü von Unity zu **Edit > Project Settings > Audiodatei**.
* Suchen Sie nach der Dropdown Liste **spatializer Plugin** , und wählen Sie **MS HRTF spatializer**aus.
* Wählen Sie im Bereich **Hierarchie** die Option **hologramcollection > P0LY**aus.
* Suchen Sie im **Inspektor** -Panel die Komponente **Audioquelle** .
* Aktivieren Sie das Kontrollkästchen **spatialize** .
* Ziehen Sie  den Schieberegler räumlichkeits Weise in **3D**, oder geben Sie 1 in das Bearbeitungsfeld **ein** .

Wir erstellen nun das Projekt in Unity und konfigurieren die Projekt Mappe in Visual Studio.

1. Wählen Sie in Unity **Datei >** Buildeinstellungen aus.
2. Klicken Sie auf **offene Szenen hinzufügen** , um die Szene hinzuzufügen.
3. Wählen Sie in der Liste **Plattform** **universelle Windows-Plattform** aus, und klicken Sie auf **Plattform wechseln**.
4. Wenn Sie speziell für hololens entwickeln, legen Sie **Zielgerät** auf **hololens**fest. Andernfalls sollten Sie es auf **jedem Gerät**belassen.
5. Stellen  Sie sicher, dass der Buildtyp auf **D3D** und das **SDK** auf **Latest installiert** festgelegt ist (was SDK 16299 oder höher sein sollte).
6. Klicken Sie auf **Erstellen**.
7. Erstellen Sie einen **neuen Ordner** mit dem Namen "App".
8. Klicken Sie einfach auf den **App** -Ordner.
9. Drücken **Sie Ordner auswählen**.

Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.

1. Öffnen Sie den **App** -Ordner.
2. Öffnen Sie die Projekt Mappe **Decibel Visual Studio**.

Bei der Bereitstellung in hololens:

1. Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x86**.
2. Klicken Sie auf den Dropdown Pfeil neben der Schaltfläche lokaler Computer, und wählen Sie **Remote Computer**aus.
3. Geben Sie **die IP-Adresse des hololens-Geräts** ein, und legen Sie den Authentifizierungsmodus auf **Universal (unverschlüsseltes Protokoll)** Klicken Sie auf **Auswählen**. Wenn Sie die IP-Adresse Ihres Geräts nicht kennen, suchen Sie unter **Einstellungen > Netzwerk & Internet > Erweiterte Optionen**.
4. Klicken Sie in der oberen Menüleiste auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**. Wenn Sie die Bereitstellung auf Ihrem Gerät zum ersten Mal durchführt, müssen Sie [es mit Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen)koppeln.

Bei der Bereitstellung auf einem immersiven Headset:

1. Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x64**.
2. Stellen Sie sicher, dass das Bereitstellungs Ziel auf **lokaler Computer**festgelegt ist.
3. Klicken Sie in der oberen Menüleiste auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.

## <a name="chapter-2---spatial-sound-and-interaction"></a>Kapitel 2: räumlicher Sound und Interaktion

### <a name="objectives"></a>Ziele

* Verbessern Sie das – Hologramm-Realismus mithilfe von Sound.
* Leiten Sie den Benutzer Blick mithilfe von Sound weiter.
* Stellen Sie Gesten Feedback mit Sound bereit.

### <a name="part-1---enhancing-realism"></a>Teil 1: verbessern des Realismus

#### <a name="key-concepts"></a>Wichtige Konzepte

* Räumalisieren Sie – Hologramm-Sounds.
* Audioquellen sollten an einem geeigneten Speicherort auf dem Hologram abgelegt werden.

Der richtige Speicherort für den Sound hängt von dem Hologram ab. Wenn das – Hologramm z. b. von einem Menschen ist, sollte sich die Audioquelle nahe dem Mund und nicht der Fußzeile befinden.

#### <a name="instructions"></a>Anweisungen

Die folgenden Anweisungen fügen einen räumlichen Sound an ein Hologramm an.

* Erweitern Sie im Bereich **Hierarchie** den Knoten **hologrammcollection** , und wählen Sie **P0LY**aus.
* Klicken Sie im Bereich **Inspector** in der **audiosource**auf den Kreis neben **Audioclip** , und wählen Sie im Popup Fenster **polyhover** aus.
* Klicken Sie auf den Kreis neben **Ausgabe** , und wählen Sie im Popup Fenster **soundeffects** aus.

Project Decibel verwendet eine Unity- **Audiomixer** -Komponente, um das Anpassen von Sound Ebenen für Gruppen von Sounds zu ermöglichen. Durch das Gruppieren von Sounds auf diese Weise kann das Gesamt Volume angepasst werden, während die relative Menge der einzelnen Sounds beibehalten wird.

* Erweitern Sie in der **audiosource** **3D Sound Settings**.
* Legen Sie die **Doppler-Ebene** auf **0**fest.

Durch das Festlegen von Doppler-Level auf NULL werden die Änderungen in der durch Bewegung (entweder im – Hologramm oder im Benutzer) verursachten Tonhöhe deaktiviert. Ein klassisches Beispiel für Doppler ist ein schnell beweglicher Wagen. Wenn sich das Auto auf einen stationären Listener nähert, steigt die Tonhöhe der Engine. Wenn Sie den Listener übergibt, wird die-Tonhöhe mit Distance gesenkt.

### <a name="part-2---directing-the-users-gaze"></a>Teil 2: leiten des Benutzer Blicks

#### <a name="key-concepts"></a>Wichtige Konzepte

* Verwenden Sie Sound, um auf wichtige holograms aufzurufen.
* Die Ohren helfen Ihnen, den Augenblick zu lenken.
* Das Gehirn hat einige Erwartungen gelernt.

Ein Beispiel für die gewonnenen Erwartungen ist, dass die Vögel in der Regel über den Köpfen der Menschen sind. Wenn ein Benutzer ein vogelton hört, besteht die anfängliche Reaktion darin, nach oben zu suchen. Das Platzieren eines Vogels unterhalb des Benutzers kann dazu führen, dass er mit der richtigen Richtung des Sounds zurechtkommt, aber das – Hologramm nicht finden kann, je nachdem, dass er gesucht werden muss.

#### <a name="instructions"></a>Anweisungen

Mithilfe der folgenden Anweisungen können Sie P0LY hinter Ihnen verbergen, damit Sie den Sound verwenden können, um das Hologram zu suchen.

* Wählen Sie im Bereich **Hierarchie** die Option **Manager**aus.
* Suchen Sie im **Inspektor** -Panel den **Spracheingabe Handler**.
* Erweitern Sie im **Spracheingabe Handler**den Bereich **Gehe ausblenden**.
* Ändern Sie **keine Funktion** in **polyactions. gohide**.

![Schlüsselwort Ausblenden ausblenden](images/gohide.png)

### <a name="part-3---gesture-feedback"></a>Teil 3: Gesten Feedback

#### <a name="key-concepts"></a>Wichtige Konzepte

* Bereitstellen von positiver Gesten Bestätigung mit Sound
* Bewegen Sie die Benutzer übermäßig lauter Sounds nicht auf die gleiche Weise
* Feine Sounds funktionieren am besten

#### <a name="instructions"></a>Anweisungen

* Erweitern Sie im Bereich **Hierarchie** den Knoten **hologrammcollection**.
* Erweitern Sie **energyhub** , und wählen Sie **Basis**aus.
* Klicken Sie im **Inspektor** -Panel auf **Komponente hinzufügen** , und fügen Sie **Gesten Sound Handler**hinzu.
* Klicken Sie in **Gesten Sound Handler**auf den Kreis neben **Navigation Started Clip** und **Navigation aktualisierte Clip** , und wählen Sie im Popup Fenster für beide den Bereich **rotateclick** aus.
* Doppelklicken Sie auf "gesturesound Handler", um in Visual Studio zu laden.

Der Gesten Sound Handler führt die folgenden Aufgaben aus:

* Erstellen und konfigurieren Sie eine **audiosource**.
* Platzieren Sie die **audiosource** an der Position des entsprechenden **gameobject**.
* Gibt den **Audioclip** wieder, der mit der Geste verknüpft ist.

#### <a name="build-and-deploy"></a>Erstellen und bereitstellen

1. Wählen Sie in Unity **Datei >** Buildeinstellungen aus.
2. Klicken Sie auf **Erstellen**.
3. Klicken Sie einfach auf den **App** -Ordner.
4. Drücken **Sie Ordner auswählen**.

Überprüfen Sie, ob die Symbolleiste "Release", "x86", "x64" und "Remote Gerät" heißt. Wenn dies nicht der Fall ist, ist dies die Codierungs Instanz von Visual Studio. Möglicherweise müssen Sie die Projekt Mappe aus dem App-Ordner erneut öffnen.

* Wenn Sie dazu aufgefordert werden, laden Sie die Projektdateien erneut
* Stellen Sie wie zuvor über Visual Studio bereit.

Nachdem die Anwendung bereitgestellt wurde:

* Beobachten Sie, wie sich der Sound bei der Umstellung auf P0LY ändert.
* Sagen Sie *"go hide" (ausblenden* ), um P0LY zu einem Speicherort hinter Ihnen zu wechseln. Suchen Sie nach dem Sound.
* Schauen Sie sich die Basis des Energy Hubs an. Tippen und ziehen Sie nach links oder rechts, um das – Hologramm zu drehen, und sehen Sie, wie der Klick Sound die Geste bestätigt.

Hinweis: Ein Text Panel wird zusammen mit Ihnen angezeigt. Diese werden die verfügbaren Sprachbefehle enthalten, die Sie in diesem Kurs verwenden können.

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a>Kapitel 3: räumliche und räumliche Zuordnung

### <a name="objectives"></a>Ziele

* Bestätigen Sie die Interaktion zwischen holograms und der realen Welt mit Sound.
* Verwenden Sie den Sound mit der physischen Welt.

### <a name="part-1---physical-world-interaction"></a>Teil 1-physische Welt Interaktion

#### <a name="key-concepts"></a>Wichtige Konzepte

* Physische Objekte machen im Allgemeinen einen Sound, wenn Sie auf eine Oberfläche oder ein anderes Objekt stoßen.
* Sounds sollte Kontext freundlich sein.

Beispielsweise sollte das Festlegen eines Cup für eine Tabelle einen ruhigeren Sound als das Löschen eines Boulders auf einem Metal-Gerät machen.

#### <a name="instructions"></a>Anweisungen

* Erweitern Sie im Bereich **Hierarchie** den Knoten **hologrammcollection**.
* Erweitern Sie **energyhub**, und wählen Sie **Basis**aus.
* Klicken Sie im **Inspektor** -Panel auf **Komponente hinzufügen** , und fügen Sie **mit Sound und Action Tap**hinzu.
* **Tippen Sie auf, um mit Sound und Action zu platzieren**:
  * Aktivieren Sie **übergeordnetes Element bei tippen**.
  * Legen Sie **Platzierungs Sound** auf **platzieren**fest.
  * Legen Sie **Pickup Sound** auf **Pickup**fest.
  * Drücken Sie die Taste + unten rechts unter sowohl **bei der** Aufnahme-als auch bei der **Platzierungs Aktion**. Ziehen Sie energyhub aus der Szene in die Felder **None (Object)** .
    * Klicken Sie unter **on Pickup Action**auf **No Function** -> **energyhubbase** -> **resettanimation.**
    * Klicken Sie unter **Platzierungs Aktion**auf **keine Funktion** -> **energyhubbase** -> **onselect**.

![Mit Sound und Action tippen](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a>Teil 2: Sound Okklusion

#### <a name="key-concepts"></a>Wichtige Konzepte

* Sound, wie z. b. Light, können ausgeblendet werden.

Ein klassisches Beispiel ist eine Concert Hall. Wenn ein Listener außerhalb der Halle steht und die Tür geschlossen ist, hört sich die Musik mit gedämpften Tönen an. Es gibt in der Regel auch eine Reduzierung des Volumes. Wenn die Tür geöffnet ist, wird das gesamte Spektrum des Sounds auf dem eigentlichen Volume gehört. Sounds mit hoher Frequenz werden im Allgemeinen mehr als niedrige Frequenzen erfasst.

#### <a name="instructions"></a>Anweisungen

* Erweitern Sie im Bereich **Hierarchie** den Knoten **hologrammcollection** , und wählen Sie **P0LY**aus.
* Klicken Sie im **Inspektor** -Panel auf **Komponente hinzufügen** , und fügen Sie **audioemitter**hinzu.

Die audioemitter-Klasse bietet die folgenden Features:

* Stellt alle Änderungen am Volume der **audiosource**wieder her.
* Führt eine " **Physik. raycastnonzuweisung** " aus der Position des Benutzers in der Richtung des **gameobject** aus, an das der **audioemitter** angefügt ist.

Die raycastnonalloc-Methode wird als Leistungsoptimierung verwendet, um Zuordnungen und die Anzahl der zurückgegebenen Ergebnisse einzuschränken.

* Für jeden gefundenen **iaudioinflutercer** Ruft die **applyeffect** -Methode auf.
* Für jeden vorherigen **iaudioinfludencer** , der nicht mehr gefunden wird, wird die **removeeffect** -Methode aufgerufen.

Beachten Sie, dass audioemitter bei menschlichen Zeitskalen aktualisiert wird, im Gegensatz zu pro Frame. Der Grund hierfür ist, dass Menschen im Allgemeinen nicht schnell genug verschieben, damit die Auswirkungen häufiger als jedes Quartal oder die Hälfte der Sekunde aktualisiert werden müssen. Hologramme, die schnell von einem Speicherort an einen anderen teleportieren, können die Illusion unterbrechen.

* Erweitern Sie im Bereich **Hierarchie** den Knoten **hologrammcollection**.
* Erweitern Sie **energyhub** , und wählen Sie **blobaußen**aus.
* Klicken Sie im **Inspektor** -Panel auf **Komponente hinzufügen** , und fügen Sie **audiookokder**hinzu.
* Legen Sie in **audiookder**den Umstellungs **Frequenz** -Wert auf **1500**fest.

Diese Einstellung schränkt die audiosource-Frequenzen auf 1500 Hz und niedriger ein.

* Legen Sie den **volumedurchlauf** auf **0,9**fest.

Mit dieser Einstellung wird das Volume der audiosource auf die aktuelle Ebene von 90% reduziert.

Der audiookton implementiert iaudioinflutencer für Folgendes:

* Anwenden eines Okklusions Effekts mithilfe eines **audiolowpassfilter** , der an die **audiosource** angefügt wird, die den **audioemitter**kauft.
* Wendet die volumedämpfung auf die audiosource an.
* Deaktiviert den Effekt durch Festlegen einer neutralen Umstellungs Frequenz und Deaktivieren des Filters.

Die als neutral verwendete Häufigkeit ist 22 kHz (22000 Hz). Diese Häufigkeit wurde gewählt, weil Sie über der maximalen maximalen Frequenz liegt, die vom menschlichen Ohr gehört werden kann, sodass keine erkennbaren Auswirkungen auf den Sound entstehen.

* Wählen Sie im Bereich **Hierarchie** die Option **spatialmapping**aus.
* Klicken Sie im **Inspektor** -Panel auf **Komponente hinzufügen** , und fügen Sie **audiookokder**hinzu.
* Legen Sie in **audiookder**den Umstellungs **Frequenz** -Wert auf **750**fest.

Wenn sich mehrere okader im Pfad zwischen dem Benutzer und dem **audioemitter**befinden, wird die niedrigste Frequenz auf den Filter angewendet.

* Legen Sie den **volumedurchlauf** auf **0,75**fest.

Wenn sich mehrere okader im Pfad zwischen dem Benutzer und dem **audioemitter**befinden, wird das Volume weitergeleitet.

* Wählen Sie im Bereich **Hierarchie** die Option **Manager**aus.
* Erweitern Sie im **Inspektor** -Panel den **Spracheingabe Handler**.
* Erweitern Sie im **Spracheingabe Handler den Eintrag** **go-Belastung**.
* Ändern Sie **keine Funktion** in **polyactions. goabgerechnet**.

![Schlüsselwort Gehe zu](images/gocharge.png)

* Erweitern Sie **hier**.
* Ändern Sie **keine Funktion** in **polyactions. ComeBack**.

![Schlüsselwort Komm her](images/comehere.png)

#### <a name="build-and-deploy"></a>Erstellen und bereitstellen

* Erstellen Sie wie zuvor das Projekt in Unity, und stellen Sie es in Visual Studio bereit.

Nachdem die Anwendung bereitgestellt wurde:

* Sagen Sie *"Go-Kosten"* , damit P0LY den Energie-Hub eingeben.

Beachten Sie die Änderung des Sounds. Dies sollte ein wenig leiser werden. Wenn Sie sich in der Lage sind, sich mit einer Wand oder einem anderen Objekt zwischen Ihnen und dem Energie-Hub zu positionieren, sollten Sie aufgrund der Okklusion der realen Welt eine weitere Belastung des Sounds feststellen.

* Sagen *Sie* , dass P0LY den Energie-Hub verlassen und sich vor Ihnen positionieren muss.

Beachten Sie, dass die Sound Okklusion einmal entfernt wird P0LY beendet den Energie-Hub. Wenn Sie immer noch mit der Okklusion hören, wird P0LY möglicherweise von der realen Welt ausgeschlossen. Versuchen Sie, die Umstellung durchführen zu lassen.

### <a name="part-3---room-models"></a>Teile von 3-Raum-Modellen

#### <a name="key-concepts"></a>Wichtige Konzepte

* Die Größe des Speicherplatzes bietet unter-Warteschlangen, die zur Sound Lokalisierung beitragen.
* Raummodelle werden pro**audiosource**festgelegt.
* Das [mixedrealitytoolkit für Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) stellt Code zum Festlegen des raummodells bereit.
* Wählen Sie für gemischte Realität das Raummodell aus, das am besten zu dem realen Raum passt.

Wenn Sie ein virtuelles Reality-Szenario erstellen, wählen Sie das Raummodell aus, das für die virtuelle Umgebung am besten geeignet ist.

## <a name="chapter-4---sound-design"></a>Kapitel 4: Sound Design

### <a name="objectives"></a>Ziele

* Verstehen Sie die Überlegungen für den effektiven Sound Entwurf.
* Erlernen Sie die Vorgehensweisen für das Mischen von Techniken

### <a name="part-1---sound-and-experience-design"></a>Teil 1: Sound und Erfahrungs Entwurf

In diesem Abschnitt werden die wichtigsten Überlegungen und Richtlinien für Sound und Design erläutert.

#### <a name="normalize-all-sounds"></a>Alle Sounds normalisieren

Dadurch ist es nicht erforderlich, dass Sonderfallcode die volumeebenen pro Sound anpasst, was zeitaufwändig sein kann, und die Möglichkeit zum einfachen Aktualisieren von Sounddateien einschränkt.

#### <a name="design-for-an-untethered-experience"></a>Entwurf für eine unteschte Darstellung

Hololens ist ein vollständig enthaltener holografischer Computer. Ihre Benutzer können Ihre Erfahrungen während des Verschiebens nutzen und verwenden. Testen Sie Ihre Audiomischung, indem Sie Sie durchlaufen.

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a>Ausgabe von logischen Speicherorten auf Ihren holograms

In der Praxis kommt ein Hund nicht von seinem Ende her, und die Stimme eines Menschen wird nicht von seinen Füßen entfernt. Vermeiden Sie, dass Ihre Sounds aus unerwarteten teilen ihrer holograms ausgegeben werden.

Bei kleinen holograms ist es sinnvoll, eine Soundausgabe aus der Mitte der Geometrie zu haben.

#### <a name="familiar-sounds-are-most-localizable"></a>Vertraute Sounds sind die meisten lokalisierbaren Sounds

Die Menschen Sprache und Musik sind sehr einfach zu lokalisieren. Wenn jemand Ihren Namen aufruft, können Sie genau feststellen, welche Richtung die Stimme erhalten hat und wie weit entfernt. Kurze, unbekannte Sounds sind schwieriger zu lokalisieren.

#### <a name="be-cognizant-of-user-expectations"></a>Erkennen von Erwartungen von Benutzern

Die Lebensdauer spielt einen Teil der Möglichkeit, den Speicherort eines Sounds zu erkennen. Dies ist ein Grund, warum die menschliche Stimme besonders leicht lokalisiert werden kann. Es ist wichtig, dass Sie wissen, welche Erwartungen der Benutzer beim Platzieren Ihrer Sounds hat.

Wenn ein Benutzer beispielsweise einen vogelsong hört, sehen Sie sich im Allgemeinen an, da sich die Vögel in der Regel über der Sicht befinden (in der Struktur oder in einer Struktur). Es ist nicht ungewöhnlich, dass ein Benutzer die korrekte Richtung eines Sounds einschaltet, aber in der falschen vertikalen Richtung sucht und verwirrt oder frustriert wird, wenn er das Hologram nicht finden kann.

#### <a name="avoid-hidden-emitters"></a>Vermeiden Sie verborgene Emitter.

In der realen Welt können wir, wenn wir einen Sound hören, im Allgemeinen das Objekt identifizieren, das den Sound ausgibt. Dies sollte auch für Ihre Erfahrungen sorgen. Es kann sehr stark sein, dass Benutzer einen Sound hören und wissen, woher der Sound stammt und ein Objekt nicht sehen kann.

Es gibt einige Ausnahmen zu dieser Richtlinie. Umgebungs Klänge wie z. b. Crickets in einem Feld müssen z. b. nicht sichtbar sein. Mit der Lebensdauer können wir uns mit der Quelle dieser Sounds vertraut machen, ohne Sie sehen zu müssen.

### <a name="part-2---sound-mixing"></a>Teil 2: Sound Mischung

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a>Ziel ihrer Mischung für 70% Volume in den hololens

Gemischte Realität ermöglicht das Erkennen von holograms in der realen Welt. Sie sollten auch das hören von echten Sounds erlauben. Ein 70%-volumespeicherziel ermöglicht dem Benutzer, die Welt mit dem Sound Ihrer Benutzerumgebung zu hören.

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a>Hololens bei 100% Volume sollten externe Sounds auslagern

Eine Volumeebene von 100% ist vergleichbar mit einer Virtual Reality-Darstellung. Der Benutzer wird visuell in eine andere Welt transportiert. Dasselbe sollte true sein.

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a>Verwenden des Unity Audiomixer zum Anpassen von Sound Kategorien

Beim Entwerfen ihrer Mischung ist es häufig hilfreich, audiokategorien zu erstellen, und Sie können das Volume als Einheit vergrößern oder verkleinern. Dies behält die relativen Ebenen jedes Sounds bei und ermöglicht gleichzeitig schnelle und einfache Änderungen an der gesamten Mischung. Zu den allgemeinen Kategorien gehören: Soundeffekte, Ambiente, Sprachausgabe und Hintergrundmusik.

#### <a name="mix-sounds-based-on-the-users-gaze"></a>Sounds auf der Grundlage des Benutzer Blicks mischen

Häufig kann es hilfreich sein, die Sound Mischung in Ihrer Benutzer Darstellung zu ändern, je nachdem, wo ein Benutzer sucht (oder nicht). Diese Technik wird häufig verwendet, um die Volumeebene für holograms zu verringern, die sich außerhalb des Holographic Frame befinden, um dem Benutzer die Möglichkeit zu geben, sich auf die darin vorgelagerten Informationen zu konzentrieren. Eine andere Verwendung besteht darin, das Volume eines Sounds zu vergrößern, um die Aufmerksamkeit des Benutzers auf ein wichtiges Ereignis zu zeichnen.

#### <a name="building-your-mix"></a>Entwickeln der Mischung

Wenn Sie Ihre Mischung entwickeln, empfiehlt es sich, mit der Hintergrund Audiofunktion Ihrer Benutzererfahrung zu beginnen und Ebenen basierend auf der Wichtigkeit hinzuzufügen. Dies führt häufig dazu, dass jede Ebene lauter ist als die vorherige.

Wenn Sie Ihre Mischung als umgekehrten Trichter mit den geringsten wichtigen (und üblicherweise ruhigste Sounds) im unteren Bereich vorstellen, empfiehlt es sich, die Mischung ähnlich wie im folgenden Diagramm zu strukturieren.

![Sound Mischungs Struktur](images/soundlevels.png)

Die Sprachausgabe ist ein interessantes Szenario. Basierend auf der von Ihnen erstellten Benutzersprache möchten Sie möglicherweise einen Stereo-Sound (nicht lokalisiert) oder eine räumliche Sprache umgestalten. Zwei veröffentlichte Microsoft-Erfahrungen veranschaulichen hervorragende Beispiele für jedes Szenario.

[Holotour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) verwendet eine Stereo Stimme über. Wenn die Sprachausgabe den Speicherort beschreibt, der angezeigt wird, ist der Sound konsistent und unterscheidet sich nicht je nach Position des Benutzers. Dadurch kann die Sprachausgabe die Szene beschreiben, ohne die räumlichen Klänge der Umgebung zu nutzen.

[Fragmente](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) nutzt eine spatialisierte Stimme in Form eines Detektiven. Die Stimme des Detektivs wird verwendet, um dem Benutzer einen wichtigen Hinweis zu vermitteln, als wäre ein tatsächlicher Mensch im Raum. Dies bietet noch mehr Einblicke in die Möglichkeiten der Behebung des Geheimnisses.

### <a name="part-3--performance"></a>Teil 3: Leistung

#### <a name="cpu-usage"></a>CPU-Auslastung

Bei Verwendung von räumlichem Sound verbrauchen 10-12-Emitter ungefähr 12% der CPU.

#### <a name="stream-long-audio-files"></a>Lange Audiodateien streamen

Audiodaten können groß sein, insbesondere bei häufigen Stichproben Raten (44,1 und 48 kHz). Eine allgemeine Regel ist, dass Audiodateien, die länger als 5-10 Sekunden sind, gestreamt werden sollten, um die Anwendungs Speicherauslastung zu reduzieren

In Unity können Sie eine Audiodatei für das Streaming in den Import Einstellungen der Datei markieren.

![Audioimportierungseinstellungen](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a>Kapitel 5: besondere Effekte

### <a name="objectives"></a>Ziele

* Fügen Sie "Magic Windows" Tiefe hinzu.
* Bringen Sie den Benutzer in die virtuelle Welt.

### <a name="magic-windows"></a>Magische Fenster

#### <a name="key-concepts"></a>Wichtige Konzepte

* Das Erstellen von Ansichten in eine verborgene Welt ist visuell attraktiv.
* Verbessern Sie die Realismus durch Hinzufügen von Audioeffekten, wenn ein – Hologramm oder der Benutzer sich in der Nähe der verborgenen Welt befindet

#### <a name="instructions"></a>Anweisungen

* Erweitern Sie im Bereich **Hierarchie** den Knoten **hologrammcollection** , und wählen Sie dann **Underworld**aus.
* Erweitern Sie **Underworld** , und wählen Sie **voicesource**aus.
* Klicken Sie im **Inspektor** -Panel auf **Komponente hinzufügen** , und fügen Sie den **Benutzer sprach Effekt**hinzu.

Eine **audiosource** -Komponente wird " **voicesource**" hinzugefügt.

* Legen Sie in **audiosource** **Output** auf **UserVoice (Mixer)** fest.
* Aktivieren Sie das Kontrollkästchen **spatialize** .
* Ziehen Sie  den Schieberegler räumlichkeits Weise in **3D**, oder geben Sie 1 in das Bearbeitungsfeld **ein** .
* Erweitern Sie **3D-Sound Einstellungen**.
* Legen Sie die **Doppler-Ebene** auf **0**fest.
* Legen Sie unter **User Voice Effect**das über **geordnete Objekt** auf die **Unterwelt** aus der Szene fest.
* Legen Sie **Max Distance** auf **1**fest.

Durch das Festlegen von " **Max Distance** " wird der **Benutzer** darüber informiert, wie nah der Benutzer auf das übergeordnete Objekt sein muss, bevor der Effekt aktiviert ist.

* Erweitern Sie unter **User Voice Effect**den Eintrag **Chorus Parameters**.
* Legen Sie die **Tiefe** auf **0,1**fest.
* Legen Sie **Tap 1 Volume**, **Tap 2 Volume** und **3 Volume** auf **0,8**fest.
* Legen Sie **ursprüngliches Sound Volume** auf **0,5**fest.

Mit den vorherigen Einstellungen werden die Parameter des Unity- **audiochor-Filters** konfiguriert, der verwendet wird, um die Stimme des Benutzers zu ergänzen.

* Erweitern Sie unter **User Voice Effect**den Eintrag **Echo Parameters**.
* **Verzögerung** auf **300** festlegen
* Legen Sie das **Zerfalls Verhältnis** auf **0,2**fest.
* Legen Sie **ursprüngliches Sound Volume** auf **0**fest.

Mit den vorherigen Einstellungen werden die Parameter des Unity- **audioechofilters** konfiguriert, der verwendet wird, um die Stimme des Benutzers zu spiegeln.

Das Skript für den Benutzer sprach Effekt ist für Folgendes zuständig:

* Messen des Abstands zwischen dem Benutzer und dem **gameobject** , an das das Skript angefügt wird.
* Es wird ermittelt, ob der Benutzer dem **gameobject-Objekt**zusteht.

Der Benutzer muss das gameobject-Objekt, unabhängig von der Entfernung, sehen, damit der Effekt aktiviert wird.

* Anwenden und Konfigurieren eines **audiochor-Filters** und eines **audioechofilters** auf die **audiosource**.
* Deaktivieren der Auswirkung durch Deaktivieren der Filter.

Der Benutzer sprach Effekt verwendet die MIC-Datenstrom Auswahl Komponente aus dem [mixedrealitytoolkit für Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), um den hochwertigen Voice-Stream auszuwählen und ihn in das Audiosystem von Unity weiterzuleiten.

* Wählen Sie im Bereich **Hierarchie** die Option **Manager**aus.
* Erweitern Sie im **Inspektor** -Panel den **Spracheingabe Handler**.
* Erweitern Sie in **Spracheingabe Handler**die Option **Unterwelt anzeigen**.
* Ändern Sie **keine Funktion** in " **underworldbase. onenable**".

![Schlüsselwort Unterwelt anzeigen](images/showunderworld.png)

* Erweitern Sie die Option **Unterwelt ausblenden**.
* Ändern Sie **keine Funktion** in **underworldbase. ondeaktiviert**.

![Schlüsselwort Unterwelt ausblenden](images/hideunderworld.png)

#### <a name="build-and-deploy"></a>Erstellen und bereitstellen

* Erstellen Sie wie zuvor das Projekt in Unity, und stellen Sie es in Visual Studio bereit.

Nachdem die Anwendung bereitgestellt wurde:

* Stellen Sie eine Oberfläche (Wall, Floor, Table) dar, und sagen Sie *"Show Underworld"* .

Die Unterwelt wird angezeigt, und alle anderen holograms werden ausgeblendet. Wenn die Unterwelt nicht angezeigt wird, stellen Sie sicher, dass Sie mit der realen Oberfläche konfrontiert sind.

* Ansatz innerhalb von 1 Meter des Unterwelt – Hologramm, und beginnen Sie mit der Kommunikation.

Es gibt jetzt Audioeffekte, die auf Ihre Stimme angewendet werden!

* Schalten Sie die Unterwelt aus, und beachten Sie, dass der Effekt nicht mehr angewendet wird.
* Sagen Sie *"Unterwelt ausblenden"* , um die Unterwelt auszublenden.

Die Unterwelt wird ausgeblendet, und die zuvor ausgeblendeten holograms werden erneut angezeigt.

## <a name="the-end"></a>Das Ende

Herzlichen Glückwunsch! Sie haben jetzt die **räumliche 220 von abgeschlossen: Räumlicher**Sound.

Lauschen Sie auf die Welt, und bringen Sie Ihre Erfahrungen mit Sound!
