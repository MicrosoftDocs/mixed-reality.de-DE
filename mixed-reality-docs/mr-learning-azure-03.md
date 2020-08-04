---
title: Azure-Cloudtutorials – 3. Integrieren von Azure-Custom Vision
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie Azure Custom Vision innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, HoloLens 2, Azure Custom Vision, Azure Cognitive Services
ms.localizationpriority: high
ms.openlocfilehash: 0fc3793315dd05f91a6193b68343205f53a3092a
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376462"
---
# <a name="3-integrating-azure-custom-vision"></a><span data-ttu-id="7977b-105">3. Integrieren von Azure-Custom Vision</span><span class="sxs-lookup"><span data-stu-id="7977b-105">3. Integrating Azure Custom Vision</span></span>

<span data-ttu-id="7977b-106">In diesem Tutorial erfahren Sie, wie Sie **Azure Custom Vision** verwenden. Sie laden einen Satz Fotos hoch, um sie einem *nachverfolgten Objekt* zuzuordnen. Laden Sie sie in den **Custom Vision**-Dienst hoch, und starten Sie den Trainingsvorgang.</span><span class="sxs-lookup"><span data-stu-id="7977b-106">In this tutorial, you will learn how to use **Azure Custom Vision**.You will upload a set of photos to associate it with a *Tracked Object*, upload them to the **Custom Vision** service and start the training process.</span></span> <span data-ttu-id="7977b-107">Anschließend verwenden Sie den Dienst, um das *nachverfolgte Objekt* zu erkennen, indem Sie Fotos aus dem Webcamfeed erfassen.</span><span class="sxs-lookup"><span data-stu-id="7977b-107">Then you will use the service to detect the *Tracked Object* by capturing photos from the webcam feed.</span></span>

## <a name="objectives"></a><span data-ttu-id="7977b-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="7977b-108">Objectives</span></span>

* <span data-ttu-id="7977b-109">Grundlagen zu Azure Custom Vision</span><span class="sxs-lookup"><span data-stu-id="7977b-109">Learn the basics about Azure Custom Vision</span></span>
* <span data-ttu-id="7977b-110">Erfahren Sie, wie Sie die Szene einrichten, um Azure Custom Vision in diesem Projekt zu verwenden</span><span class="sxs-lookup"><span data-stu-id="7977b-110">Learn how to setup the scene to use Custom Vision in this project</span></span>
* <span data-ttu-id="7977b-111">Erfahren Sie, wie Sie Uploads, Training und die Erkennung von Bildern integrieren</span><span class="sxs-lookup"><span data-stu-id="7977b-111">Learn how to integrate upload, train and detect images</span></span>

## <a name="understanding-azure-custom-vision"></a><span data-ttu-id="7977b-112">Grundlegendes zu Azure Custom Vision</span><span class="sxs-lookup"><span data-stu-id="7977b-112">Understanding Azure Custom Vision</span></span>

<span data-ttu-id="7977b-113">**Azure Custom Vision** ist Teil der **Cognitive Services**-Produktfamilie und wird zum Trainieren von Bildklassifizierern verwendet.</span><span class="sxs-lookup"><span data-stu-id="7977b-113">**Azure Custom Vision** is part of the **Cognitive Services** family and is used to train image classifiers.</span></span> <span data-ttu-id="7977b-114">Der Bildklassifizierer ist ein KI-Dienst, der das trainierte Modell verwendet, um entsprechende Tags anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="7977b-114">The image classifier is an AI service that uses the trained model to apply matching tags.</span></span> <span data-ttu-id="7977b-115">Diese Klassifizierungsfunktion wird von unserer Anwendung verwendet, um *nachverfolgte Objekte* zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="7977b-115">This classification feature will be used by our application to detect *Tracked Objects*.</span></span>

