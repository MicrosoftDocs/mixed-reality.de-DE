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
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "79028480"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a><span data-ttu-id="06d0c-105">4. Einrichten des Verstehens von Absichten und natürlicher Sprache</span><span class="sxs-lookup"><span data-stu-id="06d0c-105">4. Setting up intent and natural language understanding</span></span>

<span data-ttu-id="06d0c-106">In diesem Tutorial untersuchen wir die Absichtserkennung des Azure-Sprachdiensts.</span><span class="sxs-lookup"><span data-stu-id="06d0c-106">In this tutorial, you will explore the Azure Speech Service's intent recognition.</span></span> <span data-ttu-id="06d0c-107">Die Absichtserkennung ermöglicht es Ihnen, Ihre Anwendung mit KI-gestützten Sprachbefehlen auszustatten. In diesem Fall können Benutzer unspezifische Sprachbefehle äußern, und ihre Absicht wird trotzdem vom System verstanden.</span><span class="sxs-lookup"><span data-stu-id="06d0c-107">The intent recognition allows you to equip our application with AI-powered speech commands, where users can say non-specific speech commands and still have their intent understood by the system.</span></span>

## <a name="objectives"></a><span data-ttu-id="06d0c-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="06d0c-108">Objectives</span></span>

* <span data-ttu-id="06d0c-109">Das Erlernen der Einrichtung von Absicht, Entitäten und Äußerungen im LUIS-Portal</span><span class="sxs-lookup"><span data-stu-id="06d0c-109">Learn how to set up intent, entities, and utterances in the LUIS portal</span></span>
* <span data-ttu-id="06d0c-110">Erlernen der Implementierung des Erkennens von Absichten und des Verstehens natürlicher Sprache in unserer Anwendung</span><span class="sxs-lookup"><span data-stu-id="06d0c-110">Learn how to implement intent and natural language understanding in our application</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="06d0c-111">Vorbereiten des Szenarios</span><span class="sxs-lookup"><span data-stu-id="06d0c-111">Preparing the scene</span></span>

<span data-ttu-id="06d0c-112">Wählen Sie im Hierarchiefenster das **Lunarcom**-Objekt aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um dem Lunarcom-Objekt die Komponente **Lunarcom Intent Recognizer (Script)** hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="06d0c-112">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Intent Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-1.png)

<span data-ttu-id="06d0c-114">Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher**, ziehen Sie das Prefab **RocketLauncher_Complete** in Ihr Hierarchiefenster, und platzieren Sie es an einem passenden Ort vor der Kamera, beispielsweise:</span><span class="sxs-lookup"><span data-stu-id="06d0c-114">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher_Complete** prefab into your Hierarchy window, and place it at a suitable location in front of the camera, for example:</span></span>

* <span data-ttu-id="06d0c-115">**Transformationsposition** X = 0, Y = -0,4, Z = 1</span><span class="sxs-lookup"><span data-stu-id="06d0c-115">Transform **Position** X = 0, Y = -0.4, Z = 1</span></span>
* <span data-ttu-id="06d0c-116">**Transformationsrotation** X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="06d0c-116">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-2.png)

<span data-ttu-id="06d0c-118">Wählen Sie im Hierarchiefenster das **Lunarcom**-Objekt erneut aus, klappen Sie dann das Objekt **RocketLauncher_Complete** > **Button** auf, und weisen Sie jedem untergeordneten Objekt des **Buttons**-Objekts das entsprechende **Lunar Launcher Buttons**-Feld zu:</span><span class="sxs-lookup"><span data-stu-id="06d0c-118">In the Hierarchy window, select the **Lunarcom** object again, then expand the **RocketLauncher_Complete** > **Button** object and assign each of the **Buttons** object's child objects to the corresponding **Lunar Launcher Buttons** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section1-step1-3.png)

## <a name="creating-the-azure-language-understanding-resource"></a><span data-ttu-id="06d0c-120">Erstellen der Azure Language Understanding-Ressource</span><span class="sxs-lookup"><span data-stu-id="06d0c-120">Creating the Azure Language Understanding resource</span></span>

<span data-ttu-id="06d0c-121">In diesem Abschnitt erstellen Sie eine Azure-Vorhersageressource für die LUIS-App (Language Understanding Intelligent Service), die Sie im nächsten Abschnitt erstellen.</span><span class="sxs-lookup"><span data-stu-id="06d0c-121">In this section, you will create an Azure prediction resource for the Language Understanding Intelligent Service (LUIS) app you will create in the next section.</span></span>

<span data-ttu-id="06d0c-122">Melden Sie sich bei <a href="https://portal.azure.com" target="_blank">Azure</a> an, und klicken Sie auf **Ressource erstellen**.</span><span class="sxs-lookup"><span data-stu-id="06d0c-122">Sign in to <a href="https://portal.azure.com" target="_blank">Azure</a> and click **Create a resource**.</span></span> <span data-ttu-id="06d0c-123">Suchen Sie dann nach **Language Understanding**, und wählen Sie es aus:</span><span class="sxs-lookup"><span data-stu-id="06d0c-123">Then search for and select **Language Understanding**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-1.png)

<span data-ttu-id="06d0c-125">Klicken Sie auf die Schaltfläche **Erstellen**, um eine Instanz dieses Diensts zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="06d0c-125">Click the **Create** button to create an instance of this service:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-2.png)

<span data-ttu-id="06d0c-127">Klicken Sie auf der Seite „Erstellen“ auf die Option **Vorhersage**, und geben Sie die folgenden Werte ein:</span><span class="sxs-lookup"><span data-stu-id="06d0c-127">On the Create page, click the **Prediction** option and enter the following values:</span></span>

