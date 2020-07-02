---
title: 6. Verpacken und Bereitstellen auf einem Gerät oder in einem Emulator
description: Teil 6 von 6 einer Tutorialreihe zum Erstellen einer einfachen Schach-App mit der Unreal Engine 4 und dem UX Tools-Plug-In des Mixed Reality-Toolkits
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Tutorial, erste Schritte, MRTK, UXT, UX Tools, Dokumentation
ms.openlocfilehash: 99407a4069f914bf077e6323dde3e12978f6b765
ms.sourcegitcommit: 7ca383ef1c5dc895ca2a289435f2e9d4c1ee6e65
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2020
ms.locfileid: "85345690"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a>6. Verpacken und Bereitstellen auf einem Gerät oder in einem Emulator

## <a name="overview"></a>Übersicht

Im vorhergehenden Tutorial haben Sie eine einfache Schaltfläche hinzugefügt, mit der die Schachfigur an ihre ursprüngliche Position zurückgesetzt wird. In diesem letzten Abschnitt führen Sie die App auf HoloLens 2 oder in einem Emulator aus. Wenn Sie über ein HoloLens 2 verfügen, können Sie die App entweder von Ihrem Computer t streamen oder verpacken, um sie direkt auf dem Gerät auszuführen. Wenn Sie kein Gerät haben, verpacken Sie die App, um Sie auf dem Emulator auszuführen. Am Ende dieses Abschnitts verfügen Sie über eine bereitgestellte Mixed Reality-App mit Interaktionen und Benutzeroberfläche, die Sie abspielen können.

## <a name="objectives"></a>Ziele

* Streamen der App an HoloLens 2 mit holografischem App-Remoting (nur Gerät)
* Verpacken und Bereitstellen der App auf einem HoloLens 2-Gerät oder in einem Emulator

## <a name="device-only-streaming"></a>Streamen (nur Gerät)
[Holografisches Remoting](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) bedeutet in diesem Fall das Streamen von Daten von einem PC oder einem eigenständigen UWP-Gerät auf die HoloLens 2, ohne den Kanal zu wechseln. Dabei empfängt die Remotinghost-App einen Eingabedatenstrom von einer HoloLens, rendert die Inhalte in einer virtuellen Rundumsicht und streamt die Inhaltsframes über WLAN zurück an die HoloLens. Streaming ermöglicht es Ihnen, Remoteansichten mit der vorhandenen Desktop-PC-Software zu generieren und mehr Systemressourcen zu nutzen. 

Um diese Möglichkeit für die Schach-App zu nutzen, müssen einige Voraussetzungen erfüllt sein:

1.  Installieren Sie den **Holographic Remoting-Player** aus dem Microsoft Store auf Ihrem HoloLens 2-Gerät, und führen Sie die App aus.

2.  Klicken Sie auf **Edit > Project Settings** (Bearbeiten > Projekteinstellungen), und aktivieren Sie im Abschnitt **Holographic Remoting** (Holografisches Remoting) die Option **enable remoting** (Remoting aktivieren).

