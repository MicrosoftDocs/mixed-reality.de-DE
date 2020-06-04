---
title: Spracheingabe
description: Tutorial zum Einrichten und Verwenden von Spracheingaben in hololens 2 und Unreal Engine
author: hferrone
ms.author: v-haferr
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, Unreal, Unreal Engine 4, UE4, hololens 2, Voice, Voice Input, Spracherkennung, gemischte Realität, Entwicklung, Features, Dokumentation, Anleitungen, holograms, Spieleentwicklung
ms.openlocfilehash: c5de0cd912674ccd681fd398fb6fe5fd345ab6f2
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330632"
---
# <a name="voice-input-in-unreal"></a><span data-ttu-id="20754-104">Spracheingabe in Unreal</span><span class="sxs-lookup"><span data-stu-id="20754-104">Voice Input in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="20754-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="20754-105">Overview</span></span>
<span data-ttu-id="20754-106">Mit der Spracheingabe können Sie mit einem – Hologramm interagieren, ohne Handgesten verwenden zu müssen, und werden auf hololens (1st Gen) und hololens 2 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="20754-106">Voice input allows you to interact with a hologram without having to use hand gestures and is supported on HoloLens (1st Gen) and HoloLens 2.</span></span> <span data-ttu-id="20754-107">Sie wird von der gleichen Engine unterstützt, die Sprache in allen anderen universellen Windows-Apps unterstützt, und Sie kann der Art und Weise, wie Sie in gemischter Realität interagieren, ein natürliches Gefühl verleihen</span><span class="sxs-lookup"><span data-stu-id="20754-107">It's powered by the same engine that supports speech in all other Universal Windows Apps and can add a natural feeling to the way you interact in mixed reality.</span></span> 

