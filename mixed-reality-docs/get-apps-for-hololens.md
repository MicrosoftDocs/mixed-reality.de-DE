---
title: Apps für hololens erhalten
description: Beschreibt die Installation von Apps für hololens, beides über das Microsoft Store und das Sideloading.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Sideload, Seitenlast, Sideloading, Store, UWP, APP, Installation
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522561"
---
# <a name="get-apps-for-hololens"></a>Apps für hololens erhalten

Als Windows 10-Gerät unterstützt hololens viele vorhandene UWP-Anwendungen aus dem App Store sowie neue apps, die speziell für hololens erstellt wurden. Darüber hinaus können Sie sogar Ihre eigenen Apps oder die Ihrer Freunde [entwickeln](development-overview.md) und installieren.

## <a name="installing-apps"></a>Installieren von apps

Es gibt drei Möglichkeiten, neue apps auf Ihren hololens zu installieren. Die primäre Methode ist die Installation neuer Anwendungen aus dem Windows Store. Allerdings können Sie Ihre eigenen Anwendungen auch über das Geräte Portal oder durch Bereitstellung aus Visual Studio installieren.

### <a name="from-the-microsoft-store"></a>Aus der Microsoft Store
1. Führen Sie eine [Bloom-Geste](gestures.md#bloom) aus, um das [Startmenü](navigating-the-windows-mixed-reality-home.md#start-menu) zu öffnen.
2. Wählen Sie die Store-App aus, und tippen Sie dann auf diese Kachel in die Welt.
3. Nachdem die Store-App geöffnet wurde, verwenden Sie die Suchleiste, um nach einer beliebigen gewünschten Anwendung zu suchen.
4. Wählen Sie auf der Seite der Anwendung die Option **Get** oder **install** (ein Kauf ist möglicherweise erforderlich).

### <a name="installing-an-application-package-with-the-device-portal"></a>Installieren eines Anwendungspakets mit dem Geräte Portal
1. Stellen Sie eine Verbindung zwischen dem [Geräte Portal](using-the-windows-device-portal.md) und den Ziel-hololens her.
2. Navigieren Sie im linken Navigationsbereich zur Seite **apps** .
3. Navigieren Sie unter **App-Paket** zu der AppX-Datei, die Ihrer Anwendung zugeordnet ist.
  >[!IMPORTANT]
  >Stellen Sie sicher, dass Sie auf verknüpfte Abhängigkeits-und Zertifikat Dateien verweisen

4. Klicken Sie auf **Go**.

![App-Formular im Windows-Geräte Portal auf Microsoft hololens installieren](images/deviceportal-appmanager.jpg)<br>
Verwenden des Windows-Geräte Portals zum Installieren einer APP auf hololens

### <a name="deploying-from-microsoft-visual-studio-2015"></a>Bereitstellen von Microsoft Visual Studio 2015
1. Öffnen Sie die Visual Studio-Projekt Mappe (SLN-Datei) Ihrer APP.
2. Öffnen Sie die **Eigenschaften** des Projekts.
3. Wählen Sie die folgende Buildkonfiguration aus: Master/x86/Remote Computer.
4. Wenn Sie Remote Computer auswählen:
   * Stellen Sie sicher, dass die Adresse auf die WiFi-IP-Adresse des hololens verweist.
   * Legen Sie die Authentifizierung auf Universal (unverschlüsseltes Protokoll) fest.
5. Erstellen Sie die Lösung.
6. Klicken Sie auf die Schaltfläche **Remote Computer** , um die APP von Ihrem Entwicklungs-PC in ihren hololens bereitzustellen. Wenn Sie bereits über einen vorhandenen Build auf den hololens verfügen, wählen Sie ja aus, um diese neuere Version erneut zu installieren.<br>
  ![Remote Computer Bereitstellung für Apps für Microsoft hololens in Visual Studio](images/vs2015-remotedeployment.jpg)<br>
7. Die Anwendung wird auf Ihren hololens installiert und automatisch gestartet.
