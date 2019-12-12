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
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="13971-105">4. Einrichten der Absicht und der Kenntnisse in natürlicher Sprache</span><span class="sxs-lookup"><span data-stu-id="13971-105">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="13971-106">In dieser Lektion erfahren Sie mehr über das Intent-Feature des Azure Speech Service.</span><span class="sxs-lookup"><span data-stu-id="13971-106">In this lesson, you will explore the Azure Speech Service's Intent feature.</span></span> <span data-ttu-id="13971-107">Das Intent-Feature ermöglicht es Ihnen, unsere Anwendung mit Ki-gestützten Sprachbefehlen auszustatten, bei denen Benutzer nicht spezifische Sprachbefehle sagen können und dennoch vom System verstanden werden können.</span><span class="sxs-lookup"><span data-stu-id="13971-107">The Intent feature allows you to equip our application with AI-powered voice commands, where users can say non-specific voice commands and still have their intent understood by the system.</span></span> <span data-ttu-id="13971-108">In dieser Lektion richten wir unser Azure-Luis-Portal ein, richten unsere Absichten/Entitäten/Äußerungen ein, veröffentlichen unsere Intent-Ressource, verbinden unsere Unity-App mit unserer Intent-Ressource und machen unseren ersten beabsichtigten API-Rückruf.</span><span class="sxs-lookup"><span data-stu-id="13971-108">During this lesson, we will set up our Azure LUIS Portal, setup our Intent/Entities/Utterances, publish our Intent Resource, connect our Unity app to our Intent Resource, and make our first Intent API call.</span></span>

## <a name="objectives"></a><span data-ttu-id="13971-109">Ziele</span><span class="sxs-lookup"><span data-stu-id="13971-109">Objectives</span></span>

- <span data-ttu-id="13971-110">Erfahren Sie, wie Sie in unserer Anwendung das Verständnis von Absicht und natürlicher Sprache einrichten</span><span class="sxs-lookup"><span data-stu-id="13971-110">Learn how to set up intent and natural language understanding in our application</span></span>
- <span data-ttu-id="13971-111">Erfahren Sie, wie Sie das Luis-Portal von Azure einrichten.</span><span class="sxs-lookup"><span data-stu-id="13971-111">Learn how to set up Azure's LUIS Portal</span></span>
- <span data-ttu-id="13971-112">Erfahren Sie, wie Sie Intent, Entitäten und Äußerungen in Azure einrichten.</span><span class="sxs-lookup"><span data-stu-id="13971-112">Learn how to set up intent, entities, and utterances on Azure</span></span>

## <a name="instructions"></a><span data-ttu-id="13971-113">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="13971-113">Instructions</span></span>

1. <span data-ttu-id="13971-114">Ermöglicht dem Computer das Aktivieren von Diktat.</span><span class="sxs-lookup"><span data-stu-id="13971-114">Allow your machine to enable Dictation.</span></span> <span data-ttu-id="13971-115">Wechseln Sie zu diesem Zweck zu Windows-Einstellungen, wählen Sie "Datenschutz", dann "Sprache" und anschließend "Inking & typisieren" aus, und aktivieren Sie Sprachdienste, und geben Sie Vorschläge ein.</span><span class="sxs-lookup"><span data-stu-id="13971-115">To do this, go to Windows Settings, select "privacy," then "speech," followed by "inking & typing" and turn on speech services and typing suggestions.</span></span>

    ![Module4Chapter4step1aim](images/module4chapter4step1aim.PNG)

    ![Module4Chapter4step1bim](images/module4chapter4step1bim.PNG)

    ![Module4Chapter4step1cim](images/module4chapter4step1cim.PNG)

