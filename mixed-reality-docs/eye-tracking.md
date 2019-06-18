---
title: Eyetracking – Blickverfolgung
description: Eyetracking – Blickverfolgung
author: sostel
ms.author: sostel
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Eyetracking, Blickverfolgung, Mixed Reality, Eingabe, Anvisieren mit den Augen
ms.openlocfilehash: 7298a34a946f86aaf789cfe44ad971169fc8ece3
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66453699"
---
# <a name="eye-tracking-on-hololens-2"></a>Blickverfolgung auf HoloLens 2
Mit HoloLens 2 erschließt sich in Bezug auf Kontext und menschliches Verständnis eine ganz neue Ebene der holografischen Erfahrung. Das Gerät bietet Entwicklern nämlich die unglaubliche Möglichkeit, Informationen zur Zielanvisierung mit den Augen und zur Blickbewegung des Benutzers zu verwenden. Diese Seite gibt einen Überblick darüber, wie Entwickler bei verschiedenen Anwendungsfällen von der Blickverfolgung profitieren können und was sie beim Entwerfen von Benutzeroberflächen beachten müssen, bei denen das Anvisieren mit den Augen die Grundlage bildet. 

## <a name="use-cases"></a>Anwendungsfälle
Mit der Blickverfolgung können Anwendungen in Echtzeit verfolgen, wohin der Benutzer schaut. In diesem Abschnitt werden einige mögliche Anwendungsfälle und neuartige Interaktionen beschrieben, die in der Mixed Reality-Umgebung mit der Blickverfolgung möglich sind.
Bevor Sie beginnen: Im Folgenden wird mehrmals der [Mixed Reality-Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) erwähnt, da mit ihm mehrere interessante und leistungsfähige Beispiele für die Blickverfolgung bereitgestellt werden, wie beispielsweise die schnelle und mühelose blickgestützte Zielauswahl und das automatische Scrollen durch Text anhand des Blickverlaufs des Benutzers. 

### <a name="user-intent"></a>Benutzerabsicht    
Die Informationen zu den Punkten, auf die der Benutzer schaut, bilden einen leistungsfähigen **Kontext für andere Eingaben** (z.B. Sprach- und Handeingaben und Eingaben über den Controller).
Dies kann für verschiedene Aufgaben verwendet werden.
Das beginnt beispielsweise bei der schnellen und mühelosen **Zieladressierung** in der Szene, indem der Benutzer einfach ein Hologramm anvisiert und „Auswählen“ sagt (siehe auch [Anvisieren mit dem Kopf und Ausführen](gaze-and-commit.md)). Oder der Benutzer sagt „Auswählen, Verschieben“, visiert dann den Punkt an, an dem das Hologramm platziert werden soll, und sagt „...hierhin“. Beispiele hierfür finden Sie in den Artikeln [Mixed Reality Toolkit – Eye-supported Target Selection](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) (Mixed Reality-Toolkit – Blickgestützte Zielauswahl) und [Mixed Reality Toolkit – Eye-supported Target Positioning](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html) (Mixed Reality-Toolkit – Blickgestützte Zielpositionierung).

Ein weiteres Beispiel für die Benutzerabsicht ist beispielsweise die Nutzung der Informationen zu den Punkten, auf die ein Benutzer schaut, um den Einsatz der enthaltenen virtuellen Agents und interaktiven Hologramme zu verbessern. Virtuelle Agents können beispielsweise die verfügbaren Optionen und deren Verhalten anhand des aktuell anvisierten Inhalts anpassen. 

