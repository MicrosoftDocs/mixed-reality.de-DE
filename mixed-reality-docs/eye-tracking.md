---
title: Eye-tracking
description: Eye-tracking
author: sostel
ms.author: sostel
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Nachverfolgen von Auge, Mixed Reality "," Input "," Eye Blicke
ms.openlocfilehash: d41b9973ede323e842d7187becb1220ba9980a5d
ms.sourcegitcommit: 5b4292ef786447549c0199003e041ca48bb454cd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402348"
---
# <a name="eye-tracking-on-hololens-2"></a>Eye-tracking für HoloLens 2
HoloLens 2 ermöglicht die für eine ganz neue Ebene von Kontext und menschliche Verständnis der Holographic nutzen möchten, um Entwicklern die unglaublichen Möglichkeit der Verwendung von Informationen, was Benutzer betrachten. Diese Seite bietet einen Überblick darüber, wie Entwickler von Eye-Überwachung für verschiedene Anwendungsfälle profitieren können und was Sie beachten müssen, wenn Eye-Blicke-basierten Benutzeroberflächen zu entwerfen. 

## <a name="use-cases"></a>Anwendungsfälle
Eye-tracking kann Anwendungen überwachen, in denen der Benutzer in Echtzeit sucht. Dieser Abschnitt beschreibt einige der möglichen Anwendungsfälle und neuartige Interaktionen, die mit Eye-tracking in mixed Reality möglich werden.
Bevor Sie beginnen, in der folgenden wird erläutert die [Mixed Reality-Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) mehrere Male auf, da sie einige Beispiele für interessanter und leistungsfähiger bereitstellt, für die Verwendung von Eye nachverfolgen, wie z. B. schnelle und mühelose Eye-unterstützt-Ziel Auswahl und automatisch einen Bildlauf Text basierend auf, in dem der Benutzer am sucht. 

### <a name="user-intent"></a>Benutzerabsicht    
Informationen zu, in denen ein Benutzer untersucht, bietet eine leistungsstarke **Kontext für die anderen Eingaben**, z. B. Sprach-, praktische und Controller.
Dies kann für verschiedene Aufgaben verwendet werden.
Beispielsweise diese reichen von schnell und mühelos **für** in der Szene, indem Sie einfach ggf. ein Hologramm ansehen und sagen "select" (Siehe auch [Head-Blicke und Commit](gaze-and-commit.md)) oder indem Sie sagen, "put dies...", klicken Sie dann über möchten, sollen die Hologramm platzieren und klicke auf "... There". Beispiele hierfür finden Sie im [Mixed Reality-Toolkit – Zielauswahl Eye-Unterstützung](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) und [gemischte Realität-Toolkit – Eye unterstützte Ziel Positionierung](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html).

Ein weiteres Beispiel für die Benutzerabsicht herausgeberkontos ausgewiesenen Form mithilfe von Informationen über Benutzer betrachten die Mitwirkung von beispielsweise virtuelle Agents und interaktive Hologramme zu verbessern. Klicken Sie z. B. virtuelle Agents können die verfügbare Optionen anpassen, und ihr Verhalten entsprechend der derzeit auf angezeigt Inhalt. 

