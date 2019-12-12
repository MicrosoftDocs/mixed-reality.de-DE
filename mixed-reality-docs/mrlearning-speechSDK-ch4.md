---
title: Tutorials zu Azure Speech Services-4. Einrichten von Absicht und natürlicher Sprache
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: e712fc2fd66b1add5b16b7dd8e6c37551aefe43a
ms.sourcegitcommit: 9005b3fdfa87ac8fdc18a594a681e25c00ac5ce1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2019
ms.locfileid: "75003209"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a>4. Einrichten der Absicht und der Kenntnisse in natürlicher Sprache

In dieser Lektion erfahren Sie mehr über das Intent-Feature des Azure Speech Service. Das Intent-Feature ermöglicht es Ihnen, unsere Anwendung mit Ki-gestützten Sprachbefehlen auszustatten, bei denen Benutzer nicht spezifische Sprachbefehle sagen können und dennoch vom System verstanden werden können. In dieser Lektion richten wir unser Azure-Luis-Portal ein, richten unsere Absichten/Entitäten/Äußerungen ein, veröffentlichen unsere Intent-Ressource, verbinden unsere Unity-App mit unserer Intent-Ressource und machen unseren ersten beabsichtigten API-Rückruf.

## <a name="objectives"></a>Ziele

- Erfahren Sie, wie Sie in unserer Anwendung das Verständnis von Absicht und natürlicher Sprache einrichten
- Erfahren Sie, wie Sie das Luis-Portal von Azure einrichten.
- Erfahren Sie, wie Sie Intent, Entitäten und Äußerungen in Azure einrichten.

## <a name="instructions"></a>Anweisungen

