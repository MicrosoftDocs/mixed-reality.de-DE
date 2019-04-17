---
title: Mixed Reality-App-Typen
description: Einer der Vorteile bei der Entwicklung von apps für Windows Mixed Reality ist, dass es ein Spektrum an Funktionen, die die Plattform zu überlagern von LED-Informationen über aktuelle Environmentl eines Benutzers aus vollbildschirmanwendungen, virtuellen Umgebungen unterstützen kann.
author: rwinj
ms.author: willyang
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, entwerfen, app-Muster
ms.openlocfilehash: 97f8039dcd9bbf8ee3d6c7be926db16b60a76b97
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593708"
---
# <a name="types-of-mixed-reality-apps"></a>Mixed Reality-App-Typen

Einer der Vorteile bei der Entwicklung von apps für Windows Mixed Reality ist, dass es ein Spektrum an Funktionen, die die Plattform unterstützt werden. Von der vollbildschirmanwendungen, virtuelle Umgebungen zu hell Informationen, die Schichten über eine aktuelle benutzerumgebung bietet Windows Mixed Reality einen robusten Satz von Tools, die Erfahrung zum Leben zu erwecken. Es ist wichtig für den Ersteller einer app zu einem frühen Zeitpunkt in ihren Entwicklungsprozess, die auf diesem Spektrum, wo ihre Erfahrungen liegt. Diese Entscheidung wirkt sich sowohl die Zusammensetzung der app-Design und der technologischen Pfad für die Entwicklung letztlich.

## <a name="enhanced-environment-apps-hololens-only"></a>Verbesserte Umgebung apps (nur für HoloLens)

Eine der effektivsten Möglichkeiten, die gemischte Realität Wert für Benutzer bietet ist durch die Erleichterung der Platzierung von digitaler Informationen oder den Inhalt in die aktuelle Umgebung des Benutzers. Dies ist eine app für die erweiterte Umgebung. Dieser Ansatz ist häufig für apps, in denen die kontextbezogene Platzierung von digitalen Inhalten in der Praxis ist von größter Bedeutung bzw. ist der Schlüssel "present", während ihre Erfahrungen mit dem realen Umgebung des Benutzers beibehalten. Dieser Ansatz ermöglicht es auch Benutzer problemlos Verschieben von Aufgaben der realen Welt zu digitalen Aufgaben und wieder ganz einfach, und ist sogar noch mehr an Glaubwürdigkeit gewinnt um, die die mixed Reality-apps Versprechen, die dem Benutzer angezeigt wird, wirklich Teil ihrer Umgebung sind.

![Verbesserte Umgebung apps](images/enhancedenvironmentapps-640px.jpg)<br>
*Verbesserte Umgebung apps*

**Beispielverwendungen**
* Ein mixed Reality-Editor-Stil-app, mit dem Benutzer zu erstellen, und platzieren die Anmerkungen zu dieser Version für ihre Umgebung
* Eine Fernsehgerät mixed Reality-app platziert wird, in einen anderen Ort für die Anzeige
* Gemischte Realität Kochen app platziert wird, über die Küche Insel an, um eine Kochen Aufgabe unterstützen
* Ein mixed Reality-app, das Benutzern das Gefühl der "x-Ray Vision" bietet (z. B. ggf. ein Hologramm platziert werden, auf der Basis von und imitiert einen realen-Objekt, gleichzeitig werden den Benutzer holografisch "darin" angezeigt)
* Mixed Reality-Anmerkungen gespeichert, in einer Factory die erforderlichen Informationen für den Worker zu erteilen
* Mixed Reality Wayfinding in einem Office-Bereich
* Mixed Reality als Desktop-Umgebungen (d. h. Erfahrungen Brettspiel-Stil)
* Mixed Reality-Kommunikations-apps wie Skype

## <a name="blended-environment-apps"></a>Gemischte Umgebung apps

