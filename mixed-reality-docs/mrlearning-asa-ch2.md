---
title: MR Learning ASA-Modul Azure räumliche Anker für HoloLens 2
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: f8a52660fe05b6ed4508321ed246b8e299b75bca
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523333"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2. Speichern, abrufen und Freigeben von Azure räumliche Anker

In diesem Lernprogramm lernen wir unsere Azure räumliche Anker über mehrere appsitzungen hinweg zu sparen, indem Sie unsere Anchor-Informationen in die HoloLens-2-Datenträger gespeichert. Außerdem lernen wir, wie diese Anker-Informationen mit anderen Geräten für eine Multi-Device-Anchor-Ausrichtung freigegeben werden.

## <a name="objectives"></a>Ziele

* Erfahren Sie, wie zum Speichern und Abrufen von Azure räumliche Anchor-Informationen aus dem lokalen HoloLens-2-Datenträger, für die Dauerhaftigkeit zwischen app-Sitzungen

* Erfahren Sie, wie Azure räumliche Anchor-Informationen zwischen den Benutzern in einem Szenario mit mehreren Geräten gemeinsam nutzen

  

## <a name="instructions"></a>Anweisungen

### <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>Azure Anker zwischen App-Sitzungen - speichern Anker-ID auf dem Datenträger beibehalten

1. Suchen und das Prefab SaveAnchorToDisk zu Ihrer Szene hinzufügen. Dies schließt zwei Schaltflächen, eine Schaltfläche zum Speichern von alle verfügbaren Azure-Anker-IDs in die HoloLens-2-Datenträger und eine für alle IDs werden vom Datenträger abgerufen.

   ![module2chapter2step1im](images/module2chapter2step1im.PNG)

2. Jede Schaltfläche gemäß den Anweisungen unten "konfigurieren"
   - Erstellen Sie für die Schaltfläche mit dem Namen SaveToDisk ein neues Ereignis unter den Ereignistrigger gedrückt als auch den Ereignistrigger klicken Sie auf. Ziehen Sie das ParentAnchor-Objekt in das leere Feld ein, und weisen Sie die SaveAzureAnchorIDToDisk()-Methode des Objekts ParentAnchor ASAmoduleScript Komponente.
   
     > Hinweis: einige der Schaltflächen möglicherweise überlappen die anderen Schaltflächen in der Szene. Sie können der Schaltfläche positionieren.
   

  ![module2chapter2step2aim](images/module2chapter2step2aim.PNG)

![module2chapter2step2aim](images/module2chapter2step2bim.PNG)

![module2chapter2step2aim](images/module2chapter2step2cim.PNG)

   - Erstellen Sie für die Schaltfläche mit dem Namen GetFromDisk ein neues Ereignis unter den Ereignistrigger gedrückt als auch den Ereignistrigger klicken Sie auf. Ziehen Sie das ParentAnchor-Objekt in das leere Feld ein, und weisen Sie die LoadAzureAnchorIDsFromDisk()-Methode des Objekts ParentAnchor ASAmoduleScript Komponente.

3. Befolgen Sie die Anweisungen Tutoiral 1 fest, um die aktualisierte Anwendung auf Ihrem Gerät zu erstellen. Nach dem Drücken der Schaltfläche mit den Azure-Anker erstellen, wie in der vorherigen Lektion haben möglicherweise jetzt der Azure-Anker-ID auf dem Datenträger gespeichert werden durch Drücken des Speichervorgangs auf die Schaltfläche "Datenträger".

4. Starten Sie die Anwendung neu, starten Sie die Azure-Sitzung, drücken Sie die Last Anker-ID ein, und drücken Sie dann die suchen Azure Anker zum Suchen des Ankers verknüpft, die mit der ID auf dem Datenträger gespeichert ist. Die gesamte Szene ausgerichtet werden soll jetzt in Position, an der Position den Anker zuvor gespeicherte!

### <a name="share-azure-anchors-between-multiple-devices"></a>Freigeben von Azure-Anker zwischen mehreren Geräten

In diesem Abschnitt erfahren wir, wie der Azure-Anker-ID zwischen mehreren Geräten gemeinsam genutzt werden. Dadurch können mehrere Geräte zum Abfragen von Azure für die gleiche Anker-ID, sodass unsere verankerten Hologramme und Szenen räumlich ausgerichtet werden sollen. Räumlichen Ausrichtung (sehen die gleichen Hologramme in demselben physischen Standort von mehreren Geräten) ist, um einen lokalen freigegebenen Erfahrungen in der HoloLens-2. Es gibt viele Möglichkeiten zum Übertragen von Informationen in Bezug auf Azure-IDs von Geräten, einschließlich der Methoden in den freigegebenen Erfahrungen mit Azure räumliche Anker Tutorials (TODO: Link hinzufügen.) Dieses Beispiel verwendet einen einfachen Webdienst zum Hoch- und Herunterladen der Anker-IDs zwischen Geräten.

1. Fügen Sie das Prefab ShareAnchor in Ihrer Hierarchie hinzu. Diese Prefab fügt zwei neue Schaltflächen zu Ihrer Szene; eine für das Hochladen der Anker-ID-Informationen und eine für das Herunterladen von Anker-ID-Informationen. 

   ![module2chapter2step5im](images/module2chapter2step5im.PNG)

