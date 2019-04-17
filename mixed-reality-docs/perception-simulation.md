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
# <a name="perception-simulation"></a><span data-ttu-id="3974f-104">Perception simulation</span><span class="sxs-lookup"><span data-stu-id="3974f-104">Perception simulation</span></span>

<span data-ttu-id="3974f-105">Möchten Sie die Erstellung ein automatisiertes Tests für Ihre app?</span><span class="sxs-lookup"><span data-stu-id="3974f-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="3974f-106">Möchten Sie Ihre Tests auf Komponentenebene Komponententests hinausgehen und führen Sie Ihre app End-to-End wirklich?</span><span class="sxs-lookup"><span data-stu-id="3974f-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="3974f-107">Perception Simulation ist, wonach Sie suchen.</span><span class="sxs-lookup"><span data-stu-id="3974f-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="3974f-108">Die Wahrnehmung Simulation-Bibliothek sendet gefälschte menschlicher und Eingabedaten Welt an Ihre app, damit Sie Ihre Tests zu automatisieren.</span><span class="sxs-lookup"><span data-stu-id="3974f-108">The Perception Simulation library sends fake human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="3974f-109">Beispielsweise können Sie die Eingabe eines menschlichen Suchen von links und rechts und anschließend ausführen, die eine Geste simulieren.</span><span class="sxs-lookup"><span data-stu-id="3974f-109">For example, you can simulate the input of a human looking left and right and then performing a gesture.</span></span>

<span data-ttu-id="3974f-110">Perception Simulation kann simulierte Eingabe wie folgt an einen physischen HoloLens, den Emulator für HoloLens oder einen PC mit Mixed Reality-Portal installiert senden.</span><span class="sxs-lookup"><span data-stu-id="3974f-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="3974f-111">Perception Simulation umgeht die live Sensoren auf einem Gerät Mixed Reality und sendet simulierte Eingabe für Anwendungen, die auf dem Gerät ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="3974f-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="3974f-112">Anwendungen erhalten diese gefälschte Eingabeereignisse über die gleichen APIs, die sie immer verwenden, und nicht den Unterschied zwischen der Ausführung mit echten Sensoren im Vergleich zu der Wahrnehmung-Simulation mit erkennen.</span><span class="sxs-lookup"><span data-stu-id="3974f-112">Applications receive these fake input events through the same APIs they always use, and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="3974f-113">Perception Simulation ist die gleiche Technologie, die von den Emulator für HoloLens zum Senden von simulierten Eingabe den HoloLens virtuellen Computer verwendet.</span><span class="sxs-lookup"><span data-stu-id="3974f-113">Perception Simulation is the same technology used by the HoloLens emulator to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="3974f-114">Simulation wird durch Erstellen eines Objekts IPerceptionSimulationManager gestartet.</span><span class="sxs-lookup"><span data-stu-id="3974f-114">Simulation starts by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="3974f-115">Aus diesem Objekt können Sie Befehle zum Steuern der Eigenschaften einer simulierten "Menschen", wie z.B. Head Position Hand Position und Gesten ausgeben.</span><span class="sxs-lookup"><span data-stu-id="3974f-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="3974f-116">Einrichten von Visual Studio-Projekt für die Wahrnehmung Simulation</span><span class="sxs-lookup"><span data-stu-id="3974f-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="3974f-117">[Installieren Sie den Emulator für HoloLens](install-the-tools.md) auf Ihrem Entwicklungs-PC.</span><span class="sxs-lookup"><span data-stu-id="3974f-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="3974f-118">Der Emulator enthält die Bibliotheken, die Sie für die Wahrnehmung Simulation verwenden.</span><span class="sxs-lookup"><span data-stu-id="3974f-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="3974f-119">Erstellen Sie eine neue Visual Studio C# Desktopprojekt (ein Konsolenprojekt funktioniert hervorragend für den Einstieg).</span><span class="sxs-lookup"><span data-stu-id="3974f-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="3974f-120">Die folgenden Binärdateien dem Projekt als Verweise hinzufügen (Projekt -> Hinzufügen -> Verweis...). Sie finden diese in **% ProgramFiles% (x86) %\Microsoft XDE\10.0.11082.0** ein.</span><span class="sxs-lookup"><span data-stu-id="3974f-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in **%ProgramFiles(x86)%\Microsoft XDE\10.0.11082.0** a.</span></span> <span data-ttu-id="3974f-121">PerceptionSimulationManager.Interop.dll - verwalteten C# Wrapper für die Wahrnehmung Simulation.</span><span class="sxs-lookup"><span data-stu-id="3974f-121">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="3974f-122">b.</span><span class="sxs-lookup"><span data-stu-id="3974f-122">b.</span></span> <span data-ttu-id="3974f-123">PerceptionSimulationRest.dll - Bibliothek für das Einrichten eines Web-Socket-Kommunikationskanals für das HoloLens oder den Emulator.</span><span class="sxs-lookup"><span data-stu-id="3974f-123">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="3974f-124">c.</span><span class="sxs-lookup"><span data-stu-id="3974f-124">c.</span></span> <span data-ttu-id="3974f-125">SimulationStream.Interop.dll - freigegebenen Typen für die Simulation.</span><span class="sxs-lookup"><span data-stu-id="3974f-125">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="3974f-126">Fügen Sie die Implementierung binäre PerceptionSimulationManager.dll zu Ihrem Projekt ein.</span><span class="sxs-lookup"><span data-stu-id="3974f-126">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="3974f-127">Zunächst als Binärdatei zum Projekt hinzufügen (Projekt -> Hinzufügen -> Vorhandenes Element...). Speichern Sie es als einen Link, damit sie es in Ihrem Projektordner für die Quelle nicht kopiert.</span><span class="sxs-lookup"><span data-stu-id="3974f-127">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="3974f-128">![Fügen Sie dem Projekt als Link PerceptionSimulationManager.dll](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="3974f-128">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="3974f-129">Stellen Sie sicher, dass es erhalten der in Ihrem Ordner "Output" für Build kopiert.</span><span class="sxs-lookup"><span data-stu-id="3974f-129">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="3974f-130">Dies ist im Eigenschaftenblatt für die Binärdatei.</span><span class="sxs-lookup"><span data-stu-id="3974f-130">This is in the property sheet for the binary .</span></span> <span data-ttu-id="3974f-131">![Mark PerceptionSimulationManager.dll in das Ausgabeverzeichnis kopieren](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="3974f-131">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="3974f-132">Erstellen eines IPerceptionSimulation-Manager-Objekts</span><span class="sxs-lookup"><span data-stu-id="3974f-132">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="3974f-133">Um die Simulation zu steuern, müssen Sie Updates auf Objekte, die von einem Objekt IPerceptionSimulationManager abgerufen ausgeben.</span><span class="sxs-lookup"><span data-stu-id="3974f-133">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="3974f-134">Der erste Schritt ist dieses Objekt abgerufen, und verbinden Sie es auf Ihrem Gerät oder Emulator.</span><span class="sxs-lookup"><span data-stu-id="3974f-134">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="3974f-135">Sie können die IP-Adresse Ihrem Emulator abrufen, indem Sie durch Klicken auf die Schaltfläche "Device Portal" in der [Symbolleiste](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)</span><span class="sxs-lookup"><span data-stu-id="3974f-135">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md#anatomy-of-the-hololens-emulator)</span></span>

