---
title: 'Tutorials zu Mehrbenutzerfunktionen: 2 Vorbereiten von Unity für die Entwicklung'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: f7ae77d6978b5da860d890bcfe5b6f7c3d4640c8
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031238"
---
# <a name="2-getting-unity-ready-for-development"></a>2. Vorbereiten von Unity für die Entwicklung

In diesem Tutorial erfahren Sie, wie Sie Unity für die Anwendungsentwicklung vorbereiten und konfigurieren, einschließlich des Importierens des Mixed Reality-Toolkits, des Konfigurierens von Buildeinstellungen und des Vorbereitens der Szene.

## <a name="objectives"></a>Ziele

* Konfigurieren von Unity für die Anwendungsentwicklung
* Importieren des Mixed Reality-Toolkits
* Vorbereiten Ihrer Projektszene

## <a name="instructions"></a>Anweisungen

1. Laden Sie das Mixed Reality Toolkit Foundation-Unity-Paket herunter, und speichern Sie es, indem Sie [hier](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage) klicken.

2. Klicken Sie in Unity auf das Assets-Menü, wählen Sie „Import Package“ (Paket importieren) aus, und klicken Sie dann auf „Custom Package“ (Benutzerdefiniertes Paket).

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. Wählen Sie das Unity-Paket aus, das Sie soeben über den in Schritt 1 angegebenen Link heruntergeladen haben. Wenn das Popupfenster „Importieren“ in Unity angezeigt wird, klicken Sie auf die Schaltfläche „Importieren“, um mit dem Importieren des MRTK zu beginnen. Dieser Vorgang kann einige Minuten in Anspruch nehmen.

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    >Das heruntergeladene Paket befindet sich in Ihrem lokalen Ordner, in dem Sie die Datei gespeichert haben. Die Abbildung oben ist keine wahrheitsgemäße Darstellung des Speicherorts des Pakets.

    Nachdem das Paket importiert wurde, sollte das MRTK Project Configurator-Fenster (MRTK-Projektkonfiguration) angezeigt werden. Wenn das nicht der Fall ist, öffnen Sie es, indem Sie im Unity-Menü „Mixed Reality Toolkit > Utilities > Configure Unity Project“ (Mixed Reality-Toolkit > Utilitys > Unity-Projekt konfigurieren) auswählen.

    Erweitern Sie im MRTK Project Configurator-Fenster den Abschnitt „Modify Configurations“ (Konfigurationen ändern), deaktivieren Sie das Kontrollkästchen „Enable MSBuild for Unity“ (MSBuild für Unity aktivieren), achten Sie darauf, dass alle anderen Optionen aktiviert sind, und klicken Sie auf die Schaltfläche „Apply“ (Übernehmen), um die Einstellungen zu übernehmen.

    ![Module3Chapter2note1im](images/module3chapter2note1im-missing01.png)

    > [!CAUTION]
    > MSBuild für Unity unterstützt möglicherweise nicht alle verwenden SDKs, und die Deaktivierung nach der erstmaligen Aktivierung kann schwierig sein. Es wird daher dringend empfohlen, MSBuild für Unity nicht zu aktivieren.
    
4. Erstellen Sie eine neue Szene. Sie können hierzu auf „Datei“ klicken und „Neue Szene“ auswählen. Speichern Sie sie als HLSharedProjectMain.

5. Klicken Sie unter Mixed Reality-Toolkit auf „Zur Szene hinzufügen und konfigurieren“.

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. Sobald das erledigt ist, wählen Sie in der Hierarchie „Mixed-Reality Toolkit (MRTK)“ aus. Ändern Sie im Inspektorbereich das MRTK-Konfigurationsprofil in DefaultHoloLens2ConfigurationProfile.

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima-missing01.png)

