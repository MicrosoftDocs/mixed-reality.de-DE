---
title: 2. Initialisieren des Projekts und der ersten Anwendung
description: Teil 2 eines Tutorials zum Erstellen einer einfachen Schach-App mit Unreal Engine 4 und dem UX-Tools-Plug-In des Mixed Reality-Toolkits
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Tutorial, erste Schritte, MRTK, UXT, UX Tools, Dokumentation
ms.openlocfilehash: fc85f011ff3b186f3b4b5449b4f8ec49f0b6418f
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851574"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Initialisieren des Projekts und der ersten Anwendung

In diesem Abschnitt finden Sie Informationen zu den ersten Schritten bei der Erstellung einer neuen Unreal-Anwendung für HoloLens 2. 

## <a name="objectives"></a>Ziele

* Konfigurieren von Unreal für die HoloLens-Entwicklung
* Importieren von Assets und Einrichten der Szene

## <a name="create-a-new-unreal-project"></a>Erstellen eines neuen Unreal-Projekts

1. Starten von Unreal Engine

2. Wählen Sie unter **New Project Categories** (Kategorien für neues Projekt) die Option **Games** (Spiele) aus, und klicken Sie auf „Next“ (Weiter). Wählen Sie eine leere Vorlage (**Blank**) aus, und klicken Sie auf „Next“ (Weiter). 

![Auswählen einer leeren Vorlage](images/unreal-uxt/2-template.PNG)

3. Wählen Sie in den Projekteinstellungen die Optionen **C++, Scalable 3D or 2D, Mobile / Tablet** („C++“, „Skalierbares 3D oder 2D“, „Mobilgerät/Tablet“) und **No Starter Content** (Keine Startinhalte) aus. Wählen Sie einen Speicherort für Ihr Projekt aus, und klicken Sie auf **Create Project** (Projekt erstellen). Daraufhin werden Ihre C++-Dateien in einem Visual Studio-Projekt und im Unreal-Editor geöffnet. 

![Anfängliche Projekteinstellungen](images/unreal-uxt/2-project-settings.PNG)

4. Navigieren Sie links oben zu **Edit > Plugins** („Bearbeiten“ > „Plug-Ins“). Aktivieren Sie unter „Augmented Reality“ das Kontrollkästchen für **HoloLens**, um dieses Plug-In zu aktivieren. Scrollen Sie nach unten zum Abschnitt „Virtual Reality“, und aktivieren Sie das Kontrollkästchen für **Microsoft Windows Mixed Reality**, um dieses Plug-In zu aktivieren. Beide Plug-Ins werden für die Entwicklung für HoloLens 2 benötigt. Starten Sie den Editor neu. 

![Plug-Ins](images/unreal-uxt/2-plugins.PNG)

5. Navigieren Sie links oben zu **File > New Level** („Datei“ > „Neues Level“). Wählen Sie **Empty Level** (Leeres Level) aus. Die Standardszene im Viewport sollte nun leer sein.

6. Platzieren Sie „PlayerStart“ mittels Drag & Drop aus dem Modusbereich auf der linken Seite (auf der Registerkarte „Basic“ (Standard)). Legen Sie im Detailbereich auf der rechten Seite die Position auf „X = 0“, „Y = 0“ und „Z = 0“ fest, damit der Benutzer beim Start der App am Ursprung startet.

![Viewport mit „PlayerStart“](images/unreal-uxt/2-playerstart.PNG)

7. Ziehen Sie einen Würfel (**Cube**) von der Registerkarte „Basic“ (Standard) des Modusbereichs in den Viewport. Legen Sie im Detailbereich die Position auf „X = 50“, „Y = 0“ und „Z = 0“ fest, damit der Würfel beim Start 50 cm vom Spieler entfernt ist. Da der Standardwürfel sehr groß ist, ändern Sie die Skalierung des Würfels in „0,2“, „0,2“, „0,2“. 

8. Der Würfel ist nur sichtbar, wenn Sie Ihrer Szene ein Licht hinzufügen. Wechseln Sie im Modusbereich zur Registerkarte **Lights** (Lichter), ziehen Sie ein gerichtetes Licht (**Directional Light**) in die Szene, und platzieren Sie es oberhalb von „PlayerStart“.

![Viewport mit hinzugefügtem Licht](images/unreal-uxt/2-light.PNG)

9.  Klicken Sie auf der Symbolleiste auf die Schaltfläche **Play** (Spielen), um den Würfel im Viewport zu sehen. Drücken Sie **ESC**, um das Level zu beenden. 

![Ein Würfel im Viewport](images/unreal-uxt/2-cube.PNG)

10. Speichern Sie Ihr Level. Klicken Sie hierzu links oben auf **File > Save Current** („Datei“ > „Aktuellen Stand speichern“). Nennen Sie Ihr Level „Main“, und klicken Sie auf **Save** (Speichern). 

## <a name="set-up-a-chess-scene"></a>Einrichten einer Schachszene

