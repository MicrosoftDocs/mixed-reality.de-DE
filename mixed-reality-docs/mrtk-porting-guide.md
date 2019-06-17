---
title: Vorbereiten von Apps für HoloLens 2
description: Dieses Dokument richtet sich an Entwickler, die eine vorhandene App für HoloLens (1. Generation) und/oder einen älteren MRTK haben und diese für MRTK Version 2 und HoloLens 2 portieren möchten.
author: grbury
ms.author: grbury
ms.date: 04/12/19
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, Testen, MRTK, MRTK Version 2, HoloLens 2
ms.openlocfilehash: 02dabd21b7a6add2ce53fe291a447e49057184d0
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66270397"
---
# <a name="getting-your-existing-app-ready-for-hololens-2"></a>Vorbereiten einer vorhandenen App für HoloLens 2

Dieses Handbuch ist speziell auf Entwickler zugeschnitten, um diese bei der Portierung einer vorhandenen Unity-App für HoloLens (1. Generation) in eine Anwendung für die neuen HoloLens 2-Geräte zu unterstützen. Beim Portieren einer Unity-App für HoloLens (1. Generation) in eine App für HoloLens 2 gibt es vier wichtige Schritte. Die folgenden Abschnitte enthalten Detailinformationen zu den einzelnen Phasen. 

| Schritt 1 | Schritt 2 | Schritt 3 | Schritt 4 |
|----------|-------------------|-------------------|-------------------|
| ![Visual Studio-Logo](images/visualstudio_logo.png) | ![Unity-Logo](images/unity_logo.png)| ![Unity-Symbol](images/hololens2_icon.jpg) | ![MRTK-Logo](images/MRTKIcon.jpg) |
| Herunterladen der aktuellen Tools | Aktualisieren des Unity-Projekts | Kompilieren für ARM | Migrieren zu MRTK Version 2

Entwicklern wird vor dem Beginn des Portierungsvorgangs **dringend empfohlen**, mithilfe der Quellcodeverwaltung eine Momentaufnahme des ursprünglichen App-Status zu speichern. Während des Vorgangs ist es außerdem empfehlenswert, an verschiedenen Punkten einen Prüfpunktstatus zu *speichern*. Es kann auch sehr hilfreich sein, eine weitere Unity-Instanz der ursprünglichen App zu erstellen, um die beiden während des Portierungsvorgangs parallel vergleichen zu können. 

> [!NOTE]
> Stellen Sie vor dem Portieren sicher, dass die aktuellen Tools für die Windows Mixed Reality-Entwicklung installiert sind. Bei den meisten bestehenden HoloLens-Entwicklern bedeutet dies ein Update auf das aktuelle Visual Studio 2017 und die Installation des entsprechenden Windows-SDKs. Im weiteren Verlauf werden die verschiedenen Unity-Versionen und der Mixed Reality-Toolkit Version 2 näher erläutert.
>
> Weitere Informationen finden Sie unter [Installieren der Tools](install-the-tools.md).

## <a name="migrate-project-to-latest-version-of-unity"></a>Migrieren des Projekts zur aktuellen Unity-Version

Wenn Sie MRTK v2 verwenden, ist Unity 2018 LTS der am besten geeignete langfristige Support-Pfad ohne bedeutende Änderungen in Unity oder MRTK.  Der empfohlene Unity-Build, wie unter „Installieren der Tools“ (siehe oben) beschrieben, ist Unity 2018.3, die künftige LTS-Version für Unity 2018.  Darüber hinaus gewährleistet MRTK v2 stets Support für Unity 2018 LTS, jedoch nicht zwangsläufig für jede Iteration von Unity 2019.x. 

Um weitere Unterschiede zwischen Unity 2018.3.x und Unity 2019.1.x zu verdeutlichen, werden nachstehend die Vor-und Nachteile dieser beiden Versionen aufgezeigt, wobei der bedeutsamste Unterschied in der Möglichkeit liegt, in Unity 2019 für ARM64 zu kompilieren. 

