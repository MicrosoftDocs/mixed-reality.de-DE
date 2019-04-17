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
# <a name="gaze-gestures-and-motion-controllers-in-directx"></a>Blicke, Gesten und während der Übertragung von Controllern in DirectX

Wenn Sie vorhaben, um direkt auf der Plattform zu erstellen, müssen vom Benutzer – z. B., in denen der Benutzer über sucht eine Eingabe kommen behandeln [Head Blicke](gaze.md) und was der Benutzer ausgewählt hat, mit [Gesten](gestures.md) oder [motion Controller](motion-controllers.md). Kombinieren diese Formen der Eingabe, können Sie einem Benutzer platzieren ermöglichen eine [– Hologramm](hologram.md) in Ihrer app. Die [holographic app-Vorlage](creating-a-holographic-directx-project.md) enthält ein Beispiel einfach zu verwenden.

>[!NOTE]
>Die Codeausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstatt C ++ 17-kompatible C++"/ WinRT", wie in der [ C++ holographic Projektvorlage](creating-a-holographic-directx-project.md).  Die Konzepte sind Entsprechung für einen C++"/ WinRT"-Projekt, aber Sie benötigen, um den Code zu übersetzen.

## <a name="gaze-input"></a>Eingabe via Anvisieren

Des Benutzers den Zugriff auf [Head Blicke](gaze.md), Sie verwenden die [SpatialPointerPose](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialpointerpose.aspx) Typ. Die holographic app-Vorlage enthält die grundlegenden Code für das Verständnis Blicke. Dieser Code stellt einen Vektor zeigt Weiterleiten von einschließlich Augen des Benutzers unter Berücksichtigung des Geräts-Position und Ausrichtung in einem bestimmten [Koordinatensystem](coordinate-systems-in-directx.md).




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

Sie können sich z.B. finden: "Aber woher das Koordinatensystem stammen aus?"

Lassen Sie uns diese Frage zu beantworten. In unserem AppMain des **Update** -Funktion verarbeitet eine räumliche Eingabeereignis durch diese relativ zu das Koordinatensystem für unsere StationaryFrameOfReference anfordern. Denken Sie daran, dass die StationaryFrameOfReference erstellt wurde, wenn wir richten die [HolographicSpace](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx), und das Koordinatensystem abgerufen wurde, am Anfang des [Update](rendering-in-directx.md).




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

Beachten Sie, dass die Daten in einen Zeiger-Zustand, der eine Art gebunden ist. Wir erhalten diese aus dem eine räumliche Eingabeereignis. Das Ereignisobjekt für die Daten enthält einem Koordinatensystem, sodass Sie immer die Blicke Richtung zum Zeitpunkt des Ereignisses auf den spatial Koordinatensystem beziehen können, die Sie benötigen. In der Tat müssen Sie dies tun, um den Zeiger Haltung zu erhalten.

