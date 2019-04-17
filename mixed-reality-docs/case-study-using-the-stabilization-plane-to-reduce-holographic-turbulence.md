---
title: 'Fallstudie: verwenden die Ebene der Stabilisierung zum Reduzieren von holographic Turbulenzen'
description: Verwenden die Ebene der Stabilisierung zum Reduzieren von holographic Turbulenzen
author: bstrukus
ms.author: bestruku
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Hologramme, Stabilisierung, Fallstudie
ms.openlocfilehash: a084ede5f9bf3d5f058cc81ec75840e2c2e75af2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593237"
---
# <a name="case-study---using-the-stabilization-plane-to-reduce-holographic-turbulence"></a>Fallstudie: verwenden die Ebene der Stabilisierung zum Reduzieren von holographic Turbulenzen

Arbeiten mit Hologramme kann schwierig sein. Die Tatsache, dass können Sie Ihrem Bereich verschieben und Ihre Hologramme aus allen verschiedenen Blickwinkeln bietet eine Immersion, die mit einem normalen Computerbildschirm nicht erreicht werden kann. Halten diese Hologramme vorhanden, und suchen realistisch ist eine technische Leistung erreicht, indem sowohl die Hardware für Microsoft HoloLens und intelligente Gestaltung der holographic apps.

## <a name="the-tech"></a>Der Technologie

