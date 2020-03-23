---
title: 'Tutorials zu Azure Speech-Diensten: 3 Hinzufügen der Sprachübersetzungskomponente von Azure Cognitive Services'
description: In diesem Kurs erfahren Sie, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: d8e73e24f0522ff71b95ea1886d59893216b0597
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79028342"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a><span data-ttu-id="ff250-105">3. Hinzufügen der Sprachübersetzungskomponente von Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="ff250-105">3. Adding the Azure Cognitive Services speech translation component</span></span>

<span data-ttu-id="ff250-106">In diesem Tutorial fügen Sie Ihrem Projekt Sprachübersetzung hinzu, die es Ihnen ermöglicht, Ihre Sprache in drei verschiedene Sprachen zu übersetzen und zu transkribieren.</span><span class="sxs-lookup"><span data-stu-id="ff250-106">In this tutorial, you will add speech translation to your project which will allow you to translate and transcribed your speech into three different languages.</span></span>

## <a name="objectives"></a><span data-ttu-id="ff250-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="ff250-107">Objectives</span></span>

* <span data-ttu-id="ff250-108">Erlernen der Integration von Azure-Sprachübersetzung</span><span class="sxs-lookup"><span data-stu-id="ff250-108">Learn how to integrate Azure speech translation</span></span>

## <a name="instructions"></a><span data-ttu-id="ff250-109">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="ff250-109">Instructions</span></span>

<span data-ttu-id="ff250-110">Wählen Sie im Hierarchiefenster das **Lunarcom**-Objekt aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um dem Lunarcom-Objekt die Komponente **Lunarcom Translation Recognizer (Script)** hinzuzufügen und sie wie folgt zu konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="ff250-110">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Translation Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="ff250-111">Ändern Sie die **Zielsprache** in eine Sprache Ihrer Wahl, z. B. _Deutsch_</span><span class="sxs-lookup"><span data-stu-id="ff250-111">Change the **Target Language** to a language of your choosing, for example, _German_</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="ff250-113">Die Komponente „Lunarcom Translation Recognizer (Script)“ ist kein Bestandteil des MRTK.</span><span class="sxs-lookup"><span data-stu-id="ff250-113">The Lunarcom Translation Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="ff250-114">Sie wurde zusammen mit den Ressourcen für dieses Tutorial zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="ff250-114">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="ff250-115">Wenn Sie jetzt in den Spielmodus wechseln, können Sie die Sprachübersetzung testen, indem Sie zuerst auf die Satellitenschaltfläche klicken.</span><span class="sxs-lookup"><span data-stu-id="ff250-115">If you now enter Game mode, you can test the speech translation by first pressing the satellite button.</span></span> <span data-ttu-id="ff250-116">Falls Ihr Computer über ein Mikrofon verfügt, wird Ihre Sprache dann, wenn Sie etwas sagen, in die gewählte Sprache übersetzt und im Terminalbereich transkribiert:</span><span class="sxs-lookup"><span data-stu-id="ff250-116">Then, assuming your computer has a microphone, when you say something, your speech will be translated into the chosen language and transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-2.png)

> [!CAUTION]
> <span data-ttu-id="ff250-118">Die Anwendung muss eine Verbindung mit Azure herstellen, achten Sie also darauf, dass Ihr Computer/Gerät mit dem Internet verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="ff250-118">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="ff250-119">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="ff250-119">Congratulations</span></span>

<span data-ttu-id="ff250-120">Ihr Projekt kann nun die von Ihnen gesprochenen Wörter erfolgreich in verschiedene Sprachen übersetzen.</span><span class="sxs-lookup"><span data-stu-id="ff250-120">Your project can now successfully translate the words you speak into several different languages.</span></span> <span data-ttu-id="ff250-121">Führen Sie die Anwendung auf Ihrem Gerät aus, um sicherzustellen, dass das Feature ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="ff250-121">Run the application on your device to ensure the feature is working properly.</span></span>

[<span data-ttu-id="ff250-122">Nächstes Tutorial: 4. Einrichten des Verständnisses von Absichten und natürlicher Sprache</span><span class="sxs-lookup"><span data-stu-id="ff250-122">Next tutorial: 4. Setting up intent and natural language understanding</span></span>](mrlearning-speechSDK-ch4.md)
