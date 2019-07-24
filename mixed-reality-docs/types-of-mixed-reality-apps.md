---
title: Typen von Mixed Reality-apps
description: Einer der Vorteile bei der Entwicklung von Apps für Windows Mixed Reality besteht darin, dass es eine Palette an Erfahrungen gibt, die die Plattform von vollständig immersiven virtuellen Umgebungen unterstützen kann, um Informationen über die aktuelle Umgebung eines Benutzers zu erhalten.
author: rwinj
ms.author: willyang
ms.date: 03/21/2018
ms.topic: article
keywords: Gemischte Windows-Realität, Entwurf, App-Muster
ms.openlocfilehash: 97f8039dcd9bbf8ee3d6c7be926db16b60a76b97
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63549125"
---
# <a name="types-of-mixed-reality-apps"></a>Typen von Mixed Reality-apps

Einer der Vorteile bei der Entwicklung von Apps für Windows Mixed Reality besteht darin, dass es eine Palette von Erfahrungen gibt, die die Plattform unterstützen kann. Von vollständig immersiven, virtuellen Umgebungen bis hin zu hellen Informationen über die aktuelle Umgebung eines Benutzers bietet Windows Mixed Reality einen robusten Satz von Tools, mit denen Sie jede beliebige Umgebung nutzen können. Es ist wichtig, dass ein App-Ersteller frühzeitig im Entwicklungsprozess daran interessiert ist, an welcher Stelle dieses Spektrum liegt. Diese Entscheidung wirkt sich letztendlich sowohl auf die Zusammensetzung des App-Entwurfs als auch auf den technologischen Entwicklungspfad aus.

## <a name="enhanced-environment-apps-hololens-only"></a>Erweiterte Umgebungs-Apps (nur hololens)

Eine der leistungsfähigsten Möglichkeiten, mit der Gemischte Realität den Benutzern Wert einbringen kann, besteht darin, die Platzierung digitaler Informationen oder Inhalte in der aktuellen Umgebung eines Benutzers zu vereinfachen. Dies ist eine erweiterte Umgebungs-app. Diese Vorgehensweise ist bei apps beliebt, bei denen die kontextabhängige Platzierung digitaler Inhalte in der realen Welt von größter Bedeutung ist und/oder die tatsächliche Umgebung der Benutzer in der Praxis "vorhanden" ist. Diese Vorgehensweise ermöglicht es Benutzern auch, problemlos von realen Aufgaben zu digitalen Aufgaben und wieder zurückzukehren, um zu garantieren, dass die gemischten Reality-apps, die der Benutzer sieht, wirklich Teil Ihrer Umgebung sind.

![Erweiterte Umgebungs-apps](images/enhancedenvironmentapps-640px.jpg)<br>
*Erweiterte Umgebungs-apps*

**Verwendungs Beispiele**
* Eine gemischte Reality-App im Editor-Stil, die Benutzern das Erstellen und Platzieren von Notizen in Ihrer Umgebung ermöglicht
* Eine gemischte Reality-TV-APP, die für die Anzeige
* Eine gemischte Reality-APP, die sich über der Kücheninsel befindet, um eine Koch Aufgabe zu unterstützen
* Eine Mixed Reality-APP, die Benutzern das Gefühl der "x-ray-Vision" bietet (d. h. ein – Hologramm, das auf ein reales Objekt gesetzt und es imitiert, gleichzeitig dem Benutzer die Möglichkeit bietet, "darin" zu sehen)
* In einer Factory enthaltene gemischte Reality-Anmerkungen, um die erforderlichen Informationen zu den Mitarbeitern zu senden
* Mixed Reality-Wegsuchen in einem Bürobereich
* Gemischte Realität: richtige-Erfahrungen (z. t. Spiel Stil der Platine)
* Kommunikations-apps mit gemischter Realität wie Skype

## <a name="blended-environment-apps"></a>Apps für gemischte Umgebungen

