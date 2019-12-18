---
title: Verwenden von räumlichem Sound in Anwendungen mit gemischter Realität
description: Räumlicher Sound ist ein leistungsfähiges Tool für das Eintauchen, die Barrierefreiheit und den UX-Entwurf in Anwendungen mit gemischter Realität.
author: kegodin
ms.author: kegodin
ms.date: 11/02/2019
ms.topic: article
keywords: Windows Mixed Reality, räumlicher Sound, Entwurf, Stil
ms.openlocfilehash: 34923e1ebfc8e46ea8e67a4444fe3c2691efd4db
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182010"
---
# <a name="how-to-use-sound-in-mixed-reality-applications"></a>Verwenden von Sound in Anwendungen mit gemischter Realität

Mit Sound können Sie das geistige Modell des Benutzers der Anwendung informieren und verstärken. Verwenden Sie bei Bedarf spatialization, um Klänge in der Mixed-Reality-Welt zu platzieren. Wenn Sie das Akustik und das visuelle Element auf diese Weise verbinden, vertiefen Sie die intuitive Natur der Interaktionen und erhöhen die Benutzer Zuverlässigkeit.
<br><br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="when-to-add-sounds"></a>Wann sollten Sounds hinzugefügt werden?
Anwendungen mit gemischter Realität verfügen häufig über eine größere Notwendigkeit für Sound als 2D-apps, da Sie nicht über eine benutzerfreundliche Schnittstelle verfügen. Fügen Sie Sounds hinzu, wenn Sie den Benutzer informieren oder Interaktionen verstärken.

### <a name="inform-and-reinforce"></a>Informieren und verstärken
* Bei Ereignissen, die nicht vom Benutzer initiiert werden (z. b. Benachrichtigungen), wird der Benutzer mit Sound informiert, dass eine Änderung aufgetreten ist.
* Interaktionen können mehrere Stufen aufweisen. Verwenden Sie Sound, um Phasenübergänge zu verstärken.

Sehen Sie sich die folgenden Beispiele für Interaktionen, Ereignisse und empfohlene Sound Merkmale an.

### <a name="exercise-restraint"></a>Übungs Zurückhaltung
Benutzer haben keine unbegrenzte Kapazität für Audioinformationen.
* Jeder Sound sollte bestimmte, wertvolle Informationen vermitteln.
* Wenn Ihre APP einen Sound wieder gibt, um den Benutzer zu informieren, verringern Sie vorübergehend das Aufkommen anderer Sounds.
* Fügen Sie für schaltflächenhover-Sounds (siehe folgende Informationen) eine Zeitverzögerung hinzu, um eine übermäßige Geräusch Auslösung zu verhindern.

### <a name="dont-rely-solely-on-sounds"></a>Verlassen Sie sich nicht ausschließlich auf Sounds.
Sounds, die gut verwendet werden, sind für Ihre Benutzer wertvoll. Stellen Sie jedoch sicher, dass Ihre Anwendung auch dann verwendbar ist, wenn der Sound ausgeschaltet ist.
* Benutzer werden möglicherweise beeinträchtigt.
* Ihre Anwendung kann in einer laut Umgebung verwendet werden.
* Benutzer haben möglicherweise Probleme mit dem Datenschutz oder andere Gründe, das Gerät zu deaktivieren.

## <a name="how-to-sonify-interactions"></a>Vorgehensweise beim sonify von Interaktionen
Interaktions Typen in gemischter Realität umfassen Gesten, direkte Bearbeitung und Spracheingabe. Verwenden Sie die folgenden empfohlenen Merkmale, um Klänge für diese Interaktionen auszuwählen oder zu entwerfen.

