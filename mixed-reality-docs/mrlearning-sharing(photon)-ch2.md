---
title: 'Tutorials zu Mehrbenutzerfunktionen: 3 Verbinden mehrerer Benutzer'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: a597aadbddb49fefc824d8c5b5193585fa9476a5
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610910"
---
# <a name="2-connecting-multiple-users"></a><span data-ttu-id="4bb90-105">2. Verbinden mehrerer Benutzer</span><span class="sxs-lookup"><span data-stu-id="4bb90-105">2. Connecting multiple users</span></span>

<span data-ttu-id="4bb90-106">In diesem Tutorial lernen Sie, wie Sie mehrere Benutzer im Rahmen einer freigegebenen Live-Benutzererfahrung verbinden.</span><span class="sxs-lookup"><span data-stu-id="4bb90-106">In this tutorial, you will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="4bb90-107">Am Ende des Tutorials können Sie die Anwendung auf mehreren Geräten ausführen, und jedem Benutzer wird der bewegte Avatar anderer Benutzer in Echtzeit angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4bb90-107">By the end of the tutorial you will be able to run the application on multiple devices and have each user see the avatar of other users move in real-time.</span></span>

## <a name="objectives"></a><span data-ttu-id="4bb90-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="4bb90-108">Objectives</span></span>

* <span data-ttu-id="4bb90-109">Erlernen des Verbindens mehrerer Benutzer in einer freigegebenen Umgebung</span><span class="sxs-lookup"><span data-stu-id="4bb90-109">Learn how to connect multiple users in a shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="4bb90-110">Vorbereiten der Szene</span><span class="sxs-lookup"><span data-stu-id="4bb90-110">Preparing the scene</span></span>

<span data-ttu-id="4bb90-111">In diesem Abschnitt bereiten Sie die Szene vor, indem Sie einige der Tutorial-Prefabs hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="4bb90-111">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="4bb90-112">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs**.</span><span class="sxs-lookup"><span data-stu-id="4bb90-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder.</span></span> <span data-ttu-id="4bb90-113">Klicken Sie mit gedrückter STRG-Taste auf **DebugWindow**, **NetworkLobby** und **SharedPlayground**, um die drei Prefabs auszuwählen:</span><span class="sxs-lookup"><span data-stu-id="4bb90-113">While holding down the CTRL button, click on **DebugWindow**, **NetworkLobby**, and **SharedPlayground** to select the three prefabs:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section1-step1-1.png)

<span data-ttu-id="4bb90-115">Ziehen Sie die drei noch ausgewählten Prefabs auf das Hierarchiefenster, um sie der Szene hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="4bb90-115">With the three prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a><span data-ttu-id="4bb90-117">Erstellen des Benutzerprefabs</span><span class="sxs-lookup"><span data-stu-id="4bb90-117">Creating the user prefab</span></span>

<span data-ttu-id="4bb90-118">In diesem Abschnitt erstellen Sie ein Prefab, das verwendet wird, um auf der freigegebenen Benutzeroberfläche die Benutzer darzustellen.</span><span class="sxs-lookup"><span data-stu-id="4bb90-118">In this section, you will create a prefab that will be used to represent the users in the shared experience.</span></span>

### <a name="1-create-and-configure-the-user"></a><span data-ttu-id="4bb90-119">1. Erstellen und Konfigurieren des Benutzers</span><span class="sxs-lookup"><span data-stu-id="4bb90-119">1. Create and configure the user</span></span>

<span data-ttu-id="4bb90-120">Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf einen leeren Bereich, wählen Sie **Create Empty** (Leer erstellen) aus, um Ihrer Szene ein leeres Objekt hinzuzufügen, benennen Sie das Objekt **PhotonUser**, und konfigurieren Sie es folgendermaßen:</span><span class="sxs-lookup"><span data-stu-id="4bb90-120">In the Hierarchy window, right-click on an empty area and select **Create Empty** to add an empty object to your scene, name the object **PhotonUser**, and configure it as follows:</span></span>

