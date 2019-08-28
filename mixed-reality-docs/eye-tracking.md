---
title: Augenblick
description: Hololens 2 ermöglicht ein neues Maß an Kontext und menschliches Verständnis in der holografischen Benutzerfreundlichkeit, indem Entwicklern die Möglichkeit geboten wird, Informationen zu den Benutzern zu verwenden, die von Benutzern untersucht werden.
author: sostel
ms.author: sostel
ms.date: 04/05/2019
ms.topic: article
keywords: Augen Verfolgung, gemischte Realität, Eingabe, Augenblick, Augenblick
ms.openlocfilehash: 6c51e1cdc2057142f47b6f96e8a1f1aec0bbcc17
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047107"
---
# <a name="eye-gaze-on-hololens-2"></a>Blick auf hololens 2
Hololens 2 ermöglicht ein neues Maß an Kontext und menschliches Verständnis in der holografischen Benutzerfreundlichkeit, indem Entwicklern die Möglichkeit geboten wird, Informationen zu den Benutzern zu verwenden, die von Benutzern untersucht werden. Auf dieser Seite erfahren Entwickler, wie Sie von der Eye-Nachverfolgung für verschiedene Anwendungsfälle profitieren können, und worauf Sie achten müssen, wenn Sie auf Augenblick basierende Benutzeroberflächen entwerfen. 


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
     <td>Augenblick</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="use-cases"></a>Anwendungsfälle
Mit der Blickverfolgung können Anwendungen in Echtzeit verfolgen, wohin der Benutzer schaut. In den folgenden Anwendungsfällen werden einige Interaktionen beschrieben, die mit der Eye-Nachverfolgung in gemischter Realität möglich sind.
Beachten Sie, dass das [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) nützlich ist, um einige interessante und leistungsstarke Beispiele für die Verwendung der Eye-Nachverfolgung bereitzustellen, wie z. b. schnelle und mühelose Unterstützung für die Zielauswahl und Automatisches Scrollen durch Text basierend auf das, was der Benutzer sieht. 

### <a name="user-intent"></a>Benutzerabsicht    
Informationen dazu, wo und was ein Benutzer untersucht, bieten einen leistungsstarken **Kontext für andere Eingaben**, wie z. b. Voice, Hands und Controller.
Dies kann für verschiedene Aufgaben verwendet werden.
Dies kann z. b. von schnell und mühelos auf die gesamte Szene **abzielen** , indem Sie einfach ein Hologramm betrachten und "Select" (siehe auch [Kopf-und Commit](gaze-and-commit.md)) oder "put this..." und dann den Speicherort des Benutzers überprüfen. Das – Hologramm und sagen "... vorhanden sind. Beispiele hierfür finden Sie in den Artikeln [Mixed Reality Toolkit – Eye-supported Target Selection](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) (Mixed Reality-Toolkit – Blickgestützte Zielauswahl) und [Mixed Reality Toolkit – Eye-supported Target Positioning](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html) (Mixed Reality-Toolkit – Blickgestützte Zielpositionierung).

Außerdem kann ein Beispiel für die Benutzer Absicht die Verwendung von Informationen zu den Benutzern, die von Benutzern untersucht werden, beinhalten, um die Einbindung von verkörperten virtuellen Agents und interaktiven holograms Beispielsweise können virtuelle Agents verfügbare Optionen und ihr Verhalten basierend auf dem aktuell angezeigten Inhalt anpassen. 

