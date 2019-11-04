---
title: WinRT-APIs mit Unity für hololens
description: Erläutert, wie Sie WinRT-APIs (den Windows-Namespace) in Ihrem Unity-Projekt für hololens verwenden.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, Windows Mixed Reality, API, Exemplarische Vorgehensweise
ms.openlocfilehash: 73764d191813f6dcae750e74ce3181af987c9e0e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437236"
---
# <a name="winrt-apis-with-unity-for-hololens"></a><span data-ttu-id="01988-104">WinRT-APIs mit Unity für hololens</span><span class="sxs-lookup"><span data-stu-id="01988-104">WinRT APIs with Unity for HoloLens</span></span>

<span data-ttu-id="01988-105">Auf dieser Seite wird beschrieben, wie Sie WinRT-APIs in Ihrem Unity-Projekt für hololens verwenden.</span><span class="sxs-lookup"><span data-stu-id="01988-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="mixed-reality-apis"></a><span data-ttu-id="01988-106">Mixed Reality-APIs</span><span class="sxs-lookup"><span data-stu-id="01988-106">Mixed Reality APIs</span></span>

<span data-ttu-id="01988-107">Eine gemischte Realität fokussierte Teilmenge der Windows SDK wurde in einer .NET Standard 2,0-kompatiblen Projektion zur Verfügung gestellt, die Sie in Ihrem Projekt ohne Präprozessordirektiven verwenden können.</span><span class="sxs-lookup"><span data-stu-id="01988-107">A Mixed Reality focused subset of the Windows SDK has been made available in a .NET Standard 2.0 compatible projection, which you can use in your project without preprocessor directives.</span></span> <span data-ttu-id="01988-108">Dies umfasst die meisten APIs in den Namespaces "Windows. perception" und "Windows. UI. Input. Spatial" und kann erweitert werden, um in Zukunft weitere APIs einzubeziehen.</span><span class="sxs-lookup"><span data-stu-id="01988-108">This includes most APIs in the Windows.Perception and Windows.UI.Input.Spatial namespaces, and may expand to include additional APIs in the future.</span></span> <span data-ttu-id="01988-109">Die projizierten APIs können während der Ausführung im Editor verwendet werden, was die Verwendung des [Wiedergabemodus](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode)ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="01988-109">The projected APIs can be used while running in the Editor, which enables the use of [Play Mode](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode).</span></span> <span data-ttu-id="01988-110">Um diese Projektion zu verwenden, nehmen Sie die folgenden Änderungen am Projekt vor:</span><span class="sxs-lookup"><span data-stu-id="01988-110">To use this projection, make the following modifications to your project:</span></span>

1) <span data-ttu-id="01988-111">Fügen Sie mithilfe [von nuget für Unity](https://github.com/GlitchEnzo/NuGetForUnity)einen Verweis auf das nuget-Paket [Microsoft. Windows. mixedreality. dotnetwinrt](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) hinzu.</span><span class="sxs-lookup"><span data-stu-id="01988-111">Add a reference to the [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span>
2) <span data-ttu-id="01988-112">Verweise auf den `Windows`-Namespace mit `Microsoft.`Präfix:</span><span class="sxs-lookup"><span data-stu-id="01988-112">Prefix references to the `Windows` namespace with `Microsoft.`:</span></span>
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) <span data-ttu-id="01988-113">Ersetzen Sie Native Zeiger Umwandlungen durch `FromNativePtr`:</span><span class="sxs-lookup"><span data-stu-id="01988-113">Replace native pointer casts with `FromNativePtr`:</span></span>
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="01988-114">Bedingtes Einschließen von WinRT-API-aufrufen</span><span class="sxs-lookup"><span data-stu-id="01988-114">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="01988-115">Alternativ können WinRT-APIs für Unity-Projekte genutzt werden, die für die universelle Windows-Plattform-und Xbox One-Plattform mithilfe von Präprozessordirektiven erstellt wurden. Jeder Code, den Sie in Unity-Skripts schreiben, die auf WinRT-APIs abzielen, muss nur für diese Builds bedingt eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="01988-115">Alternatively, WinRT APIs can be leveraged for Unity projects built for the Universal Windows Platform and Xbox One platform by using preprocessor directives; any code that you write in Unity scripts that target WinRT APIs must be conditionally included for only those builds.</span></span> 

