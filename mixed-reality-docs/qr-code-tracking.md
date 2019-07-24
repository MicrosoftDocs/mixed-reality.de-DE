---
title: QR-Code Nachverfolgung
description: Erfahren Sie, wie Sie die QR-Code Überwachung für Ihr Windows Mixed Reality-immersive-Headset (VR) aktivieren und das Feature in ihren VR-apps implementieren.
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: VR, LBE, Location based Entertainment, VR-Arkade, Arcade, immersive, QR, QR-Code
ms.openlocfilehash: 465056cf645a8b9dc9e0e2d3f9dacf887df67c52
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829986"
---
# <a name="qr-code-tracking"></a><span data-ttu-id="5ef1e-104">QR-Code Nachverfolgung</span><span class="sxs-lookup"><span data-stu-id="5ef1e-104">QR code tracking</span></span>

<span data-ttu-id="5ef1e-105">Die QR-Code Überwachung wird in den Windows Mixed Reality Driver for Immersive (VR)-Headsets implementiert.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-105">QR code tracking is implemented in the Windows Mixed Reality driver for immersive (VR) headsets.</span></span> <span data-ttu-id="5ef1e-106">Durch Aktivieren der QR-Code Protokollierung im Headset-Treiber scannt das Headset nach QR-Codes und wird an interessierte apps gemeldet.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-106">By enabling the QR code tracker in the headset driver, the headset scans for QR codes and they are reported to interested apps.</span></span> <span data-ttu-id="5ef1e-107">Diese Funktion ist nur ab dem [Windows 10-Update vom Oktober 2018 (auch bekannt als RS5)](release-notes-october-2018.md)verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-107">This feature is only available as of the [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span>

>[!NOTE]
><span data-ttu-id="5ef1e-108">Die Code Ausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung C++von/CX anstelle von C + +17- C++kompatibler/WinRT, wie Sie in der [ C++ Holographic-Projektvorlage](creating-a-holographic-directx-project.md)verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-108">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="5ef1e-109">Die Konzepte sind äquivalent für ein C++/WinRT-Projekt, obwohl Sie den Code übersetzen müssen.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-109">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="device-support"></a><span data-ttu-id="5ef1e-110">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="5ef1e-110">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="5ef1e-111"><strong>Funktion</strong></span><span class="sxs-lookup"><span data-stu-id="5ef1e-111"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="5ef1e-112"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="5ef1e-112"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="5ef1e-113"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="5ef1e-113"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="5ef1e-114">QR-Code Nachverfolgung</span><span class="sxs-lookup"><span data-stu-id="5ef1e-114">QR code tracking</span></span></td>
        <td><span data-ttu-id="5ef1e-115">❌</span><span class="sxs-lookup"><span data-stu-id="5ef1e-115">❌</span></span></td>
        <td><span data-ttu-id="5ef1e-116">✔️</span><span class="sxs-lookup"><span data-stu-id="5ef1e-116">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a><span data-ttu-id="5ef1e-117">Aktivieren und Deaktivieren der QR-Code-Nachverfolgung für Ihr Headset</span><span class="sxs-lookup"><span data-stu-id="5ef1e-117">Enabling and disabling QR code tracking for your headset</span></span>
<span data-ttu-id="5ef1e-118">Hinweis: Dieser Abschnitt gilt nur für [Windows 10-Update vom Oktober 2018 (auch bekannt als RS5)](release-notes-october-2018.md).</span><span class="sxs-lookup"><span data-stu-id="5ef1e-118">Note: This section is only valid for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md).</span></span> <span data-ttu-id="5ef1e-119">Ab 19h1 müssen Sie dies nicht mehr tun.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-119">From 19h1 builds onwards you will not have to do this.</span></span>
<span data-ttu-id="5ef1e-120">Unabhängig davon, ob Sie eine Mixed Reality-App entwickeln, die die QR-Code-Nachverfolgung nutzt, oder Sie sind ein Kunde einer dieser apps, müssen Sie die QR-Code-Nachverfolgung manuell in den Treiber Ihres Headsets einschalten.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-120">Whether you're developing a mixed reality app that will leverage QR code tracking, or you're a customer of one of these apps, you'll need to manually turn on QR code tracking in your headset's driver.</span></span>

