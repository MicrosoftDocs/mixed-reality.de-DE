---
title: Azure-Cloudtutorials – 2. Integrieren von Azure Storage
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie Azure Table Storage und Azure Blob Storage in einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, HoloLens 2, Azure Storage
ms.localizationpriority: high
ms.openlocfilehash: 847e7a93717951af48157f0af32397d686cbbb84
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86304937"
---
# <a name="2-integrating-azure-storage"></a>2. Integrieren von Azure Storage

In diesem Tutorial erfahren Sie, wie Sie Entitätsdaten in Azure Table Storage und Miniaturansichten in Azure Blob Storage speichern. Mit dieser Funktion können wir *nachverfolgte Objekte* mit Daten wie ID, Name, Miniaturansicht usw. sitzungs- und geräteübergreifend in der Cloud speichern und aus ihr abrufen.

## <a name="objectives"></a>Ziele

* Grundlagen zu Azure Storage
* Erfahren Sie, wie Sie Daten in Table Storage speichern oder ändern bzw. aus Table Storage abrufen
* Erfahren Sie, wie Sie Bilder in Blob Storage speichern und aus Blob Storage löschen

## <a name="understanding-azure-storage"></a>Grundlegendes zu Azure Storage

**Azure Storage** ist eine Microsoft-Speicherlösung in der Cloud, die viele Szenarien und Anforderungen abdecken kann. Sie kann massiv skaliert werden und ist für Entwickler problemlos zugänglich. Alle Dienste können im Rahmen eines **Azure Storage-Kontos** genutzt werden. In unserem Anwendungsfall verwenden wir *Table Storage* und *Blob Storage*.

Weitere Informationen zu [Azure-Speicherdiensten](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-overview).

### <a name="azure-table-storage"></a>Azure Table Storage

Dieser Dienst ermöglicht es uns, Daten auf NoSQL-Art zu speichern. In diesem Projekt verwenden wir ihn, um Informationen zum *nachverfolgten Objekt* zu speichern, z. B. den Namen, eine Beschreibung, eine räumliche Anker-ID und mehr.

Im Kontext der Demoanwendung benötigen Sie zwei Tabellen: eine Tabelle zum Speichern von Informationen zum Projekt mit Informationen über den Zustand der trainierten Modelle (mehr dazu im Tutorial [Integrieren von Azure Custom Vision](mr-learning-azure-03.md)) und eine zweite Tabelle zum Speichern von Informationen zu *nachverfolgten Objekten*.

