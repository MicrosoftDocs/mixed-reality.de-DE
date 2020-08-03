---
title: Konfigurieren eines neuen Unity-Projekts für Windows Mixed Reality
description: Anweisungen zum Konfigurieren eines Unity-Projekts für Windows Mixed Reality
author: thetuvix
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, gemischte Realität, Entwicklung, Einstieg, neues Projekt
ms.openlocfilehash: 877bdb803dc69e519a274eedabb8e51fe0197689
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476772"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>Konfigurieren eines neuen Unity-Projekts für Windows Mixed Reality 

## <a name="overview"></a>Übersicht

Windows Mixed Reality (WMR) ist eine Microsoft-Plattform, die als Teil des Betriebssystems Windows 10 eingeführt wird. Mit der WMR-Plattform können Sie Anwendungen erstellen, mit denen digitale Inhalte auf Holographic-und VR-Geräten angezeigt werden.

Wenn Sie für WMR einrichten, können Sie zwei Pfade verwenden. Ihre erste Option besteht darin, das [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) (mrtk) v2 zu installieren, mit dem die WMR-Umgebung automatisch eingerichtet wird. Die zweite Option besteht darin, einige Unity-Einstellungen manuell zu ändern, um Sie mit WMR zu umgehen. 

> [!NOTE]
> Sie können mrtk später jederzeit importieren, sodass es für die manuelle Route keinen Nachteil gibt.

Wenn Sie die manuelle Einrichtung von WMR auswählen, werden die Einstellungen, die Sie ändern müssen, in zwei Kategorien unterteilt: pro Projekt und pro Szene.

## <a name="per-project-settings"></a>Einstellungen pro Projekt

Die erste Einstellung, die Sie für WMR ändern müssen, ist die Projektplattform: 
1. **Datei > Buildeinstellungen auswählen...**
2. Wählen Sie in der Liste Plattform **universelle Windows-Plattform** aus, und klicken Sie auf **Plattform wechseln**
3. Festlegen des **SDK** auf **Universal 10**
4. Festlegen des **Zielgeräts** für **ein beliebiges Gerät** zur Unterstützung von immersiven Headsets oder wechseln zu **hololens**
5. **Buildtyp** auf **D3D** festlegen
6. **UWP SDK** auf **Letztes installiert** festlegen

![Unity-XR-Einstellungen](images/unity-uwp-settings.png)<br>
*Unity-XR-Einstellungen*

Nachdem die Plattform ordnungsgemäß konfiguriert wurde, müssen Sie Unity mitteilen, dass Ihre APP beim Exportieren eine [immersive Ansicht](app-views.md) anstelle einer 2D-Ansicht erstellen sollte:
1. Öffnen Sie im Fenster " **Buildeinstellungen** " die **Player-Einstellungen...**
2. Wählen Sie die **Einstellungen für universelle Windows-Plattform** Registerkarte und dann die Gruppe " **XR-Einstellungen** "
3. Aktivieren Sie im Abschnitt " **XR-Einstellungen** " das Kontrollkästchen " **Virtual Reality supported** ", um die Liste **Virtual Reality-Geräte** hinzuzufügen.
4. Vergewissern Sie sich in der Gruppe " **XR-Einstellungen** ", dass **"Windows Mixed Reality"** als unterstütztes Gerät aufgeführt ist. (diese Option kann in älteren Versionen von Unity als **Windows Holographic** angezeigt werden.)

![Unity-UWP-Einstellungen](images/xrsettings.png)<br>
*Unity-XR-Einstellungen*

### <a name="updating-the-manifest"></a>Aktualisieren des Manifests

Ihre APP kann jetzt Holographic-Rendering und räumliche Eingaben verarbeiten. Ihre APP muss jedoch die entsprechenden Funktionen in ihrem Manifest deklarieren, um von bestimmten Funktionen profitieren zu können. Sie finden Ihre Projektfunktionen, indem Sie zu den Einstellungen **für Player Einstellungen > Einstellungen für universelle Windows-Plattform > Veröffentlichungs Einstellungen > Funktionen**wechseln. 

