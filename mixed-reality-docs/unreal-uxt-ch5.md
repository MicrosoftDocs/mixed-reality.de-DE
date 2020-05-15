---
title: 5. Hinzufügen einer Taste und Zurücksetzen von Figurenpositionen
description: Teil 5 eines Tutorials zum Erstellen einer einfachen Schach-App mit Unreal Engine 4 und dem UX-Tools-Plug-In des Mixed Reality-Toolkits
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Tutorial, erste Schritte, MRTK, UXT, UX Tools, Dokumentation
ms.openlocfilehash: df5ea22e7097fdd3b788ec298bc1cd78c315b585
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840399"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a>5. Hinzufügen einer Taste und Zurücksetzen von Figurenpositionen

In diesem Abschnitt werden weiter die Funktionen des UX-Tools-Plug-Ins des Mixed Reality-Toolkits veranschaulicht und die Features Ihrer Schach-App erweitert. Dazu wird eine neue Funktion erstellt, und Sie erfahren, wie Sie Verweise auf Akteure aus Ihrem Level in eine Blaupause integrieren.

## <a name="objectives"></a>Ziele

* Hinzufügen eines Schalters zu Ihrem Projekt
* Erstellen der neuen Funktion „Reset Location“ (Position zurücksetzen), um eine Figur wieder auf ihre ursprüngliche Position zurückzusetzen
* Einbinden des Schalters, damit beim Drücken des Schalters die neu erstellte Funktion ausgelöst wird

## <a name="create-a-function-to-reset-location"></a>Erstellen einer Funktion zum Zurücksetzen der Position

1.  Öffnen Sie **WhiteKing**. Klicken Sie im Bereich **My Blueprint** (Meine Blaupause) neben dem Abschnitt **Functions** (Funktionen) auf die Plusschaltfläche (+), um eine neue Funktion zu erstellen. Nennen Sie diese Funktion „Reset Location“ (Position zurücksetzen). 

2.  Ziehen Sie in der neu erstellten Blaupause **Reset Location** (Position zurücksetzen) den Ausführungspin an eine beliebige Stelle des Blaupausenrasters, und lassen Sie ihn los, um einen Knoten vom Typ **SetActorRelativeTransform** aufzurufen. Durch diese Funktion wird die Transformation (Position, Rotation und Skalierung) eines Akteurs relativ zum übergeordneten Element festgelegt. Hier wird diese Funktion verwendet, um die Position des Königs auf dem Schachbrett zurückzusetzen, auch wenn sich dieses nicht mehr an seiner ursprünglichen Position befindet. Erstellen Sie einen Knoten vom Typ **Make Transform** (Transformation erstellen) mit der Position „X = -26“, „Y = 4“ und „Z = 0“, und verbinden Sie ihn mit der Eingabe „New Relative Transform“ (Neue relative Transformation). 

![Funktion zum Zurücksetzen der Position](images/unreal-uxt/5-function.PNG)

3.  Kompilieren und speichern Sie **WhiteKing**. Kehren Sie zum Hauptfenster zurück. 

## <a name="add-a-button"></a>Hinzufügen eines Schalters

1.  Erstellen Sie im Ordner **Blueprints** eine neue Blaupause als Unterklasse von „SimpleButton“. „SimpleButton“ ist ein Blaupausenakteur in Form eines 3D-Schalters, der im Rahmen des UX-Tools-Plug-Ins bereitgestellt wird. Nennen Sie diesen Schalter „ResetButton“, und doppelklicken Sie darauf, um die Blaupause zu öffnen. 

![Verwenden der neuen Blaupause als Unterklasse von „SimpleButton“](images/unreal-uxt/5-subclass.PNG)

2.  Klicken Sie im Bereich **Components** (Komponenten) auf **PressableButton (Inherited)** (PressableButton (geerbt)). Scrollen Sie im Detailbereich zum Abschnitt **Events** (Ereignisse). Klicken Sie neben **On Button Pressed** (Beim Drücken des Schalters) auf die grüne Plusschaltfläche. Dadurch wird dem Ereignisdiagramm ein Ereignis vom Typ **On Button Pressed** (Beim Drücken des Schalters) hinzugefügt, das beim Drücken des Schalters aufgerufen wird. Hier möchten wir die Funktion „Reset Location“ (Position zurücksetzen) für den weißen König (WhiteKing) aufrufen. Dazu wird zunächst ein Verweis auf den Akteur „WhiteKing“ im Level benötigt. 

3.  Navigieren Sie im Bereich **My Blueprint** (Meine Blaupause) zum Abschnitt **Variables** (Variablen), und klicken Sie auf die Schaltfläche **+** , um eine neue Variable hinzuzufügen. Nennen Sie diese Variable „WhiteKing“. Wählen Sie im Detailbereich die Dropdownliste neben **Variable Type** (Variablentyp) aus, suchen Sie nach „WhiteKing“, und wählen Sie den Objektverweis (**Object Reference**) aus. Aktivieren Sie abschließend das Kontrollkästchen neben **Instance Editable** (Bearbeitbare Instanz). Dadurch kann die Variable von der Hauptebene aus festgelegt werden. 

![Erstellen einer Variablen](images/unreal-uxt/5-var.PNG)

4.  Ziehen Sie die Variable „WhiteKing“ aus **My Blueprint > Variables** („Meine Blaupause“ > „Variablen“) auf das Ereignisdiagramm für die einfache Taste. Wählen Sie **Get WhiteKing** („WhiteKing“ abrufen) aus. 

5.  Ziehen Sie den Ausgabepin von „WhiteKing“, und lassen Sie ihn los, um einen neuen Knoten zu platzieren. Wählen Sie die Funktion **Reset Location** (Position zurücksetzen) aus. Ziehen Sie abschließend den ausgehenden Ausführungspin von **On Button Pressed** (Beim Drücken des Schalters) zum eingehenden Ausführungspin von **Reset Location** (Position zurücksetzen). **Kompilieren** und **speichern** Sie die Blaupause „ResetButton“, und kehren Sie anschließend zum Hauptfenster zurück. 

![Aufrufen der Funktion zum Zurücksetzen der Position über „On Button Pressed“ (Beim Drücken des Schalters)](images/unreal-uxt/5-callresetloc.PNG)

6.  Ziehen Sie **SimpleButton** in den Viewport, und legen Sie die Position auf „X = 50“, „Y = -25“ und „Z = 10“ fest. Legen Sie unter **Default** (Standard) den Wert der Variablen „WhiteKing“ auf **WhiteKing** fest.

![Festlegen der Variablen](images/unreal-uxt/5-buttonlevel.PNG)

Sie verfügen nun über eine Mixed Reality-App mit einer greifbaren Schachfigur und einem greifbaren Schachbrett sowie mit einem funktionsfähigen Schalter, der gedrückt werden kann, um die Position der Schachfigur zurückzusetzen. Die bis hierhin fertige App steht auf [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) zur Verfügung. Sie können gerne noch einen Schritt weitergehen und die restlichen Schachfiguren einrichten, sodass das gesamte Schachbrett zurückgesetzt wird, wenn der Benutzer auf die Taste drückt.

![Fertige Szene im Viewport](images/unreal-uxt/5-endscene.PNG)

[Nächster Abschnitt: 6. Verpacken und Bereitstellen auf einem Gerät oder Emulator](unreal-uxt-ch6.md)