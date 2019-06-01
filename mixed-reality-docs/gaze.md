---
title: Blickeingabe
description: Blicke ist die erste Form der Eingabe und eine primäre Form für die Zielgruppenadressierung in mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Mixed Reality, Blicke, Interaktion, Entwerfen
ms.openlocfilehash: 9e50067f9dfeacf3dce5ea9a928990d1b142e4d0
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453707"
---
# <a name="gaze"></a><span data-ttu-id="4e933-104">Blickeingabe</span><span class="sxs-lookup"><span data-stu-id="4e933-104">Gaze</span></span>

<span data-ttu-id="4e933-105">**Bestaunen** ist die erste Form der Eingabe und eine primäre Form für die Zielgruppenadressierung in mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="4e933-105">**Gaze** is the first form of input and is a primary form of targeting within mixed reality.</span></span> <span data-ttu-id="4e933-106">Blicke Aufschluss darüber, wo der Benutzer ist in der Welt betrachtet und können Sie ihre Absichten zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="4e933-106">Gaze tells you where the user is looking in the world and lets you determine their intent.</span></span> <span data-ttu-id="4e933-107">In der realen Welt in der Regel betrachten ein Objekt Sie das von Ihnen zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="4e933-107">In the real world, you'll typically look at an object that you intend to interact with.</span></span> <span data-ttu-id="4e933-108">Dies ist identisch mit Blicke.</span><span class="sxs-lookup"><span data-stu-id="4e933-108">This is the same with gaze.</span></span>

<span data-ttu-id="4e933-109">Mixed Reality-Headsets werden Position und Ausrichtung von Ihres Benutzers Head verwenden, um ihre Head Blicke Vektor zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="4e933-109">Mixed reality headsets use the position and orientation of your user's head to determine their head gaze vector.</span></span> <span data-ttu-id="4e933-110">Sie können dieses Vektors als einen Laserpointer jetzt direkt aus direkt zwischen dem Benutzer die Augen vorstellen.</span><span class="sxs-lookup"><span data-stu-id="4e933-110">You can think of this vector as a laser pointer straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="4e933-111">Wie der Benutzer im Raum dargestellt wird, kann Ihre Anwendung diese Chow, sowohl mit eigenen Hologramme und überschneiden der [räumliche Zuordnung](spatial-mapping.md) Mesh bestimmen, welche virtuell oder Real-World Ihre Benutzer möglicherweise ansehen.</span><span class="sxs-lookup"><span data-stu-id="4e933-111">As the user looks around the room, your application can intersect this ray, both with its own holograms and with the [spatial mapping](spatial-mapping.md) mesh to determine what virtual or real-world object your user may be looking at.</span></span>

