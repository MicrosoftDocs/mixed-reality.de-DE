---
title: Spracheingabe in DirectX
description: Erläutert, wie zur Implementierung von Sprachbefehlen und kleine Ausdruck und satzbegrenzungszeichen verwendet in einer DirectX-app für Windows Mixed Reality.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Exemplarische Vorgehensweise, Sprachbefehl, Ausdruck, Erkennung, Spracherkennung, Directx, Plattform, Cortana, Windows mixed reality
ms.openlocfilehash: 728457a495616e5f65ec3986dfb6ac60231f9e46
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605104"
---
# <a name="voice-input-in-directx"></a><span data-ttu-id="09329-104">Spracheingabe in DirectX</span><span class="sxs-lookup"><span data-stu-id="09329-104">Voice input in DirectX</span></span>

<span data-ttu-id="09329-105">In diesem Thema wird erläutert, wie implementieren [Sprachbefehle](voice-input.md), und klein Ausdruck und Satz Anerkennung in einer DirectX-app für Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="09329-105">This topic explains how to implement [voice commands](voice-input.md), and small phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="09329-106">Die Codeausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstatt C ++ 17-kompatible C++"/ WinRT", wie in der [ C++ holographic Projektvorlage](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="09329-106">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="09329-107">Die Konzepte sind Entsprechung für einen C++"/ WinRT"-Projekt, aber Sie benötigen, um den Code zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="09329-107">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a><span data-ttu-id="09329-108">Verwenden Sie eine SpeechRecognizer für kontinuierliche Erkennung von Stimmbefehlen</span><span class="sxs-lookup"><span data-stu-id="09329-108">Use a SpeechRecognizer for continuous recognition of voice commands</span></span>

<span data-ttu-id="09329-109">In diesem Abschnitt beschrieben, wie kontinuierliche Spracherkennung zu verwenden, um Sprachbefehle in Ihrer app zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="09329-109">In this section, we describe how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="09329-110">In dieser exemplarischen Vorgehensweise verwendet den Code aus der [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) Beispiel.</span><span class="sxs-lookup"><span data-stu-id="09329-110">This walkthrough uses code from the [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) Sample.</span></span> <span data-ttu-id="09329-111">Wenn das Beispiel ausgeführt wird, sprechen Sie den Namen einer der Befehle zum Ändern der Farbe der sich drehenden Würfels registrierten Farbe.</span><span class="sxs-lookup"><span data-stu-id="09329-111">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="09329-112">Erstellen Sie zunächst ein neues **Windows::Media::SpeechRecognition::SpeechRecognizer** Instanz.</span><span class="sxs-lookup"><span data-stu-id="09329-112">First, create a new **Windows::Media::SpeechRecognition::SpeechRecognizer** instance.</span></span>

<span data-ttu-id="09329-113">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span><span class="sxs-lookup"><span data-stu-id="09329-113">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="09329-114">Sie müssen eine Liste mit Befehlen der Sprache für das Erkennungsmodul zum Lauschen auf zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="09329-114">You'll need to create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="09329-115">Hier erstellen wir eine Reihe von Befehlen zum Ändern der Farbe der ggf. ein Hologramm.</span><span class="sxs-lookup"><span data-stu-id="09329-115">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="09329-116">Aus Gründen der Einfachheit halber erstellen wir auch die Daten, die wir für die Befehle später verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="09329-116">For the sake of convenience, we also create the data that we'll use for the commands later on.</span></span>

```
m_speechCommandList = ref new Platform::Collections::Vector<String^>();
   m_speechCommandData.clear();
   m_speechCommandList->Append(StringReference(L"white"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"grey"));
   m_speechCommandData.push_back(float4(0.5f, 0.5f, 0.5f, 1.f));
   m_speechCommandList->Append(StringReference(L"green"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"black"));
   m_speechCommandData.push_back(float4(0.1f, 0.1f, 0.1f, 1.f));
   m_speechCommandList->Append(StringReference(L"red"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"yellow"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"aquamarine"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"blue"));
   m_speechCommandData.push_back(float4(0.f, 0.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"purple"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 1.f, 1.f));
```

<span data-ttu-id="09329-117">Befehle können phonetische Wörter verwenden, die in einem Wörterbuch möglicherweise nicht angegeben werden:</span><span class="sxs-lookup"><span data-stu-id="09329-117">Commands can be specified using phonetic words that might not be in a dictionary:</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="09329-118">Die Liste der Befehle wird in die Liste der Einschränkungen für die Spracherkennung geladen.</span><span class="sxs-lookup"><span data-stu-id="09329-118">The list of commands is loaded into the list of constraints for the speech recognizer.</span></span> <span data-ttu-id="09329-119">Dies erfolgt mithilfe einer [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) Objekt.</span><span class="sxs-lookup"><span data-stu-id="09329-119">This is done by using a [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) object.</span></span>

```
SpeechRecognitionListConstraint^ spConstraint = ref new SpeechRecognitionListConstraint(m_speechCommandList);
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(spConstraint);
   create_task(m_speechRecognizer->CompileConstraintsAsync()).then([this](SpeechRecognitionCompilationResult^ compilationResult)
   {
       if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
       {
           m_speechRecognizer->ContinuousRecognitionSession->StartAsync();
       }
       else
       {
           // Handle errors here.
       }
   });
```

<span data-ttu-id="09329-120">Abonnieren Sie den [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) Ereignis für der Spracherkennung [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span><span class="sxs-lookup"><span data-stu-id="09329-120">Subscribe to the [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) event on the speech recognizer's [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span></span> <span data-ttu-id="09329-121">Dieses Ereignis wird Ihre app benachrichtigt, wenn einer der Befehle erkannt wurde.</span><span class="sxs-lookup"><span data-stu-id="09329-121">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="09329-122">Ihre **OnResultGenerated** Ereignishandler empfängt Ereignisdaten in einer [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) Instanz.</span><span class="sxs-lookup"><span data-stu-id="09329-122">Your **OnResultGenerated** event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instance.</span></span> <span data-ttu-id="09329-123">Wenn das Vertrauen größer als der Schwellenwert, die Sie definiert haben ist, sollte Ihre app Beachten Sie, dass das Ereignis aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="09329-123">If the confidence is greater than the threshold you have defined, your app should note that the event happened.</span></span> <span data-ttu-id="09329-124">Speichern Sie die Ereignisdaten, sodass Sie vornehmen können, es in einer Schleife nachfolgende Aktualisierung verwenden.</span><span class="sxs-lookup"><span data-stu-id="09329-124">Save the event data so that you can make use of it in a subsequent update loop.</span></span>

<span data-ttu-id="09329-125">From *HolographicVoiceInputSampleMain.cpp*:</span><span class="sxs-lookup"><span data-stu-id="09329-125">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

```
// Change the cube color, if we get a valid result.
   void HolographicVoiceInputSampleMain::OnResultGenerated(SpeechContinuousRecognitionSession ^sender, SpeechContinuousRecognitionResultGeneratedEventArgs ^args)
   {
       if (args->Result->RawConfidence > 0.5f)
       {
           m_lastCommand = args->Result->Text;
       }
   }
```

<span data-ttu-id="09329-126">Stellen Sie jedoch Ihr app-Szenario für Daten verwenden.</span><span class="sxs-lookup"><span data-stu-id="09329-126">Make use of the data however applicable to your app scenario.</span></span> <span data-ttu-id="09329-127">In unserem Beispielcode ändern wir die Farbe des – Hologramm sich drehenden Würfels gemäß des Benutzers-Befehl.</span><span class="sxs-lookup"><span data-stu-id="09329-127">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="09329-128">From *HolographicVoiceInputSampleMain::Update*:</span><span class="sxs-lookup"><span data-stu-id="09329-128">From *HolographicVoiceInputSampleMain::Update*:</span></span>

```
// Check for new speech input since the last frame.
   if (m_lastCommand != nullptr)
   {
       auto command = m_lastCommand;
       m_lastCommand = nullptr;

       int i = 0;
       for each (auto& iter in m_speechCommandList)
       {
           if (iter == command)
           {
               m_spinningCubeRenderer->SetColor(m_speechCommandData[i]);
               break;
           }

           ++i;
       }
   }
```

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a><span data-ttu-id="09329-129">Verwenden Sie für die One-Shot-Erkennung von Sprache Ausdrücken und Sätzen Diktat</span><span class="sxs-lookup"><span data-stu-id="09329-129">Use dictation for one-shot recognition of speech phrases and sentences</span></span>

<span data-ttu-id="09329-130">Sie können eine Spracherkennung zum Lauschen auf Ausdrücke oder Sätze gesprochen, die vom Benutzer konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="09329-130">You can configure a speech recognizer to listen for phrases or sentences spoken by the user.</span></span> <span data-ttu-id="09329-131">In diesem Fall verwenden wir eine SpeechRecognitionTopicConstraint, der angibt, welche Art von Eingabe zu erwarten, dass der freigegebene Spracherkennung.</span><span class="sxs-lookup"><span data-stu-id="09329-131">In this case, we apply a SpeechRecognitionTopicConstraint that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="09329-132">Der app-Workflow ist wie folgt, und für diese Art von Anwendungsfall:</span><span class="sxs-lookup"><span data-stu-id="09329-132">The app workflow is as follows, for this type of use case:</span></span>
1. <span data-ttu-id="09329-133">Ihre app erstellt die SpeechRecognizer, Benutzeroberfläche-eingabeaufforderungen bietet und beginnt die Überwachung für einen Befehl aus, um sofort gesprochen werden.</span><span class="sxs-lookup"><span data-stu-id="09329-133">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a command to be spoken immediately.</span></span>
2. <span data-ttu-id="09329-134">Der Benutzer spricht einen Ausdruck oder Satz.</span><span class="sxs-lookup"><span data-stu-id="09329-134">The user speaks a phrase, or sentence.</span></span>
3. <span data-ttu-id="09329-135">Erkennung des Benutzers Spracheingabe wird ausgeführt, und ein Ergebnis an die app zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="09329-135">Recognition of the user's speech is performed, and a result is returned to the app.</span></span> <span data-ttu-id="09329-136">An diesem Punkt sollten Ihre app bereitstellen, Benutzeroberflächen-Eingabeaufforderung, der angibt, dass die Erkennung aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="09329-136">At this point, your app should provide a UI prompt indicating that recognition has occurred.</span></span>
4. <span data-ttu-id="09329-137">Abhängig von der Vertrauensgrad, die, dem Sie beantworten möchten, und der Vertrauensgrad, der das Erkennungsergebnis für die Sprache, kann Ihre app Verarbeiten des Ergebnisses und entsprechend reagieren.</span><span class="sxs-lookup"><span data-stu-id="09329-137">Depending on the confidence level you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="09329-138">Dieser Abschnitt beschreibt, wie Sie eine SpeechRecognizer erstellen, Kompilieren die Einschränkung und die Spracheingabe lauschen.</span><span class="sxs-lookup"><span data-stu-id="09329-138">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="09329-139">Der folgende Code kompiliert die Thema-Einschränkung, die in diesem Fall für die Suche im Web optimiert ist.</span><span class="sxs-lookup"><span data-stu-id="09329-139">The following code compiles the topic constraint, which in this case is optimized for Web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="09329-140">Wenn die Kompilierung erfolgreich war, können Sie mit der Spracherkennung fortfahren.</span><span class="sxs-lookup"><span data-stu-id="09329-140">If compilation succeeds, we can proceed with speech recognition.</span></span>

```
try
       {
           SpeechRecognitionCompilationResult^ compilationResult = previousTask.get();

           // Check to make sure that the constraints were in a proper format and the recognizer was able to compile it.
           if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
           {
               // If the compilation succeeded, we can start listening for the user's spoken phrase or sentence.
               create_task(m_speechRecognizer->RecognizeAsync()).then([this](task<SpeechRecognitionResult^>& previousTask)
               {
```

<span data-ttu-id="09329-141">Das Ergebnis wird dann an die app zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="09329-141">The result is then returned to the app.</span></span> <span data-ttu-id="09329-142">Wenn wir sicher genug ist, im Ergebnis sind, können wir den Befehl verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="09329-142">If we are confident enough in the result, we can process the command.</span></span> <span data-ttu-id="09329-143">Dieses Codebeispiel werden Ergebnisse mindestens mittlere zuverlässig verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="09329-143">This code example processes results with at least Medium confidence.</span></span>

```
try
                   {
                       auto result = previousTask.get();

                       if (result->Status != SpeechRecognitionResultStatus::Success)
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech recognition was not successful: ") +
                               result->Status.ToString()->Data() +
                               L"\n"
                               );
                       }

                       // In this example, we look for at least medium confidence in the speech result.
                       if ((result->Confidence == SpeechRecognitionConfidence::High) ||
                           (result->Confidence == SpeechRecognitionConfidence::Medium))
                       {
                           // If the user said a color name anywhere in their phrase, it will be recognized in the
                           // Update loop; then, the cube will change color.
                           m_lastCommand = result->Text;

                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech phrase was: ") +
                               m_lastCommand->Data() +
                               L"\n"
                               );
                       }
                       else
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Recognition confidence not high enough: ") +
                               result->Confidence.ToString()->Data() +
                               L"\n"
                               );
                       }
                   }
```

<span data-ttu-id="09329-144">Wenn Sie die Spracherkennung verwenden, sollten Sie für Ausnahmen achten, die hinweisen, dass das Mikrofon in den Systemeinstellungen für den Datenschutz der Benutzer deaktiviert hat.</span><span class="sxs-lookup"><span data-stu-id="09329-144">Whenever you use speech recognition, you should watch for exceptions that could indicate the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="09329-145">Dies kann während der Initialisierung oder während der Erkennung vorkommen.</span><span class="sxs-lookup"><span data-stu-id="09329-145">This can happen during initialization, or during recognition.</span></span>

```
catch (Exception^ exception)
                   {
                       // Note that if you get an "Access is denied" exception, you might need to enable the microphone
                       // privacy setting on the device and/or add the microphone capability to your app manifest.

                       PrintWstringToDebugConsole(
                           std::wstring(L"Speech recognizer error: ") +
                           exception->ToString()->Data() +
                           L"\n"
                           );
                   }
               });

               return true;
           }
           else
           {
               OutputDebugStringW(L"Could not initialize predefined grammar speech engine!\n");

               // Handle errors here.
               return false;
           }
       }
       catch (Exception^ exception)
       {
           // Note that if you get an "Access is denied" exception, you might need to enable the microphone
           // privacy setting on the device and/or add the microphone capability to your app manifest.

           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to initialize predefined grammar speech engine:") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
           return false;
       }
   });
```

<span data-ttu-id="09329-146">**HINWEIS:** Es gibt einige vordefinierte [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) zur Optimierung der Spracherkennung verfügbar.</span><span class="sxs-lookup"><span data-stu-id="09329-146">**NOTE:** There are several predefined [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) available for optimizing speech recognition.</span></span>
* <span data-ttu-id="09329-147">Wenn Sie die für Diktat optimieren möchten, verwenden Sie das Diktieren-Szenario:</span><span class="sxs-lookup"><span data-stu-id="09329-147">If you want to optimize for dictation, use the Dictation scenario:</span></span>

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* <span data-ttu-id="09329-148">Verwendung von Spracherkennung Web gesucht werden soll, können Sie eine Web-spezifischen Szenario Einschränkung wie folgt:</span><span class="sxs-lookup"><span data-stu-id="09329-148">When using speech to perform a Web search, you can use a Web-specific scenario constraint as follows:</span></span>

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* <span data-ttu-id="09329-149">Verwenden Sie die Form-Einschränkung, um das Ausfüllen von Formularen.</span><span class="sxs-lookup"><span data-stu-id="09329-149">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="09329-150">In diesem Fall empfiehlt es sich um Ihre eigenen Grammatik anzuwenden, die für das Formular ausfüllen optimiert ist.</span><span class="sxs-lookup"><span data-stu-id="09329-150">In this case, it is best to apply your own grammar that is optimized for filling out your form.</span></span>

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* <span data-ttu-id="09329-151">Sie können Ihre eigenen Grammatik, die mit dem SRGS-Format bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="09329-151">You can provide your own grammar using the SRGS format.</span></span>

## <a name="use-continuous-freeform-speech-dictation"></a><span data-ttu-id="09329-152">Verwenden Sie fortlaufend, Freihandform-Spracherkennung Diktat</span><span class="sxs-lookup"><span data-stu-id="09329-152">Use continuous, freeform speech dictation</span></span>

<span data-ttu-id="09329-153">Finden Sie im Windows 10-UWP-Speech-Codebeispiel für das Szenario fortlaufendem diktieren [hier.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span><span class="sxs-lookup"><span data-stu-id="09329-153">See the Windows 10 UWP speech code sample for the continuous dictation scenario [here.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span></span>

## <a name="handle-degradation-in-quality"></a><span data-ttu-id="09329-154">Behandeln Sie die Verringerung der Qualität</span><span class="sxs-lookup"><span data-stu-id="09329-154">Handle degradation in quality</span></span>

<span data-ttu-id="09329-155">Bedingungen in der Umgebung können manchmal Spracherkennung verhindern.</span><span class="sxs-lookup"><span data-stu-id="09329-155">Conditions in the environment can sometimes prevent speech recognition from working.</span></span> <span data-ttu-id="09329-156">Z. B. im Raum ist möglicherweise zu viel Rauschen verursacht, oder der Benutzer kann mit zu hohem ein Volumen sprechen.</span><span class="sxs-lookup"><span data-stu-id="09329-156">For example, the room might be too noisy or the user might speak at too high a volume.</span></span> <span data-ttu-id="09329-157">Passen Sie die spracherkennungs-API-stellt Informationen bereit, wenn möglich, über die Bedingungen, die eine Verschlechterung in Qualität verursacht haben.</span><span class="sxs-lookup"><span data-stu-id="09329-157">The speech recognition API provides info, where possible, about conditions that have caused a degradation in quality.</span></span>

<span data-ttu-id="09329-158">Diese Informationen wird auf Ihre app mit einer WinRT-Ereignis abgelegt.</span><span class="sxs-lookup"><span data-stu-id="09329-158">This information is pushed to your app using a WinRT event.</span></span> <span data-ttu-id="09329-159">Hier ist ein Beispiel für dieses Ereignis abonnieren.</span><span class="sxs-lookup"><span data-stu-id="09329-159">Here is an example of how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="09329-160">In unserem Codebeispiel wählen wir die Bedingungen Informationen in der Debugkonsole zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="09329-160">In our code sample, we choose to write the conditions info to the debug console.</span></span> <span data-ttu-id="09329-161">Eine app kann für dem Benutzer über die Benutzeroberfläche, die Sprachsynthese und So weiter Feedback geben möchten, oder ggf. Verhalten sich anders, wenn die Sprache von eine temporäre Verringerung der Qualität unterbrochen wird.</span><span class="sxs-lookup"><span data-stu-id="09329-161">An app might want to provide feedback to the user via UI, speech synthesis, and so on, or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

```
void HolographicSpeechPromptSampleMain::OnSpeechQualityDegraded(SpeechRecognizer^ recognizer, SpeechRecognitionQualityDegradingEventArgs^ args)
   {
       switch (args->Problem)
       {
       case SpeechRecognitionAudioProblem::TooFast:
           OutputDebugStringW(L"The user spoke too quickly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooSlow:
           OutputDebugStringW(L"The user spoke too slowly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooQuiet:
           OutputDebugStringW(L"The user spoke too softly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooLoud:
           OutputDebugStringW(L"The user spoke too loudly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooNoisy:
           OutputDebugStringW(L"There is too much noise in the signal.\n");
           break;

       case SpeechRecognitionAudioProblem::NoSignal:
           OutputDebugStringW(L"There is no signal.\n");
           break;

       case SpeechRecognitionAudioProblem::None:
       default:
           OutputDebugStringW(L"An error was reported with no information.\n");
           break;
       }
   }
```

<span data-ttu-id="09329-162">Wenn Sie zum Erstellen Ihrer DirectX-app nicht Verweisklassen verwenden, müssen Sie das Ereignisabonnement vor dem Freigeben oder zum Neuerstellen Ihrer Spracherkennung.</span><span class="sxs-lookup"><span data-stu-id="09329-162">If you are not using ref classes to create your DirectX app, you must unsubscribe from the event before releasing or recreating your speech recognizer.</span></span> <span data-ttu-id="09329-163">Die HolographicSpeechPromptSample verfügt über eine Routine zum Beenden der Erkennung und abbestellen von Ereignisabonnements wie folgt:</span><span class="sxs-lookup"><span data-stu-id="09329-163">The HolographicSpeechPromptSample has a routine to stop recognition, and unsubscribe from events like so:</span></span>

```
Concurrency::task<void> HolographicSpeechPromptSampleMain::StopCurrentRecognizerIfExists()
   {
       return create_task([this]()
       {
           if (m_speechRecognizer != nullptr)
           {
               return create_task(m_speechRecognizer->StopRecognitionAsync()).then([this]()
               {
                   m_speechRecognizer->RecognitionQualityDegrading -= m_speechRecognitionQualityDegradedToken;

                   if (m_speechRecognizer->ContinuousRecognitionSession != nullptr)
                   {
                       m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated -= m_speechRecognizerResultEventToken;
                   }
               });
           }
           else
           {
               return create_task([this]() { m_speechRecognizer = nullptr; });
           }
       });
   }
```

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a><span data-ttu-id="09329-164">Verwenden von Sprachsynthese zu akustische Sprachansagen</span><span class="sxs-lookup"><span data-stu-id="09329-164">Use speech synthesis to provide audible voice prompts</span></span>

<span data-ttu-id="09329-165">Die holographic Speech-Beispiele verwenden die Sprachsynthese akustische Anweisungen für den Benutzer bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="09329-165">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="09329-166">Dieses Thema führt durch den Prozess zum Erstellen einer synthetisierten Stimme-Beispiel und Wiedergabe wieder mithilfe der HRTF-audio-APIs.</span><span class="sxs-lookup"><span data-stu-id="09329-166">This topic walks through the process of creating a synthesized voice sample, and playing it back using the HRTF audio APIs.</span></span>

<span data-ttu-id="09329-167">Sie sollten Ihre eigenen Sprache aufgefordert, beim Anfordern des Ausdruck-Eingabe bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="09329-167">You should provide your own speech prompts when requesting phrase input.</span></span> <span data-ttu-id="09329-168">Dies kann auch hilfreich, der angibt, sein, wenn Sprachbefehle können, für eine kontinuierliche Erkennung-Szenario gesprochen werden.</span><span class="sxs-lookup"><span data-stu-id="09329-168">This can also be helpful for indicating when speech commands can be spoken, for a continuous recognition scenario.</span></span> <span data-ttu-id="09329-169">Hier ist ein Beispiel dafür, wie dies mit einer Sprache-Synthesizer; Beachten Sie, dass Sie auch verwenden können, einen Clip aufgezeichnete Stimme, einer visuellen Benutzeroberfläche oder anderen Indikatoren der Vorgehensweise, z. B. in Szenarien sagen, wo die Eingabeaufforderung nicht dynamisch ist.</span><span class="sxs-lookup"><span data-stu-id="09329-169">Here is an example of how to do that with a speech synthesizer; note that you could also use a pre-recorded voice clip, a visual UI, or other indicator of what to say, for example in scenarios where the prompt is not dynamic.</span></span>

<span data-ttu-id="09329-170">Erstellen Sie zunächst das Objekt "speechsynthesizer":</span><span class="sxs-lookup"><span data-stu-id="09329-170">First, create the SpeechSynthesizer object:</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="09329-171">Außerdem benötigen Sie eine Zeichenfolge mit der Text, der umgewandelt werden soll:</span><span class="sxs-lookup"><span data-stu-id="09329-171">You also need a string with the text to be synthesized:</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="09329-172">Sprache wird asynchron mit SynthesizeTextToStreamAsync synthetisiert.</span><span class="sxs-lookup"><span data-stu-id="09329-172">Speech is synthesized asynchronously using SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="09329-173">Beginnen wir hier eine asynchrone Aufgabe, die sprachsynthetisier ein.</span><span class="sxs-lookup"><span data-stu-id="09329-173">Here, we kick off an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="09329-174">Die Sprachsynthese wird als Bytedatenstrom gesendet.</span><span class="sxs-lookup"><span data-stu-id="09329-174">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="09329-175">Wir können eine XAudio2 Stimme, Byte-Stream initialisieren; Unsere holographic Codebeispiele wiedergeben wir es als ein HRTF Audioeffekts.</span><span class="sxs-lookup"><span data-stu-id="09329-175">We can initialize an XAudio2 voice using that byte stream; for our holographic code samples, we play it back as an HRTF audio effect.</span></span>

```
Windows::Media::SpeechSynthesis::SpeechSynthesisStream^ stream = synthesisStreamTask.get();

           auto hr = m_speechSynthesisSound.Initialize(stream, 0);
           if (SUCCEEDED(hr))
           {
               m_speechSynthesisSound.SetEnvironment(HrtfEnvironment::Small);
               m_speechSynthesisSound.Start();

               // Amount of time to pause after the audio prompt is complete, before listening
               // for speech input.
               static const float bufferTime = 0.15f;

               // Wait until the prompt is done before listening.
               m_secondsUntilSoundIsComplete = m_speechSynthesisSound.GetDuration() + bufferTime;
               m_waitingForSpeechPrompt = true;
           }
       }
```

<span data-ttu-id="09329-176">Wie die Spracherkennung löst Sprachsynthese eine Ausnahme, wenn etwas schief geht.</span><span class="sxs-lookup"><span data-stu-id="09329-176">As with speech recognition, speech synthesis will throw an exception if something goes wrong.</span></span>

```
catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to synthesize speech: ") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
       }
   });
```

## <a name="see-also"></a><span data-ttu-id="09329-177">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="09329-177">See also</span></span>
* [<span data-ttu-id="09329-178">Sprache-app-design</span><span class="sxs-lookup"><span data-stu-id="09329-178">Speech app design</span></span>](https://msdn.microsoft.com/library/dn596121.aspx)
* [<span data-ttu-id="09329-179">Räumliche Sound in DirectX</span><span class="sxs-lookup"><span data-stu-id="09329-179">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="09329-180">SpeechRecognitionAndSynthesis-Beispiel</span><span class="sxs-lookup"><span data-stu-id="09329-180">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
