---
title: Lernprogramme für Mehrbenutzerfunktionen-3. Verbinden von mehreren Benutzern
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Umgebungen mit mehreren Benutzern in einer hololens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: d3068a1ebbbc2b6db8b563be8bf8c6e488e9491a
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701938"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="c4141-105">3. Verbinden von mehreren Benutzern</span><span class="sxs-lookup"><span data-stu-id="c4141-105">3. Connecting multiple users</span></span>

<span data-ttu-id="c4141-106">In dieser Lektion erfahren Sie, wie Sie mehrere Benutzer im Rahmen einer Live-freigegebenen Benutzererfahrung verbinden.</span><span class="sxs-lookup"><span data-stu-id="c4141-106">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="c4141-107">Am Ende dieser Lektion sind Sie in der Lage, die Anwendung auf mehreren Geräten zu öffnen und den von einer Kugel dargestellten Avatar durch Darstellungen der einzelnen Joins anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="c4141-107">By the end of this lesson, you'll be able to open the application on multiple devices, and see avatar, represented by a sphere, representations of each person that joins.</span></span> 

<span data-ttu-id="c4141-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="c4141-108">Objectives:</span></span>

- <span data-ttu-id="c4141-109">Konfigurieren von Wortspiel innerhalb Ihrer Anwendung</span><span class="sxs-lookup"><span data-stu-id="c4141-109">Configure PUN within your application</span></span>
- <span data-ttu-id="c4141-110">Konfigurieren von Playern</span><span class="sxs-lookup"><span data-stu-id="c4141-110">Configure players</span></span>
- <span data-ttu-id="c4141-111">Erfahren Sie, wie Sie mehrere Benutzer mit einer gemeinsamen Benutzer Verbindung verbinden.</span><span class="sxs-lookup"><span data-stu-id="c4141-111">Learn how to connect multiple users in a shared experience</span></span>

## <a name="instructions"></a><span data-ttu-id="c4141-112">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="c4141-112">Instructions</span></span>

1. <span data-ttu-id="c4141-113">Ziehen Sie im Projekt Panel im Ordner Assets-> Resources-> Prefabs den Ordner "networklobby" in die Hierarchie, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="c4141-113">In the Assets->Resources->Prefabs folder in the Project panel, drag and drop the NetworkLobby prefab in to the hierarchy as shown in the image below.</span></span>

