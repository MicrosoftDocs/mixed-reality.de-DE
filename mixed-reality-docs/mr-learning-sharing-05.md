---
title: 'Tutorials zu Mehrbenutzerfunktionen: 5 Integrieren von Azure Spatial Anchors in eine gemeinsam genutzte Umgebung'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: fc8e20a9ddaa595db0a3d59975e7c785d01c0a6d
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376582"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a>5. Integrieren von Azure Spatial Anchors in eine gemeinsam genutzte Umgebung

In diesem Tutorial erfahren Sie, wie Sie Azure Spatial Anchors (ASA) in die geteilte Benutzererfahrung integrieren. ASA ermöglicht es, dass mehrere Geräte einen gemeinsamen Bezug auf die physische Welt nutzen, sodass sich die Benutzer gegenseitig an ihren realen physischen Standorten sehen und die gemeinsame Benutzererfahrung am gleichen Ort sehen.

## <a name="objectives"></a>Ziele

* Integrieren von ASA in einer geteilten Benutzererfahrung für die Ausrichtung mehrerer Geräte.
* Erlernen der grundlegenden Funktionsweise von ASA im Kontext einer lokalen gemeinsamen Benutzererfahrung.

## <a name="preparing-the-scene"></a>Vorbereiten der Szene

Klappen Sie im Hierarchiefenster das **SharedPlayground**-Objekt auf, und klappen Sie dann das **TableAnchor**-Objekt auf, um dessen untergeordnete Objekte anzuzeigen:

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section1-step1-1.png)

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs**, und ziehen Sie das Prefab **Buttons** auf das untergeordnete **TableAnchor**-Objekt, um es Ihrer Szene als untergeordnetes Element des TableAnchor-Objekts hinzuzufügen:

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Konfigurieren der Schaltflächen zum Betreiben der Szene

In diesem Abschnitt konfigurieren Sie eine Reihe von Schaltflächenereignissen, an denen sich die Grundlagen der Verwendung von Azure Spatial Anchors zum Erreichen einer räumlichen Ausrichtung in einer gemeinsamen Benutzererfahrung zeigen lassen.

Klappen Sie im Hierarchiefenster das **Button**-Objekt auf, und wählen Sie das erste untergeordnete Schaltflächenobjekt mit dem Namen **StartAzureSession** aus:

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-1.png)

Suchen Sie im Inspektorfenster die Komponente **Interactable (Script)** , und konfigurieren Sie das **OnClick ()** -Ereignis folgendermaßen:

* Weisen Sie das **TableAnchor**-Objekt dem Feld **None (Object)** zu.
* Wählen Sie in der Dropdownliste **No Function** die Funktion **AnchorModuleScript** > **StartAzureSession ()** aus.

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-2.png)

Wählen Sie im Hierarchiefenster das zweite untergeordnete Schaltflächenobjekt mit dem Namen **CreateAzureAnchor** aus, suchen Sie dann im Inspektorfenster die Komponente **Interactable (Script)** , und konfigurieren Sie das **OnClick ()** -Ereignis in folgender Weise:

* Weisen Sie das **TableAnchor**-Objekt dem Feld **None (Object)** zu.
* Wählen Sie in der Dropdownliste **No Function** die Funktion **AnchorModuleScript** > **CreateAzureAnchor ()** aus.
* Weisen Sie das **TableAnchor**-Objekt dem neuen Feld **None (Game Object)** zu, das jetzt angezeigt wird

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-3.png)

Wählen Sie im Hierarchiefenster das dritte untergeordnete Schaltflächenobjekt mit dem Namen **ShareAzureAnchor** aus, suchen Sie dann im Inspektorfenster die Komponente **Interactable (Script)** , und konfigurieren Sie das **OnClick ()** -Ereignis in folgender Weise:

* Weisen Sie das **TableAnchor**-Objekt dem Feld **None (Object)** zu.
* Wählen Sie in der Dropdownliste **No Function** die Funktion **SharingModuleScript** > **ShareAzureAnchor ()** aus.

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-4.png)

Wählen Sie im Hierarchiefenster das vierte untergeordnete Schaltflächenobjekt mit dem Namen **GetAzureAnchor** aus, suchen Sie dann im Inspektorfenster die Komponente **Interactable (Script)** , und konfigurieren Sie das **OnClick ()** -Ereignis in folgender Weise:

* Weisen Sie das **TableAnchor**-Objekt dem Feld **None (Object)** zu.
* Wählen Sie in der Dropdownliste **No Function** die Funktion **SharingModuleScript** > **GetAzureAnchor ()** aus.

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>Verbinden der Szene mit der Azure-Ressource

Klappen Sie im Hierarchiefenster das **SharedPlayground**-Objekt auf, und wählen Sie das **TableAnchor**-Objekt aus.