### <a name="implicit-actions"></a>Implizite Aktionen
Die Kategorie der impliziten Aktionen steht in enger Beziehung zur Benutzerabsicht.
Die Idee ist, dass Hologramme oder Elemente der Benutzeroberfläche auf eine mehr instinktive Art und Weise reagieren, wodurch vielleicht nicht einmal der Eindruck entsteht, dass der Benutzer mit dem System interagiert, sondern dass System und Benutzer synchron arbeiten. Ein besonders erfolgreiches Beispiel hierfür ist das **automatische Scrollen durch Anvisieren mit den Augen**. Die Idee ist einfach: Der Benutzer liest einen Test und kann einfach weiter lesen. Der Text verschiebt sich allmählich nach oben, um den Lesefluss des Benutzers zu unterstützen. Ein wichtiger Aspekt ist, dass sich die Scrollgeschwindigkeit an die Lesegeschwindigkeit des Benutzers anpasst.
Ein weiteres Beispiel ist das **blickgestützte Zoomen und Schwenken**, bei dem der Benutzer das Gefühl hat, genau in das einzutauchen, worauf er sich konzentriert. Das Auslösen des Zoomvorgangs und das Steuern der Zoomgeschwindigkeit kann über Sprach- oder Handeingaben erfolgen, was wichtig ist, um dem Benutzer ein Gefühl der Kontrolle zu vermitteln und eine Überforderung zu vermeiden (diese Entwurfsrichtlinien werden im Detail weiter unten behandelt). Nach dem Vergrößern kann der Benutzer dann nahtlos durch Anvisieren mit den Augen zum Beispiel einem Straßenverlauf folgen und seine Umgebung erkunden.
Demobeispiele für diese Arten von Interaktion finden Sie im Beispiel [Mixed Reality Toolkit – Eye-supported Navigation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) (Mixed Reality-Toolkit – Blickgestützte Navigation).

Weitere Anwendungsfälle für _implizite Aktionen_:
- **Intelligente Benachrichtigungen**: Ärgern Sie sich auch jedes Mal, wenn Benachrichtigungen dort angezeigt werden, wohin Sie gerade schauen? Wenn Sie berücksichtigen, worauf die Aufmerksamkeit eines Benutzers gerichtet ist, können Sie es besser machen! Zeigen Sie Benachrichtigungen mit einem Offset von der Stelle an, auf die der Benutzer aktuell schaut, um Ablenkungen auf ein Minimum zu beschränken. Schließen Sie die Benachrichtigungen automatisch, nachdem der Benutzer sie zu Ende gelesen hat. 
- **„Aufmerksame“ Hologramme:** Hologramme können fast unmerklich reagieren, wenn sie angeschaut werden. Dies können leicht erglühende Oberflächenelemente, eine langsam erblühende Blume oder ein virtuelles Haustier sein, das beginnt, Ihren Blick zu erwidern, oder das nach einer Weile des Anvisierens den Blick abwendet. Dies kann in Ihrer App zu einem interessanten Gefühl von Verbundenheit und Zufriedenheit führen.

### <a name="attention-tracking"></a>Aufmerksamkeitsverfolgung   
Informationen zu den Punkten, auf die der Benutzer schaut, stellen ein unglaublich leistungsfähiges Tool zur Bewertung der Benutzerfreundlichkeit von Designs und zum Identifizieren von Problemen in effizienten Arbeitsabläufen dar. Mittlerweile sind Visualisierung und Analyse mittels Blickverfolgung in verschiedenen Anwendungsbereichen bereits gängige Praxis. Mit HoloLens 2 stellen wir eine neue Dimension für diese Grundlagen bereit, da 3D-Hologramme in reale Kontexte platziert und parallel mit diesen bewertet werden können. Der [Mixed Reality-Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) enthält grundlegende Beispiele für das Protokollieren und Laden von Blickverfolgungsdaten sowie für das Visualisieren dieser Daten.

Zu diesem Bereich zählen möglicherweise auch die folgenden Anwendungen: 
-   **Visualisieren des entfernten Anvisierens mit den Augen:** Visualisieren Sie, worauf entfernte Projektmitarbeiter schauen, um z.B. sicherzustellen, dass Anweisungen richtig verstanden und befolgt werden.
-   **Forschungsstudien zum Benutzerverhalten:** Anhand der Aufmerksamkeitsverfolgung kann untersucht werden, wie unerfahrene Benutzer im Vergleich zu erfahrenen Benutzern Inhalte visuell analysieren oder bei komplexen Aufgaben (z.B. Analyse medizinischer Daten oder beim Betrieb von Maschinen) die Hand-/Augeninteraktion koordinieren.
-   **Schulungssimulationen und Leistungsüberwachung:** Üben Sie die Ausführung von Aufgaben, und optimieren Sie diese, indem Sie Engpässe im Ausführungsablauf effektiver identifizieren.
-   **Entwurfsbewertungen, Werbung und Marktforschung:** Die Blickverfolgung ist ein gängiges Tool für die Marktforschung, um Website -und Produktentwürfe zu bewerten.

