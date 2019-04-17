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
# <a name="voice-input-in-directx"></a>Spracheingabe in DirectX

In diesem Thema wird erläutert, wie implementieren [Sprachbefehle](voice-input.md), und klein Ausdruck und Satz Anerkennung in einer DirectX-app für Windows Mixed Reality.

>[!NOTE]
>Die Codeausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstatt C ++ 17-kompatible C++"/ WinRT", wie in der [ C++ holographic Projektvorlage](creating-a-holographic-directx-project.md).  Die Konzepte sind Entsprechung für einen C++"/ WinRT"-Projekt, aber Sie benötigen, um den Code zu übersetzen.

## <a name="use-a-speechrecognizer-for-continuous-recognition-of-voice-commands"></a>Verwenden Sie eine SpeechRecognizer für kontinuierliche Erkennung von Stimmbefehlen

In diesem Abschnitt beschrieben, wie kontinuierliche Spracherkennung zu verwenden, um Sprachbefehle in Ihrer app zu aktivieren. In dieser exemplarischen Vorgehensweise verwendet den Code aus der [HolographicVoiceInput](http://go.microsoft.com/fwlink/p/?LinkId=844964) Beispiel. Wenn das Beispiel ausgeführt wird, sprechen Sie den Namen einer der Befehle zum Ändern der Farbe der sich drehenden Würfels registrierten Farbe.

Erstellen Sie zunächst ein neues **Windows::Media::SpeechRecognition::SpeechRecognizer** Instanz.

From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:

```
m_speechRecognizer = ref new SpeechRecognizer();
```

Sie müssen eine Liste mit Befehlen der Sprache für das Erkennungsmodul zum Lauschen auf zu erstellen. Hier erstellen wir eine Reihe von Befehlen zum Ändern der Farbe der ggf. ein Hologramm. Aus Gründen der Einfachheit halber erstellen wir auch die Daten, die wir für die Befehle später verwenden werden.

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

Befehle können phonetische Wörter verwenden, die in einem Wörterbuch möglicherweise nicht angegeben werden:

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

Die Liste der Befehle wird in die Liste der Einschränkungen für die Spracherkennung geladen. Dies erfolgt mithilfe einer [SpeechRecognitionListConstraint](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionlistconstraint.aspx) Objekt.

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

Abonnieren Sie den [ResultGenerated](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.resultgenerated.aspx) Ereignis für der Spracherkennung [SpeechContinuousRecognitionSession](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionsession.aspx). Dieses Ereignis wird Ihre app benachrichtigt, wenn einer der Befehle erkannt wurde.

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

Ihre **OnResultGenerated** Ereignishandler empfängt Ereignisdaten in einer [SpeechContinuousRecognitionResultGeneratedEventArgs](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechcontinuousrecognitionresultgeneratedeventargs.aspx) Instanz. Wenn das Vertrauen größer als der Schwellenwert, die Sie definiert haben ist, sollte Ihre app Beachten Sie, dass das Ereignis aufgetreten ist. Speichern Sie die Ereignisdaten, sodass Sie vornehmen können, es in einer Schleife nachfolgende Aktualisierung verwenden.

From *HolographicVoiceInputSampleMain.cpp*:

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

Stellen Sie jedoch Ihr app-Szenario für Daten verwenden. In unserem Beispielcode ändern wir die Farbe des – Hologramm sich drehenden Würfels gemäß des Benutzers-Befehl.

From *HolographicVoiceInputSampleMain::Update*:

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

## <a name="use-dictation-for-one-shot-recognition-of-speech-phrases-and-sentences"></a>Verwenden Sie für die One-Shot-Erkennung von Sprache Ausdrücken und Sätzen Diktat

Sie können eine Spracherkennung zum Lauschen auf Ausdrücke oder Sätze gesprochen, die vom Benutzer konfigurieren. In diesem Fall verwenden wir eine SpeechRecognitionTopicConstraint, der angibt, welche Art von Eingabe zu erwarten, dass der freigegebene Spracherkennung. Der app-Workflow ist wie folgt, und für diese Art von Anwendungsfall:
1. Ihre app erstellt die SpeechRecognizer, Benutzeroberfläche-eingabeaufforderungen bietet und beginnt die Überwachung für einen Befehl aus, um sofort gesprochen werden.
2. Der Benutzer spricht einen Ausdruck oder Satz.
3. Erkennung des Benutzers Spracheingabe wird ausgeführt, und ein Ergebnis an die app zurückgegeben wird. An diesem Punkt sollten Ihre app bereitstellen, Benutzeroberflächen-Eingabeaufforderung, der angibt, dass die Erkennung aufgetreten ist.
4. Abhängig von der Vertrauensgrad, die, dem Sie beantworten möchten, und der Vertrauensgrad, der das Erkennungsergebnis für die Sprache, kann Ihre app Verarbeiten des Ergebnisses und entsprechend reagieren.

Dieser Abschnitt beschreibt, wie Sie eine SpeechRecognizer erstellen, Kompilieren die Einschränkung und die Spracheingabe lauschen.

Der folgende Code kompiliert die Thema-Einschränkung, die in diesem Fall für die Suche im Web optimiert ist.

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

Wenn die Kompilierung erfolgreich war, können Sie mit der Spracherkennung fortfahren.

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

Das Ergebnis wird dann an die app zurückgegeben. Wenn wir sicher genug ist, im Ergebnis sind, können wir den Befehl verarbeiten. Dieses Codebeispiel werden Ergebnisse mindestens mittlere zuverlässig verarbeitet.

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

Wenn Sie die Spracherkennung verwenden, sollten Sie für Ausnahmen achten, die hinweisen, dass das Mikrofon in den Systemeinstellungen für den Datenschutz der Benutzer deaktiviert hat. Dies kann während der Initialisierung oder während der Erkennung vorkommen.

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

**HINWEIS:** Es gibt einige vordefinierte [SpeechRecognitionScenarios](https://msdn.microsoft.com/library/windows/apps/windows.media.speechrecognition.speechrecognitionscenario.aspx) zur Optimierung der Spracherkennung verfügbar.
* Wenn Sie die für Diktat optimieren möchten, verwenden Sie das Diktieren-Szenario:

```
// Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
```
* Verwendung von Spracherkennung Web gesucht werden soll, können Sie eine Web-spezifischen Szenario Einschränkung wie folgt:

```
// Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
```
* Verwenden Sie die Form-Einschränkung, um das Ausfüllen von Formularen. In diesem Fall empfiehlt es sich um Ihre eigenen Grammatik anzuwenden, die für das Formular ausfüllen optimiert ist.

```
// Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
```
* Sie können Ihre eigenen Grammatik, die mit dem SRGS-Format bereitstellen.

## <a name="use-continuous-freeform-speech-dictation"></a>Verwenden Sie fortlaufend, Freihandform-Spracherkennung Diktat

Finden Sie im Windows 10-UWP-Speech-Codebeispiel für das Szenario fortlaufendem diktieren [hier.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)

## <a name="handle-degradation-in-quality"></a>Behandeln Sie die Verringerung der Qualität

Bedingungen in der Umgebung können manchmal Spracherkennung verhindern. Z. B. im Raum ist möglicherweise zu viel Rauschen verursacht, oder der Benutzer kann mit zu hohem ein Volumen sprechen. Passen Sie die spracherkennungs-API-stellt Informationen bereit, wenn möglich, über die Bedingungen, die eine Verschlechterung in Qualität verursacht haben.

Diese Informationen wird auf Ihre app mit einer WinRT-Ereignis abgelegt. Hier ist ein Beispiel für dieses Ereignis abonnieren.

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

In unserem Codebeispiel wählen wir die Bedingungen Informationen in der Debugkonsole zu schreiben. Eine app kann für dem Benutzer über die Benutzeroberfläche, die Sprachsynthese und So weiter Feedback geben möchten, oder ggf. Verhalten sich anders, wenn die Sprache von eine temporäre Verringerung der Qualität unterbrochen wird.

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

Wenn Sie zum Erstellen Ihrer DirectX-app nicht Verweisklassen verwenden, müssen Sie das Ereignisabonnement vor dem Freigeben oder zum Neuerstellen Ihrer Spracherkennung. Die HolographicSpeechPromptSample verfügt über eine Routine zum Beenden der Erkennung und abbestellen von Ereignisabonnements wie folgt:

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

## <a name="use-speech-synthesis-to-provide-audible-voice-prompts"></a>Verwenden von Sprachsynthese zu akustische Sprachansagen

Die holographic Speech-Beispiele verwenden die Sprachsynthese akustische Anweisungen für den Benutzer bereitstellen. Dieses Thema führt durch den Prozess zum Erstellen einer synthetisierten Stimme-Beispiel und Wiedergabe wieder mithilfe der HRTF-audio-APIs.

Sie sollten Ihre eigenen Sprache aufgefordert, beim Anfordern des Ausdruck-Eingabe bereitstellen. Dies kann auch hilfreich, der angibt, sein, wenn Sprachbefehle können, für eine kontinuierliche Erkennung-Szenario gesprochen werden. Hier ist ein Beispiel dafür, wie dies mit einer Sprache-Synthesizer; Beachten Sie, dass Sie auch verwenden können, einen Clip aufgezeichnete Stimme, einer visuellen Benutzeroberfläche oder anderen Indikatoren der Vorgehensweise, z. B. in Szenarien sagen, wo die Eingabeaufforderung nicht dynamisch ist.

Erstellen Sie zunächst das Objekt "speechsynthesizer":

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

Außerdem benötigen Sie eine Zeichenfolge mit der Text, der umgewandelt werden soll:

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

Sprache wird asynchron mit SynthesizeTextToStreamAsync synthetisiert. Beginnen wir hier eine asynchrone Aufgabe, die sprachsynthetisier ein.

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

Die Sprachsynthese wird als Bytedatenstrom gesendet. Wir können eine XAudio2 Stimme, Byte-Stream initialisieren; Unsere holographic Codebeispiele wiedergeben wir es als ein HRTF Audioeffekts.

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

Wie die Spracherkennung löst Sprachsynthese eine Ausnahme, wenn etwas schief geht.

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

## <a name="see-also"></a>Siehe auch
* [Sprache-app-design](https://msdn.microsoft.com/library/dn596121.aspx)
* [Räumliche Sound in DirectX](spatial-sound-in-directx.md)
* [SpeechRecognitionAndSynthesis-Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
