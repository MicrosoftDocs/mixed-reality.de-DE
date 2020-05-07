---
title: Blick Eingabe in Unreal
description: Erläutert, wie Sie die Überblicks Eingabe in Unreal verwenden
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, hololens, Eye Tracking
ms.openlocfilehash: 7387bb3f25cdbdfac32f508c173fbd098f844e84
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835623"
---
# <a name="gaze-input"></a>Blick Eingabe

Das Windows Mixed Reality-Plug-in stellt keine speziellen Funktionen für die Eingabe des Blicks bereit. Alles funktioniert auch mit der Unreal-Standard-API.

[Head-Blick-API](https://docs.unrealengine.com/en-US/BlueprintAPI/Input/HeadMountedDisplay/index.html)

## <a name="eye-tracking"></a>Eyetracking – Blickverfolgung

Um die Eye Tracking-API zu verwenden, sollten Entwickler in ihren hololens-Projekteinstellungen die Funktion "Blick Eingabe" aktivieren. Wenn die Anwendung gestartet wird, wird dem Benutzer die folgende Zustimmungsaufforderung angezeigt.

![Eye-Eingabe Berechtigungen](images/unreal/eye-input-permissions.png)
 
Wenn der Benutzer seine Berechtigung erteilt, erhält die Anwendung eine Eingabe für den Augenblick. 

Die Eye Tracking-API von Unreal ist [hier](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html) dokumentiert.

Die technischen Details der Eye-Nachverfolgung finden Sie [hier](eye-tracking.md) .

Beachten Sie, dass die hololens-Eye-Verfolgung speziell für Unreal einen einzelnen Blick Strahl auf beide Augen hat. Hololens stellt keine stereoprotokollierung für den stereodruck bereit.
