---
title: Freigeben von 250 - HoloLens und immersive Headsets MR
description: Führen Sie diese exemplarische Vorgehensweise mit Unity, Visual Studio, HoloLens und Windows Mixed Reality-Headsets für die Details der Freigabe Hologramme zwischen mixed Reality-Geräte zu programmieren.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Holotoolkit, Mixedrealitytoolkit, Mixedrealitytoolkit-Unity, immersive motion, Controller, Freigabe, Xbox-Controller, Netzwerke, Geräteübergreifende
ms.openlocfilehash: 9e1cb0d168b8bf830b4477190516cd19caef7972
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593444"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

<br>

# <a name="mr-sharing-250-hololens-and-immersive-headsets"></a>MR 250 freigeben: HoloLens und immersive headsets

Mit der Flexibilität der universellen Windows-Plattform (UWP) ist es einfach, eine Anwendung erstellen, die mehrere Geräte umfasst. Durch diese Flexibilität können wir Umgebungen schaffen, die die Stärken der einzelnen Geräte nutzen. In diesem Tutorial werden Grundkenntnisse in einem freigegebenen behandelt, die sowohl HoloLens und Windows Mixed Reality immersive Headsets ausgeführt wird. Dieser Inhalt wurde ursprünglich auf der Microsoft Build 2017-Konferenz in Seattle, WA, USA gesendet.

**In diesem Tutorial wird Folgendes beschrieben:**

* Einrichten eines Netzwerks mit UNET an.
* Teilen Sie Hologramme in mixed Reality-Geräte.
* Richten Sie eine andere Ansicht der Anwendung, je nachdem, welche mixed Reality-Gerät verwendet wird.
* Erstellen Sie eine freigegebene Umgebung, in denen Benutzer mit HoloLens immersive Headsets durch einige einfache Rätsel Benutzerhandbuch.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td>MR 250 freigeben: HoloLens und immersive headsets</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Bevor Sie beginnen

### <a name="prerequisites"></a>Vorraussetzungen

* Ein Windows 10-PCs mit dem [erforderlichen Entwicklungstools](install-the-tools.md) und [so konfiguriert, dass eine immersive Windows Mixed Reality-Kopfhörer unterstützen](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).
* Ein Xbox-Controller, die mit Ihrem PC.
* Mindestens ein HoloLens-Gerät und eine immersive Kopfhörer.
* Ein Netzwerk, das UDP-Broadcast für die Ermittlung ermöglicht.

### <a name="project-files"></a>Projektdateien

