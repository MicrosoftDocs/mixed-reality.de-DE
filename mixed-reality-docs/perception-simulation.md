---
title: Perception Simulation (Wahrnehmungssimulation)
description: Leitfaden zur Verwendung der Wahrnehmungs Simulations Bibliothek zum Automatisieren von simulierten Eingaben für immersive Anwendungen
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: Hololens, Simulation, Tests
ms.openlocfilehash: 701fd39490d87b70df9bd68cc99da6482d41b676
ms.sourcegitcommit: 6d9d01d53137435c787f247f095d5255581695fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/12/2020
ms.locfileid: "83228025"
---
# <a name="perception-simulation"></a><span data-ttu-id="ab19d-104">Perception Simulation (Wahrnehmungssimulation)</span><span class="sxs-lookup"><span data-stu-id="ab19d-104">Perception simulation</span></span>

<span data-ttu-id="ab19d-105">Möchten Sie einen automatisierten Test für Ihre APP erstellen?</span><span class="sxs-lookup"><span data-stu-id="ab19d-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="ab19d-106">Möchten Sie, dass Ihre Tests über Komponententests auf Komponentenebene hinausgehen und Ihre APP End-to-End wirklich ausführen?</span><span class="sxs-lookup"><span data-stu-id="ab19d-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="ab19d-107">Die Wahrnehmungs Simulation ist das, was Sie suchen.</span><span class="sxs-lookup"><span data-stu-id="ab19d-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="ab19d-108">Die Bibliothek für Wahrnehmungs Simulationen sendet Benutzer-und Welt Eingabedaten an Ihre APP, damit Sie Ihre Tests automatisieren können.</span><span class="sxs-lookup"><span data-stu-id="ab19d-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="ab19d-109">Beispielsweise können Sie die Eingabe eines Menschen simulieren, das eine bestimmte, wiederholbare Position und dann eine Geste oder einen Bewegungs Controller verwendet.</span><span class="sxs-lookup"><span data-stu-id="ab19d-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="ab19d-110">Die perception Simulation kann simulierte Eingaben wie diese an physische hololens, den hololens-Emulator (1. Generation), den hololens 2-Emulator oder einen PC mit installierter gemischtes Reality-Portal senden.</span><span class="sxs-lookup"><span data-stu-id="ab19d-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="ab19d-111">Die Wahrnehmungs Simulation umgeht die Live Sensoren auf einem Mixed Reality-Gerät und sendet simulierte Eingaben an Anwendungen, die auf dem Gerät ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="ab19d-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="ab19d-112">Anwendungen empfangen diese Eingabeereignisse über dieselben APIs, die Sie immer verwenden, und können den Unterschied zwischen der Ausführung mit echten Sensoren und der Ausführung mit der Wahrnehmungs Simulation nicht erkennen.</span><span class="sxs-lookup"><span data-stu-id="ab19d-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="ab19d-113">Die perception Simulation ist dieselbe Technologie, die von den hololens-Emulatoren verwendet wird, um simulierte Eingaben an den virtuellen Computer hololens zu senden.</span><span class="sxs-lookup"><span data-stu-id="ab19d-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="ab19d-114">Beginnen Sie zunächst mit der Verwendung von Simulation in Ihrem Code, indem Sie ein ipertionsimulationmanager-Objekt erstellen.</span><span class="sxs-lookup"><span data-stu-id="ab19d-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="ab19d-115">Aus diesem Objekt können Sie Befehle ausgeben, um die Eigenschaften eines simulierten "Menschen" zu steuern, einschließlich der Kopfposition, der Handposition und Gesten, und Sie können Bewegungs Controller aktivieren und bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="ab19d-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="ab19d-116">Einrichten eines Visual Studio-Projekts für die Wahrnehmungs Simulation</span><span class="sxs-lookup"><span data-stu-id="ab19d-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="ab19d-117">[Installieren Sie den hololens-Emulator](install-the-tools.md) auf dem Entwicklungs-PC.</span><span class="sxs-lookup"><span data-stu-id="ab19d-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="ab19d-118">Der Emulator enthält die Bibliotheken, die Sie für die Wahrnehmungs Simulation verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="ab19d-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="ab19d-119">Erstellen Sie ein neues Visual Studio c#-Desktop Projekt (ein Konsolen Projekt funktioniert hervorragend für den Einstieg).</span><span class="sxs-lookup"><span data-stu-id="ab19d-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="ab19d-120">Fügen Sie dem Projekt die folgenden Binärdateien als Verweise hinzu (Project->Add->Reference...). Sie finden Sie unter% Program Files (x86)% \ Microsoft XDE \\ (Version), z. b. **% Program Files (x86)% \ Microsoft XDE \\ 10.0.18362.0** für den hololens 2-Emulator.</span><span class="sxs-lookup"><span data-stu-id="ab19d-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="ab19d-121">(Hinweis: Obwohl die Binärdateien Teil des hololens 2-Emulators sind, funktionieren Sie auch für Windows Mixed Reality auf dem Desktop.) ein.</span><span class="sxs-lookup"><span data-stu-id="ab19d-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="ab19d-122">"Perceptionsimulationmanager. Interop. dll": verwalteter c#-Wrapper für die Wahrnehmungs Simulation.</span><span class="sxs-lookup"><span data-stu-id="ab19d-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="ab19d-123">b.</span><span class="sxs-lookup"><span data-stu-id="ab19d-123">b.</span></span> <span data-ttu-id="ab19d-124">Perzeptionsimulationrest. dll-Bibliothek zum Einrichten eines websocketkommunikationskanals für die hololens oder den Emulator.</span><span class="sxs-lookup"><span data-stu-id="ab19d-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="ab19d-125">c.</span><span class="sxs-lookup"><span data-stu-id="ab19d-125">c.</span></span> <span data-ttu-id="ab19d-126">Simulationstream. Interop. dll: freigegebene Typen für die Simulation.</span><span class="sxs-lookup"><span data-stu-id="ab19d-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="ab19d-127">Fügen Sie die-Implementierungs Binärdatei "perceptionsimulationmanager. dll" zu Ihrem Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="ab19d-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="ab19d-128">Fügen Sie Sie zunächst als Binärdatei zum Projekt hinzu (Projekt >Add->vorhandenes Element...). Speichern Sie Sie als Link, damit Sie nicht in Ihren Projekt Quellordner kopiert wird.</span><span class="sxs-lookup"><span data-stu-id="ab19d-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="ab19d-129">![Fügen Sie dem Projekt die Datei "perceptionsimulationmanager. dll" als Link ](images/saveaslink.png) b hinzu.</span><span class="sxs-lookup"><span data-stu-id="ab19d-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="ab19d-130">Stellen Sie dann sicher, dass Sie beim Build in den Ausgabeordner kopiert werden.</span><span class="sxs-lookup"><span data-stu-id="ab19d-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="ab19d-131">Dies befindet sich auf dem Eigenschaften Blatt für die Binärdatei.</span><span class="sxs-lookup"><span data-stu-id="ab19d-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="ab19d-132">![Markieren Sie "perceptionsimulationmanager. dll", um Sie in das Ausgabeverzeichnis zu kopieren](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="ab19d-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="ab19d-133">Legen Sie die Aktive Projektmappenplattform auf x64 fest.</span><span class="sxs-lookup"><span data-stu-id="ab19d-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="ab19d-134">(Verwenden Sie die Configuration Manager, um einen Platt Form Eintrag für x64 zu erstellen, wenn noch keiner vorhanden ist.)</span><span class="sxs-lookup"><span data-stu-id="ab19d-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="ab19d-135">Erstellen eines ipertionsimulation-Manager-Objekts</span><span class="sxs-lookup"><span data-stu-id="ab19d-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="ab19d-136">Um die Simulation zu steuern, geben Sie Aktualisierungen an Objekten aus, die von einem ipertionsimulationmanager-Objekt abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="ab19d-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="ab19d-137">Der erste Schritt besteht darin, dieses Objekt zu erhalten und es mit Ihrem Zielgerät oder Emulator zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="ab19d-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="ab19d-138">Klicken Sie in der [Symbolleiste](using-the-hololens-emulator.md) auf die Schaltfläche Geräte Portal, um die IP-Adresse des Emulators zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="ab19d-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="ab19d-139">![Symbol zum Öffnen des Geräte Portals ](images/emulator-deviceportal.png) **Öffnen Sie das Geräte Portal**: Öffnen Sie das Windows-Geräte Portal für das hololens-Betriebssystem im Emulator.</span><span class="sxs-lookup"><span data-stu-id="ab19d-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="ab19d-140">Für Windows Mixed Reality kann dies in der App "Einstellungen" unter "Aktualisieren der & Sicherheit" und dann "für Entwickler" im Abschnitt "Connect using:" unter "Enable Device Portal" abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="ab19d-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="ab19d-141">Achten Sie darauf, dass Sie die IP-Adresse und den Port beachten.</span><span class="sxs-lookup"><span data-stu-id="ab19d-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="ab19d-142">Zuerst rufen Sie restsimulationstreamsink. Create auf, um ein restsimulationstreamsink-Objekt abzurufen.</span><span class="sxs-lookup"><span data-stu-id="ab19d-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="ab19d-143">Dies ist das Zielgerät oder der Emulator, das Sie über eine HTTP-Verbindung steuern werden.</span><span class="sxs-lookup"><span data-stu-id="ab19d-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="ab19d-144">Ihre Befehle werden an das [Windows-Geräte Portal](using-the-windows-device-portal.md) , das auf dem Gerät oder Emulator ausgeführt wird, weitergeleitet und verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="ab19d-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="ab19d-145">Die vier Parameter, die Sie zum Erstellen eines Objekts benötigen, sind:</span><span class="sxs-lookup"><span data-stu-id="ab19d-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="ab19d-146">URI-URI: IP-Adresse des Zielgeräts (z. b. " https://123.123.123.123 " oder " https://123.123.123.123:50080 ")</span><span class="sxs-lookup"><span data-stu-id="ab19d-146">Uri uri - IP address of the target device (e.g., "https://123.123.123.123" or "https://123.123.123.123:50080")</span></span>
* <span data-ttu-id="ab19d-147">System .net. NetworkCredential-Anmelde Informationen: Benutzername/Kennwort für die Verbindung mit dem [Windows-Geräte Portal](using-the-windows-device-portal.md) auf dem Zielgerät oder Emulator.</span><span class="sxs-lookup"><span data-stu-id="ab19d-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="ab19d-148">Wenn Sie eine Verbindung mit dem Emulator über seine lokale Adresse herstellen (z. b. 168.*.*. \*) auf demselben PC werden alle Anmelde Informationen akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="ab19d-148">If you are connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="ab19d-149">bool normal: true für normale Priorität, false für niedrige Priorität.</span><span class="sxs-lookup"><span data-stu-id="ab19d-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="ab19d-150">In der Regel sollten Sie diese Einstellung für Testszenarien auf *true* festlegen, sodass der Test die Kontrolle übernehmen kann.</span><span class="sxs-lookup"><span data-stu-id="ab19d-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="ab19d-151">Der Emulator und die Windows Mixed Reality-Simulation verwenden Verbindungen mit niedriger Priorität.</span><span class="sxs-lookup"><span data-stu-id="ab19d-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="ab19d-152">Wenn Ihr Test auch eine Verbindung mit niedriger Priorität verwendet, wird die zuletzt festgelegte Verbindung gesteuert.</span><span class="sxs-lookup"><span data-stu-id="ab19d-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="ab19d-153">System. Threading. CancellationToken Token-Token, um den asynchronen Vorgang abzubrechen.</span><span class="sxs-lookup"><span data-stu-id="ab19d-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="ab19d-154">Zweitens erstellen Sie ipertionsimulationmanager.</span><span class="sxs-lookup"><span data-stu-id="ab19d-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="ab19d-155">Dies ist das Objekt, das Sie verwenden, um die Simulation zu steuern.</span><span class="sxs-lookup"><span data-stu-id="ab19d-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="ab19d-156">Beachten Sie, dass dies auch in einer Async-Methode erfolgen muss.</span><span class="sxs-lookup"><span data-stu-id="ab19d-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="ab19d-157">Steuern des simulierten Menschen</span><span class="sxs-lookup"><span data-stu-id="ab19d-157">Control the simulated Human</span></span>