Entwickler sollten alle derzeit im Projekt vorhandenen [Plug-In-Abhängigkeiten](https://docs.unity3d.com/Manual/Plugins.html) analysieren und prüfen, ob diese DLLs für ARM64 erstellt werden können. Wenn ein Plug-In mit harter Abhängigkeit für ARM64 nicht erstellt werden kann, müssen Sie Unity 2018 LTS verwenden.


| Unity 2018.3.x | Unity 2019.1+ |
|----------|-------------------|
| ARM32-Buildunterstützung | ARM32- und ARM64-Buildunterstützung |
| Stabile LTS-Buildversion | Beta-Stabilität |
| [.NET-Skriptverarbeitungs-Back-End](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *veraltet* | [.NET-Skriptverarbeitungs-Back-End](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *entfernt* |
| UNET-Netzwerk *veraltet* | UNET-Netzwerk *entfernt* |

## <a name="update-sceneproject-settings-in-unity"></a>Aktualisieren von Szenen-/Projekteinstellungen in Unity

Nach dem Update auf Unity 2018.3.x oder Unity 2019+ ist es für optimale Ergebnisse ratsam, auf dem Gerät bestimmte Einstellungen in Unity zu aktualisieren. Diese Einstellungen werden ausführlich unter **[Empfohlene Einstellungen für Unity](Recommended-settings-for-Unity.md)** beschrieben.

Noch einmal: Das [.NET-Skriptverarbeitungs-Back-End](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) wird in Unity 2018 als veraltet markiert und in Unity 2019 *entfernt*. Daher sollten Entwickler unbedingt eine Umstellung Ihres Projekts auf [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html) in Betracht ziehen. 

> [!NOTE]
> Das IL2CPP-Skriptverarbeitungs-Back-End kann von Unity bis zu Visual Studio längere Buildzeiten verursachen. Daher sollten Entwickler ihren Entwicklungscomputer für eine [Optimierung der IL2CPP-Buildzeiten](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) einrichten.
> Darüber hinaus es kann vorteilhaft sein, besonders für Unity-Projekte mit sehr vielen Ressourcen (mit Ausnahme von Skriptdateien) oder ständig wechselnden Szenen/Ressourcen, einen [Cacheserver](https://docs.unity3d.com/Manual/CacheServer.html) einzurichten. Beim Öffnen eines Projekts speichert Unity die qualifizierenden Ressourcen in einem internen Cacheformat auf dem Entwicklercomputer. Bei Änderungen müssen die Elemente neu importiert und daher neu verarbeitet werden. Dieser Prozess kann einmal durchgeführt, in einem Cacheserver gespeichert und anschließend für andere Entwickler freigegeben werden, damit diese Zeit sparen und den erneuten Import der Änderungen nicht mehr einzeln und lokal verarbeiten müssen.

Wenn nach der Umstellung auf die aktualisierte Unity-Version alle wichtigen Änderungen behandelt wurden, sollten die Entwickler ihre aktuellen Apps auf HoloLens (1. Generation) erstellen und testen. Außerdem ist dies ein guter Zeitpunkt, ein Commit für die Quellcodeverwaltung zu erstellen und zu speichern. 

## <a name="compile-dependenciesplugins-for-arm-processor"></a>Kompilieren von Abhängigkeiten/Plug-Ins für ARM-Prozessor

HoloLens (1. Generation) hat Anwendungen auf einem x86-Prozessor ausgeführt, während für das neue HoloLens 2-Gerät ein ARM-Prozessor zum Einsatz kommt. Daher müssen vorhandene Anwendungen portiert werden, damit ARM unterstützt wird. Wie bereits erwähnt, unterstützt Unity 2018 die Kompilierung für ARM32-Apps, während Unity 2019+ die Kompilierung für ARM64-Apps unterstützt. Die Entwicklung für ARM64-Anwendungen wird allgemein bevorzugt, da es einen wesentlichen Unterschied in Bezug auf die Leistung gibt. Dies setzt jedoch voraus, dass auch alle [Plug-In-Abhängigkeiten](https://docs.unity3d.com/Manual/Plugins.html) für ARM64 erstellt werden müssen. 

Überprüfen Sie alle derzeit in Ihrer Anwendung vorhandenen DLL-Abhängigkeiten. Wenn eine Abhängigkeit nicht mehr benötigt wird, ist es ratsam, sie aus dem Projekt zu entfernen. Nehmen Sie für die verbleibenden Plug-Ins, die erforderlich sind, die entsprechenden ARM32- oder ARM64-Binärdateien in Ihr Unity-Projekt auf. 

Erstellen Sie nach der Aufnahme der relevanten DLLs aus Unity eine Visual Studio-Projektmappe, und kompilieren Sie dann in Visual Studio eine AppX für ARM, um zu testen, ob Ihre Anwendung für ARM-Prozessoren erstellt werden kann. Dies ist ein weiterer Punkt, an dem es sich empfiehlt, ein Commit in der Quellcodeverwaltungslösung zu speichern. 

## <a name="update-to-mrtk-version-2"></a>Update auf MRTK Version 2

MRTK Version 2 ist das neue Toolkit für Unity, das sowohl HoloLens (1. Generation) als auch HoloLens 2 unterstützt und alle neuen HoloLens 2-Funktionen (z.B. Handinteraktionen und Eye-Tracking) enthält.

### <a name="prepare-for-the-migration"></a>Vorbereitungen für die Migration

Vor der Übernahme der neuen [*.unitypackage-Dateien für MRTK v2](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) ist es empfehlenswert, ein Inventar von **(1) jeglichem benutzerdefinierten Code, der in MRTK v1 integriert ist** und **(2) jeglichem benutzerdefinierten Code für Eingabeinteraktionen oder Komponenten der Benutzerumgebung** zu erstellen. Ein häufiger und weit verbreiteter Konflikt, der bei der Aufnahme des neuen MRTK v2 auftritt, bezieht sich auf Eingabe und Interaktionen. Daher sollte ein Mixed Reality-Entwickler unbedingt das [MRTK v2-Eingabemodell](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) lesen und verstehen.

Schließlich wurde beim neuen MRTK v2 die Umstellung von einem Modell mit Skripts und Managerobjekten in den Szenen zu einer Architektur mit Konfiguration und Dienstanbietern vollzogen. Daraus ergibt sich ein übersichtlicheres Szenenhierarchie- und Architekturmodell, das jedoch einen gewissen Lernaufwand erfordert, um die neuen Konfigurationsprofile zu verstehen. Lesen Sie daher das [Konfigurationshandbuch zum Mixed Reality-Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html), um sich mit den wichtigen Einstellungen und Profilen zum Anpassen an die Anforderungen Ihrer Anwendung vertraut zu machen. 

### <a name="perform-the-migration"></a>Durchführen der Migration

Nach dem Import von MRTK v2 weist Ihr Unity-Projekt wahrscheinlich viele compilerbezogene Fehler auf. Diese sind aufgrund der neuen Namespacestruktur und der neuen Komponentennamen sehr häufig anzutreffen. Beheben Sie diese Fehler, indem Sie Ihre Skripts ändern und an die neuen Namespaces und Komponenten anpassen. 

Weitere Informationen zu speziellen API-Unterschieden zwischen HTK/MRTK und MRTK Version 2, finden Sie im Portierungshandbuch im [MRTK v2-Wiki](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html).

### <a name="best-practices"></a>Empfohlene Methoden

- Bevorzugen Sie die Verwendung des standardmäßigen MRTK-Shaders
- Arbeiten Sie nur jeweils an einem wichtigen Änderungstyp (z.B. IFocusable to IMixedRealityFocusHandler)
- Führen Sie nach jeder Änderung einen Test aus, und nutzen Sie die Quellcodeverwaltung
- Verwenden Sie nach Möglichkeit die MRTK-Standardbenutzerumgebung (Schaltflächen, Slates usw.)
- Ändern Sie nach Möglichkeit MRTK Dateien nicht direkt, sondern erstellen Sie Wrapper um MRTK-Komponenten
    - Das bietet einen Schutz bei Aufnahmen und Updates von zukünftigen MRTKs
- Prüfen und untersuchen Sie die Beispielszenen, die im MRTK bereitgestellt werden (insbesondere *HandInteractionExamples.scene*)
- Erstellen Sie eine canvasbasierte Benutzeroberfläche neu mit Quads, Collidern und TextMeshPro-Text

### <a name="testing-your-application"></a>Testen Ihrer Anwendung

Da nun HoloLens 2-Komponenten und -Funktionen in MRTK Version 2 ab [RC1](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/tag/v2.0.0-RC1) verfügbar sind, können Sie die Handinteraktionen direkt in Unity simulieren und Entwicklungen für die neuen APIs für Handinteraktionen und Eye-Tracking vornehmen.  Für eine hochwertige Erfahrung ist das HoloLens 2-Gerät erforderlich, aber Sie können zumindest in den Tools und der Dokumentation schon mit dem Lernen beginnen. Außerdem unterstützt MRTK v2 die Entwicklung auf HoloLens (1. Generation). Daher können auch herkömmliche Eingabemodelle wie die Auswahl durch Tippen in die Luft noch auf HoloLens-Geräten der 1. Generation getestet werden. 

## <a name="updating-interaction-model-for-hololens-2"></a>Aktualisieren des Interaktionsmodells für HoloLens 2

Nachdem Sie Ihre App portiert und für HoloLens 2 vorbereitet haben, können Sie die Aktualisierung Ihres Interaktionsmodells und der Hologrammentwürfe/Hologrammplatzierung in Betracht ziehen.
Ihre Anwendung, die auf HoloLens (1. Generation) basiert, verfügt wahrscheinlich über das Interaktionsmodell „Anvisieren und Ausführen“, bei dem die Hologramme relativ weit entfernt sind, damit sie in das Sichtfeld passen.

Schritte zum Aktualisieren Ihres App-Entwurfs, die für HoloLens 2 am besten geeignet sind:
1.  MRTK-Komponenten: Wenn Sie MRTK v2 hinzugefügt haben, gibt es aufgrund der Vorarbeit verschiedene Komponenten/Skripts, die für HoloLens 2 konzipiert und optimiert wurden, und die Sie nutzen können.

2.  Interaktionsmodell: Ziehen Sie die Aktualisierung Ihres Interaktionsmodells in Betracht.  In den meisten Fällen empfehlen wir, vom Anvisieren und Ausführen zur Handinteraktion zu wechseln.  Wenn Sie mit Ihren Hologrammen, die sich in der Regel außer Reichweite befinden, zur Handinteraktion wechseln, ergibt sich daraus eine ferne Interaktion mit zielendem Lichtstrahl und Greifgesten.
Hinweis: Es gibt Szenarien, in denen ein handfreies Interaktionsmodell erforderlich ist, z. B. als Task Worker, der Werkzeuge hält. Für diese Fälle gibt es bestimmte Entwurfsrichtlinien. 

3.  Hologrammplatzierung: Erwägen Sie nach dem Wechsel zum Handinteraktionsmodell, einige Hologramme in den Nahbereich zu verschieben, damit eine direkte Interaktion mit den Hologrammen mit den Händen über Greifgesten der nahen Interaktion möglich wird.  Zu den Hologrammtypen, die zum direkten Greifen oder für eine direkte Interaktion in den Nahbereich verschoben werden sollten, zählen kleine Zielmenüs, Steuerelemente, Schaltflächen und kleinere Hologramme, die beim Greifen und Untersuchen des Hologramms in das HoloLens 2-Sichtfeld passen.
<br>
Jede App und jedes Szenario ist anders, und wir werden auch in Zukunft anhand von Feedback oder durch fortgesetztes Lernen Entwurfsrichtlinien optimieren und veröffentlichen.


## <a name="additional-learnings-from-moving-apps-from-x86-to-arm"></a>Zusätzliche Erkenntnisse über das Verlagern von Apps von x86 zu ARM

- Reine Unity-Apps sind einfach, da Sie ein ARM-AppX-Paket direkt auf dem Gerät erstellen bzw. bereitstellen können, und die App läuft.
Die Schwierigkeiten beginnen mit der Unity-App, die native Plug-Ins verwendet.  Alle nativen Plug-Ins müssen auf Visual Studio 2017 aktualisiert und für ARM neu erstellt werden, und zwar mit Unity 2019 für ARM64.

- Eine App verwendete das AudioKinetic Wwise-Plug-In für Unity, und die verwendete Version hatte kein UWP-ARM-Plug-In. Es dauerte mehrere Tage, den Sound in der Anwendung neu zu erstellen, damit er auf ARM funktioniert.

- In anderen Fällen ist möglicherweise kein UWP/ARM-Plug-In für die Plug-Ins vorhanden, die für die Anwendung erforderlich sind, wodurch die Möglichkeit zum Portieren und Ausführen auf HoloLens 2 versperrt ist.  Möglicherweise müssen Sie mit dem Anbieter des Plug-Ins zusammenarbeiten, um die Sperre aufzuheben und ARM zu unterstützen.

- minfloat (und Varianten wie min16float, minint usw.) in Shaders verhalten sich auf HoloLens 2 möglicherweise anders als auf HoloLens (1. Generation). Diese sorgen insbesondere dafür, dass „mindestens die angegebene Bitanzahl verwendet wird“. Auf Intel/Nvidia-GPUs werden diese größtenteils nur als 32-Bit behandelt. Auf ARM wird tatsächlich die angegebene Bitanzahl berücksichtigt. Dies bedeutet in der Praxis, dass diese Zahlen auf HoloLens 2 möglicherweise eine geringere Genauigkeit/kleineren Bereich aufweisen, als dies auf HoloLens (1. Generation) der Fall war.

- Die _asm-Anweisungen funktionieren anscheinend auf ARM nicht, was bedeutet, dass jeder Code mit _asm-Anweisungen neu geschrieben werden muss.

- Das SIMD-Anweisungsset wird auf ARM nicht unterstützt. Dies bedeutet, dass verschiedene Header wie „xmmintrin.h“, „emmintrin.h“," tmmintrin.h“ und „immintrin.h“ auf ARM nicht verfügbar sind.

- Der Shader-Compiler auf ARM wird beim ersten Draw-Aufruf nach dem Laden des Shaders oder nach der Änderung einer Komponente, auf die sich der Shader stützt, ausgeführt, und nicht zur Ladezeit des Shaders. Die Auswirkungen auf die Bildfrequenz können erheblich sein, je nachdem, wie viele Shader kompiliert werden müssen. Das hat verschiedene Auswirkungen auf das unterschiedliche Verarbeiten/Packen/Aktualisieren von Shadern auf HoloLens 2 (gegenüber HoloLens der 1. Generation).

## <a name="see-also"></a>Weitere Informationen
* [Erste Schritte mit MRTK Version 2](mrtk-getting-started.md)
* [Gewusst wie: MRTK Version 2](https://microsoft.github.io/MixedRealityToolkit-Unity/External/HowTo/README.html)
* [Installieren der Tools](install-the-tools.md)
* [Empfohlene Einstellungen für Unity](recommended-settings-for-unity.md)
* [Grundlegendes zur Leistung für Mixed Reality](understanding-performance-for-mixed-reality.md)

