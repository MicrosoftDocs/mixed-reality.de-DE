---
title: Mr Learning ASA-Modul Azure Spatial Anchor on hololens 2
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: b263d30905c5a1ba81bfb59ba6a49c7710c43869
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485740"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2. Speichern, abrufen und Freigeben von räumlichen Azure-Ankern

In diesem Tutorial erfahren Sie, wie Sie unsere räumlichen Azure-Anker in mehreren App-Sitzungen speichern, indem Sie die Anker Informationen auf dem Datenträger von hololens 2 speichern. Außerdem erfahren Sie, wie Sie diese Anker Informationen für eine Ausrichtung auf mehrere Geräte verankern für andere Geräte freigeben.

## <a name="objectives"></a>Ziele

* Erfahren Sie, wie Sie Informationen zum räumlichen Azure-Anker aus dem lokalen Datenträger hololens 2 speichern und für die Persistenz zwischen App-Sitzungen abrufen.

* Erfahren Sie, wie Sie Azure Spatial Anchor-Informationen zwischen Benutzern in einem Szenario mit mehreren Geräten freigeben.

## <a name="instructions"></a>Anweisungen

### <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>Beibehalten von Azure-Ankern zwischen App-Sitzungen: Anker-ID auf Datenträger speichern

1. Suchen Sie nach der vorfab saveanchoresdisk, und fügen Sie Sie Ihrer Szene hinzu. Hierzu gehören zwei Schaltflächen, eine Schaltfläche zum Speichern sämtlicher verfügbarer Azure-Anker-IDs auf dem Datenträger hololens 2 und eine weitere zum Abrufen von IDs vom Datenträger.

![module2chapter2step1im](images/module2chapter2step1im.PNG)

2. Konfigurieren Sie jede Schaltfläche gemäß den folgenden Anweisungen.

   - Erstellen Sie für die Schaltfläche mit dem Namen saveondisk ein neues Ereignis unter dem Tastendruck-Ereignis-und dem Click-Ereignis-auslöst. Ziehen Sie das Objekt "objeanchor" in das leere Feld, und weisen Sie die saveazureanchoriddedisk ()-Methode aus der asamodulescript-Komponente des Objektanker Objekts zu.
   
     > Hinweis: einige der Schaltflächen werden möglicherweise überlappen, die anderen Schaltflächen in der Szene. Sie können die Positionierung der Schaltfläche anpassen.

![module2chapter2step2aim](images/module2chapter2step2aim.PNG)

![module2chapter2step2aim](images/module2chapter2step2bim.PNG)

![module2chapter2step2aim](images/module2chapter2step2cim.PNG)


   - Erstellen Sie für die Schaltfläche getfromdisk ein neues Ereignis sowohl unter dem Schaltflächen-gedrückten Ereignis-als auch auf dem Click-Ereignis-Auslösers. Ziehen Sie das Objekt "objeanchor" in das leere Feld, und weisen Sie die Methode "loadazureanchoridsfromdisk ()" aus der Komponente "asamodulescript" des Objekts "Objektanchor" zu.

3. Befolgen Sie die Anweisungen von tuum 1, um die aktualisierte Anwendung auf Ihrem Gerät zu erstellen. Nachdem Sie die Schaltfläche Azure Anchor erstellen wie in der vorherigen Lektion gedrückt haben, können Sie die Azure-Anker-ID jetzt auf dem Datenträger speichern, indem Sie die Schaltfläche auf Datenträger speichern drücken.

4. Starten Sie die Anwendung neu, starten Sie die Azure-Sitzung, klicken Sie auf Anker-ID laden, und klicken Sie dann auf Azure-Anker suchen, um den Anker zu suchen, der der ID zugeordnet ist, die wir Die gesamte Szene sollte nun an der Position, an der Sie den Anker zuvor gespeichert haben, an der Position andocken.

### <a name="share-azure-anchors-between-multiple-devices"></a>Freigeben von Azure-Ankern für mehrere Geräte

In diesem Abschnitt erfahren Sie, wie Sie die Azure-Anker-ID für mehrere Geräte freigeben. Dies ermöglicht es mehreren Geräten, Azure nach der gleichen Anker-ID abzufragen, sodass die verankerten Hologramme und Szenen räumlich ausgerichtet werden können. Die räumliche Ausrichtung (das sehen der gleichen holograms am gleichen physischen Standort zwischen mehreren Geräten) ist der Schlüssel für die lokale gemeinsame Nutzung in den hololens 2. Es gibt viele Methoden zum Übertragen von Informationen in Bezug auf Azure-IDs zwischen Geräten, einschließlich der Methoden, die in den Azure Spatial Anchor-Lernprogrammen (TODO: Add Link) beschrieben werden. In diesem Beispiel wird ein einfacher Webdienst zum Hochladen und Herunterladen von Anker-IDs zwischen Geräten verwendet.

1. Fügen Sie der-Hierarchie den Share Anchor-präfab hinzu. Diese Prefab fügt Ihrer Szene zwei neue Schaltflächen hinzu. eine zum Hochladen von Anker-ID-Informationen und eine weitere zum Herunterladen der Anker-ID 

![module2chapter2step5im](images/module2chapter2step5im.PNG)