<span data-ttu-id="ab19d-158">Ein ipertionsimulationmanager verfügt über eine menschliche Eigenschaft, die ein isimulatedhuman-Objekt zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="ab19d-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="ab19d-159">Um den simulierten Menschen zu steuern, führen Sie Vorgänge für dieses Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="ab19d-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="ab19d-160">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="ab19d-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="ab19d-161">Einfache c#-Beispiel Konsolenanwendung</span><span class="sxs-lookup"><span data-stu-id="ab19d-161">Basic Sample C# console application</span></span>

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
                        new Uri("https://169.254.227.115"),
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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="ab19d-162">Erweiterte c#-Beispiel Konsolenanwendung</span><span class="sxs-lookup"><span data-stu-id="ab19d-162">Extended Sample C# console application</span></span>

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
                        new Uri("https://169.254.227.115"),
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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="ab19d-163">Hinweis auf 6-DOF-Controllern</span><span class="sxs-lookup"><span data-stu-id="ab19d-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="ab19d-164">Vor dem Aufrufen von Eigenschaften für Methoden auf einem simulierten 6-DOF-Controller müssen Sie den Controller aktivieren.</span><span class="sxs-lookup"><span data-stu-id="ab19d-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="ab19d-165">Wenn dies nicht der Fall ist, wird eine Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="ab19d-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="ab19d-166">Ab dem Windows 10-Update von Mai 2019 können simulierte 6-DOF-Controller installiert und aktiviert werden, indem die Status-Eigenschaft für das isimulatedsixdofcontroller-Objekt auf simulatedsixdofcontrollerstatus. Active festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="ab19d-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="ab19d-167">Beim Windows 10-Update vom Oktober 2018 und früher müssen Sie zuerst einen simulierten 6-DOF-Controller separat installieren, indem Sie das Tool "perceptionsimulationdevice" aufrufen, das sich im Ordner "\Windows\System32" befindet.</span><span class="sxs-lookup"><span data-stu-id="ab19d-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="ab19d-168">Die Verwendung dieses Tools ist wie folgt:</span><span class="sxs-lookup"><span data-stu-id="ab19d-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="ab19d-169">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="ab19d-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="ab19d-170">Folgende Aktionen werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="ab19d-170">Supported actions are:</span></span>
* <span data-ttu-id="ab19d-171">i = Installation</span><span class="sxs-lookup"><span data-stu-id="ab19d-171">i = install</span></span>
* <span data-ttu-id="ab19d-172">q = Abfrage</span><span class="sxs-lookup"><span data-stu-id="ab19d-172">q = query</span></span>
* <span data-ttu-id="ab19d-173">r = entfernen</span><span class="sxs-lookup"><span data-stu-id="ab19d-173">r = remove</span></span>

<span data-ttu-id="ab19d-174">Unterstützte Instanzen:</span><span class="sxs-lookup"><span data-stu-id="ab19d-174">Supported instances are:</span></span>
* <span data-ttu-id="ab19d-175">1 = der linke 6-DOF-Controller</span><span class="sxs-lookup"><span data-stu-id="ab19d-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="ab19d-176">2 = der Rechte 6-DOF-Controller</span><span class="sxs-lookup"><span data-stu-id="ab19d-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="ab19d-177">Der Exitcode des Prozesses gibt einen Erfolg (ein NULL-Rückgabewert) oder einen Fehler (ein Rückgabewert ungleich null) an.</span><span class="sxs-lookup"><span data-stu-id="ab19d-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="ab19d-178">Wenn Sie die Aktion "q" verwenden, um abzufragen, ob ein Controller installiert ist oder nicht, ist der Rückgabewert 0 (null), wenn der Controller nicht bereits installiert ist, oder ein (1), wenn der Controller installiert ist.</span><span class="sxs-lookup"><span data-stu-id="ab19d-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="ab19d-179">Wenn Sie einen Controller am Windows 10-Update vom Oktober 2018 oder früher entfernen, legen Sie seinen Status zuerst über die API auf OFF fest, und nennen Sie dann das Tool "perzeptionsimulationdevice".</span><span class="sxs-lookup"><span data-stu-id="ab19d-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="ab19d-180">Beachten Sie, dass dieses Tool als Administrator ausgeführt werden muss.</span><span class="sxs-lookup"><span data-stu-id="ab19d-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="ab19d-181">API-Referenz</span><span class="sxs-lookup"><span data-stu-id="ab19d-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="ab19d-182">Microsoft. perceptionsimulation. simulateddebug Type</span><span class="sxs-lookup"><span data-stu-id="ab19d-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="ab19d-183">Beschreibt einen simulierten Gerätetyp.</span><span class="sxs-lookup"><span data-stu-id="ab19d-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="ab19d-184">**Microsoft. perceptionsimulation. simulatedtovicetype. Reference**</span><span class="sxs-lookup"><span data-stu-id="ab19d-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="ab19d-185">Ein fiktives Referenzgerät, der Standardwert für "perceptionsimulationmanager"</span><span class="sxs-lookup"><span data-stu-id="ab19d-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="ab19d-186">Microsoft. perceptionsimulation. headtrackermode</span><span class="sxs-lookup"><span data-stu-id="ab19d-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="ab19d-187">Beschreibt einen Head Tracker-Modus.</span><span class="sxs-lookup"><span data-stu-id="ab19d-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="ab19d-188">**Microsoft. perceptionsimulation. headtrackermode. Default**</span><span class="sxs-lookup"><span data-stu-id="ab19d-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="ab19d-189">Standard Head-Nachverfolgung.</span><span class="sxs-lookup"><span data-stu-id="ab19d-189">Default Head Tracking.</span></span> <span data-ttu-id="ab19d-190">Dies bedeutet, dass das System basierend auf den Lauf Zeit Bedingungen den besten Head-nach Verfolgungs Modus auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="ab19d-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="ab19d-191">**Microsoft. perceptionsimulation. headtrackermode. Orientation**</span><span class="sxs-lookup"><span data-stu-id="ab19d-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="ab19d-192">Nur Ausrichtung Head Tracking.</span><span class="sxs-lookup"><span data-stu-id="ab19d-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="ab19d-193">Dies bedeutet, dass die nach verfolgte Position möglicherweise nicht zuverlässig ist und einige Funktionen, die von der Head-Position abhängig sind, möglicherweise nicht verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="ab19d-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="ab19d-194">**Microsoft. perceptionsimulation. headtrackermode. Position**</span><span class="sxs-lookup"><span data-stu-id="ab19d-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="ab19d-195">Nachverfolgung von positionellen Köpfen.</span><span class="sxs-lookup"><span data-stu-id="ab19d-195">Positional Head Tracking.</span></span> <span data-ttu-id="ab19d-196">Dies bedeutet, dass die Position und Ausrichtung der überwachten Kopfzeile zuverlässig sind.</span><span class="sxs-lookup"><span data-stu-id="ab19d-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="ab19d-197">Microsoft. perceptionsimulation. simulatedgesten</span><span class="sxs-lookup"><span data-stu-id="ab19d-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="ab19d-198">Beschreibt eine simulierte Geste</span><span class="sxs-lookup"><span data-stu-id="ab19d-198">Describes a simulated gesture</span></span>

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

<span data-ttu-id="ab19d-199">**Microsoft. perceptionsimulation. simulatedgesten. None**</span><span class="sxs-lookup"><span data-stu-id="ab19d-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="ab19d-200">Ein Sentinelwert, mit dem keine Gesten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ab19d-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="ab19d-201">**Microsoft. perceptionsimulation. simulatedgesten. fingerpressed**</span><span class="sxs-lookup"><span data-stu-id="ab19d-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="ab19d-202">Eine gedrückte Stift Bewegung.</span><span class="sxs-lookup"><span data-stu-id="ab19d-202">A finger pressed gesture.</span></span>

<span data-ttu-id="ab19d-203">**Microsoft. perceptionsimulation. simulatedgesten. fingerreleased**</span><span class="sxs-lookup"><span data-stu-id="ab19d-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="ab19d-204">Eine von Fingern freigegebene Geste.</span><span class="sxs-lookup"><span data-stu-id="ab19d-204">A finger released gesture.</span></span>

<span data-ttu-id="ab19d-205">**Microsoft. perceptionsimulation. simulatedgesten. Home**</span><span class="sxs-lookup"><span data-stu-id="ab19d-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="ab19d-206">Die "Home/System"-Geste.</span><span class="sxs-lookup"><span data-stu-id="ab19d-206">The home/system gesture.</span></span>

<span data-ttu-id="ab19d-207">**Microsoft. perceptionsimulation. simulatedgesten. Max**</span><span class="sxs-lookup"><span data-stu-id="ab19d-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="ab19d-208">Die maximale gültige Geste.</span><span class="sxs-lookup"><span data-stu-id="ab19d-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="ab19d-209">Microsoft. perceptionsimulation. simulatedsixdofcontrollerstatus</span><span class="sxs-lookup"><span data-stu-id="ab19d-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="ab19d-210">Die möglichen Zustände eines simulierten 6-DOF-Controllers.</span><span class="sxs-lookup"><span data-stu-id="ab19d-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="ab19d-211">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerstatus. Off**</span><span class="sxs-lookup"><span data-stu-id="ab19d-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="ab19d-212">Der 6-DOF-Controller ist ausgeschaltet.</span><span class="sxs-lookup"><span data-stu-id="ab19d-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="ab19d-213">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerstatus. Active**</span><span class="sxs-lookup"><span data-stu-id="ab19d-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="ab19d-214">Der 6-DOF-Controller ist eingeschaltet und wird nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="ab19d-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="ab19d-215">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerstatus. trackinglost**</span><span class="sxs-lookup"><span data-stu-id="ab19d-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="ab19d-216">Der 6-DOF-Controller ist eingeschaltet, kann aber nicht nachverfolgt werden.</span><span class="sxs-lookup"><span data-stu-id="ab19d-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="ab19d-217">Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton</span><span class="sxs-lookup"><span data-stu-id="ab19d-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="ab19d-218">Die unterstützten Schaltflächen auf einem simulierten 6-DOF-Controller.</span><span class="sxs-lookup"><span data-stu-id="ab19d-218">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="ab19d-219">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. None**</span><span class="sxs-lookup"><span data-stu-id="ab19d-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="ab19d-220">Ein Sentinelwert, mit dem keine Schaltflächen angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="ab19d-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="ab19d-221">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. Home**</span><span class="sxs-lookup"><span data-stu-id="ab19d-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="ab19d-222">Die Start Schaltfläche wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="ab19d-222">The Home button is pressed.</span></span>

