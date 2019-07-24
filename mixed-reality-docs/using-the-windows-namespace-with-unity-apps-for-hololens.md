---
title: Verwenden des Windows-Namespace mit Unity-Apps für hololens
description: Erläutert die Verwendung von WinRT-APIs in Ihrem Unity-Projekt für hololens.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, Windows Mixed Reality, API, Exemplarische Vorgehensweise
ms.openlocfilehash: fd25548de8eeb3c8157a3f9de283dc5004ed1180
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548738"
---
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a><span data-ttu-id="445bd-104">Verwenden des Windows-Namespace mit Unity-Apps für hololens</span><span class="sxs-lookup"><span data-stu-id="445bd-104">Using the Windows namespace with Unity apps for HoloLens</span></span>

<span data-ttu-id="445bd-105">Auf dieser Seite wird beschrieben, wie Sie WinRT-APIs in Ihrem Unity-Projekt für hololens verwenden.</span><span class="sxs-lookup"><span data-stu-id="445bd-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="445bd-106">Bedingtes Einschließen von WinRT-API-aufrufen</span><span class="sxs-lookup"><span data-stu-id="445bd-106">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="445bd-107">WinRT-APIs können für Unity-Projekte genutzt werden, die für die universelle Windows-Plattform und Xbox One-Plattform erstellt wurden. Jeder Code, den Sie in Unity-Skripts schreiben, die auf WinRT-APIs abzielen, muss nur für diese Builds bedingt eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="445bd-107">WinRT APIs can be leveraged for Unity projects built for the Universal Windows Platform and Xbox One platform; any code that you write in Unity scripts that target WinRT APIs must be conditionally included for only those builds.</span></span> 

<span data-ttu-id="445bd-108">Dies kann über zwei Schritte in Unity erfolgen:</span><span class="sxs-lookup"><span data-stu-id="445bd-108">This can be done via two steps in Unity:</span></span>
1) <span data-ttu-id="445bd-109">Der API-Kompatibilitäts Grad muss in den Player Einstellungen auf **.NET 4,6** oder **.NET Standard 2,0** festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="445bd-109">API compatibility level must be set to **.NET 4.6** or **.NET Standard 2.0** in the player settings</span></span>
    - <span data-ttu-id="445bd-110">**Bearbeiten** >  >  >      Sie den Kompatibilitäts Grad der Projekt Einstellungs Player-Konfigurations-API auf .NET 4,6 oder .NET Standard 2,0 > </span><span class="sxs-lookup"><span data-stu-id="445bd-110">**Edit** > **Project Settings** > **Player** > **Configuration** > **Api Compatibility Level** to **.NET 4.6** or **.NET Standard 2.0**</span></span>
2) <span data-ttu-id="445bd-111">Die Präprozessordirektive **ENABLE_WINMD_SUPPORT** muss alle mit WinRT ausgelnelten Code umschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="445bd-111">The preprocessor directive **ENABLE_WINMD_SUPPORT** must be wrapped around any WinRT-leveraged code</span></span>

<span data-ttu-id="445bd-112">Der folgende Code Ausschnitt befindet sich auf der manuellen Seite von Unity [für universelle Windows-Plattform: WinRT-API C# in](http://docs.unity3d.com/Manual/windowsstore-scripts.html)Skripts.</span><span class="sxs-lookup"><span data-stu-id="445bd-112">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](http://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="445bd-113">In diesem Beispiel wird eine Werbe-ID zurückgegeben, jedoch nur für UWP-und Xbox One-Builds:</span><span class="sxs-lookup"><span data-stu-id="445bd-113">In this example, an advertising ID is returned, but only on UWP and Xbox One builds:</span></span>

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if ENABLE_WINMD_SUPPORT
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="445bd-114">Bearbeiten von Skripts in einem C# Unity-Projekt</span><span class="sxs-lookup"><span data-stu-id="445bd-114">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="445bd-115">Wenn Sie im Unity-Editor auf ein Skript doppelklicken, wird das Skript standardmäßig in einem Editor-Projekt gestartet.</span><span class="sxs-lookup"><span data-stu-id="445bd-115">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="445bd-116">Die WinRT-APIs scheinen unbekannt zu sein, da das Visual Studio-Projekt nicht auf das Windows-Runtime verweist.</span><span class="sxs-lookup"><span data-stu-id="445bd-116">The WinRT APIs will appear to be unknown because the Visual Studio project does not reference the Windows Runtime.</span></span> <span data-ttu-id="445bd-117">Außerdem ist die **ENALBE_WINMD_SUPPORT** -Direktive nicht definiert, und alle *#if* umschließenden Codes werden ignoriert, bis Sie Ihr Projekt in eine UWP-Visual Studio-Projekt Mappe erstellen.</span><span class="sxs-lookup"><span data-stu-id="445bd-117">Further, the **ENALBE_WINMD_SUPPORT** directive will be undefined and any *#if* wrapped code will be ignored until you build your project into a UWP Visual Studio solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="445bd-118">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="445bd-118">See also</span></span>
* [<span data-ttu-id="445bd-119">Exportieren und Erstellen einer Unity-Projektmappe für Visual Studio</span><span class="sxs-lookup"><span data-stu-id="445bd-119">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="445bd-120">Windows-Runtime Unterstützung von Unity</span><span class="sxs-lookup"><span data-stu-id="445bd-120">Windows Runtime Support Unity</span></span>](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)