---
title: Spracherkennung und-Aufzeichnung für das Lern-SDK-Modul von Mr
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: e8dc5da5a089079ba38a26969df6070af8bc6200
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460302"
---
# <a name="2----adding-an-offline-mode-for-local-speech-to-text-translation"></a><span data-ttu-id="1b03b-104">2.    Hinzufügen eines Offline Modus für die lokale Sprachübersetzung</span><span class="sxs-lookup"><span data-stu-id="1b03b-104">2.    Adding an offline mode for local speech-to-text translation</span></span>

<span data-ttu-id="1b03b-105">In diesem Tutorial fügen wir einen Offline Modus hinzu, mit dem Sie eine lokale Sprachübersetzung durchführen können, wenn keine Verbindung mit dem Azure-Dienst hergestellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="1b03b-105">In this tutorial, we'll add an offline mode that lets you perform local speech-to-text translation when we are unable to connect to the Azure service.</span></span> <span data-ttu-id="1b03b-106">Wir *simulieren* auch den Zustand "getrennt".</span><span class="sxs-lookup"><span data-stu-id="1b03b-106">We will also *simulate* a disconnected state.</span></span>

1. <span data-ttu-id="1b03b-107">Wählen Sie das Lunarcom_Base-Objekt in der Hierarchie aus, und klicken Sie im Inspektor-Panel auf Komponente hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="1b03b-107">Select the Lunarcom_Base object in the hierarchy, and click Add Component in the Inspector panel.</span></span> <span data-ttu-id="1b03b-108">Suchen Sie nach der lunarcom-Offline Kennung, und wählen Sie Sie aus</span><span class="sxs-lookup"><span data-stu-id="1b03b-108">Search for and select the Lunarcom Offline Recognition.</span></span>

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

2. <span data-ttu-id="1b03b-110">Klicken Sie in der Dropdown Liste auf die Dropdown Liste, und wählen Sie aktiviert aus.</span><span class="sxs-lookup"><span data-stu-id="1b03b-110">Click the drop-down in the LunarcomOfflineRecognizer, and select Enabled.</span></span> <span data-ttu-id="1b03b-111">Dadurch wird das Projekt so programmiert, dass der Benutzer nicht über eine Verbindung verfügt.</span><span class="sxs-lookup"><span data-stu-id="1b03b-111">This programs the project to act like the user doesn't have a connection.</span></span> 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. <span data-ttu-id="1b03b-113">Klicken Sie jetzt im Unity-Editor auf Play, und testen Sie es.</span><span class="sxs-lookup"><span data-stu-id="1b03b-113">Now, press play in Unity Editor, and test it.</span></span> <span data-ttu-id="1b03b-114">Drücken Sie das Mikrofon in der unteren linken Ecke der Szene, und beginnen Sie mit der Spracheingabe.</span><span class="sxs-lookup"><span data-stu-id="1b03b-114">Press the microphone in the bottom left hand corner in the scene, and begin speaking.</span></span> 

> [!NOTE]
> <span data-ttu-id="1b03b-115">Da wir offline sind, wurde die Wake-Word-Funktion deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="1b03b-115">Because we’re offline, wake word functionality has been disabled.</span></span> <span data-ttu-id="1b03b-116">Sie müssen jedes Mal, wenn Sie die Sprache im Offline Zustand erkennen möchten, physisch auf das Mikrofon klicken.</span><span class="sxs-lookup"><span data-stu-id="1b03b-116">You'll have to physically click the microphone every time you wish to have your speech recognized when offline.</span></span> 

<span data-ttu-id="1b03b-117">Im folgenden finden Sie ein Beispiel dafür, wie ihre Szene aussehen könnte.</span><span class="sxs-lookup"><span data-stu-id="1b03b-117">Below is an example of what your scene could look like.</span></span>

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a><span data-ttu-id="1b03b-119">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="1b03b-119">Congratulations</span></span>

<span data-ttu-id="1b03b-120">Der Offline Modus wurde aktiviert.</span><span class="sxs-lookup"><span data-stu-id="1b03b-120">The offline mode has been enabled.</span></span> <span data-ttu-id="1b03b-121">Wenn Sie nun offline sind, können Sie weiterhin mit dem Sprach-SDK für Ihr Projekt arbeiten.</span><span class="sxs-lookup"><span data-stu-id="1b03b-121">Now, when you're offline, you can still work on your project with the speech-SDK!</span></span> 


[<span data-ttu-id="1b03b-122">Nächstes Tutorial: 3.  Hinzufügen der Komponente zur Sprachübersetzung von Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="1b03b-122">Next Tutorial: 3.  Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)