<span data-ttu-id="ab19d-223">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. Menu**</span><span class="sxs-lookup"><span data-stu-id="ab19d-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="ab19d-224">Die Menü Schaltfläche wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="ab19d-224">The Menu button is pressed.</span></span>

<span data-ttu-id="ab19d-225">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. Grip**</span><span class="sxs-lookup"><span data-stu-id="ab19d-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="ab19d-226">Die Zieh Fläche wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="ab19d-226">The Grip button is pressed.</span></span>

<span data-ttu-id="ab19d-227">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. touchpadpress**</span><span class="sxs-lookup"><span data-stu-id="ab19d-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="ab19d-228">Der Touchpad ist gedrückt.</span><span class="sxs-lookup"><span data-stu-id="ab19d-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="ab19d-229">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. Select**</span><span class="sxs-lookup"><span data-stu-id="ab19d-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="ab19d-230">Die Schaltfläche auswählen wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="ab19d-230">The Select button is pressed.</span></span>

<span data-ttu-id="ab19d-231">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. touchpadtouch**</span><span class="sxs-lookup"><span data-stu-id="ab19d-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="ab19d-232">Das Touchpad ist berührt.</span><span class="sxs-lookup"><span data-stu-id="ab19d-232">The TouchPad is touched.</span></span>

<span data-ttu-id="ab19d-233">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. Thumbstick**</span><span class="sxs-lookup"><span data-stu-id="ab19d-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="ab19d-234">Der Finger Stick wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="ab19d-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="ab19d-235">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. Max**</span><span class="sxs-lookup"><span data-stu-id="ab19d-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="ab19d-236">Die maximale gültige Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="ab19d-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="ab19d-237">Microsoft. perceptionsimulation. simulatedeyescalibrationstate</span><span class="sxs-lookup"><span data-stu-id="ab19d-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="ab19d-238">Der Kalibrierungs Zustand der simulierten Augen</span><span class="sxs-lookup"><span data-stu-id="ab19d-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="ab19d-239">**Microsoft. perceptionsimulation. simulatedeyescalibrationstate. nicht verfügbar**</span><span class="sxs-lookup"><span data-stu-id="ab19d-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="ab19d-240">Die Augen-Kalibrierung ist nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ab19d-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="ab19d-241">**Microsoft. perceptionsimulation. simulatedeyescalibrationstate. Ready**</span><span class="sxs-lookup"><span data-stu-id="ab19d-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="ab19d-242">Die Augen wurden gekalibriert.</span><span class="sxs-lookup"><span data-stu-id="ab19d-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="ab19d-243">Dies ist der Standardwert.</span><span class="sxs-lookup"><span data-stu-id="ab19d-243">This is the default value.</span></span>

<span data-ttu-id="ab19d-244">**Microsoft. perceptionsimulation. simulatedeyescalibrationstate. konfiguriert**</span><span class="sxs-lookup"><span data-stu-id="ab19d-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="ab19d-245">Die Augen werden gerade gekalibriert.</span><span class="sxs-lookup"><span data-stu-id="ab19d-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="ab19d-246">**Microsoft. perceptionsimulation. simulatedeyescalibrationstate. usercalibrationbenötigte**</span><span class="sxs-lookup"><span data-stu-id="ab19d-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="ab19d-247">Die Augen müssen kalibriert werden.</span><span class="sxs-lookup"><span data-stu-id="ab19d-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="ab19d-248">Microsoft. perceptionsimulation. simulatedhandjointtrackingaccuracy</span><span class="sxs-lookup"><span data-stu-id="ab19d-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="ab19d-249">Die nach Verfolgungs Genauigkeit einer gemeinsamen Hand.</span><span class="sxs-lookup"><span data-stu-id="ab19d-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="ab19d-250">**Microsoft. perceptionsimulation. simulatedhandjointtrackingaccuracy. nicht verfügbar**</span><span class="sxs-lookup"><span data-stu-id="ab19d-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="ab19d-251">Das gemeinsame wird nicht nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="ab19d-251">The joint is not tracked.</span></span>

<span data-ttu-id="ab19d-252">**Microsoft. perceptionsimulation. simulatedhandjointtrackingaccuracy. ungefähre**</span><span class="sxs-lookup"><span data-stu-id="ab19d-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="ab19d-253">Die gemeinsame Position wird abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="ab19d-253">The joint position is inferred.</span></span>

<span data-ttu-id="ab19d-254">**Microsoft. perceptionsimulation. simulatedhandjointtrackingaccuracy. Visible**</span><span class="sxs-lookup"><span data-stu-id="ab19d-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="ab19d-255">Das gemeinsame ist vollständig nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="ab19d-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="ab19d-256">Microsoft. perceptionsimulation. simulatedhandpose</span><span class="sxs-lookup"><span data-stu-id="ab19d-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="ab19d-257">Die nach Verfolgungs Genauigkeit einer gemeinsamen Hand.</span><span class="sxs-lookup"><span data-stu-id="ab19d-257">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="ab19d-258">**Microsoft. perceptionsimulation. simulatedhandpose. Closed**</span><span class="sxs-lookup"><span data-stu-id="ab19d-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="ab19d-259">Die Fingergelenke der Hand werden so konfiguriert, dass Sie eine geschlossene Darstellung widerspiegeln.</span><span class="sxs-lookup"><span data-stu-id="ab19d-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="ab19d-260">**Microsoft. perceptionsimulation. simulatedhandpose. Open**</span><span class="sxs-lookup"><span data-stu-id="ab19d-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="ab19d-261">Die Fingergelenke der Hand werden so konfiguriert, dass Sie eine offene Pose widerspiegeln.</span><span class="sxs-lookup"><span data-stu-id="ab19d-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="ab19d-262">**Microsoft. perceptionsimulation. simulatedhandpose. Point**</span><span class="sxs-lookup"><span data-stu-id="ab19d-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="ab19d-263">Die Fingergelenke der Hand werden so konfiguriert, dass Sie eine Zeige Darstellung widerspiegeln.</span><span class="sxs-lookup"><span data-stu-id="ab19d-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="ab19d-264">**Microsoft. perceptionsimulation. simulatedhandpose. Pinch**</span><span class="sxs-lookup"><span data-stu-id="ab19d-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="ab19d-265">Die Fingergelenke der Hand werden so konfiguriert, dass Sie eine zusammendrücken-Pose widerspiegeln.</span><span class="sxs-lookup"><span data-stu-id="ab19d-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="ab19d-266">**Microsoft. perceptionsimulation. simulatedhandpose. Max**</span><span class="sxs-lookup"><span data-stu-id="ab19d-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="ab19d-267">Der maximale gültige Wert für simulatedhandpose.</span><span class="sxs-lookup"><span data-stu-id="ab19d-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="ab19d-268">Microsoft. perceptionsimulation. playbackstate</span><span class="sxs-lookup"><span data-stu-id="ab19d-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="ab19d-269">Beschreibt den Zustand einer Wiedergabe.</span><span class="sxs-lookup"><span data-stu-id="ab19d-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="ab19d-270">**Microsoft. perceptionsimulation. playbackstate. beendet**</span><span class="sxs-lookup"><span data-stu-id="ab19d-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="ab19d-271">Die Aufzeichnung ist zurzeit beendet und ist für die Wiedergabe bereit.</span><span class="sxs-lookup"><span data-stu-id="ab19d-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="ab19d-272">**Microsoft. perceptionsimulation. playbackstate. Play**</span><span class="sxs-lookup"><span data-stu-id="ab19d-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="ab19d-273">Die Aufzeichnung wird zurzeit wiedergegeben.</span><span class="sxs-lookup"><span data-stu-id="ab19d-273">The recording is currently playing.</span></span>

<span data-ttu-id="ab19d-274">**Microsoft. perceptionsimulation. playbackstate. angehalten**</span><span class="sxs-lookup"><span data-stu-id="ab19d-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="ab19d-275">Die Aufzeichnung ist derzeit angehalten.</span><span class="sxs-lookup"><span data-stu-id="ab19d-275">The recording is currently paused.</span></span>

<span data-ttu-id="ab19d-276">**Microsoft. perceptionsimulation. playbackstate. End**</span><span class="sxs-lookup"><span data-stu-id="ab19d-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="ab19d-277">Die Aufzeichnung hat das Ende erreicht.</span><span class="sxs-lookup"><span data-stu-id="ab19d-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="ab19d-278">Microsoft. perceptionsimulation. Vector3</span><span class="sxs-lookup"><span data-stu-id="ab19d-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="ab19d-279">Beschreibt einen 3-Komponenten Vektor, der einen Punkt oder einen Vektor im 3D-Raum beschreiben könnte.</span><span class="sxs-lookup"><span data-stu-id="ab19d-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="ab19d-280">**Microsoft. perceptionsimulation. Vector3. X**</span><span class="sxs-lookup"><span data-stu-id="ab19d-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="ab19d-281">Die X-Komponente des Vektors.</span><span class="sxs-lookup"><span data-stu-id="ab19d-281">The X component of the vector.</span></span>

<span data-ttu-id="ab19d-282">**Microsoft. perceptionsimulation. Vector3. Y**</span><span class="sxs-lookup"><span data-stu-id="ab19d-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="ab19d-283">Die Y-Komponente des Vektors.</span><span class="sxs-lookup"><span data-stu-id="ab19d-283">The Y component of the vector.</span></span>

<span data-ttu-id="ab19d-284">**Microsoft. perceptionsimulation. Vector3. Z**</span><span class="sxs-lookup"><span data-stu-id="ab19d-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="ab19d-285">Die Z-Komponente des Vektors.</span><span class="sxs-lookup"><span data-stu-id="ab19d-285">The Z component of the vector.</span></span>

<span data-ttu-id="ab19d-286">**Microsoft. perceptionsimulation. Vector3. #ctor (System. Single, System. Single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="ab19d-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="ab19d-287">Erstellen Sie eine neue Vector3.</span><span class="sxs-lookup"><span data-stu-id="ab19d-287">Construct a new Vector3.</span></span>

