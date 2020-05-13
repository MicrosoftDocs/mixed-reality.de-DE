---
title: OpenXR
description: Erstellen Sie eine Engine mithilfe des portablen openxr-API-Standards, und stellen Sie Sie für Windows Mixed Reality-und hololens 2-Headsets bereit.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: Openxr, Khronos, basicxrapp, DirectX, Native, Native APP, benutzerdefinierte Engine, Middleware
ms.openlocfilehash: 8263e530336d53020ebe35091426f0596f257805
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/12/2020
ms.locfileid: "83228035"
---
# <a name="openxr"></a>OpenXR

Openxr ist ein offener, kostenloser API-Standard von <a href="https://www.khronos.org/" target="_blank">Khronos</a> , der Modulen systemeigenen Zugriff auf eine große Bandbreite von Geräten von vielen Anbietern ermöglicht, die sich über das [gemischte Reality-Spektrum](mixed-reality.md)erstrecken.

Sie können auf dem Desktop mit openxr auf einem hololens 2-oder Windows Mixed Reality-immersiven Headset entwickeln.  Wenn Sie keinen Zugriff auf ein Headset haben, können Sie stattdessen den hololens 2-Emulator oder den Windows Mixed Reality-Simulator verwenden.

## <a name="why-openxr"></a>Gründe für openxr

Mit openxr können Sie Engines entwickeln, die sowohl auf Holographic-Geräte (wie hololens 2) abzielen, die digitale Inhalte in der realen Welt platzieren, als wären Sie tatsächlich vorhanden, als auch immersive Geräte (z. b. Windows Mixed Reality-Headsets für Desktop-PCs), die die physische Welt ausblenden und durch eine digitale Umgebung ersetzen.  Mit openxr können Sie Code einmal schreiben, der dann über eine große Bandbreite von Hardwareplattformen portabel ist.

Die openxr-API verwendet ein Lade Modul, das Ihre Anwendung direkt mit der nativen Platt Form Unterstützung Ihres Headsets verbindet.  Dies bietet Endbenutzern maximale Leistung und minimale Latenzzeit, unabhängig davon, ob Sie ein Windows Mixed Reality-Headset oder ein anderes Headset verwenden.

## <a name="what-is-openxr"></a>Was ist openxr?

Die openxr-API stellt die Kernfunktionen für Vorhersage, Frame Timing und räumliche Eingaben bereit, die Sie zum Erstellen eines Moduls benötigen, das sowohl Holographic-Geräte als auch hololens 2 und immersive Geräte wie Windows Mixed Reality-Headsets als Ziel hat.

Informationen zur openxr-API finden Sie in der openxr 1,0- <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Spezifikation</a>, der <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API-Referenz</a> und der <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">kurz Referenzanleitung</a>.  Weitere Informationen finden Sie auf der <a href="https://www.khronos.org/openxr/" target="_blank">Seite zu Khronos openxr</a>.

