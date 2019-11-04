---
title: Tastatureingabe in Unity
description: Unity stellt die touchscreenkeyboard-Klasse bereit, um Tastatureingaben zu akzeptieren, wenn keine physische Tastatur verfügbar ist.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Tastatur, Eingabe, Unity, touchscreenkeyboard
ms.openlocfilehash: f506415f9658d9723bf31b339d63fe4569100ace
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438561"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="c61f3-104">Tastatureingabe in Unity</span><span class="sxs-lookup"><span data-stu-id="c61f3-104">Keyboard input in Unity</span></span>

<span data-ttu-id="c61f3-105">**Namespace:** *unityengine*</span><span class="sxs-lookup"><span data-stu-id="c61f3-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="c61f3-106">**Typ**:  *[touchscreenkeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="c61f3-106">**Type**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="c61f3-107">Obwohl hololens viele Formen von Eingaben einschließlich Bluetooth-Tastaturen unterstützt, können die meisten Anwendungen nicht davon ausgehen, dass für alle Benutzer eine physische Tastatur verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="c61f3-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications cannot assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="c61f3-108">Wenn für Ihre Anwendung Texteingaben erforderlich sind, sollte eine Form von auf Bildschirmtastatur angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="c61f3-108">If your application requires text input, some form of on screen keyboard should be provided.</span></span>

