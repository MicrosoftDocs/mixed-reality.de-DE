---
title: Tutorials zu Azure Speech Services-3. Hinzufügen der Komponente zur Sprachübersetzung von Azure Cognitive Services
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 490b9f6142208a190748b6d76c57be493172c1e5
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913197"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="5f749-105">3. Hinzufügen der Komponente zur Sprachübersetzung von Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="5f749-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="5f749-106">In diesem Tutorial erfahren Sie mehr über die Komponente zur Sprachübersetzung von Azure Cognitive Services in unserem Projekt sowie über die Übersetzung in drei verschiedene Sprachen.</span><span class="sxs-lookup"><span data-stu-id="5f749-106">In this tutorial, we learn about the Azure Cognitive Services Speech Translation component in our project as well as translate into three different languages.</span></span>

## <a name="instructions"></a><span data-ttu-id="5f749-107">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="5f749-107">Instructions</span></span>

1. <span data-ttu-id="5f749-108">Wählen Sie das Objekt Lunarcom_Base in der Hierarchie aus, und klicken Sie im Inspektor-Panel auf Komponente hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5f749-108">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="5f749-109">Suchen Sie nach dem lunarcom-Übersetzungs Erkennungs Modul.</span><span class="sxs-lookup"><span data-stu-id="5f749-109">Search for and select Lunarcom Translation Recognizer.</span></span>

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    <span data-ttu-id="5f749-111">Deaktivieren Sie den Simulator im Offline Modus.</span><span class="sxs-lookup"><span data-stu-id="5f749-111">Disable the offline mode simulator.</span></span>

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    ><span data-ttu-id="5f749-113">Bevor Sie fortfahren, stellen Sie sicher, dass der Simulator im Offline Modus deaktiviert ist (siehe Abbildung oben), bevor Sie den Sprach-SDK-Konvertierer testen.</span><span class="sxs-lookup"><span data-stu-id="5f749-113">Before moving on, ensure the offline mode simulator is disabled, as shown in the image above, before testing the Speech-SDK translator.</span></span> <span data-ttu-id="5f749-114">Zum übersetzen müssen Sie mit dem Internet verbunden sein.</span><span class="sxs-lookup"><span data-stu-id="5f749-114">In order to translate, you must be connected to the internet.</span></span>

2. <span data-ttu-id="5f749-115">Klicken Sie in der lunarcom-Übersetzungs Erkennung auf die Dropdown Liste, und wählen Sie die Sprache aus, in die übersetzt werden soll.</span><span class="sxs-lookup"><span data-stu-id="5f749-115">Click the drop-down in the Lunarcom Translation Recognizer, and select the language you would like to translate to.</span></span>

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="5f749-117">Führen Sie nun die Anwendung aus, und testen Sie den Translator, indem Sie auf die Schaltfläche Satellit klicken und mit der Sprache beginnen.</span><span class="sxs-lookup"><span data-stu-id="5f749-117">Now, run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="5f749-118">Klicken Sie erneut auf die Schaltfläche Satellit, um die Erkennung zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="5f749-118">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="5f749-119">Im folgenden finden Sie ein Beispiel dafür, wie ihre Szene aussehen sollte.</span><span class="sxs-lookup"><span data-stu-id="5f749-119">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="5f749-120">Sie können die Sprache in der Dropdown Liste "Zielsprache" (siehe Abbildung oben) ändern, um die Übersetzung in andere Sprachen zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="5f749-120">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

    <span data-ttu-id="5f749-121">Im folgenden finden Sie ein Beispiel dafür, wie ihre Szene aussehen sollte:</span><span class="sxs-lookup"><span data-stu-id="5f749-121">Below is an example of what your scene should look like:</span></span>

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="5f749-123">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="5f749-123">Congratulations</span></span>

<span data-ttu-id="5f749-124">Jetzt kann Ihr Projekt die Wörter, die Sie sprechen, in verschiedene Sprachen übersetzen.</span><span class="sxs-lookup"><span data-stu-id="5f749-124">Now your project can translate the words you speak into several different languages.</span></span> <span data-ttu-id="5f749-125">Sie können mit den Sprachen experimentieren und die Genauigkeit der Übersetzung testen.</span><span class="sxs-lookup"><span data-stu-id="5f749-125">Feel free to play around with the languages, and test the accuracy of the translation.</span></span>

[<span data-ttu-id="5f749-126">Nächstes Tutorial: 4. Einrichten der Absicht und der Kenntnisse in natürlicher Sprache</span><span class="sxs-lookup"><span data-stu-id="5f749-126">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
