---
title: Eyetracking – Blickverfolgung
description: Hololens 2 ermöglicht ein neues Maß an Kontext und menschliches Verständnis in der holografischen Benutzerfreundlichkeit, indem Entwicklern die Möglichkeit geboten wird, Informationen über den Benutzer zu verwenden.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: Augen Verfolgung, gemischte Realität, Eingabe, Augenblick, Kalibrierung
ms.openlocfilehash: 1f3699330fb4879258693b6959724441bd838d98
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491139"
---
# <a name="eye-tracking-on-hololens-2"></a>Blickverfolgung auf HoloLens 2

![Demo zur Eye-Nachverfolgung in mrtk](images/mrtk_et_scenemenu.jpg)

Hololens 2 ermöglicht ein neues Maß an Kontext und menschliches Verständnis in der holografischen Benutzerfreundlichkeit, indem Entwicklern die Möglichkeit geboten wird, Informationen über den Benutzer zu verwenden. Auf dieser Seite wird erläutert, wie Entwickler von der Eye-Nachverfolgung für verschiedene Anwendungsfälle profitieren können, und worauf Sie achten müssen, wenn Sie auf Augenblick basierende Benutzerinteraktionen entwerfen. 

Die Eye Tracking-API wurde mit dem Datenschutz eines Benutzers entworfen, sodass keine identifizierbaren Informationen, insbesondere jegliche Biometrie, übergeben werden. Bei der Überwachung von nach Verfolgungs fähigen Anwendungen muss der Benutzer der APP die Berechtigung zur Verwendung von Augen Verfolgungs Informationen erteilen. 


### <a name="device-support"></a>Unterstützung von Geräten
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

<br>

## <a name="calibration"></a>Energie 
Damit die Eye-Nachverfolgung ordnungsgemäß funktioniert, muss jeder Benutzer eine nach [Verfolgungs Benutzer-Kalibrierung](calibration.md) durchlaufen, für die der Benutzer eine Reihe von Holographic-Zielen betrachten muss. Dies ermöglicht es dem Gerät, das System für eine komfortablere und qualitativ hochwertige Anzeige für den Benutzer anzupassen und gleichzeitig eine genaue Eye-Nachverfolgung sicherzustellen. 

Die Augen Verfolgung sollte für die meisten Benutzer funktionieren, aber es gibt selten Fälle, in denen ein Benutzer möglicherweise nicht in der Lage ist, eine Kalibrierung erfolgreich durchzusetzen. Die Kalibrierung kann aus verschiedenen Gründen fehlschlagen, einschließlich, aber nicht beschränkt auf: 
* Der Benutzer hat sich zuvor für den Kalibrierungsprozess entschieden.
* Der Benutzer ist abgelenkt und hat die kalibrierungsziele nicht befolgt.
* Der Benutzer verfügt über bestimmte Arten von Kontaktlinsen und-Gläsern, die das System noch nicht unterstützt. 
* Der Benutzer hat bestimmte Augen Physiologie, Augen Bedingungen oder eine Augenoperation, die das System noch nicht unterstützt.  
* Externe Faktoren behindern die zuverlässige Eye-Nachverfolgung, wie z. b. smudges auf den holten-Hypervisor oder-Brillen, intensive direkte Sonneneinstrahlung und-oksionen aufgrund von Haaren vor Augen.

Entwickler sollten sicherstellen, dass Sie angemessene Unterstützung für Benutzer bereitstellen, für die die Augen Verfolgungs Daten möglicherweise nicht verfügbar sind (die nicht in der Lage sind, erfolgreich zu kalibrieren). Wir haben Empfehlungen für Fall Back Lösungen im Abschnitt unten auf dieser Seite bereitgestellt. 

Weitere Informationen zur Kalibrierung und zur Gewährleistung eines reibungslosen Erlebnisses finden Sie auf unserer Seite zur [Benutzer seitigen Überwachung](calibration.md) .

<br>