<span data-ttu-id="5ef1e-121">Um die **QR-Code** -Nachverfolgung für Ihr immersives (VR)-Headset zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="5ef1e-121">In order to **turn on QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="5ef1e-122">Schließen Sie die Mixed Reality-Portal-App auf Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-122">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="5ef1e-123">Entfernen Sie das Headset von Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-123">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="5ef1e-124">Führen Sie das folgende Skript an der Eingabeaufforderung aus:</span><span class="sxs-lookup"><span data-stu-id="5ef1e-124">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. <span data-ttu-id="5ef1e-125">Verbinden Sie Ihr Headset erneut mit Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-125">Reconnect your headset to your PC.</span></span>

<span data-ttu-id="5ef1e-126">Um die **QR-Code** -Nachverfolgung für Ihr immersives (VR)-Headset zu deaktivieren:</span><span class="sxs-lookup"><span data-stu-id="5ef1e-126">In order to **turn off QR code tracking** for your immersive (VR) headset:</span></span>

1. <span data-ttu-id="5ef1e-127">Schließen Sie die Mixed Reality-Portal-App auf Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-127">Close the Mixed Reality Portal app on your PC.</span></span>
2. <span data-ttu-id="5ef1e-128">Entfernen Sie das Headset von Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-128">Unplug the headset from your PC.</span></span>
3. <span data-ttu-id="5ef1e-129">Führen Sie das folgende Skript an der Eingabeaufforderung aus:</span><span class="sxs-lookup"><span data-stu-id="5ef1e-129">Run the following script in the Command Prompt:</span></span><br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. <span data-ttu-id="5ef1e-130">Verbinden Sie Ihr Headset erneut mit Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-130">Reconnect your headset to your PC.</span></span> <span data-ttu-id="5ef1e-131">Dadurch werden alle ermittelten QR-Codes "nicht erstellbar".</span><span class="sxs-lookup"><span data-stu-id="5ef1e-131">This will make any discovered QR codes "non-locatable."</span></span>

## <a name="printing-codes"></a><span data-ttu-id="5ef1e-132">Druck Codes</span><span class="sxs-lookup"><span data-stu-id="5ef1e-132">Printing codes</span></span>

