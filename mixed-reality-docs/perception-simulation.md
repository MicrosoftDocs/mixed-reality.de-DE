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
# <a name="perception-simulation"></a><span data-ttu-id="5dc47-104">Perception simulation</span><span class="sxs-lookup"><span data-stu-id="5dc47-104">Perception simulation</span></span>

<span data-ttu-id="5dc47-105">Möchten Sie die Erstellung ein automatisiertes Tests für Ihre app?</span><span class="sxs-lookup"><span data-stu-id="5dc47-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="5dc47-106">Möchten Sie Ihre Tests auf Komponentenebene Komponententests hinausgehen und führen Sie Ihre app End-to-End wirklich?</span><span class="sxs-lookup"><span data-stu-id="5dc47-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="5dc47-107">Perception Simulation ist, wonach Sie suchen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="5dc47-108">Die Wahrnehmung Simulation-Bibliothek sendet menschlichen Welt Eingabe Daten für Ihre app aus, damit Sie Ihre Tests zu automatisieren.</span><span class="sxs-lookup"><span data-stu-id="5dc47-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="5dc47-109">Beispielsweise können Sie die Eingabe eines menschlichen an eine bestimmte, wiederholbaren Position gesucht und anschließend ausführen, die eine Geste oder mithilfe eines Controllers während der Übertragung simulieren.</span><span class="sxs-lookup"><span data-stu-id="5dc47-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="5dc47-110">Perception Simulation simulierten Eingabe wie folgt an einen physischen HoloLens, den Emulator für HoloLens senden kann (1. Generation), die HoloLens 2 Emulator oder einem PC mit Mixed Reality-Portal installiert.</span><span class="sxs-lookup"><span data-stu-id="5dc47-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="5dc47-111">Perception Simulation umgeht die live Sensoren auf einem Gerät Mixed Reality und sendet simulierte Eingabe für Anwendungen, die auf dem Gerät ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="5dc47-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="5dc47-112">Anwendungen erhalten diese Eingabeereignisse über die gleichen APIs, die sie immer verwenden, und den Unterschied zwischen der Ausführung mit echten Sensoren im Vergleich zu der Wahrnehmung-Simulation mit nicht erkennen kann.</span><span class="sxs-lookup"><span data-stu-id="5dc47-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="5dc47-113">Perception Simulation ist die gleiche Technologie ein, die HoloLens-Emulatoren für simulierte Eingaben, die HoloLens-VM zu senden.</span><span class="sxs-lookup"><span data-stu-id="5dc47-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="5dc47-114">Um zu beginnen, Simulation im Code verwenden, erstellen Sie zunächst ein IPerceptionSimulationManager-Objekt.</span><span class="sxs-lookup"><span data-stu-id="5dc47-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="5dc47-115">Aus diesem Objekt Sie können Befehle, die Eigenschaften einer simulierten "Menschen", wie z.B. Head Position Hand Position und Bewegungen zu steuern und können Sie aktivieren, und Bearbeiten von Motion-Controller.</span><span class="sxs-lookup"><span data-stu-id="5dc47-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="5dc47-116">Einrichten von Visual Studio-Projekt für die Wahrnehmung Simulation</span><span class="sxs-lookup"><span data-stu-id="5dc47-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="5dc47-117">[Installieren Sie den Emulator für HoloLens](install-the-tools.md) auf Ihrem Entwicklungs-PC.</span><span class="sxs-lookup"><span data-stu-id="5dc47-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="5dc47-118">Der Emulator enthält die Bibliotheken, die Sie für die Wahrnehmung Simulation verwenden.</span><span class="sxs-lookup"><span data-stu-id="5dc47-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="5dc47-119">Erstellen Sie eine neue Visual Studio C# Desktopprojekt (ein Konsolenprojekt funktioniert hervorragend für den Einstieg).</span><span class="sxs-lookup"><span data-stu-id="5dc47-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="5dc47-120">Die folgenden Binärdateien dem Projekt als Verweise hinzufügen (Projekt -> Hinzufügen -> Verweis...). Sie finden diese in % ProgramFiles% (x86) %\Microsoft XDE\\(Version), wie z. B. **% ProgramFiles% (x86) %\Microsoft XDE\\10.0.18362.0** für den 2-Emulator für HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5dc47-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="5dc47-121">(Hinweis: Obwohl die Binärdateien der 2-Emulator für HoloLens angehören, zusätzlich arbeiten für die Windows Mixed Reality auf dem Desktop.) ein.</span><span class="sxs-lookup"><span data-stu-id="5dc47-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="5dc47-122">PerceptionSimulationManager.Interop.dll - verwalteten C# Wrapper für die Wahrnehmung Simulation.</span><span class="sxs-lookup"><span data-stu-id="5dc47-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="5dc47-123">b.</span><span class="sxs-lookup"><span data-stu-id="5dc47-123">b.</span></span> <span data-ttu-id="5dc47-124">PerceptionSimulationRest.dll - Bibliothek für das Einrichten eines Web-Socket-Kommunikationskanals für das HoloLens oder den Emulator.</span><span class="sxs-lookup"><span data-stu-id="5dc47-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="5dc47-125">c.</span><span class="sxs-lookup"><span data-stu-id="5dc47-125">c.</span></span> <span data-ttu-id="5dc47-126">SimulationStream.Interop.dll - freigegebenen Typen für die Simulation.</span><span class="sxs-lookup"><span data-stu-id="5dc47-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="5dc47-127">Fügen Sie die Implementierung binäre PerceptionSimulationManager.dll zu Ihrem Projekt ein.</span><span class="sxs-lookup"><span data-stu-id="5dc47-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="5dc47-128">Zunächst als Binärdatei zum Projekt hinzufügen (Projekt -> Hinzufügen -> Vorhandenes Element...). Speichern Sie es als einen Link, damit sie es in Ihrem Projektordner für die Quelle nicht kopiert.</span><span class="sxs-lookup"><span data-stu-id="5dc47-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="5dc47-129">![Fügen Sie dem Projekt als Link PerceptionSimulationManager.dll](images/saveaslink.png) b.</span><span class="sxs-lookup"><span data-stu-id="5dc47-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="5dc47-130">Stellen Sie sicher, dass es erhalten der in Ihrem Ordner "Output" für Build kopiert.</span><span class="sxs-lookup"><span data-stu-id="5dc47-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="5dc47-131">Dies ist im Eigenschaftenblatt für die Binärdatei.</span><span class="sxs-lookup"><span data-stu-id="5dc47-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="5dc47-132">![Mark PerceptionSimulationManager.dll in das Ausgabeverzeichnis kopieren](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="5dc47-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="5dc47-133">Legen Sie Ihre Aktive Projektmappenplattform auf X64 an.</span><span class="sxs-lookup"><span data-stu-id="5dc47-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="5dc47-134">(Verwenden Sie die Configuration Manager einen Plattform-Eintrag für X64 zu erstellen, wenn nicht bereits vorhanden ist.)</span><span class="sxs-lookup"><span data-stu-id="5dc47-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="5dc47-135">Erstellen eines IPerceptionSimulation-Manager-Objekts</span><span class="sxs-lookup"><span data-stu-id="5dc47-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="5dc47-136">Um die Simulation zu steuern, müssen Sie Updates auf Objekte, die von einem Objekt IPerceptionSimulationManager abgerufen ausgeben.</span><span class="sxs-lookup"><span data-stu-id="5dc47-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="5dc47-137">Der erste Schritt ist dieses Objekt abgerufen, und verbinden Sie es auf Ihrem Gerät oder Emulator.</span><span class="sxs-lookup"><span data-stu-id="5dc47-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="5dc47-138">Sie können die IP-Adresse Ihrem Emulator abrufen, indem Sie durch Klicken auf die Schaltfläche "Device Portal" in der [Symbolleiste](using-the-hololens-emulator.md)</span><span class="sxs-lookup"><span data-stu-id="5dc47-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="5dc47-139">![Symbol "Device Portal öffnen"](images/emulator-deviceportal.png) **öffnen Device Portal**: Öffnen Sie das Windows-Geräteportal für das HoloLens-Betriebssystem im Emulator.</span><span class="sxs-lookup"><span data-stu-id="5dc47-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="5dc47-140">Für Windows Mixed Reality, dies kann abgerufen werden in der Einstellungs-app unter "Update und Sicherheit" aus, und klicken Sie dann "für Entwickler" in der "Herstellen einer Verbindung mit:" im Abschnitt unter "Enable Device Portal."</span><span class="sxs-lookup"><span data-stu-id="5dc47-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="5dc47-141">Achten Sie darauf, dass Sie den IP-Adresse und die Portnummer zu beachten.</span><span class="sxs-lookup"><span data-stu-id="5dc47-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="5dc47-142">Zunächst rufen Sie RestSimulationStreamSink.Create zum Abrufen einer RestSimulationStreamSink-Objekts.</span><span class="sxs-lookup"><span data-stu-id="5dc47-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="5dc47-143">Dies ist das Zielgerät oder den Emulator, mit denen Sie über eine http-Verbindung gesteuert werden.</span><span class="sxs-lookup"><span data-stu-id="5dc47-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="5dc47-144">Die Befehle übergeben und von behandelt werden die [Windows Device Portal](using-the-windows-device-portal.md) auf dem Gerät oder Emulator ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="5dc47-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="5dc47-145">Die vier Parameter, die Sie ein Objekt erstellt müssen werden:</span><span class="sxs-lookup"><span data-stu-id="5dc47-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="5dc47-146">URI-Uri - IP-Adresse des Zielgeräts (z. B. "http://123.123.123.123"oder"http://123.123.123.123:50080")</span><span class="sxs-lookup"><span data-stu-id="5dc47-146">Uri uri - IP address of the target device (e.g., "http://123.123.123.123" or "http://123.123.123.123:50080")</span></span>
* <span data-ttu-id="5dc47-147">System.Net.NetworkCredential Anmeldeinformationen – Benutzername und Kennwort für die Verbindung mit der [Windows Device Portal](using-the-windows-device-portal.md) auf dem Gerät oder Emulator.</span><span class="sxs-lookup"><span data-stu-id="5dc47-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="5dc47-148">Wenn Sie die Verbindung mit dem Emulator über die lokale Adresse herstellen (z. B. 168. *.* . \*) auf demselben PC, werden alle Anmeldeinformationen akzeptiert werden.</span><span class="sxs-lookup"><span data-stu-id="5dc47-148">If you are connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="5dc47-149">normal: "bool" (normale Priorität), "false" für mit niedriger Priorität "true".</span><span class="sxs-lookup"><span data-stu-id="5dc47-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="5dc47-150">Sie möchten in der Regel diese Einstellung auf *"true"* für Testszenarien, in dem den Test die Steuerung übernehmen können.</span><span class="sxs-lookup"><span data-stu-id="5dc47-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="5dc47-151">Verwenden den Emulator als auch Windows Mixed Reality-Simulation Verbindungen mit niedriger Priorität.</span><span class="sxs-lookup"><span data-stu-id="5dc47-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="5dc47-152">Wenn der Test auch eine Verbindung mit niedriger Priorität verwendet wird, eingerichtet am häufigsten vor kurzem, dass die Verbindung im Steuerelement werden kann.</span><span class="sxs-lookup"><span data-stu-id="5dc47-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="5dc47-153">"System.Threading.CancellationToken" Token - Token zum Abbrechen des asynchronen Vorgangs.</span><span class="sxs-lookup"><span data-stu-id="5dc47-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="5dc47-154">Erstellen Sie zweitens die IPerceptionSimulationManager.</span><span class="sxs-lookup"><span data-stu-id="5dc47-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="5dc47-155">Dies ist das Objekt, das Sie verwenden, um die Simulation zu steuern.</span><span class="sxs-lookup"><span data-stu-id="5dc47-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="5dc47-156">Beachten Sie, dass dies auch in einer asynchronen Methode durchgeführt werden muss.</span><span class="sxs-lookup"><span data-stu-id="5dc47-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="5dc47-157">Steuern Sie die simulierte menschliche</span><span class="sxs-lookup"><span data-stu-id="5dc47-157">Control the simulated Human</span></span>

