---
title: Audioinhalte in gemischter Realität
description: Audioinhalte in gemischter Realität können das Vertrauen von Benutzeroberflächen Interaktionen erhöhen und Benutzer in der Benutzeroberfläche eintauchen.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: räumlicher Sound, Umschließungs Sound, 3D--Audio, 3D--Ton, räumliche Audiodaten
ms.openlocfilehash: b939433daf80a95a11bc0e1ac2ffd75dfe0cf299
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181980"
---
# <a name="audio-in-mixed-reality"></a>Audioinhalte in gemischter Realität
Das Audiomaterial ist ein wesentlicher Bestandteil von Design und Produktivität in gemischter Realität. Sound kann:
* Erhöhen Sie das Vertrauen von Benutzern in Gesten-und sprach Interaktionen.
* Leiten Sie die Benutzer zu den nächsten Schritten.
* Kombinieren Sie virtuelle Objekte effektiv mit der realen Welt.

Die Head-Nachverfolgung mit niedriger Latenz von Mixed Reality-Headsets (einschließlich hololens) unterstützt die auf hoher Qualität basierende Spatialisierung. Sie können Audiodaten in Ihrer Anwendung für Folgendes spatialisieren:
* Beachten Sie, dass visuelle Elemente aufgerufen werden.
* Helfen Sie Benutzern dabei, das Bewusstsein ihrer realen Umgebung zu wahren.

Die Akustik verbindet Hologramme tiefer mit der Mixed-Reality-Welt. Es stellt Hinweise zur Umgebung und zum Objektzustand bereit.

Weitere Informationen finden Sie [unter ausführliche Entwurfs Beispiele für die Verwendung von Audiodateien](spatial-sound-design.md).

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
        <td><a href="hololens-hardware-details.md"><strong>Hololens (erste Generation)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Erzeugen von räumlicher Tiefe</td>
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

## <a name="use-of-sounds-in-mixed-reality"></a>Verwendung von Sounds in gemischter Realität
Die [Verwendung von Sounds in gemischter Realität](spatial-sound-design.md) erfordert einen anderen Ansatz als in der Touchscreen-und Tastatur-und Maus Anwendungen. Wichtige Entscheidungen zum Entwurf von Entscheidungen umfassen, welche Sounds räumlich und welche Interaktionen mit sonify zu tun haben. Diese Entscheidungen wirken sich stark auf Benutzer vertrauen, Produktivität und Lernkurve aus.

### <a name="case-studies"></a>Fallstudien
Mit holotour werden Benutzer praktisch zu touristischen und historischen Websites auf der ganzen Welt. Weitere Informationen finden Sie in der Fallstudie [Sound Design for holotour](case-study-spatial-sound-design-for-holotour.md) . Ein spezielles Mikrofon und renderingsetup wurden zum Erfassen der Themenbereiche verwendet.

Roboraid ist ein Hochenergie geschütztes Gerät für hololens. In der Fallstudie [Sound Design for roboraid](case-study-using-spatial-sound-in-roboraid.md) werden die Entwurfs Optionen beschrieben, die getroffen wurden, um sicherzustellen, dass räumliche Audiodaten in vollem Umfang dramatisch wirksam werden.

## <a name="spatialization"></a>Erzeugen von räumlicher Tiefe
Spatialization ist die direktionale Komponente räumlicher Audiodaten. Bei einem 7,1-Home-Theater-Setup ist die Spatialisierung so einfach wie das Schwenken zwischen Lautsprechern. Doch für Kopfhörer in gemischter Realität ist es von entscheidender Bedeutung, eine auf HRTF basierende Technologie für Genauigkeit und Komfort zu verwenden. Windows bietet eine auf HRTF basierende Spatialisierung. diese Unterstützung ist auf hololens 2 Hardware beschleunigt.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a>Sollte ich räumlich spatialisieren?
Die Spatialisierung kann viele Sounds in gemischten Reality-Anwendungen verbessern. Die Spatialisierung nimmt einen Sound aus dem Kopf des Listener und platziert Sie in der Welt. Vorschläge zur effektiven Verwendung von spatialization in Ihrer Anwendung finden Sie unter [Spatial Sound Design](spatial-sound-design.md).

### <a name="spatializer-personalization"></a>Spatializer-Personalisierung
HRTFs bearbeitet die Ebenen-und Phasenunterschiede zwischen den Ohren im Frequenzspektrum. Sie basieren auf physischen Modellen und Messungen von Menschen Kopf-, Rumpf-und Ohrformen (pinnae). Unsere Gehirne reagieren auf diese Unterschiede, um die wahrgenommene Richtung in Sound bereitzustellen.

Jede Person verfügt über eine eindeutige Ohrform, Kopfgröße und Position. Das beste ist also die beste Lösung für Sie. Um die räumungsgenauigkeit zu erhöhen, verwendet hololens ihren Inter-pupilary Distance (IPD) aus den Headset-anzeigen, um den HRTFs für die Kopfgröße anzupassen.

### <a name="spatializer-platform-support"></a>Unterstützung für spatializer-Plattform
Windows bietet mithilfe der [ispatialaudioclient-API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)eine spatialization, einschließlich HRTFs. Diese API macht die Hardwarebeschleunigung von hololens 2 HRTF für Anwendungen verfügbar.

### <a name="spatializer-middleware-support"></a>Unterstützung für spatializer-Middleware
Die Unterstützung für Windows ' HRTFs ist für die folgenden Drittanbieter-AUDIOMODULE verfügbar.
* Ein [Plug-in für Unity-Audiodateien](spatial-sound-in-unity.md)
* Ein [wwise-Audiomodul-Plug-](https://www.audiokinetic.com/products/plug-ins/msspatial/) in

## <a name="acoustics"></a>Akustische
Räumliche Audiodaten sind ungefähr mehr als die Richtung. Weitere Dimensionen sind Okklusion, Behinderung, Reverb, portalling und Quell Modellierung. Gemeinsam werden diese Dimensionen als *Akustik*bezeichnet. Ohne Akustik fehlt bei spatialisierten Sounds eine nicht wahrgenommene Entfernung.

Die Akustik ist von einfach bis sehr komplex. Sie können einen einfachen Reverb verwenden, der von jedem Audiomodul unterstützt wird, um spatialisierte Sounds in die Umgebung des Listener zu überführen. Akustiksysteme wie z. b. die [Projekt Akustik](https://aka.ms/acoustics) bieten umfangreichere und überzeugende Akustik Behandlungen. Die Projekt Akustik kann die Auswirkung von Wänden, Türen und anderen Szenen Geometrie in einem Sound modellieren. Es ist eine effektive Option in Fällen, in denen die relevante Szene Geometrie zur Entwicklungszeit bekannt ist.

## <a name="next-steps"></a>Nächste Schritte
- [Raumklang in Unity](spatial-sound-in-unity.md)
- [Verwenden von Sound in Anwendungen mit gemischter Realität](spatial-sound-design.md)
