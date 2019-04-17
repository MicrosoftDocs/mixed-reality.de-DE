---
title: Mithilfe des Windows-Namespaces mit Unity-apps für HoloLens
description: Erläutert das Verwenden von WinRT-APIs in Ihrem Unity-Projekt für HoloLens.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, Windows mixed Reality,-API, exemplarische Vorgehensweise
ms.openlocfilehash: ed65b5995d74c54057a49b878c1206d0f06394ca
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594173"
---
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a><span data-ttu-id="1edfc-104">Mithilfe des Windows-Namespaces mit Unity-apps für HoloLens</span><span class="sxs-lookup"><span data-stu-id="1edfc-104">Using the Windows namespace with Unity apps for HoloLens</span></span>

<span data-ttu-id="1edfc-105">Diese Seite beschreibt das Nutzen von WinRT-APIs in Ihrem Unity-Projekt für HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1edfc-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="1edfc-106">Bedingt gehören Sie WinRT-API-Aufrufe</span><span class="sxs-lookup"><span data-stu-id="1edfc-106">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="1edfc-107">WinRT-APIs wird nur in Builds von Unity-Projekt verwendet werden, die auf Windows 8, Windows 8.1 und die universelle Windows-Plattform abzielen. Jeder Code, den Sie im Unity-Skripts schreiben, die WinRT-APIs ausgerichtet ist, muss bedingt für nur diesen Builds enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="1edfc-107">WinRT APIs will only be used in Unity project builds that target Windows 8, Windows 8.1, or the Universal Windows Platform; any code that you write in Unity scripts that targets WinRT APIs must be conditionally included for only those builds.</span></span> <span data-ttu-id="1edfc-108">Dies erfolgt mit den Präprozessor NETFX_CORE oder WINDOWS_UWP-Definitionen.</span><span class="sxs-lookup"><span data-stu-id="1edfc-108">This is done using the NETFX_CORE or WINDOWS_UWP preprocessor definitions.</span></span> <span data-ttu-id="1edfc-109">Diese Regel gilt für die mithilfe von Anweisungen sowie anderen Code.</span><span class="sxs-lookup"><span data-stu-id="1edfc-109">This rule applies to using statements, as well as other code.</span></span>

<span data-ttu-id="1edfc-110">Der folgende Codeausschnitt ist über die manuelle Unity-Seite für [universelle Windows-Plattform: WinRT-API in C# Skripts](http://docs.unity3d.com/Manual/windowsstore-scripts.html).</span><span class="sxs-lookup"><span data-stu-id="1edfc-110">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](http://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="1edfc-111">In diesem Beispiel wird eine werbungs-ID zurückgegeben, jedoch nur auf Windows 8.0 oder höher Ziel Builds:</span><span class="sxs-lookup"><span data-stu-id="1edfc-111">In this example, an advertising ID is returned, but only on Windows 8.0 or higher target builds:</span></span>

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if NETFX_CORE
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="1edfc-112">Bearbeiten Sie Ihre Skripts in einem Unity C# Projekt</span><span class="sxs-lookup"><span data-stu-id="1edfc-112">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="1edfc-113">Wenn Sie ein Skript im Unity-Editor doppelklicken, wird standardmäßig das Skript in einem Editor-Projekt gestartet.</span><span class="sxs-lookup"><span data-stu-id="1edfc-113">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="1edfc-114">Die WinRT-APIs wird angezeigt, aus zwei Gründen unbekannt sein: NETFX_CORE ist nicht in dieser Umgebung definiert, und das Projekt verweist nicht auf die Windows-Runtime.</span><span class="sxs-lookup"><span data-stu-id="1edfc-114">The WinRT APIs will appear to be unknown for two reasons: NETFX_CORE is not defined in this environment, and the project does not reference the Windows Runtime.</span></span> <span data-ttu-id="1edfc-115">Bei Verwendung der [Export empfohlen und Einstellungen erstellt](exporting-and-building-a-unity-visual-studio-solution.md), und bearbeiten Sie die Skripts in diesem Projekt stattdessen, wird auch einen Verweis auf die Windows-Runtime; mit dieser Konfiguration vorhanden sind und NETFX_CORE definieren, WinRT-APIs für IntelliSense verfügbar.</span><span class="sxs-lookup"><span data-stu-id="1edfc-115">If you use the [recommended export and built settings](exporting-and-building-a-unity-visual-studio-solution.md), and edit the scripts in that project instead, it will define NETFX_CORE and also include a reference to the Windows Runtime; with this configuration in place, WinRT APIs will be available for IntelliSense.</span></span>

<span data-ttu-id="1edfc-116">Beachten Sie, dass Ihre Unity C# Projekt kann auch über Ihre Skripts mit F5 Debuggen in Visual Studio remote Debuggen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1edfc-116">Note that your Unity C# project can also be used to debug through your scripts using F5 remote debugging in Visual Studio.</span></span> <span data-ttu-id="1edfc-117">Wenn Sie nicht angezeigt, werden IntelliSense arbeiten zum erste Mal öffnen Sie Ihre Unity C# Projekt, schließen Sie das Projekt, und öffnen Sie es erneut.</span><span class="sxs-lookup"><span data-stu-id="1edfc-117">If you do not see IntelliSense working the first time that you open your Unity C# project, close the project and re-open it.</span></span> <span data-ttu-id="1edfc-118">IntelliSense sollte arbeiten.</span><span class="sxs-lookup"><span data-stu-id="1edfc-118">IntelliSense should start working.</span></span>

## <a name="see-also"></a><span data-ttu-id="1edfc-119">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1edfc-119">See also</span></span>
* [<span data-ttu-id="1edfc-120">Exportieren und Erstellen von Unity Visual Studio-Projektmappe</span><span class="sxs-lookup"><span data-stu-id="1edfc-120">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
