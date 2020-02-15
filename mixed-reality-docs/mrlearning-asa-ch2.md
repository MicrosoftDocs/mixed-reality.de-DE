---
title: Tutorials für räumliche Azure-Anker-2. Speichern, abrufen und Freigeben von räumlichen Azure-Ankern
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 7b19233a9634e2568200476c9483464bbf9dd3c8
ms.sourcegitcommit: a580166a19294f835b8e09c780f663f228dd5de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2020
ms.locfileid: "77250737"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a>2. speichern, abrufen und Freigeben von räumlichen Azure-Ankern

In diesem Tutorial erfahren Sie, wie Sie räumliche Azure-Anker in mehreren App-Sitzungen speichern, indem Sie die Anker-ID im Speicher von hololens 2 speichern. Darüber hinaus erfahren Sie, wie Sie diese Anker-ID für eine Ausrichtung auf mehrere Geräte als Anker für andere Geräte freigeben.

## <a name="objectives"></a>Ziele

* Erfahren Sie, wie Sie räumliche Azure-Anker-IDs auf dem lokalen Datenträger von hololens 2 speichern und abrufen, um Persistenz zwischen App-Sitzungen zu erhalten.
* Erfahren Sie, wie Sie Azure Spatial Anchor-IDs zwischen Benutzern in einem Szenario mit mehreren Geräten freigeben.

## <a name="preparing-the-scene"></a>Vorbereiten der Szene

Navigieren Sie im Projektfenster zu **Assets** > **mrtk. Tutorials. azurespatialanchor** > Ordner " **Prefabs** ". Wenn Sie die STRG-Taste gedrückt halten, klicken Sie auf **ButtonParent_SaveAnchorId** , und **ButtonParent_ShareAnchorId** Sie die beiden Prefabs aus, und ziehen Sie Sie in das Hierarchie Fenster, um Sie der Szene hinzuzufügen:

![mrlearning-ASA](images/mrlearning-asa/tutorial2-section1-step1-1.png)

## <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a>Beibehalten von Azure-Ankern zwischen App-Sitzungen: Anker-ID auf Datenträger speichern
<!-- TODO: Consider renaming to 'Persist Azure Anchors between app sessions' -->

In diesem Abschnitt erfahren Sie, wie Sie die Azure-Anker-ID auf dem lokalen Datenträger hololens 2 speichern und abrufen. Dies ermöglicht es Ihnen, Azure nach der gleichen Anker-ID zwischen verschiedenen App-Sitzungen abzufragen, sodass die verankerten Hologramme an demselben Speicherort wie in der vorherigen App-Sitzung positioniert werden können.

Erweitern Sie im Fenster Hierarchie das **ButtonParent_SaveAnchorId** Objekt, das zwei Schaltflächen enthält, eine Schaltfläche zum Speichern der Azure-Anker-ID im Speicher hololens 2 und eine andere zum Abrufen der gespeicherten ID vom Datenträger:

![mrlearning-ASA](images/mrlearning-asa/tutorial2-section2-step1-1.png)

Führen Sie die gleichen Schritte wie in den Anweisungen [Konfigurieren der Schaltflächen zum Ausführen der Szene](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) aus dem vorherigen Tutorial aus, um die **Druck Bare Schaltfläche Holo Lens 2 (Skript)** und die **interactable-Komponente (Skript)** auf jeder der beiden Schaltflächen zu konfigurieren:

* Weisen Sie für das **saveazureanchoriddedisk** -Objekt die Funktion anchormodulescript > **saveazureanchoriddedisk ()** zu.
* Weisen Sie für das **getazureanchoridfromdisk** -Objekt die anchormodulescript-> **getazureanchoridfromdisk ()** -Funktion zu.

Wenn Sie die aktualisierte Anwendung in ihren hololens erstellen, können Sie jetzt räumliche Azure-Anker zwischen App-Sitzungen beibehalten, indem Sie die Azure-Anker-ID speichern. Zum Testen können Sie die folgenden Schritte ausführen:

1. Verschieben Sie das Launcher-Start Programm an den gewünschten Speicherort.
2. Starten Sie die Azure-Sitzung.
3. Erstellen Sie einen Azure-Anker (erstellt Anker am Speicherort der Start Programm Darstellung).
4. Speichert die Azure-Anker-ID auf dem Datenträger.
5. Starten Sie die Anwendung neu.
6. Azure Anchor von Datenträger erhalten (lädt die soeben gespeicherte Anker-ID).
7. Starten Sie die Azure-Sitzung.
8. Suchen Sie nach Azure Anchor (positioniert die Funktion des Raketenstart Programms an dem Standort aus Schritt 3).

## <a name="share-azure-anchors-between-multiple-devices"></a>Freigeben von Azure-Ankern für mehrere Geräte

