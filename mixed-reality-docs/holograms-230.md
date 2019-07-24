---
title: Räumliche 230-räumliche Zuordnung
description: Befolgen Sie diese exemplarische Vorgehensweise für die Code Erstellung mithilfe von Unity, Visual Studio und hololens, um die Details der Konzepte räumlicher Zuordnung kennenzulernen.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, Tutorial, räumliche Zuordnung, Oberflächenrekonstruktion, Mesh
ms.openlocfilehash: ed58676a0fda660cc6b4c197239aeb53166baa4d
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993563"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.

<br>

# <a name="mr-spatial-230-spatial-mapping"></a>Räumliche Daten 230: Räumliche Zuordnung

[Räumliche Zuordnung](spatial-mapping.md) kombiniert die reale und die virtuelle Welt zusammen, indem Hologramme über die Umgebung vermittelt werden. Im räumlichen 230 (Project Planetarium) erfahren Sie Folgendes:

* Scannen Sie die Umgebung, und übertragen Sie Daten aus den hololens auf den Entwicklungs Computer.
* Entdecken Sie Shader, und erfahren Sie, wie Sie Sie zum Visualisieren Ihres Speicherplatzes verwenden können.
* Unterbrechen Sie das Raum Netz mithilfe der Mesh-Verarbeitung in einfache Ebenen.
* Gehen Sie über die in den [Grundlagen 101](holograms-101.md)erlernten Platzierungs Techniken hinaus, und geben Sie Feedback darüber an, wo ein – Hologramm in der Umgebung platziert werden kann.
* Entdecken Sie die Auswirkungen auf die Okklusion. wenn sich Ihr – Hologramm hinter einem realen Objekt befindet, können Sie es dennoch mit der x-ray-Vision sehen!

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>Räumliche Daten 230: Räumliche Zuordnung</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Bevor Sie beginnen

### <a name="prerequisites"></a>Vorraussetzungen

* Ein Windows 10-PC, der mit den richtigen [installierten Tools](install-the-tools.md)konfiguriert ist.
* Einige Grund C# Legende Programmiermöglichkeiten.
* Sie sollten die [Grundlagen von 101](holograms-101.md)abgeschlossen haben.
* Ein hololens-Gerät, das [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode)ist.

### <a name="project-files"></a>Projektdateien

* Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) , die für das Projekt erforderlich sind. Erfordert Unity 2017,2 oder höher.
  * Wenn Sie weiterhin Unity 5,6-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).
  * Wenn Sie weiterhin Unity 5,5-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).
  * Wenn Sie weiterhin Unity 5,4-Unterstützung benötigen, verwenden Sie [Diese Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).
* Deinstallieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht zugänglichen Speicherort.

>[!NOTE]
>Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).

### <a name="notes"></a>Hinweise

* "Enable nur eigenen Code" muss in Visual Studio unter Extras > Optionen > Debuggen*deaktiviert (deaktiviert*) werden, um Breakpoints im Code zu erreichen.

## <a name="unity-setup"></a>Unity-Setup

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* Starten Sie **Unity**.
* Wählen Sie **neu** aus, um ein neues Projekt zu erstellen.
* Nennen Sie das Projekt **Planetarium**.
* Überprüfen Sie, ob die Einstellung **3D** ausgewählt ist.
* Klicken Sie auf **Projekt erstellen**.
* Nachdem Unity gestartet wurde, wechseln Sie zu **Edit > Project Settings > Player**.
* Suchen Sie im **Inspektor** -Panel nach dem grünen **Windows Store** -Symbol, und wählen Sie es aus.
* Erweitern Sie **andere Einstellungen**.
* Aktivieren Sie im Abschnitt " **Rendering** " die Option " **Virtual Reality supported** ".
* Vergewissern Sie sich, dass **Windows Holographic** in der Liste der **Virtual Reality sdert**angezeigt wird. Wenn nicht, klicken Sie **+** auf die Schaltfläche unten in der Liste, und wählen Sie **Windows Holographic**aus.
* Erweitern Sie **Veröffentlichungs Einstellungen**.
* Überprüfen Sie im Abschnitt **Funktionen** die folgenden Einstellungen:
    * Internetclientserver
    * Privatenetworkclientserver
    * Mikrofon
    * Spatialperception
