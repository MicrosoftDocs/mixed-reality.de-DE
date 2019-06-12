---
title: HoloLens Research-Modus
description: Research-Modus in HoloLens verwenden, kann eine Anwendung Key Gerät Sensor Streams (Tiefe, Umgebung, die nachverfolgung und IR-Reflexionsvermögen) zugreifen.
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: Research-Modus, cv, rs4, maschinelles sehen, Forschung, HoloLens
ms.openlocfilehash: e9a7683f8d582b459185066e74655e8f2b236db4
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829931"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="acebb-104">HoloLens Research-Modus</span><span class="sxs-lookup"><span data-stu-id="acebb-104">HoloLens Research mode</span></span>

> [!NOTE]
> <span data-ttu-id="acebb-105">Dieses Feature wurde hinzugefügt, als Teil der [Windows 10 April 2018 Update](release-notes-april-2018.md) für HoloLens, und ist in früheren Versionen nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="acebb-105">This feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

<span data-ttu-id="acebb-106">Research-Modus ist eine neue Funktion von HoloLens, die Anwendung den Zugriff auf die wichtigsten Sensoren auf dem Gerät bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="acebb-106">Research mode is a new capability of HoloLens that provides application access to the key sensors on the device.</span></span> <span data-ttu-id="acebb-107">Dazu gehören:</span><span class="sxs-lookup"><span data-stu-id="acebb-107">These include:</span></span>
- <span data-ttu-id="acebb-108">Die vier Umgebung, die nachverfolgung von Kameras, die vom System verwendet wird, zum Erstellen der Zuordnung und Head überwachen.</span><span class="sxs-lookup"><span data-stu-id="acebb-108">The four environment tracking cameras used by the system for map building and head tracking.</span></span>
- <span data-ttu-id="acebb-109">Zwei Versionen der Tiefe Kameradaten – eine für hoher Frequenz (30 FPS) in der Nähe-Depth-Erkennung, häufig verwendet, Nachverfolgen von hand und die andere für die untere Frequenz (1 f/s) weit-Depth ermitteln, an, die derzeit von räumliche Zuordnung verwendet,</span><span class="sxs-lookup"><span data-stu-id="acebb-109">Two versions of the depth camera data – one for high-frequency (30 FPS) near-depth sensing, commonly used in hand tracking, and the other for lower-frequency (1 FPS) far-depth sensing, currently used by Spatial Mapping,</span></span>
- <span data-ttu-id="acebb-110">Zwei Versionen einer IR-Reflexionsvermögen-Stream, der durch die HoloLens verwendet werden, um Tiefe, aber die wertvollen selbständige zu berechnen, wie diese Images aus dem HoloLens beleuchtete und angemessen Umgebungslicht betroffen sind.</span><span class="sxs-lookup"><span data-stu-id="acebb-110">Two versions of an IR-reflectivity stream, used by the HoloLens to compute depth, but valuable in its own right as these images are illuminated from the HoloLens and reasonably unaffected by ambient light.</span></span>

