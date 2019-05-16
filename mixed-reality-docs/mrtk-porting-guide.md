---
title: Vorbereiten Ihrer app für HoloLens 2
description: Richtet sich an Entwickler, die eine vorhandene app für HoloLens haben (der 1. Generation) und/oder ältere MRTK wird, und an den Port MRTK Version 2 und HoloLens-2.
author: grbury
ms.author: grbury
ms.date: 04/12/19
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, zu testen, MRTK, MRTK Version 2, 2 für HoloLens
ms.openlocfilehash: 98fde1a597bcc20b14037176748258d35ef99ab9
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730868"
---
# <a name="getting-your-existing-app-ready-for-hololens-2"></a>Vorbereiten der Sie vorhandene Apps für HoloLens 2

Dieses Handbuch ist speziell angepasst, um Entwicklern dabei helfen, die über eine vorhandene Unity-app für HoloLens verfügen (1. Generation) so portieren Sie ihre Anwendung für das neue HoloLens-2-Gerät. Es gibt vier wichtigsten Schritte zum Portieren einer HoloLens (1. Generation) Unity-app mit HoloLens 2. In den folgenden Abschnitten werden die Informationen für die einzelnen Phasen ausführlich beschrieben. 

| Schritt 1 | Schritt 2 | Schritt 3 | Schritt 4 |
|----------|-------------------|-------------------|-------------------|
| ![Visual Studio-logo](images/visualstudio_logo.png) | ![Unity-logo](images/unity_logo.png)| ![Unity-Symbol](images/hololens2_icon.jpg) | ![MRTK-logo](images/MRTKIcon.jpg) |
| Herunterladen der neuesten tools | Aktualisieren des Unity-Projekt | Kompilieren für ARM | Migrieren zu MRTK v2

Es ist **dringend empfohlen,** , vor dem portieren, Entwickler Datenquellen-Steuerelement, um eine Momentaufnahme von den ursprünglichen Zustand der app speichern verwenden. Es wird außerdem empfohlen, *speichern* Prüfpunkt-Status zu verschiedenen Zeitpunkten während des Prozesses. Es kann auch sehr hilfreich, damit eine andere Instanz von Unity der ursprünglichen app können für den Vergleich von Seite-an-Seite bei der Port sein. 

> [!NOTE]
> Vor dem portieren, stellen Sie sicher, dass Sie die neuesten Tools, die für die Windows Mixed Reality-Entwicklung installiert haben. Für die meisten vorhandenen HoloLens-Entwickler wird dies in erster Linie auf das neueste Visual Studio 2017 aktualisieren, und installieren das entsprechende Windows SDK umfassen. Tauchen Sie der Inhalt weiter unten wird weiter in verschiedenen Versionen von Unity und den Mixed Reality-Toolkit, Version 2.
>
> Weitere Informationen finden Sie unter [Installieren der Tools](install-the-tools.md).

## <a name="migrate-project-to-latest-version-of-unity"></a>Migrieren Sie Projekt, auf die neueste Version von Unity

Wenn der MRTK v2 verwenden zu können, werden Unity 2018 LTS am besten geeignete langfristige unterstützungspfad ohne wichtige Änderungen in Unity oder MRTK.  Der empfohlene Unity-Build pro der oben genannten "Installieren der Tools" ist Unity 2018.3, die der LTS-Release für Unity 2018 werden soll.  Darüber hinaus der MRTK v2 Unterstützung für Unity 2018 LTS immer garantiert wird, aber nicht zwangsläufig Unterstützung für jede Iteration von Unity 2019.x. 

Um zu verdeutlichen, dass weiterer Unterschiede zwischen Unity 2018.3.x oder Unity 2019.1.x, unten zeigt die vor-und Nachteile zwischen diesen zwei Versionen, mit der wichtigste Unterschied von "significance" wird die Möglichkeit, für ARM64 in Unity 2019 kompilieren. 

