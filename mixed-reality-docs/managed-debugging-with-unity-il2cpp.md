---
title: Verwaltetes Debuggen mit Unity IL2CPP
description: In diesem Artikel wird beschrieben, wie einen verwalteten Debugger auf Ihr Unity-IL2CPP-UWP-Projekt ausgeführt wird.
author: keveleigh
ms.author: kurtie
ms.date: 06/13/19
ms.topic: article
keywords: Unity und visual Studio Debuggen, il2cpp
ms.openlocfilehash: eb4655633384fcb5d7f27546134e21857e5c5502
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148855"
---
# <a name="managed-debugging-with-unity-il2cpp"></a>Verwaltetes Debuggen mit Unity IL2CPP

Um Ihr Unity-IL2CPP-UWP-Build einen verwalteten Debugger anzufügen, gehen Sie wie folgt vor. Dieses Handbuch wurde ursprünglich für HoloLens und 2 für HoloLens entwickelt.

1. Sicherstellen, dass **InternetClientServer** und **PrivateNetworkClientServer** im Unity unter Einstellungen für die UWP-Veröffentlichungsfunktionen aktiviert sind.

    ![UWP-Einstellungen von Funktionen zu veröffentlichen](images/il2cpp-debugging-capabilities.png)

1. Konfigurieren Sie die UWP für Unity-Buildeinstellungen:
    - Development Build
    - Skriptdebugging
    - Warten Sie auf den Managed Debugger (optional)

    ![UWP-Buildeinstellungen](images/il2cpp-debugging-build.png)

1. Erstellen Sie in Unity.
1. Erstellen und Bereitstellen von Visual Studio-Projektmappe auf Ihrem Gerät. Sie sollten die Erstellung mit der **Debuggen** oder **Version** Konfigurationen. Die **Master** Konfiguration den Unity-Profiler deaktiviert und können verhindern, dass eine optimale Debuggen. Überprüfen Sie optional **Internet (Client & Server)** und **Private Netzwerke (Client & Server)** in der Liste "Funktionen" in "Package.appxmanifest" in der Projektmappe.
1. Die app auf Ihrem Gerät zu starten. Stellen Sie sicher, dass Ihr Gerät mit dem gleichen Netzwerk wie Ihr PC verbunden ist.
1. Stellen Sie sicher, dass das Gerät **nicht** auf Ihren PC über USB verbunden.
1. Wechseln Sie zu Visual Studio-Projektmappe, die erstellt wird, wenn Sie doppelklicken auf ein Skript in Unity klicken, können Sie anzeigen und Bearbeiten Ihrer C# Skripts.
1. Debuggen -> Unity-Debugger anfügen.

    ![Unity-Debugger anfügen](images/il2cpp-debugging-attach.png)

1. Wählen Sie Ihr Gerät in der Liste aus, und klicken Sie auf "OK" anfügen.

    ![Geräteliste](images/il2cpp-debugging-machines.png)