Angesichts der Fähigkeit von Windows Mixed Reality, die Umgebung des Benutzers zu erkennen und zuzuordnen, ist es in der Lage, eine digitale Ebene zu erstellen, die vollständig auf den Platz des Benutzers überlagert werden kann. Die schlanke Ebene respektiert die Form und die Grenzen der Benutzerumgebung, aber die APP kann bestimmte Elemente transformieren, die sich am besten für das Eintauchen des Benutzers in der APP eignen. Dies wird als gemischte Umgebungs-App bezeichnet. Anders als bei einer erweiterten Umgebungs-APP sind gemischte Umgebungs-Apps möglicherweise nur ausreichend für die Umgebung geeignet, um das jeweilige Benutzer Verhalten (z. b. das fördern von Bewegung oder durchsuchen) und das Ersetzen von Elementen durch Änderungen (eine Küche der Counter ist praktisch erfasst, um ein anderes Kachel Muster anzuzeigen). Diese Art von Umgebung kann sogar ein Element in ein völlig anderes Objekt transformieren, aber dennoch die groben Dimensionen des Objekts als Basis beibehalten (eine Kücheninsel wird in eine dumpfunktion für ein Krimi Spiel für den Krimi transformiert).

![Apps für gemischte Umgebungen](images/blendedenvironmentapps-640px.jpg)<br>
*Apps für gemischte Umgebungen*

**Verwendungs Beispiele**
* Eine gemischte Reality-Design-APP, mit der Wände, gegen Flächen oder Fußböden in verschiedenen Farben und Mustern gezeichnet werden können
* Eine Mixed Reality-APP, die es einem Automobildesigner ermöglicht, neue Entwurfs Iterationen für eine bevorstehende Fahrzeug Aktualisierung über ein vorhandenes Auto zu überlagern
* Ein Bett ist "abgedeckt" und wird durch eine Mischung aus der Realität der Realität im Spiel der Kinder ersetzt.
* Ein Schreibtisch wird "abgedeckt" und durch eine gemischte Realität dumpester in einem Krimi Spiel
* Eine hängende Laterne wird "abgedeckt" und durch Signpost ersetzt, wobei ungefähr dieselbe Form und Dimension verwendet werden.
* Eine APP, die es Benutzern ermöglicht, Löcher in ihren realen oder immersiven weltweiten Wänden zu sprengen, die eine magische Welt offenlegen

## <a name="immersive-environment-apps"></a>Immersive Umgebungs-apps

Immersive Umgebungs-apps sind auf eine Umgebung ausgerichtet, die die Benutzer Welt vollständig ändert und Sie in einer anderen Zeit und in einem anderen Bereich platzieren kann. Diese Umgebungen können sich als sehr real vorstellen, und es werden immersive und aufregende Oberflächen geschaffen, die nur durch die Phantasie der APP-Ersteller eingeschränkt werden. Anders als bei Umgebungen mit gemischten Umgebungen, wenn Windows Mixed Reality den Platz des Benutzers identifiziert, kann eine immersive Umgebungs-APP die aktuelle Umgebung des Benutzers vollständig ignorieren und den gesamten Bestand durch einen eigenen ersetzen. Diese Erfahrungen können auch den Zeit-und Speicherplatz vollständig trennen, d. h. ein Benutzer kann die Straßen von Rom in einem immersiven Erlebnis durchlaufen, während er sich relativ noch in Ihrem realen Raum verbleiben würde. Der Kontext der realen Umgebung ist für eine immersive Umgebungs-App möglicherweise nicht von Bedeutung.

![Immersive Umgebungs-apps](images/windows-mixed-reality-640px.jpg)<br>
*Immersive Umgebungs-apps*

**Verwendungs Beispiele**
* Eine immersive APP, die es einem Benutzer ermöglicht, einen Platz vollständig voneinander getrennt zu machen (d. h. durch einen berühmten Gebäude, ein Museum, beliebte Stadt)
* Eine immersive APP, die ein Ereignis oder Szenario um den Benutzer orchestriert (d. h. einen Kampf oder eine Leistung).

## <a name="see-also"></a>Siehe auch
* [Entwicklung – Übersicht](development-overview.md)
* [App-Modell](app-model.md)
* [App-Ansichten](app-views.md)
