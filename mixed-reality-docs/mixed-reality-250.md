---
title: Mr-Freigabe 250-hololens und immersive Headsets
description: Befolgen Sie diese exemplarische Vorgehensweise zum Programmieren mit Unity, Visual Studio, hololens und Windows Mixed Reality-Headsets, um die Details der Freigabe von holograms zwischen gemischten Reality-Geräten zu erlernen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, immersive, Motion Controller, Freigabe, Xbox Controller, Networking, Geräte übergreifend
ms.openlocfilehash: c8d341f75424887ca1b0994c8a4d16a0bded671e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437863"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es wurde [eine neue Reihe von Tutorials](mrlearning-base.md) für hololens 2 gepostet.

<br>

# <a name="mr-sharing-250-hololens-and-immersive-headsets"></a>Mr-Freigabe 250: hololens und immersive Headsets

Mit der Flexibilität von universelle Windows-Plattform (UWP) ist es einfach, eine Anwendung zu erstellen, die mehrere Geräte umfasst. Mit dieser Flexibilität können wir Umgebungen erstellen, die die Stärken der einzelnen Geräte nutzen. Dieses Tutorial behandelt eine grundlegende freigegebene Darstellung, die auf hololens und Windows Mixed Reality-immersiven Headsets ausgeführt wird. Dieser Inhalt wurde ursprünglich auf der Microsoft Build 2017-Konferenz in Seattle, WA, bereitgestellt.

**In diesem Tutorial werden folgende Aktionen durchführt:**

* Richten Sie ein Netzwerk mithilfe von uNet ein.
* Freigeben von holograms auf gemischten Reality-Geräten.
* Richten Sie abhängig davon, welches gemischte Reality-Gerät verwendet wird, eine andere Ansicht der Anwendung ein.
* Sorgen Sie für eine gemeinsame Nutzung, bei der hololens-Benutzer über einige einfache Rätsel mit den Benutzer in der Hand arbeiten.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>Mr-Freigabe 250: hololens und immersive Headsets</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Bevor Sie beginnen

### <a name="prerequisites"></a>Voraussetzungen

* Einen Windows 10-PC mit den [erforderlichen Entwicklungs Tools](install-the-tools.md) [, die zur Unterstützung eines Windows Mixed Reality-immersiven Headsets konfiguriert](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)sind.
* Einen Xbox-Controller, der mit Ihrem PC funktioniert.
* Mindestens ein hololens-Gerät und ein immersives Headset.
* Ein Netzwerk, das UDP-Broadcast für die Ermittlung ermöglicht.

### <a name="project-files"></a>Projektdateien

* Herunterladen der [Dateien](https://github.com/Microsoft/MixedReality250/archive/master.zip) , die für das Projekt erforderlich sind. Extrahieren Sie die Dateien an einen leicht zu vermerkbaren Speicherort.
* Dieses Projekt erfordert [eine empfohlene Version von Unity mit Windows Mixed Reality-Unterstützung](install-the-tools.md).

>[!NOTE]
>Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/MixedReality250).

## <a name="chapter-1---holo-world"></a>Kapitel 1-Holo World

