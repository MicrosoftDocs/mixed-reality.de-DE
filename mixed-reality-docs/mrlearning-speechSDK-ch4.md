---
title: 'Tutorials zu Azure Speech-Diensten: 4. Einrichten des Verstehens von Absichten und natürlicher Sprache'
description: In diesem Kurs erfahren Sie, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: b2342e7d0d502af2787ca311d18a44f8726acf2d
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79028480"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a>4. Einrichten des Verstehens von Absichten und natürlicher Sprache

In diesem Tutorial untersuchen wir die Absichtserkennung des Azure-Sprachdiensts. Die Absichtserkennung ermöglicht es Ihnen, Ihre Anwendung mit KI-gestützten Sprachbefehlen auszustatten. In diesem Fall können Benutzer unspezifische Sprachbefehle äußern, und ihre Absicht wird trotzdem vom System verstanden.

## <a name="objectives"></a>Ziele

* Das Erlernen der Einrichtung von Absicht, Entitäten und Äußerungen im LUIS-Portal
* Erlernen der Implementierung des Erkennens von Absichten und des Verstehens natürlicher Sprache in unserer Anwendung

## <a name="preparing-the-scene"></a>Vorbereiten des Szenarios

Wählen Sie im Hierarchiefenster das **Lunarcom**-Objekt aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um dem Lunarcom-Objekt die Komponente **Lunarcom Intent Recognizer (Script)** hinzuzufügen:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-1.png)

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher**, ziehen Sie das Prefab **RocketLauncher_Complete** in Ihr Hierarchiefenster, und platzieren Sie es an einem passenden Ort vor der Kamera, beispielsweise:

* **Transformationsposition** X = 0, Y = -0,4, Z = 1
* **Transformationsrotation** X = 0, Y = 90, Z = 0

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-2.png)

Wählen Sie im Hierarchiefenster das **Lunarcom**-Objekt erneut aus, klappen Sie dann das Objekt **RocketLauncher_Complete** > **Button** auf, und weisen Sie jedem untergeordneten Objekt des **Buttons**-Objekts das entsprechende **Lunar Launcher Buttons**-Feld zu:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-3.png)

## <a name="creating-the-azure-language-understanding-resource"></a>Erstellen der Azure Language Understanding-Ressource

In diesem Abschnitt erstellen Sie eine Azure-Vorhersageressource für die LUIS-App (Language Understanding Intelligent Service), die Sie im nächsten Abschnitt erstellen.

Melden Sie sich bei <a href="https://portal.azure.com" target="_blank">Azure</a> an, und klicken Sie auf **Ressource erstellen**. Suchen Sie dann nach **Language Understanding**, und wählen Sie es aus:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-1.png)

Klicken Sie auf die Schaltfläche **Erstellen**, um eine Instanz dieses Diensts zu erstellen:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-2.png)

Klicken Sie auf der Seite „Erstellen“ auf die Option **Vorhersage**, und geben Sie die folgenden Werte ein:

* Wählen Sie unter **Abonnement** **Kostenlose Testversion** aus, wenn Sie über ein Testabonnement verfügen, und wählen Sie andernfalls eins Ihrer anderen Abonnements aus
* Klicken Sie für die **Ressourcengruppe** auf den Link **Neue erstellen**, geben Sie einen passenden Namen ein, beispielsweise *MRKT-Tutorials*, und klicken Sie dann auf **OK**

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-3.png)

> [!NOTE]
> Zum Zeitpunkt der Entstehung dieses Artikels muss nicht eigens eine Erstellungsressource erstellt werden, da in LUIS automatisch ein Erstellungs-Testschlüssel generiert wird, wenn Sie im nächsten Abschnitt den Language Understanding Intelligent Service (LUIS) erstellen.

> [!TIP]
> Wenn Sie bereits über eine andere geeignete Ressourcengruppe in Ihrem Azure-Konto verfügen, beispielsweise, wenn Sie das [Azure Spatial Anchor](mrlearning-asa-ch1.md)-Tutorial abgeschlossen haben, können Sie diese Ressourcengruppe verwenden, statt eine neue zu erstellen.

Geben Sie noch auf der Seite „Erstellen“ die folgenden Werte ein:

* Geben Sie für **Name** einen passenden Namen für den Dienst ein, z. B. *MRTK-Tutorials-AzureSpeechServices*
* Wählen Sie als **Speicherort für die Vorhersage** einen Speicherort in der Nähe des Standorts Ihres App-Benutzers aus, z. B. *(USA) USA, Westen*
* Wählen Sie als **Tarif für Vorhersage** im Rahmen dieses Tutorials **F0 (5 Aufrufe pro Sekunde, 10.000 Aufrufe pro Monat)** aus

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-4.png)

