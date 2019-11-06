---
title: Spracheingabe in DirectX
description: Erläutert das Implementieren von Sprachbefehlen und kleinen Ausdrücken und Satz Erkennung in einer DirectX-App für Windows Mixed Reality.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Exemplarische Vorgehensweise, Sprachbefehl, Ausdruck, Erkennung, Sprache, DirectX, Plattform, Cortana, Windows Mixed Reality
ms.openlocfilehash: 0dcfaae13f763c9b8a06910f11558d2fd8e00276
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641074"
---
# <a name="voice-input-in-directx"></a>Spracheingabe in DirectX

In diesem Thema wird erläutert, wie [Sprachbefehle](voice-input.md)und kleine Ausdrücke und die Satz Erkennung in einer DirectX-App für Windows Mixed Reality implementiert werden.

>[!NOTE]
>Die Code Ausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung C++von/CX anstelle von C + +17- C++kompatibler/WinRT, wie Sie in der [ C++ Holographic-Projektvorlage](creating-a-holographic-directx-project.md)verwendet werden.  Die Konzepte sind äquivalent für ein C++/WinRT-Projekt, obwohl Sie den Code übersetzen müssen.

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a>Verwenden eines Sprech Erkennungs Moduls für die kontinuierliche Erkennung von Sprachbefehlen

