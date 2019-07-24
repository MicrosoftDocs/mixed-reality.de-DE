---
title: Mr und Azure 313-IOT Hub Service
description: In diesem Kurs erfahren Sie, wie Sie Azure IOT Hub-Dienst auf einem virtuellen Computer mit Ubuntu 16,4 implementieren und anschließend die Nachrichten Daten mithilfe von Microsoft hololens oder einem immersiven (VR)-Headset visualisieren.
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Edge, IOT Edge, Tutorial, API, Benachrichtigung, Funktionen, Tabellen, hololens, immersive, VR, IOT, virtueller Computer, Ubuntu, python
ms.openlocfilehash: 93f7dc64426360d2e02b0ee0a9b1796fc8f2b469
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694597"
---
>[!NOTE]
><span data-ttu-id="7d32d-104">Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="7d32d-105">Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.</span><span class="sxs-lookup"><span data-stu-id="7d32d-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="7d32d-106">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="7d32d-107">Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können.</span><span class="sxs-lookup"><span data-stu-id="7d32d-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="7d32d-108">Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="7d32d-109">Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-313-iot-hub-service"></a><span data-ttu-id="7d32d-110">Mr und Azure 313: IOT Hub-Dienst</span><span class="sxs-lookup"><span data-stu-id="7d32d-110">MR and Azure 313: IoT Hub Service</span></span>

![Kurs Ergebnis](images/AzureLabs-Lab313-00.png)

<span data-ttu-id="7d32d-112">In diesem Kurs erfahren Sie, wie Sie eine **Azure IOT Hub Service** auf einem virtuellen Computer implementieren, auf dem das Betriebssystem Ubuntu 16,4 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="7d32d-112">In this course, you will learn how to implement an **Azure IoT Hub Service** on a virtual machine running the Ubuntu 16.4 operating system.</span></span> <span data-ttu-id="7d32d-113">Ein **Azure-Funktionen-App** wird dann zum Empfangen von Nachrichten von Ihrer Ubuntu-VM verwendet und speichert das Ergebnis in einem **Azure-Tabellen Speicherdienst**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-113">An **Azure Function App** will then be used to receive messages from your Ubuntu VM, and store the result within an **Azure Table Service**.</span></span> <span data-ttu-id="7d32d-114">Anschließend können Sie diese Daten mithilfe von **Power BI** auf dem Microsoft hololens oder im immersiven (VR)-Headset anzeigen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-114">You will then be able to view this data using **Power BI** on Microsoft HoloLens or immersive (VR) headset.</span></span>

<span data-ttu-id="7d32d-115">Der Inhalt *dieses Kurses gilt* für IOT Edge Geräte, aber im Rahmen dieses Kurses liegt der Schwerpunkt auf der Umgebung eines virtuellen Computers, sodass der Zugriff auf ein physisches Edgegerät nicht erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="7d32d-115">The content of this course *is applicable* to IoT Edge devices, though for the purpose of this course, the focus will be on a virtual machine environment, so that access to a physical Edge device is not necessary.</span></span>

<span data-ttu-id="7d32d-116">Wenn Sie diesen Kurs abschließen, lernen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="7d32d-116">By completing this course, you will learn to:</span></span>

- <span data-ttu-id="7d32d-117">Stellen Sie ein **IOT Edge Modul** auf einem virtuellen Computer (Ubuntu 16 OS) bereit, der ihr IOT-Gerät darstellt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-117">Deploy an **IoT Edge module** to a Virtual Machine (Ubuntu 16 OS), which will represent your IoT device.</span></span>
- <span data-ttu-id="7d32d-118">Fügen Sie dem Edge-Modul ein **Azure Custom Vision tensorflow-Modell** mit Code hinzu, mit dem im Container gespeicherte Images analysiert werden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-118">Add an **Azure Custom Vision Tensorflow Model** to the Edge module, with code that will analyze images stored in the container.</span></span>
- <span data-ttu-id="7d32d-119">Richten Sie das Modul ein, um die Analyseergebnis Nachricht zurück an den **IOT Hub-Dienst**zu senden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-119">Set up the module to send the analysis result message back to your **IoT Hub Service**.</span></span>
- <span data-ttu-id="7d32d-120">Verwenden Sie eine **Azure-Funktionen-App** , um die Nachricht in einer Azure- **Tabelle**zu speichern.</span><span class="sxs-lookup"><span data-stu-id="7d32d-120">Use an **Azure Function App** to store the message within an **Azure Table**.</span></span>
- <span data-ttu-id="7d32d-121">Richten Sie **Power BI** ein, um die gespeicherte Nachricht zu erfassen und einen Bericht zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-121">Set up **Power BI** to collect the stored message and create a report.</span></span>
- <span data-ttu-id="7d32d-122">Visualisieren Sie Ihre IOT-Nachrichten Daten in **Power BI**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-122">Visualize your IoT message data within **Power BI**.</span></span>

<span data-ttu-id="7d32d-123">Zu den Diensten, die Sie verwenden werden, gehören:</span><span class="sxs-lookup"><span data-stu-id="7d32d-123">The Services you will use include:</span></span>

