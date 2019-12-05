---
title: Tastatur-, Maus-und Controller Eingaben in DirectX
description: Erläutert das Erstellen einer APP für Windows Mixed Reality, in der Tastatur-, Maus-und Spielcontroller verwendet werden.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Tastatur, Maus, Game Controller, Xbox Controller, hololens, Desktop, Exemplarische Vorgehensweise, Beispielcode
ms.openlocfilehash: 1e61cb50a561492fdc6849b5b231e97fab1bb6cf
ms.sourcegitcommit: 05fa75193059a2dac4b580a9eef7b6c4bb64d8d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74835096"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a><span data-ttu-id="0e01d-104">Tastatur-, Maus-und Controller Eingaben in DirectX</span><span class="sxs-lookup"><span data-stu-id="0e01d-104">Keyboard, mouse, and controller input in DirectX</span></span>

<span data-ttu-id="0e01d-105">Tastaturen, Mäuse und Spielcontroller können als nützliche Formen der Eingabe für Windows Mixed Reality-Geräte dienen.</span><span class="sxs-lookup"><span data-stu-id="0e01d-105">Keyboards, mice, and game controllers can all be useful forms of input for Windows Mixed Reality devices.</span></span> <span data-ttu-id="0e01d-106">Bluetooth-Tastaturen und-Mäuse werden sowohl in hololens unterstützt als auch beim Debuggen Ihrer APP oder als Alternative Form der Eingabe.</span><span class="sxs-lookup"><span data-stu-id="0e01d-106">Bluetooth keyboards and mice are both supported on HoloLens, for use with debugging your app or as an alternate form of input.</span></span> <span data-ttu-id="0e01d-107">Windows Mixed Reality unterstützt auch immersive Headsets, die an PCs angeschlossen sind, bei denen Mäuse, Tastaturen und Spielcontroller in der Vergangenheit die Norm waren.</span><span class="sxs-lookup"><span data-stu-id="0e01d-107">Windows Mixed Reality also supports immersive headsets attached to PCs - where mice, keyboards, and game controllers have historically been the norm.</span></span>

<span data-ttu-id="0e01d-108">Um Tastatureingaben in hololens zu verwenden, koppeln Sie eine Bluetooth-Tastatur mit Ihrem Gerät, oder verwenden Sie die virtuelle Eingabe über das Windows-Geräte Portal.</span><span class="sxs-lookup"><span data-stu-id="0e01d-108">To use keyboard input on HoloLens, pair a Bluetooth keyboard to your device or use virtual input via the Windows Device Portal.</span></span> <span data-ttu-id="0e01d-109">Wenn Sie Tastatureingaben beim Durchführen eines Windows Mixed Reality-immersiven Headsets verwenden möchten, weisen Sie der gemischten Realität den Eingabefokus zu, indem Sie das Gerät platzieren oder die Tastenkombination Windows-Taste + Y verwenden.</span><span class="sxs-lookup"><span data-stu-id="0e01d-109">To use keyboard input while wearing a Windows Mixed Reality immersive headset, assign input focus to mixed reality by putting on the device or using the Windows Key + Y keyboard combination.</span></span> <span data-ttu-id="0e01d-110">Beachten Sie, dass apps, die für hololens vorgesehen sind, Funktionen ohne angehängte Geräte bereitstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="0e01d-110">Keep in mind that apps intended for HoloLens must provide functionality without these devices attached.</span></span>

>[!NOTE]
><span data-ttu-id="0e01d-111">Die Code Ausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung C++von/CX anstelle von C + +17- C++kompatibler/WinRT, wie Sie in der [ C++ Holographic-Projektvorlage](creating-a-holographic-directx-project.md)verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0e01d-111">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="0e01d-112">Die Konzepte sind äquivalent für ein C++/WinRT-Projekt, obwohl Sie den Code übersetzen müssen.</span><span class="sxs-lookup"><span data-stu-id="0e01d-112">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="subscribe-for-corewindow-input-events"></a><span data-ttu-id="0e01d-113">Abonnieren von corewindow-Eingabe Ereignissen</span><span class="sxs-lookup"><span data-stu-id="0e01d-113">Subscribe for CoreWindow input events</span></span>