<span data-ttu-id="7977b-116">Weitere Informationen zu [Azure Custom Vision](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span><span class="sxs-lookup"><span data-stu-id="7977b-116">Learn more about [Azure Custom Vision](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span></span>

## <a name="preparing-azure-custom-vision"></a><span data-ttu-id="7977b-117">Vorbereiten von Azure-Custom Vision</span><span class="sxs-lookup"><span data-stu-id="7977b-117">Preparing Azure Custom Vision</span></span>

<span data-ttu-id="7977b-118">Bevor Sie beginnen können, müssen Sie ein Custom Vision-Projekt erstellen. Am schnellsten geht dies über das Webportal.</span><span class="sxs-lookup"><span data-stu-id="7977b-118">Before you can start, you have to create a custom vision project, the fastest way is by using the web portal.</span></span>

<span data-ttu-id="7977b-119">Befolgen Sie dieses [Schnellstarttutorial](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images) zum Einrichten Ihres Kontos und Projekts bis zum Abschnitt *Hochladen und Taggen von Bildern*.</span><span class="sxs-lookup"><span data-stu-id="7977b-119">Follow this [quickstart tutorial](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images) to setup your account and project until section *Upload and tag images*.</span></span>

> [!WARNING]
> <span data-ttu-id="7977b-120">Zum Trainieren eines Modells benötigen Sie mindestens zwei Tags und fünf Bilder pro Tag.</span><span class="sxs-lookup"><span data-stu-id="7977b-120">To train a model you need to have at least 2 tags and 5 images per tag.</span></span> <span data-ttu-id="7977b-121">Um diese Anwendung zu verwenden, sollten Sie mindestens ein Tag mit fünf Bildern erstellen, damit der Trainingsvorgang später nicht fehlschlägt.</span><span class="sxs-lookup"><span data-stu-id="7977b-121">To use this application you should at least create one tag with 5 images, so that the training process later won't fail.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="7977b-122">Vorbereiten der Szene</span><span class="sxs-lookup"><span data-stu-id="7977b-122">Preparing the scene</span></span>

<span data-ttu-id="7977b-123">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**.</span><span class="sxs-lookup"><span data-stu-id="7977b-123">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-1.png)

<span data-ttu-id="7977b-125">Ziehen Sie dort das Prefab **ObjectDetectionManager** in die Hierarchie der Szene.</span><span class="sxs-lookup"><span data-stu-id="7977b-125">From there drag the prefab **ObjectDetectionManager** into the scene Hierarchy.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-2.png)

<span data-ttu-id="7977b-127">Suchen Sie im Hierarchiefenster nach dem **ObjectDetectionManager**-Objekt, und wählen Sie es aus.</span><span class="sxs-lookup"><span data-stu-id="7977b-127">In the Hierarchy window locate the **ObjectDetectionManager** object and select it.</span></span>
<span data-ttu-id="7977b-128">Das Prefab **ObjectDetectionManager** enthält die Komponente **ObjectDetectionManager (Script)** . Wie Sie im Inspektor-Fenster erkennen können, hängt sie von mehreren Einstellungen ab.</span><span class="sxs-lookup"><span data-stu-id="7977b-128">The **ObjectDetectionManager** prefab contains the **ObjectDetectionManager (script)** component and as you can see from the Inspector window it depends on several settings.</span></span>

## <a name="retrieving-azure-api-resource-credentials"></a><span data-ttu-id="7977b-129">Abrufen von Azure-API-Ressourcenanmeldeinformationen</span><span class="sxs-lookup"><span data-stu-id="7977b-129">Retrieving Azure api resource credentials</span></span>

<span data-ttu-id="7977b-130">Die erforderlichen Anmeldeinformationen für die Einstellungen von **ObjectDetectionManager (Script)** können aus dem Azure-Portal und aus dem Custom Vision-Portal abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="7977b-130">The necessary credentials for the **ObjectDetectionManager (script)** settings can be retrieve from the Azure Portal and the custom vision portal.</span></span>

### <a name="azure-portal"></a><span data-ttu-id="7977b-131">Azure-Portal</span><span class="sxs-lookup"><span data-stu-id="7977b-131">Azure Portal</span></span>

<span data-ttu-id="7977b-132">Suchen Sie nach der Custom Vision-Ressource vom Typ **Cognitive Services**, die Sie im Abschnitt *Vorbereiten der Szene* dieses Tutorials erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="7977b-132">Find and locate the custom vision resource of type **Cognitive Services** you have created in the *Preparing the scene* section of this tutorial.</span></span> <span data-ttu-id="7977b-133">Klicken Sie dort auf *Keys and Endpoint* (Schlüssel und Endpunkt), um die erforderlichen Anmeldeinformationen abzurufen.</span><span class="sxs-lookup"><span data-stu-id="7977b-133">There click on *Keys and Endpoint* to retrieve the necessary credentials.</span></span>

### <a name="custom-vision-dashboard"></a><span data-ttu-id="7977b-134">Custom Vision-Dashboard</span><span class="sxs-lookup"><span data-stu-id="7977b-134">Custom Vision Dashboard</span></span>