<span data-ttu-id="5dc47-158">Ein IPerceptionSimulationManager verfügt über eine Human-Eigenschaft, die ein ISimulatedHuman-Objekt zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="5dc47-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="5dc47-159">Um die simulierten menschliche zu steuern, die Vorgänge, für dieses Objekt.</span><span class="sxs-lookup"><span data-stu-id="5dc47-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="5dc47-160">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="5dc47-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="5dc47-161">Beispiel eines grundlegenden C# Konsolenanwendung</span><span class="sxs-lookup"><span data-stu-id="5dc47-161">Basic Sample C# console application</span></span>

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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="5dc47-162">Erweiterte Beispiel C# Konsolenanwendung</span><span class="sxs-lookup"><span data-stu-id="5dc47-162">Extended Sample C# console application</span></span>

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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="5dc47-163">Notieren Sie sich auf 6-FG-Controller</span><span class="sxs-lookup"><span data-stu-id="5dc47-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="5dc47-164">Vor dem Aufrufen von Eigenschaften auf Methoden in einem simulierten 6-FG-Controller, müssen Sie den Controller aktivieren.</span><span class="sxs-lookup"><span data-stu-id="5dc47-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="5dc47-165">Nicht auf diese Weise führt eine Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="5dc47-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="5dc47-166">Ab Windows 10 möglicherweise 2019 aktualisieren, simulierte 6-FG Controller installiert und durch Festlegen der Status-Eigenschaft für das Objekt ISimulatedSixDofController SimulatedSixDofControllerStatus.Active aktiviert werden können.</span><span class="sxs-lookup"><span data-stu-id="5dc47-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="5dc47-167">In Windows 10 Oktober 2018 aktualisieren und früher müssen Sie separat einen simulierten 6-FG Controller zunächst installieren durch Aufrufen der PerceptionSimulationDevice-Tool befindet sich im Ordner \Windows\System32.</span><span class="sxs-lookup"><span data-stu-id="5dc47-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="5dc47-168">Die Verwendung dieses Tools lautet wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="5dc47-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="5dc47-169">Zum Beispiel</span><span class="sxs-lookup"><span data-stu-id="5dc47-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="5dc47-170">Unterstützte Aktionen sind:</span><span class="sxs-lookup"><span data-stu-id="5dc47-170">Supported actions are:</span></span>
* <span data-ttu-id="5dc47-171">Ich = Install</span><span class="sxs-lookup"><span data-stu-id="5dc47-171">i = install</span></span>
* <span data-ttu-id="5dc47-172">q = query</span><span class="sxs-lookup"><span data-stu-id="5dc47-172">q = query</span></span>
* <span data-ttu-id="5dc47-173">R = entfernen</span><span class="sxs-lookup"><span data-stu-id="5dc47-173">r = remove</span></span>

<span data-ttu-id="5dc47-174">Unterstützte Instanzen werden zu können:</span><span class="sxs-lookup"><span data-stu-id="5dc47-174">Supported instances are:</span></span>
* <span data-ttu-id="5dc47-175">1 = den linken 6-FG-Controller</span><span class="sxs-lookup"><span data-stu-id="5dc47-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="5dc47-176">2 = die richtige 6-FG-Controller</span><span class="sxs-lookup"><span data-stu-id="5dc47-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="5dc47-177">(Eine NULL-Wert zurückgeben) Erfolg oder Fehler (ein Wert ungleich NULL zurück), wird der Exitcode des Prozesses angegeben.</span><span class="sxs-lookup"><span data-stu-id="5dc47-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="5dc47-178">Wenn die Aktion "Q" zum Abfragen, und zwar unabhängig davon, ob ein Controller installiert ist, wird der zurückgegebene Wert sein, NULL (0), wenn der Controller noch nicht installiert ist oder eins (1), wenn der Controller installiert ist.</span><span class="sxs-lookup"><span data-stu-id="5dc47-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="5dc47-179">Beim Entfernen eines Controllers auf dem Windows aktualisieren Sie 10 Oktober 2018 oder früher legen Sie seinen Status aus über die API zuerst, klicken Sie dann das Tool PerceptionSimulationDevice aufrufen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="5dc47-180">Beachten Sie, dass dieses Tool als Administrator ausgeführt werden muss.</span><span class="sxs-lookup"><span data-stu-id="5dc47-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="5dc47-181">API-Referenz</span><span class="sxs-lookup"><span data-stu-id="5dc47-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="5dc47-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span><span class="sxs-lookup"><span data-stu-id="5dc47-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="5dc47-183">Beschreibt einen Typ des simulierten Geräts</span><span class="sxs-lookup"><span data-stu-id="5dc47-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="5dc47-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span><span class="sxs-lookup"><span data-stu-id="5dc47-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="5dc47-185">Ein Gerät fiktiven Verweis, der Standardwert für PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="5dc47-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="5dc47-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span><span class="sxs-lookup"><span data-stu-id="5dc47-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="5dc47-187">Beschreibt einen Head-Tracker-Modus</span><span class="sxs-lookup"><span data-stu-id="5dc47-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="5dc47-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span><span class="sxs-lookup"><span data-stu-id="5dc47-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="5dc47-189">Standard-Head nachverfolgen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-189">Default Head Tracking.</span></span> <span data-ttu-id="5dc47-190">Dies bedeutet, dass das System die beste Head Überwachungsmodus basierend auf laufzeitbedingungen auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="5dc47-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="5dc47-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span><span class="sxs-lookup"><span data-stu-id="5dc47-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="5dc47-192">Ausrichtung nur Head nachverfolgen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="5dc47-193">Dies bedeutet, dass die nachverfolgte Position möglicherweise nicht zuverlässig, und einige Funktionen, die abhängig von Head Position möglicherweise nicht Verfügung zur.</span><span class="sxs-lookup"><span data-stu-id="5dc47-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="5dc47-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span><span class="sxs-lookup"><span data-stu-id="5dc47-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="5dc47-195">Mit Feldern fester Breite Head-nachverfolgung.</span><span class="sxs-lookup"><span data-stu-id="5dc47-195">Positional Head Tracking.</span></span> <span data-ttu-id="5dc47-196">Dies bedeutet, dass die nachverfolgten Head Position und Ausrichtung zuverlässig sind</span><span class="sxs-lookup"><span data-stu-id="5dc47-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="5dc47-197">Microsoft.PerceptionSimulation.SimulatedGesture</span><span class="sxs-lookup"><span data-stu-id="5dc47-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="5dc47-198">Beschreibt eine Geste für eine simulierte</span><span class="sxs-lookup"><span data-stu-id="5dc47-198">Describes a simulated gesture</span></span>

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

