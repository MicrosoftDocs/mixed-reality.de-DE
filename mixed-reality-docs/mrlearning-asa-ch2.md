---
title: 'Tutorials zu Azure Spatial Anchors: 2 Speichern, Abrufen und Freigeben von Azure Spatial Anchors'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 36f25229469e848a3f0612a5971cc8e9381262f5
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "80362011"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2. Speichern, Abrufen und Freigeben von Azure Spatial Anchors

In diesem Tutorial erfahren Sie, wie Sie Azure Spatial Anchors über mehrere App-Sitzungen hinweg speichern, indem Sie die Anker-ID im Speicher von HoloLens 2 speichern. Darüber hinaus erfahren Sie, wie Sie diese Anker-ID für für andere Geräte freigeben, um eine Ankerausrichtung auf mehreren Geräten zu erreichen.

## <a name="objectives"></a>Ziele

* Erfahren Sie, wie Sie Azure Spatial Anchor IDs auf dem lokalen Datenträger von HoloLens 2 speichern und abrufen, um Persistenz zwischen App-Sitzungen zu erzielen.
* Erfahren Sie, wie Azure Spatial Anchor IDs zwischen Benutzern in einem Mehrgeräteszenario geteilt werden können

## <a name="preparing-the-scene"></a>Vorbereiten der Szene

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs**. Klicken Sie bei gedrückter STRG-Taste auf **ButtonParent_SaveAnchorId** und **ButtonParent_ShareAnchorId**, um die beiden Prefabs auszuwählen, und ziehen Sie sie dann auf das Hierarchiefenster, um sie der Szene hinzuzufügen:

![mrlearning-asa](images/mrlearning-asa/tutorial2-section1-step1-1.png)

## <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>Bewahren von Azure Anchors zwischen App-Sitzungen: Speichern der Anchor ID auf Datenträgern
<!-- TODO: Consider renaming to 'Persist Azure Anchors between app sessions' -->

In diesem Abschnitt erfahren Sie, wie Sie die Azure Anchor ID auf der lokalen Festplatte der HoloLens 2 speichern und abrufen. Dies ermöglicht es Ihnen, in verschiedenen App-Sitzungen die gleiche Anchor ID bei Azure abzufragen, was die Positionierung verankerter Hologramme an der gleichen Position wie in der vorhergehenden App-Sitzung ermöglicht.

Erweitern Sie im Hierarchiefenster das **ButtonParent_SaveAnchorId**-Objekt, das zwei Schaltflächen enthält, eine Schaltfläche zum Speichern der Azure Anchor ID im Speicher der HoloLens 2 und eine weitere zum Abrufen der gespeicherten ID vom Datenträger:

![mrlearning-asa](images/mrlearning-asa/tutorial2-section2-step1-1.png)

Führen Sie die gleichen Schritte wie in den Anleitungen zum [Konfigurieren der Schaltflächen zum Betreiben der Szene](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) aus dem vorhergehenden Tutorial aus, um die Komponente **Pressable Button Holo Lens 2 (Script)** (Drückbare Schaltfläche HoloLens 2 (Skript)) und die Komponente **Interactable (Script)** auf jeder der zwei Schaltflächen zu konfigurieren:

* Weisen Sie für das **SaveAzureAnchorIdToDisk**-Objekt die AnchorModuleScript-> **SaveAzureAnchorIdToDisk ()** -Funktion zu.
* Weisen Sie für das **GetAzureAnchorIdFromDisk**-Objekt die AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** -Funktion zu.

Wenn Sie die aktualisierte Anwendung für Ihre HoloLens erstellen, können Sie jetzt Azure Spatial Anchors zwischen App-Sitzungen bewahren, indem Sie die Azure Anchor ID speichern. Um das zu Testen, können Sie diese Schritte ausführen:

1. Verschieben Sie die Raketenstartbasis-Erfahrung an den gewünschten Speicherort.
2. Starten Sie eine Azure-Sitzung.
3. Erstellen Sie Azure Anchors (erstellt Anker am Speicherort der Raketenstartbasis-Benutzererfahrung).
4. Speichern Sie die Azure Anchor ID auf dem Datenträger.
5. Führen Sie einen Neustart der Anwendung aus
6. Rufen Sie den Azure Anchor vom Datenträger ab (lädt die Anchor ID, die Sie soeben gespeichert haben).
7. Starten Sie eine Azure-Sitzung.
8. Suchen Sie nach dem Azure Anchor (er positioniert die Raketenstartbasis-Benutzererfahrung an der Position aus Schritt 3).

> [!NOTE]
> Für einen vollständigen Neustart der Anwendung muss nach dem Schließen der immersiven App-Ansicht das App-Fenster in der Mixed Reality Startumgebung geschlossen werden, bevor die Anwendung über das Startmenü neu gestartet wird. Weitere Details finden Sie in der Dokumentation [Verwenden von Apps in HoloLens](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens).

