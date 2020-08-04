---
title: 'Tutorials zu Mehrbenutzerfunktionen: 3 Verbinden mehrerer Benutzer'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 5937b581e92ffc5a13b55574ffd8a0ca7c4bca40
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376392"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="6da78-105">3. Verbinden mehrerer Benutzer</span><span class="sxs-lookup"><span data-stu-id="6da78-105">3. Connecting multiple users</span></span>

<span data-ttu-id="6da78-106">In diesem Tutorial lernen Sie, wie Sie mehrere Benutzer im Rahmen einer freigegebenen Live-Benutzererfahrung verbinden.</span><span class="sxs-lookup"><span data-stu-id="6da78-106">In this tutorial, you will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="6da78-107">Am Ende des Tutorials können Sie die App auf mehreren Geräten ausführen, und jedem Benutzer wird der bewegte Avatar anderer Benutzer in Echtzeit angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6da78-107">By the end of the tutorial, you will be able to run the app on multiple devices and have each user see the avatar of other users move in real-time.</span></span>

## <a name="objectives"></a><span data-ttu-id="6da78-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="6da78-108">Objectives</span></span>

* <span data-ttu-id="6da78-109">Erlernen des Verbindens mehrerer Benutzer in einer freigegebenen Umgebung</span><span class="sxs-lookup"><span data-stu-id="6da78-109">Learn how to connect multiple users in a shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="6da78-110">Vorbereiten der Szene</span><span class="sxs-lookup"><span data-stu-id="6da78-110">Preparing the scene</span></span>

<span data-ttu-id="6da78-111">In diesem Abschnitt bereiten Sie die Szene vor, indem Sie einige der Tutorial-Prefabs hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="6da78-111">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="6da78-112">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs**, klicken Sie auf die folgenden Prefabs, und ziehen Sie sie dann in das Hierarchiefenster, um sie Ihrer Szene hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="6da78-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="6da78-113">**NetworkLobby**-Prefab</span><span class="sxs-lookup"><span data-stu-id="6da78-113">**NetworkLobby** prefab</span></span>
* <span data-ttu-id="6da78-114">**SharedPlayground**-Prefab</span><span class="sxs-lookup"><span data-stu-id="6da78-114">**SharedPlayground** prefab</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

<span data-ttu-id="6da78-116">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs**, klicken Sie auf das folgende Prefab, und ziehen Sie es in das Hierarchiefenster, um es Ihrer Szene hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="6da78-116">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefab into the Hierarchy window to add it to your scene:</span></span>

* <span data-ttu-id="6da78-117">**DebugWindow**-Prefab</span><span class="sxs-lookup"><span data-stu-id="6da78-117">**DebugWindow** prefab</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a><span data-ttu-id="6da78-119">Erstellen des Benutzerprefabs</span><span class="sxs-lookup"><span data-stu-id="6da78-119">Creating the user prefab</span></span>

<span data-ttu-id="6da78-120">In diesem Abschnitt erstellen Sie ein Prefab, das verwendet wird, um auf der freigegebenen Benutzeroberfläche die Benutzer darzustellen.</span><span class="sxs-lookup"><span data-stu-id="6da78-120">In this section, you will create a prefab that will be used to represent the users in the shared experience.</span></span>

### <a name="1-create-and-configure-the-user"></a><span data-ttu-id="6da78-121">1. Erstellen und Konfigurieren des Benutzers</span><span class="sxs-lookup"><span data-stu-id="6da78-121">1. Create and configure the user</span></span>

<span data-ttu-id="6da78-122">Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf einen leeren Bereich, wählen Sie **Create Empty** (Leer erstellen) aus, um Ihrer Szene ein leeres Objekt hinzuzufügen, benennen Sie das Objekt **PhotonUser**, und konfigurieren Sie es folgendermaßen:</span><span class="sxs-lookup"><span data-stu-id="6da78-122">In the Hierarchy window, right-click on an empty area and select **Create Empty** to add an empty object to your scene, name the object **PhotonUser**, and configure it as follows:</span></span>

* <span data-ttu-id="6da78-123">Vergewissern Sie sich, dass die **Transformationsposition** auf X = 0, Y = 0, Z = 0 festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="6da78-123">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-1.png)

