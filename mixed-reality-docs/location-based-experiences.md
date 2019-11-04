---
title: Location based Entertainment mit Windows Mixed Reality
description: Erhalten Sie Zugriff auf die zugrunde liegenden Holographic Native-Objekte in Unity.
author: jessemcculloch
ms.author: ishitak
ms.date: 08/22/2019
ms.topic: article
keywords: Mixed Reality, VR, LBE, Location
ms.openlocfilehash: de9cfdaca77574bbbbec96c2e94fddeaa2712c33
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437941"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a>Location based Entertainment mit Windows Mixed Reality

In den letzten Jahren haben wir eine unglaubliche Menge an Wachstum und Innovation in der ortsbasierten Unterhaltungs Kategorie beobachtet. Herkömmliche Veranstaltungsorte wie Design Parks und Theater haben mit der Bereitstellung von immersiven multiplayererlebnissen für vorhandene Fahrten und Installationen begonnen. Neue Operatoren und Veranstaltungsorte bieten einzigartige Umgebungen mit mehreren sensorischen und mehr Spielern zu einem attraktiven Preis. Alle diese Möglichkeiten übertragen den Umschlag für das, was mit gemischter Realität möglich ist.

Dieses Dokument ist ein Leitfaden für die ersten Schritte mit Windows Mixed Reality in der Kategorie Location based Entertainment. Die nachfolgenden Anleitungen können zusätzlich auf standortbasierte Erfahrungen über Unterhaltung, wie z. b. Schulungen, Produktentwürfe oder andere Anwendungsfälle, angewendet werden.

## <a name="engineering-faq"></a>Technische FAQ

### <a name="hardware"></a>Hardware

**F: welche Hardware ist von Microsoft und seinen Partnern verfügbar, die ich in meinem Setup verwenden kann?**

A: Microsoft und seine OEM-Partner bieten ein überzeugendes Portfolio von Geräten, aus denen Sie abhängig von Ihren Anforderungen wählen können.  

Wenn die Benutzeroberflächen, die Sie Ihren Kunden bereitstellen, Virtual Reality-Headsets benötigen, sind die folgenden Markt Einführungs-Headsets von HP, Samsung und Acer sehr gut geeignet. Jedes Headset hat seine eigenen differenzierten Attribute. Weitere Details finden Sie unten.

