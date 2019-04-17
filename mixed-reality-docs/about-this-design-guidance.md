---
title: Informationen zu diesem Leitfaden zum design
description: Dieser Leitfaden verfasst wurde es von Microsoft-Designer, Entwickler, Programm-Managern und Forscher, deren Arbeit holographic-Geräten (z. B. HoloLens) und immersive Geräte (z. B. die Acer und HP Windows Mixed Reality-Headsets) umfasst.
author: MRWied
ms.author: jonwie
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, entwerfen, Einführung, Anleitungen
ms.openlocfilehash: b4f128c001a2fa6ed72e1548ef82693ad1488099
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593800"
---
# <a name="about-this-design-guidance"></a>Informationen zu diesem Leitfaden zum design

## <a name="introduction"></a>Einführung

**Hallo und Willkommen bei Ihrem Entwurfsrichtlinien für mixed Reality.**

Dieser Leitfaden verfasst wurde es von Microsoft-Designer, Entwickler, Programm-Managern und Forscher, deren Arbeit holographic-Geräten (z. B. HoloLens) und immersive Geräte (z. B. die Acer und HP Windows Mixed Reality-Headsets) umfasst. Daher sollten Sie diese Arbeit als eine Reihe von Themen für die "Gewusst wie: Entwerfen für Windows-Head eingebundenen zeigt" ein.

Mit Ihnen werden wir eine äußerst interessante neue Ära der Datenverarbeitung eingeben. Bahnbrechende Head bereitgestellt wird, zeigt, räumliche Sound, Sensoren, Umweltbewusstseins, Eingabe und 3D-Grafiken führen Sie uns, und fordern Sie uns, neue Typen von Benutzeroberflächen definieren... eine neue Grenze, die erheblich mehr personal, intuitive, immersive und kontextbezogene ist.

Wo immer dies möglich ist, bieten wir umsetzbare Entwurfsrichtlinien, mit zugehörigem Code auf GitHub. Also, da es rechts neben Sie beschäftigen, wir nicht immer möglich, hier bestimmte, wertvolle Anleitung anzubieten. Einige der geben wir werden im Geiste "Lektionen haben wir gelernt," und "zu vermeiden, ausfällt, dass der Pfad".

Und wir wissen, dass viele innovative Funktionen von der größeren Designcommunity, generiert werden, damit wir von Ihnen hören und Lernen aus der Sie arbeiten eng mit Ihnen freuen. Für unsere Teil werden wir unser Bestes geben, um unsere Erkenntnisse, zu teilen, selbst wenn sie dienen zur Orientierung und früh, mit der Absicht, es Entwicklern und Designern mit Design-Überlegungen, bewährte Methoden und die zugehörigen öffnen Datenquellen-Steuerelemente, Muster und Beispiel-apps, die Sie verwenden können direkt in Ihre eigene Arbeit.

## <a name="overview"></a>Übersicht