### <a name="additional-use-cases"></a>Weitere Anwendungsfälle
- **Spiele:** Wollten Sie jemals übernatürliche Kräfte haben? Hier kommt Ihre Chance! Lassen Sie Hologramme durch Anvisieren frei schweben. Schießen Sie Laserstrahlen aus Ihren Augen. Verwandeln Sie Feinde in Stein, oder frieren Sie sie ein. Verwenden Sie Ihren Röntgenblick, um Gebäude zu erkunden. Ihrer Phantasie sind keine Grenzen gesetzt!  

- **Ausdrucksstarke Avatare:** Die Blickverfolgung ermöglicht ausdrucksvollere 3D-Avatare. Mithilfe der Blickverfolgungsdaten in Echtzeit lassen sich die Augen des Avatars so animieren, dass sie darauf hinweisen, worauf der Benutzer aktuell schaut. Durch zusätzliches Zwinkern und Blinzeln wird außerdem mehr Ausdruckskraft erzielt. 

- **Texteingabe:** Die Blickverfolgung kann als interessante Alternative für eine Texteingabe mit wenig Aufwand verwendet werden, besonders wenn die Benutzung von Sprache oder Händen unpraktisch ist. 


## <a name="eye-tracking-api"></a>Blickverfolgungs-API
Bevor wir zu den Einzelheiten der speziellen Entwurfsrichtlinien für die Interaktion durch Anvisieren mit den Augen kommen, möchten wir kurz auf die Funktionen eingehen, über die der Eyetracker von HoloLens 2 verfügt. Auf die [Blickverfolgungs-API](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) kann über `Windows.Perception.People.EyesPose` zugegriffen werden. Sie stellt Entwicklern einen einzelnen Lichtstrahl zum Anvisieren mit den Augen (Anvisierursprung und -richtung) bereit.
Der Blickverfolger (Eyetracker) stellt Daten mit einer Bildfrequenz von etwa _30 FPS_ bereit.
Das prognostizierte Anvisieren mit den Augen liegt in einem Sehwinkel von ca. 1,0-1,5 Grad um das tatsächlich anvisierte Ziel. Da geringfügige Ungenauigkeiten zu erwarten sind, sollten Sie einen gewissen Spielraum um diesen unteren Wert einplanen. Dies wird im weiteren Verlauf noch behandelt. Damit die Blickverfolgung exakt funktioniert, muss jeder Benutzer eine Benutzerkalibrierung für seine Blickverfolgung durchlaufen. 

![Optimale Zielgröße im Abstand von 2 Metern](images/gazetargeting-size-1000px.jpg)<br>
*Optimale Zielgröße im Abstand von 2 Metern*


## <a name="eye-gaze-design-guidelines"></a>Entwurfsrichtlinien für das Anvisieren mit den Augen
Das Erstellen einer Interaktion, welche die schnelle und bewegliche Zieladressierung mit den Augen nutzt, kann eine Herausforderung darstellen. In diesem Abschnitt sind die wichtigsten Vorteile und Herausforderungen zusammengefasst, die Sie beim Entwerfen Ihrer App berücksichtigen sollten. 

### <a name="benefits-of-eye-gaze-input"></a>Vorteile der Eingabe durch Anvisieren mit den Augen
- **Zeigen mit hoher Geschwindigkeit.** Der Augenmuskel ist der am schnellsten reagierende Muskel in unserem Körper. 

- **Wenig Aufwand.** Es sind kaum physische Bewegungen erforderlich. 

- **Selbstverständlichkeit.** Informationen zu den Blickbewegungen des Benutzers geben dem System Informationen zu dem Ziel, mit dem der Benutzer in Kontakt treten möchte, was häufig von Benutzern als „Gedankenlesen“ bezeichnet wird. 

