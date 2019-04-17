---
title: Exportieren und Erstellen von Unity Visual Studio-Projektmappe
description: Dieser Artikel beschreibt das mixed Reality-Projekt aus Unity exportieren, damit können Sie erstellen und in Visual Studio bereitstellen.
author: ''
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Unity und visual Studio exportieren, erstellen und bereitstellen
ms.openlocfilehash: 68c86fdfe0e589536dafe2bf53c7d4e5dffcc514
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596381"
---
# <a name="exporting-and-building-a-unity-visual-studio-solution"></a>Exportieren und Erstellen von Unity Visual Studio-Projektmappe

Wenn Sie nicht über die Systemtastatur in Ihrer Anwendung wünschen, unsere Empfehlung ist die Verwendung *D3D* wie Ihre Anwendung etwas weniger Speicher verwenden und eine etwas schneller starten haben. Wenn Sie die TouchScreenKeyboard-API in Ihrem Projekt verwenden die Systemtastatur verwendet, müssen Sie als exportieren *XAML*.

## <a name="how-to-export-from-unity"></a>Gewusst wie: Exportieren von Unity

![Unity-Buildeinstellungen](images/unitybuildsettings-300px.png)<br>
*Unity-Buildeinstellungen*

1. Wenn Sie Ihr Projekt aus Unity exportieren möchten, öffnen Sie die **Datei** Menü **Buildeinstellungen...**
2. Klicken Sie auf **öffnen Szenen hinzufügen** auf dem Build Ihrer Szene hinzufügen.
3. In der **Buildeinstellungen** Dialogfeld Wählen Sie die folgenden Optionen zum Exportieren von für HoloLens:
   * **Plattform:** *Universelle Windows-Plattform* , und wählen Sie **Plattform wechseln** für Ihre Auswahl wirksam werden.
   * **SDK:** *Universal 10*.
   * **UWP-Buildtyp:** *D3D*.
4. **Optional**: **Unity C# Projekte:** Überprüft.

>[!NOTE]
>Aktivieren des Kontrollkästchens können Sie die folgenden Schritte ausführen:
>* Debuggen Sie Ihre app in Visual Studio remote Debugger.
>* Bearbeiten von Skripts im Unity C# Projekt bei der Verwendung von IntelliSense für WinRT-APIs.

5. Von der **Buildeinstellungen...**  geöffnete Fenster **Playereinstellungen...**
6. Wählen Sie die **Einstellungen für die universelle Windows-Plattform** Registerkarte.
7. Erweitern Sie die **XR-Einstellungen** Gruppe.
8. In der **XR-Einstellungen** aktivieren Sie im Abschnitt der **virtuelle Realität unterstützt** Kontrollkästchen zum Hinzufügen einer neuen **Virtual Reality-Geräte** aus, und vergewissern Sie sich **"Windows Mixed Reality"** wird als ein unterstütztes Gerät aufgeführt.
9. Wechseln Sie zurück zur der **Buildeinstellungen** Dialogfeld.
10. Wählen Sie **erstellen**.
11. Erstellen Sie in der Windows-Explorer-Dialogfeld, das angezeigt wird einen neuen Ordner zum Speichern von Unity-Build-Ausgabe. Im Allgemeinen nennen wir Sie den Ordner "App".
12. Wählen Sie den neu erstellten Ordner aus, und klicken Sie auf **Ordner auswählen**.
13. Wenn Unity erstellen abgeschlossen ist, wird ein Windows-Explorer-Fenster zum Stammverzeichnis Projekts geöffnet. Navigieren Sie in den neu erstellten Ordner.
14. Öffnen Sie die generierte Visual Studio-Projektmappendatei, die in diesem Ordner befinden.

## <a name="when-to-re-export-from-unity"></a>Wenn von Unity erneut exportieren

Überprüfen der "C# Projekten" aktivieren, wenn Ihre app in Unity exportieren Visual Studio-Projektmappe erstellt, enthält alle Ihre Unity-Skriptdateien. Dadurch können Sie Ihre Skripts abarbeiten, ohne Sie neu in Unity exportieren. Wenn Sie Änderungen an Ihrem Projekt, die nur den Inhalt des Skripts ändern, werden nicht vornehmen möchten, müssen Sie jedoch erneut in Unity exportieren. Sind einige Beispiele für die Häufigkeit, mit die Sie erneut in Unity exportieren möchten:
* Sie hinzufügen oder Entfernen von datenassets in der Registerkarte "Projekt".
* Sie ändern einen beliebigen Wert in der Registerkarte "Inspector".
* Sie hinzufügen oder Entfernen von Objekten aus der Registerkarte "Hierarchie".
* Sie ändern, dass alle Einstellungen der Unity-Projekt

## <a name="building-and-deploying-a-unity-visual-studio-solution"></a>Erstellen und Bereitstellen von Unity Visual Studio-Projektmappe

Die restlichen erstellen und Bereitstellen von apps erfolgt im [Visual Studio](using-visual-studio.md). Sie müssen eine Unity-Buildkonfiguration angeben. Konventionen zur Namensgebung von Unity können davon unterscheiden, was Sie in der Regel in Visual Studio kennen:

|  Konfiguration  |  Erläuterung | 
|----------|----------|
|  Debugging  |  Alle Optimierungen deaktiviert und der Profiler aktiviert ist. Zum Debuggen von Skripts verwendet. | 
|  Master  |  Alle Optimierungen sind aktiviert, und der Profiler ist deaktiviert. Verwendet, um die apps an den Store übermitteln. | 
|  Version  |  Alle Optimierungen sind aktiviert, und der Profiler aktiviert ist. Zum Auswerten der Leistung der app verwendet. | 

Beachten Sie, dass die obige Liste eine Teilmenge der gängigen Trigger ist, die Visual Studio-Projekt generiert werden müssen verursachen. Bearbeiten von CS-Dateien in Visual Studio erfordert im Allgemeinen keinen das Projekt aus in Unity neu generiert werden.

## <a name="troubleshooting"></a>Problembehandlung

Wenn Sie feststellen, dass Änderungen an den CS-Dateien in Ihrem Visual Studio-Projekt nicht erkannt werden, stellen Sie sicher, dass "Unity C# Projekte" beim Generieren der VS-Projekt aus Unity Menü "Build" aktiviert ist.
