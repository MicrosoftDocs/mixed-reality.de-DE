---
title: Wahrnehmungs Simulation
description: Leitfaden zur Verwendung der Wahrnehmungs Simulations Bibliothek zum Automatisieren von simulierten Eingaben für immersive Anwendungen
author: pbarnettms
ms.author: pbarnett
ms.date: 04/26/2019
ms.topic: article
keywords: Hololens, Simulation, Tests
ms.openlocfilehash: 503533bc5a2e9307b7c5217632d42670285aac0a
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437547"
---
# <a name="perception-simulation"></a><span data-ttu-id="b6cf7-104">Wahrnehmungs Simulation</span><span class="sxs-lookup"><span data-stu-id="b6cf7-104">Perception simulation</span></span>

<span data-ttu-id="b6cf7-105">Möchten Sie einen automatisierten Test für Ihre APP erstellen?</span><span class="sxs-lookup"><span data-stu-id="b6cf7-105">Do you want to build an automated test for your app?</span></span> <span data-ttu-id="b6cf7-106">Möchten Sie, dass Ihre Tests über Komponententests auf Komponentenebene hinausgehen und Ihre APP End-to-End wirklich ausführen?</span><span class="sxs-lookup"><span data-stu-id="b6cf7-106">Do you want your tests to go beyond component-level unit testing and really exercise your app end-to-end?</span></span> <span data-ttu-id="b6cf7-107">Die Wahrnehmungs Simulation ist das, was Sie suchen.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-107">Perception Simulation is what you're looking for.</span></span> <span data-ttu-id="b6cf7-108">Die Bibliothek für Wahrnehmungs Simulationen sendet Benutzer-und Welt Eingabedaten an Ihre APP, damit Sie Ihre Tests automatisieren können.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-108">The Perception Simulation library sends human and world input data to your app so you can automate your tests.</span></span> <span data-ttu-id="b6cf7-109">Beispielsweise können Sie die Eingabe eines Menschen simulieren, das eine bestimmte, wiederholbare Position und dann eine Geste oder einen Bewegungs Controller verwendet.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-109">For example, you can simulate the input of a human looking to a specific, repeatable position and then performing a gesture or using a motion controller.</span></span>

<span data-ttu-id="b6cf7-110">Die perception Simulation kann simulierte Eingaben wie diese an physische hololens, den hololens-Emulator (1. Generation), den hololens 2-Emulator oder einen PC mit installierter gemischtes Reality-Portal senden.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-110">Perception Simulation can send simulated input like this to a physical HoloLens, the HoloLens emulator (1st gen), the HoloLens 2 Emulator, or a PC with Mixed Reality Portal installed.</span></span> <span data-ttu-id="b6cf7-111">Die Wahrnehmungs Simulation umgeht die Live Sensoren auf einem Mixed Reality-Gerät und sendet simulierte Eingaben an Anwendungen, die auf dem Gerät ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-111">Perception Simulation bypasses the live sensors on a Mixed Reality device and sends simulated input to applications running on the device.</span></span> <span data-ttu-id="b6cf7-112">Anwendungen empfangen diese Eingabeereignisse über dieselben APIs, die Sie immer verwenden, und können den Unterschied zwischen der Ausführung mit echten Sensoren und der Ausführung mit der Wahrnehmungs Simulation nicht erkennen.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-112">Applications receive these input events through the same APIs they always use and can't tell the difference between running with real sensors versus running with Perception Simulation.</span></span> <span data-ttu-id="b6cf7-113">Die perception Simulation ist dieselbe Technologie, die von den hololens-Emulatoren verwendet wird, um simulierte Eingaben an den virtuellen Computer hololens zu senden.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-113">Perception Simulation is the same technology used by the HoloLens emulators to send simulated input to the HoloLens Virtual Machine.</span></span>

<span data-ttu-id="b6cf7-114">Beginnen Sie zunächst mit der Verwendung von Simulation in Ihrem Code, indem Sie ein ipertionsimulationmanager-Objekt erstellen.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-114">To begin using simulation in your code, start by creating an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="b6cf7-115">Aus diesem Objekt können Sie Befehle ausgeben, um die Eigenschaften eines simulierten "Menschen" zu steuern, einschließlich der Kopfposition, der Handposition und Gesten, und Sie können Bewegungs Controller aktivieren und bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-115">From that object, you can issue commands to control properties of a simulated "human", including head position, hand position, and gestures, and you can enable and manipulate motion controllers.</span></span>

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a><span data-ttu-id="b6cf7-116">Einrichten eines Visual Studio-Projekts für die Wahrnehmungs Simulation</span><span class="sxs-lookup"><span data-stu-id="b6cf7-116">Setting Up a Visual Studio Project for Perception Simulation</span></span>
1. <span data-ttu-id="b6cf7-117">[Installieren Sie den hololens-Emulator](install-the-tools.md) auf dem Entwicklungs-PC.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-117">[Install the HoloLens emulator](install-the-tools.md) on your development PC.</span></span> <span data-ttu-id="b6cf7-118">Der Emulator enthält die Bibliotheken, die Sie für die Wahrnehmungs Simulation verwenden werden.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-118">The emulator includes the libraries you will use for Perception Simulation.</span></span>
2. <span data-ttu-id="b6cf7-119">Erstellen Sie ein neues Visual C# Studio-Desktop Projekt (ein Konsolen Projekt funktioniert hervorragend für den Einstieg).</span><span class="sxs-lookup"><span data-stu-id="b6cf7-119">Create a new Visual Studio C# desktop project (a Console Project works great to get started).</span></span>
3. <span data-ttu-id="b6cf7-120">Fügen Sie dem Projekt die folgenden Binärdateien als Verweise hinzu (Project-> Add-> Reference...). Sie finden Sie unter% Program Files (x86)% \ Microsoft XDE\\(Version), z. b. **% Program Files (x86)% \ Microsoft XDE\\10.0.18362.0** für den hololens 2-Emulator.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-120">Add the following binaries to your project as references (Project->Add->Reference...). You can find them in %ProgramFiles(x86)%\Microsoft XDE\\(version), such as **%ProgramFiles(x86)%\Microsoft XDE\\10.0.18362.0** for the HoloLens 2 Emulator.</span></span>  <span data-ttu-id="b6cf7-121">(Hinweis: Obwohl die Binärdateien Teil des hololens 2-Emulators sind, funktionieren Sie auch für Windows Mixed Reality auf dem Desktop.) ein.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-121">(Note: although the binaries are part of the HoloLens 2 Emulator, they also work for Windows Mixed Reality on the desktop.) a.</span></span> <span data-ttu-id="b6cf7-122">Perceptionsimulationmanager. Interop. dll: verwalteter C# Wrapper für die Wahrnehmungs Simulation.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-122">PerceptionSimulationManager.Interop.dll - Managed C# wrapper for Perception Simulation.</span></span>
    <span data-ttu-id="b6cf7-123">b.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-123">b.</span></span> <span data-ttu-id="b6cf7-124">Perzeptionsimulationrest. dll-Bibliothek zum Einrichten eines websocketkommunikationskanals für die hololens oder den Emulator.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-124">PerceptionSimulationRest.dll - Library for setting up a web-socket communication channel to the HoloLens or emulator.</span></span>
    <span data-ttu-id="b6cf7-125">c.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-125">c.</span></span> <span data-ttu-id="b6cf7-126">Simulationstream. Interop. dll: freigegebene Typen für die Simulation.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-126">SimulationStream.Interop.dll - Shared types for simulation.</span></span>
4. <span data-ttu-id="b6cf7-127">Fügen Sie die-Implementierungs Binärdatei "perceptionsimulationmanager. dll" zu Ihrem Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-127">Add the implementation binary PerceptionSimulationManager.dll to your project a.</span></span> <span data-ttu-id="b6cf7-128">Fügen Sie Sie zunächst als Binärdatei zum Projekt hinzu (Projekt > Add-> vorhandenes Element...). Speichern Sie Sie als Link, damit Sie nicht in Ihren Projekt Quellordner kopiert wird.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-128">First add it as a binary to the project (Project->Add->Existing Item...). Save it as a link so that it doesn't copy it to your project source folder.</span></span> <span data-ttu-id="b6cf7-129">![dem Projekt die Datei "perceptionsimulationmanager. dll" als Link](images/saveaslink.png) b hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-129">![Add PerceptionSimulationManager.dll to the project as a link](images/saveaslink.png) b.</span></span> <span data-ttu-id="b6cf7-130">Stellen Sie dann sicher, dass Sie beim Build in den Ausgabeordner kopiert werden.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-130">Then make sure that it get's copied to your output folder on build.</span></span> <span data-ttu-id="b6cf7-131">Dies befindet sich auf dem Eigenschaften Blatt für die Binärdatei.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-131">This is in the property sheet for the binary .</span></span> <span data-ttu-id="b6cf7-132">![Markierung "perceptionsimulationmanager. dll", um in das Ausgabeverzeichnis zu kopieren](images/copyalways.png)</span><span class="sxs-lookup"><span data-stu-id="b6cf7-132">![Mark PerceptionSimulationManager.dll to copy to the output directory](images/copyalways.png)</span></span>
5. <span data-ttu-id="b6cf7-133">Legen Sie die Aktive Projektmappenplattform auf x64 fest.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-133">Set your active solution platform to x64.</span></span>  <span data-ttu-id="b6cf7-134">(Verwenden Sie die Configuration Manager, um einen Platt Form Eintrag für x64 zu erstellen, wenn noch keiner vorhanden ist.)</span><span class="sxs-lookup"><span data-stu-id="b6cf7-134">(Use the Configuration Manager to create a Platform entry for x64 if one does not already exist.)</span></span>

## <a name="creating-an-iperceptionsimulation-manager-object"></a><span data-ttu-id="b6cf7-135">Erstellen eines ipertionsimulation-Manager-Objekts</span><span class="sxs-lookup"><span data-stu-id="b6cf7-135">Creating an IPerceptionSimulation Manager Object</span></span>

<span data-ttu-id="b6cf7-136">Um die Simulation zu steuern, geben Sie Aktualisierungen an Objekten aus, die von einem ipertionsimulationmanager-Objekt abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-136">To control simulation, you'll issue updates to objects retrieved from an IPerceptionSimulationManager object.</span></span> <span data-ttu-id="b6cf7-137">Der erste Schritt besteht darin, dieses Objekt zu erhalten und es mit Ihrem Zielgerät oder Emulator zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-137">The first step is to get that object and connect it to your target device or emulator.</span></span> <span data-ttu-id="b6cf7-138">Klicken Sie in der [Symbolleiste](using-the-hololens-emulator.md) auf die Schaltfläche Geräte Portal, um die IP-Adresse des Emulators zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-138">You can get the IP address of your emulator by clicking on the Device Portal button in the [toolbar](using-the-hololens-emulator.md)</span></span>

<span data-ttu-id="b6cf7-139">Öffnen Sie ![Geräte Portal Symbol](images/emulator-deviceportal.png) öffnen Sie das **Geräte Portal**: Öffnen Sie das Windows-Geräte Portal für das hololens-Betriebssystem im Emulator.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-139">![Open Device Portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>  <span data-ttu-id="b6cf7-140">Für Windows Mixed Reality kann dies in der App "Einstellungen" unter "Aktualisieren der & Sicherheit" und dann "für Entwickler" im Abschnitt "Connect using:" unter "Enable Device Portal" abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-140">For Windows Mixed Reality, this can be retrieved in the Settings app under "Update & Security", then "For developers" in the "Connect using:" section under "Enable Device Portal."</span></span>  <span data-ttu-id="b6cf7-141">Achten Sie darauf, dass Sie die IP-Adresse und den Port beachten.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-141">Be sure to note both the IP address and port.</span></span>

