---
title: Bewährte Methoden für die Arbeit mit Unity und Visual Studio
description: Tipps und tricks zum Erstellen einer mixed Reality-Anwendung mit Unity und Visual Studio den Workflow zu optimieren.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Bereitstellen Sie, Unity und visual Studio, HoloLens, immersive Kopfhörer
ms.openlocfilehash: 80a533851b3bee0d747a90dfececbaa558c4ec1f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596687"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Bewährte Methoden für die Arbeit mit Unity und Visual Studio

Ein Entwickler, die Erstellung einer mixed Reality-Anwendung mit Unity müssen Wechseln zwischen Unity und Visual Studio, um das Anwendungspaket zu erstellen, das HoloLens bzw. eine immersive Kopfhörer bereitgestellt wird. Standardmäßig sind zwei Instanzen von Visual Studio erforderlich sind (eine so ändern Sie die Unity-Skripts) und eine für die Bereitstellung auf dem Gerät und dem Debuggen. Das folgende Verfahren ermöglicht die Entwicklung mit Visual Studio-Einzelinstanz, verringert die Häufigkeit der Unity-Projekte exportieren und verbessert die Debugleistung.

## <a name="improving-iteration-time"></a>Verbessern der Iteration Zeit

Ein häufiges Problem der Workflow bei der Arbeit mit Unity und Visual Studio hat mehrere Fenster von Visual Studio öffnen und die Notwendigkeit, Sie ständig zwischen Visual Studio und Unity durchlaufen zu wechseln.
1. **Unity** : zum Ändern der Szene, und Exportieren von Visual Studio-Projektmappe
2. **Visual Studio (1)** : zum Ändern von Skripts
3. **Visual Studio (2)** : für die Erstellung und Bereitstellung von Unity Visual Studio-Projektmappe auf dem Gerät exportieren.

Glücklicherweise ist es eine Möglichkeit, auf eine einzelne Instanz von Visual Studio optimieren und verkürzen sich auf häufige Exporte aus Unity.

Wenn [exportieren das Projekt aus Unity](exporting-and-building-a-unity-visual-studio-solution.md), überprüfen Sie die **Unity C# Projekte** Kontrollkästchen im Menü "Datei > Buildeinstellungen". Nun, das Sie von Unity exportieren-Projekt enthält alle Ihres Projekts C# -Skripts und hat mehrere Vorteile:
* Verwenden Sie dieselbe Instanz von Visual Studio für das Schreiben von Skripts, und erstellen/Bereitstellen Ihres Projekts
* Exportieren von Unity nur, wenn die Szene in der Unity-Editor geändert wird; ändern den Inhalt des Skripts kann in Visual Studio ohne erneut zu exportieren, durchgeführt werden.

Mit **Unity C# Projekte** aktiviert ist, muss nur eine Instanz jedes Programms geöffnet werden:
1. **Unity** : zum Ändern der Szene, und Exportieren von Visual Studio-Projektmappe
2. **Visual Studio** Skripts ändern, und klicken Sie dann die Erstellung und Bereitstellung von Unity Visual Studio-Projektmappe auf dem Gerät exportiert:

## <a name="visual-studio-tools-for-unity"></a>Visual Studio-Tools für Unity

Herunterladen [Visual Studio-Tools für Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)

**Vorteile von Visual Studio-Tools für Unity**
* Debuggen Sie Unity im Editor Spielmodus aus Visual Studio durch Einfügen von Haltepunkten, Auswerten von Variablen und komplexe Ausdrücke aus.
* Verwenden Sie im Unity-Projekt-Explorer, um Ihr Skript mit dem genau gleichen Hierarchie zu suchen, in der Unity angezeigt.
* Die Unity-Konsole direkt in Visual Studio zu erhalten.
* Verwenden Sie Assistenten zum Erstellen, oder navigieren Sie zu Skripts.

## <a name="expose-c-class-variables-for-easy-tuning"></a>Verfügbar machen C# Klasse Sie Variablen für die einfache Optimierung

Es gibt zwei Möglichkeiten, Klassenvariablen verfügbar zu machen. Die empfohlene Methode dazu ist das Attribut [SerializeField] Ihre private Variablen hinzu. Dadurch können sie aus dem Editor zugegriffen werden, aber nicht programmgesteuert verfügbar gemacht werden.  Die andere Möglichkeit ist, C# -Klasse Variablen öffentlich, um sie in der Benutzeroberfläche des seiteneditors verfügbar zu machen. 

Beide Ansätze können ganz einfach Variablen während der Wiedergabe im Editor optimieren. Dies ist besonders nützlich für die Interaktion Mechanic Optimierungseigenschaften.

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Generieren Sie UWP Visual Studio-Projektmappen ein, nach dem upgrade von Windows SDK oder Unity

Visual Studio für UWP-Lösungen, die die quellcodeverwaltung eingecheckt können veraltete abrufen, nach dem Upgrade auf eine neue Windows-SDK oder Unity-Engine. Sie können dies nach dem Upgrade beheben, erstellen eine neue Lösung für die UWP aus Unity und anschließend alle Unterschiede in der Projektmappe eingecheckt zusammenführen.

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>Verwenden Sie zum einfachen Vergleich von inhaltsänderungen in Textformat Ressourcen

Speichern von Ressourcen im Text-Format erleichtert es, inhaltsänderung Unterschiede in Visual Studio zu überprüfen. Sie können diese in "Bearbeiten > Einstellungen > Projekteditors" aktivieren, indem Sie ändern **Asset Serialisierung** Modus **Erzwingen von Text**. Allerdings das Zusammenführen der dateiänderungen für Text-Asset ist fehleranfällig und nicht zu empfehlen, daher sollten Sie exklusive binäre Auschecken in Ihrem Quellcodeverwaltungssystem zu aktivieren.