* <span data-ttu-id="06d0c-128">Wählen Sie unter **Abonnement** **Kostenlose Testversion** aus, wenn Sie über ein Testabonnement verfügen, und wählen Sie andernfalls eins Ihrer anderen Abonnements aus</span><span class="sxs-lookup"><span data-stu-id="06d0c-128">For **Subscription**, select **Free Trail** if you have a trial subscription, otherwise, select one of your other subscriptions</span></span>
* <span data-ttu-id="06d0c-129">Klicken Sie für die **Ressourcengruppe** auf den Link **Neue erstellen**, geben Sie einen passenden Namen ein, beispielsweise *MRKT-Tutorials*, und klicken Sie dann auf **OK**</span><span class="sxs-lookup"><span data-stu-id="06d0c-129">For the **Resource group**, click the **Create new** link, enter a suitable name, for example, *MRKT-Tutorials*, and then click the **OK**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="06d0c-131">Zum Zeitpunkt der Entstehung dieses Artikels muss nicht eigens eine Erstellungsressource erstellt werden, da in LUIS automatisch ein Erstellungs-Testschlüssel generiert wird, wenn Sie im nächsten Abschnitt den Language Understanding Intelligent Service (LUIS) erstellen.</span><span class="sxs-lookup"><span data-stu-id="06d0c-131">As of the time of this writing, you do not need to create an authoring resource because an authoring trial key will automatically be generated within LUIS when you create the Language Understanding Intelligent Service (LUIS) in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="06d0c-132">Wenn Sie bereits über eine andere geeignete Ressourcengruppe in Ihrem Azure-Konto verfügen, beispielsweise, wenn Sie das [Azure Spatial Anchor](mrlearning-asa-ch1.md)-Tutorial abgeschlossen haben, können Sie diese Ressourcengruppe verwenden, statt eine neue zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="06d0c-132">If you already have another suitable resource group in your Azure account, for example, if you completed the [Azure Spatial Anchors](mrlearning-asa-ch1.md) tutorial, you may use this resource group instead of creating a new one.</span></span>

<span data-ttu-id="06d0c-133">Geben Sie noch auf der Seite „Erstellen“ die folgenden Werte ein:</span><span class="sxs-lookup"><span data-stu-id="06d0c-133">While still on the Create page, enter the following values:</span></span>

* <span data-ttu-id="06d0c-134">Geben Sie für **Name** einen passenden Namen für den Dienst ein, z. B. *MRTK-Tutorials-AzureSpeechServices*</span><span class="sxs-lookup"><span data-stu-id="06d0c-134">For **Name**, enter a suitable name for the service, for example, *MRTK-Tutorials-AzureSpeechServices*</span></span>
* <span data-ttu-id="06d0c-135">Wählen Sie als **Speicherort für die Vorhersage** einen Speicherort in der Nähe des Standorts Ihres App-Benutzers aus, z. B. *(USA) USA, Westen*</span><span class="sxs-lookup"><span data-stu-id="06d0c-135">For **Prediction location**, choose a location close to your app users' physical location, for example, *(US) West US*</span></span>
* <span data-ttu-id="06d0c-136">Wählen Sie als **Tarif für Vorhersage** im Rahmen dieses Tutorials **F0 (5 Aufrufe pro Sekunde, 10.000 Aufrufe pro Monat)** aus</span><span class="sxs-lookup"><span data-stu-id="06d0c-136">For **Prediction pricing tier**, for the purpose of this tutorial, select **F0 (5 Calls per second, 10K Calls per month)**</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-4.png)

<span data-ttu-id="06d0c-138">Navigieren Sie als nächstes zur Registerkarte **Überprüfen + Erstellen**, überprüfen Sie die Details, und klicken Sie dann auf die Schaltfläche **Erstellen** am unteren Rand der Seite, um die Ressource sowie die neue Ressourcengruppe zu erstellen, falls Sie die Erstellung einer Ressourcengruppe konfiguriert haben:</span><span class="sxs-lookup"><span data-stu-id="06d0c-138">Next, go to the **Review + create** tab, review the details, and then click the **Create** button, located at the bottom of the page, to create the resource, as well as, the new resource group if you configured one to be created:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-5.png)

> [!NOTE]
> <span data-ttu-id="06d0c-140">Nachdem Sie auf die Schaltfläche „Erstellen“ geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. Dies kann einige Minuten in Anspruch nehmen.</span><span class="sxs-lookup"><span data-stu-id="06d0c-140">After you click the Create button, you will have to wait for the service to be created, which might take a few minutes.</span></span>

<span data-ttu-id="06d0c-141">Nachdem der Vorgang zum Erstellen der Ressource abgeschlossen ist, wird die Meldung angezeigt **Ihre Bereitstellung wurde abgeschlossen.** :</span><span class="sxs-lookup"><span data-stu-id="06d0c-141">Once the resource creation process is completed, you will see the message **Your deployment is complete**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section2-step1-6.png)

## <a name="creating-the-language-understanding-intelligent-service-luis"></a><span data-ttu-id="06d0c-143">Erstellen des Language Understanding Intelligent Service (LUIS)</span><span class="sxs-lookup"><span data-stu-id="06d0c-143">Creating the Language Understanding Intelligent Service (LUIS)</span></span>

<span data-ttu-id="06d0c-144">In diesem Abschnitt erstellen Sie eine LUIS-App, konfigurieren und trainieren ihr Vorhersagemodell und verbinden es mit der Azure-Vorhersageressource, die Sie im vorherigen Schritt erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="06d0c-144">In this section, you will create a LUIS app, configure and train its prediction model, and connect it to the Azure prediction resource you created in the previous step.</span></span>

<span data-ttu-id="06d0c-145">Insbesondere erstellen Sie eine Absicht, die, falls der Benutzer sagt, dass eine Aktion ausgeführt werden soll, das Interactable.OnClick()-Ereignis für eine der drei roten Schaltflächen im Szenario auslöst, je nachdem, auf welche Schaltfläche der Benutzer verweist.</span><span class="sxs-lookup"><span data-stu-id="06d0c-145">Specifically, you will create an intent that if the user says an action should be taken, the app will trigger the Interactable.OnClick() event on one of the three red buttons in the scene, depending on which button the user references.</span></span>

