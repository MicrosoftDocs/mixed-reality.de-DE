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
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a>Verwenden des Windows-Namespace mit Unity-Apps für hololens

Auf dieser Seite wird beschrieben, wie Sie WinRT-APIs in Ihrem Unity-Projekt für hololens verwenden.

## <a name="conditionally-include-winrt-api-calls"></a>Bedingtes Einschließen von WinRT-API-aufrufen

WinRT-APIs können für Unity-Projekte genutzt werden, die für die universelle Windows-Plattform und Xbox One-Plattform erstellt wurden. Jeder Code, den Sie in Unity-Skripts schreiben, die auf WinRT-APIs abzielen, muss nur für diese Builds bedingt eingeschlossen werden. 

Dies kann über zwei Schritte in Unity erfolgen:
1) Der API-Kompatibilitäts Grad muss in den Player Einstellungen auf **.NET 4,6** oder **.NET Standard 2,0** festgelegt werden.
    - **Bearbeiten** >  >  >      Sie den Kompatibilitäts Grad der Projekt Einstellungs Player-Konfigurations-API auf .NET 4,6 oder .NET Standard 2,0 > 
2) Die Präprozessordirektive **ENABLE_WINMD_SUPPORT** muss alle mit WinRT ausgelnelten Code umschlossen werden.

Der folgende Code Ausschnitt befindet sich auf der manuellen Seite von Unity [für universelle Windows-Plattform: WinRT-API C# in](http://docs.unity3d.com/Manual/windowsstore-scripts.html)Skripts. In diesem Beispiel wird eine Werbe-ID zurückgegeben, jedoch nur für UWP-und Xbox One-Builds:

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Bearbeiten von Skripts in einem C# Unity-Projekt

Wenn Sie im Unity-Editor auf ein Skript doppelklicken, wird das Skript standardmäßig in einem Editor-Projekt gestartet. Die WinRT-APIs scheinen unbekannt zu sein, da das Visual Studio-Projekt nicht auf das Windows-Runtime verweist. Außerdem ist die **ENALBE_WINMD_SUPPORT** -Direktive nicht definiert, und alle *#if* umschließenden Codes werden ignoriert, bis Sie Ihr Projekt in eine UWP-Visual Studio-Projekt Mappe erstellen.

## <a name="see-also"></a>Siehe auch
* [Exportieren und Erstellen einer Unity-Projektmappe für Visual Studio](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows-Runtime Unterstützung von Unity](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)