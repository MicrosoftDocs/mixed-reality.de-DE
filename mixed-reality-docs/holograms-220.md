---
title: MR räumlich 220 - räumliche sound
description: Führen Sie diese Codierung Exemplarische Vorgehensweise mit Unity, Visual Studio und HoloLens um die Details der räumlichen sound Konzepte zu erfahren.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Holotoolkit, Mixedrealitytoolkit, Mixedrealitytoolkit-Unity, Academy, Tutorial, räumliche sound
ms.openlocfilehash: 50d17fe8c9a6e3f18b1309a59c9c41af982a7505
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593832"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

<br>

# <a name="mr-spatial-220-spatial-sound"></a>MR Spatial 220: Raumklang

[Räumliche Sound](spatial-sound.md) breathes Leben in Hologramme und sorgt dafür, dass in unserer Welt. Hologramme von Licht und Sound bestehen, und wenn Sie doch Ihre Hologramme aus den Augen zu verlieren, räumliche Sound können Sie zu finden. Es ist kein räumlicher Sound wie typische Sounds, die Sie auf die Radio hören würde, Klänge, mit denen im 3D-Raum positioniert ist. Räumliche Sound können Sie machen Hologramme sound scheinen hinter, neben oder sogar auf den Kopf zu sein! In diesem Kurs führen Sie folgende Aktionen ausführen:

* Konfigurieren Sie Ihre Entwicklungsumgebung für Microsoft Spatial Sound verwenden.
* Verwenden Sie räumliche Sound, um Interaktionen zu verbessern.
* Verwenden Sie räumliche Sound in Verbindung mit räumlichen zuordnen.
* Erfahren Sie, Entwurf und die Verwendung von bewährten Methoden.
* Verwendung von Tönen verbessern Spezialeffekte zu erzeugen, und schalten den Benutzer in die Welt der Mixed Reality.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td>MR Spatial 220: Raumklang</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Bevor Sie beginnen

### <a name="prerequisites"></a>Vorraussetzungen

* Ein Windows 10-PCs mit dem richtigen konfiguriert [-Tools installiert](install-the-tools.md).
* Einige grundlegende C# Programmierkenntnisse.
* Sie sollten abgeschlossen haben [MR Grundlagen 101](holograms-101.md).
* Ein Gerät HoloLens [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Projektdateien

* Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) vom Projekt erforderlich sind. Ist Unity 2017.2 oder höher erforderlich.
  * Wenn Sie weitere Unity 5.6-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip). Diese Version kann nicht mehr auf dem neuesten Stand sein.
  * Wenn Sie weitere Unity 5.5-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip). Diese Version kann nicht mehr auf dem neuesten Stand sein.
  * Wenn Sie weitere 5.4 von Unity-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip). Diese Version kann nicht mehr auf dem neuesten Stand sein.
* Un-Archive die Dateien auf dem Desktop oder andere einfach auf den Speicherort zugreifen.

>[!NOTE]
>Wenn Sie vor dem Herunterladen, den Quellcode ansehen möchten es [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).

### <a name="errata-and-notes"></a>Fehler und Anmerkungen zu dieser Version

* "Nur eigenen Code aktivieren" muss deaktiviert sein (*deaktiviert*) in Visual Studio unter Extras -> Optionen-Debuggen >, um die Haltepunkte in Ihrem Code.

## <a name="chapter-1---unity-setup"></a>Kapitel 1: Unity-Setup

### <a name="objectives"></a>Ziele

* Ändern von Unity sound-Konfiguration zum Microsoft Spatial Sound verwenden.
* Fügen Sie auf ein Objekt in Unity 3D Sound hinzu.

### <a name="instructions"></a>Anweisungen

* Starten Sie Unity.
* Wählen Sie **öffnen**.
* Navigieren Sie zu Ihrem Desktop und suchen Sie den Ordner Sie zuvor nicht archiviert.
* Klicken Sie auf die **Starting\Decibel** Ordner, und drücken Sie dann die **Ordner auswählen** Schaltfläche.
* Warten Sie auf das Projekt im Unity geladen.
* In der **Projekt** Bereich öffnen **Scenes\Decibel.unity**.
* In der **Hierarchie** erweitern **HologramCollection** , und wählen Sie **P0LY**.
* Erweitern Sie in der Eigenschaftenanalyse **AudioSource** und beachten Sie, dass es keine **Spatialize** Kontrollkästchen.

Standardmäßig wird in Unity eine Spatializer-Plug-Ins nicht geladen. Die folgenden Schritte können räumlich Sound im Projekt.

