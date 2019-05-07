---
title: MR räumlich 230 - räumliche Zuordnung
description: Führen Sie diese exemplarische Vorgehensweise verwenden die Details der räumlichen Mapping-Konzepten finden Sie Unity, Visual Studio und HoloLens codieren.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Holotoolkit, Mixedrealitytoolkit, Mixedrealitytoolkit-Unity, Academy, Tutorial, räumliche Zuordnung, Surface Wiederaufbau, Netz
ms.openlocfilehash: ed58676a0fda660cc6b4c197239aeb53166baa4d
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993563"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

<br>

# <a name="mr-spatial-230-spatial-mapping"></a>MR Spatial 230: Räumliche Zuordnung

[Räumliche Zuordnung](spatial-mapping.md) kombiniert die reale Welt und die virtuelle Welt von unterrichten Hologramme über die Umgebung. In räumlichen MR-230 (Projekt Planetarium) erfahren wir Gewusst wie:

* Überprüfen Sie die Umgebung und Daten aus der HoloLens auf Ihren Entwicklungscomputer.
* Erkunden Sie Shader, und erfahren Sie, wie zum Visualisieren der Speicherplatz zu verwenden.
* Unterteilen Sie das Netz Platz in einfachen Ebenen mithilfe von Mesh-Verarbeitung aus.
* Wechseln Sie über die Platzierung-Techniken, die wir gelernt [MR Grundlagen 101](holograms-101.md), und geben Sie Feedback zur, in denen ggf. ein Hologramm, in der Umgebung platziert werden kann.
* Untersuchen Sie verdecken Effekte, also wenn Ihre – Hologramm hinter einem echten Objekt ist, Sie immer noch mit x-Ray-Vision sehen!

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td>MR Spatial 230: Räumliche Zuordnung</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Bevor Sie beginnen

### <a name="prerequisites"></a>Vorraussetzungen

* Ein Windows 10-PCs mit dem richtigen konfiguriert [-Tools installiert](install-the-tools.md).
* Einige grundlegende C# Programmierkenntnisse.
* Sie sollten abgeschlossen haben [MR Grundlagen 101](holograms-101.md).
* Ein Gerät HoloLens [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Projektdateien

* Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) vom Projekt erforderlich sind. Ist Unity 2017.2 oder höher erforderlich.
  * Wenn Sie weitere Unity 5.6-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).
  * Wenn Sie weitere Unity 5.5-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).
  * Wenn Sie weitere 5.4 von Unity-Unterstützung benötigen, verwenden Sie [dieser Version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).
* Un-Archive die Dateien auf dem Desktop oder andere einfach auf den Speicherort zugreifen.

>[!NOTE]
>Wenn Sie vor dem Herunterladen, den Quellcode ansehen möchten es [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).

### <a name="notes"></a>Hinweise

* "Nur eigenen Code aktivieren" in Visual Studio muss deaktiviert werden soll (*deaktiviert*) unter Extras > Optionen > Debugging, um die Haltepunkte in Ihrem Code.

## <a name="unity-setup"></a>Unity-setup

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* Starten Sie **Unity**.
* Wählen Sie **neu** zum Erstellen eines neuen Projekts.
* Nennen Sie das Projekt **Planetarium**.
* Überprüfen Sie, ob die **3D** Einstellung ausgewählt ist.
* Klicken Sie auf **erstellen Projekt**.
* Nachdem Unity gestartet wird, wechseln Sie zur **Bearbeiten > Projekteinstellungen > Player**.
* In der **Inspektor** Bereich, suchen und wählen Sie das grüne **Windows Store** Symbol.
* Erweitern Sie **andere Einstellungen**.
* In der **Rendern** aktivieren Sie im Abschnitt der **virtuelle Realität unterstützt** Option.
* Überprüfen Sie, ob **Windows Holographic** angezeigt wird, in der Liste der **virtuelle Realität SDKs**. Wenn nicht der Fall, wählen Sie die **+** Schaltfläche am unteren Rand der Liste aus, und wählen Sie **Windows Holographic**.
* Erweitern Sie **Einstellungen veröffentlichen**.
* In der **Funktionen** Abschnitt, überprüfen Sie die folgenden Einstellungen:
    * InternetClientServer
    * PrivateNetworkClientServer
    * Mikrofon
    * SpatialPerception