Navigieren Sie als nächstes zur Registerkarte **Überprüfen + Erstellen**, überprüfen Sie die Details, und klicken Sie dann auf die Schaltfläche **Erstellen** am unteren Rand der Seite, um die Ressource sowie die neue Ressourcengruppe zu erstellen, falls Sie die Erstellung einer Ressourcengruppe konfiguriert haben:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-5.png)

> [!NOTE]
> Nachdem Sie auf die Schaltfläche „Erstellen“ geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. Dies kann einige Minuten in Anspruch nehmen.

Nachdem der Vorgang zum Erstellen der Ressource abgeschlossen ist, wird die Meldung angezeigt **Ihre Bereitstellung wurde abgeschlossen.** :

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-6.png)

## <a name="creating-the-language-understanding-intelligent-service-luis"></a>Erstellen des Language Understanding Intelligent Service (LUIS)

In diesem Abschnitt erstellen Sie eine LUIS-App, konfigurieren und trainieren ihr Vorhersagemodell und verbinden es mit der Azure-Vorhersageressource, die Sie im vorherigen Schritt erstellt haben.

Insbesondere erstellen Sie eine Absicht, die, falls der Benutzer sagt, dass eine Aktion ausgeführt werden soll, das Interactable.OnClick()-Ereignis für eine der drei roten Schaltflächen im Szenario auslöst, je nachdem, auf welche Schaltfläche der Benutzer verweist.

Wenn der Benutzer beispielsweise sagt **Fahre fort, starte die Rakete**, sagt die App vorher, dass **Fahre fort** bedeutet, dass eine **Aktion** ausgeführt werden soll, und dass das **anzuzielende** Interactable.OnClick()-Ereignis sich auf der Schaltfläche **Starten** befindet.

Dies sind die wichtigsten Schritte, die Sie durchführen müssen:

1. Erstellen einer LUIS-App
2. Erstellen von Absichten
3. Erstellen von Beispieläußerungen
4. Erstellen von Entitäten
5. Zuweisen von Entitäten zu den Beispieläußerungen
6. Trainieren, Testen und Veröffentlichen der App
7. Zuweisen einer Azure-Vorhersageressource zur App

### <a name="1-create-a-luis-app"></a>1. Erstellen einer LUIS-App

Melden Sie sich bei <a href="https://www.luis.ai" target="_blank">LUIS</a> mit demselben Benutzerkonto an, das Sie zum Erstellen der Azure-Ressource im vorherigen Abschnitt verwendet haben, wählen Sie Ihr Land aus, und stimmen Sie den Nutzungsbedingungen zu. Wenn Sie im nächsten Schritt aufgefordert werden, **Ihr Azure-Konto zu verknüpfen**, wählen Sie **Weiterhin den Testschlüssel verwenden** aus, um stattdessen eine Azure-Erstellungsressource zu verwenden.

> [!NOTE]
> Wenn Sie sich bereits für LUIS registriert haben und Ihr Erstellungs-Testschlüssel abgelaufen ist, finden Sie Informationen zum Umstellen Ihrer LUIS-Erstellungsressource auf Azure in der [Migrieren zu einem Azure-Ressourcen-Erstellungsschlüssel](https://docs.microsoft.com/azure/cognitive-services/luis/luis-migration-authoring)-Dokumentation.

Navigieren Sie nach der Anmeldung zur Seite **Meine Apps**, klicken Sie auf **Neue App erstellen**, und geben Sie im Fenster **Neue App erstellen** die folgenden Werte ein:

* Geben Sie für **Name** einen passenden Namen ein, z. B. *MRTK-Tutorials – AzureSpeechServices*
* Wählen Sie für **Kultur** die Option **Englisch** aus
* Geben Sie für **Beschreibung** optional eine passende Beschreibung ein

Klicken Sie dann auf die Schaltfläche **Erstellen**, um die neue App zu erstellen.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-1.png)

Wenn die neue App erstellt wurde, werden Sie zur **Dashboard** Seite der App geleitet:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-2.png)

### <a name="2-create-intents"></a>2. Erstellen von Absichten

