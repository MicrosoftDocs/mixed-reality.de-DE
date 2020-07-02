---
title: 3. Einrichten Ihres Projekts für Mixed Reality
description: Teil 3 von 6 einer Tutorialreihe zum Erstellen einer einfachen Schach-App mit der Unreal Engine 4 und dem UX Tools-Plug-In des Mixed Reality-Toolkits
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Tutorial, erste Schritte, MRTK, UXT, UX Tools, Dokumentation
ms.openlocfilehash: f79985b2ce9e26971c23acf36a3538bf7f3c166e
ms.sourcegitcommit: ff0e89b07d0b4a945967d64c5b8845a21dc5f476
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84879555"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a>3. Einrichten Ihres Projekts für Mixed Reality

## <a name="overview"></a>Übersicht

Im vorherigen Tutorial haben Sie Zeit für das Einrichten des Schach-App-Projekts aufgewendet. Dieser Abschnitt führt Sie durch das Einrichten der App für die Mixed Reality-Entwicklung, was konkret das Hinzufügen einer AR-Sitzung bedeutet. Sie verwenden für diese Aufgabe ein ARSessionConfig-Datenobjekt, das viele nützliche AR-Einstellungen wie räumliche Abbildung und Verdeckung aufweist. Wenn Sie tiefer einsteigen möchten, finden Sie in der Dokumentation zur Unreal Engine weitere Details zum Medienobjekt [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) und der Klasse [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html).

## <a name="objectives"></a>Ziele
* Arbeiten mit den AR-Einstellungen der Unreal Engine 
* Verwenden eines ARSessionConfig-Datenobjekts
* Einrichten eines Pawns und des Spielemodus

## <a name="adding-the-session-asset"></a>Hinzufügen des Sitzungsobjekts
AR-Sitzungen in Unreal kommen nicht aus dem Nichts zustande. Um eine Sitzung zu verwenden, benötigen Sie ein ARSessionConfig-Datenobjekt, mit dem Sie arbeiten können, und das ist Ihre nächste Aufgabe:

1. Klicken Sie im **Content Browser** (Inhaltsbrowser) auf **Add New > Miscellaneous > Data Asset** (Neu hinzufügen > Sonstiges > Datenobjekt). Achten Sie darauf, dass Sie sich auf der Stammebene des Ordners **Content** befinden. 
    * Wählen Sie **ARSessionConfig** aus, klicken Sie auf **Select** (Auswählen), und geben Sie dem Objekt den Namen **ARSessionConfig**.

![Erstellen einer Datenressource](images/unreal-uxt/3-createasset.PNG)

3. Doppelklicken Sie auf **ARSessionConfig**, um es zu öffnen, lassen Sie die Standardeinstellungen unverändert, und klicken Sie auf **Save** (Speichern). Kehren Sie zum Hauptfenster zurück. 

![AR-Sitzungskonfiguration](images/unreal-uxt/3-arsessionconfig.PNG)

Nachdem dies erledigt ist, überzeugen Sie sich im nächsten Schritt davon, dass die AR-Sitzung beim Laden des Levels gestartet und mit dem Ende des Levels beendet wird. Glücklicherweise verfügt Unreal über eine spezielle Art Blaupause, die als **Level Blueprint** (Levelblaupause) bezeichnet wird und als levelweites globales Ereignisdiagramm fungiert. Durch das Verbinden des ARSessionConfig-Medienobjekts mit der **Level Blueprint** wird sichergestellt, dass die AR-Sitzung ordnungsgemäß ausgelöst wird, wenn das Spiel beginnt.

1. Klicken Sie in der Editor-Symbolleiste auf **Blueprints > Open Level Blueprint** (Blaupausen > Levelblaupause öffnen): 

![Geöffnete Levelblaupause](images/unreal-uxt/3-level-blueprint.PNG)

5. Ziehen Sie den Ausführungsknoten (nach links gerichtetes Pfeilsymbol) von **Event BeginPlay** (BeginPlay-Ereignis) herunter, und geben Sie ihn frei. Suchen Sie nach dem Knoten **Start AR Session** (AR-Sitzung starten), und drücken Sie die EINGABETASTE.  
    * Klicken Sie unter **Session Config** (Sitzungskonfiguration) auf die Dropdownliste **Select Asset** (Medienobjekt auswählen), und wählen Sie das Medienobjekt **ARSessionConfig** aus. 

![Starten der AR-Sitzung](images/unreal-uxt/3-start-ar-session.PNG)

6. Klicken Sie an beliebiger Stelle im EventGraph mit der rechten Maustaste, und erstellen Sie einen neuen Knoten **Event EndPlay**. Ziehen Sie den Ausführungspin, und geben Sie ihn frei. Suchen Sie nach einem Knoten **Stop AR Session**, und drücken Sie die EINGABETASTE. Wenn die AR-Sitzung mit dem Ende des Levels nicht beendet wird, funktionieren bestimmte Features möglicherweise nicht mehr, wenn Sie die App beim Streaming zu einem Headset neu starten. 
    * Klicken Sie auf **Compile** (Kompilieren), **speichern** Sie Ihre Arbeit, und kehren Sie dann zum Hauptfenster zurück.

