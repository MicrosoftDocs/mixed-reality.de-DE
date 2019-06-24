## <a name="lesson-4"></a><span data-ttu-id="459e0-101">Lektion 4</span><span class="sxs-lookup"><span data-stu-id="459e0-101">Lesson 4</span></span>

<span data-ttu-id="459e0-102">In Kapitel 4 wird der beabsichtigte Sprachfunktion für Dienste erläutert.</span><span class="sxs-lookup"><span data-stu-id="459e0-102">In chapter 4, we will explore the Speech services Intent feature.</span></span> <span data-ttu-id="459e0-103">Wir werden unsere Azure LUIS-Portal einrichten, unser Absichten/Entitäten/Äußerungen einrichten, unsere Absicht-Ressource veröffentlicht, Herstellen einer Verbindung unsere Absicht-Ressource mit der Unity-app und unsere erste Absicht API-Aufruf.</span><span class="sxs-lookup"><span data-stu-id="459e0-103">We will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

1. <span data-ttu-id="459e0-104">Ermöglichen Sie Ihren Computer zu diktieren, dazu, zu Windows-Einstellungen wechseln, wählen Sie "Datenschutz", und klicken Sie dann "Speech", und schließlich "Freihand & eingeben" und Sprachdienste und Typisierung Vorschläge aktivieren.</span><span class="sxs-lookup"><span data-stu-id="459e0-104">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

> <span data-ttu-id="459e0-108">Hinweis: Informationen dazu, wie Sie dazu auf einem Mac/Macbook, klicken Sie auf [hier](linkgoeshere).</span><span class="sxs-lookup"><span data-stu-id="459e0-108">note: for information on how to do this on a Mac/Macbook, click [here](linkgoeshere).</span></span>