![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="c4141-115">Wenn Sie networklobby erweitern, sehen Sie ein untergeordnetes Objekt mit dem Namen networkroom.</span><span class="sxs-lookup"><span data-stu-id="c4141-115">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="c4141-116">Wenn Sie Network Room ausgewählt haben, wechseln Sie im Inspektor-Panel, und klicken Sie auf Komponente hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c4141-116">With NetworkRoom selected, go into the Inspector panel, and click Add Component.</span></span> <span data-ttu-id="c4141-117">Suchen Sie nach photonview, und fügen Sie die Komponente hinzu.</span><span class="sxs-lookup"><span data-stu-id="c4141-117">Search for PhotonView and add the component.</span></span>

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="c4141-119">Erstellen Sie ein neues leeres Spielobjekt in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="c4141-119">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="c4141-120">Klicken Sie mit der rechten Maustaste in die Hierarchie, und wählen Sie im Kontextmenü leer aus.</span><span class="sxs-lookup"><span data-stu-id="c4141-120">Right click in the hierarchy, and select Empty from the Context menu.</span></span> <span data-ttu-id="c4141-121">Stellen Sie sicher, dass die Positionierung auf x = 0, y = 0, z = 0 festgelegt ist, und benennen Sie das Objekt "photonuser".</span><span class="sxs-lookup"><span data-stu-id="c4141-121">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="c4141-123">Klicken Sie auf Komponente hinzufügen, und geben Sie Generic net Sync ein. Wählen Sie die generische net Sync-Klasse aus.</span><span class="sxs-lookup"><span data-stu-id="c4141-123">Click Add Component, and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="c4141-124">Wenn die Klasse angezeigt wird, klicken Sie auf das Kontrollkästchen Benutzer, um Sie zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="c4141-124">When the class appears, click on the User check box to turn it on.</span></span> 

![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="c4141-126">Klicken Sie erneut auf Komponente hinzufügen, und geben Sie "Photon View" ein</span><span class="sxs-lookup"><span data-stu-id="c4141-126">Click on Add Component again, and type Photon View.</span></span> <span data-ttu-id="c4141-127">Wählen Sie die in der Dropdown Liste angezeigte Klasse der Photon-Ansicht aus.</span><span class="sxs-lookup"><span data-stu-id="c4141-127">Select the Photon View class that appears in the drop-down list.</span></span>

![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="c4141-129">Klicken Sie auf das Dateisymbol für die generische net Sync-Klasse.</span><span class="sxs-lookup"><span data-stu-id="c4141-129">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="c4141-130">Ziehen Sie es in das Feld beobachtete Komponenten der Photon-Ansicht.</span><span class="sxs-lookup"><span data-stu-id="c4141-130">Drag and drop it in the Photon View's Observed Components field.</span></span> 

![module3chapter3updateStep6im. png](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="c4141-132">Als Nächstes erstellen wir Bereiche, die jede Person darstellen, die mit einer gemeinsamen Benutzerfunktion verbunden ist.</span><span class="sxs-lookup"><span data-stu-id="c4141-132">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="c4141-133">Klicken Sie mit der rechten Maustaste auf das soeben erstellte Objekt "photonuser", Scrollen Sie zu "3D-Objekt, und klicken Sie auf Kugel.</span><span class="sxs-lookup"><span data-stu-id="c4141-133">Right click the PhotonUser object you just created, and scrolldown to "3D Object, and click Sphere.</span></span> <span data-ttu-id="c4141-134">Dadurch wird ein Kugel Spielobjekt als untergeordnetes Element des photonuser-Objekts erstellt.</span><span class="sxs-lookup"><span data-stu-id="c4141-134">This will create a sphere game object as a child of the PhotonUser object.</span></span>

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="c4141-136">Skalieren Sie die Kugel auf x = 0,06, y = 0,06, AD z = 0,06.</span><span class="sxs-lookup"><span data-stu-id="c4141-136">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="c4141-138">Ziehen Sie das "photonuser"-Spielobjekt in den Ordner "Prefabs" im Projekt Panel, und löschen Sie es aus der Szene.</span><span class="sxs-lookup"><span data-stu-id="c4141-138">Drag the PhotonUser game object into the Prefabs folder in the Project panel, and then delete it from the scene.</span></span> <span data-ttu-id="c4141-139">Wir haben nun ein präfab erstellt, das verwendet werden kann, um neue Player in einer gemeinsamen Darstellung zu erstellen oder zu instanziieren.</span><span class="sxs-lookup"><span data-stu-id="c4141-139">We have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="c4141-141">Hinweis: Stellen Sie sicher, dass das Spielobjekt erfolgreich in den Ordner "Prefabs" kopiert wurde, bevor es aus der Hierarchie gelöscht wird.</span><span class="sxs-lookup"><span data-stu-id="c4141-141">Note: ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="c4141-142">Erstellen Sie ein neues-Objekt in der Hierarchie, indem Sie die Anweisungen in Schritt 3 befolgen, und benennen Sie es sharedplayground.</span><span class="sxs-lookup"><span data-stu-id="c4141-142">Create a new object in the hierarchy by following the instructions in Step 3, and name it SharedPlayground.</span></span> <span data-ttu-id="c4141-143">Klicken Sie dann auf Komponente hinzufügen, suchen Sie nach generischem Netzwerk-Manager, und klicken Sie darauf, um die generische Netzwerk-Manager-Komponente hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="c4141-143">Then, click Add Component, and search for generic network manager, and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="c4141-144">Ändern Sie die Position des Objekts in x = 0, y = 0 und z = 0.</span><span class="sxs-lookup"><span data-stu-id="c4141-144">Change the position of the object to x=0, y=0, and z =0.</span></span>

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="c4141-146">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="c4141-146">Congratulations</span></span>

<span data-ttu-id="c4141-147">Nachdem alle oben aufgeführten Schritte ausgeführt wurden und der Buildprozess ebenfalls vollständig ist, klicken Sie auf die Schaltfläche Wiedergabe, und verbinden Sie die hololens 2.</span><span class="sxs-lookup"><span data-stu-id="c4141-147">Once all the steps above are complete, and the build process is also complete, press the play button and connect your HoloLens 2.</span></span> <span data-ttu-id="c4141-148">Wenn Sie Ihre Kopfzeile bewegen, sollte eine Kugel angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c4141-148">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="c4141-149">Dies wird für jeden Benutzer angezeigt, der Ihrem Unity-Projekt Beitritt.</span><span class="sxs-lookup"><span data-stu-id="c4141-149">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="c4141-150">[Nächste Lektion: 4. Freigeben von Objektbewegungen für mehrere Benutzer](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="c4141-150">[Next Lesson: 4. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch4.md)</span></span>

