---
title: HoloLens Research-Modus
description: Research-Modus in HoloLens verwenden, kann eine Anwendung Key Gerät Sensor Streams (Tiefe, Umgebung, die nachverfolgung und IR-Reflexionsvermögen) zugreifen.
author: davidgedye
ms.author: dgedye
ms.date: 05/03/2018
ms.topic: article
keywords: Research-Modus, cv, rs4, maschinelles sehen, Forschung, HoloLens
ms.openlocfilehash: 5feda021bd6a1a90fd98c751b1cea768eed980af
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593229"
---
# <a name="hololens-research-mode"></a>HoloLens Research-Modus

> [!NOTE]
> Dieses Feature wurde hinzugefügt, als Teil der [Windows 10 April 2018 Update](release-notes-april-2018.md) für HoloLens, und ist in früheren Versionen nicht verfügbar.

Research-Modus ist eine neue Funktion von HoloLens, die Anwendung den Zugriff auf die wichtigsten Sensoren auf dem Gerät bereitstellt. Dazu gehören:
- Die vier Umgebung, die nachverfolgung von Kameras, die vom System verwendet wird, zum Erstellen der Zuordnung und Head überwachen.
- Zwei Versionen der Tiefe Kameradaten – eine für hoher Frequenz (30 FPS) in der Nähe-Depth-Erkennung, häufig verwendet, Nachverfolgen von hand und die andere für die untere Frequenz (1 f/s) weit-Depth ermitteln, an, die derzeit von räumliche Zuordnung verwendet,
- Zwei Versionen einer IR-Reflexionsvermögen-Stream, der durch die HoloLens verwendet werden, um Tiefe, aber die wertvollen selbständige zu berechnen, wie diese Images aus dem HoloLens beleuchtete und angemessen Umgebungslicht betroffen sind.

![Research-Modus-app-screenshot](images/sensor-stream-viewer.jpg)<br>
*Einer mixed Reality-Erfassung einer testanwendung, in dem die acht Sensor-Datenströme, die im Modus für Research verfügbar angezeigt.*

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Feature</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td> Research-Modus</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

## <a name="before-using-research-mode"></a>Vor der Verwendung von Research-Modus

Research-Modus ist auch mit dem Namen: Es ist vorgesehen, academic und gewerbeprozessen Forschern, testen neue Ideen in die Felder der maschinelles sehen und Robotik.  Research-Modus ist nicht für Anwendungen vorgesehen, die in einem Unternehmen bereitgestellt oder in der Microsoft Store zur Verfügung gestellt werden. Der Grund dafür ist, dass Research Modus die Sicherheit Ihres Geräts verringert und wesentlich mehr Akkuleistung als Normalbetrieb belegt. Microsoft ist nicht verpflichtet sich somit, diesen Modus für alle zukünftigen Geräte unterstützen. Daher empfehlen wir, dass Sie zum Entwickeln und testen neue Ideen verwenden; Allerdings werden Sie nicht häufig Anwendungen bereitstellen, die Research-Modus verwenden oder alle Assurance, die sie weiterhin funktionieren, auf zukünftige Hardware.

## <a name="enabling-research-mode"></a>Research-Modus aktivieren

Research-Modus ist eine untergeordnete des Entwicklermodus. Sie müssen zunächst Entwicklermodus in der Einstellungs-app zu aktivieren (**Einstellungen > Update und Sicherheit > für Entwickler**):

1. Legen Sie "Verwenden der Funktionen für Entwickler" auf **auf**
2. Legen Sie auf "Enable-Geräteportal" **auf**

Klicken Sie dann über einen Webbrowser, der mit dem gleichen Wi-Fi-Netzwerk als Ihre HoloLens, verbunden ist, navigieren Sie auf die IP-Adresse Ihrer HoloLens (abgerufenes **Einstellungen > Netzwerk und Internet > Wi-Fi > Hardwareeigenschaften**). Dies ist die [Device Portal](using-the-windows-device-portal.md), und eine Seite "Research-Modus" finden Sie im Abschnitt "System" des Portals:

![Überprüfen Sie die Registerkarte "Standortmodus" des Portals für HoloLens-Gerät](images/ResearchModeDevPortal.png)<br>
*Research-Modus im Portal HoloLens-Gerät*

Nach der Auswahl **zulassen des Zugriffs auf Sensor Streams**, Sie benötigen, HoloLens neu zu starten. Dies ist im Portal klicken Sie unter "Power" am oberen Rand der Seite Gerät möglich.

Nachdem Ihr Gerät neu gestartet wurde, sollte Anwendungen, die über das Device Portal geladen wurden Research Modus Streams zugreifen können.

## <a name="using-sensor-data-in-your-apps"></a>Mithilfe von Sensordaten in Ihren apps

Anwendungen können Daten von triebwerksensoren Stream zugreifen, indem öffnen [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) Streams auf genau die gleiche Weise Zugriff auf den Foto/Video-Kamera-Datenstrom. 

Außerdem stehen alle APIs, die für die Entwicklung für HoloLens arbeiten im Research-Modus zur Verfügung. Insbesondere kann die Anwendung wissen genau, in dem HoloLens im 6DoF Raum zur Erfassungszeit jeden Sensor-Frame ist.

Beispielanwendungen, die zeigt, wie Sie die verschiedenen Research Modus Streams zugreifen, wie Sie die systeminterne Funktionen und Extrinsics verwenden und das Aufzeichnen von Streams finden Sie in der [HoloLensForCV-GitHub-Repository](https://github.com/Microsoft/HoloLensForCV).

## <a name="known-issues"></a>Bekannte Probleme

Finden Sie unter den [problemverfolgung](https://github.com/Microsoft/HololensForCV/issues) im HoloLensForCV-Repository.

## <a name="see-also"></a>Siehe auch

* [Microsoft Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [HoloLensForCV-GitHub-Repository](https://github.com/Microsoft/HoloLensForCV)
* [Verwenden die Windows Device Portal](using-the-windows-device-portal.md)
