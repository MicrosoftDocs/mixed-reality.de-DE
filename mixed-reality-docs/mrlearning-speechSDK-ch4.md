---
title: Spracherkennung und-Aufzeichnung für das Lern-SDK-Modul von Mr
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: b434b9c79a702067a9c3db6fb25b0f75cdc6030d
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485777"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a>4. Einrichten von Absicht und natürlicher Sprache

In dieser Lektion erfahren Sie mehr über das Intent-Feature des Azure Speech Service. Mit der Intent-Funktion können wir unsere Anwendung mit Ki-gestützten Sprachbefehlen ausstatten, bei denen Benutzer nicht spezifische Sprachbefehle sagen können und dennoch vom System verstanden werden können. In dieser Lektion richten wir unser Azure-Luis-Portal ein, richten unsere Absichten/Entitäten/Äußerungen ein, veröffentlichen unsere Intent-Ressource, verbinden unsere Unity-App mit unserer Intent-Ressource und machen unseren ersten beabsichtigten API-Rückruf.

## <a name="objectives"></a>Ziele

- Erfahren Sie, wie Sie in unserer Anwendung das Verständnis von Absicht und natürlicher Sprache einrichten
- Erfahren Sie, wie Sie das Luis-Portal von Azure einrichten.
- Erfahren Sie, wie Sie Intent, Entitäten und Äußerungen in Azure einrichten.

## <a name="instructions"></a>Anweisungen
1. Gestatten Sie dem Computer das Aktivieren von Diktat. wechseln Sie hierzu zu den Windows-Einstellungen, wählen Sie "Datenschutz", "Sprache" und schließlich "& typisieren" aus, und schalten Sie die Sprachdienste ein, und geben Sie Vorschläge ein.

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)


2. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an. Wenn Sie angemeldet sind, klicken Sie auf Ressource erstellen, suchen Sie nach "Language Understanding", und drücken Sie die EINGABETASTE.

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. Wählen Sie die Schaltfläche erstellen aus, um eine Instanz dieses Dienstanbieter zu erstellen. Benennen Sie Ihr Projekt mit dem Namen "Speech_SDK_Learning_Module", und wählen Sie "Pay as you go".

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. Wählen Sie Ihre Region aus.  Wählen Sie für dieses Tutorial "(USA) USA, Westen" aus. Wählen Sie dann "F0" für den Tarif aus. Klicken Sie jetzt auf "erstellen" (in der unteren linken Ecke), um die Ressource zu erstellen.

>  Hinweis: Wenn Sie auf "erstellen" geklickt haben, müssen Sie warten, bis der Dienst erstellt wird. dieser Vorgang kann einige Minuten in Anspruch nehmen.

5. Sobald die Ressource erstellt wurde, wird im Portal eine Benachrichtigung angezeigt. Klicken Sie auf diese Benachrichtigung, und wählen Sie "zu Ressource wechseln" aus.

6. Navigieren Sie auf der Seite "Schnellstart" Ihres "Luis API"-Dienstanbieter zum ersten Schritt, rufen Sie Ihre "Schlüssel" auf, und klicken Sie auf "Schlüssel" (Sie können dies auch durch Klicken auf den blauen Hyperlink "Keys" erreichen, der in der Abbildung unten dargestellt ist). Dadurch wird Ihr Dienst, "Keys", angezeigt. Speichern Sie eine Kopie eines der Schlüssel, damit Sie Sie später in der App verwenden können.

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. Klicken Sie auf der Seite "Schnellstart" im Abschnitt 2B auf "Language Understanding Portal" (in der Abbildung oben gezeigt), um auf die Webseite umgeleitet zu werden, mit der Sie den neuen Dienst in der Luis-Anwendung erstellen.

> Hinweis: Wenn Sie das "Language Understanding-Portal" erreicht haben, müssen Sie sich ggf. nicht mehr mit denselben Anmelde Informationen wie Ihre Azure-Portal anmelden. Wenn Sie zum ersten Mal Luis verwenden, müssen Sie zum unteren Rand der Willkommensseite Scrollen, um die Schaltfläche "erstellen Sie Luis" zu suchen und darauf zu klicken.

8. Klicken Sie nach der Anmeldung auf "meine apps" (wenn Sie sich derzeit nicht in diesem Abschnitt befinden). Klicken Sie dann auf neue APP erstellen. Nennen Sie die neue App "Speech SDK Learning Module". Fügen Sie auch "Speech SDK Learning Module" zum Beschreibungsfeld hinzu. Klicken Sie dann auf "Done".

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> Nebenbei Wenn Ihre APP eine andere Sprache als Englisch verstehen soll, sollten Sie die "Kultur" in die entsprechende Sprache ändern.

9. Klicken Sie oben rechts auf "Build".

10. Wählen Sie unter APP-Assets auf der linken Seite die Option "Intents" aus, klicken Sie auf "Create New Intent", und nennen Sie Sie "pressbutton". 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> Hinweis: Es ist wichtig, die Namen der Intents und Entitäten zu verwenden, die in diesem Tutorial verwendet werden, da die lunarcom-App anhand ihres Namens auf Sie verweist. 
>
> Hinweis: Sie sollten jetzt über zwei Intents verfügen: "Press Button" und "None".

