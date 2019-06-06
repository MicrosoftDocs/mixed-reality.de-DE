---
title: Erstellen von 3D-Modellen für die Verwendung zu Hause
description: Asset-Anforderungen, und erstellen die Anleitungen für 3D-Modelle, die in die Windows Mixed Reality home HoloLens sowohl für immersive Headsets von (VR) verwendet werden.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: 3D, Modellierung, Modellieren von Anleitungen, Asset-Anforderungen, Erstellen von Richtlinien, Startprogramm, 3D Startprogramm, Textur, Materialien, Komplexität, Dreiecke, Netz, Polygone, Polycount, beschränkt.
ms.openlocfilehash: 73af40cf2915742cab612625c8243a36ee74d748
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692285"
---
# <a name="create-3d-models-for-use-in-the-home"></a>Erstellen von 3D-Modellen für die Verwendung zu Hause

Die [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) ist der Ausgangspunkt, in denen Benutzer weitergeleitet, vor dem Starten von Anwendungen. Sie können Ihre Anwendung für Windows Mixed Reality-Headsets nutzen entwerfen eine [3D-Modellen als eine app-Startfeld](implementing-3d-app-launchers.md) und ermöglichen [3D deep-Links in der Windows Mixed Reality home platziert werden](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles) aus in Ihrer app. Dieser Artikel beschreibt die Richtlinien zum Erstellen von 3D-Modellen mit der Windows Mixed Reality home kompatibel.

