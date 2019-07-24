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
# <a name="voice-input-in-unity"></a>Spracheingabe in Unity

Unity bietet drei Möglichkeiten zum Hinzufügen von [Spracheingaben](voice-input.md) zu ihrer Unity-Anwendung.

Mit keywordrecognizer (einem von zwei Typen von phraserecognizers) kann Ihrer APP ein Array von Zeichen folgen Befehlen zugewiesen werden, die überwacht werden sollen. Mit dem Grammatiken von Grammatiken (dem anderen Typ von phraserecognizer) kann Ihrer APP eine SRGS-Datei zugewiesen werden, die eine bestimmte Grammatik zum lauschen definiert. Mit dem "diktationerkenzer" kann Ihre APP auf ein beliebiges Wort lauschen und dem Benutzer einen Hinweis oder eine andere Anzeige seiner Sprache bereitstellen.

>[!NOTE]
>Nur die Diktat-oder Ausdrucks Erkennung kann gleichzeitig behandelt werden. Dies bedeutet, dass ein "yntationerkenzer" nicht aktiv sein kann und umgekehrt ist, wenn ein "grammmarerkenzer" oder "keywordrecognizer" aktiv ist.

## <a name="enabling-the-capability-for-voice"></a>Aktivieren der Sprachfunktion

Die **Mikrofon** Funktion muss für eine APP deklariert werden, um die Spracheingabe zu nutzen.
1. Navigieren Sie im Unity-Editor zu den Player Einstellungen, indem Sie zu "> Projekteinstellungen bearbeiten > Player" navigieren.
2. Klicken Sie auf die Registerkarte "Windows Store".
3. Aktivieren Sie im Abschnitt "Veröffentlichungs Einstellungen > Funktionen" die **Mikrofon** Funktion.

## <a name="phrase-recognition"></a>Ausdrucks Erkennung

Damit Ihre APP auf bestimmte vom Benutzer gesprochene Ausdrücke lauschen kann, müssen Sie Folgendes tun:
1. Angeben der zu überwachenden Ausdrücke mithilfe eines keywordrecognizer-oder grammarerkenzer-Elements
2. Behandeln Sie das onphraserecognized-Ereignis, und ergreifen Sie entsprechende Aktionen für den erkannten Ausdruck.

### <a name="keywordrecognizer"></a>Keywordrecognizer

**Namespace:** *Unityengine. Windows. Speech*<br>
**Solche** *Keywordrecognizer*, *phraserecognizedeventargs*, *Sprachfehler*, *Sprachsystem Status*

Zum Speichern einiger Tastatureingaben benötigen wir einige using-Anweisungen:

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

Fügen Sie der Klasse nun einige Felder hinzu, um das Erkennungs-und Schlüsselwort > Aktions Wörterbuch zu speichern:

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

Fügen Sie nun dem Wörterbuch ein Schlüsselwort hinzu (z. b. innerhalb einer Start ()-Methode). Das Schlüsselwort "aktivieren" wird in diesem Beispiel hinzugefügt:

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

Erstellen Sie die Schlüsselwort Erkennung, und teilen Sie Ihnen mit, was wir erkennen möchten:

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

Registrieren Sie sich jetzt für das onphraserecognized-Ereignis.

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

Ein Beispiel Handler ist:

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

Beginnen Sie schließlich mit der Erkennung!

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>Grammarerkenzer

**Namespace:** *Unityengine. Windows. Speech*<br>
**Typen**: *Grammarerkenzer*, *phraserecognizedeventargs*, *Sprachfehler*, *Sprachsystem Status*

Die Grammatiken werden verwendet, wenn Sie Ihre Erkennungs Grammatik mithilfe von SRGS angeben. Dies kann hilfreich sein, wenn Ihre APP mehr als nur einige wenige Schlüsselwörter aufweist, wenn Sie komplexere Ausdrücke erkennen möchten, oder wenn Sie Sätze von Befehlen problemlos aktivieren und deaktivieren möchten. Thema [Erstellen Sie Grammatiken mithilfe von SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) für Dateiformat Informationen.