<span data-ttu-id="5dc47-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span><span class="sxs-lookup"><span data-stu-id="5dc47-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="5dc47-200">Ein Sentinelwert verwendet, um keine Gesten anzugeben.</span><span class="sxs-lookup"><span data-stu-id="5dc47-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="5dc47-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span><span class="sxs-lookup"><span data-stu-id="5dc47-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="5dc47-202">Ein Finger Geste gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="5dc47-202">A finger pressed gesture.</span></span>

<span data-ttu-id="5dc47-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span><span class="sxs-lookup"><span data-stu-id="5dc47-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="5dc47-204">Eine Geste Finger veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="5dc47-204">A finger released gesture.</span></span>

<span data-ttu-id="5dc47-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span><span class="sxs-lookup"><span data-stu-id="5dc47-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="5dc47-206">Die Start/System-Bewegung.</span><span class="sxs-lookup"><span data-stu-id="5dc47-206">The home/system gesture.</span></span>

<span data-ttu-id="5dc47-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span><span class="sxs-lookup"><span data-stu-id="5dc47-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="5dc47-208">Die maximale gültige Tastenkombination.</span><span class="sxs-lookup"><span data-stu-id="5dc47-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="5dc47-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span><span class="sxs-lookup"><span data-stu-id="5dc47-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="5dc47-210">Die möglichen Zustände eines simulierten 6-FG-Controllers.</span><span class="sxs-lookup"><span data-stu-id="5dc47-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="5dc47-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span><span class="sxs-lookup"><span data-stu-id="5dc47-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="5dc47-212">Der Controller 6-FG ist deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="5dc47-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="5dc47-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span><span class="sxs-lookup"><span data-stu-id="5dc47-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="5dc47-214">6-FG Controller wird eingeschaltet und nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="5dc47-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="5dc47-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span><span class="sxs-lookup"><span data-stu-id="5dc47-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="5dc47-216">6-FG Controller wird aktiviert, aber es kann nicht nachverfolgt werden.</span><span class="sxs-lookup"><span data-stu-id="5dc47-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="5dc47-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span><span class="sxs-lookup"><span data-stu-id="5dc47-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="5dc47-218">Die unterstützten Schaltflächen auf einem simulierten 6-FG-Controller.</span><span class="sxs-lookup"><span data-stu-id="5dc47-218">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="5dc47-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span><span class="sxs-lookup"><span data-stu-id="5dc47-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="5dc47-220">Ein Sentinelwert verwendet, um keine Schaltflächen anzugeben.</span><span class="sxs-lookup"><span data-stu-id="5dc47-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="5dc47-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span><span class="sxs-lookup"><span data-stu-id="5dc47-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="5dc47-222">Die Start-Schaltfläche gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="5dc47-222">The Home button is pressed.</span></span>

<span data-ttu-id="5dc47-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span><span class="sxs-lookup"><span data-stu-id="5dc47-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="5dc47-224">Die Schaltfläche gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="5dc47-224">The Menu button is pressed.</span></span>

<span data-ttu-id="5dc47-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span><span class="sxs-lookup"><span data-stu-id="5dc47-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="5dc47-226">Der Ziehpunkt ist gedrückt.</span><span class="sxs-lookup"><span data-stu-id="5dc47-226">The Grip button is pressed.</span></span>

<span data-ttu-id="5dc47-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span><span class="sxs-lookup"><span data-stu-id="5dc47-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="5dc47-228">Das TouchPad gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="5dc47-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="5dc47-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span><span class="sxs-lookup"><span data-stu-id="5dc47-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="5dc47-230">Die auswählen-Schaltfläche gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="5dc47-230">The Select button is pressed.</span></span>

<span data-ttu-id="5dc47-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span><span class="sxs-lookup"><span data-stu-id="5dc47-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="5dc47-232">Das TouchPad ist berührt werden.</span><span class="sxs-lookup"><span data-stu-id="5dc47-232">The TouchPad is touched.</span></span>

<span data-ttu-id="5dc47-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span><span class="sxs-lookup"><span data-stu-id="5dc47-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="5dc47-234">Ministick gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="5dc47-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="5dc47-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span><span class="sxs-lookup"><span data-stu-id="5dc47-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="5dc47-236">Die maximale gültige Taste.</span><span class="sxs-lookup"><span data-stu-id="5dc47-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="5dc47-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span><span class="sxs-lookup"><span data-stu-id="5dc47-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="5dc47-238">Der Status der Kalibrierung der simulierten Augen</span><span class="sxs-lookup"><span data-stu-id="5dc47-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="5dc47-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span><span class="sxs-lookup"><span data-stu-id="5dc47-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="5dc47-240">Die Augen Kalibrierung ist nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5dc47-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="5dc47-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span><span class="sxs-lookup"><span data-stu-id="5dc47-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="5dc47-242">Die Augen haben kalibriert.</span><span class="sxs-lookup"><span data-stu-id="5dc47-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="5dc47-243">Dies ist der Standardwert.</span><span class="sxs-lookup"><span data-stu-id="5dc47-243">This is the default value.</span></span>

<span data-ttu-id="5dc47-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span><span class="sxs-lookup"><span data-stu-id="5dc47-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="5dc47-245">Die Augen werden kalibriert werden.</span><span class="sxs-lookup"><span data-stu-id="5dc47-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="5dc47-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span><span class="sxs-lookup"><span data-stu-id="5dc47-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="5dc47-247">Die Augen kalibriert werden müssen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="5dc47-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span><span class="sxs-lookup"><span data-stu-id="5dc47-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="5dc47-249">Die Genauigkeit der nachverfolgung von eine Verbindung der Hand.</span><span class="sxs-lookup"><span data-stu-id="5dc47-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="5dc47-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span><span class="sxs-lookup"><span data-stu-id="5dc47-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="5dc47-251">Die Verbindung wird nicht nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="5dc47-251">The joint is not tracked.</span></span>

<span data-ttu-id="5dc47-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span><span class="sxs-lookup"><span data-stu-id="5dc47-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="5dc47-253">Die gemeinsame Position abgeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="5dc47-253">The joint position is inferred.</span></span>

