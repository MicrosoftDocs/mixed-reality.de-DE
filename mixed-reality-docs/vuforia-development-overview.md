---
title: Verwenden von vuforia mit Unity
description: Nutzen Sie vuforia zum Erstellen von Windows Mixed Reality-Anwendungen in Unity.
author: ailyadis
ms.author: ''
ms.date: 01/28/2019
ms.topic: article
keywords: Vuforia, Marker, Koordinaten, Referenzrahmen, Nachverfolgung
ms.openlocfilehash: c0d2f6d0707e1ddd3ee00d3eb80af9fb459f252b
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750350"
---
# <a name="using-vuforia-engine-with-unity"></a>Verwenden der vuforia-Engine mit Unity

Die vuforia-Engine bringt hololens eine wichtige Funktion ein – die Strom Umgebung, um eine Verbindung zwischen aren Erfahrungen und bestimmten Bildern und Objekten in der Umgebung herzustellen. Sie können diese Funktion verwenden, um eine Schritt-für-Schritt-Anleitung für das Industrieunternehmen zu überlagern oder digitale Features und Erfahrungen zu einem physischen Produkt oder Spiel hinzuzufügen. 

Die vuforia-Engine bietet eine große Bandbreite an Features und Zielen, um bei der Entwicklung von aren Erfahrungen mehr Flexibilität zu erzielen. Eine unserer neuesten Features, vuforia-Modell Ziele, ist eine wichtige Funktion für gewerbliche und Industrieanwendungen. Mithilfe von Modell Zielen können Anwendungen physische Objekte wie Computer, Automobile oder Toys erkennen und basierend auf einem CAD-oder Digital 3D-Modell verfolgen. Bei Industrieanwendungen kann dieses Feature assemblyarbeitsthreads und Dienst Technikern eine ausführliche Arbeitsanleitung und Anleitungen für die Bereitstellung in der Factory und im Außendienst bereitstellen. 

Vorhandene vuforia-Engine-apps, die für Smartphones und Tablets erstellt wurden, können problemlos in Unity zur unter hololens-Konfiguration konfiguriert werden. Sie können die vuforia-Engine sogar verwenden, um Ihre neue hololens-App auf Windows 10-Tablets wie Surface pro 4 und Surface Book zu übernehmen.

## <a name="get-the-tools"></a>Laden Sie die Tools herunter

[Installieren Sie die empfohlenen Versionen](install-the-tools.md) von Visual Studio und Unity, und konfigurieren Sie Unity so, dass Visual Studio und die bevorzugte IDE und der Compiler verwendet werden. 

Achten Sie bei der Installation von Unity darauf, dass Sie entweder "Windows Store .net Scripting Backend" oder "Windows Store IL2CPP Scripting Backend" installieren. Achten Sie auch darauf, "vuforia Augmented Reality Support" auszuwählen, um die vuforia-Engine in Unity zu aktivieren.


## <a name="getting-started-with-vuforia-engine"></a>Einstieg in die vuforia-Engine