* <span data-ttu-id="4bb90-121">Vergewissern Sie sich, dass die **Transformationsposition** auf X = 0, Y = 0, Z = 0 festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="4bb90-121">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-1.png)

<span data-ttu-id="4bb90-123">Verwenden Sie bei noch immer ausgewähltem **PhotonUser**-Objekt im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um dem PhotonUser-Objekt die **Photon User (Script)** -Komponente hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="4bb90-123">With the **PhotonUser** object still selected, in the Inspector window, use the **Add Component** button to add the **Photon User (Script)** component to the PhotonUser object:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-2.png)

<span data-ttu-id="4bb90-125">Verwenden Sie im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um dem PhotonUser-Objekt die Komponente **Generic Net Sync (Script)** hinzuzufügen, und konfigurieren Sie sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="4bb90-125">In the Inspector window, use the **Add Component** button to add the **Generic Net Sync (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="4bb90-126">Aktivieren Sie das Kontrollkästchen **Is User** (Ist Benutzer)</span><span class="sxs-lookup"><span data-stu-id="4bb90-126">Check the **Is User** checkbox</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-3.png)

<span data-ttu-id="4bb90-128">Verwenden Sie im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um dem PhotonUser-Objekt die Komponente **Photon View (Script)** hinzuzufügen, und konfigurieren Sie sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="4bb90-128">In the Inspector window, use the **Add Component** button to add the **Photon View (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="4bb90-129">Weisen Sie die Komponente „Generic Net Sync (Script)“ dem Feld **Observed Components** (Beobachtete Komponenten) zu</span><span class="sxs-lookup"><span data-stu-id="4bb90-129">To the **Observed Components** field, assign the Generic Net Sync (Script) component</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-4.png)

### <a name="2-create-the-avatar"></a><span data-ttu-id="4bb90-131">2. Erstellen des Avatars</span><span class="sxs-lookup"><span data-stu-id="4bb90-131">2. Create the avatar</span></span>

<span data-ttu-id="4bb90-132">Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf das **PhotonUser**-Objekt, wählen Sie **3D Object** > **Sphere** (3D-Objekt > Kugel) aus, um ein Kugelobjekt als untergeordnetes Objekt des PhotonUser-Objekts zu erstellen, und konfigurieren Sie es folgendermaßen:</span><span class="sxs-lookup"><span data-stu-id="4bb90-132">In the Hierarchy window, right-click on the **PhotonUser** object and select **3D Object** > **Sphere** to create a sphere object as a child of the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="4bb90-133">Vergewissern Sie sich, dass die **Transformationsposition** auf X = 0, Y = 0, Z = 0 festgelegt ist</span><span class="sxs-lookup"><span data-stu-id="4bb90-133">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="4bb90-134">Ändern Sie den **Transformationsmaßstab** auf eine passende Größe beispielsweise X = 0,15, Y = 0,15, Z = 0,15</span><span class="sxs-lookup"><span data-stu-id="4bb90-134">Change the Transform **Scale** to a suitable size, for example, X = 0.15, Y = 0.15, Z = 0.15</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step2-1.png)

### <a name="3-create-the-prefab"></a><span data-ttu-id="4bb90-136">3. Erstellen der Prefab</span><span class="sxs-lookup"><span data-stu-id="4bb90-136">3. Create the prefab</span></span>

<span data-ttu-id="4bb90-137">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources**:</span><span class="sxs-lookup"><span data-stu-id="4bb90-137">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-1.png)

<span data-ttu-id="4bb90-139">**Klicken und ziehen** Sie bei noch ausgewähltem Ordner „Resources“ das **PhotonUser**-Objekt aus dem Hierarchiefenster in den **Resources**-Ordner, um aus dem PhotonUser-Objekt ein Prefab zu machen:</span><span class="sxs-lookup"><span data-stu-id="4bb90-139">With the Resources folder still selected, **click-and-drag** the **PhotonUser** object from the Hierarchy window into the **Resources** folder to make the PhotonUser object a prefab:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-2.png)

