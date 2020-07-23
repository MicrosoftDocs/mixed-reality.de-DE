---
title: Streaming in Unreal
description: Eine Anleitung für das Streamen zu HoloLens 2 in Unreal
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Streaming, PC, Holographic App Remoting, Holographic Remoting Player, Dokumentation
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: d25efbcf83e45749cc4eb8b99581b71105c59c9d
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86303531"
---
# <a name="streaming-in-unreal"></a><span data-ttu-id="c9824-104">Streaming in Unreal</span><span class="sxs-lookup"><span data-stu-id="c9824-104">Streaming in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="c9824-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="c9824-105">Overview</span></span>
<span data-ttu-id="c9824-106">Das Streamen von einem PC zu HoloLens bietet hauptsächlich zwei Vorteile:</span><span class="sxs-lookup"><span data-stu-id="c9824-106">Streaming from a PC to HoloLens provides two major advantages:</span></span> 
* <span data-ttu-id="c9824-107">Es ermöglicht Ihrer Mixed Reality-App die Nutzung der Rechenleistung Ihres PCs.</span><span class="sxs-lookup"><span data-stu-id="c9824-107">It lets your mixed reality app take advantage of your PCs computational power.</span></span> 
* <span data-ttu-id="c9824-108">Es verkürzt die Iterationszeiten bei der Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="c9824-108">It helps speed up development iteration time.</span></span> 

<span data-ttu-id="c9824-109">Für den Einstieg müssen Sie den [Holographic Remoting Player](holographic-remoting-player.md) auf Ihr HoloLens-Gerät herunterladen.</span><span class="sxs-lookup"><span data-stu-id="c9824-109">To get started, you'll need to download the [Holographic Remoting Player](holographic-remoting-player.md) to your HoloLens device.</span></span> <span data-ttu-id="c9824-110">Dadurch kann Ihre App direkt aus den folgenden Quellen zum Remoteplayer auf Ihrer HoloLens streamen:</span><span class="sxs-lookup"><span data-stu-id="c9824-110">This allows your app to stream  directly to the remoting player on your HoloLens from the following sources:</span></span>

* <span data-ttu-id="c9824-111">dem Unreal Engine-Editor</span><span class="sxs-lookup"><span data-stu-id="c9824-111">The Unreal Engine editor</span></span>
* <span data-ttu-id="c9824-112">einer verpackten Windows-Programmdatei</span><span class="sxs-lookup"><span data-stu-id="c9824-112">A packaged Windows executable</span></span> 