### <a name="implicit-actions"></a>Implizite Aktionen
Die Kategorie der implizite Aktionen bezieht sich genau auf der Benutzerabsicht verwendet wird.
Die Idee ist, dass Hologramme oder Elemente der Benutzeroberfläche auf etwas instinctual Weise, die nicht selbst vielleicht den Eindruck reagieren, wie Sie mit dem System alle, sondern vielmehr interagiert werden, dass das System und der Benutzer synchronisiert sind. Ein Beispiel für die äußerst erfolgreiche ist z. B. **Eye-Blicke basierende AutoBildlauf**. Die Idee ist einfach: Der Benutzer einen Text liest und kann nur weiterlesen. Der Text verschiebt allmählich nach oben zu Benutzern in ihrer Flow lesen. Ein wichtiger Aspekt ist, dass die Geschwindigkeit des Bildlaufs an die Geschwindigkeit beim Lesen des Benutzers anpasst.
Ein weiteres Beispiel ist **Eye unterstützte Zoom- und schwenkoptionen** für die der Benutzer profitieren wie näher eingegangen wird genau auf was er am konzentriert. Das Auslösen für den Zoomfaktor und die Zoom-Geschwindigkeit steuern über Voice gesteuert werden können oder übergeben die Eingabe, die zum Bereitstellen im Gefühl der Kontrolle wichtig ist, und vermeiden einer Überlastung des Benutzers (wird diese Entwurfsrichtlinien im folgenden ausführlicher erläutert). Nachdem das Diagramm vergrößert ist, kann der Benutzer klicken Sie dann reibungslos, z. B. die eine Straße auf seinem Nachbarschaft zu entdecken, indem Sie ihren Augen Blicke einfach durchzuführen.
Demo-Beispiele für diese Arten von Aktivitäten finden Sie in der [Mixed Reality-Toolkit - Navigation Eye-Unterstützung](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) Beispiel.

Weitere Anwendungsfälle für _implizite Aktionen_ herausgeberkontos ausgewiesenen Form:
- **Intelligente Benachrichtigungen:** Je abrufen nicht mögen von Benachrichtigungen oben rechts, in dem Sie sich konzentrieren, wurden, entfernt wurde? Beachten Sie dabei, in denen ein Benutzer derzeit auf Kosten, können Sie es besser machen! Zeigen Sie Benachrichtigungen, die Abweichung von der, in denen der Benutzer derzeit suchen wird, um ablenkungen zu beschränken, und schließen sie automatisch einmal gelesen. 
- **Basiert auf aufmerksamer Hologramme:** Hologramme, die leicht zu reagieren, wenn betrachtet wird. Dies kann eine langsam boomende Blume virtuelles Haustier Ausgangspunkt zurück betrachten Sie oder Ihre Augen Blicke vermeiden Sie nach einem längeren Vorgang verfolgen möchten zwischen etwas leuchtendes UI-Elemente liegen. Dies kann eine interessante sinnvoll sein, der Konnektivität und die Kundenzufriedenheit in Ihrer app bereitstellen.

### <a name="attention-tracking"></a>Nachverfolgen von Aufmerksamkeit   
Informationen zu, in denen Benutzer betrachten ist ein unglaublich leistungsfähiges Tool zur Bewertung der Nutzbarkeit von Designs und Probleme effizient Arbeitsschritte zu identifizieren. Mittlerweile sind Eye-tracking visualisierungs- und Analysefunktionen bereits üblicherweise in verschiedenen Anwendungsbereichen. Mit HoloLens-2 bieten wir eine neue Dimension ein, um dieses Verständnis, wie 3D Hologramme in realen Kontexten platziert und zusammen mit bewertet werden können. Die [Mixed Reality-Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) enthält grundlegende Beispiele, für die Protokollierung und Eye-tracking Daten geladen und für das sie visuell darzustellen.

Andere Anwendungen in diesem Bereich können Folgendes umfassen: 
-   **Remote Eye Blicke Visualisierung:** Visualisieren, was remote Projektmitarbeiter, z. B. betrachten, stellen Sie sicher, ob Anweisungen richtig verstanden und befolgt werden.
-   **Research Benutzerstudien:** Aufmerksamkeit nachverfolgen kann, sehen Sie sich die Anfänger und Experten Benutzer visuell zu analysieren, Inhalt oder ihre Hand-Augen-Koordinierung für komplexe Aufgaben (z. B. für die Analyse, medizinische Daten oder beim Betrieb von Maschinen) verwendet werden.
-   **Training Simulationen und Überwachung der Anwendungsleistung:** Üben Sie, und Optimieren Sie die Ausführung von Aufgaben, durch das Erkennen von Engpässen effektiver auf den Ausführungsablauf.
-   **Entwerfen Sie Bewertungen, Ankündigungen und marketing Research:** Eye-tracking ist ein gängiges Tool für marktforschungs-Website und Produktentwürfe ausgewertet.

