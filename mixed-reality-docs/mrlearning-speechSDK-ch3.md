---
title: Azure Speech Services tutorials - 3. Adding the Azure Cognitive Services speech translation component
description: In this course, you will learn how to implement Azure Speech SDK within a mixed reality application.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: dc5300b51ccb151a2e38f9d15b84a4a9031e2bb4
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143233"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="9e0a4-105">3. Adding the Azure Cognitive Services speech translation component</span><span class="sxs-lookup"><span data-stu-id="9e0a4-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="9e0a4-106">In this tutorial, you'll learn about the Azure Cognitive Services Speech Translation component of your project, as well as how to translate into three different languages.</span><span class="sxs-lookup"><span data-stu-id="9e0a4-106">In this tutorial, you'll learn about the Azure Cognitive Services Speech Translation component of your project, as well as how to translate into three different languages.</span></span>

## <a name="instructions"></a><span data-ttu-id="9e0a4-107">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="9e0a4-107">Instructions</span></span>

1. <span data-ttu-id="9e0a4-108">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span><span class="sxs-lookup"><span data-stu-id="9e0a4-108">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="9e0a4-109">Search for and select Lunarcom Translation Recognizer.</span><span class="sxs-lookup"><span data-stu-id="9e0a4-109">Search for and select Lunarcom Translation Recognizer.</span></span>

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    <span data-ttu-id="9e0a4-111">Disable the offline mode simulator.</span><span class="sxs-lookup"><span data-stu-id="9e0a4-111">Disable the offline mode simulator.</span></span>

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    ><span data-ttu-id="9e0a4-113">Before moving on, ensure that the offline mode simulator is disabled (as shown in the image above) before testing the Speech-SDK translator.</span><span class="sxs-lookup"><span data-stu-id="9e0a4-113">Before moving on, ensure that the offline mode simulator is disabled (as shown in the image above) before testing the Speech-SDK translator.</span></span> <span data-ttu-id="9e0a4-114">In order to translate, you must be connected to the internet.</span><span class="sxs-lookup"><span data-stu-id="9e0a4-114">In order to translate, you must be connected to the internet.</span></span>

2. <span data-ttu-id="9e0a4-115">Click the drop-down in the Lunarcom Translation Recognizer, and select the language you would like to translate to.</span><span class="sxs-lookup"><span data-stu-id="9e0a4-115">Click the drop-down in the Lunarcom Translation Recognizer, and select the language you would like to translate to.</span></span>

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="9e0a4-117">Run the application and test the translator by clicking the Satellite button, and begin speaking.</span><span class="sxs-lookup"><span data-stu-id="9e0a4-117">Run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="9e0a4-118">Press the Satellite button again to stop the recognition.</span><span class="sxs-lookup"><span data-stu-id="9e0a4-118">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="9e0a4-119">Below is an example of what your scene should look like.</span><span class="sxs-lookup"><span data-stu-id="9e0a4-119">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="9e0a4-120">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span><span class="sxs-lookup"><span data-stu-id="9e0a4-120">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

    <span data-ttu-id="9e0a4-121">Below is an example of what your scene should look like:</span><span class="sxs-lookup"><span data-stu-id="9e0a4-121">Below is an example of what your scene should look like:</span></span>

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="9e0a4-123">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="9e0a4-123">Congratulations</span></span>

<span data-ttu-id="9e0a4-124">Your project can now successfully translate the words you speak into several different languages.</span><span class="sxs-lookup"><span data-stu-id="9e0a4-124">Your project can now successfully translate the words you speak into several different languages.</span></span> <span data-ttu-id="9e0a4-125">Feel free to play around with the languages, and test the accuracy of the translation.</span><span class="sxs-lookup"><span data-stu-id="9e0a4-125">Feel free to play around with the languages, and test the accuracy of the translation.</span></span>

[<span data-ttu-id="9e0a4-126">Nächstes Tutorial: 4. Einrichten der Absicht und der Kenntnisse in natürlicher Sprache</span><span class="sxs-lookup"><span data-stu-id="9e0a4-126">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
