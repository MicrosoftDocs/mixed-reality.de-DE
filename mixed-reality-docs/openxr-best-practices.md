---
title: Bewährte Methoden für openxr
description: Informieren Sie sich über die bewährten Methoden für die visuelle Qualität, Stabilität und Leistung Ihrer openxr-Anwendungen.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: Openxr, Khronos, basicxrapp, DirectX, Native, Native APP, benutzerdefiniertes Modul, Middleware, bewährte Methoden, Leistung, Qualität, Stabilität
ms.openlocfilehash: 01ce2ac0a69ffdf5dd1f00b92f37f54964f4c30c
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163354"
---
# <a name="openxr-app-best-practices"></a>Bewährte Methoden für die openxr-App

Ein Beispiel für die unten aufgeführten bewährten Methoden finden Sie in der Datei " [openxrprogram. cpp](https://github.com/microsoft/OpenXR-SDK-VisualStudio/blob/master/samples/BasicXrApp/OpenXrProgram.cpp) " von basicxrapp. Die Run ()-Funktion am Anfang erfasst einen typischen openxr-App-Codefluss von der Initialisierung zur Ereignis-und Renderingschleife.

## <a name="best-practices-for-visual-quality-and-stability"></a>Bewährte Methoden für die visuelle Qualität und Stabilität

Die bewährten Methoden in diesem Abschnitt beschreiben, wie Sie die beste visuelle Qualität und Stabilität in jeder openxr-Anwendung erzielen.

