---
title: Testen Ihrer APP auf hololens
description: Leitfaden und Vorschläge zum Testen Ihrer hololens-App
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Hololens, testen
ms.openlocfilehash: b8c8e7ea8f90633cbb3b2aa01764398ef9a5c12a
ms.sourcegitcommit: 76a7aa6e64e114b63ace058dd6d6d662b3c9f09e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/26/2019
ms.locfileid: "68507908"
---
# <a name="testing-your-app-on-hololens"></a>Testen Ihrer APP auf hololens

Das Testen von hololens-Anwendungen ähnelt dem Testen von Windows-Anwendungen. Alle üblichen Bereiche sollten berücksichtigt werden (Funktionalität, Interoperabilität, Leistung, Sicherheit, Zuverlässigkeit usw.). Es gibt jedoch einige Bereiche, die besondere Behandlung oder Aufmerksamkeit auf Details erfordern, die in PC-oder Phone-apps in der Regel nicht beachtet werden. Holographic apps müssen problemlos in verschiedenen Umgebungen ausgeführt werden. Außerdem müssen Sie jederzeit Leistung und Benutzerfreundlichkeit gewährleisten. Anleitungen zum Testen dieser Bereiche finden Sie in diesem Thema.

## <a name="performance"></a>Leistung

Holographic apps müssen problemlos in verschiedenen Umgebungen ausgeführt werden. Außerdem müssen Sie jederzeit Leistung und Benutzerfreundlichkeit gewährleisten. Die Leistung ist für die Benutzer Darstellung mit einer Holographic-APP, für die wir ein gesamtes Thema haben, so wichtig. Stellen Sie sicher, dass Sie die Grundlagen der [Leistung für gemischte Realität](understanding-performance-for-mixed-reality.md) lesen und befolgen.

## <a name="testing-3d-in-3d"></a>Testen von 3D in 3D
1. **Testen Sie Ihre APP in so vielen unterschiedlichen Bereichen wie möglich.** Probieren Sie große Räume, kleine Räume, Bäder, Küchen, Schlafräume, Büros usw. aus. Berücksichtigen Sie auch Räume mit nicht standardmäßigen Merkmalen, wie z. b. nicht vertikale Wände, gekrümmte Wände, nicht horizontale Obergrenzen. Funktioniert es gut, wenn es Zwischenräumen, Etagen und Durchgänge oder Treppen wechselt?
2. **Testen Sie Ihre APP in verschiedenen Beleuchtungsbedingungen.** Reagiert er ordnungsgemäß auf verschiedene Umgebungsbedingungen wie Beleuchtung, schwarze Oberflächen, transparente/reflektierend Oberflächen, wie z. b. Spiegel, Glas Wände usw.
3. **Testen Sie Ihre APP in verschiedenen bewegungsbedingungen.** Legen Sie auf dem Gerät fest, und testen Sie Ihre Szenarios in verschiedenen Bewegungs Zuständen. Reagiert der Dienst ordnungsgemäß auf eine andere Verschiebung oder einen stabilen Zustand?
4. **Testen Sie, wie Ihre APP aus unterschiedlichen Winkeln funktioniert.** Wenn Sie ein Welt gesperrtes Hologram haben, was passiert, wenn Ihr Benutzer darauf geht? Was geschieht, wenn etwas zwischen dem Benutzer und dem Hologram kommt? Was geschieht, wenn der Benutzer das – Hologramm von oben oder unten ansieht?
5. **Verwenden Sie räumliche und Audiohinweise.** Stellen Sie sicher, dass Ihre APP diese verwendet, um zu verhindern, dass der Benutzer verloren geht.
6. **Testen Sie Ihre APP auf unterschiedlichen Ebenen des Umgebungs Rauschens.** Wenn Sie Sprachbefehle implementiert haben, versuchen Sie, Sie mit unterschiedlichen Umgebungsgeräuschen aufzurufen.
7. **Testen Sie Ihre APP, und stellen Sie Sie**ein. Stellen Sie sicher, dass Sie sowohl an der Platz Position als auch an der Position
8. **Testen Sie Ihre APP aus unterschiedlichen Entfernungen**. Können UI-Elemente von weitem gelesen und interagiert werden? Reagiert Ihre APP darauf, dass Benutzer zu nahe an Ihren holograms gelangen?
9. **Testen Sie Ihre APP mit häufigen Interaktionen mit der APP-Leiste**. Alle App-Kacheln und universellen 2D-apps verfügen über eine [App-Leiste](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) , mit der Sie steuern können, wie die app in der gemischten Welt positioniert ist. Stellen Sie sicher, dass durch Klicken auf "entfernen" der App-Prozess ordnungsgemäß beendet wird und die Schaltfläche "zurück" im Kontext ihrer universellen 2D-App unterstützt Versuchen Sie, die APP im [Anpassungsmodus](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) zu skalieren und zu verschieben, während Sie aktiv ist, während Sie eine angehaltene App-Kachel ist.

### <a name="environmental-test-matrix"></a>Umgebungs Test Matrix

