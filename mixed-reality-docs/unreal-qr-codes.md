---
title: QR-Codes in Unreal
description: Leitfaden zur Verwendung von QR-Codes in Unreal
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, QR-Codes
ms.openlocfilehash: a53fad14ab76136f1da419379dd39eca3a29701a
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376102"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="607d2-104">QR-Codes in Unreal</span><span class="sxs-lookup"><span data-stu-id="607d2-104">QR codes in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="607d2-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="607d2-105">Overview</span></span>

<span data-ttu-id="607d2-106">HoloLens 2 kann QR-Codes in der Außenwelt mithilfe der Webcam sehen und gibt sie mithilfe eines Koordinatensystems an jeder Position von Codes in der Realwelt als Hologramme wieder.</span><span class="sxs-lookup"><span data-stu-id="607d2-106">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms using a coordinate system at each code's real-world position.</span></span>  <span data-ttu-id="607d2-107">Über einzelne QR-Codes hinaus kann HoloLens 2 Hologramme außerdem an der gleichen Position auf mehreren Geräten rendern, um eine gemeinsame Erfahrung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="607d2-107">In addition to single QR codes, HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="607d2-108">Achten Sie darauf, die bewährten Methoden für das Hinzufügen von QR-Codes zu Ihren Anwendungen zu befolgen:</span><span class="sxs-lookup"><span data-stu-id="607d2-108">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="607d2-109">Ruhezonen</span><span class="sxs-lookup"><span data-stu-id="607d2-109">Quiet zones</span></span>
- <span data-ttu-id="607d2-110">Beleuchtung und Hintergrund</span><span class="sxs-lookup"><span data-stu-id="607d2-110">Lighting and backdrop</span></span>
- <span data-ttu-id="607d2-111">Größe, Abstand und Winkelposition</span><span class="sxs-lookup"><span data-stu-id="607d2-111">Size, distance, and angular position</span></span>

<span data-ttu-id="607d2-112">Achten Sie besonders auf [Umgebungsaspekte](environment-considerations-for-hololens.md), wenn in Ihrer App QR-Codes platziert werden.</span><span class="sxs-lookup"><span data-stu-id="607d2-112">Pay special attention to the [environment considerations](environment-considerations-for-hololens.md) when QR codes are being placed in your app.</span></span> <span data-ttu-id="607d2-113">Weitere Informationen zu jedem dieser Themen und Anweisungen zum Herunterladen des erforderlichen NuGet-Pakets finden Sie im Dokument zum [Nachverfolgen von QR-Codes](qr-code-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="607d2-113">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](qr-code-tracking.md) document.</span></span> 

## <a name="enabling-qr-detection"></a><span data-ttu-id="607d2-114">Aktivieren der QR-Erkennung</span><span class="sxs-lookup"><span data-stu-id="607d2-114">Enabling QR detection</span></span>
<span data-ttu-id="607d2-115">Da HoloLens 2 die Webcam verwenden muss, um QR-Codes zu sehen, müssen Sie diese in den Projekteinstellungen aktivieren:</span><span class="sxs-lookup"><span data-stu-id="607d2-115">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="607d2-116">Öffnen Sie **Edit > Project Settings** (Bearbeiten > Projekteinstellungen), scrollen Sie zum Abschnitt **Platforms** (Plattformen), und klicken Sie auf **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="607d2-116">Open **Edit > Project Settings**, scroll to the **Platforms** section and click **HoloLens**.</span></span>
    + <span data-ttu-id="607d2-117">Klappen Sie den Abschnitt **Capabilities** (Funktionen) auf, und aktivieren Sie **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="607d2-117">Expand the **Capabilities** section and check **Webcam**.</span></span>  

