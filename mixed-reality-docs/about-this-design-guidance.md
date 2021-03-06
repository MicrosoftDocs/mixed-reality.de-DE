---
title: Informationen zu diesem Entwurfs Leit Faden
description: Dieser Leitfaden wurde von Microsoft-Designern, -Entwicklern, -Programmmanagern und -Forschern verfasst, deren Arbeit holografische Geräte (wie HoloLens) und immersive Geräte (wie die Windows Mixed Reality-Headsets von Acer und HP) umfasst.
author: mrwied
ms.author: jonwie
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Design, Introduction, Leitfaden
ms.openlocfilehash: 114a3808d57b2bd78044ce743d568bd5effe25bb
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277518"
---
# <a name="about-this-design-guidance"></a>Informationen zu diesem Entwurfs Leit Faden

## <a name="introduction"></a>Einführung

**Hallo, und Willkommen bei Ihrem Entwurfs Leit Faden für gemischte Realität.**

Diese Anleitung wird von Microsoft-Designern, Entwicklern, Programmmanagern und Forschern verfasst, deren Arbeit auf Holographic-Geräte, wie hololens und immersive Geräte, wie z. b. Acer und HP Windows Mixed Reality-Headsets, basiert. Beachten Sie diese Aufgabe als Satz von Themen zum Entwerfen von Windows-voreingestellten anzeigen.

Mit Ihnen wird ein überaus spannender neuer Zeitraum für die computingzeit eingegeben. Durchbrüche in den bereitgestellten anzeigen, räumlichen Sound, Sensoren, Umgebungs Informationen, Eingabe-und 3D-Grafiken haben wir uns herausgestellt und fordern uns an, neue Arten von Erfahrungen zu definieren, also eine neue Grenze, die deutlich persönlicher, intuitiver, immersiver und kontextbezogen ist.

Nach Möglichkeit bieten wir Ihnen einen aussagekräftigen Entwurfs Leit Faden mit verknüpften Code auf GitHub. Da wir direkt mit Ihnen zusammenarbeiten, sind wir hier nicht immer in der Lage, spezielle, Handlungs relevante Anleitungen zu bieten. Einige der freigegebenen Elemente werden im Sinne von "Lektionen, die wir gelernt haben" und "vermeiden, dass dieser Pfad ausfällt".

Und wir wissen, dass viele Innovationen von der größeren Entwurfs Community generiert werden. Wir freuen uns, von Ihnen zu hören, von Ihnen zu lernen und eng mit Ihnen zusammenzuarbeiten. Wir werden unsere Erkenntnisse unserer Meinung nach am besten teilen, auch wenn Sie explorativ und frühzeitig mit der Absicht arbeiten, Entwicklern und Designern Entwurfs-, bewährte Methoden und die dazugehörigen Open Source-Steuerelemente, Muster und Beispiel-apps zu ermöglichen, die Sie direkt in ihrer eigenen Arbeit verwenden können.

## <a name="overview"></a>Übersicht

