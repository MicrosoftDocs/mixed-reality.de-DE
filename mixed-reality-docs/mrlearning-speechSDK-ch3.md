---
title: Tutorials zu Azure Speech Services-3. Hinzufügen der Komponente zur Sprachübersetzung von Azure Cognitive Services
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 490b9f6142208a190748b6d76c57be493172c1e5
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913197"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3. Hinzufügen der Komponente zur Sprachübersetzung von Azure Cognitive Services

In diesem Tutorial erfahren Sie mehr über die Komponente zur Sprachübersetzung von Azure Cognitive Services in unserem Projekt sowie über die Übersetzung in drei verschiedene Sprachen.

## <a name="instructions"></a>Anweisungen

1. Wählen Sie das Objekt Lunarcom_Base in der Hierarchie aus, und klicken Sie im Inspektor-Panel auf Komponente hinzufügen. Suchen Sie nach dem lunarcom-Übersetzungs Erkennungs Modul.

    ![Module4Chapter3step1im](images/module4chapter3step1im.PNG)

    Deaktivieren Sie den Simulator im Offline Modus.

    ![Module4Chapter3noteim](images/module4chapter3noteim.PNG)

    >[!IMPORTANT]
    >Bevor Sie fortfahren, stellen Sie sicher, dass der Simulator im Offline Modus deaktiviert ist (siehe Abbildung oben), bevor Sie den Sprach-SDK-Konvertierer testen. Zum übersetzen müssen Sie mit dem Internet verbunden sein.

2. Klicken Sie in der lunarcom-Übersetzungs Erkennung auf die Dropdown Liste, und wählen Sie die Sprache aus, in die übersetzt werden soll.

    ![Module4Chapter3step2im](images/module4chapter3step2im.PNG)

3. Führen Sie nun die Anwendung aus, und testen Sie den Translator, indem Sie auf die Schaltfläche Satellit klicken und mit der Sprache beginnen. Klicken Sie erneut auf die Schaltfläche Satellit, um die Erkennung zu verhindern. Im folgenden finden Sie ein Beispiel dafür, wie ihre Szene aussehen sollte. Sie können die Sprache in der Dropdown Liste "Zielsprache" (siehe Abbildung oben) ändern, um die Übersetzung in andere Sprachen zu untersuchen.

    Im folgenden finden Sie ein Beispiel dafür, wie ihre Szene aussehen sollte:

    ![Module4Chapter3exampleim](images/module4chapter3exampleim.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Jetzt kann Ihr Projekt die Wörter, die Sie sprechen, in verschiedene Sprachen übersetzen. Sie können mit den Sprachen experimentieren und die Genauigkeit der Übersetzung testen.

[Nächstes Tutorial: 4. Einrichten der Absicht und der Kenntnisse in natürlicher Sprache](mrlearning-speechSDK-ch4.md)
