---
title: 3. Einrichten Ihres Projekts für Mixed Reality
description: Teil 3 eines Tutorials zum Erstellen einer einfachen Schach-App mit der Unreal Engine 4 und dem UX-Tools-Plug-In des Mixed Reality-Toolkits
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Tutorial, erste Schritte, MRTK, UXT, UX Tools, Dokumentation
ms.openlocfilehash: b5b5e2de787279602341e60f2bfa29aa05ea9b31
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840619"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a>3. Einrichten Ihres Projekts für Mixed Reality

In diesem Abschnitt erfahren Sie Schritt für Schritt, wie Sie Ihre App für die Mixed Reality-Entwicklung konfigurieren. 

## <a name="objectives"></a>Ziele

* Einrichten eines Mixed Reality-Projekts mit „ARSessionConfig“, Pawn und „GameMode“

## <a name="configure-the-session"></a>Konfigurieren der Sitzung

1. Navigieren Sie im Inhaltsbrowser wieder zum Ordner **Content**. Klicken Sie auf **Add New > Miscellaneous > Data Asset** („Neu hinzufügen“ > „Sonstiges“ > „Datenressource“). 

2. Wählen **ARSessionConfig** als Klasse aus, und klicken Sie auf **Select** (Auswählen). Nennen Sie die Ressource „ARSessionConfig“.

![Erstellen einer Datenressource](images/unreal-uxt/3-createasset.PNG)

3. Doppelklicken Sie auf „ARSessionConfig“, um die Ressource zu öffnen. Die Datenressource „ARSessionConfig“ enthält eine Reihe praktischer AR-Einstellungen wie räumliche Abbildung und Verdeckung. Ausführlichere Informationen zu „ARSessionConfig“ finden Sie in der Unreal Engine-Dokumentation zu [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html). Da für die Schach-App keine Einstellungen geändert werden müssen, können Sie einfach auf **Save** (Speichern) klicken und zum Hauptfenster zurückkehren. 

![AR-Sitzungskonfiguration](images/unreal-uxt/3-arsessionconfig.PNG)

4. Klicken Sie auf der Symbolleiste über dem Viewport auf **Blueprints > Open Level Blueprint** („Blaupausen“ > „Levelblaupause öffnen“). Bei der Levelblaupause handelt es sich um eine spezielle Blaupause, die als levelweites globales Ereignisdiagramm fungiert. Hier starten wir eine AR-Sitzung, damit unsere AR-Sitzungskonfiguration beim Starten des Levels angewendet wird.  

5. Ziehen Sie den Ausführungsknoten aus **Event BeginPlay** (Ereignis „BeginPlay“), und lassen Sie ihn los. Suchen Sie nach dem Knoten **Start AR Session** (AR-Sitzung starten). Klicken Sie auf **Session Config** (Sitzungskonfiguration), und wählen Sie die neu erstellte Ressource **ARSessionConfig** aus. Klicken Sie auf **Compile** (Kompilieren) und anschließend auf **Save** (Speichern). Kehren Sie zum Hauptfenster zurück.

![Starten der AR-Sitzung](images/unreal-uxt/3-startarsession.PNG)

## <a name="create-a-pawn"></a>Erstellen eines Pawns

1.  Erstellen Sie im Ordner „Content“ eine neue Blaupause, die von **DefaultPawn** erbt. In Unreal stellt ein Pawn den Benutzer im Spiel (oder in diesem Fall: in der HoloLens 2-Umgebung) dar. Benennen Sie Ihr neues Pawn in „MRPawn“ um, und doppelklicken Sie darauf, um es zu öffnen. 

![Erstellen eines neuen Pawns, das von „DefaultPawn“ erbt](images/unreal-uxt/3-defaultpawn.PNG)

2.  Das Pawn verfügt standardmäßig über eine Gitterkomponente und über eine Kollisionskomponente, da vom Spieler gesteuerte Pawns in den meisten Unreal-Projekten solide Objekte sind, die mit anderen Komponenten kollidieren. In diesem Fall ist der Benutzer das Pawn, weshalb es möglich sein soll, sich durch Hologramme zu bewegen, ohne eine Kollision zu generieren. Wählen Sie im Komponentenbereich die Kollisionskomponente (**CollisionComponent**) aus. Scrollen Sie im Detailbereich nach unten zum Abschnitt „Collision“ (Kollision), und klicken Sie neben „Collision Presets“ (Kollisionsvoreinstellungen) auf die Dropdownliste. Ändern Sie die Einstellung von „Pawn“ in **NoCollision**. Führen Sie die gleichen Schritte auch für **MeshComponent** aus. **Kompilieren** Sie die Blaupause, und **speichern** Sie sie anschließend. Kehren Sie zum Hauptfenster zurück. 

![Anpassen der Kollisionsvoreinstellungen des Pawns](images/unreal-uxt/3-nocollision.PNG)

## <a name="create-a-game-mode"></a>Erstellen eines Spielmodus

1.  Erstellen Sie im Inhaltsbrowser im Ordner „Content“ eine neue Blaupause mit dem übergeordneten Element **Game Mode Base** (Spielmodusbasis). Nennen Sie sie „MRGameMode“, und doppelklicken Sie darauf, um sie zu öffnen. In Unreal bestimmt der Spielmodus eine Reihe von Einstellungen für das Spiel oder die Umgebung, zu denen unter anderem auch das zu verwendende Standard-Pawn gehört. 

![„MRGameMode“ im Inhaltsbrowser](images/unreal-uxt/3-gamemode.PNG)

2.  Navigieren Sie im Detailbereich zum Abschnitt „Classes“ (Klassen). Ändern Sie die Standard-Pawn-Klasse (Default Pawn Class) von „DefaultPawn“ in das soeben erstellte Pawn **MRPawn**. Klicken Sie auf **Compile** (Kompilieren) und anschließend auf **Save** (Speichern). Kehren Sie zum Hauptfenster zurück. 

![Festlegen der Standard-Pawn-Klasse](images/unreal-uxt/3-setpawn.PNG)

3.  Im letzten Einrichtungsschritt für Ihr Projekt muss Unreal angewiesen werden, standardmäßig „MRGameMode“ zu verwenden. Navigieren Sie zu **Edit > Projects Settings > Maps & Modes** („Bearbeiten“ > „Projekteinstellungen“ > „Zuordnungen und Modi“) im Projektabschnitt. Klicken Sie im Abschnitt „Default Modes“ (Standardmodi) auf die Dropdownliste, und wählen Sie **MRGameMode** aus. Ändern Sie direkt darunter im Abschnitt „Default Maps“ (Standardzuordnungen) sowohl **EditorStartupMap** als auch **GameDefaultMap** in **Main**. Wenn Sie nun den Editor schließen und wieder öffnen, wird standardmäßig die Zuordnung „Main“ ausgewählt. Analog dazu wird beim Spielen des Spiels die Zuordnung „Main“ als Level gestartet. 

![Projekteinstellungen: Zuordnungen und Modi](images/unreal-uxt/3-mapsandmodes.PNG)

[Nächster Abschnitt: 4. Interaktives Gestalten der Szene](unreal-uxt-ch4.md)