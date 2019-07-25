---
title: Spracherkennung und-Aufzeichnung für das Lern-SDK-Modul von Mr
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 0cffb9ac8f61f77b77fc5925264b95ba57d94ece
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460349"
---
# <a name="speech-sdk-learning-module---intent-and-natural-language-understanding"></a><span data-ttu-id="ff08c-104">Sprach-SDK-Lernmodul: beabsichtigte und natürliche Language Understanding</span><span class="sxs-lookup"><span data-stu-id="ff08c-104">Speech SDK Learning Module - Intent and Natural Language Understanding</span></span>

<span data-ttu-id="ff08c-105">In dieser Lektion erfahren Sie mehr über das Intent-Feature des Azure Speech Service.</span><span class="sxs-lookup"><span data-stu-id="ff08c-105">In this lesson, we will explore the Azure Speech Service's Intent feature.</span></span> <span data-ttu-id="ff08c-106">Mit der Intent-Funktion können wir unsere Anwendung mit Ki-gestützten Sprachbefehlen ausstatten, bei denen Benutzer nicht spezifische Sprachbefehle sagen können und dennoch vom System verstanden werden können.</span><span class="sxs-lookup"><span data-stu-id="ff08c-106">The Intent feature allows us to equip our application with AI-powered voice commands, where users can say non-specific voice commands, and still have their intent understood by the system.</span></span> <span data-ttu-id="ff08c-107">In dieser Lektion richten wir unser Azure-Luis-Portal ein, richten unsere Absichten/Entitäten/Äußerungen ein, veröffentlichen unsere Intent-Ressource, verbinden unsere Unity-App mit unserer Intent-Ressource und machen unseren ersten beabsichtigten API-Rückruf.</span><span class="sxs-lookup"><span data-stu-id="ff08c-107">During this lesson, we will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

## <a name="objectives"></a><span data-ttu-id="ff08c-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="ff08c-108">Objectives</span></span>

- <span data-ttu-id="ff08c-109">Erfahren Sie, wie Sie in unserer Anwendung das Verständnis von Absicht und natürlicher Sprache einrichten</span><span class="sxs-lookup"><span data-stu-id="ff08c-109">Learn how to set up intent and natural language understanding in our application</span></span>
- <span data-ttu-id="ff08c-110">Erfahren Sie, wie Sie das Luis-Portal von Azure einrichten.</span><span class="sxs-lookup"><span data-stu-id="ff08c-110">Learn how to set up Azure's LUIS Portal</span></span>
- <span data-ttu-id="ff08c-111">Erfahren Sie, wie Sie Intent, Entitäten und Äußerungen in Azure einrichten.</span><span class="sxs-lookup"><span data-stu-id="ff08c-111">Learn how to set up intent, entities, and utterances on Azure</span></span>

## <a name="instructions"></a><span data-ttu-id="ff08c-112">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="ff08c-112">Instructions</span></span>
1. <span data-ttu-id="ff08c-113">Gestatten Sie dem Computer das Aktivieren von Diktat. wechseln Sie hierzu zu den Windows-Einstellungen, wählen Sie "Datenschutz", "Sprache" und schließlich "& typisieren" aus, und schalten Sie die Sprachdienste ein, und geben Sie Vorschläge ein.</span><span class="sxs-lookup"><span data-stu-id="ff08c-113">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)


2. <span data-ttu-id="ff08c-117">Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an.</span><span class="sxs-lookup"><span data-stu-id="ff08c-117">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="ff08c-118">Wenn Sie angemeldet sind, klicken Sie auf Ressource erstellen, suchen Sie nach "Language Understanding", und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="ff08c-118">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

![Module4Chapter4step2im](images/module4chapter4step2im.PNG)

3. <span data-ttu-id="ff08c-120">Wählen Sie die Schaltfläche erstellen aus, um eine Instanz dieses Dienstanbieter zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ff08c-120">Select the Create button, to create an instance of this service.</span></span> <span data-ttu-id="ff08c-121">Benennen Sie Ihr Projekt mit dem Namen "Speech_SDK_Learning_Module", und wählen Sie "Pay as you go".</span><span class="sxs-lookup"><span data-stu-id="ff08c-121">Name your project “Speech_SDK_Learning_Module” and select “Pay As You Go.”</span></span>

