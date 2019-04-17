---
title: Tastatur-, Maus- und Controller-Eingaben in DirectX
description: Erläutert, wie Sie eine app für Windows Mixed Reality zu erstellen, die Tastatur, Maus und Gamecontroller verwendet.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Tastatur, Maus, Gamecontroller, Xbox-Controller, HoloLens, Desktop, exemplarische Vorgehensweise mit Beispielcode
ms.openlocfilehash: 1e61cb50a561492fdc6849b5b231e97fab1bb6cf
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605085"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>Tastatur-, Maus- und Controller-Eingaben in DirectX

Tastaturen, Mäuse und Gamecontroller können alle nützliche Formulare der Eingabe für Windows Mixed Reality-Geräte sein. Bluetooth-Tastaturen und Mäusen werden sowohl für HoloLens, für die Verwendung mit dem Debuggen Ihrer app oder als eine alternative Form der Eingabe unterstützt. Windows Mixed Reality unterstützt auch immersive Headsets an PCs – wobei Tastaturen, Mäuse und Gamecontroller die Norm bisher angefügt.

Tastatureingaben für HoloLens, Paar eine Bluetooth-Tastatur auf Ihrem Gerät oder verwenden Sie die virtuelle Eingabe über die Windows Device Portal. Um Tastatureingaben zu verwenden und eine immersive Windows Mixed Reality-Kopfhörer trägt, weisen Sie Eingabefokus Realität zu mixed Reality, indem Sie auf dem Gerät platzieren oder mithilfe der Windows-Taste + Y-Tastenkombination. Bedenken Sie, dass Anwendungen für HoloLens Funktionalität ohne diese angeschlossenen Geräte bereitstellen müssen.

>[!NOTE]
>Die Codeausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstatt C ++ 17-kompatible C++"/ WinRT", wie in der [ C++ holographic Projektvorlage](creating-a-holographic-directx-project.md).  Die Konzepte sind Entsprechung für einen C++"/ WinRT"-Projekt, aber Sie benötigen, um den Code zu übersetzen.

## <a name="subscribe-for-corewindow-input-events"></a>Melden Sie sich für Eingabeereignisse "corewindow"

### <a name="keyboard-input"></a>Tastatureingabe

In die Windows Holographic app-Vorlage enthalten einen Ereignishandler für Tastatureingaben, genau wie alle anderen UWP-Apps. Ihrer app verarbeitet die Eingabedaten der Tastatur die gleiche Weise in Windows Mixed Reality.

Von AppView.cpp:

```
// Register for keypress notifications.
   window->KeyDown +=
       ref new TypedEventHandler<CoreWindow^, KeyEventArgs^>(this, &AppView::OnKeyPressed);

    …

   // Input event handlers

   void AppView::OnKeyPressed(CoreWindow^ sender, KeyEventArgs^ args)
   {
       //
       // TODO: Respond to keyboard input here.
       //
   }
```

### <a name="virtual-keyboard-input"></a>Virtuelle Tastatureingaben
Für immersive Headsets desktop können Sie auch virtuelle Tastaturen, die von Windows gerendert wird, über die immersive Ansicht unterstützen. Um dies zu unterstützen, kann Ihre app implementieren **CoreTextEditContext**. Dadurch wird Windows, die den Zustand Ihrer eigenen app gerendert Textfelder, zu verstehen, damit die virtuelle Tastatur ordnungsgemäß auf den Text es beitragen kann.

Weitere Informationen zum Implementieren der CoreTextEditContext-Unterstützung finden Sie unter den [CoreTextEditContext Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).

### <a name="mouse-input"></a>Mauseingabe

Sie können auch die Mauseingabe, erneut über die Eingabe UWP "corewindow"-Ereignishandler. Hier ist die Windows Holographic-app-Vorlage zur Unterstützung von Mausklicks in die gleiche Weise wie gedrückten Gesten ändern. Nach der Erstellung wird diese Änderung ist, klicken mit der Maus während ein Geräts immersive Kopfhörer steht, geteert neu positionieren, den Cube.

