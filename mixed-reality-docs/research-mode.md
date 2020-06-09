---
title: Hololens Research-Modus
description: Mithilfe des Research-Modus auf hololens kann eine Anwendung auf wichtige Geräte Sensordaten Ströme (Tiefe, Umgebungs Überwachung und IR-Reflektivität) zugreifen.
author: hferrone
ms.author: v-haferr
ms.date: 05/03/2018
ms.topic: article
keywords: Research Mode, CV, RS4, Maschinelles sehen, Forschung, hololens, hololens 2
ms.openlocfilehash: ec6f7b73a1f25932f10c10a7f0daaf78e536c0c4
ms.sourcegitcommit: 7f50210b71a65631fd1bc3fdb215064e0db34333
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84533102"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="06752-104">HoloLens-Forschungsmodus</span><span class="sxs-lookup"><span data-stu-id="06752-104">HoloLens Research mode</span></span>

## <a name="overview"></a><span data-ttu-id="06752-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="06752-105">Overview</span></span>

<span data-ttu-id="06752-106">Der Forschungs Modus wurde in den ersten hololens der Generation eingeführt, um den Zugriff auf die Schlüssel Sensoren auf dem Gerät zu erhalten, insbesondere für Forschungsanwendungen, die nicht für die Bereitstellung vorgesehen sind.</span><span class="sxs-lookup"><span data-stu-id="06752-106">Research mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="06752-107">Sie können jetzt Daten aus den folgenden Eingaben sammeln:</span><span class="sxs-lookup"><span data-stu-id="06752-107">You can now gather data from the following inputs:</span></span>

