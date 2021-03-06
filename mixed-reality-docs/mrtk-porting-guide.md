---
title: Vorbereiten einer vorhandenen App für HoloLens 2
description: Dieses Dokument richtet sich an Entwickler, die eine vorhandene App für HoloLens (1. Generation) und/oder ein älteres MRTK haben und diese nach MRTK Version 2 und HoloLens 2 portieren möchten.
author: grbury
ms.author: grbury
ms.date: 07/29/2020
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, Testen, MRTK, MRTK Version 2, HoloLens 2
ms.openlocfilehash: a6d6c4ad2b9ec0de2663536f2299f31f7d79571a
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476992"
---
# <a name="get-your-existing-app-ready-for-hololens-2"></a>Vorbereiten einer vorhandenen App für HoloLens 2

## <a name="overview"></a>Übersicht

Dieses Handbuch soll Entwickler bei der Portierung einer vorhandenen Unity-Anwendung für HoloLens (1. Generation) in eine Anwendung für HoloLens 2-Geräte zu unterstützen. Beim Portieren einer Unity-Anwendung für HoloLens (1. Generation) in eine Anwendung für HoloLens 2 gibt es vier wichtige Schritte. 

Die folgenden Abschnitte enthalten Detailinformationen zu den einzelnen Phasen:

| Schritt 1 | Schritt 2 | Schritt 3 | Schritt 4 |
|----------|-------------------|-------------------|-------------------|
| ![Visual Studio-Logo](images/visualstudio_logo.png) | ![Unity-Logo](images/final_unity_logo.png)| ![Unity-Symbol](images/hololens2_icon.jpg) | ![MRTK-Logo](images/final_mrtk-small_logo.png) |
| Herunterladen der aktuellen Tools | Aktualisieren des Unity-Projekts | Kompilieren für ARM | Migrieren zu MRTK Version 2

Voraussetzungen:

Es wird vor dem Beginn des Portierungsvorgangs **dringend empfohlen**, dass Sie mithilfe der Quellcodeverwaltung eine Momentaufnahme des ursprünglichen Zustands Ihrer Anwendungen speichern. Während des Vorgangs ist es außerdem empfehlenswert, zu verschiedenen Zeitpunkten einen Prüfpunktstatus zu *speichern*. Es kann auch hilfreich sein, eine weitere Unity-Instanz der ursprünglichen Anwendung zu erstellen, um die beiden während des Portierungsvorgangs parallel vergleichen zu können. 

> [!NOTE]
> Stellen Sie vor dem Portieren sicher, dass die aktuellen Tools für die Windows Mixed Reality-Entwicklung installiert sind. Bei den meisten bestehenden HoloLens-Entwicklern bedeutet dies ein Update auf die neueste Version von Visual Studio 2019 und die Installation des entsprechenden Windows-SDKs. Im weiteren Verlauf werden die verschiedenen Unity-Versionen und das Mixed Reality-Toolkit (MRTK) Version 2 näher erläutert.
>
> Weitere Informationen finden Sie unter [Installieren der Tools](install-the-tools.md).

## <a name="migrate-project-to-the-latest-version-of-unity"></a>Migrieren des Projekts zur aktuellen Unity-Version

