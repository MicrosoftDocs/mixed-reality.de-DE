---
title: Tutorials zu Azure Spatial Anchor-3. Anzeigen des Azure Spatial Anchor-Feedbacks
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 3d762950ea8e211fd5a8e4cf8af717674d3fe7e1
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553934"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3. Anzeigen des Azure Spatial Anchor-Feedbacks

In diesem Tutorial erfahren Sie, wie Sie Benutzern Feedback zur Anker Ermittlung, zu Ereignissen und zum Status bei der Verwendung von Azure Spatial Anchor (ASA) bereitstellen.

## <a name="objectives"></a>Ziele

* Erfahren Sie, wie Sie einen Benutzeroberflächen Bereich einrichten, in dem wichtige Informationen zur aktuellen ASA-Sitzung angezeigt werden.
* Verstehen und untersuchen Sie Feedback Elemente, die das ASA SDK Benutzern zur Verfügung stellt.

## <a name="set-up-asa-feedback-ui-panel"></a>Einrichten des ASA-Feedback-UI-Panels

Klicken Sie im Hierarchie Fenster mit der rechten Maustaste auf die **Anweisungen** > **textcontent** -Objekt, und wählen Sie **3D-Objekt** > **Text-textmeschpro** aus, um ein textmeshpro-Textobjekt als untergeordnetes Element der Anweisungen > textcontent-Objekt zu erstellen und ihm einen passenden Namen zuzuweisen, z. b. **Feedback**:

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> Um die Arbeit mit der Szene zu vereinfachen, legen Sie die <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Sichtbarkeit der Szene</a> für das Objekt "Objektanker" auf OFF fest, indem Sie auf das Augensymbol links neben dem Objekt klicken. Dadurch wird das Objekt im Szenen Fenster ausgeblendet, ohne die in-Game-Sichtbarkeit zu ändern.

Wenn das **Feedback** Objekt noch ausgewählt ist, ändern Sie im Inspektor-Fenster seine Position und Größe so, dass es sich unter dem Anweisungs Text befindet, z. b.:

* Ändern der Rect-Transformation **Torys Y** in-0,24
* Ändern Sie die **Breite** der Rect-Transformation in 0,555.
* Ändern Sie die **Höhe** der Rect-Transformation in 0,1.

Wählen Sie dann Schriftart Eigenschaften aus, damit der Text gut in den Textbereich passt, z. b.:

* Ändern Sie den Text Mesh pro- **Schrift** Schnitt (Skript) in "Fett".
* Ändern Sie den **Schrift** Grad Text Mesh pro (Skript) in 0,17.
* Ändern der **Ausrichtung** von Text Mesh pro (Skript) in Mitte und Mitte

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

Wenn das **Feedback** Objekt noch ausgewählt ist, verwenden Sie im Inspektor-Fenster die Schaltfläche **Komponente hinzufügen** , um dem Feedback Objekt die Komponente für das **Anchor-Feedback Skript (Skript)** hinzuzufügen:

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

Weisen Sie das **Feedback** Objekt selbst dem **Feedback Textfeld** des **Anchor-Feedback Skripts (Skript)** zu:

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, wie Sie einen Bereich für die Benutzeroberfläche erstellen, um den aktuellen Status der Azure Spatial Anchor-Oberfläche zum Bereitstellen von Echtzeitfeedback anzuzeigen.