<span data-ttu-id="ab19d-288">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab19d-288">Parameters</span></span>
* <span data-ttu-id="ab19d-289">x: die x-Komponente des Vektors.</span><span class="sxs-lookup"><span data-stu-id="ab19d-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="ab19d-290">y: die y-Komponente des Vektors.</span><span class="sxs-lookup"><span data-stu-id="ab19d-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="ab19d-291">z-die z-Komponente des Vektors.</span><span class="sxs-lookup"><span data-stu-id="ab19d-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="ab19d-292">Microsoft. perceptionsimulation. Rotation3</span><span class="sxs-lookup"><span data-stu-id="ab19d-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="ab19d-293">Beschreibt eine 3-Komponenten Rotation.</span><span class="sxs-lookup"><span data-stu-id="ab19d-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="ab19d-294">**Microsoft. perceptionsimulation. Rotation3. Pitch**</span><span class="sxs-lookup"><span data-stu-id="ab19d-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="ab19d-295">Die Tonkomponente der Drehung um die X-Achse.</span><span class="sxs-lookup"><span data-stu-id="ab19d-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="ab19d-296">**Microsoft. perceptionsimulation. Rotation3. Yaw**</span><span class="sxs-lookup"><span data-stu-id="ab19d-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="ab19d-297">Die GW-Komponente der Drehung, direkt um die Y-Achse.</span><span class="sxs-lookup"><span data-stu-id="ab19d-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="ab19d-298">**Microsoft. perceptionsimulation. Rotation3. Roll**</span><span class="sxs-lookup"><span data-stu-id="ab19d-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="ab19d-299">Die rollenkomponente der Drehung, direkt um die Z-Achse.</span><span class="sxs-lookup"><span data-stu-id="ab19d-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="ab19d-300">**Microsoft. perceptionsimulation. Rotation3. #ctor (System. Single, System. Single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="ab19d-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="ab19d-301">Erstellen Sie eine neue Rotation3.</span><span class="sxs-lookup"><span data-stu-id="ab19d-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="ab19d-302">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab19d-302">Parameters</span></span>
* <span data-ttu-id="ab19d-303">Pitch: die Tonkomponente der Drehung.</span><span class="sxs-lookup"><span data-stu-id="ab19d-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="ab19d-304">Yaw-die Yaw-Komponente der Drehung.</span><span class="sxs-lookup"><span data-stu-id="ab19d-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="ab19d-305">Rollup der rollforwardkomponente der Drehung.</span><span class="sxs-lookup"><span data-stu-id="ab19d-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="ab19d-306">Microsoft. perceptionsimulation. simulatedhandjointconfiguration</span><span class="sxs-lookup"><span data-stu-id="ab19d-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="ab19d-307">Beschreibt die Konfiguration einer zusammenhängenden in einer simulierten Hand.</span><span class="sxs-lookup"><span data-stu-id="ab19d-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="ab19d-308">**Microsoft. perceptionsimulation. simulatedhandjointconfiguration. Position**</span><span class="sxs-lookup"><span data-stu-id="ab19d-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="ab19d-309">Die Position des gemeinsamen.</span><span class="sxs-lookup"><span data-stu-id="ab19d-309">The position of the joint.</span></span>

<span data-ttu-id="ab19d-310">**Microsoft. perceptionsimulation. simulatedhandjointconfiguration. Rotation**</span><span class="sxs-lookup"><span data-stu-id="ab19d-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="ab19d-311">Die Drehung der gemeinsam.</span><span class="sxs-lookup"><span data-stu-id="ab19d-311">The rotation of the joint.</span></span>

<span data-ttu-id="ab19d-312">**Microsoft. perceptionsimulation. simulatedhandjointconfiguration. trackingaccuracy**</span><span class="sxs-lookup"><span data-stu-id="ab19d-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="ab19d-313">Die nach Verfolgungs Genauigkeit der gemeinsamen.</span><span class="sxs-lookup"><span data-stu-id="ab19d-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="ab19d-314">Microsoft. perceptionsimulation. Frustum</span><span class="sxs-lookup"><span data-stu-id="ab19d-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="ab19d-315">Beschreibt eine Ansicht, wie Sie in der Regel von einer Kamera verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ab19d-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="ab19d-316">**Microsoft. perceptionsimulation. Frustum. Near**</span><span class="sxs-lookup"><span data-stu-id="ab19d-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="ab19d-317">Der Mindestabstand, der in der Frustum-Klasse enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="ab19d-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="ab19d-318">**Microsoft. perceptionsimulation. Frustum. Far**</span><span class="sxs-lookup"><span data-stu-id="ab19d-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="ab19d-319">Der maximale Abstand, der in der Frustum-Klasse enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="ab19d-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="ab19d-320">**Microsoft. perceptionsimulation. Frustum. fieldofiview**</span><span class="sxs-lookup"><span data-stu-id="ab19d-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="ab19d-321">Das horizontale Feld der Ansicht des Frustum im Bogenmaße (kleiner als PI).</span><span class="sxs-lookup"><span data-stu-id="ab19d-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="ab19d-322">**Microsoft. perceptionsimulation. Frustum. AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="ab19d-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="ab19d-323">Das Verhältnis des horizontalen Sicht Felds zum vertikalen Sichtfeld.</span><span class="sxs-lookup"><span data-stu-id="ab19d-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a><span data-ttu-id="ab19d-324">Microsoft. perceptionsimulation. simulateddisplayconfiguration</span><span class="sxs-lookup"><span data-stu-id="ab19d-324">Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration</span></span>

<span data-ttu-id="ab19d-325">Beschreibt die Konfiguration der Anzeige des simulierten Headsets.</span><span class="sxs-lookup"><span data-stu-id="ab19d-325">Describes the configuration of the simulated headset's display.</span></span>

```
public struct SimulatedDisplayConfiguration
{
    public Vector3 LeftEyePosition;
    public Rotation3 LeftEyeRotation;
    public Vector3 RightEyePosition;
    public Rotation3 RightEyeRotation;
    public float Ipd;
    public bool ApplyEyeTransforms;
    public bool ApplyIpd;
}
```

<span data-ttu-id="ab19d-326">**Microsoft. perceptionsimulation. simulateddisplayconfiguration. lefteyeposition**</span><span class="sxs-lookup"><span data-stu-id="ab19d-326">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyePosition**</span></span>

<span data-ttu-id="ab19d-327">Die Transformation von der Mitte des Kopfes nach Links für das Stereo Rendering.</span><span class="sxs-lookup"><span data-stu-id="ab19d-327">The transform from the center of the head to the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="ab19d-328">**Microsoft. perceptionsimulation. simulateddisplayconfiguration. lefteyerotation**</span><span class="sxs-lookup"><span data-stu-id="ab19d-328">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyeRotation**</span></span>

<span data-ttu-id="ab19d-329">Die Drehung der linken Seite für das Stereo Rendering.</span><span class="sxs-lookup"><span data-stu-id="ab19d-329">The rotation of the left eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="ab19d-330">**Microsoft. perceptionsimulation. simulateddisplayconfiguration. rechtschaffyeposition**</span><span class="sxs-lookup"><span data-stu-id="ab19d-330">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyePosition**</span></span>

<span data-ttu-id="ab19d-331">Die Transformation von der Mitte des Kopfes zum rechten Auge für das Stereo Rendering.</span><span class="sxs-lookup"><span data-stu-id="ab19d-331">The transform from the center of the head to the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="ab19d-332">**Microsoft. perceptionsimulation. simulateddisplayconfiguration. rechtschafferiotation**</span><span class="sxs-lookup"><span data-stu-id="ab19d-332">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyeRotation**</span></span>

<span data-ttu-id="ab19d-333">Die Drehung des rechten Auges für das Stereo Rendering.</span><span class="sxs-lookup"><span data-stu-id="ab19d-333">The rotation of the right eye for purposes of stereo rendering.</span></span>

<span data-ttu-id="ab19d-334">**Microsoft. perceptionsimulation. simulateddisplayconfiguration. IPD**</span><span class="sxs-lookup"><span data-stu-id="ab19d-334">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.Ipd**</span></span>

<span data-ttu-id="ab19d-335">Der IPD-Wert, der vom System für das Stereo Rendering gemeldet wird.</span><span class="sxs-lookup"><span data-stu-id="ab19d-335">The Ipd value reported by the system for purposes of stereo rendering.</span></span>

<span data-ttu-id="ab19d-336">**Microsoft. perceptionsimulation. simulateddisplayconfiguration. applyeyetransformationen**</span><span class="sxs-lookup"><span data-stu-id="ab19d-336">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyEyeTransforms**</span></span>

<span data-ttu-id="ab19d-337">Ob die für "Left" und "Right Eye" bereitgestellten Werte als gültig eingestuft werden und auf das laufende System angewendet werden sollen.</span><span class="sxs-lookup"><span data-stu-id="ab19d-337">Whether or not the values provided for left and right eye transforms should be considered valid and applied to the running system.</span></span>

<span data-ttu-id="ab19d-338">**Microsoft. perceptionsimulation. simulateddisplayconfiguration. applyipd**</span><span class="sxs-lookup"><span data-stu-id="ab19d-338">**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyIpd**</span></span>

<span data-ttu-id="ab19d-339">Gibt an, ob der für IPD angegebene Wert gültig und auf das laufende System angewendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="ab19d-339">Whether or not the value provided for Ipd should be considered valid and applied to the running system.</span></span>


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="ab19d-340">Microsoft. perceptionsimulation. ipertionsimulationmanager</span><span class="sxs-lookup"><span data-stu-id="ab19d-340">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="ab19d-341">Der Stamm zum Erstellen der zum Steuern eines Geräts verwendeten Pakete.</span><span class="sxs-lookup"><span data-stu-id="ab19d-341">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="ab19d-342">**Microsoft. perceptionsimulation. ipertionsimulationmanager. Device**</span><span class="sxs-lookup"><span data-stu-id="ab19d-342">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="ab19d-343">Rufen Sie das simulierte Geräte Objekt ab, das den simulierten Menschen und die simulierte Welt interpretiert.</span><span class="sxs-lookup"><span data-stu-id="ab19d-343">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="ab19d-344">**Microsoft. perceptionsimulation. ipertionsimulationmanager. Human**</span><span class="sxs-lookup"><span data-stu-id="ab19d-344">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="ab19d-345">Rufen Sie das-Objekt ab, das den simulierten Menschen steuert.</span><span class="sxs-lookup"><span data-stu-id="ab19d-345">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="ab19d-346">**Microsoft. perceptionsimulation. ipertionsimulationmanager. Reset**</span><span class="sxs-lookup"><span data-stu-id="ab19d-346">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="ab19d-347">Setzt die Simulation auf ihren Standardzustand zurück.</span><span class="sxs-lookup"><span data-stu-id="ab19d-347">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="ab19d-348">Microsoft. perceptionsimulation. isimulateddevice</span><span class="sxs-lookup"><span data-stu-id="ab19d-348">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="ab19d-349">Schnittstelle, die das Gerät beschreibt, das die simulierte Welt und den simulierten Menschen interpretiert</span><span class="sxs-lookup"><span data-stu-id="ab19d-349">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="ab19d-350">**Microsoft. perceptionsimulation. isimulateddevice. headtracker**</span><span class="sxs-lookup"><span data-stu-id="ab19d-350">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="ab19d-351">Rufen Sie den Head Tracker vom simulierten Gerät ab.</span><span class="sxs-lookup"><span data-stu-id="ab19d-351">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="ab19d-352">**Microsoft. perceptionsimulation. isimulateddevice. Handtracker**</span><span class="sxs-lookup"><span data-stu-id="ab19d-352">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="ab19d-353">Rufen Sie die Hand Verfolgung vom simulierten Gerät ab.</span><span class="sxs-lookup"><span data-stu-id="ab19d-353">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="ab19d-354">**Microsoft. perceptionsimulation. isimulateddevice. setsimulatedde vicetype (Microsoft. perceptionsimulation. simulateddebug Type)**</span><span class="sxs-lookup"><span data-stu-id="ab19d-354">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="ab19d-355">Legen Sie die Eigenschaften des simulierten Geräts so fest, dass Sie dem angegebenen Gerätetyp entsprechen.</span><span class="sxs-lookup"><span data-stu-id="ab19d-355">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="ab19d-356">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab19d-356">Parameters</span></span>
* <span data-ttu-id="ab19d-357">Type: der neue Typ des simulierten Geräts</span><span class="sxs-lookup"><span data-stu-id="ab19d-357">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice2"></a><span data-ttu-id="ab19d-358">Microsoft. perceptionsimulation. ISimulatedDevice2</span><span class="sxs-lookup"><span data-stu-id="ab19d-358">Microsoft.PerceptionSimulation.ISimulatedDevice2</span></span>