### <a name="gesture-interactions"></a>Gesten Interaktionen
In gemischter Realität können Benutzer mit Schaltflächen interagieren, indem Sie eine Maus verwenden. Schaltflächen Aktionen treten in der Regel auf, wenn der Benutzer loslässt, anstatt die Schaltfläche zu drücken, um dem Benutzer das Abbrechen der Interaktion zu gestatten. Verwenden Sie Sounds, um diese Phasen zu verstärken. Zur Unterstützung von Benutzern bei der Ausrichtung von fern enden Schaltflächen sollten Sie auch einen Zeiger auf Zeiger zeigen.
* Die Schaltfläche "Sound" sollte ein kurzes, taktiles "klicken" sein.<br/>Beispiel: [MRTK_ButtonPress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* Die Schaltfläche "unpress"-Sounds sollte ein ähnliches taktiles Gefühl aufweisen. Eine höhere Tonhöhe als der Press Sound verstärkt den Sinn der Vervollständigung.<br/>Beispiel: [MRTK_ButtonUnpress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)
* Für Hover-Sounds empfiehlt es sich, einen kleinen und nicht bedrohlichen Sound zu verwenden, z. b. eine niedrige Häufigkeits-oder Stoß Bewegung.

### <a name="direct-manipulation"></a>Direkte Bearbeitung
Bei hololens 2 unterstützt die Handschrift Nachverfolgung die direkte Bearbeitung von Elementen der Benutzeroberfläche. Sounds sind wichtig, wenn kein anderes physisches Feedback vorhanden ist.

Ein *Schalt* Flächen-Press Sound ist bei direkter Bearbeitung wichtig, da der Benutzer keine andere Anzeige erhält, wenn er das Ende des Tasten Strichs erreicht. Die audioindikatoren von Schlüssel Reisen können klein, geringfügig und okton sein. Wie bei Gesten Interaktionen sollte das Drücken von Schaltflächen auf einen kurzen, über taktilen Sound wie ein Klick erhalten. Unpressen sollten einen ähnlichen Klick Sound haben, jedoch mit erhöhter Tonhöhe.
* Beispiel: [MRTK_ButtonPress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* Beispiel: [MRTK_ButtonUnpress. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_ButtonUnpress)

Es ist schwierig, eine Aktion zum durchlassen oder veröffentlichen visuell zu bestätigen. Der Benutzer hat häufig einen visuellen Effekt, und in Festkörper Objekten fehlt eine echte visuelle Analogie von "Grabbing". Sounds können erfolgreiche Interaktionen und releaseinteraktionen effektiv übermitteln.
* Bei der Aufnahme von Aktionen sollte ein kurzer, etwas gedämpfte taktischender Sound vorhanden sein, der die Idee von Fingern zum Schließen eines Objekts auslöst. Manchmal gibt es auch einen "whoosh"-Sound, der zum übermitteln der Bewegung führt.<br/>Beispiel: [MRTK_Move_Start. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_Move_Start.wav)
* Releaseaktionen sollten einen ähnlich kurzen und unauditon Sound erhalten. Es ist in der Regel niedriger als der Ton und in umgekehrter Reihenfolge, mit einer Auswirkung und einem "whoosh", um zu kommunizieren, dass sich das Objekt am Ort befindet.<br/>Beispiel: [MRTK_Move_End. wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Audio/MRTK_Move_End.wav)

Eine *Zeichnungs* Interaktion sollte einen permanenten Schleifen Sound erhalten, dessen Volume durch die Bewegung des Benutzers bestimmt wird. Er sollte unbeaufsichtigt sein, wenn die Hand des Benutzers immer noch ist, wenn die Hand bewegt wird.

### <a name="voice-interactions"></a>Sprach Interaktionen
Sprach Interaktionen haben häufig feine visuelle Elemente. Verwenden Sie Sounds, um Interaktions Phasen zu verstärken. Möglicherweise möchten Sie mehr tontöne verwenden, um Sie von Gesten-und direkt Manipulations Geräuschen zu unterscheiden.

* Verwenden Sie für die *Bestätigung*von Sprachbefehlen einen positiven Ton Sound. Steigende Töne und große musikalische Intervalle sind effektiv.
* Verwenden Sie für sprach Befehls *Fehler*einen kürzeren, weniger positiven Ton Sound. Vermeiden Sie negative Sounds. Verwenden Sie stattdessen einen perkussiven, neutralen Sound, um zu kommunizieren, dass die Anwendung von der Interaktion aus bewegt wird.
* Wenn Ihre Anwendung ein Reaktivierungs Wort hat, verwenden Sie einen kurzen, sanften Ton, wenn das Gerät mit dem *lauschen beginnt*. Verwenden Sie einen feinen Schleifen Sound, während die *Anwendung lauscht* .

### <a name="notifications"></a>Benachrichtigungen
Benachrichtigungen kommunizieren Anwendungs Zustandsänderungen und andere Ereignisse, die nicht vom Benutzer initiiert werden, wie z. b. Prozess Vervollständigungen, Nachrichten und Telefonanrufe.

In gemischter Realität werden Objekte manchmal aus der Sicht des Benutzers verschoben. Begleitenden *animierten Objekten* mit einem räumlichen Ton, der vom Objekttyp und der Geschwindigkeit der Bewegung abhängig ist.
* Es hilft, einen räumlichen Sound am Ende einer Animation wiederzugeben, um den Benutzer über die neue Position des Objekts zu informieren.
* Bei schrittweisen Verschiebungen unterstützt ein "whoosh"-Sound während der Bewegung den Benutzer beim Nachverfolgen des Objekts.

Nach *richten-Benachrichtigungs* Sounds werden möglicherweise wiederholt, manchmal in schneller Folge. Es ist wichtig, dass Sie sich nicht herausstellen oder hart klingen. Positive klangliche Töne im mittleren Bereich sind effektiv.

* Die Sounds für eingehende Anrufe sollten ähnliche Qualitäten wie ein zelltelefonrington aufweisen. Dabei handelt es sich normalerweise um Schleifen, die so lange wiedergegeben werden, bis der Benutzer den-Befehl aufruft
* Die sprach Kommunikationsverbindung und die Verbindungs Trennung sollten einen kurzen, klanglichen Ton aufweisen. Der Verbindungs Sound sollte ein positiver Ton sein, um eine erfolgreiche Verbindung anzugeben. Der Sound für die Trennung der Verbindung sollte ein neutraler Sound sein, um den Abschluss des Aufrufes anzuzeigen.

## <a name="handle-spatialization"></a>Behandeln der Spatialisierung
Bei der Spatialisierung werden Stereo-Kopfhörer oder Referenten verwendet, um Klänge in der gemischten Realität zu platzieren.

### <a name="which-sounds-to-spatialize"></a>Die zu räumlichen Sounds
Ein Sound sollte räumlich räumlich sein, wenn er einem Ereignis zugeordnet ist, das einen räumlichen Standort aufweist. Dies umfasst die Benutzeroberfläche, die verkörperten Ki-Stimmen und visuelle Indikatoren.

Spatialisieren Sie Elemente der *Benutzeroberfläche* , um den Platz in der Benutzeroberfläche zu entgrenzen, indem Sie die Anzahl von Stereo Tönen beschränken, die Sie hören. Bearbeitungs Interaktionen, wie z. b. berühren, einspielen und freigeben, sind naturgemäß, wenn Audiofeedback räumlich verziiert ist. Beachten Sie die folgenden Informationen zur Entfernungs Dämpfung für diese Elemente.

Spatialisieren Sie *visuelle Indikatoren* , und informieren Sie sich über *Ki-Stimmen* , um Benutzer intuitiv zu informieren, wenn diese Dinge außerhalb der Ansicht stehen.
    
Vermeiden Sie im Gegensatz dazu die Spatialisierung für *facettenreiche Ki-Stimmen* und andere Elemente, die keinen klar definierten räumlichen Speicherort haben. Die Spatialisierung ohne ein verwandtes visuelles Element kann Benutzer dazu lenken, zu glauben, dass es ein visuelles Element gibt, das nicht gefunden werden kann.

Die Spatialisierung führt zu einigen CPU-Kosten. Viele Anwendungen haben höchstens zwei Sounds, die gleichzeitig abgespielt werden. Die Kosten für die Spatialisierung in diesem Fall sind wahrscheinlich unerheblich. Mit dem mrtk-Frameraten Monitor können Sie die Auswirkungen der Hinzufügung von spatialization beurteilen.

### <a name="when-and-how-to-apply-distance-based-attenuation"></a>Wann und wie die Entfernungs basierte Dämpfung angewendet wird
In der physischen Welt sind Sounds, die weiter entfernt sind, leiser. Die Audioengine kann diese Dämpfung basierend auf der Quell Distanz modellieren. Verwenden Sie die Entfernungs basierte Dämpfung, wenn Sie relevante Informationen kommuniziert.

Die Entfernungen zu *visuellen Indikatoren*, *animierten holograms*und andere informative Sounds sind in der Regel für den Benutzer relevant. Verwenden Sie die Entfernungs basierte Dämpfung, um intuitiv Hinweise bereitzustellen.

Passen Sie die Dämpfung der Dämpfung für jede Quelle an die Größe ihrer Bereiche mit gemischter Realität an. Die Standardkurve ihrer Audioengine ist häufig für sehr große (bis zu halbkilometer) Leerzeichen vorgesehen.

Sounds, die die *progressiven Phasen von Schaltflächen Aktionen* und anderen Interaktionen verstärken, sollten die Dämpfung nicht anwenden. Die Verstärkungseffekte dieser Sounds sind im allgemeinen wichtiger als die Übertragung der Entfernung an die Schaltfläche. Variationen können ablenkend sein, insbesondere bei Tastaturen, wenn viele Schaltflächen Klicks nacheinander angezeigt werden.

### <a name="which-spatialization-technology-to-use"></a>Welche spatialisierungs Technologie zu verwenden ist
Mithilfe von Kopf Köpfen oder den Referenten von hololens verwenden Sie auf der Basis der auf der Start bezogenen Übertragungsfunktion basierenden spatialization-Technologien. Diese Technologien modellieren die audioweitergabe um den Kopf in der physischen Welt. Auch wenn sich eine Audioquelle auf der äußersten Seite eines Kopfes befindet, wird der Sound mit einer gewissen Dämpfung und Verzögerung an das entfernte Ohr weitergegeben. Lautsprecher schwenken ist dagegen nur eine Dämpfung und die gesamte Dämpfung im linken Ohr, wenn sich die Sounds auf der rechten Seite befinden (und umgekehrt). Diese Technik kann für "normale hörlistener" und nicht für Listener, die eine Hörbehinderung in einem Ohr haben, nicht zugänglich sein.

## <a name="next-steps"></a>Nächste Schritte
* [Verwenden von räumlichem Sound in Unity](spatial-sound-in-unity.md)
* [Fallstudie von roboraid](case-study-using-spatial-sound-in-roboraid.md)
* [Fallstudie von holotour](case-study-spatial-sound-design-for-holotour.md)
