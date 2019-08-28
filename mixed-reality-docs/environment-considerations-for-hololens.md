---
title: Überlegungen zur Umgebung für hololens
description: Erzielen Sie mithilfe von hololens die bestmögliche Benutzerumgebung, wenn Sie das Gerät für Ihre Augen und Umgebung optimieren. Viele verschiedene Umgebungsfaktoren werden kombiniert, um die Nachverfolgung zu ermöglichen. als Entwickler von Mixed Reality gibt es jedoch verschiedene Faktoren, die Sie beachten sollten, um einen Platz für ein besseres Hologramm zu optimieren.
author: dorreneb
ms.author: dobrown
ms.date: 04/22/2019
ms.topic: article
keywords: Holographic Frame, Feld of View, FOV, Kalibrierung, Spaces, Environment, How-to
ms.openlocfilehash: cc856c42aaf4ddfca8365f63ab0c7df1a1a3b248
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047079"
---
# <a name="environment-considerations-for-hololens"></a>Überlegungen zur Umgebung für hololens

Hololens verbindet die Holographic mit der "realen" Welt, wobei Hologramme in Ihrer Umgebung platziert werden. Ein Holographic-App-Fenster "hängt" auf der Wand, eine Holographic Ballerina dreht sich auf der Tabletop-Leiste, und Hasenohren sitzen auf dem Kopf Ihres Kollegen. Wenn Sie ein immersives Spiel oder eine APP verwenden, wird die Holographic World so verteilt, dass Ihre Umgebung ausgefüllt wird – aber Sie können den Platz immer noch anzeigen und verschieben.

Die von Ihnen platzierten Hologramme bleiben erhalten, wo Sie sie abgelegt haben, auch wenn Sie Ihr Gerät ausschalten. 

## <a name="setting-up-an-environment"></a>Einrichten einer Umgebung

Hololens-Geräte wissen, wie Sie stabile und exakte holograms platzieren können, indem Sie Benutzer in einem Bereich nach *verfolgen* . Ohne die richtige Nachverfolgung versteht das Gerät die Umgebung oder den darin enthaltenen Benutzer nicht. Daher können holograms an den falschen Stellen angezeigt werden, werden nicht jedes Mal an derselben Stelle angezeigt, oder Sie werden überhaupt nicht angezeigt. Die Daten, die zum Nachverfolgen von Benutzern verwendet werden, werden in der *räumlichen Karte*dargestellt. 

Die Nachverfolgung der Leistung hängt stark von der Umgebung ab, in der sich der Benutzer befindet, und das Optimieren einer Umgebung, um eine stabile und konsistente Nachverfolgung auszulösen, ist eine Kunst und keine Wissenschaft. Viele verschiedene Umgebungsfaktoren werden kombiniert, um die Nachverfolgung zu ermöglichen. als Entwickler für gemischte Realität können Sie jedoch verschiedene Faktoren beachten, um einen Raum für eine bessere Überwachung zu optimieren.
 
### <a name="lighting"></a>Beleuchtung
Windows Mixed Reality verwendet visuelle Beleuchtung, um den Speicherort des Benutzers zu verfolgen. Wenn eine Umgebung zu hell ist, können die Kameras satt werden, und es wird nichts angezeigt. Wenn die Umgebung zu dunkel ist, können die Kameras nicht genügend Informationen aufnehmen, und es wird nichts angezeigt. Die Beleuchtung sollte sogar und ausreichend hell sein, die ein Mensch ohne Aufwand sehen kann, aber nicht so hell ist, dass das Licht mühsam zu sehen ist.

Bereiche, in denen es sich um helle Licht in einem Gesamt-Dim-Bereich handelt, sind ebenfalls problematisch, da die Kamera beim Verschieben von hellen Leerzeichen angepasst werden muss. Dies kann dazu führen, dass das Gerät "verloren geht", und es wird angenommen, dass die Änderung des Lichts einer Änderung des Standorts entspricht. Stabile Licht Ebenen in einem Bereich führen zu einer besseren Nachverfolgung.

Jede Beleuchtung im Außenbereich kann auch Instabilität in der Nachverfolgung verursachen, da die Sonne im Laufe der Zeit beträchtlich variieren kann. Beispielsweise kann die Nachverfolgung im Vergleich zum Sommer im Vergleich zum Winter drastisch zu unterschiedlichen Ergebnissen führen, da das sekundäre Licht außerhalb zu unterschiedlichen Jahreszeiten höher sein kann.