Suchen Sie im Inspektor-Fenster die Komponente **Spatial Anchor Manager (Script)** , und konfigurieren Sie den Abschnitt **Credentials** (Anmeldeinformationen) mit den Anmeldeinformationen aus dem Azure Spatial Anchors-Konto, das Sie im Rahmen der [Voraussetzungen](mr-learning-sharing-01.md#prerequisites) für diese Tutorialreihe erstellt haben:

* Fügen Sie in das Feld **Spatial Anchors Account ID** die **Konto-ID** Ihres Azure Spatial Anchors-Kontos ein
* Fügen Sie in das Feld **Spatial Anchors Account Key** (Spatial Anchors-Kontoschlüssel) den primären oder sekundären **Zugriffsschlüssel** aus Ihrem Azure Spatial Anchors-Konto ein

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-1.png)

> [!TIP]
> Anstatt die Spatial Anchors-Konto-ID und den Schlüssel in der Szene festzulegen, können Sie diese Werte für das gesamte Projekt festlegen. Dies kann von Vorteil sein, wenn Sie über mehrere Szenen mit ASA verfügen. Navigieren Sie dazu im Projektfenster zur Ressource „Assets > AzureSpatialAnchors.SDK > Resources > **SpatialAnchorConfig**, und legen Sie dann die Werte im Inspektor-Fenster fest.

Wählen Sie im Hierarchiefenster das **TableAnchor-Objekt** aus, und suchen Sie dann im Inspektor-Fenster nach der Komponente **Anchor Module (Script)** , um sie wie folgt zu konfigurieren:

* Ändern Sie im Feld **Public Sharing Pin** (PIN für öffentliche Freigabe) einige Ziffern, sodass die PIN für Ihr Projekt eindeutig ist.

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-2.png)

Vergewissern Sie sich bei noch immer ausgewähltem **TableAnchor**-Objekt im Inspektor-Fenster, dass alle Skriptkomponenten **aktiviert** sind:

* Aktivieren Sie das Kontrollkästchen neben den **Spatial Anchor Manager (Script)** -Komponenten, um sie zu aktivieren
* Aktivieren Sie das Kontrollkästchen neben den **Anchor Module Script (Script)** -Komponenten, um sie zu aktivieren
* Aktivieren Sie das Kontrollkästchen neben den **Sharing Module Script (Script)** -Komponenten, um sie zu aktivieren

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-3.png)

## <a name="trying-the-experience-with-spatial-alignment"></a>Ausprobieren der Benutzererfahrung mit räumlicher Ausrichtung

> [!NOTE]
> Azure Spatial Anchors können nicht in Unity ausgeführt werden. Um die Funktionalität der Azure Spatial Anchors zu testen, müssen Sie das Projekt daher auf mindestens zwei Geräten bereitstellen.

Wenn Sie das Unity-Projekt jetzt erstellen und es auf zwei Geräten bereitstellen, können Sie räumliche Ausrichtung zwischen den Geräten erreichen, indem Sie die Azure Anchor-ID teilen. Um das zu Testen, können Sie diese Schritte ausführen:

1. Auf Gerät 1: **Starten Sie die App** (der Rover-Explorer wird instanziiert und auf dem Tisch positioniert)
2. Auf Gerät 2: **Starten Sie die App** (beide Benutzer sehen den Tisch mit dem Rover-Explorer, der Tisch wird jedoch nicht am gleichen Ort dargestellt und die Benutzeravatare werden nicht dort angezeigt, wo sich die Benutzer befinden)
3. Auf Gerät 1: Drücken Sie die Schaltfläche **Start Azure Session** (Azure-Sitzung starten)
4. Auf Gerät 1: Drücken Sie die Schaltfläche **Create Azure Anchor** (Azure Anchor erstellen; erstellt einen Anker am Speicherort des TableAnchor-Objekts und speichert die Ankerinformationen in der Azure-Ressource).
5. Auf Gerät 1: Drücken Sie die Schaltfläche **Share Azure Anchor** (Azure Anchor teilen; teilt die Anker-ID in Echtzeit mit anderen Benutzern)
6. Auf Gerät 2: Drücken Sie die Schaltfläche **Start Azure Session** (Azure-Sitzung starten)
7. Auf Gerät 2: Drücken Sie die Schaltfläche **Get Azure Anchor** (Azure Anchor abrufen) (stellt eine Verbindung mit der Azure-Ressource her, um die Ankerinformationen für die freigegebene Anker-ID abzurufen, und verschiebt dann das TableAnchor-Objekt an den Speicherort, an dem der Anker mit dem Gerät 1 erstellt wurde)

> [!TIP]
> Wenn Sie keinen Zugriff auf zwei HoloLens-Geräte haben, können Sie die Anweisungen unter [Erstellen von Azure Spatial Anchors für mobile Geräte](mr-learning-asa-05.md) befolgen, um das Projekt auf Ihrem mobilen Gerät bereitzustellen.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, wie Sie die leistungsstarken Spatial Anchors von Azure integrieren, um Geräte in einer gemeinsamen Benutzererfahrung auszurichten.

Dieses Tutorial bildet zugleich den Abschluss der Tutorialreihe, in der Sie gelernt haben, wie ein Photon-Konto eingerichtet, eine PUN-Anwendung erstellt und PUN in das Unity-Projekt integriert wird und Benutzeravatare und geteilte Objekte konfiguriert und schließlich mehrere Teilnehmer mithilfe von Azure Spatial Anchors ausgerichtet werden.