* Wechseln Sie zu **Bearbeiten > Projekteinstellungen > Qualität**
* In der **Inspektor** Bereich unter dem Windows Store-Symbol, wählen den schwarzen Pfeil der Dropdownliste unter der Zeile mit "Default", und ändern Sie die Standardeinstellung **sehr niedrig**.
* Wechseln Sie zu **Assets > Paket importieren > benutzerdefiniertes Paket**.
* Navigieren Sie zu der **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** Ordner.
* Klicken Sie auf **Planetarium.unitypackage**.
* Klicken Sie auf **Öffnen**.
* Ein **Unity-Paket importieren** Fenster sollte angezeigt werden, klicken Sie auf die **Import** Schaltfläche.
* Warten Sie Unity aus, um alle Ressourcen zu importieren, die wir benötigen, um dieses Projekt abzuschließen.
* In der **Hierarchie** panel, löschen Sie die **Main Camera**.
* In der **Projekt** Bereich **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** Ordner finden Sie die **Main Camera** Objekt.
* Drag & drop die **Main Camera** prefab in die **Hierarchie** Bereich.
* In der **Hierarchie** panel, löschen Sie die **gerichtetes Licht** Objekt.
* In der **Projekt** Bereich **Hologramme** Ordner, suchen Sie die **Cursor** Objekt.
* Drag & drop die **Cursor** prefab in die **Hierarchie**.
* In der **Hierarchie** wählen die **Cursor** Objekt.
* In der **Inspektor** Bereich, klicken Sie auf die **Ebene** Dropdownliste aus, und wählen **Ebenen bearbeiten...** .
* Namen **Benutzerebene 31** als "**SpatialMapping**".
* Speichern Sie die neue Szene: **Datei > Szene speichern unter...**
* Klicken Sie auf **neuer Ordner** und nennen Sie den Ordner **Szenen**.
* Nennen Sie die Datei "**Planetarium**", und speichern Sie ihn in das **Szenen** Ordner.

## <a name="chapter-1---scanning"></a>Kapitel 1: Überprüfen

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

**Ziele**
* Informationen Sie zu den SurfaceObserver und wie die Auswirkungen der Einstellungen in der Benutzeroberfläche und Leistung.
* Erstellen Sie ein Zimmer Scannen Erfahrung, um die Gitter des Raums erfassen.

**Anweisungen**
* In der **Projekt** Bereich **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** Ordner finden Sie die **SpatialMapping** prefab.
* Drag & drop die **SpatialMapping** prefab in die **Hierarchie** Bereich.