### <a name="keyboard-input"></a><span data-ttu-id="0e01d-114">Tastatureingabe</span><span class="sxs-lookup"><span data-stu-id="0e01d-114">Keyboard input</span></span>

<span data-ttu-id="0e01d-115">In der Windows Holographic-App-Vorlage fügen wir einen Ereignishandler für Tastatureingaben wie jede andere UWP-App ein.</span><span class="sxs-lookup"><span data-stu-id="0e01d-115">In the Windows Holographic app template, we include an event handler for keyboard input just like any other UWP app.</span></span> <span data-ttu-id="0e01d-116">Ihre APP beansprucht Tastatureingabe Daten in Windows Mixed Reality auf dieselbe Weise.</span><span class="sxs-lookup"><span data-stu-id="0e01d-116">Your app consumes keyboard input data the same way in Windows Mixed Reality.</span></span>

<span data-ttu-id="0e01d-117">Aus appview. cpp:</span><span class="sxs-lookup"><span data-stu-id="0e01d-117">From AppView.cpp:</span></span>

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

### <a name="virtual-keyboard-input"></a><span data-ttu-id="0e01d-118">Virtuelle Tastatureingabe</span><span class="sxs-lookup"><span data-stu-id="0e01d-118">Virtual keyboard input</span></span>
<span data-ttu-id="0e01d-119">Bei immersiven Desktop-Headsets können Sie auch virtuelle Tastaturen unterstützen, die von Windows gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="0e01d-119">For immersive desktop headsets, you can also support virtual keyboards rendered by Windows over your immersive view.</span></span> <span data-ttu-id="0e01d-120">Um dies zu unterstützen, kann Ihre APP **coretexteditcontext**implementieren.</span><span class="sxs-lookup"><span data-stu-id="0e01d-120">To support this, your app can implement **CoreTextEditContext**.</span></span> <span data-ttu-id="0e01d-121">Dadurch kann Windows den Zustand ihrer eigenen, von der APP gerenderten Textfelder verstehen, sodass die virtuelle Tastatur ordnungsgemäß zum Text beitragen kann.</span><span class="sxs-lookup"><span data-stu-id="0e01d-121">This lets Windows understand the state of your own app-rendered text boxes, so the virtual keyboard can correctly contribute to the text there.</span></span>