Navigieren Sie von der Dashboard-Seite zur Seite „Build > App Assets > **Intents**“ (Erstellen > App-Ressourcen > Absichten), klicken Sie dann auf **Create new intent** (Neue Absicht erstellen), und geben Sie den folgenden Wert im Popupfenster **Create new intent** ein:

* Geben Sie als **Absichtsname** **PressButton** ein

Klicken Sie dann auf die Schaltfläche **Done** (Fertig), um die neue Ansicht zu erstellen.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-1.png)

> [!CAUTION]
> Im Rahmen dieses Tutorials verweist Ihr Unity-Projekt anhand des Namens auf diese Absicht, d. h. ‚PressButton‘. Es ist daher äußerst wichtig, dass Sie Ihre Absicht genau gleich benennen.

Wenn die neue Absicht erstellt wurde, werden Sie zu der Seite dieser Absicht geleitet:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-2.png)

### <a name="3-create-example-utterances"></a>3. Erstellen von Beispieläußerungen

Fügen Sie der Liste mit **Beispieläußerungen** der Absicht **PressButton** die folgenden Beispieläußerungen hinzu:

* Startsequenz aktivieren
* Platzierungshinweis anzeigen
* Startsequenz einleiten
* Schaltflächen für Platzierungshinweise drücken
* Gib mit einen Hinweis
* Startschaltfläche drücken
* Ich brauche einen Hinweis
* Taste „Zurücksetzen“ drücken
* Zeit zum Zurücksetzen des Experiments
* Fahre fort, starte die Rakete

Wenn alle Beispieläußerungen hinzugefügt wurden, sollte die Seite Ihrer Absicht PressButton so ähnlich aussehen:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step3-1.png)

> [!CAUTION]
> Im Rahmen dieses Tutorials verweist Ihr Unity-Projekt auf die Wörter „Hinweis“, „Hinweise“, „Zurücksetzen“ und „Starten“. Daher ist es äußerst wichtig, dass Sie diese Wörter in genau der gleichen Weise schreiben.

### <a name="4-create-entities"></a>4. Erstellen von Entitäten

Navigieren Sie von der Seite der Absicht PressButton zur Seite Erstellen > App-Ressourcen > **Entitäten**, klicken Sie dann auf **Neue Entität erstellen**, und geben Sie die folgenden Werte im Popupfenster **Neue Entität erstellen** ein:

* Geben Sie als **Entitätsname** **Aktion** ein
* Wählen Sie als **Entitätstyp** **Einfach** aus

Klicken Sie dann auf die Schaltfläche **Fertig**, um die neue Entität zu erstellen.

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-1.png)

**Wiederholen** Sie den vorhergehenden Schritt, um eine weitere Entität mit dem Namen **Ziel** zu erstellen, sodass Sie über zwei Entitäten verfügen, mit den Namen „Aktion“ und „Ziel“:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-2.png)

> [!CAUTION]
> Im Rahmen dieses Tutorials verweist Ihr Unity-Projekt anhand des Namens auf diese Entitäten, d. h. „Aktion“ und „Ziel“. Es ist daher äußerst wichtig, dass Sie Ihre Entitäten genau gleich benennen.

### <a name="5-assign-entities-to-the-example-utterances"></a>5. Zuweisen von Entitäten zu den Beispieläußerungen

Navigieren Sie auf der Seite Entitäten zurück zur Seite der Absicht **PressButton**.

Sobald Sie sich wieder auf der Seite der Absicht PressButton befinden, klicken Sie auf das Wort **Fahre**, dann auf das Wort **fort**, und wählen Sie dann im Kontext-Popupmenü **Aktion (Einfach)** aus, um **Fahre fort** als einen Entitätswert für **Aktion**-zu bezeichnen:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-1.png)

Der Ausdruck **Fahre fort** ist jetzt als Entitätswert für **Aktion** definiert. Wenn Sie den Mauszeiger auf dem Entitätsnamen „Aktion“ ruhen lassen, können Sie den zugeordneten Wert der Entität Aktion sehen:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-2.png)

> [!NOTE]
> Die rote Linie, die unter der Bezeichnung in der Abbildung oben angezeigt wird, weist darauf hin, dass der Entitätswert nicht vorhergesagt wurde. Dies wird behoben, wenn Sie das Modell im nächsten Abschnitt trainieren.

Klicken Sie als nächstes auf das Wort **starte**, und wählen Sie dann im Kontext-Popupmenü **Ziel (Einfach)** aus, um **starte** als einen **Ziel**-Entitätswert zu bezeichnen:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-3.png)