2. Jede Schaltfläche gemäß den Anweisungen unten "konfigurieren"

   - Erstellen Sie für die Schaltfläche mit dem Namen SendSharedAnchor ein neues Ereignis unter den Ereignistrigger gedrückt als auch den Ereignistrigger klicken Sie auf. Ziehen Sie das ParentAnchor-Objekt in das leere Feld ein, und weisen Sie die ShareAnchor()-Methode des Objekts ParentAnchor ASAmoduleScript Komponente.

     ![module2chapter2step6aim](images/module2chapter2step6aim.PNG)

     ![module2chapter2step6bim](images/module2chapter2step6bim.PNG)

     

   - Erstellen Sie für die Schaltfläche mit dem Namen GetSharedAnchor ein neues Ereignis unter den Ereignistrigger gedrückt als auch den Ereignistrigger klicken Sie auf. Ziehen Sie das ParentAnchor-Objekt in das leere Feld ein, und weisen Sie die GetSharedAzureAnchor()-Methode des Objekts ParentAnchor ASAmoduleScript Komponente.

3. Befolgen Sie die Anweisungen aus [Tutorial 1](mrlearning-base-ch1.md). um die aktualisierte Anwendung auf Ihrem Gerät zu erstellen. Nach Drücken der Schaltfläche mit den Azure-Anker erstellen, wie in der vorherigen Lektion können Sie jetzt der Anker-ID von Azure mit anderen Geräten freigeben durch Drücken der Schaltfläche zu anderen Gerät freigeben.

   > Hinweis: Wählen Sie den übergeordneten Anker und scrollen Sie zu das übergeordnete Anchor-Skript. Stellen Sie sicher, dass die öffentliche Freigabe Pin eindeutig ist, wenn Sie es freigeben, Sie wissen, dass ihr Konto ist, die Sie gemeinsam nutzen. Es kann Tausende von Benutzern, die ihre Azure-Anker, freigeben, damit auf diese Weise können Sie sicherstellen, dass Sie die richtigen Azure Anker freigegeben haben.

4. Wenn Sie ein anderes HoloLens-2-Gerät haben, starten Sie die Anwendung, und klicken Sie dann starten Sie die Azure-Sitzung. Drücken Sie die Schaltfläche "freigegebene Anker-ID abrufen", und drücken Sie dann auf die Schaltfläche "Suchen von Azure-Anker" zum Suchen des Ankers verknüpft, die mit der ID auf dem Datenträger gespeichert ist. Die gesamte Szene jetzt in der Position ausgerichtet werden soll an die Where sie auf der anderen HoloLens-2-Geräts abgelegt wurde. Wenn nur eine HoloLens-2 haben, können Sie dennoch testen Funktionalität durch einen Neustart der Anwendung Azure-Sitzung gestartet und drücken Sie dann die Schaltfläche mit den "Freigegebene Anker-ID abrufen" und drücken Sie die Azure-Anker Suchen-Schaltfläche, um der Anker suchen mit zugeordneten der Die ID, die auf dem Datenträger gespeichert. Die gesamte Szene ausgerichtet werden soll jetzt in Position, an der Position den Anker zuvor gespeicherte!

## <a name="congratulations"></a>Herzlichen Glückwunsch!
In dieser Lektion haben Sie gelernt, wie Azure räumliche Anker zwischen anwendungssitzungen und Neustarts der Anwendung beibehalten werden, durch Speichern der räumlichen Anker-ID von Azure auf dem lokalen Datenträger für HoloLens 2 wird. Außerdem haben Sie gelernt, mehrere Geräte für eine grundlegende mehrere Benutzer, statische – Hologramm freigegebene Benutzeroberfläche räumliche Anker Azure gemeinsam.

Erfahren Sie, wie Azure räumliche Anker als Teil der eine vollständig interaktive lokale freigegebene Benutzeroberfläche während der letzten Lektion des Moduls Freigabe zu implementieren. Eine lokale freigabeerfahrung herausgeberkontos ausgewiesenen Form Funktionen wie z. B. synchronisierten 3D-Objekt Position, Drehung und Skalierung, Bezeichner für jeden Benutzer und Anwendungsstatus freigegeben. Azure räumliche Anker verbessert diese freigegebenen Szenarios durch die Bereitstellung von jedem Teilnehmer mit ein common Anker, mit dem alle Benutzer, die virtuelle Objekte in demselben physischen Standort finden Sie unter. Dies gilt, auf einer Vielzahl von Plattformen, einschließlich HoloLens, Android und iOS-Geräte. Informationen zum Entwickeln einer gemeinsamen Erfahrung, schließen Sie alle Lektionen in diesem Modul für die Freigabe.

In der nächsten Lektion lernen wir, wie Sie Benutzern in Echtzeit Feedback bereitzustellen. Dieses Feedback enthalten Informationen zu den Anker erstellen, die Qualität der Umgebung verstehen und den Status der Azure-Sitzung. Ohne Feedback Benutzer wissen möglicherweise nicht, ob ein Anker Hochladen in Azure erfolgreich war, ob die Qualität der Umgebung ausreichend für Anker erstellen oder der aktuelle Zustand ist.

[Nächste Lektion: ASA Tutorial 3](mrlearning-asa-ch3.md)

