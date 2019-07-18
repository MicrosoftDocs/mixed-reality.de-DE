---
title: Mr Learning Sharing Module für hololens 2
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Umgebungen mit mehreren Benutzern in einer hololens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 92bea1f3130f67645c10e36fe40cd4bc6f8b9151
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293668"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="491f0-104">Verbinden von mehreren Benutzern</span><span class="sxs-lookup"><span data-stu-id="491f0-104">Connecting multiple users</span></span>

<span data-ttu-id="491f0-105">In dieser Lektion erfahren Sie, wie Sie mehrere Benutzer im Rahmen einer Live-freigegebenen Benutzererfahrung verbinden.</span><span class="sxs-lookup"><span data-stu-id="491f0-105">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="491f0-106">Am Ende dieser Lektion sind Sie in der Lage, die Anwendung auf mehreren Geräten zu öffnen und den von einer Kugel dargestellten Avatar durch Darstellungen der einzelnen Joins anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="491f0-106">By the end of this lesson, you'll be able to open the application on multiple devices, and see avatar, represented by a sphere, representations of each person that joins.</span></span> 

<span data-ttu-id="491f0-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="491f0-107">Objectives:</span></span>

- <span data-ttu-id="491f0-108">Konfigurieren von Wortspiel innerhalb Ihrer Anwendung</span><span class="sxs-lookup"><span data-stu-id="491f0-108">Configure PUN within your application</span></span>
- <span data-ttu-id="491f0-109">Konfigurieren von Playern</span><span class="sxs-lookup"><span data-stu-id="491f0-109">Configure players</span></span>
- <span data-ttu-id="491f0-110">Erfahren Sie, wie Sie mehrere Benutzer mit einer gemeinsamen Benutzer Verbindung verbinden.</span><span class="sxs-lookup"><span data-stu-id="491f0-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="491f0-111">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="491f0-111">Instructions</span></span>

1. <span data-ttu-id="491f0-112">Ziehen Sie im Projekt Panel im Ordner Assets-> Resources-> Prefabs den Ordner "networklobby" in die Hierarchie, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="491f0-112">In the Assets->Resources->Prefabs folder in the Project panel, drag and drop the NetworkLobby prefab in to the hierarchy as shown in the image below.</span></span>

