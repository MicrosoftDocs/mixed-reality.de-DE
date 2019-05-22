---
title: 'Fallstudie: 3 HoloStudio Benutzeroberfläche sowie die Interaktion entwerfen Erkenntnisse'
description: Entwerfen von HoloStudio UI und Interaktion Erkenntnisse
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, HoloStudio, Windows Mixed Reality
ms.openlocfilehash: e01e2ea888398e9982b56fd95f90ef0731ec6bc2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974830"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a><span data-ttu-id="17d7e-104">Fallstudie: 3 HoloStudio Benutzeroberfläche sowie die Interaktion entwerfen Erkenntnisse</span><span class="sxs-lookup"><span data-stu-id="17d7e-104">Case study - 3 HoloStudio UI and interaction design learnings</span></span>

<span data-ttu-id="17d7e-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) wurde eine der ersten Microsoft-apps für HoloLens.</span><span class="sxs-lookup"><span data-stu-id="17d7e-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) was one of the first Microsoft apps for HoloLens.</span></span> <span data-ttu-id="17d7e-106">Aus diesem Grund mussten wir erstellen neue bewährte Methoden für 3D Benutzeroberfläche und entwerfen.</span><span class="sxs-lookup"><span data-stu-id="17d7e-106">Because of this, we had to create new best practices for 3D UI and interaction design.</span></span> <span data-ttu-id="17d7e-107">Wir haben dies über viele Benutzer zu testen, Erstellen von Prototypen und Versuch und Irrtum.</span><span class="sxs-lookup"><span data-stu-id="17d7e-107">We did this through a lot of user testing, prototyping, and trial and error.</span></span>

<span data-ttu-id="17d7e-108">Wir wissen, dass nicht jeder verfügt über die Ressourcen zur Verfügung, die diese Art der Untersuchungen durchführen, sodass wir unsere Sr. Holographic Designer Marcus Ghaly, drei Dinge freigeben haben wir gelernt, während der Entwicklung von HoloStudio zum Design von Benutzeroberfläche und Interaktion für apps für HoloLens.</span><span class="sxs-lookup"><span data-stu-id="17d7e-108">We know that not everyone has the resources at their disposal to do this type of research, so we had our Sr. Holographic Designer, Marcus Ghaly, share three things we learned during the development of HoloStudio about UI and interaction design for HoloLens apps.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="17d7e-109">Video ansehen</span><span class="sxs-lookup"><span data-stu-id="17d7e-109">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a><span data-ttu-id="17d7e-110">Problem #1: Benutzer möchten nicht auf ihre schöpfungen bewegen</span><span class="sxs-lookup"><span data-stu-id="17d7e-110">Problem #1: People didn't want to move around their creations</span></span>

<span data-ttu-id="17d7e-111">Wir ursprünglich entworfen die Workbench im HoloStudio als eines Rechtecks, der viel wie finden Sie in der Praxis würde.</span><span class="sxs-lookup"><span data-stu-id="17d7e-111">We originally designed the workbench in HoloStudio as a rectangle, much like you'd find in the real world.</span></span> <span data-ttu-id="17d7e-112">Das Problem ist, dass Personen Erfahrungen, die informiert bleiben weiterhin zur Verfügung, wenn sie an einem Tisch sitzen oder vor einem Computer arbeiten, damit sie verschieben, um die Workbench waren nicht und untersuchen deren 3D Erstellung von allen Seiten.</span><span class="sxs-lookup"><span data-stu-id="17d7e-112">The problem is that people have a lifetime of experience that tells them to stay still when they're sitting at a desk or working in front of a computer, so they weren't moving around the workbench and exploring their 3D creation from all sides.</span></span>

![Der rechteckige Entwurf der Workbench in HoloStudio dissuaded Benutzer verschieben und die Erstellung von allen Seiten angezeigt.](images/rectangular-workbench-500px.jpg)

<span data-ttu-id="17d7e-114">Wir hatten die Erkenntnis, zu der Workbench zu runden, sodass gab es keine "Front", oder deaktivieren Sie vorhanden, die Sie bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="17d7e-114">We had the insight to make the workbench round, so that there was no "front" or clear place that you were supposed to stand.</span></span> <span data-ttu-id="17d7e-115">Wenn wir dies getestet, gestartet plötzlich Personen, verschieben, und untersuchen ihre schöpfungen selbst.</span><span class="sxs-lookup"><span data-stu-id="17d7e-115">When we tested this, suddenly people started moving around and exploring their creations on their own.</span></span>

![Zirkuläre Workbench Entwurf ermutigt Benutzer, um deren Erstellung zu durchlaufen.](images/circular-workbench-500px.jpg)

