---
title: Implementieren von 3D-App-launchern (Win32-Apps)
description: Erfahren Sie, wie Sie 3D-App-Launcher und-Logos für Win32-VR-apps und-Spiele (außerhalb von Steam) erstellen, sodass Sie im Windows Mixed Reality-Startmenü und in der Home-Umgebung angezeigt werden.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, Logo, Symbol, Modellierung, Start Programm, 3D-Start Programm, Kachel, Live Cube, Win32
ms.openlocfilehash: 87eadfb5184f9fb5f8d513ab00a2a954e71df376
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438574"
---
# <a name="implement-3d-app-launchers-win32-apps"></a><span data-ttu-id="f2097-104">Implementieren von 3D-App-launchern (Win32-Apps)</span><span class="sxs-lookup"><span data-stu-id="f2097-104">Implement 3D app launchers (Win32 apps)</span></span>

> [!NOTE]
> <span data-ttu-id="f2097-105">Diese Funktion ist nur für PCs verfügbar, auf denen die neuesten [Windows-Insider](https://insider.windows.com) -Flüge (RS5), Build 17704 und höher ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="f2097-105">This feature is only available to PCs running the latest [Windows Insider](https://insider.windows.com) flights (RS5), build 17704 and newer.</span></span>

<span data-ttu-id="f2097-106">Der [Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) -Startpunkt ist der Ausgangspunkt, an dem Benutzer vor dem Starten von Anwendungen landen.</span><span class="sxs-lookup"><span data-stu-id="f2097-106">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="f2097-107">Standardmäßig müssen immersive Win32 VR-apps und Spiele von außerhalb des Headsets gestartet werden und werden nicht in der Liste "alle apps" im Windows Mixed Reality-Startmenü angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f2097-107">By default, immersive Win32 VR apps and games have to be launched from outside the headset and won't appear in the "All apps" list on the Windows Mixed Reality Start menu.</span></span> <span data-ttu-id="f2097-108">Wenn Sie jedoch die Anweisungen in diesem Artikel befolgen, um ein 3D-App-Startfeld zu implementieren, können Sie die immersive Win32-VR-Umgebung im Windows Mixed Reality-Startmenü und in der Home-Umgebung starten.</span><span class="sxs-lookup"><span data-stu-id="f2097-108">However, by following the instructions in this article to implement a 3D app launcher, your immersive Win32 VR experience can be launched from within the Windows Mixed Reality Start menu and home environment.</span></span>

<span data-ttu-id="f2097-109">Dies gilt nur für immersive Win32-VR-Erlebnisse, die außerhalb von Steam verteilt sind.</span><span class="sxs-lookup"><span data-stu-id="f2097-109">This is only true for immersive Win32 VR experiences distributied outside of Steam.</span></span> <span data-ttu-id="f2097-110">Bei der durch die Verwendung von [Steam verteilten](updating-your-steamvr-application-for-windows-mixed-reality.md)VR-Oberfläche haben wir [die Windows Mixed Reality für steamvr Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) zusammen mit den neuesten Windows Insider RS5-Flügen aktualisiert, damit die steamvr-Titel im Windows Mixed Reality-Startmenü in der Liste "alle apps" angezeigt werden. Automatisches verwenden eines Standard Start Programms.</span><span class="sxs-lookup"><span data-stu-id="f2097-110">For VR experiences [distributed through Steam](updating-your-steamvr-application-for-windows-mixed-reality.md), we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest Windows Insider RS5 flights so that SteamVR titles show up in the Windows Mixed Reality Start menu in the "All apps" list automatically using a default launcher.</span></span> <span data-ttu-id="f2097-111">Anders ausgedrückt: die in diesem Artikel beschriebene Methode ist für die steamvr-Titel unnötig und wird von der Windows Mixed Reality for steamvr Beta-Funktionalität überschrieben.</span><span class="sxs-lookup"><span data-stu-id="f2097-111">In other words, the method described in this article is unnecessary for SteamVR titles and will be overridden by the Windows Mixed Reality for SteamVR Beta functionality.</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="f2097-112">Erstellung eines 3D-App-Start Programms</span><span class="sxs-lookup"><span data-stu-id="f2097-112">3D app launcher creation process</span></span>

<span data-ttu-id="f2097-113">Zum Erstellen eines 3D-App-Start Programms sind drei Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="f2097-113">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="f2097-114">Entwurf und Konzept</span><span class="sxs-lookup"><span data-stu-id="f2097-114">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="f2097-115">Modellieren und exportieren</span><span class="sxs-lookup"><span data-stu-id="f2097-115">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="f2097-116">Integration in Ihre Anwendung (dieser Artikel)</span><span class="sxs-lookup"><span data-stu-id="f2097-116">Integrating it into your application (this article)</span></span>

<span data-ttu-id="f2097-117">3D-Ressourcen, die als Launcher für Ihre Anwendung verwendet werden sollen, sollten mithilfe der [Windows Mixed Reality Authoring Guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) erstellt werden, um die Kompatibilität zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="f2097-117">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="f2097-118">Assets, die diese Erstellungs Spezifikation nicht erfüllen, werden nicht in der Windows Mixed Reality-Startseite gerendert.</span><span class="sxs-lookup"><span data-stu-id="f2097-118">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="f2097-119">Konfigurieren des 3D-Start Programms</span><span class="sxs-lookup"><span data-stu-id="f2097-119">Configuring the 3D launcher</span></span>

<span data-ttu-id="f2097-120">Win32-Anwendungen werden in der Liste "alle apps" im Windows Mixed Reality-Startmenü angezeigt, wenn Sie ein 3D-App-Startfeld für Sie erstellen.</span><span class="sxs-lookup"><span data-stu-id="f2097-120">Win32 applications will appear in the "All apps" list on the Windows Mixed Reality Start menu if you create a 3D app launcher for them.</span></span> <span data-ttu-id="f2097-121">Erstellen Sie hierzu eine XML- [Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) -XML-Datei, die auf das 3D-App-Startfeld verweist, indem Sie die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="f2097-121">To do that, create a [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML file referencing the 3D App Launcher by following these steps:</span></span>

1. <span data-ttu-id="f2097-122">Erstellen einer Ressource für ein **3D-App-Start** Programm (siehe [modellieren und exportieren](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span><span class="sxs-lookup"><span data-stu-id="f2097-122">Create a **3D App Launcher asset GLB file** (See [Modeling and exporting](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span></span>
2. <span data-ttu-id="f2097-123">Erstellen Sie ein **[visuelles Element Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** für Ihre Anwendung.</span><span class="sxs-lookup"><span data-stu-id="f2097-123">Create a **[Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** for your application.</span></span>
    1. <span data-ttu-id="f2097-124">Sie können mit dem [folgenden Beispiel](#sample-visual-elements-manifest)beginnen.</span><span class="sxs-lookup"><span data-stu-id="f2097-124">You can start with the [sample below](#sample-visual-elements-manifest).</span></span>  <span data-ttu-id="f2097-125">Weitere Informationen finden Sie in der Dokumentation zum vollständigen [visuellen Element Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) .</span><span class="sxs-lookup"><span data-stu-id="f2097-125">See the full [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) documentation for more details.</span></span>
    2. <span data-ttu-id="f2097-126">Aktualisieren Sie **Square150x150Logo** und **Square70x70Logo** mit einem PNG/JPG/GIF für Ihre APP.</span><span class="sxs-lookup"><span data-stu-id="f2097-126">Update **Square150x150Logo** and **Square70x70Logo** with a PNG/JPG/GIF for your app.</span></span>
        * <span data-ttu-id="f2097-127">Diese werden für das 2D-Logo der app in der Windows Mixed Reality all apps-Liste und für das Startmenü auf dem Desktop verwendet.</span><span class="sxs-lookup"><span data-stu-id="f2097-127">These will be used for the app’s 2D logo in the Windows Mixed Reality All Apps list and for the Start Menu on desktop.</span></span>
        * <span data-ttu-id="f2097-128">Der Dateipfad ist relativ zum Ordner, der das visuelle Element Manifest enthält.</span><span class="sxs-lookup"><span data-stu-id="f2097-128">The file path is relative to the folder containing the Visual Elements Manifest.</span></span>
        * <span data-ttu-id="f2097-129">Sie müssen immer noch ein Desktop-Start Menü Symbol für Ihre APP über die Standardmechanismen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="f2097-129">You still need to provide a desktop Start Menu icon for your app through the standard mechanisms.</span></span> <span data-ttu-id="f2097-130">Dies kann entweder direkt in der ausführbaren Datei oder in der von Ihnen erstellten Verknüpfung erfolgen (z. b. über IShellLink:: "conticonlocation").</span><span class="sxs-lookup"><span data-stu-id="f2097-130">This can either be directly in the executable or in the shortcut you create (e.g. via IShellLink::SetIconLocation).</span></span>
        * <span data-ttu-id="f2097-131">*Optional:* Sie können eine "Resources. pri"-Datei verwenden, wenn Sie möchten, dass für MRT mehrere assetgrößen für verschiedene Auflösungs Skalen und Designs mit hohem Kontrast bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="f2097-131">*Optional:* You can use a resources.pri file if you would like for MRT to provide multiple asset sizes for different resolution scales and high contrast themes.</span></span>
    3. <span data-ttu-id="f2097-132">Aktualisieren Sie den **Pfad von mixedrealitymodel** , sodass er auf den GLB für das 3D-App-Startfeld verweist.</span><span class="sxs-lookup"><span data-stu-id="f2097-132">Update the **MixedRealityModel Path** to point to the GLB for your 3D App Launcher</span></span>
    4. <span data-ttu-id="f2097-133">Speichern Sie die Datei mit dem gleichen Namen wie die ausführbare Datei mit der Erweiterung ". Visualelementsmanifest. xml ", und speichern Sie Sie im selben Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="f2097-133">Save the file with the same name as your executable file, with an extension of ".VisualElementsManifest.xml" and save it in the same directory.</span></span> <span data-ttu-id="f2097-134">Beispielsweise wird für die ausführbare Datei "CSO. exe" die zugehörige XML-Datei mit dem Namen "Configuration. visualelementsmanifest. xml" benannt.</span><span class="sxs-lookup"><span data-stu-id="f2097-134">For example, for the executable file "contoso.exe", the accompanying XML file is named "contoso.visualelementsmanifest.xml".</span></span>
3. <span data-ttu-id="f2097-135">Fügen Sie dem Desktop Windows-Startmenü **eine Verknüpfung** zu Ihrer Anwendung hinzu.</span><span class="sxs-lookup"><span data-stu-id="f2097-135">**Add a shortcut** to your application to the desktop Windows Start Menu.</span></span> <span data-ttu-id="f2097-136">Im [folgenden](#sample-app-launcher-shortcut-creation) Beispiel finden Sie eine Beispiel C++ Implementierung.</span><span class="sxs-lookup"><span data-stu-id="f2097-136">See the [sample below](#sample-app-launcher-shortcut-creation) for an example C++ implementation.</span></span> 
    * <span data-ttu-id="f2097-137">Erstellen Sie die Datei unter%ALLUSERSPROFILE%\Microsoft\Windows\Start menu\programme (Machine) oder%APPDATA%\Microsoft\Windows\Start menu\programme (User).</span><span class="sxs-lookup"><span data-stu-id="f2097-137">Create it in %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) or %APPDATA%\Microsoft\Windows\Start Menu\Programs (user)</span></span>
    * <span data-ttu-id="f2097-138">Wenn ein Update das Manifest der visuellen Elemente oder die darin referenzierten Ressourcen ändert, sollte der Updater oder Installer die Verknüpfung aktualisieren, sodass das Manifest neu analysiert und zwischengespeicherte Objekte aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="f2097-138">If an update changes your visual elements manifest or the assets referenced by it, the updater or installer should update the shortcut such that the manifest is reparsed and cached assets are updated.</span></span>
4. <span data-ttu-id="f2097-139">*Optional:* Wenn die Desktop Verknüpfung nicht direkt auf die exe-Datei der Anwendung zeigt (z. b., wenn Sie einen benutzerdefinierten Protokollhandler wie "MyApp://" aufruft), findet das Startmenü nicht automatisch die Datei "visualelementsmanifest. xml" der app.</span><span class="sxs-lookup"><span data-stu-id="f2097-139">*Optional:* If your desktop shortcut does not point directly to your application’s EXE (e.g., if it invokes a custom protocol handler like “myapp://”), the Start Menu won’t automatically find the app’s VisualElementsManifest.xml file.</span></span> <span data-ttu-id="f2097-140">Um dieses Problem zu beheben, sollte in der Verknüpfung der Dateipfad des visuellen Element Manifests mithilfe von System. appusermodel. visualelementsmanifesthintpath () angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="f2097-140">To resolve this, the shortcut should specify the file path of the Visual Elements Manifest using System.AppUserModel.VisualElementsManifestHintPath ().</span></span> <span data-ttu-id="f2097-141">Dies kann in der Verknüpfung mit denselben Techniken wie System.AppUserModel.ID festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="f2097-141">This can be set in the shortcut using the same techniques as System.AppUserModel.ID.</span></span> <span data-ttu-id="f2097-142">Sie müssen System.AppUserModel.ID nicht verwenden, aber Sie können dies tun, wenn die Verknüpfung mit der expliziten Anwendungs Benutzer Modell-ID der Anwendung abgeglichen werden soll, wenn eine solche verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f2097-142">You are not required to use System.AppUserModel.ID but you may do so if you wish for the shortcut to match the explicit Application User Model ID of the application if one is used.</span></span>  <span data-ttu-id="f2097-143">Ein C++ Beispiel finden Sie im Abschnitt zur [Erstellung von Beispielen](#sample-app-launcher-shortcut-creation) für das App-Start Programm.</span><span class="sxs-lookup"><span data-stu-id="f2097-143">See the [sample app launcher shortcut creation](#sample-app-launcher-shortcut-creation) section below for a C++ sample.</span></span>

### <a name="sample-visual-elements-manifest"></a><span data-ttu-id="f2097-144">Beispiel für visuelle Element Manifeste</span><span class="sxs-lookup"><span data-stu-id="f2097-144">Sample Visual Elements Manifest</span></span>

```xml
<Application xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance">
  <VisualElements
    ShowNameOnSquare150x150Logo="on"
    Square150x150Logo="YOUR_APP_LOGO_150X150.png"
    Square70x70Logo=" YOUR_APP_LOGO_70X70.png"
    ForegroundText="light"
    BackgroundColor="#000000">
    <MixedRealityModel Path="YOUR_3D_APP_LAUNCHER_ASSET.glb">
        <SpatialBoundingBox Center="0,0,0" Extents="Auto" />
    </MixedRealityModel>
  </VisualElements>
</Application>
```

### <a name="sample-app-launcher-shortcut-creation"></a><span data-ttu-id="f2097-145">Beispiel Erstellung für App-Start Programm Verknüpfung</span><span class="sxs-lookup"><span data-stu-id="f2097-145">Sample app launcher shortcut creation</span></span>

<span data-ttu-id="f2097-146">Der folgende Beispielcode zeigt, wie Sie eine Verknüpfung in C++erstellen können, einschließlich der Überschreibung der Pfad zur XML-Datei des visuellen Elements.</span><span class="sxs-lookup"><span data-stu-id="f2097-146">The sample code below shows how you can create a shortcut in C++, including overriding the path to the Visual Elements Manifest XML file.</span></span> <span data-ttu-id="f2097-147">Beachten Sie, dass die außer Kraft Setzung nur in Fällen erforderlich ist, in denen die Verknüpfung nicht direkt auf die dem Manifest zugeordnete exe verweist (z. b.</span><span class="sxs-lookup"><span data-stu-id="f2097-147">Note the override is only required in cases where your shortcut does not point directly to the EXE associated with the manifest (eg.</span></span> <span data-ttu-id="f2097-148">die Verknüpfung verwendet einen benutzerdefinierten Protokollhandler wie "MyApp://").</span><span class="sxs-lookup"><span data-stu-id="f2097-148">your shortcut uses a custom protocol handler like "myapp://").</span></span>

#### <a name="sample-lnk-shortcut-creation-c"></a><span data-ttu-id="f2097-149">Blutprobe. Lnk-VerknüpfungsC++Erstellung ()</span><span class="sxs-lookup"><span data-stu-id="f2097-149">Sample .LNK shortcut creation (C++)</span></span>

```cpp
#include <windows.h>
#include <propkey.h>
#include <shlobj_core.h>
#include <shlwapi.h>
#include <propvarutil.h>
#include <wrl.h>

#include <memory>

using namespace Microsoft::WRL;

#define RETURN_IF_FAILED(x) do { HRESULT hr = x; if (FAILED(hr)) { return hr; } } while(0)
#define RETURN_IF_WIN32_BOOL_FALSE(x) do { DWORD res = x; if (res == 0) { return HRESULT_FROM_WIN32(GetLastError()); } } while(0)

int wmain()
{
    RETURN_IF_FAILED(CoInitializeEx(nullptr, COINIT_APARTMENTTHREADED));

    ComPtr<IShellLink> shellLink;
    RETURN_IF_FAILED(CoCreateInstance(__uuidof(ShellLink), nullptr, CLSCTX_INPROC_SERVER, IID_PPV_ARGS(&shellLink)));
    RETURN_IF_FAILED(shellLink->SetPath(L"MyLauncher://launch/app-identifier"));

    // It is also possible to use an icon file in another location. For example, "C:\Program Files (x86)\MyLauncher\assets\app-identifier.ico".
    RETURN_IF_FAILED(shellLink->SetIconLocation(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.exe", 0 /*iIcon*/));

    ComPtr<IPropertyStore> propStore;
    RETURN_IF_FAILED(shellLink.As(&propStore));

    {
        // Optional: If the application has an explict Application User Model ID, then you should usually specify it in the shortcut.
        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"ExplicitAppUserModelID", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_ID, propVar));
        PropVariantClear(&propVar);
    }

    {
        // A hint path to the manifest is only necessary if the target path of the shortcut is not a file path to the executable.
        // By convention the manifest is named <executable name>.VisualElementsManifest.xml and is in the same folder as the executable
        // (and resources.pri if applicable). Assets referenced by the manifest are relative to the folder containing the manifest.

        //
        // PropKey.h
        //
        //  Name:     System.AppUserModel.VisualElementsManifestHintPath -- PKEY_AppUserModel_VisualElementsManifestHintPath
        //  Type:     String -- VT_LPWSTR  (For variants: VT_BSTR)
        //  FormatID: {9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}, 31
        //  
        //  Suggests where to look for the VisualElementsManifest for a Win32 app
        //
        // DEFINE_PROPERTYKEY(PKEY_AppUserModel_VisualElementsManifestHintPath, 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3, 31);
        // #define INIT_PKEY_AppUserModel_VisualElementsManifestHintPath { { 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3 }, 31 }

        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.visualelementsmanifest.xml", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_VisualElementsManifestHintPath, propVar));
        PropVariantClear(&propVar);
    }

    constexpr PCWSTR shortcutPath = L"%APPDATA%\\Microsoft\\Windows\\Start Menu\\Programs\\game.lnk";
    const DWORD requiredBufferLength = ExpandEnvironmentStrings(shortcutPath, nullptr, 0);
    RETURN_IF_WIN32_BOOL_FALSE(requiredBufferLength);

    const auto expandedShortcutPath = std::make_unique<wchar_t[]>(requiredBufferLength);
    RETURN_IF_WIN32_BOOL_FALSE(ExpandEnvironmentStrings(shortcutPath, expandedShortcutPath.get(), requiredBufferLength));

    ComPtr<IPersistFile> persistFile;
    RETURN_IF_FAILED(shellLink.As(&persistFile));
    RETURN_IF_FAILED(persistFile->Save(expandedShortcutPath.get(), FALSE));

    return 0;
}
```

#### <a name="sample-url-launcher-shortcut"></a><span data-ttu-id="f2097-150">Blutprobe. URL-Start Programm Verknüpfung</span><span class="sxs-lookup"><span data-stu-id="f2097-150">Sample .URL launcher shortcut</span></span> 

```
[{9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}]
Prop31=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.visualelementsmanifest.xml
Prop5=ExplicitAppUserModelID

[{000214A0-0000-0000-C000-000000000046}]
Prop3=19,0

[InternetShortcut]
IDList=
URL=MyLauncher://launch/app-identifier
IconFile=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.exe
IconIndex=0
```

## <a name="see-also"></a><span data-ttu-id="f2097-151">Weitere Informationen:</span><span class="sxs-lookup"><span data-stu-id="f2097-151">See also</span></span>

* <span data-ttu-id="f2097-152">[Gemischtes Reality-Modell Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) mit einem 3D-App-Start Programm.</span><span class="sxs-lookup"><span data-stu-id="f2097-152">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="f2097-153">Entwurfsanleitung für 3D-App-Startprogramm</span><span class="sxs-lookup"><span data-stu-id="f2097-153">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="f2097-154">Erstellen von 3D-Modellen für die Verwendung in der Windows Mixed Reality-Startseite</span><span class="sxs-lookup"><span data-stu-id="f2097-154">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="f2097-155">Implementieren von 3D-App-launchern (UWP-Apps)</span><span class="sxs-lookup"><span data-stu-id="f2097-155">Implementing 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="f2097-156">Navigieren auf der Startseite von Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f2097-156">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
