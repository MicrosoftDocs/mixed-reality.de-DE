---
title: Informationen zu diesem Entwurfs Leit Faden
description: Dieser Leitfaden wurde von Microsoft-Designern, -Entwicklern, -Programmmanagern und -Forschern verfasst, deren Arbeit holografische Geräte (wie HoloLens) und immersive Geräte (wie die Windows Mixed Reality-Headsets von Acer und HP) umfasst.
author: MRWied
ms.author: jonwie
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Design, Introduction, Leitfaden
ms.openlocfilehash: 0e5601898c2b1f351b5ab2aaa491a7c64ae57f7e
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414163"
---
# <a name="about-this-design-guidance"></a>Informationen zu diesem Entwurfs Leit Faden

## <a name="introduction"></a>Einführung

**Hallo, und Willkommen bei Ihrem Entwurfs Leit Faden für gemischte Realität.**

Diese Anleitung wird von Microsoft-Designern, Entwicklern, Programmmanagern und Forschern verfasst, deren Arbeit auf Holographic-Geräte, wie hololens und immersive Geräte, wie z. b. Acer und HP Windows Mixed Reality-Headsets, basiert. Beachten Sie diese Aufgabe als Satz von Themen zum Entwerfen von Windows-voreingestellten anzeigen.

Mit Ihnen wird ein überaus spannender neuer Zeitraum für die computingzeit eingegeben. Durchbrüche in den bereitgestellten anzeigen, räumlichen Sound, Sensoren, Umgebungs Informationen, Eingabe-und 3D-Grafiken haben wir uns herausgestellt und fordern uns an, neue Arten von Erfahrungen zu definieren, also eine neue Grenze, die deutlich persönlicher, intuitiver, immersiver und kontextbezogen ist.

Nach Möglichkeit bieten wir Ihnen einen aussagekräftigen Entwurfs Leit Faden mit verknüpften Code auf GitHub. Da wir direkt mit Ihnen zusammenarbeiten, sind wir hier nicht immer in der Lage, spezielle, Handlungs relevante Anleitungen zu bieten. Einige der freigegebenen Elemente werden im Sinne von "Lektionen, die wir gelernt haben" und "vermeiden, dass dieser Pfad ausfällt".

Und wir wissen, dass viele Innovationen von der größeren Entwurfs Community generiert werden. Wir freuen uns, von Ihnen zu hören, von Ihnen zu lernen und eng mit Ihnen zusammenzuarbeiten. Unserer Meinung nach machen wir unsere Erkenntnisse, auch wenn Sie explorativ und frühzeitig mit der Absicht arbeiten, Entwicklern und Designern Entwurfs denken, bewährte Methoden und die dazugehörigen Open Source-Steuerelemente, Muster und Beispiel-apps zu ermöglichen, die Sie verwenden können. direkt in ihrer eigenen Arbeit.

## <a name="overview"></a>Übersicht

