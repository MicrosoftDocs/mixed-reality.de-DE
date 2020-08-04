---
title: 'Tutorials zu Azure Spatial Anchors: 4 Anzeigen von Azure Spatial Anchors-Feedback'
description: In diesem Kurs erfahren Sie, wie Sie Azure Spatial Anchors in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: afcd7753fb2296503e67a1977b183df951124560
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376522"
---
# <a name="4-displaying-feedback-from-azure-spatial-anchors"></a>4. Anzeigen des Feedbacks von Azure Spatial Anchors

In diesem Tutorial erfahren Sie, wie Sie Feedback zur Ankerermittlung, zu Ereignissen und zum Status bei der Verwendung von Azure Spatial Anchors (ASA) für Benutzer bereitstellen.

## <a name="objectives"></a>Ziele

* Erlernen des Einrichtens eines Bereichs der Benutzeroberfläche, in dem grundlegende Informationen über die aktuelle ASA-Sitzung angezeigt werden
* Kennenlernen und Untersuchen der Feedbackelemente, die Benutzern vom ASA SDK zur Verfügung gestellt werden

## <a name="setting-up-asa-feedback-panel"></a>Einrichten des ASA-Feedbackbereichs

Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf das Objekt **Instructions** > **TextContent**. Wählen Sie **3D Object** > **Text - TextMeshPro** (3D-Objekt > Text – TextMeshPro) aus, um ein Textobjekt von TextMeshPro als untergeordnetes Element des Objekts „Instructions > TextContent“ zu erstellen:

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-1.png)

> [!TIP]
> Um das Arbeiten mit Ihrer Szene zu erleichtern, legen Sie die <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> (Sichtbarkeit in der Szene) für das ParentAnchor-Objekt auf „Aus“ fest, indem Sie links neben dem Objekt auf das Augensymbol klicken. Dadurch wird das Objekt im Szenenfenster ausgeblendet, ohne seine Sichtbarkeit im Spiel zu ändern.

Benennen Sie das neu erstellte Textobjekt (TMP) **Feedback**, und ändern Sie dann im Inspektorfenster seine Position und Größe so, dass es ordentlich unter dem Anweisungstext platziert ist, beispielsweise:

* Ändern Sie die **Pos Y** (Y-Position) der Rect Transform-Komponente in -0,24.
* Ändern Sie die **Width** (Breite) der Rect Transform-Komponente in 0,555.
* Ändern Sie die **Height** (Höhe) der Rect Transform-Komponente in 0,1.

Wählen Sie dann die Schriftarteigenschaften so, dass der Text gut in den Textbereich passt, beispielsweise:

* Ändern Sie den **Font Style** (Schriftschnitt) der TextMeshPro – Text-Komponente in Fett.
* Ändern Sie die **Font Size** (Schriftgrad) der TextMeshPro – Text-Komponente in 0,17.
* Ändern Sie das **Alignment** (Ausrichtung) der TextMeshPro – Text-Komponente in „Zentriert“ und „Mitte“.

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-2.png)

Wählen Sie im Hierarchiefenster das **Feedback**-Objekt aus, verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um die Komponente **Anchor Feedback Script (Script)** hinzuzufügen, und konfigurieren Sie sie wie folgt:

* Weisen Sie das **Feedback**-Objekt selbst dem Feld **Feedbacktext** der **Anchor Feedback Script (Script)** -Komponente zu.

![mr-learning-asa](images/mr-learning-asa/asa-04-section1-step1-3.png)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, wie Sie einen Benutzeroberflächenbereich erstellen. Er zeigt den aktuellen Status der Azure Spatial Anchor-Erfahrung an, um Benutzern Feedback in Echtzeit zu geben.

[Nächstes Tutorial: 5. Azure Spatial Anchors für Android und iOS](mr-learning-asa-05.md)
