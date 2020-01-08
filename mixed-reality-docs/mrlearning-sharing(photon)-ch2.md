---
title: Lernprogramme für Mehrbenutzerfunktionen-2. Vorbereiten von Unity für die Entwicklung
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Umgebungen mit mehreren Benutzern in einer hololens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 6840bcc583fe3e42dcaa6f42e71098f4dbe76f4c
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334312"
---
# <a name="2-getting-unity-ready-for-development"></a>2. Vorbereiten von Unity für die Entwicklung

In diesem Tutorial erfahren Sie, wie Sie Unity für die Anwendungsentwicklung vorbereiten und konfigurieren, einschließlich Importieren des Mixed Reality Toolkit, Konfigurieren von Buildeinstellungen und Vorbereiten der Szene.

## <a name="objectives"></a>Ziele

* Konfigurieren von Unity für die Anwendungsentwicklung
* Importieren des Mixed Reality-Toolkits
* Vorbereiten der Projekt Szene

## <a name="instructions"></a>Anweisungen

1. Klicken Sie hier, um das Mixed Reality Toolkit Foundation-Unity-Paket herunterzuladen und zu speichern [.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)

2. Klicken Sie in Unity auf das Menü Assets, wählen Sie Paket importieren aus, und klicken Sie dann auf benutzerdefiniertes Paket.

    ![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. Wählen Sie das Unity-Paket aus, das Sie soeben aus dem in Schritt 1 angegebenen Link heruntergeladen haben. Nachdem das Popup Fenster Importieren in Unity angezeigt wird, klicken Sie auf die Schaltfläche Importieren, um mit dem Importieren von mrtk zu beginnen. Dieser Vorgang kann einige Minuten in Anspruch nehmen.

    ![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

    >[!NOTE]
    >Das heruntergeladene Paket befindet sich in Ihrem lokalen Ordner, in dem Sie die Datei gespeichert haben. In der Abbildung oben wird nicht dargestellt, wo Sie das Paket finden.

4. Erstellen Sie eine neue Szene. Klicken Sie hierzu auf Datei, und wählen Sie neue Szene aus. Speichern Sie Sie als hlsharedprojectmain.

    Möglicherweise wird ein Popup Fenster angezeigt, das ähnlich wie in der folgenden Abbildung aussieht. Klicken Sie vorerst auf Nein.
    ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. Klicken Sie unter Mixed Reality Toolkit auf zur Szene hinzufügen und konfigurieren.

    ![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. Sobald der Vorgang beendet ist, wird eine neue Konfigurationsdatei angezeigt, die Ihnen die Möglichkeit gibt, das Profil anzupassen.

    ![Module2Chapter1step4ima](images/Module2Chapter1step4ima.PNG)

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

    ein. [Unity. HoloLens2. GettingStarted. Tutorials. Asset. 2.1.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.0/Unity.HoloLens2.GettingStarted.Tutorials.Asset.2.1.0.0.unitypackage)

    b. [Unity. HoloLens2. multiuserfunktionalitäten. Tutorials. Asset. 2.1.0.0. unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.1.0.0/Unity.HoloLens2.MultiUserCapabilities.Tutorials.Asset.2.1.0.0.unitypackage)

    >[!TIP]
    >Wenn Sie die [Tutorials zu](mrlearning-base-ch1.md)den ersten Schritten abgeschlossen haben, ist das Unity-Paket mit dem Namen _Unity. HoloLens2. GettingStarted. Tutorials. Asset. 2.1.0.0. unitypackage_ auf dem Computer gespeichert. Wenn dies der Fall ist, können Sie das Herunterladen des in Schritt a aufgeführten Assets überspringen.

    ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

13. Wechseln Sie im Projekt Panel zum Ordner Prefabs. In den folgenden Schritten implementieren Sie einige Prefabs in der Szene. Klicken Sie im Ordner Prefabs auf das Fenster Prefab, Debug, und ziehen Sie es in die Hierarchie. Wenn Sie fertig sind, speichern Sie das Projekt, indem Sie auf Datei und dann auf Speichern klicken oder STRG + S drücken.

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

    Sie werden möglicherweise feststellen, dass ein Popup Fenster angezeigt wird, wenn Sie auf die vorfab klicken und Sie zu tmp Essentials auffordern. Klicken Sie auf tmp Essentials nach Bedarf importieren. Wenn dieses Popup Fenster angezeigt wird, müssen Sie möglicherweise die vorfab aus Ihrer Hierarchie löschen und in ihre Hierarchie ziehen, um potenzielle Text bezogene Fehler zu vermeiden.

    ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Ihr Unity-Projekt ist nun für das Photon bereit. In den nächsten Tutorials bauen wir auf dieser Szene und unserem Unity-Projekt auf, um eine vollständige gemeinsame Nutzung zu ermöglichen.

[Nächstes Tutorial: 3. Verbinden von mehreren Benutzern](mrlearning-sharing(photon)-ch3.md)
