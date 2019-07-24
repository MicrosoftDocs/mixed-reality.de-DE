---
title: In-App-Käufe
description: In-App-Käufe werden in Mixed Reality-Apps unterstützt, aber es gibt einige Aufgaben, die Sie einrichten müssen.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: in-App-Käufe, hololens
ms.openlocfilehash: bc96893d1777e94295285736982fd9a7167240a4
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515291"
---
# <a name="in-app-purchases"></a>In-App-Käufe

In-App-Käufe werden in hololens unterstützt, aber es gibt einige Aufgaben, die Sie einrichten müssen.

Um die in App-Purchase-Funktionalität nutzen zu können, müssen Sie folgende Schritte ausführen:
* Erstellen einer XAML- [2D-Ansicht](app-views.md) , die als Slate angezeigt wird
* Wechseln Sie zu dieser Option, um die Platzierung zu aktivieren, die die immersive Ansicht verlässt.
* Aufrufen der API: warten auf [currentapp. requestproductpurchaseasync ("durableitemiapname");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)

Diese API öffnet das Windows-Betriebssystem-Popup Fenster, das den Namen, die Beschreibung und den Preis in der APP anzeigt. Der Benutzer kann dann die Option Kaufoptionen auswählen. Nachdem die Aktion abgeschlossen ist, muss die APP die Benutzeroberfläche anzeigen, sodass der Benutzer wieder zu seiner [immersiven Ansicht](app-views.md)wechseln kann.

Für apps, die auf Desktop basierte Windows Mixed Reality-dashboardend abzielen, ist es nicht erforderlich, manuell zu einer XAML-Ansicht zu wechseln, bevor die requestproductpurchaseasync-API aufgerufen wird.
