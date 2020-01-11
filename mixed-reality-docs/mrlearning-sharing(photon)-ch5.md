---
title: Lernprogramme für Mehrbenutzerfunktionen-5. Integrieren von Azure Spatial Anchor in eine gemeinsame Nutzung
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Umgebungen mit mehreren Benutzern in einer hololens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: a3b136023b0beea7cf6eecd52a9a21447576d482
ms.sourcegitcommit: 2bfe9b1af4ee2cc0d668caeccb8ebc3137cbc20b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901467"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a>5. integrieren von Azure Spatial Anchor in eine freigegebene Darstellung

In dieser Lektion erfahren Sie, wie Sie Azure Spatial Anchor (ASA) in unsere freigegebene Erfahrung integrieren. ASA ermöglicht es, dass mehrere zusammengestellte Geräte über einen allgemeinen Verweis verfügen, wenn ihre physische Umgebung darin besteht, virtuelle Oberflächen so zu verankern, dass alle Teilnehmer Objekte am gleichen physischen Speicherort sehen.

## <a name="objectives"></a>Ziele

* Integrieren Sie ASA in eine freigegebene Darstellung für die Ausrichtung auf mehrere Geräte.
* Lernen Sie die Grundlagen der Funktionsweise von ASA im Kontext einer lokalen gemeinsamen Umgebung kennen.

## <a name="instructions"></a>Anweisungen

1. Wählen Sie unter dem übergeordneten Element mixedrealityplayspace das vorfab tableanchor aus, und löschen Sie es.

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. Wechseln Sie in der Projektansicht zu Assets-> Resources-> Prefabs, und ziehen Sie das tableanchor-präfab oberhalb des sharedplayground-Objekts, um es als untergeordnetes Element festzulegen.

3. Erweitern Sie das übergeordnete Objekt mixedrealityplayspace, das tableanchor-Objekt, und erweitern Sie auch das Schaltflächen Objekt.

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. Wählen Sie nun in der Hierarchie shareazureanchorbutton aus, und verschieben Sie Ihre Aufmerksamkeit auf den Inspektor-Bereich. Scrollen Sie nach unten zum Dropdown Menü, das in der folgenden Abbildung dargestellt ist, wählen Sie anchormodulescript aus, und klicken Sie auf shareanchornetwork ().

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. Wählen Sie getazureanchorbutton aus (siehe Schritt 4), und verschieben Sie Ihre Aufmerksamkeit zurück zum Inspektor-Panel. Scrollen Sie nach unten zum Dropdown Menü, das in der folgenden Abbildung angezeigt wird, wählen Sie anchormodulescript aus, klicken Sie auf getsharedanchornetwork () und dann auf speichern.

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. Um das Freigabe Modul zu testen, klicken Sie auf die Schaltfläche "Azure ASA-Sitzung starten", die die Azure-Sitzung für räumliche Anker startet, und erstellen Sie dann den Azure-Anker durch Klicken auf die Schaltfläche "Azure-Anker erstellen" Warten Sie, bis der Azure-Anker erstellt wurde. Nachdem der Azure-Anker erstellt wurde, klicken Sie auf die Schaltfläche "Azure-Anker freigeben", um den erstellten Azure-Anker aus den hololens zu teilen.

7. Um den gemeinsam genutzten Azure-Anker in einem anderen hololens zu erhalten, klicken Sie auf die "Azure ASA-Sitzung starten", um zu beginnen und zur aktuellen ASA-Sitzung zu gelangen.

8. Klicken Sie auf die Schaltfläche "Azure-Anker erhalten", um den freigegebenen Azure-Anker aus den anderen hololens zu erhalten.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In dieser Lektion haben Sie gelernt, wie Sie die leistungsstarken neuen räumlichen Anker von Azure integrieren, um zusammengestellte Geräte in einer freigegebenen Erfahrung auszurichten. Dies schließt auch das Freigabe Modul ein. Wir haben gelernt, wie Sie ein neues Photon-Konto einrichten, die Verwendung von Photon und pun in eine neue Unity-Anwendung, das Konfigurieren von Avatare und freigegebenen Objekten und schließlich das Ausrichten mehrerer Teilnehmer mithilfe von ASA.
