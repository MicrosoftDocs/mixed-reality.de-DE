---
title: Hololens Research-Modus
description: Mithilfe des Research-Modus auf hololens kann eine Anwendung auf wichtige Geräte Sensordaten Ströme (Tiefe, Umgebungs Überwachung und IR-Reflektivität) zugreifen.
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: Research Mode, CV, RS4, Maschinelles sehen, Forschung, hololens
ms.openlocfilehash: e9a7683f8d582b459185066e74655e8f2b236db4
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829931"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="469f2-104">Hololens Research-Modus</span><span class="sxs-lookup"><span data-stu-id="469f2-104">HoloLens Research mode</span></span>

> [!NOTE]
> <span data-ttu-id="469f2-105">Diese Funktion wurde als Teil des [Windows 10-Updates vom April 2018](release-notes-april-2018.md) für hololens hinzugefügt und ist in früheren Versionen nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="469f2-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

<span data-ttu-id="469f2-106">Der Forschungs Modus ist eine neue Funktion von hololens, die Anwendungs Zugriff auf die Schlüssel Sensoren auf dem Gerät bietet.</span><span class="sxs-lookup"><span data-stu-id="469f2-106">Research mode is a new capability of HoloLens that provides application access to the key sensors on the device.</span></span> <span data-ttu-id="469f2-107">Dazu gehören:</span><span class="sxs-lookup"><span data-stu-id="469f2-107">These include:</span></span>
- <span data-ttu-id="469f2-108">Die vier Umgebungs Überwachungskameras, die vom System für das Zuordnen von Zuordnungen und das Head-Tracking verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="469f2-108">The four environment tracking cameras used by the system for map building and head tracking.</span></span>
- <span data-ttu-id="469f2-109">Zwei Versionen der tiefenkamera Daten – eine für die nahe greifende Erfassung mit hoher Frequenz (30 fps), häufig in der Hand Nachverfolgung verwendet, und die andere für die untere Frequenz (1 fps), bei der es sich um eine weitgehende Erfassung handelt, die zurzeit von der räumlichen Zuordnung verwendet wird,</span><span class="sxs-lookup"><span data-stu-id="469f2-109">Two versions of the depth camera data – one for high-frequency (30 FPS) near-depth sensing, commonly used in hand tracking, and the other for lower-frequency (1 FPS) far-depth sensing, currently used by Spatial Mapping,</span></span>
- <span data-ttu-id="469f2-110">Zwei Versionen eines IR-Reflektivität-Streams, die von den hololens zur computetiefe verwendet werden, aber von der eigenen richtigen Bedeutung sind, da diese Bilder aus den hololens beleuchtet werden und von Umgebungslicht nicht beeinträchtigt werden.</span><span class="sxs-lookup"><span data-stu-id="469f2-110">Two versions of an IR-reflectivity stream, used by the HoloLens to compute depth, but valuable in its own right as these images are illuminated from the HoloLens and reasonably unaffected by ambient light.</span></span>

