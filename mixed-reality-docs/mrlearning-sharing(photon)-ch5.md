---
title: Lernen die Freigabe-Modul für HoloLens 2 MR
description: Führen Sie diesen Kurs erfahren, wie Sie mehrere Benutzer freigegebene Umgebungen innerhalb einer HoloLens-2-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 2a16d318c6d749bcbf6ed9db0d6cd2228a6ea06e
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465204"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a>Azure räumliche Anker sowie veröffentlichte Erfahrungen

In dieser Lektion erfahren wir, wie Azure räumliche Anker (ASA) in unserem gemeinsamen Erfahrung zu integrieren. ASA kann mehrere zusammengestellten Geräte eine Referenz zu häufigen haben, wenn es sich bei ihrer physischen Umgebung zu virtuellen Umgebungen Anker ist, sodass alle Teilnehmer die Objekte in der gleichen physischen Ort finden Sie unter.

Bevor Sie mit dieser Lektion fortfahren müssen wir das ASA-Learning-Modul erfüllt werden, das darunter die ASA-Grundlagen, Azure-Konto und das Erstellen von Ressourcen und andere grundlegende Gebäude-Blöcke, die erforderlich sind, bevor wir in unserem gemeinsamen Erfahrung ASA integrieren beschrieben wird.

Ziele:

- Integrieren von ASA in einer gemeinsamen Erfahrung bei der Multi-Device-Ausrichtung
- Grundlagen der Funktionsweise von ASA im Rahmen einer gemeinsamen lokalen Erfahrung

### <a name="instructions"></a>Anweisungen

1. Speichern Sie das Projekt aus der vorherigen Lektion (STRG + S), und nennen Sie sie "HLSharedProjectMainPart5.unity", sodass es leichter zu finden, wenn Sie ihn wieder benötigen.

2. Wählen Sie das Prefab TableAnchor unterhalb des übergeordneten Objekts, MixedRealityPlayspace, und löschen Sie sie.

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)



3.  In der Projektansicht wechseln Sie zu den Ressourcen-Ressourcen > -> prefabs (Vorlagen) werden soll, und ziehen Sie das Prefab TableAnchor über das SharedPlayground-Objekt, das als untergeordnetes.
4.  Erweitern Sie die MixedRealityPlayspace übergeordnete-Objekt, das TableAnchor-Objekt, und auch das Schaltflächen-Objekt. 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. Wählen Sie jetzt in der Hierarchie ShareAzureAnchorButton, und verschieben Sie Ihre Aufmerksamkeit auf den Zugriffsbereich Inaspector. Scrollen Sie im Dropdown-Menü in der Abbildung unten dargestellt und wählen Sie AnchorModuleScript aus, und klicken Sie auf ShareAnchorNetework().

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. Wählen Sie GetAzureAnchorButton (siehe Schritt 4), und verschieben Sie Ihre Aufmerksamkeit an den Bereich der Eigenschaftenanalyse. Scrollen Sie im Dropdown-Menü in der Abbildung unten dargestellt und wählen Sie AnchorModuleScript aus, und klicken Sie auf GetSharedAnchorNetwork(), und speichern.

![Module3hapter5step7im](images/module3chapter5step7im.PNG)




## <a name="congratulations"></a>Herzlichen Glückwunsch!

In dieser Lektion haben Sie gelernt, wie Sie Azure leistungsfähige neue räumliche Anker zum Ausrichten von zusammengestellten Geräte in einer freigegebenen Umgebung zu integrieren. In dieser Lektion wird auch das Modul Freigabe abgeschlossen. Wir haben gelernt, wie zum Einrichten eines neuen Photon-Kontos integrieren Photon und WORTSPIEL in einer neuen Unity-Anwendung, Profilbild und freigegebene Objekte konfigurieren und schließlich Ausrichten von mehreren Beteiligten mit ASA. 

