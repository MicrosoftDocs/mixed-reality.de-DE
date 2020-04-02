---
title: Installieren der Tools
description: Beginnen Sie hier, um sich auf die Mixed Reality-Entwicklung vorzubereiten. Dieser Artikel sollte immer die aktuellsten Versionen von Unity, Visual Studio und anderen Tools berücksichtigen, die für die Entwicklung für HoloLens und immersiven Windows Mixed Reality-Headsets empfohlen werden.
author: thetuvix
ms.author: alexturn
ms.date: 3/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Aktuell, Tools, Erste Schritte, Grundlagen, Unity, Visual Studio, Toolkit
ms.openlocfilehash: a2f62ecad1d6f1bbe90b3684391e6a1825de9d00
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362050"
---
# <a name="install-the-tools"></a>Installieren der Tools

Holen Sie sich die Tools, die Sie benötigen, um Anwendungen für Microsoft HoloLens und immersive Windows Mixed Reality-Headsets (VR) zu entwickeln. Es gibt kein separates SDK für die Entwicklung für Windows Mixed Reality. Sie verwenden Visual Studio mit dem Windows 10 SDK.

Sie besitzen kein Mixed Reality-Gerät? Sie können den [HoloLens-Emulator](using-the-hololens-emulator.md) installieren, um einige Funktionen von Mixed Reality-Anwendungen ohne eine HoloLens zu testen. Sie können auch den [Windows Mixed Reality-Simulator](using-the-windows-mixed-reality-simulator.md) verwenden, um Ihre Mixed Reality-Anwendungen für immersive Headsets zu testen.

Wir empfehlen die Installation der Unity-Spielengine – dies ist die einfachste Möglichkeit, mit dem Erstellen von Mixed Reality-Apps zu beginnen. DirectX kann auch verwendet werden, wenn eine benutzerdefinierte Engine gewünscht ist.

>[!TIP]
>Fügen Sie diese Seite als Lesezeichen hinzu und überprüfen Sie sie regelmäßig, um über die neueste Version der einzelnen Tools auf dem Laufenden zu bleiben, die für die Mixed Reality-Entwicklung empfohlen werden.

<br>