<span data-ttu-id="607d2-118">Ferner müssen Sie die Nachverfolgung von QR-Codes abonnieren, indem Sie [ein ARSessionConfig-Objekt hinzufügen](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="607d2-118">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

<span data-ttu-id="607d2-119">Unmittelbar vor der Verwendung sollten Sie die Nachverfolgung manuell durch Aufrufen von `UHoloLensARFunctionLibrary::StartQRCodeCapture()` aktivieren.</span><span class="sxs-lookup"><span data-stu-id="607d2-119">Right before the usage, you should manually enable the tracking by calling `UHoloLensARFunctionLibrary::StartQRCodeCapture()`.</span></span> <span data-ttu-id="607d2-120">Nachdem Sie die QR-Codenachverfolgung beendet haben, sollten Sie sie mittels `UHoloLensARFunctionLibrary::StopCameraCapture()` deaktivieren, um die Geräteressourcen zu sparen.</span><span class="sxs-lookup"><span data-stu-id="607d2-120">After ending the QR code tracking, you should disable it by `UHoloLensARFunctionLibrary::StopCameraCapture()` to save the device resources.</span></span> 

## <a name="setting-up-a-tracked-image"></a><span data-ttu-id="607d2-121">Einrichten eines nachverfolgten Bilds</span><span class="sxs-lookup"><span data-stu-id="607d2-121">Setting up a tracked image</span></span>

<span data-ttu-id="607d2-122">QR-Codes werden über das AR-Geometrienachverfolgungssystem von Unreal als nachverfolgtes Bild bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="607d2-122">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="607d2-123">Damit dies funktioniert, müssen Sie Folgendes ausführen:</span><span class="sxs-lookup"><span data-stu-id="607d2-123">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="607d2-124">Erstellen einer Blaupause und Hinzufügen einer **ARTrackableNotify**-Komponente.</span><span class="sxs-lookup"><span data-stu-id="607d2-124">Create a Blueprint and add an **ARTrackableNotify** component.</span></span>

![QR: In AR nachverfolgbare Benachrichtigung](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="607d2-126">Wählen Sie **ARTrackableNotify** aus, und klappen Sie im Bereich **Details** den Abschnitt **Events** (Ereignisse) auf.</span><span class="sxs-lookup"><span data-stu-id="607d2-126">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel.</span></span> 

![QR: Ereignisse](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="607d2-128">Klicken Sie neben **On Add Tracked Geometry** (Beim Hinzufügen von nachverfolgter Geometrie) auf **+** , um dem Ereignisdiagramm den Knoten hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="607d2-128">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="607d2-129">Die vollständige Liste der Ereignisse finden Sie in der Komponenten-API [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="607d2-129">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

![QR: Renderbeispiel](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a><span data-ttu-id="607d2-131">Verwenden eines nachverfolgten Bilds</span><span class="sxs-lookup"><span data-stu-id="607d2-131">Using a tracked image</span></span>
<span data-ttu-id="607d2-132">Das Ereignisdiagramm in der folgenden Abbildung zeigt, wie das **OnUpdateTrackedImage**-Ereignis dazu verwendet wird, einen Punkt in der Mitte eines QR-Codes zu rendern und dessen Daten auszugeben.</span><span class="sxs-lookup"><span data-stu-id="607d2-132">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span> 

![QR: Renderbeispiel](images/unreal-qr-render.PNG)

<span data-ttu-id="607d2-134">Das geschieht bei diesem Vorgang:</span><span class="sxs-lookup"><span data-stu-id="607d2-134">Here's what's going on:</span></span>
1. <span data-ttu-id="607d2-135">Zunächst wird das nachverfolgte Bild in einen **ARTrackedQRCode** umgewandelt, um zu prüfen, ob es sich bei dem aktuellen aktualisierten Bild um einen QR-Code handelt.</span><span class="sxs-lookup"><span data-stu-id="607d2-135">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="607d2-136">Die codierten Daten werden aus der **QRCode**-Variable abgerufen.</span><span class="sxs-lookup"><span data-stu-id="607d2-136">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="607d2-137">Sie können den oberen linken Punkt des QR-Codes aus der Position von **GetLocalToWorldTransform** und seine Abmessungen mit **GetEstimateSize** abrufen.</span><span class="sxs-lookup"><span data-stu-id="607d2-137">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span> 

<span data-ttu-id="607d2-138">Ferner können Sie [das Koordinatensystem für einen QR-Code in Code abrufen](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code).</span><span class="sxs-lookup"><span data-stu-id="607d2-138">You can also [get the coordinate system for a QR code](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="607d2-139">Ermitteln der eindeutigen ID</span><span class="sxs-lookup"><span data-stu-id="607d2-139">Finding the unique ID</span></span>
<span data-ttu-id="607d2-140">Jeder QR-Code weist eine eindeutige GUID-ID auf, die Sie auf diese Weise herausfinden können:</span><span class="sxs-lookup"><span data-stu-id="607d2-140">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="607d2-141">Ziehen und Ablegen des **As ARTracked QRCode**-Stifts und Suchen nach **Get Unique ID** (Eindeutige ID abrufen).</span><span class="sxs-lookup"><span data-stu-id="607d2-141">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![QR: GUID](images/unreal-qr-guid.PNG)

<span data-ttu-id="607d2-143">Mit QR-Codes passiert eine Menge hinter den Kulissen, daher ist diese Erörterung nicht abschließend.</span><span class="sxs-lookup"><span data-stu-id="607d2-143">There's a lot going on behind the scenes with QR codes, so this isn't the end of the road.</span></span> <span data-ttu-id="607d2-144">Folgen Sie unbedingt den folgenden Links, um mehr über die inneren Vorgänge zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="607d2-144">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="see-also"></a><span data-ttu-id="607d2-145">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="607d2-145">See also</span></span>
* [<span data-ttu-id="607d2-146">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="607d2-146">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="607d2-147">Hologramme</span><span class="sxs-lookup"><span data-stu-id="607d2-147">Holograms</span></span>](hologram.md)
* [<span data-ttu-id="607d2-148">Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="607d2-148">Coordinate systems</span></span>](coordinate-systems.md)