- <span data-ttu-id="7d32d-124">**Azure IOT Hub** ist ein Microsoft Azure Dienst, mit dem Entwickler IOT-Assets verbinden, überwachen und verwalten können.</span><span class="sxs-lookup"><span data-stu-id="7d32d-124">**Azure IoT Hub** is a Microsoft Azure Service which allows developers to connect, monitor, and manage, IoT assets.</span></span> <span data-ttu-id="7d32d-125">Weitere Informationen finden Sie auf der [Seite **Azure IOT Hub-Dienst** ](https://azure.microsoft.com/en-au/services/iot-hub/).</span><span class="sxs-lookup"><span data-stu-id="7d32d-125">For more information, visit the [**Azure IoT Hub Service** page](https://azure.microsoft.com/en-au/services/iot-hub/).</span></span>

- <span data-ttu-id="7d32d-126">**Azure Container Registry** ist ein Microsoft Azure Dienst, der Entwicklern das Speichern von Container Images für verschiedene Containertypen ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="7d32d-126">**Azure Container Registry** is a Microsoft Azure Service which allows developers to store container images, for various types of containers.</span></span> <span data-ttu-id="7d32d-127">Weitere Informationen finden Sie auf der [Seite **Azure Container Registry-Dienst** ](https://azure.microsoft.com/en-au/services/container-registry/).</span><span class="sxs-lookup"><span data-stu-id="7d32d-127">For more information, visit the [**Azure Container Registry Service** page](https://azure.microsoft.com/en-au/services/container-registry/).</span></span>

- <span data-ttu-id="7d32d-128">Bei **Azure Funktionen-App** handelt es sich um einen Microsoft Azure Dienst, der es Entwicklern ermöglicht, in Azure kleine Code Elemente, "Functions", auszuführen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-128">**Azure Function App** is a Microsoft Azure Service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="7d32d-129">Dies bietet eine Möglichkeit zum Delegieren von Arbeit an die Cloud und nicht an Ihre lokale Anwendung, die viele Vorteile haben kann.</span><span class="sxs-lookup"><span data-stu-id="7d32d-129">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="7d32d-130">**Azure Functions** unterstützt mehrere Entwicklungs Sprachen, wie\#z.\#b. C, F, Node. js, Java und PHP.</span><span class="sxs-lookup"><span data-stu-id="7d32d-130">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="7d32d-131">Weitere Informationen finden Sie auf der [Seite **Azure Functions** ](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="7d32d-131">For more information, visit the [**Azure Functions** page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

- <span data-ttu-id="7d32d-132">**Azure Storage: Tabellen** sind ein Microsoft Azure Dienst, mit dem Entwickler strukturierte, nicht-SQL-Daten in der Cloud speichern können, sodass Sie überall problemlos zugänglich sind.</span><span class="sxs-lookup"><span data-stu-id="7d32d-132">**Azure Storage: Tables** is a Microsoft Azure Service, which allows developers to store structured, non-SQL, data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="7d32d-133">Der Dienst verfügt über einen Schema losen Entwurf, der die Weiterentwicklung von Tabellen nach Bedarf ermöglicht und daher sehr flexibel ist.</span><span class="sxs-lookup"><span data-stu-id="7d32d-133">The Service boasts a schema-less design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="7d32d-134">Weitere Informationen finden Sie auf der Seite mit den [ **Azure-Tabellen** .](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="7d32d-134">For more information, visit the [**Azure Tables** page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="7d32d-135">In diesem Kurs erfahren Sie, wie Sie den IOT Hub-Dienst einrichten und verwenden und dann eine Antwort visualisieren, die von einem Gerät bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="7d32d-135">This course will teach you how to setup and use the IoT Hub Service, and then visualize a response provided by a device.</span></span> <span data-ttu-id="7d32d-136">Sie müssen diese Konzepte auf eine benutzerdefinierte IOT Hub Service-Einrichtung anwenden, die Sie möglicherweise erstellen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-136">It will be up to you to apply these concepts to a custom IoT Hub Service setup, which you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="7d32d-137">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="7d32d-137">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="7d32d-138">Natürlich</span><span class="sxs-lookup"><span data-stu-id="7d32d-138">Course</span></span></th><th style="width:150px"> <span data-ttu-id="7d32d-139"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="7d32d-139"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="7d32d-140"><a href="immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="7d32d-140"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="7d32d-141">Mr und Azure 313: IOT Hub-Dienst</span><span class="sxs-lookup"><span data-stu-id="7d32d-141">MR and Azure 313: IoT Hub Service</span></span></td><td style="text-align: center;"> <span data-ttu-id="7d32d-142">✔️</span><span class="sxs-lookup"><span data-stu-id="7d32d-142">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="7d32d-143">✔️</span><span class="sxs-lookup"><span data-stu-id="7d32d-143">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="7d32d-144">Vorraussetzungen</span><span class="sxs-lookup"><span data-stu-id="7d32d-144">Prerequisites</span></span>

<span data-ttu-id="7d32d-145">Aktuelle Voraussetzungen für die Entwicklung mit gemischter Realität, einschließlich der Microsoft hololens, finden Sie im Artikel [Installieren der Tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) .</span><span class="sxs-lookup"><span data-stu-id="7d32d-145">For the most up-to-date prerequisites for developing with mixed reality, including with the Microsoft HoloLens, visit the [Install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article.</span></span>

> [!NOTE]
> <span data-ttu-id="7d32d-146">Dieses Lernprogramm ist für Entwickler konzipiert, die über die grundlegende Verwendung von python verfügen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-146">This tutorial is designed for developers who have basic experience with Python.</span></span> <span data-ttu-id="7d32d-147">Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Juli 2018).</span><span class="sxs-lookup"><span data-stu-id="7d32d-147">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="7d32d-148">Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](install-the-tools.md) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="7d32d-148">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than that listed below.</span></span>

<span data-ttu-id="7d32d-149">Folgende Hardware und Software ist erforderlich:</span><span class="sxs-lookup"><span data-stu-id="7d32d-149">The following hardware and software is required:</span></span>

- <span data-ttu-id="7d32d-150">Windows 10 Fall Creators Update (oder höher), **Entwicklermodus aktiviert**</span><span class="sxs-lookup"><span data-stu-id="7d32d-150">Windows 10 Fall Creators Update (or later), **Developer Mode enabled**</span></span>

    > [!WARNING]
    > <span data-ttu-id="7d32d-151">Es ist nicht möglich, einen virtuellen Computer mit Hyper-V unter Windows 10 Home Edition auszuführen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-151">You cannot run a Virtual Machine using Hyper-V on Windows 10 Home Edition.</span></span>

- <span data-ttu-id="7d32d-152">Windows 10 SDK (neueste Version)</span><span class="sxs-lookup"><span data-stu-id="7d32d-152">Windows 10 SDK (latest version)</span></span>
- <span data-ttu-id="7d32d-153">Hololens, **Entwicklermodus aktiviert**</span><span class="sxs-lookup"><span data-stu-id="7d32d-153">A HoloLens, **Developer Mode enabled**</span></span>
- <span data-ttu-id="7d32d-154">Visual Studio 2017.15.4 (nur für den Zugriff auf die Azure-Cloud-Explorer verwendet)</span><span class="sxs-lookup"><span data-stu-id="7d32d-154">Visual Studio 2017.15.4 (Only used to access the Azure Cloud Explorer)</span></span>
- <span data-ttu-id="7d32d-155">Internet Zugriff für Azure und für IOT Hub-Dienst.</span><span class="sxs-lookup"><span data-stu-id="7d32d-155">Internet Access for Azure, and for IoT Hub Service.</span></span> <span data-ttu-id="7d32d-156">Weitere Informationen finden Sie [unter diesem Link zur IOT Hub Dienst Seite](https://azure.microsoft.com/en-au/services/iot-hub/) .</span><span class="sxs-lookup"><span data-stu-id="7d32d-156">For more information, please follow this [link to IoT Hub Service page](https://azure.microsoft.com/en-au/services/iot-hub/)</span></span>
- <span data-ttu-id="7d32d-157">Ein Machine Learning-Modell.</span><span class="sxs-lookup"><span data-stu-id="7d32d-157">A machine learning model.</span></span> <span data-ttu-id="7d32d-158">Wenn Sie nicht über ein eigenes Modell verfügen, [können Sie das mit diesem Kurs bereitgestellte Modell verwenden](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span><span class="sxs-lookup"><span data-stu-id="7d32d-158">If you do not have your own ready to use model, [you can use the model provided with this course](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).</span></span>
- <span data-ttu-id="7d32d-159">Auf Ihrem Windows 10-Entwicklungs Computer ist **Hyper-V-** Software aktiviert.</span><span class="sxs-lookup"><span data-stu-id="7d32d-159">**Hyper-V** software enabled on your Windows 10 development machine.</span></span>
- <span data-ttu-id="7d32d-160">Ein virtueller Computer, auf dem Ubuntu (16,4 oder 18,4) ausgeführt wird und der auf dem Entwicklungs Computer ausgeführt wird. Alternativ können Sie einen separaten Computer mit Linux (Ubuntu 16,4 oder 18,4) verwenden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-160">A Virtual Machine running Ubuntu (16.4 or 18.4), running on your development machine or alternatively you can use a separate computer running Linux (Ubuntu 16.4 or 18.4).</span></span> <span data-ttu-id="7d32d-161">Weitere Informationen zum Erstellen eines virtuellen Computers unter Windows mit Hyper-V finden Sie im [Kapitel "bevor Sie beginnen"](#before-you-start). (https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="7d32d-161">You can find more information on how to create a VM on Windows using Hyper-V in the ["Before you Start" chapter](#before-you-start).(https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).</span></span>  



### <a name="before-you-start"></a><span data-ttu-id="7d32d-162">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="7d32d-162">Before you start</span></span>

1. <span data-ttu-id="7d32d-163">Richten Sie Ihre hololens ein, und testen Sie Sie.</span><span class="sxs-lookup"><span data-stu-id="7d32d-163">Set up and test your HoloLens.</span></span> <span data-ttu-id="7d32d-164">Wenn Sie Unterstützung für die Einrichtung ihrer hololens benötigen, [besuchen Sie den Artikel zum Einrichten von hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="7d32d-164">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span>
2. <span data-ttu-id="7d32d-165">Es empfiehlt sich, eine **Kalibrierung** und **Sensor** Optimierung durchzuführen, wenn Sie mit der Entwicklung einer neuen hololens-App beginnen (manchmal kann es hilfreich sein, diese Aufgaben für jeden Benutzer auszuführen).</span><span class="sxs-lookup"><span data-stu-id="7d32d-165">It is a good idea to perform **Calibration** and **Sensor Tuning** when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span>

<span data-ttu-id="7d32d-166">Hilfe zur Kalibrierung finden Sie unter diesem [Link zum Artikel zur hololens-Kalibrierung](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="7d32d-166">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="7d32d-167">Hilfe zur Sensor Optimierung finden Sie unter diesem [Link zum Artikel zur Überwachung von hololens-Sensoren](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="7d32d-167">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

3. <span data-ttu-id="7d32d-168">Richten Sie Ihren **virtuellen Ubuntu-Computer** mithilfe von **Hyper-V**ein.</span><span class="sxs-lookup"><span data-stu-id="7d32d-168">Set up your **Ubuntu Virtual Machine** using **Hyper-V**.</span></span> <span data-ttu-id="7d32d-169">Die folgenden Ressourcen helfen Ihnen bei diesem Vorgang.</span><span class="sxs-lookup"><span data-stu-id="7d32d-169">The following resources will help you with the process.</span></span>
    1.  <span data-ttu-id="7d32d-170">Befolgen Sie zuerst den folgenden Link, um die ISO-Datei von [Ubuntu 16.04.4 LTS (xenial Xerus) herunterzuladen](http://au.releases.ubuntu.com/16.04/).</span><span class="sxs-lookup"><span data-stu-id="7d32d-170">First, follow this link to [download the Ubuntu 16.04.4 LTS (Xenial Xerus) ISO](http://au.releases.ubuntu.com/16.04/).</span></span> <span data-ttu-id="7d32d-171">Wählen Sie das **amd64-Desktop Image (64-Bit-PC)** aus.</span><span class="sxs-lookup"><span data-stu-id="7d32d-171">Select the **64-bit PC (AMD64) desktop image**.</span></span>
    2.  <span data-ttu-id="7d32d-172">Stellen Sie sicher, dass **Hyper-V** auf Ihrem Windows 10-Computer aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="7d32d-172">Make sure **Hyper-V** is enabled on your Windows 10 machine.</span></span> <span data-ttu-id="7d32d-173">Unter diesem Link finden Sie Anleitungen zum [Installieren und Aktivieren von Hyper-V unter Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span><span class="sxs-lookup"><span data-stu-id="7d32d-173">You can follow this link for guidance on [installing and enabling Hyper-V on Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).</span></span>
    3.  <span data-ttu-id="7d32d-174">Starten Sie Hyper-V, und erstellen Sie einen neuen virtuellen Ubuntu-Computer.</span><span class="sxs-lookup"><span data-stu-id="7d32d-174">Start Hyper-V and create a new Ubuntu VM.</span></span> <span data-ttu-id="7d32d-175">Unter diesem Link finden Sie eine Schritt-für- [Schritt-Anleitung zum Erstellen eines virtuellen Computers mit Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span><span class="sxs-lookup"><span data-stu-id="7d32d-175">You can follow this link for a [step by step guide on how to create a VM with Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine).</span></span> <span data-ttu-id="7d32d-176">Wenn Sie die **Option "Betriebssystem von einer Start baren Image Datei installieren"** angefordert haben, wählen Sie die zuvor heruntergeladene **Ubuntu-ISO** -Datei aus.</span><span class="sxs-lookup"><span data-stu-id="7d32d-176">When requested to **"Install an operating system from a bootable image file"**, select the **Ubuntu ISO** you have download earlier.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7d32d-177">Die Verwendung von **Hyper-V Quick Create** ist nicht empfehlenswert.</span><span class="sxs-lookup"><span data-stu-id="7d32d-177">Using **Hyper-V Quick Create** is not suggested.</span></span>  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a><span data-ttu-id="7d32d-178">Kapitel 1: Abrufen des Custom Vision Modells</span><span class="sxs-lookup"><span data-stu-id="7d32d-178">Chapter 1 - Retrieve the Custom Vision model</span></span>

<span data-ttu-id="7d32d-179">In diesem Kurs haben Sie Zugriff auf ein [vorgefertigter Custom Vision Modell](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) , das Tastaturen und Mäuse von Bildern erkennt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-179">With this course you will have access to a [pre-built Custom Vision model](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) that detects keyboards and mice from images.</span></span> <span data-ttu-id="7d32d-180">Wenn Sie diese verwenden, fahren Sie mit [Kapitel 2](#chapter-2---the-container-registry-service)fort.</span><span class="sxs-lookup"><span data-stu-id="7d32d-180">If you use this, proceed to [Chapter 2](#chapter-2---the-container-registry-service).</span></span>

<span data-ttu-id="7d32d-181">Sie können jedoch die folgenden Schritte ausführen, wenn Sie Ihr eigenes Custom Vision Modell verwenden möchten:</span><span class="sxs-lookup"><span data-stu-id="7d32d-181">However, you can follow these steps if you wish to use your own Custom Vision model:</span></span>

1. <span data-ttu-id="7d32d-182">Wechseln Sie in Ihrem **Custom Vision Projekt** zur Registerkarte **Leistung** .</span><span class="sxs-lookup"><span data-stu-id="7d32d-182">In your **Custom Vision Project** go to the **Performance** tab.</span></span>

    > [!WARNING]
    > <span data-ttu-id="7d32d-183">Ihr Modell muss eine *kompakte* Domäne verwenden, um das Modell zu exportieren.</span><span class="sxs-lookup"><span data-stu-id="7d32d-183">Your model must use a *compact* domain, to export the model.</span></span> <span data-ttu-id="7d32d-184">Sie können die Modell Domäne in den Einstellungen für Ihr Projekt ändern.</span><span class="sxs-lookup"><span data-stu-id="7d32d-184">You can change your models domain in the settings for your project.</span></span>

    ![Registerkarte Leistung](images/AzureLabs-Lab313-01.png)

2. <span data-ttu-id="7d32d-186">Wählen Sie die **Iterationen** aus, die Sie exportieren möchten, und klicken Sie auf **exportieren**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-186">Select the **Iteration** you want to export and click on **Export**.</span></span> <span data-ttu-id="7d32d-187">Ein Blatt wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-187">A blade will appear.</span></span>

    ![Blatt "Exportieren"](images/AzureLabs-Lab313-02.png)

3. <span data-ttu-id="7d32d-189">Klicken Sie auf dem Blatt auf **docker-Datei**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-189">In the blade click **Docker File**.</span></span>

    ![docker auswählen](images/AzureLabs-Lab313-03.png)

4. <span data-ttu-id="7d32d-191">Klicken Sie im Dropdown Menü auf **Linux** , und klicken Sie dann auf **herunterladen**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-191">Click **Linux** in the drop-down menu and then click on **Download**.</span></span>

    ![Auf herunterladen klicken](images/AzureLabs-Lab313-04.png)

5. <span data-ttu-id="7d32d-193">Entzippen Sie den Inhalt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-193">Unzip the content.</span></span> <span data-ttu-id="7d32d-194">Sie werden Sie später in diesem Kurs verwenden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-194">You will use it later in this course.</span></span>

## <a name="chapter-2---the-container-registry-service"></a><span data-ttu-id="7d32d-195">Kapitel 2: der Container Registry-Dienst</span><span class="sxs-lookup"><span data-stu-id="7d32d-195">Chapter 2 - The Container Registry Service</span></span>

<span data-ttu-id="7d32d-196">Der **Container Registry-Dienst** ist das Repository, das zum Hosten Ihrer Container verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="7d32d-196">The **Container Registry Service** is the repository used to host your containers.</span></span>

<span data-ttu-id="7d32d-197">Der **IOT Hub-Dienst** , den Sie in diesem Kurs erstellen und verwenden, bezieht sich auf **Container Registry Dienst** , um die Container zu erhalten, die auf Ihrem Edge-Gerät bereitgestellt werden sollen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-197">The **IoT Hub Service** that you will build and use in this course, refers to **Container Registry Service** to obtain the containers to deploy in your Edge Device.</span></span>

1. <span data-ttu-id="7d32d-198">Befolgen Sie zuerst [den Link zum Azure-Portal](https://portal.azure.com/), und melden Sie sich mit Ihren Anmelde Informationen an.</span><span class="sxs-lookup"><span data-stu-id="7d32d-198">First, follow this [link to the Azure Portal](https://portal.azure.com/), and login with your credentials.</span></span>

2. <span data-ttu-id="7d32d-199">Wechseln Sie zu **Ressource erstellen** , und suchen Sie nach **Container Registry**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-199">Go to **Create a resource** and look for **Container Registry**.</span></span>

    ![Container Registrierung](images/AzureLabs-Lab313-05.png)

3. <span data-ttu-id="7d32d-201">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-201">Click on **Create**.</span></span>

    ![](images/AzureLabs-Lab313-06.png)

4. <span data-ttu-id="7d32d-202">Legen Sie die Dienst Setup Parameter fest:</span><span class="sxs-lookup"><span data-stu-id="7d32d-202">Set the Service setup parameters:</span></span>

    1. <span data-ttu-id="7d32d-203">Fügen Sie einen Namen für das Projekt ein. in diesem Beispiel wird er als " **iotcregistry**" bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="7d32d-203">Insert a name for your project, In this example its called **IoTCRegistry**.</span></span>

    2. <span data-ttu-id="7d32d-204">Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** .</span><span class="sxs-lookup"><span data-stu-id="7d32d-204">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="7d32d-205">Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-205">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="7d32d-206">Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Kursen) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.</span><span class="sxs-lookup"><span data-stu-id="7d32d-206">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    3. <span data-ttu-id="7d32d-207">Legen Sie den Speicherort des Dienstanbieter fest.</span><span class="sxs-lookup"><span data-stu-id="7d32d-207">Set the location of the Service.</span></span>

    4. <span data-ttu-id="7d32d-208">Legen Sie **Administrator Benutzer** auf **aktivieren**fest.</span><span class="sxs-lookup"><span data-stu-id="7d32d-208">Set **Admin user** to **Enable**.</span></span>

    5. <span data-ttu-id="7d32d-209">Legen Sie **SKU** auf **Basic**fest.</span><span class="sxs-lookup"><span data-stu-id="7d32d-209">Set **SKU** to **Basic**.</span></span> 

    ![](images/AzureLabs-Lab313-07.png)

5. <span data-ttu-id="7d32d-210">Klicken Sie auf **Erstellen** , und warten Sie, bis die Dienste erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-210">Click **Create** and wait for the Services to be created.</span></span> 

6. <span data-ttu-id="7d32d-211">Sobald die Benachrichtigung angezeigt wird, dass die *Container Registry*erfolgreich erstellt wurde, klicken Sie auf **zu Ressource** wechseln, um zur Seite des Diensts umgeleitet zu gelangen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-211">Once the notification pops up informing you of the successful creation of the *Container Registry*, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![](images/AzureLabs-Lab313-08.png)

7. <span data-ttu-id="7d32d-212">Klicken Sie auf der Seite *Container Registry* Dienst auf **Zugriffsschlüssel**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-212">In the *Container Registry* Service page, click on **Access keys**.</span></span>

8. <span data-ttu-id="7d32d-213">Notieren Sie sich (Sie können den Editor verwenden) der folgenden Parameter:</span><span class="sxs-lookup"><span data-stu-id="7d32d-213">Take note (you could use your Notepad) of the following parameters:</span></span>
    1. <span data-ttu-id="7d32d-214">**Anmelde Server**</span><span class="sxs-lookup"><span data-stu-id="7d32d-214">**Login Server**</span></span>
    2. <span data-ttu-id="7d32d-215">**User**</span><span class="sxs-lookup"><span data-stu-id="7d32d-215">**Username**</span></span>
    3. <span data-ttu-id="7d32d-216">**Kennwort**</span><span class="sxs-lookup"><span data-stu-id="7d32d-216">**Password**</span></span>

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a><span data-ttu-id="7d32d-217">Kapitel 3: der IOT Hub-Dienst</span><span class="sxs-lookup"><span data-stu-id="7d32d-217">Chapter 3 - The IoT Hub Service</span></span>

<span data-ttu-id="7d32d-218">Nun beginnen Sie mit der Erstellung und Einrichtung Ihres **IOT Hub Dienstanbieter**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-218">Now you will begin the creation and setup of your **IoT Hub Service**.</span></span>

1. <span data-ttu-id="7d32d-219">Wenn Sie noch nicht angemeldet sind, melden Sie sich beim [Azure-Portal](https://portal.azure.com)an.</span><span class="sxs-lookup"><span data-stu-id="7d32d-219">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="7d32d-220">Nachdem Sie sich angemeldet haben, klicken Sie in der oberen linken Ecke auf **Ressource erstellen** , suchen Sie nach **IOT Hub**, und drücken Sie die **Eingabe**Taste.</span><span class="sxs-lookup"><span data-stu-id="7d32d-220">Once logged in, click on **Create a resource** in the top left corner, and search for **IoT Hub**, and click **Enter**.</span></span>

 ![Suchen nach Speicherkonto](images/AzureLabs-Lab313-10.png)

3.  <span data-ttu-id="7d32d-222">Auf der neuen Seite wird eine Beschreibung des **Speicherkonto** Dienstanbieter bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-222">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="7d32d-223">Klicken Sie unten links in dieser Eingabeaufforderung auf die Schaltfläche **Erstellen** , um eine Instanz dieses Dienstanbieter zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-223">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![Speicher Instanz erstellen](images/AzureLabs-Lab313-11.png)

4.  <span data-ttu-id="7d32d-225">Nachdem Sie auf **Erstellen**geklickt haben, wird ein Panel angezeigt:</span><span class="sxs-lookup"><span data-stu-id="7d32d-225">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="7d32d-226">Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** .</span><span class="sxs-lookup"><span data-stu-id="7d32d-226">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="7d32d-227">Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-227">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="7d32d-228">Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Kursen) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.</span><span class="sxs-lookup"><span data-stu-id="7d32d-228">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="7d32d-229">Weitere Informationen zu Azure-Ressourcengruppen finden Sie unter diesem [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="7d32d-229">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>


    2. <span data-ttu-id="7d32d-230">Wählen Sie einen geeigneten **Speicherort** aus (verwenden Sie den gleichen Speicherort für alle Dienste, die Sie in diesem Kurs erstellen).</span><span class="sxs-lookup"><span data-stu-id="7d32d-230">Select an appropriate **Location** (Use the same location across all the Services you create in this course).</span></span>

    3. <span data-ttu-id="7d32d-231">Fügen Sie den gewünschten **Namen** für diese Dienst Instanz ein.</span><span class="sxs-lookup"><span data-stu-id="7d32d-231">Insert your desired **Name** for this Service instance.</span></span>    

5.  <span data-ttu-id="7d32d-232">Klicken Sie unten auf der Seite auf weiter **: Größe und Skalierung**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-232">On the bottom of the page click on **Next: Size and scale**.</span></span>

    ![Speicher Instanz erstellen](images/AzureLabs-Lab313-12.png)

6.  <span data-ttu-id="7d32d-234">Wählen Sie auf dieser Seite die **Preis-und Skalierungs** Ebene aus (wenn es sich um Ihre erste IOT Hub Dienst Instanz handelt, sollte Ihnen ein Free-Tarif zur Verfügung stehen).</span><span class="sxs-lookup"><span data-stu-id="7d32d-234">In this page, select your **Pricing and scale tier** (if this is your first IoT Hub Service instance, a free tier should be available to you).</span></span>  

7.  <span data-ttu-id="7d32d-235">Klicken Sie auf **überprüfen und erstellen**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-235">Click on **Review + Create**.</span></span>

    ![Speicher Instanz erstellen](images/AzureLabs-Lab313-13.png)

8.  <span data-ttu-id="7d32d-237">Überprüfen Sie die Einstellungen, und klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-237">Review your settings and click on **Create**.</span></span>

    ![Speicher Instanz erstellen](images/AzureLabs-Lab313-14.png)

9. <span data-ttu-id="7d32d-239">Sobald die Benachrichtigung angezeigt wird, dass Sie die erfolgreiche Erstellung des *IOT Hub* Diensts erhalten hat, klicken Sie auf **zu Ressource** wechseln, um zur Seite des Diensts umgeleitet zu gelangen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-239">Once the notification pops up informing you of the successful creation of the *IoT Hub* Service, click on **Go to resource** to be redirected to your Service page.</span></span>

    ![Speicher Instanz erstellen](images/AzureLabs-Lab313-15.png)

10. <span data-ttu-id="7d32d-241">Scrollen Sie auf der linken Seite nach links, bis die *Automatische Geräteverwaltung*angezeigt wird, und klicken Sie auf **IOT Edge**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-241">Scroll the side panel on the left until you see *Automatic Device Management*, the click on **IoT Edge**.</span></span>

    ![Speicher Instanz erstellen](images/AzureLabs-Lab313-16.png)

11. <span data-ttu-id="7d32d-243">Klicken Sie im Fenster, das rechts angezeigt wird, auf **IOT Edge Gerät hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-243">In the window that appears to the right, click on **Add IoT Edge Device**.</span></span> <span data-ttu-id="7d32d-244">Auf der rechten Seite wird ein Blatt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-244">A blade will appear to the right.</span></span>

12. <span data-ttu-id="7d32d-245">Geben Sie auf dem Blatt das neue Gerät als **Geräte-ID** (Name Ihrer Wahl) an.</span><span class="sxs-lookup"><span data-stu-id="7d32d-245">In the blade, provide your new device a **Device ID** (a name of your choice).</span></span> <span data-ttu-id="7d32d-246">Klicken Sie dann auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-246">Then, click **Save**.</span></span> <span data-ttu-id="7d32d-247">Der *primäre* und der *sekundäre Schlüssel* werden automatisch generiert, wenn Sie die **Automatische Generierung** von aktivierten durchführen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-247">The *Primary* and *Secondary Keys* will auto generate, if you have **Auto Generate** ticked.</span></span>

    ![Speicher Instanz erstellen](images/AzureLabs-Lab313-17.png)

13. <span data-ttu-id="7d32d-249">Navigieren Sie zurück zum Abschnitt *IOT Edge Geräte* , in dem Ihr neues Gerät aufgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="7d32d-249">You will navigate back to the *IoT Edge Devices* section, where your new device will be listed.</span></span> <span data-ttu-id="7d32d-250">Klicken Sie auf das neue Gerät (in der Abbildung unten rot dargestellt).</span><span class="sxs-lookup"><span data-stu-id="7d32d-250">Click on your new device (outlined in red in the below image).</span></span> 

    ![Speicher Instanz erstellen](images/AzureLabs-Lab313-18.png)

14. <span data-ttu-id="7d32d-252">Erstellen Sie auf der angezeigten Seite *Geräte Details* eine Kopie der **Verbindungs Zeichenfolge** (Primärschlüssel).</span><span class="sxs-lookup"><span data-stu-id="7d32d-252">On the *Device Details* page that appears, take a copy of the **Connection String** (primary key).</span></span>

    ![Speicher Instanz erstellen](images/AzureLabs-Lab313-19.png)

15. <span data-ttu-id="7d32d-254">Wechseln Sie zurück zum Bereich auf der linken Seite, und klicken Sie auf SAS- *Richtlinien*, um ihn zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-254">Go back to the panel on the left, and click *Shared access policies*, to open it.</span></span> 

16. <span data-ttu-id="7d32d-255">Klicken Sie auf der Seite, die angezeigt wird, auf **iothubowner**, und rechts neben dem Bildschirm wird ein Blatt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-255">On the page that appears, click **iothubowner**, and a blade will appear to the right of the screen.</span></span> 

17. <span data-ttu-id="7d32d-256">Notieren Sie sich (in Ihrem Editor) die **Verbindungs Zeichenfolge** (Primärschlüssel) für die spätere Verwendung beim Festlegen der *Verbindungs Zeichenfolge* auf Ihr Gerät.</span><span class="sxs-lookup"><span data-stu-id="7d32d-256">Take note (on your Notepad) of the **Connection string** (primary key), for later use when setting the *Connection String* to your device.</span></span>

    ![Speicher Instanz erstellen](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a><span data-ttu-id="7d32d-258">Kapitel 4: Einrichten der Entwicklungsumgebung</span><span class="sxs-lookup"><span data-stu-id="7d32d-258">Chapter 4 - Setting up the development environment</span></span>

<span data-ttu-id="7d32d-259">Zum Erstellen und Bereitstellen von Modulen für *IOT Hub Edge*müssen die folgenden Komponenten auf dem Entwicklungs Computer installiert sein, auf dem Windows 10 ausgeführt wird:</span><span class="sxs-lookup"><span data-stu-id="7d32d-259">In order to create and deploy modules for *IoT Hub Edge*, you will require the following components installed on your development machine running Windows 10:</span></span>

1.  <span data-ttu-id="7d32d-260">[Docker für Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows)werden Sie aufgefordert, ein Konto zu erstellen, das heruntergeladen werden kann.</span><span class="sxs-lookup"><span data-stu-id="7d32d-260">[Docker for Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), it will ask you to create an account to be able to download.</span></span> 

    <span data-ttu-id="7d32d-261">[![docker für Windows herunterladen](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span><span class="sxs-lookup"><span data-stu-id="7d32d-261">[![download docker for windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="7d32d-262">Docker erfordert, dass *Windows 10 pro*, *Enterprise 14393*oder *Windows Server 2016 RTM*ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="7d32d-262">Docker requires *Windows 10 PRO*, *Enterprise 14393*, or *Windows Server 2016 RTM*, to run.</span></span> <span data-ttu-id="7d32d-263">Wenn Sie andere Versionen von Windows 10 ausführen, können Sie versuchen, docker mithilfe der [docker-Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/)zu installieren.</span><span class="sxs-lookup"><span data-stu-id="7d32d-263">If you are running other versions of Windows 10, you can try installing Docker using the [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).</span></span>

2.  <span data-ttu-id="7d32d-264">[Python 3,6](https://www.python.org/downloads/).</span><span class="sxs-lookup"><span data-stu-id="7d32d-264">[Python 3.6](https://www.python.org/downloads/).</span></span>

    <span data-ttu-id="7d32d-265">[![Herunterladen von Python 3,6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span><span class="sxs-lookup"><span data-stu-id="7d32d-265">[![download python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)</span></span>

3.  <span data-ttu-id="7d32d-266">[Visual Studio Code (auch bekannt als vs Code)](https://code.visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="7d32d-266">[Visual Studio Code (also known as VS Code)](https://code.visualstudio.com/download).</span></span>

    <span data-ttu-id="7d32d-267">[![Download vs Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span><span class="sxs-lookup"><span data-stu-id="7d32d-267">[![download VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)</span></span>

<span data-ttu-id="7d32d-268">Nach der Installation der oben erwähnten Software müssen Sie den Computer neu starten.</span><span class="sxs-lookup"><span data-stu-id="7d32d-268">After installing the software mentioned above, you will need to restart your machine.</span></span>

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a><span data-ttu-id="7d32d-269">Kapitel 5: Einrichten der Ubuntu-Umgebung</span><span class="sxs-lookup"><span data-stu-id="7d32d-269">Chapter 5 - Setting up the Ubuntu environment</span></span>

<span data-ttu-id="7d32d-270">Nun können Sie mit dem Einrichten Ihres Geräts fortfahren, auf dem **Ubuntu OS ausgeführt**wird.</span><span class="sxs-lookup"><span data-stu-id="7d32d-270">Now you can move on to setting up your device **running Ubuntu OS**.</span></span> <span data-ttu-id="7d32d-271">Führen Sie die folgenden Schritte aus, um die erforderliche Software zu installieren, um Ihre Container auf Ihrem Board bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="7d32d-271">Follow the steps below, to install the necessary software, to deploy your containers on your board:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7d32d-272">Sie sollten den Terminal Befehlen vor dem Ausführen von **sudo** immer als Administrator Benutzer vorangestellt sein.</span><span class="sxs-lookup"><span data-stu-id="7d32d-272">You should always precede the terminal commands with **sudo** to run as admin user.</span></span> <span data-ttu-id="7d32d-273">d</span><span class="sxs-lookup"><span data-stu-id="7d32d-273">i.e:</span></span>
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  <span data-ttu-id="7d32d-274">Öffnen Sie das **Ubuntu-Terminal**, und installieren Sie **PIP**mit dem folgenden Befehl:</span><span class="sxs-lookup"><span data-stu-id="7d32d-274">Open the **Ubuntu Terminal**, and use the following command to install **pip**:</span></span>

    > [! Hinweis]<span data-ttu-id="7d32d-275"> Sie können das *Terminal* problemlos mithilfe der Tastenkombination öffnen: **STRG + ALT + T**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-275"> You can open *Terminal* very easily through using the keyboard shortcut: **Ctrl + Alt + T**.</span></span>

    ```bash
        sudo apt-get install python-pip
    ```

2.  <span data-ttu-id="7d32d-276">In diesem Kapitel werden Sie ggf. vom *Terminal*aufgefordert, die Berechtigung zur Verwendung Ihres Geräte Speichers zu erhalten, und Sie können **y/n** (yes oder No) eingeben, geben Sie **"y"** ein, und drücken Sie dann die **Eingabe** Taste, um zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="7d32d-276">Throughout this Chapter, you may be prompted, by *Terminal*, for permission to use your device storage, and for you to input **y/n** (yes or no), type **'y'**, and then press the **Enter** key, to accept.</span></span>

3.  <span data-ttu-id="7d32d-277">Nachdem dieser Befehl abgeschlossen ist, verwenden Sie den folgenden Befehl zum Installieren von **curl**:</span><span class="sxs-lookup"><span data-stu-id="7d32d-277">Once that command has completed, use the following command to install **curl**:</span></span>

    ```bash
        sudo apt install curl
    ```

4.  <span data-ttu-id="7d32d-278">Verwenden Sie nach der Installation von **PIP** und **curl** den folgenden Befehl, um die **IOT Edge Runtime**zu installieren. Dies ist erforderlich, um die Module auf Ihrem Board bereitzustellen und zu steuern:</span><span class="sxs-lookup"><span data-stu-id="7d32d-278">Once **pip** and **curl** are installed, use the following command to install the **IoT Edge runtime**, this is necessary to deploy and control the modules on your board:</span></span>

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

5. <span data-ttu-id="7d32d-279">An diesem Punkt werden Sie aufgefordert, die *Lauf Zeit Konfigurationsdatei*zu öffnen, um die **Geräte Verbindungs Zeichenfolge**einzufügen, die Sie im Editor notiert haben (in Ihrem Editor), wenn Sie den **IOT Hub-Dienst** erstellen (in[Schritt 14 von Kapitel 3](#chapter-3---the-iot-hub-service)).</span><span class="sxs-lookup"><span data-stu-id="7d32d-279">At this point you will be prompted to open up the *runtime config file*, to insert the **Device Connection String**, that you noted down (in your Notepad), when creating the **IoT Hub Service** ([at step 14, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="7d32d-280">Führen Sie die folgende Zeile im Terminal aus, um diese Datei zu öffnen:</span><span class="sxs-lookup"><span data-stu-id="7d32d-280">Run the following line on the terminal to open that file:</span></span>

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. <span data-ttu-id="7d32d-281">Die Datei " **config. YAML** " wird angezeigt und kann nun bearbeitet werden:</span><span class="sxs-lookup"><span data-stu-id="7d32d-281">The **config.yaml** file will be displayed, ready for you to edit:</span></span>

    > [!WARNING]
    > <span data-ttu-id="7d32d-282">Wenn diese Datei geöffnet wird, kann Sie etwas verwirrend sein.</span><span class="sxs-lookup"><span data-stu-id="7d32d-282">When this file opens, it may be somewhat confusing.</span></span> <span data-ttu-id="7d32d-283">Sie werden diese Datei im *Terminal* selbst bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="7d32d-283">You will be text editing this file, within the *Terminal* itself.</span></span> 

    1.  <span data-ttu-id="7d32d-284">Verwenden Sie die Pfeiltasten auf der Tastatur, um einen Bildlauf nach unten durchführen (Sie müssen einen Bildlauf nach unten durchführen), um die Zeile zu erreichen, die Folgendes enthält:</span><span class="sxs-lookup"><span data-stu-id="7d32d-284">Use the arrow keys on your keyboard to scroll down (you will need to scroll down a little way), to reach the line containing":</span></span>

        <span data-ttu-id="7d32d-285">**"\<GERÄTE VERBINDUNGS ZEICHENFOLGE HIER HINZUFÜGEN >** ".</span><span class="sxs-lookup"><span data-stu-id="7d32d-285">"**\<ADD DEVICE CONNECTION STRING HERE>**".</span></span>

    2. <span data-ttu-id="7d32d-286">Ersatz Linie, **einschließlich der Klammern**, mit der **Geräte Verbindungs Zeichenfolge** , die Sie zuvor notiert haben.</span><span class="sxs-lookup"><span data-stu-id="7d32d-286">Substitute line, **including the brackets**, with the **Device Connection String** you have noted earlier.</span></span>

7. <span data-ttu-id="7d32d-287">Drücken Sie Ihre Verbindungs Zeichenfolge, und drücken Sie auf der Tastatur die Tastenkombination **STRG + X** , um die Datei zu speichern.</span><span class="sxs-lookup"><span data-stu-id="7d32d-287">With your Connection String in place, on your keyboard, press the **Ctrl-X** keys to save the file.</span></span> <span data-ttu-id="7d32d-288">Sie werden zur Bestätigung aufgefordert, indem Sie **Y**eingeben. Drücken Sie dann die **Eingabe** Taste, um dies zu bestätigen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-288">It will ask you to confirm by typing **Y**. Then, press the **Enter** key, to confirm.</span></span> <span data-ttu-id="7d32d-289">Sie kehren zum regulären *Terminal*zurück.</span><span class="sxs-lookup"><span data-stu-id="7d32d-289">You will go back to the regular *Terminal*.</span></span> 

8. <span data-ttu-id="7d32d-290">Nachdem diese Befehle erfolgreich ausgeführt wurden, haben Sie die **IOT Edge Runtime**installiert.</span><span class="sxs-lookup"><span data-stu-id="7d32d-290">Once these commands have all run successfully, you will have installed the **IoT Edge Runtime**.</span></span> <span data-ttu-id="7d32d-291">Nachdem die Laufzeit initialisiert wurde, wird Sie jedes Mal, wenn das Gerät eingeschaltet ist, auf dem neuesten Stand, und es wird auf die Bereitstellung der Module aus dem **IOT Hub-Dienst**gewartet.</span><span class="sxs-lookup"><span data-stu-id="7d32d-291">Once initialized, the runtime will start on its own every time the device is powered up, and will sit in the background, waiting for modules to be deployed from the **IoT Hub Service**.</span></span>

9.  <span data-ttu-id="7d32d-292">Führen Sie die folgende Befehlszeile aus, um die *IOT Edge Runtime*zu initialisieren:</span><span class="sxs-lookup"><span data-stu-id="7d32d-292">Run the following command line to initialize the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="7d32d-293">Wenn Sie Änderungen an der YAML-Datei oder an der oben beschriebenen Einrichtung vornehmen, müssen Sie die oben angegebene Neustart Zeile im *Terminal*erneut ausführen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-293">If you make changes to your .yaml file, or the above setup, you will need to run the above restart line again, within *Terminal*.</span></span>

10. <span data-ttu-id="7d32d-294">Überprüfen Sie den Lauf Zeit Status der *IOT Edge* , indem Sie die folgende Befehlszeile ausführen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-294">Check the *IoT Edge Runtime* status by running the following command line.</span></span> <span data-ttu-id="7d32d-295">Die Laufzeit sollte mit dem Status " **aktiv" (wird ausgeführt)** in grünem Text angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-295">The runtime should appear with the status **active (running)** in green text.</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

11. <span data-ttu-id="7d32d-296">Drücken Sie die Tastenkombination **STRG + C** , um die Statusseite zu beenden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-296">Press the **Ctrl-C** keys, to exit the status page.</span></span> <span data-ttu-id="7d32d-297">Durch Eingabe des folgenden Befehls können Sie überprüfen, ob die *IOT Edge Runtime* die Container ordnungsgemäß durchläuft:</span><span class="sxs-lookup"><span data-stu-id="7d32d-297">You can verify that the *IoT Edge Runtime* is pulling the containers correctly by typing the following command:</span></span>

    ```bash
        sudo docker ps
    ```

12. <span data-ttu-id="7d32d-298">Eine Liste mit zwei (2) Containern sollte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-298">A list with two (2) containers should appear.</span></span> <span data-ttu-id="7d32d-299">Dies sind die Standardmodule, die automatisch vom IOT Hub-Dienst (edgeagent und edgehub) erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-299">These are the default modules that are automatically created by the IoT Hub Service (edgeAgent and edgeHub).</span></span> <span data-ttu-id="7d32d-300">Nachdem Sie Ihre eigenen Module erstellt und bereitgestellt haben, werden Sie in dieser Liste unterhalb der Standardwerte angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-300">Once you create and deploy your own modules, they will appear in this list, underneath the default ones.</span></span>

## <a name="chapter-6---install-the-extensions"></a><span data-ttu-id="7d32d-301">Kapitel 6: Installieren der Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="7d32d-301">Chapter 6 - Install the extensions</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7d32d-302">Die nächsten Kapitel (6-9) müssen auf Ihrem Windows 10-Computer ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-302">The next few Chapters (6-9) are to be performed on your Windows 10 machine.</span></span>

1. <span data-ttu-id="7d32d-303">Öffnen Sie **vs Code**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-303">Open **VS Code**.</span></span>

2. <span data-ttu-id="7d32d-304">Klicken Sie in der linken Leiste vs Code auf die Schaltfläche **Erweiterungen** (Quadrat), um den Bereich **Erweiterungen**zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-304">Click on the **Extensions** (square) button on the left bar of VS Code, to open the **Extensions panel**.</span></span>

3. <span data-ttu-id="7d32d-305">Suchen Sie nach den folgenden Erweiterungen (wie in der Abbildung unten gezeigt), und installieren Sie Sie:</span><span class="sxs-lookup"><span data-stu-id="7d32d-305">Search for, and install, the following extensions (as shown in the image below):</span></span>

    1. <span data-ttu-id="7d32d-306">Azure IoT Edge</span><span class="sxs-lookup"><span data-stu-id="7d32d-306">Azure IoT Edge</span></span>
    2. <span data-ttu-id="7d32d-307">Azure IOT-Toolkit</span><span class="sxs-lookup"><span data-stu-id="7d32d-307">Azure IoT Toolkit</span></span>
    3. <span data-ttu-id="7d32d-308">Docker</span><span class="sxs-lookup"><span data-stu-id="7d32d-308">Docker</span></span>   

    ![Erstellen des Containers](images/AzureLabs-Lab313-24.png)

4. <span data-ttu-id="7d32d-310">Nachdem Sie die Erweiterungen installiert haben, schließen Sie vs Code, und öffnen Sie es erneut.</span><span class="sxs-lookup"><span data-stu-id="7d32d-310">Once the extensions are installed, close and re-open VS Code.</span></span>

5. <span data-ttu-id="7d32d-311">Wenn vs Code noch einmal geöffnet ist, navigieren Sie zu **Anzeige** > **integrierter Terminal**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-311">With VS Code open once more, navigate to **View** > **Integrated terminal**.</span></span>

6. <span data-ttu-id="7d32d-312">Sie installieren nun **cookiecutter**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-312">You will now install **Cookiecutter**.</span></span> <span data-ttu-id="7d32d-313">Führen Sie im Terminal den folgenden bash-Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="7d32d-313">In the terminal run the following bash command:</span></span>

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! Hinweis]<span data-ttu-id="7d32d-314">, wenn Sie Probleme mit diesem Befehl haben:</span><span class="sxs-lookup"><span data-stu-id="7d32d-314"> If you have trouble with this command:</span></span> 
    >1. <span data-ttu-id="7d32d-315">Starten Sie vs Code und/oder den Computer neu.</span><span class="sxs-lookup"><span data-stu-id="7d32d-315">Restart VS Code, and/ or your computer.</span></span>
    >2. <span data-ttu-id="7d32d-316">Möglicherweise ist es erforderlich, das **vs Code Terminal** auf das zu ändern, das Sie zum Installieren von Python verwendet haben, d. h. **PowerShell** (insbesondere für den Fall, dass die python-Umgebung bereits auf Ihrem Computer installiert wurde).</span><span class="sxs-lookup"><span data-stu-id="7d32d-316">It might be necessary to switch the **VS Code Terminal** to the one you have been using to install Python, i.e. **Powershell** (especially in case the Python environment was already installed on your machine).</span></span> <span data-ttu-id="7d32d-317">Wenn das Terminal geöffnet ist, finden Sie das Dropdown Menü auf der rechten Seite des Terminals.</span><span class="sxs-lookup"><span data-stu-id="7d32d-317">With the Terminal open, you will find the drop down menu on the right side of the Terminal.</span></span>
     <span data-ttu-id="7d32d-318">![Erstellen des Containers](images/AzureLabs-Lab313-24b.png)</span><span class="sxs-lookup"><span data-stu-id="7d32d-318">![Create your container](images/AzureLabs-Lab313-24b.png)</span></span> 
    >3. <span data-ttu-id="7d32d-319">Stellen Sie sicher, dass der **python** -Installationspfad als **Umgebungs Variable** auf dem Computer hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="7d32d-319">Make sure the **Python** installation path is added as **Environment Variable** on your machine.</span></span> <span data-ttu-id="7d32d-320">Cookiecutter sollte Teil desselben Standort Pfads sein.</span><span class="sxs-lookup"><span data-stu-id="7d32d-320">Cookiecutter should be part of the same location path.</span></span> <span data-ttu-id="7d32d-321">[Weitere Informationen zu Umgebungsvariablen](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx)finden Sie unter diesem Link.</span><span class="sxs-lookup"><span data-stu-id="7d32d-321">Please follow this [link for more information on Environment Variables](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx),</span></span> 

7. <span data-ttu-id="7d32d-322">Nachdem die Installation von **cookiecutter** abgeschlossen ist, sollten Sie den Computer neu starten, damit **cookiecutter** in der Umgebung Ihres Systems als Befehl erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="7d32d-322">Once **Cookiecutter** has finished installing, you should restart your machine, so that **Cookiecutter** is recognized as a command, within your System's environment.</span></span>

## <a name="chapter-7---create-your-container-solution"></a><span data-ttu-id="7d32d-323">Kapitel 7: Erstellen der Containerlösung</span><span class="sxs-lookup"><span data-stu-id="7d32d-323">Chapter 7 - Create your container solution</span></span>

<span data-ttu-id="7d32d-324">An diesem Punkt müssen Sie den Container mit dem-Modul erstellen, damit er in die *Container Registry*übermittelt werden kann.</span><span class="sxs-lookup"><span data-stu-id="7d32d-324">At this point, you need to create the container, with the module, to be pushed into the *Container Registry*.</span></span> <span data-ttu-id="7d32d-325">Nachdem Sie den Container per Pushvorgang übermittelt haben, verwenden Sie den *IOT Hub Edge* -Dienst, um ihn auf Ihrem Gerät bereitzustellen, auf dem die *IOT Edge Laufzeit*ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="7d32d-325">Once you have pushed your container, you will use the *IoT Hub Edge* Service to deploy it to your device, which is running the *IoT Edge runtime*.</span></span>

1. <span data-ttu-id="7d32d-326">Klicken Sie in vs Code auf**Befehls Palette** **anzeigen** > .</span><span class="sxs-lookup"><span data-stu-id="7d32d-326">From VS Code, click **View** > **Command palette**.</span></span>

2. <span data-ttu-id="7d32d-327">Suchen und führen **Sie in der Palette Azure IOT Edge aus: Neue IOT Edge-** Lösung.</span><span class="sxs-lookup"><span data-stu-id="7d32d-327">In the palette, search and run **Azure IoT Edge: New Iot Edge Solution**.</span></span>

3. <span data-ttu-id="7d32d-328">Navigieren Sie zu einem Speicherort, an dem Sie die Projekt Mappe erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="7d32d-328">Browse into a location where you want to create your solution.</span></span> <span data-ttu-id="7d32d-329">Drücken **Sie die Eingabe** Taste, um den Speicherort zu akzeptieren.</span><span class="sxs-lookup"><span data-stu-id="7d32d-329">Press the **Enter** key, to accept the location.</span></span>

4. <span data-ttu-id="7d32d-330">Nennen Sie die Projekt Mappe.</span><span class="sxs-lookup"><span data-stu-id="7d32d-330">Give a name to your solution.</span></span> <span data-ttu-id="7d32d-331">Drücken **Sie die Eingabe** Taste, um den angegebenen Namen zu bestätigen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-331">Press the **Enter** key, to confirm your provided name.</span></span>

5. <span data-ttu-id="7d32d-332">Nun werden Sie aufgefordert, das Vorlagen Framework für Ihre Lösung auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-332">Now you will be prompted to choose the template framework for your solution.</span></span> <span data-ttu-id="7d32d-333">Klicken Sie auf **Python-Modul**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-333">Click **Python Module**.</span></span> <span data-ttu-id="7d32d-334">Drücken **Sie die Eingabe** Taste, um diese Auswahl zu bestätigen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-334">Press the **Enter** key, to confirm this choice.</span></span>

6. <span data-ttu-id="7d32d-335">Benennen Sie Ihr Modul.</span><span class="sxs-lookup"><span data-stu-id="7d32d-335">Give a name to your module.</span></span> <span data-ttu-id="7d32d-336">Drücken **Sie die Eingabe** Taste, um den Namen des Moduls zu bestätigen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-336">Press the **Enter** key, to confirm the name of your module.</span></span> <span data-ttu-id="7d32d-337">Stellen Sie sicher, dass Sie einen Hinweis (mit Ihrem Editor) des Modulnamens verwenden, da er später verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="7d32d-337">Make sure to take a note (with your Notepad) of the module name, as it is used later.</span></span>

7. <span data-ttu-id="7d32d-338">Sie werden feststellen, dass in der Palette eine vorgefertigte *docker-imagerepository* -Adresse angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="7d32d-338">You will notice a pre-built *Docker Image Repository* address will appear on the palette.</span></span> <span data-ttu-id="7d32d-339">Dies sieht wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="7d32d-339">It will look like:</span></span>

    <span data-ttu-id="7d32d-340">**localhost: 5000/-der Name Ihres Moduls**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-340">**localhost:5000/-THE NAME OF YOUR MODULE-**.</span></span> 

8. <span data-ttu-id="7d32d-341">Löschen Sie **localhost: 5000**, und fügen Sie dort die *Container Registry* **Anmelde Server** Adresse ein, die Sie beim Erstellen des **Container Registry Diensts** notiert haben ([in Schritt 8 von Kapitel 2](#chapter-2---the-container-registry-service)).</span><span class="sxs-lookup"><span data-stu-id="7d32d-341">Delete **localhost:5000**, and in its place insert the *Container Registry* **Login Server** address, which you noted when creating the **Container Registry Service** ([in step 8, of Chapter 2](#chapter-2---the-container-registry-service)).</span></span> <span data-ttu-id="7d32d-342">Drücken **Sie die Eingabe** Taste, um die Adresse zu bestätigen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-342">Press the **Enter** key, to confirm the address.</span></span>

9. <span data-ttu-id="7d32d-343">An diesem Punkt wird die Projekt Mappe, die die Vorlage für das Python-Modul enthält, erstellt, und die Struktur wird auf der **Registerkarte**"Durchsuchen" der vs Code auf der linken Seite des Bildschirms angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-343">At this point, the solution containing the template for your Python module will be created and its structure will be displayed in the **Explore Tab**, of VS Code, on the left side of the screen.</span></span> <span data-ttu-id="7d32d-344">Wenn die **Registerkarte** "Durchsuchen" nicht geöffnet ist, können Sie Sie öffnen, indem Sie in der Leiste auf der linken Seite auf die oberste Schaltfläche klicken.</span><span class="sxs-lookup"><span data-stu-id="7d32d-344">If the **Explore Tab** is not open, you can open it by clicking the top-most button, in the bar on the left.</span></span>

    ![Erstellen des Containers](images/AzureLabs-Lab313-25.png)

10. <span data-ttu-id="7d32d-346">Der letzte Schritt in diesem Kapitel besteht darin, auf die Datei " **. ATV**" auf der **Registerkarte**"Durchsuchen" zu klicken und Sie zu öffnen und Ihre *Container Registry* **Benutzername** und **Kennwort**hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-346">The last step for this Chapter, is to click and open the **.env file**, from within the **Explore Tab**, and add your *Container Registry* **username** and **password**.</span></span> <span data-ttu-id="7d32d-347">Diese Datei wird von git ignoriert, aber beim Aufbau des Containers werden die Anmelde Informationen für den Zugriff auf den **Container Registry Dienst**von festgelegt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-347">This file is ignored by git, but on building the container, will set the credentials to access the **Container Registry Service**.</span></span>

    ![Erstellen des Containers](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a><span data-ttu-id="7d32d-349">Kapitel 8: Bearbeiten der Containerlösung</span><span class="sxs-lookup"><span data-stu-id="7d32d-349">Chapter 8 - Editing your container solution</span></span>

<span data-ttu-id="7d32d-350">Sie vervollständigen nun die Containerlösung, indem Sie die folgenden Dateien aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="7d32d-350">You will now complete the container solution, by updating the following files:</span></span>

- <span data-ttu-id="7d32d-351">*Main<span></span>. py* Python-Skript.</span><span class="sxs-lookup"><span data-stu-id="7d32d-351">*main<span></span>.py* python script.</span></span>
- <span data-ttu-id="7d32d-352">" *Requirements. txt*".</span><span class="sxs-lookup"><span data-stu-id="7d32d-352">*requirements.txt*.</span></span>
- <span data-ttu-id="7d32d-353">" *Deployment. Template. JSON*".</span><span class="sxs-lookup"><span data-stu-id="7d32d-353">*deployment.template.json*.</span></span>
- <span data-ttu-id="7d32d-354">*Dockerfile. amd64*</span><span class="sxs-lookup"><span data-stu-id="7d32d-354">*Dockerfile.amd64*</span></span>

<span data-ttu-id="7d32d-355">Anschließend erstellen Sie den Ordner *Images* , der vom Python-Skript verwendet wird, um zu überprüfen, ob Bilder mit Ihrem *Custom Vision Modell*abgeglichen werden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-355">You will then create the *images* folder, used by the python script to check for images to match against your *Custom Vision model*.</span></span> <span data-ttu-id="7d32d-356">Schließlich fügen Sie die Datei " *Labels. txt* " hinzu, um das Modell zu lesen, und die Datei " *Model. PB* ", die das Modell ist.</span><span class="sxs-lookup"><span data-stu-id="7d32d-356">Lastly, you will add the *labels.txt* file, to help read your model, and the *model.pb* file, which is your model.</span></span>

1. <span data-ttu-id="7d32d-357">Wenn vs Code geöffnet ist, navigieren Sie zu Ihrem Modul Ordner, und suchen Sie nach dem Skript mit dem Namen **<span></span>Main. py**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-357">With VS Code open, navigate to your module folder, and look for the script called **main<span></span>.py**.</span></span> <span data-ttu-id="7d32d-358">Doppelklicken Sie, um es zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-358">Double-click to open it.</span></span>

2. <span data-ttu-id="7d32d-359">Löschen Sie den Inhalt der Datei, und fügen Sie den folgenden Code ein:</span><span class="sxs-lookup"><span data-stu-id="7d32d-359">Delete the content of the file and insert the following code:</span></span>

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

3.  <span data-ttu-id="7d32d-360">Öffnen Sie die Datei " **Requirements. txt**", und ersetzen Sie deren Inhalt durch Folgendes:</span><span class="sxs-lookup"><span data-stu-id="7d32d-360">Open the file called **requirements.txt**, and substitute its content with the following:</span></span>

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  <span data-ttu-id="7d32d-361">Öffnen Sie die Datei " **Deployment. Template. JSON**", und ersetzen Sie deren Inhalt nach der folgenden Richtlinie:</span><span class="sxs-lookup"><span data-stu-id="7d32d-361">Open the file called **deployment.template.json**, and substitute its content following the below guideline:</span></span>

    1. <span data-ttu-id="7d32d-362">Da Sie über eine eigene, eindeutige JSON-Struktur verfügen, müssen Sie Sie manuell bearbeiten (anstatt ein Beispiel zu kopieren).</span><span class="sxs-lookup"><span data-stu-id="7d32d-362">Because you will have your own, unique, JSON structure, you will need to edit it by hand (rather than copying an example).</span></span> <span data-ttu-id="7d32d-363">Um dies zu erleichtern, verwenden Sie das folgende Bild als Leitfaden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-363">To make this easy, use the below image as a guide.</span></span>
    2. <span data-ttu-id="7d32d-364">Bereiche, die sich von Ihnen unterscheiden, aber **nicht geändert werden sollten, sind gelb hervorgehoben**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-364">Areas which will look different to yours, but which you **should NOT change are highlighted yellow**.</span></span>
    3. <span data-ttu-id="7d32d-365">**Abschnitte, die Sie löschen müssen, sind hervorgehoben.**</span><span class="sxs-lookup"><span data-stu-id="7d32d-365">**Sections which you need to delete, are a highlighted red.**</span></span>
    4. <span data-ttu-id="7d32d-366">Achten Sie darauf, die richtigen Klammern zu löschen, und entfernen Sie auch die Kommas.</span><span class="sxs-lookup"><span data-stu-id="7d32d-366">Be careful to delete the correct brackets, and also remove the commas.</span></span>

        ![Erstellen des Containers](images/AzureLabs-Lab313-27.png)

    5. <span data-ttu-id="7d32d-368">Der abgeschlossene JSON-Code sollte wie in der folgenden Abbildung aussehen (jedoch mit ihren eindeutigen unterschieden: *Benutzername/Kennwort/Modulname/Modul Verweise*):</span><span class="sxs-lookup"><span data-stu-id="7d32d-368">The completed JSON should look like the following image (though, with your unique differences: *username/password/module name/module references*):</span></span>

        ![Erstellen des Containers](images/AzureLabs-Lab313-28.png)

5.  <span data-ttu-id="7d32d-370">Öffnen Sie die Datei **dockerfile. amd64**, und ersetzen Sie den Inhalt durch Folgendes:</span><span class="sxs-lookup"><span data-stu-id="7d32d-370">Open the file called **Dockerfile.amd64**, and substitute its content with the following:</span></span>

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

6.  <span data-ttu-id="7d32d-371">Klicken Sie mit der rechten Maustaste auf den Ordner unterhalb der **Module** (er enthält den Namen, den Sie zuvor angegeben haben. im Beispiel weiter unten wird er als " *Pythonmodule*" bezeichnet), und klicken Sie auf " **neuer Ordner**".</span><span class="sxs-lookup"><span data-stu-id="7d32d-371">Right-click on the folder beneath **modules** (it will have the name you provided previously; in the example further down, it is called *pythonmodule*), and click on **New Folder**.</span></span> <span data-ttu-id="7d32d-372">Nennen Sie den Ordner **Images**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-372">Name the folder **images**.</span></span>

7.  <span data-ttu-id="7d32d-373">Fügen Sie im Ordner einige Bilder hinzu, die Maus oder Tastatur enthalten.</span><span class="sxs-lookup"><span data-stu-id="7d32d-373">Inside the folder, add some images containing mouse or keyboard.</span></span> <span data-ttu-id="7d32d-374">Dabei handelt es sich um die Bilder, die vom tensorflow-Modell analysiert werden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-374">Those will be the images that will be analyzed by the Tensorflow model.</span></span>

    > [!WARNING]
    > <span data-ttu-id="7d32d-375">Wenn Sie ein eigenes Modell verwenden, müssen Sie es ändern, um Ihre eigenen Modelldaten widerzuspiegeln.</span><span class="sxs-lookup"><span data-stu-id="7d32d-375">If you are using your own model, you will need to change this to reflect your own models data.</span></span>

8.  <span data-ttu-id="7d32d-376">Sie müssen nun die Dateien " **Labels. txt** " und **"Model. PB** " aus dem Ordner "Model" abrufen, den Sie zuvor heruntergeladen (oder aus Ihrem eigenen **Custom Vision Service**erstellt haben), in [Kapitel 1](#chapter-1---retrieve-the-custom-vision-model).</span><span class="sxs-lookup"><span data-stu-id="7d32d-376">You will now need to retrieve the **labels.txt** and **model.pb** files from the model folder, which you previous downloaded (or created from your own **Custom Vision Service**), in [Chapter 1](#chapter-1---retrieve-the-custom-vision-model).</span></span> <span data-ttu-id="7d32d-377">Wenn Sie über die Dateien verfügen, platzieren Sie sie zusammen mit den anderen Dateien in der Projekt Mappe.</span><span class="sxs-lookup"><span data-stu-id="7d32d-377">Once you have the files, place them within your solution, alongside the other files.</span></span> <span data-ttu-id="7d32d-378">Das Endergebnis sollte wie in der folgenden Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="7d32d-378">The final result should look like the image below:</span></span>

    ![Erstellen des Containers](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a><span data-ttu-id="7d32d-380">Kapitel 9: Verpacken der Projekt Mappe als Container</span><span class="sxs-lookup"><span data-stu-id="7d32d-380">Chapter 9 - Package the solution as a container</span></span>

1.  <span data-ttu-id="7d32d-381">Sie sind jetzt bereit, Ihre Dateien als Container zu verpacken und per Push an Ihre **Azure Container Registry**zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-381">You are now ready to "package" your files as a container and push it to your **Azure Container Registry**.</span></span> <span data-ttu-id="7d32d-382">Öffnen Sie in vs Code das *integrierte Terminal* (**anzeigen** > **integrierter Terminals** oder **STRG**+ **\`** ), und verwenden Sie die folgende Zeile, um sich bei **docker** anzumelden (ersetzen Sie die Werte des Befehl mit den Anmelde Informationen Ihres **Azure Container Registry (ACR)** ):</span><span class="sxs-lookup"><span data-stu-id="7d32d-382">Within VS Code, open the *Integrated Terminal* (**View** > **Integrated Terminal** or **Ctrl**+**\`**), and use the following line to login to **Docker** (substitute the values of the command with the credentials of your **Azure Container Registry (ACR)**):</span></span>

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. <span data-ttu-id="7d32d-383">Klicken Sie mit der rechten Maustaste auf die Datei **Deployment. Template. JSON**, und klicken Sie auf IOT Edge Projekt Mappe **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-383">Right-click on the file **deployment.template.json**, and click **Build IoT Edge Solution**.</span></span> <span data-ttu-id="7d32d-384">Dieser Buildprozess dauert einige Zeit (abhängig von Ihrem Gerät) und sollte daher darauf warten, gewartet zu werden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-384">This build process takes quite some time (depending on your device), so be prepared to wait.</span></span> <span data-ttu-id="7d32d-385">Nachdem der Buildprozess abgeschlossen ist, wurde eine Datei " **Deployment. JSON** " in einem neuen Ordner mit dem Namen " **config**" erstellt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-385">After the build process finishes, a **deployment.json** file will have been created inside a new folder called **config**.</span></span>

    ![Bereitstellung erstellen](images/AzureLabs-Lab313-30.png)

3. <span data-ttu-id="7d32d-387">Öffnen Sie die **Befehls Palette** erneut, und suchen **Sie nach Azure: Melden Sie**sich an.</span><span class="sxs-lookup"><span data-stu-id="7d32d-387">Open the **Command Palette** again, and search for **Azure: Sign In**.</span></span> <span data-ttu-id="7d32d-388">Befolgen Sie die Anweisungen unter Verwendung der Anmelde Informationen Ihres Azure-Kontos. VS Code wird Ihnen eine Option zum *Kopieren und öffnen*zur Verfügung gestellt, die den Geräte Code kopiert, den Sie in Kürze benötigen, und den Standard Webbrowser öffnen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-388">Follow the prompts using your Azure Account credentials; VS Code will provide you with an option to *Copy and Open*, which will copy the device code you will soon need, and open your default web browser.</span></span> <span data-ttu-id="7d32d-389">Wenn Sie gefragt werden, fügen Sie den Geräte Code ein, um den Computer zu authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="7d32d-389">When asked, paste the device code, to authenticate your machine.</span></span>

    ![Kopieren und öffnen](images/AzureLabs-Lab313-31.png)

4. <span data-ttu-id="7d32d-391">Nachdem Sie sich angemeldet haben, werden Sie am unteren Rand des Bereichs " *erkunden* " einen neuen Abschnitt mit dem Namen " **Azure IOT Hub Geräte**" bemerken.</span><span class="sxs-lookup"><span data-stu-id="7d32d-391">Once signed in you will notice, on the bottom side of the *Explore* panel, a new section called **Azure IoT Hub Devices**.</span></span> <span data-ttu-id="7d32d-392">Klicken Sie auf diesen Abschnitt, um ihn zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="7d32d-392">Click this section to expand it.</span></span>

    ![Edge-Gerät](images/AzureLabs-Lab313-32.png)

5. <span data-ttu-id="7d32d-394">Wenn Ihr Gerät hier nicht angezeigt wird, klicken Sie mit der rechten Maustaste auf *Azure IOT Hub Geräte*, und klicken Sie dann auf **IOT Hub Verbindungs Zeichenfolge festlegen**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-394">If your device is not here, you will need to right-click *Azure IoT Hub Devices*, and then click **Set IoT Hub Connection String**.</span></span> <span data-ttu-id="7d32d-395">Dann sehen Sie, dass Sie in der **Befehls Palette** (oben in vs Code) aufgefordert werden, die *Verbindungs Zeichenfolge*einzugeben.</span><span class="sxs-lookup"><span data-stu-id="7d32d-395">You will then see that the **Command Palette** (at the top of VS Code), will prompt you to input your *Connection String*.</span></span> <span data-ttu-id="7d32d-396">Dies ist die *Verbindungs Zeichenfolge* , die Sie am Ende von [Kapitel 3](#chapter-3---the-iot-hub-service)notiert haben.</span><span class="sxs-lookup"><span data-stu-id="7d32d-396">This is the *Connection String* you noted down at the end of [Chapter 3](#chapter-3---the-iot-hub-service).</span></span> <span data-ttu-id="7d32d-397">Drücken Sie die **Eingabe** Taste, nachdem Sie die Zeichenfolge in kopiert haben.</span><span class="sxs-lookup"><span data-stu-id="7d32d-397">Press the **Enter** key, once you have copied the string in.</span></span>    

6. <span data-ttu-id="7d32d-398">Ihr Gerät sollte geladen werden und angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-398">Your device should load, and appear.</span></span> <span data-ttu-id="7d32d-399">Klicken Sie mit der rechten Maustaste auf den Gerätenamen, und klicken Sie dann auf **Bereitstellung für einzelnes Gerät erstellen**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-399">Right-click on the device name, and then click, **Create Deployment for Single Device**.</span></span>

    ![Bereitstellung erstellen](images/AzureLabs-Lab313-33b.png)

7. <span data-ttu-id="7d32d-401">Sie erhalten eine *Datei-Explorer* -Eingabeaufforderung, in der Sie zum Ordner " **config** " navigieren und dann die Datei " **Deployment. JSON** " auswählen können.</span><span class="sxs-lookup"><span data-stu-id="7d32d-401">You will get a *File Explorer* prompt, where you can navigate to the **config** folder, and then select the **deployment.json** file.</span></span> <span data-ttu-id="7d32d-402">Wenn diese Datei ausgewählt ist, klicken Sie auf die Schaltfläche **Edge-Bereitstellungs Manifest auswählen** .</span><span class="sxs-lookup"><span data-stu-id="7d32d-402">With that file selected, click the **Select Edge Deployment Manifest** button.</span></span>

    ![Bereitstellung erstellen](images/AzureLabs-Lab313-34.png)

8. <span data-ttu-id="7d32d-404">An diesem Punkt haben Sie Ihren **IOT Hub Dienst** mit dem Manifest bereitgestellt, um den Container, als Modul, von Ihrer **Azure Container Registry**bereitzustellen und effektiv auf Ihrem Gerät bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-404">At this point you have provided your **IoT Hub Service** with the manifest for it to deploy your container, as a module, from your **Azure Container Registry**, effectively deploying it to your device.</span></span>

9. <span data-ttu-id="7d32d-405">Um die Nachrichten anzuzeigen, die vom Gerät an den IOT Hub gesendet werden, klicken Sie mit der rechten Maustaste erneut auf den Gerätenamen im Bereich **Azure IOT Hub Geräte** im Bereich **Explorer** , und klicken Sie auf **Überwachung D2C Meldung starten**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-405">To view the messages sent from your device to the IoT Hub, right-click again on your device name in the **Azure IoT Hub Devices** section, in the **Explorer** panel, and click on **Start Monitoring D2C Message**.</span></span> <span data-ttu-id="7d32d-406">Die von Ihrem Gerät gesendeten Nachrichten sollten im vs-Terminal angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-406">The messages sent from your device should appear in the VS Terminal.</span></span> <span data-ttu-id="7d32d-407">Seien Sie geduldig, da dies einige Zeit in Anspruch nehmen kann.</span><span class="sxs-lookup"><span data-stu-id="7d32d-407">Be patient, as this may take some time.</span></span> <span data-ttu-id="7d32d-408">Weitere Informationen zum Debuggen und zum Überprüfen, ob die Bereitstellung erfolgreich war</span><span class="sxs-lookup"><span data-stu-id="7d32d-408">See the next Chapter for debugging, and checking if deployment was successful.</span></span>

<span data-ttu-id="7d32d-409">Dieses Modul durchläuft nun zwischen den Bildern im Ordner " **Images** " und analysiert sie mit jeder Iterationen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-409">This module will now iterate between the images in the **images** folder and analyze them, with each iteration.</span></span> <span data-ttu-id="7d32d-410">Dies ist offensichtlich nur ein Beispiel dafür, wie Sie das grundlegende Machine Learning-Modell für eine IOT Edge Geräte Umgebung einsetzen können.</span><span class="sxs-lookup"><span data-stu-id="7d32d-410">This is obviously just a demonstration of how to get the basic machine learning model to work in an IoT Edge device environment.</span></span> 

<span data-ttu-id="7d32d-411">Um die Funktionalität dieses Beispiels zu erweitern, können Sie auf verschiedene Weise fortfahren.</span><span class="sxs-lookup"><span data-stu-id="7d32d-411">To expand the functionality of this example, you could proceed in several ways.</span></span> <span data-ttu-id="7d32d-412">Eine Möglichkeit besteht darin, Code in den Container einzubeziehen, der Fotos von einer mit dem Gerät verbundenen Webcam erfasst und die Bilder im Ordner Images speichert.</span><span class="sxs-lookup"><span data-stu-id="7d32d-412">One way could be including some code in the container, that captures photos from a webcam that is connected to the device, and saves the images in the images folder.</span></span> 

<span data-ttu-id="7d32d-413">Eine andere Möglichkeit besteht darin, die Images vom IOT-Gerät in den Container zu kopieren.</span><span class="sxs-lookup"><span data-stu-id="7d32d-413">Another way could be copying the images from the IoT device into the container.</span></span> <span data-ttu-id="7d32d-414">Eine praktische Möglichkeit besteht darin, den folgenden Befehl im IOT-Geräte Terminal auszuführen (möglicherweise könnte eine kleine APP den Auftrag ausführen, wenn Sie den Prozess automatisieren möchten).</span><span class="sxs-lookup"><span data-stu-id="7d32d-414">A practical way to do that is to run the following command in the IoT device Terminal (perhaps a small app could do the job, if you wished to automate the process).</span></span> <span data-ttu-id="7d32d-415">Sie können diesen Befehl testen, indem Sie ihn manuell aus dem Ordner Speicherort ausführen, in dem die Dateien gespeichert sind:</span><span class="sxs-lookup"><span data-stu-id="7d32d-415">You can test this command by running it manually from the folder location where your files are stored:</span></span>

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a><span data-ttu-id="7d32d-416">Kapitel 10: Debuggen der IOT Edge Laufzeit</span><span class="sxs-lookup"><span data-stu-id="7d32d-416">Chapter 10 - Debugging the IoT Edge Runtime</span></span>

<span data-ttu-id="7d32d-417">Im folgenden finden Sie eine Liste mit Befehlszeilen und Tipps, die Sie beim Überwachen und Debuggen der Messaging Aktivität der *IOT Edge Runtime*von Ihrem **Ubuntu-Gerät**aus unterstützen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-417">The following are a list of command lines, and tips, to help you monitor and debug the messaging activity of the *IoT Edge Runtime*, from your **Ubuntu device**.</span></span> 

- <span data-ttu-id="7d32d-418">Überprüfen Sie den Lauf Zeit Status der *IOT Edge* , indem Sie die folgende Befehlszeile ausführen:</span><span class="sxs-lookup"><span data-stu-id="7d32d-418">Check the *IoT Edge Runtime* status by running the following command line:</span></span>

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > <span data-ttu-id="7d32d-419">Drücken Sie **STRG + C**, um die Anzeige des Status abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-419">Remember to press **Ctrl + C**, to finish viewing the status.</span></span>

- <span data-ttu-id="7d32d-420">Listet die Container auf, die zurzeit bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-420">List the containers that are currently deployed.</span></span> <span data-ttu-id="7d32d-421">Wenn der *IOT Hub-Dienst* die Container erfolgreich bereitgestellt hat, werden diese angezeigt, indem Sie die folgende Befehlszeile ausführen:</span><span class="sxs-lookup"><span data-stu-id="7d32d-421">If the *IoT Hub Service* has deployed the containers successfully, they will be displayed by running the following command line:</span></span>

    ```bash
        sudo iotedge list
    ```

    <span data-ttu-id="7d32d-422">oder</span><span class="sxs-lookup"><span data-stu-id="7d32d-422">Or</span></span>

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > <span data-ttu-id="7d32d-423">Das obige ist eine gute Möglichkeit, um zu überprüfen, ob das Modul erfolgreich bereitgestellt wurde, da es in der Liste angezeigt wird. Andernfalls werden **nur** *edgehub* und *edgeagent*angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-423">The above is a good way to check whether your module has been deployed successfully, as it will appear in the list; you will otherwise **only** see the *edgeHub* and *edgeAgent*.</span></span>

- <span data-ttu-id="7d32d-424">Um die Code Protokolle eines Containers anzuzeigen, führen Sie die folgende Befehlszeile aus:</span><span class="sxs-lookup"><span data-stu-id="7d32d-424">To display the code logs of a container, run the following command line:</span></span>

    ```bash
        journalctl -u iotedge
    ```

<span data-ttu-id="7d32d-425">**Nützliche Befehle zum Verwalten der IOT Edge Laufzeit:**</span><span class="sxs-lookup"><span data-stu-id="7d32d-425">**Useful commands to manage the IoT Edge Runtime:**</span></span>

-  <span data-ttu-id="7d32d-426">So löschen Sie alle Container auf dem Host:</span><span class="sxs-lookup"><span data-stu-id="7d32d-426">To delete all containers in the host:</span></span>

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  <span data-ttu-id="7d32d-427">So verhindern Sie die *IOT Edge Laufzeit*:</span><span class="sxs-lookup"><span data-stu-id="7d32d-427">To stop the *IoT Edge Runtime*:</span></span>

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a><span data-ttu-id="7d32d-428">Kapitel 11: Erstellen eines Tabellen Dienstanbieter</span><span class="sxs-lookup"><span data-stu-id="7d32d-428">Chapter 11 - Create Table Service</span></span> 

<span data-ttu-id="7d32d-429">Navigieren Sie zurück zu Ihrem Azure-Portal, in dem Sie einen Azure Tables-Dienst erstellen, indem Sie eine Speicher Ressource erstellen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-429">Navigate back to your Azure Portal, where you will create an Azure Tables Service, by creating a Storage resource.</span></span>

1. <span data-ttu-id="7d32d-430">Wenn Sie noch nicht angemeldet sind, melden Sie sich beim [Azure-Portal](https://portal.azure.com)an.</span><span class="sxs-lookup"><span data-stu-id="7d32d-430">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="7d32d-431">Nachdem Sie sich angemeldet haben, klicken Sie in der oberen linken Ecke auf **Ressource erstellen**, suchen Sie nach **Speicherkonto**, und drücken **Sie die Eingabe** Taste, um die Suche zu starten.</span><span class="sxs-lookup"><span data-stu-id="7d32d-431">Once logged in, click on **Create a resource**, in the top left corner, and search for **Storage account**, and press the **Enter** key, to start the search.</span></span>

3. <span data-ttu-id="7d32d-432">Wenn die Datei angezeigt wird, klicken Sie auf **Speicherkonto-BLOB, Datei, Tabelle, Warteschlange** aus der Liste.</span><span class="sxs-lookup"><span data-stu-id="7d32d-432">Once it has appeared, click **Storage account - blob, file, table, queue** from the list.</span></span>

    ![Suchen nach Speicherkonto](images/AzureLabs-Lab313-35.png)

4. <span data-ttu-id="7d32d-434">Auf der neuen Seite wird eine Beschreibung des **Speicherkonto** Dienstanbieter bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-434">The new page will provide a description of the **Storage account** Service.</span></span> <span data-ttu-id="7d32d-435">Klicken Sie unten links in dieser Eingabeaufforderung auf die Schaltfläche **Erstellen** , um eine Instanz dieses Dienstanbieter zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-435">At the bottom left of this prompt, click the **Create** button, to create an instance of this Service.</span></span>

    ![Speicher Instanz erstellen](images/AzureLabs-Lab313-36.png)

5. <span data-ttu-id="7d32d-437">Nachdem Sie auf **Erstellen**geklickt haben, wird ein Panel angezeigt:</span><span class="sxs-lookup"><span data-stu-id="7d32d-437">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="7d32d-438">Fügen Sie den gewünschten **Namen** für diese Dienst Instanz ein (*nur klein*Buchstaben).</span><span class="sxs-lookup"><span data-stu-id="7d32d-438">Insert your desired **Name** for this Service instance (*must be all lowercase*).</span></span>

    2. <span data-ttu-id="7d32d-439">Klicken Sie unter **Bereitstellungs Modell**auf **Ressourcen-Manager**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-439">For **Deployment model**, click **Resource manager**.</span></span>

    3. <span data-ttu-id="7d32d-440">Klicken Sie unter **Kontoart**im Dropdown Menü auf **Speicher (universell v1)** .</span><span class="sxs-lookup"><span data-stu-id="7d32d-440">For **Account kind**, using the dropdown menu, click **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="7d32d-441">Klicken Sie auf einen geeigneten **Speicherort**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-441">Click an appropriate **Location**.</span></span>
    
    5. <span data-ttu-id="7d32d-442">Klicken Sie im Dropdown Menü **Replikation** auf **georedundanten Speicher mit Lesezugriff (RA-GRS)** .</span><span class="sxs-lookup"><span data-stu-id="7d32d-442">For the **Replication** dropdown menu, click **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6. <span data-ttu-id="7d32d-443">Klicken Sie für die **Leistung**auf **Standard**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-443">For **Performance**, click **Standard**.</span></span>

    7. <span data-ttu-id="7d32d-444">Klicken Sie im Abschnitt **Secure Transfer required** auf **deaktiviert**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-444">Within the **Secure transfer required** section, click **Disabled**.</span></span>

    8. <span data-ttu-id="7d32d-445">Klicken Sie im Dropdown Menü **Abonnement** auf ein entsprechendes Abonnement.</span><span class="sxs-lookup"><span data-stu-id="7d32d-445">From the **Subscription** dropdown menu, click an appropriate subscription.</span></span>

    9. <span data-ttu-id="7d32d-446">Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** .</span><span class="sxs-lookup"><span data-stu-id="7d32d-446">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="7d32d-447">Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-447">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="7d32d-448">Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Kursen) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.</span><span class="sxs-lookup"><span data-stu-id="7d32d-448">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="7d32d-449">Weitere Informationen zu Azure-Ressourcengruppen finden Sie unter diesem [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="7d32d-449">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="7d32d-450">Lassen Sie **virtuelle Netzwerke** **deaktiviert**, wenn dies eine Option für Sie ist.</span><span class="sxs-lookup"><span data-stu-id="7d32d-450">Leave **Virtual networks** as **Disabled**, if this is an option for you.</span></span>

    11. <span data-ttu-id="7d32d-451">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-451">Click **Create**.</span></span>

        ![Speicher Details ausfüllen](images/AzureLabs-Lab313-37.png)

6. <span data-ttu-id="7d32d-453">Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-453">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

7. <span data-ttu-id="7d32d-454">Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-454">A notification will appear in the Portal once the Service instance is created.</span></span> <span data-ttu-id="7d32d-455">Klicken Sie auf die Benachrichtigungen, um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-455">Click on the notifications to explore your new Service instance.</span></span>

    ![neue Speicher Benachrichtigung](images/AzureLabs-Lab313-38.png)

8. <span data-ttu-id="7d32d-457">Klicken Sie in der Benachrichtigung auf die Schaltfläche **zum Ressourcen** Wechsel, und Sie gelangen zur Übersichtsseite der neuen Speicherdienst Instanz.</span><span class="sxs-lookup"><span data-stu-id="7d32d-457">Click the **Go to resource** button in the notification, and you will be taken to your new Storage Service instance overview page.</span></span>

    ![Gehe zu Ressource](images/AzureLabs-Lab313-39.png)

9. <span data-ttu-id="7d32d-459">Klicken Sie auf der Seite Übersicht auf die Rechte Seite, und klicken Sie auf **Tabellen**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-459">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![Spielern](images/AzureLabs-Lab313-40.png)

10. <span data-ttu-id="7d32d-461">Der Bereich auf der rechten Seite ändert sich, um die **Tabellen Dienst** Informationen anzuzeigen, in denen Sie eine neue Tabelle hinzufügen müssen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-461">The panel on the right will change to show the **Table Service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="7d32d-462">Klicken Sie hierzu auf die Schaltfläche **+ Table** in der linken oberen Ecke.</span><span class="sxs-lookup"><span data-stu-id="7d32d-462">Do this by clicking the **+ Table** button to the top-left corner.</span></span>

    ![Öffnen von Tabellen](images/AzureLabs-Lab313-41.png)

11. <span data-ttu-id="7d32d-464">Es wird eine neue Seite angezeigt, auf der Sie einen **Tabellennamen**eingeben müssen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-464">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="7d32d-465">Dies ist der Name, den Sie in späteren Kapiteln (Erstellen von Funktionen-APP und Power BI) verwenden, um auf die Daten in Ihrer Anwendung zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-465">This is the name you will use to refer to the data in your application in later Chapters (creating Function App, and Power BI).</span></span> <span data-ttu-id="7d32d-466">Fügen Sie **iotmessages** als Name ein. (Sie können sich auch selbst merken, wenn Sie es später in diesem Dokument verwenden), und klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-466">Insert **IoTMessages** as the name (you can choose your own, just remember it when used later in this document) and click **OK**.</span></span> 

12. <span data-ttu-id="7d32d-467">Nachdem die neue Tabelle erstellt wurde, können Sie Sie auf der Seite **Tabellen Dienst** (unten) sehen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-467">Once the new table has been created, you will be able to see it within the **Table Service** page (at the bottom).</span></span>

    ![neue Tabelle erstellt](images/AzureLabs-Lab313-42.png)  

13. <span data-ttu-id="7d32d-469">Klicken Sie nun auf **Zugriffsschlüssel** , und nehmen Sie eine Kopie des **Speicherkonto namens** und- **Schlüssels** auf (mithilfe Ihres Notepad). Sie verwenden diese Werte später in diesem Kurs, wenn Sie die **Azure-Funktionen-App**erstellen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-469">Now click on **Access keys** and take a copy of the **Storage account name** and **Key** (using your Notepad), you will use these values later in this course, when creating the **Azure Function App**.</span></span>

    ![neue Tabelle erstellt](images/AzureLabs-Lab313-43.png) 

14. <span data-ttu-id="7d32d-471">Scrollen Sie im Bereich auf der linken Seite zum Abschnitt *Tabellen Dienst* , und klicken Sie auf **Tabellen** (oder Tabellen in neueren Portalen **Durchsuchen**), und erstellen Sie eine Kopie der **Tabellen-URL** (mit Ihrem Editor).</span><span class="sxs-lookup"><span data-stu-id="7d32d-471">Using the panel on the left again, scroll to the *Table Service* section, and click **Tables** (or **Browse Tables**, in newer Portals) and take a copy of the **Table URL** (using your Notepad).</span></span> <span data-ttu-id="7d32d-472">Sie verwenden diesen Wert später in diesem Kurs, wenn Sie Ihre Tabelle mit Ihrer **Power BI** Anwendung verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-472">You will use this value later in this course, when linking your table to your **Power BI** application.</span></span>

    ![neue Tabelle erstellt](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a><span data-ttu-id="7d32d-474">Kapitel 12: Abschließen der Azure-Tabelle</span><span class="sxs-lookup"><span data-stu-id="7d32d-474">Chapter 12 - Completing the Azure Table</span></span>

<span data-ttu-id="7d32d-475">Nachdem Sie das Speicher **Dienst** -Speicherkonto eingerichtet haben, ist es an der Zeit, Daten hinzuzufügen, die zum Speichern und Abrufen von Informationen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-475">Now that your **Table Service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="7d32d-476">Die Bearbeitung der Tabellen kann über **Visual Studio**erfolgen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-476">The editing of your Tables can be done through **Visual Studio**.</span></span>

1. <span data-ttu-id="7d32d-477">Öffnen Sie **Visual Studio** (**nicht** Visual Studio Code).</span><span class="sxs-lookup"><span data-stu-id="7d32d-477">Open **Visual Studio** (**not** Visual Studio Code).</span></span>

2. <span data-ttu-id="7d32d-478">Klicken Sie im Menü auf**Cloud-Explorer** **anzeigen** > .</span><span class="sxs-lookup"><span data-stu-id="7d32d-478">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![Cloud-Explorer öffnen](images/AzureLabs-Lab313-45.png)

3. <span data-ttu-id="7d32d-480">Der **Cloud-Explorer** wird als angedocktes Element geöffnet (als "Patient", da der Ladevorgang Zeit in Anspruch nehmen kann).</span><span class="sxs-lookup"><span data-stu-id="7d32d-480">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="7d32d-481">Wenn das Abonnement, das Sie zum Erstellen Ihrer *Speicher Konten* verwendet haben, nicht sichtbar ist, stellen Sie Folgendes sicher:</span><span class="sxs-lookup"><span data-stu-id="7d32d-481">If the subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="7d32d-482">Sie sind beim gleichen Konto angemeldet, das Sie für das Azure-Portal verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="7d32d-482">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="7d32d-483">Wählen Sie auf der Seite "Kontoverwaltung" Ihr Abonnement aus (möglicherweise müssen Sie einen Filter aus Ihren Kontoeinstellungen anwenden):</span><span class="sxs-lookup"><span data-stu-id="7d32d-483">Selected your subscription from the Account Management page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![Abonnement suchen](images/AzureLabs-Lab313-46.png)

4. <span data-ttu-id="7d32d-485">Ihre Azure-Clouddienste werden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-485">Your Azure cloud Services will be shown.</span></span> <span data-ttu-id="7d32d-486">Suchen Sie nach **Speicher Konten** , und klicken Sie auf den Pfeil auf der linken Seite, um Ihre Konten zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="7d32d-486">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![Öffnen von Speicher Konten](images/AzureLabs-Lab313-47.png)

5. <span data-ttu-id="7d32d-488">Nach der Erweiterung sollte Ihr neu erstelltes **Speicherkonto** verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="7d32d-488">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="7d32d-489">Klicken Sie auf den Pfeil links neben dem Speicher, und wählen Sie dann nach dem Erweitern der Tabelle **Tabellen** aus, und klicken Sie auf den Pfeil daneben, um die **Tabelle** anzuzeigen, die Sie im letzten Kapitel erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="7d32d-489">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="7d32d-490">Doppelklicken Sie auf die **Tabelle**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-490">Double-click your **Table**.</span></span>

6. <span data-ttu-id="7d32d-491">Ihre Tabelle wird in der Mitte Ihres Visual Studio-Fensters geöffnet.</span><span class="sxs-lookup"><span data-stu-id="7d32d-491">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="7d32d-492">Klicken Sie auf das Symboltabelle **+** mit dem (plus)-Symbol.</span><span class="sxs-lookup"><span data-stu-id="7d32d-492">Click the table icon with the **+** (plus) on it.</span></span>

    ![neue Tabelle hinzufügen](images/AzureLabs-Lab313-48.png)

7. <span data-ttu-id="7d32d-494">Ein Fenster wird angezeigt, in dem Sie aufgefordert werden, *Entitäten hinzuzufügen*.</span><span class="sxs-lookup"><span data-stu-id="7d32d-494">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="7d32d-495">Sie erstellen nur eine Entität, Sie verfügen jedoch über drei Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="7d32d-495">You will create only one entity, though it will have three properties.</span></span> <span data-ttu-id="7d32d-496">Sie werden feststellen, dass *PartitionKey* und *RowKey* bereits bereitgestellt werden, da diese von der Tabelle zum Suchen Ihrer Daten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-496">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![Partitions-und Zeilen Schlüssel](images/AzureLabs-Lab313-49.png)

8. <span data-ttu-id="7d32d-498">Aktualisieren Sie die folgenden Werte:</span><span class="sxs-lookup"><span data-stu-id="7d32d-498">Update the following values:</span></span>

    - <span data-ttu-id="7d32d-499">Name: **PartitionKey**, Wert: **PK_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="7d32d-499">Name: **PartitionKey**, Value: **PK_IoTMessages**</span></span> 

    - <span data-ttu-id="7d32d-500">Name: **RowKey**, Wert: **RK_1_IoTMessages**</span><span class="sxs-lookup"><span data-stu-id="7d32d-500">Name: **RowKey**, Value: **RK_1_IoTMessages**</span></span> 

9. <span data-ttu-id="7d32d-501">Klicken Sie dann auf **Eigenschaft hinzufügen** (unten links im Fenster *Entität hinzufügen* ), und fügen Sie die folgende Eigenschaft hinzu:</span><span class="sxs-lookup"><span data-stu-id="7d32d-501">Then, click **Add property** (to the lower left of the *Add Entity* window) and add the following property:</span></span>

    - <span data-ttu-id="7d32d-502">Bei **messagecontent**wird als *Zeichen*Folge der Wert leer gelassen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-502">**MessageContent**, as a *string*, leave the Value empty.</span></span>

10. <span data-ttu-id="7d32d-503">Die Tabelle sollte der Tabelle in der folgenden Abbildung entsprechen:</span><span class="sxs-lookup"><span data-stu-id="7d32d-503">Your table should match the one in the image below:</span></span>

    ![korrekte Werte hinzufügen](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > <span data-ttu-id="7d32d-505">Der Grund, warum die Entität die Zahl 1 im Zeilen Schlüssel hat, liegt daran, dass Sie möglicherweise weitere Nachrichten hinzufügen möchten, sollten Sie mit diesem Kurs weiter experimentieren.</span><span class="sxs-lookup"><span data-stu-id="7d32d-505">The reason why the entity has the number 1 in the row key, is because you might want to add more messages, should you desire to experiment further with this course.</span></span>

11. <span data-ttu-id="7d32d-506">Klicken Sie anschließend auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-506">Click **OK** when you are finished.</span></span> <span data-ttu-id="7d32d-507">Die Tabelle ist jetzt zur Verwendung bereit.</span><span class="sxs-lookup"><span data-stu-id="7d32d-507">Your table is now ready to be used.</span></span>

## <a name="chapter-13---create-an-azure-function-app"></a><span data-ttu-id="7d32d-508">Kapitel 13: Erstellen eines Azure-Funktionen-App</span><span class="sxs-lookup"><span data-stu-id="7d32d-508">Chapter 13 - Create an Azure Function App</span></span> 

<span data-ttu-id="7d32d-509">Nun ist es an der Zeit, eine *Azure-Funktionen-App*zu erstellen, die vom *IOT Hub-Dienst* aufgerufen wird, um die *IOT Edge* Geräte Nachrichten im **Tabellen** Dienst zu speichern, die Sie im vorherigen Kapitel erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="7d32d-509">It is now time to create an *Azure Function App*, which will be called by the *IoT Hub Service* to store the *IoT Edge* device messages in the **Table** Service, which you created in the previous Chapter.</span></span>

<span data-ttu-id="7d32d-510">Zunächst müssen Sie eine Datei erstellen, die es ihrer Azure-Funktion ermöglicht, die benötigten Bibliotheken zu laden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-510">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="7d32d-511">Öffnen Sie **Editor** (drücken Sie die *Windows-Taste*, und geben Sie *Editor*ein).</span><span class="sxs-lookup"><span data-stu-id="7d32d-511">Open **Notepad** (press the *Windows Key*, and type *notepad*).</span></span>

    ![Editor öffnen](images/AzureLabs-Lab313-51.png)

2.  <span data-ttu-id="7d32d-513">Fügen Sie bei geöffneter Notepad die JSON-Struktur unten ein.</span><span class="sxs-lookup"><span data-stu-id="7d32d-513">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="7d32d-514">Wenn Sie dies abgeschlossen haben, speichern Sie es auf Ihrem Desktop als " **Project. JSON**".</span><span class="sxs-lookup"><span data-stu-id="7d32d-514">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="7d32d-515">Diese Datei definiert die Bibliotheken, die von ihrer Funktion verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-515">This file defines the libraries your function will use.</span></span> <span data-ttu-id="7d32d-516">Wenn Sie nuget verwendet haben, wird es vertraut aussehen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-516">If you have used NuGet, it will look familiar.</span></span>
    
    > [!WARNING]
    > <span data-ttu-id="7d32d-517">Es ist wichtig, dass die Benennung korrekt ist. Stellen Sie sicher, dass die Dateierweiterung **txt nicht** vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="7d32d-517">It is important that the naming is correct; ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="7d32d-518">Weitere Informationen finden Sie weiter unten:</span><span class="sxs-lookup"><span data-stu-id="7d32d-518">See below for reference:</span></span>
    >
    > ![JSON-Speicherung](images/AzureLabs-Lab313-52.png)

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

3.  <span data-ttu-id="7d32d-520">Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.</span><span class="sxs-lookup"><span data-stu-id="7d32d-520">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="7d32d-521">Wenn Sie angemeldet sind, klicken Sie in der oberen linken Ecke auf **Ressource erstellen** , suchen Sie nach **Funktionen-App**, und drücken Sie die **Eingabe** Taste, um zu suchen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-521">Once you are logged in, click on **Create a resource** in the top left corner, and search for **Function App**, and press the **Enter** key, to search.</span></span> <span data-ttu-id="7d32d-522">Klicken Sie in den Ergebnissen auf *Funktionen-App* , um einen neuen Bereich zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-522">Click *Function App* from the results, to open a new panel.</span></span>

    ![nach Funktionen-App suchen](images/AzureLabs-Lab313-53.png)

5.  <span data-ttu-id="7d32d-524">Im neuen Panel wird eine Beschreibung des **Funktionen-App** Dienstanbieter bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-524">The new panel will provide a description of the **Function App** Service.</span></span> <span data-ttu-id="7d32d-525">Klicken Sie unten links in diesem Bereich auf die Schaltfläche **Erstellen** , um eine Verknüpfung mit diesem Dienst zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-525">At the bottom left of this panel, click the **Create** button, to create an association with this Service.</span></span>

    ![Funktionen-app-Instanz](images/AzureLabs-Lab313-54.png)

6.  <span data-ttu-id="7d32d-527">Nachdem Sie auf **Erstellen**geklickt haben, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="7d32d-527">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="7d32d-528">Fügen Sie für **App-Name**den gewünschten Namen für diese Dienst Instanz ein.</span><span class="sxs-lookup"><span data-stu-id="7d32d-528">For **App name**, insert your desired name for this Service instance.</span></span>

    2. <span data-ttu-id="7d32d-529">Wählen Sie ein **Abonnement**aus.</span><span class="sxs-lookup"><span data-stu-id="7d32d-529">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="7d32d-530">Wählen Sie den für Sie geeigneten Tarif aus. Wenn Sie zum ersten Mal einen **Funktionen-App Dienst**erstellen, sollte Ihnen ein Free-Tarif zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-530">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="7d32d-531">Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** .</span><span class="sxs-lookup"><span data-stu-id="7d32d-531">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="7d32d-532">Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-532">A resource group provides a way to monitor, control access, provision, and manage, billing for a collection of Azure assets.</span></span> <span data-ttu-id="7d32d-533">Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Kursen) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.</span><span class="sxs-lookup"><span data-stu-id="7d32d-533">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="7d32d-534">Weitere Informationen zu Azure-Ressourcengruppen finden Sie unter diesem [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="7d32d-534">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="7d32d-535">Klicken Sie für **Betriebssystem**auf Windows, da dies die beabsichtigte Plattform ist.</span><span class="sxs-lookup"><span data-stu-id="7d32d-535">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="7d32d-536">Wählen Sie einen **Hostingplan** aus (in diesem Tutorial wird ein **Verbrauchs Plan**verwendet.)</span><span class="sxs-lookup"><span data-stu-id="7d32d-536">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="7d32d-537">Wählen Sie einen **Standort** aus (Wählen Sie den gleichen Speicherort wie für den Speicher aus, den Sie im vorherigen Schritt erstellt haben).</span><span class="sxs-lookup"><span data-stu-id="7d32d-537">Select a **Location** (choose the same location as the storage you have built in the previous step)</span></span>

    8. <span data-ttu-id="7d32d-538">Im Abschnitt **Speicher** **müssen Sie den Speicherdienst auswählen, den Sie im vorherigen Schritt erstellt**haben.</span><span class="sxs-lookup"><span data-stu-id="7d32d-538">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="7d32d-539">Sie benötigen keine *Application Insights* in dieser APP, sodass Sie Sie nicht mehr **Deaktivieren**können.</span><span class="sxs-lookup"><span data-stu-id="7d32d-539">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="7d32d-540">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-540">Click **Create**.</span></span>

        ![neue Instanz erstellen](images/AzureLabs-Lab313-55.png)

7.  <span data-ttu-id="7d32d-542">Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-542">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="7d32d-543">Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-543">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![neue Benachrichtigung](images/AzureLabs-Lab313-56.png)

9.  <span data-ttu-id="7d32d-545">Nachdem die Bereitstellung erfolgreich abgeschlossen wurde, klicken Sie auf die Benachrichtigung.</span><span class="sxs-lookup"><span data-stu-id="7d32d-545">Click on the notification, once deployment is successful (has finished).</span></span>

10. <span data-ttu-id="7d32d-546">Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-546">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![Gehe zu Ressource](images/AzureLabs-Lab313-57.png)

11. <span data-ttu-id="7d32d-548">Klicken Sie auf der linken Seite des neuen Panels auf das **+** Symbol (Pluszeichen) neben *Functions*, um eine neue Funktion zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-548">In the left side of the new panel, click the **+** (plus) icon next to *Functions*, to create a new function.</span></span>

    ![neue Funktion hinzufügen](images/AzureLabs-Lab313-58.png)

12. <span data-ttu-id="7d32d-550">Im mittleren Bereich wird das Fenster für die **Funktions** Erstellung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-550">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="7d32d-551">Scrollen Sie nach unten, und klicken Sie auf **benutzerdefinierte Funktion**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-551">Scroll down further, and click on **Custom function**.</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-59.png)

13. <span data-ttu-id="7d32d-553">Scrollen Sie auf der nächsten Seite nach unten, bis Sie **IOT Hub (Event Hub)** gefunden haben, und klicken Sie dann darauf.</span><span class="sxs-lookup"><span data-stu-id="7d32d-553">Scroll down the next page, until you find **IoT Hub (Event Hub)**, then click on it.</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-60.png)

14. <span data-ttu-id="7d32d-555">Legen Sie auf dem Blatt **IOT Hub (Event Hub)** die **Sprache** auf **C#** fest, und klicken Sie dann auf **neu**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-555">In the **IoT Hub (Event Hub)** blade, set the **Language** to **C#** and then click on **new**.</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-61.png)

15. <span data-ttu-id="7d32d-557">Stellen Sie im Fenster, das angezeigt wird, sicher, dass **IOT Hub** ausgewählt ist und der Name des *IOT Hub* Felds mit dem Namen des *IOT Hub Dienstanbieter* übereinstimmt, den Sie zuvor erstellt haben ([in Schritt 8 von Kapitel 3](#chapter-3---the-iot-hub-service)).</span><span class="sxs-lookup"><span data-stu-id="7d32d-557">In the window that will appear, make sure that **IoT Hub** is selected and the name of the *IoT Hub* field corresponds with the name of your *IoT Hub Service* that you have created previously ([in step 8, of Chapter 3](#chapter-3---the-iot-hub-service)).</span></span> <span data-ttu-id="7d32d-558">Klicken Sie dann auf die Schaltfläche **auswählen** .</span><span class="sxs-lookup"><span data-stu-id="7d32d-558">Then click the **Select** button.</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-62.png)

16. <span data-ttu-id="7d32d-560">Klicken Sie auf dem Blatt **IOT Hub (Event Hub)** auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-560">Back on the **IoT Hub (Event Hub)** blade, click on **Create**.</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-63.png)

17. <span data-ttu-id="7d32d-562">Sie werden zum Funktions-Editor umgeleitet.</span><span class="sxs-lookup"><span data-stu-id="7d32d-562">You will be redirected to the function editor.</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-64.png)

18. <span data-ttu-id="7d32d-564">Löschen Sie den gesamten Code, und ersetzen Sie ihn durch Folgendes:</span><span class="sxs-lookup"><span data-stu-id="7d32d-564">Delete all the code in it and replace it with the following:</span></span>

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

19. <span data-ttu-id="7d32d-565">Ändern Sie die folgenden Variablen, damit Sie den entsprechenden Werten entsprechen (**Tabellen** -und **Speicher** Werte aus [Schritt 11 und 13 bzw. in Kapitel 11](#chapter-11---create-table-service)), die Sie in Ihrem **Speicherkonto**finden:</span><span class="sxs-lookup"><span data-stu-id="7d32d-565">Change the following variables, so that they correspond to the appropriate values (**Table** and **Storage** values, from [step 11 and 13, respectively, of Chapter 11](#chapter-11---create-table-service)), that you will find in your **Storage Account**:</span></span>

    - <span data-ttu-id="7d32d-566">**TableName**, mit dem Namen der **Tabelle** in Ihrem **Speicherkonto**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-566">**tableName**, with the name of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="7d32d-567">**tableurl**, wobei sich die URL Ihrer **Tabelle** in Ihrem **Speicherkonto**befindet.</span><span class="sxs-lookup"><span data-stu-id="7d32d-567">**tableURL**, with the URL of your **Table** located in your **Storage Account**.</span></span>
    - <span data-ttu-id="7d32d-568">**storageaccountname**, mit dem Namen des Werts, der dem Namen Ihres **Speicherkonto** namens entspricht.</span><span class="sxs-lookup"><span data-stu-id="7d32d-568">**storageAccountName**, with the name of the value corresponding with the name of your **Storage Account** name.</span></span>
    - <span data-ttu-id="7d32d-569">**storageaccountkey**mit dem Schlüssel, den Sie im zuvor erstellten Speicherdienst abgerufen haben.</span><span class="sxs-lookup"><span data-stu-id="7d32d-569">**storageAccountKey**, with the Key you have obtained in the Storage Service you have created previously.</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-65.png)

20. <span data-ttu-id="7d32d-571">Klicken Sie mit dem Code auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-571">With the code in place, click **Save**.</span></span>

21. <span data-ttu-id="7d32d-572">Klicken Sie anschließend auf **\<** der rechten Seite der Seite auf das Symbol (Pfeil).</span><span class="sxs-lookup"><span data-stu-id="7d32d-572">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-66.png)

22. <span data-ttu-id="7d32d-574">Ein Panel wird von rechts nach rechts angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-574">A panel will slide in from the right.</span></span> <span data-ttu-id="7d32d-575">Klicken Sie in diesem Bereich auf **hochladen**, und ein *Datei Browser* wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-575">In that panel, click **Upload**, and a *File Browser* will appear.</span></span>

23. <span data-ttu-id="7d32d-576">Navigieren Sie zu, und klicken Sie auf die Datei **Project. JSON** , die Sie **zuvor im** Editor erstellt haben, und klicken Sie dann auf die Schaltfläche **Öffnen** .</span><span class="sxs-lookup"><span data-stu-id="7d32d-576">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="7d32d-577">Diese Datei definiert die Bibliotheken, die von ihrer Funktion verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-577">This file defines the libraries that your function will use.</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-67.png)

24. <span data-ttu-id="7d32d-579">Wenn die Datei hochgeladen wurde, wird Sie im Panel auf der rechten Seite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-579">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="7d32d-580">Wenn Sie darauf klicken, wird es im **Funktions** -Editor geöffnet.</span><span class="sxs-lookup"><span data-stu-id="7d32d-580">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="7d32d-581">Es muss **genau** wie das nächste Bild aussehen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-581">It must look **exactly** the same as the next image.</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-68.png)

25. <span data-ttu-id="7d32d-583">An diesem Punkt wäre es gut, die Funktion ihrer Funktion zu testen, um die Nachricht in der *Tabelle*zu speichern.</span><span class="sxs-lookup"><span data-stu-id="7d32d-583">At this point it would be good to test the capability of your Function to store the message on your *Table*.</span></span> <span data-ttu-id="7d32d-584">Klicken Sie oben rechts im Fenster auf **Test**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-584">On the top right side of the window, click on **Test**.</span></span>

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-69.png)

26. <span data-ttu-id="7d32d-586">Fügen Sie eine Meldung in den **Anforderungs Text**ein, wie in der obigen Abbildung gezeigt, und klicken Sie auf **Ausführen**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-586">Insert a message on the **Request body**, as shown in the image above, and click on **Run**.</span></span> 

27. <span data-ttu-id="7d32d-587">Die Funktion wird ausgeführt und zeigt den Ergebnis Status an (Sie werden feststellen, dass der grüne **Status 202 akzeptiert**wurde, oberhalb des *Ausgabe* Fensters, was bedeutet, dass es sich um einen erfolgreichen Rückruf handelt):</span><span class="sxs-lookup"><span data-stu-id="7d32d-587">The function will run, displaying the result status (you will notice the green **Status 202 Accepted**, above the *Output* window, which means it was a successful call):</span></span>

    ![Ausgabe Ergebnis](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a><span data-ttu-id="7d32d-589">Kapitel 14: Anzeigen von aktiven Nachrichten</span><span class="sxs-lookup"><span data-stu-id="7d32d-589">Chapter 14 - View active messages</span></span>

<span data-ttu-id="7d32d-590">Wenn Sie Visual Studio (**nicht** Visual Studio Code) öffnen, können Sie das Testnachrichten Ergebnis visualisieren, da es im Bereich der *messagecontent* -Zeichenfolge gespeichert wird.</span><span class="sxs-lookup"><span data-stu-id="7d32d-590">If you now open Visual Studio (**not** Visual Studio Code), you can visualize your test message result, as it will be stored in the *MessageContent* string area.</span></span>

![benutzerdefinierte Funktion](images/AzureLabs-Lab313-71.png)

<span data-ttu-id="7d32d-592">Wenn der Tabellen Dienst und der Funktionen-app vorhanden sind, werden Ihre Ubuntu-Geräte Meldungen in der Tabelle " *iotmessages* " angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-592">With the Table Service and Function App in place, your Ubuntu device messages will appear in your *IoTMessages* Table.</span></span> <span data-ttu-id="7d32d-593">Wenn Sie nicht bereits ausgeführt werden, starten Sie das Gerät erneut, und Sie können die Ergebnismeldungen von Ihrem Gerät und Modul innerhalb Ihrer Tabelle mithilfe von Visual Studio *Cloud-Explorer*anzeigen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-593">If not already running, start your device again, and you will be able to see the result messages from your device, and module, within your Table, through using Visual Studio *Cloud Explorer*.</span></span>

![Visualisieren von Daten](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a><span data-ttu-id="7d32d-595">Kapitel 15: Power BI-Setup</span><span class="sxs-lookup"><span data-stu-id="7d32d-595">Chapter 15 - Power BI Setup</span></span>

<span data-ttu-id="7d32d-596">Zum Visualisieren der Daten von Ihrem IOT-Gerät richten Sie **Power BI** (Desktop Version) ein, um die Daten aus dem *Tabellen* Speicherdienst zu erfassen, den Sie soeben erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="7d32d-596">To visualize the data from your IOT device you will setup **Power BI** (desktop version), to collect the data from the *Table* Service, which you just created.</span></span> <span data-ttu-id="7d32d-597">Die *hololens* -Version von Power BI verwendet diese Daten dann, um das Ergebnis visuell darzustellen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-597">The *HoloLens* version of Power BI will then use that data to visualize the result.</span></span>

1.  <span data-ttu-id="7d32d-598">Öffnen Sie die Microsoft Store unter Windows 10, und suchen Sie nach **Power BI Desktop**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-598">Open the Microsoft Store on Windows 10 and search for **Power BI Desktop**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  <span data-ttu-id="7d32d-600">Laden Sie die Anwendung herunter.</span><span class="sxs-lookup"><span data-stu-id="7d32d-600">Download the application.</span></span> <span data-ttu-id="7d32d-601">Nachdem der Download abgeschlossen ist, öffnen Sie ihn.</span><span class="sxs-lookup"><span data-stu-id="7d32d-601">Once it has finished downloading, open it.</span></span>

3.  <span data-ttu-id="7d32d-602">Melden Sie sich mit Ihrem **Microsoft 365 Konto**bei *Power BI* an.</span><span class="sxs-lookup"><span data-stu-id="7d32d-602">Log into *Power BI* with your **Microsoft 365 account**.</span></span> <span data-ttu-id="7d32d-603">Sie werden möglicherweise zu einem Browser umgeleitet, um sich zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="7d32d-603">You may be redirected to a browser, to sign up.</span></span> <span data-ttu-id="7d32d-604">Nachdem Sie sich angemeldet haben, wechseln Sie zurück zur Power BI-APP, und melden Sie sich erneut an.</span><span class="sxs-lookup"><span data-stu-id="7d32d-604">Once you are signed up, go back to the Power BI app, and sign in again.</span></span>

4.  <span data-ttu-id="7d32d-605">Klicken Sie auf **Daten erhalten** , und klicken Sie dann auf **Weitere...** .</span><span class="sxs-lookup"><span data-stu-id="7d32d-605">Click on **Get Data** and then click on **More...**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  <span data-ttu-id="7d32d-607">Klicken Sie auf **Azure**, **Azure Table Storage**, und klicken Sie dann auf **verbinden**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-607">Click **Azure**, **Azure Table Storage**, then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  <span data-ttu-id="7d32d-609">Sie werden aufgefordert, die Tabellen- **URL** einzufügen, die Sie zuvor gesammelt haben ([in Schritt 13 von Kapitel 11](#chapter-11---create-table-service)), während Sie den Tabellen Speicherdienst erstellen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-609">You will be prompted to insert the **Table URL** that you collected earlier ([in step 13 of Chapter 11](#chapter-11---create-table-service)), while creating your Table Service.</span></span> <span data-ttu-id="7d32d-610">Nachdem Sie die URL eingefügt haben, löschen Sie den Teil des Pfads, der sich auf die Tabelle "Unterordner" bezieht (in diesem Kurs iotmessages).</span><span class="sxs-lookup"><span data-stu-id="7d32d-610">After inserting the URL, delete the portion of the path referring to the Table "sub-folder" (which was IoTMessages, in this course).</span></span> <span data-ttu-id="7d32d-611">Das Endergebnis sollte wie in der folgenden Abbildung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-611">The final result should be as displayed in the image below.</span></span> <span data-ttu-id="7d32d-612">Klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-612">Then click on **OK**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  <span data-ttu-id="7d32d-614">Wenn Sie Ihre Table Storage erstellen, werden Sie aufgefordert, den von Ihnen notierten **Speicher Schlüssel** ([in Schritt 11 von Kapitel 11](#chapter-11---create-table-service)) hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-614">You will be prompted to insert the **Storage Key** that you noted ([in step 11 of Chapter 11](#chapter-11---create-table-service)) earlier while creating your Table Storage.</span></span> <span data-ttu-id="7d32d-615">Klicken Sie dann auf **verbinden**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-615">Then click on **Connect**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. <span data-ttu-id="7d32d-617">Ein **Navigator Panel** wird angezeigt, und klicken Sie auf das Kontrollkästchen neben der Tabelle, und klicken Sie auf **Laden**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-617">A **Navigator Panel** will be displayed, tick the box next to your Table and click on **Load**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. <span data-ttu-id="7d32d-619">Die Tabelle wurde nun auf Power BI geladen, erfordert jedoch eine Abfrage, um die darin angezeigten Werte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-619">Your table has now been loaded on Power BI, but it requires a query to display the values in it.</span></span> <span data-ttu-id="7d32d-620">Klicken Sie hierzu mit der rechten Maustaste auf den Tabellennamen, der sich im **Bereich Felder** auf der rechten Seite des Bildschirms befindet.</span><span class="sxs-lookup"><span data-stu-id="7d32d-620">To do so, right-click on the table name located in the **FIELDS panel** at the right side of the screen.</span></span> <span data-ttu-id="7d32d-621">Klicken Sie dann auf **Abfrage bearbeiten**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-621">Then click on **Edit Query**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. <span data-ttu-id="7d32d-623">Ein **Power Query-Editor** wird als neues Fenster geöffnet, in dem die Tabelle angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="7d32d-623">A **Power Query Editor**  will open up as a new window, displaying your table.</span></span> <span data-ttu-id="7d32d-624">Klicken Sie in der *Inhalts* Spalte der Tabelle auf den Word- **Datensatz** , um den gespeicherten Inhalt visuell darzustellen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-624">Click on the word **Record** within the *Content* column of the table, to visualize your stored content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. <span data-ttu-id="7d32d-626">Klicken Sie oben links im Fenster auf die **Tabelle**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-626">Click on **Into Table**, at the top-left of the window.</span></span> 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. <span data-ttu-id="7d32d-628">Klicken Sie auf **Schließen, & anwenden**.</span><span class="sxs-lookup"><span data-stu-id="7d32d-628">Click on **Close & Apply**.</span></span>

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. <span data-ttu-id="7d32d-630">Nachdem das Laden der Abfrage abgeschlossen ist, können Sie im **Bereich Felder**auf der rechten Seite des Bildschirms die Felder mit den Parametern **Name** und **Wert**versehen, um den Inhalt der **messagecontent** -Spalte visuell darzustellen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-630">Once it has finished loading the query, within the **FIELDS panel**, on the right side of the screen, tick the boxes corresponding to the parameters **Name** and **Value**, to visualize the **MessageContent** column content.</span></span>

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. <span data-ttu-id="7d32d-632">Klicken Sie oben links im Fenster auf das blaue Datenträger **Symbol** , um die Arbeit in einem Ordner Ihrer Wahl zu speichern.</span><span class="sxs-lookup"><span data-stu-id="7d32d-632">Click on the **blue disk icon** at the top left of the window to save your work in a folder of your choice.</span></span>

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. <span data-ttu-id="7d32d-634">Sie können jetzt auf die Schaltfläche "veröffentlichen" klicken, um die Tabelle in Ihren Arbeitsbereich hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-634">You can now click on the Publish button to upload your table to your Workspace.</span></span> <span data-ttu-id="7d32d-635">Wenn Sie dazu aufgefordert werden, klicken Sie auf **Arbeitsbereich** und dann auf *auswählen*</span><span class="sxs-lookup"><span data-stu-id="7d32d-635">When prompted, click **My workspace** and click *Select*.</span></span> <span data-ttu-id="7d32d-636">Warten Sie, bis das erfolgreiche Ergebnis der Übermittlung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="7d32d-636">Wait for it to display the successful result of the submission.</span></span>

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> <span data-ttu-id="7d32d-639">Das folgende Kapitel ist hololens-spezifisch.</span><span class="sxs-lookup"><span data-stu-id="7d32d-639">The following Chapter is HoloLens specific.</span></span> <span data-ttu-id="7d32d-640">Power BI derzeit nicht als immersive Anwendung verfügbar ist, können Sie die Desktop Version jedoch im Windows Mixed Reality-Portal (auch als "Klippe House" bezeichnet) über die Desktop-App ausführen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-640">Power BI is not currently availble as an immersive application, however you can run the desktop version in the Windows Mixed Reality Portal (aka Cliff House), through the Desktop app.</span></span>

## <a name="chapter-16---display-power-bi-data-on-hololens"></a><span data-ttu-id="7d32d-641">Kapitel 16: Anzeigen von Power BI Daten in hololens</span><span class="sxs-lookup"><span data-stu-id="7d32d-641">Chapter 16 - Display Power BI data on HoloLens</span></span>

1. <span data-ttu-id="7d32d-642">Melden Sie sich auf Ihren hololens beim **Microsoft Store**an, indem Sie auf das zugehörige Symbol in der Anwendungsliste tippen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-642">On your HoloLens, log in to the **Microsoft Store**, by tapping on its icon in the applications list.</span></span>

    ![Power BI Hl](images/AzureLabs-Lab313-87.png)

2. <span data-ttu-id="7d32d-644">Suchen Sie die **Power BI** Anwendung, und laden Sie Sie herunter.</span><span class="sxs-lookup"><span data-stu-id="7d32d-644">Search and then download the **Power BI** application.</span></span>

    ![Power BI Hl](images/AzureLabs-Lab313-88.png)

3. <span data-ttu-id="7d32d-646">Starten Sie **Power BI** aus der Anwendungsliste.</span><span class="sxs-lookup"><span data-stu-id="7d32d-646">Start **Power BI** from your applications list.</span></span> 

4. <span data-ttu-id="7d32d-647">**Power BI** werden Sie möglicherweise aufgefordert, sich bei Ihrem **Microsoft 365 Konto**anzumelden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-647">**Power BI** might ask you to login to your **Microsoft 365 account**.</span></span>

5. <span data-ttu-id="7d32d-648">In der APP sollte der Arbeitsbereich standardmäßig angezeigt werden, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-648">Once inside the app, the workspace should display by default as shown in the image below.</span></span> <span data-ttu-id="7d32d-649">Wenn dies nicht der Fall ist, klicken Sie einfach auf das Arbeitsbereichs Symbol auf der linken Seite des Fensters.</span><span class="sxs-lookup"><span data-stu-id="7d32d-649">If that does not happen, simply click on the workspace icon on the left side of the window.</span></span>

    ![Power BI Hl](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a><span data-ttu-id="7d32d-651">Ihre IOT Hub Anwendung ist abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="7d32d-651">Your finished your IoT Hub application</span></span>

<span data-ttu-id="7d32d-652">Herzlichen Glückwunsch, Sie haben erfolgreich einen IOT Hub-Dienst mit einem simulierten VM Edge-Gerät erstellt.</span><span class="sxs-lookup"><span data-stu-id="7d32d-652">Congratulations, you have successfully created an IoT Hub Service, with a simulated Virtual Machine Edge device.</span></span> <span data-ttu-id="7d32d-653">Ihr Gerät kann die Ergebnisse eines Machine Learning-Modells an einen Azure-Tabellen Dienst übermitteln, der von einem Azure-Funktionen-APP, der in Power BI gelesen und in einem Microsoft hololens visualisiert ist, ermöglicht wird.</span><span class="sxs-lookup"><span data-stu-id="7d32d-653">Your device can  communicate the results of a machine learning model to an Azure Table Service, facilitated by an Azure Function App, which is read into Power BI, and visualized within a Microsoft HoloLens.</span></span>
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="7d32d-655">Bonus Übungen</span><span class="sxs-lookup"><span data-stu-id="7d32d-655">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="7d32d-656">Übung 1</span><span class="sxs-lookup"><span data-stu-id="7d32d-656">Exercise 1</span></span>

<span data-ttu-id="7d32d-657">Erweitern Sie die in der Tabelle gespeicherte Messaging Struktur, und zeigen Sie Sie als Diagramm an.</span><span class="sxs-lookup"><span data-stu-id="7d32d-657">Expand the messaging structure stored in the table and display it as a graph.</span></span> <span data-ttu-id="7d32d-658">Möglicherweise möchten Sie weitere Daten sammeln und in derselben Tabelle speichern, damit Sie später angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7d32d-658">You might want to collect more data and store it in the same table, to be later displayed.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="7d32d-659">Übung 2</span><span class="sxs-lookup"><span data-stu-id="7d32d-659">Exercise 2</span></span>

<span data-ttu-id="7d32d-660">Erstellen Sie ein zusätzliches Modul für die Kamera Erfassung, das auf dem IOT-Board bereitgestellt werden soll, damit es Bilder über die zu analysierende Kamera erfassen kann.</span><span class="sxs-lookup"><span data-stu-id="7d32d-660">Create an additional "camera capture" module to be deployed on the IoT board, so that it can capture images through the camera to be analyzed.</span></span>
