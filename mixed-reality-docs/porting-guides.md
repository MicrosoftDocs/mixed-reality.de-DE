---
title: Portierungsleitfäden
description: Eine schrittweise exemplarische Vorgehensweise erläutert, wie Sie eine vorhandene Anwendung immersive Windows Mixed Reality portieren.
author: ChimeraScorn
ms.author: cwhite
ms.date: 10/02/2018
ms.topic: article
keywords: Port, portieren, Unity, Middleware-engine, handelt es sich bei UWP
ms.openlocfilehash: a4a8c78f1c45fd8e3b85a767d139bae9f67540e0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595361"
---
# <a name="porting-guides"></a>Portierungsleitfäden

> [!NOTE]
> Weitere Anleitungen, die speziell für HoloLens 2 [bald](index.md#news-and-notes).

Windows 10 bietet Unterstützung für immersive und holographic Headsets direkt an. Wenn Sie Inhalt für ein anderes Gerät wie Oculus Rift oder HTC Vive erstellt haben, weisen diese Abhängigkeiten von Bibliotheken, die über das Betriebssystem-Plattform-API-vorhanden sind. Vorhandene Inhalte zu Windows Mixed Reality quellfilterung umfasst die neuzuweisung von der Verwendung dieser anderen SDKs auf die Windows-APIs. Die [Windows-Plattform-APIs für mixed Reality](https://docs.microsoft.com/uwp/api/Windows.Perception) funktioniert nur in das app-Modell für universelle Windows-Plattform (UWP). Wenn Ihre app für UWP nicht bereits erstellt wurde, wird für die UWP Portieren Teil der Portierung Umgebung seien.

## <a name="porting-overview"></a>Übersicht über die Portieren

Im Allgemeinen sind dies die Schritte zum Portieren von vorhandenem Inhalt:
1. **Stellen Sie sicher, dass Ihr PC Windows 10 Fall Creators Update (16299) ausgeführt wird.** Wir empfehlen nicht mehr aus des Rings jetzt überspringen Insider Preview empfangen erstellt werden. da diese Builds dieser am stabilsten für mixed Reality-Entwicklung nicht.
2. **Aktualisieren Sie auf die neueste Version der Grafiken oder Spiele-Engine.** Spiele-Engines müssen zur Unterstützung von Windows 10 SDK-Version 10.0.15063.0 (veröffentlicht im April 2017) oder höher.
3. **Aktualisieren Sie jede Middleware, -Plug-ins oder Komponenten.** Wenn Ihre app alle Komponenten enthält, ist es eine gute Idee, auf die neueste Version zu aktualisieren. Neuere Versionen der am häufigsten verwendeten-Plug-ins bieten, Unterstützung für UWP wird.
4. **Entfernen Sie Abhängigkeiten von doppelten SDKs**. Je nachdem welche Geräte Ihre Inhalte wurde, müssen Sie entfernen oder bedingt zu kompilieren, (z. B. SteamVR)-SDK damit stattdessen die Windows-APIs ausgeführt werden können.
5. **Über die Buildprobleme arbeiten.** An diesem Punkt bezieht sich in dieser Übung Portieren Ihrer app, Ihre-Engine und die komponentenabhängigkeiten, was man.

## <a name="common-porting-steps"></a>Allgemeine Schritte für die Portierung

### <a name="common-step-1-make-sure-you-have-the-right-development-hardware"></a>Allgemeiner Schritt 1: Stellen Sie sicher, dass Sie die richtigen Entwicklung Hardware haben

Die [Installieren der Tools](install-the-tools.md#for-immersive-vr-headset-development) Seite listet die empfohlenen Development-Hardware.

### <a name="common-step-2-upgrade-to-the-latest-flight-of-windows-10"></a>Allgemeiner Schritt 2: Ein Upgrade auf die neueste Flug mit einer Windows 10

Die Windows Mixed Reality-Plattform ist, weiterhin in der aktiven Entwicklung, und um am effektivsten zu sein, Sie sollten auf dem Flug "Windows-Insider Fast". Um Zugriff auf Windows-Flüge haben, Sie müssen [am Windows Insider-Programm beitreten](https://insider.windows.com/).
1. Installieren Sie die [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)
2. [Join](https://insider.windows.com/) am Windows Insider-Programm.
3. Aktivieren Sie [Entwicklermodus](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
4. Wechseln Sie zu der [Windows Insider Fast Flügen](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview) >--über die Einstellungen > Update und der Abschnitt "Sicherheit"

### <a name="common-step-3-upgrade-to-the-most-recent-build-of-visual-studio"></a>Allgemeiner Schritt 3: Ein Upgrade auf den neuesten Build von Visual Studio
* Informieren Sie sich [Installieren der Tools](install-the-tools.md#installation-checklist) Seite unter Visual Studio 2017

### <a name="common-step-4-be-ready-for-the-store"></a>Allgemeine Schritt 4: Bereit für den Store
* Verwendung [Windows App Certification Kit](https://developer.microsoft.com/windows/develop/app-certification-kit) (auch bekannt als WACK) frühzeitig und häufig!
* Verwendung [Portability Analyzer](https://docs.microsoft.com/dotnet/standard/portability-analyzer) ([herunterladen](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer))

### <a name="common-step-5-choose-the-correct-adapter"></a>Allgemeine Schritt 5: Wählen Sie den richtigen Adapter
* In Systemen wie Notebooks mit zwei GPUs [als Ziel den richtigen Adapter](rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications). Dies gilt für Unity-apps, darüber hinaus auf systemeigenen DirectX-apps, in dem eine ID3D11Device, entweder explizit oder implizit erstellt wird (Media Foundation), für die Funktionalität.

## <a name="unity-porting-guidance"></a>Unity-portierungsleitfadens

### <a name="unity-step-1-follow-the-common-porting-steps"></a>Unity-Schritt 1: Führen Sie die Schritte für häufige Portieren

Führen Sie die allgemeinen Schritte aus. Wählen Sie in Schritt #3 die **Spieleentwicklung mit Unity** arbeitsauslastung. Sie können die optionale Komponente von Unity-Editor deaktivieren, da Sie eine neuere Version von Unity aus den folgenden Anweisungen installieren müssen.

### <a name="unity-step-2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>Unity-Schritt 2: Ein Upgrade auf die neueste öffentliche Builds von Unity mit Unterstützung für Windows-MR
1. Herunterladen der neuesten [empfohlen öffentlichen Builds von Unity](install-the-tools.md) mit mixed Reality zu unterstützen.
2. Speichern Sie eine Kopie des Projekts ein, bevor Sie beginnen
3. Überprüfen Sie die [Dokumentation](https://docs.unity3d.com/Manual/UpgradeGuides.html) zum Portieren von Unity zur Verfügung.
4. Führen Sie die [Anweisungen](https://docs.unity3d.com/Manual/APIUpdater.html) auf Unity-Website für die Verwendung von deren automatische API-Updater
5. Überprüfen Sie und festzustellen Sie, ob weitere Änderungen, die Sie benötigen, um sicherzustellen, damit Ihr Projekt ausgeführt wird, und arbeiten Sie sich durch die verbleibenden Fehlern und Warnungen. Hinweis: Wenn Sie Middleware, von denen Sie abhängen verfügen, müssen Sie diese Middleware zum loslegen (mehr Details in Schritt 3 weiter unten) zu aktualisieren.

### <a name="unity-step-3-upgrade-your-middleware-to-the-latest-versions"></a>Unity-Schritt 3: Aktualisieren Sie Ihre Middleware auf die neuesten Versionen

Mit Unity Updates ist es eine hohe Wahrscheinlichkeit, die Sie benötigen mindestens eine middlewarepakete zu aktualisieren, von denen Ihr Spiel oder Ihre Anwendung abhängt. Darüber hinaus wird die neueste Version aller Ihrer Middleware Ihre Erfolgschancen bei der in der restlichen über den portiervorgang erhöht. Viele middlewarepakete haben vor kurzem Unterstützung für universelle Windows-Plattform (UWP) hinzugefügt, und ein Upgrade auf die aktuellste Version, können Sie die Arbeit zu nutzen.

### <a name="unity-step-4-target-your-application-to-run-on-universal-windows-platform-uwp"></a>Unity-Schritt 4: Ziel der Anwendung für universelle Windows-Plattform (UWP) ausgeführt.

Nach der Installation der Tools müssen Sie Ihre app, die als universelle Windows-app einsatzbereit zu machen.
* Führen Sie die [ausführliche schrittweise exemplarische Vorgehensweise](https://unity3d.com/partners/microsoft/porting-guides) von Unity bereitgestellten. Bitte beachten Sie, dass Sie auf die neueste LTS-Release (alle 20xx.4-Version) für Windows-MR bleiben sollen.
* Weitere Ressourcen für die UWP-Entwicklung, sehen Sie sich die [Handbuch für Windows 10-Entwicklung von Spielen](https://docs.microsoft.com/windows/uwp/gaming/e2e).
* Bitte beachten Sie, dass Unity weiterhin IL2CPP-Unterstützung zu verbessern; IL2CPP erleichtert einige UWP Ports erheblich. Wenn Sie derzeit .net Back-End-Skripts verwenden möchten, sollten Sie die Konvertierung in das IL2CPP-Back-End stattdessen zu nutzen.

Hinweis: Wenn die Anwendung alle Abhängigkeiten auf bestimmte Dienste wie z. B. überein, die aus dem Stream, wodurch müssen Sie sie in diesem Schritt zu deaktivieren. Zu einem späteren Zeitpunkt können Sie sich an die entsprechenden Dienste einbinden, die Windows bereitstellt.

### <a name="unity-step-5-deprecated"></a>Unity-Schritt 5: (Veraltet)

Schritt 5 ist nicht mehr erforderlich. Wir werden es hier verlässt, so, dass die Indizierung von Schritten unverändert bleibt.

### <a name="unity-step-6-get-your-windows-mixed-reality-hardware-set-up"></a>Unity-Schritt 6: Erhalten Sie Ihr Windows Mixed Reality-Hardware einrichten
1. Überprüfen Sie die Schritte [Immersive Kopfhörer-Setup](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)
2. Erfahren Sie mehr über [Verwendung des Simulators Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md) und [Navigieren durch die Windows Mixed Reality-Homepage](navigating-the-windows-mixed-reality-home.md)

### <a name="unity-step-7-target-your-application-to-run-on-windows-mixed-reality"></a>Unity-Schritt 7: Ihre Anwendung zur Ausführung auf Windows Mixed Reality
1. Sie müssen zuerst entfernen oder bedingt zu kompilieren, alle anderen bibliotheksunterstützung spezifisch für einen bestimmten VR-SDK. Diese Ressourcen ändern sich häufig Einstellungen und Eigenschaften auf das Projekt im Möglichkeiten, die nicht mit anderen VR-SDKs, wie z. B. Windows Mixed Reality kompatibel sind.
    * Wenn Ihr Projekt das SteamVR SDK verweist, müssen Sie z. B. aktualisieren Sie Ihr Projekt, um diese prefabs (Vorlagen) und Skript-API-Aufrufe ausschließen, wenn Sie für das Windows Store-Build-Ziel zu exportieren.
    * Spezielle Schritte für die bedingte ausschließen andere VR-SDKs ist in Kürze verfügbar.
2. In Ihrem Unity-Projekt [Windows 10 SDK als Ziel](holograms-100.md#target-windows-10-sdk)
3. Für jede Szene [einrichten die Kamera](holograms-100.md#chapter-2---setup-the-camera)

### <a name="unity-step-8-use-the-stage-to-place-content-on-the-floor"></a>Unity-Schritt 8: Verwenden Sie die Phase, um Inhalt auf dem Boden zu platzieren

Sie können Mixed Reality-Umgebungen erstellen, eine Vielzahl von [auftreten Skalen](coordinate-systems.md).

Wenn Sie Portieren eine **sitzen Skalierung Erfahrung**, müssen Sie sicherstellen, Unity nastaven NA hodnotu der **stationär** Überwachungstyp Speicherplatz:

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

Hiermit wird von Unity globales Koordinatensystem zum Nachverfolgen der [feststehende Verweisrahmen](coordinate-systems.md#spatial-coordinate-systems). In den Modus zum Nachverfolgen von nicht bewegt, wird Inhalt im Editor einfach vor der Kamera-Standardspeicherort platziert (forward ist – Z) wird vor dem Benutzer angezeigt, wenn die app gestartet wird. Um verschoben der Benutzer der Ursprung sitzen, rufen Sie Unity [XR. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) Methode.

Wenn Sie Portieren eine **ständigen Skalierung Erfahrung** oder **Platz Skalierung Erfahrung**, Sie werden Inhalte werden relativ zu dem Boden platzieren. Sie des Benutzers verständlich floor, mit der  **[räumliche Phase](coordinate-systems.md#spatial-coordinate-systems)**, Etage Ursprung und optional Platz Grenze definiert die des Benutzers darstellt, richten Sie während der ersten ausführen. Für diese Umgebungen, müssen Sie sicherstellen, Unity festgelegt ist, um die **RoomScale** Speicherplatz Überwachungstyp. Während RoomScale der Standardwert ist, sollten Sie sie explizit festgelegt, und stellen Sie sicher, dass Sie wieder "true", um Situationen abzufangen, in denen der Benutzer ihren Computer den Raum verschoben wurde, die sie kalibriert, erhalten:

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

Sobald Ihre app erfolgreich der Überwachungstyp Speicherplatz, Inhalte auf der y-platziert RoomScale festgelegt = 0, die auf dem Boden Ebene angezeigt wird. Der Ursprung an (0, 0, 0) werden die bestimmten Stelle auf dem Boden, in denen der Benutzer vor während des Setups Platz mit -Z, die sie während des Setups konfrontiert wurden vorwärts darstellt.

In Skriptcode können Sie rufen Sie die TryGetGeometry-Methode für Sie sind der UnityEngine.Experimental.XR.Boundary-Typ, um eine Begrenzung Vieleck, erhalten ein Grenze TrackedArea angeben werden. Wenn der Benutzer eine Grenze definiert (erhalten Sie wieder eine Liste der Scheitelpunkte), wissen Sie, es ist sicher bereitstellen eine **Platz Skalierung Erfahrung** für den Benutzer, in dem sie eine in der Szene Anleitung zu erstellen.

Beachten Sie, dass das System automatisch die Grenze gerendert wird, wenn der Benutzer es erreicht. Ihre app muss nicht auf dieses Polygon zu verwenden, um die Begrenzung selbst zu rendern.

Weitere Informationen finden Sie unter den [Koordinatensysteme in Unity](coordinate-systems-in-unity.md) Seite.

Einige Anwendungen verwenden ein Rechteck um die Interaktion zu beschränken. Abrufen von das größte angegebenen Rechteck wird in die UWP-API oder Unity nicht direkt unterstützt. Der Beispielcode verknüpften mit unten zeigt wie Sie ein Rechteck innerhalb der Grenzen der Ablaufverfolgung durchgeführt wird. Es Heuristik basiert, nicht die optimale Lösung gefunden werden kann, Ergebnisse sind jedoch im Allgemeinen konsistent mit den Erwartungen. Parameter in der Algorithmus können optimiert werden, um eine genauere Ergebnisse auf Kosten der Verarbeitungszeit zu suchen. Der Algorithmus ist in einer Fork des Mixed Reality Toolkits, die 5.6 Vorschau MRTP-Version von Unity verwendet. Dies ist nicht öffentlich verfügbar. Der Code sollte direkt in Unity 2017.2 und höheren Versionen verwendet werden. Der Code wird in naher Zukunft zu den aktuellen MRTK portiert werden.

[ZIP-Datei der Code auf GitHub](https://github.com/KevinKennedy/MixedRealityToolkit-Unity/releases/tag/5.6.MRTP20) wichtige Dateien:
* Assets/HoloToolkit/Stage/Scripts/StageManager.cs - Beispiel der Nutzung
* Assets/HoloToolkit/Stage/Scripts/LargestRectangle.cs - Implementierung des Algorithmus
* Assets/HoloToolkit-UnitTests/Editor/Stage/LargestRectangleTest.cs - trivial Test des-Algorithmus

Beispiel für Ergebnisse:

![Beispiel für Ergebnisse](images/largestrectangle-400px.jpg)

Algorithmus basiert auf einem Blog von Daniel Smilkov: [Größten Rechteck in einer polygoninstanz](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)

### <a name="unity-step-9-work-through-your-input-model"></a>Unity-Schritt 9: Arbeiten Sie sich durch Ihre Eingabemodell

Jedes Spiel oder eine Anwendung, die für eine vorhandene HMD müssen eine Reihe von Eingaben, die ihn verarbeitet, die Typen von Eingaben, die sie für die Benutzeroberfläche benötigt, und spezifische APIs, die ihn aufruft, um diese Eingaben zu erhalten. Wir haben investiert, bei dem Versuch, ihn so einfach und unkompliziert wie möglich zu nutzen, der Eingaben in Windows Mixed Reality verfügbar zu machen.
1. Lesen Sie die **[Eingabe Portieren von Unity-Handbuch](input-porting-guide-for-unity.md)** Weitere Informationen zur Verwendung macht Windows Mixed Reality Eingabe, und auch heute schon machen kann, die wie Ihre Anwendung zugeordnet.
2. Wählen Sie, ob Sie Unity-Cross-VR-SDK-Eingabe-API nutzen wollen, oder die MR-spezifischen-API Eingabe. Die allgemeine Input.GetButton/Input.GetAxis-APIs werden verwendet, von Unity-VR-apps noch heute für [Oculus Eingabe](https://docs.unity3d.com/Manual/OculusControllers.html) und [OpenVR Eingabe](https://docs.unity3d.com/Manual/OpenVRControllers.html). Wenn Ihre apps bereits für Controller, die während der Übertragung dieser APIs verwenden, dies ist der einfachste Weg – nur müssen Sie Schaltflächen und Achsen in der Eingabe-Manager neu zuordnen.
    * Sie können Controller Bewegungsdaten in Unity mithilfe der entweder den allgemeinen Cross-VR-SDK Input.GetButton/Input.GetAxis APIs oder die MR-spezifische UnityEngine.XR.WSA.Input-APIs zugreifen. (zuvor im Namespace UnityEngine.XR.WSA.Input in Unity 5.6)
    * Finden Sie unter den [Beispiel im Toolkit](https://github.com/Microsoft/HoloToolkit-Unity/pull/572) das Gamepad und während der Übertragung Controller kombiniert.

### <a name="unity-step-10-performance-testing-and-tuning"></a>Unity-Schritt 10: Testen der Leistung und Optimierung

Windows Mixed Reality wird auf eine umfangreiche Klasse von Geräten verfügbar sein, bis zu einem beenden Spiele-PCs, auf umfassende Markt des grundlegenden PCs. Je nachdem welche Markt, die Sie verwenden möchten, besteht ein deutlicher Unterschied in den verfügbaren COMPUTE- und Grafiken Budgets für Ihre Anwendung zur Verfügung. In dieser Übung portieren Sie wahrscheinlich nutzen einen Premium-PC und hatten wichtige COMPUTE- und Grafiken Budgets zu Ihrer app. Wenn Sie Ihre app einem breiteren Publikum zur Verfügung stellen möchten, sollten Sie testen und profilerstellung für Ihre app auf [die repräsentative Hardware, die Sie möchten Ziel](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

Beide [Unity](https://docs.unity3d.com/Manual/Profiler.html) und [Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index) umfassen die Leistungsanalyse und beide [Microsoft](understanding-performance-for-mixed-reality.md) und [Intel](https://software.intel.com/articles/vr-content-developer-guide) Richtlinien veröffentlichen leistungsprofilerstellung und Optimierung. Es steht eine umfassende Beschreibung der Leistung unter [Leistung für Mixed Reality](understanding-performance-for-mixed-reality.md). Darüber hinaus stehen bestimmte Details für Unity unter [Empfehlungen zur Leistung für Unity](performance-recommendations-for-unity.md).

## <a name="see-also"></a>Siehe auch
* [Eingabe Portieren von Unity-Handbuch](input-porting-guide-for-unity.md)
* [Windows Mixed Reality minimale PC Kompatibilität an die hardwareempfehlungen](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Grundlegendes zur Leistung für Mixed Reality](understanding-performance-for-mixed-reality.md)
* [Empfehlungen zur Leistung für Unity](performance-recommendations-for-unity.md)
* [Hinzufügen von Xbox Live-Unterstützung zu Unity für UWP](https://docs.microsoft.com/windows/uwp/xbox-live/get-started-with-partner/partner-add-xbox-live-to-unity-uwp)