### <a name="implicit-actions"></a>Implizite Aktionen
Die Kategorie der impliziten Aktionen steht in enger Beziehung zur Benutzerabsicht.
Die Idee ist, dass holograms oder Benutzeroberflächen Elemente in einer etwas instinstalen Weise reagieren, die nicht einmal so aussieht, als ob der Benutzer mit dem System interagiert, sondern dass das System und der Benutzer synchron sind. Ein Beispiel hierfür ist ein **auf Augenblick basierender automatischer** Bildlauf, bei dem der Benutzer Text liest, während der Text weiterhin durch einen Bildlauf oder einen Datenfluss synchron mit dem Benutzer angezeigt wird. Ein wichtiger Aspekt hierbei ist, dass sich die Scrollgeschwindigkeit an die Lesegeschwindigkeit des Benutzers anpasst.
Ein weiteres Beispiel sind die **Augen unterstützten Zoom-und Schwenken-** Elemente, bei denen der Benutzer das Gefühl hat, dass er sich genau zu dem befindet, worauf er sich konzentriert Das Auslösen von Zoom und das Steuern der Zoomgeschwindigkeit kann durch die Stimme oder Hand Eingabe gesteuert werden. Dies ist wichtig, um dem Benutzer das Gefühl der Kontrolle zu bieten, ohne dass eine über Überlastung erfolgt. Diese Entwurfs Richtlinien werden im folgenden ausführlicher erläutert. Nach dem vergrößern kann der Benutzer problemlos auf den Kurs einer Straße folgen, um seine Umgebung zu durchsuchen, indem er einfach den Augenblick verwendet.
Demobeispiele für diese Arten von Interaktion finden Sie im Beispiel [Mixed Reality Toolkit – Eye-supported Navigation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) (Mixed Reality-Toolkit – Blickgestützte Navigation).

Zusätzliche Anwendungsfälle für _implizite Aktionen_ können Folgendes umfassen:
- **Intelligente Benachrichtigungen**: Ärgern Sie sich auch jedes Mal, wenn Benachrichtigungen dort angezeigt werden, wohin Sie gerade schauen? Wenn Sie das Konto berücksichtigen, auf das ein Benutzer achten wird, können Sie diese Umgebung verbessern, indem Sie Benachrichtigungen von dem Speicherort der Benutzer auslagern Dadurch werden Ablenkungen eingeschränkt und automatisch geschlossen, sobald der Benutzer das Lesen abgeschlossen hat. 
- **„Aufmerksame“ Hologramme:** Holograms, die bei der Verwendung von auf eine beliebige Weise reagieren. Dies kann von leicht leuchtenden Benutzeroberflächen Elementen bis hin zu einer langsam blühenden Blume zu einem virtuellen Haustier reichen, beginnend mit dem Benutzer oder dem Versuch, den Augenblick des Benutzers nach einem längeren Blick zu vermeiden. Diese Interaktion kann ein interessantes Gefühl der Konnektivität und Zufriedenheit in Ihrer Anwendung darstellen.

### <a name="attention-tracking"></a>Aufmerksamkeitsverfolgung   
Informationen dazu, wo oder was Benutzer sehen, ist ein äußerst leistungsfähiges Tool zum Bewerten der Nutzbarkeit von Entwürfen und zum Erkennen von Problemen in effizienten Workflows. Die Visualisierung und Analyse von Augen Nachverfolgung ist eine gängige Vorgehensweise in verschiedenen Anwendungsbereichen. Mit hololens 2 bieten wir eine neue Dimension für dieses Verständnis, da 3D holograms in realen Kontexten platziert und entsprechend bewertet werden können. Das [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) enthält grundlegende Beispiele für das Protokollieren und Laden von Augen Verfolgungs Daten und deren Visualisierung.

Andere Anwendungen in diesem Bereich können Folgendes umfassen: 
-   **Remote Ansicht für den Augenblick:** Visualisieren Sie, welche Remote Mitarbeiter sich ansehen, um sicherzustellen, dass die Anweisungen ordnungsgemäß verstanden und befolgt werden.
-   **Forschungsstudien zum Benutzerverhalten:** Die Nachverfolgung von Nachrichten kann verwendet werden, um die Art und Weise zu untersuchen, in der Anfänger und Experten Inhalte visuell analysieren, oder wie Ihre Hand-Auge-Koordination für komplexe Aufgaben wie z. b. die Analyse von medizinischen Daten oder betriebsmaschinen funktioniert.
-   **Schulungssimulationen und Leistungsüberwachung:** Üben Sie die Ausführung von Aufgaben, und optimieren Sie diese, indem Sie Engpässe im Ausführungsablauf effektiver identifizieren.
-   **Entwurfsbewertungen, Werbung und Marktforschung:** Die Augen Verfolgung ist ein gängiges Tool für Marktforschung, wenn Sie Website-und Produktentwürfe evaluieren.

