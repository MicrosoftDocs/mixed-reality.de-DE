---
title: 1. Erste Schritte
description: Teil 1 von 6 einer Tutorialreihe zum Erstellen einer einfachen Schach-App mit der Unreal Engine 4 und dem UX Tools-Plug-In des Mixed Reality-Toolkits
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Tutorial, erste Schritte, MRTK, UXT, UX Tools, Dokumentation
ms.openlocfilehash: 39e4e7218341dcc69eacf01f43b5e0721e76031b
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720376"
---
# <a name="1-getting-started"></a>1. Erste Schritte

Einsteigern in die Welt der Mixed Reality ebenso wie erfahrenen Experten wird hier gleichermaßen der ideale Ausgangspunkt geboten, um [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) und die [Unreal Engine](https://www.unrealengine.com/en-US/) kennenzulernen. In dieser Tutorialreihe erhalten Sie eine ausführliche Anleitung zum Erstellen einer interaktiven Schach-App mit dem [UX Tools-Plug-In](https://github.com/microsoft/MixedReality-UXTools-Unreal), das Teil des [Mixed Reality Toolkit für Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) ist. Das Plug-in unterstützt Sie beim Hinzufügen allgemeiner UX-Features zu Ihren Projekten anhand von Code, Blaupausen und Beispielen. 

![Fertige Szene im Viewport](images/unreal-uxt/5-endscene.PNG)

Am Ende der Reihe haben Sie praktische Erfahrungen mit folgenden Aufgaben gesammelt:
* Erstellen eines neuen Projekts
* Einrichtung für Mixed Reality
* Arbeiten mit Benutzereingaben
* Hinzufügen von Schaltflächen
* Wiedergabe in einem Emulator oder auf einem Gerät

Wenn Sie Fragen haben, finden Sie weitere Informationen unter [Unreal-Entwicklung – Übersicht](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).

## <a name="prerequisites"></a>Voraussetzungen
Vergewissern Sie sich, dass die folgenden Voraussetzungen erfüllt sind, bevor Sie loslegen:
* Windows 10 (1809 oder höher)
* Windows 10 SDK (10.0.18362.0 oder höher)
* [Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 oder höher
* [Für die Entwicklung konfiguriertes](using-visual-studio.md#enabling-developer-mode) Microsoft HoloLens 2-Gerät oder entsprechender Emulator
* Visual Studio 2019 mit den folgenden Workloads

### <a name="installing-visual-studio-2019"></a>Installieren von Visual Studio 2019
Der letzte Schritt ist das Einrichten von Visual Studio:
1. Installieren Sie die aktuelle Version von [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/).
2. Installieren Sie die folgenden [Workloads](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-workloads):
    * Desktopentwicklung mit C++
    * .NET-Desktopentwicklung
    * Entwicklung für die universelle Windows-Plattform

3. Installieren Sie die folgenden [Komponenten](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-individual-components):
    * „Compiler, Buildtools und Runtimes“ > „MSVC v142 – VS 2019 C++-ARM64-Buildtools“ (neueste Version)

Das war's. Jetzt haben Sie alle Vorbereitungen getroffen, um mit dem Schach-App-Projekt beginnen zu können.

[Nächster Abschnitt: 2. Initialisieren des Projekts und der ersten Anwendung](unreal-uxt-ch2.md)