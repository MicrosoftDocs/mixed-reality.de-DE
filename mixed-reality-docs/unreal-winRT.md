---
title: WinRT in Unreal
description: Übersicht zum Plug-In für räumliche Audiowiedergabe für die Unreal Engine.
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 07/08/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Streaming, Remoting, Mixed Reality, Entwicklung, erste Schritte, Features, neues Projekt, Emulator, Dokumentation, Leitfäden, Features, Hologramme, Spieleentwicklung
ms.openlocfilehash: 7a64002a5fa48bb589ab113f0a8dc1bfcb92d535
ms.sourcegitcommit: 2813f5b3027d47f7c6e9772338935eeccfa2aaec
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2020
ms.locfileid: "86408218"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="abea9-104">WinRT in Unreal</span><span class="sxs-lookup"><span data-stu-id="abea9-104">WinRT in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="abea9-105">Überblick</span><span class="sxs-lookup"><span data-stu-id="abea9-105">Overview</span></span>

<span data-ttu-id="abea9-106">Im Verlauf der hololens-Entwicklung müssen Sie möglicherweise eine Funktion mit WinRT schreiben.</span><span class="sxs-lookup"><span data-stu-id="abea9-106">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="abea9-107">Wenn Sie z. b. eine Datei Dialogfeld in einer hololens-Anwendung öffnen, benötigen Sie die filesavepicker in der Header Datei WinRT/Windows. Storage. Pickers. h.</span><span class="sxs-lookup"><span data-stu-id="abea9-107">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span>  <span data-ttu-id="abea9-108">Da Unreal WinRT-Code nicht nativ kompiliert, ist es Ihre Aufgabe, eine separate Binärdatei zu erstellen, die vom Buildsystem von Unreal verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="abea9-108">Since Unreal doesn't natively compile WinRT code, it's your job to build a separate binary and that can be consumed by Unreal’s build system.</span></span> <span data-ttu-id="abea9-109">Dieses Tutorial führt Sie durch ein solches Szenario.</span><span class="sxs-lookup"><span data-stu-id="abea9-109">This tutorial will walk you through just such a scenario.</span></span>

## <a name="objectives"></a><span data-ttu-id="abea9-110">Ziele</span><span class="sxs-lookup"><span data-stu-id="abea9-110">Objectives</span></span>
- <span data-ttu-id="abea9-111">Erstellen einer universellen Windows-DLL, die ein filesavedialog öffnet</span><span class="sxs-lookup"><span data-stu-id="abea9-111">Create a Universal Windows DLL that opens a FileSaveDialogue</span></span>
- <span data-ttu-id="abea9-112">Diese DLL mit einem Unreal Game-Projekt verknüpfen</span><span class="sxs-lookup"><span data-stu-id="abea9-112">Link that DLL to an Unreal game project</span></span>
- <span data-ttu-id="abea9-113">Speichern einer Datei in den hololens von einem Unreal Blueprint mithilfe der neuen dll</span><span class="sxs-lookup"><span data-stu-id="abea9-113">Save a file on the HoloLens from an Unreal blueprint using the new DLL</span></span>

