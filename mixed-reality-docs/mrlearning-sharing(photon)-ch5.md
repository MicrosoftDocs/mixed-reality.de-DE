---
title: Lernen die Freigabe-Modul für HoloLens 2 MR
description: Führen Sie diesen Kurs erfahren, wie Sie mehrere Benutzer freigegebene Umgebungen innerhalb einer HoloLens-2-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 9f4a0c0cc37ab097a60c44891d56fa65f6032418
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326945"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a>Azure räumliche Anker sowie veröffentlichte Erfahrungen

In dieser Lektion lernen wir, wie Sie Azure räumliche Anker (ASA) in unserem gemeinsamen Erfahrung zu integrieren. ASA kann mehrere zusammengestellten Geräte ein gemeinsames Verständnis ihrer physischen Umgebung aus, um die virtuellen Verankern durchgeführter so, dass alle Teilnehmer Objekte in der gleichen physischen Ort zu haben.

Bevor Sie mit dieser Lektion fortfahren müssen wir das ASA-Learning-Modul erfüllt werden, darunter die ASA-Grundlagen, Azure-Konto und das Erstellen von Ressourcen und andere grundlegende Gebäude-Blöcke, die erforderlich sind, bevor wir in unserem gemeinsamen Erfahrung ASA integrieren beschrieben wird.

Ziele:

- Integrieren von ASA in einer gemeinsamen Erfahrung bei der Multi-Device-Ausrichtung
- Grundlagen der Funktionsweise von ASA im Rahmen einer gemeinsamen lokalen Erfahrung

### <a name="instructions"></a>Anweisungen

1. Speichern Sie das Projekt aus der vorherigen Lektion (STRG + S), und nennen Sie sie "HLSharedProjectMainPart5.unity", sodass es leichter zu finden, wenn Sie ihn wieder benötigen.

2. Wählen Sie das Prefab TableAnchor unterhalb des übergeordneten Objekts, "MixedRealityPlayspace", und löschen Sie sie.

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3. Genau wie einige der vorherigen Lektionen, importieren Sie ein neues benutzerdefiniertes Paket, das sollte man [hier.](placeholderlink)

![Module3Chapter5step3im](images/module3chapter5step3im.PNG)

4. Nach dem Importieren, ziehen Sie den neu aktualisierte Tabelle Anker (aus dem Unity-Paket, das im vorherigen Schritt importiert) aus dem Ordner "Prefabs" im Projektfenster, und legen Sie es in das übergeordnete Objekt "MixedRealityPlayspace."

![Module3hapter5step4im](images/module3chapter5step4im.PNG)

5. Erweitern Sie das übergeordnete Objekt von "MixedRealityPlayspace", und klicken Sie dann auf das Objekt "TableAnchor", und auch das "Schaltflächen"-Objekt. 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

6. Wählen Sie jetzt in der Hierarchie, die "ShareAzureAnchorButton" und verschieben Sie Ihre Aufmerksamkeit auf den Bereich der Eigenschaftenanalyse. Scrollen Sie im Dropdownmenü mit den in der Abbildung unten dargestellt, und wählen Sie "AnchorModuleScript", und klicken Sie auf "ShareAnchorNetework()."

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

7. Ähnlich wie Schritt 6 Wählen Sie die "GetAzureAnchorButton" aus, und verschieben Sie Ihre Aufmerksamkeit an den Bereich der Eigenschaftenanalyse. Scrollen Sie im Dropdownmenü mit den in der Abbildung unten dargestellt, und wählen Sie "AnchorModuleScript", und klicken Sie auf "GetSharedAnchorNetwork()." Klicken Sie dann zu speichern.

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a>Herzlichen Glückwunsch!

In dieser Lektion haben Sie gelernt, wie Sie Azure leistungsfähige neue räumliche Anker zum Ausrichten von zusammengestellten Geräte in einer freigegebenen Umgebung zu integrieren. In dieser Lektion wird auch das Modul Freigabe abgeschlossen. Wir haben gelernt, wie zum Einrichten eines neuen Photon-Kontos integrieren Photon und WORTSPIEL in einer neuen Unity-Anwendung, Profilbild und freigegebene Objekte konfigurieren und schließlich Ausrichten von mehreren Beteiligten mit ASA. 