* Navigieren Sie im oberen Menü Unity zu **Bearbeiten > Projekteinstellungen > Audio**.
* Suchen der **Spatializer-Plug-Ins** Dropdown-Liste, und wählen Sie **MS HRTF Spatializer**.
* In der **Hierarchie** wählen **HologramCollection > P0LY**.
* In der **Inspektor** Bereich, suchen Sie nach der **Audio Source** Komponente.
* Überprüfen Sie die **Spatialize** Kontrollkästchen.
* Ziehen Sie die **räumliche Blend** Schieberegler ganz nach **3D**, oder geben Sie **1** in das Bearbeitungsfeld.

Jetzt erstellen Sie das Projekt in Unity und konfigurieren die Projektmappe in Visual Studio.

1. Wählen Sie in Unity **Datei > Buildeinstellungen**.
2. Klicken Sie auf **öffnen Szenen hinzufügen** die Szene hinzufügen.
3. Wählen Sie **universelle Windows-Plattform** in die **Plattform** aus, und klicken Sie auf **Plattform wechseln**.
4. Wenn Sie speziell für HoloLens entwickeln, legen Sie **Zielgerät** zu **HoloLens**. Andernfalls lassen Sie es auf **jedes Gerät**.
5. Stellen Sie sicher **Build Type** nastaven NA hodnotu **D3D** und **SDK** nastaven NA hodnotu **zuletzt installierte** (die sollte SDK 16299 oder höher sein).
6. Klicken Sie auf **Erstellen**.
7. Erstellen Sie eine **neuer Ordner** mit dem Namen "App".
8. Mausklick die **App** Ordner.
9. Drücken Sie **wählen Sie Ordner**.

Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.

1. Öffnen der **App** Ordner.
2. Öffnen der **Dezibel Visual Studio-Projektmappe**.

Wenn für HoloLens bereitstellen zu können:

