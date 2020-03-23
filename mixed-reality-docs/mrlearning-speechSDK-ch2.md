---
title: 'Tutorials zu Azure Speech-Diensten: 2 Hinzufügen eines Offlinemodus für die lokale Sprache-zu-Text-Übersetzung'
description: In diesem Kurs erfahren Sie, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 75ddce9063bb9d33f5fe2343fe30178222a5f8ac
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031623"
---
# <a name="2-using-speech-recognition-to-execute-commands"></a><span data-ttu-id="9f508-105">2. Verwenden der Spracherkennung zum Ausführen von Befehlen</span><span class="sxs-lookup"><span data-stu-id="9f508-105">2. Using speech recognition to execute commands</span></span>

<span data-ttu-id="9f508-106">In diesem Tutorial fügen Sie die Möglichkeit hinzu, Befehle mithilfe der Azure-Spracherkennung auszuführen, sodass Sie basierend auf dem von Ihnen definierten Wort oder Ausdruck eine Aktion auslösen können.</span><span class="sxs-lookup"><span data-stu-id="9f508-106">In this tutorial, you will add the ability to execute commands using Azure speech recognition which will allow you to make something happen based on the word or phrase you define.</span></span>

## <a name="objectives"></a><span data-ttu-id="9f508-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="9f508-107">Objectives</span></span>

* <span data-ttu-id="9f508-108">Erfahren, wie die Azure-Spracherkennung zum Ausführen von Befehlen verwendet werden kann</span><span class="sxs-lookup"><span data-stu-id="9f508-108">Learn how Azure speech recognition can be used to execute commands</span></span>

## <a name="instructions"></a><span data-ttu-id="9f508-109">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="9f508-109">Instructions</span></span>

<span data-ttu-id="9f508-110">Wählen Sie im Hierarchiefenster das **Lunarcom**-Objekt aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um dem Lunarcom-Objekt die Komponente **Lunarcom Wake Word Recognizer (Script)** hinzuzufügen und sie wie folgt zu konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="9f508-110">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Wake Word Recognizer (Script)** component to the Lunarcom object and configure it as follows:</span></span>

* <span data-ttu-id="9f508-111">Geben Sie im Feld **Wake Word** (Wort zum Aufwecken) einen passenden Ausdruck ein, z. B. _Terminal aktivieren_.</span><span class="sxs-lookup"><span data-stu-id="9f508-111">In the **Wake Word** field, enter a suitable phrase, for example, _Activate terminal_.</span></span>
* <span data-ttu-id="9f508-112">Geben Sie im Feld **Dismiss Word** (Wort zum Schließen) einen passenden Ausdruck ein, z. B. _Terminal schließen_.</span><span class="sxs-lookup"><span data-stu-id="9f508-112">In the **Dismiss Word** field, enter a suitable phrase, for example, _Dismiss terminal_.</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="9f508-114">Die Komponente „Lunarcom Wake Word Recognizer (Script)“ ist kein Bestandteil des MRTK.</span><span class="sxs-lookup"><span data-stu-id="9f508-114">The Lunarcom Wake Word Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="9f508-115">Sie wurde zusammen mit den Ressourcen für dieses Tutorial zur Verfügung gestellt.</span><span class="sxs-lookup"><span data-stu-id="9f508-115">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="9f508-116">Wenn Sie jetzt in den Spielmodus wechseln, wie im vorherigen Tutorial, ist der Terminalbereich standardmäßig aktiviert. Sie können ihn jetzt jedoch deaktivieren, indem Sie das Wort zum Schließen aussprechen, **Terminal schließen**:</span><span class="sxs-lookup"><span data-stu-id="9f508-116">If you now enter Game mode, as in the previous tutorial, the terminal panel is enabled by default, but you can now disable it by saying the Dismiss Word, **Dismiss terminal**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-2.png)

<span data-ttu-id="9f508-118">Und es erneut aktivieren, indem Sie das Wort zum Aufwecken sprechen **Terminal aktivieren**:</span><span class="sxs-lookup"><span data-stu-id="9f508-118">And enable it again by saying the Wake Word, **Activate terminal**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="9f508-120">Die Anwendung muss eine Verbindung mit Azure herstellen, achten Sie also darauf, dass Ihr Computer/Gerät mit dem Internet verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="9f508-120">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

> [!TIP]
> <span data-ttu-id="9f508-121">Wenn Sie davon ausgehen müssen, dass Sie häufig keine Verbindung mit Azure herstellen können, können Sie außerdem Sprachbefehle mithilfe von MRTK implementieren. Befolgen Sie dazu die Anweisungen unter [Aktivieren der Sprachbefehle](mrlearning-base-ch5.md#enabling-voice-commands).</span><span class="sxs-lookup"><span data-stu-id="9f508-121">If you anticipate frequently not being able to connect to Azure, you can also implement speech commands using MRTK by following the [Enabling Voice Commands](mrlearning-base-ch5.md#enabling-voice-commands) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="9f508-122">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="9f508-122">Congratulations</span></span>

<span data-ttu-id="9f508-123">Sie haben die von Azure unterstützten Sprachbefehle implementiert.</span><span class="sxs-lookup"><span data-stu-id="9f508-123">You have implemented speech commands powered by Azure.</span></span> <span data-ttu-id="9f508-124">Führen Sie die Anwendung auf Ihrem Gerät aus, um sicherzustellen, dass das Feature ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="9f508-124">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="9f508-125">Im nächsten Tutorial erfahren Sie, wie Sprache mithilfe von Azure-Sprachübersetzung übersetzt wird.</span><span class="sxs-lookup"><span data-stu-id="9f508-125">In the next tutorial, you will learn how to translate speech using Azure speech translation.</span></span>

[<span data-ttu-id="9f508-126">Nächstes Tutorial: 3. Hinzufügen der Sprachübersetzungskomponente von Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="9f508-126">Next Tutorial: 3. Adding the Azure Cognitive Services speech translation component</span></span>](mrlearning-speechSDK-ch3.md)