Um den vollständigen Feature-Satz von hololens 2 als Ziel festzulegen, verwenden Sie auch herstellerübergreifende und herstellerspezifische openxr-Erweiterungen, die über openxr 1,0 Core hinausgehende Features ermöglichen, wie z. b. die Nachverfolgung von Hand, die Augen Verfolgung, die räumliche Zuordnung und räumliche Anker.  Weitere Informationen zu den weiter unten in diesem Jahr anstehenden Erweiterungen finden Sie im nachfolgenden [Abschnitt Roadmap](#roadmap) .

Beachten Sie, dass openxr nicht selbst ein gemischtes Reality-Engine ist.  Stattdessen ermöglicht openxr Modulen wie Unity und Unreal das einmalige Schreiben von portablen Code, der dann auf die nativen Plattformfunktionen des Holographic-oder immersiven Geräts des Benutzers zugreifen kann, unabhängig davon, welcher Anbieter diese Plattform erstellt hat.

## <a name="roadmap"></a>Roadmap

Die openxr-Spezifikation definiert einen Erweiterungsmechanismus, mit dem Lauf Zeit Implementierungen zusätzliche Funktionen über die in der Basisversion von <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">openxr 1,0</a>definierten [Kernfunktionen](#what-is-openxr) hinaus verfügbar machen können.

Es gibt drei Arten von openxr-Erweiterungen:
* **Lieferanten Erweiterungen (z. b. `MSFT` ):** ermöglicht die herstellerspezifische Innovation in Hardware-oder Software Features.  Alle Lauf Zeit Hersteller können jederzeit eine Anbieter Erweiterung einführen und versenden.
  * **Experimentelle Lieferanten Erweiterungen (z. b. `MSFT_preview` ):** experimentelle Lieferanten Erweiterungen, die in der Vorschau angezeigt werden.  `MSFT_preview`Erweiterungen sind nur für Entwickler Geräte vorgesehen und werden entfernt, wenn die tatsächliche Erweiterung ausgeliefert wird.  Um mit Ihnen zu experimentieren, können Sie [Vorschau Erweiterungen auf Ihrem Entwickler Gerät aktivieren](openxr-getting-started.md#using-preview-extensions).
* **Anbieter übergreifende `EXT` Erweiterungen:** Anbieter übergreifende Erweiterungen, die von mehreren Unternehmen definiert und implementiert werden.  Gruppen von Interessen Unternehmen können jederzeit ext-Erweiterungen einführen.
* **Offizielle `KHR` Erweiterungen:** offizielle Khronos-Erweiterungen, die im Rahmen einer Core-Spezifikation-Version ratifiziert wurden.  KHR-Erweiterungen werden durch dieselbe Lizenz abgedeckt wie die Kern Spezifikation selbst.

Ab dem 2020 unterstützt die Windows Mixed Reality openxr-Laufzeit eine Reihe von `MSFT` -und- `EXT` Erweiterungen, die den vollständigen Satz von hololens 2-Funktionen zu openxr-Anwendungen bringen:

| Featurebereich | Verfügbarkeit der Erweiterung |
|--------------|------------------------|
| Systeme und Sitzungen | **Openxr 1,0 Core-Spezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [Verweis Plätze (Ansicht, lokal, Phase)](coordinate-systems.md) | **Openxr 1,0 Core-Spezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| Konfigurationen anzeigen (Mono, Stereo) | **Openxr 1,0 Core-Spezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [SwapChain](rendering.md)  +  [Frame zeitliche Steuerung](understanding-performance-for-mixed-reality.md) | **Openxr 1,0 Core-Spezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| Kompositions Ebenen<br />(Projektion, Quad) | **Openxr 1,0 Core-Spezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [Eingabe und Haptik](interaction-fundamentals.md) | **Openxr 1,0 Core-Spezifikation:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Integration von Direct3D 11 | **Offizielle `KHR` Erweiterung veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code> |
| Direct3D 12-Integration | **Offizielle `KHR` Erweiterung in [Preview Runtime 2003](openxr-getting-started.md#using-preview-extensions):**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code><br /><p>**Unterstützung in stabiler Laufzeit**: Mai 2020 *(geplant)*</p> |
| [Ungebundener Referenzraum <br /> (weltweit skalierbar)](coordinate-systems.md#building-a-world-scale-experience) | **`MSFT`Erweiterung veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [Raumanker](spatial-anchors.md) | **`MSFT`Erweiterung veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code> |
| [Hand Interaktion <br /> (Ziehpunkt/Ziel darstellen, Luft tippen, Reichweite)](hands-and-tools.md)<p>*Nur hololens 2*</p> | **`MSFT`Erweiterung veröffentlicht:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_interaction">XR_MSFT_hand_interaction</a></code> |
| [Handgelenke und Hand Mesh](hands-and-tools.md)<p>*Nur hololens 2*</p> | **`MSFT_preview`Erweiterungen in der [Vorschau Laufzeit 2001](openxr-getting-started.md#using-preview-extensions):**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_hand_tracking_preview">XR_MSFT_hand_tracking_preview</a></code><br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_hand_tracking_mesh_preview">XR_MSFT_hand_tracking_mesh_preview</a></code><p>** `MSFT` oder `EXT` Extension in Preview Runtime**: Mai 2020 *(geplant)*</p> |
| [Anvisieren mit den Augen](eye-tracking.md)<p>*Nur hololens 2*</p> | ** `EXT` Erweiterung in [Preview Runtime 2003](openxr-getting-started.md#using-preview-extensions)**:<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code><p>**Unterstützung in stabiler Laufzeit**: Mai 2020 *(geplant)*</p> |
| Interop mit anderen hololens-sdchen (z. b. [QR](qr-code-tracking.md))<p>*Nur hololens 2*</p> | **`MSFT_preview`Erweiterung in [Preview Runtime 2001](openxr-getting-started.md#using-preview-extensions):**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_spatial_graph_bridge_preview">XR_MSFT_spatial_graph_bridge_preview</a></code><p>** `MSFT` Erweiterung in der Vorschau Laufzeit**: Mai 2020 *(geplant)*</p> |
| [Transformation für gemischte Realität <br /> (drittes Rendering von PV-Kamera)](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*Nur hololens 2*</p> | **`MSFT_preview`Erweiterungen in der [Vorschau Laufzeit 2003](openxr-getting-started.md#using-preview-extensions):**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_secondary_view_configuration_preview">XR_MSFT_secondary_view_configuration_preview</a></code><br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_first_person_observer_preview">XR_MSFT_first_person_observer_preview</a></code><p>** `MSFT` Erweiterung in der Vorschau Laufzeit**: Juni 2020 *(geplant)*</p> |
| [Bewegungs Controller-Rendering-Modelle](motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT_preview`Erweiterung in [Preview Runtime 2003](openxr-getting-started.md#using-preview-extensions):**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_controller_model_preview">XR_MSFT_controller_model_preview</a></code><p>** `MSFT` Erweiterung in der Vorschau Laufzeit**: Juli 2020 *(geplant)*</p> |
| [Szenen Verständnis (Flächen, Netze)](scene-understanding.md)<p>*Nur hololens 2*</p> | <p>** `MSFT_preview` Erweiterung in der Vorschau Laufzeit**: Juni 2020 *(geplant)*</p><p>** `MSFT` Erweiterung in der Vorschau Laufzeit**: Juli 2020 *(geplant)*</p> |
| Weitere herstellerübergreifende Erweiterungen | <p>**Offizielle `KHR` Erweiterungen veröffentlicht:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><p>**`EXT`veröffentlichte Erweiterungen:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code> |

Während einige dieser Erweiterungen als anbieterspezifische Erweiterungen gestartet werden können `MSFT` , arbeiten Microsoft und andere openxr-Lauf Zeit Anbieter zusammen, um Anbieter übergreifende Erweiterungen `EXT` oder `KHR` Erweiterungen für viele dieser Featurebereiche zu entwerfen.  Dadurch kann der Code, den Sie für diese Funktionen schreiben, über Lauf Zeit Anbieter hinweg portabel sein, ebenso wie bei der Kern Spezifikation.

## <a name="get-started-with-openxr"></a>Einstieg in openxr

Sie können auf dem Desktop mit openxr auf einem hololens 2-oder Windows Mixed Reality-immersiven Headset entwickeln.  Wenn Sie keinen Zugriff auf ein Headset haben, können Sie stattdessen den hololens 2-Emulator oder den Windows Mixed Reality-Simulator verwenden.

Informationen zum Einstieg in die Entwicklung von openxr-Anwendungen für hololens 2 oder immersive Windows Mixed Reality-Headsets finden Sie unter Erste Schritte [mit der openxr-Entwicklung](openxr-getting-started.md).

## <a name="see-also"></a>Siehe auch

* <a href="https://www.khronos.org/openxr/" target="_blank">Weitere Informationen zu openxr</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Openxr 1,0-Spezifikation</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">Openxr 1,0-API-Referenz</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Openxr 1,0 kurz Referenzhandbuch</a>