<span data-ttu-id="c61f3-109">Unity stellt die *[touchscreenkeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* -Klasse bereit, um Tastatureingaben zu akzeptieren, wenn keine physische Tastatur verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="c61f3-109">Unity provides the *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there is no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="c61f3-110">Hololens System Tastatur Verhalten in Unity</span><span class="sxs-lookup"><span data-stu-id="c61f3-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="c61f3-111">Auf hololens nutzt *touchscreenkeyboard* die Bildschirmtastatur des Systems.</span><span class="sxs-lookup"><span data-stu-id="c61f3-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on screen keyboard.</span></span> <span data-ttu-id="c61f3-112">Die Tastatur des Systems auf dem Bildschirm kann nicht oberhalb einer Volumetrische-Ansicht überlagert werden, sodass Unity eine sekundäre 2D-XAML-Ansicht erstellen muss, um die Tastatur anzuzeigen, und dann zurück an die volumetriansicht zurückgegeben wird, sobald die Eingabe übermittelt wurde.</span><span class="sxs-lookup"><span data-stu-id="c61f3-112">The system's on screen keyboard is unable to overlay on top of a volumetric view so Unity has to create a secondary 2D XAML view to show the keyboard then return back to the volumetric view once input has been submitted.</span></span> <span data-ttu-id="c61f3-113">Der Benutzer Ablauf sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="c61f3-113">The user flow goes like this:</span></span>
1. <span data-ttu-id="c61f3-114">Der Benutzer führt eine Aktion aus, die bewirkt, dass APP-Code *touchscreenkeyboard* aufruft.</span><span class="sxs-lookup"><span data-stu-id="c61f3-114">The user performs an action causing app code to call *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="c61f3-115">Die APP ist für das Anhalten des App-Zustands vor dem Aufrufen von *touchscreenkeyboard* verantwortlich.</span><span class="sxs-lookup"><span data-stu-id="c61f3-115">The app is responsible for pausing app state before calling *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="c61f3-116">Die APP kann beendet werden, bevor Sie zur Volumetrische-Ansicht zurück wechselt.</span><span class="sxs-lookup"><span data-stu-id="c61f3-116">The app may terminate before ever switching back to the volumetric view</span></span>
2. <span data-ttu-id="c61f3-117">Unity wechselt zu einer 2D-XAML-Ansicht, die automatisch in der Welt platziert wird</span><span class="sxs-lookup"><span data-stu-id="c61f3-117">Unity switches to a 2D XAML view which is auto-placed in the world</span></span>
3. <span data-ttu-id="c61f3-118">Der Benutzer gibt mithilfe der System Tastatur Text ein und übermittelt oder bricht ihn ab.</span><span class="sxs-lookup"><span data-stu-id="c61f3-118">The user enters text using the system keyboard and submits or cancels</span></span>
4. <span data-ttu-id="c61f3-119">Unity wechselt zurück zur volumetriansicht</span><span class="sxs-lookup"><span data-stu-id="c61f3-119">Unity switches back to the volumetric view</span></span>
    * <span data-ttu-id="c61f3-120">Die APP ist für das Fortsetzen des App-Zustands verantwortlich, wenn *touchscreenkeyboard* abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="c61f3-120">The app is responsible for resuming app state when the *TouchScreenKeyboard* is done</span></span>
5. <span data-ttu-id="c61f3-121">Der übermittelte Text ist in *touchscreenkeyboard* verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c61f3-121">Submitted text is available in the *TouchScreenKeyboard*</span></span>

### <a name="available-keyboard-views"></a><span data-ttu-id="c61f3-122">Verfügbare Tastatur Ansichten</span><span class="sxs-lookup"><span data-stu-id="c61f3-122">Available keyboard views</span></span>

<span data-ttu-id="c61f3-123">Es stehen sechs verschiedene Tastatur Ansichten zur Verfügung:</span><span class="sxs-lookup"><span data-stu-id="c61f3-123">There are six different keyboard views available:</span></span>
* <span data-ttu-id="c61f3-124">Einzeilige Textfeld</span><span class="sxs-lookup"><span data-stu-id="c61f3-124">Single-line textbox</span></span>
* <span data-ttu-id="c61f3-125">Einzeilige Textfeld mit Titel</span><span class="sxs-lookup"><span data-stu-id="c61f3-125">Single-line textbox with title</span></span>
* <span data-ttu-id="c61f3-126">Mehrzeilige Textfeld</span><span class="sxs-lookup"><span data-stu-id="c61f3-126">Multi-line textbox</span></span>
* <span data-ttu-id="c61f3-127">Mehrzeilige Textfeld mit Titel</span><span class="sxs-lookup"><span data-stu-id="c61f3-127">Multi-line textbox with title</span></span>
* <span data-ttu-id="c61f3-128">Einzeilige Kenn Wort Feld</span><span class="sxs-lookup"><span data-stu-id="c61f3-128">Single-line password box</span></span>
* <span data-ttu-id="c61f3-129">Einzeilige Kenn Wort Feld mit Titel</span><span class="sxs-lookup"><span data-stu-id="c61f3-129">Single-line password box with title</span></span>

## <a name="how-to-enable-the-system-keyboard-in-unity"></a><span data-ttu-id="c61f3-130">Aktivieren der System Tastatur in Unity</span><span class="sxs-lookup"><span data-stu-id="c61f3-130">How to enable the system keyboard in Unity</span></span>

<span data-ttu-id="c61f3-131">Die System Tastatur hololens ist nur für Unity-Anwendungen verfügbar, die mit dem "UWP Build Type" auf "XAML" exportiert werden.</span><span class="sxs-lookup"><span data-stu-id="c61f3-131">The HoloLens system keyboard is only available to Unity applications that are exported with the "UWP Build Type" set to "XAML".</span></span> <span data-ttu-id="c61f3-132">Wenn Sie "XAML" als "UWP Build Type" über "D3D" auswählen, müssen Sie die vor-und Nachteile treffen.</span><span class="sxs-lookup"><span data-stu-id="c61f3-132">There are tradeoffs you make when you choose "XAML" as the "UWP Build Type" over "D3D".</span></span> <span data-ttu-id="c61f3-133">Wenn Sie mit diesen vor-und Nachteile nicht vertraut sind, möchten Sie möglicherweise eine [Alternative Eingabe Lösung](#alternative-keyboard-options) für die System Tastatur untersuchen.</span><span class="sxs-lookup"><span data-stu-id="c61f3-133">If you aren't comfortable with those tradeoffs, you may wish to explore an [alternative input solution](#alternative-keyboard-options) to the system keyboard.</span></span>
1. <span data-ttu-id="c61f3-134">Öffnen Sie das Menü **Datei** , und wählen Sie Buildeinstellungen aus **.**</span><span class="sxs-lookup"><span data-stu-id="c61f3-134">Open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="c61f3-135">Stellen Sie sicher, dass die **Plattform** auf **Windows Store**festgelegt ist, das **SDK** auf **Universal 10**festgelegt ist, und legen Sie den **UWP-Buildtyp** auf **XAML**fest.</span><span class="sxs-lookup"><span data-stu-id="c61f3-135">Ensure the **Platform** is set to **Windows Store**, the **SDK** is set to **Universal 10**, and set the **UWP Build Type** to **XAML**.</span></span>
3. <span data-ttu-id="c61f3-136">Klicken Sie im Dialogfeld " **Buildeinstellungen** " auf die Schaltfläche **Player Einstellungen...** .</span><span class="sxs-lookup"><span data-stu-id="c61f3-136">In the **Build Settings** dialog, click the **Player Settings...** button</span></span>
4. <span data-ttu-id="c61f3-137">Wählen Sie die Registerkarte **Einstellungen für Windows Store aus** .</span><span class="sxs-lookup"><span data-stu-id="c61f3-137">Select the **Settings for Windows Store** tab</span></span>
5. <span data-ttu-id="c61f3-138">Erweitern Sie die Gruppe **andere Einstellungen** .</span><span class="sxs-lookup"><span data-stu-id="c61f3-138">Expand the **Other Settings** group</span></span>
6. <span data-ttu-id="c61f3-139">Aktivieren Sie im Abschnitt " **Rendering** " das Kontrollkästchen " **Virtual Reality supported** ", um eine neue **Virtual Reality-Geräte** Liste hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="c61f3-139">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list</span></span>
7. <span data-ttu-id="c61f3-140">Stellen Sie sicher, dass **Windows Holographic** in der Liste der Virtual Reality sdert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c61f3-140">Ensure **Windows Holographic** appears in the list of Virtual Reality SDKs</span></span>

>[!NOTE]
><span data-ttu-id="c61f3-141">Wenn Sie den Build nicht als virtuelle Realität markieren, die mit dem hololens-Gerät unterstützt wird, exportiert das Projekt als 2D-XAML-app.</span><span class="sxs-lookup"><span data-stu-id="c61f3-141">If you don't mark the build as Virtual Reality Supported with the HoloLens device, the project will export as a 2D XAML app.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="c61f3-142">Verwenden der System Tastatur in ihrer Unity-App</span><span class="sxs-lookup"><span data-stu-id="c61f3-142">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="c61f3-143">Tastatur deklarieren</span><span class="sxs-lookup"><span data-stu-id="c61f3-143">Declare the keyboard</span></span>

<span data-ttu-id="c61f3-144">Deklarieren Sie in der-Klasse eine Variable zum Speichern der *touchscreenkeyboard* und eine Variable, um die von der Tastatur zurückgegebene Zeichenfolge zu speichern.</span><span class="sxs-lookup"><span data-stu-id="c61f3-144">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="c61f3-145">Tastatur aufrufen</span><span class="sxs-lookup"><span data-stu-id="c61f3-145">Invoke the keyboard</span></span>

<span data-ttu-id="c61f3-146">Wenn ein Ereignis beim Anfordern von Tastatureingaben auftritt, wird eine dieser Funktionen aufgerufen, abhängig vom Typ der gewünschten Eingabe.</span><span class="sxs-lookup"><span data-stu-id="c61f3-146">When an event occurs requesting keyboard input, call one of these functions depending upon the type of input desired.</span></span> <span data-ttu-id="c61f3-147">Beachten Sie, dass der Titel im textplachalter-Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="c61f3-147">Note that the title is specified in the textPlaceholder parameter.</span></span>

```cs
// Single-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);

// Single-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false, "Single-line title");

// Multi-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false);

// Multi-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false, "Multi-line Title");

// Single-line password box
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false);

// Single-line password box with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false, "Secure Single-line Title");
```

### <a name="retrieve-typed-contents"></a><span data-ttu-id="c61f3-148">Abrufen von typisiertem Inhalt</span><span class="sxs-lookup"><span data-stu-id="c61f3-148">Retrieve typed contents</span></span>

<span data-ttu-id="c61f3-149">Überprüfen Sie in der Update Schleife, ob die Tastatur neue Eingaben empfangen hat, und speichern Sie Sie an anderer Stelle.</span><span class="sxs-lookup"><span data-stu-id="c61f3-149">In the update loop, check if the keyboard received new input and store it for use elsewhere.</span></span>

```cs
if (TouchScreenKeyboard.visible == false && keyboard != null)
{
       if (keyboard.done == true)
       {
           keyboardText = keyboard.text;
           keyboard = null;
       }
}
```

## <a name="alternative-keyboard-options"></a><span data-ttu-id="c61f3-150">Alternative Tastatur Optionen</span><span class="sxs-lookup"><span data-stu-id="c61f3-150">Alternative keyboard options</span></span>

<span data-ttu-id="c61f3-151">Wir wissen, dass das Wechseln aus einer Volumetrische-Sicht in eine 2D-Ansicht nicht die ideale Methode ist, um Texteingaben vom Benutzer zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="c61f3-151">We understand that switching out of a volumetric view into a 2D view isn't the ideal way to get text input from the user.</span></span>

<span data-ttu-id="c61f3-152">Die aktuellen Alternativen zur Verwendung der System Tastatur über Unity umfassen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="c61f3-152">The current alternatives to leveraging the system keyboard through Unity include:</span></span>
* <span data-ttu-id="c61f3-153">Verwendung der Spracherkennung für die Eingabe (<b>Hinweis:</b> Dies ist oft fehleranfällig für Wörter, die nicht im Wörterbuch gefunden wurden und für die Kenn Wort Eingabe nicht geeignet sind).</span><span class="sxs-lookup"><span data-stu-id="c61f3-153">Using speech dictation for input (<b>Note:</b> this is often error prone for words not found in the dictionary and is not suitable for password entry)</span></span>
* <span data-ttu-id="c61f3-154">Erstellen einer Tastatur, die in der exklusiven Ansicht Ihrer Anwendungen funktioniert</span><span class="sxs-lookup"><span data-stu-id="c61f3-154">Create a keyboard that works in your applications exclusive view</span></span>
