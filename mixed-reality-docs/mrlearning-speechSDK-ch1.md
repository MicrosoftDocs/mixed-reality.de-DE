# <a name="speech-sdk-learning-module"></a><span data-ttu-id="fcf18-101">Spracherkennungs-SDK-Learning-Modul</span><span class="sxs-lookup"><span data-stu-id="fcf18-101">Speech SDK Learning Module</span></span>

<span data-ttu-id="fcf18-102">In diesem Tutorial erstellen Sie eine Mixed Reality-Anwendung, die die Verwendung von Azure Cognitive Services Speech SDK mit dem HoloLens 2 untersucht.</span><span class="sxs-lookup"><span data-stu-id="fcf18-102">In this tutorial you will create a Mixed Reality application that explores the use of Azure Cognitive Services Speech SDK with the HoloLens 2.</span></span> <span data-ttu-id="fcf18-103">Wenn in dieser tutorialreihe abgeschlossen ist, werden Sie verwenden Ihre Gerätemikrofon Spracherkennung in Echtzeit zu transkribieren und übersetzen die Spracherkennung in andere Sprachen nutzen die Speech SDK beabsichtigte Funktion mit Sprachbefehle verstehen künstliche Intelligenz.</span><span class="sxs-lookup"><span data-stu-id="fcf18-103">When finished with this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Speech SDK’s Intent feature to understand voice commands using artificial intelligence.</span></span>

<span data-ttu-id="fcf18-104">Ziele:</span><span class="sxs-lookup"><span data-stu-id="fcf18-104">Objectives:</span></span>

- <span data-ttu-id="fcf18-105">Erfahren Sie, wie das Azure-Spracherkennungs-SDK in eine HoloLens-2-Anwendung zu integrieren.</span><span class="sxs-lookup"><span data-stu-id="fcf18-105">Learn how to integrate the Azure Speech SDK into a HoloLens 2 application</span></span>
- <span data-ttu-id="fcf18-106">Erfahren Sie, wie Sie mithilfe von Sprachbefehlen</span><span class="sxs-lookup"><span data-stu-id="fcf18-106">Learn how to use voice commands</span></span>
- <span data-ttu-id="fcf18-107">Informationen Sie zum Verwenden von Sprache-zu-Text-Funktionen</span><span class="sxs-lookup"><span data-stu-id="fcf18-107">Learn how to use speech-to-text capabilities</span></span>

## <a name="instructions"></a><span data-ttu-id="fcf18-108">Anweisungen</span><span class="sxs-lookup"><span data-stu-id="fcf18-108">Instructions</span></span>

### <a name="getting-started"></a><span data-ttu-id="fcf18-109">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="fcf18-109">Getting Started</span></span>

1. <span data-ttu-id="fcf18-110">Starten Sie Unity aus, und Erstellen eines neuen Projekts.</span><span class="sxs-lookup"><span data-stu-id="fcf18-110">Start Unity and create a new project.</span></span> <span data-ttu-id="fcf18-111">Geben Sie den Namen des Projekts "Speech SDK Lernmodul."</span><span class="sxs-lookup"><span data-stu-id="fcf18-111">Enter the project name “Speech SDK Learning Module.”</span></span> <span data-ttu-id="fcf18-112">Wählen Sie einen Speicherort, an die Ihr Projekt zu speichern.</span><span class="sxs-lookup"><span data-stu-id="fcf18-112">Choose a location for where to save your project.</span></span> <span data-ttu-id="fcf18-113">Klicken Sie dann auf "Create Project".</span><span class="sxs-lookup"><span data-stu-id="fcf18-113">Then click "Create Project."</span></span>