### <a name="additional-use-cases"></a>Zusätzliche Szenarien
- **Spiele:** Wollten Sie jemals Finger geradezu übernatürliche Kräfte haben? Hier ist Ihre Gelegenheit! Levitate Hologramme durch diese Ertragen. Schießen Sie Laser Balken aus Ihren Augen ein. Verwandeln Sie Feinde in Stein gemeißelt oder einfrieren. Verwenden Sie Ihre Vision Röntgen Gebäude zu untersuchen. Ihre Vorstellungskraft liegt die Beschränkung!  

- **Ausdrucksbasierte Avatare:** Eye-tracking ausdrucksvoller 3D Avatare unterstützt die Internetsuche mithilfe von live blickbewegungsregistrierung Datum zum Animieren des Avatars die Augen, um anzugeben, was der Benutzer derzeit ausgewertet wird. Darüber hinaus wird mehrere Ausdruckskraft hinzugefügt, durch Hinzufügen von Animoticons und blinkt. 

- **Texteingabe:** Eye-tracking kann als eine interessante Alternative für die Texteingabe mit geringer Leistung verwendet werden, insbesondere wenn schüren oder Hände Ereignislisten als unpraktisch werden. 


## <a name="eye-tracking-api"></a>Eye-Tracking-API
Vor dem Wechsel in die Details für den bestimmten Entwurfsrichtlinien für die Interaktion mit Eye-Blicke, wollen wir kurz auf die Funktionen verweisen, die die HoloLens-2-Augen-nachverfolgung bereitstellt. Die [Eye-Tracking-API](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) über zugegriffen werden kann: `Windows.Perception.People.EyesPose`. Es bietet eine einzelne Eye Blicke-Ray (Blicke Ursprung und Richtung) für Entwickler.
Die nachverfolgung Eye enthält Daten über _30 FPS_.
Die vorhergesagten Eye Blicke liegt innerhalb der Zertifizierungsstelle. 1.0 – 1,5 Grad, die am Ziel in visual Winkel um die tatsächlichen gesucht werden. Wie geringfügige Ungenauigkeiten erwartet werden, sollten Sie für einen gewissen Spielraum, um diesen Wert für die untere Grenze planen. Wir besprechen dies mehr unten. Für Eye-tracking korrekt funktioniert muss jeder Benutzer eine Eye-tracking Benutzer Kalibrierung durchlaufen. 

![Optimale Zielgröße im Abstand von 2 Verbrauchseinheit](images/gazetargeting-size-1000px.jpg)<br>
*Optimale Zielgröße im Abstand von 2 Verbrauchseinheit*


## <a name="eye-gaze-design-guidelines"></a>Richtlinien zum Entwerfen von Eye Blicke
Erstellen eine Aktivität, die schnell Anwendungen verschieben Eye für nutzt, kann eine Herausforderung darstellen. In diesem Abschnitt zusammengefasst wird, die wichtigsten Vorteile und Herausforderungen in Betracht ziehen, wenn Sie Ihre app zu entwerfen. 

### <a name="benefits-of-eye-gaze-input"></a>Vorteile der Eye blickverlaufseingabe
- **Zeigen hohe Geschwindigkeiten.** Die Augen zu Nutze ist der am schnellsten reacting Muskel in unseren Text. 

- **Niedriger Aufwand.** Kaum physische Bewegungen sind erforderlich. 

- **Implicitness.** Häufig von Benutzern als "Beachten Sie beim Lesen" beschrieben, kann Informationen über Bewegungen, die Augen des Benutzers das System zu informieren, die als Ziel der benutzertarife, um mit in Verbindung setzen. 

- **Alternative Eingabekanal.** Eye Blicke kann eine leistungsfähige Unterstützung Eingabe für die Hand und stimme Eingabe Erstellung bereitstellen auf langjähriger Erfahrung von Benutzern, die basierend auf ihre Hand-Augen-Koordinierung.

