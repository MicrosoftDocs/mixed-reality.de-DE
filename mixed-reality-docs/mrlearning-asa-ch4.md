---
title: Mr Learning ASA-Modul Azure Spatial Anchor on hololens 2
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 141aa90f2bf5d90527a0fe1e6a812c1ce56bd0eb
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437800"
---
# <a name="photon-correct-me-if-im-wrong"></a>Photon (korrigieren, wenn ich falsch bin)

In dieser Lektion 

Ziele

* Weitere Informationen finden Sie unter _____________________________________________

* Weitere Informationen finden Sie unter _________________________________________________

  

## <a name="instructions"></a>Anweisungen

### <a name="setting-up-photon"></a>Einrichten von PHOTON

1. Richten Sie ein [Photon](https://dashboard.photonengine.com//Account/SignUp) -Konto ein. Dies führt dazu, dass Ihre e-Mail beeinträchtigt wird und einige Überprüfungs Schritte durchgeführt werden.
   

![Module2Chapter4step1im](images/Module2chapter4step1im.png)

2. Nachdem Sie sich angemeldet haben, klicken Sie auf sdert. Wenn Sie sich auf dieser Seite befinden, klicken Sie auf "Server", und stellen Sie sicher, dass Sie "selbstgeh ostet" lautet. Scrollen Sie dann nach unten, und klicken Sie auf "Server", wie in der zweiten Abbildung unten gezeigt.

   

   ![Module2Chapter2step2aim](images/Module2chapter4step2aim.png)

   ![Module2Chapter2step2bim](images/Module2chapter4step2bim.png)
   
   3. Dadurch wird ein Textfeld mit der Bezeichnung "Read Me" angezeigt. Lesen Sie den Vorgang. Wenn Sie fertig sind, klicken Sie auf den Link neben "Download SDK", um ihn herunterzuladen.


![Module2Chapter4step3im](images/Module2chapter4step3im.png)

4. Wenn der Download abgeschlossen ist, doppelklicken Sie auf den Ordner.  Wenn der Datei-Explorer geöffnet wird und der SDK-Ordner angezeigt wird, kopieren Sie den SDK-Ordner.
   
   - Der nächste Schritt besteht darin, auf das Laufwerk "Windows C:" zu wechseln und einen neuen Ordner namens "Server" zu erstellen.
   
   ![Module2Chapter4step4im](images/Module2chapter4step4aim.png)
   
   - Öffnen Sie jetzt den Ordner, und fügen Sie den zuvor kopierten SDK-Ordner ein.
   
   ![Module2Chapter4step4im](images/Module2chapter4step4bim.png)
   
5. Öffnen Sie nach Abschluss des Vorgangs den SDK-Ordner, und navigieren Sie zu "Bereitstellen", dann "bin_Win64". Doppelklicken Sie dann auf "Photon-Steuerelement".


![Module2Chapter4step4im](images/Module2chapter4step5im.png)

> Hinweis: Wenn Sie Fragen zur IP-Adresse oder zu anderen ähnlichen Fragen haben, finden Sie die meisten Ihrer Informationen in der Symbolleiste (wie in der Abbildung unten dargestellt).
>
> ![Module2Chapter4step4im](images/Module2chapter4noteim.png)

6. Nachdem der Server eingerichtet und initiiert wurde, wechseln Sie zurück zur Website von PHOTON, und klicken Sie auf das Profil Symbol (in der Abbildung unten dargestellt), und wählen Sie "Ihre Anwendungen".
   

![Module2Chapter3step5im](images/Module2chapter4step6im.png)

7. Erstellen Sie eine Anwendungs-ID, indem Sie auf die Schaltfläche "neue APP erstellen" klicken.

   ![Module2Chapter3step8im](images/Module2chapter4step7aim.png)

   - Wählen Sie im Dropdown Menü unter "Photon Type" die Option "Photon Run" aus. Nennen Sie es dann (etwas, das Sie merken würden). In diesem Beispiel nennen wir es "hololersphutonproject". Wenn Sie fertig sind, klicken Sie auf "erstellen".

   ![Module2Chapter3step8im](images/Module2chapter4step7bim.png)

8. Sobald dies erfolgt ist, kehren Sie zur Seite "Anwendungen" zurück, und es sollte etwas ähnlich der folgenden Abbildung angezeigt werden. Klicken Sie auf die APP-ID, und kopieren Sie Sie. Einfügen ist ein Ort, auf den Sie problemlos zugreifen können.  
   

![Module2Chapter4step9im](images/Module2chapter4step8im.png)

9. Erstellen Sie ein neues Unity-Projekt. Öffnen Sie den Unity-Hub, und klicken Sie auf "neu". Nennen Sie es "hlsharingproject". Klicken Sie anschließend auf erstellen. 

   > Hinweis: je nach Geschwindigkeit des Computers kann es bis zu 2 Minuten dauern, bis der Ladevorgang abgeschlossen ist.

![Module2Chapter4step9im](images/Module2chapter4step9im.png)

> Hinweis: Wählen Sie einen Ort aus, an dem das Projekt auf Ihrem Computer gespeichert werden soll, indem Sie die Option "Standort" ändern. Speichern Sie Sie an einem Speicherort, den Sie merken werden und für den Sie einfachen Zugriff haben.

10. Nachdem das Projekt geladen wurde, klicken Sie auf den "Assets Store". Geben Sie dann im Suchfeld, das in der folgenden Abbildung gezeigt wird, "pun" ein, und wählen Sie das Asset "Photon pun-2 Free" aus. 

    ![Module2Chapter4step10im](images/Module2chapter4step10im.PNG)
    
    11. Herunterladen und importieren!
    
    ![Module2Chapter4step11im](images/Module2chapter4step11im.png)

### <a name="setting-up-the-unity-project"></a>**Einrichten des Unity-Projekts** 

11. Laden Sie ein neues Asset herunter, das zum Einrichten von Photon in Unity erforderlich ist, indem Sie [hier klicken.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1-Refresh/Microsoft.MixedReality.Toolkit.Unity.Examples-v2.0.0-RC1-Refresh.unitypackage)

12. Klicken Sie in Unity auf das Menü Assets, und wählen Sie "Objekte importieren" aus, und klicken Sie dann auf "benutzerdefinierte Objekte".

![Module2Chapter4step12im](images/Module2chapter4step12im.PNG)

13. Wählen Sie das Unity-Paket aus, das Sie soeben aus dem in Schritt 1 angegebenen Link heruntergeladen haben. Wenn die Schaltfläche Importieren in Unity angezeigt wird, klicken Sie darauf.

![Module2Chapter4step13im](images/Module2chapter4step13im.png)

> Hinweis: Wenn Sie das Paket heruntergeladen haben, finden Sie es dort, wo Sie es finden. In der Abbildung oben wird nicht dargestellt, wo Sie das Paket finden.

14. Erstellen Sie eine neue Szene (Dies kann mithilfe von Control/Command + N oder durch Klicken auf "Datei" und "neue Szene" erfolgen.) Speichern Sie die Szene als "hlsharedprojectmain".

> Hinweis: Sie erhalten möglicherweise ein Popup, das ähnlich wie in der folgenden Abbildung aussieht. Klicken Sie vorerst einfach auf "Nein".
>
> ![Module2Chapter4note2im](images/Module2chapter4note2im.png)

15. Klicken Sie unter "Mixed Reality Toolkit" auf "zu Szene hinzufügen und konfigurieren".

![Module2Chapter4step15im](images/Module2chapter4step15im.png)

16. Sobald der Vorgang beendet ist, wird eine neue Konfigurationsdatei angezeigt, die Ihnen die Möglichkeit gibt, das Profil anzupassen. Klicken Sie auf "Kopieren und anpassen".

![Module2Chapter4step16im](images/Module2chapter4step16im.png)

17. Scrollen Sie nach unten, und deaktivieren Sie die Option "Diagnosesystem aktivieren". Dadurch wird die Einrichtung dieses Projekts vereinfacht.

![Module2Chapter4step17im](images/Module2chapter4step17im.png)

18. Öffnen Sie die Buildeinstellungen (Control + Shift + B). Beachten Sie, dass das Programm derzeit auf der Plattform "PC, Mac und Linux Standalone" festgelegt ist. Legen Sie für dieses Projekt die Plattform auf "universelle Windows-Plattform" fest. Wählen Sie diese Option aus, und klicken Sie auf Plattform wechseln.

![Module2Chapter4step18im](images/Module2chapter4step18im.png)

19. Wenn Sie fertig sind, klicken Sie auf das Feld "offene Szenen hinzufügen". Wechseln Sie nun zum Bereich Inspector, und stellen Sie sicher, dass das Kontrollkästchen rechts neben "unterstützte virtuelle Realität" (wie in der folgenden Abbildung gezeigt) aktiviert ist. 

![Module2Chapter4step19im](images/Module2chapter4step19im.png)

> Hinweis: Stellen Sie außerdem sicher, dass das Kontrollkästchen neben "Szenen/hlsharedprojectmain" ebenfalls aktiviert ist.

20. Scrollen Sie im Inspektor-Panel unter "Veröffentlichungs Einstellungen" nach unten zu "Funktionen", und stellen Sie sicher, dass nur die folgenden Kontrollkästchen markiert sind:

- Internet Client
- Internet Client Server
- privater Netzwerkclient Server
- Kamera/Webcam
- Mikrofon

21. Ebenso wie bei Schritt 12 wäre der nächste Schritt das Importieren eines weiteren benutzerdefinierten Pakets namens "Lesson2", das hier heruntergeladen werden kann. [Lesson2. unitypackage-Link hier einfügen] Importieren Sie das Paket.

![Module2Chapter4step21im](images/Module2chapter4step20im.png)

22. Wechseln Sie nun im Projekt Panel zum Ordner "Prefabs", denn in den nächsten Schritten werden Sie einige Prefabs in der Szene implementieren. Klicken Sie im Ordner "Prefabs" auf die Prefab-"debugWindow"-Komponente, und ziehen Sie Sie in die Hierarchie. Wenn Sie fertig sind, speichern Sie das Projekt (Klicken Sie auf Datei, dann auf Speichern oder auf + S).

![Module2Chapter4step22im](images/Module2chapter4step21im.PNG)

> Hinweis: Sie werden feststellen, dass ein Popup Fenster angezeigt wird, wenn Sie auf die vorfab klicken, und Sie werden aufgefordert, tmp Essentials anzuzeigen. Klicken Sie auf "tmp Essentials importieren", wenn Sie benötigt werden.
>
> ![Module2Chapter4note3im](images/Module2chapter4note3im.PNG)

### <a name="connecting-multiple-users"></a>**Verbinden von mehreren Benutzern**

23. Der nächste Schritt besteht im Ordner "Prefabs" im Projekt Panel darin, die vorfab "networklobby" per Drag & amp; Drop in die Hierarchie zu verschieben. 

![Module2Chapter4step22im](images/Module2chapter4step22im.png)

24. Wenn Sie die übergeordnete Prefab "networklobby" öffnen, sollte eine untergeordnete vorfab angezeigt werden, "Network Room". Wenn diese Option ausgewählt ist, wechseln Sie im Inspektor-Panel, und klicken Sie auf "Komponente hinzufügen". Suchen Sie nach "photonview", und fügen Sie die Komponente hinzu.

![Module2Chapter4step23im](images/Module2chapter4step23im.png)

25. Erstellen Sie ein neues leeres Spielobjekt in der Hierarchie (Klicken Sie mit der rechten Maustaste in die Hierarchie, und wählen Sie "Empty" Stellen Sie sicher, dass die Positionierung auf x = 0, y = 0, z = 0 festgelegt ist, und benennen Sie das Objekt "photonuser".

![Module2Chapter4step24im](images/Module2chapter4step24im.png)

## <a name="congratulations"></a>Herzlichen Glückwunsch!