## <a name="share-azure-anchors-between-multiple-devices"></a>Teilen von Azure Anchors zwischen mehreren Geräten

In diesem Abschnitt erfahren Sie, wie Sie die Azure Anchor ID gemeinsam auf mehreren Geräten verwenden. Dies ermöglicht es mehreren Geräten, die gleiche Anchor ID bei Azure abzufragen, was die räumliche Ausrichtung der verankerten Hologramme gestattet. Die räumliche Ausrichtung, d. h. die Anzeige der gleichen Hologramme an den gleichen physischen Positionen auf mehreren Geräten, ist entscheidend für gemeinsame lokale Benutzererlebnisse in HoloLens 2.

Es gibt viele Möglichkeiten, Azure Anchor IDs zwischen Geräten zu übertragen, einschließlich der Methoden, die in den Reihen der [Tutorials zu Mehrbenutzerfunktionen](mrlearning-sharing(photon)-ch1.md) beschrieben sind. In diesem Beispiel verwenden Sie einen einfachen Webdienst zum Hochladen und Herunterladen von Anchor IDs zwischen Geräten.

Klappen Sie im Hierarchiefenster das **ButtonParent_ShareAnchorId**-Objekt auf, das zwei Schaltflächen enthält, eine Schaltfläche zum Hochladen der Azure Anchor ID auf den Webserver und eine weitere zum Herunterladen der ID vom Webserver:

![mrlearning-asa](images/mrlearning-asa/tutorial2-section3-step1-1.png)

Führen Sie die gleichen Schritte wie in den Anleitungen zum [Konfigurieren der Schaltflächen zum Betreiben der Szene](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) aus dem vorhergehenden Tutorial aus, um die Komponente **Pressable Button Holo Lens 2 (Script)** (Drückbare Schaltfläche HoloLens 2 (Skript)) und die Komponente **Interactable (Script)** auf jeder der zwei Schaltflächen zu konfigurieren:

* Weisen Sie dem **ShareAzureAnchorIdToNetwork** Objekt die AnchorModuleScript-> **ShareAzureAnchorIdToNetwork ()** -Funktion zu.
* Weisen Sie dem **GetAzureAnchorIdFromNetwork**-Objekt die AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** -Funktion zu.

Wenn Sie die aktualisierte Anwendung auf zwei HoloLens-Geräten erstellen, können Sie jetzt eine räumliche Ausrichtung zwischen den Geräten erzielen, indem Sie die Azure Anchor ID freigeben. Um das zu Testen, können Sie diese Schritte ausführen:

1. Auf HoloLens-Gerät 1: Verschieben Sie die Raketenstartbasis-Erfahrung an den gewünschten Speicherort.
2. Auf HoloLens-Gerät 1: Starten Sie eine Azure-Sitzung.
3. Auf HoloLens-Gerät 1: Erstellen Sie Azure Anchors (erstellt Anker am Speicherort der Raketenstartbasis-Benutzererfahrung).
4. Auf HoloLens-Gerät 1: Geben Sie die Azure Anchor ID im Netzwerk frei.
5. Auf HoloLens-Gerät 2: Starten Sie die Anwendung.
6. Auf HoloLens-Gerät 2: Rufen Sie die Shared Anchor ID aus dem Netzwerk ab (ruft die Anchor ID ab, die gerade von HoloLens-Gerät 1 freigegeben worden war).
7. Auf HoloLens-Gerät 2: Starten Sie eine Azure-Sitzung.
8. Auf HoloLens-Gerät 2: Suchen Sie nach dem Azure Anchor (er positioniert die Raketenstartbasis-Benutzererfahrung an der Position aus Schritt 3).

> [!TIP]
> Wenn Sie nur über ein HoloLens-Gerät verfügen, können Sie die Funktionalität trotzdem testen, indem Sie die Anwendung neu starten, statt ein zweites HoloLens-Gerät zu verwenden.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie erfahren, wie Sie Azure Spatial Anchors zwischen Anwendungssitzungen und über Anwendungsneustarts hinweg beibehalten, indem Sie die Azure Spatial Anchor ID auf dem lokalen Datenträger auf HoloLens speichern. Sie haben darüber hinaus gelernt, wie Azure Spatial Anchors zwischen mehreren Geräten geteilt werden, um eine einfache geteilte Mehrbenutzererfahrung mit statischen Hologrammen zu erzielen.

Im nächsten Tutorial erfahren Sie, wie Sie für Benutzer Feedback in Echtzeit bereitstellen. Dieses Feedback enthält Informationen zur Ankererstellung, zur Qualität des Verstehens der Umgebung und zum Status der Azure-Sitzung. Ohne Feedback wissen Benutzer möglicherweise nicht, ob ein Anker erfolgreich zu Azure hochgeladen wurde, ob die Qualität der Umgebung für die Ankererstellung ausreicht und wie der aktuelle Zustand ist.

[Nächste Lektion: 3. Anzeigen von Azure Spatial Anchors-Feedback](mrlearning-asa-ch3.md)
