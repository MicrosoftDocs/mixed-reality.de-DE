---
title: Hinzufügen der benutzerdefinierte Startseite Umgebungen
description: Zusätzlich zu den home Windows Mixed Reality-Umgebungen, die wir bereitstellen, können Sie sich beim Erstellen und verwenden Ihren eigenen experimentieren.
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, virtuelle Realität, VR, MR, Home, benutzerdefinierte Umgebungen, Orte, Cliff Haus, Skyloft, Benutzer erstellen
ms.openlocfilehash: ef140efd88aa0d3329ae2aa7e5b202c3bfe77c0a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593233"
---
# <a name="add-custom-home-environments"></a>Hinzufügen der benutzerdefinierte Startseite Umgebungen

>[!NOTE]
>Dies ist ein experimentelles Feature. Probieren sie es und Spaß dabei jedoch nicht überraschen, wenn alles, was Recht nicht wie erwartet funktioniert. Wir bewerten die Lebensfähigkeit von dieser Funktion und das Interesse an ihn verwenden, also Bitte teilen Sie uns über Ihre Erfahrung (und alle Fehler, die Sie gefunden haben) in der [Entwicklerforen](https://forums.hololens.com/categories/custom-home-environments).

Beginnend mit der [Windows 10 April 2018 aktualisieren](#release-notes-april-2018.md), wir haben ein experimentelles Feature, mit dem Sie die Auswahl stellen (im Startmenü) für die Verwendung als eine angepasste Umgebung hinzufügen kann aktiviert die [Windows Mixed Reality home](#navigating-the-windows-mixed-reality-home.md). Windows Mixed Reality verfügt über zwei standardumgebungen, Cliff House "und" Skyloft, die Sie als Ihre Startseite auswählen können. Eine angepasste Umgebung erstellen, können Sie diese Liste mit Ihren eigenen Kreationen zu erweitern. Dies zur Verfügung in einem frühen Zustand zu relevanten schaffenden und Entwicklern ausgewertet werden, finden, welche Arten von Bereichen erstellen und zu verstehen, wie Sie mit anderen Erstellungstools arbeiten.

Bei Verwendung eine benutzerdefinierte Umgebung sehen Sie diese Teleporting funktioniert die Interaktion mit apps, und platzieren Hologramme wie in der Cliff House und Skyloft. Sie können das Web in einer Landschaft Fantasy durchsuchen oder eine futuristischen Stadt mit Hologramme – die Möglichkeiten sind grenzenlos!

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Feature</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td> Benutzerdefinierte Startseite Umgebungen</td><td style="text-align: center;"></td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="trying-a-sample-environment"></a>Versuchen eine beispielumgebung

Wir haben eine beispielumgebung erstellt, die einige der kreative Ansätze der benutzerdefinierten Startseite Umgebungen anzeigt. Um es auszuprobieren, gehen Sie wie folgt vor:
1. [Unsere Fantasie Insel beispielumgebung herunterladen](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (Links zu einer selbstextrahierenden ausführbaren Datei).

    ![Beispielumgebung Fantasy-Insel](images/FantasyLand.jpg)<br>
    *Beispielumgebung Fantasy-Insel*<br>

2. Führen Sie die **Fantasy_Island.exe** Datei, die Sie gerade heruntergeladen haben.

    > [!NOTE]
    > Wenn möchten, führen Sie eine .exe-Datei aus dem Web (wie dieses hier) heruntergeladen werden, können Sie ein Popup mit "Windows-Ihr PC geschützt" auftreten. Wählen Sie zum Ausführen von Fantasy_Island.exe in diesem Popupfenster **Informationen** und dann **trotzdem ausführen**. Diese sicherheitseinstellung dient zum Schutz von Herunterladen von Dateien, die möglicherweise Sie nicht vertrauen, also möchten wählen Sie diese Option nur, wenn Sie die Quelle der Datei vertrauenswürdig.

3. Open **Datei-Explorer** und navigieren Sie zu dem Ordner "Umgebungen" durch Einfügen von in der Adressleiste die folgende: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`.
4. Kopieren Sie die beispielumgebung, die Sie heruntergeladen haben, in diesen Ordner.
5. Starten Sie neu **Mixed Reality-Portal**. Dadurch wird die Liste der Umgebungen, in der Auswahl stellen aktualisiert.
6. Stellen Sie auf Ihre Kopfhörer. Sobald Sie zu Hause haben, öffnen Sie die **Menü "Start"** mithilfe der Windows Ihres Controllers Schaltfläche.
7. Wählen Sie die **stellen** Symbol oberhalb der Liste der angehefteten apps auf einer privaten Umgebung.
8. Finden Sie die Umgebung Fantasy Insel, die Sie in der Liste der Orte heruntergeladen. Wählen Sie **Fantasy Insel** die neue Umgebung für das benutzerdefinierte Startseite eingeben.

## <a name="creating-your-own-custom-environment"></a>Erstellen einer eigenen benutzerdefinierten Umgebung

Zusätzlich zur Verwendung unserer beispielumgebungen, können Sie Ihre eigenen benutzerdefinierten Umgebungen, die mit Ihrer bevorzugten 3D Software bearbeiten exportieren. 

### <a name="modeling-guidelines"></a>Modellieren von Richtlinien

Beachten Sie beim Modellieren Ihrer Umgebung die folgenden Empfehlungen. Dadurch wird der Benutzer erzeugt in der richtigen Ausrichtung in einer Welt believably Größe sichergestellt:

1. Benutzer werden Ihr Standort gewünschten erzeugen, um den Ursprung 0,0,0). dies der Fall ist zentriert erzeugen.
2. Arbeitseinheiten sollte mit Werten festgelegt werden, damit Ressourcen bedarfsorientiert Welt erstellt werden können.
3. Die Achse auf sollte auf "Y" festgelegt werden.
4. Das Medienobjekt sollte "forward" auf der positiven Z-Achse auftreten.
5. Alle Gitter müssen nicht kombiniert werden, aber es wird empfohlen, wenn Sie Geräte mit ressourcenbeschränkung verwenden möchten.

### <a name="exporting-your-environment"></a>Exportieren Ihre Umgebung

Windows Mixed Reality basiert auf binärer GlTF (.glb) als das Asset-übermittlungsformat für Umgebungen. GlTF ist eine lizenzgebührenfreie kostenlose offener Standard für 3D medienobjektübermittlung, die von der Gruppe "Khronos" verwaltet wird. GlTF als Branchenstandard für interoperable 3D-Inhalt weiterentwickelt, daher werden Microsoft Unterstützung für das Format für Windows-apps und Umgebungen.

Der erste Schritt beim Exportieren von Ressourcen als benutzerdefinierte Startseite Umgebungen verwendet werden soll, wird ein Modell GlTF 2.0 generiert. Die Arbeitsgruppe GlTF verwaltet eine [Liste der unterstützten metadatenexport- und Konverter](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) zum Erstellen eines Modells GlTF 2.0. Klicken Sie zum Einstieg verwenden Sie eines der Programme auf dieser Seite aufgeführten erstellen und exportieren ein Modell GlTF 2.0, oder konvertieren Sie ein vorhandenes Modell mit einer der unterstützten Konverter.

Darüber hinaus sehen Sie sich [in diesem Artikel hilfreiche](https://www.khronos.org/blog/art-pipeline-for-gltf) die bietet eine Übersicht über einen Workflow Kunst, zum Exportieren von GlTF Modelle von Blender und 3DS Max direkt. 

### <a name="environment-limits"></a>Grenzwerte der Umgebung

Alle Umgebungen müssen < 256 MB sein. Umgebungen, die größer als 256 MB können nicht geladen werden und mit nur den Zusammenhang mit des Benutzers Skybox ein Fallback auf eine leere Welt. Bedenken dieser dateigrößenbeschränkung beim Ihre Modelle zu erstellen. Darüber hinaus, wenn Sie beabsichtigen, Ihrer Umgebung mithilfe der WindowsMRAssetConverter, wie im folgenden beschrieben optimieren, darüber im Klaren sein, dass die Texturgröße erhöht wird, wie der Abfrageoptimierer Texturen, die eine größere Dateigröße erstellt, jedoch schneller geladen. 

### <a name="optimizing-your-environment"></a>Optimieren der Umgebung

Windows Mixed Reality unterstützt eine Reihe von optionalen Optimierungen, die die Ladezeit von Ihren Umgebungen erheblich senken. Dies kann besonders für Umgebungen mit vielen Texturen, wichtig sein, wie manchmal tritt ein Timeout während des Ladens. Im Allgemeinen empfehlen wir diesen Schritt für alle Objekte, jedoch in kleineren Umgebungen mit wenigen oder mit geringer Auflösung Texturen nicht immer erforderlich es. 

Um diesen Prozess zu vereinfachen, haben wir die [Windows Mixed Reality Asset-Konverter (verfügbar auf GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases) Ihre Optimierungen ausführen. Dieses Tool verwendet eine Reihe von Dienstprogrammen, die im Microsoft GlTF Toolkit verfügbar sind, alle standard 2.0 GlTF oder .glb zu optimieren, indem eine zusätzliche Textur Packen von Metriken, die Komprimierung und Auflösung formatverkleinerung. 

Der Konverter unterstützt derzeit eine Anzahl von Flags, die das genaue Verhalten der Optimierungen zu optimieren. Es wird empfohlen, mit der folgenden Flags für optimale Ergebnisse:

Flag|Empfohlene Werte.|Beschreibung
---|---|---
– max-Textur-Größe|1024 oder 2048| Optimieren diese Option, um die Verbesserung der Qualität der Texturen ändern, Standardwert ist 512 x 512. Beachten Sie, dass ein größerer Wert die Größe der Umgebung erheblich beeinträchtigen wird also Bedenken Sie den Grenzwert von 256 mb
– min-version|1803|Eine angepasste Umgebung werden nur für Versionen von Windows unterstützt > = Version 1803. Dieses Flag Texturen für ältere Versionen entfernt und reduzieren Sie die Dateigröße des endgültigen Assets

Zum Beispiel:

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a>Testen Ihre Umgebung

Sobald Sie Ihre endgültige .glb Umgebung haben können Sie dies zu testen, in den Kopfhörer. Starten Sie in Schritt 2 der ["Versuchen eine beispielumgebung"](#trying-a-sample-environment) Abschnitt aus, um Ihrer benutzerdefinierten Umgebung als der gemischte Realität home verwenden. 

## <a name="feedback"></a>Feedback senden

Während wir dieses experimentelle Feature bewerten möchten, wir erfahren, wie Sie eine angepasste Umgebung, Fehlern, die auftreten können, verwenden, möchten, und wie Sie die Funktion. Geben Sie alle Feedback zum Erstellen und Verwenden von benutzerdefinierten private Umgebungen, in der [Entwicklerforen](https://forums.hololens.com/categories/custom-home-environments).

## <a name="troubleshooting-and-tips"></a>Problembehandlung und Tipps

### <a name="how-do-i-change-the-name-of-the-environment"></a>Wie ändere ich den Namen der Umgebung?

Der Dateiname im Ordner "Umgebungen" wird in der Auswahl Stellen verwendet werden. So ändern Sie den Namen Ihrer Umgebung einfach Umbenennen der Umgebung Dateinamen an, und wiederholen Sie die Mixed Reality-Portal.

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a>Wie entferne ich eine angepasste Umgebung aus meiner Auswahl stellen?

Um eine benutzerdefinierte Umgebung zu entfernen, öffnen Sie den Ordner "Umgebungen" auf Ihrem PC (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`) und löschen Sie die Umgebung. Nachdem Sie die Mixed Reality-Portal neu starten, wird diese Umgebung nicht mehr in der Auswahl Stellen angezeigt. 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a>Wie standardmäßig ich meine bevorzugte benutzerdefinierte Umgebung?

Sie können derzeit nicht die Standard-Umgebung ändern. Jedes Mal, die Sie Mixed Reality-Portal neu starten, werden Sie in der Umgebung Cliff House zurückgegeben. 

### <a name="i-spawn-into-a-blank-space"></a>Ich erzeugen, in eine leere Fläche

Windows Mixed Reality [unterstützt nicht die Umgebungen, in denen 256 mb nicht überschreiten](#environment-limits). Wenn Sie eine Umgebung diesen Grenzwert überschreitet, gelangen Sie in das Feld leer Sky mit kein Modell.

### <a name="it-takes-a-long-time-to-load-my-environment"></a>Es nimmt viel Zeit in meiner Umgebung laden

Sie können optionale Optimierungen für Ihre Umgebung zu vereinfachen schneller geladen, hinzufügen. Finden Sie unter ["Optimieren der Umgebung"](#optimizing-your-environment) Details.

### <a name="the-scale-of-my-environment-is-incorrect"></a>Die Skalierung der Umgebung ist falsch

Windows Mixed Reality übersetzt GlTF Einheiten 1 Meter Umkreis um beim Laden von Umgebungen. Wenn ein unerwarteter Skalierung der Umgebung geladen wird, überprüfen Sie Ihre Ausführer aus, um sicherzustellen, dass Sie auf einer Skala von 1 Meter Umkreis um modellieren. 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a>Das Erstellen eines Prozesses in meiner Umgebung wurde falsch angegeben.

Der Standardspeicherort für das Erstellen eines Prozesses befindet sich unter 0,0,0 in der Umgebung. Die nicht derzeit möglich, diesem Speicherort anpassen, damit den Spawn Punkt, Sie ändern müssen durch den Export Ihrer Umgebung mit dem Ursprung positioniert, an dem Punkt der gewünschten erzeugen.

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a>Das Audio klingt nicht in der Umgebung richtig.

Bei der Erstellung Ihrer benutzerdefinierten Umgebung werden sie eine Simulation der Akustik Rendering verwenden, die nicht den physischen Speicherplatz übereinstimmen, die, den Sie erstellt haben. Sound die falschen Anweisungen stammen dürfen und mag dumpf. 

## <a name="see-also"></a>Siehe auch
* [Navigieren in der Windows Mixed Reality-Startseite](#navigating-the-windows-mixed-reality-home.md)
* [Windows Mixed Reality-Asset-Konverter (auf GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases)

