---
title: 1. Erste Schritte
description: Teil 1 von 6 einer Tutorialreihe zum Erstellen einer einfachen Schach-App mit der Unreal Engine 4 und dem UX Tools-Plug-In des Mixed Reality-Toolkits
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Tutorial, erste Schritte, MRTK, UXT, UX Tools, Dokumentation
ms.openlocfilehash: c16671fc8f4233378dafa646786df1f7b5ae18e1
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330167"
---
# <a name="1-getting-started"></a><span data-ttu-id="5c46d-104">1. Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="5c46d-104">1. Getting started</span></span>

<span data-ttu-id="5c46d-105">Einsteigern in die Welt der Mixed Reality ebenso wie erfahrenen Experten wird hier gleichermaßen der ideale Ausgangspunkt geboten, um [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) und die [Unreal Engine](https://www.unrealengine.com/en-US/) kennenzulernen.</span><span class="sxs-lookup"><span data-stu-id="5c46d-105">Whether you're new to mixed reality or a seasoned pro, this is the place to start your journey with [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) and [Unreal Engine](https://www.unrealengine.com/en-US/).</span></span> <span data-ttu-id="5c46d-106">In dieser Tutorialreihe erhalten Sie eine ausführliche Anleitung zum Erstellen einer interaktiven Schach-App mit dem [UX Tools-Plug-In](https://github.com/microsoft/MixedReality-UXTools-Unreal), das Teil des [Mixed Reality Toolkit für Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) ist.</span><span class="sxs-lookup"><span data-stu-id="5c46d-106">This tutorial series will give you a step by step guide on how to build an interactive chess app with the [UX Tools plugin](https://github.com/microsoft/MixedReality-UXTools-Unreal) - part of the [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span></span> <span data-ttu-id="5c46d-107">Das Plug-in unterstützt Sie beim Hinzufügen allgemeiner UX-Features zu Ihren Projekten anhand von Code, Blaupausen und Beispielen.</span><span class="sxs-lookup"><span data-stu-id="5c46d-107">The plugin will help you add common UX features to your projects with code, blueprints, and examples.</span></span> 

![Fertige Szene im Viewport](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="5c46d-109">Am Ende der Reihe haben Sie praktische Erfahrungen mit folgenden Aufgaben gesammelt:</span><span class="sxs-lookup"><span data-stu-id="5c46d-109">By the end of the series you'll have hands-on experience with:</span></span>
* <span data-ttu-id="5c46d-110">Erstellen eines neuen Projekts</span><span class="sxs-lookup"><span data-stu-id="5c46d-110">Starting a new project</span></span>
* <span data-ttu-id="5c46d-111">Einrichtung für Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="5c46d-111">Setting up for mixed reality</span></span>
* <span data-ttu-id="5c46d-112">Arbeiten mit Benutzereingaben</span><span class="sxs-lookup"><span data-stu-id="5c46d-112">Working with user input</span></span>
* <span data-ttu-id="5c46d-113">Hinzufügen von Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="5c46d-113">Adding buttons</span></span>
* <span data-ttu-id="5c46d-114">Wiedergabe in einem Emulator oder auf einem Gerät</span><span class="sxs-lookup"><span data-stu-id="5c46d-114">Playing on an emulator or device</span></span>

<span data-ttu-id="5c46d-115">Wenn Sie Fragen haben, finden Sie weitere Informationen unter [Unreal-Entwicklung – Übersicht](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span><span class="sxs-lookup"><span data-stu-id="5c46d-115">If you have any questions, check out our [Unreal development overview](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5c46d-116">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="5c46d-116">Prerequisites</span></span>
<span data-ttu-id="5c46d-117">Vergewissern Sie sich, dass die folgenden Voraussetzungen erfüllt sind, bevor Sie loslegen:</span><span class="sxs-lookup"><span data-stu-id="5c46d-117">Make sure you've met the following requirements before jumping in:</span></span>
* <span data-ttu-id="5c46d-118">Windows 10 (1809 oder höher)</span><span class="sxs-lookup"><span data-stu-id="5c46d-118">Windows 10 1809 or later</span></span>
* <span data-ttu-id="5c46d-119">Windows 10 SDK (10.0.18362.0 oder höher)</span><span class="sxs-lookup"><span data-stu-id="5c46d-119">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="5c46d-120">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 oder höher</span><span class="sxs-lookup"><span data-stu-id="5c46d-120">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 or later</span></span>
* <span data-ttu-id="5c46d-121">[Für die Entwicklung konfiguriertes](using-visual-studio.md#enabling-developer-mode) Microsoft HoloLens 2-Gerät oder entsprechender Emulator</span><span class="sxs-lookup"><span data-stu-id="5c46d-121">Microsoft HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode) or Emulator</span></span>
* <span data-ttu-id="5c46d-122">Visual Studio 2019 mit den folgenden Workloads</span><span class="sxs-lookup"><span data-stu-id="5c46d-122">Visual Studio 2019 with the workloads below</span></span>

### <a name="installing-visual-studio-2019"></a><span data-ttu-id="5c46d-123">Installieren von Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="5c46d-123">Installing Visual Studio 2019</span></span>
<span data-ttu-id="5c46d-124">Der letzte Schritt ist das Einrichten von Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="5c46d-124">The last step is to setup Visual Studio as follows:</span></span>
1. <span data-ttu-id="5c46d-125">Installieren Sie die aktuelle Version von [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/).</span><span class="sxs-lookup"><span data-stu-id="5c46d-125">Install the latest version of [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span></span>
2. <span data-ttu-id="5c46d-126">Installieren Sie die folgenden [Workloads](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-workloads):</span><span class="sxs-lookup"><span data-stu-id="5c46d-126">Install the following [workloads](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-workloads):</span></span>
    * <span data-ttu-id="5c46d-127">Desktopentwicklung mit C++</span><span class="sxs-lookup"><span data-stu-id="5c46d-127">Desktop development with C++</span></span>
    * <span data-ttu-id="5c46d-128">.NET-Desktopentwicklung</span><span class="sxs-lookup"><span data-stu-id="5c46d-128">.NET desktop development</span></span>
    * <span data-ttu-id="5c46d-129">Entwicklung für die universelle Windows-Plattform</span><span class="sxs-lookup"><span data-stu-id="5c46d-129">Universal Windows Platform development</span></span>

3. <span data-ttu-id="5c46d-130">Installieren Sie die folgenden [Komponenten](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-individual-components):</span><span class="sxs-lookup"><span data-stu-id="5c46d-130">Install the following [components](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?view=vs-2019#modify-individual-components):</span></span>
    * <span data-ttu-id="5c46d-131">„Compiler, Buildtools und Runtimes“ > „MSVC v142 – VS 2019 C++-ARM64-Buildtools“ (neueste Version)</span><span class="sxs-lookup"><span data-stu-id="5c46d-131">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

<span data-ttu-id="5c46d-132">Das war's.</span><span class="sxs-lookup"><span data-stu-id="5c46d-132">That's it!</span></span> <span data-ttu-id="5c46d-133">Jetzt haben Sie alle Vorbereitungen getroffen, um mit dem Schach-App-Projekt beginnen zu können.</span><span class="sxs-lookup"><span data-stu-id="5c46d-133">You're all set to move on to starting the chess app project.</span></span>

[<span data-ttu-id="5c46d-134">Nächster Abschnitt: 2. Initialisieren des Projekts und der ersten Anwendung</span><span class="sxs-lookup"><span data-stu-id="5c46d-134">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)