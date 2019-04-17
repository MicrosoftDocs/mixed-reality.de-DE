---
title: Verwenden Vuforia mit Unity
description: Nutzen Sie Vuforia Windows Mixed Reality-Anwendungen in Unity erstellen.
author: ChimeraScorn
ms.author: cwhite
ms.date: 03/21/2018
ms.topic: article
keywords: Vuforia, Marker, die Koordinaten, die als Referenz, Nachverfolgen
ms.openlocfilehash: 43a74989b931fee898af0aeae9e240303b2eef01
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595988"
---
# <a name="using-vuforia-engine-with-unity"></a>Verwenden Vuforia-Engine mit Unity

Vuforia-Engine bietet eine wichtige Funktion für HoloLens: die Möglichkeit, AR-Verbindung auftritt, bestimmte Bilder und Objekte in der Umgebung. Sie können diese Funktion verwenden, zum überlagern geführte Anleitung zusätzlich der Maschinen für die Industrie Enterprise oder zum Hinzufügen von digitalen Features und Funktionen physischen Produkt oder eine Spiel. 

Für größere Flexibilität beim Entwickeln von AR auftritt, bietet Vuforia-Engine eine Vielzahl von Features und Zielen. Eine unserer neuesten Features, Vuforia-Modell ausgerichtet ist, ist ein entscheidendes Merkmal für kommerzielle und Industrie verwendet. Modellziele können Anwendungen erkennen physische Objekte wie Computer "," Automobile "oder" Toys, und verfolgen basierend auf der CAD- oder digitale 3D-Modells verwendet wird. Für die Industrie verwendet kann dieses Feature Assembly-Worker und Technikern mit AR arbeiten, Anweisungen und schrittweise Anleitungen, während Sie in der Factory oder out-im Feld. 

Vorhandene Vuforia-Engine-apps, die für Smartphones und Tablets erstellt wurden, können ganz einfach in Unity auf HoloLens ausgeführt konfiguriert werden. Sie können sogar Vuforia-Engine verwenden, zu der neuen HoloLens-app auf Windows 10-Tablets, z. B. 4 Surface Pro und Surface Book.

## <a name="get-the-tools"></a>Laden Sie die Tools herunter

[Installieren Sie die empfohlenen Versionen](install-the-tools.md) von Visual Studio und Unity und konfigurieren Sie Unity aus, um Visual Studio und die bevorzugte IDE und den Compiler zu verwenden. 

Bei der Installation von Unity, achten Sie darauf, dass Sie entweder "Windows Store .NET Scripting Back-End" oder "Windows Store IL2CPP Scripting Back-End" installieren. Darüber hinaus werden Sie sicher, dass "Vuforia Augmented Reality-Unterstützung" Vuforia-Modul in Unity aktiviert.


## <a name="getting-started-with-vuforia-engine"></a>Erste Schritte mit Vuforia-Engine