<span data-ttu-id="01988-116">Dies kann über zwei Schritte in Unity erfolgen:</span><span class="sxs-lookup"><span data-stu-id="01988-116">This can be done via two steps in Unity:</span></span>
1) <span data-ttu-id="01988-117">Der API-Kompatibilitäts Grad muss in den Player Einstellungen auf **.NET 4,6** oder **.NET Standard 2,0** festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="01988-117">API compatibility level must be set to **.NET 4.6** or **.NET Standard 2.0** in the player settings</span></span>
    - <span data-ttu-id="01988-118">**Bearbeiten** Sie > **Projekteinstellungen** > **Player** > **Konfigurations** > **API-Kompatibilitäts Grad** auf **.NET 4,6** oder **.NET Standard 2,0**</span><span class="sxs-lookup"><span data-stu-id="01988-118">**Edit** > **Project Settings** > **Player** > **Configuration** > **Api Compatibility Level** to **.NET 4.6** or **.NET Standard 2.0**</span></span>
2) <span data-ttu-id="01988-119">Die Präprozessordirektive **ENABLE_WINMD_SUPPORT** muss alle mit WinRT ausgelnelten Code umschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="01988-119">The preprocessor directive **ENABLE_WINMD_SUPPORT** must be wrapped around any WinRT-leveraged code</span></span>

<span data-ttu-id="01988-120">Der folgende Code Ausschnitt befindet sich auf der manuellen Seite von Unity für [universelle Windows-Plattform: WinRT- C# API in Skripts](https://docs.unity3d.com/Manual/windowsstore-scripts.html).</span><span class="sxs-lookup"><span data-stu-id="01988-120">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](https://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="01988-121">In diesem Beispiel wird eine Werbe-ID zurückgegeben, jedoch nur für UWP-und Xbox One-Builds:</span><span class="sxs-lookup"><span data-stu-id="01988-121">In this example, an advertising ID is returned, but only on UWP and Xbox One builds:</span></span>

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="01988-122">Bearbeiten von Skripts in einem C# Unity-Projekt</span><span class="sxs-lookup"><span data-stu-id="01988-122">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="01988-123">Wenn Sie im Unity-Editor auf ein Skript doppelklicken, wird das Skript standardmäßig in einem Editor-Projekt gestartet.</span><span class="sxs-lookup"><span data-stu-id="01988-123">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="01988-124">Die WinRT-APIs scheinen unbekannt zu sein, da das Visual Studio-Projekt nicht auf das Windows-Runtime verweist.</span><span class="sxs-lookup"><span data-stu-id="01988-124">The WinRT APIs will appear to be unknown because the Visual Studio project does not reference the Windows Runtime.</span></span> <span data-ttu-id="01988-125">Außerdem ist die **ENABLE_WINMD_SUPPORT** -Direktive nicht definiert, und alle *#if* umschließenden Codes werden ignoriert, bis Sie Ihr Projekt in eine UWP-Visual Studio-Projekt Mappe erstellen.</span><span class="sxs-lookup"><span data-stu-id="01988-125">Further, the **ENABLE_WINMD_SUPPORT** directive will be undefined and any *#if* wrapped code will be ignored until you build your project into a UWP Visual Studio solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="01988-126">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="01988-126">See also</span></span>
* [<span data-ttu-id="01988-127">Exportieren und Erstellen einer Unity-Projektmappe für Visual Studio</span><span class="sxs-lookup"><span data-stu-id="01988-127">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="01988-128">Windows-Runtime Unterstützung von Unity</span><span class="sxs-lookup"><span data-stu-id="01988-128">Windows Runtime Support Unity</span></span>](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)
