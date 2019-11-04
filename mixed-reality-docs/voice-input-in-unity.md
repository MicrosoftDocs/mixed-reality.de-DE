---
title: Spracheingabe in Unity
description: Unity bietet drei Möglichkeiten zum Hinzufügen von Spracheingaben zu Ihrer Windows Mixed Reality-Anwendung.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Spracheingabe, keywordrecognizer, grammarerkenzer, Mikrofon, Diktat, Stimme
ms.openlocfilehash: d1cd2a2b954a195bc3f2688d915965f89aa30f98
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438198"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="240cf-104">Spracheingabe in Unity</span><span class="sxs-lookup"><span data-stu-id="240cf-104">Voice input in Unity</span></span>

>[!NOTE]
><span data-ttu-id="240cf-105">Verwenden Sie anstelle der folgenden Informationen das Unity-Plug-in für das Cognitive Speech Services SDK, das deutlich bessere Ergebnisse bei der sprach Genauigkeit bietet und einen einfachen Zugriff auf die sprach-zu-Text-Decodierung und erweiterte sprach Features wie Dialog, Intent-basiert bietet. Interaktion, Übersetzung, Text-zu-Sprache-Synthese und Spracherkennung in natürlicher Sprache.</span><span class="sxs-lookup"><span data-stu-id="240cf-105">Instead of the below information, consider using the Unity plug-in for the Cognitive Speech Services SDK which has much better Speech Accuracy results and provides easy access to speech-to-text decode and advanced speech features like dialog, intent based interaction, translation, text-to-speech synthesis and natural language speech recognition.</span></span> <span data-ttu-id="240cf-106">Hier finden Sie das Beispiel und Dokumentation: https://docs.microsoft.com//azure/cognitive-services/speech-service/quickstart-csharp-unity</span><span class="sxs-lookup"><span data-stu-id="240cf-106">Find the sample and documentaion here: https://docs.microsoft.com//azure/cognitive-services/speech-service/quickstart-csharp-unity</span></span>   

<span data-ttu-id="240cf-107">Unity bietet drei Möglichkeiten zum Hinzufügen von [Spracheingaben](voice-input.md) zu ihrer Unity-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="240cf-107">Unity exposes three ways to add [Voice input](voice-input.md) to your Unity application.</span></span>

<span data-ttu-id="240cf-108">Mit keywordrecognizer (einem von zwei Typen von phraserecognizers) kann Ihrer APP ein Array von Zeichen folgen Befehlen zugewiesen werden, die überwacht werden sollen.</span><span class="sxs-lookup"><span data-stu-id="240cf-108">With the KeywordRecognizer (one of two types of PhraseRecognizers), your app can be given an array of string commands to listen for.</span></span> <span data-ttu-id="240cf-109">Mit dem Grammatiken von Grammatiken (dem anderen Typ von phraserecognizer) kann Ihrer APP eine SRGS-Datei zugewiesen werden, die eine bestimmte Grammatik zum lauschen definiert.</span><span class="sxs-lookup"><span data-stu-id="240cf-109">With the GrammarRecognizer (the other type of PhraseRecognizer), your app can be given an SRGS file defining a specific grammar to listen for.</span></span> <span data-ttu-id="240cf-110">Mit dem "diktationerkenzer" kann Ihre APP auf ein beliebiges Wort lauschen und dem Benutzer einen Hinweis oder eine andere Anzeige seiner Sprache bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="240cf-110">With the DictationRecognizer, your app can listen for any word and provide the user with a note or other display of their speech.</span></span>

>[!NOTE]
><span data-ttu-id="240cf-111">Nur die Diktat-oder Ausdrucks Erkennung kann gleichzeitig behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="240cf-111">Only dictation or phrase recognition can be handled at once.</span></span> <span data-ttu-id="240cf-112">Dies bedeutet, dass ein "yntationerkenzer" nicht aktiv sein kann und umgekehrt ist, wenn ein "grammmarerkenzer" oder "keywordrecognizer" aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="240cf-112">That means if a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can not be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="240cf-113">Aktivieren der Sprachfunktion</span><span class="sxs-lookup"><span data-stu-id="240cf-113">Enabling the capability for Voice</span></span>