<span data-ttu-id="5dc47-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span><span class="sxs-lookup"><span data-stu-id="5dc47-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="5dc47-255">Die Verbindung wird vollständig nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="5dc47-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="5dc47-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span><span class="sxs-lookup"><span data-stu-id="5dc47-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="5dc47-257">Die Genauigkeit der nachverfolgung von eine Verbindung der Hand.</span><span class="sxs-lookup"><span data-stu-id="5dc47-257">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="5dc47-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span><span class="sxs-lookup"><span data-stu-id="5dc47-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="5dc47-259">Das Handsymbol des Fingers Joints werden entsprechend einer geschlossenen Haltung konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="5dc47-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="5dc47-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span><span class="sxs-lookup"><span data-stu-id="5dc47-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="5dc47-261">Das Handsymbol des Fingers Joints werden eine offene Haltung entsprechend konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="5dc47-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="5dc47-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span><span class="sxs-lookup"><span data-stu-id="5dc47-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="5dc47-263">Das Handsymbol des Fingers Joints werden entsprechend einer zeigen Haltung konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="5dc47-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="5dc47-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span><span class="sxs-lookup"><span data-stu-id="5dc47-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="5dc47-265">Das Handsymbol des Fingers Joints werden entsprechend einer Pinch Haltung konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="5dc47-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="5dc47-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span><span class="sxs-lookup"><span data-stu-id="5dc47-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="5dc47-267">Der gültige Höchstwert für SimulatedHandPose.</span><span class="sxs-lookup"><span data-stu-id="5dc47-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="5dc47-268">Microsoft.PerceptionSimulation.PlaybackState</span><span class="sxs-lookup"><span data-stu-id="5dc47-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="5dc47-269">Beschreibt den Status der eine Wiedergabe.</span><span class="sxs-lookup"><span data-stu-id="5dc47-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="5dc47-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span><span class="sxs-lookup"><span data-stu-id="5dc47-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="5dc47-271">Die Aufzeichnung ist derzeit beendet "und" bereit für die Wiedergabe.</span><span class="sxs-lookup"><span data-stu-id="5dc47-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="5dc47-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span><span class="sxs-lookup"><span data-stu-id="5dc47-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="5dc47-273">Die Aufzeichnung wird aktuell wiedergegebenen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-273">The recording is currently playing.</span></span>

<span data-ttu-id="5dc47-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span><span class="sxs-lookup"><span data-stu-id="5dc47-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="5dc47-275">Die Aufzeichnung wird angehalten.</span><span class="sxs-lookup"><span data-stu-id="5dc47-275">The recording is currently paused.</span></span>

<span data-ttu-id="5dc47-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span><span class="sxs-lookup"><span data-stu-id="5dc47-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="5dc47-277">Das Ende wurde die Aufzeichnung erreicht werden.</span><span class="sxs-lookup"><span data-stu-id="5dc47-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="5dc47-278">Microsoft.PerceptionSimulation.Vector3</span><span class="sxs-lookup"><span data-stu-id="5dc47-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="5dc47-279">Beschreibt einen Vektor 3 Komponenten, der einen Punkt oder einen Vektor im 3D-Raum beschreiben kann.</span><span class="sxs-lookup"><span data-stu-id="5dc47-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="5dc47-280">**Microsoft.PerceptionSimulation.Vector3.X**</span><span class="sxs-lookup"><span data-stu-id="5dc47-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="5dc47-281">Die X-Komponente des Vektors.</span><span class="sxs-lookup"><span data-stu-id="5dc47-281">The X component of the vector.</span></span>

<span data-ttu-id="5dc47-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span><span class="sxs-lookup"><span data-stu-id="5dc47-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="5dc47-283">Die Y-Komponente des Vektors.</span><span class="sxs-lookup"><span data-stu-id="5dc47-283">The Y component of the vector.</span></span>

<span data-ttu-id="5dc47-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span><span class="sxs-lookup"><span data-stu-id="5dc47-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="5dc47-285">Die Z-Komponente des Vektors.</span><span class="sxs-lookup"><span data-stu-id="5dc47-285">The Z component of the vector.</span></span>

<span data-ttu-id="5dc47-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="5dc47-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="5dc47-287">Erstellen Sie eine neue Vector3.</span><span class="sxs-lookup"><span data-stu-id="5dc47-287">Construct a new Vector3.</span></span>

<span data-ttu-id="5dc47-288">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dc47-288">Parameters</span></span>
* <span data-ttu-id="5dc47-289">X: die X-Komponente des Vektors.</span><span class="sxs-lookup"><span data-stu-id="5dc47-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="5dc47-290">y - der y-Komponente des Vektors.</span><span class="sxs-lookup"><span data-stu-id="5dc47-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="5dc47-291">Z - der Z-Komponente des Vektors.</span><span class="sxs-lookup"><span data-stu-id="5dc47-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="5dc47-292">Microsoft.PerceptionSimulation.Rotation3</span><span class="sxs-lookup"><span data-stu-id="5dc47-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="5dc47-293">Beschreibt eine Drehung um 3 Komponenten an.</span><span class="sxs-lookup"><span data-stu-id="5dc47-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="5dc47-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span><span class="sxs-lookup"><span data-stu-id="5dc47-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="5dc47-295">Die Schriftbreite-Komponente, der die Drehung nach unten, um die x-Achse.</span><span class="sxs-lookup"><span data-stu-id="5dc47-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="5dc47-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span><span class="sxs-lookup"><span data-stu-id="5dc47-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="5dc47-297">Der Yaw-Komponente der Drehung, ganz in der Nähe der Y-Achse dargestellt.</span><span class="sxs-lookup"><span data-stu-id="5dc47-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="5dc47-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span><span class="sxs-lookup"><span data-stu-id="5dc47-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="5dc47-299">Die Rollup-Komponente von der Rotation nach rechts um die Z-Achse.</span><span class="sxs-lookup"><span data-stu-id="5dc47-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="5dc47-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span><span class="sxs-lookup"><span data-stu-id="5dc47-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="5dc47-301">Erstellen Sie eine neue Rotation3.</span><span class="sxs-lookup"><span data-stu-id="5dc47-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="5dc47-302">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dc47-302">Parameters</span></span>
* <span data-ttu-id="5dc47-303">Schriftbreite – die Schriftbreite-Komponente der Drehung.</span><span class="sxs-lookup"><span data-stu-id="5dc47-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="5dc47-304">Yaw - der Yaw-Komponente der Drehung.</span><span class="sxs-lookup"><span data-stu-id="5dc47-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="5dc47-305">Rollback - die Rollup-Komponente der Drehung.</span><span class="sxs-lookup"><span data-stu-id="5dc47-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="5dc47-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span><span class="sxs-lookup"><span data-stu-id="5dc47-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="5dc47-307">Beschreibt die Konfiguration der eine Verbindung unter einer simulierten Hand.</span><span class="sxs-lookup"><span data-stu-id="5dc47-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="5dc47-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span><span class="sxs-lookup"><span data-stu-id="5dc47-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="5dc47-309">Die Position des gemeinsamen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-309">The position of the joint.</span></span>

<span data-ttu-id="5dc47-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span><span class="sxs-lookup"><span data-stu-id="5dc47-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="5dc47-311">Die Drehung des gemeinsamen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-311">The rotation of the joint.</span></span>