>[!VIDEO https://www.youtube.com/embed/3l20TWhw4S8]

## <a name="installation-checklist"></a>Checkliste für die Installation


| Tool | Beschreibung | Hinweise |
|---------|---------|---------|
| ![Windows-Logo](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (Link zur manuellen Installation)</a> | Installieren Sie die neueste Version von Windows 10, damit das Betriebssystem Ihres PCs mit der Plattform übereinstimmt, für die Sie Mixed Reality-Anwendungen entwickeln. | **Installieren von Windows 10** <br> <ul><li>Sie können die neueste Version von Windows 10 über Windows Update in den Einstellungen oder durch Erstellen von Installationsmedien (über den Link in der linken Spalte) installieren.<li>Informationen zu den neuesten Mixed Reality-Features, die mit den jeweiligen Versionen von Windows 10 verfügbar sind, finden Sie unter [Aktuelle Versionshinweise](release-notes-october-2018.md).</ul> **Aktivieren Sie den Entwicklermodus auf Ihrem PC** unter „Einstellungen > Update und Sicherheit > Für Entwickler“. <br><br> **Hinweis für PCs in Unternehmen:** Wenn Ihr PC von der IT-Abteilung Ihres Unternehmens verwaltet wird, müssen Sie sich möglicherweise an diese wenden, um ein Update durchzuführen. <br><br> **„N“-Versionen von Windows:** Immersive Windows Mixed Reality-Headsets (VR) werden von „N“-Versionen von Windows nicht unterstützt. |
| ![Visual Studio-Logo](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.2 oder höher)** (Link zur Installation)</a> | Voll funktionsfähige integrierte Entwicklungsumgebung (IDE) für Windows und mehr. Sie verwenden Visual Studio, um Code zu schreiben, zu debuggen, zu testen und bereitzustellen. | Installieren Sie unbedingt die folgenden Workloads: <ul><li>**Desktopentwicklung mit C++**</li><li>**Entwicklung mit der Universellen Windows-Plattform (UWP)**</li></ul>Achten Sie innerhalb der UWP-Workload darauf, die folgende optionale Komponente zu aktivieren, wenn Sie für HoloLens entwickeln:<ul><li>**USB-Gerätekonnektivität**</li></ul>**Hinweis zu Unity:** Sofern Sie nicht bewusst versuchen, eine neuere (Nicht-LTS-) Version von Unity für einen bestimmten Zweck zu installieren, empfehlen wir, die Installation der Unity-Workload *nicht* im Rahmen der Visual Studio-Installation durchzuführen und stattdessen den **Unity 2018.4 LTS**-Stream zu installieren, wie unten beschrieben.<br> <br>**Hinweis:** Es gibt derzeit einige bekannte Probleme beim Debuggen von Mixed Reality-Anwendungen in Visual Studio 2019, Version 16.0.  Stellen Sie sicher, dass Sie auf **Visual Studio 2019, Version 16.2 oder höher,** aktualisieren. |
| ![Windows-Logo](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK (10.0.18362.0)** (Link zur manuellen Installation)</a> | Enthält die neuesten Header, Bibliotheken, Metadaten und Tools zum Erstellen von Apps für Windows 10 für HoloLens 2. | Sie müssen das Windows SDK, Build 18362 oder höher, installieren, um HoloLens 2-Apps zu entwickeln.<br> <br> Wenn Sie nur Anwendungen für Windows Mixed Reality-Desktopheadsets oder HoloLens (1. Generation) entwickeln, können Sie das von Visual Studio 2017 installierte Windows SDK verwenden. |
| ![Visual Studio-Logo](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2121323" target="_blank">**HoloLens 2-Emulator (Update von März 2020)** (Link zur Installation: 10.0.18362.1056)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens-Emulator (1. Generation)** (Link zur Installation: 10.0.17763.134)</a> | Mit dem Emulator können Sie Anwendungen auf dem HoloLens-Image eines virtuellen Computers ohne physische HoloLens ausführen.<br> <br> | Weitere Informationen zu den ersten Schritten mit dem Emulator finden Sie unter [Verwendung des HoloLens-Emulators](using-the-hololens-emulator.md).<br> <br> **Ihr System muss Hyper-V** unterstützen, damit die Installation des Emulators erfolgreich ist. Weitere Informationen finden Sie unten im Abschnitt zu den Systemanforderungen. <br>|

## <a name="choose-your-engine"></a>Auswählen Ihrer Engine

:::row:::
    :::column:::
        <a href="https://unity3d.com/unity/qa/lts-releases?version=2018.4" target="_blank">![Unity](images/unity_logo.png)<br>
        **Unity**</a><br>
        Wir empfehlen in der Regel den Unity LTS-Stream (Long Term Support) als beste Version, um neue Projekte zu starten und auf die neueste Version zu aktualisieren, um die neuesten stabilen Korrekturen zu erhalten.<br>
        <br>
        Die aktuelle Empfehlung ist die Verwendung von **Unity 2018.4.x**, wobei es sich um den LTS-Build handelt, der unten für MRTK v2 erforderlich ist.<br>
        <br>
        Einige Entwickler möchten möglicherweise aus bestimmten Gründen eine andere Version von Unity verwenden. In diesen Fällen unterstützt Unity die parallele Installation verschiedener Versionen.<br>
        <br>
        Lesen Sie die [Unity-Entwicklung – Übersicht](unity-development-overview.md), um in die Unity-Entwicklung für HoloLens 2 oder immersive Headsets für Windows Mixed Reality einzusteigen.<br>
        <br>
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/releases" target="_blank">![MRTK](images/final_mrtk-small_logo.png)<br>
        **Mixed Reality-Toolkit (MRTK)** </a><br>
        Mixed Reality Toolkit (MRTK) v2 für Unity ist ein plattformübergreifendes Open Source-Entwicklungskit für Mixed Reality-Anwendungen.<br>
        <br>
        MRTK v2 soll die Entwicklung von Anwendungen für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen. Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community zu leisten, während sich die Dinge entwickeln.
    :::column-end:::
    :::column:::
        <a href="https://docs.unrealengine.com//GettingStarted/Installation/index.html" target="_blank">![Unreal](images/Unreal_logo.png)<br>
        **Unreal**</a><br>
        Unreal Engine 4 ist eine leistungsstarke, Open Source-Erstellungsengine mit voller Unterstützung für Mixed Reality in C++ und Blueprints.<br>
        <br>
        Die HoloLens-Unterstützung für die Unreal Engine 4.24 befindet sich derzeit in der Betaversion.<br>
        <br>
        Informationen zum Einstieg in die Unreal-Entwicklung für HoloLens 2 finden Sie in der [Unreal-Entwicklung – Übersicht](unreal-development-overview.md).
    :::column-end:::
    :::column:::
        ![Entwicklung nativer Apps](images/visualstudio-small_logo.png)<br>
        [**Nativ (OpenXR)** ](openxr-getting-started.md)<br>
        OpenXR ist ein offener, lizenzgebührenfreier API-Standard von Khronos, mit dem Engines nativen Zugriff auf eine große Bandbreite von Geräten von vielen Herstellern aus dem gesamten Mixed Reality-Spektrum erhalten.  Das <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>-Projekt zeigt ein einfaches OpenXR-Beispiel mit zwei Visual Studio-Projektdateien, eine für eine Win32-Desktop-App und eine für eine UWP HoloLens 2-App.<br>
        <br>
        <a href="https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX" target="_blank">**Nativ (WinRT)** </a><br>
        Die <a href="https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX" target="_blank">Nativen Windows Mixed Reality-App-Vorlagen</a> bieten alle grundlegenden Bestandteile, die Sie benötigen, um mit dem Erstellen einer Mixed Reality-App anzufangen, die DirectX und native APIs verwendet. Enthält eine Renderschleife (oder „Spielschleife“), eine DeviceResources-Hilfsklasse zur Verwaltung des Direct3D-Geräts und des Kontexts sowie einen einfachen Hologramm-Beispielrenderer. Verfügbar für Direct3D 11 und Direct3D 12.<br>
        <br>
        Lesen Sie die [Native-Entwicklung – Übersicht](directx-development-overview.md), um in die Entwicklung einer nativen App für HoloLens 2 oder für immersive Headsets für Windows Mixed Reality mithilfe von WinRT oder OpenXR einzusteigen.
    :::column-end:::
:::row-end:::

<br>

## <a name="mixed-reality-toolkit-mrtk"></a>Mixed Reality-Toolkit (MRTK)

Das Mixed Reality Toolkit stellt Komponenten und Features bereit, die die Entwicklung von Anwendungen für Microsoft HoloLens, Windows Mixed Reality-Headsets und die OpenVR-Plattform beschleunigen sollen. Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community zu leisten, während sich die Dinge entwickeln.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality-Toolkit</a>: Eine Sammlung von Skripts und Komponenten, die die Entwicklung von Mixed Reality-Anwendungen beschleunigen sollen.
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality-Toolkit – Unity</a>: Verwendet den Code aus dem Basistoolkit, was die Verwendung von Unity erleichtert.
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit</a>: Codebits und Komponenten, die möglicherweise nicht direkt auf HoloLens- oder immersive Headsets (VR) ausgeführt, sondern stattdessen mit ihnen gekoppelt werden, um Erfahrungen mit Windows Mixed Reality zu sammeln.

## <a name="setting-up-your-pc-for-mixed-reality-development"></a>Einrichten Ihres PCs für die Mixed Reality-Entwicklung

Das Windows SDK funktioniert am besten unter dem Betriebssystem Windows 10. Das SDK wird auch unter folgenden Betriebssystemen unterstützt: Windows 8.1, Windows 8, Windows 7, Windows Server 2012 und Windows Server 2008 R2. Beachten Sie, dass nicht alle Tools unter älteren Betriebssystemen unterstützt werden. 

### <a name="for-hololens-development"></a>HoloLens-Entwicklung

Wenn Sie Ihren Entwicklungs-PC für die HoloLens-Entwicklung einrichten, stellen Sie sicher, dass er die Systemanforderungen sowohl für <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> als auch für <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> erfüllt. Wenn Sie planen, den HoloLens-Emulator zu verwenden, sollten Sie sicherstellen, dass Ihr PC auch die [Systemanforderungen des HoloLens-Emulators](using-the-hololens-emulator.md#hololens-emulator-system-requirements) erfüllt.

Informationen zu den ersten Schritten mit dem HoloLens-Emulator finden Sie unter [Verwendung des HoloLens-Emulators](using-the-hololens-emulator.md).

Wenn Sie planen, sowohl für HoloLens als auch für immersive Windows Mixed Reality-Headsets (VR) zu entwickeln, verwenden Sie die Systemempfehlungen und Anforderungen im folgenden Abschnitt.

### <a name="for-immersive-vr-headset-development"></a>Entwicklung für immersive Headsets (VR)

>[!NOTE]
>Die folgenden Richtlinien sind die derzeit empfohlenen Mindestanforderungen und Spezifikationen für Ihren *Entwicklungs-PC* für immersive Headsets (VR) und werden regelmäßig aktualisiert.

>[!WARNING]
>Verwechseln Sie dies nicht mit den [Richtlinien zur minimalen PC-Hardwarekompatibilität](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), die die *Spezifikationen von Consumer-PCs* umreißen, auf die Sie Ihre immersive Headset-App (VR) oder Ihr Spiel ausrichten sollten.

Wenn Ihr Entwicklungs-PC für immersive Headsets nicht über vollwertige HDMI- und/oder USB 3.0-Anschlüsse verfügt, benötigen Sie [Adapter](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs), um Ihr Headset anzuschließen.

Es gibt derzeit [bekannte Probleme](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) bei einigen Hardwarekonfigurationen, insbesondere bei Notebooks mit Hybridgrafik.

<table>
<tr>
<th></th><th> Minimum</th><th> Empfohlen</th>
</tr><tr>
<td> Prozessor</td><td> <b>Notebook:</b> Intel Mobile Core i5-CPU der 7. Generation, Dual-Core mit Hyperthreading <b>Desktop:</b> Intel Desktop i5-CPU der 6. Generation, Dual-Core mit Hyperthreading <b>ODER</b> AMD FX4350 mit 4,2 GHz und vier Kernen</td><td> <b>Desktop:</b> Intel Desktop i7 der 6. Generation (6 Kerne) <b>ODER</b> AMD Ryzen 5 1600 (6 Kerne, 12 Threads)</td>
</tr><tr>
<td> GPU</td><td> <b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2 GB) – gleichwertig oder höher, DX12-fähige GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2 GB) – gleichwertig oder höher, DX12-fähige GPU</td><td><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2 GB) – gleichwertig oder höher, DX12-fähige GPU</td>
</tr><tr>
<td> GPU-Treiber (WDDM-Version)</td><td colspan="2"> WDDM 2.2-Treiber</td>
</tr><tr>
<td> Wärmeleistung</td><td colspan="2"> 15 W oder höher</td>
</tr><tr>
<td> Anschlüsse der Grafikanzeige</td><td colspan="2"> Ein verfügbarer Grafikanzeigeanschluss für&#160;Headset (HDMI 1.4 oder DisplayPort 1.2 für Headsets mit 60 Hz, HDMI 2.0 oder DisplayPort 1.2 für Headsets mit 90 Hz)</td>
</tr><tr>
<td> Anzeigeauflösung</td><td colspan="2"> Auflösung: SVGA (800 x 600) oder höhere Bittiefe: Farbe: 32 Bit pro Pixel</td>
</tr><tr>
<td> Memory</td><td> 8&#160;GB RAM oder mehr</td><td> 16 GB RAM oder mehr</td>
</tr><tr>
<td> Speicher</td><td colspan="2"> &gt;10 GB zusätzlicher freier Speicherplatz</td>
</tr><tr>
<td> USB-Anschlüsse</td><td colspan="2"> Ein verfügbare USB-Anschluss für Headset (USB-3.0 Type-A) <b>Hinweis: USB muss mindestens 900 mA bereitstellen</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (für den Anschluss von Zubehör)</td>
</tr>
</table>

## <a name="see-also"></a>Siehe auch

* [Entwicklung – Übersicht](development.md)
* [Verwendung des HoloLens-Emulators](using-the-hololens-emulator.md)
* [Verwenden des Windows Mixed Reality-Simulators](using-the-windows-mixed-reality-simulator.md)
* [Unity-Entwicklung – Übersicht](unity-development-overview.md)
* [Ureal-Entwicklung – Übersicht](unreal-development-overview.md)
* [DirectX-Entwicklung – Übersicht](directx-development-overview.md)
* [Archiv für HoloLens-Emulator](hololens-emulator-archive.md)