1. Verwenden obere auf der Symbolleiste in Visual Studio, ändern Sie das Ziel vom Debugmodus in den **Version** und ARM, **X86**.
2. Klicken Sie auf den Dropdownpfeil neben der Schaltfläche mit den lokalen Computer, und wählen **Remotecomputer**.
3. Geben Sie **die HoloLens-Geräte-IP-Adresse** und legen Sie den Authentifizierungsmodus auf **universell (unverschlüsseltes Protokoll)**. Klicken Sie auf **Auswählen**. Wenn Sie Ihre IP-Adresse des Geräts nicht kennen, suchen Sie im **Einstellungen > Netzwerk und Internet > Erweiterte Optionen**.
4. Klicken Sie in der Menüleiste im oberen Bereich auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**. Ist dies beim ersten auf Ihrem Gerät bereitstellen, Sie müssen [verbinden Sie es mit Visual Studio](using-visual-studio.md#pairing-your-device---hololens-1st-gen).

Wenn eine immersive Kopfhörer bereitstellen:

1. Verwenden obere auf der Symbolleiste in Visual Studio, ändern Sie das Ziel vom Debugmodus in den **Version** und ARM, **X64**.
2. Stellen Sie sicher, dass das Bereitstellungsziel nastaven NA hodnotu **lokalen Computer**.
3. Klicken Sie in der Menüleiste im oberen Bereich auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**.

## <a name="chapter-2---spatial-sound-and-interaction"></a>Kapitel 2: räumliche Sound- und Interaktion

### <a name="objectives"></a>Ziele

* Verbessern Sie – Hologramm wirklichkeitsgetreuen Bilder mithilfe von Sounds.
* Weiterleiten des Benutzers Blicke Sound verwenden.
* Geben Sie mithilfe von Sound Geste-Feedback.

### <a name="part-1---enhancing-realism"></a>Teil 1 – Verbesserung realer zu gestalten.

#### <a name="key-concepts"></a>Wichtige Konzepte

* Spatialize – Hologramm Sounds.
* Sound Quellen, die am einen geeigneten Speicherort auf dem Hologramm eingefügt werden soll.

Die gewünschte Position für den Sound wird die Hologramm abhängig. Wenn einem Benutzer, der die – Hologramm ist, sollten z. B. Schallquelle Mund und nicht die Füße gespeichert sein.

#### <a name="instructions"></a>Anweisungen

Die folgenden Anweisungen werden ggf. ein Hologramm Sound spatialized zuordnen.

* In der **Hierarchie** erweitern **HologramCollection** , und wählen Sie **P0LY**.
* In der **Inspektor** im Bereich der **AudioSource**, klicken Sie auf den Kreis neben **AudioClip** , und wählen Sie **PolyHover** aus der Popupliste.
* Klicken Sie auf den Kreis neben **Ausgabe** , und wählen Sie **SoundEffects** aus der Popupliste.

Projekt Dezibel verwendet eine Unity **AudioMixer** -Komponente verwendet, damit Geräuschpegel für Gruppen von Sounds anpassen. Durch Gruppierung von Sounds auf diese Weise kann das gesamte Volume und gleichzeitig die relative Menge der einzelnen Sound angepasst werden.

* In der **AudioSource**, erweitern Sie **3D Sound Einstellungen**.
* Legen Sie **Doppler-Ebene** zu **0**.

Festlegen von Doppler Ebene auf 0 (null) deaktiviert die Änderungen in der Stimmhöhe verursacht werden, die in Motion (entweder die Hologramm oder der Benutzer). Ein klassisches Beispiel Doppler ist eine schnelle, flexible Auto. Wenn sich das Fahrzeug stationären Listener nähert, steigt die Schriftbreite des Datenbankmoduls. Wenn den Listener übergibt, verringert sich die Schriftbreite mit Abstand.

### <a name="part-2---directing-the-users-gaze"></a>Teil 2: Weiterleiten des Benutzers Blicke

#### <a name="key-concepts"></a>Wichtige Konzepte

* Verwenden Sie die Aufmerksamkeit auf wichtige Hologramme Sound.
* Die Ohren besser, in denen die Augen suchen soll.
* Das Gehirn hat bestimmte Erwartungen Gelernten.

Ein Beispiel für gelernten Erwartungen ist, dass Vögel in der Regel über den Köpfen der Menschen. Wenn ein Benutzer einen Sound Bird hört, ist ihre erste Reaktion nachschlagen. Platzieren einer Bird unterhalb der Benutzer kann Ihnen den Klang, aber nicht auf die – Hologramm basierend auf der Annahme zu suchen müssen, finden Sie die richtige Richtung zeigenden führen.

#### <a name="instructions"></a>Anweisungen

Die folgenden Anweisungen aktivieren P0LY hinter, ausblenden, sodass Sie Sound verwenden können, die – Hologramm gesucht werden soll.

* In der **Hierarchie** wählen **Managern**.
* In der **Inspektor** Bereich, suchen Sie nach **Spracherkennung Eingabe Handler**.
* In **Spracherkennung Eingabe Handler**, erweitern Sie **wechseln ausblenden**.
* Änderung **keine Funktion** zu **PolyActions.GoHide**.

![Keyword: Wechseln Sie ausblenden](images/gohide.png)

### <a name="part-3---gesture-feedback"></a>Teil 3 – Geste Feedback

#### <a name="key-concepts"></a>Wichtige Konzepte

* Bietet dem Benutzer mit positiven Geste Bestätigung mithilfe von sound
* Des Benutzers, übermäßig laut Sounds Get auf die Weise nicht zu überlasten
* Feine Sounds Arbeit best - nicht überlagern, die Benutzeroberfläche

#### <a name="instructions"></a>Anweisungen

* In der **Hierarchie** erweitern **HologramCollection**.
* Erweitern Sie **EnergyHub** , und wählen Sie **Base**.
* In der **Inspektor** auf **Add Component** und fügen **Sound Gestenhandler**.
* In **Sound Gestenhandler**, klicken Sie auf den Kreis neben **Navigation Schritte Clip** und **Navigation aktualisiert Clip** , und wählen Sie **RotateClick**aus der Popupliste für beide.
* Doppelklicken Sie auf "GestureSoundHandler" in Visual Studio geladen.

Geste Sound-Ereignishandler führt die folgenden Aufgaben durch:

* Erstellen und Konfigurieren einer **AudioSource**.
* Ort der **AudioSource** am Speicherort des entsprechenden **"gameobject"**.
* Spielt den **AudioClip** der Bewegung zugeordneten.

#### <a name="build-and-deploy"></a>Erstellen und bereitstellen

1. Wählen Sie in Unity **Datei > Buildeinstellungen**.
2. Klicken Sie auf **Erstellen**.
3. Mausklick die **App** Ordner.
4. Drücken Sie **wählen Sie Ordner**.

Überprüfen Sie, dass die Symbolleiste "Release", "x 86" oder "X64" und "Remotegerät" lautet. Wenn dies nicht der Fall ist, dies ist die Codierung Instanz von Visual Studio. Sie müssen möglicherweise die Lösung über den App-Ordner erneut zu öffnen.

* Wenn Sie dazu aufgefordert werden, laden Sie die Projektdateien.
* Wie zuvor in Visual Studio bereitstellen.

Nachdem die Anwendung bereitgestellt wird:

* Beachten Sie, wie der Sound ändert, während Sie sich auf P0LY bewegen.
* Sagen Sie *"Wechseln Sie verbergen"* P0LY an eine Position hinter Ihnen verschieben vornehmen. Finden Sie es, indem Sie den Sound.
* Bestaunen Sie an der Basis des Energie-Hubs. Tippen Sie auf, und ziehen Sie nach links oder rechts drehen den – Hologramm, und beachten, wie der Sound durch Klicken auf die Aktion bestätigt.

Hinweis: Es ist ein Text-Bereich, der Tag-along mit Ihnen wird ein. Diese werden die verfügbaren Stimmbefehle enthalten, die Sie in diesem Kurs verwenden können.

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a>Kapitel 3: räumliche Sound und räumliche Zuordnung

### <a name="objectives"></a>Ziele

* Interaktion zwischen Hologramme und die reale Welt, die mit der Sound zu bestätigen.
* Verdeckt Sound mithilfe der realen Welt.

### <a name="part-1---physical-world-interaction"></a>Teil 1 – die Interaktion der realen Welt

#### <a name="key-concepts"></a>Wichtige Konzepte

* Physische Objekte in der Regel einen Sound vornehmen, wenn festgestellt wird eine Fläche oder einem anderen Objekt.
* Sounds sollte innerhalb der Umgebung geeigneten Kontext.

Festlegen einer Tasse in einer Tabelle sollten z. B. ruhigerer Sound als eine Boulder auf einen Teil-Metal-Computern löschen.

#### <a name="instructions"></a>Anweisungen

* In der **Hierarchie** erweitern **HologramCollection**.
* Erweitern Sie **EnergyHub**Option **Base**.
* In der **Inspektor** auf **Add Component** und fügen **tippen, direkt mit Sound- und Aktion**.
* In **Tippen Sie auf, um anstelle von Sounds und Aktion**:
  * Überprüfen Sie **Platzieren von übergeordneten auf Tap**.
  * Legen Sie **Platzierung Sound** zu **Ort**.
  * Legen Sie **Pickup Sound** zu **Pickup**.
  * Drücken Sie die + in der unteren rechten in beiden Verzeichnissen **bei Pickup Aktion** und **bei Platzierung Aktion**. Ziehen Sie EnergyHub aus der Szene in der **None (Objekt)** Felder.
    * Klicken Sie unter **bei Pickup Aktion**, klicken Sie auf **keine Funktion** -> **EnergyHubBase** -> **ResetAnimation**.
    * Klicken Sie unter **bei Platzierung Aktion**, klicken Sie auf **keine Funktion** -> **EnergyHubBase** -> **OnSelect**.

![Tippen Sie auf, um anstelle von Sounds und Aktion](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a>Teil 2 – Sound verdecken.

#### <a name="key-concepts"></a>Wichtige Konzepte

* Sound, wie Licht, kann okkludierte sein.

Ein klassisches Beispiel ist eine Concert Hall. Wenn ein Listener verfügbar ist, außerhalb des Unternehmens und die Tür geschlossen ist, die dumpf Musik und Sound. Es ist auch in der Regel eine Reduzierung des Volumens. Wenn die Tür geöffnet wird, ist das gesamte Spektrum von den Sound am des tatsächlichen Umfangs hören. Hohe Auslastung Sounds sind in der Regel mehr als Frequenzen absorbiert.

#### <a name="instructions"></a>Anweisungen

* In der **Hierarchie** erweitern **HologramCollection** , und wählen Sie **P0LY**.
* In der **Inspektor** auf **Add Component** und fügen **Audio Korrekturemitter**.

Die Korrekturemitter für Audio-Klasse bietet die folgenden Features:

* Stellt alle Änderungen auf das Volume von der **AudioSource**.
* Führt eine **Physics.RaycastNonAlloc** aus Position in Richtung des Benutzers die **"gameobject"** , die **AudioEmitter** angefügt ist.

Die RaycastNonAlloc-Methode wird zur leistungsoptimierung verwendet, um Zuordnungen sowie die Anzahl der zurückgegebenen Ergebnisse zu beschränken.

* Für jede **IAudioInfluencer** auftritt, ruft der **ApplyEffect** Methode.
* Für jeden vorherigen **IAudioInfluencer** , nicht mehr festgestellt werden, Aufruf der **RemoveEffect** Methode.

Beachten Sie, dass AudioEmitter auf pro-Frame-Basis auf menschliche Zeitskalen, im Gegensatz zu updates. Dies geschieht, da die Menschen in der Regel nicht schnell genug für den Effekt, die häufiger als einmal pro Quartal oder eine halbe Sekunde aktualisiert werden müssen verschieben. Hologramme, Teleport schnell von einem Speicherort in einen anderen kann die Illusion unterbrochen werden.

* In der **Hierarchie** erweitern **HologramCollection**.
* Erweitern Sie **EnergyHub** , und wählen Sie **BlobOutside**.
* In der **Inspektor** auf **Add Component** und fügen **Audio Occluder**.
* In **Audio Occluder**legen **Grenzwert Häufigkeit** zu **1500**.

Diese Einstellung beschränkt die AudioSource Frequenzen für 1500 Hz und niedriger.

* Legen Sie **Pass-Through-Datenträger** zu **0.9**.

Diese Einstellung verringert die Menge an die AudioSource 90 % der aktuellen Ebene.

Audio Occluder implementiert IAudioInfluencer auf:

* Anwenden einer verdecken Effekt mithilfe einer **AudioLowPassFilter** dem zugeordnet, der **AudioSource** verwalteten kaufen der **AudioEmitter**.
* Gilt die AudioSource Volume Attenuation hinzu.
* Deaktiviert die Auswirkungen von einer neutralen Grenzfrequenz festlegen, und Deaktivieren des Filters.

Die Häufigkeit, die als neutrale ist 22 kHz (22000 Hz). Die Häufigkeit wurde gewählt, da über die nominale maximale Häufigkeit, die das menschliche Ohr, diese vornehmen keine wahrnehmbaren Auswirkungen auf den Sound hören kann.

* In der **Hierarchie** wählen **SpatialMapping**.
* In der **Inspektor** auf **Add Component** und fügen **Audio Occluder**.
* In **Audio Occluder**legen **Grenzwert Häufigkeit** zu **750**.

Wenn mehrere Occluders sind, auf dem Pfad zwischen Benutzer und dem **AudioEmitter**, die niedrigste Häufigkeit wird angewendet, um den Filter.

* Legen Sie **Pass-Through-Datenträger** zu **0,75**.

Wenn mehrere Occluders sind, auf dem Pfad zwischen Benutzer und dem **AudioEmitter**, die Pass-through-Datenträger lichtdurchlässigen angewendet wird.

* In der **Hierarchie** wählen **Managern**.
* In der **Inspektor** erweitern **Spracherkennung Eingabe Handler**.
* In **Spracherkennung Eingabe Handler**, erweitern Sie **wechseln Gebühren**.
* Änderung **keine Funktion** zu **PolyActions.GoCharge**.

![Keyword: Wechseln Sie kostenlos](images/gocharge.png)

* Erweitern Sie **hierher**.
* Änderung **keine Funktion** zu **PolyActions.ComeBack**.

![Keyword: Komm her](images/comehere.png)

#### <a name="build-and-deploy"></a>Erstellen und bereitstellen

* Wie zuvor erstellen Sie das Projekt im Unity, und stellen Sie in Visual Studio bereit.

Nachdem die Anwendung bereitgestellt wird:

* Sagen Sie *"Wechseln Sie kostenlos"* P0LY Geben Sie den Hub Energie haben.

Beachten Sie die Änderung der Sound. Es sollte dumpfe und ein wenig leiser klingen. Wenn Sie sich mit einer Wand oder ein anderes Objekt zwischen Ihnen und dem Hub Energie positionieren können, sollten Sie feststellen, einen weiteren muffling des Sounds am Einschluss von der realen Welt.

* Sagen Sie *"Kommen hier"* P0LY, lassen Sie den Hub Energie, und positionieren Sie sich selbst vor Ihnen haben.

Beachten Sie, dass der sound verdecken entfernt wird, sobald P0LY Energie Hub beendet wird. Falls Sie immer noch hören verdecken, können von der realen Welt P0LY okkludierte sein. Versuchen Sie, um sicherzustellen, dass Sie eine klare uneingeschränkten Zugriff auf P0LY zu verschieben.

### <a name="part-3---room-models"></a>Teil 3 – Platz Modelle

#### <a name="key-concepts"></a>Wichtige Konzepte

* Die Größe des Speicherplatzes bietet subliminalen Warteschlangen, die zur Lokalisierung der sound beitragen.
* Raum Modelle werden pro festgelegt-**AudioSource**.
* Die [MixedRealityToolkit für Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) enthält Code zum Festlegen des Modells Platz.
* Wählen Sie für Mixed Reality-Umgebungen das Platz-Modell, das den realen Welt Speicherplatz am besten geeignet ist.

Wenn Sie ein Virtual Reality-Szenario erstellen, wählen Sie das Platz-Modell, das die virtuelle Umgebung am besten geeignet ist.

## <a name="chapter-4---sound-design"></a>Kapitel 4 – Entwurf

### <a name="objectives"></a>Ziele

* Erfahren Sie, Überlegungen zum effektiven Entwurf.
* Erfahren Sie, Mischen von Methoden und Richtlinien.

### <a name="part-1---sound-and-experience-design"></a>Teil 1 – Sound- und Entwurf der Benutzeroberfläche

Dieser Abschnitt beschreibt die wichtigsten Sound und Überlegungen zum Entwurf der Benutzeroberfläche und Richtlinien.

#### <a name="normalize-all-sounds"></a>Normalisieren Sie alle sounds

Dadurch muss die Groß-/Kleinschreibung spezialcode Lautstärkestufen pro Sound, Anpassen der zeitaufwändig sein kann, und beschränkt die Fähigkeit, um Audiodateien problemlos zu aktualisieren.

#### <a name="design-for-an-untethered-experience"></a>Entwurf für eine unabhängig

HoloLens handelt es sich um eine vollständig enthaltene, unabhängig holographic-Computer. Ihre Benutzer können und Ihre Erfahrungen beim Verschieben von verwenden. Achten Sie darauf, dass die audio Mischung zu testen, indem Sie zu durchlaufen.

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a>Ausgeben von Sounds über logischen Laufwerke auf Ihrem Hologramme

In der realen Welt Hundes nicht über die Tail Hundegebellsound, und einem Benutzer, der die Sprache nicht aus seiner Fuß stammt. Vermeiden Sie, die Ihre Sounds aus unerwarteten Teile Ihrer Hologramme ausgeben.

Kleine Hologramme ist es sinnvoll, die aus der Mitte der Geometrie ausgeben klingen.

#### <a name="familiar-sounds-are-most-localizable"></a>Vertraut klingt sind die meisten lokalisierbar

Die menschliche Stimme und Musik sind sehr einfach zu lokalisieren. Wenn ein Benutzer den Namen Ihres aufgerufen wird, können Sie sehr genau bestimmen, in welche Richtung die Stimme stammen und wie weit entfernt. Sounds für kurzen, nicht vertraut sind schwerer zu lokalisieren.

#### <a name="be-cognizant-of-user-expectations"></a>Werden Sie die Erwartungen der Benutzer kennen sollten

Leben Erfahrung spielt eine Rolle in unserer Fähigkeit zur Identifizierung des Speicherorts eines Sounds. Dies ist ein Grund, warum die menschliche Stimme besonders einfach zu lokalisieren ist. Es ist wichtig zu beachten gelernten Erwartungen des Benutzers bei der Platzierung Ihrer Sounds.

Z. B. wenn ein Benutzer eine Bird "Song" hört suchen sie in der Regel, wie Vögel tendenziell über den uneingeschränkten Zugriff (fliegenden oder in einer Struktur). Es ist nicht ungewöhnlich, dass ein Benutzer in der richtigen Richtung eines Sounds, aber in vertikaler Richtung falsche suchen und verwechseln oder frustriert sind, wenn sie nicht die Hologramm gefunden werden.

#### <a name="avoid-hidden-emitters"></a>Vermeiden Sie ausgeblendete korrekturemitter ab

In der Praxis Wenn wir hören, dass eine solide, können wir in der Regel das Objekt identifizieren, das den Klang ausgibt. Dies sollte auch in Ihre Erfahrungen mit "true" enthalten. Sie können für Benutzer, einen Sound hören, wissen Sie in den Ursprung des Klang sehr verwirrend sein und nicht auf ein Objekt finden Sie unter.

Es gibt einige Ausnahmen von dieser Richtlinie. Beispielsweise müssen Ambiente Audiokomponenten wie Crickets in einem Feld nicht angezeigt. Life-Erfahrung bietet uns die Vertrautheit mit der Quelle dieser Sounds, ohne dass es finden Sie unter.

### <a name="part-2---sound-mixing"></a>Teil 2 – Sound mischen.

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a>Die Mischung für die HoloLens 70 % Volume als Ziel

Mixed Reality-Erfahrungen ermöglichen Hologramme, die in der realen Welt angezeigt werden. Sie sollten auch reale Welt Sounds zu ermöglichen. Ein Ziel 70 % Volume kann der Benutzer die Welt um diese zusammen mit Ihren Erfahrungen zu hören.

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a>HoloLens unter 100 % Volume sollte herausfiltert externe ertrinken.

Eine Volume-Ebene von 100 % entspricht in etwa eine Virtual Reality-Erfahrung. Visuell wird der Benutzer zu einem anderen System übertragen. Die gleiche muss "true" akustisch enthalten sind.

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a>Verwenden Sie die Unity-AudioMixer Kategorien von Sounds anpassen

Beim Entwerfen Ihrer testmischung ist es oft hilfreich, sound Kategorien erstellen und haben die Möglichkeit, erhöhen oder Verringern ihres Umfangs als eine Einheit. Dies behält die relativen Leistungsstufen für jeden Sound gleichzeitig schnelle und einfache Änderungen an der Kombination aus. Allgemeine Kategorien sind: Soundeffekte, Umgebung, Voice-Failover und Hintergrundmusik.

#### <a name="mix-sounds-based-on-the-users-gaze"></a>Kombinieren Sie anhand des Benutzers Blicke sounds

Es kann häufig hilfreich sein, ändern Sie den sound Mischung in Ihre Umgebung basierend auf den Speicherort ein Benutzers ist (oder nicht) suchen. Ein gängiges Szenario für dieses Verfahren werden die Volumeebene für Hologramme zu reduzieren, die außerhalb von den Holographic Frame für den Benutzer zu konzentrieren, die Informationen direkt vor ihnen erleichtern. Eine weitere Verwendungsmöglichkeit ist zum Erhöhen der Lautstärke eines Sounds aus, um die Aufmerksamkeit des Benutzers auf ein wichtiges Ereignis zu zeichnen.

#### <a name="building-your-mix"></a>Erstellen die Mischung

Wenn Sie die Mischung erstellen zu können, empfiehlt es sich mit hintergrundaudiofunktion für Ihre Umgebung die beginnen, und basierte auf Wichtigkeit Ebenen hinzufügen. Oft führt dies in jeder Schicht wird als die vorherige lauter.

Die Mischung vorstellen, als eine invertierte Trichter, mit dem am wenigsten wichtige (und in der Regel leisesten Sounds) im unteren Bereich wird empfohlen, die ähnlich wie im folgenden Diagramm Mischung Struktur.

![Sound Mix-Struktur](images/soundlevels.png)

Voice-Failover sind ein interessantes Szenario. Basierend auf der Erfahrung, die Sie erstellen Sie nach Wunsch eine (nicht lokalisierte) Stereosound oder Ihre Stimme Failover spatialize. Zwei Microsoft veröffentlichte Erfahrungen hervorragende Beispiele für jedes Szenario zu veranschaulichen.

[HoloTour](http://www.microsoft.com/store/p/holotour/9nblggh5pj87) Sprachnotizen Stereo verwendet. Wenn die Sprachausgabe den Speicherort, der angezeigt wird, beschreibt, wird der Sound sind konsistent und ist nicht variieren je nach Position des Benutzers. Dies ermöglicht die Sprachausgabe um der Szene ohne Durchführung von die spatialized Sounds aus der Umgebung zu beschreiben.

[Fragmente](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) nutzt eine spatialized Stimme über in Form einer Detective. Des Detektivs Stimme wird verwendet, zu bringen die Aufmerksamkeit des Benutzers, ein wichtiger Hinweis darauf, wie bei einer tatsächlichen Menschen im Raum. Dies ermöglicht eine noch größere Eindruck davon zu Entwicklungsthemen in die Oberfläche der Rätsel lösen.

### <a name="part-3--performance"></a>Teil 3: Leistung

#### <a name="cpu-usage"></a>CPU-Auslastung

Wenn räumliche Sound verwenden, werden 10.-12. korrekturemitter ungefähr 12 % der CPU verbraucht.

#### <a name="stream-long-audio-files"></a>Lange Audiodateien Stream

Audiodaten können vor allem bei allgemeinen Samplingraten (48, und 44,1 kHz) groß sein. Eine allgemeine Regel gilt, Audiodateien, die länger als 5 bis 10 Sekunden gestreamt werden sollen, um die speicherauslastung der Anwendung zu reduzieren.

In Unity können Sie eine Audiodatei für das streaming in der Datei importeinstellungen markieren.

![Audio Importieren von Einstellungen](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a>Kapitel 5 – Spezialeffekte zu erzeugen

### <a name="objectives"></a>Ziele

* Tiefe "Magic-Windows" hinzufügen.
* Bringen Sie den Benutzer in der virtuellen Welt ein.

### <a name="magic-windows"></a>Magic Windows

#### <a name="key-concepts"></a>Wichtige Konzepte

* Erstellen von Ansichten in einer ausgeblendeten Welt, ist eine visuell ansprechende.
* Verbessern Sie realer zu gestalten, indem Sie das Hinzufügen von Audioeffekten Wenn ggf. ein Hologramm oder der Benutzer in der Nähe der ausgeblendeten Welt ist.

#### <a name="instructions"></a>Anweisungen

* In der **Hierarchie** erweitern **HologramCollection** , und wählen Sie **Underworld**.
* Erweitern Sie **Underworld** , und wählen Sie **VoiceSource**.
* In der **Inspektor** auf **Add Component** und fügen **User Voice-Effekt**.

Ein **AudioSource** Komponente hinzugefügt **VoiceSource**.

* In **AudioSource**legen **Ausgabe** zu **UserVoice (Mixer)**.
* Überprüfen Sie die **Spatialize** Kontrollkästchen.
* Ziehen Sie die **räumliche Blend** Schieberegler ganz nach **3D**, oder geben Sie **1** in das Bearbeitungsfeld.
* Erweitern Sie **3D Sound Einstellungen**.
* Legen Sie **Doppler-Ebene** zu **0**.
* In **User Voice-Effekt**legen **übergeordnetes Objekt** auf die **Underworld** aus der Szene.
* Legen Sie **maximaler Abstand** zu **1**.

Festlegen von **maximaler Abstand** weist **User Voice-Effekt** wie nahe der Benutzer auf das übergeordnete Objekt sein muss, bevor der Effekt aktiviert ist.

* In **User Voice-Effekt**, erweitern Sie **heißen Talbot Parameter**.
* Legen Sie **Tiefe** zu **0,1**.
* Legen Sie **Tippen Sie auf 1 Volume**, **Tippen Sie auf 2 Volume** und **Tippen Sie auf 3 Volume** zu **0,8**.
* Legen Sie **ursprünglichen Sound Volume** zu **0,5**.

Die vorherigen Einstellungen konfigurieren Sie die Parameter von Unity **AudioChorusFilter** verwendet, um Sie Umfang des Benutzers Stimme hinzufügen.

* In **User Voice-Effekt**, erweitern Sie **Echo Parameter**.
* Legen Sie **Verzögerung** zu **300**
* Legen Sie **Decay-Verhältnis** zu **0,2**.
* Legen Sie **ursprünglichen Sound Volume** zu **0**.

Die vorherigen Einstellungen konfigurieren Sie die Parameter von Unity **AudioEchoFilter** verwendet, damit das Benutzerfeedback, das zurückgegeben wird.

Das Skript User Voice-Effekt ist verantwortlich für:

* Den Abstand zwischen dem Benutzer zu messen und die **"gameobject"** , dem das Skript zugeordnet ist.
* Bestimmen, und zwar unabhängig davon, ob der Benutzer zeigt die **"gameobject"**.

Der Benutzer muss das "gameobject", unabhängig vom Abstand für den Effekt zu aktivierenden verbunden ist.

* Anwenden und konfigurieren eine **AudioChorusFilter** und ein **AudioEchoFilter** auf die **AudioSource**.
* Deaktivieren den Effekt, indem Sie die Filter deaktivieren.

User Voice-Effekt verwendet die Mic-Stream-Selektor-Komponente, aus der [MixedRealityToolkit für Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), um die qualitativ hochwertige Sprachstream wählen aus, und sie in Unity-audio-System weiterzuleiten.

* In der **Hierarchie** wählen **Managern**.
* In der **Inspektor** erweitern **Spracherkennung Eingabe Handler**.
* In **Spracherkennung Eingabe Handler**, erweitern Sie **anzeigen Underworld**.
* Änderung **keine Funktion** zu **UnderworldBase.OnEnable**.

![Keyword: Underworld anzeigen](images/showunderworld.png)

* Erweitern Sie **ausblenden Underworld**.
* Änderung **keine Funktion** zu **UnderworldBase.OnDisable**.

![Keyword: Hide Underworld](images/hideunderworld.png)

#### <a name="build-and-deploy"></a>Erstellen und bereitstellen

* Wie zuvor erstellen Sie das Projekt im Unity, und stellen Sie in Visual Studio bereit.

Nachdem die Anwendung bereitgestellt wird:

* Sehen Sie eine Fläche (Wand, Floor, Tabelle) und sagen *"Underworld anzeigen"*.

Die Underworld wird angezeigt, und alle anderen Hologramme ausgeblendet werden. Die Underworld nicht angezeigt wird, sicher, dass eine reale Oberfläche aufgetretenen.

* Innerhalb von 1 Meter Umkreis um die Underworld – Hologramm Ansatz, und sprechen.

Es gibt jetzt Audioeffekte angewendet werden, um Ihre Stimme!

* Aktivieren Sie die Underworld, und beachten Sie, wie der Effekt nicht mehr angewendet wird.
* Sagen Sie *"Underworld ausblenden"* der Underworld ausblenden.

Die Underworld werden ausgeblendet, und die zuvor nicht Hologramme werden erneut angezeigt.

## <a name="the-end"></a>Das Ende

Herzlichen Glückwunsch! Sie haben jetzt **MR räumliche 220: Räumliche Sound**.

Lauschen auf der ganzen Welt, und setzen Sie Ihre Erfahrungen mit Sound!