- **Alternativer Eingabekanal.** Das Anvisieren mit den Augen kann eine leistungsfähige Unterstützung für die Hand- und Spracheingabe darstellen und beruht auf jahrelanger Erfahrung mit der Hand-/Augen-Koordination bei Benutzern.

- **Visuelle Aufmerksamkeit.** Ein weiterer wichtiger Vorteil ist die Möglichkeit, abzuleiten, auf was ein Benutzer seine Aufmerksamkeit richtet. Dies kann in verschiedenen Anwendungsbereichen nützlich sein, angefangen bei der effektiveren Auswertung unterschiedlicher Entwürfe über intelligentere Benutzeroberflächen bis hin zu erweiterten sozialen Hinweisen für die Remotekommunikation.

Kurz gesagt, die Eingabe durch das Anvisieren mit den Augen bietet potenziell ein schnelles und müheloses kontextbezogenes Signal, das besonders in Kombination mit anderen Eingaben wie *Sprach-* und *Hand*eingaben sehr leistungsstark ist, um die Benutzerabsicht zu bestätigen.


### <a name="challenges-of-eye-gaze-as-an-input"></a>Herausforderung bei der Eingabe durch Anvisieren mit den Augen
Mit viel Leistungspotenzial geht eine hohe Verantwortung einher: Auch wenn das Anvisieren mit den Augen zum Erstellen magischer Benutzererfahrungen (der Benutzer fühlt sich wie ein Superheld) verwendet werden kann, ist es wichtig zu wissen, wofür es nicht geeignet ist und dies entsprechend zu berücksichtigen. Im Folgenden werden einige *Herausforderungen*, die bei der Arbeit mit Eingaben durch Anvisieren mit den Augen auftreten und zu beachten sind, erörtert und Lösungsansätze aufgezeigt: 

- **Das Anvisieren mit den Augen ist „immer aktiv“** In dem Moment, in dem Sie das Augenlid öffnen, beginnen Ihre Augen, Dinge in Ihrer Umgebung zu fixieren. Wenn auf jeden Ihrer Blicke eine Reaktion erfolgte und Sie möglicherweise versehentlich Aktionen auslösten, da Sie etwas zu lange betrachtet haben, wäre dies eine erschreckende Erfahrung!
Aus diesem Grund empfehlen wir, das Anvisieren mit den Augen mit einem *Sprachbefehl*, einer *Handgeste*, dem *Anklicken einer Schaltfläche* oder einer verlängerten Verweilzeit zu kombinieren, um die Auswahl eines Ziels auszulösen.
Diese Lösung ermöglicht auch einen Modus, in dem der Benutzer frei umherschauen kann, ohne das erdrückende Gefühl haben zu müssen, versehentlich etwas auszulösen. Dieses Problem sollte auch beim Entwerfen von visuellem und akustischem Feedback berücksichtigt werden, wenn der Benutzer lediglich ein Ziel anschaut.
Überfordern Sie den Benutzer nicht mit sofortigen Popup-Effekten oder Sounds beim kurzen Verweilen auf einem Ziel. „Dezent“ ist das Mittel der Wahl! Weiter unten werden im Zusammenhang mit den Entwurfsempfehlungen einige bewährte Methoden hierfür erläutert.

- **Betrachten und Steuern** Stellen Sie sich vor, Sie möchten ein Bild an der Wand genau ausrichten. Sie schauen zuerst auf den Rahmen und dann auf die Umgebung, um festzustellen, ob es richtig ausgerichtet ist. Stellen Sie sich jetzt vor, wie Sie vorgehen würden, wenn Sie das Anvisieren mit Ihren Augen gleichzeitig als Eingabe zum Verschieben des Bilds verwenden möchten. Schwierig, nicht wahr? Dies beschreibt die doppelte Rolle des Anvisierens mit den Augen, wenn es gleichzeitig für Eingabe und Steuerung verwendet wird. 

- **Abwenden vor dem Klicken:** Untersuchungen haben gezeigt, dass sich bei der schnellen Zielauswahl der Blick des Benutzers möglicherweise bereits vor dem Ausführen eines manuellen Klicks (z.B. Tippen in die Luft) abgewendet hat. Daher ist bei der Synchronisierung des schnellen Blicksignals beim Anvisieren mit den Augen mit der langsameren Steuereingabe (z.B. Sprach- oder Handbefehl, Eingabe über Controller) besondere Aufmerksamkeit geboten.

