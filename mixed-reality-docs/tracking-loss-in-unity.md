---
title: Verlust der Überwachung in Unity
description: Behandeln von Datenverlust in einer Unity-app nachverfolgen.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Nachverfolgen von Verlust, -nachverfolgung Verlust image
ms.openlocfilehash: eb675860d67e9cad0d1129b3a6f61343990a4179
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595715"
---
# <a name="tracking-loss-in-unity"></a>Verlust der Überwachung in Unity

Wenn das Gerät in der ganzen Welt finden kann, hat die app "Verlust der Überwachung". Standardmäßig werden Unity Anhalten von der Aktualisierungsschleife des und ein Image des Begrüßungsbildschirms für den Benutzer angezeigt. Bei der nachverfolgung wieder auf die ist, wird das Image des Begrüßungsbildschirms verschwindet, und der Aktualisierungsschleife des wird fortgesetzt.

Als Alternative kann der Benutzer manuell dieser Übergang verarbeiten, durch die Einstellung deaktivieren. Alle Inhalte scheinbar Text gesperrt, während der nachverfolgung verloren gehen, wenn nichts ausgeführt wird, um es zu verarbeiten sind.

## <a name="default-handling"></a>Die Standardbehandlung

Standardmäßig wird der Aktualisierungsschleife des von der app sowie alle Nachrichten und Ereignisse für die Dauer der nachverfolgung von Verlust beendet. Gleichzeitig wird, wird ein Bild für den Benutzer angezeigt. Sie können dieses Image anpassen, indem Sie zu bearbeiten -> Einstellungen -> Player verwenden, klicken auf die Splash-Image, und Festlegen des Bildformats Holographic nachverfolgung verloren gehen.

## <a name="manual-handling"></a>Manuelle Behandlung

Zum Verlust der Überwachung manuell verarbeiten zu können, müssen Sie besuchen **bearbeiten** > **Projekteinstellungen** > **Player**  >   **Registerkarte "Einstellungen" Universal Windows Platform** > **Splash-Image** > **Windows Holographic** , und deaktivieren Sie "auf nachverfolgung Verlust anhalten und Bild anzeigen ". Nach dem Nachverfolgen von Änderungen mit den APIs, die unten angegebenen behandelt werden müssen.

**Namespace:** *UnityEngine.XR.WSA*<br>
**Typ:** *WorldManager*

* World-Manager macht eine Ereignis, um die nachverfolgung verloren geht/gewonnen erkennen (*WorldManager.OnPositionalLocatorStateChanged*) und eine Eigenschaft, die den aktuellen Status Abfragen (*WorldManager.state*)
* Wenn der Status der änderungsnachverfolgung nicht aktiv ist, wird die Kamera nicht angezeigt, in der virtuellen Welt zu übersetzen, auch wenn der Benutzer übersetzt. Dies bedeutet, dass Objekte nicht mehr alle physischen Standort entspricht, und alle gesperrt Text angezeigt.

Bei der Behandlung von Nachverfolgen von Änderungen auf Ihre eigenen. Sie müssen entweder für den Abruf von der State-Eigenschaft jeder Frame oder das Handle der *OnPositionalLocatorStateChanged* Ereignis.

### <a name="polling"></a>Abfragezeitplan

Der wichtigste Zustand ist *PositionalLocatorState.Active* d.h. nachverfolgung voll funktionsfähig ist. Jedem anderen Zustand werden an die Hauptkamera nur rotierenden Deltas vorgenommen. Zum Beispiel:

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a>Behandeln des Ereignisses OnPositionalLocatorStateChanged

Alternativ können Sie einfacher, und Sie können auch abonnieren *OnPositionalLocatorStateChanged* , die Übergänge zu behandeln:

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a>Siehe auch
* [Behandeln von Datenverlust in DirectX nachverfolgen](coordinate-systems-in-directx.md#handling-tracking-loss)
