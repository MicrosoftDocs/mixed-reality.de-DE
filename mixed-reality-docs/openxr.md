---
title: Openxr
description: Erstellen Sie eine Engine mithilfe des portablen openxr-API-Standards, und stellen Sie Sie für Windows Mixed Reality-und hololens 2-Headsets bereit.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: Openxr, Khronos, basicxrapp, gemischte Realität openxr-Entwickler Portal, DirectX, Native, Native App Custom-Engine, Middleware
ms.openlocfilehash: 67d2ab42a40aa04eb9dcd6881a4392a81c0f3b8f
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2019
ms.locfileid: "73914395"
---
# <a name="openxr"></a>Openxr

Openxr ist ein offener, kostenloser API-Standard von <a href="https://www.khronos.org/" target="_blank">Khronos</a> , der Modulen systemeigenen Zugriff auf eine große Bandbreite von Geräten von vielen Anbietern ermöglicht, die sich über das [gemischte Reality-Spektrum](mixed-reality.md)erstrecken.

Sie können auf dem Desktop mit openxr auf einem hololens 2-oder Windows Mixed Reality-immersiven Headset entwickeln.  Wenn Sie keinen Zugriff auf ein Headset haben, können Sie stattdessen den hololens 2-Emulator oder den Windows Mixed Reality-Simulator verwenden.

## <a name="why-openxr"></a>Gründe für openxr

Mit openxr können Sie Engines entwickeln, die sowohl auf Holographic-Geräte (wie hololens 2) abzielen, die digitale Inhalte in der realen Welt platzieren, als wären Sie tatsächlich vorhanden, als auch immersive Geräte (z. b. Windows Mixed Reality-Headsets für Desktop-PCs), die die physische und ersetzen Sie Sie durch eine digitale Umgebung.  Mit openxr können Sie Code einmal schreiben, der dann über eine große Bandbreite von Hardwareplattformen portabel ist.

Die openxr-API verwendet ein Lade Modul, das Ihre Anwendung direkt mit der nativen Platt Form Unterstützung Ihres Headsets verbindet.  Dies bietet Endbenutzern maximale Leistung und minimale Latenzzeit, unabhängig davon, ob Sie ein Windows Mixed Reality-Headset oder ein anderes Headset verwenden.

## <a name="what-is-openxr"></a>Was ist openxr?

Die zentrale openxr 1,0-API bietet die Basisfunktionalität, die Sie zum Erstellen eines Moduls benötigen, das sowohl auf Holographic-Geräte als auch auf hololens 2 und immersive Geräte wie Windows Mixed Reality-Headsets ausgerichtet ist:
* Systeme und Sitzungen
* Verweis Plätze (Ansicht, lokal, Phase)
* Konfigurationen anzeigen (Mono, Stereo)
* SwapChain + Frame zeitliche Steuerung
* Kompositions Ebenen
* Eingabe und Haptik
* Grafik-API + Platt Form Integration

Informationen zur openxr-API finden Sie in der openxr 1,0- <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Spezifikation</a>, der <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API-Referenz</a> und der <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">kurz Referenzanleitung</a>.  Weitere Informationen finden Sie auf der <a href="https://www.khronos.org/openxr/" target="_blank">Seite zu Khronos openxr</a>.

Um den vollständigen Feature-Satz von hololens 2 als Ziel festzulegen, verwenden Sie auch herstellerübergreifende und herstellerspezifische openxr-Erweiterungen, die über openxr 1,0 Core hinausgehende Features ermöglichen, wie z. b. die Nachverfolgung von Hand, die Augen Verfolgung, die räumliche Zuordnung und räumliche Anker.  Weitere Informationen zu den weiter unten in diesem Jahr anstehenden Erweiterungen finden Sie im Abschnitt " [Roadmap](openxr.md#roadmap) " weiter unten.

Beachten Sie, dass openxr nicht selbst ein gemischtes Reality-Engine ist.  Stattdessen ermöglicht openxr Modulen wie Unity und Unreal das einmalige Schreiben von portablen Code, der dann auf die nativen Plattformfunktionen des Holographic-oder immersiven Geräts des Benutzers zugreifen kann, unabhängig davon, welcher Anbieter diese Plattform erstellt hat.