## <a name="asset-requirements-overview"></a>Übersicht über Asset-Anforderungen
Beim Erstellen von 3D-Modellen für Windows Mixed Reality gibt es einige Anforderungen, die alle Ressourcen erfüllen muss: 
1. [Exportieren von](#exporting-models) -Objekte im .glb-Dateiformat (binäre GlTF) übermittelt werden müssen.
2. [Modellieren von](#modeling-guidelines) -Ressourcen muss weniger als 10 KB Dreiecke, und haben nicht mehr als 64 Knoten und 32 Submeshes pro LOD
3. [Materialien](#material-guidelines) – Texturen darf nicht größer als 4096 x 4096 und die kleinste mip-Zuordnung sollte nicht größer als 4 auf entweder Dimension
4. [Animation](#animation-guidelines) -Animationen sind nicht mehr als 20 Minuten unter 30 BpS (36.000 Keyframes) sein und darf < = 8192 Morph Ziel Vertices
5. [Optimieren von](#optimizations) -Assets mit optimiert werden sollen die [WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases). Dies ist **auf Windows-Betriebssystemversionen erforderlich, < = 1709** und empfohlen, die auf Windows-Betriebssystemversionen > = 1803

Im weiteren Verlauf dieses Artikels enthält einen ausführlichen Überblick über diese Anforderungen als auch zusätzliche Richtlinien stellen Sie sicher, dass Ihre Modelle auch für die Windows Mixed Reality home geeignet. 

## <a name="detailed-guidance"></a>Ausführliche Anweisungen

### <a name="exporting-models"></a>Exportieren von Modellen

Die Windows Mixed Reality home erwartet 3D-Objekten, verwenden das Dateiformat .glb mit eingebetteten Bildern und binären Daten übermittelt werden soll. GLB ist die binäre Version des Formats GlTF die ist eine lizenzgebührenfreie kostenlose offener Standard für 3D medienobjektübermittlung, die von der Gruppe "Khronos" verwaltet wird. Weiterentwicklung von GlTF als Branchenstandard für interoperable 3D-Inhalt werden Sie also Microsoft Unterstützung für das Format für Windows-apps und-Umgebungen. Wenn Sie ein Medienobjekt GlTF erstellt haben, bevor Sie finden eine [Liste der unterstützten metadatenexport- und Konverter](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) auf der Github-Seite von GlTF arbeiten Gruppe.  

### <a name="modeling-guidelines"></a>Modellieren von Richtlinien

Windows erwartet, dass Ressourcen für die folgenden Richtlinien für die Modellierung zur Sicherstellung der Kompatibilität mit der Startseite Mixed Reality-Erfahrung mit generiert werden. Bedenken Sie beim Erstellen von Modellen in Ihrem Programm Ihrer Wahl die folgenden Empfehlungen und Einschränkungen:
1. Die Achse auf sollte auf "Y" festgelegt werden.
2. Das Medienobjekt sollte "forward" auf der positiven Z-Achse auftreten.
3. Alle Medienobjekte sollten auf der Grundebene auf den szenenursprung (0,0,0) erstellt werden
4. Arbeitseinheiten sollte auf Verbrauchseinheiten und Ressourcen festgelegt werden, sodass Welt skalierte Objekte erstellt werden können
5. Alle Gitter müssen nicht kombiniert werden, aber es wird empfohlen, wenn Sie Geräte mit eingeschränkten Ressourcen verwenden möchten
6. Alle Gitter freigeben 1 Material, mit nur 1 Textur, die für das gesamte Objekt verwendet wird
7. UVs müssen in einer quadratischen Anordnung in der 0-1 angeordnet werden Leerzeichen. Vermeiden Sie Tiling Texturen, obwohl sie zulässig sind.
8. Multi-UVs werden nicht unterstützt.
9. Doppelte zweiseitig Materialien werden nicht unterstützt.

### <a name="triangle-counts-and-levels-of-detail-lods"></a>Dreieck-Anzahl und Detailebenen (LODs)

Die Windows Mixed Reality home unterstützt keine Modelle mit mehr als 10.000 Dreiecke. Es wird empfohlen, dass Sie Ihre Gitter Triangulieren Sie vor dem exportieren, um sicherzustellen, dass sie nicht diese Anzahl überschritten werden. Windows-MR unterstützt auch optionale Geometrie Detailebenen (LODs) um sicherzustellen, dass eine leistungsfähige und qualitativ hochwertige benutzerfreundlichkeit. [Die WindowsMRAssetConverter](https://github.com/Microsoft/glTF-Toolkit/releases) können Sie die 3 Versionen des Modells in einem einzelnen .glb-Modell zu kombinieren. Windows bestimmt die LOD zum Anzeigen auf der Menge Bildschirmplatz basieren, die das Modell und verbraucht wird. Nur 3 LOD Ebenen werden durch den folgenden unterstützt Dreieck Anzahl empfohlen:
<br>

|  LOD-Ebene  |  Empfohlene Anzahl von Dreieck  |  Maximale Anzahl von Dreieck | 
|------|------|------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5,000  |  10,000 | 
|  LOD 2 |  2,500  |  10,000 | 

### <a name="node-counts-and-submesh-limits"></a>Anzahl von Knoten und Submesh-Grenzwerte
Die Windows Mixed Reality home unterstützt keine Modelle mit mehr als 64 Knoten oder 32 Submeshes pro LOD. Knoten sind ein Konzept in der [GlTF Spezifikation](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy) , definieren die Objekte in der Szene. Submeshes werden definiert, in dem Array [primitive](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes) auf das Netz im-Objekt. 

|  Feature |  Beschreibung  |  Max. unterstützt | Dokumentation |
|------|------|------|------|
|  Knoten |  Objekte in der Szene glTF |  64 pro LOD | [Hier](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  Submeshes |  Summe von primitiven Typen, auf alle Gitter |  32 pro LOD | [Hier](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>Material-Richtlinien

Texturen sollten mithilfe eines PBR-Metal-Rauigkeit Workflows darauf vorbereitet sein. Erstellen einen vollständigen Satz von Texturen, einschließlich Albedo, Normal, verdecken, Metallic und Rauigkeit zunächst. Windows Mixed Reality-unterstützt-Texturen mit Lösungen, die auf 4096 x 4096, aber es wird empfohlen, erstellen Sie zunächst 512 x 512 einrichten. Außerdem sollten Texturen in Auflösungen in Vielfachen von 4 erstellt werden, da dies eine Voraussetzung für das Komprimierungsformat auf Texturen in den Export von Schritten, die unten beschriebenen angewendet ist. Schließlich Wenn MipMaps Gerating oder einer Struktur der niedrigsten mip maximal 4 x 4 sein muss.
<br>

|  Empfohlene Texturgröße  |  Maximale Texturgröße | Niedrigste Mip
|----|----|----|
|  512x512  |  4096x4096 | Max. 4 x 4|

### <a name="albedo-base-color-map"></a>Zuordnung von Albedo (Basis Farbe)

Unformatierte Farbe ohne Beleuchtung-Informationen. Diese Zuordnung enthält außerdem die Reflexionsvermögen und diffusen Informationen für die-Metal-Computern (in der metallic Zuordnung weiß) und Isolierung (Schwarz auf der Karte metallic) Flächen bzw.

### <a name="normal"></a>Normal

Tangenten Speicherplatz Normal-Karte

### <a name="roughness-map"></a>Rauigkeit-Karte

Beschreibt die Microsurface des Objekts an. Whitepaper 1.0 ist ein Ungefährer Schwarz 0,0 ist. Diese Zuordnung gibt die Ressource, die die Zeichen, wie sie wirklich die Oberfläche beschreibt, z. B. ein kleiner Teil dessen, Fingerabdrücke, Flecken, Grime usw. an.

### <a name="ambient-occlusion-map"></a>Verdecken von Ambient-Karte

Wertzuordnung Skalierung mit Bereichen okkludierte Licht die Reflexionen blockiert

### <a name="metallic-map"></a>Metallic Zuordnung

Weist dem Shader an, ob etwas-Metal-Computern ist. RAW-Metal-= 1,0 weiß nicht Metall = 0,0 Schwarz. Povolena transitional grauen Werte, die für den raw-Metal-Computern wie z. B. wurde angeben, aber im Allgemeinen muss diese Zuordnung nur Schwarz und weiß.

## <a name="optimizations"></a>Optimierungen

Windows Mixed Reality private bietet eine Reihe von Optimierungen, die zusätzlich zu den Core GlTF-Spezifikation, die mithilfe der benutzerdefinierter Erweiterungen definiert. Diese Optimierungen sind erforderlich, auf Windows-Versionen < = 1709 und auf neuere Versionen von Windows empfohlen. Können Sie leicht optimieren jeder GlTF 2.0-Modell mithilfe der [Windows Mixed Reality Asset-Konverter auf GitHub verfügbar](https://github.com/Microsoft/glTF-Toolkit/releases). Dieses Tool führt die richtige Textur Packen und Optimierungen, wie unten beschrieben. Für die allgemeine Nutzung empfiehlt sich die WindowsMRAssetConverter, aber wenn Sie mehr Kontrolle über die Benutzeroberfläche benötigen, und Ihre eigene Pipeline für die Systemkonfiguration erstellen möchten dann sehen Sie sich die ausführliche Spezifikation unten.  

### <a name="materials"></a>Materialien

Zur Verbesserung der Ladezeit in Mixed Reality-Umgebungen Windows MR Asset unterstützt das Rendern von komprimierter DDS-Texturen, die gemäß der Textur, die in diesem Abschnitt definierten Schema Packen gepackt. DDS-Texturen sind verweisen, indem Sie die [MSFT_texture_dds Erweiterung](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds). Komprimieren von Strukturen wird dringend empfohlen. 

#### <a name="hololens"></a>HoloLens

Mixed Reality HoloLens-basierten Umgebungen erwarten, dass Texturen mit einem 2-Textur-Setup mithilfe der folgenden Spezifikation der Verpackung gepackt werden:
<br>

|  GlTF-Eigenschaft  |  Textur  |  Packen von Metriken-Schema | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Rot (R), Grün (G), Blau (B) | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalRoughnessMetallicTexture  |  Normal (RG), Rauigkeit (B) Metallic (A) | 


Wenn die DDS-Texturen zu komprimieren muss die folgende Komprimierung auf jeder Karte:
<br>

|  Textur  |  Erwartete Komprimierung | 
|------|------|
|  baseColorTexture, normalRoughnessMetallicTexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>Immersive Headsets von (VR)

PC-basierter Windows Mixed Reality-Erfahrungen für immersive Headsets von (VR) erwarten, dass Texturen mit einem 3-Textur-Setup mithilfe der folgenden Spezifikation der Verpackung gepackt werden:

##### <a name="windows-os--1803"></a>Windows OS >= 1803

<br>

|  GlTF-Eigenschaft  |  Textur  |  Packen von Metriken-Schema | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Rot (R), Grün (G), Blau (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  occlusionRoughnessMetallicTexture  |  Occlusion (R), Rauigkeit (G), Metallic (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normal (RG) | 

Wenn die DDS-Texturen zu komprimieren muss die folgende Komprimierung auf jeder Karte:
<br>

|  Textur  |  Erwartete Komprimierung | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, occlusionRoughnessMetallicTexture  |  BC7 | 

##### <a name="windows-os--1709"></a>Windows OS <= 1709
<br>

|  GlTF-Eigenschaft  |  Textur  |  Packen von Metriken-Schema | 
|----------|----------|----------|
|  pbrMetallicRoughness  |  baseColorTexture  |  Rot (R), Grün (G), Blau (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessMetallicOcclusionTexture  |  Roughness (R), Metallic (G), verdecken (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normalTexture  |  Normal (RG) | 

Wenn die DDS-Texturen zu komprimieren muss die folgende Komprimierung auf jeder Karte:
<br>

|  Textur  |  Erwartete Komprimierung | 
|------|------|
|  normalTexture  |  BC5 | 
|  baseColorTexture, roughnessMetallicOcclusionTexture | BC7 |

### <a name="adding-mesh-lods"></a>Hinzufügen von Mesh LODs

Windows-MR verwendet Geometrie-Knoten LODs zum Rendern von 3D-Modellen in verschiedenen Ausführlichkeitsgraden je nach Bildschirm-Abdeckung. Während dieses Feature technisch nicht erforderlich ist, wird für alle Medienobjekte dringend empfohlen. Derzeit unterstützt Windows 3 Detailebenen. Der Standardwert LOD ist 0, was die höchste Qualität darstellt. Andere LODs werden sequenziell nummeriert, z. B. 1, 2 und Get progressiv niedrigere Qualität. Die [Windows Mixed Reality Asset Konverter](https://github.com/Microsoft/glTF-Toolkit/releases) unterstützt das Generieren von Ressourcen, die diese Spezifikation LOD erfüllt werden, indem mehrere GlTF Modelle akzeptieren und in einem einzelnen Medienobjekt mit gültigen LOD Ebenen zusammenführen. In der folgende Tabelle sind die erwarteten Ziele von LOD Sortier- und Dreieck aufgeführt:
<br>

|  LOD-Ebene  |  Empfohlene Anzahl von Dreieck  |  Maximale Anzahl von Dreieck | 
|-------|-------|-------|
|  LOD 0 |  10,000 |  10,000 | 
|  LOD 1 |  5,000  |  10,000 | 
|  LOD 2 |  2,500  |  10,000 | 

Bei LODs immer Geben Sie 3 LOD Ebenen an. Fehlende LODs bewirkt, dass das Modell, das nicht unerwartet wie die LOD-System-Switches auf die fehlende LOD gerendert. GlTF 2.0 unterstützt derzeit LODs als Teil der Core-Spezifikation nicht. LODs sollten daher mit definiert werden die [MSFT_LOD Erweiterung](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod).

### <a name="screen-coverage"></a>Bildschirm-Abdeckung

LODs werden in Windows Mixed Reality basiert auf einem System gesteuert, die durch den Bildschirm Coverage Wert, legen Sie für jede LOD angezeigt. Objekte, die derzeit einen größeren Teil der Platz auf dem Bildschirm verwendet werden, werden auf einer höheren LOD angezeigt. Bildschirm-Abdeckung ist nicht Teil der Core GlTF 2.0-Spezifikation und muss angegeben werden, verwenden im Abschnitt "Extras" MSFT_ScreenCoverage der [MSFT_lod Erweiterung](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod).
<br>

|  LOD-Ebene  |  Empfohlene Bereich  |  Standardbereich | 
|-------|-------|-------|
|  LOD 0  |  100% - 50% |  .5 | 
|  LOD 1 |  Unter 50 % 20 %  |  .2 | 
|  LOD 2 |  Unter 20 % 1 %  |  .01 | 
|  LOD 4  |  Unter 1 %  |  - | 

## <a name="animation-guidelines"></a>Animation-Richtlinien

> [!NOTE]
> Dieses Feature wurde hinzugefügt, als Teil des [Windows 10 April 2018 Update](release-notes-april-2018.md). Unter älteren Versionen von Windows, die diese Animationen nicht wiedergegeben werden, werden jedoch sie immer noch geladen, wenn gemäß den Anweisungen in diesem Artikel erstellt.  

Die mixed Reality-Homepage unterstützt animierte GlTF-Objekte für HoloLens und immersive Headsets von (VR). Wenn Sie Animationen auf Ihrem Modell auslösen möchten, müssen Sie die Zuordnung der Animation-Erweiterung für das GlTF-Format verwenden. Mit dieser Erweiterung können Sie Animationen im GlTF Modell basierend auf dem Vorhandensein der Benutzer in der ganzen Welt auslösen, z. B. Auslösen einer Animation, wenn der Benutzer ist in der Nähe des Objekts oder während sie diese betrachten. Wenn Sie GlTF Objekt Animationen, aber keine Trigger definiert werden die Animationen nicht wiedergegeben werden. Weiter unten im Abschnitt wird beschrieben, ein Workflow für jedes Objekt animierte GlTF diese Trigger hinzugefügt werden.

### <a name="tools"></a>Tools
Laden Sie zunächst die folgenden Tools auf, wenn sie noch nicht vorhanden ist. Diese Tools werden erleichtern Ihnen alle GlTF Modell öffnen, Vorschau anzuzeigen, Änderungen vornehmen und Speichern von wieder als GlTF oder .glb:
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [GlTF-Tools für Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>Sie öffnen und Anzeigen einer Vorschau des Modells
Starten Sie durch das GlTF-Modell in Visual Studio Code durch Ziehen der .glTF-Datei in das Editorfenster öffnen. Beachten Sie, wenn man eine .glb anstelle einer .glTF-Datei zu importieren, können sie in VSCode mit der GlTF Tools-Add-in, das Sie heruntergeladen. Wechseln Sie zu "-Ansicht > Befehlspalette den Befehl" mit der Eingabe von "GlTF" in der befehlspalette beginnen, und wählen "GlTF: Importieren von Glb"dem Sie eine Dateiauswahl für den import einer .glb mit angezeigt wird. 

Wenn Sie Ihr Modell GlTF geöffnet haben, sollten Sie den JSON-Code im Editor-Fenster sehen. Beachten Sie, dass Sie auch das Modell in einer live-3D-Viewer mit der Vorschau anzeigen können die von der rechten Maustaste auf den Dateinamen und Auswählen der "GlTF: Preview 3D-Modell"Befehl Abkürzung aus der rechten Maustaste öffnen. 

### <a name="adding-the-triggers"></a>Die Trigger hinzufügen
Animationstrigger werden GlTF Modell JSON-Daten mithilfe der Animation Zuordnungs-Erweiterung hinzugefügt. Die Animation-Zuordnungs-Erweiterung wird öffentlich dokumentiert [hier auf GitHub](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) (Hinweis: DIES IST EIN ENTWURF-ERWEITERUNG). Hinzufügen der Erweiterung für das Modell nur scrollleiste an das Ende der GlTF-Datei im Editor, und fügen den Block "ExtensionsUsed" und "Erweiterungen" in die Datei ein, wenn sie nicht bereits vorhanden sind. Klicken Sie im Abschnitt "ExtensionsUsed" Fügen Sie einen Verweis auf die Erweiterung "EXT_animation_map" und in den Block "Extensions" Fügen Sie Ihre Zuordnungen auf die Animationen im Modell.

Wie bereits erwähnt [in der Spezifikation](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) Sie definieren, was löst die Animation, die unter Verwendung der "semantischen" Zeichenfolge in der Liste der "Animationen" wird ein Array von Indizes der Animation. Im folgenden Beispiel haben wir die Animation gestartet wird, während der Benutzer auf das Objekt gazing wird angegeben:

```json
  "extensionsUsed": [
    "EXT_animation_map"
  ],
  "extensions" : {
      "EXT_animation_map" : {
            "bindings": [
                {
                    "semantic": "GAZE",
                    "animations": [0]
                }
            ]
      }
  }
```
Die folgenden Trigger Semantik für Animation werden von der Windows Mixed Reality home unterstützt.  
* "ALWAYS": Ständig Schleife einer animation
* "ENTHALTENE": Während der gesamten Dauer Schleife ist ein Objekt Ruhe.
* "BLICKE": In einer Schleife, während ein Objekt betrachtet wird
* "NEAR": In einer Schleife, während ein Viewer in der Nähe eines Objekts befindet
* "ZEIGT": In einer Schleife, während ein Benutzer auf ein Objekt verweist

### <a name="saving-and-exporting"></a>Speichern und exportieren
Einmal vorgenommenen Änderungen an Ihrem GlTF-Modell können Sie es direkt als GlTF speichern, oder klicken Sie rechts auf den Namen der Datei im Editor, und wählen Sie "GlTF: Exportieren in GLB (Binärdatei) "eine .glb stattdessen zu exportieren. 

### <a name="restrictions"></a>Restrictions
Animationen darf nicht länger als 20 Minuten und können nicht mehr als 36.000 Keyframes (20 Minuten unter 30 BpS) enthalten. Außerdem bei Verwendung von Morph Ziel aufgrund Animationen nicht überschreiten 8192 Morph Ziel Vertices oder weniger. Überschreitung dieser Anzahl wird latenzkritischen das animierte Objekt in die Windows Mixed Reality-Homepage nicht unterstützt werden. 

|Feature|Maximal|
|-----|-----|
|Dauer|20 Minuten|
|Keyframes|36,000| 
|Morph Ziel Vertices|8.192|

## <a name="gltf-implementation-notes"></a>Hinweise zur Implementierung der glTF
Windows-MR unterstützt Kipp Geometrie, die mithilfe von negativer Skalen nicht. Geometrie mit negativen Skalen führt wahrscheinlich zu visuelle Artefakte aufweisen.

Das Medienobjekt GlTF muss der Standard-Szene mit, dass die Szene-Attribut durch Windows MR gerendert werden verweisen. Außerdem das Windows-MR GlTF-Ladeprogramm vor der [Windows 10 April 2018 aktualisieren](release-notes-april-2018.md) **erfordert** Accessoren:
* Minimal- und Maximalwerte müssen.
* SKALARE muss ComponentType UNSIGNED_SHORT (5123) oder UNSIGNED_INT (5125) aufweisen.
* Typ VEC2 und VEC3 müssen ComponentType "float" (5126) sein.

Die folgenden Material-Eigenschaften sind in Core GlTF 2.0-Spezifikation verwendet, jedoch nicht erforderlich:
* baseColorFactor, metallicFactor, roughnessFactor
* baseColorTexture: Muss auf eine Textur im Dds gespeichert verweisen.
* emissiveTexture: Muss auf eine Textur im Dds gespeichert verweisen.
* emissiveFactor
* alphaMode

Die folgenden Material-Eigenschaften werden aus der Core-Spezifikation ignoriert:
* Alle Multi-UVs
* metalRoughnessTexture: Microsoft optimiert Textur Packen von Metriken, die nachstehend definiert müssen stattdessen verwenden.
* normalTexture: Microsoft optimiert Textur Packen von Metriken, die nachstehend definiert müssen stattdessen verwenden.
* normalScale
* OcclusionTexture: Microsoft optimiert Textur Packen von Metriken, die nachstehend definiert müssen stattdessen verwenden.
* occlusionStrength

Windows-MR unterstützt keine primitiven Modus Linien und Punkten. 

Es wird nur ein einziges UV Vertex Attribut unterstützt.

## <a name="additional-resources"></a>Zusätzliche Ressourcen
* [GlTF Metadatenexport- und Konverter](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [GlTF Toolkit](https://github.com/Microsoft/glTF-Toolkit)
* [GlTF 2.0 Specification](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Microsoft GlTF LOD Erweiterungsspezifikation](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [PC Mixed Reality Textur Packen Extensions-Spezifikation](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [HoloLens, Mixed Reality Textur Packen Extensions-Spezifikation](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Microsoft DDS-Texturen GlTF Extensions-Spezifikation](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>Siehe auch

* [Implementieren von 3D-App-Startprogrammen (UWP-Apps)](implementing-3d-app-launchers.md)
* [Implementieren von 3D-App-Startprogrammen (Win32-Apps)](implementing-3d-app-launchers-win32.md)
* [Navigieren auf der Startseite von Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