<span data-ttu-id="5dc47-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span><span class="sxs-lookup"><span data-stu-id="5dc47-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="5dc47-313">Die Genauigkeit der nachverfolgung von der Verbindung.</span><span class="sxs-lookup"><span data-stu-id="5dc47-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="5dc47-314">Microsoft.PerceptionSimulation.Frustum</span><span class="sxs-lookup"><span data-stu-id="5dc47-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="5dc47-315">Beschreibt eine Sicht Frustums, in der Regel durch eine Kamera verwendet.</span><span class="sxs-lookup"><span data-stu-id="5dc47-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="5dc47-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span><span class="sxs-lookup"><span data-stu-id="5dc47-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="5dc47-317">Der Mindestabstand, der in der Frustums enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="5dc47-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="5dc47-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span><span class="sxs-lookup"><span data-stu-id="5dc47-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="5dc47-319">Der maximale Abstand, der in der Frustums enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="5dc47-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="5dc47-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span><span class="sxs-lookup"><span data-stu-id="5dc47-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="5dc47-321">Das horizontale Sichtfeld der der Frustums, im Bogenmaß (weniger als PI).</span><span class="sxs-lookup"><span data-stu-id="5dc47-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="5dc47-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="5dc47-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="5dc47-323">Das Verhältnis der horizontale Sichtfeld auf einer vertikale Sichtfeld.</span><span class="sxs-lookup"><span data-stu-id="5dc47-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="5dc47-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="5dc47-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="5dc47-325">Stammverzeichnis für das Generieren der Pakete verwendet, um ein Gerät zu steuern.</span><span class="sxs-lookup"><span data-stu-id="5dc47-325">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="5dc47-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span><span class="sxs-lookup"><span data-stu-id="5dc47-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="5dc47-327">Abrufen der simulierten Geräte-Objekt, das die simulierten menschliche und die simulierten Welt interpretiert.</span><span class="sxs-lookup"><span data-stu-id="5dc47-327">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="5dc47-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span><span class="sxs-lookup"><span data-stu-id="5dc47-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="5dc47-329">Rufen Sie das Objekt, das die simulierte menschliche steuert.</span><span class="sxs-lookup"><span data-stu-id="5dc47-329">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="5dc47-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span><span class="sxs-lookup"><span data-stu-id="5dc47-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="5dc47-331">Die Simulation zurückgesetzt auf ihren Standardzustand.</span><span class="sxs-lookup"><span data-stu-id="5dc47-331">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="5dc47-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span><span class="sxs-lookup"><span data-stu-id="5dc47-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="5dc47-333">Schnittstelle, die das Gerät, das in der simulierten Welt und die simulierten menschliche interpretiert beschreibt.</span><span class="sxs-lookup"><span data-stu-id="5dc47-333">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="5dc47-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span><span class="sxs-lookup"><span data-stu-id="5dc47-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="5dc47-335">Abrufen der Head-nachverfolgung vom simulierten Gerät an.</span><span class="sxs-lookup"><span data-stu-id="5dc47-335">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="5dc47-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span><span class="sxs-lookup"><span data-stu-id="5dc47-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="5dc47-337">Rufen Sie die nachverfolgung manuell vom simulierten Gerät an.</span><span class="sxs-lookup"><span data-stu-id="5dc47-337">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="5dc47-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span><span class="sxs-lookup"><span data-stu-id="5dc47-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="5dc47-339">Legen Sie die Eigenschaften des simulierten Geräts entsprechend den angegebenen Gerätetyp.</span><span class="sxs-lookup"><span data-stu-id="5dc47-339">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="5dc47-340">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dc47-340">Parameters</span></span>
* <span data-ttu-id="5dc47-341">Type - der neuen Typs des simulierten Geräts</span><span class="sxs-lookup"><span data-stu-id="5dc47-341">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="5dc47-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span><span class="sxs-lookup"><span data-stu-id="5dc47-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="5dc47-343">Schnittstelle, die den Teil des simulierten Geräts, das den Anfang der simulierten Benutzer nachverfolgt beschreibt.</span><span class="sxs-lookup"><span data-stu-id="5dc47-343">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="5dc47-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span><span class="sxs-lookup"><span data-stu-id="5dc47-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="5dc47-345">Ruft ab, und setzt den aktuellen Modus des Head-Tracker.</span><span class="sxs-lookup"><span data-stu-id="5dc47-345">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="5dc47-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span><span class="sxs-lookup"><span data-stu-id="5dc47-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="5dc47-347">Schnittstelle, die den Teil des simulierten Geräts, das die Hände von den simulierten Benutzer nachverfolgt beschreibt.</span><span class="sxs-lookup"><span data-stu-id="5dc47-347">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="5dc47-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="5dc47-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="5dc47-349">Rufen Sie die Position des Knotens in Bezug auf der ganzen Welt in Meter.</span><span class="sxs-lookup"><span data-stu-id="5dc47-349">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="5dc47-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span><span class="sxs-lookup"><span data-stu-id="5dc47-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="5dc47-351">Abrufen und die Position der simulierten Hand Tracker Bezug auf den Mittelpunkt des Anfangswerts festlegen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-351">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="5dc47-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span><span class="sxs-lookup"><span data-stu-id="5dc47-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="5dc47-353">Abrufen und die nach unten weisenden Tonhöhe der nachverfolgung von simulierten manuell festlegen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-353">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="5dc47-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span><span class="sxs-lookup"><span data-stu-id="5dc47-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="5dc47-355">Rufen Sie ab und festlegen Sie, ob die Frustums simulierten Hand Tracker ignoriert wird.</span><span class="sxs-lookup"><span data-stu-id="5dc47-355">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="5dc47-356">Wenn ignoriert, sind die beiden Händen immer sichtbar.</span><span class="sxs-lookup"><span data-stu-id="5dc47-356">When ignored, both hands are always visible.</span></span> <span data-ttu-id="5dc47-357">Wenn (Standard) nicht ignoriert sind praktische nur sichtbar, wenn sie innerhalb der Frustums Hand Tracker sind.</span><span class="sxs-lookup"><span data-stu-id="5dc47-357">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="5dc47-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span><span class="sxs-lookup"><span data-stu-id="5dc47-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="5dc47-359">Abrufen und Festlegen der Frustums Eigenschaften verwendet, um zu bestimmen, ob die Hände für die nachverfolgung von simulierten Hand sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="5dc47-359">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="5dc47-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span><span class="sxs-lookup"><span data-stu-id="5dc47-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="5dc47-361">Top Level-Schnittstelle zum Steuern von den simulierten Benutzer.</span><span class="sxs-lookup"><span data-stu-id="5dc47-361">Top level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="5dc47-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="5dc47-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="5dc47-363">Abzurufen Sie, und legen Sie die Position des Knotens Bezug auf der ganzen Welt, in Meter.</span><span class="sxs-lookup"><span data-stu-id="5dc47-363">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="5dc47-364">Die Position entspricht einem Punkt in der Mitte der Mensch Zentimetern Abweichung.</span><span class="sxs-lookup"><span data-stu-id="5dc47-364">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="5dc47-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span><span class="sxs-lookup"><span data-stu-id="5dc47-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="5dc47-366">Abrufen und Festlegen der Richtung der simulierten menschliche Gesichter in der ganzen Welt.</span><span class="sxs-lookup"><span data-stu-id="5dc47-366">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="5dc47-367">0 Bogenmaß Gesichtern nach unten der negativen Z-Achse.</span><span class="sxs-lookup"><span data-stu-id="5dc47-367">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="5dc47-368">Positive Bogenmaß Drehen im Uhrzeigersinn die y-Achse.</span><span class="sxs-lookup"><span data-stu-id="5dc47-368">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="5dc47-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span><span class="sxs-lookup"><span data-stu-id="5dc47-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="5dc47-370">Abrufen und Festlegen der Höhe der simulierten vom Menschen in Meter.</span><span class="sxs-lookup"><span data-stu-id="5dc47-370">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="5dc47-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span><span class="sxs-lookup"><span data-stu-id="5dc47-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="5dc47-372">Abrufen von links von den simulierten Benutzer.</span><span class="sxs-lookup"><span data-stu-id="5dc47-372">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="5dc47-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span><span class="sxs-lookup"><span data-stu-id="5dc47-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="5dc47-374">Rufen Sie die rechte Seite von den simulierten Benutzer.</span><span class="sxs-lookup"><span data-stu-id="5dc47-374">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="5dc47-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span><span class="sxs-lookup"><span data-stu-id="5dc47-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="5dc47-376">Rufen Sie den Anfang der simulierten Benutzer.</span><span class="sxs-lookup"><span data-stu-id="5dc47-376">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="5dc47-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="5dc47-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="5dc47-378">Verschieben Sie die simulierte menschliche Bezug auf seine aktuelle Position in Meter.</span><span class="sxs-lookup"><span data-stu-id="5dc47-378">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="5dc47-379">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dc47-379">Parameters</span></span>
* <span data-ttu-id="5dc47-380">Übersetzung: die Verschiebung, relativ zur aktuellen Position zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="5dc47-380">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="5dc47-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span><span class="sxs-lookup"><span data-stu-id="5dc47-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="5dc47-382">Drehen Sie die simulierte menschliche relativ zum aktuellen Richtung, die y-Achse im Uhrzeigersinn</span><span class="sxs-lookup"><span data-stu-id="5dc47-382">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="5dc47-383">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dc47-383">Parameters</span></span>
* <span data-ttu-id="5dc47-384">Bogenmaß (Radiant) – der Betrag, um die y-Achse gedreht.</span><span class="sxs-lookup"><span data-stu-id="5dc47-384">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="5dc47-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="5dc47-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="5dc47-386">Zusätzliche Eigenschaften zur Verfügung, durch das Umwandeln der ISimulatedHuman zu ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="5dc47-386">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="5dc47-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span><span class="sxs-lookup"><span data-stu-id="5dc47-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="5dc47-388">Abgerufen Sie den linke 6-FG-Controller werden.</span><span class="sxs-lookup"><span data-stu-id="5dc47-388">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="5dc47-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span><span class="sxs-lookup"><span data-stu-id="5dc47-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="5dc47-390">Rufen Sie den richtigen 6-FG-Controller.</span><span class="sxs-lookup"><span data-stu-id="5dc47-390">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="5dc47-391">Microsoft.PerceptionSimulation.ISimulatedHand</span><span class="sxs-lookup"><span data-stu-id="5dc47-391">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="5dc47-392">Schnittstelle, die eine Hand von den simulierten Benutzer beschreibt.</span><span class="sxs-lookup"><span data-stu-id="5dc47-392">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="5dc47-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="5dc47-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="5dc47-394">Rufen Sie die Position des Knotens in Bezug auf der ganzen Welt in Meter.</span><span class="sxs-lookup"><span data-stu-id="5dc47-394">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="5dc47-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span><span class="sxs-lookup"><span data-stu-id="5dc47-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="5dc47-396">Abrufen und Festlegen der Position eines simulierten relativ zu der vom Menschen in Meter.</span><span class="sxs-lookup"><span data-stu-id="5dc47-396">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="5dc47-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span><span class="sxs-lookup"><span data-stu-id="5dc47-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="5dc47-398">Rufen Sie ab und festlegen Sie, ob das Handsymbol derzeit aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="5dc47-398">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="5dc47-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span><span class="sxs-lookup"><span data-stu-id="5dc47-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="5dc47-400">Rufen Sie, ob das Handsymbol derzeit sichtbar ist, um die SimulatedDevice ist (z. B. ob er in der Lage, die von der HandTracker erkannt werden ist).</span><span class="sxs-lookup"><span data-stu-id="5dc47-400">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="5dc47-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="5dc47-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="5dc47-402">Verschieben Sie die Hand, dass es für die SimulatedDevice sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="5dc47-402">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="5dc47-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="5dc47-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="5dc47-404">Verschieben Sie die Position eines simulierten Bezug auf seine aktuelle Position in Meter.</span><span class="sxs-lookup"><span data-stu-id="5dc47-404">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="5dc47-405">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dc47-405">Parameters</span></span>
* <span data-ttu-id="5dc47-406">Übersetzung: der Betrag, um die simulierten manuell übersetzt.</span><span class="sxs-lookup"><span data-stu-id="5dc47-406">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="5dc47-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span><span class="sxs-lookup"><span data-stu-id="5dc47-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="5dc47-408">Führen Sie eine Geste für eine mithilfe der simulierten Hand.</span><span class="sxs-lookup"><span data-stu-id="5dc47-408">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="5dc47-409">Es wird nur vom System erkannt werden, wenn die Seite aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="5dc47-409">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="5dc47-410">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dc47-410">Parameters</span></span>
* <span data-ttu-id="5dc47-411">Tastenkombination: die Geste zum Ausführen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-411">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="5dc47-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="5dc47-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="5dc47-413">Zusätzliche Eigenschaften sind durch das Umwandeln einer ISimulatedHand zu ISimulatedHand2 verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5dc47-413">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="5dc47-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span><span class="sxs-lookup"><span data-stu-id="5dc47-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="5dc47-415">Rufen Sie ab, oder legen Sie die Rotation der simulierten Hand.</span><span class="sxs-lookup"><span data-stu-id="5dc47-415">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="5dc47-416">Positive Bogenmaß (Radiant) werden bei der Suche auf der Achse im Uhrzeigersinn drehen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-416">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="5dc47-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="5dc47-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="5dc47-418">Zusätzliche Eigenschaften zur Verfügung, durch das Umwandeln einer ISimulatedHand zu ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="5dc47-418">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="5dc47-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="5dc47-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="5dc47-420">Rufen Sie die gemeinsame Konfiguration für die angegebene Verbindung.</span><span class="sxs-lookup"><span data-stu-id="5dc47-420">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="5dc47-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span><span class="sxs-lookup"><span data-stu-id="5dc47-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="5dc47-422">Legen Sie die gemeinsame Konfiguration für die angegebene Verbindung.</span><span class="sxs-lookup"><span data-stu-id="5dc47-422">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="5dc47-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span><span class="sxs-lookup"><span data-stu-id="5dc47-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="5dc47-424">Legen Sie das Handsymbol, auf einen bekannten Haltung mit ein optionalen Kennzeichen, um zu animieren.</span><span class="sxs-lookup"><span data-stu-id="5dc47-424">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="5dc47-425">Hinweis: Animieren in Joints sofort reflektieren ihren endgültigen gemeinsamen Konfigurationen wird nicht dazu.</span><span class="sxs-lookup"><span data-stu-id="5dc47-425">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="5dc47-426">Microsoft.PerceptionSimulation.ISimulatedHead</span><span class="sxs-lookup"><span data-stu-id="5dc47-426">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="5dc47-427">Schnittstelle, die den Anfang der simulierten Menschen beschreibt.</span><span class="sxs-lookup"><span data-stu-id="5dc47-427">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="5dc47-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="5dc47-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="5dc47-429">Rufen Sie die Position des Knotens in Bezug auf der ganzen Welt in Meter.</span><span class="sxs-lookup"><span data-stu-id="5dc47-429">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="5dc47-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span><span class="sxs-lookup"><span data-stu-id="5dc47-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="5dc47-431">Rufen Sie die Rotation der simulierten Head.</span><span class="sxs-lookup"><span data-stu-id="5dc47-431">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="5dc47-432">Positive Bogenmaß (Radiant) werden bei der Suche auf der Achse im Uhrzeigersinn drehen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-432">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="5dc47-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span><span class="sxs-lookup"><span data-stu-id="5dc47-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="5dc47-434">Abrufen des simulierten Anfangselements Durchmesser.</span><span class="sxs-lookup"><span data-stu-id="5dc47-434">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="5dc47-435">Dieser Wert wird verwendet, um zu bestimmen, des Anfangselements Center (Punkt der Drehung).</span><span class="sxs-lookup"><span data-stu-id="5dc47-435">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="5dc47-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="5dc47-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="5dc47-437">Drehen Sie die simulierte Head relativ zu dessen aktuellen Rotationsachse.</span><span class="sxs-lookup"><span data-stu-id="5dc47-437">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="5dc47-438">Positive Bogenmaß (Radiant) werden bei der Suche auf der Achse im Uhrzeigersinn drehen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-438">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="5dc47-439">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dc47-439">Parameters</span></span>
* <span data-ttu-id="5dc47-440">Rotation – der Betrag, um zu drehen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-440">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="5dc47-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="5dc47-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="5dc47-442">Zusätzliche Eigenschaften zur Verfügung, durch das Umwandeln einer ISimulatedHead zu ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="5dc47-442">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="5dc47-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span><span class="sxs-lookup"><span data-stu-id="5dc47-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="5dc47-444">Rufen Sie die Augen der simulierten Mensch.</span><span class="sxs-lookup"><span data-stu-id="5dc47-444">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="5dc47-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span><span class="sxs-lookup"><span data-stu-id="5dc47-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="5dc47-446">Schnittstelle, die einen 6-FG-Controller mit dem simulierten Menschen verknüpften beschreibt.</span><span class="sxs-lookup"><span data-stu-id="5dc47-446">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="5dc47-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="5dc47-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="5dc47-448">Rufen Sie die Position des Knotens in Bezug auf der ganzen Welt in Meter.</span><span class="sxs-lookup"><span data-stu-id="5dc47-448">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="5dc47-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span><span class="sxs-lookup"><span data-stu-id="5dc47-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="5dc47-450">Rufen Sie ab, oder legen Sie den aktuellen Status des Controllers.</span><span class="sxs-lookup"><span data-stu-id="5dc47-450">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="5dc47-451">Der Status des Controllers muss auf einen Wert festgelegt werden, außer aus vor allen Aufrufen von verschieben, drehen, oder drücken die Schaltflächen erfolgreich ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="5dc47-451">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="5dc47-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span><span class="sxs-lookup"><span data-stu-id="5dc47-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="5dc47-453">Abrufen oder Festlegen der Position des simulierten Controllers relativ zu der vom Menschen in Meter.</span><span class="sxs-lookup"><span data-stu-id="5dc47-453">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="5dc47-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span><span class="sxs-lookup"><span data-stu-id="5dc47-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="5dc47-455">Abrufen oder Festlegen der Ausrichtung des simulierten Controllers.</span><span class="sxs-lookup"><span data-stu-id="5dc47-455">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="5dc47-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span><span class="sxs-lookup"><span data-stu-id="5dc47-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="5dc47-457">Verschieben Sie die Position des simulierten Controllers Bezug auf seine aktuelle Position in Meter.</span><span class="sxs-lookup"><span data-stu-id="5dc47-457">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="5dc47-458">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dc47-458">Parameters</span></span>
* <span data-ttu-id="5dc47-459">Übersetzung: der Betrag, um den simulierten Controller zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-459">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="5dc47-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="5dc47-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="5dc47-461">Drücken Sie eine Schaltfläche auf dem simulierten Controller aus.</span><span class="sxs-lookup"><span data-stu-id="5dc47-461">Press a button on the simulated controller.</span></span>  <span data-ttu-id="5dc47-462">Es wird nur vom System erkannt werden, wenn der Controller aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="5dc47-462">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="5dc47-463">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dc47-463">Parameters</span></span>
* <span data-ttu-id="5dc47-464">-Die Schaltfläche drücken.</span><span class="sxs-lookup"><span data-stu-id="5dc47-464">button - The button to press.</span></span>