1. Klicken Sie in Ihrem Inhaltsbrowser auf das Symbol unter „Add New“ (Neu hinzufügen), um den Quellenbereich anzuzeigen. Klicken Sie anschließend auf **Add New > New Folder** („Neu hinzufügen“ > „Neuer Ordner“), und nennen Sie den Ordner „ChessAssets“. Doppelklicken Sie auf den Ordner, um dorthin zu navigieren. Hier werden die 3D-Ressourcen für das Schachspiel importiert.

![Anzeigen oder Ausblenden des Quellenbereichs](images/unreal-uxt/2-showhidesources.PNG)

2. Laden Sie die ZIP-Datei mit den Ressourcen aus [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) herunter. Diese Datei enthält die 3D-Modelle für ein Schachbrett und ein Schachspiel. Entzippen Sie die Datei.

3. Klicken Sie oben im Inhaltsbrowser auf **Import** (Importieren). Navigieren Sie zu dem Ordner, den Sie soeben entzippt haben, und wählen Sie alle darin enthaltenen Elemente aus. Dieser Ordner enthält FBX-Dateien (die 3D-Ressourcen für das Schachbrett und die Schachfiguren) sowie TGA-Dateien (die Texturmaps zum Erstellen von Materialien für das Schachbrett und die Schachfiguren). Klicken Sie auf **Öffnen**. 

4. Daraufhin wird ein Fenster mit FBX-Importoptionen geöffnet. Ändern Sie im Abschnitt **Material** die Methode für den Materialimport (**Material Import Method**) in **Do Not Create Material** (Kein Material erstellen). Klicken Sie anschließend auf **Import All** (Alle importieren).

![FBX-Importoptionen](images/unreal-uxt/2-nocreatemat.PNG)

5. Erstellen Sie in Ihrem Inhaltsordner einen neuen Ordner namens **Blueprints**. Dort werden sämtliche Blaupausen gespeichert. Bei Blaupausen handelt es sich um spezielle Ressourcen, die eine knotenbasierte Oberfläche bieten, über die neue Arten von Akteuren und Ereignissen auf der Skriptebene erstellt werden können. 

6. Doppelklicken Sie auf den Ordner **Blueprints**, um dorthin zu navigieren. Klicken Sie anschließend in Ihrem Inhaltsbrowser mit der rechten Maustaste, und wählen Sie **Blueprint Class** (Blaupausenklasse) aus. Klicken Sie auf **Actor** (Akteur), und nennen Sie die neue Blaupause „Board“. Doppelklicken Sie auf „Board“, um die Blaupause zu öffnen. 

![Auswählen einer übergeordneten Klasse für Ihre Blaupause](images/unreal-uxt/2-bpparent.PNG)

![Die neue Blaupause „Board“](images/unreal-uxt/2-bpboard.PNG)

7. Navigieren Sie im Blaupausen-Editor zum Komponentenbereich, und klicken Sie auf **Add Component > Scene** („Komponente hinzufügen“ > „Szene“). Nennen Sie die neu erstellte Szene „Root“, klicken Sie darauf, und ziehen Sie „Root“ auf „DefaultSceneRoot“. Dadurch wird der standardmäßige Szenenstamm ersetzt und die Kugel im Viewport entfernt. 

![Ersetzen des Stamms](images/unreal-uxt/2-root.PNG)

8. Klicken Sie erneut auf **Add Component** (Komponente hinzufügen), wählen Sie diesmal aber **Static Mesh** (Statisches Gitter) aus. Nennen Sie das neue statische Gitter „SM_Board“. 

![Hinzufügen eines statischen Gitters](images/unreal-uxt/2-sm-board.PNG)

9. Navigieren Sie im Bereich **Details** zum Abschnitt **Static Mesh** (Statisches Gitter), und klicken Sie auf die Dropdownliste. Wählen Sie **ChessBoard** aus. 

![Das Schachbrettgitter im Viewport](images/unreal-uxt/2-sm-board-view.PNG)

10. Navigieren Sie als Nächstes im Bereich **Details** zum Abschnitt **Materials** (Material), und klicken Sie auf die Dropdownliste. Wählen Sie unter **Create New Asset** (Neue Ressource erstellen) die Option **Material** aus. Nennen Sie die Ressource **M_ChessBoard**, und speichern Sie sie im Ordner **ChessAssets**. 

![Erstellen eines neuen Materials](images/unreal-uxt/2-newmat.PNG)

11. Doppelklicken Sie auf das Quadrat neben der Dropdownliste „M_ChessBoard“, um Ihr neu erstelltes Material „M_ChessBoard“ zu öffnen. Klicken Sie im Material-Editor mit der rechten Maustaste, und suchen Sie nach dem Knoten **Texture Sample** (Texturbeispiel). Klicken Sie im Bereich **Details** im Abschnitt **Material Expression Texture Base** (Texturbasis für Materialausdruck) auf die Dropdownliste, und wählen Sie **ChessBoard_Albedo** aus. Ziehen Sie abschließend den Pin der Ausgabe **RGB** zum Pin der Basisfarbe von **M_ChessBoard**. 

