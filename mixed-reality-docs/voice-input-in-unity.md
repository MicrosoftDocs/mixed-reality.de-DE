---
title: Spracheingabe in Unity
description: Unity bietet drei Möglichkeiten zum Hinzufügen von Spracheingaben zu Ihrer Windows Mixed Reality-Anwendung.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Spracheingabe, keywordrecognizer, grammarerkenzer, Mikrofon, Diktat, Stimme
ms.openlocfilehash: ef8114a1c877fe9b858122e0c64628d4b71a69cd
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548685"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="88991-104">Spracheingabe in Unity</span><span class="sxs-lookup"><span data-stu-id="88991-104">Voice input in Unity</span></span>

<span data-ttu-id="88991-105">Unity bietet drei Möglichkeiten zum Hinzufügen von [Spracheingaben](voice-input.md) zu ihrer Unity-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="88991-105">Unity exposes three ways to add [Voice input](voice-input.md) to your Unity application.</span></span>

<span data-ttu-id="88991-106">Mit keywordrecognizer (einem von zwei Typen von phraserecognizers) kann Ihrer APP ein Array von Zeichen folgen Befehlen zugewiesen werden, die überwacht werden sollen.</span><span class="sxs-lookup"><span data-stu-id="88991-106">With the KeywordRecognizer (one of two types of PhraseRecognizers), your app can be given an array of string commands to listen for.</span></span> <span data-ttu-id="88991-107">Mit dem Grammatiken von Grammatiken (dem anderen Typ von phraserecognizer) kann Ihrer APP eine SRGS-Datei zugewiesen werden, die eine bestimmte Grammatik zum lauschen definiert.</span><span class="sxs-lookup"><span data-stu-id="88991-107">With the GrammarRecognizer (the other type of PhraseRecognizer), your app can be given an SRGS file defining a specific grammar to listen for.</span></span> <span data-ttu-id="88991-108">Mit dem "diktationerkenzer" kann Ihre APP auf ein beliebiges Wort lauschen und dem Benutzer einen Hinweis oder eine andere Anzeige seiner Sprache bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="88991-108">With the DictationRecognizer, your app can listen for any word and provide the user with a note or other display of their speech.</span></span>

>[!NOTE]
><span data-ttu-id="88991-109">Nur die Diktat-oder Ausdrucks Erkennung kann gleichzeitig behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="88991-109">Only dictation or phrase recognition can be handled at once.</span></span> <span data-ttu-id="88991-110">Dies bedeutet, dass ein "yntationerkenzer" nicht aktiv sein kann und umgekehrt ist, wenn ein "grammmarerkenzer" oder "keywordrecognizer" aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="88991-110">That means if a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can not be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="88991-111">Aktivieren der Sprachfunktion</span><span class="sxs-lookup"><span data-stu-id="88991-111">Enabling the capability for Voice</span></span>

<span data-ttu-id="88991-112">Die **Mikrofon** Funktion muss für eine APP deklariert werden, um die Spracheingabe zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="88991-112">The **Microphone** capability must be declared for an app to leverage Voice input.</span></span>
1. <span data-ttu-id="88991-113">Navigieren Sie im Unity-Editor zu den Player Einstellungen, indem Sie zu "> Projekteinstellungen bearbeiten > Player" navigieren.</span><span class="sxs-lookup"><span data-stu-id="88991-113">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
2. <span data-ttu-id="88991-114">Klicken Sie auf die Registerkarte "Windows Store".</span><span class="sxs-lookup"><span data-stu-id="88991-114">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="88991-115">Aktivieren Sie im Abschnitt "Veröffentlichungs Einstellungen > Funktionen" die **Mikrofon** Funktion.</span><span class="sxs-lookup"><span data-stu-id="88991-115">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="88991-116">Ausdrucks Erkennung</span><span class="sxs-lookup"><span data-stu-id="88991-116">Phrase Recognition</span></span>

