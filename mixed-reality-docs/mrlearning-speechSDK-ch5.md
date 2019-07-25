---
title: Spracherkennung und-Aufzeichnung für das Lern-SDK-Modul von Mr
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: fc65dccfcbc181af0c0b321374c721797e120e5d
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460338"
---
# <a name="speech-sdk-learning-module---rocket-launcher-control-using-speech-commands"></a><span data-ttu-id="ef337-104">Sprach-SDK-Lernmodul-Starter Launcher-Steuerelement mithilfe von Sprachbefehlen</span><span class="sxs-lookup"><span data-stu-id="ef337-104">Speech SDK Learning Module - Rocket Launcher Control Using Speech Commands</span></span>

<span data-ttu-id="ef337-105">In dieser Lektion verwenden wir das Intent-Feature des Azure Speech Service, um die Absicht der Sprache zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="ef337-105">In this lesson, we will be using Azure Speech Service's Intent feature to understand the intent of the speech.</span></span> <span data-ttu-id="ef337-106">Wir verwenden die erkannte Absicht der Sprache als Sprachbefehle, um das Raketen Starter Programm zu steuern.</span><span class="sxs-lookup"><span data-stu-id="ef337-106">We will be using the detected intent of speech as the voice commands to control the rocket launcher.</span></span> <span data-ttu-id="ef337-107">In dieser Lektion importieren wir das Raketenstart Programm Asset, und wir verbinden die erkannten Intent Voice-Befehle mit vordefinierten Steuerungs Schaltflächen, um die Raketen zu steuern.</span><span class="sxs-lookup"><span data-stu-id="ef337-107">During this lesson, we will be importing the Rocket Launcher asset and We will interface the detected intent voice commands to predefined control buttons to control the rocket.</span></span> 

## <a name="objectives"></a><span data-ttu-id="ef337-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="ef337-108">Objectives</span></span>

- <span data-ttu-id="ef337-109">Erfahren Sie, wie Sie Sprech Absicht als Sprachbefehle verbinden.</span><span class="sxs-lookup"><span data-stu-id="ef337-109">Learn how to connect speech intent as voice commands.</span></span>
- <span data-ttu-id="ef337-110">Erfahren Sie, wie Sie sprach beabsichtigte Sprachbefehle als Eingabe Befehle für die Befehls Eingabe verwenden.</span><span class="sxs-lookup"><span data-stu-id="ef337-110">Learn how to use speech intent voice commands as rocket control input commands.</span></span>

## <a name="instructions"></a><span data-ttu-id="ef337-111">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="ef337-111">Instructions</span></span>
1. <span data-ttu-id="ef337-112">In diesem Tutorial verwenden wir ein "basemodule"-Asset, um das Raketenstart Programm mit den Sprachbefehlen zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="ef337-112">In this tutorial, we will be using a "BaseModule" asset to integrate rocket launcher with the speech commands.</span></span> <span data-ttu-id="ef337-113">Dafür müssen wir das Medienobjekt in unser Projekt importieren.</span><span class="sxs-lookup"><span data-stu-id="ef337-113">For that, we need to import the asset into our project.</span></span> <span data-ttu-id="ef337-114">Sie können das Asset "Launcher Launcher" mithilfe dieses Links (Anfügen des Links) herunterladen.</span><span class="sxs-lookup"><span data-stu-id="ef337-114">You can download the "Rocket Launcher" asset using this link (Attach the link).</span></span> 

2. <span data-ttu-id="ef337-115">Um das Medienobjekt zu importieren, wechseln Sie zu Assets-> Paket > benutzerdefiniertes Paket importieren > Navigieren Sie zu der heruntergeladenen Datei, und klicken Sie auf importieren.</span><span class="sxs-lookup"><span data-stu-id="ef337-115">To import the asset, please go to assets->Import package->Custom package-> navigate to the downloaded file and click import.</span></span>

![module4chapter5step1](images/module4chapter5step1.PNG)

3. <span data-ttu-id="ef337-117">Navigieren Sie nach dem Importieren des Assets "Launcher Launcher" in der Ordner "Launcher Launcher" > Prefabs-> Wählen Sie "Launcher_Complete" aus, und legen Sie es dann per Drag & amp; Drop in die vorhandene Szenen Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="ef337-117">After importing the "Rocket Launcher" asset, navigate inside the "Rocket Launcher" folder->Prefabs-> Select "Rocket Launcher_Complete", and then drag and drop it into the existing scene Hierarchy.</span></span>

![module4chapter5step2](images/module4chapter5step2.PNG)

4. <span data-ttu-id="ef337-119">Nun müssen wir unser "Launcher"-Start Programm in unser Luis-Projekt integrieren, das wir in unserer vorherigen Lektion (Link für lesson4) gearbeitet haben.</span><span class="sxs-lookup"><span data-stu-id="ef337-119">Now we need to integrate our "Rocket Launcher" with our LUIS project that we worked in our previous lesson (link for lesson4).</span></span> <span data-ttu-id="ef337-120">Erweitern Sie dazu die vorfab "Launcher Launcher_Complete" in der Hierarchie, und suchen Sie nach den Schaltflächen "launchroundbutton", "restotroundbutton" und "Platzierungs Hinweise".</span><span class="sxs-lookup"><span data-stu-id="ef337-120">For that, expand the "Rocket Launcher_Complete" prefab in the hierarchy and find the "LaunchRoundButton", "ResetRoundButton" and "Placement Hints" buttons.</span></span>