### <a name="additional-use-cases"></a>Weitere Anwendungsfälle
- **Spiele:** Wollten Sie jemals übernatürliche Kräfte haben? Hier kommt Ihre Chance! Sie können holograms durch ein-und ansehen. Schießen Sie Laserstrahlen aus Ihren Augen. Verwandeln Sie Feinde in den Stein, oder fixieren Sie Sie. Verwenden Sie Ihren Röntgenblick, um Gebäude zu erkunden. Ihrer Phantasie sind keine Grenzen gesetzt!  

- **Ausdrucksstarke Avatare:** Die Eye-Nachverfolgung hilft bei komplexeren 3D-Avataren durch die Verwendung von Live-Eye-nach Verfolgungs Daten, um die Augen des Avatare zu animieren, die den Inhalt des Benutzers angeben. Außerdem wird durch das Hinzufügen von Blinks weitere Ausdrucksfähigkeit hinzugefügt. 

- **Texteingabe:** Die Eye-Nachverfolgung kann als Alternative für den Text Eintrag mit geringem Aufwand verwendet werden, insbesondere dann, wenn Sprache oder Hände unpraktisch zu verwenden sind. 


## <a name="eye-tracking-api"></a>Blickverfolgungs-API
Bevor wir uns mit den speziellen Entwurfs Richtlinien für die Interaktion mit Blick auf das Auge befassen, möchten wir kurz auf die Funktionen hinweisen, die die hololens 2 Eye Tracker-API Entwicklern bereitstellt. Es stellt einen einzelnen Blick auf den Ursprung und die Richtung des Augenblicks bereit und stellt Daten bei ungefähr _30 Hz_bereit. 

Der vorhergesagte Augenblick liegt innerhalb der Zertifizierungsstelle. 1,0-1,5 Grad im visuellen Winkel um das tatsächliche Ziel. Da geringfügige Ungenauigkeiten zu erwarten sind, sollten Sie einen gewissen Spielraum um diesen unteren Wert einplanen. Dies wird im weiteren Verlauf noch behandelt. Damit die Blickverfolgung exakt funktioniert, muss jeder Benutzer eine Benutzerkalibrierung für seine Blickverfolgung durchlaufen. 

![Optimale Zielgröße im Abstand von 2 Metern](images/gazetargeting-size-1000px.jpg)<br>
*Optimale Zielgröße bei einer Entfernung von 2 Stunden*
<br>
<br>
Der Zugriff auf die [Eye Tracking-API](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) ist über: "Windows. perception. People. eyespose" möglich. 