<span data-ttu-id="3974f-136">![Symbol "Device Portal öffnen"](images/emulator-deviceportal.png) **öffnen Device Portal**: Öffnen Sie die Windows Device Portal für das Betriebssystem HoloLens im Emulator.</span><span class="sxs-lookup"><span data-stu-id="3974f-136">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>

<span data-ttu-id="3974f-137">Zunächst rufen Sie RestSimulationStreamSink.Create zum Abrufen einer RestSimulationStreamSink-Objekts.</span><span class="sxs-lookup"><span data-stu-id="3974f-137">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="3974f-138">Dies ist das Zielgerät oder den Emulator, mit denen Sie über eine http-Verbindung gesteuert werden.</span><span class="sxs-lookup"><span data-stu-id="3974f-138">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="3974f-139">Die Befehle übergeben und von behandelt werden die [Windows Device Portal](using-the-windows-device-portal.md) auf dem Gerät oder Emulator ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="3974f-139">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="3974f-140">Die vier Parameter, die Sie ein Objekt erstellt müssen werden:</span><span class="sxs-lookup"><span data-stu-id="3974f-140">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="3974f-141">URI-Uri - IP-Adresse des Zielgeräts (z. B. "http://123.123.123.123")</span><span class="sxs-lookup"><span data-stu-id="3974f-141">Uri uri - IP address of the target device (e.g., "http://123.123.123.123")</span></span>
* <span data-ttu-id="3974f-142">System.Net.NetworkCredential Anmeldeinformationen – Benutzername und Kennwort für die Verbindung mit der [Windows Device Portal](using-the-windows-device-portal.md) auf dem Gerät oder Emulator.</span><span class="sxs-lookup"><span data-stu-id="3974f-142">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="3974f-143">Wenn Sie die Verbindung mit dem Emulator über die lokale 168 herstellen. *.* . \* Adresse auf einem PC, werden keine Anmeldeinformationen akzeptiert werden.</span><span class="sxs-lookup"><span data-stu-id="3974f-143">If you are connecting to the emulator via its local 168.*.*.\* address on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="3974f-144">normal: "bool" (normale Priorität), "false" für mit niedriger Priorität "true".</span><span class="sxs-lookup"><span data-stu-id="3974f-144">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="3974f-145">Sie möchten in der Regel diese Einstellung auf *"true"* für Testszenarien nutzen.</span><span class="sxs-lookup"><span data-stu-id="3974f-145">You generally want to set this to *true* for test scenarios.</span></span>
* <span data-ttu-id="3974f-146">"System.Threading.CancellationToken" Token - Token zum Abbrechen des asynchronen Vorgangs.</span><span class="sxs-lookup"><span data-stu-id="3974f-146">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="3974f-147">Erstellen Sie zweitens die IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="3974f-147">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="3974f-148">Dies ist das Objekt, das Sie verwenden, um die Simulation zu steuern.</span><span class="sxs-lookup"><span data-stu-id="3974f-148">This is the object you use to control simulation.</span></span> <span data-ttu-id="3974f-149">Beachten Sie, dass dies auch in einer asynchronen Methode durchgeführt werden muss.</span><span class="sxs-lookup"><span data-stu-id="3974f-149">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="3974f-150">Steuern Sie die simulierte menschliche</span><span class="sxs-lookup"><span data-stu-id="3974f-150">Control the simulated Human</span></span>

<span data-ttu-id="3974f-151">Ein IPerceptionSimulationManager verfügt über eine Human-Eigenschaft, die ein ISimulatedHuman-Objekt zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="3974f-151">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="3974f-152">Um die simulierten menschliche zu steuern, die Vorgänge, für dieses Objekt.</span><span class="sxs-lookup"><span data-stu-id="3974f-152">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="3974f-153">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="3974f-153">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="3974f-154">Beispiel eines grundlegenden C# Konsolenanwendung</span><span class="sxs-lookup"><span data-stu-id="3974f-154">Basic Sample C# console application</span></span>

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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="3974f-155">Erweiterte Beispiel C# Konsolenanwendung</span><span class="sxs-lookup"><span data-stu-id="3974f-155">Extended Sample C# console application</span></span>

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

