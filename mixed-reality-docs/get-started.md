---
title: Beginnen
description: Dieses Handbuch skizziert die schnellste Möglichkeit, mit der Entwicklung von mixed Reality betriebsbereit zu machen.
author: mattzmsft
ms.author: mazeller
ms.date: 08/06/2018
ms.topic: article
keywords: Erste Schritte, Grundlagen, HoloLens, immersive Kopfhörer, Ar, Vr, Unity, visual Studio, Schnellstart, wie Sie
ms.openlocfilehash: 4277de37ffe4a7ab03f382626452b96bf9157634
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873963"
---
# <a name="get-started"></a>Beginnen

Willkommen Sie auf der ganzen Welt von mixed Reality-Entwicklung! Wenn Sie noch nicht mit MR sind, werden in der vorliegenden Ihren Hub einrichten und so schnell wie möglich ausgeführt. Wir unterstützen Sie Ihre PC-Gruppe für die Entwicklung einzurichten, bereiten Sie Ihre Geräte und Installieren von Tools, die den Entwicklungsprozess MR beschleunigen werden. 

## <a name="intro-to-mixed-reality"></a>Einführung zu mixed reality

Sie müssen möglicherweise einige Fragen darüber, was wir unter "mixed Reality" verstehen, und wie deren Beziehung zu augmented Reality-Modus (AR) und virtuelle Realität (VR). Kurz gesagt, werden mixed Reality die Mischung der realen Welt mit der digitalen Welt leben, daher wird ein Spektrum, die von augmented Reality-Modus, ist alles abgedeckt wird digitaler Inhalte in der realen Welt, um virtuelle Realität platziert, in denen die reale Welt fast vollständig ist durch die digitale ersetzt. 

![Beispiel für ein mixed Reality-app, die HoloLens und immersive Headsets von (VR) unterstützt](images/mr-island.png)<br>
*Mixed Reality-apps können sowohl HoloLens auch immersive Headsets von (VR) unterstützen.*

