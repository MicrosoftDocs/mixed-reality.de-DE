---
title: Lernen die Freigabe-Modul für HoloLens 2 MR
description: Führen Sie diesen Kurs erfahren, wie Sie mehrere Benutzer freigegebene Umgebungen innerhalb einer HoloLens-2-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 80cefb36ec1944ec6f537aafcbf4b63f7f812d26
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523297"
---
#  <a name="setting-up-photon-unity-networking"></a>Photon Unity Netzwerk einrichten

In diesem Tutorial erfahren wir, wie auf eine gemeinsame Erfahrung erstellen, durch den Import von Photon Unity Networking (WORTSPIEL) in Ihrem Unity-Projekt vorzubereiten. Photon ist eine von mehreren Netzwerken Optionen Mixed Reality-Entwicklern zur Verfügung, freigegebene Anwendungen zu schaffen. Es wird erfahren Sie, wie ein Photon-Konto erstellen, importieren Photon und erstellen einen optionalen lokalen Server

Ziele:

* Erfahren Sie, wie ein Photon-Konto erstellen

* Erfahren Sie, wie nach und importieren Sie Photon Unity Networking

* Einrichten eines lokalen Photon-Servers

  

### <a name="setting-up-photon"></a>Einrichten von Photon

1. Richten Sie eine [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) Konto. Navigieren Sie durch Klicken auf der Registrierungsseite für Photon [diesen Link](https://dashboard.photonengine.com/en-US/Account/SignUp). Befolgen Sie die Anweisungen auf der Registrierungsseite aus, um das Konto zu erstellen. 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)



![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

2. Erstellen Sie eine Anwendungs-ID durch Klicken auf das Erstellen einer neuen App-Schaltfläche.

![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

3. Wählen Sie aus dem Dropdownmenü unter Photon Photon WORTSPIEL. Klicken Sie dann benennen Sie sie. In diesem Beispiel den Namen wir HoloLensPhotonProject. Sobald Sie fertig sind, klicken Sie auf die Schaltfläche "erstellen".

![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

4. Sobald das geschehen ist, kehren Sie zu Ihrer Seite "Anwendungen" zurück und sollte in etwa der folgenden Abbildung. Klicken Sie auf die Anwendungs-ID, und kopieren Sie ihn. Fügen Sie ist etwas, das Sie auf einfache Weise zugreifen können.  

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

5. Erstellen eines neuen Unity-Projekts, und nennen Sie sie HLSharingProject aus. Anweisungen dazu, wie Sie ein neues Unity-Projekt erstellen, finden Sie unter [die Basis des Moduls "Unity-Projekt erstellen" im Abschnitt](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 

6. Nachdem das Projekt geladen wurde, klicken Sie auf der Registerkarte "Ressourcen-Store", wie in der folgenden Abbildung dargestellt. Klicken Sie dann in das Suchfeld in der folgenden Abbildung hervorgehoben wird, geben Sie in WORTSPIEL, und wählen die Photon WORTSPIEL-2 - FRE"Asset in den Suchergebnissen. 

![Module3Chapter1step10im](images/module3chapter1step10im.PNG)

7. Herunterladen Sie und importieren Sie dieses Medienobjekts durch Drücken der Tasten herunterladen und importieren.

![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

8. Sobald Photon der Importvorgang abgeschlossen ist, wird die Wortspiel-Assistent angezeigt. Nutzen Sie die Anwendungs-ID (die in die Zwischenablage sein sollte), in Schritt 4, und fügen Sie ihn in das App-ID-Feld aus, und drücken Sie die Schaltfläche "Setup-Projekt". 
![module3chapter1step12im](images/module3chapter1step12im.PNG)

9. Nachdem die App-ID wurde erfolgreich hinzugefügt wurde, navigieren Sie zu Photon PhotonUnityNetworking -> -> Ressourcen -> PhotonServerSettings in Objekte. Wählen Sie die Namenserver für die Verwendung-Option aus, und legen Sie die festen Bereich an uns oder YourPphoton-Service-Region.

   ![module3chapter1step13im](images/module3chapter1step13im.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben erfolgreich Photon-Konto erstellt, einen lokalen Photon-Server einrichten und WORTSPIEL in Unity importiert. Der nächste Schritt ist, richten Sie das Projekt, und lassen Sie Verbindungen mit anderen Benutzern, damit mehrere Benutzer Ihre Arbeit sehen können. 

[Nächsten Lernprogramm: Vorbereitung von Unity für die Entwicklung](mrlearning-sharing(photon)-ch2.md)

