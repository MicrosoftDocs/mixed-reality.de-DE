---
title: Testen Ihrer app für HoloLens
description: Anleitungen und Empfehlungen zum Testen Ihrer app HoloLens
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, testing
ms.openlocfilehash: 35e8eff230cdcd719952ad2633ec610c9a9a26a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594216"
---
# <a name="testing-your-app-on-hololens"></a>Testen Ihrer app für HoloLens

HoloLens-testanwendungen sind sehr ähnlich ist, um Windows-Anwendungen zu testen. (Funktionen, Interoperabilität, Leistung, Sicherheit, Zuverlässigkeit, usw.), sollten alle üblichen Bereiche berücksichtigt werden. Es gibt jedoch einige Bereiche, die erfordern besondere Behandlung oder Aufmerksamkeit auf Details, die nicht in der Regel im PC oder Phone-apps beachtet werden. Holographic apps müssen reibungslos in eine Vielzahl von Umgebungen ausgeführt. Sie müssen auch die Leistung und Komfort jederzeit beizubehalten. Einen Leitfaden zum Testen dieser Bereiche wird in diesem Thema beschrieben.

## <a name="performance"></a>Leistung

Holographic apps müssen reibungslos in eine Vielzahl von Umgebungen ausgeführt. Sie müssen auch die Leistung und Komfort jederzeit beizubehalten. Leistung ist so wichtig, die benutzererfahrung mit einer Holographic app haben wir eine gesamte Thema für sie. Stellen Sie sicher, dass Sie lesen und befolgen Sie die [Leistung für Mixed Reality](understanding-performance-for-mixed-reality.md)

## <a name="testing-3d-in-3d"></a>Testen 3D in 3D
1. **Testen Sie Ihre app in anderen Leerzeichen wie möglich.** Versuchen Sie es im big-Räume, kleine Räume, Badezimmer, Keller-, Schlafzimmer, Niederlassungen usw. Berücksichtigen Sie auch Aspekt Zimmern aufbewahrt und mit nicht-Standardfunktionen wie nicht vertikale Wände, gekrümmte Wände, nicht-Horizontal Obergrenzen. Funktioniert gut, wenn zwischen Räume Übergang, Etagen, Fluren oder Bodens durcharbeiten?
2. **Testen Sie Ihre app in verschiedenen Lichtverhältnissen.** Sie ordnungsgemäß auf verschiedenen umgebungsbedingungen wie Beleuchtung, Schwarz Oberflächen, transparente/reflektierenden Oberflächen wie Spiegel, Glaswände usw. reagieren.
3. **Testen Sie Ihre app in verschiedenen Motion-Bedingungen.** Auf Gerät abgelegt, und versuchen Sie es Ihrer Szenarien in verschiedenen Zuständen der Bewegung. Reagiert er ordnungsgemäß zum anderen verschieben oder im stabilen Zustand?
4. **Testen Sie, wie Ihre app aus verschiedenen Blickwinkeln funktioniert.** Wenn Sie ein Hologramm Welt gesperrt haben, was geschieht, wenn Ihre Benutzer dahinter führt? Was geschieht, wenn etwas zwischen dem Benutzer und dem – Hologramm stammt? Was geschieht, wenn der Benutzer untersucht die Hologramm von oben oder unten?
5. **Verwenden Sie die Hinweise für räumliche und audio.** Stellen Sie sicher, dass Ihre app diese verwendet, um zu verhindern, dass den Benutzer den Überblick zu verlieren.
6. **Testen Sie Ihre app auf unterschiedlichen Ebenen der Umgebungsgeräusch.** Wenn Sie Sprachbefehle implementiert haben, versuchen Sie sie mit wechselnden Berechtigungsebenen Umgebungsgeräusch aufrufen.
7. **Testen Sie Ihre app sitzen und ständigen**. Stellen Sie sicher, zum Testen von Sitzplätze und ständigen Positionen.
8. **Testen Sie Ihre app aus verschiedenen Abstände**. Können Elemente der Benutzeroberfläche werden gelesen und interagiert mit von weit entfernt? Verfügt Ihre app React für Benutzer, die erste zu schließen, um Ihre Hologramme?
9. **Testen Sie Ihre app für die allgemeine app-Leiste Interaktionen**. Alle app-Kacheln und Direct2D-universal-apps verfügen über eine [app-Leiste](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) , mit der Sie steuern, wie die app in der gemischten Welt positioniert wird. Stellen Sie sicher auf die Schaltfläche Entfernen Ihrer app Prozess ordnungsgemäß beendet wird, dass die Schaltfläche "zurück" im Rahmen Ihrer Direct2D-universal-app unterstützt wird. Sollten Sie versuchsweise hoch- und wie Sie Ihre app in [anpassen Modus](navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) während er aktiv ist, und zwar eine angehaltene app-Kachel.