Weitere Informationen zu [Azure Table Storage](https://docs.microsoft.com/azure/storage/tables/table-storage-overview).

### <a name="azure-blob-storage"></a>Azure Blob Storage

Dieser Dienst ermöglicht das Speichern großer Binärdateien. Diese werden zum Speichern von Fotos verwendet, die für *nachverfolgte Objekte* als Miniaturansicht erstellt wurden.
Für die Demoanwendung benötigen Sie einen Blobcontainer, um die Bilder zu speichern.

Weitere Informationen zu [Azure Blob Storage](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction).

## <a name="preparing-azure-storage"></a>Vorbereiten von Azure Storage

Um die Azure-Speicherdienste nutzen zu können, benötigen Sie ein Azure-Speicherkonto. Informationen zum Erstellen eines Speicherkontos finden Sie unter [Erstellen eines Speicherkontos](https://docs.microsoft.com/azure/storage/common/storage-account-create?tabs=azure-portal). Weitere Informationen zu Speicherkonten finden Sie unter [Übersicht über das Azure-Speicherkonto](https://docs.microsoft.com/azure/storage/common/storage-account-overview).

Sobald Sie über ein Speicherkonto verfügen, können Sie die Verbindungszeichenfolge aus dem **Azure-Portal** abrufen, die im nächsten Abschnitt dieser Lektion benötigt wird.

### <a name="optional-azure-storage-explorer"></a>Optionaler Azure Storage-Explorer

Obwohl Sie alle Datenänderungen über die Benutzeroberfläche innerhalb der Anwendung anzeigen und überprüfen können, empfiehlt es sich, [Azure Storage-Explorer](https://azure.microsoft.com/features/storage-explorer/) zu installieren. Dieses Tool ermöglicht es Ihnen, die Daten im Azure-Speicher visuell anzuzeigen und ist eine große Hilfe beim Debuggen und Lernen.

> [!TIP]
> Zum Testen innerhalb des Unity-Editors können Sie einen lokalen Emulator verwenden:

> * Unter Windows 10 können Sie den [Azure-Speicheremulator](https://docs.microsoft.com/azure/storage/common/storage-use-emulator) verwenden.
> * Unter macOS/Linux können Sie [Azurite Docker Image](https://hub.docker.com/_/microsoft-azure-storage-azurite) für Docker verwenden.

## <a name="preparing-the-scene"></a>Vorbereiten der Szene

Suchen Sie im Hierarchiefenster nach dem **DataManager**-Objekt, und wählen Sie es aus.

![mr-learning-azure](images/mr-learning-azure/tutorial2-section4-step1-1.png)

Im Inspektor-Fenster sehen Sie, dass sich die Komponente **DataManager (Script)** dort befindet, wo sich alle Einstellungen befinden, die zu **Azure-Speicher** gehören. Alle relevanten Einstellungen sind bereits festgelegt. Sie müssen lediglich das Feld *Verbindungszeichenfolge* durch den Wert ersetzen, den Sie aus dem Azure-Portal abrufen können. Wenn Sie eine lokale Azure-Speicheremulatorlösung verwenden, können Sie die bereits bereitgestellte *Verbindungszeichenfolge* beibehalten.

**DataManager (Script)** ist für die Kommunikation mit **Table Storage** bzw. **Blob Storage** zuständig, die von anderen Controllerskripts in den Benutzeroberflächenkomponenten genutzt werden.

## <a name="writing-and-reading-data-from-azure-table-storage"></a>Schreiben und Lesen von Daten aus Azure Table Storage

Nach Abschluss der Vorbereitungen ist es an der Zeit, ein *nachverfolgtes Objekt* zu erstellen.

Öffnen Sie die Anwendung auf Ihrem HoloLens-Gerät, und klicken Sie auf **Set Object** (Objekt festlegen). Sie erkennen, wie das *EnterObjectName-* -Objekt in der Hierarchie aktiviert wird. Klicken Sie in diesem Menü auf die *Suchleiste*, und geben Sie den Namen ein, den Sie dem *nachverfolgten Objekt* zuweisen möchten. Nachdem Sie einen Namen festgelegt haben, klicken Sie auf die Schaltfläche **Set Object** (Objekt festlegen). Dadurch wird das *nachverfolgte Objekt* in Azure Table Storage erstellt, und die **Objektkarte** wird angezeigt.

Diese **Objektkarte** ist eine Benutzeroberflächendarstellung des *nachverfolgten Objekts* und spielt in dieser Tutorialreihe an mehreren Stellen eine wichtige Rolle.

Klicken Sie nun auf das *Textfeld* mit der Beschreibung, und geben Sie „Car“ (Auto) ein. Klicken Sie anschließend auf die Schaltfläche **Save** (Speichern), um die Änderungen zu speichern. Beenden Sie die Anwendung, und führen Sie sie dann erneut aus.

Klicken Sie dieses Mal auf **Search Object** (Objekt suchen), und geben Sie den Namen in die *Suchleiste* ein, den Sie zuvor beim Erstellen des *nachverfolgten Objekts* verwendet haben. Sie sehen, dass die **Objektkarte** mit allen Daten aus **Azure Table Storage** abgerufen wird.

Sie können die **Objektkarte** schließen, neue *nachverfolgte Objekte* erstellen und ihre Daten bearbeiten.

> [!TIP]
> Wenn Sie [Azure Storage-Explorer](https://azure.microsoft.com/features/storage-explorer/) installiert haben, sehen Sie sich die Tabelle *objects* an, die die erstellten *nachverfolgten Objekte* enthält.

## <a name="uploading-and-download-image-from-azure-blob-storage"></a>Hochladen von Bildern in Azure Blob Storage und Herunterladen von Bildern aus Azure Blob Storage

In diesem Abschnitt verwenden Sie Azure Blob Storage zum Hochladen und Herunterladen von Bildern, die als Miniaturansichten für *nachverfolgte Objekte* verwendet werden.

> [!NOTE]
> In diesem Tutorial verwendet die Anwendung Fotos zum Hochladen von Bildern in den Blobspeicher. Wenn Sie dies lokal über den Unity-Editor ausführen, stellen Sie sicher, dass eine Webcam mit Ihrem Computer verbunden ist.

Öffnen Sie die Anwendung auf dem HoloLens-Gerät, klicken Sie auf **Set Object** (Objekt festlegen), und geben Sie in die *Suchleiste* den Begriff „Car“ (Auto) ein. Nun sollte die **Objektkarte** angezeigt werden. Klicken Sie auf die Schaltfläche **Camera** (Kamera). Sie werden dann aufgefordert, eine AirTap-Aktion auszuführen, um ein Foto aufzunehmen. Nach der Aufnahme eines Fotos wird eine Meldung angezeigt, die Sie über den aktiven Upload informiert. Nach einer Weile sollte das Bild an der Stelle angezeigt werden, an der sich zuvor der Platzhalter befunden hat.

Führen Sie nun die Anwendung erneut aus, und suchen Sie nach dem *nachverfolgten Objekt*. Das zuvor hochgeladene Bild sollte als Miniaturansicht angezeigt werden.

## <a name="deleting-image-from-azure-blob-storage"></a>Löschen von Bildern aus Azure Blob Storage

Im vorherigen Abschnitt haben Sie neue Images in Azure Blob Storage hochgeladen. In diesem Abschnitt löschen Sie eine Bildminiaturansicht für *nachverfolgte Objekte*.

Öffnen Sie die Anwendung auf dem HoloLens-Gerät, klicken Sie auf **Set Object** (Objekt festlegen), und geben Sie in die *Suchleiste* den Begriff „Car“ (Auto) ein. Nun sollte die **Objektkarte** mit dem Miniaturbild angezeigt werden. Klicken Sie auf die Schaltfläche **Delete** (Löschen). Beachten Sie, dass die Miniaturansicht des Bilds durch das Platzhalterbild ersetzt wird.

Führen Sie die Anwendung nun erneut aus, und suchen Sie nach dem *nachverfolgten Objekt* der zuvor gelöschten Miniaturansicht. Es sollte nur das Platzhalterbild angezeigt werden.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie erfahren, wie Sie mithilfe der Azure-Speicherdienste unstrukturierte Daten persistent speichern können (in diesem Fall **nachverfolgte Objekte** und Binärdateien in Form von Miniaturansichten für die **HoloLens 2**-Demoanwendung in der Cloud).

Im nächsten Tutorial erfahren Sie, wie Sie mithilfe von Azure Custom Vision Bilder erkennen können, die einem *nachverfolgten Objekt* zugeordnet sind.

[Nächstes Tutorial: 3. Integrieren von Azure Custom Vision](mr-learning-azure-03.md)
