---
title: Verwenden von vuforia mit Unity
description: Nutzen Sie vuforia zum Erstellen von Windows Mixed Reality-Anwendungen in Unity.
author: thetuvix
ms.author: alexturn
ms.date: 12/20/2019
ms.topic: article
keywords: Vuforia, Marker, Koordinaten, Referenzrahmen, Nachverfolgung
ms.openlocfilehash: 2d7cc27cd9a5fe9bb6502edaa6df0b7a80755049
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334476"
---
# <a name="using-vuforia-engine-with-unity"></a>Verwenden der vuforia-Engine mit Unity

Die vuforia-Engine bringt hololens eine wichtige Funktion ein – die Strom Umgebung, um eine Verbindung zwischen aren Erfahrungen und bestimmten Bildern und Objekten in der Umgebung herzustellen. Sie können diese Funktion verwenden, um eine Schritt-für-Schritt-Anleitung für das Industrieunternehmen zu überlagern oder digitale Features und Erfahrungen zu einem physischen Produkt oder Spiel hinzuzufügen.

Die vuforia-Engine bietet eine große Bandbreite an Features und Zielen, um bei der Entwicklung von aren Erfahrungen mehr Flexibilität zu erzielen. Eine unserer neuesten Features, vuforia-Modell Ziele, ist eine wichtige Funktion für gewerbliche und Industrieanwendungen. Mithilfe von Modell Zielen können Anwendungen physische Objekte wie Computer, Automobile oder Toys erkennen und basierend auf einem CAD-oder Digital 3D-Modell verfolgen. Bei Industrieanwendungen kann dieses Feature assemblyarbeitsthreads und Dienst Technikern eine ausführliche Arbeitsanleitung und Anleitungen für die Bereitstellung in der Factory und im Außendienst bereitstellen.

Vorhandene vuforia-Engine-apps, die für Smartphones und Tablets erstellt wurden, können problemlos in Unity zur unter hololens-Konfiguration konfiguriert werden. Sie können die vuforia-Engine sogar verwenden, um Ihre neue hololens-App auf Windows 10-Tablets wie Surface pro und Surface Book zu übernehmen.


## <a name="get-the-tools"></a>Laden Sie die Tools herunter

[Installieren Sie die empfohlenen Versionen](install-the-tools.md) von Visual Studio und Unity, und konfigurieren Sie Unity so, dass Visual Studio und die bevorzugte IDE und der Compiler verwendet werden. 

Stellen Sie bei der Installation von Unity sicher, dass Sie das "Windows Store IL2CPP Scripting Backend" installieren.

Das Hinzufügen der Unterstützung der vuforia-Engine funktioniert abhängig von ihrer Unity-Version unterschiedlich:
*   Unity 2018,4: Herunterladen des Installers für die vuforia-Engine für Unity 2018,4 aus dem vuforia-Entwickler Portal
*   Unity 2019,2: Holen Sie sich das neueste [Paket der vuforia-Engine](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/vuforia-engine-package-hosting-for-unity.html) . 

## <a name="getting-started-with-vuforia-engine"></a>Einstieg in die vuforia-Engine

