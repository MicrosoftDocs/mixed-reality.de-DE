---
title: Implementieren von 3D app-startfeldern von (Win32-apps)
description: Wie zum Erstellen von 3D app-startfeldern und Logos für Win32-VR-apps und Spiele (außerhalb von Stream verteilt) daher sie in der Windows Mixed Reality starten im Menü und die Startseite angezeigt.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, Logo, Symbol, Modellierung, Startprogramm, 3D Startprogramm, Kachel, live-Cube, win32
ms.openlocfilehash: ac3d5e17614bcd1072f6843a46bf0525f441f130
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594650"
---
# <a name="implement-3d-app-launchers-win32-apps"></a><span data-ttu-id="24c26-104">Implementieren von 3D app-startfeldern von (Win32-apps)</span><span class="sxs-lookup"><span data-stu-id="24c26-104">Implement 3D app launchers (Win32 apps)</span></span>

> [!NOTE]
> <span data-ttu-id="24c26-105">Dieses Feature steht nur für PCs mit den neuesten [Windows Insider](https://insider.windows.com) Flüge (RS5), Build 17704 und höher.</span><span class="sxs-lookup"><span data-stu-id="24c26-105">This feature is only available to PCs running the latest [Windows Insider](https://insider.windows.com) flights (RS5), build 17704 and newer.</span></span>

<span data-ttu-id="24c26-106">Die [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) ist der Ausgangspunkt, in denen Benutzer weitergeleitet, vor dem Starten von Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="24c26-106">The [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="24c26-107">Standardmäßig können Sie immersive Win32-VR-apps und Spiele müssen Sie von außerhalb der Kopfhörer gestartet werden und wird nicht in der Liste "Alle apps" auf Windows Mixed Reality-Startmenü angezeigt.</span><span class="sxs-lookup"><span data-stu-id="24c26-107">By default, immersive Win32 VR apps and games have to be launched from outside the headset and won't appear in the "All apps" list on the Windows Mixed Reality Start menu.</span></span> <span data-ttu-id="24c26-108">Allerdings kann mithilfe der Anweisungen in diesem Artikel eine-3D-app-Startfeld implementieren, Ihre Win32-VR-Eintauchen von in die Windows Mixed Reality-Startmenü und die home-Umgebung gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="24c26-108">However, by following the instructions in this article to implement a 3D app launcher, your immersive Win32 VR experience can be launched from within the Windows Mixed Reality Start menu and home environment.</span></span>

<span data-ttu-id="24c26-109">Dies ist nur für immersive Distributied der Win32-VR-Umgebungen außerhalb von Stream "true".</span><span class="sxs-lookup"><span data-stu-id="24c26-109">This is only true for immersive Win32 VR experiences distributied outside of Steam.</span></span> <span data-ttu-id="24c26-110">VR-Funktionen zu nutzen [über Stream verteilt](updating-your-steamvr-application-for-windows-mixed-reality.md), haben wir [aktualisiert, die Windows Mixed Reality für SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) zusammen mit den neuesten Windows Insider RS5 Flügen, sodass SteamVR zeigen Sie in der Windows titles Mixed Reality Menü "Start" in der Liste "Alle apps", die automatisch mit einer Standard-Startprogramm.</span><span class="sxs-lookup"><span data-stu-id="24c26-110">For VR experiences [distributed through Steam](updating-your-steamvr-application-for-windows-mixed-reality.md), we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest Windows Insider RS5 flights so that SteamVR titles show up in the Windows Mixed Reality Start menu in the "All apps" list automatically using a default launcher.</span></span> <span data-ttu-id="24c26-111">Das heißt, die in diesem Artikel beschriebene Methode ist nicht erforderlich für SteamVR Titel und wird durch die Windows Mixed Reality für SteamVR Beta Funktionen überschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="24c26-111">In other words, the method described in this article is unnecessary for SteamVR titles and will be overridden by the Windows Mixed Reality for SteamVR Beta functionality.</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="24c26-112">3D app-Startprogramm-Erstellungsprozess</span><span class="sxs-lookup"><span data-stu-id="24c26-112">3D app launcher creation process</span></span>

<span data-ttu-id="24c26-113">Es gibt 3 Schritte zum Erstellen einer-3D-app-Startfeld:</span><span class="sxs-lookup"><span data-stu-id="24c26-113">There are 3 steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="24c26-114">Entwerfen und concepting</span><span class="sxs-lookup"><span data-stu-id="24c26-114">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="24c26-115">Modellieren und exportieren</span><span class="sxs-lookup"><span data-stu-id="24c26-115">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="24c26-116">Die Integration in Ihre Anwendung (in diesem Artikel)</span><span class="sxs-lookup"><span data-stu-id="24c26-116">Integrating it into your application (this article)</span></span>

<span data-ttu-id="24c26-117">3D-Objekte verwendet werden, wie mithilfe Startprogramme für Ihre Anwendung erstellt werden soll die [Windows Mixed Reality Erstellen von Richtlinien](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) um die Kompatibilität sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="24c26-117">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="24c26-118">Ressourcen, die diese Spezifikation authoring einhalten werden nicht in die Windows Mixed Reality home gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="24c26-118">Assets that fail to meet this authoring specification will not be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="24c26-119">Konfigurieren das Startprogramm 3D</span><span class="sxs-lookup"><span data-stu-id="24c26-119">Configuring the 3D launcher</span></span>

<span data-ttu-id="24c26-120">Win32-Anwendungen werden in der Liste "Alle apps" auf Windows Mixed Reality-Startmenü angezeigt, wenn Sie eine-3D-app-Startfeld für sie erstellen.</span><span class="sxs-lookup"><span data-stu-id="24c26-120">Win32 applications will appear in the "All apps" list on the Windows Mixed Reality Start menu if you create a 3D app launcher for them.</span></span> <span data-ttu-id="24c26-121">Zu diesem Zweck erstellen Sie eine [visuelle Elemente Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML-Datei verweisen auf das App-Startfeld 3D mit folgenden Schritten:</span><span class="sxs-lookup"><span data-stu-id="24c26-121">To do that, create a [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML file referencing the 3D App Launcher by following these steps:</span></span>

1. <span data-ttu-id="24c26-122">Erstellen Sie eine **3D-App-Startfeld GLB medienobjektdatei** (finden Sie unter [Crashmodellierungen und Exportieren von](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span><span class="sxs-lookup"><span data-stu-id="24c26-122">Create a **3D App Launcher asset GLB file** (See [Modeling and exporting](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).</span></span>
2. <span data-ttu-id="24c26-123">Erstellen Sie eine **[visuelle Elemente Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** für Ihre Anwendung.</span><span class="sxs-lookup"><span data-stu-id="24c26-123">Create a **[Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** for your application.</span></span>
    1. <span data-ttu-id="24c26-124">Beginnen Sie mit der [Untenstehendes](#sample-visual-elements-manifest).</span><span class="sxs-lookup"><span data-stu-id="24c26-124">You can start with the [sample below](#sample-visual-elements-manifest).</span></span>  <span data-ttu-id="24c26-125">Die vollständige [visuelle Elemente Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="24c26-125">See the full [Visual Elements Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) documentation for more details.</span></span>
    2. <span data-ttu-id="24c26-126">Update **Square150x150Logo** und **Square70x70Logo** mit einem PNG/JPG/GIF für Ihre app.</span><span class="sxs-lookup"><span data-stu-id="24c26-126">Update **Square150x150Logo** and **Square70x70Logo** with a PNG/JPG/GIF for your app.</span></span>
        * <span data-ttu-id="24c26-127">Diese werden für die app 2D-Logo in der Liste der Windows Mixed Reality alle Apps und für das Menü Start auf Desktop verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="24c26-127">These will be used for the app’s 2D logo in the Windows Mixed Reality All Apps list and for the Start Menu on desktop.</span></span>
        * <span data-ttu-id="24c26-128">Der Pfad ist relativ zum Ordner, der die visuellen Elemente-Manifest enthält.</span><span class="sxs-lookup"><span data-stu-id="24c26-128">The file path is relative to the folder containing the Visual Elements Manifest.</span></span>
        * <span data-ttu-id="24c26-129">Sie müssen weiterhin auf einen Desktop-Menü "Start"-Symbol für Ihre app über die Standardmechanismen angeben.</span><span class="sxs-lookup"><span data-stu-id="24c26-129">You still need to provide a desktop Start Menu icon for your app through the standard mechanisms.</span></span> <span data-ttu-id="24c26-130">Dies kann entweder sein, direkt in die ausführbare Datei oder in der Verknüpfung, die Sie (z.B. über die IShellLink::SetIconLocation) zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="24c26-130">This can either be directly in the executable or in the shortcut you create (e.g. via IShellLink::SetIconLocation).</span></span>
        * <span data-ttu-id="24c26-131">*Optional:* Sie können eine resources.pri-Datei verwenden, wenn Sie für einen MRT mehrere Asset-Größen für andere Auflösung skaliert und Designs mit hohem Kontrast bereitstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="24c26-131">*Optional:* You can use a resources.pri file if you would like for MRT to provide multiple asset sizes for different resolution scales and high contrast themes.</span></span>
    3. <span data-ttu-id="24c26-132">Update der **MixedRealityModel Pfad** , zeigen Sie auf der GLB für Ihre App-Startfeld von 3D</span><span class="sxs-lookup"><span data-stu-id="24c26-132">Update the **MixedRealityModel Path** to point to the GLB for your 3D App Launcher</span></span>
    4. <span data-ttu-id="24c26-133">Speichern Sie die Datei mit dem gleichen Namen wie die ausführbare Datei, mit der Erweiterung ". VisualElementsManifest.xml", und speichern Sie es im selben Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="24c26-133">Save the file with the same name as your executable file, with an extension of ".VisualElementsManifest.xml" and save it in the same directory.</span></span> <span data-ttu-id="24c26-134">Beispielsweise ist die zugehörige XML-Datei für die ausführbare Datei "contoso.exe", "contoso.visualelementsmanifest.xml" benannt.</span><span class="sxs-lookup"><span data-stu-id="24c26-134">For example, for the executable file "contoso.exe", the accompanying XML file is named "contoso.visualelementsmanifest.xml".</span></span>
3. <span data-ttu-id="24c26-135">**Hinzufügen einer Verknüpfung** auf die Anwendung auf dem desktop Windows-Startmenü.</span><span class="sxs-lookup"><span data-stu-id="24c26-135">**Add a shortcut** to your application to the desktop Windows Start Menu.</span></span> <span data-ttu-id="24c26-136">Finden Sie unter den [Untenstehendes](#sample-app-launcher-shortcut-creation) ein Beispiel für C++ Implementierung.</span><span class="sxs-lookup"><span data-stu-id="24c26-136">See the [sample below](#sample-app-launcher-shortcut-creation) for an example C++ implementation.</span></span> 
    * <span data-ttu-id="24c26-137">Erstellen Sie es in %ALLUSERSPROFILE%\Microsoft\Windows\Start \Programme (Computer) oder %APPDATA%\Microsoft\Windows\Start \Programme (Benutzer)</span><span class="sxs-lookup"><span data-stu-id="24c26-137">Create it in %ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs (machine) or %APPDATA%\Microsoft\Windows\Start Menu\Programs (user)</span></span>
    * <span data-ttu-id="24c26-138">Wenn ein Update Ihr Manifest visuelle Elemente oder die Ressourcen, die es verweist ändert, sollte der Updater oder das Installationsprogramm die Verknüpfung aktualisieren, so, dass das Manifest erneut analysiert wird und zwischengespeicherten Assets werden aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="24c26-138">If an update changes your visual elements manifest or the assets referenced by it, the updater or installer should update the shortcut such that the manifest is reparsed and cached assets are updated.</span></span>
4. <span data-ttu-id="24c26-139">*Optional:* Wenn es sich bei Ihrer desktop-Verknüpfung nicht direkt auf Ihrer Anwendung exe-Datei verweist (z. B. wenn er einen benutzerdefiniertes Protokollhandler wie ruft "" MyApp ": / /"), im Startmenü nicht automatisch der Datei VisualElementsManifest.xml finden.</span><span class="sxs-lookup"><span data-stu-id="24c26-139">*Optional:* If your desktop shortcut does not point directly to your application’s EXE (e.g., if it invokes a custom protocol handler like “myapp://”), the Start Menu won’t automatically find the app’s VisualElementsManifest.xml file.</span></span> <span data-ttu-id="24c26-140">Um dies zu beheben, sollten die Verknüpfung den Dateipfad der visuellen Elemente Anwendungsmanifest mit System.AppUserModel.VisualElementsManifestHintPath (-) angeben.</span><span class="sxs-lookup"><span data-stu-id="24c26-140">To resolve this, the shortcut should specify the file path of the Visual Elements Manifest using System.AppUserModel.VisualElementsManifestHintPath ().</span></span> <span data-ttu-id="24c26-141">Dies kann in der Verknüpfung mit den gleichen Verfahren wie System.AppUserModel.ID festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="24c26-141">This can be set in the shortcut using the same techniques as System.AppUserModel.ID.</span></span> <span data-ttu-id="24c26-142">Sie sind nicht erforderlich, um System.AppUserModel.ID verwenden, aber Sie können dies tun werden, wenn Sie möchten, für die Verknüpfung für die explizite Anwendung Benutzer-Modell-ID der Anwendung zu entsprechen, sofern einer verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="24c26-142">You are not required to use System.AppUserModel.ID but you may do so if you wish for the shortcut to match the explicit Application User Model ID of the application if one is used.</span></span>  <span data-ttu-id="24c26-143">Finden Sie unter den [Beispiel-app-Startfeld Erstellen einer Verknüpfung](#sample-app-launcher-shortcut-creation) im nachfolgenden Abschnitt eine C++ Beispiel.</span><span class="sxs-lookup"><span data-stu-id="24c26-143">See the [sample app launcher shortcut creation](#sample-app-launcher-shortcut-creation) section below for a C++ sample.</span></span>

### <a name="sample-visual-elements-manifest"></a><span data-ttu-id="24c26-144">Visuelle Elemente Beispielmanifest</span><span class="sxs-lookup"><span data-stu-id="24c26-144">Sample Visual Elements Manifest</span></span>

```xml
<Application xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
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

### <a name="sample-app-launcher-shortcut-creation"></a><span data-ttu-id="24c26-145">Erstellen einer Beispiel-app-Startfeld Verknüpfung</span><span class="sxs-lookup"><span data-stu-id="24c26-145">Sample app launcher shortcut creation</span></span>

<span data-ttu-id="24c26-146">Der folgende Beispielcode zeigt, wie Sie eine Verknüpfung erstellen können C++, einschließlich den Pfad zu der visuellen Elemente Manifest-XML-Datei zu überschreiben.</span><span class="sxs-lookup"><span data-stu-id="24c26-146">The sample code below shows how you can create a shortcut in C++, including overriding the path to the Visual Elements Manifest XML file.</span></span> <span data-ttu-id="24c26-147">Beachten Sie die Außerkraftsetzung ist nur in Fällen erforderlich, in dem Ihre Verknüpfung nicht direkt auf die EXE-Datei mit dem Manifest verknüpft ist, (z. b. verweist</span><span class="sxs-lookup"><span data-stu-id="24c26-147">Note the override is only required in cases where your shortcut does not point directly to the EXE associated with the manifest (eg.</span></span> <span data-ttu-id="24c26-148">die Verknüpfung zu Ihrem verwendet einen benutzerdefiniertes Protokollhandler wie "" MyApp ": / /").</span><span class="sxs-lookup"><span data-stu-id="24c26-148">your shortcut uses a custom protocol handler like "myapp://").</span></span>

#### <a name="sample-lnk-shortcut-creation-c"></a><span data-ttu-id="24c26-149">Ein Beispiel. Erstellen einer Verknüpfung LNK (C++)</span><span class="sxs-lookup"><span data-stu-id="24c26-149">Sample .LNK shortcut creation (C++)</span></span>

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

#### <a name="sample-url-launcher-shortcut"></a><span data-ttu-id="24c26-150">Ein Beispiel. Die URL-Startprogramm-Verknüpfung</span><span class="sxs-lookup"><span data-stu-id="24c26-150">Sample .URL launcher shortcut</span></span> 

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

## <a name="see-also"></a><span data-ttu-id="24c26-151">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="24c26-151">See also</span></span>

* <span data-ttu-id="24c26-152">[Mixed Reality-modellbeispiels](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) , die eine-3D-app-Startfeld enthält.</span><span class="sxs-lookup"><span data-stu-id="24c26-152">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="24c26-153">Leitfaden zum Entwerfen von 3D app-Startfeld</span><span class="sxs-lookup"><span data-stu-id="24c26-153">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="24c26-154">Erstellen von 3D-Modellen für die Verwendung zu Hause Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="24c26-154">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="24c26-155">Implementieren von 3D app-startfeldern von (UWP-apps)</span><span class="sxs-lookup"><span data-stu-id="24c26-155">Implementing 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="24c26-156">Navigieren Sie in der Windows Mixed Reality home</span><span class="sxs-lookup"><span data-stu-id="24c26-156">Navigating the Windows Mixed Reality home</span></span>](navigating-the-windows-mixed-reality-home.md)
