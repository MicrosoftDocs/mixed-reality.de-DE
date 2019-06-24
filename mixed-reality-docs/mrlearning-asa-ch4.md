---
title: MR Learning ASA-Modul Azure räumliche Anker für HoloLens 2
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: b29f27284c352d27fb1d4d4de701a1ebc2a7cd1c
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327841"
---
# <a name="photon-correct-me-if-im-wrong"></a>Photon (korrigieren mich, wenn ich falsch bin)

In dieser Lektion 

Ziele:

* Erfahren Sie, wie Sie in den ___

* Erfahren Sie, wie Sie in den ___

  

## <a name="instructions"></a>Anweisungen

### <a name="setting-up-photon"></a>Einrichten von Photon

1. Richten Sie eine [Photon](https://dashboard.photonengine.com/en-US/Account/SignUp) Konto. Auf diese Weise wird der imputing Ihre e-Mail-Adresse ein, und durchlaufen einige Überprüfungsschritte bestehen.
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. Sobald Sie angemeldet sind, klicken Sie auf der SDKs. Sobald Sie auf dieser Seite sind, klicken Sie auf "Server", und stellen Sie sicher Name schon sagt, "selbst gehostet." Scrollen Sie nach unten, und klicken Sie auf "Server", wie in der zweiten Abbildung unten dargestellt.

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. Ein Textfeld mit der Bezeichnung, angezeigt werden. dadurch "read me." Fahren Sie fort, und Lesen Sie sie. Sobald Sie fertig sind, klicken Sie auf den Link neben "DownloadSDK", um sie herunterzuladen.


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. Doppelklicken Sie den Ordner aus, nachdem der Download abgeschlossen ist.  Wenn Ihre Datei-Explorer geöffnet wird, den SDK-Ordner offenzulegen, kopieren Sie den SDK-Ordner.
   
   - Der nächste Schritt wäre in der Windows-Laufwerk "c:" wechseln, und erstellen einen neuen Ordner namens "Server".
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - Jetzt öffnen Sie den Ordner, und fügen Sie den SDK-Ordner, die, den Sie zuvor kopiert haben.
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. Sobald dies abgeschlossen ist, öffnen Sie den SDK-Ordner, und wechseln Sie zu ", klicken Sie dann"bin_Win64,"Bereitstellen" doppelklicken und klicken Sie dann auf "Photon-Steuerelement".


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> Hinweis: Wenn Sie Fragen zur IP-Adresse oder andere ähnlichen Fragen haben, finden die meisten Informationen auf der Symbolleiste Sie (wie in der folgenden Abbildung gezeigt).
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. Jetzt an, dass der Server eingerichtet und initiiert wird, wechseln Sie zurück zur Website Photon und klicken Sie auf das Symbol "Profil" (geschachtelt in der Abbildung unten) und wählen Sie "Ihrer Anwendungen."
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. Erstellen Sie eine Anwendungs-ID, indem Sie auf die Schaltfläche "erstellen eine neue app".

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - Wählen Sie "Photon ausführen" aus dem Dropdown-Menü unter "Photon geben." Klicken Sie dann benennen Sie es, (etwas, das Sie daran denken, würde). In diesem Beispiel mit dem Namen wir es "HoloLensPhotonProject." Sobald Sie fertig sind, klicken Sie auf "erstellen".

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. Sobald das geschehen ist, kehren Sie zu Ihrer Seite "Anwendungen" zurück und sollte in etwa der folgenden Abbildung. Klicken Sie auf die app-ID, und kopieren Sie ihn. Fügen Sie ist etwas, das Sie auf einfache Weise zugreifen können.  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. Erstellen Sie ein neues Unity-Projekt. Öffnen Sie Unity-Hub, und klicken Sie auf "Neu". Nennen Sie es mit "HLSharingProject." Klicken Sie dann auf erstellen zu können. 

   > Hinweis: Dies kann zu laden, bis zu 2 Minuten dauern, basierend auf der Geschwindigkeit des Computers.

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> Hinweis: Wählen Sie einen Speicherort für Ihr Projekt auf Ihrem Computer zu speichern, indem Sie die Option "Location" ändern. Speichern Sie es an einem Ort, den Sie werden merken und einfachen Zugriff auf.

10. Nachdem das Projekt geladen wurde, klicken Sie auf der "Assets"Speicher. Klicken Sie dann in das Suchfeld in der folgenden Abbildung gezeigt, geben Sie in "WORTSPIEL", und wählen Sie das Medienobjekt "Photon WORTSPIEL-2-frei". 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. Herunterladen und importieren.
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a>**Einrichten des Unity-Projekts** 

11. Laden Sie ein neues Medienobjekt erforderlich, um Photon in Unity einrichten, indem Sie auf [hier.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)

12. Klicken Sie in Unity auf das Menü "Assets" "Importieren Assets" Wählen Sie aus, und klicken Sie auf "benutzerdefinierte Ressourcen."

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. Wählen Sie das Unity-Paket, die, das Sie gerade heruntergeladen, über den Link in Schritt 1 bereitgestellt haben. Wenn die Schaltfläche "Importieren" in Unity angezeigt wird, klicken Sie darauf.

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> Hinweis: ganz egal, wo Sie das Paket heruntergeladen werden, wo Sie ihn finden. In der Abbildung oben ist nicht darstellen, in dem Sie das Paket finden.

14. Erstellen Sie eine neue Szene (Dies kann sein, mithilfe des Steuerelements / Befehl + N oder durch Klicken auf "file", und wählen "neue Szene."). Speichern Sie die Szene als "HLSharedProjectMain."

> Hinweis: erhalten Sie möglicherweise ein Popupfenster, das in der folgenden Abbildung ähneln. Jetzt klicken Sie einfach auf "Nein" festgelegt wird.
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. Klicken Sie unter "Mixed Reality-Toolkit" auf "Szene hinzufügen und konfigurieren."

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. Sobald dies abgeschlossen ist, wird eine neue Konfigurationsdatei angezeigt, bietet Ihnen die Möglichkeit, die das Profil anzupassen. Klicken Sie auf "kopieren und anpassen."

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. Scrollen Sie nach unten, und deaktivieren Sie die Option "Diagnostics-System aktivieren". Dies wird zum Einrichten dieses Projekts erleichtern.

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. Öffnen Sie die Buildeinstellungen (STRG + UMSCHALTTASTE + B). Beachten Sie, dass das Programm derzeit unter der Plattform "PC, Mac und Linux-eigenständig" festgelegt ist. Legen Sie für dieses Projekt die Plattform "universelle Windows-Plattform" sein. Wählen Sie sie aus, und klicken Sie auf "switch Platform".

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. Sobald der Vorgang abgeschlossen ist, klicken Sie auf das Kontrollkästchen "open Szenen hinzufügen". Kehren Sie jetzt den Inspektor-Zugriffsbereich und sicherstellen, dass das Kontrollkästchen rechts neben "virtual Reality unterstützt" (wie in der folgenden Abbildung gezeigt) aktiviert ist. 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> Hinweis: Stellen Sie außerdem sicher, dass Sie das Kontrollkästchen neben "Szenen/HLSharedProjectMain" ebenfalls aktiviert ist.

20. Klicken Sie unter "veröffentlichungseinstellungen" im Bereich Inspektor scrollen "Funktionen", und stellen Sie sicher, es werden nur die folgenden Kontrollkästchen markiert:

- Internetclient
- IIS-Client-server
- VPN-Client-server
- camera/webcam
- Mikrofon

21. Schritt 12, wie wäre der nächste Schritt, importieren ein anderes benutzerdefiniertes Paket namens "Lektion 2: komplettes" das [Hier] heruntergeladen werden kann [lesson2.unitypackage Link hier einfügen] Importieren Sie das Paket an.

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. Im Projektfenster, wechseln Sie nun zum Ordner "Prefabs", da in den nächsten Schritten Sie einige prefabs (Vorlagen) in der Szene implementieren werden. Klicken Sie im Ordner "Prefabs" klicken Sie, und ziehen Sie das Prefab, "DebugWindow" in der Hierarchie. Sobald Sie fertig sind, speichern Sie das Projekt (klicken Sie auf Datei, klicken Sie dann speichern, oder STRG + S)

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> Hinweis: Sie werden feststellen, dass ein Popupfenster angezeigt, wenn Sie auf das Prefab klicken TMP Essentials gefragt. Klicken Sie auf "Import TMP Essentials", da sie benötigt werden.
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a>**Verbinden von mehreren Benutzern**

23. Wie in Schritt 22, im Ordner "Prefabs" im Projektfenster, besteht der nächste Schritt, um Drag & drop die Prefab "NetworkLobby" in der Hierarchie. 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. Wenn Sie den übergeordneten-Prefab "NetworkLobby," öffnen, sehen Sie ein untergeordnetes Element prefab, "NetworkRoom." Klicken Sie mit der sie ausgewählt haben wechseln Sie in den Bereich der Eigenschaftenanalyse, und klicken Sie auf "Komponente hinzufügen" aus. Suchen Sie nach "PhotonView", und fügen Sie die Komponente.

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. Erstellen Sie ein neues, leeres game-Objekt, in der Hierarchie (Rechtsklick in der Hierarchie, und wählen Sie "leere"). Stellen Sie sicher, die Positionierung festgelegt ist, auf X = 0, y = 0, Z = 0, und nennen Sie das Objekt "PhotonUser."

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a>Herzlichen Glückwunsch!



