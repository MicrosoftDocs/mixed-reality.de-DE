---
title: Erstellen von 3D-Modellen für die Verwendung in der Startseite
description: Asset-Anforderungen und Erstellungs Anleitungen für 3D-Modelle, die in der Windows Mixed Reality-Startseite sowohl auf hololens-als auch in immersiven (VR)-Headsets verwendet werden.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: 3D, Modellierung, Modellierungs Anleitung, Asset-Anforderungen, Erstellungs Richtlinien, Start Programm, 3D-Start Programm, Textur, Material, Komplexität, Dreiecke, Mesh, Polygone, Polycount, Limits
ms.openlocfilehash: 536fd9bc2002d679ee3bf73d5c906b84c51e5d46
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926578"
---
# <a name="create-3d-models-for-use-in-the-home"></a>Erstellen von 3D-Modellen für die Verwendung in der Startseite

Der [Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) -Startpunkt ist der Ausgangspunkt, an dem Benutzer vor dem Starten von Anwendungen landen. Sie können Ihre Anwendung für Windows Mixed Reality-Headsets entwerfen, um ein [3D-Modell als App](implementing-3d-app-launchers.md) -Startfeld zu nutzen und um [das Platzieren von 3D-Deep-Links in der Windows Mixed Reality-Startseite](implementing-3d-app-launchers.md#3d-deep-links-secondarytiles) innerhalb Ihrer APP zu ermöglichen. In diesem Artikel werden die Richtlinien für die Erstellung von 3D-Modellen beschrieben, die mit dem Windows Mixed Reality-Start

## <a name="asset-requirements-overview"></a>Übersicht über Asset-Anforderungen
Beim Erstellen von 3D-Modellen für Windows Mixed Reality gibt es einige Anforderungen, die alle Assets erfüllen müssen: 
1. [Export](#exporting-models) -Assets müssen im. GLB-Dateiformat (binäres gltf) übermittelt werden.
2. [Modellierung](#modeling-guidelines) : Assets müssen kleiner als 10.000 Dreiecke sein, dürfen nicht mehr als 64 Knoten und 32 Subnetze pro Lod aufweisen.
3. [Material](#material-guidelines) : Texturen dürfen nicht größer als 4096 x 4096 sein, und die kleinste MIP-Zuordnung sollte in beiden Dimensionen nicht größer als 4 sein.
4. [Animation](#animation-guidelines) -Animationen dürfen nicht länger als 20 Minuten bei 30 fps (36.000 Keyframes) sein und müssen < = 8192 Morph-Ziel Vertices enthalten.
5. [Optimieren](#optimizations) : Assets sollten mithilfe von [windowsmrassetconverter](https://github.com/Microsoft/glTF-Toolkit/releases)optimiert werden. Dies ist **unter Windows-Betriebssystemversionen < = 1709 erforderlich** und wird unter Windows-Betriebssystemversionen empfohlen > = 1803

Der Rest dieses Artikels enthält eine ausführliche Übersicht über diese Anforderungen sowie weitere Richtlinien, um sicherzustellen, dass Ihre Modelle mit dem Windows Mixed Reality-Start gut funktionieren. 

## <a name="detailed-guidance"></a>Ausführliche Anleitungen

### <a name="exporting-models"></a>Exportieren von Modellen

Die Windows Mixed Reality-Startseite erwartet, dass 3D-Assets über das. GLB-Dateiformat mit eingebetteten Bildern und Binärdaten übermittelt werden. GLB ist die binäre Version des gltf-Formats, bei der es sich um einen kostenlosen Open-Standard für die 3D-Asset-Bereitstellung handelt, der von der Khronos-Gruppe Da sich gltf als Industriestandard für interoperablen 3D-Inhalt entwickelt, unterstützt Microsoft das Format in Windows-apps und-Umgebungen. Wenn Sie noch kein gltf-Asset erstellt haben, können Sie auf der GitHub-Seite der gltf-Arbeitsgruppe eine [Liste der unterstützten Export-und Konverter](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) finden.  

### <a name="modeling-guidelines"></a>Modellierungs Richtlinien

Windows erwartet anhand der folgenden Modellierungs Richtlinien, dass Assets generiert werden, um die Kompatibilität mit der gemischten Realität zu gewährleisten. Beachten Sie beim Modellieren in Ihrem Programm Ihre Wahl die folgenden Empfehlungen und Einschränkungen:
1. Die up-Achse sollte auf "Y" festgelegt werden.
2. Das Medienobjekt sollte für die positive Z-Achse "Vorwärts" stehen.
3. Alle Assets sollten auf der Grundebene am Ursprung der Szene (0,0) erstellt werden.
4. Arbeitseinheiten sollten auf Meter und Ressourcen festgelegt werden, damit Assets weltweit skaliert werden können
5. Alle Netzen müssen nicht kombiniert werden, es wird jedoch empfohlen, wenn Sie auf Ressourcen beschränkte Geräte abzielen.
6. Alle Netzen sollten 1 Material gemeinsam nutzen, wobei nur ein Textur Satz für das gesamte Asset verwendet wird.
7. UVS müssen in einer quadratischen Anordnung im 0-1-Bereich angeordnet werden. Vermeiden Sie das Durchsuchen von Texturen, auch wenn Sie zulässig sind.
8. Multiudfs werden nicht unterstützt.
9. Doppelte seitige Materialien werden nicht unterstützt.

### <a name="triangle-counts-and-levels-of-detail-lods"></a>Dreiecks Anzahl und Detailebenen (LODs)

Die Windows Mixed Reality-Startseite bietet keine Unterstützung für Modelle mit mehr als 10.000 Dreiecken. Es wird empfohlen, dass Sie Ihre Netzen vor dem Exportieren auslassen, um sicherzustellen, dass diese Anzahl nicht überschritten wird. Windows Mr unterstützt auch optionale Geometrie Ebenen (LODs), um eine leistungsfähige und qualitativ hochwertige Darstellung sicherzustellen. [Der windowsmrassetconverter unter](https://github.com/Microsoft/glTF-Toolkit/releases) stützt Sie beim Kombinieren von drei Versionen Ihres Modells in einem einzigen. GLB-Modell. Windows legt fest, welche Lod basierend auf der Menge der Bildschirmfläche angezeigt werden soll, die das Modell einnimmt. Es werden nur drei Lod-Ebenen mit den folgenden empfohlenen Dreiecks Zählungen unterstützt:
<br>

|  LOD-Ebene  |  Empfohlene Dreiecks Anzahl  |  Maximale Anzahl von Dreiecks | 
|------|------|------|
|  LOD 0 |  10.000 |  10.000 | 
|  LOD 1 |  5\.000  |  10.000 | 
|  LOD 2 |  2\.500  |  10.000 | 

### <a name="node-counts-and-submesh-limits"></a>Knoten Zähler und submesh-Limits
Die Windows Mixed Reality-Startseite unterstützt keine Modelle mit mehr als 64 Knoten oder 32 Subnetzen pro Lod. Knoten sind ein Konzept in der [gltf-Spezifikation](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy) , die die Objekte in der Szene definieren. Subnetze werden im Array von [primitiven](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes) im-Objekt definiert. 

|  Feature |  Beschreibung  |  Maximal unterstützt | Unterlagen |
|------|------|------|------|
|  Knoten |  Objekte in der gltf-Szene |  64 pro Lod | [Anwesend](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#nodes-and-hierarchy)|
|  Subnetze |  Summe von primitiven für alle Netzen |  32 pro Lod | [Anwesend](https://github.com/KhronosGroup/glTF/tree/master/specification/2.0#meshes)|

## <a name="material-guidelines"></a>Material Leit Fäden

Texturen sollten mithilfe eines PBR-Metal-rautheit-Workflows vorbereitet werden. Beginnen Sie, indem Sie einen vollständigen Satz von Texturen erstellen, einschließlich Albedo, normal, Okklusion, Metallic und rauen. Windows Mixed Reality unterstützt Texturen mit Auflösungen bis 4096x4096, aber es wird empfohlen, dass Sie die Erstellung bei 512x512 durch schreiben. Außerdem sollten Texturen bei Auflösungen in Vielfachen von 4 erstellt werden, da dies eine Voraussetzung für das Komprimierungs Format ist, das auf Texturen in den unten beschriebenen Export Schritten angewendet wird. Beim Erstellen von MIP-Zuordnungen oder einer Textur muss das niedrigste MIP höchstens 4 x 4 sein.
<br>

|  Empfohlene Textur Größe  |  Maximale Textur Größe | Niedrigste MIP
|----|----|----|
|  512 x 512  |  4096x4096 | Max. 4 x 4|

### <a name="albedo-base-color-map"></a>Karte "Albedo (Basis Farbe)"

Rohfarbe ohne Beleuchtungs Informationen. Diese Karte enthält auch die Reflektions-und diffusen Informationen für Metal (weiß in der metallischen Karte) und die Flächen (schwarz in der metallischen Karte).

### <a name="normal"></a>Normal

Tangens Raum normaler Karte

### <a name="roughness-map"></a>Rautenzuordnung

Beschreibt die-Oberfläche des-Objekts. Weiß 1,0 ist grob schwarz 0,0 ist glatt. Diese Karte gibt dem Medienobjekt das meiste Zeichen, da es die Oberfläche beschreibt, z. b. Kratzer, Fingerabdrücke, smudges, Grime usw.

### <a name="ambient-occlusion-map"></a>Ambiente-Okklusions Zuordnung

Werte Skalierungs Zuordnung, die Bereiche der okkludierten Beleuchtung darstellt, die Reflektionen blockieren

### <a name="metallic-map"></a>Metallische Karte

Weist den Shader an, wenn etwas Metal ist oder nicht. RAW Metal = 1,0 White Non Metal = 0,0 Black. Es können vorübergehende graue Werte vorhanden sein, die darauf hinweisen, dass das unformatierte Metall wie z. b. "Dirt" ist, aber im Allgemeinen sollte diese Karte nur schwarz und weiß sein

## <a name="optimizations"></a>Optimierungen

Windows Mixed Reality Home bietet eine Reihe von Optimierungen, die auf der Core-gltf-Spezifikation liegen, die mit benutzerdefinierten Erweiterungen definiert wurde. Diese Optimierungen sind in Windows-Versionen < = 1709 erforderlich und werden für neuere Versionen von Windows empfohlen. Mithilfe des [Windows Mixed Reality Asset Converter, der auf GitHub verfügbar](https://github.com/Microsoft/glTF-Toolkit/releases)ist, können Sie ein beliebiges gltf 2,0-Modell problemlos optimieren. Dieses Tool führt die richtige Textur Verpackung und Optimierungen wie unten angegeben aus. Zur allgemeinen Verwendung empfiehlt sich die Verwendung von windowsmrassetconverter. Wenn Sie jedoch mehr Kontrolle über die Benutzerfunktion benötigen und eine eigene Optimierungs Pipeline erstellen möchten, können Sie die unten angegebene Ausführliche Spezifikation verwenden.  

### <a name="materials"></a>Werk

Zum Verbessern der Lade Zeit für Medienobjekte in Mixed Reality-Umgebungen unterstützt Windows Mr das Rendern komprimierter DDS-Texturen entsprechend dem in diesem Abschnitt definierten Textur Verpackungs Schema. Auf DDS-Texturen wird mit der [MSFT_texture_dds-Erweiterung](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_texture_dds)verwiesen. Das Komprimieren von Texturen wird dringend empfohlen. 

#### <a name="hololens"></a>HoloLens

Die auf hololens basierende gemischte Realität erwartet, dass Texturen mithilfe eines 2-Textur-Setups verpackt werden, indem die folgende Packungs Spezifikation verwendet wird:
<br>

|  gltf-Eigenschaft  |  Konsistenz  |  Verpackungs Schema | 
|----------|----------|----------|
|  pbrmetallicroughness  |  basecolortexture  |  Rot (R), grün (G), blau (B) | 
|  [MSFT_packing_normalRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)  |  normalroughnessmetallictexture  |  Normal (RG), rautheit (B), metallisch (a) | 


Beim Komprimieren der DDS-Texturen wird die folgende Komprimierung auf jeder Zuordnung erwartet:
<br>

|  Konsistenz  |  Erwartete Komprimierung | 
|------|------|
|  basecolortexture, normroughnessmetallictexture |  BC7 | 

#### <a name="immersive-vr-headsets"></a>Immersive (VR)-Headsets

Die PC-basierte Windows Mixed Reality-Umgebung für immersive (VR)-Headsets erwartet, dass Texturen mithilfe eines 3-Textur-Setups verpackt werden, indem die folgende Packungs Spezifikation verwendet wird:

##### <a name="windows-os--1803"></a>Windows-Betriebssystem > = 1803

<br>

|  gltf-Eigenschaft  |  Konsistenz  |  Verpackungs Schema | 
|----------|----------|----------|
|  pbrmetallicroughness  |  basecolortexture  |  Rot (R), grün (G), blau (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  oksionroughnessmetallictexture  |  Okklusion (R), rautheit (G), metallisch (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normaltexture  |  Normal (RG) | 

Beim Komprimieren der DDS-Texturen wird die folgende Komprimierung auf jeder Zuordnung erwartet:
<br>

|  Konsistenz  |  Erwartete Komprimierung | 
|------|------|
|  normaltexture  |  BC5 | 
|  basecolortexture, oksionroughnessliclictexture  |  BC7 | 

##### <a name="windows-os--1709"></a>Windows-Betriebssystem < = 1709
<br>

|  gltf-Eigenschaft  |  Konsistenz  |  Verpackungs Schema | 
|----------|----------|----------|
|  pbrmetallicroughness  |  basecolortexture  |  Rot (R), grün (G), blau (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  roughnessmetallicocclusiontexture  |  Rautheit (R), metallisch (G), Okklusion (B) | 
|  [MSFT_packing_occlusionRoughnessMetallic](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)  |  normaltexture  |  Normal (RG) | 

Beim Komprimieren der DDS-Texturen wird die folgende Komprimierung auf jeder Zuordnung erwartet:
<br>

|  Konsistenz  |  Erwartete Komprimierung | 
|------|------|
|  normaltexture  |  BC5 | 
|  basecolortexture, roughnessmetallicocclusiontexture | BC7 |

### <a name="adding-mesh-lods"></a>Hinzufügen von Mesh-LODs

Windows Mr verwendet Geometrie Knoten-LODs, um 3D-Modelle abhängig von der Bildschirm Abdeckung in unterschiedlichen Detailebenen zu Rendering. Diese Funktion ist zwar technisch nicht erforderlich, wird jedoch für alle Assets dringend empfohlen. Derzeit werden von Windows drei Detailebenen unterstützt. Der Standard-Lod ist 0 (null), der die höchste Qualität darstellt. Andere LODs werden sequenziell nummeriert, z. b. 1, 2, und erzielen die Qualität progressiv. Der [Windows Mixed Reality Asset Converter](https://github.com/Microsoft/glTF-Toolkit/releases) unterstützt das Erstellen von Assets, die diese Lod-Spezifikation erfüllen, indem mehrere gltf-Modelle akzeptiert und in einem einzelnen Medienobjekt mit gültigen Lod-Ebenen zusammengeführt werden. In der folgenden Tabelle sind die erwarteten Lod-Reihen folgen und Dreiecks Ziele aufgeführt:
<br>

|  LOD-Ebene  |  Empfohlene Dreiecks Anzahl  |  Maximale Anzahl von Dreiecks | 
|-------|-------|-------|
|  LOD 0 |  10.000 |  10.000 | 
|  LOD 1 |  5\.000  |  10.000 | 
|  LOD 2 |  2\.500  |  10.000 | 

Wenn Sie LODs verwenden, geben Sie immer drei Lod-Ebenen an. Fehlende LODs bewirken, dass das Modell nicht unerwartet wieder verwendet wird, wenn das Lod-System zur fehlenden Lod-Ebene wechselt. gltf 2,0 unterstützt derzeit keine LODs als Teil der Kern Spezifikation. Daher sollten LODs mit der [MSFT_LOD-Erweiterung](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)definiert werden.

### <a name="screen-coverage"></a>Bildschirm Abdeckung

LODs werden in Windows Mixed Reality auf Grundlage eines Systems angezeigt, das durch den für jede Lod festgelegten Bildschirm Abdeckungs Wert gesteuert wird. Objekte, die gerade einen größeren Teil des Bildschirmbereichs beanspruchen, werden auf einer höheren Lod-Ebene angezeigt. Die Bildschirm Abdeckung ist nicht Teil der Core gltf 2,0-Spezifikation und muss mit MSFT_ScreenCoverage im Abschnitt "Extras" der [MSFT_lod Erweiterung](https://github.com/sbtron/glTF/tree/MSFT_lod/extensions/Vendor/MSFT_lod)angegeben werden.
<br>

|  LOD-Ebene  |  Empfohlener Bereich  |  Standardbereich | 
|-------|-------|-------|
|  LOD 0  |  100%-50% |  ADDI | 
|  LOD 1 |  Unter 50%-20%  |  Multi | 
|  LOD 2 |  Weniger als 20%-1%  |  01 | 
|  LOD 4  |  Unter 1%  |  - | 

## <a name="animation-guidelines"></a>Animations Richtlinien

> [!NOTE]
> Diese Funktion wurde als Teil des [Windows 10-Updates vom April 2018](release-notes-april-2018.md)hinzugefügt. In älteren Versionen von Windows werden diese Animationen nicht wiedergegeben, aber Sie werden nach dem Erstellen der Anweisungen in diesem Artikel weiterhin geladen.  

Die Mixed Reality-Startseite unterstützt animierte gltf-Objekte auf hololens-und immersive-Headsets (VR). Wenn Sie Animationen für Ihr Modell verwenden möchten, müssen Sie die Animations Zuordnungs Erweiterung im gltf-Format verwenden. Mit dieser Erweiterung können Sie Animationen im gltf-Modell auf der Grundlage der Benutzer in der Welt Auslösern, z. b. eine Animation, wenn sich der Benutzer in der Nähe des Objekts befindet oder wenn er sich darauf befindet. Wenn Sie ein gltf-Objekt mit Animationen haben, aber keine Trigger definieren, werden die Animationen nicht wiedergegeben. Der folgende Abschnitt beschreibt einen Workflow zum Hinzufügen dieser Trigger zu einem animierten gltf-Objekt.

### <a name="tools"></a>Tools
Laden Sie zunächst die folgenden Tools herunter, wenn Sie noch nicht vorhanden sind. Mit diesen Tools können Sie ganz einfach ein beliebiges gltf-Modell öffnen, eine Vorschau anzeigen, Änderungen vornehmen und das Back-End als gltf oder. GLB speichern:
1. [Visual Studio Code](https://code.visualstudio.com/)
2. [gltf-Tools für Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode)


### <a name="opening-and-previewing-the-model"></a>Öffnen und Anzeigen der Vorschau des Modells
Öffnen Sie zunächst das gltf-Modell in vscode, indem Sie die. gltf-Datei in das Editor-Fenster ziehen. Beachten Sie Folgendes: Wenn Sie über eine. GLB-Datei anstelle einer. gltf-Datei verfügen, können Sie Sie mit dem heruntergeladenen Tool "gltf Tools" in vscode importieren. Wechseln Sie zu "View-> Command Palette", und beginnen Sie dann mit der Eingabe von "gltf" in der Befehls Palette, und wählen Sie "gltf: Import from GLB" aus. Daraufhin wird eine Dateiauswahl angezeigt, mit der Sie eine. GLB-Datei importieren können. 

Nachdem Sie das gltf-Modell geöffnet haben, sollte der JSON-Code im Editor-Fenster angezeigt werden. Beachten Sie, dass Sie die Vorschau des Modells in einem Live-3D-Viewer mithilfe von auch in einer Vorschau anzeigen können, indem Sie mit der rechten Maustaste auf den Dateinamen klicken und die Befehls Verknüpfung "gltf: Preview 3D Model" im Kontextmenü auswählen 

### <a name="adding-the-triggers"></a>Hinzufügen der Trigger
Animations Trigger werden dem gltf-Modell JSON mithilfe der Animations Zuordnungs Erweiterung hinzugefügt. Die Animations Zuordnungs Erweiterung wird [hier auf GitHub](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) öffentlich dokumentiert (Hinweis: Dies ist eine Entwurfs Erweiterung). Wenn Sie dem Modell die Erweiterung hinzufügen möchten, Scrollen Sie einfach zum Ende der gltf-Datei im Editor, und fügen Sie der Datei den Block "extensionsused" und "Extensions" hinzu, wenn Sie nicht bereits vorhanden sind. Im Abschnitt "extensionsused" fügen Sie einen Verweis auf die Erweiterung "EXT_animation_map" hinzu, und im Block "Extensions" fügen Sie die Zuordnungen den Animationen im Modell hinzu.

Wie [in der Spezifikation](https://github.com/msfeldstein/glTF/blob/04f7005206257cf97b215df5e3f469d7838c1fee/extensions/Vendor/FB_animation_map/README.md) angegeben, definieren Sie, was die Animation auslöst, indem Sie die "semantische" Zeichenfolge in einer Liste von "Animationen" verwendet, bei der es sich um ein Array von Animations Indizes handelt Im folgenden Beispiel haben wir die Animation angegeben, die abgespielt werden soll, während der Benutzer am Objekt sucht:

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
Die folgenden Animations Trigger-Semantik wird von der Windows Mixed Reality-Startseite unterstützt.  
* "Always": beständig Schleife einer Animation
* "Gehalten": Schleife während der gesamten Dauer, in der ein Objekt gepackt wird.
* "Blick": Schleifen Schleifen, während ein Objekt betrachtet wird.
* "Near": Schleife, während sich ein Viewer in der Nähe eines Objekts befindet.
* "Zeigen": Schleife, während ein Benutzer auf ein Objekt zeigt

### <a name="saving-and-exporting"></a>Speichern und exportieren
Nachdem Sie die Änderungen an Ihrem gltf-Modell vorgenommen haben, können Sie es direkt als gltf speichern, oder Sie können mit der rechten Maustaste auf den Namen der Datei im Editor klicken und "gltf: Export to GLB (Binary File)" auswählen, um stattdessen eine. GLB-Datei zu exportieren. 

### <a name="restrictions"></a>Einschränkungen
Animationen dürfen nicht länger als 20 Minuten sein und dürfen nicht mehr als 36.000 Keyframes (20 Minuten bei 30 fps) enthalten. Außerdem werden bei Verwendung von Morph-Ziel basierten Animationen nicht mehr als 8192 Morph-Ziel Vertices oder weniger überschritten. Wenn diese Anzahl überschritten wird, wird das animierte Asset in der Windows Mixed Reality-Startseite nicht unterstützt. 

|Feature|Maximal|
|-----|-----|
|Duration|20 Minuten|
|Keyframes|36.000| 
|Ziel Vertices für Morph|8\.192|

## <a name="gltf-implementation-notes"></a>Hinweise zur gltf-Implementierung
Windows Mr unterstützt keine flippinggeometrie mit negativen Skalen. Geometrie mit negativen Skalen führt wahrscheinlich zu visuellen Artefakten.

Das gltf-Asset muss auf die Standard Szene zeigen, wobei das Scene-Attribut verwendet wird, das von Windows Mr gerendert wird. Zusätzlich **erfordert** das Windows Mr-gltf-Lade Modul vor dem [Windows 10-Update vom April 2018](release-notes-april-2018.md) Accessoren:
* Muss über minimale und maximale Werte verfügen.
* Der Typ Skalar muss ein componentType-UNSIGNED_SHORT (5123) oder UNSIGNED_INT (5125) sein.
* Type vec2 und VEC3 müssen componentType float (5126) sein.

Die folgenden Materialeigenschaften werden aus der Core gltf 2,0-Spezifikation verwendet, sind jedoch nicht erforderlich:
* basecolorfactor, Metal licfactor, roughnessfactor
* basecolortexture: muss auf eine in DDS gespeicherte Textur zeigen.
* emissivetexture: muss auf eine in DDS gespeicherte Textur zeigen.
* emissivefactor
* Alpha AMODE

Die folgenden Materialeigenschaften werden von der Kern Spezifikation ignoriert:
* Alle Multi-UVS
* metalroughnesstexture: muss stattdessen die unten definierte Microsoft-optimierte Textur Verpackung verwenden.
* normaltexture: muss stattdessen die unten definierte Microsoft-optimierte Textur Verpackung verwenden.
* normal skalieren
* oksiontexture: muss stattdessen die unten definierte Microsoft-optimierte Textur Verpackung verwenden.
* oksions Stärke

Die Zeilen und Punkte des primitiven Modus werden von Windows Mr nicht unterstützt. 

Nur ein einzelnes UV-Vertex-Attribut wird unterstützt.

## <a name="additional-resources"></a>Weitere Ressourcen
* [gltf-Export-und-Konverter](https://github.com/KhronosGroup/glTF#converters-and-exporters)
* [gltf-Toolkit](https://github.com/Microsoft/glTF-Toolkit)
* [gltf 2,0-Spezifikation](https://github.com/KhronosGroup/glTF/blob/master/README.md)
* [Microsoft gltf Lod-Erweiterungs Spezifikation](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_lod/README.md)
* [Spezifikation für die Textur Verpackungs Erweiterungen für PCs Mixed Reality](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_occlusionRoughnessMetallic/README.md)
* [Hololens Mixed Reality Texture Packaging Extensions Specification](https://github.com/KhronosGroup/glTF/blob/master/extensions/2.0/Vendor/MSFT_packing_normalRoughnessMetallic/README.md)
* [Microsoft DDS Texturen gltf Extensions Specification](https://github.com/KhronosGroup/glTF/tree/master/extensions/2.0/Vendor/MSFT_texture_dds)

## <a name="see-also"></a>Weitere Informationen:

* [Implementieren von 3D-App-Startprogrammen (UWP-Apps)](implementing-3d-app-launchers.md)
* [Implementieren von 3D-App-Startprogrammen (Win32-Apps)](implementing-3d-app-launchers-win32.md)
* [Navigieren auf der Startseite von Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