## <a name="available-eye-tracking-data"></a>Verfügbare Augen Verfolgungs Daten
Bevor Sie sich ausführlich über bestimmte Anwendungsfälle für die Augenblick Eingaben beschäftigen, möchten wir kurz auf die Funktionen hinweisen, die von der hololens 2 [Eye Tracking-API](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose) bereitstellt werden. Entwickler erhalten Zugriff auf einen Augenblick Strahl ("Ursprung" und "Richtung") bei ungefähr _30 fps (30 Hz)_ .
Ausführlichere Informationen zum Zugreifen auf die Augen Verfolgungs Daten finden Sie in unseren Entwickler Handbüchern zur Verwendung von [Eye-Blick in DirectX](gaze-in-directx.md) und [im Blickwinkel in Unity](https://aka.ms/mrtk-eyes).

Der vorhergesagte Augenblick liegt ungefähr innerhalb von 1,5 Grad im visuellen Winkel um das eigentliche Ziel (siehe Abbildung unten). Da geringfügige unveränderungen erwartet werden, sollten Entwickler einen gewissen Rand um diesen niedrigeren Grenzwert planen (z. b. können 2.0-3.0 Grad zu einer viel komfortableren Umgebung führen). Im folgenden wird erläutert, wie Sie die Auswahl kleiner Ziele im folgenden ausführlicher behandeln. Damit die Blickverfolgung exakt funktioniert, muss jeder Benutzer eine Benutzerkalibrierung für seine Blickverfolgung durchlaufen. 

![Optimale Zielgröße im Abstand von 2 Metern](images/gazetargeting-size-1000px.jpg)<br>
*Optimale Zielgröße bei einer Entfernung von 2 Stunden*

<br>

## <a name="use-cases"></a>Anwendungsfälle
Mit der Blickverfolgung können Anwendungen in Echtzeit verfolgen, wohin der Benutzer schaut. In den folgenden Anwendungsfällen werden einige Interaktionen beschrieben, die mit der Eye-Nachverfolgung auf hololens 2 in gemischter Realität möglich sind.
Beachten Sie, dass diese Anwendungsfälle noch nicht Teil der Holographic Shell-Oberfläche sind (d. h. die Schnittstelle, die Sie beim Start der hololens 2 sehen).
Sie können einige davon im [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)ausprobieren, das einige interessante und leistungsstarke Beispiele für die Verwendung der Eye-Nachverfolgung bereitstellt, wie z. b. schnelle und mühelose durchschauen unterstützte Ziel Optionen, und den automatischen Bildlauf durch Text basierend auf dem, was der Benutzer sieht. 

### <a name="user-intent"></a>Benutzerabsicht    
Informationen dazu, wo und was ein Benutzer untersucht, bieten einen leistungsstarken **Kontext für andere Eingaben**, wie z. b. Voice, Hands und Controller.
Dies kann für verschiedene Aufgaben verwendet werden.
Dies kann z. b. von schnell und mühelos auf die gesamte Szene **abzielen** , indem Sie einfach ein Hologramm betrachten und *"auswählen"* (auch "anzeigen" [und "Commit](gaze-and-commit.md)") oder *"put this..."* auswählen, um zu sehen, wo der Benutzer das – Hologramm platzieren möchte.  *vorhanden*sind. Beispiele hierfür finden Sie in den Artikeln [Mixed Reality Toolkit – Eye-supported Target Selection](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) (Mixed Reality-Toolkit – Blickgestützte Zielauswahl) und [Mixed Reality Toolkit – Eye-supported Target Positioning](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html) (Mixed Reality-Toolkit – Blickgestützte Zielpositionierung).

Außerdem kann ein Beispiel für die Benutzer Absicht die Verwendung von Informationen zu den Benutzern, die von Benutzern untersucht werden, beinhalten, um die Einbindung von verkörperten virtuellen Agents und interaktiven holograms Beispielsweise können virtuelle Agents verfügbare Optionen und ihr Verhalten basierend auf dem aktuell angezeigten Inhalt anpassen. 

### <a name="implicit-actions"></a>Implizite Aktionen
Die Kategorie der impliziten Aktionen steht in enger Beziehung zur Benutzerabsicht.
Die Idee ist, dass holograms oder Benutzeroberflächen Elemente auf eine instanzitive Weise reagieren, die nicht einmal so aussieht, als ob der Benutzer mit dem System interagiert, sondern dass das System und der Benutzer synchron sind. Ein Beispiel hierfür ist ein bidirektionaler **automatischer** Bildlauf, bei dem der Benutzer einen langen Text lesen kann, der automatisch mit dem Scrollen beginnt, sobald der Benutzer am unteren Rand des Textfelds geht, um den Benutzer im Lesevorgang zu halten, ohne einen Finger zu heben.  
Ein wichtiger Aspekt hierbei ist, dass sich die Scrollgeschwindigkeit an die Lesegeschwindigkeit des Benutzers anpasst.
Ein weiteres Beispiel sind die **Augen unterstützten Zoom-und Schwenken-** Elemente, bei denen der Benutzer das Gefühl hat, dass er sich genau zu dem befindet, worauf er sich konzentriert Das Auslösen und Steuern der Zoomgeschwindigkeit kann mit der Stimme oder Hand Eingaben gesteuert werden, was wichtig ist, um dem Benutzer das Gefühl der Kontrolle zu bieten, während er nicht überlastet ist. Diese Entwurfs Überlegungen werden im folgenden ausführlicher erläutert. Nach dem vergrößern kann der Benutzer problemlos auf den Kurs einer Straße folgen, um seine Umgebung zu durchsuchen, indem er einfach den Augenblick verwendet.
Demobeispiele für diese Arten von Interaktion finden Sie im Beispiel [Mixed Reality Toolkit – Eye-supported Navigation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html) (Mixed Reality-Toolkit – Blickgestützte Navigation).

Weitere Anwendungsfälle für _implizite Aktionen_:
- **Intelligente Benachrichtigungen:** Haben Sie sich immer über Benachrichtigungen benachrichtigt, wenn Sie sich mit den Nachrichten beschäftigen? Wenn Sie das Konto berücksichtigen, auf das ein Benutzer achten wird, können Sie diese Umgebung verbessern, indem Sie Benachrichtigungen von dem Speicherort der Benutzer auslagern Dadurch werden Ablenkungen eingeschränkt und automatisch geschlossen, sobald der Benutzer das Lesen abgeschlossen hat. 
- **Aufmerksame Hologramme:** Holograms, die bei der Verwendung von auf eine beliebige Weise reagieren. Dies kann von leicht leuchtenden Benutzeroberflächen Elementen bis hin zu einem langsam blühenden Blumen Wert zu einem virtuellen Hund, der mit der Betrachtung des Benutzers beginnt, und dem Ende seines Endes. Diese Interaktion kann ein interessantes Gefühl der Konnektivität und Zufriedenheit in Ihrer Anwendung darstellen.

### <a name="attention-tracking"></a>Aufmerksamkeitsverfolgung   
Informationen dazu, wo oder was Benutzer sehen, können ein äußerst leistungsfähiges Tool sein. Es kann helfen, die Nutzbarkeit von Entwürfen zu bewerten und Probleme in Workflows zu identifizieren, um Sie effizienter zu gestalten.
Die Visualisierung und Analyse von Augen Nachverfolgung ist eine gängige Vorgehensweise in verschiedenen Anwendungsbereichen. Mit hololens 2 bieten wir eine neue Dimension für dieses Verständnis, da 3D holograms in realen Kontexten platziert und entsprechend bewertet werden können. Das [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) enthält grundlegende Beispiele für das Protokollieren und Laden von Augen Verfolgungs Daten und deren Visualisierung.
Microsoft ist für die Vereinfachung von Innovationen vorgesehen und stellt gleichzeitig sicher, dass die Benutzer über eine fundierte und transparente benutzerfreundliche Darstellung verfügen.  Wir arbeiten mit unseren Entwicklern und UX-Teams zusammen, um eine Anleitung für Drittanbieter bereitzustellen, um sicherzustellen, dass die Benutzererfahrung auf den Benutzer ausgerichtet ist.  


Zu diesem Bereich zählen möglicherweise auch die folgenden Anwendungen: 
-   Remote Ansicht für den **Augenblick:** Remote-Blick Visualisierungen: visualisieren Sie, welche Remote Mitarbeiter sich ansehen, um sofortiges Feedback bereitstellen und genauere Informationen verarbeiten zu können.
-   **Forschungsstudien für Benutzer:** Die Nachverfolgung von Nachrichten kann den Forschern helfen, mehr Einblicke in die Art und Weise zu erhalten, wie Benutzer die natürliche Umgebung wahrnehmen und mit ihr interagieren, ohne sich zu stören, um mehr instanzielle Interaktionen zwischen Die Eye-Nachverfolgung kann Informationen bereitstellen, die nicht direkt von Teilnehmern in der Studie artikuliert werden, die andernfalls leicht vom Forscher übersehen werden. 
-   **Schulungs-und Leistungsüberwachung:** Üben und optimieren Sie die Ausführung von Tasks, indem Sie Engpässe im Ausführungs Fluss effektiver erkennen. Die Eye-Nachverfolgung kann natürliche Echtzeitinformationen und Ziel Informationen bereitstellen, um die Schulung, Produktivität und Sicherheit am Arbeitsplatz zu verbessern. 
-   **Entwurfs Auswertungen, Marketing-und consumerforschung:** Die Augen Verfolgung ermöglicht kommerziellen Unternehmen das Durchführen von Marketing-und consumerstudien in realen Umgebungen oder das Analysieren der Aufmerksamkeit eines Benutzers, um das Produkt oder den Raum Entwurf zu verbessern. 

### <a name="additional-use-cases"></a>Weitere Anwendungsfälle
- **Spiele:** Wollten Sie jemals über Supermächte verfügen? Hier kommt Ihre Chance! Sie können holograms durch ein-und ansehen. Lösen Sie die Laserstrahlen von ihren Augen. Probieren Sie es in [roboraid für hololens 2](https://www.microsoft.com/p/roboraid/9nblggh5fv3j)aus.
Verwandeln Sie Feinde in den Stein, oder fixieren Sie Sie. Verwenden Sie Ihren Röntgenblick, um Gebäude zu erkunden. Ihrer Phantasie sind keine Grenzen gesetzt!
Achten Sie darauf, den Benutzer nicht zu überfordern. um weitere Informationen zu erhalten, sehen Sie sich die Richtlinien für den auf [Augenblick basierenden Eingabe Entwurf](eye-gaze-interaction.md)an.

- **Ausdrucksstarke Avatare:** Die Eye-Nachverfolgung hilft bei komplexeren 3D-Avataren durch die Verwendung von Live-Eye-nach Verfolgungs Daten, um die Augen des Avatare zu animieren, die den Inhalt des Benutzers angeben. 

- **Text Eintrag:** Die Eye-Nachverfolgung kann als Alternative für den Text Eintrag mit geringem Aufwand verwendet werden, insbesondere dann, wenn Sprache oder Hände unpraktisch zu verwenden sind. 

<br>

## <a name="using-eye-gaze-for-interaction"></a>Verwenden des Augenblicks für die Interaktion
Das Entwickeln einer Interaktion, die die schnelle Ziel Ausrichtung nutzt, kann eine Herausforderung darstellen.
Einerseits bewegen sich die Augen so schnell, dass Sie sorgfältig darauf achten müssen, wie Sie die Eingabe im Blickwinkel verwenden, da die Benutzer die Benutzeroberflächen möglicherweise als überwältigend oder ablenkend empfinden. Andererseits können Sie auch wirklich magische Erfahrungen erstellen, die Ihre Benutzer begeistern werden! Um Ihnen zu helfen, sehen Sie sich die Übersicht über die wichtigsten Vorteile, Herausforderungen und Entwurfs Empfehlungen für die [Interaktion](eye-gaze-interaction.md)an. 
 
## <a name="fallback-solutions-when-eye-tracking-is-not-available"></a>Fall Back Lösungen, wenn die Augen Verfolgung nicht verfügbar ist

In seltenen Fällen sind die Augen Verfolgungs Daten möglicherweise nicht verfügbar.
Dies kann auf verschiedene Ursachen zurückzuführen sein, von denen die am häufigsten aufgelisteten aufgeführt sind:
* Das System konnte [den Benutzer nicht kalibrieren](calibration.md).
* Der Benutzer hat die [Kalibrierung](calibration.md)übersprungen.   
* Der Benutzer ist zwar kalibriert, hat sich jedoch entschieden, der APP keine Berechtigung zur Verwendung der Augen Verfolgungs Daten zu erteilen.    
* Der Benutzer hat eine eindeutige Brillen-oder Augen Bedingung, die vom System noch nicht unterstützt wird.    
* Externe Faktoren behindern die zuverlässige Eye-Nachverfolgung, wie z. b. smudges auf den holten-Hypervisor oder-Brillen, intensive direkte Sonneneinstrahlung und-oksionen aufgrund von Haaren vor Augen.   

Daher sollten Entwickler sicherstellen, dass für diese Benutzer eine geeignete Ausweich Unterstützung vorhanden ist. Auf der Seite " [Eye Tracking in DirectX](gaze-in-directx.md#fallback-when-eye-tracking-is-not-available) " werden die APIs erläutert, die erforderlich sind, um zu ermitteln, ob Eye-Überwachungsdaten verfügbar sind. 

Einige Benutzer haben sich möglicherweise bewusst entschieden, den Zugriff auf Ihre Augen Verfolgungs Daten aufzuheben, und sind mit dem Nachteil einer geringeren Benutzerfunktion für den Datenschutz, dass Sie keinen Zugriff auf Ihre Überwachungsdaten bereitstellt, in einigen Fällen kann dies unbeabsichtigt sein.  
Wenn Ihre APP die Augen Nachverfolgung verwendet, und dies ein wichtiger Bestandteil der Benutzeroberflächen ist, empfiehlt es sich, diese Funktion an den Benutzer zu übermitteln.     
Wenn Sie den Benutzer darüber informieren, warum die Augen Verfolgung für Ihre Anwendung wichtig ist (vielleicht sogar einige erweiterte Features auflisten), um das volle Potenzial Ihrer Anwendung zu erhalten, kann der Benutzer helfen, besser zu verstehen, was Sie erhalten.   
Helfen Sie dem Benutzer, herauszufinden, warum die Eye-Nachverfolgung möglicherweise nicht funktioniert (basierend auf den obigen Überprüfungen), und bieten Sie einige Vorschläge, um potenzielle Probleme schnell zu beheben.     
Wenn Sie z. b. feststellen können, dass das System die Eye-Nachverfolgung unterstützt, wird der Benutzer kalibriert und hat selbst seine Berechtigung, aber es werden keine Augen Verfolgungs Daten empfangen.    
Beachten Sie, dass es selten Fälle gibt, in denen die Eye-Nachverfolgung möglicherweise einfach nicht funktioniert.   
Achten Sie daher darauf, dass Sie Erinnerungen zum Aktivieren der Eye-Nachverfolgung in Ihrer APP verwerfen oder sogar deaktivieren können.

### <a name="fallback-for-apps-using-eye-gaze-as-a-primary-input-pointer"></a>Fallback für apps, die den Augenblick als primären Eingabe Zeiger verwenden
Wenn Ihre APP den Augenblick als Zeiger Eingabe verwendet, um in der Szene schnell holograms auszuwählen, sind die Augen Verfolgungs Daten nicht verfügbar. es wird empfohlen, auf den Mauszeiger zurückzukehren und den Cursor für den Cursor zu zeigen. Es wird empfohlen, ein Timeout (z. b. 500 – 1.500 ms) zu verwenden, um zu bestimmen, ob gewechselt werden soll. Diese Aktion verhindert, dass Cursor jedes Mal angezeigt werden, wenn das System die Nachverfolgung aufgrund von schnellen Augenbewegungen oder winas und Blinks kurz verlieren kann. Wenn Sie ein Unity-Entwickler sind, wird der automatische Fall Back auf den Head-Blick bereits im Mixed Reality Toolkit behandelt. Wenn Sie ein DirectX-Entwickler sind, müssen Sie diesen Switch selbst verarbeiten.

### <a name="fallback-for-other-eye-tracking-specific-applications"></a>Fallback für andere Überwachungs spezifische Anwendungen
Ihre APP kann den Augenblick auf eine einzigartige Weise verwenden, die speziell auf die Augen zugeschnitten ist. Beispielsweise werden bei der Animation eines Avatars oder bei der Augen basierten Aufmerksamkeit Heatmaps auf genaue Informationen zur visuellen Aufmerksamkeit angewiesen. In diesem Fall gibt es keinen klaren Fallback. Wenn die Augen Verfolgung nicht verfügbar ist, müssen diese Funktionen möglicherweise einfach deaktiviert werden.
Auch hier wird empfohlen, dass Sie dem Benutzer, der möglicherweise nicht weiß, dass die Funktion nicht funktioniert, eindeutig kommunizieren.

<br>

Auf dieser Seite haben Sie hoffentlich einen guten Überblick erhalten, mit dem Sie die Rolle der Eye-Nachverfolgung und die Eingabe des Augenblicks für hololens 2 verstanden haben. Um mit der Entwicklung zu beginnen, sehen Sie sich unsere Informationen über die Rolle des [Augenblicks für die Interaktion mit holograms](eye-gaze-interaction.md), den [Augenblick in Unity](https://aka.ms/mrtk-eyes) und den [Augenblick in DirectX](gaze-in-directx.md)an.


## <a name="see-also"></a>Weitere Informationen
* [Kalibrierung](calibration.md)
* [Komfort](comfort.md)
* [Interaktion durch Anvisieren](eye-gaze-interaction.md)
* [Blick in DirectX](gaze-in-directx.md)
* [Blick in Unity (Mixed Reality Toolkit)](https://aka.ms/mrtk-eyes)
* [Anvisieren und Ausführen](gaze-and-commit.md)
* [Spracheingabe](voice-design.md)