<span data-ttu-id="ab19d-359">Wenn Sie isimulateddevice in ISimulatedDevice2 umwandeln, sind zusätzliche Eigenschaften verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ab19d-359">Additional properties are available by casting the ISimulatedDevice to ISimulatedDevice2</span></span>

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

<span data-ttu-id="ab19d-360">**Microsoft. perceptionsimulation. ISimulatedDevice2. isuserpresent**</span><span class="sxs-lookup"><span data-stu-id="ab19d-360">**Microsoft.PerceptionSimulation.ISimulatedDevice2.IsUserPresent**</span></span>

<span data-ttu-id="ab19d-361">Ruft ab oder legt fest, ob der simulierte Mensch das Headset aktiv durchläuft.</span><span class="sxs-lookup"><span data-stu-id="ab19d-361">Retrieve or set whether or not the simulated human is actively wearing the headset.</span></span>

<span data-ttu-id="ab19d-362">**Microsoft. perceptionsimulation. ISimulatedDevice2. displayconfiguration**</span><span class="sxs-lookup"><span data-stu-id="ab19d-362">**Microsoft.PerceptionSimulation.ISimulatedDevice2.DisplayConfiguration**</span></span>

<span data-ttu-id="ab19d-363">Ruft die Eigenschaften der simulierten Anzeige ab oder legt Sie fest.</span><span class="sxs-lookup"><span data-stu-id="ab19d-363">Retrieve or set the properties of the simulated display.</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="ab19d-364">Microsoft. perceptionsimulation. isimulatedheadtracker</span><span class="sxs-lookup"><span data-stu-id="ab19d-364">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="ab19d-365">Schnittstelle, die den Teil des simulierten Geräts beschreibt, der die Kopfzeile des simulierten Menschen nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="ab19d-365">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="ab19d-366">**Microsoft. perceptionsimulation. isimulatedheadtracker. headtrackermode**</span><span class="sxs-lookup"><span data-stu-id="ab19d-366">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="ab19d-367">Ruft den aktuellen Head-Tracker-Modus ab und legt diesen fest.</span><span class="sxs-lookup"><span data-stu-id="ab19d-367">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="ab19d-368">Microsoft. perceptionsimulation. isimulatedhandtracker</span><span class="sxs-lookup"><span data-stu-id="ab19d-368">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="ab19d-369">Schnittstelle, die den Teil des simulierten Geräts beschreibt, der die Hände des simulierten Menschen nachverfolgt</span><span class="sxs-lookup"><span data-stu-id="ab19d-369">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="ab19d-370">**Microsoft. perceptionsimulation. isimulatedhandtracker. worldposition**</span><span class="sxs-lookup"><span data-stu-id="ab19d-370">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="ab19d-371">Rufen Sie die Position des Knotens mit der Welt in Meter ab.</span><span class="sxs-lookup"><span data-stu-id="ab19d-371">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="ab19d-372">**Microsoft. perceptionsimulation. isimulatedhandtracker. Position**</span><span class="sxs-lookup"><span data-stu-id="ab19d-372">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="ab19d-373">Ruft die Position der simulierten Hand Tracker relativ zum Mittelpunkt des Kopfes ab und legt diese fest.</span><span class="sxs-lookup"><span data-stu-id="ab19d-373">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="ab19d-374">**Microsoft. perceptionsimulation. isimulatedhandtracker. Pitch**</span><span class="sxs-lookup"><span data-stu-id="ab19d-374">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="ab19d-375">Abrufen und Festlegen der nach unten gerichteten Menge der simulierten Hand Tracker.</span><span class="sxs-lookup"><span data-stu-id="ab19d-375">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="ab19d-376">**Microsoft. perceptionsimulation. isimulatedhandtracker. frustumignored**</span><span class="sxs-lookup"><span data-stu-id="ab19d-376">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="ab19d-377">Rufen Sie ab, und legen Sie fest, ob der Wert der simulierten Hand Verfolgung ignoriert wird.</span><span class="sxs-lookup"><span data-stu-id="ab19d-377">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="ab19d-378">Wenn Sie ignoriert werden, sind beide Hände immer sichtbar.</span><span class="sxs-lookup"><span data-stu-id="ab19d-378">When ignored, both hands are always visible.</span></span> <span data-ttu-id="ab19d-379">Wenn Sie nicht ignoriert werden (die Standardeinstellung), sind Sie nur sichtbar, wenn Sie sich innerhalb der Frustum-Klasse des Hand Trackers befinden.</span><span class="sxs-lookup"><span data-stu-id="ab19d-379">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="ab19d-380">**Microsoft. perceptionsimulation. isimulatedhandtracker. Frustum**</span><span class="sxs-lookup"><span data-stu-id="ab19d-380">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="ab19d-381">Dient zum Abrufen und Festlegen der Frustum-Eigenschaften, mit denen bestimmt wird, ob die Hände für die simulierte Hand Verfolgung sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="ab19d-381">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="ab19d-382">Microsoft. perceptionsimulation. isimulatedhuman</span><span class="sxs-lookup"><span data-stu-id="ab19d-382">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="ab19d-383">Oberfläche der obersten Ebene zum Steuern des simulierten Menschen.</span><span class="sxs-lookup"><span data-stu-id="ab19d-383">Top level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="ab19d-384">**Microsoft. perceptionsimulation. isimulatedhuman. worldposition**</span><span class="sxs-lookup"><span data-stu-id="ab19d-384">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="ab19d-385">Abrufen und Festlegen der Position des Knotens, der sich auf die Welt bezieht, in Meter.</span><span class="sxs-lookup"><span data-stu-id="ab19d-385">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="ab19d-386">Die Position entspricht einem Punkt in der Mitte der menschlichen Füße.</span><span class="sxs-lookup"><span data-stu-id="ab19d-386">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="ab19d-387">**Microsoft. perceptionsimulation. isimulatedhuman. Direction**</span><span class="sxs-lookup"><span data-stu-id="ab19d-387">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="ab19d-388">Abrufen und Festlegen der Richtung der simulierten menschlichen Gesichter in der Welt.</span><span class="sxs-lookup"><span data-stu-id="ab19d-388">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="ab19d-389">0 Bogenmaße steht nach unten auf der negativen Z-Achse.</span><span class="sxs-lookup"><span data-stu-id="ab19d-389">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="ab19d-390">Positive Bogenmaße drehen sich um die Y-Achse im Uhrzeigersinn.</span><span class="sxs-lookup"><span data-stu-id="ab19d-390">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="ab19d-391">**Microsoft. perceptionsimulation. isimulatedhuman. Height**</span><span class="sxs-lookup"><span data-stu-id="ab19d-391">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="ab19d-392">Ruft die Höhe des simulierten menschlichen in Meter ab und legt diese fest.</span><span class="sxs-lookup"><span data-stu-id="ab19d-392">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="ab19d-393">**Microsoft. perceptionsimulation. isimulatedhuman. Lefthand**</span><span class="sxs-lookup"><span data-stu-id="ab19d-393">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="ab19d-394">Rufen Sie die linke Seite des simulierten Menschen ab.</span><span class="sxs-lookup"><span data-stu-id="ab19d-394">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="ab19d-395">**Microsoft. perceptionsimulation. isimulatedhuman. rightHand**</span><span class="sxs-lookup"><span data-stu-id="ab19d-395">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="ab19d-396">Rufen Sie die Rechte des simulierten Menschen ab.</span><span class="sxs-lookup"><span data-stu-id="ab19d-396">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="ab19d-397">**Microsoft. perceptionsimulation. isimulatedhuman. Head**</span><span class="sxs-lookup"><span data-stu-id="ab19d-397">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="ab19d-398">Rufen Sie die Kopfzeile des simulierten Menschen ab.</span><span class="sxs-lookup"><span data-stu-id="ab19d-398">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="ab19d-399">**Microsoft. perceptionsimulation. isimulatedhuman. Move (Microsoft. perceptionsimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="ab19d-399">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="ab19d-400">Verschieben Sie den simulierten menschlichen in Relation zur aktuellen Position in Meter.</span><span class="sxs-lookup"><span data-stu-id="ab19d-400">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="ab19d-401">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab19d-401">Parameters</span></span>
* <span data-ttu-id="ab19d-402">Translation: die Verschiebung, die relativ zur aktuellen Position verschoben werden soll.</span><span class="sxs-lookup"><span data-stu-id="ab19d-402">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="ab19d-403">**Microsoft. perceptionsimulation. isimulatedhuman. Rotation (System. Single)**</span><span class="sxs-lookup"><span data-stu-id="ab19d-403">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="ab19d-404">Drehen des simulierten menschlichen in Relation zur aktuellen Richtung, im Uhrzeigersinn um die Y-Achse</span><span class="sxs-lookup"><span data-stu-id="ab19d-404">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="ab19d-405">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab19d-405">Parameters</span></span>
* <span data-ttu-id="ab19d-406">Bogenmaß: der Betrag für die Drehung um die Y-Achse.</span><span class="sxs-lookup"><span data-stu-id="ab19d-406">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="ab19d-407">Microsoft. perceptionsimulation. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="ab19d-407">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="ab19d-408">Wenn Sie isimulatedhuman in ISimulatedHuman2 umwandeln, sind zusätzliche Eigenschaften verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ab19d-408">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="ab19d-409">**Microsoft. perceptionsimulation. ISimulatedHuman2. leftcontroller**</span><span class="sxs-lookup"><span data-stu-id="ab19d-409">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="ab19d-410">Rufen Sie den linken 6-DOF-Controller ab.</span><span class="sxs-lookup"><span data-stu-id="ab19d-410">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="ab19d-411">**Microsoft. perceptionsimulation. ISimulatedHuman2. rightcontroller**</span><span class="sxs-lookup"><span data-stu-id="ab19d-411">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="ab19d-412">Rufen Sie den rechten 6-DOF-Controller ab.</span><span class="sxs-lookup"><span data-stu-id="ab19d-412">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="ab19d-413">Microsoft. perceptionsimulation. isimulatedhand</span><span class="sxs-lookup"><span data-stu-id="ab19d-413">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="ab19d-414">Schnittstelle, die eine Hand des simulierten Menschen beschreibt</span><span class="sxs-lookup"><span data-stu-id="ab19d-414">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="ab19d-415">**Microsoft. perceptionsimulation. isimulatedhand. worldposition**</span><span class="sxs-lookup"><span data-stu-id="ab19d-415">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="ab19d-416">Rufen Sie die Position des Knotens mit der Welt in Meter ab.</span><span class="sxs-lookup"><span data-stu-id="ab19d-416">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="ab19d-417">**Microsoft. perceptionsimulation. isimulatedhand. Position**</span><span class="sxs-lookup"><span data-stu-id="ab19d-417">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="ab19d-418">Abrufen und Festlegen der Position der simulierten Hand in Relation zum menschlichen Wert in Meter.</span><span class="sxs-lookup"><span data-stu-id="ab19d-418">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="ab19d-419">**Microsoft. perceptionsimulation. isimulatedhand. aktiviert**</span><span class="sxs-lookup"><span data-stu-id="ab19d-419">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="ab19d-420">Rufen Sie ab, und legen Sie fest, ob die Hand aktuell aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="ab19d-420">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="ab19d-421">**Microsoft. perceptionsimulation. isimulatedhand. Visible**</span><span class="sxs-lookup"><span data-stu-id="ab19d-421">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="ab19d-422">Ruft ab, ob die Hand derzeit für simulateddevice sichtbar ist (d. h., ob Sie sich in einer von der Handtracker erkannten Position befindet).</span><span class="sxs-lookup"><span data-stu-id="ab19d-422">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="ab19d-423">**Microsoft. perceptionsimulation. isimulatedhand. EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="ab19d-423">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="ab19d-424">Verschieben Sie die Hand so, dass Sie für simulateddevice sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="ab19d-424">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="ab19d-425">**Microsoft. perceptionsimulation. isimulatedhand. Move (Microsoft. perceptionsimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="ab19d-425">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="ab19d-426">Verschiebt die Position der simulierten Hand in Relation zur aktuellen Position in Meter.</span><span class="sxs-lookup"><span data-stu-id="ab19d-426">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="ab19d-427">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab19d-427">Parameters</span></span>
* <span data-ttu-id="ab19d-428">Translation: der Betrag, um den die simulierte Hand übersetzt werden soll.</span><span class="sxs-lookup"><span data-stu-id="ab19d-428">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="ab19d-429">**Microsoft. perceptionsimulation. isimulatedhand. performgesten (Microsoft. perceptionsimulation. simulatedgesten)**</span><span class="sxs-lookup"><span data-stu-id="ab19d-429">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="ab19d-430">Führt eine Geste mithilfe der simulierten Hand aus.</span><span class="sxs-lookup"><span data-stu-id="ab19d-430">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="ab19d-431">Sie wird nur vom System erkannt, wenn die Hand aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="ab19d-431">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="ab19d-432">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab19d-432">Parameters</span></span>
* <span data-ttu-id="ab19d-433">Geste: die auszuführende Geste.</span><span class="sxs-lookup"><span data-stu-id="ab19d-433">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="ab19d-434">Microsoft. perceptionsimulation. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="ab19d-434">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="ab19d-435">Weitere Eigenschaften werden durch Umwandeln von isimulatedhand in ISimulatedHand2 verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ab19d-435">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="ab19d-436">**Microsoft. perceptionsimulation. ISimulatedHand2. Orientation**</span><span class="sxs-lookup"><span data-stu-id="ab19d-436">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="ab19d-437">Ruft die Drehung der simulierten Hand ab oder legt Sie fest.</span><span class="sxs-lookup"><span data-stu-id="ab19d-437">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="ab19d-438">Bei der Betrachtung der Achse wird der Uhrzeigersinn im Uhrzeigersinn gedreht.</span><span class="sxs-lookup"><span data-stu-id="ab19d-438">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="ab19d-439">Microsoft. perceptionsimulation. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="ab19d-439">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="ab19d-440">Weitere Eigenschaften werden durch Umwandeln von isimulatedhand in ISimulatedHand3 verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ab19d-440">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="ab19d-441">**Microsoft. perceptionsimulation. ISimulatedHand3. getjointconfiguration**</span><span class="sxs-lookup"><span data-stu-id="ab19d-441">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="ab19d-442">Die gemeinsame Konfiguration für die angegebene Verbindung wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ab19d-442">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="ab19d-443">**Microsoft. perceptionsimulation. ISimulatedHand3. setjointconfiguration**</span><span class="sxs-lookup"><span data-stu-id="ab19d-443">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="ab19d-444">Legen Sie die gemeinsame Konfiguration für die angegebene Verbindung fest.</span><span class="sxs-lookup"><span data-stu-id="ab19d-444">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="ab19d-445">**Microsoft. perceptionsimulation. ISimulatedHand3. ".**</span><span class="sxs-lookup"><span data-stu-id="ab19d-445">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="ab19d-446">Legen Sie die Hand auf eine bekannte Pose mit einem optionalen Flag zum Animieren fest.</span><span class="sxs-lookup"><span data-stu-id="ab19d-446">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="ab19d-447">Hinweis: das Animieren führt nicht dazu, dass die Gelenke sofort ihre abschließenden gemeinsamen Konfigurationen widerspiegeln.</span><span class="sxs-lookup"><span data-stu-id="ab19d-447">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="ab19d-448">Microsoft. perceptionsimulation. isimulatedhead</span><span class="sxs-lookup"><span data-stu-id="ab19d-448">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="ab19d-449">Schnittstelle, die den Anfang des simulierten Menschen beschreibt.</span><span class="sxs-lookup"><span data-stu-id="ab19d-449">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="ab19d-450">**Microsoft. perceptionsimulation. isimulatedhead. worldposition**</span><span class="sxs-lookup"><span data-stu-id="ab19d-450">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="ab19d-451">Rufen Sie die Position des Knotens mit der Welt in Meter ab.</span><span class="sxs-lookup"><span data-stu-id="ab19d-451">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="ab19d-452">**Microsoft. perceptionsimulation. isimulatedhead. Rotation**</span><span class="sxs-lookup"><span data-stu-id="ab19d-452">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="ab19d-453">Ruft die Drehung des simulierten Kopfes ab.</span><span class="sxs-lookup"><span data-stu-id="ab19d-453">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="ab19d-454">Bei der Betrachtung der Achse wird der Uhrzeigersinn im Uhrzeigersinn gedreht.</span><span class="sxs-lookup"><span data-stu-id="ab19d-454">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="ab19d-455">**Microsoft. perceptionsimulation. isimulatedhead. Durchmesser**</span><span class="sxs-lookup"><span data-stu-id="ab19d-455">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="ab19d-456">Ruft den Durchmesser des simulierten Kopfes ab.</span><span class="sxs-lookup"><span data-stu-id="ab19d-456">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="ab19d-457">Dieser Wert wird verwendet, um den Mittelpunkt (Punkt der Drehung) zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="ab19d-457">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="ab19d-458">**Microsoft. perceptionsimulation. isimulatedhead. Rotation (Microsoft. perceptionsimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="ab19d-458">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="ab19d-459">Drehen Sie den simulierten Kopf in Relation zur aktuellen Drehung.</span><span class="sxs-lookup"><span data-stu-id="ab19d-459">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="ab19d-460">Bei der Betrachtung der Achse wird der Uhrzeigersinn im Uhrzeigersinn gedreht.</span><span class="sxs-lookup"><span data-stu-id="ab19d-460">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="ab19d-461">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab19d-461">Parameters</span></span>
* <span data-ttu-id="ab19d-462">Rotation: die Menge, die gedreht werden soll.</span><span class="sxs-lookup"><span data-stu-id="ab19d-462">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="ab19d-463">Microsoft. perceptionsimulation. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="ab19d-463">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="ab19d-464">Weitere Eigenschaften sind verfügbar, indem ein isimulatedhead-Element in ISimulatedHead2 umgewandelt wird.</span><span class="sxs-lookup"><span data-stu-id="ab19d-464">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="ab19d-465">**Microsoft. perceptionsimulation. ISimulatedHead2. Eyes**</span><span class="sxs-lookup"><span data-stu-id="ab19d-465">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="ab19d-466">Rufen Sie die Augen des simulierten Menschen ab.</span><span class="sxs-lookup"><span data-stu-id="ab19d-466">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="ab19d-467">Microsoft. perceptionsimulation. isimulatedsixdofcontroller</span><span class="sxs-lookup"><span data-stu-id="ab19d-467">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="ab19d-468">Eine Schnittstelle, die einen dem simulierten Menschen zugeordneten 6-DOF-Controller beschreibt.</span><span class="sxs-lookup"><span data-stu-id="ab19d-468">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="ab19d-469">**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. worldposition**</span><span class="sxs-lookup"><span data-stu-id="ab19d-469">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="ab19d-470">Rufen Sie die Position des Knotens mit der Welt in Meter ab.</span><span class="sxs-lookup"><span data-stu-id="ab19d-470">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="ab19d-471">**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. Status**</span><span class="sxs-lookup"><span data-stu-id="ab19d-471">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="ab19d-472">Ruft den aktuellen Zustand des Controllers ab oder legt ihn fest.</span><span class="sxs-lookup"><span data-stu-id="ab19d-472">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="ab19d-473">Der Controller Status muss auf einen anderen Wert als "Off" festgelegt werden, bevor Aufrufe zum Verschieben, drehen oder Drücken von Schaltflächen erfolgreich ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="ab19d-473">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="ab19d-474">**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. Position**</span><span class="sxs-lookup"><span data-stu-id="ab19d-474">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="ab19d-475">Ruft die Position des simulierten Controllers in Relation zum menschlichen in Meter ab oder legt diese fest.</span><span class="sxs-lookup"><span data-stu-id="ab19d-475">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="ab19d-476">**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. Orientation**</span><span class="sxs-lookup"><span data-stu-id="ab19d-476">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="ab19d-477">Ruft die Ausrichtung des simulierten Controllers ab oder legt Sie fest.</span><span class="sxs-lookup"><span data-stu-id="ab19d-477">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="ab19d-478">**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. Move (Microsoft. perceptionsimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="ab19d-478">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="ab19d-479">Verschiebt die Position des simulierten Controllers relativ zu seiner aktuellen Position in Meter.</span><span class="sxs-lookup"><span data-stu-id="ab19d-479">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="ab19d-480">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab19d-480">Parameters</span></span>
* <span data-ttu-id="ab19d-481">Translation: der Betrag, um den der simulierte Controller übersetzt werden soll.</span><span class="sxs-lookup"><span data-stu-id="ab19d-481">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="ab19d-482">**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. pressbutton (simulatedsixdofcontrollerbutton)**</span><span class="sxs-lookup"><span data-stu-id="ab19d-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="ab19d-483">Drücken Sie auf dem simulierten Controller eine Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="ab19d-483">Press a button on the simulated controller.</span></span>  <span data-ttu-id="ab19d-484">Sie wird nur vom System erkannt, wenn der Controller aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="ab19d-484">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="ab19d-485">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab19d-485">Parameters</span></span>
* <span data-ttu-id="ab19d-486">Schaltfläche: die Schaltfläche zum drücken.</span><span class="sxs-lookup"><span data-stu-id="ab19d-486">button - The button to press.</span></span>

<span data-ttu-id="ab19d-487">**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. releasebutton (simulatedsixdofcontrollerbutton)**</span><span class="sxs-lookup"><span data-stu-id="ab19d-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="ab19d-488">Gibt eine Schaltfläche auf dem simulierten Controller frei.</span><span class="sxs-lookup"><span data-stu-id="ab19d-488">Release a button on the simulated controller.</span></span>  <span data-ttu-id="ab19d-489">Sie wird nur vom System erkannt, wenn der Controller aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="ab19d-489">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="ab19d-490">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab19d-490">Parameters</span></span>
* <span data-ttu-id="ab19d-491">Button: die Schaltfläche, die freigegeben werden soll.</span><span class="sxs-lookup"><span data-stu-id="ab19d-491">button - The button to release.</span></span>

<span data-ttu-id="ab19d-492">**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. gettouchpadposition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="ab19d-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="ab19d-493">Die Position eines simulierten Fingers im Touchpad des simulierten Controllers erhalten.</span><span class="sxs-lookup"><span data-stu-id="ab19d-493">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="ab19d-494">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab19d-494">Parameters</span></span>
* <span data-ttu-id="ab19d-495">x: die horizontale Position des Fingers.</span><span class="sxs-lookup"><span data-stu-id="ab19d-495">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="ab19d-496">y-die vertikale Position des Fingers.</span><span class="sxs-lookup"><span data-stu-id="ab19d-496">y - The vertical position of the finger.</span></span>

<span data-ttu-id="ab19d-497">**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. settouchpadposition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="ab19d-497">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="ab19d-498">Legen Sie die Position eines simulierten Fingers auf dem Touchpad des simulierten Controllers fest.</span><span class="sxs-lookup"><span data-stu-id="ab19d-498">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="ab19d-499">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab19d-499">Parameters</span></span>
* <span data-ttu-id="ab19d-500">x: die horizontale Position des Fingers.</span><span class="sxs-lookup"><span data-stu-id="ab19d-500">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="ab19d-501">y-die vertikale Position des Fingers.</span><span class="sxs-lookup"><span data-stu-id="ab19d-501">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="ab19d-502">Microsoft. perceptionsimulation. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="ab19d-502">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="ab19d-503">Zusätzliche Eigenschaften und Methoden sind verfügbar, indem ein isimulatedsixdofcontroller in ISimulatedSixDofController2 umgewandelt wird.</span><span class="sxs-lookup"><span data-stu-id="ab19d-503">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="ab19d-504">**Microsoft. perceptionsimulation. ISimulatedSixDofController2. getthumbstickposition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="ab19d-504">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="ab19d-505">Gibt die Position des simulierten thumbsticks auf dem simulierten Controller an.</span><span class="sxs-lookup"><span data-stu-id="ab19d-505">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="ab19d-506">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab19d-506">Parameters</span></span>
* <span data-ttu-id="ab19d-507">x: die horizontale Position des fingersticks.</span><span class="sxs-lookup"><span data-stu-id="ab19d-507">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="ab19d-508">y: die vertikale Position des Finger anheften.</span><span class="sxs-lookup"><span data-stu-id="ab19d-508">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="ab19d-509">**Microsoft. perceptionsimulation. ISimulatedSixDofController2. setthumbstickposition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="ab19d-509">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="ab19d-510">Legen Sie die Position des simulierten thumbsticks auf dem simulierten Controller fest.</span><span class="sxs-lookup"><span data-stu-id="ab19d-510">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="ab19d-511">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab19d-511">Parameters</span></span>
* <span data-ttu-id="ab19d-512">x: die horizontale Position des fingersticks.</span><span class="sxs-lookup"><span data-stu-id="ab19d-512">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="ab19d-513">y: die vertikale Position des Finger anheften.</span><span class="sxs-lookup"><span data-stu-id="ab19d-513">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="ab19d-514">**Microsoft. perceptionsimulation. ISimulatedSixDofController2. Akku Level**</span><span class="sxs-lookup"><span data-stu-id="ab19d-514">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="ab19d-515">Ruft den Akku Pegel des simulierten Controllers ab oder legt ihn fest.</span><span class="sxs-lookup"><span data-stu-id="ab19d-515">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="ab19d-516">Der Wert muss größer als 0,0 und kleiner oder gleich 100,0 sein.</span><span class="sxs-lookup"><span data-stu-id="ab19d-516">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="ab19d-517">Microsoft. perceptionsimulation. isimulatedeyes</span><span class="sxs-lookup"><span data-stu-id="ab19d-517">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="ab19d-518">Schnittstelle, die die Augen des simulierten Menschen beschreibt.</span><span class="sxs-lookup"><span data-stu-id="ab19d-518">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="ab19d-519">**Microsoft. perceptionsimulation. isimulatedeyes. Rotation**</span><span class="sxs-lookup"><span data-stu-id="ab19d-519">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="ab19d-520">Ruft die Drehung der simulierten Augen ab.</span><span class="sxs-lookup"><span data-stu-id="ab19d-520">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="ab19d-521">Bei der Betrachtung der Achse wird der Uhrzeigersinn im Uhrzeigersinn gedreht.</span><span class="sxs-lookup"><span data-stu-id="ab19d-521">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="ab19d-522">**Microsoft. perceptionsimulation. isimulatedeyes. Rotation (Microsoft. perceptionsimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="ab19d-522">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="ab19d-523">Drehen der simulierten Augen in Relation zur aktuellen Drehung.</span><span class="sxs-lookup"><span data-stu-id="ab19d-523">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="ab19d-524">Bei der Betrachtung der Achse wird der Uhrzeigersinn im Uhrzeigersinn gedreht.</span><span class="sxs-lookup"><span data-stu-id="ab19d-524">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="ab19d-525">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab19d-525">Parameters</span></span>
* <span data-ttu-id="ab19d-526">Rotation: die Menge, die gedreht werden soll.</span><span class="sxs-lookup"><span data-stu-id="ab19d-526">rotation - The amount to rotate.</span></span>

<span data-ttu-id="ab19d-527">**Microsoft. perceptionsimulation. isimulatedeyes. calibrationstate**</span><span class="sxs-lookup"><span data-stu-id="ab19d-527">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="ab19d-528">Ruft den Kalibrierungs Zustand der simulierten Augen ab oder legt ihn fest.</span><span class="sxs-lookup"><span data-stu-id="ab19d-528">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="ab19d-529">**Microsoft. perceptionsimulation. isimulatedeyes. worldposition**</span><span class="sxs-lookup"><span data-stu-id="ab19d-529">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="ab19d-530">Rufen Sie die Position des Knotens mit der Welt in Meter ab.</span><span class="sxs-lookup"><span data-stu-id="ab19d-530">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="ab19d-531">Microsoft. perceptionsimulation. isimulationrecording</span><span class="sxs-lookup"><span data-stu-id="ab19d-531">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="ab19d-532">Schnittstelle für die Interaktion mit einer einzelnen, für die Wiedergabe geladenen Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="ab19d-532">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="ab19d-533">**Microsoft. perceptionsimulation. isimulationrecording. DataTypes**</span><span class="sxs-lookup"><span data-stu-id="ab19d-533">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="ab19d-534">Ruft die Liste der Datentypen in der Aufzeichnung ab.</span><span class="sxs-lookup"><span data-stu-id="ab19d-534">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="ab19d-535">**Microsoft. perceptionsimulation. isimulationrecording. State**</span><span class="sxs-lookup"><span data-stu-id="ab19d-535">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="ab19d-536">Ruft den aktuellen Zustand der Aufzeichnung ab.</span><span class="sxs-lookup"><span data-stu-id="ab19d-536">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="ab19d-537">**Microsoft. perceptionsimulation. isimulationrecording. Play**</span><span class="sxs-lookup"><span data-stu-id="ab19d-537">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="ab19d-538">Starten Sie die Wiedergabe.</span><span class="sxs-lookup"><span data-stu-id="ab19d-538">Start the playback.</span></span> <span data-ttu-id="ab19d-539">Wenn die Aufzeichnung angehalten wurde, wird die Wiedergabe an der angehaltenen Position fortgesetzt. Wenn der Vorgang beendet ist, wird die Wiedergabe am Anfang gestartet.</span><span class="sxs-lookup"><span data-stu-id="ab19d-539">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="ab19d-540">Wenn Sie bereits abgespielt wird, wird dieser-Befehl ignoriert.</span><span class="sxs-lookup"><span data-stu-id="ab19d-540">If already playing, this call is ignored.</span></span>

<span data-ttu-id="ab19d-541">**Microsoft. perceptionsimulation. isimulationrecording. Pause**</span><span class="sxs-lookup"><span data-stu-id="ab19d-541">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="ab19d-542">Hält die Wiedergabe an Ihrer aktuellen Position an.</span><span class="sxs-lookup"><span data-stu-id="ab19d-542">Pauses the playback at its current location.</span></span> <span data-ttu-id="ab19d-543">Wenn die Aufzeichnung beendet wird, wird der-Rückruf ignoriert.</span><span class="sxs-lookup"><span data-stu-id="ab19d-543">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="ab19d-544">**Microsoft. perceptionsimulation. isimulationrecording. Seek (System. UInt64)**</span><span class="sxs-lookup"><span data-stu-id="ab19d-544">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="ab19d-545">Sucht die Aufzeichnung bis zur angegebenen Zeit (in 100 Nanosekunden-Intervallen von Anfang an) und hält an dieser Stelle an.</span><span class="sxs-lookup"><span data-stu-id="ab19d-545">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="ab19d-546">Wenn die Uhrzeit hinter dem Ende der Aufzeichnung liegt, wird Sie im letzten Frame angehalten.</span><span class="sxs-lookup"><span data-stu-id="ab19d-546">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="ab19d-547">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab19d-547">Parameters</span></span>
* <span data-ttu-id="ab19d-548">Ticks-die Zeit, nach der gesucht werden soll.</span><span class="sxs-lookup"><span data-stu-id="ab19d-548">ticks - The time to which to seek.</span></span>

<span data-ttu-id="ab19d-549">**Microsoft. perceptionsimulation. isimulationrecording. anhalten**</span><span class="sxs-lookup"><span data-stu-id="ab19d-549">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="ab19d-550">Beendet die Wiedergabe und setzt die Position auf den Anfang zurück.</span><span class="sxs-lookup"><span data-stu-id="ab19d-550">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="ab19d-551">Microsoft. perceptionsimulation. isimulationrecordingcallback</span><span class="sxs-lookup"><span data-stu-id="ab19d-551">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="ab19d-552">Schnittstelle zum Empfangen von Zustandsänderungen während der Wiedergabe.</span><span class="sxs-lookup"><span data-stu-id="ab19d-552">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="ab19d-553">**Microsoft. perceptionsimulation. isimulationrecordingcallback. playbackstatechanged (Microsoft. perceptionsimulation. playbackstate)**</span><span class="sxs-lookup"><span data-stu-id="ab19d-553">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="ab19d-554">Wird aufgerufen, wenn sich der Wiedergabe Zustand einer isimulationrecording geändert hat.</span><span class="sxs-lookup"><span data-stu-id="ab19d-554">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="ab19d-555">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab19d-555">Parameters</span></span>
* <span data-ttu-id="ab19d-556">newState: der neue Status der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="ab19d-556">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="ab19d-557">Microsoft. perceptionsimulation. perceptionsimulationmanager</span><span class="sxs-lookup"><span data-stu-id="ab19d-557">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="ab19d-558">Das Stamm Objekt zum Erstellen von perception Simulation-Objekten.</span><span class="sxs-lookup"><span data-stu-id="ab19d-558">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="ab19d-559">**Microsoft. perceptionsimulation. perceptionsimulationmanager. kreateperceptionsimulationmanager (Microsoft. perceptionsimulation. isimulationstreamsink)**</span><span class="sxs-lookup"><span data-stu-id="ab19d-559">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="ab19d-560">Erstellen Sie ein Objekt zum Erstellen von simulierten Paketen und zum Bereitstellen der Pakete an die angegebene Senke.</span><span class="sxs-lookup"><span data-stu-id="ab19d-560">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="ab19d-561">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab19d-561">Parameters</span></span>
* <span data-ttu-id="ab19d-562">Sink: die Senke, die alle generierten Pakete empfängt.</span><span class="sxs-lookup"><span data-stu-id="ab19d-562">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="ab19d-563">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="ab19d-563">Return value</span></span>

<span data-ttu-id="ab19d-564">Der erstellte Manager.</span><span class="sxs-lookup"><span data-stu-id="ab19d-564">The created Manager.</span></span>

<span data-ttu-id="ab19d-565">**Microsoft. perceptionsimulation. perceptionsimulationmanager. kreateperceptionsimulationrecording (System. String)**</span><span class="sxs-lookup"><span data-stu-id="ab19d-565">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="ab19d-566">Erstellen Sie eine Senke, in der alle empfangenen Pakete in einer Datei unter dem angegebenen Pfad gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="ab19d-566">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="ab19d-567">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab19d-567">Parameters</span></span>
* <span data-ttu-id="ab19d-568">Path: der Pfad der zu erstellenden Datei.</span><span class="sxs-lookup"><span data-stu-id="ab19d-568">path - The path of the file to create.</span></span>

<span data-ttu-id="ab19d-569">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="ab19d-569">Return value</span></span>

<span data-ttu-id="ab19d-570">Die erstellte Senke.</span><span class="sxs-lookup"><span data-stu-id="ab19d-570">The created sink.</span></span>

<span data-ttu-id="ab19d-571">**Microsoft. perceptionsimulation. perceptionsimulationmanager. loadperceptionsimulationrecording (System. String, Microsoft. perceptionsimulation. isimulationstreamsink Factory)**</span><span class="sxs-lookup"><span data-stu-id="ab19d-571">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="ab19d-572">Lädt eine Aufzeichnung aus der angegebenen Datei.</span><span class="sxs-lookup"><span data-stu-id="ab19d-572">Load a recording from the specified file.</span></span>

<span data-ttu-id="ab19d-573">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab19d-573">Parameters</span></span>
* <span data-ttu-id="ab19d-574">Path: der Pfad der zu ladenden Datei.</span><span class="sxs-lookup"><span data-stu-id="ab19d-574">path - The path of the file to load.</span></span>
* <span data-ttu-id="ab19d-575">Factory: eine Factory, die von der Aufzeichnung zum Erstellen einer isimulationstreamsink bei Bedarf verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ab19d-575">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="ab19d-576">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="ab19d-576">Return value</span></span>

<span data-ttu-id="ab19d-577">Die geladene Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="ab19d-577">The loaded recording.</span></span>

<span data-ttu-id="ab19d-578">**Microsoft. perceptionsimulation. perzeptionsimulationmanager. loadperceptionsimulationrecording (System. String, Microsoft. perceptionsimulation. isimulationstreamsink Factory, Microsoft. perceptionsimulation. isimulationrecordingcallback)**</span><span class="sxs-lookup"><span data-stu-id="ab19d-578">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="ab19d-579">Lädt eine Aufzeichnung aus der angegebenen Datei.</span><span class="sxs-lookup"><span data-stu-id="ab19d-579">Load a recording from the specified file.</span></span>

<span data-ttu-id="ab19d-580">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab19d-580">Parameters</span></span>
* <span data-ttu-id="ab19d-581">Path: der Pfad der zu ladenden Datei.</span><span class="sxs-lookup"><span data-stu-id="ab19d-581">path - The path of the file to load.</span></span>
* <span data-ttu-id="ab19d-582">Factory: eine Factory, die von der Aufzeichnung zum Erstellen einer isimulationstreamsink bei Bedarf verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="ab19d-582">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="ab19d-583">Callback: ein Rückruf, der Updates empfängt, die den Status der Aufzeichnung neu formatidieren.</span><span class="sxs-lookup"><span data-stu-id="ab19d-583">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="ab19d-584">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="ab19d-584">Return value</span></span>

<span data-ttu-id="ab19d-585">Die geladene Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="ab19d-585">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="ab19d-586">Microsoft. perceptionsimulation. streamdatatypes</span><span class="sxs-lookup"><span data-stu-id="ab19d-586">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="ab19d-587">Beschreibt die unterschiedlichen Typen von Streamdaten.</span><span class="sxs-lookup"><span data-stu-id="ab19d-587">Describes the different types of stream data.</span></span>

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    SixDofControllers = 0x40,
    Eyes = 0x80,
    DisplayConfiguration = 0x100
    All = None | Head | Hands | SpatialMapping | Calibration | Environment | SixDofControllers | Eyes | DisplayConfiguration
}
```

<span data-ttu-id="ab19d-588">**Microsoft. perceptionsimulation. streamdatatypes. None**</span><span class="sxs-lookup"><span data-stu-id="ab19d-588">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="ab19d-589">Ein Sentinelwert, der verwendet wird, um keine streamdatentypen anzugeben</span><span class="sxs-lookup"><span data-stu-id="ab19d-589">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="ab19d-590">**Microsoft. perceptionsimulation. streamdatatypes. Head**</span><span class="sxs-lookup"><span data-stu-id="ab19d-590">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="ab19d-591">Datenstrom bezüglich der Position und Ausrichtung des Kopfes.</span><span class="sxs-lookup"><span data-stu-id="ab19d-591">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="ab19d-592">**Microsoft. perceptionsimulation. streamdatatypes. Hands**</span><span class="sxs-lookup"><span data-stu-id="ab19d-592">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="ab19d-593">Datenstrom in Bezug auf die Position und Gesten von Händen.</span><span class="sxs-lookup"><span data-stu-id="ab19d-593">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="ab19d-594">**Microsoft. perceptionsimulation. streamdatatypes. spatialmapping**</span><span class="sxs-lookup"><span data-stu-id="ab19d-594">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="ab19d-595">Datenstrom in Bezug auf die räumliche Zuordnung der Umgebung.</span><span class="sxs-lookup"><span data-stu-id="ab19d-595">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="ab19d-596">**Microsoft. perceptionsimulation. streamdatatypes. Kalibrierung**</span><span class="sxs-lookup"><span data-stu-id="ab19d-596">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="ab19d-597">Datenstrom zur Kalibrierung des Geräts.</span><span class="sxs-lookup"><span data-stu-id="ab19d-597">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="ab19d-598">Kalibrierungs Pakete werden nur von einem System im Remote Modus akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="ab19d-598">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="ab19d-599">**Microsoft. perceptionsimulation. streamdatatypes. Environment**</span><span class="sxs-lookup"><span data-stu-id="ab19d-599">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="ab19d-600">Datenstrom in Bezug auf die Umgebung des Geräts.</span><span class="sxs-lookup"><span data-stu-id="ab19d-600">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="ab19d-601">**Microsoft. perceptionsimulation. streamdatatypes. sixdof Controllers**</span><span class="sxs-lookup"><span data-stu-id="ab19d-601">**Microsoft.PerceptionSimulation.StreamDataTypes.SixDofControllers**</span></span>

<span data-ttu-id="ab19d-602">Datenstrom in Bezug auf Motion-Controller.</span><span class="sxs-lookup"><span data-stu-id="ab19d-602">Stream of data regarding motion controllers.</span></span>

<span data-ttu-id="ab19d-603">**Microsoft. perceptionsimulation. streamdatatypes. Eyes**</span><span class="sxs-lookup"><span data-stu-id="ab19d-603">**Microsoft.PerceptionSimulation.StreamDataTypes.Eyes**</span></span>

<span data-ttu-id="ab19d-604">Datenstrom in Bezug auf die Augen des simulierten Menschen.</span><span class="sxs-lookup"><span data-stu-id="ab19d-604">Stream of data regarding the eyes of the simulated human.</span></span>

<span data-ttu-id="ab19d-605">**Microsoft. perceptionsimulation. streamdatatypes. displayconfiguration**</span><span class="sxs-lookup"><span data-stu-id="ab19d-605">**Microsoft.PerceptionSimulation.StreamDataTypes.DisplayConfiguration**</span></span>

<span data-ttu-id="ab19d-606">Datenstrom in Bezug auf die Anzeige Konfiguration des Geräts.</span><span class="sxs-lookup"><span data-stu-id="ab19d-606">Stream of data regarding the display configuration of the device.</span></span>

<span data-ttu-id="ab19d-607">**Microsoft. perceptionsimulation. streamdatatypes. all**</span><span class="sxs-lookup"><span data-stu-id="ab19d-607">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="ab19d-608">Ein Sentinelwert, der verwendet wird, um alle aufgezeichneten Datentypen anzugeben.</span><span class="sxs-lookup"><span data-stu-id="ab19d-608">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="ab19d-609">Microsoft. perceptionsimulation. isimulationstreamsink</span><span class="sxs-lookup"><span data-stu-id="ab19d-609">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="ab19d-610">Ein Objekt, das Datenpakete von einem Simulationsdaten Strom empfängt.</span><span class="sxs-lookup"><span data-stu-id="ab19d-610">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="ab19d-611">**Microsoft. perceptionsimulation. isimulationstreamsink. onpacketempfang\uint length, Byte [] Packet)**</span><span class="sxs-lookup"><span data-stu-id="ab19d-611">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="ab19d-612">Empfängt ein einzelnes Paket, das intern eingegeben und mit Versions Angabe versehen ist.</span><span class="sxs-lookup"><span data-stu-id="ab19d-612">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="ab19d-613">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab19d-613">Parameters</span></span>
* <span data-ttu-id="ab19d-614">length: die Länge des Pakets.</span><span class="sxs-lookup"><span data-stu-id="ab19d-614">length - The length of the packet.</span></span>
* <span data-ttu-id="ab19d-615">Packet: die Daten des Pakets.</span><span class="sxs-lookup"><span data-stu-id="ab19d-615">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="ab19d-616">Microsoft. perceptionsimulation. isimulationstreamsink Factory</span><span class="sxs-lookup"><span data-stu-id="ab19d-616">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="ab19d-617">Ein Objekt, das isimulationstreamsink erstellt.</span><span class="sxs-lookup"><span data-stu-id="ab19d-617">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="ab19d-618">**Microsoft. perceptionsimulation. isimulationstreamsink Factory. kreatesimulationstreamsink ()**</span><span class="sxs-lookup"><span data-stu-id="ab19d-618">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="ab19d-619">Erstellt eine einzelne Instanz von isimulationstreamsink.</span><span class="sxs-lookup"><span data-stu-id="ab19d-619">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="ab19d-620">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="ab19d-620">Return value</span></span>

<span data-ttu-id="ab19d-621">Die erstellte Senke.</span><span class="sxs-lookup"><span data-stu-id="ab19d-621">The created sink.</span></span>