<span data-ttu-id="17d7e-117">**Was wir gelernt haben**</span><span class="sxs-lookup"><span data-stu-id="17d7e-117">**What we learned**</span></span>

<span data-ttu-id="17d7e-118">Immer, nachzudenken, was für den Benutzer vertraut ist.</span><span class="sxs-lookup"><span data-stu-id="17d7e-118">Always be thinking about what's comfortable for the user.</span></span> <span data-ttu-id="17d7e-119">Der physische Speicherplatz zu nutzen, ist ein interessantes Feature der HoloLens und etwas, das mit anderen Geräten nicht möglich.</span><span class="sxs-lookup"><span data-stu-id="17d7e-119">Taking advantage of their physical space is a cool feature of HoloLens and something you can't do with other devices.</span></span>

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a><span data-ttu-id="17d7e-120">Problem #2: Modale Dialogfelder sind manchmal aus dem holographic Rahmen</span><span class="sxs-lookup"><span data-stu-id="17d7e-120">Problem #2: Modal dialogs are sometimes out of the holographic frame</span></span>

<span data-ttu-id="17d7e-121">In einigen Fällen kann der Benutzer in eine andere Richtung von einem Element suchen, die ihre Aufmerksamkeit in Ihrer app benötigt.</span><span class="sxs-lookup"><span data-stu-id="17d7e-121">Sometimes, your user may be looking in a different direction from something that needs their attention in your app.</span></span> <span data-ttu-id="17d7e-122">Auf einem PC Sie können ein Dialogfeld nur Popupfenster einrichten, aber wenn Sie in ein Gesicht in einer Umgebung mit 3D dazu können auch wie im Dialogfeld auf ihre Weise erhält.</span><span class="sxs-lookup"><span data-stu-id="17d7e-122">On a PC, you can just pop up a dialog, but if you do this in someone's face in a 3D environment, it can feel like the dialog is getting in their way.</span></span> <span data-ttu-id="17d7e-123">Sie benötigen diese für die Nachricht zu lesen, aber ihre instinkthafte Verhalten besteht darin, davon zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="17d7e-123">You need them to read the message, but their instinct is to try to get away from it.</span></span> <span data-ttu-id="17d7e-124">Diese Reaktion eignet sich hervorragend, wenn sind Sie ein Spiel, aber in ein Tool für die Arbeit, andere als ideal ist.</span><span class="sxs-lookup"><span data-stu-id="17d7e-124">This reaction is great if you're playing a game, but in a tool designed for work, it's less than ideal.</span></span>

<span data-ttu-id="17d7e-125">Nach dem Testen verschiedene Funktionen, wir schließlich ausgeglichen zur Verwendung von einem System "dachte Blase" für unsere Dialogfelder und Tendrils, die Benutzer an, wo ihre Aufmerksamkeit, in der Anwendung erforderlich ist hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="17d7e-125">After trying a few different things, we finally settled on using a "thought bubble" system for our dialogs and added tendrils that users can follow to where their attention is needed in our application.</span></span> <span data-ttu-id="17d7e-126">Wir haben auch den Puls Tendrils, der einen Überblick über die direktionalität impliziert, damit Benutzer wissen, an welcher Stelle wechseln.</span><span class="sxs-lookup"><span data-stu-id="17d7e-126">We also made the tendrils pulse, which implied a sense of directionality so that users knew where to go.</span></span>

![Das System "Betrachtet Blase" enthalten pulsierender Tendrils, die einen Überblick über die Richtung, führt der Benutzer, in dem ihre Aufmerksamkeit benötigt wurde, in der app bereitgestellt.](images/thought-bubble-500px.jpg)

<span data-ttu-id="17d7e-128">**Was wir gelernt haben**</span><span class="sxs-lookup"><span data-stu-id="17d7e-128">**What we learned**</span></span>

<span data-ttu-id="17d7e-129">Es ist viel schwieriger in 3D um Benutzer auf Dinge, denen sie beachten müssen.</span><span class="sxs-lookup"><span data-stu-id="17d7e-129">It's much harder in 3D to alert users to things they need to pay attention to.</span></span> <span data-ttu-id="17d7e-130">Mithilfe von Aufmerksamkeit Directors wie [räumliche Sound](spatial-sound.md)light Strahlung oder Überlegungen ausgelöst wird, kann zu führen, Benutzer erforderlich sein.</span><span class="sxs-lookup"><span data-stu-id="17d7e-130">Using attention directors such as [spatial sound](spatial-sound.md), light rays, or thought bubbles, can lead users to where they need to be.</span></span>

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a><span data-ttu-id="17d7e-131">Problem #3: Manchmal kann Benutzeroberfläche von anderen Hologramme blockiert werden</span><span class="sxs-lookup"><span data-stu-id="17d7e-131">Problem #3: Sometimes UI can get blocked by other holograms</span></span>