2. <span data-ttu-id="13971-119">Melden Sie sich beim [Azure-Portal](https://portal.azure.com/) an.</span><span class="sxs-lookup"><span data-stu-id="13971-119">Log in to the [Azure Portal](https://portal.azure.com/).</span></span> <span data-ttu-id="13971-120">Wenn Sie angemeldet sind, klicken Sie auf Ressource erstellen, suchen Sie nach "Language Understanding", und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="13971-120">Once you are logged in, click on Create a resource, search for "Language Understanding" and click Enter.</span></span>

    ![mrlearning-Speech-CH4-1-step2. png](images/mrlearning-speech-ch4-1-step2.png)

3. <span data-ttu-id="13971-122">Klicken Sie auf die Schaltfläche **Erstellen** , um eine Instanz dieses Dienstanbieter zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="13971-122">Click the **Create** button to create an instance of this service.</span></span>

    ![mrlearning-Speech-CH4-1-step3a. png](images/mrlearning-speech-ch4-1-step3a.png)

    <span data-ttu-id="13971-124">Geben Sie der Ressource einen **Namen**, z. b. " *Speech-SDK-Learning-Module*".</span><span class="sxs-lookup"><span data-stu-id="13971-124">Give your resource a **Name**, for example, *Speech-SDK-Learning-Module*.</span></span> <span data-ttu-id="13971-125">Wählen Sie für **Abonnement**die Option *Pay as you go* oder *Free Trail* aus, wenn Sie über ein Testkonto verfügen.</span><span class="sxs-lookup"><span data-stu-id="13971-125">For **Subscription**, select *Pay As You Go* or *Free Trail* if you have a trial account.</span></span> <span data-ttu-id="13971-126">Erstellen Sie als nächstes eine neue **Ressourcengruppe** , indem Sie auf den Link **neu erstellen** klicken, geben Sie einen Namen ein, z. b. *hololens-2-Tutorials-Resource-Group*, und klicken Sie auf die Schaltfläche **OK** .</span><span class="sxs-lookup"><span data-stu-id="13971-126">Next, create a new **Resource Group** by clicking the **Create new** link, enter a name, for example, *HoloLens-2-Tutorials-Resource-Group*, and click the **OK** button.</span></span>

    ![mrlearning-Speech-CH4-1-step3b. png](images/mrlearning-speech-ch4-1-step3b.png)

4. <span data-ttu-id="13971-128">Wählen Sie den **Speicherort der Erstellung** und den **Speicherort**der</span><span class="sxs-lookup"><span data-stu-id="13971-128">Select your **Authoring location** and **Runtime location**.</span></span> <span data-ttu-id="13971-129">Verwenden Sie für dieses Lernprogramm *(USA) USA, Westen*, und wählen Sie dann *F0 (5 Anrufe pro Sekunde, 10K Anrufe pro Monat)* für **den Erstellungs** Tarif und den **Lauf**Zeit Tarif aus.</span><span class="sxs-lookup"><span data-stu-id="13971-129">For the purpose of this tutorial, use *(US) West US*, then choose *F0 (5 Calls per second, 10K Calls per month)* for the **Authoring pricing tier** and **Runtime pricing tier**.</span></span> <span data-ttu-id="13971-130">Klicken Sie abschließend auf die Schaltfläche **Erstellen** , um die Ressource zu erstellen, sowie die neue Ressourcengruppe.</span><span class="sxs-lookup"><span data-stu-id="13971-130">Finally, click the **Create** button to create the resource, as well as the new resource group.</span></span>

    ![mrlearning-Speech-CH4-1-step4. png](images/mrlearning-speech-ch4-1-step4.png)

    >[!NOTE]
    ><span data-ttu-id="13971-132">Nachdem Sie auf die Schaltfläche "erstellen" geklickt haben, müssen Sie warten, bis der Dienst erstellt wird. dieser Vorgang kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="13971-132">After you click the Create button, you will have to wait for the service to be created, which might take a few minutes.</span></span>

5. <span data-ttu-id="13971-133">Nachdem der Vorgang zur Ressourcen Erstellung fertiggestellt wurde, wird die Meldung **Ihre Bereitstellung ist beendet**angezeigt.</span><span class="sxs-lookup"><span data-stu-id="13971-133">Once the resource creation process is complete, you will see the message **Your deployment is complete**.</span></span>

    ![mrlearning-Speech-CH4-1-step5. png](images/mrlearning-speech-ch4-1-step5.png)

6. <span data-ttu-id="13971-135">Melden Sie sich mit demselben Benutzerkonto beim [Language Understanding Intelligent Service (Luis)](https://www.luis.ai/) -Portal an, wählen Sie Ihr Land aus, und stimmen Sie den Nutzungsbedingungen zu.</span><span class="sxs-lookup"><span data-stu-id="13971-135">Using the same user account, sign in to the [Language Understanding Intelligent Service (LUIS)](https://www.luis.ai/) portal, select your country, and agree to the terms of use.</span></span>

    >[!NOTE]
    ><span data-ttu-id="13971-136">Wenn Sie das Language Understanding-Portal erreicht haben, müssen Sie sich ggf. mit denselben Anmelde Informationen wie Ihre Azure-Portal anmelden, falls Sie dies noch nicht getan haben.</span><span class="sxs-lookup"><span data-stu-id="13971-136">Upon reaching the Language Understanding portal, you may need to log in, if you are not already, with the same credentials as your Azure portal.</span></span> <span data-ttu-id="13971-137">Wenn Sie zum ersten Mal Luis verwenden, müssen Sie einen Bildlauf zum unteren Rand der Willkommensseite durchführen, um auf die Schaltfläche "Erstellen einer Luis-app" zu klicken.</span><span class="sxs-lookup"><span data-stu-id="13971-137">If this is your first time using LUIS, you will need to scroll down to the bottom of the Welcome page to find and click the "Create LUIS" app button.</span></span>

7. <span data-ttu-id="13971-138">Klicken Sie nach der Anmeldung auf "meine apps" (wenn Sie sich derzeit nicht in diesem Abschnitt befinden).</span><span class="sxs-lookup"><span data-stu-id="13971-138">Once logged in, click My Apps (if you are not currently in that section).</span></span> <span data-ttu-id="13971-139">Klicken Sie dann auf neue APP erstellen.</span><span class="sxs-lookup"><span data-stu-id="13971-139">You can then click on Create new app.</span></span> <span data-ttu-id="13971-140">Nennen Sie die neue App "Speech SDK Learning Module".</span><span class="sxs-lookup"><span data-stu-id="13971-140">Name the new app “Speech SDK Learning Module.”</span></span> <span data-ttu-id="13971-141">Fügen Sie auch "Speech SDK Learning Module" zum Beschreibungsfeld hinzu.</span><span class="sxs-lookup"><span data-stu-id="13971-141">Add “Speech SDK Learning Module" to the description field, as well.</span></span> <span data-ttu-id="13971-142">Klicken Sie dann auf "Done".</span><span class="sxs-lookup"><span data-stu-id="13971-142">Then click "done."</span></span>

    ![Module4Chapter4step8aim](images/module4chapter4step8aim.PNG)

    ![Module4Chapter4step8bim](images/module4chapter4step8bim.PNG)

    >[!NOTE]
    ><span data-ttu-id="13971-145">Wenn Ihre APP eine andere Sprache als Englisch verstehen soll, sollten Sie die "Kultur" in die entsprechende Sprache ändern.</span><span class="sxs-lookup"><span data-stu-id="13971-145">If your app is supposed to understand a language different from English, you should change the "Culture" to the appropriate language.</span></span>

8. <span data-ttu-id="13971-146">Klicken Sie oben rechts auf "Build".</span><span class="sxs-lookup"><span data-stu-id="13971-146">Click “Build” located in the top right.</span></span>

9. <span data-ttu-id="13971-147">Wählen Sie unter APP-Assets auf der linken Seite die Option "Intents" aus, klicken Sie auf "Create New Intent", und nennen Sie Sie "pressbutton".</span><span class="sxs-lookup"><span data-stu-id="13971-147">Under App Assets on the left, select “Intents” then click “Create New Intent” and name it “PressButton.”</span></span>

    ![Module4Chapter4step10im](images/module4chapter4step10im.PNG)

    >[!NOTE]
    ><span data-ttu-id="13971-149">Es ist wichtig, die Namen der Intents und Entitäten zu verwenden, die in diesem Tutorial verwendet werden, da die lunarcom-App anhand ihres Namens auf Sie verweist.</span><span class="sxs-lookup"><span data-stu-id="13971-149">It is important to use the names of Intents and Entities used in this tutorial because the Lunarcom app will be referencing them by name.</span></span>

    >[!NOTE]
    ><span data-ttu-id="13971-150">Sie sollten jetzt über zwei Intents verfügen: "Press Button" und "None".</span><span class="sxs-lookup"><span data-stu-id="13971-150">You should now have 2 Intents - “PressButton” and “None."</span></span>

10. <span data-ttu-id="13971-151">Wählen Sie unter APP-Assets auf der linken Seite die Option Entitäten aus, klicken Sie auf "neue Entität erstellen", benennen Sie Sie "action", und behalten Sie den Entitätstyp "Simple" bei.</span><span class="sxs-lookup"><span data-stu-id="13971-151">Under App Assets on the left, select “Entities”, click “Create New Entity”, name it “Action” and keep the Entity Type as “Simple.”</span></span>

    ![Module4Chapter4step11im](images/module4chapter4step11im.PNG)

11. <span data-ttu-id="13971-153">Klicken Sie erneut auf "neue Entität erstellen", und nennen Sie Sie "target".</span><span class="sxs-lookup"><span data-stu-id="13971-153">Click “Create New Entity” again and name it “Target”.</span></span> <span data-ttu-id="13971-154">Behalten Sie auch den Entitätstyp "Simple" bei.</span><span class="sxs-lookup"><span data-stu-id="13971-154">Keep the Entity Type as “Simple”, as well.</span></span>

    ![Module4Chapter4step12im](images/module4chapter4step12im.PNG)

12. <span data-ttu-id="13971-156">Wählen Sie unter APP-Assets auf der linken Seite die Option "Intents" aus, und klicken Sie dann auf die Absicht, die Sie in Schritt 10 erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="13971-156">Under App Assets on the left, select "Intents" then click on your "PressButton" Intent that you created in step 10.</span></span>

    ![Module4Chapter4step13im](images/module4chapter4step13im.PNG)

13. <span data-ttu-id="13971-158">Klicken Sie auf das Dropdown Menü "Optionen anzeigen" auf der rechten Seite, und wählen Sie "Entitäts Werte anzeigen" aus.</span><span class="sxs-lookup"><span data-stu-id="13971-158">Click the "View options" dropdown on the right and select "show entity values."</span></span>

    ![Module4Chapter4step14aim](images/module4chapter4step14aim.PNG)

    <span data-ttu-id="13971-160">Klicken Sie auf das Beispiel "Beispiel eingeben...".</span><span class="sxs-lookup"><span data-stu-id="13971-160">Click the “Enter an example…”</span></span> <span data-ttu-id="13971-161">ein.</span><span class="sxs-lookup"><span data-stu-id="13971-161">textbox.</span></span> <span data-ttu-id="13971-162">Geben Sie dann die folgenden Äußerungen ein:</span><span class="sxs-lookup"><span data-stu-id="13971-162">Then, enter the following utterances:</span></span>

    ![Module4Chapter4step14bim](images/module4chapter4step14bim.PNG)

14. <span data-ttu-id="13971-164">Klicken Sie auf das Dropdown Menü "Optionen anzeigen" auf der rechten Seite, und wählen Sie "Entitäts Namen anzeigen" aus.</span><span class="sxs-lookup"><span data-stu-id="13971-164">Click the "View options" dropdown on the right and select "Show entity names."</span></span>

    ![Module4Chapter4step15im](images/module4chapter4step15im.PNG)

15. <span data-ttu-id="13971-166">Stellen Sie sicher, dass jede der 10 Äußerungen die folgenden Entitäts Bezeichnungen an den folgenden Stellen von 1 hat.) Klicken Sie auf Wörter, die falsch gekennzeichnet sind, und wählen Sie im Popup Fenster die Option "Bezeichnung entfernen" und 2 aus.) Klicken Sie auf Wörter, die mit einer Bezeichnung versehen werden sollen, und wählen Sie im Popup Fenster die entsprechende Bezeichnung aus.</span><span class="sxs-lookup"><span data-stu-id="13971-166">Ensure that each of the 10 Utterances have the following Entity labels in the following places by 1.) clicking on words that are mislabeled and, in the popup, selecting "remove label" and 2.) clicking on words that should be labeled and, in the popup, selecting the appropriate label.</span></span>

    ![Module4Chapter4step16im](images/module4chapter4step16im.PNG)