* Wechseln Sie zu **Edit > Project Settings > Quality**
* Wählen Sie im **Inspektor** -Panel unter dem Windows Store-Symbol den schwarzen Dropdown Pfeil unter der Zeile "Default" aus, und ändern Sie die Standardeinstellung in **sehr niedrig**.
* Wechseln Sie zu **Assets > Importieren Sie das Paket > benutzerdefiniertes Paket**.
* Navigieren Sie zum Ordner " **. ..\holographicacademy-holograms-230-spatialmapping\starting** ".
* Klicken Sie auf " **Planetarium. unitypackage**".
* Klicken Sie auf **Öffnen**.
* Ein Fenster zum **Importieren von Unity-Paketen** sollte angezeigt werden. Klicken Sie auf die Schaltfläche **importieren** .
* Warten Sie, bis Unity alle Assets importiert, die wir benötigen, um dieses Projekt abzuschließen.
* Löschen Sie im **Hierarchie** Panel die **Hauptkamera**.
* Suchen Sie im **Projekt** Panel im Ordner **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** das **Hauptkamera** Objekt.
* Ziehen Sie die **Hauptkamera** -vorfab per Drag & Drop in den Bereich **Hierarchie** .
* Löschen Sie im **Hierarchie** Panel das **direktionale Light** -Objekt.
* Suchen Sie im **Projekt** Panel im Ordner **holograms** das **Cursor** Objekt.
* Ziehen Sie & den **Cursor** vorfab in der **Hierarchie**ablegen.
* Wählen Sie im Bereich **Hierarchie** das **Cursor** Objekt aus.
* Klicken Sie im **Inspektor** -Panel auf die Dropdown Liste **Ebene** , und wählen Sie **Ebenen bearbeiten...** aus.
* Benennen Sie die **Benutzerebene 31** als "**spatialmapping**".
* Speichern Sie die neue Szene: **Datei > Szene speichern unter...**
* Klicken Sie auf **neuer Ordner** , und benennen Sie die Ordner **Szenen**.
* Benennen Sie die Datei "**Planetarium**", und speichern Sie Sie im Ordner **Szenen** .

## <a name="chapter-1---scanning"></a>Kapitel 1: Scannen

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

**Ziele**
* Erfahren Sie mehr über den surfaceobserver und wie sich seine Einstellungen auf die Leistung und Leistung auswirken.
* Erstellen Sie eine Raum Überprüfung, um die Netze Ihres Raums zu erfassen.

**Anweisungen**
* Suchen Sie im Ordner " **Projekt** Panel **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** " nach der **spatialmapping** -vorfab.
* Ziehen Sie & ziehen Sie die vorfab **spatialmapping** in den Bereich **Hierarchie** .

**Build und Bereitstellung (Teil 1)**
* Wählen Sie in Unity **Datei >** Buildeinstellungen aus.
* Klicken Sie auf **offene Szenen hinzufügen** , um dem Build die **Planetarium** -Szene hinzuzufügen.
* Wählen Sie in der Liste **Plattform** **universelle Windows-Plattform** aus, und klicken Sie auf **Plattform wechseln**.
* Legen Sie **SDK** auf **Universal 10** und **UWP Build Type** auf **D3D**fest.
* Überprüfen Sie **Unity C# -Projekte**.
* Klicken Sie auf **Erstellen**.
* Erstellen Sie einen **neuen Ordner** mit dem Namen "App".
* Klicken Sie einfach auf den **App** -Ordner.
* Klicken Sie auf die Schaltfläche **Ordner auswählen** .
* Wenn Unity erstellt wurde, wird ein Datei-Explorer-Fenster angezeigt.
* Doppelklicken Sie auf den **App** -Ordner, um ihn zu öffnen.
* Doppelklicken Sie auf " **Planetarium. sln** ", um das Projekt in Visual Studio zu laden.
* Verwenden Sie in Visual Studio die obere Symbolleiste, um die Konfiguration in **Release**zu ändern.
* Ändern Sie die Plattform in **x86**.
* Klicken Sie auf den Dropdown Pfeil rechts neben "lokaler Computer", und wählen Sie **Remote Computer**aus.
* Geben Sie die [IP-Adresse Ihres Geräts](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) in das Adressfeld ein, und ändern Sie den Authentifizierungsmodus in **Universal (unverschlüsseltes Protokoll)** .
* Klicken Sie auf **Debuggen > Starten ohne Debugging** , oder drücken Sie **STRG + F5**.
* Sehen Sie sich den **Ausgabe** Bereich in Visual Studio zum Erstellen und Bereitstellen des Status an.
* Nachdem Ihre APP bereitgestellt wurde, durchlaufen Sie den Raum. Sie sehen die umgebenden Oberflächen, die durch schwarze und weiße Draht Modell-Meshes abgedeckt werden.
* Überprüfen Sie Ihre Umgebung. Achten Sie darauf, Wände, Oberflächen und Fußböden zu betrachten.

