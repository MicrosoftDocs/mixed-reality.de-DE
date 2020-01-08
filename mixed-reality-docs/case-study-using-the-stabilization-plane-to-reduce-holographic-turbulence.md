---
title: 'Fallstudie: Verwenden der Stabilisierungs Ebene zum Reduzieren von Holographic-Turbulenzen'
description: Verringern von Holographic-Turbulenzen mithilfe der Stabilisierungs Ebene
author: bstrukus
ms.author: bestruku
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, holograms, Stabilisierung, Fallstudie
ms.openlocfilehash: 039b8f671f02a27393c30c7954cf0e2925635ad0
ms.sourcegitcommit: d0da0214fdd2bbac5a91a5d895bf0e87413b29b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597653"
---
# <a name="case-study---using-the-stabilization-plane-to-reduce-holographic-turbulence"></a>Fallstudie: Verwenden der Stabilisierungs Ebene zum Reduzieren von Holographic-Turbulenzen

Das Arbeiten mit holograms kann schwierig sein. Die Tatsache, dass Sie Ihren Raum verschieben und die Hologramme aus allen verschiedenen Winkeln anzeigen können, bietet eine Ebene des einfügebens, die Sie nicht mit einem normalen Computerbildschirm erreichen können. Die Beibehaltung dieser Hologramme und die realistische Betrachtung ist eine technische Aufgabe, die sowohl von der Hardware von Microsoft hololens als auch vom intelligenten Entwurf von Holographic apps durchgeführt wird.

## <a name="the-tech"></a>Die Technologie

