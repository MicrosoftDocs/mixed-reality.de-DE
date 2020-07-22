---
title: Azure-Cloudtutorials – 4. Integrieren von Azure Spatial Anchors
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie Azure Spatial Anchors innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, HoloLens 2, Azure Spatial Anchors
ms.localizationpriority: high
ms.openlocfilehash: 4eac2b96519abeebc277a53ad83d1b6dec8d61fd
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304931"
---
# <a name="4-integrating-azure-spatial-anchors"></a>4. Integrieren von Azure Spatial Anchors

In diesem Tutorial erfahren Sie, wie Sie **Azure Spatial Anchors** verwenden. Sie speichern die Position eines **nachverfolgten Objekts** als Azure Spatial Anchor. Anschließend fragen Sie die Position ab und stellen dem Benutzer einen Richtungspfeil zur Verfügung, der auf die Position zeigt.

## <a name="objectives"></a>Ziele

* Erlernen Sie die Grundlagen von Azure Spatial Anchors.
* Erfahren Sie, wie Sie die Szene einrichten, um Azure Spatial Anchors in diesem Projekt zu verwenden.
* Erfahren Sie, wie Sie Speicher- und Abfragespositionen integrieren.

## <a name="understanding-azure-spatial-anchors"></a>Grundlegendes zu Azure Spatial Anchors

 **Azure Spatial Anchors** ist Teil der Azure Cloud Services-Produktfamilie und wird zum Speichern von Ankerpositionen verwendet. Die gespeicherten Ankerpositionen können basierend auf der *Anker-ID* aus der Cloud abgerufen werden. Diese Ankerposition kann von Multi-Plattformgeräten wie HoloLens-, iOS- und Android-Geräten gemeinsam genutzt werden.

Weitere Informationen zu [Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/overview).

## <a name="preparing-azure-spatial-anchors"></a>Vorbereiten von Azure Spatial Anchors

Bevor Sie beginnen können, müssen Sie im Azure-Portal eine räumliche Ankerressource erstellen.
Erfahren Sie, wie Sie eine [räumliche Ankerressource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) erstellen können.

## <a name="preparing-the-scene"></a>Vorbereiten der Szene

In diesem Abschnitt erfahren Sie, wie Sie die Szene konfigurieren und die erforderlichen Änderungen vornehmen.

Navigieren Sie im Projektfenster zu **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager**.

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step1-1.png)

Ziehen Sie das Prefab **Anchor Manager** (Anker-Manager) aus dem Ordner **Manager** mithilfe von Drag & Drop in die Hierarchie der Szene.

Wählen Sie „**Anchor Manager** GameObject“ in der Hierarchie aus. Im Abschnitt „Inspector“ finden Sie **Spatial Anchor Manager (Script)** . Suchen Sie nach der Konto-ID und dem Schlüsselfeld, und fügen Sie die Anmeldeinformationen hinzu, die Sie in der vorherigen Phase als Voraussetzung erstellt haben.

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step2-1.png)

Suchen Sie nun das **Scene Controller**-Objekt (Szenencontroller) in der Hierarchie Ihrer Szene, und wählen Sie es aus. Der **Scene Controller**-Inspektor wird angezeigt.

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step3-1.png)

Sie sehen, dass das Feld **Anchor Manager** in der Komponente **Scene Controller** leer ist. Ziehen Sie **Anchor Manager** mithilfe von Drag & Drop aus der Hierarchie in der Szene in dieses Feld, und speichern Sie die Szene.

## <a name="build-and-deploy-the-app-to-your-hololens-2"></a>Erstellen und Bereitstellen der App auf dem HoloLens 2-Gerät

Azure Spatial Anchors können nicht in Unity ausgeführt werden, daher müssen Sie das Projekt auf Ihrem Gerät bereitstellen, um die Azure Spatial Anchors-Funktionalität zu testen.

> [!TIP]
> Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer Anwendung auf Ihrem Gerät](mr-learning-base-ch1.md#build-your-application-to-your-device).

## <a name="run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>Führen Sie die App auf Ihrer HoloLens 2 aus, und folgen Sie den Anweisungen in der App

### <a name="create-an-anchor-to-store-a-location"></a>Erstellen eines Ankers zum Speichern einer Position

In diesem Abschnitt erfahren Sie, wie Sie die Objektposition speichern.

Führen Sie die Anwendung aus, und klicken Sie im Hauptmenü der Benutzeroberfläche auf **Set Object** (Objekt festlegen).

Geben Sie den **Namen** des Objekts an, das Sie speichern möchten, und klicken Sie auf **Set Object** (Objekt festlegen), um den Vorgang fortzusetzen. Wenn Sie weitere Informationen zum Objekt hinzufügen möchten, wählen Sie das **Bild** aus, und beschreiben Sie das Objekt.

Um die Position zu speichern, klicken Sie auf **Save Location** (Position speichern).

Sie sehen einen **Ankerzeiger**, den Sie verschieben und an der Position platzieren können, die Sie speichern möchten. Anschließend wird ein Bestätigungspopupfenster angezeigt. Wenn Sie die Position bestätigen und speichern möchten, klicken Sie auf **Yes** (Ja). Andernfalls können Sie die Position ändern, indem Sie auf **No** (Nein) klicken und die Position erneut auswählen.

Nachdem Sie die Position durch Klicken auf **Yes** bestätigt haben, werden die Position und die Anker-ID im Azure-Cloudspeicher gespeichert. Nach dem Speichern wird das **Objekttag** im Anker mit dem Namen des Objekts angezeigt.

Die Objektposition wurde nun erfolgreich gespeichert.

### <a name="query-for-finding-an-anchor-location"></a>Abfrage zum Suchen nach einer Ankerposition

Nachdem Sie die Ankerposition ein Mal erfolgreich gespeichert haben, können Sie die Ankerposition nun durch Auswählen von **Search Object** (Nach Objekt suchen) im Hauptmenü ermitteln.

Nachdem Sie auf **Search Object** (Nach Objekt suchen) geklickt haben, wird ein neues Fenster geöffnet, in dem Sie den Namen des zu suchenden Objekts angeben.

Geben Sie den Namen des Objekts ein, und klicken Sie auf **Search Object** (Nach Objekt suchen). Wenn das Objekt zuvor gespeichert wurde und in der Datenbank gefunden wird, erhalten Sie die Objektkarte mit allen Details des Objekts, das Sie zuvor gespeichert haben.

Nun können Sie auf **Show Location** (Position anzeigen) klicken, um nach dem Objekt zu suchen. Wenn Sie auf **Show Location** (Position anzeigen) klicken, fragt das System die Objektadresse im Cloudspeicher ab.

Nachdem Sie die Position erfolgreich abgerufen haben, weist ein **Pfeil** auf die Position des Objekts hin. Folgen Sie der Pfeilmarkierung, bis Sie die Position des Objekts gefunden haben.

Nachdem Sie das Objekt gefunden haben, wird der Objektname oben angezeigt, und die Pfeilmarkierung wird ausgeblendet. Sie können nun auf das **Objekttag** klicken, um die Details des Objekts anzuzeigen.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie erfahren, wie Azure Spatial Anchors die Objektposition auf HoloLens 2 speichern und abrufen kann.

Im letzten Tutorial erfahren Sie, wie Sie **Azure Bot Service** verwenden, um natürliche Sprache als neue Interaktionsmethode für die Anwendung hinzuzufügen.

[Nächstes Tutorial: 5. Integrieren von Azure Bot Service in LUIS](mr-learning-azure-05.md)
