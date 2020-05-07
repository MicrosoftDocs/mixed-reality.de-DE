---
title: Spracheingabe
description: Erläutert die Verwendung von Spracheingaben.
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, hololens
ms.openlocfilehash: d61a9f9d40c76c8872ff0a1b39d65f95ae88d2b7
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835311"
---
# <a name="voice-input"></a><span data-ttu-id="ab16b-104">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="ab16b-104">Voice Input</span></span>

<span data-ttu-id="ab16b-105">Um die Spracherkennung in hololens zu aktivieren, muss der Entwickler "Mikrofon" im Unreal-Editor Unterprojekt Einstellungen > Plattform > hololens > Funktionen aktivieren.</span><span class="sxs-lookup"><span data-stu-id="ab16b-105">To enable speech recognition on HoloLens, the developer needs to enable “Microphone” in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span> <span data-ttu-id="ab16b-106">Auf dem Gerät muss auch die Spracherkennung in den Einstellungen > Datenschutz > Sprache aktiviert sein und die englische Sprache verwenden.</span><span class="sxs-lookup"><span data-stu-id="ab16b-106">The device must also have Speech recognition enabled in Settings > Privacy > Speech and use the English language.</span></span>

![Einstellungen für die Windows-Spracherkennung](images/unreal/speech-recognition-settings.png)

<span data-ttu-id="ab16b-108">Es wird empfohlen, die Online Spracherkennung auch für die bestmögliche Qualität des Dienstanbieter zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="ab16b-108">It’s recommended to enable Online speech recognition too for the best possible quality of the service.</span></span> <span data-ttu-id="ab16b-109">Technische Details zur Spracherkennung in hololens finden Sie [hier](voice-input.md) .</span><span class="sxs-lookup"><span data-stu-id="ab16b-109">Technical details for speech recognition on HoloLens can be found [here](voice-input.md)</span></span>

<span data-ttu-id="ab16b-110">Dem Benutzer wird dann ein Dialogfeld angezeigt, in dem das Mikrofon beim ersten Start der Anwendung aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="ab16b-110">Then user will see a dialog about enabling the microphone when the application first starts.</span></span> <span data-ttu-id="ab16b-111">Wenn ein Benutzer "Ja" auswählt, beginnt die Anwendung mit der Spracheingabe.</span><span class="sxs-lookup"><span data-stu-id="ab16b-111">If a user selects Yes, the application will begin getting voice input.</span></span>

<span data-ttu-id="ab16b-112">Die Spracheingabe erfordert keine spezielle Windows Mixed Reality-API und basiert stattdessen auf der vorhandenen API für die Eingabe Zuordnung von Unreal Engine 4.</span><span class="sxs-lookup"><span data-stu-id="ab16b-112">Speech input doesn’t require a special Windows Mixed Reality API and is instead built upon the existing Unreal Engine 4 Input mapping API.</span></span> <span data-ttu-id="ab16b-113">Details zur Verwendung der Eingabe-API finden Sie [hier](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html) .</span><span class="sxs-lookup"><span data-stu-id="ab16b-113">Details on how to use the Input API are [here](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html)</span></span>

<span data-ttu-id="ab16b-114">Sprach Zuordnungen wurden dem Bindungs Abschnitt der Engine – Input unter Action and Axis Mappings hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="ab16b-114">Speech Mappings have been added to the Bindings section of Engine – Input below Action and Axis Mappings.</span></span> 

![UE4-Engine-Eingabeeinstellungen](images/unreal/engine-input.png)
 
<span data-ttu-id="ab16b-116">Im folgenden finden Sie ein Beispiel für eine hinzugefügte Überwachung der Welt "Jump".</span><span class="sxs-lookup"><span data-stu-id="ab16b-116">Here is an example of added monitoring for the world “jump”.</span></span> <span data-ttu-id="ab16b-117">Alle englischen Wörter oder kurzen Sätze können verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ab16b-117">Any English word(s) or short sentences can be used.</span></span> 

<span data-ttu-id="ab16b-118">Nachdem eine sprach Zuordnung über Projekteinstellungen hinzugefügt wurde, kann ein Entwickler standardmäßige Unreal Logic verwenden, um die Eingabe zu verarbeiten, wie im folgenden Beispiel gezeigt:</span><span class="sxs-lookup"><span data-stu-id="ab16b-118">After a Speech Mapping is added via Project Settings, a developer can then use standard Unreal logic to handle the input, as in the following example:</span></span> 
 
![Einfache Aktion für Stimme](images/unreal/input-action-bp.png)