Das Wort **starte** ist jetzt als Entitätswert für **Ziel** definiert. Wenn Sie den Mauszeiger auf dem Entitätsnamen „Ziel“ ruhen lassen, können Sie den zugeordneten Wert der Entität Ziel sehen:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-4.png)

Die Beispieläußerung „Fahre fort, starte die Rakete“ für die PressButton-Absicht ist jetzt dafür konfiguriert, in folgender Weise vorhergesagt zu werden :

* Absicht: PressButton
* Action-Entität: Fahre fort
* Zielentität: starte

**Wiederholen** Sie die vorhergehenden zwei Schritte, um jeder der Beispieläußerungen eine Aktions- und eine Zielentitätsbezeichnung zuzuweisen, und behalten Sie dabei im Blick, dass die folgenden Wörter als **Ziel**-Entitäten bezeichnet werden sollen:

* **Hinweis** (zielt auf die HintsButton-Schaltfläche im Unity-Projekt ab)
* **Hinweise** (zielt auf die HintsButton-Schaltfläche im Unity-Projekt ab)
* **Zurücksetzen** (zielt auf die ResetButton-Schaltfläche im Unity-Projekt ab)
* **starte** (zielt auf die LaunchButton-Schaltfläche im Unity-Projekt ab)

Wenn alle Beispieläußerungen bezeichnet wurden, sollte die Seite Ihrer Absicht PressButton so ähnlich aussehen:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-5.png)

Um mit einem alternativen Verfahren zu prüfen, ob Sie die richtigen Entitäten zugewiesen haben, klicken Sie auf das Menü **Ansichtsoptionen**, und wechseln Sie zur Ansicht **Entitätswerte anzeigen**:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-6.png)

Jetzt, mit einer Ansicht, in der Entitätswerte angezeigt werden, können Sie den Mauszeiger auf den bezeichneten Wörtern und Ausdrücken ruhen lassen, um schnell den Namen der zugewiesenen Entität zu überprüfen:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-7.png)

### <a name="6-train-test-and-publish-the-app"></a>6. Trainieren, Testen und Veröffentlichen der App

Um die App zu trainieren, klicken Sie auf die Schaltfläche **Trainieren**, und warten Sie, bis der Trainingsprozess abgeschlossen ist:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-1.png)

> [!NOTE]
> Wie Sie in der Abbildung oben sehen können, wurden die roten Linien unter allen Bezeichnungen entfernt, was darauf hinweist, dass alle Entitätswerte vorhergesagt wurden. Beachten Sie außerdem, dass das Statussymbol links auf der Trainieren-Schaltfläche die Farbe von rot zu grün gewechselt hat.

Wenn die Verarbeitung des Trainings abgeschlossen ist, klicken Sie auf die Schaltfläche **Testen**, geben Sie dann **Fahre fort, starte die Rakete** ein, und drücken Sie die EINGABETASTE:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-2.png)

Wenn die Testäußerung verarbeitet wurde, klicken Sie auf **Prüfen**, um das Testergebnis anzuzeigen:

* Absicht: PressButton (mit einer Sicherheit von 98,5 %)
* Aktion-Entität:Fahre fort
* Ziel-Entität: starte

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-3.png)

Um die App zu veröffentlichen, klicken Sie oben rechts auf die Schaltfläche **Publish** (Veröffentlichen), wählen Sie dann im Popupfenster **Choose your publishing slot and settings** (Wählen Sie Ihren Veröffentlichungsslot und Ihre Einstellungen) **Production** (Produktion) aus, und klicken Sie auf die Schaltfläche **Publish**:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-4.png)

Warten Sie auf den Abschluss des Veröffentlichungsprozesses:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-5.png)

### <a name="7-assign-an-azure-prediction-resource-to-the-app"></a>7. Zuweisen einer Azure-Vorhersageressource zur App

Navigieren Sie zur Seite Verwalten > Anwendungseinstellungen > **Azure-Ressourcen**:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-1.png)

Klicken Sie auf der Seite „Azure-Ressourcen“ auf die Schaltfläche **Vorhersageressource hinzufügen**, und wählen Sie die folgenden Werte im Popupfenster **Ihrer App eine Ressource zuweisen** aus:

* Wählen Sie als **Mandantenname** den Namen Ihres Mandanten aus
* Wählen Sie als **Abonnementname** das gleiche Abonnement aus, das Sie zuvor beim [Erstellen der Azure Language Understanding-Ressource](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource) verwendet haben
* Wählen Sie als **Name der LUIS-Ressource** die gleiche Vorhersageressource aus, die Sie zuvor beim [Erstellen der Azure Language Understanding-Ressource](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource) erstellt haben