<span data-ttu-id="6da78-125">Wählen Sie im Hierarchiefenster das **PhotonUser**-Objekt aus, und verwenden Sie dann im Inspektor-Fenster die Schaltfläche **Add Component** (Komponente hinzufügen), um dem PhotonUser-Objekt die Komponente **Photon User (Script)** hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="6da78-125">In the Hierarchy window, select the **PhotonUser** object, then in the Inspector window, use the **Add Component** button to add the **Photon User (Script)** component to the PhotonUser object:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-2.png)

<span data-ttu-id="6da78-127">Verwenden Sie im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um dem PhotonUser-Objekt die Komponente **Generic Net Sync (Script)** hinzuzufügen, und konfigurieren Sie sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="6da78-127">In the Inspector window, use the **Add Component** button to add the **Generic Net Sync (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="6da78-128">Aktivieren Sie das Kontrollkästchen **Is User** (Ist Benutzer)</span><span class="sxs-lookup"><span data-stu-id="6da78-128">Check the **Is User** checkbox</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-3.png)

<span data-ttu-id="6da78-130">Verwenden Sie im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um dem PhotonUser-Objekt die Komponente **Photon View (Script)** hinzuzufügen, und konfigurieren Sie sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="6da78-130">In the Inspector window, use the **Add Component** button to add the **Photon View (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="6da78-131">Weisen Sie die Komponente **Generic Net Sync (Script)** dem Feld **Observed Components** (Beobachtete Komponenten) zu.</span><span class="sxs-lookup"><span data-stu-id="6da78-131">To the **Observed Components** field, assign the **Generic Net Sync (Script)** component</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-4.png)

### <a name="2-create-the-avatar"></a><span data-ttu-id="6da78-133">2. Erstellen des Avatars</span><span class="sxs-lookup"><span data-stu-id="6da78-133">2. Create the avatar</span></span>

<span data-ttu-id="6da78-134">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Materials**, um nach den MRTK-Materialien zu suchen.</span><span class="sxs-lookup"><span data-stu-id="6da78-134">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Materials** folder to locate the MRTK materials.</span></span>

<span data-ttu-id="6da78-135">Klicken Sie dann im Hierarchiefenster mit der rechten Maustaste auf das **PhotonUser**-Objekt, wählen Sie **3D Object** > **Sphere** (3D-Objekt > Kugel) aus, um ein Kugelobjekt als untergeordnetes Objekt des PhotonUser-Objekts zu erstellen, und konfigurieren Sie es folgendermaßen:</span><span class="sxs-lookup"><span data-stu-id="6da78-135">Then, in the Hierarchy window, right-click on the **PhotonUser** object and select **3D Object** > **Sphere** to create a sphere object as a child of the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="6da78-136">Vergewissern Sie sich, dass die **Transformationsposition** auf X = 0, Y = 0, Z = 0 festgelegt ist</span><span class="sxs-lookup"><span data-stu-id="6da78-136">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="6da78-137">Ändern Sie den **Transformationsmaßstab** auf eine passende Größe beispielsweise X = 0,15, Y = 0,15, Z = 0,15</span><span class="sxs-lookup"><span data-stu-id="6da78-137">Change the Transform **Scale** to a suitable size, for example, X = 0.15, Y = 0.15, Z = 0.15</span></span>
* <span data-ttu-id="6da78-138">Weisen Sie dem Feld „MeshRenderer > Materials > **Element 0**“ das Material **MRTK_Standard_White** zu.</span><span class="sxs-lookup"><span data-stu-id="6da78-138">To the MeshRenderer > Materials > **Element 0** field, assign the **MRTK_Standard_White** material</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step2-1.png)

### <a name="3-create-the-prefab"></a><span data-ttu-id="6da78-140">3. Erstellen der Prefab</span><span class="sxs-lookup"><span data-stu-id="6da78-140">3. Create the prefab</span></span>

<span data-ttu-id="6da78-141">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources**:</span><span class="sxs-lookup"><span data-stu-id="6da78-141">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-1.png)