- **Kleine Ziele:** Kennen Sie das Gefühl, wenn Sie versuchen, einen Text zu lesen, der nur ein wenig zu klein ist, um ihn bequem lesen zu können? Dieses Gefühl überstrapazierter Augen, das dazu führt, dass Sie sich ermüdet und gestresst fühlen, weil Sie versuchen, Ihre Augen neu zu justieren, um besser fokussieren zu können?
Dieses Gefühl rufen Sie möglicherweise bei Ihren Benutzern hervor, wenn Sie diese zwingen, bei der Zieladressierung mit den Augen zu kleine Ziele auszuwählen.
Damit Sie für Ihre Benutzer eine angenehme und komfortable Erfahrung schaffen, sollte bei Zielen für Ihren Entwurf der Sehwinkel mindestens 2 Grad (vorzugsweise mehr) betragen.

- **Flatterhafte Blickbewegungen** Unsere Augen vollführen von Fixierung zu Fixierung schnelle Bewegungen. Wenn Sie Scanwege aufgezeichneter Blickbewegungen betrachten, können Sie die Flatterhaftigkeit erkennen. Unsere Augen bewegen sich gegenüber dem *Anvisieren mit dem Kopf* oder *Handbewegungen* schnell und springen spontan hin und her.  

- **Zuverlässigkeit der Verfolgung:** Die Genauigkeit der Blickverfolgung wird ein wenig bei sich ändernden Lichtverhältnissen beeinträchtigt, während sich das Auge an die neuen Bedingungen anpasst.
Dies wirkt sich jedoch nicht unbedingt auf Ihr App-Design aus, da die Genauigkeit innerhalb der oben beschriebenen Grenze von 2 Grad liegen sollte. Dies kann bedeuten, dass der Benutzer hat eine weitere Kalibrierung ausführen muss. 


### <a name="design-recommendations"></a>Entwurfsempfehlungen
Nachfolgend finden Sie auf Grundlage der beschriebenen Vorteile und Herausforderungen spezielle Entwurfsempfehlungen für die Eingabe durch Anvisieren mit den Augen:

1. **„Anvisieren mit den Augen“ unterscheidet sich vom „Anvisieren mit dem Kopf“:**
    - **Überlegen Sie, ob schnelle, aber gleichzeitig flatterhafte Blickbewegungen zu der Eingabeaufgabe passen:** Während sich schnelle und flatterhafte Blickbewegungen hervorragend für die Auswahl von Zielen im Sichtfeld eignen, sind sie für Aufgaben, die gleichmäßige Eingabeverläufe verlangen (z.B. Zeichnen oder Einkreisen von Bemerkungen) weniger geeignet. In diesem Fall ist das Zeigen mit Hand oder Kopf zu bevorzugen.
  
    - **Vermeiden Sie ein direktes Anfügen von Objekten (z. B. Schieberegler oder Cursor) an den Blickverlauf des Benutzers.**
Bei einem Cursor kann durch den leichten Offset im projizierten Blicksignal der Effekt des „fliehenden Cursors“ entstehen. Bei einem Schieberegler ergeben sich Konflikte mit der Doppelrolle. Sie möchten einerseits den Schieberegler mit Ihren Augen steuern, gleichzeitig aber auch prüfen, ob sich das Objekt an der richtigen Stelle befindet. Kurz gesagt, der Benutzer kann sich schnell überfordert und abgelenkt fühlen, vor allem, wenn das Signal für diesen Benutzer ungenau ist. 
  