![Beenden der AR-Sitzung](images/unreal-uxt/3-stoparsession.PNG)

## <a name="create-a-pawn"></a>Erstellen eines Pawns
An diesem Punkt benötigt das Projekt noch immer ein Playerobjekt. In Unreal stellt ein **Pawn** den Benutzer im Spiel dar, aber in diesem Fall handelt es sich um die HoloLens 2-Umgebung.

1. Klicken Sie im Ordner **Content** (Inhalt) auf **Add New > Blueprint Class** (Neu hinzufügen > Blaupausenklasse), und klappen Sie unten den Abschnitt **All Classes** (Alle Klassen) auf. 
    * Suchen Sie nach **DefaultPawn**, klicken Sie auf **Select** (Auswählen), und doppelklicken Sie auf das Medienobjekt, um es zu öffnen. 

![Erstellen eines neuen Pawns, das von „DefaultPawn“ erbt](images/unreal-uxt/3-defaultpawn.PNG)

> [!NOTE]
> Standardmäßig verfügen Pawns über Gittermodell- und Kollisionskomponenten. In den meisten Unreal-Projekten handelt es sich bei Pawns um feste Objekte, die mit anderen Komponenten zusammenstoßen können. Da das Pawn und der Benutzer im Fall von Mixed Reality das Gleiche sind, möchten Sie imstande sein, Hologramme ohne Zusammenstoß zu durchschreiten. 

2. Wählen Sie im Bereich **Components** (Komponenten) **CollisionComponent** aus, und scrollen Sie im Bereich **Details** nach unten zum Abschnitt **Collision** (Kollision). 
    * Klicken Sie auf die Dropdownliste **Collision Presets** (Kollisionseinstellung), und ändern Sie den Wert in **NoCollision** (Keine Kollision). 
    * Führen Sie die gleichen Schritte für **MeshComponent** aus, und **kompilieren** und **speichern** Sie dann die Blaupause. 

![Anpassen der Kollisionsvoreinstellungen des Pawns](images/unreal-uxt/3-nocollision.PNG)

Nachdem Sie Ihre Arbeit hier erledigt haben, kehren Sie zum Hauptfenster zurück.

## <a name="create-a-game-mode"></a>Erstellen eines Spielmodus
Das letzte Puzzleteil der Mixed Reality-Einrichtung ist der Spielemodus. Der Spielemodus bestimmt eine Reihe von Einstellungen für das Spiel oder die Umgebung, zu denen unter anderem auch das zu verwendende Standard-Pawn gehört.

1.  Klicken Sie im Ordner **Content** (Inhalt) auf **Add New > Blueprint Class** (Neu hinzufügen > Blaupausenklasse), und klappen Sie unten den Abschnitt **All Classes** (Alle Klassen) auf. 
    * Suchen Sie nach **Game Mode Base** (Spielemodusbasis), benennen Sie sie **MRGameMode**, und doppelklicken Sie dann darauf, um sie zu öffnen. 

![„MRGameMode“ im Inhaltsbrowser](images/unreal-uxt/3-gamemode.PNG)

2.  Navigieren Sie im Bereich **Details** zum Abschnitt **Classes** (Klassen), und ändern Sie die **Default Pawn Class** (Pawn-Standardklasse) in **MRPawn**. 
    * Klicken Sie auf **Compile** (Kompilieren), **speichern** Sie Ihre Arbeit, und kehren Sie dann zum Hauptfenster zurück. 

![Festlegen der Standard-Pawn-Klasse](images/unreal-uxt/3-setpawn.PNG)

3.  Wählen Sie **Edit > Projects Settings** (Bearbeiten > Projekteinstellungen) aus, und klicken Sie in der Liste auf der linken Seite auf **Maps & Modes** (Zuordnungen und Modi). 
    * Klappen Sie **Default Modes** (Standardmodi) auf, und ändern Sie **Default Game Mode** (Standardspielemodus) in **MRGameMode**. 
    * Klappen Sie **Default Maps** (Standardzuordnungen) auf, und ändern Sie sowohl **EditorStartupMap** als auch **GameDefaultMap** in **Main**. Wenn Sie den Editor schließen und wieder öffnen oder das Spiel spielen, wird auf diese Weise standardmäßig die Hauptzuordnung ausgewählt.

![Projekteinstellungen: Zuordnungen und Modi](images/unreal-uxt/3-mapsandmodes.PNG)

Mit dem jetzt vollständig für Mixed Reality eingerichteten Projekt können Sie jetzt mit dem nächsten Tutorial fortfahren und damit beginnen, der Szene Benutzereingaben hinzuzufügen. 

[Nächster Abschnitt: 4. Interaktives Gestalten der Szene](unreal-uxt-ch4.md)