<span data-ttu-id="17d7e-132">Es gibt Situationen, wenn ein Benutzer möchte, für die Interaktion mit ggf. ein Hologramm und die zugeordnete UI-Steuerelemente, werden jedoch blockiert, aus der Ansicht, da eine andere – Hologramm vorangestellt ist.</span><span class="sxs-lookup"><span data-stu-id="17d7e-132">There are times when a user wants to interact with a hologram and its associated UI controls, but they are blocked from view because another hologram is in front of them.</span></span> <span data-ttu-id="17d7e-133">Während wir HoloStudio entwickelten, verwendet haben wir Versuch und Irrtum ist auf eine Lösung für dieses.</span><span class="sxs-lookup"><span data-stu-id="17d7e-133">While we were developing HoloStudio, we used trial and error to come to a solution for this.</span></span>

![Ein UI-Steuerelement zugeordnete ggf. ein Hologramm kann blockiert werden, wenn eine andere – Hologramm zwischen ihnen und dem Benutzer steht, geteert HoloLens vorhanden ist.](images/ui-blocked-500px.jpg)

<span data-ttu-id="17d7e-135">Wir haben versucht, das UI-Steuerelement näher an den Benutzer verschieben, es konnte nicht erhalten blockiert jedoch festgestellt, dass es war nicht vertraut, damit der Benutzer auf ein Steuerelement zu suchen, die beim Nähe Sie gleichzeitig Blick auf ggf. ein Hologramm, die weit entfernt wurde.</span><span class="sxs-lookup"><span data-stu-id="17d7e-135">We tried moving the UI control closer to the user so it couldn't get blocked, but found that it wasn't comfortable for the user to look at a control that was near to you while simultaneously looking at a hologram that was far away.</span></span> <span data-ttu-id="17d7e-136">Wenn Sie allerdings wir dem Benutzer das Steuerelement vor der nächsten – Hologramm verschoben, glaubten sie, wie sie aus der Hologramm getrennt wurde, die es beeinträchtigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="17d7e-136">If, however, we moved the control in front of the closest hologram to the user, they felt like it was detached from the hologram it should be affecting.</span></span>

<span data-ttu-id="17d7e-137">Wir schließlich letztendlich ghosting von UI-Steuerelement, und legen Sie sie die gleiche Distanz vom Benutzer als Hologramm, die es verknüpft ist, damit beide verbundenen.</span><span class="sxs-lookup"><span data-stu-id="17d7e-137">We finally ended up ghosting the UI control, and put it at the same distance from the user as the hologram it's associated with, so they both feel connected.</span></span> <span data-ttu-id="17d7e-138">Dadurch kann der Benutzer mit dem Steuerelement interagieren, auch wenn es verborgen wurde, ist.</span><span class="sxs-lookup"><span data-stu-id="17d7e-138">This allows the user to interact with the control even though it's been obscured.</span></span>

![Die Lösung: wir verwaist. das UI-Steuerelement, die Interaktion mit dem Steuerelement zulässig und machte es die Verbindung mit dem – Hologramm können sie beeinträchtigt wurde.](images/ghosting-ui-500px.jpg)

<span data-ttu-id="17d7e-140">**Was wir gelernt haben**</span><span class="sxs-lookup"><span data-stu-id="17d7e-140">**What we learned**</span></span>

<span data-ttu-id="17d7e-141">Benutzer müssen können problemlos Benutzeroberflächen-Steuerelemente zugreifen, selbst wenn sie blockiert haben, sodass Methoden, um sicherzustellen, dass Benutzer ihre Aufgaben unabhängig davon, wo ihre Hologramme in der Praxis sind abschließen können Sie herausfinden.</span><span class="sxs-lookup"><span data-stu-id="17d7e-141">Users need to be able to easily access UI controls even if they've been blocked, so figure out methods to ensure that users can complete their tasks no matter where their holograms are in the real world.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="17d7e-142">Der Autor</span><span class="sxs-lookup"><span data-stu-id="17d7e-142">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="17d7e-143"><b>Marcus Ghaly</b></span><span class="sxs-lookup"><span data-stu-id="17d7e-143"><b>Marcus Ghaly</b></span></span><br><span data-ttu-id="17d7e-144">SR. Holographic-Designer @Microsoft</span><span class="sxs-lookup"><span data-stu-id="17d7e-144">Sr. Holographic Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="17d7e-145">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="17d7e-145">See also</span></span>
* [<span data-ttu-id="17d7e-146">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="17d7e-146">Instinctual interactions</span></span>](interaction-fundamentals.md)

 
