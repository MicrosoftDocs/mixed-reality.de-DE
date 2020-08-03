---
title: Hololens Research-Modus
description: Mithilfe des Research-Modus auf hololens kann eine Anwendung auf wichtige Geräte Sensordaten Ströme (Tiefe, Umgebungs Überwachung und IR-Reflektivität) zugreifen.
author: hferrone
ms.author: v-haferr
ms.date: 07/31/2020
ms.topic: article
keywords: Research Mode, CV, RS4, Maschinelles sehen, Forschung, hololens, hololens 2
ms.openlocfilehash: dd49186d1218b6a6a6c9a8d5943159daad3bcefb
ms.sourcegitcommit: 36316e2658d3dfa804d798b9f4fb2f9186052144
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2020
ms.locfileid: "87507694"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="4a190-104">Hololens Research-Modus</span><span class="sxs-lookup"><span data-stu-id="4a190-104">HoloLens Research Mode</span></span>

<span data-ttu-id="4a190-105">Der Forschungs Modus wurde in den ersten hololens der Generation eingeführt, um den Zugriff auf die Schlüssel Sensoren auf dem Gerät zu erhalten, insbesondere für Forschungsanwendungen, die nicht für die Bereitstellung vorgesehen sind.</span><span class="sxs-lookup"><span data-stu-id="4a190-105">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span>  <span data-ttu-id="4a190-106">Der Forschungs Modus für hololens 2 behält die Funktionen von hololens 1 bei und bietet Zugriff auf zusätzliche Streams:</span><span class="sxs-lookup"><span data-stu-id="4a190-106">Research Mode for HoloLens 2 retains the capabilities of HoloLens 1, adding access to additional streams:</span></span>

* <span data-ttu-id="4a190-107">**Sichtbare helle Umgebungs Überwachungskameras** : graue Kameras, die vom System für die Head-Nachverfolgung und die Zuordnungs Bildung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="4a190-107">**Visible Light Environment Tracking Cameras** - Gray-scale cameras used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="4a190-108">**Tiefe Kamera** – wird in zwei Modi betrieben:</span><span class="sxs-lookup"><span data-stu-id="4a190-108">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="4a190-109">Ahat, hohe Häufigkeit (45 fps), die für die Hand Verfolgung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="4a190-109">AHAT, high-frequency (45 FPS) near-depth sensing used for hand tracking.</span></span> <span data-ttu-id="4a190-110">Anders als bei der ersten Version des kurzthrow-Modus gibt ahat eine Pseudo Tiefe mit einem Phasen Umbruch über 1 Meter hinaus.</span><span class="sxs-lookup"><span data-stu-id="4a190-110">Differently from the 1st version short-throw mode, AHAT gives pseudo-depth with phase wrap beyond 1 meter.</span></span> 
    + <span data-ttu-id="4a190-111">Lange throw-, Low-Frequency (1-5 fps)-Erkennung, die von der [räumlichen Zuordnung](spatial-mapping.md) verwendet wird</span><span class="sxs-lookup"><span data-stu-id="4a190-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](spatial-mapping.md)</span></span>

* <span data-ttu-id="4a190-112">**Zwei Versionen des IR-Reflektivität-Streams** : werden von den hololens zum Berechnen der Tiefe verwendet.</span><span class="sxs-lookup"><span data-stu-id="4a190-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="4a190-113">Diese Bilder werden von Infrarot beleuchtet und sind von der Sichtbarkeit sichtbar.</span><span class="sxs-lookup"><span data-stu-id="4a190-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="4a190-114">Wenn Sie ein hololens 2 verwenden, haben Sie auch Zugriff auf die unten aufgeführten zusätzlichen Eingaben:</span><span class="sxs-lookup"><span data-stu-id="4a190-114">If you're using a HoloLens 2 you also have access to the additional inputs below:</span></span>