16. <span data-ttu-id="13971-168">Klicken Sie in der oberen rechten Ecke auf "trainieren", um das Modell zu veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="13971-168">Now, to publish the model, click "Train" in the top right.</span></span> <span data-ttu-id="13971-169">Nachdem die Verarbeitung abgeschlossen ist, klicken Sie in der oberen rechten Ecke auf "Test".</span><span class="sxs-lookup"><span data-stu-id="13971-169">Then, once it has finished processing, click "Test" in the top right.</span></span>

    ![Module4Chapter4step17im](images/module4chapter4step17im.PNG)

17. <span data-ttu-id="13971-171">Geben Sie in das Textfeld "Start Schaltfläche auswählen" ein.</span><span class="sxs-lookup"><span data-stu-id="13971-171">Enter in “select the launch button” in  the textbox.</span></span>

    >[!NOTE]
    ><span data-ttu-id="13971-172">Wir haben in unseren Äußerungen nicht "Select" als Aktion hinzugefügt, aber wenn Sie auf "überprüfen" klicken, hat das Modell "Select" als Aktions Entität erkannt.</span><span class="sxs-lookup"><span data-stu-id="13971-172">We did not add “select” as an action in any of our Utterances, but if you click on “Inspect,” the model recognized “select” as an action entity.</span></span>
    >
    > ![Module4Chapter4noteim](images/module4chapter4noteim.PNG)