3.  Starten Sie den Editor neu. [Suchen Sie die IP-Adresse Ihres Geräts](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens#connect-over-wi-fi), geben Sie sie ein, und klicken Sie dann auf **Connect** (Verbinden).

Wenn die Verbindung hergestellt wurde, klicken Sie rechts neben der Schaltfläche **Play** (Wiedergeben) auf den Dropdownpfeil, und wählen Sie **VR Preview** (VR-Vorschau) aus. Dadurch wird die App im VR-Vorschaufenster ausgeführt, das an das HoloLens-Headset gestreamt wird. 

## <a name="packaging-and-deploying-the-app"></a>Packen und Bereitstellen der App 

>[!NOTE]
>Wenn Sie zum ersten Mal eine Unreal-App für HoloLens verpacken, müssen Sie unterstützende Dateien aus dem Epic-Startprogramm herunterladen. 
>- Wechseln Sie im Epic Games-Startprogramm zur Registerkarte **Library** (Bibliothek), klicken Sie neben **Launch** (Starten) auf den Dropdownpfeil und dann auf **Options** (Optionen). 
>- Wählen Sie unter **Target Platforms** (Zielplattformen) **HoloLens 2** aus, und klicken Sie auf **Apply** (Übernehmen). 
>![Projekteinstellungen: Beschreibung](images/unreal-uxt/6-installationoptions.PNG)

1.  Navigieren Sie zu **Edit > Project Settings** („Bearbeiten“ > „Projekteinstellungen“). 
    * Fügen Sie unter **Project > Description > About > Project Name** (Projekt > Beschreibung > Info > Projektname) einen Namen für Ihr Projekt hinzu. 
    * Fügen Sie unter **Project > Description > Publisher > Company Distinguished Name** (Projekt > Beschreibung > Herausgeber > Definierter Name des Unternehmens) Folgendes ein: **CN=IhrFirmenname**.

> [!IMPORTANT]
> Eins dieser Felder leer zu lassen, führt zu einem Fehler, wenn Sie in Schritt 3 versuchen, ein neues Zertifikat zu generieren. 

> [!IMPORTANT]
> Der Name des Ausstellers muss im [LADPv3-Format für definierte Namen](https://www.ietf.org/rfc/rfc2253.txt) vorliegen. Ein Ausstellername in ungültigem Format führt beim Verpacken zum Fehler „Signaturschlüssel nicht gefunden. Die App konnte nicht digital signiert werden“ .

![Projekteinstellungen: Beschreibung](images/unreal-uxt/6-cn.PNG)

2.  Aktivieren Sie unter **Platforms > HoloLens** (Plattformen > HoloLens) die Optionen **Build for HoloLens Emulation** (Build für HoloLens-Emulation) und/oder **Build for HoloLens Device** (Build für HoloLens-Gerät).

3.  Klicken Sie im Abschnitt **Packaging** (Verpacken) neben **Signing Certificate** (Signaturzertifikat) auf **Generate new** (Neu generieren).

> [!IMPORTANT]
> Wenn Sie ein bereits generiertes Zertifikat verwenden, muss der Name des Zertifikatausstellers gleich dem Namen des Herausgebers der Anwendung sein. Andernfalls führt dies zum „Signaturschlüssel nicht gefunden. Die App konnte nicht digital signiert werden“- Fehler.

![Projekteinstellungen: Plattformen (HoloLens)](images/unreal-uxt/6-packaging.PNG)

4. Klicken Sie für Testzwecke auf **Keins**, wenn Sie aufgefordert werden, ein Kennwort für den privaten Schlüssel zu erstellen.

![Generieren eines neuen Zertifikats](images/unreal-uxt/6-private-key-testing.png)

5. Navigieren Sie zu **File > Package Project** („Datei“ > „Projekt verpacken“), und wählen Sie **HoloLens** aus. 
    * Erstellen Sie einen neuen Ordner zum Speichern Ihres Pakets, und klicken Sie auf **Select Folder** (Ordner auswählen). 

6.  Öffnen Sie nach dem Verpacken der App das [Windows-Geräteportal](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal), navigieren Sie zu **Views > Apps** (Ansichten > Apps), und suchen Sie nach dem Abschnitt **Deploy apps** (Apps bereitstellen).

7.  Klicken Sie auf **Durchsuchen...** , navigieren Sie zur Datei **ChessApp.appxbundle**, und klicken Sie auf **Öffnen**. 

    * Aktivieren Sie das Kontrollkästchen neben **Allow me to select framework packages** (Auswählen von Framework-Paketen zulassen), wenn Sie die App zum ersten Mal auf Ihrem Gerät installieren. 
    * Schließen Sie im nächsten Dialogfeld die entsprechenden **VCLibs**- und **appx**-Dateien ein („arm64“ für Gerät, „x64“ für Emulator). Sie finden diese in dem Ordner, in dem Sie das Paket gespeichert haben, unter **HoloLens**.

8.  Klicken Sie auf **Install** (Installieren).
    * Sie können jetzt zu **All Apps** (Alle Apps) wechseln und auf die neu installierte App tippen, um sie auszuführen. Sie können die App jedoch auch direkt über das **Windows-Geräteportal** starten. 

Herzlichen Glückwunsch! Ihre Mixed Reality-Anwendung für HoloLens ist fertig und einsatzbereit. Das ist aber noch nicht alles. MRTK verfügt über viele eigenständige Features, die Sie zu Ihren Projekten hinzufügen können, einschließlich räumlicher Zuordnung, Anvisieren und Spracheingabe und sogar QR-Codes. Weitere Informationen zu diesen Features finden Sie unter [Unreal-Entwicklung: Übersicht](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).
