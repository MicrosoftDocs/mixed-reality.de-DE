---
title: Tutorials zu Azure Speech Services-3. Hinzufügen der Komponente zur Sprachübersetzung von Azure Cognitive Services
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: c7cbdca3c22253042a9be44a194fca8925f0f446
ms.sourcegitcommit: 599bbdd861ce6ff11b6cfb345a0a995f8b7bf85b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2019
ms.locfileid: "68977964"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="b0e16-105">3. Hinzufügen der Komponente zur Sprachübersetzung von Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="b0e16-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="b0e16-106">In diesem Tutorial erfahren Sie mehr über die Komponente zur Sprachübersetzung von Azure Cognitive Services in unserem Projekt sowie über die Übersetzung in drei verschiedene Sprachen.</span><span class="sxs-lookup"><span data-stu-id="b0e16-106">In this tutorial, we learn about the Azure Cognitive Services Speech Translation component in our project as well as translate into three different languages.</span></span> 

## <a name="instructions"></a><span data-ttu-id="b0e16-107">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="b0e16-107">Instructions</span></span>

1. <span data-ttu-id="b0e16-108">Wählen Sie das Lunarcom_Base-Objekt in der Hierarchie aus, und klicken Sie im Inspektor-Panel auf Komponente hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b0e16-108">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="b0e16-109">Suchen Sie nach lunarcomtranslationerkenzer, und wählen Sie ihn aus.</span><span class="sxs-lookup"><span data-stu-id="b0e16-109">Search for and select LunarcomTranslationRecognizer.</span></span>

![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

> <span data-ttu-id="b0e16-111">Hinweis: Stellen Sie sicher, dass der Simulator im Offline Modus deaktiviert ist, bevor Sie die Sprach-SDK-Übersetzer</span><span class="sxs-lookup"><span data-stu-id="b0e16-111">Note: Ensure the offline mode simulator is disabled before testing the Speech-SDK translator.</span></span> <span data-ttu-id="b0e16-112">Zum übersetzen müssen Sie mit dem Internet verbunden sein.</span><span class="sxs-lookup"><span data-stu-id="b0e16-112">In order to translate, you must be connected to the internet.</span></span> <span data-ttu-id="b0e16-113">Siehe Abbildung unten, wo Sie diese Einstellung finden.</span><span class="sxs-lookup"><span data-stu-id="b0e16-113">See image below on where to find this setting.</span></span> 
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

2. <span data-ttu-id="b0e16-115">Klicken Sie in der Dropdown Liste auf die Dropdown Liste, und wählen Sie die Sprache aus, in die übersetzt werden soll.</span><span class="sxs-lookup"><span data-stu-id="b0e16-115">Click the drop-down in the LunarcomTranslationRecognizer, and select the language you would like to translate to.</span></span>

![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="b0e16-117">Führen Sie nun die Anwendung aus, und testen Sie den Translator, indem Sie auf die Schaltfläche Satellit klicken und mit der Sprache beginnen.</span><span class="sxs-lookup"><span data-stu-id="b0e16-117">Now, run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="b0e16-118">Klicken Sie erneut auf die Schaltfläche Satellit, um die Erkennung zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="b0e16-118">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="b0e16-119">Im folgenden finden Sie ein Beispiel dafür, wie ihre Szene aussehen sollte.</span><span class="sxs-lookup"><span data-stu-id="b0e16-119">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="b0e16-120">Sie können die Sprache in der Dropdown Liste "Zielsprache" (siehe Abbildung oben) ändern, um die Übersetzung in andere Sprachen zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="b0e16-120">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

> <span data-ttu-id="b0e16-121">Hinweis: Vergewissern Sie sich vor dem Testen, dass der Offline Simulator deaktiviert ist, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="b0e16-121">Note: Before testing, ensure that the offline simulator is disabled, as shown in the image below.</span></span>
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

<span data-ttu-id="b0e16-123">Im folgenden finden Sie ein Beispiel dafür, wie ihre Szene aussehen sollte:</span><span class="sxs-lookup"><span data-stu-id="b0e16-123">Below is an example of what your scene should look like:</span></span>

![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="b0e16-125">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="b0e16-125">Congratulations</span></span>

<span data-ttu-id="b0e16-126">Jetzt kann Ihr Projekt die Wörter, die Sie sprechen, in verschiedene Sprachen übersetzen.</span><span class="sxs-lookup"><span data-stu-id="b0e16-126">Now your project can translate the words you speak into several different languages.</span></span> <span data-ttu-id="b0e16-127">Sie können mit den Sprachen experimentieren und die Genauigkeit der Übersetzung testen.</span><span class="sxs-lookup"><span data-stu-id="b0e16-127">Feel free to play around with the languages, and test the accuracy of the translation.</span></span> 

[<span data-ttu-id="b0e16-128">Nächstes Tutorial: 4. Einrichten des Verständnisses von Absichten und natürlicher Sprache</span><span class="sxs-lookup"><span data-stu-id="b0e16-128">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)