<span data-ttu-id="06d0c-146">Wenn der Benutzer beispielsweise sagt **Fahre fort, starte die Rakete**, sagt die App vorher, dass **Fahre fort** bedeutet, dass eine **Aktion** ausgeführt werden soll, und dass das **anzuzielende** Interactable.OnClick()-Ereignis sich auf der Schaltfläche **Starten** befindet.</span><span class="sxs-lookup"><span data-stu-id="06d0c-146">For example, if the user says **go ahead and launch the rocket**, the app will predict that **go ahead** means some **action** should be taken, and that the Interactable.OnClick() event to **target** is on the **launch** button.</span></span>

<span data-ttu-id="06d0c-147">Dies sind die wichtigsten Schritte, die Sie durchführen müssen:</span><span class="sxs-lookup"><span data-stu-id="06d0c-147">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="06d0c-148">Erstellen einer LUIS-App</span><span class="sxs-lookup"><span data-stu-id="06d0c-148">Create a LUIS app</span></span>
2. <span data-ttu-id="06d0c-149">Erstellen von Absichten</span><span class="sxs-lookup"><span data-stu-id="06d0c-149">Create intents</span></span>
3. <span data-ttu-id="06d0c-150">Erstellen von Beispieläußerungen</span><span class="sxs-lookup"><span data-stu-id="06d0c-150">Create example utterances</span></span>
4. <span data-ttu-id="06d0c-151">Erstellen von Entitäten</span><span class="sxs-lookup"><span data-stu-id="06d0c-151">Create entities</span></span>
5. <span data-ttu-id="06d0c-152">Zuweisen von Entitäten zu den Beispieläußerungen</span><span class="sxs-lookup"><span data-stu-id="06d0c-152">Assign entities to the example utterances</span></span>
6. <span data-ttu-id="06d0c-153">Trainieren, Testen und Veröffentlichen der App</span><span class="sxs-lookup"><span data-stu-id="06d0c-153">Train, test, and publish the app</span></span>
7. <span data-ttu-id="06d0c-154">Zuweisen einer Azure-Vorhersageressource zur App</span><span class="sxs-lookup"><span data-stu-id="06d0c-154">Assign an Azure prediction resource to the app</span></span>

### <a name="1-create-a-luis-app"></a><span data-ttu-id="06d0c-155">1. Erstellen einer LUIS-App</span><span class="sxs-lookup"><span data-stu-id="06d0c-155">1. Create a LUIS app</span></span>

<span data-ttu-id="06d0c-156">Melden Sie sich bei <a href="https://www.luis.ai" target="_blank">LUIS</a> mit demselben Benutzerkonto an, das Sie zum Erstellen der Azure-Ressource im vorherigen Abschnitt verwendet haben, wählen Sie Ihr Land/Ihre Region aus, und stimmen Sie den Nutzungsbedingungen zu.</span><span class="sxs-lookup"><span data-stu-id="06d0c-156">Using the same user account you used when creating the Azure resource in the previous section, sign in to <a href="https://www.luis.ai" target="_blank">LUIS</a>, select your country, and agree to the terms of use.</span></span> <span data-ttu-id="06d0c-157">Wenn Sie im nächsten Schritt aufgefordert werden, **Ihr Azure-Konto zu verknüpfen**, wählen Sie **Weiterhin den Testschlüssel verwenden** aus, um stattdessen eine Azure-Erstellungsressource zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="06d0c-157">In the next step, when asked to **Link your Azure account**, choose **Continue using your trial key**, to use an Azure authoring resource instead.</span></span>

> [!NOTE]
> <span data-ttu-id="06d0c-158">Wenn Sie sich bereits für LUIS registriert haben und Ihr Erstellungs-Testschlüssel abgelaufen ist, finden Sie Informationen zum Umstellen Ihrer LUIS-Erstellungsressource auf Azure in der [Migrieren zu einem Azure-Ressourcen-Erstellungsschlüssel](https://docs.microsoft.com/azure/cognitive-services/luis/luis-migration-authoring)-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="06d0c-158">If you have already signed up for LUIS and your authoring trial key has expired, you can refer to the [Migrate to an Azure resource authoring key](https://docs.microsoft.com/azure/cognitive-services/luis/luis-migration-authoring) documentation to switch your LUIS authoring resource to Azure.</span></span>

<span data-ttu-id="06d0c-159">Navigieren Sie nach der Anmeldung zur Seite **Meine Apps**, klicken Sie auf **Neue App erstellen**, und geben Sie im Fenster **Neue App erstellen** die folgenden Werte ein:</span><span class="sxs-lookup"><span data-stu-id="06d0c-159">Once signed in, navigate to the **My apps** page, then click **Create new app** and enter the following values in the **Create new app** popup window:</span></span>

* <span data-ttu-id="06d0c-160">Geben Sie für **Name** einen passenden Namen ein, z. B. *MRTK-Tutorials – AzureSpeechServices*</span><span class="sxs-lookup"><span data-stu-id="06d0c-160">For **Name**, enter a suitable name, for example, *MRTK Tutorials - AzureSpeechServices*</span></span>
* <span data-ttu-id="06d0c-161">Wählen Sie für **Kultur** die Option **Englisch** aus</span><span class="sxs-lookup"><span data-stu-id="06d0c-161">For **Culture**, select **English**</span></span>
* <span data-ttu-id="06d0c-162">Geben Sie für **Beschreibung** optional eine passende Beschreibung ein</span><span class="sxs-lookup"><span data-stu-id="06d0c-162">For **Description**, optionally enter a suitable description</span></span>

<span data-ttu-id="06d0c-163">Klicken Sie dann auf die Schaltfläche **Erstellen**, um die neue App zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="06d0c-163">Then click the **Done** button to create the new app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-1.png)

<span data-ttu-id="06d0c-165">Wenn die neue App erstellt wurde, werden Sie zur **Dashboard** Seite der App geleitet:</span><span class="sxs-lookup"><span data-stu-id="06d0c-165">When the new app has been created, you will be taken to that app's **Dashboard** page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step1-2.png)

### <a name="2-create-intents"></a><span data-ttu-id="06d0c-167">2. Erstellen von Absichten</span><span class="sxs-lookup"><span data-stu-id="06d0c-167">2. Create intents</span></span>