- **Visual Aufmerksamkeit.** Ein anderer wichtiger Vorteil ist die Möglichkeit, abgeleitet, was eines Benutzers auf Kosten. Diese kann in verschiedenen Anwendungsbereichen, die im Bereich von mehr effektive Auswertung unterschiedlichen Entwürfe, die dadurch intelligenter Benutzeroberflächen und soziale Hinweise für die Remotekommunikation verbessert.

Kurz gesagt, Eye Blicke verwenden, wie eine Eingabe möglicherweise schnell und mühelos kontextbezogene Signal - bietet dies ist besonders effektiv in Kombination mit anderen Eingaben wie z. B. *Voice* und *manuelle* Eingaben an Vergewissern Sie sich die Absicht des Benutzers.


### <a name="challenges-of-eye-gaze-as-an-input"></a>Herausforderungen bei der Eye bestaunen als Eingabe
Mit viel Strom Leistungspotenzial zuständig: Während Eye Blicke verwendet werden kann, um magische Benutzeroberflächen, wie eine Superheld zu erstellen, ist es auch wichtig zu wissen, was es nicht gut mit Konto für diese angemessen ist. Im folgenden wird erörtert einige *Herausforderungen* Konto und zu ihnen zu begegnen, bei der Arbeit mit Eye blickverlaufseingabe berücksichtigen: 

- **Ihre Augen Blicke ist "always on-** dem Moment, die Sie Ihrem Deckel Augen öffnen Ihren Augen langsam fixating in Ihrer Umgebung. Reagieren, die jeder Sie sehen, stellen und Aktionen möglicherweise versehentlich ausgegeben werden, da Sie betrachtet etwas für lange würde eine schlechte Erfahrung.
Aus diesem Grund empfiehlt kombinieren Eye Blicke mit ist eine *voice-Befehl*, *Geste übergeben*, *Schaltflächenklick* oder erweiterte Dwell zum Auslösen der Auswahl eines Ziels.
Diese Lösung ermöglicht es auch für einen Modus, in dem der Benutzer frei ohne die überwältigend Gefühl der auslösenden unfreiwillig etwas gesucht werden kann um. Dieses Problem sollte auch berücksichtigt werden, wenn visual und akustische Feedback zu entwerfen, wenn Sie lediglich ein Ziel untersuchen.
Überlasten Sie den Benutzer mit der unmittelbaren Popout-Auswirkungen und zeigen Sie mit Sounds nicht. Besonderheit ist entscheidend. Einige bewährten Methoden werden für diese weiter unten besprochen beim Sprechen Empfehlungen für den Entwurf.

- **Beobachtung und Steuerelement** Imagine genau ein Foto auf der Pinnwand ausgerichtet werden sollen. Überprüfen Sie zunächst die Rahmen und dessen Umgebung um festzustellen, ob sie gut entspricht. Angenommen Sie, wie Sie dies tun würden, wenn zur gleichen Zeit Sie Ihre Augen Blicke als Eingabe verwenden, um das Bild zu verschieben möchten. Nicht schwierig, WAHR? Hier wird die doppelte Rolle Eye Blicke beschrieben, bei Bedarf sowohl für Eingabe- und Steuerelement. 

- **Lassen Sie vor dem klicken:** Bei einer schnellen Ziel Auswahl Research ergab, dass eines Benutzers Eye Blicke verschieben kann, vor dem Abschluss einer manuellen klicken Sie auf (z. B. eine Airtap). Daher müssen besondere Aufmerksamkeit bis hin zur Synchronisierung des schnelle Eye Blicke Signals mit langsamer Steuerelementeingabe (z. B. Sprach-, praktische, Controller).

