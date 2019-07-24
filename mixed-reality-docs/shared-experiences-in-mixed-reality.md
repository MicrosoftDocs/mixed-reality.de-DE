---
title: Gemeinsam genutzte Umgebungen in gemischter Realität
description: Holographic Apps können räumliche Anker von einem hololens zu einem anderen gemeinsam nutzen, sodass Benutzer ein Hologramm an derselben Stelle in der realen Welt über mehrere Geräte hinweg Rendering können.
author: thetuvix
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: gemeinsam genutzte Benutzeroberflächen, gemischte Realität, Hologram, räumlicher Anker, mehrere Benutzer, mehrere
ms.openlocfilehash: b27da1e73c927a26e33746cd2db08e67c6f70acc
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63518483"
---
# <a name="shared-experiences-in-mixed-reality"></a>Gemeinsam genutzte Umgebungen in gemischter Realität

Holograms müssen nicht nur für einen Benutzer privat bleiben. Holographic Apps können [räumliche Anker](coordinate-systems.md) von einem hololens-, IOS-oder Android-Gerät zu einem anderen gemeinsam nutzen, sodass Benutzer ein Hologramm an derselben Stelle in der realen Welt über mehrere Geräte hinweg Rendering können.

## <a name="six-questions-to-define-shared-scenarios"></a>Sechs Fragen zum Definieren von freigegebenen Szenarien

Bevor Sie mit dem Entwerfen für freigegebene Umgebungen beginnen, ist es wichtig, die Ziel Szenarien zu definieren. In diesen Szenarien wird erläutert, was Sie entwerfen und ein gängiges Vokabular einrichten, mit dem Sie die für Ihre Benutzer Arbeit erforderlichen Features vergleichen und vergleichen können. Wenn Sie das grundlegende Problem und die verschiedenen Lösungsmöglichkeiten verstehen, ist es entscheidend, die Verkaufschancen dieses neuen Mediums zu decken.

Mithilfe interner Prototypen und Explorationen von unseren hololens-Partnerbehörden haben wir sechs Fragen erstellt, um Ihnen beim Definieren von freigegebenen Szenarien zu helfen. Diese Fragen bilden ein Framework, das nicht vollständig ist, um die wichtigen Attribute Ihrer Szenarios zu unterstützen.

### <a name="1-how-are-they-sharing"></a>1. Wie werden Sie gemeinsam genutzt?

Eine Präsentation kann von einem einzelnen virtuellen Benutzer geleitet werden, während mehrere Benutzer zusammenarbeiten können, oder ein Lehrer stellt Anleitungen für virtuelle Schüler und Studenten bereit, die mit virtuellen Materialien arbeiten – die Komplexität der Erfahrungen erhöht sich basierend auf der Ebene der Behörde, die ein Benutzer hat oder kann in einem Szenario vorhanden sein.

![Man und Women mit Holograph für die Tabelle](images/man-and-women-with-holograph-on-table-500px.png)

Es gibt viele Möglichkeiten für die Freigabe, aber wir haben festgestellt, dass die meisten in drei Kategorien unterteilt sind:
* **Präsentation**: Wenn mehrere Benutzer denselben Inhalt angezeigt werden. Zum Beispiel: Ein Professor gibt eine Präsentation an mehrere Studenten aus, die das gleiche Holographic-Material für jeden bereitstellt. Der Professor könnte jedoch seine eigenen Hinweise und Notizen enthalten, die für andere Personen möglicherweise nicht sichtbar sind.
* **Zusammenarbeit**: Wenn die Mitarbeiter zusammenarbeiten, um einige gängige Ziele zu erreichen. Zum Beispiel: Der Professor hat ein Projekt gegeben, um mehr über die Durchführung einer Herzoperation zu erfahren. Schüler/Studenten koppeln und erstellen eine freigegebene Skills Lab-Umgebung, mit der medizinische Studenten am Kernmodell arbeiten und lernen können.
* **Leitfaden**: Wenn eine Person eine Person unterstützt, um ein Problem in einer mehrstufigen Interaktion zu lösen. Zum Beispiel: Der Professor gibt eine Anleitung an einen Schüler/Student, wenn er das Herzstück für das Lab-Labor in der gemeinsamen Umgebung ausführt.

### <a name="2-what-is-the-group-size"></a>2. Was ist die Gruppengröße?