![Umgebungs Test Matrix für die hololens-App-Entwicklung](images/environment-matrix-600px.png)

## <a name="comfort"></a>Bequem
1. **Ausschneide Flächen.** Achten Sie darauf, wo [holograms gerendert](hologram-stability.md#hologram-render-distances)werden.
2. **Vermeiden Sie eine virtuelle Verschiebung, die sich nicht auf die tatsächliche Kopfbewegung** Vermeiden Sie das Verschieben der Kamera auf eine Weise, die für die tatsächliche Bewegung des Benutzers nicht repräsentativ ist. Wenn Ihre APP den Benutzer durch eine Szene verschieben muss, machen Sie die Bewegung vorhersagbar, minimieren Sie die Beschleunigung, und lassen Sie den Benutzer die Bewegung steuern.
3. **Befolgen Sie die Richtlinien für die – Hologramm-Qualität.** Leistungsfähige apps, die den [Leitfaden für die Qualität von holograms](hologram-stability.md) implementieren, werden weniger wahrscheinlich zu Benutzer Unannehmlichkeiten führen.
4. **Sie sollten Hologramme horizontal und nicht vertikal verteilen.** Wenn Sie den Benutzer zwingen, erweiterte Zeiträume für die Suche nach oben oder unten zu verbringen, kann dies zu Ermüdung im Nacken führen.

## <a name="input"></a>Eingabe

### <a name="gaze-and-gestures"></a>Blick und Gesten

Der [Blick](gaze.md) ist eine grundlegende Form der Eingabe auf hololens, die es Benutzern ermöglichen, holograms und die Umgebung zu Zielen. Basierend auf der Cursorposition können Sie visuell sehen, wohin Ihr Blick ausgerichtet ist. Es ist üblich, den Cursor Cursor einem Maus Cursor zuzuordnen.

[Gesten](gestures.md) sind die Interaktion mit holograms, wie z. b. mit einem Mausklick. In den meisten Fällen sind die Maus-und Berührungs Verhalten identisch, aber es ist wichtig, zu verstehen und zu überprüfen, wann Sie sich unterscheiden.

**Überprüfen Sie, ob Ihre APP über ein anderes Verhalten mit Maus und Fingereingabe verfügt.** Dadurch werden Inkonsistenzen und Hilfe bei Entwurfsentscheidungen identifiziert, um die Benutzeroberflächen für Benutzer natürlicher zu gestalten. Beispielsweise wird eine Aktion ausgelöst, die auf Hover basiert.

> [!NOTE]
> Weitere Anleitungen sind für hololens 2 in [Kürze](index.md#news-and-notes)verfügbar.

### <a name="custom-voice-commands"></a>Benutzerdefinierte Sprachbefehle

Die [Spracheingabe](voice-input.md) ist eine natürliche Form der Interaktion. Abhängig von der Auswahl der Befehle und ihrer Offenlegung kann die Benutzer Darstellung entweder magisch oder verwirrend sein. Als Regel sollten Sie keine System Sprachbefehle wie "Select" oder "Hey Cortana" als benutzerdefinierte Befehle verwenden. Hier sind einige Punkte zu beachten:
1. **Vermeiden Sie die Verwendung von Befehlen, die ähnlich klingen.** Dies kann möglicherweise den falschen Befehl auslöst.
2. **Wählen Sie nach Möglichkeit phonetisch Rich Words aus.** Dadurch werden falsche Aktivierungen minimiert und/oder vermieden.

### <a name="peripherals"></a>Peripheriegeräte

Benutzer können über [Peripherie](hardware-accessories.md)Geräte mit Ihrer APP interagieren. Apps müssen nichts Besonderes tun, um diese Funktion nutzen zu können. es gibt jedoch einige Dinge, die überprüft werden müssen.
1. **Überprüfen Sie benutzerdefinierte Interaktionen.** Dinge wie benutzerdefinierte Tastenkombinationen für Ihre APP.
2. **Überprüfen der Umstellung von Eingabetypen** Es wird versucht, mehrere Eingabemethoden zu verwenden, um eine Aufgabe (z. b. sprach-, Gesten-, Maus-und Tastatureingaben) im gleichen Szenario abzuschließen.

## <a name="system-integration"></a>Systemintegration

### <a name="battery"></a>Akku

Testen Sie Ihre Anwendung, ohne dass eine Stromquelle verbunden ist, um zu verstehen, wie schnell der Akku abläuft. Mithilfe von Power LED-Messungen können Sie den Akku Status leicht nachvollziehen. 

![LED-Zustände, die die Akkuleistung angeben](images/batterypowerledindication-500px.png)<br>

*LED-Zustände, die die Akkuleistung angeben*

### <a name="power-state-transitions"></a>Energie Zustandsübergänge

Überprüfen Sie, ob die wichtigsten Szenarien beim Übergang zwischen den Energiezuständen erwartungsgemäß funktionieren. Beispielsweise verbleibt die Anwendung an ihrer ursprünglichen Position? Behält sie seinen Status ordnungsgemäß bei? Funktioniert Sie weiterhin erwartungsgemäß?
1. **Fortsetzung/fortsetzen.** Um in den Standbymodus zu wechseln, können Sie den Netzschalter sofort drücken und freigeben. Das Gerät wird nach 3 Minuten Inaktivität auch automatisch in den Standbymodus versetzt. Um den Standbymodus fortzusetzen, können Sie den Netzschalter sofort drücken und freigeben. Das Gerät wird auch dann fortgesetzt, wenn Sie eine Verbindung mit einer Stromquelle herstellen oder die Verbindung trennen.
2. **Herunterfahren/neu starten.** Zum Herunterfahren halten Sie den Netzschalter fortlaufend für 6 Sekunden gedrückt. Um neu zu starten, klicken Sie auf den Schaltflächen Strom

### <a name="multi-app-scenarios"></a>Szenarien mit mehreren apps

Überprüfen Sie die Kernfunktionen der APP beim Wechseln zwischen apps, insbesondere, wenn Sie eine Hintergrundaufgabe implementiert haben. Beim Kopieren/Einfügen und der Integration von Cortana sollten Sie ggf. auch überprüfen.

## <a name="telemetry"></a>Telemetrie

Verwenden Sie Telemetrie und Analysen, um Sie zu begleiten. Durch die Integration von Analytics in Ihre APP erhalten Sie Einblicke in Ihre APP von ihren Beta-Testern und Endbenutzern. Diese Daten können verwendet werden, um die APP vor der Übermittlung an den Store und zukünftige Updates zu optimieren. Es gibt viele Analytics-Optionen. Wenn Sie nicht sicher sind, wo Sie beginnen sollen, sehen Sie sich die [App Insights](https://www.visualstudio.com/products/application-insights-vs.aspx)an.

Zu berücksichtigende Fragen:
1. Wie verwenden Benutzer den Speicherplatz?
2. Wie kann die APP Objekte in der Welt platzieren? können Sie Probleme erkennen?
3. Wie viel Zeit verbringen Sie in verschiedenen Phasen der Anwendung?
4. Wie viel Zeit verbringen Sie in der APP?
5. Was sind die häufigsten Verwendungs Pfade, die die Benutzer versuchen?
6. Treten Benutzer unerwartete Zustände und/oder Fehler auf?

## <a name="emulator-and-simulated-input"></a>Emulator und simulierte Eingabe

Der [hololens-Emulator](using-the-hololens-emulator.md) ist eine hervorragend Möglichkeit, ihre Holographic-App mit einer Vielzahl von simulierten Benutzer Merkmalen und Leerzeichen effizient zu testen. Im folgenden finden Sie einige Vorschläge für die effektive Verwendung des Emulators zum Testen Ihrer APP:
1. **Verwenden Sie die virtuellen Räume des Emulators, um die Tests zu erweitern.** Der Emulator verfügt über eine Reihe virtueller Räume, die Sie zum Testen Ihrer APP in noch mehr Umgebungen verwenden können.
2. **Verwenden Sie den Emulator, um Ihre APP aus allen Winkeln zu betrachten.** Mit den Schlüsseln PageUp/pagedn wird der simulierte Benutzer größer oder kürzer.
3. **Testen Sie Ihre APP mit einem echten hololens.** Der hololens-Emulator ist ein großartiges Tool, das Ihnen hilft, eine APP schnell zu durchlaufen und neue Fehler abzufangen. Sie sollten sich jedoch vor der Übermittlung an den Windows Store auch auf einen physischen hololens testen. Dies ist wichtig, um sicherzustellen, dass die Leistung und die Leistung auf echter Hardware groß sind.

## <a name="automated-testing-with-perception-simulation"></a>Automatisierte Tests mit der Wahrnehmungs Simulation

Einige App-Entwickler möchten möglicherweise das Testen Ihrer Apps automatisieren. Über einfache Komponententests hinaus können Sie den [Wahrnehmungs Simulations](perception-simulation.md) Stapel in hololens verwenden, um die Benutzer-und Welt Eingaben für Ihre APP zu automatisieren. Die Wahrnehmungs Simulations-API kann simulierte Eingaben an den hololens-Emulator oder an physische hololens senden.

## <a name="windows-app-certification-kit"></a>Zertifizierungskit für Windows-Apps

Damit Ihre APP die beste Chance erhält, [im Windows Store veröffentlicht](submitting-an-app-to-the-microsoft-store.md)zu werden, überprüfen und testen Sie Sie lokal, bevor Sie Sie zur Zertifizierung einreichen. Wenn Ihre APP auf die Windows. Holographic-Gerätefamilie abzielt, führt das [zertifizierungskit für Windows-apps](https://msdn.microsoft.com/library/windows/apps/xaml/mt186449.aspx) nur lokale statische Analyse Tests auf Ihrem PC aus. Auf den hololens werden keine Tests ausgeführt.

## <a name="see-also"></a>Siehe auch
* [Übermitteln einer APP an den Windows Store](submitting-an-app-to-the-microsoft-store.md)
