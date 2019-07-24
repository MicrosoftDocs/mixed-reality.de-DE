---
title: Spracheingabe in DirectX
description: Erläutert das Implementieren von Sprachbefehlen und kleinen Ausdrücken und Satz Erkennung in einer DirectX-App für Windows Mixed Reality.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Exemplarische Vorgehensweise, Sprachbefehl, Ausdruck, Erkennung, Sprache, DirectX, Plattform, Cortana, Windows Mixed Reality
ms.openlocfilehash: 728457a495616e5f65ec3986dfb6ac60231f9e46
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548663"
---
# <a name="voice-input-in-directx"></a><span data-ttu-id="83924-104">Spracheingabe in DirectX</span><span class="sxs-lookup"><span data-stu-id="83924-104">Voice input in DirectX</span></span>

<span data-ttu-id="83924-105">In diesem Thema wird erläutert, wie [Sprachbefehle](voice-input.md)und kleine Ausdrücke und die Satz Erkennung in einer DirectX-App für Windows Mixed Reality implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="83924-105">This topic explains how to implement [voice commands](voice-input.md), and small phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="83924-106">Die Code Ausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung C++von/CX anstelle von C + +17- C++kompatibler/WinRT, wie Sie in der [ C++ Holographic-Projektvorlage](creating-a-holographic-directx-project.md)verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="83924-106">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="83924-107">Die Konzepte sind äquivalent für ein C++/WinRT-Projekt, obwohl Sie den Code übersetzen müssen.</span><span class="sxs-lookup"><span data-stu-id="83924-107">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a><span data-ttu-id="83924-108">Verwenden eines Sprech Erkennungs Moduls für die kontinuierliche Erkennung von Sprachbefehlen</span><span class="sxs-lookup"><span data-stu-id="83924-108">Use a SpeechRecognizer for continuous recognition of voice commands</span></span>

