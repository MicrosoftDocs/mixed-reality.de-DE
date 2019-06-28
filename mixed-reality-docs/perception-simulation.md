---
title: Perception simulation
description: Eine Anleitung zur Verwendung der Bibliothek Perception Simulation simulierten Eingaben für die immersiven Anwendungen automatisieren
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: HoloLens, Simulation, testen
ms.openlocfilehash: 8152181bdbe8c83d2b706b34f1f2fb5d51f4c880
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414529"
---
# <a name="perception-simulation"></a>Perception simulation

Möchten Sie die Erstellung ein automatisiertes Tests für Ihre app? Möchten Sie Ihre Tests auf Komponentenebene Komponententests hinausgehen und führen Sie Ihre app End-to-End wirklich? Perception Simulation ist, wonach Sie suchen. Die Wahrnehmung Simulation-Bibliothek sendet menschlichen Welt Eingabe Daten für Ihre app aus, damit Sie Ihre Tests zu automatisieren. Beispielsweise können Sie die Eingabe eines menschlichen an eine bestimmte, wiederholbaren Position gesucht und anschließend ausführen, die eine Geste oder mithilfe eines Controllers während der Übertragung simulieren.

Perception Simulation simulierten Eingabe wie folgt an einen physischen HoloLens, den Emulator für HoloLens senden kann (1. Generation), die HoloLens 2 Emulator oder einem PC mit Mixed Reality-Portal installiert. Perception Simulation umgeht die live Sensoren auf einem Gerät Mixed Reality und sendet simulierte Eingabe für Anwendungen, die auf dem Gerät ausgeführt. Anwendungen erhalten diese Eingabeereignisse über die gleichen APIs, die sie immer verwenden, und den Unterschied zwischen der Ausführung mit echten Sensoren im Vergleich zu der Wahrnehmung-Simulation mit nicht erkennen kann. Perception Simulation ist die gleiche Technologie ein, die HoloLens-Emulatoren für simulierte Eingaben, die HoloLens-VM zu senden.

Um zu beginnen, Simulation im Code verwenden, erstellen Sie zunächst ein IPerceptionSimulationManager-Objekt. Aus diesem Objekt Sie können Befehle, die Eigenschaften einer simulierten "Menschen", wie z.B. Head Position Hand Position und Bewegungen zu steuern und können Sie aktivieren, und Bearbeiten von Motion-Controller.

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>Einrichten von Visual Studio-Projekt für die Wahrnehmung Simulation
1. [Installieren Sie den Emulator für HoloLens](install-the-tools.md) auf Ihrem Entwicklungs-PC. Der Emulator enthält die Bibliotheken, die Sie für die Wahrnehmung Simulation verwenden.
2. Erstellen Sie eine neue Visual Studio C# Desktopprojekt (ein Konsolenprojekt funktioniert hervorragend für den Einstieg).
3. Die folgenden Binärdateien dem Projekt als Verweise hinzufügen (Projekt -> Hinzufügen -> Verweis...). Sie finden diese in % ProgramFiles% (x86) %\Microsoft XDE\\(Version), wie z. B. **% ProgramFiles% (x86) %\Microsoft XDE\\10.0.18362.0** für den 2-Emulator für HoloLens.  (Hinweis: Obwohl die Binärdateien der 2-Emulator für HoloLens angehören, zusätzlich arbeiten für die Windows Mixed Reality auf dem Desktop.) ein. PerceptionSimulationManager.Interop.dll - verwalteten C# Wrapper für die Wahrnehmung Simulation.
    b. PerceptionSimulationRest.dll - Bibliothek für das Einrichten eines Web-Socket-Kommunikationskanals für das HoloLens oder den Emulator.
    c. SimulationStream.Interop.dll - freigegebenen Typen für die Simulation.
4. Fügen Sie die Implementierung binäre PerceptionSimulationManager.dll zu Ihrem Projekt ein. Zunächst als Binärdatei zum Projekt hinzufügen (Projekt -> Hinzufügen -> Vorhandenes Element...). Speichern Sie es als einen Link, damit sie es in Ihrem Projektordner für die Quelle nicht kopiert. ![Fügen Sie dem Projekt als Link PerceptionSimulationManager.dll](images/saveaslink.png) b. Stellen Sie sicher, dass es erhalten der in Ihrem Ordner "Output" für Build kopiert. Dies ist im Eigenschaftenblatt für die Binärdatei. ![Mark PerceptionSimulationManager.dll in das Ausgabeverzeichnis kopieren](images/copyalways.png)
5. Legen Sie Ihre Aktive Projektmappenplattform auf X64 an.  (Verwenden Sie die Configuration Manager einen Plattform-Eintrag für X64 zu erstellen, wenn nicht bereits vorhanden ist.)