<span data-ttu-id="06d0c-168">Navigieren Sie von der Dashboard-Seite zur Seite „Build > App Assets > **Intents**“ (Erstellen > App-Ressourcen > Absichten), klicken Sie dann auf **Create new intent** (Neue Absicht erstellen), und geben Sie den folgenden Wert im Popupfenster **Create new intent** ein:</span><span class="sxs-lookup"><span data-stu-id="06d0c-168">From the Dashboard page, navigate to the Build > App Assets > **Intents** page, then click **Create new intent** and enter the following value in the **Create new intent** popup window:</span></span>

* <span data-ttu-id="06d0c-169">Geben Sie als **Absichtsname** **PressButton** ein</span><span class="sxs-lookup"><span data-stu-id="06d0c-169">For **Intent name**, enter **PressButton**</span></span>

<span data-ttu-id="06d0c-170">Klicken Sie dann auf die Schaltfläche **Done** (Fertig), um die neue Ansicht zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="06d0c-170">Then click the **Done** button to create the new intent:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-1.png)

> [!CAUTION]
> <span data-ttu-id="06d0c-172">Im Rahmen dieses Tutorials verweist Ihr Unity-Projekt anhand des Namens auf diese Absicht, d. h. ‚PressButton‘.</span><span class="sxs-lookup"><span data-stu-id="06d0c-172">For the purpose of this tutorial, your Unity project will reference this intent by its name, i.e. 'PressButton'.</span></span> <span data-ttu-id="06d0c-173">Es ist daher äußerst wichtig, dass Sie Ihre Absicht genau gleich benennen.</span><span class="sxs-lookup"><span data-stu-id="06d0c-173">Consequently, it is extremely important that you name your intent exactly the same.</span></span>

<span data-ttu-id="06d0c-174">Wenn die neue Absicht erstellt wurde, werden Sie zu der Seite dieser Absicht geleitet:</span><span class="sxs-lookup"><span data-stu-id="06d0c-174">When the new intent has been created, you will be taken to that intent's page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step2-2.png)

### <a name="3-create-example-utterances"></a><span data-ttu-id="06d0c-176">3. Erstellen von Beispieläußerungen</span><span class="sxs-lookup"><span data-stu-id="06d0c-176">3. Create example utterances</span></span>

<span data-ttu-id="06d0c-177">Fügen Sie der Liste mit **Beispieläußerungen** der Absicht **PressButton** die folgenden Beispieläußerungen hinzu:</span><span class="sxs-lookup"><span data-stu-id="06d0c-177">To the **PressButton** intent's **Example utterance** list, add the following example utterances:</span></span>

* <span data-ttu-id="06d0c-178">Startsequenz aktivieren</span><span class="sxs-lookup"><span data-stu-id="06d0c-178">activate launch sequence</span></span>
* <span data-ttu-id="06d0c-179">Platzierungshinweis anzeigen</span><span class="sxs-lookup"><span data-stu-id="06d0c-179">show me a placement hint</span></span>
* <span data-ttu-id="06d0c-180">Startsequenz einleiten</span><span class="sxs-lookup"><span data-stu-id="06d0c-180">initiate the launch sequence</span></span>
* <span data-ttu-id="06d0c-181">Schaltflächen für Platzierungshinweise drücken</span><span class="sxs-lookup"><span data-stu-id="06d0c-181">press placement hints button</span></span>
* <span data-ttu-id="06d0c-182">Gib mit einen Hinweis</span><span class="sxs-lookup"><span data-stu-id="06d0c-182">give me a hint</span></span>
* <span data-ttu-id="06d0c-183">Startschaltfläche drücken</span><span class="sxs-lookup"><span data-stu-id="06d0c-183">push the launch button</span></span>
* <span data-ttu-id="06d0c-184">Ich brauche einen Hinweis</span><span class="sxs-lookup"><span data-stu-id="06d0c-184">i need a hint</span></span>
* <span data-ttu-id="06d0c-185">Taste „Zurücksetzen“ drücken</span><span class="sxs-lookup"><span data-stu-id="06d0c-185">press the reset button</span></span>
* <span data-ttu-id="06d0c-186">Zeit zum Zurücksetzen des Experiments</span><span class="sxs-lookup"><span data-stu-id="06d0c-186">time to reset the experience</span></span>
* <span data-ttu-id="06d0c-187">Fahre fort, starte die Rakete</span><span class="sxs-lookup"><span data-stu-id="06d0c-187">go ahead and launch the rocket</span></span>

<span data-ttu-id="06d0c-188">Wenn alle Beispieläußerungen hinzugefügt wurden, sollte die Seite Ihrer Absicht PressButton so ähnlich aussehen:</span><span class="sxs-lookup"><span data-stu-id="06d0c-188">When all the example utterances have been added, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step3-1.png)

> [!CAUTION]
> <span data-ttu-id="06d0c-190">Im Rahmen dieses Tutorials verweist Ihr Unity-Projekt auf die Wörter „Hinweis“, „Hinweise“, „Zurücksetzen“ und „Starten“.</span><span class="sxs-lookup"><span data-stu-id="06d0c-190">For the purpose of this tutorial, your Unity project will reference the words 'hint', 'hints', 'reset', and 'launch'.</span></span> <span data-ttu-id="06d0c-191">Daher ist es äußerst wichtig, dass Sie diese Wörter in genau der gleichen Weise schreiben.</span><span class="sxs-lookup"><span data-stu-id="06d0c-191">Consequently, it is extremely important that you spell these words in the exact same way.</span></span>

### <a name="4-create-entities"></a><span data-ttu-id="06d0c-192">4. Erstellen von Entitäten</span><span class="sxs-lookup"><span data-stu-id="06d0c-192">4. Create entities</span></span>

<span data-ttu-id="06d0c-193">Navigieren Sie von der Seite der Absicht PressButton zur Seite Erstellen > App-Ressourcen > **Entitäten**, klicken Sie dann auf **Neue Entität erstellen**, und geben Sie die folgenden Werte im Popupfenster **Neue Entität erstellen** ein:</span><span class="sxs-lookup"><span data-stu-id="06d0c-193">From the PressButton intent page, navigate to the Build > App Assets > **Entities** page, then click **Create new entity** and enter the following values in the **Create new entity** popup window:</span></span>