<span data-ttu-id="5ef1e-133">Vor allem bedeutet die [Spezifikation für QR-Codes, dass](https://www.qrcode.com/en/howto/code.html) der QR-Code Symbol Bereich einen Rand oder eine "Stille Zone" für die Verwendung benötigt.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-133">First and foremost, the [spec for QR codes](https://www.qrcode.com/en/howto/code.html) says "The QR Code symbol area requires a margin or "quiet zone" around it to be used.</span></span> <span data-ttu-id="5ef1e-134">Der Rand ist ein klarer Bereich um ein Symbol, in dem nichts gedruckt wird.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-134">The margin is a clear area around a symbol where nothing is printed.</span></span> <span data-ttu-id="5ef1e-135">Der QR-Code erfordert einen vier-Module-breiten Rand an allen Seiten eines Symbols. "</span><span class="sxs-lookup"><span data-stu-id="5ef1e-135">QR Code requires a four-module wide margin at all sides of a symbol."</span></span> <span data-ttu-id="5ef1e-136">Dies muss auf jeder Seite eine Breite von vier Mal der Größe eines Moduls aufweisen, einem einzelnen schwarzen Quadrat im Code.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-136">This needs to have a width, on every side, of four times the size of a module - a single black square in the code.</span></span> <span data-ttu-id="5ef1e-137">Die Seite "Spezifikationen" enthält Ratschläge zum Drucken von QR-Codes und zum Ermitteln des Bereichs, der zum Erstellen eines QR-Codes mit einer bestimmten Größe erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-137">The spec page contains advice on how to print QR codes and figure out the area required to make a certain sized QR code.</span></span>

<span data-ttu-id="5ef1e-138">Derzeit ist die Qualität der QR-Code Erkennung anfällig für die unterschiedliche Beleuchtung und den Hintergrund.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-138">Currently QR code detection quality is susceptible to varying illumination and backdrop.</span></span> <span data-ttu-id="5ef1e-139">Um dies zu bekämpfen, notieren Sie sich Ihre Beleuchtung, und Drucken Sie den entsprechenden Code.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-139">To combat this, note your illumination and print the appropriate code.</span></span> <span data-ttu-id="5ef1e-140">Drucken Sie in einer Szene mit besonders heller Beleuchtung einen Code, der in einem grauen Hintergrund schwarz ist.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-140">In a scene with particularly bright lighting, print a code that is black on a gray background.</span></span> <span data-ttu-id="5ef1e-141">In einer Low-Light-Szene ist schwarz bei White Works.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-141">Under a low-light scene, black on white works.</span></span> <span data-ttu-id="5ef1e-142">Wenn der Hintergrund des Codes besonders dunkel ist, sollten Sie auch eine schwarz mit grauem Code ausprobieren, wenn die Erkennungsrate niedrig ist.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-142">Likewise, if the backdrop to the code is particularly dark, try a black on gray code if your detection rate is low.</span></span> <span data-ttu-id="5ef1e-143">Andernfalls sollte ein regulärer Code einwandfrei funktionieren, wenn der Hintergrund heller ist.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-143">Otherwise, if the backdrop is lighter, a regular code should work fine.</span></span>

## <a name="qrtracking-api"></a><span data-ttu-id="5ef1e-144">Qrtracking-API</span><span class="sxs-lookup"><span data-stu-id="5ef1e-144">QRTracking API</span></span>

<span data-ttu-id="5ef1e-145">Das qrtracking-Plug-in macht die APIs für die QR-Code Überwachung verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-145">The QRTracking plugin exposes the APIs for QR code tracking.</span></span> <span data-ttu-id="5ef1e-146">Um das Plug-in zu verwenden, müssen Sie die folgenden Typen aus dem *qrcodestrackerplugin* -Namespace verwenden.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-146">To use the plugin, you will need to use the following types from the *QRCodesTrackerPlugin* namespace.</span></span>

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

## <a name="implementing-qr-code-tracking-in-unity"></a><span data-ttu-id="5ef1e-147">Implementieren der QR-Code-Nachverfolgung in Unity</span><span class="sxs-lookup"><span data-stu-id="5ef1e-147">Implementing QR code tracking in Unity</span></span>

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a><span data-ttu-id="5ef1e-148">Beispiel für Unity-Szenen in mrtk (Mixed Reality Toolkit)</span><span class="sxs-lookup"><span data-stu-id="5ef1e-148">Sample Unity scenes in MRTK (Mixed Reality Toolkit)</span></span>

<span data-ttu-id="5ef1e-149">Ein Beispiel für die Verwendung der QR-Überwachungs-API finden Sie auf der [GitHub-Website](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)des Mixed Reality-Toolkits.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-149">You can find an example for how to use the QR Tracking API in the Mixed Reality Toolkit [GitHub site](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).</span></span>

<span data-ttu-id="5ef1e-150">Mrtk hat die benötigten Skripts implementiert, um die Verwendung der QR-Nachverfolgung zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-150">MRTK has implemented the needed scripts to simpilify the QR tracking usage.</span></span> <span data-ttu-id="5ef1e-151">Alle erforderlichen Assets zum Entwickeln von QR-nach Verfolgungs-apps befinden sich im Ordner "qrtracker".</span><span class="sxs-lookup"><span data-stu-id="5ef1e-151">All necessary assets to develop QR tracking apps are in the "QRTracker" folder.</span></span> <span data-ttu-id="5ef1e-152">Es gibt zwei Szenen: das erste ist ein Beispiel für die einfache Anzeige der Details der QR-Codes, wenn Sie erkannt werden. das zweite Beispiel zeigt, wie das Koordinatensystem, das mit dem QR-Code verknüpft ist, zum Anzeigen von holograms verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-152">There are two scenes: the first is a sample to simply show details of the QR codes as they are detected, and the second demonstrates how to use the coordinate system attached to the QR code to display holograms.</span></span>
<span data-ttu-id="5ef1e-153">Es gibt eine Prefab "qrscanner", bei der alle notwendigen Skripts zu den Kulissen hinzugefügt wurden, um qrcodes zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-153">There is a prefab "QRScanner" which added all the necessary scripts to the scenes to use QRCodes.</span></span> <span data-ttu-id="5ef1e-154">Das Skript "qrcodemanager" ist eine Singleton-Klasse, die die QRCode-API implementiert.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-154">The script QRCodeManager is a singleton class that implements the QRCode API.</span></span> <span data-ttu-id="5ef1e-155">Diese muss Ihrer Szene hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-155">This needs to be added to your scene.</span></span> <span data-ttu-id="5ef1e-156">Das Skript "attachdeqrcode" wird verwendet, um Hologramme an die QR-Code Koordinatensysteme anzufügen. dieses Skript kann jedem ihrer holograms hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-156">The script "AttachToQRCode" is used to attach holograms to the QR Code coordinate systems, this script can be added to any of your holograms.</span></span> <span data-ttu-id="5ef1e-157">Das "spatialgraphcoordinatesystem" zeigt, wie das QRCode-Koordinatensystem verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-157">The "SpatialGraphCoordinateSystem" shows how to use the QRCode coordinate system.</span></span> <span data-ttu-id="5ef1e-158">Diese Skripts können unverändert in Ihren Projekt Kulissen verwendet werden, oder Sie können Ihre eigenen Skripts direkt mithilfe des Plug-ins schreiben, wie oben beschrieben.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-158">These scripts can be used as-is in your project scenes or you can write your own directly using the plugin as described above.</span></span>

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a><span data-ttu-id="5ef1e-159">Implementieren der QR-Code-Nachverfolgung in Unity ohne mrtk</span><span class="sxs-lookup"><span data-stu-id="5ef1e-159">Implementing QR code tracking in Unity without MRTK</span></span>

<span data-ttu-id="5ef1e-160">Sie können auch die QR-nach Verfolgungs-API in Unity verwenden, ohne eine Abhängigkeit von mrtk zu treffen.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-160">You can also use the QR Tracking API in Unity without taking a dependency on MRTK.</span></span> <span data-ttu-id="5ef1e-161">Um die API zu verwenden, müssen Sie das Projekt mit der folgenden Anweisung vorbereiten:</span><span class="sxs-lookup"><span data-stu-id="5ef1e-161">In order to use the API, you will need to prepare your project with the following instruction:</span></span>

1. <span data-ttu-id="5ef1e-162">Erstellen Sie im Ordner "Assets" Ihres Unity-Projekts einen neuen Ordner mit dem folgenden Namen: "Plug-ins".</span><span class="sxs-lookup"><span data-stu-id="5ef1e-162">Create a new folder in the assets folder of your unity project with the name: "Plugins".</span></span>
2. <span data-ttu-id="5ef1e-163">Kopieren Sie alle erforderlichen Dateien aus [diesem Ordner](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) in den lokalen Ordner "Plug-ins", den Sie soeben erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-163">Copy all the required files from [this folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) into the local "Plugins" folder you just created.</span></span>
3. <span data-ttu-id="5ef1e-164">Sie können die QR-nach Verfolgungs Skripts im [Ordner "mrtk Scripts](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) " verwenden oder eigene schreiben.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-164">You can use the QR tracking scripts in the [MRTK scripts folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) or write your own.</span></span>
<span data-ttu-id="5ef1e-165">Hinweis: Diese Plug-ins sind nur für [Windows 10-Updates vom Oktober 2018 (auch bekannt als RS5)](release-notes-october-2018.md) .</span><span class="sxs-lookup"><span data-stu-id="5ef1e-165">Note: These plugins are only for [Windows 10 October 2018 Update (also known as RS5)](release-notes-october-2018.md) builds.</span></span> <span data-ttu-id="5ef1e-166">Die Plug-ins werden mit der nächsten Windows-Version aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-166">The plugins will be updated with the next windows release.</span></span> <span data-ttu-id="5ef1e-167">Die aktuellen Plug-ins waren experimentell und funktionieren nicht für zukünftige Versionen von Windows.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-167">The current plugins were experimental and will not work for future version of the windows.</span></span> <span data-ttu-id="5ef1e-168">Neue Plug-ins werden veröffentlicht, die in der nächsten Windows-Version verwendet werden können, und Sie sind nicht abwärts kompatibel und funktionieren nicht mit RS5).</span><span class="sxs-lookup"><span data-stu-id="5ef1e-168">New plugins will be published which can be used from next windows release and they will not be backwards compatable and will not work with RS5).</span></span>

