---
title: Openxr
description: Erstellen Sie eine Engine mithilfe des portablen openxr-API-Standards, und stellen Sie Sie für Windows Mixed Reality-und hololens 2-Headsets bereit.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: Openxr, Khronos, basicxrapp, gemischte Realität openxr-Entwickler Portal, DirectX, Native, Native App Custom-Engine, Middleware
ms.openlocfilehash: 057d01527163f2ffcfe10d2e105592f07ff9e9e2
ms.sourcegitcommit: 23e172664c2ee1220fe3b4468c104b37ef3ceda9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2019
ms.locfileid: "68601601"
---
# <a name="openxr"></a>Openxr

Openxr ist ein offener, kostenloser API-Standard von [Khronos](https://www.khronos.org/) , der Modulen systemeigenen Zugriff auf eine große Bandbreite von Geräten von vielen Anbietern ermöglicht, die sich über das [gemischte Reality-Spektrum](mixed-reality.md)erstrecken.

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

Weitere Informationen zur openxr-API finden Sie in der [openxr 1,0-Spezifikation](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html) und in der [openxr 1,0-API-Referenz](https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/).  Weitere Informationen finden Sie auf der [Seite zu Khronos openxr](https://www.khronos.org/openxr/).

Um den vollständigen Feature-Satz von hololens 2 als Ziel festzulegen, verwenden Sie auch herstellerübergreifende und herstellerspezifische openxr-Erweiterungen, die über openxr 1,0 Core hinausgehende Features ermöglichen, wie z. b. die Nachverfolgung von Hand, die Augen Verfolgung, die räumliche Zuordnung und räumliche Anker.  Weitere Informationen zu den weiter unten in diesem Jahr anstehenden Erweiterungen finden Sie im Abschnitt " [Roadmap](openxr.md#roadmap) " weiter unten.

Beachten Sie, dass openxr nicht selbst ein gemischtes Reality-Engine ist.  Stattdessen ermöglicht openxr Modulen wie Unity und Unreal das einmalige Schreiben von portablen Code, der dann auf die nativen Plattformfunktionen des Holographic-oder immersiven Geräts des Benutzers zugreifen kann, unabhängig davon, welcher Anbieter diese Plattform erstellt hat.

## <a name="getting-started-with-openxr-for-hololens-2"></a>Getting Started with openxr for hololens 2

So beginnen Sie mit der Entwicklung von openxr-Anwendungen für hololens 2:

1. Richten Sie einen hololens 2 ein, oder befolgen Sie die Anweisungen zum [Installieren des hololens 2-Emulators](using-the-hololens-emulator.md).
1. Starten Sie die Store-App innerhalb des Geräts oder Emulators, und stellen Sie sicher, dass alle apps aktualisiert werden.  Dadurch wird sichergestellt, dass die openxr-Laufzeit auf Ihren hololens auf openxr 1,0 aktualisiert wird.  Wenn Sie den Emulator verwenden, sollten Sie sich die [Emulator-Eingabe Anweisungen](using-the-hololens-emulator.md#basic-emulator-input) ansehen, damit Sie die Store-App im Emulator verwenden können.

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Einstieg in openxr für Windows Mixed Reality-Headsets

So beginnen Sie mit der Entwicklung von openxr-Anwendungen für immersive Windows Mixed Reality-Headsets:

1. Stellen Sie sicher, dass Sie das Windows 10-Update "Mai 2019" (1903) ausführen. Dies ist die Mindestanforderung für Endbenutzer von Windows Mixed Reality, openxr-Anwendungen auszuführen.  Wenn Sie eine frühere Version von Windows 10 verwenden, können Sie mit dem [Windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10)ein Upgrade auf das Update von Mai 2019 durchführen.  Wenn Sie Ihren PC nicht aktualisieren können, ist es auch möglich, [die openxr-App mit dem Windows 10-Update vom Oktober 2018 (1809) zu entwickeln](openxr.md#developing-on-windows-10-october-2018-update), obwohl möglicherweise niedrigere Leistungs-oder andere Probleme auftreten.
1. Richten Sie ein Windows Mixed Reality-Headset ein, oder befolgen Sie die Anweisungen zum [Aktivieren des Windows Mixed Reality-Simulators](using-the-windows-mixed-reality-simulator.md).
1. Installieren Sie die [app "openxr Developer Portal" in Mixed Reality](https://www.microsoft.com/store/productId/9n5cvvl23qbt).  Wenn Sie diese APP installieren, wird die gemischte Realität openxr Runtime automatisch installiert.  Nachdem die openxr-Laufzeit installiert wurde, wird die Laufzeit vom Microsoft Store auf dem neuesten Stand gehalten.
1. Führen Sie die Mixed Reality openxr Developer Portal-App über das Startmenü aus, und befolgen Sie die Anweisungen, um die Laufzeit zu aktivieren.

![Gemischte Realität openxr-Entwickler Portal-App](images/mixed-reality-openxr-developer-portal.png)

> [!NOTE]
> Die gemischte Realität openxr-Laufzeit wird in Kürze allen Windows Mixed Reality-Endbenutzern über die Mixed Reality-Portal-App zur Verfügung gestellt.

## <a name="building-a-sample-openxr-app"></a>Aufbauen einer openxr-Beispiel-App

Das [basicxrapp](https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp) -Projekt veranschaulicht ein einfaches openxr-Beispiel mit zwei Visual Studio-Projektdateien, eines für eine Win32-Desktop-App und eines für eine UWP hololens 2-App.  Da die Projekt Mappe ein hololens-UWP-Projekt enthält, benötigen Sie die [Arbeitsauslastung der universelle Windows-Plattform Entwicklung](install-the-tools.md#installation-checklist) , die in Visual Studio installiert ist, um Sie vollständig zu öffnen.

Beachten Sie Folgendes: während die Win32-und UWP-Projektdateien aufgrund von Unterschieden bei der Paket Erstellung und Bereitstellung getrennt sind, ist der app-Code in jedem Projekt 100% identisch.

## <a name="roadmap"></a>Roadmap

Die openxr-Spezifikation definiert einen Erweiterungsmechanismus, mit dem Lauf Zeit Implementierungen zusätzliche Funktionen über die in der Basisversion von [openxr 1,0](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html)definierten [Kernfunktionen](openxr.md#what-is-openxr) hinaus verfügbar machen können.

Es gibt drei Arten von openxr-Erweiterungen:
* **Lieferanten Erweiterungen (z. b. msft):** Ermöglicht die herstellerspezifische Innovation in Hardware-oder Software Features.  Alle Lauf Zeit Hersteller können jederzeit eine Anbieter Erweiterung einführen und versenden.
* **EXT-Erweiterungen:** Anbieter übergreifende Erweiterungen, die von mehreren Unternehmen definiert und implementiert werden.  Gruppen von Interessen Unternehmen können jederzeit ext-Erweiterungen einführen.
* **KHR-Erweiterungen:** Offizielle Khronos-Erweiterungen, die im Rahmen einer Core-Spezifikation-Version ratifiziert wurden.  KHR-Erweiterungen werden durch dieselbe Lizenz abgedeckt wie die Kern Spezifikation selbst.

Am Ende des Jahres unterstützt die openxr-Laufzeit von Mixed Reality eine Reihe von msft-und ext-Erweiterungen, die den vollständigen Satz von hololens 2-Funktionen zu openxr-Anwendungen bringen:
* [Ungebundener Referenzraum (weltweit skalierbar)](coordinate-systems.md#building-a-world-scale-experience)
* [Räumliche Anker und Speicher](spatial-anchors.md)
* [Handgelenke und Hand Mesh](hands-and-tools.md)
* [Anvisieren mit den Augen](eye-tracking.md)
* [Sekundäre Ansichts Konfigurationen (Mixed Reality Capture)](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)
* [Räumliche Abbildung](spatial-mapping.md)
* Interop mit Windows SDK-APIs

Während einige dieser Erweiterungen als anbieterspezifische MSFT-Erweiterungen gestartet werden können, arbeiten Microsoft und andere openxr-Lauf Zeit Anbieter zusammen, um Anbieter übergreifende ext-oder KHR-Erweiterungen für viele dieser Featurebereiche zu entwerfen.  Dadurch kann der Code, den Sie für diese Funktionen schreiben, über Lauf Zeit Anbieter hinweg portabel sein, ebenso wie bei der Kern Spezifikation.

## <a name="troubleshooting"></a>Problembehandlung

Hier finden Sie einige Tipps zur Problembehandlung für die gemischte Realität openxr Runtime.  Wenn Sie weitere Fragen zur [openxr 1,0-Spezifikation](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html)haben, besuchen Sie die [Khronos openxr-Foren](https://community.khronos.org/c/openxr) oder [Slack #openxr Channel](https://khr.io/slack).

### <a name="developing-on-windows-10-october-2018-update"></a>Entwickeln unter Windows 10 Oktober 2018-Update

Wenn Sie [ihren Entwicklungs-PC nicht auf das Update von Mai 2019 aktualisieren](https://www.microsoft.com/en-us/software-download/windows10)können, können Sie den Windows 10-Computer vom Oktober 2018 Update (1809) für die Entwicklung einrichten, indem Sie einen weiteren Schritt ausführen:

1. Führen Sie die obigen Schritte aus, um mit openxr auf Ihrem Desktop-PC zu beginnen.
1. Um die gemischte Realität openxr Runtime als aktive openxr-Laufzeit Ihres Systems festzulegen, installieren Sie das [Mixed Reality openxr Developer Compatibility Pack](https://aka.ms/openxr-compat).

> [!NOTE]
> Obwohl Windows 10 Oktober 2018 Update (1809) für die Entwicklung von openxr-Anwendungen verwendet werden kann, ist das Windows 10-Update von Mai 2019 (1903) die Mindestanforderung für Endbenutzer, openxr mit Windows Mixed Reality zu verwenden.  Beim Ausführen der openxr-App im Oktober 2018-Update treten möglicherweise niedrigere Leistungs-oder andere Probleme auf.  Es wird dringend empfohlen, dass Sie Ihr Entwicklungs-PC auf das Windows 10-Update vom Mai 2019 (1903) aktualisieren.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>Openxr-App startet nicht Windows Mixed Reality

Wenn Ihre openxr-APP nicht Windows Mixed Reality startet, wenn Sie Sie ausführen, kann die gemischte Realität openxr Runtime nicht als aktive Laufzeit festgelegt werden.  Stellen Sie sicher, dass Sie die Entwickler Portal-App mit gemischter Realität ausführen, und befolgen Sie die Anweisungen, um die Laufzeit zu aktivieren.

### <a name="mixed-reality-openxr-developer-portal-app-cannot-be-installed"></a>Die gemischte Realität openxr-Entwickler Portal-App kann nicht installiert werden. 

Stellen Sie sicher, dass mindestens das Windows 10-Update vom Oktober 2018 (1809) ausgeführt wird.  Wenn Sie eine frühere Version von Windows 10 verwenden, können Sie mit dem [Windows 10 Update Assistant](https://www.microsoft.com/en-us/software-download/windows10)auf das Update von Mai 2019 (1903) aktualisieren.

Wenn die Schaltfläche "installieren" in der Mixed Reality-app "openxr-Entwickler Portal" unter Windows 10-Update vom Oktober 2018 nichts bewirkt, hat das System möglicherweise veraltete Systemanforderungen für die APP zwischengespeichert.  Sie können den Befehl `wsreset.exe` über eine Eingabeaufforderung ausführen, um den Cache zu löschen.

## <a name="see-also"></a>Siehe auch

* [Weitere Informationen zu openxr](https://www.khronos.org/openxr/)
* [Openxr 1,0-Spezifikation](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html)
* [Openxr 1,0-API-Referenz](https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/)
* [Openxr 1,0 kurz Referenzhandbuch](https://www.khronos.org/registry/OpenXR/specs/1.0/refguide/OpenXR-1.0-web.pdf)