<span data-ttu-id="5dc47-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span><span class="sxs-lookup"><span data-stu-id="5dc47-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="5dc47-466">Freigeben einer Schaltfläche auf dem simulierten Controller.</span><span class="sxs-lookup"><span data-stu-id="5dc47-466">Release a button on the simulated controller.</span></span>  <span data-ttu-id="5dc47-467">Es wird nur vom System erkannt werden, wenn der Controller aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="5dc47-467">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="5dc47-468">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dc47-468">Parameters</span></span>
* <span data-ttu-id="5dc47-469">-Die Schaltfläche freigeben.</span><span class="sxs-lookup"><span data-stu-id="5dc47-469">button - The button to release.</span></span>

<span data-ttu-id="5dc47-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="5dc47-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="5dc47-471">Die Position mit einem simulierten Finger auf der simulierten Controller Touchpad abzurufen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-471">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="5dc47-472">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dc47-472">Parameters</span></span>
* <span data-ttu-id="5dc47-473">X – die horizontale Position des Fingers.</span><span class="sxs-lookup"><span data-stu-id="5dc47-473">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="5dc47-474">y - die vertikale Position des Fingers.</span><span class="sxs-lookup"><span data-stu-id="5dc47-474">y - The vertical position of the finger.</span></span>

<span data-ttu-id="5dc47-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span><span class="sxs-lookup"><span data-stu-id="5dc47-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="5dc47-476">Positionieren Sie die mit einem simulierten Finger auf der simulierten Controller Touchpad.</span><span class="sxs-lookup"><span data-stu-id="5dc47-476">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="5dc47-477">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dc47-477">Parameters</span></span>
* <span data-ttu-id="5dc47-478">X – die horizontale Position des Fingers.</span><span class="sxs-lookup"><span data-stu-id="5dc47-478">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="5dc47-479">y - die vertikale Position des Fingers.</span><span class="sxs-lookup"><span data-stu-id="5dc47-479">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="5dc47-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="5dc47-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="5dc47-481">Zusätzliche Eigenschaften und Methoden sind verfügbar, durch das Umwandeln einer ISimulatedSixDofController zu ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="5dc47-481">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="5dc47-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="5dc47-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="5dc47-483">Die Position des simulierten Ministick auf dem simulierten Controller abzurufen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-483">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="5dc47-484">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dc47-484">Parameters</span></span>
* <span data-ttu-id="5dc47-485">X – die horizontale Position des Ministick.</span><span class="sxs-lookup"><span data-stu-id="5dc47-485">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="5dc47-486">y - die vertikale Position des Ministick.</span><span class="sxs-lookup"><span data-stu-id="5dc47-486">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="5dc47-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span><span class="sxs-lookup"><span data-stu-id="5dc47-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="5dc47-488">Legen Sie die Position des simulierten Ministick, auf dem simulierten Controller.</span><span class="sxs-lookup"><span data-stu-id="5dc47-488">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="5dc47-489">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dc47-489">Parameters</span></span>
* <span data-ttu-id="5dc47-490">X – die horizontale Position des Ministick.</span><span class="sxs-lookup"><span data-stu-id="5dc47-490">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="5dc47-491">y - die vertikale Position des Ministick.</span><span class="sxs-lookup"><span data-stu-id="5dc47-491">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="5dc47-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span><span class="sxs-lookup"><span data-stu-id="5dc47-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="5dc47-493">Abrufen oder Festlegen der Ladezustand der Batterie des simulierten Controllers.</span><span class="sxs-lookup"><span data-stu-id="5dc47-493">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="5dc47-494">Der Wert muss größer als 0,0 sein und kleiner als oder gleich 100,0.</span><span class="sxs-lookup"><span data-stu-id="5dc47-494">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="5dc47-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span><span class="sxs-lookup"><span data-stu-id="5dc47-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="5dc47-496">Schnittstelle, die die Augen der simulierten Mensch beschreibt.</span><span class="sxs-lookup"><span data-stu-id="5dc47-496">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="5dc47-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span><span class="sxs-lookup"><span data-stu-id="5dc47-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="5dc47-498">Rufen Sie die Rotation der simulierten Augen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-498">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="5dc47-499">Positive Bogenmaß (Radiant) werden bei der Suche auf der Achse im Uhrzeigersinn drehen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-499">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="5dc47-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="5dc47-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="5dc47-501">Drehen Sie die simulierten Augen relativ zu dessen aktuellen Rotationsachse.</span><span class="sxs-lookup"><span data-stu-id="5dc47-501">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="5dc47-502">Positive Bogenmaß (Radiant) werden bei der Suche auf der Achse im Uhrzeigersinn drehen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-502">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="5dc47-503">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dc47-503">Parameters</span></span>
* <span data-ttu-id="5dc47-504">Rotation – der Betrag, um zu drehen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-504">rotation - The amount to rotate.</span></span>

