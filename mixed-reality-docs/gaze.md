---
title: Blickeingabe
description: Der Blick ist die erste Form der Eingabe und ist eine primäre Form der Ausrichtung in gemischter Realität.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Gemischte Realität, Blick, Interaktion, Entwurf
ms.openlocfilehash: 7e65d26d3e9edabbd01d35a887ffc8622a3c6337
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414372"
---
# <a name="gaze"></a><span data-ttu-id="c59a8-104">Blickeingabe</span><span class="sxs-lookup"><span data-stu-id="c59a8-104">Gaze</span></span>

<span data-ttu-id="c59a8-105">Der **Blick** ist die erste Form der Eingabe und ist eine primäre Form der Ausrichtung in gemischter Realität.</span><span class="sxs-lookup"><span data-stu-id="c59a8-105">**Gaze** is the first form of input and is a primary form of targeting within mixed reality.</span></span> <span data-ttu-id="c59a8-106">Der Blick zeigt Ihnen, wo der Benutzer in der Welt sucht, und ermöglicht Ihnen, seine Absicht zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="c59a8-106">Gaze tells you where the user is looking in the world and lets you determine their intent.</span></span> <span data-ttu-id="c59a8-107">In der Praxis sehen Sie in der Regel ein Objekt, mit dem Sie interagieren möchten.</span><span class="sxs-lookup"><span data-stu-id="c59a8-107">In the real world, you'll typically look at an object that you intend to interact with.</span></span> <span data-ttu-id="c59a8-108">Dies ist mit Blick identisch.</span><span class="sxs-lookup"><span data-stu-id="c59a8-108">This is the same with gaze.</span></span>

<span data-ttu-id="c59a8-109">Mixed Reality-Headsets verwenden die Position und Ausrichtung des Hauptteils Ihres Benutzers, um den Vektor für den Head-Blick zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="c59a8-109">Mixed reality headsets use the position and orientation of your user's head to determine their head gaze vector.</span></span> <span data-ttu-id="c59a8-110">Sie können sich diesen Vektor als Laser Zeiger direkt zwischen den Augen des Benutzers vorstellen.</span><span class="sxs-lookup"><span data-stu-id="c59a8-110">You can think of this vector as a laser pointer straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="c59a8-111">Wenn sich der Benutzer um den Raum kümmert, kann die Anwendung diesen Strahl sowohl mit eigenen holograms als auch mit dem [räumlichen](spatial-mapping.md) zuordnungsmesh überschneiden, um zu bestimmen, welches virtuelle oder reale Objekt Ihr Benutzer möglicherweise ansieht.</span><span class="sxs-lookup"><span data-stu-id="c59a8-111">As the user looks around the room, your application can intersect this ray, both with its own holograms and with the [spatial mapping](spatial-mapping.md) mesh to determine what virtual or real-world object your user may be looking at.</span></span>

