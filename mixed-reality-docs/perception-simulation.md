---
title: Wahrnehmungs Simulation
description: Leitfaden zur Verwendung der Wahrnehmungs Simulations Bibliothek zum Automatisieren von simulierten Eingaben für immersive Anwendungen
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: Hololens, Simulation, Tests
ms.openlocfilehash: 8152181bdbe8c83d2b706b34f1f2fb5d51f4c880
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414529"
---
# <a name="perception-simulation"></a>Wahrnehmungs Simulation

Möchten Sie einen automatisierten Test für Ihre APP erstellen? Möchten Sie, dass Ihre Tests über Komponententests auf Komponentenebene hinausgehen und Ihre APP End-to-End wirklich ausführen? Die Wahrnehmungs Simulation ist das, was Sie suchen. Die Bibliothek für Wahrnehmungs Simulationen sendet Benutzer-und Welt Eingabedaten an Ihre APP, damit Sie Ihre Tests automatisieren können. Beispielsweise können Sie die Eingabe eines Menschen simulieren, das eine bestimmte, wiederholbare Position und dann eine Geste oder einen Bewegungs Controller verwendet.

Die perception Simulation kann simulierte Eingaben wie diese an physische hololens, den hololens-Emulator (1. Generation), den hololens 2-Emulator oder einen PC mit installierter gemischtes Reality-Portal senden. Die Wahrnehmungs Simulation umgeht die Live Sensoren auf einem Mixed Reality-Gerät und sendet simulierte Eingaben an Anwendungen, die auf dem Gerät ausgeführt werden. Anwendungen empfangen diese Eingabeereignisse über dieselben APIs, die Sie immer verwenden, und können den Unterschied zwischen der Ausführung mit echten Sensoren und der Ausführung mit der Wahrnehmungs Simulation nicht erkennen. Die perception Simulation ist dieselbe Technologie, die von den hololens-Emulatoren verwendet wird, um simulierte Eingaben an den virtuellen Computer hololens zu senden.

Beginnen Sie zunächst mit der Verwendung von Simulation in Ihrem Code, indem Sie ein ipertionsimulationmanager-Objekt erstellen. Aus diesem Objekt können Sie Befehle ausgeben, um die Eigenschaften eines simulierten "Menschen" zu steuern, einschließlich der Kopfposition, der Handposition und Gesten, und Sie können Bewegungs Controller aktivieren und bearbeiten.

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>Einrichten eines Visual Studio-Projekts für die Wahrnehmungs Simulation
1. [Installieren Sie den hololens-Emulator](install-the-tools.md) auf dem Entwicklungs-PC. Der Emulator enthält die Bibliotheken, die Sie für die Wahrnehmungs Simulation verwenden werden.
2. Erstellen Sie ein neues Visual C# Studio-Desktop Projekt (ein Konsolen Projekt funktioniert hervorragend für den Einstieg).
3. Fügen Sie dem Projekt die folgenden Binärdateien als Verweise hinzu (Project-> Add-> Reference...). Sie finden Sie unter% Program Files (x86)% \ Microsoft XDE\\(Version), z. b. **% Program Files (x86)% \ Microsoft XDE\\10.0.18362.0** für den hololens 2-Emulator.  (Hinweis: Obwohl die Binärdateien Teil des hololens 2-Emulators sind, funktionieren Sie auch für Windows Mixed Reality auf dem Desktop.) ein. Perceptionsimulationmanager. Interop. dll: verwalteter C# Wrapper für die Wahrnehmungs Simulation.
    b. Perzeptionsimulationrest. dll-Bibliothek zum Einrichten eines websocketkommunikationskanals für die hololens oder den Emulator.
    c. Simulationstream. Interop. dll: freigegebene Typen für die Simulation.