In diesem Abschnitt wird beschrieben, wie die fortlaufende Spracherkennung verwendet wird, um Sprachbefehle in Ihrer APP zu aktivieren. In dieser exemplarischen Vorgehensweise wird Code aus dem [holographicvoiceinput](https://go.microsoft.com/fwlink/p/?LinkId=844964) -Beispiel verwendet. Wenn das Beispiel ausgeführt wird, sprechen Sie mit dem Namen eines der registrierten Farb Befehle, um die Farbe des drehenden Cubes zu ändern.

Erstellen Sie zunächst eine neue **Windows:: Media:: Redner Recognition:: sprecherkenzer** -Instanz.

Aus *holographicvoiceinputsamplemain:: kreatespeecheinschräninzforcurrentstate*:

```
m_speechRecognizer = ref new SpeechRecognizer();
```

Sie müssen eine Liste von Sprachbefehlen erstellen, auf die die Erkennung lauschen soll. Hier erstellen wir einen Satz von Befehlen, um die Farbe eines holograms zu ändern. Der Vorteil ist, dass wir auch die Daten erstellen, die wir später für die Befehle verwenden werden.

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

Befehle können mit phonetischen Wörtern angegeben werden, die möglicherweise nicht in einem Wörterbuch vorhanden sind:

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

Die Liste der Befehle wird in die Liste der Einschränkungen für die Spracherkennung geladen. Dies erfolgt mithilfe eines [sprach Erkennungs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) Objekts.

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

Abonnieren Sie das [resultgenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) -Ereignis für die Speech [continuouserkentionsession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx)der Spracherkennung. Dieses Ereignis benachrichtigt Ihre APP, wenn einer ihrer Befehle erkannt wurde.

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

Der **onresultgenerated** -Ereignishandler empfängt Ereignisdaten in einer Sprech Anwendung [continuouserkentionresultgeneratedeventargs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) . Wenn die Zuverlässigkeit den von Ihnen definierten Schwellenwert überschreitet, sollte Ihre APP beachten, dass das Ereignis aufgetreten ist. Speichern Sie die Ereignisdaten, damit Sie Sie in einer nachfolgenden Update Schleife verwenden können.

Aus *holographicvoiceingeputsamplemain. cpp*:

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

Verwenden Sie die Daten, die für Ihr App-Szenario gelten. In unserem Beispielcode ändern wir die Farbe des spinenden – Hologramm-Cubes entsprechend dem Befehl des Benutzers.

Aus *holographicvoiceingeputsamplemain:: Update*:

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

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a>Verwenden Sie die Diktat-und Einschuss Erkennung von sprach Ausdrücken und-Sätzen.

Sie können eine Spracherkennung so konfigurieren, dass Sie auf Ausdrücke oder Sätze lauscht, die vom Benutzer gesprochen werden. In diesem Fall wenden wir eine SpeechRecognitionTopicConstraint an, die der Spracherkennung mitteilt, welche Art von Eingabe erwartet wird. Der APP-Workflow ist für diese Art von Anwendungsfall wie folgt:
1. Ihre APP erstellt die sprechererkennende, stellt Benutzeroberflächen Aufforderungen bereit und beginnt mit dem lauschen, dass ein Befehl sofort gesprochen wird.
2. Der Benutzer spricht einen Ausdruck oder einen Satz.
3. Die Erkennung der Sprache des Benutzers wird durchgeführt, und es wird ein Ergebnis an die APP zurückgegeben. An diesem Punkt sollte Ihre APP eine UI-Eingabeaufforderung bereitstellen, die anzeigt, dass eine Erkennung aufgetreten ist.
4. Abhängig vom Vertrauensgrad, auf den Sie reagieren möchten, und dem Vertrauensgrad des sprach Erkennungs Ergebnisses kann Ihre APP das Ergebnis verarbeiten und entsprechend reagieren.

In diesem Abschnitt wird beschrieben, wie eine Sprech Erkennung erstellt, die Einschränkung kompiliert und auf Spracheingaben gelauscht wird.

Der folgende Code kompiliert die Topic-Einschränkung, die in diesem Fall für die Websuche optimiert ist.

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

Wenn die Kompilierung erfolgreich ist, können wir die Spracherkennung fortsetzen.

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

Das Ergebnis wird dann an die APP zurückgegeben. Wenn wir sicher genug im Ergebnis sind, können wir den Befehl verarbeiten. In diesem Codebeispiel werden Ergebnisse mit mindestens mittlerem Vertrauen verarbeitet.

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

Wenn Sie die Spracherkennung verwenden, sollten Sie auf Ausnahmen achten, die darauf hindeuten können, dass der Benutzer das Mikrofon in den Systemdaten Schutzeinstellungen ausgeschaltet hat. Dies kann während der Initialisierung oder während der Erkennung auftreten.

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

**Hinweis:** Es gibt mehrere vordefinierte [sprechererkennungsszenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) zur Optimierung der Spracherkennung.
* Wenn Sie die diktierung optimieren möchten, verwenden Sie das Diktat Szenario:

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* Wenn Sie zum Ausführen einer Websuche Sprache verwenden, können Sie eine webspezifische szenarioeinschränkung wie folgt verwenden:

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* Verwenden Sie die Formular Einschränkung zum Ausfüllen von Formularen. In diesem Fall ist es am besten, eine eigene Grammatik anzuwenden, die für das Ausfüllen des Formulars optimiert ist.

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* Sie können Ihre eigene Grammatik mit dem SRGS-Format bereitstellen.

## <a name="use-continuous-freeform-speech-dictation"></a>Verwenden von kontinuierlichen, frei Form sprach Diktat

Das Windows 10 UWP-Sprachcode Beispiel für das kontinuierliche Diktat Szenario finden Sie [hier.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)

## <a name="handle-degradation-in-quality"></a>Beeinträchtigung der Qualität

Bedingungen in der Umgebung können mitunter verhindern, dass die Spracherkennung funktioniert. Der Raum könnte z. b. zu grob sein, oder der Benutzer spricht zu einem zu hohen Volumen. Die Spracherkennungs-API stellt Informationen, soweit möglich, zu Bedingungen bereit, die zu einer Verschlechterung der Qualität geführt haben.

Diese Informationen werden mithilfe eines WinRT-Ereignisses per pushübertragung an Ihre APP übermittelt. Im folgenden finden Sie ein Beispiel für das Abonnieren dieses Ereignisses.

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

In unserem Codebeispiel schreiben wir die Bedingungs Informationen in die Debugkonsole. Eine APP kann dem Benutzer über die Benutzeroberfläche, die Sprachsynthese usw. Feedback geben, oder es muss anders Verhalten sein, wenn die Sprache durch eine temporäre Qualitätsminderung unterbrochen wird.

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

Wenn Sie keine Verweis Klassen zum Erstellen Ihrer DirectX-App verwenden, müssen Sie das Ereignis kündigen, bevor Sie die Spracherkennung freigeben oder neu erstellen. Das holographicsprechpromptsample-Objekt verfügt über eine Routine, um die Erkennung zu beenden und Ereignisse wie folgt abzubestellen:

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

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a>Verwenden von Sprachsynthese zur Bereitstellung audiobarer sprach Aufforderungen

Die Holographic-sprach Beispiele verwenden die Sprachsynthese, um dem Benutzer akustische Anweisungen bereitzustellen. In diesem Thema wird erläutert, wie Sie ein sprach Beispiel mit synthetischer Sprache erstellen und mit den HRTF-audioapis wiedergeben.

Beim Anfordern der Eingabe von Eingaben sollten Sie Ihre eigenen Spracheingabe Aufforderungen angeben. Dies kann auch hilfreich sein, um anzugeben, wann Sprachbefehle für ein kontinuierliches Erkennungs Szenario gesprochen werden können. Im folgenden finden Sie ein Beispiel dafür, wie Sie mit einem Sprachsynthesizer Vorgehen. Beachten Sie, dass Sie auch einen vorab aufgezeichneten Sprach Clip, eine visuelle Benutzeroberfläche oder einen anderen Indikator für die Bedeutung verwenden können, z. b. in Szenarien, in denen die Eingabeaufforderung nicht dynamisch ist.

Erstellen Sie zuerst das Sprachsynthesizer-Objekt:

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

Außerdem benötigen Sie eine Zeichenfolge mit dem Text, der synthetisiert werden soll:

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

Die Sprache wird mithilfe von "synzetextto streamasync" asynchron synthetisiert. Hier starten wir eine Async-Aufgabe, um die Sprache zu synthetisieren.

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

Die Sprachsynthese wird als Bytestream gesendet. Wir können eine XAudio2-Stimme mit diesem Bytestream initialisieren. für unsere Holographic-Codebeispiele wird es als HRTF-Audioeffekt wiedergegeben.

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

Wie bei der Spracherkennung löst die Sprachsynthese eine Ausnahme aus, wenn etwas schief geht.

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

## <a name="see-also"></a>Weitere Informationen:
* [Sprach-App-Entwurf](https://msdn.microsoft.com/library/dn596121.aspx)
* [Beispiel für die Spracherkennung](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
