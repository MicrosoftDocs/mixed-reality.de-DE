---
title: 'Tutorials zu Azure Spatial Anchors: 3 Speichern, Abrufen und Freigeben von Azure Spatial Anchors'
description: In diesem Kurs erfahren Sie, wie Sie Azure Spatial Anchors in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 274722588f156cb01fdd45525912e2e15687bc2d
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376532"
---
# <a name="3-saving-retrieving-and-sharing-azure-spatial-anchors"></a>3. Speichern, Abrufen und Freigeben von Azure Spatial Anchors

In diesem Tutorial erfahren Sie, wie Sie Azure Spatial Anchors über mehrere App-Sitzungen hinweg speichern, indem Sie die Anker-ID im Speicher von HoloLens 2 speichern. Darüber hinaus erfahren Sie, wie Sie diese Anker-ID für für andere Geräte freigeben, um eine Ankerausrichtung auf mehreren Geräten zu erreichen.

## <a name="objectives"></a>Ziele

* Erfahren, wie die räumliche Ausrichtung über mehrere App-Sitzungen erreicht wird
* Erfahren, wie räumliche Ausrichtung zwischen mehreren Geräten erreicht werden kann

## <a name="preparing-the-scene"></a>Vorbereiten der Szene

Klappen Sie im Hierarchiefenster das **ButtonParent**-Objekt auf. Wählen Sie die **vier letzten untergeordneten Schaltflächenobjekte** aus. **Aktivieren** Sie im Inspektorfenster das Kontrollkästchen neben dem Namensfeld, um alle diese Objekte als aktiv festzulegen.

![mr-learning-asa](images/mr-learning-asa/asa-03-section1-step1-1.png)

Wählen Sie im Hierarchiefenster die **ButtonParent**-Objekte aus. Suchen Sie dann im Inspektorfenster die **GridObjectCollection**-Komponente, und klicken Sie auf die Schaltfläche **Update Collection** (Sammlung aktualisieren), um die Position aller untergeordneten Objekte des **ButtonParent**-Objekts zu aktualisieren.

![mr-learning-asa](images/mr-learning-asa/asa-03-section1-step1-2.png)

## <a name="persisting-azure-spatial-anchors-between-app-sessions"></a>Beibehalten von Azure Spatial Anchors über App-Sitzungen hinweg

In diesem Abschnitt erfahren Sie, wie Sie die Azure Anchor ID auf der lokalen Festplatte der HoloLens speichern und abrufen. Auf diese Weise können Sie in verschiedenen App-Sitzungen die gleiche Anchor-ID bei Azure abrufen. Das ermöglicht es, verankerte Hologramme an den gleichen Orten zu positionieren wie in der vorangegangenen App-Sitzung.

Klappen Sie im Hierarchiefenster das **ButtonParent**-Objekt auf, und suchen Sie die zwei Schaltflächen mit den Namen **SaveAzureAnchorIdToDisk** und **GetAzureAnchorIdFromDisk**:

![mr-learning-asa](images/mr-learning-asa/asa-03-section2-step1-1.png)

Führen Sie die gleichen Schritte wie in den Anleitungen zum [Konfigurieren der Schaltflächen zum Betreiben der Szene](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene) aus dem vorhergehenden Tutorial aus, um die Komponente **Interactable (Script)** für jede der zwei Schaltflächen zu konfigurieren:

* Weisen Sie für das **SaveAzureAnchorIdToDisk**-Schaltflächenobjekt die AnchorModuleScript-> **SaveAzureAnchorIdToDisk ()** -Funktion zu.
* Weisen Sie für das **GetAzureAnchorIdFromDisk**-Schaltflächenobjekt die AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** -Funktion zu.

Wenn Sie die aktualisierte App für Ihre HoloLens erstellen, können Sie jetzt Azure Spatial Anchors zwischen App-Sitzungen beibehalten, indem Sie die Azure Anchor ID speichern. Um das zu Testen, können Sie diese Schritte ausführen:

1. Bewegen des Rover Explorers an die gewünschte Position
2. Starten einer Azure-Sitzung
3. Erstellen von Azure Anchors (erstellt Anker an der Position des Rover Explorers)
4. Speichern der Azure Anchor-ID auf dem Datenträger
5. Erneutes Starten der App
6. Abrufen des Azure Anchors vom Datenträger (lädt die Anker-ID, die Sie gerade erst gespeichert haben)
7. Starten einer Azure-Sitzung
8. Suchen eines Azure Anchors (platziert den Rover Explorer an der Position aus Schritt 3)

> [!NOTE]
> Für einen vollständigen Neustart der App muss nach dem Schließen der immersiven App-Ansicht das App-Fenster in der Mixed Reality Startumgebung geschlossen werden, bevor die App über das Startmenü neu gestartet wird. Weitere Details finden Sie in der Dokumentation [Verwenden von Apps in HoloLens](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens).