18. <span data-ttu-id="13971-174">Klicken Sie oben rechts auf "veröffentlichen".</span><span class="sxs-lookup"><span data-stu-id="13971-174">Click "publish" in the top right.</span></span> <span data-ttu-id="13971-175">Stellen Sie sicher, dass in der Dropdown Liste "Produktion" angezeigt wird, und klicken Sie im Popup Fenster auf "veröffentlichen".</span><span class="sxs-lookup"><span data-stu-id="13971-175">Ensure the dropdown says “Production” and click "publish" on the popup, as well.</span></span>

    ![Module4Chapter4step19im](images/module4chapter4step19im.PNG)

19. <span data-ttu-id="13971-177">Nach der Veröffentlichung sollte am oberen Rand der Seite eine grüne Leiste angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="13971-177">Once published, a green bar should appear at the top of the page.</span></span> <span data-ttu-id="13971-178">Klicken Sie auf die grüne Leiste, um die Seite "verwalten" anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="13971-178">Click the green bar to view the "Manage" page.</span></span>

    ![Module4Chapter4step20im](images/module4chapter4step20im.PNG)

20. <span data-ttu-id="13971-180">Klicken Sie auf der linken Seite unter "Anwendungseinstellungen" auf "Schlüssel und Endpunkte".</span><span class="sxs-lookup"><span data-stu-id="13971-180">Click "Keys and Endpoints" under “Application Settings” to the left.</span></span> <span data-ttu-id="13971-181">Legen Sie dann die Dropdown-Einstellung "veröffentlichen auf" als "Produktion" fest.</span><span class="sxs-lookup"><span data-stu-id="13971-181">Then, set the drop down "Publish To" as "Production."</span></span> <span data-ttu-id="13971-182">Legen Sie die Zeitzone entsprechend fest, und aktivieren Sie das Kontrollkästchen, um alle vorhergesagten Intent-Ergebnisse einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="13971-182">Set the time-zone to match yours, and check the box to include all predicted intent scores.</span></span> <span data-ttu-id="13971-183">Klicken Sie abschließend auf "Ressource zuweisen".</span><span class="sxs-lookup"><span data-stu-id="13971-183">Lastly, click "Assign resource."</span></span>

    ![Module4Chapter4step21im](images/module4chapter4step21im.PNG)