**Erstellen und bereitstellen (Teil 2)**

Betrachten wir nun, wie sich die räumliche Zuordnung auf die Leistung auswirken kann.
* Wählen Sie in Unity **Fenster > Profiler**aus.
* Klicken Sie auf **Profiler > GPU hinzufügen**.
* Klicken Sie **> <Enter IP>auf aktiver Profiler** .
* Geben Sie die **IP-Adresse** der hololens ein.
* Klicken Sie auf **Verbinden**.
* Beachten Sie die Anzahl der Millisekunden, die die GPU zum Rendering eines Frames benötigt.
* Verhindern, dass die Anwendung auf dem Gerät ausgeführt wird.
* Kehren Sie zu Visual Studio zurück, und öffnen Sie **SpatialMappingObserver.cs**. Sie finden ihn im Ordner "holotoolkit\spatialmapping" des Projekts "Assembly-CSharp" (Universal Windows).
* Suchen Sie die Funktion " **Awa()** ", und fügen Sie die folgende Codezeile hinzu: **"Zanglespercubicmeter" = 1200;**
* Stellen Sie das Projekt erneut auf Ihrem Gerät bereit, und stellen Sie dann **erneut eine Verbindung mit dem Profiler**her. Beachten Sie die Änderung in der Anzahl von Millisekunden zum Rendering eines Frames.
* Verhindern, dass die Anwendung auf dem Gerät ausgeführt wird.

**Speichern und laden in Unity**

Schließlich speichere ich unser Raum Netz und lade es in Unity.
* Kehren Sie zu Visual Studio zurück, und entfernen Sie die Zeile " **tranglespercubicmeter** ", die Sie in der Funktion " **Awa()** " im vorherigen Abschnitt hinzugefügt haben.
* Stellen Sie das Projekt erneut auf Ihrem Gerät bereit. Wir sollten nun mit **500** Dreiecke pro Kubikmeter ausführen.
* Öffnen Sie einen Browser, und geben Sie die IP-Adresse des hololens ein, um zum **Windows-Geräte Portal**zu navigieren.
* Wählen Sie die Option **3D-Ansicht** im linken Bereich aus.
* Klicken Sie unter **Oberflächen wieder** Herstellung auf die Schaltfläche **Aktualisieren** .
* Sehen Sie sich an, wie die Bereiche, die Sie auf den hololens überprüft haben, im Anzeige Fenster angezeigt werden.
* Zum Speichern des Raum Scans klicken Sie auf die Schaltfläche **Speichern** .
* Öffnen Sie den Ordner " **Downloads** ", um das gespeicherte Raummodell " **srmesh. obj**" zu finden.
* Kopieren Sie " **srmesh. obj** " in den Ordner " **Assets** " Ihres Unity-Projekts.
* Wählen Sie in Unity das **spatialmapping** -Objekt im **Hierarchie** Panel aus.
* Suchen Sie die Komponente **Objekt Oberflächen Beobachter (Skript)** .
* Klicken Sie auf den Kreis rechts neben der Eigenschaft **Raummodell** .
* Suchen und wählen Sie das **srmesh** -Objekt aus, und schließen Sie das Fenster.
* Vergewissern Sie sich, dass die Eigenschaft **Raummodell** im **Inspektor** -Panel nun auf **srmesh**festgelegt ist.
* Drücken Sie die **Wiedergabe** Schaltfläche, um den Vorschaumodus von Unity einzugeben.
* Die spatialmapping-Komponente lädt die Netzen aus dem gespeicherten Raummodell, sodass Sie Sie in Unity verwenden können.
* Wechseln Sie zur Ansicht **Szene** , um das gesamte mit dem Draht Modell-Shader angezeigte Raummodell anzuzeigen.
* Drücken Sie erneut die **Wiedergabe** Schaltfläche, um den Vorschaumodus zu beenden

