---
title: Szenen Verständnis
description: Einführung in die Funktionen zum verstehen von Szenen für hololens
author: szymons
ms.author: szymons
ms.date: 07/08/19
ms.topic: article
keywords: Szenen Verständnis, räumliche Zuordnung, Windows Mixed Reality, Unity
ms.openlocfilehash: fc77126958c653cac2d82f02cceeed9a29bffdf4
ms.sourcegitcommit: c4c293971bb3205a82121bbfb40d1ac52b5cb38e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/10/2019
ms.locfileid: "68941217"
---
# <a name="scene-understanding"></a>Szenen Verständnis

Das Verständnis von Szenen bietet Entwicklern gemischter Realität eine strukturierte, allgemeine Darstellung in der Umgebung, die entwickelt wurde, um die Entwicklung für Anwendungen mit hoher Ebene intuitiv zu gestalten. Das Verständnis der Szene führt dies durch Kombinieren der Leistungsfähigkeit vorhandener gemischter Laufzeiten, wie z. b. der äußerst präzisen weniger strukturierten [räumlichen Zuordnung](spatial-mapping.md) und neuer Ki-gesteuerter Laufzeiten. Durch die Kombination dieser Technologien generiert das Szene Verständnis Darstellungen von 3D--Umgebungen, die denen ähneln, die Sie möglicherweise in Frameworks wie Unity oder Arkit/Arcore verwendet haben. Die Szene, die EntryPoint versteht, beginnt mit einem Szenen Beobachter, der von Ihrer Anwendung aufgerufen wird, um eine neue Szene zu berechnen. Heutzutage ist die Technologie in der Lage, drei verschiedene, aber verwandte Objektkategorien zu erzeugen: vereinfachte wasserdichte Umgebungs Netze, die die planare Raumstruktur ohne Übersichtlichkeit ableiten, Ebenen-Bereiche für die Platzierung, die wir als Quads bezeichnen, und eine Momentaufnahme des [ das räumliche Mapping](spatial-mapping.md) -Mesh, das sich auf die von uns angezeigten Quads/wasserdichten Daten anpasst.

![Räumliches Mapping-Mesh, Bezeichnung planare Oberflächen, wasserdichtes Mesh](images/SUScenarios.png)

Dieses Dokument soll eine Szenarioübersicht bereitstellen und die Beziehung erläutern, die von der Szene und der räumlichen Zuordnung gemeinsam genutzt wird. Ausführliche Informationen zur Funktionsweise von Szenen Kenntnissen und zur Entwicklung dafür finden Sie in der Dokumentation zum Thema "Scene Understanding [SDK Overview](scene-understanding-SDK.md) ".

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Feature</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1. Generation)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> Szenen Verständnis</td><td style="text-align: center;">️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

## <a name="common-usage-scenarios"></a>Allgemeine Verwendungsszenarien

![Abbildungen allgemeiner Verwendungs Szenarien für räumliche Zuordnung: Platzierung, Okklusion, Physik und Navigation](images/sm-concepts-1000px.png)

Viele der Kern Szenarien für Anwendungen, die in Umgebungen unterstützt werden (Platzierung, Okklusion, Physik usw.), können sowohl durch räumliche Zuordnung als auch durch Szenen Verständnis adressiert werden. in diesem Abschnitt werden diese Unterschiede hervorgehoben. Ein Hauptunterschied zwischen Szenen Verständnis und räumlicher Zuordnung ist der Nachteil der maximalen Genauigkeit und Latenz bei der Struktur und Einfachheit. Wenn für Ihre Anwendung die geringste Latenzzeit erforderlich ist und Gitter Dreiecke erforderlich sind, sollten Sie direkt auf die räumliche Zuordnung zugreifen. Wenn Sie jedoch eine höhere Verarbeitungsleistung durchführen, können Sie in Erwägung gezogen werden, dass Sie in das Szene Verständnis Modell wechseln. Sie sollten eine Reihe von Funktionen bereitstellen. Beachten Sie außerdem, dass Sie immer auf die vollständigsten und präziseren räumlichen Zuordnungsdaten zugreifen können, weil szeneninformationen das räumliche zugriffsmesh als Teil der Darstellung bereitstellt.

 In den folgenden Abschnitten werden die wichtigsten Szenarios für räumliche Mapping im Kontext des neuen Szenarios zum verstehen von Szenarios erneut besucht.

