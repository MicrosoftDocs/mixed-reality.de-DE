---
title: QR-Codes in Unreal
description: Leitfaden zur Verwendung von QR-Codes in Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, QR-Codes
ms.openlocfilehash: 90a51227ae455389168fb3262e83f34b64a7bfb5
ms.sourcegitcommit: ee7f04148d3608b0284c59e33b394a67f0934255
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84428756"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="bd4a8-104">QR-Codes in Unreal</span><span class="sxs-lookup"><span data-stu-id="bd4a8-104">QR codes in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="bd4a8-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="bd4a8-105">Overview</span></span>

<span data-ttu-id="bd4a8-106">HoloLens 2 kann QR-Codes in der Außenwelt mithilfe der Webcam sehen und gibt sie mithilfe eines Koordinatensystems an jeder Position von Codes in der Realwelt als Hologramme wieder.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-106">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms using a coordinate system at each code's real-world position.</span></span>  <span data-ttu-id="bd4a8-107">Über einzelne QR-Codes hinaus kann HoloLens 2 Hologramme außerdem an der gleichen Position auf mehreren Geräten rendern, um eine gemeinsame Erfahrung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-107">In addition to single QR codes, HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="bd4a8-108">Achten Sie darauf, die bewährten Methoden für das Hinzufügen von QR-Codes zu Ihren Anwendungen zu befolgen:</span><span class="sxs-lookup"><span data-stu-id="bd4a8-108">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="bd4a8-109">Ruhezonen</span><span class="sxs-lookup"><span data-stu-id="bd4a8-109">Quiet zones</span></span>
- <span data-ttu-id="bd4a8-110">Beleuchtung und Hintergrund</span><span class="sxs-lookup"><span data-stu-id="bd4a8-110">Lighting and backdrop</span></span>
- <span data-ttu-id="bd4a8-111">Größe, Abstand und Winkelposition</span><span class="sxs-lookup"><span data-stu-id="bd4a8-111">Size, distance, and angular position</span></span>

<span data-ttu-id="bd4a8-112">Achten Sie besonders auf [Umgebungsaspekte](environment-considerations-for-hololens.md), wenn in Ihrer App QR-Codes platziert werden.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-112">Pay special attention to the [environment considerations](environment-considerations-for-hololens.md) when QR codes are being placed in your app.</span></span> <span data-ttu-id="bd4a8-113">Weitere Informationen zu jedem dieser Themen und Anweisungen zum Herunterladen des erforderlichen NuGet-Pakets finden Sie im Dokument zum [Nachverfolgen von QR-Codes](qr-code-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="bd4a8-113">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](qr-code-tracking.md) document.</span></span> 

## <a name="enabling-qr-detection"></a><span data-ttu-id="bd4a8-114">Aktivieren der QR-Erkennung</span><span class="sxs-lookup"><span data-stu-id="bd4a8-114">Enabling QR detection</span></span>
<span data-ttu-id="bd4a8-115">Da HoloLens 2 die Webcam verwenden muss, um QR-Codes zu sehen, müssen Sie diese in den Projekteinstellungen aktivieren:</span><span class="sxs-lookup"><span data-stu-id="bd4a8-115">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="bd4a8-116">Öffnen Sie **Edit > Project Settings** (Bearbeiten > Projekteinstellungen), scrollen Sie zum Abschnitt **Platforms** (Plattformen), und klicken Sie auf **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-116">Open **Edit > Project Settings**, scroll to the **Platforms** section and click **HoloLens**.</span></span>
    + <span data-ttu-id="bd4a8-117">Klappen Sie den Abschnitt **Capabilities** (Funktionen) auf, und aktivieren Sie **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-117">Expand the **Capabilities** section and check **Webcam**.</span></span>  