<span data-ttu-id="b6cf7-142">Zuerst rufen Sie restsimulationstreamsink. Create auf, um ein restsimulationstreamsink-Objekt abzurufen.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-142">First, you'll call RestSimulationStreamSink.Create to get a RestSimulationStreamSink object.</span></span> <span data-ttu-id="b6cf7-143">Dies ist das Zielgerät oder der Emulator, das Sie über eine HTTP-Verbindung steuern werden.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-143">This is the target device or emulator that you will control over an http connection.</span></span> <span data-ttu-id="b6cf7-144">Ihre Befehle werden an das [Windows-Geräte Portal](using-the-windows-device-portal.md) , das auf dem Gerät oder Emulator ausgeführt wird, weitergeleitet und verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-144">Your commands will be passed to and handled by the [Windows Device Portal](using-the-windows-device-portal.md) running on the device or emulator.</span></span> <span data-ttu-id="b6cf7-145">Die vier Parameter, die Sie zum Erstellen eines Objekts benötigen, sind:</span><span class="sxs-lookup"><span data-stu-id="b6cf7-145">The four parameters you'll need to create an object are:</span></span>
* <span data-ttu-id="b6cf7-146">URI-URI: IP-Adresse des Zielgeräts (z. b. "https://123.123.123.123" oder "https://123.123.123.123:50080")</span><span class="sxs-lookup"><span data-stu-id="b6cf7-146">Uri uri - IP address of the target device (e.g., "https://123.123.123.123" or "https://123.123.123.123:50080")</span></span>
* <span data-ttu-id="b6cf7-147">System .net. NetworkCredential-Anmelde Informationen: Benutzername/Kennwort für die Verbindung mit dem [Windows-Geräte Portal](using-the-windows-device-portal.md) auf dem Zielgerät oder Emulator.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-147">System.Net.NetworkCredential credentials - Username/password for connecting to the [Windows Device Portal](using-the-windows-device-portal.md) on the target device or emulator.</span></span> <span data-ttu-id="b6cf7-148">Wenn Sie eine Verbindung mit dem Emulator über seine lokale Adresse herstellen (z. b. 168. *.* . \*) auf demselben PC werden alle Anmelde Informationen akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-148">If you are connecting to the emulator via its local address (e.g., 168.*.*.\*) on the same PC, any credentials will be accepted.</span></span>
* <span data-ttu-id="b6cf7-149">bool normal: true für normale Priorität, false für niedrige Priorität.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-149">bool normal - True for normal priority, false for low priority.</span></span> <span data-ttu-id="b6cf7-150">In der Regel sollten Sie diese Einstellung für Testszenarien auf *true* festlegen, sodass der Test die Kontrolle übernehmen kann.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-150">You generally want to set this to *true* for test scenarios, which allows your test to take control.</span></span>  <span data-ttu-id="b6cf7-151">Der Emulator und die Windows Mixed Reality-Simulation verwenden Verbindungen mit niedriger Priorität.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-151">The emulator and Windows Mixed Reality simulation use low priority connections.</span></span>  <span data-ttu-id="b6cf7-152">Wenn Ihr Test auch eine Verbindung mit niedriger Priorität verwendet, wird die zuletzt festgelegte Verbindung gesteuert.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-152">If your test also uses a low priority connection, the most recently established connection will be in control.</span></span>
* <span data-ttu-id="b6cf7-153">System. Threading. CancellationToken Token-Token, um den asynchronen Vorgang abzubrechen.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-153">System.Threading.CancellationToken token - Token to cancel the async operation.</span></span>

<span data-ttu-id="b6cf7-154">Zweitens erstellen Sie ipertionsimulationmanager.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-154">Second you will create the IPerceptionSimulationManager.</span></span> <span data-ttu-id="b6cf7-155">Dies ist das Objekt, das Sie verwenden, um die Simulation zu steuern.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-155">This is the object you use to control simulation.</span></span> <span data-ttu-id="b6cf7-156">Beachten Sie, dass dies auch in einer Async-Methode erfolgen muss.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-156">Note that this must also be done in an async method.</span></span>

## <a name="control-the-simulated-human"></a><span data-ttu-id="b6cf7-157">Steuern des simulierten Menschen</span><span class="sxs-lookup"><span data-stu-id="b6cf7-157">Control the simulated Human</span></span>

<span data-ttu-id="b6cf7-158">Ein ipertionsimulationmanager verfügt über eine menschliche Eigenschaft, die ein isimulatedhuman-Objekt zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-158">An IPerceptionSimulationManager has a Human property that returns an ISimulatedHuman object.</span></span> <span data-ttu-id="b6cf7-159">Um den simulierten Menschen zu steuern, führen Sie Vorgänge für dieses Objekt aus.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-159">To control the simulated human, perform operations on this object.</span></span> <span data-ttu-id="b6cf7-160">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="b6cf7-160">For example:</span></span>

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a><span data-ttu-id="b6cf7-161">Einfache Beispiel C# Konsolenanwendung</span><span class="sxs-lookup"><span data-stu-id="b6cf7-161">Basic Sample C# console application</span></span>

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

## <a name="extended-sample-c-console-application"></a><span data-ttu-id="b6cf7-162">Erweiterte Beispiel C# Konsolenanwendung</span><span class="sxs-lookup"><span data-stu-id="b6cf7-162">Extended Sample C# console application</span></span>

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

## <a name="note-on-6-dof-controllers"></a><span data-ttu-id="b6cf7-163">Hinweis auf 6-DOF-Controllern</span><span class="sxs-lookup"><span data-stu-id="b6cf7-163">Note on 6-DOF controllers</span></span>

<span data-ttu-id="b6cf7-164">Vor dem Aufrufen von Eigenschaften für Methoden auf einem simulierten 6-DOF-Controller müssen Sie den Controller aktivieren.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-164">Before calling any properties on methods on a simulated 6-DOF controller, you must activate the controller.</span></span>  <span data-ttu-id="b6cf7-165">Wenn dies nicht der Fall ist, wird eine Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-165">Not doing so will result in an exception.</span></span>  <span data-ttu-id="b6cf7-166">Ab dem Windows 10-Update von Mai 2019 können simulierte 6-DOF-Controller installiert und aktiviert werden, indem die Status-Eigenschaft für das isimulatedsixdofcontroller-Objekt auf simulatedsixdofcontrollerstatus. Active festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-166">Starting with the Windows 10 May 2019 Update, simulated 6-DOF controllers can be installed and activated by setting the Status property on the ISimulatedSixDofController object to SimulatedSixDofControllerStatus.Active.</span></span>
<span data-ttu-id="b6cf7-167">Beim Windows 10-Update vom Oktober 2018 und früher müssen Sie zuerst einen simulierten 6-DOF-Controller separat installieren, indem Sie das Tool "perceptionsimulationdevice" aufrufen, das sich im Ordner "\Windows\System32" befindet.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-167">In the Windows 10 October 2018 Update and earlier, you must separately install a simulated 6-DOF controller first by calling the PerceptionSimulationDevice tool located in the \Windows\System32 folder.</span></span>  <span data-ttu-id="b6cf7-168">Die Verwendung dieses Tools ist wie folgt:</span><span class="sxs-lookup"><span data-stu-id="b6cf7-168">The usage of this tool is as follows:</span></span>


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

<span data-ttu-id="b6cf7-169">Zum Beispiel</span><span class="sxs-lookup"><span data-stu-id="b6cf7-169">For example</span></span>

```
    PerceptionSimulationDevice.exe i 6dof 1
```

<span data-ttu-id="b6cf7-170">Folgende Aktionen werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="b6cf7-170">Supported actions are:</span></span>
* <span data-ttu-id="b6cf7-171">i = Installation</span><span class="sxs-lookup"><span data-stu-id="b6cf7-171">i = install</span></span>
* <span data-ttu-id="b6cf7-172">q = Abfrage</span><span class="sxs-lookup"><span data-stu-id="b6cf7-172">q = query</span></span>
* <span data-ttu-id="b6cf7-173">r = entfernen</span><span class="sxs-lookup"><span data-stu-id="b6cf7-173">r = remove</span></span>

<span data-ttu-id="b6cf7-174">Unterstützte Instanzen:</span><span class="sxs-lookup"><span data-stu-id="b6cf7-174">Supported instances are:</span></span>
* <span data-ttu-id="b6cf7-175">1 = der linke 6-DOF-Controller</span><span class="sxs-lookup"><span data-stu-id="b6cf7-175">1 = the left 6-DOF controller</span></span>
* <span data-ttu-id="b6cf7-176">2 = der Rechte 6-DOF-Controller</span><span class="sxs-lookup"><span data-stu-id="b6cf7-176">2 = the right 6-DOF controller</span></span>

<span data-ttu-id="b6cf7-177">Der Exitcode des Prozesses gibt einen Erfolg (ein NULL-Rückgabewert) oder einen Fehler (ein Rückgabewert ungleich null) an.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-177">The exit code of the process will indicate success (a zero return value) or failure (a non-zero return value).</span></span>  <span data-ttu-id="b6cf7-178">Wenn Sie die Aktion "q" verwenden, um abzufragen, ob ein Controller installiert ist oder nicht, ist der Rückgabewert 0 (null), wenn der Controller nicht bereits installiert ist, oder ein (1), wenn der Controller installiert ist.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-178">When using the 'q' action to query whether or not a controller is installed, the return value will be zero (0) if the controller is not already installed or one (1) if the controller is installed.</span></span>

<span data-ttu-id="b6cf7-179">Wenn Sie einen Controller am Windows 10-Update vom Oktober 2018 oder früher entfernen, legen Sie seinen Status zuerst über die API auf OFF fest, und nennen Sie dann das Tool "perzeptionsimulationdevice".</span><span class="sxs-lookup"><span data-stu-id="b6cf7-179">When removing a controller on the Windows 10 October 2018 Update or earlier, set its status to Off via the API first, then call the PerceptionSimulationDevice tool.</span></span>

<span data-ttu-id="b6cf7-180">Beachten Sie, dass dieses Tool als Administrator ausgeführt werden muss.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-180">Note that this tool must be run as Administrator.</span></span>




## <a name="api-reference"></a><span data-ttu-id="b6cf7-181">API-Referenz</span><span class="sxs-lookup"><span data-stu-id="b6cf7-181">API Reference</span></span>

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a><span data-ttu-id="b6cf7-182">Microsoft. perceptionsimulation. simulateddebug Type</span><span class="sxs-lookup"><span data-stu-id="b6cf7-182">Microsoft.PerceptionSimulation.SimulatedDeviceType</span></span>

<span data-ttu-id="b6cf7-183">Beschreibt einen simulierten Gerätetyp.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-183">Describes a simulated device type</span></span>

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

<span data-ttu-id="b6cf7-184">**Microsoft. perceptionsimulation. simulatedtovicetype. Reference**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-184">**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**</span></span>

<span data-ttu-id="b6cf7-185">Ein fiktives Referenzgerät, der Standardwert für "perceptionsimulationmanager"</span><span class="sxs-lookup"><span data-stu-id="b6cf7-185">A fictitious reference device, the default for PerceptionSimulationManager</span></span>

### <a name="microsoftperceptionsimulationheadtrackermode"></a><span data-ttu-id="b6cf7-186">Microsoft. perceptionsimulation. headtrackermode</span><span class="sxs-lookup"><span data-stu-id="b6cf7-186">Microsoft.PerceptionSimulation.HeadTrackerMode</span></span>

<span data-ttu-id="b6cf7-187">Beschreibt einen Head Tracker-Modus.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-187">Describes a head tracker mode</span></span>

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

<span data-ttu-id="b6cf7-188">**Microsoft. perceptionsimulation. headtrackermode. Default**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-188">**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**</span></span>

<span data-ttu-id="b6cf7-189">Standard Head-Nachverfolgung.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-189">Default Head Tracking.</span></span> <span data-ttu-id="b6cf7-190">Dies bedeutet, dass das System basierend auf den Lauf Zeit Bedingungen den besten Head-nach Verfolgungs Modus auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-190">This means the system may select the best head tracking mode based upon runtime conditions.</span></span>