<span data-ttu-id="469f2-111">![Screenshot der Recherche Modus-App](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="469f2-111">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="469f2-112">*Eine gemischte Realität-Erfassung einer Testanwendung, die die acht im Research-Modus verfügbaren Sensordaten Ströme anzeigt*</span><span class="sxs-lookup"><span data-stu-id="469f2-112">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

## <a name="device-support"></a><span data-ttu-id="469f2-113">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="469f2-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="469f2-114"><strong>Funktion</strong></span><span class="sxs-lookup"><span data-stu-id="469f2-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="469f2-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="469f2-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="469f2-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="469f2-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="469f2-117">Forschungs Modus</span><span class="sxs-lookup"><span data-stu-id="469f2-117">Research mode</span></span></td>
        <td><span data-ttu-id="469f2-118">✔️</span><span class="sxs-lookup"><span data-stu-id="469f2-118">✔️</span></span></td>
        <td><span data-ttu-id="469f2-119">❌</span><span class="sxs-lookup"><span data-stu-id="469f2-119">❌</span></span></td>
    </tr>
</table>

## <a name="before-using-research-mode"></a><span data-ttu-id="469f2-120">Vor der Verwendung des Research-Modus</span><span class="sxs-lookup"><span data-stu-id="469f2-120">Before using Research mode</span></span>

<span data-ttu-id="469f2-121">Der Forschungs Modus ist gut benannt: er ist für akademische und Industrieexperten gedacht, die neue Ideen in den Feldern von Maschinelles Sehen und Robotik ausprobieren.</span><span class="sxs-lookup"><span data-stu-id="469f2-121">Research mode is well named: it is intended for academic and industrial researchers trying out new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="469f2-122">Der Forschungs Modus ist nicht für Anwendungen gedacht, die über ein Unternehmen bereitgestellt oder in der Microsoft Store bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="469f2-122">Research mode is not intended for applications that will be deployed across an enterprise or made available in the Microsoft Store.</span></span> <span data-ttu-id="469f2-123">Der Grund hierfür ist, dass der Research-Modus die Sicherheit Ihres Geräts verringert und eine deutlich höhere Akkuleistung als der normale Betrieb beansprucht.</span><span class="sxs-lookup"><span data-stu-id="469f2-123">The reason for this is that Research mode lowers the security of your device and consumes significantly more battery power than normal operation.</span></span> <span data-ttu-id="469f2-124">Microsoft ist nicht verpflichtet, diesen Modus auf zukünftigen Geräten zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="469f2-124">Microsoft is not committing to supporting this mode on any future devices.</span></span> <span data-ttu-id="469f2-125">Daher empfiehlt es sich, diese zum entwickeln und Testen neuer Ideen zu verwenden. Allerdings sind Sie nicht in der Lage, Anwendungen, die den Research-Modus verwenden, umfassend bereitzustellen oder sicherzustellen, dass Sie weiterhin auf zukünftiger Hardware funktionieren.</span><span class="sxs-lookup"><span data-stu-id="469f2-125">Thus, we recommend you use it to develop and test new ideas; however, you will not be able to widely deploy applications that use Research mode or have any assurance that it will continue to work on future hardware.</span></span>

## <a name="enabling-research-mode"></a><span data-ttu-id="469f2-126">Aktivieren des Research-Modus</span><span class="sxs-lookup"><span data-stu-id="469f2-126">Enabling Research mode</span></span>

<span data-ttu-id="469f2-127">Der Forschungs Modus ist ein unter Modus des Entwicklermodus.</span><span class="sxs-lookup"><span data-stu-id="469f2-127">Research mode is a sub-mode of developer mode.</span></span> <span data-ttu-id="469f2-128">Sie müssen zunächst den Entwicklermodus in der App "Einstellungen" aktivieren (**Einstellungen > Update & Sicherheits > für Entwickler**):</span><span class="sxs-lookup"><span data-stu-id="469f2-128">You first need to enable developer mode in the Settings app (**Settings > Update & Security > For developers**):</span></span>

1. <span data-ttu-id="469f2-129">Legen Sie "Entwickler Features verwenden" auf **on** fest.</span><span class="sxs-lookup"><span data-stu-id="469f2-129">Set "Use developer features" to **On**</span></span>
2. <span data-ttu-id="469f2-130">Legen **Sie "** Geräte Portal aktivieren" auf ein fest.</span><span class="sxs-lookup"><span data-stu-id="469f2-130">Set "Enable Device Portal" to **On**</span></span>

<span data-ttu-id="469f2-131">Navigieren Sie dann mithilfe eines Webbrowsers, der mit dem gleichen WLAN verbunden ist wie Ihre hololens, zur IP-Adresse Ihres hololens (über **Einstellungen > Netzwerk & Internet > Wi-Fi-> Hardware Eigenschaften**).</span><span class="sxs-lookup"><span data-stu-id="469f2-131">Then using a web browser that is connected to the same Wi-Fi network as your HoloLens, navigate to the IP address of your HoloLens (obtained through **Settings > Network & Internet > Wi-Fi > Hardware properties**).</span></span> <span data-ttu-id="469f2-132">Dies ist das [Geräte Portal](using-the-windows-device-portal.md), und im Abschnitt "System" des Portals finden Sie eine Seite "Research Mode":</span><span class="sxs-lookup"><span data-stu-id="469f2-132">This is the [Device Portal](using-the-windows-device-portal.md), and you will find a "Research mode" page in the "System" section of the portal:</span></span>

<span data-ttu-id="469f2-133">![Registerkarte "Forschungs Modus" des hololens-Geräte Portals](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="469f2-133">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="469f2-134">*Forschungs Modus im hololens-Geräte Portal*</span><span class="sxs-lookup"><span data-stu-id="469f2-134">*Research mode in the HoloLens Device Portal*</span></span>

<span data-ttu-id="469f2-135">Nachdem Sie **Zugriff auf Sensordaten Ströme zulassen**ausgewählt haben, müssen Sie hololens neu starten.</span><span class="sxs-lookup"><span data-stu-id="469f2-135">After selecting **Allow access to sensor streams**, you will need to reboot HoloLens.</span></span> <span data-ttu-id="469f2-136">Dies können Sie über das Geräte Portal unter dem Menü Element "Power" am oberen Rand der Seite tun.</span><span class="sxs-lookup"><span data-stu-id="469f2-136">You can do this from the Device Portal, under the "Power" menu item at the top of the page.</span></span>

<span data-ttu-id="469f2-137">Nachdem das Gerät neu gestartet wurde, sollten Anwendungen, die über das Geräte Portal geladen wurden, auf Datenströme im Forschungs Modus zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="469f2-137">Once your device has rebooted, applications that have been loaded through Device Portal should be able to access Research mode streams.</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="469f2-138">Verwenden von Sensordaten in ihren apps</span><span class="sxs-lookup"><span data-stu-id="469f2-138">Using sensor data in your apps</span></span>

<span data-ttu-id="469f2-139">Anwendungen können auf Sensordaten Ströme zugreifen, indem Sie [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) Datenströme genau auf die gleiche Weise öffnen, wie Sie auf den Photo/Video-Kamera-Stream zugreifen.</span><span class="sxs-lookup"><span data-stu-id="469f2-139">Applications can access sensor stream data by opening [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) streams in exactly the same way they access the photo/video camera stream.</span></span> 

<span data-ttu-id="469f2-140">Alle APIs, die für die hololens-Entwicklung funktionieren, sind auch im Research-Modus verfügbar.</span><span class="sxs-lookup"><span data-stu-id="469f2-140">All APIs that work for HoloLens development are also available when in Research mode.</span></span> <span data-ttu-id="469f2-141">Insbesondere kann die Anwendung genau wissen, wo sich hololens bei jeder Sensor Frame-Erfassungs Zeit in einem 6DOF-Raum befindet.</span><span class="sxs-lookup"><span data-stu-id="469f2-141">In particular, the application can know precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="469f2-142">Beispielanwendungen, die zeigen, wie Sie auf die verschiedenen Datenstreams im Forschungs Modus zugreifen, wie Sie die systeminternen und extrinsics verwenden und Datenströme aufzeichnen, sind im [GitHub-Repository hololensforcv](https://github.com/Microsoft/HoloLensForCV)verfügbar.</span><span class="sxs-lookup"><span data-stu-id="469f2-142">Sample applications showing how you access the various Research mode streams, how to use the intrinsics and extrinsics, and how to record streams are available in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV).</span></span>

## <a name="known-issues"></a><span data-ttu-id="469f2-143">Bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="469f2-143">Known issues</span></span>

<span data-ttu-id="469f2-144">Weitere Informationen finden Sie im Repository "hololensforcv" unter [Problem](https://github.com/Microsoft/HololensForCV/issues) Verfolgung.</span><span class="sxs-lookup"><span data-stu-id="469f2-144">See the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="469f2-145">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="469f2-145">See also</span></span>

* [<span data-ttu-id="469f2-146">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="469f2-146">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="469f2-147">Hololensforcv GitHub-Repository</span><span class="sxs-lookup"><span data-stu-id="469f2-147">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="469f2-148">Verwenden des Windows-Geräteportals</span><span class="sxs-lookup"><span data-stu-id="469f2-148">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