> [!NOTE]
> Weitere Anleitungen, die speziell für HoloLens 2 [bald](index.md#news-and-notes).

## <a name="gesture-and-motion-controller-input"></a>Gesten und während der Übertragung Controller Eingabe

In Windows Mixed Reality, beide übergeben [Gesten](gestures.md) und [motion Controller](motion-controllers.md) erfolgt über die gleichen räumliche Eingabe-APIs finden Sie in der [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) Namespace. Dadurch können Sie Baseler Ausschusses für häufig verwendete Aktionen wie **wählen** drückt die gleiche Weise wie für praktische und Motion-Controller.

Es gibt zwei Ebenen der API, die Sie abzielen können, bei der Verarbeitung von Gesten oder Motion-Controllern in mixed Reality:
* [Interaktionen](gestures.md#the-two-core-gestures-of-hololens) ([SourcePressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed.aspx), [SourceReleased](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased.aspx) und [SourceUpdated](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated.aspx)), der Zugriff mithilfe einer [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx)
* [Zusammengesetzte Gesten](gestures.md#composite-gestures) ([Tapped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.tapped.aspx), enthalten, Manipulation, Navigation), der Zugriff mithilfe einer [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)

### <a name="selectmenugrasptouchpadthumbstick-interactions-spatialinteractionmanager"></a>Wählen Sie/Menü/verstehen/Touchpad/Ministick Interaktionen: SpatialInteractionManager

Zum Erkennen von Low-Level drückt, Releases und Updates für praktische und Eingabegeräte in Windows Mixed Reality starten Sie über eine [SpatialInteractionManager](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionmanager.aspx). Die SpatialInteractionManager hat ein Ereignis, das Sie informiert die app nach einer Hand oder Motion-Controller verfügt über Eingabe erkannt wird.

Es gibt drei wichtige Arten von SpatialInteractionSource, die durch einen anderen Wert für die SpatialInteractionSourceKind dargestellt:
* **Hand** erkannte Hand eines Benutzers darstellt. Hand-Datenquellen stehen nur für HoloLens.
* **Controller** einen gekoppelten Motion-Controller darstellt. Während der Übertragung Controller bieten eine Vielzahl von Funktionen, z.B.: Wählen Sie die Trigger, Menüschaltflächen, verstehen Schaltflächen, Touchpad und Thumbsticks.
* **Voice** des Benutzers Voice Schlüsselwörter System hat Vorträge darstellt. Das Drücken einer Option Einfügen wird und freizugeben, wenn der Benutzer sagt "Select".

Um drückt auf allen der folgenden Quellen Interaktion zu erkennen, können Sie das Ereignis SourcePressed auf SpatialInteractionManager in SpatialInputHandler.cpp behandeln:


```cpp
m_interactionManager = SpatialInteractionManager::GetForCurrentView();
    
// Bind a handler to the SourcePressed event.
m_sourcePressedEventToken =
    m_interactionManager->SourcePressed +=
        ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
            bind(&SpatialInputHandler::OnSourcePressed, this, _1, _2)
            );
```

Dieses Ereignis gedrückte wird asynchron zu Ihrer app gesendet. Ihre app oder eine Spiele-Engine möglicherweise ausführen möchten sofort verarbeiten oder möglicherweise möchten die Daten in der Eingabe verarbeiten Routine in die Warteschlange.

Die Vorlage enthält eine Hilfsklasse, um Ihnen den Einstieg erleichtern. Diese Vorlage forgoes Verarbeitungsschritte aus Gründen der Einfachheit des Entwurfs. Die Hilfsklasse behält den Überblick, ob ein oder mehrere **Pressed** Ereignisse aufgetreten sind, seit der letzten **Update** aufrufen. Von SpatialInputHandler.cpp:




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

Wenn also es gibt die [SpatialInteractionSourceState](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) für die letzten Eingabeereignis während des nächsten Updates. Von SpatialInputHandler.cpp:




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

Beachten Sie, dass der obige Code alle behandelt drückt die gleiche Weise, ob der Benutzer einen primären ausführt **wählen** drücken oder ein sekundäres Replikat **im Menü** oder **verstehen** drücken. Die **wählen** Press ist eine primäre Form der Interaktion über praktische, Controller oder Stimme, die ausgelöst werden, entweder durch ein manuelles eine tippbewegung ausführen, auf ein Controller während der Übertragung mit der primären Trigger/Schaltfläche gedrückt, während der Übertragung oder des Benutzers unterstützt Voice-sagen "Select". Drückt die Option darstellen des Benutzers Absicht an, die – Hologramm aktiviert werden, die sie verwenden möchten.

Welche Art von Press verständlich auftritt, ändern wir den SpatialInteractionManager::SourceUpdated-Ereignishandler. Unser Code verstehen drückt erkennt, (sofern verfügbar) und diese verwenden, um den Cube neu zu positionieren. Wenn Sie verstehen, nicht verfügbar ist, verwenden wir wählen drückt stattdessen.

Fügen Sie die folgenden privaten Member-Deklarationen zu SpatialInputHandler.h: 


```cpp
void OnSourceUpdated(
       Windows::UI::Input::Spatial::SpatialInteractionManager^ sender,
       Windows::UI::Input::Spatial::SpatialInteractionSourceEventArgs^ args);
   Windows::Foundation::EventRegistrationToken m_sourceUpdatedEventToken;
```

Open SpatialInputHandler.cpp. Fügen Sie die folgenden ereignisregistrierung an den Konstruktor hinzu: 


```cpp
m_sourceUpdatedEventToken =
       m_interactionManager->SourceUpdated +=
       ref new TypedEventHandler<SpatialInteractionManager^, SpatialInteractionSourceEventArgs^>(
           bind(&SpatialInputHandler::OnSourceUpdated, this, _1, _2)
           );
```

Dies ist der Code des ereignishandlers. Wenn die Eingabequelle verstanden hat, wird der Zeiger Haltung für von der Aktualisierungsschleife des nächsten gespeichert werden. Andernfalls wird für eine Option, drücken Sie stattdessen überprüft. Von SpatialInputHandler.cpp:




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

Stellen Sie sicher, dass den Ereignishandler im Destruktor aufgehoben werden. Von SpatialInputHandler.cpp:


```cpp
m_interactionManager->SourceUpdated -= m_sourcePressedEventToken;
```

Kompilieren Sie erneut, und klicken Sie dann erneut bereitstellen. Ihr Vorlagenprojekt sollte jetzt verstehen von Interaktionen an Position sich drehenden Würfels erkennen zu können.

Die SpatialInteractionSource-API unterstützt die Controller, mit einer Vielzahl von Funktionen. Im oben gezeigten Beispiel überprüfen wir ermitteln, ob verstehen unterstützt wird, bevor Sie versuchen, die sie verwenden. Die SpatialInteractionSource unterstützt die folgenden optionalen Funktionen über die allgemeinen **wählen** drücken:
* **Schaltfläche:** Überprüfen Sie durch Überprüfen der IsMenuSupported-Eigenschaft unterstützen. Wenn unterstützt, überprüfen Sie die [SpatialInteractionSourceState::IsMenuPressed](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) Eigenschaft, um zu ermitteln, ob die Menüschaltfläche gedrückt wird.
* **Verstehen Sie die Schaltfläche:** Überprüfen Sie durch Überprüfen der IsGraspSupported-Eigenschaft unterstützen. Wenn unterstützt, überprüfen Sie die [SpatialInteractionSourceState::IsGrasped](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialinteractionsourcestate.aspx) Eigenschaft, um herauszufinden, ob verstehen aktiviert ist.

Für Controller verwendet hat die SpatialInteractionSource eine Controller-Eigenschaft, mit zusätzlichen Funktionen.
* **HasThumbstick:** Bei "true", hat der Controller eine Ministick an. Überprüfen Sie die [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) Eigenschaft der SpatialInteractionSourceState Ministick abrufen x und y-Werte (ThumbstickX und ThumbstickY) sowie ihren aktuellen Status (IsThumbstickPressed).
* **HasTouchpad:** Bei "true", hat der Controller Touchpads an. Überprüfen Sie die ControllerProperties-Eigenschaft, der die SpatialInteractionSourceState zum Abrufen der Touchpad x- und y Werte (TouchpadX und TouchpadY), und wissen, ob der Benutzer das Pad "" (IsTouchpadTouched) berührt, und wenn sie das Touchpad nach unten (drücken, werden IsTouchpadPressed).
* **SimpleHapticsController:** Die SimpleHapticsController-API für den Controller können Sie die Funktionen Haptics des Controllers zu überprüfen, und sie können außerdem zum Übermitteln von haptischem Feedback zu steuern.

Beachten Sie, dass der Bereich für Touchpad und Ministick von – 1, 1 für beide Achsen (von unten nach oben und von links nach rechts). Der Bereich für den analogen Trigger, die mithilfe der SpatialInteractionSourceState::SelectPressedValue-Eigenschaft zugegriffen wird, hat es sich um einen Bereich von 0 bis 1. Ein Wert von 1 korreliert mit IsSelectPressed ist gleich "true". Jeder andere Wert korreliert mit IsSelectPressed ist gleich "false".

Beachten Sie, dass für eine Hand und ein Controller, mit SpatialInteractionSourceState::Properties::TryGetLocation Hand-Position des Benutzers erhalten – Dies unterscheidet sich von den Zeiger darstellen des Controllers zeigen Chow darstellt. Wenn Sie etwa an der Hand Position zeichnen möchten, verwenden Sie TryGetLocation. Wenn Sie von der Spitze des Controllers Raycast möchten, rufen Sie zeigen Strahl aus TryGetInteractionSourcePose auf die SpatialPointerPose aus.

Sie können auch die anderen Ereignisse auf SpatialInteractionManager, z. B. SourceDetected und SourceLost, zu reagieren, wenn die Hände einzugeben oder zu verlassen, anzeigen oder wenn sie für oder gegen die bereit Position (Index Finger ausgelöst mit Palm weiterleiten) Verschieben des Geräts, oder wenn motion Controller sind die ein-und aktiviert wird oder werden zugeordnet/Ungepaarte.

### <a name="grip-pose-vs-pointing-pose"></a>Ziehpunkt Haltung im Vergleich zu zeigenden Haltung

Windows Mixed Reality unterstützt Controller, die während der Übertragung in einer Vielzahl von Formfaktoren, des Controllers Entwurf unterscheidet sich in der Beziehung zwischen Hand-Position des Benutzers und der natürliche "Weiterleiten" Richtung dieser apps sollten mit auf beim Rendern der Controller.

Um diese Controller besser darstellen zu können, gibt es zwei Arten von ist, die Sie für jede Quelle Interaktion untersuchen können:
* Die **Ziehpunkt Haltung**, den Speicherort der dies im Handumdrehen einer Hand, die von einem HoloLens erkannt werden, oder dies mit einem Controller während der Übertragung im Handumdrehen darstellt.
    * Für immersive Headsets, diese Haltung wird am besten zum Rendern **des Benutzers manuell** oder **frei, die ein Objekt des Benutzers verfügen**, z. B. eine "sword" oder dem damoklesschwert.
    * Die **fassen Sie Position**: Der Schwerpunkt Palm, wenn der Controller natürlich mit angepasst nach links oder rechts zentriert die Position in den Ziehpunkt.
    * Die **fassen Sie die rechte Achse die Ausrichtung**: Wenn Sie Ihre Hand, um einen flachen 5 Finger Haltung bilden vollständig geöffnet haben, dem Strahl, der ist normal, zu Ihrem Palm (vorwärts vom linken Palm, rückwärts von rechts Palm)
    * Die **fassen Sie die Ausrichtung, vorwärts gerichtete Achse**: Wenn Sie Ihre Hand schließen, teilweise (als ob den Controller enthält), der vom Strahl, der "forward" über die Tube gebildet, indem die Finger nicht-Thumb-Steuerelement zeigt.
    * Die **fassen Sie die Ausrichtung des einrichten Achse**: Die nach-oben-Achse impliziert durch die rechts- und -Weiterleiten-Definitionen.
    * Sie können auf den Ziehpunkt Haltung über zugreifen [SpatialInteractionSourceState.Properties.TryGetLocation(...) ](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).
* Die **Zeiger Haltung**, das die Spitze des Controllers vorwärts zeigt darstellt.
    * Diese Haltung wird am besten verwendet, um Raycast beim **zeigen Sie auf der Benutzeroberfläche** Wenn Sie den Rendervorgang des Controllermodell selbst.
    * Sie können den Zeiger Haltung über zugreifen [SpatialInteractionSourceState.Properties.TryGetLocation(...). SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) oder [SpatialInteractionSourceState.TryGetPointerPose(...). TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).

### <a name="composite-gestures-spatialgesturerecognizer"></a>Zusammengesetzte Gesten: SpatialGestureRecognizer

Ein [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) interpretiert Benutzerinteraktionen aus Hände Motion-Controller und der Sprach-Befehl "Select" auf der Entwurfsoberfläche räumliche Gestenereignisse, welchen Benutzern, die mit ihren Head Blicke.

Räumliche Bewegungen sind eine wichtige Art der Eingabe für die Windows Mixed Reality-apps. Durch routing Interaktionen über die SpatialInteractionManager, ggf. ein Hologramm SpatialGestureRecognizer können Ereignisse tippen, halten, Bearbeitung und Navigation gleichmäßig über praktische, Sprach- und räumliche Eingabegeräte, erkennen Sie apps, ohne drückt behandeln zu müssen und manuell frei.

SpatialGestureRecognizer führt nur die minimale Mehrdeutigkeit zwischen den Satz von Aktionen, die Sie anfordern. Z. B., wenn Sie nur tippen anfordern, kann der Benutzer den Finger halten Sie solange wie sie und durch Tippen auf finden weiterhin statt. Wenn Sie anfordern, tippen Sie auf und enthalten Sie, die nach einer Sekunde von der Sie ihren Finger gedrückt halten, die Bewegung zu stehen stuft, und durch Tippen auf nicht mehr ausgeführt wird.

Um SpatialGestureRecognizer verwenden zu können, behandelt der SpatialInteractionManager des [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) Ereignis- und Ziehpunkte, die es auf die SpatialPointerPose verfügbar gemacht. Verwenden für die Überschneidung mit den Hologramme des Benutzers Head Blicke Strahl von diesem Haltung und Oberfläche, die in der Umgebung des Benutzers, um zu bestimmen, was der Benutzer beabsichtigt ist, für die Interaktion mit Gitter. Klicken Sie dann die SpatialInteraction weitergeleitet, in die Ereignisargumente, um das Ziel – Hologramm SpatialGestureRecognizer, mit dessen [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) Methode. Dies startet diese Interaktion nach Interpretation der [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) legen Sie für dieses Erkennungsmodul zum Zeitpunkt der Erstellung – oder durch [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).

Für HoloLens sollten Interaktionen und Gesten in der Regel ableiten, die für die Zielgruppenadressierung von Head Blicke des Benutzers, statt beim Rendern oder an die Hand, die Position direkt interagieren. Nachdem eine Aktivität gestartet wurde, können relative Bewegungen des Zeigers verwendet werden zur Steuerung der Bewegung wie bei der Manipulation oder die Bildschirmnavigation Bewegung.

## <a name="see-also"></a>Siehe auch
* [Blicke](gaze.md)
* [Gesten](gestures.md)
* [Motion-Controller](motion-controllers.md)