## <a name="api-reference"></a><span data-ttu-id="3974f-156">API-Referenz</span><span class="sxs-lookup"><span data-stu-id="3974f-156">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="3974f-157">Microsoft.PerceptionSimulation.SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="3974f-157">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="3974f-158">Beschreibt einen Typ des simulierten Geräts</span><span class="sxs-lookup"><span data-stu-id="3974f-158">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="3974f-159">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span><span class="sxs-lookup"><span data-stu-id="3974f-159">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="3974f-160">Ein Gerät fiktiven Verweis, der Standardwert für PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="3974f-160">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="3974f-161">Microsoft.PerceptionSimulation.HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="3974f-161">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="3974f-162">Beschreibt einen Head-Tracker-Modus</span><span class="sxs-lookup"><span data-stu-id="3974f-162">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="3974f-163">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span><span class="sxs-lookup"><span data-stu-id="3974f-163">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="3974f-164">Standard-Head nachverfolgen.</span><span class="sxs-lookup"><span data-stu-id="3974f-164">Default Head Tracking.</span></span> <span data-ttu-id="3974f-165">Dies bedeutet, dass das System die beste Head Überwachungsmodus basierend auf laufzeitbedingungen auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="3974f-165">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="3974f-166">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span><span class="sxs-lookup"><span data-stu-id="3974f-166">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="3974f-167">Ausrichtung nur Head nachverfolgen.</span><span class="sxs-lookup"><span data-stu-id="3974f-167">Orientation Only Head Tracking.</span></span> <span data-ttu-id="3974f-168">Dies bedeutet, dass die nachverfolgte Position möglicherweise nicht zuverlässig, und einige Funktionen, die abhängig von Head Position möglicherweise nicht Verfügung zur.</span><span class="sxs-lookup"><span data-stu-id="3974f-168">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="3974f-169">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span><span class="sxs-lookup"><span data-stu-id="3974f-169">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="3974f-170">Mit Feldern fester Breite Head-nachverfolgung.</span><span class="sxs-lookup"><span data-stu-id="3974f-170">Positional Head Tracking.</span></span> <span data-ttu-id="3974f-171">Dies bedeutet, dass die nachverfolgten Head Position und Ausrichtung zuverlässig sind</span><span class="sxs-lookup"><span data-stu-id="3974f-171">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="3974f-172">Microsoft.PerceptionSimulation.SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="3974f-172">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="3974f-173">Beschreibt eine Geste für eine simulierte</span><span class="sxs-lookup"><span data-stu-id="3974f-173">Describes a simulated gesture</span></span>

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

<span data-ttu-id="3974f-174">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span><span class="sxs-lookup"><span data-stu-id="3974f-174">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="3974f-175">Sentinelwert verwendet, um keine Gesten anzugeben.</span><span class="sxs-lookup"><span data-stu-id="3974f-175">A sentinel value used to indicate no gestures</span></span>

<span data-ttu-id="3974f-176">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="3974f-176">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="3974f-177">Ein Finger Geste gedrückt</span><span class="sxs-lookup"><span data-stu-id="3974f-177">A finger pressed gesture</span></span>

<span data-ttu-id="3974f-178">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="3974f-178">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="3974f-179">Eine Geste für ein Finger veröffentlicht</span><span class="sxs-lookup"><span data-stu-id="3974f-179">A finger released gesture</span></span>

<span data-ttu-id="3974f-180">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span><span class="sxs-lookup"><span data-stu-id="3974f-180">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="3974f-181">Die home-Bewegung</span><span class="sxs-lookup"><span data-stu-id="3974f-181">The home gesture</span></span>

<span data-ttu-id="3974f-182">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span><span class="sxs-lookup"><span data-stu-id="3974f-182">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="3974f-183">Die maximale gültige stiftbewegungs</span><span class="sxs-lookup"><span data-stu-id="3974f-183">The maximum valid gesture</span></span>

### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="3974f-184">Microsoft.PerceptionSimulation.PlaybackState</span><span class="sxs-lookup"><span data-stu-id="3974f-184">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="3974f-185">Beschreibt den Status des eine Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="3974f-185">Describes the state of a playback</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="3974f-186">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span><span class="sxs-lookup"><span data-stu-id="3974f-186">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="3974f-187">Die Aufzeichnung wird zurzeit beendet "und" bereit für die Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="3974f-187">The recording is currently stopped and ready for playback</span></span>

<span data-ttu-id="3974f-188">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span><span class="sxs-lookup"><span data-stu-id="3974f-188">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="3974f-189">Die Aufzeichnung wird aktuell wiedergegebenen.</span><span class="sxs-lookup"><span data-stu-id="3974f-189">The recording is currently playing</span></span>

<span data-ttu-id="3974f-190">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span><span class="sxs-lookup"><span data-stu-id="3974f-190">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="3974f-191">Die Aufzeichnung wird angehalten.</span><span class="sxs-lookup"><span data-stu-id="3974f-191">The recording is currently paused</span></span>

<span data-ttu-id="3974f-192">**Microsoft.PerceptionSimulation.PlaybackState.End**</span><span class="sxs-lookup"><span data-stu-id="3974f-192">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="3974f-193">Die Aufzeichnung wurde das Ende erreicht.</span><span class="sxs-lookup"><span data-stu-id="3974f-193">The recording has reached the end</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="3974f-194">Microsoft.PerceptionSimulation.Vector3</span><span class="sxs-lookup"><span data-stu-id="3974f-194">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="3974f-195">Beschreibt einen Vektor 3 Komponenten, der einen Punkt oder einen Vektor im 3D-Raum beschreiben können</span><span class="sxs-lookup"><span data-stu-id="3974f-195">Describes a 3 components vector, which might describe a point or a vector in 3D space</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="3974f-196">**Microsoft.PerceptionSimulation.Vector3.X**</span><span class="sxs-lookup"><span data-stu-id="3974f-196">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="3974f-197">Die X-Komponente des Vektors</span><span class="sxs-lookup"><span data-stu-id="3974f-197">The X component of the vector</span></span>

<span data-ttu-id="3974f-198">**Microsoft.PerceptionSimulation.Vector3.Y**</span><span class="sxs-lookup"><span data-stu-id="3974f-198">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="3974f-199">Die Y-Komponente des Vektors</span><span class="sxs-lookup"><span data-stu-id="3974f-199">The Y component of the vector</span></span>

<span data-ttu-id="3974f-200">**Microsoft.PerceptionSimulation.Vector3.Z**</span><span class="sxs-lookup"><span data-stu-id="3974f-200">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="3974f-201">Die Z-Komponente des Vektors</span><span class="sxs-lookup"><span data-stu-id="3974f-201">The Z component of the vector</span></span>

<span data-ttu-id="3974f-202">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="3974f-202">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="3974f-203">Erstellen Sie eine neue Vector3</span><span class="sxs-lookup"><span data-stu-id="3974f-203">Construct a new Vector3</span></span>