Wir haben Windows Mixed Reality erstellt, als eine einzelne Entwicklungsplattform und eine Reihe von Tools, die das MR Spektrum abdecken können, und wir unterstützen derzeit zwei Gerätetypen, die die gleiche Spektrum abdecken: [Microsoft HoloLens](https://www.microsoft.com/hololens), weltweit erste eigenständige holographic Kopfhörer, und [immersive Headsets Windows Mixed Reality und der Motion-Controllern](https://www.microsoft.com/windows/windows-mixed-reality), die auf einem PC verbinden, leistungsstarke virtuelle Realität-Funktionen zu nutzen. Sehen Sie sich unsere Was ist [mixed Reality?] (finden Sie eine ausführlichere Antwort, wenn Sie sich interessieren.

## <a name="choose-your-development-path"></a>Wählen Sie den Entwicklungspfad

Die einfachste Möglichkeit zum Entwickeln einer mixed Reality-app verwendet den [Unity](https://unity3d.com), eine leistungsstarke und beliebte Middleware-Tool, das häufig für die Entwicklung von Spielen verwendet. Wenn Sie eine benutzerdefinierte Engine verwenden möchten, können Sie auch [für DirectX erstellen](directx-development-overview.md), aber die meisten MR-Entwickler verwenden Unity für ihre Spiele und apps. Mit Unity werden Sie möglicherweise eine mixed Reality-app zu erstellen, die Ziel von HoloLens, immersive Headsets von (VR) oder beides!

## <a name="prepare-your-pc-and-devices-for-development"></a>Bereiten Sie Ihre PCs und Geräten für die Entwicklung

Egal ob Sie eine mixed Reality-app, die HoloLens, immersive Headsets von (VR) oder beides ausgerichtet ist erstellen, müssen Sie einen gemeinsamen Satz von Tools und APIs verwenden. Sie sollten auch sicherstellen, dass Ihr PC leistungsfähig genug ist, für die Entwicklung ist, die Sie durchführen müssen. 

>[!NOTE]
>Finden Sie unseren Empfehlungen auf Entwicklungs-PC-Spezifikationen, unterstützte Versionen der einzelnen Softwaretools und die relevanten Einstellungen oder Konfiguration Anmerkungen dieser für jede in der [Installieren der Tools](install-the-tools.md) Artikel. Überprüfen Sie diesen Artikel vor der Installation die folgenden Tools.

Tools zum installieren:
* [Unity](https://store.unity.com/download)
* [Visual Studio (mit Windows 10 SDK)](https://developer.microsoft.com/windows/downloads)
* [Mixed Reality-Toolkit für Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)

Sie sollten auch [Entwicklermodus Ihr Zielgerät abgelegt, und Konfigurieren von Visual Studio zum Bereitstellen von apps auf dem Zielgerät](using-visual-studio.md).

### <a name="a-note-about-the-mixed-reality-toolkit-for-unity"></a>Ein Hinweis zum Mixed Reality-Toolkit für Unity

![MRTK für Unity](images/mrtkandunity.png)<br>

***AN DEM SIE AUSZUARBEITEN DIESER OUT UND ERZÄHLEN SIE UNS AN, WARUM MRTK-UNITY IST SO EINDRUCKSVOLLE WEISE UND ALL DIE COOLEN DINGE IN :)***

Das Mixed Reality-Toolkit ist eine Sammlung von Skripts, und Komponenten, die zum Beschleunigen der Entwicklung von Anwendungen für Microsoft HoloLens und Windows Mixed Reality-Headsets Verwendung vorgesehen. Das Projekt zielt auf die Reduzierung von Sperren auf einen Eintrag in mixed Reality-Anwendungen zu erstellen und an der Community beitragen, wenn wir alle wachsen.

## <a name="start-your-first-mr-project"></a>Starten Sie Ihr erste MR-Projekt

Nun, Ihren PC und Geräte eingerichtet werden, können Sie Ihr erstes mixed Reality-Projekt in Unity zu erstellen. Nutzen Sie unsere erste MR Academy-Kurs [MR Grundlagen 100: Erste Schritte mit Unity](holograms-100.md), am Ende verfügen Sie über einen Cube auf eine Kopfhörer mixed Reality.

![Screenshot eines Cubes in einem Unity-Projekt für mixed reality](images/mr-cube.PNG)<br>
*Ihr erstes mixed Reality-Projekt im Unity - Hello World!*

## <a name="learn-more-and-get-help"></a>Weitere Informationen und Hilfe

Nachdem Sie Ihr erste MR-Projekt erfolgreich erstellt haben, können Sie wahrscheinlich viel mehr! Hier sind einige Ressourcen, die dabei helfen soll:
* [Mixed Reality-Entwicklerdokumentation](mixed-reality.md) – Sie sind bereits hier, aber es gibt noch viele weitere Auschecken, einschließlich technischer Dokumentation, Leitfaden zum Entwerfen, Beispielprojekte und Fallstudien.
* [Mixed Reality-Tutorials](tutorials.md) – nutzen Sie Lernprogramme, die alles von Projekten, für die Implementierung der wichtigsten Bausteine für MR einrichten, um die Integration von Azure-Clouddienste in Ihre app MR.
* [Erfahren Sie, Unity](https://unity3d.com/learn) – der Unity-Website bietet Lernprogramme, Projekte und live-Schulungen für Entwickler in jeder Phase des Lernens.

Sie können auch die Unterstützung von diesen große Community-Ressourcen erhalten:
* [Mixed Reality-Entwicklerforen](https://forums.hololens.com/) – das offizielle-Forum für mixed Reality-Entwickler zu stellen und beantworten Sie Fragen, als auch MR Entwicklungsnachrichten direkt von Microsoft lesen.
* [HoloDevelopers Slack-Kanal](https://holodevelopersslack.azurewebsites.net/) -die stabile und findigen Unternehmen externe mixed Reality-spezifische Developer Channel, der Entwickler hier kompetenten und hilfreich.
* [Unity-Foren](https://forum.unity3d.com/) – offiziellen von Unity-Foren.