Da die vuforia-Engine in Unity integriert ist, müssen Entwickler keine zusätzlichen Tools herunterladen oder installieren. Die empfohlene Version von Unity ist der LTS-Datenstrom, der derzeit 2017,3 ist und die vuforia-Engine 7.0.57 enthält. Der beste Ausgangspunkt für die Verwendung der vuforia-Engine mit hololens ist das [Beispiel der vuforia-Engine hololens](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (verfügbar im Unity-Ressourcen Speicher). Das Beispiel enthält ein umfassendes hololens-Projekt, das vorkonfigurierte Szenen umfasst, die in einem hololens bereitgestellt werden können.

In den Kulissen wird gezeigt, wie Sie mithilfe von vuforia-Bild Zielen ein Bild erkennen und mit digitalen Inhalten in einer hololens-Funktionalität erweitern können. Entwickler, die neuere Versionen von Unity und vuforia verwenden, haben Zugriff auf aktualisierte Beispiele, die eine Szene mit der Verwendung von Modell Zielen in hololens enthalten. Sie können Ihren eigenen Inhalt problemlos in den Kulissen austauschen, um mit der Erstellung von hololens-apps zu experimentieren, die die vuforia-Engine verwenden.


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

Hinweis: Ab Version 7,2 enthält das Beispiel für die vuforia-Engine für hololens eine Beispiel Szene einschließlich Beispiel Verwendung von Modell Zielen.

## <a name="the-vuforia-developer-portal"></a>Das vuforia-Entwickler Portal

Entwickler, die ihre eigenen aren Erfahrungen mit der vuforia-Engine und hololens erstellen möchten, sollten sich bei unserem vuforia-Entwickler Portal unter [Developer.vuforia.com](https://developer.vuforia.com/)anmelden. Im Portal haben Entwickler Zugriff auf die [vuforia-Engine-Foren](https://developer.vuforia.com/forum) , in denen Sie Communitydiskussionen beitreten können, eine [Bibliothek](https://library.vuforia.com/) mit ausführlicher Dokumentation zu allen Features der vuforia-Engine und der [vuforia-Ziel-Manager](https://developer.vuforia.com/target-manager) , in dem Benutzer Erstellen Sie Ihre eigenen benutzerdefinierten Ziele. Entwickler können sich mit dem [vuforia-Lizenz-Manager](https://developer.vuforia.com/license-manager)auch für eine kostenlose Entwicklerlizenz registrieren.

## <a name="extended-tracking-with-vuforia"></a>Erweiterte Nachverfolgung mit vuforia

Bei der [erweiterten Nachverfolgung](https://library.vuforia.com/articles/Training/Extended-Tracking) wird eine Zuordnung der Umgebung erstellt, um die Nachverfolgung beizubehalten, auch wenn ein Ziel nicht mehr angezeigt wird. Es ist das Pendant von vuforia Engines zu der räumlichen Zuordnung, die von hololens durchgeführt wird. Wenn Sie die erweiterte Nachverfolgung für ein Ziel aktivieren, können Sie die Pose dieses Ziels an das räumliche Zuordnungssystem weitergeben. Auf diese Weise können Ziele sowohl in der vuforia-Engine als auch in den räumlichen Koordinatensystemen hololens vorhanden sein, jedoch nicht gleichzeitig.

![Unity-Einstellungsfenster](images/vuforia-extendedtracking.png)<br>
*Unity-Einstellungsfenster*

**Aktivieren der erweiterten Nachverfolgung für ein Ziel**

Die vuforia-Engine transformiert automatisch die Pose eines Ziels, das die erweiterte Nachverfolgung verwendet, in das räumliche-Koordinatensystem hololens. Dadurch können hololens die Überwachung übernehmen und Inhalte integrieren, die in die räumliche Karte der Zielumgebung erweitert werden. Dieser Prozess findet zwischen der vuforia-Engine und Mixed Reality-APIs in Unity statt und erfordert keine Programmierung durch den Entwickler. er wird automatisch verarbeitet.

**Hier sehen Sie, was passiert...**
1. Der Ziel-Tracker von vuforia erkennt das Ziel.
2. Die Ziel Überwachung wird initialisiert.
3. Die Position und die Drehung des Ziels werden analysiert, um eine robuste Positions Schätzung für die zu verwendenden hololens bereitzustellen.
4. Vuforia wandelt die-Pose des Ziels in das hololens Spatial Mapping-Koordinaten Bereich um.
5. Hololens übernimmt die Überwachung, und der vuforia-Tracker wird deaktiviert.

Der Entwickler kann diesen Prozess steuern, um die Steuerung an vuforia zurückzugeben, indem er die erweiterte Nachverfolgung für das targetbehaviour-Verhalten deaktiviert.

**HINWEIS:** Ab vuforia 7,2 ist die erweiterte Nachverfolgung nicht mehr pro Ziel aktiviert. Stattdessen können Entwickler die Geräteüberwachung aktivieren, um eine ähnliche Funktionalität für alle Ziele in der Szene zu aktivieren.


## <a name="see-also"></a>Siehe auch
* [Installieren der Tools](install-the-tools.md)
* [Koordinatensysteme](coordinate-systems.md)
* [Räumliche Abbildung](spatial-mapping.md)
* [Kamera in Unity](camera-in-unity.md)
* [Exportieren und Erstellen einer Unity-Projektmappe für Visual Studio](exporting-and-building-a-unity-visual-studio-solution.md)
* [Vuforia-Dokumentation: Entwickeln für Windows 10 in Unity](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [Vuforia-Dokumentation: Installieren der vuforia Unity-Erweiterung](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [Vuforia-Dokumentation: Arbeiten mit dem hololens-Beispiel in Unity](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [Vuforia-Dokumentation: Erweiterte Nachverfolgung in vuforia](https://library.vuforia.com/articles/Training/Extended-Tracking)