21. <span data-ttu-id="13971-185">Wählen Sie in der ersten Dropdown Liste Mandant aus, und wählen Sie in der Dropdown Liste Abonnement Name den Namen "Pay-as-you-go" aus.</span><span class="sxs-lookup"><span data-stu-id="13971-185">Select tenant from the first dropdown and select “Pay-as-you-go” in the Subscription Name dropdown.</span></span> <span data-ttu-id="13971-186">Wählen Sie unter Luis Resource Name die zuvor erstellte Ressource in den Schritten 1-5 aus.</span><span class="sxs-lookup"><span data-stu-id="13971-186">Under LUIS resource name, choose the resource that we created above in steps 1-5.</span></span> <span data-ttu-id="13971-187">Klicken Sie dann auf "Ressource zuweisen".</span><span class="sxs-lookup"><span data-stu-id="13971-187">Then, click on "Assign resource."</span></span>

    ![Module4Chapter4step22im](images/module4chapter4step22im.PNG)

    >[!NOTE]
    ><span data-ttu-id="13971-189">Stellen Sie sicher, dass Sie die der soeben zugewiesenen Ressource zugeordnete Endpunkt-URL kopieren und speichern, damit der nächste Abschnitt leicht zugänglich ist.</span><span class="sxs-lookup"><span data-stu-id="13971-189">Ensure to copy and save the Endpoint URL associated with the resource we just assigned so it is easily accessible for the next section.</span></span>

    >[!NOTE]
    ><span data-ttu-id="13971-190">Geben Sie für den Mandanten Namen ihre Corporation oder Ihr Profil ein, das Sie für diese Anwendung erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="13971-190">For the Tenant name, put your corporation or profile that you created for this application.</span></span>