<span data-ttu-id="b6cf7-191">**Microsoft. perceptionsimulation. headtrackermode. Orientation**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-191">**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**</span></span>

<span data-ttu-id="b6cf7-192">Nur Ausrichtung Head Tracking.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-192">Orientation Only Head Tracking.</span></span> <span data-ttu-id="b6cf7-193">Dies bedeutet, dass die nach verfolgte Position möglicherweise nicht zuverlässig ist und einige Funktionen, die von der Head-Position abhängig sind, möglicherweise nicht verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-193">This means that the tracked position may not be reliable, and some functionality dependent on head position may not be available.</span></span>

<span data-ttu-id="b6cf7-194">**Microsoft. perceptionsimulation. headtrackermode. Position**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-194">**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**</span></span>

<span data-ttu-id="b6cf7-195">Nachverfolgung von positionellen Köpfen.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-195">Positional Head Tracking.</span></span> <span data-ttu-id="b6cf7-196">Dies bedeutet, dass die Position und Ausrichtung der überwachten Kopfzeile zuverlässig sind.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-196">This means that the tracked head position and orientation are both reliable</span></span>

### <a name="microsoftperceptionsimulationsimulatedgesture"></a><span data-ttu-id="b6cf7-197">Microsoft. perceptionsimulation. simulatedgesten</span><span class="sxs-lookup"><span data-stu-id="b6cf7-197">Microsoft.PerceptionSimulation.SimulatedGesture</span></span>

<span data-ttu-id="b6cf7-198">Beschreibt eine simulierte Geste</span><span class="sxs-lookup"><span data-stu-id="b6cf7-198">Describes a simulated gesture</span></span>

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

<span data-ttu-id="b6cf7-199">**Microsoft. perceptionsimulation. simulatedgesten. None**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-199">**Microsoft.PerceptionSimulation.SimulatedGesture.None**</span></span>

<span data-ttu-id="b6cf7-200">Ein Sentinelwert, mit dem keine Gesten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-200">A sentinel value used to indicate no gestures.</span></span>

<span data-ttu-id="b6cf7-201">**Microsoft. perceptionsimulation. simulatedgesten. fingerpressed**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-201">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**</span></span>

<span data-ttu-id="b6cf7-202">Eine gedrückte Stift Bewegung.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-202">A finger pressed gesture.</span></span>

<span data-ttu-id="b6cf7-203">**Microsoft. perceptionsimulation. simulatedgesten. fingerreleased**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-203">**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**</span></span>

<span data-ttu-id="b6cf7-204">Eine von Fingern freigegebene Geste.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-204">A finger released gesture.</span></span>

<span data-ttu-id="b6cf7-205">**Microsoft. perceptionsimulation. simulatedgesten. Home**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-205">**Microsoft.PerceptionSimulation.SimulatedGesture.Home**</span></span>

<span data-ttu-id="b6cf7-206">Die "Home/System"-Geste.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-206">The home/system gesture.</span></span>

<span data-ttu-id="b6cf7-207">**Microsoft. perceptionsimulation. simulatedgesten. Max**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-207">**Microsoft.PerceptionSimulation.SimulatedGesture.Max**</span></span>

<span data-ttu-id="b6cf7-208">Die maximale gültige Geste.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-208">The maximum valid gesture.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a><span data-ttu-id="b6cf7-209">Microsoft. perceptionsimulation. simulatedsixdofcontrollerstatus</span><span class="sxs-lookup"><span data-stu-id="b6cf7-209">Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus</span></span>

<span data-ttu-id="b6cf7-210">Die möglichen Zustände eines simulierten 6-DOF-Controllers.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-210">The possible states of a simulated 6-DOF controller.</span></span>

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

<span data-ttu-id="b6cf7-211">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerstatus. Off**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-211">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**</span></span>

<span data-ttu-id="b6cf7-212">Der 6-DOF-Controller ist ausgeschaltet.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-212">The 6-DOF controller is turned off.</span></span>

<span data-ttu-id="b6cf7-213">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerstatus. Active**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-213">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**</span></span>

<span data-ttu-id="b6cf7-214">Der 6-DOF-Controller ist eingeschaltet und wird nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-214">The 6-DOF controller is turned on and tracked.</span></span>

<span data-ttu-id="b6cf7-215">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerstatus. trackinglost**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-215">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**</span></span>

<span data-ttu-id="b6cf7-216">Der 6-DOF-Controller ist eingeschaltet, kann aber nicht nachverfolgt werden.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-216">The 6-DOF controller is turned on but cannot be tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a><span data-ttu-id="b6cf7-217">Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton</span><span class="sxs-lookup"><span data-stu-id="b6cf7-217">Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton</span></span>

<span data-ttu-id="b6cf7-218">Die unterstützten Schaltflächen auf einem simulierten 6-DOF-Controller.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-218">The supported buttons on a simulated 6-DOF controller.</span></span>

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

<span data-ttu-id="b6cf7-219">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. None**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-219">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**</span></span>

<span data-ttu-id="b6cf7-220">Ein Sentinelwert, mit dem keine Schaltflächen angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-220">A sentinel value used to indicate no buttons.</span></span>

<span data-ttu-id="b6cf7-221">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. Home**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-221">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**</span></span>

<span data-ttu-id="b6cf7-222">Die Start Schaltfläche wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-222">The Home button is pressed.</span></span>

<span data-ttu-id="b6cf7-223">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. Menu**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-223">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**</span></span>

<span data-ttu-id="b6cf7-224">Die Menü Schaltfläche wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-224">The Menu button is pressed.</span></span>

<span data-ttu-id="b6cf7-225">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. Grip**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-225">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**</span></span>

<span data-ttu-id="b6cf7-226">Die Zieh Fläche wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-226">The Grip button is pressed.</span></span>

<span data-ttu-id="b6cf7-227">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. touchpadpress**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-227">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**</span></span>

<span data-ttu-id="b6cf7-228">Der Touchpad ist gedrückt.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-228">The TouchPad is pressed.</span></span>

<span data-ttu-id="b6cf7-229">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. Select**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-229">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**</span></span>

<span data-ttu-id="b6cf7-230">Die Schaltfläche auswählen wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-230">The Select button is pressed.</span></span>

<span data-ttu-id="b6cf7-231">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. touchpadtouch**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-231">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**</span></span>

<span data-ttu-id="b6cf7-232">Das Touchpad ist berührt.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-232">The TouchPad is touched.</span></span>

<span data-ttu-id="b6cf7-233">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. Thumbstick**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-233">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**</span></span>

<span data-ttu-id="b6cf7-234">Der Finger Stick wird gedrückt.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-234">The Thumbstick is pressed.</span></span>

<span data-ttu-id="b6cf7-235">**Microsoft. perceptionsimulation. simulatedsixdofcontrollerbutton. Max**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-235">**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**</span></span>

<span data-ttu-id="b6cf7-236">Die maximale gültige Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-236">The maximum valid button.</span></span>


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a><span data-ttu-id="b6cf7-237">Microsoft. perceptionsimulation. simulatedeyescalibrationstate</span><span class="sxs-lookup"><span data-stu-id="b6cf7-237">Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState</span></span>

<span data-ttu-id="b6cf7-238">Der Kalibrierungs Zustand der simulierten Augen</span><span class="sxs-lookup"><span data-stu-id="b6cf7-238">The calibration state of the simulated eyes</span></span>

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

<span data-ttu-id="b6cf7-239">**Microsoft. perceptionsimulation. simulatedeyescalibrationstate. nicht verfügbar**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-239">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**</span></span>

<span data-ttu-id="b6cf7-240">Die Augen-Kalibrierung ist nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-240">The eyes calibration is unavailable.</span></span>

<span data-ttu-id="b6cf7-241">**Microsoft. perceptionsimulation. simulatedeyescalibrationstate. Ready**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-241">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**</span></span>

<span data-ttu-id="b6cf7-242">Die Augen wurden gekalibriert.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-242">The eyes have been calibrated.</span></span>  <span data-ttu-id="b6cf7-243">Dies ist der Standardwert.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-243">This is the default value.</span></span>

<span data-ttu-id="b6cf7-244">**Microsoft. perceptionsimulation. simulatedeyescalibrationstate. konfiguriert**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-244">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Configuring**</span></span>

<span data-ttu-id="b6cf7-245">Die Augen werden gerade gekalibriert.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-245">The eyes are being calibrated.</span></span>

<span data-ttu-id="b6cf7-246">**Microsoft. perceptionsimulation. simulatedeyescalibrationstate. usercalibrationbenötigte**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-246">**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**</span></span>

<span data-ttu-id="b6cf7-247">Die Augen müssen kalibriert werden.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-247">The eyes need to be calibrated.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a><span data-ttu-id="b6cf7-248">Microsoft. perceptionsimulation. simulatedhandjointtrackingaccuracy</span><span class="sxs-lookup"><span data-stu-id="b6cf7-248">Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy</span></span>

<span data-ttu-id="b6cf7-249">Die nach Verfolgungs Genauigkeit einer gemeinsamen Hand.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-249">The tracking accuracy of a joint of the hand.</span></span>

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

<span data-ttu-id="b6cf7-250">**Microsoft. perceptionsimulation. simulatedhandjointtrackingaccuracy. nicht verfügbar**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-250">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**</span></span>

<span data-ttu-id="b6cf7-251">Das gemeinsame wird nicht nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-251">The joint is not tracked.</span></span>

<span data-ttu-id="b6cf7-252">**Microsoft. perceptionsimulation. simulatedhandjointtrackingaccuracy. ungefähre**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-252">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**</span></span>

<span data-ttu-id="b6cf7-253">Die gemeinsame Position wird abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-253">The joint position is inferred.</span></span>

<span data-ttu-id="b6cf7-254">**Microsoft. perceptionsimulation. simulatedhandjointtrackingaccuracy. Visible**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-254">**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**</span></span>

<span data-ttu-id="b6cf7-255">Das gemeinsame ist vollständig nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-255">The joint is fully tracked.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a><span data-ttu-id="b6cf7-256">Microsoft. perceptionsimulation. simulatedhandpose</span><span class="sxs-lookup"><span data-stu-id="b6cf7-256">Microsoft.PerceptionSimulation.SimulatedHandPose</span></span>

<span data-ttu-id="b6cf7-257">Die nach Verfolgungs Genauigkeit einer gemeinsamen Hand.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-257">The tracking accuracy of a joint of the hand.</span></span>

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

<span data-ttu-id="b6cf7-258">**Microsoft. perceptionsimulation. simulatedhandpose. Closed**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-258">**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**</span></span>

<span data-ttu-id="b6cf7-259">Die Fingergelenke der Hand werden so konfiguriert, dass Sie eine geschlossene Darstellung widerspiegeln.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-259">The hand's finger joints are configured to reflect a closed pose.</span></span>

<span data-ttu-id="b6cf7-260">**Microsoft. perceptionsimulation. simulatedhandpose. Open**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-260">**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**</span></span>

<span data-ttu-id="b6cf7-261">Die Fingergelenke der Hand werden so konfiguriert, dass Sie eine offene Pose widerspiegeln.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-261">The hand's finger joints are configured to reflect an open pose.</span></span>

<span data-ttu-id="b6cf7-262">**Microsoft. perceptionsimulation. simulatedhandpose. Point**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-262">**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**</span></span>

<span data-ttu-id="b6cf7-263">Die Fingergelenke der Hand werden so konfiguriert, dass Sie eine Zeige Darstellung widerspiegeln.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-263">The hand's finger joints are configured to reflect a pointing pose.</span></span>

<span data-ttu-id="b6cf7-264">**Microsoft. perceptionsimulation. simulatedhandpose. Pinch**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-264">**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**</span></span>

<span data-ttu-id="b6cf7-265">Die Fingergelenke der Hand werden so konfiguriert, dass Sie eine zusammendrücken-Pose widerspiegeln.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-265">The hand's finger joints are configured to reflect a pinching pose.</span></span>

<span data-ttu-id="b6cf7-266">**Microsoft. perceptionsimulation. simulatedhandpose. Max**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-266">**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**</span></span>