* <span data-ttu-id="06d0c-194">Geben Sie als **Entitätsname** **Aktion** ein</span><span class="sxs-lookup"><span data-stu-id="06d0c-194">For **Entity name**, enter **Action**</span></span>
* <span data-ttu-id="06d0c-195">Wählen Sie als **Entitätstyp** **Einfach** aus</span><span class="sxs-lookup"><span data-stu-id="06d0c-195">For **Entity type**, select **Simple**</span></span>

<span data-ttu-id="06d0c-196">Klicken Sie dann auf die Schaltfläche **Fertig**, um die neue Entität zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="06d0c-196">Then click the **Done** button to create the new entity:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-1.png)

<span data-ttu-id="06d0c-198">**Wiederholen** Sie den vorhergehenden Schritt, um eine weitere Entität mit dem Namen **Ziel** zu erstellen, sodass Sie über zwei Entitäten verfügen, mit den Namen „Aktion“ und „Ziel“:</span><span class="sxs-lookup"><span data-stu-id="06d0c-198">**Repeat** the previous step to create another entity named **Target**, so you have two entities named Action and Target:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step4-2.png)

> [!CAUTION]
> <span data-ttu-id="06d0c-200">Im Rahmen dieses Tutorials verweist Ihr Unity-Projekt anhand des Namens auf diese Entitäten, d. h. „Aktion“ und „Ziel“.</span><span class="sxs-lookup"><span data-stu-id="06d0c-200">For the purpose of this tutorial, your Unity project will reference these entities by their names, i.e. 'Action' and 'Target'.</span></span> <span data-ttu-id="06d0c-201">Es ist daher äußerst wichtig, dass Sie Ihre Entitäten genau gleich benennen.</span><span class="sxs-lookup"><span data-stu-id="06d0c-201">Consequently, it is extremely important that you name your entities exactly the same.</span></span>

### <a name="5-assign-entities-to-the-example-utterances"></a><span data-ttu-id="06d0c-202">5. Zuweisen von Entitäten zu den Beispieläußerungen</span><span class="sxs-lookup"><span data-stu-id="06d0c-202">5. Assign entities to the example utterances</span></span>

<span data-ttu-id="06d0c-203">Navigieren Sie auf der Seite Entitäten zurück zur Seite der Absicht **PressButton**.</span><span class="sxs-lookup"><span data-stu-id="06d0c-203">From the Entities page, navigate back to the **PressButton** intent page.</span></span>

<span data-ttu-id="06d0c-204">Sobald Sie sich wieder auf der Seite der Absicht PressButton befinden, klicken Sie auf das Wort **Fahre**, dann auf das Wort **fort**, und wählen Sie dann im Kontext-Popupmenü **Aktion (Einfach)** aus, um **Fahre fort** als einen Entitätswert für **Aktion**-zu bezeichnen:</span><span class="sxs-lookup"><span data-stu-id="06d0c-204">Once back on the the PressButton intent page, click on the word **go** and then on the word **ahead**, and then select **Action (Simple)** from the contextual popup menu to label **go ahead** as an **Action** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-1.png)

<span data-ttu-id="06d0c-206">Der Ausdruck **Fahre fort** ist jetzt als Entitätswert für **Aktion** definiert.</span><span class="sxs-lookup"><span data-stu-id="06d0c-206">The **go ahead** phrase is now defined as an **Action** entity value.</span></span> <span data-ttu-id="06d0c-207">Wenn Sie den Mauszeiger auf dem Entitätsnamen „Aktion“ ruhen lassen, können Sie den zugeordneten Wert der Entität Aktion sehen:</span><span class="sxs-lookup"><span data-stu-id="06d0c-207">If you hover your mouse cursor above the Action entity name, you can see the associated Action entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-2.png)

> [!NOTE]
> <span data-ttu-id="06d0c-209">Die rote Linie, die unter der Bezeichnung in der Abbildung oben angezeigt wird, weist darauf hin, dass der Entitätswert nicht vorhergesagt wurde. Dies wird behoben, wenn Sie das Modell im nächsten Abschnitt trainieren.</span><span class="sxs-lookup"><span data-stu-id="06d0c-209">The red line you see under the label in the image above indicates that the entity value has not been predicted, this will be resolved when you train the model in the next section.</span></span>

<span data-ttu-id="06d0c-210">Klicken Sie als nächstes auf das Wort **starte**, und wählen Sie dann im Kontext-Popupmenü **Ziel (Einfach)** aus, um **starte** als einen **Ziel**-Entitätswert zu bezeichnen:</span><span class="sxs-lookup"><span data-stu-id="06d0c-210">Next, click on the word **launch**, and then select **Target (Simple)** from the contextual popup menu to label **launch** as a **Target** entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-3.png)

<span data-ttu-id="06d0c-212">Das Wort **starte** ist jetzt als Entitätswert für **Ziel** definiert.</span><span class="sxs-lookup"><span data-stu-id="06d0c-212">The **launch** word is now defined as a **Target** entity value.</span></span> <span data-ttu-id="06d0c-213">Wenn Sie den Mauszeiger auf dem Entitätsnamen „Ziel“ ruhen lassen, können Sie den zugeordneten Wert der Entität Ziel sehen:</span><span class="sxs-lookup"><span data-stu-id="06d0c-213">If you hover your mouse cursor above the Target entity name, you can see the associated Target entity value:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-4.png)

<span data-ttu-id="06d0c-215">Die Beispieläußerung „Fahre fort, starte die Rakete“ für die PressButton-Absicht ist jetzt dafür konfiguriert, in folgender Weise vorhergesagt zu werden :</span><span class="sxs-lookup"><span data-stu-id="06d0c-215">The PressButton intent example utterance 'go ahead and launch the rocket' is now configured to be predicted as follows:</span></span>

