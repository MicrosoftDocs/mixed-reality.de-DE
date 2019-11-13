---
title: Spracherkennung und-Aufzeichnung für das Lern-SDK-Modul von Mr
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: da485f167ef3902dd75adf8da8181504fbc6c6df
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913167"
---
# <a name="speech-sdk-learning-module---rocket-launcher-control-using-speech-commands"></a>Sprach-SDK-Lernmodul-Starter Launcher-Steuerelement mithilfe von Sprachbefehlen

In dieser Lektion verwenden wir das Intent-Feature des Azure Speech Service, um die Absicht der Sprache zu verstehen. Wir verwenden die erkannte Absicht der Sprache als Sprachbefehle, um das Raketen Starter Programm zu steuern. In dieser Lektion importieren wir das Raketenstart Programm Asset, und wir verbinden die erkannten Intent Voice-Befehle mit vordefinierten Steuerungs Schaltflächen, um die Raketen zu steuern.

## <a name="objectives"></a>Ziele

- Erfahren Sie, wie Sie Sprech Absicht als Sprachbefehle verbinden.
- Erfahren Sie, wie Sie sprach beabsichtigte Sprachbefehle als Eingabe Befehle für die Befehls Eingabe verwenden.

## <a name="instructions"></a>Anweisungen

1. In diesem Tutorial verwenden wir ein "basemodule"-Asset, um das Raketenstart Programm mit den Sprachbefehlen zu integrieren. Dafür müssen wir das Medienobjekt in unser Projekt importieren. Sie können das Asset "Launcher Launcher" mithilfe dieses [Links](https://github.com/Developer-OI/MixedRealityLearning/releases/download/1.2.1/BaseModuleAssets-1.2.1.unitypackage)herunterladen.

2. Um das Medienobjekt zu importieren, wechseln Sie zu Assets-> Paket > benutzerdefiniertes Paket importieren > Navigieren Sie zu der heruntergeladenen Datei, und klicken Sie auf importieren.

    ![module4chapter5step1](images/module4chapter5step1.PNG)

3. Navigieren Sie nach dem Importieren des Assets "Base Module Assets" im Ordner "Base Module Assets" > Prefabs-> Wählen Sie "Rocket Launcher_Complete" aus, und ziehen Sie ihn dann per Drag & amp; Drop in die vorhandene Szenen Hierarchie.

    ![module4chapter5step2](images/module4chapter5step2.PNG)

4. Nun müssen wir unser "Launcher"-Start Programm in unser Luis-Projekt integrieren, das wir in unserer [vorherigen Lektion gearbeitet haben.](mrlearning-speechSDK-ch4.md) Erweitern Sie dazu in der Hierarchie die vorfab "Launcher Launcher_Complete", und suchen Sie die Schaltflächen "launchroundbutton", "Reort-Taste" und "Platzierungs Hinweise".

    ![module4chapter5step3](images/module4chapter5step3.PNG)

5. Wählen Sie "launchroundbutton" aus, und wechseln Sie im Inspektor-Panel zu "interactable", und legen Sie unter Ereignisse "OnClick ()" die vorfab "lunarmodule" mit Drag und Drop ab. Wählen Sie dann die Dropdown Liste Funktion aus, und wählen Sie "lunarmodule" aus. Navigieren Sie dann zur Funktion "startthruester ()", und wählen Sie Sie aus.

    ![module4chapter5step 3.0](images/module4chapter5step3.0.PNG)

    ![module4chapter5step3a](images/module4chapter5step3a.PNG)

6. Wählen Sie "rebertroundbutton" aus, und wechseln Sie im Inspektor-Panel zu "interactable", und legen Sie unter Ereignisse "OnClick ()" die vorfab "lunarmodule" mit Drag und Drop ab. Wählen Sie dann die Dropdown-Funktion aus, und wählen Sie "lunarmodule" aus. Navigieren Sie dann zur Funktion "resetmodule ()", und wählen Sie Sie aus.

    ![module4chapter5step3b](images/module4chapter5step3b.PNG)

7. Wählen Sie "Platzierungs Hinweise" aus, und wechseln Sie im Inspektor-Panel zu "interactable", und legen Sie unter Ereignisse "OnClick ()" die vorfab "lunarmodule" mit Drag & Drop ab. Wählen Sie dann die Dropdown-Funktion aus, und wählen Sie "lunarmodule" aus. Navigieren Sie dann zur Funktion "Schalter", und wählen Sie "Token" () aus.

    ![module4chapter5step3c](images/module4chapter5step3c.PNG)

8. Wählen Sie als nächstes die Lunarcom_Completed Prefab in der Hierarchie aus, und navigieren Sie zum Skript "lunarcom Intent erkenzer" in Inspector, und ziehen Sie dann die Schaltflächen "launchroundbutton", "rebertroundbutton" und "Platzierungs Hinweise" in die entsprechenden Positionen.

    ![module4chapter5step4](images/module4chapter5step4.PNG)

9. Klicken Sie im Unity-Editor auf die Schaltfläche "Wiedergabe", und klicken Sie auf die Schaltfläche "Launcher", und geben Sie die Ausdrücke wie "Push-Raketenstart Schaltfläche", "Anzeigen eines Platzierungs Hinweises", "drücken Sie die Rest-Schaltfläche" oder andere Ausdrücke im Zusammenhang mit der Anforderung zum Starten, zurücksetzen oder

    ![module4chapter5step5a](images/module4chapter5step5a.PNG)

    ![module4chapter5step5b](images/module4chapter5step5b.PNG)

    ![module4chapter5step5c](images/module4chapter5step5c.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In dieser Lektion haben wir gelernt, wie Sie die KI-gestützten Sprachbefehle mit Sprachbefehlen verbinden, um Sie als Eingabemethode zu verwenden. Nun kann unser Programm die Referenten als Sprachbefehle verwenden, um Eingaben für das Raketen Starter Programm zu erhalten.
