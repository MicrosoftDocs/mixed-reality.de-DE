---
title: 'Tutorials zu Azure Spatial Anchors: 4 Anzeigen von Azure Spatial Anchors-Feedback'
description: In diesem Kurs erfahren Sie, wie Sie Azure Spatial Anchors in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: d221a7e64bda7a6dabf76b60c7bff7c6333666ef
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304955"
---
# <a name="4-displaying-feedback-from-azure-spatial-anchors"></a><span data-ttu-id="955e5-105">4. Anzeigen des Feedbacks von Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="955e5-105">4. Displaying feedback from Azure Spatial Anchors</span></span>

<span data-ttu-id="955e5-106">In diesem Tutorial erfahren Sie, wie Sie Feedback zur Ankerermittlung, zu Ereignissen und zum Status bei der Verwendung von Azure Spatial Anchors (ASA) für Benutzer bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="955e5-106">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="955e5-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="955e5-107">Objectives</span></span>

* <span data-ttu-id="955e5-108">Erlernen des Einrichtens eines Bereichs der Benutzeroberfläche, in dem grundlegende Informationen über die aktuelle ASA-Sitzung angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="955e5-108">Learn how to set up a UI panel that displays essential information about the current ASA session</span></span>
* <span data-ttu-id="955e5-109">Kennenlernen und Untersuchen der Feedbackelemente, die Benutzern vom ASA SDK zur Verfügung gestellt werden</span><span class="sxs-lookup"><span data-stu-id="955e5-109">learn about and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="setting-up-asa-feedback-panel"></a><span data-ttu-id="955e5-110">Einrichten des ASA-Feedbackbereichs</span><span class="sxs-lookup"><span data-stu-id="955e5-110">Setting up ASA feedback panel</span></span>

<span data-ttu-id="955e5-111">Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf das Objekt **Instructions** > **TextContent**.</span><span class="sxs-lookup"><span data-stu-id="955e5-111">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object.</span></span> <span data-ttu-id="955e5-112">Wählen Sie **3D Object** > **Text - TextMeshPro** (3D-Objekt > Text – TextMeshPro) aus, um ein Textobjekt von TextMeshPro als untergeordnetes Element des Objekts „Instructions > TextContent“ zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="955e5-112">Select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="955e5-114">Um das Arbeiten mit Ihrer Szene zu erleichtern, legen Sie die <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> (Sichtbarkeit in der Szene) für das ParentAnchor-Objekt auf „Aus“ fest, indem Sie links neben dem Objekt auf das Augensymbol klicken.</span><span class="sxs-lookup"><span data-stu-id="955e5-114">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="955e5-115">Dadurch wird das Objekt im Szenenfenster ausgeblendet, ohne seine Sichtbarkeit im Spiel zu ändern.</span><span class="sxs-lookup"><span data-stu-id="955e5-115">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="955e5-116">Benennen Sie das neu erstellte Textobjekt (TMP) **Feedback**, und ändern Sie dann im Inspektorfenster seine Position und Größe so, dass es ordentlich unter dem Anweisungstext platziert ist, beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="955e5-116">Rename the newly created Text (TMP) object **Feedback**, then, in the Inspector window, change its position and size, so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="955e5-117">Ändern Sie die **Pos Y** (Y-Position) der Rect Transform-Komponente in -0,24.</span><span class="sxs-lookup"><span data-stu-id="955e5-117">Change the Rect Transform component's **Pos Y** to -0.24.</span></span>
* <span data-ttu-id="955e5-118">Ändern Sie die **Width** (Breite) der Rect Transform-Komponente in 0,555.</span><span class="sxs-lookup"><span data-stu-id="955e5-118">Change the Rect Transform component's **Width** to 0.555.</span></span>
* <span data-ttu-id="955e5-119">Ändern Sie die **Height** (Höhe) der Rect Transform-Komponente in 0,1.</span><span class="sxs-lookup"><span data-stu-id="955e5-119">Change the Rect Transform component's **Height** to 0.1.</span></span>

<span data-ttu-id="955e5-120">Wählen Sie dann die Schriftarteigenschaften so, dass der Text gut in den Textbereich passt, beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="955e5-120">Then choose font properties, so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="955e5-121">Ändern Sie den **Font Style** (Schriftschnitt) der TextMeshPro – Text-Komponente in Fett.</span><span class="sxs-lookup"><span data-stu-id="955e5-121">Change the TextMeshPro - Text component's **Font Style** to Bold.</span></span>
* <span data-ttu-id="955e5-122">Ändern Sie die **Font Size** (Schriftgrad) der TextMeshPro – Text-Komponente in 0,17.</span><span class="sxs-lookup"><span data-stu-id="955e5-122">Change the TextMeshPro - Text component's **Font Size** to 0.17.</span></span>
* <span data-ttu-id="955e5-123">Ändern Sie das **Alignment** (Ausrichtung) der TextMeshPro – Text-Komponente in „Zentriert“ und „Mitte“.</span><span class="sxs-lookup"><span data-stu-id="955e5-123">Change the TextMeshPro - Text component's **Alignment** to Center and Middle.</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-2.png)

<span data-ttu-id="955e5-125">Wählen Sie im Hierarchiefenster das **Feedback**-Objekt aus, verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um die Komponente **Anchor Feedback Script (Script)** hinzuzufügen, und konfigurieren Sie sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="955e5-125">In the Hierarchy window, select the **Feedback** object still, then in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="955e5-126">Weisen Sie das **Feedback**-Objekt selbst dem Feld **Feedbacktext** der **Anchor Feedback Script (Script)** -Komponente zu.</span><span class="sxs-lookup"><span data-stu-id="955e5-126">Assign the **Feedback** object itself to the **Anchor Feedback Script (Script)** component's **Feedback Text** field.</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="955e5-128">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="955e5-128">Congratulations</span></span>

<span data-ttu-id="955e5-129">In diesem Tutorial haben Sie gelernt, wie Sie einen Benutzeroberflächenbereich erstellen.</span><span class="sxs-lookup"><span data-stu-id="955e5-129">In this tutorial, you learned how to create a UI panel.</span></span> <span data-ttu-id="955e5-130">Er zeigt den aktuellen Status der Azure Spatial Anchor-Erfahrung an, um Benutzern Feedback in Echtzeit zu geben.</span><span class="sxs-lookup"><span data-stu-id="955e5-130">It displays the current status of the Azure Spatial Anchors experience for providing users with real-time feedback.</span></span>

[<span data-ttu-id="955e5-131">Nächstes Tutorial: 5. Azure Spatial Anchors für Android und iOS</span><span class="sxs-lookup"><span data-stu-id="955e5-131">Next Tutorial: 5. Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)
