---
title: 'Tutorials zu Mehrbenutzerfunktionen: 4 Freigeben von Objektbewegungen für mehrere Benutzer'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: cd8f0cb8888e7225566acc8c4b26aced3e4d977e
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305230"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. Freigeben von Objektbewegungen für mehrere Benutzer

In diesem Tutorial erfahren Sie, wie Sie die Bewegungen von Objekten teilen, damit alle Teilnehmer einer geteilten Benutzeroberfläche zusammenarbeiten und die Interaktionen der einzelnen Benutzer anzeigen können.

## <a name="objectives"></a>Ziele

* Konfigurieren des Projekts zum Teilen der Bewegungen von Objekten
* Erlernen des Erstellens einer einfachen Mehrbenutzer-App zur Zusammenarbeit

## <a name="preparing-the-scene"></a>Vorbereiten der Szene

In diesem Abschnitt bereiten Sie die Szene vor, indem Sie das Tutorial-Prefab hinzufügen.

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs**, und ziehen Sie das **TableAnchor**-Prefab auf das **SharedPlayground**-Objekt im Hierarchiefenster, um es Ihrer Szene als untergeordnetes Objekt des SharedPlayground-Objekts hinzuzufügen:

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a>Konfigurieren von PUN zum Instanziieren der Objekte

In diesem Abschnitt konfigurieren Sie das Projekt so, dass es die Benutzeroberfläche von Rover-Explorer verwendet, die in den [Tutorials mit den ersten Schritten](mr-learning-base-01.md) erstellt wurde, und definieren, wo sie instanziiert werden soll.

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources**.

Klappen Sie im Hierarchiefenster das **NetworkLobby**-Objekt auf, wählen Sie das untergeordnete Objekt **NetworkRoom** aus, und suchen Sie dann im Inspektorfenster die Komponente **Photon Room (Script)** , um sie wie folgt zu konfigurieren:

* Weisen Sie dem Feld **RoverExplorer Prefab** das Prefab **RoverExplorer_Complete_Variant** aus dem Ordner „Resources“ zu.

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section2-step1-1.png)

Klappen Sie im Hierarchiefenster das **TableAnchor**-Objekt auf, während das untergeordnete Objekt **NetworkRoom** noch ausgewählt ist, und suchen Sie dann im Inspektorfenster die Komponente **Photon Room (Script)** , um sie wie folgt zu konfigurieren:

* Weisen Sie dem Feld **Rover Explorer Location** (Rover-Explorer-Position) das untergeordnete Objekt **Table** aus dem Hierarchiefenster zu.

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a>Ausprobieren der Benutzeroberfläche mit geteilter Objektbewegung

Wenn Sie das Unity-Projekt jetzt für Ihr HoloLens-Gerät erstellen und bereitstellen und anschließend, wieder in Unity, auf die Schaltfläche „Wiedergabe“ drücken, um in den Spielmodus zu wechseln, während die App auf Ihrem HoloLens-Gerät ausgeführt wird, sehen Sie, wie sich das Objekt in Unity bewegt, wenn Sie es in HoloLens bewegen:

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section3-step1-1.gif)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben Ihr Projekt erfolgreich so konfiguriert, dass Objektbewegungen synchronisiert werden, damit Benutzer sehen können, wie sich die Objekte bewegen, wenn andere Benutzer sie bewegen. Im nächsten Tutorial implementieren Sie Funktionen, um die Lösung in der physischen Welt auszurichten. Dadurch wird sichergestellt, dass die Benutzer einander an ihrem tatsächlichen physischen Standort sehen, sodass die Objekte für alle Benutzer in der gleichen physischen Position und Drehung angezeigt werden.

[Nächstes Tutorial: 5. Integrieren von Azure Spatial Anchors in eine gemeinsam genutzte Umgebung](mr-learning-sharing-05.md)