<span data-ttu-id="6da78-143">**Klicken und ziehen** Sie bei noch ausgewähltem Ordner „Resources“ das **PhotonUser**-Objekt aus dem Hierarchiefenster in den **Resources**-Ordner, um aus dem PhotonUser-Objekt ein Prefab zu machen:</span><span class="sxs-lookup"><span data-stu-id="6da78-143">With the Resources folder still selected, **click-and-drag** the **PhotonUser** object from the Hierarchy window into the **Resources** folder to make the PhotonUser object a prefab:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-2.png)

<span data-ttu-id="6da78-145">Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf das **PhotonUser**-Objekt, und wählen Sie **Löschen** aus, um es aus der Szene zu entfernen:</span><span class="sxs-lookup"><span data-stu-id="6da78-145">In the Hierarchy window, right-click on the **PhotonUser** object and select **Delete** to remove it from the scene:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a><span data-ttu-id="6da78-147">Konfigurieren von PUN zum Instanziieren des Benutzerprefabs</span><span class="sxs-lookup"><span data-stu-id="6da78-147">Configuring PUN to instantiate the user prefab</span></span>

<span data-ttu-id="6da78-148">In diesem Abschnitt konfigurieren Sie das Projekt für die Verwendung des PhotonUser-Prefabs, das Sie im vorherigen Abschnitt erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="6da78-148">In this section, you will configure the project to use the PhotonUser prefab you created in the previous section.</span></span>

<span data-ttu-id="6da78-149">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources**.</span><span class="sxs-lookup"><span data-stu-id="6da78-149">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="6da78-150">Klappen Sie im Hierarchiefenster das **NetworkLobby**-Objekt auf, wählen Sie das untergeordnete Objekt **NetworkRoom** aus, und suchen Sie dann im Inspektorfenster die Komponente **Photon Room (Script)** , um sie wie folgt zu konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="6da78-150">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="6da78-151">Weisen Sie das **PhotonUser**-Prefab aus dem Ordner „Resources“ dem **Photon User Prefab**-Feld zu</span><span class="sxs-lookup"><span data-stu-id="6da78-151">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a><span data-ttu-id="6da78-153">Ausprobieren der Benutzeroberfläche mit mehreren Benutzern</span><span class="sxs-lookup"><span data-stu-id="6da78-153">Trying the experience with multiple users</span></span>

<span data-ttu-id="6da78-154">Wenn Sie das Unity-Projekt jetzt für Ihr HoloLens-Gerät erstellen und bereitstellen und zurück in Unity in den Spielmodus wechseln, während die App auf Ihrem HoloLens-Gerät ausgeführt wird, sehen Sie, wie sich der HoloLens-Benutzeravatar bewegt, wenn Sie Ihren Kopf (HoloLens) bewegen:</span><span class="sxs-lookup"><span data-stu-id="6da78-154">If you now build and deploy the Unity project to your HoloLens, then, back in Unity, enter Game mode while the app is running on your HoloLens, you will see the HoloLens user avatar move when you move your head (HoloLens) around:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> <span data-ttu-id="6da78-156">Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer App auf dem HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="6da78-156">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!CAUTION]
> <span data-ttu-id="6da78-157">Die App muss eine Verbindung mit Photon herstellen, achten Sie also darauf, dass Ihr Computer/Gerät mit dem Internet verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="6da78-157">The app needs to connect to Photon, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="6da78-158">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="6da78-158">Congratulations</span></span>

<span data-ttu-id="6da78-159">Sie haben Ihr Projekt erfolgreich so konfiguriert, dass es mehreren Benutzern ermöglicht, Verbindungen mit der gleichen Benutzeroberfläche herzustellen und die Bewegungen der anderen Teilnehmer zu sehen.</span><span class="sxs-lookup"><span data-stu-id="6da78-159">You have successfully configured your project to allow multiple users to connect to the same experience and see each other's movements.</span></span> <span data-ttu-id="6da78-160">Im nächsten Tutorial implementieren Sie die Funktionalität zum Teilen der Bewegungen von Objekten unter mehreren Geräten.</span><span class="sxs-lookup"><span data-stu-id="6da78-160">In the next tutorial, you will implement functionality so that the movements of objects are also shared across multiple devices.</span></span>

[<span data-ttu-id="6da78-161">Nächstes Tutorial: 4. Freigeben von Objektbewegungen für mehrere Benutzer</span><span class="sxs-lookup"><span data-stu-id="6da78-161">Next Tutorial: 4. Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