![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="491f0-114">Wenn Sie networklobby erweitern, sehen Sie ein untergeordnetes Objekt mit dem Namen networkroom.</span><span class="sxs-lookup"><span data-stu-id="491f0-114">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="491f0-115">Wenn Sie Network Room ausgewählt haben, wechseln Sie im Inspektor-Panel, und klicken Sie auf Komponente hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="491f0-115">With NetworkRoom selected, go into the Inspector panel, and click Add Component.</span></span> <span data-ttu-id="491f0-116">Suchen Sie nach photonview, und fügen Sie die Komponente hinzu.</span><span class="sxs-lookup"><span data-stu-id="491f0-116">Search for PhotonView and add the component.</span></span>

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="491f0-118">Erstellen Sie ein neues leeres Spielobjekt in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="491f0-118">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="491f0-119">Klicken Sie mit der rechten Maustaste in die Hierarchie, und wählen Sie im Kontextmenü leer aus.</span><span class="sxs-lookup"><span data-stu-id="491f0-119">Right click in the hierarchy, and select Empty from the Context menu.</span></span> <span data-ttu-id="491f0-120">Stellen Sie sicher, dass die Positionierung auf x = 0, y = 0, z = 0 festgelegt ist, und benennen Sie das Objekt "photonuser".</span><span class="sxs-lookup"><span data-stu-id="491f0-120">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="491f0-122">Klicken Sie auf Komponente hinzufügen, und geben Sie Generic net Sync ein. Wählen Sie die generische net Sync-Klasse aus.</span><span class="sxs-lookup"><span data-stu-id="491f0-122">Click Add Component, and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="491f0-123">Wenn die Klasse angezeigt wird, klicken Sie auf das Kontrollkästchen Benutzer, um Sie zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="491f0-123">When the class appears, click on the User check box to turn it on.</span></span> 

![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="491f0-125">Klicken Sie erneut auf Komponente hinzufügen, und geben Sie "Photon View" ein</span><span class="sxs-lookup"><span data-stu-id="491f0-125">Click on Add Component again, and type Photon View.</span></span> <span data-ttu-id="491f0-126">Wählen Sie die in der Dropdown Liste angezeigte Klasse der Photon-Ansicht aus.</span><span class="sxs-lookup"><span data-stu-id="491f0-126">Select the Photon View class that appears in the drop-down list.</span></span>

![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="491f0-128">Klicken Sie auf das Dateisymbol für die generische net Sync-Klasse.</span><span class="sxs-lookup"><span data-stu-id="491f0-128">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="491f0-129">Ziehen Sie es in das Feld beobachtete Komponenten der Photon-Ansicht.</span><span class="sxs-lookup"><span data-stu-id="491f0-129">Drag and drop it in the Photon View's Observed Components field.</span></span> 

![module3chapter3updateStep6im. png](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="491f0-131">Als Nächstes erstellen wir Bereiche, die jede Person darstellen, die mit einer gemeinsamen Benutzerfunktion verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="491f0-131">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="491f0-132">Klicken Sie mit der rechten Maustaste auf das soeben erstellte Objekt "photonuser", Scrollen Sie zu "3D-Objekt, und klicken Sie auf Kugel.</span><span class="sxs-lookup"><span data-stu-id="491f0-132">Right click the PhotonUser object you just created, and scrolldown to "3D Object, and click Sphere.</span></span> <span data-ttu-id="491f0-133">Dadurch wird ein Kugel Spielobjekt als untergeordnetes Element des photonuser-Objekts erstellt.</span><span class="sxs-lookup"><span data-stu-id="491f0-133">This will create a sphere game object as a child of the PhotonUser object.</span></span>

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="491f0-135">Skalieren Sie die Kugel auf x = 0,06, y = 0,06, AD z = 0,06.</span><span class="sxs-lookup"><span data-stu-id="491f0-135">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="491f0-137">Ziehen Sie das "photonuser"-Spielobjekt in den Ordner "Prefabs" im Projekt Panel, und löschen Sie es aus der Szene.</span><span class="sxs-lookup"><span data-stu-id="491f0-137">Drag the PhotonUser game object into the Prefabs folder in the Project panel, and then delete it from the scene.</span></span> <span data-ttu-id="491f0-138">Wir haben nun ein präfab erstellt, das verwendet werden kann, um neue Player in einer gemeinsamen Darstellung zu erstellen oder zu instanziieren.</span><span class="sxs-lookup"><span data-stu-id="491f0-138">We have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="491f0-140">Hinweis: Stellen Sie sicher, dass das Spielobjekt erfolgreich in den Ordner "Prefabs" kopiert wurde, bevor es aus der Hierarchie gelöscht wird.</span><span class="sxs-lookup"><span data-stu-id="491f0-140">Note: ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="491f0-141">Erstellen Sie ein neues-Objekt in der Hierarchie, indem Sie die Anweisungen in Schritt 3 befolgen, und benennen Sie es sharedplayground.</span><span class="sxs-lookup"><span data-stu-id="491f0-141">Create a new object in the hierarchy by following the instructions in Step 3, and name it SharedPlayground.</span></span> <span data-ttu-id="491f0-142">Klicken Sie dann auf Komponente hinzufügen, suchen Sie nach generischem Netzwerk-Manager, und klicken Sie darauf, um die generische Netzwerk-Manager-Komponente hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="491f0-142">Then, click Add Component, and search for generic network manager, and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="491f0-143">Ändern Sie die Position des Objekts in x = 0, y = 0 und z = 0.</span><span class="sxs-lookup"><span data-stu-id="491f0-143">Change the position of the object to x=0, y=0, and z =0.</span></span>

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="491f0-145">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="491f0-145">Congratulations</span></span>

<span data-ttu-id="491f0-146">Nachdem alle oben aufgeführten Schritte ausgeführt wurden und der Buildprozess ebenfalls vollständig ist, klicken Sie auf die Schaltfläche Wiedergabe, und verbinden Sie die hololens 2.</span><span class="sxs-lookup"><span data-stu-id="491f0-146">Once all the steps above are complete, and the build process is also complete, press the play button and connect your HoloLens 2.</span></span> <span data-ttu-id="491f0-147">Wenn Sie Ihre Kopfzeile bewegen, sollte eine Kugel angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="491f0-147">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="491f0-148">Dies wird für jeden Benutzer angezeigt, der Ihrem Unity-Projekt Beitritt.</span><span class="sxs-lookup"><span data-stu-id="491f0-148">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="491f0-149">[Nächste Lektion: Freigabe (Photon), Lektion 4](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="491f0-149">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>

