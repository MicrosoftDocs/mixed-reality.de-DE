---
title: 'Fallstudie: Erstellen von HoloSketch, eine räumliche Layout und die UX-app für HoloLens skizzieren'
description: HoloSketch ist auf dem Gerät räumliche Layout und UX skizzieren Tool für HoloLens, um holographic Benutzeroberflächen zu erstellen.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloSketch, HoloLens, Windows Mixed Reality, skizzieren, app
ms.openlocfilehash: d7f94a09bf4a8a16000c2345adf1a046dab4bd15
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594280"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>Fallstudie: Erstellen von HoloSketch, eine räumliche Layout und die UX-app für HoloLens skizzieren

HoloSketch ist auf dem Gerät räumliche Layout und UX skizzieren Tool für HoloLens, um holographic Benutzeroberflächen zu erstellen. HoloSketch arbeitet mit gekoppelten Bluetooth-Tastatur und Maus als auch Gestik- und Befehle. Der Zweck der HoloSketch ist ein einfaches UX-Layout-Tool für rasche visualisierungs- und Iteration bereitstellen.

![HoloSketch: Eine räumliche Layout und die UX-app für HoloLens skizzieren.](images/holosketch-image-01-640px.png)<br>
*HoloSketch: räumliche Layout und die UX-app für HoloLens skizzieren*

![Eine einfache Benutzeroberfläche Tool "Layout" für rasche visualisierungs- und Iteration.](images/holosketch-image-02.png)<br>
*Ein einfaches UX-Layout-Tool für rasche visualisierungs- und iteration*

## <a name="features"></a>Features

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>-Grundtypen für die schnelle Studien und skalieren – Erstellen von Prototypen

![Primitive Formen](images/holosketch-primitives-giphy.gif)

Verwenden Sie primitive-Shapes für schnelle massing Studien und skalieren – Erstellen von Prototypen.

### <a name="import-objects-through-onedrive"></a>Importieren von Objekten über OneDrive

![Importieren von Objekten](images/holosketch-importobjects-giphy.gif)

PNG/JPG-Bilder oder FBX-3D-Objekte importieren (erfordert die paketerstellung in Unity) in den mixed Reality-Bereich über OneDrive.

### <a name="manipulate-objects"></a>Bearbeiten von Objekten

![Bearbeiten von Objekten](images/manipulate-objects-640px.jpg)

Bearbeiten von Objekten (verschieben/drehen/skalieren) mit einer vertrauten 3D-Objekt-Schnittstelle.

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>Bluetooth, Maus und Tastatur, Gesten und Stimme Befehle

![unterstützt die Bluetooth](images/supports-bluetooth-640px.jpg)

HoloSketch unterstützt Bluetooth-Tastatur oder Maus, Gesten und Sprachbefehle.

## <a name="background"></a>Hintergrund

### <a name="importance-of-experiencing-your-design-in-the-device"></a>Wichtigkeit der auf Ihren Entwurf auf dem Gerät

Wenn Sie etwas für HoloLens entwerfen, ist es wichtig, damit können Sie Ihren Entwurf auf dem Gerät. Einer der größten Herausforderungen in mixed Reality-app-Design ist, dass es schwer, um die Bedeutung von Skalierung, Position und Tiefe, insbesondere über herkömmliche 2D Skizzen zu erhalten.

### <a name="cost-of-2d-based-communication"></a>Kosten für 2D-basierte Kommunikation

Um die UX-Flows und andere Szenarien effektiv kommunizieren zu können, kann ein Designer schließlich verbringen viel Zeit mit der Erstellung von Ressourcen mithilfe der herkömmlichen 2D Tools wie Illustrator, Photoshop und PowerPoint. Diese Entwürfe 2D erfordern häufig zusätzlichen Aufwand konvertieren ihn in 3D. Einige Ideen in diese Übersetzung von 2D in 3D verloren.

### <a name="complex-deployment-process"></a>Komplexe Bereitstellung

Gemischte Realität eine neuen Zeichenbereich für uns daher viel hat und der Versuch und Irrtum naturgemäß verbunden. Für den Designer, die mit Tools wie z. B. Unity und Visual Studio nicht vertraut sind, ist es nicht einfach etwas in HoloLens zusammengestellt. In der Regel müssen Sie das nachfolgend beschriebene Verfahren durchlaufen, um Ihre 2D-/3D-Bilder auf dem Gerät finden Sie unter. Dies war eine große Hürde für Designer, durchlaufen schnell von Ideen und Szenarien.

![Komplexe Bereitstellung](images/holosketch-image-03-1000px.png)<br>
*Bereitstellungsprozess*

