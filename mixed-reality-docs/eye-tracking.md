---
title: Eyetracking – Blickverfolgung
description: Mit HoloLens 2 erschließt sich in Bezug auf Kontext und menschliches Verständnis eine neue Ebene der holografischen Erfahrung. Das Gerät bietet Entwicklern nämlich die Möglichkeit, Informationen zur Zielanvisierung mit den Augen und zur Blickbewegung des Benutzers zu verwenden.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: Augen Verfolgung, gemischte Realität, Eingabe, Augenblick, Kalibrierung
ms.openlocfilehash: 60de5ceb9f55ca7e2f74856af9bd75567763e382
ms.sourcegitcommit: a5dc182da237f63f0487d40a2e11894027208b6c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2019
ms.locfileid: "73441119"
---
# <a name="eye-tracking-on-hololens-2"></a>Blickverfolgung auf HoloLens 2

![Demo zur Eye-Nachverfolgung in mrtk](images/mrtk_et_scenemenu.jpg)

Mit HoloLens 2 erschließt sich in Bezug auf Kontext und menschliches Verständnis eine neue Ebene der holografischen Erfahrung. Das Gerät bietet Entwicklern nämlich die Möglichkeit, Informationen zur Zielanvisierung mit den Augen und zur Blickbewegung des Benutzers zu verwenden. Auf dieser Seite finden Sie eine Übersicht über diese neue Funktion für Entwickler und Designer, wie Sie von der Augen Verfolgung für verschiedene Anwendungsfälle und grundlegenden Anleitungen für Entwickler profitieren können. 


## <a name="calibration"></a>Energie 
Damit die Eye-Nachverfolgung ordnungsgemäß funktioniert, muss jeder Benutzer eine nach [Verfolgungs Benutzer-Kalibrierung](calibration.md) durchlaufen, für die der Benutzer eine Reihe von Holographic-Zielen betrachten muss. Dies ermöglicht es dem Gerät, das System für eine komfortablere und qualitativ hochwertige Anzeige für den Benutzer anzupassen und gleichzeitig eine genaue Eye-Nachverfolgung sicherzustellen. Die Augen Verfolgung sollte für die meisten Benutzer funktionieren, aber es gibt selten Fälle, in denen ein Benutzer möglicherweise nicht in der Lage ist, die Kalibrierung erfolgreich durchzusetzen.
Weitere Informationen zur Kalibrierung und zur Gewährleistung eines reibungslosen Erlebnisses finden Sie auf unserer Seite zur [Benutzer seitigen Überwachung](calibration.md) .


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
     <td>Augenblick</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="available-eye-tracking-data"></a>Verfügbare Augen Verfolgungs Daten
