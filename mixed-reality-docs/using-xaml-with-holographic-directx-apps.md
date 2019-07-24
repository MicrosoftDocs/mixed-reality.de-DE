---
title: Verwenden von XAML mit Holographic DirectX-apps
description: Erläutert die Auswirkungen des Wechsels zwischen 2D-XAML-Ansichten und immersiven Sichten in Ihrer DirectX-App sowie die effiziente Verwendung einer XAML-Ansicht und einer immersiven Ansicht.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, UWP, App-Ansichts Verwaltung, XAML, Tastatur, Exemplarische Vorgehensweise, DirectX
ms.openlocfilehash: 32b2feea0cb6b8aba972c1772451ca7b5b9946d5
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548704"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>Verwenden von XAML mit Holographic DirectX-apps

In diesem Thema wird erläutert, wie sich der Wechsel zwischen [2D-XAML-Ansichten und immersiven Sichten](app-views.md) in Ihrer DirectX-APP und die effiziente Verwendung einer XAML-Ansicht und der immersiven Ansicht Unternehmen.

## <a name="xaml-view-switching-overview"></a>Übersicht über das Wechseln der XAML-Ansicht

Bei hololens muss eine im allgemeinen immersive APP, die später eine 2D-XAML-Ansicht anzeigen kann, die XAML-Ansicht zunächst initialisieren und sofort zu einer immersiven Ansicht wechseln. Dies bedeutet, dass XAML geladen wird, bevor Ihre APP etwas Unternehmen kann. Dies führt zu einer geringen Erhöhung der Startzeit, und XAML belegt weiterhin Speicherplatz in Ihrem App-Prozess, während er sich im Hintergrund befindet. die Menge der Startverzögerung und Speicherauslastung hängt davon ab, was Ihre APP mit XAML durchführt, bevor Sie zur systemeigenen Ansicht gewechselt wird. Wenn Sie in Ihrem XAML-Start Code zunächst nur beginnen, wenn Sie mit der immersiven Ansicht beginnen, sollte die Auswirkung gering sein. Da Ihr holografisches Rendering direkt in der immersiven Ansicht erfolgt, vermeiden Sie außerdem alle XAML-bezogenen Einschränkungen für dieses Rendering.

Beachten Sie, dass die Speicherauslastung für CPU und GPU angerechnet wird. Direct3D 11 kann den virtuellen Grafikspeicher austauschen, kann jedoch möglicherweise einige oder alle XAML-GPU-Ressourcen nicht austauschen, und es kann zu einem spürbaren Leistungseinbußen kommen. In beiden Fällen bleibt das Laden von XAML-Features, die Sie nicht benötigen, für Ihre APP mehr Platz und bietet eine bessere Benutzer Leistung.

## <a name="xaml-view-switching-workflow"></a>Workflow für die XAML-Ansichts Umstellung

Der Workflow für eine APP, die direkt von XAML in den immersiven Modus wechselt, sieht wie folgt aus:
* Die APP startet in der 2D-XAML-Ansicht.
* Die XAML-Startsequenz der APP erkennt, ob das aktuelle System Holographic-Rendering unterstützt:
* Wenn dies der Fall ist, erstellt die APP die immersive Ansicht und bringt Sie sofort in den Vordergrund. Das Laden von XAML wird für alles, was auf Windows Mixed Reality-Geräten nicht erforderlich ist, ausgelassen, einschließlich aller Renderingklassen und Laden von Assets in der XAML-Ansicht. Wenn die APP XAML für Tastatureingaben verwendet, sollte diese Eingabe Seite weiterhin erstellt werden.
* Andernfalls kann die XAML-Ansicht das Unternehmen wie gewohnt fortsetzen.

## <a name="tip-for-rendering-graphics-across-both-views"></a>Tipp zum Rendern von Grafiken in beiden Ansichten

Wenn Ihre APP eine gewisse Menge an Rendering in DirectX für die XAML-Ansicht in Windows Mixed Reality implementieren muss, besteht die beste Lösung darin, einen Renderer zu erstellen, der mit beiden Ansichten arbeiten kann. Der Renderer muss eine Instanz sein, auf die von beiden Ansichten aus zugegriffen werden kann, und Sie sollte in der Lage sein, zwischen dem 2D-und dem Holographic-Rendering zu wechseln. Auf diese Weise werden GPU-Assets nur einmal geladen. Dies reduziert die Ladezeiten, die Arbeitsspeicher Auswirkung und die Menge der Ressourcen, die beim Wechseln von Sichten ausgetauscht werden sollen.