## <a name="creating-an-iperceptionsimulation-manager-object"></a>Erstellen eines IPerceptionSimulation-Manager-Objekts

Um die Simulation zu steuern, müssen Sie Updates auf Objekte, die von einem Objekt IPerceptionSimulationManager abgerufen ausgeben. Der erste Schritt ist dieses Objekt abgerufen, und verbinden Sie es auf Ihrem Gerät oder Emulator. Sie können die IP-Adresse Ihrem Emulator abrufen, indem Sie durch Klicken auf die Schaltfläche "Device Portal" in der [Symbolleiste](using-the-hololens-emulator.md)

![Symbol "Device Portal öffnen"](images/emulator-deviceportal.png) **öffnen Device Portal**: Öffnen Sie das Windows-Geräteportal für das HoloLens-Betriebssystem im Emulator.  Für Windows Mixed Reality, dies kann abgerufen werden in der Einstellungs-app unter "Update und Sicherheit" aus, und klicken Sie dann "für Entwickler" in der "Herstellen einer Verbindung mit:" im Abschnitt unter "Enable Device Portal."  Achten Sie darauf, dass Sie den IP-Adresse und die Portnummer zu beachten.

Zunächst rufen Sie RestSimulationStreamSink.Create zum Abrufen einer RestSimulationStreamSink-Objekts. Dies ist das Zielgerät oder den Emulator, mit denen Sie über eine http-Verbindung gesteuert werden. Die Befehle übergeben und von behandelt werden die [Windows Device Portal](using-the-windows-device-portal.md) auf dem Gerät oder Emulator ausgeführt wird. Die vier Parameter, die Sie ein Objekt erstellt müssen werden:
* URI-Uri - IP-Adresse des Zielgeräts (z. B. "http://123.123.123.123"oder"http://123.123.123.123:50080")
* System.Net.NetworkCredential Anmeldeinformationen – Benutzername und Kennwort für die Verbindung mit der [Windows Device Portal](using-the-windows-device-portal.md) auf dem Gerät oder Emulator. Wenn Sie die Verbindung mit dem Emulator über die lokale Adresse herstellen (z. B. 168. *.* . *) auf demselben PC, werden alle Anmeldeinformationen akzeptiert werden.
* normal: "bool" (normale Priorität), "false" für mit niedriger Priorität "true". Sie möchten in der Regel diese Einstellung auf *"true"* für Testszenarien, in dem den Test die Steuerung übernehmen können.  Verwenden den Emulator als auch Windows Mixed Reality-Simulation Verbindungen mit niedriger Priorität.  Wenn der Test auch eine Verbindung mit niedriger Priorität verwendet wird, eingerichtet am häufigsten vor kurzem, dass die Verbindung im Steuerelement werden kann.
* "System.Threading.CancellationToken" Token - Token zum Abbrechen des asynchronen Vorgangs.

Erstellen Sie zweitens die IPerceptionSimulationManager. Dies ist das Objekt, das Sie verwenden, um die Simulation zu steuern. Beachten Sie, dass dies auch in einer asynchronen Methode durchgeführt werden muss.

## <a name="control-the-simulated-human"></a>Steuern Sie die simulierte menschliche