<span data-ttu-id="4e933-112">Für HoloLens-2 Interaktionen können angewendet werden, indem entweder vom Benutzer Head Blicke, Eye Blicke über in der Nähe oder Interaktionen zu weit übergeben.</span><span class="sxs-lookup"><span data-stu-id="4e933-112">On HoloLens 2, interactions can be targeted by either the user's head gaze, eye gaze or through near or far hand interactions.</span></span>
<span data-ttu-id="4e933-113">Für HoloLens (der 1. Generation), Interaktionen sollte im Allgemeinen abgeleitet werden, die für die Zielgruppenadressierung von Head Blicke des Benutzers, statt beim Rendern oder an die Hand, die Position direkt interagieren.</span><span class="sxs-lookup"><span data-stu-id="4e933-113">On HoloLens (1st gen), interactions should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="4e933-114">Nach dem Start einer Interaktion können relative Bewegungen des Zeigers verwendet werden, um zu steuern die [Geste](gestures.md), wie bei der [Manipulation oder die Bildschirmnavigation](gestures.md#composite-gestures) Bewegung.</span><span class="sxs-lookup"><span data-stu-id="4e933-114">Once an interaction has started, relative motions of the hand may be used to control the [gesture](gestures.md), as with the [manipulation or navigation](gestures.md#composite-gestures) gesture.</span></span> <span data-ttu-id="4e933-115">Mit immersive Headsets, können Sie als Ziel verwenden entweder Head Blicke oder zeigt-fähige [motion Controller](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="4e933-115">With immersive headsets, you can target using either head gaze or pointing-capable [motion controllers](motion-controllers.md).</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a><span data-ttu-id="4e933-116">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="4e933-116">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="4e933-117">Feature</span><span class="sxs-lookup"><span data-stu-id="4e933-117">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="4e933-118"><a href="hololens-hardware-details.md">HoloLens (1. Generation)</a></span><span class="sxs-lookup"><span data-stu-id="4e933-118"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="4e933-119">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4e933-119">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="4e933-120"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span><span class="sxs-lookup"><span data-stu-id="4e933-120"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="4e933-121">Head Blicke</span><span class="sxs-lookup"><span data-stu-id="4e933-121">Head gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="4e933-122">✔️</span><span class="sxs-lookup"><span data-stu-id="4e933-122">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="4e933-123">✔️</span><span class="sxs-lookup"><span data-stu-id="4e933-123">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="4e933-124">✔️</span><span class="sxs-lookup"><span data-stu-id="4e933-124">✔️</span></span></td>
</tr><tr>
<td> <span data-ttu-id="4e933-125">Eye Blicke</span><span class="sxs-lookup"><span data-stu-id="4e933-125">Eye gaze</span></span></td><td></td><td style="text-align: center;"><span data-ttu-id="4e933-126">✔️</span><span class="sxs-lookup"><span data-stu-id="4e933-126">✔️</span></span></td><td></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="4e933-127">Weitere Anleitungen, die speziell für HoloLens 2 [bald](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="4e933-127">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>


## <a name="uses-of-gaze"></a><span data-ttu-id="4e933-128">Verwendung des Blicke</span><span class="sxs-lookup"><span data-stu-id="4e933-128">Uses of gaze</span></span>

<span data-ttu-id="4e933-129">Als Entwickler mixed Reality möglich deutlich mit Haupt- oder Eye Blicke:</span><span class="sxs-lookup"><span data-stu-id="4e933-129">As a mixed reality developer, you can do a lot with head or eye gaze:</span></span>
* <span data-ttu-id="4e933-130">Ihre app kann mit der Hologramme in Ihrer Szene Blicke, um zu bestimmen, wo Aufmerksamkeit des Benutzers überlappen.</span><span class="sxs-lookup"><span data-stu-id="4e933-130">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is.</span></span>
* <span data-ttu-id="4e933-131">Gesten und Controller-drückt, die anhand des Benutzers Blicke, den Benutzer auszuwählen, zu aktivieren, erfassen, führen Sie einen Bildlauf oder andernfalls ihre Hologramme interagieren, kann Ihre app abzielen.</span><span class="sxs-lookup"><span data-stu-id="4e933-131">Your app can target gestures and controller presses based on the user's gaze, letting the user select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="4e933-132">Ihre app kann Benutzer Hologramme auf Flächen der realen Welt, zu platzieren, indem Sie ihre Blicke Chow mit dem Netz räumliche Zuordnung überschneidenden lassen.</span><span class="sxs-lookup"><span data-stu-id="4e933-132">Your app can let the user place holograms on real-world surfaces, by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="4e933-133">Ihre app kann der Benutzer wissen *nicht* Suchen in Richtung des ein wichtiger-Objekt, das Ihrer app gerne SEH- und Hinweise für das Objekt zu aktivieren, führen kann.</span><span class="sxs-lookup"><span data-stu-id="4e933-133">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

## <a name="cursor"></a><span data-ttu-id="4e933-134">Cursor</span><span class="sxs-lookup"><span data-stu-id="4e933-134">Cursor</span></span>

<span data-ttu-id="4e933-135">Für Head Blicke, sollten die meisten apps verwenden eine [Cursor](cursors.md) (oder andere akustische/Visual-Angabe) das Vertrauen in was zu gewähren, den sie für die Interaktion mit sind.</span><span class="sxs-lookup"><span data-stu-id="4e933-135">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="4e933-136">Sie werden in der Regel dieser Cursor in der ganzen Welt, in dem ihre Head Blicke Strahl zuerst ein Objekt, schneidet die ggf. ein Hologramm oder eine reale-Oberfläche möglicherweise, positionieren.</span><span class="sxs-lookup"><span data-stu-id="4e933-136">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span>

<span data-ttu-id="4e933-137">![Ein Beispiel für die visual Cursor Blicke angezeigt](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="4e933-137">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
<span data-ttu-id="4e933-138">*Ein Beispiel für die visual Cursor Blicke angezeigt*</span><span class="sxs-lookup"><span data-stu-id="4e933-138">*An example visual cursor to show gaze*</span></span>

<span data-ttu-id="4e933-139">Für die Augen Blicke, empfehlen wir im allgemeinen *nicht* einen Cursor, der angezeigt wird, wie dies schnell zu allgemeiner Ablenkung und es ziemlich ärgerlich, für den Benutzer werden kann.</span><span class="sxs-lookup"><span data-stu-id="4e933-139">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="4e933-140">Stattdessen leicht markieren Sie visual Ziele oder verwenden Sie einen sehr schwach Eye-Cursor zu vertrauen zu den neuerungen des Benutzers zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="4e933-140">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="4e933-141">Weitere Informationen finden Sie unserem [Entwurfsleitfaden für die Eingabe Eye-basierte](eye-tracking.md) für HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4e933-141">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>

## <a name="giving-action-to-the-users-gaze"></a><span data-ttu-id="4e933-142">Aktion sodass des Benutzers Blicke</span><span class="sxs-lookup"><span data-stu-id="4e933-142">Giving action to the user's gaze</span></span>

<span data-ttu-id="4e933-143">Sobald der Benutzer ein Hologramm oder reales Objekt über die Blicke angewendet wurde, ist ihre nächste Schritt für die Reaktion auf dieses Objekt.</span><span class="sxs-lookup"><span data-stu-id="4e933-143">Once the user has targeted a hologram or real-world object using their gaze, their next step is to take action on that object.</span></span> <span data-ttu-id="4e933-144">Die primäre Methode für einen Benutzer zu ergreifen, werden über [Gesten](gestures.md), [motion Controller](motion-controllers.md) und [Voice](voice-input.md).</span><span class="sxs-lookup"><span data-stu-id="4e933-144">The primary ways for a user to take action are through [gestures](gestures.md), [motion controllers](motion-controllers.md) and [voice](voice-input.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4e933-145">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4e933-145">See also</span></span>
* [<span data-ttu-id="4e933-146">MR-Eingabe 210: Head Blicke</span><span class="sxs-lookup"><span data-stu-id="4e933-146">MR Input 210: Head gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="4e933-147">Anvisieren mit dem Kopf und mit den Augen in DirectX</span><span class="sxs-lookup"><span data-stu-id="4e933-147">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="4e933-148">Head Blicke in Unity</span><span class="sxs-lookup"><span data-stu-id="4e933-148">Head gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="4e933-149">Eye-tracking für HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4e933-149">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="4e933-150">Eye Blicke in Unity mithilfe von Mixed Reality-Toolkit</span><span class="sxs-lookup"><span data-stu-id="4e933-150">Eye gaze in Unity using Mixed Reality Toolkit</span></span>](https://aka.ms/mrtk-eyes)