## <a name="calibration"></a>Energie 
Damit die Blickverfolgung exakt funktioniert, muss jeder Benutzer eine Benutzerkalibrierung für seine Blickverfolgung durchlaufen. Bei hololens 2 wird der Benutzer beim Einrichten des Geräts zur Kalibrierung von visuellen Elementen aufgefordert, indem er den Satz von Fixierungs Zielen ansieht. Dies ermöglicht es dem Gerät, das Gerät für eine bequeme und qualitativ hochwertige Anzeige für den Benutzer anzupassen und gleichzeitig eine genaue Eye-Nachverfolgung sicherzustellen.  Die Kalibrierung sollte für die meisten Benutzer funktionieren, aber es gibt Fälle, in denen der Benutzer möglicherweise nicht in der Lage ist, die Kalibrierung erfolgreich durchzusetzen.  Weitere Informationen zur Kalibrierung finden Sie unter [Kalibrierung](https://docs.microsoft.com/en-us/windows/mixed-reality/calibration).

## <a name="eye-gaze-design-guidelines"></a>Entwurfs Richtlinien für den Augenblick
Das Entwickeln einer Interaktion, die die schnelle Ziel Ausrichtung nutzt, kann eine Herausforderung darstellen. In diesem Abschnitt werden die wichtigsten Vorteile und Herausforderungen zusammengefasst, die beim Entwerfen Ihrer Anwendung zu beachten sind. 

### <a name="benefits-of-eye-gaze-input"></a>Vorteile der Eingabe für den Augenblick
- **Zeigen mit hoher Geschwindigkeit.** Der Augenschein ist der schnellste reagierende Muskel im menschlichen Körper. 

- **Wenig Aufwand.** Es sind kaum physische Bewegungen erforderlich. 

- **Selbstverständlichkeit.** Häufig von Benutzern als "Gedanken Lesevorgang" beschrieben, kann das System anhand der Informationen über die Augenbewegungen eines Benutzers erkennen, welche Ziele der Benutzer einbindet. 

- **Alternativer Eingabekanal.** Der Augenblick kann eine leistungsstarke, unterstützende Eingabe für Hand-und Spracheingaben bereitstellen, die auf der Grundlage ihrer Hand-Auge-Koordination von Benutzern entwickelt wurden.

- **Visuelle Aufmerksamkeit.** Ein weiterer wichtiger Vorteil ist die Möglichkeit, zu ableiten, worauf ein Benutzer achten soll. Dies kann in verschiedenen Anwendungsbereichen hilfreich sein, von der effektiveren Auswertung verschiedener Entwürfe bis hin zu intelligenteren Benutzeroberflächen und erweiterten sozialen Netzwerken für die Remote Kommunikation.

Kurz gesagt: die Verwendung von Eye-Blick als Eingabe bietet ein schnelles und mühelose Kontext Signal. Dies ist insbesondere in Kombination mit anderen Eingaben, wie z. b. *Voice* und *manueller* Eingabe, zur Bestätigung der Absicht des Benutzers sehr leistungsstark


### <a name="challenges-of-eye-gaze-as-an-input"></a>Herausforderungen des Augenblicks als Eingabe
Mit einer großen Menge von Energie.
Wenngleich der Augenblick verwendet werden kann, um zufriedenstellende Benutzeroberflächen zu erstellen, die Ihnen einen Superhelden vermitteln, ist es auch wichtig zu wissen, was für dieses nicht geeignet ist. Im folgenden werden einige *Probleme* erläutert, die berücksichtigt werden müssen, und es wird erläutert, wie Sie bei der Arbeit mit Augenblick Eingaben behandelt werden: 

- **Ihr Blick ist "Always on"** . In dem Moment, in dem Sie Ihre Augen Deckeln öffnen, beginnen Ihre Augen damit, die Dinge in der Umgebung zu fixieren. Wenn Sie auf jede Art und Weise reagieren, die Sie durchführen, und versehentlich Aktionen ausgeben, weil Sie etwas zu lange untersucht haben, würde dies zu einer unkomplizierten
Daher empfiehlt es sich, den Augenblick mit einem *Sprachbefehl*, einer *Handbewegung*, einem *Schaltflächen Klick* oder einem erweiterten Wohnort zu kombinieren, um die Auswahl eines Ziels zu initiieren.
Diese Lösung ermöglicht außerdem einen Modus, in dem der Benutzer sich ohne überdies durch eine unwillkürlich Auslösung von etwas bewegen kann. Dieses Problem sollte auch beim Entwerfen von visuellem und auditiven Feedback berücksichtigt werden, wenn Sie nur ein Ziel betrachten.
Überfordern Sie den Benutzer nicht mit sofortigen Popup-Effekten oder Sounds beim kurzen Verweilen auf einem Ziel. Die Feinheit ist der Schlüssel. Weiter unten werden im Zusammenhang mit den Entwurfsempfehlungen einige bewährte Methoden hierfür erläutert.

- **Überwachung und Steuerung** Stellen Sie sich vor, dass Sie ein Foto genau auf Ihre Wand ausrichten möchten. Sie schauen zuerst auf den Rahmen und dann auf die Umgebung, um festzustellen, ob es richtig ausgerichtet ist. Stellen Sie sich nun vor, wie Sie dies tun würden, wenn Sie den Blick als Eingabe zum Verschieben des Bilds verwenden möchten. Schwierig, nicht wahr? Dies beschreibt die doppelte Rolle des Augenblicks, wenn Sie sowohl für die Eingabe als auch für die Steuerung erforderlich ist. 

- **Abwenden vor dem Klicken:** Für eine schnelle Zielauswahl hat Research gezeigt, dass der Augenblick eines Benutzers fortfahren kann, bevor ein manueller Klick (z. b. eine airtap) abgeschlossen wird. Daher muss besonders darauf geachtet werden, dass das schnelle Eye-Eye-Signal mit einer langsameren Steuerungs Eingabe (z. b. Voice, Hands, Controller) synchronisiert wird.

- **Kleine Ziele:** Wissen Sie das Gefühl, wenn Sie versuchen, Text zu lesen, der nur etwas zu klein ist, um bequem lesbar zu sein? Diese Überlastung kann dazu führen, dass Sie müde und ausgegraut sind, da Sie versuchen, Ihre Augen besser zu fokussieren.
Dies ist ein Gefühl, das Sie in Ihren Benutzern aufrufen können, wenn Sie erzwingen, dass Sie Ziele auswählen, die in Ihrer Anwendung mit der Ziel Ausrichtung zu klein sind.
Damit Sie für Ihre Benutzer eine angenehme und komfortable Erfahrung schaffen, sollte bei Zielen für Ihren Entwurf der Sehwinkel mindestens 2 Grad (vorzugsweise mehr) betragen.

- Unregelmäßige **Augenblicke Bewegungen** Unsere Augen führen zu schnellen Bewegungen von der Fixierung bis zur Fixierung. Wenn Sie Scanwege aufgezeichneter Blickbewegungen betrachten, können Sie die Flatterhaftigkeit erkennen. Unsere Augen bewegen sich gegenüber dem *Anvisieren mit dem Kopf* oder *Handbewegungen* schnell und springen spontan hin und her.  

- **Zuverlässigkeit der Verfolgung:** Die Genauigkeit der Blickverfolgung wird ein wenig bei sich ändernden Lichtverhältnissen beeinträchtigt, während sich das Auge an die neuen Bedingungen anpasst.
Dies sollte sich nicht notwendigerweise auf den Entwurf Ihrer Anwendung auswirken, da die Genauigkeit innerhalb der Begrenzung von 2 ° liegen sollte, ist es möglicherweise erforderlich, dass der Benutzer erneut eine Kalibrierung durchführe. 


## <a name="design-recommendations"></a>Entwurfsempfehlungen
Im folgenden finden Sie eine Liste mit spezifischen Entwurfs Empfehlungen, die auf den beschriebenen Vorteilen und Herausforderungen für die Augenblick Eingabe basieren:

1. **Der Augenblick ist nicht der gleiche wie der Haupt Blick:**
    - **Überlegen Sie, ob schnelle, aber gleichzeitig flatterhafte Blickbewegungen zu der Eingabeaufgabe passen:** Während unsere schnellen und unregelmäßigen Augenbewegungen bei der schnellen Auswahl von Zielen im Sichtbereich sehr nützlich sind, sind Sie für Aufgaben, die Smooth-Eingabe-Bewegungsabläufe erfordern (z. b. das Zeichnen oder einschließen von Anmerkungen), weniger anwendbar. In diesem Fall ist das Zeigen mit Hand oder Kopf zu bevorzugen.
  
    - **Vermeiden Sie, etwas direkt an den Augenblick des Benutzers anzufügen (z. b. einen Schieberegler oder Cursor).**
Bei einem Cursor führt dies möglicherweise zu einem "flüchtig Cursor"-Effekt aufgrund geringfügiger Offsets im projizierten Augenblick Signal. Im Fall eines Schiebereglers kann der Schieberegler mit der doppelten Rolle des Schiebereglers in Konflikt stehen, während gleichzeitig überprüft werden soll, ob sich das Objekt am richtigen Speicherort befindet. Kurz gesagt, können Benutzer überlastet und abgelenkt werden, insbesondere wenn das Signal für diesen Benutzer unpräzise ist. 
  
2. **Kombinieren Sie den Augenblick mit anderen Eingaben:** Die Integration der Eye-Nachverfolgung mit anderen Eingaben, z. b. Handgesten, Sprachbefehle oder Schaltflächen drückt, bietet mehrere Vorteile:
    - **Möglichkeit der freien Betrachtung:** Die Hauptrolle unserer Augen besteht darin, unsere Umgebung zu beobachten. es ist wichtig, dass Benutzer die Möglichkeit haben, sich anzusehen, ohne irgendwelche (visuellen, auditiven usw.) Feedback oder Aktionen auszulösen. 
    Das Kombinieren der Eye-Nachverfolgung mit einem anderen Eingabe Steuerelement ermöglicht einen reibungslosen Übergang zwischen der Überwachung der Augen Verfolgung und den Eingabe
  
    - **Leistungsstarker Kontextanbieter:** Wenn Sie Informationen dazu verwenden, wo und was der Benutzer beim ututing eines sprach Befehls oder beim Ausführen einer Handbewegung sucht, kann die Eingabe nahtlos über das Feld der Ansicht hinweg übertragen werden. Zum Beispiel: Mit „Put that there“ (Auswählen, Verschieben, ...hierhin) können Sie schnell und flüssig ein Hologramm auswählen und über die Szene verschieben. Dazu brauchen Sie nur ein Ziel und den Bestimmungsort anzuschauen. 

    - **Multimodale Eingaben müssen synchronisiert werden (Problem des vor dem Klicken abgewendeten Blicks):** Das Kombinieren von Rapid Eye-Bewegungen mit komplexeren zusätzlichen Eingaben, wie z. b. langen Sprachbefehlen oder Handgesten, birgt das Risiko, dass Sie Ihren Blick vor dem Abschluss des zusätzlichen Eingabe Befehls fortsetzen. Wenn Sie also Ihre eigenen Eingabe Steuerelemente erstellen (z. b. benutzerdefinierte Handgesten), sollten Sie das Auftreten dieser Eingabe oder der ungefähren Dauer protokollieren, um Sie mit dem zu korrelieren, was ein Benutzer in der Vergangenheit eingegeben hat.
    
3. **Dezentes Feedback für Eingaben über die Blickverfolgung:** Es ist hilfreich, Feedback zu geben, wenn ein Ziel untersucht wird, um anzugeben, dass das System wie beabsichtigt funktioniert, aber dennoch gering gehalten werden sollte. Dies kann eine langsame Mischung, ein-und ausgehende, visuelle Highlights oder andere, feine Ziel Verhaltensweisen, wie z. b. langsame Bewegungen, z. b. eine geringfügige Erhöhung der Zielgröße, beinhalten, um anzugeben, dass das System ordnungsgemäß erkannt hat, dass der Benutzer ein Ziel unnötiges unterbrechen des aktuellen Workflows des Benutzers. 

4. **Vermeiden des Erzwingens unnatürlicher Augenbewegungen für die Eingabe:** Erzwingen Sie nicht, dass Benutzer bestimmte Augenbewegungen (Augenbewegungen) ausführen, um Aktionen in der Anwendung zu initiieren.

5. **Berücksichtigen von Ungenauigkeiten:** Wir unterscheiden zwei Arten von imsions, die für die Benutzer bemerkbar sind: Offset und Jitter. Die einfachste Möglichkeit, einen Offset zu behandeln, besteht darin, ausreichend große Ziele für die Interaktion bereitzustellen. Es wird empfohlen, einen visuellen Winkel größer als 2 ° als Verweis zu verwenden. Beispielsweise ist die Miniaturansicht ungefähr 2 ° im visuellen Winkel, wenn Sie den Arm ausdehnen. Dies führt zu folgender Richtlinie:
    - Erzwingen Sie nicht, dass Benutzer kleine Ziele auswählen. Die Untersuchung hat ergeben, dass die Interaktionen, wenn die Ziele ausreichend groß sind und das System gut entworfen wurde, mühelos und magisch beschrieben werden. Wenn Ziele zu klein sind, empfinden Benutzer die Erfahrung als ermüdend und frustrierend.
   

## <a name="see-also"></a>Siehe auch
* [Anvisieren mit dem Kopf und Ausführen](gaze-and-commit.md)
* [Kopf-und Augenblick in DirectX](gaze-in-directx.md)
* [Blick in Unity (Mixed Reality Toolkit)](https://aka.ms/mrtk-eyes)
* [Kalibrierung](https://docs.microsoft.com/en-us/windows/mixed-reality/calibration)
* [Handgesten](gestures.md)
* [Spracheingabe](voice-design.md)
* [Motion-Controller](motion-controllers.md)
* [Komfort](comfort.md)
