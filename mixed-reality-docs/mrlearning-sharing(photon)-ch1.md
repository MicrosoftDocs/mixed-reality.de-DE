---
title: Lernen die Freigabe-Modul für HoloLens 2 MR
description: Führen Sie diesen Kurs erfahren, wie Sie mehrere Benutzer freigegebene Umgebungen innerhalb einer HoloLens-2-Anwendung zu implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 8940de029ef5c67c38f427a238f88fcab527d79d
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327764"
---
# <a name="setting-up-photon"></a>Einrichten von Photon

In dieser Lektion lernen wir, wie Sie für die Erstellung von einer gemeinsamen Erfahrung durch das Importieren von Photon Unity Networking (WORTSPIEL) in Ihrem Unity-Projekt vorzubereiten. Photon ist eine von mehreren Netzwerken Optionen Mixed Reality-Entwicklern zur Verfügung, freigegebene Anwendungen zu schaffen. Es wird erfahren Sie, wie ein Photon-Konto erstellen, importieren Photon und erstellen einen optionalen lokalen Server

Ziele:

* Erfahren Sie, wie Sie Photon-Konto erstellen

* Erfahren Sie, wie nach und importieren Sie Photon Unity Networking

* Einrichten eines lokalen Photon-Servers

  

### <a name="setting-up-photon"></a>Einrichten von Photon

1. Richten Sie eine [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) Konto. Navigieren Sie durch Klicken auf der Registrierungsseite für Photon [diesen Link](https://dashboard.photonengine.com/en-US/Account/SignUp). Befolgen Sie die Anweisungen auf der Registrierungsseite aus, um das Konto zu erstellen. 
   

![Module3Chapter1step1im](images/module3chapter1step1im.PNG)

2. Sobald Sie angemeldet sind, klicken Sie auf der SDKs. Sobald Sie auf dieser Seite sind, klicken Sie auf "Server", und stellen Sie sicher Name schon sagt, "selbst gehostet." Scrollen Sie nach unten, und klicken Sie auf "Server", wie in der zweiten Abbildung unten dargestellt.

   

   ![Module3Chapter1step2aim](images/module3chapter1step2aim.PNG)

   ![Module3Chapter1step2bim](images/module3chapter1step2bim.PNG)
   
   3. Ein Textfeld mit der Bezeichnung, angezeigt werden. dadurch "read me." Fahren Sie fort, und Lesen Sie sie. Sobald Sie fertig sind, klicken Sie auf den Link neben "DownloadSDK", um sie herunterzuladen.


![Module3Chapter1step3im](images/module3chapter1step3im.PNG)

4. Doppelklicken Sie den Ordner aus, nachdem der Download abgeschlossen ist.  Wenn Ihre Datei-Explorer geöffnet wird, den SDK-Ordner offenzulegen, kopieren Sie den SDK-Ordner.
   
   - Der nächste Schritt wäre in der Windows-Laufwerk "c:" wechseln, und erstellen einen neuen Ordner namens "Server".
   
   ![Module3Chapter1step4aim](images/module3chapter1step4aim.PNG)
   
   - Jetzt öffnen Sie den Ordner, und fügen Sie den SDK-Ordner, die, den Sie zuvor kopiert haben.
   
   ![Module3Chapter1step4bim](images/module3chapter1step4bim.PNG)
   
5. Sobald dies abgeschlossen ist, öffnen Sie den SDK-Ordner, und wechseln Sie zu ", klicken Sie dann"bin_Win64,"Bereitstellen" doppelklicken und klicken Sie dann auf "Photon-Steuerelement".


![Module3Chapter1step5im](images/module3chapter1step5im.PNG)

> Hinweis: Wenn Sie Fragen zur IP-Adresse oder andere ähnlichen Fragen haben, finden die meisten Informationen auf der Symbolleiste Sie (wie in der folgenden Abbildung gezeigt).
>
> ![Module3Chapter1noteim](images/module3chapter1noteim.PNG)

6. Nun, dass der Server eingerichtet und initiiert wird, wechseln Sie zurück zur Website Photon und stellen Sie sicher, dass Sie immer noch angemeldet sind (oder wieder anmelden, wenn Sie nicht sind.) Klicken Sie auf das Symbol "Profil" (geschachtelt in der oberen rechten Ecke von der Abbildung unten), und wählen Sie "Ihrer Anwendungen."
   

![Module3Chapter1step6im](images/module3chapter1step6im.PNG)

7. Erstellen Sie eine Anwendungs-ID, indem Sie auf die Schaltfläche "erstellen eine neue app".

   ![Module3Chapter1step7aim](images/module3chapter1step7aim.PNG)

   - Wählen Sie "Photon WORTSPIEL" aus dem Dropdown-Menü unter "Photon geben." Klicken Sie dann benennen Sie sie, in diesem Beispiel, das wir den Namen "HoloLensPhotonProject." Sobald Sie fertig sind, klicken Sie auf die Schaltfläche "Erstellen".

   ![Module3Chapter1step7bim](images/module3chapter1step7bim.PNG)

8. Sobald das geschehen ist, kehren Sie zu Ihrer Seite "Anwendungen" zurück und sollte in etwa der folgenden Abbildung. Klicken Sie auf die app-ID, und kopieren Sie ihn. Fügen Sie ist etwas, das Sie auf einfache Weise zugreifen können.  
   

![Module3Chapter1step8im](images/module3chapter1step8im.PNG)

9. Erstellen eines neuen Unity-Projekts, und nennen Sie sie "HLSharingProject." Anweisungen dazu, wie Sie ein neues Unity-Projekt erstellen, finden Sie unter [die Basis des Moduls "Unity-Projekt erstellen" im Abschnitt](https://docs.microsoft.com/en-us/windows/mixed-reality/mrlearning-base-ch1#create-new-unity-project). 


10. Nachdem das Projekt geladen wurde, klicken Sie auf auf der Registerkarte "Ressourcen-Store", wie in der folgenden Abbildung dargestellt. Klicken Sie dann in das Suchfeld in der folgenden Abbildung hervorgehoben wird, geben Sie in "WORTSPIEL", und wählen Sie das "Photon WORTSPIEL-2-FREE"-Objekt in den Suchergebnissen. 

    ![Module3Chapter1step10im](images/module3chapter1step10im.PNG)
    
    11. Herunterladen Sie und importieren Sie dieses Medienobjekts durch Drücken die Schaltflächen "Herunterladen" und "Importieren".
    
    ![Module3Chapter1step11im](images/module3chapter1step11im.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben erfolgreich Photon-Konto erstellt, einen lokalen Photon-Server einrichten und WORTSPIEL in Unity importiert. Der nächste Schritt ist, richten Sie das Projekt, und lassen Sie Verbindungen mit anderen Benutzern, damit mehrere Benutzer Ihre Arbeit sehen können. 

[Nächste Lektion: Sharing(Photon) Lektion 2](mrlearning-sharing(photon)-ch2.md)