* <span data-ttu-id="06d0c-216">Absicht: PressButton</span><span class="sxs-lookup"><span data-stu-id="06d0c-216">Intent: PressButton</span></span>
* <span data-ttu-id="06d0c-217">Action-Entität: Fahre fort</span><span class="sxs-lookup"><span data-stu-id="06d0c-217">Action entity: go ahead</span></span>
* <span data-ttu-id="06d0c-218">Zielentität: starte</span><span class="sxs-lookup"><span data-stu-id="06d0c-218">Target entity: launch</span></span>

<span data-ttu-id="06d0c-219">**Wiederholen** Sie die vorhergehenden zwei Schritte, um jeder der Beispieläußerungen eine Aktions- und eine Zielentitätsbezeichnung zuzuweisen, und behalten Sie dabei im Blick, dass die folgenden Wörter als **Ziel**-Entitäten bezeichnet werden sollen:</span><span class="sxs-lookup"><span data-stu-id="06d0c-219">**Repeat** the previous two-step process to assign an Action and a Target entity label to each of the example utterances, keeping in mind that the following words should be labeled as **Target** entities:</span></span>

* <span data-ttu-id="06d0c-220">**Hinweis** (zielt auf die HintsButton-Schaltfläche im Unity-Projekt ab)</span><span class="sxs-lookup"><span data-stu-id="06d0c-220">**hint** (targets the HintsButton in the Unity project)</span></span>
* <span data-ttu-id="06d0c-221">**Hinweise** (zielt auf die HintsButton-Schaltfläche im Unity-Projekt ab)</span><span class="sxs-lookup"><span data-stu-id="06d0c-221">**hints** (targets HintsButton in the Unity project)</span></span>
* <span data-ttu-id="06d0c-222">**Zurücksetzen** (zielt auf die ResetButton-Schaltfläche im Unity-Projekt ab)</span><span class="sxs-lookup"><span data-stu-id="06d0c-222">**reset** (targets the ResetButton in the Unity project)</span></span>
* <span data-ttu-id="06d0c-223">**starte** (zielt auf die LaunchButton-Schaltfläche im Unity-Projekt ab)</span><span class="sxs-lookup"><span data-stu-id="06d0c-223">**launch** (targets the LaunchButton in the Unity project)</span></span>

<span data-ttu-id="06d0c-224">Wenn alle Beispieläußerungen bezeichnet wurden, sollte die Seite Ihrer Absicht PressButton so ähnlich aussehen:</span><span class="sxs-lookup"><span data-stu-id="06d0c-224">When all the example utterances have been labeled, your PressButton intent page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-5.png)

<span data-ttu-id="06d0c-226">Um mit einem alternativen Verfahren zu prüfen, ob Sie die richtigen Entitäten zugewiesen haben, klicken Sie auf das Menü **Ansichtsoptionen**, und wechseln Sie zur Ansicht **Entitätswerte anzeigen**:</span><span class="sxs-lookup"><span data-stu-id="06d0c-226">For an alternative way to double-check that you have assigned the correct entities, click the **View options** menu and switch the view to **Show entity values**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-6.png)

<span data-ttu-id="06d0c-228">Jetzt, mit einer Ansicht, in der Entitätswerte angezeigt werden, können Sie den Mauszeiger auf den bezeichneten Wörtern und Ausdrücken ruhen lassen, um schnell den Namen der zugewiesenen Entität zu überprüfen:</span><span class="sxs-lookup"><span data-stu-id="06d0c-228">Now, with the view set to show entity values, you can hover the mouse courser over the labeled words and phrases to quickly verify the assigned entity name:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step5-7.png)

### <a name="6-train-test-and-publish-the-app"></a><span data-ttu-id="06d0c-230">6. Trainieren, Testen und Veröffentlichen der App</span><span class="sxs-lookup"><span data-stu-id="06d0c-230">6. Train, test, and publish the app</span></span>

<span data-ttu-id="06d0c-231">Um die App zu trainieren, klicken Sie auf die Schaltfläche **Trainieren**, und warten Sie, bis der Trainingsprozess abgeschlossen ist:</span><span class="sxs-lookup"><span data-stu-id="06d0c-231">To train the app, click the **Train** button and wait for the training process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-1.png)

> [!NOTE]
> <span data-ttu-id="06d0c-233">Wie Sie in der Abbildung oben sehen können, wurden die roten Linien unter allen Bezeichnungen entfernt, was darauf hinweist, dass alle Entitätswerte vorhergesagt wurden.</span><span class="sxs-lookup"><span data-stu-id="06d0c-233">As you can see in the image above, the red lines under all the labels have been removed, indicating that all the entity values have been predicted.</span></span> <span data-ttu-id="06d0c-234">Beachten Sie außerdem, dass das Statussymbol links auf der Trainieren-Schaltfläche die Farbe von rot zu grün gewechselt hat.</span><span class="sxs-lookup"><span data-stu-id="06d0c-234">Also notice that the status icon to the left of the Train button has changed color from red to green.</span></span>

<span data-ttu-id="06d0c-235">Wenn die Verarbeitung des Trainings abgeschlossen ist, klicken Sie auf die Schaltfläche **Testen**, geben Sie dann **Fahre fort, starte die Rakete** ein, und drücken Sie die EINGABETASTE:</span><span class="sxs-lookup"><span data-stu-id="06d0c-235">When the training is finished processing, click the **Test** button, then type in **go ahead and launch the rocket** and press the Enter key:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-2.png)

<span data-ttu-id="06d0c-237">Wenn die Testäußerung verarbeitet wurde, klicken Sie auf **Prüfen**, um das Testergebnis anzuzeigen:</span><span class="sxs-lookup"><span data-stu-id="06d0c-237">When the test utterance has been processed, click **Inspect** to see the test result:</span></span>

* <span data-ttu-id="06d0c-238">Absicht: PressButton (mit einer Sicherheit von 98,5 %)</span><span class="sxs-lookup"><span data-stu-id="06d0c-238">Intent: PressButton (with a 98.5% certainty)</span></span>
* <span data-ttu-id="06d0c-239">Aktion-Entität:Fahre fort</span><span class="sxs-lookup"><span data-stu-id="06d0c-239">Action entity: go ahead</span></span>
* <span data-ttu-id="06d0c-240">Ziel-Entität: starte</span><span class="sxs-lookup"><span data-stu-id="06d0c-240">Target entity: launch</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-3.png)

