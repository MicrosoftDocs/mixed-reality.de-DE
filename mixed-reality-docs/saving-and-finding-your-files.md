---
title: Speichern und suchen von Dateien
description: Suchen, speichern und Freigeben von Dateien auf hololens.
author: mattzmsft
ms.author: mazeller
ms.date: 09/27/2018
ms.topic: article
keywords: Vorgehensweise, Dateiauswahl, Dateien, Fotos, Videos, Bilder, onedrive, Storage, Datei-Explorer
ms.openlocfilehash: d539af29fc94fdbde0d2cf08157ae8b5ce8ad0a1
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524605"
---
# <a name="saving-and-finding-your-files"></a>Speichern und suchen von Dateien

Dateien können auf ähnliche Weise wie andere Windows 10 Desktop-und mobile-Geräte gespeichert und verwaltet werden:
* Verwenden der Datei-Explorer-App für den Zugriff auf lokale Ordner
* Innerhalb des eigenen Speichers einer APP
* In einem speziellen bekannten Ordner (z. b. in der Video-oder Musikbibliothek)
* Verwenden eines Speicher Dienstanbieter mit einer APP und einer Dateiauswahl (z. b. onedrive)
* Verwenden eines Desktop-PCs, der über USB mit ihren hololens verbunden ist, über MTP (Media Transfer Protocol)-Unterstützung

## <a name="file-explorer"></a>Datei-Explorer

Sie können die Datei-Explorer-App verwenden, um Dateien aus hololens zu verschieben und zu löschen.

>[!NOTE]
>Wenn im Datei-Explorer keine Dateien angezeigt werden, ist der Filter "zuletzt" möglicherweise aktiv (das Clock-Symbol wird im linken Bereich hervorgehoben). Um dieses Problem zu beheben, wählen Sie das Symbol **dieses Geräte** Dokument im linken Bereich aus (unterhalb des Takt Symbols), oder öffnen Sie das Menü, und wählen Sie **dieses Gerät**aus.

## <a name="files-within-an-app"></a>Dateien in einer APP

Wenn eine Anwendung Dateien auf Ihrem Gerät speichert, können Sie diese Anwendung verwenden, um auf Sie zuzugreifen.

### <a name="where-are-my-photosvideos"></a>Wo sind meine Fotos/Videos?

Fotos und Videos mit [gemischter Realität](mixed-reality-capture.md) werden im Ordner für die Kamera Rollen des Geräts gespeichert. Auf diese kann über die [Fotos-App](see-your-photos.md#photos-app)zugegriffen werden. Mit der Fotos-App können Sie Ihre Fotos und Videos mit onedrive synchronisieren. Sie können auch auf Ihre Fotos und Videos im [Windows-Geräte Portal](using-the-windows-device-portal.md#mixed-reality-capture)über die Seite zur Erfassung gemischter Realität zugreifen.

### <a name="requesting-files-from-another-app"></a>Anfordern von Dateien aus einer anderen APP

Eine Anwendung kann zum Speichern einer Datei oder zum Öffnen einer Datei aus einer anderen APP über [Datei-Picker](app-model.md#file-pickers)aufgefordert werden.

## <a name="known-folders"></a>Bekannte Ordner

Hololens unterstützt eine Reihe [bekannter Ordner](app-model.md#known-folders) , für die apps eine Zugriffsberechtigung anfordern können.

## <a name="files-in-a-service"></a>Dateien in einem Dienst

Zum Speichern einer Datei in einem Dienst (oder zum Zugreifen auf Dateien) muss die dem Dienst zugeordnete App installiert werden. Um Dateien in onedrive zu speichern und auf Dateien zuzugreifen, müssen Sie die [onedrive-App](https://www.microsoft.com/store/apps/onedrive/9wzdncrfj1p3)installieren.

## <a name="mtp-media-transfer-protocol"></a>MTP (Media Transfer Protocol)

Stellen Sie wie bei anderen mobilen Geräten hololens mit Ihrem Desktop-PC her, und öffnen Sie den Datei-Explorer auf dem PC, um auf Ihre hololens-Bibliotheken (Fotos, Videos, Dokumente) zuzugreifen.

## <a name="clarifications"></a>Erklärungen

* Hololens unterstützt keine Verbindung mit externen Festplatten oder SD-Karten.
* Ab [Windows 10 April 2018 Update (RS4) für hololens](release-notes-april-2018.md)enthält hololens den Datei-Explorer zum Speichern und Verwalten von Dateien auf dem Gerät. Durch das Hinzufügen des Datei-Explorers haben Sie auch die Möglichkeit, die Dateiauswahl auszuwählen (z. b. das Speichern einer Datei auf Ihrem Gerät oder onedrive).
