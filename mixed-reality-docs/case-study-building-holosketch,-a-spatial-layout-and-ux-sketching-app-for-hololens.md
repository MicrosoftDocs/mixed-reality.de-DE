---
title: 'Fallstudie: Erstellen von holosketch, ein räumliches Layout und eine UX-skizzieren-App für hololens'
description: Holosketch ist ein auf dem Gerät räumliches Layout und UX-skeshottool für hololens, das Sie bei der Erstellung von Holographic-Erfahrungen unterstützt.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Holosketch, hololens, Windows Mixed Reality, Sketching, App
ms.openlocfilehash: d6d22aae7709bcc1a33b142a100d1a0f9645d3cc
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436943"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>Fallstudie: Erstellen von holosketch, ein räumliches Layout und eine UX-skizzieren-App für hololens

Holosketch ist ein auf dem Gerät räumliches Layout und UX-skeshottool für hololens, das Sie bei der Erstellung von Holographic-Erfahrungen unterstützt. Holosketch funktioniert mit einer gekoppelten Bluetooth-Tastatur und-Maus sowie mit Gesten-und Sprachbefehlen. Der Zweck von holosketch besteht darin, ein einfaches UX-Layouttool für die schnelle Visualisierung und Iterationen bereitzustellen.

![holosketch: ein räumliches Layout und eine UX-skizzieren-App für hololens.](images/holosketch-image-01-640px.png)<br>
*Holosketch: räumliche Layout und UX-App für hololens*

![ein einfaches UX-Layouttool für die schnelle Visualisierung und Iterationen.](images/holosketch-image-02.png)<br>
*Ein einfaches UX-Layouttool für die schnelle Visualisierung und Iterationen*

## <a name="features"></a>Features

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>Grundtypen für schnelles Studium und Skalierung von Prototypen

![Verwenden primitiver Formen](images/holosketch-primitives-giphy.gif)

Verwenden Sie primitive Formen für schnelle und skalierbare Prototypen.

### <a name="import-objects-through-onedrive"></a>Importieren von Objekten über onedrive

![Importieren von Objekten](images/holosketch-importobjects-giphy.gif)

Importieren Sie PNG/JPG-Images oder 3D-b-Objekte (erfordert Verpacken in Unity) in den gemischten Reality-Raum über onedrive.

### <a name="manipulate-objects"></a>Objekte bearbeiten

![Bearbeiten von Objekten](images/manipulate-objects-640px.jpg)

Bearbeiten Sie Objekte (verschieben/drehen/Skalieren) mit einer vertrauten 3D-Objektschnittstelle.

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>Bluetooth-, Maus-/Tastatur-, Gesten-und Sprachbefehle

![unterstützt Bluetooth](images/supports-bluetooth-640px.jpg)

Holosketch unterstützt Bluetooth-Maus/Tastatur, Gesten und Sprachbefehle.

## <a name="background"></a>Hintergrund

### <a name="importance-of-experiencing-your-design-in-the-device"></a>Wichtigkeit der Erfahrung des Entwurfs im Gerät

Wenn Sie etwas für hololens entwerfen, ist es wichtig, dass Sie Ihr Design auf dem Gerät haben. Eine der größten Herausforderungen beim Mixed Reality-App-Entwurf besteht darin, dass es schwierig ist, den Sinn von Skalierbarkeit, Position und Tiefe zu erzielen, insbesondere durch herkömmliche 2D-Skizzen.

### <a name="cost-of-2d-based-communication"></a>Kosten der 2D-basierten Kommunikation

Zum effektiven kommunizieren von UX-Flows und-Szenarien für andere kann es sein, dass ein Designer viel Zeit für die Erstellung von Assets mit herkömmlichen 2D-Tools wie Illustrator, Photoshop und PowerPoint aufwenden könnte. Diese 2D-Entwürfe erfordern häufig zusätzlichen Aufwand, Sie in 3D zu konvertieren. Einige Ideen gehen bei dieser Übersetzung von 2D in 3D verloren.

### <a name="complex-deployment-process"></a>Komplexer Bereitstellungs Prozess

Da gemischte Realität eine neue Canvas für uns ist, umfasst Sie viele Entwurfs Iterationen und-Testversionen und-Fehler. Für Designer, die mit Tools wie Unity und Visual Studio nicht vertraut sind, ist es nicht einfach, etwas in hololens zu platzieren. In der Regel müssen Sie den folgenden Prozess durchlaufen, um Ihre 2D/3D-Grafik im Gerät anzuzeigen. Dies war eine große Barriere für Entwickler, die Ideen und Szenarios schnell durchlaufen.

