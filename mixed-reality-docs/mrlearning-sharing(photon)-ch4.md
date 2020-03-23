---
title: 'Tutorials zu Mehrbenutzerfunktionen: 4 Freigeben von Objektbewegungen für mehrere Benutzer'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: b0ddf0799fd94c29ce8f1221c55073cd77b63703
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031246"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="713e2-105">4. Freigeben von Objektbewegungen für mehrere Benutzer</span><span class="sxs-lookup"><span data-stu-id="713e2-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="713e2-106">In diesem Tutorial erfahren Sie, wie Sie die Bewegungen von Objekten teilen, damit alle Teilnehmer einer freigegebenen Sitzung zusammenarbeiten und die Interaktionen der einzelnen Benutzer anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="713e2-106">In this Tutorial, you'll learn how to share the movements of objects so that all participants of a shared session can collaborate and view each others' interactions.</span></span> <span data-ttu-id="713e2-107">Diese Lektion baut auf der Mondstartbasis auf, die im Rahmen der [Basismodul-Tutorials](mrlearning-base.md) erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="713e2-107">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

## <a name="objectives"></a><span data-ttu-id="713e2-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="713e2-108">Objectives</span></span>

- <span data-ttu-id="713e2-109">Einbringen der Mondstartbasis als zu teilendes 3D-Modell</span><span class="sxs-lookup"><span data-stu-id="713e2-109">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="713e2-110">Konfigurieren des Projekts zum Teilen der Bewegungen des 3D-Modells</span><span class="sxs-lookup"><span data-stu-id="713e2-110">Configure your project to share the movements of the 3D model</span></span>
- <span data-ttu-id="713e2-111">Erlernen des Erstellens einer einfachen Mehrbenutzeranwendung zur Zusammenarbeit</span><span class="sxs-lookup"><span data-stu-id="713e2-111">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="instructions"></a><span data-ttu-id="713e2-112">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="713e2-112">Instructions</span></span>

1. <span data-ttu-id="713e2-113">Speichern Sie die Szene aus der vorherigen Lektion (STRG+S).</span><span class="sxs-lookup"><span data-stu-id="713e2-113">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="713e2-114">Sie können sie HLSharedProjectMainPart4.unity benennen, damit sie leichter zu finden ist, wenn Sie sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="713e2-114">You can name it HLSharedProjectMainPart4.unity so it's easier to find when you need it.</span></span>

2. <span data-ttu-id="713e2-115">Doppelklicken Sie im Projektfenster im Ordner „Assets > Scripts“ (Ressourcen > Skripts) auf „GenericNetSync“, um es in Visual Studio oder einem beliebigen anderen Editor, den Sie verwenden, zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="713e2-115">From the Project window, in the Assets->Scripts folder, double-click GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="713e2-117">Entfernen Sie in den Zeilen 34 und 38 "//", um den Code für die Tabelle zu aktivieren, die Sie in dieser Lektion verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="713e2-117">On Lines 34 and 38, remove "//" to activate the code for the table that you will use in this lesson.</span></span> <span data-ttu-id="713e2-118">Speichern Sie dann die Datei.</span><span class="sxs-lookup"><span data-stu-id="713e2-118">Next, save the file.</span></span>

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="713e2-120">Doppelklicken Sie im Projektfenster im Ordner „Assets > Scripts“ auf die Datei „PhotonRoom.cs“, um sie in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="713e2-120">In the Project window, double-click the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span>

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="713e2-122">Wie schon in Schritt 3 müssen wir "//" entfernen, um den Code in den Zeilen 25, 26 und 106 zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="713e2-122">Just like in Step 3, we need to remove "//" to activate the code at Lines 25, 26, and 106.</span></span>

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="713e2-125">Wählen Sie in der Hierarchieansicht das NetworkRoom-Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="713e2-125">In the Hierarchy view, select the NetworkRoom object.</span></span>

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="713e2-127">Navigieren Sie in der Projektansicht zu „Assets > Resources > Prefabs“.</span><span class="sxs-lookup"><span data-stu-id="713e2-127">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="713e2-128">Ziehen Sie das Table-Prefab auf den Tableprefab-Slot der PhotonRoom-Klasse.</span><span class="sxs-lookup"><span data-stu-id="713e2-128">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="713e2-129">Ziehen Sie als nächstes das RocketLauncherCompleteVariantprefab auf den Slot „Module Prefab“ der PhotonRoom-Klasse.</span><span class="sxs-lookup"><span data-stu-id="713e2-129">Next, drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    ><span data-ttu-id="713e2-131">Wenn Sie auf eins der Prefab-Objekte klicken und die Maustaste loslassen, wechselt der Inspektor zu dem betreffenden Objekt.</span><span class="sxs-lookup"><span data-stu-id="713e2-131">If you click one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="713e2-132">Legen Sie jedes Objekt durch Klicken, Ziehen, Ablegen und Freigeben auf seinem passenden Slot ab.</span><span class="sxs-lookup"><span data-stu-id="713e2-132">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="713e2-133">Klicken Sie auf den Pfeil links neben MixedRealityPlayspace, und verschieben Sie das untergeordnete Spielobjekt MainCamera nach unten auf das SharedPlayground-Prefab.</span><span class="sxs-lookup"><span data-stu-id="713e2-133">Click the arrow to the left of MixedRealityPlayspace and move the child game object MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="713e2-134">Löschen Sie anschließend das MixedRealityPlayspace-Prefab, indem Sie das Prefab auswählen und auf der Tastatur ENTF drücken.</span><span class="sxs-lookup"><span data-stu-id="713e2-134">Next, delete the prefab, MixedRealityPlayspace by selecting the prefab and tap "delete" on your keyboard).</span></span>

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    ><span data-ttu-id="713e2-136">Vergewissern Sie sich, dass die Positionen von „Main Camera“ ebenso wie von „SharedPlayground“ auf 0,0,0 festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="713e2-136">Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="713e2-137">Wählen Sie das SharedPlayground-Objekt aus, und klicken Sie mit der rechten Maustaste, um die Option „create empty“ (Leer erstellen) auszuwählen, um ein leeres Spielobjekt als untergeordnetes Objekt des Spielobjekts „SharedPlayground“ zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="713e2-137">Select "SharedPlayground" object and right click the mouse to choose "create empty" option to create an empty game object as a child of "SharedPlayground" game object.</span></span>

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. <span data-ttu-id="713e2-139">Ändern Sie bei in der Hierarchie ausgewähltem neuem Objekt den Namen des Objekts im Inspektorbereich in „TableAnchor“.</span><span class="sxs-lookup"><span data-stu-id="713e2-139">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="713e2-140">Klicken Sie außerdem auf „Komponente hinzufügen“, und suchen Sie nach der TableAnchor-Komponente.</span><span class="sxs-lookup"><span data-stu-id="713e2-140">Also, click Add Component and search for the TableAnchor component.</span></span> <span data-ttu-id="713e2-141">Wählen Sie sie aus, und fügen Sie sie dem-Objekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="713e2-141">Select it and add it to the object.</span></span>

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="713e2-143">Ziehen Sie aus dem Projektbereich im Prefabs-Ordner das Table-Prefab auf das untergeordnete „TableAnchor“-Objekt, das Sie soeben erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="713e2-143">From the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object that you just created.</span></span>

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

