---
title: Entwerfen Sie Ihre eigenen immersiven Umgebungen
description: Zusätzlich zu den Windows Mixed Reality-Start Umgebungen, die wir bereitstellen, können Sie mit der Erstellung und Verwendung ihrer eigenen experimentieren.
author: thmignon
ms.author: thmignon
ms.date: 04/30/2018
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Home, Custom Environment, Places, Klippe House, SkyLoft, User, CREATE
ms.openlocfilehash: e133e1438410540592a51f54ed136aecd04c6244
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437079"
---
# <a name="design-your-own-immersive-environments"></a>Entwerfen Sie Ihre eigenen immersiven Umgebungen

>[!NOTE]
>Dies ist ein experimentelles Feature. Probieren Sie es aus, und machen Sie sich damit vertraut, aber es ist nicht verwunderlich, wenn alles wie erwartet funktioniert. Wir evaluieren die Fähigkeit dieses Features und arbeiten daran, Sie zu verwenden. Teilen Sie uns daher ihre Erfahrung (und alle gefundenen Fehler) in den [Entwickler Foren](https://forums.hololens.com/categories/custom-home-environments)mit.

Ab dem [Windows 10 April 2018-Update](release-notes-april-2018.md)haben wir eine experimentelle Funktion aktiviert, mit der Sie der Stellen Auswahl (im Startmenü) benutzerdefinierte Umgebungen hinzufügen können, um Sie als [Windows Mixed Reality Home](navigating-the-windows-mixed-reality-home.md)zu verwenden. Windows Mixed Reality verfügt über zwei Standard Umgebungen, die Sie als Startseite auswählen können. Durch das Erstellen von benutzerdefinierten Umgebungen können Sie diese Liste mit ihren eigenen Schöpfungen erweitern. Wir stellen dies in einem frühen Zustand zur Verfügung, um die Interessen von Creators und Entwicklern zu evaluieren, die Art der von Ihnen erstellten Umgebungen anzuzeigen und zu verstehen, wie Sie mit verschiedenen Authoring Tools arbeiten.

Wenn Sie eine benutzerdefinierte Umgebung verwenden, werden Sie feststellen, dass die teleportierung, die Interaktion mit apps und das Platzieren von holograms so funktioniert, wie es im-und SkyLoft funktioniert. Sie können das Web in einer Fantasy-Landschaft durchsuchen oder einen futuristischen Ort mit holograms ausfüllen. die Möglichkeiten sind unendlich.

## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Feature</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Benutzerdefinierte Heim Umgebungen</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="trying-a-sample-environment"></a>Ausprobieren einer Beispiel Umgebung

Wir haben eine Beispiel Umgebung erstellt, in der einige der kreativen Möglichkeiten von benutzerdefinierten Heim Umgebungen gezeigt werden. Führen Sie die folgenden Schritte aus, um es auszuprobieren:
1. [Laden Sie unsere Beispiel-Fantasy-Inselumgebung herunter](https://download.microsoft.com/download/B/2/5/B25C1AEF-40CD-4B03-A596-4BCA3D33035A/Fantasy_Island.exe) (Link Punkte auf selbst extrahierende ausführbare Datei).

    ![Fantasy-Insel-Beispiel Umgebung](images/FantasyLand.jpg)<br>
    *Beispiel Umgebung der Fantasy-Insel*<br>

2. Führen Sie die soeben heruntergeladene Datei **Fantasy_Island. exe** aus.

    > [!NOTE]
    > Wenn Sie versuchen, eine aus dem Web heruntergeladene EXE-Datei auszuführen (z. b. diese), kann das Popup Fenster "Windows-geschützter PC" angezeigt werden. Um Fantasy_Island. exe in diesem Popup auszuführen, wählen Sie **Weitere Informationen** aus, und **führen**Sie dann trotzdem aus. Diese Sicherheitseinstellung soll Sie vor dem Herunterladen von Dateien schützen, denen Sie nicht vertrauen möchten. Wählen Sie daher diese Option nur aus, wenn Sie der Quelle der Datei vertrauen.

3. Öffnen Sie den **Datei-Explorer** , und navigieren Sie zum Ordner Umgebungen, indem Sie Folgendes in die Adressleiste einfügen: `%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`.
4. Kopieren Sie die Beispiel Umgebung, die Sie in diesen Ordner heruntergeladen haben.
5. Starten Sie **Mixed Reality-Portal**neu. Dadurch wird die Liste der Umgebungen in der Auswahl Orte der Orte aktualisiert.
6. Legen Sie auf Ihrem Headset ab. Wenn Sie sich in der Startseite befinden, öffnen Sie das **Startmenü** mithilfe der Windows-Schaltfläche für den Controller.
7. Wählen Sie das Symbol " **Orte** " oberhalb der Liste der angehefteten Apps aus, um eine Heimumgebung auszuwählen.
8. Sie finden die Fantasie Inselumgebung, die Sie heruntergeladen haben, in der Liste der Orte. Wählen Sie **Fantasie Insel** aus, um Ihre neue benutzerdefinierte Home-Umgebung einzugeben!

## <a name="creating-your-own-custom-environment"></a>Erstellen einer eigenen benutzerdefinierten Umgebung

Zusätzlich zur Verwendung unserer Beispiel Umgebungen können Sie Ihre eigenen benutzerdefinierten Umgebungen mit Ihrer bevorzugten 3D-Bearbeitungssoftware exportieren. 

### <a name="modeling-guidelines"></a>Modellierungs Richtlinien

Beachten Sie beim Modellieren Ihrer Umgebung die folgenden Empfehlungen. Dadurch wird sichergestellt, dass der Benutzer in einer Welt mit der Glaubwürdigkeit in der richtigen Ausrichtung ist:

1. Benutzer werden bei 0, 0 und 0 erstellt, sodass Sie die gewünschte Ausgangsposition um den Ursprung zentrieren können.
2. Arbeitseinheiten sollten auf Meter festgelegt werden, damit Assets weltweit skaliert werden können.
3. Die up-Achse sollte auf "Y" festgelegt werden.
4. Das Medienobjekt sollte für die positive Z-Achse "Vorwärts" stehen.
5. Alle Netzen müssen nicht kombiniert werden, Sie werden jedoch empfohlen, wenn Sie auf Ressourcen beschränkte Geräte abzielen.

### <a name="exporting-your-environment"></a>Exportieren Ihrer Umgebung

Windows Mixed Reality basiert auf binärem gltf (. GLB) als Übermittlungs Format für das Medienobjekt. gltf ist ein kostenloser offener Standard für die 3D-Asset-Bereitstellung, der von der Khronos-Gruppe verwaltet wird. Da sich gltf als Industriestandard für interoperablen 3D-Inhalt entwickelt, unterstützt Microsoft das Format in Windows-apps und-Umgebungen.

Der erste Schritt beim Exportieren von Assets, die als benutzerdefinierte Heimumgebung verwendet werden sollen, ist das Erstellen eines gltf 2,0-Modells. Die Arbeitsgruppe "gltf" verwaltet eine [Liste der unterstützten Export-und Konverter](https://github.com/KhronosGroup/glTF/blob/master/README.md#converters-and-exporters) , um ein gltf 2,0-Modell zu erstellen. Verwenden Sie zum Einstieg eines der auf dieser Seite aufgeführten Programme, um ein gltf 2,0-Modell zu erstellen und zu exportieren, oder konvertieren Sie ein vorhandenes Modell mit einem der unterstützten Konverter.

Lesen Sie außerdem [diesen nützlichen Artikel](https://www.khronos.org/blog/art-pipeline-for-gltf) , der einen Überblick über einen Kunst Workflow zum direkten Exportieren von gltf-Modellen aus Blender und 3ds Max bietet. 

### <a name="environment-limits"></a>Umgebungs Limits

Alle Umgebungen müssen < 256-MB betragen. Umgebungen, die größer als 256 MB sind, können nicht geladen werden und greifen auf eine leere Welt zurück, die nur die standardmäßige Skybox für den Benutzer enthält. Beachten Sie beim Erstellen der Modelle diese Dateigrößen Beschränkung. Wenn Sie eine Optimierung Ihrer Umgebung mithilfe von windowsmrassetconverter planen, wie unten beschrieben, sollten Sie außerdem erkennen, dass die Textur Größe zunimmt, wenn der Optimierer Texturen erstellt, die eine größere Dateigröße aufweisen, aber schneller geladen werden. 

### <a name="optimizing-your-environment"></a>Optimieren der Umgebung

Windows Mixed Reality unterstützt eine Reihe optionaler Optimierungen, die die Ladezeit Ihrer Umgebungen erheblich verringern. Dies kann besonders für Umgebungen mit vielen Texturen von Bedeutung sein, da Sie beim Laden gelegentlich einen Timeout aufweisen werden. Im Allgemeinen empfiehlt es sich, diesen Schritt für alle Ressourcen zu empfehlen, aber kleinere Umgebungen mit wenigen oder mit geringer Auflösung benötigten Texturen sind nicht immer erforderlich. 

Um diesen Prozess zu vereinfachen, haben wir den [Windows Mixed Reality Asset Converter (verfügbar auf GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases) zum Durchführen ihrer Optimierungen erstellt. Dieses Tool verwendet eine Reihe von Hilfsprogrammen, die im Microsoft gltf Toolkit verfügbar sind, um jeden Standard 2,0 gltf oder. GLB durch die Durchführung einer zusätzlichen Textur Komprimierung, Komprimierung und Auflösung nach unten Skalieren zu optimieren. 

Der Konverter unterstützt derzeit eine Reihe von Flags, um das genaue Verhalten der Optimierungen zu optimieren. Wir empfehlen die Ausführung mit den folgenden Flags, um optimale Ergebnisse zu erzielen:

Flag|Empfohlene Werte|Beschreibung
---|---|---
-Max-Textur Größe|1024 oder 2048| Optimieren Sie diese, um die Qualität der Texturen zu verbessern. der Standardwert ist 512 x 512. Beachten Sie, dass sich ein größerer Wert erheblich auf die Dateigröße der Umgebung auswirkt. behalten Sie also den Grenzwert von 256 MB bei.
-Minimale Version|1803|Benutzerdefinierte Umgebungen werden nur für Versionen von Windows > = 1803 unterstützt. Mit diesem Flag werden Texturen für ältere Versionen entfernt und die Dateigröße des endgültigen Assets reduziert.

Zum Beispiel:

```cmd
WindowsMRAssetConverter FileToConvert.gltf -max-texture-size 1024 -min-version 1803
```

### <a name="testing-your-environment"></a>Testen Ihrer Umgebung

Sobald Sie die endgültige. GLB-Umgebung haben, können Sie Sie im Headset testen. Beginnen Sie mit Schritt 2 im Abschnitt ["ausprobieren einer Beispiel Umgebung"](#trying-a-sample-environment) , um Ihre benutzerdefinierte Umgebung als gemischte Reality-Startseite zu verwenden. 

## <a name="feedback"></a>Feedback senden

Während wir diese experimentelle Funktion evaluieren, möchten wir uns mit der Verwendung von benutzerdefinierten Umgebungen, den Fehlern, die auftreten können, und der Art der Funktion vertraut machen. Bitte geben Sie ein beliebiges Feedback zum Erstellen und Verwenden von benutzerdefinierten Heim Umgebungen in den [Entwickler Foren](https://forums.hololens.com/categories/custom-home-environments)frei.

## <a name="troubleshooting-and-tips"></a>Problembehandlung und Tipps

### <a name="how-do-i-change-the-name-of-the-environment"></a>Gewusst wie den Namen der Umgebung ändern?

Der Dateiname im Ordner "Umgebungen" wird in der Auswahl "Orte" verwendet. Um den Namen Ihrer Umgebung zu ändern, benennen Sie einfach den Namen der umgebungsdatei um, und starten Sie dann das Mixed Reality-Portal neu.

### <a name="how-do-i-remove-custom-environments-from-my-places-picker"></a>Gewusst wie benutzerdefinierte Umgebungen aus meiner stellen Auswahl entfernen?

Um eine benutzerdefinierte Umgebung zu entfernen, öffnen Sie den Ordner Umgebungen auf Ihrem PC (`%LOCALAPPDATA%\Packages\EnvironmentsApp_cw5n1h2txyewy\LocalState`), und löschen Sie die Umgebung. Nachdem Sie das Mixed Reality-Portal neu gestartet haben, wird diese Umgebung nicht mehr in der Auswahl der Orte angezeigt. 

### <a name="how-do-i-default-to-my-favorite-custom-environment"></a>Gewusst wie standardmäßig meine bevorzugte benutzerdefinierte Umgebung?

Die Standardumgebung kann derzeit nicht geändert werden. Jedes Mal, wenn Sie das Mixed Reality-Portal neu starten, werden Sie zur Umgebung "Klippe House" zurückkehren. 

### <a name="i-spawn-into-a-blank-space"></a>Ich erstelle einen leeren Bereich

Windows Mixed Reality [unterstützt keine Umgebungen, die mehr als 256 MB](#environment-limits)umfassen. Wenn eine Umgebung diese Beschränkung überschreitet, werden Sie in das leere Feld ohne Modell.

### <a name="it-takes-a-long-time-to-load-my-environment"></a>Das Laden meiner Umgebung dauert sehr lange.

Sie können Ihrer Umgebung optionale Optimierungen hinzufügen, um den Ladevorgang zu beschleunigen. Weitere Informationen finden [Sie unter "Optimieren der Umgebung"](#optimizing-your-environment) .

### <a name="the-scale-of-my-environment-is-incorrect"></a>Die Skala meiner Umgebung ist falsch.

Die gemischte Realität von Windows übersetzt die gltf-Einheiten beim Laden von Umgebungen in 1 Meter. Wenn in Ihrer Umgebung eine unerwartete Skalierung auftritt, überprüfen Sie das Exportprogramm, um sicherzustellen, dass Sie eine Modellierung bei einer Skala von 1 Meter durcharbeiten. 

### <a name="the-spawn-location-in-my-environment-is-incorrect"></a>Der Speicherort in meiner Umgebung ist falsch.

Der standardmäßige Speicherort für die Suche befindet sich in der Umgebung bei 0, 0 und 0. Dieser Speicherort kann nicht angepasst werden. Daher müssen Sie den Ausgangspunkt ändern, indem Sie Ihre Umgebung mit dem Ursprung exportieren, der am gewünschten Ausgangspunkt positioniert ist.

### <a name="the-audio-doesnt-sound-correct-in-the-environment"></a>Die Audiodaten werden in der Umgebung nicht richtig klingen

Wenn Sie Ihre benutzerdefinierte Umgebung erstellen, wird eine Akustik-Rendering-Simulation verwendet, die nicht mit dem von Ihnen erstellten physischen Speicherplatz identisch ist. Sound kann aus den falschen Richtungen stammen und mit einem gedämpften Sound klingen. 

## <a name="see-also"></a>Weitere Informationen:
* [Windows Mixed Reality Asset Converter (auf GitHub)](https://github.com/Microsoft/glTF-Toolkit/releases)

