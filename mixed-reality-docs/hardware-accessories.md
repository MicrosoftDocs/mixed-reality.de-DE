---
title: Hardware Zubehör
description: Beschreibt die verfügbaren Zubehör Typen für hololens und Windows Mixed Reality sowie deren Einrichtung.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Anleitungen, Zubehör, Bluetooth, BT, Controller, Gamepad, Clicker, Xbox
ms.openlocfilehash: c25f849cbf05a78ba2fe7118dbe160d05e0f5e3f
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526614"
---
# <a name="hardware-accessories"></a>Hardware Zubehör

Windows Mixed Reality-Geräte unterstützen Zubehör. Sie koppeln unterstützte Zubehör mithilfe von Bluetooth mit hololens, während Sie Bluetooth oder USB verwenden können, um unterstützte Zubehör über den PC, mit dem Sie verbunden ist, mit einem immersiven Headset zu koppeln.

Zwei gängige Szenarios für die Verwendung von Zubehör mit hololens sind die Ersatz für die Luft tippen Bewegung und die virtuelle Tastatur. Hierfür sind die beiden gängigsten Zubehör Punkte der **hololens-Clicker** und **Bluetooth-Tastaturen**. Microsoft hololens enthält ein Bluetooth 4,1-Radio und unterstützt [Bluetooth HID](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Human_Interface_Device_Profile_.28HID.29) -und [Bluetooth-GATT](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Generic_Attribute_Profile_.28GATT.29) -Profile.

Immersive Headsets in Windows Mixed Reality erfordern Zubehör für Eingaben, die über den [Blick](gaze.md) und die [Stimme](voice-input.md)hinausgehen. Unterstützte Zubehör sind **Tastatur-und Maus-** , **Gamepad**-und **[Bewegungs Controller](motion-controllers.md)** .

## <a name="pairing-bluetooth-accessories"></a>Kopplung von Bluetooth-Zubehör

Die Kopplung einer Bluetooth-Peripherie mit Microsoft hololens ähnelt der Kopplung einer Bluetooth-Peripherie mit einem Windows 10-Desktop oder einem mobilen Gerät:
1. Öffnen Sie im Startmenü die app " **Einstellungen** ".
2. Zu **Geräten** wechseln
3. Aktivieren Sie das Bluetooth-Radio, wenn es mit dem Schieberegler deaktiviert ist.
4. Platzieren Sie Ihr Bluetooth-Gerät im Paarmodus. Dies variiert von Gerät zu Gerät. Auf den meisten Bluetooth-Geräten erfolgt dies durch Drücken und halten einer oder mehrerer Schaltflächen.
5. Warten Sie, bis der Name des Geräts in der Liste der Bluetooth-Geräte angezeigt wird. Wählen Sie dann das Gerät aus, und wählen Sie dann die Schaltfläche **paar** aus. Wenn Sie über viele Bluetooth-Geräte in der Nähe verfügen, müssen Sie möglicherweise einen Bildlauf zum Ende der Bluetooth-Geräteliste durchführen, um das Gerät anzuzeigen, das Sie koppeln möchten.
6. Beim Koppeln von Bluetooth-Peripheriegeräten mit Eingabefunktionen (z. b.: Bluetooth-Tastaturen), eine 6-stellige oder eine 8-stellige PIN kann angezeigt werden. Achten Sie darauf, dass Sie diese Pin am Peripheriegerät eingeben und dann die EINGABETASTE drücken, um die Kopplung mit Microsoft hololens abzuschließen.

## <a name="motion-controllers"></a>Motion-Controller

Windows Mixed Reality [Motion Controller](motion-controllers.md) werden von immersiven Headsets, aber nicht von hololens unterstützt. Diese Controller bieten mithilfe der Sensoren im immersiven Headset eine präzise und reaktionsfähige Nachverfolgung der Bewegung in Ihrem Sichtfeld, d. h., es ist nicht erforderlich, Hardware an den Wänden in Ihrem Bereich zu installieren. Jeder Controller verfügt über mehrere Methoden der Eingabe.

![Windows Mixed Reality-Bewegungs Controller](images/winmr-ck-1080x1080-350px.jpg)

## <a name="hololens-clicker"></a>Hololens Clicker

