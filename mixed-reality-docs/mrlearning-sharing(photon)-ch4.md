---
title: 'Tutorials zu Mehrbenutzerfunktionen: 5 Integrieren von Azure Spatial Anchors in eine gemeinsam genutzte Umgebung'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: c27ed7327cfe0a61f2b63e309348bdea1a535ea1
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604971"
---
# <a name="4-integrating-azure-spatial-anchors-into-a-shared-experience"></a>4. Integrieren von Azure Spatial Anchors in eine gemeinsam genutzte Umgebung

In diesem Tutorial erfahren Sie, wie Sie Azure Spatial Anchors (ASA) in die geteilte Benutzererfahrung integrieren. ASA ermöglicht es, dass mehrere Geräte einen gemeinsamen Bezug auf die physische Welt nutzen, sodass sich die Benutzer gegenseitig an ihren realen physischen Standorten sehen und die gemeinsame Benutzererfahrung am gleichen Ort sehen.

## <a name="objectives"></a>Ziele

* Integrieren von ASA in einer geteilten Benutzererfahrung für die Ausrichtung mehrerer Geräte.
* Erlernen der grundlegenden Funktionsweise von ASA im Kontext einer lokalen gemeinsamen Benutzererfahrung.

## <a name="preparing-the-scene"></a>Vorbereiten der Szene

Klappen Sie im Hierarchiefenster das **SharedPlayground**-Objekt auf, und klappen Sie dann das **TableAnchor**-Objekt auf, um dessen untergeordnete Objekte anzuzeigen:

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-1.png)

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs**, und ziehen Sie das **Buttons**-Prefab auf das untergeordnete **TableAnchor**-Objekt im Hierarchiefenster, um es Ihrer Szene als untergeordnetes Element des TableAnchor-Objekts hinzuzufügen:

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Konfigurieren der Schaltflächen zum Betreiben der Szene

In diesem Abschnitt konfigurieren Sie eine Reihe von Schaltflächenereignissen, an denen sich die Grundlagen der Verwendung von Azure Spatial Anchors zum Erreichen einer räumlichen Ausrichtung in einer gemeinsamen Benutzererfahrung zeigen lassen.

Klappen Sie im Hierarchiefenster das **Button**-Objekt auf, und wählen Sie das erste untergeordnete Schaltflächenobjekt mit dem Namen **StartAzureSession** aus:

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-1.png)

Suchen Sie im Inspektorfenster die Komponente **Interactable (Script)** , und konfigurieren Sie das **OnClick ()** -Ereignis folgendermaßen:

* Weisen Sie das **TableAnchor**-Objekt dem Feld **None (Object)** zu
* Wählen Sie in der Dropdownliste **No Function** die Funktion **AnchorModuleScript** > **StartAzureSession ()** aus

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-2.png)

Wählen Sie im Hierarchiefenster das zweite untergeordnete Schaltflächenobjekt mit dem Namen **CreateAzureAnchor** aus, suchen Sie dann im Inspektorfenster die Komponente **Interactable (Script)** , und konfigurieren Sie das **OnClick ()** -Ereignis in folgender Weise:

* Weisen Sie das **TableAnchor**-Objekt dem Feld **None (Object)** zu
* Wählen Sie in der Dropdownliste **No Function** die Funktion **AnchorModuleScript** > **CreateAzureAnchor ()** aus
* Weisen Sie das **TableAnchor**-Objekt dem neuen Feld **None (Game Object)** zu, das jetzt angezeigt wird

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-3.png)

Wählen Sie im Hierarchiefenster das dritte untergeordnete Schaltflächenobjekt mit dem Namen **ShareAzureAnchor** aus, suchen Sie dann im Inspektorfenster die Komponente **Interactable (Script)** , und konfigurieren Sie das **OnClick ()** -Ereignis in folgender Weise:

* Weisen Sie das **TableAnchor**-Objekt dem Feld **None (Object)** zu
* Wählen Sie in der Dropdownliste **No Function** die Funktion **SharingModuleScript** > **ShareAzureAnchor ()** aus

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-4.png)

Wählen Sie im Hierarchiefenster das vierte untergeordnete Schaltflächenobjekt mit dem Namen **GetAzureAnchor** aus, suchen Sie dann im Inspektorfenster die Komponente **Interactable (Script)** , und konfigurieren Sie das **OnClick ()** -Ereignis in folgender Weise:

* Weisen Sie das **TableAnchor**-Objekt dem Feld **None (Object)** zu
* Wählen Sie in der Dropdownliste **No Function** die Funktion **SharingModuleScript** > **GetAzureAnchor ()** aus

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>Verbinden der Szene mit der Azure-Ressource

