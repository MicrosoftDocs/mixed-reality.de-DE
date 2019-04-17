---
title: Abrufen von apps für HoloLens
description: Beschreibt die Installation von apps für HoloLens, sowohl über die Microsoft Store und querladen.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: per sideload übertragen, clientseitige auslastungs-, sideloading, Store, Uwp, -app installieren
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593248"
---
# <a name="get-apps-for-hololens"></a>Abrufen von apps für HoloLens

HoloLens unterstützt viele vorhandene UWP-Anwendungen aus dem appstore als auch neue apps, die speziell für HoloLens, als ein Windows 10-Gerät. Zusätzlich dazu, möglicherweise sogar möchten [entwickeln](development-overview.md) herunter, und installieren Sie Ihre eigenen apps oder der Anmeldeinformationen Ihren Freunden!

## <a name="installing-apps"></a>Installieren von Apps

Es gibt drei Möglichkeiten, neue apps auf Ihre HoloLens zu installieren. Die primäre Methode werden neue Anwendungen aus dem Windows Store installiert werden. Allerdings können Sie auch Ihre eigenen Anwendungen mithilfe des Verwaltungsportals Gerät installieren oder indem Sie sie aus Visual Studio bereitstellen.

### <a name="from-the-microsoft-store"></a>Aus dem Microsoft Store
1. Führen Sie eine [Bloom](gestures.md#bloom) Geste zum Öffnen der [Menü "Start"](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Wählen Sie die Store-app, und tippen Sie dann auf diese Kachel in Ihre Welt zu platzieren.
3. Wenn die Store-app geöffnet wird, verwenden Sie die Suchleiste, um für alle gewünschten Anwendungen zu suchen.
4. Wählen Sie **erhalten** oder **installieren** auf der Seite der Anwendung (eine Bestellung kann erforderlich sein).

### <a name="installing-an-application-package-with-the-device-portal"></a>Installieren ein Anwendungspaket mit dem Device Portal
1. Herstellen einer Verbindung zwischen [Device Portal](using-the-windows-device-portal.md) an das Ziel HoloLens.
2. Navigieren Sie zu der **Apps** Seite im linken Navigationsbereich.
3. Klicken Sie unter **App-Paket** navigieren Sie zu der AppX-Datei Ihrer Anwendung zugeordnet.
  >[!IMPORTANT]
  >Stellen Sie sicher, dass alle zugehörigen Abhängigkeiten und Zertifikat-Dateien zu verweisen.

4. Klicken Sie auf **wechseln**.

![Installieren von app-Formular in Windows Device Portal für Microsoft HoloLens](images/deviceportal-appmanager.jpg)<br>
Mithilfe von Windows Device Portal-Installation eine app für HoloLens

### <a name="deploying-from-microsoft-visual-studio-2015"></a>Bereitstellen von Microsoft Visual Studio 2015
1. Öffnen Sie Visual Studio-Projektmappe (SLN-Datei) Ihrer app.
2. Öffnen des Projekts **Eigenschaften** .
3. Wählen Sie die folgenden Build-Konfiguration: Master/X86/Remote-Computer.
4. Wenn Sie Remotecomputer auswählen:
   * Stellen Sie sicher die adresspunkte, die HoloLens' WiFi IP-Adresse.
   * Festlegen der Authentifizierung auf universell (unverschlüsseltes Protokoll).
5. Erstellen Sie die Projektmappe.
6. Klicken Sie auf die **Remotecomputer** Schaltfläche, um die app von Ihrem Entwicklungs-PC auf Ihre HoloLens bereitgestellt. Wenn Sie bereits einen vorhandenen Build auf die HoloLens haben, wählen Sie Ja aus, um diese neuere Version neu installieren.<br>
  ![Remote-computerbereitstellung für apps, Microsoft HoloLens in Visual Studio](images/vs2015-remotedeployment.jpg)<br>
7. Die Anwendung installiert und automatisch zu starten, auf Ihre HoloLens.