Beachten Sie, dass die UWP-apps auch XY-Rohdaten für die Maus mit abrufen können die [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.

Starten Sie, indem Sie einen neuen OnPointerPressed-Handler in AppView.h deklarieren:

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

Fügen Sie auf "SetWindow" AppView.cpp diesen Code hinzu:

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

Fügen Sie diese Definition für OnPointerPressed klicken Sie dann am unteren Rand der Datei:

```
void AppView::OnPointerPressed(CoreWindow^ sender, PointerEventArgs^ args)
   {
       // Allow the user to interact with the holographic world using the mouse.
       if (m_main != nullptr)
       {
           m_main->OnPointerPressed();
       }
   }
```

Die Ereignishandler soeben hinzugefügte ist ein Passthrough-Vorgang, um die Hauptklasse für die Vorlage. Ändern wir die Hauptklasse dieser Pass-Through-Unterstützung. Fügen Sie diese Deklaration für die öffentliche Methode in der Headerdatei hinzu:

```
// Handle mouse input.
       void OnPointerPressed();
```

Sie benötigen diese Private Membervariable, auch Folgendes:

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

Zum Schluss aktualisieren wir "main"-Klasse mit der neuen Logik zur Unterstützung von Mausklicks. Starten Sie durch diesen Ereignishandler hinzufügen. Ändern Sie den Namen der Klasse:

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

Ersetzen Sie nun in der Update-Methode, die vorhandene Logik zum Abrufen einer Haltung Zeiger mit diesem:

```
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

Erneut kompilieren und bereitstellen. Sie sollten feststellen, dass der Maus auf den Cube in Ihrem immersive Kopfhörer- oder HoloLens jetzt mit Bluetooth-Maus angefügt Position wird.

### <a name="game-controller-support"></a>Gamecontroller-Unterstützung

Gamecontroller möglich, dass eine ansprechende und bequem gestattet es dem Benutzer eine immersive Windows Mixed Reality-Erfahrung zu steuern.

Der erste Schritt beim Hinzufügen von Unterstützung für Gamecontroller zu die Windows Holographic app-Vorlage ist so die Headerklasse für die main-Datei die folgenden privaten Member-Deklarationen hinzu:

```
// Recognize gamepads that are plugged in after the app starts.
       void OnGamepadAdded(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
// Stop looking for gamepads that are unplugged.
       void OnGamepadRemoved(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
Windows::Foundation::EventRegistrationToken                     m_gamepadAddedEventToken;
       Windows::Foundation::EventRegistrationToken                     m_gamepadRemovedEventToken;
```

```
// Keeps track of a gamepad and the state of its A button.
       struct GamepadWithButtonState
       {
           Windows::Gaming::Input::Gamepad^ gamepad;
           bool buttonAWasPressedLastFrame = false;
       };
       std::vector<GamepadWithButtonState>                             m_gamepads;
```

Gamepad-Ereignisse und alle Gamepads, die zurzeit zugeordnet sind, im Konstruktor für die main-Klasse zu initialisieren:

```
// If connected, a game controller can also be used for input.
   m_gamepadAddedEventToken = Gamepad::GamepadAdded +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadAdded, this, _1, _2)
           );
```

```
m_gamepadRemovedEventToken = Gamepad::GamepadRemoved +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadRemoved, this, _1, _2)
           );
```

```
for (auto const& gamepad : Gamepad::Gamepads)
   {
       OnGamepadAdded(nullptr, gamepad);
   }
```

Fügen Sie der main-Klasse diese Ereignishandler hinzu. Ändern Sie den Namen der Klasse:

```
void MyHolographicAppMain::OnGamepadAdded(Object^, Gamepad^ args)
   {
       for (auto const& gamepadWithButtonState : m_gamepads)
       {
           if (args == gamepadWithButtonState.gamepad)
           {
               // This gamepad is already in the list.
               return;
           }
       }
       m_gamepads.push_back({ args, false });
   }