![Festlegen der Basisfarbe](images/unreal-uxt/2-boardalbedomat.PNG)

12. Verknüpfen Sie auf die gleiche Weise das Texturbeispiel **ChessBoard_AO** mit dem Pin **Ambient Occlusion** (Umgebungsverdeckung), das Texturbeispiel **ChessBoard_Metal** mit dem Pin **Metallic** (Metallisch), das Texturbeispiel **ChessBoard_Normal** mit dem Pin **Normal** und das Texturbeispiel **ChessBoard_Rough** mit dem Pin **Roughness** (Rauheit). Klicken Sie auf **Speichern**. 

![Verbinden der restlichen Texturen](images/unreal-uxt/2-boardmat.PNG)

13. Kehren Sie zur Blaupause **Board** zurück. Wie Sie sehen, wurde das soeben erstellte Material auf Ihre Blaupause angewendet. Ändern Sie die Skalierung (**Scale**) des Schachbretts in „0,05“, „0,05“ und „0,05“ und die Drehung (**Rotation**) in „Z = 90“, damit das Schachbrett eine geeignete Größe und Position hat, wenn es in der Szene platziert wird. Klicken Sie auf der oberen Symbolleiste auf **Compile** (Kompilieren) und anschließend auf **Speichern**. Kehren Sie zu Ihrem Hauptfenster zurück. 

![Schachbrett mit angewendetem Material](images/unreal-uxt/2-chessboard.PNG)

14. Als Nächstes löschen wir den Würfel und ersetzen ihn durch den neu erstellten Akteur „Board“. Klicken Sie im Gliederungs-Editor (**World Outliner**) mit der rechten Maustaste auf den Würfel, und wählen Sie anschließend **Edit > Delete** („Bearbeiten“ > „Löschen“) aus. Ziehen Sie „Board“ aus Ihrem Inhaltsbrowser in den Viewport. Legen Sie die Position des Schachbretts auf „X = 80“, „Y = 0“ und „Z = -20“ fest. 

15. Klicken Sie auf die Schaltfläche **Play** (Spielen), um das neue Schachbrett in Ihrem Level zu betrachten. Drücken Sie **ESC**, um zum Editor zurückzukehren. 

16. Als Nächstes wird mit der gleichen Vorgehensweise wie für das Schachbrett eine Schachfigur erstellt, diesmal allerdings unter Verwendung des Gitters und Materials für die Schachfigur:

    a) Navigieren Sie im Inhaltsbrowser zum Ordner „Blueprints“, und erstellen Sie eine neue Blaupausenklasse vom Typ „Actor“ (Akteur). Nennen Sie diesen Akteur „WhiteKing“.

    b) Doppelklicken Sie auf „WhiteKing“, um den Akteur zu öffnen. Fügen Sie eine neue Szenenkomponente namens „Root“ hinzu, und ersetzen Sie damit „DefaultSceneRoot“. 

    c) Fügen Sie eine neue statische Gitterkomponente namens „SM_King“ hinzu. Legen Sie im Detailbereich die Option **Static Mesh** (Statisches Gitter) auf **Chess_King** und die Option **Material** auf ein neues Material mit dem Namen **M_ChessWhite** fest. 

    d) Öffnen Sie das neue Material **M_ChessWhite**, und verbinden Sie die relevanten Texturen mit den entsprechenden Materialeingaben. 

    ![Erstellen des Materials für den König (Schachfigur)](images/unreal-uxt/2-chesskingmat.PNG)

    e) Kehren Sie zu Ihrer Blaupause **WhiteKing** zurück, und ändern Sie die Skalierung (**Scale**) in „0,05“, „0,05“ und „0,05“ sowie die Drehung (**Rotation**) in „Z = 90“.

    f) Kompilieren und speichern Sie die Blaupause, und kehren Sie anschließend wieder zu Ihrem Hauptfenster zurück. 

17. Ziehen Sie „WhiteKing“ in Ihren Viewport. Ziehen Sie „WhiteKing“ im Gliederungs-Editor (**World Outliner**) auf „Board“, um „WhiteKing“ zu einem untergeordneten Element von „Board“ zu machen. 

![Gliederungs-Editor](images/unreal-uxt/2-child.PNG)

18. Legen Sie im Bereich **Details** unter **Transform** (Transformieren) die Position (**Location**) von „WhiteKing“ auf „X = -26“, „Y = 4“ und „Z = 0“ fest.

19. Klicken Sie auf **Play** (Spielen), um Ihr Level zu betrachten. Drücken Sie zum Beenden **ESC**. 

[Nächster Abschnitt: 3. Einrichten Ihres Projekts für Mixed Reality](unreal-uxt-ch3.md)