## <a name="sharing-azure-spatial-anchors-between-devices"></a>Teilen von Azure Spatial Anchors zwischen Geräten

In diesem Abschnitt erfahren Sie, wie Sie die Azure Anchor ID gemeinsam auf mehreren Geräten verwenden. Dies ermöglicht es mehreren Geräten, die gleiche Anchor ID bei Azure abzufragen, was die räumliche Ausrichtung der verankerten Hologramme gestattet. Die räumliche Ausrichtung, d. h. die Anzeige der gleichen Hologramme an den gleichen physischen Positionen auf mehreren Geräten, ist entscheidend für gemeinsame lokale Benutzererlebnisse in HoloLens 2.

Es gibt viele Möglichkeiten, Azure Anchor IDs zwischen Geräten zu übertragen, einschließlich der Methoden, die in der Reihe der [Tutorials zu Mehrbenutzerfunktionen](mr-learning-sharing-02.md) beschrieben sind. In diesem Beispiel verwenden Sie einen einfachen Webdienst zum Hochladen und Herunterladen von Anchor IDs zwischen Geräten.

Klappen Sie im Hierarchiefenster das **ButtonParent**-Objekt auf.   Suchen Sie die zwei Schaltflächen **ShareAzureAnchorIdToNetwork** und **GetAzureAnchorIdFromNetwork**:

![mr-learning-asa](images/mr-learning-asa/asa-03-section3-step1-1.png)

Führen Sie die gleichen Schritte wie in den Anleitungen zum [Konfigurieren der Schaltflächen zum Betreiben der Szene](mr-learning-asa-02.md#configuring-the-buttons-to-operate-the-scene) aus dem vorhergehenden Tutorial aus, um die Komponente **Interactable (Script)** für jede der zwei Schaltflächen zu konfigurieren:

* Weisen Sie dem **ShareAzureAnchorIdToNetwork** Objekt die AnchorModuleScript-> **ShareAzureAnchorIdToNetwork ()** -Funktion zu.
* Weisen Sie dem **GetAzureAnchorIdFromNetwork**-Objekt die AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** -Funktion zu.

Wenn Sie die aktualisierte App auf zwei HoloLens-Geräten erstellen, können Sie jetzt eine räumliche Ausrichtung erzielen, indem Sie die Azure Anchor ID freigeben. Um das zu Testen, können Sie diese Schritte ausführen:

1. Auf HoloLens-Gerät 1: Bewegen Sie den Rover Explorer an die gewünschte Position.
2. Auf HoloLens-Gerät 1: Starten Sie eine Azure-Sitzung.
3. Auf HoloLens-Gerät 1: Erstellen Sie einen Azure Anchor (erstellt Anker an der Position des Rover Explorers).
4. Auf HoloLens-Gerät 1: Geben Sie die Azure Anchor ID im Netzwerk frei.
5. Auf HoloLens-Gerät 2: Starten Sie die App.
6. Auf HoloLens-Gerät 2: Rufen Sie die Shared Anchor ID aus dem Netzwerk ab (ruft die Anchor ID ab, die gerade von HoloLens-Gerät 1 freigegeben worden war).
7. Auf HoloLens-Gerät 2: Starten Sie eine Azure-Sitzung.
8. Auf HoloLens-Gerät 2: Suchen Sie den Azure Anchor (positioniert den Rover Explorer am Ort aus Schritt 3).

> [!TIP]
> Wenn Sie nur über ein HoloLens-Gerät verfügen, können Sie die Funktionalität trotzdem testen, indem Sie die App neu starten, statt ein zweites HoloLens-Gerät zu verwenden.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie erfahren, wie Sie Azure Spatial Anchors zwischen App-Sitzungen und über App-Neustarts hinweg beibehalten, indem Sie die Azure Spatial Anchor ID auf dem lokalen Datenträger auf HoloLens speichern. Sie haben darüber hinaus gelernt, wie Azure Spatial Anchors zwischen mehreren Geräten geteilt werden, um eine einfache geteilte Mehrbenutzererfahrung mit statischen Hologrammen zu erzielen.

Im nächsten Tutorial erfahren Sie, wie Sie für Benutzer Feedback in Echtzeit bereitstellen. Dieses Feedback enthält Informationen zur Ankererstellung, zur Qualität des Verstehens der Umgebung und zum Status der Azure-Sitzung. Ohne Feedback wissen Benutzer möglicherweise nicht, ob ein Anker erfolgreich zu Azure hochgeladen wurde, ob die Qualität der Umgebung für die Ankererstellung ausreicht und wie der aktuelle Zustand ist.

[Nächstes Tutorial: 4. Anzeigen von Azure Spatial Anchors-Feedback](mr-learning-asa-04.md)
