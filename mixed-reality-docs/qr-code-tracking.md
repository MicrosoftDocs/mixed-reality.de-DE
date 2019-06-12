---
title: Qr-Code, Nachverfolgen
description: Erfahren Sie mehr Informationen zum Aktivieren von QR-Code für Ihr Windows Mixed Reality immersive (VR) Kopfhörer, und implementieren Sie das Feature in Ihren VR-apps.
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: vr, lbe, location based entertainment, vr arcade, arcade, immersive, qr, qr code
ms.openlocfilehash: 465056cf645a8b9dc9e0e2d3f9dacf887df67c52
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829986"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="45387-104">Qr-Code, Nachverfolgen</span><span class="sxs-lookup"><span data-stu-id="45387-104">QR code tracking</span></span>

<span data-ttu-id="45387-105">Qr-Code, die nachverfolgung wird in der Windows Mixed Reality-Treiber für immersive Headsets von (VR) implementiert.</span><span class="sxs-lookup"><span data-stu-id="45387-105">QR code tracking is implemented in the Windows Mixed Reality driver for immersive (VR) headsets.</span></span> <span data-ttu-id="45387-106">Durch das Aktivieren der QR-Code-nachverfolgung im Treiber Kopfhörer, den Kopfhörer sucht QR-Codes, und sie möchten apps gemeldet werden.</span><span class="sxs-lookup"><span data-stu-id="45387-106">By enabling the QR code tracker in the headset driver, the headset scans for QR codes and they are reported to interested apps.</span></span> <span data-ttu-id="45387-107">Dieses Feature ist nur verfügbar, ab der [Windows 10 Oktober 2018 Update (auch bekannt als RS5)](release-notes-october-2018.md).</span><span class="sxs-lookup"><span data-stu-id="45387-107">This feature is only available as of the [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span>

>[!NOTE]
><span data-ttu-id="45387-108">Die Codeausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstatt C ++ 17-kompatible C++"/ WinRT", wie in der [ C++ holographic Projektvorlage](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="45387-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="45387-109">Die Konzepte sind Entsprechung für einen C++"/ WinRT"-Projekt, aber Sie benötigen, um den Code zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="45387-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="device-support"></a><span data-ttu-id="45387-110">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="45387-110">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="45387-111"><strong>Funktion</strong></span><span class="sxs-lookup"><span data-stu-id="45387-111"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="45387-112"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="45387-112"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="45387-113"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="45387-113"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="45387-114">Qr-Code, Nachverfolgen</span><span class="sxs-lookup"><span data-stu-id="45387-114">QR code tracking</span></span></td>
        <td><span data-ttu-id="45387-115">❌</span><span class="sxs-lookup"><span data-stu-id="45387-115">❌</span></span></td>
        <td><span data-ttu-id="45387-116">✔️</span><span class="sxs-lookup"><span data-stu-id="45387-116">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a><span data-ttu-id="45387-117">Aktivieren und Deaktivieren von QR-code Überwachung für Ihre Kopfhörer</span><span class="sxs-lookup"><span data-stu-id="45387-117">Enabling and disabling QR code tracking for your headset</span></span>
<span data-ttu-id="45387-118">Hinweis: Dieser Abschnitt gilt nur für [Windows 10 Oktober 2018 Update (auch bekannt als RS5)](release-notes-october-2018.md).</span><span class="sxs-lookup"><span data-stu-id="45387-118">Note: This section is only valid for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span> <span data-ttu-id="45387-119">In 19-h-1-Builds oder höher müssen Sie nicht dazu.</span><span class="sxs-lookup"><span data-stu-id="45387-119">From 19h1 builds onwards you will not have to do this.</span></span>
<span data-ttu-id="45387-120">Ob Sie entwickeln eine mixed Reality-app, die nachverfolgung von QR-Code nutzen, wird, oder Sie ein Kunde eine dieser apps sind, müssen Sie manuell aktivieren, QR-Code in Ihre Kopfhörer des Treibers nachverfolgen.</span><span class="sxs-lookup"><span data-stu-id="45387-120">Whether you're developing a mixed reality app that will leverage QR code tracking, or you're a customer of one of these apps, you'll need to manually turn on QR code tracking in your headset's driver.</span></span>

<span data-ttu-id="45387-121">Um **QR-Code, Nachverfolgen von einschalten** für Ihre immersive (VR) Kopfhörer:</span><span class="sxs-lookup"><span data-stu-id="45387-121">In order to **turn on QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="45387-122">Schließen Sie die Mixed Reality-app auf Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="45387-122">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="45387-123">Trennen Sie die Kopfhörer von Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="45387-123">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="45387-124">Führen Sie das folgende Skript an der Eingabeaufforderung ein:</span><span class="sxs-lookup"><span data-stu-id="45387-124">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. <span data-ttu-id="45387-125">Verbinden Sie Ihre Kopfhörer auf Ihren PC erneut.</span><span class="sxs-lookup"><span data-stu-id="45387-125">Reconnect your headset to your PC.</span></span>

<span data-ttu-id="45387-126">Um **QR-Code, Nachverfolgen von deaktivieren** für Ihre immersive (VR) Kopfhörer:</span><span class="sxs-lookup"><span data-stu-id="45387-126">In order to **turn off QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="45387-127">Schließen Sie die Mixed Reality-app auf Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="45387-127">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="45387-128">Trennen Sie die Kopfhörer von Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="45387-128">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="45387-129">Führen Sie das folgende Skript an der Eingabeaufforderung ein:</span><span class="sxs-lookup"><span data-stu-id="45387-129">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. <span data-ttu-id="45387-130">Verbinden Sie Ihre Kopfhörer auf Ihren PC erneut.</span><span class="sxs-lookup"><span data-stu-id="45387-130">Reconnect your headset to your PC.</span></span> <span data-ttu-id="45387-131">Dadurch wird jede ermittelte QR-Codes "nicht-gefunden werden."</span><span class="sxs-lookup"><span data-stu-id="45387-131">This will make any discovered QR codes "non-locatable."</span></span>

## <a name="printing-codes"></a><span data-ttu-id="45387-132">Drucken-codes</span><span class="sxs-lookup"><span data-stu-id="45387-132">Printing codes</span></span>

<span data-ttu-id="45387-133">Zuallererst die [für QR-Codes Spec](https://www.qrcode.com/en/howto/code.html) sagt, "Bereich Symbol QR-Code erfordert einen Rand oder der"stillen Zone"dazu verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="45387-133">First and foremost, the [spec for QR codes](https://www.qrcode.com/en/howto/code.html) says "The QR Code symbol area requires a margin or "quiet zone" around it to be used.</span></span> <span data-ttu-id="45387-134">Der Rand ist eine klare Bereich auf ein Symbol, in dem nichts gedruckt wird.</span><span class="sxs-lookup"><span data-stu-id="45387-134">The margin is a clear area around a symbol where nothing is printed.</span></span> <span data-ttu-id="45387-135">Qr-Code erfordert eine vier-Module bonustoken auf allen Seiten eines Symbols".</span><span class="sxs-lookup"><span data-stu-id="45387-135">QR Code requires a four-module wide margin at all sides of a symbol."</span></span> <span data-ttu-id="45387-136">Dies muss eine Breite auf jeder Seite der vier Mal die Größe eines Moduls - eine einzelne Schwarzes Quadrat im Code haben.</span><span class="sxs-lookup"><span data-stu-id="45387-136">This needs to have a width, on every side, of four times the size of a module - a single black square in the code.</span></span> <span data-ttu-id="45387-137">Spec diese Seite enthält Hinweise zum Drucken des QR-Codes, und ermitteln, die den Bereich erforderlich, um eine bestimmte Größe QR-Code zu machen.</span><span class="sxs-lookup"><span data-stu-id="45387-137">The spec page contains advice on how to print QR codes and figure out the area required to make a certain sized QR code.</span></span>

<span data-ttu-id="45387-138">Derzeit ist die Erkennung von Qualität von QR-Code anfällig für unterschiedliche Beleuchtung und Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="45387-138">Currently QR code detection quality is susceptible to varying illumination and backdrop.</span></span> <span data-ttu-id="45387-139">Damit dies Beachten Sie Ihrer Beleuchtung aus, und drucken Sie den entsprechenden Code.</span><span class="sxs-lookup"><span data-stu-id="45387-139">To combat this, note your illumination and print the appropriate code.</span></span> <span data-ttu-id="45387-140">Drucken Sie in einer Szene mit besonders hellen Beleuchtung einen Code, der auf einen grauen Hintergrund Schwarz ist.</span><span class="sxs-lookup"><span data-stu-id="45387-140">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="45387-141">Unter einer Licht-Szene, Schwarz in Weiß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="45387-141">Under a low-light scene, black on white works.</span></span> <span data-ttu-id="45387-142">Ebenso ist der Hintergrund auf den Code besonders dunkel, versuchen Sie es Schwarz auf Grau Code Wenn Ihre Erkennungsrate niedrig ist.</span><span class="sxs-lookup"><span data-stu-id="45387-142">Likewise, if the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="45387-143">Andernfalls ist der Hintergrund heller, sollte ein reguläre Code problemlos funktionieren.</span><span class="sxs-lookup"><span data-stu-id="45387-143">Otherwise, if the backdrop is lighter, a regular code should work fine.</span></span>

## <a name="qrtracking-api"></a><span data-ttu-id="45387-144">QRTracking API</span><span class="sxs-lookup"><span data-stu-id="45387-144">QRTracking API</span></span>

<span data-ttu-id="45387-145">Die QRTracking-Plug-Ins macht die APIs für QR-Code, nachverfolgen.</span><span class="sxs-lookup"><span data-stu-id="45387-145">The QRTracking plugin exposes the APIs for QR code tracking.</span></span> <span data-ttu-id="45387-146">Um das Plug-in verwenden zu können, müssen Sie die folgenden Typen von verwenden die *QRCodesTrackerPlugin* Namespace.</span><span class="sxs-lookup"><span data-stu-id="45387-146">To use the plugin, you will need to use the following types from the *QRCodesTrackerPlugin* namespace.</span></span>

```cs
 // QRTracker plugin namespace
 namespace QRCodesTrackerPlugin
 {
    // Encapsulates information about a labeled QR code element.
    public class QRCode
    {        
        // Unique id that identifies this QR code for this session.
        public Guid Id { get; private set; }
           
        // Version of this QR code.
        public Int32 Version { get; private set; }
        
        // PhysicalSizeMeters of this QR code.
        public float PhysicalSizeMeters { get; private set; }
        
        // QR code Data.
        public string Code { get; private set; }
        
        // QR code DataStream this is the error corrected data stream
        public Byte[] CodeStream { get; private set; }
        
        // QR code last detected QPC ticks.
        public Int64 LastDetectedQPCTicks { get; private set; }
    };
    
    // The type of a QR Code added event.
    public class QRCodeAddedEventArgs
    {   
        // Gets the QR Code that was added
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code removed event.
    public class QRCodeRemovedEventArgs
    {
        // Gets the QR Code that was removed.
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code updated event.
    public class QRCodeUpdatedEventArgs
    {
        // Gets the QR Code that was updated.
        public QRCode Code { get; private set; }
    };
    
    // A callback for handling the QR Code added event.
    public delegate void QRCodeAddedHandler(QRCodeAddedEventArgs args);
    
    // A callback for handling the QR Code removed event.
    public delegate void QRCodeRemovedHandler(QRCodeRemovedEventArgs args);
    
    // A callback for handling the QR Code updated event.
    public delegate void QRCodeUpdatedHandler(QRCodeUpdatedEventArgs args);
    
    // Enumerates the possible results of a start of QRTracker.
    public enum QRTrackerStartResult
    {
        // The start has succeeded.
        Success = 0,
        
        //  The currently no device is connected.
        DeviceNotConnected = 1,
        
        // The QRTracking Feature is not supported by the current HMD driver
        // systems
        FeatureNotSupported = 2,
        
        // The access is denide. Administrator needs to enable QR tracker feature.
        AccessDenied = 3,
    };
    
    // QRTracker
    public class QRTracker
    {
        // Constructs a new QRTracker.
        public QRTracker(){}
        
        // Gets the QRTracker.
        public static QRTracker Get()
        {
            return new QRTracker();
        }
        
        // Start the QRTracker. Returns QRTrackerStartResult.
        public QRTrackerStartResult Start()
        {
            throw new NotImplementedException();
        }
        
        // Stops tracking QR codes.
        public void Stop() {}

        // Not Implemented
        Windows.Foundation.Collections.IVector<QRCode> GetList() { throw new NotImplementedException(); }
        
        // Event representing the addition of a QR Code.
        public event QRCodeAddedHandler Added = delegate { };
        
        // Event representing the removal of a QR Code.
        public event QRCodeRemovedHandler Removed = delegate { };
        
        // Event representing the update of a QR Code.
        public event QRCodeUpdatedHandler Updated = delegate { };
    };
}
```

## <a name="implementing-qr-code-tracking-in-unity"></a><span data-ttu-id="45387-147">Implementieren von QR-Code in Unity nachverfolgen</span><span class="sxs-lookup"><span data-stu-id="45387-147">Implementing QR code tracking in Unity</span></span>

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a><span data-ttu-id="45387-148">Beispiel für Unity-Szenen in MRTK (Mixed Reality-Toolkit)</span><span class="sxs-lookup"><span data-stu-id="45387-148">Sample Unity scenes in MRTK (Mixed Reality Toolkit)</span></span>

<span data-ttu-id="45387-149">Sie finden ein Beispiel für die Verwendung der QR-Arbeitselementverfolgungs-API im Mixed Reality-Toolkit [GitHub-Website](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).</span><span class="sxs-lookup"><span data-stu-id="45387-149">You can find an example for how to use the QR Tracking API in the Mixed Reality Toolkit [GitHub site](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).</span></span>

<span data-ttu-id="45387-150">MRTK verfügt über die erforderlichen Skripts Simpilify das Nachverfolgen der Nutzung QR implementiert.</span><span class="sxs-lookup"><span data-stu-id="45387-150">MRTK has implemented the needed scripts to simpilify the QR tracking usage.</span></span> <span data-ttu-id="45387-151">Alle erforderlichen Ressourcen zum Entwickeln von apps nachverfolgen QR befinden sich im Ordner "QRTracker".</span><span class="sxs-lookup"><span data-stu-id="45387-151">All necessary assets to develop QR tracking apps are in the "QRTracker" folder.</span></span> <span data-ttu-id="45387-152">Es gibt zwei Szenen: die erste ist ein Beispiel einfach Details zu den QR-Codes angezeigt, wie sie erkannt werden, und die zweite zeigt, wie das Koordinatensystem, die angefügt werden, um den QR-Code zu verwenden, um Hologramme anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="45387-152">There are two scenes: the first is a sample to simply show details of the QR codes as they are detected, and the second demonstrates how to use the coordinate system attached to the QR code to display holograms.</span></span>
<span data-ttu-id="45387-153">Es gibt eine prefab "QRScanner" die im Hintergrund QRCodes verwenden alle erforderlichen Skripts hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="45387-153">There is a prefab "QRScanner" which added all the necessary scripts to the scenes to use QRCodes.</span></span> <span data-ttu-id="45387-154">Das Skript QRCodeManager ist eine Singletonklasse, die QRCode-API implementiert.</span><span class="sxs-lookup"><span data-stu-id="45387-154">The script QRCodeManager is a singleton class that implements the QRCode API.</span></span> <span data-ttu-id="45387-155">Dies muss der Szene hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="45387-155">This needs to be added to your scene.</span></span> <span data-ttu-id="45387-156">Das Skript "AttachToQRCode" wird verwendet, können Sie den QR-Code Koordinatensysteme Hologramme zuordnen, kann dieses Skript auf Ihrem Hologramme hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="45387-156">The script "AttachToQRCode" is used to attach holograms to the QR Code coordinate systems, this script can be added to any of your holograms.</span></span> <span data-ttu-id="45387-157">Die "SpatialGraphCoordinateSystem" veranschaulicht, wie das QRCode-Koordinatensystem.</span><span class="sxs-lookup"><span data-stu-id="45387-157">The "SpatialGraphCoordinateSystem" shows how to use the QRCode coordinate system.</span></span> <span data-ttu-id="45387-158">Diese Skripts können verwendet werden, als-ist in Ihrem Projekt im Hintergrund oder Sie können Ihre eigenen direkt mit schreiben das Plug-in wie oben beschrieben.</span><span class="sxs-lookup"><span data-stu-id="45387-158">These scripts can be used as-is in your project scenes or you can write your own directly using the plugin as described above.</span></span>

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a><span data-ttu-id="45387-159">Implementieren von QR-Code in Unity ohne MRTK nachverfolgen</span><span class="sxs-lookup"><span data-stu-id="45387-159">Implementing QR code tracking in Unity without MRTK</span></span>

<span data-ttu-id="45387-160">Sie können auch den QR-Arbeitselementverfolgungs-API in Unity verwenden, ohne eine Abhängigkeit auf MRTK.</span><span class="sxs-lookup"><span data-stu-id="45387-160">You can also use the QR Tracking API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="45387-161">Um die API zu verwenden, müssen Sie Ihr Projekt mit der folgenden Anweisung vorzubereiten:</span><span class="sxs-lookup"><span data-stu-id="45387-161">In order to use the API, you will need to prepare your project with the following instruction:</span></span>

1. <span data-ttu-id="45387-162">Erstellen Sie einen neuen Ordner, in dem Ordner "Assets" Ihres Unity-Projekts mit dem Namen: "Plug-Ins".</span><span class="sxs-lookup"><span data-stu-id="45387-162">Create a new folder in the assets folder of your unity project with the name: "Plugins".</span></span>
2. <span data-ttu-id="45387-163">Kopieren Sie alle erforderlichen Dateien aus [in diesem Ordner](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) in den lokalen "Plug-Ins"-Ordner, die Sie gerade erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="45387-163">Copy all the required files from [this folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) into the local "Plugins" folder you just created.</span></span>
3. <span data-ttu-id="45387-164">Können Sie den QR-nachverfolgung-Skripts in der [MRTK Ordner "Scripts"](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) oder Ihr eigenes schreiben.</span><span class="sxs-lookup"><span data-stu-id="45387-164">You can use the QR tracking scripts in the [MRTK scripts folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) or write your own.</span></span>
<span data-ttu-id="45387-165">Hinweis: Diese Plug-Ins sind nur für [Windows 10 Oktober 2018 Update (auch bekannt als RS5)](release-notes-october-2018.md) erstellt.</span><span class="sxs-lookup"><span data-stu-id="45387-165">Note: These plugins are only for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md) builds.</span></span> <span data-ttu-id="45387-166">Die Plug-Ins wird mit der nächsten Version von Windows aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="45387-166">The plugins will be updated with the next windows release.</span></span> <span data-ttu-id="45387-167">Die aktuelle Plug-Ins wurden experimentelle und funktionieren nicht bei zukünftigen Versionen von Windows.</span><span class="sxs-lookup"><span data-stu-id="45387-167">The current plugins were experimental and will not work for future version of the windows.</span></span> <span data-ttu-id="45387-168">Neue Plug-Ins werden veröffentlicht, die aus der nächsten Version von Windows verwendet werden kann, und sie werden nicht rückwärts kompatibel und können nicht mehr mit RS5).</span><span class="sxs-lookup"><span data-stu-id="45387-168">New plugins will be published which can be used from next windows release and they will not be backwards compatable and will not work with RS5).</span></span>