**HINWEIS:** Wenn Sie das nächste Mal in Unity in den Vorschaumodus wechseln, wird das gespeicherte Raum Netz standardmäßig geladen.

## <a name="chapter-2---visualization"></a>Kapitel 2: Visualisierung

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

**Ziele**
* Erfahren Sie mehr über die Grundlagen von Shaders.
* Visualisieren Sie Ihre Umgebung.

**Anweisungen**
* Wählen Sie im Bereich **Hierarchie** der Unity das **spatialmapping** -Objekt aus.
* Suchen Sie im **Inspektor** -Panel die Komponente räumlicher zuordnungsmanager **(Skript)** .
* Klicken Sie auf den Kreis rechts neben der Eigenschaft **Oberflächen Material** .
* Suchen und wählen Sie das Material **bluelinesonwalls** aus, und schließen Sie das Fenster.
* Doppelklicken Sie im **Projekt** Panel Ordner **Shaders** auf **bluelinesonwalls** , um den Shader in Visual Studio zu öffnen.
* Dies ist ein einfacher Pixel-Shader (Vertex zu Fragment), der die folgenden Aufgaben durchführt:
    1. Konvertiert den Speicherort eines Scheitel Punkts in den Raum.
    2. Überprüft den normalen Scheitelpunkt, um zu bestimmen, ob ein Pixel vertikal ist.
    3. Legt die Farbe des Pixels zum Rendern fest.

**Erstellen und bereitstellen**
* Kehren Sie zu Unity zurück, und drücken Sie die **Wiedergabe** Taste, um den Vorschau
* Blaue Linien werden auf allen vertikalen Oberflächen des Raum Netzes gerendert (das automatisch aus den gespeicherten Scandaten geladen wird).
* Wechseln Sie zur Registerkarte **Szene** , um die Ansicht des Raums anzupassen und zu sehen, wie das gesamte Raum Netz in Unity angezeigt wird.
* Suchen Sie im **Projekt** Panel den Ordner **Material** , und wählen Sie das Material **bluelinesonwalls** aus.
* Ändern Sie einige Eigenschaften, und sehen Sie, wie die Änderungen im Unity-Editor angezeigt werden.
    * Passen Sie im **Inspektor** -Panel den **linescale** -Wert an, damit die Linien dicker oder dünner angezeigt werden.
    * Passen Sie im **Inspektor** -Panel den Wert von **linespermeter** an, um zu ändern, wie viele Zeilen auf jeder Wand angezeigt werden.
* Klicken Sie erneut auf **abspielen** , um den Vorschaumodus zu beenden
* Erstellen Sie die hololens und stellen Sie Sie bereit, und beobachten Sie, wie das Shader-Rendering auf realen Oberflächen erscheint.

Unity bietet eine hervorragende Vorschau der Materialien, aber es ist immer eine gute Idee, das Rendering im Gerät auszuchecken.

## <a name="chapter-3---processing"></a>Kapitel 3: verarbeiten

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

**Ziele**
* Erlernen Sie Techniken zum Verarbeiten räumlicher Mapping-Daten für die Verwendung in Ihrer Anwendung.
* Analysieren räumlicher Zuordnungsdaten zum Suchen von Ebenen und Entfernen von Dreiecken
* Verwenden Sie für die – Hologramm-Platzierung Flächen.

