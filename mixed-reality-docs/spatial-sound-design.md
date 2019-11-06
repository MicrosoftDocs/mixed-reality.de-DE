---
title: Verwenden von Sound in Mixed Reality-Anwendungen
description: Räumlicher Sound ist ein leistungsfähiges Tool für das Eintauchen, die Barrierefreiheit und den UX-Entwurf in gemischten Reality-Anwendungen.
author: kegodin
ms.author: kegodin
ms.date: 11/02/2019
ms.topic: article
keywords: Windows Mixed Reality, räumlicher Sound, Entwurf, Stil
ms.openlocfilehash: c069095808eaa9d31b1ffa41dbaa29c9f635837b
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641065"
---
# <a name="using-sound-in-mixed-reality-applications"></a>Verwenden von Sound in Mixed Reality-Anwendungen

Verwenden Sie den Sound, um das geistige Modell des Benutzers für den Anwendungs Zustand zu informieren und zu verstärken. Verwenden Sie bei Bedarf spatialization, um Klänge in die gemischte Welt zu versetzen. Wenn Sie das Akustik und das visuelle Element auf diese Weise verbinden, wird die intuitive Natur vieler Interaktionen vertieft und die Benutzer Zuverlässigkeit gesteigert.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="when-should-i-add-sounds"></a>Wann sollte ich Sounds hinzufügen?
Gemischte Reality-Anwendungen haben häufig eine größere Notwendigkeit für Sounds als Anwendungen auf einem 2D-Bildschirm, weil keine physische Schnittstelle vorhanden ist. Sounds sollten hinzugefügt werden, wenn Sie den Benutzer informieren oder Interaktionen verstärken.

### <a name="inform-and-reinforce"></a>Informieren und verstärken
* Bei Ereignissen, die nicht vom Benutzer initiiert werden (z. b. Benachrichtigungen), sollten Sie Sounds hinzufügen, um dem Benutzer mitzuteilen, dass eine Änderung aufgetreten ist
* Interaktionen können mehrere Stufen aufweisen. Verwenden Sie Sounds, um Phasenübergänge zu verstärken.

Im folgenden finden Sie Beispiele für Interaktionen, Ereignisse und empfohlene Sound Merkmale.

### <a name="exercise-restraint"></a>Übungs Zurückhaltung
Benutzer haben keine unbegrenzte Kapazität für Audioinformationen:
* Jeder Sound sollte bestimmte, wertvolle Informationen vermitteln.
* Bei der Wiedergabe von Sounds, die den Benutzer informieren sollen, wird die Menge anderer Sounds vorübergehend reduziert.
* Fügen Sie für Tastendruck Sounds (siehe unten) eine Zeitverzögerung hinzu, um eine übermäßige Auslösung von Sounds zu verhindern.

### <a name="dont-rely-solely-on-sounds"></a>Verlassen Sie sich nicht ausschließlich auf Sounds.
Die verwendeten Sounds sind hilfreich, wenn Ihre Benutzer Sie hören können, aber stellen Sie sicher, dass Ihre Anwendung auch mit dem Sound Off verwendbar ist.
* Benutzer werden möglicherweise beeinträchtigt.
* Ihre Anwendung kann in einer laut Umgebung verwendet werden.
* Benutzer haben möglicherweise Datenschutz oder andere Gründe, um das Audiogerät zu deaktivieren.

## <a name="how-should-i-sonify-interactions"></a>Wie kann ich Interaktionen sonify ausführen?
Interaktions Typen in gemischter Realität umfassen Gesten, direkte Bearbeitung und Spracheingabe. Verwenden Sie die folgenden empfohlenen Merkmale, um Klänge für diese Interaktionen auszuwählen oder zu entwerfen.