## <a name="implementing-qr-code-tracking-in-directx"></a><span data-ttu-id="45387-169">Implementieren von QR-Code in DirectX nachverfolgen</span><span class="sxs-lookup"><span data-stu-id="45387-169">Implementing QR code tracking in DirectX</span></span>

<span data-ttu-id="45387-170">Um die QRTrackingPlugin in Visual Studio verwenden zu können, müssen Sie die .winmd Verweis von der QRTrackingPlugin hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="45387-170">To use the QRTrackingPlugin in Visual Studio, you will need to add reference of the QRTrackingPlugin to the .winmd.</span></span> <span data-ttu-id="45387-171">Sie finden die [erforderlichen Dateien für die unterstützten Plattformen hier](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span><span class="sxs-lookup"><span data-stu-id="45387-171">You can find the [required files for supported platforms here](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span></span>

```cpp
// MyClass.h
public ref class MyClass
{
    private:
      QRCodesTrackerPlugin::QRTracker^ m_qrtracker;
      // Handlers
      void OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args);
      void OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args);
      void OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args);
    ..
};
```

```cpp
// MyClass.cpp
MyClass::MyClass()
{
    // Create the tracker and register the callbacks
    m_qrtracker = ref new QRCodesTrackerPlugin::QRTracker();
    m_qrtracker->Added += ref new QRCodesTrackerPlugin::QRCodeAddedHandler(this, &OnAddedQRCode);
    m_qrtracker->Updated += ref new QRCodesTrackerPlugin::QRCodeUpdatedHandler(this, &OnUpdatedQRCode);
    m_qrtracker->Removed += ref new QRCodesTrackerPlugin::QRCodeRemovedHandler(this, &QOnRemovedQRCode);

    // Start the tracker
    if (m_qrtracker->Start() != QRCodesTrackerPlugin::QRTrackerStartResult::Success)
    {
      // Handle the failure
      // It can fail for multiple reasons and can be handled properly 
    }
}

void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    // use args->Code add to own list  
}

void MyClass::OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args)
{
    // use args->Code update the existing one with the new one in own list 
}

void MyClass::OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args)
{
    // use args->Code remove from own list.
}
```

## <a name="getting-a-coordinate-system"></a><span data-ttu-id="45387-172">Abrufen von einem Koordinatensystem</span><span class="sxs-lookup"><span data-stu-id="45387-172">Getting a coordinate system</span></span>

<span data-ttu-id="45387-173">Wir definieren ein rechten Koordinatensystem, die mit dem QR-Code auf der oberen linken Ecke des Quadrats Schnelle Erkennung in der oberen linken Ecke ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="45387-173">We define a right-hand coordinate system aligned with the QR code at the top left corner of the fast detection square in the top left.</span></span> <span data-ttu-id="45387-174">Das Koordinatensystem ist unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="45387-174">The coordinate system is shown below.</span></span> <span data-ttu-id="45387-175">Die z-Achse in das Dokument (nicht gezeigt) zeigt, in Unity die z-Achse ist jedoch kein Papier und Linkshänder.</span><span class="sxs-lookup"><span data-stu-id="45387-175">The Z-axis is pointing into the paper (not shown), but in Unity the z-axis is out of the paper and left-handed.</span></span>

<span data-ttu-id="45387-176">Eine SpatialCoordinateSystem wird definiert, die wie gezeigt ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="45387-176">A SpatialCoordinateSystem is defined that is aligned as shown.</span></span> <span data-ttu-id="45387-177">Dieses Koordinatensystem abgerufen werden kann, von der Plattform, die mit der API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.</span><span class="sxs-lookup"><span data-stu-id="45387-177">This coordinate system can be obtained from the platform using the API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.</span></span>

![Qr-Code-Koordinatensystem](images/Qr-coordinatesystem.png) 

<span data-ttu-id="45387-179">Von QRCode ^-Objekt Code, der folgende Code zeigt, wie Sie ein Rechteck erstellt, und fügen Sie ihn in den QR-Koordinatensystem:</span><span class="sxs-lookup"><span data-stu-id="45387-179">From QRCode^ Code object, the following code shows how to create a rectangle and put it in QR coordinate system:</span></span>

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> SpatialStageManager::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0,  0, 0 };
    vertices[1] = { width,  0, 0 };
    vertices[2] = { width,  height, 0 };
    vertices[3] = { 0,  height, 0 };

    return vertices;
}
```

<span data-ttu-id="45387-180">Sie können die physische Größe verwenden, um den QR-Rechteck zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="45387-180">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

<span data-ttu-id="45387-181">Zeichnen den QR-Code oder das Anfügen von Hologramme auf den Speicherort, kann das Koordinatensystem verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="45387-181">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

<span data-ttu-id="45387-182">Vollständig zu entfernen und Ihre *QRCodesTrackerPlugin::QRCodeAddedHandler* kann etwa wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="45387-182">Altogether, your *QRCodesTrackerPlugin::QRCodeAddedHandler* may look something like this:</span></span>

```cpp
void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    std::vector<float3> qrVertices = CreateRectangle(args->Code->PhysicalSizeMeters, args->Code->PhysicalSizeMeters);
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem =  Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(args->Code->Id);
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            reinterpret_cast<std::vector<XMFLOAT3>&>(qrVertices),
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="troubleshooting-and-faq"></a><span data-ttu-id="45387-183">Problembehandlung und häufig gestellte Fragen</span><span class="sxs-lookup"><span data-stu-id="45387-183">Troubleshooting and FAQ</span></span>