- **Kleine Ziele:** Kennen Sie das Gefühl, wenn Sie versuchen, den Text zu lesen, die nur ein wenig zu klein ist, um bequem zu lesen ist? Diese überzustrapazieren Gefühl für die Augen, die dazu führen, Sie es vielleicht leid und Verschlissene fühlen dass, weil Sie versuchen, Ihren Augen zu konzentrieren, die eine bessere Anpassung?
Hierbei handelt es sich um einen Eindruck, die, den Sie bei Auswählen der zu klein Ziele in Ihrer app, die Augen der Zielgruppenadressierung auf Ihre Benutzer aufrufen können.
Für den Entwurf um eine angenehme und wissen, Erfahrung für Benutzer zu erstellen. empfehlen wir Ziele mindestens 2 Grad in visual Winkel, vorzugsweise größer werden soll.

- **Unregelmäßige Eye Blicke Bewegungen** im Auge führen Sie eine schnelle Bewegungen von Fixation, Fixation. Wenn Sie die Überprüfung von Pfaden von aufgezeichneten Eye-Bewegungen betrachten, sehen Sie sich, dass sie unregelmäßige aussehen. Verschieben Sie Ihren Augen schnell und spontane Sprünge im Vergleich zur *Head Blicke* oder *übergeben Bewegungen*.  

- **Verfolgen Zuverlässigkeit:** Eye-tracking Genauigkeit beeinträchtigt ein bisschen Licht ändern, wenn im Auge zu den neuen Bedingungen anpassen.
Während dies nicht unbedingt Ihr app-Design auswirken soll, sollte als die Genauigkeit der oben genannten Einschränkung von 2 Grad liegen. Dies kann bedeuten, dass der Benutzer hat eine andere Kalibrierung ausgeführt. 


### <a name="design-recommendations"></a>Entwurfsempfehlungen
Im folgenden zeigen wir Ihnen Empfehlungen für den bestimmten Entwurf basierend auf der beschriebenen Vorteile und Herausforderungen für Auge bestaunen Eingabe:

1. **Eye Blicke! = Head Blicke:**
    - **Beachten Sie, ob schnelle und gleichzeitig unregelmäßige Eye Bewegungen die eingegebene Aufgabe anpassen:** Während unsere Bewegungen, die schnelle und unregelmäßige Eye hervorragend, Ziele schnell über unsere Sichtfeld auszuwählen sind, ist es weniger geeignet für Aufgaben, die smooth Eingabe herabstürzendes erfordern (z. B. zeichnen oder Umschließungsnetzen Anmerkungen). In diesem Fall sollte manuell oder durch Verweisen Head vorgezogen werden.
  
    - **Vermeiden Sie ein direktes Anfügen an des Benutzers Eye Blicke (z. B. einen Schieberegler oder Cursor).**
Im Falle eines Cursors daher kann dies die "Flucht angenommen hat Cursor" Auswirkungen aufgrund geringfügige abweichungen im projizierten Eye Blicke Signal haben. Bei einem Schieberegler steht in Konflikt es mit der doppelten Rolle steuern den Schieberegler mit Ihren Augen beim möchten auch überprüfen, ob das Objekt am richtigen Speicherort ist. Kurz gesagt, Benutzer schnell überwältigt und abgelenkt, vor allem fühlen sich möglicherweise, wenn das Signal für diesen Benutzer unpräzise ist. 
  