2. <span data-ttu-id="459e0-109">Melden Sie sich bei der [Azure-Portal](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="459e0-109">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="459e0-110">Sobald Sie, klicken Sie auf eine Ressource erstellen, und suchen Sie nach "Sprachverständnis angemeldet sind", und klicken Sie auf eingeben.</span><span class="sxs-lookup"><span data-stu-id="459e0-110">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. <span data-ttu-id="459e0-112">Wählen Sie die Schaltfläche "erstellen", um eine Instanz dieses Diensts zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="459e0-112">Select the Create button, to create an instance of this service.</span></span> <span data-ttu-id="459e0-113">Benennen Sie das Projekt "Speech_SDK_Learning_Module", und wählen Sie "Nutzungsbasierte Bezahlung."</span><span class="sxs-lookup"><span data-stu-id="459e0-113">Name your project “Speech_SDK_Learning_Module” and select “Pay As You Go.”</span></span>

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. <span data-ttu-id="459e0-116">Wählen Sie Ihre Region aus.</span><span class="sxs-lookup"><span data-stu-id="459e0-116">Select your Region.</span></span>  <span data-ttu-id="459e0-117">Wählen Sie in diesem Tutorial "(USA) West US".</span><span class="sxs-lookup"><span data-stu-id="459e0-117">For the purpose of this tutorial, select "(US) West US."</span></span> <span data-ttu-id="459e0-118">Wählen Sie dann "F0" für den Tarif an.</span><span class="sxs-lookup"><span data-stu-id="459e0-118">Then choose "F0" for the pricing tier.</span></span> <span data-ttu-id="459e0-119">Klicken Sie nun auf "erstellen" (befindet sich in der unteren linken Ecke) um die Ressource zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="459e0-119">Now click "create" (located in the bottom left corner) to create the resource.</span></span>

   >  <span data-ttu-id="459e0-120">Hinweis: Sobald Sie auf "erstellen" geklickt haben, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.</span><span class="sxs-lookup"><span data-stu-id="459e0-120">note: once you have clicked on "create," you will have to wait for the service to be created, this might take a minute.</span></span>

5. <span data-ttu-id="459e0-121">Im Portal wird eine Benachrichtigung angezeigt, sobald die Ressource erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="459e0-121">A notification will appear in the portal once the Resource is created.</span></span> <span data-ttu-id="459e0-122">Klicken Sie auf diese Benachrichtigung, und wählen Sie "Zu Ressource wechseln."</span><span class="sxs-lookup"><span data-stu-id="459e0-122">Click on this notification and select "Go to resource."</span></span>

6. <span data-ttu-id="459e0-123">Von der Seite "Schnellstart" des Diensts "LUIS API" der erste Schritt navigieren Sie, ziehen Sie die "Keys", und klicken Sie auf "Schlüssel" (Sie können die Bereitstellungsinformationen auch durch Klicken auf den blauen Link "Schlüssel", in der folgenden Abbildung dargestellt).</span><span class="sxs-lookup"><span data-stu-id="459e0-123">From the "Quick Start" page of your "LUIS API" service, navigate to the first step, grab your "keys," and click "keys" (you can also achieve this by clicking the blue hyperlink "keys," shown in the image below).</span></span> <span data-ttu-id="459e0-124">Dadurch wird den Dienst "Schlüssel". angezeigt.</span><span class="sxs-lookup"><span data-stu-id="459e0-124">This will reveal your service, "Keys."</span></span> <span data-ttu-id="459e0-125">Speichern Sie eine Kopie einer der Schlüssel, damit Sie sie später in der app verwenden können.</span><span class="sxs-lookup"><span data-stu-id="459e0-125">Save a copy of one of the keys so you can use it later in the app.</span></span>

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. <span data-ttu-id="459e0-127">Zurück auf der Seite "Schnellstart" unter dem Abschnitt 2 b klicken Sie auf "Language Understanding-Portal" (in der Abbildung oben dargestellt) aus, um zur Webseite umgeleitet werden, das Sie verwenden werden, um den neuen Dienst, in der LUIS-Anwendung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="459e0-127">Back in the "Quick Start" page under Section 2b, click on "Language Understanding Portal" (shown in the image above) to be redirected to the webpage which you will use to create your new service, within the LUIS application.</span></span>

> <span data-ttu-id="459e0-128">Hinweis: Beim Erreichen der "Language Understanding-Portal", müssen Sie sich anmelden, wenn Sie noch nicht mit den gleichen Anmeldeinformationen wie Ihr Azure-Portal sind.</span><span class="sxs-lookup"><span data-stu-id="459e0-128">note: Upon reaching the "Language Understanding Portal," you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="459e0-129">Ist dies zum ersten Mal LUIS verwenden, müssen Sie einen Bildlauf zum unteren Rand der Seite Willkommen zu suchen, und klicken auf "erstellen LUIS"-app.</span><span class="sxs-lookup"><span data-stu-id="459e0-129">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

8. <span data-ttu-id="459e0-130">Sobald Sie angemeldet sind, klicken Sie auf meine Apps, (Wenn Sie nicht in diesem Abschnitt, derzeit sind).</span><span class="sxs-lookup"><span data-stu-id="459e0-130">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="459e0-131">Sie können dann auf die neue Anwendung erstellen klicken.</span><span class="sxs-lookup"><span data-stu-id="459e0-131">You can then click on Create new app.</span></span> <span data-ttu-id="459e0-132">Benennen Sie die neue app "Speech SDK Lernmodul."</span><span class="sxs-lookup"><span data-stu-id="459e0-132">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="459e0-133">Fügen Sie in das Beschreibungsfeld ein ist, werden auch "Speech SDK-Learning-Modul" hinzu.</span><span class="sxs-lookup"><span data-stu-id="459e0-133">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="459e0-134">Klicken Sie dann auf "Fertig".</span><span class="sxs-lookup"><span data-stu-id="459e0-134">Then click "done."</span></span>

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> <span data-ttu-id="459e0-137">Hinweis: Wenn Ihre app um zu eine anderen Sprache als Englisch zu verstehen, sollten Sie die "Culture" in der entsprechenden Sprache ändern.</span><span class="sxs-lookup"><span data-stu-id="459e0-137">note: If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

9. <span data-ttu-id="459e0-138">Klicken Sie auf "Build" befindet sich in der rechten oberen Ecke.</span><span class="sxs-lookup"><span data-stu-id="459e0-138">Click “Build” located in the top right.</span></span>

10. <span data-ttu-id="459e0-139">Wählen Sie unter App-Ressourcen auf der linken Seite "Intents", und klicken Sie auf "Erstellen einer neuen Intent", und nennen Sie sie "PressButton."</span><span class="sxs-lookup"><span data-stu-id="459e0-139">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span> 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> <span data-ttu-id="459e0-141">Hinweis: Es ist wichtig, dass die Namen von Intents und Entitäten, die in diesem Tutorial verwendet werden, da die app Lunarcom sie verweist anhand des Namens.</span><span class="sxs-lookup"><span data-stu-id="459e0-141">note: it is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span>  <span data-ttu-id="459e0-142">Für andere Projekte können die Benennungskonventionen für beliebige sein.</span><span class="sxs-lookup"><span data-stu-id="459e0-142">For other projects, naming conventions can be whatever you choose.</span></span> 
>
> <span data-ttu-id="459e0-143">Hinweis: Sie verfügen nun über die Absicht "2" - "PressButton" und "None".</span><span class="sxs-lookup"><span data-stu-id="459e0-143">note: you should now have 2 Intents - “PressButton” and “None."</span></span>

11. <span data-ttu-id="459e0-144">Wählen Sie unter App-Ressourcen auf der linken Seite "Entitäten" und klicken Sie auf "Neue Entität erstellen", und nennen Sie sie "Aktion" und behalten Sie den Entitätstyp als "Einfach".</span><span class="sxs-lookup"><span data-stu-id="459e0-144">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. <span data-ttu-id="459e0-146">Klicken Sie erneut auf "Neue Entität erstellen", und nennen Sie es "Target", und behalten Sie auch den Entitätstyp als "Einfach".</span><span class="sxs-lookup"><span data-stu-id="459e0-146">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. <span data-ttu-id="459e0-148">Wählen Sie unter App-Ressourcen auf der linken Seite "Intents" und klicken Sie dann auf Ihre "PressButton" Absicht, die Sie in Schritt 10 erstellt.</span><span class="sxs-lookup"><span data-stu-id="459e0-148">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. <span data-ttu-id="459e0-150">Klicken Sie auf die Dropdownliste "Anzeigen der Optionen" auf der rechten Seite, und wählen Sie "Entitätswerte anzeigen" aus.</span><span class="sxs-lookup"><span data-stu-id="459e0-150">Click on the "View options" dropdown on the right and select "show entity values."</span></span> 

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)<span data-ttu-id="459e0-152">Klicken Sie auf der "Geben Sie ein Beispiel für..."</span><span class="sxs-lookup"><span data-stu-id="459e0-152">Click on the “Enter an example…”</span></span> <span data-ttu-id="459e0-153">Textfeld.</span><span class="sxs-lookup"><span data-stu-id="459e0-153">textbox.</span></span> <span data-ttu-id="459e0-154">Geben Sie dann die folgenden äußerungen aus:</span><span class="sxs-lookup"><span data-stu-id="459e0-154">Then, enter the following utterances:</span></span> 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. <span data-ttu-id="459e0-156">Klicken Sie auf die Dropdownliste "Anzeigen der Optionen" auf der rechten Seite, und wählen Sie "Entitätsnamen anzeigen" aus.</span><span class="sxs-lookup"><span data-stu-id="459e0-156">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. <span data-ttu-id="459e0-158">Sicherstellen, dass jede der 10 Äußerungen haben die folgenden Bezeichnungen für die Entität in den folgenden Stellen, um 1.) Sie klicken Wörter, die mit falscher Achsenbeschriftung sind und in das Popupfenster, auswählen von "remove Label" und 2.) Klicken Sie auf ein Wort, die mit der Bezeichnung werden sollte und im Popupfenster die entsprechende Bezeichnung auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="459e0-158">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. <span data-ttu-id="459e0-160">Jetzt, um das Modell zu veröffentlichen, klicken Sie auf "Train" in der rechten oberen Ecke.</span><span class="sxs-lookup"><span data-stu-id="459e0-160">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="459e0-161">Klicken Sie dann nach Abschluss der Verarbeitung, klicken Sie auf "Test" in der rechten oberen Ecke.</span><span class="sxs-lookup"><span data-stu-id="459e0-161">Then, once it has finished processing, click "Test" in the top right.</span></span>

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. <span data-ttu-id="459e0-163">Geben Sie in "die Schaltfläche" Start "in das Textfeld auswählen".</span><span class="sxs-lookup"><span data-stu-id="459e0-163">Enter in “select the launch button” in  the textbox.</span></span>