22. <span data-ttu-id="13971-191">Öffnen Sie nun die neue app in Unity, und wählen Sie das Lunarcom_Base-Objekt in der Hierarchie aus.</span><span class="sxs-lookup"><span data-stu-id="13971-191">Now, open the new app in Unity and select the Lunarcom_Base object in the hierarchy.</span></span> <span data-ttu-id="13971-192">Klicken Sie im Inspektor-Panel auf "Komponente hinzufügen", suchen Sie nach "lunarcomintenterkenzer", und wählen Sie ihn aus.</span><span class="sxs-lookup"><span data-stu-id="13971-192">Click “Add Component” in the inspector panel and search for and select “LunarcomIntentRecognizer.”</span></span>

    ![Module4Chapter4step23im](images/module4chapter4step23im.PNG)

23. <span data-ttu-id="13971-194">Geben Sie im Feld für den Luis-Endpunkt der "lunarcomintenterkenzer" im Inspektor-Panel die Endpunkt-URL ein, die Sie in Schritt 22 gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="13971-194">In the Luis Endpoint field of the "LunarcomIntentRecognizer" in the inspector panel, enter the Endpoint URL that you saved in step 22.</span></span>

    ![Module4Chapter4step24im](images/module4chapter4step24im.PNG)

    >[!NOTE]
    ><span data-ttu-id="13971-196">Stellen Sie sicher, dass in der Komponente "lunarcomofflinerecognizer" im Inspektor-Panel "deaktivieren" für "simulateofflinemode" ausgewählt ist. andernfalls funktioniert das Testen des Programms nicht.</span><span class="sxs-lookup"><span data-stu-id="13971-196">In the "LunarcomOfflineRecognizer" component in the inspector panel, make sure that “disable” is selected for "SimulateOfflineMode" otherwise, testing the program will not work.</span></span>

24. <span data-ttu-id="13971-197">Klicken Sie im Unity-Editor auf die Wiedergabe Schaltfläche, und klicken Sie auf die Schaltfläche ""</span><span class="sxs-lookup"><span data-stu-id="13971-197">Press the Play button in the Unity Editor and click the rocket button to start intent recognition.</span></span> <span data-ttu-id="13971-198">Sagen Sie den Ausdruck "starten Sie die Schaltfläche" starten "aus.</span><span class="sxs-lookup"><span data-stu-id="13971-198">Utter the phrase “select the launch rocket button.”</span></span>

    >[!NOTE]
    ><span data-ttu-id="13971-199">Die APP hat die gewünschte Funktion erkannt und die Schaltfläche "Rocket" aktiviert.</span><span class="sxs-lookup"><span data-stu-id="13971-199">The app recognized the desired function and activated the rocket button.</span></span>
    >
    >![Module4Chapter4step24im](images/module4chapter4note2im.PNG)

## <a name="congratulations"></a><span data-ttu-id="13971-201">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="13971-201">Congratulations</span></span>

<span data-ttu-id="13971-202">In dieser Lektion haben Sie gelernt, wie Sie Ki-gestützte Sprachbefehle hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="13971-202">In this lesson, you learned how to add AI-powered speech commands.</span></span> <span data-ttu-id="13971-203">Jetzt kann Ihr Programm die Absicht der Benutzer erkennen, auch wenn Sie keine präzisen Sprachbefehle mehr haben!</span><span class="sxs-lookup"><span data-stu-id="13971-203">Now your program can recognize users' intent, even if they do not utter precise voice commands!</span></span>
