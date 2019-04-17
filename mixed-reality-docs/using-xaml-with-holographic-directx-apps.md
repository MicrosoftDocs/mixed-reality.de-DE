---
title: Verwenden von XAML mit holographic DirectX-apps
description: Erläutert die Auswirkung des Wechsels zwischen 2D XAML und immersive Ansichten in Ihrer DirectX-app, und wie Sie eine XAML-Ansichts- und immersive Ansicht effizient nutzen.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows mixed Reality, UWP-app anzeigen, Verwaltung, Xaml, Tastatur, exemplarische Vorgehensweise, DirectX
ms.openlocfilehash: 32b2feea0cb6b8aba972c1772451ca7b5b9946d5
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593700"
---
# <a name="using-xaml-with-holographic-directx-apps"></a>Verwenden von XAML mit holographic DirectX-apps

In diesem Thema wird erläutert, den Auswirkungen dieses Wechsels zwischen [2D XAML und immersive Ansichten](app-views.md) in DirectX-Apps, und wie Sie eine XAML-Ansichts- und immersive Ansicht effizient nutzen.

## <a name="xaml-view-switching-overview"></a>Wechseln der Übersicht über die XAML-Ansicht

Für HoloLens muss eine in der Regel immersive-app, die später eine Direct2D-XAML-Ansicht anzeigen kann initialisieren zuerst diese XAML-Ansicht und sofort in eine immersive Ansicht wechseln Sie von dort aus. Dies bedeutet, dass XAML geladen werden, bevor Ihre app alles tun kann. Daher wird eine geringe Leistungssteigerung Ihrer Startzeit und XAML wird fortgesetzt, belegen Sie Speicherplatz in Ihrem app-Prozess aus, während es im Hintergrund befindet; die Menge der Verzögerung beim Systemstart und des Speichers, von denen abhängt, dass die Nutzung Ihrer app, die mit XAML ausführt wird, bevor Sie in der einheitlichen Ansicht wechseln. Wenn nichts in Ihrer XAML-Startvorgangs Code zuerst mit der Ausnahme die immersive Ansicht starten, sollten die Auswirkungen auf kleinere sein. Da das holographic Rendering direkt auf die immersive Sicht ausgeführt wird, werden Sie außerdem XAML-bezogene Einschränkungen hinsichtlich der, Rendern vermeiden.

Beachten Sie, dass die Auslastung des Speichers für CPU- und GPU zählt. Direct3D 11 ist tauschen, virtuelle Grafikspeicher, aber es möglicherweise nicht um einige oder alle der XAML-GPU-Ressourcen zu wechseln, und möglicherweise gibt es einen spürbaren Leistungseinbußen. In beiden Fällen benötigen nicht geladen. alle XAML-Features Sie nicht mehr Platz für Ihre app und eine größere benutzerfreundlichkeit bereitzustellen.

## <a name="xaml-view-switching-workflow"></a>Wechseln von Workflow XAML-Ansicht

Der Workflow für eine app, durchläuft direkt in XAML immersiven Modus ist, etwa so:
* Die app gestartet wird, in der 2D XAML-Ansicht.
* Die app XAML-Startsequenz wird erkannt, ob das aktuelle System holographic komplexe Darstellung unterstützt:
* Wenn dies der Fall ist, wird die app erstellt die Sicht für immersive und schaltet sie sofort in den Vordergrund gestellt. Laden von XAML wird für alle nicht erforderlichen Daten auf Windows Mixed Reality-Geräte, einschließlich Renderingklassen und Laden Sie in der XAML-Ansicht von Asset übersprungen. Wenn die app für die Tastatureingabe XAML verwendet, sollte diese Eingabeseite noch erstellt werden.
* Wenn dies nicht der Fall ist, wird die XAML-Ansicht mit Unternehmen wie üblich fortfahren kann.

## <a name="tip-for-rendering-graphics-across-both-views"></a>Tipp für beide Ansichten Rendern von Grafiken

Wenn Ihre app gewisse Rendering in DirectX für die XAML-Ansicht in Windows Mixed Reality zu implementieren muss, ist es am besten, einen Renderer erstellen, die mit den beiden Ansichten arbeiten können. Der Renderer muss eine Instanz, die von beiden Ansichten zugegriffen werden kann, und es muss zwischen 2D- und holographic Rendering wechseln. Auf diese Weise nur einmal - GPU-Ressourcen geladen wird reduziert Ladezeiten, Auswirkungen auf den Arbeitsspeicher und die Menge der Ressourcen, die ausgetauscht werden sollen, wenn die Ansicht gewechselt.
