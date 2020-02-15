---
title: Tutorials zu Azure Spatial Anchor-3. Anzeigen des Azure Spatial Anchor-Feedbacks
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: f4f609a71b05a52e8761e282763a540b42e9f7f5
ms.sourcegitcommit: a580166a19294f835b8e09c780f663f228dd5de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2020
ms.locfileid: "77250691"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a><span data-ttu-id="249c7-105">3. Anzeigen des Azure Spatial Anchor-Feedbacks</span><span class="sxs-lookup"><span data-stu-id="249c7-105">3. Displaying Azure Spatial Anchor feedback</span></span>

<span data-ttu-id="249c7-106">In diesem Tutorial erfahren Sie, wie Sie Benutzern Feedback zur Anker Ermittlung, zu Ereignissen und zum Status bei der Verwendung von Azure Spatial Anchor (ASA) bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="249c7-106">In this tutorial, you will learn how to provide users with feedback about anchor discovery, events, and status when using Azure Spatial Anchors (ASA).</span></span>

## <a name="objectives"></a><span data-ttu-id="249c7-107">Ziele</span><span class="sxs-lookup"><span data-stu-id="249c7-107">Objectives</span></span>

* <span data-ttu-id="249c7-108">Erfahren Sie, wie Sie einen Benutzeroberflächen Bereich einrichten, in dem wichtige Informationen zur aktuellen ASA-Sitzung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="249c7-108">Learn how to set up a UI panel that displays important information about the current ASA session</span></span>
* <span data-ttu-id="249c7-109">Verstehen und untersuchen Sie Feedback Elemente, die das ASA SDK Benutzern zur Verfügung stellt.</span><span class="sxs-lookup"><span data-stu-id="249c7-109">Understand and explore feedback elements that the ASA SDK makes available to users</span></span>

## <a name="set-up-asa-feedback-ui-panel"></a><span data-ttu-id="249c7-110">Einrichten des ASA-Feedback-UI-Panels</span><span class="sxs-lookup"><span data-stu-id="249c7-110">Set up ASA feedback UI panel</span></span>

<span data-ttu-id="249c7-111">Klicken Sie im Hierarchie Fenster mit der rechten Maustaste auf die **Anweisungen** > **textcontent** -Objekt, und wählen Sie **3D-Objekt** > **Text-textmeschpro** aus, um ein textmeshpro-Textobjekt als untergeordnetes Element der Anweisungen > textcontent-Objekt zu erstellen und ihm einen passenden Namen zuzuweisen, z. b. **Feedback**:</span><span class="sxs-lookup"><span data-stu-id="249c7-111">In the Hierarchy window, right-click on the **Instructions** > **TextContent** object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro text object as a child of the Instructions > TextContent object and give it a suitable name, for example, **Feedback**:</span></span>

![mrlearning: Basis](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="249c7-113">Um die Arbeit mit der Szene zu vereinfachen, legen Sie die <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Sichtbarkeit der Szene</a> für das Objekt "Objektanker" auf OFF fest, indem Sie auf das Augensymbol links neben dem Objekt klicken.</span><span class="sxs-lookup"><span data-stu-id="249c7-113">To make it easier to work with your scene, set the  <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> for the ParentAnchor object to off by clicking the eye icon to the left of the object.</span></span> <span data-ttu-id="249c7-114">Dadurch wird das Objekt im Szenen Fenster ausgeblendet, ohne die in-Game-Sichtbarkeit zu ändern.</span><span class="sxs-lookup"><span data-stu-id="249c7-114">This hides the object in the Scene window without changing their in-game visibility.</span></span>

<span data-ttu-id="249c7-115">Wenn das **Feedback** Objekt noch ausgewählt ist, ändern Sie im Inspektor-Fenster seine Position und Größe so, dass es sich unter dem Anweisungs Text befindet, z. b.:</span><span class="sxs-lookup"><span data-stu-id="249c7-115">With the **Feedback** object still selected, in the Inspector window change its position and size so it is placed neatly underneath the instruction text, for example:</span></span>

* <span data-ttu-id="249c7-116">Ändern der Rect-Transformation **Torys Y** in-0,24</span><span class="sxs-lookup"><span data-stu-id="249c7-116">Change the Rect Transform **Pos Y** to -0.24</span></span>
* <span data-ttu-id="249c7-117">Ändern Sie die **Breite** der Rect-Transformation in 0,555.</span><span class="sxs-lookup"><span data-stu-id="249c7-117">Change the Rect Transform **Width** to 0.555</span></span>
* <span data-ttu-id="249c7-118">Ändern Sie die **Höhe** der Rect-Transformation in 0,1.</span><span class="sxs-lookup"><span data-stu-id="249c7-118">Change the Rect Transform **Height** to 0.1</span></span>

<span data-ttu-id="249c7-119">Wählen Sie dann Schriftart Eigenschaften aus, damit der Text gut in den Textbereich passt, z. b.:</span><span class="sxs-lookup"><span data-stu-id="249c7-119">Then choose font properties so the text fits nicely within the text area, for example:</span></span>

* <span data-ttu-id="249c7-120">Ändern Sie den Text Mesh pro- **Schrift** Schnitt (Skript) in "Fett".</span><span class="sxs-lookup"><span data-stu-id="249c7-120">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="249c7-121">Ändern Sie den **Schrift** Grad Text Mesh pro (Skript) in 0,17.</span><span class="sxs-lookup"><span data-stu-id="249c7-121">Change the Text Mesh Pro (Script) **Font Size** to 0.17</span></span>
* <span data-ttu-id="249c7-122">Ändern der **Ausrichtung** von Text Mesh pro (Skript) in Mitte und Mitte</span><span class="sxs-lookup"><span data-stu-id="249c7-122">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning: Basis](images/mrlearning-asa/tutorial3-section1-step1-2.png)

<span data-ttu-id="249c7-124">Wenn das **Feedback** Objekt noch ausgewählt ist, verwenden Sie im Inspektor-Fenster die Schaltfläche **Komponente hinzufügen** , um dem Feedback Objekt die Komponente für das **Anchor-Feedback Skript (Skript)** hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="249c7-124">With the **Feedback** object still selected, in the Inspector window, use the **Add Component** button to add the **Anchor Feedback Script (Script)** component to the Feedback object:</span></span>

![mrlearning: Basis](images/mrlearning-asa/tutorial3-section1-step1-3.png)

<span data-ttu-id="249c7-126">Weisen Sie das **Feedback** Objekt dem **Feedback Textfeld** für das **Anchor-Feedback Skript (Skript)** zu:</span><span class="sxs-lookup"><span data-stu-id="249c7-126">Assign the **Feedback** object to the **Anchor Feedback Script (Script)** component's **Feedback Text** field:</span></span>

![mrlearning: Basis](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="249c7-128">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="249c7-128">Congratulations</span></span>

<span data-ttu-id="249c7-129">In diesem Tutorial haben Sie gelernt, wie Sie einen Bereich für die Benutzeroberfläche erstellen, um den aktuellen Status der Azure Spatial Anchor-Oberfläche zum Bereitstellen von Echtzeitfeedback anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="249c7-129">In this tutorial, you learned how to create a UI panel to display the current status of the Azure Spatial Anchor experience for providing users with real-time feedback.</span></span>