> <span data-ttu-id="459e0-164">Hinweis: wir nicht hinzufügen "auswählen" als Aktion in einem der unsere Äußerungen -, jedoch das Modell, wenn Sie auf "Prüfen" klicken, als eine Aktion Entität erkannt werden "select".</span><span class="sxs-lookup"><span data-stu-id="459e0-164">note: we did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. <span data-ttu-id="459e0-166">Nun, klicken Sie auf "Veröffentlichen" in der rechten oberen Ecke.</span><span class="sxs-lookup"><span data-stu-id="459e0-166">Now, click "publish" in the top right.</span></span> <span data-ttu-id="459e0-167">Stellen Sie sicher, dass die Dropdownliste "Produktion", sagt aus, und klicken Sie auf "Veröffentlichen Sie auch im Popup".</span><span class="sxs-lookup"><span data-stu-id="459e0-167">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span> 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. <span data-ttu-id="459e0-169">Nach der Veröffentlichung sollte eine grüne Leiste am oberen Rand der Seite angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="459e0-169">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="459e0-170">Klicken Sie auf der grünen Leiste an, die auf der Seite "Verwalten" ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="459e0-170">Click on the green bar to be taken to the "Manage" page.</span></span> 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. <span data-ttu-id="459e0-172">Klicken Sie auf der linken Seite auf "Schlüssel und Endpunkten" unter "Anwendungseinstellungen".</span><span class="sxs-lookup"><span data-stu-id="459e0-172">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="459e0-173">Legen Sie dann die Drop-down "Veröffentlichen zu" als "Produktion".</span><span class="sxs-lookup"><span data-stu-id="459e0-173">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="459e0-174">Legen Sie die Zeitzone auf Ihren, und aktivieren Sie das Kontrollkästchen Alle prognostizierten intent-Werte enthalten.</span><span class="sxs-lookup"><span data-stu-id="459e0-174">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="459e0-175">Klicken Sie abschließend auf "Assign-Ressource."</span><span class="sxs-lookup"><span data-stu-id="459e0-175">Lastly, Click on "Assign resource."</span></span>

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. <span data-ttu-id="459e0-177">Wählen Sie aus der ersten Dropdownliste-Mandanten, und wählen Sie "Nutzungsbasierte Bezahlung", in der Dropdownliste "Abonnementname".</span><span class="sxs-lookup"><span data-stu-id="459e0-177">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="459e0-178">Wählen Sie LUIS-Ressourcenname Ressource, die wir zuvor erstellt, in den Schritten 1 bis 5 haben aus.</span><span class="sxs-lookup"><span data-stu-id="459e0-178">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="459e0-179">Klicken Sie auf "Zuweisen von Ressource".</span><span class="sxs-lookup"><span data-stu-id="459e0-179">Then, click on "Assign resource."</span></span> 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> <span data-ttu-id="459e0-181">Hinweis: Achten Sie darauf, kopieren und speichern Sie die Endpunkt-URL der Ressource, die wir nur zugewiesen, sodass sie leicht zugänglich ist, für den nächsten Abschnitt ist zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="459e0-181">note: ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>
>
> <span data-ttu-id="459e0-182">Hinweis: Legen Sie für den Namen des Mandanten, die Ihr Unternehmen oder das Profil, das Sie für diese Anwendung erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="459e0-182">note: for the Tenant name, put your corporation or profile that you created for this application.</span></span>