Wenn Sie über einen Luxmeter verfügen, ist ein konstanter 500-1000 Lux ein guter Ausgangspunkt. 

#### <a name="types-of-lighting"></a>Arten der Beleuchtung
Verschiedene Arten von Licht in einem Leerzeichen können auch die Nachverfolgung beeinflussen. Lightglüh Birnen mit der laufenden Stromversorgung Pulse: Wenn die AC-Frequenz 50 Hz beträgt, wird das Licht bei 50 Hz Pulse. Bei einem Menschen wird diese pulsierender nicht bemerkt. Die 30 fps-Kamera von hololens sieht jedoch diese Änderungen. einige Frames werden gut beleuchtet, einige werden unzureichend beleuchtet, und einige werden über-verfügbar gemacht, wenn die Kamera versucht, leichte Pulse auszugleichen.

In den USA ist der standardstromfrequency-Standard 60Hz, sodass Glühbirnen-Pulse mit den hololens-Framerate-60Hz-Impulsen mit dem 30-fps-Framerate von hololens abgestimmt werden. Viele Länder verfügen jedoch über einen AC-Häufigkeits Standard von 50Hz, d. h., es werden einige hololens-Frames während der Pulse verwendet, andere hingegen nicht. Insbesondere ist es bekannt, dass die Leuchtstoff Beleuchtung in Europa Probleme verursacht hat. 

Es gibt einige Dinge, die Sie versuchen können, Probleme beim Flimmern zu beheben. Temperatur, Glühbirnen Alter und Aufwärm Zyklen sind häufige Gründe für das fluoroering und das Austauschen von Glühbirnen. Das verschärfen von Glühbirnen und die Sicherstellung, dass die aktuellen Zeichnungen konstant sind, können auch 

### <a name="items-in-a-space"></a>Elemente in einem Leerzeichen
Hololens verwendet einzigartige Umgebungs Merkmale, auch bekannt als *Features*, um sich selbst in einem Bereich zu finden. 

Ein Gerät kann fast nie in einem Funktions Armen Bereich nachverfolgt werden, da das Gerät nicht weiß, wo er sich befindet. Das Hinzufügen von Features zu den Wänden eines leer Zeichens ist in der Regel eine gute Möglichkeit zur Verbesserung der Überwachung. Poster, Symbole, die an eine Wand, Werke, eindeutige Objekte oder andere ähnliche Elemente weitergeleitet werden. Ein Messtisch ist ein gutes Beispiel für eine Umgebung, die zu einer guten Nachverfolgung führt. es gibt viele verschiedene Features in einem einzelnen Bereich. 

Verwenden Sie darüber hinaus eindeutige Features im gleichen Bereich. Das gleiche Poster, das mehrmals über einer Wand wiederholt wird, führt z. b. zu Geräte Verwirrung, da die hololens nicht wissen, welche der sich wiederholenden Poster Sie sehen. Eine gängige Methode zum Hinzufügen eindeutiger Features ist die Verwendung von Linien des Maskierungs Bands, um eindeutige, nicht wiederholende Muster entlang der Wände und des Boden Raums eines leer Zeichens zu erstellen. 

Eine gute Frage ist: Wenn Sie nur einen kleinen Teil der Szene gesehen haben, können Sie sich im Raum eindeutig Auffinden? Wenn dies nicht der Fall ist, ist es wahrscheinlich, dass das Gerät ebenfalls Probleme nachverfolgt.

#### <a name="wormholes"></a>Wurmlöcher
Wenn Sie über zwei Bereiche oder Bereiche verfügen, die gleich aussehen, könnte der Tracker vermuten, dass Sie identisch sind. Dies hat zur Folge, dass sich das Gerät an einem anderen Ort befindet. Diese Typen von wiederkehrenden Bereichen werden als *Wurmlöcher*bezeichnet. 

Um Wurm Lücken zu verhindern, versuchen Sie, identische Bereiche im gleichen Bereich zu verhindern. Identische Bereiche können auch Factory-Stationen, Fenster in einem Gebäude, Server Racks oder Arbeitsstationen enthalten. Durch das bezeichnen von Bereichen oder das Hinzufügen eindeutiger Features zu jedem ähnlich aussehenden Bereich können Wurm Lücken verringert werden.

