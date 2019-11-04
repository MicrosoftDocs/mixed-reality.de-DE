---
title: Lernprogramme für Mehrbenutzerfunktionen-2. Vorbereiten von Unity für die Entwicklung
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Umgebungen mit mehreren Benutzern in einer hololens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 5d8194e9a51bdb0ce32f345b4adfbfaf408c5396
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438389"
---
# <a name="2-getting-unity-ready-for-development"></a>2. Vorbereiten von Unity für die Entwicklung 


In diesem Tutorial erfahren Sie, wie Sie Unity für die Anwendungsentwicklung vorbereiten und konfigurieren, einschließlich Importieren des Mixed Reality Toolkit, Konfigurieren von Buildeinstellungen und Vorbereiten der Szene.

## <a name="objectives"></a>Ziele

- Konfigurieren von Unity für die Anwendungsentwicklung

- Importieren des Mixed Reality-Toolkits

- Vorbereiten der Projekt Szene

## <a name="instructions"></a>Anweisungen

1. Klicken Sie hier, um das Unity-Paket für Mixed Reality Toolkit herunterzuladen und zu speichern [.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)

2. Klicken Sie in Unity auf das Menü Assets, wählen Sie Paket importieren aus, und klicken Sie dann auf benutzerdefiniertes Paket.

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. Wählen Sie das Unity-Paket aus, das Sie soeben aus dem in Schritt 1 angegebenen Link heruntergeladen haben. Nachdem das Popup Fenster Importieren in Unity angezeigt wird, klicken Sie auf die Schaltfläche Importieren, um mit dem Importieren von mrtk zu beginnen. Dieser Vorgang kann einige Minuten in Anspruch nehmen.

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> Hinweis: das heruntergeladene Paket befindet sich in Ihrem lokalen Ordner, in dem Sie die Datei gespeichert haben. In der Abbildung oben wird nicht dargestellt, wo Sie das Paket finden.

4. Erstellen Sie eine neue Szene. Klicken Sie hierzu auf Datei, und wählen Sie neue Szene aus. Speichern Sie Sie als hlsharedprojectmain.

> Hinweis: Sie erhalten möglicherweise ein Popup, das ähnlich wie in der folgenden Abbildung aussieht. Klicken Sie vorerst auf Nein.
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. Klicken Sie unter Mixed Reality Toolkit auf zur Szene hinzufügen und konfigurieren.

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. Sobald der Vorgang beendet ist, wird eine neue Konfigurationsdatei angezeigt, die Ihnen die Möglichkeit gibt, das Profil anzupassen. Klicken Sie auf Kopieren und anpassen.

![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. Scrollen Sie nach unten, und deaktivieren Sie Diagnosesystem aktivieren, wenn Sie das Diagnosefenster ausblenden möchten. Es wird empfohlen, das Diagnosefenster während der Anwendungsentwicklung zu aktivieren, um die Leistung zu überwachen und es dann während der Produktions-oder Anwendungs Demos zu deaktivieren. 

![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. Öffnen Sie die Buildeinstellungen, indem Sie STRG + UMSCHALT + B drücken, oder wechseln Sie zu Datei > Buildeinstellungen. Beachten Sie, dass das Programm derzeit unter der eigenständigen PC-, Mac-und Linux-Plattform festgelegt ist. Legen Sie für die Entwicklung von hololens 2 die Plattform auf universelle Windows-Plattform fest. Wählen Sie es aus, und klicken Sie auf Plattform wechseln.

![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. Klicken Sie nach Abschluss des Vorgangs auf das Feld mit dem Namen offene Szenen hinzufügen Wechseln Sie nun zum Inspektor-Panel, und stellen Sie sicher, dass das Kontrollkästchen rechts von Virtual Reality unterstützt wird (wie in der folgenden Abbildung dargestellt). Stellen Sie außerdem sicher, dass das Kontrollkästchen nebenszenen/hlsharedprojectmain ebenfalls aktiviert ist, wie in der folgenden Abbildung dargestellt.

![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. Scrollen Sie im Bereich Inspector im Bereich Veröffentlichungs Einstellungen nach unten zu Funktionen, und stellen Sie sicher, dass die folgenden Kontrollkästchen markiert sind:

![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. Importieren Sie das benutzerdefinierte Paket mit dem Namen "sharingassetcollection", das hier heruntergeladen werden kann [.](https://github.com/microsoft/MixedRealityLearning/releases/tag/development)

![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. Wechseln Sie im Projekt Panel zum Ordner Prefabs. In den folgenden Schritten implementieren Sie einige Prefabs in der Szene. Klicken Sie im Ordner Prefabs auf das Fenster Prefab, Debug, und ziehen Sie es in die Hierarchie. Wenn Sie fertig sind, speichern Sie das Projekt, indem Sie auf Datei und dann auf Speichern klicken oder STRG + S drücken.

![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > Hinweis: Sie werden feststellen, dass ein Popup Fenster angezeigt wird, wenn Sie auf die vorfab klicken, und Sie werden aufgefordert, tmp Essentials anzuzeigen. Klicken Sie auf tmp Essentials nach Bedarf importieren. Wenn dieses Popup Fenster angezeigt wird, müssen Sie möglicherweise die vorfab aus Ihrer Hierarchie löschen und in ihre Hierarchie ziehen, um potenzielle Text bezogene Fehler zu vermeiden.
   >
>![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a>Herzlichen Glückwunsch!

Ihr Unity-Projekt ist nun für das Photon bereit. In den nächsten Tutorials bauen wir auf dieser Szene und unserem Unity-Projekt auf, um eine vollständige gemeinsame Nutzung zu ermöglichen.

[Nächstes Tutorial: 3. Verbinden von mehreren Benutzern](mrlearning-sharing(photon)-ch3.md)