Die **einmalige** Nutzung bietet eine starke Baseline, und im Idealfall kann Ihr Konzept auf dieser Ebene erstellt werden. Beachten Sie aber, dass die Freigabe mit großen Gruppen (über 6 Personen) zu Schwierigkeiten von technischen (Daten und Netzwerken) bis hin zu sozialen Daten führen kann (die Auswirkung der Verwendung eines Raums mit [mehreren Avataren](https://vimeo.com/160704056)). Die Komplexität steigt exponentiell, wenn Sie zwischen **kleinen** und **großen Gruppen**wechseln.

Wir haben festgestellt, dass die Anforderungen von Gruppen in drei Größen Kategorien fallen können:
* 1:1
* Small < 7
* Große > = 7

Die Gruppengröße stellt eine wichtige Frage dar, da sich dies auf Folgendes auswirkt:
* Darstellungen von Menschen in Holographic Space
* Skalieren von Objekten
* Skalieren der Umgebung

### <a name="3-where-is-everyone"></a>3. Wo ist jeder?

Die Stärke der gemischten Realität kommt ins Spiel, wenn eine gemeinsame Nutzung am gleichen Ort stattfinden kann. Wir nennen das **zusammen**gestellte. Wenn die Gruppe dagegen verteilt ist und sich mindestens ein Teilnehmer nicht im selben physischen Raum befindet (was häufig bei VR der Fall ist), wird ein Remote Vorgang aufgerufen. Häufig ist es der Fall, dass Ihre Gruppe **sowohl** zusammengestellte als auch Remote Teilnehmer (z. b. zwei Gruppen in Konferenzräumen) umfasst.

![Drei Personen mit Holograph für die Tabelle](images/three-people-with-holograph-on-table-500px.png)

Die folgenden Kategorien helfen Ihnen, den Speicherort der Benutzer zu vermitteln:
* Zusammengestellt: Alle Ihre Benutzer befinden sich im selben physischen Bereich.
* Gene Alle Ihre Benutzer befinden sich in separaten physischen Räumen.
* Zwar Bei ihren Benutzern handelt es sich um eine Mischung aus zusammengestellten und Remote Plätzen.

Einige Gründe, warum diese Frage entscheidend ist, weil Sie sich auf Folgendes auswirkt:
* Wie werden Personen miteinander kommunizieren?
* Zum Beispiel: Ob Sie über Avatare verfügen sollen?
* Welche Objekte werden angezeigt? Werden alle Objekte freigegeben?
* Ob wir uns an die Umgebung anpassen müssen?

### <a name="4-when-are-they-sharing"></a>4. Wann werden Sie gemeinsam genutzt?

In der Regel sind **synchrone** Erfahrungen zu beachten, wenn die gemeinsame Oberfläche zu beachten ist Wir arbeiten damit. Sie können jedoch ein einzelnes virtuelles Element einschließen, das von einer anderen Person hinzugefügt wurde, und Sie haben ein **asynchrones** Szenario. Stellen Sie sich einen Hinweis oder ein sprach Memo in einer virtuellen Umgebung vor. Wie behandeln Sie 100 Virtual Sprachnotizen im Entwurf? Was geschieht, wenn Sie von Dutzenden von Menschen mit unterschiedlichen Datenschutz Ebenen abweichen?

Sehen Sie sich Ihre Erfahrungen als eine dieser Zeitkategorien an:
* **Synchron**: Gleich Zeitangabe der Holographic-Darstellung. Zum Beispiel: Zwei Schüler und Studenten, die das Skills Lab gleichzeitig durchführen.
* **Asynchron**: Freigeben der Holographic-Darstellung zu unterschiedlichen Zeitpunkten. Zum Beispiel: Zwei Schüler/Studenten, die das Skills Lab ausführen, aber zu unterschiedlichen Zeiten an separaten Abschnitten arbeiten.
* **Beides**: Die Benutzer werden manchmal synchron, aber in anderen Fällen asynchron freigegeben. Zum Beispiel: Der Professor stuft die Zuweisung ein, die von den Schülern zu einem späteren Zeitpunkt durchgeführt wird, und gibt die Notizen für den nächsten Tag aus.

Einige Gründe, warum diese Frage wichtig ist, weil Sie sich auf Folgendes auswirkt:
* Objekt-und Umgebungs Persistenz. Zum Beispiel: Speichern der Zustände, damit Sie abgerufen werden können.
* Benutzer Perspektive. Zum Beispiel: Vielleicht denken Sie daran, was der Benutzer beim hinterlassen von Notizen betrachtet hat.

### <a name="5-how-similar-are-their-physical-environments"></a>5. Wie ähnlich sind ihre physischen Umgebungen?

Die Wahrscheinlichkeit, dass zwei identische reale Umgebungen außerhalb der zusammengestellten Erfahrung vorhanden sind, ist schlank, es sei denn, diese Umgebungen sind so konzipiert, dass Sie identisch sind. Es ist wahrscheinlicher, dass Sie **ähnliche** Umgebungen haben. Beispielsweise sind Konferenzräume ähnlich – Sie haben in der Regel eine zentral lokalisierte Tabelle, die von den Lehrstühlen umgeben ist. Wohn Räume sind dagegen normalerweise unter **schiedlich** und können eine beliebige Anzahl von Möbeln in einem unendlichen Array von Layouts enthalten.

![Holograph für Tabelle](images/holograph-on-table-500px.png)

Stellen Sie sich vor, dass ihre Freigabe Umgebungen in eine der folgenden beiden Kategorien passen:
* **Ähnlich**: Umgebungen mit ähnlichen Möbeln, Umgebungslicht und Sound, physischer Raum. Zum Beispiel: Der Professor ist in der Vortragshalle a, und die Schüler/Studenten befinden sich in der Vortragshalle b. in der Vortragshalle a sind möglicherweise weniger Lehrstühle als B enthalten
* **Ungleich**: Umgebungen, die sich in den Einstellungen von Möbeln, Raumgrößen, Licht-und Ton Überlegungen erheblich unterscheiden. Zum Beispiel: Der Professor ist in einem Schwerpunkt Raum, Studenten und Lehrkräfte sind jedoch in einer großen Vortragshalle.

Es ist wichtig, sich über die Umgebung zu Gedanken machen, da Sie sich darauf auswirken wird:
* Wie werden diese Objekte durch Benutzer angezeigt? Zum Beispiel: Wenn Sie für eine Tabelle am besten geeignet sind und der Benutzer über keine Tabelle verfügt? Oder auf einer flachen Oberfläche, aber der Benutzer verfügt über einen Bereich mit Leerzeichen.
* Skalieren der Objekte. Zum Beispiel: Das Platzieren eines 6-Meter-menschlichen Modells in einer Tabelle kann eine Herausforderung darstellen, aber ein Herzmodell würde hervorragend funktionieren.

### <a name="6-what-devices-are-they-using"></a>6. Welche Geräte verwenden Sie?

Heutzutage ist es häufig wahrscheinlich, dass Sie gemeinsame Erfahrungen zwischen zwei **immersiven Geräten** sehen (diese Geräte unterscheiden sich möglicherweise geringfügig von Schaltflächen und relativer Funktionen, aber nicht erheblich) oder zwei **Holographic-Geräte** , die für die Ziel Lösungen konzipiert sind. auf diesen Geräten. Beachten Sie jedoch, dass **2D-Geräte** (ein mobiler/Desktop Teilnehmer oder Beobachter) eine notwendige Überlegung sein werden, insbesondere in Situationen mit **gemischten 2D-und 3D-Geräten**. Das Verständnis der Arten von Geräten, die von ihren Teilnehmern verwendet werden, ist wichtig, nicht nur, weil Sie unterschiedliche Treue-und Daten Einschränkungen und-Möglichkeiten aufweisen, sondern da die Benutzer für jede Plattform besondere Erwartungen haben.

## <a name="exploring-the-potential-of-shared-experiences"></a>Erkunden des Potenzials von freigegebenen Erfahrungen

Antworten auf die obigen Fragen können kombiniert werden, um das freigegebene Szenario besser zu verstehen und die Herausforderungen zu verdeutlichen, wenn Sie die Benutzeroberflächen erweitern. Für das Team bei Microsoft trug dies dazu bei, eine Roadmap für die Verbesserung der heute verwendeten Erfahrungen zu schaffen, das Verständnis der Nuance dieser komplexen Probleme und die Vorteile der gemeinsamen Erfahrungen in gemischter Realität zu nutzen.

Sehen Sie sich beispielsweise eines der Skype-Szenarien aus dem Start von hololens an: ein Benutzer hat sich mit der [Behebung eines unterbrochenen leichten Schalters](https://www.youtube.com/watch?v=iBfzs3G8BEA) mit Hilfe von einem Remote Experten beschäftigt.

![Beheben eines leichten Schalters mit Unterstützung über Skype für hololens](images/fix-a-broken-switch-with-hololens-640px.jpg)

<i>Ein Experte stellt <b>1:1</b> -Anleitungen von seinem <b>2D</b>-Desktop Computer für einen Benutzer eines <b>3D-Geräts mit gemischter Realität</b> bereit. Die <b>Anleitung</b> ist <b>synchron</b> , und die physischen Umgebungen sind unter <b>schiedlich</b>.</i>

Eine solche Vorgehensweise ist eine Schritt-für-Schritt-Änderung unserer aktuellen Darstellung – die Anwendung des Paradigmas von Video und Voice auf ein neues Medium. Wenn wir uns aber die Zukunft ansehen, müssen wir die Gelegenheit unserer Szenarios besser definieren und Erfahrungen mit der Sicherheit der gemischten Realität schaffen.

Sehen Sie sich das [onsight](https://www.youtube.com/watch?v=ZOWQp0-Bkkw) -Zusammenarbeits Tool an, das vom Jet Drive-Labor der NASA Analysten, die an Daten von Mars-Rover-Missionen arbeiten, können in den Daten aus dem Martian-Querformat in Echtzeit mit Kollegen zusammenarbeiten.

![Getrennte Zusammenarbeit zwischen Kollegen, um die Arbeit für den Mars-Rover zu planen](images/onsight-nasa-jpl.gif)

<i>Ein Analyst untersucht eine Umgebung mithilfe eines <b>3D-Geräts mit gemischter Realität</b> und einer <b>kleinen</b> Gruppe von <b>Remote</b> Kollegen, die <b>3D-und 2D</b> -Geräte verwenden. Die <b>Zusammenarbeit</b> ist <b>synchron</b> (kann jedoch asynchron wieder besucht werden), und die physischen Umgebungen sind (virtuell) <b>ähnlich</b>.</i>

Erfahrungen wie onsight bieten neue Möglichkeiten für die Zusammenarbeit. Von physischen verweisen auf Elemente in der virtuellen Umgebung auf die Position neben einem Kollegen und die gemeinsame Nutzung ihrer Perspektive, wenn Sie Ihre Ergebnisse erläutern. Onsight verwendet den Einblick in das Eintauchen und Anwesenheits Verfahren, um die Freigabe von Erfahrungen in gemischter Realität zu überdenken

Die intuitive Zusammenarbeit ist die Grundlage für die Konversation und die Zusammenarbeit und das Verständnis, wie wir diese Intuition auf die Komplexität gemischter Realität anwenden können. Wenn wir nicht nur die gemeinsame Nutzung von Erfahrungen in gemischter Realität neu erstellen können, sondern auch die Nutzung der Arbeit steigern, ist es ein Paradigmenwechsel für die Zukunft der Arbeit. Der Entwurf für freigegebene Umgebungen in gemischter Realität ist neuer und aufregender Bereich – und wir sind nur am Anfang.

## <a name="get-started-sharing-experiences"></a>Einführung in den Einstieg in die Freigabe

Abhängig von Ihrer Anwendung und Ihrem Szenario müssen verschiedene Anforderungen erfüllt sein, damit Sie Ihre gewünschte benutzerfreundliche Anwendung erreichen können. Hierzu zählen u. a.
* Treffer Findung: Möglichkeit zum Erstellen von Sitzungen, ankündigen der Sitzung und ermitteln und einladen bestimmter Personen, sowohl lokal als auch Remote, um der Sitzung beizutreten.
* Anker Freigabe: Die Möglichkeit, Koordinaten auf mehreren Geräten in einem gemeinsamen lokalen Raum auszurichten, sodass holograms für alle Personen am gleichen Ort angezeigt werden.
* Ungs Die Möglichkeit, Positionen, Interaktionen und Bewegungen von Personen und holograms in Echtzeit über alle Teilnehmer hinweg zu synchronisieren.
* Zustands Speicher: Möglichkeit zum Speichern von – Hologramm-Merkmalen und-Speicherorten für die Teilnahme in der Mitte der Sitzung, Rückruf zu einem späteren Zeitpunkt und Stabilität vor Netzwerkproblemen.


Der Schlüssel für die gemeinsame Nutzung besteht darin, dass mehrere Benutzer die gleichen holograms weltweit auf Ihrem eigenen Gerät sehen. Dies geschieht häufig durch Freigeben von Ankern, um Koordinaten Geräte übergreifend auszurichten.
Verwenden Sie zum Freigeben von Ankern die <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">räumlichen Azure-Anker</a>:
* Zuerst platziert der Benutzer das Hologram.
* Die App erstellt einen [räumlichen Anker](coordinate-systems.md) , um dieses Hologramm exakt in der Welt anzuheften.
* Die Anker können über die <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">räumlichen Azure-Anker</a>für hololens-, IOS-und Android-Geräte freigegeben werden. 

Bei einem freigegebenen räumlichen Anker verfügt die APP auf jedem Gerät nun über ein gemeinsames Koordinatensystem, in dem Sie Inhalte platzieren können. Nun kann die APP sicherstellen, dass Sie das – Hologramm am gleichen Speicherort positioniert und orientiert.
Auf hololens-Geräten können Sie auch die Anker von einem Gerät an einen anderen offline freigeben.  Verwenden Sie die folgenden Links, um zu entscheiden, was für Ihre Anwendung am besten geeignet ist.


## <a name="see-also"></a>Siehe auch
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [Gemeinsame Raumanker in DirectX](shared-spatial-anchors-in-directx.md)
* [Gemeinsame Erlebnisse in Unity](shared-experiences-in-unity.md)
* [Spectator View](spectator-view.md)