---
title: Tastatureingabe in Unity
description: Unity stellt die touchscreenkeyboard-Klasse bereit, um Tastatureingaben zu akzeptieren, wenn keine physische Tastatur verfügbar ist.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Tastatur, Eingabe, Unity, touchscreenkeyboard
ms.openlocfilehash: 35f6f0df993931eea35db7b167110b341ea0c0f2
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515740"
---
# <a name="keyboard-input-in-unity"></a>Tastatureingabe in Unity

**Namespace:** *UnityEngine*<br>
 **Typ**: *[Touchscreenkeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

Obwohl hololens viele Formen von Eingaben einschließlich Bluetooth-Tastaturen unterstützt, können die meisten Anwendungen nicht davon ausgehen, dass für alle Benutzer eine physische Tastatur verfügbar ist. Wenn für Ihre Anwendung Texteingaben erforderlich sind, sollte eine Form von auf Bildschirmtastatur angegeben werden.

Unity stellt die *[touchscreenkeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* -Klasse bereit, um Tastatureingaben zu akzeptieren, wenn keine physische Tastatur verfügbar ist.

## <a name="hololens-system-keyboard-behavior-in-unity"></a>Hololens System Tastatur Verhalten in Unity

Auf hololens nutzt *touchscreenkeyboard* die Bildschirmtastatur des Systems. Die Tastatur des Systems auf dem Bildschirm kann nicht oberhalb einer Volumetrische-Ansicht überlagert werden, sodass Unity eine sekundäre 2D-XAML-Ansicht erstellen muss, um die Tastatur anzuzeigen, und dann zurück an die volumetriansicht zurückgegeben wird, sobald die Eingabe übermittelt wurde. Der Benutzer Ablauf sieht wie folgt aus:
1. Der Benutzer führt eine Aktion aus, die bewirkt, dass APP-Code *touchscreenkeyboard* aufruft.
    * Die APP ist für das Anhalten des App-Zustands vor dem Aufrufen von *touchscreenkeyboard* verantwortlich.
    * Die APP kann beendet werden, bevor Sie zur Volumetrische-Ansicht zurück wechselt.
2. Unity wechselt zu einer 2D-XAML-Ansicht, die automatisch in der Welt platziert wird
3. Der Benutzer gibt mithilfe der System Tastatur Text ein und übermittelt oder bricht ihn ab.
4. Unity wechselt zurück zur volumetriansicht
    * Die APP ist für das Fortsetzen des App-Zustands verantwortlich, wenn *touchscreenkeyboard* abgeschlossen ist.
5. Der übermittelte Text ist in *touchscreenkeyboard* verfügbar.

### <a name="available-keyboard-views"></a>Verfügbare Tastatur Ansichten

Es stehen sechs verschiedene Tastatur Ansichten zur Verfügung:
* Einzeilige Textfeld
* Einzeilige Textfeld mit Titel
* Mehrzeilige Textfeld
* Mehrzeilige Textfeld mit Titel
* Einzeilige Kenn Wort Feld
* Einzeilige Kenn Wort Feld mit Titel

## <a name="how-to-enable-the-system-keyboard-in-unity"></a>Aktivieren der System Tastatur in Unity

Die System Tastatur hololens ist nur für Unity-Anwendungen verfügbar, die mit dem "UWP Build Type" auf "XAML" exportiert werden. Wenn Sie "XAML" als "UWP Build Type" über "D3D" auswählen, müssen Sie die vor-und Nachteile treffen. Wenn Sie mit diesen vor-und Nachteile nicht vertraut sind, möchten Sie möglicherweise eine [Alternative Eingabe Lösung](#alternative-keyboard-options) für die System Tastatur untersuchen.
1. Öffnen Sie das Menü **Datei** , und wählen Sie Buildeinstellungen aus **.**
2. Stellen Sie sicher, dass die **Plattform** auf **Windows Store**festgelegt ist, das **SDK** auf **Universal 10**festgelegt ist, und legen Sie den **UWP** -Buildtyp auf **XAML**fest.
3. Klicken Sie  im Dialogfeld "Buildeinstellungen" auf die Schaltfläche **Player Einstellungen...** .
4. Wählen Sie die Registerkarte **Einstellungen für Windows Store aus** .
5. Erweitern Sie die Gruppe **andere Einstellungen** .
6. Aktivieren Sie im Abschnitt " **Rendering** " das Kontrollkästchen " **Virtual Reality supported** ", um eine neue **Virtual Reality-Geräte** Liste hinzuzufügen.
7. Stellen Sie sicher, dass **Windows Holographic** in der Liste der Virtual Reality sdert angezeigt wird.

>[!NOTE]
>Wenn Sie den Build nicht als virtuelle Realität markieren, die mit dem hololens-Gerät unterstützt wird, exportiert das Projekt als 2D-XAML-app.

## <a name="using-the-system-keyboard-in-your-unity-app"></a>Verwenden der System Tastatur in ihrer Unity-App

### <a name="declare-the-keyboard"></a>Tastatur deklarieren

Deklarieren Sie in der-Klasse eine Variable zum Speichern der *touchscreenkeyboard* und eine Variable, um die von der Tastatur zurückgegebene Zeichenfolge zu speichern.

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>Tastatur aufrufen

Wenn ein Ereignis beim Anfordern von Tastatureingaben auftritt, wird eine dieser Funktionen aufgerufen, abhängig vom Typ der gewünschten Eingabe. Beachten Sie, dass der Titel im textplachalter-Parameter angegeben wird.

```cs
// Single-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);

// Single-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false, "Single-line title");

// Multi-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false);

// Multi-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false, "Multi-line Title");

// Single-line password box
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false);

// Single-line password box with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false, "Secure Single-line Title");
```

### <a name="retrieve-typed-contents"></a>Abrufen von typisiertem Inhalt

Überprüfen Sie in der Update Schleife, ob die Tastatur neue Eingaben empfangen hat, und speichern Sie Sie an anderer Stelle.

```cs
if (TouchScreenKeyboard.visible == false && keyboard != null)
{
       if (keyboard.done == true)
       {
           keyboardText = keyboard.text;
           keyboard = null;
       }
}
```

## <a name="alternative-keyboard-options"></a>Alternative Tastatur Optionen

Wir wissen, dass das Wechseln aus einer Volumetrische-Sicht in eine 2D-Ansicht nicht die ideale Methode ist, um Texteingaben vom Benutzer zu erhalten.

Die aktuellen Alternativen zur Verwendung der System Tastatur über Unity umfassen Folgendes:
* Verwendung der Spracherkennung für die Eingabe (<b>Hinweis:</b> Dies ist oft fehleranfällig für Wörter, die nicht im Wörterbuch gefunden wurden und für die Kenn Wort Eingabe nicht geeignet sind).
* Erstellen einer Tastatur, die in der exklusiven Ansicht Ihrer Anwendungen funktioniert
