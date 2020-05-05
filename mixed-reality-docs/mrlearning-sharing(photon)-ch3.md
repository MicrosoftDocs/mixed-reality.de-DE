---
title: 'Tutorials zu Mehrbenutzerfunktionen: 4 Freigeben von Objektbewegungen für mehrere Benutzer'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 41b62eb2d9f400d0af341c9fcce887c72af7a3aa
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610629"
---
# <a name="3-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="812c2-105">3. Freigeben von Objektbewegungen für mehrere Benutzer</span><span class="sxs-lookup"><span data-stu-id="812c2-105">3. Sharing object movements with multiple users</span></span>

<span data-ttu-id="812c2-106">In diesem Tutorial erfahren Sie, wie Sie die Bewegungen von Objekten teilen, damit alle Teilnehmer einer geteilten Benutzeroberfläche zusammenarbeiten und die Interaktionen der einzelnen Benutzer anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="812c2-106">In this tutorial, you will learn how to share the movements of objects so that all participants of a shared experience can collaborate and view each others' interactions.</span></span>

## <a name="objectives"></a><span data-ttu-id="812c2-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="812c2-107">Objectives</span></span>

* <span data-ttu-id="812c2-108">Konfigurieren des Projekts zum Teilen der Bewegungen von Objekten</span><span class="sxs-lookup"><span data-stu-id="812c2-108">Configure your project to share the movements of objects</span></span>
* <span data-ttu-id="812c2-109">Erlernen des Erstellens einer einfachen Mehrbenutzeranwendung zur Zusammenarbeit</span><span class="sxs-lookup"><span data-stu-id="812c2-109">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="812c2-110">Vorbereiten der Szene</span><span class="sxs-lookup"><span data-stu-id="812c2-110">Preparing the scene</span></span>

<span data-ttu-id="812c2-111">In diesem Abschnitt bereiten Sie die Szene vor, indem Sie das Tutorial-Prefab hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="812c2-111">In this section, you will prepare the scene by adding the tutorial prefab.</span></span>

<span data-ttu-id="812c2-112">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs**, und ziehen Sie das **TableAnchor**-Prefab auf das **SharedPlayground**-Objekt im Hierarchiefenster, um es Ihrer Szene als untergeordnetes Objekt des SharedPlayground-Objekts hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="812c2-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **TableAnchor** prefab on top of the **SharedPlayground** object in the Hierarchy window to add it to your scene as a child of the SharedPlayground object:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a><span data-ttu-id="812c2-114">Konfigurieren von PUN zum Instanziieren der Objekte</span><span class="sxs-lookup"><span data-stu-id="812c2-114">Configuring PUN to instantiate the objects</span></span>

<span data-ttu-id="812c2-115">In diesem Abschnitt konfigurieren Sie das Projekt für die Verwendung des RocketLauncher_Complete_Variant-Prefabs, das Sie im vorherigen Abschnitt erstellt haben, und definieren, wo es instanziiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="812c2-115">In this section, you will configure the project to use the RocketLauncher_Complete_Variant prefab you created in the previous section and define where it will be instantiated.</span></span>

<span data-ttu-id="812c2-116">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources**.</span><span class="sxs-lookup"><span data-stu-id="812c2-116">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="812c2-117">Klappen Sie im Hierarchiefenster das **NetworkLobby**-Objekt auf, wählen Sie das untergeordnete Objekt **NetworkRoom** aus, und suchen Sie dann im Inspektorfenster die Komponente **Photon Room (Script)** , um sie wie folgt zu konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="812c2-117">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="812c2-118">Weisen Sie das **PhotonUser**-Prefab aus dem Ordner „Resources“ dem **Photon User Prefab**-Feld zu</span><span class="sxs-lookup"><span data-stu-id="812c2-118">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-1.png)

<span data-ttu-id="812c2-120">Klappen Sie im Hierarchiefenster das **TableAnchor**-Objekt auf, während das untergeordnete Objekt **NetworkRoom** noch ausgewählt ist, und suchen Sie dann im Inspektorfenster die Komponente **Photon Room (Script)** , um sie wie folgt zu konfigurieren:</span><span class="sxs-lookup"><span data-stu-id="812c2-120">With the **NetworkRoom** child object still selected, in the Hierarchy window, expand the **TableAnchor** object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="812c2-121">Weisen Sie das untergeordnete Objekt **Table** aus dem Hierarchiefenster dem **Rocket Launcher Location**-Feld zu</span><span class="sxs-lookup"><span data-stu-id="812c2-121">To the **Rocket Launcher Location** field, assign the **Table** child object from the Hierarchy window</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a><span data-ttu-id="812c2-123">Ausprobieren der Benutzeroberfläche mit geteilter Objektbewegung</span><span class="sxs-lookup"><span data-stu-id="812c2-123">Trying the experience with shared object movement</span></span>

<span data-ttu-id="812c2-124">Wenn Sie das Unity-Projekt jetzt für Ihre HoloLens erstellen und bereitstellen und anschließend, wieder in Unity, auf die Schaltfläche „Wiedergabe“ drücken, um in den Spielmodus zu wechseln, während die Anwendung auf Ihrer HoloLens ausgeführt wird, sehen Sie, wie sich das Objekt in Unity bewegt, wenn Sie es in HoloLens bewegen:</span><span class="sxs-lookup"><span data-stu-id="812c2-124">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the application is running on your HoloLens, you will see the object move in Unity when you move the object in HoloLens:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section3-step1-1.gif)

## <a name="congratulations"></a><span data-ttu-id="812c2-126">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="812c2-126">Congratulations</span></span>

<span data-ttu-id="812c2-127">Sie haben Ihr Projekt erfolgreich so konfiguriert, dass Objektbewegungen synchronisiert werden und Benutzer die Objektbewegungen sehen können, wenn andere Benutzer die Objekte bewegen.</span><span class="sxs-lookup"><span data-stu-id="812c2-127">You have successfully configured your project so object movements are synchronized and users can see the objects move when other users move the objects.</span></span> <span data-ttu-id="812c2-128">Im nächsten Tutorial implementieren Sie Funktionen zur Ausrichtung der gemeinsamen Benutzeroberfläche an der physischen Welt, damit sich die Benutzer gegenseitig an ihren realen physischen Standorten sehen können und Objekte für alle Benutzer an der gleichen physischen Position und mit der gleichen Drehung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="812c2-128">In the next tutorial, you will implement functionality so the shared experience is aligned in the physical world and the users see each other in their actual physical location and so the objects appear in the same physical position and rotation for all users.</span></span>

<span data-ttu-id="812c2-129">[Nächstes Tutorial: 4. Integrieren von Azure Spatial Anchors in eine gemeinsam genutzte Umgebung](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="812c2-129">[Next tutorial: 4. Integrating Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch4.md)</span></span>
