---
title: Lernprogramme für Mehrbenutzerfunktionen-1. Einrichten von Photon Unity-Netzwerken
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Umgebungen mit mehreren Benutzern in einer hololens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: d879144c7097d8b3873618f986b9f169e8553fa8
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553818"
---
# <a name="1-setting-up-photon-unity-networking"></a>1. Einrichten der Einrichtung von Photon Unity-Netzwerken

## <a name="overview"></a>Übersicht

In diesem Tutorial erfahren Sie, wie Sie sich auf das Erstellen einer gemeinsamen Benutzeroberfläche vorbereiten, indem Sie das Photon Unity-Netzwerk (pun) in Ihr Unity-Projekt importieren. Bei "Photon" handelt es sich um eine von mehreren Netzwerkoptionen, die für Mixed Reality-Entwickler zur Verfügung stehen Sie erfahren, wie Sie ein Photon-Konto erstellen, ein Photon importieren und einen optionalen lokalen Server erstellen.

## <a name="objectives"></a>Ziele

* Erfahren Sie, wie Sie ein Photon-Konto erstellen.
* Erfahren Sie, wie Sie das Unity-Netzwerk von Photon suchen und importieren
* Einrichten eines lokalen-Photon-Servers

## <a name="prerequisites"></a>Erforderliche Komponenten

>[!TIP]
>Wenn Sie die Lernprogramme "erste Schritte" und " [Azure Spatial](mrlearning-asa-ch1.md) Anchor" noch nicht abgeschlossen haben, empfiehlt es sich, [diese Tutorials zuerst](mrlearning-base.md) abzuschließen.

* Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](install-the-tools.md) ist
* Windows 10 SDK (10.0.18362.0 oder höher)
* Grundlagenkenntnisse in der C#-Programmierung
* Ein für die [Entwicklung konfiguriertes](using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät

>[!IMPORTANT]
> Die empfohlene Unity-Version für diese Tutorialreihe ist Unity 2019.2.X. Diese übertrifft alle Versionsanforderungen oder -empfehlungen, die in den oben verlinkten Voraussetzungen angegeben sind.

## <a name="setting-up-photon"></a>Einrichten von PHOTON

1. Richten Sie ein [Photon](https://dashboard.photonengine.com//Account/SignUp) -Konto ein. Navigieren Sie zur Anmeldeseite von PHOTON, indem Sie auf [diesen Link](https://dashboard.photonengine.com//Account/SignUp)klicken. Befolgen Sie die Anweisungen auf der Registrierungsseite, um das Konto zu erstellen.

    ![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

    ![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. Erstellen Sie eine Anwendungs-ID, indem Sie auf die Schaltfläche Neue APP erstellen klicken.

    ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. Wählen Sie im Dropdown Menü unter "Photon Type" den Typ "Photon" aus. Benennen Sie dann den Namen. In diesem Beispiel nennen wir es hololersphutonproject. Klicken Sie anschließend auf die Schaltfläche erstellen.

    ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. Kehren Sie zur Seite "Anwendungen" zurück, und es sollte etwas ähnlich der folgenden Abbildung angezeigt werden. Klicken Sie auf die Anwendungs-ID und kopieren Sie Sie. Fügen Sie Sie an einer beliebigen Stelle ein.  

    ![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. Erstellen Sie ein neues Unity-Projekt, und nennen Sie es hlsharingproject. Anweisungen zum Erstellen eines neuen Unity-Projekts finden Sie [im Abschnitt "Erstellen eines Unity-Projekts" des Basismoduls](https://docs.microsoft.com//windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 

6. Nachdem das Projekt geladen wurde, klicken Sie auf die Registerkarte Ressourcen Speicher, wie in der folgenden Abbildung dargestellt. Geben Sie dann im Suchfeld, das in der folgenden Abbildung hervorgehoben ist, das Wort "wortwort" ein, und wählen Sie in den Suchergebnissen das Objekt "Photon pun 2-Free" aus.

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. Sie können dieses Asset durch Drücken der Schaltflächen herunterladen und importieren herunterladen und importieren.

    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Nachdem der Import Vorgang von Photon abgeschlossen wurde, wird der pun-Assistent angezeigt. Verwenden Sie die Anwendungs-ID (die sich in der Zwischenablage befinden sollte) aus Schritt 4, fügen Sie Sie in das Feld AppID ein, und klicken Sie auf die Schaltfläche Projekt einrichten.

    ![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. Nachdem Sie die AppID erfolgreich hinzugefügt haben, navigieren Sie zu "Photon-> photonunitynetworking-> Resources->" photonserversettings "in" Assets ". Wählen Sie die Option Namen Server verwenden aus, und legen Sie den Bereich für die festgelegte Region auf US oder Ihren Bereich für den Photonen Dienst

    ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben erfolgreich ein Photon-Konto erstellt, einen lokalen-Photon-Server eingerichtet und ein Wortspiel in Unity importiert. Der nächste Schritt besteht darin, das Projekt einzurichten und Verbindungen mit anderen Benutzern zuzulassen, damit mehrere Benutzer ihre Arbeit sehen können.

[Nächstes Tutorial: 2. Vorbereiten von Unity für die Entwicklung](mrlearning-sharing(photon)-ch2.md)