### <a name="environmental-test-matrix"></a>Environmental Testmatrix

![Umgebung Testmatrix für die Entwicklung für HoloLens-Apps](images/environment-matrix-600px.png)

## <a name="comfort"></a>Komfort
1. **Schneiden Sie Ebenen.** Werden auf den Speicherort basiert auf aufmerksamer [Hologramme werden gerendert](hologram-stability.md#hologram-render-distances).
2. **Vermeiden Sie die virtuellen verschieben, die nicht mit tatsächlichen Bewegungen.** Verhindern, dass die Kamera auf eine Weise, die nicht repräsentativ für die tatsächliche Bewegung des Benutzers ist. Wenn Ihre app den Benutzer über eine Szene verschieben benötigt, stellen Sie die Bewegung vorhersagbaren, minimieren Sie die Beschleunigung und kann der Benutzer, der die Bewegung zu steuern.
3. **Befolgen Sie die Richtlinien – Hologramm Qualität.** Leistungsstarke apps, die implementieren die [– Hologramm Qualität Anleitungen](hologram-stability.md) weniger wahrscheinlich zu Benutzer angefasst werden.
4. **Verteilen Sie Hologramme horizontal statt vertikal.** Erzwingen den Benutzer ausgeben längeren Zeitraum nachschlagen oder nach unten zu Ermüdung in HALs führen kann.

## <a name="input"></a>Input

### <a name="gaze-and-gestures"></a>Blicke und Gesten

[Bestaunen](gaze.md) ist eine einfache Form der Eingabe für HoloLens, mit denen Benutzer Hologramme und die Umgebung darstellen können. Sie können visuell basierend auf die Position des sehen, in dem Ihre Blicke ausgerichtet ist. Es ist üblich, ein Mauscursor Blicke Cursor zugeordnet werden soll.

[Bewegungen](gestures.md) sind die Interaktion mit Hologramme, z. B. ein Mausklick. In den meisten Fällen die Maus und Toucheingabe Verhaltensweisen sind identisch, aber es ist wichtig zu verstehen und zu überprüfen, wenn sie sich unterscheiden.

**Überprüfen Sie, wenn Ihre app per Touch mit Maus und ein anderes Verhalten aufweist.** Inkonsistenzen zu identifizieren werden und Hilfe bei entwurfsentscheidungen, die Erfahrung für Benutzer natürlicher zu machen. Z. B. Auslösen einer Aktion basierend auf den gezeigt wird.

> [!NOTE]
> Weitere Anleitungen, die speziell für HoloLens 2 [bald](index.md#news-and-notes).

### <a name="custom-voice-commands"></a>Befehle für benutzerdefinierte Sprachnachrichten

[Voice-Eingabe](voice-input.md) ist eine natürliche Form der Interaktion. Die benutzererfahrung kann magische oder abhängig von Ihrer Auswahl von Befehlen und wie Sie machen verwirrend sein. Als Faustregel gilt sollten Sie Sprachbefehle System, z. B. "Select" oder "Hey Cortana" nicht als benutzerdefinierte Befehle verwenden. Hier sind einige Punkte zu berücksichtigen:
1. **Verwenden Sie Befehle, die ähnlich klingen.** Dadurch kann möglicherweise den falschen Befehl ausgelöst.
2. **Wählen Sie die phonetisch umfangreiche Wörter, nach Möglichkeit.** Dies wird minimieren bzw. "false" Aktivierungen vermeiden.

### <a name="peripherals"></a>Peripheriegeräte

Benutzer können mit Ihrer App über interagieren [Peripheriegeräte](hardware-accessories.md). Apps müssen nicht extra um profitieren Sie von dieser Funktion, und es gibt jedoch einige Punkte zu überprüfen.
1. **Überprüfen Sie die benutzerdefinierte Aktivitäten.** Dinge wie benutzerdefinierte Tastenkombinationen für Ihre app.
2. **Überprüfen Sie die Eingabetypen wechseln.** Versucht, mehrere Eingabemethoden zum Abschluss einer Aufgabe, wie z. B. Sprach-, Geste, Maus und Tastatur in das gleiche Szenario verwenden.

## <a name="system-integration"></a>System-Integration

### <a name="battery"></a>Akku

Testen Sie Ihre Anwendung, ohne eine Stromquelle angeschlossen, um zu verstehen, wie schnell den Akku leer saugt. Eine kann problemlos den Status des Akkus verstehen, anhand Betriebsanzeige-LED Messwerten. ![LED-Statusanzeigen, die angeben, Akku](images/batterypowerledindication-500px.png)

### <a name="power-state-transitions"></a>Power-Statusübergänge

Überprüfen Sie wichtige Szenarien arbeiten, wie erwartet, wenn sich im Übergang zwischen Energiezustände. Beispielsweise bleibt die Anwendung in seiner ursprünglichen Position? Beibehalten es seinen Status richtig? Weiterhin er wie erwartet?
1. **Standby / fortsetzen.** Um in den Standbymodus, kann eine drücken und lassen den Netzschalter sofort. Das Gerät wird Standby auch automatisch nach 3 Minuten der Inaktivität versetzt werden. Zum Fortsetzen aus dem Standbymodus kann eine drücken und lassen den Netzschalter sofort. Das Gerät wird auch fortgesetzt, wenn Sie eine Verbindung herstellen oder einer Stromquelle trennen.
2. **Herunterfahren / neu starten.** Zum Herunterfahren halten Sie den Netzschalter kontinuierlich für 6 Sekunden. Drücken Sie den Netzschalter betätigen, um neu zu starten.

### <a name="multi-app-scenarios"></a>Multi-App-Szenarien

Überprüfen Sie Core-app-Funktionalität beim Wechseln zwischen apps, insbesondere dann, wenn Sie eine Hintergrundtask implementiert haben. Kopieren und einfügen und Cortana-Integration sind ebenfalls prüfen, ob, sofern zutreffend.

## <a name="telemetry"></a>Telemetrie

Verwenden Sie die Telemetrie und Analysen, die Anweisungen enthalten. Integrieren Analysen in Ihre app hilft Ihnen Einblicke in Ihre app aus Ihren Betatestern und Endbenutzer zu erhalten. Diese Daten dienen zum Optimieren Ihrer app vor der Übermittlung an den Store und für zukünftige Updates. Es gibt es viele Analytics-Optionen. Wenn Sie nicht, wo Sie anfangen kennen, sehen Sie sich [App Insights](https://www.visualstudio.com/products/application-insights-vs.aspx).

Fragen zu berücksichtigen:
1. Wie werden Benutzer, den Speicherplatz nutzen?
2. Wie die app ist Platzieren von Objekten in der Welt – können Sie Probleme erkennen?
3. Wie viel Zeit verbringen sie auf die verschiedenen Phasen der Anwendung?
4. Wie viel Zeit verbringen sie in der app?
5. Gibt die am häufigsten verwendeten Nutzung Pfade der Benutzer versuchen?
6. Werden Benutzer werden unerwartete Zustände und/oder Fehler erreicht?

## <a name="emulator-and-simulated-input"></a>Emulator und simulierte Eingabe

Die [Emulator für HoloLens](using-the-hololens-emulator.md) ist eine hervorragende Möglichkeit, Ihre Holographic app mit einer Vielzahl von simulierten Benutzer Merkmale und Leerzeichen effizient zu testen. Hier sind einige Vorschläge für die effektive Nutzung des Emulators zum Testen Ihrer app:
1. **Verwenden des Emulators virtuelle Teamräume, erweitern Sie Ihre Tests.** Der Emulator enthält eine Reihe von virtuellen Räumen, mit denen Sie Ihre app in Umgebungen mit noch mehr zu testen.
2. **Verwenden Sie den Emulator, um Ihre app aus allen Winkeln untersuchen.** Die Schlüssel PageUp/PageDn veranlasst den simulierten Benutzer vergrößern oder verkleinern.
3. **Testen Sie Ihre app mit einem echten HoloLens.** Die HoloLens-Emulator ist ein großartiges Tool können Sie schnell auf eine app durchlaufen und neue Fehler abfangen, aber stellen Sie sicher, dass Sie sich auch auf einem physischen HoloLens Testen vor der Übermittlung an den Windows Store. Dies ist wichtig, um sicherzustellen, dass die Leistung und benutzerfreundlichkeit auf echter Hardware.

## <a name="automated-testing-with-perception-simulation"></a>Automatisierte Tests mit Perception Simulation

Einige app-Entwickler möchten automatisierte Tests für ihre Apps. Über einfache Komponententests, können Sie die [Perception Simulation](perception-simulation.md) -Stapels in HoloLens, um menschliche und World Eingabe für Ihre app zu automatisieren. Die Wahrnehmung Simulation-API kann simulierte Eingabe auf den Emulator für HoloLens oder ein physischer HoloLens senden.

## <a name="windows-app-certification-kit"></a>Zertifizierungskit für Windows-Apps

Um Ihrer app wird die beste Chance geben [auf dem Windows Store veröffentlichten](submitting-an-app-to-the-microsoft-store.md), überprüfen und lokal testen, bevor Sie sie zur Zertifizierung einreichen. Wenn Ihre app die Gerätefamilie Windows.Holographic, abzielt. der [Windows App Certification Kit](https://msdn.microsoft.com/library/windows/apps/xaml/mt186449.aspx) werden nur lokale statische Analyse-Tests auf Ihrem PC ausgeführt. Auf Ihre HoloLens werden keine Tests ausgeführt werden.

## <a name="see-also"></a>Siehe auch
* [Übermitteln einer app an den Windows Store](submitting-an-app-to-the-microsoft-store.md)