<span data-ttu-id="b6cf7-267">Der maximale gültige Wert für simulatedhandpose.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-267">The maximum valid value for SimulatedHandPose.</span></span>


### <a name="microsoftperceptionsimulationplaybackstate"></a><span data-ttu-id="b6cf7-268">Microsoft. perceptionsimulation. playbackstate</span><span class="sxs-lookup"><span data-stu-id="b6cf7-268">Microsoft.PerceptionSimulation.PlaybackState</span></span>

<span data-ttu-id="b6cf7-269">Beschreibt den Zustand einer Wiedergabe.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-269">Describes the state of a playback.</span></span>

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

<span data-ttu-id="b6cf7-270">**Microsoft. perceptionsimulation. playbackstate. beendet**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-270">**Microsoft.PerceptionSimulation.PlaybackState.Stopped**</span></span>

<span data-ttu-id="b6cf7-271">Die Aufzeichnung ist zurzeit beendet und ist für die Wiedergabe bereit.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-271">The recording is currently stopped and ready for playback.</span></span>

<span data-ttu-id="b6cf7-272">**Microsoft. perceptionsimulation. playbackstate. Play**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-272">**Microsoft.PerceptionSimulation.PlaybackState.Playing**</span></span>

<span data-ttu-id="b6cf7-273">Die Aufzeichnung wird zurzeit wiedergegeben.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-273">The recording is currently playing.</span></span>

<span data-ttu-id="b6cf7-274">**Microsoft. perceptionsimulation. playbackstate. angehalten**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-274">**Microsoft.PerceptionSimulation.PlaybackState.Paused**</span></span>

<span data-ttu-id="b6cf7-275">Die Aufzeichnung ist derzeit angehalten.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-275">The recording is currently paused.</span></span>

<span data-ttu-id="b6cf7-276">**Microsoft. perceptionsimulation. playbackstate. End**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-276">**Microsoft.PerceptionSimulation.PlaybackState.End**</span></span>

<span data-ttu-id="b6cf7-277">Die Aufzeichnung hat das Ende erreicht.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-277">The recording has reached the end.</span></span>

### <a name="microsoftperceptionsimulationvector3"></a><span data-ttu-id="b6cf7-278">Microsoft. perceptionsimulation. Vector3</span><span class="sxs-lookup"><span data-stu-id="b6cf7-278">Microsoft.PerceptionSimulation.Vector3</span></span>

<span data-ttu-id="b6cf7-279">Beschreibt einen 3-Komponenten Vektor, der einen Punkt oder einen Vektor im 3D-Raum beschreiben könnte.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-279">Describes a 3 components vector, which might describe a point or a vector in 3D space.</span></span>

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

<span data-ttu-id="b6cf7-280">**Microsoft. perceptionsimulation. Vector3. X**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-280">**Microsoft.PerceptionSimulation.Vector3.X**</span></span>

<span data-ttu-id="b6cf7-281">Die X-Komponente des Vektors.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-281">The X component of the vector.</span></span>

<span data-ttu-id="b6cf7-282">**Microsoft. perceptionsimulation. Vector3. Y**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-282">**Microsoft.PerceptionSimulation.Vector3.Y**</span></span>

<span data-ttu-id="b6cf7-283">Die Y-Komponente des Vektors.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-283">The Y component of the vector.</span></span>

<span data-ttu-id="b6cf7-284">**Microsoft. perceptionsimulation. Vector3. Z**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-284">**Microsoft.PerceptionSimulation.Vector3.Z**</span></span>

<span data-ttu-id="b6cf7-285">Die Z-Komponente des Vektors.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-285">The Z component of the vector.</span></span>

<span data-ttu-id="b6cf7-286">**Microsoft. perceptionsimulation. Vector3. #ctor (System. Single, System. Single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-286">**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="b6cf7-287">Erstellen Sie eine neue Vector3.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-287">Construct a new Vector3.</span></span>

<span data-ttu-id="b6cf7-288">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6cf7-288">Parameters</span></span>
* <span data-ttu-id="b6cf7-289">x: die x-Komponente des Vektors.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-289">x - The x component of the vector.</span></span>
* <span data-ttu-id="b6cf7-290">y: die y-Komponente des Vektors.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-290">y - The y component of the vector.</span></span>
* <span data-ttu-id="b6cf7-291">z-die z-Komponente des Vektors.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-291">z - The z component of the vector.</span></span>

### <a name="microsoftperceptionsimulationrotation3"></a><span data-ttu-id="b6cf7-292">Microsoft. perceptionsimulation. Rotation3</span><span class="sxs-lookup"><span data-stu-id="b6cf7-292">Microsoft.PerceptionSimulation.Rotation3</span></span>

<span data-ttu-id="b6cf7-293">Beschreibt eine 3-Komponenten Rotation.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-293">Describes a 3 components rotation.</span></span>

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

<span data-ttu-id="b6cf7-294">**Microsoft. perceptionsimulation. Rotation3. Pitch**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-294">**Microsoft.PerceptionSimulation.Rotation3.Pitch**</span></span>

<span data-ttu-id="b6cf7-295">Die Tonkomponente der Drehung um die X-Achse.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-295">The Pitch component of the Rotation, down around the X axis.</span></span>

<span data-ttu-id="b6cf7-296">**Microsoft. perceptionsimulation. Rotation3. Yaw**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-296">**Microsoft.PerceptionSimulation.Rotation3.Yaw**</span></span>

<span data-ttu-id="b6cf7-297">Die GW-Komponente der Drehung, direkt um die Y-Achse.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-297">The Yaw component of the Rotation, right around the Y axis.</span></span>

<span data-ttu-id="b6cf7-298">**Microsoft. perceptionsimulation. Rotation3. Roll**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-298">**Microsoft.PerceptionSimulation.Rotation3.Roll**</span></span>

<span data-ttu-id="b6cf7-299">Die rollenkomponente der Drehung, direkt um die Z-Achse.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-299">The Roll component of the Rotation, right around the Z axis.</span></span>

<span data-ttu-id="b6cf7-300">**Microsoft. perceptionsimulation. Rotation3. #ctor (System. Single, System. Single, System. Single)**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-300">**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single,System.Single,System.Single)**</span></span>

<span data-ttu-id="b6cf7-301">Erstellen Sie eine neue Rotation3.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-301">Construct a new Rotation3.</span></span>

<span data-ttu-id="b6cf7-302">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6cf7-302">Parameters</span></span>
* <span data-ttu-id="b6cf7-303">Pitch: die Tonkomponente der Drehung.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-303">pitch - The pitch component of the Rotation.</span></span>
* <span data-ttu-id="b6cf7-304">Yaw-die Yaw-Komponente der Drehung.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-304">yaw - The yaw component of the Rotation.</span></span>
* <span data-ttu-id="b6cf7-305">Rollup der rollforwardkomponente der Drehung.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-305">roll - The roll component of the Rotation.</span></span>

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a><span data-ttu-id="b6cf7-306">Microsoft. perceptionsimulation. simulatedhandjointconfiguration</span><span class="sxs-lookup"><span data-stu-id="b6cf7-306">Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration</span></span>

<span data-ttu-id="b6cf7-307">Beschreibt die Konfiguration einer zusammenhängenden in einer simulierten Hand.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-307">Describes the configuration of a joint on a simulated hand.</span></span>

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

<span data-ttu-id="b6cf7-308">**Microsoft. perceptionsimulation. simulatedhandjointconfiguration. Position**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-308">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**</span></span>

<span data-ttu-id="b6cf7-309">Die Position des gemeinsamen.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-309">The position of the joint.</span></span>

<span data-ttu-id="b6cf7-310">**Microsoft. perceptionsimulation. simulatedhandjointconfiguration. Rotation**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-310">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**</span></span>

<span data-ttu-id="b6cf7-311">Die Drehung der gemeinsam.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-311">The rotation of the joint.</span></span>

<span data-ttu-id="b6cf7-312">**Microsoft. perceptionsimulation. simulatedhandjointconfiguration. trackingaccuracy**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-312">**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**</span></span>

<span data-ttu-id="b6cf7-313">Die nach Verfolgungs Genauigkeit der gemeinsamen.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-313">The tracking accuracy of the joint.</span></span>


### <a name="microsoftperceptionsimulationfrustum"></a><span data-ttu-id="b6cf7-314">Microsoft. perceptionsimulation. Frustum</span><span class="sxs-lookup"><span data-stu-id="b6cf7-314">Microsoft.PerceptionSimulation.Frustum</span></span>

<span data-ttu-id="b6cf7-315">Beschreibt eine Ansicht, wie Sie in der Regel von einer Kamera verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-315">Describes a view frustum, as typically used by a camera.</span></span>

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

<span data-ttu-id="b6cf7-316">**Microsoft. perceptionsimulation. Frustum. Near**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-316">**Microsoft.PerceptionSimulation.Frustum.Near**</span></span>

<span data-ttu-id="b6cf7-317">Der Mindestabstand, der in der Frustum-Klasse enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-317">The minimum distance that is contained in the frustum.</span></span>

<span data-ttu-id="b6cf7-318">**Microsoft. perceptionsimulation. Frustum. Far**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-318">**Microsoft.PerceptionSimulation.Frustum.Far**</span></span>

<span data-ttu-id="b6cf7-319">Der maximale Abstand, der in der Frustum-Klasse enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-319">The maximum distance that is contained in the frustum.</span></span>

<span data-ttu-id="b6cf7-320">**Microsoft. perceptionsimulation. Frustum. fieldofiview**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-320">**Microsoft.PerceptionSimulation.Frustum.FieldOfView**</span></span>

<span data-ttu-id="b6cf7-321">Das horizontale Feld der Ansicht des Frustum im Bogenmaße (kleiner als PI).</span><span class="sxs-lookup"><span data-stu-id="b6cf7-321">The horizontal field of view of the frustum, in radians (less than PI).</span></span>

<span data-ttu-id="b6cf7-322">**Microsoft. perceptionsimulation. Frustum. AspectRatio**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-322">**Microsoft.PerceptionSimulation.Frustum.AspectRatio**</span></span>

<span data-ttu-id="b6cf7-323">Das Verhältnis des horizontalen Sicht Felds zum vertikalen Sichtfeld.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-323">The ratio of horizontal field of view to vertical field of view.</span></span>

### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a><span data-ttu-id="b6cf7-324">Microsoft. perceptionsimulation. ipertionsimulationmanager</span><span class="sxs-lookup"><span data-stu-id="b6cf7-324">Microsoft.PerceptionSimulation.IPerceptionSimulationManager</span></span>

<span data-ttu-id="b6cf7-325">Der Stamm zum Erstellen der zum Steuern eines Geräts verwendeten Pakete.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-325">Root for generating the packets used to control a device.</span></span>

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

<span data-ttu-id="b6cf7-326">**Microsoft. perceptionsimulation. ipertionsimulationmanager. Device**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-326">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**</span></span>

<span data-ttu-id="b6cf7-327">Rufen Sie das simulierte Geräte Objekt ab, das den simulierten Menschen und die simulierte Welt interpretiert.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-327">Retrieve the simulated device object that interprets the simulated human and the simulated world.</span></span>

<span data-ttu-id="b6cf7-328">**Microsoft. perceptionsimulation. ipertionsimulationmanager. Human**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-328">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**</span></span>

<span data-ttu-id="b6cf7-329">Rufen Sie das-Objekt ab, das den simulierten Menschen steuert.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-329">Retrieve the object that controls the simulated human.</span></span>

<span data-ttu-id="b6cf7-330">**Microsoft. perceptionsimulation. ipertionsimulationmanager. Reset**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-330">**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**</span></span>

<span data-ttu-id="b6cf7-331">Setzt die Simulation auf ihren Standardzustand zurück.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-331">Resets the simulation to its default state.</span></span>