<span data-ttu-id="3974f-204">Parameter</span><span class="sxs-lookup"><span data-stu-id="3974f-204">Parameters</span></span>
* <span data-ttu-id="3974f-205">X: die X-Komponente des Vektors</span><span class="sxs-lookup"><span data-stu-id="3974f-205">x - The x component of the vector</span></span>
* <span data-ttu-id="3974f-206">y - der y-Komponente des Vektors</span><span class="sxs-lookup"><span data-stu-id="3974f-206">y - The y component of the vector</span></span>
* <span data-ttu-id="3974f-207">Z - die Z-Komponente des Vektors</span><span class="sxs-lookup"><span data-stu-id="3974f-207">z - The z component of the vector</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="3974f-208">Microsoft.PerceptionSimulation.Rotation3</span><span class="sxs-lookup"><span data-stu-id="3974f-208">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="3974f-209">Beschreibt eine Drehung um 3 Komponenten</span><span class="sxs-lookup"><span data-stu-id="3974f-209">Describes a 3 components rotation</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="3974f-210">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span><span class="sxs-lookup"><span data-stu-id="3974f-210">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="3974f-211">Die Schriftbreite-Komponente, der die Drehung der x-Achse nach-unten</span><span class="sxs-lookup"><span data-stu-id="3974f-211">The Pitch component of the Rotation, down around the X axis</span></span>

<span data-ttu-id="3974f-212">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span><span class="sxs-lookup"><span data-stu-id="3974f-212">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="3974f-213">Der Yaw-Komponente der Drehung, ganz in der Nähe der y-Achse</span><span class="sxs-lookup"><span data-stu-id="3974f-213">The Yaw component of the Rotation, right around the Y axis</span></span>

<span data-ttu-id="3974f-214">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span><span class="sxs-lookup"><span data-stu-id="3974f-214">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="3974f-215">Die Rollup-Komponente von der Rotation nach rechts um die Z-Achse</span><span class="sxs-lookup"><span data-stu-id="3974f-215">The Roll component of the Rotation, right around the Z axis</span></span>

<span data-ttu-id="3974f-216">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="3974f-216">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="3974f-217">Erstellen Sie eine neue Rotation3</span><span class="sxs-lookup"><span data-stu-id="3974f-217">Construct a new Rotation3</span></span>

<span data-ttu-id="3974f-218">Parameter</span><span class="sxs-lookup"><span data-stu-id="3974f-218">Parameters</span></span>
* <span data-ttu-id="3974f-219">Schriftbreite – die Schriftbreite-Komponente der Drehung</span><span class="sxs-lookup"><span data-stu-id="3974f-219">pitch - The pitch component of the Rotation</span></span>
* <span data-ttu-id="3974f-220">Yaw - der Yaw-Komponente der Drehung</span><span class="sxs-lookup"><span data-stu-id="3974f-220">yaw - The yaw component of the Rotation</span></span>
* <span data-ttu-id="3974f-221">Zurücksetzen Sie – die Rollup-Komponente der Drehung</span><span class="sxs-lookup"><span data-stu-id="3974f-221">roll - The roll component of the Rotation</span></span>

### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="3974f-222">Microsoft.PerceptionSimulation.Frustum</span><span class="sxs-lookup"><span data-stu-id="3974f-222">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="3974f-223">Beschreibt eine Sicht Frustums, in der Regel durch eine Kamera verwendet.</span><span class="sxs-lookup"><span data-stu-id="3974f-223">Describes a view frustum, as typically used by a camera</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="3974f-224">**Microsoft.PerceptionSimulation.Frustum.Near**</span><span class="sxs-lookup"><span data-stu-id="3974f-224">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="3974f-225">Der Mindestabstand, der in der Frustums enthalten ist</span><span class="sxs-lookup"><span data-stu-id="3974f-225">The minimum distance that is contained in the frustum</span></span>

<span data-ttu-id="3974f-226">**Microsoft.PerceptionSimulation.Frustum.Far**</span><span class="sxs-lookup"><span data-stu-id="3974f-226">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="3974f-227">Der maximale Abstand, der in der Frustums enthalten ist</span><span class="sxs-lookup"><span data-stu-id="3974f-227">The maximum distance that is contained in the frustum</span></span>

<span data-ttu-id="3974f-228">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="3974f-228">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="3974f-229">Das horizontale Sichtfeld der Frustums, im Bogenmaß (weniger als PI)</span><span class="sxs-lookup"><span data-stu-id="3974f-229">The horizontal field of view of the frustum, in radians (less than PI)</span></span>

<span data-ttu-id="3974f-230">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="3974f-230">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="3974f-231">Das Verhältnis der horizontale Sichtfeld auf einer vertikale Sichtfeld</span><span class="sxs-lookup"><span data-stu-id="3974f-231">The ratio of horizontal field of view to vertical field of view</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="3974f-232">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="3974f-232">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="3974f-233">Stammverzeichnis für das Generieren von den Paketen, die zum Steuern eines Geräts</span><span class="sxs-lookup"><span data-stu-id="3974f-233">Root for generating the packets used to control a device</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="3974f-234">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span><span class="sxs-lookup"><span data-stu-id="3974f-234">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="3974f-235">Abrufen der simulierten Geräte-Objekt, das die simulierten menschliche und die simulierten Welt interpretiert.</span><span class="sxs-lookup"><span data-stu-id="3974f-235">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="3974f-236">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span><span class="sxs-lookup"><span data-stu-id="3974f-236">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="3974f-237">Rufen Sie das Objekt, das die simulierte menschliche steuert.</span><span class="sxs-lookup"><span data-stu-id="3974f-237">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="3974f-238">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span><span class="sxs-lookup"><span data-stu-id="3974f-238">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="3974f-239">Die Simulation zurückgesetzt auf ihren Standardzustand.</span><span class="sxs-lookup"><span data-stu-id="3974f-239">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="3974f-240">Microsoft.PerceptionSimulation.ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="3974f-240">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="3974f-241">Schnittstelle, die das Gerät, das in der simulierten Welt und die simulierten menschliche interpretiert beschreibt.</span><span class="sxs-lookup"><span data-stu-id="3974f-241">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="3974f-242">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="3974f-242">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="3974f-243">Abrufen der Head-nachverfolgung vom simulierten Gerät an.</span><span class="sxs-lookup"><span data-stu-id="3974f-243">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="3974f-244">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span><span class="sxs-lookup"><span data-stu-id="3974f-244">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="3974f-245">Rufen Sie die nachverfolgung manuell vom simulierten Gerät an.</span><span class="sxs-lookup"><span data-stu-id="3974f-245">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="3974f-246">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="3974f-246">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="3974f-247">Legen Sie die Eigenschaften des simulierten Geräts entsprechend den angegebenen Gerätetyp.</span><span class="sxs-lookup"><span data-stu-id="3974f-247">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="3974f-248">Parameter</span><span class="sxs-lookup"><span data-stu-id="3974f-248">Parameters</span></span>
* <span data-ttu-id="3974f-249">Type - der neuen Typs des simulierten Geräts</span><span class="sxs-lookup"><span data-stu-id="3974f-249">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="3974f-250">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="3974f-250">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="3974f-251">Schnittstelle, die den Teil des simulierten Geräts, das den Anfang der simulierten Benutzer nachverfolgt beschreibt.</span><span class="sxs-lookup"><span data-stu-id="3974f-251">Interface describing the portion of the simulated device that tracks the head of the simulated human</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="3974f-252">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="3974f-252">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="3974f-253">Ruft ab, und setzt den aktuellen Modus des Head-Tracker.</span><span class="sxs-lookup"><span data-stu-id="3974f-253">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="3974f-254">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="3974f-254">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="3974f-255">Schnittstelle, die den Teil des simulierten Geräts, das die Hände von den simulierten Benutzer nachverfolgt beschreibt.</span><span class="sxs-lookup"><span data-stu-id="3974f-255">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="3974f-256">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="3974f-256">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="3974f-257">Die Position des Knotens in Bezug auf der ganzen Welt in Metern abzurufen</span><span class="sxs-lookup"><span data-stu-id="3974f-257">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="3974f-258">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span><span class="sxs-lookup"><span data-stu-id="3974f-258">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="3974f-259">Abrufen und die Position der simulierten Hand Tracker Bezug auf den Mittelpunkt des Anfangswerts festlegen.</span><span class="sxs-lookup"><span data-stu-id="3974f-259">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="3974f-260">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span><span class="sxs-lookup"><span data-stu-id="3974f-260">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="3974f-261">Abzurufen Sie und festzulegen Sie, die nach unten weisenden Tonhöhe der simulierten Hand-nachverfolgung</span><span class="sxs-lookup"><span data-stu-id="3974f-261">Retrieve and set the downward pitch of the simulated hand tracker</span></span>

