---
title: QR-Codes in Unreal
description: Leitfaden zur Verwendung von QR-Codes in Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, QR-Codes
ms.openlocfilehash: 67a3a8092ab908cba6768e92ed6a0e7bd2737275
ms.sourcegitcommit: 5b802078090700e06630c8fc665fedeaa0a16eb7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83342658"
---
# <a name="qr-codes-in-unreal"></a>QR-Codes in Unreal

HoloLens kann QR-Codes im Weltbereich erkennen, um Hologramme an bekannten Positionen in der realen Welt zu rendern.  Dies kann auch verwendet werden, um auf mehreren Geräten Hologramme an der gleichen Position zu rendern und so ein gemeinsames Erlebnis zu ermöglichen. 

Wenn Sie die QR-Erkennung für HoloLens aktivieren möchten, vergewissern Sie sich im Unreal-Editor unter „Project Settings“ (Projekteinstellungen) > „Platform“ (Plattform) > „HoloLens“ > „Capabilities“ (Funktionen), dass das Kontrollkästchen für die Webcamfunktion aktiviert ist.  

Entscheiden Sie sich für die Verwendung von QR-Code-Nachverfolgung in Unreal, indem Sie eine ARSession mit der Funktion StartARSession starten. 

QR-Codes werden über das AR-Geometrienachverfolgungssystem von Unreal als nachverfolgtes Bild bereitgestellt.  Für dessen Verwendung muss einem Blaupausenakteur eine in AR nachverfolgbare Benachrichtigungskomponente hinzugefügt werden: 

![QR: In AR nachverfolgbare Benachrichtigung](images/unreal-spatialmapping-artrackablenotify.PNG)

Navigieren Sie dann zu den Details der Komponente, und klicken Sie auf die grüne Plusschaltfläche (+) für die zu überwachenden Ereignisse.  

![QR: Ereignisse](images/unreal-spatialmapping-events.PNG)

Hier wurde „OnUpdateTrackedImage“ abonniert, um einen Punkt in der Mitte eines QR-Codes zu rendern und die codierten Daten des QR-Codes auszugeben. 

![QR: Renderbeispiel](images/unreal-qr-render.PNG)

Wandeln Sie das nachverfolgte Bild zuerst in „ARTrackedQRCode“ um, um sich zu vergewissern, dass es sich bei dem derzeitigen aktualisierten Bild um einen QR-Code handelt.  Anschließend können die codierten Daten mithilfe der Variablen „QRCode“ abgerufen werden.  Die linke obere Ecke des QR-Codes kann auf der Grundlage der Position von „GetLocalToWorldTransform“ abgerufen werden.  Die Dimensionen können mithilfe von „GetEstimateSize“ abgerufen werden. 

Jeder QR-Code verfügt auch über eine eindeutige GUID: 

![QR: GUID](images/unreal-qr-guid.PNG)

## <a name="see-also"></a>Siehe auch
* [Nachverfolgen von QR-Codes](qr-code-tracking.md)
