---
title: Motion-Controller
description: Informationen zu den Controller während der Übertragung Mixed Reality.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 6dof Controller Motion-Controller
ms.openlocfilehash: fc6b0dcf7f338224af9ea9bc59e07187c33adda2
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024552"
---
# <a name="motion-controllers"></a>Motion-Controller

Während der Übertragung Controller sind [Hardwarezubehör](hardware-accessories.md) , mit denen Benutzer eine Aktion in mixed Reality. Ein Vorteil der Motion-Controller über [Gesten](gestures.md) besteht darin, dass der Controller eine genaue Position im Raum dargestellt und ermöglicht eine differenzierte Interaktion durch digitale Objekte. Für Windows Mixed Reality immersive Headsets sind während der Übertragung Controller der einfachste Weg, dass Benutzer in ihrer Umgebung eine Aktion ausführt.

![Windows Mixed Reality-Motion-Controller](images/winmr-ck-1080x1080-350px.jpg)


## <a name="device-support"></a>Unterstützung von Geräten

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Funktion</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
     <td><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></td>
</tr>
<tr>
     <td>Motion-Controller</td>
     <td>❌</td>
     <td>❌</td>
     <td>✔️</td>
</tr>
</table>

## <a name="hardware-details"></a>Hardwaredetails

>[!VIDEO https://www.youtube.com/embed/1nlcdDNOdm8]

Windows Mixed Reality-Motion-Controller bieten präzise und reaktionsfähige nachverfolgung von Verschieben von Daten in Ihrem Blickfeld verwenden die Sensoren in die immersive Kopfhörer, was bedeutet, dass besteht keine Notwendigkeit zum Installieren von Hardware an den Wänden in Ihrem Bereich. Diese Controller während der Übertragung werden die gleichen leichte Einrichtung und Portabilität als Windows Mixed Reality immersive Headsets anbieten. Unsere Partner Gerät planen, vermarkten und verkaufen diese Controller in Retail Regalen diesem fest.

![Lernen Sie kennen Ihre controller](images/controllerimage-750px.png)<br>
*Lernen Sie kennen Ihre controller*

**Funktionen:**
* Optische Überwachung
* Trigger
* Ziehen Sie die Schaltfläche "
* Ministick
* Touchpad

## <a name="setup"></a>Setup

### <a name="before-you-begin"></a>Vorbemerkungen

**Sie benötigen:**
* Ein Satz von zwei Motion-Controller.
* Vier AA Batterien.
* Bluetooth-4.0 kann PC.

**Suchen Sie nach Updates für Windows, Unity und Treiber**
* Besuchen Sie [Installieren der Tools](install-the-tools.md) für die bevorzugte Versionen von Windows, Unity, usw., für die Entwicklung von mixed Reality.
* Stellen Sie sicher, dass die aktuelle [Kopfhörer und Bewegung Controller-Treiber](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software).

### <a name="pairing-controllers"></a>Kopplung von Controllern

Motion-Controller mit Host-PCs verbunden werden können mithilfe von Windows-Einstellungen wie jedes andere Bluetooth-Gerät.

1. Schließen Sie 2 AA Batterien, an der Rückseite des Controllers. Lassen Sie die Akkuabdeckung deaktiviert unverändert.
2. Wenn Sie einen externen USB-Bluetooth-Adapter anstelle einer integrierten Bluetooth-Funktion verwenden, überprüfen Sie die [Bluetooth-bewährte](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) vor dem fortfahren. Für desktop-Konfiguration mit integrierten Radio stellen Sie sicher, dass die Antenne verbunden ist.
3. Open **Windows-Einstellungen** -> **Geräte** -> **Bluetooth hinzufügen oder ein anderes Gerät** -> **Bluetooth** und entfernen Sie alle früheren Instanzen von "Motion – direkt" und "Motion-Controller – Links". Überprüfen Sie auch andere Kategorie "Geräte" am unteren Rand der Liste.
4. Wählen Sie **Bluetooth hinzufügen oder ein anderes Gerät** und die Datenbank ab, um Bluetooth-Geräte zu ermitteln.
5. Halten Sie die Windows-Schaltfläche des Controllers, um den Controller einschalten, freigeben, sobald es Buzzes.
6. Drücken und halten Sie die kopplungstaste (Registerkarte im Depot Akku), bis die LEDs beginnen zeitverzerrten.
7. Warten Sie, "Motion - Links" oder "Während der Übertragung Controllers - rechten" am Ende der Liste angezeigt werden. Wählen Sie auf Paar. Controller wird einmal Vibrieren, wenn eine Verbindung besteht.

   ![Wählen Sie während der Übertragung Controller-Paar aus, wenn mehrere Instanzen von erscheinen Ende der Liste auswählen](images/450px-bluetooth-add-a-device-300px.png)<br>
   *Wählen Sie "Während der Übertragung von Controller" Pair; Wenn mehrere Instanzen vorhanden sind, wählen Sie eine zwischen dem unteren Rand der Liste*
   
8. Sehen Sie den Controller in die Bluetooth-Einstellungen unter angezeigt **"Maus, Tastatur und Stift" Kategorie** als **verbunden**. An diesem Punkt erhalten Sie möglicherweise eine Aktualisierung der Firmware – finden Sie unter [nächsten Abschnitt](motion-controllers.md#updating-controller-firmware).
9. Schließen Sie die Batterie Cover wieder.
10. Wiederholen Sie Schritte 1 bis 9 für den zweiten Controller aus.

Nach der Kopplung wurde erfolgreich beide Controller aus, sollte Ihre Einstellungen sehen folgendermaßen unter **"Maus, Tastatur und Stift" Kategorie** 

   ![Motion-Controller verbunden](images/450px-motion-controller-connected-300px.png)<br>
   *Motion-Controller verbunden*

Wenn der Controller nach der Kopplung deaktiviert sind, wird deren Status als gepaarten angezeigt. Wenn der Controller dauerhaft unter "Andere Geräte" Kopplung Kategorie nur teilweise abgeschlossen wurden möglicherweise und muss erneut ausgeführt werden, um die Controller funktionale erhalten bleiben.

### <a name="updating-controller-firmware"></a>Aktualisieren der Controllerfirmware

* Wenn eine immersive Kopfhörer auf Ihren PC verbunden ist, und neue Controllerfirmware zur Verfügung steht, wird die Firmware auf Ihre Controller während der Übertragung automatisch das nächste Mal übertragen, die, das Sie aktiviert sind. Controller-Firmware-Updates werden von einem Muster von leuchtenden LED Quadranten in einer kreisförmigen Bewegung, und 1 bis 2 Minuten in Anspruch nehmen.
* Nach dem Update der Firmware abgeschlossen ist, werden der Controller neu starten und erneut eine Verbindung herzustellen. Beide Controller sollte jetzt verbunden werden. 
    
    ![Controller verbunden](images/cyk-connected-300px.jpg)<br>
    *Controller verbunden wird, in die Bluetooth-Einstellungen*

* Überprüfen Sie Ihre Arbeit Controller ordnungsgemäß:
    1. Starten Sie **Mixed Reality-Portal** , und geben Sie Ihre Mixed Reality-Startseite.
    2. Verschieben Sie Ihre Controller und überprüfen Sie die nachverfolgung, Schaltflächen, die Tests aus, und stellen Sie sicher [Teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) funktioniert. Wenn sie nicht der Fall, klicken Sie dann Auschecken [motion Problembehandlung Domänencontroller](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers).

## <a name="gazing-and-pointing"></a>Gazing und verweisen

Windows Mixed Reality unterstützt zwei Modelle, die Schlüssel für die Interaktion, **bestaunen und committen Sie** und **zeigen, und committen**:
* Mit **bestaunen und committen Sie**, Benutzer als Ziel ein Objekts mit ihren [bestaunen](gaze.md) und wählen Sie dann die Objekte mit Hand Air-Taps eine Gamepad, eine Clicker oder ihre Stimme.
* Mit **zeigen, und committen**, ein Benutzer kann Ziel ist, einen Controller verweist-fähige während der Übertragung an das Zielobjekt, und wählen Sie dann die Objekte mit des Controllers Trigger.

-Apps, die Unterstützung, die während der Übertragung mit verweisen auch sollten können Blicke gesteuerte Interaktionen aus, nach Möglichkeit, Benutzern Ihrer Wahl in was als Eingabe für Geräte, die sie verwenden.

### <a name="managing-recoil-when-pointing"></a>Verwalten von Recoil, wenn Sie zeigen

Wenn während der Übertragung Controller zum zeigen, und committen, verwendet Ihre Benutzer den Controller und dann durch Ziehen der Trigger eine Aktion ausführen. Benutzer, die den Trigger kräftig abrufen können am Ende den Controller, die am Ende von deren Trigger Pull höher abzielen, als sie wollten.

Um alle solche Recoil verwalten, die auftreten können, wenn Benutzer, den Trigger abrufen, kann Ihre app die Zielgruppenadressierung anhand bestimmter Chow ausrichten, bei seiner analoge Achsenwert über 0,0 ansteigt. Sie können dann Aktion verwenden, für die Zielgruppenadressierung Chow einige Frames später nach der Triggerwert 1.0 erreicht, solange die endgültige drücken Sie innerhalb eines kurzen Zeitfensters tritt auf, nutzen. Wenn Sie die auf höherer Ebene verwenden [zusammengesetzten tippbewegung](gestures.md#composite-gestures), Windows verwaltet diese für Chow erfassen und Timeout für Sie.

## <a name="grip-pose-vs-pointing-pose"></a>Ziehpunkt Haltung im Vergleich zu zeigenden Haltung

Windows Mixed Reality unterstützt Controller, die während der Übertragung in einer Vielzahl von Formfaktoren, des Controllers Entwurf unterscheidet sich in der Beziehung zwischen Hand-Position des Benutzers und der natürliche "Weiterleiten" Richtung dieser apps sollten mit auf beim Rendern der Controller.

Um diese Controller besser darstellen zu können, es gibt zwei Arten von ist, können Sie für jede Datenquelle Interaktion untersuchen, der **Ziehpunkt Haltung** und **Zeiger Haltung**.

### <a name="grip-pose"></a>Ziehpunkt Haltung

Die **Ziehpunkt Haltung** stellt den Speicherort des dies im Handumdrehen einer Hand, die von einem HoloLens erkannt werden oder dies mit einem Controller während der Übertragung im Handumdrehen dar.

Für immersive Headsets, wird der Haltung Ziehpunkt am besten zum Rendern verwendet **des Benutzers manuell** oder **frei, die ein Objekt des Benutzers verfügen**, z. B. eine "sword" oder dem damoklesschwert. Der Ziehpunkt Haltung wird auch verwendet, bei der Visualisierung von eines Controllers während der Übertragung als die **zum Rendern Modell** bereitgestellten von Windows für eine Bewegung Controller als Ursprungs- und Mittelpunkt der Drehung der Ziehpunkt Haltung verwendet.

Der Ziehpunkt Haltung wird insbesondere wie folgt definiert:
* Die **fassen Sie Position**: Der Schwerpunkt Palm, wenn der Controller natürlich mit angepasst nach links oder rechts zentriert die Position in den Ziehpunkt. Auf dem Windows Mixed Reality-Motion-Controller entspricht dieser Position in der Regel die Schaltfläche "verstehen".
* Die **fassen Sie die rechte Achse die Ausrichtung**: Wenn Sie Ihre Hand, um einen flachen 5 Finger Haltung bilden vollständig geöffnet haben, dem Strahl, der ist normal, zu Ihrem Palm (vorwärts vom linken Palm, rückwärts von rechts Palm)
* Die **fassen Sie die Ausrichtung, vorwärts gerichtete Achse**: Wenn Sie Ihre Hand schließen, teilweise (als ob den Controller enthält), der vom Strahl, der "forward" über die Tube gebildet, indem die Finger nicht-Thumb-Steuerelement zeigt.
* Die **fassen Sie die Ausrichtung des einrichten Achse**: Die nach-oben-Achse impliziert durch die rechts- und -Weiterleiten-Definitionen.

### <a name="pointer-pose"></a>Zeiger Haltung

Die **Zeiger Haltung** stellt die Spitze des Controllers vorwärts verweist.

Die vom System bereitgestellte Zeiger Haltung ist am besten zum Raycast verwendet, wenn Sie können **das Controllermodell selbst rendern**. Wenn Sie ein anderes virtuelles Objekt anstelle der Controller, z. B. eine virtuelle damoklesschwert, rendern sollten Sie mit einem Strahl verweisen, die für diese virtuellen Objekts, z. B. ein Strahl, die entlang der Lauf der app definierte damoklesschwert Modell geleitet. Da Benutzer die virtuelles Objekt und nicht auf dem physischen Controller sehen können, werden zeigen mit dem virtuellen Objekt natürlichere für Benutzer, die Ihre app Sie wahrscheinlich.

## <a name="controller-tracking-state"></a>Status der Controller-änderungsnachverfolgung

Wie bei der Headsets muss die Windows Mixed Reality-Motion-Controller keine Einrichtung der externen Überwachung Sensoren. Stattdessen werden die Controller von Sensoren in den Kopfhörer selbst nachverfolgt.

Wenn der Benutzer aus den Kopfhörer des Sichtfelds Controller verschoben wird, wird in den meisten Fällen Windows weiterhin Positionen von Controller ableiten und Dokumente für die app bereitstellen. Wenn der Controller verloren hat visual nachverfolgung für lange genug, des Controllers Positionen an ungefähren Genauigkeit Positionen gelöscht werden.

An diesem Punkt werden Body-Sperre den Controller für den Benutzer, die Position des Benutzers nachverfolgen, wie sie beim Verfügbarmachen immer noch auf "true" des Controllers-Ausrichtung mit der internen Ausrichtung Sensoren, verschieben. Viele apps, die auf verweisen, und aktivieren die Elemente der Benutzeroberfläche mithilfe von verwaltungscontrollern können normalerweise ungefähre Genauigkeit im bemerken die Benutzer arbeiten.

&nbsp;

>[!VIDEO https://www.youtube.com/embed/rkDpRllbLII]

### <a name="reasoning-about-tracking-state-explicitly"></a>Schlussfolgerungen über zustandsnachverfolgung explizit

Apps, die Positionen, die je nach der zustandsnachverfolgung unterschiedlich behandeln möchten möglicherweise weiter gehen, und überprüfen die Eigenschaften des controllerzustands, z. B. SourceLossRisk und PositionAccuracy:

<table>
<tr>
<th> Status der änderungsnachverfolgung </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>Hohe Genauigkeit</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> Hoch </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Hohe Genauigkeit (Risiko der verlierenden)</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: green; color: white"> Hoch </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Ungefähre Genauigkeit</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Ungefähr </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Keine position</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Ungefähr </td><td style="background-color: orange"> false</td>
</tr>
</table>



Statusdefinitionen nachverfolgung während der Übertragung Controller sind wie folgt definiert:
* **Hoher Genauigkeit:** Während sich der Controller während der Übertragung in den Kopfhörer des Sichtfelds, erhalten sie in der Regel hohe Genauigkeit Positionen, basierend auf visuelle Verfolgung. Beachten Sie, dass ein verschieben Controller, die vorübergehend das Sichtfeld verlässt oder vorübergehend von der Kopfhörer Sensoren verdeckt wird (z. B. durch der Benutzer der anderen Hand) wird weiterhin hoch-Genauigkeit ist für kurze Zeit, basierend auf Trägheit nachverfolgung des Controllers zurück sich selbst.
* **Hohe Genauigkeit (Risiko der verlierenden):** Wenn der Benutzer den Controller während der Übertragung über den Rand der Kopfhörer des Sichtfelds bewegt, den Kopfhörer visuell des Controllers Position kann nicht in Kürze. Die app erkennt, wenn der Controller diese Grenze Blickfeld von angezeigt erreicht hat die **SourceLossRisk** 1.0 zu erreichen. An diesem Punkt können die app Controller-Gesten anhalten, die einem stetigen Strom an sehr hoher Qualität ist erforderlich.
* **Ungefähre Genauigkeit:** Wenn der Controller verloren hat visual nachverfolgung für lange genug, des Controllers Positionen an ungefähren Genauigkeit Positionen gelöscht werden. An diesem Punkt werden Body-Sperre den Controller für den Benutzer, die Position des Benutzers nachverfolgen, wie sie beim Verfügbarmachen immer noch auf "true" des Controllers-Ausrichtung mit der internen Ausrichtung Sensoren, verschieben. Viele apps, die mithilfe von verwaltungscontrollern, zeigen Sie auf, und aktivieren die Elemente der Benutzeroberfläche können als normale Zeit mit einer Genauigkeit von ungefähren im bemerken die Benutzer ausgeführt werden. Apps mit geringeres Routingaufkommen eingabeanforderungen können diese Verringerung von erkennen **hohe** Genauigkeit **ungefähr** Genauigkeit durch Überprüfen der **PositionAccuracy** -Eigenschaft für Beispiel: um dem Benutzer eine großzügigeren Hitbox auf außerhalb des Bildschirms Zielen während dieser Zeit geben.
* **Keine Position:** Während der Controller auf ungefähre Genauigkeit für einen langen Zeitraum ausgeführt werden kann, weiß das System manchmal, dass auch eine Text-locked Position im Moment nicht aussagekräftig ist. Z. B. ein Controller, der nur eingeschaltet wurde möglicherweise nie beobachtet wurde visuell, oder Sie einen Controller, der dann von einer anderen Person übernommen wird ein Benutzer festlegen kann. Zu diesen Zeitpunkten, wird das System keine einer beliebigen Position, an die app bereitgestellt und **TryGetPosition** wird "false" zurückgegeben.

## <a name="interactions-low-level-spatial-input"></a>Interaktionen: Auf niedriger Ebene räumliche Eingabe

Die Core-Interaktionen über praktische und Motion-Controllern sind **wählen**, **Menü**, **verstehen**, **Touchpad**,  **Ministick**, und **Startseite**.
* **Wählen Sie** ist die Interaktion primäre, ggf. ein Hologramm, bestehend aus einem drücken, gefolgt von einer Version zu aktivieren. Führen Sie für Controller die während der Übertragung, Drücken einer Option, die mithilfe des Controllers Trigger aus. Weitere Informationen zum Ausführen einer SELECT-Anweisung werden per Spracheingabe stellen, die [voice-Befehl](voice-input.md) "Select". Die gleiche Option Interaktion kann innerhalb einer app verwendet werden. Stellen Sie sich auf wie das Äquivalent der Maus klicken, eine universelle Aktion, die Sie einmal erfahren Sie, und klicken Sie dann für alle Ihre apps anwenden.
* **Menü** ist die sekundäre Interaktion, denen Sie Aktionen für ein Objekt, das verwendet, um ein Kontextmenü-pull- oder eine andere sekundäre Aktion. Mit Motion-Controllern, Sie können entsprechende Maßnahmen ein Menü mithilfe des Controllers *Menü* Schaltfläche. (d. h. die Schaltfläche mit dem Hamburger-Symbol für die "Menu" auf)
* **Fassen Sie** ist, wie Benutzer direkt auf die Objekte an die Hand, die sie bearbeiten mit Maßnahmen ergreifen können. Mit der Motion-Controller können Sie Ihre erste eng Ärmel eine Aktion verstehen Zweck. Ein Controller während der Übertragung erkennt möglicherweise mit einer Schaltfläche Ziehpunkte, Palm-Trigger oder anderen Sensor verstanden.
* **Touchpad** Bestätigen der Aktion wird durch Klicken auf das Touchpad ermöglicht dem Benutzer eine Aktion in zwei Dimensionen entlang der Fläche des eine Bewegung des Controllers Touchpad, anpassen. Touchpad bieten gedrückt, berührt Zustand und normalisierte XY-Koordinaten. X- und Y zwischen-1 und 1 im Bereich des zirkulären Touchpads, mit einem Mittelpunkt (0, 0). X 1, auf der linken Seite und 1 ist auf der rechten Seite. Für "Y" -1 im unteren Bereich und 1 ist am oberen Rand.
* **Ministick** ermöglicht dem Benutzer eine Aktion in zwei Dimensionen anpassen, indem Sie das Verschieben eines Motion-Controllers Ministick innerhalb des kreisförmigen Bereichs, bestätigen Sie die Aktion, durch Klicken auf die Ministick. Thumbsticks gedrückt bieten außerdem normalisiert XY-Koordinaten. X- und Y zwischen-1 und 1 im Bereich des zirkulären Touchpads, mit einem Mittelpunkt (0, 0). X 1, auf der linken Seite und 1 ist auf der rechten Seite. Für "Y" -1 im unteren Bereich und 1 ist am oberen Rand.
* **Startseite** ist eine spezielle Systemaktion, die verwendet wird, um zurück zum Startmenü zu wechseln. Dies ähnelt der Windows-Taste drücken, einer Tastatur oder der Xbox-Schaltfläche, auf eine Xbox-Controller. Sie können Startseite navigieren, durch Drücken der Windows-Schaltfläche in einem Controller während der Übertragung. Beachten Sie, können Sie auch immer Start Zurückgeben von "Hey Cortana, Go Home" angezeigt. Apps können nicht speziell auf home Aktionen reagieren, wie diese vom System verarbeitet werden.

## <a name="composite-gestures-high-level-spatial-input"></a>Zusammengesetzte Gesten: Auf hoher Ebene räumliche Eingabe

Beide [Gesten übergeben](gestures.md) Motion-Controller nachverfolgt werden können, im Laufe der Zeit, um einen gemeinsamen Satz von allgemeinen erkennen  **[zusammengesetzten Gesten](gestures.md#composite-gestures)** . Dadurch kann Ihre app auf hoher Ebene erkennen **Tippen Sie auf**, **enthalten**, **Manipulation** und **Navigation** anwendungsstiftbewegungen, die, ob der Benutzer am Ende mit praktische oder Controllern.

## <a name="rendering-the-motion-controller-model"></a>Die Motion-Controllermodell Rendern

**3D Controller Modelle** Windows zur Verfügung apps ein Modell zum Rendern von jedem Controller während der Übertragung im System zurzeit aktiv. Wenn Ihre app, die dynamisch geladen und Erläutern Sie, diese Modelle vom System bereitgestellten Controller zur Laufzeit verwenden, können Sie sicherstellen, dass Ihre app vorwärts-kompatiblen auf jede zukünftige Controller Entwürfe ist.

Diese Modelle zum Rendern alle gerendert werden soll, auf die **Ziehpunkt Haltung** des Controllers, als der Ursprung des Modells orientiert sich diesem Punkt in der realen Welt. Wenn Sie Modelle Controller rendern, dann möchten Raycast in die Szene aus der **Zeiger Haltung**, steht für des Strahls, an denen Benutzer auf natürliche Weise erwarten, zeigen dass, des Controllers physischen Entwurfsstrukturen angegeben.

Weitere Informationen dazu, wie Sie die Controller-Modelle in Unity dynamisch geladen werden, finden Sie die [Rendern der Motion-Controllermodell in Unity](gestures-and-motion-controllers-in-unity.md#rendering-the-motion-controller-model-in-unity) Abschnitt.

**2D Controller Liniengrafiken** Anfügen von in-app Controller-Tipps und Befehle, die in-app Controller-Modelle selbst wird empfohlen, möglicherweise möchten einige Entwickler 2D Zeile Art Darstellungen der Controller während der Übertragung in Flatfile "Tutorial" oder "Gewusst-wie" verwenden -BENUTZEROBERFLÄCHE. Für Entwickler haben wir PNG Motion Controller Zeile ClipArt-Dateien in beide Schwarz-Weiß-denken überwinden unten verfügbar (mit der rechten Maustaste speichern) vorgenommen.

![Vorschau der Motion-Controller-Liniengrafik](images/motioncontrollers-black-preview-300px.png)

 [Voller Auflösung Motion-Controllern/w-Grafik in ''' weißen '''](images/motioncontrollers-white.png)
 
 [Voller Auflösung Motion-Controllern/w-Grafik in ''' Schwarz '''](images/motioncontrollers-black.png)

## <a name="faq"></a>Häufig gestellte Fragen

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a>Kann ich Paar Controller mit mehreren PCs motion?

Motion-Domänencontroller unterstützen Kopplung mit einem einzigen PC. Befolgen Sie die Anweisungen auf [motion Testcontroller-Setup](motion-controllers.md#setup) Ihre Controller zu koppeln.

### <a name="how-do-i-update-motion-controller-firmware"></a>Wie aktualisiere ich die Controllerfirmware während der Übertragung?

Während der Übertragung Controllerfirmware ist Bestandteil des Treibers Kopfhörer und automatisch aktualisiert werden für Verbindung bei Bedarf. Firmware-Updates werden in der Regel 1 bis 2 Minuten je nach Bluetooth-Radio und Link-Qualität. In seltenen Fällen dauert Controller Firmware-Updates bis zu 10 Minuten der angeben kann, eine schlechte Bluetooth-Konnektivität oder Radio Störungen. Informieren Sie sich [Bluetooth-bewährte Methoden im Handbuch Enthusiast](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) um Konnektivitätsprobleme zu beheben. Nach einem Firmwareupdate Controller wird neu gestartet und erneutes Verbinden mit dem Host-PC (Sie können die LEDs für die nachverfolgung hellen wechseln beachten). Wenn eine Aktualisierung der Firmware unterbrochen wird (z. B. Controller verlieren Power), es wird versucht beim nächsten Controller eingeschaltet sind.

### <a name="how-i-can-check-battery-level"></a>Wie überprüfe ich den Ladezustand der Batterie?

In der [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md), können Sie auf der Ladezustand der Batterie auf der Rückseite des virtuellen Modells finden Sie unter Ihrem Controller über aktivieren. Es gibt keinen physischen Akku-auf-Indikator.

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>Können Sie diesen Controller ohne einen Kopfhörer verwenden? Nur für die Eingabe Joystick, Trigger usw.?

Nicht für universelle Windows-Anwendungen.

## <a name="troubleshooting"></a>Problembehandlung

Finden Sie unter [motion Problembehandlung Domänencontroller](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers) im Handbuch Enthusiast.

## <a name="filing-motion-controller-feedbackbugs"></a>Während der Übertragung Controller Feedback/Programmfehlern

[Geben Sie uns Feedback](give-us-feedback.md) im Feedback-Hub, verwenden Sie die Kategorie "Mixed Reality-Eingabe >".

## <a name="see-also"></a>Siehe auch
* [Gesten und Motion-Controller in Unity](gestures-and-motion-controllers-in-unity.md)
* [Hände und Motion-Controller in DirectX](hands-and-motion-controllers-in-directx.md)
* [Gesten](gestures.md)
* [MR-Eingabe 213: Motion-Controller](mixed-reality-213.md)
* [Enthusiast-Handbuch: Ihr Windows Mixed Reality home](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [Enthusiast-Handbuch: Verwenden Spiele und apps in Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [Funktionsweise von innen nach außen nachverfolgen](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/tracking-system)
