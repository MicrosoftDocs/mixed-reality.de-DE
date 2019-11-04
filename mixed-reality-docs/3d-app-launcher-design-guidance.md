---
title: Leitfaden zum Entwerfen von 3D-apps
description: Ein 3D-App-Startfeld ist ein "physisches" Objekt im gemischten Reality-Haus des Benutzers, das Sie auswählen können, um eine APP zu starten.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Design, 3D-App-Startfeld, immersives Headset, Live Cube
ms.openlocfilehash: ce9d242e26d67c8fe5af7ac32f4e910a15715d25
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437231"
---
# <a name="3d-app-launcher-design-guidance"></a>Leitfaden zum Entwerfen von 3D-apps

Wenn Sie ein Windows Mixed Reality immersive (VR)-Headset platzieren, können Sie die Windows Mixed Reality-Startseite eingeben und als Haus auf einer Klippe visualisieren, die von Bergen und Wasser umgeben ist (Sie können jedoch [auch andere Umgebungen auswählen und sogar eigene Umgebungen erstellen](add-custom-home-environments.md)). Innerhalb des Raums dieses Zuhause kann ein Benutzer die 3D-Objekte und-apps, die für Sie wichtig sind, anordnen und organisieren. Ein **3D-App-** Startfeld ist ein "physisches" Objekt im gemischten Reality-Haus des Benutzers, das Sie auswählen können, um eine APP zu starten.