![komplexer Bereitstellungs Prozess](images/holosketch-image-03-1000px.png)<br>
*Bereitstellungs Prozess*

### <a name="simplified-process-with-holosketch"></a>Vereinfachter Prozess mit holosketch

Mit holosketch wollten wir diesen Prozess vereinfachen, ohne die Entwicklungs Tools und Geräte Portal Kopplung einzubeziehen. Mithilfe von onedrive können Benutzer problemlos 2D/3D-Assets in hololens einfügen.

![vereinfachten Prozess mit holosketch](images/holosketch-image-04-1000px.png)<br>
*Vereinfachter Prozess mit holosketch*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>Fördern von dreidimensionalen Entwurfs Gedanken und-Lösungen

Wir dachten, dass dieses Tool Entwicklern die Möglichkeit bietet, Lösungen in einem wirklich dreidimensionalen Raum zu untersuchen und nicht in 2D stecken zu müssen. Sie müssen sich keine Gedanken über das Erstellen eines 3D-Hintergrunds für die Benutzeroberfläche machen, da der Hintergrund im Fall von hololens die wirkliche Welt ist. Holosketch öffnet eine Methode, mit der Designer den 3D-Entwurf auf hololens problemlos untersuchen können.

## <a name="get-started"></a>Erste Schritte

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>Importieren von 2D-images (JPG/PNG) in holosketch

* Laden Sie JPG/PNG-Bilder in ihren onedrive-Ordner "Documents/holosketch" hoch.
* Über das onedrive-Menü in holosketch können Sie das Bild auswählen und in der Umgebung platzieren.

![Importieren von 2D-images](images/import-2d-images-1000px.jpg)<br>
*Importieren von Bildern und 3D-Objekten über onedrive*

### <a name="how-to-import-3d-objects-into-holosketch"></a>Importieren von 3D-Objekten in holosketch

Führen Sie vor dem Hochladen in ihren onedrive-Ordner die folgenden Schritte aus, um die 3D-Objekte in ein Unity-Ressourcen Bündel zu packen. Mithilfe dieses Prozesses können Sie Ihre Dateien mit dem Namen "f" und "obj" aus 3D-Software importieren, z. b. Maya, Kino 4D und Microsoft Paint 3D.

>[!IMPORTANT]
>Derzeit wird die Erstellung von Asset-Paketen mit Unity-Version 5.4.5 F1 unterstützt.