<span data-ttu-id="7977b-135">Öffnen Sie das Projekt, das Sie für dieses Tutorial erstellt haben, im [Custom Vision](https://www.customvision.ai/projects)-Dashboard, und klicken Sie auf das Zahnradsymbol in der rechten oberen Ecke der Seite, um die Seite mit den Einstellungen zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="7977b-135">In the [custom vision](https://www.customvision.ai/projects) dashboard, open the project you have created for this tutorial and click on the top right corner of the page on the gear icon to open the settings page.</span></span> <span data-ttu-id="7977b-136">Hier finden Sie die erforderlichen Anmeldeinformationen im Abschnitt *Ressourcen* auf der rechten Seite.</span><span class="sxs-lookup"><span data-stu-id="7977b-136">Here on the right hand *Resources* section you will find the necessary credentials.</span></span>

<span data-ttu-id="7977b-137">Nachdem **ObjectDetectionManager (Script)** ordnungsgemäß eingerichtet wurde, suchen Sie in der Hierarchie der Szene nach dem **SceneController**-Objekt, und wählen Sie es aus.</span><span class="sxs-lookup"><span data-stu-id="7977b-137">Now with the **ObjectDetectionManager (script)** setup correctly, find the **SceneController** object in your scene Hierarchy and select it.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-3.png)

<span data-ttu-id="7977b-139">Sie sehen, dass das Feld *Object Detection Manager* (Objekterkennungs-Manager) in der **SceneController**-Komponente leer ist. Ziehen Sie **ObjectDetectionManager** aus der Hierarchie in dieses Feld, und speichern Sie die Szene.</span><span class="sxs-lookup"><span data-stu-id="7977b-139">You see *Object Detection Manager* field in the **SceneController** component is empty, drag the **ObjectDetectionManager** from the Hierarchy into that field and save the scene.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial3-section4-step1-4.png)

## <a name="take-and-upload-images"></a><span data-ttu-id="7977b-141">Aufnehmen und Hochladen von Bildern</span><span class="sxs-lookup"><span data-stu-id="7977b-141">Take and upload images</span></span>

<span data-ttu-id="7977b-142">Führen Sie die Szene aus, klicken Sie auf **Set Object** (Objekt festlegen), und geben Sie den Namen für eines der **nachverfolgten Objekte** ein, die Sie in der [vorherigen Lektion](mr-learning-azure-02.md) erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="7977b-142">Run the scene and click on **Set Object**, type in the name for one of the **Tracked Objects** you have created in the [previous lesson](mr-learning-azure-02.md).</span></span> <span data-ttu-id="7977b-143">Klicken Sie nun auf die Schaltfläche **Computer Vision** (Maschinelles Sehen), die Sie unten auf der **Objektkarte** finden.</span><span class="sxs-lookup"><span data-stu-id="7977b-143">Now click on **Computer Vision** button you can find at the bottom of the **Object Card**.</span></span>

<span data-ttu-id="7977b-144">Ein neues Fenster wird geöffnet, in dem Sie sechs Fotos aufnehmen müssen, um das Modell für die Bilderkennung zu trainieren.</span><span class="sxs-lookup"><span data-stu-id="7977b-144">A new window will open where you have to take six photos to train the model for image recognition.</span></span> <span data-ttu-id="7977b-145">Klicken Sie auf die Schaltfläche **Camera** (Kamera), und führen Sie eine AirTap-Aktion aus, wenn Sie das Objekt ansehen, das Sie nachverfolgen möchten. Führen Sie diesen Vorgang sechs Mal aus.</span><span class="sxs-lookup"><span data-stu-id="7977b-145">Click on the **Camera** button and perform an AirTap when you look on the object you like to track, do this six times.</span></span>

> [!TIP]
> <span data-ttu-id="7977b-146">Um das Modelltraining zu verbessern, versuchen Sie, jedes Bild aus unterschiedlichen Winkeln und unter verschiedenen Beleuchtungsbedingungen aufzunehmen.</span><span class="sxs-lookup"><span data-stu-id="7977b-146">To improve the model training try to take each image from different angles and lighting conditions.</span></span>

