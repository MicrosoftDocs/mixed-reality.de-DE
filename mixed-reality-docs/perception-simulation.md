---
title: Perception simulation
description: Eine Anleitung zur Verwendung der Bibliothek Perception Simulation simulierten Eingaben für die immersiven Anwendungen automatisieren
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Simulation, testen
ms.openlocfilehash: 693750eb753bd11cbe7d7cfb47e04f1a3506ca9a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595376"
---
# <a name="perception-simulation"></a>Perception simulation

Möchten Sie die Erstellung ein automatisiertes Tests für Ihre app? Möchten Sie Ihre Tests auf Komponentenebene Komponententests hinausgehen und führen Sie Ihre app End-to-End wirklich? Perception Simulation ist, wonach Sie suchen. Die Wahrnehmung Simulation-Bibliothek sendet gefälschte menschlicher und Eingabedaten Welt an Ihre app, damit Sie Ihre Tests zu automatisieren. Beispielsweise können Sie die Eingabe eines menschlichen Suchen von links und rechts und anschließend ausführen, die eine Geste simulieren.

Perception Simulation kann simulierte Eingabe wie folgt an einen physischen HoloLens, den Emulator für HoloLens oder einen PC mit Mixed Reality-Portal installiert senden. Perception Simulation umgeht die live Sensoren auf einem Gerät Mixed Reality und sendet simulierte Eingabe für Anwendungen, die auf dem Gerät ausgeführt. Anwendungen erhalten diese gefälschte Eingabeereignisse über die gleichen APIs, die sie immer verwenden, und nicht den Unterschied zwischen der Ausführung mit echten Sensoren im Vergleich zu der Wahrnehmung-Simulation mit erkennen. Perception Simulation ist die gleiche Technologie, die von den Emulator für HoloLens zum Senden von simulierten Eingabe den HoloLens virtuellen Computer verwendet.

Simulation wird durch Erstellen eines Objekts IPerceptionSimulationManager gestartet. Aus diesem Objekt können Sie Befehle zum Steuern der Eigenschaften einer simulierten "Menschen", wie z.B. Head Position Hand Position und Gesten ausgeben.

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>Einrichten von Visual Studio-Projekt für die Wahrnehmung Simulation
1. [Installieren Sie den Emulator für HoloLens](install-the-tools.md) auf Ihrem Entwicklungs-PC. Der Emulator enthält die Bibliotheken, die Sie für die Wahrnehmung Simulation verwenden.
2. Erstellen Sie eine neue Visual Studio C# Desktopprojekt (ein Konsolenprojekt funktioniert hervorragend für den Einstieg).
3. Die folgenden Binärdateien dem Projekt als Verweise hinzufügen (Projekt -> Hinzufügen -> Verweis...). Sie finden diese in **% ProgramFiles% (x86) %\Microsoft XDE\10.0.11082.0** ein. PerceptionSimulationManager.Interop.dll - verwalteten C# Wrapper für die Wahrnehmung Simulation.
    b. PerceptionSimulationRest.dll - Bibliothek für das Einrichten eines Web-Socket-Kommunikationskanals für das HoloLens oder den Emulator.
    c. SimulationStream.Interop.dll - freigegebenen Typen für die Simulation.
4. Fügen Sie die Implementierung binäre PerceptionSimulationManager.dll zu Ihrem Projekt ein. Zunächst als Binärdatei zum Projekt hinzufügen (Projekt -> Hinzufügen -> Vorhandenes Element...). Speichern Sie es als einen Link, damit sie es in Ihrem Projektordner für die Quelle nicht kopiert. ![Fügen Sie dem Projekt als Link PerceptionSimulationManager.dll](images/saveaslink.png) b. Stellen Sie sicher, dass es erhalten der in Ihrem Ordner "Output" für Build kopiert. Dies ist im Eigenschaftenblatt für die Binärdatei. ![Mark PerceptionSimulationManager.dll in das Ausgabeverzeichnis kopieren](images/copyalways.png)