## <a name="implementing-qr-code-tracking-in-directx"></a><span data-ttu-id="5ef1e-169">Implementieren der QR-Code-Nachverfolgung in DirectX</span><span class="sxs-lookup"><span data-stu-id="5ef1e-169">Implementing QR code tracking in DirectX</span></span>

<span data-ttu-id="5ef1e-170">Um das qrtrackingplugin in Visual Studio verwenden zu können, müssen Sie der Datei ". winmd" einen Verweis auf das qrtrackingplugin hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-170">To use the QRTrackingPlugin in Visual Studio, you will need to add reference of the QRTrackingPlugin to the .winmd.</span></span> <span data-ttu-id="5ef1e-171">Die [erforderlichen Dateien für die unterstützten Plattformen](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA)finden Sie hier.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-171">You can find the [required files for supported platforms here](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).</span></span>

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

## <a name="getting-a-coordinate-system"></a><span data-ttu-id="5ef1e-172">Erhalten eines Koordinatensystems</span><span class="sxs-lookup"><span data-stu-id="5ef1e-172">Getting a coordinate system</span></span>

<span data-ttu-id="5ef1e-173">Wir definieren ein richtiges Koordinatensystem, das mit dem QR-Code in der oberen linken Ecke des Quadrats für schnelle Erkennung in der oberen linken Ecke ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-173">We define a right-hand coordinate system aligned with the QR code at the top left corner of the fast detection square in the top left.</span></span> <span data-ttu-id="5ef1e-174">Das Koordinatensystem ist unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-174">The coordinate system is shown below.</span></span> <span data-ttu-id="5ef1e-175">Die z-Achse zeigt auf das Papier (nicht dargestellt), aber in Unity ist die z-Achse nicht aus dem Papier und von Links.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-175">The Z-axis is pointing into the paper (not shown), but in Unity the z-axis is out of the paper and left-handed.</span></span>