Weitere Leistungs Empfehlungen für hololens 2 finden Sie weiter unten im Abschnitt [bewährte Methoden für die Leistung auf hololens 2](#best-practices-for-performance-on-hololens-2) .

### <a name="gamma-correct-rendering"></a>Gamma-korrektes Rendering

Um sicherzustellen, dass die Renderingpipeline Gamma-correct ist, muss darauf geachtet werden. Beim Rendern in eine vorhandenes SwapChain sollte das Renderziel-Ansichts Format dem vorhandenes SwapChain-Format entsprechen (z. b. DXGI_FORMAT_B8G8R8A8_UNORM_SRGB für das vorhandenes SwapChain-Format und die renderzielansicht).
Eine Ausnahme ist, wenn die Renderingpipeline der App eine manuelle sRGB-Konvertierung in Shader-Code durchführt. in diesem Fall sollte die APP ein sRGB-vorhandenes SwapChain-Format anfordern, aber das lineare Format für die renderzielansicht verwenden (z. b. Anforderungs DXGI_FORMAT_B8G8R8A8_UNORM_SRGB als Das vorhandenes SwapChain-Format, jedoch DXGI_FORMAT_B8G8R8A8_UNORM als renderzielansicht), um zu verhindern, dass Inhalt doppelt korrigiert wird.

### <a name="submit-depth-buffer-for-projection-layers"></a>Tiefen Puffer für Projektions Ebenen übermitteln

Verwenden Sie immer `XR_KHR_composition_layer_depth` Erweiterung, und übermitteln Sie den tiefen Puffer mit der Projektionsebene, wenn Sie einen Frame an `xrEndFrame`senden.
Dies verbessert die Stabilität des Hologramms durch die Aktivierung der neuprojektion von Hardware auf hololens 2.

### <a name="choose-a-reasonable-depth-range"></a>Auswählen eines angemessenen tiefen Bereichs

Bevorzugen Sie einen engeren tiefenbereich, um den Bereich der virtuellen Inhalte so zu gestalten, dass Sie die – Hologramm-Stabilität auf hololens
Beispielsweise verwendet das openxrprogram. cpp-Beispiel 0,1 bis 20 Meter.
Verwenden Sie [umgekehrtes-Z](https://developer.nvidia.com/content/depth-precision-visualized) für eine einheitlichere tiefen Auflösung.
Beachten Sie, dass bei hololens 2 die Verwendung des bevorzugten `DXGI_FORMAT_D16_UNORM` tiefen Formats dazu beiträgt, eine bessere Framerate und-Leistung zu erzielen, obwohl 16-Bit-Tiefen Puffer weniger Tiefe Auflösung als 24-Bit-Tiefen Puffer bieten.
Daher ist es wichtiger, diese bewährten Methoden zu befolgen, um die Tiefe Auflösung optimal zu nutzen.

### <a name="prepare-for-different-environment-blend-modes"></a>Vorbereiten für verschiedene Umgebungs-Blend-Modi

Wenn Ihre Anwendung auch auf immersiven Headsets ausgeführt werden soll, die die Welt vollständig blockieren, stellen Sie sicher, dass Sie unterstützte Umgebungs-Blend-Modi mithilfe `xrEnumerateEnvironmentBlendModes`-API auflisten und ihren Renderinginhalt entsprechend vorbereiten.
Für ein System mit `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE` z. b. hololens sollte die APP beispielsweise transparent als Klartext verwenden. bei einem System mit `XR_ENVIRONMENT_BLEND_MODE_OPAQUE`sollte die APP jedoch eine nicht transparente Farbe oder einen virtuellen Raum im Hintergrund darstellen.

### <a name="choose-unbounded-reference-space-as-applications-root-space"></a>Nicht begrenzten Verweis Raum als Stamm Bereich der Anwendung auswählen

Anwendungen stellen in der Regel einen bestimmten Stamm Koordinaten Bereich zum Verbinden von Sichten, Aktionen und holograms her.
Verwenden Sie `XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT`, wenn die Erweiterung für die Einrichtung eines [weltweiten Koordinatensystems](coordinate-systems.md#building-a-world-scale-experience)unterstützt wird. Dadurch kann Ihre APP unerwünschte – Hologramm-Abweichungen vermeiden, wenn sich der Benutzer weit entfernt (z. b. 5 Meter entfernt), von wo aus die APP gestartet wird.
Verwenden Sie `XR_REFERENCE_SPACE_TYPE_LOCAL` als Fall Back, wenn die unbeschränkte Speicherplatz Erweiterung nicht vorhanden ist.

### <a name="associate-hologram-with-spatial-anchor"></a>– Hologramm mit räumlichem Anker verknüpfen

Wenn Sie einen ungebundenen Verweis Bereich verwenden, können Hologramme, die Sie direkt in diesem Verweis Bereich platzieren, abweichen, wenn [der Benutzer zu den entfernten Räumen geht und dann zurück](coordinate-systems.md#building-a-world-scale-experience)kehrt.
Für – Hologramm-Benutzer, die sich an einem diskreten Ort auf der Welt befinden, erstellen Sie mithilfe der `xrCreateSpatialAnchorSpaceMSFT` Erweiterungs Funktion [einen räumlichen Anker](spatial-anchors.md#best-practices) und positionieren das – Hologramm an seinem Ursprung.
Dadurch bleibt dieses Hologramm im Lauf der Zeit unabhängig.

### <a name="support-mixed-reality-capture"></a>Unterstützen der Erfassung gemischter Realität

Obwohl die primäre Anzeige von hololens 2 die Additive Umgebungs Mischung verwendet, wird der Renderinginhalt der APP mit dem Videodaten Strom der Umgebung in Alpha gemischt gemischt, wenn der Benutzer die [gemischte Reality-Erfassung](mixed-reality-capture-for-developers.md)initiiert.
Um die beste visuelle Qualität in gemischten Reality-Erfassungs Videos zu erzielen, empfiehlt es sich, die `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` im `layerFlags`der Projektionsebene festzulegen.

## <a name="best-practices-for-performance-on-hololens-2"></a>Bewährte Methoden für die Leistung in hololens 2

Als mobiles Gerät mit Unterstützung für die Hardware neuprojektion haben hololens 2 strengere Anforderungen, um eine optimale Leistung zu erzielen.  Es gibt eine Reihe von Möglichkeiten, Kompositions Daten über `xrEndFrame` zu senden, was zu einer Nachbearbeitung führt, die eine spürbare Leistungseinbußen verursachen wird.

### <a name="select-a-swapchain-format"></a>Wählen Sie ein vorhandenes SwapChain-Format aus.

Auflisten Sie die unterstützten Pixel Formate immer mithilfe von `xrEnumerateSwapchainFormats`, und wählen Sie das erste Farb-und tiefen Pixel Format aus der Laufzeit aus, die die App unterstützt, da die Common Language Runtime die optimale Leistung bevorzugt. Beachten Sie, dass bei hololens 2 `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` und `DXGI_FORMAT_D16_UNORM` in der Regel die erste Wahl ist, eine bessere Renderingleistung zu erzielen. Diese Einstellung kann sich auf einem Desktop-PC unterscheiden, der auf einem Desktop-PC ausgeführt wird, bei dem 24-Bit-Tiefen Puffer weniger Leistungseinbußen aufweisen.
  
**Leistungs Warnung:** Wenn Sie ein anderes Format als das primäre vorhandenes SwapChain-Farb Format verwenden, führt dies zur Laufzeit nach der Verarbeitung, was zu einer erheblichen Leistungs Einbuße führt.

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a>Rendern mit empfohlenen Renderingparametern und Frame zeitliche Steuerung

Rendern Sie immer mit der empfohlenen Ansichts Konfigurations Breite/-Höhe (`recommendedImageRectWidth` und `recommendedImageRectHeight` von `XrViewConfigurationView`), und verwenden Sie immer `xrLocateViews`-API, um die empfohlenen Ansichts-, FOV-und anderen Renderingparameter vor dem Rendering abzufragen.
Verwenden Sie beim Abfragen von Posen und Sichten immer die `XrFrameEndInfo.predictedDisplayTime` aus dem aktuellen `xrWaitFrame`-Aufrufs.
Dies ermöglicht hololens das Anpassen des Rendering und die Optimierung der visuellen Qualität für die Person, die die hololens trägt.

### <a name="use-a-single-projection-layer"></a>Verwenden einer einzelnen Projektions Schicht

Hololens 2 verfügt über eingeschränkte GPU-Leistung für Anwendungen zum Rendering von Inhalten und einen Hardware-Compositor, der für eine einzelne Projektions Schicht optimiert ist.
Immer eine einzelne Projektions Schicht zu verwenden, kann der Framerate der Anwendung, der – Hologramm-Stabilität und der visuellen Qualität helfen.  
  
**Leistungs Warnung:** Wenn Sie etwas anderes als eine einzelne Schutzschicht übermitteln, führt dies zur Laufzeit nach der Verarbeitung, was zu einer erheblichen Leistungs Einbuße führt.

### <a name="render-with-texture-array-and-vprt"></a>Mit Textur Array und VPRT Rendering

Erstellen Sie eine `xrSwapchain` sowohl für Links als auch für rechtsbündig, indem Sie `arraySize=2` für Color SwapChain und einen für die Tiefe verwenden.
Rendering Sie den linken Bereich in Slice 0 und das rechte Auge in Slice 1.
Verwenden Sie einen Shader mit VPRT und instanzierten Draw-aufrufen für das stereorenrendering zum Minimieren der GPU-Auslastung.
Dadurch wird auch die Optimierung der Laufzeit ermöglicht, um die beste Leistung für hololens 2 zu erzielen.
Alternativen zur Verwendung eines Textur Arrays, z. b. ein Double-Wide Rendering oder eine separate vorhandenes SwapChain pro Auge, führen zur Laufzeit nach der Verarbeitung, was zu einem erheblichen Leistungsabfall führt.

### <a name="avoid-quad-layers"></a>Vermeiden von vier Ebenen

Anstatt vier Ebenen als Kompositions Ebenen mit `XrCompositionLayerQuad`zu übermitteln, sollten Sie den Quad-Inhalt direkt in der Projektions-SwapChain-Darstellung ablegen.

**Leistungs Warnung:** Das Bereitstellen zusätzlicher Ebenen über eine einzelne Projektions Schicht, wie z. b. Quad-Ebenen, führt zur Laufzeit nach der Verarbeitung, was zu einer erheblichen Leistungs Einbuße führt.