<span data-ttu-id="acebb-111">![Research-Modus-app-screenshot](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="acebb-111">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="acebb-112">*Einer mixed Reality-Erfassung einer testanwendung, in dem die acht Sensor-Datenströme, die im Modus für Research verfügbar angezeigt.*</span><span class="sxs-lookup"><span data-stu-id="acebb-112">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

## <a name="device-support"></a><span data-ttu-id="acebb-113">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="acebb-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="acebb-114"><strong>Funktion</strong></span><span class="sxs-lookup"><span data-stu-id="acebb-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="acebb-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="acebb-115"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="acebb-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="acebb-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="acebb-117">Research-Modus</span><span class="sxs-lookup"><span data-stu-id="acebb-117">Research mode</span></span></td>
        <td><span data-ttu-id="acebb-118">✔️</span><span class="sxs-lookup"><span data-stu-id="acebb-118">✔️</span></span></td>
        <td><span data-ttu-id="acebb-119">❌</span><span class="sxs-lookup"><span data-stu-id="acebb-119">❌</span></span></td>
    </tr>
</table>

## <a name="before-using-research-mode"></a><span data-ttu-id="acebb-120">Vor der Verwendung von Research-Modus</span><span class="sxs-lookup"><span data-stu-id="acebb-120">Before using Research mode</span></span>

<span data-ttu-id="acebb-121">Research-Modus ist auch mit dem Namen: Es ist vorgesehen, academic und gewerbeprozessen Forschern, testen neue Ideen in die Felder der maschinelles sehen und Robotik.</span><span class="sxs-lookup"><span data-stu-id="acebb-121">Research mode is well named: it is intended for academic and industrial researchers trying out new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="acebb-122">Research-Modus ist nicht für Anwendungen vorgesehen, die in einem Unternehmen bereitgestellt oder in der Microsoft Store zur Verfügung gestellt werden.</span><span class="sxs-lookup"><span data-stu-id="acebb-122">Research mode is not intended for applications that will be deployed across an enterprise or made available in the Microsoft Store.</span></span> <span data-ttu-id="acebb-123">Der Grund dafür ist, dass Research Modus die Sicherheit Ihres Geräts verringert und wesentlich mehr Akkuleistung als Normalbetrieb belegt.</span><span class="sxs-lookup"><span data-stu-id="acebb-123">The reason for this is that Research mode lowers the security of your device and consumes significantly more battery power than normal operation.</span></span> <span data-ttu-id="acebb-124">Microsoft ist nicht verpflichtet sich somit, diesen Modus für alle zukünftigen Geräte unterstützen.</span><span class="sxs-lookup"><span data-stu-id="acebb-124">Microsoft is not committing to supporting this mode on any future devices.</span></span> <span data-ttu-id="acebb-125">Daher empfehlen wir, dass Sie zum Entwickeln und testen neue Ideen verwenden; Allerdings werden Sie nicht häufig Anwendungen bereitstellen, die Research-Modus verwenden oder alle Assurance, die sie weiterhin funktionieren, auf zukünftige Hardware.</span><span class="sxs-lookup"><span data-stu-id="acebb-125">Thus, we recommend you use it to develop and test new ideas; however, you will not be able to widely deploy applications that use Research mode or have any assurance that it will continue to work on future hardware.</span></span>

## <a name="enabling-research-mode"></a><span data-ttu-id="acebb-126">Research-Modus aktivieren</span><span class="sxs-lookup"><span data-stu-id="acebb-126">Enabling Research mode</span></span>

<span data-ttu-id="acebb-127">Research-Modus ist eine untergeordnete des Entwicklermodus.</span><span class="sxs-lookup"><span data-stu-id="acebb-127">Research mode is a sub-mode of developer mode.</span></span> <span data-ttu-id="acebb-128">Sie müssen zunächst Entwicklermodus in der Einstellungs-app zu aktivieren (**Einstellungen > Update und Sicherheit > für Entwickler**):</span><span class="sxs-lookup"><span data-stu-id="acebb-128">You first need to enable developer mode in the Settings app (**Settings > Update & Security > For developers**):</span></span>

1. <span data-ttu-id="acebb-129">Legen Sie "Verwenden der Funktionen für Entwickler" auf **auf**</span><span class="sxs-lookup"><span data-stu-id="acebb-129">Set "Use developer features" to **On**</span></span>
2. <span data-ttu-id="acebb-130">Legen Sie auf "Enable-Geräteportal" **auf**</span><span class="sxs-lookup"><span data-stu-id="acebb-130">Set "Enable Device Portal" to **On**</span></span>

<span data-ttu-id="acebb-131">Klicken Sie dann über einen Webbrowser, der mit dem gleichen Wi-Fi-Netzwerk als Ihre HoloLens, verbunden ist, navigieren Sie auf die IP-Adresse Ihrer HoloLens (abgerufenes **Einstellungen > Netzwerk und Internet > Wi-Fi > Hardwareeigenschaften**).</span><span class="sxs-lookup"><span data-stu-id="acebb-131">Then using a web browser that is connected to the same Wi-Fi network as your HoloLens, navigate to the IP address of your HoloLens (obtained through **Settings > Network & Internet > Wi-Fi > Hardware properties**).</span></span> <span data-ttu-id="acebb-132">Dies ist die [Device Portal](using-the-windows-device-portal.md), und eine Seite "Research-Modus" finden Sie im Abschnitt "System" des Portals:</span><span class="sxs-lookup"><span data-stu-id="acebb-132">This is the [Device Portal](using-the-windows-device-portal.md), and you will find a "Research mode" page in the "System" section of the portal:</span></span>

<span data-ttu-id="acebb-133">![Überprüfen Sie die Registerkarte "Standortmodus" des Portals für HoloLens-Gerät](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="acebb-133">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="acebb-134">*Research-Modus im Portal HoloLens-Gerät*</span><span class="sxs-lookup"><span data-stu-id="acebb-134">*Research mode in the HoloLens Device Portal*</span></span>

<span data-ttu-id="acebb-135">Nach der Auswahl **zulassen des Zugriffs auf Sensor Streams**, Sie benötigen, HoloLens neu zu starten.</span><span class="sxs-lookup"><span data-stu-id="acebb-135">After selecting **Allow access to sensor streams**, you will need to reboot HoloLens.</span></span> <span data-ttu-id="acebb-136">Dies ist im Portal klicken Sie unter "Power" am oberen Rand der Seite Gerät möglich.</span><span class="sxs-lookup"><span data-stu-id="acebb-136">You can do this from the Device Portal, under the "Power" menu item at the top of the page.</span></span>

<span data-ttu-id="acebb-137">Nachdem Ihr Gerät neu gestartet wurde, sollte Anwendungen, die über das Device Portal geladen wurden Research Modus Streams zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="acebb-137">Once your device has rebooted, applications that have been loaded through Device Portal should be able to access Research mode streams.</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="acebb-138">Mithilfe von Sensordaten in Ihren apps</span><span class="sxs-lookup"><span data-stu-id="acebb-138">Using sensor data in your apps</span></span>

<span data-ttu-id="acebb-139">Anwendungen können Daten von triebwerksensoren Stream zugreifen, indem öffnen [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) Streams auf genau die gleiche Weise Zugriff auf den Foto/Video-Kamera-Datenstrom.</span><span class="sxs-lookup"><span data-stu-id="acebb-139">Applications can access sensor stream data by opening [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) streams in exactly the same way they access the photo/video camera stream.</span></span> 

<span data-ttu-id="acebb-140">Außerdem stehen alle APIs, die für die Entwicklung für HoloLens arbeiten im Research-Modus zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="acebb-140">All APIs that work for HoloLens development are also available when in Research mode.</span></span> <span data-ttu-id="acebb-141">Insbesondere kann die Anwendung wissen genau, in dem HoloLens im 6DoF Raum zur Erfassungszeit jeden Sensor-Frame ist.</span><span class="sxs-lookup"><span data-stu-id="acebb-141">In particular, the application can know precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="acebb-142">Beispielanwendungen, die zeigt, wie Sie die verschiedenen Research Modus Streams zugreifen, wie Sie die systeminterne Funktionen und Extrinsics verwenden und das Aufzeichnen von Streams finden Sie in der [HoloLensForCV-GitHub-Repository](https://github.com/Microsoft/HoloLensForCV).</span><span class="sxs-lookup"><span data-stu-id="acebb-142">Sample applications showing how you access the various Research mode streams, how to use the intrinsics and extrinsics, and how to record streams are available in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV).</span></span>

## <a name="known-issues"></a><span data-ttu-id="acebb-143">Bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="acebb-143">Known issues</span></span>

<span data-ttu-id="acebb-144">Finden Sie unter den [problemverfolgung](https://github.com/Microsoft/HololensForCV/issues) im HoloLensForCV-Repository.</span><span class="sxs-lookup"><span data-stu-id="acebb-144">See the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="acebb-145">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="acebb-145">See also</span></span>

* [<span data-ttu-id="acebb-146">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="acebb-146">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="acebb-147">HoloLensForCV-GitHub-Repository</span><span class="sxs-lookup"><span data-stu-id="acebb-147">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="acebb-148">Verwenden des Windows-Geräteportals</span><span class="sxs-lookup"><span data-stu-id="acebb-148">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
