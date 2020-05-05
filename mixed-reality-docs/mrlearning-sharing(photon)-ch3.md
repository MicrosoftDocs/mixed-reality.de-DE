---
title: 'Tutorials zu Mehrbenutzerfunktionen: 4 Freigeben von Objektbewegungen für mehrere Benutzer'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 41b62eb2d9f400d0af341c9fcce887c72af7a3aa
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610629"
---
# <a name="3-sharing-object-movements-with-multiple-users"></a>3. Freigeben von Objektbewegungen für mehrere Benutzer

In diesem Tutorial erfahren Sie, wie Sie die Bewegungen von Objekten teilen, damit alle Teilnehmer einer geteilten Benutzeroberfläche zusammenarbeiten und die Interaktionen der einzelnen Benutzer anzeigen können.

## <a name="objectives"></a>Ziele

* Konfigurieren des Projekts zum Teilen der Bewegungen von Objekten
* Erlernen des Erstellens einer einfachen Mehrbenutzeranwendung zur Zusammenarbeit

## <a name="preparing-the-scene"></a>Vorbereiten der Szene

In diesem Abschnitt bereiten Sie die Szene vor, indem Sie das Tutorial-Prefab hinzufügen.

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs**, und ziehen Sie das **TableAnchor**-Prefab auf das **SharedPlayground**-Objekt im Hierarchiefenster, um es Ihrer Szene als untergeordnetes Objekt des SharedPlayground-Objekts hinzuzufügen:

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a>Konfigurieren von PUN zum Instanziieren der Objekte

In diesem Abschnitt konfigurieren Sie das Projekt für die Verwendung des RocketLauncher_Complete_Variant-Prefabs, das Sie im vorherigen Abschnitt erstellt haben, und definieren, wo es instanziiert werden soll.

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources**.

Klappen Sie im Hierarchiefenster das **NetworkLobby**-Objekt auf, wählen Sie das untergeordnete Objekt **NetworkRoom** aus, und suchen Sie dann im Inspektorfenster die Komponente **Photon Room (Script)** , um sie wie folgt zu konfigurieren:

* Weisen Sie das **PhotonUser**-Prefab aus dem Ordner „Resources“ dem **Photon User Prefab**-Feld zu

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-1.png)

Klappen Sie im Hierarchiefenster das **TableAnchor**-Objekt auf, während das untergeordnete Objekt **NetworkRoom** noch ausgewählt ist, und suchen Sie dann im Inspektorfenster die Komponente **Photon Room (Script)** , um sie wie folgt zu konfigurieren:

* Weisen Sie das untergeordnete Objekt **Table** aus dem Hierarchiefenster dem **Rocket Launcher Location**-Feld zu

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a>Ausprobieren der Benutzeroberfläche mit geteilter Objektbewegung

Wenn Sie das Unity-Projekt jetzt für Ihre HoloLens erstellen und bereitstellen und anschließend, wieder in Unity, auf die Schaltfläche „Wiedergabe“ drücken, um in den Spielmodus zu wechseln, während die Anwendung auf Ihrer HoloLens ausgeführt wird, sehen Sie, wie sich das Objekt in Unity bewegt, wenn Sie es in HoloLens bewegen:

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section3-step1-1.gif)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben Ihr Projekt erfolgreich so konfiguriert, dass Objektbewegungen synchronisiert werden und Benutzer die Objektbewegungen sehen können, wenn andere Benutzer die Objekte bewegen. Im nächsten Tutorial implementieren Sie Funktionen zur Ausrichtung der gemeinsamen Benutzeroberfläche an der physischen Welt, damit sich die Benutzer gegenseitig an ihren realen physischen Standorten sehen können und Objekte für alle Benutzer an der gleichen physischen Position und mit der gleichen Drehung angezeigt werden.

[Nächstes Tutorial: 4. Integrieren von Azure Spatial Anchors in eine gemeinsam genutzte Umgebung](mrlearning-sharing(photon)-ch4.md)