<span data-ttu-id="5ef1e-176">Ein spatialcoordinatesystem ist definiert, das wie gezeigt ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-176">A SpatialCoordinateSystem is defined that is aligned as shown.</span></span> <span data-ttu-id="5ef1e-177">Dieses Koordinatensystem kann von der Plattform mithilfe der API-Fenster abgerufen werden *::P erception:: Spatial::P Review:: spatialgraphinteroppreview:: foratecoordinatesystemfornode*.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-177">This coordinate system can be obtained from the platform using the API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.</span></span>

![QR-Code Koordinatensystem](images/Qr-coordinatesystem.png) 

<span data-ttu-id="5ef1e-179">Im Code-Objekt von QRCode ^ zeigt der folgende Code, wie ein Rechteck erstellt und in das QR-Koordinatensystem eingefügt wird:</span><span class="sxs-lookup"><span data-stu-id="5ef1e-179">From QRCode^ Code object, the following code shows how to create a rectangle and put it in QR coordinate system:</span></span>

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

<span data-ttu-id="5ef1e-180">Sie können die physische Größe zum Erstellen des QR-Rechtecks verwenden:</span><span class="sxs-lookup"><span data-stu-id="5ef1e-180">You can use the physical size to create the QR rectangle:</span></span>

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

<span data-ttu-id="5ef1e-181">Das Koordinatensystem kann zum Zeichnen des QR-Codes oder zum Anfügen von holograms an den Speicherort verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="5ef1e-181">The coordinate system can be used to draw the QR code or attach holograms to the location:</span></span>

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