HP-Reverb: [Details](https://hp.com/go/Reverbpro)

Samsung Odyssey +: [Details](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)

Acer: [Details](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)

Wenn Ihr Standort auf gemischte oder Erweiterte Realität spezialisiert ist, die die Verwendung eines "See-Through"-Headsets erfordert, können Sie die Microsoft hololens 2 beschaffen (jetzt für die Vorabbestellung geöffnet).  

Hololens 2: [Anordnen von Interesse](https://www.microsoft.com//hololens/buy)

Wenn Sie mit Erfahrungen experimentieren, die eine erweiterte Maschinelles sehen-, sprach-und Text Überwachung erfordern, finden Sie das Azure kinect-DK möglicherweise für Ihre Bedürfnisse.  

Azure kinect: [Details](https://azure.microsoft.com//services/kinect-dk/)

**F: Was ist das Portfolio von Rucksack-PCs, die ich verwenden kann, um meine PC-Tethering-VR-Erfahrungen auszuführen?**

Unsere OEMs bieten eine unglaubliche Auswahl von Rucksack-PCs, die genau für diese Anforderungen erstellt wurden.

HP hat soeben seinen HP VR-Rucksack G2 gestartet, der weltweit leistungsfähigste tragbaren PC – optimiert für die kostenlose Roaming-Umgebung, die jetzt 30% mehr Leistung mit einer RTX 2080-GPU in hat. [Details](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a>Setup

**F: Wie kann ich das Setup leichter konfigurieren und das Mixed Reality-Portal für LBE anpassen?**

>[!NOTE]
>Diese Funktion erfordert eine Version 2000.19061.1011.0 oder höher.  

Möglicherweise stellen Sie fest, dass Sie eine bessere Anpassung des gemischten Reality-Portals benötigen, als normalerweise über die APP zur Bereitstellung von Apps für Kiosk-oder angepasste Benutzeroberflächen verfügbar ist Das letzte Update des Mixed Reality-Portals von Juli unterstützt mehrere erweiterte Einstellungen, die über eine Konfigurationsdatei verfügen können, um folgende Aktionen durchzuführen:  

Fehlgeschlagene Systemüberprüfungen zulassen – normalerweise prüft der Setup Prozess den PC auf Kompatibilität mit Windows Mixed Reality, bevor das Setup abgeschlossen wird. Das umgehen dieses Problems kann Probleme verursachen, wenn Sie Windows Mixed Reality ausführen, wenn Kompatibilitätsprobleme vorliegen.  

Geräte-Begleit-App überspringen – die DCA bietet für den Hersteller bereitgestellte, vom Hersteller bereitgestellte, vom Hersteller bereitgestellte und aktualisierbare Aktualisierungs Schritte.  

Raumeinrichtung überspringen – anstatt zum Erstellen einer Raum Begrenzung aufgefordert zu werden, können Sie direkt mit dem-Headset im Modus "sitzend/stehend" fortfahren.  

Installieren von Apps aus dem Store überspringen: beim normalen Setup werden mehrere Store-Apps installiert, einschließlich des 3D-Viewers und des Edge 360 Viewer-Add-on. Dadurch wird die Installation dieser apps übersprungen, möglicherweise fehlen jedoch Gerätefunktionen.  

Vorschau anzeigen im Vollbild – im Mixed Reality-Portal wird standardmäßig die Headset-Vorschau im Vollbildmodus auf dem Desktop-PC angezeigt, während das Headset verwendet wird.  

Neue Option für den Seitenbereich ausblenden – dadurch wird verhindert, dass das neue Fenster für Sie beim Start des gemischten Reality-Portals erweitert wird.  

#### <a name="how-to-configure"></a>Vorgehensweise beim Konfigurieren von:  

Zum Festlegen dieser Konfigurationen müssen Sie in diesem Verzeichnis eine Datei namens " _userconfig. JSON_ " erstellen: _$ENV: LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState\\_

Für die meisten Benutzer sieht dies wie folgt aus: _c:\Benutzer\<username > \AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState\\_

Die JSON-Datei sollte den folgenden Inhalt aufweisen, wenn "true" für eine der oben genannten Einstellungen festgelegt ist, die Sie aktivieren möchten:  

```
{

  "shouldAllowFailedSystemChecks": true,

  "shouldSkipDcaApp": true,

  "shouldSkipRoomSetup": true,

  "shouldSkipStoreAppInstall": true,

  "shouldShowPreviewFullScreen": true,

  "shouldHideEngagementPane": true

}
```
 
**F: gibt es Hinweise zum Konfigurieren des Playspace?**

A: das Konfigurieren eines Playspace sollte wie bei der Benutzer Einrichtung durch den Consumer erfolgen. Mit dem Einrichtungs Vorgang für Räume können Sie auch Ihre Raum Grenzen definieren. Weitere Informationen zum Konfigurieren von Raum Begrenzungen finden Sie [hier](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).

Wie bereits im obigen Dokument erläutert, liegt der maximal zulässige Wert für die einfache Koordinate bei etwa 5mx5m. Wenn Sie über einen größeren Bereich verfügen möchten, können Sie die Funktion räumlicher Anker im Windows Holographic-API-Stapel verwenden. Die Verwendung dieser API erfordert eine benutzerdefinierte Entwicklung in den Erfahrungen, die Sie erzeugen.  

Weitere Informationen zum Optimieren von Inhalten für verschiedene Speicherplatz Größen finden Sie [hier](https://docs.microsoft.com//windows/mixed-reality/coordinate-systems).
 

**F: der Speicherplatz ist zu groß, und es treten Fehler auf, wenn ich versuche, eine bestehende Funktion mit Grenzen einzurichten. Was soll ich tun, um meine große kostenlose Roaming-Arbeit einzurichten?**

A: Wenn Sie einen größeren Speicherplatz als ~ 18x18ft einrichten möchten, können Sie die vom System bereitgestellte Begrenzungs Funktion nicht verwenden.  Die Begrenzungs Systeme nutzen eine einzelne festgelegte Koordinate "Anker", die instabil werden kann, wenn ein Benutzer zu weit vom Anker der Mittelstufe entfernt ist. 

Stattdessen können Sie den Modus "sitzend" einrichten, in dem die Grenze nicht angezeigt wird, oder Sie können keine Stufen Begrenzungen oder einen Playspace konfigurieren.  Anschließend müssen Sie mehrere räumliche Anker innerhalb der App konfigurieren, um auf physische Begrenzungs Bereiche zu verweisen. 

Der Anwendungsentwickler ist dafür verantwortlich, die erforderlichen Sicherheitsvorkehrungen anzuzeigen, damit Benutzer nicht mit der physischen Umgebung in Konflikt stehen.  Dabei kann es sich um digitale Wände innerhalb der Darstellung oder um ein angepasstes visuelles Spielelement handeln. 

Anleitungen zum Einrichten der Raumgrenze mit WMR finden Sie [hier](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).

**F: wo befindet sich der Ursprung des Playspace?**

A: der Ursprung des Playspace wird durch die Einrichtung des Raums festgelegt, genauer gesagt die Position des HMD, wenn während des Setups die Schaltfläche "Mittelpunkt" gedrückt wird. 

### <a name="multi-player-setup"></a>Einrichtung von mehreren Playern

**F: Ich lege in meinem Veranstaltungsort eine Multiplayer-Funktionalität bereit. Wird dies unter Windows Mixed Reality unterstützt?**

A: das Mixed Reality Spatial Data Packager-Tool ist ein Beta Feature, das das Lokalisieren von mehreren Playern im gleichen Raum ermöglicht, indem es das Portieren räumlicher Daten von einem PC auf einen anderen ermöglicht. Sie können auf das Tool zugreifen und weitere [Informationen dazu erhalten.](mixedrealityspatialdatapackager.md)

Wenn Sie sich für die Builds von Windows 20h1 oder höher entscheiden (über unser [Insider](https://docs.microsoft.com//windows-insider/at-home/get-started) -Programm), können Sie auf eine neue Schnittstelle für die Karten Freigabe zugreifen. Diese neue Funktionalität ist über die Map Manager-Schnittstelle des Windows-Geräte Portals verfügbar. Gehen Sie folgendermaßen vor, um dieses Tool zu verwenden:
- Stellen Sie sicher, dass Sie 20 H1 oder höher gewählt haben (ab September 2019 Dies bedeutet, dass unser Insider-Programm verwendet wird).
- Aktivieren Sie das Windows-Geräte Portal (WDP). Anweisungen finden Sie [hier](https://docs.microsoft.com//windows/uwp/debug-test-perf/device-portal-desktop) .
- Einbinden eines Windows Mixed Reality-HMD, bei dem Sie entweder eine vorhandene Karte herunterladen oder eine neue Karte importieren möchten
- Navigieren Sie im Browser Ihrer Wahl zum WDP, und verwenden Sie dabei die URL, die auf dem Bildschirm Einstellungen angegeben ist. 
  - Navigieren Sie anschließend zum Abschnitt "Mixed Reality", und wählen Sie "Map Manager" aus. 
  - Sie können jetzt die Schaltfläche "herunterladen" verwenden, um eine vorhandene Karte vom Computer zu exportieren. 
  - Sie können die Schaltfläche "Hochladen einer Zuordnungs Datei" verwenden, um eine Zuordnung aus einem vorherigen Export (vielleicht auf einem anderen Computer) zu importieren. 
  - Sie können "Importieren" verwenden, um das System für die Verwendung dieser Zuordnung für dieses HMD auf diesem Computer zu aktivieren.
  
### <a name="tracking"></a>Paletten

F: wie funktioniert die nach Verfolgungs Technologie in den Windows Mixed Reality-Headsets?  

Gemischte Realität nutzt dieselbe nach Verfolgungs Technologie wie hololens. Weitere Informationen zum in-out-nach Verfolgungs [System finden Sie in der Dokumentation.](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/tracking-system)

Eine Beschreibung der Funktionsweise des räumlichen Zuordnungs Systems auf höherer Ebene finden Sie [hier](spatial-mapping.md).

**F: gibt es bewährte Methoden, um ein zuverlässiges nach Verfolgungs Volume zu erhalten?**

Zum optimalen Konfigurieren der Umgebung für die erfolgreiche Überwachung können Sie die bewährten Methoden in diesem [Beitrag](environment-considerations-for-hololens.md)lesen.

**F: gibt es bestimmte Nuancen bei der Nachverfolgung von Speicherplätzen oder Optimierungen, die in Erwägung gezogen werden sollen?**

A: mithilfe der folgenden Vorgehensweisen können Sie ein zuverlässigeres nach Verfolgungs Volume erzielen:  

Wenn Sie eine Vielzahl von Features im Raum bereitstellen, die sich an mehreren Positionen überlappen, kann das Überwachungssystem eine solide Sperre erhalten. Stellen Sie sich die zufälligen Zeichnungs-Splatter und Schraffuren vor, anstelle von Solid-Contour-stillinien. 

Minimieren Sie möglichst den dynamischen Bereich der Beleuchtung in Ihrem Bereich. Die Überwachungskameras in den Mixed Reality-HMDs sind nicht HDR und verfügen über AGC (automatischer Gewinn) und AEC (automatische verfügbar machung), um mit der unterschiedlichen Beleuchtung umzugehen. Abhängig von der Verteilung von Oberflächen Licht, Mustern und Kontrast kann es sein, dass entweder "AGC" oder "AEC" sich in einem sehr viel weißen und schwarzen Raum befindet Wenn Sie versuchen, ein inneres Bild vor einem äußeren Fenster mit heller Sommerzeit zu machen, und Sie die Verfügbarkeit anpassen, sodass Sie Details außerhalb von sehen können, ist alles im Inneren nicht verfügbar und schwarz. Wenn Sie in festgelegt ist, wird alles außen nun überlastet und weiß.  

Gibt einen Raum (auch mehr Aufwand) aus, der angezeigt wird, wenn Überwachungskameras manchmal Täter sein können, die den AEC/AGC der Überwachungskameras verwechseln. Die flache/Diffused-Beleuchtung ist hilfreich.  

### <a name="mixed-reality-cloud-services-and-azure"></a>Gemischte Realität Cloud Services und Azure 

**F: Wie kann Microsoft Azure meiner geschäftlichen Skalierbarkeit helfen?**

A: Azure-basierte und Remote Verwaltung können Ihrem Unternehmen helfen, Daten gesteuert zu werden, Betriebskosten zu senken und die Bereitstellung über vorhandene und neue Standorte hinweg zu skalieren. Azure-Clouddienste wie Azure Storage, Azure Functions, App Service, Azure-Netzwerke und IOT Hub können die folgenden Anwendungsfälle unterstützen:  

Remote Geräte Bereitstellung & Verwaltung 

Echtzeitanalyse 

Intelligent anpassbares LBE-Spiel 

Streaming und Bereitstellung von LBE-Inhalten 

Heatmap für LBE-Player-Vorlieben 

LBE-Reservierungs-und-Reservierungs System 

**F: Ich entwickle eine räumliche MMOG für die Bereitstellung über einen riesigen Speicherbedarf. Alle Dienste, die mir helfen, meine Inhalte und Objekt Persistenz zu verwalten?**

A: räumliche Azure-Anker sind ein neuer gemischter Reality-Dienst, der mehr Benutzer, räumlich unterstützende gemischte Reality-Umgebungen auf hololens-, IOS-und Android-Geräten ermöglicht. Weitere Informationen zu räumlichen Azure-Ankern finden Sie [hier](https://azure.microsoft.com//services/spatial-anchors/).

**F: Unser Veranstaltungsort ist auf die Erfahrung von mehreren Playern spezialisiert, und ich möchte unsere Entwicklungszeit auf Inhalte und die Front-End-Entwicklung konzentrieren. Gibt es Angebote, die mir helfen können, die Back-End-Entwicklung zu Bootstrap oder auszulagern?**

A: Azure playfab ist eine umfassende Back-End-Plattform für Live Spiele. Weitere Informationen hierzu finden Sie [hier](https://playfab.com/).

### <a name="misc"></a>Sonstige

**F: Ich verwende "steamvr", um meine Erfahrungen bereitzustellen. Funktioniert Windows Mixed Reality mit steamvr?**

A: Windows Mixed Reality für steamvr ermöglicht Benutzern das Ausführen von steamvr-Erfahrungen auf Windows Mixed Reality-immersiven Headsets. Weitere Informationen zu "steamvr" mit WMR [finden Sie hier](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality).

### <a name="support-and-community"></a>Support und Community  

Im folgenden finden Sie einige hilfreiche Ressourcen, mit denen Sie sich mit Experten in unserem Team befassen, Support bei der Problembehandlung erhalten und an der umfassenderen Community dev Community mitwirken können.  

Wenn Sie Probleme mit öffentlich veröffentlichten Features haben, melden Sie einen Fehler mit dem FeedHub. eine Anleitung finden Sie auf dieser [Seite](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/filing-feedback).

Wenn Sie weitere Hilfe zur Problembehandlung bei WMR benötigen, wenden Sie sich an das Kundensupport Team, indem Sie eine [Supportanfrage](https://support.microsoft.com//supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782)einreichen.

Treten Sie unserem holodevelopers Slack-Channel bei, um sich mit den Entwicklern zu beschäftigen, die an gemischter Realität und Fachleuten des Teams arbeiten: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)

Twitter: Befolgen Sie unser Mixed Reality Developer Beziehungs Team für Neuigkeiten, Veranstaltungen und Updates @MxdRealityDev 

Wenn Sie sich in der Nähe von San Francisco befinden, gibt es immer etwas, das im Microsoft-Reaktor passiert. Sie können den Kalender der Ereignisse [hier](https://developer.microsoft.com//reactor/Location/San%20Francisco)sehen.
