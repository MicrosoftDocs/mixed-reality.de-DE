---
title: Eingabe Portieren von Unity-Handbuch
description: Erfahren Sie, wie Eingaben für die Windows Mixed Reality in Unity behandelt.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Input "," Unity Portieren
ms.openlocfilehash: 20e8efa09d20b0a9eaa246015d9c185884f9c216
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595727"
---
# <a name="input-porting-guide-for-unity"></a>Eingabe Portieren von Unity-Handbuch

Sie können die Eingabe Logik Windows Mixed Reality mit einer der beiden Ansätzen von Unity allgemeine Input.GetButton/GetAxis-APIs, die auf mehreren Plattformen erstrecken, oder der Windows-spezifische XR portieren. WSA. Geben Sie die APIs, die umfangreichere Daten speziell für die Motion-Controllern und HoloLens Hände zu bieten.

## <a name="general-inputgetbuttongetaxis-apis"></a>Allgemeine Input.GetButton/GetAxis-APIs

Unity derzeit seine allgemeine Input.GetButton/Input.GetAxis-APIs verwendet, um Eingaben für verfügbar zu machen [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) und [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html). Wenn Ihre apps bereits für die Eingabe diese APIs verwenden, ist dies die einfachste Möglichkeit für die Unterstützung von Motion-Controller in Windows Mixed Reality: nur müssen Sie Schaltflächen und Achsen in der Eingabe-Manager neu zuordnen.

Weitere Informationen finden Sie unter den [Unity Schaltfläche/Achse Mapping Table (.NET Standard](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) und [Übersicht über die allgemeine Unity-APIs](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).

## <a name="windows-specific-xrwsainput-apis"></a>Windows-spezifische XR. WSA. Eingabe-APIs

Wenn Ihre app bereits benutzerdefinierte Eingabelogik für jede Plattform erstellt wurde, können Sie die Windows-spezifische räumliche Eingabe-APIs unter dem **UnityEngine.XR.WSA.Input** Namespace. Dadurch können Sie den Zugriff auf zusätzliche Informationen, z. B. Position Genauigkeit oder der datenquellenart, können Sie die praktische und Controllern, die voneinander entfernt auf HoloLens mitteilen.

Weitere Informationen finden Sie unter den [Übersicht über die UnityEngine.XR.WSA.Input APIs](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).

## <a name="grip-pose-vs-pointing-pose"></a>Ziehpunkt Haltung im Vergleich zu zeigenden Haltung

Windows Mixed Reality unterstützt Controller, die während der Übertragung in einer Vielzahl von Formfaktoren, des Controllers Entwurf unterscheidet sich in der Beziehung zwischen Hand-Position des Benutzers und der natürliche "Weiterleiten" Richtung dieser apps sollten mit auf beim Rendern der Controller.

Um diese Controller besser darstellen zu können, gibt es zwei Arten von ist, die Sie für jede Quelle Interaktion untersuchen können:

* Die **Ziehpunkt Haltung**, den Speicherort der dies im Handumdrehen einer Hand, die von einem HoloLens erkannt werden, oder dies mit einem Controller während der Übertragung im Handumdrehen darstellt.
    * Für immersive Headsets, diese Haltung wird am besten zum Rendern **des Benutzers manuell** oder **frei, die ein Objekt des Benutzers verfügen**, z. B. eine "sword" oder dem damoklesschwert.
    * Die **fassen Sie Position**: Der Schwerpunkt Palm, wenn der Controller natürlich mit angepasst nach links oder rechts zentriert die Position in den Ziehpunkt.
    * Die **fassen Sie die rechte Achse die Ausrichtung**: Wenn Sie Ihre Hand, um einen flachen 5 Finger Haltung bilden vollständig geöffnet haben, dem Strahl, der ist normal, zu Ihrem Palm (vorwärts vom linken Palm, rückwärts von rechts Palm)
    * Die **fassen Sie die Ausrichtung, vorwärts gerichtete Achse**: Wenn Sie Ihre Hand schließen, teilweise (als ob den Controller enthält), der vom Strahl, der "forward" über die Tube gebildet, indem die Finger nicht-Thumb-Steuerelement zeigt.
    * Die **fassen Sie die Ausrichtung des einrichten Achse**: Die nach-oben-Achse impliziert durch die rechts- und -Weiterleiten-Definitionen.
    * Sie können auf den Ziehpunkt Haltung über anbieterübergreifende Eingabe für die entweder von Unity-API zugreifen (**[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation**) oder über die Windows-spezifische API (**sourceState.sourcePose.TryGetPosition/Rotation**, der Haltung Ziehpunkt anfordern).
* Die **Zeiger Haltung**, das die Spitze des Controllers vorwärts zeigt darstellt.
    * Diese Haltung wird am besten verwendet, um Raycast beim **zeigen Sie auf der Benutzeroberfläche** Wenn Sie den Rendervorgang des Controllermodell selbst.
    * Der Zeiger Haltung ist derzeit nur über die Windows-spezifische API verfügbar (**sourceState.sourcePose.TryGetPosition/Rotation**, die Zeiger Haltung anfordern).

Diese Haltung, die die Koordinaten werden in Unity globalen Koordinaten angegeben.

## <a name="see-also"></a>Siehe auch
* [Motion-Controller](motion-controllers.md)
* [Gesten und Motion-Controller in Unity](gestures-and-motion-controllers-in-unity.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Portieren von Führungslinien](porting-guides.md)
