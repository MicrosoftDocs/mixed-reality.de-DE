---
title: Holographic Remoting-Player
description: Der Holographic Remoting-Player ist eine Begleit-app, die eine Verbindung mit der PC-apps und Spiele, die Holographic Remoting unterstützen. Holographic Remoting streamt holographic Inhalte von einem PC in Ihrer Microsoft HoloLens in Echtzeit über eine Wi-Fi-Verbindung.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Remoting, Holographic Remoting
ms.openlocfilehash: 24213444686dd2e5dbda4016dd551a8ead8f305a
ms.sourcegitcommit: aba33a8ad1416f7598048ac35ae9ab1734bd5c37
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2019
ms.locfileid: "66270317"
---
# <a name="holographic-remoting-player"></a>Holographic Remoting-Player

Der Holographic Remoting-Player ist eine Begleit-app, die eine Verbindung mit der PC-apps und Spiele, die Holographic Remoting unterstützen. Holographic Remoting streamt holographic Inhalte von einem PC in Ihrer Microsoft HoloLens in Echtzeit über eine Wi-Fi-Verbindung.

Der Holographic Remoting-Player kann nur mit PC-apps verwendet werden, die speziell zur Unterstützung von Holographic Remoting.

Der Holographic Remoting-Player ist für HoloLens und HoloLens 2 verfügbar.  PC-apps, die Holographic Remoting mit HoloLens unterstützt zur Unterstützung von Holographic Remtoing mit HoloLens 2 aktualisiert werden müssen.  Wenden Sie sich an Ihren app-Anbieter, wenn Sie Fragen haben, die welche Versionen unterstützt werden.

## <a name="connecting-to-the-holographic-remoting-player"></a>Herstellen einer Verbindung mit der Holographic Remoting-Player

Führen Sie die Ihrer app-Anleitungen zum Verbinden mit der Holographic Remoting-Player. Sie benötigen die IP-Adresse des Geräts HoloLens eingeben, die Sie wie folgt auf den Remoting-Player-Hauptbildschirm sehen können:

![Holographic Remoting-Player](images/holographicremotingplayer.png)

Wenn Sie im Hauptbildschirm sehen, wissen Sie, dass Sie nicht über eine verbundene app verfügen.

Beachten Sie, dass die holographic Remotingverbindung **nicht verschlüsselt**. Sie sollten immer Holographic Remoting über eine sichere Wi-Fi-Verbindung verwenden, die Sie vertrauen.

## <a name="quality-and-performance"></a>Qualität und Leistung

Die Qualität und Leistung Ihrer Erfahrung variieren basierend auf drei Faktoren ab:
* **Sie führen holografischen Benutzeroberfläche** -Apps, die mit hoher Auflösung oder äußerst detaillierte Inhalt Rendern erfordern einen schnelleren PC oder schneller drahtlose Verbindung.
* **Ihre PC Hardware** -Ihr PC benötigt wird, in der Lage, ausführen und Ihre holografischen Benutzeroberfläche mit 60 Bildern pro Sekunde zu codieren. Für eine Grafikkarte empfehlen wir in der Regel eine GeForce GTX 970 oder AMD Radeon R9 290 oder höher. In diesem Fall möglicherweise Ihre bestimmte Umgebung eine höhere oder Low-End-Karte.
* **Die Wi-Fi-Verbindung** -Ihre holografischen Benutzeroberfläche über Wi-Fi gestreamt wird. Verwenden Sie ein schnelles Netzwerk mit niedriger Überlastung, um die Qualität zu maximieren. Verwenden Sie einen PC, der über ein Ethernetkabel verbunden ist, kann anstelle von Wi-Fi, auch Qualität verbessern.

## <a name="diagnostics"></a>Diagnose

Um die Qualität Ihrer Verbindung zu messen, z. B. **"Diagnose aktivieren"** zwar auf dem Hauptbildschirm des Holographic Remoting-Players. Wenn die Diagnose aktiviert wurde, wird die app Sie angezeigt:
* **FPS** : die durchschnittliche Anzahl der Einzelbilder, die der Remoting-Player empfangen wird und Rendern pro Sekunde. Ideal sind 60 FPS.
* **Latenz** : die durchschnittliche Länge der Zeit, die für einen Frame aus, um von Ihrem PC zu wechseln, um die HoloLens. Je niedriger, desto besser. Dies ist in hohem Maße abhängig von Ihrem Wi-Fi-Netzwerk.

Sie können auf dem Hauptbildschirm, sagen **"Deaktivieren der Diagnose"** zum Deaktivieren der Diagnose zu aktivieren.

## <a name="pc-system-requirements"></a>PC-Systemanforderungen
* Ihr PC **müssen** wird das Windows 10 Anniversary Update oder höher.
* Es wird empfohlen, eine GeForce GTX 970 oder AMD Radeon R9 290 oder bessere Grafikkarte.
* Es wird empfohlen, dass Sie eine solche mit Ihrem Netzwerk über Ethernet zum Reduzieren der Anzahl der Hops, die drahtlose Verbindung herstellen.

## <a name="see-also"></a>Siehe auch
* [Holographic Remoting-Software – Lizenzbedingungen](microsoft-holographic-remoting-software-license-terms.md)
* [Datenschutzbestimmungen von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