Im folgenden finden Sie eine kurze Übersicht darüber, wie dieser Entwurfs Leit Faden organisiert ist. 
* **[Übersicht](design.md)** : erfahren Sie mehr über den Entwurfsprozess, die wichtigsten Konzepte und Interaktions Faktoren, die berücksichtigt werden müssen.
* **[Grundlegende Konzepte](core-concepts-landingpage.md)** : erfahren Sie mehr über Komfort, Holographic Frame, räumliche Zuordnung und andere wichtige Konzepte, die berücksichtigt werden müssen.
* **[Interaktionsmodelle](interaction-fundamentals.md)** : Diese Anleitung ist in drei Haupt Interaktions Modellen gegliedert.
* **[UX-Elemente](app-patterns-landingpage.md)** : Verwenden Sie Steuerelemente und Verhaltensweisen als Bausteine zum Erstellen Ihrer eigenen Anwendungserfahrung.
* **[Ressourcen](design.md#choose-a-prototyping-option)** : Starten Sie Ihr Projekt mit Entwurfs Tools und Prototypen-Optionen.

Für alle oben genannten Ziele soll die richtige Mischung aus Text, Abbildungen und Diagrammen und Videos bereitgestellt werden, sodass wir mit unterschiedlichen Formaten und Techniken experimentieren können, die alles mit der Absicht bereitstellen, was Sie brauchen. In den kommenden Monaten wird diese Taxonomie erweitert, um einen umfassenderen Satz von Entwurfs Themen einzubeziehen. Nach Möglichkeit geben wir Ihnen einen Überblick darüber, was als nächstes geplant ist. Bitte überprüfen Sie also immer wieder.

## <a name="objectives"></a>Ziele

Hier sehen Sie eine kurze Übersicht über einige allgemeine Ziele, die diese Arbeit leiten, damit Sie verstehen können, woher wir kommen.

### <a name="help-solve-customer-challenges"></a>Hilfe bei der Lösung von Kundenproblemen

![Hilfe bei der Lösung von Kundenproblemen](images/500px-fix-a-broken-switch-with-hololens.jpg) <br>

Wir führen viele der gleichen Probleme aus, und wir verstehen, wie ihre Arbeit schwierig ist. Es ist aufregend, eine neue Grenze zu erforschen und zu definieren... Außerdem kann es sich als beängstigend erweisen. Alte Paradigmen und Vorgehensweisen müssen neu gedacht werden. Kunden benötigen neue Erfahrungen. und es gibt so viele Möglichkeiten für Innovationen. Wir möchten, dass diese Arbeit so umfassend wie möglich ist, und Sie sollten sich über einen Stil Leit Faden hinaus bewegen. Wir sind bestrebt, einen umfassenden Satz von Entwurfs Anleitungen bereitzustellen, in denen gemischte Interaktionen, Befehle, Navigation, Eingaben und Stil behandelt werden – alle auf menschliches Verhalten und Szenarios basieren. 

### <a name="point-the-way-towards-a-new-more-human-way-of-computing"></a>Zeigen Sie auf eine neue, menschlichere Art von Computing

![Zeigen Sie auf eine neue, menschlichere Art von Computing](images/500px-man-and-women-with-holograph-on-table.png)<br>

Obwohl es wichtig ist, sich auf bestimmte Kunden Probleme zu konzentrieren, möchten wir uns auch selbst übertragen, um darüber nachzudenken und mehr zu erreichen. Wir glauben, dass es sich bei dem Design nicht um "einfach" um die Problembehebung handelt, sondern um eine Möglichkeit zur sinnvollen Aktivierung der menschlichen Entwicklung. Neue Methoden für menschliches Verhalten; neue Arten von Personen, die sich auf sich selbst, ihre Aktivitäten und Ihre Umgebung beziehen. neue Möglichkeiten, unsere Welt zu sehen... Wir möchten, dass unser Leitfaden all diese stärker anzurufenden Ansätze widerspiegelt. 

### <a name="meet-creators-where-they-are"></a>Treffen Sie Ersteller, wo Sie

![Treffen Sie Ersteller, wo Sie](images/500px-creators.jpg) <br>

Wir hoffen, dass viele Zielgruppen diese Anleitung finden, um hilfreich zu sein. Sie verfügen über unterschiedliche Fertigkeiten (beginnend, Intermediate, Advanced), verwenden verschiedene Tools (Unity, DirectX, C++, C#usw.), sind mit verschiedenen Plattformen (Windows, Ios, Android) vertraut und stammen aus unterschiedlichen Hintergründen (Mobile, Enterprise, Gaming) und arbeiten an verschiedenen Größen Teams ("Solo", "Small", "Medium", "Large"). Diese Anleitung kann also mit unterschiedlichen Perspektiven und Anforderungen angezeigt werden. Nach Möglichkeit werden wir versuchen, diese Vielfalt zu berücksichtigen und unsere Richtlinien so wichtig wie möglich für so viele Personen wie möglich zu gestalten. Darüber hinaus wissen wir, dass viele von Ihnen bereits auf GitHub vorhanden sind. Wir werden also direkt mit den GitHub-Repositorys und Foren verknüpft, um Ihnen den Speicherort zu begegnen, an dem Sie bereits sind. 

### <a name="share-as-much-as-possible-from-experimental-to-explicit"></a>So viel wie möglich von experimentellen bis expliziten teilen

![So viel wie möglich von experimentellen bis expliziten teilen](images/500px-man-playinggame.jpg) <br>

Eine der Herausforderungen bei der Bereitstellung eines Entwurfs Leitfadens in diesem neuen 3D-Medium besteht darin, dass wir nicht immer definitive Anleitungen zum Angebot haben. Ebenso wie Sie lernen, experimentieren, Prototypen, Problembehebung und Anpassung, wenn wir auf Hindernisse stoßen. Anstatt auf eine mythliche Zukunft zu warten, in der wir alles herausgefunden haben, wollen wir unsere Meinung in Echtzeit teilen, auch wenn Sie nicht eindeutig ist. Unser Ziel ist natürlich, an jedem Punkt eine definitive Aufgabe zu sein, eine klare, flexible Entwurfs Anleitung bereitzustellen, die mit Open Source-Code verknüpft ist und in Entwicklungs-und Entwurfs Tools von Microsoft handlungsfähig ist. Das Erreichen dieses Punkts dauert jedoch viele Runden an Iterationen und Lern Vorgängen. Wir möchten uns mit Ihnen in Verbindung treten und mit Ihnen zusammenarbeiten. Mit all diesen Gründen werden wir unsere bestmögliche Freigabe tun, auch wenn unsere experimentellen Inhalte experimentell sind. 

### <a name="the-right-balance-of-global-and-local-design"></a>Das richtige Gleichgewicht des globalen und des lokalen Entwurfs

![Das richtige Gleichgewicht des globalen und des lokalen Entwurfs](images/500px-fluentdesign.jpg) <br>

Wir bieten zwei Entwurfs Leit Fäden: Global und local. Unser "Global"-Entwurfs Leit Faden ist im Design [System "fließend](https://fluent.microsoft.com)" enthalten. Es wird ausführlich erläutert, wie wir über Grundlagen wie Light, Tiefe, Bewegung, Material und Skalierung für alle Microsoft-Entwürfe nachzudenken, unsere Geräte, Produkte, Tools und Dienste. Dies bedeutet, dass in diesem größeren System erhebliche gerätespezifische Unterschiede vorhanden sind. Der "lokale" Entwurfs Leit Faden für die in der Eingabe bereitgestellten anzeigen beschreibt den Entwurf für holografische und immersive Geräte, die häufig verschiedene Eingabe-und Ausgabemethoden sowie unterschiedliche Benutzer Anforderungen und-Szenarien aufweisen. Leitfaden zum lokalen Design behandelt die für HMDs eindeutigen Themen. Beispiel: 3D-Umgebungen und-Objekte; freigegebene Umgebungen; Verwendung von Sensoren, Augen Verfolgung und räumlicher Zuordnung und die Möglichkeiten räumlicher Audiodaten. Im Rahmen unserer Anleitung werden Sie wahrscheinlich sowohl auf die globalen als auch auf die lokalen Aspekte Bezug sehen. Hoffentlich hilft Ihnen dies, ihre Arbeit in einer größeren Entwurfs Grundlage zu unterstützen und gleichzeitig die Entwurfs Unterschiede zwischen bestimmten Geräten zu nutzen.

### <a name="have-a-discussion"></a>Diskussion

![Diskussion](images/500px-share.jpg) <br>

Vielleicht am wichtigsten ist, dass wir uns mit Ihnen, der Community von Holographic und immersiven Designern und Entwicklern in Verbindung treten möchten, um diesen neuen Entwurfs Zeitraum zu definieren. Wie bereits erwähnt, wissen wir, dass wir nicht alle Antworten haben. Aus diesem Grund werden wir glauben, dass viele interessante Lösungen und Innovationen von Ihnen kommen. Wir sind bestrebt, offen und verfügbar zu sein, um zu erfahren, wie Sie mit Ihnen Online und bei Veranstaltungen besprechen können, und Sie können jederzeit den Wert hinzufügen. Wir freuen uns, ein Teil dieser beeindruckenden Entwurfs Community zu sein, die ein Adventure zusammenfasst. 

## <a name="please-dive-in"></a>Informationen finden Sie unter

Wir hoffen, dass dieser Einführungs Artikel einen sinnvollen Kontext bietet, während Sie unsere Entwurfs Leit Fäden kennenlernen. Informieren Sie sich über Ihre Gedanken in den GitHub-Foren, die Sie in unseren Artikeln verknüpft haben, oder auf Microsoft Design auf [Twitter](https://twitter.com/MicrosoftDesign) und [Facebook](https://www.facebook.com/microsoftdesign/). Lassen Sie uns die Zukunft gemeinsam entwerfen!