2. **Kombinieren Sie Eye Blicke, mit anderen Eingaben:** Die Integration von Eye-Tracking mit anderen Eingaben, z. B. gestensteuerung, Sprachbefehlen oder betätigen, hat mehrere Vorteile:
    - **Lassen Sie kostenlos Beobachtung:** Angesichts der Tatsache, dass die Hauptrolle des im Auge ist unsere Umgebung zu beobachten, unbedingt ermöglichen Benutzern, um anzuzeigen, ohne dass eine (visuellen, akustische,...) Feedback oder Aktionen. 
    Durch die ET mit einem anderen Eingabesteuerelement kombinieren können, für den Übergang reibungslos zwischen ET Beobachtung und -Steuerelement.
  
    - **Leistungsstarke Kontextanbieter:** Verwenden Informationen zu, in denen der Benutzer wird beim leistungsstarke eines Sprachbefehl ansehen oder Kanäle mühelos die Eingabe in das Feld-der-Ansicht ermöglicht eine Geste für ein manuell ausführen. Dazu gehören: "Put, die es" zu schnell und nahtlos wählen, und positionieren Sie ggf. ein Hologramm in der Szene, indem Sie einfach nur am Ziel und Ziel zu suchen. 

    - **Erforderlich für die Synchronisierung von Multimodale Eingaben ("lassen sich vor dem Klicken Sie auf"-Problem):** Kombinieren schnelle Bewegungen, die Augen komplexere weitere Eingaben verwenden (z. B. lange Sprachbefehle oder gestensteuerung), trägt das Risiko von vor dem Beenden des zusätzlichen Eingabe-Befehls mit Ihre Augen Blicke fortfahren. Wenn Sie Ihre eigenen Benutzereingabe-Steuerelemente (z. B. benutzerdefinierte gestensteuerung) erstellen, stellen Sie daher Sie sicher, dass sich der Einsatz dieser Eingabe- oder ungefähre Dauer zum Abgleichen mit was für ein Benutzer in der Vergangenheit fixated hatte.
    
3. **Feine Feedback für Eye-tracking-Eingabe:** Es ist nützlich, um Feedback bereitzustellen, wenn ein Ziel, (um anzugeben, dass das System erwartungsgemäß arbeitet) betrachtet wird, aber feine beibehalten werden sollen. Sind langsam blending in/out-Highlights von visual oder andere geringfügige Ziel-Verhalten, z. B. langsame Bewegungen ausführen (z. B. etwas erhöht das Ziel) um anzugeben, dass ordnungsgemäß wurde festgestellt, dass der Benutzer auf ein Ziel, sieht jedoch ohne Unterbrechen unnötigerweise aktuellen Workflow des Benutzers ein. 

4. **Vermeiden Sie die Erzwingung von unnatürlichen Eye Bewegungen, die als Eingabe:** Erzwingen Sie keinen Benutzer bestimmte Eye Bewegungen (Blicke Bewegungen) zum Auslösen von Aktionen in Ihrer app ausführen.

5. **Konto für Ungenauigkeiten:** Wir können zwei Arten von Ungenauigkeiten sind für Benutzer bemerkbar: Offset und Jitter. Die einfachste Möglichkeit, die Offsets der Adresse ist zu groß genug Ziele für die Interaktion mit (> 2° in visual Winkel – als Referenz: die Miniaturansicht ist ungefähr 2° in visual Winkel aus, wenn Sie sich Ihre von Arm (1) ein stretching). Dies führt zu folgenden Leitfaden:
    - Erzwingen Sie keinen Benutzer kleine Ziele auswählen: Untersuchung ergab, dass Benutzer die Interaktion als mühelose und magische, wenn Ziele groß genug sind (und das System auch dient beschreiben). Wenn Ziele zu klein sind, wird Benutzern die Benutzeroberfläche als fatiguing und frustrierendes.
    
## <a name="eye-gaze-design-guidelines"></a>Richtlinien zum Entwerfen von Eye Blicke

Mit HoloLens 2 haben wir die großartige Gelegenheit, die Blicke & Commit schneller und besser vertraut zu machen, indem Sie Head Blicke Eye Blicke anstelle. Allerdings Eye Blicke verhält sich sehr unterschiedlich Head Blicke auf bestimmte Weise und enthält daher eine Reihe von einzigartige Herausforderungen bereit. Im Auge bestaunen Entwurfsrichtlinien zusammengefasst wird allgemein Vorteile und Herausforderungen in Betracht ziehen, wenn Eye-Tracking als eine Eingabe Mittel in Ihrer app holographic verwenden. In diesem Abschnitt liegt der Schwerpunkt auf die spezifische Überlegungen zu lösungsentwürfen für Auge Blicke & Commit. Zunächst unser Auge unglaublich schnell zu verschieben und somit auch sehr schnell über die Ansicht als Ziel. Dadurch wird die Augen bestaunen ideal für schnelle Blicke & commit Aktionen vor allem zusammen mit schnellen Commits wie z. B. eine tippbewegung oder eine Schaltfläche drücken.

