---
title: Hardware-Zubehör
description: Beschreibt die Typen von Zubehör zur Verwendung mit HoloLens und Windows Mixed Reality und wie deren Einrichtung zur Verfügung.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Exemplarische Vorgehensweise, Zubehör, Bluetooth, Bt, Controller, Gamepad, Clicker, xbox
ms.openlocfilehash: c25f849cbf05a78ba2fe7118dbe160d05e0f5e3f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604735"
---
# <a name="hardware-accessories"></a>Hardware-Zubehör

Windows Mixed Reality-Geräte unterstützen Zubehör. Sie müssen koppeln unterstützten Zubehör, HoloLens, die mithilfe von Bluetooth, können Sie Bluetooth oder USB-zu-Paar unterstützt Zubehör eine immersive Kopfhörer über den PC mit dem sie verbunden ist.

Zwei häufige Szenarios für die Verwendung von Zubehör mit HoloLens sind als Ersatz für die Luft Gesten und der virtuellen Tastatur tippen. Hierzu werden die beiden am häufigsten verwendeten Zubehör der **HoloLens Clicker** und **Bluetooth-Tastaturen**. Microsoft HoloLens enthält ein Optionsfeld Bluetooth-4.1 und unterstützt [Bluetooth-HID](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Human_Interface_Device_Profile_.28HID.29) und [Bluetooth GATT](https://en.wikipedia.org/wiki/List_of_Bluetooth_profiles#Generic_Attribute_Profile_.28GATT.29) Profile.

Windows Mixed Reality immersive Headsets Zubehör erfordern, für die Eingabe über [bestaunen](gaze.md) und [Voice](voice-input.md). Unterstützte Zubehör enthalten **Tastatur und Maus**, **Gamepad**, und  **[motion Controller](motion-controllers.md)**.

## <a name="pairing-bluetooth-accessories"></a>Kopplung von Bluetooth-Zubehör

Koppeln einen Bluetooth-Peripheriegeräte mit Microsoft HoloLens ähnelt der Kopplung einen Bluetooth-Peripheriegeräte mit einem Windows 10 desktop oder Mobilgerät:
1. Öffnen Sie über das Startmenü die **Einstellungen** app
2. Wechseln Sie zu **Geräte**
3. Schalten Sie die Bluetooth-Funktion ist dies mithilfe des Schieberegler-Schalters
4. Platzieren Sie das Bluetooth-Gerät im Modus Kopplung. Dies variiert je nach Gerät. In den meisten Bluetooth-Geräten wird dies durch das Drücken und halten eine oder mehrere Schaltflächen.
5. Warten Sie auf den Namen des Geräts in der Liste der Bluetooth-Geräten angezeigt wird. Wenn sie, wählen Sie das Gerät und wählen Sie dann die **Paar** Schaltfläche. Wenn Sie haben möglicherweise viele Bluetooth-Geräte in der Nähe Sie müssen einen Bildlauf zum unteren Rand der Bluetooth-Gerät-Liste auf das Gerät, die, das Sie koppeln möchten, finden Sie unter.
6. Wenn Kopplung mit Bluetooth-Peripheriegeräte Funktion Eingabe-(z. B.: Bluetooth-Tastaturen), eine 6-stellige oder eine Pin 8-stellige kann angezeigt werden. Achten Sie darauf, dass Sie diese Pin in der Peripheriegerät eingeben, und drücken Sie die EINGABETASTE, um die vollständige Verbindung mit Microsoft HoloLens.

## <a name="motion-controllers"></a>Motion-Controller

Windows Mixed Reality [motion Controller](motion-controllers.md) immersive Headsets, aber nicht HoloLens verwendet werden. Diese Controller bieten präzise und reaktionsfähige nachverfolgung von Verschieben von Daten in Ihrem Blickfeld verwenden die Sensoren in die immersive Kopfhörer, was bedeutet, dass besteht keine Notwendigkeit zum Installieren von Hardware an den Wänden in Ihrem Bereich. Jeder Controller bietet verschiedene Methoden der Eingabe.

![Windows Mixed Reality-Motion-Controller](images/winmr-ck-1080x1080-350px.jpg)

## <a name="hololens-clicker"></a>HoloLens Clicker

Die HoloLens Clicker ist die erste Peripheriegerät wurde speziell für HoloLens und in die HoloLens Development Edition enthalten. Die HoloLens Clicker ermöglicht einen Benutzer auf, und führen Sie einen Bildlauf mit minimalen Hand während der Übertragung als Ersatz für die tippbewegung Bewegung. Es ist kein Ersatz für alle [Gesten](gestures.md). Z. B. [Bloom](gestures.md#bloom) und [Größe oder Position von](gestures.md#composite-gestures) Gesten verwenden Bewegungen von Hand. Die HoloLens Clicker ist ein Ausrichtung Sensor-Gerät mit einer einfachen Schaltfläche. Verbindung mit der Verwendung von Bluetooth Low Energy (BTLE) HoloLens.

![Die HoloLens Clicker](images/hololens-clicker-500px.jpg)

Auswählen einer [– Hologramm](hologram.md)bestaunen an, und klicken Sie dann auf. Ausrichtung der Clicker spielt keine Rolle für diesen Vorgang. Drehen Sie um zu scrollen oder schwenken, klicken Sie auf, und halten, klicken Sie dann die Clicker hoch-/Herunterskalieren oder links/rechts. Beim Durchführen eines Bildlaufs erreichen Sie die schnellste Geschwindigkeit, mit so wenig wie +/-15 Grad der Drehung der Finger. Verschieben von mehr keinen schneller Bildlauf durchführen.

Es gibt zwei LEDs innerhalb der Clicker:
* Die weiße LED gibt an, ob das Gerät (blinkende) Kopplung ist bzw. Aufladen (stetig)
* Die gelbe LED zeigt an, dass das Gerät ist der Akku (blinkende) oder hat einen Fehler (stetig) ist

Sie können mindestens zwei Wochen der normale Verwendung auf einer vollständigen Aufladen (d. h. 2 bis 3 Stunden auf einer Wand Ladegerät) erwarten. Wenn die Batterie gering ist, die gelbe, die LED 10 Mal über einen Zeitraum von 5 Sekunden blinkt wird, wenn Sie die Schaltfläche oder aus dem Standbymodus reaktiviert. Die gelbe, die LED über ein 5-Sekunden-Zeitraums Wenn schneller blinkt wird, ist Ihre Clicker äußerst niedriger Akkustand.

## <a name="bluetooth-keyboards"></a>Bluetooth-Tastaturen

Englische Bluetooth Qwerty-Tastaturen gekoppelt werden können und überall die Verwendung der Tastatur holographic verwendet. Erhalten eine Tastatur Qualität ein Unterschied, also ist es empfehlenswert die [Microsoft Universal zur Kompilierzeit reduzierbare Keyboard](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001) oder [Microsoft Designer Bluetooth-Desktop](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001).

## <a name="bluetooth-gamepads"></a>Bluetooth-gamepads

Sie können einen Controller mit apps und Spiele, die speziell Gamepad-Unterstützung zu aktivieren. Gamepads kann nicht verwendet werden, um die HoloLens-Benutzeroberfläche zu steuern.

Xbox-Controller Drahtlosnetzwerke, die im Lieferumfang der Xbox eine S oder verkauft als Zubehör für das ein Xbox-S-Feature Bluetooth-Verbindungen, mit die sie mit HoloLens und immersive Headsets verwendet werden können. Die Xbox-Controller Wireless [muss aktualisiert werden,](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) , bevor sie mit HoloLens verwendet werden kann.

Unter Umständen andere Marken von Bluetooth-Gamepads Windows Mixed Reality-Geräte möglich, aber Unterstützung von Anwendung variieren.

## <a name="other-bluetooth-accessories"></a>Andere Bluetooth-Zubehör

Solange das Peripheriegerät der Bluetooth-HID oder GATT-Profile unterstützt, ist es, die mit HoloLens möglich. Andere Bluetooth-HID und GATT Geräte neben der Tastatur, Mäusen und die HoloLens Clicker möglicherweise eine unterstützende Anwendung für Microsoft HoloLens voll funktionsfähig ist.

Nicht unterstützte Peripheriegeräte gehören:
* Peripheriegeräte in den Bluetooth-audio-Profilen werden nicht unterstützt.
* Audio Bluetooth-Geräten wie z. B. Referenten und Headsets möglicherweise in der Einstellungs-app als verfügbar angezeigt, jedoch werden nicht unterstützt werden, um die mit Microsoft HoloLens als audio-Endpunkt verwendet werden.
* Bluetooth-fähigen Smartphones und PCs werden nicht unterstützt, zugeordnet und für die Übertragung von Dateien verwendet werden soll.

## <a name="unpairing-a-bluetooth-peripheral"></a>Entkoppelt Sie eine Bluetooth-Peripheriegeräte
1. Öffnen Sie über das Startmenü die **Einstellungen** app
2. Wechseln Sie zu **Geräte**
3. Bluetooth-Funk schalten Sie ein, wenn sie deaktiviert ist
4. Suchen Sie Ihr Gerät in der Liste der verfügbaren Bluetooth-Geräte
5. Wählen Sie Ihr Gerät aus der Liste aus, und wählen Sie dann die **entfernen** Schaltfläche

## <a name="disabling-bluetooth-on-microsoft-hololens"></a>Deaktivieren von Bluetooth auf Microsoft HoloLens

Die RF-Komponenten von Bluetooth-Funk deaktivieren wird und deaktivieren alle Bluetooth-Funktionalität für Microsoft HoloLens.
1. Öffnen Sie über das Startmenü die **Einstellungen** app
2. Wechseln Sie zu **Geräte**
3. Verschieben Sie den Schieberegler-Schalter von Bluetooth in die position