### <a name="placement"></a>Platzierung

Das Verständnis von Szenen bietet neue Konstrukte, die speziell zur Vereinfachung von Platzierungs Szenarien entwickelt wurden Eine Szene kann primitive als scenequads berechnen, die flache Oberflächen beschreiben, auf denen holograms platziert werden können. Scenequads wurden speziell um die Platzierung entworfen und beschreiben eine 2D-Oberfläche und stellen eine API für die Platzierung auf dieser Oberfläche bereit. Zuvor musste bei Verwendung des Dreiecks Netzes zum Durchführen der Platzierung alle Bereiche des viervieres durchsucht werden, und die Abfüllung/Nachbearbeitung von Löchern wird durchgeführt, um gute Positionen für die Objekt Platzierung zu ermitteln. Dies ist bei Quads nicht immer erforderlich, da die Szene, die die Laufzeit versteht, ableiten kann, welche Bereiche des Quad-Moduls nicht gescannt wurden, und die Bereiche des Quad, die nicht Teil der Oberfläche sind, werden ungültig.

![Scenequads mit deaktiviertem Rückschluss, wobei Platzierungs Bereiche für überprüfte Bereiche erfasst werden.](images/SUQuads.png)
##### <a name="1-scenequads-with-inference-disabled-capturing-placement-areas-for-scanned-regions"></a>[1] "scenequads mit deaktiviertem Rückschluss, das Erfassen von Platzierungs Bereichen für gescannte Bereiche."

![Quads mit aktiviertem Inferenz ist die Platzierung nicht mehr auf überprüfte Bereiche beschränkt.](images/SUWatertight.png)
##### <a name="2-quads-with-inference-enabled-placement-is-no-longer-limited-to-scanned-areas"></a>[2] "Quads, bei aktiviertem Inferenz, ist die Platzierung nicht mehr auf überprüfte Bereiche beschränkt."

Wenn Ihre Anwendung in starren Strukturen Ihrer Umgebung 2D-oder 3D-Hologramme platzieren soll, ist die Einfachheit und Vereinfachung der scenequads für die Platzierung dem Berechnen dieser Informationen aus dem Oberflächen Netz vorzuziehen. Weitere Informationen zu diesem Thema finden Sie in der [Scene Understanding SDK-Referenz](scene-understanding-SDK.md) .

