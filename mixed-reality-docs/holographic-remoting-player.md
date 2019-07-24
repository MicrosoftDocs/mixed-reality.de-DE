---
title: Holographic Remoting Player
description: Der Holographic Remoting Player ist eine begleitende APP, die eine Verbindung mit PC-Apps und spielen herstellt, die Holographic Remoting unterstützen. Holographic Remoting streamt Holographic Content per Wi-Fi-Verbindung von einem PC zu Ihren Microsoft hololens in Echtzeit.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Hololens, Remoting, Holographic Remoting
ms.openlocfilehash: b8354295f9752e73cc9b34c1769254e49808b63f
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813718"
---
# <a name="holographic-remoting-player"></a>Holographic Remoting Player

Der Holographic Remoting Player ist eine begleitende APP, die eine Verbindung mit PC-Apps und spielen herstellt, die Holographic Remoting unterstützen. Holographic Remoting streamt Holographic Content per Wi-Fi-Verbindung von einem PC zu Ihren Microsoft hololens in Echtzeit.

Der Holographic Remoting Player kann nur mit PC-Apps verwendet werden, die speziell für die Unterstützung von Holographic Remoting entwickelt wurden.

Der Holographic Remoting Player ist für hololens und hololens 2 verfügbar.  PC-Apps, die Holographic-Remoting mit hololens unterstützen, müssen aktualisiert werden, um Holographic remtoting mit hololens 2 zu unterstützen.  Wenden Sie sich an Ihren app-Anbieter, wenn Sie Fragen dazu haben, welche Versionen unterstützt werden.

## <a name="connecting-to-the-holographic-remoting-player"></a>Herstellen einer Verbindung mit dem Holographic Remoting Player

Befolgen Sie die Anweisungen Ihrer APP, um eine Verbindung mit dem Holographic Remoting Player herzustellen. Sie müssen die IP-Adresse Ihres hololens-Geräts eingeben, das Sie auf dem Hauptbildschirm des Remoting-Players wie folgt sehen können:

![Holographic Remoting Player](images/holographicremotingplayer.png)

Wenn der Hauptbildschirm angezeigt wird, wissen Sie, dass Sie keine app verbunden haben.

Beachten Sie, dass die Holographic-remotingverbindung **nicht verschlüsselt**ist. Sie sollten Holographic Remoting immer über eine sichere WLAN-Verbindung verwenden, die Sie als vertrauenswürdig einstufen.

## <a name="quality-and-performance"></a>Qualität und Leistung

Die Qualität und die Leistung Ihrer Benutzeroberflächen variieren je nach den drei Faktoren:
* **Die holografische Darstellung, die Sie ausführen** : apps, die hochauflösende oder sehr ausführliche Inhalte Renderingfunktionen darstellen, benötigen möglicherweise einen schnelleren PC oder eine schnellere drahtlose Verbindung.
* **Die Hardware Ihres PCs** : Ihr PC muss in der Lage sein, ihre holografische Darstellung bei 60 Frames pro Sekunde auszuführen und zu codieren. Für eine Grafikkarte empfehlen wir in der Regel eine GeForce GTX 970 oder AMD Radeon R9 290 oder höher. Auch hier ist für ihre jeweilige Obergrenze möglicherweise eine höhere oder niedrigere Karte erforderlich.
* **Ihre Wi-Fi-Verbindung** : Ihre Holographic-Darstellung wird über Wi-Fi gestreamt. Verwenden Sie ein schnelles Netzwerk mit geringer Überlastung, um die Qualität zu maximieren. Wenn Sie einen PC verwenden, der über ein Ethernet-Kabel anstatt über Wi-Fi verbunden ist, kann die Qualität ebenfalls verbessern.

## <a name="diagnostics"></a>Diagnose

Zum Messen der Qualität der Verbindung **Geben Sie "Diagnose aktivieren"** auf dem Hauptbildschirm des Holographic Remoting Players ein. Wenn die Diagnose aktiviert ist, werden Sie von der App angezeigt:
* **Fps** : die durchschnittliche Anzahl der gerenderten Frames, die der Remoting-Player empfängt und pro Sekunde rendert. Der ideale Wert ist 60 fps.
* **Latenz** Zeit: die durchschnittliche Zeitspanne, die ein Frame benötigt, um von Ihrem PC auf die hololens zu gelangen. Je niedriger der bessere. Dies hängt größtenteils von Ihrem Wi-Fi-Netzwerk ab.

Auf dem Hauptbildschirm können Sie beispielsweise **"Diagnose deaktivieren"** , um die Diagnose zu deaktivieren.

## <a name="pc-system-requirements"></a>PC-System Anforderungen
* Auf dem PC **muss** Windows 10 Anniversary Update oder höher ausgeführt werden.
* Wir empfehlen eine GeForce GTX 970-oder AMD Radeon R9 290-oder bessere Grafikkarte.
* Wir empfehlen Ihnen, Ihren PC über Ethernet mit Ihrem Netzwerk zu verbinden, um die Anzahl der drahtlosen Hops zu verringern.

## <a name="see-also"></a>Siehe auch
* [Holographic Remoting-Software – Lizenzbedingungen](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzbestimmungen von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
