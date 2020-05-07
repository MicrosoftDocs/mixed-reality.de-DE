---
title: Spracheingabe
description: Erläutert die Verwendung von Spracheingaben.
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, hololens
ms.openlocfilehash: d61a9f9d40c76c8872ff0a1b39d65f95ae88d2b7
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835311"
---
# <a name="voice-input"></a>Spracheingabe

Um die Spracherkennung in hololens zu aktivieren, muss der Entwickler "Mikrofon" im Unreal-Editor Unterprojekt Einstellungen > Plattform > hololens > Funktionen aktivieren. Auf dem Gerät muss auch die Spracherkennung in den Einstellungen > Datenschutz > Sprache aktiviert sein und die englische Sprache verwenden.

![Einstellungen für die Windows-Spracherkennung](images/unreal/speech-recognition-settings.png)

Es wird empfohlen, die Online Spracherkennung auch für die bestmögliche Qualität des Dienstanbieter zu aktivieren. Technische Details zur Spracherkennung in hololens finden Sie [hier](voice-input.md) .

Dem Benutzer wird dann ein Dialogfeld angezeigt, in dem das Mikrofon beim ersten Start der Anwendung aktiviert wird. Wenn ein Benutzer "Ja" auswählt, beginnt die Anwendung mit der Spracheingabe.

Die Spracheingabe erfordert keine spezielle Windows Mixed Reality-API und basiert stattdessen auf der vorhandenen API für die Eingabe Zuordnung von Unreal Engine 4. Details zur Verwendung der Eingabe-API finden Sie [hier](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html) .

Sprach Zuordnungen wurden dem Bindungs Abschnitt der Engine – Input unter Action and Axis Mappings hinzugefügt. 

![UE4-Engine-Eingabeeinstellungen](images/unreal/engine-input.png)
 
Im folgenden finden Sie ein Beispiel für eine hinzugefügte Überwachung der Welt "Jump". Alle englischen Wörter oder kurzen Sätze können verwendet werden. 

Nachdem eine sprach Zuordnung über Projekteinstellungen hinzugefügt wurde, kann ein Entwickler standardmäßige Unreal Logic verwenden, um die Eingabe zu verarbeiten, wie im folgenden Beispiel gezeigt: 
 
![Einfache Aktion für Stimme](images/unreal/input-action-bp.png)