<span data-ttu-id="240cf-114">Die **Mikrofon** Funktion muss für eine APP deklariert werden, um die Spracheingabe zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="240cf-114">The **Microphone** capability must be declared for an app to leverage Voice input.</span></span>
1. <span data-ttu-id="240cf-115">Navigieren Sie im Unity-Editor zu den Player Einstellungen, indem Sie zu "> Projekteinstellungen bearbeiten > Player" navigieren.</span><span class="sxs-lookup"><span data-stu-id="240cf-115">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
2. <span data-ttu-id="240cf-116">Klicken Sie auf die Registerkarte "Windows Store".</span><span class="sxs-lookup"><span data-stu-id="240cf-116">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="240cf-117">Aktivieren Sie im Abschnitt "Veröffentlichungs Einstellungen > Funktionen" die **Mikrofon** Funktion.</span><span class="sxs-lookup"><span data-stu-id="240cf-117">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="240cf-118">Ausdrucks Erkennung</span><span class="sxs-lookup"><span data-stu-id="240cf-118">Phrase Recognition</span></span>

<span data-ttu-id="240cf-119">Damit Ihre APP auf bestimmte vom Benutzer gesprochene Ausdrücke lauschen kann, müssen Sie Folgendes tun:</span><span class="sxs-lookup"><span data-stu-id="240cf-119">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="240cf-120">Angeben der zu überwachenden Ausdrücke mithilfe eines keywordrecognizer-oder grammarerkenzer-Elements</span><span class="sxs-lookup"><span data-stu-id="240cf-120">Specify which phrases to listen for using a KeywordRecognizer or GrammarRecognizer</span></span>
2. <span data-ttu-id="240cf-121">Behandeln Sie das onphraserecognized-Ereignis, und ergreifen Sie entsprechende Aktionen für den erkannten Ausdruck.</span><span class="sxs-lookup"><span data-stu-id="240cf-121">Handle the OnPhraseRecognized event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="240cf-122">Keywordrecognizer</span><span class="sxs-lookup"><span data-stu-id="240cf-122">KeywordRecognizer</span></span>

<span data-ttu-id="240cf-123">**Namespace:** *unityengine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="240cf-123">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="240cf-124">**Typen:** *keywordrecognizer*, *phraserecognizedeventargs*, *delegatfehler*, Sprech *Systemstatus*</span><span class="sxs-lookup"><span data-stu-id="240cf-124">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="240cf-125">Zum Speichern einiger Tastatureingaben benötigen wir einige using-Anweisungen:</span><span class="sxs-lookup"><span data-stu-id="240cf-125">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="240cf-126">Fügen Sie der Klasse nun einige Felder hinzu, um das Erkennungs-und Schlüsselwort > Aktions Wörterbuch zu speichern:</span><span class="sxs-lookup"><span data-stu-id="240cf-126">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="240cf-127">Fügen Sie nun dem Wörterbuch ein Schlüsselwort hinzu (z. b. innerhalb einer Start ()-Methode).</span><span class="sxs-lookup"><span data-stu-id="240cf-127">Now add a keyword to the dictionary (e.g. inside of a Start() method).</span></span> <span data-ttu-id="240cf-128">Das Schlüsselwort "aktivieren" wird in diesem Beispiel hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="240cf-128">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="240cf-129">Erstellen Sie die Schlüsselwort Erkennung, und teilen Sie Ihnen mit, was wir erkennen möchten:</span><span class="sxs-lookup"><span data-stu-id="240cf-129">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="240cf-130">Registrieren Sie sich jetzt für das onphraserecognized-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="240cf-130">Now register for the OnPhraseRecognized event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="240cf-131">Ein Beispiel Handler ist:</span><span class="sxs-lookup"><span data-stu-id="240cf-131">An example handler is:</span></span>

```
private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    System.Action keywordAction;
    // if the keyword recognized is in our dictionary, call that Action.
    if (keywords.TryGetValue(args.text, out keywordAction))
    {
        keywordAction.Invoke();
    }
}
```

<span data-ttu-id="240cf-132">Beginnen Sie schließlich mit der Erkennung!</span><span class="sxs-lookup"><span data-stu-id="240cf-132">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="240cf-133">Grammarerkenzer</span><span class="sxs-lookup"><span data-stu-id="240cf-133">GrammarRecognizer</span></span>

