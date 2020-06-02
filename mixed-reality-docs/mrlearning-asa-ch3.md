---
title: 'Tutorials zu Azure Spatial Anchors: 3 Anzeigen von Azure Spatial Anchors-Feedback'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 62ce1151837a345dea1bea4a8bea275cc851b9bd
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/26/2020
ms.locfileid: "83866900"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="a89c0-105">3. Anzeigen von Azure Spatial Anchors-Feedback</span><span class="sxs-lookup"><span data-stu-id="a89c0-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="a89c0-106">In diesem Tutorial erfahren Sie, wie Sie Feedback zur Ankerermittlung, zu Ereignissen und zum Status bei der Verwendung von Azure Spatial Anchors (ASA) für Benutzer bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="a89c0-106">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="a89c0-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="a89c0-107">Objectives</span></span>

* <span data-ttu-id="a89c0-108">Erlernen des Einrichtens eines Bereichs der Benutzeroberfläche, in dem wichtige Informationen über die aktuelle ASA-Sitzung angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="a89c0-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>
* <span data-ttu-id="a89c0-109">Verstehen und Untersuchen der Feedbackelemente, die Benutzern vom ASA SDK zur Verfügung gestellt werden.</span><span class="sxs-lookup"><span data-stu-id="a89c0-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="a89c0-110">Einrichten des Benutzeroberflächenbereichs für ASA-Feedback</span><span class="sxs-lookup"><span data-stu-id="a89c0-110">Set up ASA feedback UI panel</span></span>

<span data-ttu-id="a89c0-111">Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf das Objekt **Instructions** > **TextContent**, wählen Sie **3D Object** > **Text - TextMeshPro** aus, um ein TextMeshPro-Textobjekt als untergeordnetes Element des Objekts „Instructions > TextContent“ zu erstellen, und geben Sie ihm einen passenden Namen, beispielsweise **Feedback**:</span><span class="sxs-lookup"><span data-stu-id="a89c0-111">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object and give it a suitable name, for example, **Feedback**:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="a89c0-113">Um das Arbeiten mit Ihrer Szene zu erleichtern, legen Sie die <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> (Sichtbarkeit in der Szene) für das ParentAnchor-Objekt auf „Aus“ fest, indem Sie links neben dem Objekt auf das Augensymbol klicken.</span><span class="sxs-lookup"><span data-stu-id="a89c0-113">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="a89c0-114">Dadurch wird das Objekt im Szenenfenster ausgeblendet, ohne seine Sichtbarkeit im Spiel zu ändern.</span><span class="sxs-lookup"><span data-stu-id="a89c0-114">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="a89c0-115">Ändern Sie bei noch ausgewähltem **Feedback**-Objekt im Inspektorfenster seine Position und Größe so, dass es ordentlich unter dem Anweisungstext platziert ist, beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="a89c0-115">With the **Feedback** object still selected, in the Inspector window change its position and size so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="a89c0-116">Ändern Sie die Rect-Transformations-**Pos Y** in -0,24</span><span class="sxs-lookup"><span data-stu-id="a89c0-116">Change the Rect Transform **Pos Y** to -0.24</span></span>
* <span data-ttu-id="a89c0-117">Ändern Sie die Rect-Transformations-**Breite** in 0,555</span><span class="sxs-lookup"><span data-stu-id="a89c0-117">Change the Rect Transform **Width** to 0.555</span></span>
* <span data-ttu-id="a89c0-118">Ändern Sie die Rect-Transformations-**Höhe** in 0,1</span><span class="sxs-lookup"><span data-stu-id="a89c0-118">Change the Rect Transform **Height** to 0.1</span></span>

<span data-ttu-id="a89c0-119">Wählen Sie dann die Schriftarteigenschaften so, dass der Text gut in den Textbereich passt, beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="a89c0-119">Then choose font properties so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="a89c0-120">Ändern Sie den **Schriftschnitt** von „Text Mesh Pro (Script)“ in Fett</span><span class="sxs-lookup"><span data-stu-id="a89c0-120">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="a89c0-121">Ändern Sie den **Schriftgrad** von „Text Mesh Pro (Script)“ in 0,17</span><span class="sxs-lookup"><span data-stu-id="a89c0-121">Change the Text Mesh Pro (Script) **Font Size** to 0.17</span></span>
* <span data-ttu-id="a89c0-122">Ändern Sie die **Ausrichtung** von „Text Mesh Pro (Script)“ in „Zentriert und Mittig“</span><span class="sxs-lookup"><span data-stu-id="a89c0-122">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

<span data-ttu-id="a89c0-124">Verwenden Sie bei noch immer ausgewähltem **Feedback**-Objekt im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um dem Feedback-Objekt die **Anchor-Feedback (Script)** -Komponente hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="a89c0-124">With the **Feedback** object still selected, in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component to the Feedback object:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

<span data-ttu-id="a89c0-126">Weisen Sie das **Feedback**-Objekt selbst dem Feld **Feedbacktext** der **Anchor Feedback Script (Script)** -Komponente zu:</span><span class="sxs-lookup"><span data-stu-id="a89c0-126">Assign the **Feedback** object itself to the **Anchor Feedback Script (Script)** component's **Feedback Text** field:</span></span>

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="a89c0-128">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="a89c0-128">Congratulations</span></span>

<span data-ttu-id="a89c0-129">In diesem Tutorial haben Sie gelernt, wie Sie einen Benutzeroberflächenbereich erstellen, um den aktuellen Status der Azure Spatial Anchor-Benutzererfahrung anzuzeigen, um Echtzeitfeedback für Benutzer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="a89c0-129">In this tutorial, you learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>

[<span data-ttu-id="a89c0-130">Nächste Lektion: 4. Azure Spatial Anchors für Android und iOS</span><span class="sxs-lookup"><span data-stu-id="a89c0-130">Next Lesson: 4. Azure Spatial Anchors for Android and iOS</span></span>](mrlearning-asa-ch4.md)
