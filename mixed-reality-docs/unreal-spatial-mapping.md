---
title: Räumliche Abbildung in Unreal
description: Leitfaden für die Verwendung der räumlichen Abbildung in Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, räumliche Abbildung
ms.openlocfilehash: 32f8247010745b23bf73c5161c378bc1284169ef
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840079"
---
# <a name="spatial-mapping-in-unreal"></a>Räumliche Abbildung in Unreal

Im Unreal-Editor muss unter „Project Settings“ (Projekteinstellungen) > „Platform“ (Plattform) > „HoloLens“ > „Capabilities“ (Funktionen) die Funktion für die räumliche Wahrnehmung (Spatial Perception) aktiviert sein, um die räumliche Abbildung für HoloLens verwenden zu können.  

Wenn Sie die räumliche Abbildung in einem HoloLens-Spiel verwenden möchten, aktivieren Sie in „ARSessionConfig“ die Option „Generate Mesh Data from Tracked Geometry“ (Gitterdaten auf der Grundlage der nachverfolgten Geometrie generieren).  Daraufhin werden vom HoloLens-Plug-In asynchron räumliche Abbildungsdaten abgerufen und über „MRMesh“ für Unreal verfügbar gemacht. 

![Raumanker: Speicher bereit](images/unreal-spatialmapping-arsettings.PNG)

Aktivieren Sie zum Anzeigen einer Debugvisualisierung des Gitters der räumlichen Abbildung das Kontrollkästchen „Render Mesh Data in Wireframe“ (Gitterdaten in Drahtmodell rendern) in „ARSessionConfig“, um eine weiße Drahtmodellkontur jedes Dreiecks in „MRMesh“ anzuzeigen. 

Unter „Project Settings“ (Projekteinstellungen) > „Platform“ (Plattform) > „HoloLens“ > „Spatial Mapping“ (Räumliche Abbildung) können folgende Parameter geändert werden, um das Laufzeitverhalten der räumlichen Abbildung zu aktualisieren: 

![Raumanker: Projekteinstellungen](images/unreal-spatialmapping-projectsettings.PNG)

„Max Triangles Per Cubic Meter“ (Maximale Anzahl von Dreiecken pro Kubikmeter) dient zum Aktualisieren der Dichte der Dreiecke im Gitter der räumlichen Abbildung.  „Spatial Meshing Volume Size“ (Volumengröße des räumlichen Gitters) dient zum Angeben der Größe des Würfels, der den Spieler umgibt, um Daten der räumlichen Abbildung zu rendern und zu aktualisieren.  Im Falle einer großen Anwendungslaufzeitumgebung muss der Wert in diesem Feld ggf. hoch sein, um dem realen Raum gerecht zu werden.  Müssen von der Anwendung dagegen lediglich Hologramme auf Oberflächen in der unmittelbareren Umgebung des Benutzers platziert werden, kann in diesem Feld ein niedrigerer Wert verwendet werden.  Wenn sich der Benutzer in der Umgebung bewegt, bewegt sich das Volumen der räumlichen Abbildung mit ihm mit. 

Um zur Laufzeit auf „MRMesh“ zugreifen zu können, fügen Sie zunächst einem Blaupausenakteur eine in AR nachverfolgbare Benachrichtigungskomponente hinzu: 

![Raumanker: In AR nachverfolgbare Benachrichtigung](images/unreal-spatialmapping-artrackablenotify.PNG)

Navigieren Sie dann zu den Details der Komponente, und klicken Sie auf die grüne Plusschaltfläche (+) für die zu überwachenden Ereignisse. 

![Raumanker: Ereignisse](images/unreal-spatialmapping-events.PNG)

In diesem Fall überwachen wir das Ereignis „On Add Tracked Geometry“ (Beim Hinzufügen von nachverfolgter Geometrie), um nach gültigen Weltgittern zu suchen, die Daten der räumlichen Abbildung entsprechen, und ändern das Material des Gitters: 

![Raumanker: Beispiel](images/unreal-spatialmapping-example.PNG)

In C++ kann der Delegat „OnTrackableAdded“ abonniert werden, um die in AR nachverfolgte Geometrie (ARTrackedGeometry) abzurufen, sobald sie verfügbar ist.  Für Aktualisierungs- und Entfernungsereignisse stehen ähnliche Delegaten zur Verfügung: „AddOnTrackableUpdatedDelegate_Handle“ und „AddOnTrackableRemovedDelegate_Handle“. 

![Raumanker: C++-Beispielcode](images/unreal-spatialmapping-examplecode.PNG)

„build.cs“ des Projekts muss „AugmentedReality“ in der Liste „PublicDependencyModuleNames“ enthalten, um „ARBlueprintLibrary.h“ und „MRMesh“ für die Untersuchung der MRMesh-Komponente von „UARTrackedGeometry“ einzuschließen. 

Da die räumliche Abbildung nicht der einzige Datentyp ist, der über „ARTrackedGeometries“ verfügbar gemacht wird, vergewissern wir uns zunächst, dass „EARObjectClassification“ auf „World“ festgelegt ist. Dadurch wird angegeben, dass es sich hierbei um eine Geometrie der räumlichen Abbildung handelt. 

## <a name="see-also"></a>Siehe auch
* [Räumliche Abbildung](spatial-mapping.md)
