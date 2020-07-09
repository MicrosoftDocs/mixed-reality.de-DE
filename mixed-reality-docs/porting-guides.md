---
title: Portierungsleitfäden
description: Eine Schritt-für-Schritt-Anleitung, in der erläutert wird, wie Sie eine vorhandene immersive Anwendung in Windows Mixed Reality portieren.
author: JBrentJ
ms.author: alexturn
ms.date: 07/07/2020
ms.topic: article
keywords: Port, portieren, Unity, Middleware, Engine, UWP, Win32
ms.openlocfilehash: a1e3cd47096d728091d62d6c038bf6b2eb6bab16
ms.sourcegitcommit: 0eb99fae933d4374af2c032af4e9ceda1807e532
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86156771"
---
# <a name="porting-guides"></a>Portierungsleitfäden

## <a name="overview"></a>Übersicht

Windows 10 bietet direkte Unterstützung für immersive und holografische Headsets. Wenn Sie Inhalte für andere Geräte erstellt haben, wie z. b. den Oculus-oder den HTC-Vive, haben diese Abhängigkeiten von Bibliotheken, die über der Plattform-API des Betriebssystems vorhanden sind. Das Bereitstellen von vorhandenem Inhalt in Windows Mixed Reality umfasst die Neuausrichtung der Verwendung dieser anderen sdken auf die Windows-APIs. Die [Windows-Plattform-APIs für gemischtes Reality](https://docs.microsoft.com/uwp/api/Windows.Perception) funktionieren sowohl mit dem Win32-als auch dem universelle Windows-Plattform-App-Modell (UWP). Wenn Ihre APP nicht bereits für UWP erstellt wurde, ist die Umstellung auf UWP Teil der Portierung.

## <a name="porting-overview"></a>Übersicht über das Portieren

Auf hoher Ebene sind die folgenden Schritte zum Portieren vorhandener Inhalte beteiligt:
1. **Stellen Sie sicher, dass auf Ihrem PC das Windows 10 Fall Creators Update (16299) ausgeführt wird.** Wir empfehlen Ihnen nicht mehr, vorschaubuilds aus dem Insider-Ahead-Ring zu erhalten, da diese Builds für die Entwicklung mit gemischter Realität nicht am stabilsten sind.
2. **Führen Sie ein Upgrade auf die neueste Version Ihrer Grafik oder Spiel-Engine aus.** Game Engines müssen die Windows 10 SDK-Version 10.0.15063.0 (veröffentlicht im April 2017) oder höher unterstützen.
3. **Aktualisieren Sie alle Middleware, Plug-ins oder Komponenten.** Wenn Ihre APP Komponenten enthält, empfiehlt es sich, ein Upgrade auf die neueste Version durchzuführen. Neuere Versionen der gängigsten Plug-ins haben Unterstützung für UWP.
4. **Entfernen Sie Abhängigkeiten für doppelte sdche**. Je nachdem, auf welchem Gerät Ihre Inhalte ausgerichtet waren, müssen Sie dieses SDK (z. b. "steamvr") entfernen oder bedingt kompilieren, damit Sie stattdessen die Windows-APIs verwenden können.
5. **Arbeiten Sie durch Buildprobleme.** An diesem Punkt ist die Portierungs Übung spezifisch für Ihre APP, die Engine und die Komponenten Abhängigkeiten, die Sie haben.

## <a name="common-porting-steps"></a>Allgemeine Schritte zum Portieren

### <a name="common-step-1-make-sure-you-have-the-right-development-hardware"></a>Allgemeine Schritt 1: Stellen Sie sicher, dass Sie über die richtige Entwicklungs Hardware verfügen.

Auf der Seite [Tools installieren](install-the-tools.md#for-immersive-vr-headset-development) wird die empfohlene Entwicklungs Hardware aufgeführt.

### <a name="common-step-2-upgrade-to-the-latest-flight-of-windows-10"></a>Common Step 2: Upgrade auf den letzten Flug von Windows 10

Die Windows Mixed Reality-Plattform ist noch nicht aktiv. Es wird empfohlen, [das Windows Insider-Programm](https://insider.windows.com/) für den Zugriff auf den "Windows Insider fast"-Flug zu verbinden.
1. Installieren Sie das [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10) .
2. [Treten](https://insider.windows.com/) Sie dem Windows-Insider Programm bei.
3. [Entwicklermodus](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development) aktivieren
4. Wechseln Sie zum Abschnitt " [Windows Insider fast-Flüge](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview) über **Einstellungen > Update & Sicherheit** ".

### <a name="common-step-3-upgrade-to-the-most-recent-build-of-visual-studio-uwp-only"></a>Common Step 3: Upgrade auf den neuesten Build von Visual Studio (nur UWP)
* Weitere Informationen finden Sie unter [Installieren der Tools](install-the-tools.md#installation-checklist) -Seite unter Visual Studio 2019

### <a name="common-step-4-be-ready-for-the-store-uwp-only"></a>Allgemeine Schritt 4: bereit für den Store (nur UWP)
* Verwenden Sie das [Windows-zertifizierungskit für apps](https://developer.microsoft.com/windows/develop/app-certification-kit) (auch als Wack bezeichnet) früh und häufig!
* [Portabilitäts Analyse](https://docs.microsoft.com/dotnet/standard/portability-analyzer) verwenden ([Download](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer))

### <a name="common-step-5-choose-the-correct-adapter"></a>Common Step 5: Auswählen des richtigen Adapters
* Richten Sie in Systemen wie Notebooks mit zwei GPUs [den richtigen Adapter](rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications)ein. Dies gilt für Unity-und Native DirectX-apps, bei denen ein ID3D11Device entweder explizit oder implizit (Media Foundation) für seine Funktionalität erstellt wird.

## <a name="unity-porting-guidance"></a>Leitfaden für die Unity-Portierung

### <a name="unity-step-1-follow-the-common-porting-steps"></a>Unity-Schritt 1: Befolgen Sie die allgemeinen Schritte zum Portieren.

Führen Sie alle gängigen Schritte aus. Wenn Sie in Schritt #3, wählen Sie die Arbeitsauslastung für die **Spieleentwicklung mit Unity** aus. Deaktivieren Sie die optionale Komponente des Unity-Editors, da Sie eine neuere Version von Unity aus den Anweisungen unten installieren.

### <a name="unity-step-2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>Unity, Schritt 2: Upgrade auf den neuesten öffentlichen Build von Unity mit Windows Mr-Unterstützung
1. Laden Sie den neuesten [empfohlenen öffentlichen Build von Unity](install-the-tools.md) mit gemischter Reality-Unterstützung herunter.
2. Speichern Sie eine Kopie des Projekts, bevor Sie loslegen.
3. Überprüfen Sie die in Unity verfügbare [Dokumentation](https://docs.unity3d.com/Manual/UpgradeGuides.html) zum Portieren.
4. Befolgen Sie die [Anweisungen](https://docs.unity3d.com/Manual/APIUpdater.html) auf der Website von Unity, um Ihren automatischen API-Updater zu verwenden.
5. Überprüfen Sie, ob weitere Änderungen vorhanden sind, die Sie vornehmen müssen, um das Projekt ausführen zu können, und arbeiten Sie mit allen verbleibenden Fehlern und Warnungen. 

> [!Note] 
> Wenn Sie über eine Middleware verfügen, von der Sie abhängig sind, überprüfen Sie, ob Sie die neueste Version verwenden (Weitere Informationen finden Sie unten in Schritt 3).

### <a name="unity-step-3-upgrade-your-middleware-to-the-latest-versions"></a>Unity Schritt 3: Aktualisieren der Middleware auf die neuesten Versionen

Bei jedem Unity-Update besteht eine gute Chance, dass Sie ein oder mehrere Middlewarepakete aktualisieren müssen, von denen Ihr Spiel oder Ihre Anwendung abhängig ist. Außerdem erhöht sich die Wahrscheinlichkeit, dass Sie im gesamten Rest des Portierungs Prozesses Erfolg haben, auf dem neuesten Stand der aktuellen Middleware. Viele Middlewarepakete haben vor kurzem Unterstützung für universelle Windows-Plattform (UWP) hinzugefügt, und durch ein Upgrade auf die neuesten Versionen können Sie diese Arbeit nutzen.

### <a name="unity-step-4-target-your-application-to-run-on-universal-windows-platform-uwp"></a>Unity Schritt 4: Ausrichten der Anwendung für die Ausführung auf universelle Windows-Plattform (UWP)

Wenn Sie Win32 als Ziel verwenden, können Sie diesen Schritt überspringen und mit Schritt 5 fortfahren.

Nachdem Sie die Tools installiert haben, müssen Sie Ihre APP als universelle Windows-app ausführen.

* Befolgen Sie die [ausführlichen Schritte](https://unity3d.com/partners/microsoft/porting-guides) , die von Unity bereitgestellt werden. Sie sollten auf der neuesten LTS-Version (alle 20xx. 4 Releases) für Windows Mr bleiben.
* Weitere UWP-Entwicklungsressourcen finden Sie im [Windows 10-Spiel Entwicklungs Handbuch](https://docs.microsoft.com/windows/uwp/gaming/e2e).

> [!NOTE]
> Unity verbessern weiterhin IL2CPP-Unterstützung; IL2CPP macht einige UWP-Ports leichter. Wenn Sie zurzeit das .NET-Skript-Back-End als Ziel verwenden, sollten Sie in Erwägung gezogen werden, um stattdessen das IL2CPP-Backend

* Sie können "Unity Step 5" überspringen, da Sie anstelle von Win32 UWP als Ziel verwenden.

> [!NOTE] 
> Wenn Ihre Anwendung Abhängigkeiten von gerätespezifischen Diensten aufweist (z. b. die Abgleich von "Stream"), müssen Sie Sie in diesem Schritt deaktivieren. Sie können die entsprechenden Dienste einrichten, die von Windows später bereitstellt werden.

### <a name="unity-step-5-target-your-application-to-run-on-win32"></a>Unity-Schritt 5: Ausrichten der Anwendung auf Win32

In ihrer Unity-Anwendung:

* Navigieren Sie zu Datei-> Buildeinstellungen.
* Wählen Sie "PC, Mac, eigenständiges Linux" aus.
* Legen Sie die Zielplattform auf "Windows" fest.
* Legen Sie Architektur auf "x86" Select "Switch Platform" fest.


### <a name="unity-step-6-setup-your-windows-mixed-reality-hardware"></a>Unity Schritt 6: Einrichten der Windows Mixed Reality-Hardware
1. Überprüfen der Schritte in der [immersiven Headset-Einrichtung](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)
2. Erfahren Sie mehr über [die Verwendung des Windows Mixed Reality-Simulators](using-the-windows-mixed-reality-simulator.md) und [Navigieren in Windows Mixed Reality Home](navigating-the-windows-mixed-reality-home.md)

### <a name="unity-step-7-target-your-application-to-run-on-windows-mixed-reality"></a>Unity-Schritt 7: ausrichten Ihrer Anwendung auf Windows Mixed Reality
1. Zunächst müssen Sie alle anderen Bibliotheks Unterstützung für ein bestimmtes VR-SDK entfernen oder bedingt kompilieren. Diese Assets ändern häufig Einstellungen und Eigenschaften für Ihr Projekt in einer Weise, die nicht mit anderen VR-sDas kompatibel ist, wie z. b. Windows Mixed Reality.
    * Wenn Ihr Projekt beispielsweise auf das steamvr-SDK verweist, müssen Sie das Projekt aktualisieren, um die Prefabs-und Skript-API-Aufrufe beim Exportieren für das Windows Store-Buildziel auszuschließen.
    * In Kürze werden bestimmte Schritte zum bedingten ausschließen anderer VR-sdche in Kürze ausgeführt.
2. In Ihrem Unity-Projekt [das Windows 10-SDK als Ziel](holograms-100.md#target-windows-10-sdk)
3. Richten Sie [die Kamera](holograms-100.md#chapter-2---setup-the-camera) für jede Szene ein.

### <a name="unity-step-8-use-the-stage-to-place-content-on-the-floor"></a>Unity-Schritt 8: Verwenden der Stufe zum Platzieren von Inhalten im Boden

Sie können in einer Vielzahl von [Erfahrungs Skalen](coordinate-systems.md)Umgebungen mit gemischter Realität entwickeln.

Wenn Sie eine Anwendung mit **sitzender Skalierung**portieren, müssen Sie sicherstellen, dass Unity auf den Typ des **stationären** nach Verfolgungs Raums festgelegt ist:

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

Mit dem obigen Code wird das World-Koordinatensystem von Unity festgelegt, um den [stationären Verweis Rahmen](coordinate-systems.md#spatial-coordinate-systems)zu verfolgen. Im Modus der stationären Nachverfolgung wird der Inhalt, der direkt vor dem Standard Speicherort der Kamera (vorwärts ist-Z) im Editor eingefügt wird, vor dem Benutzer angezeigt, wenn die APP gestartet wird. Um den sitzenden Ursprung des Benutzers wieder einzugeben, können Sie den "XR"-Befehl von Unity aufzurufen [. Inputtracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) -Methode.

Wenn **Sie eine vorhandene** Oberfläche oder **Raum Skalierung**portieren, werden Sie Inhalte relativ zum Boden platzieren. Sie haben eine Begründung für den Benutzer, der die **[räumliche Phase](coordinate-systems.md#spatial-coordinate-systems)** verwendet, die den definierten Ursprung und die optionale Raumgrenze des Benutzers darstellt, die während der ersten Durchführung eingerichtet wird. Für diese Umgebungen müssen Sie sicherstellen, dass Unity auf den Typ des **roomscale** -nach Verfolgungs Raums festgelegt ist. Obwohl es sich bei der Standardeinstellung um die Standardeinstellung handelt, sollten Sie Sie explizit festlegen und sicherstellen, dass Sie den Vorgang wiederholen.

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

Nachdem Ihre APP den Typ für die Nachverfolgung von roomscale festgelegt hat, wird der Inhalt auf der Ebene "y = 0" auf der Etage angezeigt. Der Ursprung bei (0,0) ist die spezifische Stelle auf dem Boden, an der der Benutzer während des Raum Setups Stand, wobei-Z die Vorwärtsrichtung darstellt, die während des Setups aufgetreten ist.

In Skriptcode können Sie dann die trygetgeometry-Methode aufrufen, indem Sie den Typ "unityengine. experimental. XR. Boundary" verwenden, um ein Begrenzungs Polygon abzurufen und dabei den Grenztyp "trackedarea" anzugeben. Wenn der Benutzer eine Grenze definiert hat (Sie erhalten eine Liste mit Scheitel Punkten), ist es sicher, dem Benutzer eine **Raum** Umgebung bereitzustellen, in der Sie die von Ihnen erstellte Szene durchlaufen können.

Das System gibt die Grenze automatisch aus, wenn der Benutzer es nähert. Ihre APP muss dieses Polygon nicht verwenden, um die Grenze selbst zu erzeugen.

Weitere Informationen finden Sie auf der Seite [Koordinatensysteme in Unity](coordinate-systems-in-unity.md) .

Einige Anwendungen verwenden ein Rechteck, um die Interaktion einzuschränken. Das Abrufen des größten eingeschriebenen Rechtecks wird in der UWP-API oder in Unity nicht direkt unterstützt. Der folgende Beispielcode zeigt, wie Sie ein Rechteck innerhalb der nach verfolgten Begrenzungen finden. Die Heuristik basiert daher möglicherweise nicht auf der optimalen Lösung, aber die Ergebnisse entsprechen den Erwartungen. Parameter im Algorithmus können optimiert werden, um auf Kosten der Verarbeitungszeit genauere Ergebnisse zu finden. Der Algorithmus befindet sich in einer Verzweigung des Mixed Reality Toolkit, das die 5,6 Preview MRTP-Version von Unity verwendet. Dies ist nicht öffentlich verfügbar. Der Code sollte direkt in 2017,2 und höheren Versionen von Unity verwendet werden können. Der Code wird in naher Zukunft in den aktuellen mrtk portiert.

[ZIP-Datei mit Code auf GitHub](https://github.com/KevinKennedy/MixedRealityToolkit-Unity/releases/tag/5.6.MRTP20) Wichtige Dateien:
* Assets/holotoolkit/Stage/Scripts/stagemanager. cs: Beispiel für die Verwendung
* Assets/holotoolkit/Stage/Scripts/largestrechteck. cs-Implementierung des Algorithmus
* Assets/holotoolkit-Unittests/Editor/Stage/largestrechgletest. cs-trivialer Test des Algorithmus

Beispiel für Ergebnisse:

![Beispiel für Ergebnisse](images/largestrectangle-400px.jpg)

Der Algorithmus basiert auf einem Blog von Daniel smilkow: [größten Rechteck in einem Polygon](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)

### <a name="unity-step-9-work-through-your-input-model"></a>Unity-Schritt 9: Arbeiten durch das Eingabe Modell

Jedes Spiel oder jede Anwendung, das auf ein vorhandenes HMD ausgerichtet ist, verfügt über eine Reihe von Eingaben, die es verarbeitet, sowie über die Typen von Eingaben, die für die Benutzer Anforderung benötigt werden Wir haben versucht, es so einfach und unkompliziert wie möglich zu gestalten, um die in Windows Mixed Reality verfügbaren Eingaben zu nutzen.
1. Ausführliche Informationen zur Bereitstellung von Eingaben durch Windows Mixed Reality finden Sie im **[Leitfaden für die Eingabe Portierung für Unity](input-porting-guide-for-unity.md)** .
2. Wählen Sie aus, ob Sie die API für das over-VR-SDK-Eingabe-API von Unity oder die Mr-spezifische Eingabe-API nutzen möchten. Die allgemeinen Input. getbutton/Input. getaxis-APIs werden heute von Unity-VR-Apps für die Verwendung von [Oculus](https://docs.unity3d.com/Manual/OculusControllers.html) -und [openvr-Eingaben](https://docs.unity3d.com/Manual/OpenVRControllers.html)verwendet. Wenn Ihre apps bereits diese APIs für Motion-Controller verwenden, ist dies der einfachste Pfad. Sie müssen nur Schaltflächen und Achsen im Eingabe-Manager neu zuordnen.
    * Sie können auf Motion Controller-Daten in Unity zugreifen, indem Sie entweder die allgemeine Cross-VR-SDK-Eingabe. getbutton/Input. getaxis-APIs oder die Mr-spezifischen unityengine. XR. WSA. Input-APIs verwenden. (zuvor im Namespace "unityengine. XR. WSA. Input" in Unity 5,6)
    * Sehen Sie sich das [Beispiel im Toolkit an](https://github.com/Microsoft/HoloToolkit-Unity/pull/572) , das Gamepad-und Motion-Controller kombiniert.

### <a name="unity-step-10-performance-testing-and-tuning"></a>Unity Schritt 10: Leistungstests und-Optimierung

Windows Mixed Reality steht auf einer Vielzahl von Geräten zur Verfügung, die von High-End-Gaming-PCs bis hin zu großen Markt Einführungs PCs reichen. Je nachdem, welchen Markt Sie als Ziel haben, gibt es einen signifikanten Unterschied in den verfügbaren COMPUTE-und Grafik Budgets für Ihre Anwendung. Während dieser Portierungs Übung nutzen Sie wahrscheinlich einen Premium-PC und haben bedeutende COMPUTE-und Grafik Budgets für Ihre APP zur Verfügung gestellt. Wenn Sie Ihre APP für eine größere Zielgruppe verfügbar machen möchten, sollten Sie Ihre APP auf [der repräsentativen Hardware](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)testen und erstellen, die Sie als Ziel festlegen möchten.

Sowohl [Unity](https://docs.unity3d.com/Manual/Profiler.html) als auch [Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index) beinhalten leistungsprofilerstellungs-und sowohl [Microsoft](understanding-performance-for-mixed-reality.md) -als auch [Intel](https://software.intel.com/articles/vr-content-developer-guide) -Veröffentlichungs Richtlinien zur Leistungsprofil Erstellung und-Optimierung. Es gibt eine umfassende Erörterung der Leistung, um die [Leistung für gemischte Realität zu verstehen](understanding-performance-for-mixed-reality.md). Darüber hinaus gibt es spezifische Details für Unity unter [Empfehlungen zur Leistung für Unity](performance-recommendations-for-unity.md).

## <a name="see-also"></a>Weitere Informationen
* [Leitfaden für Eingabeportierung für Unity](input-porting-guide-for-unity.md)
* [Windows Mixed Reality-Mindestanforderungen für die PC-Hardware Kompatibilität](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Grundlegendes zur Leistung für gemischte Realität](understanding-performance-for-mixed-reality.md)
* [Empfehlungen zur Leistung für Unity](performance-recommendations-for-unity.md)
* [Hinzufügen von Xbox Live-Unterstützung zu Unity für UWP](https://docs.microsoft.com/windows/uwp/xbox-live/get-started-with-partner/partner-add-xbox-live-to-unity-uwp)