1. Das Unity-Projekt ["AssetBunlder_Unity"](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity)herunterladen und öffnen. Dieses Unity-Projekt enthält das Skript für die Bundle-Asset-Generierung.
2. Erstellen Sie ein neues gameobject-Objekt.
3. Benennen Sie das gameobject basierend auf dem Inhalt.
4. Klicken Sie im Inspektor-Panel auf "Komponente hinzufügen", und fügen Sie "Box Collider" hinzu. 

   ![Klicken Sie im Inspektor-Panel auf "Komponente hinzufügen", und fügen Sie "Box Collider" hinzu.](images/holosketch-10a-assetbundles-1000px.png)
   
   ![Klicken Sie im Inspektor-Panel auf "Komponente hinzufügen", und fügen Sie den #2 "Box Collider" hinzu.](images/holosketch-10b-assetbundles-1000px.png)

5. Importieren Sie die 3D-Datei-Datei, indem Sie Sie in das Projekt Panel ziehen.
6. Ziehen Sie das Objekt in den Bereich Hierarchie **unter dem neuen gameobject**.

   ![Ziehen Sie das Objekt in den Bereich Hierarchie unter dem neuen gameobject.](images/holosketch-12-assetbundles-1000px.png)

7. Passen Sie die Collider-Dimension an, wenn Sie nicht mit dem-Objekt identisch ist. Drehen Sie das Objekt um die **Z-Achse**.

   ![Passen Sie die Collider-Dimension an, wenn Sie nicht mit dem Objekt identisch ist.](images/holosketch-13-assetbundles-1000px.png)

8. Ziehen Sie das Objekt aus dem Bereich Hierarchie in das Projekt Panel, um **es vorzu machen**.
9. Klicken Sie unten im Inspektor-Panel auf die Dropdown Liste, erstellen Sie einen neuen eindeutigen Namen, und weisen Sie ihn zu. Das folgende Beispiel zeigt das Hinzufügen und Zuweisen von "brownstuhl" für den assetbundle-Namen. 

   ![Klicken Sie im unteren Bereich des inspektorbereichs auf die Dropdown Liste, und weisen Sie einen neuen eindeutigen Namen zu.](images/holosketch-14-assetbundles-1000px.png)

10. Bereiten Sie ein Miniaturbild für das Modell Objekt vor. 
   ![ziehen Sie ein Bild in das Projekt Panel, und weisen Sie den Namen zu, der für das Objekt verwendet wird.](images/holosketch-15-assetbundles-1000px.png)

11. Erstellen Sie im Ordner "Asset" des Unity-Projekts einen Ordner mit dem Namen "assetbundles".

12. Wählen Sie im Menü Assets die Option zum Erstellen von assetbundles aus, um die Datei zu generieren. 
   Wählen Sie ![im Menü Assets die Option zum Erstellen von assetbundles aus, um die Datei zu generieren.](images/holosketch-15a-assetbundles.png)


13. **Laden Sie die generierte Datei in den Ordner/Files/Documents/HoloSketch auf onedrive hoch.** Laden Sie nur die asset_unique_name Datei hoch. Manifestressourcen oder assetbundle-Dateien müssen nicht hochgeladen werden. <br>
![Hinzufügen von Dateien zu Dateien/Dokumenten/holosketch/Ordner](images/holosketch-onedriveupload-1000px.png)
![wird das hinzugefügte 3D-Objekt im onedrive-Menü von holosketch angezeigt](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>Vorgehensweise beim Bearbeiten der Objekte

Holosketch unterstützt die herkömmliche Oberfläche, die häufig in 3D-Software verwendet wird. Sie können das Verschieben, drehen und Skalieren der Objekte mit Gesten und Maus verwenden. Sie können schnell zwischen verschiedenen Modi mit Stimme oder Tastatur wechseln.

### <a name="object-manipulation-modes"></a>Objekt Bearbeitungsmodi

![, wie die Objekte bearbeitet werden](images/holosketch-image-06-1000px.png)<br>
*Vorgehensweise beim Bearbeiten der Objekte*

### <a name="contextual-and-tool-belt-menus"></a>Kontext-und toolbandmenüs

**Verwenden des Kontextmenüs**

Doppel Tippen Sie auf, um das Kontextmenü zu öffnen. 

Menü Elemente:
* **Layoutoberfläche:** Dabei handelt es sich um ein 3D-Raster System, in dem Sie mehrere Objekte erstellen und als Gruppe verwalten können. Doppel Tippen Sie auf die layoutoberfläche, um Ihr Objekte hinzuzufügen.
* **Primitive:** Verwenden Sie Cubes, Bereiche, Zylinder und Kegel zum Durchführen von Studien.
* **Onedrive:** Öffnen Sie das onedrive-Menü, um Objekte zu importieren.
* **Hilfe:** Zeigt den Hilfe Bildschirm an.

![Kontextmenü](images/holosketch-image-07.png)<br>
*Kontextmenü*

**Verwenden des toolbandmenüs**

Verschieben, drehen, skalieren, speichern und Laden von Szenen sind im Menüband-Menü verfügbar. 

## <a name="using-keyboard-gestures-and-voice-commands"></a>Verwenden von Tastatur, Gesten und Sprachbefehlen

![Tastatur, Gesten und Sprachbefehle](images/holosketch-image-08-1000px.png)<br>
*Tastatur-, Gesten-und Sprachbefehle*

## <a name="download-the-app"></a>Herunterladen der APP

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Laden Sie die holosketch-App kostenlos herunter, und installieren Sie Sie im Microsoft Store</a>
</td>
</tr>
</table>

## <a name="known-issues"></a>Bekannte Probleme
* Derzeit wird die Erstellung von Ressourcen Paketen mit **Unity-Version 5.4.5 F1** unterstützt.
* Abhängig von der Datenmenge in Ihrem onedrive wird die APP möglicherweise so angezeigt, als ob Sie beim Laden von onedrive-Inhalten angehalten wurde.
* Zurzeit unterstützt die Funktion "Speichern und laden" nur primitive Objekte.
* Text-, Ton-, Video-und Fotomenüs sind im Kontextmenü deaktiviert.
* Die Wiedergabe Schaltfläche im Menüband-Menü löscht die Manipulation Gizmos

## <a name="sharing-your-sketches"></a>Freigeben von Skizzen

Sie können das Video Aufzeichnungs Feature in hololens verwenden, indem Sie "Hey Cortana, Start/stoppaufzeichnung" sagen. Drücken Sie die Taste nach oben/unten, um ein Bild der Skizze zu machen.

## <a name="about-the-authors"></a>Informationen zu den Autoren

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong-Yoon-Park</b><br>UX-Designer-@Microsoft</td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><b>Patrick-Bring</b><br>Entwickler @Microsoft</td>
</tr>
</table> 
