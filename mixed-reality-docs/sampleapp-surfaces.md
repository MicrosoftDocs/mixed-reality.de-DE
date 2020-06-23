---
title: Surface
description: Oberflächen ist eine Open-Source-Beispiel-App aus den Mixed Reality-Entwurfs Labors von Microsoft. Es wird erläutert, wie wir mit visuellen, Audiodaten und vollständig artikulierten Hand Nachverfolgung eine taktikvolle Sensation erstellen können.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Windows Mixed Reality, hololens, mrtk, Design, Beispiel-APP, Steuerelemente
ms.openlocfilehash: fb6948ceda2a059323d23d72d6d3245a3a9896ee
ms.sourcegitcommit: 4282d92e93869e4829338bdf7d981c3ee0260bfd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85240456"
---
# <a name="surfaces"></a><span data-ttu-id="301a2-105">Surface</span><span class="sxs-lookup"><span data-stu-id="301a2-105">Surfaces</span></span>

>[!NOTE]
><span data-ttu-id="301a2-106">In diesem Artikel wird ein exploratives Beispiel erläutert, das wir in den [Entwurfs Labors für gemischte Realität](https://github.com/Microsoft/MRDesignLabs_Unity)erstellt haben, einem Ort, an dem wir unsere Erkenntnisse und Vorschläge für die Entwicklung gemischter Reality-apps teilen.</span><span class="sxs-lookup"><span data-stu-id="301a2-106">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="301a2-107">Unsere Entwurfs bezogenen Artikel und Code werden sich weiterentwickeln, wenn wir neue Ermittlungen durchführen.</span><span class="sxs-lookup"><span data-stu-id="301a2-107">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="301a2-108">[Oberflächen](https://github.com/microsoft/MRDL_Unity_Surfaces) ist eine Open-Source-Beispiel-App aus den Mixed Reality-Entwurfs Labors von Microsoft.</span><span class="sxs-lookup"><span data-stu-id="301a2-108">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="301a2-109">Es wird erläutert, wie wir mit visuellen, Audiodaten und vollständig artikulierten Hand Nachverfolgung eine taktikvolle Sensation erstellen können.</span><span class="sxs-lookup"><span data-stu-id="301a2-109">It explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span>

![Surface](images/MRDL_Surfaces_1.jpg)

## <a name="about-the-app"></a><span data-ttu-id="301a2-111">Informationen zur APP</span><span class="sxs-lookup"><span data-stu-id="301a2-111">About the app</span></span>
<span data-ttu-id="301a2-112">Oberflächen zeigt, wie das Eingabe System von Mixed Reality Toolkit (mrtk) und die Bausteine zum Erstellen einer APP-Oberfläche für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="301a2-112">Surfaces demonstrates how to use Mixed Reality Toolkit(MRTK)'s input system and building blocks to create an app experience for HoloLens 2.</span></span> <span data-ttu-id="301a2-113">In diesem Projekt finden Sie die Beispiele für:</span><span class="sxs-lookup"><span data-stu-id="301a2-113">In this project, you can find the examples of:</span></span>
- <span data-ttu-id="301a2-114">Verwenden Sie das [Eingabe System](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)von mrtk, insbesondere die Hand-und gemeinsame Nachverfolgung.</span><span class="sxs-lookup"><span data-stu-id="301a2-114">Use MRTK's [Input System](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html), specifically hand / joint tracking.</span></span>
- <span data-ttu-id="301a2-115">Verwenden Sie den [Standard-Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) von mrtk für leistungsfähige Grafiken.</span><span class="sxs-lookup"><span data-stu-id="301a2-115">Use MRTK's [Standard Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) for performant graphics.</span></span>

<span data-ttu-id="301a2-116">Sie können diese Projektkomponenten verwenden, um Ihre eigenen Umgebungen mit gemischter Reality-APP zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="301a2-116">You can use this project's components to create your own mixed reality app experiences.</span></span>

## <a name="mr-dev-days-2020---learnings-from-the-mr-surfaces-app"></a><span data-ttu-id="301a2-117">Mr dev Days 2020-Learnings von der App "Mr-Oberflächen"</span><span class="sxs-lookup"><span data-stu-id="301a2-117">MR Dev Days 2020 - Learnings from the MR Surfaces App</span></span>
[<span data-ttu-id="301a2-118">Erkenntnisse von der App "Mr-Oberflächen"</span><span class="sxs-lookup"><span data-stu-id="301a2-118">Learnings from the MR Surfaces App</span></span>](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)

<span data-ttu-id="301a2-119">Lars Simkins, Senior Designer hinter der mrdl-Oberflächen-APP, spricht über die Entwurfs Story der APP und technische Highlights.</span><span class="sxs-lookup"><span data-stu-id="301a2-119">Lars Simkins, Senior designer behind the MRDL Surfaces app talks about the app's design story and technical highlights.</span></span>

## <a name="project-repository-on-github"></a><span data-ttu-id="301a2-120">Projektrepository auf GitHub</span><span class="sxs-lookup"><span data-stu-id="301a2-120">Project repository on GitHub</span></span>
[https://github.com/microsoft/MRDL_Unity_Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a><span data-ttu-id="301a2-121">Herunterladen der APP aus Microsoft Store in hololens 2</span><span class="sxs-lookup"><span data-stu-id="301a2-121">Download app from Microsoft Store in HoloLens 2</span></span>
https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0#activetab=pivot:overviewtab

<span data-ttu-id="301a2-122">(Die APP ist nur auf hololens verfügbar 2)</span><span class="sxs-lookup"><span data-stu-id="301a2-122">(The app is only available on HoloLens 2)</span></span>

## <a name="about-the-author"></a><span data-ttu-id="301a2-123">Zum Autor</span><span class="sxs-lookup"><span data-stu-id="301a2-123">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="301a2-124"><b>Dong-Yoon-Park</b></span><span class="sxs-lookup"><span data-stu-id="301a2-124"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="301a2-125">UX-Designer@Microsoft</span><span class="sxs-lookup"><span data-stu-id="301a2-125">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="301a2-126">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="301a2-126">See also</span></span>

* [<span data-ttu-id="301a2-127">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="301a2-127">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="301a2-128">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="301a2-128">Object collection</span></span>](object-collection.md)