## <a name="getting-started-with-openxr-for-hololens-2"></a>Getting Started with openxr for hololens 2

So beginnen Sie mit der Entwicklung von openxr-Anwendungen für hololens 2:

1. Richten Sie einen hololens 2 ein, oder befolgen Sie die Anweisungen zum [Installieren des hololens 2-Emulators](using-the-hololens-emulator.md).
1. Starten Sie die Store-App innerhalb des Geräts oder Emulators, und stellen Sie sicher, dass alle apps aktualisiert werden.  Dadurch wird sichergestellt, dass die openxr-Laufzeit auf Ihren hololens auf openxr 1,0 aktualisiert wird.  Wenn Sie den Emulator verwenden, sollten Sie sich die [Emulator-Eingabe Anweisungen](using-the-hololens-emulator.md#basic-emulator-input) ansehen, damit Sie die Store-App im Emulator verwenden können.

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Einstieg in openxr für Windows Mixed Reality-Headsets

So beginnen Sie mit der Entwicklung von openxr-Anwendungen für immersive Windows Mixed Reality-Headsets:

1. Stellen Sie sicher, dass Sie das Windows 10-Update "Mai 2019" (1903) ausführen. Dies ist die Mindestanforderung für Endbenutzer von Windows Mixed Reality, openxr-Anwendungen auszuführen.  Wenn Sie eine frühere Version von Windows 10 verwenden, können Sie mit dem <a href="https://www.microsoft.com//software-download/windows10" target="_blank">Windows 10 Update Assistant</a>ein Upgrade auf das Update von Mai 2019 durchführen.  Wenn Sie Ihren PC nicht aktualisieren können, ist es auch möglich, [die openxr-App mit dem Windows 10-Update vom Oktober 2018 (1809) zu entwickeln](openxr.md#developing-on-windows-10-october-2018-update), obwohl möglicherweise niedrigere Leistungs-oder andere Probleme auftreten.
2. Richten Sie ein Windows Mixed Reality-Headset ein, oder befolgen Sie die Anweisungen zum [Aktivieren des Windows Mixed Reality-Simulators](using-the-windows-mixed-reality-simulator.md).  Nach dem Einrichten von Windows Mixed Reality wird die Windows Mixed Reality openxr-Laufzeit automatisch von Mixed Reality Portal installiert.  Der Microsoft Store behält die Laufzeit dann bei.
3. Aktivieren Sie die Windows Mixed Reality openxr-Laufzeit, indem Sie das gemischte Reality-Portal im Startmenü starten und dann auf die Schaltfläche... unten links, und wählen Sie "openxr einrichten".<br>
![Einrichten von openxr im Mixed Reality-Portal](images/mixed-reality-portal-set-up-openxr.png)

Wenn Sie die Windows Mixed Reality-openxr-Laufzeit erneut aktivieren müssen, wiederholen Sie Schritt 3.

> [!NOTE]
> Die Windows Mixed Reality openxr-Laufzeit wird in Kürze automatisch für alle Windows Mixed Reality-Endbenutzer eingerichtet.

## <a name="getting-the-mixed-reality-openxr-developer-portal"></a>Holen Sie sich das Entwickler Portal für gemischte Realität openxr

Um die Windows Mixed Reality openxr-Laufzeit auszuprobieren, können Sie die <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">[gemischte Realität openxr-Entwickler Portal-App</a>installieren.  Diese APP bietet eine Demo Szene, die verschiedene Features von openxr sowie eine Seite mit dem System Status ausführt, die wichtige Informationen zur aktiven Laufzeit und zum aktuellen Headset bereitstellt.

![Gemischte Realität openxr-Entwickler Portal-App](images/mixed-reality-openxr-developer-portal.png)

## <a name="building-a-sample-openxr-app"></a>Aufbauen einer openxr-Beispiel-App

Das <a href="https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp" target="_blank">basicxrapp</a> -Projekt veranschaulicht ein einfaches openxr-Beispiel mit zwei Visual Studio-Projektdateien, eines für eine Win32-Desktop-App und eines für eine UWP hololens 2-App.  Da die Projekt Mappe ein hololens-UWP-Projekt enthält, benötigen Sie die [Arbeitsauslastung der universelle Windows-Plattform Entwicklung](install-the-tools.md#installation-checklist) , die in Visual Studio installiert ist, um Sie vollständig zu öffnen.

Beachten Sie Folgendes: während die Win32-und UWP-Projektdateien aufgrund von Unterschieden bei der Paket Erstellung und Bereitstellung getrennt sind, ist der app-Code in jedem Projekt 100% identisch.

## <a name="openxr-app-best-practices-for-hololens-2"></a>Bewährte Methoden für openxr-Apps für hololens 2

Ein Beispiel für die unten aufgeführten bewährten Methoden finden Sie in der Datei " [openxrprogram. cpp](https://github.com/microsoft/OpenXR-SDK-VisualStudio/blob/master/samples/BasicXrApp/OpenXrProgram.cpp) " von basicxrapp. Die Run ()-Funktion am Anfang erfasst einen typischen openxr-App-Codefluss von der Initialisierung zur Ereignis-und Renderingschleife.

### <a name="select-a-pixel-format"></a>Pixel Format auswählen

Listet die unterstützten Pixel Formate immer mit `xrEnumerateSwapchainFormats`auf und wählt das erste Farb-und tiefen Pixel Format aus der Laufzeit aus, die von der App unterstützt wird, da dies von der Common Language Runtime bevorzugt wird. Beachten Sie, dass bei hololens 2 `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` und `DXGI_FORMAT_D16_UNORM` in der Regel die erste Wahl ist, eine bessere Renderingleistung zu erzielen. Diese Einstellung kann sich auf der Ausführung von VR-Headsets auf einem Desktop-PC unterscheiden.  
  
**Leistungs Warnung:** Wenn Sie ein anderes Format als das primäre vorhandenes SwapChain-Farb Format verwenden, führt dies zur Laufzeit nach der Verarbeitung, was zu einer erheblichen Leistungs Einbuße führt.

### <a name="gamma-correct-rendering"></a>Gamma-korrektes Rendering

Obwohl dies für alle openxr-Runtimes gilt, muss sorgfältig vorgegangen werden, um sicherzustellen, dass die Renderingpipeline Gamma-correct ist. Beim Rendern in eine vorhandenes SwapChain sollte das Renderziel-Ansichts Format dem vorhandenes SwapChain-Format entsprechen (z. b. DXGI_FORMAT_B8G8R8A8_UNORM_SRGB für das vorhandenes SwapChain-Format und die renderzielansicht).
Eine Ausnahme ist, wenn die Renderingpipeline der App eine manuelle sRGB-Konvertierung in Shader-Code durchführt. in diesem Fall sollte die APP ein sRGB-vorhandenes SwapChain-Format anfordern, aber das lineare Format für die renderzielansicht verwenden (z. b. Anforderungs DXGI_FORMAT_B8G8R8A8_UNORM_SRGB als Das vorhandenes SwapChain-Format, jedoch DXGI_FORMAT_B8G8R8A8_UNORM als renderzielansicht), um zu verhindern, dass Inhalt doppelt korrigiert wird.

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

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a>Rendern mit empfohlenen Renderingparametern und Frame zeitliche Steuerung

Rendern Sie immer mit der empfohlenen Ansichts Konfigurations Breite/-Höhe (`recommendedImageRectWidth` und `recommendedImageRectHeight` von `XrViewConfigurationView`), und verwenden Sie immer `xrLocateViews`-API, um die empfohlenen Ansichts-, FOV-und anderen Renderingparameter vor dem Rendering abzufragen.
Verwenden Sie beim Abfragen von Posen und Sichten immer die `XrFrameEndInfo.predictedDisplayTime` aus dem aktuellen `xrWaitFrame`-Aufrufs.
Dies ermöglicht hololens das Anpassen des Rendering und die Optimierung der visuellen Qualität für die Person, die die hololens trägt.

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

**Leistungs Warnung:** Wenn das `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT`-Flag auf der einzelnen Projektionsebene weggelassen wird, führt dies zur Laufzeit nach der Verarbeitung, was zu einer erheblichen Leistungs Einbuße führt.

### <a name="avoid-quad-layers"></a>Vermeiden von vier Ebenen

Anstatt vier Ebenen als Kompositions Ebenen mit `XrCompositionLayerQuad`zu übermitteln, sollten Sie den Quad-Inhalt direkt in der Projektions-SwapChain-Darstellung ablegen.

**Leistungs Warnung:** Das Bereitstellen zusätzlicher Ebenen über eine einzelne Projektions Schicht, wie z. b. Quad-Ebenen, führt zur Laufzeit nach der Verarbeitung, was zu einer erheblichen Leistungs Einbuße führt.

## <a name="openxr-app-performance-on-hololens-2"></a>Openxr-App-Leistung auf hololens 2

Auf hololens 2 gibt es eine Reihe von Möglichkeiten, Kompositions Daten über `xrEndFrame` zu senden, was zu einer Nachbearbeitung führt, die eine spürbare Leistungs Einbuße verursachen wird.
Um Leistungsdaten zu vermeiden, [Senden Sie eine einzelne `XrCompositionProjectionLayer`](#use-a-single-projection-layer) mit den folgenden Merkmalen:
* [Verwenden eines Textur Arrays vorhandenes SwapChain](#render-with-texture-array-and-vprt)
* [Verwenden des Haupt Farb-vorhandenes SwapChain-Formats](#select-a-pixel-format)
* [Festlegen des Texture-Source-Alpha-Mischungs Flags](#support-mixed-reality-capture)
* [Empfohlene Anzeige Dimensionen verwenden](#render-with-recommended-rendering-parameters-and-frame-timing)
* Legen Sie das `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT`-Flag nicht fest.
* Legen Sie den `XrCompositionLayerDepthInfoKHR` `minDepth` auf 0,0 f fest, und `maxDepth` auf 1.0 f.

Weitere Überlegungen führen zu einer besseren Leistung:
* [Verwenden des 16-Bit-Tiefen Formats](#choose-a-reasonable-depth-range)
* [Erstellen von instanziierten zeichnen-aufrufen](#render-with-texture-array-and-vprt)

## <a name="roadmap"></a>Roadmap

Die openxr-Spezifikation definiert einen Erweiterungsmechanismus, mit dem Lauf Zeit Implementierungen zusätzliche Funktionen über die in der Basisversion von <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">openxr 1,0</a>definierten [Kernfunktionen](openxr.md#what-is-openxr) hinaus verfügbar machen können.

Es gibt drei Arten von openxr-Erweiterungen:
* **Lieferanten Erweiterungen (z. b. msft):** Ermöglicht die herstellerspezifische Innovation in Hardware-oder Software Features.  Alle Lauf Zeit Hersteller können jederzeit eine Anbieter Erweiterung einführen und versenden.
* **Ext-Erweiterungen:** Anbieter übergreifende Erweiterungen, die von mehreren Unternehmen definiert und implementiert werden.  Gruppen von Interessen Unternehmen können jederzeit ext-Erweiterungen einführen.
* **KHR-Erweiterungen:** Offizielle Khronos-Erweiterungen, die im Rahmen einer Core-Spezifikation-Version ratifiziert wurden.  KHR-Erweiterungen werden durch dieselbe Lizenz abgedeckt wie die Kern Spezifikation selbst.

Am Ende des Jahres unterstützt die openxr-Laufzeit von Windows Mixed Reality einen Satz von msft-und ext-Erweiterungen, die den vollständigen Satz von hololens 2-Funktionen zu openxr-Anwendungen bringen:
* [Ungebundener Referenzraum (weltweit skalierbar)](coordinate-systems.md#building-a-world-scale-experience)
* [Räumliche Anker und Speicher](spatial-anchors.md)
* [Handgelenke und Hand Mesh](hands-and-tools.md)
* [Anvisieren mit den Augen](eye-tracking.md)
* [Sekundäre Ansichts Konfigurationen (Mixed Reality Capture)](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)
* [Grundlegendes zu Szenen](scene-understanding.md)
* Interop mit Windows SDK-APIs

Während einige dieser Erweiterungen als anbieterspezifische MSFT-Erweiterungen gestartet werden können, arbeiten Microsoft und andere openxr-Lauf Zeit Anbieter zusammen, um Anbieter übergreifende ext-oder KHR-Erweiterungen für viele dieser Featurebereiche zu entwerfen.  Dadurch kann der Code, den Sie für diese Funktionen schreiben, über Lauf Zeit Anbieter hinweg portabel sein, ebenso wie bei der Kern Spezifikation.

## <a name="troubleshooting"></a>Fehlerbehebung

Im folgenden finden Sie einige Tipps zur Problembehandlung für die Windows Mixed Reality openxr-Laufzeit.  Wenn Sie weitere Fragen zur <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">openxr 1,0-Spezifikation</a>haben, besuchen Sie die <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos openxr-Foren</a> oder <a href="https://khr.io/slack" target="_blank">Slack #openxr Channel</a>.

### <a name="developing-on-windows-10-october-2018-update"></a>Entwickeln unter Windows 10 Oktober 2018-Update

Wenn Sie [ihren Entwicklungs-PC nicht auf das Update von Mai 2019 aktualisieren](https://www.microsoft.com//software-download/windows10)können, können Sie den Windows 10-Computer vom Oktober 2018 Update (1809) für die Entwicklung einrichten, indem Sie einen weiteren Schritt ausführen:

1. Führen Sie die obigen Schritte aus, um mit openxr auf Ihrem Desktop-PC zu beginnen.
1. Um die openxr-Laufzeit von Windows Mixed Reality als aktive openxr-Laufzeit Ihres Systems festzulegen, installieren Sie das [Windows Mixed Reality openxr Developer Compatibility Pack](https://aka.ms/openxr-compat).

> [!NOTE]
> Obwohl Windows 10 Oktober 2018 Update (1809) für die Entwicklung von openxr-Anwendungen verwendet werden kann, ist das Windows 10-Update von Mai 2019 (1903) die Mindestanforderung für Endbenutzer, openxr mit Windows Mixed Reality zu verwenden.  Beim Ausführen der openxr-App im Oktober 2018-Update treten möglicherweise niedrigere Leistungs-oder andere Probleme auf.  Es wird dringend empfohlen, dass Sie Ihr Entwicklungs-PC auf das Windows 10-Update vom Mai 2019 (1903) aktualisieren.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>Openxr-App startet nicht Windows Mixed Reality

Wenn Ihre openxr-APP nicht Windows Mixed Reality startet, wenn Sie Sie ausführen, kann die openxr-Laufzeit von Windows Mixed Reality nicht als aktive Laufzeit festgelegt werden.  Befolgen Sie die obigen Anweisungen für den [Einstieg in openxr für Windows Mixed Reality-Headsets](#getting-started-with-openxr-for-windows-mixed-reality-headsets) , um die Laufzeit zu aktivieren.

Sie können das [Entwickler Portal für gemischte Realität](#getting-the-mixed-reality-openxr-developer-portal) auch ausführen, um zusätzliche Hilfe zur Problembehandlung im Zusammenhang mit dem Status der Windows Mixed Reality openxr-Laufzeit auf Ihrem System zu erhalten.

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a>Das gemischte Reality-Portal zeigt das Menü Element "Set up openxr" nicht an.

Stellen Sie sicher, dass mindestens das Windows 10-Update vom Oktober 2018 (1809) ausgeführt wird.  Wenn Sie eine frühere Version von Windows 10 verwenden, können Sie mit dem [Windows 10 Update Assistant](https://www.microsoft.com//software-download/windows10)auf das Update von Mai 2019 (1903) aktualisieren.

Das Menü Element "Einrichten von openxr" ist möglicherweise nicht verfügbar, wenn Sie eine ältere Version der Mixed Reality-Portal-APP haben.  [Überprüfen Sie, ob](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m) Sie über die neueste Version verfügen.

Beachten Sie, dass das Menü Element "Set up openxr" nicht angezeigt wird, wenn die Windows Mixed Reality openxr-Laufzeit bereits installiert und aktiv ist.  Sie können das [gemischte openxr-Entwickler Portal](#getting-the-mixed-reality-openxr-developer-portal) installieren, um den aktuellen Status der openxr-Laufzeit auf Ihrem System zu ermitteln.

## <a name="see-also"></a>Weitere Informationen:

* <a href="https://www.khronos.org/openxr/" target="_blank">Weitere Informationen zu openxr</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Openxr 1,0-Spezifikation</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">Openxr 1,0-API-Referenz</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Openxr 1,0 kurz Referenzhandbuch</a>
