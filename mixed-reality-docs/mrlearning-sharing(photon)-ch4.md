---
title: 'Tutorials zu Mehrbenutzerfunktionen: 4 Freigeben von Objektbewegungen für mehrere Benutzer'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: b0ddf0799fd94c29ce8f1221c55073cd77b63703
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031246"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. Freigeben von Objektbewegungen für mehrere Benutzer

In diesem Tutorial erfahren Sie, wie Sie die Bewegungen von Objekten teilen, damit alle Teilnehmer einer freigegebenen Sitzung zusammenarbeiten und die Interaktionen der einzelnen Benutzer anzeigen können. Diese Lektion baut auf der Mondstartbasis auf, die im Rahmen der [Basismodul-Tutorials](mrlearning-base.md) erstellt wurde.

## <a name="objectives"></a>Ziele

- Einbringen der Mondstartbasis als zu teilendes 3D-Modell
- Konfigurieren des Projekts zum Teilen der Bewegungen des 3D-Modells
- Erlernen des Erstellens einer einfachen Mehrbenutzeranwendung zur Zusammenarbeit

## <a name="instructions"></a>Anweisungen

1. Speichern Sie die Szene aus der vorherigen Lektion (STRG+S). Sie können sie HLSharedProjectMainPart4.unity benennen, damit sie leichter zu finden ist, wenn Sie sie benötigen.

2. Doppelklicken Sie im Projektfenster im Ordner „Assets > Scripts“ (Ressourcen > Skripts) auf „GenericNetSync“, um es in Visual Studio oder einem beliebigen anderen Editor, den Sie verwenden, zu öffnen.  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. Entfernen Sie in den Zeilen 34 und 38 "//", um den Code für die Tabelle zu aktivieren, die Sie in dieser Lektion verwenden werden. Speichern Sie dann die Datei.

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. Doppelklicken Sie im Projektfenster im Ordner „Assets > Scripts“ auf die Datei „PhotonRoom.cs“, um sie in Visual Studio zu öffnen.

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. Wie schon in Schritt 3 müssen wir "//" entfernen, um den Code in den Zeilen 25, 26 und 106 zu aktivieren.

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. Wählen Sie in der Hierarchieansicht das NetworkRoom-Objekt aus.

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. Navigieren Sie in der Projektansicht zu „Assets > Resources > Prefabs“. Ziehen Sie das Table-Prefab auf den Tableprefab-Slot der PhotonRoom-Klasse. Ziehen Sie als nächstes das RocketLauncherCompleteVariantprefab auf den Slot „Module Prefab“ der PhotonRoom-Klasse.

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    >Wenn Sie auf eins der Prefab-Objekte klicken und die Maustaste loslassen, wechselt der Inspektor zu dem betreffenden Objekt. Legen Sie jedes Objekt durch Klicken, Ziehen, Ablegen und Freigeben auf seinem passenden Slot ab.

8. Klicken Sie auf den Pfeil links neben MixedRealityPlayspace, und verschieben Sie das untergeordnete Spielobjekt MainCamera nach unten auf das SharedPlayground-Prefab. Löschen Sie anschließend das MixedRealityPlayspace-Prefab, indem Sie das Prefab auswählen und auf der Tastatur ENTF drücken.

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    >Vergewissern Sie sich, dass die Positionen von „Main Camera“ ebenso wie von „SharedPlayground“ auf 0,0,0 festgelegt sind.

9. Wählen Sie das SharedPlayground-Objekt aus, und klicken Sie mit der rechten Maustaste, um die Option „create empty“ (Leer erstellen) auszuwählen, um ein leeres Spielobjekt als untergeordnetes Objekt des Spielobjekts „SharedPlayground“ zu erstellen.

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. Ändern Sie bei in der Hierarchie ausgewähltem neuem Objekt den Namen des Objekts im Inspektorbereich in „TableAnchor“. Klicken Sie außerdem auf „Komponente hinzufügen“, und suchen Sie nach der TableAnchor-Komponente. Wählen Sie sie aus, und fügen Sie sie dem-Objekt hinzu.

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. Ziehen Sie aus dem Projektbereich im Prefabs-Ordner das Table-Prefab auf das untergeordnete „TableAnchor“-Objekt, das Sie soeben erstellt haben.

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sobald dies erledigt ist, sehen Sie sich um, um das Mondmodul zu finden. Anschließend können alle Benutzer, die Ihrem Unity-Projekt beitreten, die Mondstartbasis bewegen.  Alle Bewegungen werden synchronisiert, sodass jeder Benutzer die Interaktionen der anderen Benutzer sehen kann. Diese Konzepte dienen als Grundbausteine für voll ausgestattete, gemeinsam genutzte Umgebungen zur Zusammenarbeit.

Obwohl alle Benutzer als Teil einer geteilten Umgebung verbunden sind und die relativen Bewegungen von Objekten sehen können, fehlt der Anwendung noch die Möglichkeit, Avatare und Objekte genau auszurichten, sodass lokale Benutzer nicht in der Lage sind, einander und Objekte am gleichen Ort in der physischen Welt zu sehen. Um ein lokales gemeinsames Benutzererlebnis zu verankern, benötigt jedes Gerät ein gemeinsames Verständnis der physischen Umgebung. In diesem Modul erreichen wir dies mithilfe von [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA), die in der nächsten Lektion implementiert werden.

Bevor Sie mit der nächsten Lektion fortfahren, müssen wir das ASA-Lernmodul abschließen, das die ASA-Grundlagen, die Erstellung von Azure-Konten und Ressourcen sowie weitere Grundbausteine behandelt, die für die Integration in unserer geteilten Benutzerumgebung erforderlich sind.

[Nächste Lektion: 5. Integrieren von Azure Spatial Anchors in eine gemeinsam genutzte Umgebung](mrlearning-sharing(photon)-ch5.md)
