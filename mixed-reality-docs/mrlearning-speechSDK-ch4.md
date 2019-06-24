## <a name="lesson-4"></a>Lektion 4

In Kapitel 4 wird der beabsichtigte Sprachfunktion für Dienste erläutert. Wir werden unsere Azure LUIS-Portal einrichten, unser Absichten/Entitäten/Äußerungen einrichten, unsere Absicht-Ressource veröffentlicht, Herstellen einer Verbindung unsere Absicht-Ressource mit der Unity-app und unsere erste Absicht API-Aufruf.

1. Ermöglichen Sie Ihren Computer zu diktieren, dazu, zu Windows-Einstellungen wechseln, wählen Sie "Datenschutz", und klicken Sie dann "Speech", und schließlich "Freihand & eingeben" und Sprachdienste und Typisierung Vorschläge aktivieren.

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

> Hinweis: Informationen dazu, wie Sie dazu auf einem Mac/Macbook, klicken Sie auf [hier](linkgoeshere).

2. Melden Sie sich bei der [Azure-Portal](https://portal.azure.com/). Sobald Sie, klicken Sie auf eine Ressource erstellen, und suchen Sie nach "Sprachverständnis angemeldet sind", und klicken Sie auf eingeben.

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. Wählen Sie die Schaltfläche "erstellen", um eine Instanz dieses Diensts zu erstellen. Benennen Sie das Projekt "Speech_SDK_Learning_Module", und wählen Sie "Nutzungsbasierte Bezahlung."

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. Wählen Sie Ihre Region aus.  Wählen Sie in diesem Tutorial "(USA) West US". Wählen Sie dann "F0" für den Tarif an. Klicken Sie nun auf "erstellen" (befindet sich in der unteren linken Ecke) um die Ressource zu erstellen.

   >  Hinweis: Sobald Sie auf "erstellen" geklickt haben, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.

5. Im Portal wird eine Benachrichtigung angezeigt, sobald die Ressource erstellt wird. Klicken Sie auf diese Benachrichtigung, und wählen Sie "Zu Ressource wechseln."

6. Von der Seite "Schnellstart" des Diensts "LUIS API" der erste Schritt navigieren Sie, ziehen Sie die "Keys", und klicken Sie auf "Schlüssel" (Sie können die Bereitstellungsinformationen auch durch Klicken auf den blauen Link "Schlüssel", in der folgenden Abbildung dargestellt). Dadurch wird den Dienst "Schlüssel". angezeigt. Speichern Sie eine Kopie einer der Schlüssel, damit Sie sie später in der app verwenden können.

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. Zurück auf der Seite "Schnellstart" unter dem Abschnitt 2 b klicken Sie auf "Language Understanding-Portal" (in der Abbildung oben dargestellt) aus, um zur Webseite umgeleitet werden, das Sie verwenden werden, um den neuen Dienst, in der LUIS-Anwendung zu erstellen.

> Hinweis: Beim Erreichen der "Language Understanding-Portal", müssen Sie sich anmelden, wenn Sie noch nicht mit den gleichen Anmeldeinformationen wie Ihr Azure-Portal sind. Ist dies zum ersten Mal LUIS verwenden, müssen Sie einen Bildlauf zum unteren Rand der Seite Willkommen zu suchen, und klicken auf "erstellen LUIS"-app.

8. Sobald Sie angemeldet sind, klicken Sie auf meine Apps, (Wenn Sie nicht in diesem Abschnitt, derzeit sind). Sie können dann auf die neue Anwendung erstellen klicken. Benennen Sie die neue app "Speech SDK Lernmodul." Fügen Sie in das Beschreibungsfeld ein ist, werden auch "Speech SDK-Learning-Modul" hinzu. Klicken Sie dann auf "Fertig".

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> Hinweis: Wenn Ihre app um zu eine anderen Sprache als Englisch zu verstehen, sollten Sie die "Culture" in der entsprechenden Sprache ändern.

9. Klicken Sie auf "Build" befindet sich in der rechten oberen Ecke.

10. Wählen Sie unter App-Ressourcen auf der linken Seite "Intents", und klicken Sie auf "Erstellen einer neuen Intent", und nennen Sie sie "PressButton." 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> Hinweis: Es ist wichtig, dass die Namen von Intents und Entitäten, die in diesem Tutorial verwendet werden, da die app Lunarcom sie verweist anhand des Namens.  Für andere Projekte können die Benennungskonventionen für beliebige sein. 
>
> Hinweis: Sie verfügen nun über die Absicht "2" - "PressButton" und "None".

11. Wählen Sie unter App-Ressourcen auf der linken Seite "Entitäten" und klicken Sie auf "Neue Entität erstellen", und nennen Sie sie "Aktion" und behalten Sie den Entitätstyp als "Einfach".

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. Klicken Sie erneut auf "Neue Entität erstellen", und nennen Sie es "Target", und behalten Sie auch den Entitätstyp als "Einfach".

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. Wählen Sie unter App-Ressourcen auf der linken Seite "Intents" und klicken Sie dann auf Ihre "PressButton" Absicht, die Sie in Schritt 10 erstellt.

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. Klicken Sie auf die Dropdownliste "Anzeigen der Optionen" auf der rechten Seite, und wählen Sie "Entitätswerte anzeigen" aus. 

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)Klicken Sie auf der "Geben Sie ein Beispiel für..." Textfeld. Geben Sie dann die folgenden äußerungen aus: 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. Klicken Sie auf die Dropdownliste "Anzeigen der Optionen" auf der rechten Seite, und wählen Sie "Entitätsnamen anzeigen" aus.

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. Sicherstellen, dass jede der 10 Äußerungen haben die folgenden Bezeichnungen für die Entität in den folgenden Stellen, um 1.) Sie klicken Wörter, die mit falscher Achsenbeschriftung sind und in das Popupfenster, auswählen von "remove Label" und 2.) Klicken Sie auf ein Wort, die mit der Bezeichnung werden sollte und im Popupfenster die entsprechende Bezeichnung auszuwählen.

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. Jetzt, um das Modell zu veröffentlichen, klicken Sie auf "Train" in der rechten oberen Ecke. Klicken Sie dann nach Abschluss der Verarbeitung, klicken Sie auf "Test" in der rechten oberen Ecke.

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. Geben Sie in "die Schaltfläche" Start "in das Textfeld auswählen".