### <a name="simplified-process-with-holosketch"></a>Vereinfachter Prozess mit HoloSketch

Wir wollten mit HoloSketch diesen Prozess zu vereinfachen, ohne die Einbeziehung von Entwicklungstools und Device Portal Kopplung. OneDrive zu verwenden, können Benutzer problemlos 2D-/3D-Assets in HoloLens versetzen.

![Vereinfachter Prozess mit HoloSketch](images/holosketch-image-04-1000px.png)<br>
*Vereinfachter Prozess mit HoloSketch*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>Ermutigend dreidimensionalen Design-Überlegungen und Lösungen

Wir dachten, dass dieses Tool Designer erhalten Gelegenheit, zu entdecken Sie Lösungen in einem tatsächlich dreidimensionalen Raum und nicht in 2D unterbrochen werden. Sie müssen überlegen, 3D Hintergrund für ihre Benutzeroberfläche erstellen, da der Hintergrund der realen Welt im Fall von Hololens ist. HoloSketch wird eine Möglichkeit, sich dann 3D Entwurf für Hololens-Designer geöffnet.

## <a name="get-started"></a>Erste Schritte

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>Vorgehensweise beim Importieren von 2D-Bilder JPG-/PNG-() in HoloSketch

* JPG-/PNG-Bilder in Ihrem OneDrive-Ordner "Dokumente/HoloSketch" hochladen.
* Wählen Sie im Menü "OneDrive" in HoloSketch werden Sie auswählen, und übertragen Sie das Abbild in der Umgebung.

![Importieren von 2D-Bilder](images/import-2d-images-1000px.jpg)<br>
*Importieren von Images und 3D-Objekte über OneDrive*

### <a name="how-to-import-3d-objects-into-holosketch"></a>Vorgehensweise beim Importieren von 3D-Objekten in HoloSketch

Befolgen Sie bevor Sie in Ihrem OneDrive-Ordner hochladen die folgenden Schritte zum Packen Ihrer 3D-Objekte in einem Unity Asset Bündel. Mit diesem Prozess können Sie Ihre FBX/OBJ-Dateien von 3D Software, z. B. Maya, Kino 4D und Microsoft Paint 3D importieren.

>[!IMPORTANT]
>Derzeit wird die medienobjekterstellung-Bundle mit Unity Version 5.4.5f1 unterstützt.

