---
title: Gemeinsam genutzte Umgebungen in gemischter Realität
description: Holographic Apps können räumliche Anker von einem hololens zu einem anderen Teilen, sodass Benutzer ein Hologramm an derselben Stelle in der realen Welt auf mehreren Geräten darstellen können.
author: thetuvix
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: gemeinsam genutzte Benutzeroberflächen, gemischte Realität, Hologram, räumlicher Anker, mehrere Benutzer, mehrere
ms.openlocfilehash: 4e71bdefa32d2f6cf3b85b074c3d9fcbdb6aa909
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437471"
---
# <a name="shared-experiences-in-mixed-reality"></a>Gemeinsam genutzte Umgebungen in gemischter Realität

Holograms müssen nicht nur für einen Benutzer privat bleiben. Holographic Apps können [räumliche Anker](spatial-anchors.md) von einem hololens-, IOS-oder Android-Gerät zu einem anderen gemeinsam nutzen, sodass Benutzer ein Hologramm an derselben Stelle in der realen Welt über mehrere Geräte hinweg Rendering können.

## <a name="six-questions-to-define-shared-scenarios"></a>Sechs Fragen zum Definieren von freigegebenen Szenarien

Bevor Sie mit dem Entwerfen für freigegebene Umgebungen beginnen, ist es wichtig, die Ziel Szenarien zu definieren. In diesen Szenarien wird erläutert, was Sie entwerfen und ein gängiges Vokabular einrichten, mit dem Sie die für Ihre Benutzer Arbeit erforderlichen Features vergleichen und vergleichen können. Wenn Sie das grundlegende Problem und die verschiedenen Lösungsmöglichkeiten verstehen, ist es entscheidend, die Verkaufschancen dieses neuen Mediums zu decken.

Mithilfe interner Prototypen und Explorationen von unseren hololens-Partnerbehörden haben wir sechs Fragen erstellt, um Ihnen beim Definieren von freigegebenen Szenarien zu helfen. Diese Fragen bilden ein Framework, das nicht vollständig ist, um die wichtigen Attribute Ihrer Szenarios zu unterstützen.

### <a name="1-how-are-they-sharing"></a>1. wie werden Sie gemeinsam genutzt?

Eine Präsentation kann von einem einzelnen virtuellen Benutzer geleitet werden, während mehrere Benutzer zusammenarbeiten können, oder ein Lehrer stellt Anleitungen für virtuelle Schüler und Studenten bereit, die mit virtuellen Materialien arbeiten – die Komplexität der Erfahrungen erhöht sich basierend auf der Ebene der Behörde, die ein Benutzer hat oder kann in einem Szenario vorhanden sein.

![Man und Women mit Holograph für die Tabelle](images/man-and-women-with-holograph-on-table-500px.png)

Es gibt viele Möglichkeiten für die Freigabe, aber wir haben festgestellt, dass die meisten in drei Kategorien unterteilt sind:

* **Präsentation**: Wenn der gleiche Inhalt mehreren Benutzern angezeigt wird. Beispiel: ein Professor gibt eine Präsentation an mehrere Studenten aus, die das gleiche Holographic-Material bereitstellt, das für jeden Benutzer bereitgestellt wird. Der Professor könnte jedoch seine eigenen Hinweise und Notizen enthalten, die für andere Personen möglicherweise nicht sichtbar sind.
* **Zusammenarbeit**: Wenn Mitarbeiter zusammenarbeiten, um einige gängige Ziele zu erreichen. Beispiel: der Professor hat ein Projekt gegeben, um mehr über die Durchführung einer Herzoperation zu erfahren. Schüler/Studenten koppeln und erstellen eine freigegebene Skills Lab-Umgebung, mit der medizinische Studenten am Kernmodell arbeiten und lernen können.
* **Leitfaden**: Wenn eine Person eine Person unterstützt, um ein Problem in einer mehrstufigen Interaktion zu lösen. Dies ist beispielsweise der Fall, wenn der Professor eine Anleitung für einen Schüler/Student bietet, wenn er das Herzstück der Übung in der gemeinsam genutzten Umgebung ausführt.

