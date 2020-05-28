---
title: 6. Verpacken und Bereitstellen auf einem Gerät oder in einem Emulator
description: Teil 6 eines Tutorials zum Erstellen einer einfachen Schach-App mit Unreal Engine 4 und dem UX-Tools-Plug-In des Mixed Reality-Toolkits
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Tutorial, erste Schritte, MRTK, UXT, UX Tools, Dokumentation
ms.openlocfilehash: b3f0b5f9ca5347c337091539b1cc0e214515c989
ms.sourcegitcommit: 09d9fa153cd9072f60e33a5f83ced8167496fcd7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/18/2020
ms.locfileid: "83519966"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a>6. Verpacken und Bereitstellen auf einem Gerät oder in einem Emulator

In diesem Abschnitt erfahren Sie Schritt für Schritt, wie Sie Ihre App für die Ausführung auf einem HoloLens 2-Gerät oder in einem Emulator vorbereiten. Wenn Sie über ein Gerät verfügen, können Sie die App entweder von Ihrem Computer an das Gerät streamen oder die App verpacken, um sie direkt auf dem Gerät auszuführen. Wenn Sie über kein Gerät verfügen, müssen Sie die App verpacken, um sie im Emulator ausführen zu können. 

## <a name="objectives"></a>Ziele

* Streamen der App an HoloLens 2 mittels holografischem App-Remoting (nur Gerät)
* Verpacken und Bereitstellen der App auf einem HoloLens 2-Gerät oder in einem Emulator

## <a name="device-only-stream"></a>Streamen (nur Gerät)

1.  Installieren Sie den **Holographic Remoting-Player** aus dem Microsoft Store auf Ihrem HoloLens 2-Gerät, und führen Sie die App aus.

2.  Navigieren Sie zu **Edit > Project Settings** („Bearbeiten“ > „Projekteinstellungen“). Aktivieren Sie im Abschnitt „Holographic Remoting“ (Holografisches Remoting) das Kontrollkästchen zum Aktivieren des Remotings, und starten Sie den Editor neu.

3.  Geben Sie die IP-Adresse Ihres Geräts ein, und klicken Sie auf „Connect“ (Verbinden).

4.  Wenn die Verbindung hergestellt wurde, klicken Sie in Ihrem UE4-Editor rechts neben der Schaltfläche „Play“ (Spielen) auf den Dropdownpfeil, und wählen Sie „VR Preview“ (VR-Vorschau) aus.

## <a name="package-and-deploy-your-app"></a>Verpacken und Bereitstellen Ihrer App 

>[!NOTE]
>Wenn Sie zum ersten Mal eine Unreal-App für HoloLens verpacken, müssen Sie unterstützende Dateien aus dem Epic-Startprogramm herunterladen. Wechseln Sie dazu zur Registerkarte **Library** (Bibliothek) im Startprogramm von Epic Games. Wählen Sie den Dropdownpfeil neben **Launch** (Starten) und dann **Options** (Optionen) aus. Wählen Sie unter **Target Platforms** (Zielplattformen) **HoloLens 2** aus, und klicken Sie auf **Apply** (Übernehmen). 
>![Projekteinstellungen: Beschreibung](images/unreal-uxt/6-installationoptions.PNG)

1.  Navigieren Sie zu **Edit > Project Settings** („Bearbeiten“ > „Projekteinstellungen“). Geben Sie unter **Project > Description > About > Project Name** („Projekt“ > „Beschreibung“ > „Info“ > „Projektname“) einen Namen für Ihr Projekt an. Geben Sie unter **Project > Description > Publisher > Company Distinguished Name** („Projekt“ > „Beschreibung“ > „Herausgeber“ > „Definierter Name des Unternehmens“) Folgendes ein: CN={NAME DES UNTERNEHMENS}. Wenn Sie eines dieser Felder leer lassen, tritt ein Fehler auf. 

![Projekteinstellungen: Beschreibung](images/unreal-uxt/6-cn.PNG)

2.  Wählen Sie unter **Platforms > HoloLens** („Plattformen“ > „HoloLens“) je nach gewünschtem Ziel „Emulation“ und/oder „Device“ (Gerät) aus.

3.  Klicken Sie im Abschnitt **Packaging** (Verpacken) neben **Signing Certificate** (Signaturzertifikat) auf die Schaltfläche **Generate new** (Neu generieren), um ein neues Signaturzertifikat zu generieren. Kehren Sie zum Hauptfenster zurück.

![Projekteinstellungen: Plattformen (HoloLens)](images/unreal-uxt/6-packaging.PNG)

4.  Navigieren Sie zu **File > Package Project** („Datei“ > „Projekt verpacken“), und wählen Sie **HoloLens** aus. Erstellen Sie einen neuen Ordner zum Speichern Ihres Pakets, und klicken Sie auf **Select Folder** (Ordner auswählen). 

5.  Nachdem die App erfolgreich verpackt wurde, öffnen Sie das **Windows-Geräteportal**, navigieren Sie zu **Ansichten > Apps**, und suchen Sie nach dem Abschnitt **Deploy apps** (Apps bereitstellen).

6.  Klicken Sie auf **Durchsuchen...** , und navigieren Sie zur Datei **ChessApp.appxbundle**. Klicken Sie auf **Öffnen**. 

    * Wenn Sie die App zum ersten Mal auf Ihrem Gerät installieren, aktivieren Sie das Kontrollkästchen neben **Allow me to select framework packages** (Auswählen von Framework-Paketen zulassen). Schließen Sie im nächsten Dialogfeld die entsprechende VCLibs-APPX-Datei ein („arm64“ für Gerät, „x64“ für Emulator). 

7.  Klicken Sie auf **Install** (Installieren).

Damit ist dieses Tutorial abgeschlossen.  