## <a name="creating-an-iperceptionsimulation-manager-object"></a>Erstellen eines IPerceptionSimulation-Manager-Objekts

Um die Simulation zu steuern, müssen Sie Updates auf Objekte, die von einem Objekt IPerceptionSimulationManager abgerufen ausgeben. Der erste Schritt ist dieses Objekt abgerufen, und verbinden Sie es auf Ihrem Gerät oder Emulator. Sie können die IP-Adresse Ihrem Emulator abrufen, indem Sie durch Klicken auf die Schaltfläche "Device Portal" in der [Symbolleiste](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)

![Symbol "Device Portal öffnen"](images/emulator-deviceportal.png) **öffnen Device Portal**: Öffnen Sie die Windows Device Portal für das Betriebssystem HoloLens im Emulator.

Zunächst rufen Sie RestSimulationStreamSink.Create zum Abrufen einer RestSimulationStreamSink-Objekts. Dies ist das Zielgerät oder den Emulator, mit denen Sie über eine http-Verbindung gesteuert werden. Die Befehle übergeben und von behandelt werden die [Windows Device Portal](using-the-windows-device-portal.md) auf dem Gerät oder Emulator ausgeführt wird. Die vier Parameter, die Sie ein Objekt erstellt müssen werden:
* URI-Uri - IP-Adresse des Zielgeräts (z. B. "http://123.123.123.123")
* System.Net.NetworkCredential Anmeldeinformationen – Benutzername und Kennwort für die Verbindung mit der [Windows Device Portal](using-the-windows-device-portal.md) auf dem Gerät oder Emulator. Wenn Sie die Verbindung mit dem Emulator über die lokale 168 herstellen. *.* . * Adresse auf einem PC, werden keine Anmeldeinformationen akzeptiert werden.
* normal: "bool" (normale Priorität), "false" für mit niedriger Priorität "true". Sie möchten in der Regel diese Einstellung auf *"true"* für Testszenarien nutzen.
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
                try
                {
                    RestSimulationStreamSink sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        new System.Threading.CancellationToken());

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
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
            Task.Run(async () =>
            {
                try
                {
                    RestSimulationStreamSink sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("http://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        new System.Threading.CancellationToken());

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

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
        }
    }
}
```

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

Sentinelwert verwendet, um keine Gesten anzugeben.

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**

Ein Finger Geste gedrückt

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**

Eine Geste für ein Finger veröffentlicht

**Microsoft.PerceptionSimulation.SimulatedGesture.Home**

Die home-Bewegung

**Microsoft.PerceptionSimulation.SimulatedGesture.Max**

Die maximale gültige stiftbewegungs

### <a name="microsoftperceptionsimulationplaybackstate"></a>Microsoft.PerceptionSimulation.PlaybackState

Beschreibt den Status des eine Wiedergabe

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

Die Aufzeichnung wird zurzeit beendet "und" bereit für die Wiedergabe

**Microsoft.PerceptionSimulation.PlaybackState.Playing**

Die Aufzeichnung wird aktuell wiedergegebenen.

**Microsoft.PerceptionSimulation.PlaybackState.Paused**

Die Aufzeichnung wird angehalten.

**Microsoft.PerceptionSimulation.PlaybackState.End**

Die Aufzeichnung wurde das Ende erreicht.

### <a name="microsoftperceptionsimulationvector3"></a>Microsoft.PerceptionSimulation.Vector3

Beschreibt einen Vektor 3 Komponenten, der einen Punkt oder einen Vektor im 3D-Raum beschreiben können

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

Die X-Komponente des Vektors

**Microsoft.PerceptionSimulation.Vector3.Y**

Die Y-Komponente des Vektors

**Microsoft.PerceptionSimulation.Vector3.Z**

Die Z-Komponente des Vektors

**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**

Erstellen Sie eine neue Vector3

Parameter
* X: die X-Komponente des Vektors
* y - der y-Komponente des Vektors
* Z - die Z-Komponente des Vektors

### <a name="microsoftperceptionsimulationrotation3"></a>Microsoft.PerceptionSimulation.Rotation3

Beschreibt eine Drehung um 3 Komponenten

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

Die Schriftbreite-Komponente, der die Drehung der x-Achse nach-unten

**Microsoft.PerceptionSimulation.Rotation3.Yaw**

Der Yaw-Komponente der Drehung, ganz in der Nähe der y-Achse

**Microsoft.PerceptionSimulation.Rotation3.Roll**

Die Rollup-Komponente von der Rotation nach rechts um die Z-Achse

**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**

Erstellen Sie eine neue Rotation3

Parameter
* Schriftbreite – die Schriftbreite-Komponente der Drehung
* Yaw - der Yaw-Komponente der Drehung
* Zurücksetzen Sie – die Rollup-Komponente der Drehung

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

Der Mindestabstand, der in der Frustums enthalten ist

**Microsoft.PerceptionSimulation.Frustum.Far**

Der maximale Abstand, der in der Frustums enthalten ist

**Microsoft.PerceptionSimulation.Frustum.FieldOfView**

Das horizontale Sichtfeld der Frustums, im Bogenmaß (weniger als PI)

**Microsoft.PerceptionSimulation.Frustum.AspectRatio**

Das Verhältnis der horizontale Sichtfeld auf einer vertikale Sichtfeld

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.IPerceptionSimulationManager

Stammverzeichnis für das Generieren von den Paketen, die zum Steuern eines Geräts

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

Die Position des Knotens in Bezug auf der ganzen Welt in Metern abzurufen

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**

Abrufen und die Position der simulierten Hand Tracker Bezug auf den Mittelpunkt des Anfangswerts festlegen.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**

Abzurufen Sie und festzulegen Sie, die nach unten weisenden Tonhöhe der simulierten Hand-nachverfolgung

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**

Rufen Sie ab und festlegen Sie, ob die Frustums simulierten Hand Tracker ignoriert wird. Wenn ignoriert, sind die beiden Händen immer sichtbar. Wenn (Standard) nicht ignoriert sind praktische nur sichtbar, wenn sie innerhalb der Frustums Hand Tracker sind.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**

Abrufen und Festlegen der Frustums Eigenschaften verwendet, um zu bestimmen, ob die Hände für die nachverfolgung von simulierten Hand sichtbar sind.

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>Microsoft.PerceptionSimulation.ISimulatedHuman

Top Level-Schnittstelle zum Steuern von den simulierten Benutzer

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

Abrufen und Festlegen der Höhe der simulierten vom Menschen in Metern

**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**

Links von den simulierten Benutzer abrufen

**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**

Die rechte Seite von den simulierten Benutzer abrufen

**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**

Der Anfang der simulierten Benutzer abrufen

**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**

Verschieben Sie die simulierte menschliche Bezug auf seine aktuelle Position in Metern

Parameter
* Translation – Übersetzung, relativ zur aktuellen Position verschieben

**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**

Drehen Sie die simulierte menschliche relativ zum aktuellen Richtung, die y-Achse im Uhrzeigersinn

Parameter
* Bogenmaß (Radiant) – der Betrag, um die y-Achse drehen

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

Die Position des Knotens in Bezug auf der ganzen Welt in Metern abzurufen

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
* Übersetzung – der Betrag, um das simulierte Handsymbol übersetzen

**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**

Führen Sie eine Geste für eine mithilfe der simulierten Hand (es wird nur vom System erkannt werden, wenn die Seite aktiviert ist).

Parameter
* Aktion - die Aktion ausführen

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

Die Position des Knotens in Bezug auf der ganzen Welt in Metern abzurufen

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**

Rufen Sie die Rotation der simulierten Head. Positive Bogenmaß (Radiant) werden bei der Suche auf der Achse im Uhrzeigersinn drehen.

**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**

Abrufen des simulierten Anfangselements Durchmesser. Dieser Wert wird verwendet, um zu bestimmen, des Anfangselements Center (Punkt der Drehung).

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**

Drehen Sie die simulierte Head relativ zu dessen aktuellen Rotationsachse. Positive Bogenmaß (Radiant) werden bei der Suche auf der Achse im Uhrzeigersinn drehen.

Parameter
* Rotation – der Betrag, um drehen

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
* Ticks – die Uhrzeit für die Suche

**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**

Die Wiedergabe beendet und setzt die Position zum Anfang

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>Microsoft.PerceptionSimulation.ISimulationRecordingCallback

Schnittstelle für den Empfang von Änderungen des Ansichtszustands während der Wiedergabe

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**

Wird aufgerufen, wenn ein ISimulationRecordings Wiedergabe-Zustand geändert hat

Parameter
* NewState – der neue Status der Aufzeichnung

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.PerceptionSimulationManager

Stammobjekt für das Erstellen von Objekten der Wahrnehmung Simulation

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
* Sink - Senke, die alle generierten Pakete erhalten

Rückgabewert

Der erstellte-Manager

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**

Erstellen Sie eine Senke, die alle empfangenen Pakete in einer Datei unter dem angegebenen Pfad gespeichert.

Parameter
* Pfad – der Pfad des zu erstellenden Datei

Rückgabewert

Die erstellte Senke

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**

Laden Sie eine Aufzeichnung aus der angegebenen Datei

Parameter
* Pfad – der Pfad der zu ladenden Datei
* Factory – eine Factory, die zum Erstellen einer ISimulationStreamSink bei Bedarf durch die Aufzeichnung verwendet

Rückgabewert

Die Aufzeichnung geladen

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory, Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**

Laden Sie eine Aufzeichnung aus der angegebenen Datei

Parameter
* Pfad – der Pfad der zu ladenden Datei
* Factory – eine Factory, die zum Erstellen einer ISimulationStreamSink bei Bedarf durch die Aufzeichnung verwendet
* Rückruf - aktualisiert ein Rückruf an, empfängt die Aufzeichnung des Status Umpacken

Rückgabewert

Die Aufzeichnung geladen

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>Microsoft.PerceptionSimulation.StreamDataTypes

Beschreibt die verschiedenen Typen von Streamdaten

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

Sentinelwert verwendet, um keine Datentypen Stream anzugeben.

**Microsoft.PerceptionSimulation.StreamDataTypes.Head**

Stream der Daten in Bezug auf die Position und Ausrichtung des Anfangswerts

**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**

Stream der Daten in Bezug auf die Position und Gesten Händen

**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**

Stream der Daten in Bezug auf räumliche Zuordnung der Umgebung

**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**

Der Stream der Daten in Bezug auf die Kalibrierung des Geräts. Kalibrierung Pakete werden nur von einem System im Remotemodus angenommen.

**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**

Stream der Daten in Bezug auf die Umgebung des Geräts

**Microsoft.PerceptionSimulation.StreamDataTypes.All**

Sentinelwert verwendet, um alle aufgezeichneten Datentypen anzugeben.

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>Microsoft.PerceptionSimulation.ISimulationStreamSink

Ein Objekt, das Datenpakete aus einem Stream Simulation empfängt.

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived (Uint-Länge, Byte []-Paket)**

Empfängt ein einzelnes Paket, das intern typisierten und mit Versionsangabe versehen ist

Parameter
* Länge - die Länge des Pakets
* Paket - die Daten des Pakets

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory

Ein Objekt, das ISimulationStreamSink erstellt.

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**

Erstellt eine einzelne Instanz der ISimulationStreamSink

Rückgabewert

Die erstellte Senke
