---
title: Informationen zu diesem Leitfaden zum design
description: Dieser Leitfaden wurde von Microsoft-Designern, -Entwicklern, -Programmmanagern und -Forschern verfasst, deren Arbeit holografische Geräte (wie HoloLens) und immersive Geräte (wie die Windows Mixed Reality-Headsets von Acer und HP) umfasst.
author: MRWied
ms.author: jonwie
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, entwerfen, Einführung, Anleitungen
ms.openlocfilehash: 6173f7cd2bcc4280f86f8f5ecaae1e90e01b62a0
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326126"
---
# <a name="about-this-design-guidance"></a>Informationen zu diesem Leitfaden zum design

## <a name="introduction"></a>Einführung

**Hallo und Willkommen bei Ihrem Entwurfsrichtlinien für mixed Reality.**

Dieser Leitfaden verfasst wurde es von Microsoft-Designer, Entwickler, Programm-Managern und Forscher, deren Arbeit holographic-Geräten wie HoloLens und immersive Geräten, z. B. Acer und HP Windows Mixed Reality-Headsets umfasst. Berücksichtigen Sie diese Arbeit als eine Reihe von Themen zur Verwendung von für Windows-Head eingebundenen zeigt zu entwerfen.

Mit Ihnen werden wir eine äußerst interessante neue Ära der Datenverarbeitung eingeben. Bahnbrechende zeigt Head eingebaut, räumliche Sound, Sensoren, Umweltbewusstseins, Eingabe-und 3D-Grafiken führen wir ein, und fordern uns, neue Typen von Benutzeroberflächen – eine neue Grenze, die erheblich mehr personal, intuitive, immersive und kontextbezogene definieren.

Wo immer dies möglich ist, bieten wir umsetzbare Entwurfsrichtlinien mit zugehörigem Code auf GitHub. Also, da es rechts neben Sie beschäftigen, wir nicht immer möglich, hier bestimmte, wertvolle Anleitung anzubieten. Einige der geben wir werden im Geiste "Lektionen haben wir gelernt," und "zu vermeiden, ausfällt, dass der Pfad".

Und wir wissen, von der größeren Entwurf Community viele innovative Funktionen generiert werden. Daher freuen wir von Ihnen hören und Lernen aus der Sie arbeiten eng mit Ihnen. Für unsere Teil tun wir unser Bestes freigeben unserer Einblicke, auch wenn sie die explorative und früher mit der Absicht, es Entwicklern und Designern mit Design-Überlegungen, bewährte Methoden und zugehörige open-Source-Steuerelemente, Muster und Beispiel-apps, die Sie verwenden können, sind direkt in Ihre eigene Arbeit.

## <a name="overview"></a>Übersicht