> Hinweis: wir nicht hinzufügen "auswählen" als Aktion in einem der unsere Äußerungen -, jedoch das Modell, wenn Sie auf "Prüfen" klicken, als eine Aktion Entität erkannt werden "select".
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. Nun, klicken Sie auf "Veröffentlichen" in der rechten oberen Ecke. Stellen Sie sicher, dass die Dropdownliste "Produktion", sagt aus, und klicken Sie auf "Veröffentlichen Sie auch im Popup". 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. Nach der Veröffentlichung sollte eine grüne Leiste am oberen Rand der Seite angezeigt werden.  Klicken Sie auf der grünen Leiste an, die auf der Seite "Verwalten" ausgeführt werden. 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. Klicken Sie auf der linken Seite auf "Schlüssel und Endpunkten" unter "Anwendungseinstellungen". Legen Sie dann die Drop-down "Veröffentlichen zu" als "Produktion". Legen Sie die Zeitzone auf Ihren, und aktivieren Sie das Kontrollkästchen Alle prognostizierten intent-Werte enthalten. Klicken Sie abschließend auf "Assign-Ressource."

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. Wählen Sie aus der ersten Dropdownliste-Mandanten, und wählen Sie "Nutzungsbasierte Bezahlung", in der Dropdownliste "Abonnementname". Wählen Sie LUIS-Ressourcenname Ressource, die wir zuvor erstellt, in den Schritten 1 bis 5 haben aus. Klicken Sie auf "Zuweisen von Ressource". 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> Hinweis: Achten Sie darauf, kopieren und speichern Sie die Endpunkt-URL der Ressource, die wir nur zugewiesen, sodass sie leicht zugänglich ist, für den nächsten Abschnitt ist zugeordnet.
>
> Hinweis: Legen Sie für den Namen des Mandanten, die Ihr Unternehmen oder das Profil, das Sie für diese Anwendung erstellt haben.

23. Klicken Sie nun öffnen Sie die neue app in Unity, und wählen Sie das Lunarcom_Base-Objekt in der Hierarchie. Klicken Sie auf "Komponente hinzufügen" im Bedienfeld "Inspector", und suchen Sie nach, und wählen Sie "LunarcomIntentRecognizer."

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. Geben Sie die Endpunkt-URL, die Sie in Schritt 22 gespeichert haben, im Feld Luis Endpoint von "LunarcomIntentRecognizer" in den Bereich der Eigenschaftenanalyse. 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  Hinweis: In der Komponente "LunarcomOfflineRecognizer" im Bedienfeld "Inspector" sicher, dass "deaktivieren" für "SimulateOfflineMode" andernfalls ausgewählt ist, testen das Programm nicht funktioniert. 

25. Drücken Sie auf die Wiedergabeschaltfläche im Unity-Editor, und klicken Sie auf die Rocket-Schaltfläche, um die Absicht bei gesprochenen Inhalten zu starten. Ramsch den Ausdruck "die Schaltfläche" Start-Rocket "select".

>  Hinweis: Die app die gewünschte Funktion erkannt und aktiviert die Schaltfläche "Rocket".
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Offiziell haben Sie gelernt, Speech-Befehle aus dem Speech SDK-Programm hinzufügen! Das Programm kann jetzt Sprachbefehle aller Arten von Varianten erkennen. Probieren Sie es aus, und etwas Spaß dabei!

[Nächste Lektion: Speech SDK Lektion 5](placeholderlink)

