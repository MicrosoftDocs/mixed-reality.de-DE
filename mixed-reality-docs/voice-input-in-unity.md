---
title: Spracheingabe in Unity
description: Unity stellt drei Möglichkeiten zum Hinzufügen von Spracheingabe für Ihre Windows Mixed Reality-Anwendung.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Voice input, KeywordRecognizer, GrammarRecognizer, microphone, dictation, voice
ms.openlocfilehash: ef8114a1c877fe9b858122e0c64628d4b71a69cd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604815"
---
# <a name="voice-input-in-unity"></a>Spracheingabe in Unity

Unity stellt drei Möglichkeiten zum Hinzufügen von [Voice-Eingabe](voice-input.md) für Ihre Unity-Anwendung.

Mit der KeywordRecognizer (eine von zwei Arten von PhraseRecognizers) kann Ihre app ein Array von String-Befehlen zum Lauschen auf angegeben werden. Mit der GrammarRecognizer (die andere Art von PhraseRecognizer) kann Ihre app eine SRGS-Datei definieren eine bestimmte Grammatik zum Lauschen auf angegeben werden. Mit der DictationRecognizer Ihre app für alle Wörter zu Lauschen und bieten dem Benutzer eine Notiz oder anderen enthalten ihre Spracheingabe.

>[!NOTE]
>Nur Diktat oder Spracheingaben kann auf einmal verarbeitet werden. Das bedeutet, wenn eine GrammarRecognizer oder KeywordRecognizer aktiv ist, eine DictationRecognizer nicht aktiv sein und umgekehrt.

## <a name="enabling-the-capability-for-voice"></a>Aktivieren die Funktion für Sprachfunktionen

Die **Mikrofon** Funktion muss deklariert werden, damit eine app Spracheingabe nutzen.
1. Rufen Sie im Unity-Editor die playereinstellungen durch Navigieren zu "Bearbeiten > Projekt Einstellungen > Player"
2. Klicken Sie auf der Registerkarte "Windows Store"
3. Überprüfen Sie im Abschnitt "Einstellungen > Veröffentlichungsfunktionen" die **Mikrofon** Funktion

## <a name="phrase-recognition"></a>Spracheingaben

Klicken Sie in Ihrer Anwendung zum Lauschen auf spezifische gesprochenen Sätzen durch den Benutzer dann eine bestimmte Aktion, müssen Sie:
1. Geben Sie die Ausdrücke für die Verwendung einer KeywordRecognizer oder GrammarRecognizer Lauschen
2. Behandeln des Ereignisses OnPhraseRecognized und Maßnahmen für den Ausdruck erkannt

### <a name="keywordrecognizer"></a>KeywordRecognizer

**Namespace:** *UnityEngine.Windows.Speech*<br>
**Typen:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

Wir benötigen einige wenige using-Anweisungen, die einige Tastenanschläge sparen:

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

Anschließend fügen Sie einige Felder der Klasse zum Speichern der Erkennung und das Schlüsselwort-aktionsdatenwörterbuch > hinzu:

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

Fügen Sie jetzt ein Schlüsselwort, die dem Wörterbuch (z. B. innerhalb einer Start()-Methode) hinzu. Fügen wir das Schlüsselwort "aktivieren" in diesem Beispiel hinzu:

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

Erstellen Sie die Schlüsselwort-Erkennung, und weisen Sie es mit, was wir erkennen möchten:

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

Registrieren Sie sich nun für das Ereignis OnPhraseRecognized

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

Ein Beispiel-Handler ist:

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

Beginnen Sie mit dem erkennen.

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>GrammarRecognizer

**Namespace:** *UnityEngine.Windows.Speech*<br>
**Typen**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