```

```
void MyHolographicAppMain::OnGamepadRemoved(Object^, Gamepad^ args)
   {
       m_gamepads.erase(
           std::remove_if(m_gamepads.begin(), m_gamepads.end(), [&](GamepadWithButtonState& gamepadWithState)
               {
                   return gamepadWithState.gamepad == args;
               }),
           m_gamepads.end());
   }
```

Zum Schluss aktualisieren Sie die Eingabe Logik zur Erkennung von Änderungen in den Zustand des Domänencontrollers. Hier verwenden wir die gleichen M_pointerPressed-Variable, die im Abschnitt oben zum Hinzufügen von Mausereignissen erläutert. Kurz vor, in dem sie die SpatialPointerPose prüft, ob die Update-Methode Folgendes hinzu:

```
// Check for new input state since the last frame.
   for (auto& gamepadWithButtonState : m_gamepads)
   {
       bool buttonDownThisUpdate = ((gamepadWithButtonState.gamepad->GetCurrentReading().Buttons & GamepadButtons::A) == GamepadButtons::A);
       if (buttonDownThisUpdate && !gamepadWithButtonState.buttonAWasPressedLastFrame)
       {
           m_pointerPressed = true;
       }
       gamepadWithButtonState.buttonAWasPressedLastFrame = buttonDownThisUpdate;
   }
```

```
// For context.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

Vergessen Sie nicht die Ereignisse beim Bereinigen von "main"-Klasse aufgehoben werden:

```
if (m_gamepadAddedEventToken.Value != 0)
   {
       Gamepad::GamepadAdded -= m_gamepadAddedEventToken;
   }
   if (m_gamepadRemovedEventToken.Value != 0)
   {
       Gamepad::GamepadRemoved -= m_gamepadRemovedEventToken;
   }
```

Kompilieren und erneut bereitstellen. Sie können jetzt anzufügen, oder koppeln, einen game Controller und verwenden, um den sich drehenden Würfels neu positionieren.

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>Wichtige Richtlinien für die Tastatur- und Mauseingaben

Es gibt einige wichtige Unterschiede in wie dieser Code für Microsoft HoloLens – kann, ein Gerät, die stützt sich hauptsächlich auf natürliche Benutzereingaben verwendet werden – im Vergleich zu, was auf einem PC Windows Mixed Reality-fähigen verfügbar ist.
* Sie können nicht auf Tastatur- oder Mauseingaben vorhanden sein verlassen. Alle von den Funktionen Ihrer app müssen mit Blicke, Gesten und Spracheingabe zusammenarbeiten.
* Wenn eine Bluetooth-Tastatur angefügt ist, kann es hilfreich sein, Tastatureingaben zu jedem Text zu aktivieren, die Ihre app anfordern kann. Dies kann eine hervorragende Ergänzung für Diktat, z. B. sein.
* Wenn es darum geht, Sie entwerfen Sie Ihre app, verlassen Sie sich nicht auf (z. B.) WASD und Maus sehen die Steuerelemente für Ihr Spiel. HoloLens dient für den Benutzer im Raum zu durchlaufen. In diesem Fall steuert der Benutzer direkt die Kamera aus. Eine Schnittstelle zum Steuern von der Kamera im Raum verschieben/aussehen Steuerelemente wird nicht die gleiche Funktionalität bereitstellen.
* Tastatureingabe möglich, dass eine hervorragende Möglichkeit, steuern die Debuggen Aspekte Ihrer app oder einer Spiele-Engine, besonders, da der Benutzer nicht zum Verwenden der Tastatur erforderlich ist. Einrichten von es ist identisch, wie Sie mit "corewindow" Ereignis-APIs gewöhnt sind. In diesem Szenario können Sie auswählen, um ein Verfahren zum Konfigurieren Ihrer app zum Weiterleiten von Ereignissen zum Modus "nur Eingabe debug" Tastatur während der Debugsitzungen zu implementieren.
* Bluetooth-Controller funktionieren ebenfalls.

## <a name="see-also"></a>Siehe auch
* [Hardware-Zubehör](hardware-accessories.md)