### <a name="qr-codes-in-environments"></a>QR-Codes in Umgebungen.
Hololens können [QR-Codes](qr-code-tracking.md) aus mehreren Gründen verwenden, wie z. b. das bezeichnen von Objekten oder das Bereitstellen zusätzlicher Kontext für Umgebungen. Sie können jedoch auch zur Verbesserung der Überwachungs Qualität verwendet werden. Hololens verwenden automatisch die QR-Codes, um eine Zuordnung zu erstellen, auch wenn Sie nicht die in den Codes eingebetteten Daten verarbeiten.

Wenn Sie QR-Codes verwenden, um die Nachverfolgung zu unterstützen, benötigen Sie zwei bis drei Codes innerhalb eines bestimmten Sicht Felds. In vielen Szenarien bedeutet dies, dass Sie einen QR-Code alle 2-3 Meter oder 6-9 Füße platzieren.

Stellen Sie sicher, dass die QR-Codes flach und eng an Wände oder andere Oberflächen angefügt sind.

Bewährte Methoden zum Erstellen und Drucken von QR-Codes finden Sie unter [bewährte Methoden für die Erkennung von QR-Codes](qr-code-tracking.md#best-practices-for-qr-code-detection).
 
### <a name="movement-in-a-space"></a>Bewegung in einem Leerzeichen
Wenn sich Ihre Umgebung ständig verschiebt und ändert, verfügt das Gerät nicht über stabile Features, die für das Gerät zu finden sind. 

Die verschiebenden Objekte, die sich in einem Leerzeichen befinden, einschließlich der Personen, desto einfacher ist es, die Nachverfolgung zu verlieren. Das Verschieben von baubändern, Elementen in verschiedenen Konstruktions Zuständen und vielen Personen in einem Bereich hat bekanntermaßen Probleme Nachverfolgung verursacht.

Die hololens können schnell an diese Änderungen angepasst werden, jedoch nur, wenn dieser Bereich für das Gerät eindeutig sichtbar ist. Bereiche, die nicht als häufig angesehen werden, können hinter der Realität liegen, was zu Fehlern in der räumlichen Karte führen kann. Ein Benutzer scannt z. b. einen Freund und schaltet sich um, während der Friend den Raum verlässt. Eine "inaktive" Darstellung des Friend behält die räumlichen Daten der Zuordnung bei, bis der Benutzer den nun leeren Bereich erneut scannt.
 
### <a name="proximity-of-the-user-to-items-in-the-space"></a>Benutzer Nähe zu Elementen im Raum
Ähnlich wie bei der Konzentration von Objekten auf Objekte, die sich in der Nähe der Augen befinden, kämpfen hololens, wenn sich Objekte in der Nähe der Kameras befinden. Wenn ein Objekt zu nah ist, um mit beiden Kameras sichtbar zu sein, oder wenn ein Objekt eine Kamera blockiert, hat das Gerät weitaus mehr Probleme bei der Überwachung des Objekts. 

Die Kameras können nicht mehr als 15cm von einem Objekt sehen.
 
### <a name="surfaces-in-a-space"></a>Oberflächen in einem Leerzeichen
Stark reflektierenden Oberflächen werden wahrscheinlich unterschiedlich aussehen, abhängig vom Winkel, der sich auf die Überwachung auswirkt. Sehen Sie sich ein brandneues Auto an. Wenn Sie es herum bewegen, reflektiert das Licht, und es werden verschiedene Objekte auf der Oberfläche angezeigt, während Sie sich bewegen. Die unterschiedlichen Objekte, die auf der-Oberfläche reflektiert werden, stellen eine veränderliche Umgebung dar, und das Gerät verliert die Nachverfolgung.

Weniger glänzende Objekte können leichter nachverfolgt werden.

### <a name="wifi-fingerprint-considerations"></a>Überlegungen WiFi
Solange WiFi aktiviert ist, werden Kartendaten mit einem WiFi-Fingerabdruck korreliert, auch wenn keine Verbindung mit einem eigentlichen WiFi-Netzwerk/-Router besteht. Ohne WiFi-Informationen sind das Leerzeichen und die Hologramme möglicherweise langsamer zu erkennen. Wenn sich die WLAN-Signale erheblich ändern, kann das Gerät annehmen, dass es sich in einem anderen Raum befindet.

Die Netzwerk Identifizierung (d.h. SSID, Mac-Adresse) wird nicht an Microsoft gesendet, und alle WiFi-Verweise werden lokal auf den hololens gespeichert.

## <a name="mapping-new-spaces"></a>Zuordnung neuer Leerzeichen
Wenn Sie ein neues Leerzeichen eingeben (oder ein vorhandenes laden), wird eine Mesh-Grafik angezeigt, die den Bereich verteilt. Dies bedeutet, dass Ihr Gerät Ihrer Umgebung entspricht. Während ein hololens im Laufe der Zeit einen Raum erfährt, gibt es [Tipps und Tricks, um Leerzeichen](use-hololens-in-new-spaces.md)zuzuordnen. 

## <a name="environment-management"></a>Umgebungs Verwaltung
Es gibt zwei Einstellungen, mit denen die Benutzer die Möglichkeit haben, Hologramme zu "bereinigen" und "hololens" ein Leerzeichen zu "vergessen".  Sie sind in "holograms und Umgebungen" in der App "Einstellungen" vorhanden, wobei die zweite Einstellung auch unter "Datenschutz" in der App "Einstellungen" angezeigt wird.

1.  Löschen von nahe gelegenen holograms – indem Sie diese Einstellung auswählen, löschen hololens alle verankerten Hologramme und alle gespeicherten Kartendaten für den "aktuellen Raum", in dem sich das Gerät befindet.  Ein neuer Karten Abschnitt wird erstellt und in der Datenbank für diesen Speicherort gespeichert, sobald holograms wieder im gleichen Bereich abgelegt werden.

2.  Alle holograms löschen – wenn Sie diese Einstellung auswählen, werden hololens alle Zuordnungs Daten löschen und Hologramme in den gesamten Daten Bank Bereichen verankert.  Es werden keine holograms wiedererkannt, und alle Hologramme müssen neu platziert werden, um Kartenabschnitte in der Datenbank zu speichern.


## <a name="hologram-quality"></a>Hologram-Qualität

Holograms können in Ihrer Umgebung platziert werden – hoch, niedrig und alle um Sie – Sie werden jedoch über einen [Holographic-Frame](holographic-frame.md) angezeigt, der vor ihren Augen liegt. Um die beste Ansicht zu erhalten, stellen Sie sicher, dass Sie Ihr Gerät anpassen, damit Sie den gesamten Frame sehen können. Und erfahren Sie nicht, wie Sie Ihre Umgebung durchlaufen und entdecken!

Damit Ihre [Hologramme](hologram.md) scharf, klar und stabil aussehen, müssen ihre hololens nur für Sie abgestimmt werden. Wenn Sie Ihre hololens zum ersten Mal einrichten, werden Sie durch diesen Vorgang geleitet. Wenn holograms später nicht mehr richtig aussehen oder viele Fehler auftreten, können Sie Anpassungen vornehmen.

Wenn Sie Probleme bei der Zuordnung von Leerzeichen haben, versuchen Sie, nahe gelegene Hologramme zu löschen und den Speicherplatz neu zuzuordnen.

### <a name="calibration"></a>Energie

Wenn Ihre Hologramme jitterie oder wacklig aussehen, oder wenn Sie Probleme beim Platzieren von holograms haben, müssen Sie zunächst die [Kalibrierungs-App](calibration.md)ausprobieren. Diese APP kann auch hilfreich sein, wenn Sie bei der Verwendung von hololens Probleme haben.

Wechseln Sie zu Einstellungen > System > Hilfsprogramme, um zur Kalibrierungs-APP zu gelangen. Wählen Sie Kalibrierung öffnen aus, und befolgen Sie die Anweisungen.

Wenn Sie die Kalibrierungs-app ausführen und weiterhin Probleme mit der – Hologramm-Qualität auftreten, oder wenn Sie eine häufige Meldung "Nachverfolgung verloren" sehen, testen Sie die Sensor Optimierungs-app. Wechseln Sie zu Einstellungen > System > Hilfsprogramme, wählen Sie Sensor Optimierung öffnen aus, und befolgen Sie die Anweisungen.

Wenn eine andere Person ihre hololens verwendet, sollten Sie die Kalibrierungs-App zuerst ausführen, damit das Gerät ordnungsgemäß eingerichtet ist.

## <a name="see-also"></a>Siehe auch
* [Gestaltung von räumlicher Abbildung](spatial-mapping-design.md)
* [Hologramme](hologram.md)
* [Kalibrierung](calibration.md)
* [Verwenden von HoloLens in neuen Räumen](use-hololens-in-new-spaces.md)