![module4chapter5step3](images/module4chapter5step3.PNG)

5. <span data-ttu-id="ef337-122">Wählen Sie "launchroundbutton" aus, und wechseln Sie im Inspektor-Panel zu "interactable", und legen Sie unter Ereignisse "OnClick ()" die vorfab "lunarmodule" mit Drag und Drop ab.</span><span class="sxs-lookup"><span data-stu-id="ef337-122">Select "LaunchRoundButton" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="ef337-123">Wählen Sie dann die Dropdown Liste Funktion aus, und wählen Sie "lunarmodule" aus. Navigieren Sie dann zur Funktion "startthruester ()", und wählen Sie Sie aus.</span><span class="sxs-lookup"><span data-stu-id="ef337-123">Then, select the function drop down and select " LunarModule" and then navigate to "StartThruster()" function and select it.</span></span>

![module4chapter5step 3.0](images/module4chapter5step3.0.PNG)

![module4chapter5step3a](images/module4chapter5step3a.PNG)

6. <span data-ttu-id="ef337-126">Wählen Sie "rebertroundbutton" aus, und wechseln Sie im Inspektor-Panel zu "interactable", und legen Sie unter Ereignisse "OnClick ()" die vorfab "lunarmodule" mit Drag und Drop ab.</span><span class="sxs-lookup"><span data-stu-id="ef337-126">Select "ResetRoundButton" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="ef337-127">Wählen Sie dann die Dropdown-Funktion aus, und wählen Sie "lunarmodule" aus. Navigieren Sie dann zur Funktion "resetmodule ()", und wählen Sie Sie aus.</span><span class="sxs-lookup"><span data-stu-id="ef337-127">Then, select the function drop down and select " LunarModule" and then navigate to "resetModule()" function and select it.</span></span>

![module4chapter5step3b](images/module4chapter5step3b.PNG)

7. <span data-ttu-id="ef337-129">Wählen Sie "Platzierungs Hinweise" aus, und wechseln Sie im Inspektor-Panel zu "interactable", und legen Sie unter Ereignisse "OnClick ()" die vorfab "lunarmodule" mit Drag & Drop ab.</span><span class="sxs-lookup"><span data-stu-id="ef337-129">Select "Placement Hints" and in inspector panel, go to "Interactable" and under events "OnClick ()", drag and drop the "LunarModule" prefab.</span></span> <span data-ttu-id="ef337-130">Wählen Sie dann die Dropdown-Funktion aus, und wählen Sie "lunarmodule" aus. Navigieren Sie dann zur Funktion "Schalter", und wählen Sie "Token" () aus.</span><span class="sxs-lookup"><span data-stu-id="ef337-130">Then, select the function drop down and select " LunarModule" and then navigate to "TogglePlacementHints" function and select ToggleGameOBjects().</span></span>

![module4chapter5step3c](images/module4chapter5step3c.PNG)

8.  <span data-ttu-id="ef337-132">Wählen Sie als nächstes die Lunarcom_Completed Prefab in der Hierarchie aus, und navigieren Sie zum Skript "lunarcom Intent erkenzer" in Inspector, und ziehen Sie dann die Schaltflächen "launchroundbutton", "rel troundbutton" und "Platzierungs Hinweise" an ihre jeweiligen Orte.</span><span class="sxs-lookup"><span data-stu-id="ef337-132">Next, Select the Lunarcom_Completed prefab in Hierarchy and navigate to "Lunarcom Intent Recognizer" script in Inspector and then drag and drop  "LaunchRoundButton", "ResetRoundButton" and "Placement Hints" buttons to their respective places.</span></span>

![module4chapter5step4](images/module4chapter5step4.PNG)

9. <span data-ttu-id="ef337-134">Klicken Sie im Unity-Editor auf die Schaltfläche "Wiedergabe", und klicken Sie auf die Schaltfläche "Launcher", und geben Sie die Ausdrücke wie "Push-Raketenstart Schaltfläche", "Anzeigen eines Platzierungs Hinweises", "drücken Sie die Rest-Schaltfläche" oder andere Ausdrücke im Zusammenhang mit der Anforderung zum Starten, zurücksetzen oder</span><span class="sxs-lookup"><span data-stu-id="ef337-134">Press the play button in Unity Editor and click on the "Rocket" button and utter the phrases like "Push rocket launch button","show me a placement hint", "press the rest button" or any other phrases related to launch, reset or hint's request for the rocket launcher.</span></span>

![module4chapter5step5a](images/module4chapter5step5a.PNG)

![module4chapter5step5b](images/module4chapter5step5b.PNG)

![module4chapter5step5c](images/module4chapter5step5c.PNG)

## <a name="congratulations"></a><span data-ttu-id="ef337-138">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="ef337-138">Congratulations</span></span>

<span data-ttu-id="ef337-139">In dieser Lektion haben wir gelernt, wie Sie die KI-gestützten Sprachbefehle mit Sprachbefehlen verbinden, um Sie als Eingabemethode zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="ef337-139">In this lesson, we learned how to connect the AI-powered speech commands to voice commands to use it as an input method.</span></span> <span data-ttu-id="ef337-140">Nun kann unser Programm die Referenten als Sprachbefehle verwenden, um Eingaben für das Raketen Starter Programm zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="ef337-140">Now our program can use the speakers intent as voice commands to give inputs for the rocket launcher.</span></span>