## <a name="congratulations"></a><span data-ttu-id="713e2-145">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="713e2-145">Congratulations</span></span>

<span data-ttu-id="713e2-146">Sobald dies erledigt ist, sehen Sie sich um, um das Mondmodul zu finden.</span><span class="sxs-lookup"><span data-stu-id="713e2-146">Once this is complete, look around to find the lunar module.</span></span> <span data-ttu-id="713e2-147">Anschließend können alle Benutzer, die Ihrem Unity-Projekt beitreten, die Mondstartbasis bewegen.</span><span class="sxs-lookup"><span data-stu-id="713e2-147">After this, all users that join your Unity project can move the lunar launcher around.</span></span>  <span data-ttu-id="713e2-148">Alle Bewegungen werden synchronisiert, sodass jeder Benutzer die Interaktionen der anderen Benutzer sehen kann.</span><span class="sxs-lookup"><span data-stu-id="713e2-148">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="713e2-149">Diese Konzepte dienen als Grundbausteine für voll ausgestattete, gemeinsam genutzte Umgebungen zur Zusammenarbeit.</span><span class="sxs-lookup"><span data-stu-id="713e2-149">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span>

<span data-ttu-id="713e2-150">Obwohl alle Benutzer als Teil einer geteilten Umgebung verbunden sind und die relativen Bewegungen von Objekten sehen können, fehlt der Anwendung noch die Möglichkeit, Avatare und Objekte genau auszurichten, sodass lokale Benutzer nicht in der Lage sind, einander und Objekte am gleichen Ort in der physischen Welt zu sehen.</span><span class="sxs-lookup"><span data-stu-id="713e2-150">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users were not able see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="713e2-151">Um ein lokales gemeinsames Benutzererlebnis zu verankern, benötigt jedes Gerät ein gemeinsames Verständnis der physischen Umgebung.</span><span class="sxs-lookup"><span data-stu-id="713e2-151">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="713e2-152">In diesem Modul erreichen wir dies mithilfe von [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA), die in der nächsten Lektion implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="713e2-152">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) which will be implemented in the next lesson.</span></span>

<span data-ttu-id="713e2-153">Bevor Sie mit der nächsten Lektion fortfahren, müssen wir das ASA-Lernmodul abschließen, das die ASA-Grundlagen, die Erstellung von Azure-Konten und Ressourcen sowie weitere Grundbausteine behandelt, die für die Integration in unserer geteilten Benutzerumgebung erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="713e2-153">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, as well as other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="713e2-154">[Nächste Lektion: 5. Integrieren von Azure Spatial Anchors in eine gemeinsam genutzte Umgebung](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="713e2-154">[Next Lesson: 5. Integration Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch5.md)</span></span>
