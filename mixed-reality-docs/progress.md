---
title: Anzeigen des Fortschritts
description: Ein Statussteuerelement gibt dem Benutzer eine Rückmeldung, dass ein Vorgang mit langer Laufzeit ausgeführt wird.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Design, Steuerelemente, UI, UX
ms.openlocfilehash: 84853a23a73bbece30c1f96b83e586642f3ab762
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523252"
---
# <a name="displaying-progress"></a><span data-ttu-id="47821-104">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="47821-104">Displaying progress</span></span>

<span data-ttu-id="47821-105">Ein Statussteuerelement gibt dem Benutzer eine Rückmeldung, dass ein Vorgang mit langer Laufzeit ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="47821-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="47821-106">Dies kann bedeuten, dass der Benutzer bei Anzeigen der Statusanzeige nicht mit der App interagieren kann. Je nach verwendetem Indikator wird auch die Länge der Wartezeit angegeben.</span><span class="sxs-lookup"><span data-stu-id="47821-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<span data-ttu-id="47821-107">![Beispiel für Fortschritts Ring in hololens](images/HoloLens2_Loader.gif)</span><span class="sxs-lookup"><span data-stu-id="47821-107">![Progress ring example in HoloLens](images/HoloLens2_Loader.gif)</span></span><br>
<span data-ttu-id="47821-108">*Beispiel für Fortschritts Ring in hololens*</span><span class="sxs-lookup"><span data-stu-id="47821-108">*Progress ring example in HoloLens*</span></span>

## <a name="types-of-progress"></a><span data-ttu-id="47821-109">Typen von Statussteuerelementen</span><span class="sxs-lookup"><span data-stu-id="47821-109">Types of progress</span></span>

<span data-ttu-id="47821-110">Es ist wichtig, dass Sie die Benutzerinformationen zu den Vorgängen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="47821-110">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="47821-111">In Mixed Reality können Benutzer problemlos von der physischen Umgebung oder von Objekten abgelenkt werden, wenn Ihre APP kein gutes visuelles Feedback bietet.</span><span class="sxs-lookup"><span data-stu-id="47821-111">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="47821-112">Für Situationen, die einige Sekunden dauern, z. b. beim Laden von Daten oder beim Aktualisieren einer Szene, empfiehlt es sich, einen visuellen Indikator anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="47821-112">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="47821-113">Es gibt zwei Möglichkeiten, den Benutzer anzuzeigen, dass ein Vorgang ausgeführt wird – eine **Status** Anzeige oder ein **Fortschritts Ring**.</span><span class="sxs-lookup"><span data-stu-id="47821-113">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

### <a name="progress-bar"></a><span data-ttu-id="47821-114">Statusanzeige</span><span class="sxs-lookup"><span data-stu-id="47821-114">Progress bar</span></span>

![Beispiel für Statusanzeige in hololens](images/640px-progressbar.jpg)

<span data-ttu-id="47821-116">Eine Statusanzeige zeigt den Prozentsatz der abgeschlossenen Aufgabe an.</span><span class="sxs-lookup"><span data-stu-id="47821-116">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="47821-117">Er sollte bei einem Vorgang verwendet werden, dessen Dauer bekannt ist (determinate), aber der Fortschritt sollte die Interaktion des Benutzers mit der APP nicht blockieren.</span><span class="sxs-lookup"><span data-stu-id="47821-117">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span>

### <a name="progress-ring"></a><span data-ttu-id="47821-118">Statusring</span><span class="sxs-lookup"><span data-stu-id="47821-118">Progress ring</span></span>

![Beispiel für Fortschritts Ring in hololens](images/640px-progressring.jpg)

<span data-ttu-id="47821-120">Ein Fortschritts Ring hat nur einen unbestimmten Status und sollte verwendet werden, wenn eine weitere Benutzerinteraktion blockiert wird, bis der Vorgang abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="47821-120">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span>

### <a name="progress-with-a-custom-object"></a><span data-ttu-id="47821-121">Fortschritt mit einem benutzerdefinierten Objekt</span><span class="sxs-lookup"><span data-stu-id="47821-121">Progress with a custom object</span></span>

![Fortschritt mit einem benutzerdefinierten Mesh-Beispiel in hololens](images/640px-progresscustom.jpg)

<span data-ttu-id="47821-123">Sie können der Identität und Markenidentität Ihrer APP hinzufügen, indem Sie das Status Steuerelement mit ihren eigenen benutzerdefinierten 2D-/3D-Objekten anpassen.</span><span class="sxs-lookup"><span data-stu-id="47821-123">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span>

## <a name="best-practices"></a><span data-ttu-id="47821-124">Empfohlene Methoden</span><span class="sxs-lookup"><span data-stu-id="47821-124">Best practices</span></span>
* <span data-ttu-id="47821-125">Schließen Sie das [Abrechnungs-oder tagboarding](billboarding-and-tag-along.md) eng mit der Anzeige des Fortschritts ab, da der Benutzer problemlos seinen Kopf in einen leeren Bereich verschieben und Kontext verlieren kann.</span><span class="sxs-lookup"><span data-stu-id="47821-125">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="47821-126">Ihre APP könnte so aussehen, als ob Sie abgestürzt ist, wenn der Benutzer nichts sehen kann.</span><span class="sxs-lookup"><span data-stu-id="47821-126">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="47821-127">Das fakboardingboarding und das Tag-Along sind in den Fortschritt vorfab integriert.</span><span class="sxs-lookup"><span data-stu-id="47821-127">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="47821-128">Es ist immer gut, Statusinformationen zu den Ereignissen für den Benutzer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="47821-128">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="47821-129">Die Fortschritts präfab stellt verschiedene visuelle Stile bereit, einschließlich des Windows-standardmäßigen Rings-Typs zum Angeben des Status.</span><span class="sxs-lookup"><span data-stu-id="47821-129">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="47821-130">Sie können auch ein benutzerdefiniertes Mesh mit einer Animation verwenden, wenn Sie möchten, dass der Stil Ihres Fortschritts an der Marke Ihrer APP ausgerichtet wird.</span><span class="sxs-lookup"><span data-stu-id="47821-130">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

## <a name="see-also"></a><span data-ttu-id="47821-131">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="47821-131">See also</span></span>
* [<span data-ttu-id="47821-132">Fortschritts Skripts und Prefabs im Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="47821-132">Progress scripts and prefabs on Mixed Reality Toolkit</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [<span data-ttu-id="47821-133">Begrenzungs Fenster</span><span class="sxs-lookup"><span data-stu-id="47821-133">Bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="47821-134">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="47821-134">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="47821-135">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="47821-135">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="47821-136">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="47821-136">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