<span data-ttu-id="20754-108">Zu den unterstützten sprach Features gehören:</span><span class="sxs-lookup"><span data-stu-id="20754-108">Supported voice features include:</span></span>
- <span data-ttu-id="20754-109">Der [SELECT-Befehl](https://docs.microsoft.com/windows/mixed-reality/voice-input#the-select-command)</span><span class="sxs-lookup"><span data-stu-id="20754-109">The [Select command](https://docs.microsoft.com/windows/mixed-reality/voice-input#the-select-command)</span></span>
- [<span data-ttu-id="20754-110">Hallo, Cortana</span><span class="sxs-lookup"><span data-stu-id="20754-110">Hey, Cortana</span></span>](https://docs.microsoft.com/windows/mixed-reality/voice-input#hey-cortana)
- <span data-ttu-id="20754-111">"Weitere Informationen" für die Interaktion mit Schaltflächen und Bezeichnungen</span><span class="sxs-lookup"><span data-stu-id="20754-111">"See it, say it" for button and label interaction</span></span>
- <span data-ttu-id="20754-112">Diktieren</span><span class="sxs-lookup"><span data-stu-id="20754-112">Dictation</span></span>

<span data-ttu-id="20754-113">Weitere Informationen finden Sie in der Dokumentation zur Haupt [Spracheingabe](voice-input.md) .</span><span class="sxs-lookup"><span data-stu-id="20754-113">For more information, check out the main [Voice Input](voice-input.md) documentation.</span></span>

## <a name="enabling-speech-recognition"></a><span data-ttu-id="20754-114">Aktivieren der Spracherkennung</span><span class="sxs-lookup"><span data-stu-id="20754-114">Enabling Speech Recognition</span></span>

<span data-ttu-id="20754-115">So aktivieren Sie die Spracherkennung in hololens:</span><span class="sxs-lookup"><span data-stu-id="20754-115">To enable speech recognition on HoloLens:</span></span>
1. <span data-ttu-id="20754-116">Wählen Sie **Projekteinstellungen > Plattform > hololens > Funktionen** aus, und aktivieren Sie das **Mikrofon**.</span><span class="sxs-lookup"><span data-stu-id="20754-116">Select **Project Settings > Platform > HoloLens > Capabilities** and enable **Microphone**.</span></span> 
2. <span data-ttu-id="20754-117">Aktivieren Sie die Spracherkennung in den **Einstellungen > Datenschutz > Sprache** , und wählen Sie **Englisch**aus.</span><span class="sxs-lookup"><span data-stu-id="20754-117">Enabled speech recogniztion in **Settings > Privacy > Speech** and select **English**.</span></span>

> [!NOTE]
> <span data-ttu-id="20754-118">Die Spracherkennung funktioniert immer in der in der App " **Einstellungen** " konfigurierten Windows-Anzeige Sprache.</span><span class="sxs-lookup"><span data-stu-id="20754-118">Speech recognition always functions in the Windows display language configured in the **Settings** app.</span></span> <span data-ttu-id="20754-119">Es wird empfohlen, dass Sie auch die **Online Spracherkennung** für die beste Dienst Qualität aktivieren.</span><span class="sxs-lookup"><span data-stu-id="20754-119">It’s recommended that you also enable **Online speech recognition** for the best service quality.</span></span>

![Einstellungen für die Windows-Spracherkennung](images/unreal/speech-recognition-settings.png)

3. <span data-ttu-id="20754-121">Ein Dialogfeld wird angezeigt, wenn die Anwendung zum ersten Mal gefragt wird, ob Sie das Mikrofon aktivieren möchten.</span><span class="sxs-lookup"><span data-stu-id="20754-121">A dialog will show up when the application first starts to ask if you want to enable the microphone.</span></span> <span data-ttu-id="20754-122">Wenn Sie **Ja** auswählen, wird die Spracheingabe in der APP gestartet.</span><span class="sxs-lookup"><span data-stu-id="20754-122">Selecting **Yes** starts voice input in the app.</span></span>

<span data-ttu-id="20754-123">Die Spracheingabe erfordert keine speziellen Windows Mixed Reality-APIs. Es basiert auf der vorhandenen API für die [Eingabe](https://docs.unrealengine.com/Gameplay/Input/index.html) Zuordnung von Unreal Engine 4.</span><span class="sxs-lookup"><span data-stu-id="20754-123">Voice input doesn’t require any special Windows Mixed Reality APIs; it's built on the existing Unreal Engine 4 [Input](https://docs.unrealengine.com/Gameplay/Input/index.html) mapping API.</span></span> 

## <a name="adding-speech-mappings"></a><span data-ttu-id="20754-124">Hinzufügen von sprach Zuordnungen</span><span class="sxs-lookup"><span data-stu-id="20754-124">Adding Speech Mappings</span></span>
<span data-ttu-id="20754-125">Das Verbinden von Sprache und Aktion ist ein wichtiger Schritt bei der Verwendung von Spracheingaben.</span><span class="sxs-lookup"><span data-stu-id="20754-125">Connecting speech to action is an important step when using voice input.</span></span> <span data-ttu-id="20754-126">Diese Zuordnungen überwachen die APP auf sprach Schlüsselwörter, die ein Benutzer möglicherweise anweist, und lösen dann eine verknüpfte Aktion aus.</span><span class="sxs-lookup"><span data-stu-id="20754-126">These mappings monitor the app for speech keywords that a user might say, then fire off a linked action.</span></span> <span data-ttu-id="20754-127">Sie finden sprach Zuordnungen wie folgt:</span><span class="sxs-lookup"><span data-stu-id="20754-127">You can find Speech Mappings by:</span></span>
1. <span data-ttu-id="20754-128">Wählen Sie **> Projekteinstellungen bearbeiten**aus, Scrollen Sie zum Abschnitt **Engine** , und klicken Sie auf **Eingabe**.</span><span class="sxs-lookup"><span data-stu-id="20754-128">Selecting **Edit > Project Settings**, scrolling to the **Engine** section, and clicking **Input**.</span></span>

<span data-ttu-id="20754-129">So fügen Sie eine neue sprach Zuordnung für einen Jump-Befehl hinzu:</span><span class="sxs-lookup"><span data-stu-id="20754-129">To add a new Speech Mapping for a jump command:</span></span>
1. <span data-ttu-id="20754-130">Klicken Sie auf das **+** Symbol neben **Array Elemente** , und füllen Sie die folgenden Werte aus:</span><span class="sxs-lookup"><span data-stu-id="20754-130">Click the **+** icon next to **Array elements** and fill out the following values:</span></span>
    * <span data-ttu-id="20754-131">**jumpword** für **Aktions Name**</span><span class="sxs-lookup"><span data-stu-id="20754-131">**jumpWord** for **Action Name**</span></span>
    * <span data-ttu-id="20754-132">**springen** für **sprach Schlüsselwort**</span><span class="sxs-lookup"><span data-stu-id="20754-132">**jump** for **Speech Keyword**</span></span>

> [!NOTE]
> <span data-ttu-id="20754-133">Alle englischen Wörter oder kurzsätze können als Schlüsselwort verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="20754-133">Any English word(s) or short sentence(s) can be used as a keyword.</span></span> 

![UE4-Engine-Eingabeeinstellungen](images/unreal/engine-input.png)

<span data-ttu-id="20754-135">Sprach Zuordnungen können als Eingabe Komponenten wie Aktions-oder Achsen Zuordnungen oder als Blueprint-Knoten im Ereignis Diagramm verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="20754-135">Speech Mappings can be used as Input components like Action or Axis Mappings or as blueprint nodes in the Event Graph.</span></span> <span data-ttu-id="20754-136">Beispielsweise können Sie den Jump-Befehl verknüpfen, um zwei verschiedene Protokolle auszugeben, je nachdem, wann das Wort gesprochen wird:</span><span class="sxs-lookup"><span data-stu-id="20754-136">For example, you could link the jump command to print out two different logs depending on when the word is spoken:</span></span>

1. <span data-ttu-id="20754-137">Doppelklicken Sie auf eine Blaupause, um Sie im **Ereignis Diagramm**zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="20754-137">Double-click a blueprint to open it in the **Event Graph**.</span></span>
2. <span data-ttu-id="20754-138">**Klicken Sie mit der rechten Maustaste** , und suchen Sie nach dem **Aktions Namen** ihrer sprach Zuordnung (in diesem Fall **jumpword**), und drücken Sie dann die **Eingabe**Taste.</span><span class="sxs-lookup"><span data-stu-id="20754-138">**Right-click** and search for the **Action Name** of your speech mapping (in this case **jumpWord**), then hit **Enter**.</span></span> <span data-ttu-id="20754-139">Dadurch wird dem Diagramm ein **Eingabe Aktions** Knoten hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="20754-139">This adds an **Input Action** node to the graph.</span></span>
3. <span data-ttu-id="20754-140">Ziehen Sie die **gedrückte** PIN per Drag & Drop auf den Knoten **Druck Zeichenfolge** , wie in der folgenden Abbildung dargestellt</span><span class="sxs-lookup"><span data-stu-id="20754-140">Drag and drop the **Pressed** pin to **Print String** node as shown in the image below.</span></span> <span data-ttu-id="20754-141">Sie können die **freigegebene** Pin leer lassen, ohne dass für sprach Zuordnungen etwas ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="20754-141">You can leave the **Released** pin empty, it won't execute anything for speech mappings.</span></span>
 
![Einfache Aktion für Stimme](images/unreal/voice-input-img-03.png)

4. <span data-ttu-id="20754-143">Spielen Sie die APP, sagen Sie, das Wort **springt** , und sehen Sie sich an, dass die Konsole die Protokolle ausgibt</span><span class="sxs-lookup"><span data-stu-id="20754-143">Play the app, say the word **jump** and watch the console print out the logs!</span></span>

<span data-ttu-id="20754-144">Das ist alles, was Sie benötigen, um Ihren hololens-apps in Unreal Spracheingaben hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="20754-144">That's all the setup you'll need to start adding voice input to your HoloLens apps in Unreal.</span></span> <span data-ttu-id="20754-145">Weitere Informationen zu Sprache und Interaktivität finden Sie unter den folgenden Links. Stellen Sie sicher, dass Sie sich über die Benutzeroberflächen Gedanken machen, die Sie für Ihre Benutzer erstellen.</span><span class="sxs-lookup"><span data-stu-id="20754-145">You can find more information on speech and interactivity can be found at the links below, and be sure to think about the experience you're creating for your users.</span></span>

## <a name="see-also"></a><span data-ttu-id="20754-146">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="20754-146">See also</span></span>
* [<span data-ttu-id="20754-147">Anvisieren und Ausführen</span><span class="sxs-lookup"><span data-stu-id="20754-147">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="20754-148">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="20754-148">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="20754-149">MR-Eingabe 212: Sprache</span><span class="sxs-lookup"><span data-stu-id="20754-149">MR Input 212: Voice</span></span>](holograms-212.md)
