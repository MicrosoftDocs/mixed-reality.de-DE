---
title: Asset-Erstellungs Prozess
description: Leitfaden zum Erstellen von Assets für gemischte Realität.
author: paseb
ms.author: paseb
ms.date: 03/21/2018
ms.topic: article
keywords: Asset, Erstellung, Prozess, Budget, Polygone, Texturen, Shader, Leistung
ms.openlocfilehash: 513a9856ac35e4229cfb7bc8bcb92d9d6a152980
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692301"
---
# <a name="asset-creation-process"></a>Asset-Erstellungs Prozess

Windows Mixed Reality baut auf den jahrzehntelangen Investitionen auf, die Microsoft in DirectX getätigt hat. Dies bedeutet, dass alle Erfahrung und Fähigkeiten, die Entwickler bei der Entwicklung von 3D-Grafiken haben, bei hololens weiterhin wertvoll sind.

Die Assets, die Sie für ein Projekt erstellen, sind in vielen Formen und Formularen enthalten. Sie können aus einer Reihe von Texturen/Bildern, Audiodaten, Videos, 3D-Modellen und Animationen bestehen. Wir können nicht alle Tools abdecken, die verfügbar sind, um die verschiedenen Typen von Assets zu erstellen, die in einem Projekt verwendet werden. In diesem Artikel konzentrieren wir uns auf die Methoden zum Erstellen von 3D-Assets.

![Konzept, Erstellung, Integration und Iterations Fluss](images/concept-creation-integration-iteration-flow-640px.jpg)<br>
*Konzept, Erstellung, Integration und Iterations Fluss*

## <a name="things-to-consider"></a>Zu berücksichtigende Informationen

Wenn Sie sich den Eindruck verschaffen, dass Sie sich als **Budget** vorstellen, können Sie es für die Erstellung der besten Leistung aufwenden. Es gibt nicht notwendigerweise Feste Grenzwerte für die Anzahl von **Polygonen** oder **Materialtypen** , die in ihren Assets verwendet werden, sondern eher einen Budget Satz von vor-und Nachteile.

Im folgenden finden Sie ein Beispiel Budget für Ihre Benutzer. Die Leistung ist in der Regel keine Single Point of Failure, aber der Tod durch eine Tausendfache Kürzung pro SE.
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><b>Werten</b></th><th style="text-align:right;"> CPU</th><th> GPU</th><th> Arbeitsspeicher</th>
</tr><tr>
<td> Polygone</td><td> 1,0</td><td> 5%</td><td> 10 %</td>
</tr><tr>
<td> Texturen</td><td> 5%</td><td> 17.15</td><td>25%</td>
</tr><tr>
<td> Shader</td><td> 17.15</td><td> 35 %</td><td> 1,0</td>
</tr><tr>
<td> <b>Dynamics</b></td><td></td><td></td><td></td>
</tr><tr>
<td> Mikro</td><td> 5%</td><td> 17.15</td><td> 1,0</td>
</tr><tr>
<td> Echtzeitbeleuchtung</td><td> 10 %</td><td> 1,0</td><td> 1,0</td>
</tr><tr>
<td> Medien (Audiodatei/Video)</td><td> -</td><td> 17.15</td><td> 25%</td>
</tr><tr>
<td> Skript/Logik</td><td> 25%</td><td> 1,0</td><td> 5%</td>
</tr><tr>
<td> Allgemeiner Verwaltungsaufwand</td><td> 5%</td><td> 5%</td><td> 5%</td>
</tr><tr>
<td> <b>Totales</b></td><td> <b>65%</b></td><td> <b>90%</b></td><td> <b>70%</b></td>
</tr>
</table>

**Gesamtanzahl von Assets**
* Wie viele Assets sind in der Szene aktiv?

**Komplexität von Assets**
* Wie viele Dreiecke/Polygone?
* Wie komplex ist der Shader?

Sowohl Entwickler als auch Künstler müssen die Funktionen des Geräts und der Grafik-Engine in Erwägung gezogen werden. Microsoft hololens verfügt über alle in das Gerät integrierten Berechnungs-und Grafikdaten. Es gibt die Funktionen, die Entwickler auf einer mobilen Plattform finden.

