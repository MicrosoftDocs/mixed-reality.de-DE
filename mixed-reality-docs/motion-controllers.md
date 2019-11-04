---
title: Motion-Controller
description: Details zu den Mixed Reality-Bewegungs Controllern.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 6DOF-Controller, Motion-Controller
ms.openlocfilehash: 84ebc6c0d7c63e58346b6ee9e565811bc40571b5
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437858"
---
# <a name="motion-controllers"></a>Motion-Controller

:::row:::
    :::column:::
        Bewegungs Controller sind [Hardware Zubehör](hardware-accessories.md) , mit denen Benutzer in gemischter Realität Maßnahmen ergreifen können. Ein Vorteil von Bewegungs Controllern gegenüber [Gesten](gaze-and-commit.md#composite-gestures) besteht darin, dass die Controller eine genaue Position im Raum aufweisen und eine differenzierte Interaktion mit digitalen Objekten ermöglichen. Für Windows Mixed Reality-immersive Headsets sind Bewegungs Controller die primäre Methode, mit der Benutzer in ihrer Welt Maßnahmen ergreifen können.<br>
        <br>
        *Bild: ein Windows Mixed Reality Motion Controller*
    :::column-end:::
        :::column:::
       ![Windows Mixed Reality-Bewegungs Controller](images/winmr-ck-1080x1080-350px.jpg)<br> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="device-support"></a>Geräteunterstützung

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Feature</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
</tr>
<tr>
     <td>Motion-Controller</td>
     <td>❌</td>
     <td>❌</td>
     <td>✔️</td>
</tr>
</table>

## <a name="hardware-details"></a>Hardware Details

<iframe width="940" height="530" src="https://www.youtube.com/embed/1nlcdDNOdm8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Windows Mixed Reality Motion Controllers bieten mithilfe der Sensoren im immersiven Headset eine präzise und reaktionsfähige Nachverfolgung der Bewegung in Ihrem Sichtfeld, d. h., es ist nicht erforderlich, Hardware an den Wänden in Ihrem Bereich zu installieren. Diese Motion-Controller bieten dieselbe einfache Einrichtung und Portabilität wie Windows Mixed Reality (immersive Headsets). Unsere Geräte Partner planen das vermarkten und verkaufen dieser Controller in Einzelhandels Regalen in diesem Urlaub.

![Ihren Controller kennen](images/controllerimage-750px.png)<br>
*Lernen Sie Ihren Controller kennen*

**Aspekte**
* Optische Nachverfolgung
* Trigger
* Schaltfläche ""
* Ministick
* Touchpad

## <a name="setup"></a>Setup

### <a name="before-you-begin"></a>Vorbemerkungen

**Sie benötigen Folgendes:**
* Ein Satz von zwei Bewegungs Controllern.
* Vier AA-Akkus
* Ein PC, der Bluetooth 4,0-fähig ist.

**Auf Windows-, Unity-und Treiber Updates überprüfen**
* Weitere Informationen finden Sie unter [Installieren der Tools](install-the-tools.md) für die bevorzugten Versionen von Windows, Unity usw. für die Entwicklung mit gemischter Realität.
* Stellen Sie sicher, dass Sie über die aktuellsten Headset- [und Motion Controller-Treiber](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)verfügen.

### <a name="pairing-controllers"></a>Kopplung von Controllern

Bewegungs Controller können mit dem Host-PC mithilfe von Windows-Einstellungen wie allen anderen Bluetooth-Geräten gebunden werden.

1. Fügen Sie 2 AA-Akkus in die Rückseite des Controllers ein. Lassen Sie die Akku Abdeckung vorerst deaktiviert.
2. Wenn Sie anstelle eines integrierten Bluetooth-Funk Adapters einen externen USB-Bluetooth-Adapter verwenden, lesen Sie die [bewährten Methoden für Bluetooth](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) , bevor Sie fortfahren. Stellen Sie für die Desktop Konfiguration mit dem integrierten Radio sicher, dass die Antenne verbunden ist.
3. Öffnen **Sie Windows-Einstellungen** -> **Geräte** -> **Sie Bluetooth oder ein anderes Gerät** -> **Bluetooth** hinzuzufügen, und entfernen Sie alle früheren Instanzen von "Motion Controller – right" und "Motion Controller – Left". Überprüfen Sie auch die Kategorie andere Geräte am Ende der Liste.
4. Wählen Sie **Bluetooth oder anderes Gerät hinzufügen** aus, und starten Sie die Ermittlung von Bluetooth-Geräten.
5. Drücken Sie die Windows-Schaltfläche des Controllers, um den Controller einzuschalten.
6. Halten Sie die Schaltfläche "Kopplung" gedrückt (Registerkarte im Akku Depot), bis die LEDs mit dem Pulsing beginnen.

:::row:::
    :::column:::
7. Warten Sie, bis am Ende der Liste "Motion Controller-Left" oder "Motion Controller-right" angezeigt wird. Wählen Sie diese Option aus, um Der Controller wird bei der Verbindungs Herstellung einmal vibrieren.<br>
        <br>
        *Bild: Wählen Sie "Motion Controller", um es zu koppeln. Wenn mehrere Instanzen vorhanden sind, wählen Sie eine am Ende der Liste aus.*
    :::column-end:::
        :::column:::
       ![Wählen Sie Motion Controller zum Koppeln aus, wenn mehrere Instanzen eine Auswahl aus der Liste unten in der Liste auswählen.](images/450px-bluetooth-add-a-device-300px.png)<br> 
    :::column-end:::
:::row-end:::
   
8. Sie sehen, dass der Controller in den Bluetooth-Einstellungen unter der **Kategorie "Maus, Tastatur, & Stift"** als **verbunden**angezeigt wird. An diesem Punkt erhalten Sie möglicherweise ein Firmwareupdate – Weitere Informationen finden Sie im [nächsten Abschnitt](motion-controllers.md#updating-controller-firmware).
9. Akku Abdeckung erneut anfügen.
10. Wiederholen Sie die Schritte 1-9 für den zweiten Controller.

<br>

:::row:::
    :::column:::
        Nachdem beide Controller erfolgreich gekoppelt wurden, sollten die Einstellungen in der **Kategorie "Maus, Tastatur, & Pen"** wie folgt aussehen. <br>
        <br>
        *Image: Motion-Controller verbunden*
    :::column-end:::
        :::column:::
       ![Verbundene Bewegungs Controller](images/450px-motion-controller-connected-300px.png)<br>
    :::column-end:::
:::row-end:::

Wenn die Controller nach der Kopplung ausgeschaltet sind, wird Ihr Status als gekoppelt angezeigt. Wenn Controller unter der Kategorie "andere Geräte" dauerhaft bleiben, wurde die Kopplung möglicherweise nur teilweise abgeschlossen und muss erneut ausgeführt werden, um den Controller funktionsfähig zu machen.

### <a name="updating-controller-firmware"></a>Aktualisieren der Controller Firmware

* Wenn ein immersives Headset mit dem PC verbunden ist und eine neue Controller Firmware verfügbar ist, wird die Firmware bei Ihrer nächsten Aktivierung automatisch an die Motion-Controller übermittelt. Controller-Firmwareupdates werden durch ein Muster zur Beleuchtung der LED von vorangehenden Quadranten in einer Kreisbewegung angegeben und benötigen 1-2 Minuten.


:::row:::
    :::column:::
* Nachdem das Firmwareupdate abgeschlossen ist, werden die Controller neu gestartet und die Verbindung wieder hergestellt. Beide Controller sollten jetzt verbunden werden. <br>
        <br>
        *Image: in Bluetooth-Einstellungen verbundene Controller*
    :::column-end:::
        :::column:::
       ![Verbundene Controller](images/cyk-connected-300px.jpg)<br>
    :::column-end:::
:::row-end:::


* Überprüfen Sie, ob Ihre Controller ordnungsgemäß funktionieren
    1. Starten Sie das **Mixed Reality-Portal** , und geben Sie Ihr Mixed Reality-Start
    2. Verschieben Sie Ihre Controller, und überprüfen Sie die Nachverfolgung, Test Schaltflächen [und überprüfen](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) Sie, ob die Wenn Sie dies nicht tun, sehen Sie sich die Problembehandlung für [Motion Controller](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers)an

## <a name="gazing-and-pointing"></a>Schauen und zeigen

Windows Mixed Reality unterstützt zwei Schlüsselmodelle für Interaktion, **Blick und Commit** und **Punkt und Commit**:
* Mit " **Blick" und "Commit**" können Benutzer ein Objekt mit dem [Blick](gaze-and-commit.md) auf ein Objekt ausrichten und dann Objekte mit Hand Luft tippen, einem Gamepad, einem Clicker oder ihrer Stimme auswählen.
* Mit **Point und Commit**kann ein Benutzer auf das Zielobjekt einen pointfähigen Bewegungs Controller ausrichten und dann Objekte mit dem Controller des Controllers auswählen.

Apps, die mit der Anzeige von Bewegungs Controllern unterstützen, sollten nach Möglichkeit auch Blick gesteuerte Interaktionen aktivieren, damit Benutzer entscheiden können, welche Eingabegeräte verwendet werden.

### <a name="managing-recoil-when-pointing"></a>Verwalten von Recoil beim verweisen

Wenn Sie Bewegungs Controller verwenden, um zu zeigen und zu übernehmen, verwenden die Benutzer den Controller zum Ausrichten und anschließenden Ausführen von Aktionen, indem Sie den zugehörigen Triggern ziehen. Benutzer, die den-Auslösern stark abrufen, werden am Ende des Pull-Pull-Pull-Vorgängen möglicherweise am Ende des Controllers weitergeleitet als beabsichtigt.

Um eine solche Recoil zu verwalten, die beim Abrufen des Auslösers durch die Benutzer auftreten kann, kann Ihre APP den Ziel-Ray ausrichten, wenn der Wert der analogen Achse des Auslösers über 0,0 steigt. Anschließend können Sie mithilfe dieses Ziel-Ray einige Frames später verwenden, wenn der Triggerwert 1,0 erreicht, solange der letzte Vorgang innerhalb eines kurzen Zeitfensters erfolgt. Wenn Sie die zusammen [gesetzte Tap-Bewegung](gaze-and-commit.md#composite-gestures)auf höherer Ebene verwenden, verwaltet Windows diese Zielsetzung der peererfassung und des Timeouts für Sie.

## <a name="grip-pose-vs-pointing-pose"></a>Ziehpunkt im Vergleich zu Zeige darstellen

Windows Mixed Reality unterstützt Bewegungs Controller in einer Vielzahl von Formfaktoren, wobei sich der Entwurf des Controllers in seiner Beziehung zwischen der Handposition des Benutzers und der natürlichen Vorwärtsrichtung unterscheidet, die apps beim Rendern der ern.

Um diese Controller besser darzustellen, gibt es zwei Arten von Posen, die Sie für jede Interaktions Quelle untersuchen können, die Ziehpunkt- **und die** **Zeiger**Darstellung.

### <a name="grip-pose"></a>Ziehpunkt darstellen

Die Ziehpunkt- **Pose** stellt die Position der Palme einer Hand dar, die von einem hololens erkannt wird, oder die Palme, die einen Bewegungs Controller enthält.

Bei immersiven Headsets eignet sich die Zieh Punkt Darstellung am besten zum Rendering **der Benutzer Hand** oder **eines Objekts, das in der Hand des Benutzers gehalten**wird, z. b. ein Schwert oder eine Waffe. Die Zieh Punkt Darstellung wird auch bei der Visualisierung eines Bewegungs Controllers verwendet, da das **renderbare Modell** , das von Windows für einen Motion-Controller bereitgestellt wird, die Zieh Punkt Darstellung als Ursprung und Mittelpunkt der Drehung verwendet.

Die Ziehpunkt-Pose wird wie folgt definiert:
* Die Zieh **Punktposition**: der Palmen Schwerpunkt bei der natürlichen Aufbewahrung des Controllers, nach links oder rechts, um die Position im Ziehpunkt zu zentrieren. Auf dem Windows Mixed Reality Motion Controller richtet sich diese Position im Allgemeinen nach der Schaltfläche "verstehen".
* Die **Rechte Achse**der Ziehpunkt Ausrichtung: Wenn Sie Ihre Hand vollständig geöffnet haben, um eine flache 5-Finger-Darstellung zu bilden, ist das Strahl-Ray, das normal ist (vorwärts von links nach links, rückwärts von rechter Palme).
* Die **Forward-Achse**der Ziehpunkt Ausrichtung: Wenn Sie die Hand teilweise schließen (wie beim Halten des Controllers), wird der Strahl, der durch das durch ihre nicht-Thumb-Finger formatierte Rohr auf "Vorwärts" zeigt.
* Die **aufwärts Achse**der Ziehpunkt Ausrichtung: die aufwärts Achse, die durch die Rechte-und vorwärts Definitionen impliziert wird.

### <a name="pointer-pose"></a>Zeiger Pose

Die **Zeiger** Darstellung stellt die Spitze des Controllers dar, der vorwärts zeigt.

Die vom System bereitgestellte Zeiger Darstellung eignet sich am besten für raycast, wenn Sie **das Controller Modell selbst Rendern**. Wenn Sie ein anderes virtuelles Objekt anstelle des Controllers (z. b. eine virtuelle Pistole) rendern, sollten Sie auf einen Strahl zeigen, der für dieses virtuelle Objekt am natürlichsten ist, z. b. ein Strahl, der entlang des fassers des App-defined Gun-Modells verläuft. Da Benutzer das virtuelle Objekt und nicht den physischen Controller sehen können, ist das verweisen mit dem virtuellen Objekt für diejenigen, die Ihre APP verwenden, wahrscheinlich natürlicher.

## <a name="controller-tracking-state"></a>Controller nach verfolgungsstatus

Wie bei den Headsets ist für Windows Mixed Reality Motion Controller das Einrichten externer nach Verfolgungs Sensoren nicht erforderlich. Stattdessen werden die Controller von Sensoren im Headset selbst nachverfolgt.

Wenn der Benutzer die Controller aus dem Feld des endfelds der Ansicht verschiebt, werden in den meisten Fällen die Controller Positionen von Windows weiter abgeleitet und der APP bereitgestellt. Wenn die visuelle Überwachung für den Controller lange genug verloren gegangen ist, werden die Positionen des Controllers auf Positionen mit ungefähren Genauigkeit abgelegt.

An diesem Punkt sperrt das System den Controller für den Benutzer, wobei die Position des Benutzers nachverfolgt wird, während er sich bewegt, während er weiterhin die echte Ausrichtung des Controllers mithilfe der internen Ausrichtungs Sensoren verfügbar macht. Viele apps, die Controller verwenden, um auf Benutzeroberflächen Elemente zu verweisen und diese zu aktivieren, können normal funktionieren, ohne dass der Benutzer das merkt.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/rkDpRllbLII" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### <a name="reasoning-about-tracking-state-explicitly"></a>Grund für die explizite Nachverfolgung des Zustands

Apps, die Positionen basierend auf dem nach verfolgungsstatus unterschiedlich behandeln möchten, können weiter gehen und die Eigenschaften des Controller Zustands überprüfen, z. b. sourcelossrisk und positionaccuracy:

<table>
<tr>
<th> Nach verfolgungsstatus </th><th> Sourcelossrisk </th><th> Positionsgenauigkeit </th><th> Trygetposition</th>
</tr><tr>
<td> <b>Hohe Genauigkeit</b> </td><td style="background-color: green; color: white"> &lt; 1,0 </td><td style="background-color: green; color: white"> Hoch </td><td style="background-color: green; color: white"> Wahr</td>
</tr><tr>
<td> <b>Hohe Genauigkeit (Risiko des Verlusts)</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: green; color: white"> Hoch </td><td style="background-color: green; color: white"> Wahr</td>
</tr><tr>
<td> <b>Ungefähre Genauigkeit</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Ungefähr </td><td style="background-color: green; color: white"> Wahr</td>
</tr><tr>
<td> <b>Keine Position</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Ungefähr </td><td style="background-color: orange"> Falsch</td>
</tr>
</table>



Diese Motion Controller-Überwachungs Zustände werden wie folgt definiert:
* **Hohe Genauigkeit:** Während sich der Motion-Controller in der Ansicht des Dashboards befindet, stellt er im Allgemeinen hohe Genauigkeits Positionen auf der Grundlage der visuellen Nachverfolgung bereit. Beachten Sie, dass ein beweglicher Controller, der das Sichtfeld vorübergehend verlässt oder vorübergehend von den Headset-Sensoren (z. b. durch die andere Seite des Benutzers) verdeckt wird, weiterhin hohe Genauigkeit für kurze Zeit zurückgibt, basierend auf der Trägheits Verfolgung des Controllers. etabliert.
* **Hohe Genauigkeit (Risiko des Verlusts):** Wenn der Benutzer den Bewegungs Controller über den Rand des Felds der Ansicht bewegt, kann das Headset die Position des Controllers in Kürze nicht visuell nachverfolgen. Die APP weiß, wann der Controller diese FOV-Grenze erreicht hat, indem er den **sourcelossrisk** -REACH-1,0 sieht. An diesem Punkt kann die APP die Controller Gesten anhalten, die einen stabilen Stream von sehr hochwertigen Posen erfordern.
* **Ungefähre Genauigkeit:** Wenn die visuelle Überwachung für den Controller lange genug verloren gegangen ist, werden die Positionen des Controllers auf Positionen mit ungefähren Genauigkeit abgelegt. An diesem Punkt sperrt das System den Controller für den Benutzer, wobei die Position des Benutzers nachverfolgt wird, während er sich bewegt, während er weiterhin die echte Ausrichtung des Controllers mithilfe der internen Ausrichtungs Sensoren verfügbar macht. Viele apps, die Controller verwenden, um auf Benutzeroberflächen Elemente zu verweisen und diese zu aktivieren, können so normal agieren, dass Sie in der ungefähren Genauigkeit nicht bemerkt werden Bei apps mit schwereren Eingabe Anforderungen ist es möglicherweise sinnvoll, diesen Löschvorgang von **hoher** Genauigkeit zur **ungefähren** Genauigkeit zu verstehen, indem die **positionaccuracy** -Eigenschaft überprüft wird Während dieser Zeit.
* **Keine Position:** Obwohl der Controller für einen längeren Zeitraum mit der ungefähren Genauigkeit arbeiten kann, weiß das System manchmal, dass auch eine vom Text gesperrte Position im Moment nicht aussagekräftig ist. Beispielsweise kann ein Controller, der gerade eingeschaltet war, nie visuell beobachtet werden, oder ein Benutzer kann einen Controller ablegen, der von einer anderen Person abgerufen wird. Zu diesen Zeitpunkten stellt das System keine Position für die APP bereit, und **trygetposition** gibt false zurück.

## <a name="interactions-low-level-spatial-input"></a>Interaktionen: räumliche Eingabe auf niedriger Ebene

Die wichtigsten Interaktionen zwischen Händen und Bewegungs Controllern sind **Select**, **Menu**, **grasp**, **Touchpad**, **Thumbstick**und **Home**.
* **Select** ist die primäre Interaktion zum Aktivieren eines holograms, das aus einem Press gefolgt von einem Release besteht. Für Bewegungs Controller führen Sie eine SELECT-Taste mithilfe des Controllers des Controllers aus. Weitere Möglichkeiten zum Durchführen eines SELECT-Befehls finden Sie im [Sprachbefehl](voice-input.md) "Select". Dieselbe SELECT-Interaktion kann in jeder beliebigen App verwendet werden. Stellen Sie sich als Äquivalent eines Mausklicks vor, eine universelle Aktion, die Sie einmal erlernen und dann auf alle Ihre apps anwenden.
* **Menü** ist die sekundäre Interaktion zum agieren für ein Objekt, das zum Abrufen eines Kontextmenüs oder zum Ausführen einer anderen sekundären Aktion verwendet wird. Mit Motion Controllers können Sie mithilfe der *Menü* Schaltfläche des Controllers eine Menü Aktion ausführen. (d. h. die Schaltfläche mit dem Hamburger "Menü"-Symbol)
* Der **Einblick** ist, wie Benutzer direkt Aktionen an Objekten durchführen können, um Sie zu bearbeiten. Mit Motion-Controllern können Sie eine Handschlag Aktion durchführen, indem Sie Ihre Faust eng durch drücken. Ein Bewegungs Controller kann eine Reichweite mit einer Schaltfläche zum Durchsuchen, einem Palmen-oder einem anderen Sensor erkennen.
* **Touchpad** ermöglicht dem Benutzer, eine Aktion in zwei Dimensionen entlang der Oberfläche des Touchpads eines Bewegungs Controllers anzupassen. dabei wird ein Commit für die Aktion durch Klicken auf den Touchpad ausgeführt. Touchpads bieten einen gedrückten Zustand, einen berührten Zustand und normalisierte XY-Koordinaten. Der Bereich X und Y liegt zwischen-1 und 1 über dem Bereich des kreisförmigen Touchpads mit einem Mittelpunkt (0,0). Für X befindet sich-1 auf der linken Seite, und 1 befindet sich auf der rechten Seite. Bei Y befindet sich-1 unten und 1 oben.
* Mit **Ministick** kann der Benutzer eine Aktion in zwei Dimensionen anpassen, indem er den Finger Stick eines Bewegungs Controllers innerhalb seines Kreis Bereichs verschiebt, indem er auf den Finger Stick klickt, um die Aktion auszuführen. Thumbsticks bieten außerdem einen gedrückten Zustand und normalisierte XY-Koordinaten. Der Bereich X und Y liegt zwischen-1 und 1 über dem Bereich des kreisförmigen Touchpads mit einem Mittelpunkt (0,0). Für X befindet sich-1 auf der linken Seite, und 1 befindet sich auf der rechten Seite. Bei Y befindet sich-1 unten und 1 oben.
* **Home** ist eine spezielle System Aktion, die verwendet wird, um zum Startmenü zurückzukehren. Dies ähnelt dem Drücken der Windows-Taste auf einer Tastatur oder der Xbox-Schaltfläche auf einem Xbox-Controller. Sie können zu Hause navigieren, indem Sie auf einem Bewegungs Controller auf die Windows-Taste klicken. Beachten Sie, dass Sie auch immer zu Beginn zurückkehren können, indem Sie "Hey Cortana, Go Home" sagen. Apps können nicht speziell auf Start Aktionen reagieren, da diese vom System behandelt werden.

## <a name="composite-gestures-high-level-spatial-input"></a>Zusammengesetzte Gesten: räumliche Eingabe auf hoher Ebene

Beide [Handgesten](gaze-and-commit.md#composite-gestures) und Bewegungs Controller können im Laufe der Zeit überwacht werden, um einen gemeinsamen Satz von zusammen **[gesetzten Gesten](gaze-and-commit.md#composite-gestures)** auf hoher Ebene zu erkennen. Dadurch kann Ihre APP auf hoher Ebene **Tap**-, **Hold**-, **Manipulations** -und **Navigations** Gesten erkennen, unabhängig davon, ob die Benutzer Hände oder Controller verwenden.

## <a name="rendering-the-motion-controller-model"></a>Rendern des Motion Controller-Modells

**3D-Controller Modelle** Windows stellt apps ein renderbares Modell für jeden Motion Controller zur Verfügung, der derzeit im System aktiv ist. Wenn Sie Ihre APP dynamisch laden und diese vom System bereitgestellten Controller Modelle zur Laufzeit formulieren, können Sie sicherstellen, dass Ihre APP an zukünftige Controller Entwürfe weiterleiten kann.

Diese renderbaren Modelle sollten alle in der Zieh Punkt **Darstellung des Controllers** gerendert werden, da der Ursprung des Modells an diesem Punkt in der physischen Welt ausgerichtet ist. Wenn Sie Controller Modelle rendern, können Sie sich in der Szene von der **Zeiger**Darstellung, die den Strahl darstellt, auf den Benutzer erwartungsgemäß nach dem physischen Design des Controllers zeigen werden, in die Szene umwandeln.

Weitere Informationen zum dynamischen Laden von Controller Modellen in Unity finden Sie im Abschnitt [Rendern des Motion Controller-Modells in Unity](gestures-and-motion-controllers-in-unity.md#rendering-the-motion-controller-model-in-unity) .

**2D-Controller Linienart** Es empfiehlt sich, in-App-Controller-Tipps und-Befehle an die in-App Controller-Modelle selbst anzufügen, aber einige Entwickler möchten möglicherweise 2D-line-Art-Darstellungen der Motion-Controller in einer flachen "Tutorial"-oder "Gewusst wie"-Benutzeroberfläche verwenden. Für diese Entwickler haben wir. png Motion Controller line-Art-Dateien in schwarz und weiß unten verfügbar gemacht (Klicken Sie mit der rechten Maustaste, um zu speichern).

![Linienart der Vorschau der Motion Controller](images/motioncontrollers-black-preview-300px.png)

[Vollauflösung von Bewegungs Controllern in ' ' ' White ' ' '](images/motioncontrollers-white.png)
 
[Vollauflösung von Bewegungs Controllern in ' ' ' Black ' ' ' Black ' ' '](images/motioncontrollers-black.png)

## <a name="faq"></a>Häufig gestellte Fragen

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a>Kann ich Motion-Controller mit mehreren PCs koppeln?

Bewegungs Controller unterstützen die Kopplung mit einem einzelnen PC. Befolgen Sie die Anweisungen unter [Motion Controller Setup](motion-controllers.md#setup) , um Ihre Controller zu koppeln.

### <a name="how-do-i-update-motion-controller-firmware"></a>Gewusst wie Update Motion Controller Firmware?

Motion Controller Firmware ist Teil des Headset-Treibers und wird bei Bedarf automatisch bei der Verbindung aktualisiert. Firmwareupdates dauern in der Regel je nach Bluetooth-Radio und-linkqualität 1-2 Minuten. In seltenen Fällen kann es bis zu 10 Minuten dauern, bis Controller-Firmwareupdates auf eine schlechte Bluetooth-Konnektivität oder Funkstörungen hindeuten. Informationen zur Behebung von Konnektivitätsproblemen finden Sie unter [bewährte Methoden für Bluetooth im Leitfaden für Enthusiasten](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) . Nach einem Firmwareupdate werden die Controller neu gestartet und die Verbindung mit dem Host-PC wieder hergestellt (Sie werden feststellen, dass die LEDs für die Nachverfolgung hell sind). Wenn ein Firmwareupdate unterbrochen wird (z. b. wenn die Controller die Stromversorgung verlieren), wird erneut versucht, wenn die Controller das nächste Mal eingeschaltet werden.

### <a name="how-i-can-check-battery-level"></a>Wie kann ich den Akku Pegel überprüfen?

In der [Windows Mixed Reality-Start](navigating-the-windows-mixed-reality-home.md)Seite können Sie Ihren Controller einschalten, um seine Akku Ebene auf der umgekehrten Seite des virtuellen Modells anzuzeigen. Es ist kein physischer Akku pegelindikator vorhanden.

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>Können Sie diese Controller ohne ein Headset verwenden? Nur für die Eingabe des Joysticks/Auslösers/usw.

Nicht für universelle Windows-Anwendungen.

## <a name="troubleshooting"></a>Fehlerbehebung

Weitere Informationen finden Sie im Leitfaden zur Problembehandlung für [Motion Controller](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers) .

## <a name="filing-motion-controller-feedbackbugs"></a>Einreichen von Feedback/Fehlern in Motion Controller

[Geben Sie uns Feedback](give-us-feedback.md) im Feedback-Hub mit der Kategorie "Mixed Reality-> Input".

## <a name="see-also"></a>Weitere Informationen:
* [Gesten und Motion-Controller in Unity](gestures-and-motion-controllers-in-unity.md)
* [Hände und Motion-Controller in DirectX](hands-and-motion-controllers-in-directx.md)
* [Gesten](gaze-and-commit.md#composite-gestures)
* [Mr-Eingabe 213: Motion-Controller](mixed-reality-213.md)
* [Leitfaden für Enthusiasten: Ihre Windows Mixed Reality-Startseite](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [Leitfaden für Enthusiasten: Verwenden von Spielen & apps in Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [Funktionsweise der inneren Nachverfolgung](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/tracking-system)