1. Herunterladen und öffnen Sie das Unity-Projekt ["AssetBunlder_Unity"](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity). Dieses Unity-Projekt enthält das Skript für die Generierung der Bundle-Asset an.
2. Erstellen Sie einen neuen "gameobject".
3. Der Name der basierend auf dem Inhalt "gameobject".
4. Klicken Sie im Bereich mit den Inspektor klicken Sie auf "Komponente hinzufügen", und fügen Sie "Box-Collider" hinzu. 

   ![Klicken Sie im Bereich mit den Inspektor klicken Sie auf "Komponente hinzufügen", und fügen Sie "Box-Collider" hinzu](images/holosketch-10a-assetbundles-1000px.png)
   
   ![Klicken Sie in den Inspektor-Bereich klicken Sie auf "Komponente hinzufügen", und fügen Sie 'Box-Collider' #2](images/holosketch-10b-assetbundles-1000px.png)

5. Importieren Sie FBX-3D-Datei, indem Sie in den Projektbereich ziehen.
6. Ziehen Sie das Objekt in den Bereich für die Hierarchie **unter Ihrer neuen "gameobject"**.

   ![Ziehen Sie das Objekt in den Bereich der Hierarchie unter Ihrem neuen "gameobject"](images/holosketch-12-assetbundles-1000px.png)

7. Passen Sie die Dimension "collider" aus, wenn sie nicht das Objekt entspricht. Drehen Sie das Objekt, das auftreten **z-Achse**.

   ![Passen Sie "collider" Dimension aus, wenn sie nicht das Objekt entspricht.](images/holosketch-13-assetbundles-1000px.png)

8. Ziehen Sie das Objekt aus dem Bereich der Hierarchie, in das Projektfenster, **erleichtern prefab**.
9. Klicken Sie unten im Inspektor-Bereich klicken Sie auf die Dropdownliste, erstellen Sie, und weisen Sie einen neuen eindeutigen Namen. Folgende Beispiel zeigt, hinzufügen und Zuweisen von 'Brownchair' für den AssetBundle-Namen. 

   ![Am unteren Rand der Inspektor-Bereich klicken Sie auf die Dropdownliste, und weisen Sie einen neuen eindeutigen Namen.](images/holosketch-14-assetbundles-1000px.png)

10. Bereiten Sie ein Miniaturbild für das Modellobjekt vor. 
   ![Ziehen Sie ein Bild in der Projektbereich, und weisen Sie den Namen für das Objekt.](images/holosketch-15-assetbundles-1000px.png)

11. Erstellen Sie einen Ordner namens "Assetbundles" Ordner "Asset" des Unity-Projekts.

12. Wählen Sie im Menü Assets "AssetBundles erstellen", um die Datei zu generieren. 
   ![Wählen Sie im Menü Assets "AssetBundles erstellen", um die Datei zu generieren.](images/holosketch-15a-assetbundles.png)


13. **Hochladen Sie die generierte Datei wird in den /Files/Documents/HoloSketch-Ordner in OneDrive.** Laden Sie nur die Asset_unique_name-Datei hoch. Sie müssen nicht Manifestdateien oder AssetBundles-Datei hochladen. <br>
![Hinzufügen von Dateien, Dateien/Dokumente/HoloSketch/Ordner](images/holosketch-onedriveupload-1000px.png)
![hinzugefügten 3D-Objekt in HoloSketchs OneDrive-Menü wird angezeigt](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>Wie Sie die Objekte bearbeiten

HoloSketch unterstützt die herkömmliche-Schnittstelle, die häufig verwendet wird, in 3D Software. Sie können verschieben, drehen, Skalieren die Objekte mit Gesten und eine Maus. Sie können schnell zwischen verschiedenen Modi mit Sprach- oder Tastatur wechseln.

### <a name="object-manipulation-modes"></a>Modi zum Bearbeiten von Objekt

![Wie Sie die Objekte bearbeiten](images/holosketch-image-06-1000px.png)<br>
*Wie Sie die Objekte bearbeiten*

### <a name="contextual-and-tool-belt-menus"></a>Menüs Kontext- und Toolsammlung

**Verwenden im Kontextmenü**

Doppelte Tippen Sie auf die über das Kontextmenü zu öffnen. 

Menüelemente:
* **Layout-Oberfläche:** Dies ist eine 3D-Rastersystem, können Sie das Layout mehrerer Objekte und diese als Gruppe verwalten. Double-tippbewegung auf der Layout-Oberfläche, um diese Objekte hinzuzufügen.
* **Primitive Typen:** Verwenden Sie Cubes, die Kugeln, Touren und Kegel für massing Studien.
* **OneDrive:** Öffnen Sie die OneDrive-Menü zum Importieren von Objekten.
* **Hilfe:** Zeigt Hilfe an.

![Kontextmenü](images/holosketch-image-07.png)<br>
*Kontextmenü*

**Verwenden das Tool Belt-Menü**

Verschieben, drehen, skalieren, speichern und Laden Szene im Tool Belt-Menü verfügbar sind. 

## <a name="using-keyboard-gestures-and-voice-commands"></a>Mithilfe der Tastatur, Gesten und Sprachbefehle

![Tastatur, Gesten und Sprachbefehle](images/holosketch-image-08-1000px.png)<br>
*Tastatur, Gesten und Sprachbefehle*

## <a name="download-the-app"></a>Die app herunterladen

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Herunterladen Sie und installieren Sie die app HoloSketch kostenlos aus dem Microsoft Store</a>
</td>
</tr>
</table>

## <a name="known-issues"></a>Bekannte Probleme
* Erstellung von Medienobjekten Bundle wird derzeit unterstützt, mit **Unity Version 5.4.5f1.**
* Abhängig von der Menge der Daten in Ihrem OneDrive kann die app angezeigt, als ob er, beim Laden der OneDrive-Inhalt beendet wurde
* Speichern Sie derzeit und Last-Funktion unterstützt nur primitive Objekte
* Text, Audio-, Video- und Foto-Menüs sind im Kontextmenü deaktiviert.
* Die entsprechende Schaltfläche, auf das Menü "Toolsammlung" löscht die Manipulation gizmos

## <a name="sharing-your-sketches"></a>Freigeben Ihrer Skizzen

Sie können die videoaufzeichnung-Funktion in HoloLens verwenden, indem mit dem Text "Hey Cortana, Aufnahme starten/beenden". Drücken Sie die Volume-Schlüssel zusammen, um einen Überblick über Ihre Sketch werden nach oben/unten aus.

## <a name="about-the-authors"></a>Über die Autoren

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>UX-Designer @Microsoft</td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><b>Patrick Sebring</b><br>Entwickler @Microsoft</td>
</tr>
</table> 
