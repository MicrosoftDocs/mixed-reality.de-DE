---
title: Koordinatensysteme
description: Der räumliche Koordinatensysteme verwendet, um sitzen erstellen, gemischt ständigen, Raum skalierbare und weltweit einsetzbaren Realität Erfahrungen.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Koordinatensystem, räumliche Koordinatensystem, Ausrichtung, sitzen Skalierung, ständigen Maß Platz-skalieren, weltweit skalierbare, 360-Grad-sitzen, ständigen, Raum, Welt, skalieren, Position, Ausrichtung, nicht bewegt werden angefügte, Phase, Anker, räumliche Anker, World gesperrt, Welt sperrende, Text-gesperrt, Text-sperren, den angegebenen Begrenzungen, Dauerhaftigkeit, Freigabe, cloud Nachverfolgen von Verlust, räumliche Anker
ms.openlocfilehash: f4b945a3ffb83b9ac0a94e0d793a19939aece3bb
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829858"
---
# <a name="coordinate-systems"></a>Koordinatensysteme

In ihrem Kern mixed Reality-apps direkt [Hologramme](hologram.md) in Ihre Welt, die Aussehen und hört auf echte Objekte. Dies umfasst genau positionieren und Ausrichten von diesen Hologramme an Stellen in der ganzen Welt, die für den Benutzer von Bedeutung sind, ob die Welt ihre physischen Raum oder ein virtueller Bereich, die Sie erstellt haben. Wenn z. B. über die Position und Ausrichtung von Ihrem Hologramme oder andere Geometrie Ansatzpunkt der [bestaunen](gaze.md) Chow oder [übergeben Positionen](gestures.md), Windows bietet verschiedene realen Koordinatensysteme in der der Geometry ausgedrückt werden kann, bekannt als **räumliche Koordinatensysteme**.

<br>