Hier ist ein schnellen Überblick darüber, wie dieser Leitfaden zum Design organisiert sind. Sie finden Abschnitte für jeden dieser Bereiche mit Links zu mehreren Artikeln.
* **[Erste Schritte mit Design](mixed-reality.md)**  – unsere Allgemeinen Gedanken lesen und verstehen Sie die Prinzipien, die wir befolgen.
* **[Instinctual Interaktionen](interaction-fundamentals.md)**  -erfahren Sie mehr über die Eingabe, Befehle, Navigation und andere Interaktion-Grundlagen für die Entwicklung von apps.
* **[Stil](typography.md)**  -machen Sie Ihre Anwendung ansprechenden, indem Sie mithilfe von Farbe, Typografie und während der Übertragung.
* **[App-Muster](types-of-mixed-reality-apps.md)**  -erfahren Sie, wie app Ications können Szenarien über faszinierende und realistische Umgebungen erstrecken.
* **[Steuerelemente](interactable-object.md)**  -Steuerelemente und Muster als Bausteine zum Erstellen Ihrer eigenen anwendungserfahrung verwenden.
* **[Beispiel-apps](design.md#sample-apps)**  -hoch funktionale Umgebungen aus Beispielen entworfen und erstellt, die von unserem Team haben.
* **[Entwerfen von Tools und Ressourcen](design.md#design-tools)**  -beschleunigen Sie Ihr Projekt mit Designvorlagen und Tools.

Für alle oben genannten wir versuchen, um die richtige Kombination von Texten, Abbildungen und Diagrammen zu übermitteln und Videos, sodass Sie uns das Experimentieren mit verschiedenen Formaten und Techniken, sehen alle mit der Absicht an, welche Informationen Sie bereitstellen müssen. Und in den Monaten im Voraus erweitern wir diese Taxonomie eine größere Gruppe der Design-Themen. Wann immer möglich, wir bieten Ihnen eine Heads-Up zu was als Nächstes geplant ist, wenden Sie sich also regelmäßig rein beibehalten.

## <a name="objectives"></a>Ziele

Wird hier ein kurzen Blick auf einige allgemeine Ziele, die diese Arbeit Richtlinien sind, damit Sie nachvollziehen können, in dem wir von kommen

### <a name="help-solve-customer-challenges"></a>Lösen Sie Kundenprobleme.

![Lösen Sie Kundenprobleme.](images/500px-fix-a-broken-switch-with-hololens.jpg) <br>

Wir Gelernte mit vielen Faktoren, die Sie aus, und wir wissen, welche Herausforderung die Arbeit ist. Es ist aufregend zu untersuchen und definieren eine neue Grenze... und es kann auch schwierig sein. Alte Paradigmen und Methoden müssen erneut betrachtet werden. Kunden benötigen neue Möglichkeiten bieten; und es ist sehr viel potenzielle für Innovationen. Angesichts der Tatsache, dass diese Arbeit so umfassend wie möglich, Verschieben ebenfalls über eine Styleguide sein soll. Wir sollen bieten eine umfassende Reihe von Entwurfsrichtlinien, die abdeckt, mixed Reality-Interaktion, Befehle, Navigation, Eingabe und Stil – alle an die Hand geben in menschliches Verhalten und Szenarien. 

### <a name="point-the-way-towards-a-new-more-human-way-of-computing"></a>Zeigen Sie die Möglichkeit für einen neuen, Menschen Weg der Datenverarbeitung

![Zeigen Sie die Möglichkeit für einen neuen, Menschen Weg der Datenverarbeitung](images/500px-man-and-women-with-holograph-on-table.png)<br>

Zwar es wichtig ist, die auf bestimmte Kundenprobleme konzentrieren, möchten wir auch selbst, darüber hinaus zu betrachten und mehr bereitstellen mithilfe von Push übertragen. Wir glauben, dass gutes Design nicht "einfach" Beheben von Problemen, sondern auch eine Möglichkeit, interaktive Entwicklung sinnvoll zu aktivieren. Neue Möglichkeiten der menschliches Verhalten; neue Methoden für die Personen, die im Zusammenhang mit sich selbst, ihre Aktivitäten und ihre Umgebungen; neue Weise sehen Sie in unserem... Wir möchten unsere Leitfäden entsprechend der folgenden mehr Plans weisen Denkweise zu. 

### <a name="meet-creators-where-they-are"></a>Entwickler, wo sie sind, zu erfüllen

![Entwickler, wo sie sind, zu erfüllen](images/500px-creators.jpg) <br>

Wir hoffen, dass viele Zielgruppen dieses Leitfadens hilfreich sein. Sie haben verschiedene-Fähigkeiten (beginnend, Zertifizierungsstellen-Zwischenzertifikat, erweitert), verwenden Sie verschiedene Tools (Unity, DirectX, C++, C#, andere), sind vertraut mit verschiedenen Plattformen (Windows, iOS, Android), stammen aus verschiedenen Hintergründen (Mobile, Enterprise, Spiele ), und arbeiten an einer anderen Größe des Teams (Solo, klein, Mittel, groß). Daher kann diese Anleitung mit unterschiedlichen Perspektiven und Anforderungen angezeigt werden. Wann immer möglich, versuchen wir, diese Vielfalt Beachten Sie, und nehmen Sie unsere Leitfäden so relevant wie möglich an so viele Anwender wie möglich. Außerdem wissen wir, dass viele von Ihnen bereits auf GitHub. Also werden wir direkt links zu GitHub-Repositorys und -Foren, die Sie erfüllen, in denen Sie bereits sind. 

### <a name="share-as-much-as-possible-from-experimental-to-explicit"></a>Freigeben Sie so weit wie möglich, aus der experimentellen zum expliziten

![Freigeben Sie so weit wie möglich, aus der experimentellen zum expliziten](images/500px-man-playinggame.jpg) <br>

Eine der Herausforderungen beim Entwurf Anleitungen in diesem neuen 3D Mittel ist, dass wir immer die definitive Anleitung zu bieten haben. Genau wie Sie sind wir learning-experimentieren, Erstellen von Prototypen, Beheben von Problemen und anpassen, Hindernisse drücken. Statt für einige Radiomoderator zukünftige Moment warten, wenn wir alles herausgefunden haben, sind wir bemüht, unser denken für Sie freigeben, in Echtzeit, auch wenn es nicht lizenzvertragsbedingungen ist. Natürlich ist unser Ziel definitive sein, wo wir können Bereitstellen klarer, flexibles Design Anleitung zu Open-Source-Code, und die in der Microsoft-Entwicklungsplattform und Entwurfstools gebunden. An diesem Punkt viele testrunden zur Iteration und Learning nimmt jedoch. Wir möchten gemeinsam mit Ihnen und mit Ihnen auf dem Weg erfahren. Mit der alle vor diesem Hintergrund müssen wir unser Bestes geben, freigeben, wie wir, auch bei unserer Plattform gesendet werden, die experimentelle ist. 

### <a name="the-right-balance-of-global-and-local-design"></a>Die richtige Balance zwischen globalen und lokalen Entwurf

![Die richtige Balance zwischen globalen und lokalen Entwurf](images/500px-fluentdesign.jpg) <br>

Bieten wir zwei Ebenen der Leitfaden zum Design: globale und lokale. Unsere "global" Entwurfsrichtlinien verkörperten ist die [Fluent-Entwurfssystem](http://fluent.microsoft.com). Fluent-Details wie wir zu den Grundlagen wie Licht, Tiefe, Bewegung, Material und Skalierung für alle Microsoft-Design – unsere Geräte, Produkte, Tools und Dienste denken. Dies bedeutet, dass erhebliche Unterschiede von gerätespezifischen in dieses größeres System vorhanden sind. Also unsere 'local' Entwurfsrichtlinien für Head eingebundenen zeigt Entwerfen für holographic und immersive-Geräte, die häufig weisen unterschiedliche Eingabe und Ausgabe von Methoden sowie anderer benutzeranforderungen und Szenarien beschrieben. Lokale Entwurfsrichtlinien enthält Themen, die für HMDs eindeutig. Zum Beispiel: 3D Umgebungen und Objekte; Freigegebene Umgebungen die Verwendung von Sensoren, Eye-Tracking und räumliche Zuordnung; und die Möglichkeiten des räumlichen Audio. In der gesamten Anleitungen wird wahrscheinlich uns auf diese globale und die lokalen Aspekte verweisen angezeigt. Hoffentlich hilft dies Ihnen Ihre Arbeit in eine größere Grundlage des Designs Erden, und nutzt die Unterschiede zwischen bestimmten Geräten.

### <a name="have-a-discussion"></a>Besprechen Sie dies

![Besprechen Sie dies](images/500px-share.jpg) <br>

Vielleicht wichtigste, möchten wir interagieren mit der Community der holographic und immersive Designer und Entwickler, dieser aufregenden neuen Ära des Entwurfs zu definieren. Wie bereits erwähnt, wissen wir, dass wir nicht über alle Antworten verfügen. Die warum wir glauben viele interessante Lösungen und Innovationen werden Sie stammen. Wir sollen öffnen und erfahren Sie mehr über, und mit Ihnen besprechen, online und Ereignisse Wert hinzufügen, wo möglich verfügbar sein. Wir freuen uns, die Teil dieses faszinierende Designcommunity, einer eingehenden zusammen Abenteuer sein. 

## <a name="please-dive-in"></a>Tauchen Sie

Wir hoffen, dass es sich bei diesem einführenden Artikel einige aussagekräftigen Kontext bereitstellt, während Sie untersuchen, dass unser Leitfaden zum Design. Tauchen Sie aus, und teilen Sie uns Ihre Meinung in den GitHub-Foren Sie finden in unseren Artikeln oder unter Microsoft Design verknüpft [Twitter](https://twitter.com/MicrosoftDesign) und [Facebook](https://www.facebook.com/microsoftdesign/). Lassen Sie uns gemeinsam entwerfen Sie die Zukunft zusammen!