Die GrammarRecognizer wird verwendet, wenn es sich bei Angabe Ihrer Erkennung-Grammatik, die SRGS verwenden. Dies kann nützlich sein, wenn Ihre Anwendung mehr als nur ein paar Schlüsselwörter, verfügt, sollten Sie eine komplexere Ausdrücke zu erkennen, oder wenn Sie ganz einfach aktivieren bzw. deaktivieren Sie Befehle möchten. Thema [Erstellen von Grammatiken mit SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) für Informationen zum Dateiformat.

Nachdem Sie Ihre SRGS-Grammatik haben, und es in Ihrem Projekt in einem [StreamingAssets Ordner](http://docs.unity3d.com/Manual/StreamingAssets.html):

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

Erstellen Sie eine GrammarRecognizer, und übergeben sie den Pfad zu Ihrer SRGS-Datei:

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

Registrieren Sie sich nun für das Ereignis OnPhraseRecognized

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

Sie erhalten einen Rückruf an, die in Ihrer SRGS-Grammatik, die Sie angemessen behandeln können angegebenen Informationen enthält. Die meisten der wichtigen Informationen werden in das Array SemanticMeanings angegeben werden.

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

Beginnen Sie mit dem erkennen.

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>Diktieren

**Namespace:** *UnityEngine.Windows.Speech*<br>
**Typen**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*

Verwenden Sie die DictationRecognizer des Benutzers Sprache in Text konvertiert. Macht die DictationRecognizer [Diktat](voice-input.md#dictation) Funktionalität und unterstützt die Registrierung und zum Lauschen Hypothese und jeden Ausdruck abgeschlossen Ereignisse, sodass Sie Feedback für den Benutzer zuweisen können, während sie sprechen und später. Methoden Start() und Stop() ist bzw. aktivieren und deaktivieren die Erkennung Spracheingaben. Sobald die Erkennung abgeschlossen wird, sollten sie Dispose()-Methode verwenden, um die Ressourcen freizugeben, die sie verwendet freigegeben werden. Sie werden diese Ressourcen freigeben automatisch während der Garbagecollection auf einer zusätzlichen Leistungseinbußen, wenn sie nicht vor, die veröffentlicht werden.

Es gibt nur wenige Schritte erforderlich, um den ersten Schritten mit Diktat:
1. Erstellen Sie eine neue DictationRecognizer
2. Behandeln von Ereignissen für Diktat
3. Starten Sie den DictationRecognizer

### <a name="enabling-the-capability-for-dictation"></a>Aktivieren die Funktion für Diktat

Die Funktion "Internet-Client", zusätzlich zu den oben genannten "Mikrofon"-Funktion muss für eine app Diktat nutzen deklariert werden.
1. Rufen Sie im Unity-Editor die playereinstellungen durch Navigieren zu "Bearbeiten > Projekt Einstellungen > Player"-Seite
2. Klicken Sie auf der Registerkarte "Windows Store"
3. Überprüfen Sie im Abschnitt "Einstellungen > Veröffentlichungsfunktionen" die **InternetClient** Funktion

### <a name="dictationrecognizer"></a>DictationRecognizer

Erstellen Sie eine DictationRecognizer wie folgt:

```
dictationRecognizer = new DictationRecognizer();
```

Es gibt vier Diktat-Ereignisse, die abonniert und behandelt, um Spracheingaben Verhalten implementiert werden können.
1. DictationResult
2. DictationComplete
3. DictationHypothesis
4. DictationError

**DictationResult**

Dieses Ereignis wird ausgelöst, nachdem der Benutzer angehalten wird, in der Regel am Ende eines Satzes. Die vollständige erkannt, dass hier Zeichenfolge zurückgegeben wird.

Abonnieren Sie zunächst das DictationResult-Ereignis:

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

Klicken Sie dann behandeln des Rückrufs DictationResult:

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**DictationHypothesis**

Dieses Ereignis wird ausgelöst, fortlaufend auf, während der Benutzer gerade spricht. Wie die Erkennung wird lauscht, bietet es Text, dessen, was bisher gehört.

Abonnieren Sie zunächst das DictationHypothesis-Ereignis:

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

Klicken Sie dann behandeln des Rückrufs DictationHypothesis:

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**DictationComplete**

Dieses Ereignis wird ausgelöst, wenn die Erkennung anhält, wird, ob von Stop() aufgerufen wird, ein Timeout auftritt oder ein anderer Fehler.

Abonnieren Sie zunächst das DictationComplete-Ereignis:

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

Klicken Sie dann behandeln des Rückrufs DictationComplete:

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**DictationError**

Dieses Ereignis wird ausgelöst, wenn ein Fehler auftritt.

Abonnieren Sie zunächst das DictationError-Ereignis:

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

Klicken Sie dann behandeln des Rückrufs DictationError:

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

Sobald Sie abonniert und behandelt die Diktat-Ereignisse, denen Sie interessieren, starten Sie die Erkennung Diktat zum Empfangen von Ereignissen zu beginnen.

```
dictationRecognizer.Start();
```

Wenn Sie nicht mehr die DictationRecognizer um beibehalten möchten, müssen Sie die Ereignisse zu kündigen und die DictationRecognizer zu verwerfen.

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**Tipps**
* Methoden Start() und Stop() ist bzw. aktivieren und deaktivieren die Erkennung Spracheingaben.
* Sobald die Erkennung abgeschlossen wird, muss er Dispose()-Methode verwenden, um die Ressourcen freizugeben, die sie verwendet freigegeben werden. Sie werden diese Ressourcen freigeben automatisch während der Garbagecollection auf einer zusätzlichen Leistungseinbußen, wenn sie nicht vor, die veröffentlicht werden.
* Timeouts treten auf, nach einem festgelegten Zeitraum. Sie können diese Timeouts im Ereignis DictationComplete überprüfen. Es gibt zwei Timeouts zu beachten:
   1. Wenn die Erkennung gestartet wird und keine Audiodaten für die ersten fünf Sekunden zu hören, tritt ein Timeout ein.
   2. Wenn die Erkennung erhält ein Ergebnis, aber dann Ruheintervall 20 Sekunden lang hört, tritt ein Timeout ein.

## <a name="using-both-phrase-recognition-and-dictation"></a>Mithilfe von Spracheingaben und Diktat

Wenn Sie sowohl Spracheingaben und Diktat in Ihrer app verwenden möchten, müssen Sie vollständig eine heruntergefahren, bevor Sie die andere starten können. Wenn Sie mehrere KeywordRecognizers ausgeführt wird, können Sie diese gleichzeitig mit Beenden alle:

```
PhraseRecognitionSystem.Shutdown();
```

Um alle Erkennungen in ihren vorherigen Zustand, wiederherzustellen, nachdem die DictationRecognizer beendet wurde, können Sie Folgendes aufrufen:

```
PhraseRecognitionSystem.Restart();
```

Eine KeywordRecognizer, die die PhraseRecognitionSystem ebenfalls neu gestartet wird, konnte auch einfach gestartet werden.

## <a name="using-the-microphone-helper"></a>Unter Verwendung des Hilfsprogramms Mikrofon

Die Mixed Reality-Toolkit auf GitHub enthält eine Hilfsklasse Mikrofon, um Hinweise für Entwickler ist es ein verwendbaren Mikrofon auf dem System. Eine Verwendungsmöglichkeit dafür ist, in denen eine überprüfen, ob Mikrofon System vor dem Anzeigen des Interaktion Hinweise in der Anwendung für jede Sprache möchten.

Das Mikrofon Hilfsskript finden Sie in der [Eingabe-/Skripts/-Dienstprogramme Ordner](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs). Das GitHub-Repository enthält außerdem eine [kleine](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) veranschaulicht, wie das Hilfsprogramm.

## <a name="voice-input-in-mixed-reality-toolkit"></a>Spracheingabe in Mixed Reality-Toolkit
Die Beispiele für die Spracheingabe finden Sie in dieser.

- [HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
