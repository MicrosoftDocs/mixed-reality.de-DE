---
title: Lernprogramme für Mehrbenutzerfunktionen-1. Einrichten von Photon Unity-Netzwerken
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Umgebungen mit mehreren Benutzern in einer hololens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: acb6966ace81180e95e6a0fe447d350572f7c0dd
ms.sourcegitcommit: af1602710c1ccb7ed870a491923350d387706129
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701968"
---
#  <a name="1-setting-up-photon-unity-networking"></a>1. Einrichten von Photon Unity-Netzwerken

In diesem Tutorial erfahren Sie, wie Sie sich für das Erstellen einer gemeinsamen Benutzeroberfläche vorbereiten, indem Sie das Photon Unity-Netzwerk (pun) in Ihr Unity-Projekt importieren. Bei "Photon" handelt es sich um eine von mehreren Netzwerkoptionen, die für Mixed Reality-Entwickler zur Verfügung stehen Wir erfahren, wie ein Photon-Konto erstellt, ein Photon importiert und ein optionaler lokaler Server erstellt wird.

## <a name="objectives"></a>Ziele

* Erfahren Sie, wie Sie ein Photon-Konto erstellen.

* Erfahren Sie, wie Sie das Unity-Netzwerk von Photon suchen und importieren

* Einrichten eines lokalen-Photon-Servers

  

## <a name="setting-up-photon"></a>Einrichten von PHOTON

1. Richten Sie ein [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) -Konto ein. Navigieren Sie zur Anmeldeseite von PHOTON, indem Sie auf [diesen Link](https://dashboard.photonengine.com/en-US/Account/SignUp)klicken. Befolgen Sie die Anweisungen auf der Registrierungsseite, um das Konto zu erstellen. 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. Erstellen Sie eine Anwendungs-ID, indem Sie auf die Schaltfläche Neue APP erstellen klicken.

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. Wählen Sie im Dropdown Menü unter "Photon Type" den Typ "Photon" aus. Benennen Sie dann den Namen. In diesem Beispiel nennen wir es hololersphutonproject. Klicken Sie anschließend auf die Schaltfläche erstellen.

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. Sobald dies erfolgt ist, kehren Sie zur Seite "Anwendungen" zurück, und es sollte etwas ähnlich der folgenden Abbildung angezeigt werden. Klicken Sie auf die Anwendungs-ID, und kopieren Sie Sie. Fügen Sie Sie an einer beliebigen Stelle ein.  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. Erstellen Sie ein neues Unity-Projekt, und nennen Sie es hlsharingproject. Anweisungen zum Erstellen eines neuen Unity-Projekts finden Sie [im Abschnitt "Erstellen eines Unity-Projekts" des Basismoduls](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 

6. Nachdem das Projekt geladen wurde, klicken Sie auf die Registerkarte Ressourcen Speicher, wie in der folgenden Abbildung dargestellt. Geben Sie dann im Suchfeld, das in der folgenden Abbildung hervorgehoben ist, das Wort "wortwort" ein, und wählen Sie in den Suchergebnissen das Objekt "Photon pun 2-Free" aus. 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. Sie können dieses Asset durch Drücken der Schaltflächen herunterladen und importieren herunterladen und importieren.

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Nachdem der Import Vorgang von Photon abgeschlossen wurde, wird der pun-Assistent angezeigt. Verwenden Sie die Anwendungs-ID (die sich in der Zwischenablage befinden sollte) aus Schritt 4, und fügen Sie Sie in das Feld "AppID" ein, und klicken Sie auf die Schaltfläche Projekt einrichten. 
![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. Nachdem Sie die AppID erfolgreich hinzugefügt haben, navigieren Sie zu "Photon-> photonunitynetworking-> Resources->" photonserversettings "in" Assets ". Wählen Sie die Option Namen Server verwenden aus, und legen Sie den Bereich für die festgelegte Region auf US oder Ihren Bereich für den Photonen Dienst

![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben erfolgreich ein Photon-Konto erstellt, einen lokalen-Photon-Server eingerichtet und ein Wortspiel in Unity importiert. Der nächste Schritt besteht darin, das Projekt einzurichten und dann Verbindungen mit anderen Benutzern zuzulassen, damit mehrere Benutzer ihre Arbeit sehen können. 

[Nächstes Tutorial: 2. Vorbereiten von Unity für die Entwicklung](mrlearning-sharing(photon)-ch2.md)