<span data-ttu-id="06d0c-242">Um die App zu veröffentlichen, klicken Sie oben rechts auf die Schaltfläche **Publish** (Veröffentlichen), wählen Sie dann im Popupfenster **Choose your publishing slot and settings** (Wählen Sie Ihren Veröffentlichungsslot und Ihre Einstellungen) **Production** (Produktion) aus, und klicken Sie auf die Schaltfläche **Publish**:</span><span class="sxs-lookup"><span data-stu-id="06d0c-242">To publish the app, click the **Publish** button in the top right, then in the **Choose your publishing slot and settings** popup window, select **Production** and click the **Publish** button:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-4.png)

<span data-ttu-id="06d0c-244">Warten Sie auf den Abschluss des Veröffentlichungsprozesses:</span><span class="sxs-lookup"><span data-stu-id="06d0c-244">Wait for the publishing process to complete:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step6-5.png)

### <a name="7-assign-an-azure-prediction-resource-to-the-app"></a><span data-ttu-id="06d0c-246">7. Zuweisen einer Azure-Vorhersageressource zur App</span><span class="sxs-lookup"><span data-stu-id="06d0c-246">7. Assign an Azure prediction resource to the app</span></span>

<span data-ttu-id="06d0c-247">Navigieren Sie zur Seite Verwalten > Anwendungseinstellungen > **Azure-Ressourcen**:</span><span class="sxs-lookup"><span data-stu-id="06d0c-247">Navigate to the Manage > Application Settings > **Azure Resources** page:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-1.png)

<span data-ttu-id="06d0c-249">Klicken Sie auf der Seite „Azure-Ressourcen“ auf die Schaltfläche **Vorhersageressource hinzufügen**, und wählen Sie die folgenden Werte im Popupfenster **Ihrer App eine Ressource zuweisen** aus:</span><span class="sxs-lookup"><span data-stu-id="06d0c-249">On the Azure Resources page, click the **Add prediction resource** button and select the following values in the **Assign a resource to your app** popup window:</span></span>

* <span data-ttu-id="06d0c-250">Wählen Sie als **Mandantenname** den Namen Ihres Mandanten aus</span><span class="sxs-lookup"><span data-stu-id="06d0c-250">For **Tenant name**, select your tenant name</span></span>
* <span data-ttu-id="06d0c-251">Wählen Sie als **Abonnementname** das gleiche Abonnement aus, das Sie zuvor beim [Erstellen der Azure Language Understanding-Ressource](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource) verwendet haben</span><span class="sxs-lookup"><span data-stu-id="06d0c-251">For **Subscription Name**, select the same subscription you used earlier when [Creating the Azure Language Understanding resource](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)</span></span>
* <span data-ttu-id="06d0c-252">Wählen Sie als **Name der LUIS-Ressource** die gleiche Vorhersageressource aus, die Sie zuvor beim [Erstellen der Azure Language Understanding-Ressource](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource) erstellt haben</span><span class="sxs-lookup"><span data-stu-id="06d0c-252">For **LUIS resource name**, select the prediction resource you created earlier when [Creating the Azure Language Understanding resource](mrlearning-speechSDK-ch4.md#creating-the-azure-language-understanding-resource)</span></span>

<span data-ttu-id="06d0c-253">Klicken Sie dann auf die Schaltfläche **Ressource zuweisen**, um Ihrer App die Azure-Vorhersageressource zuzuweisen:</span><span class="sxs-lookup"><span data-stu-id="06d0c-253">Then click the **Assign resource** button to assign the Azure prediction resource to your app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-2.png)

<span data-ttu-id="06d0c-255">Wenn die Ressource zugewiesen wurde, sollte Ihre Seite „Azure-Ressourcen“ so ähnlich wie in der folgenden Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="06d0c-255">When the resource has been assigned, your Azure Resources page should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section3-step7-3.png)

## <a name="connecting-the-unity-project-to-the-luis-app"></a><span data-ttu-id="06d0c-257">Verbinden des Unity-Projekts mit der LUIS-App</span><span class="sxs-lookup"><span data-stu-id="06d0c-257">Connecting the Unity project to the LUIS app</span></span>

<span data-ttu-id="06d0c-258">Klicken Sie auf der Seite Verwalten > Anwendungseinstellungen > **Azure-Ressourcen** auf das Symbol **Kopieren**, um die **Beispielabfrage** zu kopieren:</span><span class="sxs-lookup"><span data-stu-id="06d0c-258">On the Manage > Application Settings > **Azure Resources** page, click the **copy** icon to copy the **Example Query**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-1.png)

<span data-ttu-id="06d0c-260">Wählen Sie wieder in Ihrem Unity-Projekt im Hierarchiefenster das Objekt **Lunarcom** aus, suchen Sie dann im Inspektor-Fenster die Komponente **Lunarcom Intent Recognizer (Script)** aus, und konfigurieren Sie sie wie folgt:</span><span class="sxs-lookup"><span data-stu-id="06d0c-260">Back in your Unity project, in the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Intent Recognizer (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="06d0c-261">Fügen Sie in das Feld **LUIS-Endpunkt** die **Beispielabfrage** ein, die Sie im vorherigen Schritt kopiert hatten:</span><span class="sxs-lookup"><span data-stu-id="06d0c-261">In the **LUIS Endpoint** field, past the **Example Query** you copied in the previous step:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section4-step1-2.png)

## <a name="testing-and-improving-the-intent-recognition"></a><span data-ttu-id="06d0c-263">Testen und Verbessern der Absichtserkennung</span><span class="sxs-lookup"><span data-stu-id="06d0c-263">Testing and improving the intent recognition</span></span>