Entwickler sollten abwägen, alle [-Plug-Ins Abhängigkeiten](https://docs.unity3d.com/Manual/Plugins.html) vorhanden, die derzeit in ihrem Projekt und davon, ob diese DLLs für ARM64 erstellt werden können. Wenn eine harte Abhängigkeit-Plug-In für ARM64 nicht erstellt werden kann, müssen eine Unity 2018 LTS nutzen.


| Unity 2018.3.x | Unity 2019.1+ |
|----------|-------------------|
| ARM32-Unterstützung | ARM32 und ARM64-Buildunterstützung |
| Stabile LTS Release, build | Beta-Stabilität |
| [Scripting .NET Back-End](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *als veraltet markiert* | [Scripting .NET Back-End](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *entfernt* |
| UNET Networking *als veraltet markiert* | UNET Networking *entfernt* |

## <a name="update-sceneproject-settings-in-unity"></a>Aktualisieren der Einstellungen der Szene oder eines Projekts in Unity

Nach dem Update auf Unity 2018.3.x oder Unity 2019 +, es wird empfohlen, bestimmte Einstellungen in Unity für optimale Ergebnisse auf Gerät aktualisieren. Diese Einstellungen werden ausführlich unter  **[empfohlene Einstellungen für Unity](Recommended-settings-for-Unity.md)**.

Erneut durchlaufenen wird, die die [Scripting .NET Back-End](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) wird in Unity 2018 eingestellt und *entfernt* in Unity 2019 und daher Entwickler sollten unbedingt wechselt zu ihresProjekts[ IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html). 

> [!NOTE]
> Skripterstellung IL2CPP-Back-End kann dazu führen, dass längere Buildzeiten von Unity in Visual Studio, und Entwickler sollte daher ihren Entwicklungscomputer für setup [Optimieren von Buildzeiten IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html).

Beheben Sie alle Änderungen nach dem Wechsel zu der aktualisierten Version von Unity, Entwickler erstellen und Testen Sie ihre aktuellen apps für HoloLens sollten (1. Generation). Darüber hinaus ist dies ein guter Zeitpunkt, um erstellen und speichern Sie einen Commit für die quellcodeverwaltung. 

## <a name="compile-dependenciesplugins-for-arm-processor"></a>Kompilieren Sie Abhängigkeiten/Plug-Ins für ARM-Prozessor

HoloLens (1. Generation) Ausführung von Anwendungen auf x X86 Prozessor, während das neue HoloLens-2-Gerät mit einen ARM-Prozessor verwendet. Daher müssen vorhandene Anwendungen zur Unterstützung von ARM über portiert werden. Wie bereits erwähnt, unterstützt Unity 2018 für ARM32 apps kompilieren, während Unity 2019 + Kompilieren für ARM64-apps unterstützt. Entwickeln für ARM64-Anwendungen wird allgemein bevorzugt, wie es einen grundlegenden Unterschied in Bezug auf Leistung gibt. Allerdings erfordert dies alle [-Plug-Ins Abhängigkeiten](https://docs.unity3d.com/Manual/Plugins.html) für ARM64 auch erstellt werden sollen. 

Überprüfen Sie alle DLL-Abhängigkeiten in Ihrer Anwendung derzeit ein. Wenn eine Abhängigkeit nicht mehr benötigt wird, ist es ratsam, die sie aus Ihrem Projekt entfernen. Erfassen Sie für die verbleibenden-Plug-Ins, die erforderlich sind die entsprechenden ARM32 oder ARM64-Binärdateien in Ihrem Unity-Projekt. 

Klicken Sie nach dem Erfassen der relevanten DLLs, erstellen Sie eine Visual Studio-Lösung von Unity, und kompilieren Sie dann eine AppX-Datei für ARM in Visual Studio zum Testen, ob Ihre Anwendung für die ARM-Prozessoren erstellt werden kann. Diese ein weiterer Punkt, in denen es sich empfiehlt, einen Commit in der Lösung für die quellcodeverwaltung zu speichern. 

## <a name="update-to-mrtk-version-2"></a>Aktualisieren Sie auf MRTK Version 2

MRTK Version 2 ist das neue Toolkit auf Unity unterstützen beide HoloLens (1. Generation) und 2 für HoloLens, und, in dem alle neuen Funktionen, HoloLens 2 hinzugefügt wurden, wie z. B. übergeben, Interaktionen und -Augen-nachverfolgung.

### <a name="prepare-for-the-migration"></a>Vorbereiten der migration

Vor der Erfassung von neuen [*.unitypackage-Dateien für MRTK v2](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases), es wird empfohlen, ein Inventar der auszuführende **(1) benutzerdefinierten Code, der integriert werden, MRTK v1** und **(2) keinen benutzerdefinierten Code für Interaktionen mit Eingabe- oder Komponenten von UX**. Die meisten allgemeinen und weit verbreitet Konflikt für ein Mixed Reality-Entwickler, die Erfassung von der neuen MRTK v2 wird ein- und Interaktionen umfassen. Es wird daher empfohlen, die gelesen werden soll und das Verständnis der [MRTK v2-Eingabemodell](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html).

Schließlich ist der neue MRTK v2 aus einem Modell von Skripts und in der Szene-Manager-Objekte in einer Konfiguration und die Anbieter-Dienstearchitektur gewechselt. Dies führt zu eine übersichtlichere Szene Hierarchie und die Architektur Modell jedoch erfordert Lernaufwand, um zu verstehen, die neue Konfigurationsprofile. Lesen Sie daher die [Mixed Reality-Toolkit-Konfigurationshandbuch](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) um vertraut machen mit wichtige Einstellungen und Profile Anpassung an die Anforderungen Ihrer Anwendung zu starten. 

### <a name="perform-the-migration"></a>Führen Sie die migration

Nach dem Importieren MRTK v2 Ihr Unity-Projekt müssen wahrscheinlich viele Compiler von Netzwerkfehlern. Dies sind am häufigsten aufgrund der neuen Namespacestruktur und den neuen Komponentennamen. Fahren Sie mit diese Fehler zu beheben, indem Sie Ihre Skripts auf den neuen Namespaces und Komponenten ändern. 

Weitere Informationen zu bestimmten API-Unterschiede zwischen HTK/MRTK und MRTK Version 2, finden Sie unter den Leitfaden zum Portieren auf die [MRTK Version 2-Wiki](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html).

### <a name="best-practices"></a>Empfohlene Methoden

- Bevorzugen der Verwendung des standardmäßigen MRTK shader
- Arbeit an einem aktuellen Typ zu einem Zeitpunkt ändern (z. B.: IFocusable zu IMixedRealityFocusHandler)
- Testen Sie nach jeder Änderung, und Nutzen von Datenquellen-Steuerelement
- Standard verwenden MRTK UX (Schaltflächen, Slate-PCs usw.) nach Möglichkeit
- Versuchen Sie, Sie davon absehen, MRTK Dateien direkt ändern, erstellen Sie stattdessen die Wrapper MRTK-Komponenten
    - Dies schützt vor zukünftigen MRTK Ingestions und updates
- Prüfen und untersuchen Sie die Beispiel-Szenen in MRTK bereitgestellt (insbesondere *HandInteractionExamples.scene*)
- Erstellen Sie stattdessen Canvas-basierte Benutzeroberfläche mit Quads "," collider "und" TextMeshPro Text neu

### <a name="testing-your-application"></a>Testen der Anwendung

Nun, HoloLens-2-Komponenten und Funktionen in MRTK, Version 2, verfügbar sind als der [RC1](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/tag/v2.0.0-RC1), können Sie simulieren die Interaktionen manuell direkt in Unity und für die neue APIs für Hand Interaktionen und Eye-tracking zu entwickeln.  Die HoloLens-2-Geräts ist erforderlich, um eine hervorragende Benutzeroberfläche erstellen, aber mindestens eine konnte Learning beginnen, in die Tools und Dokumentation. Darüber hinaus MRTK v2 unterstützt die Entwicklung für HoloLens (1. Generation) und daher herkömmliche Eingabe modelliert, z. B. Select über tippbewegung noch für HoloLens getestet werden kann (1. Generation) Geräte. 

## <a name="updating-interaction-model-for-hololens-2"></a>Aktualisieren die Interaktion für HoloLens 2

Nachdem Sie Ihre app portiert und Sie können für HoloLens 2 haben, können Sie erwägen, Ihre Interaktion Modell und – Hologramm Entwürfe und-Verteilung zu aktualisieren.
HoloLens stammen (der 1. Generation), Ihre Anwendung wahrscheinlich hat ein Interaktionsmodell Blicke und Commit mit Hologramme relativ weit entfernt in das Sichtfeld passt.

Schritte zum Aktualisieren des app-Entwurfs für HoloLens-2 am besten geeignet sein:
1.  MRTK-Komponenten: Pro Arbeit vor Wenn Sie MRTK v2 hinzugefügt sind verschiedene Komponenten/Skripts nutzen, die für HoloLens 2 optimiert und konzipiert wurden.

2.  Interaktionsmodell: Erwägen Sie das Interaktionsmodell zu aktualisieren.  In den meisten Fällen wird empfohlen, der Wechsel von Blicke und in die Hände zu übernehmen.  Mit Ihrem Hologramme in der Regel nicht genügend Gelenkarme zu erreichen, wechseln zur Hand weit Interaktion zeigen Strahlung gelöscht und Gesten abrufen.
Hinweis: Es gibt Szenarien, in denen eine automatische Interaktionsmodell ist erforderlich, z. B. einen taskworker, die mit Tools, und es gibt bestimmte Entwurfsrichtlinien für solche Fälle. 

3.  – Hologramm Platzierung: Erwägen Sie nach der Umstellung auf eine praktische Interaktionsmodell einige Hologramme näher direkte Interaktion mit der Hologramme mit der Hand, die in der Nähe von Interaktion Ziehpunkte Gesten verwenden.  Die Typen von Hologramme empfohlen, eine direkte Ziehen oder Interaktion näher sind kleine Ziel-Menüs, Steuerelemente, Schaltflächen und kleinere Hologramme, die in die HoloLens 2 Sichtfeld beim Abrufen und überprüfen die – Hologramm passen.
<br>
Jede app und das Szenario ist anders, und wir werden weiterhin zu optimieren, und Posten Entwurf Anleitungen basierend auf Feedback und Erkenntnisse fortgesetzt.


## <a name="additional-learnings-from-moving-apps-from-x86-to-arm"></a>Zusätzliche Erkenntnisse über das Verschieben von apps aus X86 in ARM

- Gerade Unity-apps sind einfach, wie Sie eine ARM-Appx-Paket erstellen oder direkt auf dem Gerät bereitstellen können, und er ausgeführt wird.
Die Herausforderung kommt, wenn es sich bei der Unity-app native-Plug-Ins verwendet.  Alle die native-Plug-Ins müssen ein Upgrade auf Visual Studio 2017 und neu erstellt, für ARM und mit Unity 2019 "," ARM64.

- Eine app, die AudioKinetic Wwise-Plug-In für Unity verwendet, und die verwendete Version hatte eine UWP-ARM-Plug-in keine. Es dauerte mehrere Tage den Sound erneut in die Anwendung funktioniert auf ARM zu arbeiten.

- In anderen Fällen kann eine UWP/ARM-Plug-in nicht für app-required-Plug-Ins, blockieren die Möglichkeit, port, und führen Sie auf HoloLens 2 vorhanden.  Engagement mit dem Anbieter-Plug-in kann erforderlich sein, zu entsperren und ARM unterstützt.

- Die Minfloat (und Varianten wie min16float Minint, usw.) im Shader verhält sich möglicherweise anders als bei HoloLen 2 als für HoloLens (1. Generation). Insbesondere diese garantieren, dass "mindestens die angegebene Anzahl von Bits verwendet werden". Auf Intel/Nvidia-GPUs werden diese größtenteils nur als 32-Bit behandelt. Auf ARM wird die angegebene Anzahl von Bits tatsächlich berücksichtigt. Dies bedeutet, dass in der Praxis ist diese Zahlen möglicherweise weniger Genauigkeit/Range für HoloLens 2 als für HoloLens wurden (der 1. Generation).

- Die _asm-Anweisungen nicht angezeigt, funktioniert auf ARM, was bedeutet, dass mithilfe der Anweisungen von _asm Code neu geschrieben werden muss.

- Die SIMD-Anweisungssatz wird auf ARM nicht unterstützt. Dies bedeutet verschiedene Header, z. B. xmmintrin.h "," emmintrin.h "," tmmintrin.h "und" immintrin.h nicht auf ARM verfügbar sind.

- Der Shader-Compiler auf ARM ausgeführt wird, während des ersten zeichnen, nachdem die Shader geladen wurde, oder etwas des Shaders verwendet wurde geändert, nicht zur Ladezeit des Shader. Die Auswirkungen auf die Framerate kann sein, je nachdem, wie viele Shader kompiliert werden müssen, äußerst bemerkenswerten. Dies hat verschiedene Auswirkungen auf die wie Shader verarbeitet/verpackt/aktualisiert anders in HoloLens 2 und HoloLens werden soll (der 1. Generation).

## <a name="see-also"></a>Siehe auch
* [Erste Schritte mit MRTK Version 2](mrtk-getting-started.md)
* [MRTK Version 2 des Clients](https://microsoft.github.io/MixedRealityToolkit-Unity/External/HowTo/README.html)
* [Installieren der Tools](install-the-tools.md)
* [Empfohlene Einstellungen für Unity](recommended-settings-for-unity.md)
* [Grundlegendes zur Leistung für Mixed Reality](understanding-performance-for-mixed-reality.md)

