---
title: Spracherkennung und-Aufzeichnung für das Lern-SDK-Modul von Mr
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: b13b22fcdce2e7fa1319d241302b764f457aabba
ms.sourcegitcommit: b086d7a62ee0c7913aa8f66c90e9d2527f270264
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68485602"
---
# <a name="2----adding-an-offline-mode-for-local-speech-to-text-translation"></a>2.    Hinzufügen eines Offline Modus für die lokale Sprachübersetzung

In diesem Tutorial fügen wir einen Offline Modus hinzu, mit dem Sie eine lokale Sprachübersetzung durchführen können, wenn keine Verbindung mit dem Azure-Dienst hergestellt werden kann. Wir *simulieren* auch den Zustand "getrennt".

## <a name="instructions"></a>Anweisungen

1. Wählen Sie das Lunarcom_Base-Objekt in der Hierarchie aus, und klicken Sie im Inspektor-Panel auf Komponente hinzufügen. Suchen Sie nach der lunarcom-Offline Kennung, und wählen Sie Sie aus

![Module4Chapter2step1im](images/module4chapter2step1im.PNG)

2. Klicken Sie in der Dropdown Liste auf die Dropdown Liste, und wählen Sie aktiviert aus. Dadurch wird das Projekt so programmiert, dass der Benutzer nicht über eine Verbindung verfügt. 

![Module4Chapter2step1im](images/module4chapter2step2im.PNG)

3. Klicken Sie jetzt im Unity-Editor auf Play, und testen Sie es. Drücken Sie das Mikrofon in der unteren linken Ecke der Szene, und beginnen Sie mit der Spracheingabe. 

> [!NOTE]
> Da wir offline sind, wurde die Wake-Word-Funktion deaktiviert. Sie müssen jedes Mal, wenn Sie die Sprache im Offline Zustand erkennen möchten, physisch auf das Mikrofon klicken. 

Im folgenden finden Sie ein Beispiel dafür, wie ihre Szene aussehen könnte.

![Module4Chapter2exampleim](images/module4chapter2exampleim.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Der Offline Modus wurde aktiviert. Wenn Sie nun offline sind, können Sie weiterhin mit dem Sprach-SDK für Ihr Projekt arbeiten. 


[Nächstes Tutorial: 3.  Hinzufügen der Komponente zur Sprachübersetzung von Azure Cognitive Services](mrlearning-speechSDK-ch3.md)