<span data-ttu-id="4bb90-141">Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf das **PhotonUser**-Objekt, und wählen Sie **Löschen** aus, um es aus der Szene zu entfernen:</span><span class="sxs-lookup"><span data-stu-id="4bb90-141">In the Hierarchy window, right-click on the **PhotonUser** object and select **Delete** to remove it from the scene:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a><span data-ttu-id="4bb90-143">Konfigurieren von PUN zum Instanziieren des Benutzerprefabs</span><span class="sxs-lookup"><span data-stu-id="4bb90-143">Configuring PUN to instantiate the user prefab</span></span>

<span data-ttu-id="4bb90-144">In diesem Abschnitt konfigurieren Sie das Projekt für die Verwendung des PhotonUser-Prefabs, das Sie im vorherigen Abschnitt erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="4bb90-144">In this section, you will configure the project to use the PhotonUser prefab you created in the previous section.</span></span>

<span data-ttu-id="4bb90-145">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources**.</span><span class="sxs-lookup"><span data-stu-id="4bb90-145">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="4bb90-146">Klappen Sie im Hierarchiefenster das **NetworkLobby**-Objekt auf, wählen Sie das untergeordnete Objekt **NetworkRoom** aus, und suchen Sie dann im Inspektorfenster die Komponente **Photon Room (Script)** , um sie wie folgt zu konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="4bb90-146">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="4bb90-147">Weisen Sie das **PhotonUser**-Prefab aus dem Ordner „Resources“ dem **Photon User Prefab**-Feld zu</span><span class="sxs-lookup"><span data-stu-id="4bb90-147">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a><span data-ttu-id="4bb90-149">Ausprobieren der Benutzeroberfläche mit mehreren Benutzern</span><span class="sxs-lookup"><span data-stu-id="4bb90-149">Trying the experience with multiple users</span></span>

<span data-ttu-id="4bb90-150">Wenn Sie das Unity-Projekt jetzt für Ihre HoloLens erstellen und bereitstellen und anschließend, wieder in Unity, auf die Schaltfläche „Wiedergabe“ drücken, um in den Spielmodus zu wechseln, während die Anwendung auf Ihrer HoloLens ausgeführt wird, sehen Sie, wie sich der HoloLens-Benutzeravatar bewegt, wenn Sie Ihren Kopf (HoloLens) bewegen:</span><span class="sxs-lookup"><span data-stu-id="4bb90-150">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the application is running on your HoloLens, you will see the HoloLens user avatar move when you move your head (HoloLens) around:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section4-step1-1.gif)

> [!TIP]
> <span data-ttu-id="4bb90-152">Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer Anwendung auf Ihrem Gerät](mrlearning-base-ch1.md#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="4bb90-152">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

> [!CAUTION]
> <span data-ttu-id="4bb90-153">Die Anwendung muss eine Verbindung mit Photon herstellen, achten Sie also darauf, dass Ihr Computer/Gerät mit dem Internet verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="4bb90-153">The application needs to connect to Photon, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="4bb90-154">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="4bb90-154">Congratulations</span></span>

<span data-ttu-id="4bb90-155">Sie haben Ihr Projekt erfolgreich so konfiguriert, dass es mehreren Benutzern ermöglicht, Verbindungen mit der gleichen Benutzeroberfläche herzustellen und die Bewegungen der anderen Teilnehmer zu sehen.</span><span class="sxs-lookup"><span data-stu-id="4bb90-155">You have successfully configured your project to allow multiple users to connect to the same experience and see each other's movements.</span></span> <span data-ttu-id="4bb90-156">Im nächsten Tutorial implementieren Sie die Funktionalität zum Teilen der Bewegungen von Objekten unter mehreren Geräten.</span><span class="sxs-lookup"><span data-stu-id="4bb90-156">In the next tutorial, you will implement functionality so that the movements of objects are also shared across multiple devices.</span></span>

<span data-ttu-id="4bb90-157">[Nächstes Tutorial: 2. Freigeben von Objektbewegungen für mehrere Benutzer](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="4bb90-157">[Next tutorial: 2. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>
