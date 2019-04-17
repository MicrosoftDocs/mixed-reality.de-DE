---
title: 'MR und Azure-313: IoT Hub-Dienst'
description: Führen Sie diesen Kurs erfahren, wie Sie Azure IoT Hub-Dienst auf einem virtuellen Computer unter Ubuntu 16.4 implementieren, und klicken Sie dann visualisieren Sie die Nachrichtendaten, die mithilfe von Microsoft HoloLens oder eine immersive (VR) Kopfhörer zu.
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Edge, Iot-Edge, Tutorial, api, Notification, Funktionen, Tabellen, immersive Hololens, Vr, Iot, VM, Ubuntu, Python
ms.openlocfilehash: 1ab7c48ac3cff1cb2283cadb171098af9e148628
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593253"
---
>[!NOTE]
><span data-ttu-id="56dbe-104">In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.</span><span class="sxs-lookup"><span data-stu-id="56dbe-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="56dbe-105">Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.</span><span class="sxs-lookup"><span data-stu-id="56dbe-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="56dbe-106">In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="56dbe-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="56dbe-107">Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="56dbe-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="56dbe-108">Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="56dbe-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="56dbe-109">Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="56dbe-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-313-iot-hub-service"></a><span data-ttu-id="56dbe-110">MR und Azure-313: IoT Hub-Dienst</span><span class="sxs-lookup"><span data-stu-id="56dbe-110">MR and Azure 313: IoT Hub Service</span></span>

![Kurs Ergebnis](images/AzureLabs-Lab313-00.png)

<span data-ttu-id="56dbe-112">In diesem Kurs erfahren Sie, wie zum Implementieren einer **Azure IoT Hub-Dienst** auf einem virtuellen Computer das Betriebssystem die Ubuntu-16.4 ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="56dbe-112">In this course, you will learn how to implement an **Azure IoT Hub Service** on a virtual machine running the Ubuntu 16.4 operating system.</span></span> <span data-ttu-id="56dbe-113">Ein **Azure Function-App** wird dann zum Empfangen von Nachrichten von Ihrem Ubuntu-VM verwendet werden, und speichern Sie das Ergebnis in eine **Azure-Tabellendienst**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-113">An **Azure Function App** will then be used to receive messages from your Ubuntu VM, and store the result within an **Azure Table Service**.</span></span> <span data-ttu-id="56dbe-114">Sie werden dann in der Lage sind, zeigen Sie diese Daten mithilfe **Power BI** für Microsoft HoloLens oder Kopfhörer für immersive (VR).</span><span class="sxs-lookup"><span data-stu-id="56dbe-114">You will then be able to view this data using **Power BI** on Microsoft HoloLens or immersive (VR) headset.</span></span>

<span data-ttu-id="56dbe-115">Der Inhalt dieses Kurses *gilt* auf IoT Edge-Geräten, obwohl in diesem Kurs, der Fokus werden in einer VM-Umgebung, damit kein Zugriff auf ein physisches edgegerät erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="56dbe-115">The content of this course *is applicable* to IoT Edge devices, though for the purpose of this course, the focus will be on a virtual machine environment, so that access to a physical Edge device is not necessary.</span></span>

<span data-ttu-id="56dbe-116">Nach Abschluss dieses Kurses, lernen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="56dbe-116">By completing this course, you will learn to:</span></span>

- <span data-ttu-id="56dbe-117">Bereitstellen einer **IoT Edge-Modul** an einen virtuellen Computer (Ubuntu 16 OS), die Ihr IoT-Gerät darstellen wird.</span><span class="sxs-lookup"><span data-stu-id="56dbe-117">Deploy an **IoT Edge module** to a Virtual Machine (Ubuntu 16 OS), which will represent your IoT device.</span></span>
- <span data-ttu-id="56dbe-118">Hinzufügen einer **Azure Custom Vision Tensorflow-Modells** für das Edge-Modul, mit Code, der im Container gespeicherte Bilder analysiert wird.</span><span class="sxs-lookup"><span data-stu-id="56dbe-118">Add an **Azure Custom Vision Tensorflow Model** to the Edge module, with code that will analyze images stored in the container.</span></span>
- <span data-ttu-id="56dbe-119">Richten Sie das Modul zum Senden der Nachricht der Analysis-Ergebnis zurück an Ihre **IoT Hub-Dienst**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-119">Set up the module to send the analysis result message back to your **IoT Hub Service**.</span></span>
- <span data-ttu-id="56dbe-120">Verwenden einer **Azure Function-App** zum Speichern der Nachricht in eine **Azure Table**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-120">Use an **Azure Function App** to store the message within an **Azure Table**.</span></span>
- <span data-ttu-id="56dbe-121">Richten Sie **Power BI** gespeicherten Nachrichten sammeln, und erstellen Sie einen Bericht.</span><span class="sxs-lookup"><span data-stu-id="56dbe-121">Set up **Power BI** to collect the stored message and create a report.</span></span>
- <span data-ttu-id="56dbe-122">Visualisieren Sie Ihre IoT-Nachrichtendaten in **Power BI**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-122">Visualize your IoT message data within **Power BI**.</span></span>

<span data-ttu-id="56dbe-123">Die Dienste, die Sie verwenden, umfassen:</span><span class="sxs-lookup"><span data-stu-id="56dbe-123">The Services you will use include:</span></span>