![Module4Chapter4step3aim](images/module4chapter4step3aim.png)

![Module4Chapter4step3bim](images/module4chapter4step3bim.PNG)

4. <span data-ttu-id="ff08c-124">Wählen Sie Ihre Region aus.</span><span class="sxs-lookup"><span data-stu-id="ff08c-124">Select your Region.</span></span>  <span data-ttu-id="ff08c-125">Wählen Sie für dieses Tutorial "(USA) USA, Westen" aus.</span><span class="sxs-lookup"><span data-stu-id="ff08c-125">For the purpose of this tutorial, select "(US) West US."</span></span> <span data-ttu-id="ff08c-126">Wählen Sie dann "F0" für den Tarif aus.</span><span class="sxs-lookup"><span data-stu-id="ff08c-126">Then choose "F0" for the pricing tier.</span></span> <span data-ttu-id="ff08c-127">Klicken Sie jetzt auf "erstellen" (in der unteren linken Ecke), um die Ressource zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="ff08c-127">Now click "create" (located in the bottom left corner) to create the resource.</span></span>

>  <span data-ttu-id="ff08c-128">Hinweis: Wenn Sie auf "erstellen" geklickt haben, müssen Sie warten, bis der Dienst erstellt wird. dieser Vorgang kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="ff08c-128">Note: once you have clicked on "create," you will have to wait for the service to be created, this might take a minute.</span></span>

5. <span data-ttu-id="ff08c-129">Sobald die Ressource erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ff08c-129">A notification will appear in the portal once the Resource is created.</span></span> <span data-ttu-id="ff08c-130">Klicken Sie auf diese Benachrichtigung, und wählen Sie "zu Ressource wechseln" aus.</span><span class="sxs-lookup"><span data-stu-id="ff08c-130">Click on this notification and select "Go to resource."</span></span>

6. <span data-ttu-id="ff08c-131">Navigieren Sie auf der Seite "Schnellstart" Ihres "Luis API"-Dienstanbieter zum ersten Schritt, rufen Sie Ihre "Schlüssel" auf, und klicken Sie auf "Schlüssel" (Sie können dies auch durch Klicken auf den blauen Hyperlink "Keys" erreichen, der in der Abbildung unten dargestellt ist).</span><span class="sxs-lookup"><span data-stu-id="ff08c-131">From the "Quick Start" page of your "LUIS API" service, navigate to the first step, grab your "keys," and click "keys" (you can also achieve this by clicking the blue hyperlink "keys," shown in the image below).</span></span> <span data-ttu-id="ff08c-132">Dadurch wird Ihr Dienst, "Keys", angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ff08c-132">This will reveal your service, "Keys."</span></span> <span data-ttu-id="ff08c-133">Speichern Sie eine Kopie eines der Schlüssel, damit Sie Sie später in der App verwenden können.</span><span class="sxs-lookup"><span data-stu-id="ff08c-133">Save a copy of one of the keys so you can use it later in the app.</span></span>

![Module4Chapter4step6im](images/module4chapter4step6im.PNG)

7. <span data-ttu-id="ff08c-135">Klicken Sie auf der Seite "Schnellstart" im Abschnitt 2B auf "Language Understanding Portal" (in der Abbildung oben gezeigt), um auf die Webseite umgeleitet zu werden, mit der Sie den neuen Dienst in der Luis-Anwendung erstellen.</span><span class="sxs-lookup"><span data-stu-id="ff08c-135">Back in the "Quick Start" page under Section 2b, click on "Language Understanding Portal" (shown in the image above) to be redirected to the webpage which you will use to create your new service, within the LUIS application.</span></span>

> <span data-ttu-id="ff08c-136">Hinweis: Wenn Sie das "Language Understanding-Portal" erreicht haben, müssen Sie sich ggf. nicht mehr mit denselben Anmelde Informationen wie Ihre Azure-Portal anmelden.</span><span class="sxs-lookup"><span data-stu-id="ff08c-136">Note: Upon reaching the "Language Understanding Portal," you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="ff08c-137">Wenn Sie zum ersten Mal Luis verwenden, müssen Sie zum unteren Rand der Willkommensseite Scrollen, um die Schaltfläche "erstellen Sie Luis" zu suchen und darauf zu klicken.</span><span class="sxs-lookup"><span data-stu-id="ff08c-137">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

