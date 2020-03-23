---
title: 'Tutorials zu Mehrbenutzerfunktionen: 1 Einrichten von Photon Unity Networking'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 94068ff706e0e56ca8ec0f23beaed3a34159b777
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031330"
---
# <a name="1-setting-up-photon-unity-networking"></a>1. Einrichten von Photon Unity Networking

## <a name="overview"></a>Übersicht

In diesem Tutorial erfahren Sie, wie Sie sich auf das Erstellen einer gemeinsamen Benutzeroberfläche vorbereiten, indem Sie das Photon Unity-Netzwerk (PUN) in Ihr Unity-Projekt importieren. Photon ist eine von mehreren Netzwerkoptionen, die Mixed Reality-Entwicklern zum Erstellen gemeinsamer Benutzererfahrungen zur Verfügung stehen. Sie erfahren, wie Sie ein Photon-Konto erstellen, Photon importieren und einen optionalen lokalen Server erstellen.

## <a name="objectives"></a>Ziele

* Erlernen des Erstellens eines Photon-Kontos
* Erfahren, wie Photon Unity Networking gesucht und importiert wird
* Einrichten eines lokalen Photon-Servers

## <a name="prerequisites"></a>Voraussetzungen

>[!TIP]
>Wenn Sie die Tutorialreihen [Tutorials zu den ersten Schritten](mrlearning-base.md) und [Einstieg in Azure Spatial Anchors](mrlearning-asa-ch1.md) noch nicht abgeschlossen haben, empfiehlt es sich, zunächst diese Tutorials abzuschließen.

* Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](install-the-tools.md) ist
* Windows 10 SDK (10.0.18362.0 oder höher)
* Grundlagenkenntnisse in der C#-Programmierung
* Ein für die [Entwicklung konfiguriertes](using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät

>[!IMPORTANT]
> Die empfohlene Unity-Version für diese Tutorialreihe ist Unity 2019.2.X. Diese übertrifft alle Versionsanforderungen oder -empfehlungen, die in den oben verlinkten Voraussetzungen angegeben sind.

## <a name="setting-up-photon"></a>Einrichten von Photon

1. Richten Sie ein [Photon](https://dashboard.photonengine.com//Account/SignUp)-Konto ein. Navigieren Sie über [diesen Link](https://dashboard.photonengine.com//Account/SignUp) zur Registrierungsseite von Photon. Befolgen Sie die Anweisungen auf der Registrierungsseite, um das Konto zu erstellen.

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. Erstellen Sie eine Anwendungs-ID, indem Sie auf die Schaltfläche „Create a New App“ (Neue App erstellen) klicken.

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. Wählen Sie im Dropdownmenü unter „Photon Type“ das Element „Photon PUN“ aus. Geben Sie ihm dann einen Namen. In diesem Beispiel haben wir es „HoloLensPhotonProject“ benannt. Wenn Sie damit fertig sind, klicken Sie auf die Erstellen-Schaltfläche.

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. Wenn Sie zu Ihrer Anwendungsseite zurückkehren, sollten Sie etwas ähnlich der Abbildung unten sehen. Klicken Sie auf die Anwendungs-ID, und kopieren Sie sie. Fügen Sie sie an einem beliebigen Ort ein, auf den Sie leicht zugreifen können.  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. Erstellen Sie ein neues Unity-Projekt, und benennen Sie es HLSharingProject. Anweisungen zum Erstellen eines neuen Unity-Projekts finden Sie im [Abschnitt „Unity-Projekt erstellen“ des Basismoduls](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 

6. Nachdem das Projekt geladen wurde, klicken Sie auf die Registerkarte „Assets Store“, wie in der Abbildung unten dargestellt. Geben Sie dann im Suchfeld, das in der Abbildung unten hervorgehoben ist, „PUN“ ein, und wählen Sie in den Suchergebnissen die Ressource „Photon PUN 2 - FREE“ aus.

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. Sie können diese Ressource durch Drücken der Schaltflächen „Herunterladen“ und „Importieren“ herunterladen und importieren.

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Nachdem Photon den Importvorgang abgeschlossen hat, wird der PUN-Assistent angezeigt. Nehmen Sie die Anwendungs-ID aus Schritt 4 (die sich in Ihrer Zwischenablage befinden sollte), fügen Sie sie in das AppID-Feld ein, und drücken Sie die Schaltfläche „Setup Project“ (Projekt einrichten).

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. Nach erfolgreichem Hinzufügen der AppID navigieren Sie in „Assets“ zu „Photon > PhotonUnityNetworking > Resources > PhotonServerSettings“. Wählen Sie die Option „Use Name Server“ (Namensserver verwenden) aus, und legen Sie die feste Region auf US oder auf die Region Ihres Photon-Diensts fest.

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben erfolgreich ein Photon-Konto erstellt, einen lokalen Photon-Server eingerichtet und PUN in Unity importiert. Der nächste Schritt besteht darin, das Projekt einzurichten und Verbindungen mit anderen Benutzern zuzulassen, damit mehrere Benutzer Ihre Arbeit sehen können.

[Nächstes Tutorial: 2. Vorbereiten von Unity für die Entwicklung](mrlearning-sharing(photon)-ch2.md)
