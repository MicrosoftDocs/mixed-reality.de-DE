---
title: Fallstudie-3 holostudio UI und Interaktionen Design Erkenntnisse
description: Entwicklungs-und Interaktions Entwurfs Lernelemente von holostudio
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: Hololens, holostudio, gemischte Windows-Realität
ms.openlocfilehash: e01e2ea888398e9982b56fd95f90ef0731ec6bc2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974830"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a><span data-ttu-id="bbe80-104">Fallstudie-3 holostudio UI und Interaktionen Design Erkenntnisse</span><span class="sxs-lookup"><span data-stu-id="bbe80-104">Case study - 3 HoloStudio UI and interaction design learnings</span></span>

<span data-ttu-id="bbe80-105">[Holostudio](https://www.youtube.com/watch?v=BRIJG0x_We8) war eine der ersten Microsoft-Apps für hololens.</span><span class="sxs-lookup"><span data-stu-id="bbe80-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) was one of the first Microsoft apps for HoloLens.</span></span> <span data-ttu-id="bbe80-106">Aus diesem Grund mussten wir neue bewährte Methoden für die 3D-Benutzeroberfläche und den Interaktions Entwurf erstellen.</span><span class="sxs-lookup"><span data-stu-id="bbe80-106">Because of this, we had to create new best practices for 3D UI and interaction design.</span></span> <span data-ttu-id="bbe80-107">Wir haben dies durch eine Vielzahl von Benutzer Tests, Prototypen und Test-und Fehler Tests durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="bbe80-107">We did this through a lot of user testing, prototyping, and trial and error.</span></span>

<span data-ttu-id="bbe80-108">Wir wissen, dass nicht jeder Benutzer über die zur Verfügung stehenden Ressourcen verfügt, um diese Art von Untersuchungen durchzuführen. daher hatten wir unseren SR. Holographic Designer, Marcus Ghaly, drei Dinge, die wir bei der Entwicklung von holostudio kennengelernt haben, über UI-und Interaktions Entwürfe für hololens-apps.</span><span class="sxs-lookup"><span data-stu-id="bbe80-108">We know that not everyone has the resources at their disposal to do this type of research, so we had our Sr. Holographic Designer, Marcus Ghaly, share three things we learned during the development of HoloStudio about UI and interaction design for HoloLens apps.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="bbe80-109">Video ansehen</span><span class="sxs-lookup"><span data-stu-id="bbe80-109">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a><span data-ttu-id="bbe80-110">Problem #1: Personen wollten sich nicht um ihre Schöpfungen bewegen.</span><span class="sxs-lookup"><span data-stu-id="bbe80-110">Problem #1: People didn't want to move around their creations</span></span>

<span data-ttu-id="bbe80-111">Wir haben die Workbench ursprünglich in holostudio als Rechteck entworfen, ähnlich wie Sie es in der realen Welt finden.</span><span class="sxs-lookup"><span data-stu-id="bbe80-111">We originally designed the workbench in HoloStudio as a rectangle, much like you'd find in the real world.</span></span> <span data-ttu-id="bbe80-112">Das Problem besteht darin, dass die Benutzer über die Lebensdauer einer Erfahrung verfügen, die Sie darüber informiert, dass Sie immer noch unterwegs sind, wenn Sie sich an einem Computer befinden oder vor einem Computer arbeiten, sodass Sie nicht in der Workbench unterwegs waren und Ihre 3D-Erstellung auf allen Seiten untersucht.</span><span class="sxs-lookup"><span data-stu-id="bbe80-112">The problem is that people have a lifetime of experience that tells them to stay still when they're sitting at a desk or working in front of a computer, so they weren't moving around the workbench and exploring their 3D creation from all sides.</span></span>

![Der rechteckige Entwurf der Workbench in holostudio hat Benutzern den Umstieg auf die Entwicklung von allen Seiten durchgeführt.](images/rectangular-workbench-500px.jpg)

<span data-ttu-id="bbe80-114">Wir hatten die Einblicke, um die Workbench zu runden, sodass es keine "Front"-oder Clear-Position gab, die Sie positionieren sollten.</span><span class="sxs-lookup"><span data-stu-id="bbe80-114">We had the insight to make the workbench round, so that there was no "front" or clear place that you were supposed to stand.</span></span> <span data-ttu-id="bbe80-115">Als wir dies getestet haben, begannen plötzlich Benutzer, ihre eigenen Schöpfungen zu erkunden.</span><span class="sxs-lookup"><span data-stu-id="bbe80-115">When we tested this, suddenly people started moving around and exploring their creations on their own.</span></span>

![Der zirkuläre Workbench-Entwurf hat die Benutzer dazu ermutigt, sich ganz auf ihre Schöpfungen zu bewegen.](images/circular-workbench-500px.jpg)

<span data-ttu-id="bbe80-117">**Was wir gelernt haben**</span><span class="sxs-lookup"><span data-stu-id="bbe80-117">**What we learned**</span></span>

<span data-ttu-id="bbe80-118">Denken Sie immer daran, was für den Benutzer von Bedeutung ist.</span><span class="sxs-lookup"><span data-stu-id="bbe80-118">Always be thinking about what's comfortable for the user.</span></span> <span data-ttu-id="bbe80-119">Der physische Speicherplatz zu nutzen, ist ein interessantes Feature von hololens und etwas, das Sie mit anderen Geräten nicht erledigen können.</span><span class="sxs-lookup"><span data-stu-id="bbe80-119">Taking advantage of their physical space is a cool feature of HoloLens and something you can't do with other devices.</span></span>

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a><span data-ttu-id="bbe80-120">Problem #2: Modale Dialoge sind manchmal aus dem Holographic-Frame heraus.</span><span class="sxs-lookup"><span data-stu-id="bbe80-120">Problem #2: Modal dialogs are sometimes out of the holographic frame</span></span>

<span data-ttu-id="bbe80-121">Manchmal kann der Benutzer in einer anderen Richtung als etwas sehen, das seine Aufmerksamkeit in Ihrer APP benötigt.</span><span class="sxs-lookup"><span data-stu-id="bbe80-121">Sometimes, your user may be looking in a different direction from something that needs their attention in your app.</span></span> <span data-ttu-id="bbe80-122">Auf einem PC können Sie einfach ein Dialogfeld einklappen, aber wenn Sie dies in einer 3D-Umgebung auf einem anderen Element tun, kann es so aussehen, als ob das Dialogfeld in den Weg kommt.</span><span class="sxs-lookup"><span data-stu-id="bbe80-122">On a PC, you can just pop up a dialog, but if you do this in someone's face in a 3D environment, it can feel like the dialog is getting in their way.</span></span> <span data-ttu-id="bbe80-123">Sie benötigen Sie, um die Nachricht zu lesen, aber Ihr Instinkt besteht darin, die Nachricht zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="bbe80-123">You need them to read the message, but their instinct is to try to get away from it.</span></span> <span data-ttu-id="bbe80-124">Diese Reaktion ist großartig, wenn Sie ein Spiel spielen, aber in einem Tool, das für die Arbeit entwickelt wurde, ist es weniger als ideal.</span><span class="sxs-lookup"><span data-stu-id="bbe80-124">This reaction is great if you're playing a game, but in a tool designed for work, it's less than ideal.</span></span>

<span data-ttu-id="bbe80-125">Nachdem wir einige unterschiedliche Dinge ausprobiert haben, haben wir uns schließlich mit der Verwendung eines "gedankenblasen"-Systems für unsere Dialoge und der hinzugefügten tendrils befasst, die Benutzer nachvollziehen können, wo Ihre Aufmerksamkeit in unserer Anwendung benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="bbe80-125">After trying a few different things, we finally settled on using a "thought bubble" system for our dialogs and added tendrils that users can follow to where their attention is needed in our application.</span></span> <span data-ttu-id="bbe80-126">Wir haben auch den "tendrils"-Impuls erstellt, der einen Sinn der Direktionalität impliziert, damit die Benutzer wissen, wo Sie unterwegs sind.</span><span class="sxs-lookup"><span data-stu-id="bbe80-126">We also made the tendrils pulse, which implied a sense of directionality so that users knew where to go.</span></span>

![Das System "Thought Blase" enthielt pulsierender-tendrils, das eine Vorstellung von Richtung bot, sodass Benutzer in der APP an der Stelle waren, an der Ihre Aufmerksamkeit notwendig war.](images/thought-bubble-500px.jpg)

<span data-ttu-id="bbe80-128">**Was wir gelernt haben**</span><span class="sxs-lookup"><span data-stu-id="bbe80-128">**What we learned**</span></span>

<span data-ttu-id="bbe80-129">Es ist in 3D viel schwieriger, Benutzer an Dinge zu warnen, auf die Sie achten müssen.</span><span class="sxs-lookup"><span data-stu-id="bbe80-129">It's much harder in 3D to alert users to things they need to pay attention to.</span></span> <span data-ttu-id="bbe80-130">Mithilfe von Aufmerksamkeits Leitern, wie z. b. [räumlichem Sound](spatial-sound.md), Lichtstrahlen oder gedankenblasen, können Benutzer dazu führen, wo Sie sich befinden müssen.</span><span class="sxs-lookup"><span data-stu-id="bbe80-130">Using attention directors such as [spatial sound](spatial-sound.md), light rays, or thought bubbles, can lead users to where they need to be.</span></span>

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a><span data-ttu-id="bbe80-131">Problem #3: Manchmal kann die Benutzeroberfläche durch andere Hologramme blockiert werden.</span><span class="sxs-lookup"><span data-stu-id="bbe80-131">Problem #3: Sometimes UI can get blocked by other holograms</span></span>

<span data-ttu-id="bbe80-132">Es gibt Zeiten, in denen ein Benutzer mit einem – Hologramm und den zugehörigen UI-Steuerelementen interagieren möchte, die jedoch nicht in der Ansicht angezeigt werden, da ein anderes – Hologramm vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="bbe80-132">There are times when a user wants to interact with a hologram and its associated UI controls, but they are blocked from view because another hologram is in front of them.</span></span> <span data-ttu-id="bbe80-133">Während der Entwicklung von holostudio haben wir Test-und Fehlerinformationen verwendet, um zu einer Lösung zu gelangen.</span><span class="sxs-lookup"><span data-stu-id="bbe80-133">While we were developing HoloStudio, we used trial and error to come to a solution for this.</span></span>

![Ein UI-Steuerelement, das einem – Hologramm zugeordnet ist, kann blockiert werden, wenn zwischen dem Benutzer und dem Benutzer hololens ein anderes – Hologramm vorhanden ist.](images/ui-blocked-500px.jpg)

<span data-ttu-id="bbe80-135">Wir haben versucht, das UI-Steuerelement näher an den Benutzer zu verschieben, sodass es nicht blockiert werden konnte, aber es war nicht gut, dass der Benutzer sich ein Steuerelement ansehen konnte, das sich in Ihrer Nähe befand, gleichzeitig ein – Hologramm, das weit entfernt war.</span><span class="sxs-lookup"><span data-stu-id="bbe80-135">We tried moving the UI control closer to the user so it couldn't get blocked, but found that it wasn't comfortable for the user to look at a control that was near to you while simultaneously looking at a hologram that was far away.</span></span> <span data-ttu-id="bbe80-136">Wenn wir jedoch das Steuerelement vor dem nächstgelegenen – Hologramm an den Benutzer verschoben haben, haben Sie das Gefühl, dass es von dem – Hologramm getrennt wurde, das beeinträchtigt werden sollte.</span><span class="sxs-lookup"><span data-stu-id="bbe80-136">If, however, we moved the control in front of the closest hologram to the user, they felt like it was detached from the hologram it should be affecting.</span></span>

<span data-ttu-id="bbe80-137">Schließlich haben wir das UI-Steuerelement in die gleiche Entfernung versetzt wie das – Hologramm, dem es zugeordnet ist, sodass beide miteinander verbunden sind.</span><span class="sxs-lookup"><span data-stu-id="bbe80-137">We finally ended up ghosting the UI control, and put it at the same distance from the user as the hologram it's associated with, so they both feel connected.</span></span> <span data-ttu-id="bbe80-138">Dies ermöglicht es dem Benutzer, mit dem Steuerelement zu interagieren, auch wenn es verdeckt ist.</span><span class="sxs-lookup"><span data-stu-id="bbe80-138">This allows the user to interact with the control even though it's been obscured.</span></span>

![Die Lösung: Wir haben das UI-Steuerelement gehosttet, das sowohl eine Interaktion mit dem Steuerelement ermöglichte als auch eine Verbindung mit dem – Hologramm hergestellt hat, das es beeinflusst hat.](images/ghosting-ui-500px.jpg)

<span data-ttu-id="bbe80-140">**Was wir gelernt haben**</span><span class="sxs-lookup"><span data-stu-id="bbe80-140">**What we learned**</span></span>

<span data-ttu-id="bbe80-141">Benutzer müssen problemlos auf UI-Steuerelemente zugreifen können, selbst wenn Sie blockiert wurden. Daher sollten Sie Methoden ermitteln, um sicherzustellen, dass Benutzer ihre Aufgaben unabhängig davon, wo sich Ihre Hologramme in der realen Welt befinden, ausführen können.</span><span class="sxs-lookup"><span data-stu-id="bbe80-141">Users need to be able to easily access UI controls even if they've been blocked, so figure out methods to ensure that users can complete their tasks no matter where their holograms are in the real world.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="bbe80-142">Informationen zum Autor</span><span class="sxs-lookup"><span data-stu-id="bbe80-142">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="bbe80-143"><b>Marcus Ghaly</b></span><span class="sxs-lookup"><span data-stu-id="bbe80-143"><b>Marcus Ghaly</b></span></span><br><span data-ttu-id="bbe80-144">SR. Holographic-Designer@Microsoft</span><span class="sxs-lookup"><span data-stu-id="bbe80-144">Sr. Holographic Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="bbe80-145">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="bbe80-145">See also</span></span>
* [<span data-ttu-id="bbe80-146">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="bbe80-146">Instinctual interactions</span></span>](interaction-fundamentals.md)

 