Der hololens-Clicker ist das erste Peripheriegerät, das speziell für hololens entwickelt wurde und in der hololens Development Edition enthalten ist. Der hololens-Clicker ermöglicht Benutzern das Klicken und Scrollen mit minimaler Handbewegung als Ersatz für die Tastenkombination. Es ist kein Ersatz für alle [Gesten](gestures.md). Beispielsweise sind für die [aufblühende](gestures.md#bloom) Geste oder die Geste zum [Ändern der Größe oder Verschieben](gestures.md#composite-gestures) eine Handbewegung nötig. Der hololens-Clicker ist ein Ausrichtungs Sensorgerät mit einer einfachen Schaltfläche. Es stellt eine Verbindung mit den hololens mithilfe von Bluetooth Low Energy (btle) her.

![Der hololens-Clicker](images/hololens-clicker-500px.jpg)

Um ein [– Hologramm](hologram.md)auszuwählen, schauen Sie es an, und klicken Sie dann auf. Die Ausrichtung des Clicker ist für diesen Vorgang nicht von Bedeutung. Um einen Bildlauf oder einen Bildlauf durchführen zu können, klicken und halten Sie den Clicker nach oben/unten oder links/rechts. Bei einem Bildlauf erreichen Sie die schnellste Geschwindigkeit mit weniger als +/-15 ° der Hand Drehung. Wenn Sie mehr verschieben, werden Sie nicht schneller scrollen.

Es gibt zwei LEDs innerhalb des Clicker:
* Die weiße LED zeigt an, ob das Gerät paarkopplung (blinkende) oder Überladung (Solid) ist.
* Die Bernstein LED zeigt an, dass das Gerät eine geringe Akkukapazität aufweist (blinkend) oder einen Fehler verursacht hat (Solid).

Sie können mit einer vollständigen Nutzung von 2 Wochen oder mehr rechnen (d.h. 2-3 Stunden auf einem Wand Lader). Wenn der Akku niedrig ist, blinkt die Bernstein-LED 10 mal über einen Zeitraum von 5 Sekunden, wenn Sie die Schaltfläche drücken oder Sie aus dem Standbymodus aktivieren. Die Bernstein-LED blinkt schneller in einem Zeitraum von 5 Sekunden, wenn sich Ihr Clicker im Modus mit niedriger Akkuleistung befindet.

## <a name="bluetooth-keyboards"></a>Bluetooth-Tastaturen

In englischer Sprache Verfügbarkeit Bluetooth-Tastaturen können paarweise gekoppelt und überall dort verwendet werden, wo Sie die holografische Tastatur verwenden können. Wenn Sie eine Qualitäts Tastatur erhalten, empfiehlt es sich, die [universelle Microsoft-Tastatur](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001) oder den [Microsoft Designer Bluetooth Desktop](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001)zu erhalten.

## <a name="bluetooth-gamepads"></a>Bluetooth-Gamepads

Sie können einen Controller mit apps und spielen verwenden, die die Gamepad-Unterstützung speziell aktivieren. Gamepads können nicht zum Steuern der hololens-Benutzeroberfläche verwendet werden.

Xbox Wireless-Controller, die mit der Xbox One s geliefert werden oder als Zubehör für die Xbox One s-Funktion als Zubehör verkauft werden, sind Bluetooth-Verbindungen, die die Verwendung mit hololens und immersiven Headsets ermöglichen. Der Xbox Wireless Controller [muss aktualisiert werden](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) , bevor er mit hololens verwendet werden kann.

Andere Marken von Bluetooth-Gamepads können mit Windows Mixed Reality-Geräten verwendet werden, die Unterstützung variiert jedoch je nach Anwendung.

## <a name="other-bluetooth-accessories"></a>Andere Bluetooth-Zubehör

Solange das Peripheriegerät entweder die Bluetooth HID-oder GATT-Profile unterstützt, kann es mit hololens gekoppelt werden. Andere Bluetooth HID-und GATT-Geräte außer Tastatur, MICE und hololens Clicker erfordern möglicherweise, dass eine Begleit Anwendung auf Microsoft hololens voll funktionsfähig ist.

Zu den nicht unterstützten Peripheriegeräten gehören:
* Peripheriegeräte in Bluetooth-audioprofilen werden nicht unterstützt.
* Bluetooth-Audiogeräte, wie z. b. Sprecher und Headsets, werden möglicherweise als verfügbar in der App "Einstellungen" angezeigt, werden aber nicht für die Verwendung mit Microsoft hololens als audioendpunkt unterstützt.
* Für Bluetooth aktivierte Telefone und PCs wird das kombinieren und Verwenden von Dateiübertragungen nicht unterstützt.

## <a name="unpairing-a-bluetooth-peripheral"></a>Entkopplung einer Bluetooth-Peripherie
1. Öffnen Sie im Startmenü die app " **Einstellungen** ".
2. Zu **Geräten** wechseln
3. Aktivieren Sie das Bluetooth-Radio, wenn es deaktiviert ist.
4. Suchen Ihres Geräts in der Liste der verfügbaren Bluetooth-Geräte
5. Wählen Sie Ihr Gerät aus der Liste aus, und klicken Sie dann auf die Schaltfläche **Entfernen**

## <a name="disabling-bluetooth-on-microsoft-hololens"></a>Deaktivieren von Bluetooth für Microsoft hololens

Dadurch werden die RF-Komponenten des Bluetooth-Options Felds ausgeschaltet und die gesamte Bluetooth-Funktionalität für Microsoft hololens deaktiviert.
1. Öffnen Sie im Startmenü die app " **Einstellungen** ".
2. Zu **Geräten** wechseln
3. Verschieben Sie den Schieberegler für Bluetooth an die Position aus.
