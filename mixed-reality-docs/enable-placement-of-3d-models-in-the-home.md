---
title: Aktivieren Sie die Platzierung von 3D-Modellen zu Hause
description: Wie 3D-Modelle aus Ihrer Website oder Anwendung in die Windows Mixed Reality home abgelegt.
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, Modell, an Startseite, Ort, weltweit, Modellierung, mixed Reality home, Web, app
ms.openlocfilehash: 3a50353aae8e03c3ebb3ee9ec2f642f21836e925
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605024"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a>Aktivieren Sie die Platzierung von 3D-Modellen in die gemischte Realität home

> [!NOTE]
> Dieses Feature wurde hinzugefügt, als Teil der [Windows 10 April 2018 Update](release-notes-april-2018.md). Ältere Versionen von Windows sind nicht mit diesem Feature kompatibel.

Die [Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md) ist der Ausgangspunkt, in denen Benutzer weitergeleitet, vor dem Starten von Anwendungen. In einigen Szenarien ermöglichen Direct2D-apps (z. B. die app Hologramme) Platzierung von 3D-Modellen direkt in die mixed Reality-Homepage, Ergänzungen oder zur weiteren Untersuchung in vollständigem 3D. Die *Modell Protokoll hinzufügen,* können Sie ein 3D-Modell auf Ihrer Website oder Anwendung direkt in die Windows Mixed Reality home, senden, wo es beibehalten werden wie [3D app-startfeldern von](3d-app-launcher-design-guidance.md), Direct2D-apps und -Hologramme. 

Z. B. Wenn Sie einer Anwendung, auf einen Katalog mit 3D Möbel für das Entwerfen von einem Leerzeichen entwickeln, können die *Modell Protokoll hinzufügen,* , dass Benutzer diese 3D Möbel Modelle aus dem Katalog zu platzieren können. Sobald in der Welt platziert wird, können Benutzer verschieben, Ändern der Größe und entfernen diese 3D-Modelle genau wie andere Hologramme zu Hause. Dieser Artikel bietet einen Überblick über die Implementierung der *Modell Protokoll hinzufügen,* , damit Sie beginnen können Benutzern ermöglichen, ihre Welt 3D-Objekte aus Ihrer app oder im Internet zu ergänzen.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Feature</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td>Modell-Protokoll hinzufügen</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="overview"></a>Übersicht

Es gibt 2 Schritte aus, um die Platzierung von 3D-Modellen in die Windows Mixed Reality home aktivieren:
1. [Stellen Sie sicher, Ihre 3D-Modell ist kompatibel mit der Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).
2. Implementieren der *Modell Protokoll hinzufügen,* in Ihrer Anwendung oder Webseite (dieser Artikel).

## <a name="implementing-the-add-model-protocol"></a>Implementieren der *Modell Protokoll hinzufügen*

Nachdem Sie haben eine [kompatibel 3D-Modell](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), können Sie implementieren die *Modell Protokoll hinzufügen,* durch den folgenden URI von einer Webseite oder Anwendung zu aktivieren:

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

Wenn der URI mit einer Remoteressource verweist, wird dann automatisch heruntergeladen und zu Hause platziert. Lokale Ressourcen werden in app-Datenordner der mixed Reality-Startseite kopiert werden, bevor Sie zu Hause platziert wird. Es wird empfohlen, Entwerfen Ihre Erfahrung mit Konto für Szenarien, in denen der Benutzer eine ältere Version von Windows kann, die diese Funktion nicht unterstützt ausgeführt werden, durch die Schaltfläche ausblenden oder deaktivieren es nach Möglichkeit. 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a>Aufrufen der *Modell Protokoll hinzufügen,* aus einer universellen Windows-Plattform-app:

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a>Aufrufen der *Modell Protokoll hinzufügen,* über eine Webseite:

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a>Überlegungen für immersive Headsets von (VR)

* Für immersive Headsets (VR), Mixed Reality Portal muss nicht vor dem Aufrufen ausgeführt wird, werden die *Modell Protokoll hinzufügen,*. In diesem Fall die *Modell Protokoll hinzufügen,* startet das Mixed Reality-Portal und platzieren Sie das Objekt direkt, in denen die Kopfhörer sucht nach der Sie in der die gemischte Realität Startseite gelangen. 
* Beim Aufrufen der *Modell Protokoll hinzufügen,* auf dem Desktop mit dem Mixed Reality-Portal bereits ausgeführt wird, stellen Sie sicher, dass die Kopfhörer "aktiv" ist. Wenn dies nicht der Fall ist, wird die Platzierung nicht erfolgreich ausgeführt werden. 

## <a name="see-also"></a>Siehe auch

* [Erstellen von 3D-Modellen für die Verwendung zu Hause Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Navigieren Sie in der Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md)
