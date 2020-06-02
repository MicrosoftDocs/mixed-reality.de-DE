---
title: 'Tutorials zu Azure Spatial Anchors: 3 Anzeigen von Azure Spatial Anchors-Feedback'
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 62ce1151837a345dea1bea4a8bea275cc851b9bd
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/26/2020
ms.locfileid: "83866900"
---
# <a name="3-displaying-azure-spatial-anchor-feedback"></a>3. Anzeigen von Azure Spatial Anchors-Feedback

In diesem Tutorial erfahren Sie, wie Sie Feedback zur Ankerermittlung, zu Ereignissen und zum Status bei der Verwendung von Azure Spatial Anchors (ASA) für Benutzer bereitstellen.

## <a name="objectives"></a>Ziele

* Erlernen des Einrichtens eines Bereichs der Benutzeroberfläche, in dem wichtige Informationen über die aktuelle ASA-Sitzung angezeigt werden
* Verstehen und Untersuchen der Feedbackelemente, die Benutzern vom ASA SDK zur Verfügung gestellt werden.

## <a name="set-up-asa-feedback-ui-panel"></a>Einrichten des Benutzeroberflächenbereichs für ASA-Feedback

Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf das Objekt **Instructions** > **TextContent**, wählen Sie **3D Object** > **Text - TextMeshPro** aus, um ein TextMeshPro-Textobjekt als untergeordnetes Element des Objekts „Instructions > TextContent“ zu erstellen, und geben Sie ihm einen passenden Namen, beispielsweise **Feedback**:

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-1.png)

> [!TIP]
> Um das Arbeiten mit Ihrer Szene zu erleichtern, legen Sie die <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> (Sichtbarkeit in der Szene) für das ParentAnchor-Objekt auf „Aus“ fest, indem Sie links neben dem Objekt auf das Augensymbol klicken. Dadurch wird das Objekt im Szenenfenster ausgeblendet, ohne seine Sichtbarkeit im Spiel zu ändern.

Ändern Sie bei noch ausgewähltem **Feedback**-Objekt im Inspektorfenster seine Position und Größe so, dass es ordentlich unter dem Anweisungstext platziert ist, beispielsweise:

* Ändern Sie die Rect-Transformations-**Pos Y** in -0,24
* Ändern Sie die Rect-Transformations-**Breite** in 0,555
* Ändern Sie die Rect-Transformations-**Höhe** in 0,1

Wählen Sie dann die Schriftarteigenschaften so, dass der Text gut in den Textbereich passt, beispielsweise:

* Ändern Sie den **Schriftschnitt** von „Text Mesh Pro (Script)“ in Fett
* Ändern Sie den **Schriftgrad** von „Text Mesh Pro (Script)“ in 0,17
* Ändern Sie die **Ausrichtung** von „Text Mesh Pro (Script)“ in „Zentriert und Mittig“

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-2.png)

Verwenden Sie bei noch immer ausgewähltem **Feedback**-Objekt im Inspektorfenster die Schaltfläche **Komponente hinzufügen**, um dem Feedback-Objekt die **Anchor-Feedback (Script)** -Komponente hinzuzufügen:

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-3.png)

Weisen Sie das **Feedback**-Objekt selbst dem Feld **Feedbacktext** der **Anchor Feedback Script (Script)** -Komponente zu:

![mrlearning-base](images/mrlearning-asa/tutorial3-section1-step1-4.png)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, wie Sie einen Benutzeroberflächenbereich erstellen, um den aktuellen Status der Azure Spatial Anchor-Benutzererfahrung anzuzeigen, um Echtzeitfeedback für Benutzer bereitzustellen.

[Nächste Lektion: 4. Azure Spatial Anchors für Android und iOS](mrlearning-asa-ch4.md)
