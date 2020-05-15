---
title: Raumanker in Unreal
description: Leitfaden für die Verwendung von Raumankern in Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, Raumanker
ms.openlocfilehash: c35d8efc9998aac5b40de833e5acbf7f80353e6b
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840139"
---
# <a name="spatial-anchors-in-unreal"></a>Raumanker in Unreal

Raumanker werden verwendet, um Hologramme zwischen Anwendungssitzungen im realen Raum beizubehalten.  Dies wird über Unreal mithilfe von „ARPins“ erreicht und für spätere Sitzungen im Ankerspeicher von HoloLens gespeichert. 

Vergewissern Sie sich vor dem Speichern oder Laden von Ankern zunächst, dass der Ankerspeicher bereit ist.  Wenn Sie versuchen, eine der HoloLens-Ankerfunktionen aufzurufen, bevor der Ankerspeicher bereit ist, ist der Aufruf nicht erfolgreich.  

![Raumanker: Speicher bereit](images/unreal-spatialanchors-store-ready.PNG)

## <a name="save-anchors"></a>Speichern von Ankern

Sobald die Anwendung über eine Komponente verfügt, die in der Umgebung fixiert werden muss, kann sie wie folgt im Ankerspeicher gespeichert werden: 

![Raumanker: Speichern](images/unreal-spatialanchors-save.PNG)

Hier erzeugen wir einen Akteur an einer bekannten Position und erstellen einen AR-Pin mit dieser Position sowie einen Namen, der auf der Klasse des Akteurs basiert. Außerdem fügen wir den Akteur dem AR-Pin hinzu und speichern den Pin im HoloLens-Ankerspeicher.  Da der gewählte Ankername eindeutig sein muss, wird in diesem Beispiel der aktuelle Zeitstempel angefügt.  Wenn der Anker erfolgreich im Ankerspeicher gespeichert wurde, kann er im HoloLens-Geräteportal unter „System“ > „Map manager“ (Zuordnungs-Manager) > „Anchor Files Saved On Device“ (Auf dem Gerät gespeicherte Ankerdateien) überprüft werden. 

## <a name="load-anchors"></a>Laden von Ankern

Beim Start einer Anwendung kann die folgende Blaupause aufgerufen werden, um Komponenten an ihren Ankerpositionen wiederherzustellen:

![Raumanker: Laden](images/unreal-spatialanchors-load.PNG)

In diesem Beispiel durchlaufen wir alle Anker im Ankerspeicher, erzeugen einen Akteur am neutralen Element und heften diesen Akteur an den AR-Pin aus dem Ankerspeicher an.  Es ist wichtig, den Akteur am neutralen Element zu erzeugen, da der Anker dazu dient, das Hologramm in der Umgebung auf der Grundlage des gespeicherten Orts zu positionieren, sodass jede hier hinzugefügte Transformation dem Anker ein Offset hinzufügt. 

Die Anker-ID wird ebenfalls abgefragt, um abhängig vom gespeicherten Namen des Ankers unterschiedliche Akteure erzeugen zu können. 

## <a name="remove-anchors"></a>Entfernen von Ankern 

Wenn Sie einen Anker nicht mehr benötigen, können Sie entweder den gesamten Ankerspeicher löschen oder einzelne Anker aus dem Ankerspeicher entfernen, damit sie in zukünftigen Sitzungen nicht mehr verwendet werden: 

![Raumanker: Entfernen](images/unreal-spatialanchors-remove.PNG)

## <a name="see-also"></a>Siehe auch
* [Raumanker](spatial-anchors.md)
* [Koordinatensysteme](coordinate-systems.md)