<span data-ttu-id="83924-109">In diesem Abschnitt wird beschrieben, wie die fortlaufende Spracherkennung verwendet wird, um Sprachbefehle in Ihrer APP zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="83924-109">In this section, we describe how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="83924-110">In dieser exemplarischen Vorgehensweise wird Code aus dem [holographicvoiceinput](http://go.microsoft.com/fwlink/p/?LinkId=844964) -Beispiel verwendet.</span><span class="sxs-lookup"><span data-stu-id="83924-110">This walkthrough uses code from the [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) Sample.</span></span> <span data-ttu-id="83924-111">Wenn das Beispiel ausgeführt wird, sprechen Sie mit dem Namen eines der registrierten Farb Befehle, um die Farbe des drehenden Cubes zu ändern.</span><span class="sxs-lookup"><span data-stu-id="83924-111">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="83924-112">Erstellen Sie zunächst eine neue **Windows:: Media:: Redner Recognition:: sprecherkenzer** -Instanz.</span><span class="sxs-lookup"><span data-stu-id="83924-112">First, create a new **Windows::Media::SpeechRecognition::SpeechRecognizer** instance.</span></span>

<span data-ttu-id="83924-113">Aus *holographicvoiceinputsamplemain:: kreatespeecheinschräninzforcurrentstate*:</span><span class="sxs-lookup"><span data-stu-id="83924-113">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="83924-114">Sie müssen eine Liste von Sprachbefehlen erstellen, auf die die Erkennung lauschen soll.</span><span class="sxs-lookup"><span data-stu-id="83924-114">You'll need to create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="83924-115">Hier erstellen wir einen Satz von Befehlen, um die Farbe eines holograms zu ändern.</span><span class="sxs-lookup"><span data-stu-id="83924-115">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="83924-116">Der Vorteil ist, dass wir auch die Daten erstellen, die wir später für die Befehle verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="83924-116">For the sake of convenience, we also create the data that we'll use for the commands later on.</span></span>

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

<span data-ttu-id="83924-117">Befehle können mit phonetischen Wörtern angegeben werden, die möglicherweise nicht in einem Wörterbuch vorhanden sind:</span><span class="sxs-lookup"><span data-stu-id="83924-117">Commands can be specified using phonetic words that might not be in a dictionary:</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="83924-118">Die Liste der Befehle wird in die Liste der Einschränkungen für die Spracherkennung geladen.</span><span class="sxs-lookup"><span data-stu-id="83924-118">The list of commands is loaded into the list of constraints for the speech recognizer.</span></span> <span data-ttu-id="83924-119">Dies erfolgt mithilfe eines [sprach Erkennungs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) Objekts.</span><span class="sxs-lookup"><span data-stu-id="83924-119">This is done by using a [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) object.</span></span>

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

<span data-ttu-id="83924-120">Abonnieren Sie das [resultgenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) -Ereignis für die Speech [continuouserkentionsession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)der Spracherkennung.</span><span class="sxs-lookup"><span data-stu-id="83924-120">Subscribe to the [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) event on the speech recognizer's [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx).</span></span> <span data-ttu-id="83924-121">Dieses Ereignis benachrichtigt Ihre APP, wenn einer ihrer Befehle erkannt wurde.</span><span class="sxs-lookup"><span data-stu-id="83924-121">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="83924-122">Der **onresultgenerated** -Ereignishandler empfängt Ereignisdaten in einer Sprech Anwendung [continuouserkentionresultgeneratedeventargs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) .</span><span class="sxs-lookup"><span data-stu-id="83924-122">Your **OnResultGenerated** event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) instance.</span></span> <span data-ttu-id="83924-123">Wenn die Zuverlässigkeit den von Ihnen definierten Schwellenwert überschreitet, sollte Ihre APP beachten, dass das Ereignis aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="83924-123">If the confidence is greater than the threshold you have defined, your app should note that the event happened.</span></span> <span data-ttu-id="83924-124">Speichern Sie die Ereignisdaten, damit Sie Sie in einer nachfolgenden Update Schleife verwenden können.</span><span class="sxs-lookup"><span data-stu-id="83924-124">Save the event data so that you can make use of it in a subsequent update loop.</span></span>

<span data-ttu-id="83924-125">Aus *holographicvoiceingeputsamplemain. cpp*:</span><span class="sxs-lookup"><span data-stu-id="83924-125">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

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

<span data-ttu-id="83924-126">Verwenden Sie die Daten, die für Ihr App-Szenario gelten.</span><span class="sxs-lookup"><span data-stu-id="83924-126">Make use of the data however applicable to your app scenario.</span></span> <span data-ttu-id="83924-127">In unserem Beispielcode ändern wir die Farbe des spinenden – Hologramm-Cubes entsprechend dem Befehl des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="83924-127">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="83924-128">Aus *holographicvoiceingeputsamplemain:: Update*:</span><span class="sxs-lookup"><span data-stu-id="83924-128">From *HolographicVoiceInputSampleMain::Update*:</span></span>

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

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a><span data-ttu-id="83924-129">Verwenden Sie die Diktat-und Einschuss Erkennung von sprach Ausdrücken und-Sätzen.</span><span class="sxs-lookup"><span data-stu-id="83924-129">Use dictation for one-shot recognition of speech phrases and sentences</span></span>

<span data-ttu-id="83924-130">Sie können eine Spracherkennung so konfigurieren, dass Sie auf Ausdrücke oder Sätze lauscht, die vom Benutzer gesprochen werden.</span><span class="sxs-lookup"><span data-stu-id="83924-130">You can configure a speech recognizer to listen for phrases or sentences spoken by the user.</span></span> <span data-ttu-id="83924-131">In diesem Fall wenden wir eine SpeechRecognitionTopicConstraint an, die der Spracherkennung mitteilt, welche Art von Eingabe erwartet wird.</span><span class="sxs-lookup"><span data-stu-id="83924-131">In this case, we apply a SpeechRecognitionTopicConstraint that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="83924-132">Der APP-Workflow ist für diese Art von Anwendungsfall wie folgt:</span><span class="sxs-lookup"><span data-stu-id="83924-132">The app workflow is as follows, for this type of use case:</span></span>
1. <span data-ttu-id="83924-133">Ihre APP erstellt die sprechererkennende, stellt Benutzeroberflächen Aufforderungen bereit und beginnt mit dem lauschen, dass ein Befehl sofort gesprochen wird.</span><span class="sxs-lookup"><span data-stu-id="83924-133">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a command to be spoken immediately.</span></span>
2. <span data-ttu-id="83924-134">Der Benutzer spricht einen Ausdruck oder einen Satz.</span><span class="sxs-lookup"><span data-stu-id="83924-134">The user speaks a phrase, or sentence.</span></span>
3. <span data-ttu-id="83924-135">Die Erkennung der Sprache des Benutzers wird durchgeführt, und es wird ein Ergebnis an die APP zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="83924-135">Recognition of the user's speech is performed, and a result is returned to the app.</span></span> <span data-ttu-id="83924-136">An diesem Punkt sollte Ihre APP eine UI-Eingabeaufforderung bereitstellen, die anzeigt, dass eine Erkennung aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="83924-136">At this point, your app should provide a UI prompt indicating that recognition has occurred.</span></span>
4. <span data-ttu-id="83924-137">Abhängig vom Vertrauensgrad, auf den Sie reagieren möchten, und dem Vertrauensgrad des sprach Erkennungs Ergebnisses kann Ihre APP das Ergebnis verarbeiten und entsprechend reagieren.</span><span class="sxs-lookup"><span data-stu-id="83924-137">Depending on the confidence level you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="83924-138">In diesem Abschnitt wird beschrieben, wie eine Sprech Erkennung erstellt, die Einschränkung kompiliert und auf Spracheingaben gelauscht wird.</span><span class="sxs-lookup"><span data-stu-id="83924-138">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="83924-139">Der folgende Code kompiliert die Topic-Einschränkung, die in diesem Fall für die Websuche optimiert ist.</span><span class="sxs-lookup"><span data-stu-id="83924-139">The following code compiles the topic constraint, which in this case is optimized for Web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="83924-140">Wenn die Kompilierung erfolgreich ist, können wir die Spracherkennung fortsetzen.</span><span class="sxs-lookup"><span data-stu-id="83924-140">If compilation succeeds, we can proceed with speech recognition.</span></span>

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

<span data-ttu-id="83924-141">Das Ergebnis wird dann an die APP zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="83924-141">The result is then returned to the app.</span></span> <span data-ttu-id="83924-142">Wenn wir sicher genug im Ergebnis sind, können wir den Befehl verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="83924-142">If we are confident enough in the result, we can process the command.</span></span> <span data-ttu-id="83924-143">In diesem Codebeispiel werden Ergebnisse mit mindestens mittlerem Vertrauen verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="83924-143">This code example processes results with at least Medium confidence.</span></span>

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

<span data-ttu-id="83924-144">Wenn Sie die Spracherkennung verwenden, sollten Sie auf Ausnahmen achten, die darauf hindeuten können, dass der Benutzer das Mikrofon in den Systemdaten Schutzeinstellungen ausgeschaltet hat.</span><span class="sxs-lookup"><span data-stu-id="83924-144">Whenever you use speech recognition, you should watch for exceptions that could indicate the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="83924-145">Dies kann während der Initialisierung oder während der Erkennung auftreten.</span><span class="sxs-lookup"><span data-stu-id="83924-145">This can happen during initialization, or during recognition.</span></span>

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

<span data-ttu-id="83924-146">**HINWEIS:** Es gibt mehrere vordefinierte [sprechererkennungsszenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) zur Optimierung der Spracherkennung.</span><span class="sxs-lookup"><span data-stu-id="83924-146">**NOTE:** There are several predefined [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) available for optimizing speech recognition.</span></span>
* <span data-ttu-id="83924-147">Wenn Sie die diktierung optimieren möchten, verwenden Sie das Diktat Szenario:</span><span class="sxs-lookup"><span data-stu-id="83924-147">If you want to optimize for dictation, use the Dictation scenario:</span></span>

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* <span data-ttu-id="83924-148">Wenn Sie zum Ausführen einer Websuche Sprache verwenden, können Sie eine webspezifische szenarioeinschränkung wie folgt verwenden:</span><span class="sxs-lookup"><span data-stu-id="83924-148">When using speech to perform a Web search, you can use a Web-specific scenario constraint as follows:</span></span>

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* <span data-ttu-id="83924-149">Verwenden Sie die Formular Einschränkung zum Ausfüllen von Formularen.</span><span class="sxs-lookup"><span data-stu-id="83924-149">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="83924-150">In diesem Fall ist es am besten, eine eigene Grammatik anzuwenden, die für das Ausfüllen des Formulars optimiert ist.</span><span class="sxs-lookup"><span data-stu-id="83924-150">In this case, it is best to apply your own grammar that is optimized for filling out your form.</span></span>

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* <span data-ttu-id="83924-151">Sie können Ihre eigene Grammatik mit dem SRGS-Format bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="83924-151">You can provide your own grammar using the SRGS format.</span></span>

## <a name="use-continuous-freeform-speech-dictation"></a><span data-ttu-id="83924-152">Verwenden von kontinuierlichen, frei Form sprach Diktat</span><span class="sxs-lookup"><span data-stu-id="83924-152">Use continuous, freeform speech dictation</span></span>

<span data-ttu-id="83924-153">Das Windows 10 UWP-Sprachcode Beispiel für das kontinuierliche Diktat Szenario finden Sie [hier.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span><span class="sxs-lookup"><span data-stu-id="83924-153">See the Windows 10 UWP speech code sample for the continuous dictation scenario [here.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)</span></span>

## <a name="handle-degradation-in-quality"></a><span data-ttu-id="83924-154">Beeinträchtigung der Qualität</span><span class="sxs-lookup"><span data-stu-id="83924-154">Handle degradation in quality</span></span>

<span data-ttu-id="83924-155">Bedingungen in der Umgebung können mitunter verhindern, dass die Spracherkennung funktioniert.</span><span class="sxs-lookup"><span data-stu-id="83924-155">Conditions in the environment can sometimes prevent speech recognition from working.</span></span> <span data-ttu-id="83924-156">Der Raum könnte z. b. zu grob sein, oder der Benutzer spricht zu einem zu hohen Volumen.</span><span class="sxs-lookup"><span data-stu-id="83924-156">For example, the room might be too noisy or the user might speak at too high a volume.</span></span> <span data-ttu-id="83924-157">Die Spracherkennungs-API stellt Informationen, soweit möglich, zu Bedingungen bereit, die zu einer Verschlechterung der Qualität geführt haben.</span><span class="sxs-lookup"><span data-stu-id="83924-157">The speech recognition API provides info, where possible, about conditions that have caused a degradation in quality.</span></span>

<span data-ttu-id="83924-158">Diese Informationen werden mithilfe eines WinRT-Ereignisses per pushübertragung an Ihre APP übermittelt.</span><span class="sxs-lookup"><span data-stu-id="83924-158">This information is pushed to your app using a WinRT event.</span></span> <span data-ttu-id="83924-159">Im folgenden finden Sie ein Beispiel für das Abonnieren dieses Ereignisses.</span><span class="sxs-lookup"><span data-stu-id="83924-159">Here is an example of how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="83924-160">In unserem Codebeispiel schreiben wir die Bedingungs Informationen in die Debugkonsole.</span><span class="sxs-lookup"><span data-stu-id="83924-160">In our code sample, we choose to write the conditions info to the debug console.</span></span> <span data-ttu-id="83924-161">Eine APP kann dem Benutzer über die Benutzeroberfläche, die Sprachsynthese usw. Feedback geben, oder es muss anders Verhalten sein, wenn die Sprache durch eine temporäre Qualitätsminderung unterbrochen wird.</span><span class="sxs-lookup"><span data-stu-id="83924-161">An app might want to provide feedback to the user via UI, speech synthesis, and so on, or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

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

<span data-ttu-id="83924-162">Wenn Sie keine Verweis Klassen zum Erstellen Ihrer DirectX-App verwenden, müssen Sie das Ereignis kündigen, bevor Sie die Spracherkennung freigeben oder neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="83924-162">If you are not using ref classes to create your DirectX app, you must unsubscribe from the event before releasing or recreating your speech recognizer.</span></span> <span data-ttu-id="83924-163">Das holographicsprechpromptsample-Objekt verfügt über eine Routine, um die Erkennung zu beenden und Ereignisse wie folgt abzubestellen:</span><span class="sxs-lookup"><span data-stu-id="83924-163">The HolographicSpeechPromptSample has a routine to stop recognition, and unsubscribe from events like so:</span></span>

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

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a><span data-ttu-id="83924-164">Verwenden von Sprachsynthese zur Bereitstellung audiobarer sprach Aufforderungen</span><span class="sxs-lookup"><span data-stu-id="83924-164">Use speech synthesis to provide audible voice prompts</span></span>

<span data-ttu-id="83924-165">Die Holographic-sprach Beispiele verwenden die Sprachsynthese, um dem Benutzer akustische Anweisungen bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="83924-165">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="83924-166">In diesem Thema wird erläutert, wie Sie ein sprach Beispiel mit synthetischer Sprache erstellen und mit den HRTF-audioapis wiedergeben.</span><span class="sxs-lookup"><span data-stu-id="83924-166">This topic walks through the process of creating a synthesized voice sample, and playing it back using the HRTF audio APIs.</span></span>

<span data-ttu-id="83924-167">Beim Anfordern der Eingabe von Eingaben sollten Sie Ihre eigenen Spracheingabe Aufforderungen angeben.</span><span class="sxs-lookup"><span data-stu-id="83924-167">You should provide your own speech prompts when requesting phrase input.</span></span> <span data-ttu-id="83924-168">Dies kann auch hilfreich sein, um anzugeben, wann Sprachbefehle für ein kontinuierliches Erkennungs Szenario gesprochen werden können.</span><span class="sxs-lookup"><span data-stu-id="83924-168">This can also be helpful for indicating when speech commands can be spoken, for a continuous recognition scenario.</span></span> <span data-ttu-id="83924-169">Im folgenden finden Sie ein Beispiel dafür, wie Sie mit einem Sprachsynthesizer Vorgehen. Beachten Sie, dass Sie auch einen vorab aufgezeichneten Sprach Clip, eine visuelle Benutzeroberfläche oder einen anderen Indikator für die Bedeutung verwenden können, z. b. in Szenarien, in denen die Eingabeaufforderung nicht dynamisch ist.</span><span class="sxs-lookup"><span data-stu-id="83924-169">Here is an example of how to do that with a speech synthesizer; note that you could also use a pre-recorded voice clip, a visual UI, or other indicator of what to say, for example in scenarios where the prompt is not dynamic.</span></span>

<span data-ttu-id="83924-170">Erstellen Sie zuerst das Sprachsynthesizer-Objekt:</span><span class="sxs-lookup"><span data-stu-id="83924-170">First, create the SpeechSynthesizer object:</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="83924-171">Außerdem benötigen Sie eine Zeichenfolge mit dem Text, der synthetisiert werden soll:</span><span class="sxs-lookup"><span data-stu-id="83924-171">You also need a string with the text to be synthesized:</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="83924-172">Die Sprache wird mithilfe von "synzetextto streamasync" asynchron synthetisiert.</span><span class="sxs-lookup"><span data-stu-id="83924-172">Speech is synthesized asynchronously using SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="83924-173">Hier starten wir eine Async-Aufgabe, um die Sprache zu synthetisieren.</span><span class="sxs-lookup"><span data-stu-id="83924-173">Here, we kick off an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="83924-174">Die Sprachsynthese wird als Bytestream gesendet.</span><span class="sxs-lookup"><span data-stu-id="83924-174">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="83924-175">Wir können eine XAudio2-Stimme mit diesem Bytestream initialisieren. für unsere Holographic-Codebeispiele wird es als HRTF-Audioeffekt wiedergegeben.</span><span class="sxs-lookup"><span data-stu-id="83924-175">We can initialize an XAudio2 voice using that byte stream; for our holographic code samples, we play it back as an HRTF audio effect.</span></span>

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

<span data-ttu-id="83924-176">Wie bei der Spracherkennung löst die Sprachsynthese eine Ausnahme aus, wenn etwas schief geht.</span><span class="sxs-lookup"><span data-stu-id="83924-176">As with speech recognition, speech synthesis will throw an exception if something goes wrong.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="83924-177">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="83924-177">See also</span></span>
* [<span data-ttu-id="83924-178">Sprach-App-Entwurf</span><span class="sxs-lookup"><span data-stu-id="83924-178">Speech app design</span></span>](https://msdn.microsoft.com/library/dn596121.aspx)
* [<span data-ttu-id="83924-179">Raumklang in DirectX</span><span class="sxs-lookup"><span data-stu-id="83924-179">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="83924-180">Beispiel für die Spracherkennung</span><span class="sxs-lookup"><span data-stu-id="83924-180">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