Ein IPerceptionSimulationManager verfügt über eine Human-Eigenschaft, die ein ISimulatedHuman-Objekt zurückgibt. Um die simulierten menschliche zu steuern, die Vorgänge, für dieses Objekt. Zum Beispiel:

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a>Beispiel eines grundlegenden C# Konsolenanwendung

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Task.Run(async () =>
            {
                RestSimulationStreamSink sink = null;
                CancellationToken token = new System.Threading.CancellationToken();

                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }

                // Always close the sink to return control to the previous application.
                if (sink != null)
                {
                    await sink.Close(token);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a>Erweiterte Beispiel C# Konsolenanwendung

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            RestSimulationStreamSink sink = null;
            CancellationToken token = new System.Threading.CancellationToken();

            Task.Run(async () =>
            {
                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

                    // Activate the right hand
                    manager.Human.RightHand.Activated = true;

                    // Simulate Bloom gesture, which should cause Shell to disappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... this time, Shell should reappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate a Head rotation down around the X axis
                    // This should cause gaze to aim about the center of the screen
                    manager.Human.Head.Rotate(new Rotation3(0.04f, 0.0f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a finger press & release
                    // Should cause a tap on the center tile, thus launching it
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate a second finger press & release
                    // Should activate the app that was launched when the center tile was clicked
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(5000);

                    // Simulate a Head rotation towards the upper right corner
                    manager.Human.Head.Rotate(new Rotation3(-0.14f, 0.17f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a third finger press & release
                    // Should press the Remove button on the app
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... bringing the Shell back once more
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();

            // Always close the sink to return control to the previous application.
            if (sink != null)
            {
                sink.Close(token);
            }
        }
    }
}
```

## <a name="note-on-6-dof-controllers"></a>Notieren Sie sich auf 6-FG-Controller

Vor dem Aufrufen von Eigenschaften auf Methoden in einem simulierten 6-FG-Controller, müssen Sie den Controller aktivieren.  Nicht auf diese Weise führt eine Ausnahme ausgelöst.  Ab Windows 10 möglicherweise 2019 aktualisieren, simulierte 6-FG Controller installiert und durch Festlegen der Status-Eigenschaft für das Objekt ISimulatedSixDofController SimulatedSixDofControllerStatus.Active aktiviert werden können.
In Windows 10 Oktober 2018 aktualisieren und früher müssen Sie separat einen simulierten 6-FG Controller zunächst installieren durch Aufrufen der PerceptionSimulationDevice-Tool befindet sich im Ordner \Windows\System32.  Die Verwendung dieses Tools lautet wie folgt aus:


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

Zum Beispiel

```
    PerceptionSimulationDevice.exe i 6dof 1
```

Unterstützte Aktionen sind:
* Ich = Install
* q = query
* R = entfernen

Unterstützte Instanzen werden zu können:
* 1 = den linken 6-FG-Controller
* 2 = die richtige 6-FG-Controller

(Eine NULL-Wert zurückgeben) Erfolg oder Fehler (ein Wert ungleich NULL zurück), wird der Exitcode des Prozesses angegeben.  Wenn die Aktion "Q" zum Abfragen, und zwar unabhängig davon, ob ein Controller installiert ist, wird der zurückgegebene Wert sein, NULL (0), wenn der Controller noch nicht installiert ist oder eins (1), wenn der Controller installiert ist.

Beim Entfernen eines Controllers auf dem Windows aktualisieren Sie 10 Oktober 2018 oder früher legen Sie seinen Status aus über die API zuerst, klicken Sie dann das Tool PerceptionSimulationDevice aufrufen.

Beachten Sie, dass dieses Tool als Administrator ausgeführt werden muss.




## <a name="api-reference"></a>API-Referenz

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a>Microsoft.PerceptionSimulation.SimulatedDeviceType

Beschreibt einen Typ des simulierten Geräts

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**

Ein Gerät fiktiven Verweis, der Standardwert für PerceptionSimulationManager

### <a name="microsoftperceptionsimulationheadtrackermode"></a>Microsoft.PerceptionSimulation.HeadTrackerMode

Beschreibt einen Head-Tracker-Modus

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**

Standard-Head nachverfolgen. Dies bedeutet, dass das System die beste Head Überwachungsmodus basierend auf laufzeitbedingungen auswählen kann.

**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**

Ausrichtung nur Head nachverfolgen. Dies bedeutet, dass die nachverfolgte Position möglicherweise nicht zuverlässig, und einige Funktionen, die abhängig von Head Position möglicherweise nicht Verfügung zur.

**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**

Mit Feldern fester Breite Head-nachverfolgung. Dies bedeutet, dass die nachverfolgten Head Position und Ausrichtung zuverlässig sind

### <a name="microsoftperceptionsimulationsimulatedgesture"></a>Microsoft.PerceptionSimulation.SimulatedGesture

Beschreibt eine Geste für eine simulierte

```
public enum SimulatedGesture
{
    None = 0,
    FingerPressed = 1,
    FingerReleased = 2,
    Home = 4,
    Max = Home
}
```

**Microsoft.PerceptionSimulation.SimulatedGesture.None**

Ein Sentinelwert verwendet, um keine Gesten anzugeben.

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**

Ein Finger Geste gedrückt wird.

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**

Eine Geste Finger veröffentlicht.

**Microsoft.PerceptionSimulation.SimulatedGesture.Home**

Die Start/System-Bewegung.

**Microsoft.PerceptionSimulation.SimulatedGesture.Max**

Die maximale gültige Tastenkombination.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a>Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus

Die möglichen Zustände eines simulierten 6-FG-Controllers.

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**

Der Controller 6-FG ist deaktiviert.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**

6-FG Controller wird eingeschaltet und nachverfolgt.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**

6-FG Controller wird aktiviert, aber es kann nicht nachverfolgt werden.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a>Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton

Die unterstützten Schaltflächen auf einem simulierten 6-FG-Controller.

```
public enum SimulatedSixDofControllerButton
{
    None = 0,
    Home = 1,
    Menu = 2,
    Grip = 4,
    TouchpadPress = 8,
    Select = 16,
    TouchpadTouch = 32,
    Thumbstick = 64,
    Max = Thumbstick
}
```

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**

Ein Sentinelwert verwendet, um keine Schaltflächen anzugeben.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**

Die Start-Schaltfläche gedrückt wird.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**

Die Schaltfläche gedrückt wird.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**

Der Ziehpunkt ist gedrückt.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**

Das TouchPad gedrückt wird.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**

Die auswählen-Schaltfläche gedrückt wird.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**

Das TouchPad ist berührt werden.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**

Ministick gedrückt wird.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**

Die maximale gültige Taste.


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a>Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState

Der Status der Kalibrierung der simulierten Augen

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**

Die Augen Kalibrierung ist nicht verfügbar.

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**

Die Augen haben kalibriert.  Dies ist der Standardwert.

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**

Die Augen werden kalibriert werden.

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**

Die Augen kalibriert werden müssen.

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a>Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy

Die Genauigkeit der nachverfolgung von eine Verbindung der Hand.

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**

Die Verbindung wird nicht nachverfolgt.

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**

Die gemeinsame Position abgeleitet wird.

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**

Die Verbindung wird vollständig nachverfolgt.

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a>Microsoft.PerceptionSimulation.SimulatedHandPose

Die Genauigkeit der nachverfolgung von eine Verbindung der Hand.

```
public enum SimulatedHandPose
{
    Closed = 0,
    Open = 1,
    Point = 2,
    Pinch = 3,
    Max = Pinch
}
```

**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**

Das Handsymbol des Fingers Joints werden entsprechend einer geschlossenen Haltung konfiguriert.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**

Das Handsymbol des Fingers Joints werden eine offene Haltung entsprechend konfiguriert.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**

Das Handsymbol des Fingers Joints werden entsprechend einer zeigen Haltung konfiguriert.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**

Das Handsymbol des Fingers Joints werden entsprechend einer Pinch Haltung konfiguriert.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**

Der gültige Höchstwert für SimulatedHandPose.


### <a name="microsoftperceptionsimulationplaybackstate"></a>Microsoft.PerceptionSimulation.PlaybackState

Beschreibt den Status der eine Wiedergabe.

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

**Microsoft.PerceptionSimulation.PlaybackState.Stopped**

Die Aufzeichnung ist derzeit beendet "und" bereit für die Wiedergabe.

**Microsoft.PerceptionSimulation.PlaybackState.Playing**

Die Aufzeichnung wird aktuell wiedergegebenen.

**Microsoft.PerceptionSimulation.PlaybackState.Paused**

Die Aufzeichnung wird angehalten.

**Microsoft.PerceptionSimulation.PlaybackState.End**

Das Ende wurde die Aufzeichnung erreicht werden.

### <a name="microsoftperceptionsimulationvector3"></a>Microsoft.PerceptionSimulation.Vector3

Beschreibt einen Vektor 3 Komponenten, der einen Punkt oder einen Vektor im 3D-Raum beschreiben kann.

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

**Microsoft.PerceptionSimulation.Vector3.X**

Die X-Komponente des Vektors.

**Microsoft.PerceptionSimulation.Vector3.Y**

Die Y-Komponente des Vektors.

**Microsoft.PerceptionSimulation.Vector3.Z**

Die Z-Komponente des Vektors.

**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**

Erstellen Sie eine neue Vector3.

Parameter
* X: die X-Komponente des Vektors.
* y - der y-Komponente des Vektors.
* Z - der Z-Komponente des Vektors.

### <a name="microsoftperceptionsimulationrotation3"></a>Microsoft.PerceptionSimulation.Rotation3

Beschreibt eine Drehung um 3 Komponenten an.

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

**Microsoft.PerceptionSimulation.Rotation3.Pitch**

Die Schriftbreite-Komponente, der die Drehung nach unten, um die x-Achse.

**Microsoft.PerceptionSimulation.Rotation3.Yaw**

Der Yaw-Komponente der Drehung, ganz in der Nähe der Y-Achse dargestellt.

**Microsoft.PerceptionSimulation.Rotation3.Roll**

Die Rollup-Komponente von der Rotation nach rechts um die Z-Achse.

**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**

Erstellen Sie eine neue Rotation3.

Parameter
* Schriftbreite – die Schriftbreite-Komponente der Drehung.
* Yaw - der Yaw-Komponente der Drehung.
* Rollback - die Rollup-Komponente der Drehung.

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a>Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration

Beschreibt die Konfiguration der eine Verbindung unter einer simulierten Hand.

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**

Die Position des gemeinsamen.

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**

Die Drehung des gemeinsamen.

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**

Die Genauigkeit der nachverfolgung von der Verbindung.


### <a name="microsoftperceptionsimulationfrustum"></a>Microsoft.PerceptionSimulation.Frustum

Beschreibt eine Sicht Frustums, in der Regel durch eine Kamera verwendet.

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

**Microsoft.PerceptionSimulation.Frustum.Near**

Der Mindestabstand, der in der Frustums enthalten ist.

**Microsoft.PerceptionSimulation.Frustum.Far**

Der maximale Abstand, der in der Frustums enthalten ist.

**Microsoft.PerceptionSimulation.Frustum.FieldOfView**

Das horizontale Sichtfeld der der Frustums, im Bogenmaß (weniger als PI).

**Microsoft.PerceptionSimulation.Frustum.AspectRatio**

Das Verhältnis der horizontale Sichtfeld auf einer vertikale Sichtfeld.

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.IPerceptionSimulationManager

Stammverzeichnis für das Generieren der Pakete verwendet, um ein Gerät zu steuern.

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**

Abrufen der simulierten Geräte-Objekt, das die simulierten menschliche und die simulierten Welt interpretiert.

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**

Rufen Sie das Objekt, das die simulierte menschliche steuert.

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**

Die Simulation zurückgesetzt auf ihren Standardzustand.

### <a name="microsoftperceptionsimulationisimulateddevice"></a>Microsoft.PerceptionSimulation.ISimulatedDevice

Schnittstelle, die das Gerät, das in der simulierten Welt und die simulierten menschliche interpretiert beschreibt.

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**

Abrufen der Head-nachverfolgung vom simulierten Gerät an.

**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**

Rufen Sie die nachverfolgung manuell vom simulierten Gerät an.

**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**

Legen Sie die Eigenschaften des simulierten Geräts entsprechend den angegebenen Gerätetyp.

Parameter
* Type - der neuen Typs des simulierten Geräts

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHeadTracker

Schnittstelle, die den Teil des simulierten Geräts, das den Anfang der simulierten Benutzer nachverfolgt beschreibt.

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**

Ruft ab, und setzt den aktuellen Modus des Head-Tracker.

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHandTracker

Schnittstelle, die den Teil des simulierten Geräts, das die Hände von den simulierten Benutzer nachverfolgt beschreibt.

```
public interface ISimulatedHandTracker
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    float Pitch { get; set; }
    bool FrustumIgnored { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    Frustum Frustum { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**

Rufen Sie die Position des Knotens in Bezug auf der ganzen Welt in Meter.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**

Abrufen und die Position der simulierten Hand Tracker Bezug auf den Mittelpunkt des Anfangswerts festlegen.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**

Abrufen und die nach unten weisenden Tonhöhe der nachverfolgung von simulierten manuell festlegen.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**

Rufen Sie ab und festlegen Sie, ob die Frustums simulierten Hand Tracker ignoriert wird. Wenn ignoriert, sind die beiden Händen immer sichtbar. Wenn (Standard) nicht ignoriert sind praktische nur sichtbar, wenn sie innerhalb der Frustums Hand Tracker sind.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**

Abrufen und Festlegen der Frustums Eigenschaften verwendet, um zu bestimmen, ob die Hände für die nachverfolgung von simulierten Hand sichtbar sind.

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>Microsoft.PerceptionSimulation.ISimulatedHuman

Top Level-Schnittstelle zum Steuern von den simulierten Benutzer.

```
public interface ISimulatedHuman 
{
    Vector3 WorldPosition { get; set; }
    float Direction { get; set; }
    float Height { get; set; }
    ISimulatedHand LeftHand { get; }
    ISimulatedHand RightHand { get; }
    ISimulatedHead Head { get; }
    void Move(Vector3 translation);
    void Rotate(float radians);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**

Abzurufen Sie, und legen Sie die Position des Knotens Bezug auf der ganzen Welt, in Meter. Die Position entspricht einem Punkt in der Mitte der Mensch Zentimetern Abweichung.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**

Abrufen und Festlegen der Richtung der simulierten menschliche Gesichter in der ganzen Welt. 0 Bogenmaß Gesichtern nach unten der negativen Z-Achse. Positive Bogenmaß Drehen im Uhrzeigersinn die y-Achse.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**

Abrufen und Festlegen der Höhe der simulierten vom Menschen in Meter.

**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**

Abrufen von links von den simulierten Benutzer.

**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**

Rufen Sie die rechte Seite von den simulierten Benutzer.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**

Rufen Sie den Anfang der simulierten Benutzer.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**

Verschieben Sie die simulierte menschliche Bezug auf seine aktuelle Position in Meter.

Parameter
* Übersetzung: die Verschiebung, relativ zur aktuellen Position zu verschieben.

**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**

Drehen Sie die simulierte menschliche relativ zum aktuellen Richtung, die y-Achse im Uhrzeigersinn

Parameter
* Bogenmaß (Radiant) – der Betrag, um die y-Achse gedreht.

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a>Microsoft.PerceptionSimulation.ISimulatedHuman2

Zusätzliche Eigenschaften zur Verfügung, durch das Umwandeln der ISimulatedHuman zu ISimulatedHuman2

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**

Abgerufen Sie den linke 6-FG-Controller werden.

**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**

Rufen Sie den richtigen 6-FG-Controller.


### <a name="microsoftperceptionsimulationisimulatedhand"></a>Microsoft.PerceptionSimulation.ISimulatedHand

Schnittstelle, die eine Hand von den simulierten Benutzer beschreibt.

```
public interface ISimulatedHand
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    bool Activated { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    bool Visible { [return: MarshalAs(UnmanagedType.Bool)] get; }
    void EnsureVisible();
    void Move(Vector3 translation);
    void PerformGesture(SimulatedGesture gesture);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**

Rufen Sie die Position des Knotens in Bezug auf der ganzen Welt in Meter.

**Microsoft.PerceptionSimulation.ISimulatedHand.Position**

Abrufen und Festlegen der Position eines simulierten relativ zu der vom Menschen in Meter.

**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**

Rufen Sie ab und festlegen Sie, ob das Handsymbol derzeit aktiviert ist.

**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**

Rufen Sie, ob das Handsymbol derzeit sichtbar ist, um die SimulatedDevice ist (z. B. ob er in der Lage, die von der HandTracker erkannt werden ist).

**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**

Verschieben Sie die Hand, dass es für die SimulatedDevice sichtbar ist.

**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**

Verschieben Sie die Position eines simulierten Bezug auf seine aktuelle Position in Meter.

Parameter
* Übersetzung: der Betrag, um die simulierten manuell übersetzt.

**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**

Führen Sie eine Geste für eine mithilfe der simulierten Hand.  Es wird nur vom System erkannt werden, wenn die Seite aktiviert ist.

Parameter
* Tastenkombination: die Geste zum Ausführen.

### <a name="microsoftperceptionsimulationisimulatedhand2"></a>Microsoft.PerceptionSimulation.ISimulatedHand2

Zusätzliche Eigenschaften sind durch das Umwandeln einer ISimulatedHand zu ISimulatedHand2 verfügbar.
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**

Rufen Sie ab, oder legen Sie die Rotation der simulierten Hand.  Positive Bogenmaß (Radiant) werden bei der Suche auf der Achse im Uhrzeigersinn drehen.

### <a name="microsoftperceptionsimulationisimulatedhand3"></a>Microsoft.PerceptionSimulation.ISimulatedHand3

Zusätzliche Eigenschaften zur Verfügung, durch das Umwandeln einer ISimulatedHand zu ISimulatedHand3
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**

Rufen Sie die gemeinsame Konfiguration für die angegebene Verbindung.

**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**

Legen Sie die gemeinsame Konfiguration für die angegebene Verbindung.

**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**

Legen Sie das Handsymbol, auf einen bekannten Haltung mit ein optionalen Kennzeichen, um zu animieren.  Hinweis: Animieren in Joints sofort reflektieren ihren endgültigen gemeinsamen Konfigurationen wird nicht dazu.


### <a name="microsoftperceptionsimulationisimulatedhead"></a>Microsoft.PerceptionSimulation.ISimulatedHead

Schnittstelle, die den Anfang der simulierten Menschen beschreibt.

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**

Rufen Sie die Position des Knotens in Bezug auf der ganzen Welt in Meter.

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**

Rufen Sie die Rotation der simulierten Head. Positive Bogenmaß (Radiant) werden bei der Suche auf der Achse im Uhrzeigersinn drehen.

**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**

Abrufen des simulierten Anfangselements Durchmesser. Dieser Wert wird verwendet, um zu bestimmen, des Anfangselements Center (Punkt der Drehung).

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**

Drehen Sie die simulierte Head relativ zu dessen aktuellen Rotationsachse. Positive Bogenmaß (Radiant) werden bei der Suche auf der Achse im Uhrzeigersinn drehen.

Parameter
* Rotation – der Betrag, um zu drehen.

### <a name="microsoftperceptionsimulationisimulatedhead2"></a>Microsoft.PerceptionSimulation.ISimulatedHead2

Zusätzliche Eigenschaften zur Verfügung, durch das Umwandeln einer ISimulatedHead zu ISimulatedHead2

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**

Rufen Sie die Augen der simulierten Mensch.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a>Microsoft.PerceptionSimulation.ISimulatedSixDofController

Schnittstelle, die einen 6-FG-Controller mit dem simulierten Menschen verknüpften beschreibt.

```
public interface ISimulatedSixDofController
{
    Vector3 WorldPosition { get; }
    SimulatedSixDofControllerStatus Status { get; set; }
    Vector3 Position { get; }
    Rotation3 Orientation { get; set; }
    void Move(Vector3 translation);
    void PressButton(SimulatedSixDofControllerButton button);
    void ReleaseButton(SimulatedSixDofControllerButton button);
    void GetTouchpadPosition(out float x, out float y);
    void SetTouchpadPosition(float x, float y);
}
```

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**

Rufen Sie die Position des Knotens in Bezug auf der ganzen Welt in Meter.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**

Rufen Sie ab, oder legen Sie den aktuellen Status des Controllers.  Der Status des Controllers muss auf einen Wert festgelegt werden, außer aus vor allen Aufrufen von verschieben, drehen, oder drücken die Schaltflächen erfolgreich ausgeführt werden.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**

Abrufen oder Festlegen der Position des simulierten Controllers relativ zu der vom Menschen in Meter.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**

Abrufen oder Festlegen der Ausrichtung des simulierten Controllers.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**

Verschieben Sie die Position des simulierten Controllers Bezug auf seine aktuelle Position in Meter.

Parameter
* Übersetzung: der Betrag, um den simulierten Controller zu übersetzen.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**

Drücken Sie eine Schaltfläche auf dem simulierten Controller aus.  Es wird nur vom System erkannt werden, wenn der Controller aktiviert ist.

Parameter
* -Die Schaltfläche drücken.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**

Freigeben einer Schaltfläche auf dem simulierten Controller.  Es wird nur vom System erkannt werden, wenn der Controller aktiviert ist.

Parameter
* -Die Schaltfläche freigeben.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**

Die Position mit einem simulierten Finger auf der simulierten Controller Touchpad abzurufen.

Parameter
* X – die horizontale Position des Fingers.
* y - die vertikale Position des Fingers.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**

Positionieren Sie die mit einem simulierten Finger auf der simulierten Controller Touchpad.

Parameter
* X – die horizontale Position des Fingers.
* y - die vertikale Position des Fingers.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a>Microsoft.PerceptionSimulation.ISimulatedSixDofController2

Zusätzliche Eigenschaften und Methoden sind verfügbar, durch das Umwandeln einer ISimulatedSixDofController zu ISimulatedSixDofController2

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**

Die Position des simulierten Ministick auf dem simulierten Controller abzurufen.

Parameter
* X – die horizontale Position des Ministick.
* y - die vertikale Position des Ministick.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**

Legen Sie die Position des simulierten Ministick, auf dem simulierten Controller.

Parameter
* X – die horizontale Position des Ministick.
* y - die vertikale Position des Ministick.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**

Abrufen oder Festlegen der Ladezustand der Batterie des simulierten Controllers.  Der Wert muss größer als 0,0 sein und kleiner als oder gleich 100,0.


### <a name="microsoftperceptionsimulationisimulatedeyes"></a>Microsoft.PerceptionSimulation.ISimulatedEyes

Schnittstelle, die die Augen der simulierten Mensch beschreibt.

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**

Rufen Sie die Rotation der simulierten Augen. Positive Bogenmaß (Radiant) werden bei der Suche auf der Achse im Uhrzeigersinn drehen.

**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**

Drehen Sie die simulierten Augen relativ zu dessen aktuellen Rotationsachse. Positive Bogenmaß (Radiant) werden bei der Suche auf der Achse im Uhrzeigersinn drehen.

Parameter
* Rotation – der Betrag, um zu drehen.

**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**

Ruft ab, oder legt diesen fest den Status der Kalibrierung der simulierten Augen.

**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**

Rufen Sie die Position des Knotens in Bezug auf der ganzen Welt in Meter.


### <a name="microsoftperceptionsimulationisimulationrecording"></a>Microsoft.PerceptionSimulation.ISimulationRecording

Eine Schnittstelle für die Interaktion mit einem einzelnen geladen, für die Wiedergabe aufzeichnen.

```
public interface ISimulationRecording
{
    StreamDataTypes DataTypes { get; }
    PlaybackState State { get; }
    void Play();
    void Pause();
    void Seek(UInt64 ticks);
    void Stop();
};
```

**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**

Ruft eine Liste der Datentypen in die Aufzeichnung.

**Microsoft.PerceptionSimulation.ISimulationRecording.State**

Ruft den aktuellen Status der Aufzeichnung ab.

**Microsoft.PerceptionSimulation.ISimulationRecording.Play**

Die Wiedergabe zu starten. Wenn die Aufzeichnung angehalten wird, wird die Wiedergabe aus dem angehaltenen Speicherort fortgesetzt; Wenn beendet, wird die Wiedergabe am Anfang beginnen. Wenn bereits abgespielt wird, wird dieser Aufruf ignoriert.

**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**

Hält die Wiedergabe an dessen aktuellen Speicherort an. Wenn die Aufzeichnung beendet wird, wird der Aufruf ignoriert.

**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**

Suchen die Aufzeichnung auf die angegebene Zeit (in 100-Nanosekunden-Intervallen ab) und an dieser Position angehalten wird. Wenn die Zeit nach dem Ende der Aufzeichnung ist, wird es im letzten Frame angehalten.

Parameter
* Ticks - die Zeit, um zu suchen.

**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**

Die Wiedergabe beendet, und setzt die Position, an den Anfang.

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>Microsoft.PerceptionSimulation.ISimulationRecordingCallback

Eine Schnittstelle für den Empfang von Änderungen des Ansichtszustands während der Wiedergabe.

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**

Wird aufgerufen, wenn es sich bei einer ISimulationRecordings Wiedergabe-Zustand geändert hat.

Parameter
* NewState – der neue Status der Aufzeichnung.

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.PerceptionSimulationManager

Stammobjekt zum Erstellen von Perception Simulation-Objekten.

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**

Erstellen Sie auf das Objekt zum Generieren von simulierten Pakete und an die angegebene Senke bereitstellen.

Parameter
* Sink - Senke, die alle generierten Pakete empfangen wird.

Rückgabewert

Der erstellte-Manager.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**

Erstellen Sie eine Senke, die alle empfangenen Pakete in einer Datei unter dem angegebenen Pfad gespeichert.

Parameter
* Pfad – der Pfad des zu erstellenden Datei.

Rückgabewert

Die erstellte Senke.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**

Laden Sie eine Aufzeichnung aus der angegebenen Datei.

Parameter
* Pfad – der Pfad der zu ladenden Datei.
* Factory – eine Factory, die durch die Aufzeichnung für die Erstellung einer ISimulationStreamSink bei Bedarf verwendet.

Rückgabewert

Die geladenen Aufzeichnung.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory, Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**

Laden Sie eine Aufzeichnung aus der angegebenen Datei.

Parameter
* Pfad – der Pfad der zu ladenden Datei.
* Factory – eine Factory, die durch die Aufzeichnung für die Erstellung einer ISimulationStreamSink bei Bedarf verwendet.
* Rückruf - aktualisiert ein Rückruf an, empfängt die Aufzeichnung des Status Umpacken.

Rückgabewert

Die geladenen Aufzeichnung.

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>Microsoft.PerceptionSimulation.StreamDataTypes

Beschreibt die verschiedenen Typen von datenstromdaten an.

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    All = None | Head | Hands | SpatialMapping | Calibration | Environment
}
```

**Microsoft.PerceptionSimulation.StreamDataTypes.None**

Ein Sentinelwert verwendet, um keine Datentypen Stream anzugeben.

**Microsoft.PerceptionSimulation.StreamDataTypes.Head**

Der Stream der Daten in Bezug auf die Position und Ausrichtung des Anfangswerts.

**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**

Der Stream der Daten in Bezug auf die Position und Gesten Händen.

**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**

Der Stream der Daten in Bezug auf räumliche Zuordnung der Umgebung.

**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**

Der Stream der Daten in Bezug auf die Kalibrierung des Geräts. Kalibrierung Pakete werden nur von einem System im Remotemodus angenommen.

**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**

Der Stream der Daten in Bezug auf die Umgebung des Geräts.

**Microsoft.PerceptionSimulation.StreamDataTypes.All**

Ein Sentinelwert verwendet, um alle aufgezeichneten Datentypen anzugeben.

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>Microsoft.PerceptionSimulation.ISimulationStreamSink

Ein Objekt, das Datenpakete aus einem Stream Simulation empfängt.

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived (Uint-Länge, Byte []-Paket)**

Empfängt ein einzelnes Paket, das intern typisierten und mit Versionsangabe versehen ist.

Parameter
* Länge - die Länge des Pakets.
* Paket - die Daten des Pakets.

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory

Ein Objekt, das ISimulationStreamSink erstellt.

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**

Erstellt eine einzelne Instanz von ISimulationStreamSink an.

Rückgabewert

Die erstellte Senke.
