---
title: Tastatureingaben in Unity
description: Unity bietet die Klasse TouchScreenKeyboard Tastatureingaben akzeptieren, wenn keine physische Tastatur verfügbar ist.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Tastatur, Eingabe, Unity, touchscreenkeyboard
ms.openlocfilehash: 35f6f0df993931eea35db7b167110b341ea0c0f2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604885"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="73259-104">Tastatureingaben in Unity</span><span class="sxs-lookup"><span data-stu-id="73259-104">Keyboard input in Unity</span></span>

<span data-ttu-id="73259-105">**Namespace:** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="73259-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="73259-106">**Typ**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="73259-106">**Type**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="73259-107">HoloLens viele Formen der Eingabe, einschließlich Bluetooth-Tastaturen unterstützt, wird die meisten Anwendungen können nicht davon ausgegangen, dass alle Benutzer eine physische Tastatur, die zur Verfügung hat.</span><span class="sxs-lookup"><span data-stu-id="73259-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications cannot assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="73259-108">Wenn Ihre Anwendung die Texteingabe erforderlich ist, muss eine Form der Bildschirmtastatur bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="73259-108">If your application requires text input, some form of on screen keyboard should be provided.</span></span>

<span data-ttu-id="73259-109">Unity bietet die *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* -Klasse für Tastatureingaben akzeptiert, wenn keine physische Tastatur verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="73259-109">Unity provides the *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there is no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="73259-110">HoloLens-System-Tastaturverhalten in Unity</span><span class="sxs-lookup"><span data-stu-id="73259-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="73259-111">Für HoloLens die *TouchScreenKeyboard* nutzt die Bildschirmtastatur des Systems.</span><span class="sxs-lookup"><span data-stu-id="73259-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on screen keyboard.</span></span> <span data-ttu-id="73259-112">Die Bildschirmtastatur des Systems kann nicht auf eine volumetrische Ansicht zu überlagern, weshalb Unity erstellen eine sekundäre 2D XAML-Ansicht zum Anzeigen der Tastatur, und klicken Sie dann an die volumetrische Sicht zurückgegeben wird, nach der Eingabe übermittelt wurde.</span><span class="sxs-lookup"><span data-stu-id="73259-112">The system's on screen keyboard is unable to overlay on top of a volumetric view so Unity has to create a secondary 2D XAML view to show the keyboard then return back to the volumetric view once input has been submitted.</span></span> <span data-ttu-id="73259-113">Der benutzerflow läuft folgendermaßen ab:</span><span class="sxs-lookup"><span data-stu-id="73259-113">The user flow goes like this:</span></span>
1. <span data-ttu-id="73259-114">Der Benutzer führt eine Aktion, die app-Code aufrufen, wodurch *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="73259-114">The user performs an action causing app code to call *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="73259-115">Die app ist verantwortlich für das Anhalten des app-Status vor dem Aufruf *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="73259-115">The app is responsible for pausing app state before calling *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="73259-116">Die app möglicherweise beenden, bevor Sie jemals wieder an die volumetrische Ansicht wechseln</span><span class="sxs-lookup"><span data-stu-id="73259-116">The app may terminate before ever switching back to the volumetric view</span></span>
2. <span data-ttu-id="73259-117">Unity wechselt zu einer XAML-2D-Ansicht automatisch platzierte in der der ganzen Welt</span><span class="sxs-lookup"><span data-stu-id="73259-117">Unity switches to a 2D XAML view which is auto-placed in the world</span></span>
3. <span data-ttu-id="73259-118">Der Benutzer Text mithilfe der Systemtastatur eingegeben und übermittelt oder abgebrochen</span><span class="sxs-lookup"><span data-stu-id="73259-118">The user enters text using the system keyboard and submits or cancels</span></span>
4. <span data-ttu-id="73259-119">Unity, wechselt zurück in die volumetrische Ansicht</span><span class="sxs-lookup"><span data-stu-id="73259-119">Unity switches back to the volumetric view</span></span>
    * <span data-ttu-id="73259-120">Die app ist verantwortlich für das Fortsetzen der app Zustand über, wenn die *TouchScreenKeyboard* erfolgt</span><span class="sxs-lookup"><span data-stu-id="73259-120">The app is responsible for resuming app state when the *TouchScreenKeyboard* is done</span></span>
5. <span data-ttu-id="73259-121">Gesendeten Text finden Sie in der *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="73259-121">Submitted text is available in the *TouchScreenKeyboard*</span></span>

