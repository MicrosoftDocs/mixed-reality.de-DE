---
title: Bewährte Methoden für die Arbeit mit Unity und Visual Studio
description: Tipps und Tricks, um den Workflow für die Erstellung einer gemischten Reality-Anwendung mit Unity und Visual Studio zu optimieren.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: bereitstellen, Unity, Visual Studio, hololens, hololens 2, immersives Headset
ms.openlocfilehash: f897c9280505b1e84f8e6342729f1598d4b2f559
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436964"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Bewährte Methoden für die Arbeit mit Unity und Visual Studio

Ein Entwickler, der eine gemischte Reality-Anwendung mit Unity erstellt, muss zwischen Unity und Visual Studio wechseln, um das Anwendungspaket zu erstellen, das in hololens und/oder einem immersiven Headset bereitgestellt wird. Standardmäßig sind zwei Instanzen von Visual Studio erforderlich (eine zum Ändern von Unity-Skripts und eine zum Bereitstellen auf dem Gerät und zum Debuggen). Das folgende Verfahren ermöglicht die Entwicklung mit einer einzelnen Visual Studio-Instanz, verringert die Häufigkeit des Exports von Unity-Projekten und verbessert die debuggingdarstellung.

## <a name="improving-iteration-time"></a>Verbessern der Iterations Zeit

Unterstützung für .NET-Skript-Back-End in Unity wird in Unity 2018 als veraltet markiert und in Unity 2019 und höher entfernt. Daher wird empfohlen, zu [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html)zu wechseln. Dies kann jedoch längere Buildzeiten von Unity zu Visual Studio verursachen. Um eine schnellere Iteration zu verbessern, sollten Sie Ihre Umgebung für optimale Kompilierungs Ergebnisse einrichten.

1) Nutzen Sie das inkrementelle erstellen, indem Sie Ihr Projekt jedes Mal in demselben Verzeichnis erstellen, indem Sie die vorgefertigten Dateien wieder verwenden.
2) Antischadsoftwarescans für Ihr Projekt & Buildordner deaktivieren
   - Öffnen Sie **Viren & Bedrohungsschutz** unter Ihrer Windows 10-Einstellungs-APP.
   - Wählen Sie unter **Viren & Bedrohungsschutz Einstellungen** die Option **Einstellungen verwalten** .
   - Wählen Sie im Abschnitt **Ausschlüsse** die Option **Ausschlüsse hinzufügen oder entfernen**
   - Klicken Sie auf **Ausschluss hinzufügen** , und wählen Sie den Ordner mit Ihrem Unity-Projekt Code und Buildausgaben
3) Verwenden eines SSD zum entwickeln

Weitere Informationen finden Sie im Artikel [zum Optimieren der Buildzeiten für IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) . Lesen Sie auch [Debuggen für IL2CPP-Skript-Back-End](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html).

Außerdem sollten Sie die [Visual Studio-Erweiterung *unityscriptanalyzer* ](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)installieren. Dieses Tool analysiert Ihre Unity C# -Skripts auf Code, der möglicherweise auf optimierte Weise geschrieben werden kann.

## <a name="visual-studio-tools-for-unity"></a>Visual Studio-Tools für Unity

Download [Visual Studio-Tools für Unity](https://docs.microsoft.com/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity?view=vs-2019)

**Vorteile von Visual Studio-Tools für Unity**
* Debuggen Sie den Unity-im-Editor-Wiedergabemodus in Visual Studio, indem Sie Haltepunkte einfügen, Variablen und komplexe Ausdrücke auswerten.
* Verwenden Sie den Unity-Projekt-Explorer, um das Skript mit derselben Hierarchie zu suchen, die in Unity angezeigt wird.
* Holen Sie sich die Unity-Konsole direkt in Visual Studio.
* Mithilfe von Assistenten können Sie schnell Skripts erstellen oder zu ihnen navigieren.

## <a name="expose-c-class-variables-for-easy-tuning"></a>Verfügbar C# machen von Klassen Variablen für die einfache Optimierung

Es gibt zwei Möglichkeiten, Klassen Variablen verfügbar zu machen. Die empfohlene Vorgehensweise besteht darin, das Attribut [serializefield] den privaten Variablen hinzuzufügen. Auf diese Weise können Sie über den Editor darauf zugreifen, werden aber nicht Programm gesteuert bereitgestellt.  Die andere Möglichkeit besteht darin, C# Klassen Variablen öffentlich zu machen, um Sie in der Benutzeroberfläche des Editors verfügbar zu machen. 

Beide Ansätze ermöglichen es, Variablen während der Wiedergabe in-Editor problemlos zu optimieren. Dies ist besonders nützlich für das Optimieren von Interaktions Eigenschaften.

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Neugenerieren von Visual Studio-Projektmappen nach Windows SDK oder Unity-Upgrade

UWP-Visual Studio-Projektmappen, die in die Quell Code Verwaltung eingecheckt werden, können nach dem Upgrade auf eine neue Windows SDK oder Unity-Engine veraltet werden. Sie können dieses Problem nach dem Upgrade beheben, indem Sie eine neue UWP-Lösung aus Unity aufbauen und dann alle Unterschiede in der eingecheckten Lösung zusammenführen.

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>Verwenden von Textformaten zum einfachen Vergleichen von Inhalts Änderungen

Durch das Speichern von Medienobjekten im Textformat wird das Überprüfen von Änderungen der Inhalts Änderung in Visual Studio vereinfacht. Sie können dies in "Edit > Project Settings > Editor" aktivieren, indem Sie den **assetserialisierungsmodus** ändern, um **Text zu erzwingen**. Das Zusammenführen von Text-assetdateiänderungen ist jedoch fehleranfällig und wird nicht empfohlen. Daher sollten Sie in Ihrem Quell Code Verwaltungssystem exklusive binäre Auschecken aktivieren.

## <a name="see-also"></a>Weitere Informationen:
- [Visual Studio-Tools für Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [Optimieren von Buildzeiten für IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [*Unityscriptanalyzer* Visual Studio-Erweiterung](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)