2. **Kombinieren Sie das Anvisieren mit den Augen mit anderen Eingaben:** Die Integration der Blickverfolgung mit anderen Eingaben (z.B. Gesten, Sprachbefehle oder Drücken von Schaltflächen) hat mehrere Vorteile:
    - **Möglichkeit der freien Betrachtung:** Angesichts der Tatsache, dass die Hauptrolle der Augen die Betrachtung der Umgebung ist, ist es wichtig, dem Benutzer die Möglichkeit zu geben, sich umzuschauen, ohne ein Feedback (visuell, akustisch usw.) oder eine Aktion auszulösen. 
    Durch die Kombination der Blickverfolgung mit einer anderen Eingabesteuerung ermöglichen Sie einen sanften Übergang zwischen den Blickverfolgungsmodi der freien Betrachtung und der Eingabesteuerung.
  
    - **Leistungsstarker Kontextanbieter:** Mit den Informationen zu den Punkten, auf die der Benutzer bei der Ausgabe eines Sprachbefehls oder der Ausführung einer Handgeste schaut, können Sie die Eingabe mühelos über das Sichtfeld übermitteln. Beispiele: Mit „Put that there“ (Auswählen, Verschieben, ...hierhin) können Sie schnell und flüssig ein Hologramm auswählen und über die Szene verschieben. Dazu brauchen Sie nur ein Ziel und den Bestimmungsort anzuschauen. 

    - **Multimodale Eingaben müssen synchronisiert werden (Problem des vor dem Klicken abgewendeten Blicks):** Die Kombination schneller Blickbewegungen mit komplexeren weiteren Eingaben (z.B. lange Sprachbefehle oder Handgesten) birgt das Risiko, dass der Benutzer seinen Blick abwendet, bevor er den zusätzlichen Eingabebefehl abgeschlossen hat. Daher sollten Sie beim Erstellen eigener Eingabesteuerungen (z.B. benutzerdefinierte Handgesten) unbedingt das Einsetzen dieser Eingabe und die ungefähre Dauer protokollieren, um dies auf die Fixierdauer abzustimmen, die Benutzer in der Vergangenheit gezeigt haben.
    
3. **Dezentes Feedback für Eingaben über die Blickverfolgung:** Es ist zwar nützlich, ein Feedback bereitzustellen, wenn ein Ziel anvisiert wird (um anzugeben, dass das System erwartungsgemäß funktioniert), jedoch sollte es dezent gehalten werden. Dazu zählen möglicherweise das langsame Ein- und Ausblenden von visuellen Markierungen oder das fast unmerkliche Verhalten anderer Ziele wie in Zeitlupe (z.B. leichtes Vergrößern des Ziels), um anzugeben, dass das System korrekt das Anvisieren eines Ziels durch den Benutzer erkannt hat, jedoch ohne unnötigerweise den aktuellen Workflow des Benutzers zu unterbrechen. 

4. **Vermeiden des Erzwingens unnatürlicher Augenbewegungen für die Eingabe:** Zwingen Sie Ihre Benutzer nicht, zum Auslösen von Aktionen in Ihrer App bestimmte Augenbewegungen (Fixierbewegungen) auszuführen.

5. **Berücksichtigen von Ungenauigkeiten:** Wir unterscheiden zwei Arten von Ungenauigkeiten, die für den Benutzer wahrnehmbar sind: Offset und Jitter. Die einfachste Möglichkeit zur Behandlung von Offsets ist die Bereitstellung ausreichend großer Ziele für die Interaktion (Sehwinkel >2 ° – Referenz: Ihr Daumennagel befindet sich in einem Sehwinkel von ca. 2 °, wenn Sie den Arm ausstrecken(1)). Dies führt zu folgender Richtlinie:
    - Zwingen Sie Benutzer nicht, kleine Ziele auszuwählen: Untersuchung haben ergeben, dass Benutzer die Interaktion als mühelos und zauberhaft beschreiben, wenn Ziele groß genug sind (und auch das System gut entworfen ist). Wenn Ziele zu klein sind, empfinden Benutzer die Erfahrung als ermüdend und frustrierend.
   

## <a name="see-also"></a>Weitere Informationen
* [Anvisieren mit dem Kopf und Ausführen](gaze-and-commit.md)
* [Anvisieren mit dem Kopf und mit den Augen in DirectX](gaze-in-directx.md)
* [Anvisieren mit den Augen in Unity (Mixed Reality-Toolkit)](https://aka.ms/mrtk-eyes)
* [Handgesten](gestures.md)
* [Spracheingabe](voice-design.md)
* [Motion-Controller](motion-controllers.md)
* [Komfort](comfort.md)
