---
title: Spracheingabe in DirectX
description: Erläutert das Implementieren von Sprachbefehlen und kleinen Ausdrücken und Satz Erkennung in einer DirectX-App für Windows Mixed Reality.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Exemplarische Vorgehensweise, Sprachbefehl, Ausdruck, Erkennung, Sprache, DirectX, Plattform, Cortana, Windows Mixed Reality
ms.openlocfilehash: c0a7ca85c24147e607603e733c9d191c64cbd927
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181820"
---
# <a name="voice-input-in-directx"></a><span data-ttu-id="66291-104">Spracheingabe in DirectX</span><span class="sxs-lookup"><span data-stu-id="66291-104">Voice input in DirectX</span></span>

<span data-ttu-id="66291-105">In diesem Artikel wird erläutert, wie Sie [Sprachbefehle](voice-input.md) sowie Small-Phrase und die Satz Erkennung in einer DirectX-App für Windows Mixed Reality implementieren.</span><span class="sxs-lookup"><span data-stu-id="66291-105">This article explains how to implement [voice commands](voice-input.md) plus small-phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="66291-106">Die Code Ausschnitte in diesem Artikel verwenden C++/CX anstelle von C + +17-kompatibler C++/WinRT, der in der [ C++ Holographic-Projektvorlage](creating-a-holographic-directx-project.md)verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="66291-106">The code snippets in this article use C++/CX rather than C++17-compliant C++/WinRT, which is used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="66291-107">Die Konzepte sind äquivalent für ein C++/WinRT-Projekt, aber Sie müssen den Code übersetzen.</span><span class="sxs-lookup"><span data-stu-id="66291-107">The concepts are equivalent for a C++/WinRT project, but you need to translate the code.</span></span>

## <a name="use-speechrecognizer-for-continuous-speech-recognition"></a><span data-ttu-id="66291-108">Verwenden der Sprech Erkennung für fortlaufende Spracherkennung</span><span class="sxs-lookup"><span data-stu-id="66291-108">Use SpeechRecognizer for continuous speech recognition</span></span>