1. Ermöglicht dem Computer das Aktivieren von Diktat. Wechseln Sie zu diesem Zweck zu Windows-Einstellungen, wählen Sie "Datenschutz", dann "Sprache" und anschließend "Inking & typisieren" aus, und aktivieren Sie Sprachdienste, und geben Sie Vorschläge ein.

    ![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

    ![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

    ![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

2. Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an. Wenn Sie angemeldet sind, klicken Sie auf Ressource erstellen, suchen Sie nach "Language Understanding", und drücken Sie die EINGABETASTE.

    ![mrlearning-Speech-CH4-1-step2. png](images/mrlearning-speech-ch4-1-step2.png)

3. Klicken Sie auf die Schaltfläche **Erstellen** , um eine Instanz dieses Dienstanbieter zu erstellen.

    ![mrlearning-Speech-CH4-1-step3a. png](images/mrlearning-speech-ch4-1-step3a.png)

    Geben Sie der Ressource einen **Namen**, z. b. " *Speech-SDK-Learning-Module*". Wählen Sie für **Abonnement**die Option *Pay as you go* oder *Free Trail* aus, wenn Sie über ein Testkonto verfügen. Erstellen Sie als nächstes eine neue **Ressourcengruppe** , indem Sie auf den Link **neu erstellen** klicken, geben Sie einen Namen ein, z. b. *hololens-2-Tutorials-Resource-Group*, und klicken Sie auf die Schaltfläche **OK** .

    ![mrlearning-Speech-CH4-1-step3b. png](images/mrlearning-speech-ch4-1-step3b.png)

4. Wählen Sie den **Speicherort der Erstellung** und den **Speicherort**der Verwenden Sie für dieses Lernprogramm *(USA) USA, Westen*, und wählen Sie dann *F0 (5 Anrufe pro Sekunde, 10K Anrufe pro Monat)* für **den Erstellungs** Tarif und den **Lauf**Zeit Tarif aus. Klicken Sie abschließend auf die Schaltfläche **Erstellen** , um die Ressource zu erstellen, sowie die neue Ressourcengruppe.

    ![mrlearning-Speech-CH4-1-step4. png](images/mrlearning-speech-ch4-1-step4.png)

    >[!NOTE]
    >Nachdem Sie auf die Schaltfläche "erstellen" geklickt haben, müssen Sie warten, bis der Dienst erstellt wird. dieser Vorgang kann einige Minuten in Anspruch nehmen.

5. Nachdem der Vorgang zur Ressourcen Erstellung fertiggestellt wurde, wird die Meldung **Ihre Bereitstellung ist beendet**angezeigt.

    ![mrlearning-Speech-CH4-1-step5. png](images/mrlearning-speech-ch4-1-step5.png)

6. Melden Sie sich mit demselben Benutzerkonto beim [Language Understanding Intelligent Service (Luis)](https://www.luis.ai/) -Portal an, wählen Sie Ihr Land aus, und stimmen Sie den Nutzungsbedingungen zu.

    >[!NOTE]
    >Wenn Sie das Language Understanding-Portal erreicht haben, müssen Sie sich ggf. mit denselben Anmelde Informationen wie Ihre Azure-Portal anmelden, falls Sie dies noch nicht getan haben. Wenn Sie zum ersten Mal Luis verwenden, müssen Sie einen Bildlauf zum unteren Rand der Willkommensseite durchführen, um auf die Schaltfläche "Erstellen einer Luis-app" zu klicken.

7. Klicken Sie nach der Anmeldung auf "meine apps" (wenn Sie sich derzeit nicht in diesem Abschnitt befinden). Klicken Sie dann auf neue APP erstellen. Nennen Sie die neue App "Speech SDK Learning Module". Fügen Sie auch "Speech SDK Learning Module" zum Beschreibungsfeld hinzu. Klicken Sie dann auf "Done".

    ![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

    ![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

    >[!NOTE]
    >Wenn Ihre APP eine andere Sprache als Englisch verstehen soll, sollten Sie die "Kultur" in die entsprechende Sprache ändern.

8. Klicken Sie oben rechts auf "Build".

9. Wählen Sie unter APP-Assets auf der linken Seite die Option "Intents" aus, klicken Sie auf "Create New Intent", und nennen Sie Sie "pressbutton".

    ![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

    >[!NOTE]
    >Es ist wichtig, die Namen der Intents und Entitäten zu verwenden, die in diesem Tutorial verwendet werden, da die lunarcom-App anhand ihres Namens auf Sie verweist.

    >[!NOTE]
    >Sie sollten jetzt über zwei Intents verfügen: "Press Button" und "None".

10. Wählen Sie unter APP-Assets auf der linken Seite die Option Entitäten aus, klicken Sie auf "neue Entität erstellen", benennen Sie Sie "action", und behalten Sie den Entitätstyp "Simple" bei.

    ![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

11. Klicken Sie erneut auf "neue Entität erstellen", und nennen Sie Sie "target". Behalten Sie auch den Entitätstyp "Simple" bei.

    ![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

12. Wählen Sie unter APP-Assets auf der linken Seite die Option "Intents" aus, und klicken Sie dann auf die Absicht, die Sie in Schritt 10 erstellt haben.

    ![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

13. Klicken Sie auf das Dropdown Menü "Optionen anzeigen" auf der rechten Seite, und wählen Sie "Entitäts Werte anzeigen" aus.

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)

    Klicken Sie auf das Beispiel "Beispiel eingeben...". ein. Geben Sie dann die folgenden Äußerungen ein:

    ![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

14. Klicken Sie auf das Dropdown Menü "Optionen anzeigen" auf der rechten Seite, und wählen Sie "Entitäts Namen anzeigen" aus.

    ![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

15. Stellen Sie sicher, dass jede der 10 Äußerungen die folgenden Entitäts Bezeichnungen an den folgenden Stellen von 1 hat.) Klicken Sie auf Wörter, die falsch gekennzeichnet sind, und wählen Sie im Popup Fenster die Option "Bezeichnung entfernen" und 2 aus.) Klicken Sie auf Wörter, die mit einer Bezeichnung versehen werden sollen, und wählen Sie im Popup Fenster die entsprechende Bezeichnung aus.

    ![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

16. Klicken Sie in der oberen rechten Ecke auf "trainieren", um das Modell zu veröffentlichen. Nachdem die Verarbeitung abgeschlossen ist, klicken Sie in der oberen rechten Ecke auf "Test".

    ![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

17. Geben Sie in das Textfeld "Start Schaltfläche auswählen" ein.

    >[!NOTE]
    >Wir haben in unseren Äußerungen nicht "Select" als Aktion hinzugefügt, aber wenn Sie auf "überprüfen" klicken, hat das Modell "Select" als Aktions Entität erkannt.
    >
    > ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

18. Klicken Sie oben rechts auf "veröffentlichen". Stellen Sie sicher, dass in der Dropdown Liste "Produktion" angezeigt wird, und klicken Sie im Popup Fenster auf "veröffentlichen".

    ![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

19. Nach der Veröffentlichung sollte am oberen Rand der Seite eine grüne Leiste angezeigt werden. Klicken Sie auf die grüne Leiste, um die Seite "verwalten" anzuzeigen.

    ![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

20. Klicken Sie auf der linken Seite unter "Anwendungseinstellungen" auf "Schlüssel und Endpunkte". Legen Sie dann die Dropdown-Einstellung "veröffentlichen auf" als "Produktion" fest. Legen Sie die Zeitzone entsprechend fest, und aktivieren Sie das Kontrollkästchen, um alle vorhergesagten Intent-Ergebnisse einzuschließen. Klicken Sie abschließend auf "Ressource zuweisen".

    ![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

21. Wählen Sie in der ersten Dropdown Liste Mandant aus, und wählen Sie in der Dropdown Liste Abonnement Name den Namen "Pay-as-you-go" aus. Wählen Sie unter Luis Resource Name die zuvor erstellte Ressource in den Schritten 1-5 aus. Klicken Sie dann auf "Ressource zuweisen".

    ![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

    >[!NOTE]
    >Stellen Sie sicher, dass Sie die der soeben zugewiesenen Ressource zugeordnete Endpunkt-URL kopieren und speichern, damit der nächste Abschnitt leicht zugänglich ist.

    >[!NOTE]
    >Geben Sie für den Mandanten Namen ihre Corporation oder Ihr Profil ein, das Sie für diese Anwendung erstellt haben.

22. Öffnen Sie nun die neue app in Unity, und wählen Sie das Lunarcom_Base-Objekt in der Hierarchie aus. Klicken Sie im Inspektor-Panel auf "Komponente hinzufügen", suchen Sie nach "lunarcomintenterkenzer", und wählen Sie ihn aus.

    ![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

23. Geben Sie im Feld für den Luis-Endpunkt der "lunarcomintenterkenzer" im Inspektor-Panel die Endpunkt-URL ein, die Sie in Schritt 22 gespeichert haben.

    ![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

    >[!NOTE]
    >Stellen Sie sicher, dass in der Komponente "lunarcomofflinerecognizer" im Inspektor-Panel "deaktivieren" für "simulateofflinemode" ausgewählt ist. andernfalls funktioniert das Testen des Programms nicht.

24. Klicken Sie im Unity-Editor auf die Wiedergabe Schaltfläche, und klicken Sie auf die Schaltfläche "" Sagen Sie den Ausdruck "starten Sie die Schaltfläche" starten "aus.

    >[!NOTE]
    >Die APP hat die gewünschte Funktion erkannt und die Schaltfläche "Rocket" aktiviert.
    >
    >![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In dieser Lektion haben Sie gelernt, wie Sie Ki-gestützte Sprachbefehle hinzufügen. Jetzt kann Ihr Programm die Absicht der Benutzer erkennen, auch wenn Sie keine präzisen Sprachbefehle mehr haben!
