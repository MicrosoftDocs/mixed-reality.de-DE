---
title: 'Tutorials zu Mehrbenutzerfunktionen: 5 Integrieren von Azure Spatial Anchors in eine gemeinsam genutzte Umgebung'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 7fb8cd03b2f3739037dee38786493bfd9012f6ce
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031687"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a>5. Integrieren von Azure Spatial Anchors in eine gemeinsam genutzte Umgebung

In dieser Lektion erfahren Sie, wie Sie Azure Spatial Anchors (ASA) in unsere freigegebene Benutzererfahrung integrieren. ASA ermöglicht es, dass mehrere Geräte in einem gemeinsamen Bereich eine gemeinsame Referenz verwenden, wenn in ihrer physischen Umgebung virtuelle Benutzererfahrungen verankert sind, sodass alle Teilnehmer Objekte am gleichen physischen Ort sehen.

## <a name="objectives"></a>Ziele

* Integrieren von ASA in einer freigegebenen Benutzererfahrung für die Ausrichtung mehrerer Geräte.
* Erlernen der grundlegenden Funktionsweise von ASA im Kontext einer lokalen gemeinsamen Umgebung.

## <a name="instructions"></a>Anweisungen

1. Wählen Sie unter dem übergeordneten Objekt MixedRealityPlayspace das TableAnchor-Prefab aus, und löschen Sie es.

    ![Module3Chapter5tep2im](images/module3chapter5step2im.PNG)

2. Wechseln Sie in der Projektansicht zu „Assets > Resources > Prefabs“, und ziehen Sie das TableAnchor-Prefab auf das SharedPlayground-Objekt, um es zu einem untergeordneten Objekt zu machen.

3. Klappen Sie das übergeordnete MixedRealityPlayspace-Objekt, das TableAnchor-Objekt und auch das Buttons-Objekt auf.

    ![Module3hapter5step5im](images/module3chapter5step5im.PNG)

4. Wählen Sie nun in der Hierarchie ShareAzureAnchorButton aus, und verlegen Sie Ihre Aufmerksamkeit auf den Inspektorbereich. Scrollen Sie nach unten zum Dropdownmenü, das im Bild unten angezeigt wird, wählen Sie AnchorModuleScript aus, und klicken Sie auf ShareAnchorNetwork().

    ![Module3hapter5step6im](images/module3chapter5step6im.PNG)

5. Wählen Sie GetAzureAnchorButton aus (siehe Schritt 4), und verlegen Sie Ihre Aufmerksamkeit wieder auf den Inspektorbereich. Scrollen Sie nach unten zum Dropdownmenü, das im Bild unten angezeigt wird, wählen Sie AnchorModuleScript aus, klicken Sie auf ShareAnchorNetwork(), und speichern Sie.

    ![Module3hapter5step7im](images/module3chapter5step7im.PNG)

6. Wiederholen Sie Schritt 4, um die StartAzureSession ()-Funktion in StartAzureSessionButton einzuhängen.

7. Wiederholen Sie Schritt 4, um die CreateAzureAnchor ()-Funktion in CreateAzureAnchorButton einzuhängen, und überprüfen Sie, ob das TableAnchor-Objekt dem Parameterfeld ‚Game Object‘ der Funktion zugewiesen ist.

8. Befolgen Sie die Anweisungen unter [Verbinden der Szene mit der Azure-Ressource](mrlearning-asa-ch1.md#4-connect-the-scene-to-the-azure-resource), um Ihre Dienstanmeldeinformationen für Azure Spatial Anchors hinzuzufügen.

9. Um das Freigabemodul zu testen, klicken Sie auf die Schaltfläche „Start Azure ASA Session“ (Azure ASA-Sitzung starten), wodurch die Azure Spatial Anchors-Sitzung gestartet wird, und erstellen Sie dann den Azure-Anker, indem Sie auf die Schaltfläche „Create Azure Anchor“ (Azure Anchor erstellen) klicken. Warten Sie, bis der Azure-Anker erstellt wurde. Nachdem der Azure-Anker erstellt wurde, klicken Sie auf die Schaltfläche „Share Azure Anchor“ (Azure Anchor freigeben), um den erstellten Azure-Anker aus der HoloLens zu teilen.

10. Um den freigegebenen Azure Anchor in einer weiteren HoloLens zu empfangen, klicken Sie auf „Start Azure ASA Session“ (Azure ASA-Sitzung starten), um zu starten und zur aktuellen ASA-Sitzung zu gelangen

11. Klicken Sie auf die Schaltfläche „Get Azure Anchor“, um den freigegebenen Azure Anchor aus der anderen HoloLens abzurufen.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In dieser Lektion haben Sie gelernt, wie Sie die leistungsstarken neuen Spatial Anchors von Azure integrieren, um Geräte in einem gemeinsamen Bereich in einer gemeinsamen Erfahrung auszurichten. Damit ist das Freigabemodul abgeschlossen. Wir haben gelernt, wie ein neues Photon-Konto einrichtet wird, wie Photon und PUN in eine neue Unity-Anwendung integriert werden, Avatare und geteilte Objekte konfiguriert und schließlich mehrere Teilnehmer mithilfe von ASA ausgerichtet werden.