![Beispiel: floaty Bird 3D-App-Startfeld](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*Beispiel für floaty Bird 3D-App-Startfeld (fiktive APP)*

## <a name="3d-app-launcher-creation-process"></a>Erstellung eines 3D-App-Start Programms

Zum Erstellen eines 3D-App-Start Programms sind drei Schritte erforderlich:
1. Entwerfen und entwerfen (dieser Artikel)
2. [Modellieren und exportieren](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integration in Ihre Anwendung:
    * [UWP-Apps](implementing-3d-app-launchers.md)
    * [Win32-apps](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>Entwurfskonzepte

### <a name="fantastic-yet-familiar"></a>Fantastisch, aber schon vertraut

Die Windows Mixed Reality-Umgebung, in der sich Ihr App-Startfeld befindet, ist Teil vertraut, Teil fantastisch/Sci-Fi. Die besten Launcher befolgen die Regeln dieser Welt. Stellen Sie sich vor, wie Sie ein vertrautes, repräsentatives Objekt von Ihrer APP aus erstellen, aber einige der Regeln der tatsächlichen Realität übernehmen können. Magic führt dazu.

### <a name="intuitive"></a>Intuitiven

Wenn Sie sich Ihr App-Startfeld ansehen, sollte der Zweck zum Starten Ihrer APP offensichtlich sein und keine Verwirrung verursachen. Stellen Sie sich z. b. vor, dass Ihr Start Programm ein offensichtlich-genug repräsentativ für Ihre APP ist, dass Sie nicht mit einem Teil der Einrichtung im Klippe-Haus verwechselt wird. Ihr App-Start Programm sollte Personen einladen, Sie zu berühren bzw. auszuwählen.

![Beispiel: neues Hinweis 3D-App-Startfeld](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*Neues Hinweis Beispiel für 3D-App-Start Programm (fiktive APP)*

### <a name="home-scale"></a>Start Skala

3D-App-Launcher Leben im Klippe-Haus, und ihre Standardgröße sollte mit den anderen "physischen" Objekten im Raum Sinn machen. Wenn Sie das Start Programm anordnen, beispielsweise eine Hausanlage oder einige Möbel, sollte es sich in der eigenen Größe fühlen. Ein guter Ausgangspunkt ist, zu sehen, wie es 30 Kubikzentimeter aussieht, aber denken Sie daran, dass Benutzer es bei Bedarf zentral hoch-oder Herunterskalieren können.

### <a name="own-able"></a>Eigen fähig

Das App-Start Programm sollte sich wie ein Objekt erweisen, das eine Person im Raum haben würde. Sie werden sich praktisch durch diese Dinge umgeben, sodass das Start Programm so aussehen sollte, wie etwas, was der Benutzer als wünschenswert erachtet hat

![Beispiel: Astro Warp 3D-App-Startfeld](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*Beispiel für ein Beispiel für die Astro Warp 3D-app (fiktive APP)*

### <a name="recognizable"></a>Unerkannt

Ihr 3D-App-Startfeld sollte den Benutzern, die Sie sehen, umgehend die "Marke Ihrer APP" ausdrücken. Wenn Sie ein Sternzeichen oder ein besonders identifizierbares Objekt in Ihrer APP haben, empfiehlt es sich, dieses als einen großen Teil des Entwurfs zu verwenden. In einer Mixed Reality-Welt zeichnet ein Objekt von Benutzern mehr Interesse als nur ein Logo allein. Erkennbare Objekte kommunizieren schnell und eindeutig.

### <a name="volumetric"></a>Volumetrische

Ihre APP verdient mehr als nur Ihr Logo auf eine flache Ebene zu bringen und Sie täglich Aufrufs. Das Start Programm sollte sich wie ein spannendes, 3D-Objekt im Bereich des Benutzers fühlen. Eine gute Vorgehensweise besteht darin, sich zu vorstellen, dass Ihre APP in der Tages Parade der Macy-Tage eine Sprechblase enthalten würde. Fragen Sie sich, was wirklich Menschen ist, die sich in der Straße befinden? Was ist für alle Anzeige Winkel großartig?


:::row:::
    :::column:::
        ![Logo nur](images/20171016-140436-mixedreality-640px.jpg) *Logo*
    :::column-end:::
    :::column:::
        ![mit einem Zeichen besser erkennbar](images/20171016-140557-mixedreality-640px.jpg) *mit einem Zeichen besser erkennbar*
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        ![flachen Ansatz, nicht überraschend, ist ein flacher](images/20171016-155101-mixedreality-640px.jpg) *flacher Ansatz, nicht überraschend, ist flach* .
    :::column-end:::
    :::column:::
        ![Volumetric-Ansatz stellt Ihre APP besser dar](images/20171016-161407-mixedreality-640px.jpg) *volumetriansatz Ihre APP besser präsentiert* .
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a>Tipps für gute 3D-Modelle

### <a name="best-practices"></a>Bewährte Verfahren
* Wenn Sie Dimensionen für das App-Start Programm planen, sollten Sie ungefähr einen 30cm-Cube durchsuchen. Also ein Größenverhältnis von 1:1:1.
* Modelle müssen unter 10.000 Polygone liegen. [Weitere Informationen zu Dreiecks Zählungen und Ebenen der Details (LODs)](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* Testen Sie nach Möglichkeit ein immersives Headset.
* Builddetails in der Geometrie des Modells, soweit möglich – verlassen Sie sich nicht auf Texturen.
* Erstellen einer "wasserdichten" geschlossenen Geometrie. Keine Lücken, die nicht in modelliert werden.
* Verwenden Sie natürliche Materialien in Ihrem Objekt. Stellen Sie sich vor, Sie erstellen Sie in der Praxis.
* Stellen Sie sicher, dass Ihr Modell in unterschiedlichen Entfernungen und Größen gut funktioniert.
* Wenn Ihr Modell einsatzbereit ist, lesen Sie die [Richtlinien zum Exportieren von Assets](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).

![Modell mit geringfügigen Details in der Textur](images/20171013-143334-mixedreality-640px.jpg)<br>
*Modell mit geringfügigen Details in der Textur*

### <a name="what-to-avoid"></a>Was Sie vermeiden sollten
* Verwenden Sie keine kontrastreichen Details oder kleine, ausgelastete Muster und Texturen.
* Verwenden Sie Thin Geometry nicht – es funktioniert nicht gut in einer Entfernung und ist falsch.
* Lassen Sie Teile des Modells nicht zu viel über das Größenverhältnis von 1:1:1 hinaus erweitern. Es werden Skalierungsprobleme entstehen.

![vermeiden Sie Muster mit hohem Kontrast und wenig ausgelastet](images/20171013-143603-mixedreality-640px.jpg)<br>
*Vermeiden Sie große Kontraste, kleine, ausgelastete Muster*

## <a name="how-to-handle-type"></a>Vorgehensweise beim Behandeln von Typen

### <a name="best-practices"></a>Bewährte Verfahren
* Es wird empfohlen, dass Ihr Typ ungefähr 1/3 ihres App-Start Programms umfasst (oder mehr). Der Typ ist das wichtigste, das den Benutzern eine Vorstellung gibt, dass es sich bei Ihrem Start Programm tatsächlich um ein Start Programm handelt, sodass es sehr schön ist.
* Vermeiden Sie einen Super weiten Typ – versuchen Sie, ihn innerhalb der Grenzen der Kerndimensionen der App-Launcher (mehr oder weniger) zu halten.
* Der flattype kann funktionieren, aber beachten Sie, dass er in bestimmten Winkeln und in bestimmten Umgebungen schwer zu erkennen ist. Möglicherweise sollten Sie ein solides Objekt oder einen Hintergrund dahinter ablegen, um dies zu unterstützen.
* Das Hinzufügen von Dimensionen zu Ihrem Typ ist in 3D gut. Das Schattieren der Seiten des Typs unterscheidet sich durch die Lesbarkeit.


:::row:::
    :::column:::
        ![flattype ohne einen Hintergrund kann in bestimmten Winkeln und in bestimmten Umgebungen schwer zu finden sein](images/flattype-640px.png) *flacher Typ ohne Hintergrund kann in bestimmten Winkeln und in bestimmten Umgebungen schwer zu sehen sein* .
    :::column-end:::
    :::column:::
        ![Typ mit einem integrierten Hintergrund kann gut funktionieren](images/flattypeandbkg-640px.png) *Typ mit einem integrierten Hintergrund kann gut funktionieren* .
    :::column-end:::
    :::column:::
        Wenn Sie die Seiten schattieren, ![der Typ "extrudiert" gut funktioniert,](images/20171016-160221-mixedreality-640px.jpg) der *Typ "extrudiert" gut funktionieren, wenn Sie die Seiten schattieren*
    :::column-end:::
:::row-end:::


**Typfarben, die funktionieren**
* Weisse
* Box
* Helle halb satte Farbe

![typfarben, die funktionieren.](images/20171016-112111-mixedreality-640px.jpg)<br>
*Typfarben, die funktionieren*

### <a name="what-to-avoid"></a>Was Sie vermeiden sollten

**Typfarben, die Probleme verursachen**
* Mitteltöne
* grau
* Über satte Farben oder nicht satte Farben

![typfarben, die Probleme verursachen.](images/20171016-112246-mixedreality-640px.jpg)<br>
*Typfarben, die Probleme verursachen*

## <a name="lighting"></a>Beleuchtung

Die Beleuchtung für das App-Start Programm stammt aus der Umgebung "Klippe House". Stellen Sie sicher, dass Sie das Start Programm an mehreren Stellen im ganzen Haus testen, damit es in Licht und Schatten gut aussieht. Die gute Nachricht ist, dass Sie, wenn Sie den anderen Entwurfs Leit Faden in diesem Dokument befolgt haben, das Start Programm in einer ziemlich guten Form für die meisten Beleuchtung im Klippe-Haus aufweisen sollten.

Ein guter Ausgangspunkt, um zu testen, wie das Start Programm in den verschiedenen Lichtern in der Umgebung aussieht, sind Studio, der Medienraum, an einer beliebigen Stelle außerhalb und auf der Rückseite (der konkrete Bereich mit dem Rasen). Ein weiterer guter Test besteht darin, den halblicht-und Halbschatten zu platzieren und zu sehen, wie er aussieht.

![stellen Sie sicher, dass das Start Programm sowohl in Beleuchtung als auch in Schatten angezeigt wird.](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*Stellen Sie sicher, dass das Start Programm in Licht und Schatten gut aussieht*

## <a name="texturing"></a>Texturierung

### <a name="authoring-your-textures"></a>Erstellen von Texturen

Das Endformat des 3D-App-Start Programms ist eine. GLB-Datei, die mithilfe der PBR-Pipeline (physisch basiertes Rendering) erstellt wird. Dies kann ein kniffliger Prozess sein. jetzt ist es ein guter Zeitpunkt, einen technischen Künstler zu verwenden, wenn Sie dies noch nicht getan haben. Wenn Sie ein mutiger DIY sind und sich die Zeit nehmen, sich mit der [PBR-Terminologie](https://wiki.polycount.com/wiki/PBR) vertraut zu machen und zu erfahren, was im Hintergrund passiert, bevor Sie beginnen, können Sie häufige Fehler vermeiden. 

![Beispiel: App für neue Notiz](images/pbr-freshnote1-640px-500px.png)<br>
*Neues Hinweis Beispiel für 3D-App-Start Programm (fiktive APP)*

**Empfohlenes Authoring Tool**

Es wird empfohlen, den [Substanz Maler](https://www.allegorithmic.com/products/substance-painter) von allethmic zu verwenden, um Ihre endgültige Datei zu verfassen. Wenn Sie nicht mit der Erstellung von PBR-Shadern in der Inhalts Malerin vertraut sind, finden Sie hier ein [Tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).

(Alternativ kann [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/)oder [marthset](https://www.marmoset.co/toolbag/) auch verwendet werden, wenn Sie mit einer der beiden vertraut sind.)

### <a name="best-practices"></a>Bewährte Verfahren

* Wenn das App-Start Programmobjekt für PBR erstellt wurde, sollte es recht einfach sein, es für die Umgebung "Klippe" zu konvertieren.
* Unser Shader erwartet einen Metal/roughness-Workflow – der Unreal PBR-Shader ist ein schließende Fax.
* Wenn Sie Ihre Texturen exportieren, sollten Sie die [empfohlenen Textur Größen](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) berücksichtigen.
* Stellen Sie sicher, dass Sie die Objekte für die Echtzeitbeleuchtung erstellen – Dies bedeutet Folgendes:
    * Vermeiden gebackener Schatten – oder gezeichnete Schatten
    * Vermeiden Sie eine gebackenes Beleuchtung in den Texturen
    * Verwenden Sie eines der Pakete zur Erstellung von PBR-Materialien, um die richtigen Zuordnungen für den Shader zu erhalten.

## <a name="see-also"></a>Weitere Informationen:

* [Erstellen von 3D-Modellen für die Verwendung in der Mixed Reality-Startseite](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementieren von 3D-App-Startprogrammen (UWP-Apps)](implementing-3d-app-launchers.md)
* [Implementieren von 3D-App-Startprogrammen (Win32-Apps)](implementing-3d-app-launchers-win32.md)