7. Wählen Sie in der Hierarchie „Mixed Reality-Toolkit (MRTK)“ aus. Suchen Sie im Inspektorbereich nach dem Mixed Reality-Toolkitskript, und wählen Sie die Schaltfläche „Copy & Customize“ (Kopieren und anpassen) aus, wie in der Abbildung unten dargestellt.  Darauf hin wird ein Pop angezeigt, und Sie können im Popupmenü eine Klonoption auswählen.

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. Scrollen Sie nach unten, und deaktivieren Sie „Enable Diagnostics-System“, wenn Sie das Diagnosefenster ausblenden möchten. Wir empfehlen, das Diagnosefenster während der Anwendungsentwicklung aktiviert zu lassen, um die Leistung zu überwachen, und es anschließend im Produktionsbetrieb oder bei Demos der Anwendung zu deaktivieren. 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. Öffnen Sie die Buildeinstellungen, indem Sie STRG+UMSCHALT+B drücken oder zu „Datei > Buildeinstellungen“ wechseln. Beachten Sie, dass das Programm derzeit unter der eigenständigen PC-, Mac- und Linux-Plattform konfiguriert ist. Legen Sie für die HoloLens 2-Entwicklung die Plattform auf Universelle Windows-Plattform fest. Wählen Sie sie aus, und klicken Sie auf „Switch Platform“ (Plattform wechseln).

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. Klicken Sie nach Abschluss des Vorgangs auf das Feld mit der Bezeichnung „Add Open Scenes“ (Offene Szenen hinzufügen). Navigieren Sie jetzt zum Inspektorbereich, und vergewissern Sie sich, dass das Kontrollkästchen rechts neben „Virtual Reality Supported“ (Virtual Reality unterstützt) aktiviert ist (wie in der Abbildung unten dargestellt). Stellen Sie ferner sicher, dass das Kontrollkästchen neben „scenes/HLSharedProjectMain“ ebenfalls aktiviert ist, wie in der folgenden Abbildung dargestellt.

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. Scrollen Sie im Abschnitt „Publishing Settings“ (Veröffentlichungseinstellungen) nach unten bis zu „Capabilities“ (Funktionen), und stellen Sie sicher, dass die folgenden Kontrollkästchen aktiviert sind:

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. Importieren Sie die aufgelisteten benutzerdefinierten Pakete:

    * [AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (Version 2.1.1)
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)
    * [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    >Wenn Sie eine Auffrischung zum Konfigurieren eines Unity-Projekts für Azure Spatial Anchors benötigen, lesen Sie das Tutorial [Erste Schritte mit Azure Spatial Anchors](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1), das Teil der [Azure Spatial Anchor](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1)-Tutorialreihe ist.


13. Wechseln Sie im Projektbereich zum Ordner „Prefabs“. In den folgenden Schritten implementieren Sie einige Prefabs in der Szene. Klicken Sie im Ordner „Prefabs“ auf das Fenster „Prefab, Debug“, und ziehen Sie es in die Hierarchie. Nachdem Sie dies abgeschlossen haben, speichern Sie das Projekt, indem Sie auf „Datei“ klicken, und speichern Sie dann, oder drücken Sie STRG+S.

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    Möglicherweise wird ein Popup angezeigt, wenn Sie auf das Prefab klicken, das TMP Essentials anfragt. Klicken Sie in diesem Fall auf „Import TMP Essentials“, da diese erforderlich sind. Wenn dieses Popup angezeigt wird, müssen Sie möglicherweise das Prefab aus Ihrer Hierarchie löschen und es erneut in Ihre Hierarchie ziehen, um mögliche Fehler im Zusammenhang mit Text zu vermeiden.

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Ihr Unity-Projekt ist jetzt für Photon bereit. In den nächsten Tutorials bauen wir auf dieser Szene und unserem Unity-Projekt auf, mit dem Ziel einer vollständigen gemeinsamen Benutzererfahrung.

[Nächstes Tutorial: 3. Verbinden mehrerer Benutzer](mrlearning-sharing(photon)-ch3.md)
