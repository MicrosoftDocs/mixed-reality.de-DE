---
title: Spracherkennung und-Aufzeichnung für das Lern-SDK-Modul von Mr
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: e5d0919a69c9e6b0c4233d23bf6d370f3def6576
ms.sourcegitcommit: c7c7e3c836373b65e319609b4e8389dea6b081de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460310"
---
# <a name="3----adding-the-azure-cognitive-services-speech-translation-component"></a>3.    Hinzufügen der Komponente zur Sprachübersetzung von Azure Cognitive Services

In diesem Tutorial erfahren Sie mehr über die Azure Cognitive Services Speech Translation-Komponente in unserem Projekt sowie über die Übersetzung in drei verschiedene Sprachen. 

1. Wählen Sie das Lunarcom_Base-Objekt in der Hierarchie aus, und klicken Sie im Inspektor-Panel auf Komponente hinzufügen. Suchen Sie nach lunarcomtranslationerkenzer, und wählen Sie ihn aus.

![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

> Hinweis: Stellen Sie sicher, dass der Simulator im Offline Modus deaktiviert ist, bevor Sie die Sprach-SDK-Übersetzer Zum übersetzen müssen Sie mit dem Internet verbunden sein. Siehe Abbildung unten, wo Sie diese Einstellung finden. 
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

2. Klicken Sie in der Dropdown Liste auf die Dropdown Liste, und wählen Sie die Sprache aus, in die übersetzt werden soll.

![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. Führen Sie nun die Anwendung aus, und testen Sie den Translator, indem Sie auf die Schaltfläche Satellit klicken und mit der Sprache beginnen. Klicken Sie erneut auf die Schaltfläche Satellit, um die Erkennung zu verhindern. Im folgenden finden Sie ein Beispiel dafür, wie ihre Szene aussehen sollte. Sie können die Sprache in der Dropdown Liste "Zielsprache" (siehe Abbildung oben) ändern, um die Übersetzung in andere Sprachen zu untersuchen.

> Hinweis: Vergewissern Sie sich vor dem Testen, dass der Offline Simulator deaktiviert ist, wie in der folgenden Abbildung dargestellt.
>
> ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

Im folgenden finden Sie ein Beispiel dafür, wie ihre Szene aussehen sollte:

![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Jetzt kann Ihr Projekt die Wörter, die Sie sprechen, in verschiedene Sprachen übersetzen. Sie können mit den Sprachen experimentieren und die Genauigkeit der Übersetzung testen. 

[Nächstes Tutorial: 4.  Einrichten des Verständnisses von Absichten und natürlicher Sprache](mrlearning-speechSDK-ch4.md)

