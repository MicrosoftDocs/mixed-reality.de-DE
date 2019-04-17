---
title: Kalibrierung
description: Kalibrierung Ihre Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor (interpupillary Abstand), kann die Qualität Ihrer Visuals verbessern. Sowohl HoloLens und Windows Mixed Reality immersive Headsets bieten Möglichkeiten zum Anpassen von IPD.
author: xerxesb85
ms.author: xerxesb
ms.date: 02/24/2019
ms.topic: article
keywords: calibration, comfort, visuals, quality, ipd
ms.openlocfilehash: 91af069bc4ae5e49d9eb9c529f0d0db7b1567fc8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604794"
---
# <a name="calibration"></a>Kalibrierung

Kalibrierung Ihre Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor (interpupillary Abstand), kann die Qualität Ihrer Visuals verbessern. Sowohl HoloLens und Windows Mixed Reality immersive Headsets bieten Möglichkeiten zum Anpassen von IPD.

## <a name="hololens"></a>HoloLens

### <a name="during-setup"></a>Während des Setups

![IPD-Finger-Ausrichtung-Bildschirm im zweiten Schritt](images/ipd-finger-alignment-300px.jpg)<br>

*IPD-Finger-Ausrichtung-Bildschirm im zweiten Schritt*

Für HoloLens werden Sie aufgefordert, Ihre visuellen Elemente während des Setups kalibrieren. Dies ermöglicht dem Gerät anpassen – Hologramm Anzeige gemäß des Benutzers [interpupillary Abstand](https://en.wikipedia.org/wiki/Interpupillary_distance) (Implementierungsparameterdeskriptor, Implementierungszeilendeskriptor). Mit einer falschen IPD möglicherweise Hologramme instabil wird oder in einem falschen Abstand angezeigt.

Nach dem Cortana selbst eingeführt werden, ist der erste Schritt der Installation Kalibrierung an. Es wird empfohlen, dass Sie den Kalibrierungsschritt in dieser Phase von Setup ausführen, aber es übersprungen werden, kann indem Sie warten, bis Sie Cortana sagen Sie "Skip" zum Fortfahren aufgefordert werden, zu verwenden.

Benutzer werden aufgefordert, den Finger mit einer Reihe von sechs Ziele pro Eye ausgerichtet. Im Rahmen dieses Prozesses legt die richtigen IPD von HoloLens für den Benutzer fest. Wenn die Kalibrierung aktualisiert oder für einen neuen Benutzer angepasst werden muss, kann es außerhalb von Setup mithilfe der Kalibrierung-app ausgeführt werden.

### <a name="calibration-app"></a>Kalibrierung-app

Kalibrierung kann jederzeit über die Kalibrierung-app ausgeführt werden. Die Kalibrierung-app wird standardmäßig installiert, und über das Startmenü oder über die Einstellungs-app zugegriffen werden kann. Kalibrierung wird empfohlen, wenn Sie möchten, zum Verbessern der Qualität Ihrer Visuals oder kalibrieren visuelle Elemente für einen neuen Benutzer.

**Starten der app aus starten**
1. Verwendung [Bloom](gestures.md#bloom) , um erhalten [Menü "Start"](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Wählen Sie **+** alle apps anzeigen.
3. Starten Sie **Kalibrierung**.

![Zugriff auf die Kalibrierung-app in der Befehlsshell](images/calibration-shell.png)

![Die Kalibrierung-app als eine Live-Cube angezeigt wird, nachdem er gestartet wurde](images/calibration-livecube-200px.png)

**Starten der app aus Einstellungen**
1. Verwendung [Bloom](gestures.md#bloom) , um erhalten [Menü "Start"](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Wählen Sie **+** alle apps anzeigen, wenn **Einstellungen** ist nicht an Start angeheftet.
3. Starten Sie **Einstellungen**.
4. Navigieren Sie zu **System** > **Dienstprogramme** , und wählen Sie **öffnen Kalibrierung**.

![Starten der Kalibrierung-app aus der einstellungs-app](images/calibration-settings-500px.jpg)

## <a name="hololens-2"></a>HoloLens 2

> [!NOTE]
> Weitere Anleitungen, die speziell für HoloLens 2 [bald](index.md#news-and-notes).

## <a name="immersive-headsets"></a>Immersive headsets

Um innerhalb Ihrer Kopfhörer IPD zu ändern, öffnen Sie die Einstellungen-app, und navigieren Sie zu **Mixed Reality** > **Kopfhörer Anzeige** und verschieben Sie das Schieberegler-Steuerelement. Sie sehen die Änderungen in Echtzeit in Ihre Kopfhörer. Wenn Sie Ihre IPD kennen, können möglicherweise von Besuchen der Augenärzten Sie es auch direkt eingeben.

Sie können diese Einstellung auch anpassen, indem Sie zu **Einstellungen** > **Mixed Reality** > **Kopfhörer Anzeige** auf Ihrem PC.

Wenn Ihre Kopfhörer IPD-Anpassung nicht unterstützt, wird diese Einstellung deaktiviert.

## <a name="see-also"></a>Siehe auch
* [Aspekte der Umgebung für HoloLens](environment-considerations-for-hololens.md)
