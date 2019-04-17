---
title: Freigegebene Funktionen in mixed reality
description: Holographic apps können räumliche Anker aus einem HoloLens zu einem anderen Benutzer Rendern ggf. ein Hologramm an derselben Stelle in der realen Welt auf mehreren Geräten gemeinsam nutzen.
author: thetuvix
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: Gemischte Realität, Hologramm, räumliche Anker, mehrere Benutzer, mehrere freigegebene Benutzeroberfläche
ms.openlocfilehash: b27da1e73c927a26e33746cd2db08e67c6f70acc
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605134"
---
# <a name="shared-experiences-in-mixed-reality"></a>Freigegebene Funktionen in mixed reality

Hologramme müssen nicht nur einen Benutzer privat bleiben. Holographic apps freigeben können [räumliche Anker](coordinate-systems.md) aus einem HoloLens, iOS oder Android-Gerät zu einem anderen Benutzern ermöglichen, ggf. ein Hologramm an derselben Stelle in der realen Welt auf mehreren Geräten zu rendern.

## <a name="six-questions-to-define-shared-scenarios"></a>Sechs Fragen zum Definieren von freigegebenen Szenarios

Bevor Sie den Entwurf für freigegebene Funktionen beginnen, ist es wichtig, definieren die Zielszenarios kennen. Diese Szenarien verdeutlichen, was Sie entwerfen und herstellen ein allgemeines Vokabular, um zu vergleichen und gegenüberstellen von Funktionen, die in Ihrer Umgebung erforderlich sind. Das Kernproblem und verschiedene Angriffsmethoden für Lösungen zu verstehen, ist entscheidend für hin Chancen, die in dieses neue Medium.

Durch interne Prototypen und auswertungen von unserem Partneragenturen HoloLens haben wir sechs Fragen, um Ihnen das Definieren von freigegebenen Szenarios erstellt. Diese Fragen bilden ein Framework, das nicht als vollständig ist, können Sie die wichtigen Attribute Ihrer Szenarien zu verwandeln.

### <a name="1-how-are-they-sharing"></a>1. Wie werden sie gemeinsam nutzen?

Eine Präsentation kann von einem einzelnen virtuellen Benutzer, geführt werden, während mehrere Benutzer können zusammenarbeiten, oder ein Lehrer kann bieten den virtuellen Schüler/Studenten, die Arbeit mit virtuellen Materialien, die Komplexität des Erfahrungen erhöht basierend auf der Ebene der Behörde, die ein Benutzer hat oder in einem Szenario möglich.

![Mann und Frauen mit Holograph für Tabelle](images/man-and-women-with-holograph-on-table-500px.png)

Es gibt viele Möglichkeiten zum Freigeben, aber wir haben festgestellt, dass die meisten von ihnen in drei Kategorien einordnen:
* **Präsentation**: Wenn der gleiche Inhalt an mehrere Benutzer angezeigt wird. Zum Beispiel: Professor ist für mehrere Schüler/Studenten, die mit dem gleichen holographic Material für alle Benutzer angezeigt wird, eine Vorlesung gewähren. Die Professor möglicherweise jedoch seinen eigenen Hinweise und die Anmerkungen zu dieser Version, die möglicherweise nicht für andere Benutzer sichtbar.
* **Zusammenarbeit**: Wenn Personen arbeiten zusammen, um einige allgemeine Ziele zu erreichen. Zum Beispiel: Die Professor erhielten Sie ein Projekt erfahren Sie mehr über einen Kern oder ausführen. Schüler/Studenten, kombinieren Sie und erstellen eine freigegebene Fähigkeiten Lab-Umgebung medizinische Schüler/Studenten zur Zusammenarbeit, die auf dem Kern-Modell aus, und erfahren, wodurch.
* **Anleitungen**: Wenn eine Person eine Person zur Lösung eines Problems in einer Interaktion mit mehr 1: 1-Format unterstützt. Zum Beispiel: Die Professor Ihnen Tipps an Schüler/Student ein, wenn er das Herzstück oder Fähigkeiten Lab in der freigegebenen Umgebung ausgeführt wird.

### <a name="2-what-is-the-group-size"></a>2. Was ist die Größe der Gruppe?