* <span data-ttu-id="06752-108">**Sichtbare Umgebungs Überwachungskameras** , die vom System für die Kopf-und Zuordnungs Bildung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="06752-108">**Visible Light Environment Tracking Cameras** - Used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="06752-109">**Tiefe Kamera** – wird in zwei Modi betrieben:</span><span class="sxs-lookup"><span data-stu-id="06752-109">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="06752-110">Short-Throw, High Frequency (30 fps) fast-Tiefe-Erkennung für die [Hand Verfolgung](interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="06752-110">Short-throw, high-frequency (30 FPS) near-depth sensing used for [Hand Tracking](interaction-fundamentals.md)</span></span>
    + <span data-ttu-id="06752-111">Lange throw-, Low-Frequency (1-5 fps)-Erkennung, die von der [räumlichen Zuordnung](spatial-mapping.md) verwendet wird</span><span class="sxs-lookup"><span data-stu-id="06752-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](spatial-mapping.md)</span></span>
* <span data-ttu-id="06752-112">**Zwei Versionen des IR-Reflektivität-Streams** : werden von den hololens zum Berechnen der Tiefe verwendet.</span><span class="sxs-lookup"><span data-stu-id="06752-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="06752-113">Diese Bilder werden von Infrarot beleuchtet und sind von der Sichtbarkeit sichtbar.</span><span class="sxs-lookup"><span data-stu-id="06752-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="06752-114">Wenn Sie ein hololens 2 verwenden, können Sie auch auf die folgenden Eingaben zugreifen:</span><span class="sxs-lookup"><span data-stu-id="06752-114">If you're using a HoloLens 2 you will also be able to access the following inputs:</span></span>

* <span data-ttu-id="06752-115">**Beschleunigungsmesser** – wird vom System verwendet, um die lineare Beschleunigung entlang der X-, Y-und Z-Achse und der Schweregrad zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="06752-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y and Z axes and gravity.</span></span>
* <span data-ttu-id="06752-116">**Gyro** – wird vom System verwendet, um Drehungen zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="06752-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="06752-117">**Magnetometer** – wird vom System zum Schätzen der absoluten Ausrichtung verwendet.</span><span class="sxs-lookup"><span data-stu-id="06752-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

<span data-ttu-id="06752-118">![Screenshot der Recherche Modus-App](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="06752-118">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="06752-119">*Eine gemischte Realität-Erfassung einer Testanwendung, die die acht im Research-Modus verfügbaren Sensordaten Ströme anzeigt*</span><span class="sxs-lookup"><span data-stu-id="06752-119">*A mixed reality capture of a test application that displays the eight sensor streams available in Research mode*</span></span>

> [!NOTE]
> <span data-ttu-id="06752-120">Die Research Mode-Funktion wurde als Teil des [Windows 10-Updates vom April 2018](release-notes-april-2018.md) für hololens hinzugefügt und ist in früheren Versionen nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="06752-120">The Research Mode feature was added as part of the [Windows 10 April 2018 Update](release-notes-april-2018.md) for HoloLens, and is not available on earlier releases.</span></span>

## <a name="usage"></a><span data-ttu-id="06752-121">Verwendung</span><span class="sxs-lookup"><span data-stu-id="06752-121">Usage</span></span>

<span data-ttu-id="06752-122">Der Forschungs Modus wurde für akademische und Industrieexperten entwickelt, die neue Ideen in den Feldern Maschinelles Sehen und Robotik kennenlernen.</span><span class="sxs-lookup"><span data-stu-id="06752-122">Research mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="06752-123">Sie ist nicht für Anwendungen gedacht, die in Unternehmensumgebungen bereitgestellt werden oder über die Microsoft Store oder andere Vertriebskanäle verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="06752-123">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="06752-124">Außerdem bietet Microsoft keine Garantie dafür, dass der Forschungs Modus oder die entsprechende Funktionalität bei zukünftigen Hardware-oder Betriebssystemupdates unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="06752-124">Additionally, Microsoft doesn't provide assurances that research mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="06752-125">Dies sollte jedoch nicht daran hindern, ihn zum entwickeln und Testen neuer Ideen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="06752-125">However, this shouldn't stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="06752-126">Sicherheit und Leistung</span><span class="sxs-lookup"><span data-stu-id="06752-126">Security and performance</span></span>

<span data-ttu-id="06752-127">Beachten Sie, dass die Aktivierung des Research-Modus mehr Akkuleistung als die Verwendung der hololens 2 unter normalen Bedingungen beansprucht.</span><span class="sxs-lookup"><span data-stu-id="06752-127">Be aware that enabling research mode uses more battery power than using the HoloLens 2 under normal conditions.</span></span> <span data-ttu-id="06752-128">Dies gilt auch dann, wenn die Anwendung, die die Research Mode-Features verwendet, nicht ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="06752-128">This is true even if the application using the research mode features is not running.</span></span>  <span data-ttu-id="06752-129">Wenn Sie diesen Modus aktivieren, kann die Gesamtsicherheit Ihres Geräts auch gesenkt werden, da Anwendungen möglicherweise Sensordaten missbrauchen.</span><span class="sxs-lookup"><span data-stu-id="06752-129">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="06752-130">Weitere Informationen zur Gerätesicherheit finden Sie in den häufig gestellten Fragen zur [hololens-Sicherheit](https://docs.microsoft.com/hololens/hololens-faq-security).</span><span class="sxs-lookup"><span data-stu-id="06752-130">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  


## <a name="device-support"></a><span data-ttu-id="06752-131">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="06752-131">Device support</span></span>

<table>
    <colgroup>
    <col width="50%" />
    <col width="50%" />
    <!-- <col width="33%" /> -->
    </colgroup>
    <tr>
        <td><span data-ttu-id="06752-132"><strong>Funktion</strong></span><span class="sxs-lookup"><span data-stu-id="06752-132"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="06752-133"><a href="hololens-hardware-details.md"><strong>Hololens 1. Gen</strong></a></span><span class="sxs-lookup"><span data-stu-id="06752-133"><a href="hololens-hardware-details.md"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <!-- <td><a href="hololens2-hardware.md"><strong>HoloLens 2</strong></a></td> -->
    </tr>
     <tr>
        <td><span data-ttu-id="06752-134">Kopf Verfolgungs Kameras</span><span class="sxs-lookup"><span data-stu-id="06752-134">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="06752-135">✔️</span><span class="sxs-lookup"><span data-stu-id="06752-135">✔️</span></span></td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="06752-136">Tiefe & IR-Kamera</span><span class="sxs-lookup"><span data-stu-id="06752-136">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="06752-137">✔️</span><span class="sxs-lookup"><span data-stu-id="06752-137">✔️</span></span></td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="06752-138">Beschleunigungsmesser</span><span class="sxs-lookup"><span data-stu-id="06752-138">Accelerometer</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="06752-139">Gyroskop</span><span class="sxs-lookup"><span data-stu-id="06752-139">Gyroscope</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
    <tr>
        <td><span data-ttu-id="06752-140">Magnetometer</span><span class="sxs-lookup"><span data-stu-id="06752-140">Magnetometer</span></span></td>
        <td>❌</td>
        <!-- <td>❌</td> -->
    </tr>
</table>

> [!IMPORTANT]
> <span data-ttu-id="06752-141">Die Unterstützung für den Research-Modus für hololens 2 wird voraussichtlich in der öffentlichen Vorschauversion im Juli 2020 verfügbar sein und umfasst alle oben aufgeführten Features.</span><span class="sxs-lookup"><span data-stu-id="06752-141">Research Mode support for HoloLens 2 is expected to be available in public preview in July 2020 and will include all the features listed above.</span></span> <span data-ttu-id="06752-142">Weitere Informationen finden Sie hier.</span><span class="sxs-lookup"><span data-stu-id="06752-142">Please check back for more information.</span></span> 

## <a name="enabling-research-mode"></a><span data-ttu-id="06752-143">Aktivieren des Research-Modus</span><span class="sxs-lookup"><span data-stu-id="06752-143">Enabling Research mode</span></span>

<span data-ttu-id="06752-144">Der Forschungs Modus ist eine Erweiterung des Entwicklermodus.</span><span class="sxs-lookup"><span data-stu-id="06752-144">Research mode is an extension of Developer Mode.</span></span> <span data-ttu-id="06752-145">Bevor Sie beginnen, müssen die Entwickler Funktionen des Geräts für den Zugriff auf die Einstellungen für den Research-Modus aktiviert werden:</span><span class="sxs-lookup"><span data-stu-id="06752-145">Before starting, the developer features of the device need to be enabled to access the research mode settings:</span></span> 

* <span data-ttu-id="06752-146">Öffnen Sie das **Startmenü > Einstellungen** , und wählen Sie **Updates**aus.</span><span class="sxs-lookup"><span data-stu-id="06752-146">Open **Start Menu > Settings** and select **Updates**.</span></span>
* <span data-ttu-id="06752-147">Wählen Sie **für Entwickler aus** , und aktivieren Sie **Entwicklermodus**.</span><span class="sxs-lookup"><span data-stu-id="06752-147">Select **For Developers** and enable **Developer Mode**.</span></span>
* <span data-ttu-id="06752-148">Scrollen Sie nach unten, und aktivieren Sie das **Geräte Portal**.</span><span class="sxs-lookup"><span data-stu-id="06752-148">Scroll down and enable **Device Portal**.</span></span>

<span data-ttu-id="06752-149">Nachdem die Entwickler Features aktiviert wurden, stellen Sie eine [Verbindung mit dem Geräte Portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) her, um die Funktionen des Research-Modus zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="06752-149">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the research mode features.</span></span>

<span data-ttu-id="06752-150">Auf *hololens 1. Gen*:</span><span class="sxs-lookup"><span data-stu-id="06752-150">On *HoloLens 1st Gen*:</span></span>

* <span data-ttu-id="06752-151">Wechseln Sie im **Geräte Portal**zum **System > Research-Modus** .</span><span class="sxs-lookup"><span data-stu-id="06752-151">Go to **System > Research mode** in the **Device Portal**.</span></span>
* <span data-ttu-id="06752-152">Wählen Sie **Zugriff auf Sensordaten Strom zulassen**aus.</span><span class="sxs-lookup"><span data-stu-id="06752-152">Select **Allow access to sensor stream**.</span></span>
* <span data-ttu-id="06752-153">Starten Sie das Gerät über das **Power** -Menü Element oben auf der Seite neu.</span><span class="sxs-lookup"><span data-stu-id="06752-153">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="06752-154">Nachdem Sie das Gerät neu gestartet haben, können die Anwendungen, die über das **Geräte Portal** geladen werden, auf Datenströme im Forschungs Modus zugreifen.</span><span class="sxs-lookup"><span data-stu-id="06752-154">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research mode streams.</span></span>

<span data-ttu-id="06752-155">![Registerkarte "Forschungs Modus" des hololens-Geräte Portals](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="06752-155">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="06752-156">*Fenster "Forschungs Modus" im hololens-Geräte Portal*</span><span class="sxs-lookup"><span data-stu-id="06752-156">*Research mode window in the HoloLens Device Portal*</span></span>

## <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="06752-157">Verwenden von Sensordaten in ihren apps</span><span class="sxs-lookup"><span data-stu-id="06752-157">Using sensor data in your apps</span></span>

<span data-ttu-id="06752-158">*Hololens 1. Gen*</span><span class="sxs-lookup"><span data-stu-id="06752-158">*HoloLens 1st Gen*</span></span>

<span data-ttu-id="06752-159">Anwendungen können auf die Sensordaten Strom Daten auf die gleiche Weise zugreifen wie auf Foto-und Videokamera-Streams über [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span><span class="sxs-lookup"><span data-stu-id="06752-159">Applications can access the sensor stream data in the same way that photo and video camera streams are accessed through [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197).</span></span> 

<span data-ttu-id="06752-160">Alle APIs, die für die hololens-Entwicklung funktionieren, sind auch im Research-Modus verfügbar.</span><span class="sxs-lookup"><span data-stu-id="06752-160">All APIs that work for HoloLens development are also available in Research mode.</span></span> <span data-ttu-id="06752-161">Insbesondere weiß die Anwendung genau, wo sich hololens bei jeder Sensor Frame-Erfassungs Zeit in einem 6DOF-Raum befindet.</span><span class="sxs-lookup"><span data-stu-id="06752-161">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="06752-162">Beispielanwendungen zum Zugreifen auf die verschiedenen Datenströme im Forschungs Modus, zum Verwenden der systeminternen Funktionen [und der extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)und zum Aufzeichnen von Streams im GitHub-Repository-Repository [hololensforcv](https://github.com/Microsoft/HoloLensForCV) .</span><span class="sxs-lookup"><span data-stu-id="06752-162">You can find sample applications on how to access the various Research mode streams, how to use the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and how to record streams in the [HoloLensForCV GitHub repo](https://github.com/Microsoft/HoloLensForCV) repo.</span></span>

 > [!NOTE]
 > <span data-ttu-id="06752-163">Zu diesem Zeitpunkt funktioniert das hololensforcv-Beispiel nicht auf hololens 2.</span><span class="sxs-lookup"><span data-stu-id="06752-163">At this time, the HoloLensForCV sample doesn't work on HoloLens 2.</span></span>

## <a name="known-issues"></a><span data-ttu-id="06752-164">Bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="06752-164">Known issues</span></span>

<span data-ttu-id="06752-165">Sie können den [Issue Tracker](https://github.com/Microsoft/HololensForCV/issues) im hololensforcv-Repository verwenden, um bekannte Probleme zu verfolgen.</span><span class="sxs-lookup"><span data-stu-id="06752-165">You can use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to follow known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="06752-166">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="06752-166">See also</span></span>

* [<span data-ttu-id="06752-167">Microsoft Media Foundation</span><span class="sxs-lookup"><span data-stu-id="06752-167">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="06752-168">Hololensforcv GitHub-Repository</span><span class="sxs-lookup"><span data-stu-id="06752-168">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="06752-169">Verwenden des Windows-Geräteportals</span><span class="sxs-lookup"><span data-stu-id="06752-169">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
