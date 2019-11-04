---
title: Openxr
description: Erstellen Sie eine Engine mithilfe des portablen openxr-API-Standards, und stellen Sie Sie für Windows Mixed Reality-und hololens 2-Headsets bereit.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: Openxr, Khronos, basicxrapp, gemischte Realität openxr-Entwickler Portal, DirectX, Native, Native App Custom-Engine, Middleware
ms.openlocfilehash: cf8795e6fed7db9fd0743d0902ce1585d56fa5e0
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438134"
---
# <a name="openxr"></a>Openxr

Openxr ist ein offener, kostenloser API-Standard von <a href="https://www.khronos.org/" target="_blank">Khronos</a> , der Modulen systemeigenen Zugriff auf eine große Bandbreite von Geräten von vielen Anbietern ermöglicht, die sich über das [gemischte Reality-Spektrum](mixed-reality.md)erstrecken.

Sie können auf dem Desktop mit openxr auf einem hololens 2-oder Windows Mixed Reality-immersiven Headset entwickeln.  Wenn Sie keinen Zugriff auf ein Headset haben, können Sie stattdessen den hololens 2-Emulator oder den Windows Mixed Reality-Simulator verwenden.

## <a name="why-openxr"></a>Gründe für openxr

Mit openxr können Sie Engines entwickeln, die sowohl auf Holographic-Geräte (wie hololens 2) abzielen, die digitale Inhalte in der realen Welt platzieren, als wären Sie tatsächlich vorhanden, als auch immersive Geräte (z. b. Windows Mixed Reality-Headsets für Desktop-PCs), die die physische und ersetzen Sie Sie durch eine digitale Umgebung.  Mit openxr können Sie Code einmal schreiben, der dann über eine große Bandbreite von Hardwareplattformen portabel ist.

Die openxr-API verwendet ein Lade Modul, das Ihre Anwendung direkt mit der nativen Platt Form Unterstützung Ihres Headsets verbindet.  Dies bietet Endbenutzern maximale Leistung und minimale Latenzzeit, unabhängig davon, ob Sie ein Windows Mixed Reality-Headset oder ein anderes Headset verwenden.

## <a name="what-is-openxr"></a>Was ist openxr?

Die zentrale openxr 1,0-API bietet die Basisfunktionalität, die Sie zum Erstellen eines Moduls benötigen, das sowohl auf Holographic-Geräte als auch auf hololens 2 und immersive Geräte wie Windows Mixed Reality-Headsets ausgerichtet ist:
* Systeme und Sitzungen
* Verweis Plätze (Ansicht, lokal, Phase)
* Konfigurationen anzeigen (Mono, Stereo)
* SwapChain + Frame zeitliche Steuerung
* Kompositions Ebenen
* Eingabe und Haptik
* Grafik-API + Platt Form Integration

Informationen zur openxr-API finden Sie in der openxr 1,0- <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Spezifikation</a>, der <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">API-Referenz</a> und der <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">kurz Referenzanleitung</a>.  Weitere Informationen finden Sie auf der <a href="https://www.khronos.org/openxr/" target="_blank">Seite zu Khronos openxr</a>.

Um den vollständigen Feature-Satz von hololens 2 als Ziel festzulegen, verwenden Sie auch herstellerübergreifende und herstellerspezifische openxr-Erweiterungen, die über openxr 1,0 Core hinausgehende Features ermöglichen, wie z. b. die Nachverfolgung von Hand, die Augen Verfolgung, die räumliche Zuordnung und räumliche Anker.  Weitere Informationen zu den weiter unten in diesem Jahr anstehenden Erweiterungen finden Sie im Abschnitt " [Roadmap](openxr.md#roadmap) " weiter unten.

Beachten Sie, dass openxr nicht selbst ein gemischtes Reality-Engine ist.  Stattdessen ermöglicht openxr Modulen wie Unity und Unreal das einmalige Schreiben von portablen Code, der dann auf die nativen Plattformfunktionen des Holographic-oder immersiven Geräts des Benutzers zugreifen kann, unabhängig davon, welcher Anbieter diese Plattform erstellt hat.

## <a name="getting-started-with-openxr-for-hololens-2"></a>Getting Started with openxr for hololens 2

So beginnen Sie mit der Entwicklung von openxr-Anwendungen für hololens 2:

1. Richten Sie einen hololens 2 ein, oder befolgen Sie die Anweisungen zum [Installieren des hololens 2-Emulators](using-the-hololens-emulator.md).
1. Starten Sie die Store-App innerhalb des Geräts oder Emulators, und stellen Sie sicher, dass alle apps aktualisiert werden.  Dadurch wird sichergestellt, dass die openxr-Laufzeit auf Ihren hololens auf openxr 1,0 aktualisiert wird.  Wenn Sie den Emulator verwenden, sollten Sie sich die [Emulator-Eingabe Anweisungen](using-the-hololens-emulator.md#basic-emulator-input) ansehen, damit Sie die Store-App im Emulator verwenden können.

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Einstieg in openxr für Windows Mixed Reality-Headsets

So beginnen Sie mit der Entwicklung von openxr-Anwendungen für immersive Windows Mixed Reality-Headsets:

1. Stellen Sie sicher, dass Sie das Windows 10-Update "Mai 2019" (1903) ausführen. Dies ist die Mindestanforderung für Endbenutzer von Windows Mixed Reality, openxr-Anwendungen auszuführen.  Wenn Sie eine frühere Version von Windows 10 verwenden, können Sie mit dem <a href="https://www.microsoft.com//software-download/windows10" target="_blank">Windows 10 Update Assistant</a>ein Upgrade auf das Update von Mai 2019 durchführen.  Wenn Sie Ihren PC nicht aktualisieren können, ist es auch möglich, [die openxr-App mit dem Windows 10-Update vom Oktober 2018 (1809) zu entwickeln](openxr.md#developing-on-windows-10-october-2018-update), obwohl möglicherweise niedrigere Leistungs-oder andere Probleme auftreten.
2. Richten Sie ein Windows Mixed Reality-Headset ein, oder befolgen Sie die Anweisungen zum [Aktivieren des Windows Mixed Reality-Simulators](using-the-windows-mixed-reality-simulator.md).  Nach dem Einrichten von Windows Mixed Reality wird die Windows Mixed Reality openxr-Laufzeit automatisch von Mixed Reality Portal installiert.  Der Microsoft Store behält die Laufzeit dann bei.
3. Aktivieren Sie die Windows Mixed Reality openxr-Laufzeit, indem Sie das gemischte Reality-Portal im Startmenü starten und dann auf die Schaltfläche... unten links, und wählen Sie "openxr einrichten".<br>
![Einrichten von openxr im Mixed Reality-Portal](images/mixed-reality-portal-set-up-openxr.png)

Wenn Sie die Windows Mixed Reality-openxr-Laufzeit erneut aktivieren müssen, wiederholen Sie Schritt 3.

> [!NOTE]
> Die Windows Mixed Reality openxr-Laufzeit wird in Kürze automatisch für alle Windows Mixed Reality-Endbenutzer eingerichtet.

## <a name="getting-the-mixed-reality-openxr-developer-portal"></a>Holen Sie sich das Entwickler Portal für gemischte Realität openxr

Um die Windows Mixed Reality openxr-Laufzeit auszuprobieren, können Sie die <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">[gemischte Realität openxr-Entwickler Portal-App</a>installieren.  Diese APP bietet eine Demo Szene, die verschiedene Features von openxr sowie eine Seite mit dem System Status ausführt, die wichtige Informationen zur aktiven Laufzeit und zum aktuellen Headset bereitstellt.

![Gemischte Realität openxr-Entwickler Portal-App](images/mixed-reality-openxr-developer-portal.png)

## <a name="building-a-sample-openxr-app"></a>Aufbauen einer openxr-Beispiel-App

Das <a href="https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp" target="_blank">basicxrapp</a> -Projekt veranschaulicht ein einfaches openxr-Beispiel mit zwei Visual Studio-Projektdateien, eines für eine Win32-Desktop-App und eines für eine UWP hololens 2-App.  Da die Projekt Mappe ein hololens-UWP-Projekt enthält, benötigen Sie die [Arbeitsauslastung der universelle Windows-Plattform Entwicklung](install-the-tools.md#installation-checklist) , die in Visual Studio installiert ist, um Sie vollständig zu öffnen.

Beachten Sie Folgendes: während die Win32-und UWP-Projektdateien aufgrund von Unterschieden bei der Paket Erstellung und Bereitstellung getrennt sind, ist der app-Code in jedem Projekt 100% identisch.

## <a name="roadmap"></a>Roadmap

Die openxr-Spezifikation definiert einen Erweiterungsmechanismus, mit dem Lauf Zeit Implementierungen zusätzliche Funktionen über die in der Basisversion von <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">openxr 1,0</a>definierten [Kernfunktionen](openxr.md#what-is-openxr) hinaus verfügbar machen können.

Es gibt drei Arten von openxr-Erweiterungen:
* **Lieferanten Erweiterungen (z. b. msft):** Ermöglicht die herstellerspezifische Innovation in Hardware-oder Software Features.  Alle Lauf Zeit Hersteller können jederzeit eine Anbieter Erweiterung einführen und versenden.
* **Ext-Erweiterungen:** Anbieter übergreifende Erweiterungen, die von mehreren Unternehmen definiert und implementiert werden.  Gruppen von Interessen Unternehmen können jederzeit ext-Erweiterungen einführen.
* **KHR-Erweiterungen:** Offizielle Khronos-Erweiterungen, die im Rahmen einer Core-Spezifikation-Version ratifiziert wurden.  KHR-Erweiterungen werden durch dieselbe Lizenz abgedeckt wie die Kern Spezifikation selbst.

Am Ende des Jahres unterstützt die openxr-Laufzeit von Windows Mixed Reality einen Satz von msft-und ext-Erweiterungen, die den vollständigen Satz von hololens 2-Funktionen zu openxr-Anwendungen bringen:
* [Ungebundener Referenzraum (weltweit skalierbar)](coordinate-systems.md#building-a-world-scale-experience)
* [Räumliche Anker und Speicher](spatial-anchors.md)
* [Handgelenke und Hand Mesh](hands-and-tools.md)
* [Anvisieren mit den Augen](eye-tracking.md)
* [Sekundäre Ansichts Konfigurationen (Mixed Reality Capture)](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)
* [Räumliche Abbildung](spatial-mapping.md)
* Interop mit Windows SDK-APIs

Während einige dieser Erweiterungen als anbieterspezifische MSFT-Erweiterungen gestartet werden können, arbeiten Microsoft und andere openxr-Lauf Zeit Anbieter zusammen, um Anbieter übergreifende ext-oder KHR-Erweiterungen für viele dieser Featurebereiche zu entwerfen.  Dadurch kann der Code, den Sie für diese Funktionen schreiben, über Lauf Zeit Anbieter hinweg portabel sein, ebenso wie bei der Kern Spezifikation.

## <a name="troubleshooting"></a>Fehlerbehebung

Im folgenden finden Sie einige Tipps zur Problembehandlung für die Windows Mixed Reality openxr-Laufzeit.  Wenn Sie weitere Fragen zur <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">openxr 1,0-Spezifikation</a>haben, besuchen Sie die <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos openxr-Foren</a> oder <a href="https://khr.io/slack" target="_blank">Slack #openxr Channel</a>.

### <a name="developing-on-windows-10-october-2018-update"></a>Entwickeln unter Windows 10 Oktober 2018-Update

Wenn Sie [ihren Entwicklungs-PC nicht auf das Update von Mai 2019 aktualisieren](https://www.microsoft.com//software-download/windows10)können, können Sie den Windows 10-Computer vom Oktober 2018 Update (1809) für die Entwicklung einrichten, indem Sie einen weiteren Schritt ausführen:

1. Führen Sie die obigen Schritte aus, um mit openxr auf Ihrem Desktop-PC zu beginnen.
1. Um die openxr-Laufzeit von Windows Mixed Reality als aktive openxr-Laufzeit Ihres Systems festzulegen, installieren Sie das [Windows Mixed Reality openxr Developer Compatibility Pack](https://aka.ms/openxr-compat).

> [!NOTE]
> Obwohl Windows 10 Oktober 2018 Update (1809) für die Entwicklung von openxr-Anwendungen verwendet werden kann, ist das Windows 10-Update von Mai 2019 (1903) die Mindestanforderung für Endbenutzer, openxr mit Windows Mixed Reality zu verwenden.  Beim Ausführen der openxr-App im Oktober 2018-Update treten möglicherweise niedrigere Leistungs-oder andere Probleme auf.  Es wird dringend empfohlen, dass Sie Ihr Entwicklungs-PC auf das Windows 10-Update vom Mai 2019 (1903) aktualisieren.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>Openxr-App startet nicht Windows Mixed Reality

Wenn Ihre openxr-APP nicht Windows Mixed Reality startet, wenn Sie Sie ausführen, kann die openxr-Laufzeit von Windows Mixed Reality nicht als aktive Laufzeit festgelegt werden.  Befolgen Sie die obigen Anweisungen für den [Einstieg in openxr für Windows Mixed Reality-Headsets](#getting-started-with-openxr-for-windows-mixed-reality-headsets) , um die Laufzeit zu aktivieren.

Sie können das [Entwickler Portal für gemischte Realität](#getting-the-mixed-reality-openxr-developer-portal) auch ausführen, um zusätzliche Hilfe zur Problembehandlung im Zusammenhang mit dem Status der Windows Mixed Reality openxr-Laufzeit auf Ihrem System zu erhalten.

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a>Das gemischte Reality-Portal zeigt das Menü Element "Set up openxr" nicht an.

Stellen Sie sicher, dass mindestens das Windows 10-Update vom Oktober 2018 (1809) ausgeführt wird.  Wenn Sie eine frühere Version von Windows 10 verwenden, können Sie mit dem [Windows 10 Update Assistant](https://www.microsoft.com//software-download/windows10)auf das Update von Mai 2019 (1903) aktualisieren.

Das Menü Element "Einrichten von openxr" ist möglicherweise nicht verfügbar, wenn Sie eine ältere Version der Mixed Reality-Portal-APP haben.  [Überprüfen Sie, ob](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m) Sie über die neueste Version verfügen.

Beachten Sie, dass das Menü Element "Set up openxr" nicht angezeigt wird, wenn die Windows Mixed Reality openxr-Laufzeit bereits installiert und aktiv ist.  Sie können das [gemischte openxr-Entwickler Portal](#getting-the-mixed-reality-openxr-developer-portal) installieren, um den aktuellen Status der openxr-Laufzeit auf Ihrem System zu ermitteln.

## <a name="see-also"></a>Weitere Informationen:

* <a href="https://www.khronos.org/openxr/" target="_blank">Weitere Informationen zu openxr</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Openxr 1,0-Spezifikation</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">Openxr 1,0-API-Referenz</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Openxr 1,0 kurz Referenzhandbuch</a>