**Anweisungen**
* Suchen Sie im **Projekt** Panel von Unity im Ordner **holograms** das **spatialprocessing** -Objekt.
* Ziehen Sie & das **spatialprocessing** -Objekt in den Bereich **Hierarchie** ablegen.

Das spatialprocessing-präfab umfasst Komponenten für die Verarbeitung der räumlichen Zuordnungsdaten. **SurfaceMeshesToPlanes.cs** findet und generiert auf der Grundlage der räumlichen Zuordnungsdaten Ebenen. Wir verwenden in unserer Anwendung Flächen zum Darstellen von Wänden, Flächen und Oberflächen. Diese vorfab umfasst auch **RemoveSurfaceVertices.cs** , mit dem Vertices aus dem räumlichen zuordnungsmesh entfernt werden können. Dies kann verwendet werden, um Löcher im Mesh zu erstellen oder um überzählige Dreiecke zu entfernen, die nicht mehr benötigt werden (da stattdessen Flächen verwendet werden können).
* Suchen Sie im **Projekt** Panel von Unity im Ordner **holograms** das **spacecollection** -Objekt.
* Ziehen Sie das **spacecollection** -Objekt per Drag & Drop in den Bereich **Hierarchie** .
* Wählen Sie im Bereich **Hierarchie** das **spatialprocessing** -Objekt aus.
* Suchen Sie im **Inspektor** -Panel die Komponente " **Play Space Manager (Skript)** ".
* Doppelklicken Sie auf **PlaySpaceManager.cs** , um es in Visual Studio zu öffnen.

PlaySpaceManager.cs enthält anwendungsspezifischen Code. Wir werden diesem Skriptfunktionen hinzufügen, um folgendes Verhalten zu ermöglichen:
1. Die Erfassung räumlicher Zuordnungsdaten wird beendet, wenn das Überprüfungs Zeit Limit (10 Sekunden) überschritten wird.
2. Verarbeiten Sie die räumlichen Mapping-Daten:
    1. Verwenden Sie surfacetten, um eine einfachere Darstellung der Welt als Flächen (Wände, Flächen, Oberflächen usw.) zu erstellen.
    2. Verwenden Sie removesurfacevertices, um Oberflächen überdreitel zu entfernen, die innerhalb der Ebenen liegen.
3. Generieren Sie eine Sammlung von holograms auf der ganzen Welt, und platzieren Sie Sie in der Nähe des Benutzers auf der Wand-und Bodenebene.

Führen Sie die in PlaySpaceManager.cs markierten Codierungs Übungen aus, oder ersetzen Sie das Skript durch die fertige Projekt Mappe aus folgendem:

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by 
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

**Erstellen und bereitstellen**
* Drücken Sie vor der Bereitstellung in den hololens in Unity die **Wiedergabe** Schaltfläche, um den Wiedergabemodus einzugeben.
* Nachdem das Raum Netz aus der Datei geladen wurde, warten Sie 10 Sekunden, bevor die Verarbeitung im Netz für räumliche Zuordnung gestartet wird.
* Wenn die Verarbeitung fertiggestellt ist, werden die flächenflächen, Wände, Ceiling usw. angezeigt.
* Nachdem alle Ebenen gefunden wurden, sollte ein Sonnensystem in einer Tabelle mit der Nähe der Kamera angezeigt werden.
* In der Nähe der Kamera sollten auch zwei Poster angezeigt werden. Wechseln Sie zur Registerkarte **Szene** , wenn Sie im **Spiel** Modus nicht angezeigt werden.
* Drücken Sie erneut die **Wiedergabe** Schaltfläche, um den Wiedergabemodus zu beenden
* Erstellen und stellen Sie die hololens wie gewohnt bereit.
* Warten Sie, bis die Überprüfung und Verarbeitung der räumlichen Mapping-Daten durchgeführt wurden.
* Wenn Sie die Ebenen sehen, finden Sie heraus, das Sonnensystem und die Poster in ihrer Welt zu finden.

## <a name="chapter-4---placement"></a>Kapitel 4: Platzierung

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

