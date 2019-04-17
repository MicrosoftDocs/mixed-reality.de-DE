---
title: Leitfaden zum Entwerfen von 3D app-Startfeld
description: Ein-3D-app-Startfeld ist ein "physical"-Objekt in der Benutzer mixed Reality Haus, die sie auswählen können, um eine app zu starten.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Entwurf, 3D app-Startfeld, immersive Kopfhörer, live-cube
ms.openlocfilehash: 47db5bffa121c0cc11d246dc749c464e5f187270
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593645"
---
# <a name="3d-app-launcher-design-guidance"></a>Leitfaden zum Entwerfen von 3D app-Startfeld

Wenn Sie auf einem Windows Mixed Reality immersive (VR) Kopfhörer einfügen, Sie geben Sie die Windows Mixed Reality home, als ein Haus auf ein enthaltender Alpen und Wasser Cliff visualisiert (obwohl Sie können [andere Umgebungen auswählen, und erstellen Sie eigene](add-custom-home-environments.md)). Innerhalb des Bereichs dieses ist ein Benutzer home, anordnen und Organisieren Sie die 3D-Objekte und apps, die sie beliebig interessieren gewünschten kostenlos. Ein **-3D-app-Startfeld** ist ein "physical"-Objekt in der Benutzer die Realität Haus, die sie auswählen können, um eine app zu starten gemischt.