<span data-ttu-id="5ef1e-182">Ihr *qrcodestrackerplugin:: qrcodeaddedhandler* könnte etwa wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="5ef1e-182">Altogether, your *QRCodesTrackerPlugin::QRCodeAddedHandler* may look something like this:</span></span>

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

## <a name="troubleshooting-and-faq"></a><span data-ttu-id="5ef1e-183">Problembehandlung und FAQ</span><span class="sxs-lookup"><span data-stu-id="5ef1e-183">Troubleshooting and FAQ</span></span>

<span data-ttu-id="5ef1e-184">**Allgemeine Problembehandlung**</span><span class="sxs-lookup"><span data-stu-id="5ef1e-184">**General troubleshooting**</span></span>

* <span data-ttu-id="5ef1e-185">Führt der PC das Windows 10-Update vom Oktober 2018 aus?</span><span class="sxs-lookup"><span data-stu-id="5ef1e-185">Is your PC running the Windows 10 October 2018 Update?</span></span>
* <span data-ttu-id="5ef1e-186">Haben Sie den Schlüssel "reg" festgelegt?</span><span class="sxs-lookup"><span data-stu-id="5ef1e-186">Have you set the reg key?</span></span> <span data-ttu-id="5ef1e-187">Sie das Gerät später neu starten?</span><span class="sxs-lookup"><span data-stu-id="5ef1e-187">Restarted the device afterwards?</span></span>
* <span data-ttu-id="5ef1e-188">Ist die QR-Code Version eine unterstützte Version?</span><span class="sxs-lookup"><span data-stu-id="5ef1e-188">Is the QR code version a supported version?</span></span> <span data-ttu-id="5ef1e-189">Die aktuelle API unterstützt bis zu QR-Code Version 20.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-189">Current API supports up to QR Code Version 20.</span></span> <span data-ttu-id="5ef1e-190">Wir empfehlen die Verwendung von Version 5 für die allgemeine Verwendung.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-190">We recommend using version 5 for general usage.</span></span> 
* <span data-ttu-id="5ef1e-191">Sind Sie für den QR-Code fast ausreichend?</span><span class="sxs-lookup"><span data-stu-id="5ef1e-191">Are you close enough to the QR code?</span></span> <span data-ttu-id="5ef1e-192">Je näher die Kamera an dem QR-Code liegt, desto höher ist die QR-Code Version, die von der API unterstützt werden kann.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-192">The closer the camera is to the QR code, the higher the QR code version the API can support.</span></span>  

<span data-ttu-id="5ef1e-193">**Wie nah muss ich auf den QR-Code sein, um ihn zu erkennen?**</span><span class="sxs-lookup"><span data-stu-id="5ef1e-193">**How close do I need to be to the QR code to detect it?**</span></span>