**Ziele**
* Stellen Sie fest, ob ein – Hologramm auf eine Oberfläche passt.
* Geben Sie dem Benutzer Feedback, wenn ein – Hologramm in eine Oberfläche passt oder nicht.

**Anweisungen**
* Wählen Sie im Bereich **Hierarchie** der Unity das **spatialprocessing** -Objekt aus.
* Suchen Sie im **Inspektor** -Panel nach der Komponente, die an die Flächen **(Skript)** ausgerichtet ist.
* Ändern Sie die Eigenschaft **zeichnen-Ebenen** in **nichts** , um die Auswahl zu löschen.
* Ändern Sie die Eigenschaft **zeichnen-Ebenen** in **Wall**, sodass nur die Zeichen Wandflächen gerendert werden.
* Doppelklicken Sie im **Projekt** Panel im Ordner **Skripts** auf **Placeable.cs** , um es in Visual Studio zu öffnen.

Das  ersetzbare Skript ist bereits an das Poster-und Projektions Feld angefügt, die nach Abschluss der Flächensuche erstellt werden. Wir müssen lediglich Code auskommentieren, und mit diesem Skript wird Folgendes erreicht:
1. Stellen Sie fest, ob ein – Hologramm auf eine Oberfläche passt, indem Sie das Raycasting aus dem Mittelpunkt und vier Ecken des umgebenden Cubes anfügen.
2. Überprüfen Sie die Oberflächen normale, um zu ermitteln, ob Sie für das – Hologramm reibungslos genug ist.
3. Rendering eines umgebenden Cubes um das Hologramm, um die tatsächliche Größe beim Platzieren anzuzeigen.
4. Wandeln Sie einen Schatten unter/hinter dem – Hologramm um, um anzuzeigen, wo er auf der Etage/Wand platziert wird.
5. Renderden Schatten als rot, wenn das – Hologramm nicht auf der Oberfläche platziert werden kann, oder grün, wenn dies möglich ist.
6. Richten Sie das Hologramm erneut an den Surface-Typ (vertikal oder horizontal) aus, zu dem er eine Affinität hat.
7. Platzieren Sie das – Hologramm reibungslos auf der ausgewählten Oberfläche, um das Springen oder Ausrichtungs Verhalten zu vermeiden.

Kommentieren Sie den gesamten Code in der Codierungs Übung unten aus, oder verwenden Sie diese abgeschlossene Lösung in **Placeable.cs**:

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.    
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The aligntoVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.        
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

**Erstellen und bereitstellen**
* Erstellen Sie wie zuvor das Projekt, und stellen Sie es auf den hololens bereit.
* Warten Sie, bis die Überprüfung und Verarbeitung der räumlichen Mapping-Daten durchgeführt wurden.
* Wenn das Sonnensystem angezeigt wird, schauen Sie sich das folgende Projektions Feld an, und führen Sie eine Auswahl Geste aus, um es zu verschieben. Während das Projektions Feld ausgewählt ist, wird ein umschließender Cube um das Projektions Feld sichtbar.
* Bewegen Sie den Blick an eine andere Position im Raum. Das Projektions Feld sollte dem Blick folgen. Wenn der Schatten unterhalb des Projektions Felds rot angezeigt wird, können Sie das Hologramm nicht auf dieser Oberfläche platzieren. Wenn der Schatten unterhalb der Projektionsfläche grün wird, können Sie das – Hologramm durch Ausführen einer weiteren Auswahl Bewegung platzieren.
* Suchen und wählen Sie eines der Holographic-Poster an einer Wand aus, um es an einen neuen Speicherort zu verschieben. Beachten Sie, dass Sie das Poster nicht auf der Boden-oder Ceiling-Oberfläche platzieren können und dass es bei der Navigation ordnungsgemäß auf die einzelnen Wände ausgerichtet bleibt.

## <a name="chapter-5---occlusion"></a>Kapitel 5-Okklusion

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

**Ziele**
* Stellen Sie fest, ob ein – Hologramm durch das räumliche Mapping-Mesh verdeckt wird.
* Anwenden verschiedener Okklusions Techniken, um einen Spaß Effekt zu erzielen.

