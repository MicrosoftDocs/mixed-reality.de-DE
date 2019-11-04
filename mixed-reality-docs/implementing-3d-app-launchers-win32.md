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
# <a name="implement-3d-app-launchers-win32-apps"></a>Implementieren von 3D-App-launchern (Win32-Apps)

> [!NOTE]
> Diese Funktion ist nur für PCs verfügbar, auf denen die neuesten [Windows-Insider](https://insider.windows.com) -Flüge (RS5), Build 17704 und höher ausgeführt werden.

Der [Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) -Startpunkt ist der Ausgangspunkt, an dem Benutzer vor dem Starten von Anwendungen landen. Standardmäßig müssen immersive Win32 VR-apps und Spiele von außerhalb des Headsets gestartet werden und werden nicht in der Liste "alle apps" im Windows Mixed Reality-Startmenü angezeigt. Wenn Sie jedoch die Anweisungen in diesem Artikel befolgen, um ein 3D-App-Startfeld zu implementieren, können Sie die immersive Win32-VR-Umgebung im Windows Mixed Reality-Startmenü und in der Home-Umgebung starten.

Dies gilt nur für immersive Win32-VR-Erlebnisse, die außerhalb von Steam verteilt sind. Bei der durch die Verwendung von [Steam verteilten](updating-your-steamvr-application-for-windows-mixed-reality.md)VR-Oberfläche haben wir [die Windows Mixed Reality für steamvr Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) zusammen mit den neuesten Windows Insider RS5-Flügen aktualisiert, damit die steamvr-Titel im Windows Mixed Reality-Startmenü in der Liste "alle apps" angezeigt werden. Automatisches verwenden eines Standard Start Programms. Anders ausgedrückt: die in diesem Artikel beschriebene Methode ist für die steamvr-Titel unnötig und wird von der Windows Mixed Reality for steamvr Beta-Funktionalität überschrieben.

## <a name="3d-app-launcher-creation-process"></a>Erstellung eines 3D-App-Start Programms

Zum Erstellen eines 3D-App-Start Programms sind drei Schritte erforderlich:
1. [Entwurf und Konzept](3d-app-launcher-design-guidance.md)
2. [Modellieren und exportieren](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integration in Ihre Anwendung (dieser Artikel)

3D-Ressourcen, die als Launcher für Ihre Anwendung verwendet werden sollen, sollten mithilfe der [Windows Mixed Reality Authoring Guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) erstellt werden, um die Kompatibilität zu gewährleisten. Assets, die diese Erstellungs Spezifikation nicht erfüllen, werden nicht in der Windows Mixed Reality-Startseite gerendert.

## <a name="configuring-the-3d-launcher"></a>Konfigurieren des 3D-Start Programms

Win32-Anwendungen werden in der Liste "alle apps" im Windows Mixed Reality-Startmenü angezeigt, wenn Sie ein 3D-App-Startfeld für Sie erstellen. Erstellen Sie hierzu eine XML- [Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) -XML-Datei, die auf das 3D-App-Startfeld verweist, indem Sie die folgenden Schritte ausführen:

1. Erstellen einer Ressource für ein **3D-App-Start** Programm (siehe [modellieren und exportieren](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)).
2. Erstellen Sie ein **[visuelles Element Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx)** für Ihre Anwendung.
    1. Sie können mit dem [folgenden Beispiel](#sample-visual-elements-manifest)beginnen.  Weitere Informationen finden Sie in der Dokumentation zum vollständigen [visuellen Element Manifest](https://msdn.microsoft.com/library/windows/apps/dn393983.aspx) .
    2. Aktualisieren Sie **Square150x150Logo** und **Square70x70Logo** mit einem PNG/JPG/GIF für Ihre APP.
        * Diese werden für das 2D-Logo der app in der Windows Mixed Reality all apps-Liste und für das Startmenü auf dem Desktop verwendet.
        * Der Dateipfad ist relativ zum Ordner, der das visuelle Element Manifest enthält.
        * Sie müssen immer noch ein Desktop-Start Menü Symbol für Ihre APP über die Standardmechanismen bereitstellen. Dies kann entweder direkt in der ausführbaren Datei oder in der von Ihnen erstellten Verknüpfung erfolgen (z. b. über IShellLink:: "conticonlocation").
        * *Optional:* Sie können eine "Resources. pri"-Datei verwenden, wenn Sie möchten, dass für MRT mehrere assetgrößen für verschiedene Auflösungs Skalen und Designs mit hohem Kontrast bereitgestellt werden.
    3. Aktualisieren Sie den **Pfad von mixedrealitymodel** , sodass er auf den GLB für das 3D-App-Startfeld verweist.
    4. Speichern Sie die Datei mit dem gleichen Namen wie die ausführbare Datei mit der Erweiterung ". Visualelementsmanifest. xml ", und speichern Sie Sie im selben Verzeichnis. Beispielsweise wird für die ausführbare Datei "CSO. exe" die zugehörige XML-Datei mit dem Namen "Configuration. visualelementsmanifest. xml" benannt.
3. Fügen Sie dem Desktop Windows-Startmenü **eine Verknüpfung** zu Ihrer Anwendung hinzu. Im [folgenden](#sample-app-launcher-shortcut-creation) Beispiel finden Sie eine Beispiel C++ Implementierung. 
    * Erstellen Sie die Datei unter%ALLUSERSPROFILE%\Microsoft\Windows\Start menu\programme (Machine) oder%APPDATA%\Microsoft\Windows\Start menu\programme (User).
    * Wenn ein Update das Manifest der visuellen Elemente oder die darin referenzierten Ressourcen ändert, sollte der Updater oder Installer die Verknüpfung aktualisieren, sodass das Manifest neu analysiert und zwischengespeicherte Objekte aktualisiert werden.
4. *Optional:* Wenn die Desktop Verknüpfung nicht direkt auf die exe-Datei der Anwendung zeigt (z. b., wenn Sie einen benutzerdefinierten Protokollhandler wie "MyApp://" aufruft), findet das Startmenü nicht automatisch die Datei "visualelementsmanifest. xml" der app. Um dieses Problem zu beheben, sollte in der Verknüpfung der Dateipfad des visuellen Element Manifests mithilfe von System. appusermodel. visualelementsmanifesthintpath () angegeben werden. Dies kann in der Verknüpfung mit denselben Techniken wie System.AppUserModel.ID festgelegt werden. Sie müssen System.AppUserModel.ID nicht verwenden, aber Sie können dies tun, wenn die Verknüpfung mit der expliziten Anwendungs Benutzer Modell-ID der Anwendung abgeglichen werden soll, wenn eine solche verwendet wird.  Ein C++ Beispiel finden Sie im Abschnitt zur [Erstellung von Beispielen](#sample-app-launcher-shortcut-creation) für das App-Start Programm.

### <a name="sample-visual-elements-manifest"></a>Beispiel für visuelle Element Manifeste

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

### <a name="sample-app-launcher-shortcut-creation"></a>Beispiel Erstellung für App-Start Programm Verknüpfung

Der folgende Beispielcode zeigt, wie Sie eine Verknüpfung in C++erstellen können, einschließlich der Überschreibung der Pfad zur XML-Datei des visuellen Elements. Beachten Sie, dass die außer Kraft Setzung nur in Fällen erforderlich ist, in denen die Verknüpfung nicht direkt auf die dem Manifest zugeordnete exe verweist (z. b. die Verknüpfung verwendet einen benutzerdefinierten Protokollhandler wie "MyApp://").

#### <a name="sample-lnk-shortcut-creation-c"></a>Blutprobe. Lnk-VerknüpfungsC++Erstellung ()

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

#### <a name="sample-url-launcher-shortcut"></a>Blutprobe. URL-Start Programm Verknüpfung 

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

## <a name="see-also"></a>Weitere Informationen:

* [Gemischtes Reality-Modell Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) mit einem 3D-App-Start Programm.
* [Entwurfsanleitung für 3D-App-Startprogramm](3d-app-launcher-design-guidance.md)
* [Erstellen von 3D-Modellen für die Verwendung in der Windows Mixed Reality-Startseite](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementieren von 3D-App-launchern (UWP-Apps)](implementing-3d-app-launchers.md)
* [Navigieren auf der Startseite von Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
