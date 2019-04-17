---
title: Lokale Anchor-Übertragungen in Unity
description: Übertragen Sie Anker zwischen mehreren HoloLens-Geräte in einer Unity-Anwendung.
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: Freigabe, Anker, WorldAnchor, MR Freigabe 250, WorldAnchorTransferBatch, SpatialPerception, Übertragung, lokalen Anchor-Übertragung, Anchor-Export, Anker importieren
ms.openlocfilehash: 82bcd07417fd5aa1b265ebc3c8edc939101dd783
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605055"
---
# <a name="local-anchor-transfers-in-unity"></a>Lokale Anchor-Übertragungen in Unity

In Situationen, in dem können keine <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure räumliche Anker</a>, die Übertragung von lokalen Anker ermöglichen ein HoloLens-Gerät so exportieren Sie einen Anker, die durch ein zweites Gerät mit HoloLens importiert werden.

>[!NOTE]
>Lokale Anker Übertragungen bieten weniger stabil Anchor-Rückruf als <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure räumliche Anker</a>, und IOS- und Android-Geräte werden von diesem Ansatz nicht unterstützt.

### <a name="setting-the-spatialperception-capability"></a>Festlegen der SpatialPerception-Funktion

Damit eine app zum Übertragen von räumlichen Anker, der *SpatialPerception* Funktion muss aktiviert sein.

Vorgehensweise: Aktivieren der *SpatialPerception* Funktion:
1. Öffnen Sie im Unity-Editor, der **"Player Settings"** Bereich (Bearbeiten > Projekteinstellungen > Player)
2. Klicken Sie auf die **"Windows Store"** Registerkarte
3. Erweitern Sie **"Veröffentlichungseinstellungen"** und überprüfen Sie die **"SpatialPerception"** -Funktion in der **"Funktionen"** Liste

>[!NOTE]
>Wenn Sie bereits Ihr Unity-Projekt in Visual Studio-Projektmappe exportiert haben, müssen Sie zum Exportieren in einen neuen Ordner oder manuell [legen Sie diese Funktion in die appxmanifest-Datei in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).

### <a name="anchor-transfer"></a>Anker-Übertragung

**Namespace:** *UnityEngine.XR.WSA.Sharing*<br>
**Typ**: *WorldAnchorTransferBatch*

Zum Übertragen einer [WorldAnchor](coordinate-systems-in-unity.md), muss einen Anker zu übertragende herstellen. Der Benutzer von einem HoloLens scannt ihre Umgebung und entweder manuell oder programmgesteuert, wählt einen Punkt im Raum der Anker für den gemeinsamen Erfahrung sein. Die Daten, die von diesem Punkt stellt werden anschließend serialisiert und an die anderen Geräte, die in der Umgebung gemeinsam nutzen übertragen. Jedes Gerät dann Deserialisierung wird die Anker-Daten und versucht, diesen Punkt im Raum zu finden. In der Reihenfolge für Anker übertragen wird, funktionieren muss jedes Gerät so viele Zeichen von der Umgebung gescannt haben, dass der Punkt, der durch den Anker dargestellt wird, identifiziert werden kann.

### <a name="setup"></a>Setup

Der Beispielcode auf dieser Seite verfügt über einige Felder, die initialisiert werden müssen:
1. *"Gameobject" RootGameObject* ist eine *"gameobject"* in Unity, die eine *WorldAnchor* Komponente auf. Ein Benutzer in der gemeinsamen Erfahrung platziert diese *"gameobject"* und Exportieren der Daten in die andere Benutzer.
2. *WorldAnchor GameRootAnchor* ist die *UnityEngine.XR.WSA.WorldAnchor* , die sich in *RootGameObject*.
3. *Byte [] ImportedData* ist ein Bytearray, für den serialisierten Anker, die jeder Client über das Netzwerk empfangen wird.

```
public GameObject rootGameObject;
private UnityEngine.XR.WSA.WorldAnchor gameRootAnchor;

void Start ()
{
    gameRootAnchor = rootGameObject.GetComponent<UnityEngine.XR.WSA.WorldAnchor>();

    if (gameRootAnchor == null)
    {
        gameRootAnchor = rootGameObject.AddComponent<UnityEngine.XR.WSA.WorldAnchor>();
    }
}
```

### <a name="exporting"></a>Exportieren

Um zu exportieren, müssen wir nur eine *WorldAnchor* und wissen es nennen wir werden so, dass es für die empfangenden app sinnvoll ist. Ein Client in der freigegebenen Umgebung führt vor, um den freigegebenen Anker zu exportieren:
1. Erstellen Sie eine *WorldAnchorTransferBatch*
2. Hinzufügen der *WorldAnchors* übertragen
3. Der Export starten
4. Behandeln der *OnExportDataAvailable* Ereignis als Daten verfügbar.
5. Behandeln der *OnExportComplete* Ereignis

Wir erstellen eine *WorldAnchorTransferBatch* , um was zu kapseln wir werden übertragen und dann exportieren, die in Bytes:

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

Wenn Daten verfügbar sind, senden Sie die Bytes an den Client oder Puffer zu, wie Segmente der Daten zur Verfügung steht, und senden Sie auf den gewünschten Weise:

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

Nachdem der Export abgeschlossen ist, wenn wir Daten übertragen wurden haben, und Fehler bei der Serialisierung, die dem Client mitteilen, die Daten zu verwerfen. Wenn die Serialisierung erfolgreich war, weisen Sie den Client, dass alle Daten übertragen wurden, und Importieren von starten kann:

```
private void OnExportComplete(SerializationCompletionReason completionReason)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        SendExportFailedToClient();
    }
    else
    {
        SendExportSucceededToClient();
    }
}
```

### <a name="importing"></a>Importieren von

Nachdem alle Bytes vom Absender empfangen werden müssen, können wir importieren Sie die Daten wieder in einen *WorldAnchorTransferBatch* und Sperren Sie unsere Spiele Stammobjekt in demselben physischen Standort. Hinweis: der Import manchmal transiently fehl, und wiederholt werden muss:

```
// This byte array should have been updated over the network from TransferDataToClient
private byte[] importedData;
private int retryCount = 3;

private void ImportRootGameObject()
{
    WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
}

private void OnImportComplete(SerializationCompletionReason completionReason, WorldAnchorTransferBatch deserializedTransferBatch)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        Debug.Log("Failed to import: " + completionReason.ToString());
        if (retryCount > 0)
        {
            retryCount--;
            WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
        }
        return;
    }

    this.gameRootAnchor = deserializedTransferBatch.LockObject("gameRoot", this.rootGameObject);
}
```

Nach einer *"gameobject"* gesperrt ist, über die *LockObject* Aufruf muss eine *WorldAnchor* die in derselben physischen Position in der ganzen Welt halten, aber es kann sein, auf eine anderen Standort in der Unity-Zielkoordinatenbereich als andere Benutzer.

