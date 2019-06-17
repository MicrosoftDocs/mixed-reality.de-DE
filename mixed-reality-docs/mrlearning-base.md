---
title: Einführung in MR-Learning-Basis-Modul
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: d4220527a7de8e596f2825fd9d199d536510b972
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148624"
---
# <a name="mr-learning-base-module-overview--objectives"></a><span data-ttu-id="7a593-104">Modulübersicht MR-Learning-Basis und Ziele</span><span class="sxs-lookup"><span data-stu-id="7a593-104">MR Learning Base Module Overview & Objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="7a593-105">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="7a593-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7a593-106"><strong>Kurs</strong></span><span class="sxs-lookup"><span data-stu-id="7a593-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="7a593-107"><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="7a593-107"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="7a593-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="7a593-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="7a593-109"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="7a593-109"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td><span data-ttu-id="7a593-110">❌</span><span class="sxs-lookup"><span data-stu-id="7a593-110">❌</span></span></td>
        <td><span data-ttu-id="7a593-111">✔️</span><span class="sxs-lookup"><span data-stu-id="7a593-111">✔️</span></span></td>
        <td><span data-ttu-id="7a593-112">❌</span><span class="sxs-lookup"><span data-stu-id="7a593-112">❌</span></span></td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="7a593-113">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="7a593-113">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="7a593-114">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="7a593-114">Prerequisites</span></span>

* <span data-ttu-id="7a593-115">Ein Windows 10-PCs mit dem richtigen konfiguriert [-Tools installiert](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="7a593-115">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="7a593-116">Windows 10 SDK 10.0.18362.0 oder höher</span><span class="sxs-lookup"><span data-stu-id="7a593-116">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="7a593-117">Einige grundlegende C# Programmierkenntnisse.</span><span class="sxs-lookup"><span data-stu-id="7a593-117">Some basic C# programming ability.</span></span>
* <span data-ttu-id="7a593-118">Ein Gerät HoloLens 2 [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="7a593-118">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>