<span data-ttu-id="45387-184">**Allgemeine Problembehandlung**</span><span class="sxs-lookup"><span data-stu-id="45387-184">**General troubleshooting**</span></span>

* <span data-ttu-id="45387-185">Wird Ihr PC mit Windows 10 Oktober 2018 aktualisieren?</span><span class="sxs-lookup"><span data-stu-id="45387-185">Is your PC running the Windows 10 October 2018 Update?</span></span>
* <span data-ttu-id="45387-186">Haben Sie den Registrierungsschlüssel festgelegt?</span><span class="sxs-lookup"><span data-stu-id="45387-186">Have you set the reg key?</span></span> <span data-ttu-id="45387-187">Neustart das Gerät anschließend?</span><span class="sxs-lookup"><span data-stu-id="45387-187">Restarted the device afterwards?</span></span>
* <span data-ttu-id="45387-188">Ist die Version des QR-Code eine unterstützte Version?</span><span class="sxs-lookup"><span data-stu-id="45387-188">Is the QR code version a supported version?</span></span> <span data-ttu-id="45387-189">Aktuelle API unterstützt bis zu 20 für QR-Code-Version.</span><span class="sxs-lookup"><span data-stu-id="45387-189">Current API supports up to QR Code Version 20.</span></span> <span data-ttu-id="45387-190">Es wird empfohlen, Version 5 für die allgemeine Nutzung verwenden.</span><span class="sxs-lookup"><span data-stu-id="45387-190">We recommend using version 5 for general usage.</span></span> 
* <span data-ttu-id="45387-191">Sind Sie genug, um den QR-Code schließen?</span><span class="sxs-lookup"><span data-stu-id="45387-191">Are you close enough to the QR code?</span></span> <span data-ttu-id="45387-192">Je näher die Kamera ist den QR-Code, je höher der QR-Code-Version der API unterstützen kann.</span><span class="sxs-lookup"><span data-stu-id="45387-192">The closer the camera is to the QR code, the higher the QR code version the API can support.</span></span>  