## <a name="getting-started"></a><span data-ttu-id="abea9-114">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="abea9-114">Getting started</span></span>
1. <span data-ttu-id="abea9-115">Überprüfen Sie, ob alle [erforderlichen Tools](unreal-uxt-ch1.md) installiert sind</span><span class="sxs-lookup"><span data-stu-id="abea9-115">Check that you have all [required tools](unreal-uxt-ch1.md) installed</span></span>
2. <span data-ttu-id="abea9-116">[Erstellen Sie ein neues Unreal-Projekt](unreal-uxt-ch2.md#creating-a-new-unreal-project) , und nennen Sie es **consumewinrt** .</span><span class="sxs-lookup"><span data-stu-id="abea9-116">[Create a new Unreal project](unreal-uxt-ch2.md#creating-a-new-unreal-project) and name it **Consumewinrt**</span></span>
3. <span data-ttu-id="abea9-117">Aktivieren der [erforderlichen](unreal-uxt-ch2.md#enabling-required-plugins) Plug-Ins für die hololens-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="abea9-117">Enable the [required plugins](unreal-uxt-ch2.md#enabling-required-plugins) for HoloLens development</span></span>
4. <span data-ttu-id="abea9-118">[Setup für die Bereitstellung](unreal-uxt-ch6.md) auf einem Gerät oder Emulator</span><span class="sxs-lookup"><span data-stu-id="abea9-118">[Setup for deployment](unreal-uxt-ch6.md) to a device or emulator</span></span>

## <a name="creating-a-winrt-dll"></a><span data-ttu-id="abea9-119">Erstellen einer WinRT-dll</span><span class="sxs-lookup"><span data-stu-id="abea9-119">Creating a WinRT DLL</span></span> 
1. <span data-ttu-id="abea9-120">Öffnen Sie ein neues Visual Studio-Projekt, und erstellen Sie ein DLL-Projekt **(Universal Windows)** im gleichen Verzeichnis wie die **uproject** -Datei des Unreal-Spiels.</span><span class="sxs-lookup"><span data-stu-id="abea9-120">Open a new Visual Studio project and create a **DLL (Universal Windows)** project in the same directory to the Unreal game’s **uproject** file.</span></span> 

![Erstellen einer dll](images/unreal-winrt-img-01.png)

2. <span data-ttu-id="abea9-122">Nennen Sie das Projekt **hololenswinrtdll** , und legen Sie den Speicherort als Unterverzeichnis **thirdparty** auf die uproject-Datei des Unreal-Spiels fest.</span><span class="sxs-lookup"><span data-stu-id="abea9-122">Name the project **HoloLensWinrtDLL** and set the location as a **ThirdParty** subdirectory to the Unreal game’s uproject file.</span></span> 
    * <span data-ttu-id="abea9-123">Wählen Sie **Projekt Mappe und Projekt in demselben Verzeichnis platzieren** aus, um die Suche nach Pfaden später zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="abea9-123">Select **Place solution and project in the same directory** to simplify looking for paths later.</span></span> 

![Konfigurieren der dll](images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> <span data-ttu-id="abea9-125">Nachdem das neue Projekt kompiliert wurde, sollten Sie besonders auf die leeren cpp-und Header Dateien achten, mit dem Namen **hololenswinrtdll. cpp** bzw. **hololenswinrtdll. h** .</span><span class="sxs-lookup"><span data-stu-id="abea9-125">After the new project compiles, you want to pay special attention to the blank cpp and header files, named **HoloLensWinrtDLL.cpp** and **HoloLensWinrtDLL.h** respectively.</span></span> <span data-ttu-id="abea9-126">Der-Header ist die Includedatei, die die dll in Unreal verwendet, während der cpp den Text der Funktionen enthält, die Sie exportieren, und einen WinRT-Code enthält, den Unreal nicht anderweitig kompilieren kann.</span><span class="sxs-lookup"><span data-stu-id="abea9-126">The header is the include file that uses the DLL in Unreal, while the cpp holds the body of any functions you export and includes any WinRT code that Unreal wouldn't otherwise be able to compile.</span></span> 

3. <span data-ttu-id="abea9-127">Bevor Sie Code hinzufügen, müssen Sie die Projekteigenschaften aktualisieren, um sicherzustellen, dass der benötigte WinRT-Code kompiliert werden kann:</span><span class="sxs-lookup"><span data-stu-id="abea9-127">Before you add any code, you need to update the project properties to ensure the WinRT code you need can compile:</span></span> 
    * <span data-ttu-id="abea9-128">Klicken Sie mit der rechten Maustaste auf das Projekt hololenswinrtdll, und wählen Sie **Eigenschaften**</span><span class="sxs-lookup"><span data-stu-id="abea9-128">Right click on the HoloLensWinrtDLL project and select **properties**</span></span>  
    * <span data-ttu-id="abea9-129">Ändern Sie die Dropdown Liste **Konfiguration** auf **alle Konfigurationen** und die Dropdown Liste für die **Plattform** auf **alle Plattformen** .</span><span class="sxs-lookup"><span data-stu-id="abea9-129">Change the **Configuration** dropdown to **All Configurations** and the **Platform** dropdown to **All Platforms**</span></span>  
    * <span data-ttu-id="abea9-130">Unter **Konfigurations Eigenschaften> C/C++> alle Optionen**:</span><span class="sxs-lookup"><span data-stu-id="abea9-130">Under **Configuration Properties> C/C++> All Options**:</span></span>
        * <span data-ttu-id="abea9-131">Fügen Sie **zusätzliche Optionen** hinzu **, um sicher** zustellen, dass wir auf asynchrone Tasks warten können.</span><span class="sxs-lookup"><span data-stu-id="abea9-131">Add **await** to **Additional Options** to ensure we can wait on async tasks</span></span>  
        * <span data-ttu-id="abea9-132">Ändern Sie den **C++-Sprachstandard** in **ISO C++ 17 Standard (/Std: C++ 17)** , um WinRT-Code einzubeziehen.</span><span class="sxs-lookup"><span data-stu-id="abea9-132">Change **C++ Language Standard** to **ISO C++17 Standard (/std:c++17)** to include any WinRT code</span></span>

![Konfigurieren der dll](images/unreal-winrt-img-03.png)

<span data-ttu-id="abea9-134">Das Projekt ist zum Aktualisieren der DLL-Quelle mit WinRT-Code bereit, mit dem ein Datei Dialogfeld geöffnet und eine Datei auf dem Datenträger für hololens gespeichert wird.</span><span class="sxs-lookup"><span data-stu-id="abea9-134">Your project is ready to update the DLL’s source with WinRT code that opens a file dialogue and saves a file to the HoloLens disk.</span></span>  

## <a name="adding-the-dll-code"></a><span data-ttu-id="abea9-135">Hinzufügen des dll-Codes</span><span class="sxs-lookup"><span data-stu-id="abea9-135">Adding the DLL code</span></span>
1. <span data-ttu-id="abea9-136">Öffnen Sie **hololenswinrtdll. h** , und fügen Sie eine exportierte DLL-Funktion hinzu, damit Unreal verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="abea9-136">Open **HoloLensWinrtDLL.h** and add a dll exported function for Unreal to consume:</span></span> 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. <span data-ttu-id="abea9-137">Öffnen Sie **hololenswinrtdll. cpp** , und fügen Sie alle Header hinzu, die von der-Klasse verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="abea9-137">Open **HoloLensWinrtDLL.cpp** and add all headers the class will use:</span></span>  

```cpp
#include "pch.h"
#include "HoloLensWinrtDLL.h"

#include <winrt/Windows.Storage.h>
#include <winrt/Windows.Storage.Streams.h>
#include <winrt/Windows.Storage.Pickers.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Foundation.Collections.h>

#include <string>
#include <vector>
#include <thread>
```

> [!NOTE]
> <span data-ttu-id="abea9-138">Der gesamte WinRT-Code wird in **hololenswinrtdll. cpp** gespeichert, sodass Unreal nicht versucht, beim Verweis auf den Header einen WinRT-Code einzufügen.</span><span class="sxs-lookup"><span data-stu-id="abea9-138">All WinRT code is stored in **HoloLensWinrtDLL.cpp** so Unreal doesn't try to include any WinRT code when referencing the header.</span></span> 

3. <span data-ttu-id="abea9-139">Fügen Sie in **hololenswinrtdll. cpp**einen Funktions Text für OpenFileDialog () und den gesamten unterstützten Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="abea9-139">Still in **HoloLensWinrtDLL.cpp**, add a function body for OpenFileDialogue() and all supported code:</span></span> 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. <span data-ttu-id="abea9-140">Fügen Sie eine SavegameManager-Klasse zu **hololenswinrtdll. cpp** hinzu, um das Datei Dialogfeld zu verarbeiten und die Datei zu speichern:</span><span class="sxs-lookup"><span data-stu-id="abea9-140">Add a SaveGameManager class to **HoloLensWinrtDLL.cpp** to handle the file dialogue and saving the file:</span></span> 

```cpp
class SaveGameManager
{
public:
    SaveGameManager()
    {
    }

    ~SaveGameManager()
    {
        // Wait for currently running thread to complete before terminating.
        if(m_thread.joinable())
        {
            m_thread.join();
        }
    }

    void SaveGame()
    {
        OpenFileDialogueAction();
    }

private:
    winrt::Windows::Storage::StorageFile m_file = winrt::Windows::Storage::StorageFile(nullprt);
    std::thread m_thread;

    winrt::Windows::Foundation::IAsyncAction OpenFileDialogueAction()
    {
        std::vector<winrt::hstring> extensions;
        extensions.push_back(L".txt");

        auto picker = winrt::Windows::Storage::Pickers::FileSavePicker();

        // FileSavePicker needs a file type to open without errors.
        picker.FileTypeChoices().Insert(L"Plain Text",
                                        winrt::single_threaded_vector<winrt::hstring>(
                                        std::move(extensions)));

        // Opening the FilePicker must be done on the Game UI thread.
        // Any other IAsyncOperations should be done on a background thread.
        m_file = co_await picker.PickSaveFileAsync();

        if(m_file)
        {
            // Unreal's game thread is an STA, async tasks need to run on
            // a background MTA thread, or waiting on them will deadlock.    
            std::thread thread([this]() { RunThread(); });
            m_thread = std::move(thread);
        }
    }

    void RunThread()
    {
        // Ensure this thread is an MTA
        winrt::init_apartment();
        Run().get();
    }

    winrt::Windows::Foundation::IAsyncAction Run()
    {
        co_await winrt::Windows::Storage::FileIO::WriteTextAsync(
                m_file, L"Hello WinRT");
    }
};
```

5. <span data-ttu-id="abea9-141">Erstellen Sie die Projekt Mappe für **Release > ARM64** , um die DLL für das untergeordnete Verzeichnis ARM64/Release/hololenswinrtdll aus der DLL-Projekt Mappe zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="abea9-141">Build the solution for **Release > ARM64** to build the DLL to the child directory ARM64/Release/HoloLensWinrtDLL from the DLL solution.</span></span> 

## <a name="adding-the-winrt-binary-to-unreal"></a><span data-ttu-id="abea9-142">Hinzufügen der WinRT-Binärdatei zu Unreal</span><span class="sxs-lookup"><span data-stu-id="abea9-142">Adding the WinRT binary to Unreal</span></span> 
<span data-ttu-id="abea9-143">Das Verknüpfen und Verwenden einer DLL in Unreal erfordert ein C++-Projekt.</span><span class="sxs-lookup"><span data-stu-id="abea9-143">Linking and using a DLL in Unreal requires a C++ project.</span></span> <span data-ttu-id="abea9-144">Wenn Sie ein Blueprint-Projekt verwenden, kann es problemlos in ein C++-Projekt konvertiert werden, indem eine C++-Klasse hinzugefügt wird:</span><span class="sxs-lookup"><span data-stu-id="abea9-144">If you're using a Blueprint project, it can be easily converted to a C++ project by adding a C++ class:</span></span>  

1. <span data-ttu-id="abea9-145">Öffnen Sie im Unreal Editor **File > New C++ Class...**</span><span class="sxs-lookup"><span data-stu-id="abea9-145">In the Unreal editor, open **File > New C++ Class…**</span></span> <span data-ttu-id="abea9-146">und erstellen Sie einen neuen **Actor** namens **winrtactor** , um den Code in der DLL auszuführen:</span><span class="sxs-lookup"><span data-stu-id="abea9-146">and create a new **Actor** named **WinrtActor** to run the code in the DLL:</span></span> 

![Konfigurieren der dll](images/unreal-winrt-img-04.png)

> [!NOTE]
> <span data-ttu-id="abea9-148">Eine Projekt Mappe wurde nun im gleichen Verzeichnis wie die uproject-Datei erstellt, zusammen mit einem neuen Buildskript mit dem Namen "Source/consumewinrt/consumerwinrt. Build. cs".</span><span class="sxs-lookup"><span data-stu-id="abea9-148">A solution has now been created in the same directory as the uproject file along with a new build script named Source/ConsumeWinRT/ConsumerWinRT.Build.cs.</span></span>

2. <span data-ttu-id="abea9-149">Öffnen Sie die Projekt Mappe, suchen Sie nach dem Ordner **Games/consumewinrt/Source/consumewinrt** , und öffnen Sie **ConsumeWinRT.Build.cs**:</span><span class="sxs-lookup"><span data-stu-id="abea9-149">Open the solution, browse for the **Games/ConsumeWinRT/Source/ConsumeWinRT** folder, and open **ConsumeWinRT.build.cs**:</span></span>

![Konfigurieren der dll](images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a><span data-ttu-id="abea9-151">Verknüpfen der dll</span><span class="sxs-lookup"><span data-stu-id="abea9-151">Linking the DLL</span></span>
1. <span data-ttu-id="abea9-152">Fügen Sie in **ConsumeWinRT.Build.cs**eine Eigenschaft hinzu, um den Includepfad für die dll zu suchen (das Verzeichnis, das hololenswinrtdll. h enthält).</span><span class="sxs-lookup"><span data-stu-id="abea9-152">In **ConsumeWinRT.build.cs**, add a property to find the include path for the DLL (the directory containing HoloLensWinrtDLL.h).</span></span> <span data-ttu-id="abea9-153">Die dll befindet sich in einem untergeordneten Verzeichnis des include-Pfads, sodass diese Eigenschaft als binäres Stammverzeichnis verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="abea9-153">The DLL is in a child directory to the include path, so this property will be used as the binary root dir:</span></span>

```cs
public class ConsumeWinRT : ModuleRules
{
    private string WinrtIncPath
    {
        get 
        {
            string ModulePath = Path.GetDirectoryName(
                   RulesCompiler.GetFileNameFromType(this.GetType()));

            // Third party directory is at the project root,
            // which is two directories up from the game .exe (Binaries/HoloLens)
            return Path.GetFullPath(
                   Path.Combine(ModulePath,
                   "../../ThirddParty/HoloLensWinrtDLL"));
        }
    }
}
```

2. <span data-ttu-id="abea9-154">Fügen Sie im Klassenkonstruktor den folgenden Code hinzu, um den Includepfad zu aktualisieren, verknüpfen Sie die neue lib, und kopieren Sie die dll in den gepackten AppX-Speicherort:</span><span class="sxs-lookup"><span data-stu-id="abea9-154">In the class constructor, add the following code to update the include path, link the new lib, and delay-load and copy the DLL to the packaged appx location:</span></span>

```cs
public ConsumeWinRT(ReadOnlyTargetRules target) : base(Target)
{
    // This is the directory the DLL's include header is in.
    PublicIncludePaths.Add(WinrtIncPath);

    // The code in HoloLensWinrtDLL will only work in a Windows Store app.
    // Only link these binaries for HoloLens.
    // Similar code can be written for desktop and similarly linked 
    // to use the same features when using Holographic Remoting.
    if(Target.Platform == UnrealTargetPlatform.HoloLens)
    {
        // Link the lib
        PublicAdditionalLibraries.Add(Path.Combine(
              WinrtIncPath, "ARM64", "Release",
              "HoloLensWinrtDLL","HoloLensWinrtDLL.lib"));

        string winrtDLL = "HoloLensWinrtDLL.dll";
        // Mark the dll to be DelayLoaded
        PublicDelayLoadDLLs.Add(winrtDLL);
        // RuntimeDependencies are included in packaged builds.
        RuntimeDependencies.Add(Path.Combine(WinrtIncPath,
                "ARM64", "Release", "HoloLensWinrtDLL", winrtDLL));
    }

    // Preserve the original code in build.cs below:
}
```

3. <span data-ttu-id="abea9-155">Öffnen Sie **winrtactor. h** , und fügen Sie zwei Funktionsdefinitionen, eine Blaupause und eine andere, die den DLL-Code verwendet:</span><span class="sxs-lookup"><span data-stu-id="abea9-155">Open **WinrtActor.h** and add two function definitions, one that a blueprint can use and another that uses the DLL code:</span></span> 
```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue;
```

4. <span data-ttu-id="abea9-156">Öffnen Sie " **winrtactor. cpp** ", und laden Sie die dll in "beginplay":</span><span class="sxs-lookup"><span data-stu-id="abea9-156">Open **WinrtActor.cpp** and load the DLL in BeginPlay:</span></span> 

```cpp
void AWinfrtActor::BeginPlay()
{
#if PLATFORM_HOLOLENS
    HoloLensWinrtDLL::OpenFileDialogue();
#endif
}
``` 

>[!CAUTION]
> <span data-ttu-id="abea9-157">Die dll muss geladen werden, bevor Sie Ihre Funktionen aufrufen können.</span><span class="sxs-lookup"><span data-stu-id="abea9-157">The DLL must be loaded before calling any of its functions.</span></span>

### <a name="building-the-game"></a><span data-ttu-id="abea9-158">Entwickeln des Spiels</span><span class="sxs-lookup"><span data-stu-id="abea9-158">Building the game</span></span>
1. <span data-ttu-id="abea9-159">Erstellen Sie die Spiel Projekt Mappe, um den Unreal Editor zu starten, der für das Spiel Projekt geöffnet wurde:</span><span class="sxs-lookup"><span data-stu-id="abea9-159">Build the game solution to launch the Unreal editor opened to the game project:</span></span> 
    * <span data-ttu-id="abea9-160">Suchen Sie auf der Registerkarte **platzieren der Actors** nach dem neuen **winrtactor** , und ziehen Sie ihn in die Szene.</span><span class="sxs-lookup"><span data-stu-id="abea9-160">In the **Place Actors** tab, search for the new **WinrtActor** and drag it into the scene</span></span> 
    * <span data-ttu-id="abea9-161">Öffnen Sie die Ebene Blueprint, um die Aufruf Bare Blueprint-Funktion im **winrtactor** auszuführen.</span><span class="sxs-lookup"><span data-stu-id="abea9-161">Open the level blueprint to execute the blueprint callable function in the **WinrtActor**</span></span> 

![Konfigurieren der dll](images/unreal-winrt-img-06.png)

2. <span data-ttu-id="abea9-163">Suchen Sie im **World Outliner**den zuvor in der Szene gelöschten **windrtactor** , und ziehen Sie ihn in den Blueprint der Ebene:</span><span class="sxs-lookup"><span data-stu-id="abea9-163">In the **World Outliner**, find the **WindrtActor** previously dropped into the scene and drag it into the level blueprint:</span></span> 

![Konfigurieren der dll](images/unreal-winrt-img-07.png)

3. <span data-ttu-id="abea9-165">Ziehen Sie in der Ebene Blueprint den Ausgabe Knoten von winrtactor, suchen Sie nach dem Dialogfeld " **Datei öffnen**", und leiten Sie den Knoten von jeder Benutzereingabe weiter.</span><span class="sxs-lookup"><span data-stu-id="abea9-165">In the level blueprint, drag the output node from WinrtActor, search for **Open File Dialogue**, then route the node from any user input.</span></span>  <span data-ttu-id="abea9-166">In diesem Fall wird das Dialogfeld "Datei öffnen" von einem sprach Ereignis aufgerufen:</span><span class="sxs-lookup"><span data-stu-id="abea9-166">In this case, Open File Dialogue is being called from a speech event:</span></span> 

![Konfigurieren der dll](images/unreal-winrt-img-08.png)

4. <span data-ttu-id="abea9-168">[Packen Sie dieses Spiel für hololens](unreal-uxt-ch6.md), stellen Sie es bereit, und führen Sie aus.</span><span class="sxs-lookup"><span data-stu-id="abea9-168">[Package this game for HoloLens](unreal-uxt-ch6.md), deploy it, and run.</span></span>  

<span data-ttu-id="abea9-169">Wenn Unreal "OpenFileDialog" aufruft, wird ein Datei Dialogfeld in den hololens geöffnet, in dem der Dateiname "</span><span class="sxs-lookup"><span data-stu-id="abea9-169">When Unreal calls OpenFileDialogue, a File Dialogue opens on the HoloLens prompting for a .txt file name.</span></span>  <span data-ttu-id="abea9-170">Nachdem die Datei gespeichert wurde, wechseln Sie im Geräte Portal zur Registerkarte " **Datei-Explorer** ", um den Inhalt "Hello WinRT" anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="abea9-170">After the file is saved, go to the **File explorer** tab in the device portal to see the contents “Hello WinRT”.</span></span> 

## <a name="summary"></a><span data-ttu-id="abea9-171">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="abea9-171">Summary</span></span> 

<span data-ttu-id="abea9-172">Wir empfehlen Ihnen, den Code in diesem Tutorial als Ausgangspunkt für die Verwendung von WinRT-Code in Unreal zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="abea9-172">We encourage you to use the code in this tutorial as a starting point for consuming WinRT code in Unreal.</span></span>  <span data-ttu-id="abea9-173">Er ermöglicht Benutzern das Speichern von Dateien auf dem hololens-Datenträger mit demselben Datei Dialogfeld wie Windows.</span><span class="sxs-lookup"><span data-stu-id="abea9-173">It allows users to save files to the HoloLens disk using the same file dialogue as Windows.</span></span>  <span data-ttu-id="abea9-174">Führen Sie den gleichen Vorgang aus, um zusätzliche Funktionen aus dem hololenswinrtdll-Header zu exportieren und in Unreal verwendet zu werden.</span><span class="sxs-lookup"><span data-stu-id="abea9-174">Follow the same process to export any additional functions from the HoloLensWinrtDLL header and used in Unreal.</span></span>  <span data-ttu-id="abea9-175">Beachten Sie den DLL-Code, der auf einen asynchronen WinRT-Code in einem MTA-Hintergrund Thread wartet, der das Deadlocks des Unreal Game-Threads vermeidet.</span><span class="sxs-lookup"><span data-stu-id="abea9-175">Note the DLL code that waits on any async WinRT code in a background MTA thread, which avoids deadlocking the Unreal game thread.</span></span> 

## <a name="see-also"></a><span data-ttu-id="abea9-176">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="abea9-176">See also</span></span>
* [<span data-ttu-id="abea9-177">C++/WinRT-APIs</span><span class="sxs-lookup"><span data-stu-id="abea9-177">C++/WinRT APIs</span></span>](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="abea9-178">Filesavepicker-Klasse</span><span class="sxs-lookup"><span data-stu-id="abea9-178">FileSavePicker class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="abea9-179">Unreal-Bibliotheken von Drittanbietern</span><span class="sxs-lookup"><span data-stu-id="abea9-179">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
