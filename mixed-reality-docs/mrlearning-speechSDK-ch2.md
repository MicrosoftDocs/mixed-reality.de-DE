---
title: 'Tutorials zu Azure Speech-Diensten: 2 Hinzufügen eines Offlinemodus für die lokale Sprache-zu-Text-Übersetzung'
description: In diesem Kurs erfahren Sie, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 75ddce9063bb9d33f5fe2343fe30178222a5f8ac
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "79031623"
---
# <a name="2-using-speech-recognition-to-execute-commands"></a>2. Verwenden der Spracherkennung zum Ausführen von Befehlen

In diesem Tutorial fügen Sie die Möglichkeit hinzu, Befehle mithilfe der Azure-Spracherkennung auszuführen, sodass Sie basierend auf dem von Ihnen definierten Wort oder Ausdruck eine Aktion auslösen können.

## <a name="objectives"></a>Ziele

* Erfahren, wie die Azure-Spracherkennung zum Ausführen von Befehlen verwendet werden kann

## <a name="instructions"></a>Anweisungen

Wählen Sie im Hierarchiefenster das **Lunarcom**-Objekt aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um dem Lunarcom-Objekt die Komponente **Lunarcom Wake Word Recognizer (Script)** hinzuzufügen und sie wie folgt zu konfigurieren:

* Geben Sie im Feld **Wake Word** (Wort zum Aufwecken) einen passenden Ausdruck ein, z. B. _Terminal aktivieren_.
* Geben Sie im Feld **Dismiss Word** (Wort zum Schließen) einen passenden Ausdruck ein, z. B. _Terminal schließen_.

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> Die Komponente „Lunarcom Wake Word Recognizer (Script)“ ist kein Bestandteil des MRTK. Sie wurde zusammen mit den Ressourcen für dieses Tutorial zur Verfügung gestellt.

Wenn Sie jetzt in den Spielmodus wechseln, wie im vorherigen Tutorial, ist der Terminalbereich standardmäßig aktiviert. Sie können ihn jetzt jedoch deaktivieren, indem Sie das Wort zum Schließen aussprechen, **Terminal schließen**:

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-2.png)

Und es erneut aktivieren, indem Sie das Wort zum Aufwecken sprechen **Terminal aktivieren**:

![mrlearning-speech](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> Die Anwendung muss eine Verbindung mit Azure herstellen, achten Sie also darauf, dass Ihr Computer/Gerät mit dem Internet verbunden ist.

> [!TIP]
> Wenn Sie davon ausgehen müssen, dass Sie häufig keine Verbindung mit Azure herstellen können, können Sie außerdem Sprachbefehle mithilfe von MRTK implementieren. Befolgen Sie dazu die Anweisungen unter [Aktivieren der Sprachbefehle](mrlearning-base-ch5.md#enabling-voice-commands).

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben die von Azure unterstützten Sprachbefehle implementiert. Führen Sie die Anwendung auf Ihrem Gerät aus, um sicherzustellen, dass das Feature ordnungsgemäß funktioniert.

Im nächsten Tutorial erfahren Sie, wie Sprache mithilfe von Azure-Sprachübersetzung übersetzt wird.

[Nächstes Tutorial: 3. Hinzufügen der Sprachübersetzungskomponente von Azure Cognitive Services](mrlearning-speechSDK-ch3.md)
