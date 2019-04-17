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
# <a name="using-the-windows-namespace-with-unity-apps-for-hololens"></a>Mithilfe des Windows-Namespaces mit Unity-apps für HoloLens

Diese Seite beschreibt das Nutzen von WinRT-APIs in Ihrem Unity-Projekt für HoloLens.

## <a name="conditionally-include-winrt-api-calls"></a>Bedingt gehören Sie WinRT-API-Aufrufe

WinRT-APIs wird nur in Builds von Unity-Projekt verwendet werden, die auf Windows 8, Windows 8.1 und die universelle Windows-Plattform abzielen. Jeder Code, den Sie im Unity-Skripts schreiben, die WinRT-APIs ausgerichtet ist, muss bedingt für nur diesen Builds enthalten sein. Dies erfolgt mit den Präprozessor NETFX_CORE oder WINDOWS_UWP-Definitionen. Diese Regel gilt für die mithilfe von Anweisungen sowie anderen Code.

Der folgende Codeausschnitt ist über die manuelle Unity-Seite für [universelle Windows-Plattform: WinRT-API in C# Skripts](http://docs.unity3d.com/Manual/windowsstore-scripts.html). In diesem Beispiel wird eine werbungs-ID zurückgegeben, jedoch nur auf Windows 8.0 oder höher Ziel Builds:

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Bearbeiten Sie Ihre Skripts in einem Unity C# Projekt

Wenn Sie ein Skript im Unity-Editor doppelklicken, wird standardmäßig das Skript in einem Editor-Projekt gestartet. Die WinRT-APIs wird angezeigt, aus zwei Gründen unbekannt sein: NETFX_CORE ist nicht in dieser Umgebung definiert, und das Projekt verweist nicht auf die Windows-Runtime. Bei Verwendung der [Export empfohlen und Einstellungen erstellt](exporting-and-building-a-unity-visual-studio-solution.md), und bearbeiten Sie die Skripts in diesem Projekt stattdessen, wird auch einen Verweis auf die Windows-Runtime; mit dieser Konfiguration vorhanden sind und NETFX_CORE definieren, WinRT-APIs für IntelliSense verfügbar.

Beachten Sie, dass Ihre Unity C# Projekt kann auch über Ihre Skripts mit F5 Debuggen in Visual Studio remote Debuggen verwendet werden. Wenn Sie nicht angezeigt, werden IntelliSense arbeiten zum erste Mal öffnen Sie Ihre Unity C# Projekt, schließen Sie das Projekt, und öffnen Sie es erneut. IntelliSense sollte arbeiten.

## <a name="see-also"></a>Siehe auch
* [Exportieren und Erstellen von Unity Visual Studio-Projektmappe](exporting-and-building-a-unity-visual-studio-solution.md)
