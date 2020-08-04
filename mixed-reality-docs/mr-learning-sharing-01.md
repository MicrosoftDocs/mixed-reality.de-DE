---
title: 'Tutorials zu Mehrbenutzerfunktionen: 1 Einführung'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: ebdef9818aace28b32e91384cd9d3278da2733b4
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376342"
---
# <a name="1-introduction"></a><span data-ttu-id="1ed43-105">1. Einführung</span><span class="sxs-lookup"><span data-stu-id="1ed43-105">1. Introduction</span></span>

## <a name="overview"></a><span data-ttu-id="1ed43-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="1ed43-106">Overview</span></span>

<span data-ttu-id="1ed43-107">Willkommen bei den Tutorials zu Mehrbenutzerfunktionen!</span><span class="sxs-lookup"><span data-stu-id="1ed43-107">Welcome to the Multi-User Capabilities tutorials!</span></span> <span data-ttu-id="1ed43-108">In dieser Tutorialreihe erlernen Sie die Grundlagen zum Entwickeln einer Mehrbenutzerumgebung mithilfe von <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN).</span><span class="sxs-lookup"><span data-stu-id="1ed43-108">Through this tutorial series, you will learn the fundamentals of building a multi-user experience using <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN).</span></span> <span data-ttu-id="1ed43-109">PUN ist eine von mehreren Netzwerkoptionen, die Mixed Reality-Entwicklern zum Erstellen gemeinsamer Benutzererfahrungen zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="1ed43-109">PUN is one of several networking options available to mixed reality developers to create shared experiences.</span></span>

<span data-ttu-id="1ed43-110">Tutorials in dieser Reihe:</span><span class="sxs-lookup"><span data-stu-id="1ed43-110">Tutorials in this series:</span></span>