<span data-ttu-id="5ef1e-194">Dies hängt von der Größe des QR-Codes und von der Version ab.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-194">This will depend on the size of the QR code, and also what version it is.</span></span> <span data-ttu-id="5ef1e-195">Bei einem QR-Code der Version 1, der zwischen 5 cm-Seiten und 25 cm-Seiten variiert, liegt der Abstand der minimalen Erkennung zwischen 0,15 und 0,5 Meter.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-195">For a version 1 QR code varying from 5 cm sides to 25 cm sides, the minimum detection distance ranges from 0.15 meters to 0.5 meters.</span></span> <span data-ttu-id="5ef1e-196">Die am weitesten entfernten Werte können von ungefähr 0,3 Meter für die kleineren QR-codeziele auf 1,4 Meter für die größere festgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-196">The farthest away these can be detected from goes from about 0.3 meters for the smaller QR code targets to 1.4 meters for the bigger.</span></span> <span data-ttu-id="5ef1e-197">Bei QR-Codes, die größer als dieser Wert sind, können Sie schätzen: der Erkennungsabstand für die Größe erhöht sich linear.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-197">For QR codes bigger than that, you can estimate; the detection distance for size increases linearly.</span></span> <span data-ttu-id="5ef1e-198">Unsere Tracker funktioniert nicht mit QR-Codes, die kleiner als 5 cm sind.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-198">Our tracker does not work with QR codes with sides smaller than 5 cm.</span></span>

<span data-ttu-id="5ef1e-199">**Funktionieren QR-Codes mit Logos?**</span><span class="sxs-lookup"><span data-stu-id="5ef1e-199">**Do QR codes with logos work?**</span></span>

<span data-ttu-id="5ef1e-200">QR-Codes mit Logos wurden nicht getestet und werden zurzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-200">QR codes with logos have not been tested and are currently unsupported.</span></span>

<span data-ttu-id="5ef1e-201">**Gewusst wie die QR-Codes aus meiner app löschen, damit Sie nicht persistent gespeichert werden?**</span><span class="sxs-lookup"><span data-stu-id="5ef1e-201">**How do I clear QR codes from my app so they don't persist?**</span></span>

* <span data-ttu-id="5ef1e-202">QR-Codes werden nur in der Start Sitzung beibehalten.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-202">QR codes are only persisted in the boot session.</span></span> <span data-ttu-id="5ef1e-203">Sobald Sie den Treiber neu starten (oder neu starten), werden diese nach dem nächsten Mal als neue Objekte erkannt.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-203">Once you reboot (or restart the driver), they will be gone and detected as new objects next time.</span></span>
* <span data-ttu-id="5ef1e-204">Der QR-Code Verlauf wird auf der Systemebene in der Treiber Sitzung gespeichert, aber Sie können Ihre APP so konfigurieren, dass Sie QR-Codes ignoriert, die älter als ein bestimmter Zeitstempel sind, wenn Sie möchten.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-204">QR code history is saved at the system level in the driver session, but you can configure your app to ignore QR codes older than a specific timestamp if you want.</span></span> <span data-ttu-id="5ef1e-205">Derzeit unterstützt die API das Löschen von QR-Code Verläufen, da mehrere Apps möglicherweise an den Daten interessiert sind.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-205">Currently the API does support clearing QR code history, as multiple apps might be interested in the data.</span></span>

<span data-ttu-id="5ef1e-206">**Die Plug-Ins für RS5 und zukünftige Versionen können nicht komprimiert werden** . RS5 Version des Plug-ins funktioniert nur für RS5 und kann für zukünftige Versionen nicht verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-206">**The plugins for RS5 and future versions are not compatable** RS5 version of the plugin only works for RS5 and will not work for future versions.</span></span> <span data-ttu-id="5ef1e-207">Das expermentelle Plug-in wird durch das echte Plug-in ersetzt und sollte in zukünftigen Versionen von Windows verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5ef1e-207">The expermental plugin will be replaced with the real plugin and should be the one that we can use in future versions of the windows.</span></span>
