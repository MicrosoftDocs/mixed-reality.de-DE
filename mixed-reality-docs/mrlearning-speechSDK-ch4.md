---
title: Tutorials zu Azure Speech Services-4. Einrichten von Absicht und natürlicher Sprache
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 9235452d9dce38e9d849821a694a5d4c710d8e87
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913318"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="e002c-105">4. Einrichten der Absicht und der Kenntnisse in natürlicher Sprache</span><span class="sxs-lookup"><span data-stu-id="e002c-105">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="e002c-106">In dieser Lektion erfahren Sie mehr über das Intent-Feature des Azure Speech Service.</span><span class="sxs-lookup"><span data-stu-id="e002c-106">In this lesson, we will explore the Azure Speech Service's Intent feature.</span></span> <span data-ttu-id="e002c-107">Mit der Intent-Funktion können wir unsere Anwendung mit Ki-gestützten Sprachbefehlen ausstatten, bei denen Benutzer nicht spezifische Sprachbefehle sagen können und dennoch vom System verstanden werden können.</span><span class="sxs-lookup"><span data-stu-id="e002c-107">The Intent feature allows us to equip our application with AI-powered voice commands, where users can say non-specific voice commands, and still have their intent understood by the system.</span></span> <span data-ttu-id="e002c-108">In dieser Lektion richten wir unser Azure-Luis-Portal ein, richten unsere Absichten/Entitäten/Äußerungen ein, veröffentlichen unsere Intent-Ressource, verbinden unsere Unity-App mit unserer Intent-Ressource und machen unseren ersten beabsichtigten API-Rückruf.</span><span class="sxs-lookup"><span data-stu-id="e002c-108">During this lesson, we will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

## <a name="objectives"></a><span data-ttu-id="e002c-109">Ziele</span><span class="sxs-lookup"><span data-stu-id="e002c-109">Objectives</span></span>

- <span data-ttu-id="e002c-110">Erfahren Sie, wie Sie in unserer Anwendung das Verständnis von Absicht und natürlicher Sprache einrichten</span><span class="sxs-lookup"><span data-stu-id="e002c-110">Learn how to set up intent and natural language understanding in our application</span></span>
- <span data-ttu-id="e002c-111">Erfahren Sie, wie Sie das Luis-Portal von Azure einrichten.</span><span class="sxs-lookup"><span data-stu-id="e002c-111">Learn how to set up Azure's LUIS Portal</span></span>
- <span data-ttu-id="e002c-112">Erfahren Sie, wie Sie Intent, Entitäten und Äußerungen in Azure einrichten.</span><span class="sxs-lookup"><span data-stu-id="e002c-112">Learn how to set up intent, entities, and utterances on Azure</span></span>

## <a name="instructions"></a><span data-ttu-id="e002c-113">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="e002c-113">Instructions</span></span>