<span data-ttu-id="88991-117">Damit Ihre APP auf bestimmte vom Benutzer gesprochene Ausdrücke lauschen kann, müssen Sie Folgendes tun:</span><span class="sxs-lookup"><span data-stu-id="88991-117">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="88991-118">Angeben der zu überwachenden Ausdrücke mithilfe eines keywordrecognizer-oder grammarerkenzer-Elements</span><span class="sxs-lookup"><span data-stu-id="88991-118">Specify which phrases to listen for using a KeywordRecognizer or GrammarRecognizer</span></span>
2. <span data-ttu-id="88991-119">Behandeln Sie das onphraserecognized-Ereignis, und ergreifen Sie entsprechende Aktionen für den erkannten Ausdruck.</span><span class="sxs-lookup"><span data-stu-id="88991-119">Handle the OnPhraseRecognized event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="88991-120">Keywordrecognizer</span><span class="sxs-lookup"><span data-stu-id="88991-120">KeywordRecognizer</span></span>

<span data-ttu-id="88991-121">**Namespace:** *Unityengine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="88991-121">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="88991-122">**Solche** *Keywordrecognizer*, *phraserecognizedeventargs*, *Sprachfehler*, *Sprachsystem Status*</span><span class="sxs-lookup"><span data-stu-id="88991-122">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="88991-123">Zum Speichern einiger Tastatureingaben benötigen wir einige using-Anweisungen:</span><span class="sxs-lookup"><span data-stu-id="88991-123">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="88991-124">Fügen Sie der Klasse nun einige Felder hinzu, um das Erkennungs-und Schlüsselwort > Aktions Wörterbuch zu speichern:</span><span class="sxs-lookup"><span data-stu-id="88991-124">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="88991-125">Fügen Sie nun dem Wörterbuch ein Schlüsselwort hinzu (z. b. innerhalb einer Start ()-Methode).</span><span class="sxs-lookup"><span data-stu-id="88991-125">Now add a keyword to the dictionary (e.g. inside of a Start() method).</span></span> <span data-ttu-id="88991-126">Das Schlüsselwort "aktivieren" wird in diesem Beispiel hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="88991-126">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="88991-127">Erstellen Sie die Schlüsselwort Erkennung, und teilen Sie Ihnen mit, was wir erkennen möchten:</span><span class="sxs-lookup"><span data-stu-id="88991-127">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="88991-128">Registrieren Sie sich jetzt für das onphraserecognized-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="88991-128">Now register for the OnPhraseRecognized event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="88991-129">Ein Beispiel Handler ist:</span><span class="sxs-lookup"><span data-stu-id="88991-129">An example handler is:</span></span>

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

<span data-ttu-id="88991-130">Beginnen Sie schließlich mit der Erkennung!</span><span class="sxs-lookup"><span data-stu-id="88991-130">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="88991-131">Grammarerkenzer</span><span class="sxs-lookup"><span data-stu-id="88991-131">GrammarRecognizer</span></span>

<span data-ttu-id="88991-132">**Namespace:** *Unityengine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="88991-132">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="88991-133">**Typen**: *Grammarerkenzer*, *phraserecognizedeventargs*, *Sprachfehler*, *Sprachsystem Status*</span><span class="sxs-lookup"><span data-stu-id="88991-133">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="88991-134">Die Grammatiken werden verwendet, wenn Sie Ihre Erkennungs Grammatik mithilfe von SRGS angeben.</span><span class="sxs-lookup"><span data-stu-id="88991-134">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="88991-135">Dies kann hilfreich sein, wenn Ihre APP mehr als nur einige wenige Schlüsselwörter aufweist, wenn Sie komplexere Ausdrücke erkennen möchten, oder wenn Sie Sätze von Befehlen problemlos aktivieren und deaktivieren möchten.</span><span class="sxs-lookup"><span data-stu-id="88991-135">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="88991-136">Thema [Erstellen Sie Grammatiken mithilfe von SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) für Dateiformat Informationen.</span><span class="sxs-lookup"><span data-stu-id="88991-136">See: [Create Grammars Using SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) for file format information.</span></span>