>[!VIDEO https://www.youtube.com/embed/IC0rp6rLiEc]

### <a name="objectives"></a>Ziele

Stellen Sie sicher, dass die Entwicklungsumgebung mit einem einfachen Projekt fertig ist.

### <a name="what-we-will-build"></a>Build

Eine Anwendung, die ein – Hologramm für hololens oder ein Windows Mixed Reality-immersives Headset anzeigt.

### <a name="steps"></a>Schritte

* Öffnen Sie Unity.
    * Wählen Sie **Öffnen**aus.
    * Navigieren Sie dorthin, wo Sie die Projektdateien extrahiert haben.
    * Klicken Sie auf **Ordner auswählen**.
    * *Es dauert einige Zeit, bis Unity das Projekt erstmalig verarbeitet.*
* Überprüfen Sie, ob gemischte Realität in Unity aktiviert ist.
    * Öffnen Sie das Dialogfeld "Buildeinstellungen" (STRG +**UMSCHALT + B** oder **Datei > Erstellen von Einstellungen...** ).
    * Wählen Sie **universelle Windows-Plattform** klicken Sie dann auf **Plattform wechseln**.
    * Wählen Sie **> Player Einstellungen bearbeiten**aus.
    * Erweitern Sie im Bereich **Inspector** auf der rechten Seite die Option **XR-Einstellungen**.
    * Aktivieren Sie das Kontrollkästchen **virtuelle Realität unterstützt** .
    * *Windows Mixed Reality sollte das Virtual Reality SDK sein.*
* Erstellen Sie eine Szene.
    * Klicken Sie in der **Hierarchie** mit der rechten Maustaste auf **Hauptkamera** **Löschen**.
    * Aus **holotoolkit > Eingabe > Prefabs** **mixedrealitycameraparent** in die **Hierarchie**ziehen.
* Hinzufügen von holograms zur Szene
    * Ziehen Sie in **appprefabs** **Skybox** in die **Ansicht Szene**.
    * Aus **appprefabs** ziehen Sie **Manager** in die **Hierarchie**.
    * Ziehen Sie die **Insel** von **appprefabs** auf die- **Hierarchie**.
* Speichern und erstellen
    * Speichern (entweder **Control + S** oder **File > Szene speichern**)
    * Da es sich um eine neue Szene handelt, müssen Sie diese benennen. Der Name ist nicht wichtig, aber wir verwenden sharedmixedreality.
* In Visual Studio exportieren
    * Öffnen Sie das Menü "Build" (STRG +**UMSCHALT + B** oder **Datei > Buildeinstellungen**).
    * Klicken Sie auf **offene Szenen hinzufügen.**
    * **Unity C# -Projekte** überprüfen
    * Klicken Sie auf **Erstellen**.
    * Erstellen Sie im daraufhin angezeigten Fenster "Datei-Explorer" einen neuen Ordner mit dem Namen " **App**".
    * Klicken Sie einfach auf den **App** -Ordner.
    * Drücken **Sie Ordner auswählen.**
    * **Warten Sie, bis der Build beendet wurde.**
    * Navigieren Sie im Datei-Explorer-Fenster, das angezeigt wird, in den **App** -Ordner.
    * Doppelklicken Sie auf **sharedmixedreality. sln** , um Visual Studio zu starten.
* Build aus Visual Studio
    * Verwenden des oberen Symbolleisten-Änderungs Ziels für **Release** und **x86**.
    * Klicken Sie auf den Pfeil neben **lokaler Computer** , und wählen Sie **Gerät** für die Bereitstellung in hololens aus.
    * Klicken Sie auf den Pfeil neben **Gerät** , und wählen Sie **lokaler Computer** für die Bereitstellung für das Mixed Reality-Headset aus.
    * Klicken Sie auf **Debuggen > Starten ohne Debuggen** oder **Steuern + F5** , um die Anwendung zu starten.

### <a name="digging-into-the-code"></a>Durchforsten des Codes

Navigieren Sie im Projekt Panel zu **asset\holotoolkit\input\script\utilities** , und doppelklicken Sie auf **MixedRealityCameraManager.cs** , um es zu öffnen.

**Übersicht:** MixedRealityCameraManager.cs ist ein einfaches Skript, das Qualitäts-und Hintergrundeinstellungen basierend auf dem Gerät anpasst. Schlüssel hier ist holographicsettings. isdisplaytransparent, mit dem ein Skript erkennen kann, ob es sich bei dem Gerät um einen hololens handelt (isdisplayopaque gibt false zurück), oder ein immersives Headset (isdisplayopaque gibt true zurück).

### <a name="enjoy-your-progress"></a>Nutzen Sie Ihren Fortschritt

An diesem Punkt wird nur ein Hologram von der Anwendung erstellt. Wir werden dem – Hologramm später eine Interaktion hinzufügen. Beide Geräte erzeugen das – Hologramm gleich. Das immersive Headset gibt auch einen blauen Himmel und Clouds-Hintergrund aus.

## <a name="chapter-2---interaction"></a>Kapitel 2: Interaktion

>[!VIDEO https://www.youtube.com/embed/Lrb1y4sQRvI]

### <a name="objectives"></a>Ziele

Zeigt, wie Eingaben für eine Windows Mixed Reality-Anwendung behandelt werden.

### <a name="what-we-will-build"></a>Build

Auf der Grundlage der Anwendung aus Kapitel 1 fügen wir Funktionen hinzu, die es dem Benutzer ermöglichen, das Hologramm zu übernehmen und es auf der realen Oberfläche in hololens oder einer virtuellen Tabelle in einem immersiven Headset zu platzieren.

**Eingabe Auffrischung:** Bei hololens ist die Auswahl Geste die **Luftlinie**. Bei immersiven Headsets verwenden wir die Schaltfläche **A** auf dem Xbox-Controller. Weitere Informationen finden Sie in der [Übersicht über das Interaktionsmodell](interaction-fundamentals.md).

### <a name="steps"></a>Schritte

* Eingabe-Manager hinzufügen
    * Aus **holotoolkit > Eingabe > Prefabs** als untergeordnetes Element von **Vorgesetzten** **in die** **Hierarchie** ziehen.
    * Aus **holotoolkit > Eingabe > präfabs > Cursor** Cursor **in** die **Hierarchie**ziehen.
* Räumliche Zuordnung hinzufügen
    * Aus **holotoolkit > spatialmapping > Prefabs** **spatialmapping** in die **Hierarchie**ziehen.
* Virtuellen Playspace hinzufügen
    * Erweitern Sie in **Hierarchie** den Knoten **mixedrealitycameraparent** Select **Boundary** .
    * Aktivieren Sie im **Inspektor** -Panel das Kontrollkästchen zum Aktivieren der **Grenze** .
    * Ziehen Sie in **appprefabs** **vrroom** auf **Hierarchie**.
* Worldanchormanager hinzufügen
    * Wählen Sie in **Hierarchie**die Option **Manager**aus.
    * Klicken Sie in **Inspector**auf **Komponente hinzufügen**.
    * Geben Sie **World Anchor Manager**ein.
    * Wählen Sie **World Anchor Manager** aus, um ihn hinzuzufügen.
* Hinzufügen von taptoplace zur Insel
    * Erweitern Sie in **Hierarchie**den Knoten **Insel**.
    * Wählen Sie **mixedrealitylands**aus.
    * Klicken Sie in **Inspector**auf **Komponente hinzufügen**.
    * Geben Sie tippen Sie ein **,** und wählen Sie ihn aus.
    * Aktivieren Sie **übergeordnetes Element bei tippen**.
    * Legen Sie **Platzierungs Offset** auf **(0, 0,1, 0)** fest.
* Speichern und erstellen wie zuvor

### <a name="digging-into-the-code"></a>Durchforsten des Codes

**Skript 1-GamepadInput.cs**

Navigieren Sie im Projekt Panel zu **asset\holotoolkit\input\script\inputsources** , und doppelklicken Sie auf **GamepadInput.cs** , um es zu öffnen. Doppelklicken Sie im Projekt Panel auf denselben Pfad, und doppelklicken Sie auf **InteractionSourceInputSource.cs**.

Beachten Sie, dass beide Skripts über eine allgemeine Basisklasse (baseinputsource) verfügen.

Baseinputsource speichert einen Verweis auf einen InputManager, wodurch ein Skriptereignisse auslöst. In diesem Fall ist das inputgeklickt-Ereignis relevant. Dies ist wichtig, wenn Sie das Skript 2, taptoplace, erhalten. Im Fall von "gamepadinput" rufen wir die Schaltfläche "A" auf dem Controller ab, die gedrückt werden soll. Anschließend wird das Ereignis "inputgeklickt" aufgerufen. Im Fall von interaktionsourceinputsource wird das inputgeklickt-Ereignis als Antwort auf das tappedevent-Ereignis ausgelöst.

**Skript 2-TapToPlace.cs**

Navigieren Sie im Projekt Panel zu **assets\holotoolkit\spatialmapping\scripts** , und doppelklicken Sie auf **TapToPlace.cs** , um es zu öffnen.

Das erste, was viele Entwickler implementieren möchten, wenn Sie eine Holographic-Anwendung erstellen, ist das Verschieben von holograms mit Gesten Eingaben. Daher haben wir uns bemüht, dieses Skript gründlich zu kommentieren. Einige Dinge sind für dieses Tutorial besonders hervorzuheben.

Beachten Sie zunächst, dass "taptoplace" iinputclickhandler implementiert. Iinputclickhandler macht die Funktionen verfügbar, die das von GamePadInput.cs oder InteractionSourceInputSource.cs ausgebene inputclick-Ereignis behandeln. "Oninputclick" wird aufgerufen, wenn ein "baseinputsource" einen Klick erkennt, während das Objekt mit "taptoplace" den Fokus hat. Das-Ereignis wird entweder durch airtippen auf hololens oder durch Drücken der Schaltfläche auf dem Xbox-Controller auslöst.

Zweitens: der Code wird in Update ausgeführt, um festzustellen, ob eine Oberfläche betrachtet wird, damit wir das Spielobjekt auf einer Oberfläche platzieren können, z. b. eine Tabelle. Das immersive Headset weist kein Konzept von echten Oberflächen auf, sodass das Objekt, das die Tabelle oben darstellt (Vroom > tablethingy > Cube) mit der spatialmapping-Physik Schicht markiert wurde, sodass die Strahl Umwandlung bei Update mit der virtuellen Tabelle oben in Konflikt steht.

### <a name="enjoy-your-progress"></a>Nutzen Sie Ihren Fortschritt

Dieses Mal können Sie die Insel auswählen, um Sie zu verschieben. Auf hololens können Sie die Insel auf eine echte Oberfläche verschieben. Im immersiven Headset können Sie die Insel in die virtuelle Tabelle verschieben, die wir hinzugefügt haben.

## <a name="chapter-3---sharing"></a>Kapitel 3: Freigabe

>[!VIDEO https://www.youtube.com/embed/1diycJvxfDc]

### <a name="objectives"></a>Ziele

Stellen Sie sicher, dass das Netzwerk ordnungsgemäß konfiguriert ist, und erläutern Sie, wie räumliche Anker von Geräten gemeinsam genutzt werden

### <a name="what-we-will-build"></a>Build

Das Projekt wird in ein multiplayerprojekt konvertiert. Wir fügen Benutzeroberfläche und Logik zum Hosten oder Verknüpfen von Sitzungen hinzu. Hololens-Benutzer werden einander in der Sitzung mit Clouds über ihren Köpfen sehen, und immersive Headset-Benutzer haben Clouds in der Nähe des Ankers. Benutzer in den immersiven Headsets sehen die hololens-Benutzer relativ zum Ursprung der Szene. Hololens-Benutzer sehen alle das Hologramm der Insel am gleichen Ort. Beachten Sie, dass die Benutzer in den immersiven dashboarden in diesem Kapitel nicht auf der Insel sein werden, sondern sich ähnlich wie hololens Verhalten, mit einer Vogelperspektive auf der Insel.

### <a name="steps"></a>Schritte

* Insel und vrroom entfernen
    * Klicken **Sie in** **Hierarchie** mit der rechten Maustaste auf **Insel** .
    * Klicken Sie in **Hierarchie** mit der rechten Maustaste auf **vrroom** Select **Delete**
* Add-in
    * **Ziehen Sie** in **appprefabs** auf die **Hierarchie**.
* Ziehen Sie in **appprefabs** die folgenden Befehle in die **Hierarchie**:
    * **Unetsharingstage**
    * **Unetanchorroot**
    * **UIContainer**
    * **Debug-Schaltfläche**
* Speichern und erstellen wie zuvor

### <a name="digging-into-the-code"></a>Durchforsten des Codes

Navigieren Sie im Projekt Panel zu **assets\appprefabs\support\sharingwithunet\scripts** , und doppelklicken Sie auf **UnetAnchorManager.cs**. Die Fähigkeit eines hololens, Überwachungsinformationen mit anderen hololens gemeinsam zu nutzen, sodass beide Geräte denselben Platz gemeinsam nutzen können, ist nahezu magisch. Die Leistung gemischter Realität kommt in Kraft, wenn zwei oder mehr Personen mit denselben digitalen Daten zusammenarbeiten können.

In diesem Skript können einige Punkte aufgeführt werden:

Beachten Sie in der Funktion Start die Überprüfung auf **isdisplaytransparent**. In diesem Fall wird der Anker festgelegt. Dies liegt daran, dass die immersiven Headsets keine Möglichkeit zum Importieren oder Exportieren von Ankern bereitstellen. Wenn Sie jedoch auf einem hololens ausführen, implementiert dieses Skript gemeinsame Anker zwischen den Geräten. Das Gerät, von dem die Sitzung gestartet wird, erstellt einen Anker für den Export. Das Gerät, das einer Sitzung Beitritt, fordert den Anker von dem Gerät an, das die Sitzung gestartet hat.

**Export**

Wenn ein Benutzer eine Sitzung erstellt, wird die unetanchormanager-Funktion von networkdiscoverywithanchor aufgerufen. Gehen wir folgendermaßen vor:

Wir beginnen mit der Arbeit mit der Verwaltung und löschen alle Daten, die wir möglicherweise für vorherige Anker gesammelt haben. Dann überprüfen wir, ob ein zwischen gespeicherter Anker zum Laden vorhanden ist. Die Anker Daten liegen tendenziell zwischen 5 und 20 MB, sodass die Wiederverwendung zwischen gespeicherter Anker die Menge der Daten einsparen kann, die wir über das Netzwerk übertragen müssen. Wir sehen, wie dies etwas später funktioniert. Auch wenn wir den Anker wieder verwenden, müssen wir die Anker Daten für den Fall bereitstellen, dass ein neuer clientjoins vorhanden ist, der nicht über den Anker verfügt.

Beim Vorbereiten der Anker Daten stellt die worldanchortransferbatch-Klasse die Funktionalität zum Vorbereiten von Anker Daten für das Senden an ein anderes Gerät oder eine andere Anwendung sowie die Funktionalität zum Importieren der Anker Daten bereit. Da wir den Export Pfad verwenden, fügen wir den Anker zu worldanchortransferbatch hinzu und nennen die exportasync-Funktion. Exportasync ruft dann den Rück schreibe Rückruf auf, wenn Daten für den Export generiert werden. Wenn alle Daten exportiert wurden, wird der Export Complete aufgerufen. In "Write Buffer" fügen wir den Datenblock zu einer Liste hinzu, die für den Export beibehalten wird. In "exportcomplete" konvertieren wir die Liste in ein Array. Außerdem wird die anchorname-Variable festgelegt, die andere Geräte auslöst, um den Anker anzufordern, wenn Sie ihn nicht haben.

In einigen Fällen wird der Anker nicht exportiert oder erstellt so wenig Daten, die wir erneut versuchen werden. Hier wird nur "kreateanchor" aufgerufen.

Eine abschließende Funktion im Export Pfad ist anchorfoundremote. Wenn ein anderes Gerät den Anker findet, teilt dieses Gerät den Host, und der Host verwendet diese als Signal, dass der Anker ein "guter Anker" ist und zwischengespeichert werden kann.

**Humi**

Wenn ein hololens einer Sitzung Beitritt, muss ein Anker importiert werden. In der Update-Funktion von unetanchormanager wird der anchorname abgerufen. Wenn sich der Anker Name ändert, beginnt der Import Vorgang. Zuerst versuchen wir, den Anker mit dem angegebenen Namen aus dem lokalen Anker Speicher zu laden. Wenn wir das bereits haben, können wir es verwenden, ohne die Daten erneut herunterzuladen. Wenn dies nicht der Fall ist, wird waitforanchor aufgerufen, um den Download zu initiieren.

Wenn der Download abgeschlossen ist, wird NetworkTransmitter_dataReadyEvent aufgerufen. Dadurch wird die Aktualisierungs Schleife signalisiert, um importasync mit den heruntergeladenen Daten aufzurufen. Importasync wird importcomplete aufrufen, wenn der Import Vorgang beendet ist. Wenn der Import erfolgreich ist, wird der Anker im lokalen Player Speicher gespeichert. PlayerController.cs bewirkt, dass anchorfoundremote aufgerufen wird, damit der Host weiß, dass ein guter Anker eingerichtet wurde.

### <a name="enjoy-your-progress"></a>Nutzen Sie Ihren Fortschritt

Dieses Mal hostet ein Benutzer mit einem hololens eine Sitzung mithilfe der Schaltfläche **Sitzung starten** in der Benutzeroberfläche. Andere Benutzer, sowohl auf hololens als auch auf einem immersiven Headset, wählen die Sitzung aus und wählen dann die Schaltfläche **Sitzung beitreten** in der Benutzeroberfläche aus. Wenn Sie über mehrere Personen mit hololens-Geräten verfügen, werden diese über rote Clouds verfügen. Es gibt auch eine blaue Cloud für jedes immersive Headset, aber die blauen Clouds werden nicht über den Headsets angezeigt, da die Headsets nicht versuchen, denselben weltweiten Koordinatenraum wie die hololens-Geräte zu finden.

Dieser Punkt im Projekt ist eine enthaltene Freigabe Anwendung. Dies funktioniert nicht sehr viel und kann als Baseline fungieren. In den nächsten Kapiteln beginnen wir damit, eine benutzerfreundliche Lösung zu entwickeln. Weitere Anleitungen zum Entwurf von freigegebenen Funktionen finden Sie hier.

## <a name="chapter-4---immersion-and-teleporting"></a>Kapitel 4: eintauchen und teleportierung

>[!VIDEO https://www.youtube.com/embed/kUHZ5tCOfvY]

### <a name="objectives"></a>Ziele

Sorgen Sie für die einzelnen Arten gemischter Reality-Geräte.

### <a name="what-we-will-build"></a>Build

Wir werden die Anwendung aktualisieren, um immersive Headset-Benutzer auf der Insel mit einer immersiven Ansicht zu platzieren. Hololens-Benutzer verfügen weiterhin über die Augen Ansicht der Insel. Benutzer jedes Gerätetyps können andere Benutzer sehen, wie Sie in der Welt angezeigt werden. Beispielsweise können immersive Headset-Benutzer die anderen Avatare in anderen Pfaden auf der Insel sehen, und Sie sehen die hololens-Benutzer als riesige Clouds oberhalb der Insel. Immersive Headset-Benutzer sehen auch den Cursor des Blicks Strahl des hololens-Benutzers, wenn der hololens-Benutzer die Insel ansieht. Hololens-Benutzern wird ein Avatar auf der Insel angezeigt, der jeden immersiven Headset-Benutzer darstellt.

**Aktualisierte Eingabe für das immersive Gerät:**

* Die Schaltflächen Linker und rechter Stoß Taste auf dem Xbox-Controller drehen den Player.
* Wenn Sie die Y-Schaltfläche auf dem Xbox-Controller halten, wird ein [teleportcursor](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) aktiviert. Wenn der Cursor einen drehenden Pfeil anzeigt, wenn Sie die Y-Schaltfläche loslassen, werden Sie an die Position des Cursors portiert.

### <a name="steps"></a>Schritte

* Mixedrealityteleport zu mixedrealitycameraparent hinzufügen
    * Wählen Sie in **Hierarchie**die Option " **Verwendung**von".
    * Aktivieren Sie im **Inspektor**das **Steuerelement Ebene**.
    * Wählen Sie in **Hierarchie**die Option **mixedrealitycameraparent**aus.
    * Klicken Sie in **Inspector**auf **Komponente hinzufügen**.
    * Geben Sie **gemischter Reality-Teleport** ein, und wählen Sie den

### <a name="digging-into-the-code"></a>Durchforsten des Codes

Immersive Headset-Benutzer werden mit einem Kabel auf ihren PCs getestet, aber unsere Insel ist größer als das Kabel. Um dies zu kompensieren, benötigen wir die Möglichkeit, die Kamera unabhängig von der Bewegung des Benutzers zu verschieben. Auf der [Seite "Komfort](comfort.md) " finden Sie weitere Informationen zum Entwerfen Ihrer gemischten Reality-Anwendung (insbesondere selbst Bewegung und Fortbewegung).

Um diesen Prozess zu beschreiben, ist es hilfreich, zwei Begriffe zu definieren. Zunächst ist **Dolly** das Objekt, das die Kamera unabhängig vom Benutzer verschiebt. Ein untergeordnetes Spielobjekt von **Dolly** ist die **Hauptkamera**. Die Hauptkamera wird an den Kopf des Benutzers angefügt.

Navigieren Sie im Projekt Panel zu **assetion\appprefabs\support\script\gamelogic** , und doppelklicken Sie auf **MixedRealityTeleport.cs**.

Mixedrealityteleport verfügt über zwei Aufträge. Zuerst wird die Drehung mithilfe der Stoßdämpfer verarbeitet. In der Funktion "Update" rufen wir "Button up" für "leftbumper" und "rightbumper" ab. "Getbuttonup" gibt nur "true" auf dem ersten Frame zurück, wenn eine Schaltfläche nicht mehr vorhanden ist. Wenn eine der beiden Schaltflächen ausgelöst wurde, wissen wir, dass der Benutzer sich drehen muss.

Wenn wir drehen, gehen wir mit einem einfachen Skript, das als "Fade-Steuerelement" bezeichnet wird, ein und blenden es aus. Dies geschieht, um zu verhindern, dass der Benutzer eine unnatürliche Bewegung sieht, was zu einem Unbehagen führen könnte. Der Einblend-und Ausgabe Effekt ist ziemlich einfach. Wir haben ein schwarzes Quad vor der **Hauptkamera**. Beim Ausblenden wird der Alpha-Wert von 0 auf 1 umgestellt. Dies bewirkt allmählich, dass die schwarzen Pixel des Quad-Elements dargestellt werden, und Sie verbergen alles dahinter. Beim zurückkehren wird der Alpha-Wert auf Null zurückgesetzt.

Wenn wir die Drehung berechnen, beachten Sie, dass wir unsere **Dolly** drehen, aber die Drehung um die **Hauptkamera**berechnen. Dies ist wichtig, wenn die **Hauptkamera** von 0, 0 und 0 entfernt wird, desto weniger genau wird eine Drehung um den Dolly aus der Sicht des Benutzers. Wenn Sie sich nicht um die Kameraposition drehen, wird der Benutzer in einem Bogen um den **Dolly** bewegt, anstatt sich zu drehen.

Der zweite Auftrag für mixedrealityteleport ist das Verschieben von **Dolly**. Dies erfolgt in setworldposition. Setworldposition nimmt die gewünschte Weltposition an, an der Position, an der der Benutzer seine Mitarbeiter bewohnen möchte. Wir müssen den **Dolly** an dieser Position abzüglich der lokalen Position der **Hauptkamera**platzieren, da dieser Offset jedem Frame hinzugefügt wird.

Ein zweites Skript ruft setworldposition auf. Sehen wir uns dieses Skript an. Navigieren Sie im Projekt Panel zu **assetion\appprefabs\support\script\gamelogic** , und doppelklicken Sie auf **TeleportScript.cs**.

Dieses Skript ist etwas komplizierter als mixedrealityteleport. Das Skript prüft, dass die Y-Schaltfläche auf dem Xbox-Controller gedrückt gehalten werden soll. Wenn die Schaltfläche gedrückt gehalten wird, wird ein teleportcursor gerendert, und das Skript wandelt einen Strahl von der Blick Position des Benutzers um. Wenn sich dieser Strahl auf eine Oberfläche mit mehr oder weniger zeigenden Zeichen stößt, wird die Oberfläche als eine gute Oberfläche für die teleportierung angesehen, und die Animation des Teleport Cursors wird aktiviert. Wenn der Strahl nicht mit einer Oberfläche in Konflikt steht, die mehr oder weniger nach oben zeigt, wird die Animation auf dem Cursor deaktiviert. Wenn die Y-Schaltfläche losgelassen wird und der berechnete Punkt des Strahls eine gültige Position ist, ruft das Skript setworldposition mit der Position ab, an der sich der Strahl überschneidet.

### <a name="enjoy-your-progress"></a>Nutzen Sie Ihren Fortschritt

Dieses Mal müssen Sie einen Freund suchen.

Ein Benutzer mit dem hololens-Host hostet wiederum eine Sitzung. Andere Benutzer werden an der Sitzung teilnehmen. Die Anwendung platziert die ersten drei Benutzer, um von einem immersiven Headset an einem der drei Pfade auf der Insel beizutreten. Sie können sich die Insel in diesem Abschnitt ansehen.

Beachten Sie die folgenden Details:

1. Sie können Gesichter in den Clouds sehen, was einem eingetauchten Benutzer hilft, zu sehen, welche Richtung ein hololens-Benutzer sucht.
2. Die Avatare auf der Insel haben Hals Striche, die sich drehen. Sie gehen nicht darauf ein, was der Benutzer tatsächlich macht (da wir nicht über diese Informationen verfügen), sondern eine schöne benutzerfreundliche Darstellung.
3. Wenn der hololens-Benutzer die Insel ansieht, können die eingetauchten Benutzer Ihren Cursor sehen.
4. Die Clouds, die die hololens-Benutzer darstellen, wandeln Schatten ein.

## <a name="chapter-5---finale"></a>Kapitel 5-Finale

>[!VIDEO https://www.youtube.com/embed/n_HDWJbfpNg]

### <a name="objectives"></a>Ziele

Erstellen Sie eine interaktive Interaktion zwischen den beiden Gerätetypen.

### <a name="what-we-will-build"></a>Build

Wenn ein Benutzer mit einem immersiven Headset in Kapitel 4 in der Nähe eines Rätsels auf der Insel kommt, erhalten die hololens-Benutzer eine QuickInfo mit einem Hinweis auf das Rätsel. Sobald alle immersiven Headset-Benutzer ihre Rätsel und den "Ready Pad" im Raketen Raum erhalten haben, wird die-Rakete gestartet.

### <a name="steps"></a>Schritte

* Wählen Sie in **Hierarchie**die Option " **Verwendung**von".
* Aktivieren Sie im **Inspektor**in der **Ebene-Steuerung**die Option **Zusammenarbeit aktivieren**.

### <a name="digging-into-the-code"></a>Durchforsten des Codes

Sehen wir uns nun LevelControl.cs an. Dieses Skript ist der Kern der Spiellogik und behält den Spielzustand bei. Da es sich hierbei um ein Multiplayer-Spiel mit uNet handelt, müssen wir verstehen, wie Daten fließen, zumindest gut genug, um dieses Tutorial zu ändern. Eine ausführlichere Übersicht über das uNet finden Sie in der Unity-Dokumentation.

Navigieren Sie im Projekt Panel zu **assetion\appprefabs\support\script\gamelogic** , und doppelklicken Sie auf **LevelControl.cs**.

Teilen Sie uns mit, wie ein immersives Headset anzeigt, dass Sie für den Raketenstart bereit sind. Die Bereitschaft der Startbereitschaft wird übermittelt, indem eines von drei boolesche in einer Liste von boolesche festgelegt wird, die den drei Pfaden auf der Insel entsprechen. Der boolesche Wert eines Pfads wird festgelegt, wenn sich der Benutzer, der dem Pfad zugewiesen ist, über dem braunen Pad innerhalb des Raketen Raums befindet. OK, jetzt können Sie die Details anzeigen.

Wir beginnen in der Update ()-Funktion. Sie werden feststellen, dass es eine "Cheat"-Funktion gibt. Wir haben dies bei der Entwicklung verwendet, um die Reihenfolge der Starts und der zurück Setzung zu testen Dies funktioniert nicht in der mehr Benutzer Funktionalität. Hoffentlich, wenn Sie die folgenden Informationen internalisieren, können Sie die Arbeit durchführen. Nachdem wir überprüft haben, um zu überprüfen, ob der lokale Player in den Spiel kommt. Wir möchten uns darauf konzentrieren, wie wir feststellen, dass wir das Ziel haben. Bei der Überprüfung bei if (eingetaucht) gibt es einen aufzurufenden prüfgoal-Vorgang hinter der **enablecollaboration** bool. Dies entspricht dem Kontrollkästchen, das Sie bei der Ausführung der Schritte für dieses Kapitel geprüft haben. Innerhalb von enablecollaboration wird ein Rückruf von checkgoal () angezeigt.

Checkgoal führt einige mathematische Berechnungen durch, um zu sehen, ob Sie mehr oder weniger auf dem Pad stehen. Wenn dies der Fall ist, Debuggen wir ". log", das beim Ziel eingetroffen ist, und dann rufe ich "sendatgoalmessage ()" auf. In sendatgoalmessage wird "playercontroller. sendatgoal" aufgerufen. Um einige Zeit zu sparen, hier ist der Code:

```cs
private void CmdSendAtGoal(int GoalIndex)
{
    levelState.SetGoalIndex(GoalIndex);
}
```

```cs
public void SendAtGoal(int GoalIndex)
{
    if (isLocalPlayer)
    {
        Debug.Log("sending at goal " + GoalIndex);
        CmdSendAtGoal(GoalIndex);
    }
}
```

Beachten Sie, dass sendatgoalmessage cmdsendatgoal aufruft, das "levelstate. setgoalindex" aufruft, das sich wieder in LevelControl.cs befindet. Auf den ersten Blick erscheint dies seltsam. Warum nicht einfach nur setgateindex aufrufen, sondern nicht das seltsame Routing durch den Player Controller? Der Grund hierfür ist, dass wir mit dem Datenmodell übereinstimmen, das uNet verwendet, um Daten synchron zu halten. Um das betrügen und übersetzen zu verhindern, erfordert uNet, dass jedes-Objekt über einen Benutzer verfügt, der über die Berechtigung zum Ändern der synchronisierten Variablen verfügt. Außerdem kann nur der Host (der Benutzer, der die Sitzung gestartet hat) Daten direkt ändern. Benutzer, die nicht der Host sind, aber über eine Autorität verfügen, müssen einen "Befehl" an den Host senden, um die Variable zu ändern. Standardmäßig verfügt der Host über eine Autorität für alle Objekte, mit Ausnahme des Objekts, das zur Darstellung des Benutzers erzeugt wird. In unserem Fall weist dieses Objekt das playercontoller-Skript auf. Es gibt eine Möglichkeit, eine Autorität für ein Objekt anzufordern und dann Änderungen vorzunehmen, aber wir wählen die Tatsache aus, dass der Player Controller über eine Self-Authority-und Route-Befehle über den Player Controller verfügt.

Anders gesagt: Wenn wir uns an unser Ziel gefunden haben, muss der Spieler den Host informieren, und der Host informiert alle anderen Personen.

Zurück in LevelControl.cs betrachten Sie setgoalindex. Hier legen wir den Wert eines Werts in einem SyncList (atgoal) fest. Beachten Sie, dass wir uns im Kontext des Hosts befinden. Ähnlich wie bei einem-Befehl kann ein RPC von dem Host ausgegeben werden, was dazu führt, dass alle Clients Code ausführen. Hier wird "rpccheckallgoals" aufgerufen. Jeder Client prüft einzeln, ob alle drei atziele festgelegt sind. wenn dies der Fall ist, wird die Ausführung gestartet.

### <a name="enjoy-your-progress"></a>Nutzen Sie Ihren Fortschritt

Im vorherigen Kapitel wird die Sitzung wie zuvor gestartet. Wenn die Benutzer im immersiven Headset das "Door" in Ihrem Pfad erreichen, wird eine QuickInfo angezeigt, die nur die hololens-Benutzer sehen können. Die hololens-Benutzer sind dafür verantwortlich, diesen Hinweis an die Benutzer im immersiven Headset zu übermitteln. Die Rakete wird in den Speicherplatz gestartet, sobald jeder Avatar auf dem entsprechenden braunen Pad innerhalb des Vulkans verstrichen ist. Die Szene wird nach 60 Sekunden zurückgesetzt, damit Sie Sie wiederholen können.

## <a name="see-also"></a>Weitere Informationen:

* [Mr-Eingabe 213: Motion-Controller](mixed-reality-213.md)
