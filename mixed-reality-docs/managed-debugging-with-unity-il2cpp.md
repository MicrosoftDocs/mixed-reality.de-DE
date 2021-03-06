---
title: Verwaltetes Debuggen mit Unity IL2CPP
description: In diesem Artikel wird beschrieben, wie Sie einen verwalteten Debugger in Ihrem Unity IL2CPP-UWP-Projekt ausführen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Unity, Visual Studio, Debugging, il2cpp
ms.openlocfilehash: 970d3000df995e7c6e331a41d10e25dc5aa370a8
ms.sourcegitcommit: 7e8b9de561cbc8483e84511f3e9cbd779f3a999f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/27/2019
ms.locfileid: "75502661"
---
# <a name="managed-debugging-with-unity-il2cpp"></a>Verwaltetes Debuggen mit Unity IL2CPP

Führen Sie die folgenden Schritte aus, um einen verwalteten Debugger an Ihren Unity IL2CPP UWP-Build anzufügen. Dieses Handbuch wurde ursprünglich für hololens und hololens 2 entwickelt.

1. Sie müssen sich in einem Netzwerk befinden, das [Multicast](https://en.wikipedia.org/wiki/Multicast)unterstützt.
1. Stellen Sie sicher, dass **internetclientserver** und **privatenetworkclientserver** in Unity unter den Funktionen der UWP-Veröffentlichungs Einstellungen eingeglichen werden.

    ![Funktionen der UWP-Veröffentlichungs Einstellungen](images/il2cpp-debugging-capabilities.png)

1. Konfigurieren Sie die Unity-UWP-Buildeinstellungen:
    - Development Build
    - Skriptdebugging
    - Auf verwalteten Debugger warten (optional)

    ![UWP-Buildeinstellungen](images/il2cpp-debugging-build.png)

1. Erstellen Sie in Unity.
1. Erstellen Sie die Visual Studio-Projekt Mappe, und stellen Sie Sie auf Ihrem Gerät bereit. Sie sollten mit den **Debug** -oder **Releasekonfigurationen** erstellen. Die **Master** Konfiguration deaktiviert den Unity-Profiler und kann ein optimales Debuggen verhindern. Überprüfen Sie optional das **Internet (Client & Server)** und **private Netzwerke (Client & Server)** in der Liste der Funktionen in "Package. appxmanifest" in der Projekt Mappe.
1. Starten Sie die APP auf Ihrem Gerät. Stellen Sie sicher, dass das Gerät mit dem Netzwerk verbunden ist, das mit dem PC verbunden ist.
1. Stellen Sie sicher, dass das Gerät nicht über USB mit dem PC verbunden **ist** .
1. Wechseln Sie zur Visual Studio-Projekt Mappe, die erstellt wird, wenn Sie auf ein Skript in Unity doppelklicken, wo Sie Ihre C# Skripts anzeigen und bearbeiten können.
1. Debug-> Unity-Debugger anfügen.

    ![Unity-Debugger anhängen](images/il2cpp-debugging-attach.png)

1. Wählen Sie in der Liste Ihr Gerät aus, und klicken Sie auf "OK"

    ![Geräteliste](images/il2cpp-debugging-machines.png)