Da in Unity Vuforia-Engine integriert ist, müssen Entwickler nicht herunterladen oder installieren keine zusätzlichen Tools. Die empfohlene Version von Unity ist der LTS-Stream ist zurzeit 2017.3 und Vuforia Engine 7.0.57 enthält. Die am besten Anfangspunkt für etwas über die Verwendung von Vuforia-Engine mit HoloLens mit ist der [Vuforia-Engine HoloLens Beispiel](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (verfügbar in der Unity Asset Store). Das Beispiel bietet ein vollständiges HoloLens-Projekt, einschließlich vorkonfiguriert, dass Szenen, die auf eine HoloLens bereitgestellt werden können.

Im Hintergrund zeigen, wie Sie ein Bild zu erkennen und erweitern sie digitale Inhalte in einer Benutzeroberfläche HoloLens Vuforia Image Ziele mit. Entwickler, die mit aktuelleren Versionen von Unity und Vuforia haben Zugriff auf aktualisierte Beispiele, darunter eine Szene, der die Verwendung von Modellziele auf HoloLens anzeigt. Sie können ganz einfach Ihre eigenen Inhalte in den Kulissen experimentieren Sie mit der Erstellung von apps für HoloLens, mit denen Vuforia-Engine ersetzen.


## <a name="configuring-a-vuforia-app-for-hololens"></a>Konfigurieren einer App Vuforia für HoloLens

Entwickeln eine app Vuforia-Engine für HoloLens ist im Grunde identisch mit der Entwicklung von Vuforia-Engine-apps für andere Geräte. Sie können dann die Buildeinstellungen und Konfigurationen, die im Abschnitt unten beschrieben anwenden. Das ist alles, die was erforderlich ist, um Vuforia-Engine mit der HoloLens räumliche Zuordnung Geschäfts-, Schul- oder mit Feldern fester Breite tracking-Systeme zu aktivieren.

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>Erstellen Sie und führen Sie des Beispiels Vuforia-Engine für HoloLens aus
1.  Herunterladen der [Vuforia-Engine-Beispiel für HoloLens](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) aus dem Unity Asset Store
2.  Anwenden der [empfohlene Unity-Engine-Optionen für die Stromversorgung und Leistung](performance-recommendations-for-unity.md)
3.  Fügen Sie die Beispiel-Szenen Szenen in Build hinzu.
4.  Festlegen von Ihrer Zielplattform für den Build für "Universal Windows Platform" in Datei > Buildeinstellungen.
5.  Wählen Sie die folgenden Konfigurationseinstellungen der Plattform erstellen: 
   * Geräte = HoloLens
   * Buildtyp D3D =
   * SDK = aktuelle installiert
   * Visual Studio-Version = aktuelle installiert
   * Erstellen und Ausführen auf = lokalen Computer
6.  Definieren Sie einen eindeutigen **Produktname**im **Playereinstellungen**, als der Name der app bei der Installation auf die HoloLens dienen.
7.  Überprüfen Sie **Vuforia Augmented Reality** und **virtuelle Realität unterstützt** in **Playereinstellungen > XR-Einstellungen**
8.  Außerdem **XR-Einstellungen**, stellen Sie sicher, dass "Windows Mixed Reality" hinzugefügt wird die **virtuelle Realität SDKs** Liste
9.  Überprüfen Sie die folgenden Funktionen in den Player-Einstellungen > Veröffentlichungseinstellungen 
   * InternetClient
   * WebCam
   * SpatialPerception – Wenn Sie beabsichtigen, die Oberfläche Observer-API verwenden
10. Wählen Sie Build aus, generiert Visual Studio-Projekt
11. Die ausführbare Datei aus Visual Studio erstellen und installieren Sie ihn auf Ihrem HoloLens

Hinweis: Ab Version 7.2, HoloLens die Vuforia-Engine zum Beispiel umfasst eine Beispiel-Szene, einschließlich Beispiel für die Verwendung der Modell-Ziele

## <a name="the-vuforia-developer-portal"></a>Das Vuforia-Entwicklerportal

Entwickler, die zum Erstellen von eigenen AR mit Vuforia-Engine hat und HoloLens sollten registrieren Sie sich auf unsere Vuforia-Entwicklerportal unter [developer.vuforia.com](https://developer.vuforia.com/). Im Portal haben Entwickler Zugriff auf die [Vuforia-Engine-Foren](https://developer.vuforia.com/forum) , wo sie Communitydiskussionen, beitreten können eine [Bibliothek](https://library.vuforia.com/) ausführliche Dokumentation für alle Vuforia-Engine-Funktionen und die [ Ziel-Manager Vuforia](https://developer.vuforia.com/target-manager) in dem Benutzer eigene benutzerdefinierte Ziele erstellen können. Entwickler können außerdem registrieren Sie sich für eine kostenlose Entwicklerlizenz mit der [Vuforia License Manager](https://developer.vuforia.com/license-manager).

## <a name="extended-tracking-with-vuforia"></a>Erweiterte Überwachung mit Vuforia

[Die erweiterte nachverfolgung](https://library.vuforia.com/articles/Training/Extended-Tracking) erstellt eine Zuordnung der Umgebung zu verwalten, nachverfolgen, selbst wenn ein Ziel nicht mehr angezeigt wird. Es handelt es sich um Vuforia Engines Gegenstück, die räumliche Zuordnung von HoloLens ausgeführt. Wenn Sie die erweiterte Überwachung auf einem Ziel aktivieren, können Sie die Haltung, Ziel, das räumliche Zuordnung-System übergeben werden soll. Auf diese Weise können Ziele die Vuforia Modul- und HoloLens räumliche Koordinatensysteme, jedoch nicht gleichzeitig vorhanden sein.

![Unity-Fenster "Einstellungen"](images/vuforia-extendedtracking.png)<br>
*Unity-Fenster "Einstellungen"*

**Aktivieren der erweiterten Überwachung für ein Ziel**

Vuforia-Engine wird automatisch der Haltung eines Ziels transformieren, die erweiterte Überwachung in der räumlichen HoloLens-Koordinatensystem verwendet. Dadurch wird die HoloLens Überwachungsprofil übernehmen und alle Inhalte, erweitern in die räumliche Zuordnung des Zielbereichs-Umgebung zu integrieren. Dieser Prozess erfolgt zwischen Vuforia-Engine "und" mixed Reality-APIs in Unity und erfordert keinen vom Entwickler programmieren – erfolgt automatisch.

**Hier ist, was geschieht...**
1. Die Vuforia Target Tracker erkennt das Ziel
2. Ziel, die nachverfolgung wird anschließend initialisiert.
3. Die Position und Drehung des Ziels werden analysiert, um eine stabile Haltung Schätzung für HoloLens verwenden
4. Vuforia transformiert des Ziels Haltung in HoloLens räumliche Zuordnung Koordinatenbereich
5. HoloLens übernimmt nachverfolgen und die Vuforia nachverfolgung ist deaktiviert.

Der Entwickler kann dieser Prozess, damit die Steuerung auf Vuforia, durch das Deaktivieren der erweiterten Überwachung für die TargetBehaviour steuern.

**HINWEIS:** Seit Vuforia 7.2, ist erweiterte nachverfolgung nicht mehr auf einer pro-Ziel-Basis aktiviert. Stattdessen können Entwickler auf dem Gerät Überwachungsdatenbank-ähnliche Funktionalität für alle Ziele in der Szene zu aktivieren.


## <a name="see-also"></a>Siehe auch
* [Installieren der tools](install-the-tools.md)
* [Koordinatensysteme](coordinate-systems.md)
* [Räumliche Zuordnung](spatial-mapping.md)
* [Kamera in Unity](camera-in-unity.md)
* [Exportieren und Erstellen von Unity Visual Studio-Projektmappe](exporting-and-building-a-unity-visual-studio-solution.md)
* [Vuforia Dokumentation: Entwickeln für Windows 10 in Unity](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [Vuforia Dokumentation: Vorgehensweise: installieren die Vuforia Unity-Erweiterung](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [Vuforia Dokumentation: Arbeiten mit dem HoloLens-Beispiel in Unity](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [Vuforia Dokumentation: Erweiterte Überwachung in Vuforia](https://library.vuforia.com/articles/Training/Extended-Tracking)