<span data-ttu-id="45387-193">**Muss ich wie nah an den QR-Code erkannt werden?**</span><span class="sxs-lookup"><span data-stu-id="45387-193">**How close do I need to be to the QR code to detect it?**</span></span>

<span data-ttu-id="45387-194">Dies hängt von der Größe des QR-Codes, und darüber Version ist.</span><span class="sxs-lookup"><span data-stu-id="45387-194">This will depend on the size of the QR code, and also what version it is.</span></span> <span data-ttu-id="45387-195">Für eine Version 1 QR-Code von 5 cm Seiten auf 25 cm Seiten variieren reicht die minimale Erkennung Entfernung von 0,15 Zähler zu 0,5 m ein.</span><span class="sxs-lookup"><span data-stu-id="45387-195">For a version 1 QR code varying from 5 cm sides to 25 cm sides, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> <span data-ttu-id="45387-196">Die am weitesten entfernten entfernt, die diese aus erkannt werden können reicht von ca. 0.3 Meter für die kleineren QR-Code-Ziele 1,4-Zähler für die größeren.</span><span class="sxs-lookup"><span data-stu-id="45387-196">The farthest away these can be detected from goes from about 0.3 meters for the smaller QR code targets to 1.4 meters for the bigger.</span></span> <span data-ttu-id="45387-197">Für QR-Codes größer als, können Sie schätzen, die Erkennung von Entfernung für Größe steigt linear.</span><span class="sxs-lookup"><span data-stu-id="45387-197">For QR codes bigger than that, you can estimate; the detection distance for size increases linearly.</span></span> <span data-ttu-id="45387-198">Unsere Tracker funktioniert nicht mit QR-Codes mit Seiten kleiner als 5 cm.</span><span class="sxs-lookup"><span data-stu-id="45387-198">Our tracker does not work with QR codes with sides smaller than 5 cm.</span></span>