<span data-ttu-id="5dc47-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span><span class="sxs-lookup"><span data-stu-id="5dc47-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="5dc47-506">Ruft ab, oder legt diesen fest den Status der Kalibrierung der simulierten Augen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-506">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="5dc47-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span><span class="sxs-lookup"><span data-stu-id="5dc47-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="5dc47-508">Rufen Sie die Position des Knotens in Bezug auf der ganzen Welt in Meter.</span><span class="sxs-lookup"><span data-stu-id="5dc47-508">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="5dc47-509">Microsoft.PerceptionSimulation.ISimulationRecording</span><span class="sxs-lookup"><span data-stu-id="5dc47-509">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="5dc47-510">Eine Schnittstelle für die Interaktion mit einem einzelnen geladen, für die Wiedergabe aufzeichnen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-510">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="5dc47-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span><span class="sxs-lookup"><span data-stu-id="5dc47-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="5dc47-512">Ruft eine Liste der Datentypen in die Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="5dc47-512">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="5dc47-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span><span class="sxs-lookup"><span data-stu-id="5dc47-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="5dc47-514">Ruft den aktuellen Status der Aufzeichnung ab.</span><span class="sxs-lookup"><span data-stu-id="5dc47-514">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="5dc47-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span><span class="sxs-lookup"><span data-stu-id="5dc47-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="5dc47-516">Die Wiedergabe zu starten.</span><span class="sxs-lookup"><span data-stu-id="5dc47-516">Start the playback.</span></span> <span data-ttu-id="5dc47-517">Wenn die Aufzeichnung angehalten wird, wird die Wiedergabe aus dem angehaltenen Speicherort fortgesetzt; Wenn beendet, wird die Wiedergabe am Anfang beginnen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-517">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="5dc47-518">Wenn bereits abgespielt wird, wird dieser Aufruf ignoriert.</span><span class="sxs-lookup"><span data-stu-id="5dc47-518">If already playing, this call is ignored.</span></span>

<span data-ttu-id="5dc47-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span><span class="sxs-lookup"><span data-stu-id="5dc47-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="5dc47-520">Hält die Wiedergabe an dessen aktuellen Speicherort an.</span><span class="sxs-lookup"><span data-stu-id="5dc47-520">Pauses the playback at its current location.</span></span> <span data-ttu-id="5dc47-521">Wenn die Aufzeichnung beendet wird, wird der Aufruf ignoriert.</span><span class="sxs-lookup"><span data-stu-id="5dc47-521">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="5dc47-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span><span class="sxs-lookup"><span data-stu-id="5dc47-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="5dc47-523">Suchen die Aufzeichnung auf die angegebene Zeit (in 100-Nanosekunden-Intervallen ab) und an dieser Position angehalten wird.</span><span class="sxs-lookup"><span data-stu-id="5dc47-523">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="5dc47-524">Wenn die Zeit nach dem Ende der Aufzeichnung ist, wird es im letzten Frame angehalten.</span><span class="sxs-lookup"><span data-stu-id="5dc47-524">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="5dc47-525">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dc47-525">Parameters</span></span>
* <span data-ttu-id="5dc47-526">Ticks - die Zeit, um zu suchen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-526">ticks - The time to which to seek.</span></span>