<span data-ttu-id="c59a8-112">Bei hololens 2 können Interaktionen entweder durch den Haupt-oder den Augenblick des Benutzers oder durch near-oder weite Interaktionen erreicht werden.</span><span class="sxs-lookup"><span data-stu-id="c59a8-112">On HoloLens 2, interactions can be targeted by either the user's head gaze, eye gaze or through near or far hand interactions.</span></span>
<span data-ttu-id="c59a8-113">Bei hololens (1. Generation) sollten Interaktionen im Allgemeinen die Zielvorgabe von der Kopfzeile des Benutzers ableiten, anstatt zu versuchen, direkt an der Position der Hand zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="c59a8-113">On HoloLens (1st gen), interactions should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="c59a8-114">Nachdem eine Interaktion begonnen hat, können relative Bewegungen der Hand verwendet werden, um die [Bewegung](gestures.md)zu steuern, wie bei der [Manipulation oder Navigation](gestures.md#composite-gestures) .</span><span class="sxs-lookup"><span data-stu-id="c59a8-114">Once an interaction has started, relative motions of the hand may be used to control the [gesture](gestures.md), as with the [manipulation or navigation](gestures.md#composite-gestures) gesture.</span></span> <span data-ttu-id="c59a8-115">Mit immersiven Headsets können Sie mithilfe von Head-und zeige fähigen [Bewegungs Controllern](motion-controllers.md)auf abzielen.</span><span class="sxs-lookup"><span data-stu-id="c59a8-115">With immersive headsets, you can target using either head gaze or pointing-capable [motion controllers](motion-controllers.md).</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a><span data-ttu-id="c59a8-116">Unterstützung von Geräten</span><span class="sxs-lookup"><span data-stu-id="c59a8-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c59a8-117"><strong>Funktion</strong></span><span class="sxs-lookup"><span data-stu-id="c59a8-117"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="c59a8-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="c59a8-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="c59a8-119"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="c59a8-119"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="c59a8-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="c59a8-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c59a8-121">Kopfzeile</span><span class="sxs-lookup"><span data-stu-id="c59a8-121">Head gaze</span></span></td>
        <td><span data-ttu-id="c59a8-122">✔️</span><span class="sxs-lookup"><span data-stu-id="c59a8-122">✔️</span></span></td>
        <td><span data-ttu-id="c59a8-123">✔️</span><span class="sxs-lookup"><span data-stu-id="c59a8-123">✔️</span></span></td>
        <td><span data-ttu-id="c59a8-124">✔️</span><span class="sxs-lookup"><span data-stu-id="c59a8-124">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c59a8-125">Augenblick</span><span class="sxs-lookup"><span data-stu-id="c59a8-125">Eye gaze</span></span></td>
        <td><span data-ttu-id="c59a8-126">❌</span><span class="sxs-lookup"><span data-stu-id="c59a8-126">❌</span></span></td>
        <td><span data-ttu-id="c59a8-127">✔️</span><span class="sxs-lookup"><span data-stu-id="c59a8-127">✔️</span></span></td>
        <td><span data-ttu-id="c59a8-128">❌</span><span class="sxs-lookup"><span data-stu-id="c59a8-128">❌</span></span></td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="c59a8-129">Weitere Anleitungen sind für hololens 2 in [Kürze](index.md#news-and-notes)verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c59a8-129">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>


## <a name="uses-of-gaze"></a><span data-ttu-id="c59a8-130">Verwendung von Blick</span><span class="sxs-lookup"><span data-stu-id="c59a8-130">Uses of gaze</span></span>

<span data-ttu-id="c59a8-131">Als Entwickler mit gemischter Realität können Sie mit dem Kopf-oder Augenblick viel anfangen:</span><span class="sxs-lookup"><span data-stu-id="c59a8-131">As a mixed reality developer, you can do a lot with head or eye gaze:</span></span>
* <span data-ttu-id="c59a8-132">Ihre APP kann den Blick mit den holograms in Ihrer Szene überschneiden, um zu bestimmen, wo die Aufmerksamkeit des Benutzers ist.</span><span class="sxs-lookup"><span data-stu-id="c59a8-132">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is.</span></span>
* <span data-ttu-id="c59a8-133">Ihre APP kann auf Gesten und Controller drückt werden, die auf der Sicht des Benutzers basieren, sodass der Benutzer seine Hologramme auswählen, aktivieren, einlesen, Scrollen oder anderweitig interagieren kann.</span><span class="sxs-lookup"><span data-stu-id="c59a8-133">Your app can target gestures and controller presses based on the user's gaze, letting the user select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="c59a8-134">Ihre APP ermöglicht dem Benutzer das Platzieren von holograms auf realen Oberflächen, indem er seinen Blick Strahl mit dem räumlichen Mapping-Gitter schneidet.</span><span class="sxs-lookup"><span data-stu-id="c59a8-134">Your app can let the user place holograms on real-world surfaces, by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="c59a8-135">Ihre APP kann wissen, wenn der Benutzer *nicht* in der Richtung eines wichtigen Objekts sucht, was dazu führen kann, dass Ihre APP visuelle und Audiohinweise zum Umwandeln des Objekts erhält.</span><span class="sxs-lookup"><span data-stu-id="c59a8-135">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

## <a name="cursor"></a><span data-ttu-id="c59a8-136">Cursor</span><span class="sxs-lookup"><span data-stu-id="c59a8-136">Cursor</span></span>

<span data-ttu-id="c59a8-137">Für den Kopf Blick sollten die meisten apps einen [Cursor](cursors.md) (oder einen anderen Auditory/visuellen Hinweis) verwenden, um dem Benutzer die Gewissheit zu verschaffen, mit welchem Element er interagiert.</span><span class="sxs-lookup"><span data-stu-id="c59a8-137">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="c59a8-138">In der Regel positionieren Sie diesen Cursor in der Welt, in der der Head-Blick Strahl zuerst ein Objekt schneidet, das ein Hologramm oder eine reale Oberfläche sein kann.</span><span class="sxs-lookup"><span data-stu-id="c59a8-138">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span>

<span data-ttu-id="c59a8-139">![Ein Beispiel für einen visuellen Cursor zum Anzeigen des Blicks](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="c59a8-139">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
<span data-ttu-id="c59a8-140">*Ein Beispiel für einen visuellen Cursor zum Anzeigen des Blicks*</span><span class="sxs-lookup"><span data-stu-id="c59a8-140">*An example visual cursor to show gaze*</span></span>

<span data-ttu-id="c59a8-141">Für den Augenblick empfiehlt es sich im allgemeinen *nicht* , einen Cursor anzuzeigen, da dies für den Benutzer schnell ablenkend und lästig werden kann.</span><span class="sxs-lookup"><span data-stu-id="c59a8-141">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="c59a8-142">Markieren Sie stattdessen visuelle Ziele, oder verwenden Sie einen sehr schwachen Augen Cursor, um sicherzustellen, womit der Benutzer interagieren soll.</span><span class="sxs-lookup"><span data-stu-id="c59a8-142">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="c59a8-143">Weitere Informationen finden Sie in unserem [Entwurfs Leit Faden für die Augen basierte Eingabe](eye-tracking.md) auf hololens 2.</span><span class="sxs-lookup"><span data-stu-id="c59a8-143">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>

## <a name="giving-action-to-the-users-gaze"></a><span data-ttu-id="c59a8-144">Bereitstellung von Aktionen für den Benutzer</span><span class="sxs-lookup"><span data-stu-id="c59a8-144">Giving action to the user's gaze</span></span>

<span data-ttu-id="c59a8-145">Sobald der Benutzer ein – Hologramm-Objekt oder ein reales Objekt verwendet hat, ist der nächste Schritt das Ausführen von Aktionen für dieses Objekt.</span><span class="sxs-lookup"><span data-stu-id="c59a8-145">Once the user has targeted a hologram or real-world object using their gaze, their next step is to take action on that object.</span></span> <span data-ttu-id="c59a8-146">Die Hauptmethoden, mit denen ein Benutzer Maßnahmen ergreifen kann, sind [Gesten](gestures.md), [Bewegungs Controller](motion-controllers.md) und [Sprachanrufe](voice-input.md).</span><span class="sxs-lookup"><span data-stu-id="c59a8-146">The primary ways for a user to take action are through [gestures](gestures.md), [motion controllers](motion-controllers.md) and [voice](voice-input.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c59a8-147">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c59a8-147">See also</span></span>
* [<span data-ttu-id="c59a8-148">MR-Eingabe 210: Kopfzeile</span><span class="sxs-lookup"><span data-stu-id="c59a8-148">MR Input 210: Head gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="c59a8-149">Anvisieren mit dem Kopf und mit den Augen in DirectX</span><span class="sxs-lookup"><span data-stu-id="c59a8-149">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="c59a8-150">Kopf Blicke in Unity</span><span class="sxs-lookup"><span data-stu-id="c59a8-150">Head gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="c59a8-151">Blick auf hololens 2</span><span class="sxs-lookup"><span data-stu-id="c59a8-151">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="c59a8-152">Eye Eye in Unity mithilfe von Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="c59a8-152">Eye gaze in Unity using Mixed Reality Toolkit</span></span>](https://aka.ms/mrtk-eyes)