<span data-ttu-id="3974f-262">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="3974f-262">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="3974f-263">Rufen Sie ab und festlegen Sie, ob die Frustums simulierten Hand Tracker ignoriert wird.</span><span class="sxs-lookup"><span data-stu-id="3974f-263">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="3974f-264">Wenn ignoriert, sind die beiden Händen immer sichtbar.</span><span class="sxs-lookup"><span data-stu-id="3974f-264">When ignored, both hands are always visible.</span></span> <span data-ttu-id="3974f-265">Wenn (Standard) nicht ignoriert sind praktische nur sichtbar, wenn sie innerhalb der Frustums Hand Tracker sind.</span><span class="sxs-lookup"><span data-stu-id="3974f-265">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="3974f-266">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span><span class="sxs-lookup"><span data-stu-id="3974f-266">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="3974f-267">Abrufen und Festlegen der Frustums Eigenschaften verwendet, um zu bestimmen, ob die Hände für die nachverfolgung von simulierten Hand sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="3974f-267">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="3974f-268">Microsoft.PerceptionSimulation.ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="3974f-268">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="3974f-269">Top Level-Schnittstelle zum Steuern von den simulierten Benutzer</span><span class="sxs-lookup"><span data-stu-id="3974f-269">Top level interface for controlling the simulated human</span></span>

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

<span data-ttu-id="3974f-270">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="3974f-270">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="3974f-271">Abzurufen Sie, und legen Sie die Position des Knotens Bezug auf der ganzen Welt, in Meter.</span><span class="sxs-lookup"><span data-stu-id="3974f-271">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="3974f-272">Die Position entspricht einem Punkt in der Mitte der Mensch Zentimetern Abweichung.</span><span class="sxs-lookup"><span data-stu-id="3974f-272">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="3974f-273">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span><span class="sxs-lookup"><span data-stu-id="3974f-273">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="3974f-274">Abrufen und Festlegen der Richtung der simulierten menschliche Gesichter in der ganzen Welt.</span><span class="sxs-lookup"><span data-stu-id="3974f-274">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="3974f-275">0 Bogenmaß Gesichtern nach unten der negativen Z-Achse.</span><span class="sxs-lookup"><span data-stu-id="3974f-275">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="3974f-276">Positive Bogenmaß Drehen im Uhrzeigersinn die y-Achse.</span><span class="sxs-lookup"><span data-stu-id="3974f-276">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="3974f-277">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span><span class="sxs-lookup"><span data-stu-id="3974f-277">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="3974f-278">Abrufen und Festlegen der Höhe der simulierten vom Menschen in Metern</span><span class="sxs-lookup"><span data-stu-id="3974f-278">Retrieve and set the height of the simulated human, in meters</span></span>

<span data-ttu-id="3974f-279">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span><span class="sxs-lookup"><span data-stu-id="3974f-279">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="3974f-280">Links von den simulierten Benutzer abrufen</span><span class="sxs-lookup"><span data-stu-id="3974f-280">Retrieve the left hand of the simulated human</span></span>

<span data-ttu-id="3974f-281">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span><span class="sxs-lookup"><span data-stu-id="3974f-281">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="3974f-282">Die rechte Seite von den simulierten Benutzer abrufen</span><span class="sxs-lookup"><span data-stu-id="3974f-282">Retrieve the right hand of the simulated human</span></span>

<span data-ttu-id="3974f-283">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span><span class="sxs-lookup"><span data-stu-id="3974f-283">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="3974f-284">Der Anfang der simulierten Benutzer abrufen</span><span class="sxs-lookup"><span data-stu-id="3974f-284">Retrieve the head of the simulated human</span></span>

<span data-ttu-id="3974f-285">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="3974f-285">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="3974f-286">Verschieben Sie die simulierte menschliche Bezug auf seine aktuelle Position in Metern</span><span class="sxs-lookup"><span data-stu-id="3974f-286">Move the simulated human relative to its current position, in meters</span></span>

<span data-ttu-id="3974f-287">Parameter</span><span class="sxs-lookup"><span data-stu-id="3974f-287">Parameters</span></span>
* <span data-ttu-id="3974f-288">Translation – Übersetzung, relativ zur aktuellen Position verschieben</span><span class="sxs-lookup"><span data-stu-id="3974f-288">translation - The translation to move, relative to current position</span></span>

