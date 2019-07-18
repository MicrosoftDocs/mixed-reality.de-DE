---
title: Mr Learning Sharing Module für hololens 2
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Umgebungen mit mehreren Benutzern in einer hololens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 1ae880208e79e2e045bd5e7298db260b7f0b2232
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293628"
---
# <a name="azure-spatial-anchors-and-shared-experiences"></a>Räumliche Azure-Anker und gemeinsame Nutzung

In dieser Lektion erfahren Sie, wie Sie Azure Spatial Anchor (ASA) in unsere freigegebene Erfahrung integrieren. ASA ermöglicht es, dass mehrere zusammengestellte Geräte über einen allgemeinen Verweis verfügen, wenn ihre physische Umgebung darin besteht, virtuelle Oberflächen so zu verankern, dass alle Teilnehmer Objekte am gleichen physischen Speicherort sehen.

Bevor Sie mit dieser Lektion fortfahren, müssen wir das ASA-Lernmodul ausführen, das die ASA-Grundlagen, die Erstellung von Azure-Konten und-Ressourcen und andere grundlegende Bausteine behandelt, die erforderlich sind, bevor wir ASA in unsere freigegebene Erfahrung integrieren können.

Ziele

- Integrieren Sie ASA in eine freigegebene Darstellung für die Ausrichtung auf mehrere Geräte.
- Lernen Sie die Grundlagen der Funktionsweise von ASA im Kontext einer lokalen gemeinsamen Umgebung kennen.

### <a name="instructions"></a>Anweisungen

1. Speichern Sie das Projekt aus der vorherigen Lektion (Control + S), und nennen Sie es "HLSharedProjectMainPart5. unity", damit es leichter zu finden ist, wenn Sie es erneut benötigen.

2. Wählen Sie unter dem übergeordneten Element mixedrealityplayspace das vorfab tableanchor aus, und löschen Sie es.

![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

3.  Wechseln Sie in der Projektansicht zu Assets-> Resources-> Prefabs, und ziehen Sie das tableanchor-präfab oberhalb des sharedplayground-Objekts, um es als untergeordnetes Element festzulegen.
4.  Erweitern Sie das übergeordnete Objekt mixedrealityplayspace, das tableanchor-Objekt, und erweitern Sie auch das Schaltflächen Objekt. 

![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. Wählen Sie nun in der Hierarchie shareazureanchorbutton aus, und verschieben Sie Ihre Aufmerksamkeit auf den Bereich "inaspector". Scrollen Sie nach unten zum Dropdown Menü, das in der folgenden Abbildung dargestellt ist, und wählen Sie anchormodulescript aus, und klicken Sie auf shareanchornetework ().

![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. Wählen Sie getazureanchorbutton aus (siehe Schritt 4), und verschieben Sie die Aufmerksamkeit zurück zum Inspektor-Panel. Scrollen Sie nach unten zum Dropdown Menü, das in der folgenden Abbildung dargestellt ist, und wählen Sie anchormodulescript aus, und klicken Sie auf getsharedanchornetwork () und dann auf speichern.

![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. Um das Freigabe Modul zu testen, klicken Sie auf die Schaltfläche "Azure-ASA-Sitzung starten", die die Azure-Sitzung für räumliche Anker startet, und erstellen Sie dann den Azure-Anker, indem Sie auf die Schaltfläche "Azure-Anker erstellen" klicken und warten, bis der Azure-Anker erstellt wird Nachdem der Azure-Anker erstellt wurde, klicken Sie auf die Schaltfläche "Azure-Anker freigeben", um den erstellten Azure-Anker aus den hololens zu teilen.

7. Um den freigegebenen Azure-Anker in einem anderen hololens zu erhalten, klicken Sie auf "Azure ASA-Sitzung starten", um die aktuelle ASA-Sitzung zu starten, und klicken Sie auf die Schaltfläche "Get Azure Anchor", um den freigegebenen Azure-Anker aus den anderen hololens zu erhalten.

   > Hinweis: Alle Details der entsprechenden Aktionen auf den einzelnen Schaltflächen werden im Debugfenster angezeigt.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In dieser Lektion haben Sie erfahren, wie Sie die leistungsfähigen neuen räumlichen Anker von Azure integrieren, um zusammengestellte Geräte in einer freigegebenen Erfahrung auszurichten. Diese Lektion schließt auch das Freigabe Modul ein. Wir haben gelernt, wie Sie ein neues Photon-Konto einrichten, die Verwendung von Photon und pun in eine neue Unity-Anwendung, das Konfigurieren von Avatare und freigegebenen Objekten und schließlich das Ausrichten mehrerer Teilnehmer mithilfe von ASA. 