Damit wird Hologramme Eindruck, dass sie tatsächlich den Platz für Sie freigegeben haben, sollten sie ordnungsgemäß ohne farbliche Trennung ordnungsgemäß gerendert. Dies wird erreicht, teilweise von der Technologie, die in der HoloLens-Hardware, die behält Hologramme sind in der sogenannten verankert integriert eine [Stabilisierung Ebene](hologram-stability.md#stabilization-plane).

Eine Ebene wird durch einen Punkt und ein normaler definiert, aber da wir immer auf die Ebene auf die Kamera soll, wir eigentlich nur sorgen beim Festlegen der Ebene der Punkt. Können wir teilen HoloLens der zeigen Sie auf die Verarbeitung bei Keep konzentrieren, die alles verankert und stabilen, aber wie diesem Zeitpunkt fokusmodus festgelegt ist app-spezifisch ist, und kann oder unterbrechen Sie Ihre app je nach Inhalt.

Kurz gesagt, Hologramme funktioniert am besten, wenn die Ebene der Stabilisierung ordnungsgemäß angewendet wird, aber welche, die tatsächlich bedeutet, dass hängt von der Art der Anwendung, die Sie erstellen. Werfen wir einen Blick, wie einige der apps für HoloLens derzeit verfügbar. dieses Problem zu lösen.

## <a name="behind-the-scenes"></a>Im Hintergrund

Wenn Sie die folgenden apps zu entwickeln, haben wir festgestellt, wenn wir die Ebene keine verwendet haben, Objekte sway würde, wenn unseren Kopf verschoben, und wir farbliche Trennung mit schnellen Head oder – Hologramm Bewegungen sehen. Im Laufe des Zeitraums für die Entwicklung haben Sie erfahren, durch Versuch und Irrtum wie die Stabilisierung Ebene optimal genutzt und unsere apps rund um die Probleme zu entwerfen, die nicht behoben werden konnten.

### <a name="galaxy-explorer-stationary-content-3d-interactivity"></a>Galaxy-Explorer: Stationär Inhalt 3D-Interaktivität

[Galaxy Explorer](galaxy-explorer.md) umfasst zwei wesentliche Elemente in der Szene: Die Hauptansicht der astronomischer Inhalte und der kleine UI-Symbolleiste, die Ihre Blicke folgt. Für die Stabilisierung-Logik betrachten wir Ihre aktuellen Blicke Vektor mit in jedem Frame aus, um festzustellen, ob er etwas auf einer Ebene angegebene Konflikt erreicht überschneidet. In diesem Fall werden die Ebenen, die wir würden gern Planeten, fällt Ihre Blicke einer Welt, die Stabilisierung-Ebene gibt es platziert. Wenn keines der Objekte in der Kollisionen Zielebene erreicht werden, verwendet die app eine Ebene sekundären "Plan B". Wenn nichts am gazed ist, bleibt die Stabilisierung-Ebene die gleiche Distanz, wie der Inhalt gazing angezeigt wurde. Die UI-Tools sind als Ziel Ebene ausgelassen, wie wir den Unterschied zwischen in der Nähe finden und weit die Stabilität der gesamten Szene reduziert.

Der Entwurf des Galaxy-Explorers ist gut für die Dinge stabil zu halten und verringert die Auswirkungen der Trennung der Farbe. Der Benutzer wird ermutigt zu aufzusuchen, und den Inhalt orbit statt auf sie von rechts zu verschieben und Planeten sind langsam genug, dass die farbliche Trennung merkliche nicht einsetzen. Darüber hinaus wird eine Konstante 60 FPS verwaltet, die reicht weit verhindert farbliche Trennung geschieht.

Um dies selbst zu überprüfen, suchen Sie nach einer Datei namens LSRPlaneModifier.cs in die [Galaxy-Explorer-Code auf GitHub](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities).

### <a name="holostudio-stationary-content-with-a-ui-focus"></a>HoloStudio: Stationär Inhalt mit dem UI-Schwerpunkt

In HoloStudio verbringen Sie die meiste Ihrer Zeit mit der Suche unter dem gleichen Modell Sie arbeiten. Ihre Blicke verschieben nicht viel, mit Ausnahme von, wenn Sie ein neues Tool auswählen oder die Benutzeroberfläche zu navigieren, damit wir die Einstellung der Datenebene Logik einfach halten können. Bei Betrachtung die Benutzeroberfläche wird die Ebene an den UI-Element festgelegt, die Ihre Blicke ausgerichtet wird. Wenn Sie das Modell zu suchen, ist die Ebene einer festgelegten Entfernung, mit den Standardabstand zwischen Sie und das Modell entspricht.

![Die Ebene für die Stabilisierung in visualisiert HoloStudio als der Benutzer auf die Schaltfläche "Home" gazes](images/holostudio-stabilization-plane-500px.png)

### <a name="holotour-and-3d-viewer-stationary-content-with-animation-and-movies"></a>HoloTour und 3D-Viewer: Animation und Filme stationär Inhalt

In HoloTour und 3D Viewer können entdecken Sie ein einzelne animierte Objekt oder einen Film mit 3D-Effekte darauf hinzugefügt. Die snapshotisolierung in diesen apps ist festgelegt, was Sie gerade anzeigen.

HoloTour verhindert, dass auch Sie straying zu weit entfernt von Ihrer virtuellen Welt, dass für Sie zu verschieben, anstatt einer festen Position dashboardkontext zu verlassen. Dadurch wird sichergestellt, dass Sie weit genug von anderen Hologramme für Stabilitätsprobleme einschleichen erhalten.

![In diesem Beispiel aus HoloTour würde die Stabilisierung-Ebene zu diesem Film von Hadrians Pantheon festgelegt werden.](images/holotour-stabilization-plane-500px.jpg)

### <a name="roboraid-dynamic-content-and-environmental-interactions"></a>RoboRaid: Dynamischen Inhalt und environmental Interaktionen

Festlegen der Stabilisierung-Ebene in RoboRaid ist erstaunlich einfach, obwohl Sie die app, die die meisten plötzliche Bewegung ist erforderlich. Die Ebene auf das Festhalten an die Wände zugeschnitten ist, oder die umgebenden Objekte und wird in einem festen Abstand vor Ihnen float, wenn Sie nicht diese weit genug sind.

RoboRaid wurde entworfen, mit der Stabilisierung Ebene Bedenken. Das Fadenkreuz, das am häufigsten verschoben wird, da es die Head-gesperrt ist, umgeht dies mit nur Red Team und Blue, wodurch jede Farbe Entbluten reduziert wird. Sie enthält auch ein wenig Tiefe zwischen Komponenten implementiert, minimieren jede Farbe Anschnitt, die auftreten würden, indem sie mit einem bereits erwarteten Parallaxeneffekt maskiert. Roboter nicht sehr schnell zu verschieben und übertragen nur kurze Distanzen in regelmäßigen Abständen. Neigen dazu, bleiben etwa 2 Zähler vor Ihnen, in denen die snapshotisolierung wird standardmäßig festgelegt.

### <a name="fragments-and-young-conker-dynamic-content-with-environmental-interaction"></a>Fragmente und jungen Conker: Dynamischer Inhalte mithilfe von environmental Interaktion

Geschrieben von Asobo Studio in C++, Fragmente und Young Conker gehen hier anders heran die Stabilisierung-Ebene festlegen. Zeigt interessanten (Ort POI) sind im Code definiert und hinsichtlich der Priorität sortiert. POIs sind in-Game-Inhalt wie das Modell Conker in Young Conker, Menüs, die darauf abzielen-Fadenkreuz und Logos. Der POIs werden von des Benutzers Blicke geschnitten wurde, und die Ebene in der Mitte des Objekts mit der höchsten Priorität festgelegt ist. Wenn keine Überschneidung auftritt, wird die Ebene, auf den Standardabstand festgelegt.

Fragmente und Young Conker können Sie auch entwerfen, um Sie zu weit von der Hologramme durch das Anhalten der app, wenn Sie außerhalb von was zuvor als Ihre Play Leerzeichen gescannt wurde verschieben straying. Daher ist es möglich, halten sie Sie innerhalb der Grenzen, die gefunden werden, um den stabilsten Erlebnis zu bieten.

## <a name="do-it-yourself"></a>Es selbst tun.

Wenn Sie eine HoloLens haben und mit den Konzepten von mir behandelten experimentieren möchten, können eine Test-Szene herunterladen und Testen Sie die folgenden Übungen. Unity integrierte VoIP (Gizmo) API verwendet, und sie sollten Ihnen helfen, zu visualisieren, in dem die Ebene festgelegt wird. Dieser Code wurde auch verwendet, um die Screenshots in dieser Fallstudie zu erfassen.
1. Synchronisieren Sie die neueste Version des [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity).
2. Öffnen der [HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity) Szene.
3. Erstellen Sie und konfigurieren Sie das erstellte Projekt.
4. Führen Sie auf Ihrem Gerät.

### <a name="exercise-1"></a>Übung 1

Sie sehen, dass mehrere weiße Punkten unter verschiedenen Ausrichtungen für Sie. Vor Ihnen sehen Sie drei Punkte in anderen Ebenen. Tippbewegung so ändern Sie die dot-Ebene wird festgelegt. Navigieren Sie für diese Übung, und für die beiden anderen, Ihren Space gazing auf die Punkte. Aktivieren Sie Ihre Head links, rechts, oben und unten. Verschieben Sie näher an und Vater von die Punkte ein. Sehen Sie, wie sie reagieren, wenn die Ebene der Stabilisierung an verschiedenen Ziele festgelegt ist.

### <a name="exercise-2"></a>Übung 2

Aktivieren Sie nun auf der rechten Seite, bis Sie sehen, dass zwei Punkte verschieben, eine für eine horizontale Pfad und die auf einer vertikale Pfad oszilliert. Auch hier-tippbewegung um welche Punkt zu ändern, auf die Ebene festgelegt ist. Beachten Sie, wie farbliche Trennung weniger problematisch ist, wird auf den Punkt, der eine Verbindung mit der Ebene besteht angezeigt. Tippen Sie erneut, um den Punkt der Geschwindigkeit in der Datenebene Einstellung-Funktion zu verwenden. Dieser Parameter enthält einen Hinweis, HoloLens, zum gewünschten Bewegung des Objekts. Es ist wichtig, Verwendung wissen, wie Sie feststellen, wenn der Velocity auf einen Punkt verwendet wird, wird der andere gleitende Punkt stärkere Trennung der Farbe angezeigt. Beachten Sie, dass beim Entwickeln Ihrer apps – müssen zusammenhängende Flows, um die Bewegung Ihrer Objekte können verhindern, dass Elemente angezeigt wird.

### <a name="exercise-3"></a>Übung 3

Aktivieren Sie auf der rechten Seite einmal bis eine neue Konfiguration der Punkte angezeigt. Es gibt in diesem Fall Punkte bei der Entfernung und eines Punkts steigende ein-und direkt vor ihnen. Luft Tippen Sie auf der Punkt ändern die Ebene auf festgelegt ist, die Punkte in die Sicherung und der Punkt in Bewegung abwechselnd an. Beachten Sie, wie das Festlegen der Datenebene und die Geschwindigkeit, mit der stetig steigende Punkt macht Artefakte, die überall angezeigt werden.

**Tipps**
* Halten Sie Ihre Datenebene Einstellung Logik einfach. Wie Sie gesehen haben, benötigen Sie keine komplexen Ebene Einstellung Algorithmen die ein eintauchen. Die Stabilisierung-Ebene ist nur ein Teil im Puzzle.
* Wenn bei der alle möglichen immer verschieben Sie die Ebene zwischen Ziele reibungslos. Wechseln sofort entfernten Ziele kann visuell die Szene stören.
* Erwägen Sie, dass eine Option, in der Datenebene Einstellung Logik, auf ein sehr spezifisches Ziel zu sperren. Auf diese Weise können Sie die Ebene, die auf ein Objekt, z. B. einem Logo oder Titel-Bildschirm, gesperrt lassen, bei Bedarf.

## <a name="about-the-author"></a>Der Autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Ben Strukus" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Ben Strukus</b><br>Anwendungsentwickler @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Siehe auch
* [MR Basics 100: Erste Schritte mit Unity](holograms-100.md)
* [Fokuspunkt in Unity](focus-point-in-unity.md)
* [– Hologramm Stabilität](hologram-stability.md)