11. Wählen Sie unter APP-Ressourcen auf der linken Seite die Option "Entitäten" aus, klicken Sie auf "neue Entität erstellen", und geben Sie Ihr den Namen "action".

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. Klicken Sie erneut auf "neue Entität erstellen", und geben Sie Ihr den Namen "target" und den Entitätstyp ebenfalls als "einfach" an.

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. Wählen Sie unter APP-Assets auf der linken Seite die Option "Intents" aus, und klicken Sie dann auf die Absicht, die Sie in Schritt 10 erstellt haben.

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. Klicken Sie auf das Dropdown Menü "Optionen anzeigen" auf der rechten Seite, und wählen Sie "Entitäts Werte anzeigen" aus. 

![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)Klicken Sie auf das Beispiel "Beispiel eingeben...". Textfeld. Geben Sie dann die folgenden Äußerungen ein: 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. Klicken Sie auf das Dropdown Menü "Optionen anzeigen" auf der rechten Seite, und wählen Sie "Entitäts Namen anzeigen" aus.

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. Stellen Sie sicher, dass jede der 10 Äußerungen die folgenden Entitäts Bezeichnungen an den folgenden Stellen von 1 hat.) Klicken Sie auf Wörter, die falsch gekennzeichnet sind, und wählen Sie im Popup Fenster die Option "Bezeichnung entfernen" und 2 aus.) Klicken Sie auf Wörter, die mit einer Bezeichnung versehen werden sollen, und wählen Sie im Popup Fenster die entsprechende Bezeichnung aus.

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. Klicken Sie in der oberen rechten Ecke auf "trainieren", um das Modell zu veröffentlichen. Nachdem die Verarbeitung abgeschlossen ist, klicken Sie in der oberen rechten Ecke auf "Test".

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. Geben Sie in das Textfeld "Start Schaltfläche auswählen" ein.

> Hinweis: Wir haben in unseren Äußerungen nicht "Select" als Aktion hinzugefügt, aber wenn Sie auf "überprüfen" klicken, hat das Modell "Select" als Aktions Entität erkannt.
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. Klicken Sie jetzt in der oberen rechten Ecke auf "veröffentlichen". Stellen Sie sicher, dass in der Dropdown Liste "Produktion" angezeigt wird, und klicken Sie auch im Popup auf "veröffentlichen". 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. Nach der Veröffentlichung sollte am oberen Rand der Seite eine grüne Leiste angezeigt werden.  Klicken Sie auf die grüne Leiste, um zur Seite "verwalten" zu gelangen. 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. Klicken Sie auf der linken Seite unter "Anwendungseinstellungen" auf "Schlüssel und Endpunkte". Legen Sie dann die Dropdown-Einstellung "veröffentlichen auf" als "Produktion" fest. Legen Sie die Zeitzone entsprechend fest, und aktivieren Sie das Kontrollkästchen, um alle vorhergesagten Intent-Ergebnisse einzuschließen. Klicken Sie abschließend auf "Ressource zuweisen".

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. Wählen Sie in der ersten Dropdown Liste Mandant aus, und wählen Sie in der Dropdown Liste Abonnement Name den Namen "Pay-as-you-go" aus. Wählen Sie unter Luis Resource Name die zuvor erstellte Ressource in den Schritten 1-5 aus. Klicken Sie dann auf "Ressource zuweisen". 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> Hinweis: Stellen Sie sicher, dass Sie die Endpunkt-URL, die der soeben zugewiesenen Ressource zugeordnet ist, kopieren und speichern, damit Sie für den nächsten Abschnitt leicht zugänglich ist.
>
> Hinweis: Geben Sie für den Mandanten Namen ihre Corporation oder Ihr Profil ein, das Sie für diese Anwendung erstellt haben.

23. Öffnen Sie nun die neue app in Unity, und wählen Sie das Lunarcom_Base-Objekt in der Hierarchie aus. Klicken Sie im Inspektor-Panel auf "Komponente hinzufügen", suchen Sie nach "lunarcomintenterkenzer", und wählen Sie ihn aus.

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. Geben Sie im Feld für den Luis-Endpunkt der "lunarcomintenterkenzer" im Inspektor-Panel die Endpunkt-URL ein, die Sie in Schritt 22 gespeichert haben. 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  Hinweis: Stellen Sie sicher, dass in der Komponente "lunarcomofflinerecognizer" im Inspektor-Panel "deaktivieren" für "simulateofflinemode" ausgewählt ist. andernfalls funktioniert das Testen des Programms nicht. 

25. Klicken Sie im Unity-Editor auf die Wiedergabe Schaltfläche, und klicken Sie auf die Schaltfläche "" Sagen Sie den Ausdruck "starten Sie die Schaltfläche" starten "aus.

>  Hinweis: Die APP hat die gewünschte Funktion erkannt und die Schaltfläche "Rocket" aktiviert.
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In dieser Lektion haben wir gelernt, wie Sie Ki-gestützte Sprachbefehle hinzufügen können. Jetzt kann Ihr Programm die Absicht der Benutzer erkennen, auch wenn Sie keine präzisen Sprachbefehle aussprechen.

