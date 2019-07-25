---
title: Spracherkennung und-Aufzeichnung für das Lern-SDK-Modul von Mr
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: e5d0919a69c9e6b0c4233d23bf6d370f3def6576
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460310"
---
# <a name="3----adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="7ec48-104">3.    Hinzufügen der Komponente zur Sprachübersetzung von Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="7ec48-104">3.    Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="7ec48-105">In diesem Tutorial erfahren Sie mehr über die Azure Cognitive Services Speech Translation-Komponente in unserem Projekt sowie über die Übersetzung in drei verschiedene Sprachen.</span><span class="sxs-lookup"><span data-stu-id="7ec48-105">In this tutorial, we learn aabout the Azure Cognitive Services Speech Translation component in our project as well as translate into three different languages.</span></span> 

1. <span data-ttu-id="7ec48-106">Wählen Sie das Lunarcom_Base-Objekt in der Hierarchie aus, und klicken Sie im Inspektor-Panel auf Komponente hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="7ec48-106">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the inspector panel.</span></span> <span data-ttu-id="7ec48-107">Suchen Sie nach lunarcomtranslationerkenzer, und wählen Sie ihn aus.</span><span class="sxs-lookup"><span data-stu-id="7ec48-107">Search for and select LunarcomTranslationRecognizer.</span></span>

![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

> <span data-ttu-id="7ec48-109">Hinweis: Stellen Sie sicher, dass der Simulator im Offline Modus deaktiviert ist, bevor Sie die Sprach-SDK-Übersetzer</span><span class="sxs-lookup"><span data-stu-id="7ec48-109">Note: Ensure the offline mode simulator is disabled before testing the Speech-SDK translator.</span></span> <span data-ttu-id="7ec48-110">Zum übersetzen müssen Sie mit dem Internet verbunden sein.</span><span class="sxs-lookup"><span data-stu-id="7ec48-110">In order to translate, you must be connected to the internet.</span></span> <span data-ttu-id="7ec48-111">Siehe Abbildung unten, wo Sie diese Einstellung finden.</span><span class="sxs-lookup"><span data-stu-id="7ec48-111">See image below on where to find this setting.</span></span> 
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

2. <span data-ttu-id="7ec48-113">Klicken Sie in der Dropdown Liste auf die Dropdown Liste, und wählen Sie die Sprache aus, in die übersetzt werden soll.</span><span class="sxs-lookup"><span data-stu-id="7ec48-113">Click the drop-down in the LunarcomTranslationRecognizer, and select the language you would like to translate to.</span></span>

![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. <span data-ttu-id="7ec48-115">Führen Sie nun die Anwendung aus, und testen Sie den Translator, indem Sie auf die Schaltfläche Satellit klicken und mit der Sprache beginnen.</span><span class="sxs-lookup"><span data-stu-id="7ec48-115">Now, run the application and test the translator by clicking the Satellite button, and begin speaking.</span></span> <span data-ttu-id="7ec48-116">Klicken Sie erneut auf die Schaltfläche Satellit, um die Erkennung zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="7ec48-116">Press the Satellite button again to stop the recognition.</span></span> <span data-ttu-id="7ec48-117">Im folgenden finden Sie ein Beispiel dafür, wie ihre Szene aussehen sollte.</span><span class="sxs-lookup"><span data-stu-id="7ec48-117">Below is an example of what your scene should look like.</span></span> <span data-ttu-id="7ec48-118">Sie können die Sprache in der Dropdown Liste "Zielsprache" (siehe Abbildung oben) ändern, um die Übersetzung in andere Sprachen zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="7ec48-118">Feel free to change the language under the "Target Language" dropdown (see image above) to explore translation into other languages.</span></span>

> <span data-ttu-id="7ec48-119">Hinweis: Vergewissern Sie sich vor dem Testen, dass der Offline Simulator deaktiviert ist, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="7ec48-119">Note: Before testing, ensure that the offline simulator is disabled, as shown in the image below.</span></span>
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

<span data-ttu-id="7ec48-121">Im folgenden finden Sie ein Beispiel dafür, wie ihre Szene aussehen sollte:</span><span class="sxs-lookup"><span data-stu-id="7ec48-121">Below is an example of what your scene should look like:</span></span>

![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="7ec48-123">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="7ec48-123">Congratulations</span></span>

<span data-ttu-id="7ec48-124">Jetzt kann Ihr Projekt die Wörter, die Sie sprechen, in verschiedene Sprachen übersetzen.</span><span class="sxs-lookup"><span data-stu-id="7ec48-124">Now  your project can translate the words you speak into several different languages.</span></span> <span data-ttu-id="7ec48-125">Sie können mit den Sprachen experimentieren und die Genauigkeit der Übersetzung testen.</span><span class="sxs-lookup"><span data-stu-id="7ec48-125">Feel free to play around with the languages, and test the accuracy of the translation.</span></span> 

[<span data-ttu-id="7ec48-126">Nächstes Tutorial: 4.  Einrichten des Verständnisses von Absichten und natürlicher Sprache</span><span class="sxs-lookup"><span data-stu-id="7ec48-126">Next tutorial: 4.  Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)

