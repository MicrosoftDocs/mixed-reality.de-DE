---
title: Lokale Anker Übertragungen in Unity
description: Übertragen von Ankern zwischen mehreren hololens-Geräten in einer Unity-Anwendung.
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: Freigabe, Anker, worldanchor, Mr Sharing 250, worldanchortransferbatch, spatialperception, Transfer, local Anchor Transfer, Anchor Export, Anchor Import
ms.openlocfilehash: 82bcd07417fd5aa1b265ebc3c8edc939101dd783
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516136"
---
# <a name="local-anchor-transfers-in-unity"></a>Lokale Anker Übertragungen in Unity

In Fällen, in denen Sie keine <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">räumlichen Anker von Azure</a>verwenden können, ermöglichen lokale Anker Übertragungen einem hololens-Gerät das Exportieren eines Ankers, der von einem zweiten hololens-Gerät importiert werden soll.

>[!NOTE]
>Lokale Anker Übertragungen bieten weniger robusten Anker als Anker als <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">räumliche Azure-Anker</a>, und IOS-und Android-Geräte werden von diesem Ansatz nicht unterstützt.

### <a name="setting-the-spatialperception-capability"></a>Festlegen der spatialperception-Funktion

Damit eine APP räumliche Anker übertragen kann, muss die *spatialperception* -Funktion aktiviert werden.

Aktivieren der *spatialperception* -Funktion:
1. Öffnen Sie im Unity-Editor den Bereich **"Player Einstellungen"** (Bearbeiten > Projekteinstellungen > Player).
2. Klicken Sie auf die Registerkarte **"Windows Store"** .
3. Erweitern Sie **"Veröffentlichungs Einstellungen"** , und überprüfen Sie die Funktion **"spatialperception"** in der Liste **"Funktionen"** .

>[!NOTE]
>Wenn Sie Ihr Unity-Projekt bereits in eine Visual Studio-Projekt Mappe exportiert haben, müssen Sie entweder in einen neuen Ordner exportieren oder [Diese Funktion manuell in "appxmanifest" in Visual Studio festlegen](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).

### <a name="anchor-transfer"></a>Anker Übertragung

**Namespace:** *Unityengine. XR. WSA. Sharing*<br>
**Typ**: *Worldanchortransferbatch*

Zum Übertragen eines [worldanchors](coordinate-systems-in-unity.md)müssen Sie den Anker einrichten, der übertragen werden soll. Der Benutzer eines hololens scannt seine Umgebung und wählt entweder manuell oder Programm gesteuert einen Punkt im Bereich aus, um als Anker für die gemeinsame Nutzung zu gelten. Die Daten, die diesen Punkt darstellen, können dann serialisiert und an die anderen Geräte übertragen werden, die in der-Funktion gemeinsam genutzt werden. Jedes Gerät deserialisiert dann die Anker Daten und versucht, diesen Punkt im Speicherplatz zu finden. Damit die Anker Übertragung funktioniert, muss jedes Gerät in genügend der Umgebung gescannt werden, damit der durch den Anker dargestellte Punkt identifiziert werden kann.

### <a name="setup"></a>Setup

Der Beispielcode auf dieser Seite verfügt über einige Felder, die initialisiert werden müssen:
1. *Gameobject rootgameobject* ist ein *gameobject* in Unity, das über eine *worldanchor* -Komponente verfügt. Ein Benutzer in der freigegebenen Benutzer Darstellung wird dieses *gameobject* platzieren und die Daten an die anderen Benutzer exportieren.
2. *Worldanchor gamerootanchor* ist das *unityengine. XR. WSA. worldanchor* -Objekt, das auf *rootgameobject*basiert.
3. *Byte [] importeddata* ist ein Bytearray für den serialisierten Anker, der von jedem Client über das Netzwerk empfangen wird.

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

### <a name="exporting"></a>Export

Zum Exportieren benötigen wir lediglich einen *worldanchor* und wissen, wie wir ihn nennen werden, damit er für die empfangende App sinnvoll ist. Ein Client in der freigegebenen Darstellung führt diese Schritte aus, um den gemeinsamen Anker zu exportieren:
1. Erstellen eines *worldanchortransferbatches*
2. Zu übertragenden *worldanchors* hinzufügen
3. Export starten
4. Behandeln Sie das *onexportdataavailable* -Ereignis, wenn Daten verfügbar werden.
5. Behandeln des *onexportcomplete* -Ereignisses

Wir erstellen einen *worldanchortransferbatch* , um zu kapseln, was wir übertragen werden, und exportieren Sie dann in Bytes:

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

Wenn Daten verfügbar werden, senden Sie die Bytes an den Client oder Puffer, wenn Daten Segmente verfügbar sind, und senden Sie Sie über beliebige Möglichkeiten:

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

Nachdem der Export abgeschlossen ist, weisen Sie den Client an, die Daten zu verwerfen, wenn die Daten übertragen wurden und die Serialisierung fehlgeschlagen ist. Wenn die Serialisierung erfolgreich war, teilen Sie dem Client mit, dass alle Daten übertragen wurden und der Import Vorgang gestartet werden kann:

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

### <a name="importing"></a>Humi

Nachdem alle Bytes vom Absender empfangen wurden, können wir die Daten zurück in ein *worldanchortransferbatch* importieren und das Stamm Spielobjekt an demselben physischen Speicherort sperren. Hinweis: der Import schlägt gelegentlich fehl, und es muss ein erneuter Versuch unternommen werden:

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

Nachdem ein *gameobject-Objekt* über den *Lock Object* -Befehl gesperrt wurde, verfügt es über einen *worldanchor* , der ihn an derselben physischen Position in der Welt hält, er kann sich aber an einem anderen Speicherort im Unity-Koordinaten Bereich befinden als andere Benutzer.