23. <span data-ttu-id="459e0-183">Klicken Sie nun öffnen Sie die neue app in Unity, und wählen Sie das Lunarcom_Base-Objekt in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="459e0-183">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="459e0-184">Klicken Sie auf "Komponente hinzufügen" im Bedienfeld "Inspector", und suchen Sie nach, und wählen Sie "LunarcomIntentRecognizer."</span><span class="sxs-lookup"><span data-stu-id="459e0-184">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. <span data-ttu-id="459e0-186">Geben Sie die Endpunkt-URL, die Sie in Schritt 22 gespeichert haben, im Feld Luis Endpoint von "LunarcomIntentRecognizer" in den Bereich der Eigenschaftenanalyse.</span><span class="sxs-lookup"><span data-stu-id="459e0-186">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span> 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  <span data-ttu-id="459e0-188">Hinweis: In der Komponente "LunarcomOfflineRecognizer" im Bedienfeld "Inspector" sicher, dass "deaktivieren" für "SimulateOfflineMode" andernfalls ausgewählt ist, testen das Programm nicht funktioniert.</span><span class="sxs-lookup"><span data-stu-id="459e0-188">note: In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span> 

25. <span data-ttu-id="459e0-189">Drücken Sie auf die Wiedergabeschaltfläche im Unity-Editor, und klicken Sie auf die Rocket-Schaltfläche, um die Absicht bei gesprochenen Inhalten zu starten.</span><span class="sxs-lookup"><span data-stu-id="459e0-189">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="459e0-190">Ramsch den Ausdruck "die Schaltfläche" Start-Rocket "select".</span><span class="sxs-lookup"><span data-stu-id="459e0-190">Utter the phrase “select the launch rocket button.”</span></span>

>  <span data-ttu-id="459e0-191">Hinweis: Die app die gewünschte Funktion erkannt und aktiviert die Schaltfläche "Rocket".</span><span class="sxs-lookup"><span data-stu-id="459e0-191">note: The app recognized the desired function and activated the rocket button.</span></span>
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="459e0-193">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="459e0-193">Congratulations</span></span>

<span data-ttu-id="459e0-194">Offiziell haben Sie gelernt, Speech-Befehle aus dem Speech SDK-Programm hinzufügen!</span><span class="sxs-lookup"><span data-stu-id="459e0-194">You officially learned how to add speech commands from the speech SDK program!</span></span> <span data-ttu-id="459e0-195">Das Programm kann jetzt Sprachbefehle aller Arten von Varianten erkennen.</span><span class="sxs-lookup"><span data-stu-id="459e0-195">Now your program can recognize speech commands of all kinds of variants.</span></span> <span data-ttu-id="459e0-196">Probieren Sie es aus, und etwas Spaß dabei!</span><span class="sxs-lookup"><span data-stu-id="459e0-196">Test it out and have a little fun with it!</span></span>

[<span data-ttu-id="459e0-197">Nächste Lektion: Speech SDK Lektion 5</span><span class="sxs-lookup"><span data-stu-id="459e0-197">Next Lesson: Speech SDK Lesson 5</span></span>](placeholderlink)

