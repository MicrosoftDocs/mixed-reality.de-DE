---
title: Grundlegendes zu Szenen
description: Einführung in die Funktionen zum verstehen von Szenen für hololens
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: Szenen Verständnis, räumliche Zuordnung, Windows Mixed Reality, Unity
ms.openlocfilehash: 615da20df95f4a435216457e8b9f16bb7d7d069b
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604961"
---
# <a name="scene-understanding"></a>Grundlegendes zu Szenen

Das Verständnis von Szenen bietet Entwicklern gemischter Realität eine strukturierte, allgemeine Darstellung in der Umgebung, die entwickelt wurde, um die Entwicklung für Anwendungen mit hoher Ebene intuitiv zu gestalten. Der Einblick in die Szene ermöglicht das Kombinieren der Leistungsfähigkeit vorhandener gemischter Laufzeiten, wie z. b. der äußerst präzisen weniger strukturierten [räumlichen Zuordnung](spatial-mapping.md) und neuer Ki-gesteuerter Laufzeiten. Durch die Kombination dieser Technologien generiert das Szene Verständnis Darstellungen von 3D-Umgebungen, die denen ähneln, die Sie möglicherweise in Frameworks wie Unity oder Arkit/Arcore verwendet haben. Der Einstiegspunkt der Szene beginnt mit einem Szenen Beobachter, der von Ihrer Anwendung aufgerufen wird, um eine neue Szene zu berechnen. Heute ist die Technologie in der Lage, drei verschiedene, aber verwandte Objektkategorien zu erzeugen: vereinfachte wasserdichte Umgebungs Netze, die die planare Raumstruktur ohne Übersichtlichkeit, Ebenen-Bereiche für die Platzierung, die als "Quads" bezeichnet werden, und eine Momentaufnahme des [räumlichen](spatial-mapping.md) zugriffsnetzes ableiten, das sich auf die von uns angezeigten Quads/wasserdichten Daten richtet.

![Räumliches Mapping-Mesh, Bezeichnung planare Oberflächen, wasserdichtes Mesh](images/SUScenarios.png)

Dieses Dokument soll eine Szenarioübersicht bereitstellen und die Beziehung erläutern, die von der Szene und der räumlichen Zuordnung gemeinsam genutzt wird.

## <a name="developing-with-scene-understanding"></a>Entwickeln mit Szenen Verständnis

Dieser Artikel bietet nur eine Einführung in die Szene, die Laufzeit und Konzepte versteht. Wenn Sie nach einer Dokumentation zur Entwicklung mit Szenen Verständnis suchen, sind Sie möglicherweise an folgendem interessiert:

[Übersicht über das Szene Verständnis von SDK](scene-understanding-SDK.md)

Sie können die Beispiel-App für szeneninformationen von der GitHub-Beispiel Website herunterladen:

[Beispiel für Szenen Verständnis](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

Wenn Sie nicht über ein Gerät verfügen und auf Beispiel Szenen zugreifen möchten, um szeneninformationen auszuprobieren, gibt es im Beispiel Ordner "Asset" Szenen:

[Szenen Einblick in Beispiel Szenen](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a>SDK

Weitere Informationen zur Entwicklung von szeneninformationen oder Details zur Funktionsweise von Szenen Kenntnissen und zur Entwicklung für die Szene finden Sie in der Dokumentation zum [Scene Understanding SDK Overview](scene-understanding-SDK.md) .


### <a name="sample"></a>Beispiel


## <a name="device-support"></a>Unterstützung für Geräte

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Feature</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>Hololens (1. Gen)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>Hololens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Grundlegendes zu Szenen</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="common-usage-scenarios"></a>Allgemeine Verwendungsszenarios

![Abbildungen allgemeiner Verwendungs Szenarien für räumliche Zuordnung: Platzierung, oksion, Physik und Navigation](images/sm-concepts-1000px.png)<br>
*Gängige Verwendungs Szenarien für räumliche Zuordnung: Platzierung, oksion, Physik und Navigation.*

<br>

Viele der Kern Szenarien für Anwendungen, die für die Anwendung geeignet sind (Platzierung, Okklusion, Physik usw.), können sowohl durch räumliche Zuordnung als auch durch Szenen Verständnis adressiert werden. in diesem Abschnitt werden diese Unterschiede hervorgehoben. Ein Hauptunterschied zwischen Szenen Verständnis und räumlicher Zuordnung ist der Nachteil der maximalen Genauigkeit und Latenz bei der Struktur und Einfachheit. Wenn für Ihre Anwendung die möglichen Werte mit niedrigster Latenz und Gitter Dreiecke erforderlich sind, auf die nur Sie zugreifen möchten, verwenden Sie die räumliche Zuordnung direkt. Wenn Sie die Verarbeitung auf höherer Ebene durchführen, können Sie in Erwägung gezogen werden, dass Sie auf das Modell für die Szenen Einsicht umsteigen, da es Ihnen eine Reihe von Funktionen bietet. Beachten Sie auch, dass Sie immer auf die vollständigsten und präziseren räumlichen Zuordnungsdaten zugreifen können, da szeneninformationen eine Momentaufnahme des Netzes für räumliche Zuordnung als Teil ihrer Darstellung bereitstellt.

In den folgenden Abschnitten werden die wichtigsten Szenarios für räumliche Mapping im Kontext des neuen Szenarios zum verstehen von Szenarios erneut besucht.

### <a name="placement"></a>Platzierung

Das Verständnis von Szenen bietet neue Konstrukte, die speziell zur Vereinfachung von Platzierungs Szenarien entwickelt wurden Eine Szene kann primitive als scenequads berechnen, die flache Oberflächen beschreiben, auf denen holograms platziert werden können. Scenequads wurden speziell um die Platzierung entworfen und beschreiben eine 2D-Oberfläche und stellen eine API für die Platzierung auf dieser Oberfläche bereit. Zuvor musste bei Verwendung des Dreiecks Netzes zum Durchführen der Platzierung alle Bereiche des viervieres durchsucht werden, und die Abfüllung/Nachbearbeitung von Löchern wird durchgeführt, um gute Positionen für die Objekt Platzierung zu ermitteln. Dies ist bei Quads nicht immer erforderlich, da die Szene, die die Laufzeit versteht, ableiten kann, welche Bereiche des Quad-Moduls nicht gescannt wurden, und die Bereiche des Quad, die nicht Teil der Oberfläche sind, werden ungültig.

:::row:::
    :::column:::
       ![Scenequads mit deaktiviertem Rückschluss, wobei Platzierungs Bereiche für überprüfte Bereiche erfasst werden.](images/SUQuads.png)<br>
       **Bild #1** -scenequads mit deaktiviertem Rückschluss, wobei Platzierungs Bereiche für überprüfte Bereiche erfasst werden.
    :::column-end:::
        :::column:::
       ![Quads mit aktiviertem Inferenz ist die Platzierung nicht mehr auf überprüfte Bereiche beschränkt.](images/SUWatertight.png)<br>
        **Image #2** -Quads mit aktiviertem Typrückschluss ist die Platzierung nicht mehr auf überprüfte Bereiche beschränkt.
    :::column-end:::
:::row-end:::

<br>


Wenn Ihre Anwendung die Möglichkeit hat, 2D-oder 3D-Hologramme in starre Strukturen Ihrer Umgebung zu platzieren, ist die Einfachheit und Vereinfachung von scenequads für die Platzierung besser, wenn diese Informationen aus dem [räumlichen Mapping](spatial-mapping.md) -Mesh berechnet werden. Weitere Informationen zu diesem Thema finden Sie in der [Scene Understanding SDK-Referenz](scene-understanding-SDK.md) .

**Hinweis** Für Legacy-Platzierungs Code, der vom Mesh für räumliche Zuordnungen abhängt, kann das räumliche Zuordnungen-Mesh zusammen mit scenequads berechnet werden, indem die enableworldmesh-Einstellung festgelegt wird. Wenn die API-Understanding-API die Latenz Anforderungen Ihrer Anwendung nicht erfüllt, wird empfohlen, weiterhin die [räumliche Mapping-API](spatial-mapping.md#placement)zu verwenden.

### <a name="occlusion"></a>Okklusion

Die [Okklusion für räumliche](spatial-mapping.md#occlusion) Zuordnungen ist die niedrigste Methode zum Erfassen des Echt Zeit Zustands der Umgebung. Obwohl dies nützlich sein kann, um die Okklusion in sehr dynamischen Szenen bereitzustellen, empfiehlt es sich unter Umständen, das Verständnis der Szene in der Szene aus verschiedenen Gründen zu verstehen. Wenn Sie das durch Szene Verständnis generierte räumliche zuordnungsmesh verwenden, können Sie Daten aus der räumlichen Zuordnung anfordern, die nicht im lokalen Cache gespeichert werden und daher nicht über die perception-APIs zur Verfügung stehen. Die Verwendung der räumlichen Zuordnung für die Okklusion neben wasserdichten Netzen stellt zusätzlichen Wert bereit, insbesondere den Abschluss der nicht gescannten Raumstruktur.

Wenn Ihre Anforderungen die zunehmende Latenz von Szenen Verständnis tolerieren können, sollten Anwendungsentwickler die Verwendung der Szene verstehen, die das Wasser enge Mesh versteht, und vermutlich das räumliche Mapping-Mesh in gemeinsamen mit planaren Darstellungen. Dies wäre ein "Beste aus beiden Welten"-Szenario, in dem die vereinfachte wasserdichte mit einer feineren nicht planaren Geometrie verheiratet ist, die die realistischsten Karten für die Karten Zuordnung bereitstellt.

### <a name="physics"></a>Mikro

Szenen Verständnis generiert Wasser enge Netze, die Leerzeichen mit Semantik zerlegen, insbesondere, um viele Einschränkungen der Physik zu berücksichtigen, die von den Netzen räumlicher Zuordnung auferlegt werden. Wasserdichte Strukturen sorgen für eine einfachere Generierung von physikalischer Ray-Umwandlungen, und die semantische Zerlegung ermöglicht eine einfachere Generierung von Navigations Netzen für die Navigation in einem Wie im Abschnitt zu [Okklusion](#occlusion)beschrieben, wird durch das Erstellen einer Szene mit enablesceneobjectmeshes und enableworldmesh das am meisten physisch umfassende Mesh ermöglicht. Die Eigenschaft "Watertight" des Umgebungs Netzes verhindert, dass Treffer Tests auf Oberflächen gelangen, und die Mesh-Daten stellen sicher, dass die Physik mit allen Objekten in der Szene und nicht nur mit der Raumstruktur interagiert.

### <a name="navigation"></a>Navigation

Planare Netzen, die durch die semantische Klasse zerlegt werden, sind ideale Konstrukte für die Navigation und die Pfad Planung. Dadurch werden viele der Probleme, die in der Übersicht über die [Navigation über räumliche](spatial-mapping.md#navigation) Die scenemesh-Objekte, die in der Szene berechnet werden, sind bereits aus dem Surface-Typ zusammengesetzt. Dadurch wird sichergestellt, dass die NAV-Mesh-Generierung auf Oberflächen beschränkt ist, auf die Aufgrund der Einfachheit der Bodenstruktur ist die dynamische NAV-Mesh-Generierung in 3D--Engines wie Unity abhängig von den Echtzeitanforderungen erreichbar.

Das Erstellen von exakten NAV-Meshes erfordert zurzeit noch die Nachbearbeitung. Anwendungen müssen nach wie vor nach der Bearbeitung projizieren, um sicherzustellen, dass die Navigation nicht durch Übersichtlichkeit/Tabellen verläuft usw... Die präzisere Methode hierfür ist das Projizieren der World Mesh-Daten, die bereitgestellt werden, wenn die Szene mit dem enableworldmesh-Flag berechnet wird.

### <a name="visualization"></a>Visualisierung

Obwohl die Visualisierung für die [räumliche Zuordnung](spatial-mapping.md#visualization) für Echtzeitfeedback der Umgebung verwendet werden kann, gibt es viele Szenarios, in denen die Einfachheit von planaren und wasserdichten Objekten mehr Leistung oder visuelle Qualität bietet. Schattenprojektions-und Erdungs Techniken, die mithilfe räumlicher Zuordnung beschrieben werden, sind möglicherweise ansprechender, wenn Sie auf den planaren Oberflächen projiziert werden, die von Quads oder dem planaren wasserdichten Mesh Dies gilt insbesondere für Umgebungen/Szenarios, in denen eine gründliche vorab Überprüfung aufgrund der Tatsache, dass die Szene abgeleitet wird, nicht optimal ist, und durch vollständige Umgebungen und planare Annahmen werden Artefakte minimiert.

Darüber hinaus wird die Gesamtanzahl der von der räumlichen Zuordnung zurückgegebenen Oberflächen durch den internen räumlichen Cache beschränkt, während die Version des räumlichen zuordnungsnetzes der räumlichen Zuordnung auf räumliche Zuordnungsdaten zugreifen kann, die nicht zwischengespeichert werden. Aus diesem Grund ist das Verständnis der Szene besser für die Erfassung von Netz Darstellungen für größere Bereiche (z. b. mehr als einen einzelnen Raum) für die Visualisierung oder weitere Gitter Verarbeitung geeignet. Das mit enableworldmesh zurückgegebene World Mesh verfügt über eine konsistente Detailebene, die bei gerenderter Darstellung als Wireframe eine ansprechendere Visualisierung ergeben kann.

### <a name="see-also"></a>Weitere Informationen

* [Scene Understanding SDK](scene-understanding-SDK.md)
* [Räumliche Abbildung](spatial-mapping.md)
