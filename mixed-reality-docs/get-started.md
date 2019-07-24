---
title: Erste Schritte
description: In diesem Leitfaden wird die schnellste Möglichkeit zum Einstieg in die Entwicklung mit gemischter Realität erläutert.
author: mattzmsft
ms.author: mazeller
ms.date: 08/06/2018
ms.topic: article
keywords: Erste Schritte, Grundlagen, hololens, immersives Headset, AR, VR, Unity, Visual Studio, Schnellstart, Vorgehensweise
ms.openlocfilehash: 4277de37ffe4a7ab03f382626452b96bf9157634
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873963"
---
# <a name="get-started"></a>Erste Schritte

Willkommen bei der Welt der Mixed Reality-Entwicklung! Wenn Sie noch nicht mit Mr vertraut sind, ist dieser Leitfaden Ihr Hub, um so schnell wie möglich loslegen zu können. Wir unterstützen Sie dabei, Ihren PC für die Entwicklung einzurichten, Ihre Geräte bereit zu lassen und Tools zu installieren, mit denen der Entwicklungsprozess von Microsoft beschleunigt wird. 

## <a name="intro-to-mixed-reality"></a>Einführung in gemischte Realität

Möglicherweise haben Sie einige Fragen zu den Bedeutung von "Mixed Reality" und deren Beziehung zu "Augmented Reality (AR)" und "Virtual Reality (VR)". Kurz gesagt, die gemischte Realität ist die Mischung aus der physischen Welt mit der digitalen Welt, sodass es sich um ein Spektrum handelt, das alles von der erweiterten Realität abdeckt, bei dem digitale Inhalte in der realen Welt und in der virtuellen Realität platziert werden, in der die reale Welt fast vollständig ist. ersetzt durch den Digital. 

![Beispiel für eine Mixed Reality-APP, die sowohl hololens-als auch immersive-Headsets (VR) unterstützt](images/mr-island.png)<br>
*Mixed Reality-Apps können sowohl hololens-als auch immersive-Headsets (VR) unterstützen.*