### <a name="microsoftperceptionsimulationisimulateddevice"></a><span data-ttu-id="b6cf7-332">Microsoft. perceptionsimulation. isimulateddevice</span><span class="sxs-lookup"><span data-stu-id="b6cf7-332">Microsoft.PerceptionSimulation.ISimulatedDevice</span></span>

<span data-ttu-id="b6cf7-333">Schnittstelle, die das Gerät beschreibt, das die simulierte Welt und den simulierten Menschen interpretiert</span><span class="sxs-lookup"><span data-stu-id="b6cf7-333">Interface describing the device which interprets the simulated world and the simulated human</span></span>

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

<span data-ttu-id="b6cf7-334">**Microsoft. perceptionsimulation. isimulateddevice. headtracker**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-334">**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**</span></span>

<span data-ttu-id="b6cf7-335">Rufen Sie den Head Tracker vom simulierten Gerät ab.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-335">Retrieve the Head Tracker from the Simulated Device.</span></span>

<span data-ttu-id="b6cf7-336">**Microsoft. perceptionsimulation. isimulateddevice. Handtracker**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-336">**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**</span></span>

<span data-ttu-id="b6cf7-337">Rufen Sie die Hand Verfolgung vom simulierten Gerät ab.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-337">Retrieve the Hand Tracker from the Simulated Device.</span></span>

<span data-ttu-id="b6cf7-338">**Microsoft. perceptionsimulation. isimulateddevice. setsimulatedde vicetype (Microsoft. perceptionsimulation. simulateddebug Type)**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-338">**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**</span></span>

<span data-ttu-id="b6cf7-339">Legen Sie die Eigenschaften des simulierten Geräts so fest, dass Sie dem angegebenen Gerätetyp entsprechen.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-339">Set the properties of the simulated device to match the provided device type.</span></span>

<span data-ttu-id="b6cf7-340">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6cf7-340">Parameters</span></span>
* <span data-ttu-id="b6cf7-341">Type: der neue Typ des simulierten Geräts</span><span class="sxs-lookup"><span data-stu-id="b6cf7-341">type - The new type of Simulated Device</span></span>

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a><span data-ttu-id="b6cf7-342">Microsoft. perceptionsimulation. isimulatedheadtracker</span><span class="sxs-lookup"><span data-stu-id="b6cf7-342">Microsoft.PerceptionSimulation.ISimulatedHeadTracker</span></span>

<span data-ttu-id="b6cf7-343">Schnittstelle, die den Teil des simulierten Geräts beschreibt, der die Kopfzeile des simulierten Menschen nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-343">Interface describing the portion of the simulated device that tracks the head of the simulated human.</span></span>

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

<span data-ttu-id="b6cf7-344">**Microsoft. perceptionsimulation. isimulatedheadtracker. headtrackermode**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-344">**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**</span></span>

<span data-ttu-id="b6cf7-345">Ruft den aktuellen Head-Tracker-Modus ab und legt diesen fest.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-345">Retrieves and sets the current head tracker mode.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a><span data-ttu-id="b6cf7-346">Microsoft. perceptionsimulation. isimulatedhandtracker</span><span class="sxs-lookup"><span data-stu-id="b6cf7-346">Microsoft.PerceptionSimulation.ISimulatedHandTracker</span></span>

<span data-ttu-id="b6cf7-347">Schnittstelle, die den Teil des simulierten Geräts beschreibt, der die Hände des simulierten Menschen nachverfolgt</span><span class="sxs-lookup"><span data-stu-id="b6cf7-347">Interface describing the portion of the simulated device that tracks the hands of the simulated human</span></span>

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

<span data-ttu-id="b6cf7-348">**Microsoft. perceptionsimulation. isimulatedhandtracker. worldposition**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-348">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**</span></span>

<span data-ttu-id="b6cf7-349">Rufen Sie die Position des Knotens mit der Welt in Meter ab.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-349">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="b6cf7-350">**Microsoft. perceptionsimulation. isimulatedhandtracker. Position**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-350">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**</span></span>

<span data-ttu-id="b6cf7-351">Ruft die Position der simulierten Hand Tracker relativ zum Mittelpunkt des Kopfes ab und legt diese fest.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-351">Retrieve and set the position of the simulated hand tracker, relative to the center of the head.</span></span>

<span data-ttu-id="b6cf7-352">**Microsoft. perceptionsimulation. isimulatedhandtracker. Pitch**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-352">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**</span></span>

<span data-ttu-id="b6cf7-353">Abrufen und Festlegen der nach unten gerichteten Menge der simulierten Hand Tracker.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-353">Retrieve and set the downward pitch of the simulated hand tracker.</span></span>

<span data-ttu-id="b6cf7-354">**Microsoft. perceptionsimulation. isimulatedhandtracker. frustumignored**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-354">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**</span></span>

<span data-ttu-id="b6cf7-355">Rufen Sie ab, und legen Sie fest, ob der Wert der simulierten Hand Verfolgung ignoriert wird.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-355">Retrieve and set whether the frustum of the simulated hand tracker is ignored.</span></span> <span data-ttu-id="b6cf7-356">Wenn Sie ignoriert werden, sind beide Hände immer sichtbar.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-356">When ignored, both hands are always visible.</span></span> <span data-ttu-id="b6cf7-357">Wenn Sie nicht ignoriert werden (die Standardeinstellung), sind Sie nur sichtbar, wenn Sie sich innerhalb der Frustum-Klasse des Hand Trackers befinden.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-357">When not ignored (the default) hands are only visible when they are within the frustum of the hand tracker.</span></span>

<span data-ttu-id="b6cf7-358">**Microsoft. perceptionsimulation. isimulatedhandtracker. Frustum**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-358">**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**</span></span>

<span data-ttu-id="b6cf7-359">Dient zum Abrufen und Festlegen der Frustum-Eigenschaften, mit denen bestimmt wird, ob die Hände für die simulierte Hand Verfolgung sichtbar sind.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-359">Retrieve and set the frustum properties used to determine if hands are visible to the simulated hand tracker.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman"></a><span data-ttu-id="b6cf7-360">Microsoft. perceptionsimulation. isimulatedhuman</span><span class="sxs-lookup"><span data-stu-id="b6cf7-360">Microsoft.PerceptionSimulation.ISimulatedHuman</span></span>

<span data-ttu-id="b6cf7-361">Oberfläche der obersten Ebene zum Steuern des simulierten Menschen.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-361">Top level interface for controlling the simulated human.</span></span>

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

<span data-ttu-id="b6cf7-362">**Microsoft. perceptionsimulation. isimulatedhuman. worldposition**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-362">**Microsoft.PerceptionSimulation.ISimulatedHuman.WorldPosition**</span></span>

<span data-ttu-id="b6cf7-363">Abrufen und Festlegen der Position des Knotens, der sich auf die Welt bezieht, in Meter.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-363">Retrieve and set the position of the node with relation to the world, in meters.</span></span> <span data-ttu-id="b6cf7-364">Die Position entspricht einem Punkt in der Mitte der menschlichen Füße.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-364">The position corresponds to a point at the center of the human's feet.</span></span>

<span data-ttu-id="b6cf7-365">**Microsoft. perceptionsimulation. isimulatedhuman. Direction**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-365">**Microsoft.PerceptionSimulation.ISimulatedHuman.Direction**</span></span>

<span data-ttu-id="b6cf7-366">Abrufen und Festlegen der Richtung der simulierten menschlichen Gesichter in der Welt.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-366">Retrieve and set the direction the simulated human faces in the world.</span></span> <span data-ttu-id="b6cf7-367">0 Bogenmaße steht nach unten auf der negativen Z-Achse.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-367">0 radians faces down the negative Z axis.</span></span> <span data-ttu-id="b6cf7-368">Positive Bogenmaße drehen sich um die Y-Achse im Uhrzeigersinn.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-368">Positive radians rotate clockwise about the Y axis.</span></span>

<span data-ttu-id="b6cf7-369">**Microsoft. perceptionsimulation. isimulatedhuman. Height**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-369">**Microsoft.PerceptionSimulation.ISimulatedHuman.Height**</span></span>

<span data-ttu-id="b6cf7-370">Ruft die Höhe des simulierten menschlichen in Meter ab und legt diese fest.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-370">Retrieve and set the height of the simulated human, in meters.</span></span>

<span data-ttu-id="b6cf7-371">**Microsoft. perceptionsimulation. isimulatedhuman. Lefthand**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-371">**Microsoft.PerceptionSimulation.ISimulatedHuman.LeftHand**</span></span>

<span data-ttu-id="b6cf7-372">Rufen Sie die linke Seite des simulierten Menschen ab.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-372">Retrieve the left hand of the simulated human.</span></span>

<span data-ttu-id="b6cf7-373">**Microsoft. perceptionsimulation. isimulatedhuman. rightHand**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-373">**Microsoft.PerceptionSimulation.ISimulatedHuman.RightHand**</span></span>

<span data-ttu-id="b6cf7-374">Rufen Sie die Rechte des simulierten Menschen ab.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-374">Retrieve the right hand of the simulated human.</span></span>

<span data-ttu-id="b6cf7-375">**Microsoft. perceptionsimulation. isimulatedhuman. Head**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-375">**Microsoft.PerceptionSimulation.ISimulatedHuman.Head**</span></span>

<span data-ttu-id="b6cf7-376">Rufen Sie die Kopfzeile des simulierten Menschen ab.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-376">Retrieve the head of the simulated human.</span></span>