4. Fügen Sie die-Implementierungs Binärdatei "perceptionsimulationmanager. dll" zu Ihrem Projekt hinzu. Fügen Sie Sie zunächst als Binärdatei zum Projekt hinzu (Projekt > Add-> vorhandenes Element...). Speichern Sie Sie als Link, damit Sie nicht in Ihren Projekt Quellordner kopiert wird. ![Fügen Sie dem Projekt die Datei "perceptionsimulationmanager. dll](images/saveaslink.png) " als Link b hinzu. Stellen Sie dann sicher, dass Sie beim Build in den Ausgabeordner kopiert werden. Dies befindet sich auf dem Eigenschaften Blatt für die Binärdatei. ![Markieren Sie "perceptionsimulationmanager. dll", um Sie in das Ausgabeverzeichnis zu kopieren](images/copyalways.png)
5. Legen Sie die Aktive Projektmappenplattform auf x64 fest.  (Verwenden Sie die Configuration Manager, um einen Platt Form Eintrag für x64 zu erstellen, wenn noch keiner vorhanden ist.)

## <a name="creating-an-iperceptionsimulation-manager-object"></a>Erstellen eines ipertionsimulation-Manager-Objekts

Um die Simulation zu steuern, geben Sie Aktualisierungen an Objekten aus, die von einem ipertionsimulationmanager-Objekt abgerufen werden. Der erste Schritt besteht darin, dieses Objekt zu erhalten und es mit Ihrem Zielgerät oder Emulator zu verbinden. Klicken Sie in der [Symbolleiste](using-the-hololens-emulator.md) auf die Schaltfläche Geräte Portal, um die IP-Adresse des Emulators zu erhalten.

![Symbol](images/emulator-deviceportal.png) "Geräte Portal öffnen" **Geräte Portal öffnen**: Öffnen Sie das Windows-Geräteportal für das HoloLens-Betriebssystem im Emulator.  Für Windows Mixed Reality kann dies in der App "Einstellungen" unter "Aktualisieren der & Sicherheit" und dann "für Entwickler" im Abschnitt "Connect using:" unter "Enable Device Portal" abgerufen werden.  Achten Sie darauf, dass Sie die IP-Adresse und den Port beachten.

Zuerst rufen Sie restsimulationstreamsink. Create auf, um ein restsimulationstreamsink-Objekt abzurufen. Dies ist das Zielgerät oder der Emulator, das Sie über eine HTTP-Verbindung steuern werden. Ihre Befehle werden an das [Windows-Geräte Portal](using-the-windows-device-portal.md) , das auf dem Gerät oder Emulator ausgeführt wird, weitergeleitet und verarbeitet. Die vier Parameter, die Sie zum Erstellen eines Objekts benötigen, sind:
* URI-URI: IP-Adresse des Zielgeräts (z. b http://123.123.123.123. ""http://123.123.123.123:50080 oder "")
* System .net. NetworkCredential-Anmelde Informationen: Benutzername/Kennwort für die Verbindung mit dem [Windows-Geräte Portal](using-the-windows-device-portal.md) auf dem Zielgerät oder Emulator. Wenn Sie eine Verbindung mit dem Emulator über seine lokale Adresse herstellen (z. b. 168. *.* . *) auf demselben PC werden alle Anmelde Informationen akzeptiert.
* bool normal: true für normale Priorität, false für niedrige Priorität. In der Regel sollten Sie diese Einstellung für Testszenarien auf *true* festlegen, sodass der Test die Kontrolle übernehmen kann.  Der Emulator und die Windows Mixed Reality-Simulation verwenden Verbindungen mit niedriger Priorität.  Wenn Ihr Test auch eine Verbindung mit niedriger Priorität verwendet, wird die zuletzt festgelegte Verbindung gesteuert.
* System. Threading. CancellationToken Token-Token, um den asynchronen Vorgang abzubrechen.

Zweitens erstellen Sie ipertionsimulationmanager. Dies ist das Objekt, das Sie verwenden, um die Simulation zu steuern. Beachten Sie, dass dies auch in einer Async-Methode erfolgen muss.

## <a name="control-the-simulated-human"></a>Steuern des simulierten Menschen

Ein ipertionsimulationmanager verfügt über eine menschliche Eigenschaft, die ein isimulatedhuman-Objekt zurückgibt. Um den simulierten Menschen zu steuern, führen Sie Vorgänge für dieses Objekt aus. Zum Beispiel:

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a>Einfache Beispiel C# Konsolenanwendung

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

## <a name="note-on-6-dof-controllers"></a>Hinweis auf 6-DOF-Controllern

Vor dem Aufrufen von Eigenschaften für Methoden auf einem simulierten 6-DOF-Controller müssen Sie den Controller aktivieren.  Wenn dies nicht der Fall ist, wird eine Ausnahme ausgelöst.  Ab dem Windows 10-Update von Mai 2019 können simulierte 6-DOF-Controller installiert und aktiviert werden, indem die Status-Eigenschaft für das isimulatedsixdofcontroller-Objekt auf simulatedsixdofcontrollerstatus. Active festgelegt wird.
Beim Windows 10-Update vom Oktober 2018 und früher müssen Sie zuerst einen simulierten 6-DOF-Controller separat installieren, indem Sie das Tool "perceptionsimulationdevice" aufrufen, das sich im Ordner "\Windows\System32" befindet.  Die Verwendung dieses Tools ist wie folgt:


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

Beispiel:

```
    PerceptionSimulationDevice.exe i 6dof 1
```

Folgende Aktionen werden unterstützt:
* i = Installation
* q = Abfrage
* r = entfernen

Unterstützte Instanzen:
* 1 = der linke 6-DOF-Controller
* 2 = der Rechte 6-DOF-Controller

Der Exitcode des Prozesses gibt einen Erfolg (ein NULL-Rückgabewert) oder einen Fehler (ein Rückgabewert ungleich null) an.  Wenn Sie die Aktion "q" verwenden, um abzufragen, ob ein Controller installiert ist oder nicht, ist der Rückgabewert 0 (null), wenn der Controller nicht bereits installiert ist, oder ein (1), wenn der Controller installiert ist.

Wenn Sie einen Controller am Windows 10-Update vom Oktober 2018 oder früher entfernen, legen Sie seinen Status zuerst über die API auf OFF fest, und nennen Sie dann das Tool "perzeptionsimulationdevice".

Beachten Sie, dass dieses Tool als Administrator ausgeführt werden muss.




## <a name="api-reference"></a>API-Referenz

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a>Microsoft. perceptionsimulation. simulateddebug Type

Beschreibt einen simulierten Gerätetyp.

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

**Microsoft. perceptionsimulation. simulatedtovicetype. Reference**

Ein fiktives Referenzgerät, der Standardwert für "perceptionsimulationmanager"

### <a name="microsoftperceptionsimulationheadtrackermode"></a>Microsoft. perceptionsimulation. headtrackermode

Beschreibt einen Head Tracker-Modus.

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

**Microsoft. perceptionsimulation. headtrackermode. Default**

Standard Head-Nachverfolgung. Dies bedeutet, dass das System basierend auf den Lauf Zeit Bedingungen den besten Head-nach Verfolgungs Modus auswählen kann.

**Microsoft. perceptionsimulation. headtrackermode. Orientation**

Nur Ausrichtung Head Tracking. Dies bedeutet, dass die nach verfolgte Position möglicherweise nicht zuverlässig ist und einige Funktionen, die von der Head-Position abhängig sind, möglicherweise nicht verfügbar sind.

**Microsoft. perceptionsimulation. headtrackermode. Position**

Nachverfolgung von positionellen Köpfen. Dies bedeutet, dass die Position und Ausrichtung der überwachten Kopfzeile zuverlässig sind.

### <a name="microsoftperceptionsimulationsimulatedgesture"></a>Microsoft. perceptionsimulation. simulatedgesten

Beschreibt eine simulierte Geste

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

**Microsoft. perceptionsimulation. simulatedgesten. None**

Ein Sentinelwert, mit dem keine Gesten angezeigt werden.

**Microsoft. perceptionsimulation. simulatedgesten. fingerpressed**

Eine gedrückte Stift Bewegung.

**Microsoft. perceptionsimulation. simulatedgesten. fingerreleased**

Eine von Fingern freigegebene Geste.

**Microsoft. perceptionsimulation. simulatedgesten. Home**

Die "Home/System"-Geste.

**Microsoft. perceptionsimulation. simulatedgesten. Max**

Die maximale gültige Geste.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a>Microsoft. perceptionsimulation. simulatedsixdofcontrollerstatus

Die möglichen Zustände eines simulierten 6-DOF-Controllers.

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

**Microsoft. perceptionsimulation. simulatedsixdofcontrollerstatus. Off**

Der 6-DOF-Controller ist ausgeschaltet.

**Microsoft. perceptionsimulation. simulatedsixdofcontrollerstatus. Active**

Der 6-DOF-Controller ist eingeschaltet und wird nachverfolgt.

**Microsoft. perceptionsimulation. simulatedsixdofcontrollerstatus. trackinglost**

Der 6-DOF-Controller ist eingeschaltet, kann aber nicht nachverfolgt werden.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a>Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton

Die unterstützten Schaltflächen auf einem simulierten 6-DOF-Controller.

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

**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. None**

Ein Sentinelwert, mit dem keine Schaltflächen angegeben werden.

**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. Home**

Die Start Schaltfläche wird gedrückt.

**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. Menu**

Die Menü Schaltfläche wird gedrückt.

**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. Grip**

Die Zieh Fläche wird gedrückt.

**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. touchpadpress**

Der Touchpad ist gedrückt.

**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. Select**

Die Schaltfläche auswählen wird gedrückt.

**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. touchpadtouch**

Das Touchpad ist berührt.

**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. Thumbstick**

Der Finger Stick wird gedrückt.

**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. Max**

Die maximale gültige Schaltfläche.


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a>Microsoft. perceptionsimulation. simulatedeyescalibrationstate

Der Kalibrierungs Zustand der simulierten Augen

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

**Microsoft. perceptionsimulation. simulatedeyescalibrationstate. nicht verfügbar**

Die Augen-Kalibrierung ist nicht verfügbar.

**Microsoft. perceptionsimulation. simulatedeyescalibrationstate. Ready**

Die Augen wurden gekalibriert.  Dies ist der Standardwert.

**Microsoft. perceptionsimulation. simulatedeyescalibrationstate. konfiguriert**

Die Augen werden gerade gekalibriert.

**Microsoft. perceptionsimulation. simulatedeyescalibrationstate. usercalibrationbenötigte**

Die Augen müssen kalibriert werden.

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a>Microsoft. perceptionsimulation. simulatedhandjointtrackingaccuracy

Die nach Verfolgungs Genauigkeit einer gemeinsamen Hand.

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

**Microsoft. perceptionsimulation. simulatedhandjointtrackingaccuracy. nicht verfügbar**

Das gemeinsame wird nicht nachverfolgt.

**Microsoft. perceptionsimulation. simulatedhandjointtrackingaccuracy. ungefähre**

Die gemeinsame Position wird abgeleitet.

**Microsoft. perceptionsimulation. simulatedhandjointtrackingaccuracy. Visible**

Das gemeinsame ist vollständig nachverfolgt.

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a>Microsoft. perceptionsimulation. simulatedhandpose

Die nach Verfolgungs Genauigkeit einer gemeinsamen Hand.

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

**Microsoft. perceptionsimulation. simulatedhandpose. Closed**

Die Fingergelenke der Hand werden so konfiguriert, dass Sie eine geschlossene Darstellung widerspiegeln.

**Microsoft. perceptionsimulation. simulatedhandpose. Open**

Die Fingergelenke der Hand werden so konfiguriert, dass Sie eine offene Pose widerspiegeln.

**Microsoft. perceptionsimulation. simulatedhandpose. Point**

Die Fingergelenke der Hand werden so konfiguriert, dass Sie eine Zeige Darstellung widerspiegeln.

**Microsoft. perceptionsimulation. simulatedhandpose. Pinch**

Die Fingergelenke der Hand werden so konfiguriert, dass Sie eine zusammendrücken-Pose widerspiegeln.

**Microsoft. perceptionsimulation. simulatedhandpose. Max**

Der maximale gültige Wert für simulatedhandpose.


### <a name="microsoftperceptionsimulationplaybackstate"></a>Microsoft. perceptionsimulation. playbackstate

Beschreibt den Zustand einer Wiedergabe.

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

**Microsoft. perceptionsimulation. playbackstate. beendet**

Die Aufzeichnung ist zurzeit beendet und ist für die Wiedergabe bereit.

**Microsoft. perceptionsimulation. playbackstate. Play**

Die Aufzeichnung wird zurzeit wiedergegeben.

**Microsoft. perceptionsimulation. playbackstate. angehalten**

Die Aufzeichnung ist derzeit angehalten.

**Microsoft. perceptionsimulation. playbackstate. End**

Die Aufzeichnung hat das Ende erreicht.

### <a name="microsoftperceptionsimulationvector3"></a>Microsoft. perceptionsimulation. Vector3

Beschreibt einen 3-Komponenten Vektor, der einen Punkt oder einen Vektor im 3D-Raum beschreiben könnte.

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

**Microsoft. perceptionsimulation. Vector3. X**

Die X-Komponente des Vektors.

**Microsoft. perceptionsimulation. Vector3. Y**

Die Y-Komponente des Vektors.

**Microsoft. perceptionsimulation. Vector3. Z**

Die Z-Komponente des Vektors.

**Microsoft. perceptionsimulation. Vector3. #ctor (System. Single, System. Single, System. Single)**

Erstellen Sie eine neue Vector3.

Parameter
* x: die x-Komponente des Vektors.
* y: die y-Komponente des Vektors.
* z-die z-Komponente des Vektors.

### <a name="microsoftperceptionsimulationrotation3"></a>Microsoft. perceptionsimulation. Rotation3

Beschreibt eine 3-Komponenten Rotation.

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

**Microsoft. perceptionsimulation. Rotation3. Pitch**

Die Tonkomponente der Drehung um die X-Achse.

**Microsoft. perceptionsimulation. Rotation3. Yaw**

Die GW-Komponente der Drehung, direkt um die Y-Achse.

**Microsoft. perceptionsimulation. Rotation3. Roll**

Die rollenkomponente der Drehung, direkt um die Z-Achse.

**Microsoft. perceptionsimulation. Rotation3. #ctor (System. Single, System. Single, System. Single)**

Erstellen Sie eine neue Rotation3.

Parameter
* Pitch: die Tonkomponente der Drehung.
* Yaw-die Yaw-Komponente der Drehung.
* Rollup der rollforwardkomponente der Drehung.

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a>Microsoft. perceptionsimulation. simulatedhandjointconfiguration

Beschreibt die Konfiguration einer zusammenhängenden in einer simulierten Hand.

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

**Microsoft. perceptionsimulation. simulatedhandjointconfiguration. Position**

Die Position des gemeinsamen.

**Microsoft. perceptionsimulation. simulatedhandjointconfiguration. Rotation**

Die Drehung der gemeinsam.

**Microsoft. perceptionsimulation. simulatedhandjointconfiguration. trackingaccuracy**

Die nach Verfolgungs Genauigkeit der gemeinsamen.


### <a name="microsoftperceptionsimulationfrustum"></a>Microsoft. perceptionsimulation. Frustum

Beschreibt eine Ansicht, wie Sie in der Regel von einer Kamera verwendet wird.

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

**Microsoft. perceptionsimulation. Frustum. Near**

Der Mindestabstand, der in der Frustum-Klasse enthalten ist.

**Microsoft. perceptionsimulation. Frustum. Far**

Der maximale Abstand, der in der Frustum-Klasse enthalten ist.

**Microsoft. perceptionsimulation. Frustum. fieldofiview**

Das horizontale Feld der Ansicht des Frustum im Bogenmaße (kleiner als PI).

**Microsoft. perceptionsimulation. Frustum. AspectRatio**

Das Verhältnis des horizontalen Sicht Felds zum vertikalen Sichtfeld.

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>Microsoft. perceptionsimulation. ipertionsimulationmanager

Der Stamm zum Erstellen der zum Steuern eines Geräts verwendeten Pakete.

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

**Microsoft. perceptionsimulation. ipertionsimulationmanager. Device**

Rufen Sie das simulierte Geräte Objekt ab, das den simulierten Menschen und die simulierte Welt interpretiert.

**Microsoft. perceptionsimulation. ipertionsimulationmanager. Human**

Rufen Sie das-Objekt ab, das den simulierten Menschen steuert.

**Microsoft. perceptionsimulation. ipertionsimulationmanager. Reset**

Setzt die Simulation auf ihren Standardzustand zurück.

### <a name="microsoftperceptionsimulationisimulateddevice"></a>Microsoft. perceptionsimulation. isimulateddevice

Schnittstelle, die das Gerät beschreibt, das die simulierte Welt und den simulierten Menschen interpretiert

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

**Microsoft. perceptionsimulation. isimulateddevice. headtracker**

Rufen Sie den Head Tracker vom simulierten Gerät ab.

**Microsoft. perceptionsimulation. isimulateddevice. Handtracker**

Rufen Sie die Hand Verfolgung vom simulierten Gerät ab.

**Microsoft. perceptionsimulation. isimulateddevice. setsimulatedde vicetype (Microsoft. perceptionsimulation. simulateddebug Type)**

Legen Sie die Eigenschaften des simulierten Geräts so fest, dass Sie dem angegebenen Gerätetyp entsprechen.

Parameter
* Type: der neue Typ des simulierten Geräts

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a>Microsoft. perceptionsimulation. isimulatedheadtracker

Schnittstelle, die den Teil des simulierten Geräts beschreibt, der die Kopfzeile des simulierten Menschen nachverfolgt.

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

**Microsoft. perceptionsimulation. isimulatedheadtracker. headtrackermode**

Ruft den aktuellen Head-Tracker-Modus ab und legt diesen fest.

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a>Microsoft. perceptionsimulation. isimulatedhandtracker

Schnittstelle, die den Teil des simulierten Geräts beschreibt, der die Hände des simulierten Menschen nachverfolgt

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

**Microsoft. perceptionsimulation. isimulatedhandtracker. worldposition**

Rufen Sie die Position des Knotens mit der Welt in Meter ab.

**Microsoft. perceptionsimulation. isimulatedhandtracker. Position**

Ruft die Position der simulierten Hand Tracker relativ zum Mittelpunkt des Kopfes ab und legt diese fest.

**Microsoft. perceptionsimulation. isimulatedhandtracker. Pitch**

Abrufen und Festlegen der nach unten gerichteten Menge der simulierten Hand Tracker.

**Microsoft. perceptionsimulation. isimulatedhandtracker. frustumignored**

Rufen Sie ab, und legen Sie fest, ob der Wert der simulierten Hand Verfolgung ignoriert wird. Wenn Sie ignoriert werden, sind beide Hände immer sichtbar. Wenn Sie nicht ignoriert werden (die Standardeinstellung), sind Sie nur sichtbar, wenn Sie sich innerhalb der Frustum-Klasse des Hand Trackers befinden.

**Microsoft. perceptionsimulation. isimulatedhandtracker. Frustum**

Dient zum Abrufen und Festlegen der Frustum-Eigenschaften, mit denen bestimmt wird, ob die Hände für die simulierte Hand Verfolgung sichtbar sind.

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>Microsoft. perceptionsimulation. isimulatedhuman

Oberfläche der obersten Ebene zum Steuern des simulierten Menschen.

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

**Microsoft. perceptionsimulation. isimulatedhuman. worldposition**

Abrufen und Festlegen der Position des Knotens, der sich auf die Welt bezieht, in Meter. Die Position entspricht einem Punkt in der Mitte der menschlichen Füße.

**Microsoft. perceptionsimulation. isimulatedhuman. Direction**

Abrufen und Festlegen der Richtung der simulierten menschlichen Gesichter in der Welt. 0 Bogenmaße steht nach unten auf der negativen Z-Achse. Positive Bogenmaße drehen sich um die Y-Achse im Uhrzeigersinn.

**Microsoft. perceptionsimulation. isimulatedhuman. Height**

Ruft die Höhe des simulierten menschlichen in Meter ab und legt diese fest.

**Microsoft. perceptionsimulation. isimulatedhuman. Lefthand**

Rufen Sie die linke Seite des simulierten Menschen ab.

**Microsoft. perceptionsimulation. isimulatedhuman. rightHand**

Rufen Sie die Rechte des simulierten Menschen ab.

**Microsoft. perceptionsimulation. isimulatedhuman. Head**

Rufen Sie die Kopfzeile des simulierten Menschen ab.

**Microsoft. perceptionsimulation. isimulatedhuman. Move (Microsoft. perceptionsimulation. Vector3)**

Verschieben Sie den simulierten menschlichen in Relation zur aktuellen Position in Meter.

Parameter
* Translation: die Verschiebung, die relativ zur aktuellen Position verschoben werden soll.

**Microsoft. perceptionsimulation. isimulatedhuman. Rotation (System. Single)**

Drehen des simulierten menschlichen in Relation zur aktuellen Richtung, im Uhrzeigersinn um die Y-Achse

Parameter
* Bogenmaß: der Betrag für die Drehung um die Y-Achse.

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a>Microsoft. perceptionsimulation. ISimulatedHuman2

Wenn Sie isimulatedhuman in ISimulatedHuman2 umwandeln, sind zusätzliche Eigenschaften verfügbar.

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

**Microsoft. perceptionsimulation. ISimulatedHuman2. leftcontroller**

Rufen Sie den linken 6-DOF-Controller ab.

**Microsoft. perceptionsimulation. ISimulatedHuman2. rightcontroller**

Rufen Sie den rechten 6-DOF-Controller ab.


### <a name="microsoftperceptionsimulationisimulatedhand"></a>Microsoft. perceptionsimulation. isimulatedhand

Schnittstelle, die eine Hand des simulierten Menschen beschreibt

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

**Microsoft. perceptionsimulation. isimulatedhand. worldposition**

Rufen Sie die Position des Knotens mit der Welt in Meter ab.

**Microsoft. perceptionsimulation. isimulatedhand. Position**

Abrufen und Festlegen der Position der simulierten Hand in Relation zum menschlichen Wert in Meter.

**Microsoft. perceptionsimulation. isimulatedhand. aktiviert**

Rufen Sie ab, und legen Sie fest, ob die Hand aktuell aktiviert ist

**Microsoft. perceptionsimulation. isimulatedhand. Visible**

Ruft ab, ob die Hand derzeit für simulateddevice sichtbar ist (d. h., ob Sie sich in einer von der Handtracker erkannten Position befindet).

**Microsoft. perceptionsimulation. isimulatedhand. EnsureVisible**

Verschieben Sie die Hand so, dass Sie für simulateddevice sichtbar ist.

**Microsoft. perceptionsimulation. isimulatedhand. Move (Microsoft. perceptionsimulation. Vector3)**

Verschiebt die Position der simulierten Hand in Relation zur aktuellen Position in Meter.

Parameter
* Translation: der Betrag, um den die simulierte Hand übersetzt werden soll.

**Microsoft. perceptionsimulation. isimulatedhand. performgesten (Microsoft. perceptionsimulation. simulatedgesten)**

Führt eine Geste mithilfe der simulierten Hand aus.  Sie wird nur vom System erkannt, wenn die Hand aktiviert ist.

Parameter
* Geste: die auszuführende Geste.

### <a name="microsoftperceptionsimulationisimulatedhand2"></a>Microsoft. perceptionsimulation. ISimulatedHand2

Weitere Eigenschaften werden durch Umwandeln von isimulatedhand in ISimulatedHand2 verfügbar.
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

**Microsoft. perceptionsimulation. ISimulatedHand2. Orientation**

Ruft die Drehung der simulierten Hand ab oder legt Sie fest.  Bei der Betrachtung der Achse wird der Uhrzeigersinn im Uhrzeigersinn gedreht.

### <a name="microsoftperceptionsimulationisimulatedhand3"></a>Microsoft. perceptionsimulation. ISimulatedHand3

Weitere Eigenschaften werden durch Umwandeln von isimulatedhand in ISimulatedHand3 verfügbar.
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

**Microsoft. perceptionsimulation. ISimulatedHand3. getjointconfiguration**

Die gemeinsame Konfiguration für die angegebene Verbindung wird angezeigt.

**Microsoft. perceptionsimulation. ISimulatedHand3. setjointconfiguration**

Legen Sie die gemeinsame Konfiguration für die angegebene Verbindung fest.

**Microsoft. perceptionsimulation. ISimulatedHand3. ".**

Legen Sie die Hand auf eine bekannte Pose mit einem optionalen Flag zum Animieren fest.  Hinweis: das Animieren führt nicht dazu, dass die Gelenke sofort ihre abschließenden gemeinsamen Konfigurationen widerspiegeln.


### <a name="microsoftperceptionsimulationisimulatedhead"></a>Microsoft. perceptionsimulation. isimulatedhead

Schnittstelle, die den Anfang des simulierten Menschen beschreibt.

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

**Microsoft. perceptionsimulation. isimulatedhead. worldposition**

Rufen Sie die Position des Knotens mit der Welt in Meter ab.

**Microsoft. perceptionsimulation. isimulatedhead. Rotation**

Ruft die Drehung des simulierten Kopfes ab. Bei der Betrachtung der Achse wird der Uhrzeigersinn im Uhrzeigersinn gedreht.

**Microsoft. perceptionsimulation. isimulatedhead. Durchmesser**

Ruft den Durchmesser des simulierten Kopfes ab. Dieser Wert wird verwendet, um den Mittelpunkt (Punkt der Drehung) zu bestimmen.

**Microsoft. perceptionsimulation. isimulatedhead. Rotation (Microsoft. perceptionsimulation. Rotation3)**

Drehen Sie den simulierten Kopf in Relation zur aktuellen Drehung. Bei der Betrachtung der Achse wird der Uhrzeigersinn im Uhrzeigersinn gedreht.

Parameter
* Rotation: die Menge, die gedreht werden soll.

### <a name="microsoftperceptionsimulationisimulatedhead2"></a>Microsoft. perceptionsimulation. ISimulatedHead2

Weitere Eigenschaften sind verfügbar, indem ein isimulatedhead-Element in ISimulatedHead2 umgewandelt wird.

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

**Microsoft. perceptionsimulation. ISimulatedHead2. Eyes**

Rufen Sie die Augen des simulierten Menschen ab.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a>Microsoft. perceptionsimulation. isimulatedsixdofcontroller

Eine Schnittstelle, die einen dem simulierten Menschen zugeordneten 6-DOF-Controller beschreibt.

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

**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. worldposition**

Rufen Sie die Position des Knotens mit der Welt in Meter ab.

**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. Status**

Ruft den aktuellen Zustand des Controllers ab oder legt ihn fest.  Der Controller Status muss auf einen anderen Wert als "Off" festgelegt werden, bevor Aufrufe zum Verschieben, drehen oder Drücken von Schaltflächen erfolgreich ausgeführt werden.

**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. Position**

Ruft die Position des simulierten Controllers in Relation zum menschlichen in Meter ab oder legt diese fest.

**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. Orientation**

Ruft die Ausrichtung des simulierten Controllers ab oder legt Sie fest.

**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. Move (Microsoft. perceptionsimulation. Vector3)**

Verschiebt die Position des simulierten Controllers relativ zu seiner aktuellen Position in Meter.

Parameter
* Translation: der Betrag, um den der simulierte Controller übersetzt werden soll.

**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. pressbutton (simulatedsixdofcontrollerbutton)**

Drücken Sie auf dem simulierten Controller eine Schaltfläche.  Sie wird nur vom System erkannt, wenn der Controller aktiviert ist.

Parameter
* Schaltfläche: die Schaltfläche zum drücken.

**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. releasebutton (simulatedsixdofcontrollerbutton)**

Gibt eine Schaltfläche auf dem simulierten Controller frei.  Sie wird nur vom System erkannt, wenn der Controller aktiviert ist.

Parameter
* Button: die Schaltfläche, die freigegeben werden soll.

**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. gettouchpadposition (out float, out float)**

Die Position eines simulierten Fingers im Touchpad des simulierten Controllers erhalten.

Parameter
* x: die horizontale Position des Fingers.
* y-die vertikale Position des Fingers.

**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. settouchpadposition (float, float)**

Legen Sie die Position eines simulierten Fingers auf dem Touchpad des simulierten Controllers fest.

Parameter
* x: die horizontale Position des Fingers.
* y-die vertikale Position des Fingers.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a>Microsoft. perceptionsimulation. ISimulatedSixDofController2

Zusätzliche Eigenschaften und Methoden sind verfügbar, indem ein isimulatedsixdofcontroller in ISimulatedSixDofController2 umgewandelt wird.

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

**Microsoft. perceptionsimulation. ISimulatedSixDofController2. getthumbstickposition (out float, out float)**

Gibt die Position des simulierten thumbsticks auf dem simulierten Controller an.

Parameter
* x: die horizontale Position des fingersticks.
* y: die vertikale Position des Finger anheften.

**Microsoft. perceptionsimulation. ISimulatedSixDofController2. setthumbstickposition (float, float)**

Legen Sie die Position des simulierten thumbsticks auf dem simulierten Controller fest.

Parameter
* x: die horizontale Position des fingersticks.
* y: die vertikale Position des Finger anheften.

**Microsoft. perceptionsimulation. ISimulatedSixDofController2. Akku Level**

Ruft den Akku Pegel des simulierten Controllers ab oder legt ihn fest.  Der Wert muss größer als 0,0 und kleiner oder gleich 100,0 sein.


### <a name="microsoftperceptionsimulationisimulatedeyes"></a>Microsoft. perceptionsimulation. isimulatedeyes

Schnittstelle, die die Augen des simulierten Menschen beschreibt.

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

**Microsoft. perceptionsimulation. isimulatedeyes. Rotation**

Ruft die Drehung der simulierten Augen ab. Bei der Betrachtung der Achse wird der Uhrzeigersinn im Uhrzeigersinn gedreht.

**Microsoft. perceptionsimulation. isimulatedeyes. Rotation (Microsoft. perceptionsimulation. Rotation3)**

Drehen der simulierten Augen in Relation zur aktuellen Drehung. Bei der Betrachtung der Achse wird der Uhrzeigersinn im Uhrzeigersinn gedreht.

Parameter
* Rotation: die Menge, die gedreht werden soll.

**Microsoft. perceptionsimulation. isimulatedeyes. calibrationstate**

Ruft den Kalibrierungs Zustand der simulierten Augen ab oder legt ihn fest.

**Microsoft. perceptionsimulation. isimulatedeyes. worldposition**

Rufen Sie die Position des Knotens mit der Welt in Meter ab.


### <a name="microsoftperceptionsimulationisimulationrecording"></a>Microsoft. perceptionsimulation. isimulationrecording

Schnittstelle für die Interaktion mit einer einzelnen, für die Wiedergabe geladenen Aufzeichnung.

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

**Microsoft. perceptionsimulation. isimulationrecording. DataTypes**

Ruft die Liste der Datentypen in der Aufzeichnung ab.

**Microsoft. perceptionsimulation. isimulationrecording. State**

Ruft den aktuellen Zustand der Aufzeichnung ab.

**Microsoft. perceptionsimulation. isimulationrecording. Play**

Starten Sie die Wiedergabe. Wenn die Aufzeichnung angehalten wurde, wird die Wiedergabe an der angehaltenen Position fortgesetzt. Wenn der Vorgang beendet ist, wird die Wiedergabe am Anfang gestartet. Wenn Sie bereits abgespielt wird, wird dieser-Befehl ignoriert.

**Microsoft. perceptionsimulation. isimulationrecording. Pause**

Hält die Wiedergabe an Ihrer aktuellen Position an. Wenn die Aufzeichnung beendet wird, wird der-Rückruf ignoriert.

**Microsoft. perceptionsimulation. isimulationrecording. Seek (System. UInt64)**

Sucht die Aufzeichnung bis zur angegebenen Zeit (in 100 Nanosekunden-Intervallen von Anfang an) und hält an dieser Stelle an. Wenn die Uhrzeit hinter dem Ende der Aufzeichnung liegt, wird Sie im letzten Frame angehalten.

Parameter
* Ticks-die Zeit, nach der gesucht werden soll.

**Microsoft. perceptionsimulation. isimulationrecording. anhalten**

Beendet die Wiedergabe und setzt die Position auf den Anfang zurück.

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>Microsoft. perceptionsimulation. isimulationrecordingcallback

Schnittstelle zum Empfangen von Zustandsänderungen während der Wiedergabe.

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**Microsoft. perceptionsimulation. isimulationrecordingcallback. playbackstatechanged (Microsoft. perceptionsimulation. playbackstate)**

Wird aufgerufen, wenn sich der Wiedergabe Zustand einer isimulationrecording geändert hat.

Parameter
* newState: der neue Status der Aufzeichnung.

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>Microsoft. perceptionsimulation. perceptionsimulationmanager

Das Stamm Objekt zum Erstellen von perception Simulation-Objekten.

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

**Microsoft. perceptionsimulation. perceptionsimulationmanager. kreateperceptionsimulationmanager (Microsoft. perceptionsimulation. isimulationstreamsink)**

Erstellen Sie ein Objekt zum Erstellen von simulierten Paketen und zum Bereitstellen der Pakete an die angegebene Senke.

Parameter
* Sink: die Senke, die alle generierten Pakete empfängt.

Rückgabewert

Der erstellte Manager.

**Microsoft. perceptionsimulation. perceptionsimulationmanager. kreateperceptionsimulationrecording (System. String)**

Erstellen Sie eine Senke, in der alle empfangenen Pakete in einer Datei unter dem angegebenen Pfad gespeichert werden.

Parameter
* Path: der Pfad der zu erstellenden Datei.

Rückgabewert

Die erstellte Senke.

**Microsoft. perceptionsimulation. perceptionsimulationmanager. loadperceptionsimulationrecording (System. String, Microsoft. perceptionsimulation. isimulationstreamsink Factory)**

Lädt eine Aufzeichnung aus der angegebenen Datei.

Parameter
* Path: der Pfad der zu ladenden Datei.
* Factory: eine Factory, die von der Aufzeichnung zum Erstellen einer isimulationstreamsink bei Bedarf verwendet wird.

Rückgabewert

Die geladene Aufzeichnung.

**Microsoft. perceptionsimulation. perceptionsimulationmanager. loadperceptionsimulationrecording (System. String, Microsoft. perceptionsimulation. isimulationstreamsink Factory, Microsoft. perceptionsimulation. isimulationrecordingcallback)**

Lädt eine Aufzeichnung aus der angegebenen Datei.

Parameter
* Path: der Pfad der zu ladenden Datei.
* Factory: eine Factory, die von der Aufzeichnung zum Erstellen einer isimulationstreamsink bei Bedarf verwendet wird.
* Callback: ein Rückruf, der Updates empfängt, die den Status der Aufzeichnung neu formatidieren.

Rückgabewert

Die geladene Aufzeichnung.

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>Microsoft. perceptionsimulation. streamdatatypes

Beschreibt die unterschiedlichen Typen von Streamdaten.

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

**Microsoft. perceptionsimulation. streamdatatypes. None**

Ein Sentinelwert, der verwendet wird, um keine streamdatentypen anzugeben

**Microsoft. perceptionsimulation. streamdatatypes. Head**

Datenstrom bezüglich der Position und Ausrichtung des Kopfes.

**Microsoft. perceptionsimulation. streamdatatypes. Hands**

Datenstrom in Bezug auf die Position und Gesten von Händen.

**Microsoft. perceptionsimulation. streamdatatypes. spatialmapping**

Datenstrom in Bezug auf die räumliche Zuordnung der Umgebung.

**Microsoft. perceptionsimulation. streamdatatypes. Kalibrierung**

Datenstrom zur Kalibrierung des Geräts. Kalibrierungs Pakete werden nur von einem System im Remote Modus akzeptiert.

**Microsoft. perceptionsimulation. streamdatatypes. Environment**

Datenstrom in Bezug auf die Umgebung des Geräts.

**Microsoft. perceptionsimulation. streamdatatypes. all**

Ein Sentinelwert, der verwendet wird, um alle aufgezeichneten Datentypen anzugeben.

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>Microsoft. perceptionsimulation. isimulationstreamsink

Ein Objekt, das Datenpakete von einem Simulationsdaten Strom empfängt.

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**Microsoft. perceptionsimulation. isimulationstreamsink. onpacketempfang\uint length, Byte [] Packet)**

Empfängt ein einzelnes Paket, das intern eingegeben und mit Versions Angabe versehen ist.

Parameter
* length: die Länge des Pakets.
* Packet: die Daten des Pakets.

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>Microsoft. perceptionsimulation. isimulationstreamsink Factory

Ein Objekt, das isimulationstreamsink erstellt.

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**Microsoft. perceptionsimulation. isimulationstreamsink Factory. kreatesimulationstreamsink ()**

Erstellt eine einzelne Instanz von isimulationstreamsink.

Rückgabewert

Die erstellte Senke.
