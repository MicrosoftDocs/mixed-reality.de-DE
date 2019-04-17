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
# <a name="implement-3d-app-launchers-win32-apps"></a>Implementieren von 3D app-startfeldern von (Win32-apps)

> [!NOTE]
> Dieses Feature steht nur für PCs mit den neuesten [Windows Insider](https://insider.windows.com) Flüge (RS5), Build 17704 und höher.

Die [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) ist der Ausgangspunkt, in denen Benutzer weitergeleitet, vor dem Starten von Anwendungen. Standardmäßig können Sie immersive Win32-VR-apps und Spiele müssen Sie von außerhalb der Kopfhörer gestartet werden und wird nicht in der Liste "Alle apps" auf Windows Mixed Reality-Startmenü angezeigt. Allerdings kann mithilfe der Anweisungen in diesem Artikel eine-3D-app-Startfeld implementieren, Ihre Win32-VR-Eintauchen von in die Windows Mixed Reality-Startmenü und die home-Umgebung gestartet werden.

Dies ist nur für immersive Distributied der Win32-VR-Umgebungen außerhalb von Stream "true". VR-Funktionen zu nutzen [über Stream verteilt](updating-your-steamvr-application-for-windows-mixed-reality.md), haben wir [aktualisiert, die Windows Mixed Reality für SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) zusammen mit den neuesten Windows Insider RS5 Flügen, sodass SteamVR zeigen Sie in der Windows titles Mixed Reality Menü "Start" in der Liste "Alle apps", die automatisch mit einer Standard-Startprogramm. Das heißt, die in diesem Artikel beschriebene Methode ist nicht erforderlich für SteamVR Titel und wird durch die Windows Mixed Reality für SteamVR Beta Funktionen überschrieben werden.

## <a name="3d-app-launcher-creation-process"></a>3D app-Startprogramm-Erstellungsprozess

Es gibt 3 Schritte zum Erstellen einer-3D-app-Startfeld:
1. [Entwerfen und concepting](3d-app-launcher-design-guidance.md)
2. [Modellieren und exportieren](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Die Integration in Ihre Anwendung (in diesem Artikel)

3D-Objekte verwendet werden, wie mithilfe Startprogramme für Ihre Anwendung erstellt werden soll die [Windows Mixed Reality Erstellen von Richtlinien](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) um die Kompatibilität sicherzustellen. Ressourcen, die diese Spezifikation authoring einhalten werden nicht in die Windows Mixed Reality home gerendert werden.

## <a name="configuring-the-3d-launcher"></a>Konfigurieren das Startprogramm 3D

Win32-Anwendungen werden in der Liste "Alle apps" auf Windows Mixed Reality-Startmenü angezeigt, wenn Sie eine-3D-app-Startfeld für sie erstellen. Zu diesem Zweck erstellen Sie eine [visuelle Elemente Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) XML-Datei verweisen auf das App-Startfeld 3D mit folgenden Schritten:

1. Erstellen Sie eine **3D-App-Startfeld GLB medienobjektdatei** (finden Sie unter [Crashmodellierungen und Exportieren von](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).
2. Erstellen Sie eine **[visuelle Elemente Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** für Ihre Anwendung.
    1. Beginnen Sie mit der [Untenstehendes](#sample-visual-elements-manifest).  Die vollständige [visuelle Elemente Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) Dokumentation.
    2. Update **Square150x150Logo** und **Square70x70Logo** mit einem PNG/JPG/GIF für Ihre app.
        * Diese werden für die app 2D-Logo in der Liste der Windows Mixed Reality alle Apps und für das Menü Start auf Desktop verwendet werden.
        * Der Pfad ist relativ zum Ordner, der die visuellen Elemente-Manifest enthält.
        * Sie müssen weiterhin auf einen Desktop-Menü "Start"-Symbol für Ihre app über die Standardmechanismen angeben. Dies kann entweder sein, direkt in die ausführbare Datei oder in der Verknüpfung, die Sie (z.B. über die IShellLink::SetIconLocation) zu erstellen.
        * *Optional:* Sie können eine resources.pri-Datei verwenden, wenn Sie für einen MRT mehrere Asset-Größen für andere Auflösung skaliert und Designs mit hohem Kontrast bereitstellen möchten.
    3. Update der **MixedRealityModel Pfad** , zeigen Sie auf der GLB für Ihre App-Startfeld von 3D
    4. Speichern Sie die Datei mit dem gleichen Namen wie die ausführbare Datei, mit der Erweiterung ". VisualElementsManifest.xml", und speichern Sie es im selben Verzeichnis. Beispielsweise ist die zugehörige XML-Datei für die ausführbare Datei "contoso.exe", "contoso.visualelementsmanifest.xml" benannt.
3. **Hinzufügen einer Verknüpfung** auf die Anwendung auf dem desktop Windows-Startmenü. Finden Sie unter den [Untenstehendes](#sample-app-launcher-shortcut-creation) ein Beispiel für C++ Implementierung. 
    * Erstellen Sie es in %ALLUSERSPROFILE%\Microsoft\Windows\Start \Programme (Computer) oder %APPDATA%\Microsoft\Windows\Start \Programme (Benutzer)
    * Wenn ein Update Ihr Manifest visuelle Elemente oder die Ressourcen, die es verweist ändert, sollte der Updater oder das Installationsprogramm die Verknüpfung aktualisieren, so, dass das Manifest erneut analysiert wird und zwischengespeicherten Assets werden aktualisiert.
4. *Optional:* Wenn es sich bei Ihrer desktop-Verknüpfung nicht direkt auf Ihrer Anwendung exe-Datei verweist (z. B. wenn er einen benutzerdefiniertes Protokollhandler wie ruft "" MyApp ": / /"), im Startmenü nicht automatisch der Datei VisualElementsManifest.xml finden. Um dies zu beheben, sollten die Verknüpfung den Dateipfad der visuellen Elemente Anwendungsmanifest mit System.AppUserModel.VisualElementsManifestHintPath (-) angeben. Dies kann in der Verknüpfung mit den gleichen Verfahren wie System.AppUserModel.ID festgelegt werden. Sie sind nicht erforderlich, um System.AppUserModel.ID verwenden, aber Sie können dies tun werden, wenn Sie möchten, für die Verknüpfung für die explizite Anwendung Benutzer-Modell-ID der Anwendung zu entsprechen, sofern einer verwendet wird.  Finden Sie unter den [Beispiel-app-Startfeld Erstellen einer Verknüpfung](#sample-app-launcher-shortcut-creation) im nachfolgenden Abschnitt eine C++ Beispiel.

### <a name="sample-visual-elements-manifest"></a>Visuelle Elemente Beispielmanifest

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

### <a name="sample-app-launcher-shortcut-creation"></a>Erstellen einer Beispiel-app-Startfeld Verknüpfung

Der folgende Beispielcode zeigt, wie Sie eine Verknüpfung erstellen können C++, einschließlich den Pfad zu der visuellen Elemente Manifest-XML-Datei zu überschreiben. Beachten Sie die Außerkraftsetzung ist nur in Fällen erforderlich, in dem Ihre Verknüpfung nicht direkt auf die EXE-Datei mit dem Manifest verknüpft ist, (z. b. verweist die Verknüpfung zu Ihrem verwendet einen benutzerdefiniertes Protokollhandler wie "" MyApp ": / /").

#### <a name="sample-lnk-shortcut-creation-c"></a>Ein Beispiel. Erstellen einer Verknüpfung LNK (C++)

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

#### <a name="sample-url-launcher-shortcut"></a>Ein Beispiel. Die URL-Startprogramm-Verknüpfung 

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

## <a name="see-also"></a>Siehe auch

* [Mixed Reality-modellbeispiels](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) , die eine-3D-app-Startfeld enthält.
* [Leitfaden zum Entwerfen von 3D app-Startfeld](3d-app-launcher-design-guidance.md)
* [Erstellen von 3D-Modellen für die Verwendung zu Hause Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementieren von 3D app-startfeldern von (UWP-apps)](implementing-3d-app-launchers.md)
* [Navigieren Sie in der Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md)