<span data-ttu-id="88991-137">Sobald Sie die SRGS-Grammatik haben und sich in Ihrem Projekt in einem [Ordner "streamingassets](http://docs.unity3d.com/Manual/StreamingAssets.html)" befinden:</span><span class="sxs-lookup"><span data-stu-id="88991-137">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](http://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="88991-138">Erstellen Sie eine grammatisierungsklasse, und übergeben Sie Ihr den Pfad zu ihrer SRGS-Datei:</span><span class="sxs-lookup"><span data-stu-id="88991-138">Create a GrammarRecognizer and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="88991-139">Registrieren Sie sich jetzt für das onphraserecognized-Ereignis.</span><span class="sxs-lookup"><span data-stu-id="88991-139">Now register for the OnPhraseRecognized event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="88991-140">Sie erhalten einen Rückruf mit Informationen, die in der SRGS-Grammatik angegeben sind, die Sie entsprechend behandeln können.</span><span class="sxs-lookup"><span data-stu-id="88991-140">You will get a callback containing information specified in your SRGS grammar which you can handle appropriately.</span></span> <span data-ttu-id="88991-141">Die meisten wichtigen Informationen werden im semanticbedeutungen-Array bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="88991-141">Most of the important information will be provided in the semanticMeanings array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="88991-142">Beginnen Sie schließlich mit der Erkennung!</span><span class="sxs-lookup"><span data-stu-id="88991-142">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="88991-143">Diktieren</span><span class="sxs-lookup"><span data-stu-id="88991-143">Dictation</span></span>

<span data-ttu-id="88991-144">**Namespace:** *Unityengine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="88991-144">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="88991-145">**Typen**: " *Diktationerkenzer*", "sprecherfehler", " *Redner Systemstatus*</span><span class="sxs-lookup"><span data-stu-id="88991-145">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="88991-146">Verwenden Sie das diktationerkenzer-Element, um die Sprache des Benutzers in Text zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="88991-146">Use the DictationRecognizer to convert the user's speech to text.</span></span> <span data-ttu-id="88991-147">Der Diktat-Erkennungs Modul macht [Diktat](voice-input.md#dictation) Funktionen verfügbar und unterstützt das registrieren und lauschen auf Hypothese und Ausdrucks fertige Ereignisse, sodass Sie Ihrem Benutzer Feedback geben können, während Sie sprechen und danach.</span><span class="sxs-lookup"><span data-stu-id="88991-147">The DictationRecognizer exposes [dictation](voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="88991-148">Die Methoden "Start ()" und "stoppt ()" aktivieren und deaktivieren die Diktat Erkennung.</span><span class="sxs-lookup"><span data-stu-id="88991-148">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="88991-149">Sobald die Erkennung erfolgt ist, sollte Sie mithilfe der verwerfen ()-Methode freigegeben werden, um die verwendeten Ressourcen freizugeben.</span><span class="sxs-lookup"><span data-stu-id="88991-149">Once done with the recognizer, it should be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="88991-150">Diese Ressourcen werden während Garbage Collection automatisch freigegeben, wenn Sie noch nicht freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="88991-150">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>

<span data-ttu-id="88991-151">Für den Einstieg in das Diktat müssen nur wenige Schritte ausgeführt werden:</span><span class="sxs-lookup"><span data-stu-id="88991-151">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="88991-152">Erstellen eines neuen "diktationerkenzer"</span><span class="sxs-lookup"><span data-stu-id="88991-152">Create a new DictationRecognizer</span></span>
2. <span data-ttu-id="88991-153">Behandeln von Diktat Ereignissen</span><span class="sxs-lookup"><span data-stu-id="88991-153">Handle Dictation events</span></span>
3. <span data-ttu-id="88991-154">"Diktationerkenzer" starten</span><span class="sxs-lookup"><span data-stu-id="88991-154">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="88991-155">Aktivieren der Funktion für das Diktat</span><span class="sxs-lookup"><span data-stu-id="88991-155">Enabling the capability for dictation</span></span>

<span data-ttu-id="88991-156">Die Funktion "Internet Client" muss zusätzlich zu der oben erwähnten Funktion "Mikrofon" deklariert werden, damit eine Anwendung die Diktat Funktion nutzt.</span><span class="sxs-lookup"><span data-stu-id="88991-156">The "Internet Client" capability, in addition to the "Microphone" capability mentioned above, must be declared for an app to leverage dictation.</span></span>
1. <span data-ttu-id="88991-157">Navigieren Sie im Unity-Editor zu den Player Einstellungen, indem Sie zur Seite "> Projekteinstellungen bearbeiten > Player" navigieren.</span><span class="sxs-lookup"><span data-stu-id="88991-157">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="88991-158">Klicken Sie auf die Registerkarte "Windows Store".</span><span class="sxs-lookup"><span data-stu-id="88991-158">Click on the "Windows Store" tab</span></span>
3. <span data-ttu-id="88991-159">Überprüfen Sie im Abschnitt "Veröffentlichungs Einstellungen > Funktionen" die Funktion " **Internetclient** ".</span><span class="sxs-lookup"><span data-stu-id="88991-159">In the "Publishing Settings > Capabilities" section, check the **InternetClient** capability</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="88991-160">Diktationerkenzer</span><span class="sxs-lookup"><span data-stu-id="88991-160">DictationRecognizer</span></span>

<span data-ttu-id="88991-161">Erstellen Sie einen "diktationerkenzer" wie folgt:</span><span class="sxs-lookup"><span data-stu-id="88991-161">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="88991-162">Es gibt vier Diktat Ereignisse, die abonniert und behandelt werden können, um das Diktat Verhalten zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="88991-162">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. <span data-ttu-id="88991-163">"Ditationresult"</span><span class="sxs-lookup"><span data-stu-id="88991-163">DictationResult</span></span>
2. <span data-ttu-id="88991-164">"Ditationcomplete"</span><span class="sxs-lookup"><span data-stu-id="88991-164">DictationComplete</span></span>
3. <span data-ttu-id="88991-165">"Ditationhypothese"</span><span class="sxs-lookup"><span data-stu-id="88991-165">DictationHypothesis</span></span>
4. <span data-ttu-id="88991-166">"Ditationerror"</span><span class="sxs-lookup"><span data-stu-id="88991-166">DictationError</span></span>

<span data-ttu-id="88991-167">**"Ditationresult"**</span><span class="sxs-lookup"><span data-stu-id="88991-167">**DictationResult**</span></span>

<span data-ttu-id="88991-168">Dieses Ereignis wird ausgelöst, nachdem der Benutzer angehalten wurde, in der Regel am Ende eines Satzes.</span><span class="sxs-lookup"><span data-stu-id="88991-168">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="88991-169">Hier wird die vollständig erkannte Zeichenfolge zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="88991-169">The full recognized string is returned here.</span></span>

<span data-ttu-id="88991-170">Abonnieren Sie zunächst das Ereignis "" für das ""-Ereignis:</span><span class="sxs-lookup"><span data-stu-id="88991-170">First, subscribe to the DictationResult event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="88991-171">Behandeln Sie dann den "-Rückruf":</span><span class="sxs-lookup"><span data-stu-id="88991-171">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="88991-172">**"Ditationhypothese"**</span><span class="sxs-lookup"><span data-stu-id="88991-172">**DictationHypothesis**</span></span>

<span data-ttu-id="88991-173">Dieses Ereignis wird fortlaufend ausgelöst, während der Benutzer spricht.</span><span class="sxs-lookup"><span data-stu-id="88991-173">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="88991-174">Wie die Erkennung hört, bietet Sie Text zu den bisher gehörenden.</span><span class="sxs-lookup"><span data-stu-id="88991-174">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="88991-175">Abonnieren Sie zunächst das Ereignis "ditationhypothese":</span><span class="sxs-lookup"><span data-stu-id="88991-175">First, subscribe to the DictationHypothesis event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="88991-176">Behandeln Sie dann den-Rückruf von "ditationhypothese":</span><span class="sxs-lookup"><span data-stu-id="88991-176">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="88991-177">**"Ditationcomplete"**</span><span class="sxs-lookup"><span data-stu-id="88991-177">**DictationComplete**</span></span>

<span data-ttu-id="88991-178">Dieses Ereignis wird ausgelöst, wenn die Erkennung angehalten wird, und zwar unabhängig davon, ob von "Stopp ()" aufgerufen wird, ein Timeout auftritt oder ein anderer Fehler vorliegt.</span><span class="sxs-lookup"><span data-stu-id="88991-178">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="88991-179">Abonnieren Sie zunächst das Ereignis "" für das Ereignis "".</span><span class="sxs-lookup"><span data-stu-id="88991-179">First, subscribe to the DictationComplete event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="88991-180">Behandeln Sie dann den-Rückruf von "ditationcomplete":</span><span class="sxs-lookup"><span data-stu-id="88991-180">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="88991-181">**"Ditationerror"**</span><span class="sxs-lookup"><span data-stu-id="88991-181">**DictationError**</span></span>

<span data-ttu-id="88991-182">Dieses Ereignis wird ausgelöst, wenn ein Fehler auftritt.</span><span class="sxs-lookup"><span data-stu-id="88991-182">This event is fired when an error occurs.</span></span>

<span data-ttu-id="88991-183">Abonnieren Sie zunächst das Ereignis "" für "" "".</span><span class="sxs-lookup"><span data-stu-id="88991-183">First, subscribe to the DictationError event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="88991-184">Behandeln Sie dann den "-Rückruf"-Rückruf:</span><span class="sxs-lookup"><span data-stu-id="88991-184">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="88991-185">Nachdem Sie die Diktat Ereignisse abonniert und behandelt haben, die Ihnen wichtig sind, starten Sie die Diktat Erkennung, um mit dem empfangen von Ereignissen zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="88991-185">Once you have subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="88991-186">Wenn Sie die "diktationerkenzer" nicht mehr benötigen, müssen Sie die Ereignisse kündigen und den "diktationerkenzer" verwerfen.</span><span class="sxs-lookup"><span data-stu-id="88991-186">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="88991-187">**Chti**</span><span class="sxs-lookup"><span data-stu-id="88991-187">**Tips**</span></span>
* <span data-ttu-id="88991-188">Die Methoden "Start ()" und "stoppt ()" aktivieren und deaktivieren die Diktat Erkennung.</span><span class="sxs-lookup"><span data-stu-id="88991-188">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="88991-189">Sobald die Erkennung erfolgt ist, muss Sie mithilfe der Methode "verwerfen ()" freigegeben werden, um die verwendeten Ressourcen freizugeben.</span><span class="sxs-lookup"><span data-stu-id="88991-189">Once done with the recognizer, it must be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="88991-190">Diese Ressourcen werden während Garbage Collection automatisch freigegeben, wenn Sie noch nicht freigegeben werden.</span><span class="sxs-lookup"><span data-stu-id="88991-190">It will release these resources automatically during garbage collection at an additional performance cost if they are not released prior to that.</span></span>
* <span data-ttu-id="88991-191">Timeouts treten nach einer festgelegten Zeitspanne auf.</span><span class="sxs-lookup"><span data-stu-id="88991-191">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="88991-192">Sie können diese Timeouts im Ereignis "ditationcomplete" überprüfen.</span><span class="sxs-lookup"><span data-stu-id="88991-192">You can check for these timeouts in the DictationComplete event.</span></span> <span data-ttu-id="88991-193">Es gibt zwei Timeouts, die Sie beachten sollten:</span><span class="sxs-lookup"><span data-stu-id="88991-193">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="88991-194">Wenn die Erkennung startet und keine Audiodaten für die ersten fünf Sekunden hört, wird ein Timeout angezeigt.</span><span class="sxs-lookup"><span data-stu-id="88991-194">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
   2. <span data-ttu-id="88991-195">Wenn die Erkennung ein Ergebnis erhalten hat, dann aber für einen Zeitraum von 20 Sekunden den Ruhe Wert erfährt, wird ein Timeout verursacht.</span><span class="sxs-lookup"><span data-stu-id="88991-195">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="88991-196">Verwenden der Ausdrucks Erkennung und-diktierung</span><span class="sxs-lookup"><span data-stu-id="88991-196">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="88991-197">Wenn Sie in Ihrer APP sowohl die Erkennung als auch das Diktat von Ausdrücken verwenden möchten, müssen Sie eine vollständige Herunterfahren, bevor Sie die andere starten können.</span><span class="sxs-lookup"><span data-stu-id="88991-197">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="88991-198">Wenn mehrere keywordrecognizers ausgeführt werden, können Sie Sie mit folgenden Aktionen gleichzeitig Herunterfahren:</span><span class="sxs-lookup"><span data-stu-id="88991-198">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="88991-199">Wenn Sie alle erkenners in Ihrem vorherigen Zustand wiederherstellen möchten, können Sie nach dem Beenden von "diktationerkenzer" Folgendes aufzurufen:</span><span class="sxs-lookup"><span data-stu-id="88991-199">In order to restore all recognizers to their previous state, after the DictationRecognizer has stopped, you can call:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="88991-200">Sie können auch einfach einen keywordrecognizer starten, mit dem auch das phraserecognitionsystem neu gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="88991-200">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="using-the-microphone-helper"></a><span data-ttu-id="88991-201">Verwenden des Mikrofon-Hilfsprogramms</span><span class="sxs-lookup"><span data-stu-id="88991-201">Using the microphone helper</span></span>

<span data-ttu-id="88991-202">Das Mixed Reality Toolkit auf GitHub enthält eine Mikrofon-Hilfsklasse, mit der Entwickler darauf hinweisen können, ob im System ein brauchbares Mikrofon vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="88991-202">The Mixed Reality Toolkit on GitHub contains a microphone helper class to hint at developers if there is a usable microphone on the system.</span></span> <span data-ttu-id="88991-203">Eine Verwendung hierfür ist der Ort, an dem überprüft werden soll, ob ein Mikrofon im System vorhanden ist, bevor sprach Interaktions Hinweise in der Anwendung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="88991-203">One use for it is where one would want to check if there is microphone on system before showing any speech interaction hints in the application.</span></span>

<span data-ttu-id="88991-204">Das Mikrofon-Hilfsobjekt befindet sich im [Ordner Input/Scripts/Utilities](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span><span class="sxs-lookup"><span data-stu-id="88991-204">The microphone helper script can be found in the [Input/Scripts/Utilities folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span></span> <span data-ttu-id="88991-205">Das GitHub-Repository enthält auch ein [kleines Beispiel](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) , das zeigt, wie das Hilfsprogramm verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="88991-205">The GitHub repo also contains a [small sample](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) demonstrating how to use the helper.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="88991-206">Spracheingabe im Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="88991-206">Voice input in Mixed Reality Toolkit</span></span>
<span data-ttu-id="88991-207">Die Beispiele für die Spracheingabe finden Sie in dieser Szene.</span><span class="sxs-lookup"><span data-stu-id="88991-207">You can find the examples of the voice input in this scene.</span></span>

- [<span data-ttu-id="88991-208">HoloToolkit-examples/Input/Szenen/speechinputsource. unity</span><span class="sxs-lookup"><span data-stu-id="88991-208">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