<span data-ttu-id="b6cf7-377">**Microsoft. perceptionsimulation. isimulatedhuman. Move (Microsoft. perceptionsimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-377">**Microsoft.PerceptionSimulation.ISimulatedHuman.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="b6cf7-378">Verschieben Sie den simulierten menschlichen in Relation zur aktuellen Position in Meter.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-378">Move the simulated human relative to its current position, in meters.</span></span>

<span data-ttu-id="b6cf7-379">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6cf7-379">Parameters</span></span>
* <span data-ttu-id="b6cf7-380">Translation: die Verschiebung, die relativ zur aktuellen Position verschoben werden soll.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-380">translation - The translation to move, relative to current position.</span></span>

<span data-ttu-id="b6cf7-381">**Microsoft. perceptionsimulation. isimulatedhuman. Rotation (System. Single)**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-381">**Microsoft.PerceptionSimulation.ISimulatedHuman.Rotate(System.Single)**</span></span>

<span data-ttu-id="b6cf7-382">Drehen des simulierten menschlichen in Relation zur aktuellen Richtung, im Uhrzeigersinn um die Y-Achse</span><span class="sxs-lookup"><span data-stu-id="b6cf7-382">Rotate the simulated human relative to its current direction, clockwise about the Y axis</span></span>

<span data-ttu-id="b6cf7-383">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6cf7-383">Parameters</span></span>
* <span data-ttu-id="b6cf7-384">Bogenmaß: der Betrag für die Drehung um die Y-Achse.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-384">radians - The amount to rotate around the Y axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a><span data-ttu-id="b6cf7-385">Microsoft. perceptionsimulation. ISimulatedHuman2</span><span class="sxs-lookup"><span data-stu-id="b6cf7-385">Microsoft.PerceptionSimulation.ISimulatedHuman2</span></span>

<span data-ttu-id="b6cf7-386">Wenn Sie isimulatedhuman in ISimulatedHuman2 umwandeln, sind zusätzliche Eigenschaften verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-386">Additional properties are available by casting the ISimulatedHuman to ISimulatedHuman2</span></span>

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

<span data-ttu-id="b6cf7-387">**Microsoft. perceptionsimulation. ISimulatedHuman2. leftcontroller**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-387">**Microsoft.PerceptionSimulation.ISimulatedHuman2.LeftController**</span></span>

<span data-ttu-id="b6cf7-388">Rufen Sie den linken 6-DOF-Controller ab.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-388">Retrieve the left 6-DOF controller.</span></span>

<span data-ttu-id="b6cf7-389">**Microsoft. perceptionsimulation. ISimulatedHuman2. rightcontroller**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-389">**Microsoft.PerceptionSimulation.ISimulatedHuman2.RightController**</span></span>

<span data-ttu-id="b6cf7-390">Rufen Sie den rechten 6-DOF-Controller ab.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-390">Retrieve the right 6-DOF controller.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhand"></a><span data-ttu-id="b6cf7-391">Microsoft. perceptionsimulation. isimulatedhand</span><span class="sxs-lookup"><span data-stu-id="b6cf7-391">Microsoft.PerceptionSimulation.ISimulatedHand</span></span>

<span data-ttu-id="b6cf7-392">Schnittstelle, die eine Hand des simulierten Menschen beschreibt</span><span class="sxs-lookup"><span data-stu-id="b6cf7-392">Interface describing a hand of the simulated human</span></span>

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

<span data-ttu-id="b6cf7-393">**Microsoft. perceptionsimulation. isimulatedhand. worldposition**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-393">**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**</span></span>

<span data-ttu-id="b6cf7-394">Rufen Sie die Position des Knotens mit der Welt in Meter ab.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-394">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="b6cf7-395">**Microsoft. perceptionsimulation. isimulatedhand. Position**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-395">**Microsoft.PerceptionSimulation.ISimulatedHand.Position**</span></span>

<span data-ttu-id="b6cf7-396">Abrufen und Festlegen der Position der simulierten Hand in Relation zum menschlichen Wert in Meter.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-396">Retrieve and set the position of the simulated hand relative to the human, in meters.</span></span>

<span data-ttu-id="b6cf7-397">**Microsoft. perceptionsimulation. isimulatedhand. aktiviert**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-397">**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**</span></span>

<span data-ttu-id="b6cf7-398">Rufen Sie ab, und legen Sie fest, ob die Hand aktuell aktiviert ist</span><span class="sxs-lookup"><span data-stu-id="b6cf7-398">Retrieve and set whether the hand is currently activated.</span></span>

<span data-ttu-id="b6cf7-399">**Microsoft. perceptionsimulation. isimulatedhand. Visible**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-399">**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**</span></span>

<span data-ttu-id="b6cf7-400">Ruft ab, ob die Hand derzeit für simulateddevice sichtbar ist (d. h., ob Sie sich in einer von der Handtracker erkannten Position befindet).</span><span class="sxs-lookup"><span data-stu-id="b6cf7-400">Retrieve whether the hand is currently visible to the SimulatedDevice (ie, whether it's in a position to be detected by the HandTracker).</span></span>

<span data-ttu-id="b6cf7-401">**Microsoft. perceptionsimulation. isimulatedhand. EnsureVisible**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-401">**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**</span></span>

<span data-ttu-id="b6cf7-402">Verschieben Sie die Hand so, dass Sie für simulateddevice sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-402">Move the hand such that it is visible to the SimulatedDevice.</span></span>

<span data-ttu-id="b6cf7-403">**Microsoft. perceptionsimulation. isimulatedhand. Move (Microsoft. perceptionsimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-403">**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="b6cf7-404">Verschiebt die Position der simulierten Hand in Relation zur aktuellen Position in Meter.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-404">Move the position of the simulated hand relative to its current position, in meters.</span></span>

<span data-ttu-id="b6cf7-405">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6cf7-405">Parameters</span></span>
* <span data-ttu-id="b6cf7-406">Translation: der Betrag, um den die simulierte Hand übersetzt werden soll.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-406">translation - The amount to translate the simulated hand.</span></span>

<span data-ttu-id="b6cf7-407">**Microsoft. perceptionsimulation. isimulatedhand. performgesten (Microsoft. perceptionsimulation. simulatedgesten)**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-407">**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**</span></span>

<span data-ttu-id="b6cf7-408">Führt eine Geste mithilfe der simulierten Hand aus.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-408">Perform a gesture using the simulated hand.</span></span>  <span data-ttu-id="b6cf7-409">Sie wird nur vom System erkannt, wenn die Hand aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-409">It will only be detected by the system if the hand is enabled.</span></span>

<span data-ttu-id="b6cf7-410">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6cf7-410">Parameters</span></span>
* <span data-ttu-id="b6cf7-411">Geste: die auszuführende Geste.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-411">gesture - The gesture to perform.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand2"></a><span data-ttu-id="b6cf7-412">Microsoft. perceptionsimulation. ISimulatedHand2</span><span class="sxs-lookup"><span data-stu-id="b6cf7-412">Microsoft.PerceptionSimulation.ISimulatedHand2</span></span>

<span data-ttu-id="b6cf7-413">Weitere Eigenschaften werden durch Umwandeln von isimulatedhand in ISimulatedHand2 verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-413">Additional properties are available by casting an ISimulatedHand to ISimulatedHand2.</span></span>
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

<span data-ttu-id="b6cf7-414">**Microsoft. perceptionsimulation. ISimulatedHand2. Orientation**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-414">**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**</span></span>

<span data-ttu-id="b6cf7-415">Ruft die Drehung der simulierten Hand ab oder legt Sie fest.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-415">Retrieve or set the rotation of the simulated hand.</span></span>  <span data-ttu-id="b6cf7-416">Bei der Betrachtung der Achse wird der Uhrzeigersinn im Uhrzeigersinn gedreht.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-416">Positive radians rotate clockwise when looking along the axis.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhand3"></a><span data-ttu-id="b6cf7-417">Microsoft. perceptionsimulation. ISimulatedHand3</span><span class="sxs-lookup"><span data-stu-id="b6cf7-417">Microsoft.PerceptionSimulation.ISimulatedHand3</span></span>

<span data-ttu-id="b6cf7-418">Weitere Eigenschaften werden durch Umwandeln von isimulatedhand in ISimulatedHand3 verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-418">Additional properties are available by casting an ISimulatedHand to ISimulatedHand3</span></span>
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

<span data-ttu-id="b6cf7-419">**Microsoft. perceptionsimulation. ISimulatedHand3. getjointconfiguration**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-419">**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**</span></span>

<span data-ttu-id="b6cf7-420">Die gemeinsame Konfiguration für die angegebene Verbindung wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-420">Get the joint configuration for the specified joint.</span></span>

<span data-ttu-id="b6cf7-421">**Microsoft. perceptionsimulation. ISimulatedHand3. setjointconfiguration**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-421">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**</span></span>

<span data-ttu-id="b6cf7-422">Legen Sie die gemeinsame Konfiguration für die angegebene Verbindung fest.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-422">Set the joint configuration for the specified joint.</span></span>

<span data-ttu-id="b6cf7-423">**Microsoft. perceptionsimulation. ISimulatedHand3. ".**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-423">**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**</span></span>

<span data-ttu-id="b6cf7-424">Legen Sie die Hand auf eine bekannte Pose mit einem optionalen Flag zum Animieren fest.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-424">Set the hand to a known pose with an optional flag to animate.</span></span>  <span data-ttu-id="b6cf7-425">Hinweis: das Animieren führt nicht dazu, dass die Gelenke sofort ihre abschließenden gemeinsamen Konfigurationen widerspiegeln.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-425">Note: animating won't result in joints immediately reflecting their final joint configurations.</span></span>


### <a name="microsoftperceptionsimulationisimulatedhead"></a><span data-ttu-id="b6cf7-426">Microsoft. perceptionsimulation. isimulatedhead</span><span class="sxs-lookup"><span data-stu-id="b6cf7-426">Microsoft.PerceptionSimulation.ISimulatedHead</span></span>

<span data-ttu-id="b6cf7-427">Schnittstelle, die den Anfang des simulierten Menschen beschreibt.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-427">Interface describing the head of the simulated human.</span></span>

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

<span data-ttu-id="b6cf7-428">**Microsoft. perceptionsimulation. isimulatedhead. worldposition**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-428">**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**</span></span>

<span data-ttu-id="b6cf7-429">Rufen Sie die Position des Knotens mit der Welt in Meter ab.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-429">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="b6cf7-430">**Microsoft. perceptionsimulation. isimulatedhead. Rotation**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-430">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**</span></span>

<span data-ttu-id="b6cf7-431">Ruft die Drehung des simulierten Kopfes ab.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-431">Retrieve the rotation of the simulated head.</span></span> <span data-ttu-id="b6cf7-432">Bei der Betrachtung der Achse wird der Uhrzeigersinn im Uhrzeigersinn gedreht.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-432">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="b6cf7-433">**Microsoft. perceptionsimulation. isimulatedhead. Durchmesser**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-433">**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**</span></span>

<span data-ttu-id="b6cf7-434">Ruft den Durchmesser des simulierten Kopfes ab.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-434">Retrieve the simulated head's diameter.</span></span> <span data-ttu-id="b6cf7-435">Dieser Wert wird verwendet, um den Mittelpunkt (Punkt der Drehung) zu bestimmen.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-435">This value is used to determine the head's center (point of rotation).</span></span>

<span data-ttu-id="b6cf7-436">**Microsoft. perceptionsimulation. isimulatedhead. Rotation (Microsoft. perceptionsimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-436">**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="b6cf7-437">Drehen Sie den simulierten Kopf in Relation zur aktuellen Drehung.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-437">Rotate the simulated head relative to its current rotation.</span></span> <span data-ttu-id="b6cf7-438">Bei der Betrachtung der Achse wird der Uhrzeigersinn im Uhrzeigersinn gedreht.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-438">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="b6cf7-439">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6cf7-439">Parameters</span></span>
* <span data-ttu-id="b6cf7-440">Rotation: die Menge, die gedreht werden soll.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-440">rotation - The amount to rotate.</span></span>

### <a name="microsoftperceptionsimulationisimulatedhead2"></a><span data-ttu-id="b6cf7-441">Microsoft. perceptionsimulation. ISimulatedHead2</span><span class="sxs-lookup"><span data-stu-id="b6cf7-441">Microsoft.PerceptionSimulation.ISimulatedHead2</span></span>

<span data-ttu-id="b6cf7-442">Weitere Eigenschaften sind verfügbar, indem ein isimulatedhead-Element in ISimulatedHead2 umgewandelt wird.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-442">Additional properties are available by casting an ISimulatedHead to ISimulatedHead2</span></span>

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

<span data-ttu-id="b6cf7-443">**Microsoft. perceptionsimulation. ISimulatedHead2. Eyes**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-443">**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**</span></span>

<span data-ttu-id="b6cf7-444">Rufen Sie die Augen des simulierten Menschen ab.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-444">Retrieve the eyes of the simulated human.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a><span data-ttu-id="b6cf7-445">Microsoft. perceptionsimulation. isimulatedsixdofcontroller</span><span class="sxs-lookup"><span data-stu-id="b6cf7-445">Microsoft.PerceptionSimulation.ISimulatedSixDofController</span></span>

<span data-ttu-id="b6cf7-446">Eine Schnittstelle, die einen dem simulierten Menschen zugeordneten 6-DOF-Controller beschreibt.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-446">Interface describing a 6-DOF controller associated with the simulated human.</span></span>

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

<span data-ttu-id="b6cf7-447">**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. worldposition**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-447">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**</span></span>

<span data-ttu-id="b6cf7-448">Rufen Sie die Position des Knotens mit der Welt in Meter ab.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-448">Retrieve the position of the node with relation to the world, in meters.</span></span>

<span data-ttu-id="b6cf7-449">**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. Status**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-449">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**</span></span>

<span data-ttu-id="b6cf7-450">Ruft den aktuellen Zustand des Controllers ab oder legt ihn fest.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-450">Retrieve or set the current state of the controller.</span></span>  <span data-ttu-id="b6cf7-451">Der Controller Status muss auf einen anderen Wert als "Off" festgelegt werden, bevor Aufrufe zum Verschieben, drehen oder Drücken von Schaltflächen erfolgreich ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-451">The controller status must be set to a value other than Off before any calls to move, rotate or press buttons will succeed.</span></span>

<span data-ttu-id="b6cf7-452">**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. Position**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-452">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**</span></span>

<span data-ttu-id="b6cf7-453">Ruft die Position des simulierten Controllers in Relation zum menschlichen in Meter ab oder legt diese fest.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-453">Retrieve or set the position of the simulated controller relative to the human, in meters.</span></span>

<span data-ttu-id="b6cf7-454">**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. Orientation**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-454">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**</span></span>

<span data-ttu-id="b6cf7-455">Ruft die Ausrichtung des simulierten Controllers ab oder legt Sie fest.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-455">Retrieve or set the orientation of the simulated controller.</span></span>

<span data-ttu-id="b6cf7-456">**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. Move (Microsoft. perceptionsimulation. Vector3)**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-456">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**</span></span>

<span data-ttu-id="b6cf7-457">Verschiebt die Position des simulierten Controllers relativ zu seiner aktuellen Position in Meter.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-457">Move the position of the simulated controller relative to its current position, in meters.</span></span>

<span data-ttu-id="b6cf7-458">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6cf7-458">Parameters</span></span>
* <span data-ttu-id="b6cf7-459">Translation: der Betrag, um den der simulierte Controller übersetzt werden soll.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-459">translation - The amount to translate the simulated controller.</span></span>

<span data-ttu-id="b6cf7-460">**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. pressbutton (simulatedsixdofcontrollerbutton)**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-460">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="b6cf7-461">Drücken Sie auf dem simulierten Controller eine Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-461">Press a button on the simulated controller.</span></span>  <span data-ttu-id="b6cf7-462">Sie wird nur vom System erkannt, wenn der Controller aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-462">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="b6cf7-463">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6cf7-463">Parameters</span></span>
* <span data-ttu-id="b6cf7-464">Schaltfläche: die Schaltfläche zum drücken.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-464">button - The button to press.</span></span>

<span data-ttu-id="b6cf7-465">**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. releasebutton (simulatedsixdofcontrollerbutton)**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-465">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**</span></span>

<span data-ttu-id="b6cf7-466">Gibt eine Schaltfläche auf dem simulierten Controller frei.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-466">Release a button on the simulated controller.</span></span>  <span data-ttu-id="b6cf7-467">Sie wird nur vom System erkannt, wenn der Controller aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-467">It will only be detected by the system if the controller is enabled.</span></span>

<span data-ttu-id="b6cf7-468">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6cf7-468">Parameters</span></span>
* <span data-ttu-id="b6cf7-469">Button: die Schaltfläche, die freigegeben werden soll.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-469">button - The button to release.</span></span>

<span data-ttu-id="b6cf7-470">**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. gettouchpadposition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-470">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**</span></span>

<span data-ttu-id="b6cf7-471">Die Position eines simulierten Fingers im Touchpad des simulierten Controllers erhalten.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-471">Get the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="b6cf7-472">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6cf7-472">Parameters</span></span>
* <span data-ttu-id="b6cf7-473">x: die horizontale Position des Fingers.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-473">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="b6cf7-474">y-die vertikale Position des Fingers.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-474">y - The vertical position of the finger.</span></span>

<span data-ttu-id="b6cf7-475">**Microsoft. perceptionsimulation. isimulatedsixdofcontroller. settouchpadposition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-475">**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**</span></span>

<span data-ttu-id="b6cf7-476">Legen Sie die Position eines simulierten Fingers auf dem Touchpad des simulierten Controllers fest.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-476">Set the position of a simulated finger on the simulated controller's touchpad.</span></span>

<span data-ttu-id="b6cf7-477">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6cf7-477">Parameters</span></span>
* <span data-ttu-id="b6cf7-478">x: die horizontale Position des Fingers.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-478">x - The horizontal position of the finger.</span></span>
* <span data-ttu-id="b6cf7-479">y-die vertikale Position des Fingers.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-479">y - The vertical position of the finger.</span></span>

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a><span data-ttu-id="b6cf7-480">Microsoft. perceptionsimulation. ISimulatedSixDofController2</span><span class="sxs-lookup"><span data-stu-id="b6cf7-480">Microsoft.PerceptionSimulation.ISimulatedSixDofController2</span></span>

<span data-ttu-id="b6cf7-481">Zusätzliche Eigenschaften und Methoden sind verfügbar, indem ein isimulatedsixdofcontroller in ISimulatedSixDofController2 umgewandelt wird.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-481">Additional properties and methods are available by casting an ISimulatedSixDofController to ISimulatedSixDofController2</span></span>

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

<span data-ttu-id="b6cf7-482">**Microsoft. perceptionsimulation. ISimulatedSixDofController2. getthumbstickposition (out float, out float)**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-482">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**</span></span>

<span data-ttu-id="b6cf7-483">Gibt die Position des simulierten thumbsticks auf dem simulierten Controller an.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-483">Get the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="b6cf7-484">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6cf7-484">Parameters</span></span>
* <span data-ttu-id="b6cf7-485">x: die horizontale Position des fingersticks.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-485">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="b6cf7-486">y: die vertikale Position des Finger anheften.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-486">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="b6cf7-487">**Microsoft. perceptionsimulation. ISimulatedSixDofController2. setthumbstickposition (float, float)**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-487">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**</span></span>

<span data-ttu-id="b6cf7-488">Legen Sie die Position des simulierten thumbsticks auf dem simulierten Controller fest.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-488">Set the position of the simulated thumbstick on the simulated controller.</span></span>

<span data-ttu-id="b6cf7-489">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6cf7-489">Parameters</span></span>
* <span data-ttu-id="b6cf7-490">x: die horizontale Position des fingersticks.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-490">x - The horizontal position of the thumbstick.</span></span>
* <span data-ttu-id="b6cf7-491">y: die vertikale Position des Finger anheften.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-491">y - The vertical position of the thumbstick.</span></span>

<span data-ttu-id="b6cf7-492">**Microsoft. perceptionsimulation. ISimulatedSixDofController2. Akku Level**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-492">**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**</span></span>

<span data-ttu-id="b6cf7-493">Ruft den Akku Pegel des simulierten Controllers ab oder legt ihn fest.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-493">Retrieve or set the battery level of the simulated controller.</span></span>  <span data-ttu-id="b6cf7-494">Der Wert muss größer als 0,0 und kleiner oder gleich 100,0 sein.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-494">The value must be greater than 0.0 and less than or equal to 100.0.</span></span>


### <a name="microsoftperceptionsimulationisimulatedeyes"></a><span data-ttu-id="b6cf7-495">Microsoft. perceptionsimulation. isimulatedeyes</span><span class="sxs-lookup"><span data-stu-id="b6cf7-495">Microsoft.PerceptionSimulation.ISimulatedEyes</span></span>

<span data-ttu-id="b6cf7-496">Schnittstelle, die die Augen des simulierten Menschen beschreibt.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-496">Interface describing the eyes of the simulated human.</span></span>

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

<span data-ttu-id="b6cf7-497">**Microsoft. perceptionsimulation. isimulatedeyes. Rotation**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-497">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**</span></span>

<span data-ttu-id="b6cf7-498">Ruft die Drehung der simulierten Augen ab.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-498">Retrieve the rotation of the simulated eyes.</span></span> <span data-ttu-id="b6cf7-499">Bei der Betrachtung der Achse wird der Uhrzeigersinn im Uhrzeigersinn gedreht.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-499">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="b6cf7-500">**Microsoft. perceptionsimulation. isimulatedeyes. Rotation (Microsoft. perceptionsimulation. Rotation3)**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-500">**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**</span></span>

<span data-ttu-id="b6cf7-501">Drehen der simulierten Augen in Relation zur aktuellen Drehung.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-501">Rotate the simulated eyes relative to its current rotation.</span></span> <span data-ttu-id="b6cf7-502">Bei der Betrachtung der Achse wird der Uhrzeigersinn im Uhrzeigersinn gedreht.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-502">Positive radians rotate clockwise when looking along the axis.</span></span>

<span data-ttu-id="b6cf7-503">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6cf7-503">Parameters</span></span>
* <span data-ttu-id="b6cf7-504">Rotation: die Menge, die gedreht werden soll.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-504">rotation - The amount to rotate.</span></span>

<span data-ttu-id="b6cf7-505">**Microsoft. perceptionsimulation. isimulatedeyes. calibrationstate**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-505">**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**</span></span>

<span data-ttu-id="b6cf7-506">Ruft den Kalibrierungs Zustand der simulierten Augen ab oder legt ihn fest.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-506">Retrieves or sets the calibration state of the simulated eyes.</span></span>

<span data-ttu-id="b6cf7-507">**Microsoft. perceptionsimulation. isimulatedeyes. worldposition**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-507">**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**</span></span>

<span data-ttu-id="b6cf7-508">Rufen Sie die Position des Knotens mit der Welt in Meter ab.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-508">Retrieve the position of the node with relation to the world, in meters.</span></span>


### <a name="microsoftperceptionsimulationisimulationrecording"></a><span data-ttu-id="b6cf7-509">Microsoft. perceptionsimulation. isimulationrecording</span><span class="sxs-lookup"><span data-stu-id="b6cf7-509">Microsoft.PerceptionSimulation.ISimulationRecording</span></span>

<span data-ttu-id="b6cf7-510">Schnittstelle für die Interaktion mit einer einzelnen, für die Wiedergabe geladenen Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-510">Interface for interacting with a single recording loaded for playback.</span></span>

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

<span data-ttu-id="b6cf7-511">**Microsoft. perceptionsimulation. isimulationrecording. DataTypes**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-511">**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**</span></span>

<span data-ttu-id="b6cf7-512">Ruft die Liste der Datentypen in der Aufzeichnung ab.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-512">Retrieves the list of data types in the recording.</span></span>

<span data-ttu-id="b6cf7-513">**Microsoft. perceptionsimulation. isimulationrecording. State**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-513">**Microsoft.PerceptionSimulation.ISimulationRecording.State**</span></span>

<span data-ttu-id="b6cf7-514">Ruft den aktuellen Zustand der Aufzeichnung ab.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-514">Retrieves the current state of the recording.</span></span>

<span data-ttu-id="b6cf7-515">**Microsoft. perceptionsimulation. isimulationrecording. Play**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-515">**Microsoft.PerceptionSimulation.ISimulationRecording.Play**</span></span>

<span data-ttu-id="b6cf7-516">Starten Sie die Wiedergabe.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-516">Start the playback.</span></span> <span data-ttu-id="b6cf7-517">Wenn die Aufzeichnung angehalten wurde, wird die Wiedergabe an der angehaltenen Position fortgesetzt. Wenn der Vorgang beendet ist, wird die Wiedergabe am Anfang gestartet.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-517">If the recording is paused, playback will resume from the paused location; if stopped, playback will start at the beginning.</span></span> <span data-ttu-id="b6cf7-518">Wenn Sie bereits abgespielt wird, wird dieser-Befehl ignoriert.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-518">If already playing, this call is ignored.</span></span>

<span data-ttu-id="b6cf7-519">**Microsoft. perceptionsimulation. isimulationrecording. Pause**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-519">**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**</span></span>

<span data-ttu-id="b6cf7-520">Hält die Wiedergabe an Ihrer aktuellen Position an.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-520">Pauses the playback at its current location.</span></span> <span data-ttu-id="b6cf7-521">Wenn die Aufzeichnung beendet wird, wird der-Rückruf ignoriert.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-521">If the recording is stopped, the call is ignored.</span></span>

<span data-ttu-id="b6cf7-522">**Microsoft. perceptionsimulation. isimulationrecording. Seek (System. UInt64)**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-522">**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**</span></span>

<span data-ttu-id="b6cf7-523">Sucht die Aufzeichnung bis zur angegebenen Zeit (in 100 Nanosekunden-Intervallen von Anfang an) und hält an dieser Stelle an.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-523">Seeks the recording to the specified time (in 100 nanoseconds intervals from the beginning) and pauses at that location.</span></span> <span data-ttu-id="b6cf7-524">Wenn die Uhrzeit hinter dem Ende der Aufzeichnung liegt, wird Sie im letzten Frame angehalten.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-524">If the time is beyond the end of the recording, it is paused at the last frame.</span></span>

<span data-ttu-id="b6cf7-525">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6cf7-525">Parameters</span></span>
* <span data-ttu-id="b6cf7-526">Ticks-die Zeit, nach der gesucht werden soll.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-526">ticks - The time to which to seek.</span></span>

<span data-ttu-id="b6cf7-527">**Microsoft. perceptionsimulation. isimulationrecording. anhalten**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-527">**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**</span></span>

<span data-ttu-id="b6cf7-528">Beendet die Wiedergabe und setzt die Position auf den Anfang zurück.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-528">Stops the playback and resets the position to the beginning.</span></span>

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a><span data-ttu-id="b6cf7-529">Microsoft. perceptionsimulation. isimulationrecordingcallback</span><span class="sxs-lookup"><span data-stu-id="b6cf7-529">Microsoft.PerceptionSimulation.ISimulationRecordingCallback</span></span>

<span data-ttu-id="b6cf7-530">Schnittstelle zum Empfangen von Zustandsänderungen während der Wiedergabe.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-530">Interface for receiving state changes during playback.</span></span>

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

<span data-ttu-id="b6cf7-531">**Microsoft. perceptionsimulation. isimulationrecordingcallback. playbackstatechanged (Microsoft. perceptionsimulation. playbackstate)**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-531">**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**</span></span>

<span data-ttu-id="b6cf7-532">Wird aufgerufen, wenn sich der Wiedergabe Zustand einer isimulationrecording geändert hat.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-532">Called when an ISimulationRecording's playback state has changed.</span></span>

<span data-ttu-id="b6cf7-533">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6cf7-533">Parameters</span></span>
* <span data-ttu-id="b6cf7-534">newState: der neue Status der Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-534">newState - The new state of the recording.</span></span>

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a><span data-ttu-id="b6cf7-535">Microsoft. perceptionsimulation. perceptionsimulationmanager</span><span class="sxs-lookup"><span data-stu-id="b6cf7-535">Microsoft.PerceptionSimulation.PerceptionSimulationManager</span></span>

<span data-ttu-id="b6cf7-536">Das Stamm Objekt zum Erstellen von perception Simulation-Objekten.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-536">Root object for creating Perception Simulation objects.</span></span>

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

<span data-ttu-id="b6cf7-537">**Microsoft. perceptionsimulation. perceptionsimulationmanager. kreateperceptionsimulationmanager (Microsoft. perceptionsimulation. isimulationstreamsink)**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-537">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**</span></span>

<span data-ttu-id="b6cf7-538">Erstellen Sie ein Objekt zum Erstellen von simulierten Paketen und zum Bereitstellen der Pakete an die angegebene Senke.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-538">Create on object for generating simulated packets and delivering them to the provided sink.</span></span>

<span data-ttu-id="b6cf7-539">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6cf7-539">Parameters</span></span>
* <span data-ttu-id="b6cf7-540">Sink: die Senke, die alle generierten Pakete empfängt.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-540">sink - The sink that will receive all generated packets.</span></span>

<span data-ttu-id="b6cf7-541">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="b6cf7-541">Return value</span></span>

<span data-ttu-id="b6cf7-542">Der erstellte Manager.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-542">The created Manager.</span></span>

<span data-ttu-id="b6cf7-543">**Microsoft. perceptionsimulation. perceptionsimulationmanager. kreateperceptionsimulationrecording (System. String)**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-543">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**</span></span>

<span data-ttu-id="b6cf7-544">Erstellen Sie eine Senke, in der alle empfangenen Pakete in einer Datei unter dem angegebenen Pfad gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-544">Create a sink which stores all received packets in a file at the specified path.</span></span>

<span data-ttu-id="b6cf7-545">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6cf7-545">Parameters</span></span>
* <span data-ttu-id="b6cf7-546">Path: der Pfad der zu erstellenden Datei.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-546">path - The path of the file to create.</span></span>

<span data-ttu-id="b6cf7-547">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="b6cf7-547">Return value</span></span>

<span data-ttu-id="b6cf7-548">Die erstellte Senke.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-548">The created sink.</span></span>

<span data-ttu-id="b6cf7-549">**Microsoft. perceptionsimulation. perceptionsimulationmanager. loadperceptionsimulationrecording (System. String, Microsoft. perceptionsimulation. isimulationstreamsink Factory)**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-549">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**</span></span>

<span data-ttu-id="b6cf7-550">Lädt eine Aufzeichnung aus der angegebenen Datei.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-550">Load a recording from the specified file.</span></span>

<span data-ttu-id="b6cf7-551">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6cf7-551">Parameters</span></span>
* <span data-ttu-id="b6cf7-552">Path: der Pfad der zu ladenden Datei.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-552">path - The path of the file to load.</span></span>
* <span data-ttu-id="b6cf7-553">Factory: eine Factory, die von der Aufzeichnung zum Erstellen einer isimulationstreamsink bei Bedarf verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-553">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>

<span data-ttu-id="b6cf7-554">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="b6cf7-554">Return value</span></span>

<span data-ttu-id="b6cf7-555">Die geladene Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-555">The loaded recording.</span></span>

<span data-ttu-id="b6cf7-556">**Microsoft. perceptionsimulation. perceptionsimulationmanager. loadperceptionsimulationrecording (System. String, Microsoft. perceptionsimulation. isimulationstreamsink Factory, Microsoft. perceptionsimulation. isimulationrecordingcallback)**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-556">**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**</span></span>

<span data-ttu-id="b6cf7-557">Lädt eine Aufzeichnung aus der angegebenen Datei.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-557">Load a recording from the specified file.</span></span>

<span data-ttu-id="b6cf7-558">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6cf7-558">Parameters</span></span>
* <span data-ttu-id="b6cf7-559">Path: der Pfad der zu ladenden Datei.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-559">path - The path of the file to load.</span></span>
* <span data-ttu-id="b6cf7-560">Factory: eine Factory, die von der Aufzeichnung zum Erstellen einer isimulationstreamsink bei Bedarf verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-560">factory - A factory used by the recording for creating an ISimulationStreamSink when required.</span></span>
* <span data-ttu-id="b6cf7-561">Callback: ein Rückruf, der Updates empfängt, die den Status der Aufzeichnung neu formatidieren.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-561">callback - A callback which receives updates regrading the recording's status.</span></span>

<span data-ttu-id="b6cf7-562">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="b6cf7-562">Return value</span></span>

<span data-ttu-id="b6cf7-563">Die geladene Aufzeichnung.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-563">The loaded recording.</span></span>

### <a name="microsoftperceptionsimulationstreamdatatypes"></a><span data-ttu-id="b6cf7-564">Microsoft. perceptionsimulation. streamdatatypes</span><span class="sxs-lookup"><span data-stu-id="b6cf7-564">Microsoft.PerceptionSimulation.StreamDataTypes</span></span>

<span data-ttu-id="b6cf7-565">Beschreibt die unterschiedlichen Typen von Streamdaten.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-565">Describes the different types of stream data.</span></span>

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

<span data-ttu-id="b6cf7-566">**Microsoft. perceptionsimulation. streamdatatypes. None**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-566">**Microsoft.PerceptionSimulation.StreamDataTypes.None**</span></span>

<span data-ttu-id="b6cf7-567">Ein Sentinelwert, der verwendet wird, um keine streamdatentypen anzugeben</span><span class="sxs-lookup"><span data-stu-id="b6cf7-567">A sentinel value used to indicate no stream data types.</span></span>

<span data-ttu-id="b6cf7-568">**Microsoft. perceptionsimulation. streamdatatypes. Head**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-568">**Microsoft.PerceptionSimulation.StreamDataTypes.Head**</span></span>

<span data-ttu-id="b6cf7-569">Datenstrom bezüglich der Position und Ausrichtung des Kopfes.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-569">Stream of data regarding the position and orientation of the head.</span></span>

<span data-ttu-id="b6cf7-570">**Microsoft. perceptionsimulation. streamdatatypes. Hands**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-570">**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**</span></span>

<span data-ttu-id="b6cf7-571">Datenstrom in Bezug auf die Position und Gesten von Händen.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-571">Stream of data regarding the position and gestures of hands.</span></span>

<span data-ttu-id="b6cf7-572">**Microsoft. perceptionsimulation. streamdatatypes. spatialmapping**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-572">**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**</span></span>

<span data-ttu-id="b6cf7-573">Datenstrom in Bezug auf die räumliche Zuordnung der Umgebung.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-573">Stream of data regarding spatial mapping of the environment.</span></span>

<span data-ttu-id="b6cf7-574">**Microsoft. perceptionsimulation. streamdatatypes. Kalibrierung**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-574">**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**</span></span>

<span data-ttu-id="b6cf7-575">Datenstrom zur Kalibrierung des Geräts.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-575">Stream of data regarding calibration of the device.</span></span> <span data-ttu-id="b6cf7-576">Kalibrierungs Pakete werden nur von einem System im Remote Modus akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-576">Calibration packets are only accepted by a system in Remote Mode.</span></span>

<span data-ttu-id="b6cf7-577">**Microsoft. perceptionsimulation. streamdatatypes. Environment**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-577">**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**</span></span>

<span data-ttu-id="b6cf7-578">Datenstrom in Bezug auf die Umgebung des Geräts.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-578">Stream of data regarding the environment of the device.</span></span>

<span data-ttu-id="b6cf7-579">**Microsoft. perceptionsimulation. streamdatatypes. all**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-579">**Microsoft.PerceptionSimulation.StreamDataTypes.All**</span></span>

<span data-ttu-id="b6cf7-580">Ein Sentinelwert, der verwendet wird, um alle aufgezeichneten Datentypen anzugeben.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-580">A sentinel value used to indicate all recorded data types.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a><span data-ttu-id="b6cf7-581">Microsoft. perceptionsimulation. isimulationstreamsink</span><span class="sxs-lookup"><span data-stu-id="b6cf7-581">Microsoft.PerceptionSimulation.ISimulationStreamSink</span></span>

<span data-ttu-id="b6cf7-582">Ein Objekt, das Datenpakete von einem Simulationsdaten Strom empfängt.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-582">An object that receives data packets from a simulation stream.</span></span>

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

<span data-ttu-id="b6cf7-583">**Microsoft. perceptionsimulation. isimulationstreamsink. onpacketempfang\uint length, Byte [] Packet)**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-583">**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**</span></span>

<span data-ttu-id="b6cf7-584">Empfängt ein einzelnes Paket, das intern eingegeben und mit Versions Angabe versehen ist.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-584">Receives a single packet, which is internally typed and versioned.</span></span>

<span data-ttu-id="b6cf7-585">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6cf7-585">Parameters</span></span>
* <span data-ttu-id="b6cf7-586">length: die Länge des Pakets.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-586">length - The length of the packet.</span></span>
* <span data-ttu-id="b6cf7-587">Packet: die Daten des Pakets.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-587">packet - The data of the packet.</span></span>

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a><span data-ttu-id="b6cf7-588">Microsoft. perceptionsimulation. isimulationstreamsink Factory</span><span class="sxs-lookup"><span data-stu-id="b6cf7-588">Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory</span></span>

<span data-ttu-id="b6cf7-589">Ein Objekt, das isimulationstreamsink erstellt.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-589">An object that creates ISimulationStreamSink.</span></span>

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

<span data-ttu-id="b6cf7-590">**Microsoft. perceptionsimulation. isimulationstreamsink Factory. kreatesimulationstreamsink ()**</span><span class="sxs-lookup"><span data-stu-id="b6cf7-590">**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**</span></span>

<span data-ttu-id="b6cf7-591">Erstellt eine einzelne Instanz von isimulationstreamsink.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-591">Creates a single instance of ISimulationStreamSink.</span></span>

<span data-ttu-id="b6cf7-592">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="b6cf7-592">Return value</span></span>

<span data-ttu-id="b6cf7-593">Die erstellte Senke.</span><span class="sxs-lookup"><span data-stu-id="b6cf7-593">The created sink.</span></span>
