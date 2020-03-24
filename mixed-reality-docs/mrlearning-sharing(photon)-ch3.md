---
title: 'Tutorials zu Mehrbenutzerfunktionen: 3 Verbinden mehrerer Benutzer'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: cbe0d8d2db6c34ba262fe9c946b68366ed3dbb93
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031231"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="dc452-105">3. Verbinden mehrerer Benutzer</span><span class="sxs-lookup"><span data-stu-id="dc452-105">3. Connecting multiple users</span></span>

<span data-ttu-id="dc452-106">In dieser Lektion erfahren Sie, wie Sie mehrere Benutzer im Rahmen einer freigegebenen Live-Benutzererfahrung verbinden.</span><span class="sxs-lookup"><span data-stu-id="dc452-106">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="dc452-107">Am Ende dieser Lektion sind Sie in der Lage, die Anwendung auf mehreren Geräten zu öffnen und den Avatar anzuzeigen, der durch eine Kugel für jede teilnehmende Person dargestellt wird.</span><span class="sxs-lookup"><span data-stu-id="dc452-107">By the end of this lesson, you'll be able to open the application on multiple devices and see the avatar, represented by a sphere for each person that joins.</span></span>

## <a name="objectives"></a><span data-ttu-id="dc452-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="dc452-108">Objectives</span></span>

* <span data-ttu-id="dc452-109">Konfigurieren von PUN innerhalb Ihrer Anwendung</span><span class="sxs-lookup"><span data-stu-id="dc452-109">Configure PUN within your application</span></span>
* <span data-ttu-id="dc452-110">Konfigurieren von Playern</span><span class="sxs-lookup"><span data-stu-id="dc452-110">Configure players</span></span>
* <span data-ttu-id="dc452-111">Erlernen des Verbindens mehrerer Benutzer in einer freigegebenen Umgebung</span><span class="sxs-lookup"><span data-stu-id="dc452-111">Learn how to connect multiple users in a shared experience</span></span>

## <a name="instructions"></a><span data-ttu-id="dc452-112">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="dc452-112">Instructions</span></span>

1. <span data-ttu-id="dc452-113">Ziehen Sie im Ordner „Assets->Resources->Prefabs“ des Projektbereichs das NetworkLobby-Prefab auf die Hierarchie, und legen Sie es ab, wie in der Abbildung unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="dc452-113">In the Assets->Resources->Prefabs folder of the Project panel, drag and drop the NetworkLobby prefab into the hierarchy as shown in the image below.</span></span>

    ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="dc452-115">Wenn Sie NetworkLobby aufklappen, sehen Sie ein untergeordnetes Objekt mit dem Namen NetworkRoom.</span><span class="sxs-lookup"><span data-stu-id="dc452-115">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="dc452-116">Wechseln Sie mit ausgewähltem NetworkRoom-Objekt zum Inspektorbereich, und klicken Sie auf „Komponente hinzufügen“.</span><span class="sxs-lookup"><span data-stu-id="dc452-116">With NetworkRoom selected, go into the Inspector panel and click Add Component.</span></span> <span data-ttu-id="dc452-117">Suchen Sie nach PhotonView, und fügen Sie die Komponente hinzu.</span><span class="sxs-lookup"><span data-stu-id="dc452-117">Search for PhotonView and add the component.</span></span>

    ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="dc452-119">Erstellen Sie ein neues leeres Spielobjekt in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="dc452-119">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="dc452-120">Klicken Sie mit der rechten Maustaste in die Hierarchie, und wählen Sie im Kontextmenü „Leer“ aus.</span><span class="sxs-lookup"><span data-stu-id="dc452-120">Right-click in the hierarchy and select Empty from the Context menu.</span></span> <span data-ttu-id="dc452-121">Achten Sie darauf, dass die Position auf x=0, y=0, z=0 festgelegt ist, und benennen Sie das Objekt PhotonUser.</span><span class="sxs-lookup"><span data-stu-id="dc452-121">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

    ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="dc452-123">Klicken Sie auf „Komponente hinzufügen“, und geben Sie „Generic Net Sync“ ein. Wählen Sie die Klasse „Generic Net Sync“ aus.</span><span class="sxs-lookup"><span data-stu-id="dc452-123">Click Add Component and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="dc452-124">Wenn die Klasse angezeigt wird, klicken Sie auf das Kontrollkästchen „Benutzer“, um es zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="dc452-124">When the class appears, click the User check box to turn it on.</span></span>

    ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="dc452-126">Klicken Sie erneut auf „Komponente hinzufügen“, und geben Sie „Photon View“ ein.</span><span class="sxs-lookup"><span data-stu-id="dc452-126">Click Add Component again, and type Photon View.</span></span> <span data-ttu-id="dc452-127">Wählen Sie die Klasse „Photon View“ aus, die in der Dropdownliste angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="dc452-127">Select the Photon View class that appears in the drop-down list.</span></span>

    ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="dc452-129">Klicken Sie auf das Dateisymbol für die Generic Net Sync-Klasse.</span><span class="sxs-lookup"><span data-stu-id="dc452-129">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="dc452-130">Ziehen Sie die Klasse auf das Feld „Observed Components“ von Photon View.</span><span class="sxs-lookup"><span data-stu-id="dc452-130">Drag and drop it in the Photon View's Observed Components field.</span></span>

    ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png)