Klicken Sie dann auf die Schaltfläche **Ressource zuweisen**, um Ihrer App die Azure-Vorhersageressource zuzuweisen:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-2.png)

Wenn die Ressource zugewiesen wurde, sollte Ihre Seite „Azure-Ressourcen“ so ähnlich wie in der folgenden Abbildung aussehen:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-3.png)

## <a name="connecting-the-unity-project-to-the-luis-app"></a>Verbinden des Unity-Projekts mit der LUIS-App

Klicken Sie auf der Seite Verwalten > Anwendungseinstellungen > **Azure-Ressourcen** auf das Symbol **Kopieren**, um die **Beispielabfrage** zu kopieren:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-1.png)

Wählen Sie wieder in Ihrem Unity-Projekt im Hierarchiefenster das Objekt **Lunarcom** aus, suchen Sie dann im Inspektor-Fenster die Komponente **Lunarcom Intent Recognizer (Script)** aus, und konfigurieren Sie sie wie folgt:

* Fügen Sie in das Feld **LUIS-Endpunkt** die **Beispielabfrage** ein, die Sie im vorherigen Schritt kopiert hatten:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-2.png)

## <a name="testing-and-improving-the-intent-recognition"></a>Testen und Verbessern der Absichtserkennung

Um Absichtserkennung direkt im Unity-Editor zu verwenden, müssen Sie Ihrem Entwicklungscomputer die Verwendung der Diktatfunktion erlauben. Um diese Einstellung zu überprüfen, öffnen Sie Windows **Einstellungen**, wählen Sie dann **Datenschutz** > **Sprache** aus, und vergewissern Sie sich, dass **Online-Spracherkennung** aktiviert ist:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-1.png)

Wenn Sie jetzt in den Spielmodus wechseln, können Sie die Absichtserkennung testen, indem Sie zuerst auf die Raketenschaltfläche klicken. Angenommen, dass Ihr Computer über ein Mikrofon verfügt, sehen Sie dann, wenn Sie die erste Beispieläußerung **Fahre fort, starte die Rakete** sprechen, dass das LunarModule in den Weltraum abhebt:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-2.png)

Probieren Sie alle **Beispieläußerungen** und dann ebenso einige **Variationen der Beispieläußerungen** sowie einige **zufällige Äußerungen** aus.

Kehren Sie als nächstes zu <a href="https://www.luis.ai" target="_blank">LUIS</a> zurück, navigieren Sie zur Seite Erstellen > App-Leistung verbessern > **Endpunktäußerungen überprüfen**, verwenden Sie die **Umschalt**-Schaltfläche, um von der Standardansicht „Entitäten“ zur **Tokenansicht** zu wechseln, und überprüfen Sie dann die Äußerungen:

* Ändern und entfernen Sie in der Spalte **Äußerungen** die zugewiesenen Bezeichnungen nach Bedarf, sodass sie sich an Ihrer Absicht orientieren
* Überprüfen Sie in der Spalte **Zugeordnete Absicht**, ob die Absicht richtig ist
* Klicken Sie in der Spalte **Hinzufügen/Löschen** auf die Schaltfläche mit dem grünen Markierungshäkchen, um die Äußerung hinzuzufügen, oder auf die Schaltfläche mit dem roten X, um sie zu löschen

Wenn Sie so viele Äußerungen überprüft haben, wie Sie möchten, klicken Sie auf die Schaltfläche **Trainieren**, um das Modell erneut zu trainieren, und dann auf die Schaltfläche **Veröffentlichen**, um die aktualisierte App erneut zu veröffentlichen:

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-3.png)

> [!NOTE]
> Wenn sich eine Endpunktäußerung nicht an der PressButton-Absicht orientiert, Sie aber möchten, dass für die Äußerung keine Absicht gilt, können Sie die zugewiesene Absicht in Keine ändern.

**Wiederholen** Sie diesen Vorgang so oft, wie Sie möchten, um Ihr App-Modell zu verbessern.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Ihr Projekt verfügt jetzt über KI-gestützte Sprachbefehle, die es Ihrer Anwendung ermöglichen, die Absicht der Benutzer auch dann zu erkennen, wenn sie keine präzisen Befehle äußern. Führen Sie die Anwendung auf Ihrem Gerät aus, um sicherzustellen, dass das Feature ordnungsgemäß funktioniert.