**Anweisungen**

Zuerst gestatten wir dem räumlichen zuordnungsmesh, andere Hologramme zu okzieren, ohne die wirkliche Welt zu verzieren:
* Wählen Sie im Bereich **Hierarchie** das **spatialprocessing** -Objekt aus.
* Suchen Sie im **Inspektor** -Panel die Komponente " **Play Space Manager (Skript)** ".
* Klicken Sie auf den Kreis rechts neben der Eigenschaft **sekundäres Material** .
* Suchen und wählen Sie das **oksions** Material aus, und schließen Sie das Fenster.

Als Nächstes fügen wir ein spezielles Verhalten zur Erde hinzu, sodass es eine blaue Hervorhebung hat, wenn es von einem anderen – Hologramm (wie der Sun) oder durch das räumliche zuordnungsmesh wird:
* Erweitern Sie im **Projekt** Panel im Ordner **holograms** das Objekt " **Solar System** ".
* Klicken Sie auf **Erde**.
* Suchen Sie im **Inspektor** -Panel nach dem Material der Erde (untere Komponente).
* Ändern Sie in der **Shader-Dropdown-** Datei den Shader in **benutzerdefiniertes > oksionrim**. Dadurch wird eine blaue Hervorhebung um die Erde herum gerendert, wenn Sie von einem anderen Objekt verdeckt wird.

Zum Schluss aktivieren wir einen x-ray-Vision-Effekt für Planeten in unserem Sonnensystem. Wir müssen **PlanetOcclusion.cs** (im Ordner scripz\solarsystem) bearbeiten, um Folgendes zu erreichen:
1. Stellen Sie fest, ob ein Planet von der spatialmapping-Schicht (Raum-und Flächen) verdeckt wird.
2. Zeigt die Draht Modell-Darstellung eines Planeten an, wenn er von der spatialmapping-Ebene verdeckt wird.
3. Blenden Sie die Draht Modell-Darstellung eines Planeten aus, wenn er nicht durch die spatialmapping-Ebene blockiert wird.

Befolgen Sie die Codierungs Übung in PlanetOcclusion.cs, oder verwenden Sie die folgende Lösung:

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

**Erstellen und bereitstellen**
* Erstellen Sie die Anwendung wie üblich, und stellen Sie Sie in hololens bereit.
* Warten Sie, bis die Überprüfung und Verarbeitung der räumlichen Mapping-Daten fertig sind. (es sollten blaue Linien auf den Wänden angezeigt werden.)
* Suchen Sie das Projektions Feld des Sonnensystems, und wählen Sie es aus, und legen Sie dann das Kontrollkästchen neben einer Wand oder hinter einem Zählers fest.
* Sie können die grundlegende oksion anzeigen, indem Sie hinter den Oberflächen auf dem Poster oder der Projektionsfläche ausblenden.
* Suchen Sie nach der Erde. es sollte ein blauer Hervorhebungs Effekt auftreten, wenn Sie auf ein anderes Hologramm oder eine Oberfläche zurückgeht.
* Beobachten Sie, wie sich die Planeten hinter der Wand oder anderen Oberflächen im Raum bewegen. Sie verfügen nun über eine x-ray-Vision und können Ihre Draht Modell-Skelette sehen.

## <a name="the-end"></a>Das Ende

Herzlichen Glückwunsch! Sie haben jetzt die **räumliche 230 von abgeschlossen: Räumliche Zuordnung**.
* Sie wissen, wie Sie Ihre Umgebung scannen und räumliche Mapping-Daten in Unity laden.
* Sie verstehen die Grundlagen von Shadern und die Art und Weise, wie Materialien zum erneuten visualisieren der Welt eingesetzt werden können.
* Sie haben neue Verarbeitungstechniken zum Suchen von Ebenen und zum Entfernen von Dreiecken aus einem Mesh gelernt.
* Sie konnten Hologramme an Oberflächen verschieben und platzieren, die sinnvoll waren.
* Sie haben verschiedene Okklusions Techniken erlebt und die Leistungsfähigkeit der x-ray-Vision genutzt!
