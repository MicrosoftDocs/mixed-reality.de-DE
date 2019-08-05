---
title: Die Erstellung von Galaxy Explorer für hololens 2
description: Willkommen bei der Vorgehensweise beim Aktualisieren von Galaxy Explorer für hololens 2. Ebenso wie der ursprüngliche Galaxy Explorer ist unser Team offen für das Projekt auf GitHub, um sicherzustellen, dass die Community über Vollzugriff verfügt.
author: l-garrett
ms.author: grbury
ms.date: 06/30/2019
ms.topic: article
keywords: Galaxy Explorer, Fallstudie, Projekt, Beispiel
ms.openlocfilehash: 1e04b27ff0382d87f8e6a15ae2b7b2284fa020e6
ms.sourcegitcommit: be3631932ea1c88ac3ad8b2390c98c5a6e8b93ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2019
ms.locfileid: "68776441"
---
# <a name="the-making-of-galaxy-explorer-for-hololens-2"></a>Die Erstellung von Galaxy Explorer für hololens 2

Willkommen bei der Vorgehensweise beim Aktualisieren von Galaxy Explorer für hololens 2. [Galaxy Explorer] Der (https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer "Galaxy Explorer") wurde ursprünglich als Open-Source-Anwendung für hololens (1. Generation) durch das Teilen Ihres Ideen Programms entwickelt, und ist eine der ersten gemischten Szenarien, in denen viele Personen sich befinden. Nun aktualisieren wir Sie für die [neuen und spannenden Funktionen von hololens 2](https://www.microsoft.com/hololens/hardware).

Als eines der [Mixed Reality-Studio von Microsoft](galaxy-explorer-update.md#mixed-reality-studios)entwickeln wir in der Regel kommerzielle Lösungen und entwickeln & Tests auf Zielplattformen im gesamten Entwicklungs-und Entwicklungsprozess. Wir haben jetzt die einmalige Situation, in der Sie noch keinen Zugriff auf hololens 2-Geräte haben, aber aufgeregt sind, um die Aktualisierungen für den Galaxy Explorer zu starten. Wir arbeiten an diesem Projekt, indem wir die Frameworks und Tools (z. b. [mrtk v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)) nutzen, wenn Sie für uns und die Community verfügbar sind, und wir möchten Sie für die Fahrt zusammenbringen.

Ebenso wie der ursprüngliche Galaxy Explorer ist [unser Team](galaxy-explorer-update.md#meet-the-team) offen für [das Projekt auf GitHub](https://github.com/Microsoft/GalaxyExplorer) , um sicherzustellen, dass die Community über Vollzugriff verfügt. Wir werden unsere Journey hier in der gesamten Transparenz über die Möglichkeiten dokumentieren, mit denen wir die Portierung von mrtk v1 auf mrtk v2 durchgeführt haben. Außerdem wird erläutert, wie wir die Entwicklung basierend auf den neuen Features, die in hololens 2 verfügbar sind, verbessert haben und wie wir sichergestellt haben, dass der Galaxy Explorer eine mehrere Plattformen. Unabhängig davon, ob Sie den Galaxy Explorer auf hololens (1st Gen), hololens 2, ein Windows Mixed Reality-Headset oder auf Ihrem Windows 10-Desktop anzeigen, möchten wir sicherstellen, dass Sie über ein immersives Verhalten verfügen und sich so gut wie möglich mit der Journey beschäftigen!

Diese Seite wird erweitert, während wir das Projekt durchlaufen, und wir verknüpfen Sie mit ausführlicheren Artikeln, Code, Entwurfs Artefakten, zusätzlichen mrtk v2-Dokumentationen usw., um Ihnen einen Insider Einblick in das Projekt zu geben.

## <a name="unveiling-the-new-logo"></a>Entsperren des neuen Logos

Wir freuen uns, mit einer Vorschau des neuen Galaxy Explorer-Logos zu beginnen! Während wir eine Hommage an das ursprüngliche Logo mit der Milch Methode haben, haben wir eine realistische Visualisierung entworfen und die typografievisualisierung aktualisiert, um ein schlankeres und modernes Gefühl zu bieten. Das Logo enthält eine kurze Vorschau auf eines der neuen Symbole.

![Neues Galaxy Explorer-Logo](images/ge-update-app-icon.png)

Der Entwurf und die Typografie des Logos legen den Ton für das allgemeine Aussehen und Verhalten von Benutzeroberflächen Elementen während der gesamten Erfahrung fest. 

## <a name="thinking-about-interactions"></a>Überlegungen zu Interaktionen

Als Creative Studio haben wir die Berechtigung zum Portieren von Galaxy Explorer auf hololens 2 Ecstatic. Wir wussten von Anfang an, dass das neue Gerät ein Feiertag sein soll, und um zu veranschaulichen, dass die Ermächtigung der gemischten Realität nur auf die Phantasie beschränkt ist.

Hololens 2 ermöglicht Benutzern das berühren, verstehen und Verschieben von holograms auf eine Art und Weise, in der Sie sich natürlich fühlen – Sie reagieren sehr ähnlich auf echte Objekte. Vollständig Hand zeitige Modelle sind erstaunlich, da Benutzer die Natur machen können. Beispielsweise wird ein Cup leicht anders ausgewählt – und anstatt eine bestimmte Methode dafür zu erzwingen, können Sie mit hololens 2 das tun.

>[!VIDEO https://www.youtube.com/embed/wogJv5v9x-s]

Dies ist eine große Änderung von den auf der Luft tippen basierenden Schnittstellen auf hololens-Geräten der ersten Generation. Anstatt mit holograms aus einer Entfernung zu interagieren, können Benutzer jetzt "up close and Personal" erhalten. Beim Portieren vorhandener Erfahrungen in hololens 2 oder beim Planen neuer Umgebungen ist es wichtig, sich mit der direkten Bearbeitung von holograms vertraut zu machen.

### <a name="direct-manipulation-vs-the-vast-distances-in-space"></a>Direkte Bearbeitung im Vergleich zu den großen Entfernungen im Raum

Es handelt sich um eine magische Darstellung, die in der Lage ist, eine Welt zu erreichen und Sie zu halten. Die Herausforderung bei diesem Ansatz ist die Größe des Sonnensystems – es ist enorm! Der Benutzer muss seinen Raum durchlaufen, um sich in der Nähe der einzelnen Welt zu befinden, um mit ihm interagieren zu können.

Um Benutzern die Interaktion mit Objekten zu ermöglichen, die weiter entfernt sind, bietet mrtk Hand Eingaben, die aus der Mitte des Benutzers des Benutzers herausgehen und als Erweiterung der Hand fungieren. Ein ringförmiger Cursor wird an das Ende des Strahls angefügt, um anzugeben, wo sich das Strahl mit einem Zielobjekt schneidet. Das Objekt, auf dem der Cursor landet, kann dann gestische Befehle von der Hand empfangen. 

>[!VIDEO https://www.youtube.com/embed/Qol5OFNfN14]

In der ursprünglichen Version von Galaxy Explorer war der Benutzer auf einen Planet mit dem Cursor Cursor ausgerichtet, und dann tippt er darauf, um ihn näher aufzurufen. Die einfachste Möglichkeit zum Portieren des Erlebnisses auf hololens 2 besteht darin, dieses Verhalten zu übernehmen und mithilfe von Hand-Strahlen die Auswahl von Planeten auszuwählen. Obwohl dies funktioniert hat, haben wir mehr übrig.

### <a name="back-to-the-drawing-board"></a>Zurück zur Zeichnungs Platine

Wir kamen zu einer ideentienzusammenfassung, die auf die vorhandenen Interaktionen aufbauen konnte. Der Gedanke war: Obwohl hololens 2 es Benutzern ermöglicht, auf natürliche und realistische Weise mit holograms zu interagieren, sind Hologramme definitionsgemäß nicht Real. Solange eine Interaktion für den Benutzer plausibel ist, spielt es keine Rolle, ob diese Interaktion mit einem echten Objekt möglich wäre – wir können dies möglich machen.

Ein Konzept, das wir untersucht haben, basiert auf telekinesis – die Leistungsfähigkeit, Objekte mit einem Blick zu manipulieren. Eine Person, die häufig in superheldenfilmen angezeigt wird, würde sich mit Ihrem Hinterkopf befassen und ein Objekt in Ihrer geöffneten Hand aufrufen. Wir haben mit der Idee etwas weiter gearbeitet und eine kurze Übersicht darüber gegeben, wie das Konzept funktioniert.

![Konzept für die Interaktion beim Erzwingen von Handles](images/ge-update-interactions-concept-force-grab.png)

Der Benutzer würde das Hand Strahl auf einen Planeten zeigen, der das Ziel Feedback bereitstellen würde. Wenn der Benutzer dann seine geöffneten Hände erweitert, wird der Planet durch eine magische Kraft in den Benutzer gezogen, bis er genug ist, um ihn zu erfassen. Daher ist der Name für die Interaktion: Erzwingen des Erbens. Da der Benutzer den Planeten mit dem geöffneten Hand Zeiger durch die Übertragung bewegen würde, würde er wieder in seinen Umlauf zurückkehren.

### <a name="force-grab-prototyping"></a>Force-Prototypen erzwingen

Anschließend haben wir mehrere Prototypen erstellt, um das Konzept zu testen: Wie wirkt sich die Interaktion insgesamt aus? Soll das aufgerufene Objekt vor dem Benutzer angehalten werden, oder es wird bis zum Ende des Benutzers angehalten? Soll das aufgerufene Objekt während des Aufrufs die Größe oder die Skalierung ändern?

<!--
Here is Amit Rojtblat (Technical Artist) presenting one of the prototypes to Yasushi Zonno (Creative Lead).

------------------------------------------------------------------

__*--- VIDEO OF AMIT PLAYING AND EXPLAINING THE PROTOTYPE ---*__

__*--- NEEDS TO BE UPLOADED (TO YOUTUBE?) AND LINKED ---*__

------------------------------------------------------------------
-->

### <a name="implementing-force-grab-into-the-application"></a>Implementieren von "Erzwingen von Handles" in die Anwendung

Als wir den Erzwingungs Griff auf den Planeten ausprobiert haben, erkannten wir, dass wir die Skalierung des Sonnensystems ändern mussten. Es stellte sich heraus, dass eine exakte, mittelgroße Darstellung des Sonnensystems für Benutzer schwer zu verstehen und zu navigieren war. Sie wussten nicht, wo Sie aussehen sollten. Eine genaue, kleine Darstellung hat jedoch einige der zu kleinen und leicht auszuwählenden Planeten. Daher wurde die Größe der Planeten und der Abstand zwischen den Sonnen Objekten so konzipiert, dass Sie sich innerhalb eines mittelgroßen Raums gut fühlen, während gleichzeitig die relative Genauigkeit gewahrt bleibt.

In den späteren Phasen unseres entwicklungssprints waren wir glücklich genug, dass Sie mit einem internen MSFT Mixed Reality-Experten zusammenarbeiten können, sodass wir Ihre Eingaben als expertentester erhalten und kurze Iterationen für die Force-Interaktion durchgeführt haben.

![Jenny kam beim Testen eines Vorschau Builds von Galaxy Explorer](images/ge-update-user-testing.png)

In Abbildung: Jenny kam, leitender Entwurfs Leiter, Testen einer laufenden Arbeit von Galaxy Explorer.

### <a name="adding-affordances-for-targeting"></a>Hinzufügen von Kosten für das Ziel

Als wir auf hololens 2 experimentieren, stellten wir fest, dass die neuen Interaktionen natürlich und intuitiv sind, aber auch wenn die neuen Interaktionen natürlich und intuitiv sind, bleiben holograms unverändert. Da holograms kein natürliches Feedback bereitstellen, das beim interagieren mit Objekten von Menschen verwendet wird, mussten wir diese erstellen.

Das visuelle und Audiofeedback, das Benutzer für die verschiedenen Phasen Ihrer Interaktionen bereitstellen würden. da der Force-Griff Mechanismus für die Interaktion mit dem Galaxy Explorer von zentraler Bedeutung ist, haben wir viele Iterationen durchgeführt. Ziel war es, das richtige Gleichgewicht zwischen Audiomaterial und visuellem Feedback für jede Phase der Interaktion zu finden: das Augenmerk auf das beabsichtigte Objekt, das Aufrufen des Benutzers und dessen Freigabe. Wir haben gelernt, dass wesentlich mehr Audiomaterial und visuelles Feedback erforderlich waren, um die Interaktion zu verstärken, als wir für hololens (1. Gen) verwendet wurden.

![Visuelle Visualisierungen auf den Planeten](images/ge-update-planet-affordances.png)

### <a name="adding-affordances-for-force-grab"></a>Hinzufügen von Kosten für das Erzwingen von Handles
 
Nachdem wir den grundlegenden Force-Griff-Mechanismus mit Audio-und Visualisierungs Verfahren hatten, haben wir uns mit der Auswahl von "Planets" für die Benutzerfreundlichkeit beschäftigt. Es gab zwei wichtige Punkte zu berücksichtigen: Da es sich bei dem Solar System um eine 3D-Verschiebungs Schnittstelle handelt, ist es für Benutzer komplexer, das konsistente Ziel von Objekten zu erlernen. Dies wurde durch die Tatsache verstärkt, dass das Hand Strahl bei der Auswahl eines Objekts sehr schnell ist, sodass die Planeten unglaublich schnell in den Benutzer verschoben werden.

Wir haben dies mit einer dreistufigen Lösung angegangen. Der erste war recht intuitiv: verlangsamen Sie den Auswahlprozess, sodass die-Planeten den Benutzer auf natürlichere Weise erreichen. Nachdem die Geschwindigkeit angepasst wurde, mussten wir die Audioerstellung und visuelle Visualisierung wiederholen und zusätzliche Audiofeedback hinzufügen, als der für den Benutzer verfolgte Planet.

Der zweite Teil der Lösung bestand darin, dass die Visualisierung der gesamten Interaktion zum Erzwingen von Handles äußerst greifbar ist. Wir haben eine Dicke Linie visualisiert, die zum Zielobjekt bewegt wird, nachdem das Hand Strahl eine Verbindung mit dem Objekt hergestellt hat, und das Objekt dann wieder zum Benutzer hinzu, wie ein Lasso. 

![Visuelles Element "Lasso" für den Force-Griff](images/ge-update-lasso-affordances.png)

Schließlich haben wir die Skalierung des Sonnensystems optimiert, sodass die Planeten groß genug waren, damit der Benutzer den Blick darauf hat. 

Diese drei Verbesserungen ermöglichten es Benutzern, eine genaue Auswahl zu treffen, indem Sie Sie auf intuitive Weise für Sie aufgerufen haben. Insgesamt ist die Auswirkung des letzten Erzwingungs Erbens eine immersive und interaktive Darstellung des Sonnensystems.

## <a name="spotlight-on-jupiter"></a>Spotlight auf Jupiter

Das Erstellen der Sonnen Körper der Milchqualität war eine humbelte Methode. Insbesondere die eindeutigen Merkmale von Jupiter machen es zu einem Blick. Es ist das größte und farbige der Gasriesen und enthält mehr Massen als alle anderen miteinander zusammengesetzten. Seine schiere Größe und die mesmerierenden Bänder von Turbulenzen und clouddynamics sind ein Präfekt für besondere künstlerische Aufmerksamkeit.

### <a name="geometry-and-meshes"></a>Geometrie und Netzen

Als Gasriese bestehen die äußeren Shells von Jupiter aus Gasschichten. Die Kombination aus der schnellen Rotationsgeschwindigkeit, dem inneren Wärmeaustausch und den Coriolis-Kräften erstellt Farben und streamt diese Form in das Vertauschen von cloudgürteln und-Vorschauen. Die Erfassung dieser komplexen Schönheit war der Schlüssel beim Erstellen des Sonnensystems.

Es war sofort klar, dass die Verwendung von Techniken wie fließenden Simulationen und animierten Texturen mit vorab berechneten Streams nicht mehr infrage kam. Die Rechenleistung, die erforderlich ist, um dies in Kombination mit allen anderen Ereignissen zu simulieren, hätte sich erheblich nachteilig auf die Leistung ausgewirkt. 

![Übersicht über das Jupiter-Objekt](images/ge-update-jupiter-shells-complete.jpg)

Der nächste Ansatz war eine "Rauch-und Spiegelungs Lösung", die aus transparenten Textur Ebenen besteht, die jeweils einen bestimmten Aspekt der atmosphärischen Bewegung aufwiesen, der bei einer Komposition rotierender Gitter Netze kompiliert wurde.

In der folgenden Abbildung sehen Sie die innere Shell auf der linken Seite. Diese Matt-Schicht hat einen Hintergrund für die Komposition bereitgestellt, um vor kleinen Lücken zwischen den verschiedenen Ebenen zu schützen, die die Clouds umfassen. Aufgrund der langsamen Drehung der Schicht diente sie auch als visueller Puffer zwischen den schnelleren Verschiebungs Bändern, um visuelle Unity in den Ebenen zu entwickeln.

Nachdem Sie diesen Anker auf das Modell festgelegt haben, wurden die verschiebenden cloudschichten in den unten gezeigten mittleren und rechten Netzen projiziert.

![Übersicht über das Jupiter-Objekt mit getrennten Shells](images/ge-update-jupiter-shells-separated.jpg)

### <a name="texturing"></a>Texturierung

Die vorhandene Textur wurde in einen dreiteiligen Textur Atlas aufgeteilt: Das obere dritte hostet eine muteless-Ebene mit Lücken und Lücken, um einen Parameter in der Mitte zu liefern, der mittlere Abschnitt enthält die schnellen verschiebbaren Datenströme, und das untere dritte-Element enthält eine langsam drehenden inneren Basisschicht.

Der hervorragend hervorragend rote Spot wurde auch in seine verschiedenen verschiebbaren Teile aufgeteilt und dann in einen ansonsten unsichtbaren Bereich der Textur eingefügt. Diese Komponenten können als rot-tontöne im mittleren Abschnitt der Abbildung unten angezeigt werden.

Da jedes Band eine bestimmte Richtung und eine bestimmte Geschwindigkeit hat, wurde die Textur einzeln auf jedes Mesh angewendet. Die Netzen hatten dann einen gemeinsamen Mittelpunkt und Pivotpunkt, um die gesamte Oberfläche konzentrisch animieren zu können.

![Übersicht über die Jupiter-Texturen](images/ge-update-jupiter-planet-cloud-texture.png)

### <a name="rotation-and-texture-behavior"></a>Drehung und Textur Verhalten

Nachdem Sie die visuelle Komposition von Jupiter festgelegt haben, mussten wir sicherstellen, dass die Dreh-und die Umlaufgeschwindigkeit ordnungsgemäß berechnet und entsprechend angewendet wurden. Es dauert ungefähr 9 Stunden, bis Jupiter eine vollständige Rotation durchführt. Dies ist eine Frage der Definition aufgrund der differenziellen Rotation. Daher wurde der Äquatorial Datenstrom als "Master Datenstrom" festgelegt, wobei 3600 Frames für eine vollständige Drehung übernommen wurden. Jede andere Ebene muss eine Rotationsgeschwindigkeit als Faktor von 3600 aufweisen, damit Sie mit der ursprünglichen Position abgeglichen werden kann, z. b. 600, 900, 1200, 1800 usw.

![Jupiter shelltexturen](images/ge-update-shell-texture.jpg)


### <a name="the-great-red-spot"></a>Der große rote Punkt

Die einzeln rotierenden Streams stellten einen guten visuellen Eindruck dar, fehlten jedoch im Detail, wenn Sie im Bereich "Schließen" beobachtet wurden.

Der wichtigste Teil des Augen Abfangens war der große rote Fleck von Jupiter. Daher haben wir eine Reihe von Netzen und Texturen erstellt, um Sie vorzustellen.
 
Wir haben einen ähnlichen Mechanismus wie bei den Bändern von Jupiter verwendet: ein Satz rotierender Teile wurde aufeinander zusammengesetzt und auch unter seiner "Master Schicht" gruppiert, um sicherzustellen, dass Sie in der Position bleiben, unabhängig davon, wie schnell der Rest verschoben wird.

Wenn die Netzen eingerichtet und eingerichtet wurden, wurden unterschiedliche Ebenen des stürmischen Wirbel angewendet, und jede CD wurde dann einzeln animiert, die Mittel stellen sich am schnellsten, und der Rest verlangsamt sich nach außen.

![Jupiter großes rotes-Spot-Mesh](images/ge-update-great-red-spot-mesh.jpg)

Die Komposition besaß auch denselben Pivot wie jedes andere Mesh, während gleichzeitig die Neigung von der ursprünglichen y-Achse (!) beibehalten wurde, um die Animation der Rotation zu ermöglichen. 3600 Frames ist die Basisrate, wobei jede Ebene den Faktor this als Dreh Zeitraum hat.

![Jupiter große rote-Spot-Textur](images/ge-update-red-spot-mesh-texture.jpg)

### <a name="getting-it-right-in-unity"></a>Direkt in Unity

Bei der Implementierung dieses Features in Unity müssen einige wichtige Punkte berücksichtigt werden.

Unity ist leicht verwirrend, wenn Sie große Mengen von transparenten Ebenen verarbeiten. Die Lösung bestand darin, das Textur Material für jedes Mesh zu duplizieren und die aufsteigenden renderwarteschlangen-Werte progressiv von der inneren auf die äußere um 5 für jedes Material anzuwenden.

Das Ergebnis war, dass die innere Shell einen Rendering-Warteschlangen Wert von 3000 (Standard) enthielt, die statische rote-Tonfarbe später den Wert 3005, die schnellen weißen äußeren Clouds 3010. Der große rote Fleck (Fortschritt von der inneren zur äußeren Ebene) ist mit einem Wert von 3025 in diesem Modell fertig.

![Letztes Jupiter-Objekt](images/ge-update-jupiter-final.jpg)

### <a name="final-touches"></a>Abschließende Berührungen

Die texturierten Jupiter Schichten wurden zuerst eingerichtet, was für die Implementierung nicht ausreichend erwies.

Der ursprüngliche Planet Standard-Shader (und alle zugehörigen Variationen) empfangen seine Beleuchtungs Informationen über ein Skript, den sunlightreceiver, der vom mrtk-Standard-Shader nicht unterstützt wird.

Das einfache austauschen der Shader war keine Lösung, da der Planet Standard-Shader keine Textur Zuordnungen mit Transparenz unterstützt. Wir haben diesen Shader bearbeitet, damit der Jupiter-Build wie beabsichtigt funktioniert.

Zum Schluss müssen die Alpha-Mischungs Einstellungen eingerichtet werden, indem die Quelle Blend auf 10 festgelegt wird, und die Ziel Mischung auf 5.

![Jupiter Unity-Eigenschaften](images/ge-update-jupiter-unity-render-queue.jpg)

Sie können das endgültige Rendering von Jupiter in Galaxy Explorer sehen!

## <a name="meet-the-team"></a>Team Treffen 

Unser Mixed Reality Studio-Team besteht aus Designern, 3D-Künstlern, UX-Spezialisten, Entwicklern, einem Programmmanager und einem Studio-Head. Wir kommen weltweit vor: Belgien, Kanada, Deutschland, Israel, Japan, das Vereinigte Königreich und die USA. Wir sind ein multidisziplinäres Team, das aus einem vielfältigen Hintergrund stammt: Spiele, sowohl herkömmliches als auch Indie, digitales Marketing, Gesundheitswesen und Wissenschaft.

Wir freuen uns, den Galaxy Explorer für hololens 2 zu erstellen und die hololens (1st Gen)-, VR-und Desktop Versionen zu aktualisieren. 

![Das Galaxy Explorer-Team](images/ge-update-team-image.png)

Oben von links nach rechts: Artemis tsouflidou (Developer), Angie teickner (visueller Designer), David Janer (UX-Designer), Laura Garrett (Delivery &-Produktionsleiter), yashihi zonno (Creative Lead), Eline Ledent (Developer) und Ben Turner (SR. Developer).
Unten von links nach rechts: Amit rojtblat (Technical Artist), Martin Wettig (3D-Künstlerin) und Dirk songuer (Studio Head).
Nicht angezeigt: Tim Gerken (Tech Lead) und "Oscar salandin" (visueller Designer).

## <a name="additional-information"></a>Weitere Informationen

### <a name="mixed-reality-studios"></a>Mixed Reality-Studios

Microsoft Mixed Reality Studio-Teams, die sich in Nordamerika, Europa und Asien-Pazifik befinden, sind Experten für das Design der Benutzer Darstellung, Holographic Computing, AR/VR-Technologien und 3D-Entwicklung. einschließlich der Erstellung von 3D-Assets, DirectX, Unity und Unreal. Wir helfen Ihnen bei der Entwicklung gewünschter Futures, beim Entwerfen, erstellen und Bereitstellen von Lösungen, während Kunden gleichzeitig messbare Auswirkungen auf Ihre Organisation erzielen können. Die Ateliers arbeiten eng mit mehr als 22.000 Microsoft-Diensts für die Integration von Unternehmensanwendungen, die Übernahme, den Betrieb und Support.