<span data-ttu-id="c9824-113">Beim Streamen haben Sie Zugriff auf nahezu alle der HoloLens-Funktionen, die Ihnen auch beim Ausführen einer Anwendung auf einem Gerät zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="c9824-113">When streaming, you have access to almost all of the same HoloLens capabilities as you would when running an application on a device.</span></span> <span data-ttu-id="c9824-114">Dies schließt [Handgelenksnachverfolgung](unreal-hand-tracking.md) (bei einer HoloLens 2), [Räumliche Abbildung](unreal-spatial-mapping.md) und [Raumanker](unreal-spatial-anchors.md) (Spatial Anchors) ein, die Funktionen in dieser [Einschränkungsliste](holographic-remoting-troubleshooting.md) sind jedoch ausgenommen.</span><span class="sxs-lookup"><span data-stu-id="c9824-114">This includes [hand joint tracking](unreal-hand-tracking.md) (if you're on a HoloLens 2), [spatial mapping](unreal-spatial-mapping.md), and [spatial anchors](unreal-spatial-anchors.md), but leaves out the features on this [list of limitations](holographic-remoting-troubleshooting.md).</span></span> 

> [!NOTE]
> * <span data-ttu-id="c9824-115">Die Streamingqualität hängt stark von der Feldstärke Ihres WLAN-Netzwerks ab.</span><span class="sxs-lookup"><span data-stu-id="c9824-115">Streaming quality is highly dependent on the strength of your wifi network.</span></span>
> * <span data-ttu-id="c9824-116">Alle Funktionen werden automatisch für den Holographic Remoting Player aktiviert.</span><span class="sxs-lookup"><span data-stu-id="c9824-116">All capabilities are automatically enabled for the holographic remoting player.</span></span> <span data-ttu-id="c9824-117">Wenn Sie auf eine Funktion stoßen, die per Streaming nur mit einer Benutzerberechtigung arbeitet, diese bei Ausführung auf dem Gerät aber nicht benötigt (Beispiel: Eye Tracking), vergewissern Sie sich in den Projekteinstellungen, dass Sie die richtigen Funktionen aktiviert haben.</span><span class="sxs-lookup"><span data-stu-id="c9824-117">If you find a capability that requires user permission (ex: eye tracking) to be working over streaming but not when running on device, check to ensure you've enabled the proper capabilities under your project settings.</span></span>

## <a name="device-support"></a><span data-ttu-id="c9824-118">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="c9824-118">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c9824-119"><strong>Quelle</strong></span><span class="sxs-lookup"><span data-stu-id="c9824-119"><strong>Source</strong></span></span></td>
        <td><span data-ttu-id="c9824-120"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="c9824-120"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="c9824-121"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="c9824-121"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="c9824-122"><strong>Immersive Headsets</strong></span><span class="sxs-lookup"><span data-stu-id="c9824-122"><strong>Immersive Headsets</strong></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c9824-123">Unreal-Editor</span><span class="sxs-lookup"><span data-stu-id="c9824-123">Unreal editor</span></span></td>
        <td><span data-ttu-id="c9824-124">✔️</span><span class="sxs-lookup"><span data-stu-id="c9824-124">✔️</span></span></td>
        <td><span data-ttu-id="c9824-125">✔️</span><span class="sxs-lookup"><span data-stu-id="c9824-125">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="c9824-126">Windows-Paket</span><span class="sxs-lookup"><span data-stu-id="c9824-126">Windows package</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="c9824-127">✔️</span><span class="sxs-lookup"><span data-stu-id="c9824-127">✔️</span></span></td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a><span data-ttu-id="c9824-128">Streaming vom Unreal-Editor</span><span class="sxs-lookup"><span data-stu-id="c9824-128">Streaming from the Unreal editor</span></span>

<span data-ttu-id="c9824-129">Als Entwickler werden Sie feststellen, dass das Streaming vom Unreal-Editor zu Ihrem HoloLens-Gerät beim Testen große Vorteile bietet, nämlich dass Sie nicht mehr auf das Erstellen und Bereitstellen Ihrer App warten müssen, bevor Sie Ihre Updates ausprobieren.</span><span class="sxs-lookup"><span data-stu-id="c9824-129">As a developer, you'll find that streaming from the Unreal editor to your HoloLens device provides big benefits when testing, namely that you no longer have to wait for your app to build and deploy before trying out your updates.</span></span>

<span data-ttu-id="c9824-130">Im letzten Abschnitt der Tutorialreihe „Erste Schritte mit Unreal“ finden Sie ausführliche Anweisungen zum [Streamen vom Unreal-Editor](unreal-uxt-ch6.md#device-only-streaming).</span><span class="sxs-lookup"><span data-stu-id="c9824-130">You can find detailed instructions on [streaming from the Unreal editor](unreal-uxt-ch6.md#device-only-streaming) in the last section of the Getting Started with Unreal tutorial series.</span></span>

## <a name="streaming-from-a-packaged-windows-executable"></a><span data-ttu-id="c9824-131">Streamen von einer verpackten Windows-Programmdatei</span><span class="sxs-lookup"><span data-stu-id="c9824-131">Streaming from a packaged Windows executable</span></span>

<span data-ttu-id="c9824-132">Seit Unreal 4.25.1 können Sie Ihre App aus einer verpackten Windows-Programmdatei zu einem HoloLens 2-Gerät streamen, indem Sie die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="c9824-132">As of Unreal 4.25.1, you can stream your app to a HoloLens 2 device from a packaged Windows executable by following the steps below:</span></span> 

1. <span data-ttu-id="c9824-133">Wechseln Sie im Editormenü zu **Datei > Paketprojekt > Windows**.</span><span class="sxs-lookup"><span data-stu-id="c9824-133">Go to **File > Package Project > Windows** in the editor menu.</span></span> 
    * <span data-ttu-id="c9824-134">Wählen Sie einen Speicherort aus, um Ihr Paket zu speichern, und klicken Sie auf **Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="c9824-134">Choose a location to save your package and click **Select Folder**.</span></span>

2. <span data-ttu-id="c9824-135">Nachdem das Erstellen des Pakets abgeschlossen wurde, öffnen Sie den **Holographic Remoting Player** auf Ihrer HoloLens 2, und notieren Sie die IP-Adresse.</span><span class="sxs-lookup"><span data-stu-id="c9824-135">Once the package has finished building, open the **Holographic Remoting Player** on your HoloLens 2 and make note of the IP Address.</span></span> 
3. <span data-ttu-id="c9824-136">Lassen Sie den **Holographic Remoting Player** geöffnet, und verwenden Sie die Eingabeaufforderung zum:</span><span class="sxs-lookup"><span data-stu-id="c9824-136">Leave the **Holographic Remoting Player** open and use the command line prompt to:</span></span> 
    * <span data-ttu-id="c9824-137">Wechseln in das lokale Verzeichnis, in dem Sie das Paket gespeichert haben.</span><span class="sxs-lookup"><span data-stu-id="c9824-137">cd into the local directory where you saved your package.</span></span>
    * <span data-ttu-id="c9824-138">Geben Sie den folgenden Befehl ein: ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span><span class="sxs-lookup"><span data-stu-id="c9824-138">Enter the following command: ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span></span>

> [!NOTE]
> <span data-ttu-id="c9824-139">Der Anwendungsname in Ihren Projekteinstellungen sollte automatisch zum Erstellen des Windows-Pakets verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c9824-139">The application name in your project settings should be automatically used to create the Windows package.</span></span> <span data-ttu-id="c9824-140">Wenn diese aus irgendeinem Grund verschieden sind, verwenden Sie den Namen der Windows-Programmdatei in der Eingabeaufforderung.</span><span class="sxs-lookup"><span data-stu-id="c9824-140">If these are different for some reason, use the Windows executable name in the command prompt.</span></span>

<span data-ttu-id="c9824-141">Drücken Sie die EINGABETASTE, und sehen Sie, wie das Streamen Ihrer Anwendung beginnt!</span><span class="sxs-lookup"><span data-stu-id="c9824-141">Hit enter and watch your application start streaming!</span></span>

## <a name="see-also"></a><span data-ttu-id="c9824-142">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c9824-142">See also</span></span>
* [<span data-ttu-id="c9824-143">Holographic Remoting: Versionsverlauf</span><span class="sxs-lookup"><span data-stu-id="c9824-143">Holographic remoting version history</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="c9824-144">Schreiben einer benutzerdefinierten Holographic Remoting Player-App</span><span class="sxs-lookup"><span data-stu-id="c9824-144">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="c9824-145">Einrichten einer sicheren Verbindung mit Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="c9824-145">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
