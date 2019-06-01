---
title: Installieren der tools
description: Beginnen Sie hier zur Vorbereitung von mixed Reality-Entwicklung. In diesem Artikel sollten immer die aktuellsten Versionen von Unity, Visual Studio und andere Tools, die für die Entwicklung für HoloLens und Windows Mixed Reality immersive Kopfhörer empfohlen widerspiegeln.
author: yoyozilla
ms.author: yoyozilla
ms.date: 2/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: auf dem neuesten Stand, Tools, erste Schritte, Grundlagen, Unity, visual Studio, Toolkit
ms.openlocfilehash: 32dcda0eceb8d3717de7b2502d86f03cda975b8f
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66453729"
---
# <a name="install-the-tools"></a>Installieren der tools

Abrufen der Tools, die Sie zum Erstellen von apps für Microsoft HoloLens und beeindruckende Windows Mixed Reality (VR)-Headsets benötigen. Es gibt keine separate SDK für Windows Mixed Reality-Entwicklung. Sie verwenden Visual Studio mit dem Windows 10-SDK.

Sie haben ein mixed Reality-Gerät nicht? Installation kann die [Emulator für HoloLens](using-the-hololens-emulator.md) einige Funktionen von mixed Reality-apps, ohne eine HoloLens zu testen. Sie können auch die [Windows Mixed Reality-Simulator](using-the-windows-mixed-reality-simulator.md) Ihre mixed Reality-apps für immersive Headsets testen.

Wir empfehlen die Installation der Unity-spielen-Engine, die einfachste Möglichkeit zum Erstellen von Reality-apps im gemischten, aber Sie können auch erstellen mit DirectX, wenn Sie eine benutzerdefinierte-Engine verwenden möchten.

>[!TIP]
>Lesezeichen für diese Seite, und überprüfen sie regelmäßig, um auf die neueste Version der einzelnen Tools, die für die Entwicklung von mixed Reality empfohlen auf dem neuesten Stand zu halten.

<br>