* <span data-ttu-id="4a190-115">**Beschleunigungsmesser** – wird vom System verwendet, um die lineare Beschleunigung entlang der X-, Y-und Z-Achse und der Schweregrad zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="4a190-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y and Z axes and gravity.</span></span>
* <span data-ttu-id="4a190-116">**Gyro** – wird vom System verwendet, um Drehungen zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="4a190-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="4a190-117">**Magnetometer** – wird vom System zum Schätzen der absoluten Ausrichtung verwendet.</span><span class="sxs-lookup"><span data-stu-id="4a190-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4a190-118">Der Research-Modus befindet sich derzeit in Public Preview.</span><span class="sxs-lookup"><span data-stu-id="4a190-118">Research Mode is currently in Public Preview.</span></span> <span data-ttu-id="4a190-119">Hololens 2-Beispiele, Tutorials und vollständige API-Dokumentation finden Sie unter [ECCV 2020](https://eccv2020.eu/
 ) im git-Repository für den Research-Modus.</span><span class="sxs-lookup"><span data-stu-id="4a190-119">HoloLens 2 samples, tutorials, and full API documentation will be available at [ECCV 2020](https://eccv2020.eu/
 ) in the Research Mode Git repository.</span></span>

<span data-ttu-id="4a190-120">![Screenshot der Recherche Modus-App](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="4a190-120">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="4a190-121">*Eine gemischte Realität-Erfassung einer Testanwendung, die die acht im Research-Modus verfügbaren Sensordaten Ströme anzeigt*</span><span class="sxs-lookup"><span data-stu-id="4a190-121">*A mixed reality capture of a test application that displays the eight sensor streams available in Research Mode*</span></span>

## <a name="usage"></a><span data-ttu-id="4a190-122">Verwendung</span><span class="sxs-lookup"><span data-stu-id="4a190-122">Usage</span></span>

<span data-ttu-id="4a190-123">Der Forschungs Modus wurde für akademische und Industrieexperten entwickelt, die neue Ideen in den Feldern Maschinelles Sehen und Robotik kennenlernen.</span><span class="sxs-lookup"><span data-stu-id="4a190-123">Research Mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="4a190-124">Sie ist nicht für Anwendungen gedacht, die in Unternehmensumgebungen bereitgestellt werden oder über die Microsoft Store oder andere Vertriebskanäle verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="4a190-124">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="4a190-125">Außerdem bietet Microsoft keine Garantie dafür, dass der Forschungs Modus oder die entsprechende Funktionalität bei zukünftigen Hardware-oder Betriebssystemupdates unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="4a190-125">Additionally, Microsoft doesn't provide assurances that Research Mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="4a190-126">Dies sollte jedoch nicht daran hindern, ihn zum entwickeln und Testen neuer Ideen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="4a190-126">However, this shouldn't stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="4a190-127">Sicherheit und Leistung</span><span class="sxs-lookup"><span data-stu-id="4a190-127">Security and performance</span></span>

<span data-ttu-id="4a190-128">Beachten Sie, dass die Aktivierung des Research-Modus mehr Akkuleistung als die Verwendung der hololens 2 unter normalen Bedingungen beansprucht.</span><span class="sxs-lookup"><span data-stu-id="4a190-128">Be aware that enabling Research Mode uses more battery power than using the HoloLens 2 under normal conditions.</span></span> <span data-ttu-id="4a190-129">Dies gilt auch dann, wenn die Anwendung, die die Research Mode-Features verwendet, nicht ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="4a190-129">This is true even if the application using the Research Mode features is not running.</span></span>  <span data-ttu-id="4a190-130">Wenn Sie diesen Modus aktivieren, kann die Gesamtsicherheit Ihres Geräts auch gesenkt werden, da Anwendungen möglicherweise Sensordaten missbrauchen.</span><span class="sxs-lookup"><span data-stu-id="4a190-130">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="4a190-131">Weitere Informationen zur Gerätesicherheit finden Sie in den häufig gestellten Fragen zur [hololens-Sicherheit](https://docs.microsoft.com/hololens/hololens-faq-security).</span><span class="sxs-lookup"><span data-stu-id="4a190-131">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  

## <a name="device-support"></a><span data-ttu-id="4a190-132">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="4a190-132">Device support</span></span>
<table><span data-ttu-id="4a190-133">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span><span class="sxs-lookup"><span data-stu-id="4a190-133">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span></span><tr>
        <td><span data-ttu-id="4a190-134"><strong>Feature</strong></span><span class="sxs-lookup"><span data-stu-id="4a190-134"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="4a190-135"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="4a190-135"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="4a190-136"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="4a190-136"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4a190-137">Kopf Verfolgungs Kameras</span><span class="sxs-lookup"><span data-stu-id="4a190-137">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="4a190-138">✔️</span><span class="sxs-lookup"><span data-stu-id="4a190-138">✔️</span></span></td>
        <td><span data-ttu-id="4a190-139">✔️</span><span class="sxs-lookup"><span data-stu-id="4a190-139">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="4a190-140">Tiefe & IR-Kamera</span><span class="sxs-lookup"><span data-stu-id="4a190-140">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="4a190-141">✔️</span><span class="sxs-lookup"><span data-stu-id="4a190-141">✔️</span></span></td>
        <td><span data-ttu-id="4a190-142">✔️</span><span class="sxs-lookup"><span data-stu-id="4a190-142">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="4a190-143">Beschleunigungsmesser</span><span class="sxs-lookup"><span data-stu-id="4a190-143">Accelerometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="4a190-144">✔️</span><span class="sxs-lookup"><span data-stu-id="4a190-144">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="4a190-145">Gyroskop</span><span class="sxs-lookup"><span data-stu-id="4a190-145">Gyroscope</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="4a190-146">✔️</span><span class="sxs-lookup"><span data-stu-id="4a190-146">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="4a190-147">Magnetometer</span><span class="sxs-lookup"><span data-stu-id="4a190-147">Magnetometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="4a190-148">✔️</span><span class="sxs-lookup"><span data-stu-id="4a190-148">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-1st-gen-and-hololens-2"></a><span data-ttu-id="4a190-149">Aktivieren des Research-Modus (hololens 1. gen und hololens 2)</span><span class="sxs-lookup"><span data-stu-id="4a190-149">Enabling Research Mode (HoloLens 1st Gen and HoloLens 2)</span></span>

<span data-ttu-id="4a190-150">Der Forschungs Modus ist eine Erweiterung des Entwicklermodus.</span><span class="sxs-lookup"><span data-stu-id="4a190-150">Research Mode is an extension of Developer Mode.</span></span> <span data-ttu-id="4a190-151">Bevor Sie beginnen, müssen die Entwickler Funktionen des Geräts für den Zugriff auf die Einstellungen für den Research-Modus aktiviert werden:</span><span class="sxs-lookup"><span data-stu-id="4a190-151">Before starting, the developer features of the device need to be enabled to access the Research Mode settings:</span></span> 

* <span data-ttu-id="4a190-152">Öffnen Sie das **Startmenü > Einstellungen** , und wählen Sie **Updates**aus.</span><span class="sxs-lookup"><span data-stu-id="4a190-152">Open **Start Menu > Settings** and select **Updates**.</span></span>
* <span data-ttu-id="4a190-153">Wählen Sie **für Entwickler aus** , und aktivieren Sie **Entwicklermodus**.</span><span class="sxs-lookup"><span data-stu-id="4a190-153">Select **For Developers** and enable **Developer Mode**.</span></span>
* <span data-ttu-id="4a190-154">Scrollen Sie nach unten, und aktivieren Sie **Geräteportal**.</span><span class="sxs-lookup"><span data-stu-id="4a190-154">Scroll down and enable **Device Portal**.</span></span>

<span data-ttu-id="4a190-155">Nachdem die Entwickler Features aktiviert wurden, stellen Sie eine [Verbindung mit dem Geräte Portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) her, um die Funktionen des Research-Modus zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="4a190-155">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the Research Mode features:</span></span>

* <span data-ttu-id="4a190-156">Wechseln Sie im **Geräte Portal**zum **System > Research-Modus** .</span><span class="sxs-lookup"><span data-stu-id="4a190-156">Go to **System > Research Mode** in the **Device Portal**.</span></span>
* <span data-ttu-id="4a190-157">Wählen Sie **Zugriff auf Sensordaten Strom zulassen**aus.</span><span class="sxs-lookup"><span data-stu-id="4a190-157">Select **Allow access to sensor stream**.</span></span>
* <span data-ttu-id="4a190-158">Starten Sie das Gerät über das **Power** -Menü Element oben auf der Seite neu.</span><span class="sxs-lookup"><span data-stu-id="4a190-158">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="4a190-159">Nachdem Sie das Gerät neu gestartet haben, können die Anwendungen, die über das **Geräte Portal** geladen werden, auf Datenströme im Forschungs Modus zugreifen.</span><span class="sxs-lookup"><span data-stu-id="4a190-159">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research Mode streams.</span></span>

<span data-ttu-id="4a190-160">![Registerkarte "Forschungs Modus" des hololens-Geräte Portals](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="4a190-160">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="4a190-161">*Fenster "Forschungs Modus" im hololens-Geräte Portal*</span><span class="sxs-lookup"><span data-stu-id="4a190-161">*Research Mode window in the HoloLens Device Portal*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4a190-162">Der Forschungs Modus für hololens 2 ist ab Build 19041,1356 verfügbar.</span><span class="sxs-lookup"><span data-stu-id="4a190-162">Research Mode for HoloLens 2 is available beginning with build 19041.1356.</span></span> <span data-ttu-id="4a190-163">Wenn Sie in einem früheren Build Zugriff benötigen, registrieren Sie sich für unser [Insider-Vorschau](https://docs.microsoft.com/hololens/hololens-insider) Programm.</span><span class="sxs-lookup"><span data-stu-id="4a190-163">If you need access in an earlier build, sign up for our [Insider Preview](https://docs.microsoft.com/hololens/hololens-insider) program.</span></span>

### <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="4a190-164">Verwenden von Sensordaten in ihren apps</span><span class="sxs-lookup"><span data-stu-id="4a190-164">Using sensor data in your apps</span></span>

<span data-ttu-id="4a190-165">Anwendungen können auf die Sensordaten Strom Daten auf die gleiche Weise zugreifen wie auf Foto-und Videokamera-Streams über [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span><span class="sxs-lookup"><span data-stu-id="4a190-165">Applications can access the sensor stream data in the same way that photo and video camera streams are accessed through [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> 

<span data-ttu-id="4a190-166">Alle APIs, die für die hololens-Entwicklung funktionieren, sind auch im Research-Modus verfügbar.</span><span class="sxs-lookup"><span data-stu-id="4a190-166">All APIs that work for HoloLens development are also available in Research Mode.</span></span> <span data-ttu-id="4a190-167">Insbesondere weiß die Anwendung genau, wo sich hololens bei jeder Sensor Frame-Erfassungs Zeit in einem 6DOF-Raum befindet.</span><span class="sxs-lookup"><span data-stu-id="4a190-167">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="4a190-168">Beispielanwendungen zum Zugreifen auf die verschiedenen Datenströme im Forschungs Modus, zum Verwenden der systeminternen Funktionen [und der extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)und zum Aufzeichnen von Streams im GitHub-Repository-Repository [hololensforcv](https://github.com/Microsoft/HoloLensForCV) .</span><span class="sxs-lookup"><span data-stu-id="4a190-168">You can find sample applications on how to access the various Research Mode streams, how to use the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and how to record streams in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV) repo.</span></span>

 > [!NOTE]
 > <span data-ttu-id="4a190-169">Zu diesem Zeitpunkt funktioniert das hololensforcv-Beispiel nicht auf hololens 2.</span><span class="sxs-lookup"><span data-stu-id="4a190-169">At this time, the HoloLensForCV sample doesn't work on HoloLens 2.</span></span>

## <a name="support"></a><span data-ttu-id="4a190-170">Support</span><span class="sxs-lookup"><span data-stu-id="4a190-170">Support</span></span>

<span data-ttu-id="4a190-171">Verwenden Sie die [Problem](https://github.com/Microsoft/HololensForCV/issues) Verfolgung im Repository hololensforcv, um Feedback zu senden und bekannte Probleme nachzuverfolgen.</span><span class="sxs-lookup"><span data-stu-id="4a190-171">Please use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to post feedback and track known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a190-172">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4a190-172">See also</span></span>

* [<span data-ttu-id="4a190-173">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="4a190-173">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="4a190-174">Hololensforcv GitHub-Repository</span><span class="sxs-lookup"><span data-stu-id="4a190-174">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="4a190-175">Verwenden des Windows-Geräteportals</span><span class="sxs-lookup"><span data-stu-id="4a190-175">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