<span data-ttu-id="3974f-289">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span><span class="sxs-lookup"><span data-stu-id="3974f-289">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="3974f-290">Drehen Sie die simulierte menschliche relativ zum aktuellen Richtung, die y-Achse im Uhrzeigersinn</span><span class="sxs-lookup"><span data-stu-id="3974f-290">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="3974f-291">Parameter</span><span class="sxs-lookup"><span data-stu-id="3974f-291">Parameters</span></span>
* <span data-ttu-id="3974f-292">Bogenmaß (Radiant) – der Betrag, um die y-Achse drehen</span><span class="sxs-lookup"><span data-stu-id="3974f-292">radians - The amount to rotate around the Y axis</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="3974f-293">Microsoft.PerceptionSimulation.ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="3974f-293">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="3974f-294">Schnittstelle, die eine Hand von den simulierten Benutzer beschreibt.</span><span class="sxs-lookup"><span data-stu-id="3974f-294">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="3974f-295">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="3974f-295">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="3974f-296">Die Position des Knotens in Bezug auf der ganzen Welt in Metern abzurufen</span><span class="sxs-lookup"><span data-stu-id="3974f-296">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="3974f-297">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span><span class="sxs-lookup"><span data-stu-id="3974f-297">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="3974f-298">Abrufen und Festlegen der Position eines simulierten relativ zu der vom Menschen in Meter.</span><span class="sxs-lookup"><span data-stu-id="3974f-298">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="3974f-299">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span><span class="sxs-lookup"><span data-stu-id="3974f-299">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="3974f-300">Rufen Sie ab und festlegen Sie, ob das Handsymbol derzeit aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="3974f-300">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="3974f-301">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span><span class="sxs-lookup"><span data-stu-id="3974f-301">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="3974f-302">Rufen Sie, ob das Handsymbol derzeit sichtbar ist, um die SimulatedDevice ist (z. B. ob er in der Lage, die von der HandTracker erkannt werden ist).</span><span class="sxs-lookup"><span data-stu-id="3974f-302">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="3974f-303">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="3974f-303">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="3974f-304">Verschieben Sie die Hand, dass es für die SimulatedDevice sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="3974f-304">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="3974f-305">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="3974f-305">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="3974f-306">Verschieben Sie die Position eines simulierten Bezug auf seine aktuelle Position in Meter.</span><span class="sxs-lookup"><span data-stu-id="3974f-306">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="3974f-307">Parameter</span><span class="sxs-lookup"><span data-stu-id="3974f-307">Parameters</span></span>
* <span data-ttu-id="3974f-308">Übersetzung – der Betrag, um das simulierte Handsymbol übersetzen</span><span class="sxs-lookup"><span data-stu-id="3974f-308">translation - The amount to translate the simulated hand</span></span>

<span data-ttu-id="3974f-309">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="3974f-309">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="3974f-310">Führen Sie eine Geste für eine mithilfe der simulierten Hand (es wird nur vom System erkannt werden, wenn die Seite aktiviert ist).</span><span class="sxs-lookup"><span data-stu-id="3974f-310">Perform a gesture using the simulated hand (it will only be detected by the system if the hand is enabled).</span></span>

<span data-ttu-id="3974f-311">Parameter</span><span class="sxs-lookup"><span data-stu-id="3974f-311">Parameters</span></span>
* <span data-ttu-id="3974f-312">Aktion - die Aktion ausführen</span><span class="sxs-lookup"><span data-stu-id="3974f-312">gesture - The gesture to perform</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="3974f-313">Microsoft.PerceptionSimulation.ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="3974f-313">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="3974f-314">Schnittstelle, die den Anfang der simulierten Menschen beschreibt.</span><span class="sxs-lookup"><span data-stu-id="3974f-314">Interface describing the head of the simulated human</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="3974f-315">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="3974f-315">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="3974f-316">Die Position des Knotens in Bezug auf der ganzen Welt in Metern abzurufen</span><span class="sxs-lookup"><span data-stu-id="3974f-316">Retrieve the position of the node with relation to the world, in meters</span></span>

<span data-ttu-id="3974f-317">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span><span class="sxs-lookup"><span data-stu-id="3974f-317">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="3974f-318">Rufen Sie die Rotation der simulierten Head.</span><span class="sxs-lookup"><span data-stu-id="3974f-318">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="3974f-319">Positive Bogenmaß (Radiant) werden bei der Suche auf der Achse im Uhrzeigersinn drehen.</span><span class="sxs-lookup"><span data-stu-id="3974f-319">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="3974f-320">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span><span class="sxs-lookup"><span data-stu-id="3974f-320">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="3974f-321">Abrufen des simulierten Anfangselements Durchmesser.</span><span class="sxs-lookup"><span data-stu-id="3974f-321">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="3974f-322">Dieser Wert wird verwendet, um zu bestimmen, des Anfangselements Center (Punkt der Drehung).</span><span class="sxs-lookup"><span data-stu-id="3974f-322">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="3974f-323">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="3974f-323">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="3974f-324">Drehen Sie die simulierte Head relativ zu dessen aktuellen Rotationsachse.</span><span class="sxs-lookup"><span data-stu-id="3974f-324">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="3974f-325">Positive Bogenmaß (Radiant) werden bei der Suche auf der Achse im Uhrzeigersinn drehen.</span><span class="sxs-lookup"><span data-stu-id="3974f-325">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="3974f-326">Parameter</span><span class="sxs-lookup"><span data-stu-id="3974f-326">Parameters</span></span>
* <span data-ttu-id="3974f-327">Rotation – der Betrag, um drehen</span><span class="sxs-lookup"><span data-stu-id="3974f-327">rotation - The amount to rotate</span></span>

### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="3974f-328">Microsoft.PerceptionSimulation.ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="3974f-328">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="3974f-329">Eine Schnittstelle für die Interaktion mit einem einzelnen geladen, für die Wiedergabe aufzeichnen.</span><span class="sxs-lookup"><span data-stu-id="3974f-329">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="3974f-330">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span><span class="sxs-lookup"><span data-stu-id="3974f-330">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="3974f-331">Ruft eine Liste der Datentypen in die Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="3974f-331">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="3974f-332">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span><span class="sxs-lookup"><span data-stu-id="3974f-332">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="3974f-333">Ruft den aktuellen Status der Aufzeichnung ab.</span><span class="sxs-lookup"><span data-stu-id="3974f-333">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="3974f-334">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span><span class="sxs-lookup"><span data-stu-id="3974f-334">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="3974f-335">Die Wiedergabe zu starten.</span><span class="sxs-lookup"><span data-stu-id="3974f-335">Start the playback.</span></span> <span data-ttu-id="3974f-336">Wenn die Aufzeichnung angehalten wird, wird die Wiedergabe aus dem angehaltenen Speicherort fortgesetzt; Wenn beendet, wird die Wiedergabe am Anfang beginnen.</span><span class="sxs-lookup"><span data-stu-id="3974f-336">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="3974f-337">Wenn bereits abgespielt wird, wird dieser Aufruf ignoriert.</span><span class="sxs-lookup"><span data-stu-id="3974f-337">If already playing, this call is ignored.</span></span>

<span data-ttu-id="3974f-338">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span><span class="sxs-lookup"><span data-stu-id="3974f-338">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="3974f-339">Hält die Wiedergabe an dessen aktuellen Speicherort an.</span><span class="sxs-lookup"><span data-stu-id="3974f-339">Pauses the playback at its current location.</span></span> <span data-ttu-id="3974f-340">Wenn die Aufzeichnung beendet wird, wird der Aufruf ignoriert.</span><span class="sxs-lookup"><span data-stu-id="3974f-340">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="3974f-341">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span><span class="sxs-lookup"><span data-stu-id="3974f-341">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="3974f-342">Suchen die Aufzeichnung auf die angegebene Zeit (in 100-Nanosekunden-Intervallen ab) und an dieser Position angehalten wird.</span><span class="sxs-lookup"><span data-stu-id="3974f-342">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="3974f-343">Wenn die Zeit nach dem Ende der Aufzeichnung ist, wird es im letzten Frame angehalten.</span><span class="sxs-lookup"><span data-stu-id="3974f-343">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="3974f-344">Parameter</span><span class="sxs-lookup"><span data-stu-id="3974f-344">Parameters</span></span>
* <span data-ttu-id="3974f-345">Ticks – die Uhrzeit für die Suche</span><span class="sxs-lookup"><span data-stu-id="3974f-345">ticks - The time to which to seek</span></span>

<span data-ttu-id="3974f-346">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span><span class="sxs-lookup"><span data-stu-id="3974f-346">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="3974f-347">Die Wiedergabe beendet und setzt die Position zum Anfang</span><span class="sxs-lookup"><span data-stu-id="3974f-347">Stops the playback and resets the position to the beginning</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="3974f-348">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="3974f-348">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="3974f-349">Schnittstelle für den Empfang von Änderungen des Ansichtszustands während der Wiedergabe</span><span class="sxs-lookup"><span data-stu-id="3974f-349">Interface for receiving state changes during playback</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="3974f-350">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="3974f-350">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="3974f-351">Wird aufgerufen, wenn ein ISimulationRecordings Wiedergabe-Zustand geändert hat</span><span class="sxs-lookup"><span data-stu-id="3974f-351">Called when an ISimulationRecording's playback state has changed</span></span>

<span data-ttu-id="3974f-352">Parameter</span><span class="sxs-lookup"><span data-stu-id="3974f-352">Parameters</span></span>
* <span data-ttu-id="3974f-353">NewState – der neue Status der Aufzeichnung</span><span class="sxs-lookup"><span data-stu-id="3974f-353">newState - The new state of the recording</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="3974f-354">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="3974f-354">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="3974f-355">Stammobjekt für das Erstellen von Objekten der Wahrnehmung Simulation</span><span class="sxs-lookup"><span data-stu-id="3974f-355">Root object for creating Perception Simulation objects</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="3974f-356">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="3974f-356">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="3974f-357">Erstellen Sie auf das Objekt zum Generieren von simulierten Pakete und an die angegebene Senke bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="3974f-357">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="3974f-358">Parameter</span><span class="sxs-lookup"><span data-stu-id="3974f-358">Parameters</span></span>
* <span data-ttu-id="3974f-359">Sink - Senke, die alle generierten Pakete erhalten</span><span class="sxs-lookup"><span data-stu-id="3974f-359">sink - The sink that will receive all generated packets</span></span>

<span data-ttu-id="3974f-360">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="3974f-360">Return value</span></span>

<span data-ttu-id="3974f-361">Der erstellte-Manager</span><span class="sxs-lookup"><span data-stu-id="3974f-361">The created Manager</span></span>

<span data-ttu-id="3974f-362">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span><span class="sxs-lookup"><span data-stu-id="3974f-362">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="3974f-363">Erstellen Sie eine Senke, die alle empfangenen Pakete in einer Datei unter dem angegebenen Pfad gespeichert.</span><span class="sxs-lookup"><span data-stu-id="3974f-363">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="3974f-364">Parameter</span><span class="sxs-lookup"><span data-stu-id="3974f-364">Parameters</span></span>
* <span data-ttu-id="3974f-365">Pfad – der Pfad des zu erstellenden Datei</span><span class="sxs-lookup"><span data-stu-id="3974f-365">path - The path of the file to create</span></span>

<span data-ttu-id="3974f-366">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="3974f-366">Return value</span></span>

<span data-ttu-id="3974f-367">Die erstellte Senke</span><span class="sxs-lookup"><span data-stu-id="3974f-367">The created sink</span></span>

<span data-ttu-id="3974f-368">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="3974f-368">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="3974f-369">Laden Sie eine Aufzeichnung aus der angegebenen Datei</span><span class="sxs-lookup"><span data-stu-id="3974f-369">Load a recording from the specified file</span></span>

<span data-ttu-id="3974f-370">Parameter</span><span class="sxs-lookup"><span data-stu-id="3974f-370">Parameters</span></span>
* <span data-ttu-id="3974f-371">Pfad – der Pfad der zu ladenden Datei</span><span class="sxs-lookup"><span data-stu-id="3974f-371">path - The path of the file to load</span></span>
* <span data-ttu-id="3974f-372">Factory – eine Factory, die zum Erstellen einer ISimulationStreamSink bei Bedarf durch die Aufzeichnung verwendet</span><span class="sxs-lookup"><span data-stu-id="3974f-372">factory - A factory used by the recording for creating an ISimulationStreamSink when required</span></span>

