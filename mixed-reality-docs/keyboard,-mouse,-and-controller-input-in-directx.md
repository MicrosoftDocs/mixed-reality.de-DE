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
# <a name="keyboard-mouse-and-controller-input-in-directx"></a><span data-ttu-id="f3b18-104">Tastatur-, Maus- und Controller-Eingaben in DirectX</span><span class="sxs-lookup"><span data-stu-id="f3b18-104">Keyboard, mouse, and controller input in DirectX</span></span>

<span data-ttu-id="f3b18-105">Tastaturen, Mäuse und Gamecontroller können alle nützliche Formulare der Eingabe für Windows Mixed Reality-Geräte sein.</span><span class="sxs-lookup"><span data-stu-id="f3b18-105">Keyboards, mice, and game controllers can all be useful forms of input for Windows Mixed Reality devices.</span></span> <span data-ttu-id="f3b18-106">Bluetooth-Tastaturen und Mäusen werden sowohl für HoloLens, für die Verwendung mit dem Debuggen Ihrer app oder als eine alternative Form der Eingabe unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f3b18-106">Bluetooth keyboards and mice are both supported on HoloLens, for use with debugging your app or as an alternate form of input.</span></span> <span data-ttu-id="f3b18-107">Windows Mixed Reality unterstützt auch immersive Headsets an PCs – wobei Tastaturen, Mäuse und Gamecontroller die Norm bisher angefügt.</span><span class="sxs-lookup"><span data-stu-id="f3b18-107">Windows Mixed Reality also supports immersive headsets attached to PCs - where mice, keyboards, and game controllers have historically been the norm.</span></span>

<span data-ttu-id="f3b18-108">Tastatureingaben für HoloLens, Paar eine Bluetooth-Tastatur auf Ihrem Gerät oder verwenden Sie die virtuelle Eingabe über die Windows Device Portal.</span><span class="sxs-lookup"><span data-stu-id="f3b18-108">To use keyboard input on HoloLens, pair a Bluetooth keyboard to your device or use virtual input via the Windows Device Portal.</span></span> <span data-ttu-id="f3b18-109">Um Tastatureingaben zu verwenden und eine immersive Windows Mixed Reality-Kopfhörer trägt, weisen Sie Eingabefokus Realität zu mixed Reality, indem Sie auf dem Gerät platzieren oder mithilfe der Windows-Taste + Y-Tastenkombination.</span><span class="sxs-lookup"><span data-stu-id="f3b18-109">To use keyboard input while wearing a Windows Mixed Reality immersive headset, assign input focus to mixed reality by putting on the device or using the Windows Key + Y keyboard combination.</span></span> <span data-ttu-id="f3b18-110">Bedenken Sie, dass Anwendungen für HoloLens Funktionalität ohne diese angeschlossenen Geräte bereitstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="f3b18-110">Keep in mind that apps intended for HoloLens must provide functionality without these devices attached.</span></span>

