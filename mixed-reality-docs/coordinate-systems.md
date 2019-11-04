---
title: Koordinatensysteme
description: Die räumlichen Koordinatensysteme, die zum Erstellen von sitzender, stehendem, Raum-und weltweiten Umgebungen mit gemischter Realität verwendet werden.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Koordinatensystem, geografischer Koordinatensystem, nur Ausrichtung, sitzender Skalierung, aneinandergreifende Skala, Raum Skala, Welt weite, 360 Grad, sitzend, stehend, Raum, Welt, Skala, Position, Ausrichtung, stationär, angefügt, Phase, Anker, räumlicher Anker, weltweit gesperrt, Welt sperren, Text gesperrt, Body-Lock, Begrenzungen, Persistenz, Freigabe, nach Verfolgungs Verlust, räumliche cloudanker
ms.openlocfilehash: 228f46f1962c39012571234da47ccec07aa67118
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436142"
---
# <a name="coordinate-systems"></a>Koordinatensysteme

Im Kern platzieren Mixed Reality-apps [holograms](hologram.md) in ihrer Welt, die wie echte Objekte Aussehen und klingen. Dies umfasst die genaue Positionierung und Orientierung dieser Hologramme an Orten in der Welt, die für den Benutzer von Bedeutung sind, unabhängig davon, ob es sich um den physischen Raum oder einen virtuellen Bereich handelt, den Sie erstellt haben. Wenn Sie sich über die Position und Ausrichtung ihrer Hologramme oder eine beliebige andere Geometrie, wie z. b. den [Blick](gaze-and-commit.md) Strahl oder die [Handpositionen](hands-and-tools.md), in Bezug auf die Position und Ausrichtung der Argumente anwenden, bietet Windows verschiedene reale Koordinatensysteme an  **räumliche Koordinatensysteme**.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/TneGSeqVAXQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="40%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    </colgroup>
    <tr>
        <td><strong>Feature</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td><a href="coordinate-systems.md#stationary-frame-of-reference">Stationärer Frame des Verweises</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="coordinate-systems.md#attached-frame-of-reference">Angefügter Frame des Verweises</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="coordinate-systems.md#stage-frame-of-reference">Stagingframe des Verweises</a></td>
        <td>Noch nicht unterstützt</td>
        <td>Noch nicht unterstützt</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="coordinate-systems.md#spatial-anchors">Raumanker</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="spatial-mapping.md">Räumliche Abbildung</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td><a href="scene-understanding.md">Grundlegendes zu Szenen</a></td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="mixed-reality-experience-scales"></a>Skalierbarkeit mit gemischter Realität

Mixed Reality-Apps können eine Vielzahl von Benutzeroberflächen entwerfen, von 360-Fach-Video Viewern, die nur die Ausrichtung des Headsets benötigen, bis hin zu vollständig skalierbaren apps und spielen, für die räumliche und räumliche Anker erforderlich sind:
<br>

| Erfahrungs Skala | Anforderungen | Beispiel Darstellung | 
|----------|----------|----------|
|  **Nur Ausrichtung** |  **Headset-Ausrichtung** (schwer bündig ausgerichtet) |  360 °-Video-Viewer | 
|  **Sitzender Maßstab** |  Oberhalb von plus Punkt **Position** relativ zur Nullposition |  Renn Spiel-oder Leerzeichen Simulator | 
|  **Ständige Skalierung** |  Oberhalb von Plus **Stufen Boden Ursprung** |  Aktions Spiel, bei dem Sie an Ort und Stelle ausweichen  | 
|  **Raumskala** |  Oberhalb, plus **Phasen Begrenzungen Polygon** |  Rätselspiel, in dem Sie das Rätsel durchlaufen | 
|  **Weltweit skalieren** |  **Räumliche Anker** (und in der Regel [räumliche Zuordnung](spatial-mapping.md)) |  Spielen Sie mit Feinden, die von den echten Wänden stammen, z. b. [roboraid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j) | 

Diese Erfahrungs Skala folgt dem Modell "Schachteln von Puppen". Das wichtigste Entwurfs Prinzip für Windows Mixed Reality besteht darin, dass ein bestimmtes Headset Apps unterstützt, die für die Skalierung von Ziel erlebungen und für alle weniger Skalierungen entwickelt wurden:
<br>