* [<span data-ttu-id="1ed43-111">Einrichten von Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="1ed43-111">Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
* [<span data-ttu-id="1ed43-112">Verbinden mehrerer Benutzer</span><span class="sxs-lookup"><span data-stu-id="1ed43-112">Connecting multiple users</span></span>](mr-learning-sharing-03.md)
* [<span data-ttu-id="1ed43-113">Freigeben von Objektbewegungen für mehrere Benutzer</span><span class="sxs-lookup"><span data-stu-id="1ed43-113">Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
* [<span data-ttu-id="1ed43-114">Integrieren von Azure Spatial Anchors in eine gemeinsam genutzte Umgebung</span><span class="sxs-lookup"><span data-stu-id="1ed43-114">Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)

## <a name="objectives"></a><span data-ttu-id="1ed43-115">Ziele</span><span class="sxs-lookup"><span data-stu-id="1ed43-115">Objectives</span></span>

* <span data-ttu-id="1ed43-116">Erfahren, wie PUN-App erstellt und eine Verbindung Ihres Unity-Projekts mit ihr hergestellt wird</span><span class="sxs-lookup"><span data-stu-id="1ed43-116">Learn how to create a PUN app and connect your Unity project to it</span></span>
* <span data-ttu-id="1ed43-117">Erlernen des Verbindens mehrerer Benutzer in einer freigegebenen Umgebung</span><span class="sxs-lookup"><span data-stu-id="1ed43-117">Learn how to connect multiple users in a shared experience</span></span>
* <span data-ttu-id="1ed43-118">Erfahren, wie Objektbewegungen mit anderen Benutzern geteilt werden können</span><span class="sxs-lookup"><span data-stu-id="1ed43-118">Learn how to share the object movements with other users</span></span>
* <span data-ttu-id="1ed43-119">Erfahren, wie räumliche Ausrichtung zwischen mehreren Geräten erreicht werden kann</span><span class="sxs-lookup"><span data-stu-id="1ed43-119">Learn how to achieve spatial alignment between multiple devices</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1ed43-120">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="1ed43-120">Prerequisites</span></span>

* <span data-ttu-id="1ed43-121">Ein Windows 10-Computer, auf dem die richtigen [Tools installiert](install-the-tools.md) sind</span><span class="sxs-lookup"><span data-stu-id="1ed43-121">A Windows 10 computer configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="1ed43-122">Windows 10 SDK (10.0.18362.0 oder höher)</span><span class="sxs-lookup"><span data-stu-id="1ed43-122">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="1ed43-123">Ein für die [Entwicklung konfiguriertes](using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät</span><span class="sxs-lookup"><span data-stu-id="1ed43-123">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="1ed43-124"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.3.15 und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform</span><span class="sxs-lookup"><span data-stu-id="1ed43-124"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="1ed43-125">Durchgearbeiteter Abschnitt [Erstellen einer Spatial Anchors-Ressource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) des Tutorials [Schnellstart: Erstellen einer Unity HoloLens-App, die Azure Spatial Anchors verwendet](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).</span><span class="sxs-lookup"><span data-stu-id="1ed43-125">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="1ed43-126">Durchgearbeitete Tutorialserie [Erste Schritte](mr-learning-base-01.md) oder vorherige grundlegende Erfahrung mit Unity und MRTK</span><span class="sxs-lookup"><span data-stu-id="1ed43-126">Completed the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="1ed43-127">Durchgearbeitete [Tutorialserie „Azure Spatial Anchors“](mr-learning-asa-01.md) oder vorherige Erfahrung im Erstellen eines Azure Spatial Anchors-Kontos</span><span class="sxs-lookup"><span data-stu-id="1ed43-127">Completed the [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) series or prior experience creating an Azure Spatial Anchors Account</span></span>
* <span data-ttu-id="1ed43-128">Wenn Sie unter Android sowie HoloLens bereitstellen möchten</span><span class="sxs-lookup"><span data-stu-id="1ed43-128">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="1ed43-129">Ein Android-Gerät mit <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">Entwicklerunterstützung</a> und <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore-Unterstützung</a> mit USB-Verbindung zu Ihrem Windows- oder macOS-Computer</span><span class="sxs-lookup"><span data-stu-id="1ed43-129">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="1ed43-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.3.15 und hinzugefügtem Buildunterstützungsmodul für Android</span><span class="sxs-lookup"><span data-stu-id="1ed43-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Android Build Support module added</span></span>
* <span data-ttu-id="1ed43-131">Wenn Sie unter iOS sowie HoloLens bereitstellen möchten</span><span class="sxs-lookup"><span data-stu-id="1ed43-131">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="1ed43-132">Ein macOS-Computer mit installierter neuester Version von <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> und <a href="https://cocoapods.org" target="_blank">CocoaPods</a></span><span class="sxs-lookup"><span data-stu-id="1ed43-132">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="1ed43-133">Ein iOS-Gerät mit <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit-Unterstützung</a> und USB-Verbindung mit Ihrem macOS-Computer</span><span class="sxs-lookup"><span data-stu-id="1ed43-133">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="1ed43-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.3.15 und hinzugefügtem Buildunterstützungsmodul für iOS</span><span class="sxs-lookup"><span data-stu-id="1ed43-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="1ed43-135">Die empfohlene Mixed Reality Toolkit-Version für diese Tutorialreihe ist MRTK 2.4.0.</span><span class="sxs-lookup"><span data-stu-id="1ed43-135">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="1ed43-136">Die empfohlene Unity-Version für diese Tutorialreihe ist Unity 2019.3.15.</span><span class="sxs-lookup"><span data-stu-id="1ed43-136">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="1ed43-137">Diese Informationen besitzen Vorrang vor allen Unity-Versionsanforderungen, die in den oben verlinkten Voraussetzungen angegeben sind.</span><span class="sxs-lookup"><span data-stu-id="1ed43-137">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="1ed43-138">Nächstes Tutorial: 2. Einrichten von Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="1ed43-138">Next Tutorial: 2. Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