- <span data-ttu-id="56dbe-124">**Azure IoT-Hub** ist ein Microsoft Azure der Dienst ermöglicht es Entwicklern, verbinden, überwachen und Verwalten von IoT-Assets.</span><span class="sxs-lookup"><span data-stu-id="56dbe-124">**Azure IoT Hub** is a Microsoft Azure Service which allows developers to connect, monitor, and manage, IoT assets.</span></span> <span data-ttu-id="56dbe-125">Weitere Informationen finden Sie auf die [ **Azure IoT Hub-Dienst** Seite](https://azure.microsoft.com/en-au/services/iot-hub/).</span><span class="sxs-lookup"><span data-stu-id="56dbe-125">For more information, visit the [**Azure IoT Hub Service** page](https://azure.microsoft.com/en-au/services/iot-hub/).</span></span>

- <span data-ttu-id="56dbe-126">**Azure-Containerregistrierung** ist ein Microsoft Azure der Dienst ermöglicht Entwicklern das Speichern von containerimages für verschiedene Arten von Containern.</span><span class="sxs-lookup"><span data-stu-id="56dbe-126">**Azure Container Registry** is a Microsoft Azure Service which allows developers to store container images, for various types of containers.</span></span> <span data-ttu-id="56dbe-127">Weitere Informationen finden Sie auf die [ **Azure Container Registry Service** Seite](https://azure.microsoft.com/en-au/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="56dbe-127">For more information, visit the [**Azure Container Registry Service** page](https://azure.microsoft.com/en-au/services/container-registry/).</span></span>

- <span data-ttu-id="56dbe-128">**Azure-Funktions-App** ist ein Azure-Dienst von Microsoft, die Entwickler kleine Teile des Codes ausgeführt werden kann, "Funktionen", in Azure.</span><span class="sxs-lookup"><span data-stu-id="56dbe-128">**Azure Function App** is a Microsoft Azure Service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="56dbe-129">Dadurch wird eine Möglichkeit zum Delegieren der Arbeit an Ihrer lokalen Anwendung, die viele Vorteile haben kann, anstatt die Cloud.</span><span class="sxs-lookup"><span data-stu-id="56dbe-129">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="56dbe-130">**Azure Functions** unterstützt verschiedene Entwicklungssprachen, darunter C\#, F\#, Node.js, Java und PHP.</span><span class="sxs-lookup"><span data-stu-id="56dbe-130">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="56dbe-131">Weitere Informationen finden Sie auf die [ **Azure Functions** Seite](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="56dbe-131">For more information, visit the [**Azure Functions** page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

- <span data-ttu-id="56dbe-132">**Azure-Speicher: Tabellen** ist ein Microsoft Azure-Dienst, die Entwicklern das Speichern, strukturiert kann, nicht-SQL, Daten in der Cloud, somit problemlos eine beliebige Stelle.</span><span class="sxs-lookup"><span data-stu-id="56dbe-132">**Azure Storage: Tables** is a Microsoft Azure Service, which allows developers to store structured, non-SQL, data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="56dbe-133">Der Dienst bietet ein schemalose Design, sodass für die Entwicklung von Tabellen, je nach Bedarf, und ist daher sehr flexibel.</span><span class="sxs-lookup"><span data-stu-id="56dbe-133">The Service boasts a schema-less design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="56dbe-134">Weitere Informationen finden Sie auf die [ **Azure-Tabellen** Seite](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="56dbe-134">For more information, visit the [**Azure Tables** page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="56dbe-135">In diesem Kurs erfahren Sie, wie zum Einrichten und verwenden Sie den IoT Hub-Dienst und stellen dann eine Antwort von einem Gerät bereitgestellten visuell dar.</span><span class="sxs-lookup"><span data-stu-id="56dbe-135">This course will teach you how to setup and use the IoT Hub Service, and then visualize a response provided by a device.</span></span> <span data-ttu-id="56dbe-136">Sie werden sich entscheiden, ob Sie diese Konzepte zu einem benutzerdefinierten Setup für die IoT Hub-Dienst angewendet, die Sie erstellen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-136">It will be up to you to apply these concepts to a custom IoT Hub Service setup, which you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="56dbe-137">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="56dbe-137">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="56dbe-138">Kurs</span><span class="sxs-lookup"><span data-stu-id="56dbe-138">Course</span></span></th><th style="width:150px"> <span data-ttu-id="56dbe-139"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="56dbe-139"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="56dbe-140"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="56dbe-140"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="56dbe-141">MR und Azure-313: IoT Hub-Dienst</span><span class="sxs-lookup"><span data-stu-id="56dbe-141">MR and Azure 313: IoT Hub Service</span></span></td><td style="text-align: center;"> <span data-ttu-id="56dbe-142">✔️</span><span class="sxs-lookup"><span data-stu-id="56dbe-142">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="56dbe-143">✔️</span><span class="sxs-lookup"><span data-stu-id="56dbe-143">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="56dbe-144">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="56dbe-144">Prerequisites</span></span>

<span data-ttu-id="56dbe-145">Die aktuellsten Voraussetzungen für die Entwicklung mit gemischten Realität, einschließlich der mit dem Microsoft HoloLens finden Sie unter den [Installieren der Tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) Artikel.</span><span class="sxs-lookup"><span data-stu-id="56dbe-145">For the most up-to-date prerequisites for developing with mixed reality, including with the Microsoft HoloLens, visit the [Install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article.</span></span>

> [!NOTE]
> <span data-ttu-id="56dbe-146">In diesem Tutorial ist für Entwickler konzipiert, die grundlegende Erfahrung mit Python haben.</span><span class="sxs-lookup"><span data-stu-id="56dbe-146">This tutorial is designed for developers who have basic experience with Python.</span></span> <span data-ttu-id="56dbe-147">Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Juli 2018) überprüft wurde.</span><span class="sxs-lookup"><span data-stu-id="56dbe-147">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="56dbe-148">Sie können zur Verwendung der neuesten Software, wie in der [Installieren der Tools](install-the-tools.md) jedoch nicht angenommen werden soll, dass die Informationen in diesem Kurs perfekt Angebote in neueren Software als die entspricht unten aufgeführten Artikel.</span><span class="sxs-lookup"><span data-stu-id="56dbe-148">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than that listed below.</span></span>

<span data-ttu-id="56dbe-149">Die folgende Hardware und Software ist erforderlich:</span><span class="sxs-lookup"><span data-stu-id="56dbe-149">The following hardware and software is required:</span></span>

- <span data-ttu-id="56dbe-150">Windows 10 Fall Creators Update (oder höher), **Entwicklermodus aktiviert ist**</span><span class="sxs-lookup"><span data-stu-id="56dbe-150">Windows 10 Fall Creators Update (or later), **Developer Mode enabled**</span></span>

    > [!WARNING]
    > <span data-ttu-id="56dbe-151">Sie können nicht mit Hyper-V unter Windows 10 Home Edition einen virtuellen Computer ausführen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-151">You cannot run a Virtual Machine using Hyper-V on Windows 10 Home Edition.</span></span>

- <span data-ttu-id="56dbe-152">Windows 10 SDK (neueste Version)</span><span class="sxs-lookup"><span data-stu-id="56dbe-152">Windows 10 SDK (latest version)</span></span>
- <span data-ttu-id="56dbe-153">Eine HoloLens **Entwicklermodus aktiviert ist**</span><span class="sxs-lookup"><span data-stu-id="56dbe-153">A HoloLens, **Developer Mode enabled**</span></span>
- <span data-ttu-id="56dbe-154">Visual Studio 2017.15.4 (nur auf dem Azure-Cloud-Explorer verwendet)</span><span class="sxs-lookup"><span data-stu-id="56dbe-154">Visual Studio 2017.15.4 (Only used to access the Azure Cloud Explorer)</span></span>
- <span data-ttu-id="56dbe-155">Zugriff auf das Internet für Azure und IoT Hub-Dienst.</span><span class="sxs-lookup"><span data-stu-id="56dbe-155">Internet Access for Azure, and for IoT Hub Service.</span></span> <span data-ttu-id="56dbe-156">Weitere Informationen führen Sie dies [Link zur Seite für IoT Hub-Dienst](https://azure.microsoft.com/en-au/services/iot-hub/)</span><span class="sxs-lookup"><span data-stu-id="56dbe-156">For more information, please follow this [link to IoT Hub Service page](https://azure.microsoft.com/en-au/services/iot-hub/)</span></span>
- <span data-ttu-id="56dbe-157">Machine Learning-Modellen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-157">A machine learning model.</span></span> <span data-ttu-id="56dbe-158">Wenn Sie Ihre eigenen kann jetzt Modell verwenden keine [können Sie das Modell bereitgestellt, die in diesem Kurs](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span><span class="sxs-lookup"><span data-stu-id="56dbe-158">If you do not have your own ready to use model, [you can use the model provided with this course](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span></span>
- <span data-ttu-id="56dbe-159">**Hyper-V** Software auf Ihrem Entwicklungscomputer für Windows 10 aktiviert.</span><span class="sxs-lookup"><span data-stu-id="56dbe-159">**Hyper-V** software enabled on your Windows 10 development machine.</span></span>
- <span data-ttu-id="56dbe-160">Einen virtuellen Computer Ubuntu (16.4 oder 18.4), ausgeführt auf Ihrem Entwicklungscomputer oder Alternativ können Sie können sich auf einem separaten Computer unter Linux (Ubuntu 16.4 oder 18.4).</span><span class="sxs-lookup"><span data-stu-id="56dbe-160">A Virtual Machine running Ubuntu (16.4 or 18.4), running on your development machine or alternatively you can use a separate computer running Linux (Ubuntu 16.4 or 18.4).</span></span> <span data-ttu-id="56dbe-161">Können weitere Informationen finden Sie Anleitungen zum Erstellen eines virtuellen Computers unter Windows mithilfe von Hyper-V in der ["Vorbereitungen" im Kapitel](#before-you-start). () https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="56dbe-161">You can find more information on how to create a VM on Windows using Hyper-V in the ["Before you Start" chapter](#before-you-start).(https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span></span>  



### <a name="before-you-start"></a><span data-ttu-id="56dbe-162">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="56dbe-162">Before you start</span></span>

1. <span data-ttu-id="56dbe-163">Richten Sie ein und Testen Sie Ihre HoloLens.</span><span class="sxs-lookup"><span data-stu-id="56dbe-163">Set up and test your HoloLens.</span></span> <span data-ttu-id="56dbe-164">Bei Bedarf Unterstützung zum Einrichten Ihrer HoloLens, [stellen Sie sicher, dass die HoloLens-Setup-Artikel finden Sie unter](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="56dbe-164">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span>
2. <span data-ttu-id="56dbe-165">Es ist eine gute Idee, führen Sie **Kalibrierung** und **Sensor Optimierung** Beginn (manchmal es kann helfen, diese Aufgaben für jeden Benutzer) eine neue HoloLens-app entwickeln.</span><span class="sxs-lookup"><span data-stu-id="56dbe-165">It is a good idea to perform **Calibration** and **Sensor Tuning** when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span>

<span data-ttu-id="56dbe-166">Um Hilfe zur Kalibrierung, befolgen Sie diese [Link zum Artikel HoloLens Kalibrierung](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="56dbe-166">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="56dbe-167">Um Hilfe zur Optimierung der Sensor, befolgen Sie diese [Link zum Optimieren von HoloLens Sensor](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="56dbe-167">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

3. <span data-ttu-id="56dbe-168">Richten Sie Ihre **virtuellen Ubuntu-Computer** mit **Hyper-V**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-168">Set up your **Ubuntu Virtual Machine** using **Hyper-V**.</span></span> <span data-ttu-id="56dbe-169">Die folgenden Ressourcen helfen Ihnen mit dem Prozess.</span><span class="sxs-lookup"><span data-stu-id="56dbe-169">The following resources will help you with the process.</span></span>
    1.  <span data-ttu-id="56dbe-170">Führen Sie zunächst diesen Link, um [Herunterladen der ISO-Datei für Ubuntu 16.04.4 LTS (Xenial Xerus)](http://au.releases.ubuntu.com/16.04/).</span><span class="sxs-lookup"><span data-stu-id="56dbe-170">First, follow this link to [download the Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](http://au.releases.ubuntu.com/16.04/).</span></span> <span data-ttu-id="56dbe-171">Wählen Sie die **Desktopabbild für 64-Bit-PC (AMD64)**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-171">Select the **64-bit PC (AMD64) desktop image**.</span></span>
    2.  <span data-ttu-id="56dbe-172">Stellen Sie sicher, dass **Hyper-V** auf Ihrem Windows 10-Computer aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="56dbe-172">Make sure **Hyper-V** is enabled on your Windows 10 machine.</span></span> <span data-ttu-id="56dbe-173">Folgen Sie diesem Link, um Anleitungen auf [installieren und aktivieren Hyper-V unter Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span><span class="sxs-lookup"><span data-stu-id="56dbe-173">You can follow this link for guidance on [installing and enabling Hyper-V on Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span></span>
    3.  <span data-ttu-id="56dbe-174">Starten Sie die Hyper-V, und Erstellen einer neuen Ubuntu-VM.</span><span class="sxs-lookup"><span data-stu-id="56dbe-174">Start Hyper-V and create a new Ubuntu VM.</span></span> <span data-ttu-id="56dbe-175">Sie können diesem Link folgen einem [Schritt-für-Schritt-Anleitung zum Erstellen eines virtuellen Computers mit Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="56dbe-175">You can follow this link for a [step by step guide on how to create a VM with Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span></span> <span data-ttu-id="56dbe-176">Bei angeforderten **"Betriebssystem von startfähiger Imagedatei installieren"**, wählen die **Ubuntu ISO** haben Sie zuvor herunterladen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-176">When requested to **"Install an operating system from a bootable image file"**, select the **Ubuntu ISO** you have download earlier.</span></span>

    > [!NOTE]
    > <span data-ttu-id="56dbe-177">Mithilfe von **Hyper-V-Schnellerfassung** wird nicht empfohlen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-177">Using **Hyper-V Quick Create** is not suggested.</span></span>  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a><span data-ttu-id="56dbe-178">Kapitel 1: Abrufen des Custom Vision-Modells</span><span class="sxs-lookup"><span data-stu-id="56dbe-178">Chapter 1 - Retrieve the Custom Vision model</span></span>

<span data-ttu-id="56dbe-179">In diesem Kurs haben Sie Zugriff auf eine [vorgefertigte Custom Vision-Modell](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) , der erkennt, Tastaturen und Mäusen aus Bildern.</span><span class="sxs-lookup"><span data-stu-id="56dbe-179">With this course you will have access to a [pre-built Custom Vision model](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) that detects keyboards and mice from images.</span></span> <span data-ttu-id="56dbe-180">Wenn Sie diese verwenden, fahren Sie mit [Kapitel 2](#chapter-2---the-container-registry-service).</span><span class="sxs-lookup"><span data-stu-id="56dbe-180">If you use this, proceed to [Chapter 2](#chapter-2---the-container-registry-service).</span></span>

<span data-ttu-id="56dbe-181">Allerdings können Sie folgende Schritte ausführen, wenn Sie Ihre eigenen Custom Vision-Modell verwenden möchten:</span><span class="sxs-lookup"><span data-stu-id="56dbe-181">However, you can follow these steps if you wish to use your own Custom Vision model:</span></span>

1. <span data-ttu-id="56dbe-182">In Ihrer **Custom Vision Projekt** wechseln Sie zu der **Leistung** Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="56dbe-182">In your **Custom Vision Project** go to the **Performance** tab.</span></span>

    > [!WARNING]
    > <span data-ttu-id="56dbe-183">Verwenden Sie das Modell muss eine *compact* Domäne exportieren.</span><span class="sxs-lookup"><span data-stu-id="56dbe-183">Your model must use a *compact* domain, to export the model.</span></span> <span data-ttu-id="56dbe-184">Sie können Ihre Modelle Domäne in den Einstellungen für das Projekt ändern.</span><span class="sxs-lookup"><span data-stu-id="56dbe-184">You can change your models domain in the settings for your project.</span></span>

    ![Registerkarte "Leistung"](images/AzureLabs-Lab313-01.png)

2. <span data-ttu-id="56dbe-186">Wählen Sie die **Iteration** Sie exportieren möchten und klicken auf **exportieren**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-186">Select the **Iteration** you want to export and click on **Export**.</span></span> <span data-ttu-id="56dbe-187">Es wird ein Blatt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="56dbe-187">A blade will appear.</span></span>

    ![Blatt "Export"](images/AzureLabs-Lab313-02.png)

3. <span data-ttu-id="56dbe-189">Klicken Sie auf dem Blatt auf **Docker-Datei**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-189">In the blade click **Docker File**.</span></span>

    ![Wählen Sie docker](images/AzureLabs-Lab313-03.png)

4. <span data-ttu-id="56dbe-191">Klicken Sie auf **Linux** in der Dropdown-Menü, und klicken Sie dann auf **herunterladen**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-191">Click **Linux** in the drop-down menu and then click on **Download**.</span></span>

    ![Klicken Sie auf download](images/AzureLabs-Lab313-04.png)

5. <span data-ttu-id="56dbe-193">Entzippen Sie den Inhalt aus.</span><span class="sxs-lookup"><span data-stu-id="56dbe-193">Unzip the content.</span></span> <span data-ttu-id="56dbe-194">Sie werden später in diesem Kurs verwendet.</span><span class="sxs-lookup"><span data-stu-id="56dbe-194">You will use it later in this course.</span></span>

## <a name="chapter-2---the-container-registry-service"></a><span data-ttu-id="56dbe-195">Kapitel 2: der Container-Service-Registrierung</span><span class="sxs-lookup"><span data-stu-id="56dbe-195">Chapter 2 - The Container Registry Service</span></span>

<span data-ttu-id="56dbe-196">Die **-Containerregistrierungsdienst** ist das Repository, das zum Hosten Ihrer Container verwendet.</span><span class="sxs-lookup"><span data-stu-id="56dbe-196">The **Container Registry Service** is the repository used to host your containers.</span></span>

<span data-ttu-id="56dbe-197">Die **IoT Hub-Dienst** , den Sie erstellen und verwenden Sie in diesem Kurs bezieht sich auf **-Containerregistrierungsdienst** zum Abrufen der Container in Ihrem Edge-Gerät bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-197">The **IoT Hub Service** that you will build and use in this course, refers to **Container Registry Service** to obtain the containers to deploy in your Edge Device.</span></span>

1. <span data-ttu-id="56dbe-198">Führen Sie zunächst diese [Link zum Azure-Portal](https://portal.azure.com/), und melden Sie sich mit Ihren Anmeldeinformationen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-198">First, follow this [link to the Azure Portal](https://portal.azure.com/), and login with your credentials.</span></span>

2. <span data-ttu-id="56dbe-199">Wechseln Sie zu **erstellen Sie eine Ressource** und suchen Sie nach **Containerregistrierung**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-199">Go to **Create a resource** and look for **Container Registry**.</span></span>

    ![Container Registry-Instanz](images/AzureLabs-Lab313-05.png)

3. <span data-ttu-id="56dbe-201">Klicken Sie auf **erstellen**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-201">Click on **Create**.</span></span>

    ![](images/AzureLabs-Lab313-06.png)

4. <span data-ttu-id="56dbe-202">Legen Sie den Dienst Setupparameter:</span><span class="sxs-lookup"><span data-stu-id="56dbe-202">Set the Service setup parameters:</span></span>

    1. <span data-ttu-id="56dbe-203">Fügen Sie einen Namen für Ihr Projekt, In diesem Beispiel die Hauptdateitabelle **IoTCRegistry**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-203">Insert a name for your project, In this example its called **IoTCRegistry**.</span></span>

    2. <span data-ttu-id="56dbe-204">Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-204">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="56dbe-205">Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, bereitzustellen und zu verwalten, Rechnungen für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-205">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="56dbe-206">Es wird empfohlen, alle zu bewahren, an die Azure-Dienste unter einer allgemeinen Ressourcengruppe mit einem einzelnen Projekt (z. B. z. B. diese Kurse) verknüpft ist).</span><span class="sxs-lookup"><span data-stu-id="56dbe-206">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    3. <span data-ttu-id="56dbe-207">Legen Sie den Speicherort des Diensts.</span><span class="sxs-lookup"><span data-stu-id="56dbe-207">Set the location of the Service.</span></span>

    4. <span data-ttu-id="56dbe-208">Legen Sie **Administratorbenutzer** zu **aktivieren**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-208">Set **Admin user** to **Enable**.</span></span>

    5. <span data-ttu-id="56dbe-209">Legen Sie **SKU** zu **grundlegende**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-209">Set **SKU** to **Basic**.</span></span> 

    ![](images/AzureLabs-Lab313-07.png)

5. <span data-ttu-id="56dbe-210">Klicken Sie auf **erstellen** und warten Sie, für die Dienste erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="56dbe-210">Click **Create** and wait for the Services to be created.</span></span> 

6. <span data-ttu-id="56dbe-211">Sobald eingeblendet, dass die Benachrichtigung darüber informiert Sie über die erfolgreiche Erstellung von der *Containerregistrierung*, klicken Sie auf **zu Ressource wechseln** Ihrer Dienst-Seite umgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="56dbe-211">Once the notification pops up informing you of the successful creation of the *Container Registry*, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![](images/AzureLabs-Lab313-08.png)

7. <span data-ttu-id="56dbe-212">In der *Containerregistrierung* Seite, klicken Sie auf **Zugriffsschlüssel**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-212">In the *Container Registry* Service page, click on **Access keys**.</span></span>

8. <span data-ttu-id="56dbe-213">Notieren Sie sich (Sie können Ihr Editor verwenden) die folgenden Parameter:</span><span class="sxs-lookup"><span data-stu-id="56dbe-213">Take note (you could use your Notepad) of the following parameters:</span></span>
    1. <span data-ttu-id="56dbe-214">**Login Server**</span><span class="sxs-lookup"><span data-stu-id="56dbe-214">**Login Server**</span></span>
    2. <span data-ttu-id="56dbe-215">**Benutzername**</span><span class="sxs-lookup"><span data-stu-id="56dbe-215">**Username**</span></span>
    3. <span data-ttu-id="56dbe-216">**Kennwort**</span><span class="sxs-lookup"><span data-stu-id="56dbe-216">**Password**</span></span>

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a><span data-ttu-id="56dbe-217">Kapitel 3 – IoT Hub-Dienst</span><span class="sxs-lookup"><span data-stu-id="56dbe-217">Chapter 3 - The IoT Hub Service</span></span>

<span data-ttu-id="56dbe-218">Nachdem Sie die Erstellung und Einrichtung von nun an Ihre **IoT Hub-Dienst**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-218">Now you will begin the creation and setup of your **IoT Hub Service**.</span></span>

1. <span data-ttu-id="56dbe-219">Wenn nicht bereits angemeldet, melden Sie sich bei der [Azure-Portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="56dbe-219">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="56dbe-220">Sobald Sie angemeldet sind, klicken Sie auf **erstellen Sie eine Ressource** in der oberen linken Ecke, und suchen Sie nach **IoT Hub**, und klicken Sie auf **EINGABETASTE**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-220">Once logged in, click on **Create a resource** in the top left corner, and search for **IoT Hub**, and click **Enter**.</span></span>

 ![Suchen Sie nach dem Storage-Konto](images/AzureLabs-Lab313-10.png)

3.  <span data-ttu-id="56dbe-222">Die neue Seite bietet eine Beschreibung der **Speicherkonto** Service.</span><span class="sxs-lookup"><span data-stu-id="56dbe-222">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="56dbe-223">Unten links der Aufforderung, klicken Sie auf die **erstellen** Schaltfläche, um eine Instanz dieses Diensts erstellen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-223">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![Storage-Instanz erstellen](images/AzureLabs-Lab313-11.png)

4.  <span data-ttu-id="56dbe-225">Nachdem Sie auf geklickt haben **erstellen**, wird ein Panel angezeigt:</span><span class="sxs-lookup"><span data-stu-id="56dbe-225">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="56dbe-226">Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-226">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="56dbe-227">Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-227">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="56dbe-228">Es wird empfohlen, alle zu bewahren, an die Azure-Dienste unter einer allgemeinen Ressourcengruppe mit einem einzelnen Projekt (z. B. z. B. diese Kurse) verknüpft ist).</span><span class="sxs-lookup"><span data-stu-id="56dbe-228">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="56dbe-229">Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, befolgen Sie diese [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="56dbe-229">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>


    2. <span data-ttu-id="56dbe-230">Wählen Sie einen geeigneten **Speicherort** (verwenden Sie am gleichen Speicherort für alle Dienste, die Sie in diesem Kurs erstellen).</span><span class="sxs-lookup"><span data-stu-id="56dbe-230">Select an appropriate **Location** (Use the same location across all the Services you create in this course).</span></span>

    3. <span data-ttu-id="56dbe-231">Fügen Sie Ihre bevorzugte **Namen** für diese Dienstinstanz.</span><span class="sxs-lookup"><span data-stu-id="56dbe-231">Insert your desired **Name** for this Service instance.</span></span>    

5.  <span data-ttu-id="56dbe-232">Klicken Sie auf den unteren Rand der Seite auf **weiter: Größe und Skalierung**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-232">On the bottom of the page click on **Next: Size and scale**.</span></span>

    ![Storage-Instanz erstellen](images/AzureLabs-Lab313-12.png)

6.  <span data-ttu-id="56dbe-234">Auf dieser Seite Wählen Sie Ihre **Tarif und Skalierung** (ist dies Ihre erste IoT Hub-Dienst-Instanz, ein freier-Tarif muss Ihnen zur Verfügung).</span><span class="sxs-lookup"><span data-stu-id="56dbe-234">In this page, select your **Pricing and scale tier** (if this is your first IoT Hub Service instance, a free tier should be available to you).</span></span>  

7.  <span data-ttu-id="56dbe-235">Klicken Sie auf **überprüfen + erstellen**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-235">Click on **Review + Create**.</span></span>

    ![Storage-Instanz erstellen](images/AzureLabs-Lab313-13.png)

8.  <span data-ttu-id="56dbe-237">Überprüfen Sie die Einstellungen, und klicken Sie auf **erstellen**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-237">Review your settings and click on **Create**.</span></span>

    ![Storage-Instanz erstellen](images/AzureLabs-Lab313-14.png)

9. <span data-ttu-id="56dbe-239">Sobald eingeblendet, dass die Benachrichtigung darüber informiert Sie über die erfolgreiche Erstellung der *IoT Hub* -Dienst, klicken Sie auf **zu Ressource wechseln** Ihrer Dienst-Seite umgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="56dbe-239">Once the notification pops up informing you of the successful creation of the *IoT Hub* Service, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![Storage-Instanz erstellen](images/AzureLabs-Lab313-15.png)

10. <span data-ttu-id="56dbe-241">Der Seitenleiste links scrollen, bis Sie sehen *automatische Geräteverwaltung*, die auf **IoT Edge**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-241">Scroll the side panel on the left until you see *Automatic Device Management*, the click on **IoT Edge**.</span></span>

    ![Storage-Instanz erstellen](images/AzureLabs-Lab313-16.png)

11. <span data-ttu-id="56dbe-243">Klicken Sie im Fenster, das auf der rechten Seite angezeigt wird, auf **IoT Edge-Gerät hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-243">In the window that appears to the right, click on **Add IoT Edge Device**.</span></span> <span data-ttu-id="56dbe-244">Ein Blatt wird auf der rechten Seite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="56dbe-244">A blade will appear to the right.</span></span>

12. <span data-ttu-id="56dbe-245">Geben Sie auf dem Blatt, das neue Gerät einen **Geräte-ID** (einen Namen Ihrer Wahl).</span><span class="sxs-lookup"><span data-stu-id="56dbe-245">In the blade, provide your new device a **Device ID** (a name of your choice).</span></span> <span data-ttu-id="56dbe-246">Klicken Sie auf **speichern**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-246">Then, click **Save**.</span></span> <span data-ttu-id="56dbe-247">Die *primären* und *Sekundärschlüssel* automatisch generiert, wenn man **automatisch generieren** ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="56dbe-247">The *Primary* and *Secondary Keys* will auto generate, if you have **Auto Generate** ticked.</span></span>

    ![Storage-Instanz erstellen](images/AzureLabs-Lab313-17.png)

13. <span data-ttu-id="56dbe-249">Sie gelangen zurück auf die *IoT Edge-Geräte* Abschnitt, in dem das neue Gerät aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="56dbe-249">You will navigate back to the *IoT Edge Devices* section, where your new device will be listed.</span></span> <span data-ttu-id="56dbe-250">Klicken Sie auf das neue Gerät (rot markiert, in der folgenden Abbildung).</span><span class="sxs-lookup"><span data-stu-id="56dbe-250">Click on your new device (outlined in red in the below image).</span></span> 

    ![Storage-Instanz erstellen](images/AzureLabs-Lab313-18.png)

14. <span data-ttu-id="56dbe-252">Auf der *Gerätedetails* Seite, die angezeigt wird, erstellen Sie eine Kopie der **Verbindungszeichenfolge** (Primärschlüssel).</span><span class="sxs-lookup"><span data-stu-id="56dbe-252">On the *Device Details* page that appears, take a copy of the **Connection String** (primary key).</span></span>

    ![Storage-Instanz erstellen](images/AzureLabs-Lab313-19.png)

15. <span data-ttu-id="56dbe-254">Kehren Sie zurück zum Bereich auf der linken Seite, und klicken Sie auf *Richtlinien für gemeinsamen Zugriff*, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-254">Go back to the panel on the left, and click *Shared access policies*, to open it.</span></span> 

16. <span data-ttu-id="56dbe-255">Klicken Sie auf der daraufhin angezeigten Dialogfeld auf **Iothubowner**, und ein Blatt wird angezeigt, die den rechten Rand des Bildschirms.</span><span class="sxs-lookup"><span data-stu-id="56dbe-255">On the page that appears, click **iothubowner**, and a blade will appear to the right of the screen.</span></span> 

17. <span data-ttu-id="56dbe-256">Achten Sie darauf (in Ihrem Editor) des der **Verbindungszeichenfolge** (Primärschlüssel), für die spätere Verwendung beim Festlegen der *Verbindungszeichenfolge* auf Ihrem Gerät.</span><span class="sxs-lookup"><span data-stu-id="56dbe-256">Take note (on your Notepad) of the **Connection string** (primary key), for later use when setting the *Connection String* to your device.</span></span>

    ![Storage-Instanz erstellen](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a><span data-ttu-id="56dbe-258">Kapitel 4: Einrichten der Entwicklungsumgebung</span><span class="sxs-lookup"><span data-stu-id="56dbe-258">Chapter 4 - Setting up the development environment</span></span>

<span data-ttu-id="56dbe-259">Zum Erstellen und Bereitstellen von Modulen für *IoT Hub-Edge*, benötigen Sie die folgenden Komponenten auf Ihrem Entwicklungscomputer mit Windows 10 installiert:</span><span class="sxs-lookup"><span data-stu-id="56dbe-259">In order to create and deploy modules for *IoT Hub Edge*, you will require the following components installed on your development machine running Windows 10:</span></span>

1.  <span data-ttu-id="56dbe-260">[Docker für Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), fordert Sie zum Erstellen eines Kontos ein, um das Herunterladen zu können.</span><span class="sxs-lookup"><span data-stu-id="56dbe-260">[Docker for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), it will ask you to create an account to be able to download.</span></span> 

    <span data-ttu-id="56dbe-261">[![Docker für Windows herunterladen](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span><span class="sxs-lookup"><span data-stu-id="56dbe-261">[![download docker for windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="56dbe-262">Erfordert Docker *Windows 10 PRO*, *Enterprise 14393*, oder *Windows Server 2016 RTM*, um auszuführen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-262">Docker requires *Windows 10 PRO*, *Enterprise 14393*, or *Windows Server 2016 RTM*, to run.</span></span> <span data-ttu-id="56dbe-263">Wenn Sie andere Versionen von Windows 10 ausgeführt werden, können Sie versuchen, installieren Docker mit der [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).</span><span class="sxs-lookup"><span data-stu-id="56dbe-263">If you are running other versions of Windows 10, you can try installing Docker using the [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).</span></span>

2.  <span data-ttu-id="56dbe-264">[Python 3.6](https://www.python.org/downloads/).</span><span class="sxs-lookup"><span data-stu-id="56dbe-264">[Python 3.6](https://www.python.org/downloads/).</span></span>

    <span data-ttu-id="56dbe-265">[![Laden Sie Python 3.6 herunter.](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span><span class="sxs-lookup"><span data-stu-id="56dbe-265">[![download python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span></span>

3.  <span data-ttu-id="56dbe-266">[Visual Studio Code (auch bekannt als VS Code)](https://code.visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="56dbe-266">[Visual Studio Code (also known as VS Code)](https://code.visualstudio.com/download).</span></span>

    <span data-ttu-id="56dbe-267">[![Herunterladen von Visual Studio Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span><span class="sxs-lookup"><span data-stu-id="56dbe-267">[![download VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span></span>

<span data-ttu-id="56dbe-268">Nach der Installation der oben genannten Software, müssen Sie den Computer neu starten.</span><span class="sxs-lookup"><span data-stu-id="56dbe-268">After installing the software mentioned above, you will need to restart your machine.</span></span>

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a><span data-ttu-id="56dbe-269">Kapitel 5: Einrichten der Ubuntu-Umgebung</span><span class="sxs-lookup"><span data-stu-id="56dbe-269">Chapter 5 - Setting up the Ubuntu environment</span></span>

<span data-ttu-id="56dbe-270">Nachdem Sie verschieben können, um die Einrichtung Ihres Geräts **mit Ubuntu-Betriebssystem**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-270">Now you can move on to setting up your device **running Ubuntu OS**.</span></span> <span data-ttu-id="56dbe-271">Folgenden Sie die Schritte, installieren Sie die erforderliche Software, um Ihre Container in Ihrem Board bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="56dbe-271">Follow the steps below, to install the necessary software, to deploy your containers on your board:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="56dbe-272">Sie sollten immer die terminal-Befehlen mit voranstellen **"sudo"** als Administrator ausführen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-272">You should always precede the terminal commands with **sudo** to run as admin user.</span></span> <span data-ttu-id="56dbe-273">i.e:</span><span class="sxs-lookup"><span data-stu-id="56dbe-273">i.e:</span></span>
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  <span data-ttu-id="56dbe-274">Öffnen der **Ubuntu Terminal**, und verwenden Sie den folgenden Befehl, um installieren **Pip**:</span><span class="sxs-lookup"><span data-stu-id="56dbe-274">Open the **Ubuntu Terminal**, and use the following command to install **pip**:</span></span>

    > [! Hinweis]<span data-ttu-id="56dbe-275"> Sie können öffnen \*Terminal* ganz einfach über die Tastenkombination: *\*Ctrl + Alt + T*\*.</span><span class="sxs-lookup"><span data-stu-id="56dbe-275"> You can open \*Terminal* very easily through using the keyboard shortcut: *\*Ctrl + Alt + T*\*.</span></span>

    ```bash
        sudo apt-get install python-pip
    ```

2.  <span data-ttu-id="56dbe-276">In diesem Kapitel werden Sie möglicherweise aufgefordert, durch *Terminal*, für die Berechtigung zum Verwenden des Gerätespeichers und für Sie zur Eingabe **j/n** (Ja oder Nein), Typ **'y'**, und drücken Sie dann die **EINGABETASTE** Schlüssel, um zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="56dbe-276">Throughout this Chapter, you may be prompted, by *Terminal*, for permission to use your device storage, and for you to input **y/n** (yes or no), type **'y'**, and then press the **Enter** key, to accept.</span></span>

3.  <span data-ttu-id="56dbe-277">Wenn dieser Befehl abgeschlossen ist, verwenden Sie den folgenden Befehl zum Installieren **curl**:</span><span class="sxs-lookup"><span data-stu-id="56dbe-277">Once that command has completed, use the following command to install **curl**:</span></span>

    ```bash
        sudo apt install curl
    ```

4.  <span data-ttu-id="56dbe-278">Einmal **Pip** und **curl** sind installiert sind, verwenden Sie den folgenden Befehl zum Installieren der **IoT Edge-Laufzeit**, dies ist erforderlich zum Bereitstellen und steuern die Module in Ihrem Board:</span><span class="sxs-lookup"><span data-stu-id="56dbe-278">Once **pip** and **curl** are installed, use the following command to install the **IoT Edge runtime**, this is necessary to deploy and control the modules on your board:</span></span>

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. <span data-ttu-id="56dbe-279">An diesem Punkt werden Sie aufgefordert, öffnen Sie die *Config-Datei der Common Language Runtime*, zum Einfügen der **Device Connection String**, die Sie notiert (in Ihrem Editor), beim Erstellen der **IoT Hub-Dienst**  ([in Schritt 14, Kapitel 3](#chapter-3---the-iot-hub-service)).</span><span class="sxs-lookup"><span data-stu-id="56dbe-279">At this point you will be prompted to open up the *runtime config file*, to insert the **Device Connection String**, that you noted down (in your Notepad), when creating the **IoT Hub Service** ([at step 14, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="56dbe-280">Führen Sie die folgende Zeile, auf das Terminal aus, um diese Datei öffnen:</span><span class="sxs-lookup"><span data-stu-id="56dbe-280">Run the following line on the terminal to open that file:</span></span>

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. <span data-ttu-id="56dbe-281">Die **config.yaml** Datei werden angezeigt, für die Bearbeitung bereit:</span><span class="sxs-lookup"><span data-stu-id="56dbe-281">The **config.yaml** file will be displayed, ready for you to edit:</span></span>

    > [!WARNING]
    > <span data-ttu-id="56dbe-282">Wenn diese Datei geöffnet wird, kann es etwas verwirrend sein.</span><span class="sxs-lookup"><span data-stu-id="56dbe-282">When this file opens, it may be somewhat confusing.</span></span> <span data-ttu-id="56dbe-283">Sie werden zur Textbearbeitung dieser Datei in die *Terminal* selbst.</span><span class="sxs-lookup"><span data-stu-id="56dbe-283">You will be text editing this file, within the *Terminal* itself.</span></span> 

    1.  <span data-ttu-id="56dbe-284">Verwenden Sie die Pfeiltasten auf der Tastatur, um einen Bildlauf nach unten (Sie benötigen Sie einen Bildlauf eine kleine Methode), erreicht der Zeile mit ":</span><span class="sxs-lookup"><span data-stu-id="56dbe-284">Use the arrow keys on your keyboard to scroll down (you will need to scroll down a little way), to reach the line containing":</span></span>

        <span data-ttu-id="56dbe-285">"**\<GERÄTEVERBINDUNGSZEICHENFOLGE HIER HINZUFÜGEN &GT;**".</span><span class="sxs-lookup"><span data-stu-id="56dbe-285">"**\<ADD DEVICE CONNECTION STRING HERE>**".</span></span>

    2. <span data-ttu-id="56dbe-286">Ersetzen der Zeile **einschließlich der Klammern**, mit der **Device Connection String** Sie zuvor notiert haben.</span><span class="sxs-lookup"><span data-stu-id="56dbe-286">Substitute line, **including the brackets**, with the **Device Connection String** you have noted earlier.</span></span>

7. <span data-ttu-id="56dbe-287">Mit der Verbindungszeichenfolge vorhanden, auf der Tastatur, und drücken Sie die **STRG + X** Schlüssel zum Speichern der Datei.</span><span class="sxs-lookup"><span data-stu-id="56dbe-287">With your Connection String in place, on your keyboard, press the **Ctrl-X** keys to save the file.</span></span> <span data-ttu-id="56dbe-288">Werden sie aufgefordert zu bestätigen, indem Sie die Eingabe **Y**. Drücken Sie dann die **EINGABETASTE** Schlüssel, um zu bestätigen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-288">It will ask you to confirm by typing **Y**. Then, press the **Enter** key, to confirm.</span></span> <span data-ttu-id="56dbe-289">Sie kehren zurück zu den regulären *Terminal*.</span><span class="sxs-lookup"><span data-stu-id="56dbe-289">You will go back to the regular *Terminal*.</span></span> 

8. <span data-ttu-id="56dbe-290">Nachdem diese Befehle alle erfolgreich ausgeführt haben, Sie installiert die **IoT Edge-Runtime**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-290">Once these commands have all run successfully, you will have installed the **IoT Edge Runtime**.</span></span> <span data-ttu-id="56dbe-291">Nach der Initialisierung der Runtime wird auf eine eigene jedes Mal, die das Gerät eingeschaltet wird gestartet und wird im Hintergrund, warten auf Module für die Bereitstellung befinden die **IoT Hub-Dienst**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-291">Once initialized, the runtime will start on its own every time the device is powered up, and will sit in the background, waiting for modules to be deployed from the **IoT Hub Service**.</span></span>

9.  <span data-ttu-id="56dbe-292">Führen Sie die folgende Befehlszeile zum Initialisieren der *IoT Edge-Runtime*:</span><span class="sxs-lookup"><span data-stu-id="56dbe-292">Run the following command line to initialize the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="56dbe-293">Wenn Sie die yaml-Datei, oder das oben beschriebene Setup ändern, müssen Sie in diesem Fall führen Sie die obige Zeile für den Neustart innerhalb *Terminal*.</span><span class="sxs-lookup"><span data-stu-id="56dbe-293">If you make changes to your .yaml file, or the above setup, you will need to run the above restart line again, within *Terminal*.</span></span>

10. <span data-ttu-id="56dbe-294">Überprüfen Sie die *IoT Edge-Runtime* Status, indem Sie die folgende Befehlszeile ausführen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-294">Check the *IoT Edge Runtime* status by running the following command line.</span></span> <span data-ttu-id="56dbe-295">Die Laufzeit sollte angezeigt werden, mit dem Status **Active (aktiv)** in grüner Schrift.</span><span class="sxs-lookup"><span data-stu-id="56dbe-295">The runtime should appear with the status **active (running)** in green text.</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

11. <span data-ttu-id="56dbe-296">Drücken Sie die **STRG + C** Schlüssel, um die Seite "Status" beendet.</span><span class="sxs-lookup"><span data-stu-id="56dbe-296">Press the **Ctrl-C** keys, to exit the status page.</span></span> <span data-ttu-id="56dbe-297">Sie können überprüfen, ob die *IoT Edge-Runtime* geladen Container ordnungsgemäß durch den folgenden Befehl eingeben:</span><span class="sxs-lookup"><span data-stu-id="56dbe-297">You can verify that the *IoT Edge Runtime* is pulling the containers correctly by typing the following command:</span></span>

    ```bash
        sudo docker ps
    ```

12. <span data-ttu-id="56dbe-298">Eine Liste mit Containern zwei (2) sollte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="56dbe-298">A list with two (2) containers should appear.</span></span> <span data-ttu-id="56dbe-299">Hierbei handelt es sich um die Standardmodule, die vom IoT Hub-Dienst (EdgeAgent und EdgeHub) automatisch erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="56dbe-299">These are the default modules that are automatically created by the IoT Hub Service (edgeAgent and edgeHub).</span></span> <span data-ttu-id="56dbe-300">Nachdem Sie erstellen und Ihrer eigenen Module bereitstellen, werden sie in dieser Liste, darunter die Standardfarben angezeigt.</span><span class="sxs-lookup"><span data-stu-id="56dbe-300">Once you create and deploy your own modules, they will appear in this list, underneath the default ones.</span></span>

## <a name="chapter-6---install-the-extensions"></a><span data-ttu-id="56dbe-301">Kapitel 6: Installieren der Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="56dbe-301">Chapter 6 - Install the extensions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="56dbe-302">Den nächsten Kapiteln (6 bis 9) sind auf Ihrem Windows 10-Computer ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="56dbe-302">The next few Chapters (6-9) are to be performed on your Windows 10 machine.</span></span>

1. <span data-ttu-id="56dbe-303">Open **Vscode**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-303">Open **VS Code**.</span></span>

2. <span data-ttu-id="56dbe-304">Klicken Sie auf die **Erweiterungen** (Quadrat) Schaltfläche auf der linken Leiste von VS Code zum Öffnen der **Erweiterungsbereich**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-304">Click on the **Extensions** (square) button on the left bar of VS Code, to open the **Extensions panel**.</span></span>

3. <span data-ttu-id="56dbe-305">Suchen Sie nach, und installieren Sie, die folgenden Erweiterungen (wie in der folgenden Abbildung gezeigt):</span><span class="sxs-lookup"><span data-stu-id="56dbe-305">Search for, and install, the following extensions (as shown in the image below):</span></span>

    1. <span data-ttu-id="56dbe-306">Azure IoT Edge</span><span class="sxs-lookup"><span data-stu-id="56dbe-306">Azure IoT Edge</span></span>
    2. <span data-ttu-id="56dbe-307">Azure IoT Toolkit</span><span class="sxs-lookup"><span data-stu-id="56dbe-307">Azure IoT Toolkit</span></span>
    3. <span data-ttu-id="56dbe-308">Docker</span><span class="sxs-lookup"><span data-stu-id="56dbe-308">Docker</span></span>   

    ![Erstellen Sie Ihres Containers](images/AzureLabs-Lab313-24.png)

4. <span data-ttu-id="56dbe-310">Nachdem die Erweiterungen installiert sind, schließen Sie und erneut öffnen Sie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="56dbe-310">Once the extensions are installed, close and re-open VS Code.</span></span>

5. <span data-ttu-id="56dbe-311">Klicken Sie mit Visual Studio Code einmal öffnen, navigieren Sie zu **anzeigen > integriertes Terminal**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-311">With VS Code open once more, navigate to **View > Integrated terminal**.</span></span>

6. <span data-ttu-id="56dbe-312">Installieren Sie jetzt **Cookiecutter**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-312">You will now install **Cookiecutter**.</span></span> <span data-ttu-id="56dbe-313">Führen Sie im Terminal den folgenden Bash-Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="56dbe-313">In the terminal run the following bash command:</span></span>

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! Hinweis]<span data-ttu-id="56dbe-314"> Wenn Sie schwierigkeiten mit dem folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="56dbe-314"> If you have trouble with this command:</span></span> 
    >1. <span data-ttu-id="56dbe-315">Starten Sie VS Code und / oder auf dem Computer neu.</span><span class="sxs-lookup"><span data-stu-id="56dbe-315">Restart VS Code, and/ or your computer.</span></span>
    >2. <span data-ttu-id="56dbe-316">Es kann erforderlich sein, wechseln die **VS Code-Terminal** mit dem Sie verwenden bereits, installieren Python, d. h. **Powershell** (insbesondere im Fall, dass die Python-Umgebung bereits auf Ihrem Computer installiert wurde).</span><span class="sxs-lookup"><span data-stu-id="56dbe-316">It might be necessary to switch the **VS Code Terminal** to the one you have been using to install Python, i.e. **Powershell** (especially in case the Python environment was already installed on your machine).</span></span> <span data-ttu-id="56dbe-317">Das Terminal geöffnet ist finden Sie im Dropdown-Menü auf der rechten Seite des Terminals.</span><span class="sxs-lookup"><span data-stu-id="56dbe-317">With the Terminal open, you will find the drop down menu on the right side of the Terminal.</span></span>
     <span data-ttu-id="56dbe-318">![Erstellen Sie Ihres Containers](images/AzureLabs-Lab313-24b.png)</span><span class="sxs-lookup"><span data-stu-id="56dbe-318">![Create your container](images/AzureLabs-Lab313-24b.png)</span></span> 
    >3. <span data-ttu-id="56dbe-319">Stellen Sie sicher, dass die **Python** Installationspfad wurde als **Umgebungsvariable** auf Ihrem Computer.</span><span class="sxs-lookup"><span data-stu-id="56dbe-319">Make sure the **Python** installation path is added as **Environment Variable** on your machine.</span></span> <span data-ttu-id="56dbe-320">Cookiecutter muss Teil der gleichen Pfad zum Speicherort.</span><span class="sxs-lookup"><span data-stu-id="56dbe-320">Cookiecutter should be part of the same location path.</span></span> <span data-ttu-id="56dbe-321">Führen Sie dies [Link, um weitere Informationen zu den Umgebungsvariablen](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span><span class="sxs-lookup"><span data-stu-id="56dbe-321">Please follow this [link for more information on Environment Variables](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span></span> 

7. <span data-ttu-id="56dbe-322">Einmal **Cookiecutter** wurde installiert, sollten Sie Ihre Computer neu starten, damit **Cookiecutter** als einen Befehl innerhalb des Systems Umgebung erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="56dbe-322">Once **Cookiecutter** has finished installing, you should restart your machine, so that **Cookiecutter** is recognized as a command, within your System's environment.</span></span>

## <a name="chapter-7---create-your-container-solution"></a><span data-ttu-id="56dbe-323">Kapitel 7: Erstellen einer containerlösung</span><span class="sxs-lookup"><span data-stu-id="56dbe-323">Chapter 7 - Create your container solution</span></span>

<span data-ttu-id="56dbe-324">An diesem Punkt müssen Sie den Container zu erstellen, mit dem Modul in mithilfe von Push übertragen werden die *Containerregistrierung*.</span><span class="sxs-lookup"><span data-stu-id="56dbe-324">At this point, you need to create the container, with the module, to be pushed into the *Container Registry*.</span></span> <span data-ttu-id="56dbe-325">Nachdem Sie Ihren Container mithilfe von Push übertragen haben, verwenden Sie die *IoT Hub-Edge* Service sie auf Ihrem Gerät bereitstellen, die ausgeführt wird die *IoT Edge-Laufzeit*.</span><span class="sxs-lookup"><span data-stu-id="56dbe-325">Once you have pushed your container, you will use the *IoT Hub Edge* Service to deploy it to your device, which is running the *IoT Edge runtime*.</span></span>

1. <span data-ttu-id="56dbe-326">Klicken Sie in Visual Studio Code auf **Ansicht > befehlspalette**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-326">From VS Code, click **View > Command palette**.</span></span>

2. <span data-ttu-id="56dbe-327">Suchen Sie in der Palette, und führen Sie **Azure IoT Edge: Neues Iot Edge-Projektmappe**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-327">In the palette, search and run **Azure IoT Edge: New Iot Edge Solution**.</span></span>

3. <span data-ttu-id="56dbe-328">Navigieren Sie an einem Speicherort, in der Sie Ihre Lösung erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="56dbe-328">Browse into a location where you want to create your solution.</span></span> <span data-ttu-id="56dbe-329">Drücken Sie die **EINGABETASTE** Schlüssel, um den Speicherort zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="56dbe-329">Press the **Enter** key, to accept the location.</span></span>

4. <span data-ttu-id="56dbe-330">Geben Sie einen Namen zu Ihrer Projektmappe ein.</span><span class="sxs-lookup"><span data-stu-id="56dbe-330">Give a name to your solution.</span></span> <span data-ttu-id="56dbe-331">Drücken Sie die **EINGABETASTE** Schlüssel, um Ihre angegebene Name zu bestätigen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-331">Press the **Enter** key, to confirm your provided name.</span></span>

5. <span data-ttu-id="56dbe-332">Jetzt werden Sie aufgefordert werden, wählen Sie die Vorlage-Framework für Ihre Lösung.</span><span class="sxs-lookup"><span data-stu-id="56dbe-332">Now you will be prompted to choose the template framework for your solution.</span></span> <span data-ttu-id="56dbe-333">Klicken Sie auf **Python-Modul**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-333">Click **Python Module**.</span></span> <span data-ttu-id="56dbe-334">Drücken Sie die **EINGABETASTE** Schlüssel, um diese Auswahl zu bestätigen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-334">Press the **Enter** key, to confirm this choice.</span></span>

6. <span data-ttu-id="56dbe-335">Geben Sie einen Namen für Ihr Modul ein.</span><span class="sxs-lookup"><span data-stu-id="56dbe-335">Give a name to your module.</span></span> <span data-ttu-id="56dbe-336">Drücken Sie die **EINGABETASTE** Schlüssel, um den Namen Ihres Moduls zu bestätigen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-336">Press the **Enter** key, to confirm the name of your module.</span></span> <span data-ttu-id="56dbe-337">Stellen Sie sicher, dass sich (mit Ihrem Editor) den Namen des Moduls, zu nutzen, da sie später verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="56dbe-337">Make sure to take a note (with your Notepad) of the module name, as it is used later.</span></span>

7. <span data-ttu-id="56dbe-338">Sie sehen eine vorgefertigte *Docker-Image-Repository* Adresse wird auf der Palette angezeigt.</span><span class="sxs-lookup"><span data-stu-id="56dbe-338">You will notice a pre-built *Docker Image Repository* address will appear on the palette.</span></span> <span data-ttu-id="56dbe-339">Es sieht so aus wie:</span><span class="sxs-lookup"><span data-stu-id="56dbe-339">It will look like:</span></span>

    <span data-ttu-id="56dbe-340">**Localhost:5000/der Namen von IHREM Modul -**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-340">**localhost:5000/-THE NAME OF YOUR MODULE-**.</span></span> 

8. <span data-ttu-id="56dbe-341">Löschen **Localhost:5000**, und in seiner Stelle einfügen der *Containerregistrierung* **Anmeldeserver** Adresse, die Sie notiert, beim Erstellen haben der **Container Registrierungsdienst** ([in Schritt 8, Kapitel 2](#chapter-2---the-container-registry-service)).</span><span class="sxs-lookup"><span data-stu-id="56dbe-341">Delete **localhost:5000**, and in its place insert the *Container Registry* **Login Server** address, which you noted when creating the **Container Registry Service** ([in step 8, of Chapter 2](#chapter-2---the-container-registry-service)).</span></span> <span data-ttu-id="56dbe-342">Drücken Sie die **EINGABETASTE** Schlüssel, um die Adresse zu bestätigen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-342">Press the **Enter** key, to confirm the address.</span></span>

9. <span data-ttu-id="56dbe-343">An diesem Punkt wird die Lösung, mit der Vorlage für Ihre Python-Modul erstellt und in die Struktur angezeigt der **Registerkarte "Durchsuchen"**, der VS Code auf der linken Seite des Bildschirms.</span><span class="sxs-lookup"><span data-stu-id="56dbe-343">At this point, the solution containing the template for your Python module will be created and its structure will be displayed in the **Explore Tab**, of VS Code, on the left side of the screen.</span></span> <span data-ttu-id="56dbe-344">Wenn die **Registerkarte "Durchsuchen"** ist nicht geöffnet ist, können Sie sie öffnen auf die oberste Schaltfläche klicken, in der Leiste auf der linken Seite.</span><span class="sxs-lookup"><span data-stu-id="56dbe-344">If the **Explore Tab** is not open, you can open it by clicking the top-most button, in the bar on the left.</span></span>

    ![Erstellen Sie Ihres Containers](images/AzureLabs-Lab313-25.png)

10. <span data-ttu-id="56dbe-346">Der letzte Schritt zum diesem Kapitel wird, klicken Sie auf, und Öffnen der **env-Datei**, innerhalb der **Registerkarte "Durchsuchen"**, und fügen Ihre *Containerregistrierung* **Benutzername** und **Kennwort**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-346">The last step for this Chapter, is to click and open the **.env file**, from within the **Explore Tab**, and add your *Container Registry* **username** and **password**.</span></span> <span data-ttu-id="56dbe-347">Diese Datei wird von Git ignoriert, aber zur Erstellung wird der Container, legen Sie die Anmeldeinformationen den Zugriff auf die **-Containerregistrierungsdienst**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-347">This file is ignored by git, but on building the container, will set the credentials to access the **Container Registry Service**.</span></span>

    ![Erstellen Sie Ihres Containers](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a><span data-ttu-id="56dbe-349">Kapitel 8 – bearbeiten Ihre containerlösung</span><span class="sxs-lookup"><span data-stu-id="56dbe-349">Chapter 8 - Editing your container solution</span></span>

<span data-ttu-id="56dbe-350">Sie werden jetzt die Container-Lösung, schließen, indem Sie die folgenden Dateien werden aktualisiert:</span><span class="sxs-lookup"><span data-stu-id="56dbe-350">You will now complete the container solution, by updating the following files:</span></span>

- <span data-ttu-id="56dbe-351">*Main<span></span>py* Python-Skript.</span><span class="sxs-lookup"><span data-stu-id="56dbe-351">*main<span></span>.py* python script.</span></span>
- <span data-ttu-id="56dbe-352">*requirements.txt*.</span><span class="sxs-lookup"><span data-stu-id="56dbe-352">*requirements.txt*.</span></span>
- <span data-ttu-id="56dbe-353">*deployment.template.json*.</span><span class="sxs-lookup"><span data-stu-id="56dbe-353">*deployment.template.json*.</span></span>
- <span data-ttu-id="56dbe-354">*Dockerfile.amd64*</span><span class="sxs-lookup"><span data-stu-id="56dbe-354">*Dockerfile.amd64*</span></span>

<span data-ttu-id="56dbe-355">Erstellen Sie dann die *Images* Ordner ein, das Python-Skript für die prüfen, ob Bilder für den Abgleich Ihrer *Modell für benutzerdefiniertes maschinelles sehen*.</span><span class="sxs-lookup"><span data-stu-id="56dbe-355">You will then create the *images* folder, used by the python script to check for images to match against your *Custom Vision model*.</span></span> <span data-ttu-id="56dbe-356">Fügen Sie abschließend die *labels.txt* -Datei, um Hilfe, lesen Sie das Modell und die *model.pb* -Datei, die das Modell ist.</span><span class="sxs-lookup"><span data-stu-id="56dbe-356">Lastly, you will add the *labels.txt* file, to help read your model, and the *model.pb* file, which is your model.</span></span>

1. <span data-ttu-id="56dbe-357">Klicken Sie mit Visual Studio Code öffnen, navigieren Sie zu Ihrem Ordner "Module", und suchen Sie für das Skript mit dem Namen **main<span></span>py**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-357">With VS Code open, navigate to your module folder, and look for the script called **main<span></span>.py**.</span></span> <span data-ttu-id="56dbe-358">Doppelklicken Sie auf diese Option, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-358">Double-click to open it.</span></span>

2. <span data-ttu-id="56dbe-359">Löschen Sie den Inhalt der Datei, und fügen Sie den folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="56dbe-359">Delete the content of the file and insert the following code:</span></span>

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  <span data-ttu-id="56dbe-360">Öffnen Sie die Datei mit dem Namen **"Requirements.txt"**, und Ersetzen Sie den Inhalt durch Folgendes:</span><span class="sxs-lookup"><span data-stu-id="56dbe-360">Open the file called **requirements.txt**, and substitute its content with the following:</span></span>

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  <span data-ttu-id="56dbe-361">Öffnen Sie die Datei mit dem Namen **deployment.template.json**, und Ersetzen Sie den Inhalt nach der folgenden Richtlinie:</span><span class="sxs-lookup"><span data-stu-id="56dbe-361">Open the file called **deployment.template.json**, and substitute its content following the below guideline:</span></span>

    1. <span data-ttu-id="56dbe-362">Da Sie Ihre eigenen, eindeutige, JSON-Struktur besitzt, müssen Sie es von hand bearbeiten (statt ein Beispiel für das Kopieren).</span><span class="sxs-lookup"><span data-stu-id="56dbe-362">Because you will have your own, unique, JSON structure, you will need to edit it by hand (rather than copying an example).</span></span> <span data-ttu-id="56dbe-363">Um dies zu vereinfachen, verwenden Sie die folgenden Abbildung als Anleitung.</span><span class="sxs-lookup"><span data-stu-id="56dbe-363">To make this easy, use the below image as a guide.</span></span>
    2. <span data-ttu-id="56dbe-364">Bereiche, die mit Ihrer, anders aussehen, aber die Sie **sollte nicht geändert werden gelb hervorgehoben werden**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-364">Areas which will look different to yours, but which you **should NOT change are highlighted yellow**.</span></span>
    3. <span data-ttu-id="56dbe-365">**Abschnitte, die Sie benötigen, löschen, werden ein rot hervorgehoben.**</span><span class="sxs-lookup"><span data-stu-id="56dbe-365">**Sections which you need to delete, are a highlighted red.**</span></span>
    4. <span data-ttu-id="56dbe-366">Achten Sie darauf, dass Sie die richtigen Klammern zu löschen, und auch entfernen Sie, die Kommas.</span><span class="sxs-lookup"><span data-stu-id="56dbe-366">Be careful to delete the correct brackets, and also remove the commas.</span></span>

        ![Erstellen Sie Ihres Containers](images/AzureLabs-Lab313-27.png)

    5. <span data-ttu-id="56dbe-368">Der vollständige JSON-Code sollte wie in der folgenden Abbildung aussehen (jedoch mit Ihrer eindeutigen unterschieden: *Benutzername/Kennwort/Modul Name/Modulverweisen*):</span><span class="sxs-lookup"><span data-stu-id="56dbe-368">The completed JSON should look like the following image (though, with your unique differences: *username/password/module name/module references*):</span></span>

        ![Erstellen Sie Ihres Containers](images/AzureLabs-Lab313-28.png)

5.  <span data-ttu-id="56dbe-370">Öffnen Sie die Datei mit dem Namen **Dockerfile.amd64**, und Ersetzen Sie den Inhalt durch Folgendes:</span><span class="sxs-lookup"><span data-stu-id="56dbe-370">Open the file called **Dockerfile.amd64**, and substitute its content with the following:</span></span>

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  <span data-ttu-id="56dbe-371">Mit der rechten Maustaste auf den Ordner, unter **Module** (er weist den Namen, die Sie zuvor; angegeben im Beispiel weiter nach unten, es heißt *Pythonmodule*), und klicken Sie auf **neuer Ordner**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-371">Right-click on the folder beneath **modules** (it will have the name you provided previously; in the example further down, it is called *pythonmodule*), and click on **New Folder**.</span></span> <span data-ttu-id="56dbe-372">Nennen Sie den Ordner **Images**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-372">Name the folder **images**.</span></span>

7.  <span data-ttu-id="56dbe-373">Fügen Sie dem Ordner einige Images, die mit der Maus oder Tastatur.</span><span class="sxs-lookup"><span data-stu-id="56dbe-373">Inside the folder, add some images containing mouse or keyboard.</span></span> <span data-ttu-id="56dbe-374">Diese werden die Bilder, die durch das Tensorflow-Modell analysiert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-374">Those will be the images that will be analyzed by the Tensorflow model.</span></span>

    > [!WARNING]
    > <span data-ttu-id="56dbe-375">Wenn Sie Ihr eigenes Modell verwenden, müssen Sie so ändern Sie diese Option, um Ihre eigenen Modelle Daten widerzuspiegeln.</span><span class="sxs-lookup"><span data-stu-id="56dbe-375">If you are using your own model, you will need to change this to reflect your own models data.</span></span>

8.  <span data-ttu-id="56dbe-376">Sie müssen nun zum Abrufen der **labels.txt** und **model.pb** Dateien aus dem Modellordner, die Sie vorherige heruntergeladen haben (oder aus Ihren eigenen erstellt **Custom Vision Service** ), in [Kapitel 1](#chapter-1---retrieve-the-custom-vision-model).</span><span class="sxs-lookup"><span data-stu-id="56dbe-376">You will now need to retrieve the **labels.txt** and **model.pb** files from the model folder, which you previous downloaded (or created from your own **Custom Vision Service**), in [Chapter 1](#chapter-1---retrieve-the-custom-vision-model).</span></span> <span data-ttu-id="56dbe-377">Nachdem Sie die Dateien haben, platzieren Sie sie in der Projektmappe zusammen mit den anderen Dateien.</span><span class="sxs-lookup"><span data-stu-id="56dbe-377">Once you have the files, place them within your solution, alongside the other files.</span></span> <span data-ttu-id="56dbe-378">Das Endergebnis sollte wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="56dbe-378">The final result should look like the image below:</span></span>

    ![Erstellen Sie Ihres Containers](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a><span data-ttu-id="56dbe-380">Kapitel 9 - Paket der Projektmappe als container</span><span class="sxs-lookup"><span data-stu-id="56dbe-380">Chapter 9 - Package the solution as a container</span></span>

1.  <span data-ttu-id="56dbe-381">Sie können nun "packen" die Dateien als Container und per push an Ihre **Azure Container Registry**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-381">You are now ready to "package" your files as a container and push it to your **Azure Container Registry**.</span></span> <span data-ttu-id="56dbe-382">In VS Code öffnen die *integriertes Terminal* (**anzeigen > integriertes Terminal / STRG + '**), und verwenden Sie die folgende Zeile für die Anmeldung bei **Docker** (ersetzen Sie die Werte von der Befehl mit den Anmeldeinformationen Ihrer **Azure Container Registry (ACR)**):</span><span class="sxs-lookup"><span data-stu-id="56dbe-382">Within VS Code, open the *Integrated Terminal* (**View > Integrated Terminal / CTRL + \`**), and use the following line to login to **Docker** (substitute the values of the command with the credentials of your **Azure Container Registry (ACR)**):</span></span>

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. <span data-ttu-id="56dbe-383">Mit der rechten Maustaste auf die Datei **deployment.template.json**, und klicken Sie auf **IoT Edge-Projektmappe erstellen**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-383">Right-click on the file **deployment.template.json**, and click **Build IoT Edge Solution**.</span></span> <span data-ttu-id="56dbe-384">Dieser Build-Vorgang dauert einige Zeit (abhängig von Ihrem Gerät), also warten darauf vorbereitet sein.</span><span class="sxs-lookup"><span data-stu-id="56dbe-384">This build process takes quite some time (depending on your device), so be prepared to wait.</span></span> <span data-ttu-id="56dbe-385">Nach Abschluss des Buildprozesses eine **"Deployment.JSON"** Datei wird in einen neuen Ordner namens erstellt wurden **Config**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-385">After the build process finishes, a **deployment.json** file will have been created inside a new folder called **config**.</span></span>

    ![Bereitstellung erstellen](images/AzureLabs-Lab313-30.png)

3. <span data-ttu-id="56dbe-387">Öffnen der **Befehlspalette** erneut, und suchen Sie nach **Azure: Melden Sie sich bei**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-387">Open the **Command Palette** again, and search for **Azure: Sign In**.</span></span> <span data-ttu-id="56dbe-388">Befolgen Sie die Anweisungen, die mit Ihren Azure-Konto-Anmeldeinformationen ein, Visual Studio Code erhalten Sie eine Option aus, um *kopieren und öffnen Sie*, werden die des Gerätecodes Sie bald benötigen, und öffnet Ihren Standardbrowser für das Web kopiert.</span><span class="sxs-lookup"><span data-stu-id="56dbe-388">Follow the prompts using your Azure Account credentials; VS Code will provide you with an option to *Copy and Open*, which will copy the device code you will soon need, and open your default web browser.</span></span> <span data-ttu-id="56dbe-389">Wenn Sie aufgefordert, fügen Sie den Gerätecode, um Ihren Computer zu authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="56dbe-389">When asked, paste the device code, to authenticate your machine.</span></span>

    ![Kopieren und öffnen](images/AzureLabs-Lab313-31.png)

4. <span data-ttu-id="56dbe-391">Einmal signierte in Sie werden feststellen, auf den unteren Rand der *Durchsuchen* Bereich einen neuen Abschnitt namens **Azure IoT Hub-Geräte**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-391">Once signed in you will notice, on the bottom side of the *Explore* panel, a new section called **Azure IoT Hub Devices**.</span></span> <span data-ttu-id="56dbe-392">Klicken Sie auf diesen Bereich, um ihn zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="56dbe-392">Click this section to expand it.</span></span>

    ![Edge-Gerät](images/AzureLabs-Lab313-32.png)

5. <span data-ttu-id="56dbe-394">Wenn Ihr Gerät nicht hier ist, müssen Sie mit der rechten Maustaste *Azure IoT Hub-Geräte*, und klicken Sie dann auf **IoT Hub-Verbindungszeichenfolge festlegen**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-394">If your device is not here, you will need to right-click *Azure IoT Hub Devices*, and then click **Set IoT Hub Connection String**.</span></span> <span data-ttu-id="56dbe-395">Klicken Sie dann sehen Sie, dass die **Befehlspalette** (oben auf der Visual Studio Code), fordert Sie zur Eingabe Ihrer *Verbindungszeichenfolge*.</span><span class="sxs-lookup"><span data-stu-id="56dbe-395">You will then see that the **Command Palette** (at the top of VS Code), will prompt you to input your *Connection String*.</span></span> <span data-ttu-id="56dbe-396">Dies ist die *Verbindungszeichenfolge* Sie am Ende der notiert [Kapitel 3](#chapter-3---the-iot-hub-service).</span><span class="sxs-lookup"><span data-stu-id="56dbe-396">This is the *Connection String* you noted down at the end of [Chapter 3](#chapter-3---the-iot-hub-service).</span></span> <span data-ttu-id="56dbe-397">Drücken Sie die **EINGABETASTE** Schlüssel, nachdem Sie die Zeichenfolge in kopiert haben.</span><span class="sxs-lookup"><span data-stu-id="56dbe-397">Press the **Enter** key, once you have copied the string in.</span></span>    

6. <span data-ttu-id="56dbe-398">Ihr Gerät sollte geladen und angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="56dbe-398">Your device should load, and appear.</span></span> <span data-ttu-id="56dbe-399">Mit der rechten Maustaste auf den Gerätenamen, und klicken Sie dann auf, **Bereitstellung erstellen, für die einzelnen Gerät**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-399">Right-click on the device name, and then click, **Create Deployment for Single Device**.</span></span>

    ![Bereitstellung erstellen](images/AzureLabs-Lab313-33b.png)

7. <span data-ttu-id="56dbe-401">Erhalten Sie eine *Datei-Explorer* dazu aufgefordert werden, in dem Sie wechseln können, die **Config** Ordner, und wählen Sie dann die **"Deployment.JSON"** Datei.</span><span class="sxs-lookup"><span data-stu-id="56dbe-401">You will get a *File Explorer* prompt, where you can navigate to the **config** folder, and then select the **deployment.json** file.</span></span> <span data-ttu-id="56dbe-402">Mit dieser Datei ausgewählt haben, klicken Sie auf die **Edge-Bereitstellungsmanifest wählen** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="56dbe-402">With that file selected, click the **Select Edge Deployment Manifest** button.</span></span>

    ![Bereitstellung erstellen](images/AzureLabs-Lab313-34.png)

8. <span data-ttu-id="56dbe-404">Sie haben an diesem Punkt angegeben Ihre **IoT Hub-Dienst** mit dem Manifest für die Bereitstellung Ihres Containers und als Modul aus Ihrer **Azure Container Registry**effektiv auf Ihrem Gerät bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-404">At this point you have provided your **IoT Hub Service** with the manifest for it to deploy your container, as a module, from your **Azure Container Registry**, effectively deploying it to your device.</span></span>

9. <span data-ttu-id="56dbe-405">Um die von Ihrem Gerät an IoT Hub gesendete Nachrichten anzuzeigen, mit der rechten Maustaste erneut auf den Namen des Geräts in der **Azure IoT Hub-Geräte** im Abschnitt der **Explorer** Bereich, und klicken Sie auf **Überwachung starten D2C-Nachricht**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-405">To view the messages sent from your device to the IoT Hub, right-click again on your device name in the **Azure IoT Hub Devices** section, in the **Explorer** panel, and click on **Start Monitoring D2C Message**.</span></span> <span data-ttu-id="56dbe-406">Die vom Gerät gesendeten Nachrichten in der Visual Studio-Terminal angezeigt.</span><span class="sxs-lookup"><span data-stu-id="56dbe-406">The messages sent from your device should appear in the VS Terminal.</span></span> <span data-ttu-id="56dbe-407">Geduld, dieser Vorgang kann einige Zeit dauern.</span><span class="sxs-lookup"><span data-stu-id="56dbe-407">Be patient, as this may take some time.</span></span> <span data-ttu-id="56dbe-408">Finden Sie im nächste Kapitel für das Debuggen, und überprüfen, ob die Bereitstellung erfolgreich war.</span><span class="sxs-lookup"><span data-stu-id="56dbe-408">See the next Chapter for debugging, and checking if deployment was successful.</span></span>

<span data-ttu-id="56dbe-409">Dieses Modul wird jetzt leicht zwischen dem die Bilder in der **Images** Ordner und analysieren Sie sie bei jeder Iteration.</span><span class="sxs-lookup"><span data-stu-id="56dbe-409">This module will now iterate between the images in the **images** folder and analyze them, with each iteration.</span></span> <span data-ttu-id="56dbe-410">Dies ist natürlich nur ein Beispiel, wie Sie die grundlegende Machine Learning-Modell funktioniert in einer Umgebung der IoT Edge-Gerät abrufen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-410">This is obviously just a demonstration of how to get the basic machine learning model to work in an IoT Edge device environment.</span></span> 

<span data-ttu-id="56dbe-411">Um die Funktionalität dieses Beispiels zu erweitern, können Sie auf verschiedene Arten fortfahren.</span><span class="sxs-lookup"><span data-stu-id="56dbe-411">To expand the functionality of this example, you could proceed in several ways.</span></span> <span data-ttu-id="56dbe-412">Eine Möglichkeit kann Code in den Container, einschließlich werden, die Fotos von einer Webcam, die auf dem Gerät verbunden ist erfasst, und speichert die Bilder im Ordner "Images".</span><span class="sxs-lookup"><span data-stu-id="56dbe-412">One way could be including some code in the container, that captures photos from a webcam that is connected to the device, and saves the images in the images folder.</span></span> 

<span data-ttu-id="56dbe-413">Eine weitere Möglichkeit konnte die Bilder aus dem IoT-Geräte in den Container kopieren.</span><span class="sxs-lookup"><span data-stu-id="56dbe-413">Another way could be copying the images from the IoT device into the container.</span></span> <span data-ttu-id="56dbe-414">Eine praktische Möglichkeit, dies ist auf den folgenden Befehl in der IoT-Geräte-Terminal ausführen (z. B. eine kleine app konnte den Auftrag werden Wenn Sie den Vorgang zu automatisieren).</span><span class="sxs-lookup"><span data-stu-id="56dbe-414">A practical way to do that is to run the following command in the IoT device Terminal (perhaps a small app could do the job, if you wished to automate the process).</span></span> <span data-ttu-id="56dbe-415">Sie können mit diesem Befehl testen, indem Sie sie manuell ausführen, über den Speicherort des Ordners, in dem Ihre Dateien gespeichert werden:</span><span class="sxs-lookup"><span data-stu-id="56dbe-415">You can test this command by running it manually from the folder location where your files are stored:</span></span>

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a><span data-ttu-id="56dbe-416">Kapitel 10 – IoT Edge-Laufzeit-Debuggen</span><span class="sxs-lookup"><span data-stu-id="56dbe-416">Chapter 10 - Debugging the IoT Edge Runtime</span></span>

<span data-ttu-id="56dbe-417">Im folgenden finden Sie eine Liste von Befehlszeilen und Tipps, zum Überwachen und Debuggen von der messaging-Aktivität von der *IoT Edge-Runtime*, aus Ihrem **Ubuntu-Gerät**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-417">The following are a list of command lines, and tips, to help you monitor and debug the messaging activity of the *IoT Edge Runtime*, from your **Ubuntu device**.</span></span> 

- <span data-ttu-id="56dbe-418">Überprüfen Sie die *IoT Edge-Runtime* Status durch Ausführen der folgenden Befehlszeile:</span><span class="sxs-lookup"><span data-stu-id="56dbe-418">Check the *IoT Edge Runtime* status by running the following command line:</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > <span data-ttu-id="56dbe-419">Denken Sie daran, drücken die **STRG + C**, um den Vorgang abzuschließen, Anzeigen des Status.</span><span class="sxs-lookup"><span data-stu-id="56dbe-419">Remember to press **Ctrl + C**, to finish viewing the status.</span></span>

- <span data-ttu-id="56dbe-420">Listet die Container, die derzeit bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="56dbe-420">List the containers that are currently deployed.</span></span> <span data-ttu-id="56dbe-421">Wenn die *IoT Hub-Dienst* Container wurde erfolgreich bereitgestellt. sie werden durch Ausführen der folgenden Befehlszeile angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="56dbe-421">If the *IoT Hub Service* has deployed the containers successfully, they will be displayed by running the following command line:</span></span>

    ```bash
        sudo iotedge list
    ```

    <span data-ttu-id="56dbe-422">Oder</span><span class="sxs-lookup"><span data-stu-id="56dbe-422">Or</span></span>

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > <span data-ttu-id="56dbe-423">Die oben genannten ist eine gute Möglichkeit zum Überprüfen, ob Ihr Modul erfolgreich bereitgestellt wurde, wie er in der Liste angezeigt wird. Andernfalls werden **nur** finden Sie unter den *EdgeHub* und *EdgeAgent*.</span><span class="sxs-lookup"><span data-stu-id="56dbe-423">The above is a good way to check whether your module has been deployed successfully, as it will appear in the list; you will otherwise **only** see the *edgeHub* and *edgeAgent*.</span></span>

- <span data-ttu-id="56dbe-424">Um die Protokolle der Code eines Containers zu anzuzeigen, führen Sie die folgende Befehlszeile ein:</span><span class="sxs-lookup"><span data-stu-id="56dbe-424">To display the code logs of a container, run the following command line:</span></span>

    ```bash
        journalctl -u iotedge
    ```

<span data-ttu-id="56dbe-425">**Hilfreiche Befehle zum Verwalten der IoT Edge-Runtime:**</span><span class="sxs-lookup"><span data-stu-id="56dbe-425">**Useful commands to manage the IoT Edge Runtime:**</span></span>

-  <span data-ttu-id="56dbe-426">So löschen Sie alle Container auf dem Host:</span><span class="sxs-lookup"><span data-stu-id="56dbe-426">To delete all containers in the host:</span></span>

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  <span data-ttu-id="56dbe-427">Zum Beenden der *IoT Edge-Runtime*:</span><span class="sxs-lookup"><span data-stu-id="56dbe-427">To stop the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a><span data-ttu-id="56dbe-428">Kapitel 11: Erstellen der Tabellendienst</span><span class="sxs-lookup"><span data-stu-id="56dbe-428">Chapter 11 - Create Table Service</span></span> 

<span data-ttu-id="56dbe-429">Navigieren Sie zurück zu Ihrem Azure-Portal, in dem Sie eine Azure-Tabellen-Dienst, vom Erstellen einer Speicherressource erstellen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-429">Navigate back to your Azure Portal, where you will create an Azure Tables Service, by creating a Storage resource.</span></span>

1. <span data-ttu-id="56dbe-430">Wenn nicht bereits angemeldet, melden Sie sich bei der [Azure-Portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="56dbe-430">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="56dbe-431">Sobald Sie angemeldet sind, klicken Sie auf **erstellen Sie eine Ressource**, klicken Sie in der oberen linken Ecke, und suchen Sie nach **Speicherkonto**, und drücken Sie die **EINGABETASTE** Schlüssel, mit der Suche begonnen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-431">Once logged in, click on **Create a resource**, in the top left corner, and search for **Storage account**, and press the **Enter** key, to start the search.</span></span>

3. <span data-ttu-id="56dbe-432">Wenn es angezeigt wurde, klicken Sie auf **Speicherkonto – Blob, Datei, Tabelle, Warteschlange** aus der Liste.</span><span class="sxs-lookup"><span data-stu-id="56dbe-432">Once it has appeared, click **Storage account - blob, file, table, queue** from the list.</span></span>

    ![Suchen Sie nach dem Storage-Konto](images/AzureLabs-Lab313-35.png)

4. <span data-ttu-id="56dbe-434">Die neue Seite bietet eine Beschreibung der **Speicherkonto** Service.</span><span class="sxs-lookup"><span data-stu-id="56dbe-434">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="56dbe-435">Unten links der Aufforderung, klicken Sie auf die **erstellen** Schaltfläche, um eine Instanz dieses Diensts erstellen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-435">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![Storage-Instanz erstellen](images/AzureLabs-Lab313-36.png)

5. <span data-ttu-id="56dbe-437">Nachdem Sie auf geklickt haben **erstellen**, wird ein Panel angezeigt:</span><span class="sxs-lookup"><span data-stu-id="56dbe-437">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="56dbe-438">Fügen Sie Ihre bevorzugte **Namen** für diese Dienstinstanz (*müssen Kleinbuchstaben sein*).</span><span class="sxs-lookup"><span data-stu-id="56dbe-438">Insert your desired **Name** for this Service instance (*must be all lowercase*).</span></span>

    2. <span data-ttu-id="56dbe-439">Für **Bereitstellungsmodell**, klicken Sie auf **RM**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-439">For **Deployment model**, click **Resource manager**.</span></span>

    3. <span data-ttu-id="56dbe-440">Für **Kontoart**, klicken Sie im Dropdownmenü mit **Speicher (Allgemein v1)**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-440">For **Account kind**, using the dropdown menu, click **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="56dbe-441">Klicken Sie auf einen geeigneten **Speicherort**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-441">Click an appropriate **Location**.</span></span>
    
    5. <span data-ttu-id="56dbe-442">Für die **Replikation** Dropdown-Menü, klicken Sie auf **Read-Access-georedundanter Speicher (RA-GRS)**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-442">For the **Replication** dropdown menu, click **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6. <span data-ttu-id="56dbe-443">Für **Leistung**, klicken Sie auf **Standard**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-443">For **Performance**, click **Standard**.</span></span>

    7. <span data-ttu-id="56dbe-444">In der **sichere Übertragung erforderlich** auf **deaktiviert**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-444">Within the **Secure transfer required** section, click **Disabled**.</span></span>

    8. <span data-ttu-id="56dbe-445">Von der **Abonnement** Dropdown-Menü, klicken Sie auf ein entsprechendes Abonnement.</span><span class="sxs-lookup"><span data-stu-id="56dbe-445">From the **Subscription** dropdown menu, click an appropriate subscription.</span></span>

    9. <span data-ttu-id="56dbe-446">Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-446">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="56dbe-447">Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, bereitzustellen und zu verwalten, Rechnungen für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-447">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="56dbe-448">Es wird empfohlen, alle zu bewahren, an die Azure-Dienste unter einer allgemeinen Ressourcengruppe mit einem einzelnen Projekt (z. B. z. B. diese Kurse) verknüpft ist).</span><span class="sxs-lookup"><span data-stu-id="56dbe-448">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="56dbe-449">Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, befolgen Sie diese [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="56dbe-449">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="56dbe-450">Lassen Sie **virtuelle Netzwerke** als **deaktiviert**, ist dies eine Option für Sie.</span><span class="sxs-lookup"><span data-stu-id="56dbe-450">Leave **Virtual networks** as **Disabled**, if this is an option for you.</span></span>

    11. <span data-ttu-id="56dbe-451">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-451">Click **Create**.</span></span>

        ![Geben Sie im Storage-details](images/AzureLabs-Lab313-37.png)

6. <span data-ttu-id="56dbe-453">Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.</span><span class="sxs-lookup"><span data-stu-id="56dbe-453">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

7. <span data-ttu-id="56dbe-454">Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="56dbe-454">A notification will appear in the Portal once the Service instance is created.</span></span> <span data-ttu-id="56dbe-455">Klicken Sie auf die Benachrichtigungen an Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-455">Click on the notifications to explore your new Service instance.</span></span>

    ![neue Speicher-Benachrichtigung](images/AzureLabs-Lab313-38.png)

8. <span data-ttu-id="56dbe-457">Klicken Sie auf die **zu Ressource wechseln** Schaltfläche in die Benachrichtigung, und Sie gelangen auf Ihre neue Übersichtsseite für den Speicherdienst-Instanz.</span><span class="sxs-lookup"><span data-stu-id="56dbe-457">Click the **Go to resource** button in the notification, and you will be taken to your new Storage Service instance overview page.</span></span>

    ![zu Ressource wechseln](images/AzureLabs-Lab313-39.png)

9. <span data-ttu-id="56dbe-459">Klicken Sie auf der Seite "Übersicht" auf der rechten Seite auf **Tabellen**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-459">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![Tabellen](images/AzureLabs-Lab313-40.png)

10. <span data-ttu-id="56dbe-461">Bereich auf der rechten Seite wird geändert, um das Anzeigen der **Tabellendienst** Informationen, bei dem Sie eine neue Tabelle hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="56dbe-461">The panel on the right will change to show the **Table Service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="56dbe-462">Durch Klicken auf die **+ Tabelle** Schaltfläche auf der linken oberen Ecke.</span><span class="sxs-lookup"><span data-stu-id="56dbe-462">Do this by clicking the **+ Table** button to the top-left corner.</span></span>

    ![Öffnen von Tabellen](images/AzureLabs-Lab313-41.png)

11. <span data-ttu-id="56dbe-464">Eine neue Seite wird angezeigt, in dem Sie eingeben müssen, eine **Tabellenname**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-464">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="56dbe-465">Dies ist der Name, den Sie verwenden, um auf die Daten in Ihrer Anwendung in späteren Kapiteln (Erstellen von Funktionen-App und Power BI) verweisen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-465">This is the name you will use to refer to the data in your application in later Chapters (creating Function App, and Power BI).</span></span> <span data-ttu-id="56dbe-466">Fügen Sie **IoTMessages** als Name (Sie können Ihre eigenen auswählen Denken Sie bei einem späteren Zeitpunkt in diesem Dokument verwendet), und klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-466">Insert **IoTMessages** as the name (you can choose your own, just remember it when used later in this document) and click **OK**.</span></span> 

12. <span data-ttu-id="56dbe-467">Sobald die neue Tabelle erstellt wurde, Sie werden in finden Sie unter den **Tabellendienst** Seite (unten).</span><span class="sxs-lookup"><span data-stu-id="56dbe-467">Once the new table has been created, you will be able to see it within the **Table Service** page (at the bottom).</span></span>

    ![neue Tabelle](images/AzureLabs-Lab313-42.png)  

13. <span data-ttu-id="56dbe-469">Klicken Sie nun auf **Zugriffsschlüssel** und eine Kopie der **speicherkontonamen** und **Schlüssel** (mit dem Ihr Editor), verwenden Sie diese Werte später in diesem Kurs, beim Erstellen der **Azure Functions-App**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-469">Now click on **Access keys** and take a copy of the **Storage account name** and **Key** (using your Notepad), you will use these values later in this course, when creating the **Azure Function App**.</span></span>

    ![neue Tabelle](images/AzureLabs-Lab313-43.png) 

14. <span data-ttu-id="56dbe-471">Verwenden den Bereich in diesem Fall auf der linken Seite einen Bildlauf zu der *Tabellendienst* aus, und klicken Sie auf **Tabellen** (oder **Tabellen durchsuchen**, in neueren Portalen) und eine Kopie der  **Tabelle URL** (mit dem Ihr Editor).</span><span class="sxs-lookup"><span data-stu-id="56dbe-471">Using the panel on the left again, scroll to the *Table Service* section, and click **Tables** (or **Browse Tables**, in newer Portals) and take a copy of the **Table URL** (using your Notepad).</span></span> <span data-ttu-id="56dbe-472">Verwenden Sie diesen Wert später in diesem Kurs, beim Verknüpfen der Tabelle auf Ihre **Power BI** Anwendung.</span><span class="sxs-lookup"><span data-stu-id="56dbe-472">You will use this value later in this course, when linking your table to your **Power BI** application.</span></span>

    ![neue Tabelle](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a><span data-ttu-id="56dbe-474">Kapitel 12 – Abschließen der Azure-Tabelle</span><span class="sxs-lookup"><span data-stu-id="56dbe-474">Chapter 12 - Completing the Azure Table</span></span>

<span data-ttu-id="56dbe-475">Nachdem Ihre **Tabellendienst** Storage-Konto eingerichtet haben, ist es Zeit zum Hinzufügen von Daten, die zum Speichern und Abrufen von Informationen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="56dbe-475">Now that your **Table Service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="56dbe-476">Die Bearbeitung Ihrer Tabellen kann über erfolgen **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-476">The editing of your Tables can be done through **Visual Studio**.</span></span>

1. <span data-ttu-id="56dbe-477">Open **Visual Studio** (**nicht** Visual Studio-Code).</span><span class="sxs-lookup"><span data-stu-id="56dbe-477">Open **Visual Studio** (**not** Visual Studio Code).</span></span>

2. <span data-ttu-id="56dbe-478">Klicken Sie im Menü auf **Ansicht > Cloud-Explorer**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-478">From the menu, click **View > Cloud Explorer**.</span></span>

    ![Öffnen Sie den Cloud-explorer](images/AzureLabs-Lab313-45.png)

3. <span data-ttu-id="56dbe-480">Die **Cloud-Explorer** öffnet als angedockte Element (Geduld, Laden von Zeit in Anspruch).</span><span class="sxs-lookup"><span data-stu-id="56dbe-480">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="56dbe-481">Wenn das Abonnement, das Sie zum Erstellen verwendet Ihre *Speicherkonten* ist nicht sichtbar ist, sicherzustellen, dass Sie:</span><span class="sxs-lookup"><span data-stu-id="56dbe-481">If the subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="56dbe-482">Angemeldet um dasselbe Konto wie diejenige aus, die Sie für das Azure-Portal verwendet.</span><span class="sxs-lookup"><span data-stu-id="56dbe-482">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="56dbe-483">Ihr Abonnement aus der Account Management-Seite (möglicherweise müssen einen Filter aus den Einstellungen Ihres Kontos anwenden) ausgewählt:</span><span class="sxs-lookup"><span data-stu-id="56dbe-483">Selected your subscription from the Account Management page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![Suchen Sie nach Abonnement](images/AzureLabs-Lab313-46.png)

4. <span data-ttu-id="56dbe-485">Ihre Azure-Cloud-Dienste werden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="56dbe-485">Your Azure cloud Services will be shown.</span></span> <span data-ttu-id="56dbe-486">Suchen **Speicherkonten** , und klicken Sie auf den Pfeil auf der linken Seite, um Ihre Konten zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="56dbe-486">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![Öffnen Sie Storage-Konten](images/AzureLabs-Lab313-47.png)

5. <span data-ttu-id="56dbe-488">Nach der Kategorie erweitert ist, das neu erstellte **Speicherkonto** verfügbar sein sollen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-488">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="56dbe-489">Klicken Sie auf den Pfeil auf der linken Seite des Speichers, und klicken Sie dann nach, die erweitert wird, finden **Tabellen** , und klicken Sie auf den Pfeil neben der, dass zum Anzeigen der **Tabelle** Sie im letzten Abschnitt erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="56dbe-489">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="56dbe-490">Doppelklicken Sie auf Ihre **Tabelle**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-490">Double-click your **Table**.</span></span>

6. <span data-ttu-id="56dbe-491">Die Tabelle wird in der Mitte des Ihrer Visual Studio-Fenster geöffnet.</span><span class="sxs-lookup"><span data-stu-id="56dbe-491">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="56dbe-492">Klicken Sie auf das Tabellensymbol "mit der **+** (plus) auf.</span><span class="sxs-lookup"><span data-stu-id="56dbe-492">Click the table icon with the **+** (plus) on it.</span></span>

    ![neue Tabelle hinzufügen](images/AzureLabs-Lab313-48.png)

7. <span data-ttu-id="56dbe-494">Ein Fenster wird aufgefordert wird angezeigt, Sie *Entität hinzufügen*.</span><span class="sxs-lookup"><span data-stu-id="56dbe-494">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="56dbe-495">Erstellen Sie nur eine Entität, wenn es drei Eigenschaften hat.</span><span class="sxs-lookup"><span data-stu-id="56dbe-495">You will create only one entity, though it will have three properties.</span></span> <span data-ttu-id="56dbe-496">Sie werden feststellen, dass *PartitionKey* und *RowKey* werden soll, bereits bereitgestellt ist, als diese von der Tabelle verwendet werden, um Ihre Daten zu finden.</span><span class="sxs-lookup"><span data-stu-id="56dbe-496">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![Partitions-und zeilenschlüssels](images/AzureLabs-Lab313-49.png)

8. <span data-ttu-id="56dbe-498">Aktualisieren Sie die folgenden Werte ein:</span><span class="sxs-lookup"><span data-stu-id="56dbe-498">Update the following values:</span></span>

    - <span data-ttu-id="56dbe-499">Name: **PartitionKey**, Value: **PK_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="56dbe-499">Name: **PartitionKey**, Value: **PK_IoTMessages**</span></span> 

    - <span data-ttu-id="56dbe-500">Name: **RowKey**, Value: **RK_1_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="56dbe-500">Name: **RowKey**, Value: **RK_1_IoTMessages**</span></span> 

9. <span data-ttu-id="56dbe-501">Klicken Sie auf **Eigenschaft hinzufügen** (unten links in der die *Entität hinzufügen* Fenster), und fügen Sie die folgende Eigenschaft hinzu:</span><span class="sxs-lookup"><span data-stu-id="56dbe-501">Then, click **Add property** (to the lower left of the *Add Entity* window) and add the following property:</span></span>

    - <span data-ttu-id="56dbe-502">**MessageContent**, als eine *Zeichenfolge*, den Wert leer lassen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-502">**MessageContent**, as a *string*, leave the Value empty.</span></span>

10. <span data-ttu-id="56dbe-503">Die Tabelle sollte in der folgenden Abbildung entsprechen:</span><span class="sxs-lookup"><span data-stu-id="56dbe-503">Your table should match the one in the image below:</span></span>

    ![Fügen Sie die richtigen Werte](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > <span data-ttu-id="56dbe-505">Der Grund, warum die Entität die Zahl 1 in der Zeilenschlüssel ist, da es sich bei hinzuzufügenden möglicherweise Nachrichten mehr anzeigt, sollten Sie wünschen, Experimentieren mit diesem Kurs.</span><span class="sxs-lookup"><span data-stu-id="56dbe-505">The reason why the entity has the number 1 in the row key, is because you might want to add more messages, should you desire to experiment further with this course.</span></span>

11. <span data-ttu-id="56dbe-506">Klicken Sie anschließend auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-506">Click **OK** when you are finished.</span></span> <span data-ttu-id="56dbe-507">Die Tabelle kann jetzt verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="56dbe-507">Your table is now ready to be used.</span></span>

## <a name="chapter-13---create-an-azure-function-app"></a><span data-ttu-id="56dbe-508">Kapitel 13 – erstellen eine Azure-Funktions-App</span><span class="sxs-lookup"><span data-stu-id="56dbe-508">Chapter 13 - Create an Azure Function App</span></span> 

<span data-ttu-id="56dbe-509">Ist es jetzt Zeit zum Erstellen einer *Azure Function-App*, wird aufgerufen, indem die *IoT Hub-Dienst* zum Speichern der *IoT Edge* Gerät-Nachrichten der **Tabelle** -Dienst, die Sie im vorherigen Kapitel erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="56dbe-509">It is now time to create an *Azure Function App*, which will be called by the *IoT Hub Service* to store the *IoT Edge* device messages in the **Table** Service, which you created in the previous Chapter.</span></span>

<span data-ttu-id="56dbe-510">Zunächst müssen Sie eine Datei zu erstellen, mit dem Ihre Azure-Funktion, die Bibliotheken zu laden, die Sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-510">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="56dbe-511">Open **Editor** (drücken Sie die *Windows-Taste*, und geben *Editor*).</span><span class="sxs-lookup"><span data-stu-id="56dbe-511">Open **Notepad** (press the *Windows Key*, and type *notepad*).</span></span>

    ![Öffnen Sie Editor](images/AzureLabs-Lab313-51.png)

2.  <span data-ttu-id="56dbe-513">Legen Sie mit dem Editor öffnen die folgende JSON-Struktur, in es.</span><span class="sxs-lookup"><span data-stu-id="56dbe-513">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="56dbe-514">Sobald Sie dies getan haben, speichern Sie es auf Ihrem Desktop als **"Project.JSON"**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-514">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="56dbe-515">Diese Datei definiert die Bibliotheken, die Ihre Funktion verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="56dbe-515">This file defines the libraries your function will use.</span></span> <span data-ttu-id="56dbe-516">Wenn Sie NuGet verwendet haben, sieht er vertraut.</span><span class="sxs-lookup"><span data-stu-id="56dbe-516">If you have used NuGet, it will look familiar.</span></span>
    
    > [!WARNING]
    > <span data-ttu-id="56dbe-517">Es ist wichtig, dass die Benennung korrekt ist. Stellen Sie sicher, es ist **keine txt** Dateierweiterung.</span><span class="sxs-lookup"><span data-stu-id="56dbe-517">It is important that the naming is correct; ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="56dbe-518">Finden Sie weiter unten als Referenz:</span><span class="sxs-lookup"><span data-stu-id="56dbe-518">See below for reference:</span></span>
    >
    > ![JSON speichern](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  <span data-ttu-id="56dbe-520">Melden Sie sich bei der [Azure-Portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="56dbe-520">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="56dbe-521">Sobald Sie angemeldet sind, klicken Sie auf **erstellen Sie eine Ressource** in der oberen linken Ecke, und suchen Sie nach **Funktions-App**, und drücken Sie die **EINGABETASTE** Schlüssel handelt, suchen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-521">Once you are logged in, click on **Create a resource** in the top left corner, and search for **Function App**, and press the **Enter** key, to search.</span></span> <span data-ttu-id="56dbe-522">Klicken Sie auf *Funktions-App* aus den Ergebnissen aus, um ein neuer Bereich geöffnet.</span><span class="sxs-lookup"><span data-stu-id="56dbe-522">Click *Function App* from the results, to open a new panel.</span></span>

    ![Suchen Sie nach der Funktions-app](images/AzureLabs-Lab313-53.png)

5.  <span data-ttu-id="56dbe-524">Der nächste neue Bereich bietet eine Beschreibung der **Funktions-App** Service.</span><span class="sxs-lookup"><span data-stu-id="56dbe-524">The new panel will provide a description of the **Function App** Service.</span></span> <span data-ttu-id="56dbe-525">Unten links von diesem Bereich, klicken Sie auf die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-525">At the bottom left of this panel, click the **Create** button, to create an association with this Service.</span></span>

    ![Funktionen-app-Instanz](images/AzureLabs-Lab313-54.png)

6.  <span data-ttu-id="56dbe-527">Nachdem Sie auf geklickt haben **erstellen**, geben Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="56dbe-527">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="56dbe-528">Für **Anwendungsnamen**, fügen Sie dem gewünschten Namen für diese Dienstinstanz.</span><span class="sxs-lookup"><span data-stu-id="56dbe-528">For **App name**, insert your desired name for this Service instance.</span></span>

    2. <span data-ttu-id="56dbe-529">Wählen Sie eine **Abonnement**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-529">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="56dbe-530">Wählen Sie der Tarif für Sie geeignet, ist dies das erste Mal erstellen eine **-Funktion von App Service**, freier-Tarif für Sie verfügbar sein sollen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-530">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="56dbe-531">Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-531">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="56dbe-532">Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, bereitzustellen und zu verwalten, Rechnungen für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-532">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="56dbe-533">Es wird empfohlen, alle zu bewahren, an die Azure-Dienste unter einer allgemeinen Ressourcengruppe mit einem einzelnen Projekt (z. B. z. B. diese Kurse) verknüpft ist).</span><span class="sxs-lookup"><span data-stu-id="56dbe-533">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="56dbe-534">Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, befolgen Sie diese [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="56dbe-534">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="56dbe-535">Für **OS**, Windows, klicken Sie auf, da dies die angezielte Plattform ist.</span><span class="sxs-lookup"><span data-stu-id="56dbe-535">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="56dbe-536">Wählen Sie eine **Hostingplan** (in diesem Tutorial verwendet ein **Verbrauchstarif**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-536">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="56dbe-537">Wählen Sie eine **Speicherort** (Wählen Sie im vorherigen Schritt am gleichen Speicherort wie der Speicher, die Sie erstellt haben)</span><span class="sxs-lookup"><span data-stu-id="56dbe-537">Select a **Location** (choose the same location as the storage you have built in the previous step)</span></span>

    8. <span data-ttu-id="56dbe-538">Für die **Storage** Abschnitt **müssen Sie den Storage-Dienst, die Sie im vorherigen Schritt erstellt haben, auswählen**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-538">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="56dbe-539">Sie müssen keine *Application Insights* in dieser app können daher gerne bleibt bestehen **aus**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-539">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="56dbe-540">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-540">Click **Create**.</span></span>

        ![neue Instanz erstellen](images/AzureLabs-Lab313-55.png)

7.  <span data-ttu-id="56dbe-542">Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.</span><span class="sxs-lookup"><span data-stu-id="56dbe-542">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="56dbe-543">Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="56dbe-543">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![Neue Benachrichtigung](images/AzureLabs-Lab313-56.png)

9.  <span data-ttu-id="56dbe-545">Klicken Sie auf auf die Benachrichtigung, sobald die Bereitstellung erfolgreich abgeschlossen wurde (Abschluss).</span><span class="sxs-lookup"><span data-stu-id="56dbe-545">Click on the notification, once deployment is successful (has finished).</span></span>

10. <span data-ttu-id="56dbe-546">Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-546">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![zu Ressource wechseln](images/AzureLabs-Lab313-57.png)

11. <span data-ttu-id="56dbe-548">Klicken Sie auf der linken Seite des neuen Bereichs, auf die **+** (Pluszeichen) Symbol neben dem *Funktionen*, um eine neue Funktion zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-548">In the left side of the new panel, click the **+** (plus) icon next to *Functions*, to create a new function.</span></span>

    ![Fügen Sie neue Funktion](images/AzureLabs-Lab313-58.png)

12. <span data-ttu-id="56dbe-550">Klicken Sie im mittleren Bereich der **Funktion** Erstellung-Fenster wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="56dbe-550">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="56dbe-551">Scrollen Sie weiter, und klicken Sie auf **benutzerdefinierte Funktion**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-551">Scroll down further, and click on **Custom function**.</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-59.png)

13. <span data-ttu-id="56dbe-553">Bildlauf nach unten in der nächsten Seite, bis Sie gefunden **IoT Hub (Event Hub)**, klicken Sie dann darauf.</span><span class="sxs-lookup"><span data-stu-id="56dbe-553">Scroll down the next page, until you find **IoT Hub (Event Hub)**, then click on it.</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-60.png)

14. <span data-ttu-id="56dbe-555">In der **IoT Hub (Event Hub)** legen Sie auf dem Blatt der **Sprache** zu **C#** , und klicken Sie dann auf **neue**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-555">In the **IoT Hub (Event Hub)** blade, set the **Language** to **C#** and then click on **new**.</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-61.png)

15. <span data-ttu-id="56dbe-557">Im Fenster, das angezeigt wird, stellen sicher, dass **IoT Hub** ausgewählt ist und den Namen des der *IoT Hub* Feld entspricht, durch den Namen des Ihre *IoT Hub-Dienst* , die Sie zuvor erstellt haben ([in Schritt 8, Kapitel 3](#chapter-3---the-iot-hub-service)).</span><span class="sxs-lookup"><span data-stu-id="56dbe-557">In the window that will appear, make sure that **IoT Hub** is selected and the name of the *IoT Hub* field corresponds with the name of your *IoT Hub Service* that you have created previously ([in step 8, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="56dbe-558">Klicken Sie dann auf die **wählen** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="56dbe-558">Then click the **Select** button.</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-62.png)

16. <span data-ttu-id="56dbe-560">Auf der **IoT Hub (Event Hub)** auf, klicken Sie auf dem Blatt **erstellen**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-560">Back on the **IoT Hub (Event Hub)** blade, click on **Create**.</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-63.png)

17. <span data-ttu-id="56dbe-562">Sie werden auf der Funktions-Editor weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="56dbe-562">You will be redirected to the function editor.</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-64.png)

18. <span data-ttu-id="56dbe-564">Löschen Sie der gesamte Code in diese zu, und Ersetzen Sie ihn durch Folgendes:</span><span class="sxs-lookup"><span data-stu-id="56dbe-564">Delete all the code in it and replace it with the following:</span></span>

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. <span data-ttu-id="56dbe-565">Ändern Sie die folgenden Variablen, damit sie auf die entsprechenden Werte entsprechen (**Tabelle** und **Storage** Werte aus [Schritt 11 und 13, bzw. der Kapitel 11](#chapter-11---create-table-service)), die finden Sie in Ihrem **Speicherkonto**:</span><span class="sxs-lookup"><span data-stu-id="56dbe-565">Change the following variables, so that they correspond to the appropriate values (**Table** and **Storage** values, from [step 11 and 13, respectively, of Chapter 11](#chapter-11---create-table-service)), that you will find in your **Storage Account**:</span></span>

    - <span data-ttu-id="56dbe-566">**TableName**, durch den Namen Ihrer **Tabelle** befindet sich in Ihre **Speicherkonto**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-566">**tableName**, with the name of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="56dbe-567">**TableURL**, durch die URL Ihrer **Tabelle** befindet sich in Ihre **Speicherkonto**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-567">**tableURL**, with the URL of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="56dbe-568">**"storageaccountname"**, mit dem Namen des durch den Namen des entsprechenden Werts Ihrer **Speicherkonto** Name.</span><span class="sxs-lookup"><span data-stu-id="56dbe-568">**storageAccountName**, with the name of the value corresponding with the name of your **Storage Account** name.</span></span>
    - <span data-ttu-id="56dbe-569">**"storageaccountkey"**, mit dem Schlüssel, die Sie erworben haben, in den Storage-Dienst, die Sie zuvor erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="56dbe-569">**storageAccountKey**, with the Key you have obtained in the Storage Service you have created previously.</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-65.png)

20. <span data-ttu-id="56dbe-571">Mit diesem Code, klicken Sie auf **speichern**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-571">With the code in place, click **Save**.</span></span>

21. <span data-ttu-id="56dbe-572">Klicken Sie anschließend die **\<** Symbol auf der rechten Seite der Seite (Pfeil).</span><span class="sxs-lookup"><span data-stu-id="56dbe-572">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-66.png)

22. <span data-ttu-id="56dbe-574">Ein Panel wird in der rechten Seite schieben.</span><span class="sxs-lookup"><span data-stu-id="56dbe-574">A panel will slide in from the right.</span></span> <span data-ttu-id="56dbe-575">In diesem Bereich, klicken Sie auf **hochladen**, und ein *Dateibrowser* wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="56dbe-575">In that panel, click **Upload**, and a *File Browser* will appear.</span></span>

23. <span data-ttu-id="56dbe-576">Navigieren Sie zu, und klicken Sie auf, die **"Project.JSON"** -Datei, die Sie in erstellt haben **Editor** zuvor, und klicken Sie dann auf die **öffnen** Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="56dbe-576">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="56dbe-577">Diese Datei definiert die Bibliotheken, die Ihre Funktion verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="56dbe-577">This file defines the libraries that your function will use.</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-67.png)

24. <span data-ttu-id="56dbe-579">Wenn die Datei hochgeladen wurde, wird es im Bereich auf der rechten Seite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="56dbe-579">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="56dbe-580">Klicken sie auf, öffnen sie in der **Funktion** Editor.</span><span class="sxs-lookup"><span data-stu-id="56dbe-580">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="56dbe-581">Es muss aussehen **genau** identisch mit der nächsten Abbildung.</span><span class="sxs-lookup"><span data-stu-id="56dbe-581">It must look **exactly** the same as the next image.</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-68.png)

25. <span data-ttu-id="56dbe-583">An diesem Punkt das wäre allerdings gut zum Testen der Funktion Ihrer Funktion zum Speichern der Nachricht auf Ihrer *Tabelle*.</span><span class="sxs-lookup"><span data-stu-id="56dbe-583">At this point it would be good to test the capability of your Function to store the message on your *Table*.</span></span> <span data-ttu-id="56dbe-584">Klicken Sie auf der oberen rechten Seite des Fensters auf **Test**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-584">On the top right side of the window, click on **Test**.</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-69.png)

26. <span data-ttu-id="56dbe-586">Einfügen einer Nachricht auf der **Anforderungstext**, wie in der obigen Abbildung, und klicken Sie auf auf dargestellt **ausführen**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-586">Insert a message on the **Request body**, as shown in the image above, and click on **Run**.</span></span> 

27. <span data-ttu-id="56dbe-587">Die Funktion ausgeführt wird, den Ergebnisstatus anzeigen (Sie werden feststellen, die grüne **Status 202 Accepted**weiter oben die *Ausgabe* Fenster bezeichnet, es wurde ein erfolgreicher Aufruf):</span><span class="sxs-lookup"><span data-stu-id="56dbe-587">The function will run, displaying the result status (you will notice the green **Status 202 Accepted**, above the *Output* window, which means it was a successful call):</span></span>

    ![Ergebnis der Ausgabe](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a><span data-ttu-id="56dbe-589">Kapitel 14 – Anzeigen von aktiven Nachrichten</span><span class="sxs-lookup"><span data-stu-id="56dbe-589">Chapter 14 - View active messages</span></span>

<span data-ttu-id="56dbe-590">Wenn Sie jetzt Visual Studio öffnen (**nicht** Visual Studio Code), können Sie Ihre Nachricht Testergebnis visualisieren, wie es in gespeichert werden, die *MessageContent* Bereich Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="56dbe-590">If you now open Visual Studio (**not** Visual Studio Code), you can visualize your test message result, as it will be stored in the *MessageContent* string area.</span></span>

![benutzerdefinierte Funktion](images/AzureLabs-Lab313-71.png)

<span data-ttu-id="56dbe-592">Mit dem Tabellendienst und die Funktionen-App vorhanden, werden Ihr Ubuntu-Gerät-Nachrichten angezeigt, Ihre *IoTMessages* Tabelle.</span><span class="sxs-lookup"><span data-stu-id="56dbe-592">With the Table Service and Function App in place, your Ubuntu device messages will appear in your *IoTMessages* Table.</span></span> <span data-ttu-id="56dbe-593">Wenn nicht bereits ausgeführt wird, starten Sie Ihr Gerät erneut, und die ergebnisnachrichten von Ihrem Gerät und Modul in der Tabelle anzeigen, über mithilfe von Visual Studio können *Cloud-Explorer*.</span><span class="sxs-lookup"><span data-stu-id="56dbe-593">If not already running, start your device again, and you will be able to see the result messages from your device, and module, within your Table, through using Visual Studio *Cloud Explorer*.</span></span>

![Visualisieren von Daten](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a><span data-ttu-id="56dbe-595">Kapitel 15 – Power BI-Setup</span><span class="sxs-lookup"><span data-stu-id="56dbe-595">Chapter 15 - Power BI Setup</span></span>

<span data-ttu-id="56dbe-596">Zum Visualisieren von Daten aus Ihrem IOT-Gerät Sie richtet **Power BI** (Desktopversion), zum Erfassen der Daten aus der *Tabelle* -Dienst, der Sie gerade erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="56dbe-596">To visualize the data from your IOT device you will setup **Power BI** (desktop version), to collect the data from the *Table* Service, which you just created.</span></span> <span data-ttu-id="56dbe-597">Die *HoloLens* Version von Power BI verwendet dann diese Daten, um die Ergebnisse zu visualisieren.</span><span class="sxs-lookup"><span data-stu-id="56dbe-597">The *HoloLens* version of Power BI will then use that data to visualize the result.</span></span>

1.  <span data-ttu-id="56dbe-598">Öffnen Sie den Microsoft Store für Windows 10, und suchen Sie nach **Power BI Desktop**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-598">Open the Microsoft Store on Windows 10 and search for **Power BI Desktop**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  <span data-ttu-id="56dbe-600">Laden Sie die Anwendung.</span><span class="sxs-lookup"><span data-stu-id="56dbe-600">Download the application.</span></span> <span data-ttu-id="56dbe-601">Sobald der Download abgeschlossen ist, öffnen Sie es aus.</span><span class="sxs-lookup"><span data-stu-id="56dbe-601">Once it has finished downloading, open it.</span></span>

3.  <span data-ttu-id="56dbe-602">Melden Sie sich bei *Power BI* mit Ihrem **Microsoft 365-Konto**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-602">Log into *Power BI* with your **Microsoft 365 account**.</span></span> <span data-ttu-id="56dbe-603">Sie können an einen Browser, um sich registrieren umgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="56dbe-603">You may be redirected to a browser, to sign up.</span></span> <span data-ttu-id="56dbe-604">Sobald Sie angemeldet sind, wechseln Sie zurück zu Power BI-app, und melden Sie sich erneut.</span><span class="sxs-lookup"><span data-stu-id="56dbe-604">Once you are signed up, go back to the Power BI app, and sign in again.</span></span>

4.  <span data-ttu-id="56dbe-605">Klicken Sie auf **Datenabruf** , und klicken Sie dann auf **mehr...** .</span><span class="sxs-lookup"><span data-stu-id="56dbe-605">Click on **Get Data** and then click on **More...**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  <span data-ttu-id="56dbe-607">Klicken Sie auf **Azure**, **Azure Table Storage**, klicken Sie dann auf **Connect**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-607">Click **Azure**, **Azure Table Storage**, then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  <span data-ttu-id="56dbe-609">Werden Sie aufgefordert, fügen Sie der **adresa URL Tabulky** , die Sie zuvor erfasst ([in Schritt 13 der Kapitel 11](#chapter-11---create-table-service)), während der Erstellung Ihrer.</span><span class="sxs-lookup"><span data-stu-id="56dbe-609">You will be prompted to insert the **Table URL** that you collected earlier ([in step 13 of Chapter 11](#chapter-11---create-table-service)), while creating your Table Service.</span></span> <span data-ttu-id="56dbe-610">Löschen Sie nach dem Einfügen der URL, die Teil des Pfads, die auf die Tabelle "Unterordner" (die IoTMessages, in diesem Kurs war).</span><span class="sxs-lookup"><span data-stu-id="56dbe-610">After inserting the URL, delete the portion of the path referring to the Table "sub-folder" (which was IoTMessages, in this course).</span></span> <span data-ttu-id="56dbe-611">Das Endergebnis sollte sein, wie in der folgenden Abbildung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="56dbe-611">The final result should be as displayed in the image below.</span></span> <span data-ttu-id="56dbe-612">Klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-612">Then click on **OK**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  <span data-ttu-id="56dbe-614">Werden Sie aufgefordert, fügen Sie der **Speicherschlüssel** , die Sie notiert haben ([in Schritt 11 des Kapitel 11](#chapter-11---create-table-service)) weiter oben beim Erstellen von Ihrem Tabellenspeicher.</span><span class="sxs-lookup"><span data-stu-id="56dbe-614">You will be prompted to insert the **Storage Key** that you noted ([in step 11 of Chapter 11](#chapter-11---create-table-service)) earlier while creating your Table Storage.</span></span> <span data-ttu-id="56dbe-615">Klicken Sie dann auf **Connect**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-615">Then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. <span data-ttu-id="56dbe-617">Ein **Bereich "Navigator"** angezeigt wird, aktivieren Sie das Kontrollkästchen neben der Tabelle aus, und klicken Sie auf **Load**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-617">A **Navigator Panel** will be displayed, tick the box next to your Table and click on **Load**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. <span data-ttu-id="56dbe-619">Die Tabelle jetzt in Power BI geladen wurde, aber es erfordert, dass eine Abfrage aus, um die Werte darin anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-619">Your table has now been loaded on Power BI, but it requires a query to display the values in it.</span></span> <span data-ttu-id="56dbe-620">Dazu, mit der Maustaste auf den Tabellennamen in der **Felder Bereich** auf der rechten Seite des Bildschirms.</span><span class="sxs-lookup"><span data-stu-id="56dbe-620">To do so, right-click on the table name located in the **FIELDS panel** at the right side of the screen.</span></span> <span data-ttu-id="56dbe-621">Klicken Sie dann auf **Abfrage bearbeiten**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-621">Then click on **Edit Query**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. <span data-ttu-id="56dbe-623">Ein **Power Query-Editor** wird als ein neues Fenster, das Anzeigen Ihrer Tabelle geöffnet.</span><span class="sxs-lookup"><span data-stu-id="56dbe-623">A **Power Query Editor**  will open up as a new window, displaying your table.</span></span> <span data-ttu-id="56dbe-624">Klicken Sie auf das Wort **Datensatz** innerhalb der *Inhalt* -Spalte der Tabelle, um Ihre Inhalte zu visualisieren.</span><span class="sxs-lookup"><span data-stu-id="56dbe-624">Click on the word **Record** within the *Content* column of the table, to visualize your stored content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. <span data-ttu-id="56dbe-626">Klicken Sie auf **Into Tabelle**, an der oberen linken Ecke des Fensters.</span><span class="sxs-lookup"><span data-stu-id="56dbe-626">Click on **Into Table**, at the top-left of the window.</span></span> 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. <span data-ttu-id="56dbe-628">Klicken Sie auf **schließen und übernehmen**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-628">Click on **Close & Apply**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. <span data-ttu-id="56dbe-630">Sobald es abgeschlossen ist, laden die Abfrage, in der **Felder Bereich**, auf der rechten Seite des Bildschirms, aktivieren Sie die Kontrollkästchen für die Parameter **Namen** und **Wert**zu Visualisieren der **MessageContent** Spalteninhalt.</span><span class="sxs-lookup"><span data-stu-id="56dbe-630">Once it has finished loading the query, within the **FIELDS panel**, on the right side of the screen, tick the boxes corresponding to the parameters **Name** and **Value**, to visualize the **MessageContent** column content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. <span data-ttu-id="56dbe-632">Klicken Sie auf die **blaue Datenträgersymbol** am oben links im Fenster zum Speichern Ihrer Arbeit in einem Ordner Ihrer Wahl.</span><span class="sxs-lookup"><span data-stu-id="56dbe-632">Click on the **blue disk icon** at the top left of the window to save your work in a folder of your choice.</span></span>

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. <span data-ttu-id="56dbe-634">Sie können jetzt auf die Schaltfläche "Veröffentlichen" zum Hochladen von der Tabelle in Ihrem Arbeitsbereich klicken.</span><span class="sxs-lookup"><span data-stu-id="56dbe-634">You can now click on the Publish button to upload your table to your Workspace.</span></span> <span data-ttu-id="56dbe-635">Wenn Sie dazu aufgefordert werden, klicken Sie auf **Arbeitsbereich** , und klicken Sie auf *wählen*.</span><span class="sxs-lookup"><span data-stu-id="56dbe-635">When prompted, click **My workspace** and click *Select*.</span></span> <span data-ttu-id="56dbe-636">Warten Sie, um das erfolgreiche Ergebnis der Übermittlung anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-636">Wait for it to display the successful result of the submission.</span></span>

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> <span data-ttu-id="56dbe-639">Im folgende Kapitel ist bestimmte HoloLens.</span><span class="sxs-lookup"><span data-stu-id="56dbe-639">The following Chapter is HoloLens specific.</span></span> <span data-ttu-id="56dbe-640">Powerbi ist zurzeit nicht zur Verfügung als immersive Anwendung, aber im Windows Mixed Reality-Portal (auch bekannt als Cliff House), die desktop-Version ausgeführt werden kann durch die Desktop-app.</span><span class="sxs-lookup"><span data-stu-id="56dbe-640">Power BI is not currently availble as an immersive application, however you can run the desktop version in the Windows Mixed Reality Portal (aka Cliff House), through the Desktop app.</span></span>

## <a name="chapter-16---display-power-bi-data-on-hololens"></a><span data-ttu-id="56dbe-641">Kapitel 16 – zeigen Sie Power BI-Daten in HoloLens</span><span class="sxs-lookup"><span data-stu-id="56dbe-641">Chapter 16 - Display Power BI data on HoloLens</span></span>

1. <span data-ttu-id="56dbe-642">Auf Ihre HoloLens, melden Sie sich bei der **Microsoft Store**, durch Tippen auf das Symbol in der Anwendungsliste den Eintrag.</span><span class="sxs-lookup"><span data-stu-id="56dbe-642">On your HoloLens, log in to the **Microsoft Store**, by tapping on its icon in the applications list.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. <span data-ttu-id="56dbe-644">Suchen und laden die **Power BI** Anwendung.</span><span class="sxs-lookup"><span data-stu-id="56dbe-644">Search and then download the **Power BI** application.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. <span data-ttu-id="56dbe-646">Starten Sie **Power BI** aus der Anwendungsliste.</span><span class="sxs-lookup"><span data-stu-id="56dbe-646">Start **Power BI** from your applications list.</span></span> 

4. <span data-ttu-id="56dbe-647">**Power BI** möglicherweise Fragen Sie sich anmelden, Ihr **Microsoft 365-Konto**.</span><span class="sxs-lookup"><span data-stu-id="56dbe-647">**Power BI** might ask you to login to your **Microsoft 365 account**.</span></span>

5. <span data-ttu-id="56dbe-648">Einmal sollte innerhalb der app der Arbeitsbereich wird standardmäßig angezeigt werden wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="56dbe-648">Once inside the app, the workspace should display by default as shown in the image below.</span></span> <span data-ttu-id="56dbe-649">Wenn, das nicht geschieht, klicken Sie einfach auf das Symbol für den Arbeitsbereich auf der linken Seite des Fensters.</span><span class="sxs-lookup"><span data-stu-id="56dbe-649">If that does not happen, simply click on the workspace icon on the left side of the window.</span></span>

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a><span data-ttu-id="56dbe-651">Ihre fertige Ihrer IoT Hub-Anwendung</span><span class="sxs-lookup"><span data-stu-id="56dbe-651">Your finished your IoT Hub application</span></span>

<span data-ttu-id="56dbe-652">Herzlichen Glückwunsch, Sie haben erfolgreich einen IoT Hub-Dienst, mit einem simulierten Virtual Machine-Edge-Gerät erstellt.</span><span class="sxs-lookup"><span data-stu-id="56dbe-652">Congratulations, you have successfully created an IoT Hub Service, with a simulated Virtual Machine Edge device.</span></span> <span data-ttu-id="56dbe-653">Ihr Gerät kommunizieren kann, die Ergebnisse eines Machine learning-Modell in ein Azure-Tabellendienst, die von einer Azure-Funktionen-App, die in Power BI gelesen und in einer Microsoft HoloLens visualisiert bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="56dbe-653">Your device can  communicate the results of a machine learning model to an Azure Table Service, facilitated by an Azure Function App, which is read into Power BI, and visualized within a Microsoft HoloLens.</span></span>
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="56dbe-655">Bonus-Übungen</span><span class="sxs-lookup"><span data-stu-id="56dbe-655">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="56dbe-656">Übung 1</span><span class="sxs-lookup"><span data-stu-id="56dbe-656">Exercise 1</span></span>

<span data-ttu-id="56dbe-657">Erweitern Sie die messaging-Struktur in der Tabelle gespeichert, und als Diagramm anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="56dbe-657">Expand the messaging structure stored in the table and display it as a graph.</span></span> <span data-ttu-id="56dbe-658">Sie möchten möglicherweise weitere Daten sammeln und speichern Sie sie in der gleichen Tabelle, zu einem späteren Zeitpunkt angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="56dbe-658">You might want to collect more data and store it in the same table, to be later displayed.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="56dbe-659">Übung 2</span><span class="sxs-lookup"><span data-stu-id="56dbe-659">Exercise 2</span></span>

<span data-ttu-id="56dbe-660">Erstellen Sie eine weitere "Camera Capture"-Modul auf dem IoT-Board bereitgestellt werden, damit sie Images erfassen kann, durch die Kamera analysiert werden.</span><span class="sxs-lookup"><span data-stu-id="56dbe-660">Create an additional "camera capture" module to be deployed on the IoT board, so that it can capture images through the camera to be analyzed.</span></span>
