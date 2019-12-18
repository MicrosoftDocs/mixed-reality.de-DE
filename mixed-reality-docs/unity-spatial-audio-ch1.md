---
title: Lernprogramme für räumliche Audiodaten-1. Hinzufügen räumlicher Audiodaten zu Ihrem Projekt
description: Fügen Sie das Microsoft spatializer-Plug-in zu Ihrem Unity-Projekt hinzu, um auf hololens 2 HRTF Hardware Offload zuzugreifen.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: Gemischte Realität, Unity, Tutorial, hololens2, räumliche Audiodaten
ms.openlocfilehash: 8978017b3ce6c49a81b3eee2fe21e9234f4e71f0
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182797"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a>Hinzufügen räumlicher Audiodaten zu Ihrem Unity-Projekt

Willkommen beim Spatial audiotutioral für Unity auf HoloLens2. Diese tutorialsequenz zeigt Folgendes:
* Verwenden von HRTF Auslagerung auf hololens 2 in Unity
* Aktivieren von "Reverb" bei Verwendung von "HRTF Auslagerung"

Das [GitHub-Repository für Microsoft spatializer](https://github.com/microsoft/spatialaudio-unity) verfügt über ein abgeschlossenes Unity-Projekt für diese tutorialsequenz. 

Unsere Empfehlungen für den Fall, dass es hilfreich sein kann, Klänge zu spatialisieren, finden Sie unter [Spatial Sound Design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).

## <a name="objectives"></a>Ziele
In diesem ersten Kapitel gehen Sie wie folgt vor:
* Erstellen eines Unity-Projekts und Importieren von mrtk
* Importieren des Microsoft spatializer-Plug-ins
* Aktivieren des Microsoft spatializer-Plug-ins
* Aktivieren räumlicher Audiodaten auf Ihrer Entwickler Arbeitsstation

## <a name="create-a-project-and-add-nuget-for-unity"></a>Erstellen eines Projekts und Hinzufügen von nuget für Unity
Beginnen Sie mit einem leeren Unity-Projekt, und fügen Sie nuget für Unity hinzu, und konfigurieren Sie es:
1. Herunterladen des neuesten [nugetforunity. unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)
2. Klicken Sie in der Unity-Menüleiste auf **Assets-> Paket importieren > benutzerdefiniertes Paket...** , und installieren Sie das nugetforunity-Paket:

![Benutzerdefiniertes Paket importieren](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a>Hinzufügen des Windows Mixed Reality-Pakets
Die Unterstützung von Windows Mixed Reality in Unity 2019 und höher ist in einem optionalen Paket enthalten. Um Sie dem Projekt hinzuzufügen, öffnen Sie die **Fenster > Paket-Manager** über die Unity-Menüleiste:

![Paket-Manager-Menü](images/spatial-audio/package-manager-menu.png)

Suchen und installieren Sie dann das **Windows Mixed Reality** -Paket:

![Paket-Manager-Fenster](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a>Installieren von mrtk und Microsoft spatializer
Installieren Sie mithilfe von nuget für Unity die mrtk-und Microsoft spatializer-Plug-ins:
1. Klicken Sie in der Unity-Menüleiste auf **nuget-> nuget-Pakete verwalten**.

![NuGet-Pakete verwalten](images/spatial-audio/manage-nuget-packages.png)

2. Geben Sie im **Suchfeld** "Microsoft. mixedreality. Toolkit" ein, und installieren Sie das mrtk Core-Paket: **Microsoft. mixedreality. Toolkit. Foundation**

![Mrtk-nuget-Paket](images/spatial-audio/mrtk-nuget-package.png)

Das [mrtk-nuget-Paket](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) hat zusätzlichen Kontext und Details.

4. Geben Sie im **Suchfeld** "Microsoft. spatialaudiodatei" ein, und installieren Sie das Microsoft spatializer-Paket: **Microsoft. spatialaudio. spatializer. unity**

![Spatializer-Plug-in nuget](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a>Einrichten von mrtk in Ihrem Projekt

1. Öffnen Sie das Fenster mit den Buildeinstellungen, indem Sie zu **Datei > Buildeinstellungen**navigieren.

2. Wählen Sie die _universelle Windows-Plattform_ aus, und klicken Sie auf **Plattform wechseln**

3. Klicken Sie im **Fenster erstellen** auf **Player Einstellungen** , um die Eigenschaften für **Player Einstellungen** im **Inspektor** -Bereich zu öffnen.
    * Aktivieren Sie unter **XR-Einstellungen**das Kontrollkästchen **Virtual Reality supported** .
    * Ändern Sie unter " **XR Settings**" den **Stereo-Renderingmodus** in **Single Pass-instanziierten**.
    * Aktivieren Sie unter **Veröffentlichungs Einstellungen**das Kontrollkästchen **räumliche Wahrnehmung** im Abschnitt " **Funktionen** ".

4. Klicken Sie in der Menüleiste auf **Mixed Reality Toolkit-> zu Szene hinzufügen und konfigurieren.** , um mrtk Ihrer Szene hinzuzufügen.

Weitere Anleitungen, einschließlich der Erstellung der APP und Bereitstellung auf einem hololens 2, finden Sie in [Kapitel 1 des Lern Basismoduls von Mr](mrlearning-base-ch1.md).

## <a name="enable-the-microsoft-spatializer-plugin"></a>Aktivieren des Microsoft spatializer-Plug-ins
Aktivieren Sie das **Microsoft spatializer** -Plug-in. Öffnen Sie die **Projekteinstellungen bearbeiten-> > Audiodatei**, und ändern Sie das **spatializer-Plug** -in in "Microsoft spatializer". Der **Audioabschnitt** der **Projekteinstellungen** sieht nun wie folgt aus:

![Projekteinstellungen mit dem spatializer-Plug-in](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a>Aktivieren räumlicher Audiodaten auf Ihrer Arbeitsstation
Unter Desktop Versionen von Windows ist das räumliche Audioformat standardmäßig deaktiviert. Aktivieren Sie diese Option, indem Sie in der Taskleiste mit der rechten Maustaste auf das Volume-Symbol klicken. Um die beste Darstellung von hololens 2 zu erhalten, wählen Sie **räumliches sound-> Windows-Sonic für Kopfhörer aus**.

![Desktop Einstellungen für räumliche Desktops](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> Diese Einstellung ist nur erforderlich, wenn Sie Vorhaben, das Projekt im Unity-Editor zu testen.

## <a name="next-steps"></a>Nächste Schritte
Fahren Sie mit [Unity Spatial Audio Kapitel 2](unity-spatial-audio-ch2.md) fort, um Schaltflächen-Interaktions Sounds zu spatialisieren.

