---
title: In-App-Käufe
description: In-app-Käufe werden in mixed Reality-apps unterstützt, aber es gibt einiges zu deren Einrichtung.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: in-app-Käufe, hololens
ms.openlocfilehash: bc96893d1777e94295285736982fd9a7167240a4
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595781"
---
# <a name="in-app-purchases"></a>In-App-Käufe

In-app-Käufe werden in HoloLens unterstützt, aber es gibt einiges zu deren Einrichtung.

Um den in-app-Kauf nutzen zu können Funktionen, müssen Sie:
* Erstellen Sie eine XAML [2D-Ansicht](app-views.md) als ein Slate angezeigt werden
* Um die Platzierung zu aktivieren, das Ansicht des immersive verlässt wechseln
* Die API aufrufen: "await" [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

Diese API wird das vordefinierte Windows-Betriebssystem-Popup angezeigt, die zeigt, die in-app-Käufe Name, Beschreibung und Preis. Der Benutzer kann dann Kaufoptionen auswählen. Sobald die Aktion abgeschlossen ist, die app auf der Benutzeroberfläche anzuzeigen, die dem Benutzer ermöglicht, wechseln Sie zurück zur muss seine [immersive Ansicht](app-views.md).

Für apps für Desktop-basierten Windows Mixed Reality immersive Headsets ist es nicht erforderlich, manuell zu einer XAML-Ansicht vor dem Aufrufen der API RequestProductPurchaseAsync umschalten.