<span data-ttu-id="0e01d-122">Weitere Informationen zum Implementieren der coretexteditcontext-Unterstützung finden Sie im [coretexteditcontext-Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span><span class="sxs-lookup"><span data-stu-id="0e01d-122">For more information on implementing CoreTextEditContext support, see the [CoreTextEditContext sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>

### <a name="mouse-input"></a><span data-ttu-id="0e01d-123">Mauseingabe</span><span class="sxs-lookup"><span data-stu-id="0e01d-123">Mouse Input</span></span>

<span data-ttu-id="0e01d-124">Sie können auch über die Eingabe Ereignishandler von UWP corewindow auch Maus Eingaben verwenden.</span><span class="sxs-lookup"><span data-stu-id="0e01d-124">You can also use mouse input, again via the UWP CoreWindow input event handlers.</span></span> <span data-ttu-id="0e01d-125">Im folgenden wird erläutert, wie Sie die Windows Holographic-App-Vorlage ändern, um Mausklicks auf die gleiche Weise wie gedrückte Gesten zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="0e01d-125">Here's how to modify the Windows Holographic app template to support mouse clicks in the same way as pressed gestures.</span></span> <span data-ttu-id="0e01d-126">Nachdem Sie diese Änderung vorgenommen haben, wird der Cube durch einen Mausklick beim Ausführen eines immersiven Headset-Geräts neu positioniert.</span><span class="sxs-lookup"><span data-stu-id="0e01d-126">After making this modification, a mouse click while wearing an immersive headset device will reposition the cube.</span></span>

<span data-ttu-id="0e01d-127">Beachten Sie, dass UWP-apps auch unformatierte XY-Daten für die Maus mithilfe der [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) -API erhalten können.</span><span class="sxs-lookup"><span data-stu-id="0e01d-127">Note that UWP apps can also get raw XY data for the mouse by using the [MouseDevice](https://docs.microsoft.com/uwp/api/Windows.Devices.Input.MouseDevice) API.</span></span>

<span data-ttu-id="0e01d-128">Beginnen Sie mit dem Deklarieren eines neuen onpointerpressed-Handlers in appview. h:</span><span class="sxs-lookup"><span data-stu-id="0e01d-128">Start by declaring a new OnPointerPressed handler in AppView.h:</span></span>

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

<span data-ttu-id="0e01d-129">Fügen Sie in appview. cpp den folgenden Code zu SetWindow hinzu:</span><span class="sxs-lookup"><span data-stu-id="0e01d-129">In AppView.cpp, add this code to SetWindow:</span></span>

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

<span data-ttu-id="0e01d-130">Fügen Sie dann diese Definition für "onpointerpressed" am Ende der Datei ein:</span><span class="sxs-lookup"><span data-stu-id="0e01d-130">Then put this definition for OnPointerPressed at the bottom of the file:</span></span>

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

<span data-ttu-id="0e01d-131">Der soeben hinzugefügte Ereignishandler ist eine Pass-Through-Funktion für die Hauptklasse der Vorlage.</span><span class="sxs-lookup"><span data-stu-id="0e01d-131">The event handler we just added is a pass-through to the template main class.</span></span> <span data-ttu-id="0e01d-132">Ändern wir nun die Hauptklasse, um diese Pass-Through-Unterstützung zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="0e01d-132">Let's modify the main class to support this pass-through.</span></span> <span data-ttu-id="0e01d-133">Fügen Sie diese Deklaration der öffentlichen Methode der Header Datei hinzu:</span><span class="sxs-lookup"><span data-stu-id="0e01d-133">Add this public method declaration to the header file:</span></span>

```
// Handle mouse input.
       void OnPointerPressed();
```

<span data-ttu-id="0e01d-134">Sie benötigen auch diese private Member-Variable:</span><span class="sxs-lookup"><span data-stu-id="0e01d-134">You'll need this private member variable, as well:</span></span>

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

<span data-ttu-id="0e01d-135">Zum Schluss aktualisieren wir die Hauptklasse mit neuer Logik zur Unterstützung von Mausklicks.</span><span class="sxs-lookup"><span data-stu-id="0e01d-135">Finally, we will update the main class with new logic to support mouse clicks.</span></span> <span data-ttu-id="0e01d-136">Beginnen Sie mit dem Hinzufügen dieses Ereignis Handlers.</span><span class="sxs-lookup"><span data-stu-id="0e01d-136">Start by adding this event handler.</span></span> <span data-ttu-id="0e01d-137">Stellen Sie sicher, dass Sie den Klassennamen aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="0e01d-137">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

<span data-ttu-id="0e01d-138">Ersetzen Sie nun in der Update-Methode die vorhandene Logik, um eine Zeiger Pose mit folgenden Informationen zu erhalten:</span><span class="sxs-lookup"><span data-stu-id="0e01d-138">Now, in the Update method, replace the existing logic for getting a pointer pose with this:</span></span>

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

<span data-ttu-id="0e01d-139">Neukompilieren und erneut bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="0e01d-139">Recompile and redeploy.</span></span> <span data-ttu-id="0e01d-140">Beachten Sie, dass mit dem Maus Klick nun der Cube in Ihrem immersiven Headset oder hololens mit der Bluetooth-Maus angefügt wird.</span><span class="sxs-lookup"><span data-stu-id="0e01d-140">You should notice that the mouse click will now reposition the cube in your immersive headset - or HoloLens with bluetooth mouse attached.</span></span>

### <a name="game-controller-support"></a><span data-ttu-id="0e01d-141">Spiele Controller Unterstützung</span><span class="sxs-lookup"><span data-stu-id="0e01d-141">Game controller support</span></span>

<span data-ttu-id="0e01d-142">Spiele Controller können eine angenehme und bequeme Möglichkeit bieten, dem Benutzer zu ermöglichen, eine immersive Windows Mixed Reality-Darstellung zu steuern.</span><span class="sxs-lookup"><span data-stu-id="0e01d-142">Game controllers can be a fun and convenient way of allowing the user to control an immersive Windows Mixed Reality experience.</span></span>

<span data-ttu-id="0e01d-143">Der erste Schritt beim Hinzufügen von Unterstützung für Game Controller zur Windows Holographic-App-Vorlage besteht darin, die folgenden privaten Member-Deklarationen der Header Klasse für Ihre Hauptdatei hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="0e01d-143">The first step in adding support for game controllers to the Windows Holographic app template, is to add the following private member declarations to the header class for your main file:</span></span>

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

<span data-ttu-id="0e01d-144">Initialisieren Sie Gamepad-Ereignisse und alle derzeit angefügten Gamepads im Konstruktor für Ihre Hauptklasse:</span><span class="sxs-lookup"><span data-stu-id="0e01d-144">Initialize gamepad events, and any gamepads that are currently attached, in the constructor for your main class:</span></span>

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

<span data-ttu-id="0e01d-145">Fügen Sie diese Ereignishandler ihrer Hauptklasse hinzu.</span><span class="sxs-lookup"><span data-stu-id="0e01d-145">Add these event handlers to your main class.</span></span> <span data-ttu-id="0e01d-146">Stellen Sie sicher, dass Sie den Klassennamen aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="0e01d-146">Make sure to update the class name:</span></span>

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

<span data-ttu-id="0e01d-147">Aktualisieren Sie schließlich die Eingabe Logik, um Änderungen im Controller Zustand zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="0e01d-147">Finally, update the input logic to recognize changes in controller state.</span></span> <span data-ttu-id="0e01d-148">Hier verwenden wir die gleiche m_pointerPressed Variable, die im obigen Abschnitt zum Hinzufügen von Mausereignissen erläutert wurde.</span><span class="sxs-lookup"><span data-stu-id="0e01d-148">Here, we use the same m_pointerPressed variable discussed in the section above for adding mouse events.</span></span> <span data-ttu-id="0e01d-149">Fügen Sie diese der Update-Methode hinzu, kurz bevor Sie die Anwendung auf spatialpointerpose überprüft:</span><span class="sxs-lookup"><span data-stu-id="0e01d-149">Add this to the Update method, just before where it checks for the SpatialPointerPose:</span></span>

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

<span data-ttu-id="0e01d-150">Vergessen Sie nicht, die Registrierung der Ereignisse beim Bereinigen der Hauptklasse aufzuheben:</span><span class="sxs-lookup"><span data-stu-id="0e01d-150">Don't forget to unregister the events when cleaning up the main class:</span></span>

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

<span data-ttu-id="0e01d-151">Neukompilieren und erneut bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="0e01d-151">Recompile, and redeploy.</span></span> <span data-ttu-id="0e01d-152">Sie können jetzt einen Spielcontroller anfügen oder koppeln und ihn verwenden, um den drehenden Cube neu zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="0e01d-152">You can now attach, or pair, a game controller and use it to reposition the spinning cube.</span></span>

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a><span data-ttu-id="0e01d-153">Wichtige Richtlinien für Tastatur-und Maus Eingaben</span><span class="sxs-lookup"><span data-stu-id="0e01d-153">Important guidelines for keyboard and mouse input</span></span>

<span data-ttu-id="0e01d-154">Es gibt einige wichtige Unterschiede bei der Verwendung dieses Codes für Microsoft hololens – bei dem es sich um ein Gerät handelt, das hauptsächlich auf natürlichen Benutzereingaben basiert – im Vergleich zu den Funktionen, die auf einem Windows Mixed Reality-fähigen PC verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="0e01d-154">There are some key differences in how this code can be used on Microsoft HoloLens – which is a device that relies primarily on natural user input – versus what is available on a Windows Mixed Reality-enabled PC.</span></span>
* <span data-ttu-id="0e01d-155">Sie können sich nicht darauf verlassen, dass Tastatur-oder Maus Eingaben vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="0e01d-155">You can’t rely on keyboard or mouse input to be present.</span></span> <span data-ttu-id="0e01d-156">Alle Funktionen Ihrer APP müssen mit Blick, Gesten und Spracheingaben funktionieren.</span><span class="sxs-lookup"><span data-stu-id="0e01d-156">All of your app's functionality must work with gaze, gesture, and speech input.</span></span>
* <span data-ttu-id="0e01d-157">Wenn eine Bluetooth-Tastatur angefügt wird, kann es hilfreich sein, Tastatureingaben für jeden Text zu aktivieren, der von Ihrer APP angefordert werden kann.</span><span class="sxs-lookup"><span data-stu-id="0e01d-157">When a Bluetooth keyboard is attached, it can be helpful to enable keyboard input for any text that your app might ask for.</span></span> <span data-ttu-id="0e01d-158">Dies kann z. b. eine hervor artige Ergänzung zum Diktat darstellen.</span><span class="sxs-lookup"><span data-stu-id="0e01d-158">This can be a great supplement for dictation, for example.</span></span>
* <span data-ttu-id="0e01d-159">Wenn Sie Ihre APP entwerfen möchten, verlassen Sie sich nicht auf (z. b.) WASD-und Mauszeiger-Steuerelemente für Ihr Spiel.</span><span class="sxs-lookup"><span data-stu-id="0e01d-159">When it comes to designing your app, don’t rely on (for example) WASD and mouse look controls for your game.</span></span> <span data-ttu-id="0e01d-160">Hololens ist dafür konzipiert, dass der Benutzer den Raum durchläuft.</span><span class="sxs-lookup"><span data-stu-id="0e01d-160">HoloLens is designed for the user to walk around the room.</span></span> <span data-ttu-id="0e01d-161">In diesem Fall steuert der Benutzer die Kamera direkt.</span><span class="sxs-lookup"><span data-stu-id="0e01d-161">In this case, the user controls the camera directly.</span></span> <span data-ttu-id="0e01d-162">Eine Schnittstelle zum Steuern der Kamera um den Raum mit Verschiebe-und Bild-Steuerelementen bietet nicht die gleiche Umgebung.</span><span class="sxs-lookup"><span data-stu-id="0e01d-162">An interface for driving the camera around the room with move/look controls won't provide the same experience.</span></span>
* <span data-ttu-id="0e01d-163">Tastatureingaben können eine hervorragende Möglichkeit zum Steuern der debuggingaspekte Ihrer APP oder Spiel-Engine sein, insbesondere, da der Benutzer die Tastatur nicht verwenden muss.</span><span class="sxs-lookup"><span data-stu-id="0e01d-163">Keyboard input can be an excellent way to control the debugging aspects of your app or game engine, especially since the user will not be required to use the keyboard.</span></span> <span data-ttu-id="0e01d-164">Die Verknüpfung ist identisch mit der Verwendung von corewindow-Ereignis-APIs.</span><span class="sxs-lookup"><span data-stu-id="0e01d-164">Wiring it up is the same as you're used to, with CoreWindow event APIs.</span></span> <span data-ttu-id="0e01d-165">In diesem Szenario können Sie eine Möglichkeit implementieren, um Ihre APP so zu konfigurieren, dass Tastatur Ereignisse während der Debugsitzungen an den Modus "nur debugeingabe" weitergeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="0e01d-165">In this scenario, you might choose to implement a way to configure your app to route keyboard events to a "debug input only" mode during your debug sessions.</span></span>
* <span data-ttu-id="0e01d-166">Bluetooth-Controller sind ebenfalls funktionsfähig.</span><span class="sxs-lookup"><span data-stu-id="0e01d-166">Bluetooth controllers work as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="0e01d-167">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="0e01d-167">See also</span></span>
* [<span data-ttu-id="0e01d-168">Hardware-Zubehör</span><span class="sxs-lookup"><span data-stu-id="0e01d-168">Hardware accessories</span></span>](hardware-accessories.md)