<span data-ttu-id="3974f-373">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="3974f-373">Return value</span></span>

<span data-ttu-id="3974f-374">Die Aufzeichnung geladen</span><span class="sxs-lookup"><span data-stu-id="3974f-374">The loaded recording</span></span>

<span data-ttu-id="3974f-375">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory, Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="3974f-375">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="3974f-376">Laden Sie eine Aufzeichnung aus der angegebenen Datei</span><span class="sxs-lookup"><span data-stu-id="3974f-376">Load a recording from the specified file</span></span>

<span data-ttu-id="3974f-377">Parameter</span><span class="sxs-lookup"><span data-stu-id="3974f-377">Parameters</span></span>
* <span data-ttu-id="3974f-378">Pfad – der Pfad der zu ladenden Datei</span><span class="sxs-lookup"><span data-stu-id="3974f-378">path - The path of the file to load</span></span>
* <span data-ttu-id="3974f-379">Factory – eine Factory, die zum Erstellen einer ISimulationStreamSink bei Bedarf durch die Aufzeichnung verwendet</span><span class="sxs-lookup"><span data-stu-id="3974f-379">factory - A factory used by the recording for creating an ISimulationStreamSink when required</span></span>
* <span data-ttu-id="3974f-380">Rückruf - aktualisiert ein Rückruf an, empfängt die Aufzeichnung des Status Umpacken</span><span class="sxs-lookup"><span data-stu-id="3974f-380">callback - A callback which receives updates regrading the recording's status</span></span>

<span data-ttu-id="3974f-381">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="3974f-381">Return value</span></span>

<span data-ttu-id="3974f-382">Die Aufzeichnung geladen</span><span class="sxs-lookup"><span data-stu-id="3974f-382">The loaded recording</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="3974f-383">Microsoft.PerceptionSimulation.StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="3974f-383">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="3974f-384">Beschreibt die verschiedenen Typen von Streamdaten</span><span class="sxs-lookup"><span data-stu-id="3974f-384">Describes the different types of stream data</span></span>

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

<span data-ttu-id="3974f-385">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span><span class="sxs-lookup"><span data-stu-id="3974f-385">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="3974f-386">Sentinelwert verwendet, um keine Datentypen Stream anzugeben.</span><span class="sxs-lookup"><span data-stu-id="3974f-386">A sentinel value used to indicate no stream data types</span></span>

<span data-ttu-id="3974f-387">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span><span class="sxs-lookup"><span data-stu-id="3974f-387">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="3974f-388">Stream der Daten in Bezug auf die Position und Ausrichtung des Anfangswerts</span><span class="sxs-lookup"><span data-stu-id="3974f-388">Stream of data regarding the position and orientation of the head</span></span>

<span data-ttu-id="3974f-389">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span><span class="sxs-lookup"><span data-stu-id="3974f-389">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="3974f-390">Stream der Daten in Bezug auf die Position und Gesten Händen</span><span class="sxs-lookup"><span data-stu-id="3974f-390">Stream of data regarding the position and gestures of hands</span></span>

<span data-ttu-id="3974f-391">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="3974f-391">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="3974f-392">Stream der Daten in Bezug auf räumliche Zuordnung der Umgebung</span><span class="sxs-lookup"><span data-stu-id="3974f-392">Stream of data regarding spatial mapping of the environment</span></span>

<span data-ttu-id="3974f-393">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span><span class="sxs-lookup"><span data-stu-id="3974f-393">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="3974f-394">Der Stream der Daten in Bezug auf die Kalibrierung des Geräts.</span><span class="sxs-lookup"><span data-stu-id="3974f-394">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="3974f-395">Kalibrierung Pakete werden nur von einem System im Remotemodus angenommen.</span><span class="sxs-lookup"><span data-stu-id="3974f-395">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="3974f-396">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span><span class="sxs-lookup"><span data-stu-id="3974f-396">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="3974f-397">Stream der Daten in Bezug auf die Umgebung des Geräts</span><span class="sxs-lookup"><span data-stu-id="3974f-397">Stream of data regarding the environment of the device</span></span>

<span data-ttu-id="3974f-398">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span><span class="sxs-lookup"><span data-stu-id="3974f-398">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="3974f-399">Sentinelwert verwendet, um alle aufgezeichneten Datentypen anzugeben.</span><span class="sxs-lookup"><span data-stu-id="3974f-399">A sentinel value used to indicate all recorded data types</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="3974f-400">Microsoft.PerceptionSimulation.ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="3974f-400">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="3974f-401">Ein Objekt, das Datenpakete aus einem Stream Simulation empfängt.</span><span class="sxs-lookup"><span data-stu-id="3974f-401">An object that receives data packets from a simulation stream</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="3974f-402">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived (Uint-Länge, Byte []-Paket)**</span><span class="sxs-lookup"><span data-stu-id="3974f-402">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="3974f-403">Empfängt ein einzelnes Paket, das intern typisierten und mit Versionsangabe versehen ist</span><span class="sxs-lookup"><span data-stu-id="3974f-403">Receives a single packet, which is internally typed and versioned</span></span>

<span data-ttu-id="3974f-404">Parameter</span><span class="sxs-lookup"><span data-stu-id="3974f-404">Parameters</span></span>
* <span data-ttu-id="3974f-405">Länge - die Länge des Pakets</span><span class="sxs-lookup"><span data-stu-id="3974f-405">length - The length of the packet</span></span>
* <span data-ttu-id="3974f-406">Paket - die Daten des Pakets</span><span class="sxs-lookup"><span data-stu-id="3974f-406">packet - The data of the packet</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="3974f-407">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="3974f-407">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="3974f-408">Ein Objekt, das ISimulationStreamSink erstellt.</span><span class="sxs-lookup"><span data-stu-id="3974f-408">An object that creates ISimulationStreamSink</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="3974f-409">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span><span class="sxs-lookup"><span data-stu-id="3974f-409">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="3974f-410">Erstellt eine einzelne Instanz der ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="3974f-410">Creates a single instance of ISimulationStreamSink</span></span>

<span data-ttu-id="3974f-411">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="3974f-411">Return value</span></span>

<span data-ttu-id="3974f-412">Die erstellte Senke</span><span class="sxs-lookup"><span data-stu-id="3974f-412">The created sink</span></span>