7. <span data-ttu-id="dc452-132">Als nächstes erstellen wir Kugeln zum Darstellen der einzelnen Personen, die an einer freigegebenen Benutzererfahrung teilnehmen.</span><span class="sxs-lookup"><span data-stu-id="dc452-132">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="dc452-133">Klicken Sie mit der rechten Maustaste auf das soeben erstellte PhotonUser-Objekt, scrollen Sie nach unten bis zu „3D Object“, und klicken Sie auf „Sphere“.</span><span class="sxs-lookup"><span data-stu-id="dc452-133">Right-click the PhotonUser object you just created, scroll-down to "3D Object and click Sphere.</span></span> <span data-ttu-id="dc452-134">Dadurch wird ein Kugelspielobjekt als untergeordnetes Objekt des PhotonUser-Objekts erstellt.</span><span class="sxs-lookup"><span data-stu-id="dc452-134">This will create a sphere game object as a child of the PhotonUser object.</span></span>

    ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="dc452-136">Verkleinern Sie die Kugel auf x=0,06, y=0,06 und z=0,06.</span><span class="sxs-lookup"><span data-stu-id="dc452-136">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

    ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="dc452-138">Ziehen Sie das PhotonUser-Spielobjekt auf den Prefabs-Ordner im Projektbereich, und löschen Sie ihn dann aus der Szene.</span><span class="sxs-lookup"><span data-stu-id="dc452-138">Drag the PhotonUser game object into the Prefabs folder in the Project panel and then delete it from the scene.</span></span> <span data-ttu-id="dc452-139">Sie haben nun ein Prefab erstellt, das beim Erstellen oder Instanziieren neuer Spieler in einer freigegebenen Benutzererfahrung verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="dc452-139">You have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

    ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

    >[!NOTE]
    ><span data-ttu-id="dc452-141">Vergewissern Sie sich, dass das Spielobjekt erfolgreich in den Prefabs-Ordner kopiert wurde, bevor Sie es aus der Hierarchie löschen.</span><span class="sxs-lookup"><span data-stu-id="dc452-141">Ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="dc452-142">Erstellen Sie ein neues-Objekt in der Hierarchie, indem Sie die Anweisungen in Schritt 3 befolgen, und nennen Sie es SharedPlayground.</span><span class="sxs-lookup"><span data-stu-id="dc452-142">Create a new object in the hierarchy by following the instructions in Step 3 and name it SharedPlayground.</span></span> <span data-ttu-id="dc452-143">Klicken Sie anschließend auf „Komponente hinzufügen“, und suchen Sie nach dem generischen Netzwerk-Manager.</span><span class="sxs-lookup"><span data-stu-id="dc452-143">Then, click Add Component and search for generic network manager.</span></span>  <span data-ttu-id="dc452-144">Klicken Sie erneut, um die Komponente „Generic Network Manager“ hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="dc452-144">Click it again to add the Generic Network Manager component.</span></span> <span data-ttu-id="dc452-145">Ändern Sie die Position des Objekts in x = 0, y = 0 und z = 0.</span><span class="sxs-lookup"><span data-stu-id="dc452-145">Change the position of the object to x=0, y=0, and z =0.</span></span>

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)

## <a name="congratulations"></a><span data-ttu-id="dc452-147">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="dc452-147">Congratulations</span></span>

<span data-ttu-id="dc452-148">Nachdem Sie alle Schritte oben ausgeführt haben und der Buildvorgang ebenfalls abgeschlossen ist, drücken Sie die Wiedergabe-Schaltfläche, und stellen Sie eine Verbindung mit Ihrer HoloLens 2 her.</span><span class="sxs-lookup"><span data-stu-id="dc452-148">Once all the steps above are complete and the build process is also complete, press the Play button and connect your HoloLens 2.</span></span> <span data-ttu-id="dc452-149">Sie sollten eine Kugel sehen, die sich umherbewegt, wenn Sie Ihren Kopf bewegen.</span><span class="sxs-lookup"><span data-stu-id="dc452-149">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="dc452-150">Dies wird für jeden Benutzer angezeigt, der Ihrem Unity-Projekt beitritt.</span><span class="sxs-lookup"><span data-stu-id="dc452-150">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="dc452-151">[Nächste Lektion: 4. Freigeben von Objektbewegungen für mehrere Benutzer](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="dc452-151">[Next Lesson: 4. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch4.md)</span></span>
