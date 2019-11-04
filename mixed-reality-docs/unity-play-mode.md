---
title: Unity-Wiedergabemodus
description: Verwenden Sie den Wiedergabemodus im Unity-Editor, um eine Vorschau der Änderungen auf einem Gerät anzuzeigen, ohne eine APP bereitzustellen.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Remoting, Holographic Remoting, Holographic Remoting Player
ms.openlocfilehash: 6164d7ae1bc2d9ac13135f17132aca089e63ecdf
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438226"
---
# <a name="unity-play-mode"></a>Unity-Wiedergabemodus

Eine schnelle Möglichkeit, an Ihrem Unity-Projekt zu arbeiten, ist die Verwendung des "Wiedergabemodus". Dadurch wird Ihre APP lokal im Unity-Editor auf Ihrem PC ausgeführt. Unity verwendet Holographic Remoting, um eine schnelle Möglichkeit zum Anzeigen einer Vorschau Ihrer Inhalte auf einem echten hololens-Gerät bereitzustellen. Der Wiedergabemodus kann auch mit einem Windows Mixed Reality-Headset verwendet werden, das an ihren Entwicklungs-PC angeschlossen ist.

## <a name="unity-play-mode-with-holographic-remoting"></a>Unity-Wiedergabemodus mit Holographic-Remoting

Mit Holographic Remoting können Sie Ihre APP auf den hololens erleben, während Sie im Unity-Editor auf Ihrem PC ausgeführt wird. Eingaben, Gesten, Stimme und räumliche zuordnungseingaben werden von ihren hololens an Ihren PC gesendet. Gerenderte Frames werden dann zurück an Ihre hololens gesendet. Dies ist eine gute Möglichkeit, Ihre APP schnell zu debuggen, ohne ein vollständiges Projekt zu entwickeln und bereitzustellen.
1. Wechseln Sie auf Ihren hololens zum **Microsoft Store** , und installieren Sie die **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** -app.
2. Starten Sie auf Ihren hololens die **Holographic Remoting Player** -app.
3. Wechseln Sie in Unity zum Menü **Fenster** , und wählen Sie **Holographic Emulation**aus.
4. Festlegen des **Emulations Modus** auf **Remote-zu-Gerät**.
5. Geben Sie für **Remote Computer**die IP-Adresse der hololens ein.
6. Klicken Sie auf **Verbinden**. Der **Verbindungs Status** sollte in **verbunden** angezeigt werden, und der Bildschirm wechselt in den hololens leer.
7. Klicken Sie auf die **Wiedergabe** Schaltfläche, um den Wiedergabemodus zu starten und die APP auf Ihren hololens zu erleben

Holographic Remoting erfordert eine schnelle PC-und Wi-Fi-Verbindung. Ausführliche Informationen finden Sie unter [Holographic Remoting Player](holographic-remoting-player.md) .

Um optimale Ergebnisse zu erzielen, stellen Sie sicher, dass Ihre APP den [Fokuspunkt](focus-point-in-unity.md)ordnungsgemäß festlegt. Dies hilft Holographic Remoting bei der optimalen Anpassung Ihrer Szene an die Latenz Ihrer drahtlosen Verbindung.

## <a name="see-also"></a>Weitere Informationen
* [Holographic Remoting-Player](holographic-remoting-player.md)