Bevor Sie sich ausführlich über bestimmte Anwendungsfälle für die Augenblick Eingaben beschäftigen, möchten wir kurz auf die Funktionen hinweisen, die von der hololens 2 [Eye Tracking-API](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose) bereitstellt werden. Entwickler erhalten Zugriff auf einen Augenblick Strahl ("Ursprung" und "Richtung") bei ungefähr _30 fps (30 Hz)_ .
Ausführlichere Informationen zum Zugreifen auf die Augen Verfolgungs Daten finden Sie in den Entwickler Handbüchern zur Verwendung von [Eye-Blick in DirectX](gaze-in-directx.md) und [im Blickwinkel in Unity](https://aka.ms/mrtk-eyes).

Der vorhergesagte Augenblick liegt ungefähr innerhalb von 1,5 Grad im visuellen Winkel um das eigentliche Ziel (siehe Abbildung unten). Da geringfügige unveränderungen erwartet werden, sollten Entwickler einen gewissen Rand um diesen niedrigeren Grenzwert planen (z. b. können 2.0-3.0 Grad zu einer viel komfortableren Umgebung führen). Im folgenden wird erläutert, wie Sie die Auswahl kleiner Ziele im folgenden ausführlicher behandeln. Damit die Blickverfolgung exakt funktioniert, muss jeder Benutzer eine Benutzerkalibrierung für seine Blickverfolgung durchlaufen. 

![Optimale Zielgröße im Abstand von 2 Metern](images/gazetargeting-size-1000px.jpg)<br>
*Optimale Zielgröße bei einer Entfernung von 2 Stunden*

<br>

## <a name="use-cases"></a>Anwendungsfälle
Mit der Blickverfolgung können Anwendungen in Echtzeit verfolgen, wohin der Benutzer schaut. In den folgenden Anwendungsfällen werden einige Interaktionen beschrieben, die mit der Eye-Nachverfolgung auf hololens 2 in gemischter Realität möglich sind.
Beachten Sie, dass diese Anwendungsfälle noch nicht Teil der Holographic Shell-Oberfläche sind (d. h. die Schnittstelle, die Sie beim Start der hololens 2 sehen).
Sie können einige von Ihnen im [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) ausprobieren, das einige interessante und leistungsstarke Beispiele für die Verwendung der Eye-Nachverfolgung bereitstellt, z. b. schnelle und mühelose Unterstützung für die Zielauswahl und Automatisches Scrollen durch Text basiert. das, was der Benutzer sieht. 

### <a name="user-intent"></a>Benutzerabsicht    
Informationen dazu, wo und was ein Benutzer untersucht, bieten einen leistungsstarken **Kontext für andere Eingaben**, wie z. b. Voice, Hands und Controller.
Dies kann für verschiedene Aufgaben verwendet werden.
Dies kann z. b. von schnell und mühelos auf die gesamte Szene **abzielen** , indem Sie einfach ein Hologramm betrachten und *"auswählen"* (siehe auch "anzeigen" [und "Commit](gaze-and-commit.md)") oder *"put this..."* und dann den Speicherort des Benutzers ansehen. Ich möchte das – Hologramm platzieren und sagen: *"... vorhanden*sind. Beispiele hierfür finden Sie in den Artikeln [Mixed Reality Toolkit – Eye-supported Target Selection](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) (Mixed Reality-Toolkit – Blickgestützte Zielauswahl) und [Mixed Reality Toolkit – Eye-supported Target Positioning](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html) (Mixed Reality-Toolkit – Blickgestützte Zielpositionierung).

Außerdem kann ein Beispiel für die Benutzer Absicht die Verwendung von Informationen zu den Benutzern, die von Benutzern untersucht werden, beinhalten, um die Einbindung von verkörperten virtuellen Agents und interaktiven holograms Beispielsweise können virtuelle Agents verfügbare Optionen und ihr Verhalten basierend auf dem aktuell angezeigten Inhalt anpassen. 

### <a name="implicit-actions"></a>Implizite Aktionen
Die Kategorie der impliziten Aktionen steht in enger Beziehung zur Benutzerabsicht.
Die Idee ist, dass holograms oder Benutzeroberflächen Elemente auf eine instanzitive Weise reagieren, die nicht einmal so aussieht, als ob der Benutzer mit dem System interagiert, sondern dass das System und der Benutzer synchron sind. Ein Beispiel hierfür ist ein bidirektionaler **automatischer** Bildlauf, bei dem der Benutzer einen langen Text lesen kann, der automatisch mit dem Scrollen beginnt, sobald der Benutzer zum unteren Rand des Textfelds gelangt, damit der Benutzer den Lesevorgang ohne Fingerabdruck durchführt.  
Ein wichtiger Aspekt hierbei ist, dass sich die Scrollgeschwindigkeit an die Lesegeschwindigkeit des Benutzers anpasst.
Ein weiteres Beispiel sind die **Augen unterstützten Zoom-und Schwenken-** Elemente, bei denen der Benutzer das Gefühl hat, dass er sich genau zu dem befindet, worauf er sich konzentriert Das Auslösen von Zoom und das Steuern der Zoomgeschwindigkeit kann durch die Stimme oder Hand Eingabe gesteuert werden. Dies ist wichtig, um dem Benutzer das Gefühl der Kontrolle zu bieten, ohne dass eine über Überlastung erfolgt. Diese Entwurfs Überlegungen werden im folgenden ausführlicher erläutert. Nach dem vergrößern kann der Benutzer problemlos auf den Kurs einer Straße folgen, um seine Umgebung zu durchsuchen, indem er einfach den Augenblick verwendet.
Demobeispiele für diese Arten von Interaktion finden Sie im Beispiel [Mixed Reality Toolkit – Eye-supported Navigation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) (Mixed Reality-Toolkit – Blickgestützte Navigation).

Weitere Anwendungsfälle für _implizite Aktionen_:
- **Intelligente Benachrichtigungen:** Haben Sie sich immer über Benachrichtigungen benachrichtigt, wenn Sie sich mit den Nachrichten beschäftigen? Wenn Sie das Konto berücksichtigen, auf das ein Benutzer achten wird, können Sie diese Umgebung verbessern, indem Sie Benachrichtigungen von dem Speicherort der Benutzer auslagern Dadurch werden Ablenkungen eingeschränkt und automatisch geschlossen, sobald der Benutzer das Lesen abgeschlossen hat. 
- **Aufmerksame Hologramme:** Holograms, die bei der Verwendung von auf eine beliebige Weise reagieren. Dies kann von leicht leuchtenden Benutzeroberflächen Elementen bis hin zu einem langsam blühenden Blumen Wert zu einem virtuellen Hund, der mit der Betrachtung des Benutzers beginnt, und dem Ende seines Endes. Diese Interaktion kann ein interessantes Gefühl der Konnektivität und Zufriedenheit in Ihrer Anwendung darstellen.

### <a name="attention-tracking"></a>Aufmerksamkeitsverfolgung   
Informationen dazu, wo oder was Benutzer sehen, ist ein äußerst leistungsfähiges Tool zum Bewerten der Nutzbarkeit von Entwürfen und zum Erkennen von Problemen in effizienten Workflows. Die Visualisierung und Analyse von Augen Nachverfolgung ist eine gängige Vorgehensweise in verschiedenen Anwendungsbereichen. Mit hololens 2 bieten wir eine neue Dimension für dieses Verständnis, da 3D holograms in realen Kontexten platziert und entsprechend bewertet werden können. Das [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) enthält grundlegende Beispiele für das Protokollieren und Laden von Augen Verfolgungs Daten und deren Visualisierung.

Zu diesem Bereich zählen möglicherweise auch die folgenden Anwendungen: 
-   Remote Ansicht für den **Augenblick:** Visualisieren Sie, welche Remote Mitarbeiter sich ansehen, um das gemeinsame Verständnis zu verbessern.
-   **Forschungsstudien für Benutzer:** Mit der Nachverfolgung von Nachrichten können Sie besser verstehen, wie wir unsere Umgebung wahrnehmen und mit ihr in Kontakt treten, was zu besseren sinnvollen Modellen bei der Verwendung von Benutzer Computern beiträgt. 
-   **Schulung:** Verbessertes Training von Einsteiger durch das besseren Verständnis der visuellen Suchmuster von Experten und deren Hand Zeitangabe für komplexe Aufgaben, wie z. b. die Analyse von medizinischen Daten oder betriebsmaschinen.
-   **Entwurfs Auswertungen und Marktforschung:** Die Augen Verfolgung ist ein gängiges Tool für Marktforschung, wenn Sie Website-und Produktentwürfe evaluieren. Mit hololens 2 können wir dies auf 3D-Räume ausweiten, indem wir die Entwurfs Varianten digitaler Produkte mit der physischen Umgebung Zusammenführen. 

### <a name="additional-use-cases"></a>Weitere Anwendungsfälle
- **Spiele:** Wollten Sie jemals über Supermächte verfügen? Hier kommt Ihre Chance! Sie können holograms durch ein-und ansehen. Lösen Sie die Laserstrahlen von ihren Augen. Probieren Sie es in [roboraid für hololens 2](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)aus.
Verwandeln Sie Feinde in den Stein, oder fixieren Sie Sie. Verwenden Sie Ihren Röntgenblick, um Gebäude zu erkunden. Ihrer Phantasie sind keine Grenzen gesetzt!
Achten Sie darauf, den Benutzer nicht zu überfordern. um weitere Informationen zu erhalten, sehen Sie sich die Richtlinien für den auf [Augenblick basierenden Eingabe Entwurf](eye-gaze-interaction.md)an.

- **Ausdrucksstarke Avatare:** Die Eye-Nachverfolgung hilft bei komplexeren 3D-Avataren durch die Verwendung von Live-Eye-nach Verfolgungs Daten, um die Augen des Avatare zu animieren, die den Inhalt des Benutzers angeben. 

- **Text Eintrag:** Die Eye-Nachverfolgung kann als Alternative für den Text Eintrag mit geringem Aufwand verwendet werden, insbesondere dann, wenn Sprache oder Hände unpraktisch zu verwenden sind. 

<br>

## <a name="using-eye-gaze-for-interaction"></a>Verwenden des Augenblicks für die Interaktion
Das Entwickeln einer Interaktion, die die schnelle Ziel Ausrichtung nutzt, kann eine Herausforderung darstellen.
Einerseits bewegen sich die Augen so schnell, dass Sie sorgfältig darauf achten müssen, wie Sie die Eingabe im Blickwinkel verwenden, da der Benutzer andernfalls die Benutzeroberflächen ausstellt, die überwältigend oder ablenkend sind. Andererseits können Sie auch wirklich magische Erfahrungen erstellen, die Ihre Benutzer begeistern werden! Um Ihnen zu helfen, sehen Sie sich die Übersicht über die wichtigsten Vorteile, Herausforderungen und Entwurfs Empfehlungen für die [Interaktion](eye-gaze-interaction.md)an. 

<br>
 
## <a name="dev-guidance-what-if-eye-tracking-is-not-available"></a>Entwicklungs Leit Faden: Was geschieht, wenn die Augen Nachverfolgung nicht verfügbar ist?
Es kann Situationen geben, in denen Ihre APP aufgrund verschiedener Gründe keine Augen Verfolgungs Daten empfängt, einschließlich, aber nicht beschränkt auf:
* Der Benutzer hat die Eye Tracking-Kalibrierung übersprungen.
* Der Benutzer hat eine Kalibrierung durchführen, entschied sich aber dafür, der APP keine Berechtigung zur Verwendung Ihrer Überwachungsdaten zu erteilen.
* Der Benutzer hat eine eindeutige Brillen-oder Augen Bedingung, die vom System noch nicht unterstützt wird.
* Externe Faktoren behindern die zuverlässige Eye-Nachverfolgung, wie z. b. smudges auf den holten-Hypervisor oder-Brillen, intensive direkte Sonneneinstrahlung und-oksionen aufgrund von Haaren vor Augen.

Als App-Entwickler bedeutet dies, dass Sie die Unterstützung von Benutzern berücksichtigen müssen, für die möglicherweise keine Überwachungsdaten verfügbar sind. Im folgenden wird erläutert, wie Sie erkennen können, ob die Eye-Nachverfolgung verfügbar ist, und wie Sie sich behandeln, wenn Sie für verschiedene Anwendungen nicht verfügbar ist.

### <a name="1-how-to-detect-that-eye-tracking-is-available"></a>1. erkennen, dass die Augen Verfolgung verfügbar ist
Es gibt einige Überprüfungen, um zu bestimmen, ob die Augen Verfolgungs Daten verfügbar sind. Überprüfen Sie, ob...
* ... Das System unterstützt die Augen Verfolgung überhaupt. Wenden Sie die folgende *Methode*an: [Windows. perception. People. eyespose. IsSupported ()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)

* ... der Benutzer ist kalibriert. Folgende *Eigenschaft*aufzurufen: [Windows. perception. People. eyespose. iscalibrationvalid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)

* ... der Benutzer hat der APP die Berechtigung zur Verwendung der Augen Verfolgungs Daten erteilt: Rufen Sie den aktuellen _"gazinput Access Status"_ ab. Ein Beispiel hierfür finden Sie unter [anfordern des Zugriffs auf die Eingabe](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).

Darüber hinaus können Sie überprüfen, ob Ihre Augen Verfolgungs Daten nicht veraltet sind, indem Sie ein Timeout zwischen empfangenen Datenaktualisierungen für die Augen Verfolgung hinzufügen und andernfalls auf den Haupt Blick zurückgreifen, wie unten erläutert. 

Wie oben beschrieben, gibt es verschiedene Gründe, warum die Augen Verfolgungs Daten möglicherweise nicht verfügbar sind. Einige Benutzer haben sich möglicherweise bewusst entschieden, den Zugriff auf Ihre Augen Verfolgungs Daten aufzuheben, und sind mit dem Nachteil einer geringeren Benutzerfunktion für den Datenschutz, dass Sie keinen Zugriff auf Ihre Überwachungsdaten bereitstellt, in einigen Fällen kann dies unbeabsichtigt sein. Wenn Ihre APP die Augen Nachverfolgung verwendet, und dies ein wichtiger Bestandteil der Benutzeroberflächen ist, empfiehlt es sich, diese Funktion an den Benutzer zu übermitteln. Wenn Sie den Benutzer darüber informieren, warum die Augen Verfolgung für Ihre Anwendung wichtig ist (möglicherweise sogar durch das Auflisten einiger verbesserter Features), um das volle Potenzial Ihrer Anwendung zu erhalten, können Sie dem Benutzer helfen, die Ergebnisse besser zu verstehen. Helfen Sie dem Benutzer, herauszufinden, warum die Eye-Nachverfolgung möglicherweise nicht funktioniert (basierend auf den obigen Überprüfungen), und bieten Sie einige Vorschläge, um potenzielle Probleme schnell zu beheben. Wenn Sie z. b. feststellen können, dass das System die Eye-Nachverfolgung unterstützt, wird der Benutzer kalibriert und selbst seine Berechtigung erteilt, aber es werden keine Augen Verfolgungs Daten empfangen. Beachten Sie jedoch, dass es selten Fälle gibt, in denen die Eye-Nachverfolgung möglicherweise einfach nicht funktioniert. Achten Sie daher darauf, dass Sie Erinnerungen zum Aktivieren der Eye-Nachverfolgung in Ihrer APP verwerfen oder sogar deaktivieren können.

### <a name="2-fallback-for-apps-using-eye-gaze-as-a-primary-input-pointer"></a>2. Fallback für apps, die den Augenblick als primären Eingabe Zeiger verwenden
Wenn Ihre APP den Augenblick als Zeiger Eingabe verwendet, um in der Szene schnell holograms auszuwählen, sind die Augen Verfolgungs Daten nicht verfügbar. es wird empfohlen, auf den Mauszeiger zurückzukehren und den Cursor für den Cursor zu zeigen. Es wird empfohlen, ein Timeout (z. b. 500 – 1.500 ms) zu verwenden, um zu bestimmen, ob gewechselt werden soll. Dadurch wird verhindert, dass ein Cursor jedes Mal, wenn das System die Nachverfolgung aufgrund von schnellen Augenbewegungen oder winas und Blinks verliert. Wenn Sie ein Unity-Entwickler sind, wird der automatische Fall Back auf den Head-Blick bereits im Mixed Reality Toolkit behandelt. Wenn Sie ein DirectX-Entwickler sind, müssen Sie diesen Switch selbst verarbeiten.

### <a name="3-fallback-for-other-eye-tracking-specific-applications"></a>3. Fallback für andere Überwachungs spezifische Anwendungen
Ihre APP kann den Augenblick auf eine einzigartige Weise verwenden, die speziell auf die Augen zugeschnitten ist, z. b. zum Animieren der Augen eines Avatars oder zur Augen basierten Aufmerksamkeit Heatmaps, die sich auf genaue Informationen zur visuellen Aufmerksamkeit verlassen. In diesem Fall gibt es keinen klaren Fallback. Wenn die Augen Verfolgung nicht verfügbar ist, müssen diese Funktionen möglicherweise einfach deaktiviert werden.
Auch hier wird empfohlen, dass Sie dem Benutzer, der möglicherweise nicht weiß, dass die Funktion nicht funktioniert, eindeutig kommunizieren.

<br>

Auf dieser Seite haben Sie hoffentlich einen guten Überblick erhalten, mit dem Sie die Rolle der Eye-Nachverfolgung und die Eingabe des Augenblicks für hololens 2 verstanden haben. Um mit der Entwicklung zu beginnen, sehen Sie sich unsere Informationen über die Rolle des [Augenblicks für die Interaktion mit holograms](eye-gaze-interaction.md), den [Augenblick in Unity](https://aka.ms/mrtk-eyes) und den [Augenblick in DirectX](gaze-in-directx.md)an.


## <a name="see-also"></a>Weitere Informationen:
* [Kalibrierung](calibration.md)
* [Komfort](comfort.md)
* [Auf Augenblick basierende Interaktion](eye-gaze-interaction.md)
* [Blick in DirectX](gaze-in-directx.md)
* [Blick in Unity (Mixed Reality Toolkit)](https://aka.ms/mrtk-eyes)
* [Blick und Commit](gaze-and-commit.md)
* [Spracheingabe](voice-design.md)