>[!VIDEO https://www.youtube.com/embed/3l20TWhw4S8]

## <a name="installation-checklist"></a>Installations-Checkliste


| Tool | Beschreibung | Hinweise |
|---------|---------|---------|
| ![Windows-Logo](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10**<br>(Link zur manuellen Installation)</a> | Installieren Sie die neueste Version von Windows 10, damit der PC Betriebssystem der Plattform entspricht, für die Sie mixed Reality-apps erstellen. | **Installieren von Windows 10** <br> <ul><li>Sie können die neueste Version von Windows 10 über Windows Update installieren, in den Einstellungen oder durch das Erstellen von Installationsmedien (über den Link in der linken Spalte).<li>Finden Sie unter [aktuellen Anmerkungen zur Version](release-notes-october-2018.md) gemischten Sie Informationen zu den neuesten verfügbaren Wirklichkeit Features mit jeder Version von Windows 10.</ul> **Aktivieren der Entwicklermodus auf Ihrem PC** Einstellungen > Update und Sicherheit > für Entwickler. <br><br> **Hinweis für Unternehmen und Unternehmen verwalteten PCs:** Wenn von Ihrem PC verwaltet wird einem Ihrer Organisation IT-Abteilung, müssen Sie möglicherweise diesen Partner wenden, um zu aktualisieren. <br><br> **"N" Windows-Versionen:** Windows Mixed Reality immersive (VR) Headsets werden unter "n"-Versionen von Windows nicht unterstützt. |
| ![Logo für Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2017**<br>(Link zur Installation)</a> | Voll ausgestattete integrierte Entwicklungsumgebung (IDE) für Windows und vieles mehr. Sie verwenden Visual Studio zum Schreiben von Code, Debuggen, testen und bereitstellen. | **Die Workloads zu installieren:** <ul><li>Desktopentwicklung mit C++</li><li>Entwicklung für die universelle Windows-Plattform</li></ul>**Hinweis zu Unity:** Wenn Sie absichtlich eine neuere (nicht-LTS) Version von Unity für einen bestimmten Zweck installieren möchten, ist es empfehlenswert *nicht* Installieren der Unity-Workload im Rahmen der Installation von Visual Studio, und installieren stattdessen die 2018.4 LTS Der Datenstrom von Unity wie bereits erwähnt unten.<br> <br>**Hinweis**: Es gibt einige bekannte Probleme mit mixed Reality-Entwicklung in Visual Studio-2019 im Moment.  Im Moment empfehlen wir, dass Sie weiterhin mit Visual Studio 2017. |
| ![Windows-Logo](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK (10.0.18362.0)**<br>(Link zur manuellen Installation)</a> | Bietet die neuesten-Header, Bibliotheken, Metadaten und Tools zum Erstellen von Windows 10-apps für HoloLens 2 an. | Zum Erstellen von apps für HoloLens 2 müssen Sie das Windows SDK, Build 18362 oder höher installieren.<br> <br> Wenn Sie nur für desktop Windows Mixed Reality-Headsets oder HoloLens-apps entwickeln (der 1. Generation), können Sie das Windows-SDK von Visual Studio 2017 installiert. |
| ![Logo für Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2087187" target="_blank">**HoloLens 2 Emulator**<br>(Link zur Installation: 10.0.18362.1005)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens (1. Generation) Emulator**<br>(Link zur Installation: 10.0.17763.253)</a> | Der Emulator können Sie zum Ausführen von apps für HoloLens virtuelles Computerimage ohne ein physisches HoloLens.<br> <br> Dieses Paket enthält auch holographic DirectX-Projektvorlagen für Visual Studio. | Finden Sie unter [mit dem Emulator für HoloLens](using-the-hololens-emulator.md) für Weitere Informationen zu den ersten Schritten mit dem Emulator.<br> <br> **Die vom System muss die Hyper-V unterstützt** für die Emulator-Installation erfolgreich ausgeführt werden kann. Konsultieren Sie Systemanforderungen weiter unten im Abschnitt Details an. Falls gewünscht, können Sie auswählen, um nur die Vorlagen ohne den Emulator zu installieren.<br>|
| ![Unity-logo](images/unity_logo.png)<br><br><a href="https://unity3d.com/unity/qa/lts-releases?version=2018.4" target="_blank">**Unity 2018.4**<br>(Link zur Installation)</a> | Die Unity-Spiele-Engine ist die einfachste Möglichkeit zum Erstellen von mixed Reality-Umgebungen, mit integrierter Unterstützung für Windows Mixed Reality-Features. | Wir empfehlen in der Regel den Unity-LTS (Long Term Support)-Stream als die am besten geeignete Version mit dem neue Projekte gestartet Aktualisierung auf die aktuellste Version, um die neuesten stabilen Fehlerbehebungen zu übernehmen.<br> <br>Aktuelle Empfehlung ist die Verwendung **Unity 2018.4.x**, d.h. der LTS-Build für MRTK v2 unten erforderlich sind.<br> <br>Einige Entwickler sollten eine andere Version von Unity aus bestimmten Gründen verwenden. Für diese Fälle unterstützt Unity Seite-an-Seite-Installationen verschiedener Versionen. |
| ![MRTK-logo](images/MRTKIcon.jpg)<br><br><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/releases" target="_blank">**Mixed Reality-Toolkit (MRTK v2) für Unity**</a> | MRTK v2 für Unity ist ein open-Source-Cross-Platform Development-Kit für mixed Reality-Anwendungen.<br><br> Beschleunigen der Entwicklung von Anwendungen für Microsoft HoloLens, Faszinierende Windows Mixed Reality (VR)-Headsets und der Plattform OpenVR MRTK v2 soll. Das Projekt ist für professionale Vermindern der Barrieren, die einen Eintrag in mixed Reality-Anwendungen zu erstellen, und erweitern, der Community als wir alle beitragen. | Erfahren Sie mehr über MRTK v2 finden Sie auf des Projekts des <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki" target="_blank">GitHub-Wiki</a>. |


## <a name="mixed-reality-toolkit"></a>Mixed Reality-Toolkit

Das Mixed Reality-Toolkit stellt, Komponenten und Funktionen, die zum Beschleunigen der Entwicklung von Anwendungen für Microsoft HoloLens, Windows Mixed Reality-Headsets und OpenVR-Plattform vorgesehen sind. Das Projekt zielt auf die Reduzierung von Sperren auf einen Eintrag in mixed Reality-Anwendungen zu erstellen und an der Community beitragen, wenn wir alle wachsen.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">MixedRealityToolkit</a>
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">Unity-MixedRealityToolkit</a> : verwendet den Code aus dem Basis-Toolkit und erleichtert es, die in Unity nutzen.
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">MixedRealityCompanionKit</a> – code Bits und Komponenten, die nicht direkt auf HoloLens oder immersive Headsets von (VR) ausgeführt werden können, aber stattdessen-Paar mit ihnen, erstellen Sie Umgebungen als Ziel Windows Mixed Reality.

## <a name="setting-up-your-pc-for-mixed-reality-development"></a>Einrichten von Ihrem PC für die Entwicklung von mixed reality

Das Windows 10 SDK funktioniert am besten auf dem Windows 10-Betriebssystem. Dieses SDK wird auch auf Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2 unterstützt. Beachten Sie, dass nicht alle Tools, die unter älteren Betriebssystemen unterstützt werden. 

### <a name="for-hololens-development"></a>Für die Entwicklung für HoloLens

Beim Einrichten von Ihrem Entwicklungs-PC für die Entwicklung für HoloLens stellen Sie sicher, dass er erfüllt die Systemanforderungen für beide <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> und <a href="https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs" target="_blank">Visual Studio</a>. Wenn Sie planen, verwenden Sie die HoloLens (1. Generation)-Emulator, sollten Sie sicherstellen, dass Ihr PC erfüllt die [HoloLens-Emulator – Systemanforderungen](using-the-hololens-emulator.md#hololens-emulator-system-requirements) ebenfalls.

Um den ersten Schritten mit dem Emulator für HoloLens finden Sie unter [mit dem Emulator für HoloLens](using-the-hololens-emulator.md).

Wenn Sie für immersive sowohl HoloLens und Windows Mixed Reality (VR)-Headsets entwickeln möchten, verwenden Sie die systemempfehlungen und Anforderungen im Abschnitt unten.

### <a name="for-immersive-vr-headset-development"></a>Für die immersiven (VR) Kopfhörer-Entwicklung

>[!NOTE]
>Die folgenden Richtlinien sind die aktuellen Mindestanforderungen bzw. empfohlenen-Spezifikationen für Ihre immersive (VR) Kopfhörer *Entwicklungs-PC*, und regelmäßig aktualisiert werden kann.

>[!WARNING]
>Ist nicht zu verwechseln mit der [minimale PC-Hardware Compatibility Richtlinien](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), welche sind die *Consumer PC-Spezifikationen* , sollten Sie als Ihren immersive (VR) Kopfhörer App- oder Spiele Ziel.

Wenn es sich bei Ihrem immersive Kopfhörer Entwicklungs-PC nicht mit voller Größe HDMI und/oder USB 3.0-Ports verfügt, müssen Sie [Adapter](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) Ihre Kopfhörer Verbindung.

Es gibt derzeit [bekannte Probleme](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) , vor allem mit Notebooks, die Hybrid-Grafiken verfügen einige Hardwarekonfigurationen.

<table>
<tr>
<th></th><th> Minimum</th><th> Empfohlen</th>
</tr><tr>
<td> Prozessor</td><td> <b>Notebook:</b> Intel Mobile Core i5 7. Generation CPU, Dual-Core mit Hyperthreading <b>Desktop:</b> Intel Desktop i5 6. Generation CPU, Dual-Core mit Hyperthreading <b>oder</b> AMD FX4350 4.2 Ghz Quad-Core-äquivalent</td><td> <b>Desktop:</b> Desktop des Intel i7 6. Generation (6 Kerne) <b>oder</b> AMD Ryzen 5 1600 (6 Kerne, 12 Threads)</td>
</tr><tr>
<td> GPU</td><td> <b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) entspricht oder höher DX12 fähige GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) entspricht oder höher DX12 fähige GPU</td><td><b>Desktop:</b> 1060/NVIDIA GTX 980, AMD Radeon RX 480 (2GB) entspricht oder höher DX12 fähige GPU</td>
</tr><tr>
<td> GPU-Treiber WDDM-version</td><td colspan="2"> WDDM-2.2-Treibers</td>
</tr><tr>
<td> Temperaturüberwachung Design Power</td><td colspan="2"> 15 oder höher</td>
</tr><tr>
<td> Anzeigen von Grafiken ports</td><td colspan="2"> 1 x verfügbaren Grafiken anzeigen, Port für&#160;Kopfhörer (HDMI-1.4 oder DisplayPort 1.2 für 60Hz Headsets, HDMI-2.0 oder DisplayPort 1.2 für 90Hz Headsets)</td>
</tr><tr>
<td> Bildschirmauflösung</td><td colspan="2"> Lösung: SVGA (800 x 600) oder größer Bittiefe: 32 Bits pro pixel</td>
</tr><tr>
<td> Arbeitsspeicher</td><td> 8&#160;GB RAM oder höher</td><td> 16 GB RAM oder höher</td>
</tr><tr>
<td> Speicher</td><td colspan="2"> &gt;10 GB zusätzlicher freier Speicherplatz</td>
</tr><tr>
<td> USB-Anschlüsse</td><td colspan="2"> 1 x verfügbaren USB-port für Kopfhörer (USB-3.0 Type-A) <b>beachten: USB muss mindestens 900mA angeben.</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth-4.0 (für Zubehör Konnektivität)</td>
</tr>
</table>

## <a name="see-also"></a>Siehe auch

* [Übersicht über die Entwicklung](development-overview.md)
* [Verwendung des HoloLens Emulators](using-the-hololens-emulator.md)
* [Verwenden des Windows Mixed Reality-Simulators](using-the-windows-mixed-reality-simulator.md)
* [Unity-Entwicklung – Übersicht](unity-development-overview.md)
* [DirectX-Entwicklung – Übersicht](directx-development-overview.md)
* [Archiv für HoloLens-Emulator](hololens-emulator-archive.md)
