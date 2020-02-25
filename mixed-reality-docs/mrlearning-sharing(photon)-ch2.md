---
title: Lernprogramme für Mehrbenutzerfunktionen-2. Vorbereiten von Unity für die Entwicklung
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Umgebungen mit mehreren Benutzern in einer hololens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 2bcec7e70949186c6e711120c36ee8649c006ec7
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553836"
---
# <a name="2-getting-unity-ready-for-development"></a>2. Vorbereiten von Unity für die Entwicklung

In diesem Tutorial erfahren Sie, wie Sie Unity für die Anwendungsentwicklung vorbereiten und konfigurieren, einschließlich Importieren des Mixed Reality Toolkit, Konfigurieren von Buildeinstellungen und Vorbereiten der Szene.

## <a name="objectives"></a>Ziele

* Konfigurieren von Unity für die Anwendungsentwicklung
* Importieren des Mixed Reality-Toolkits
* Vorbereiten der Projekt Szene

## <a name="instructions"></a>Anweisungen

1. Klicken Sie hier, um das Mixed Reality Toolkit Foundation-Unity-Paket herunterzuladen und zu speichern [.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)

2. Klicken Sie in Unity auf das Menü Assets, wählen Sie Paket importieren aus, und klicken Sie dann auf benutzerdefiniertes Paket.

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. Wählen Sie das Unity-Paket aus, das Sie soeben aus dem in Schritt 1 angegebenen Link heruntergeladen haben. Nachdem das Popup Fenster Importieren in Unity angezeigt wird, klicken Sie auf die Schaltfläche Importieren, um mit dem Importieren von mrtk zu beginnen. Dieser Vorgang kann einige Minuten in Anspruch nehmen.

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    >Das heruntergeladene Paket befindet sich in Ihrem lokalen Ordner, in dem Sie die Datei gespeichert haben. In der Abbildung oben wird nicht dargestellt, wo Sie das Paket finden.

    Nachdem das Paket importiert wurde, sollte das MRTK Project Configurator-Fenster (MRTK-Projektkonfiguration) angezeigt werden. Wenn dies nicht der Fall ist, öffnen Sie es, indem Sie Mixed Reality Toolkit > Utilities > Konfigurieren des Unity-Projekts im Unity-Menü auswählen.

    Erweitern Sie im Fenster des mrtk-projektkonfigurators den Abschnitt Konfigurationen ändern, deaktivieren Sie das Kontrollkästchen MSBuild für Unity aktivieren, stellen Sie sicher, dass alle anderen Optionen aktiviert sind, und klicken Sie auf die Schaltfläche anwenden, um die Einstellungen zu übernehmen.

    ![Module3Chapter2note1im](images/module3chapter2note1im-missing01.png)

    > [!CAUTION]
    > MSBuild für Unity unterstützt möglicherweise nicht alle verwenden SDKs, und die Deaktivierung nach der erstmaligen Aktivierung kann schwierig sein. Es wird daher dringend empfohlen, MSBuild für Unity nicht zu aktivieren.
    
4. Erstellen Sie eine neue Szene. Klicken Sie hierzu auf Datei, und wählen Sie neue Szene aus. Speichern Sie Sie als hlsharedprojectmain.

5. Klicken Sie unter Mixed Reality Toolkit auf zur Szene hinzufügen und konfigurieren.

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. Wählen Sie nach Abschluss des Vorgangs Mixed-Reality Toolkit (mrtk) aus der Hierarchie aus. Ändern Sie im Inspektor-Panel das mrtk-Konfigurations Profil in DefaultHoloLens2ConfigurationProfile.

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima-missing01.png)

7. Wählen Sie in der Hierarchie Mixed-Reality Toolkit (mrtk) aus. Suchen Sie im Inspektor-Panel nach dem Mixed Reality Toolkit-Skript, und klicken Sie auf die Schaltfläche zum Kopieren & anpassen, wie in der folgenden Abbildung dargestellt.  Danach wird ein Pop angezeigt, und wählen Sie im Popupmenü die Option Klonen aus.

    ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

    ![Module3Chapter2step6imd](images/module3chapter2step6imd.PNG)