Der beste Ausgangspunkt für die Verwendung der vuforia-Engine mit hololens ist das [Beispiel der vuforia-Engine hololens](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (verfügbar im Unity-Ressourcen Speicher). Das Beispiel enthält ein umfassendes hololens-Projekt, das vorkonfigurierte Szenen umfasst, die in einem hololens bereitgestellt werden können.

In den Kulissen wird gezeigt, wie Sie mithilfe von vuforia-Bild Zielen ein Bild erkennen und mit digitalen Inhalten in einer hololens-Funktionalität erweitern können. Das Beispiel der vuforia-Engine hololens enthält auch eine Szene, in der die Verwendung von Modell Zielen und vgargs in hololens gezeigt wird. Sie können Ihren eigenen Inhalt problemlos in den Kulissen austauschen, um mit der Erstellung von hololens-apps zu experimentieren, die die vuforia-Engine verwenden.



## <a name="configuring-a-vuforia-app-for-hololens"></a>Konfigurieren einer vuforia-App für hololens

Das Entwickeln einer vuforia-Engine-App für hololens ist im Grunde das gleiche wie das Entwickeln von vuforia-Engine-Apps für andere Geräte. Anschließend können Sie die im Abschnitt unten beschriebenen Buildeinstellungen und Konfigurationen anwenden. Das ist alles, was erforderlich ist, um die vuforia-Engine für die Zusammenarbeit mit der räumlichen Zuordnung von hololens und den Systemen mit Positionsüberwachung zu aktivieren.

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>Erstellen und Ausführen des Beispiels "vuforia Engine" für hololens
1.  Laden Sie das [Beispiel für die vuforia-Engine für hololens](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) aus dem Unity-Asset Store herunter.
2.  Anwenden der [empfohlenen Unity-Engine-Optionen auf Leistung und Leistung](performance-recommendations-for-unity.md)
3.  Fügen Sie die Beispiel Szenen zu Szenen in Build hinzu.
4.  Legen Sie das Ziel der Platt Form Erstellung für "universelle Windows-Plattform" in Datei > Buildeinstellungen fest.
5.  Wählen Sie die folgenden Platform Build-Konfigurationseinstellungen aus: 
   * Zielgerät = hololens
   * Buildtyp = D3D
   * SDK = neueste installiert
   * Visual Studio Version = neueste installiert
   * Erstellen und ausführen auf = lokalem Computer
6.  Definieren Sie einen eindeutigen **Produktnamen**in **Player Einstellungen**, der als Name der APP fungiert, wenn Sie auf den hololens installiert werden.
7.  Überprüfen von **vuforia Augmented Reality** und **Virtual Reality unterstützt** in den **Player Einstellungen > XR-Einstellungen**
8.  Stellen Sie außerdem unter " **XR-Einstellungen**" sicher, dass "Windows Mixed Reality" der **Virtual Reality sdgt** -Liste hinzugefügt wird.
9.  Überprüfen Sie die folgenden Funktionen in den Einstellungen für Player Einstellungen > veröffentlichen. 
   * Internet Client deklarieren
   * Webcam
   * Spatialperception: Wenn Sie beabsichtigen, die Surface Observer-API zu verwenden
10. Build auswählen, um ein Visual Studio-Projekt zu generieren
11. Erstellen Sie die ausführbare Datei aus Visual Studio, und installieren Sie Sie auf Ihren hololens.

Hinweis: ab Version 7,2 enthält das Beispiel für die vuforia-Engine für hololens eine Beispiel Szene einschließlich Beispiel Verwendung von Modell Zielen.

## <a name="the-vuforia-developer-portal"></a>Das vuforia-Entwickler Portal

Entwickler, die ihre eigenen aren Erfahrungen mit der vuforia-Engine und hololens erstellen möchten, sollten sich bei unserem vuforia-Entwickler Portal unter [Developer.vuforia.com](https://developer.vuforia.com/)anmelden. Im Portal haben Entwickler Zugriff auf die [vuforia-Engine-Foren](https://developer.vuforia.com/forum) , in denen Sie Communitydiskussionen beitreten können, eine [Bibliothek](https://library.vuforia.com/) mit ausführlichen Dokumentationen zu allen Features der vuforia-Engine und der [vuforia-Ziel-Manager](https://developer.vuforia.com/target-manager) , in dem Benutzer ihre eigenen benutzerdefinierten Ziele erstellen können. Entwickler können sich mit dem [vuforia-Lizenz-Manager](https://developer.vuforia.com/license-manager)auch für eine kostenlose Entwicklerlizenz registrieren.

## <a name="extended-tracking-with-vuforia"></a>Erweiterte Nachverfolgung mit vuforia

Die [Erweiterte Nachverfolgung](https://library.vuforia.com/articles/Training/Extended-Tracking) behält die Nachverfolgung auch dann bei, wenn ein Ziel nicht mehr in der Ansicht Sie wird automatisch für alle Ziele aktiviert, wenn die Protokollierung für Positions Geräte aktiviert ist. Bei hololens-Anwendungen wird die Positional-Geräte Protokollierung automatisch in Unity gestartet.

Die vuforia-Engine verbindet die Posen automatisch von der Kamera Verfolgung und der räumlichen Nachverfolgung von hololens, um stabile Ziele bereitzustellen, unabhängig davon, ob das Ziel von der Kamera erkannt wird oder nicht.

Da der Prozess automatisch verarbeitet wird, ist keine Programmierung durch den Entwickler erforderlich.


**Im folgenden finden Sie eine allgemeine Beschreibung des Prozesses:**
1. Der Ziel-Tracker von vuforia erkennt das Ziel.
2. Die Ziel Überwachung wird initialisiert.
3. Die Position und die Drehung des Ziels werden analysiert, um eine robuste positätsschätzung für hololens bereitzustellen.
4. Die gestellungsweb-Engine wandelt die Pose des Ziels in das hololens Spatial Mapping-Koordinaten Bereich um.
5. Hololens übernimmt die Überwachung, wenn das Ziel nicht mehr in der Ansicht angezeigt wird. Wenn Sie sich das Ziel erneut ansehen, verfolgt vuforia die Bilder und Objekte weiterhin korrekt.

Ziele, die erkannt werden, aber nicht mehr in der Ansicht angezeigt werden, werden als EXTENDED_TRACKED gemeldet. In diesen Fällen rendern das defaulttrackableeventhandler-Skript, das für alle Ziele verwendet wird, den Erweiterungs Inhalt weiter. Der Entwickler kann dieses Verhalten steuern, indem er ein benutzerdefiniertes Skript für einen ausführbaren Ereignishandler implementiert.


## <a name="performance-mode-with-vuforia-engine"></a>Leistungsmodus mit der vuforia-Engine 

Es ist möglich, dass die vuforia-Engine die Leistung auf den hololens verwaltet, um die Benutzerfreundlichkeit zu verringern und die Arbeitsauslastung auf der CPU zu verringern. Die vuforia-Engine bietet drei Modi, die ausgewählt werden können: Standard, zur Optimierung der Geschwindigkeit und zur Optimierung der Qualität. 

*   Mit MODE_OPTIMIZE_SPEED können Sie die Arbeitsauslastung auf dem hololens-Gerät minimieren und eignen sich hervorragend für die Erweiterung von aren Erfahrungen. Dies empfiehlt sich für Situationen, in denen die APP statische Objekte/Ziele nachverfolgt.
*   MODE_DEFAULT ist der normale Modus, der in den meisten Szenarien verwendet werden kann.
*   MODE_OPTIMIZE_QUALITY eignet sich besser für die Nachverfolgung von verschiebbaren Zielen oder Modell Zielen, die Sie erwarten.

**Festlegen des Modus**

Wenn Sie den Leistungsmodus in Unity ändern möchten, navigieren Sie zu "vuforia Configuration" (STRG + UMSCHALT + v/cmd + UMSCHALT + v), die sich im arcamera-gameobject als Komponente befindet. 
*   Wählen Sie das Dropdown Menü für den Kamerageräte Modus aus, und wählen Sie eine der drei Optionen aus.


## <a name="see-also"></a>Weitere Informationen:
* [Installieren der Tools](install-the-tools.md)
* [Koordinatensysteme](coordinate-systems.md)
* [Räumliche Abbildung](spatial-mapping.md)
* [Kamera in Unity](camera-in-unity.md)
* [Exportieren und Erstellen einer Unity-Projektmappe für Visual Studio](exporting-and-building-a-unity-visual-studio-solution.md)
* [Vuforia-Dokumentation: entwickeln für Windows 10 in Unity](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [Vuforia-Dokumentation: Installieren der vuforia Unity-Erweiterung](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [Vuforia-Dokumentation: Arbeiten mit dem hololens-Beispiel in Unity](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [Vuforia-Dokumentation: Erweiterte Nachverfolgung in vuforia](https://library.vuforia.com/articles/Training/Extended-Tracking)
