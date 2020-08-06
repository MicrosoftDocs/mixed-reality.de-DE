# <a name="unity"></a>[Unity](#tab/unity)

![Unity](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a>1. Herunterladen der aktuellen Version

Wir empfehlen den [Unity LTS-Stream (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) als beste Version, um neue Projekte zu starten und auf die neueste Version zu aktualisieren, um die neuesten stabilen Korrekturen zu erhalten. 
* Die aktuelle Empfehlung ist die Verwendung von **Unity 2019**, wobei es sich um den LTS-Build handelt, der unten für MRTK v2 erforderlich ist.
* Wenn Sie aus bestimmten Gründen eine andere Version von Unity verwenden müssen, unterstützt Unity parallele Installationen unterschiedlicher Versionen.

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2. Importieren des Mixed Reality-Toolkits (MRTK)
![MRTK](../images/UX/MRTK_UX_Hero.png)

Das [Mixed Reality-Toolkit](../mrtk-getting-started.md) (MRTK) ist ein plattformübergreifendes Open-Source-Entwicklungskit für Mixed Reality-Anwendungen. MRTK bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen. Das Toolkit soll die Entwicklung von Anwendungen für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen.

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity](../images/MRTK-Unity-Banner.png)<br>**Mixed Reality-Toolkit – Unity (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Wenn Sie MRTK für Unity nicht verwenden möchten, müssen Sie für alle Interaktionen und Verhaltensweisen selber Skripts erstellen.

#### <a name="other-tools-optional"></a>Weitere Tools [optional]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a>: Codebits und Komponenten, die möglicherweise nicht direkt auf HoloLens- oder immersive Headsets (VR) ausgeführt, sondern stattdessen mit ihnen gekoppelt werden, um Erfahrungen mit Windows Mixed Reality zu sammeln.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit – Common (GitHub)</a>: eine Sammlung freigegebener Skripts und Komponenten.

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Einrichten Ihres PCs für die Mixed Reality-Entwicklung

Das Windows SDK funktioniert am besten unter dem Betriebssystem Windows 10. Das SDK wird auch unter folgenden Betriebssystemen unterstützt: Windows 8.1, Windows 8, Windows 7, Windows Server 2012 und Windows Server 2008 R2. Beachten Sie, dass nicht alle Tools unter älteren Betriebssystemen unterstützt werden. 

> [!NOTE]
> Sie können Ihre Apps für HoloLens, für immersive Headsets (VR) oder beides entwickeln und bereitstellen. Stellen Sie sicher, dass Sie die unten aufgeführten Anforderungen abhängig von Ihren Anforderungen erfüllen.

#### <a name="for-hololens-development"></a>HoloLens-Entwicklung

Wenn Sie Ihren Entwicklungs-PC für die HoloLens-Entwicklung einrichten, stellen Sie sicher, dass er die Systemanforderungen sowohl für <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> als auch für <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> erfüllt. Wenn Sie planen, den [HoloLens-Emulator](../using-the-hololens-emulator.md) zu verwenden, sollten Sie sicherstellen, dass Ihr PC auch die [Systemanforderungen des HoloLens-Emulators](../using-the-hololens-emulator.md#hololens-emulator-system-requirements) erfüllt.

Informationen zu den ersten Schritten mit dem HoloLens-Emulator finden Sie unter [Verwendung des HoloLens-Emulators](../using-the-hololens-emulator.md).

Wenn Sie planen, sowohl für HoloLens als auch für immersive Windows Mixed Reality-Headsets (VR) zu entwickeln, verwenden Sie die Systemempfehlungen und Anforderungen im folgenden Abschnitt.

#### <a name="immersive-vr-headset-requirements"></a>Anforderungen an immersive Headsets (VR)

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

### <a name="whats-next"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Antreten Ihrer Unity-Journey](../unity-development-overview.md)

# <a name="unreal"></a>[Unreal](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a>1. Herunterladen der aktuellen Version

Es wird empfohlen, die [Unreal-Engine, Version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) oder höher, zu installieren, um die integrierte Unterstützung von HoloLens in vollem Umfang nutzen zu können.

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2. Importieren des Mixed Reality-Toolkits (MRTK)
![MRTK](../images/UX/MRTK_UX_Hero.png)

Mixed Reality Toolkit (MRTK) ist ein plattformübergreifendes Open Source-Entwicklungskit für Mixed Reality-Anwendungen. MRTK bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen. Das Toolkit soll die Entwicklung von Anwendungen für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen.

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity](../images/MRTK-Unreal-Banner.png)<br>**Mixed Reality Toolkit-Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Wenn Sie MRTK für Unreal nicht verwenden möchten, müssen Sie für alle Interaktionen und Verhaltensweisen selber Skripts erstellen.

#### <a name="other-tools-optional"></a>Weitere Tools [optional]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a>: Codebits und Komponenten, die möglicherweise nicht direkt auf HoloLens- oder immersive Headsets (VR) ausgeführt, sondern stattdessen mit ihnen gekoppelt werden, um Erfahrungen mit Windows Mixed Reality zu sammeln.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality-Toolkit – Common (GitHub)</a>: eine Sammlung freigegebener Skripts und Komponenten.

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Einrichten Ihres PCs für die Mixed Reality-Entwicklung

Das Windows SDK funktioniert am besten unter dem Betriebssystem Windows 10. Das SDK wird auch unter folgenden Betriebssystemen unterstützt: Windows 8.1, Windows 8, Windows 7, Windows Server 2012 und Windows Server 2008 R2. Beachten Sie, dass nicht alle Tools unter älteren Betriebssystemen unterstützt werden. 

> [!NOTE]
> Sie können Ihre Apps für HoloLens, für immersive Headsets (VR) oder beides entwickeln und bereitstellen. Stellen Sie sicher, dass Sie die unten aufgeführten Anforderungen abhängig von Ihren Anforderungen erfüllen.

#### <a name="for-hololens-development"></a>HoloLens-Entwicklung

Wenn Sie Ihren Entwicklungs-PC für die HoloLens-Entwicklung einrichten, stellen Sie sicher, dass er die Systemanforderungen sowohl für [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) als auch für <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> erfüllt. Wenn Sie planen, den [HoloLens-Emulator](../using-the-hololens-emulator.md) zu verwenden, sollten Sie sicherstellen, dass Ihr PC auch die [Systemanforderungen des HoloLens-Emulators](../using-the-hololens-emulator.md#hololens-emulator-system-requirements) erfüllt.

Wenn Sie planen, sowohl für HoloLens als auch für immersive Windows Mixed Reality-Headsets (VR) zu entwickeln, verwenden Sie die Systemempfehlungen und Anforderungen im folgenden Abschnitt.

#### <a name="immersive-vr-headset-requirements"></a>Anforderungen an immersive Headsets (VR)

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

### <a name="whats-next"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Antreten Ihrer Unreal-Journey](../unreal-development-overview.md)

# <a name="native-openxr"></a>[Nativ (OpenXR)](#tab/native)

 ![Entwicklung nativer Apps](../images/native_logo_banner.png)

Die native OpenXR-Entwicklung verfügt über keine Engine, die Sie herunterladen können. Alles, was Sie benötigen, um mit der Entwicklung zu beginnen, finden Sie im Dokument [Erste Schritte mit OpenXR](../openxr-getting-started.md).

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a>1. Einrichten Ihres PCs für die Mixed Reality-Entwicklung

Das Windows SDK funktioniert am besten unter dem Betriebssystem Windows 10. Das SDK wird auch unter folgenden Betriebssystemen unterstützt: Windows 8.1, Windows 8, Windows 7, Windows Server 2012 und Windows Server 2008 R2. Beachten Sie, dass nicht alle Tools unter älteren Betriebssystemen unterstützt werden.

#### <a name="for-hololens-development"></a>HoloLens-Entwicklung

Wenn Sie Ihren Entwicklungs-PC für die HoloLens-Entwicklung einrichten, stellen Sie sicher, dass er die Systemanforderungen für <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> erfüllt. Wenn Sie planen, den [HoloLens-Emulator](../using-the-hololens-emulator.md) zu verwenden, sollten Sie sicherstellen, dass Ihr PC auch die [Systemanforderungen des HoloLens-Emulators](../using-the-hololens-emulator.md#hololens-emulator-system-requirements) erfüllt.

Wenn Sie planen, sowohl für HoloLens als auch für immersive Windows Mixed Reality-Headsets (VR) zu entwickeln, verwenden Sie die Systemempfehlungen und Anforderungen im folgenden Abschnitt.

> [!NOTE]
> Sie können Ihre Apps für HoloLens, für immersive Headsets (VR) oder beides entwickeln und bereitstellen. Stellen Sie sicher, dass Sie die unten aufgeführten Anforderungen abhängig von Ihren Anforderungen erfüllen.

#### <a name="immersive-vr-headset-requirements"></a>Anforderungen an immersive Headsets (VR)

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

### <a name="whats-next"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Antreten Ihrer nativen Journey](../directx-development-overview.md)