8. <span data-ttu-id="ff08c-138">Klicken Sie nach der Anmeldung auf "meine apps" (wenn Sie sich derzeit nicht in diesem Abschnitt befinden).</span><span class="sxs-lookup"><span data-stu-id="ff08c-138">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="ff08c-139">Klicken Sie dann auf neue APP erstellen.</span><span class="sxs-lookup"><span data-stu-id="ff08c-139">You can then click on Create new app.</span></span> <span data-ttu-id="ff08c-140">Nennen Sie die neue App "Speech SDK Learning Module".</span><span class="sxs-lookup"><span data-stu-id="ff08c-140">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="ff08c-141">Fügen Sie auch "Speech SDK Learning Module" zum Beschreibungsfeld hinzu.</span><span class="sxs-lookup"><span data-stu-id="ff08c-141">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="ff08c-142">Klicken Sie dann auf "Done".</span><span class="sxs-lookup"><span data-stu-id="ff08c-142">Then click "done."</span></span>

![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

> <span data-ttu-id="ff08c-145">Nebenbei Wenn Ihre APP eine andere Sprache als Englisch verstehen soll, sollten Sie die "Kultur" in die entsprechende Sprache ändern.</span><span class="sxs-lookup"><span data-stu-id="ff08c-145">note: If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

9. <span data-ttu-id="ff08c-146">Klicken Sie oben rechts auf "Build".</span><span class="sxs-lookup"><span data-stu-id="ff08c-146">Click “Build” located in the top right.</span></span>

10. <span data-ttu-id="ff08c-147">Wählen Sie unter APP-Assets auf der linken Seite die Option "Intents" aus, klicken Sie auf "Create New Intent", und nennen Sie Sie "pressbutton".</span><span class="sxs-lookup"><span data-stu-id="ff08c-147">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span> 

![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

> <span data-ttu-id="ff08c-149">Hinweis: Es ist wichtig, die Namen der Intents und Entitäten zu verwenden, die in diesem Tutorial verwendet werden, da die lunarcom-App anhand ihres Namens auf Sie verweist.</span><span class="sxs-lookup"><span data-stu-id="ff08c-149">Note: It is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span> 
>
> <span data-ttu-id="ff08c-150">Hinweis: Sie sollten jetzt über zwei Intents verfügen: "Press Button" und "None".</span><span class="sxs-lookup"><span data-stu-id="ff08c-150">Note: you should now have 2 Intents - “PressButton” and “None."</span></span>

11. <span data-ttu-id="ff08c-151">Wählen Sie unter APP-Ressourcen auf der linken Seite die Option "Entitäten" aus, klicken Sie auf "neue Entität erstellen", und geben Sie Ihr den Namen "action".</span><span class="sxs-lookup"><span data-stu-id="ff08c-151">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

12. <span data-ttu-id="ff08c-153">Klicken Sie erneut auf "neue Entität erstellen", und geben Sie Ihr den Namen "target" und den Entitätstyp ebenfalls als "einfach" an.</span><span class="sxs-lookup"><span data-stu-id="ff08c-153">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

13. <span data-ttu-id="ff08c-155">Wählen Sie unter APP-Assets auf der linken Seite die Option "Intents" aus, und klicken Sie dann auf die Absicht, die Sie in Schritt 10 erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="ff08c-155">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

14. <span data-ttu-id="ff08c-157">Klicken Sie auf das Dropdown Menü "Optionen anzeigen" auf der rechten Seite, und wählen Sie "Entitäts Werte anzeigen" aus.</span><span class="sxs-lookup"><span data-stu-id="ff08c-157">Click on the "View options" dropdown on the right and select "show entity values."</span></span> 

![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)<span data-ttu-id="ff08c-159">Klicken Sie auf das Beispiel "Beispiel eingeben...".</span><span class="sxs-lookup"><span data-stu-id="ff08c-159">Click on the “Enter an example…”</span></span> <span data-ttu-id="ff08c-160">Textfeld.</span><span class="sxs-lookup"><span data-stu-id="ff08c-160">textbox.</span></span> <span data-ttu-id="ff08c-161">Geben Sie dann die folgenden Äußerungen ein:</span><span class="sxs-lookup"><span data-stu-id="ff08c-161">Then, enter the following utterances:</span></span> 

![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

15. <span data-ttu-id="ff08c-163">Klicken Sie auf das Dropdown Menü "Optionen anzeigen" auf der rechten Seite, und wählen Sie "Entitäts Namen anzeigen" aus.</span><span class="sxs-lookup"><span data-stu-id="ff08c-163">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

16. <span data-ttu-id="ff08c-165">Stellen Sie sicher, dass jede der 10 Äußerungen die folgenden Entitäts Bezeichnungen an den folgenden Stellen von 1 hat.) Klicken Sie auf Wörter, die falsch gekennzeichnet sind, und wählen Sie im Popup Fenster die Option "Bezeichnung entfernen" und 2 aus.) Klicken Sie auf Wörter, die mit einer Bezeichnung versehen werden sollen, und wählen Sie im Popup Fenster die entsprechende Bezeichnung aus.</span><span class="sxs-lookup"><span data-stu-id="ff08c-165">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

17. <span data-ttu-id="ff08c-167">Klicken Sie in der oberen rechten Ecke auf "trainieren", um das Modell zu veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="ff08c-167">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="ff08c-168">Nachdem die Verarbeitung abgeschlossen ist, klicken Sie in der oberen rechten Ecke auf "Test".</span><span class="sxs-lookup"><span data-stu-id="ff08c-168">Then, once it has finished processing, click "Test" in the top right.</span></span>

![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

18. <span data-ttu-id="ff08c-170">Geben Sie in das Textfeld "Start Schaltfläche auswählen" ein.</span><span class="sxs-lookup"><span data-stu-id="ff08c-170">Enter in “select the launch button” in  the textbox.</span></span>

> <span data-ttu-id="ff08c-171">Hinweis: Wir haben in unseren Äußerungen nicht "Select" als Aktion hinzugefügt, aber wenn Sie auf "überprüfen" klicken, hat das Modell "Select" als Aktions Entität erkannt.</span><span class="sxs-lookup"><span data-stu-id="ff08c-171">note: we did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
>
> ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

19. <span data-ttu-id="ff08c-173">Klicken Sie jetzt in der oberen rechten Ecke auf "veröffentlichen".</span><span class="sxs-lookup"><span data-stu-id="ff08c-173">Now, click "publish" in the top right.</span></span> <span data-ttu-id="ff08c-174">Stellen Sie sicher, dass in der Dropdown Liste "Produktion" angezeigt wird, und klicken Sie auch im Popup auf "veröffentlichen".</span><span class="sxs-lookup"><span data-stu-id="ff08c-174">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span> 

![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

20. <span data-ttu-id="ff08c-176">Nach der Veröffentlichung sollte am oberen Rand der Seite eine grüne Leiste angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ff08c-176">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="ff08c-177">Klicken Sie auf die grüne Leiste, um zur Seite "verwalten" zu gelangen.</span><span class="sxs-lookup"><span data-stu-id="ff08c-177">Click on the green bar to be taken to the "Manage" page.</span></span> 

![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

21. <span data-ttu-id="ff08c-179">Klicken Sie auf der linken Seite unter "Anwendungseinstellungen" auf "Schlüssel und Endpunkte".</span><span class="sxs-lookup"><span data-stu-id="ff08c-179">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="ff08c-180">Legen Sie dann die Dropdown-Einstellung "veröffentlichen auf" als "Produktion" fest.</span><span class="sxs-lookup"><span data-stu-id="ff08c-180">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="ff08c-181">Legen Sie die Zeitzone entsprechend fest, und aktivieren Sie das Kontrollkästchen, um alle vorhergesagten Intent-Ergebnisse einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="ff08c-181">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="ff08c-182">Klicken Sie abschließend auf "Ressource zuweisen".</span><span class="sxs-lookup"><span data-stu-id="ff08c-182">Lastly, Click on "Assign resource."</span></span>

![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

22. <span data-ttu-id="ff08c-184">Wählen Sie in der ersten Dropdown Liste Mandant aus, und wählen Sie in der Dropdown Liste Abonnement Name den Namen "Pay-as-you-go" aus.</span><span class="sxs-lookup"><span data-stu-id="ff08c-184">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="ff08c-185">Wählen Sie unter Luis Resource Name die zuvor erstellte Ressource in den Schritten 1-5 aus.</span><span class="sxs-lookup"><span data-stu-id="ff08c-185">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="ff08c-186">Klicken Sie dann auf "Ressource zuweisen".</span><span class="sxs-lookup"><span data-stu-id="ff08c-186">Then, click on "Assign resource."</span></span> 

![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

> <span data-ttu-id="ff08c-188">Hinweis: Stellen Sie sicher, dass Sie die Endpunkt-URL, die der soeben zugewiesenen Ressource zugeordnet ist, kopieren und speichern, damit Sie für den nächsten Abschnitt leicht zugänglich ist.</span><span class="sxs-lookup"><span data-stu-id="ff08c-188">Note: Ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>
>
> <span data-ttu-id="ff08c-189">Hinweis: Geben Sie für den Mandanten Namen ihre Corporation oder Ihr Profil ein, das Sie für diese Anwendung erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="ff08c-189">Note: For the Tenant name, put your corporation or profile that you created for this application.</span></span>

23. <span data-ttu-id="ff08c-190">Öffnen Sie nun die neue app in Unity, und wählen Sie das Lunarcom_Base-Objekt in der Hierarchie aus.</span><span class="sxs-lookup"><span data-stu-id="ff08c-190">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="ff08c-191">Klicken Sie im Inspektor-Panel auf "Komponente hinzufügen", suchen Sie nach "lunarcomintenterkenzer", und wählen Sie ihn aus.</span><span class="sxs-lookup"><span data-stu-id="ff08c-191">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

24. <span data-ttu-id="ff08c-193">Geben Sie im Feld für den Luis-Endpunkt der "lunarcomintenterkenzer" im Inspektor-Panel die Endpunkt-URL ein, die Sie in Schritt 22 gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="ff08c-193">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span> 

![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

>  <span data-ttu-id="ff08c-195">Hinweis: Stellen Sie sicher, dass in der Komponente "lunarcomofflinerecognizer" im Inspektor-Panel "deaktivieren" für "simulateofflinemode" ausgewählt ist. andernfalls funktioniert das Testen des Programms nicht.</span><span class="sxs-lookup"><span data-stu-id="ff08c-195">Note: In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span> 

25. <span data-ttu-id="ff08c-196">Klicken Sie im Unity-Editor auf die Wiedergabe Schaltfläche, und klicken Sie auf die Schaltfläche ""</span><span class="sxs-lookup"><span data-stu-id="ff08c-196">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="ff08c-197">Sagen Sie den Ausdruck "starten Sie die Schaltfläche" starten "aus.</span><span class="sxs-lookup"><span data-stu-id="ff08c-197">Utter the phrase “select the launch rocket button.”</span></span>

>  <span data-ttu-id="ff08c-198">Hinweis: Die APP hat die gewünschte Funktion erkannt und die Schaltfläche "Rocket" aktiviert.</span><span class="sxs-lookup"><span data-stu-id="ff08c-198">Note: The app recognized the desired function and activated the rocket button.</span></span>
>
> ![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="ff08c-200">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="ff08c-200">Congratulations</span></span>

<span data-ttu-id="ff08c-201">In dieser Lektion haben wir gelernt, wie Sie Ki-gestützte Sprachbefehle hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="ff08c-201">In this lesson, we learned how to add AI-powered speech commands!</span></span> <span data-ttu-id="ff08c-202">Jetzt kann Ihr Programm die Absicht der Benutzer erkennen, auch wenn Sie keine präzisen Sprachbefehle aussprechen.</span><span class="sxs-lookup"><span data-stu-id="ff08c-202">Now your program can recognize users' intent even if they do not utter precise voice commands.</span></span>