Wir haben Windows Mixed Reality als eine einzelne Entwicklungsplattform und eine Reihe von Tools erstellt, die das Spektrum von Mr abdecken können, und wir unterstützen derzeit zwei Gerätetypen, die das gleiche Spektrum abdecken: [Microsoft hololens](https://www.microsoft.com/hololens), das weltweit erste eigenständige Holographic-Headset und [Windows Mixed Reality-immersive Headsets und Motion Controller](https://www.microsoft.com/windows/windows-mixed-reality), die sich mit einem PC für eine leistungsstarke virtuelle Realität verbinden. Weitere Informationen finden Sie unter Was ist [gemischte Realität?] (eine gründlichere Antwort finden Sie im Artikel, wenn Sie interessiert sind.

## <a name="choose-your-development-path"></a>Wählen Sie den Entwicklungspfad aus.

Die einfachste Methode zum Entwickeln einer Mixed Reality-APP ist die Verwendung von [Unity](https://unity3d.com), einem leistungsfähigen und beliebten middlewaretool, das häufig für die Spieleentwicklung verwendet wird. Wenn Sie ein benutzerdefiniertes Modul verwenden möchten, können Sie auch auf [DirectX aufbauen](directx-development-overview.md), aber die meisten Entwickler von Mr verwenden Unity für Ihre Spiele und apps. Mit Unity können Sie eine Mixed Reality-app erstellen, die auf hololens, immersive (VR) Headsets oder beides abzielt!

## <a name="prepare-your-pc-and-devices-for-development"></a>Vorbereiten Ihres PCs und ihrer Geräte für die Entwicklung

Unabhängig davon, ob Sie eine Mixed Reality-App entwickeln, die auf hololens, immersive Headsets (VR) oder beides abzielt, verwenden Sie einen gemeinsamen Satz von Tools und APIs. Außerdem sollten Sie sicherstellen, dass Ihr PC leistungsfähig genug für die Entwicklung ist, die Sie durchführen möchten. 

>[!NOTE]
>Sie finden unsere Empfehlungen in den Entwicklungs-PC-Spezifikationen, unterstützte Versionen der einzelnen Software Tools und relevante Einstellungen oder Konfigurations Hinweise für jede im Artikel [Installieren der Tools](install-the-tools.md) . Lesen Sie diesen Artikel, bevor Sie die folgenden Tools installieren.

Zu installier folgende Tools:
* [Unity](https://store.unity.com/download)
* [Visual Studio (mit Windows 10 SDK)](https://developer.microsoft.com/windows/downloads)
* [Mixed Reality Toolkit für Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)

Außerdem möchten Sie [das Zielgerät in den Entwicklermodus versetzen und Visual Studio für die Bereitstellung von apps auf dem Zielgerät konfigurieren](using-visual-studio.md).

### <a name="a-note-about-the-mixed-reality-toolkit-for-unity"></a>Hinweis zum Mixed Reality Toolkit für Unity

![Mrtk für Unity](images/mrtkandunity.png)<br>

***ICH WEISS, DASS ES MIR GEFÄLLT, WARUM MRTK-UNITY SO ERSTAUNLICH IST, UND ALLES, WAS ES IN:)***

Das Mixed Reality Toolkit ist eine Sammlung von Skripts und Komponenten, die dazu dienen, die Entwicklung von Anwendungen zu beschleunigen, die auf Microsoft hololens und Windows Mixed Reality-Headsets abzielen. Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community zu leisten, während dieser Bereich weiter wächst.

## <a name="start-your-first-mr-project"></a>Starten Sie Ihr erstes Mr-Projekt.

Nachdem Sie Ihren PC und Ihre Geräte eingerichtet haben, können Sie Ihr erstes gemischtes Reality-Projekt in Unity erstellen. Befolgen Sie unsere ersten Mr Academy Course, [Mr Basics 100: In den ersten Schritten](holograms-100.md)mit Unity und schließlich wird ein Cube in einem Mixed Reality-Headset ausgeführt.

![Screenshot eines Cubes in einem Mixed Reality-Unity-Projekt](images/mr-cube.PNG)<br>
*Ihr erstes gemischtes Reality-Projekt in Unity: Hello World!*

## <a name="learn-more-and-get-help"></a>Weitere Informationen und Hilfe

Nachdem Sie Ihr erstes "Mr"-Projekt erfolgreich erstellt haben, sind Sie wahrscheinlich mehr hungrig! Im folgenden finden Sie einige Ressourcen, die Ihnen helfen sollten:
* [Entwicklerdokumentation von Mixed Reality](mixed-reality.md) : Sie sind bereits hier, aber es gibt noch viel mehr zu sehen, einschließlich technischer Dokumentation, Entwurfs Leit Faden, Beispiel Projekte und Fallstudien.
* Lernprogramme für [gemischte Realität](tutorials.md) : Befolgen Sie die Lernprogramme, die sich von der Einrichtung von Projekten bis hin zur Implementierung von Kern Bausteinen in Azure und der Integration von Azure Cloud Services in Ihre Mr-App befassen.
* [Erlernen von Unity](https://unity3d.com/learn) : die Website von Unity bietet Tutorials, Projekte und Live Schulungs Sitzungen für Ersteller in jeder Phase des Lernens.

Sie können auch Hilfe von diesen großartigen Communityressourcen erhalten:
* [Mixed Reality-Entwickler Foren](https://forums.hololens.com/) : das offizielle Forum für Entwickler von Mixed Reality zum Fragen und beantworten von Fragen sowie zum Lesen von Neuigkeiten von Microsoft.
* [Holodevelopers Slack-Channel](https://holodevelopersslack.azurewebsites.net/) : der stabilste und resourvste externe, in der Praxis spezifische Entwickler Kanal. die hier aufgeführten Entwickler sind kompetent und hilfreich.
* [Unity-Foren](https://forum.unity3d.com/) : Offizielle Foren von Unity.