**1: 1-** Freigabe von Erlebnissen können Sie eine sichere Baseline ermöglichen und idealerweise Ihre Proofs of Concept erstellen auf dieser Ebene erstellt werden. Beachten Sie jedoch, dass große Gruppen (über 6 Personen) freigeben zu schwierigkeiten aus technischen (Daten und Netzwerke), soziale Medien führen kann (die Auswirkungen der in einen Raum mit [mehrere Avatare](https://vimeo.com/160704056)). Komplexität wächst exponentiell beim Wechseln vom **kleine** zu **große Gruppen**.

Wir haben festgestellt, dass die Anforderungen von Gruppen in drei Kategorien von Größe fallen können:
* 1:1
* Kleine < 7
* Large >= 7

Gruppengröße ist für eine wichtige Frage, da er wirkt sich auf:
* Darstellungen von Personen in der holografischen Speicherplatz
* Skalieren von Objekten
* Skalierung der Umgebung

### <a name="3-where-is-everyone"></a>3. Wo alle sind?

Die Stärke von mixed Reality ins Spiel, wenn es sich bei eine gemeinsame Erfahrung am gleichen Speicherort stattfinden kann. Nennen wir dies **zusammengestellte**. Im Gegensatz dazu aufrufen, wenn die Gruppe verteilt wird und mindestens einem Teilnehmer nicht im selben physischen Raum (wie häufig der Fall bei VR) wir, einen Remotebenutzer. Häufig ist es der Fall, die Ihre Gruppe **sowohl** zusammengestellte und remote-Teilnehmer (z. B. zwei Gruppen in Konferenzräumen).

![Drei Personen mit Holograph für Tabelle](images/three-people-with-holograph-on-table-500px.png)

Folgende Kategorien können vermitteln, in denen Benutzer gespeichert sind:
* Zusammengestellt: Alle Benutzer werden in den gleichen physischen Raum.
* Remotecomputer: Alle Benutzer werden in separate physische Bereiche.
* Beide: Ihre Benutzer, eine Mischung aus zusammengestellten und remote-Leerzeichen.

Einige Gründe, warum diese Frage entscheidend ist, da er wirkt sich auf:
* Wie Personen zu kommunizieren?
* Zum Beispiel: Gibt an, ob sie Avatare aufweisen sollen?
* Welche Objekte angezeigt. Werden alle Objekte werden gemeinsam genutzt?
* Gibt an, ob wir möchten Sie an ihre Umgebung anpassen?

### <a name="4-when-are-they-sharing"></a>4. Wenn freigeben sie?

Dann in der Regel sind dies **synchrone** kommt, wenn freigegebene Umgebungen in Betracht kommen: Wir machen alle diese zusammen. Aber umfassen ein einzelnes virtuelles Element, das von einem anderen Benutzer hinzugefügt wurde, und Sie haben eine **asynchrone** Szenario. Angenommen Sie, eine Notiz oder Sprachnachricht, die Links in einer virtuellen Umgebung. Wie behandeln Sie 100 virtuelle Sprachnotizen, die Ihren Entwurf bleiben? Was geschieht, wenn davon unter Dutzenden von Personen mit unterschiedlichen Datenschutz?

Beachten Sie, Ihre Erfahrungen als eine dieser Kategorien Zeit:
* **Synchron**: Freigeben von holografischen Benutzeroberfläche zur gleichen Zeit. Zum Beispiel: Zwei Schüler und Studenten das Lab Fähigkeiten zur gleichen Zeit ausführen.
* **Asynchron**: Freigeben von holografischen Benutzeroberfläche zu unterschiedlichen Zeitpunkten. Zum Beispiel: Zwei Schüler und Studenten die Fähigkeiten Übungseinheit durchführen, jedoch in separaten Abschnitten zu unterschiedlichen Zeiten arbeiten.
* **Both**: Benutzern werden manchmal synchron aber in anderen Fällen asynchron frei. Zum Beispiel: Professor Abstufung der Zuweisung von Studenten verlassen Anmerkungen zu dieser Version für Studenten zu einem späteren Zeitpunkt für den nächsten Tag ausgeführt.

Einige Gründe, warum diese Frage wichtig, ist da er wirkt sich auf:
* Die Dauerhaftigkeit Objekt und der Umgebung. Zum Beispiel: Speichern die Zustände, sodass sie abgerufen werden können.
* Perspektive des Benutzers. Zum Beispiel: Merken vielleicht, was der Benutzer ansah beim Verlassen der Anmerkungen zu dieser Version.

### <a name="5-how-similar-are-their-physical-environments"></a>5. Wie ihre physischen Umgebungen ähneln?

Die Wahrscheinlichkeit, dass zwei identische realen Umgebungen, außerhalb zusammengestellten Benutzeroberflächen, ist slim, es sei denn, diese Umgebungen vorgesehen sind, identisch sein. Sie sind eher haben **ähnliche** Umgebungen. Z.B. Konferenzräume ähneln, sie haben in der Regel eine zentral gespeicherte Tabelle Stühle enthaltender. Wohnzimmer, in der Regel auf der anderen Seite sind **unterschiedlicher** und kann eine beliebige Anzahl von Teile Möbel in einem Array unendliche Layouts enthalten.

![Holograph für Tabelle](images/holograph-on-table-500px.png)

Beachten Sie, Ihre Freigaben Erfahrungen, die in einer dieser zwei Kategorien:
* **Ähnlich wie**: Umgebungen, die ähnliche Möbel, Umgebungslicht und Sound, haben tendenziell physischen Größe. Zum Beispiel: Professor wird Vorlesung Hall ein, und Schüler und Studenten sind in Vorlesung Hall b Vorlesung Hall ein möglicherweise weniger Stühle als B jedoch beide möglicherweise eine physische – Hologramme auf platzieren.
* **Unterschiedlicher**: Umgebungen, die in Möbel-Einstellungen, Raum Größen, helle und sound Überlegungen sehr unterschiedlich sind. Zum Beispiel: Professor ist in einem Raum konzentrieren, während der Schüler und Studenten in einer großen Vorlesung Hall mit Schüler/Studenten und Lehrkräfte gefüllt sind.

Es ist wichtig, über die Umgebung zu betrachten, wie sie beeinflussen:
* Wie kommt es Personen diese Objekte. Zum Beispiel: Wenn Ihre Umgebung am besten für eine Tabelle aus, und der Benutzer keine Tabelle hat? Oder auf einer flachen Floor-Oberfläche, aber der Benutzer ein Überladen Leerzeichen enthält.
* Die Skalierung der Objekte. Zum Beispiel: Platzieren von einem menschlichen 6 FT-Modell für eine Tabelle kann eine Herausforderung sein, aber ein Kern-Modell funktioniert hervorragend.

### <a name="6-what-devices-are-they-using"></a>6. Welche Geräte verwenden sie?

Heute Sie wahrscheinlich häufig freigegebene Umgebungen zwischen zwei finden Sie unter **immersive Geräte** (unterscheiden sich diese Geräte etwas im Hinblick auf die Schaltflächen und relative-Funktion, aber nicht enorm) oder zwei **holographic-Geräten** erhält die Lösungen, die an diese Geräte abgezielt wird. Aber in Betracht ziehen, die **2D Geräte** (Mobile/Desktop-Teilnehmer oder Beobachter) werden erforderlichen berücksichtigt, insbesondere in Situationen von **gemischten 2D- und 3D-Spiele Geräte**. Grundlegendes zu den Arten von Geräten, die die Teilnehmer verwendet werden, ist wichtig, nicht nur, weil sie unterschiedliche Genauigkeit und Einschränkungen von Daten und Chancen aufweisen, aber da die Benutzer eindeutige Erwartungen für jede Plattform.

## <a name="exploring-the-potential-of-shared-experiences"></a>Untersuchen das Potenzial von gemeinsamen Erfahrungen

Antworten auf die Fragen oben können kombiniert werden, zum besseren Verständnis von Ihrem Szenario mit freigegebenem, crystallizing die Herausforderungen, wie Sie die Benutzeroberfläche erweitern. Für das Team bei Microsoft verwenden Sie diese geholfen, eine Roadmap für die Verbesserung von der Erfahrungen herzustellen wir heute, Grundlegendes zu den Nuance dieser komplexen Probleme und wie Sie profitieren von gemeinsamen Erfahrungen in mixed Reality.

Betrachten Sie beispielsweise eine Skype Szenarien aus dem HoloLens-Start: ein Benutzer bearbeitet [so eine unterbrochene Lichtschalter](https://www.youtube.com/watch?v=iBfzs3G8BEA) mit Hilfe von einem Remote-positionierte-Experten.

![Beheben als Lichtschalter mit über Skype-Unterstützung für HoloLens](images/fix-a-broken-switch-with-hololens-640px.jpg)

<i>Bietet ein Experte <b>1:1</b> Anleitungen aus seinem <b>2D</b>, desktop-PC zu einem Benutzer, der eine <b>3D, mixed Reality-</b> Gerät. Die <b>Anleitungen</b> ist <b>synchrone</b> und die physischen Umgebungen sind <b>unterschiedlicher</b>.</i>

Eine Erfahrung wie dieser ist eine Schritt-Änderung aus unseren Erfahrungen mit aktuellen – das Paradigma der Video- und in ein neues Medium anwenden. Aber wie wir in Zukunft aussehen, wir müssen besser definieren Sie die Möglichkeit, unsere Szenarien und Umgebungen, die die Stärke von mixed Reality widerspiegeln.

Betrachten Sie die [OnSight Teamarbeitstool](https://www.youtube.com/watch?v=ZOWQp0-Bkkw) von der NASA Jet Propulsion Laboratory entwickelt. Datenanalysten, die auf Daten aus der Mars-Rover Missionen ganz arbeiten können Zusammenarbeit mit Kollegen in Echtzeit innerhalb der Daten aus der bricht-Landschaft.

![Remote getrennt zwischen Kollegen zusammenarbeiten, um die Arbeit für den Mars-Rover planen](images/onsight-nasa-jpl.gif)

<i>Ein Scientist untersucht eine Umgebung mit einem <b>3D, mixed Reality-</b> Gerät mit einer <b>kleine</b> Gruppe <b>remote</b> Kollegen teilen, indem <b>3D- und 2D-spielen</b> Geräte. Die <b>Zusammenarbeit</b> ist <b>synchrone</b> (aber asynchron revisited sein kann) und die physischen Umgebungen sind (virtuell) <b>ähnliche</b>.</i>

Funktionen wie das OnSight stellen neue Möglichkeiten für die Zusammenarbeit. Von physisch Hinweise auf Elemente in der virtuellen Umgebung neben einem Kollegen ständigen und Freigeben ihrer Perspektive, wie sie ihre Ergebnisse erläutert. OnSight verwendet den Fokus von Immersion- und Anwesenheitsfunktionen Freigabe Erfahrungen in mixed Reality überdenken.

Intuitive Zusammenarbeit ist das Fundament der Konversation und arbeiten zusammen, und ist von entscheidender Bedeutung zu verstehen, wie wir diese Intuition auf die Komplexität von mixed Reality anwenden können. Wenn wir können nicht nur Freigabe Erfahrungen in mixed Reality neu erstellen, aber sie steigern der Leistung, wird es einen Paradigmenwechsel für die Zukunft der Arbeit sein. Entwerfen für freigegebene Funktionen in mixed Reality ist Speicherplatz für neue und interessante –, und wir sind nur am Anfang.

## <a name="get-started-sharing-experiences"></a>Erste Schritte Freigabe von Erlebnissen

Abhängig von Ihrer Anwendung und jedes Szenario werden verschiedene Anforderungen an Ihre gewünschte Funktionalität erzielen. Dazu zählen
* Match-Erstellung: Möglichkeit, die Sitzungen zu erstellen, -Sitzung ankündigen und ermitteln und Laden Sie bestimmte Personen, die sowohl lokal als auch Remote die Sitzung beitreten.
* Verankern Sie die Freigabe: Möglichkeit zum Ausrichten von Koordinaten auf mehreren Geräten in einen gemeinsamen lokalen Raum, sodass Hologramme am selben Ort für alle Personen angezeigt werden.
* Netzwerke: Möglichkeit, positioniert, Interaktionen, und die Bewegungen von Personen und Hologramme synchronisiert wird, im Real-Time für alle Teilnehmer.
* Speichern des Zustands für: Die Fähigkeit zum Speichern von – Hologramm Merkmale und Speicherorte im Raum für Mid-Sitzung beitreten, denken Sie daran zu einem späteren Zeitpunkt, Stabilität für Netzwerkprobleme.


Die Taste, um geteilte ist, mehrere Benutzer, die die gleichen Hologramme in der Welt auf ihre eigenen Geräte, die häufig erfolgt anhand der Anker zum Ausrichten von Koordinaten auf Geräten angezeigt wird.
Zum Freigeben Anker verwenden die <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure räumliche Anker</a>:
* Zuerst wird der Benutzer die Hologramm platziert.
* App erstellt ein [räumliche Anker](coordinate-systems.md) anheften, Hologramm genau in der ganzen Welt.
* Die Anker können gemeinsam genutzt werden, für HoloLens, IOS- und Android-Geräte über die <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure räumliche Anker</a>. 

Mit einer freigegebenen räumliche Anker hat die app auf jedem Gerät jetzt eine allgemeine Koordinatensystem, die in der Inhalt platziert werden können. Nachdem die app, zum Positionieren und die Hologramm am selben Ort zu orientieren sicherstellen kann.
Auf HoloLens-Geräten können Sie auch den Anker offline von einem Gerät in eine andere freigeben.  Verwenden Sie die folgenden Links, um entscheiden, was für Ihre Anwendung am besten geeignet ist.


## <a name="see-also"></a>Siehe auch
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure räumliche Anker</a>
* [Räumliche Anker in DirectX freigegeben](shared-spatial-anchors-in-directx.md)
* [Freigegebene Funktionen in Unity](shared-experiences-in-unity.md)
* [Spectator anzeigen](spectator-view.md)