### <a name="gesture-interactions"></a>Gesten Interaktionen
In gemischter Realität können Benutzer mit Schaltflächen über einen Cursor interagieren. Schaltflächen Aktionen werden in der Regel ausgeführt, wenn der Benutzer die Schaltfläche freigegeben hat, und nicht, wenn er gedrückt wurde, um dem Benutzer die Möglichkeit zu geben, die Interaktion abzubrechen. Verwenden Sie Sounds, um diese Phasen zu verstärken. Zum unterstützen von Benutzern bei der Ausrichtung auf entfernte Schaltflächen sollten Sie auch einen Cursor mit Cursor Bewegung verwenden.
* Die Schaltfläche zum Drücken der Schaltfläche sollte einen kurzen, nicht geklick Beispiel: [MRTK_ButtonPress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* Unpress-Sounds mit Schaltfläche sollten ein ähnliches taktiles Gefühl aufweisen. Wenn Sie einen erhöhten Platz im Vergleich zum Press Sound haben, wird der Abschluss des Abschlusses verstärkt. Beispiel: [MRTK_ButtonUnpress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)
* Für Hover-Sounds empfiehlt sich die Verwendung eines kleinen und nicht bedrohlichen Sounds, wie z. b. eine niedrige Häufigkeits-oder Stoß Bewegung.


### <a name="direct-manipulation"></a>Direkte Bearbeitung
Bei hololens 2 unterstützt die Handschrift Nachverfolgung die direkte Bearbeitung von Elementen der Benutzeroberfläche. Sounds sind wichtige Ersetzungen für den Mangel an physischem Feedback.

Ein **Schalt** Flächen-Press Sound ist bei direkter Bearbeitung wichtig, da der Benutzer nicht physisch darauf hinweist, wann er das Ende der Tastatur Fahrt erreicht hat. Visuelle Indikatoren von Schlüssel Reisen können klein, geringfügig und okkludiert sein. Wie bei Gesten Interaktionen sollte das Drücken von Schaltflächen mit einem kurzen, nicht geklickenden Sound wie ein Klick aussehen, und das Deaktivieren sollte einen ähnlichen Klick mit erhöhter Tonhöhe aufweisen.
* Beispiel: [MRTK_ButtonPress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* Beispiel: [MRTK_ButtonUnpress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonUnpress)

Das über **Prüfen eines Handles** oder **Releases** in direkter Bearbeitung ist schwierig, visuell zu kommunizieren. Der Benutzer hat häufig einen visuellen Effekt, und in Festkörper Objekten fehlt eine echte visuelle Analogie von "Grabbing". Im Gegensatz dazu können Sounds erfolgreiche Interaktionen und releaseinteraktionen effektiv übermitteln.
* Bei der Aufnahme von Aktionen sollte ein kurzer, etwas gedämpfteter taktischen Sound vorhanden sein, der die Idee von Fingern für ein Objekt widerspricht. Manchmal wird dies durch einen "whoosh"-Sound begleitet, der zu den Auswirkungen des Sounds führt, um die Bewegung beim erfassen zu vermitteln. Beispiel: [MRTK_Move_Start. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_Move_Start.wav)
* Releaseaktionen sollten einen ähnlichen kurzton und einen nicht-taktischen Sound aufweisen, der in der Regel aus dem Ton-Ton und in umgekehrter Reihenfolge heraus gepackt wird Beispiel: [MRTK_Move_End. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_Move_End.wav)

Eine **Zeichnungs** Interaktion sollte eine Schleife, einen persistenten Sound aufweisen, bei dem das Volume durch die Bewegung des Benutzers gesteuert wird, damit es vollständig unbeaufsichtigt ist, wenn der Benutzer die Hand hat, und auf dem maximalen Volume, wenn die Benutzerseite sich schnell bewegt.



### <a name="voice-interactions"></a>Sprach Interaktionen
Sprach Interaktionen haben häufig feine visuelle Elemente. Verstärken Sie die Interaktions Phasen mithilfe von Sounds. Es empfiehlt sich, mehr klangliche Sounds auszuwählen, um Sie von Gesten-und direkten Manipulations Geräuschen zu unterscheiden

* Verwenden Sie für die **Bestätigung**von Sprachbefehlen einen positiven Ton Sound. Zu diesem Zeitpunkt sind steigende Töne und große musikalische Intervalle wirksam.
* Verwenden Sie einen kürzeren, weniger positiven klanglichen Ton für den sprach Befehls **Fehler**. Vermeiden Sie negative Sounds; Verwenden Sie stattdessen einen perkussiven, neutralen Sound, um zu kommunizieren, dass die Anwendung von der Interaktion bewegt wird.
* Wenn Ihre Anwendung ein Reaktivierungs Wort verwendet, verwenden Sie einen kurzen, sanften Ton, wenn das Gerät mit dem **lauschen begonnen**hat, und einen feinen Schleifen Sound, während die Anwendung lauscht. 

### <a name="notifications"></a>Benachrichtigungen
Benachrichtigungen kommunizieren Anwendungs Zustandsänderungen und andere Ereignisse, die nicht vom Benutzer initiiert werden, wie z. b. Prozess Vervollständigungen, Meldungen und Aufrufe.

In gemischter Realität können Objekte, die verschoben werden, aus dem Sichtfeld des Benutzers heraus verschoben werden. Begleitenden **Objekten** wird ein räumlicher Sound begleitet, der vom Objekt und der Geschwindigkeit der Bewegung abhängig ist.
* Außerdem hilft es bei der Wiedergabe eines räumlichen Sounds am Ende einer Animation, um den Benutzer über die neue Position zu informieren.
* Bei allmählichen Verschiebungen unterstützt ein "whoosh" Sound während der Bewegung den Benutzer beim Nachverfolgen des Objekts.

**Nachrichten Benachrichtigungen** werden höchstwahrscheinlich mehrmals und manchmal in schneller Folge gehört. Es ist wichtig, dass es sich nicht um eine harte Situation handelt. Positive klangliche Töne in Mittelbereich sind hier wirksam.

* Aufrufe sollten ähnliche Qualitäten wie ein zelltelefonrington aufweisen. Dabei handelt es sich normalerweise um Schleifen, die so lange wiedergegeben werden, bis der Benutzer den-Befehl beantwortet.
* Die sprach Kommunikationsverbindung und die Verbindungs Trennung sollten einen kurzen, klanglichen Ton aufweisen. Der Sound der Verbindung sollte einen positiven Ton aufweisen, der die erfolgreiche Verbindung angibt, während der disverbindungssound ein neutraler Sound sein sollte, der den Abschluss des Aufrufes angibt.

## <a name="spatialization"></a>Spatialisierung
Bei der Spatialisierung werden Stereo-Kopfhörer oder Referenten verwendet, um Klänge in die gemischte Welt zu versetzen.

### <a name="which-sounds-should-i-spatialize"></a>Welche Sounds sollte ich räumlichen?
Ein Sound sollte räumlich räumlich sein, wenn er einem Ereignis zugeordnet ist, das einen räumlichen Standort aufweist. Dies umfasst die Benutzeroberfläche, die verkörperten Ki-Stimmen und visuelle Indikatoren.

Durch das spatialisieren von Elementen der **Benutzeroberfläche** wird der klangliche Raum des Benutzers entsperrt, indem die Anzahl der Stereo Sounds beschränkt wird, die auf die Köpfe gesperrt sind. Vor allem bei direkten Manipulations Interaktionen ist das berühren, einspielen und Freigeben von etwas natürlicher, wenn Audiofeedback räumlich ist. Im folgenden finden Sie jedoch Informationen zur Entfernungs Entfernung für diese Elemente.

Durch die räumliche Darstellung von **visuellen Indikatoren** und den  **_verkörperten_ Ki-Stimmen** werden Benutzer intuitiv informiert, wenn Sie sich außerhalb der Ansicht befinden.
    
Vermeiden Sie im Gegensatz dazu die Spatialisierung für  **_Facetten_ reiche Ki-Stimmen**und andere Elemente ohne klar definierte räumliche Position. Die Spatialisierung ohne ein verwandtes visuelles Element kann Benutzer dazu lenken, zu denken, dass es ein visuelles Element gibt, das Sie nicht finden können.

Das Hinzufügen der Spatialisierung führt zu einigen CPU-Kosten. Viele Anwendungen haben höchstens zwei Sounds, die gleichzeitig abgespielt werden. Die Kosten der Spatialisierung in diesem Fall können vernachlässigbar sein. Mit dem mrtk-Frameraten Monitor können Sie die Auswirkungen der Hinzufügung von spatialization beurteilen. 

### <a name="when-and-how-should-i-apply-distance-based-attenuation"></a>Wann und wie sollte ich die Entfernungs basierte Dämpfung anwenden?
In der physischen Welt sind Sounds, die weiter entfernt sind, leiser. Die Audioengine kann diese Dämpfung basierend auf der Quell Distanz modellieren. Verwenden Sie die Entfernungs basierte Dämpfung, wenn Sie relevante Informationen kommuniziert.

Die Entfernungen zu **visuellen Indikatoren**, **animierten holograms**und andere informative Sounds sind in der Regel für den Benutzer relevant. Verwenden Sie die Entfernungs basierte Dämpfung, um diesen Hinweis intuitiv bereitzustellen.
* Passen Sie die Dämpfungs Kurve für jede Quelle an die Größe Ihrer gemischten Raumbereiche an. Die Standardkurve ihrer Audioengine ist häufig für sehr große (bis zu halbkilometer) Leerzeichen vorgesehen.

Bei Sounds, die die **progressiven Phasen von Schalt** Flächen und anderen Interaktionen verstärken, sollte keine Dämpfung angewendet werden. Die Verstärkungseffekte dieser Sounds sind im allgemeinen wichtiger als die Übertragung der Entfernung an die Schaltfläche. Variationen können ablenkend sein, insbesondere bei Tastaturen, bei denen viele Schaltflächen Klicks nacheinander angezeigt werden.

### <a name="which-spatialization-technology-should-i-use"></a>Welche spatialisierungstechnologie sollte ich verwenden?
Verwenden Sie bei Verwendung von Kopfhörern oder hololens-Referenten die HRTF-basierten spatialisierungs Technologien (Head-Related Transfer Function). Sie modellieren die audioweitergabe um den Kopf in der physischen Welt. Auch wenn sich eine Audioquelle weit auf eine Seite des Kopfes befindet, wird der Sound mit einer gewissen Dämpfung und Verzögerung an das entfernte Ohr weitergegeben. Lautsprecher schwenken ist dagegen nur eine Dämpfung und die gesamte Dämpfung im linken Ohr, wenn sich die Sounds auf der rechten Seite befinden (und umgekehrt). Dies kann für normale Hörgeschädigte nicht ausreichen und für Listener mit der Hörbehinderung in einem Ohr nicht zugänglich sein.

## <a name="next-steps"></a>Nächste Schritte
* [Verwenden von räumlichem Sound in Unity](spatial-sound-in-unity.md)
* [Fallstudie von roboraid](case-study-using-spatial-sound-in-roboraid.md)
* [Fallstudie von holotour](case-study-spatial-sound-design-for-holotour.md)