<span data-ttu-id="06d0c-264">Um Absichtserkennung direkt im Unity-Editor zu verwenden, müssen Sie Ihrem Entwicklungscomputer die Verwendung der Diktatfunktion erlauben.</span><span class="sxs-lookup"><span data-stu-id="06d0c-264">To use intent recognition directly in the Unity editor, you must allow your development computer to use dictation.</span></span> <span data-ttu-id="06d0c-265">Um diese Einstellung zu überprüfen, öffnen Sie Windows **Einstellungen**, wählen Sie dann **Datenschutz** > **Sprache** aus, und vergewissern Sie sich, dass **Online-Spracherkennung** aktiviert ist:</span><span class="sxs-lookup"><span data-stu-id="06d0c-265">To verify this setting, open Windows **Settings** then choose **Privacy** > **Speech** and ensure **Online speech recognition** is turned on:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-1.png)

<span data-ttu-id="06d0c-267">Wenn Sie jetzt in den Spielmodus wechseln, können Sie die Absichtserkennung testen, indem Sie zuerst auf die Raketenschaltfläche klicken.</span><span class="sxs-lookup"><span data-stu-id="06d0c-267">If you now enter Game mode, you can test the intent recognition by first pressing the rocket button.</span></span> <span data-ttu-id="06d0c-268">Angenommen, dass Ihr Computer über ein Mikrofon verfügt, sehen Sie dann, wenn Sie die erste Beispieläußerung **Fahre fort, starte die Rakete** sprechen, dass das LunarModule in den Weltraum abhebt:</span><span class="sxs-lookup"><span data-stu-id="06d0c-268">Then, assuming your computer has a microphone, when you say the first example utterance, **go ahead and launch the rocket**, you will see the LunarModule launch into space:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-2.png)

<span data-ttu-id="06d0c-270">Probieren Sie alle **Beispieläußerungen** und dann ebenso einige **Variationen der Beispieläußerungen** sowie einige **zufällige Äußerungen** aus.</span><span class="sxs-lookup"><span data-stu-id="06d0c-270">Try all the **example utterances**, then some **variation of the example utterances**, as well as, a few **random utterances**.</span></span>

<span data-ttu-id="06d0c-271">Kehren Sie als nächstes zu <a href="https://www.luis.ai" target="_blank">LUIS</a> zurück, navigieren Sie zur Seite Erstellen > App-Leistung verbessern > **Endpunktäußerungen überprüfen**, verwenden Sie die **Umschalt**-Schaltfläche, um von der Standardansicht „Entitäten“ zur **Tokenansicht** zu wechseln, und überprüfen Sie dann die Äußerungen:</span><span class="sxs-lookup"><span data-stu-id="06d0c-271">Next, return to <a href="https://www.luis.ai" target="_blank">LUIS</a> and navigate to Build > Improve app performance > **Review endpoint utterances** page, use the **toggle** button to switch from the default Entities View to **Tokens View**, and then review the utterances:</span></span>

* <span data-ttu-id="06d0c-272">Ändern und entfernen Sie in der Spalte **Äußerungen** die zugewiesenen Bezeichnungen nach Bedarf, sodass sie sich an Ihrer Absicht orientieren</span><span class="sxs-lookup"><span data-stu-id="06d0c-272">In the **Utterance** column, change and remove the assigned labels as needed so they align with your intent</span></span>
* <span data-ttu-id="06d0c-273">Überprüfen Sie in der Spalte **Zugeordnete Absicht**, ob die Absicht richtig ist</span><span class="sxs-lookup"><span data-stu-id="06d0c-273">In the **Aligned intent** column, verify that the intent is correct</span></span>
* <span data-ttu-id="06d0c-274">Klicken Sie in der Spalte **Hinzufügen/Löschen** auf die Schaltfläche mit dem grünen Markierungshäkchen, um die Äußerung hinzuzufügen, oder auf die Schaltfläche mit dem roten X, um sie zu löschen</span><span class="sxs-lookup"><span data-stu-id="06d0c-274">In the **Add/Delete** column, click the green check mark button to add the utterance or the red x button to delete it</span></span>

<span data-ttu-id="06d0c-275">Wenn Sie so viele Äußerungen überprüft haben, wie Sie möchten, klicken Sie auf die Schaltfläche **Trainieren**, um das Modell erneut zu trainieren, und dann auf die Schaltfläche **Veröffentlichen**, um die aktualisierte App erneut zu veröffentlichen:</span><span class="sxs-lookup"><span data-stu-id="06d0c-275">When you have reviewed as many utterances as you like, click the **Train** button to retrain the model, then the **Publish** button to republish the updated app:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial4-section5-step1-3.png)

> [!NOTE]
> <span data-ttu-id="06d0c-277">Wenn sich eine Endpunktäußerung nicht an der PressButton-Absicht orientiert, Sie aber möchten, dass für die Äußerung keine Absicht gilt, können Sie die zugewiesene Absicht in Keine ändern.</span><span class="sxs-lookup"><span data-stu-id="06d0c-277">If an endpoint utterance does not align with the PressButton intent, but you would like your model to know that the utterance has no intent, you can change the Aligned intent to None.</span></span>

<span data-ttu-id="06d0c-278">**Wiederholen** Sie diesen Vorgang so oft, wie Sie möchten, um Ihr App-Modell zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="06d0c-278">**Repeat** this process as many times as you like to improve your app model.</span></span>

## <a name="congratulations"></a><span data-ttu-id="06d0c-279">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="06d0c-279">Congratulations</span></span>

<span data-ttu-id="06d0c-280">Ihr Projekt verfügt jetzt über KI-gestützte Sprachbefehle, die es Ihrer Anwendung ermöglichen, die Absicht der Benutzer auch dann zu erkennen, wenn sie keine präzisen Befehle äußern.</span><span class="sxs-lookup"><span data-stu-id="06d0c-280">Your project now have AI-powered speech commands, allowing your application to recognize the users' intent even if they do not utter precise commands.</span></span> <span data-ttu-id="06d0c-281">Führen Sie die Anwendung auf Ihrem Gerät aus, um sicherzustellen, dass das Feature ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="06d0c-281">Run the application on your device to ensure the feature is working properly.</span></span>