<span data-ttu-id="66291-109">In diesem Abschnitt wird beschrieben, wie die fortlaufende Spracherkennung verwendet wird, um Sprachbefehle in Ihrer APP zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="66291-109">This section describes how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="66291-110">In dieser exemplarischen Vorgehensweise wird Code aus dem [holographicvoiceinput](https://go.microsoft.com/fwlink/p/?LinkId=844964) -Beispiel verwendet.</span><span class="sxs-lookup"><span data-stu-id="66291-110">This walk-through uses code from the [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) sample.</span></span> <span data-ttu-id="66291-111">Wenn das Beispiel ausgeführt wird, sprechen Sie mit dem Namen eines der registrierten Farb Befehle, um die Farbe des drehenden Cubes zu ändern.</span><span class="sxs-lookup"><span data-stu-id="66291-111">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="66291-112">Erstellen Sie zunächst eine neue *Windows:: Media:: Redner Recognition:: sprecherkenzer* -Instanz.</span><span class="sxs-lookup"><span data-stu-id="66291-112">First, create a new *Windows::Media::SpeechRecognition::SpeechRecognizer* instance.</span></span>

<span data-ttu-id="66291-113">Aus *holographicvoiceinputsamplemain:: kreatespeecheinschräninzforcurrentstate*:</span><span class="sxs-lookup"><span data-stu-id="66291-113">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="66291-114">Erstellen Sie eine Liste der Sprachbefehle, auf die die Erkennung lauschen soll.</span><span class="sxs-lookup"><span data-stu-id="66291-114">Create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="66291-115">Hier erstellen wir einen Satz von Befehlen, um die Farbe eines holograms zu ändern.</span><span class="sxs-lookup"><span data-stu-id="66291-115">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="66291-116">Aus Gründen der praktische Erstellung werden auch die Daten erstellt, die wir später für die Befehle verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="66291-116">For convenience, we also create the data that we'll use for the commands later.</span></span>

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

<span data-ttu-id="66291-117">Sie können phonetische Wörter verwenden, die möglicherweise nicht in einem Wörterbuch vorhanden sind, um Befehle anzugeben.</span><span class="sxs-lookup"><span data-stu-id="66291-117">You can use phonetic words that might not be in a dictionary to specify commands.</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="66291-118">Wenn Sie die Liste der Befehle in die Liste der Einschränkungen für die Spracherkennung laden möchten, verwenden Sie ein "Speech [erkentionlisteinschränkungs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) "-Objekt.</span><span class="sxs-lookup"><span data-stu-id="66291-118">To load the commands list into the list of constraints for the speech recognizer use a [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) object.</span></span>

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

<span data-ttu-id="66291-119">Abonnieren Sie das [resultgenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) -Ereignis für die Speech [continuouserkentionsession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)der Spracherkennung.</span><span class="sxs-lookup"><span data-stu-id="66291-119">Subscribe to the [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) event on the speech recognizer's [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span></span> <span data-ttu-id="66291-120">Dieses Ereignis benachrichtigt Ihre APP, wenn einer ihrer Befehle erkannt wurde.</span><span class="sxs-lookup"><span data-stu-id="66291-120">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="66291-121">Der *onresultgenerated* -Ereignishandler empfängt Ereignisdaten in einer Sprech Anwendung [continuouserkentionresultgeneratedeventargs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) .</span><span class="sxs-lookup"><span data-stu-id="66291-121">Your *OnResultGenerated* event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instance.</span></span> <span data-ttu-id="66291-122">Wenn die Zuverlässigkeit den von Ihnen definierten Schwellenwert überschreitet, sollte Ihre APP beachten, dass das Ereignis aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="66291-122">If the confidence is greater than the threshold that you defined, your app should note that the event happened.</span></span> <span data-ttu-id="66291-123">Speichern Sie die Ereignisdaten, damit Sie Sie in einer nachfolgenden Update Schleife verwenden können.</span><span class="sxs-lookup"><span data-stu-id="66291-123">Save the event data so that you can use it in a subsequent update loop.</span></span>

<span data-ttu-id="66291-124">Aus *holographicvoiceingeputsamplemain. cpp*:</span><span class="sxs-lookup"><span data-stu-id="66291-124">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

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

<span data-ttu-id="66291-125">In unserem Beispielcode ändern wir die Farbe des spinenden – Hologramm-Cubes entsprechend dem Befehl des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="66291-125">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="66291-126">Aus *holographicvoiceingeputsamplemain:: Update*:</span><span class="sxs-lookup"><span data-stu-id="66291-126">From *HolographicVoiceInputSampleMain::Update*:</span></span>

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

## <a name="use-one-shot-recognition"></a><span data-ttu-id="66291-127">"One-Shot"-Erkennung verwenden</span><span class="sxs-lookup"><span data-stu-id="66291-127">Use "one-shot" recognition</span></span>

<span data-ttu-id="66291-128">Sie können eine Spracherkennung so konfigurieren, dass Sie auf Ausdrücke oder Sätze lauscht, die vom Benutzer gesprochen werden.</span><span class="sxs-lookup"><span data-stu-id="66291-128">You can configure a speech recognizer to listen for phrases or sentences that the user speaks.</span></span> <span data-ttu-id="66291-129">In diesem Fall wenden wir eine *SpeechRecognitionTopicConstraint* an, die der Spracherkennung mitteilt, welche Art von Eingabe erwartet wird.</span><span class="sxs-lookup"><span data-stu-id="66291-129">In this case, we apply a *SpeechRecognitionTopicConstraint* that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="66291-130">Im folgenden finden Sie einen app-Workflow für dieses Szenario:</span><span class="sxs-lookup"><span data-stu-id="66291-130">Here's an app workflow for this scenario:</span></span>
1. <span data-ttu-id="66291-131">Ihre APP erstellt die sprechererkennende, stellt Benutzeroberflächen Aufforderungen bereit und beginnt mit dem lauschen auf einen gesprochenen Befehl.</span><span class="sxs-lookup"><span data-stu-id="66291-131">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a spoken command.</span></span>
2. <span data-ttu-id="66291-132">Der Benutzer spricht einen Ausdruck oder einen Satz.</span><span class="sxs-lookup"><span data-stu-id="66291-132">The user speaks a phrase or sentence.</span></span>
3. <span data-ttu-id="66291-133">Das Erkennen der Sprache des Benutzers tritt auf, und es wird ein Ergebnis an die APP zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="66291-133">Recognition of the user's speech occurs, and a result is returned to the app.</span></span> <span data-ttu-id="66291-134">An diesem Punkt sollte Ihre APP eine UI-Eingabeaufforderung bereitstellen, um anzugeben, dass eine Erkennung aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="66291-134">At this point, your app should provide a UI prompt to indicate that recognition has occurred.</span></span>
4. <span data-ttu-id="66291-135">Abhängig vom Vertrauensgrad, auf den Sie reagieren möchten, und vom Vertrauensgrad des sprach Erkennungs Ergebnisses kann Ihre APP das Ergebnis verarbeiten und entsprechend reagieren.</span><span class="sxs-lookup"><span data-stu-id="66291-135">Depending on the confidence level that you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="66291-136">In diesem Abschnitt wird beschrieben, wie eine Sprech Erkennung erstellt, die Einschränkung kompiliert und auf Spracheingaben gelauscht wird.</span><span class="sxs-lookup"><span data-stu-id="66291-136">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="66291-137">Der folgende Code kompiliert die Topic-Einschränkung, die in diesem Fall für die Websuche optimiert ist.</span><span class="sxs-lookup"><span data-stu-id="66291-137">The following code compiles the topic constraint, which in this case is optimized for web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="66291-138">Wenn die Kompilierung erfolgreich ist, können wir die Spracherkennung fortsetzen.</span><span class="sxs-lookup"><span data-stu-id="66291-138">If compilation succeeds, we can proceed with speech recognition.</span></span>

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

<span data-ttu-id="66291-139">Das Ergebnis wird dann an die APP zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="66291-139">The result is then returned to the app.</span></span> <span data-ttu-id="66291-140">Wenn wir sicher genug im Ergebnis sind, können wir den Befehl verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="66291-140">If we're confident enough in the result, we can process the command.</span></span> <span data-ttu-id="66291-141">In diesem Codebeispiel werden Ergebnisse mit mindestens mittlerem Vertrauen verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="66291-141">This code example processes results with at least medium confidence.</span></span>

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

<span data-ttu-id="66291-142">Wenn Sie die Spracherkennung verwenden, achten Sie auf Ausnahmen, die darauf hindeuten können, dass der Benutzer das Mikrofon in den Systemdaten Schutzeinstellungen ausgeschaltet hat.</span><span class="sxs-lookup"><span data-stu-id="66291-142">Whenever you use speech recognition, watch for exceptions that could indicate that the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="66291-143">Dies kann während der Initialisierung oder Erkennung auftreten.</span><span class="sxs-lookup"><span data-stu-id="66291-143">This can happen during initialization or recognition.</span></span>

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

> [!NOTE]
> <span data-ttu-id="66291-144">Es gibt mehrere vordefinierte [sprechererkennungsszenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) , mit denen Sie die Spracherkennung optimieren können.</span><span class="sxs-lookup"><span data-stu-id="66291-144">There are several predefined [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) that you can use to optimize speech recognition.</span></span>

* <span data-ttu-id="66291-145">Verwenden Sie das Diktat Szenario, um die diktierung zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="66291-145">To optimize for dictation, use the dictation scenario.</span></span><br/>
   ```
   // Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
   ```

* <span data-ttu-id="66291-146">Verwenden Sie für sprachweb Suchvorgänge die folgende webspezifische szenarioeinschränkung.</span><span class="sxs-lookup"><span data-stu-id="66291-146">For speech web searches, use the following web-specific scenario constraint.</span></span>

   ```
   // Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
   ```

* <span data-ttu-id="66291-147">Verwenden Sie die Formular Einschränkung zum Ausfüllen von Formularen.</span><span class="sxs-lookup"><span data-stu-id="66291-147">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="66291-148">In diesem Fall ist es am besten, eine eigene Grammatik anzuwenden, die für das Ausfüllen des Formulars optimiert ist.</span><span class="sxs-lookup"><span data-stu-id="66291-148">In this case, it's best to apply your own grammar that's optimized for filling out the form.</span></span>

   ```
   // Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
   ```
* <span data-ttu-id="66291-149">Sie können Ihre eigene Grammatik im SRGS-Format bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="66291-149">You can provide your own grammar in the SRGS format.</span></span>

## <a name="use-continuous-recognition"></a><span data-ttu-id="66291-150">Fortlaufende Erkennung verwenden</span><span class="sxs-lookup"><span data-stu-id="66291-150">Use continuous recognition</span></span>

<span data-ttu-id="66291-151">Informationen zum fortlaufenden Szenario finden Sie im [Windows 10 UWP-Sprachcode Beispiel](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp).</span><span class="sxs-lookup"><span data-stu-id="66291-151">For the continuous-dictation scenario, see the [Windows 10 UWP speech code sample](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp).</span></span>

## <a name="handle-quality-degradation"></a><span data-ttu-id="66291-152">Behandeln von Qualitätseinbußen</span><span class="sxs-lookup"><span data-stu-id="66291-152">Handle quality degradation</span></span>

<span data-ttu-id="66291-153">Umgebungsbedingungen stören manchmal die Spracherkennung.</span><span class="sxs-lookup"><span data-stu-id="66291-153">Environmental conditions sometimes interfere with speech recognition.</span></span> <span data-ttu-id="66291-154">Der Raum könnte z. b. zu laut sein, oder der Benutzer spricht zu lauter.</span><span class="sxs-lookup"><span data-stu-id="66291-154">For example, the room might be too noisy, or the user might speak too loudly.</span></span> <span data-ttu-id="66291-155">Wenn möglich, stellt die Spracherkennungs-API Informationen zu den Bedingungen bereit, die die Qualitäts Beeinträchtigung verursacht haben.</span><span class="sxs-lookup"><span data-stu-id="66291-155">Whenever possible, the speech recognition API provides information about the conditions that caused the quality degradation.</span></span> <span data-ttu-id="66291-156">Diese Informationen werden über ein WinRT-Ereignis an Ihre APP übermittelt.</span><span class="sxs-lookup"><span data-stu-id="66291-156">This information is pushed to your app through a WinRT event.</span></span> <span data-ttu-id="66291-157">Im folgenden Beispiel wird gezeigt, wie dieses Ereignis abonniert wird.</span><span class="sxs-lookup"><span data-stu-id="66291-157">The following example shows  how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="66291-158">In unserem Codebeispiel werden die Bedingungen Informationen in die Debug-Konsole geschrieben.</span><span class="sxs-lookup"><span data-stu-id="66291-158">In our code sample, we write the conditions information to the debug console.</span></span> <span data-ttu-id="66291-159">Eine APP kann dem Benutzer über die Benutzeroberfläche, die Sprachsynthese und eine andere Methode Feedback geben.</span><span class="sxs-lookup"><span data-stu-id="66291-159">An app might want to provide feedback to the user through the UI, speech synthesis, and another method.</span></span> <span data-ttu-id="66291-160">Oder es muss anders Verhalten sein, wenn die Sprache durch eine temporäre Verringerung der Qualität unterbrochen wird.</span><span class="sxs-lookup"><span data-stu-id="66291-160">Or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

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

<span data-ttu-id="66291-161">Wenn Sie keine Verweis Klassen zum Erstellen Ihrer DirectX-App verwenden, müssen Sie das Ereignis kündigen, bevor Sie die Spracherkennung freigeben oder neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="66291-161">If you're not using ref classes to create your DirectX app, you must unsubscribe from the event before you release or recreate your speech recognizer.</span></span> <span data-ttu-id="66291-162">Das holographicsprechpromptsample-Objekt verfügt über eine Routine, um die Erkennung zu beenden und Ereignisse abzubestellen.</span><span class="sxs-lookup"><span data-stu-id="66291-162">The HolographicSpeechPromptSample has a routine to stop recognition and unsubscribe from events.</span></span>

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

## <a name="use-speech-synthesis-to-provide-audible-prompts"></a><span data-ttu-id="66291-163">Verwenden von Sprachsynthese zum Bereitstellen von akustischen Eingabe Aufforderungen</span><span class="sxs-lookup"><span data-stu-id="66291-163">Use speech synthesis to provide audible prompts</span></span>

<span data-ttu-id="66291-164">Die Holographic-sprach Beispiele verwenden die Sprachsynthese, um dem Benutzer akustische Anweisungen bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="66291-164">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="66291-165">In diesem Abschnitt wird gezeigt, wie Sie ein sprach Beispiel mit synthetischer Sprache erstellen und anschließend über die HRTF-audioapis wiedergeben.</span><span class="sxs-lookup"><span data-stu-id="66291-165">This section shows how to create a synthesized voice sample  and then play it back through the HRTF audio APIs.</span></span>

<span data-ttu-id="66291-166">Sie sollten ihre eigenen Spracheingabe Aufforderungen angeben, wenn Sie die Eingabe von Eingaben anfordern.</span><span class="sxs-lookup"><span data-stu-id="66291-166">You should provide your own speech prompts when you request phrase input.</span></span> <span data-ttu-id="66291-167">Mithilfe von Aufforderungen können Sie auch angeben, wann Sprachbefehle für ein kontinuierliches Erkennungs Szenario gesprochen werden können.</span><span class="sxs-lookup"><span data-stu-id="66291-167">Prompts can also help indicate when speech commands can be spoken for a continuous-recognition scenario.</span></span> <span data-ttu-id="66291-168">Im folgenden Beispiel wird veranschaulicht, wie Sie hierfür einen Sprachsynthesizer verwenden können.</span><span class="sxs-lookup"><span data-stu-id="66291-168">The following example demonstrates how to use a speech synthesizer to do this.</span></span> <span data-ttu-id="66291-169">Sie können auch einen vorab aufgezeichneten Sprach Clip, eine visuelle Benutzeroberfläche oder einen anderen Indikator dafür verwenden, was zu sagen ist, z. b. in Szenarien, in denen die Eingabeaufforderung nicht dynamisch ist.</span><span class="sxs-lookup"><span data-stu-id="66291-169">You could also use a pre-recorded voice clip, a visual UI, or another indicator of what to say, for example in scenarios where the prompt is not dynamic.</span></span>

<span data-ttu-id="66291-170">Erstellen Sie zuerst das Sprachsynthesizer-Objekt.</span><span class="sxs-lookup"><span data-stu-id="66291-170">First, create the SpeechSynthesizer object.</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="66291-171">Außerdem benötigen Sie eine Zeichenfolge, die den Text für die synthetisieren enthält.</span><span class="sxs-lookup"><span data-stu-id="66291-171">You also need a string that includes the text to  synthesize.</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="66291-172">Die Sprachausgabe wird asynchron über "synzetextchanchanasync" synthetisiert.</span><span class="sxs-lookup"><span data-stu-id="66291-172">Speech is synthesized asynchronously through SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="66291-173">Hier starten wir eine Async-Aufgabe, um die Sprache zu synthetisieren.</span><span class="sxs-lookup"><span data-stu-id="66291-173">Here, we start an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="66291-174">Die Sprachsynthese wird als Bytestream gesendet.</span><span class="sxs-lookup"><span data-stu-id="66291-174">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="66291-175">Mit diesem Bytestream können Sie eine XAudio2-Stimme initialisieren.</span><span class="sxs-lookup"><span data-stu-id="66291-175">We can use that byte stream to initialize an XAudio2 voice.</span></span> <span data-ttu-id="66291-176">Für unsere Holographic-Codebeispiele wird es als HRTF-Audioeffekt wiedergegeben.</span><span class="sxs-lookup"><span data-stu-id="66291-176">For our holographic code samples, we play it back as an HRTF audio effect.</span></span>

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

<span data-ttu-id="66291-177">Wie bei der Spracherkennung löst die Sprachsynthese eine Ausnahme aus, wenn etwas schief geht.</span><span class="sxs-lookup"><span data-stu-id="66291-177">As with speech recognition, speech synthesis throws an exception if something goes wrong.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="66291-178">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="66291-178">See also</span></span>
* [<span data-ttu-id="66291-179">Sprach-App-Entwurf</span><span class="sxs-lookup"><span data-stu-id="66291-179">Speech app design</span></span>](https://msdn.microsoft.com/library/dn596121.aspx)
* [<span data-ttu-id="66291-180">Beispiel für die Spracherkennung</span><span class="sxs-lookup"><span data-stu-id="66291-180">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
