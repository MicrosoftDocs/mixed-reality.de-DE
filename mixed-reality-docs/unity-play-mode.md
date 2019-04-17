---
title: Unity-Spielmodus
description: Verwendung des Modus spielen in der Unity-Editor, Ihre Änderungen auf einem Gerät ohne Bereitstellen einer app.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Remoting, holographic Remoting, holographic Remoting-player
ms.openlocfilehash: c118c4af61c6eb2706ef851a6654c18ff7313453
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593356"
---
# <a name="unity-play-mode"></a>Unity-Spielmodus

Eine schnelle Möglichkeit zum Arbeiten in Ihrem Unity-Projekt ist die Verwendung von "Modus wiedergeben". Dies führt Ihre app lokal im Unity-Editor auf Ihrem PC. Unity wird Holographic Remoting verwendet, um eine schnelle Möglichkeit, Ihre Inhalte auf einem echten Gerät mit HoloLens Vorschau bereitzustellen.

## <a name="unity-play-mode-with-holographic-remoting"></a>Unity-Spielmodus Holographic-Remoting

Bei Holographic-Remoting können Sie Ihre app auf die HoloLens, kommen, während der Ausführung im Unity-Editor auf Ihrem PC. Blicke, Gesten, Sprach- und räumliche Zuordnung, die Eingabe wird von Ihrem HoloLens auf Ihren PC gesendet. Gerenderter Frames werden dann zurück an Ihre HoloLens gesendet. Dies ist eine hervorragende Möglichkeit, Ihre app schnell zu debuggen, ohne die Erstellung und Bereitstellung von einem vollständigen Projekt.
1. Ihre HoloLens, wechseln Sie zu der **Microsoft Store** herunter, und Installieren der **[Holographic Remoting-Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.
2. Starten Sie auf Ihre HoloLens, die **Holographic Remoting-Player** app.
3. Wechseln Sie in Unity, zu der **Fenster** Menü **Holographic Emulation**.
4. Legen Sie **Emulationsmodus** zu **Gerät Remote**.
5. Für **Remotecomputer**, geben Sie die IP-Adresse Ihrer HoloLens.
6. Klicken Sie auf **Verbinden**. Daraufhin sollte **Verbindungsstatus** ändern in **verbunden** und der Bildschirm wechseln in der HoloLens leer angezeigt.
7. Klicken Sie auf die **spielen** Schaltfläche zum Starten von Spielen-Modus, und erleben die app auf Ihrem HoloLens.

Holographic Remoting ist eine schnelle PC und Wi-Fi-Verbindung erforderlich. Finden Sie unter [Holographic Remoting-Player](holographic-remoting-player.md) Weitere Details.

Für optimale Ergebnisse sicherzustellen, dass Ihre app ordnungsgemäß legt die [konzentrieren Punkt](focus-point-in-unity.md). Dadurch wird die Holographic Remoting zu Ihrer Szene, um die Latenz der drahtlosen Verbindung am besten passen.

## <a name="see-also"></a>Siehe auch
* [Holographic Remoting-Player](holographic-remoting-player.md)