Damit holograms angezeigt werden, als ob Sie den Platz tatsächlich mit Ihnen teilen, sollten Sie ohne Farbtrennung ordnungsgemäß Rendering werden. Dies wird teilweise durch Technologie integriert, die in die hololens-Hardware integriert ist, die holograms auf der [Ebene der Stabilisierungs Ebene](hologram-stability.md#reprojection)verankert hält.

Eine Ebene wird durch einen Punkt und einen normalen definiert, aber da wir immer die Ebene mit der Kamera machen möchten, ist es wirklich wichtig, den Punkt der Ebene festzulegen. Hololens können darauf hinweisen, dass Sie sich auf die Verarbeitung konzentrieren, damit alles verankert und stabil bleibt, aber wie dieser Fokuspunkt festgelegt wird, ist APP-spezifisch und kann Ihre APP je nach Inhalt erstellen oder unterbrechen.

Kurz gesagt: holograms funktionieren am besten, wenn die Stabilisierungs Ebene ordnungsgemäß angewendet wird, aber was eigentlich bedeutet, hängt von der Art der Anwendung ab, die Sie erstellen. Werfen wir einen Blick darauf, wie einige der derzeit für hololens verfügbaren apps dieses Problem beheben.

## <a name="behind-the-scenes"></a>Im Hintergrund

Beim Entwickeln der folgenden apps haben wir festgestellt, dass sich die Objekte, wenn wir die Ebene nicht verwendet haben, bei der Bewegung des Kopfes bewegen und die Farbtrennung mit Quick Head-oder – Hologramm-Bewegungen angezeigt würden. Im Laufe des Entwicklungs Zeitraums haben wir uns mit der Testversion und dem Fehler vertraut gemacht, wie Sie die Stabilisierungs Ebene am besten nutzen können und wie Sie unsere apps auf die Probleme entwerfen können, die nicht behoben werden können.

### <a name="galaxy-explorer-stationary-content-3d-interactivity"></a>Galaxy Explorer: stationärer Inhalt, 3D-Interaktivität

Der [Galaxy Explorer](galaxy-explorer.md) verfügt über zwei wichtige Elemente in der Szene: die Hauptansicht des Himmels Inhalts und die kleine UI-Symbolleiste, die auf Ihren Blick folgt. Bei der Stabilisierungs Logik sehen wir uns an, was Ihr aktueller Blick Vektor in jedem Frame schneidet, um zu bestimmen, ob er auf eine angegebene Kollisions Ebene trifft. In diesem Fall sind die Ebenen, an denen wir interessiert sind, die Planeten. wenn der Blick auf einen Planeten fällt, wird die Stabilisierungs Ebene dort platziert. Wenn keines der Objekte in der Ziel Kollisions Schicht auftritt, verwendet die APP eine sekundäre "Plan B"-Ebene. Wenn nichts in der-Datei gespeichert wird, wird die Stabilisierungs Ebene in derselben Entfernung wie bei der Betrachtung des Inhalts beibehalten. Die UI-Tools werden als Ziel der Ebene ausgelassen, da der Sprung zwischen nahezu und weit reduzierter Stabilität der gesamten Szene gefunden wurde.

Der Entwurf von Galaxy Explorer eignet sich gut, um die Dinge stabil zu halten und die Auswirkungen der Farbtrennung zu verringern. Der Benutzer wird empfohlen, den Inhalt zu durchlaufen und zu umbrechen, anstatt ihn von der Seite zu einem anderen zu verschieben, und die-Planeten werden langsam genug umkreist, dass die Farbtrennung nicht erkennbar ist. Außerdem wird eine Konstante 60 fps gewartet, die eine lange Weise verhindert, dass die Trennung von Farben stattfindet.

Um dies selbst zu überprüfen, suchen Sie im [Galaxy Explorer-Code auf GitHub](https://github.com/Microsoft/GalaxyExplorer/tree/master/Assets/Scripts/Utilities)nach einer Datei namens LSRPlaneModifier.cs.

### <a name="holostudio-stationary-content-with-a-ui-focus"></a>Holostudio: stationärer Inhalt mit einem UI-Fokus

In holostudio verbringen Sie den größten Teil ihrer Zeit mit dem gleichen Modell, an dem Sie gerade arbeiten. Wenn Sie ein neues Tool auswählen oder die Benutzeroberfläche durch die Benutzeroberfläche navigieren möchten, wird Ihr Blick nicht erheblich verlagert. Wenn Sie die Benutzeroberfläche betrachten, wird die Ebene auf das beliebige Benutzeroberflächen Element festgelegt, an das Ihr Blick gerichtet ist. Wenn Sie das Modell betrachten, ist die Ebene eine Menge Distanz, die dem Standardabstand zwischen Ihnen und dem Modell entspricht.

![Die Stabilisierungs Ebene, die in holostudio visualisiert wird, während der Benutzer auf der Start Schaltfläche angezeigt wird.](images/holostudio-stabilization-plane-500px.png)

### <a name="holotour-and-3d-viewer-stationary-content-with-animation-and-movies"></a>Holotour und 3D-Viewer: stationärer Inhalt mit Animation und Filmen

Im holotour-und 3D-Viewer sehen Sie sich ein einzelnes animiertes Objekt oder einen Film an, auf dem zusätzlich 3D-Effekte hinzugefügt werden. Die Stabilisierung in diesen Apps ist auf das, was Sie gerade anzeigen, festgelegt.

Mit holotour wird auch verhindert, dass Sie sich zu weit von Ihrer virtuellen Welt entfernen, da Sie sich nicht an einem festes Ort befinden. Dadurch wird sichergestellt, dass Sie nicht von anderen Hologrammen entfernt werden, um Stabilitätsprobleme zu erzielen.

![In diesem Beispiel von holotour würde die Stabilisierungs Ebene auf diesen Film von Hadrian Pantheon festgelegt werden.](images/holotour-stabilization-plane-500px.jpg)

### <a name="roboraid-dynamic-content-and-environmental-interactions"></a>Roboraid: dynamische Inhalte und Umgebungs Interaktionen

Das Festlegen der Stabilisierungs Ebene in roboraid ist erstaunlich einfach, obwohl es sich um die APP handelt, die eine möglichst plötzliche Bewegung erfordert. Die Ebene ist darauf ausgerichtet, auf die Wände oder die umgebenden Objekte zu gelangen, und wird in einer festgelegten Entfernung angezeigt, wenn Sie weit genug sind.

Roboraid wurde mit der Stabilisierungs Ebene entworfen. Der Reticle, der den größten Teil nach der Überschrift bewegt, umgeht dies, indem er nur rot und Blau verwendet, wodurch die Farb Blutungen minimiert werden. Sie enthält auch ein kleines tiefgehende Tiefe zwischen den einzelnen Elementen. Dadurch werden alle Farb verblutungs Elemente minimiert, die durch eine Maskierung mit einem bereits erwarteten parameteffekt auftreten würden. Die Roboter werden nicht sehr schnell verschoben, und es werden nur kurze Entfernungen in regelmäßigen Abständen übertragen. Sie bleiben in der Regel um 2 Meter vor Ihnen, wo die Stabilisierung standardmäßig festgelegt ist.

### <a name="fragments-and-young-conker-dynamic-content-with-environmental-interaction"></a>Fragmente und junge Zusammenspiel: dynamischer Inhalt mit Umgebungs Interaktion

Der von Asobo Studio in C++geschriebene Fragmente und der junge-Manager Unternehmen einen anderen Ansatz beim Festlegen der Stabilisierungs Ebene. Relevante Punkte (POI) werden im Code definiert und im Hinblick auf die Priorität geordnet. POIs sind in-Game-Inhalten, z. b. das-Verbindungs Modell in jungen-,-Menüs, das Ziel-Reticle und Logos. Die POIs werden durch den Benutzer Blick geschnitten, und die Ebene wird auf den Mittelpunkt des Objekts mit der höchsten Priorität festgelegt. Wenn keine Schnittmenge auftritt, wird die Ebene auf die Standard Entfernung festgelegt.

Fragmente und junge-Anker entwerfen Sie auch, wenn Sie sich zu weit von den holograms bewegen, indem Sie die APP anhalten, wenn Sie sich außerhalb der Inhalte befinden, die bereits als Wiedergabe Raum gescannt wurden. Daher behalten Sie Sie in den Grenzen, die für eine stabilere Benutzerfunktion gefunden werden.

## <a name="do-it-yourself"></a>Aufzeichnung in Eigenregie

Wenn Sie über ein hololens verfügen und mit den Konzepten in diesem Artikel experimentieren möchten, können Sie eine Test Szene herunterladen und die unten beschriebenen Übungen ausprobieren. Es verwendet die integrierte Gizmo-API von Unity und sollte Ihnen helfen, den Speicherort ihrer Ebene visuell darzustellen. Dieser Code wurde auch verwendet, um die Screenshots in dieser Fallstudie aufzuzeichnen.
1. Synchronisieren Sie die neueste Version von [mixedrealitytoolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity).
2. Öffnen Sie die [HoloToolkit-examples/Utilities/Szenen/stabilizationplaneseup. unity-](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Scenes/StabilizationPlaneSetting.unity) Szene.
3. Erstellen und konfigurieren Sie das generierte Projekt.
4. Führen Sie auf Ihrem Gerät aus.

### <a name="exercise-1"></a>Übung 1

In verschiedenen Ausrichtungen werden Ihnen mehrere weiße Punkte angezeigt. Vor Ihnen sehen Sie drei Punkte in unterschiedlicher Tiefe. Tippen Sie darauf, um den Punkt zu ändern, auf den die Ebene festgelegt ist. Bewegen Sie sich für diese Übung und für die anderen beiden Bereiche um Ihren Bereich, während Sie auf die Punkte schauen. Drehen Sie den Kopf Links, rechts, oben und unten. Verschieben Sie die Punkte näher und weiter. Sehen Sie, wie Sie reagieren, wenn die Stabilisierungs Ebene auf verschiedene Ziele festgelegt ist.

### <a name="exercise-2"></a>Übung 2

Wechseln Sie jetzt nach rechts, bis zwei verschiebende Punkte angezeigt werden, von denen eine auf einem horizontalen Pfad und einer auf einem vertikalen Pfad liegt. Tippen Sie erneut auf, um den Punkt zu ändern, auf den die Ebene festgelegt ist. Beachten Sie, dass die Farbtrennung verringert wird und auf dem Punkt angezeigt wird, der mit der Ebene verbunden ist. Tippen Sie erneut, um die Geschwindigkeit des Punkts in der setupsetting-Funktion zu verwenden. Dieser Parameter gibt hololens über die beabsichtigte Bewegung des Objekts an. Es ist wichtig zu wissen, wann dies zu tun ist. wie Sie sehen werden, wenn die Geschwindigkeit bei einem Punkt verwendet wird, wird für den anderen verschiebenden Punkt eine größere Farbtrennung angezeigt. Berücksichtigen Sie dies beim Entwerfen Ihrer Apps – Wenn Sie einen zusammenhängenden Fluss für die Bewegung ihrer Objekte haben, können Sie verhindern, dass Artefakte angezeigt werden.

### <a name="exercise-3"></a>Übung 3

Wenn Sie eine neue Konfiguration der Punkte sehen, können Sie auf das Recht klicken. In diesem Fall gibt es Punkte in der Entfernung und einen Punkt vor und nach oben. Tippen Sie auf die Linie, um den Punkt zu ändern, auf den die Ebene festgelegt ist, und wechseln Sie zwischen den Punkten im Hintergrund und dem Punkt in Bewegung. Beachten Sie, dass das Festlegen der Position der Ebene und der Geschwindigkeit, mit der der spiralförmige Punkt aussieht, Artefakte überall angezeigt werden.

**Tipps**
* Sorgen Sie dafür, dass die Logik der Ebene einfach ist. Wie Sie gesehen haben, benötigen Sie keine komplexen Ebenen-Einstellungs Algorithmen, um eine immersive Erfahrung zu erzielen. Die Stabilisierungs Ebene ist nur ein Teil des Rätsels.
* Wenn möglich, sollten Sie die Ebene immer zwischen Zielen problemlos verschieben. Das sofortige wechseln entfernter Ziele kann die Szene visuell stören.
* Ziehen Sie in Erwägung, eine Option in der Ebene festzulegen, mit der Logik auf ein bestimmtes Ziel gesperrt werden soll. Auf diese Weise können Sie bei Bedarf die Ebene für ein Objekt, z. b. ein Logo oder einen Titelbildschirm, sperren.

## <a name="about-the-author"></a>Über die Autorin

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Ben Strukus" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><b>Ben strukus</b><br>Software Entwickler @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Weitere Informationen:
* [Grundlagen 100: Einstieg in Unity](holograms-100.md)
* [Fokuspunkt in Unity](focus-point-in-unity.md)
* [Hologrammstabilität](hologram-stability.md)