| 6DOF-Nachverfolgung | Floor definiert | 360 °-Nachverfolgung | Definierte Begrenzungen | Raumanker | Maximale Leistung | 
|----------|----------|----------|----------|----------|----------|
|  Nein |  - |  - |  - |  - |  **Nur Ausrichtung** | 
|  **Ja** |  Nein |  - |  - |  - |  **Sitzen** | 
|  **Ja** |  **Ja** |  Nein |  - |  - |  **Fortschritt** | 
|  **Ja** |  **Ja** |  **Ja** |  Nein |  - |  **Steht-360 °** | 
|  **Ja** |  **Ja** |  **Ja** |  **Ja** |  Nein |  **Versand** | 
|  **Ja** |  **Ja** |  **Ja** |  **Ja** |  **Ja** |  **World** | 

Beachten Sie, dass der stagingframe von Reference für hololens noch nicht unterstützt wird. Eine Raum basierte App auf hololens muss derzeit [räumliche Zuordnung](spatial-mapping.md) oder [Szenen Verständnis](scene-understanding.md) verwenden, um den Boden und die Wände des Benutzers zu ermitteln.

## <a name="spatial-coordinate-systems"></a>Räumliche Koordinatensysteme

Alle 3D-Grafikanwendungen verwenden [kartesische Koordinatensysteme](https://docs.microsoft.com/windows/uwp/graphics-concepts/coordinate-systems) , um die Positionen und Ausrichtungen von Objekten in den von Ihnen renderischen virtuellen Bereichen zu verdeutlichen. Diese Koordinatensysteme richten drei senkrechte Achsen ein, um Objekte zu positionieren: eine X-, Y-und Z-Achse.

In [gemischter Realität](mixed-reality.md)werden Ihre apps sowohl für virtuelle als auch für physische Koordinatensysteme in den Grund. Windows Ruft ein Koordinatensystem auf, das in der physischen Welt ein **räumliches Koordinatensystem**hat.

Räumliche Koordinatensysteme drücken ihre Koordinaten Werte in Meter. Dies bedeutet, dass Objekte, die zwei Einheiten in der X-, Y-oder Z-Achse ablegen, 2 Meter voneinander getrennt angezeigt werden, wenn Sie in gemischter Realität gerendert werden. Auf diese Weise können Sie problemlos Objekte und Umgebungen in der realen Skalierung darstellen.

Im Allgemeinen können kartesische Koordinatensysteme entweder von rechts oder Links übergeben werden. Räumliche Koordinatensysteme unter Windows sind immer rechts häng, was bedeutet, dass die positive X-Achse nach rechts zeigt, die positive Y-Achse nach oben (ausgerichtet an der Schwerkraft) und die positive Z-Achse auf Sie zeigt.

Bei beiden Koordinatensystemen zeigt die positive X-Achse nach rechts und die positive Y-Achse nach oben. Der Unterschied besteht darin, ob die positive Z-Achse auf Sie hin oder Weg zeigt. Sie können merken, welche Richtung die positive Z-Achse zeigt, indem Sie die Finger entweder in der linken oder rechten Ecke in der positiven X-Richtung zeigen und Sie in die positive Y-Richtung lenken. Die Richtung, auf die sich der Ziehpunkt von Ihnen befindet, ist die Richtung, auf die die positive Z-Achse für dieses Koordinatensystem zeigt.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>Aufbauen einer reinen Orientierung oder einer Skalierungs Funktion

Der Schlüssel für das holografische [Rendering](rendering.md) besteht darin, dass Sie die Ansicht der Hologramme Ihrer APP für jeden Frame ändern, wenn der Benutzer sich bewegt, um die vorhergesagte Kopfzeile abzugleichen. Sie können Benutzeroberflächen mit **sitzender Skalierung** erstellen, die Änderungen an der Anfangsposition des Benutzers und der Kopf Richtung mithilfe eines **stationären Frame Verweises**berücksichtigen.

Einige Inhalte müssen Aktualisierungen der Head-Position ignorieren und stets an einer ausgewählten Überschrift und der Entfernung vom Benutzer entfernt bleiben. Das primäre Beispiel ist 360-Grad-Video: da das Video aus einer einzelnen, festgelegten Perspektive aufgezeichnet wird, würde es die Illusion, dass die Ansichts Position relativ zum Inhalt verschoben werden soll, auch dann zerstören, wenn sich die Ansichts Ausrichtung ändern muss, wenn sich der Benutzer befindet. Mit einem **angefügten Verweis Rahmen**können Sie diese Benutzeroberfläche **nur auf Orientierung** aufbauen.

### <a name="stationary-frame-of-reference"></a>Stationärer Frame des Verweises

Das Koordinatensystem, das von einem stationären Verweis Rahmen bereitgestellt wird, sorgt dafür, dass die Positionen von Objekten in der Nähe des Benutzers so stabil wie möglich im Verhältnis zur Welt bleiben, während Änderungen an der Hauptposition des Benutzers berücksichtigt werden.

Bei der Skalierung in einem Spiel Modul, wie z. b. [Unity](https://unity3d.com/), ist ein stationärer Frame des Verweises, der den "Welt Ursprung" der Engine definiert. Objekte, die sich in einer bestimmten Welt Koordinate befinden, verwenden den stationären Verweis Rahmen, um Ihre Position in der realen Welt mit denselben Koordinaten zu definieren. Inhalte, die in der Welt abgelegt werden, auch wenn der Benutzer Sie durchläuft, werden als **weltweit gesperrte** Inhalte bezeichnet.

Eine App erstellt in der Regel einen stationären Verweis Rahmen beim Start und verwendet das Koordinatensystem während der gesamten Lebensdauer der app. Als App-Entwickler in Unity können Sie einfach mit dem Platzieren von Inhalten in Relation zum Ursprung beginnen, was an der Anfangsposition und Ausrichtung des Benutzers liegen wird. Wenn der Benutzer an einem neuen Speicherort wechselt und seine benutzerfreundliche Umgebung fortsetzen möchten, können Sie den Ursprung der Welt an diesem Speicherort wiederholen.

Wenn das System mehr über die Umgebung des Benutzers erfährt, kann es im Laufe der Zeit feststellen, dass die Abstände zwischen verschiedenen Punkten in der realen Welt kürzer oder länger sind als das System, das zuvor angenommen wurde. Wenn Sie holograms in einem stationären Referenz Verweis für eine APP auf hololens-Systemen darstellen, bei denen Benutzer über einen Bereich von ungefähr 5 Metern hinaus bewegen, kann Ihre APP Abweichungen am beobachteten Speicherort dieser Hologramme beobachten. Wenn Benutzer in Ihrer Umgebung über 5 Meter hinausgehen, werden Sie eine [Welt weite](#building-a-world-scale-experience)Umgebung entwickeln, die zusätzliche Techniken erfordert, um Hologramme stabil zu halten, wie unten beschrieben.

### <a name="attached-frame-of-reference"></a>Angefügter Frame des Verweises

Ein angefügter Frame des Verweises wechselt mit dem Benutzer, während Sie sich bewegen, wobei eine festgelegte Überschrift definiert ist, wenn die APP erstmalig erstellt. Dadurch kann der Benutzer die Inhalte, die innerhalb dieses Referenzrahmens platziert werden, bequem überprüfen. Inhalt, der in dieser Benutzer relativen Weise gerendert wird, wird als **Text gesperrter** Inhalt bezeichnet.

Wenn das Headset nicht ermitteln kann, wo es sich auf der Welt befindet, stellt ein angefügter Frame von Reference das einzige Koordinatensystem bereit, das zum Rendering von holograms verwendet werden kann. Dies ist ideal für die Anzeige der Fall Back Benutzeroberfläche, um dem Benutzer mitzuteilen, dass das Gerät die Benutzer nicht auf der ganzen Welt finden kann. Apps mit sitzender oder höherer Skalierung sollten einen nur für die Orientierung ausgerichteten Fall Back enthalten, um dem Benutzer die Möglichkeit zu geben, die Benutzeroberfläche zu wiederholen, ähnlich wie in der [Mixed Reality-Startseite](navigating-the-windows-mixed-reality-home.md).

## <a name="building-a-standing-scale-or-room-scale-experience"></a>Aufbauen einer Dauer-oder Raum Skalierung

Um die Skalierung über ein immersives Headset hinaus zu übersetzen und eine Funktion für eine permanente **Skalierung**zu erstellen, können Sie den **Stufen Rahmen der Referenz**verwenden.

Um eine **Raum**Umgebung bereitzustellen, die es Benutzern ermöglicht, innerhalb der von Ihnen vordefinierten 5-Meter-Grenze zu navigieren, können Sie auch nach **Phasen Begrenzungen** suchen.

### <a name="stage-frame-of-reference"></a>Stagingframe des Verweises

Beim ersten Einrichten eines immersiven Headsets definiert der Benutzer eine **Stufe**, die den Raum darstellt, in dem Sie Gemischte Realität erleben werden. In der Stufe ist mindestens ein **Phasen Ursprung**definiert, ein räumliches Koordinatensystem, das sich auf die ausgewählte bodenposition des Benutzers konzentriert und die Ausrichtung des Geräts angibt. Durch das Platzieren von Inhalten in diesem Phasen Koordinatensystem auf der Ebene Y = 0 können Sie sicherstellen, dass Ihre holograms bequem auf dem Boden angezeigt werden, wenn der Benutzer steht, und den Benutzern eine Funktion zur Verfügung **steht**.

### <a name="stage-bounds"></a>Stufen Begrenzungen

Der Benutzer kann optional auch **Stufen Begrenzungen**definieren, einen Bereich innerhalb des Raums, in dem er die Möbel gelöscht hat, wo er sich in gemischter Realität bewegen möchte. Wenn dies der Fall ist, kann die APP eine **Raum Skalierung**erstellen, indem diese Begrenzungen verwendet werden, um sicherzustellen, dass Hologramme immer platziert werden, wo der Benutzer Sie erreichen kann.

Da der stagingframe von Reference ein einzelnes festes Koordinatensystem bereitstellt, in dem der Inhalt der Grundstruktur platziert werden soll, ist dies der einfachste Weg zum Portieren von Anwendungen für die permanente und Raum Skalierung, die für Virtual Reality-Headsets entwickelt wurden. Wie bei diesen VR-Plattformen kann ein einzelnes Koordinatensystem Inhalte jedoch nur in ungefähr einem 5-Meter-Durchmesser (16 Meter) stabilisieren, bevor die Auswirkung von Arm-Arm-Effekten den Anteil von Inhalten aus dem Mittelpunkt merklich ändert, wenn sich das System anpasst. Um über 5 Meter hinauszugehen, sind räumliche Anker erforderlich.

## <a name="building-a-world-scale-experience"></a>Entwickeln eines weltweiten Erlebnisses

Hololens ermöglicht echte **Welt weite** Oberflächen, mit denen Benutzer mehr als 5 Meter bewegen können. Zum Erstellen einer weltweiten App benötigen Sie neue Techniken, die über diejenigen hinausgehen, die für Raum Skalierungen verwendet werden.

### <a name="why-a-single-rigid-coordinate-system-cannot-be-used-beyond-5-meters"></a>Gründe für die Verwendung eines einzelnen starren Koordinatensystems über 5 Meter hinaus

Beim Schreiben von spielen, Daten Visualisierungs-Apps oder Virtual Reality-apps besteht der typische Ansatz darin, ein absolutes Welt Koordinatensystem einzurichten, das alle anderen Koordinaten zuverlässig wieder zuordnen können. In dieser Umgebung können Sie immer eine stabile Transformation finden, die eine Beziehung zwischen zwei beliebigen Objekten in dieser Welt definiert. Wenn Sie diese Objekte nicht verschoben haben, bleiben ihre relativen Transformationen immer gleich. Diese Art des globalen Koordinatensystems funktioniert gut, wenn eine rein virtuelle Welt gerendert wird, in der Sie die gesamte Geometrie im Voraus kennen. Heute stellen VR-apps in der Regel eine solche Art von absoluter Raumkoordinaten System mit dem Ursprung im Boden dar.

Im Gegensatz dazu verfügt ein ungeplantes gemischtes Reality-Gerät wie hololens über ein dynamisches Sensor basiertes Verständnis der Welt, bei dem seine Wissensquelle im Laufe der Zeit der Benutzerumgebung kontinuierlich angepasst wird, während Sie viele Meter in einer ganzen Etage eines Gebäudes durchlaufen. In einer weltweiten Umgebung, wenn Sie alle Ihre Hologramme in einem einzigen starren Koordinatensystem abgelegt haben, würden diese Hologramme zwangsläufig mit der Zeit, entweder relativ zur Welt oder zueinander, Abdriften.

Beispielsweise kann das Headset derzeit annehmen, dass zwei Orte der Welt vier Meter voneinander entfernt sind, und später dieses Verständnis verfeinern, indem er erfährt, dass die Standorte tatsächlich 3,9 Meter voneinander entfernt sind. Wenn diese Hologramme anfänglich vier Meter voneinander getrennt in einem einzigen starren Koordinatensystem platziert wurden, würde eine davon immer 0,1 Meter aus der realen Welt angezeigt werden.

### <a name="spatial-anchors"></a>Raumanker

Windows Mixed Reality löst das im vorherigen Abschnitt beschriebene Problem, indem es Ihnen ermöglicht, [räumliche Anker](spatial-anchors.md) zu erstellen, um wichtige Punkte in der Welt zu markieren, an denen der Benutzer holograms platziert hat. Ein Raumanker stellt einen wichtigen Punkt in der Umgebung dar, den das System im Laufe der Zeit nachverfolgen sollte.

Wenn das Gerät über die Welt erfährt, können diese räumlichen Anker ihre Position relativ zueinander anpassen, um sicherzustellen, dass jeder Anker genau dort platziert wird, wo er relativ zur realen Welt platziert wurde. Wenn Sie an der Stelle, an der der Benutzer ein – Hologramm platziert, einen räumlichen Anker platzieren und dann dieses Hologramm relativ zum räumlichen Anker positionieren, können Sie sicherstellen, dass das – Hologramm eine optimale Stabilität aufrecht erhält, auch wenn der Benutzer über Dutzende von Metern hinweg wechselt.

Diese kontinuierliche Anpassung räumlicher Anker relativ zueinander ist der wesentliche Unterschied zwischen Koordinatensystemen von räumlichen Ankern und stationären Frame Frames:

* Holograms, die im stationären Frame des Verweises abgelegt werden, behalten alle eine starre Beziehung untereinander bei. Wenn der Benutzer jedoch lange Entfernungen durchläuft, kann das Koordinatensystem dieses Frames relativ zur Welt abweichen, um sicherzustellen, dass holograms neben dem Benutzer stabil angezeigt werden.

* Holograms, die im stagingframe von Reference abgelegt werden, behalten auch eine starre Beziehung untereinander bei. Im Gegensatz zum stationären Frame bleibt der stagingframe immer relativ zum definierten physischen Ursprung festgelegt. Inhalte, die im Koordinatensystem der Stufe hinter der Grenze von fünf Metern gerendert werden, werden jedoch nur stabil angezeigt, wenn der Benutzer innerhalb dieser Grenze steht.

* Holograms, die mithilfe eines räumlichen Ankers platziert werden, können relativ zu holograms mit einem anderen räumlichen Anker abweichen. Dadurch kann Windows das Verständnis der Position jedes räumlichen Ankers verbessern, auch wenn beispielsweise ein Anker sich nach Links anpassen muss und ein anderer Anker richtig angepasst werden muss.

Im Gegensatz zu einem stationären Verweis Verweis, der immer die Stabilität in der Nähe des Benutzers optimiert, gewährleistet der Stufen Rahmen der Referenz und räumlichkeits Anker die Stabilität in der Nähe ihrer Ursprünge. Dadurch bleiben die Hologramme im Laufe der Zeit genau bestehen, aber es bedeutet auch, dass Hologramme, die zu weit vom Ursprung ihres Koordinatensystems gerendert werden, zunehmend schwerwiegende Auswirkungen auf die Hebel-Arm haben. Dies liegt daran, dass kleine Anpassungen an Position und Ausrichtung der Stufe oder des Ankers proportional zu der Entfernung von diesem Anker vergrößert werden. 

Eine gute Faustregel besteht darin, sicherzustellen, dass alles, was Sie basierend auf dem Koordinatensystem eines entfernten räumlichen Ankers Renderingsystem haben, innerhalb von ungefähr 3 Metern seines Ursprungs liegt. Für einen in der Umgebung befindlichen Ursprung ist das Rendering von entfernten Inhalten in Ordnung, da sich ein erhöhter Positionsfehler nur auf kleine Hologramme auswirkt, die in der Ansicht des Benutzers nicht stark verschoben werden.

### <a name="spatial-anchor-persistence"></a>Dauerhaftigkeit räumlicher Anker

Räumliche Anker können es Ihrer APP ermöglichen, sich auch dann an einen wichtigen Speicherort zu erinnern, wenn Ihre APP angehalten oder das Gerät heruntergefahren wird.

Sie können die räumlichen Anker, die Ihre APP erstellt, auf dem Datenträger speichern und später wieder zurück laden, indem Sie Sie im **räumlichen Anker Speicher**Ihrer APP beibehalten. Beim Speichern oder Laden eines Ankers geben Sie einen Zeichen folgen Schlüssel an, der für Ihre APP sinnvoll ist, um den Anker zu einem späteren Zeitpunkt zu identifizieren. Stellen Sie sich diesen Schlüssel als den Dateinamen für Ihren Anker vor. Wenn Sie andere Daten mit diesem Anker verknüpfen möchten, z. b. ein 3D-Modell, das der Benutzer an diesem Speicherort platziert hat, speichern Sie diese im lokalen Speicher Ihrer APP, und ordnen Sie Sie dem von Ihnen gewählten Schlüssel zu.

Durch das Beibehalten von Ankern im Geschäft können Ihre Benutzer individuelle Hologramme platzieren oder einen Arbeitsbereich platzieren, in dem eine APP die verschiedenen holograms platzieren wird. Anschließend finden Sie diese Hologramme später, wo Sie erwartet werden, über viele Verwendungszwecke Ihrer APP.

Sie können <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> auch für die asynchrone Hologrammpersistenz auf HoloLens-, iOS- und Android-Geräten verwenden.  Durch die gemeinsame Nutzung eines dauerhaften Cloudraumankers können mehrere Geräte dasselbe persistierte Hologramm im Verlauf der Zeit beobachten, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.

### <a name="spatial-anchor-sharing"></a>Räumliche Anker Freigabe

Ihre APP kann auch einen räumlichen Anker in Echtzeit mit anderen Geräten gemeinsam nutzen, sodass Sie gemeinsam genutzte Echtzeitumgebungen nutzen können.

Durch die Verwendung von <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">räumlichen Azure-Ankern</a>kann Ihre APP einen räumlichen Anker für mehrere hololens-, IOS-und Android-Geräte freigeben. Indem jedes Gerät ein Hologramm mit demselben Raumanker rendert, wird das Hologramm in der realen Welt für alle Benutzer an der gleichen Stelle angezeigt.

## <a name="avoid-head-locked-content"></a>Vermeiden von Kopf gesperrten Inhalten

Wir raten dringend davon ab, den Inhalt des gesperrten Inhalts zu rendern, der an einer festen Stelle in der Anzeige bleibt (z. b. ein HUD) Im Allgemeinen ist der Inhalt von Kopf gesperrten Inhalten für Benutzer nicht zufrieden und ist nicht wie ein natürlicher Teil ihrer Welt.

Der Inhalt des gesperrte Inhalts sollte in der Regel durch holograms ersetzt werden, die an den Benutzer angefügt oder in der Welt selbst platziert werden. Beispielsweise sollten [Cursor](cursors.md) in der Regel in die Welt übermittelt werden, wobei die Skalierung auf natürliche Weise die Position und die Entfernung des Objekts im Benutzer Blick widerspiegelt.

## <a name="handling-tracking-errors"></a>Behandeln von nach Verfolgungs Fehlern

In einigen Umgebungen, wie z. b. dunklen Hallways, ist es möglicherweise nicht möglich, dass ein Headset, das die interne Nachverfolgung verwendet, sich auf der ganzen Welt korrekt findet. Dies kann dazu führen, dass holograms entweder nicht angezeigt werden oder an falschen Stellen angezeigt werden, wenn Sie falsch behandelt werden. Wir besprechen nun die Bedingungen, unter denen dies auftreten kann, die Auswirkungen auf die Benutzerumgebung und Tipps, wie Sie diese Situation am besten verarbeiten können.

### <a name="headset-cannot-track-due-to-insufficient-sensor-data"></a>Das Headset kann aufgrund unzureichender Sensordaten nicht nachverfolgt werden.

Manchmal können die Sensoren des Headsets nicht ermitteln, wo sich das Headset befindet. Dies kann vorkommen, wenn der Raum dunkel ist, oder wenn die Sensoren durch Haare oder Hände abgedeckt werden, oder wenn die Umgebung nicht über genügend Textur verfügt.

Wenn dies der Fall ist, kann das Headset seine Position nicht mit ausreichender Genauigkeit nachverfolgen, um die Welt gesperrten holograms zu erzeugen. Sie können nicht herausfinden, wo sich ein räumlicher Anker, ein stationärer Frame oder ein stagingframe relativ zum Gerät befindet, aber Sie können nach wie vor im angefügten Frame des Verweises Text mit gesperrtem Inhalt Rendering.

Ihre APP sollte dem Benutzer mitteilen, wie die Positions Nachverfolgung rückgängig zu machen ist. dabei wird ein Fall Back-gesperrter Inhalt gerendert, der einige Tipps beschreibt, z. b. die Abdeckung der Sensoren und das Einschalten von Beleuchtung.

### <a name="headset-tracks-incorrectly-due-to-dynamic-changes-in-the-environment"></a>Das Headset ist aufgrund dynamischer Änderungen in der Umgebung falsch nachverfolgt.

Manchmal kann das Gerät nicht ordnungsgemäß nachverfolgt werden, wenn eine große Anzahl dynamischer Änderungen in der Umgebung vorhanden ist, z. b. viele Personen, die im Raum unterwegs sind. In diesem Fall scheinen die Hologramme zu springen oder zu wechseln, wenn das Gerät versucht, sich selbst in dieser dynamischen Umgebung zu verfolgen. Wenn Sie dieses Szenario erreichen, empfiehlt es sich, das Gerät in einer weniger dynamischen Umgebung zu verwenden.

### <a name="headset-tracks-incorrectly-because-the-environment-has-changed-significantly-over-time"></a>Das Headset wird falsch verfolgt, weil sich die Umgebung im Laufe der Zeit erheblich geändert

Wenn Sie in einer Umgebung, in der viele Änderungen durchgeführt wurden (z. b. bedeutende Bewegung von Möbeln, Wall-Hangings usw.), ein Headset verwenden, kann es vorkommen, dass einige holograms von ihren ursprünglichen Speicherorten verschoben werden. Die früheren Hologramme können auch umgangen werden, wenn der Benutzer in diesem neuen Bereich bewegt wird. Der Grund hierfür ist, dass das System den Speicherplatz nicht mehr enthält und versucht, die Umgebung neu zuzuordnen, während versucht wird, die Features des Raums abzustimmen. In diesem Szenario empfiehlt es sich, Benutzer dazu zu ermutigen, Hologramme, die Sie in der Welt abgelegt haben, erneut zu platzieren, wenn Sie nicht erwartungsgemäß angezeigt werden.

### <a name="headset-tracks-incorrectly-due-to-identical-spaces-in-an-environment"></a>Das Headset ist aufgrund identischer Leerzeichen in einer Umgebung falsch nachverfolgt.

Manchmal kann ein Zuhause oder ein anderer Bereich zwei identische Bereiche haben. Beispielsweise zwei identische Konferenzräume, zwei identische Eckbereiche, zwei große identische Poster, die das Ansichts Feld des Geräts abdecken. In solchen Szenarien kann das Gerät manchmal zwischen identischen Teilen verwechselt und in der internen Darstellung als identisch markiert werden. Dies kann dazu führen, dass die holograms aus einigen Bereichen an anderen Speicherorten angezeigt werden. Das Gerät verliert möglicherweise die Nachverfolgung, da die interne Darstellung der Umgebung beschädigt ist. In diesem Fall wird empfohlen, das Umweltverständnis des Systems zurückzusetzen. Beachten Sie, dass das Zurücksetzen der Zuordnung zum Verlust aller räumlichen Anker Platzierungen führt. Dies führt dazu, dass das Headset in den eindeutigen Bereichen der Umgebung gut nachverfolgt wird. Das Problem kann jedoch erneut auftreten, wenn das Gerät erneut zwischen den identischen Bereichen verwechselt wird.

## <a name="see-also"></a>Weitere Informationen:
* [GDC 2017-Präsentation zu räumlichen Koordinatensystemen und Holographic-Rendering](https://channel9.msdn.com/events/GDC/GDC-2017/GDC2017-008)
* [Koordinatensysteme in Unity](coordinate-systems-in-unity.md)
* [Koordinatensysteme in DirectX](coordinate-systems-in-directx.md)
* [Raumanker](spatial-anchors.md)
* [Gemeinsame Erlebnisse in Mixed Reality](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [Fallstudie – Schauen durch Löcher in Ihrer Realität](case-study-looking-through-holes-in-your-reality.md)