* Herunterladen der [Dateien](https://github.com/Microsoft/MixedReality250/archive/master.zip) vom Projekt erforderlich sind. Extrahieren Sie die Dateien in einem leicht zu merken Speicherort.
* Dieses Projekt erfordert die [eine empfohlene Version von Unity mit Unterstützung für Windows Mixed Reality](install-the-tools.md).

>[!NOTE]
>Wenn Sie vor dem Herunterladen, den Quellcode ansehen möchten es [auf GitHub verfügbar](https://github.com/Microsoft/MixedReality250).

## <a name="chapter-1---holo-world"></a>Kapitel 1: Holo World

>[!VIDEO https://www.youtube.com/embed/IC0rp6rLiEc]

### <a name="objectives"></a>Ziele

Stellen Sie sicher, dass die Entwicklungsumgebung mit einem einfachen Projekt wechseln kann.

### <a name="what-we-will-build"></a>Was wir erstellen

Eine Anwendung, die ggf. ein Hologramm für HoloLens oder eine immersive Windows Mixed Reality-Kopfhörer anzeigt.

### <a name="steps"></a>Schritte
* Öffnen von Unity.
    * Wählen Sie **öffnen**.
    * Navigieren Sie zu, in dem Sie die Projektdateien extrahiert haben.
    * Klicken Sie auf **Ordner auswählen**.
    * *Es dauert ein wenig während für Unity, um das Projekt erstmals zu verarbeiten.*
* Überprüfen Sie die Mixed Reality in Unity aktiviert ist.
    * Öffnen Sie das Build-Dialogfeld "Settings" (**STRG + UMSCHALT + B** oder **Datei > Buildeinstellungen...** ).
    * Wählen Sie **universelle Windows-Plattform** klicken Sie dann auf **Plattform wechseln**.
    * Wählen Sie **Bearbeiten > Playereinstellungen**.
    * In der **Inspektor** auf der rechten Seite im Bereich, erweitern Sie **XR-Einstellungen**.
    * Überprüfen Sie die **virtuelle Realität unterstützt** Feld.
    * *Windows Mixed Reality sollte die Virtual Reality-SDK.*
* Erstellen einer Szene an.
    * In der **Hierarchie** klicken Sie mit der rechten Maustaste auf **Main Camera** wählen **löschen**.
    * Von **HoloToolkit > Eingabe > Prefabs** ziehen **MixedRealityCameraParent** auf die **Hierarchie**.
* Fügen Sie in die Szene Hologramme
    * Von **AppPrefabs** ziehen **Skybox** auf die **Szenenansicht**.
    * Von **AppPrefabs** ziehen **Managern** auf die **Hierarchie**.
    * Von **AppPrefabs** ziehen **Insel** auf die **Hierarchie**.
* Speichern und erstellen
    * Speichern (entweder **STRG + S +** oder **Datei > Szene speichern**)
    * Da es sich um eine neue Szene handelt, müssen Sie es nennen. Name spielt keine Rolle, aber wir SharedMixedReality verwenden.
* Exportieren Sie in Visual Studio
    * Öffnen Sie im Menü erstellen (**STRG + UMSCHALT + B** oder **Datei > Buildeinstellungen**)
    * Klicken Sie auf **öffnende Szenen hinzufügen.**
    * Überprüfen Sie **Unity C# Projekte**
    * Klicken Sie auf **Erstellen**.
    * In dem Datei-Explorer-Fenster, das angezeigt wird, erstellen Sie einen neuen Ordner namens **App**.
    * Mausklick die **App** Ordner.
    * Drücken Sie **Ordner auswählen.**
    * **Warten Sie, bis der Buildvorgang abgeschlossen**
    * Navigieren Sie in dem Datei-Explorer-Fenster, das angezeigt wird, in der **App** Ordner.
    * Doppelklicken Sie auf **SharedMixedReality.sln** zum Starten von Visual Studio
* Erstellen Sie in Visual Studio
    * Verwenden obere auf der Symbolleiste ändern, **Version** und **X86**.
    * Klicken Sie auf den Pfeil neben **lokalen Computer** , und wählen Sie **Gerät** für HoloLens bereitstellen
    * Klicken Sie auf den Pfeil neben **Gerät** , und wählen Sie **lokalen Computer** für das mixed Reality-Kopfhörer bereitstellen.
    * Klicken Sie auf **Debuggen -> Starten ohne Debugging** oder **STRG + F5** zum Starten der Anwendung.

### <a name="digging-into-the-code"></a>Detaillierte Untersuchung des Codes

Navigieren Sie im Projektpanel zu **Assets\HoloToolkit\Input\Scripts\Utilities** und doppelklicken Sie auf **MixedRealityCameraManager.cs** um ihn zu öffnen.

**Übersicht:** MixedRealityCameraManager.cs ist ein einfaches Skript, das Qualität-Ebene und Hintergrund Einstellungen basierend auf dem Gerät anpasst. Wesentliche Idee hier besteht HolographicSettings.IsDisplayOpaque, dadurch kann ein Skript, um festzustellen, ob das Gerät eine HoloLens ist (IsDisplayOpaque gibt "false" zurück) oder eine immersive Kopfhörer (IsDisplayOpaque gibt "true" zurück).

### <a name="enjoy-your-progress"></a>Nutzen Sie Ihre Arbeit

An diesem Punkt wird die Anwendung nur ggf. ein Hologramm gerendert. Wir werden die Hologramm Interaktion später hinzufügen. Sowohl für Geräte rendert der Hologramm gleich. Die immersive Kopfhörer wird auch mit einen blauen Himmel und Clouds Hintergrund gerendert.

## <a name="chapter-2---interaction"></a>Kapitel 2 – Interaktionen

>[!VIDEO https://www.youtube.com/embed/Lrb1y4sQRvI]

### <a name="objectives"></a>Ziele

Veranschaulicht das Verarbeiten der Eingabe für eine Windows Mixed Reality-Anwendung.

### <a name="what-we-will-build"></a>Was wir erstellen

Erstellen für die Anwendung aus Kapitel 1, werden wir Funktionen ermöglichen den Benutzer, die – Hologramm übernehmen, und platzieren Sie es auf einer Oberfläche der realen Welt in HoloLens oder auf eine virtuelle Tabelle in eine immersive Kopfhörer hinzufügen.

**Aktualisierungsprogramm für Eingabe:** Für HoloLens die select-Aktion ist die **tippbewegung**. Für immersive Headsets, verwenden wir die **ein** Schaltfläche auf der Xbox-Controller. Weitere Informationen zu Eingabe [beginnen Sie hier](gestures.md).

### <a name="steps"></a>Schritte
* Eingabe-Manager hinzufügen
    * Aus **HoloToolkit > Eingabe > Prefabs** ziehen **InputManager** zu **Hierarchie** als untergeordnetes Element des **Managern**.
    * Von **HoloToolkit > Eingabe > Prefabs > Cursor** ziehen **Cursor** zu **Hierarchie**.
* Räumliche Zuordnung hinzufügen
    * Von **HoloToolkit > SpatialMapping > Prefabs** ziehen **SpatialMapping** zu **Hierarchie**.
* Hinzufügen von virtuellen Playspace
    * In **Hierarchie** erweitern **MixedRealityCameraParent** wählen **Grenze**
    * In **Inspektor** Bereich aktivieren, aktivieren Sie das Kontrollkästchen **Grenze**
    * Von **AppPrefabs** ziehen **VRRoom** zu **Hierarchie**.
* Add WorldAnchorManager
    * In **Hierarchie**Option **Managern**.
    * In **Inspektor**, klicken Sie auf **Add Component**.
    * Typ **Welt Anker Manager**.
    * Wählen Sie **Welt Anker Manager** hinzugefügt.
* Fügen Sie auf der ganzen Insel TapToPlace
    * In **Hierarchie**, erweitern Sie **Insel**.
    * Wählen Sie **MixedRealityLand**.
    * In **Inspektor**, klicken Sie auf **Add Component**.
    * Typ **tippen zu Ort** und wählen Sie ihn.
    * Überprüfen Sie **Platzieren von übergeordneten auf Tap**.
    * Legen Sie **Platzierung Offset** zu **("0", "0,1", "0")**.
* Speichern Sie und erstellen Sie wie zuvor

### <a name="digging-into-the-code"></a>Detaillierte Untersuchung des Codes

**Script 1 - GamepadInput.cs**

Navigieren Sie im Projektpanel zu **Assets\HoloToolkit\Input\Scripts\InputSources** und doppelklicken Sie auf **GamepadInput.cs** um ihn zu öffnen. Aus dem gleichen Pfad im Projektfenster auch doppelklicken **InteractionSourceInputSource.cs**.

Beachten Sie, dass beide Skripts eine allgemeine Basisklasse BaseInputSource.

BaseInputSource behält einen Verweis auf ein InputManager, die ein Skript zum Auslösen von Ereignissen ermöglicht. In diesem Fall ist das Ereignis InputClicked relevant. Dies ist wichtig zu beachten, wenn wir zum Skript 2 TapToPlace erhalten wird. Im Fall von GamePadInput wir Abfragen für die eine Schaltfläche auf dem Controller gedrückt wird, und wir das InputClicked-Ereignis auszulösen. Im Fall von InteractionSourceInputSource lösen wir die InputClicked Ereignis als Antwort auf die TappedEvent.

**Skript 2 - TapToPlace.cs**

Navigieren Sie im Projektpanel zu **Assets\HoloToolkit\SpatialMapping\Scripts** und doppelklicken Sie auf **TapToPlace.cs** um ihn zu öffnen.

Erstes möchten, dass viele Entwickler implementieren, wenn eine Holographic-Anwendung erstellen, werden Hologramme mit Gesten Eingabe verschoben. Daher haben wir versuchte, um das Skript gründlich zu kommentieren. Einige Dinge sind für dieses Tutorial wichtige.

Notieren Sie sich zunächst, dass TapToPlace IInputClickHandler implementiert. IInputClickHandler macht die Funktionen, die das InputClicked von ausgelöste Ereignis GamePadInput.cs oder InteractionSourceInputSource.cs zu behandeln. OnInputClicked wird aufgerufen, wenn eine BaseInputSource einen Klick erkennt, während das Objekt mit TapToPlace im Fokus befindet. Entweder Airtapping für HoloLens oder drücken die A-Taste auf der Xbox-Controller wird das Ereignis ausgelöst.

Zweitens ist der Code in aktualisieren, um festzustellen, ob eine Oberfläche Anzeigedaten, damit wir das spielobjekt, auf einer Oberfläche, wie eine Tabelle platzieren können ausgeführt werden. Die immersive Kopfhörer verfügt nicht über ein Konzept von echten Oberflächen, also das Objekt, das Tabelle oben (Vroom > TableThingy > Cube) gekennzeichnet wurde mit der Physik SpatialMapping, also des Strahls, umgewandelt in Update mit der virtuellen Tabelle oben in Konflikt stehen wird.

### <a name="enjoy-your-progress"></a>Nutzen Sie Ihre Arbeit

Dieses Mal können Sie der Insel, verschieben Sie ihn auswählen. Für HoloLens können Sie die Insel auf eine echte Oberfläche verschieben. In der immersive Kopfhörer können Sie die Insel auf der virtuellen Tabelle verschieben, die hinzugefügt wurden.

## <a name="chapter-3---sharing"></a>Kapitel 3 - Freigabe

>[!VIDEO https://www.youtube.com/embed/1diycJvxfDc]

### <a name="objectives"></a>Ziele

Stellen Sie sicher, dass das Netzwerk ordnungsgemäß konfiguriert ist und detail, wie Sie räumliche Anker zwischen Geräten gemeinsam genutzt werden.

### <a name="what-we-will-build"></a>Was wir erstellen

Wir werden unser Projekt in ein Multiplayer-Projekt konvertieren. Wir werden-Host oder Join-Sitzungen Benutzeroberfläche und Logik hinzufügen. HoloLens-Benutzer sehen miteinander in der Sitzung mit Clouds über ihre Mal "Kopf" und immersive Kopfhörer-Benutzer haben Clouds Nähe, in dem der Anker ist. Benutzer in der immersive Headsets werden die HoloLens-Benutzern im Hinblick auf den Ursprung der Szene angezeigt. HoloLens-Benutzer sehen alle Hologramm der Dateninsel am selben Ort. Es ist zu beachten Sie, dass die Benutzer in der immersive Headsets werden auf der ganzen Insel bei der nicht in diesem Kapitel verhält sich ähnlich, HoloLens, mit einem Vögel Einblick in die Insel Schlüssel.

### <a name="steps"></a>Schritte
* Remove-Insel und VRRoom
    * In **Hierarchie** mit der rechten Maustaste **Insel** wählen **löschen**
    * In **Hierarchie** mit der rechten Maustaste **VRRoom** wählen **löschen**
* Hinzufügen von Usland
    * Von **AppPrefabs** ziehen **Usland** zu **Hierarchie**.
* Von **AppPrefabs** ziehen Sie jede der folgenden **Hierarchie**:
    * **UNETSharingStage**
    * **UNetAnchorRoot**
    * **UIContainer**
    * **DebugPanelButton**
* Speichern Sie und erstellen Sie wie zuvor

### <a name="digging-into-the-code"></a>Detaillierte Untersuchung des Codes

Navigieren Sie im Projektpanel zu **Assets\AppPrefabs\Support\SharingWithUnet\Scripts** und doppelklicken Sie auf **UnetAnchorManager.cs**. In der Nähe magische ist die Fähigkeit einer HoloLens-Tracking-Informationen mit einer anderen HoloLens freigeben, so, dass sowohl für Geräte mit den gleichen Speicherplatz freigeben können. Die Leistungsfähigkeit von mixed Reality ist aktiv, wenn zwei oder mehr Menschen mit denselben digitale Daten zusammenarbeiten können.

Einige wichtige Punkte in diesem Skript:

Beachten Sie in der Startfunktion, die die Überprüfung auf **IsDisplayOpaque**. In diesem Fall nehmen wir, dass es sich bei der Anker hergestellt wird. Dies ist, da die immersive Headsets keine Möglichkeit zum Importieren oder Exportieren von Anker verfügbar machen. Wenn wir auf ein HoloLens ausgeführt werden, jedoch wird dieses Skript Freigabe Anker zwischen den Geräten implementiert. Das Gerät, das die Sitzung gestartet wird, wird einen Anker für den Export von erstellt. Das Gerät, das einer Sitzung Beitritt fordert den Anker auf dem Gerät, das die Sitzung gestartet wurde.

**Exportieren:**

Wenn ein Benutzer eine Sitzung erstellt, wird die NetworkDiscoveryWithAnchors UNETAnchorManagers CreateAnchor-Funktion aufrufen. Sehen wir uns CreateAnchor Flow an.

Zunächst wird eine Überprüfung, beseitigen alle Daten, die wir für die vorherigen Anker gesammelt haben kann. Dann prüfen wir, liegt ein zwischengespeicherter Anker geladen. Die Anker-Daten ist meist zwischen 5 und 20 MB, sodass die Wiederverwendung von zwischengespeicherten Anker speichern kann, auf die Menge der Daten, die über das Netzwerk übertragen möchten. Wir sehen später noch Funktionsweise. Auch wenn wir den Anker wiederverwenden, müssen wir dem Anker, die Daten für den Fall, dass ein neuer Client auf, die joins keine Anker zu erhalten.

Apropos beim Abrufen der Anker-Daten bereit, macht die WorldAnchorTransferBatch-Klasse die Funktionalität zum Anker-Daten, die für das Senden an ein anderes Gerät oder -Anwendung und die Funktionalität zum Importieren der Anker-Daten vorbereiten. Da wir auf dem Exportpfad sind, werden wir die WorldAnchorTransferBatch unsere Anker hinzu, und rufen Sie die ExportAsync-Funktion. ExportAsync ruft dann den Rückruf WriteBuffer zu exportierenden Daten generieren. Wenn alle Daten wurden exportiert wird ExportComplete aufgerufen werden. In WriteBuffer fügen wir den Datenblock, um eine Liste, die wir für den Export zu halten. In ExportComplete konvertieren wir die Liste in ein Array. Die Variable AnchorName auch festgelegt ist löst die anderen Geräte Anker anfordern, wenn sie nicht darüber verfügen.

In einigen Fällen, die der Anker wird nicht zu exportieren oder erstellt so wenig Daten, versucht es erneut. Hier rufen wir einfach CreateAnchor erneut aus.

Eine letzte Funktion in den Exportpfad ist AnchorFoundRemotely. Bei den Anker in ein anderes Gerät gefunden wird, das Gerät informiert den Host und der Host werden verwendet, die als Signal, dass der Anker ein "guter Anker" ist und kann zwischengespeichert werden.

**Importieren von:**

Wenn eine HoloLens eine Sitzung beitritt, muss es einen Anker zu importieren. In UNETAnchorManagers Update-Funktion wird die AnchorName abgerufen. Wenn der Ankername geändert wird, startet der Importvorgang. Versuchen Sie zunächst, wir den Anker mit dem angegebenen Namen aus dem lokalen Premium-Speicher zu laden. Wenn wir die bereits darüber verfügen, können wir es verwenden, ohne die Daten erneut herunterzuladen. Wenn wir nicht darüber verfügen, rufen wir WaitForAnchor dem Initiieren des Downloads wird.

Wenn der Download abgeschlossen ist, wird die NetworkTransmitter_dataReadyEvent aufgerufen. Dies signalisiert der Aktualisierungsschleife des aufzurufenden ImportAsync mit den heruntergeladenen Daten. ImportAsync wird ImportComplete aufgerufen, wenn der Importvorgang abgeschlossen ist. Wenn der Import erfolgreich ist, wird der Anker im lokalen Player-Speicher gespeichert werden. "Playercontroller.cs" ruft tatsächlich die AnchorFoundRemotely, denen der Host weiß, dass ein guter Anker eingerichtet wurde.

### <a name="enjoy-your-progress"></a>Nutzen Sie Ihre Arbeit

Dieses Mal ein Benutzer mit einem HoloLens Hosten einer Sitzung mit dem **Sitzung starten** Schaltfläche in der Benutzeroberfläche. Andere Benutzer, sowohl auf HoloLens oder eine immersive Kopfhörer, wählen Sie die Sitzung und wählen Sie dann die **Sitzung beitreten** Schaltfläche in der Benutzeroberfläche. Wenn Sie mehrere Benutzer mit HoloLens-Geräte verfügen, müssen sie über ihre Mal "Kopf" red-Clouds. Außerdem wird eine blaue Cloud für jeden immersive Kopfhörer, aber die blaue Clouds werden nicht über die Headsets, wie die Headsets nicht den gleichen koordinierten World-Bereich wie die HoloLens-Geräte ermitteln möchten.

Diesem Punkt im Projekt ist eine enthaltene Anwendung für die Freigabe. es nicht sehr viel und kann als Basislinie dienen. Beginnen wir in den nächsten Kapiteln erstellen eine Umgebung für die Freude bereitet. Um weitere Anleitungen zu gemeinsamen Erfahrung Entwurf zu erhalten, finden Sie hier.

## <a name="chapter-4---immersion-and-teleporting"></a>Kapitel 4: Immersion und teleporting

>[!VIDEO https://www.youtube.com/embed/kUHZ5tCOfvY]

### <a name="objectives"></a>Ziele

Die Erfahrung mit jeder Art von mixed Reality-Geräte zu erfüllen.

### <a name="what-we-will-build"></a>Was wir erstellen

Die Anwendung auf der ganzen Insel mit einer immersive Sicht einzufügenden immersive Kopfhörer Benutzer werden aktualisiert. HoloLens-Benutzer haben weiterhin die Vogelperspektive der Dateninsel. Benutzer von jeder Gerätetyp können andere Benutzer sehen, wie sie in der ganzen Welt angezeigt werden. Z. B. immersive Kopfhörer Benutzer sehen die anderen Avatare auf andere Pfade auf der ganzen Insel, und sie sehen die HoloLens-Benutzer als giant Clouds über Insel. Immersive Kopfhörer-Benutzer sehen den Cursor des Benutzers, der die HoloLens Blicke Chow auch, wenn der Benutzer HoloLens Insel angezeigt wird. HoloLens-Benutzer sehen einen Avatar auf der Insel, jede immersive Kopfhörer-Benutzer darstellt.

**Aktualisierte Eingaben für die immersiven Gerät:**
* Die linke rekordzahl und rechts rekordzahl Schaltflächen auf der Xbox-Controller Drehen des Players
* Halten die Schaltfläche "Y" auf dem Xbox-Controller wird aktiviert. eine [Teleport](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) Cursor. Wenn der Cursor mit Pfeil wird ein drehindikator hat, wenn Sie die Schaltfläche "Y" freigeben, werden Sie Teleported auf die Position des Cursors.

### <a name="steps"></a>Schritte
* MixedRealityCameraParent MixedRealityTeleport hinzugefügt
    * In **Hierarchie**Option **Usland**.
    * In **Inspektor**, aktivieren Sie **Kontrolle**.
    * In **Hierarchie**Option **MixedRealityCameraParent**.
    * In **Inspektor**, klicken Sie auf **Add Component**.
    * Typ **Mixed Reality Teleport** und wählen Sie ihn.

### <a name="digging-into-the-code"></a>Detaillierte Untersuchung des Codes

Immersive Kopfhörer Benutzer werden an ihre PCs über ein Kabel angeschlossen werden, aber unsere Insel ist größer als das Kabel lang ist. Um dies auszugleichen, benötigen wir die Möglichkeit, verschieben Sie die Kamera unabhängig von der während der Übertragung des Benutzers. Informieren Sie sich die [bequem Seite](comfort.md) für Weitere Informationen zum Entwerfen Ihrer mixed Reality-Anwendung (insbesondere selbst während der Übertragung und Locomotion).

Um diesen Prozess zu beschreiben werden nützlich, um zwei Begriffe definiert. Zuerst **Transportwagen** wird das Objekt, das die Kamera unabhängig vom Benutzer verschoben werden. Von einem untergeordneten-spielobjekt der **Transportwagen** werden die **Hauptkamera**. Der Hauptkamera ist an des Benutzers Head angefügt.

Navigieren Sie im Projektpanel zu **Assets\AppPrefabs\Support\Scripts\GameLogic** und doppelklicken Sie auf **MixedRealityTeleport.cs**.

MixedRealityTeleport verfügt über zwei Aufträge. Zuerst verarbeitet sie mithilfe der Rückstoßelemente Drehung. In der Update-Funktion Fragen wir nach "ButtonUp" LeftBumper und RightBumper ab. GetButtonUp nur gibt true zurück, auf den ersten Frame, die, den eine Schaltfläche aktiviert ist, nachdem er sich zuvor nach unten. Wenn eine der Schaltflächen ausgelöst worden wäre, wissen wir, dass der Benutzer muss zum Drehen.

Wenn wir drehen wir ausblenden und mit einem einfachen Skript namens "fade Steuerelement" eingeblendet. Wir tun dies, um zu verhindern, dass den Benutzer eine unnatürliche Verschiebung Dies kann zu übermäßig führen angezeigt. Das Ausblenden ist wirksam ein-und recht einfach. Wir haben die schwarzen Gevierts hängt vor der **Hauptkamera**. Wenn ausgeblendet wird, wechseln wir den alpha-Wert zwischen 0 und 1. Dadurch wird schrittweise die schwarze Pixel den Quad-Rendern und verschleiern etwas dahinter. Wenn wieder eingeblendet wechseln wir den alpha-Wert auf Null zurückgesetzt.

Wenn wir die Drehung berechnen, beachten Sie, dass wir Rotation ausführen unserer **Transportwagen** aber berechnen die Drehung um die **Hauptkamera**. Dies ist wichtig, da je weiter die **Hauptkamera** wird von 0,0,0, desto weniger genau eine Drehung um die Transportwagen würde aus der Perspektive des Benutzers werden. In der Tat, wenn Sie nicht rund um die Kameraposition drehen, der Benutzer wechselt in einen Bogen rund um die **Transportwagen** anstatt zu drehen.

Der zweite Auftrag für MixedRealityTeleport ist, behandelt das Verschieben der **Transportwagen**. Dies erfolgt in SetWorldPosition. SetWorldPosition nimmt die gewünschten World-Position, die Position, in denen der Benutzer Percieve möchte, die sie darstellen. Müssen wir fügen unserer **Transportwagen** an dieser Position minus der lokalen Position des der **Hauptkamera**, wie dem Offset jeden Frame hinzugefügt werden.

Ein zweites Skript ruft SetWorldPosition. Betrachten Sie das Skript aus. Navigieren Sie im Projektpanel zu **Assets\AppPrefabs\Support\Scripts\GameLogic** und doppelklicken Sie auf **TeleportScript.cs**.

Dieses Skript ist ein bisschen komplizierter als das MixedRealityTeleport. Das Skript überprüft für die Y-Schaltfläche gedrückt halten, auf dem Xbox-Controller. Während der gehalten wird, wird unten eine Teleport Cursor wird gerendert, und das Skript wandelt ein Strahl von Blicke-Position des Benutzers. Wenn, Chow mit einer Oberfläche kollidiert, der größer oder kleiner ist nach oben weisenden die Oberfläche betrachtet eine gute Zeichenoberfläche Teleport, und die Animation für den Cursor Teleport wird aktiviert. Wenn es sich bei der Strahl nicht mit einer Oberfläche, die mehr oder weniger zeigen, in Konflikt stehen, ist die Animation für den Cursor deaktiviert. Wenn die Schaltfläche "Y" wird veröffentlicht, und der berechneten Punkt des Strahls eine gültige Position ist, wird das Skript SetWorldPosition mit der Position, die vom Strahl geschnitten wurde, aufgerufen.

### <a name="enjoy-your-progress"></a>Nutzen Sie Ihre Arbeit

Diesmal müssen Sie einen Freund zu finden.

Auch hier hostet ein Benutzer mit der HoloLens eine Sitzung. Andere Benutzer werden der Sitzung beizutreten. Die Anwendung werden die ersten drei Benutzern den Beitritt in eine immersive Kopfhörer auf einem von drei wegen, auf der ganzen Insel zu platzieren. Insel in diesem Abschnitt untersuchen können.

Details zu beachten:
1. Sie können sehen, Gesichtern in der Cloud, wodurch einen aufbewahrt Benutzer zur Richtung, finden Sie unter Benutzer HoloLens sieht.
2. Die Avatare auf der ganzen Insel haben Necks, die zu drehen. Sie wird nicht einhalten, wozu dient der Benutzer ist real Realität (wir keine dieser Informationen haben), sondern stellt dies eine gute Erfahrung.
3. Wenn es sich bei der HoloLens-Benutzer auf der ganzen Insel sucht, können der aufbewahrt Benutzern ihren Cursor angezeigt.
4. Die Clouds, die die Benutzer HoloLens darstellen Schatten.

## <a name="chapter-5---finale"></a>Kapitel 5 - Erfahrung

>[!VIDEO https://www.youtube.com/embed/n_HDWJbfpNg]

### <a name="objectives"></a>Ziele

Erstellen Sie eine interaktive Umgebung für die Zusammenarbeit zwischen den beiden Typen.

### <a name="what-we-will-build"></a>Was wir erstellen

Erstellen in Kapitel 4, wenn ein Benutzer mit einem immersive Kopfhörer in der Nähe eines Rätsels auf der ganzen Insel erhält, werden die HoloLens-Benutzer eine QuickInfo mit einen Hinweis für das Rätsel angezeigt. Nachdem alle immersive Kopfhörer Benutzer über die Puzzles und auf das Feld"bereit" im Raum Rocket erhalten haben, wird die Rocket gestartet.

### <a name="steps"></a>Schritte
* In **Hierarchie**Option **Usland**.
* In **Inspektor**im **Kontrolle**, überprüfen Sie **Zusammenarbeit ermöglichen**.

### <a name="digging-into-the-code"></a>Detaillierte Untersuchung des Codes

Jetzt sehen wir uns am LevelControl.cs. Dieses Skript ist das Kernstück von die Spiellogik und behält den Status des spielen. Da dies ein Multiplayer-Spiel mithilfe von UNET ist müssen wir verstehen, mindestens gut genug den Datenfluss so ändern Sie in diesem Tutorial. Eine vollständige Übersicht über UNET finden Sie in der Unity-Dokumentation.

Navigieren Sie im Projektpanel zu **Assets\AppPrefabs\Support\Scripts\GameLogic** und doppelklicken Sie auf **LevelControl.cs**.

Lassen Sie uns wissen Sie, wie eine immersive Kopfhörer gibt an, dass sie bereit für den Start Rocket. Start-Bereitschaft Rocket wird durch Festlegen einer der drei Knoteneigenschaften in einer Liste von Knoteneigenschaften, die die Pfade auf der ganzen Insel entsprechen, kommuniziert. Des Pfads "bool" wird festgelegt, wenn der Benutzer, die dem Pfad zugewiesene über das Pad "brown" in den Raum Rocket ist. Okay, jetzt in den Details.

Es wird in die Update()-Funktion gestartet. Sie werden feststellen, dass eine Funktion "Spickzettel" vorhanden ist. Es bedeutete das in der Entwicklung, Testen des Rocket Start, und setzen Sie Sequenz. Andernfalls funktioniert es nicht in die Multi-Benutzeroberfläche. Hoffentlich können mit der Zeit, die Sie die folgenden Informationen verinnerlichen Sie dafür erforderlichen. Nachdem wir überprüfen, um festzustellen, ob wir cheat sollten, überprüfen wir festzustellen, ob der lokale Player befinden, ist. Wir möchten konzentrieren, wie wir, dass wir auf das Ziel sind suchen. In der If (befinden) zu überprüfen, erfolgt ein Aufruf von CheckGoal ausblenden hinter der **EnableCollaboration** "bool". Dies entspricht das Kontrollkästchen, die, das Sie überprüft haben, während Sie die Schritte in diesem Kapitel. Innerhalb von EnableCollaboration sehen wir einen Aufruf von CheckGoal().

CheckGoal führt einiger Berechnungen aus, um festzustellen, ob es sind mehr oder weniger ständigen Block auf. Wir rufen wir "Debug.log", "Am Ziel angekommen" und anschließend "SendAtGoalMessage()". In SendAtGoalMessage rufen wir playerController.SendAtGoal. Um Zeit zu sparen, ist hier der Code ein:

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

Beachten Sie, dass SendAtGoalMessage CmdSendAtGoal, welche levelState.SetGoalIndex Aufrufe aufruft, die wieder LevelControl.cs aufweist. Auf den ersten Blick scheint dies seltsam. Warum nicht rufen einfach SetGoalIndex anstatt diese seltsame routing über den Player-Controller? Der Grund ist, dass wir in das Datenmodell übereinstimmen, die UNET verwendet wird, um Daten synchron zu halten. Um Aktivitäten und arbeitsspeicherüberlastung zu vermeiden, erfordert UNET an, dass jedes Objekt verfügt über einen Benutzer, wer hat die synchronisierten Variablen zu ändern. Darüber hinaus kann nur vom Host (der Benutzer, die die Sitzung gestartet wurde) Daten direkt ändern. Benutzer, die nicht dem Host, jedoch haben die Autorität für die "Command" an den Host gesendet, wodurch die Variable geändert werden müssen. Standardmäßig hat der Host Autorität über alle Objekte, mit Ausnahme des Objekts erzeugt werden, um den Benutzer darzustellen. In diesem Fall hat dieses Objekt das playercontoller-Skript. Es gibt eine Möglichkeit zum Anfordern von Autorität für die ein Objekt, und klicken Sie dann Änderungen vornehmen, aber wählen wir die Tatsache nutzen, dass die Player-Controller selbst Autorität und folgenden Route-Befehle über den Player-Controller verfügt.

Anders ausgedrückt, haben wir uns an unser Ziel gefunden, muss des Spielers den Host darüber informieren und der Host wird angewiesen, alle anderen Benutzer.

Im LevelControl.cs SetGoalIndex ansehen. Hier wird den Wert eines Werts in einem Synclist (AtGoal) festgelegt. Denken Sie daran, dass wir im Kontext des Hosts arbeiten, während dies zu tun. Ähnlich wie ein Befehl ist RPC etwas, das der Host ausgeben kann, die alle Clients, die zum Ausführen von Code führen. Hier rufen wir "RpcCheckAllGoals". Jeder Client einzeln aktivieren, um festzustellen, ob alle drei AtGoals festgelegt sind, und wenn dies der Fall ist, starten den Rocket.

### <a name="enjoy-your-progress"></a>Nutzen Sie Ihre Arbeit

Basierend auf dem vorhergehenden Kapitel wird starten die Sitzung als vor dem wir. Diesmal, wie die Benutzer immersive Kopfhörer abrufen, die "Tür" auf ihrem Pfad, wird eine QuickInfo angezeigt werden, dass nur die HoloLens-Benutzer sehen können. Die HoloLens-Benutzer sind verantwortlich für die Kommunikation dieser Anhaltspunkt für die Benutzer in der immersive Kopfhörer. Nach jeder Avatar auf die entsprechende braunen Pad in Vulkane-Datenbankobjekt ausgeführt hat, wird die Rocket Space gestartet. Nach 60 Sekunden wird die Szene zurückgesetzt, sodass Sie es nochmal schaffen können.

## <a name="see-also"></a>Siehe auch
* [MR Eingabe 213: Motion-Controller](mixed-reality-213.md)
