---
title: Tastatur-, Maus-und Controller Eingaben in DirectX
description: Erläutert das Erstellen einer APP für Windows Mixed Reality, in der Tastatur-, Maus-und Spielcontroller verwendet werden.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Tastatur, Maus, Game Controller, Xbox Controller, hololens, Desktop, Exemplarische Vorgehensweise, Beispielcode
ms.openlocfilehash: 27f1bf72435ce6889ba3f7b83664367a4440b162
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278088"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>Tastatur-, Maus-und Controller Eingaben in DirectX

Tastaturen, Mäuse und Spielcontroller können als nützliche Formen der Eingabe für Windows Mixed Reality-Geräte dienen. Bluetooth-Tastaturen und-Mäuse werden sowohl in hololens unterstützt als auch beim Debuggen Ihrer APP oder als Alternative Form der Eingabe. Windows Mixed Reality unterstützt auch immersive Headsets, die an PCs angeschlossen sind, bei denen Mäuse, Tastaturen und Spielcontroller in der Vergangenheit die Norm waren.

Um Tastatureingaben in hololens zu verwenden, koppeln Sie eine Bluetooth-Tastatur mit Ihrem Gerät, oder verwenden Sie die virtuelle Eingabe über das Windows-Geräte Portal. Wenn Sie Tastatureingaben beim Durchführen eines Windows Mixed Reality-immersiven Headsets verwenden möchten, weisen Sie der gemischten Realität den Eingabefokus zu, indem Sie das Gerät platzieren oder die Tastenkombination Windows-Taste + Y verwenden. Beachten Sie, dass apps, die für hololens vorgesehen sind, Funktionen ohne angehängte Geräte bereitstellen müssen.

>[!NOTE]
>Die Code Ausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung C++von/CX anstelle von C + +17- C++kompatibler/WinRT, wie Sie in der [ C++ Holographic-Projektvorlage](creating-a-holographic-directx-project.md)verwendet werden.  Die Konzepte sind äquivalent für ein C++/WinRT-Projekt, obwohl Sie den Code übersetzen müssen.

## <a name="subscribe-for-corewindow-input-events"></a>Abonnieren von corewindow-Eingabe Ereignissen

### <a name="keyboard-input"></a>Tastatureingabe

In der Windows Holographic-App-Vorlage fügen wir einen Ereignishandler für Tastatureingaben wie jede andere UWP-App ein. Ihre APP beansprucht Tastatureingabe Daten in Windows Mixed Reality auf dieselbe Weise.

Aus appview. cpp:

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

### <a name="virtual-keyboard-input"></a>Virtuelle Tastatureingabe
Bei immersiven Desktop-Headsets können Sie auch virtuelle Tastaturen unterstützen, die von Windows gerendert werden. Um dies zu unterstützen, kann Ihre APP **coretexteditcontext**implementieren. Dadurch kann Windows den Zustand ihrer eigenen, von der APP gerenderten Textfelder verstehen, sodass die virtuelle Tastatur ordnungsgemäß zum Text beitragen kann.

Weitere Informationen zum Implementieren der coretexteditcontext-Unterstützung finden Sie im [coretexteditcontext-Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).

### <a name="mouse-input"></a>Mauseingabe

Sie können auch über die Eingabe Ereignishandler von UWP corewindow auch Maus Eingaben verwenden. Im folgenden wird erläutert, wie Sie die Windows Holographic-App-Vorlage ändern, um Mausklicks auf die gleiche Weise wie gedrückte Gesten zu unterstützen. Nachdem Sie diese Änderung vorgenommen haben, wird der Cube durch einen Mausklick beim Ausführen eines immersiven Headset-Geräts neu positioniert.

Beachten Sie, dass UWP-apps auch unformatierte XY-Daten für die Maus mithilfe der [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) -API erhalten können.

Beginnen Sie mit dem Deklarieren eines neuen onpointerpressed-Handlers in appview. h:

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

Fügen Sie in appview. cpp den folgenden Code zu SetWindow hinzu:

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

Fügen Sie dann diese Definition für "onpointerpressed" am Ende der Datei ein:

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

Der soeben hinzugefügte Ereignishandler ist eine Pass-Through-Funktion für die Hauptklasse der Vorlage. Ändern wir nun die Hauptklasse, um diese Pass-Through-Unterstützung zu unterstützen. Fügen Sie diese Deklaration der öffentlichen Methode der Header Datei hinzu:

```
// Handle mouse input.
       void OnPointerPressed();
```

Sie benötigen auch diese private Member-Variable:

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

Zum Schluss aktualisieren wir die Hauptklasse mit neuer Logik zur Unterstützung von Mausklicks. Beginnen Sie mit dem Hinzufügen dieses Ereignis Handlers. Stellen Sie sicher, dass Sie den Klassennamen aktualisieren:

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

Ersetzen Sie nun in der Update-Methode die vorhandene Logik, um eine Zeiger Pose mit folgenden Informationen zu erhalten:

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

Neukompilieren und erneut bereitstellen. Beachten Sie, dass mit dem Maus Klick nun der Cube in Ihrem immersiven Headset oder hololens mit der Bluetooth-Maus angefügt wird.

### <a name="game-controller-support"></a>Spiele Controller Unterstützung

Spiele Controller können eine angenehme und bequeme Möglichkeit bieten, dem Benutzer zu ermöglichen, eine immersive Windows Mixed Reality-Darstellung zu steuern.

Der erste Schritt beim Hinzufügen von Unterstützung für Game Controller zur Windows Holographic-App-Vorlage besteht darin, die folgenden privaten Member-Deklarationen der Header Klasse für Ihre Hauptdatei hinzuzufügen:

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

Initialisieren Sie Gamepad-Ereignisse und alle derzeit angefügten Gamepads im Konstruktor für Ihre Hauptklasse:

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

Fügen Sie diese Ereignishandler ihrer Hauptklasse hinzu. Stellen Sie sicher, dass Sie den Klassennamen aktualisieren:

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

Aktualisieren Sie schließlich die Eingabe Logik, um Änderungen im Controller Zustand zu erkennen. Hier verwenden wir die gleiche m_pointerPressed Variable, die im obigen Abschnitt zum Hinzufügen von Mausereignissen erläutert wurde. Fügen Sie diese der Update-Methode hinzu, kurz bevor Sie die Anwendung auf spatialpointerpose überprüft:

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

Vergessen Sie nicht, die Registrierung der Ereignisse beim Bereinigen der Hauptklasse aufzuheben:

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

Neukompilieren und erneut bereitstellen. Sie können jetzt einen Spielcontroller anfügen oder koppeln und ihn verwenden, um den drehenden Cube neu zu positionieren.

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>Wichtige Richtlinien für Tastatur-und Maus Eingaben

Es gibt einige wichtige Unterschiede bei der Verwendung dieses Codes für Microsoft hololens – bei dem es sich um ein Gerät handelt, das hauptsächlich auf natürlichen Benutzereingaben basiert – im Vergleich zu den Funktionen, die auf einem Windows Mixed Reality-fähigen PC verfügbar sind.
* Sie können sich nicht darauf verlassen, dass Tastatur-oder Maus Eingaben vorhanden sind. Alle Funktionen Ihrer APP müssen mit Blick, Gesten und Spracheingaben funktionieren.
* Wenn eine Bluetooth-Tastatur angefügt wird, kann es hilfreich sein, Tastatureingaben für jeden Text zu aktivieren, der von Ihrer APP angefordert werden kann. Dies kann z. b. eine hervor artige Ergänzung zum Diktat darstellen.
* Wenn Sie Ihre APP entwerfen möchten, verlassen Sie sich nicht auf (z. b.) WASD-und Mauszeiger-Steuerelemente für Ihr Spiel. Hololens ist dafür konzipiert, dass der Benutzer den Raum durchläuft. In diesem Fall steuert der Benutzer die Kamera direkt. Eine Schnittstelle zum Steuern der Kamera um den Raum mit Verschiebe-und Bild-Steuerelementen bietet nicht die gleiche Umgebung.
* Tastatureingaben können eine hervorragende Möglichkeit zum Steuern der debuggingaspekte Ihrer APP oder Spiel-Engine sein, insbesondere, da der Benutzer die Tastatur nicht verwenden muss. Die Verknüpfung ist identisch mit der Verwendung von corewindow-Ereignis-APIs. In diesem Szenario können Sie eine Möglichkeit implementieren, um Ihre APP so zu konfigurieren, dass Tastatur Ereignisse während der Debugsitzungen an den Modus "nur debugeingabe" weitergeleitet werden.
* Bluetooth-Controller sind ebenfalls funktionsfähig.

## <a name="see-also"></a>Siehe auch
* [Hardware-Zubehör](hardware-accessories.md)