![Beispiel: Unverankerten Bird-3D-app-Startfeld](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*Unverankerten Bird 3D-Startprogramm-Beispiel-app (fiktive app)*

## <a name="3d-app-launcher-creation-process"></a>3D app-Startprogramm-Erstellungsprozess

Es gibt 3 Schritte zum Erstellen einer-3D-app-Startfeld:
1. Entwerfen und Concepting (dieser Artikel)
2. [Modellieren und exportieren](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Die Integration in Ihre Anwendung:
    * [UWP-Apps](implementing-3d-app-launchers.md)
    * [Win32-apps](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>Entwurfskonzepte

### <a name="fantastic-yet-familiar"></a>Super, aber vertraut

Die Windows Mixed Reality-Umgebung, die Ihre app-Startfeld befindet sich in ist Teil vertraut, Teil fantastischen/SCSI-Fi an. Die beste Startprogramme folgen die Regeln der Welt. Stellen Sie sich wie ein Objekt vertraut, repräsentative aus Ihrer app nutzen können Biegen einige der Regeln der tatsächlichen Realität. Magic-Befehl führt.

### <a name="intuitive"></a>Intuitiv

Wenn Sie Ihre app-Startfeld betrachten, wird dessen Zweck - zum Starten der app - sollte klar sein, und sollte nicht zu Verwirrung führen. Beispielsweise werden Sie sicher, dass Ihre Startprogramm eine offensichtliche hinreichend repräsentativ für Ihre app, dass sie für einen Teil der Decor in das Cliff House verwechselt werden, wird nicht. Ihre app-Startfeld soll Personen Touch/es auswählen einladen.

![Beispiel: Neue Notiz-3D-app-Startfeld](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*Neue Notiz 3D-Startprogramm-Beispiel-app (fiktive app)*

### <a name="home-scale"></a>Home-Skalierung

3D app-startfeldern von befinden sich in der Cliff House und deren Standardgröße sollten Sinn für die anderen "physical" Objekte im Bereich. Wenn Sie Ihre Startprogramm neben, z. B. platzieren, sollte eine Anlage Haus oder einige Möbel, kommt es Ihnen zu Hause, size-wise. Ein guter Ausgangspunkt ist zu sehen, wie es unter 30 kubische Zentimeter aussieht, aber denken Sie daran, dass der Benutzer es nach oben oder unten skaliert werden können, wenn sie z. B.

### <a name="own-able"></a>Besitzer-fähig

Das app-Startfeld sollte wie ein Objekt sein, die eine Person sein, würde gerne in seinem Bereich verfügen. Sie werden praktisch umgebenden werden selbst mit diesen, sodass das Startprogramm wie etwas funktioniert der Gedanke Benutzer war wünschenswert genug ist, lesen, und behalten Sie in der Nähe.

![Beispiel: Astro Warp-3D-app-Startfeld](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*Beispiel für die Astro Warp 3D app-Startprogramm (fiktive app)*

### <a name="recognizable"></a>Erkannt

Ihre 3D app-Startfeld sollte sofort "Ihrer app-Brand" Personen Ausdrücken anzeigen. Wenn Sie ein Stern Zeichen oder ein besonders identifizierbaren Objekt in Ihrer app haben, empfehlen wir, verwenden, wie ein großer Teil des Entwurfs. In einer Welt mixed Reality wird ein Objekt größerem Interesse von Benutzern als nur ein Logo, die allein gezeichnet. Erkennbare Objekten kommunizieren Marke, schnell und deutlich.

### <a name="volumetric"></a>Volumetrische

Ihre app sollte mehr als nur Ihr Logo in eine flache Ebene platzieren und Aufrufen von Feierabend. Ihre Startprogramm sollte wie ein aufregende, 3D, physische Objekt im Bereich für den Benutzer fühlen. Ein guter Ansatz ist vorstellbar, dass Ihre app würde eine Sprechblase in die Macys Thanksgiving-Tag Schlag zu erhalten. Fragen Sie sich, würde wie Personen wirklich wow, wie sie die Straße stammt? Was würde aus allen Winkeln der Anzeige hervorragend aussehen?


:::row:::
    :::column:::
        ![Logo only](images/20171016-140436-mixedreality-640px.jpg)
        *Logo only*
    :::column-end:::
    :::column:::
        ![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg)
        *More recognizable with a character*
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
        ![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg)
        *Flat approach, not surprisingly, feels flat*
    :::column-end:::
    :::column:::
        ![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg)
        *Volumetric approach better showcases your app*
    :::column-end:::
:::row-end:::


## <a name="tips-for-good-3d-models"></a>Tipps für gute 3D-Modelle

### <a name="best-practices"></a>Empfohlene Methoden
* Bei der Planung von Dimensionen für Ihre app-Startfeld Schießen Sie für ungefähr einen 30-cm-Cube ein. Also eine 1: von 1:1-Größenverhältnis.
* Modelle müssen weniger als 10.000 Polygone sein. [Weitere Informationen zum Dreieck Anzahlen und weitere Details (LODs)](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* Testen Sie auf eine immersive Kopfhörer, sofern möglich.
* Details in die Geometrie des Modells zu erstellen, wenn möglich – verlassen Sie sich nicht auf Texturen für Details.
* Erstellen Sie "Kate enge" geschlossen Geometrie. Keine Lücken aufweisen, die nicht im modelliert werden.
* Verwenden Sie natürliche Materialien in Ihr Objekt an. Stellen Sie sich vor, erstellen sie in der realen Welt.
* Stellen Sie sicher, dass das Modell gut bei verschiedenen Abstände und Größen liest.
* Wenn das Modell fertig ist, lesen die [Assets Richtlinien exportieren](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).

![Modell mit den feinen Details in der Textur](images/20171013-143334-mixedreality-640px.jpg)<br>
*Modell mit den feinen Details in der Textur*

### <a name="what-to-avoid"></a>Was Sie vermeiden sollten
* Verwenden Sie keine Details mit hohem Kontrast oder Muster für kleine, ausgelastet und Texturen.
* Verwenden Sie keine thin Geometrie – nicht und funktioniert auch mit einer Entfernung alias ungültig wird.
* Teilen des Modells erweitern lassen nicht zu viel über die 1: von 1:1-Größenverhältnis. Skalierungsproblemen wird erstellt.

![Vermeiden von hohem Kontrast, kleine ausgelastet Muster](images/20171013-143603-mixedreality-640px.jpg)<br>
*Vermeiden von hohem Kontrast, kleine, gebucht Muster*

## <a name="how-to-handle-type"></a>Das Durchführen von Typ

### <a name="best-practices"></a>Empfohlene Methoden
* Es wird empfohlen, dass Ihr Typ ca. 1/3-Ihrer-app-Startfeld (oder mehr) umfasst. Der Typ ist der wichtigste Aspekt besteht, die Benutzer eine Vorstellung, die Ihre Startprogramm tatsächlich ein Startprogramm erhalten ist, daher ist es gut ist dies ganz erhebliche.
* Vermeiden, dass sehr breit Typ – versuchen, die sie innerhalb der Grenzen des app-startfeldern Core Dimensionen (mehr oder weniger) beizubehalten.
* Flatfiles kann funktionieren, aber beachten Sie, dass es zum Anzeigen von bestimmten Winkel und in bestimmten Umgebungen schwierig sein kann. Sie sollten erwägen, platzieren es ein solid Objekt oder eine Backdrop dahinter helfen.
* Hinzufügen von Dimension in den Typ fühlt gut in 3D. Schattierung die Seiten des Typs können eine andere, je dunkler Farbe für die Lesbarkeit.


:::row:::
    :::column:::
        ![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png)
        *Flat type without a backdrop can be hard to view from certain angles and in certain environments*
    :::column-end:::
    :::column:::
        ![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png)
        *Type with a built-in backdrop can work well*
    :::column-end:::
    :::column:::
        ![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg)
        *Extruded type can work well if you shade the sides*
    :::column-end:::
:::row-end:::


**Typ-Farben, die funktionieren**
* Weiß
* Schwarz
* Helle teilweise farbsättigung

![Geben Sie Farben, die funktionieren.](images/20171016-112111-mixedreality-640px.jpg)<br>
*Typ-Farben, die funktionieren*

### <a name="what-to-avoid"></a>Was Sie vermeiden sollten

**Typ-Farben, die Probleme verursachen.**
* Mid-Töne
* Grau
* Übermäßige Sättigung Farben oder entsättigte Farben

![Geben Sie Farben, die Probleme verursachen.](images/20171016-112246-mixedreality-640px.jpg)<br>
*Typ-Farben, die Probleme verursachen.*

## <a name="lighting"></a>Beleuchtung

Die Beleuchtung für Ihre app-Startfeld stammt aus der Cliff House-Umgebung. Achten Sie darauf, um Ihre Startprogramm an mehreren Stellen im gesamten Haus zu testen, damit es in Ordnung ist in Licht und Schatten. Die gute Nachricht ist, Ihre Startprogramm auf ziemlich guten Zustand für die meisten Beleuchtung in der Cliff House sein soll, wenn Sie die anderen Entwurfsrichtlinien, die Sie in diesem Dokument ausgeführt haben, an.

Testen die Darstellung Ihrer Startprogramm in der verschiedenen Lichter in der Umgebung bieten gute Einstiegspunkte sind der Studio Media Raum außerhalb von überall und im Garten zurück (der konkreten Bereich mit den Rasen). Ein weiterer guter Test ist, fügen Sie ihn in die halbe Licht und halbe Schatten und wie es aussieht.

![Stellen Sie sicher, dass Ihre Startprogramm in Licht und Schatten in Ordnung ist.](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*Stellen Sie sicher, dass Ihre Startprogramm in Licht und Schatten in Ordnung ist*

## <a name="texturing"></a>Texturen

### <a name="authoring-your-textures"></a>Erstellen Ihre Texturen

Das End-Format, der Ihre-3D-app-Startfeld werden eine .glb-Datei, die erfolgt über die Pipeline PBR (physisch basierten Rendern). Dies liegt möglicherweise eine komplizierte Prozess – jetzt ein guter Zeitpunkt, einen technischen Interpreten einsetzen, sofern Sie noch nicht geschehen ist. Eine mutig DIY-er haben sich die Zeit nehmen [untersuchen und lernen Sie die PBR Terminologie](http://wiki.polycount.com/wiki/PBR) und was im Hintergrund geschieht, bevor Sie beginnen, können Sie häufige Fehler zu vermeiden. 

![Beispiel: Neue Notiz-app](images/pbr-freshnote1-640px-500px.png)<br>
*Neue Notiz 3D-Startprogramm-Beispiel-app (fiktive app)*

**Empfohlene authoring tool**

Es wird empfohlen, [Substanz übertragen](https://www.allegorithmic.com/products/substance-painter) von Allegorithmic Ihrer endgültige Datei zu erstellen. Wenn Sie nicht mit der Erstellung von PBR-Shader in Substanz übertragen, hier die vertraut sind eine [Tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).

(Alternativ [-3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), oder [Marmoset Toolbag](https://www.marmoset.co/toolbag/) würde auch funktionieren, wenn Sie mehr mit einer dieser vertraut.)

### <a name="best-practices"></a>Empfohlene Methoden

* Wenn Ihre app-Startprogramm-Objekt für PBR erstellt wurde, sollte es ziemlich einfach, für die Umgebung Cliff House konvertieren.
* Unsere Shader-Metal-Computern/Rauigkeit Workflow erwartet – die Unreal PBR Shader ist schließen anzeigte verwenden.
* Beim Exportieren Ihre Texturen behalten die [empfohlene Größen der Textur](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) Bedenken.
* Stellen Sie sicher, dass Sie Ihre Objekte in Echtzeit Beleuchtung erstellen – Dies bedeutet:
    * Vermeiden Sie mitgelieferten Shadows – oder gezeichnete Schatten
    * Vermeiden Sie die mitgelieferten Beleuchtung in die Texturen
    * Verwenden Sie eine der das PBR-Material, das Erstellen von Paketen, um die richtigen Zuordnungen für unseren Shader generiert zu erhalten

## <a name="see-also"></a>Siehe auch

* [Erstellen von 3D-Modellen für die Verwendung in der mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementieren von 3D app-startfeldern von (UWP-apps)](implementing-3d-app-launchers.md)
* [Implementieren von 3D app-startfeldern von (Win32-apps)](implementing-3d-app-launchers-win32.md)