![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

> <span data-ttu-id="fcf18-115">Hinweis: Stellen Sie sicher, dass die Vorlage "3D" festgelegt ist, wie in der Abbildung oben gezeigt.</span><span class="sxs-lookup"><span data-stu-id="fcf18-115">Note: Ensure that the template is set to "3D," as shown in the image above.</span></span>

2. <span data-ttu-id="fcf18-116">Herunterladen der [Mixed Reality-Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity-Paket, und speichern Sie es in einem Ordner auf Ihrem PC.</span><span class="sxs-lookup"><span data-stu-id="fcf18-116">Download the [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity package and save it to a folder on your PC.</span></span> <span data-ttu-id="fcf18-117">Importieren Sie das Paket in Ihr Unity-Projekt ein.</span><span class="sxs-lookup"><span data-stu-id="fcf18-117">Import the package into your Unity project.</span></span> <span data-ttu-id="fcf18-118">Ausführliche Anleitungen hierzu finden Sie unter [Basismodul Lektion 1](mrlearning-base-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="fcf18-118">For detailed instructions on how to do this, please see [base module lesson 1](mrlearning-base-ch1.md).</span></span> 

3. <span data-ttu-id="fcf18-119">Herunterladen und importieren Sie das Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) für Unity Asset-Paket.</span><span class="sxs-lookup"><span data-stu-id="fcf18-119">Download and import the Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) for Unity asset package.</span></span> <span data-ttu-id="fcf18-120">Importieren Sie das Speech SDK-Paket durch Klicken auf "Ressourcen", "Paket importieren," Wählen Sie dann auf "benutzerdefinierte Package" auswählen</span><span class="sxs-lookup"><span data-stu-id="fcf18-120">Import the Speech SDK package by clicking on "assets," selecting "import package," then selecting "custom package."</span></span> <span data-ttu-id="fcf18-121">Ermitteln Sie die zuvor heruntergeladene Speech SDK-Paket aus, und öffnen Sie sie um den Importvorgang zu starten.</span><span class="sxs-lookup"><span data-stu-id="fcf18-121">Find the Speech SDK package downloaded earlier and open it to begin the importing process.</span></span> 

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. <span data-ttu-id="fcf18-123">Klicken Sie im nächsten Popup-Fenster auf "Import" zum Importieren von dem Speech SDK-Paket.</span><span class="sxs-lookup"><span data-stu-id="fcf18-123">In the next pop-up window, click “Import” to begin importing the Speech SDK package.</span></span> <span data-ttu-id="fcf18-124">Stellen Sie sicher, dass alle Elemente aktiviert sind, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="fcf18-124">Ensure all items are checked, as shown in the image below.</span></span>

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)


5. <span data-ttu-id="fcf18-126">Herunterladen der [Lunarcom](https://github.com/levilais/Speech-SDK-Module/raw/master/Speech SDK Module/Lunarcom.unitypackage) Asset-Paket.</span><span class="sxs-lookup"><span data-stu-id="fcf18-126">Download the [Lunarcom](https://github.com/levilais/Speech-SDK-Module/raw/master/Speech SDK Module/Lunarcom.unitypackage) asset package.</span></span> <span data-ttu-id="fcf18-127">Das Lunarcom-Asset-Paket ist eine Sammlung von Ressourcen und Skripts, die für diese Lektion Reihe entwickelt, eine praktische Verwendung von Azure Speech SDK zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="fcf18-127">The Lunarcom asset package is a collection of assets and scripts developed for this lesson series to showcase a practical use of Azure's Speech SDK.</span></span> <span data-ttu-id="fcf18-128">Es ist ein Voice-Command-Terminal, letztendlich mit der die Mondkalender Modul Assembly Erfahrung in entwickelt werden die [Base Modul Tutorial.](mrlearning-base-ch6.md)</span><span class="sxs-lookup"><span data-stu-id="fcf18-128">It is a voice-command terminal that will ultimately interface with the lunar module assembly experience developed in the [Base Module Tutorial.](mrlearning-base-ch6.md)</span></span>
6. <span data-ttu-id="fcf18-129">Importieren Sie das Lunarcom Asset-Paket in Ihr Unity-Projekt, indem Sie ähnliche Schritte, die Sie vorgenommen haben, um die Mixed Reality-Toolkit und dem Speech SDK zu importieren.</span><span class="sxs-lookup"><span data-stu-id="fcf18-129">Import the Lunarcom asset package into your Unity project by following similar steps you took to import the Mixed Reality Toolkit and Speech SDK.</span></span>
7. <span data-ttu-id="fcf18-130">Konfigurieren Sie die Mixed Reality-Toolkits (MRTK).</span><span class="sxs-lookup"><span data-stu-id="fcf18-130">Configure the Mixed Reality Toolkit (MRTK).</span></span> <span data-ttu-id="fcf18-131">Zu diesem Zweck klicken Sie auf den Bereich "Mixed Reality-Toolkit" in der oberen Rand des Fensters, und wählen Sie dann auf "Hinzufügen der Szene" und "konfigurieren".</span><span class="sxs-lookup"><span data-stu-id="fcf18-131">To do this, click on the "Mixed Reality Toolkit" panel in the top of your window, and then select "Add to Scene and Configure."</span></span>

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

8. <span data-ttu-id="fcf18-133">Die Szene wird nun mehrere neue Elemente aus der MRTK enthalten.</span><span class="sxs-lookup"><span data-stu-id="fcf18-133">Your scene will now have several new items in it from the MRTK.</span></span> <span data-ttu-id="fcf18-134">Speichern Sie Ihre Szene unter einem anderen Namen durch Klicken auf "File" "Speichern unter" klicken Sie dann, und nennen Sie die Szene "SpeechScene" an.</span><span class="sxs-lookup"><span data-stu-id="fcf18-134">Save your scene under a different name by clicking on "file," then "save as" and name your scene “SpeechScene”.</span></span> 

   > <span data-ttu-id="fcf18-135">Hinweis: Wenn Sie die entsprechende Schaltfläche in der Szene drücken, nachdem Sie die MRTK zu Ihrem Projekt hinzufügen und sie nicht den Modus "Wiedergabe" eingeben, müssen Sie Unity neu zu starten.</span><span class="sxs-lookup"><span data-stu-id="fcf18-135">Note: If you press the play button on your scene after you add the MRTK to your project, and it doesn't enter the "play" mode, you may need to restart Unity.</span></span> 

9. <span data-ttu-id="fcf18-136">Klicken Sie mit dem "MixedRealityToolkit"-Objekt, das in der Hierarchie ausgewählt ist auf "kopieren und Anpassen von" in den Bereich der Eigenschaftenanalyse.</span><span class="sxs-lookup"><span data-stu-id="fcf18-136">With the “MixedRealityToolkit" object selected in your hierarchy, click "copy and customize" in the inspector panel.</span></span>

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. <span data-ttu-id="fcf18-138">Auch im Bereich Inspector (mit dem "MixedRealityToolkit"-Objekt, das in der Hierarchie ausgewählt ist), indem Sie das Kontrollkästchen rechts neben "Aktivieren der Diagnose-System". deaktivieren Sie das Diagnostics-system</span><span class="sxs-lookup"><span data-stu-id="fcf18-138">Also in the inspector panel (with the “MixedRealityToolkit" object selected in your hierarchy), disable the diagnostics system by unchecking the box to the right of "Enable Diagnostics System."</span></span>

![Module4Chapter1step10im](images/module4chapter1step10im.PNG)

11. <span data-ttu-id="fcf18-140">Klicken Sie im Projektpanel erweitern Sie den Ordner "Lunarcom", und ziehen Sie das Prefab "Lunarcom_Base" in Ihrer Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="fcf18-140">In the project panel, expand the "Lunarcom" folder and drag the "Lunarcom_Base" prefab into your hierarchy.</span></span>

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

12. <span data-ttu-id="fcf18-142">Wählen Sie das Objekt "Lunarcom_Base" in Ihrer Hierarchie und stellen Sie sicher, dass die Position, auf x festgelegt ist = 0, y = 0 und Z = 0, sowie die Drehung, legen Sie auf X = 0, y = 0 und Z = 0.</span><span class="sxs-lookup"><span data-stu-id="fcf18-142">Select the "Lunarcom_Base" object in your hierarchy and ensure that the position is set to x=0, y=0, and z=0, as well as the rotation set to x=0, y=0, and z=0.</span></span> <span data-ttu-id="fcf18-143">Die Skalierungsgruppe lesen X = 0,008 Dollar, y = 0,008-Dollar und Z = 0,01.</span><span class="sxs-lookup"><span data-stu-id="fcf18-143">Set the scale to read x=0.008, y=0.008, and z=0.01.</span></span>

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

13. <span data-ttu-id="fcf18-145">Klicken Sie auf "Komponente hinzufügen", und suchen Sie nach, und wählen Sie "LunarcomController."</span><span class="sxs-lookup"><span data-stu-id="fcf18-145">Click "add component" and search for and select “LunarcomController.”</span></span> <span data-ttu-id="fcf18-146">Dieses Skript ist in der Lunarcom ressourcenpaket enthalten, die Sie in Schritt 6 importiert.</span><span class="sxs-lookup"><span data-stu-id="fcf18-146">This script is included in the Lunarcom asset pack that you imported in Step 6.</span></span>

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

14. <span data-ttu-id="fcf18-148">Um die app mit Azure Cognitive Services verbinden zu können, müssen Sie einen "Subscription-Key" auch bekannt als "API-Key" für den Dienst der Sprache eingeben.</span><span class="sxs-lookup"><span data-stu-id="fcf18-148">To connect our app to Azure Cognitive Services, you must enter a "subscription key" also known as an "API Key" for the Speech Service.</span></span> <span data-ttu-id="fcf18-149">Befolgen Sie die Anweisungen unter [diesen Link](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started) um ein kostenloses Abonnement-Schlüssel zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="fcf18-149">Follow the instructions at [this link](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started) to obtain a free subscription key.</span></span> <span data-ttu-id="fcf18-150">Nachdem Sie den Abonnementschlüssel erhalten haben, geben Sie ihn in das Feld "Speech-Dienst-API-Key" der Komponente "LunarcomController" im Bereich mit den Inspektor wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="fcf18-150">Once you obtain the subscription key, enter it into the “Speech Service API Key” field of the "LunarcomController" component in the inspector panel, as shown in the image below.</span></span>

15. <span data-ttu-id="fcf18-151">Geben Sie die Region, die Sie ausgewählt haben, wenn Sie für den Abonnementschlüssel in das Feld "Speech Service-Region", der im Bedienfeld "Inspector" Komponente "LunarcomController" registriert haben.</span><span class="sxs-lookup"><span data-stu-id="fcf18-151">Enter the Region that you chose when you signed up for the subscription key into the “Speech Service Region” field of the "LunarcomController" component in the inspector panel.</span></span>

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

16. <span data-ttu-id="fcf18-153">Klicken Sie in Ihrer Hierarchie erweitern Sie das Objekt "Lunarcom_Base" durch Klicken auf den Pfeil, um die links von ihm, und Gleiches gilt für das untergeordnete Objekt, "Terminaldienste", wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="fcf18-153">In your hierarchy, expand the "Lunarcom_Base" object by clicking the arrow to the left of it, then do the same for its child object, "Terminal" as shown in the image below.</span></span>

17. <span data-ttu-id="fcf18-154">Wenn "Lunarcom_Base" ausgewählt ist, klicken Sie, und ziehen Sie "Lunarcom Text" aus der Hierarchie im Slot "Ausgabetext" in der Komponente "LunarcomController" im Bereich mit den Inspektor, wie in der folgenden Abbildung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="fcf18-154">While "Lunarcom_Base" is selected, click and drag “Lunarcom Text” from the hierarchy to the "Output Text" slot in the "LunarcomController" component in the inspector panel, as shown in the image below.</span></span>
18. <span data-ttu-id="fcf18-155">Führen Sie dieselben Schritte mit dem Objekt "Terminalserver" nun in den Slot "Terminaldienste" und das Objekt "Verbindung Light" im Slot "Verbindung Light-Controller".</span><span class="sxs-lookup"><span data-stu-id="fcf18-155">Now do the same thing with the "Terminal" object into the "terminal" slot and the "Connection Light" object to the "Connection Light Controller" slot.</span></span>

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

19. <span data-ttu-id="fcf18-157">Klicken Sie auf den Pfeil neben "Lunarcom Schaltflächen"-Abschnitt des Skripts "LunarcomController" in den Bereich der Eigenschaftenanalyse, und Ändern der Größe nach 3, und drücken Sie die EINGABETASTE oder die Return-Taste auf der Tastatur.</span><span class="sxs-lookup"><span data-stu-id="fcf18-157">Click the arrow next to the "Lunarcom Buttons" section of the "LunarcomController" script in the inspector panel and change the size to 3 and press the Enter or Return key on your keyboard.</span></span> <span data-ttu-id="fcf18-158">Dadurch werden drei neue "Element"-Felder angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="fcf18-158">This will cause three new "Element" fields to appear.</span></span>

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

20. <span data-ttu-id="fcf18-160">Erweitern Sie die "Lunarcom Schaltflächen" durch Klicken auf den Pfeil daneben in Ihrer Hierarchie Drag & Drop, verwenden die gleiche Vorgehensweise wie oben beschrieben, die Mic Satelliten und Rocket "gameobjects", 0, 1 und 2 Elementverweise bzw. in der "LunarcomController"-Komponente in der Bereich der Eigenschaftenanalyse.</span><span class="sxs-lookup"><span data-stu-id="fcf18-160">Expand the "Lunarcom Buttons" by clicking the arrow next to it in your hierarchy and, using the same process as above, drag the Mic, Satellite, and Rocket gameobjects to the Element 0, 1, and 2 references respectively in the "LunarcomController" component in the inspector panel.</span></span> 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

21. <span data-ttu-id="fcf18-162">Wählen Sie das "Lunarcom_Base"-Objekt, in der Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="fcf18-162">Select the "Lunarcom_Base" object in your hierarchy.</span></span> <span data-ttu-id="fcf18-163">Klicken Sie auf "Komponente hinzufügen" im Bedienfeld "Inspector", und suchen Sie nach, und wählen Sie "LunarcomWakeWordRecognizer."</span><span class="sxs-lookup"><span data-stu-id="fcf18-163">Click “Add Component” in the inspector panel and search for and select “LunarcomWakeWordRecognizer.”</span></span>

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

22. <span data-ttu-id="fcf18-165">Geben Sie in den Slot "Wake Wort" "Aktivieren von Terminal".</span><span class="sxs-lookup"><span data-stu-id="fcf18-165">In the "Wake Word" slot, type in "Activate Terminal."</span></span> <span data-ttu-id="fcf18-166">Darüber hinaus im Slot "Wort schließen", geben Sie in "Verwerfen Terminal".</span><span class="sxs-lookup"><span data-stu-id="fcf18-166">Also, in the "Dismiss Word" slot, type in "Dismiss Terminal."</span></span>

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

## <a name="congratulations"></a><span data-ttu-id="fcf18-168">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="fcf18-168">Congratulations</span></span>

<span data-ttu-id="fcf18-169">Sie haben in Ihrer Anwendung, mit der Azure Spracherkennung eingerichtet!</span><span class="sxs-lookup"><span data-stu-id="fcf18-169">You've set up voice recognition in your application, powered by Azure!</span></span> <span data-ttu-id="fcf18-170">Führen Sie die Anwendung aus, um sicherzustellen, dass alle Funktionen ordnungsgemäß funktionieren.</span><span class="sxs-lookup"><span data-stu-id="fcf18-170">Run the application to ensure all functions are working properly.</span></span> <span data-ttu-id="fcf18-171">Beginnen Sie mit der Aktivierung Wort, die Sie in Schritt 22, "Aktivieren-Terminal." eingegeben</span><span class="sxs-lookup"><span data-stu-id="fcf18-171">Start with saying the wake word you typed in step 22, "Activate Terminal."</span></span> <span data-ttu-id="fcf18-172">Wählen Sie dann die Schaltfläche "Mikrofon", starten Sie die Spracherkennung und beginnen, sprechen.</span><span class="sxs-lookup"><span data-stu-id="fcf18-172">Then, select the microphone button to start voice recognition and begin speaking.</span></span> <span data-ttu-id="fcf18-173">Sie sehen, die Wörter im Terminal transkribiert, wie Sie sprechen.</span><span class="sxs-lookup"><span data-stu-id="fcf18-173">You will see your words transcribed in the terminal as you speak.</span></span> <span data-ttu-id="fcf18-174">Drücken Sie die Schaltfläche "Mikrofon" ein zweites Mal, um die Spracherkennung zu beenden.</span><span class="sxs-lookup"><span data-stu-id="fcf18-174">Press the microphone button a second time to stop voice recognition.</span></span> <span data-ttu-id="fcf18-175">Nehmen wir an "Terminal schließen", um das Terminal Lunarcom auszublenden.</span><span class="sxs-lookup"><span data-stu-id="fcf18-175">Say "Dismiss Terminal" to hide the Lunarcom terminal.</span></span> <span data-ttu-id="fcf18-176">In der nächsten Lektion erfahren wir, wie dynamisch wechseln Sie zur Verwendung von Gerät-gestützte Spracherkennung für Situationen, in dem Azure Sprach-SDKS nicht aufgrund der HoloLens-2, die offline verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="fcf18-176">In the next lesson, we'll learn how to dynamically switch to using device-powered voice recognition, for situations where Azure's speech SDK isn't available due to the HoloLens 2 being offline.</span></span>

[<span data-ttu-id="fcf18-177">Nächste Lektion: Speech SDK Lektion 2</span><span class="sxs-lookup"><span data-stu-id="fcf18-177">Next Lesson: Speech SDK Lesson 2</span></span>](mrlearning-speechSDK-ch2.md)