### <a name="available-keyboard-views"></a><span data-ttu-id="73259-122">Verfügbare Tastatur-Ansichten</span><span class="sxs-lookup"><span data-stu-id="73259-122">Available keyboard views</span></span>

<span data-ttu-id="73259-123">Es gibt sechs verschiedene Tastatur Ansichten verfügbar:</span><span class="sxs-lookup"><span data-stu-id="73259-123">There are six different keyboard views available:</span></span>
* <span data-ttu-id="73259-124">Einzeiliges Textfeld</span><span class="sxs-lookup"><span data-stu-id="73259-124">Single-line textbox</span></span>
* <span data-ttu-id="73259-125">Einzeiliges Textfeld mit dem Titel</span><span class="sxs-lookup"><span data-stu-id="73259-125">Single-line textbox with title</span></span>
* <span data-ttu-id="73259-126">Mehrzeiligen Textfeld</span><span class="sxs-lookup"><span data-stu-id="73259-126">Multi-line textbox</span></span>
* <span data-ttu-id="73259-127">Mehrzeiligen Textfeld mit dem Titel</span><span class="sxs-lookup"><span data-stu-id="73259-127">Multi-line textbox with title</span></span>
* <span data-ttu-id="73259-128">Einzeilige Kennwortfeld</span><span class="sxs-lookup"><span data-stu-id="73259-128">Single-line password box</span></span>
* <span data-ttu-id="73259-129">Einzeilige Kennwortfeld mit Titel</span><span class="sxs-lookup"><span data-stu-id="73259-129">Single-line password box with title</span></span>

## <a name="how-to-enable-the-system-keyboard-in-unity"></a><span data-ttu-id="73259-130">Vorgehensweise: aktivieren die Systemtastatur in Unity</span><span class="sxs-lookup"><span data-stu-id="73259-130">How to enable the system keyboard in Unity</span></span>