<span data-ttu-id="bd4a8-118">Ferner müssen Sie die Nachverfolgung von QR-Codes abonnieren, indem Sie [ein ARSessionConfig-Objekt hinzufügen](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="bd4a8-118">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

## <a name="setting-up-a-tracked-image"></a><span data-ttu-id="bd4a8-119">Einrichten eines nachverfolgten Bilds</span><span class="sxs-lookup"><span data-stu-id="bd4a8-119">Setting up a tracked image</span></span>

<span data-ttu-id="bd4a8-120">QR-Codes werden über das AR-Geometrienachverfolgungssystem von Unreal als nachverfolgtes Bild bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-120">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="bd4a8-121">Damit dies funktioniert, müssen Sie Folgendes ausführen:</span><span class="sxs-lookup"><span data-stu-id="bd4a8-121">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="bd4a8-122">Erstellen einer Blaupause und Hinzufügen einer **ARTrackableNotify**-Komponente.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-122">Create a Blueprint and add an **ARTrackableNotify** component.</span></span>

![QR: In AR nachverfolgbare Benachrichtigung](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="bd4a8-124">Wählen Sie **ARTrackableNotify** aus, und klappen Sie im Bereich **Details** den Abschnitt **Events** (Ereignisse) auf.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-124">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel.</span></span> 

![QR: Ereignisse](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="bd4a8-126">Klicken Sie neben **On Add Tracked Geometry** (Beim Hinzufügen von nachverfolgter Geometrie) auf **+** , um dem Ereignisdiagramm den Knoten hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-126">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="bd4a8-127">Die vollständige Liste der Ereignisse finden Sie in der Komponenten-API [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="bd4a8-127">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

![QR: Renderbeispiel](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a><span data-ttu-id="bd4a8-129">Verwenden eines nachverfolgten Bilds</span><span class="sxs-lookup"><span data-stu-id="bd4a8-129">Using a tracked image</span></span>
<span data-ttu-id="bd4a8-130">Das Ereignisdiagramm in der folgenden Abbildung zeigt, wie das **OnUpdateTrackedImage**-Ereignis dazu verwendet wird, einen Punkt in der Mitte eines QR-Codes zu rendern und dessen Daten auszugeben.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-130">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span> 

![QR: Renderbeispiel](images/unreal-qr-render.PNG)

<span data-ttu-id="bd4a8-132">Das geschieht dabei:</span><span class="sxs-lookup"><span data-stu-id="bd4a8-132">Here's waht's going on:</span></span>
1. <span data-ttu-id="bd4a8-133">Zunächst wird das nachverfolgte Bild in einen **ARTrackedQRCode** umgewandelt, um zu prüfen, ob es sich bei dem aktuellen aktualisierten Bild um einen QR-Code handelt.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-133">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="bd4a8-134">Die codierten Daten werden aus der **QRCode**-Variable abgerufen.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-134">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="bd4a8-135">Sie können den oberen linken Punkt des QR-Codes aus der Position von **GetLocalToWorldTransform** und seine Abmessungen mit **GetEstimateSize** abrufen.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-135">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span> 

<span data-ttu-id="bd4a8-136">Ferner können Sie [das Koordinatensystem für einen QR-Code in Code abrufen](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code).</span><span class="sxs-lookup"><span data-stu-id="bd4a8-136">You can also [get the coordinate system for a QR code](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="bd4a8-137">Ermitteln der eindeutigen ID</span><span class="sxs-lookup"><span data-stu-id="bd4a8-137">Finding the unique ID</span></span>
<span data-ttu-id="bd4a8-138">Jeder QR-Code weist eine eindeutige GUID-ID auf, die Sie auf diese Weise herausfinden können:</span><span class="sxs-lookup"><span data-stu-id="bd4a8-138">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="bd4a8-139">Ziehen und Ablegen des **As ARTracked QRCode**-Stifts und Suchen nach **Get Unique ID** (Eindeutige ID abrufen).</span><span class="sxs-lookup"><span data-stu-id="bd4a8-139">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![QR: GUID](images/unreal-qr-guid.PNG)

<span data-ttu-id="bd4a8-141">Mit QR-Codes passiert eine Menge hinter den Kulissen, daher ist diese Erörterung nicht abschließend.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-141">There's a lot going on behind the scenes with QR codes, so this isn't the end of the road.</span></span> <span data-ttu-id="bd4a8-142">Folgen Sie unbedingt den folgenden Links, um mehr über die inneren Vorgänge zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-142">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="see-also"></a><span data-ttu-id="bd4a8-143">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="bd4a8-143">See also</span></span>
* [<span data-ttu-id="bd4a8-144">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="bd4a8-144">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="bd4a8-145">Hologramme</span><span class="sxs-lookup"><span data-stu-id="bd4a8-145">Holograms</span></span>](hologram.md)
* [<span data-ttu-id="bd4a8-146">Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="bd4a8-146">Coordinate systems</span></span>](coordinate-systems.md)