Der Erstellungs Vorgang für Assets ist gleich, unabhängig davon, ob Sie für ein [holografisches Gerät oder ein immersives Gerät](mixed-reality.md#the-mixed-reality-spectrum)als Ziel verwenden. Der wichtigste Aspekt ist die oben erwähnte Geräte Funktion und die Skalierung, da Sie die reale Welt in gemischter Realität sehen können, wenn Sie die richtige Skalierung basierend auf der Umgebung beibehalten möchten. 

## <a name="authoring-assets"></a>Erstellen von Assets

Wir beginnen mit den Möglichkeiten, Ressourcen für Ihr Projekt zu erhalten:
1. Erstellen von Assets (Authoring Tools und Objekt Erfassung)
2. Erwerben von Assets (erwerben von Assets Online)
3. Portieren von Assets (vorhandene Objekte werden übernommen)
4. Auslagerung von Assets (Importieren von Assets von Drittanbietern)

### <a name="creating-assets"></a>Erstellen von Assets

**Authoring Tools**<br>
Zuerst können Sie Ihre eigenen Assets auf verschiedene Weise erstellen. 3D-Künstler verwenden eine Reihe von Anwendungen und Tools, um Modelle zu erstellen, die aus **Netzen**, **Texturen**und **Materialien**bestehen. Diese werden dann in einem Dateiformat gespeichert, das von der von der APP verwendeten Grafik-Engine importiert oder verwendet werden kann, z **. b. Oder** **. Obj**. Jedes Tool, das ein Modell generiert, das von der ausgewählten Grafik-Engine unterstützt wird, funktioniert in **hololens**. Bei 3D-Künstlern entscheiden sich viele für die Verwendung [von Autodesk Maya, die wiederum hololens](https://www.youtube.com/watch?v=q0K3n0Gf8mA) zum Transformieren der Art und Weise der Erstellung von Assets verwenden können. Wenn Sie etwas schneller erhalten möchten, können Sie auch [3D-](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) Generator verwenden, der in Windows zum Exportieren verfügbar ist. Obj für die Verwendung in Ihrer Anwendung.

**Objekt Erfassung**<br>
Außerdem ist die Option zum Erfassen von Objekten in 3D verfügbar. Die Erfassung von inanimieren-Objekten in 3D und deren Bearbeitung mit Software zur Erstellung digitaler Inhalte ist immer beliebter, wenn 3D-Druck entsteht. Mithilfe des **kinect 2** -Sensors und des [3D-](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) Generators können Sie mit der Capture-Funktion Ressourcen aus realen Objekten erstellen. Dabei handelt es sich um eine [Suite von Tools](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) , mit denen Sie die gleichen Schritte durchführen können **, indem Sie** eine Reihe von Bildern zum Zusammenführen und Mesh und Texturen verarbeiten.

### <a name="purchasing-assets"></a>Erwerben von Assets

Eine weitere hervorragende Möglichkeit besteht darin, Ressourcen für Ihre Benutzer zu erwerben. Es gibt eine Menge von Ressourcen, die über Dienste wie z. b. den Unity-Ressourcen [Speicher](https://www.assetstore.unity3d.com/) oder den [TurboSquid](http://www.turbosquid.com/) unter anderen angeboten werden.

Wenn Sie Assets von einem Drittanbieter erwerben, sollten Sie immer Folgendes überprüfen:
* **Was ist die Anzahl der polyds?**
  * Passt Sie in Ihr Budget?
* **Gibt es Detailstufen (LODs) für das Modell?**
  * Die Detailstufe eines Modells ermöglicht es Ihnen, die Details eines Modells für die Leistung zu skalieren.
* **Ist die Quelldatei verfügbar?**
  * Normalerweise nicht im [Unity-Asset-Speicher](https://www.assetstore.unity3d.com/) enthalten, aber immer in Diensten wie [Turbo squid](http://www.turbosquid.com/)enthalten.
  * Ohne die Quelldatei können Sie das Medienobjekt nicht ändern.
  * Stellen Sie sicher, dass die angegebene Quelldatei von ihren 3D-Tools importiert werden kann.
* **Wissen Sie, was Sie erhalten**
  * Werden Animationen bereitgestellt?
  * Stellen Sie sicher, dass Sie die Inhaltsliste des Assets, das Sie kaufen, überprüfen.

### <a name="porting-assets"></a>Portieren von Assets

In einigen Fällen werden Sie vorhandene Assets übergeben, die ursprünglich für andere Geräte und verschiedene apps erstellt wurden. In den meisten Fällen können diese Assets in Formate konvertiert werden, die mit der Grafik-Engine kompatibel sind, die von Ihrer APP verwendet wird.

Beim Portieren von Medienobjekten, die in der hololens-Anwendung verwendet werden sollen, sollten Sie Folgendes anfordern:
* **Können Sie direkt importieren oder müssen in ein anderes Format konvertiert werden?** Überprüfen Sie das Format, das Sie mit der Grafik-Engine importieren, die Sie verwenden.
* **Wenn die Umstellung in ein kompatibles Format etwas verlorengeht?** Manchmal können Details verloren gehen oder das Importieren von Artefakten bewirken, die in einem 3D-Authoring Tool bereinigt werden müssen.
* **Was ist die Anzahl der Dreiecke/Polygone für das Asset?** Basierend auf dem Budget für Ihre Anwendung können Sie [Simplygon](https://www.simplygon.com/) oder ähnliche Tools verwenden, um das ursprüngliche Asset zu dezimieren, das in das Budget Ihrer Anwendungen passt.

### <a name="outsourcing-assets"></a>Outsourcing von Assets

Eine weitere Option für größere Projekte, die mehr Ressourcen benötigen, als Ihr Team zur Erstellung benötigt, besteht darin, die Medienobjekt Erstellung auszulagern. Der Prozess des Outsourcing umfasst das Auffinden der richtigen Studio-oder Agentur, die auf das Outsourcing von Assets spezialisiert ist. Dies kann die aufwendigste Option sein, Sie ist jedoch auch die flexibelste Option, die Sie erhalten.
* **Definieren Sie eindeutig das, was Sie anfordern.**
  * Geben Sie so viele Details wie möglich an.
  * Bilder des Front-, Side-und Back-Konzepts
  * Referenz Kunst mit Asset im Kontext
  * Skalierung des Objekts (normalerweise in Zentimetern angegeben)
* **Budget bereitstellen**
  * Bereich für die polyzahl
  * Anzahl von Texturen
  * Typ des Shader (für Unity und hololens sollten Sie zuerst standardmäßig Mobile Shader einsetzen)
* **Verstehen der Kosten**
  * Was ist die Richtlinie für die Auslagerung von Änderungsanforderungen?

Das Outsourcing funktioniert auf Grundlage ihrer Projekt Zeitachse hervorragend, erfordert jedoch mehr Kontrolle, um sicherzustellen, dass Sie die richtigen Ressourcen erhalten, die Sie zum ersten Mal benötigen.