Sobald Sie die SRGS-Grammatik haben und sich in Ihrem Projekt in einem [Ordner "streamingassets](http://docs.unity3d.com/Manual/StreamingAssets.html)" befinden:

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

Erstellen Sie eine grammatisierungsklasse, und übergeben Sie Ihr den Pfad zu ihrer SRGS-Datei:

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

Registrieren Sie sich jetzt für das onphraserecognized-Ereignis.

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

Sie erhalten einen Rückruf mit Informationen, die in der SRGS-Grammatik angegeben sind, die Sie entsprechend behandeln können. Die meisten wichtigen Informationen werden im semanticbedeutungen-Array bereitgestellt.

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

Beginnen Sie schließlich mit der Erkennung!

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>Diktieren

**Namespace:** *Unityengine. Windows. Speech*<br>
**Typen**: " *Diktationerkenzer*", "sprecherfehler", " *Redner Systemstatus*

Verwenden Sie das diktationerkenzer-Element, um die Sprache des Benutzers in Text zu konvertieren. Der Diktat-Erkennungs Modul macht [Diktat](voice-input.md#dictation) Funktionen verfügbar und unterstützt das registrieren und lauschen auf Hypothese und Ausdrucks fertige Ereignisse, sodass Sie Ihrem Benutzer Feedback geben können, während Sie sprechen und danach. Die Methoden "Start ()" und "stoppt ()" aktivieren und deaktivieren die Diktat Erkennung. Sobald die Erkennung erfolgt ist, sollte Sie mithilfe der verwerfen ()-Methode freigegeben werden, um die verwendeten Ressourcen freizugeben. Diese Ressourcen werden während Garbage Collection automatisch freigegeben, wenn Sie noch nicht freigegeben werden.

Für den Einstieg in das Diktat müssen nur wenige Schritte ausgeführt werden:
1. Erstellen eines neuen "diktationerkenzer"
2. Behandeln von Diktat Ereignissen
3. "Diktationerkenzer" starten

### <a name="enabling-the-capability-for-dictation"></a>Aktivieren der Funktion für das Diktat

Die Funktion "Internet Client" muss zusätzlich zu der oben erwähnten Funktion "Mikrofon" deklariert werden, damit eine Anwendung die Diktat Funktion nutzt.
1. Navigieren Sie im Unity-Editor zu den Player Einstellungen, indem Sie zur Seite "> Projekteinstellungen bearbeiten > Player" navigieren.
2. Klicken Sie auf die Registerkarte "Windows Store".
3. Überprüfen Sie im Abschnitt "Veröffentlichungs Einstellungen > Funktionen" die Funktion " **Internetclient** ".

### <a name="dictationrecognizer"></a>Diktationerkenzer

Erstellen Sie einen "diktationerkenzer" wie folgt:

```
dictationRecognizer = new DictationRecognizer();
```

Es gibt vier Diktat Ereignisse, die abonniert und behandelt werden können, um das Diktat Verhalten zu implementieren.
1. "Ditationresult"
2. "Ditationcomplete"
3. "Ditationhypothese"
4. "Ditationerror"

**"Ditationresult"**

Dieses Ereignis wird ausgelöst, nachdem der Benutzer angehalten wurde, in der Regel am Ende eines Satzes. Hier wird die vollständig erkannte Zeichenfolge zurückgegeben.

Abonnieren Sie zunächst das Ereignis "" für das ""-Ereignis:

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

Behandeln Sie dann den "-Rückruf":

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**"Ditationhypothese"**

Dieses Ereignis wird fortlaufend ausgelöst, während der Benutzer spricht. Wie die Erkennung hört, bietet Sie Text zu den bisher gehörenden.

Abonnieren Sie zunächst das Ereignis "ditationhypothese":

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

Behandeln Sie dann den-Rückruf von "ditationhypothese":

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**"Ditationcomplete"**

Dieses Ereignis wird ausgelöst, wenn die Erkennung angehalten wird, und zwar unabhängig davon, ob von "Stopp ()" aufgerufen wird, ein Timeout auftritt oder ein anderer Fehler vorliegt.

Abonnieren Sie zunächst das Ereignis "" für das Ereignis "".

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

Behandeln Sie dann den-Rückruf von "ditationcomplete":

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**"Ditationerror"**

Dieses Ereignis wird ausgelöst, wenn ein Fehler auftritt.

Abonnieren Sie zunächst das Ereignis "" für "" "".

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

Behandeln Sie dann den "-Rückruf"-Rückruf:

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

Nachdem Sie die Diktat Ereignisse abonniert und behandelt haben, die Ihnen wichtig sind, starten Sie die Diktat Erkennung, um mit dem empfangen von Ereignissen zu beginnen.

```
dictationRecognizer.Start();
```

Wenn Sie die "diktationerkenzer" nicht mehr benötigen, müssen Sie die Ereignisse kündigen und den "diktationerkenzer" verwerfen.

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**Chti**
* Die Methoden "Start ()" und "stoppt ()" aktivieren und deaktivieren die Diktat Erkennung.
* Sobald die Erkennung erfolgt ist, muss Sie mithilfe der Methode "verwerfen ()" freigegeben werden, um die verwendeten Ressourcen freizugeben. Diese Ressourcen werden während Garbage Collection automatisch freigegeben, wenn Sie noch nicht freigegeben werden.
* Timeouts treten nach einer festgelegten Zeitspanne auf. Sie können diese Timeouts im Ereignis "ditationcomplete" überprüfen. Es gibt zwei Timeouts, die Sie beachten sollten:
   1. Wenn die Erkennung startet und keine Audiodaten für die ersten fünf Sekunden hört, wird ein Timeout angezeigt.
   2. Wenn die Erkennung ein Ergebnis erhalten hat, dann aber für einen Zeitraum von 20 Sekunden den Ruhe Wert erfährt, wird ein Timeout verursacht.

## <a name="using-both-phrase-recognition-and-dictation"></a>Verwenden der Ausdrucks Erkennung und-diktierung

Wenn Sie in Ihrer APP sowohl die Erkennung als auch das Diktat von Ausdrücken verwenden möchten, müssen Sie eine vollständige Herunterfahren, bevor Sie die andere starten können. Wenn mehrere keywordrecognizers ausgeführt werden, können Sie Sie mit folgenden Aktionen gleichzeitig Herunterfahren:

```
PhraseRecognitionSystem.Shutdown();
```

Wenn Sie alle erkenners in Ihrem vorherigen Zustand wiederherstellen möchten, können Sie nach dem Beenden von "diktationerkenzer" Folgendes aufzurufen:

```
PhraseRecognitionSystem.Restart();
```

Sie können auch einfach einen keywordrecognizer starten, mit dem auch das phraserecognitionsystem neu gestartet wird.

## <a name="using-the-microphone-helper"></a>Verwenden des Mikrofon-Hilfsprogramms

Das Mixed Reality Toolkit auf GitHub enthält eine Mikrofon-Hilfsklasse, mit der Entwickler darauf hinweisen können, ob im System ein brauchbares Mikrofon vorhanden ist. Eine Verwendung hierfür ist der Ort, an dem überprüft werden soll, ob ein Mikrofon im System vorhanden ist, bevor sprach Interaktions Hinweise in der Anwendung angezeigt werden.

Das Mikrofon-Hilfsobjekt befindet sich im [Ordner Input/Scripts/Utilities](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs). Das GitHub-Repository enthält auch ein [kleines Beispiel](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) , das zeigt, wie das Hilfsprogramm verwendet werden kann.

## <a name="voice-input-in-mixed-reality-toolkit"></a>Spracheingabe im Mixed Reality Toolkit
Die Beispiele für die Spracheingabe finden Sie in dieser Szene.

- [HoloToolkit-examples/Input/Szenen/speechinputsource. unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)