<span data-ttu-id="73259-131">Die HoloLens-Systemtastatur ist nur verfügbar, um Unity-Anwendungen, die mit der"UWP erstellen", "XAML" exportiert werden.</span><span class="sxs-lookup"><span data-stu-id="73259-131">The HoloLens system keyboard is only available to Unity applications that are exported with the "UWP Build Type" set to "XAML".</span></span> <span data-ttu-id="73259-132">Es gibt Kompromisse, die zu machen, bei der Auswahl von "XAML" als"UWP erstellen" über "D3D".</span><span class="sxs-lookup"><span data-stu-id="73259-132">There are tradeoffs you make when you choose "XAML" as the "UWP Build Type" over "D3D".</span></span> <span data-ttu-id="73259-133">Wenn Sie nicht mit der diese Nachteile vertraut sind, möglicherweise möchten Sie untersuchen eine [Alternative Eingabe Lösung](#alternative-keyboard-options) auf der Systemtastatur.</span><span class="sxs-lookup"><span data-stu-id="73259-133">If you aren't comfortable with those tradeoffs, you may wish to explore an [alternative input solution](#alternative-keyboard-options) to the system keyboard.</span></span>
1. <span data-ttu-id="73259-134">Öffnen der **Datei** Menü **Buildeinstellungen...**</span><span class="sxs-lookup"><span data-stu-id="73259-134">Open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="73259-135">Stellen Sie sicher die **Plattform** nastaven NA hodnotu **Windows Store**, **SDK** nastaven NA hodnotu **universelle 10**, und legen Sie die **UWP Build Type**  zu **XAML**.</span><span class="sxs-lookup"><span data-stu-id="73259-135">Ensure the **Platform** is set to **Windows Store**, the **SDK** is set to **Universal 10**, and set the **UWP Build Type** to **XAML**.</span></span>
3. <span data-ttu-id="73259-136">In der **Buildeinstellungen** Dialogfeld klicken Sie auf die **Playereinstellungen...**  Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="73259-136">In the **Build Settings** dialog, click the **Player Settings...** button</span></span>
4. <span data-ttu-id="73259-137">Wählen Sie die **Einstellungen für Windows Store** Registerkarte</span><span class="sxs-lookup"><span data-stu-id="73259-137">Select the **Settings for Windows Store** tab</span></span>
5. <span data-ttu-id="73259-138">Erweitern Sie die **Weitere Einstellungen** Gruppe</span><span class="sxs-lookup"><span data-stu-id="73259-138">Expand the **Other Settings** group</span></span>
6. <span data-ttu-id="73259-139">In der **Rendern** aktivieren Sie im Abschnitt der **virtuelle Realität unterstützt** Kontrollkästchen zum Hinzufügen einer neuen **Virtual Reality-Geräte** Liste</span><span class="sxs-lookup"><span data-stu-id="73259-139">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list</span></span>
7. <span data-ttu-id="73259-140">Stellen Sie sicher **Windows Holographic** wird in der Liste von Virtual Reality-SDKs</span><span class="sxs-lookup"><span data-stu-id="73259-140">Ensure **Windows Holographic** appears in the list of Virtual Reality SDKs</span></span>

>[!NOTE]
><span data-ttu-id="73259-141">Wenn Sie als virtuelle Realität unterstützt den Build kennzeichnen, mit dem HoloLens-Gerät nicht, wird das Projekt als einer 2D-Texturmap. XAML-app exportieren.</span><span class="sxs-lookup"><span data-stu-id="73259-141">If you don't mark the build as Virtual Reality Supported with the HoloLens device, the project will export as a 2D XAML app.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="73259-142">Verwenden die Systemtastatur in Ihrer Unity-app</span><span class="sxs-lookup"><span data-stu-id="73259-142">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="73259-143">Deklarieren Sie die Tastatur</span><span class="sxs-lookup"><span data-stu-id="73259-143">Declare the keyboard</span></span>

<span data-ttu-id="73259-144">Deklarieren Sie in der Klasse eine Variable zum Speichern der *TouchScreenKeyboard* und gibt eine Variable für die Zeichenfolge der Tastatur.</span><span class="sxs-lookup"><span data-stu-id="73259-144">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="73259-145">Rufen Sie die Tastatur</span><span class="sxs-lookup"><span data-stu-id="73259-145">Invoke the keyboard</span></span>

<span data-ttu-id="73259-146">Tritt ein Ereignis anfordernden Tastatureingaben, rufen Sie eine dieser Funktionen, die je nach Art der gewünschten Eingabe.</span><span class="sxs-lookup"><span data-stu-id="73259-146">When an event occurs requesting keyboard input, call one of these functions depending upon the type of input desired.</span></span> <span data-ttu-id="73259-147">Beachten Sie, dass der Titel im TextPlaceholder-Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="73259-147">Note that the title is specified in the textPlaceholder parameter.</span></span>

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

### <a name="retrieve-typed-contents"></a><span data-ttu-id="73259-148">Rufen Sie typisierte Inhalte</span><span class="sxs-lookup"><span data-stu-id="73259-148">Retrieve typed contents</span></span>

<span data-ttu-id="73259-149">Überprüfen Sie in der Update-Schleife, ob die Tastatur neue Eingabe empfangen, und für die Verwendung an einem anderen Ort zu speichern.</span><span class="sxs-lookup"><span data-stu-id="73259-149">In the update loop, check if the keyboard received new input and store it for use elsewhere.</span></span>

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

## <a name="alternative-keyboard-options"></a><span data-ttu-id="73259-150">Alternative Tastaturoptionen</span><span class="sxs-lookup"><span data-stu-id="73259-150">Alternative keyboard options</span></span>

<span data-ttu-id="73259-151">Uns ist bewusst, dass aus einer volumetrische Ansicht in einer 2D-wechseln die ideale Möglichkeit zum Abrufen der Texteingabe des Benutzers nicht.</span><span class="sxs-lookup"><span data-stu-id="73259-151">We understand that switching out of a volumetric view into a 2D view isn't the ideal way to get text input from the user.</span></span>

<span data-ttu-id="73259-152">Die aktuelle Alternativen zu den-Systemtastatur über Unity nutzen gehören:</span><span class="sxs-lookup"><span data-stu-id="73259-152">The current alternatives to leveraging the system keyboard through Unity include:</span></span>
* <span data-ttu-id="73259-153">Mithilfe von Spracherkennung Diktat für die Eingabe (<b>Hinweis:</b> Dies ist häufig fehleranfällig für Wörter, die nicht im Wörterbuch gefunden wurde, und eignet sich nicht zur Eingabe des Kennworts)</span><span class="sxs-lookup"><span data-stu-id="73259-153">Using speech dictation for input (<b>Note:</b> this is often error prone for words not found in the dictionary and is not suitable for password entry)</span></span>
* <span data-ttu-id="73259-154">Erstellen Sie eine Tastatur, die funktioniert in Ihrer Anwendungen exklusive-Ansicht</span><span class="sxs-lookup"><span data-stu-id="73259-154">Create a keyboard that works in your applications exclusive view</span></span>
