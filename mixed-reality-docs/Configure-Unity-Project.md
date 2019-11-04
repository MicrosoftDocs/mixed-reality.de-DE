---
title: Konfigurieren eines neuen Unity-Projekts für Windows Mixed Reality
description: Konfigurieren des Unity-Projekts ohne mrtk
author: thetuvix
ms.author: alexturn
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, gemischte Realität, Entwicklung, Einstieg, neues Projekt
ms.openlocfilehash: af30cf91eda1b654bea6048c34f63c61238626c7
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437113"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>Konfigurieren eines neuen Unity-Projekts für Windows Mixed Reality 

(überspringen, wenn Sie mrtk v2 bereits in Ihr Unity-Projekt importiert haben)

Wenn Sie ein neues Unity-Projekt erstellen möchten, ohne Mixed Reality Toolkit zu importieren, gibt es eine kleine Reihe von Unity-Einstellungen, die Sie manuell für Windows Mixed Reality ändern müssen, die in zwei Kategorien unterteilt sind: pro Projekt und pro Szene.

## <a name="per-project-settings"></a>Einstellungen pro Projekt

Um Windows Mixed Reality als Ziel festzulegen, müssen Sie zuerst Ihr Unity-Projekt so festlegen, dass es als universelle Windows-Plattform-App exportiert wird: 
1. **Datei > Buildeinstellungen auswählen...**
2. Wählen Sie in der Liste Plattform **universelle Windows-Plattform** aus, und klicken Sie auf **Plattform wechseln**
3. Festlegen des **SDK** auf **Universal 10**
4. Festlegen des **Zielgeräts** für **ein beliebiges Gerät** zur Unterstützung von immersiven Headsets oder wechseln zu **hololens**
5. **Buildtyp** auf **D3D** festlegen
6. **UWP SDK** auf **Letztes installiert** festlegen

Wir müssen Unity dann mitteilen, dass die zu exportierende App eine [immersive Ansicht](app-views.md) anstelle einer 2D-Ansicht erstellen sollte. Dies geschieht durch Aktivieren von "Virtual Reality supported":
1. Öffnen Sie im Fenster " **Buildeinstellungen** " die **Player-Einstellungen...**
2. Wählen Sie die **Einstellungen für universelle Windows-Plattform** Registerkarte aus.
3. Erweitern der Gruppe " **XR-Einstellungen** "
4. Aktivieren Sie im Abschnitt " **XR-Einstellungen** " das Kontrollkästchen " **Virtual Reality supported** ", um die Liste **Virtual Reality-Geräte** hinzuzufügen.
5. Vergewissern Sie sich in der Gruppe " **XR-Einstellungen** ", dass **"Windows Mixed Reality"** als unterstütztes Gerät aufgeführt ist. (Dies wird in älteren Versionen von Unity möglicherweise als "Windows Holographic" angezeigt)

![Unity-Qualitätseinstellungen](images/getting-started-unity-quality-settings.jpg)<br>
*Unity-XR-Einstellungen*

Ihre APP kann jetzt grundlegendes Holographic-Rendering und räumliche Eingaben durchführen. Um weiter zu gehen und bestimmte Funktionen zu nutzen, muss Ihre APP die entsprechenden Funktionen in ihrem Manifest deklarieren. Die Manifest-Deklarationen können in Unity erstellt werden, sodass Sie in jedem nachfolgenden Projekt Export enthalten sind. Die Einstellung finden Sie unter **Player Settings > Settings for universelle Windows-Plattform > Publishing Settings >-Funktionen**. Die anwendbaren Funktionen zum Aktivieren häufig verwendeter Unity-APIs für gemischte Realität sind:

|  Funktion  |  APIs, die Funktionen erfordern | 
|----------|----------|
|  Spatialperception  |  "Surfaceobserver" (Zugriff auf [räumliche](spatial-mapping.md) zuordnungsnetze in hololens)&mdash;*keine Funktion für die allgemeine räumliche Nachverfolgung des Headsets erforderlich* . | 
|  Webcam  |  Photocapture und Videocapture | 
|  Pictureslibrary/videoslibrary  |  Photocapture oder Videocapture bzw. (beim Speichern des erfassten Inhalts) | 
|  Mikrofon  |  Videocapture (bei der Erfassung von Audiodaten), "diktationerkenzer", "grammarerkenzer" und "keywordrecognizer" | 
|  Internet Client deklarieren  |  "Diktationerkenzer" (und für die Verwendung des Unity-Profilers) | 

**Unity-Qualitätseinstellungen**

![Unity-Qualitätseinstellungen](images/getting-started-unity-quality-settings.jpg)<br>
*Unity-Qualitätseinstellungen*

Hololens verfügt über eine GPU mobiler Klasse. Wenn Ihre APP auf hololens ausgerichtet ist, sollten Sie die Qualitätseinstellungen für die schnellste Leistung optimieren, um sicherzustellen, dass die vollständige Framerate beibehalten wird:
1. Wählen Sie **> Projekteinstellungen bearbeiten > Qualität** aus.
2. Wählen Sie im **Windows Store** -Logo die **Dropdown** Liste aus, und wählen Sie **sehr niedrig**aus. Sie werden feststellen, dass die Einstellung ordnungsgemäß angewendet wird, wenn das Feld in der Windows Store-Spalte und die **sehr niedrige** Zeile grün ist.

## <a name="per-scene-settings"></a>Pro-Szene-Einstellungen

**Unity-Kameraeinstellungen**

![Unity-Kameraeinstellungen](images/Unitycamerasettings.png)<br>
*Unity-Kameraeinstellungen*

Nachdem Sie das Kontrollkästchen "Virtual Reality supported" aktiviert haben, verarbeitet die [Unity-Kamera](camera-in-unity.md) Komponente die [Kopf-und stereorenderingfunktionen](rendering.md). Hierfür ist es nicht erforderlich, Sie durch eine benutzerdefinierte Kamera zu ersetzen.

Wenn Ihre APP speziell auf hololens ausgerichtet ist, gibt es einige Einstellungen, die geändert werden müssen, um die transparente Anzeige des Geräts zu optimieren, sodass Ihre APP in der physischen Welt angezeigt wird:
1. Wählen Sie in der **Hierarchie**die **Hauptkamera** aus.
2. Legen Sie im **Inspektor** -Panel die Transformations **Position** auf **0, 0, 0** fest, sodass der Speicherort des Benutzers mit dem Ursprung der Unity-Welt beginnt.
3. Ändern Sie die **Clear-Flags** in eine voll **Tonfarbe**.
4. Ändern Sie die **Hintergrund** Farbe in **RGBA 0, 0, 0**, 0. Schwarz wird in hololens als transparent gerendert.
5. Ändern Sie die **Clippingebenen in der Nähe** der [empfohlenen hololens](camera-in-unity.md#clip-planes) 0,85 (Meter).

Wenn Sie eine neue Kamera löschen und eine neue Kamera erstellen, stellen Sie sicher, dass Ihre Kamera als " **maincamera**" **gekennzeichnet** ist.


## <a name="see-also"></a>Weitere Informationen:
* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [Übersicht über Unity-Entwicklung](unity-development-overview.md)
