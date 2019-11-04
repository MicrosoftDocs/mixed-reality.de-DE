---
title: Anzeigen des Fortschritts
description: Ein Statussteuerelement gibt dem Benutzer eine Rückmeldung, dass ein Vorgang mit langer Laufzeit ausgeführt wird.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Design, Steuerelemente, UI, UX
ms.openlocfilehash: 43b4802e7c821c98c847509ace950f381da12f95
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437539"
---
# <a name="displaying-progress"></a><span data-ttu-id="26d0d-104">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="26d0d-104">Displaying progress</span></span>

<br>

<img src="images/HoloLens2_Loader.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="26d0d-105">Ein Statussteuerelement gibt dem Benutzer eine Rückmeldung, dass ein Vorgang mit langer Laufzeit ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="26d0d-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="26d0d-106">Dies kann bedeuten, dass der Benutzer bei Anzeigen der Statusanzeige nicht mit der App interagieren kann. Je nach verwendetem Indikator wird auch die Länge der Wartezeit angegeben.</span><span class="sxs-lookup"><span data-stu-id="26d0d-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="26d0d-107">Typen von Statussteuerelementen</span><span class="sxs-lookup"><span data-stu-id="26d0d-107">Types of progress</span></span>

<span data-ttu-id="26d0d-108">Es ist wichtig, dass Sie die Benutzerinformationen zu den Vorgängen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="26d0d-108">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="26d0d-109">In Mixed Reality können Benutzer problemlos von der physischen Umgebung oder von Objekten abgelenkt werden, wenn Ihre APP kein gutes visuelles Feedback bietet.</span><span class="sxs-lookup"><span data-stu-id="26d0d-109">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="26d0d-110">Für Situationen, die einige Sekunden dauern, z. b. beim Laden von Daten oder beim Aktualisieren einer Szene, empfiehlt es sich, einen visuellen Indikator anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="26d0d-110">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="26d0d-111">Es gibt zwei Möglichkeiten, den Benutzer anzuzeigen, dass ein Vorgang ausgeführt wird – eine **Status** Anzeige oder ein **Fortschritts Ring**.</span><span class="sxs-lookup"><span data-stu-id="26d0d-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="26d0d-112">Statusleiste</span><span class="sxs-lookup"><span data-stu-id="26d0d-112">Progress bar</span></span><br>
        <span data-ttu-id="26d0d-113">Eine Statusanzeige zeigt den Prozentsatz der abgeschlossenen Aufgabe an.</span><span class="sxs-lookup"><span data-stu-id="26d0d-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="26d0d-114">Er sollte bei einem Vorgang verwendet werden, dessen Dauer bekannt ist (determinate), aber der Fortschritt sollte die Interaktion des Benutzers mit der APP nicht blockieren.</span><span class="sxs-lookup"><span data-stu-id="26d0d-114">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="26d0d-115">*Bild: Statusanzeige Beispiel in hololens*</span><span class="sxs-lookup"><span data-stu-id="26d0d-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="26d0d-116">![Speicher](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="26d0d-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="26d0d-117">![Statusanzeige Beispiel in hololens](images/640px-progressbar.jpg)</span><span class="sxs-lookup"><span data-stu-id="26d0d-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="26d0d-118">Statusring</span><span class="sxs-lookup"><span data-stu-id="26d0d-118">Progress ring</span></span><br>
        <span data-ttu-id="26d0d-119">Ein Fortschritts Ring hat nur einen unbestimmten Status und sollte verwendet werden, wenn eine weitere Benutzerinteraktion blockiert wird, bis der Vorgang abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="26d0d-119">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="26d0d-120">*Image: Fortschritts Ring-Beispiel in hololens*</span><span class="sxs-lookup"><span data-stu-id="26d0d-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="26d0d-121">![Speicher](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="26d0d-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="26d0d-122">![Status Ring-Beispiel in hololens](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="26d0d-122">![Progress ring example in HoloLens](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="26d0d-123">Fortschritt mit einem benutzerdefinierten Objekt</span><span class="sxs-lookup"><span data-stu-id="26d0d-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="26d0d-124">Sie können der Identität und Markenidentität Ihrer APP hinzufügen, indem Sie das Status Steuerelement mit ihren eigenen benutzerdefinierten 2D-/3D-Objekten anpassen.</span><span class="sxs-lookup"><span data-stu-id="26d0d-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="26d0d-125">*Bild: Fortschritt mit einem benutzerdefinierten Mesh-Beispiel in hololens*</span><span class="sxs-lookup"><span data-stu-id="26d0d-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="26d0d-126">![Speicher](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="26d0d-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="26d0d-127">![Fortschritt mit einem benutzerdefinierten Mesh-Beispiel in hololens](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="26d0d-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="26d0d-128">Bewährte Verfahren</span><span class="sxs-lookup"><span data-stu-id="26d0d-128">Best practices</span></span>
* <span data-ttu-id="26d0d-129">Schließen Sie das [Abrechnungs-oder tagboarding](billboarding-and-tag-along.md) eng mit der Anzeige des Fortschritts ab, da der Benutzer problemlos seinen Kopf in einen leeren Bereich verschieben und Kontext verlieren kann.</span><span class="sxs-lookup"><span data-stu-id="26d0d-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="26d0d-130">Ihre APP könnte so aussehen, als ob Sie abgestürzt ist, wenn der Benutzer nichts sehen kann.</span><span class="sxs-lookup"><span data-stu-id="26d0d-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="26d0d-131">Das fakboardingboarding und das Tag-Along sind in den Fortschritt vorfab integriert.</span><span class="sxs-lookup"><span data-stu-id="26d0d-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="26d0d-132">Es ist immer gut, Statusinformationen zu den Ereignissen für den Benutzer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="26d0d-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="26d0d-133">Die Fortschritts präfab stellt verschiedene visuelle Stile bereit, einschließlich des Windows-standardmäßigen Rings-Typs zum Angeben des Status.</span><span class="sxs-lookup"><span data-stu-id="26d0d-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="26d0d-134">Sie können auch ein benutzerdefiniertes Mesh mit einer Animation verwenden, wenn Sie möchten, dass der Stil Ihres Fortschritts an der Marke Ihrer APP ausgerichtet wird.</span><span class="sxs-lookup"><span data-stu-id="26d0d-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="26d0d-135">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="26d0d-135">See also</span></span>
* [<span data-ttu-id="26d0d-136">Fortschritts Skripts und Prefabs im Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="26d0d-136">Progress scripts and prefabs on Mixed Reality Toolkit</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [<span data-ttu-id="26d0d-137">Begrenzungs Fenster</span><span class="sxs-lookup"><span data-stu-id="26d0d-137">Bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="26d0d-138">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="26d0d-138">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="26d0d-139">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="26d0d-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="26d0d-140">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="26d0d-140">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
