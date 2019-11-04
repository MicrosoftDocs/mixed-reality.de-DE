---
title: Problembehandlung und Einschränkungen für Holographic Remoting
description: Schritte zur Problembehandlung für Holographic Remoting auf hololens 2.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 10/28/2019
ms.topic: article
keywords: Windows Mixed Reality, holograms, Holographic Remoting, Remote Rendering, Netzwerk Rendering, hololens, Remote holograms, Problembehandlung, Hilfe
ms.openlocfilehash: 7b438d9169c9306e0056655e561c04b62b1662cf
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434232"
---
# <a name="holographic-remoting-troubleshooting"></a>Problembehandlung bei Holographic Remoting

> [!IMPORTANT]
> Diese Anleitung gilt speziell für Holographic-Remoting auf hololens 2.

## <a name="spectre-mitigated-libraries-not-found"></a>Von Spectre abgeminderte Bibliotheken wurden nicht gefunden.

Für Holographic Remoting-Beispiel-Apps ist Spectre Entschärfung (/Qspectre) in der Releasekonfiguration aktiviert.

Wenn Sie einen schwerwiegenden Linker-Fehler erhalten, der besagt, dass "vccorlib. lib" nicht geöffnet werden kann, müssen Sie sicherstellen, dass die Visual Studio-Arbeitsauslastung die von Spectre abgeminderten Bibliotheken enthält Weitere Informationen finden Sie unter https://aka.ms/Ofhn4c.

## <a name="limitations"></a>Einschränkungen

Die folgenden APIs werden zurzeit **nicht** unterstützt, wenn Holographic Remoting für hololens 2 verwendet wird, und es wird ein ```ERROR_NOT_SUPPORTED``` Fehler ausgelöst, sofern nichts anderes angegeben ist:

[Windows.Graphics.Holographic](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [Holographiccamera. viewconfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
* [Holographiccamerapose. override projectiontransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [Holographiccamerapose. overrideviewport](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [Holographiccamerapose. override viewtransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
* [Holographiccamer-deringparameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - Schlägt nicht fehl, aber der tiefen Puffer wird nicht remotetet.
* [Holographicdisplay. trygetviewconfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
* [Holographicspace. kreateframepresentationmonitor](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)

[Windows.Perception.Spatial](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [SpatialLocation. absoluteangularacceleration](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [SpatialLocation. absoluteangularaccelerationaxisangle](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [SpatialLocation. absoluteangularvelocity](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [SpatialLocation. absoluteangularvelocityaxisangle](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [SpatialLocation. absolutelinearacceleration](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [SpatialLocation. absolutelinearvelocity](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [Spatialstageframeofreferenzierungs. Current](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - Gibt immer ```nullptr```zurück.
* [Spatialstageframeofreferenzierung. requestnewstageasync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
* [Spatialanchor. removedbyuser](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [Spatialanchorexporter. GetDefault](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - Unterstützt ab Version [2.0.9](holographic-remoting-version-history.md#v2.0.9). 
  - In früheren Versionen gibt immer ```nullptr```zurück. 
* [Spatialanchorexporter. requestaccessasync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - Unterstützt ab Version [2.0.9](holographic-remoting-version-history.md#v2.0.9). 
  - In früheren Versionen wurde der asynchrone Vorgang immer mit ```SpatialPerceptionAccessStatus.DeniedBySystem```abgeschlossen.
* [Spatialanchortransfermanager. requestaccessasync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - Der Async-Vorgang wird immer mit ```SpatialPerceptionAccessStatus.DeniedBySystem```abgeschlossen.
* [Spatialanchortransfermanager. tryexportanchorsasync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - Der Async-Vorgang wird immer mit ```false```abgeschlossen.
* [Spatialanchortransfermanager. tryimportanchorsasync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - Der Async-Vorgang wird immer mit ```nullptr```abgeschlossen.

[Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [Spatialinteraktionsource. trykreatehandmeshobserver](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [Spatialinteraktionsource. trykreatehandmeshobserverasync](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)

[Windows.Perception.Spatial.Preview](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [Spatialgraphinteroppreview. kreatelocatorfornode](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [Spatialgraphinteroppreview. trykreateframeofreferenzierung](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)
* [Spatialinteraktionsource. Controller](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)

## <a name="see-also"></a>Weitere Informationen
* [Holographic Remoting-Versionsverlauf](holographic-remoting-version-history.md)
* [Schreiben einer Holographic Remoting-Host-App](holographic-remoting-create-host.md)
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](holographic-remoting-create-player.md)
* [Holographic Remoting-Software – Lizenzbedingungen](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzbestimmungen von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
