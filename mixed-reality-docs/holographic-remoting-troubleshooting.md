---
title: Problembehandlung und Einschränkungen für Holographic Remoting
description: Schritte zur Problembehandlung für Holographic Remoting auf hololens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, Holographic Remoting, Remote Rendering, Netzwerk Rendering, hololens, Remote holograms, Problembehandlung, Hilfe
ms.openlocfilehash: 593b242326b83d4596d22a7e1a39ef18c26bc67a
ms.sourcegitcommit: b392847529961ac36bbff154ce0830f8b2dbd766
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86300502"
---
# <a name="holographic-remoting-troubleshooting"></a>Problembehandlung bei Holographic Remoting

> [!IMPORTANT]
> Diese Anleitung gilt speziell für Holographic-Remoting auf hololens 2.

## <a name="spectre-mitigated-libraries-not-found"></a>Von Spectre abgeminderte Bibliotheken wurden nicht gefunden.

Für Holographic Remoting-Beispiel-Apps ist Spectre Entschärfung (/Qspectre) in der Releasekonfiguration aktiviert.

Wenn Sie einen schwerwiegenden Linker-Fehler erhalten, der besagt, dass "vccorlib. lib" nicht geöffnet werden kann, müssen Sie sicherstellen, dass die Visual Studio-Arbeitsauslastung die von Spectre abgeminderten Bibliotheken enthält Weitere Informationen finden Sie unter https://aka.ms/Ofhn4c.

## <a name="speech"></a>Spracheingabe/-ausgabe

Der Holographic Remoting Player unterstützt ein diagnoseoverlay, das durch das sagen von aktiviert ```Enable Diagnostics``` und deaktiviert werden kann ```Disable Diagnostics``` . Wenn Sie Probleme mit diesen Sprachbefehlen haben, können Sie den Holographic Remoting Player auch über einen Webbrowser starten, indem Sie ```ms-holographic-remoting:?stats``` als URL verwenden.

## <a name="h265-video-codec-not-available"></a>H265-Videocodec nicht verfügbar

Sie müssen die [hevc-Video Erweiterungen](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) installieren, wenn Sie den H265-Videocodec in Ihrer Remote-app verwenden. Wenn Sie Probleme haben, bei denen der Codec installiert ist, aber nicht verwendet werden kann, finden Sie im Handbuch zur [Problem](https://docs.microsoft.com/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) Behandlung Weitere Informationen.

## <a name="limitations"></a>Einschränkungen

Die folgenden APIs werden zurzeit **nicht** unterstützt, wenn Holographic Remoting für hololens 2 verwendet wird, und es wird ein Fehler ausgelöst, ```ERROR_NOT_SUPPORTED``` sofern nicht anders angegeben:

[Windows.Graphics.Holographic](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [HolographicCamera.ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - Unterstützt ab Version [2.0.18](holographic-remoting-version-history.md#v2.0.18)
  - In früheren Versionen löst immer einen Fehler aus.
* [HolographicCamera.IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [HolographicViewConfiguration.RequestRenderTargetSize](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - Unterstützt ab Version [2.2.0](holographic-remoting-version-history.md#v2.2.0)
  - In früheren Versionen schlägt nicht fehl, aber die Größe des Renderziels wird nicht geändert.
* [Holographiccamerapose. override projectiontransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [Holographiccamerapose. overrideviewport](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [Holographiccamerapose. override viewtransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
  - Unterstützt ab Version [2.2.0](holographic-remoting-version-history.md#v2.2.0)
* [Holographiccamer-deringparameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - Schlägt nicht fehl, aber der tiefen Puffer wird nicht remotetet.
  - Unterstützt ab Version [2.1.0](holographic-remoting-version-history.md#v2.1.0)
* [HolographicDisplay.TryGetViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - Beim Abfragen von holographicviewconfigurationkind. photovideocamera wird immer ein zurückgegeben ```nullptr``` .
  - Unterstützt ab Version [2.0.18](holographic-remoting-version-history.md#v2.0.18)
  - In früheren Versionen löst immer einen Fehler aus.
* [Holographicspace. kreateframepresentationmonitor](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [Holographicdisplay. GetDefault](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - Meldet einen Fehler, wenn aufgerufen wird, bevor eine Verbindung hergestellt wurde.


[Windows.Perception.Spatial](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [SpatialLocation. absoluteangularacceleration](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [SpatialLocation.AbsoluteAngularAccelerationAxisAngle](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [SpatialLocation. absoluteangularvelocity](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [SpatialLocation.AbsoluteAngularVelocityAxisAngle](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [SpatialLocation. absolutelinearacceleration](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [SpatialLocation. absolutelinearvelocity](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [Spatialstageframeofreferenzierungs. Current](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - Unterstützt ab Version [2.2.0](holographic-remoting-version-history.md#v2.2.0)
  - In früheren Versionen gibt immer zurück ```nullptr``` .
* [Spatialstageframeofreferenzierung. requestnewstageasync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - Unterstützt ab Version [2.2.0](holographic-remoting-version-history.md#v2.2.0)
* [Spatialanchor. removedbyuser](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [SpatialAnchorExporter.GetDefault](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - Unterstützt ab Version [2.0.9](holographic-remoting-version-history.md#v2.0.9). 
  - In früheren Versionen gibt immer zurück ```nullptr``` . 
* [SpatialAnchorExporter.RequestAccessAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - Unterstützt ab Version [2.0.9](holographic-remoting-version-history.md#v2.0.9). 
  - In früheren Versionen wurde der Async-Vorgang immer mit abgeschlossen ```SpatialPerceptionAccessStatus.DeniedBySystem``` .
* [Spatialanchortransfermanager. requestaccessasync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - Der Async-Vorgang wird immer mit abgeschlossen ```SpatialPerceptionAccessStatus.DeniedBySystem``` .
* [Spatialanchortransfermanager. tryexportanchorsasync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - Der Async-Vorgang wird immer mit abgeschlossen ```false``` .
* [Spatialanchortransfermanager. tryimportanchorsasync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - Der Async-Vorgang wird immer mit abgeschlossen ```nullptr``` .

[Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [SpatialInteractionSource.TryCreateHandMeshObserver](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [SpatialInteractionSource.TryCreateHandMeshObserverAsync](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [Spatialinteraktionsource. Controller](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - Unterstützt ab Version [2.2.0](holographic-remoting-version-history.md#v2.2.0)

[Windows.Perception.Spatial.Preview](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [SpatialGraphInteropPreview.CreateLocatorForNode](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [SpatialGraphInteropPreview.TryCreateFrameOfReference](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a>Weitere Informationen
* [Holographic Remoting-Versionsverlauf](holographic-remoting-version-history.md)
* [Schreiben einer Holographic Remoting-Remote-App](holographic-remoting-create-host.md)
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](holographic-remoting-create-player.md)
* [Holographic Remoting-Software – Lizenzbedingungen](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzerklärung von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
