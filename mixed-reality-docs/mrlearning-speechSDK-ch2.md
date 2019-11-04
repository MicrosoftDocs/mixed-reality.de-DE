---
title: Tutorials zu Azure Speech Services-2. Hinzufügen eines Offline Modus für die lokale Sprachübersetzung
description: Arbeiten Sie diesen Kurs durch, um zu erfahren, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 5382a1cce38e8607042c21b8dd3157d1da2fa72e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437552"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="73493-105">2. Hinzufügen eines Offline Modus für die lokale Sprachübersetzung</span><span class="sxs-lookup"><span data-stu-id="73493-105">2. Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="73493-106">In diesem Tutorial fügen wir einen Offline Modus hinzu, mit dem Sie eine lokale Sprachübersetzung durchführen können, wenn keine Verbindung mit dem Azure-Dienst hergestellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="73493-106">In this tutorial, we'll add an offline mode that lets you perform local speech-to-text translation when we are unable to connect to the Azure service.</span></span> <span data-ttu-id="73493-107">Wir *simulieren* auch den Zustand "getrennt".</span><span class="sxs-lookup"><span data-stu-id="73493-107">We will also *simulate* a disconnected state.</span></span>

## <a name="instructions"></a><span data-ttu-id="73493-108">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="73493-108">Instructions</span></span>

1. <span data-ttu-id="73493-109">Wählen Sie das Lunarcom_Base-Objekt in der Hierarchie aus.</span><span class="sxs-lookup"><span data-stu-id="73493-109">Select the Lunarcom_Base object in the hierarchy.</span></span>
2. <span data-ttu-id="73493-110">Klicken Sie im Inspektor-Panel auf Komponente hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="73493-110">Click Add Component in the Inspector panel.</span></span> <span data-ttu-id="73493-111">Suchen Sie nach der lunarcom-Offline Kennung, und wählen Sie Sie aus</span><span class="sxs-lookup"><span data-stu-id="73493-111">Search for and select the Lunarcom Offline Recognition.</span></span>

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

3. <span data-ttu-id="73493-113">Klicken Sie in der Dropdown Liste auf die Dropdown Liste, und wählen Sie aktiviert aus.</span><span class="sxs-lookup"><span data-stu-id="73493-113">Click the drop-down in the LunarcomOfflineRecognizer and select Enabled.</span></span> <span data-ttu-id="73493-114">Dadurch wird das Projekt so programmiert, dass der Benutzer nicht über eine Verbindung verfügt.</span><span class="sxs-lookup"><span data-stu-id="73493-114">This programs the project to act like the user doesn't have a connection.</span></span> 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

4. <span data-ttu-id="73493-116">Klicken Sie im Unity-Editor auf abspielen, und testen Sie es.</span><span class="sxs-lookup"><span data-stu-id="73493-116">Press Play in Unity Editor, and test it.</span></span> <span data-ttu-id="73493-117">Drücken Sie das Mikrofon in der unteren linken Ecke der Szene, und beginnen Sie mit der Spracheingabe.</span><span class="sxs-lookup"><span data-stu-id="73493-117">Press the microphone in the bottom-left corner in the scene and begin speaking.</span></span> 

> [!NOTE]
> <span data-ttu-id="73493-118">Da wir offline sind, wurde die Wake-Word-Funktion deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="73493-118">Because we’re offline, wake word functionality has been disabled.</span></span> <span data-ttu-id="73493-119">Sie müssen jedes Mal, wenn Sie die Sprache im Offline Zustand erkennen möchten, physisch auf das Mikrofon klicken.</span><span class="sxs-lookup"><span data-stu-id="73493-119">You'll need to physically click the microphone every time you wish to have your speech recognized when offline.</span></span> 

<span data-ttu-id="73493-120">Im folgenden finden Sie ein Beispiel dafür, wie ihre Szene aussehen könnte.</span><span class="sxs-lookup"><span data-stu-id="73493-120">Below is an example of what your scene could look like.</span></span>

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="73493-122">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="73493-122">Congratulations</span></span>

<span data-ttu-id="73493-123">Der Offline Modus wurde aktiviert.</span><span class="sxs-lookup"><span data-stu-id="73493-123">The offline mode has been enabled.</span></span> <span data-ttu-id="73493-124">Wenn Sie nun offline sind, können Sie weiterhin mit dem Sprach-SDK für Ihr Projekt arbeiten.</span><span class="sxs-lookup"><span data-stu-id="73493-124">Now, when you're offline, you can still work on your project with the speech-SDK!</span></span> 


[<span data-ttu-id="73493-125">Nächstes Tutorial: 3. Hinzufügen der Komponente zur Sprachübersetzung von Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="73493-125">Next Tutorial: 3.  Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)