**Hinweis** Für Legacy Code, der vom Oberflächen Mesh abhängig ist, kann eine Szene berechnet werden, die eine räumliche Zuordnungsausgabe zusammen mit scenequads enthält. Dadurch wird sichergestellt, dass alle Legacy Anforderungen für die Platzierung beibehalten werden können. Wenn die Daten in der Szene verstanden werden, die die Latenz Anforderungen Ihrer Anwendung nicht erfüllen, wird empfohlen, die hier dokumentierten APIs für die räumliche Zuordnung weiterhin zu verwenden: [Platzierung räumlicher Zuordnung](spatial-mapping.md#placement)

### <a name="occlusion"></a>Okklusion

Die [Okklusion für räumliche](spatial-mapping.md#occlusion) Zuordnungen ist die niedrigste Methode zum Erfassen des Echt Zeit Zustands der Umgebung. Obwohl dies nützlich sein kann, um die Okklusion in sehr dynamischen Szenen bereitzustellen, empfiehlt es sich unter Umständen, das Verständnis der Szene in der Szene aus verschiedenen Gründen zu verstehen. Wenn Sie das durch Szene Verständnis generierte räumliche zuordnungsmesh verwenden, können Sie Daten aus der räumlichen Zuordnung anfordern, die nicht im lokalen Cache gespeichert und daher nicht über die perception-APIs verfügbar sind. Die Verwendung der räumlichen Zuordnung für die Okklusion neben wasserdichten Netzen stellt zusätzlichen Wert bereit, insbesondere den Abschluss der nicht gescannten Raumstruktur.

Wenn Ihre Anforderungen die zunehmende Latenz von Szenen Verständnis tolerieren können, sollten Anwendungsentwickler die Verwendung der Szene verstehen, die das Wasser enge Mesh versteht, und vermutlich das räumliche Mapping-Mesh in gemeinsamen mit planaren Darstellungen. Dies wäre eine "Beste aus beiden Welten", bei denen die vereinfachte wasserdichte mit einer feineren nicht planaren Geometrie verheiratet ist, die die realistischsten Karten für die Karten Zuordnung bereitstellt.

### <a name="physics"></a>Mikro

Das Verständnis von Szenen generiert Wasser enge Netze, die Speicherplatz mit Semantik aufteilen, um viele Einschränkungen der Physik zu berücksichtigen, die von Oberflächen Netzen auferlegt werden. Wasserdichte Strukturen sorgen für eine einfachere Generierung von physikalischer Ray-Umwandlungen, und die semantische Zerlegung ermöglicht eine einfachere Generierung von Navigations Netzen für die Navigation in einem Wie im Abschnitt zur [Okklusion](#occlusion) beschrieben, wird durch das erstellen einer Szene mit „EnableSceneObjectMeshes“ und „EnableWorldMesh“ das Gitter erstellt, bei dem die Physik nahezu ausgereift ist. Die Eigenschaft "Watertight" des Umgebungs Netzes verhindert, dass Treffer Tests auf Oberflächen gelangen, und die Mesh-Daten stellen sicher, dass die Physik mit allen Objekten in der Szene und nicht nur mit der Raumstruktur interagiert.

### <a name="navigation"></a>Navigation

Planare Netzen, die durch die semantische Klasse zerlegt werden, sind ideale Konstrukte für die Navigation und die Pfad Planung. Dadurch werden viele der Probleme, die in der Übersicht über die [Navigation über räumliche](spatial-mapping.md#navigation) Die scenemesh-Objekte, die in der Szene berechnet werden, sind bereits aus dem Surface-Typ zusammengesetzt. Dadurch wird sichergestellt, dass die NAV-Mesh-Generierung auf Oberflächen beschränkt ist, auf die Aufgrund der Einfachheit der Bodenstruktur ist die dynamische NAV-Mesh-Generierung in 3D--Engines wie Unity abhängig von den Echtzeitanforderungen erreichbar.

Das Erstellen von exakten NAV-Meshes erfordert zurzeit noch die Nachbearbeitung. Anwendungen müssen nach wie vor nach der Bearbeitung projizieren, um sicherzustellen, dass die Navigation nicht durch Übersichtlichkeit/Tabellen verläuft usw... Die präzisere Methode hierfür ist das Projizieren der World Mesh-Daten, die bereitgestellt werden, wenn die Szene mit dem enableworldmesh-Flag berechnet wird.

### <a name="visualization"></a>Visualisierung

Obwohl die Visualisierung für die [räumliche Zuordnung](spatial-mapping.md#visualization) für Echtzeitfeedback der Umgebung verwendet werden kann, gibt es viele Szenarios, in denen die Einfachheit von planaren und wasserdichten Objekten mehr Leistung oder visuelle Qualität bietet. Schattenprojektions-und Erdungs Techniken, die mithilfe räumlicher Zuordnung beschrieben werden, sind möglicherweise ansprechender, wenn Sie auf den planaren Oberflächen projiziert werden, die von Quads oder dem planaren wasserdichten Mesh Dies gilt insbesondere für Umgebungen/Szenarios, in denen die vorab Überprüfung aufgrund der Tatsache, dass die Szene nicht durchgeführt wird, nicht optimal ist

Darüber hinaus wird die Gesamtanzahl der von der räumlichen Zuordnung zurückgegebenen Oberflächen durch den internen räumlichen Cache beschränkt, während die Version des räumlichen zuordnungsnetzes der räumlichen Zuordnung auf räumliche Zuordnungsdaten zugreifen kann, die nicht zwischengespeichert werden. Aus diesem Grund ist das Verständnis der Szene besser für die Erfassung von Netz Darstellungen für größere Bereiche (z. b. mehr als einen einzelnen Raum) für die Visualisierung oder weitere Gitter Verarbeitung geeignet. Das mit enableworldmesh zurückgegebene World Mesh verfügt über eine konsistente Detailebene, die bei gerenderter Darstellung als Wireframe eine ansprechendere Visualisierung ergeben kann.

### <a name="see-also"></a>Siehe auch

* [Scene Understanding SDK](scene-understanding-SDK.md)
* [Räumliche Zuordnung](spatial-mapping.md)
