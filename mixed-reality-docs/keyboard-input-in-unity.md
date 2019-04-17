---
title: Tastatureingaben in Unity
description: Unity bietet die Klasse TouchScreenKeyboard Tastatureingaben akzeptieren, wenn keine physische Tastatur verfügbar ist.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Tastatur, Eingabe, Unity, touchscreenkeyboard
ms.openlocfilehash: 35f6f0df993931eea35db7b167110b341ea0c0f2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604885"
---
# <a name="keyboard-input-in-unity"></a>Tastatureingaben in Unity

**Namespace:** *UnityEngine*<br>
 **Typ**: *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

HoloLens viele Formen der Eingabe, einschließlich Bluetooth-Tastaturen unterstützt, wird die meisten Anwendungen können nicht davon ausgegangen, dass alle Benutzer eine physische Tastatur, die zur Verfügung hat. Wenn Ihre Anwendung die Texteingabe erforderlich ist, muss eine Form der Bildschirmtastatur bereitgestellt werden.

Unity bietet die *[TouchScreenKeyboard](http://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* -Klasse für Tastatureingaben akzeptiert, wenn keine physische Tastatur verfügbar ist.

## <a name="hololens-system-keyboard-behavior-in-unity"></a>HoloLens-System-Tastaturverhalten in Unity

Für HoloLens die *TouchScreenKeyboard* nutzt die Bildschirmtastatur des Systems. Die Bildschirmtastatur des Systems kann nicht auf eine volumetrische Ansicht zu überlagern, weshalb Unity erstellen eine sekundäre 2D XAML-Ansicht zum Anzeigen der Tastatur, und klicken Sie dann an die volumetrische Sicht zurückgegeben wird, nach der Eingabe übermittelt wurde. Der benutzerflow läuft folgendermaßen ab:
1. Der Benutzer führt eine Aktion, die app-Code aufrufen, wodurch *TouchScreenKeyboard*
    * Die app ist verantwortlich für das Anhalten des app-Status vor dem Aufruf *TouchScreenKeyboard*
    * Die app möglicherweise beenden, bevor Sie jemals wieder an die volumetrische Ansicht wechseln
2. Unity wechselt zu einer XAML-2D-Ansicht automatisch platzierte in der der ganzen Welt
3. Der Benutzer Text mithilfe der Systemtastatur eingegeben und übermittelt oder abgebrochen
4. Unity, wechselt zurück in die volumetrische Ansicht
    * Die app ist verantwortlich für das Fortsetzen der app Zustand über, wenn die *TouchScreenKeyboard* erfolgt
5. Gesendeten Text finden Sie in der *TouchScreenKeyboard*

### <a name="available-keyboard-views"></a>Verfügbare Tastatur-Ansichten

Es gibt sechs verschiedene Tastatur Ansichten verfügbar:
* Einzeiliges Textfeld
* Einzeiliges Textfeld mit dem Titel
* Mehrzeiligen Textfeld
* Mehrzeiligen Textfeld mit dem Titel
* Einzeilige Kennwortfeld
* Einzeilige Kennwortfeld mit Titel

## <a name="how-to-enable-the-system-keyboard-in-unity"></a>Vorgehensweise: aktivieren die Systemtastatur in Unity

Die HoloLens-Systemtastatur ist nur verfügbar, um Unity-Anwendungen, die mit der"UWP erstellen", "XAML" exportiert werden. Es gibt Kompromisse, die zu machen, bei der Auswahl von "XAML" als"UWP erstellen" über "D3D". Wenn Sie nicht mit der diese Nachteile vertraut sind, möglicherweise möchten Sie untersuchen eine [Alternative Eingabe Lösung](#alternative-keyboard-options) auf der Systemtastatur.
1. Öffnen der **Datei** Menü **Buildeinstellungen...**
2. Stellen Sie sicher die **Plattform** nastaven NA hodnotu **Windows Store**, **SDK** nastaven NA hodnotu **universelle 10**, und legen Sie die **UWP Build Type**  zu **XAML**.
3. In der **Buildeinstellungen** Dialogfeld klicken Sie auf die **Playereinstellungen...**  Schaltfläche
4. Wählen Sie die **Einstellungen für Windows Store** Registerkarte
5. Erweitern Sie die **Weitere Einstellungen** Gruppe
6. In der **Rendern** aktivieren Sie im Abschnitt der **virtuelle Realität unterstützt** Kontrollkästchen zum Hinzufügen einer neuen **Virtual Reality-Geräte** Liste
7. Stellen Sie sicher **Windows Holographic** wird in der Liste von Virtual Reality-SDKs

>[!NOTE]
>Wenn Sie als virtuelle Realität unterstützt den Build kennzeichnen, mit dem HoloLens-Gerät nicht, wird das Projekt als einer 2D-Texturmap. XAML-app exportieren.

## <a name="using-the-system-keyboard-in-your-unity-app"></a>Verwenden die Systemtastatur in Ihrer Unity-app

### <a name="declare-the-keyboard"></a>Deklarieren Sie die Tastatur

Deklarieren Sie in der Klasse eine Variable zum Speichern der *TouchScreenKeyboard* und gibt eine Variable für die Zeichenfolge der Tastatur.

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>Rufen Sie die Tastatur

Tritt ein Ereignis anfordernden Tastatureingaben, rufen Sie eine dieser Funktionen, die je nach Art der gewünschten Eingabe. Beachten Sie, dass der Titel im TextPlaceholder-Parameter angegeben wird.

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

### <a name="retrieve-typed-contents"></a>Rufen Sie typisierte Inhalte

Überprüfen Sie in der Update-Schleife, ob die Tastatur neue Eingabe empfangen, und für die Verwendung an einem anderen Ort zu speichern.

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

## <a name="alternative-keyboard-options"></a>Alternative Tastaturoptionen

Uns ist bewusst, dass aus einer volumetrische Ansicht in einer 2D-wechseln die ideale Möglichkeit zum Abrufen der Texteingabe des Benutzers nicht.

Die aktuelle Alternativen zu den-Systemtastatur über Unity nutzen gehören:
* Mithilfe von Spracherkennung Diktat für die Eingabe (<b>Hinweis:</b> Dies ist häufig fehleranfällig für Wörter, die nicht im Wörterbuch gefunden wurde, und eignet sich nicht zur Eingabe des Kennworts)
* Erstellen Sie eine Tastatur, die funktioniert in Ihrer Anwendungen exklusive-Ansicht
