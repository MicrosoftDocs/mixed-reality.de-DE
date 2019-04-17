---
title: Speichern und Suchen nach Dateien
description: So suchen, speichern und Freigeben von Dateien auf HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: Exemplarische Vorgehensweise, mit der Dateiauswahl, Dateien, Fotos, Videos, Bilder, OneDrive, Speicher, Datei-Explorer
ms.openlocfilehash: d539af29fc94fdbde0d2cf08157ae8b5ce8ad0a1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595664"
---
# <a name="saving-and-finding-your-files"></a>Speichern und Suchen nach Dateien

Dateien können gespeichert und auf ähnliche Weise für andere Windows 10 Desktop und Mobile Geräte verwaltet werden:
* Verwenden die Datei-Explorer-app den Zugriff auf lokale Ordner
* In einem app eigenen Speicher
* In einem speziellen bekannte Ordner (z. B. die Videos oder Musik-Standardbibliothek)
* Verwenden einen Storage-Dienst, die eine app und Datei-Auswahl (z.B. OneDrive) enthält
* Mit einem desktop-PC verbunden auf Ihre HoloLens über USB, über die Unterstützung von MTP (Media Transfer Protocol)

## <a name="file-explorer"></a>Datei-Explorer

Sie können die Datei-Explorer-app verwenden, verschieben und Löschen von Dateien in HoloLens.

>[!NOTE]
>Wenn Sie alle Dateien im Datei-Explorer nicht angezeigt wird, der "Zuletzt verwendet"-Filter aktiv sein (Uhrsymbol wird im linken Bereich hervorgehoben). Wählen Sie zum Beheben dieses Problems die **dieses Gerät** dokumentieren Symbol im linken Bereich (unterhalb der Uhrsymbol), oder öffnen Sie das Menü, und wählen **dieses Gerät**.

## <a name="files-within-an-app"></a>Dateien in einer app

Wenn eine Anwendung Dateien auf Ihrem Gerät gespeichert wird, können Sie die Anwendung, für den Zugriff darauf.

### <a name="where-are-my-photosvideos"></a>Wo sind Meine Fotos bzw. Videos?

[Mixed Reality-Erfassung](mixed-reality-capture.md) Fotos und Videos werden auf das Gerät die-Ordner Eigene Aufnahmen gespeichert. Diese können auf das über die [Fotos-app](see-your-photos.md#photos-app). Sie können die Fotos-app verwenden, um Ihre Fotos und Videos in OneDrive zu synchronisieren. Sie können auch Ihre Fotos und Videos über die Seite Mixed Reality-Erfassen von Aufrufen der [Windows Device Portal](using-the-windows-device-portal.md#mixed-reality-capture).

### <a name="requesting-files-from-another-app"></a>Dateien von einer anderen app anfordern

Eine Anwendung kann eine Datei speichern oder öffnen Sie eine Datei von einer anderen app über anfordern [Datei Datumsauswahl](app-model.md#file-pickers).

## <a name="known-folders"></a>Bekannte Ordner

HoloLens unterstützt eine Reihe von [bekannte Ordner](app-model.md#known-folders) , dass apps über die Berechtigung zum Zugriff auf anfordern können.

## <a name="files-in-a-service"></a>Dateien in einem Dienst

Eine Datei zu speichern (oder auf Dateien aus zugreifen) einen Dienst, die app, die Verbindung mit dem Dienst muss installiert sein. Um Dateien zu speichern und auf die Dateien aus OneDrive zugreifen, müssen Sie installieren die [OneDrive-app](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3).

## <a name="mtp-media-transfer-protocol"></a>MTP (Media Transfer Protocol)

Ähnlich wie andere mobile Geräte, Herstellen einer Verbindung Ihrer Desktop-PC mit HoloLens und öffnen Datei-Explorer auf dem PC auf Ihre HoloLens-Bibliotheken (Fotos, Videos, Dokumente) zugreifen, für die einfache Übertragung an.

## <a name="clarifications"></a>Erläuterungen

* HoloLens unterstützt nicht das Herstellen einer Verbindung mit externen Festplatten oder SD-Karten.
* Ab der [Windows 10 April 2018 Update (RS4) für HoloLens](release-notes-april-2018.md), HoloLens enthält die Datei-Explorer für speichern und Verwalten von Dateien im Gerät. Das Hinzufügen von Datei-Explorer gibt Ihnen außerdem die Möglichkeit, Ihre Dateiauswahl (z. B. Speichern einer Datei auf Ihrem Gerät oder in OneDrive) auswählen.