<span data-ttu-id="45387-199">**Tun Sie qr-Codes mit Logos?**</span><span class="sxs-lookup"><span data-stu-id="45387-199">**Do QR codes with logos work?**</span></span>

<span data-ttu-id="45387-200">Qr-Codes mit Logos wurden nicht getestet und werden derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="45387-200">QR codes with logos have not been tested and are currently unsupported.</span></span>

<span data-ttu-id="45387-201">**Wie lösche ich QR-Codes aus meiner app, damit sie bleiben nicht?**</span><span class="sxs-lookup"><span data-stu-id="45387-201">**How do I clear QR codes from my app so they don't persist?**</span></span>

* <span data-ttu-id="45387-202">Qr-Codes werden nur in der startsitzung beibehalten.</span><span class="sxs-lookup"><span data-stu-id="45387-202">QR codes are only persisted in the boot session.</span></span> <span data-ttu-id="45387-203">Sobald Sie neu starten (oder neu des Treibers starten), werden sie durchgeführt und als neue Objekte nächsten erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="45387-203">Once you reboot (or restart the driver), they will be gone and detected as new objects next time.</span></span>
* <span data-ttu-id="45387-204">Verlauf der QR-Codes wird in der treibersitzung auf der Systemebene gespeichert, aber Sie können konfigurieren, dass Ihre app, um QR-Codes, die älter sind als die eines bestimmten Zeitstempels zu ignorieren, wenn Sie möchten.</span><span class="sxs-lookup"><span data-stu-id="45387-204">QR code history is saved at the system level in the driver session, but you can configure your app to ignore QR codes older than a specific timestamp if you want.</span></span> <span data-ttu-id="45387-205">Derzeit unterstützt die API Verlauf löschen QR-Codes, wie die Daten mehrere apps interessiert sein könnten.</span><span class="sxs-lookup"><span data-stu-id="45387-205">Currently the API does support clearing QR code history, as multiple apps might be interested in the data.</span></span>

<span data-ttu-id="45387-206">**Die Plug-Ins für RS5 und zukünftigen Versionen nicht kompatibel sind** RS5-Version des Plug-Ins funktioniert nur für RS5 und funktioniert nicht für zukünftige Versionen.</span><span class="sxs-lookup"><span data-stu-id="45387-206">**The plugins for RS5 and future versions are not compatable** RS5 version of the plugin only works for RS5 and will not work for future versions.</span></span> <span data-ttu-id="45387-207">Die Expermental-Plug-in mit der real-Plug-in ersetzt werden und sollte sein, dass wir in zukünftigen Versionen von Windows können.</span><span class="sxs-lookup"><span data-stu-id="45387-207">The expermental plugin will be replaced with the real plugin and should be the one that we can use in future versions of the windows.</span></span>