In diesem Abschnitt erfahren Sie, wie Sie die Azure-Anker-ID für mehrere Geräte freigeben. Dies ermöglicht es mehreren Geräten, Azure nach der gleichen Anker-ID abzufragen, sodass die verankerten holograms räumlich ausgerichtet werden können. Die räumliche Ausrichtung, d. h., dass die gleichen holograms am gleichen physischen Standort zwischen mehreren Geräten angezeigt werden, ist der Schlüssel für die lokale gemeinsame Nutzung in den hololens 2.

Es gibt zahlreiche Möglichkeiten zum Übertragen von Azure Anchor-IDs zwischen Geräten, einschließlich der in der Reihe der [Tutorials für mehrere Benutzer](mrlearning-sharing(photon)-ch1.md) beschriebenen Methoden. In diesem Beispiel verwenden Sie einen einfachen Webdienst zum Hochladen und Herunterladen von Anker-IDs zwischen Geräten.

Erweitern Sie im Fenster Hierarchie das **ButtonParent_ShareAnchorId** Objekt, das zwei Schaltflächen enthält. eine Schaltfläche zum Hochladen der Azure-Anker-ID auf den Webserver und eine andere Schaltfläche zum Herunterladen der ID vom Webserver:

![mrlearning-ASA](images/mrlearning-asa/tutorial2-section3-step1-1.png)

Führen Sie die gleichen Schritte wie in den Anweisungen [Konfigurieren der Schaltflächen zum Ausführen der Szene](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) aus dem vorherigen Tutorial aus, um die **Druck Bare Schaltfläche Holo Lens 2 (Skript)** und die **interactable-Komponente (Skript)** auf jeder der beiden Schaltflächen zu konfigurieren:

* Weisen Sie für das **shareazureanchoridtonetwork** -Objekt die Funktion anchormodulescript > **shareazureanchoridtonetwork ()** zu.
* Weisen Sie für das **getazureanchoridfromnetwork** -Objekt die anchormodulescript-> **getazureanchoridfromnetwork ()** -Funktion zu.

Wenn Sie die aktualisierte Anwendung auf zwei hololens-Geräten erstellen, können Sie jetzt eine räumliche Ausrichtung zwischen den Geräten erzielen, indem Sie die Azure-Anker-ID freigeben. Zum Testen können Sie die folgenden Schritte ausführen:

1. Auf hololens-Gerät 1: Verschieben Sie die Funktion für das Raketenstart Programm an den gewünschten Speicherort.
2. Auf hololens-Gerät 1: Starten Sie die Azure-Sitzung.
3. Auf hololens-Gerät 1: Erstellen Sie einen Azure-Anker (erstellt Anker am Speicherort des Raketenstart Programms).
4. Auf hololens Gerät 1: Geben Sie die Azure-Anker-ID für das Netzwerk frei.
5. Auf hololens-Gerät 2: Starten Sie die Anwendung neu.
6. Auf hololens-Gerät 2: Abrufen der gemeinsamen Anker-ID aus dem Netzwerk (Ruft die Anker-ID ab, die gerade von hololens-Gerät 1 gemeinsam genutzt wird)
7. Auf hololens-Gerät 2: Starten Sie die Azure-Sitzung.
8. Auf hololens-Gerät 2: Suchen Sie nach Azure-Anker (positioniert die Funktion des Raketenstart Programms an dem Standort aus Schritt 3).

> [!TIP]
> Wenn Sie nur über ein hololens verfügen, können Sie die Funktionalität weiterhin testen, indem Sie die Anwendung neu starten, anstatt ein zweites hololens-Gerät zu verwenden.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie erfahren, wie Sie räumliche Azure-Anker zwischen Anwendungs Sitzungen und Anwendungs Neustarts beibehalten, indem Sie die räumliche Azure-Anker-ID auf dem lokalen Datenträger auf hololens speichern. Außerdem haben Sie erfahren, wie Sie räumliche Azure-Anker zwischen mehreren Geräten für eine grundlegende freigegebene multibenutzerbenutzerfunktion mit mehreren Benutzern freigeben.

Im nächsten Tutorial erfahren Sie, wie Sie Benutzern Echtzeitfeedback bereitstellen. Dieses Feedback enthält Informationen zur Anker Erstellung, zur Qualität des Verständnisses der Umgebung und zum Status der Azure-Sitzung. Ohne Feedback wissen Benutzer möglicherweise nicht, ob ein Anker erfolgreich in Azure hochgeladen wurde, ob die Qualität der Umgebung für die Anker Erstellung ausreichend ist oder ob der aktuelle Zustand ist.

[Nächste Lektion: 3. Anzeigen des Azure Spatial Anchor-Feedbacks](mrlearning-asa-ch3.md)