Es wird empfohlen, dass Sie die Manifest-Deklarationen in Unity vornehmen, um Sie in allen zukünftigen Projekten einzuschließen, die Sie exportieren. Die anwendbaren Funktionen zum Aktivieren häufig verwendeter Unity-APIs für gemischte Realität sind:

|  Funktion  |  APIs, die Funktionen erfordern | 
|----------|----------|
|  SpatialPerception  |  "Surfaceobserver" (Zugriff auf [räumliche](spatial-mapping.md) zuordnungsnetze in hololens) ist &mdash; *für die allgemeine räumliche Nachverfolgung des Headsets nicht erforderlich* . | 
|  Webcam  |  Photocapture und Videocapture | 
|  Pictureslibrary/videoslibrary  |  Photocapture oder Videocapture bzw. (beim Speichern des erfassten Inhalts) | 
|  Mikrofon  |  Videocapture (bei der Erfassung von Audiodaten), "diktationerkenzer", "grammarerkenzer" und "keywordrecognizer" | 
|  InternetClient  |  "Diktationerkenzer" (und für die Verwendung des Unity-Profilers) | 

### <a name="quality-settings"></a>Qualitätseinstellungen

Hololens verfügt über eine GPU mobiler Klasse. Wenn Ihre APP auf hololens ausgerichtet ist, sollten Sie die Qualitätseinstellungen in Ihrer APP auf die schnellste Leistung optimieren, um sicherzustellen, dass Sie die vollständige Framerate beibehält:
1. Wählen Sie **> Projekteinstellungen bearbeiten > Qualität** aus.
2. Wählen Sie im **Windows Store** -Logo die **Dropdown** Liste aus, und wählen Sie **sehr niedrig**aus. Sie wissen, dass die Einstellung ordnungsgemäß angewendet wurde, wenn das Feld in der Spalte Windows Store und der Zeile **Sehr niedrig** grün ist.

![Unity-Qualitätseinstellungen](images/getting-started-unity-quality-settings.jpg)<br>
*Unity-Qualitätseinstellungen*

## <a name="per-scene-settings"></a>Pro-Szene-Einstellungen

### <a name="unity-camera-settings"></a>Unity-Kameraeinstellungen

Wenn **Virtual Reality** aktiviert ist, behandelt die [Unity-Kamera](camera-in-unity.md) Komponente die [Kopf-und stereorenderingfunktionen](rendering.md). Dies bedeutet, dass Sie das Hauptkamera Objekt nicht durch eine benutzerdefinierte Kamera ersetzen müssen.

Wenn Ihre APP speziell auf hololens ausgerichtet ist, müssen Sie einige Einstellungen ändern, um die transparente Anzeige des Geräts zu optimieren. Mit diesen Einstellungen können Sie Ihre Holographic-Inhalte in der physischen Welt anzeigen:
1. Wählen Sie in der **Hierarchie**die **Hauptkamera** aus.
2. Legen Sie im **Inspektor** -Panel die Transformations **Position** auf **0, 0, 0** fest, sodass der Speicherort des Benutzer Kopfes am Ursprung der Unity-Welt beginnt.
3. Ändern Sie die **Clear-Flags** in eine voll **Tonfarbe**.
4. Ändern Sie die **Hintergrund** Farbe in **RGBA 0, 0, 0**, 0. Schwarz wird in hololens als transparent gerendert.
5. Ändern Sie die **Clippingebenen in der Nähe** der [empfohlenen hololens](camera-in-unity.md#clip-planes) 0,85 (Meter).

![Unity-Kameraeinstellungen](images/Unitycamerasettings.png)<br>
*Unity-Kameraeinstellungen*

> [!IMPORTANT]
> Wenn Sie eine neue Kamera löschen und erstellen, stellen Sie sicher, dass die neue Kamera als " **maincamera**" gekennzeichnet ist.

## <a name="see-also"></a>Siehe auch
* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [Übersicht über Unity-Entwicklung](unity-development-overview.md)