Windows Mixed Reality Möglichkeit erkennen, und ordnen Sie die Umgebung des Benutzers erhält, kann die zum Erstellen einer digitalen Ebene, die vollständig des Benutzers Speicherplatz auf dem gelegt werden kann. Dünne Schicht berücksichtigt, die Form und die Grenzen der Umgebung des Benutzers, aber die app kann zum Transformieren von bestimmten Elementen, die am besten geeignet ist, um den Benutzer in der app tauchen auszuwählen. Dies ist eine kombinierten Umgebung-app bezeichnet. Im Gegensatz zu einer erweiterten Umgebung-app möglicherweise kombinierten Umgebung apps nur wichtig genug der Umgebung am besten verwenden Sie die Zusammensetzung für ermutigend bestimmter Benutzerverhalten (z. B. ermutigend verschieben oder Durchsuchen) oder indem Sie Elemente mit Änderungen (eine Küche ersetzen Zähler ist praktisch ein Skin zugewiesen um einen anderen Flächenmuster anzuzeigen). Diese Art von Umgebung auch ein Element in ein ganz anderes Objekt transformieren kann, aber behalten Sie die groben Abmessungen des Objekts als Basis (eine Küche Dateninsel wird umgewandelt in ein Transportpapierkorb bei einem Crime Krimi Spiel).

![Gemischte Umgebung apps](images/blendedenvironmentapps-640px.jpg)<br>
*Gemischte Umgebung apps*

**Beispielverwendungen**
* Eine innere Entwurf mixed Reality-app, die Wände, Countertops oder Stockwerken in unterschiedlichen Farben und Muster zeichnen können
* Ein mixed Reality-app, die Automobilindustrie Designer einen Ebene neue Iterationen beim Design für eine anstehende Auto-Aktualisierung auf ein vorhandenes Auto ermöglicht.
* Eine Bett "abgedeckt" und durch ein mixed Reality Obst eigenständiger im Spiel für Kinder ersetzt
* Eine – "abgedeckt" und ersetzt, die mit einer mixed Reality Transportpapierkorb in einem Crime Krimi-Spiel
* Ein hängender Laternen "abgedeckt" und durch Wegweiser mit ungefähr die gleiche Form und die Dimension ersetzt
* Eine app, die Benutzern Blast-Lücken in ihren realen oder eine immersive Welt Wände, ermöglicht, was eine magische Welt zugänglich machen.

## <a name="immersive-environment-apps"></a>Immersive Umgebung apps

Immersive Umgebung apps werden in einer Umgebung, die vollständig ändert sich der Benutzer weltweit zentriert und können in einer anderen Zeit und Speicherplatz platziert. Diese Umgebungen können sehr reale, erstellen faszinierende und schönsten Benutzeroberflächen, die nur durch den Ersteller der app die Vorstellungskraft begrenzt werden können. Im Gegensatz zur kombinierten Umgebung apps Sobald Windows Mixed Reality Speicherplatz des Benutzers identifiziert eine immersive Umgebung app möglicherweise völlig ignorieren die aktuelle Umgebung des Benutzers und gesamte Bestand durch einen eigenen ersetzen. Diese Erfahrungen können auch vollständig trennen, Zeit und Speicherplatz, was bedeutet, dass ein Benutzer durch die Straßen von "ROME" in ein Eintauchen, bleiben Sie immer noch in der realen Welt Speicherplatz relativ führen konnte. Kontext der realen Umgebung kann nicht zu einer app immersive Umgebung wichtig sein.

![Immersive Umgebung apps](images/windows-mixed-reality-640px.jpg)<br>
*Immersive Umgebung apps*

**Beispielverwendungen**
* Eine immersive app, die einen Benutzer, der ein Leerzeichen vollkommen unabhängig vom eigenen tour kann (d. h. Schritt für Schritt durch eine berühmten erstellen, Museum, beliebten Ort)
* Eine immersive app, die ein Ereignis oder Szenarios im Zusammenhang mit der Benutzer (d. h. eine Schlacht oder Leistung) orchestriert.

## <a name="see-also"></a>Siehe auch
* [Übersicht über die Entwicklung](development-overview.md)
* [App-Modell](app-model.md)
* [App-Ansichten](app-views.md)
