---
title: 1. Erste Schritte
description: Teil 1 eines Tutorials zum Erstellen einer einfachen Schach-App mit der Unreal Engine 4 und dem UX-Tools-Plug-In des Mixed Reality-Toolkits
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Tutorial, erste Schritte, MRTK, UXT, UX Tools, Dokumentation
ms.openlocfilehash: 3ca47cfe7bb0a733932f3777cc8b531ef9df8e71
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840129"
---
# <a name="1-getting-started"></a><span data-ttu-id="df635-104">1. Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="df635-104">1. Getting started</span></span>

<span data-ttu-id="df635-105">In diesem Tutorial erfahren Sie Schritt für Schritt, wie Sie mit der Unreal Engine 4 eine interaktive HoloLens 2-Schach-App erstellen.</span><span class="sxs-lookup"><span data-stu-id="df635-105">This is a step by step tutorial that will show you how to build an interactive HoloLens 2 chess app using Unreal Engine 4.</span></span> <span data-ttu-id="df635-106">Darüber hinaus erfahren Sie, wie Sie das UX-Tools-Plug-In aus dem Mixed Reality Toolkit für Unreal verwenden, um die Entwicklung zu beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="df635-106">You will also learn how to use the UX Tools plugin from the Mixed Reality Toolkit for Unreal to speed up development.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="df635-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="df635-107">Prerequisites</span></span>

* <span data-ttu-id="df635-108">Windows 10 (1809 oder höher)</span><span class="sxs-lookup"><span data-stu-id="df635-108">Windows 10 1809 or later</span></span>
* <span data-ttu-id="df635-109">Windows 10 SDK (10.0.18362.0 oder höher)</span><span class="sxs-lookup"><span data-stu-id="df635-109">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="df635-110">Unreal Engine (4.25 oder höher)</span><span class="sxs-lookup"><span data-stu-id="df635-110">Unreal Engine 4.25 or later</span></span>
* <span data-ttu-id="df635-111">[Für die Entwicklung konfiguriertes](using-visual-studio.md#enabling-developer-mode) Microsoft HoloLens 2-Gerät oder entsprechender Emulator</span><span class="sxs-lookup"><span data-stu-id="df635-111">Microsoft HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode) or Emulator</span></span>
* <span data-ttu-id="df635-112">Visual Studio 2019 (mit den folgenden Workloads und Komponenten)</span><span class="sxs-lookup"><span data-stu-id="df635-112">Visual Studio 2019 (with below workloads and components)</span></span>

### <a name="installing-visual-studio-2019-workloads-and-components"></a><span data-ttu-id="df635-113">Installieren von Visual Studio 2019, Workloads und Komponenten</span><span class="sxs-lookup"><span data-stu-id="df635-113">Installing Visual Studio 2019, workloads, and components</span></span>
1. <span data-ttu-id="df635-114">Installieren Sie die neueste Version von Visual Studio 2019, oder führen Sie ein entsprechendes Update durch.</span><span class="sxs-lookup"><span data-stu-id="df635-114">Install or and update to the latest version of Visual Studio 2019</span></span>
* [<span data-ttu-id="df635-115">Laden Sie Visual Studio 2019 herunter.</span><span class="sxs-lookup"><span data-stu-id="df635-115">Download Visual Studio 2019</span></span>](https://visualstudio.microsoft.com/downloads/)
2. <span data-ttu-id="df635-116">Installieren Sie die folgenden Workloads:</span><span class="sxs-lookup"><span data-stu-id="df635-116">Install the following workloads:</span></span>
* <span data-ttu-id="df635-117">Desktopentwicklung mit C++</span><span class="sxs-lookup"><span data-stu-id="df635-117">Desktop development with C++</span></span>
* <span data-ttu-id="df635-118">.NET-Desktopentwicklung</span><span class="sxs-lookup"><span data-stu-id="df635-118">.NET desktop development</span></span>
* <span data-ttu-id="df635-119">Entwicklung für die universelle Windows-Plattform</span><span class="sxs-lookup"><span data-stu-id="df635-119">Universal Windows Platform development</span></span>
3. <span data-ttu-id="df635-120">Installieren Sie die folgenden Einzelkomponenten:</span><span class="sxs-lookup"><span data-stu-id="df635-120">Install the following individual components:</span></span>
* <span data-ttu-id="df635-121">„Compiler, Buildtools und Runtimes“ > „MSVC v142 – VS 2019 C++-ARM64-Buildtools“ (neueste Version)</span><span class="sxs-lookup"><span data-stu-id="df635-121">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

[<span data-ttu-id="df635-122">Nächster Abschnitt: 2. Initialisieren des Projekts und der ersten Anwendung</span><span class="sxs-lookup"><span data-stu-id="df635-122">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)