Klappen Sie im Hierarchiefenster das **SharedPlayground**-Objekt auf, und wählen Sie das **TableAnchor**-Objekt aus. Suchen Sie dann im Inspektorfenster die Komponente **Spatial Anchor Manager (Script)** , und konfigurieren Sie den Abschnitt **Credentials** (Anmeldeinformationen) mit den Anmeldeinformationen aus dem Azure Spatial Anchors-Konto, das Sie im Rahmen der [Voraussetzungen](mrlearning-sharing(photon)-ch1.md#prerequisites) für diese Tutorialreihe erstellt haben:

* Fügen Sie in das Feld **Spatial Anchors Account ID** die **Konto-ID** Ihres Azure Spatial Anchors-Kontos ein
* Fügen Sie in das Feld **Spatial Anchors Account Key** (Spatial Anchors-Kontoschlüssel) den primären oder sekundären **Zugriffsschlüssel** aus Ihrem Azure Spatial Anchors-Konto ein

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-1.png)

Vergewissern Sie sich bei noch immer ausgewähltem **TableAnchor**-Objekt im Inspektorfenster, dass alle Skriptkomponenten aktiviert sind:

* Aktivieren Sie das Kontrollkästchen neben den **Spatial Anchor Manager (Script)** -Komponenten, um sie zu aktivieren
* Aktivieren Sie das Kontrollkästchen neben den **Anchor Module Script (Script)** -Komponenten, um sie zu aktivieren
* Aktivieren Sie das Kontrollkästchen neben den **Sharing Module Script (Script)** -Komponenten, um sie zu aktivieren

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-2.png)

## <a name="trying-the-experience-with-spatial-alignment"></a>Ausprobieren der Benutzererfahrung mit räumlicher Ausrichtung

> [!NOTE]
> Azure Spatial Anchors können nicht in Unity ausgeführt werden. Um die Funktionalität der Azure Spatial Anchors zu testen, müssen Sie das Projekt daher auf mindestens zwei HoloLens-Geräten bereitstellen.

Wenn Sie das Unity-Projekt jetzt erstellen und es auf zwei HoloLens-Geräten bereitstellen, können Sie räumliche Ausrichtung zwischen den Geräten erreichen, indem Sie die Azure Anchor-ID teilen. Um das zu Testen, können Sie diese Schritte ausführen:

1. Auf HoloLens-Gerät 1: **Starten Sie die Anwendung** (die Raketenstartbasis wird instanziiert und auf dem Tisch positioniert)
2. Auf HoloLens-Gerät 2: **Starten Sie die Anwendung** (beide Benutzer sehen den Tisch mit der Raketenstartbasis, der Tisch wird jedoch nicht am gleichen Ort dargestellt und die Benutzeravatare werden nicht dort angezeigt, wo sich die Benutzer befinden)
3. Auf HoloLens-Gerät 1: Drücken Sie die Schaltfläche **Start Azure Session** (Azure-Sitzung starten)
4. Auf HoloLens-Gerät 1: Drücken Sie die Schaltfläche **Create Azure Anchor** (Azure Anchor erstellen; erstellt einen Anker am Speicherort des TableAnchor-Objekts und speichert die Ankerinformationen in der Azure-Ressource).
5. Auf HoloLens-Gerät 1: Drücken Sie die Schaltfläche **Share Azure Anchor** (Azure Anchor teilen; teilt die Anker-ID in Echtzeit mit anderen Benutzern)
6. Auf HoloLens-Gerät 2: Drücken Sie die Schaltfläche **Start Azure Session** (Azure-Sitzung starten)
7. Auf HoloLens-Gerät 2: Drücken Sie die Schaltfläche **Get Azure Anchor** (Azure Anchor abrufen; stellt eine Verbindung mit der Azure-Ressource her, um die Ankerinformationen für die freigegebene Anker-ID abzurufen, und verschiebt dann das TableAnchor-Objekt an den Speicherort, an dem der Anker mit dem HoloLens-Gerät 1 erstellt wurde)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, wie Sie die leistungsstarken Spatial Anchors von Azure integrieren, um Geräte in einer gemeinsamen Benutzererfahrung auszurichten. Dieses Tutorial bildet zugleich den Abschluss der Tutorialreihe, in der Sie gelernt haben, wie ein neues Photon-Konto und eine neue Photon-Anwendung einrichtet werden, wie Photon und PUN in eine Unity-Anwendung integriert werden, Benutzeravatare und geteilte Objekte konfiguriert und schließlich mehrere Teilnehmer mithilfe von ASA ausgerichtet werden.