Hier ist ein schnellen Überblick darüber, wie dieser Leitfaden zum Design organisiert sind. Sie finden Abschnitte für jeden dieser Bereiche mit Links zu mehreren Artikeln.
* **[Erste Schritte mit Design](mixed-reality.md)**  – unsere Allgemeinen Gedanken lesen und verstehen Sie die Prinzipien, die wir befolgen.
* **[Entwerfen für](interaction-fundamentals.md)**  -erfahren Sie mehr über die Eingabe, Befehle, Navigation und andere Interaktion-Grundlagen für die Entwicklung von apps.
* **[Stil](typography.md)**  -Ihrer-app mithilfe von Farbe, Typografie und während der Übertragung ansprechenden stellen.
* **[App-Muster](types-of-mixed-reality-apps.md)**  -erfahren Sie, wie apps Szenarien über faszinierende und realistische Umgebungen erstrecken können.
* **[Steuerelemente](interactable-object.md)**  -Steuerelemente und Muster verwenden, wie Bausteine, die zum Erstellen Ihrer eigenen app tun.
* **[Beispiel-apps](design.md#sample-apps)**  -hoch funktionale Umgebungen aus Beispielen entworfen und erstellt, die von unserem Team haben.
* **[Entwerfen von Tools und Ressourcen](design.md#design-tools)**  -beschleunigen Sie Ihr Projekt mit Designvorlagen und Tools.

Für alle oben genannten wir versuchen, um die richtige Kombination von Texten, Abbildungen und Diagrammen zu übermitteln und Videos, sodass Sie uns das Experimentieren mit verschiedenen Formaten und Techniken, sehen alle mit der Absicht an, welche Informationen Sie bereitstellen müssen. Und in den Monaten im Voraus erweitern wir diese Taxonomie eine größere Gruppe der Design-Themen. Wann immer möglich, wir bieten Ihnen eine Heads-Up zu was als Nächstes geplant ist, wenden Sie sich also regelmäßig rein beibehalten.

## <a name="objectives"></a>Ziele

Hier ist ein kurzen Blick auf einige allgemeine Ziele, die diese Arbeit Richtlinien sind, damit Sie nachvollziehen können, in dem wir von kommen:

### <a name="help-solve-customer-challenges"></a>Lösen Sie Kundenprobleme.

![Lösen Sie Kundenprobleme.](images/500px-fix-a-broken-switch-with-hololens.jpg) <br>

Wir Gelernte mit vielen Faktoren, die Sie aus, und wir wissen, welche Herausforderung die Arbeit ist. Es ist aufregend zu untersuchen und definieren eine neue Grenze... und es kann auch schwierig sein. Alte Paradigmen und Methoden müssen erneut betrachtet werden. neue Erfahrungen von Kunden, erforderlich; und es ist sehr viel potenzielle für Innovationen. Diesen möchten wir diese Arbeit so umfassend wie möglich, Verschieben ebenfalls über eine Styleguide sein. Wir sollen bieten eine umfassende Reihe von Entwurfsrichtlinien, die abdeckt, mixed Reality-Interaktion, Befehle, Navigation, Eingabe und Stil – alle an die Hand geben in menschliches Verhalten und Szenarien. 

### <a name="point-the-way-towards-a-new-more-human-way-of-computing"></a>Zeigen Sie die Möglichkeit für einen neuen, Menschen Weg der Datenverarbeitung

![Zeigen Sie die Möglichkeit für einen neuen, Menschen Weg der Datenverarbeitung](images/500px-man-and-women-with-holograph-on-table.png)<br>

Zwar es wichtig ist, die auf bestimmte Kundenprobleme konzentrieren, möchten wir auch selbst, darüber hinaus zu betrachten und mehr bereitstellen mithilfe von Push übertragen. Wir glauben, dass gutes Design nicht "einfach" Beheben von Problemen, sondern auch eine Möglichkeit, interaktive Entwicklung sinnvoll zu aktivieren. Neue Möglichkeiten der menschliches Verhalten; neue Methoden für die Personen, die im Zusammenhang mit sich selbst, ihre Aktivitäten und ihre Umgebungen; neue Weise sehen Sie in unserem... Wir möchten unsere Leitfäden entsprechend der folgenden mehr Plans weisen Denkweise zu. 

### <a name="meet-creators-where-they-are"></a>Entwickler, wo sie sind, zu erfüllen

![Entwickler, wo sie sind, zu erfüllen](images/500px-creators.jpg) <br>

Wir hoffen, dass viele Zielgruppen dieses Leitfadens hilfreich sein. Sie haben verschiedene-Fähigkeiten (beginnend, Zertifizierungsstellen-Zwischenzertifikat, erweitert), verwenden Sie verschiedene Tools (Unity, DirectX, C++, C#, andere), sind vertraut mit verschiedenen Plattformen (Windows, iOS, Android), stammen aus verschiedenen Hintergründen (Mobile, Enterprise, Spiele ), und arbeiten an einer anderen Größe des Teams (Solo, klein, Mittel, groß). Daher wird dieser Anleitung mit unterschiedlichen Perspektiven und Anforderungen angezeigt werden. Wann immer möglich, versuchen wir, diese Vielfalt Beachten Sie, und nehmen Sie unsere Leitfäden so relevant wie möglich an so viele Anwender wie möglich. Außerdem wissen wir, dass viele von Ihnen bereits auf GitHub, sodass wir direkt verknüpft ist, wird auf GitHub-Repositorys und -Foren, die Sie erfüllen, in denen Sie bereits sind. 

### <a name="share-as-much-as-possible-from-experimental-to-explicit"></a>Freigeben Sie so weit wie möglich, aus der experimentellen zum expliziten

![Freigeben Sie so weit wie möglich, aus der experimentellen zum expliziten](images/500px-man-playinggame.jpg) <br>

Eine der Herausforderungen beim Entwurf Anleitungen in diesem neuen 3D Mittel ist, dass wir immer die definitive Anleitung zu bieten haben. Genau wie Sie sind wir learning-experimentieren, Erstellen von Prototypen, Beheben von Problemen und anpassen, Hindernisse drücken. Statt für einige Radiomoderator zukünftige Moment warten, wenn wir alles herausgefunden haben, versuchen wir unser denken für Sie Echtzeit freigeben, selbst wenn er nicht lizenzvertragsbedingungen ist. Natürlich ist unser Ziel definitive, wo wir können die Bereitstellung löschen, flexible Entwurfsrichtlinien an Open-Source-Code gebunden, und in der Microsoft-Tools für Entwicklung und Entwurf. An diesem Punkt viele testrunden zur Iteration und Learning nimmt jedoch. Gemeinsam mit Ihnen aus, und erfahren, mit Ihnen gerne dabei, damit wir das beste um gemeinsam nutzen durchführen, wie wir wechseln, sogar unserer Plattform, die experimentelle ist. 

### <a name="the-right-balance-of-global-and-local-design"></a>Die richtige Balance zwischen globalen und lokalen Entwurf

![Die richtige Balance zwischen globalen und lokalen Entwurf](images/500px-fluentdesign.jpg) <br>

Bieten wir zwei Ebenen der Leitfaden zum Design: globale und lokale. Unsere "global" Entwurfsrichtlinien verkörperten ist die [Fluent-Entwurfssystem](http://fluent.microsoft.com). Fluent-Details wie wir zu den Grundlagen wie Licht, Tiefe, Bewegung, Material und Skalierung für alle Microsoft-Design – unsere Geräte, Produkte, Tools und Dienste denken. Dass der besagten, erhebliche und gerätespezifische Unterschiede, die in dieses größeres System, vorhanden sind, damit unsere "Local" Anleitung Head eingebundenen zeigt entwerfen Beschreibt-Entwurf für holographic und immersive Geräte, die oft unterschiedliche Eingabe- und Ausgabemethoden, haben und andere benutzeranforderungen und Szenarien. Der lokale Entwurfsrichtlinien deckt Themen, die nur für HMDs, z. B. 3D Umgebungen und Objekte; Freigegebene Umgebungen die Verwendung von Sensoren, Eye-Tracking und räumliche Zuordnung; und die Möglichkeiten des räumlichen Audio. In der gesamten unsere Leitfäden wahrscheinlich sehen Sie uns auf diese globale und die lokalen Aspekte verweisen, und hoffentlich Dies hilft Ihnen bei die Arbeit in eine größere Grundlage des Designs Erden, und nutzt die abweichungen im Design von bestimmten Geräten.

### <a name="have-a-discussion"></a>Besprechen Sie dies

![Besprechen Sie dies](images/500px-share.jpg) <br>

Vielleicht wichtigste, möchten wir interagieren mit der Community der holographic und immersive Designer und Entwickler, dieser aufregenden neuen Ära des Entwurfs zu definieren. Wie bereits erwähnt, wissen wir wir nicht alle Antworten, und wir glauben, dass viele interessante Lösungen und Innovationen kommen Sie. Wir sollen öffnen und erfahren Sie mehr über, und mit Ihnen besprechen, online und Ereignisse Wert hinzufügen, wo möglich verfügbar sein. Wir freuen uns, die Teil dieses faszinierende Designcommunity, einer eingehenden zusammen Abenteuer sein. 

## <a name="please-dive-in"></a>Tauchen Sie

Wir hoffen, dass in diesem Artikel Willkommen einige aussagekräftigen Kontext bereitstellt, während Sie untersuchen, dass unser Leitfaden zum Design. Tauchen Sie aus, und teilen Sie uns Ihre Meinung in den GitHub-Foren Sie finden in unseren Artikeln oder unter Microsoft Design verknüpft [Twitter](https://twitter.com/MicrosoftDesign) und [Facebook](https://www.facebook.com/microsoftdesign/). Lassen Sie uns gemeinsam entwerfen Sie die Zukunft zusammen!
