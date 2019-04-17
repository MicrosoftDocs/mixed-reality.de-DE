---
title: 'Tiefe Kamera Whitepaper: ISSCC 2018'
description: Technische Whitepapers, die Tiefe Kamera im Projekt Kinect für Azure und die nächste Version von HoloLens verwendet werden.
author: mattzmsft
ms.author: mazeller
ms.date: 7/5/2018
ms.topic: article
keywords: Ereignis, Iscc, maschinelles sehen, Forschung, Kinect, Hololens, Tiefe, tof
ms.openlocfilehash: b692f9deeb7768e57ab6161b2c356a6610f18ed9
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594704"
---
# <a name="depth-camera-whitepaper---isscc-2018"></a><span data-ttu-id="6d843-104">Tiefe Kamera Whitepaper: ISSCC 2018</span><span class="sxs-lookup"><span data-stu-id="6d843-104">Depth camera whitepaper - ISSCC 2018</span></span>

<span data-ttu-id="6d843-105">**Titel:** 1Mpixel 65nm BSI 320MHz demodulierte TOF Image-Sensor mit 3.5μm globale Verschluss Pixel und analoge Diskretisierung</span><span class="sxs-lookup"><span data-stu-id="6d843-105">**Title:** 1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning</span></span>

<span data-ttu-id="6d843-106">**Mitwirkende:** Cyrus S Bamji, Swati Mehta, Barry Thompson, Leiter Elkhatib, Stefan Wurster, Onur Akkaya, Andrew Payne, John Godbaz, Mike Fenton, Vijay Rajasekaran, Larry Prather, Satya Nagaraja, Vishali Mogallapu, Dane Schnee, umfangreiche McCauley, Mustansir Mukadam, Iskender Agi, Shaun McCarthy, Zhanping Xu, Travis Perry, William Qian, Vei-Han Chan, Prabhu Adepu, Gazi Ali, Muneeb Ahmed, Aditya Mukherjee, Sheethal Nayak, Dave Gampell, Sunil Acharya, Lou Kordus, Pat O'Connor</span><span class="sxs-lookup"><span data-stu-id="6d843-106">**Contributors:** Cyrus S Bamji, Swati Mehta, Barry Thompson, Tamer Elkhatib, Stefan Wurster, Onur Akkaya, Andrew Payne, John Godbaz, Mike Fenton, Vijay Rajasekaran, Larry Prather, Satya Nagaraja, Vishali Mogallapu, Dane Snow, Rich McCauley, Mustansir Mukadam, Iskender Agi, Shaun McCarthy, Zhanping Xu, Travis Perry, William Qian, Vei-Han Chan, Prabhu Adepu, Gazi Ali, Muneeb Ahmed, Aditya Mukherjee, Sheethal Nayak, Dave Gampell, Sunil Acharya, Lou Kordus, Pat O'Connor</span></span>

<span data-ttu-id="6d843-107">**Bei ISSCC 2018 angezeigt und in ISSCC Deg veröffentlicht wurden. Tech. Whitepapers, Februar 2018.**</span><span class="sxs-lookup"><span data-stu-id="6d843-107">**Presented at ISSCC 2018 and published in ISSCC Deg. Tech. Papers, Feb 2018.**</span></span>

<span data-ttu-id="6d843-108">C.</span><span class="sxs-lookup"><span data-stu-id="6d843-108">C.</span></span> <span data-ttu-id="6d843-109">Bamji Et Al., "1Mpixel 65nm BSI 320MHz demodulierte TOF Image-Sensor mit 3.5μm globale Verschluss Pixel und analoge Klassierung" ISSCC Deg.</span><span class="sxs-lookup"><span data-stu-id="6d843-109">Bamji et al., “1Mpixel 65nm BSI 320MHz Demodulated TOF Image Sensor with 3.5μm Global Shutter Pixels and Analog Binning,” ISSCC Deg.</span></span> <span data-ttu-id="6d843-110">Tech.</span><span class="sxs-lookup"><span data-stu-id="6d843-110">Tech.</span></span> <span data-ttu-id="6d843-111">Whitepapers, s. 94-95, Februar 2018.</span><span class="sxs-lookup"><span data-stu-id="6d843-111">Papers, pp. 94-95, Feb 2018.</span></span> <span data-ttu-id="6d843-112">IEEE erkunden Link: https://ieeexplore.ieee.org/document/8310200/</span><span class="sxs-lookup"><span data-stu-id="6d843-112">IEEE Explore Link: https://ieeexplore.ieee.org/document/8310200/</span></span>

<span data-ttu-id="6d843-113">© 2018 IEEE.</span><span class="sxs-lookup"><span data-stu-id="6d843-113">© 2018 IEEE.</span></span> <span data-ttu-id="6d843-114">Persönliche Nutzung dieses Material ist zulässig.</span><span class="sxs-lookup"><span data-stu-id="6d843-114">Personal use of this material is permitted.</span></span> <span data-ttu-id="6d843-115">IEEE-Berechtigung für alle anderen einsatzmöglichkeiten, in der aktuellen oder zukünftigen Medien, einschließlich Erneutes Drucken/das erneute veröffentlichen dieses Material für Werbe- oder Marketingzwecken, neue kollektiven funktioniert, für den Wiederverkauf oder Verteilung an den Server oder Listen erstellen abgerufen werden muss oder Wiederverwendung von urheberrechtlich geschützten diese Arbeit in andere Komponenten.</span><span class="sxs-lookup"><span data-stu-id="6d843-115">Permission from IEEE must be obtained for all other uses, in any current or future media, including reprinting/republishing this material for advertising or promotional purposes, creating new collective works, for resale or redistribution to servers or lists, or reuse of any copyrighted component of this work in other works.</span></span>

<span data-ttu-id="6d843-116">**Whitepaper:**</span><span class="sxs-lookup"><span data-stu-id="6d843-116">**Whitepaper:**</span></span><br>
<span data-ttu-id="6d843-117">![Vorschau der whitepaper](images/depth-camera-isscc.PNG)</span><span class="sxs-lookup"><span data-stu-id="6d843-117">![Preview of whitepaper](images/depth-camera-isscc.PNG)</span></span><br>
[<span data-ttu-id="6d843-118">Download eines Whitepapers mit Tiefe Kamera</span><span class="sxs-lookup"><span data-stu-id="6d843-118">Download depth camera whitepaper</span></span>](images/Depth-Camera-ISSCC-2018.pdf)