**Erstellen und bereitstellen (Teil 1)**
* Wählen Sie in Unity **Datei > Buildeinstellungen**.
* Klicken Sie auf **öffnen Szenen hinzufügen** Hinzufügen der **Planetarium** Szene auf den Build.
* Wählen Sie **universelle Windows-Plattform** in die **Plattform** aus, und klicken Sie auf **Plattform wechseln**.
* Legen Sie **SDK** zu **universelle 10** und **UWP Buildtyp** zu **D3D**.
* Überprüfen Sie **Unity C# Projekte**.
* Klicken Sie auf **Erstellen**.
* Erstellen Sie eine **neuer Ordner** mit dem Namen "App".
* Mausklick die **App** Ordner.
* Drücken Sie die **Ordner auswählen** Schaltfläche.
* Unity wird nach Abschluss erstellen, ein Datei-Explorer-Fenster wird angezeigt.
* Doppelklicken Sie auf die **App** Ordner aus, um ihn zu öffnen.
* Doppelklicken Sie auf **Planetarium.sln** auf das Projekt in Visual Studio geladen werden.
* Verwenden Sie in Visual Studio obere auf der Symbolleiste, um die Konfiguration zu ändern **Version**.
* Ändern Sie die Plattform **X86**.
* Klicken Sie auf den Dropdown-Pfeil rechts neben "Lokaler Computer", und wählen Sie **Remotecomputer**.
* Geben Sie [die IP-Adresse Ihres Geräts](connecting-to-wi-fi-on-hololens.md#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) in die Adresse ein, und Ändern des Authentifizierungsmodus in **universell (unverschlüsseltes Protokoll)**.
* Klicken Sie auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**.
* Sehen Sie sich die **Ausgabe** panel in Visual Studio für Build und Bereitstellungsstatus.
* Sobald Ihre app bereitgestellt wurde, führen Sie im Raum. Sie sehen, dass die umgebenden Flächen, die von Schwarz oder weiß Drahtmodell Gitter abgedeckt.
* Überprüfen Sie Ihre Umgebung. Achten Sie darauf, Wände, Höchstgrenzen und Stockwerken ansehen.

**Erstellen und bereitstellen (Teil 2)**

Jetzt sehen wir uns wie räumliche Zuordnung Leistungseinbußen führen kann.
* Wählen Sie in Unity **Fenster > Profiler**.
* Klicken Sie auf **Profiler hinzufügen > GPU**.
* Klicken Sie auf **Active Profiler > <Enter IP>** .
* Geben Sie die **IP-Adresse** von Ihrem HoloLens.
* Klicken Sie auf **Verbinden**.
* Beachten Sie die Anzahl der Millisekunden, die es, bis die GPU dauert, einen Frame zu rendern.
* Beenden Sie die Anwendung aus, die auf dem Gerät ausgeführt.
* Zurück zu Visual Studio, und öffnen Sie **SpatialMappingObserver.cs**. Sie finden es im Ordner "HoloToolkit\SpatialMapping" des Projekts Assembly-CSharp (Universal Windows).
* Suchen der **Awake()** funktionieren, und fügen Sie die folgende Codezeile hinzu: **TrianglesPerCubicMeter = 1200;**
* Erneutes Bereitstellen des Projekts auf Ihrem Gerät, und klicken Sie dann **verbinden Sie den Profiler**. Beachten Sie die Änderung in die Anzahl der Millisekunden, die einen Frame zu rendern.
* Beenden Sie die Anwendung aus, die auf dem Gerät ausgeführt.

**Speichern Sie und Laden Sie in Unity**

Abschließend sehen wir unser Platz Netz zu speichern und Laden sie in Unity.
* Zurück zu Visual Studio, und entfernen Sie die **TrianglesPerCubicMeter** Zeile, die Sie in hinzugefügt haben die **Awake()** -Funktion während der im vorherigen Abschnitt.
* Bereitstellen Sie das Projekt auf Ihrem Gerät erneut. Wir sollten jetzt ausgeführt werden, wobei **500** Dreiecke pro kubische Meter.
* Öffnen Sie einen Browser, und geben Sie in Ihrem HoloLens IPAddress, zu dem navigiert die **Windows Device Portal**.
* Wählen Sie die **-3D-Sicht** Option im linken Bereich.
* Klicken Sie unter **Oberfläche Rekonstruktion** wählen Sie die **Update** Schaltfläche.
* Sehen Sie sich, wie der Bereiche, die Sie für Ihre HoloLens überprüft haben, die in das Anzeigefenster angezeigt werden.
* Um die Überprüfung der Raum zu speichern, drücken Sie die **speichern** Schaltfläche.
* Öffnen Ihrer **Downloads** Ordner aus, um das Modell gespeicherte Platz ermitteln **SRMesh.obj**.
* Kopie **SRMesh.obj** auf die **Assets** Ordner Ihres Unity-Projekts.
* Wählen Sie in Unity die **SpatialMapping** -Objekt in der **Hierarchie** Bereich.
* Suchen Sie die **Objekt Oberfläche Beobachter (Skript)** Komponente.
* Klicken Sie auf den Kreis neben der **Platz Modell** Eigenschaft.
* Suchen und Auswählen der **SRMesh** Objekt aus, und klicken Sie dann das Fenster schließen.
* Überprüfen Sie, ob die **Platz Modell** -Eigenschaft in der **Inspektor** Bereich ist nun so festgelegt **SRMesh**.
* Drücken Sie die **spielen** Schaltfläche Unity Vorschaumodus eingeben.
* Die SpatialMapping-Komponente wird die Gitter aus dem Modell gespeicherten Platz geladen, damit Sie sie in Unity verwenden können.
* Wechseln Sie zur **Szene** Ansicht, um die Anzeige aller Ihr Platz-Modell, das mit dem Shader Drahtmodell angezeigt.
* Drücken Sie die **spielen** Schaltfläche erneut aus, um im Vorschaumodus zu beenden.

**HINWEIS:** Das nächste Mal die Eingabe im Vorschaumodus in Unity wird das Netz gespeicherten Platz standardmäßig geladen.

## <a name="chapter-2---visualization"></a>Kapitel 2: Visualisierung

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

**Ziele**
* Enthält die Grundlagen von Shadern.
* Visualisieren Sie Ihre Umgebung.

**Anweisungen**
* In Unity **Hierarchie** wählen die **SpatialMapping** Objekt.
* In der **Inspektor** Bereich, suchen Sie nach der **räumliche Zuordnungs-Manager (Skript)** Komponente.
* Klicken Sie auf den Kreis neben der **Oberfläche Material** Eigenschaft.
* Suchen und Auswählen der **BlueLinesOnWalls** "Material" und schließen Sie das Fenster.
* In der **Projekt** Bereich **Shader** Ordner, doppelklicken Sie auf **BlueLinesOnWalls** auf den Shader in Visual Studio zu öffnen.
* Dies ist eine einfache Pixelverarbeitungsvorgänge (Vertex, fragment) Shader, der die folgenden Aufgaben erledigt wird:
    1. Konvertiert des Vertex-Speicherort in einen Raum der Welt.
    2. Überprüft, dass der Scheitelpunkt ist normal, um festzustellen, ob eine Pixel vertikal ist.
    3. Legt die Farbe des Pixels für das Rendering.

**Erstellen und bereitstellen**
* Zurück zu Unity, und drücken Sie **spielen** Vorschaumodus eingeben.
* Blaue Linien werden auf alle vertikale Oberflächen des Netzes Platz gerendert werden (die aus den gespeicherten Scannen Daten automatisch geladen wird).
* Wechseln Sie zu der **Szene** Registerkarte Anpassen Ihrer Ansicht des Raums und wie das Netz ganzen Raum in Unity angezeigt wird.
* In der **Projekt** Bereich, suchen Sie nach der **Materialien** Ordner, und wählen die **BlueLinesOnWalls** Material.
* Ändern Sie einige Eigenschaften, und sehen Sie, wie die Änderungen im Unity-Editor angezeigt.
    * In der **Inspektor** panel, passen Sie die **LineScale** Wert, um die Zeilen dicker oder schlankere angezeigt herzustellen.
    * In der **Inspektor** panel, passen Sie die **LinesPerMeter** Wert ändern, wie viele Zeilen für jede Wand angezeigt werden.
* Klicken Sie auf **spielen** erneut aus, um im Vorschaumodus zu beenden.
* Erstellen Sie und Bereitstellen Sie, die HoloLens, und beobachten Sie, wie der Shader, der rendering auf echten Oberflächen angezeigt wird.

Unity eignet sich gut in der Vorschau anzuzeigen Materialien, aber es ist immer eine gute Idee, informieren Sie sich Rendering auf dem Gerät.

## <a name="chapter-3---processing"></a>Kapitel 3 – verarbeiten

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

**Ziele**
* Erfahren Sie, Verfahren, um räumliche Zuordnung von Daten für die Verwendung in Ihrer Anwendung zu verarbeiten.
* Analysieren Sie Daten räumliche Zuordnung, um Ebenen zu finden und Dreiecke zu entfernen.
* Verwenden Sie für die Platzierung von – Hologramm Ebenen.

**Anweisungen**
* In Unity **Projekt** Bereich **Hologramme** Ordner finden Sie die **SpatialProcessing** Objekt.
* Drag & drop die **SpatialProcessing** -Objekt in der **Hierarchie** Bereich.

Das Prefab SpatialProcessing enthält Komponenten für die Verarbeitung der Daten für die räumliche Zuordnung. **SurfaceMeshesToPlanes.cs** findet und Ebenen, die basierend auf den spatial Zuordnungsdaten zu generieren. Wir verwenden Ebenen in unserer Anwendung, Wände, Etagen und Obergrenzen darstellen. Diese Prefab enthält auch **RemoveSurfaceVertices.cs** können die Scheitelpunkte aus dem Netz räumliche Zuordnung entfernen. Dies kann verwendet werden, um Lücken im Netz zu erstellen oder überschüssige Dreiecke zu entfernen, die nicht mehr benötigt werden (da Ebenen stattdessen verwendet werden können).
* In Unity **Projekt** Bereich **Hologramme** Ordner finden Sie die **SpaceCollection** Objekt.
* Drag & drop die **SpaceCollection** -Objekt in der **Hierarchie** Bereich.
* In der **Hierarchie** wählen die **SpatialProcessing** Objekt.
* In der **Inspektor** Bereich, suchen Sie nach der **spielen Space-Manager (Skript)** Komponente.
* Doppelklicken Sie auf **PlaySpaceManager.cs** um es in Visual Studio zu öffnen.

PlaySpaceManager.cs enthält anwendungsspezifische Code. Wir werden dieses Skript so aktivieren Sie das folgende Verhalten Funktionalität hinzufügen:
1. Beenden der Datensammlung räumliche Zuordnung, nachdem die Überprüfung Zeitlimit (10 Sekunden) überschritten.
2. Die räumliche Zuordnung-Daten verarbeiten:
    1. Verwenden Sie SurfaceMeshesToPlanes, um einer einfacheren Darstellung der Welt als Ebenen (Wände, Etagen, Obergrenzen, usw.) zu erstellen.
    2. Verwenden Sie RemoveSurfaceVertices Oberfläche Dreiecke zu entfernen, die in der Datenebene Grenzen liegen.
3. Generieren Sie eine Auflistung von Hologramme in der ganzen Welt, und platzieren Sie sie auf die Wand und Floor Ebenen in der Nähe der Benutzer.

Führen Sie die markierten PlaySpaceManager.cs codierungsübungen, oder Ersetzen Sie das Skript mit dem fertigen Lösung von unten:

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
* Vor der Bereitstellung, die HoloLens, drücken Sie die **spielen** -Schaltfläche in Unity Spielmodus eingeben.
* Nach dem Raum Netz aus der Datei geladen wird, warten Sie 10 Sekunden vor Beginn der Verarbeitung des Netzes räumliche Zuordnung.
* Wenn die Verarbeitung abgeschlossen ist, werden Ebenen darstellen, Floor, Wände, Ceiling usw. angezeigt.
* Nachdem alle wurden der Ebenen gefunden. Daraufhin sollte ein Sonnensystem auf eine Tabelle mit Floor in der Nähe der Kamera angezeigt werden.
* Zwei Poster sollte zu Wände in der Nähe der Kamera angezeigt werden. Wechseln Sie zu der **Szene** Registerkarte, wenn sie in nicht **Spiel** Modus.
* Drücken Sie die **spielen** Schaltfläche wieder zu Spielmodus zu schließen.
* Erstellen Sie und Bereitstellen Sie, die HoloLens, wie gewohnt.
* Warten Sie scannen und die Verarbeitung der Daten räumliche Zuordnung abgeschlossen.
* Sobald Ebenen angezeigt werden, versuchen Sie es, um den Sonnensystem und Poster in Ihre Welt zu finden.

## <a name="chapter-4---placement"></a>Kapitel 4 - Platzierung

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

**Ziele**
* Bestimmt, ob Sie ggf. ein Hologramm auf einer Oberfläche passt.
* Geben Sie Feedback an den Benutzer, wenn auf einer Oberfläche ggf. ein Hologramm passen kann/kann nicht.

**Anweisungen**
* In Unity **Hierarchie** wählen die **SpatialProcessing** Objekt.
* In der **Inspektor** Bereich, suchen Sie nach der **Oberfläche, Gitter zu Ebenen (Skript)** Komponente.
* Ändern der **Ebenen zeichnen** Eigenschaft **nichts** um die Auswahl aufzuheben.
* Ändern der **Ebenen zeichnen** Eigenschaft **Wand**, sodass nur die Wand Ebenen gerendert werden.
* In der **Projekt** Bereich **Skripts** Doppelklicken Sie auf Ordner **Placeable.cs** um sie in Visual Studio öffnen.

Die **Placeable** Skript bereits an das Poster und die Projektion-Feld, die erstellt werden, nach Abschluss der Datenebene suchen angefügt wurde. Alles, was erforderlich ist, ist einige Code auskommentiert haben und dieses Skript wird Folgendes erreichen:
1. Bestimmt, ob Sie ggf. ein Hologramm auf einer Oberfläche von feinheiten beim Raycasting, aus dem Mittelpunkt und die vier Ecken des umschließenden Cubes passt.
2. Überprüfen Sie die Oberfläche zu bestimmen, ob sie genug für die Hologramm gerne leeren auf verläuft normal.
3. Rendern Sie einen umgebenden Cube mit den Hologramm die tatsächliche Größe angezeigt werden, während des Einfügens.
4. Wandeln Sie einen Schatten unter bzw. hinter der – Hologramm, um anzuzeigen, wo er an den Boden/Wand platziert werden.
5. Rendern des Schattens Rot dargestellt, ein, wenn es sich bei der – Hologramm kann nicht auf die Entwurfsoberfläche, oder Grün, platziert werden, sofern dies möglich.
6. Neu ausrichten der – Hologramm, um mit dem Surface-Typ (vertikal oder horizontal) auszurichten, dass sie die Affinität für hat.
7. Platzieren Sie den – Hologramm reibungslos auf der ausgewählten Fläche springen oder Andocken Verhalten vermeiden.

Entfernen Sie alle Code in der Programmierung Übung unten aus, oder verwenden Sie diese abgeschlossenen Lösung in **Placeable.cs**:

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
* Wie zuvor, erstellen Sie das Projekt aus, und stellen in die HoloLens.
* Warten Sie scannen und die Verarbeitung der Daten räumliche Zuordnung abgeschlossen.
* Wenn Sonnensystem angezeigt wird, auf das nachfolgende Feld Projektion bestaunen Sie, und führen Sie eine Option Geste, verschieben Sie ihn. Während der Projektion Feld ausgewählt ist, werden ein umgebenden Cube angezeigt, um das Feld für die Projektion.
* Verschieben Sie Sie an einer anderen Stelle im Raum bestaunen lesen. Das Feld für die Projektion, sollte Ihre Blicke folgen. Wenn der Schatten unterhalb des Felds Projektion rot angezeigt wird, können nicht Sie Hologramm auf, die dann platzieren. Wenn der Schatten unterhalb des Felds Projektion Grün, können Sie die – Hologramm platzieren, anhand einer anderen Option Geste.
* Suchen Sie und wählen Sie eine holographic Poster an einer Wand in einem neuen Speicherort zu verschieben. Beachten Sie, dass das Poster kann nicht auf dem Boden oder Ceiling man und, es auf jede Wand richtig ausgerichtet bleibt, wenn Sie bewegen.

## <a name="chapter-5---occlusion"></a>Kapitel 5 – verdecken

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

**Ziele**
* Bestimmt, ob durch das Netz räumliche Zuordnung ggf. ein Hologramm okkludierte ist.
* Anwenden von verschiedenen verdecken-Techniken, um ein unterhaltsames zu erreichen wirksam.

**Anweisungen**

Zunächst werden wir räumliche Zuordnung Mesh zu anderen Hologramme verdeckt wird, ohne die reale Welt occluding zulassen:
* In der **Hierarchie** wählen die **SpatialProcessing** Objekt.
* In der **Inspektor** Bereich, suchen Sie nach der **spielen Space-Manager (Skript)** Komponente.
* Klicken Sie auf den Kreis neben der **sekundären Material** Eigenschaft.
* Suchen und Auswählen der **verdecken** "Material" und schließen Sie das Fenster.

Als Nächstes werden wir ein besonderes Verhalten auf der Erde, hinzufügen, damit sie eine blaue Hervorhebung aufweist, wenn er durch einen anderen Hologramm (z. B. die Sonne) oder durch das Netz räumliche Zuordnung okkludierte wird:
* In der **Projekt** im Bereich der **Hologramme** Ordner, erweitern Sie die **SolarSystem** Objekt.
* Klicken Sie auf **Earth**.
* In der **Inspektor** Bereich, der Erde Material (unten Komponente) zu finden.
* In der **Shader Dropdownliste**, ändern Sie den Shader **benutzerdefinierte > OcclusionRim**. Dadurch wird eine blaue Hervorhebung um Earth gerendert, wenn er von einem anderen Objekt okkludierte ist.

Abschließend werden wir einen x-Ray Vision Effekt für Planeten unseres Sonnensystems zu aktivieren. Wir müssen bearbeiten **PlanetOcclusion.cs** (finden Sie im Ordner "Scripts\SolarSystem") um Folgendes zu erreichen:
1. Bestimmt, ob eine Planeten von der SpatialMapping-Ebene (Platz Gitter und Ebenen) okkludierte ist.
2. Zeigen Sie die Drahtmodell Darstellung einer weltweit, wenn es von der Ebene SpatialMapping okkludierte ist.
3. Blenden Sie die Drahtmodell Darstellung einer weltweit, wenn er nicht von der Ebene SpatialMapping blockiert wird.

Führen Sie die Codierung Übung in PlanetOcclusion.cs, oder verwenden Sie die folgende Lösung:

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
* Erstellen und die Anwendung für HoloLens, wie gewohnt bereitstellen.
* Warten Sie, zu scannen und die Verarbeitung der Daten räumliche Zuordnung abgeschlossen sein, (daraufhin blaue Linien in Wände angezeigt werden).
* Suchen Sie und Kontrollkästchen Sie das Sonnensystem Projektion, und legen Sie dann das Kontrollkästchen neben einer Wand oder hinter einen Leistungsindikator.
* Sie können grundlegende verdecken von ausblenden hinter Flächen auf das Poster oder Projektion Peering anzeigen.
* Suchen Sie nach der Erde, sollte eine blaue Hervorhebung Auswirkung, wenn darin hinter einer anderen – Hologramm oder Fläche.
* Sehen Sie sich, wie die Planeten hinter die Wand oder andere Oberflächen im Raum verschieben. X-Ray-Vision und alle ihre Drahtmodell Skelette sehen!

## <a name="the-end"></a>Das Ende

Herzlichen Glückwunsch! Sie haben jetzt **MR räumliche 230: Räumliche Zuordnung**.
* Sie wissen, wie Sie Ihre Umgebung und Load räumliche Zuordnungsdaten mit Unity zu überprüfen.
* Sie kennen die Grundlagen der Shader und wie Materialien verwendet werden können, um die Welt neu zu visualisieren.
* Sie erfahren, von der Verarbeitungstechniken für die Suche nach Ebenen aus, und Entfernen von Dreiecke aus einem Mesh.
* Sie konnten zu verschieben, und platzieren Sie Hologramme auf Oberflächen, die sinnvoll vorgenommen.
* Sie verdecken von verschiedenen Techniken aufgetreten und ein Showcase mit die Leistungsfähigkeit von x-Ray-maschinelles sehen.
