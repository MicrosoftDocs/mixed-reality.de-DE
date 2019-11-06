---
title: Audioinhalte in gemischter Realität
description: Audioinhalte in gemischter Realität können das Vertrauen von Benutzeroberflächen Interaktionen erhöhen und Benutzer in der Benutzeroberfläche eintauchen.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: räumlicher Sound, Umschließungs Sound, 3D--Audio, 3D--Ton, räumliche Audiodaten
ms.openlocfilehash: 1930017903439aee3ac53b6c4be344fdc44c356f
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641108"
---
# <a name="audio-in-mixed-reality"></a>Audioinhalte in gemischter Realität
Audiodaten sind ein wesentlicher Bestandteil des Entwurfs und der Produktivität in gemischter Realität und können folgende Aktionen ausführen:
* Verbessern der Benutzer Zuverlässigkeit in Gesten-und sprachbasierten Interaktionen
* Benutzer zu den nächsten Schritten führen
* Effektives kombinieren virtueller Objekte mit der realen Welt

Die Head-Nachverfolgung mit niedriger Latenz von Mixed Reality-Headsets, einschließlich hololens, ermöglicht die Verwendung der auf der HRTF basierenden Spatialisierung mit hoher Qualität. Das spatialisieren von Audiodaten in der Anwendung kann:
* Aufmerksamkeit von visuellen Elementen auf Aufrufe
* Helfen Sie Benutzern dabei, das Bewusstsein für ihre reale Umgebung zu wahren.

Durch das Hinzufügen von Akustik werden Hologramme tiefer mit der gemischten Welt verbunden, und es können Hinweise zur Umgebung und zum Objektzustand bereitgestellt werden.

Ausführlichere Beispiele für den Entwurf mithilfe von Audio finden Sie unter [Sound Design](spatial-sound-design.md).

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Feature</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Spatialisierung</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Beschleunigung der spatialisierungs Hardware</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="using-sounds-in-mixed-reality"></a>Verwenden von Sounds in gemischter Realität
Die [Verwendung von Sounds in gemischter Realität](spatial-sound-design.md) kann einen anderen Ansatz als in Anwendungen mit Finger Eingaben und Tastatur und Maus erfordern. Wichtige Entscheidungen zum Entwurf von Entscheidungen umfassen, welche Sounds räumlich und welche Interaktionen mit sonify zu tun haben. Diese Entscheidungen können starke Auswirkungen auf die Benutzer Zuverlässigkeit, Produktivität und Lernkurve haben.

### <a name="case-studies"></a>Fallstudien
Mit holotour werden Benutzer praktisch zu touristischen und historischen Websites auf der ganzen Welt. Die folgende Fallstudie beschreibt den Sound Entwurf für holotour: [Sound Design für holotour](case-study-spatial-sound-design-for-holotour.md). Ein spezielles Mikrofon und renderingsetup wurden zum Erfassen der Themenbereiche verwendet.

Roboraid ist ein Hochenergie geschütztes Gerät für hololens. In der folgenden Fallstudie werden die Entwurfsentscheidungen beschrieben, mit denen sichergestellt wird, dass räumliche Audiodaten in vollem Umfang dramatisch umgesetzt werden: [Sound Design für roboraid](case-study-using-spatial-sound-in-roboraid.md).

## <a name="spatialization"></a>Spatialisierung
Spatialization ist die direktionale Komponente räumlicher Audiodaten. Bei Verwendung eines 7,1-Home-Theater Setups ist die Spatialisierung so einfach wie das Schwenken zwischen Lautsprecher. Mit den Kopfhörern in gemischter Realität ist es jedoch von entscheidender Bedeutung, eine auf HRTF basierende Technologie für Genauigkeit und Komfort zu verwenden. Windows bietet eine auf HRTF basierende Spatialisierung. diese Unterstützung ist auf hololens 2 Hardware beschleunigt.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a>Sollte ich räumlich spatialisieren?
Viele Sounds in Mixed Reality-Anwendungen profitieren von der Spatialisierung, bei der ein Sound aus dem Kopf des Listener hervorgeht und auf der ganzen Welt platziert wird. Unter " [räumlicher Sound Entwurf](spatial-sound-design.md) " finden Sie Vorschläge zu den effektivsten Verwendungsmöglichkeiten der Spatialisierung in Ihrer Anwendung.

### <a name="spatializer-personalization"></a>Spatializer-Personalisierung
HRTFs bearbeitet die Ebenen-und Phasenunterschiede zwischen den Ohren im Frequenzspektrum. Sie basieren auf physischen Modellen und Messungen von Menschen Kopf-, Rumpf-und Ohrformen (pinnae). Unsere Gehirne reagieren auf diese Unterschiede, um einen Eindruck von der Richtung in Sound zu machen. 

Jede Person verfügt über eine eindeutige Ohrform, Kopfgröße und Position, sodass Sie die besten HRTFs-Funktionen sind, die Ihnen entsprechen. Hololens erhöht die räumungsgenauigkeit, indem der IPD (Inter-pupilary Distance) aus den Headset-anzeigen verwendet wird, um den HRTFs für die Kopfgröße anzupassen.

### <a name="spatializer-platform-support"></a>Unterstützung für spatializer-Plattform
Windows bietet mithilfe der [ispatialaudioclient-API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)eine spatialization, einschließlich HRTFs. Diese API macht die Hardwarebeschleunigung von hololens 2 HRTF für Anwendungen verfügbar.

### <a name="spatializer-middleware-support"></a>Unterstützung für spatializer-Middleware
Die Unterstützung für Windows ' HRTFs ist für einige Drittanbieter-AUDIOMODULE verfügbar:
* Ein Plug-in für die [Unity-Audioengine](spatial-sound-in-unity.md) Ruft den HRTF xapo
* Ein [wwise Audio Engine-Plug-](https://www.audiokinetic.com/products/plug-ins/msspatial/) in Ruft die ispatialaudioclient-API auf.

## <a name="acoustics"></a>Akustische
Räumliche Audiodaten können mehr als die Richtung aufweisen. Andere Dimensionen, einschließlich Okklusion, Behinderung, Reverb, portalling und Quell Modellierung, werden kollektiv als "Akustik" bezeichnet. Ohne Akustik fehlt bei spatialisierten Sounds eine nicht wahrgenommene Entfernung.

Die Akustik-Behandlung kann von einfach bis sehr komplex reichen. Wenn Sie einen einfachen Reverb verwenden, wie z. b., der von einer beliebigen Audioengine unterstützt wird, können Sie spatialisierte Sounds in die Umgebung verschieben, die den Listener umgibt. Umfangreichere und überzeugendere Reinigungsmöglichkeiten sind über Akustiksysteme verfügbar, wie z. b. die [Projekt Akustik](https://aka.ms/acoustics). Die Projekt Akustik kann die Auswirkung von Wänden, Türen und anderen Szenen Geometrie in einem Sound modellieren und ist eine effektive Option für Fälle, in denen die relevante Szene Geometrie zur Entwicklungszeit bekannt ist.