>[!VIDEO https://www.youtube.com/embed/TneGSeqVAXQ]

## <a name="device-support"></a>Unterstützung von Geräten

<table>
    <colgroup>
    <col width="40%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    </colgroup>
    <tr>
        <td><strong>Funktion</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></td>
    </tr>
     <tr>
        <td><a href="coordinate-systems.md#stationary-frame-of-reference">Feststehende Verweisrahmen</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="coordinate-systems.md#attached-frame-of-reference">Angefügte Verweisrahmen</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="coordinate-systems.md#stage-frame-of-reference">Referenz für Stufe</a></td>
        <td>Noch unterstützt nicht</td>
        <td>Noch unterstützt nicht</td>
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
</table>

## <a name="mixed-reality-experience-scales"></a>Skalen für Mixed Reality-Erfahrung

Mixed Reality-apps können für eine Vielzahl von Benutzerfunktionen von 360-Grad-video-Viewern entwerfen, die nur den Kopfhörer des Ausrichtung, vollständige weltweit einsetzbaren apps und Spiele, die räumliche Zuordnung und räumliche Anker benötigen:
<br>

| Skalierung der Benutzeroberfläche | Anforderungen | Beispiel-Erfahrung | 
|----------|----------|----------|
|  **Orientation-only** |  **Kopfhörer Ausrichtung** (Schwerkraft ausgerichtet) |  360°-video-viewer | 
|  **Seated-scale** |  Oben, Plus **Kopfhörer Position** relativ zur Position null |  Rennspiels Spiel oder Leerzeichen simulator | 
|  **Standing-scale** |  Oben, Plus **Floor Ursprung bereitstellen** |  Aktion-Spiel, in dem Sie Wildenten und direktes umgehen  | 
|  **Room-scale** |  Oben, Plus **Phase Begrenzung Vieleck** |  Puzzle-Spiel, in dem das Rätsel aufzusuchen Sie | 
|  **World-scale** |  **Räumliche Anker** (und in der Regel [räumliche Zuordnung](spatial-mapping.md)) |  Spiel mit Feinde, die Ihre echten Wände, z. B. stammen [RoboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j) | 

Diese kommen Skalen führen Sie ein Modell "schachteln Puppen". Die wichtiges Entwurfsprinzip für Windows Mixed Reality hier ist, dass eine bestimmte Kopfhörer apps, die für eine Zielmenge von Erfahrungen sowie alle weniger Skalen unterstützt:
<br>

| 6DOF-nachverfolgung | Floor definiert | 360° nachverfolgen | Grenzen | Räumliche Anker | Max-Erfahrung | 
|----------|----------|----------|----------|----------|----------|
|  Nein |  - |  - |  - |  - |  **Orientation-only** | 
|  **Ja** |  Nein |  - |  - |  - |  **Sitzen** | 
|  **Ja** |  **Ja** |  Nein |  - |  - |  **Ständigen: Vorwärts** | 
|  **Ja** |  **Ja** |  **Ja** |  Nein |  - |  **Platzierung – in der 360°** | 
|  **Ja** |  **Ja** |  **Ja** |  **Ja** |  Nein |  **Room** | 
|  **Ja** |  **Ja** |  **Ja** |  **Ja** |  **Ja** |  **World** | 

Beachten Sie, dass der Phase Verweisrahmen für HoloLens noch nicht unterstützt wird. Derzeit muss eine Raum – Skalieren der app für HoloLens verwenden [räumliche Zuordnung](spatial-mapping.md) Boden und die Wände eines Benutzers zu finden.

## <a name="spatial-coordinate-systems"></a>Räumliche Koordinatensysteme

Alle 3D-Grafikanwendungen verwendet [kartesische Koordinatensysteme](https://docs.microsoft.com/windows/uwp/graphics-concepts/coordinate-systems) Grund zu den Positionen und Ausrichtungen von Objekten in der virtuellen Welt sie ordnungsgemäß gerendert werden. Solche Koordinatensysteme herzustellen 3 Senkrechte Achsen, an denen sich die Objekte zu positionieren: eine X-, Y- und Z-Achse.

In [mixed Reality](mixed-reality.md), Ihre apps werden virtuelle und physische Koordinatensysteme verständlich. Windows Ruft einem Koordinatensystem, die wirkliche Bedeutung in der realen Welt hat eine **räumliche Koordinatensystem**.

Räumliche Koordinatensysteme express die Koordinatenwerte in Meter. Dies bedeutet, dass Objekte mit 2 Einheiten eingefügt auseinander liegen, in der X, Y oder Z-Achse wird neben anderen beim Rendern in mixed Reality-2 Zähler angezeigt. Dadurch können Sie die Objekte und Umgebungen in realen Umfang problemlos zu rendern.

Im Allgemeinen kartesische Koordinatensysteme entweder rechtshändige oder Linkshänder möglich. Räumliche Koordinatensysteme für Windows sind immer rechtshändige, was bedeutet, dass der positiven X-Achse zeigt nach rechts, die positive Y-Achse zeigt nach oben (ausgerichtet auf Schwerkraft) und der positiven z-Achse verweist, zu Ihnen hin.

In beiden Arten der Koordinatensysteme der positiven X-Achse verweist, rechts, und die positive Y-Achse zeigt nach oben. Der Unterschied besteht darin, ob die positive z-Achse auf oder von Ihnen weg verweist. Sie können der Richtung der positive z-Achse verweist, verweist die Finger davon bedenken, Ihre linken oder rechten in der Positive X-Richtung und wenden sie auf die positive Y-Richtung. Die Richtung, dem Daumen hin oder von Ihnen weg zeigt, ist die Richtung, die die positive z-Achse für dieses Koordinatensystem verweist.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>Erstellen eine reine Ausrichtung oder sitzen Skalierung-Erfahrung

Der Schlüssel, holographic [Rendering](rendering.md) ändert der Ansicht Ihrer app von der Hologramme jeden Frame, wenn der Benutzer, bewegt wird, entsprechend ihren vorhergesagten Head während der Übertragung. Sie erstellen können **sitzen Skalierung Erfahrungen** Head-Position des Benutzers und der Head-Ausrichtung mit Hinsicht ändert, ein **feststehende Verweisrahmen**.

Einige Inhalte Head Position Updates an einer ausgewählten Überschrift behoben bleiben muss ignoriert werden und Entfernung des Benutzers zu jeder Zeit. Ein gutes Beispiel ist die 360-Grad-Video: Da das Video vom Standpunkt der einzelnen festen erfasst wird, würde es die Illusion für die Ansichtsposition relativ zu dem Inhalt, verschieben auflöst, obwohl die Ausrichtung der Ansicht geändert werden muss, wenn der Benutzer sich sieht. Sie können z. B. erstellen **Ausrichtung nur Erfahrungen** mit einer **Verweisrahmen angefügt**.

### <a name="stationary-frame-of-reference"></a>Feststehende Verweisrahmen

Das Koordinatensystem, die durch eine feststehende Verweisrahmen funktioniert die Positionen der Objekte in der Nähe der Benutzer relativ zu der Welt als stabil wie möglich beibehalten werden kann, Änderungen in der Head-Position des Benutzers nutzen und gleichzeitig bereitgestellt wird.

Für sitzen Skalierung wie z. B. in einer Spiele-Engine-Funktionen [Unity](https://unity3d.com/), ist eine feststehende Verweisrahmen, definiert der Engine "World Ursprung." Objekte, die an eine bestimmte globale Koordinate platziert werden mithilfe der feststehende Verweisrahmen um ihre Position in der Praxis über die gleichen Koordinaten zu definieren. Inhalt, der verbleibt in der Welt zu platzieren, auch wenn der Benutzer, führt heißt **World-locked** Inhalt.

Eine app wird in der Regel erstellen eine feststehende Verweisrahmen beim Start und seine Koordinatensystem während der Lebensdauer der app verwenden. Als app-Entwickler in Unity können Sie nur starten, platzieren Inhalt relativ zum Ursprung, der an der Anfangsposition für die Haupt- und die Ausrichtung des Benutzers ist. Wenn der Benutzer an einen neuen Ort verschoben und ihre Erfahrungen sitzen Skalierung fortsetzen möchte, können Sie verschoben Welt Ursprung an diesem Speicherort.

Im Laufe der Zeit wie das System mehr über die Umgebung des Benutzers, lernt, können sie ermitteln, ob entfernungen zwischen verschiedenen Punkten in der Praxis kürzer oder länger als das System zuvor war der Meinung sind. Wenn Sie Hologramme in eine feststehende Verweisrahmen für eine app für HoloLens gerendert, in denen Benutzer über einen Bereich von etwa 5 Meter breit will, kann Ihre app Abweichung in den beobachteten Speicherort, der diese Hologramme beobachten. Wenn Ihre Umgebung den Benutzer, die Firma noch wandering über 5 Meter gibt, die Sie erstellen eine [weltweit einsetzbaren Erfahrung](#building-a-world-scale-experience), das weitere Techniken zur Hologramme stabil zu halten, wie unten beschrieben erforderlich ist.

### <a name="attached-frame-of-reference"></a>Angefügte Verweisrahmen

Eine angefügte Verweisrahmen verschiebt mit dem Benutzer, wie sie mit einer festen Überschrift angezeigt, die definiert, wenn die app zunächst den Frame erstellt, durchlaufen. Dadurch kann der Benutzer, die Inhalte, die in dieser Referenz platziert bequem ansehen, um. Inhalte, die auf diese Weise für Benutzer relativ gerendert wird aufgerufen, **Text gesperrt** Inhalt.

Bei den Kopfhörer, in der ganzen Welt also ermitteln kann, bietet eine Referenz für angefügte das nur Koordinatensystem, die zum Rendern von Hologramme verwendet werden kann. Dies vereinfacht sich ideal für die Anzeige von fallback-Benutzeroberfläche, um dem Benutzer mitzuteilen, den sie ihr Gerät in der ganzen Welt finden können. Apps, die sitzen Skalierung oder höher sind sollte eine Ausrichtung nur Fallback ausführen, um dem Benutzer, die Benutzeroberfläche ähnlich wie in diesem Fall Einstieg helfen enthalten die [Mixed Reality home](navigating-the-windows-mixed-reality-home.md).

## <a name="building-a-standing-scale-or-room-scale-experience"></a>Erstellen eine Umgebung ständigen Skalierung oder Platz Skalierung

Sitzen Skalierung auf eine immersive Kopfhörer hinausgehen, und erstellen eine **ständigen Skalierung Erfahrung**, können Sie die **Phase Verweisrahmen**.

Bereitstellen einer **Platz Skalierung Erfahrung**, sodass Benutzer innerhalb der Begrenzung des 5-Meter sie vordefinierte aufzusuchen, sehen Sie sich für **Stufe Grenzen** auch.

### <a name="stage-frame-of-reference"></a>Referenz für Stufe

Beim ersten Einrichten einer immersive Kopfhörer des Benutzers definiert eine **Phase**, steht für den Raum in dem sie treten gemischte Realität. Die Phase minimal definiert eine **Stufe Ursprung**, einem räumliche Koordinatensystem, die der Benutzer zentriert des ausgewählt, Floor Position und die forward-Ausrichtung, in dem sie das Gerät nutzen möchten. Durch Platzieren von Inhalten in dieser Phase Koordinatensystem an den Boden-Ebene Y = 0, können Sie sicherstellen, Ihre Hologramme werden bequem auf dem Boden angezeigt, wenn der Benutzer verfügbar ist, ermöglicht dem Benutzer eine **ständigen Skalierung Erfahrung**.

### <a name="stage-bounds"></a>Phase Grenzen

Der Benutzer kann optional auch definieren **Stufe Grenzen**, ein Bereich innerhalb des Raums, die sie der Möbel gelöscht haben, in dem er im bewegen möchten, mixed Reality. Wenn also die app erstellen, können eine **Platz Skalierung Erfahrung**, diese Grenzen verwenden, um sicherzustellen, dass Hologramme immer platziert werden, in denen Benutzer auf sie zugreifen können.

Da als Referenz für die Phase bereitstellt, dass eine einzelne Koordinatensystem innerhalb der Floor-Relative Inhalt platziert behoben werden, ist es die einfachste Möglichkeit für Portieren ständigen-Skalierung und Platz-Anwendungen für virtuelle Realität Headsets entwickelt wurden. Wie mit diesen Plattformen VR ein einziges Koordinatensystem nur Inhalt zu dessen Durchmesser 5 Meter (16 Fuß) zu stabilisieren können, führt allerdings vor der Hebel-Arm-Effekte Inhalt weit entfernt von der Mitte deutlich verschoben werden, wie das System angepasst wird. Um 5 Meter hinausgehen, werden räumliche Anker benötigt.

## <a name="building-a-world-scale-experience"></a>Erstellen einer weltweit einsetzbaren-Erfahrung

HoloLens für "true" ermöglicht **weltweit einsetzbaren Erfahrungen** , mit deren Hilfe Benutzer über 5 Meter hinaus will. Um eine Welt – Skalieren der app zu erstellen, benötigen Sie neue Techniken hinausgehen für Platz Skalierung Oberflächen verwendet.

### <a name="why-a-single-rigid-coordinate-system-cannot-be-used-beyond-5-meters"></a>Warum ein einziges starres Koordinatensystem über 5 Meter verwendet werden kann

Derzeit ist beim Schreiben von Spielen, Data-visualisierungs-apps oder apps für virtuelle Realität der typische Ansatz zu, um eine absolute Welt Koordinatensystem herzustellen, die alle anderen Koordinaten zuverlässig an zuordnen können. In dieser Umgebung finden Sie immer eine stabile Transformation, die eine Beziehung zwischen zwei Objekten in dieser Welt definiert. Wenn Sie diese Objekte nicht verschieben, würde deren relativen Transformationen immer unverändert bleiben. Diese Art von globalen Koordinatensystems funktioniert gut, wenn eine rein virtuelle Welt rendern, in dem Sie alle der Geometry-Instanz im Voraus kennen. Raum einsetzbaren VR-apps richten Sie noch heute in der Regel dieser Art von absoluten Platz Skalierung Koordinatensystem mit seinem Ursprung auf dem Boden.

Im Gegensatz dazu weist eine unabhängig mixed Reality-Geräte wie HoloLens ein dynamisches Sensor gesteuerte Verständnis der Welt, sein Wissen im Laufe der Zeit der benutzerumgebung fortlaufend anpassen, wie sie viele Zähler über eine gesamte Stockwerk eines Gebäudes führen. Wenn Sie alle Ihre Hologramme in einem einzelnen starre Koordinatensystem platziert würde diese Hologramme in einer weltweit einsetzbaren-Oberfläche unbedingt im Laufe der Zeit relativ zu der ganzen Welt oder miteinander abweichen.

Beispielsweise kann die Kopfhörer glauben derzeit zwei Positionen in der ganzen Welt 4 Meter auseinander liegen sollen, und klicken Sie dann später verfeinern, besser zu verstehen, lernen, dass die Standorte in der Tat 3.9 Meter auseinander sind. Wenn diese Hologramme anfänglich 4 Meter auseinander liegen in einem einzelnen starre Koordinatensystem platziert wurde, wird eine von ihnen dann immer 0,1 Zähler aus, aus der realen Welt angezeigt.

### <a name="spatial-anchors"></a>Räumliche Anker

Windows Mixed Reality kann das Problem mit dem im vorherigen Abschnitt beschrieben werden, und lassen Sie die erstellen [räumliche Anker](spatial-anchors.md) an wichtige Punkten in der ganzen Welt zu markieren, wo der Benutzer Hologramme platziert wurde. Ein räumlicher Anker stellt einen wichtigen Punkt in der ganzen Welt, die das System nachverfolgen im Laufe der Zeit sollten dar.

Wie das Gerät über die Welt lernt, können diese räumliche Anker ihre Position relativ zu anderen anpassen, je nach Bedarf, um sicherzustellen, dass jede Anker bleibt genau, wo sie relativ zu der realen Welt abgelegt wurde. Indem ein räumliche Anker platzieren, an dem Speicherort, in denen der Benutzer ggf. ein Hologramm platziert, und positionieren diese – Hologramm relativ zu seiner räumlichen Anker, können Sie sicherstellen, dass Hologramm optimalen Stabilität verwaltet auch, wenn der Benutzer über Dutzende Verbrauchseinheiten wechselt.

Diese kontinuierliche Anpassung der räumlichen Anker zueinander ist der wesentliche Unterschied zwischen Coordinate systems aus räumlichen Anker und stationär Bezugsrahmen:

* Hologramme platziert, in der feststehende Verweisrahmen alle beibehalten eine feste Beziehung zueinander. Wie lange Strecken der Benutzer führt kann jedoch Koordinatensystem des Frames abweichen, relativ zu der ganzen Welt, um sicherzustellen, dass die stabile Hologramme neben dem Benutzer angezeigt werden.

* In der Phase Verweisrahmen platziert Hologramme erhalten Sie auch eine feste Beziehung miteinander. Im Gegensatz zu den stationär Frame bleibt der Phase Frame immer festen relativ zu dessen definierten physischen Ursprung. Inhalt in die Phase des Koordinatensystem über die Begrenzung der 5-Meter gerendert wird jedoch nur stabile angezeigt, während der Benutzer innerhalb dieser Grenze verfügbar ist.

* Hologramme eingefügt, die räumliche Anker relativ zum Hologramme abweichen kann platziert, dabei wird eine andere räumliche Anchortag. Dadurch wird Windows zur Verbesserung der seines Verständnisses der Position der einzelnen räumlichen Anker, auch wenn Sie z. B. ein Anker muss selbst Links anpassen und eine andere Anker rechts anpassen muss.

Im Gegensatz zu einem feststehende Verweisrahmen, die Stabilität in der Nähe der Benutzer immer optimiert ist, stellen Sie sicher die Referenz für Stufe und räumliche Anker Stabilität in der Nähe ihrer Ursprünge. Dadurch, dass diese Hologramme genau an die Stelle im Laufe der Zeit zu bleiben, aber es bedeutet auch, dass Hologramme gerendert zu weit entfernt von einem Koordinatensystem Ursprung zunehmend schwerwiegende Hebel-Arm-Auswirkungen auftreten. Dies ist, da kleine Anpassungen an der Position und Ausrichtung der Stufe oder Anker vergrößert werden werden auf die Entfernung vom, Anker proportional. 

Eine gute Faustregel ist, um sicherzustellen, dass alles, was Sie rendern basierend auf einer entfernten räumliche Anker Koordinatensystem innerhalb von ca. 3 Meter der Ursprungssite. Für einen nahe gelegenen Phase Ursprung entspricht entfernten Wiedergabe des Inhalts "OK", höhere mit Feldern fester Breite Fehler nur auf kleine Hologramme auswirkt, die nicht viel in die Ansicht des Benutzers verschoben wird.

### <a name="spatial-anchor-persistence"></a>Räumliche Anchor-Persistenz

Räumliche Anker können auch Ihre app einen wichtigen Speicherort speichern, auch nach Ihrer app hält oder das Gerät wird heruntergefahren.

Sie können die räumlichen Anker Ihre app erstellt auf dem Datenträger speichern, und Laden sie dann wieder es später noch Mal durch Persistentes Speichern mit Ihrer app **räumliche Premium-Shop**. Beim Speichern oder Laden einen Anker, geben Sie einen Zeichenfolgenschlüssel, der in Ihrer app sinnvoll ist, um den Anker später zu erkennen. Stellen Sie sich diesen Schlüssel als den Dateinamen für den Anker. Wenn Sie andere Daten, Anker zuordnen möchten, z. B. ein 3D-Modell, die der Benutzer an dieser Stelle platziert, speichern Sie, die in den lokalen Speicher Ihrer app, und ordnen sie den Schlüssel an, den Sie ausgewählt haben.

Durch Beibehalten von Textmarken in den Speicher können Ihre Benutzer einzelne Hologramme platzieren oder platzieren Sie einen Arbeitsbereich, die eine app platzieren Sie die verschiedenen Hologramme wird, und suchen Sie dann später die Hologramme, wo sie sie über viele Verwendungen von Ihrer app erwarten.

Können Sie auch <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure räumliche Anker</a> für asynchrone – Hologramm Persistenz für HoloLens, IOS- und Android-Geräte.  Freigeben einer permanenten räumliche cloudankers, können mehrere Geräte das gleiche persistente – Hologramm im Laufe der Zeit beobachten, auch wenn diese Geräte nicht zur gleichen Zeit zusammen vorhanden sind.

### <a name="spatial-anchor-sharing"></a>Räumliche Anker freigeben

Ihre app kann auch einen räumlichen Anker in Echtzeit freigeben für andere Geräte, sodass in Echtzeit Erfahrungen freigegeben.

Mithilfe von <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure räumliche Anker</a>, Ihrer app kann als räumliche Anker dargestellt über mehrere HoloLens, iOS und Android-Geräte freigeben. Dass jedes Gerät, das Rendern ggf. ein Hologramm, der mit dem gleichen Anker für räumliche, sehen alle Benutzer der – Hologramm an derselben Stelle in der realen Welt angezeigt werden.

## <a name="avoid-head-locked-content"></a>Vermeiden Sie Inhalte Head-gesperrt

Wir raten dringend ab, Rendern von Head-locked-Inhalt, der auf einen festen Punkt in der Anzeige (z. B. eine HUD) bleibt. Im Allgemeinen Head-locked Inhalte für Benutzer unangenehm ist und nicht können Sie sich als natürliches Element ihrer Welt.

Head-locked Inhalt sollte in der Regel durch Hologramme ersetzt werden, die für das Anfügen an den Benutzer oder in der ganzen Welt selbst platziert. Z. B. [Cursor](cursors.md) sollten im Allgemeinen werden mithilfe von Push übertragen in der ganzen Welt auf natürliche Weise skalieren, um die Position und die Entfernung des Objekts im des Benutzers Blicke widerzuspiegeln.

## <a name="handling-tracking-errors"></a>Behandeln von Fehlern der nachverfolgung

In einigen Umgebungen wie z. B. dunkel Fluren möglicherweise es nicht möglich, dass eine Kopfhörer mithilfe der nachverfolgung von innen nach außen selbst ordnungsgemäß in der ganzen Welt auffindbar. Dies kann führen, dass Hologramme, die entweder nicht angezeigt oder an falschen Positionen angezeigt werden, wenn falsch verarbeitet. Erörtert, die Bedingungen in denen dies passieren kann, die Auswirkungen auf die benutzerfreundlichkeit, jetzt und Tipps für eine optimale behandelt diese Situation.

### <a name="headset-cannot-track-due-to-insufficient-sensor-data"></a>Kopfhörer kann aufgrund unzureichender Sensordaten nicht nachverfolgen.

In einigen Fällen können sich den Kopfhörer des Sensoren nicht herausfinden, in denen die Kopfhörer ist. Dies kann vorkommen, wenn der Raum dunkel, ist die Sensoren von Haare oder Hände abgedeckt werden, oder wenn die Umgebung nicht über genügend Textur verfügen.

In diesem Fall wird die Kopfhörer nicht nachverfolgen seiner Position mit ausreichender Genauigkeit zum Rendern von Hologramme Welt gesperrt werden. Nicht möglich, herauszufinden, wo eine räumliche Anker, stationär Frame oder Phase Frame relativ zu dem Gerät ist, aber Sie können immer noch gesperrt, Text Inhalt der angefügten Verweisrahmen rendern.

Ihre app sollte dem Benutzer, wie Sie mit Feldern fester Breite nachverfolgen, Rendern von einige fallback gesperrt, Text Inhalt, der beschreibt einige Tipps, wie z. B. Mine die Sensoren und mehr Lichter einschalten erhalten haben.

### <a name="headset-tracks-incorrectly-due-to-dynamic-changes-in-the-environment"></a>Kopfhörer wird fälschlicherweise aufgrund von dynamischen Änderungen in der Umgebung nachverfolgt.

In einigen Fällen kann keine das Gerät ordnungsgemäß nachverfolgt, wenn es viele über dynamische Änderungen in der Umgebung, z. B. viele Personen, die rund um die im Raum durchlaufen. In diesem Fall scheint der Hologramme oder abweichungen, wie das Gerät versucht sich selbst in dieser dynamischen Umgebung nachverfolgen. Es wird empfohlen, das Gerät in einer weniger dynamischen Umgebung verwendet wird, wenn Sie dieses Szenario erreichen.

### <a name="headset-tracks-incorrectly-because-the-environment-has-changed-significantly-over-time"></a>Kopfhörer verfolgt falsch, da die Umgebung im Laufe der Zeit erheblich geändert hat

In einigen Fällen, wenn Sie starten mit einem Kopfhörer eine Umgebung aus, die viele Änderungen vorgenommen wurden (z. B. erhebliche Bewegung Möbel, Wandarmaturen usw.), es ist möglich, dass einige Hologramme verschobenen von ihrem ursprünglichen Speicherort vorkommen. Die früheren Hologramme können auch rund um wechseln, wenn der Benutzer in diesem neuen Bereich bewegt wird, um. Dies ist daran, dass die Systemvariable Überblick über Ihr Speicherplatz nicht mehr enthält, und versucht wird, die Umgebung neu zuordnen, beim Versuch, die Funktionen des Raums abstimmen. In diesem Szenario sollten Benutzer neu platzieren Hologramme ermutigen, die sie in der ganzen Welt angeheftet, wenn sie nicht angezeigt werden, wobei erwartet.

### <a name="headset-tracks-incorrectly-due-to-identical-spaces-in-an-environment"></a>Kopfhörer wird fälschlicherweise aufgrund von identischen Leerzeichen in einer Umgebung nachverfolgt.

In einigen Fällen möglicherweise ein Zuhause oder anderen Space zwei identische Bereiche. Zwei identische Konferenzräume, zwei identische Ecke z. B. Bereiche, zwei große identische Poster, die das Gerät die Sichtfeld abdecken. In solchen Szenarien kann das Gerät in einigen Fällen verwirrt werden, zwischen den Teilen identisch und kennzeichnet sie als in der internen Darstellung identisch. Dies verursacht möglicherweise den Hologramme aus einige Bereiche, die an anderer Stelle angezeigt. Das Gerät möglicherweise verloren gehen, häufig nachverfolgen, da die interne Darstellung der Umgebung beschädigt wurde gestartet. In diesem Fall sollten environmental Verständnis des Systems zurückgesetzt. Beachten Sie, dass das Zurücksetzen der Zuordnung zum Verlust aller räumlichen Anker Platzierungen führt. Dadurch wird die Kopfhörer zum Nachverfolgen von gut in die eindeutige Bereiche der Umgebung. Das Problem kann jedoch erneut auftreten, wenn das Gerät zwischen Bereichen identisch erneut verwechselt ruft.

## <a name="see-also"></a>Siehe auch
* [GDC-2017-Präsentation auf räumliche Koordinatensysteme und holographic rendering](https://channel9.msdn.com/events/GDC/GDC-2017/GDC2017-008)
* [Koordinatensysteme in Unity](coordinate-systems-in-unity.md)
* [Koordinatensysteme in DirectX](coordinate-systems-in-directx.md)
* [Raumanker](spatial-anchors.md)
* [Gemeinsame Erlebnisse in Mixed Reality](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [Fallstudie: Lücken in der Realität ansehen](case-study-looking-through-holes-in-your-reality.md)