### <a name="2-what-is-the-group-size"></a>2. wie lautet die Gruppengröße?

Die **einmalige** Nutzung bietet eine starke Baseline, und im Idealfall kann Ihr Konzept auf dieser Ebene erstellt werden. Beachten Sie aber, dass die Freigabe mit großen Gruppen (über 6 Personen) sowohl technische (Daten-als auch Netzwerk-) als auch soziale Probleme (die Auswirkungen der Verwendung eines Raums mit [mehreren Avataren](https://vimeo.com/160704056)) nach sich ziehen kann. Die Komplexität steigt exponentiell, wenn Sie zwischen **kleinen** und **großen Gruppen**wechseln.

Wir haben festgestellt, dass die Anforderungen von Gruppen in drei Größen Kategorien fallen können:
* 1:1
* Small < 7
* Große > = 7

Die Gruppengröße stellt eine wichtige Frage dar, da sich dies auf Folgendes auswirkt:

* Darstellungen von Menschen in Holographic Space
* Skalieren von Objekten
* Skalieren der Umgebung

### <a name="3-where-is-everyone"></a>3. wo ist jeder?

Die Stärke der gemischten Realität kommt ins Spiel, wenn eine gemeinsame Nutzung am gleichen Ort stattfinden kann. Wir nennen das **zusammen**gestellte. Wenn die Gruppe dagegen verteilt ist und sich mindestens ein Teilnehmer nicht im selben physischen Raum befindet (was häufig bei VR der Fall ist), wird ein **Remote**Vorgang aufgerufen. Häufig ist es der Fall, dass Ihre Gruppe **sowohl** zusammengestellte als auch Remote Teilnehmer (z. b. zwei Gruppen in Konferenzräumen) umfasst.

![Drei Personen mit Holograph für die Tabelle](images/three-people-with-holograph-on-table-500px.png)

Die folgenden Kategorien helfen Ihnen, den Speicherort der Benutzer zu vermitteln:

* **Zusammen**gestellt: alle Ihre Benutzer befinden sich im selben physischen Bereich.
* **Remote**: alle Ihre Benutzer befinden sich in separaten physischen Räumen.
* **Beides**: bei ihren Benutzern handelt es sich um eine Mischung aus zusammengestellten und Remote Plätzen.

Diese Frage ist wichtig, da Sie sich auf Folgendes auswirkt:

* Wie werden Personen miteinander kommunizieren?
    * Beispiel: ob Sie über Avatare verfügen sollen?
* Welche Objekte werden angezeigt? Werden alle Objekte freigegeben?
* Ob wir uns an die Umgebung anpassen müssen?

### <a name="4-when-are-they-sharing"></a>4. Wann werden Sie gemeinsam genutzt?

Wir denken in der Regel an **synchrone** Oberflächen, wenn gemeinsame Erfahrungen zu beachten sind. Wenn wir jedoch ein einzelnes virtuelles Element einschließen, das von einer anderen Person hinzugefügt wurde, haben wir ein **asynchrones** Szenario. Stellen Sie sich einen Hinweis oder ein sprach Memo in einer virtuellen Umgebung vor. Wie behandeln Sie 100 Virtual Sprachnotizen im Entwurf? Was geschieht, wenn Sie von Dutzenden von Menschen mit unterschiedlichen Datenschutz Ebenen abweichen?

Sehen Sie sich Ihre Erfahrungen als eine dieser Zeitkategorien an:

* **Synchron**: gleich zeigend, die holografische Darstellung gemeinsam zu nutzen. Beispiel: zwei Schüler und Studenten, die das Skills Lab gleichzeitig durchführen.
* **Asynchron**: Freigeben der Holographic-Darstellung zu unterschiedlichen Zeitpunkten. Beispiel: zwei Schüler/Studenten, die das Skills-Lab ausführen, aber zu unterschiedlichen Zeiten an separaten Abschnitten arbeiten.
* **Beides**: Ihre Benutzer werden manchmal synchron und in anderen Fällen asynchron freigegeben. Beispiel: ein Professor stuft die Zuweisung ein, die von den Schülern zu einem späteren Zeitpunkt durchgeführt wird, und gibt für die Schüler/Studenten am nächsten Tag Notizen aus.

Diese Frage ist wichtig, da Sie sich auf Folgendes auswirkt:

* Objekt-und Umgebungs Persistenz. Beispiel: Speichern der Zustände, damit Sie abgerufen werden können.
* Benutzer Perspektive. Dies ist beispielsweise der Fall, wenn Sie wissen, was der Benutzer beim hinterlassen von Notizen betrachtet hat.

### <a name="5-how-similar-are-their-physical-environments"></a>5. wie ähnlich ist die physische Umgebung?

Die Wahrscheinlichkeit, dass zwei identische reale Umgebungen außerhalb der zusammengestellten Erfahrung vorhanden sind, ist schlank, es sei denn, diese Umgebungen sind so konzipiert, dass Sie identisch sind. Es ist wahrscheinlicher, dass Sie **ähnliche** Umgebungen haben. Beispielsweise sind Konferenzräume ähnlich – Sie haben in der Regel eine zentral lokalisierte Tabelle, die von den Lehrstühlen umgeben ist. Wohn Räume sind dagegen normalerweise unter **schiedlich** und können eine beliebige Anzahl von Möbeln in einem unendlichen Array von Layouts enthalten.

![Holograph für Tabelle](images/holograph-on-table-500px.png)

Stellen Sie sich vor, dass ihre Freigabe Umgebungen in eine der folgenden beiden Kategorien passen:

* **Ähnlich**: Umgebungen mit ähnlichen Möbeln, Umgebungslicht und Sound, physischer Raum. Beispiel: Professor befindet sich in der Vortragshalle a, und die Schüler/Studenten befinden sich in der Vortragshalle b. in der Vortragshalle a sind möglicherweise weniger Lehrstühle als B enthalten
* Unter **schiede**: Umgebungen, die sich in den Einstellungen für die Möbel, die Raumgrößen, helle und Ton Überlegungen erheblich unterscheiden. Beispiel: ein Professor befindet sich in einem Schwerpunkt Raum, Studenten und Lehrkräfte in einer großen Vortragshalle.

Es ist wichtig, sich [über die Umgebung Gedanken zu machen](environment-considerations-for-hololens.md), da Sie Folgendes beeinflussen wird:

* Art und Weise, wie Benutzer diese Objekte erleben werden. Beispiel: Wenn Ihre Benutzerfunktion am besten in einer Tabelle funktioniert und der Benutzer keine Tabelle hat? Oder auf einer flachen Oberfläche, aber der Benutzer verfügt über einen Bereich mit Leerzeichen.
* Skalieren der Objekte. Beispiel: das Platzieren eines 6-Meter-menschlichen Modells in einer Tabelle kann eine Herausforderung darstellen, aber ein Herzmodell würde hervorragend funktionieren.

### <a name="6-what-devices-are-they-using"></a>6. welche Geräte verwenden Sie?

Heutzutage ist es häufig wahrscheinlich, dass Sie gemeinsame Erfahrungen zwischen zwei [**immersiven Geräten**](immersive-headset-hardware-details.md) sehen (diese Geräte unterscheiden sich möglicherweise geringfügig von Schaltflächen und relativer Funktionen, aber nicht erheblich) oder zwei **Holographic-Geräte** , die für die Ziel Lösungen konzipiert sind. auf diesen Geräten. Berücksichtigen Sie jedoch, ob **2D-Geräte** (ein mobiler/Desktop Teilnehmer oder Beobachter) eine notwendige Überlegung sein werden, insbesondere in Situationen mit **gemischten 2D-und 3D-Geräten**. Das Verständnis der Arten von Geräten, die von ihren Teilnehmern verwendet werden, ist wichtig, nicht nur, weil Sie unterschiedliche Treue-und Daten Einschränkungen und-Möglichkeiten aufweisen, sondern da die Benutzer für jede Plattform besondere Erwartungen haben.

## <a name="exploring-the-potential-of-shared-experiences"></a>Erkunden des Potenzials von freigegebenen Erfahrungen

Antworten auf die obigen Fragen können kombiniert werden, um das freigegebene Szenario besser zu verstehen und die Herausforderungen zu verdeutlichen, wenn Sie die Benutzeroberflächen erweitern. Für das Team bei Microsoft trug dies dazu bei, eine Roadmap für die Verbesserung der heute verwendeten Erfahrungen zu schaffen, das Verständnis der Nuance dieser komplexen Probleme und die Vorteile der gemeinsamen Erfahrungen in gemischter Realität zu nutzen.

Sehen Sie sich beispielsweise eines der Skype-Szenarien aus dem Start von hololens an: ein Benutzer hat sich mit der [Behebung eines unterbrochenen leichten Schalters](https://www.youtube.com/watch?v=iBfzs3G8BEA) mit Hilfe von einem Remote Experten beschäftigt.

![Beheben eines leichten Schalters mit Unterstützung über Skype für hololens](images/fix-a-broken-switch-with-hololens-640px.jpg)

*Ein Experte stellt **1:1** -Anleitungen von seinem **2D**-Desktop Computer für einen Benutzer eines **3D-Geräts mit gemischter Realität** bereit. Die **Anleitung** ist **synchron** , und die physischen Umgebungen sind unter **schiedlich**.*

Eine solche Vorgehensweise ist eine Schritt-für-Schritt-Änderung unserer aktuellen Darstellung – die Anwendung des Paradigmas von Video und Voice auf ein neues Medium. Wenn wir uns aber die Zukunft ansehen, müssen wir die Gelegenheit unserer Szenarios besser definieren und Erfahrungen mit der Sicherheit der gemischten Realität schaffen.

Sehen Sie sich das [onsight](https://www.youtube.com/watch?v=XtUyUJAVQ6w)-Zusammenarbeits Tool an, das vom Jet Drive-Labor der NASA entwickelt wurde Analysten, die an Daten von Mars-Rover-Missionen arbeiten, können in den Daten aus dem Martian-Querformat in Echtzeit mit Kollegen zusammenarbeiten.

![Getrennte Zusammenarbeit zwischen Kollegen, um die Arbeit für den Mars-Rover zu planen](images/onsight-nasa-jpl.gif)

*Ein Analyst untersucht eine Umgebung mithilfe eines **3D-Geräts mit gemischter Realität** und einer **kleinen** Gruppe von **Remote** Kollegen, die **3D-und 2D** -Geräte verwenden. Die **Zusammenarbeit** ist **synchron** (kann jedoch asynchron wieder besucht werden), und die physischen Umgebungen sind (virtuell) **ähnlich**.*

Erfahrungen wie onsight bieten neue Möglichkeiten für die Zusammenarbeit. Von physischen verweisen auf Elemente in der virtuellen Umgebung auf die Position neben einem Kollegen und die gemeinsame Nutzung ihrer Perspektive, wenn Sie Ihre Ergebnisse erläutern. Onsight verwendet den Einblick in das Eintauchen und Anwesenheits Verfahren, um die Freigabe von Erfahrungen in gemischter Realität zu überdenken

Die intuitive Zusammenarbeit ist die Grundlage für die Konversation, zusammenarbeiten und verstehen, wie wir diese Intuition auf die Komplexität gemischter Realität anwenden können. Wenn wir nicht nur die gemeinsame Nutzung von Erfahrungen in gemischter Realität neu erstellen können, sondern auch die Nutzung der Arbeit steigern, ist es ein Paradigmenwechsel für die Zukunft der Arbeit. Der Entwurf für freigegebene Umgebungen in gemischter Realität ist neuer und aufregender Bereich – und wir sind nur am Anfang.

## <a name="get-started-building-shared-experiences"></a>Beginnen Sie mit dem Aufbau gemeinsamer Erfahrungen

Abhängig von Ihrer Anwendung und Ihrem Szenario müssen verschiedene Anforderungen erfüllt sein, damit Sie Ihre gewünschte benutzerfreundliche Anwendung erreichen können. Hierzu gehören:

* **Übereinstimmungs Findung: die**Möglichkeit zum Erstellen von Sitzungen, ankündigen von Sitzungen, ermitteln und einladen bestimmter Personen sowohl lokal als auch Remote für die Teilnahme an der Sitzung.
* **Anker Freigabe**: die Möglichkeit, Koordinaten auf mehreren Geräten in einem gemeinsamen lokalen Raum auszurichten, sodass holograms für alle Personen am gleichen Ort angezeigt werden.
* **Netzwerk**: die Möglichkeit, Positionen, Interaktionen und Bewegungen von Personen und holograms in Echtzeit über alle Teilnehmer hinweg zu synchronisieren.
* **Zustands Speicher**: Möglichkeit zum Speichern von – Hologramm-Merkmalen und-Speicherorten für die Mitte der Sitzung, Rückruf zu einem späteren Zeitpunkt und Stabilität vor Netzwerkproblemen.

Der Schlüssel für die gemeinsame Nutzung besteht darin, dass mehrere Benutzer die gleichen holograms auf der ganzen Welt auf Ihrem eigenen Gerät sehen. Dies geschieht häufig durch Freigeben von Ankern, um Koordinaten Geräte übergreifend auszurichten.

Verwenden Sie zum Freigeben von Ankern die [räumlichen Azure-Anker](https://docs.microsoft.com/azure/spatial-anchors):

* Zuerst platziert der Benutzer das Hologram.
* Die App erstellt einen [räumlichen Anker](spatial-anchors.md), um dieses Hologramm exakt in der Welt anzuheften.
* Die Anker können über [Azure Spatial](https://docs.microsoft.com/azure/spatial-anchors/)Anchor für hololens-, IOS-und Android-Geräte freigegeben werden.

Bei einem freigegebenen räumlichen Anker verfügt die APP auf jedem Gerät nun über ein [gemeinsames Koordinatensystem](coordinate-systems.md) , in dem Sie Inhalte platzieren können. Nun kann die APP sicherstellen, dass Sie das – Hologramm am gleichen Speicherort positioniert und orientiert.

Auf hololens-Geräten können Sie auch die Anker von einem Gerät an einen anderen offline freigeben.  Verwenden Sie die folgenden Links, um zu entscheiden, was für Ihre Anwendung am besten geeignet ist.

## <a name="evaluating-tech-options"></a>Auswerten von Tech-Optionen

Es stehen verschiedene Dienst-und Technologieoptionen zur Verfügung, mit denen Sie gemischte Umgebungen mit mehreren Benutzern entwickeln können.  Es kann schwierig sein, einen Pfad auszuwählen. Wenn Sie also eine szenariobezogene Perspektive treffen möchten, sind einige Optionen unten aufgeführt.

## <a name="shared-static-holograms-no-interactions"></a>Freigegebene statische Hologramme (keine Interaktionen)

Nutzen Sie [räumliche Azure-Anker](https://docs.microsoft.com/azure/spatial-anchors/) in Ihrer APP.  Wenn Sie räumliche Anker Geräte übergreifend aktivieren und freigeben, können Sie eine Anwendung erstellen, bei der die Benutzer holograms gleichzeitig am gleichen Ort sehen.  Zusätzliche Synchronisierung über Geräte hinweg ist erforderlich, damit Benutzer mit holograms interagieren und Bewegungen oder Zustands Aktualisierungen von holograms anzeigen können.

## <a name="share-1st-person-perspective"></a>Freigeben von 1. Person-Perspektive

Nutzen Sie integrierte miracast-Unterstützung für lokale Benutzer, wenn Sie über einen unterstützten miracast-Empfänger verfügen, z. b. einen PC oder ein Fernsehgerät – es ist kein zusätzlicher app-Code erforderlich.

Nutzen Sie [mixedreality-webrtc](https://github.com/microsoft/mixedreality-webrtc) in Ihrer APP für Remote Benutzer, oder wenn Sie über nicht-miracast-Geräte verfügen, für die Sie freigeben möchten.  Wenn Sie eine webrtc-Verbindung aktivieren, werden 1:1-Audiodaten und-Videostreams zwischen Benutzern mit einem Datenkanal für Geräte übergreifende Messaging Funktionen ermöglicht.  Die Implementierung gemischter Realität optimiert für hololens durch die Bereitstellung eines Videodaten Stroms für die gemischte Realität Erfassung der Ansicht des hololens-Benutzers für andere.  Wenn Sie Video Streaming auf mehrere Remote Clients zentral hochskalieren möchten, wird in der Regel ein [MCU-Dienstanbieter](https://webrtcglossary.com/mcu/) (Multipoint-Konferenz Einheit) verwendet, z. b. [signalwire](https://signalwire.com/).  Eine One-Click-signalwire-Bereitstellung in Azure ist über [FreeSWITCH](https://github.com/andywolk/azure-freeswitch-gpu-windows)verfügbar.

> [!NOTE]
> Beachten Sie, dass es sich bei signalwire um einen kostenpflichtigen Dienst handelt, der nicht im Besitz von Microsoft ist.

## <a name="presenter-spectator-applications-and-demos"></a>Presenter-Betrachter-Anwendungen und-Demos

Nutzen Sie [mixedreality-zuschauorview](https://github.com/microsoft/MixedReality-SpectatorView) , um die [Funktionen der specator-Ansicht](spectator-view.md) in Ihre APP zu bringen.  Aktivieren Sie andere Geräte (HL, Android, IOS und Videokameras), um zu sehen, was die hololens aus einer anderen Perspektive am gleichen Speicherort sehen, und erhalten Sie Aktualisierungen bei Interaktionen des Hosts, von dem die Benutzer mit den holograms interagieren.  Sehen Sie sich an, zeichnen Sie Bilder auf, und zeichnen Sie Videos aus, die der Host mit den holograms in der Anwendung aus ihrer eigenen räumlichen Perspektive mit dem Betrachter der gleichen App verwendet.

**Hinweis:** Bilder werden über einen Screenshot auf IOS-/Android-Geräten erstellt.

## <a name="multi-user-collaborative-experience"></a>Zusammenarbeits Umgebung für mehrere Benutzer

Beginnen Sie mit unserem Tutorial zum Lernprogramm für [mehrere Benutzer](mrlearning-sharing(photon)-ch1.md), das [räumliche Azure-Anker](https://docs.microsoft.com/azure/spatial-anchors/) für lokale Benutzer und das [Photon SDK](https://www.photonengine.com/PUN) zum Synchronisieren des Inhalts/Zustands in der Szene nutzt. Erstellen Sie lokal kollaborative Anwendungen, in denen jeder Benutzer seine eigene Perspektive auf den holograms in der Szene hat und jede vollständige Interaktion mit den holograms durchführen kann.  Updates werden auf allen Geräten bereitgestellt, und die Interaktions Konflikt Verwaltung wird von Photon behandelt.

> [!NOTE]
> Beachten Sie, dass es sich bei " [Photon](https://www.photonengine.com/) " nicht um ein Microsoft-Produkt handelt, sodass eine abrechnungsbeziehung mit "Photon" erforderlich ist, um eine höhere Auslastung zu produzieren und zu skalieren.

## <a name="future-work"></a>Die Zukunft

Komponenten Funktionen und-Schnittstellen helfen bei der Bereitstellung allgemeiner Konsistenz und stabiler Unterstützung in den verschiedenen Szenarien und zugrunde liegenden Technologien.  Wählen Sie bis dahin den besten Weg aus, der dem Szenario entspricht, das Sie in Ihrer Anwendung erreichen möchten.

Anderes Szenario oder möchten Sie eine andere Technik/einen anderen Dienst verwenden? Geben Sie Feedback als GitHub-Probleme im entsprechenden Repository unten auf dieser Seite an, oder wenden Sie sich an [holodevelopers Slack](https://holodevelopers.slack.com/).

## <a name="see-also"></a>Weitere Informationen:

* [Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors)
* [Gemeinsame Raumanker in DirectX](shared-spatial-anchors-in-directx.md)
* [Gemeinsame Erlebnisse in Unity](shared-experiences-in-unity.md)
* [Spectator View](spectator-view.md)
