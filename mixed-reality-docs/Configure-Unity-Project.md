---
title: Konfigurieren Sie ein neues Unity-Projekt für Windows Mixed Reality
description: Konfigurieren von Unity-Projekt ohne MRTK
author: yoyoz
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, mixed Reality, Entwicklung, erste Schritte, neues Projekt
ms.openlocfilehash: 68dded9d0fc9e861bdda56c4954d72ddafafa686
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326091"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a>Konfigurieren Sie ein neues Unity-Projekt für Windows Mixed Reality 

(überspringen Sie, wenn Sie bereits MRTK v2 in Ihrem Unity-Projekt importiert haben)

Wenn Sie ein neues Unity-Projekt erstellt, ohne Mixed Reality-Toolkit zu importieren möchten, stehen Ihnen eine kleine Gruppe von Unity-Einstellungen manuell ändern für Windows Mixed Reality, die in zwei Kategorien unterteilt müssen: pro Projekt und pro-Szene.

## <a name="per-project-settings"></a>Einstellungen pro Projekt

Um Windows Mixed Reality Ziel festzulegen, müssen Sie zuerst Ihr Unity-Projekt als universelle Windows-Plattform-app exportieren festlegen: 
1. Wählen Sie **Datei > Buildeinstellungen...**
2. Wählen Sie **universelle Windows-Plattform** in die Plattform aus, und klicken Sie auf **Plattform wechseln**
3. Legen Sie **SDK** zu **universelle 10**
4. Legen Sie **Zielgerät** zu **einem beliebigen Gerät** zur Unterstützung einer immersive Headsets aus, oder wechseln Sie zur **HoloLens**
5. Legen Sie **Buildtyp** zu **D3D**
6. Legen Sie **UWP SDK** zu **zuletzt installierte**

Klicken Sie dann müssen wir wissen, dass die app aus, es versucht wird, exportieren, zu erstellen, sollten Unity können eine [immersive Ansicht](app-views.md) anstelle einer 2D-Ansicht. Zu diesem Zweck aktivieren "Virtuelle Realität unterstützt":
1. Von der **Buildeinstellungen...**  geöffnete Fenster **Playereinstellungen...**
2. Wählen Sie die **Einstellungen für die universelle Windows-Plattform** Registerkarte
3. Erweitern Sie die **XR-Einstellungen** Gruppe
4. In der **XR-Einstellungen** aktivieren Sie im Abschnitt der **virtuelle Realität unterstützt** Kontrollkästchen zum Hinzufügen der **Virtual Reality-Geräte** Liste.
5. In der **XR-Einstellungen** gruppieren, überprüfen Sie, ob **"Windows Mixed Reality"** wird als ein unterstütztes Gerät aufgeführt. (Dies kann als "Windows Holographic" in älteren Versionen von Unity angezeigt)

![Einstellungen für die Qualität von Unity](images/getting-started-unity-quality-settings.jpg)<br>
*Unity-Xr-Einstellungen*

Ihre app kann nun grundlegende holographic Rendering und räumliche Eingabe erfolgen. Um weiter gehen und bestimmte Funktionen nutzen, muss Ihre app die entsprechenden Funktionen im Manifest deklariert werden. Die manifest-Deklarationen können in Unity vorgenommen werden, damit sie in jedem nachfolgenden Projektexport enthalten sind. Die Einstellung finden Sie im **Playereinstellungen > Einstellungen für die universelle Windows-Plattform > Veröffentlichungseinstellungen > Funktionen**. Die entsprechenden Funktionen für die Aktivierung von häufig verwendeten Unity-APIs für Mixed Reality sind:

|  Funktion  |  APIs, die Funktion erfordern | 
|----------|----------|
|  SpatialPerception  |  SurfaceObserver (Zugriff auf [räumliche Zuordnung](spatial-mapping.md) Gitter für HoloLens)&mdash;*keine Funktion, die für allgemeine räumliche nachverfolgung von den Kopfhörer erforderlich sind* | 
|  WebCam  |  PhotoCapture und VideoCapture | 
|  PicturesLibrary / "videoslibrary"  |  PhotoCapture oder VideoCapture, bzw. (bei den aufgezeichneten Inhalt zu speichern) | 
|  Mikrofon  |  VideoCapture (wenn Audio erfassen), DictationRecognizer, GrammarRecognizer und KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (und mit der Unity-Profiler) | 

**Einstellungen für die Qualität von Unity**

![Einstellungen für die Qualität von Unity](images/getting-started-unity-quality-settings.jpg)<br>
*Einstellungen für die Qualität von Unity*

HoloLens verfügt über eine GPU-Mobile-Klasse. Wenn Ihre app HoloLens ausgelegt ist, sollten Sie die Qualität-Einstellungen für schnellste Leistung optimiert, um sicherzustellen, dass wir die vollständige Framerate verwalten:
1. Wählen Sie **Bearbeiten > Projekteinstellungen > Qualität**
2. Wählen Sie die **Dropdownliste** unter der **Windows Store** Logo, und wählen **sehr niedrig**. Wissen Sie, dass die Einstellung ist ordnungsgemäß angewendet, wenn das Feld in der Windows Store-Spalte und **sehr niedrig** Zeile wird grün angezeigt.

## <a name="per-scene-settings"></a>Pro-Szene-Einstellungen

**Unity-Kameraeinstellungen**

![Unity-Kameraeinstellungen](images/Unitycamerasettings.png)<br>
*Unity-Kameraeinstellungen*

Nachdem Sie das Kontrollkästchen "Virtuelle Realität unterstützt" aktiviert die [Unity Kamera](camera-in-unity.md) führt [head-nachverfolgung und stereoskopische Rendering](rendering.md). Es ist nicht erforderlich, es mit einer benutzerdefinierten Kamera dazu ersetzen.

Wenn Ihre app speziell HoloLens ausgelegt ist, haben Sie einige Einstellungen, die geändert werden, um die für das Gerät die transparent angezeigt, und zu optimieren, damit Ihre app durch, die physische Welt angezeigt werden müssen:
1. In der **Hierarchie**, wählen die **Main Camera**
2. In der **Inspektor** legen Sie die Transformation **Position** zu **0, 0, 0** sodass gestartet wird, der Speicherort des Anfangswerts Benutzer auf den Ursprung der Unity-Welt.
3. Änderung **Kennzeichnungen löschen** zu **Volltonfarbe**.
4. Ändern der **Hintergrund** Farbe **RGBA 0,0,0,0**. Schwarz, die als Transparenz HoloLens gerendert werden.
5. Änderung **Clipping Planes - nahezu** auf die [HoloLens empfohlen](camera-in-unity.md#clip-planes) 0,85 (Meter).

Wenn Sie zu löschen und erstellen eine neue Kamera, stellen Sie sicher, dass Ihre Kamera **markierter** als **MainCamera**.


## <a name="see-also"></a>Siehe auch
* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [Übersicht über die Unity-Entwicklung](unity-development-overview.md)