<span data-ttu-id="7977b-147">Wenn Sie über genügend Bilder verfügen, klicken Sie auf die Schaltfläche **Train** (Trainieren), um den Modelltrainingsprozess in der Cloud zu starten.</span><span class="sxs-lookup"><span data-stu-id="7977b-147">Once you have enough images click on the **Train** button to start the model training process in the cloud.</span></span> <span data-ttu-id="7977b-148">Wenn Sie das Training aktivieren, werden alle Bilder hochgeladen, und das Training wird gestartet. Dies kann bis zu einer Minute oder auch länger dauern.</span><span class="sxs-lookup"><span data-stu-id="7977b-148">Activating the training will upload all images and then start the training, this can take up to a minute or more.</span></span> <span data-ttu-id="7977b-149">Eine Meldung innerhalb des Menüs zeigt den aktuellen Status an, und sobald der Abschluss angezeigt wird, können Sie die Anwendung beenden.</span><span class="sxs-lookup"><span data-stu-id="7977b-149">A message inside the menu indicates the current progress and once it indicates the completion you can stop the application</span></span>

> [!TIP]
> <span data-ttu-id="7977b-150">**ObjectDetectionManager (Script)** lädt die aufgenommenen Bilder direkt in den Custom Vision-Dienst hoch.</span><span class="sxs-lookup"><span data-stu-id="7977b-150">The **ObjectDetectionManager (script)** directly uploads taken images into the Custom Vision service.</span></span> <span data-ttu-id="7977b-151">Als Alternative akzeptiert die Custom Vision-API URLs zu den Bildern. Als Übung können Sie **ObjectDetectionManager (Script)** , ändern, um die Bilder stattdessen in einen Blobspeicher hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="7977b-151">As an alternative the custom vision API accepts URLs to the images, as an exercise you can modify the **ObjectDetectionManager (script)** to upload the images to a Blob storage instead.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="7977b-152">Erkennen von Objekten</span><span class="sxs-lookup"><span data-stu-id="7977b-152">Detect objects</span></span>

<span data-ttu-id="7977b-153">Sie können das trainierte Modell nun testen, die Anwendung ausführen und im *Hauptmenü* auf **Search Object** (Objekt suchen) klicken und den Namen des betreffenden **nachverfolgten Objekts** eingeben.</span><span class="sxs-lookup"><span data-stu-id="7977b-153">You can now put the trained model to the test, run the application and from the *main menu* click on **Search Object** and type the name of the **Tracked Object** in question.</span></span> <span data-ttu-id="7977b-154">Die **Objektkarte** wird angezeigt. Klicken Sie auf die Schaltfläche **Custom Vision**.</span><span class="sxs-lookup"><span data-stu-id="7977b-154">The **Object Card** will appear and click on the **Custom Vision** button.</span></span> <span data-ttu-id="7977b-155">Hier beginnt **ObjectDetectionManager**, Bilder von der Kamera im Hintergrund zu erfassen, und der Status wird im Menü angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7977b-155">From here the **ObjectDetectionManager** will start taking image captures in the background from the camera and the progress will be indicated on the menu.</span></span> <span data-ttu-id="7977b-156">Richten Sie die Kamera auf das Objekt, mit dem Sie das Modell trainiert haben, und Sie sehen, dass das Objekt nach kurzer Zeit erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="7977b-156">Point the camera to the object you used to train the model and you will see that after a short while it will detect the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="7977b-157">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="7977b-157">Congratulations</span></span>

<span data-ttu-id="7977b-158">In diesem Tutorial haben Sie erfahren, wie Sie mithilfe von Azure Custom Vision Bilder trainieren und den Klassifizierungsdienst verwenden können, um Bilder zu erkennen, die dem zugehörigen **nachverfolgten Objekt** entsprechen.</span><span class="sxs-lookup"><span data-stu-id="7977b-158">In this tutorial you learned how Azure Custom Vision can be used to train images and use the classification service to detect images that match the associated **Tracked Object**.</span></span>

<span data-ttu-id="7977b-159">Im nächsten Tutorial erfahren Sie, wie Sie mithilfe von Azure Spatial Anchors ein *nachverfolgtes Objekt* mit einer Position in der physischen Welt verknüpfen und einen Pfeil anzeigen, der den Benutzer zurück zur verknüpften Position des nachverfolgten Objekts führt.</span><span class="sxs-lookup"><span data-stu-id="7977b-159">In the next tutorial you will learn how to use Azure Spatial Anchors to link a *Tracked Object* with a location in the physical world and how to display an arrow that will guide the user back to the Tracked Object's linked location.</span></span>

[<span data-ttu-id="7977b-160">Nächstes Tutorial: 4. Integrieren von Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="7977b-160">Next tutorial: 4. Integrating Azure Spatial Anchors</span></span>](mr-learning-azure-04.md)
