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
# <a name="winrt-in-unreal"></a>WinRT in Unreal

## <a name="overview"></a>Überblick

Im Verlauf der hololens-Entwicklung müssen Sie möglicherweise eine Funktion mit WinRT schreiben. Wenn Sie z. b. eine Datei Dialogfeld in einer hololens-Anwendung öffnen, benötigen Sie die filesavepicker in der Header Datei WinRT/Windows. Storage. Pickers. h.  Da Unreal WinRT-Code nicht nativ kompiliert, ist es Ihre Aufgabe, eine separate Binärdatei zu erstellen, die vom Buildsystem von Unreal verwendet werden kann. Dieses Tutorial führt Sie durch ein solches Szenario.

## <a name="objectives"></a>Ziele
- Erstellen einer universellen Windows-DLL, die ein filesavedialog öffnet
- Diese DLL mit einem Unreal Game-Projekt verknüpfen
- Speichern einer Datei in den hololens von einem Unreal Blueprint mithilfe der neuen dll

## <a name="getting-started"></a>Erste Schritte
1. Überprüfen Sie, ob alle [erforderlichen Tools](unreal-uxt-ch1.md) installiert sind
2. [Erstellen Sie ein neues Unreal-Projekt](unreal-uxt-ch2.md#creating-a-new-unreal-project) , und nennen Sie es **consumewinrt** .
3. Aktivieren der [erforderlichen](unreal-uxt-ch2.md#enabling-required-plugins) Plug-Ins für die hololens-Entwicklung
4. [Setup für die Bereitstellung](unreal-uxt-ch6.md) auf einem Gerät oder Emulator

## <a name="creating-a-winrt-dll"></a>Erstellen einer WinRT-dll 
1. Öffnen Sie ein neues Visual Studio-Projekt, und erstellen Sie ein DLL-Projekt **(Universal Windows)** im gleichen Verzeichnis wie die **uproject** -Datei des Unreal-Spiels. 

![Erstellen einer dll](images/unreal-winrt-img-01.png)

2. Nennen Sie das Projekt **hololenswinrtdll** , und legen Sie den Speicherort als Unterverzeichnis **thirdparty** auf die uproject-Datei des Unreal-Spiels fest. 
    * Wählen Sie **Projekt Mappe und Projekt in demselben Verzeichnis platzieren** aus, um die Suche nach Pfaden später zu vereinfachen. 

![Konfigurieren der dll](images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> Nachdem das neue Projekt kompiliert wurde, sollten Sie besonders auf die leeren cpp-und Header Dateien achten, mit dem Namen **hololenswinrtdll. cpp** bzw. **hololenswinrtdll. h** . Der-Header ist die Includedatei, die die dll in Unreal verwendet, während der cpp den Text der Funktionen enthält, die Sie exportieren, und einen WinRT-Code enthält, den Unreal nicht anderweitig kompilieren kann. 

3. Bevor Sie Code hinzufügen, müssen Sie die Projekteigenschaften aktualisieren, um sicherzustellen, dass der benötigte WinRT-Code kompiliert werden kann: 
    * Klicken Sie mit der rechten Maustaste auf das Projekt hololenswinrtdll, und wählen Sie **Eigenschaften**  
    * Ändern Sie die Dropdown Liste **Konfiguration** auf **alle Konfigurationen** und die Dropdown Liste für die **Plattform** auf **alle Plattformen** .  
    * Unter **Konfigurations Eigenschaften> C/C++> alle Optionen**:
        * Fügen Sie **zusätzliche Optionen** hinzu **, um sicher** zustellen, dass wir auf asynchrone Tasks warten können.  
        * Ändern Sie den **C++-Sprachstandard** in **ISO C++ 17 Standard (/Std: C++ 17)** , um WinRT-Code einzubeziehen.

![Konfigurieren der dll](images/unreal-winrt-img-03.png)

Das Projekt ist zum Aktualisieren der DLL-Quelle mit WinRT-Code bereit, mit dem ein Datei Dialogfeld geöffnet und eine Datei auf dem Datenträger für hololens gespeichert wird.  

## <a name="adding-the-dll-code"></a>Hinzufügen des dll-Codes
1. Öffnen Sie **hololenswinrtdll. h** , und fügen Sie eine exportierte DLL-Funktion hinzu, damit Unreal verwendet wird: 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. Öffnen Sie **hololenswinrtdll. cpp** , und fügen Sie alle Header hinzu, die von der-Klasse verwendet werden:  

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
> Der gesamte WinRT-Code wird in **hololenswinrtdll. cpp** gespeichert, sodass Unreal nicht versucht, beim Verweis auf den Header einen WinRT-Code einzufügen. 

3. Fügen Sie in **hololenswinrtdll. cpp**einen Funktions Text für OpenFileDialog () und den gesamten unterstützten Code hinzu: 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. Fügen Sie eine SavegameManager-Klasse zu **hololenswinrtdll. cpp** hinzu, um das Datei Dialogfeld zu verarbeiten und die Datei zu speichern: 

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

5. Erstellen Sie die Projekt Mappe für **Release > ARM64** , um die DLL für das untergeordnete Verzeichnis ARM64/Release/hololenswinrtdll aus der DLL-Projekt Mappe zu erstellen. 

## <a name="adding-the-winrt-binary-to-unreal"></a>Hinzufügen der WinRT-Binärdatei zu Unreal 
Das Verknüpfen und Verwenden einer DLL in Unreal erfordert ein C++-Projekt. Wenn Sie ein Blueprint-Projekt verwenden, kann es problemlos in ein C++-Projekt konvertiert werden, indem eine C++-Klasse hinzugefügt wird:  

1. Öffnen Sie im Unreal Editor **File > New C++ Class...** und erstellen Sie einen neuen **Actor** namens **winrtactor** , um den Code in der DLL auszuführen: 

![Konfigurieren der dll](images/unreal-winrt-img-04.png)

> [!NOTE]
> Eine Projekt Mappe wurde nun im gleichen Verzeichnis wie die uproject-Datei erstellt, zusammen mit einem neuen Buildskript mit dem Namen "Source/consumewinrt/consumerwinrt. Build. cs".

2. Öffnen Sie die Projekt Mappe, suchen Sie nach dem Ordner **Games/consumewinrt/Source/consumewinrt** , und öffnen Sie **ConsumeWinRT.Build.cs**:

![Konfigurieren der dll](images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a>Verknüpfen der dll
1. Fügen Sie in **ConsumeWinRT.Build.cs**eine Eigenschaft hinzu, um den Includepfad für die dll zu suchen (das Verzeichnis, das hololenswinrtdll. h enthält). Die dll befindet sich in einem untergeordneten Verzeichnis des include-Pfads, sodass diese Eigenschaft als binäres Stammverzeichnis verwendet wird:

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

2. Fügen Sie im Klassenkonstruktor den folgenden Code hinzu, um den Includepfad zu aktualisieren, verknüpfen Sie die neue lib, und kopieren Sie die dll in den gepackten AppX-Speicherort:

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

3. Öffnen Sie **winrtactor. h** , und fügen Sie zwei Funktionsdefinitionen, eine Blaupause und eine andere, die den DLL-Code verwendet: 
```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue;
```

4. Öffnen Sie " **winrtactor. cpp** ", und laden Sie die dll in "beginplay": 

```cpp
void AWinfrtActor::BeginPlay()
{
#if PLATFORM_HOLOLENS
    HoloLensWinrtDLL::OpenFileDialogue();
#endif
}
``` 

>[!CAUTION]
> Die dll muss geladen werden, bevor Sie Ihre Funktionen aufrufen können.

### <a name="building-the-game"></a>Entwickeln des Spiels
1. Erstellen Sie die Spiel Projekt Mappe, um den Unreal Editor zu starten, der für das Spiel Projekt geöffnet wurde: 
    * Suchen Sie auf der Registerkarte **platzieren der Actors** nach dem neuen **winrtactor** , und ziehen Sie ihn in die Szene. 
    * Öffnen Sie die Ebene Blueprint, um die Aufruf Bare Blueprint-Funktion im **winrtactor** auszuführen. 

![Konfigurieren der dll](images/unreal-winrt-img-06.png)

2. Suchen Sie im **World Outliner**den zuvor in der Szene gelöschten **windrtactor** , und ziehen Sie ihn in den Blueprint der Ebene: 

![Konfigurieren der dll](images/unreal-winrt-img-07.png)

3. Ziehen Sie in der Ebene Blueprint den Ausgabe Knoten von winrtactor, suchen Sie nach dem Dialogfeld " **Datei öffnen**", und leiten Sie den Knoten von jeder Benutzereingabe weiter.  In diesem Fall wird das Dialogfeld "Datei öffnen" von einem sprach Ereignis aufgerufen: 

![Konfigurieren der dll](images/unreal-winrt-img-08.png)

4. [Packen Sie dieses Spiel für hololens](unreal-uxt-ch6.md), stellen Sie es bereit, und führen Sie aus.  

Wenn Unreal "OpenFileDialog" aufruft, wird ein Datei Dialogfeld in den hololens geöffnet, in dem der Dateiname "  Nachdem die Datei gespeichert wurde, wechseln Sie im Geräte Portal zur Registerkarte " **Datei-Explorer** ", um den Inhalt "Hello WinRT" anzuzeigen. 

## <a name="summary"></a>Zusammenfassung 

Wir empfehlen Ihnen, den Code in diesem Tutorial als Ausgangspunkt für die Verwendung von WinRT-Code in Unreal zu verwenden.  Er ermöglicht Benutzern das Speichern von Dateien auf dem hololens-Datenträger mit demselben Datei Dialogfeld wie Windows.  Führen Sie den gleichen Vorgang aus, um zusätzliche Funktionen aus dem hololenswinrtdll-Header zu exportieren und in Unreal verwendet zu werden.  Beachten Sie den DLL-Code, der auf einen asynchronen WinRT-Code in einem MTA-Hintergrund Thread wartet, der das Deadlocks des Unreal Game-Threads vermeidet. 

## <a name="see-also"></a>Siehe auch
* [C++/WinRT-APIs](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [Filesavepicker-Klasse](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [Unreal-Bibliotheken von Drittanbietern](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