>[!NOTE]
><span data-ttu-id="f3b18-111">Die Codeausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstatt C ++ 17-kompatible C++"/ WinRT", wie in der [ C++ holographic Projektvorlage](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="f3b18-111">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="f3b18-112">Die Konzepte sind Entsprechung für einen C++"/ WinRT"-Projekt, aber Sie benötigen, um den Code zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="f3b18-112">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="subscribe-for-corewindow-input-events"></a><span data-ttu-id="f3b18-113">Melden Sie sich für Eingabeereignisse "corewindow"</span><span class="sxs-lookup"><span data-stu-id="f3b18-113">Subscribe for CoreWindow input events</span></span>

### <a name="keyboard-input"></a><span data-ttu-id="f3b18-114">Tastatureingabe</span><span class="sxs-lookup"><span data-stu-id="f3b18-114">Keyboard input</span></span>

<span data-ttu-id="f3b18-115">In die Windows Holographic app-Vorlage enthalten einen Ereignishandler für Tastatureingaben, genau wie alle anderen UWP-Apps.</span><span class="sxs-lookup"><span data-stu-id="f3b18-115">In the Windows Holographic app template, we include an event handler for keyboard input just like any other UWP app.</span></span> <span data-ttu-id="f3b18-116">Ihrer app verarbeitet die Eingabedaten der Tastatur die gleiche Weise in Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="f3b18-116">Your app consumes keyboard input data the same way in Windows Mixed Reality.</span></span>

<span data-ttu-id="f3b18-117">Von AppView.cpp:</span><span class="sxs-lookup"><span data-stu-id="f3b18-117">From AppView.cpp:</span></span>

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

### <a name="virtual-keyboard-input"></a><span data-ttu-id="f3b18-118">Virtuelle Tastatureingaben</span><span class="sxs-lookup"><span data-stu-id="f3b18-118">Virtual keyboard input</span></span>
<span data-ttu-id="f3b18-119">Für immersive Headsets desktop können Sie auch virtuelle Tastaturen, die von Windows gerendert wird, über die immersive Ansicht unterstützen.</span><span class="sxs-lookup"><span data-stu-id="f3b18-119">For immersive desktop headsets, you can also support virtual keyboards rendered by Windows over your immersive view.</span></span> <span data-ttu-id="f3b18-120">Um dies zu unterstützen, kann Ihre app implementieren **CoreTextEditContext**.</span><span class="sxs-lookup"><span data-stu-id="f3b18-120">To support this, your app can implement **CoreTextEditContext**.</span></span> <span data-ttu-id="f3b18-121">Dadurch wird Windows, die den Zustand Ihrer eigenen app gerendert Textfelder, zu verstehen, damit die virtuelle Tastatur ordnungsgemäß auf den Text es beitragen kann.</span><span class="sxs-lookup"><span data-stu-id="f3b18-121">This lets Windows understand the state of your own app-rendered text boxes, so the virtual keyboard can correctly contribute to the text there.</span></span>

<span data-ttu-id="f3b18-122">Weitere Informationen zum Implementieren der CoreTextEditContext-Unterstützung finden Sie unter den [CoreTextEditContext Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span><span class="sxs-lookup"><span data-stu-id="f3b18-122">For more information on implementing CoreTextEditContext support, see the [CoreTextEditContext sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>

### <a name="mouse-input"></a><span data-ttu-id="f3b18-123">Mauseingabe</span><span class="sxs-lookup"><span data-stu-id="f3b18-123">Mouse Input</span></span>

<span data-ttu-id="f3b18-124">Sie können auch die Mauseingabe, erneut über die Eingabe UWP "corewindow"-Ereignishandler.</span><span class="sxs-lookup"><span data-stu-id="f3b18-124">You can also use mouse input, again via the UWP CoreWindow input event handlers.</span></span> <span data-ttu-id="f3b18-125">Hier ist die Windows Holographic-app-Vorlage zur Unterstützung von Mausklicks in die gleiche Weise wie gedrückten Gesten ändern.</span><span class="sxs-lookup"><span data-stu-id="f3b18-125">Here's how to modify the Windows Holographic app template to support mouse clicks in the same way as pressed gestures.</span></span> <span data-ttu-id="f3b18-126">Nach der Erstellung wird diese Änderung ist, klicken mit der Maus während ein Geräts immersive Kopfhörer steht, geteert neu positionieren, den Cube.</span><span class="sxs-lookup"><span data-stu-id="f3b18-126">After making this modification, a mouse click while wearing an immersive headset device will reposition the cube.</span></span>

<span data-ttu-id="f3b18-127">Beachten Sie, dass die UWP-apps auch XY-Rohdaten für die Maus mit abrufen können die [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span><span class="sxs-lookup"><span data-stu-id="f3b18-127">Note that UWP apps can also get raw XY data for the mouse by using the [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span></span>

<span data-ttu-id="f3b18-128">Starten Sie, indem Sie einen neuen OnPointerPressed-Handler in AppView.h deklarieren:</span><span class="sxs-lookup"><span data-stu-id="f3b18-128">Start by declaring a new OnPointerPressed handler in AppView.h:</span></span>

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

<span data-ttu-id="f3b18-129">Fügen Sie auf "SetWindow" AppView.cpp diesen Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="f3b18-129">In AppView.cpp, add this code to SetWindow:</span></span>

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

<span data-ttu-id="f3b18-130">Fügen Sie diese Definition für OnPointerPressed klicken Sie dann am unteren Rand der Datei:</span><span class="sxs-lookup"><span data-stu-id="f3b18-130">Then put this definition for OnPointerPressed at the bottom of the file:</span></span>

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

<span data-ttu-id="f3b18-131">Die Ereignishandler soeben hinzugefügte ist ein Passthrough-Vorgang, um die Hauptklasse für die Vorlage.</span><span class="sxs-lookup"><span data-stu-id="f3b18-131">The event handler we just added is a pass-through to the template main class.</span></span> <span data-ttu-id="f3b18-132">Ändern wir die Hauptklasse dieser Pass-Through-Unterstützung.</span><span class="sxs-lookup"><span data-stu-id="f3b18-132">Let's modify the main class to support this pass-through.</span></span> <span data-ttu-id="f3b18-133">Fügen Sie diese Deklaration für die öffentliche Methode in der Headerdatei hinzu:</span><span class="sxs-lookup"><span data-stu-id="f3b18-133">Add this public method declaration to the header file:</span></span>

```
// Handle mouse input.
       void OnPointerPressed();
```

<span data-ttu-id="f3b18-134">Sie benötigen diese Private Membervariable, auch Folgendes:</span><span class="sxs-lookup"><span data-stu-id="f3b18-134">You'll need this private member variable, as well:</span></span>

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

<span data-ttu-id="f3b18-135">Zum Schluss aktualisieren wir "main"-Klasse mit der neuen Logik zur Unterstützung von Mausklicks.</span><span class="sxs-lookup"><span data-stu-id="f3b18-135">Finally, we will update the main class with new logic to support mouse clicks.</span></span> <span data-ttu-id="f3b18-136">Starten Sie durch diesen Ereignishandler hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f3b18-136">Start by adding this event handler.</span></span> <span data-ttu-id="f3b18-137">Ändern Sie den Namen der Klasse:</span><span class="sxs-lookup"><span data-stu-id="f3b18-137">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

<span data-ttu-id="f3b18-138">Ersetzen Sie nun in der Update-Methode, die vorhandene Logik zum Abrufen einer Haltung Zeiger mit diesem:</span><span class="sxs-lookup"><span data-stu-id="f3b18-138">Now, in the Update method, replace the existing logic for getting a pointer pose with this:</span></span>

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

<span data-ttu-id="f3b18-139">Erneut kompilieren und bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="f3b18-139">Recompile and redeploy.</span></span> <span data-ttu-id="f3b18-140">Sie sollten feststellen, dass der Maus auf den Cube in Ihrem immersive Kopfhörer- oder HoloLens jetzt mit Bluetooth-Maus angefügt Position wird.</span><span class="sxs-lookup"><span data-stu-id="f3b18-140">You should notice that the mouse click will now reposition the cube in your immersive headset - or HoloLens with bluetooth mouse attached.</span></span>

### <a name="game-controller-support"></a><span data-ttu-id="f3b18-141">Gamecontroller-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="f3b18-141">Game controller support</span></span>

<span data-ttu-id="f3b18-142">Gamecontroller möglich, dass eine ansprechende und bequem gestattet es dem Benutzer eine immersive Windows Mixed Reality-Erfahrung zu steuern.</span><span class="sxs-lookup"><span data-stu-id="f3b18-142">Game controllers can be a fun and convenient way of allowing the user to control an immersive Windows Mixed Reality experience.</span></span>

<span data-ttu-id="f3b18-143">Der erste Schritt beim Hinzufügen von Unterstützung für Gamecontroller zu die Windows Holographic app-Vorlage ist so die Headerklasse für die main-Datei die folgenden privaten Member-Deklarationen hinzu:</span><span class="sxs-lookup"><span data-stu-id="f3b18-143">The first step in adding support for game controllers to the Windows Holographic app template, is to add the following private member declarations to the header class for your main file:</span></span>

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

<span data-ttu-id="f3b18-144">Gamepad-Ereignisse und alle Gamepads, die zurzeit zugeordnet sind, im Konstruktor für die main-Klasse zu initialisieren:</span><span class="sxs-lookup"><span data-stu-id="f3b18-144">Initialize gamepad events, and any gamepads that are currently attached, in the constructor for your main class:</span></span>

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

<span data-ttu-id="f3b18-145">Fügen Sie der main-Klasse diese Ereignishandler hinzu.</span><span class="sxs-lookup"><span data-stu-id="f3b18-145">Add these event handlers to your main class.</span></span> <span data-ttu-id="f3b18-146">Ändern Sie den Namen der Klasse:</span><span class="sxs-lookup"><span data-stu-id="f3b18-146">Make sure to update the class name:</span></span>

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

<span data-ttu-id="f3b18-147">Zum Schluss aktualisieren Sie die Eingabe Logik zur Erkennung von Änderungen in den Zustand des Domänencontrollers.</span><span class="sxs-lookup"><span data-stu-id="f3b18-147">Finally, update the input logic to recognize changes in controller state.</span></span> <span data-ttu-id="f3b18-148">Hier verwenden wir die gleichen M_pointerPressed-Variable, die im Abschnitt oben zum Hinzufügen von Mausereignissen erläutert.</span><span class="sxs-lookup"><span data-stu-id="f3b18-148">Here, we use the same m_pointerPressed variable discussed in the section above for adding mouse events.</span></span> <span data-ttu-id="f3b18-149">Kurz vor, in dem sie die SpatialPointerPose prüft, ob die Update-Methode Folgendes hinzu:</span><span class="sxs-lookup"><span data-stu-id="f3b18-149">Add this to the Update method, just before where it checks for the SpatialPointerPose:</span></span>

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

<span data-ttu-id="f3b18-150">Vergessen Sie nicht die Ereignisse beim Bereinigen von "main"-Klasse aufgehoben werden:</span><span class="sxs-lookup"><span data-stu-id="f3b18-150">Don't forget to unregister the events when cleaning up the main class:</span></span>

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

<span data-ttu-id="f3b18-151">Kompilieren und erneut bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="f3b18-151">Recompile, and redeploy.</span></span> <span data-ttu-id="f3b18-152">Sie können jetzt anzufügen, oder koppeln, einen game Controller und verwenden, um den sich drehenden Würfels neu positionieren.</span><span class="sxs-lookup"><span data-stu-id="f3b18-152">You can now attach, or pair, a game controller and use it to reposition the spinning cube.</span></span>

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a><span data-ttu-id="f3b18-153">Wichtige Richtlinien für die Tastatur- und Mauseingaben</span><span class="sxs-lookup"><span data-stu-id="f3b18-153">Important guidelines for keyboard and mouse input</span></span>

<span data-ttu-id="f3b18-154">Es gibt einige wichtige Unterschiede in wie dieser Code für Microsoft HoloLens – kann, ein Gerät, die stützt sich hauptsächlich auf natürliche Benutzereingaben verwendet werden – im Vergleich zu, was auf einem PC Windows Mixed Reality-fähigen verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="f3b18-154">There are some key differences in how this code can be used on Microsoft HoloLens – which is a device that relies primarily on natural user input – versus what is available on a Windows Mixed Reality-enabled PC.</span></span>
* <span data-ttu-id="f3b18-155">Sie können nicht auf Tastatur- oder Mauseingaben vorhanden sein verlassen.</span><span class="sxs-lookup"><span data-stu-id="f3b18-155">You can’t rely on keyboard or mouse input to be present.</span></span> <span data-ttu-id="f3b18-156">Alle von den Funktionen Ihrer app müssen mit Blicke, Gesten und Spracheingabe zusammenarbeiten.</span><span class="sxs-lookup"><span data-stu-id="f3b18-156">All of your app's functionality must work with gaze, gesture, and speech input.</span></span>
* <span data-ttu-id="f3b18-157">Wenn eine Bluetooth-Tastatur angefügt ist, kann es hilfreich sein, Tastatureingaben zu jedem Text zu aktivieren, die Ihre app anfordern kann.</span><span class="sxs-lookup"><span data-stu-id="f3b18-157">When a Bluetooth keyboard is attached, it can be helpful to enable keyboard input for any text that your app might ask for.</span></span> <span data-ttu-id="f3b18-158">Dies kann eine hervorragende Ergänzung für Diktat, z. B. sein.</span><span class="sxs-lookup"><span data-stu-id="f3b18-158">This can be a great supplement for dictation, for example.</span></span>
* <span data-ttu-id="f3b18-159">Wenn es darum geht, Sie entwerfen Sie Ihre app, verlassen Sie sich nicht auf (z. B.) WASD und Maus sehen die Steuerelemente für Ihr Spiel.</span><span class="sxs-lookup"><span data-stu-id="f3b18-159">When it comes to designing your app, don’t rely on (for example) WASD and mouse look controls for your game.</span></span> <span data-ttu-id="f3b18-160">HoloLens dient für den Benutzer im Raum zu durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="f3b18-160">HoloLens is designed for the user to walk around the room.</span></span> <span data-ttu-id="f3b18-161">In diesem Fall steuert der Benutzer direkt die Kamera aus.</span><span class="sxs-lookup"><span data-stu-id="f3b18-161">In this case, the user controls the camera directly.</span></span> <span data-ttu-id="f3b18-162">Eine Schnittstelle zum Steuern von der Kamera im Raum verschieben/aussehen Steuerelemente wird nicht die gleiche Funktionalität bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="f3b18-162">An interface for driving the camera around the room with move/look controls won't provide the same experience.</span></span>
* <span data-ttu-id="f3b18-163">Tastatureingabe möglich, dass eine hervorragende Möglichkeit, steuern die Debuggen Aspekte Ihrer app oder einer Spiele-Engine, besonders, da der Benutzer nicht zum Verwenden der Tastatur erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="f3b18-163">Keyboard input can be an excellent way to control the debugging aspects of your app or game engine, especially since the user will not be required to use the keyboard.</span></span> <span data-ttu-id="f3b18-164">Einrichten von es ist identisch, wie Sie mit "corewindow" Ereignis-APIs gewöhnt sind.</span><span class="sxs-lookup"><span data-stu-id="f3b18-164">Wiring it up is the same as you're used to, with CoreWindow event APIs.</span></span> <span data-ttu-id="f3b18-165">In diesem Szenario können Sie auswählen, um ein Verfahren zum Konfigurieren Ihrer app zum Weiterleiten von Ereignissen zum Modus "nur Eingabe debug" Tastatur während der Debugsitzungen zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="f3b18-165">In this scenario, you might choose to implement a way to configure your app to route keyboard events to a "debug input only" mode during your debug sessions.</span></span>
* <span data-ttu-id="f3b18-166">Bluetooth-Controller funktionieren ebenfalls.</span><span class="sxs-lookup"><span data-stu-id="f3b18-166">Bluetooth controllers work as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="f3b18-167">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f3b18-167">See also</span></span>
* [<span data-ttu-id="f3b18-168">Hardware-Zubehör</span><span class="sxs-lookup"><span data-stu-id="f3b18-168">Hardware accessories</span></span>](hardware-accessories.md)