Einen Cursor werden nicht angezeigt werden: Es nahezu unmöglich, Sie interagieren zwar bestaunen ohne einen Cursor, wenn Head verwenden, der Cursor wird schnell zu allgemeiner Ablenkung und es ziemlich ärgerlich Verwendung Eye Blicke. Statt eines Cursors für den Benutzer zu informieren, ob Eye-tracking arbeitet und wurde ordnungsgemäß ermittelt derzeit suchenden am Ziel werden geringfügige Visual verwenden (Weitere Details folgen).

Streben Sie nach einer feine kombinierten Hover-Feedback: Scheinbar hervorragende visuelles Feedback für Head Blicke kann dazu führen, dass terrible, überwältigend-Erfahrungen, die mit Eye Blicke. Denken Sie daran, dass Ihre Augen überaus schnell und schnell für Punkte in Ihre Feldansicht darting sind. Schnelle plötzliche Hervorhebung Änderungen (ein/aus) können bei der Suche um flickery Feedback führen. Also beim Zeigen Sie Feedback Wir empfiehlt sich, eine Markierung reibungslos gemischt-in (und kombiniert wird, wenn sofort suchen). Dies bedeutet, dass auf den ersten Sie kaum das Feedback bemerken würden bei Betrachtung von einem Ziel. Im Verlauf von 500-1000 ms würde die Hervorhebung an Intensität erhöhen. Während der Benutzer konnte Ausschau zu halten, an das Ziel aus, um sicherzustellen, dass das System das fokussierte Ziel ordnungsgemäß erkannt wurde, können erfahrene Benutzer schnell bestaunen & Commit ausgeführt, ohne zu warten, bis das Feedback ist für die höchste Intensität. Darüber hinaus empfehlen wir Ihnen ebenfalls ein Blend-Out verwenden, wenn sich das Feedback gezeigt wird eingeblendet. Research hat gezeigt, dass schnelle Bewegungen und Kontrast Änderungen äußerst bemerkenswerten in Ihre peripheren Vision (also den Bereich des Felds Visual, in denen Sie nicht angezeigt wird). Das Ausblenden der videoüberlagerung benötigt keine so langsam wie die Blend-in zu sein. Dies ist nur wichtig, wenn hoher Kontrast oder farbänderungen für die hervorhebungs-wurden. Wenn das Feedback gezeigt wird zunächst sehr komplex war, wird nicht Sie wahrscheinlich einen Unterschied bemerken.

Achten Sie für die Synchronisierung von Blicke und Commit-Signale: Die Synchronisierung von Eingabe signalisiert ist möglicherweise kein großes Problem für einfache Blicke & Commit-, also, keine Sorge! Es ist etwas zu beachten müssen, sollten Sie kompliziertere Commit-Aktionen verwenden, obwohl, lange Sprachbefehle oder komplizierte gestensteuerung beinhalten kann. Angenommen Sie, Sie sehen Sie sich Ziel und einen lange Sprachbefehl Ramsch. Berücksichtigt die Zeit, die Sie benötigen, zu sprechen und die Zeit, die das System erkennen, was Sie gesagt werden musste, wurde Ihre Augen Blicke lange in der Regel einige neue Ziel in der Szene verschoben auf. Daher müssen Sie entweder Ihre Benutzer Beachten Sie, dass sie möglicherweise müssen an ein Ziel Ausschau zu halten, bis der Befehl erkannt wurde oder verarbeiten die Eingabe in eine Methode zum Bestimmen der Einsatz des Befehls und was der Benutzer am damals gesucht habe.

## <a name="see-also"></a>Siehe auch
* [Anvisieren mit dem Kopf und Ausführen](gaze-and-commit.md)
* [Gesten](gestures.md)
* [Sprachbefehle](voice-design.md)
* [Motion-Controller](motion-controllers.md)
* [Komfort](comfort.md)
