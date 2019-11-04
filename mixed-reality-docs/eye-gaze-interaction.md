---
title: Auf Augenblick basierende Interaktion
description: Mit HoloLens 2 erschließt sich in Bezug auf Kontext und menschliches Verständnis eine neue Ebene der holografischen Erfahrung. Das Gerät bietet Entwicklern nämlich die Möglichkeit, Informationen zur Zielanvisierung mit den Augen und zur Blickbewegung des Benutzers zu verwenden. Diese Seite enthält Entwurfs Empfehlungen für Entwickler, die den Augenblick als Eingabe verwenden möchten.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: Augen Verfolgung, gemischte Realität, Eingabe, Augenblick
ms.openlocfilehash: 93d2cfd82b5aa2a410268c5594b5772bcc0b21c7
ms.sourcegitcommit: a5dc182da237f63f0487d40a2e11894027208b6c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2019
ms.locfileid: "73441101"
---
# <a name="eye-gaze-based-interaction-on-hololens-2"></a>Auf Augenblick basierende Interaktion auf hololens 2

![Demo zur Eye-Nachverfolgung in mrtk](images/mrtk_et_scenemenu.jpg)

Eine unserer spannenden neuen Funktionen in hololens 2 ist die Augen Verfolgung.
Auf unserer Seite " [Eye Tracking auf hololens 2](eye-tracking.md) " haben wir erwähnt, dass jeder Benutzer eine [Kalibrierung](https://docs.microsoft.com/hololens/hololens-calibration)durchlaufen muss, um einige Entwickler Anleitungen und Anwendungsfälle für die Augen Verfolgung bereitzustellen.
Die Eingabe für den Augenblick ist immer noch eine ziemlich neue Art von Benutzereingaben, und es gibt viel zu erlernen. Wenngleich die Eingabe von Augenblicken nur sehr leicht in unserer Holographic Shell-Oberfläche verwendet wird (die Benutzeroberfläche, die Sie beim Starten der hololens 2 sehen), zeigen mehrere apps, wie z. b. ["Mr Playground"](https://www.microsoft.com/p/mr-playground/9nb31lh723s2), hervor artige Beispiele dazu, wie die Eingabe von Augenblicken der Magie Ihre holografische Darstellung.
Auf dieser Seite werden Entwurfs Überlegungen für die Integration von Eye-Eye-Eingaben für die Interaktion mit ihren Holographic-Anwendungen erläutert.
Sie erfahren mehr über wichtige Vorteile und auch über einzigartige Herausforderungen, die bei der Eingabe des Augenblicks auftreten.  
Basierend auf diesen bieten wir einige Entwurfs Empfehlungen, mit denen Sie zufriedenstellende Benutzeroberflächen erstellen können, die mit Augenblick unterstützt werden. 

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
     <td>Augenblick</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>


## <a name="eye-gaze-input-design-guidelines"></a>Eingabe Entwurfs Richtlinien für den Augenblick
Das Entwickeln einer Interaktion, die die schnelle Ziel Ausrichtung nutzt, kann eine Herausforderung darstellen. In diesem Abschnitt werden die wichtigsten Vorteile und Herausforderungen zusammengefasst, die beim Entwerfen Ihrer Anwendung zu beachten sind. 

### <a name="benefits-of-eye-gaze-input"></a>Vorteile der Eingabe für den Augenblick
- **Zeigen mit hoher Geschwindigkeit.** Der Augenschein ist der schnellste reagierende Muskel im menschlichen Körper. 

- **Wenig Aufwand.** Es sind kaum physische Bewegungen erforderlich. 

- **Selbstverständlichkeit.** Häufig von Benutzern als "Gedanken Lesevorgang" beschrieben, kann das System anhand der Informationen über die Augenbewegungen eines Benutzers erkennen, welche Ziele der Benutzer einbindet. 

- **Alternativer Eingabekanal.** Der Augenblick kann eine leistungsstarke, unterstützende Eingabe für Hand-und Spracheingaben bereitstellen, die auf der Grundlage ihrer Hand-Auge-Koordination von Benutzern entwickelt wurden.

- **Visuelle Aufmerksamkeit.** Ein weiterer wichtiger Vorteil ist die Möglichkeit, zu ableiten, worauf ein Benutzer achten soll. Dies kann in verschiedenen Anwendungsbereichen hilfreich sein, von der effektiveren Auswertung verschiedener Entwürfe bis hin zu intelligenteren Benutzeroberflächen und erweiterten sozialen Netzwerken für die Remote Kommunikation.

Kurz gesagt: die Verwendung von Eye-Blick als Eingabe bietet ein schnelles und mühelose kontextbezogenes Eingabe Signal. Dies ist insbesondere in Kombination mit anderen Eingaben, wie z. b. *Voice* und *manueller* Eingabe, zur Bestätigung der Absicht des Benutzers sehr leistungsstark


### <a name="challenges-of-eye-gaze-as-an-input"></a>Herausforderungen des Augenblicks als Eingabe
Mit einer großen Menge von Energie.
Wenngleich der Augenblick verwendet werden kann, um zufriedenstellende Benutzeroberflächen zu erstellen, die Ihnen einen Superhero ähneln, ist es auch wichtig zu wissen, was für dieses nicht geeignet ist. Im folgenden werden einige der zu berücksichtigenden *Probleme* und deren Behebung bei der Arbeit mit der Eingabe des Augenblicks erläutert: 

- **Ihr Blick ist "Always on"** . In dem Moment, in dem Sie Ihre Augen Deckeln öffnen, beginnen Ihre Augen damit, die Dinge in der Umgebung zu fixieren. Wenn Sie auf jede Art und Weise reagieren, die Sie durchführen, und versehentlich Aktionen ausgeben, führt dies zu einer unfreundlichen Darstellung.
Daher empfiehlt es sich, den Augenblick mit einem *Sprachbefehl*, einer *Handbewegung*, einer *Schaltfläche* oder einem erweiterten Wohnort zu kombinieren, um die Auswahl eines Ziels zu initiieren (Weitere Informationen finden Sie unter [Eye-Eye und Commit](gaze-and-commit-eyes.md)).
Diese Lösung ermöglicht außerdem einen Modus, in dem der Benutzer sich ohne überdies durch eine unwillkürlich Auslösung von etwas bewegen kann. Dieses Problem sollte auch beim Entwerfen von visuellem und auditiven Feedback bei der Betrachtung eines Ziels berücksichtigt werden.
Versuchen Sie nicht, den Benutzer mit unmittelbaren popouteffekten oder Hover-Sounds zu überfordern. Die Feinheit ist der Schlüssel. Im folgenden werden einige bewährte Methoden erläutert, die in Bezug auf [Entwurfs Empfehlungen](eye-gaze-interaction.md#design-recommendations)erläutert werden.

- **Überwachung und Steuerung** Stellen Sie sich vor, dass Sie ein Foto genau auf Ihre Wand ausrichten möchten. Sie schauen zuerst auf den Rahmen und dann auf die Umgebung, um festzustellen, ob es richtig ausgerichtet ist. Stellen Sie sich nun vor, wie Sie dies tun würden, wenn Sie den Blick als Eingabe zum Verschieben des Bilds verwenden möchten. Schwierig, nicht wahr? Dies beschreibt die doppelte Rolle des Augenblicks, wenn Sie sowohl für die Eingabe als auch für die Steuerung erforderlich ist. 

- **Verlassen Sie sich auf:** Für eine schnelle Zielauswahl hat Research gezeigt, dass der Augenblick eines Benutzers fortfahren kann, bevor ein manueller Klick abgeschlossen wird (z. b. ein lufttipp). Daher muss besonders darauf geachtet werden, dass das schnelle Eye-Eye-Signal mit einer langsameren Steuerungs Eingabe (z. b. Voice, Hands, Controller) synchronisiert wird.

- **Kleine Ziele:** Wissen Sie das Gefühl, wenn Sie versuchen, Text zu lesen, der nur etwas zu klein ist, um bequem lesbar zu sein? Diese Überlastung kann dazu führen, dass Sie müde und abgeblendet werden, da Sie versuchen, die Augen besser zu verbessern.
Dies ist ein Gefühl, das Sie in Ihren Benutzern aufrufen können, wenn Sie erzwingen, dass Sie Ziele auswählen, die in Ihrer Anwendung mit der Ziel Ausrichtung zu klein sind.
Damit Sie für Ihre Benutzer eine angenehme und komfortable Erfahrung schaffen, sollte bei Zielen für Ihren Entwurf der Sehwinkel mindestens 2 Grad (vorzugsweise mehr) betragen.

- Unregelmäßige **Augenblicke Bewegungen** Unsere Augen führen zu schnellen Bewegungen von der Fixierung bis zur Fixierung. Wenn Sie Scanwege aufgezeichneter Blickbewegungen betrachten, können Sie die Flatterhaftigkeit erkennen. Die Augen werden schnell und in spontanen Sprüngen im Vergleich zu *Kopf-* und *Handbewegungen*bewegt.  

- Nach **Verfolgung der Zuverlässigkeit:** Die Genauigkeit der Augen Verfolgung kann beim Ändern des Lichts ein wenig beeinträchtigen, wenn sich die Augen auf die neuen Bedingungen einstellen.
Dies sollte sich nicht notwendigerweise auf den Anwendungs Entwurf auswirken, da die Genauigkeit innerhalb der Begrenzung von 2 ° liegen sollte, ist es möglicherweise erforderlich, dass der Benutzer erneut eine Kalibrierung durch gibt. 


## <a name="design-recommendations"></a>Entwurfsempfehlungen
Im folgenden finden Sie eine Liste mit spezifischen Entwurfs Empfehlungen, die auf den beschriebenen Vorteilen und Herausforderungen für die Augenblick Eingabe basieren:

1. **Der Augenblick ist nicht der gleiche wie der Haupt Blick:**
    - Stellen Sie sich vor, **ob schnelle, aber unregelmäßige Augenbewegungen für Ihre Eingabe Aufgabe geeignet sind:** Während unsere schnellen und unregelmäßigen Augenbewegungen bei der schnellen Auswahl von Zielen im Sichtbereich sehr nützlich sind, sind Sie für Aufgaben, die Smooth-Eingabe-Bewegungsabläufe erfordern (z. b. das Zeichnen oder einschließen von Anmerkungen), weniger anwendbar. In diesem Fall ist das Zeigen mit Hand oder Kopf zu bevorzugen.
  
    - **Vermeiden Sie, etwas direkt an den Augenblick des Benutzers anzufügen (z. b. einen Schieberegler oder Cursor).**
Bei einem Cursor kann dies aufgrund von geringfügigen Offsets im projizierten Eye-Gaze-Signal zu einem "flüchtig"-Cursor Effekt führen. Im Fall eines Schiebereglers kann der Schieberegler mit der doppelten Rolle des Schiebereglers in Konflikt stehen, während gleichzeitig überprüft werden soll, ob sich das Objekt am richtigen Speicherort befindet. Im Beispiel für den Schieberegler ist es sinnvoller, den Augenblick in Kombination mit Handgesten zu verwenden. Dies bedeutet, dass der Benutzer schnell und mühelos zwischen einer Reihe von Schiebereglern wechseln kann, dabei seine Hand aufrichtet und den Ziehpunkt und den Finger des Indexes anpackt, um ihn zu verschieben und zu verschieben. Wenn die-Pinsel losgelassen wird, beendet der Schieberegler die Verschiebung. Kurz gesagt, können Benutzer überlastet und abgelenkt werden, insbesondere wenn das Signal für diesen Benutzer unpräzise ist. 
  
2. **Kombinieren Sie den Augenblick mit anderen Eingaben:** Die Integration der Eye-Nachverfolgung mit anderen Eingaben, z. b. Handgesten, Sprachbefehle oder Schaltflächen-Pressen, bietet mehrere Vorteile:
    - **Kostenlose Überwachung zulassen:** Da die Hauptrolle unserer Augen darin besteht, unsere Umgebung zu beobachten, ist es wichtig, dass Benutzer die Möglichkeit haben, sich anzusehen, ohne irgendwelche (visuellen, auditiven usw.) Feedback oder Aktionen auszulösen. 
    Das Kombinieren der Eye-Nachverfolgung mit einem anderen Eingabe Steuerelement ermöglicht einen reibungslosen Übergang zwischen der Überwachung der Augen Verfolgung und den Eingabe
  
    - **Leistungsfähiger Kontext Anbieter:** Wenn Sie Informationen dazu verwenden, wo und was der Benutzer sucht, während Sie einen Sprachbefehl oder eine Handbewegung ausführen, können Sie die Eingabe nahtlos über das Feld der Ansicht leiten. Nehmen Sie beispielsweise an _, dass_ Sie den Code so schnell und reibungslos auswählen und positionieren können, indem Sie einfach ein Ziel und das beabsichtigte Ziel betrachten. 

    - **Synchronisierung von multimodalen Eingaben erforderlich:** Die Kombination von Rapid Eye-Bewegungen mit komplexeren zusätzlichen Eingaben, wie z. b. langen Sprachbefehlen oder Handgesten, birgt das Risiko, dass der Benutzer bereits nach dem Fertigstellen und erkennen des zusätzlichen Eingabe Befehls eine weitere Suche durchführt. Wenn Sie also Ihre eigenen Eingabe Steuerelemente erstellen (z. b. benutzerdefinierte Handgesten), sollten Sie das Auftreten dieser Eingabe oder der ungefähren Dauer protokollieren, um Sie mit dem zu korrelieren, was ein Benutzer in der Vergangenheit gesehen hat.
    
3. **Feines Feedback für die Eingabe der Augen Verfolgung:** Es ist hilfreich, Feedback zu geben, wenn ein Ziel untersucht wird, um anzugeben, dass das System wie beabsichtigt funktioniert, aber dennoch gering gehalten werden sollte. Dies kann eine langsame Mischung, ein-und ausgehende, visuelle Highlights oder andere, feine Ziel Verhaltensweisen, wie z. b. langsame Bewegungen, z. b. eine geringfügige Erhöhung der Zielgröße, beinhalten, um anzugeben, dass das System ordnungsgemäß erkannt hat, dass der Benutzer ein Ziel unnötiges unterbrechen des aktuellen Workflows des Benutzers. 

4. **Vermeiden Sie das Erzwingen von unnatürlichen Augenbewegungen als Eingabe:** Erzwingen Sie nicht, dass Benutzer bestimmte Augenbewegungen (Augenbewegungen) ausführen, um Aktionen in der Anwendung zu initiieren.

5. **Konto für Ungenauigkeit:** Wir unterscheiden zwei Arten von imsions, die für die Benutzer bemerkbar sind: Offset und Jitter. Die einfachste Möglichkeit, einen Offset zu behandeln, besteht darin, ausreichend große Ziele für die Interaktion bereitzustellen. Es wird empfohlen, einen visuellen Winkel größer als 2 ° als Verweis zu verwenden. Beispielsweise ist die Miniaturansicht ungefähr 2 ° im visuellen Winkel, wenn Sie den Arm ausdehnen. Dies führt zu folgender Richtlinie:
    - Erzwingen Sie nicht, dass Benutzer kleine Ziele auswählen. Die Untersuchung hat ergeben, dass die Interaktionen, wenn die Ziele ausreichend groß sind und das System gut entworfen wurde, mühelos und magisch beschrieben werden. Wenn Ziele zu klein sind, empfinden Benutzer die Erfahrung als ermüdend und frustrierend.
  
<br>

Auf dieser Seite haben Sie einen guten Überblick erhalten, um Ihnen den Einstieg in die Eingabe in gemischter Realität zu verdeutlichen. Informationen zu den ersten Schritten bei der Entwicklung finden Sie in den Informationen zu den [Augenblicken in Unity](https://aka.ms/mrtk-eyes) und im Blickwinkel [in DirectX](gaze-in-directx.md).


## <a name="see-also"></a>Weitere Informationen:
* [Komfort](comfort.md)
* [Blick in DirectX](gaze-in-directx.md)
* [Blick in Unity (Mixed Reality Toolkit)](https://aka.ms/mrtk-eyes)
* [Augen Verfolgung auf hololens 2](eye-tracking.md)
* [Blick und Commit](gaze-and-commit.md)
* [Anvisieren und Verweilen](gaze-and-dwell.md)
* [Spracheingabe](voice-design.md)