2. Konfigurieren Sie jede Schaltfläche gemäß den folgenden Anweisungen.

   - Erstellen Sie für die Schaltfläche sendsharedanchor ein neues Ereignis unter dem gedrückten Ereignis-und aktivierten Ereignis-Auslösers. Ziehen Sie das Objekt "objeanchor" in das leere Feld, und weisen Sie die shareanchor ()-Methode aus der asamodulescript-Komponente des Objektanchor-Objekts zu.

![module2chapter2step6aim](images/module2chapter2step6aim.PNG)

![module2chapter2step6bim](images/module2chapter2step6bim.PNG)

   - Erstellen Sie für die Schaltfläche getsharedanchor ein neues Ereignis unter dem Befehl Schaltfläche mit gedrücktem Ereignis und dem Click-Ereignis auslöst. Ziehen Sie das Objekt "objeanchor" in das leere Feld, und weisen Sie die Methode "getsharedazureanchor ()" aus der Komponente "asamodulescript" des Objekts "Objektanchor" zu.

3. Befolgen Sie die Anweisungen im [Tutorial 1](mrlearning-base-ch1.md). zum Erstellen der aktualisierten Anwendung auf Ihrem Gerät. Nachdem Sie die Schaltfläche Azure Anchor erstellen wie in der vorherigen Lektion gedrückt haben, können Sie nun die Azure-Anker-ID für andere Geräte freigeben, indem Sie die Schaltfläche auf anderes Gerät freigeben drücken.

   > Hinweis: Wählen Sie den übergeordneten Anker aus, und Scrollen Sie nach unten zum übergeordneten Anker Skript. Stellen Sie sicher, dass ihre öffentliche Freigabe-Pin eindeutig ist, sodass Sie, wenn Sie Sie freigeben, wissen, dass Sie die Freigabe haben. Es könnten tausende von Benutzern geben, die ihre Azure-Anker gemeinsam nutzen. Dadurch können Sie sicherstellen, dass Sie die richtigen Azure-Anker gemeinsam nutzen.

4. Wenn Sie ein anderes hololens 2-Gerät haben, starten Sie die Anwendung, und starten Sie dann die Azure-Sitzung. Klicken Sie auf die Schaltfläche "freigegebene Anker-ID", und klicken Sie dann auf die Schaltfläche "Azure-Anker suchen", um den Anker zu suchen, der der ID zugeordnet ist Die gesamte Szene sollte nun an der Position, an der Sie auf dem anderen hololens 2-Gerät platziert wurde, an der Position andocken. Wenn Sie nur über ein hololens 2 verfügen, können Sie die Funktionalität weiterhin testen, indem Sie die Anwendung neu starten, die Azure-Sitzung starten und dann die Schaltfläche "freigegebene Anker-ID erhalten" drücken und dann auf die Schaltfläche "Azure-Anker suchen" klicken, um den Anker zu suchen, der dem ID, die auf dem Datenträger gespeichert wurde. Die gesamte Szene sollte nun an der Position, an der Sie den Anker zuvor gespeichert haben, an der Position andocken.

## <a name="congratulations"></a>Herzlichen Glückwunsch!
In dieser Lektion haben Sie erfahren, wie Sie räumliche Azure-Anker zwischen Anwendungs Sitzungen und Anwendungs Neustarts beibehalten, indem Sie die räumliche Azure-Anker-ID auf dem lokalen Datenträger auf hololens 2 speichern. Außerdem haben Sie erfahren, wie Sie räumliche Azure-Anker zwischen mehreren Geräten für eine grundlegende freigegebene multibenutzerbenutzerfunktion mit mehreren Benutzern freigeben.

Wir erfahren, wie Sie räumliche Azure-Anker im Rahmen einer vollständig interaktiven, freigegebenen Umgebung in der letzten Lektion des Freigabe Moduls implementieren. Eine lokale Freigabe kann Funktionen wie die synchronisierte 3D-Objektposition,-Rotation und-Skalierung, Bezeichner für jeden Benutzer und den Status der freigegebenen Anwendungen enthalten. Azure Spatial Anchor erweitert diese freigegebenen Szenarien, indem jeder Teilnehmer einen gemeinsamen Anker bereitstellt, mit dem alle Benutzer virtuelle Objekte am gleichen physischen Speicherort sehen können. Dies gilt für verschiedene Geräte Plattformen, einschließlich hololens-, Android-und IOS-Geräten. Um zu erfahren, wie Sie eine freigegebene Darstellung entwickeln, vervollständigen Sie alle Lektionen im Freigabe Modul.

In der nächsten Lektion erfahren Sie, wie Sie Benutzern Echtzeitfeedback bereitstellen. Dieses Feedback enthält Informationen zur Anker Erstellung, zur Qualität des Verständnisses der Umgebung und zum Status der Azure-Sitzung. Ohne Feedback wissen Benutzer möglicherweise nicht, ob ein Anker erfolgreich in Azure hochgeladen wurde, ob die Qualität der Umgebung für die Anker Erstellung ausreichend ist oder ob der aktuelle Zustand ist.

[Nächste Lektion: 3. Anzeigen des Azure Spatial Anchor-Feedbacks](mrlearning-asa-ch3.md)

