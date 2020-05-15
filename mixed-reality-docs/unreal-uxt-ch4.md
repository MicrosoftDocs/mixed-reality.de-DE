---
title: 4. Interaktives Gestalten der Szene
description: Teil 4 eines Tutorials zum Erstellen einer einfachen Schach-App mit Unreal Engine 4 und dem UX-Tools-Plug-In des Mixed Reality-Toolkits
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Tutorial, erste Schritte, MRTK, UXT, UX Tools, Dokumentation
ms.openlocfilehash: 17f7ab1c1126c47e5ac6388d125d45cf3f2c2d87
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851547"
---
# <a name="3-making-your-scene-interactive"></a>3. Interaktives Gestalten der Szene

Dieser Abschnitt enthält eine Einführung in das Open-Source-basierte UX-Tools-Plug-In des Mixed Reality-Toolkits, das eine Reihe von Tools bietet, mit denen Sie Ihre Szene ganz einfach interaktiv machen können. Am Ende dieses Abschnitts reagieren Ihre Schachfiguren auf Benutzereingaben. 

## <a name="objectives"></a>Ziele

* Integrieren des UX-Tools-Plug-Ins des Mixed Reality-Toolkits in Ihr Projekt
* Hinzufügen von Handinteraktionsakteuren für Ihre Fingerspitzen
* Erstellen von Manipulatoren und Anfügen der Manipulatoren an Ihr Schachbrett und an Ihre Schachfiguren 
* Überprüfen Ihres Projekts mithilfe einer Eingabesimulation

## <a name="download-the-mixed-reality-toolkit-ux-tools-plugin"></a>Herunterladen des UX-Tools-Plug-Ins des Mixed Reality-Toolkits

1.  Klonen Sie das neueste Release des MRTK-UX-Tools-Plug-Ins aus dem [GitHub-Repository für UX-Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases), oder laden Sie es herunter, und entzippen Sie es.

2.  Erstellen Sie im Stammordner Ihres Schachprojekts einen neuen Ordner namens „Plugins“. Kopieren Sie das entzippte UX-Tools-Plug-In in diesen Ordner. Starten Sie den Unreal-Editor neu. 

![Erstellen eines Plug-In-Ordners für das Projekt](images/unreal-uxt/4-plugins.PNG)

3.  Sollten nach dem Neustart in Ihrem Quellenbereich keine Inhalte des UX-Tools-Plug-Ins angezeigt werden, müssen Sie unter Umständen auf **View Options > Show Plugin Content** („Ansichtsoptionen“ > „Plug-In-Inhalt anzeigen) klicken. Wie Sie sehen, verfügt das UX-Tools-Plug-In über einen Inhaltsordner (Content) mit Zeigern (Pointers), Eingabesimulation (InputSimulation) und einer einfachen Taste (SimpleButton) sowie über einen Ordner für C++-Klassen (C++ Classes) mit nach Funktion strukturierten Unterordnern.  

![Anzeigen des Plug-In-Inhalts](images/unreal-uxt/4-showplugincontent.PNG)

## <a name="spawn-hand-interaction-actors"></a>Erzeugen von Handinteraktionsakteuren

1.  Als Erstes erzeugen wir Handinteraktionsakteure auf der Grundlage von „MRPawn“, sodass wir 1) „MRPawn“ mit einem Cursor an den Zeigefingern des Pawns visualisieren, 2) artikulierte Handeingabeereignisse über den Pawn bereitstellen (und somit Akteure direkt manipulieren) und 3) Eingabeereignisse für die Ferninteraktion mithilfe von Handstrahlen bereitstellen können, die von unseren Handflächen ausgehen. Öffnen Sie die Blaupause **MRPawn**, und navigieren Sie zum Ereignisdiagramm (**Event Graph**). 

2.  Ziehen Sie den Ausführungspin von „Event BeginPlay“, und lassen Sie ihn los, um einen neuen Knoten zu platzieren. Wählen Sie den Knoten **Spawn Actor from Class** (Klassenbasierten Akteur erzeugen) aus. Klicken Sie neben dem Pin **Class** (Klasse) auf die Dropdownliste, und suchen Sie nach **Uxt Hand Interaction Actor**. Ziehen Sie den Ausführungspin aus dem Knoten „SpawnActor Uxt Hand Interaction“, lassen Sie ihn los, und suchen Sie nach der Funktion **Set Hand** (Hand festlegen) aus der Klasse „Uxt Hand Interaction Actor“. Verbinden Sie den Rückgabewert (Return Value) des Knotens „SpawnActor“ mit dem Zielpin (Target) des Knotens „Set Hand“ (Hand festlegen), um die Hand des Handinteraktionsakteurs auf **Left** (Links) festzulegen. Erzeugen Sie einen zweiten Knoten vom Typ **Uxt Hand Interaction Actor**, legen Sie die Hand diesmal aber auf **Right** (Rechts) fest, damit zu Beginn des Ereignisses für jede Hand ein UXT-Handinteraktionsakteur erzeugt wird. 

![Erzeugen von UXT-Handinteraktionsakteuren](images/unreal-uxt/4-spawnactor.PNG)