Im folgenden finden Sie eine kurze Übersicht darüber, wie dieser Entwurfs Leit Faden organisiert ist. Sie finden Abschnitte für jeden dieser Bereiche mit Links zu mehreren Artikeln.
* **[Beginnen Sie mit dem Entwurf](mixed-reality.md)** : Lesen Sie unsere grundlegenden Gedanken, und verstehen Sie die folgenden Prinzipien.
* **[Instanzielle Interaktionen](interaction-fundamentals.md)** : erfahren Sie mehr über Eingabe-, Befehls-, Navigations-und andere Interaktions Grundlagen für das Entwerfen von apps.
* **[Stil](typography.md)** : machen Sie Ihre Anwendung mithilfe von Farbe, Typografie und Bewegung reizvoll.
* **[App-Muster](types-of-mixed-reality-apps.md)** : erfahren Sie, wie Anwendungen Szenarien in immersiven und realen Umgebungen umfassen können.
* Steuer **[Elemente](interactable-object.md)** : Verwenden Sie Steuerelemente und Muster als Bausteine, um Ihre eigene Anwendung zu erstellen.
* **[Beispiel-apps](design.md#sample-apps)** : Erstellen Sie gute Erfahrungen aus Beispielen, die von unserem Team entworfen und erstellt wurden.
* **[Entwurfs Tools und-Ressourcen](design.md#design-tools)** : Starten Sie Ihr Projekt mit Entwurfsvorlagen und-Tools.

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

Wir hoffen, dass viele Zielgruppen diese Anleitung finden, um hilfreich zu sein. Sie verfügen über unterschiedliche Fertigkeiten (Anfang, Fortgeschrittene, erweitert), verwenden verschiedene Tools (Unity, DirectX C++, C#, usw.), sind mit verschiedenen Plattformen (Windows, Ios, Android) vertraut und stammen aus unterschiedlichen Hintergründen (Mobile, Enterprise, Gaming). ), und arbeiten an unterschiedlichen Größen Teams ("Solo", "Small", "Medium", "Large"). Diese Anleitung kann also mit unterschiedlichen Perspektiven und Anforderungen angezeigt werden. Nach Möglichkeit werden wir versuchen, diese Vielfalt zu berücksichtigen und unsere Richtlinien so wichtig wie möglich für so viele Personen wie möglich zu gestalten. Darüber hinaus wissen wir, dass viele von Ihnen bereits auf GitHub vorhanden sind. Wir werden also direkt mit den GitHub-Repositorys und Foren verknüpft, um Ihnen den Speicherort zu begegnen, an dem Sie bereits sind. 

### <a name="share-as-much-as-possible-from-experimental-to-explicit"></a>So viel wie möglich von experimentellen bis expliziten teilen

![So viel wie möglich von experimentellen bis expliziten teilen](images/500px-man-playinggame.jpg) <br>

Eine der Herausforderungen bei der Bereitstellung eines Entwurfs Leitfadens in diesem neuen 3D-Medium besteht darin, dass wir nicht immer definitive Anleitungen zum Angebot haben. Ebenso wie Sie lernen, experimentieren, Prototypen, Problembehebung und Anpassung, wenn wir auf Hindernisse stoßen. Anstatt auf eine mythliche Zukunft zu warten, in der wir alles herausgefunden haben, wollen wir unsere Meinung in Echtzeit teilen, auch wenn Sie nicht eindeutig ist. Unser Ziel ist natürlich, an jedem Punkt eine definitive Aufgabe zu sein, eine klare, flexible Entwurfs Anleitung bereitzustellen, die mit Open Source-Code verknüpft ist und in Entwicklungs-und Entwurfs Tools von Microsoft handlungsfähig ist. Das Erreichen dieses Punkts dauert jedoch viele Runden an Iterationen und Lern Vorgängen. Wir möchten uns mit Ihnen in Verbindung treten und mit Ihnen zusammenarbeiten. Mit all diesen Gründen werden wir unsere bestmögliche Freigabe tun, auch wenn unsere experimentellen Inhalte experimentell sind. 

### <a name="the-right-balance-of-global-and-local-design"></a>Das richtige Gleichgewicht des globalen und des lokalen Entwurfs

![Das richtige Gleichgewicht des globalen und des lokalen Entwurfs](images/500px-fluentdesign.jpg) <br>

Wir bieten zwei Entwurfs Leit Fäden: Global und local. Unser "Global"-Entwurfs Leit Faden ist im Design [System "fließend](http://fluent.microsoft.com)" enthalten. Es wird ausführlich erläutert, wie wir über Grundlagen wie Light, Tiefe, Bewegung, Material und Skalierung für alle Microsoft-Entwürfe nachzudenken, unsere Geräte, Produkte, Tools und Dienste. Dies bedeutet, dass in diesem größeren System erhebliche gerätespezifische Unterschiede vorhanden sind. Der "lokale" Entwurfs Leit Faden für die in der Eingabe bereitgestellten anzeigen beschreibt den Entwurf für holografische und immersive Geräte, die häufig verschiedene Eingabe-und Ausgabemethoden sowie unterschiedliche Benutzer Anforderungen und-Szenarien aufweisen. Leitfaden zum lokalen Design behandelt die für HMDs eindeutigen Themen. Zum Beispiel: 3D-Umgebungen und-Objekte; freigegebene Umgebungen; Verwendung von Sensoren, Augen Verfolgung und räumlicher Zuordnung und die Möglichkeiten räumlicher Audiodaten. Im Rahmen unserer Anleitung werden Sie wahrscheinlich sowohl auf die globalen als auch auf die lokalen Aspekte Bezug sehen. Hoffentlich hilft Ihnen dies, ihre Arbeit in einer größeren Entwurfs Grundlage zu unterstützen und gleichzeitig die Entwurfs Unterschiede zwischen bestimmten Geräten zu nutzen.

### <a name="have-a-discussion"></a>Diskussion

![Diskussion](images/500px-share.jpg) <br>

Vielleicht am wichtigsten ist, dass wir uns mit Ihnen, der Community von Holographic und immersiven Designern und Entwicklern in Verbindung treten möchten, um diesen neuen Entwurfs Zeitraum zu definieren. Wie bereits erwähnt, wissen wir, dass wir nicht alle Antworten haben. Aus diesem Grund werden wir glauben, dass viele interessante Lösungen und Innovationen von Ihnen kommen. Wir sind bestrebt, offen und verfügbar zu sein, um zu erfahren, wie Sie mit Ihnen Online und bei Veranstaltungen besprechen können, und Sie können jederzeit den Wert hinzufügen. Wir freuen uns, ein Teil dieser beeindruckenden Entwurfs Community zu sein, die ein Adventure zusammenfasst. 

## <a name="please-dive-in"></a>Informationen finden Sie unter

Wir hoffen, dass dieser Einführungs Artikel einen sinnvollen Kontext bietet, während Sie unsere Entwurfs Leit Fäden kennenlernen. Informieren Sie sich über Ihre Gedanken in den GitHub-Foren, die Sie in unseren Artikeln verknüpft haben, oder auf Microsoft Design auf [Twitter](https://twitter.com/MicrosoftDesign) und [Facebook](https://www.facebook.com/microsoftdesign/). Lassen Sie uns die Zukunft gemeinsam entwerfen!
