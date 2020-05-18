---
title: QR-Codes in Unreal
description: Leitfaden zur Verwendung von QR-Codes in Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, QR-Codes
ms.openlocfilehash: 67a3a8092ab908cba6768e92ed6a0e7bd2737275
ms.sourcegitcommit: 5b802078090700e06630c8fc665fedeaa0a16eb7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83342658"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="f0b00-104">QR-Codes in Unreal</span><span class="sxs-lookup"><span data-stu-id="f0b00-104">QR codes in Unreal</span></span>

<span data-ttu-id="f0b00-105">HoloLens kann QR-Codes im Weltbereich erkennen, um Hologramme an bekannten Positionen in der realen Welt zu rendern.</span><span class="sxs-lookup"><span data-stu-id="f0b00-105">HoloLens can locate QR codes in world space to render holograms at known positions in the real world.</span></span>  <span data-ttu-id="f0b00-106">Dies kann auch verwendet werden, um auf mehreren Geräten Hologramme an der gleichen Position zu rendern und so ein gemeinsames Erlebnis zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="f0b00-106">This can also be used to render holograms on multiple devices in the same location to create a shared experience.</span></span> 

<span data-ttu-id="f0b00-107">Wenn Sie die QR-Erkennung für HoloLens aktivieren möchten, vergewissern Sie sich im Unreal-Editor unter „Project Settings“ (Projekteinstellungen) > „Platform“ (Plattform) > „HoloLens“ > „Capabilities“ (Funktionen), dass das Kontrollkästchen für die Webcamfunktion aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="f0b00-107">To enable QR detection on HoloLens, ensure the “Webcam” capability is checked in the Unreal editor under Project Settings > Platform > HoloLens > Capabilities.</span></span>  

<span data-ttu-id="f0b00-108">Entscheiden Sie sich für die Verwendung von QR-Code-Nachverfolgung in Unreal, indem Sie eine ARSession mit der Funktion StartARSession starten.</span><span class="sxs-lookup"><span data-stu-id="f0b00-108">Opt into using QR code tracking in Unreal by starting an ARSession with the StartARSession function.</span></span> 

<span data-ttu-id="f0b00-109">QR-Codes werden über das AR-Geometrienachverfolgungssystem von Unreal als nachverfolgtes Bild bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="f0b00-109">QR Codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span>  <span data-ttu-id="f0b00-110">Für dessen Verwendung muss einem Blaupausenakteur eine in AR nachverfolgbare Benachrichtigungskomponente hinzugefügt werden:</span><span class="sxs-lookup"><span data-stu-id="f0b00-110">To use this, add an AR Trackable Notify component to a Blueprint actor:</span></span> 

![QR: In AR nachverfolgbare Benachrichtigung](images/unreal-spatialmapping-artrackablenotify.PNG)

<span data-ttu-id="f0b00-112">Navigieren Sie dann zu den Details der Komponente, und klicken Sie auf die grüne Plusschaltfläche (+) für die zu überwachenden Ereignisse.</span><span class="sxs-lookup"><span data-stu-id="f0b00-112">Then go to the component’s details and click on the green “+” button on the events to monitor.</span></span>  

![QR: Ereignisse](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="f0b00-114">Hier wurde „OnUpdateTrackedImage“ abonniert, um einen Punkt in der Mitte eines QR-Codes zu rendern und die codierten Daten des QR-Codes auszugeben.</span><span class="sxs-lookup"><span data-stu-id="f0b00-114">Here, we have subscribed to OnUpdateTrackedImage to render a point in the center of a QR Code and print the QR code’s encoded data.</span></span> 

![QR: Renderbeispiel](images/unreal-qr-render.PNG)

<span data-ttu-id="f0b00-116">Wandeln Sie das nachverfolgte Bild zuerst in „ARTrackedQRCode“ um, um sich zu vergewissern, dass es sich bei dem derzeitigen aktualisierten Bild um einen QR-Code handelt.</span><span class="sxs-lookup"><span data-stu-id="f0b00-116">First cast the tracked image to an ARTrackedQRCode to verify that the current updated image is a QR code.</span></span>  <span data-ttu-id="f0b00-117">Anschließend können die codierten Daten mithilfe der Variablen „QRCode“ abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="f0b00-117">Then the encoded data can be retrieved with the QRCode variable.</span></span>  <span data-ttu-id="f0b00-118">Die linke obere Ecke des QR-Codes kann auf der Grundlage der Position von „GetLocalToWorldTransform“ abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="f0b00-118">The top-left of the QR code can be retrieved from the location of GetLocalToWorldTransform.</span></span>  <span data-ttu-id="f0b00-119">Die Dimensionen können mithilfe von „GetEstimateSize“ abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="f0b00-119">The dimensions can be retrieved with GetEstimateSize.</span></span> 

<span data-ttu-id="f0b00-120">Jeder QR-Code verfügt auch über eine eindeutige GUID:</span><span class="sxs-lookup"><span data-stu-id="f0b00-120">Every QR code also has a unique guid ID:</span></span> 

![QR: GUID](images/unreal-qr-guid.PNG)

## <a name="see-also"></a><span data-ttu-id="f0b00-122">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f0b00-122">See also</span></span>
* [<span data-ttu-id="f0b00-123">Nachverfolgen von QR-Codes</span><span class="sxs-lookup"><span data-stu-id="f0b00-123">QR code tracking</span></span>](qr-code-tracking.md)