3.  Als Nächstes müssen die UXT-Handinteraktionsakteure mit einer anfänglichen Transformation für die Erzeugung sowie mit einem Besitzer versehen werden. Ziehen Sie den Pin aus einem der Pins vom Typ **Spawn Transform** (Erzeugungstransformation), und lassen Sie ihn los, um einen neuen Knoten zu platzieren. Suchen Sie nach dem Knoten **Make Transform** (Transformation erstellen). Die anfängliche Transformation spielt keine Rolle, da die Handinteraktionsakteure sofort zu unseren Händen wechseln, sobald sie sichtbar sind. (Der entsprechende Code wurde bereits im UX-Tools-Plug-In für uns geschrieben.) Andernfalls verschwinden sie. Für die Funktion „SpawnActor“ ist jedoch eine Transformation als Eingabe erforderlich, um einen Compilerfehler zu vermeiden. Daher werden hier in „Make Transform“ (Transformation erstellen) einfach die Standardwerte übernommen. Ziehen Sie den Rückgabewert (**Return Value**) von „Make Transform“ (Transformation erstellen) auch zur Erzeugungstransformation des Interaktionsakteurs der anderen Hand. 

4.  Klicken Sie im unteren Bereich beider Knoten vom Typ „SpawnActor“ auf den **Pfeil nach unten**, um den Pin **Owner** (Besitzer) anzuzeigen. Ziehen Sie den Pin aus einem der Pins vom Typ **Owner** (Besitzer), und lassen Sie ihn los, um einen neuen Knoten zu platzieren. Suchen Sie nach „self“, und wählen Sie die Variable **Get a reference to self** (Selbstverweis abrufen) aus. Erstellen Sie auch eine Verknüpfung zwischen dem Objektverweisknoten für „Self“ und dem Besitzerpin des anderen Handinteraktionsakteurs. Sie können die Knoten gerne verschieben, um die Blaupause übersichtlicher zu machen. **Kompilieren** und **speichern** Sie Ihre Arbeit, und kehren Sie anschließend zum Hauptfenster zurück. 

![Abschließen der Einrichtung der UXT-Handinteraktionsakteure](images/unreal-uxt/4-fingerptrs.PNG)

Weitere Informationen zum Handinteraktionsakteur aus dem MRTK-UX-Tools-Plug-In finden Sie in der offiziellen [Dokumentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/HandInteraction.html).

## <a name="attach-manipulators"></a>Anfügen von Manipulatoren

1.  Als Nächstes fügen wir Manipulatoren an unser Schachbrett und an die Königsaktoren an. Bei einem Manipulator handelt es sich um eine Komponente, die auf eine artikulierte Handeingabe reagiert und gegriffen, gedreht und verschoben werden kann. Durch Anwenden der Transformation des Manipulators auf die eines Akteurs können Akteure direkt manipuliert werden. 

2.  Öffnen Sie Ihre Blaupause mit dem Namen „Board“. Klicken Sie im Bereich **Components** (Komponenten) auf **Add Component** (Komponente hinzufügen), und suchen Sie nach **Uxt Generic Manipulator** (Generischer UXT-Manipulator). Im Detailbereich befindet sich der Abschnitt **Generic Manipulator** (Generischer Manipulator). Dort können Sie festlegen, ob Sie eine ein- oder zweihändige Manipulation ermöglichen möchten, und Sie können den Rotationsmodus und die Glättung festlegen. Wählen Sie die gewünschten Modi aus, und **kompilieren** und **speichern** Sie „Board“. 

![Hinzufügen eines generischen Manipulators](images/unreal-uxt/4-addmanip.PNG)

![Festlegen des Modus](images/unreal-uxt/4-setrotmode.PNG)

3.  Wiederholen Sie die obigen Schritte für den Akteur „WhiteKing“.

Weitere Informationen zu den Manipulatorkomponenten aus dem MRTK-UX-Tools-Plug-In finden Sie in der offiziellen [Dokumentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/Manipulator.html).

## <a name="test-out-your-scene-with-simulated-hands"></a>Testen Ihrer Szene mit simulierten Händen

1.  Klicken Sie im Hauptfenster auf **Play** (Spielen). Daraufhin sollten zwei Gitterhände aus dem MRTK-UX-Tools-Plug-In angezeigt werden, bei denen jeweils ein Handstrahl von der Handfläche ausgeht. 

![Simulierte Hände im Viewport](images/unreal-uxt/4-handsim.PNG)

2.  Halten Sie zum Steuern der **rechten Hand** die **linke ALT-TASTE** gedrückt. Bewegen Sie die Maus, um die Hand zu bewegen. Scrollen Sie mit dem **Mausrad**, um die Hand **vor** oder **zurück** zu bewegen. Klicken Sie zum **Zusammendrücken** mit der linken Maustaste und zum **Anstupsen** mit der mittleren Maustaste.

3.  Halten Sie zum Steuern der **linken Hand** die **linke UMSCHALTTASTE** gedrückt. Die linke Hand wird auf die gleiche Weise gesteuert wie die rechte. 

4.  Verwenden Sie nun die simulierten Hände, um den weißen König aufzunehmen, zu bewegen und abzusetzen. Sie können auch mit dem Schachbrett interagieren. Experimentieren Sie sowohl mit der Nah- als auch mit der Ferninteraktion, und beachten Sie dabei, dass der Handstrahl verschwindet und durch einen Fingercursor an der Spitze des Zeigefingers ersetzt wird, wenn die Hand dem Schachbrett oder dem König nahe genug ist, um direkt damit zu interagieren. 

Weitere Informationen zu den simulierten Händen aus dem MRTK-UX-Tools-Plug-In finden Sie in der offiziellen [Dokumentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.8.x/Docs/InputSimulation.html).

[Nächster Abschnitt: 5. Hinzufügen einer Taste und Zurücksetzen von Figurenpositionen](unreal-uxt-ch5.md)