<span data-ttu-id="240cf-134">**Namespace:** *unityengine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="240cf-134">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="240cf-135">**Typen**: *grammarerkenzer*, *phraserecognizedeventargs*, *delegatfehler*, Sprech *Systemstatus*</span><span class="sxs-lookup"><span data-stu-id="240cf-135">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="240cf-136">Die Grammatiken werden verwendet, wenn Sie Ihre Erkennungs Grammatik mithilfe von SRGS angeben.</span><span class="sxs-lookup"><span data-stu-id="240cf-136">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="240cf-137">Dies kann hilfreich sein, wenn Ihre APP mehr als nur einige wenige Schlüsselwörter aufweist, wenn Sie komplexere Ausdrücke erkennen möchten, oder wenn Sie Sätze von Befehlen problemlos aktivieren und deaktivieren möchten.</span><span class="sxs-lookup"><span data-stu-id="240cf-137">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="240cf-138">Informationen zum Dateiformat finden [Sie unter Erstellen von Grammatiken mithilfe von SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) .</span><span class="sxs-lookup"><span data-stu-id="240cf-138">See: [Create Grammars Using SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) for file format information.</span></span>

<span data-ttu-id="240cf-139">Sobald Sie die SRGS-Grammatik haben und sich in Ihrem Projekt in einem [Ordner "streamingassets](https://docs.unity3d.com/Manual/StreamingAssets.html)" befinden:</span><span class="sxs-lookup"><span data-stu-id="240cf-139">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](https://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="240cf-140">Erstellen Sie eine grammatisierungsklasse, und übergeben Sie Ihr den Pfad zu ihrer SRGS-Datei:</span><span class="sxs-lookup"><span data-stu-id="240cf-140">Create a GrammarRecognizer and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="240cf-141">Registrieren Sie sich jetzt für das onphraserecognized-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="240cf-141">Now register for the OnPhraseRecognized event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="240cf-142">Sie erhalten einen Rückruf mit Informationen, die in der SRGS-Grammatik angegeben sind, die Sie entsprechend behandeln können.</span><span class="sxs-lookup"><span data-stu-id="240cf-142">You will get a callback containing information specified in your SRGS grammar which you can handle appropriately.</span></span> <span data-ttu-id="240cf-143">Die meisten wichtigen Informationen werden im semanticbedeutungen-Array bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="240cf-143">Most of the important information will be provided in the semanticMeanings array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="240cf-144">Beginnen Sie schließlich mit der Erkennung!</span><span class="sxs-lookup"><span data-stu-id="240cf-144">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="240cf-145">Diktieren</span><span class="sxs-lookup"><span data-stu-id="240cf-145">Dictation</span></span>

<span data-ttu-id="240cf-146">**Namespace:** *unityengine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="240cf-146">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="240cf-147">**Typen**: " *diktationerkenzer*", "sprecherfehler", " *Redner Systemstatus*</span><span class="sxs-lookup"><span data-stu-id="240cf-147">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="240cf-148">Verwenden Sie das diktationerkenzer-Element, um die Sprache des Benutzers in Text zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="240cf-148">Use the DictationRecognizer to convert the user's speech to text.</span></span> <span data-ttu-id="240cf-149">Der Diktat-Erkennungs Modul macht [Diktat](voice-input.md#dictation) Funktionen verfügbar und unterstützt das registrieren und lauschen auf Hypothese und Ausdrucks fertige Ereignisse, sodass Sie Ihrem Benutzer Feedback geben können, während Sie sprechen und danach.</span><span class="sxs-lookup"><span data-stu-id="240cf-149">The DictationRecognizer exposes [dictation](voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="240cf-150">Die Methoden "Start ()" und "stoppt ()" aktivieren und deaktivieren die Diktat Erkennung.</span><span class="sxs-lookup"><span data-stu-id="240cf-150">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="240cf-151">Sobald die Erkennung erfolgt ist, sollte Sie mithilfe der verwerfen ()-Methode freigegeben werden, um die verwendeten Ressourcen freizugeben.</span><span class="sxs-lookup"><span data-stu-id="240cf-151">Once done with the recognizer, it should be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="240cf-152">Diese Ressourcen werden während Garbage Collection automatisch freigegeben, wenn Sie noch nicht freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="240cf-152">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>

<span data-ttu-id="240cf-153">Für den Einstieg in das Diktat müssen nur wenige Schritte ausgeführt werden:</span><span class="sxs-lookup"><span data-stu-id="240cf-153">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="240cf-154">Erstellen eines neuen "diktationerkenzer"</span><span class="sxs-lookup"><span data-stu-id="240cf-154">Create a new DictationRecognizer</span></span>
2. <span data-ttu-id="240cf-155">Behandeln von Diktat Ereignissen</span><span class="sxs-lookup"><span data-stu-id="240cf-155">Handle Dictation events</span></span>
3. <span data-ttu-id="240cf-156">"Diktationerkenzer" starten</span><span class="sxs-lookup"><span data-stu-id="240cf-156">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="240cf-157">Aktivieren der Funktion für das Diktat</span><span class="sxs-lookup"><span data-stu-id="240cf-157">Enabling the capability for dictation</span></span>

<span data-ttu-id="240cf-158">Die Funktion "Internet Client" muss zusätzlich zu der oben erwähnten Funktion "Mikrofon" deklariert werden, damit eine Anwendung die Diktat Funktion nutzt.</span><span class="sxs-lookup"><span data-stu-id="240cf-158">The "Internet Client" capability, in addition to the "Microphone" capability mentioned above, must be declared for an app to leverage dictation.</span></span>
1. <span data-ttu-id="240cf-159">Navigieren Sie im Unity-Editor zu den Player Einstellungen, indem Sie zur Seite "> Projekteinstellungen bearbeiten > Player" navigieren.</span><span class="sxs-lookup"><span data-stu-id="240cf-159">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="240cf-160">Klicken Sie auf die Registerkarte "Windows Store".</span><span class="sxs-lookup"><span data-stu-id="240cf-160">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="240cf-161">Überprüfen Sie im Abschnitt "Veröffentlichungs Einstellungen > Funktionen" die Funktion " **Internetclient** ".</span><span class="sxs-lookup"><span data-stu-id="240cf-161">In the "Publishing Settings > Capabilities" section, check the **InternetClient** capability</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="240cf-162">Diktationerkenzer</span><span class="sxs-lookup"><span data-stu-id="240cf-162">DictationRecognizer</span></span>

<span data-ttu-id="240cf-163">Erstellen Sie einen "diktationerkenzer" wie folgt:</span><span class="sxs-lookup"><span data-stu-id="240cf-163">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="240cf-164">Es gibt vier Diktat Ereignisse, die abonniert und behandelt werden können, um das Diktat Verhalten zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="240cf-164">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. <span data-ttu-id="240cf-165">"Ditationresult"</span><span class="sxs-lookup"><span data-stu-id="240cf-165">DictationResult</span></span>
2. <span data-ttu-id="240cf-166">"Ditationcomplete"</span><span class="sxs-lookup"><span data-stu-id="240cf-166">DictationComplete</span></span>
3. <span data-ttu-id="240cf-167">"Ditationhypothese"</span><span class="sxs-lookup"><span data-stu-id="240cf-167">DictationHypothesis</span></span>
4. <span data-ttu-id="240cf-168">"Ditationerror"</span><span class="sxs-lookup"><span data-stu-id="240cf-168">DictationError</span></span>

<span data-ttu-id="240cf-169">**"Ditationresult"**</span><span class="sxs-lookup"><span data-stu-id="240cf-169">**DictationResult**</span></span>

<span data-ttu-id="240cf-170">Dieses Ereignis wird ausgelöst, nachdem der Benutzer angehalten wurde, in der Regel am Ende eines Satzes.</span><span class="sxs-lookup"><span data-stu-id="240cf-170">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="240cf-171">Hier wird die vollständig erkannte Zeichenfolge zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="240cf-171">The full recognized string is returned here.</span></span>

<span data-ttu-id="240cf-172">Abonnieren Sie zunächst das Ereignis "" für das ""-Ereignis:</span><span class="sxs-lookup"><span data-stu-id="240cf-172">First, subscribe to the DictationResult event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="240cf-173">Behandeln Sie dann den "-Rückruf":</span><span class="sxs-lookup"><span data-stu-id="240cf-173">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="240cf-174">**"Ditationhypothese"**</span><span class="sxs-lookup"><span data-stu-id="240cf-174">**DictationHypothesis**</span></span>

<span data-ttu-id="240cf-175">Dieses Ereignis wird fortlaufend ausgelöst, während der Benutzer spricht.</span><span class="sxs-lookup"><span data-stu-id="240cf-175">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="240cf-176">Wie die Erkennung hört, bietet Sie Text zu den bisher gehörenden.</span><span class="sxs-lookup"><span data-stu-id="240cf-176">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="240cf-177">Abonnieren Sie zunächst das Ereignis "ditationhypothese":</span><span class="sxs-lookup"><span data-stu-id="240cf-177">First, subscribe to the DictationHypothesis event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="240cf-178">Behandeln Sie dann den-Rückruf von "ditationhypothese":</span><span class="sxs-lookup"><span data-stu-id="240cf-178">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="240cf-179">**"Ditationcomplete"**</span><span class="sxs-lookup"><span data-stu-id="240cf-179">**DictationComplete**</span></span>

<span data-ttu-id="240cf-180">Dieses Ereignis wird ausgelöst, wenn die Erkennung angehalten wird, und zwar unabhängig davon, ob von "Stopp ()" aufgerufen wird, ein Timeout auftritt oder ein anderer Fehler vorliegt.</span><span class="sxs-lookup"><span data-stu-id="240cf-180">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="240cf-181">Abonnieren Sie zunächst das Ereignis "" für das Ereignis "".</span><span class="sxs-lookup"><span data-stu-id="240cf-181">First, subscribe to the DictationComplete event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="240cf-182">Behandeln Sie dann den-Rückruf von "ditationcomplete":</span><span class="sxs-lookup"><span data-stu-id="240cf-182">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="240cf-183">**"Ditationerror"**</span><span class="sxs-lookup"><span data-stu-id="240cf-183">**DictationError**</span></span>

<span data-ttu-id="240cf-184">Dieses Ereignis wird ausgelöst, wenn ein Fehler auftritt.</span><span class="sxs-lookup"><span data-stu-id="240cf-184">This event is fired when an error occurs.</span></span>

<span data-ttu-id="240cf-185">Abonnieren Sie zunächst das Ereignis "" für "" "".</span><span class="sxs-lookup"><span data-stu-id="240cf-185">First, subscribe to the DictationError event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="240cf-186">Behandeln Sie dann den "-Rückruf"-Rückruf:</span><span class="sxs-lookup"><span data-stu-id="240cf-186">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="240cf-187">Nachdem Sie die Diktat Ereignisse abonniert und behandelt haben, die Ihnen wichtig sind, starten Sie die Diktat Erkennung, um mit dem empfangen von Ereignissen zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="240cf-187">Once you have subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="240cf-188">Wenn Sie die "diktationerkenzer" nicht mehr benötigen, müssen Sie die Ereignisse kündigen und den "diktationerkenzer" verwerfen.</span><span class="sxs-lookup"><span data-stu-id="240cf-188">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="240cf-189">**Chti**</span><span class="sxs-lookup"><span data-stu-id="240cf-189">**Tips**</span></span>
* <span data-ttu-id="240cf-190">Die Methoden "Start ()" und "stoppt ()" aktivieren und deaktivieren die Diktat Erkennung.</span><span class="sxs-lookup"><span data-stu-id="240cf-190">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="240cf-191">Sobald die Erkennung erfolgt ist, muss Sie mithilfe der Methode "verwerfen ()" freigegeben werden, um die verwendeten Ressourcen freizugeben.</span><span class="sxs-lookup"><span data-stu-id="240cf-191">Once done with the recognizer, it must be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="240cf-192">Diese Ressourcen werden während Garbage Collection automatisch freigegeben, wenn Sie noch nicht freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="240cf-192">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>
* <span data-ttu-id="240cf-193">Timeouts treten nach einer festgelegten Zeitspanne auf.</span><span class="sxs-lookup"><span data-stu-id="240cf-193">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="240cf-194">Sie können diese Timeouts im Ereignis "ditationcomplete" überprüfen.</span><span class="sxs-lookup"><span data-stu-id="240cf-194">You can check for these timeouts in the DictationComplete event.</span></span> <span data-ttu-id="240cf-195">Es gibt zwei Timeouts, die Sie beachten sollten:</span><span class="sxs-lookup"><span data-stu-id="240cf-195">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="240cf-196">Wenn die Erkennung startet und keine Audiodaten für die ersten fünf Sekunden hört, wird ein Timeout angezeigt.</span><span class="sxs-lookup"><span data-stu-id="240cf-196">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
   2. <span data-ttu-id="240cf-197">Wenn die Erkennung ein Ergebnis erhalten hat, dann aber für einen Zeitraum von 20 Sekunden den Ruhe Wert erfährt, wird ein Timeout verursacht.</span><span class="sxs-lookup"><span data-stu-id="240cf-197">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="240cf-198">Verwenden der Ausdrucks Erkennung und-diktierung</span><span class="sxs-lookup"><span data-stu-id="240cf-198">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="240cf-199">Wenn Sie in Ihrer APP sowohl die Erkennung als auch das Diktat von Ausdrücken verwenden möchten, müssen Sie eine vollständige Herunterfahren, bevor Sie die andere starten können.</span><span class="sxs-lookup"><span data-stu-id="240cf-199">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="240cf-200">Wenn mehrere keywordrecognizers ausgeführt werden, können Sie Sie mit folgenden Aktionen gleichzeitig Herunterfahren:</span><span class="sxs-lookup"><span data-stu-id="240cf-200">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="240cf-201">Wenn Sie alle erkenners in Ihrem vorherigen Zustand wiederherstellen möchten, können Sie nach dem Beenden von "diktationerkenzer" Folgendes aufzurufen:</span><span class="sxs-lookup"><span data-stu-id="240cf-201">In order to restore all recognizers to their previous state, after the DictationRecognizer has stopped, you can call:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="240cf-202">Sie können auch einfach einen keywordrecognizer starten, mit dem auch das phraserecognitionsystem neu gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="240cf-202">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="using-the-microphone-helper"></a><span data-ttu-id="240cf-203">Verwenden des Mikrofon-Hilfsprogramms</span><span class="sxs-lookup"><span data-stu-id="240cf-203">Using the microphone helper</span></span>

<span data-ttu-id="240cf-204">Das Mixed Reality Toolkit auf GitHub enthält eine Mikrofon-Hilfsklasse, mit der Entwickler darauf hinweisen können, ob im System ein brauchbares Mikrofon vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="240cf-204">The Mixed Reality Toolkit on GitHub contains a microphone helper class to hint at developers if there is a usable microphone on the system.</span></span> <span data-ttu-id="240cf-205">Eine Verwendung hierfür ist der Ort, an dem überprüft werden soll, ob ein Mikrofon im System vorhanden ist, bevor sprach Interaktions Hinweise in der Anwendung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="240cf-205">One use for it is where one would want to check if there is microphone on system before showing any speech interaction hints in the application.</span></span>

<span data-ttu-id="240cf-206">Das Mikrofon-Hilfsobjekt befindet sich im [Ordner Input/Scripts/Utilities](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span><span class="sxs-lookup"><span data-stu-id="240cf-206">The microphone helper script can be found in the [Input/Scripts/Utilities folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span></span> <span data-ttu-id="240cf-207">Das GitHub-Repository enthält auch ein [kleines Beispiel](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) , das zeigt, wie das Hilfsprogramm verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="240cf-207">The GitHub repo also contains a [small sample](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) demonstrating how to use the helper.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="240cf-208">Spracheingabe im Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="240cf-208">Voice input in Mixed Reality Toolkit</span></span>
<span data-ttu-id="240cf-209">Die Beispiele für die Spracheingabe finden Sie in dieser Szene.</span><span class="sxs-lookup"><span data-stu-id="240cf-209">You can find the examples of the voice input in this scene.</span></span>

- [<span data-ttu-id="240cf-210">HoloToolkit-examples/Input/Szenen/speechinputsource. unity</span><span class="sxs-lookup"><span data-stu-id="240cf-210">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