1. <span data-ttu-id="e002c-114">Gestatten Sie dem Computer das Aktivieren von Diktat. wechseln Sie hierzu zu den Windows-Einstellungen, wählen Sie "Datenschutz", "Sprache" und schließlich "& typisieren" aus, und schalten Sie die Sprachdienste ein, und geben Sie Vorschläge ein.</span><span class="sxs-lookup"><span data-stu-id="e002c-114">Allow your machine to enable Dictation, to do this, go to Windows Settings, select "privacy," then "speech," and finally "inking & typing" and turn on speech services and typing suggestions.</span></span>

    ![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

    ![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

    ![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

2. <span data-ttu-id="e002c-118">Melden Sie sich beim [Azure-Portal](https://portal.azure.com/)an.</span><span class="sxs-lookup"><span data-stu-id="e002c-118">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="e002c-119">Wenn Sie angemeldet sind, klicken Sie auf Ressource erstellen, suchen Sie nach "Language Understanding", und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="e002c-119">Once you are logged in, click on Create a resource, and search for "Language Understanding," and click enter.</span></span>

    ![mrlearning-Speech-CH4-1-step2. png](images/mrlearning-speech-ch4-1-step2.png)

3. <span data-ttu-id="e002c-121">Klicken Sie auf die Schaltfläche **Erstellen** , um eine Instanz dieses Dienstanbieter zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e002c-121">Click the **Create** button to create an instance of this service.</span></span>

    ![mrlearning-Speech-CH4-1-step3a. png](images/mrlearning-speech-ch4-1-step3a.png)

    <span data-ttu-id="e002c-123">Geben Sie der Ressource einen **Namen**, z. b. " *Speech-SDK-Learning-Module*".</span><span class="sxs-lookup"><span data-stu-id="e002c-123">Give your resource a **Name**, for example, *Speech-SDK-Learning-Module*.</span></span> <span data-ttu-id="e002c-124">Wählen Sie für **Abonnement**die Option *Pay as you go* oder *Free Trail* aus, wenn Sie über ein Testkonto verfügen.</span><span class="sxs-lookup"><span data-stu-id="e002c-124">For **Subscription**, select *Pay As You Go* or *Free Trail* if you have a trial account.</span></span> <span data-ttu-id="e002c-125">Erstellen Sie als nächstes eine neue **Ressourcengruppe** , indem Sie auf den Link **neu erstellen** klicken. Geben Sie einen Namen ein, z. b. *hololens-2-Tutorials-Resource-Group*, und klicken Sie auf die Schaltfläche **OK** .</span><span class="sxs-lookup"><span data-stu-id="e002c-125">Next, create a new **Resource Group** by clicking the **Create new** link, enter a name, for example, *HoloLens-2-Tutorials-Resource-Group*, and clicking the **OK** button.</span></span>

    ![mrlearning-Speech-CH4-1-step3b. png](images/mrlearning-speech-ch4-1-step3b.png)

4. <span data-ttu-id="e002c-127">Wählen Sie den **Speicherort** für die Erstellung und den **Lauf Zeit Speicherort**aus. verwenden Sie für dieses Tutorial *(USA)* USA, Westen.</span><span class="sxs-lookup"><span data-stu-id="e002c-127">Select your **Authoring location** and **Runtime location**, for the purpose of this tutorial, use *(US) West US*.</span></span> <span data-ttu-id="e002c-128">Wählen Sie dann " *F0 (5 Anrufe pro Sekunde, 10K Anrufe pro Monat)* " **für den** Erstellungs Tarif und den **Lauf**Zeit Tarif aus.</span><span class="sxs-lookup"><span data-stu-id="e002c-128">Then choose *F0 (5 Calls per second, 10K Calls per month)* for the **Authoring pricing tier** and **Runtime pricing tier**.</span></span> <span data-ttu-id="e002c-129">Klicken Sie abschließend auf die Schaltfläche **Erstellen** , um die Ressource und die neue Ressourcengruppe zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e002c-129">Finally, click the **Create** button to create the resource as well as the new resource group.</span></span>

    ![mrlearning-Speech-CH4-1-step4. png](images/mrlearning-speech-ch4-1-step4.png)

    >[!NOTE]
    ><span data-ttu-id="e002c-131">Nachdem Sie auf die Schaltfläche erstellen geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="e002c-131">After you click the Create button you will have to wait for the service to be created, this might take a few minute.</span></span>

5. <span data-ttu-id="e002c-132">Nachdem der Vorgang zur Ressourcen Erstellung fertiggestellt wurde, wird die Meldung **Ihre Bereitstellung ist beendet**angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e002c-132">Once the resource creation process is complete, you will see the message **Your deployment is complete**.</span></span>

    ![mrlearning-Speech-CH4-1-step5. png](images/mrlearning-speech-ch4-1-step5.png)

6. <span data-ttu-id="e002c-134">Melden Sie sich mit demselben Benutzerkonto beim [Language Understanding Intelligent Service (Luis)](https://www.luis.ai/) -Portal an, wählen Sie Ihr Land aus, und stimmen Sie den Nutzungsbedingungen zu.</span><span class="sxs-lookup"><span data-stu-id="e002c-134">Using the same user account, sign in to the [Language Understanding Intelligent Service (LUIS)](https://www.luis.ai/) portal, select your country, and agree to the terms of use.</span></span>

    >[!NOTE]
    ><span data-ttu-id="e002c-135">Wenn Sie das Language Understanding-Portal erreicht haben, müssen Sie sich ggf. mit denselben Anmelde Informationen wie Ihre Azure-Portal anmelden, falls Sie dies noch nicht getan haben.</span><span class="sxs-lookup"><span data-stu-id="e002c-135">Upon reaching the Language Understanding portal, you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="e002c-136">Wenn Sie zum ersten Mal Luis verwenden, müssen Sie zum unteren Rand der Willkommensseite Scrollen, um die Schaltfläche "erstellen Sie Luis" zu suchen und darauf zu klicken.</span><span class="sxs-lookup"><span data-stu-id="e002c-136">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the "Create LUIS" app button.</span></span>

7. <span data-ttu-id="e002c-137">Klicken Sie nach der Anmeldung auf "meine apps" (wenn Sie sich derzeit nicht in diesem Abschnitt befinden).</span><span class="sxs-lookup"><span data-stu-id="e002c-137">Once logged in, click My Apps (if you are not in that section currently).</span></span> <span data-ttu-id="e002c-138">Klicken Sie dann auf neue APP erstellen.</span><span class="sxs-lookup"><span data-stu-id="e002c-138">You can then click on Create new app.</span></span> <span data-ttu-id="e002c-139">Nennen Sie die neue App "Speech SDK Learning Module".</span><span class="sxs-lookup"><span data-stu-id="e002c-139">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="e002c-140">Fügen Sie auch "Speech SDK Learning Module" zum Beschreibungsfeld hinzu.</span><span class="sxs-lookup"><span data-stu-id="e002c-140">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="e002c-141">Klicken Sie dann auf "Done".</span><span class="sxs-lookup"><span data-stu-id="e002c-141">Then click "done."</span></span>

    ![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

    ![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

    >[!NOTE]
    ><span data-ttu-id="e002c-144">Wenn Ihre APP eine andere Sprache als Englisch verstehen soll, sollten Sie die "Kultur" in die entsprechende Sprache ändern.</span><span class="sxs-lookup"><span data-stu-id="e002c-144">If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

8. <span data-ttu-id="e002c-145">Klicken Sie oben rechts auf "Build".</span><span class="sxs-lookup"><span data-stu-id="e002c-145">Click “Build” located in the top right.</span></span>

9. <span data-ttu-id="e002c-146">Wählen Sie unter APP-Assets auf der linken Seite die Option "Intents" aus, klicken Sie auf "Create New Intent", und nennen Sie Sie "pressbutton".</span><span class="sxs-lookup"><span data-stu-id="e002c-146">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span>

    ![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

    >[!NOTE]
    ><span data-ttu-id="e002c-148">Es ist wichtig, die Namen der Intents und Entitäten zu verwenden, die in diesem Tutorial verwendet werden, da die lunarcom-App anhand ihres Namens auf Sie verweist.</span><span class="sxs-lookup"><span data-stu-id="e002c-148">It is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span>

    >[!NOTE]
    ><span data-ttu-id="e002c-149">Sie sollten jetzt über zwei Intents verfügen: "Press Button" und "None".</span><span class="sxs-lookup"><span data-stu-id="e002c-149">You should now have 2 Intents - “PressButton” and “None."</span></span>

10. <span data-ttu-id="e002c-150">Wählen Sie unter APP-Ressourcen auf der linken Seite die Option "Entitäten" aus, klicken Sie auf "neue Entität erstellen", und geben Sie Ihr den Namen "action".</span><span class="sxs-lookup"><span data-stu-id="e002c-150">Under App Assets on the left, select “Entities” and click “Create New Entity” and name it “Action” and keep the Entity Type as “Simple.”</span></span>

    ![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

11. <span data-ttu-id="e002c-152">Klicken Sie erneut auf "neue Entität erstellen", und geben Sie Ihr den Namen "target" und den Entitätstyp ebenfalls als "einfach" an.</span><span class="sxs-lookup"><span data-stu-id="e002c-152">Click “Create New Entity” again and name it “Target” and keep the Entity Type as “Simple” as well.</span></span>

    ![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

12. <span data-ttu-id="e002c-154">Wählen Sie unter APP-Assets auf der linken Seite die Option "Intents" aus, und klicken Sie dann auf die Absicht, die Sie in Schritt 10 erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="e002c-154">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

    ![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

13. <span data-ttu-id="e002c-156">Klicken Sie auf das Dropdown Menü "Optionen anzeigen" auf der rechten Seite, und wählen Sie "Entitäts Werte anzeigen" aus.</span><span class="sxs-lookup"><span data-stu-id="e002c-156">Click on the "View options" dropdown on the right and select "show entity values."</span></span>

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)

    <span data-ttu-id="e002c-158">Klicken Sie auf das Beispiel "Beispiel eingeben...".</span><span class="sxs-lookup"><span data-stu-id="e002c-158">Click on the “Enter an example…”</span></span> <span data-ttu-id="e002c-159">Textfeld.</span><span class="sxs-lookup"><span data-stu-id="e002c-159">textbox.</span></span> <span data-ttu-id="e002c-160">Geben Sie dann die folgenden Äußerungen ein:</span><span class="sxs-lookup"><span data-stu-id="e002c-160">Then, enter the following utterances:</span></span>

    ![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

14. <span data-ttu-id="e002c-162">Klicken Sie auf das Dropdown Menü "Optionen anzeigen" auf der rechten Seite, und wählen Sie "Entitäts Namen anzeigen" aus.</span><span class="sxs-lookup"><span data-stu-id="e002c-162">Click on the "View options" dropdown on the right and select "Show entity names."</span></span>

    ![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

15. <span data-ttu-id="e002c-164">Stellen Sie sicher, dass jede der 10 Äußerungen die folgenden Entitäts Bezeichnungen an den folgenden Stellen von 1 hat.) Klicken Sie auf Wörter, die falsch gekennzeichnet sind, und wählen Sie im Popup Fenster die Option "Bezeichnung entfernen" und 2 aus.) Klicken Sie auf Wörter, die mit einer Bezeichnung versehen werden sollen, und wählen Sie im Popup Fenster die entsprechende Bezeichnung aus.</span><span class="sxs-lookup"><span data-stu-id="e002c-164">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

    ![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

16. <span data-ttu-id="e002c-166">Klicken Sie in der oberen rechten Ecke auf "trainieren", um das Modell zu veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="e002c-166">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="e002c-167">Nachdem die Verarbeitung abgeschlossen ist, klicken Sie in der oberen rechten Ecke auf "Test".</span><span class="sxs-lookup"><span data-stu-id="e002c-167">Then, once it has finished processing, click "Test" in the top right.</span></span>

    ![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

17. <span data-ttu-id="e002c-169">Geben Sie in das Textfeld "Start Schaltfläche auswählen" ein.</span><span class="sxs-lookup"><span data-stu-id="e002c-169">Enter in “select the launch button” in  the textbox.</span></span>

    >[!NOTE]
    ><span data-ttu-id="e002c-170">Wir haben in unseren Äußerungen nicht "Select" als Aktion hinzugefügt, aber wenn Sie auf "überprüfen" klicken, hat das Modell "Select" als Aktions Entität erkannt.</span><span class="sxs-lookup"><span data-stu-id="e002c-170">We did not add “select” as an action in any of our Utterances - but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
    >
    > ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

18. <span data-ttu-id="e002c-172">Klicken Sie jetzt in der oberen rechten Ecke auf "veröffentlichen".</span><span class="sxs-lookup"><span data-stu-id="e002c-172">Now, click "publish" in the top right.</span></span> <span data-ttu-id="e002c-173">Stellen Sie sicher, dass in der Dropdown Liste "Produktion" angezeigt wird, und klicken Sie auch im Popup auf "veröffentlichen".</span><span class="sxs-lookup"><span data-stu-id="e002c-173">Ensure the dropdown says “Production” and click "publish" on the popup as well.</span></span>

    ![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

19. <span data-ttu-id="e002c-175">Nach der Veröffentlichung sollte am oberen Rand der Seite eine grüne Leiste angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e002c-175">Once published, a green bar should appear at the top of the page.</span></span>  <span data-ttu-id="e002c-176">Klicken Sie auf die grüne Leiste, um zur Seite "verwalten" zu gelangen.</span><span class="sxs-lookup"><span data-stu-id="e002c-176">Click on the green bar to be taken to the "Manage" page.</span></span>

    ![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

20. <span data-ttu-id="e002c-178">Klicken Sie auf der linken Seite unter "Anwendungseinstellungen" auf "Schlüssel und Endpunkte".</span><span class="sxs-lookup"><span data-stu-id="e002c-178">Click on "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="e002c-179">Legen Sie dann die Dropdown-Einstellung "veröffentlichen auf" als "Produktion" fest.</span><span class="sxs-lookup"><span data-stu-id="e002c-179">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="e002c-180">Legen Sie die Zeitzone entsprechend fest, und aktivieren Sie das Kontrollkästchen, um alle vorhergesagten Intent-Ergebnisse einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="e002c-180">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="e002c-181">Klicken Sie abschließend auf "Ressource zuweisen".</span><span class="sxs-lookup"><span data-stu-id="e002c-181">Lastly, Click on "Assign resource."</span></span>

    ![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

21. <span data-ttu-id="e002c-183">Wählen Sie in der ersten Dropdown Liste Mandant aus, und wählen Sie in der Dropdown Liste Abonnement Name den Namen "Pay-as-you-go" aus.</span><span class="sxs-lookup"><span data-stu-id="e002c-183">Select tenant from the first dropdown, and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="e002c-184">Wählen Sie unter Luis Resource Name die zuvor erstellte Ressource in den Schritten 1-5 aus.</span><span class="sxs-lookup"><span data-stu-id="e002c-184">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="e002c-185">Klicken Sie dann auf "Ressource zuweisen".</span><span class="sxs-lookup"><span data-stu-id="e002c-185">Then, click on "Assign resource."</span></span>

    ![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

    >[!NOTE]
    ><span data-ttu-id="e002c-187">Stellen Sie sicher, dass Sie die Endpunkt-URL, die der soeben zugewiesenen Ressource zugeordnet ist, kopieren und speichern, damit Sie für den nächsten Abschnitt leicht zugänglich ist.</span><span class="sxs-lookup"><span data-stu-id="e002c-187">Ensure to copy and save the Endpoint URL associated with the resource we just assigned so that it is easily accessible for the next section.</span></span>

    >[!NOTE]
    ><span data-ttu-id="e002c-188">Geben Sie für den Mandanten Namen ihre Corporation oder Ihr Profil ein, das Sie für diese Anwendung erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="e002c-188">For the Tenant name, put your corporation or profile that you created for this application.</span></span>

22. <span data-ttu-id="e002c-189">Öffnen Sie nun die neue app in Unity, und wählen Sie das Lunarcom_Base-Objekt in der Hierarchie aus.</span><span class="sxs-lookup"><span data-stu-id="e002c-189">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="e002c-190">Klicken Sie im Inspektor-Panel auf "Komponente hinzufügen", suchen Sie nach "lunarcomintenterkenzer", und wählen Sie ihn aus.</span><span class="sxs-lookup"><span data-stu-id="e002c-190">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

    ![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

23. <span data-ttu-id="e002c-192">Geben Sie im Feld für den Luis-Endpunkt der "lunarcomintenterkenzer" im Inspektor-Panel die Endpunkt-URL ein, die Sie in Schritt 22 gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="e002c-192">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span>

    ![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

    >[!NOTE]
    ><span data-ttu-id="e002c-194">Stellen Sie sicher, dass in der Komponente "lunarcomofflinerecognizer" im Inspektor-Panel "deaktivieren" für "simulateofflinemode" ausgewählt ist. andernfalls funktioniert das Testen des Programms nicht.</span><span class="sxs-lookup"><span data-stu-id="e002c-194">In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span>

24. <span data-ttu-id="e002c-195">Klicken Sie im Unity-Editor auf die Wiedergabe Schaltfläche, und klicken Sie auf die Schaltfläche ""</span><span class="sxs-lookup"><span data-stu-id="e002c-195">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="e002c-196">Sagen Sie den Ausdruck "starten Sie die Schaltfläche" starten "aus.</span><span class="sxs-lookup"><span data-stu-id="e002c-196">Utter the phrase “select the launch rocket button.”</span></span>

    >[!NOTE]
    ><span data-ttu-id="e002c-197">Die APP hat die gewünschte Funktion erkannt und die Schaltfläche "Rocket" aktiviert.</span><span class="sxs-lookup"><span data-stu-id="e002c-197">The app recognized the desired function and activated the rocket button.</span></span>
    >
    >![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="e002c-199">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="e002c-199">Congratulations</span></span>

<span data-ttu-id="e002c-200">In dieser Lektion haben wir gelernt, wie Sie Ki-gestützte Sprachbefehle hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="e002c-200">In this lesson, we learned how to add AI-powered speech commands!</span></span> <span data-ttu-id="e002c-201">Jetzt kann Ihr Programm die Absicht der Benutzer erkennen, auch wenn Sie keine präzisen Sprachbefehle aussprechen.</span><span class="sxs-lookup"><span data-stu-id="e002c-201">Now your program can recognize users' intent even if they do not utter precise voice commands.</span></span>
