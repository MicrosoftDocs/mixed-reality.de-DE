---
title: Anzeigen des Status
description: Ein Statussteuerelement gibt dem Benutzer eine Rückmeldung, dass ein Vorgang mit langer Laufzeit ausgeführt wird.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Entwurf, Steuerelemente, Benutzeroberfläche, ux
ms.openlocfilehash: d62d86c690233f351b6c156c66eba33cb2687ea6
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813726"
---
# <a name="displaying-progress"></a><span data-ttu-id="b325f-104">Anzeigen des Status</span><span class="sxs-lookup"><span data-stu-id="b325f-104">Displaying progress</span></span>

<span data-ttu-id="b325f-105">Ein Statussteuerelement gibt dem Benutzer eine Rückmeldung, dass ein Vorgang mit langer Laufzeit ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b325f-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="b325f-106">Dies kann bedeuten, dass der Benutzer bei Anzeigen der Statusanzeige nicht mit der App interagieren kann. Je nach verwendetem Indikator wird auch die Länge der Wartezeit angegeben.</span><span class="sxs-lookup"><span data-stu-id="b325f-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<span data-ttu-id="b325f-107">![Status-Ring-Beispiel in HoloLens](images/HoloLens2_Loader.gif)</span><span class="sxs-lookup"><span data-stu-id="b325f-107">![Progress ring example in HoloLens](images/HoloLens2_Loader.gif)</span></span><br>
<span data-ttu-id="b325f-108">*Status-Ring-Beispiel in HoloLens*</span><span class="sxs-lookup"><span data-stu-id="b325f-108">*Progress ring example in HoloLens*</span></span>

## <a name="types-of-progress"></a><span data-ttu-id="b325f-109">Typen von Statussteuerelementen</span><span class="sxs-lookup"><span data-stu-id="b325f-109">Types of progress</span></span>

<span data-ttu-id="b325f-110">Es ist wichtig, zu dem Benutzerinformationen zu was passiert.</span><span class="sxs-lookup"><span data-stu-id="b325f-110">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="b325f-111">In mixed Reality können Benutzer problemlos von der physischen Umgebung oder Objekte abgelenkt werden, wenn Ihre app nicht die gute visuelles Feedback erhalten.</span><span class="sxs-lookup"><span data-stu-id="b325f-111">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="b325f-112">Für Situationen, in denen einige Sekunden dauern, z. B. beim Laden von Daten oder einer Szene wird aktualisiert, es empfiehlt sich, einen visuellen Indikator anzeigen.</span><span class="sxs-lookup"><span data-stu-id="b325f-112">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="b325f-113">Es gibt zwei Möglichkeiten, die dem Benutzer angezeigt, dass ein Vorgang ausgeführt – wird eine **Statusanzeige** oder **statuskreis**.</span><span class="sxs-lookup"><span data-stu-id="b325f-113">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

### <a name="progress-bar"></a><span data-ttu-id="b325f-114">Statusleiste</span><span class="sxs-lookup"><span data-stu-id="b325f-114">Progress bar</span></span>

![Beispiel für Fortschritt in HoloLens](images/640px-progressbar.jpg)

<span data-ttu-id="b325f-116">Eine Statusanzeige zeigt den Prozentsatz einer Aufgabe abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="b325f-116">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="b325f-117">Er sollte verwendet werden, während eines Vorgangs, deren Dauer (bestimmte) bekannt ist, jedoch seinen Status sollte die Interaktion des Benutzers mit der app nicht blockieren.</span><span class="sxs-lookup"><span data-stu-id="b325f-117">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span>

### <a name="progress-ring"></a><span data-ttu-id="b325f-118">Statusring</span><span class="sxs-lookup"><span data-stu-id="b325f-118">Progress ring</span></span>

![Status-Ring-Beispiel in HoloLens](images/640px-progressring.jpg)

<span data-ttu-id="b325f-120">Ein statuskreis nur einem unbestimmten Zustand befindet, und sollte verwendet werden, wenn weiteren Benutzereingriff blockiert wird, bis der Vorgang abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="b325f-120">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span>

### <a name="progress-with-a-custom-object"></a><span data-ttu-id="b325f-121">Mit der ein benutzerdefiniertes Objekt</span><span class="sxs-lookup"><span data-stu-id="b325f-121">Progress with a custom object</span></span>

![Mit benutzerdefinierten Mesh-Beispiel in HoloLens](images/640px-progresscustom.jpg)

<span data-ttu-id="b325f-123">Sie können zu Ihrer Persönlichkeit und Markenidentität Ihrer app hinzufügen, durch das Anpassen des Statussteuerelements mit Ihren eigenen benutzerdefinierten 2D-/3D-Objekten.</span><span class="sxs-lookup"><span data-stu-id="b325f-123">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span>

## <a name="best-practices"></a><span data-ttu-id="b325f-124">Empfohlene Methoden</span><span class="sxs-lookup"><span data-stu-id="b325f-124">Best practices</span></span>
* <span data-ttu-id="b325f-125">Eng [billboarding oder Tag-along](billboarding-and-tag-along.md) der Anzeige des Status, da der Benutzer kann einfach ihrem Kopf in den leeren Bereich verschieben und Kontext verlieren.</span><span class="sxs-lookup"><span data-stu-id="b325f-125">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="b325f-126">Ihre app möglicherweise sieht es abgestürzt ist, wenn der Benutzer können nicht alles angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b325f-126">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="b325f-127">Billboarding und Tag-along ist in den Status-Prefab integriert.</span><span class="sxs-lookup"><span data-stu-id="b325f-127">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="b325f-128">Es empfiehlt sich immer um Statusinformationen über den Ablauf für den Benutzer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="b325f-128">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="b325f-129">Die Status-Prefab bietet verschiedene visuelle Stile, einschließlich des Status des Windows-Ring-Standardtyp für die Bereitstellung von Status an.</span><span class="sxs-lookup"><span data-stu-id="b325f-129">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="b325f-130">Wenn Sie den Stil der den Fortschritt zu Ihrer app Marke ausrichten möchten, können Sie auch eine benutzerdefinierte Mesh mit einer Animation verwenden.</span><span class="sxs-lookup"><span data-stu-id="b325f-130">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

## <a name="see-also"></a><span data-ttu-id="b325f-131">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b325f-131">See also</span></span>
* [<span data-ttu-id="b325f-132">Status-Skripts und Prefabs in Mixed Reality-Toolkit</span><span class="sxs-lookup"><span data-stu-id="b325f-132">Progress scripts and prefabs on Mixed Reality Toolkit</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Loader)
* [<span data-ttu-id="b325f-133">Umgebendes Feld</span><span class="sxs-lookup"><span data-stu-id="b325f-133">Bounding Box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="b325f-134">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="b325f-134">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="b325f-135">Objektsammlung</span><span class="sxs-lookup"><span data-stu-id="b325f-135">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="b325f-136">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="b325f-136">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