8. Scrollen Sie nach unten, und deaktivieren Sie Diagnosesystem aktivieren, wenn Sie das Diagnosefenster ausblenden möchten. Es wird empfohlen, das Diagnosefenster während der Anwendungsentwicklung zu aktivieren, um die Leistung zu überwachen und es dann während der Produktions-oder Anwendungs Demos zu deaktivieren. 

    ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

9. Öffnen Sie die Buildeinstellungen, indem Sie STRG + UMSCHALT + B drücken, oder wechseln Sie zu Datei > Buildeinstellungen. Beachten Sie, dass das Programm derzeit unter der eigenständigen PC-, Mac-und Linux-Plattform festgelegt ist. Legen Sie für die Entwicklung von hololens 2 die Plattform auf universelle Windows-Plattform fest. Wählen Sie es aus, und klicken Sie auf Plattform wechseln.

    ![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

10. Klicken Sie nach Abschluss des Vorgangs auf das Feld mit dem Namen offene Szenen hinzufügen Wechseln Sie nun zum Inspektor-Panel, und stellen Sie sicher, dass das Kontrollkästchen rechts von Virtual Reality unterstützt wird (wie in der folgenden Abbildung dargestellt). Stellen Sie außerdem sicher, dass das Kontrollkästchen nebenszenen/hlsharedprojectmain ebenfalls aktiviert ist, wie in der folgenden Abbildung dargestellt.

    ![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

11. Scrollen Sie im Bereich Inspector im Bereich Veröffentlichungs Einstellungen nach unten zu Funktionen, und stellen Sie sicher, dass die folgenden Kontrollkästchen markiert sind:

    ![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

12. Importieren Sie die aufgelisteten benutzerdefinierten Pakete:

    * [Azurespatialanchor. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (Version 2.1.1)
    * [Mrtk. HoloLens2. Unity. Tutorials. Assets. GettingStarted. 2.3.0.2. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
    * [Mrtk. HoloLens2. Unity. Tutorials. Assets. azurespatialanchor. 2.3.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)
    * [Mrtk. HoloLens2. Unity. Tutorials. Assets. multiuserfunktionalitäten. 2.1.0.1. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.1.0.1.unitypackage)

    >[!TIP]
    >Eine Erinnerung zum Konfigurieren eines Unity-Projekts für räumliche Azure-Anker finden Sie im Tutorial zu den ersten Schritten [mit Azure Spatial](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) Anchor, das Teil der tutorialreihe für [räumliche Azure](https://docs.microsoft.com/windows/mixed-reality/mrlearning-asa-ch1) -Anker ist.


13. Wechseln Sie im Projekt Panel zum Ordner Prefabs. In den folgenden Schritten implementieren Sie einige Prefabs in der Szene. Klicken Sie im Ordner Prefabs auf das Fenster Prefab, Debug, und ziehen Sie es in die Hierarchie. Wenn Sie fertig sind, speichern Sie das Projekt, indem Sie auf Datei und dann auf Speichern klicken oder STRG + S drücken.

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    Sie werden möglicherweise feststellen, dass ein Popup Fenster angezeigt wird, wenn Sie auf die vorfab klicken und Sie zu tmp Essentials auffordern. Klicken Sie auf tmp Essentials nach Bedarf importieren. Wenn dieses Popup Fenster angezeigt wird, müssen Sie möglicherweise die vorfab aus Ihrer Hierarchie löschen und in ihre Hierarchie ziehen, um potenzielle Text bezogene Fehler zu vermeiden.

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Ihr Unity-Projekt ist nun für das Photon bereit. In den nächsten Tutorials bauen wir auf dieser Szene und unserem Unity-Projekt auf, um eine vollständige gemeinsame Nutzung zu ermöglichen.

[Nächstes Tutorial: 3. Verbinden von mehreren Benutzern](mrlearning-sharing(photon)-ch3.md)
