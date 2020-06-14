---
title: Räumliche Abbildung in Unreal
description: Leitfaden für die Verwendung der räumlichen Abbildung in Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, räumliche Abbildung
ms.openlocfilehash: 2bbfc3972acdb9dc7d5ebd23c85ab0ef5532cfb9
ms.sourcegitcommit: ee7f04148d3608b0284c59e33b394a67f0934255
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84428773"
---
# <a name="spatial-mapping-in-unreal"></a>Räumliche Abbildung in Unreal

## <a name="overview"></a>Übersicht
Die räumliche Abbildung ermöglicht es, durch Anzeigen der die HoloLens umgebenden Welt Objekte auf Oberflächen in der physischen Welt zu platzieren. Dadurch erscheinen Hologramme für den Benutzer realer. Die räumliche Abbildung verankert darüber hinaus Objekte in der Welt des Benutzers und nutzt dazu Tiefeninformationen der realen Welt. Dies hilft dabei, den Benutzer zu überzeugen, dass sich die betreffenden Hologramme tatsächlich in seinem Bereich befinden; frei im Raum schwebende oder sich mit dem Benutzer bewegende Hologramme fühlen sich weniger real an. Wann immer es möglich ist, sollten Sie Elemente platzieren, um das Wohlbefinden des Benutzers zu steigern.

Weitere Informationen zur Qualität der räumlichen Abbildung, Platzierung, Verdeckung, Rendering und mehr finden Sie im Dokument [Räumliche Abbildung](spatial-mapping.md).

## <a name="enabling-spatial-mapping"></a>Aktivieren der räumlichen Abbildung

So aktivieren Sie die räumliche Abbildung in HoloLens:
- Öffnen Sie **Edit > Project Settings** (Bearbeiten > Projekteinstellungen), und scrollen Sie zum Abschnitt **Platforms** (Plattformen) herunter.    
    + Wählen Sie **HoloLens** aus, und aktivieren Sie **Spatial Perception** (Räumliche Wahrnehmung).

So abonnieren Sie räumliche Abbildung und debuggen das **MRMesh** in einem HoloLens-Spiel:
1. Öffnen Sie die **ARSessionConfig**, und klappen Sie den Abschnitt **ARSettings > World Mapping** (Weltdarstellung) auf. 

2. Aktivieren Sie **Generate Mesh Data from Tracked Geometry** (Daten des Gittermodells auf der Grundlage der nachverfolgten Geometrie generieren), wodurch das HoloLens-Plug-In angewiesen wird, mit dem asynchronen Abrufen von räumlichen Abbildungsdaten und ihrer Oberflächenzuordnung in Unreal mithilfe von **MRMesh** zu beginnen. 
3. Aktivieren Sie **Render Mesh Data in Wireframe** (Gittermodelldaten im Drahtmodell rendern), um einen weißen Drahtmodellumriss jedes Dreiecks im **MRMesh** darzustellen. 

![Raumanker: Speicher bereit](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a>Räumliche Abbildung zur Laufzeit
Sie können die folgenden Parameter ändern, um das Laufzeitverhalten der räumlichen Abbildung zu ändern:

- Öffnen Sie **Edit > Project Settings** (Bearbeiten > Projekteinstellungen), scrollen Sie nach unten zum Abschnitt **Platforms** (Plattformen), und wählen Sie **HoloLens > Spatial Mapping** (HoloLens > Räumliche Abbildung) aus: 

![Raumanker: Projekteinstellungen](images/unreal-spatialmapping-projectsettings.PNG)

- **Max Triangles Per Cubic Meter** (Maximale Anzahl von Dreiecken pro Kubikmeter) dient zum Aktualisieren der Dichte der Dreiecke im Gitter der räumlichen Abbildung.  
- **Spatial Meshing Volume Size** (Volumengröße des räumlichen Gitters) dient zum Angeben der Größe des Würfels, der den Spieler umgibt, um Daten der räumlichen Abbildung zu rendern und zu aktualisieren.  
    + Im Falle einer großen Anwendungslaufzeitumgebung muss dieser Wert ggf. hoch sein, um dem realen Raum gerecht zu werden.  Dagegen kann dieser Wert kleiner sein, wenn die Anwendung lediglich Hologramme auf Oberflächen in der unmittelbareren Umgebung des Benutzers platzieren muss. Wenn sich der Benutzer in der Umgebung bewegt, bewegt sich das Volumen der räumlichen Abbildung mit ihm mit. 

## <a name="working-with-mrmesh"></a>Arbeiten mit MRMesh
So erhalten Sie zur Laufzeit Zugriff auf das **MRMesh**:
1. Fügen Sie einem Blaupausenakteur eine **ARTrackableNotify**-Komponente hinzu. 

![Raumanker: In AR nachverfolgbare Benachrichtigung](images/unreal-spatialmapping-artrackablenotify.PNG)

2. Wählen Sie die **ARTrackableNotify**-Komponente aus, und klappen Sie im Bereich **Details** den Abschnitt **Events** (Ereignisse) auf. 
    - Klicken Sie auf die Schaltfläche **+** für die Ereignisse, die Sie überwachen möchten. 

![Raumanker: Ereignisse](images/unreal-spatialmapping-events.PNG)

In diesem Fall wird das Ereignis **On Add Tracked Geometry** überwacht, das nach gültigen Gittermodellen der Realumgebung sucht, die mit Daten der räumlichen Abbildung übereinstimmen. Die vollständige Liste der Ereignisse finden Sie in der Komponenten-API [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html). 

Sie können das Material des Gittermodells im Ereignisdiagramm der Blaupause oder in C++ ändern. Auf dem Screenshot unten ist die Route der Blaupause dargestellt: 

![Raumanker: Beispiel](images/unreal-spatialmapping-example.PNG)

In C++ können Sie den `OnTrackableAdded`-Delegat abonnieren, um die `ARTrackedGeometry` abzurufen, sobald sie verfügbar ist, wie im Code unten zu sehen. 

> [!IMPORTANT]
> Die build.cs-Datei des Projekts **MUSS** **AugmentedReality** in der Liste **PublicDependencyModuleNames** aufweisen.
> - Dies schließt **ARBlueprintLibrary.h** und **MRMeshComponent.h** ein, mit deren Hilfe Sie die **MRMesh**-Komponente von **UARTrackedGeometry** untersuchen können. 

![Raumanker: C++-Beispielcode](images/unreal-spatialmapping-examplecode.PNG)

Räumliche Abbildung ist nicht der einzige Datentyp, der mithilfe von **ARTrackedGeometries** dargestellt wird. Sie können überprüfen, ob `EARObjectClassification` den Wert `World` aufweist, was bedeutet, dass es sich um Geometriedaten der räumlichen Abbildung handelt. 

Für Aktualisierungs- und Entfernungsereignisse stehen ähnliche Delegaten zur Verfügung: 
- `AddOnTrackableUpdatedDelegate_Handle` 
- `AddOnTrackableRemovedDelegate_Handle`. 

Die vollständige Liste der Ereignisse finden Sie in der Komponenten-API [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html).

## <a name="see-also"></a>Siehe auch
* [Räumliche Abbildung](spatial-mapping.md)
