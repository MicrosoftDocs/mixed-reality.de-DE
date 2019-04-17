---
title: Blicke, Gesten und während der Übertragung von Controllern in DirectX
description: Kombinieren vom Blicke, Gesten und während der Übertragung Controllern Eingabe kommen, können Sie einen Benutzer, platzieren Sie ggf. ein Hologramm in Ihrer app aktivieren.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Blicke, Gesten, während der Übertragung Controller, Directx, Eingabe, Hologramme
ms.openlocfilehash: 7cee3d3d7fbcd903eae0376e205034b9cc4ead3b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605094"
---
# <a name="gaze-gestures-and-motion-controllers-in-directx"></a><span data-ttu-id="2e715-104">Blicke, Gesten und während der Übertragung von Controllern in DirectX</span><span class="sxs-lookup"><span data-stu-id="2e715-104">Gaze, gestures, and motion controllers in DirectX</span></span>

<span data-ttu-id="2e715-105">Wenn Sie vorhaben, um direkt auf der Plattform zu erstellen, müssen vom Benutzer – z. B., in denen der Benutzer über sucht eine Eingabe kommen behandeln [Head Blicke](gaze.md) und was der Benutzer ausgewählt hat, mit [Gesten](gestures.md) oder [motion Controller](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="2e715-105">If you're going to build directly on top of the platform, you will have to handle input coming from the user - such as where the user is looking via [head gaze](gaze.md) and what the user has selected with [gestures](gestures.md) or [motion controllers](motion-controllers.md).</span></span> <span data-ttu-id="2e715-106">Kombinieren diese Formen der Eingabe, können Sie einem Benutzer platzieren ermöglichen eine [– Hologramm](hologram.md) in Ihrer app.</span><span class="sxs-lookup"><span data-stu-id="2e715-106">Combining these forms of input, you can enable a user to place a [hologram](hologram.md) in your app.</span></span> <span data-ttu-id="2e715-107">Die [holographic app-Vorlage](creating-a-holographic-directx-project.md) enthält ein Beispiel einfach zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="2e715-107">The [holographic app template](creating-a-holographic-directx-project.md) has an easy to use example.</span></span>

>[!NOTE]
><span data-ttu-id="2e715-108">Die Codeausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstatt C ++ 17-kompatible C++"/ WinRT", wie in der [ C++ holographic Projektvorlage](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="2e715-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="2e715-109">Die Konzepte sind Entsprechung für einen C++"/ WinRT"-Projekt, aber Sie benötigen, um den Code zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="2e715-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="gaze-input"></a><span data-ttu-id="2e715-110">Eingabe via Anvisieren</span><span class="sxs-lookup"><span data-stu-id="2e715-110">Gaze input</span></span>

<span data-ttu-id="2e715-111">Des Benutzers den Zugriff auf [Head Blicke](gaze.md), Sie verwenden die [SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx) Typ.</span><span class="sxs-lookup"><span data-stu-id="2e715-111">To access the user's [head gaze](gaze.md), you use the [SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx) type.</span></span> <span data-ttu-id="2e715-112">Die holographic app-Vorlage enthält die grundlegenden Code für das Verständnis Blicke.</span><span class="sxs-lookup"><span data-stu-id="2e715-112">The holographic app template includes basic code for understanding gaze.</span></span> <span data-ttu-id="2e715-113">Dieser Code stellt einen Vektor zeigt Weiterleiten von einschließlich Augen des Benutzers unter Berücksichtigung des Geräts-Position und Ausrichtung in einem bestimmten [Koordinatensystem](coordinate-systems-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="2e715-113">This code provides a vector pointing forward from between the user's eyes, taking into account the device's position and orientation in a given [coordinate system](coordinate-systems-in-directx.md).</span></span>




```cpp
void SpinningCubeRenderer::PositionHologram(SpatialPointerPose^ pointerPose)
{
    if (pointerPose != nullptr)
    {
        // Get the gaze direction relative to the given coordinate system.
        const float3 headPosition    = pointerPose->Head->Position;
        const float3 headDirection   = pointerPose->Head->ForwardDirection;
    
        // The hologram is positioned two meters along the user's gaze direction.
        static const float distanceFromUser = 2.0f; // meters
        const float3 gazeAtTwoMeters        = headPosition + (distanceFromUser * headDirection);
    
        // This will be used as the translation component of the hologram's
        // model transform.
        SetPosition(gazeAtTwoMeters);
    }
}
```

<span data-ttu-id="2e715-114">Sie können sich z.B. finden: "Aber woher das Koordinatensystem stammen aus?"</span><span class="sxs-lookup"><span data-stu-id="2e715-114">You may find yourself asking: "But where does the coordinate system come from?"</span></span>

<span data-ttu-id="2e715-115">Lassen Sie uns diese Frage zu beantworten.</span><span class="sxs-lookup"><span data-stu-id="2e715-115">Let's answer that question.</span></span> <span data-ttu-id="2e715-116">In unserem AppMain des **Update** -Funktion verarbeitet eine räumliche Eingabeereignis durch diese relativ zu das Koordinatensystem für unsere StationaryFrameOfReference anfordern.</span><span class="sxs-lookup"><span data-stu-id="2e715-116">In our AppMain's **Update** function, we processed a spatial input event by acquiring it relative to the coordinate system for our StationaryFrameOfReference.</span></span> <span data-ttu-id="2e715-117">Denken Sie daran, dass die StationaryFrameOfReference erstellt wurde, wenn wir richten die [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx), und das Koordinatensystem abgerufen wurde, am Anfang des [Update](rendering-in-directx.md).</span><span class="sxs-lookup"><span data-stu-id="2e715-117">Recall that the StationaryFrameOfReference was created when we set up the [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx), and the coordinate system was acquired at the start of [Update](rendering-in-directx.md).</span></span>




```cpp
// Check for new input state since the last frame.
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
if (pointerState != nullptr)
{
    // When a Pressed gesture is detected, the sample hologram will be repositioned
    // two meters in front of the user.
    m_spinningCubeRenderer->PositionHologram(
        pointerState->TryGetPointerPose(currentCoordinateSystem)
        );
}
```

<span data-ttu-id="2e715-118">Beachten Sie, dass die Daten in einen Zeiger-Zustand, der eine Art gebunden ist.</span><span class="sxs-lookup"><span data-stu-id="2e715-118">Note that the data is tied to a pointer state of some kind.</span></span> <span data-ttu-id="2e715-119">Wir erhalten diese aus dem eine räumliche Eingabeereignis.</span><span class="sxs-lookup"><span data-stu-id="2e715-119">We get this from a spatial input event.</span></span> <span data-ttu-id="2e715-120">Das Ereignisobjekt für die Daten enthält einem Koordinatensystem, sodass Sie immer die Blicke Richtung zum Zeitpunkt des Ereignisses auf den spatial Koordinatensystem beziehen können, die Sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="2e715-120">The event data object includes a coordinate system, so that you can always relate the gaze direction at the time of the event to whatever spatial coordinate system you need.</span></span> <span data-ttu-id="2e715-121">In der Tat müssen Sie dies tun, um den Zeiger Haltung zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="2e715-121">In fact, you must do so in order to get the pointer pose.</span></span>

> [!NOTE]
> <span data-ttu-id="2e715-122">Weitere Anleitungen, die speziell für HoloLens 2 [bald](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="2e715-122">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="gesture-and-motion-controller-input"></a><span data-ttu-id="2e715-123">Gesten und während der Übertragung Controller Eingabe</span><span class="sxs-lookup"><span data-stu-id="2e715-123">Gesture and motion controller input</span></span>

<span data-ttu-id="2e715-124">In Windows Mixed Reality, beide übergeben [Gesten](gestures.md) und [motion Controller](motion-controllers.md) erfolgt über die gleichen räumliche Eingabe-APIs finden Sie in der [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) Namespace.</span><span class="sxs-lookup"><span data-stu-id="2e715-124">In Windows Mixed Reality, both hand [gestures](gestures.md) and [motion controllers](motion-controllers.md) are handled through the same spatial input APIs, found in the [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) namespace.</span></span> <span data-ttu-id="2e715-125">Dadurch können Sie Baseler Ausschusses für häufig verwendete Aktionen wie **wählen** drückt die gleiche Weise wie für praktische und Motion-Controller.</span><span class="sxs-lookup"><span data-stu-id="2e715-125">This enables you to easily handle common actions like **Select** presses the same way across both hands and motion controllers.</span></span>

<span data-ttu-id="2e715-126">Es gibt zwei Ebenen der API, die Sie abzielen können, bei der Verarbeitung von Gesten oder Motion-Controllern in mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="2e715-126">There are two levels of API you can target when handling gestures or motion controllers in mixed reality:</span></span>
* <span data-ttu-id="2e715-127">[Interaktionen](gestures.md#the-two-core-gestures-of-hololens) ([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx), [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx) und [SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx)), der Zugriff mithilfe einer [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)</span><span class="sxs-lookup"><span data-stu-id="2e715-127">[Interactions](gestures.md#the-two-core-gestures-of-hololens) ([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx), [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx) and [SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx)), accessed using a [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)</span></span>
* <span data-ttu-id="2e715-128">[Zusammengesetzte Gesten](gestures.md#composite-gestures) ([Tapped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx), enthalten, Manipulation, Navigation), der Zugriff mithilfe einer [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)</span><span class="sxs-lookup"><span data-stu-id="2e715-128">[Composite gestures](gestures.md#composite-gestures) ([Tapped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx), Hold, Manipulation, Navigation), accessed using a [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)</span></span>

### <a name="selectmenugrasptouchpadthumbstick-interactions-spatialinteractionmanager"></a><span data-ttu-id="2e715-129">Wählen Sie/Menü/verstehen/Touchpad/Ministick Interaktionen: SpatialInteractionManager</span><span class="sxs-lookup"><span data-stu-id="2e715-129">Select/Menu/Grasp/Touchpad/Thumbstick interactions: SpatialInteractionManager</span></span>

<span data-ttu-id="2e715-130">Zum Erkennen von Low-Level drückt, Releases und Updates für praktische und Eingabegeräte in Windows Mixed Reality starten Sie über eine [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx).</span><span class="sxs-lookup"><span data-stu-id="2e715-130">To detect low-level presses, releases and updates across hands and input devices in Windows Mixed Reality, you start from a [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx).</span></span> <span data-ttu-id="2e715-131">Die SpatialInteractionManager hat ein Ereignis, das Sie informiert die app nach einer Hand oder Motion-Controller verfügt über Eingabe erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="2e715-131">The SpatialInteractionManager has an event that informs the app when a hand or motion controller has detected input.</span></span>

<span data-ttu-id="2e715-132">Es gibt drei wichtige Arten von SpatialInteractionSource, die durch einen anderen Wert für die SpatialInteractionSourceKind dargestellt:</span><span class="sxs-lookup"><span data-stu-id="2e715-132">There are three key kinds of SpatialInteractionSource, each represented by a different SpatialInteractionSourceKind value:</span></span>
* <span data-ttu-id="2e715-133">**Hand** erkannte Hand eines Benutzers darstellt.</span><span class="sxs-lookup"><span data-stu-id="2e715-133">**Hand** represents a user's detected hand.</span></span> <span data-ttu-id="2e715-134">Hand-Datenquellen stehen nur für HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2e715-134">Hand sources are available only on HoloLens.</span></span>
* <span data-ttu-id="2e715-135">**Controller** einen gekoppelten Motion-Controller darstellt.</span><span class="sxs-lookup"><span data-stu-id="2e715-135">**Controller** represents a paired motion controller.</span></span> <span data-ttu-id="2e715-136">Während der Übertragung Controller bieten eine Vielzahl von Funktionen, z.B.: Wählen Sie die Trigger, Menüschaltflächen, verstehen Schaltflächen, Touchpad und Thumbsticks.</span><span class="sxs-lookup"><span data-stu-id="2e715-136">Motion controllers can offer a variety of capabilities, for example: Select triggers, Menu buttons, Grasp buttons, touchpads and thumbsticks.</span></span>
* <span data-ttu-id="2e715-137">**Voice** des Benutzers Voice Schlüsselwörter System hat Vorträge darstellt.</span><span class="sxs-lookup"><span data-stu-id="2e715-137">**Voice** represents the user's voice speaking system-detected keywords.</span></span> <span data-ttu-id="2e715-138">Das Drücken einer Option Einfügen wird und freizugeben, wenn der Benutzer sagt "Select".</span><span class="sxs-lookup"><span data-stu-id="2e715-138">This will inject a Select press and release whenever the user says "Select".</span></span>

<span data-ttu-id="2e715-139">Um drückt auf allen der folgenden Quellen Interaktion zu erkennen, können Sie das Ereignis SourcePressed auf SpatialInteractionManager in SpatialInputHandler.cpp behandeln:</span><span class="sxs-lookup"><span data-stu-id="2e715-139">To detect presses across any of these interaction sources, you can handle the SourcePressed event on SpatialInteractionManager in SpatialInputHandler.cpp:</span></span>


```cpp
m_interactionManager = SpatialInteractionManager::GetForCurrentView();
    
// Bind a handler to the SourcePressed event.
m_sourcePressedEventToken =
    m_interactionManager->SourcePressed +=
        ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
            bind(&SpatialInputHandler::OnSourcePressed, this, _1, _2)
            );
```

<span data-ttu-id="2e715-140">Dieses Ereignis gedrückte wird asynchron zu Ihrer app gesendet.</span><span class="sxs-lookup"><span data-stu-id="2e715-140">This pressed event is sent to your app asynchronously.</span></span> <span data-ttu-id="2e715-141">Ihre app oder eine Spiele-Engine möglicherweise ausführen möchten sofort verarbeiten oder möglicherweise möchten die Daten in der Eingabe verarbeiten Routine in die Warteschlange.</span><span class="sxs-lookup"><span data-stu-id="2e715-141">Your app or game engine may want to perform some processing right away or you may want to queue up the event data in your input processing routine.</span></span>

<span data-ttu-id="2e715-142">Die Vorlage enthält eine Hilfsklasse, um Ihnen den Einstieg erleichtern.</span><span class="sxs-lookup"><span data-stu-id="2e715-142">The template includes a helper class to get you started.</span></span> <span data-ttu-id="2e715-143">Diese Vorlage forgoes Verarbeitungsschritte aus Gründen der Einfachheit des Entwurfs.</span><span class="sxs-lookup"><span data-stu-id="2e715-143">This template forgoes any processing for simplicity of design.</span></span> <span data-ttu-id="2e715-144">Die Hilfsklasse behält den Überblick, ob ein oder mehrere **Pressed** Ereignisse aufgetreten sind, seit der letzten **Update** aufrufen.</span><span class="sxs-lookup"><span data-stu-id="2e715-144">The helper class keeps track of whether one or more **Pressed** events occurred since the last **Update** call.</span></span> <span data-ttu-id="2e715-145">Von SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="2e715-145">From SpatialInputHandler.cpp:</span></span>




```cpp
void SpatialInputHandler::OnSourcePressed(SpatialInteractionManager^ sender, SpatialInteractionSourceEventArgs^ args)
{
    m_sourceState = args->State;
    
    //
    // TODO: In your app or game engine, rewrite this method to queue
    //       input events in your input class or event handler.
    //
}
```

<span data-ttu-id="2e715-146">Wenn also es gibt die [SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) für die letzten Eingabeereignis während des nächsten Updates.</span><span class="sxs-lookup"><span data-stu-id="2e715-146">If so, it returns the [SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) for the most recent input event during the next Update.</span></span> <span data-ttu-id="2e715-147">Von SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="2e715-147">From SpatialInputHandler.cpp:</span></span>




```cpp
// Checks if the user performed an input gesture since the last call to this method.
// Allows the main update loop to check for asynchronous changes to the user
// input state.
SpatialInteractionSourceState^ SpatialInputHandler::CheckForInput()
{
    SpatialInteractionSourceState^ sourceState = m_sourceState;
    m_sourceState = nullptr;
    return sourceState;
}
```

<span data-ttu-id="2e715-148">Beachten Sie, dass der obige Code alle behandelt drückt die gleiche Weise, ob der Benutzer einen primären ausführt **wählen** drücken oder ein sekundäres Replikat **im Menü** oder **verstehen** drücken.</span><span class="sxs-lookup"><span data-stu-id="2e715-148">Note that the code above will treat all presses the same way, whether the user is performing a primary **Select** press or a secondary **Menu** or **Grasp** press.</span></span> <span data-ttu-id="2e715-149">Die **wählen** Press ist eine primäre Form der Interaktion über praktische, Controller oder Stimme, die ausgelöst werden, entweder durch ein manuelles eine tippbewegung ausführen, auf ein Controller während der Übertragung mit der primären Trigger/Schaltfläche gedrückt, während der Übertragung oder des Benutzers unterstützt Voice-sagen "Select".</span><span class="sxs-lookup"><span data-stu-id="2e715-149">The **Select** press is a primary form of interaction supported across hands, motion controllers and voice, triggered either by a hand performing an air-tap, a motion controller with its primary trigger/button pressed, or the user's voice saying "Select".</span></span> <span data-ttu-id="2e715-150">Drückt die Option darstellen des Benutzers Absicht an, die – Hologramm aktiviert werden, die sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="2e715-150">Select presses represent the user's intention to activate the hologram they are targeting.</span></span>

<span data-ttu-id="2e715-151">Welche Art von Press verständlich auftritt, ändern wir den SpatialInteractionManager::SourceUpdated-Ereignishandler.</span><span class="sxs-lookup"><span data-stu-id="2e715-151">To reason about which kind of press is occurring, we will modify the SpatialInteractionManager::SourceUpdated event handler.</span></span> <span data-ttu-id="2e715-152">Unser Code verstehen drückt erkennt, (sofern verfügbar) und diese verwenden, um den Cube neu zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="2e715-152">Our code will detect Grasp presses (where available) and use them to reposition the cube.</span></span> <span data-ttu-id="2e715-153">Wenn Sie verstehen, nicht verfügbar ist, verwenden wir wählen drückt stattdessen.</span><span class="sxs-lookup"><span data-stu-id="2e715-153">If Grasp is not available, we will use Select presses instead.</span></span>

<span data-ttu-id="2e715-154">Fügen Sie die folgenden privaten Member-Deklarationen zu SpatialInputHandler.h:</span><span class="sxs-lookup"><span data-stu-id="2e715-154">Add the following private member declarations to SpatialInputHandler.h:</span></span> 


```cpp
void OnSourceUpdated(
       Windows::UI::Input::Spatial::SpatialInteractionManager^ sender,
       Windows::UI::Input::Spatial::SpatialInteractionSourceEventArgs^ args);
   Windows::Foundation::EventRegistrationToken m_sourceUpdatedEventToken;
```

<span data-ttu-id="2e715-155">Open SpatialInputHandler.cpp.</span><span class="sxs-lookup"><span data-stu-id="2e715-155">Open SpatialInputHandler.cpp.</span></span> <span data-ttu-id="2e715-156">Fügen Sie die folgenden ereignisregistrierung an den Konstruktor hinzu:</span><span class="sxs-lookup"><span data-stu-id="2e715-156">Add the following event registration to the constructor:</span></span> 


```cpp
m_sourceUpdatedEventToken =
       m_interactionManager->SourceUpdated +=
       ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
           bind(&SpatialInputHandler::OnSourceUpdated, this, _1, _2)
           );
```

<span data-ttu-id="2e715-157">Dies ist der Code des ereignishandlers.</span><span class="sxs-lookup"><span data-stu-id="2e715-157">This is the event handler code.</span></span> <span data-ttu-id="2e715-158">Wenn die Eingabequelle verstanden hat, wird der Zeiger Haltung für von der Aktualisierungsschleife des nächsten gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="2e715-158">If the input source is experiencing a Grasp, the pointer pose will be stored for the next update loop.</span></span> <span data-ttu-id="2e715-159">Andernfalls wird für eine Option, drücken Sie stattdessen überprüft.</span><span class="sxs-lookup"><span data-stu-id="2e715-159">Otherwise, it will check for a Select press instead.</span></span> <span data-ttu-id="2e715-160">Von SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="2e715-160">From SpatialInputHandler.cpp:</span></span>




```cpp
void SpatialInputHandler::OnSourceUpdated(SpatialInteractionManager^ sender, SpatialInteractionSourceEventArgs^ args)
{
    if (args->State->Source->IsGraspSupported)
    {
        if (args->State->IsGrasped)
        {
            m_sourceState = args->State;
        }
    }
    else
    {
        if (args->State->IsSelectPressed)
        {
            m_sourceState = args->State;
        }
    }
}
```

<span data-ttu-id="2e715-161">Stellen Sie sicher, dass den Ereignishandler im Destruktor aufgehoben werden.</span><span class="sxs-lookup"><span data-stu-id="2e715-161">Make sure to unregister the event handler in the destructor.</span></span> <span data-ttu-id="2e715-162">Von SpatialInputHandler.cpp:</span><span class="sxs-lookup"><span data-stu-id="2e715-162">From SpatialInputHandler.cpp:</span></span>


```cpp
m_interactionManager->SourceUpdated -= m_sourcePressedEventToken;
```

<span data-ttu-id="2e715-163">Kompilieren Sie erneut, und klicken Sie dann erneut bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="2e715-163">Recompile, and then redeploy.</span></span> <span data-ttu-id="2e715-164">Ihr Vorlagenprojekt sollte jetzt verstehen von Interaktionen an Position sich drehenden Würfels erkennen zu können.</span><span class="sxs-lookup"><span data-stu-id="2e715-164">Your template project should now be able to recognize Grasp interactions to reposition the spinning cube.</span></span>

<span data-ttu-id="2e715-165">Die SpatialInteractionSource-API unterstützt die Controller, mit einer Vielzahl von Funktionen.</span><span class="sxs-lookup"><span data-stu-id="2e715-165">The SpatialInteractionSource API supports controllers with a wide range of capabilities.</span></span> <span data-ttu-id="2e715-166">Im oben gezeigten Beispiel überprüfen wir ermitteln, ob verstehen unterstützt wird, bevor Sie versuchen, die sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="2e715-166">In the example shown above, we check to see if Grasp is supported before trying to use it.</span></span> <span data-ttu-id="2e715-167">Die SpatialInteractionSource unterstützt die folgenden optionalen Funktionen über die allgemeinen **wählen** drücken:</span><span class="sxs-lookup"><span data-stu-id="2e715-167">The SpatialInteractionSource supports the following optional features beyond the common **Select** press:</span></span>
* <span data-ttu-id="2e715-168">**Schaltfläche:** Überprüfen Sie durch Überprüfen der IsMenuSupported-Eigenschaft unterstützen.</span><span class="sxs-lookup"><span data-stu-id="2e715-168">**Menu button:** Check support by inspecting the IsMenuSupported property.</span></span> <span data-ttu-id="2e715-169">Wenn unterstützt, überprüfen Sie die [SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) Eigenschaft, um zu ermitteln, ob die Menüschaltfläche gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="2e715-169">When supported, check the [SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) property to find out if the menu button is pressed.</span></span>
* <span data-ttu-id="2e715-170">**Verstehen Sie die Schaltfläche:** Überprüfen Sie durch Überprüfen der IsGraspSupported-Eigenschaft unterstützen.</span><span class="sxs-lookup"><span data-stu-id="2e715-170">**Grasp button:** Check support by inspecting the IsGraspSupported property.</span></span> <span data-ttu-id="2e715-171">Wenn unterstützt, überprüfen Sie die [SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) Eigenschaft, um herauszufinden, ob verstehen aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="2e715-171">When supported, check the [SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) property to find out if grasp is activated.</span></span>

<span data-ttu-id="2e715-172">Für Controller verwendet hat die SpatialInteractionSource eine Controller-Eigenschaft, mit zusätzlichen Funktionen.</span><span class="sxs-lookup"><span data-stu-id="2e715-172">For controllers, the SpatialInteractionSource has a Controller property with additional capabilities.</span></span>
* <span data-ttu-id="2e715-173">**HasThumbstick:** Bei "true", hat der Controller eine Ministick an.</span><span class="sxs-lookup"><span data-stu-id="2e715-173">**HasThumbstick:** If true, the controller has a thumbstick.</span></span> <span data-ttu-id="2e715-174">Überprüfen Sie die [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) Eigenschaft der SpatialInteractionSourceState Ministick abrufen x und y-Werte (ThumbstickX und ThumbstickY) sowie ihren aktuellen Status (IsThumbstickPressed).</span><span class="sxs-lookup"><span data-stu-id="2e715-174">Inspect the [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) property of the SpatialInteractionSourceState to acquire the thumbstick x and y values (ThumbstickX and ThumbstickY), as well as its pressed state (IsThumbstickPressed).</span></span>
* <span data-ttu-id="2e715-175">**HasTouchpad:** Bei "true", hat der Controller Touchpads an.</span><span class="sxs-lookup"><span data-stu-id="2e715-175">**HasTouchpad:** If true, the controller has a touchpad.</span></span> <span data-ttu-id="2e715-176">Überprüfen Sie die ControllerProperties-Eigenschaft, der die SpatialInteractionSourceState zum Abrufen der Touchpad x- und y Werte (TouchpadX und TouchpadY), und wissen, ob der Benutzer das Pad "" (IsTouchpadTouched) berührt, und wenn sie das Touchpad nach unten (drücken, werden IsTouchpadPressed).</span><span class="sxs-lookup"><span data-stu-id="2e715-176">Inspect the ControllerProperties property of the SpatialInteractionSourceState to acquire the touchpad x and y values (TouchpadX and TouchpadY), and to know if the user is touching the pad (IsTouchpadTouched) and if they are pressing the touchpad down (IsTouchpadPressed).</span></span>
* <span data-ttu-id="2e715-177">**SimpleHapticsController:** Die SimpleHapticsController-API für den Controller können Sie die Funktionen Haptics des Controllers zu überprüfen, und sie können außerdem zum Übermitteln von haptischem Feedback zu steuern.</span><span class="sxs-lookup"><span data-stu-id="2e715-177">**SimpleHapticsController:** The SimpleHapticsController API for the controller allows you to inspect the haptics capabilities of the controller, and it also allows you to control haptic feedback.</span></span>

<span data-ttu-id="2e715-178">Beachten Sie, dass der Bereich für Touchpad und Ministick von – 1, 1 für beide Achsen (von unten nach oben und von links nach rechts).</span><span class="sxs-lookup"><span data-stu-id="2e715-178">Note that the range for touchpad and thumbstick from -1 to 1 for both axes (from bottom to top, and from left to right).</span></span> <span data-ttu-id="2e715-179">Der Bereich für den analogen Trigger, die mithilfe der SpatialInteractionSourceState::SelectPressedValue-Eigenschaft zugegriffen wird, hat es sich um einen Bereich von 0 bis 1.</span><span class="sxs-lookup"><span data-stu-id="2e715-179">The range for the analog trigger, which is accessed using the SpatialInteractionSourceState::SelectPressedValue property, has a range of 0 to 1.</span></span> <span data-ttu-id="2e715-180">Ein Wert von 1 korreliert mit IsSelectPressed ist gleich "true". Jeder andere Wert korreliert mit IsSelectPressed ist gleich "false".</span><span class="sxs-lookup"><span data-stu-id="2e715-180">A value of 1 correlates with IsSelectPressed being equal to true; any other value correlates with IsSelectPressed being equal to false.</span></span>

<span data-ttu-id="2e715-181">Beachten Sie, dass für eine Hand und ein Controller, mit SpatialInteractionSourceState::Properties::TryGetLocation Hand-Position des Benutzers erhalten – Dies unterscheidet sich von den Zeiger darstellen des Controllers zeigen Chow darstellt.</span><span class="sxs-lookup"><span data-stu-id="2e715-181">Note that for both a hand and a controller, using SpatialInteractionSourceState::Properties::TryGetLocation will provide the user's hand position - this is distinct from the pointer pose representing the controller's pointing ray.</span></span> <span data-ttu-id="2e715-182">Wenn Sie etwa an der Hand Position zeichnen möchten, verwenden Sie TryGetLocation.</span><span class="sxs-lookup"><span data-stu-id="2e715-182">If you want to draw something at the hand location, use TryGetLocation.</span></span> <span data-ttu-id="2e715-183">Wenn Sie von der Spitze des Controllers Raycast möchten, rufen Sie zeigen Strahl aus TryGetInteractionSourcePose auf die SpatialPointerPose aus.</span><span class="sxs-lookup"><span data-stu-id="2e715-183">If you want to raycast from the tip of the controller, get the pointing ray from TryGetInteractionSourcePose on the SpatialPointerPose.</span></span>

<span data-ttu-id="2e715-184">Sie können auch die anderen Ereignisse auf SpatialInteractionManager, z. B. SourceDetected und SourceLost, zu reagieren, wenn die Hände einzugeben oder zu verlassen, anzeigen oder wenn sie für oder gegen die bereit Position (Index Finger ausgelöst mit Palm weiterleiten) Verschieben des Geräts, oder wenn motion Controller sind die ein-und aktiviert wird oder werden zugeordnet/Ungepaarte.</span><span class="sxs-lookup"><span data-stu-id="2e715-184">You can also use the other events on SpatialInteractionManager, such as SourceDetected and SourceLost, to react when hands enter or leave the device's view or when they move in or out of the ready position (index finger raised with palm forward), or when motion controllers are turned on/off or are paired/unpaired.</span></span>

### <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="2e715-185">Ziehpunkt Haltung im Vergleich zu zeigenden Haltung</span><span class="sxs-lookup"><span data-stu-id="2e715-185">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="2e715-186">Windows Mixed Reality unterstützt Controller, die während der Übertragung in einer Vielzahl von Formfaktoren, des Controllers Entwurf unterscheidet sich in der Beziehung zwischen Hand-Position des Benutzers und der natürliche "Weiterleiten" Richtung dieser apps sollten mit auf beim Rendern der Controller.</span><span class="sxs-lookup"><span data-stu-id="2e715-186">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="2e715-187">Um diese Controller besser darstellen zu können, gibt es zwei Arten von ist, die Sie für jede Quelle Interaktion untersuchen können:</span><span class="sxs-lookup"><span data-stu-id="2e715-187">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source:</span></span>
* <span data-ttu-id="2e715-188">Die **Ziehpunkt Haltung**, den Speicherort der dies im Handumdrehen einer Hand, die von einem HoloLens erkannt werden, oder dies mit einem Controller während der Übertragung im Handumdrehen darstellt.</span><span class="sxs-lookup"><span data-stu-id="2e715-188">The **grip pose**, representing the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>
    * <span data-ttu-id="2e715-189">Für immersive Headsets, diese Haltung wird am besten zum Rendern **des Benutzers manuell** oder **frei, die ein Objekt des Benutzers verfügen**, z. B. eine "sword" oder dem damoklesschwert.</span><span class="sxs-lookup"><span data-stu-id="2e715-189">On immersive headsets, this pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span>
    * <span data-ttu-id="2e715-190">Die **fassen Sie Position**: Der Schwerpunkt Palm, wenn der Controller natürlich mit angepasst nach links oder rechts zentriert die Position in den Ziehpunkt.</span><span class="sxs-lookup"><span data-stu-id="2e715-190">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span>
    * <span data-ttu-id="2e715-191">Die **fassen Sie die rechte Achse die Ausrichtung**: Wenn Sie Ihre Hand, um einen flachen 5 Finger Haltung bilden vollständig geöffnet haben, dem Strahl, der ist normal, zu Ihrem Palm (vorwärts vom linken Palm, rückwärts von rechts Palm)</span><span class="sxs-lookup"><span data-stu-id="2e715-191">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
    * <span data-ttu-id="2e715-192">Die **fassen Sie die Ausrichtung, vorwärts gerichtete Achse**: Wenn Sie Ihre Hand schließen, teilweise (als ob den Controller enthält), der vom Strahl, der "forward" über die Tube gebildet, indem die Finger nicht-Thumb-Steuerelement zeigt.</span><span class="sxs-lookup"><span data-stu-id="2e715-192">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
    * <span data-ttu-id="2e715-193">Die **fassen Sie die Ausrichtung des einrichten Achse**: Die nach-oben-Achse impliziert durch die rechts- und -Weiterleiten-Definitionen.</span><span class="sxs-lookup"><span data-stu-id="2e715-193">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>
    * <span data-ttu-id="2e715-194">Sie können auf den Ziehpunkt Haltung über zugreifen [SpatialInteractionSourceState.Properties.TryGetLocation(...) ](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).</span><span class="sxs-lookup"><span data-stu-id="2e715-194">You can access the grip pose through [SpatialInteractionSourceState.Properties.TryGetLocation(...)](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).</span></span>
* <span data-ttu-id="2e715-195">Die **Zeiger Haltung**, das die Spitze des Controllers vorwärts zeigt darstellt.</span><span class="sxs-lookup"><span data-stu-id="2e715-195">The **pointer pose**, representing the tip of the controller pointing forward.</span></span>
    * <span data-ttu-id="2e715-196">Diese Haltung wird am besten verwendet, um Raycast beim **zeigen Sie auf der Benutzeroberfläche** Wenn Sie den Rendervorgang des Controllermodell selbst.</span><span class="sxs-lookup"><span data-stu-id="2e715-196">This pose is best used to raycast when **pointing at UI** when you are rendering the controller model itself.</span></span>
    * <span data-ttu-id="2e715-197">Sie können den Zeiger Haltung über zugreifen [SpatialInteractionSourceState.Properties.TryGetLocation(...). SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) oder [SpatialInteractionSourceState.TryGetPointerPose(...). TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).</span><span class="sxs-lookup"><span data-stu-id="2e715-197">You can access the pointer pose through [SpatialInteractionSourceState.Properties.TryGetLocation(...).SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) or [SpatialInteractionSourceState.TryGetPointerPose(...).TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).</span></span>

### <a name="composite-gestures-spatialgesturerecognizer"></a><span data-ttu-id="2e715-198">Zusammengesetzte Gesten: SpatialGestureRecognizer</span><span class="sxs-lookup"><span data-stu-id="2e715-198">Composite gestures: SpatialGestureRecognizer</span></span>

<span data-ttu-id="2e715-199">Ein [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) interpretiert Benutzerinteraktionen aus Hände Motion-Controller und der Sprach-Befehl "Select" auf der Entwurfsoberfläche räumliche Gestenereignisse, welchen Benutzern, die mit ihren Head Blicke.</span><span class="sxs-lookup"><span data-stu-id="2e715-199">A [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) interprets user interactions from hands, motion controllers, and the "Select" voice command to surface spatial gesture events, which users target using their head gaze.</span></span>

<span data-ttu-id="2e715-200">Räumliche Bewegungen sind eine wichtige Art der Eingabe für die Windows Mixed Reality-apps.</span><span class="sxs-lookup"><span data-stu-id="2e715-200">Spatial gestures are a key form of input for Windows Mixed Reality apps.</span></span> <span data-ttu-id="2e715-201">Durch routing Interaktionen über die SpatialInteractionManager, ggf. ein Hologramm SpatialGestureRecognizer können Ereignisse tippen, halten, Bearbeitung und Navigation gleichmäßig über praktische, Sprach- und räumliche Eingabegeräte, erkennen Sie apps, ohne drückt behandeln zu müssen und manuell frei.</span><span class="sxs-lookup"><span data-stu-id="2e715-201">By routing interactions from the SpatialInteractionManager to a hologram's SpatialGestureRecognizer, apps can detect Tap, Hold, Manipulation, and Navigation events uniformly across hands, voice, and spatial input devices, without having to handle presses and releases manually.</span></span>

<span data-ttu-id="2e715-202">SpatialGestureRecognizer führt nur die minimale Mehrdeutigkeit zwischen den Satz von Aktionen, die Sie anfordern.</span><span class="sxs-lookup"><span data-stu-id="2e715-202">SpatialGestureRecognizer performs only the minimal disambiguation between the set of gestures that you request.</span></span> <span data-ttu-id="2e715-203">Z. B., wenn Sie nur tippen anfordern, kann der Benutzer den Finger halten Sie solange wie sie und durch Tippen auf finden weiterhin statt.</span><span class="sxs-lookup"><span data-stu-id="2e715-203">For example, if you request just Tap, the user may hold their finger down as long as they like and a Tap will still occur.</span></span> <span data-ttu-id="2e715-204">Wenn Sie anfordern, tippen Sie auf und enthalten Sie, die nach einer Sekunde von der Sie ihren Finger gedrückt halten, die Bewegung zu stehen stuft, und durch Tippen auf nicht mehr ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="2e715-204">If you request both Tap and Hold, after about a second of holding down their finger, the gesture will promote to a Hold and a Tap will no longer occur.</span></span>

<span data-ttu-id="2e715-205">Um SpatialGestureRecognizer verwenden zu können, behandelt der SpatialInteractionManager des [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) Ereignis- und Ziehpunkte, die es auf die SpatialPointerPose verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="2e715-205">To use SpatialGestureRecognizer, handle the SpatialInteractionManager's [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) event and grab the SpatialPointerPose exposed there.</span></span> <span data-ttu-id="2e715-206">Verwenden für die Überschneidung mit den Hologramme des Benutzers Head Blicke Strahl von diesem Haltung und Oberfläche, die in der Umgebung des Benutzers, um zu bestimmen, was der Benutzer beabsichtigt ist, für die Interaktion mit Gitter.</span><span class="sxs-lookup"><span data-stu-id="2e715-206">Use the user's head gaze ray from this pose to intersect with the holograms and surface meshes in the user's surroundings, in order to determine what the user is intending to interact with.</span></span> <span data-ttu-id="2e715-207">Klicken Sie dann die SpatialInteraction weitergeleitet, in die Ereignisargumente, um das Ziel – Hologramm SpatialGestureRecognizer, mit dessen [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) Methode.</span><span class="sxs-lookup"><span data-stu-id="2e715-207">Then, route the SpatialInteraction in the event arguments to the target hologram's SpatialGestureRecognizer, using its [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) method.</span></span> <span data-ttu-id="2e715-208">Dies startet diese Interaktion nach Interpretation der [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) legen Sie für dieses Erkennungsmodul zum Zeitpunkt der Erstellung – oder durch [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).</span><span class="sxs-lookup"><span data-stu-id="2e715-208">This starts interpreting that interaction according to the [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) set on that recognizer at creation time - or by [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).</span></span>

<span data-ttu-id="2e715-209">Für HoloLens sollten Interaktionen und Gesten in der Regel ableiten, die für die Zielgruppenadressierung von Head Blicke des Benutzers, statt beim Rendern oder an die Hand, die Position direkt interagieren.</span><span class="sxs-lookup"><span data-stu-id="2e715-209">On HoloLens, interactions and gestures should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="2e715-210">Nachdem eine Aktivität gestartet wurde, können relative Bewegungen des Zeigers verwendet werden zur Steuerung der Bewegung wie bei der Manipulation oder die Bildschirmnavigation Bewegung.</span><span class="sxs-lookup"><span data-stu-id="2e715-210">Once an interaction has started, relative motions of the hand may be used to control the gesture, as with the Manipulation or Navigation gesture.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e715-211">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2e715-211">See also</span></span>
* [<span data-ttu-id="2e715-212">Blicke</span><span class="sxs-lookup"><span data-stu-id="2e715-212">Gaze</span></span>](gaze.md)
* [<span data-ttu-id="2e715-213">Gesten</span><span class="sxs-lookup"><span data-stu-id="2e715-213">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="2e715-214">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="2e715-214">Motion controllers</span></span>](motion-controllers.md)
