---
title: Holographic Remoting Player
description: Der Holographic Remoting Player ist eine begleitende APP, die eine Verbindung mit PC-Apps und spielen herstellt, die Holographic Remoting unterstützen. Holographic Remoting streamt Holographic Content per Wi-Fi-Verbindung von einem PC zu Ihren Microsoft hololens in Echtzeit.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Hololens, Remoting, Holographic Remoting
ms.openlocfilehash: 88a9aa0bb058776a32016e51fc22bcb73f08ab85
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092368"
---
# <a name="holographic-remoting-player"></a>Holographic Remoting Player

>[!IMPORTANT]
>Holographic Remoting für hololens 2 ist eine wesentliche Versionsänderung. [Remote Anwendungen für **hololens (1st Gen)** ](add-holographic-remoting.md) müssen das nuget-Paketversion **1. x. x** und [Remote Anwendungen für **hololens 2** ](holographic-remoting-create-host.md) verwenden. **2. x. x**muss verwendet werden. Dies bedeutet, dass für hololens 2 geschriebene Remote Anwendungen nicht mit hololens (1st Gen) und umgekehrt kompatibel sind.

Der [Holographic Remoting Player](https://www.microsoft.com/p/holographic-remoting-player/9nblggh4sv40) ist eine begleitende APP, die eine Verbindung mit PC-Apps und spielen herstellt, die Holographic Remoting unterstützen. Holographic Remoting streamt Holographic Content per Wi-Fi-Verbindung von einem PC zu Ihren Microsoft hololens in Echtzeit.

Der Holographic Remoting Player kann nur mit PC-Apps verwendet werden, die speziell für die Unterstützung von Holographic Remoting entwickelt wurden.

Der Holographic Remoting Player ist sowohl für hololens (1 St Gen) als auch für hololens 2 verfügbar.  PC-Apps, die Holographic-Remoting mit hololens unterstützen, müssen aktualisiert werden, um Holographic Remoting mit hololens 2 zu unterstützen. Wenden Sie sich an Ihren app-Anbieter, wenn Sie Fragen dazu haben, welche Versionen unterstützt werden.

## <a name="connecting-to-the-holographic-remoting-player"></a>Herstellen einer Verbindung mit dem Holographic Remoting Player

Befolgen Sie die Anweisungen Ihrer APP, um eine Verbindung mit dem Holographic Remoting Player herzustellen. Sie müssen die IP-Adresse Ihres hololens-Geräts eingeben, das Sie auf dem Hauptbildschirm des Remoting-Players sehen können, wie folgt:

![Holographic Remoting Player](images/holographicremotingplayer.png)

Wenn der Hauptbildschirm angezeigt wird, wissen Sie, dass Sie keine app verbunden haben.

Beachten Sie, dass die Holographic-remotingverbindung **nicht verschlüsselt**ist. Sie sollten Holographic Remoting immer über eine sichere WLAN-Verbindung verwenden, die Sie als vertrauenswürdig einstufen.

## <a name="quality-and-performance"></a>Qualität und Leistung

Die Qualität und die Leistung Ihrer Benutzeroberflächen variieren je nach den drei Faktoren:
* **Die holografische Darstellung, die Sie ausführen** : apps, die hochauflösende oder sehr ausführliche Inhalte Renderingfunktionen darstellen, benötigen möglicherweise einen schnelleren PC oder eine schnellere drahtlose Verbindung.
* **Die Hardware Ihres PCs** : Ihr PC muss in der Lage sein, ihre holografische Darstellung bei 60 Frames pro Sekunde auszuführen und zu codieren. Für eine Grafikkarte empfehlen wir in der Regel eine GeForce GTX 970 oder AMD Radeon R9 290 oder höher. Auch hier ist für ihre jeweilige Obergrenze möglicherweise eine höhere oder niedrigere Karte erforderlich.
* **Ihre Wi-Fi-Verbindung** : Ihre Holographic-Darstellung wird über Wi-Fi gestreamt. Verwenden Sie ein schnelles Netzwerk mit geringer Überlastung, um die Qualität zu maximieren. Wenn Sie einen PC verwenden, der über ein Ethernet-Kabel anstatt über Wi-Fi verbunden ist, kann die Qualität ebenfalls verbessern.

## <a name="diagnostics"></a>Diagnose

Zum Messen der Qualität der Verbindung **Geben Sie "Diagnose aktivieren"** auf dem Hauptbildschirm des Holographic Remoting Players ein. Wenn die Diagnose aktiviert ist, zeigt die APP auf **hololens (1. Gen)** Folgendes an:

* **Fps** : die durchschnittliche Anzahl der gerenderten Frames, die der Remoting-Player empfängt und pro Sekunde rendert. Der ideale Wert ist 60 fps.
* **Latenz** Zeit: die durchschnittliche Zeitspanne, die ein Frame benötigt, um von Ihrem PC auf die hololens zu gelangen. Je niedriger der bessere. Dies hängt größtenteils von Ihrem Wi-Fi-Netzwerk ab.

Auf **hololens 2** zeigt Ihnen die APP Folgendes:

![Holographic Remoting Player-Diagnose](images/holographicremotingplayer-diag.png)

* **Rendering** : die Anzahl der Frames, die der Remoting-Player während der letzten Sekunde gerendert hat. Beachten Sie, dass dies unabhängig von der Anzahl der Frames ist, die über das Netzwerk eingetroffen sind (siehe **Video Frames**). Außerdem wird die durchschnittliche/maximale renderdelta Zeit in Millisekunden zwischen gerenderten Frames angezeigt.

* **Video Frames** : die erste angezeigte Anzahl von Video Frames wird übersprungen, die zweite ist wiederverwendeter Videorahmen und die dritte Videorahmen werden empfangen. Alle Zahlen stellen die Anzahl in der letzten Sekunde dar.
    * ```Received frames``` die Anzahl der Video Frames ist, die in der letzten Sekunde eingetroffen sind. Unter normalen Bedingungen sollte dies 60 sein, aber wenn dies nicht der Fall ist, ist dies ein Indikator dafür, dass entweder Frames aufgrund von Netzwerkproblemen gelöscht werden oder dass die Remote-/Remote Seite keine Frames mit der erwarteten Rate erzeugt.
    * ```Reused frames``` ist die Anzahl von Video Frames, die mehr als einmal in der letzten Sekunde verwendet wurden. Wenn z. bWeise Videoframes später eintreffen, rendert die Renderingschleife des Players immer noch einen Frame, muss jedoch den Video Frame *wieder verwenden* , der bereits für den vorherigen Frame verwendet wurde.
    * ```Skipped frames``` ist die Anzahl von Video Frames, die von der Renderingschleife des Players nicht verwendet wurden. Beispielsweise kann der Netzwerk Jitter bewirken, dass die eintreffenden Video Frames nicht gleichmäßig verteilt werden. Wenn z. b. einige spät sind und andere zeitgleich mit dem Ergebnis eintreffen, dass Sie bei der Ausführung auf 60 Hz nicht über eine Delta von 16,66 Millisekunden verfügen. Es kann vorkommen, dass mehr als ein Frame zwischen zwei Ticks der Renderschleife des Players ankommt. In diesem Fall über *springt* der Spieler einen oder mehrere Frames, da der zuletzt empfangene Video Frame immer angezeigt werden soll.

    >[!NOTE]
    >Bei der Bewältigung der Netzwerk Jitter sind übersprungene und wiederverwendete Frames in der Regel ungefähr identisch. Wenn Sie dagegen nur Übersprungene Frames sehen, ist dies ein Indikator dafür, dass der Spieler seine zielframeate nicht erreichen kann. In diesem Fall sollten Sie die maximale Zeit für die Delta Zeit bei der Diagnose von Problemen berücksichtigen.

* **Video Frames Delta** : das minimale/maximale Delta zwischen den empfangenen Video Frames in der letzten Sekunde. Diese Zahl entspricht in der Regel den übersprungenen/wiederverwendeten Frames, wenn Probleme auftreten, die durch Network Jitter verursacht werden.
* **Latenz** Zeit: die durchschnittliche Zeit in Millisekunden in der letzten Sekunde. Die Durchführung in diesem Kontext ist die Zeit, die das Senden von Pose-/Sensordaten von den hololens an die Remote-/Remote-Seite anzeigt, bis der Videoframe für diese Darstellung/Telemetriedaten in den hololens angezeigt wird.
* **Verworfene Video Frames** : die Anzahl der verworfenen Video Frames in der letzten Sekunde und seit dem Herstellen einer Verbindung. Die Hauptursache für verworfene Videorahmen ist, dass ein Videorahmen nicht in der richtigen Reihenfolge eingeht und daher verworfen werden muss, da es bereits eine neuere gibt. Dies ähnelt *verworfenen Frames* , die Ursache liegt jedoch auf einer niedrigeren Ebene im remotingstapel. Verworfene Videorahmen werden nur unter sehr schlechten Netzwerkbedingungen erwartet.



Auf dem Hauptbildschirm können Sie beispielsweise **"Diagnose deaktivieren"** , um die Diagnose zu deaktivieren.

## <a name="pc-system-requirements"></a>PC-System Anforderungen
* Auf dem PC **muss** Windows 10 Anniversary Update oder höher ausgeführt werden.
* Wir empfehlen eine GeForce GTX 970-oder AMD Radeon R9 290-oder bessere Grafikkarte.
* Wir empfehlen Ihnen, Ihren PC über Ethernet mit Ihrem Netzwerk zu verbinden, um die Anzahl der drahtlosen Hops zu verringern.

## <a name="see-also"></a>Weitere Informationen
* [Hololens (1. Generation): Hinzufügen von Holographic Remoting](add-holographic-remoting.md)
* [Hololens 2: Schreiben einer Holographic Remoting-Remote-app](holographic-remoting-create-host.md)
* [Holographic Remoting-Software – Lizenzbedingungen](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzbestimmungen von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
