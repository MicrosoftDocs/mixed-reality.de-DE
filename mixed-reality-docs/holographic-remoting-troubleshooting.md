---
title: Problembehandlung und Einschränkungen für Holographic Remoting
description: Schritte zur Problembehandlung für Holographic Remoting auf hololens 2.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 08/01/2019
ms.topic: article
keywords: Windows Mixed Reality, holograms, Holographic Remoting, Remote Rendering, Netzwerk Rendering, hololens, Remote holograms, Problembehandlung, Hilfe
ms.openlocfilehash: 86b6979dbfc9b514b3af13ebdcc3d3ece17e6335
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718144"
---
# <a name="holographic-remoting-troubleshooting"></a>Problembehandlung bei Holographic Remoting

> [!IMPORTANT]
> Diese Anleitung gilt speziell für Holographic-Remoting auf hololens 2.

## <a name="spectre-mitigated-libraries-not-found"></a>Von Spectre abgeminderte Bibliotheken wurden nicht gefunden.

Für Holographic Remoting-Beispiel-Apps ist Spectre Entschärfung (/Qspectre) in der Releasekonfiguration aktiviert.

Wenn Sie einen schwerwiegenden Linker-Fehler erhalten, der besagt, dass "vccorlib. lib" nicht geöffnet werden kann, müssen Sie sicherstellen, dass die Visual Studio-Arbeitsauslastung die von Spectre abgeminderten Bibliotheken enthält Weitere Informationen finden Sie unter https://aka.ms/Ofhn4c.

# <a name="limitations"></a>Einschränkungen

Die folgenden APIs werden zurzeit **nicht** unterstützt, wenn Holographic Remoting für hololens 2 verwendet wird ```ERROR_NOT_SUPPORTED``` , und es wird ein Fehler ausgelöst, sofern nicht anders angegeben:

[Windows.Graphics.Holographic](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic)

* [Holographiccamera. viewconfiguration](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
* [Holographiccamerapose. override projectiontransform](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [Holographiccamerapose. overrideviewport](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [Holographiccamerapose. override viewtransform](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [Holographiccamer-deringparameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) -schlägt nicht fehl, aber der tiefen Puffer wird nicht remote ausgeführt.
* [Holographicdisplay. trygetviewconfiguration](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
* [Holographicspace. kreateframepresentationmonitor](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)

[Windows.Perception.Spatial](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial)

* [SpatialLocation. absoluteangularacceleration](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [SpatialLocation. absoluteangularaccelerationaxisangle](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [SpatialLocation. absoluteangularvelocity](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [SpatialLocation. absoluteangularvelocityaxisangle](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [SpatialLocation. absolutelinearacceleration](https://docs.microsoft.com/is-is/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [SpatialLocation. absolutelinearvelocity](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [Spatialstageframeofreferen. Current](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialstageframeofreference.current) -gibt immer ```nullptr```zurück.
* [Spatialstageframeofreferenzierung. requestnewstageasync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [Spatialanchor. removedbyuser](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [Spatialanchorexporter. GetDefault](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
) : gibt immer ```nullptr```zurück.
* [Spatialanchorexporter. requestaccessasync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
) -der asynchrone Vorgang wird ```SpatialPerceptionAccessStatus.DeniedBySystem```immer mit abgeschlossen.
* [Spatialanchortransfermanager. requestaccessasync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync) -der asynchrone Vorgang wird ```SpatialPerceptionAccessStatus.DeniedBySystem```immer mit abgeschlossen.
* [Spatialanchortransfermanager. tryexportanchorsasync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_) -der Async-Vorgang wird ```false```immer mit abgeschlossen.
* [Spatialanchortransfermanager. tryimportanchorsasync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
) -der Async-Vorgang wird ```nullptr```immer mit abgeschlossen.

[Windows.UI.Input.Spatial](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial)

* [Spatialinteraktionsource. trykreatehandmeshobserver](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [Spatialinteraktionsource. trykreatehandmeshobserverasync](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[Windows.Perception.Spatial.Preview](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview)

* [Spatialgraphinteroppreview. kreatelocatorfornode](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [Spatialgraphinteroppreview. trykreateframeofreferenzierung](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a>Siehe auch
* [Schreiben einer Holographic Remoting-Host-App](holographic-remoting-create-host.md)
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](holographic-remoting-create-player.md)
* [Software Lizenzbedingungen für Holographic Remoting](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzbestimmungen von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)