Wenn Sie [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity) verwenden, ist [Unity 2019 LTS](https://unity3d.com/unity/qa/lts-releases) der am besten geeignete langfristige Supportpfad ohne bedeutende Änderungen in Unity oder MRTK. Sie sollten alle derzeit in Ihrem Projekt vorhandenen [Plug-In-Abhängigkeiten](https://docs.unity3d.com/Manual/Plugins.html) analysieren und ermitteln, ob diese DLLs für ARM64 erstellt werden können. Wenn kein hartes Abhängigkeits-Plug-In für ARM64 erstellt werden kann, müssen Sie Ihre Apps möglicherweise weiterhin für ARM erstellen.

<!-- MRTK v2 always guarantees support for Unity 2018 LTS, but does not necessarily guarantee support for every iteration of Unity 2019.x.

To help clarify additional differences between [Unity 2018 LTS](https://unity3d.com/unity/qa/lts-releases) and Unity 2019.x, the following table outlines the trade-offs between the two versions. The primary difference between the two is the ability to compile for ARM64 in Unity 2019.

| Unity 2018 LTS | Unity 2019.x |
|----------|-------------------|
| ARM32 build support | ARM32 and ARM64 build support |
| Stable LTS build release | Beta stability |
| [.NET Scripting back-end](https://docs.unity3d.com/2018.4/Documentation/Manual/windowsstore-dotnet.html) *deprecated* | [.NET Scripting back-end](https://docs.unity3d.com/2018.4/Documentation/Manual/windowsstore-dotnet.html) *removed* |
| UNET Networking *deprecated* | UNET Networking *deprecated* |

-->

## <a name="update-sceneproject-settings-in-unity"></a>Aktualisieren von Szenen-/Projekteinstellungen in Unity

Nach dem Update auf [Unity 2019 LTS](https://unity3d.com/unity/qa/lts-releases) ist es für optimale Ergebnisse empfehlenswert, auf dem Gerät bestimmte Einstellungen in Unity zu aktualisieren. Diese Einstellungen werden ausführlich unter [Empfohlene Einstellungen für Unity](Recommended-settings-for-Unity.md) beschrieben.

Bedenken Sie, dass das [.NET-Back-End für die Skripterstellung](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) seit Unity 2018 veraltet ist und in Unity 2019 *entfernt* wurde. Entwickler sollten Ihre Projekte auf [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html) umstellen.

> [!NOTE]
> Das IL2CPP-Skriptverarbeitungs-Back-End kann von Unity bis zu Visual Studio längere Buildzeiten verursachen. Entwickler sollten ihren Entwicklungscomputer für eine [Optimierung der IL2CPP-Buildzeiten](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) einrichten.
> Es kann außerdem vorteilhaft sein, besonders für Unity-Projekte mit sehr vielen Ressourcen (mit Ausnahme von Skriptdateien) oder ständig wechselnden Szenen und Ressourcen, einen [Cacheserver](https://docs.unity3d.com/Manual/CacheServer.html) einzurichten. Beim Öffnen eines Projekts speichert Unity die qualifizierenden Ressourcen in einem internen Cacheformat auf dem Entwicklercomputer. Bei Änderungen müssen Elemente neu importiert und neu verarbeitet werden. Dieser Prozess kann einmal durchgeführt, in einem Cacheserver gespeichert und anschließend für andere Entwickler freigegeben werden, damit diese Zeit sparen und den erneuten Import der Änderungen nicht mehr einzeln und lokal verarbeiten müssen.

Wenn nach der Umstellung auf die aktualisierte Unity-Version alle Breaking Changes behoben wurden, sollten Sie Ihre aktuellen Anwendungen auf HoloLens (1. Generation) erstellen und testen. Dies ist ein guter Zeitpunkt, ein Commit in die Quellcodeverwaltung zu erstellen und zu speichern.

## <a name="compile-dependenciesplugins-for-arm-processor"></a>Kompilieren von Abhängigkeiten/Plug-Ins für ARM-Prozessor

HoloLens (1. Generation) führt Anwendungen auf einem x86-Prozessor aus, während HoloLens 2 einen ARM-Prozessor verwendet. Daher müssen vorhandene HoloLens-Anwendungen portiert werden, damit ARM unterstützt wird. Wie bereits erwähnt, unterstützt Unity 2018 LTS die Kompilierung von ARM32-Apps, während Unity 2019.x die Kompilierung von ARM32- und ARM64-Apps unterstützt. Die Entwicklung für ARM64-Anwendungen wird bevorzugt, da es einen wesentlichen Unterschied in Bezug auf die Leistung gibt. Dies setzt jedoch voraus, dass auch alle [Plug-In-Abhängigkeiten](https://docs.unity3d.com/Manual/Plugins.html) für ARM64 erstellt werden müssen.

Überprüfen Sie alle in Ihrer Anwendung vorhandenen DLL-Abhängigkeiten. Es ist ratsam, alle Abhängigkeiten, die nicht mehr benötigt werden, aus Ihrem Projekt zu entfernen. Nehmen Sie für die verbleibenden Plug-Ins, die erforderlich sind, die entsprechenden ARM32- oder ARM64-Binärdateien in Ihr Unity-Projekt auf.

Erstellen Sie nach der Aufnahme der relevanten DLLs aus Unity eine Visual Studio-Projektmappe, und kompilieren Sie dann in Visual Studio eine AppX für ARM, um zu testen, ob Ihre Anwendung für ARM-Prozessoren erstellt werden kann. Es empfiehlt sich, die Anwendung als Commit in der Quellcodeverwaltungslösung zu speichern.

> [!IMPORTANT]
> Anwendungen, die MRTK v1 verwenden, können auf HoloLens 2 ausgeführt werden, nachdem das Buildziel in ARM geändert wurde, wobei vorausgesetzt wird, dass alle anderen Anforderungen erfüllt sind. Dies umfasst die Sicherstellung, dass Sie über ARM-Versionen aller Ihrer Plug-Ins verfügen. Ihre App erhält jedoch keinen Zugriff auf HoloLens 2-spezifische Funktionen wie artikuliertes Hand- und Eye-Tracking. MRTK v1 und MRTK v2 verfügen über unterschiedliche Namespaces, die ermöglichen, dass beide Versionen im selben Projekt vorkommen, was für den Übergang von einer Version zur anderen nützlich ist.

## <a name="update-to-mrtk-version-2"></a>Update auf MRTK Version 2

[MRTK Version 2](https://github.com/microsoft/MixedRealityToolkit-Unity) ist das neue Toolkit über Unity, das sowohl HoloLens (1. Generation) als auch HoloLens 2 unterstützt. Hier wurden auch alle neuen Funktionen der HoloLens 2 hinzugefügt, z. B. Handinteraktionen und Eyetracking.

Weitere Informationen zur Verwendung von MRTK Version 2 finden Sie in den folgenden Ressourcen:

- [MRTK-Angebotsseite (Landing Page)](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
- [Erste Schritte mit MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
- [MRTK-Hände](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/HandTracking.html)
- [ MRTK Eye-Tracking – Blickverfolgung](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)

### <a name="prepare-for-the-migration"></a>Vorbereitungen für die Migration

Vor der Übernahme der neuen [*.unitypackage-Dateien für MRTK v2](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) ist es empfehlenswert, ein Inventar von **(1) jeglichem benutzerdefinierten Code, der in MRTK v1 integriert ist** und **(2) jeglichem benutzerdefinierten Code für Eingabeinteraktionen oder Komponenten der Benutzerumgebung** zu erstellen. Ein häufiger und weit verbreiteter Konflikt, der bei der Aufnahme des MRTK v2 auftritt, bezieht sich auf Eingabe und Interaktionen. Ein Mixed Reality-Entwickler sollte unbedingt das [MRTK v2-Eingabemodell](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) lesen und verstehen.

Schließlich wurde beim neuen [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity) die Umstellung von einem Modell mit Skripts und Managerobjekten in den Szenen zu einer Architektur mit Konfiguration und Dienstanbietern vollzogen. Daraus ergibt sich ein übersichtlicheres Szenenhierarchie- und Architekturmodell, das jedoch einen gewissen Lernaufwand erfordert, um die neuen Konfigurationsprofile zu verstehen. Lesen Sie daher das [Konfigurationshandbuch zum Mixed Reality-Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html), um sich mit den wichtigen Einstellungen und Profilen zum Anpassen an die Anforderungen Ihrer Anwendung vertraut zu machen.

### <a name="perform-the-migration"></a>Durchführen der Migration

Nach dem Import von [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity) weist Ihr Unity-Projekt höchstwahrscheinlich viele compilerbezogene Fehler auf. Diese sind aufgrund der neuen Namespacestruktur und der neuen Komponentennamen häufig anzutreffen. Beheben Sie diese Fehler, indem Sie Ihre Skripts ändern und an die neuen Namespaces und Komponenten anpassen.

Informationen zu speziellen API-Unterschieden zwischen HTK/MRTK und MRTK v2, finden Sie im Portierungshandbuch im [MRTK Version 2-Wiki](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html).

### <a name="best-practices"></a>Empfohlene Methoden

- Bevorzugen Sie die Verwendung des [standardmäßigen MRTK-Shaders](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html).
- Arbeiten Sie nur jeweils an einem wichtigen Änderungstyp (z.B. IFocusable in [IMixedRealityFocusHandler](https://microsoft.github.io/MixedRealityToolkit-Unity/api/Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler.html)).
- Führen Sie nach jeder Änderung einen Test aus, und nutzen Sie die Quellcodeverwaltung.
- Verwenden Sie nach Möglichkeit die MRTK-Standardbenutzerumgebung (Schaltflächen, Tafeln usw.).
- Ändern Sie MRTK Dateien nicht direkt, sondern erstellen Sie Wrapper um MRTK-Komponenten.
    - Diese Aktion vereinfacht Aufnahmen und Updates von zukünftigen MRTKs.
- Prüfen und untersuchen Sie die Beispielszenen, die im MRTK bereitgestellt werden, insbesondere *HandInteractionExamples.scene*.
- Erstellen Sie eine canvasbasierte Benutzeroberfläche neu mit Quads, Collidern und TextMeshPro-Text.
- Aktivieren Sie [gemeinsame Nutzung des Tiefenpuffers](camera-in-unity.md#sharing-your-depth-buffers-with-windows) oder [Festlegen des Fokuspunkts](focus-point-in-unity.md). Verwenden Sie bevorzugt einen 16-Bit-Tiefenpuffer, um die Leistung zu verbessern. Stellen Sie sicher, dass Sie beim Rendern von Farbe auch Tiefe rendern. Unity schreibt im Allgemeinen keine Tiefe für transparente und Text-gameobjects. 
- Legen Sie den Single Pass-instanziierten Renderingpfad fest.
- Nutzen Sie das [HoloLens 2-Konfigurationsprofil für MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html#hololens-2-profile)

### <a name="testing-your-application"></a>Testen Ihrer Anwendung

In MRTK Version 2 können Sie Handinteraktionen direkt in Unity simulieren sowie Entwicklungen mit den neuen APIs für Handinteraktionen und Eyetracking vornehmen. Das HoloLens 2-Gerät ist erforderlich, um eine zufriedenstellende Benutzererfahrung zu erzeugen. Ihnen wird empfohlen, die Dokumentation und die Tools zu studieren, um Ihr Verständnis zu erhöhen. [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity) unterstützt die Entwicklung auf HoloLens (1. Generation), und es können herkömmliche Eingabemodelle wie die Auswahl durch Tippen in die Luft auf HoloLens (1. Generation) getestet werden. 

## <a name="updating-your-interaction-model-for-hololens-2"></a>Aktualisieren des Interaktionsmodells für HoloLens 2

Nachdem Sie Ihre Anwendung portiert und für HoloLens 2 vorbereitet haben, können Sie die Aktualisierung Ihres Interaktionsmodells und der Hologrammentwurfsplatzierungen in Betracht ziehen.
In HoloLens (1. Generation) verfügt Ihre Anwendung wahrscheinlich über das Interaktionsmodell „Anvisieren und Ausführen“, bei dem die Hologramme relativ weit entfernt sind, damit sie in das Sichtfeld passen.

Schritte zum Aktualisieren Ihres Anwendungsentwurfs, damit dieser für HoloLens 2 optimal geeignet ist:
1.  MRTK-Komponenten: Wenn Sie [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity) hinzugefügt haben, gibt es aufgrund der Vorarbeit verschiedene Komponenten/Skripts, die für HoloLens 2 konzipiert und optimiert wurden, und die Sie nutzen können.

2.  Interaktionsmodell: Ziehen Sie die Aktualisierung Ihres Interaktionsmodells in Betracht. In den meisten Fällen empfehlen wir, vom Anvisieren und Ausführen zur Handinteraktion zu wechseln. Wenn Sie mit Ihren Hologrammen, die sich in der Regel außer Reichweite befinden, zur Handinteraktion wechseln, ergibt sich daraus eine ferne Interaktion mit zielendem Lichtstrahl und Greifgesten.

3.  Hologrammplatzierung: Erwägen Sie nach dem Wechsel zum Handinteraktionsmodell, einige Hologramme in den Nahbereich zu verschieben, damit eine direkte Interaktion mit diesen mit den Händen über Greifgesten der nahen Interaktion möglich wird. Zu den Hologrammtypen, die zum direkten Greifen oder für eine direkte Interaktion in den Nahbereich verschoben werden sollten, zählen kleine Zielmenüs, Steuerelemente, Schaltflächen und kleinere Hologramme, die beim Greifen und Untersuchen des Hologramms in das HoloLens 2-Sichtfeld passen.
<br>
Jede Anwendung und jedes Szenario ist anders, und wir werden auch in Zukunft anhand von Feedback oder durch fortgesetztes Lernen Entwurfsrichtlinien optimieren und veröffentlichen.


## <a name="additional-caveats-and-learnings-about-moving-applications-from-x86-to-arm"></a>Zusätzliche Einschränkungen und Erkenntnisse beim Verschieben von Anwendungen von x86 zu ARM

- Reine Unity-Anwendungen sind einfach, da Sie ein ARM-Anwendungspaket direkt auf dem Gerät erstellen oder bereitstellen können, auf dem das Paket laufen soll. Einige native Unity-Plug-Ins können bestimmte Herausforderungen bezüglich der Entwicklung darstellen. Aus diesem Grund müssen Sie ein Upgrade aller nativen Unity-Plug-Ins auf Visual Studio 2019 vornehmen und dann für ARM neu erstellen.

- Eine Anwendung hat das Unity AudioKinetic Wwise-Plug-In verwendet, und diese Version von Unity enthielt kein UWP ARM-Plug-In, was einen beträchtlichen Aufwand verursacht hat, um Soundfunktionen in der fraglichen Anwendung so neu zu konstruieren, dass sie auf ARM liefen. Stellen Sie sicher, dass alle erforderlichen Plug-Ins für Ihre Entwicklungspläne in Unity installiert und verfügbar sind.

- In manchen Fällen ist ein UWP/ARM-Plug-In für die Plug-Ins vorhanden, die für die Anwendung erforderlich sind, wodurch die Möglichkeit zum Portieren und Ausführen der Anwendung auf HoloLens 2 versperrt ist. Wenden Sie sich an Ihren Plug-In-Anbieter, um das Problem zu beheben und Support für ARM zu erhalten.

- Variablen des Typs „minfloat“ (und Varianten wie „min16float“, „minint“ usw.) in Shadern verhalten sich auf HoloLens 2 möglicherweise anders als auf HoloLens (1. Generation). Diese sorgen insbesondere dafür, dass „mindestens die angegebene Bitanzahl verwendet wird“. Auf Intel/Nvidia-GPUs werden diese größtenteils als 32-Bit behandelt. Auf ARM wird tatsächlich die angegebene Bitanzahl eingehalten. Dies bedeutet in der Praxis, dass diese Zahlen auf HoloLens 2 möglicherweise eine geringere Genauigkeit oder einen kleineren Bereich als auf HoloLens (1. Generation) aufweisen.

- Die „_asm“-Anweisungen funktionieren anscheinend auf ARM nicht, was bedeutet, dass jeder Code mit „_asm“-Anweisungen neu geschrieben werden muss.

- Die festgelegte SIMD-Anweisung wird auf ARM nicht unterstützt, weil verschiedene Header wie „xmmintrin.h“, „emmintrin.h“," tmmintrin.h“ und „immintrin.h“ auf ARM nicht verfügbar sind.

- Der Shader-Compiler auf ARM wird beim ersten Draw-Aufruf nach dem Laden des Shaders oder nach der Änderung einer Komponente, auf die sich der Shader stützt, ausgeführt, und nicht zur Ladezeit des Shaders. Die Auswirkungen auf die Bildfrequenz können merklich sein, je nachdem, wie viele Shader kompiliert werden müssen. Das hat verschiedene Auswirkungen auf das unterschiedliche Verarbeiten, Packen und Aktualisieren von Shadern auf HoloLens 2 gegenüber HoloLens (1. Generation).

## <a name="see-also"></a>Siehe auch
* [Installieren der Tools](install-the-tools.md)
* [Erste Schritte mit MRTK Version 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [HTK-APIs zu MRTK-APIs](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
* [Empfohlene Einstellungen für Unity](recommended-settings-for-unity.md)
* [Grundlegendes zur Leistung für Mixed Reality](understanding-performance-for-mixed-reality.md)