<span data-ttu-id="5dc47-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span><span class="sxs-lookup"><span data-stu-id="5dc47-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="5dc47-528">Die Wiedergabe beendet, und setzt die Position, an den Anfang.</span><span class="sxs-lookup"><span data-stu-id="5dc47-528">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="5dc47-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span><span class="sxs-lookup"><span data-stu-id="5dc47-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="5dc47-530">Eine Schnittstelle für den Empfang von Änderungen des Ansichtszustands während der Wiedergabe.</span><span class="sxs-lookup"><span data-stu-id="5dc47-530">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="5dc47-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span><span class="sxs-lookup"><span data-stu-id="5dc47-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="5dc47-532">Wird aufgerufen, wenn es sich bei einer ISimulationRecordings Wiedergabe-Zustand geändert hat.</span><span class="sxs-lookup"><span data-stu-id="5dc47-532">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="5dc47-533">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dc47-533">Parameters</span></span>
* <span data-ttu-id="5dc47-534">NewState – der neue Status der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="5dc47-534">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="5dc47-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span><span class="sxs-lookup"><span data-stu-id="5dc47-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="5dc47-536">Stammobjekt zum Erstellen von Perception Simulation-Objekten.</span><span class="sxs-lookup"><span data-stu-id="5dc47-536">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="5dc47-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span><span class="sxs-lookup"><span data-stu-id="5dc47-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="5dc47-538">Erstellen Sie auf das Objekt zum Generieren von simulierten Pakete und an die angegebene Senke bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-538">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="5dc47-539">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dc47-539">Parameters</span></span>
* <span data-ttu-id="5dc47-540">Sink - Senke, die alle generierten Pakete empfangen wird.</span><span class="sxs-lookup"><span data-stu-id="5dc47-540">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="5dc47-541">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="5dc47-541">Return value</span></span>

<span data-ttu-id="5dc47-542">Der erstellte-Manager.</span><span class="sxs-lookup"><span data-stu-id="5dc47-542">The created Manager.</span></span>

<span data-ttu-id="5dc47-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span><span class="sxs-lookup"><span data-stu-id="5dc47-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="5dc47-544">Erstellen Sie eine Senke, die alle empfangenen Pakete in einer Datei unter dem angegebenen Pfad gespeichert.</span><span class="sxs-lookup"><span data-stu-id="5dc47-544">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="5dc47-545">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dc47-545">Parameters</span></span>
* <span data-ttu-id="5dc47-546">Pfad – der Pfad des zu erstellenden Datei.</span><span class="sxs-lookup"><span data-stu-id="5dc47-546">path - The path of the file to create.</span></span>

<span data-ttu-id="5dc47-547">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="5dc47-547">Return value</span></span>

<span data-ttu-id="5dc47-548">Die erstellte Senke.</span><span class="sxs-lookup"><span data-stu-id="5dc47-548">The created sink.</span></span>

<span data-ttu-id="5dc47-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span><span class="sxs-lookup"><span data-stu-id="5dc47-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="5dc47-550">Laden Sie eine Aufzeichnung aus der angegebenen Datei.</span><span class="sxs-lookup"><span data-stu-id="5dc47-550">Load a recording from the specified file.</span></span>

<span data-ttu-id="5dc47-551">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dc47-551">Parameters</span></span>
* <span data-ttu-id="5dc47-552">Pfad – der Pfad der zu ladenden Datei.</span><span class="sxs-lookup"><span data-stu-id="5dc47-552">path - The path of the file to load.</span></span>
* <span data-ttu-id="5dc47-553">Factory – eine Factory, die durch die Aufzeichnung für die Erstellung einer ISimulationStreamSink bei Bedarf verwendet.</span><span class="sxs-lookup"><span data-stu-id="5dc47-553">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="5dc47-554">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="5dc47-554">Return value</span></span>

<span data-ttu-id="5dc47-555">Die geladenen Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="5dc47-555">The loaded recording.</span></span>

<span data-ttu-id="5dc47-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording (System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory, Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span><span class="sxs-lookup"><span data-stu-id="5dc47-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="5dc47-557">Laden Sie eine Aufzeichnung aus der angegebenen Datei.</span><span class="sxs-lookup"><span data-stu-id="5dc47-557">Load a recording from the specified file.</span></span>

<span data-ttu-id="5dc47-558">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dc47-558">Parameters</span></span>
* <span data-ttu-id="5dc47-559">Pfad – der Pfad der zu ladenden Datei.</span><span class="sxs-lookup"><span data-stu-id="5dc47-559">path - The path of the file to load.</span></span>
* <span data-ttu-id="5dc47-560">Factory – eine Factory, die durch die Aufzeichnung für die Erstellung einer ISimulationStreamSink bei Bedarf verwendet.</span><span class="sxs-lookup"><span data-stu-id="5dc47-560">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="5dc47-561">Rückruf - aktualisiert ein Rückruf an, empfängt die Aufzeichnung des Status Umpacken.</span><span class="sxs-lookup"><span data-stu-id="5dc47-561">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="5dc47-562">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="5dc47-562">Return value</span></span>

<span data-ttu-id="5dc47-563">Die geladenen Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="5dc47-563">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="5dc47-564">Microsoft.PerceptionSimulation.StreamDataTypes</span><span class="sxs-lookup"><span data-stu-id="5dc47-564">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="5dc47-565">Beschreibt die verschiedenen Typen von datenstromdaten an.</span><span class="sxs-lookup"><span data-stu-id="5dc47-565">Describes the different types of stream data.</span></span>

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

<span data-ttu-id="5dc47-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span><span class="sxs-lookup"><span data-stu-id="5dc47-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="5dc47-567">Ein Sentinelwert verwendet, um keine Datentypen Stream anzugeben.</span><span class="sxs-lookup"><span data-stu-id="5dc47-567">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="5dc47-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span><span class="sxs-lookup"><span data-stu-id="5dc47-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="5dc47-569">Der Stream der Daten in Bezug auf die Position und Ausrichtung des Anfangswerts.</span><span class="sxs-lookup"><span data-stu-id="5dc47-569">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="5dc47-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span><span class="sxs-lookup"><span data-stu-id="5dc47-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="5dc47-571">Der Stream der Daten in Bezug auf die Position und Gesten Händen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-571">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="5dc47-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span><span class="sxs-lookup"><span data-stu-id="5dc47-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="5dc47-573">Der Stream der Daten in Bezug auf räumliche Zuordnung der Umgebung.</span><span class="sxs-lookup"><span data-stu-id="5dc47-573">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="5dc47-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span><span class="sxs-lookup"><span data-stu-id="5dc47-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="5dc47-575">Der Stream der Daten in Bezug auf die Kalibrierung des Geräts.</span><span class="sxs-lookup"><span data-stu-id="5dc47-575">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="5dc47-576">Kalibrierung Pakete werden nur von einem System im Remotemodus angenommen.</span><span class="sxs-lookup"><span data-stu-id="5dc47-576">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="5dc47-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span><span class="sxs-lookup"><span data-stu-id="5dc47-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="5dc47-578">Der Stream der Daten in Bezug auf die Umgebung des Geräts.</span><span class="sxs-lookup"><span data-stu-id="5dc47-578">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="5dc47-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span><span class="sxs-lookup"><span data-stu-id="5dc47-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="5dc47-580">Ein Sentinelwert verwendet, um alle aufgezeichneten Datentypen anzugeben.</span><span class="sxs-lookup"><span data-stu-id="5dc47-580">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="5dc47-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span><span class="sxs-lookup"><span data-stu-id="5dc47-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="5dc47-582">Ein Objekt, das Datenpakete aus einem Stream Simulation empfängt.</span><span class="sxs-lookup"><span data-stu-id="5dc47-582">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="5dc47-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived (Uint-Länge, Byte []-Paket)**</span><span class="sxs-lookup"><span data-stu-id="5dc47-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="5dc47-584">Empfängt ein einzelnes Paket, das intern typisierten und mit Versionsangabe versehen ist.</span><span class="sxs-lookup"><span data-stu-id="5dc47-584">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="5dc47-585">Parameter</span><span class="sxs-lookup"><span data-stu-id="5dc47-585">Parameters</span></span>
* <span data-ttu-id="5dc47-586">Länge - die Länge des Pakets.</span><span class="sxs-lookup"><span data-stu-id="5dc47-586">length - The length of the packet.</span></span>
* <span data-ttu-id="5dc47-587">Paket - die Daten des Pakets.</span><span class="sxs-lookup"><span data-stu-id="5dc47-587">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="5dc47-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span><span class="sxs-lookup"><span data-stu-id="5dc47-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="5dc47-589">Ein Objekt, das ISimulationStreamSink erstellt.</span><span class="sxs-lookup"><span data-stu-id="5dc47-589">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="5dc47-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span><span class="sxs-lookup"><span data-stu-id="5dc47-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="5dc47-591">Erstellt eine einzelne Instanz von ISimulationStreamSink an.</span><span class="sxs-lookup"><span data-stu-id="5dc47-591">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="5dc47-592">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="5dc47-592">Return value</span></span>

<span data-ttu-id="5dc47-593">Die erstellte Senke.</span><span class="sxs-lookup"><span data-stu-id="5dc47-593">The created sink.</span></span>
