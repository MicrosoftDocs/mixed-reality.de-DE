---
title: Räumliche Sound in DirectX
description: Fügen Sie räumliche Sound für Ihre Windows Mixed Reality-apps, die basierend auf DirectX mithilfe der XAudio2 und xAPO audio-Bibliotheken.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows mixed Reality, räumliche Sound, XAudio2, low-Level-apps xAPO, audio-Bibliothek, exemplarische Vorgehensweise, DirectX
ms.openlocfilehash: 04d8c43ab400eed4cec5cbd848af5b888cb66e4b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605144"
---
# <a name="spatial-sound-in-directx"></a><span data-ttu-id="1bdb9-104">Räumliche Sound in DirectX</span><span class="sxs-lookup"><span data-stu-id="1bdb9-104">Spatial sound in DirectX</span></span>

<span data-ttu-id="1bdb9-105">Hinzufügen von räumlichen Sound zu Ihren Windows Mixed Reality-apps, die basierend auf DirectX verwenden die [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) und [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) audio-Bibliotheken.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-105">Add spatial sound to your Windows Mixed Reality apps based on DirectX by using the [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) and [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) audio libraries.</span></span>

<span data-ttu-id="1bdb9-106">In diesem Thema wird Beispielcode von der HolographicHRTFAudioSample verwendet.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-106">This topic uses sample code from the HolographicHRTFAudioSample.</span></span>

>[!NOTE]
><span data-ttu-id="1bdb9-107">Die Codeausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstatt C ++ 17-kompatible C++"/ WinRT", wie in der [ C++ holographic Projektvorlage](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="1bdb9-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="1bdb9-108">Die Konzepte sind Entsprechung für einen C++"/ WinRT"-Projekt, aber Sie benötigen, um den Code zu übersetzen.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="overview-of-head-relative-spatial-sound"></a><span data-ttu-id="1bdb9-109">Übersicht über die Head Relative räumliche Sound</span><span class="sxs-lookup"><span data-stu-id="1bdb9-109">Overview of Head Relative Spatial Sound</span></span>

<span data-ttu-id="1bdb9-110">Räumliche Sound wird als implementiert eine **audio Verarbeitung des Objekts (APO)** , verwendet eine **Head bezogene Übertragungsfunktion (HRTF)** filtern, um *spatialize* gewöhnliche Audiodatenstrom.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-110">Spatial sound is implemented as an **audio processing object (APO)** that uses a **head related transfer function (HRTF)** filter to *spatialize* an ordinary audio stream.</span></span>

<span data-ttu-id="1bdb9-111">Schließen Sie diese Headerdateien in "PCH.h", das Audio-APIs den Zugriff auf ein:</span><span class="sxs-lookup"><span data-stu-id="1bdb9-111">Include these header files in pch.h to access the audio APIs:</span></span>
* <span data-ttu-id="1bdb9-112">XAudio2.h</span><span class="sxs-lookup"><span data-stu-id="1bdb9-112">XAudio2.h</span></span>
* <span data-ttu-id="1bdb9-113">xapo.h</span><span class="sxs-lookup"><span data-stu-id="1bdb9-113">xapo.h</span></span>
* <span data-ttu-id="1bdb9-114">hrtfapoapi.h</span><span class="sxs-lookup"><span data-stu-id="1bdb9-114">hrtfapoapi.h</span></span>

<span data-ttu-id="1bdb9-115">So richten Sie räumliche sound</span><span class="sxs-lookup"><span data-stu-id="1bdb9-115">To set up spatial sound:</span></span>
1. <span data-ttu-id="1bdb9-116">Rufen Sie [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) zum Initialisieren einer neuen APO für HRTF-Audio.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-116">Call [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) to initialize a new APO for HRTF audio.</span></span>
2. <span data-ttu-id="1bdb9-117">Weisen Sie die [HRTF Parameter](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) und [HRTF Umgebung](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) den akustischen Merkmalen, der den räumlichen sound APO definieren.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-117">Assign the [HRTF parameters](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) and [HRTF environment](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) to define the acoustic characteristics of the spatial sound APO.</span></span>
3. <span data-ttu-id="1bdb9-118">Richten Sie die XAudio2-Engine zur Verarbeitung von HRTF.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-118">Set up the XAudio2 engine for HRTF processing.</span></span>
4. <span data-ttu-id="1bdb9-119">Erstellen Sie eine [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) Objekt, und rufen [starten](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).</span><span class="sxs-lookup"><span data-stu-id="1bdb9-119">Create an [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) object and call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).</span></span>

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a><span data-ttu-id="1bdb9-120">Implementieren von HRTF und räumliche Sound in DirectX-Apps</span><span class="sxs-lookup"><span data-stu-id="1bdb9-120">Implementing HRTF and spatial sound in your DirectX app</span></span>

<span data-ttu-id="1bdb9-121">Sie können eine Reihe von Effekten erzielen, durch Konfigurieren der HRTF APO mit verschiedenen Parametern und Umgebungen.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-121">You can achieve a variety of effects by configuring the HRTF APO with different parameters and environments.</span></span> <span data-ttu-id="1bdb9-122">Verwenden Sie den folgenden Code, um die Möglichkeiten zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-122">Use the following code to explore the possibilities.</span></span> <span data-ttu-id="1bdb9-123">Das Codebeispiel für die universelle Windows-Plattform hier herunterladen: [Sound Spatial-Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span><span class="sxs-lookup"><span data-stu-id="1bdb9-123">Download the Universal Windows Platform code sample from here: [Spatial sound sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span></span>

<span data-ttu-id="1bdb9-124">Hilfstypen sind in diesen Dateien verfügbar:</span><span class="sxs-lookup"><span data-stu-id="1bdb9-124">Helper types are available in these files:</span></span>
* <span data-ttu-id="1bdb9-125">[AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Audio-Dateien mit Media Foundation geladen und die [IMFSourceReader-Schnittstelle](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).</span><span class="sxs-lookup"><span data-stu-id="1bdb9-125">[AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Loads audio files by using Media Foundation and the [IMFSourceReader interface](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).</span></span>
* <span data-ttu-id="1bdb9-126">[XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implementiert die **SetupXAudio2** Funktion XAudio2 für die Verarbeitung von HRTF initialisiert werden.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-126">[XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implements the **SetupXAudio2** function to initialize XAudio2 for HRTF processing.</span></span>

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a><span data-ttu-id="1bdb9-127">Räumliche Sound für eine omnidirektionale Datenquelle hinzufügen</span><span class="sxs-lookup"><span data-stu-id="1bdb9-127">Add spatial sound for an omnidirectional source</span></span>

<span data-ttu-id="1bdb9-128">Einige Hologramme in der benutzerumgebung ausgeben Sound gleichmäßig in alle Richtungen.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-128">Some holograms in the user's surroundings emit sound equally in all directions.</span></span> <span data-ttu-id="1bdb9-129">Der folgende Code zeigt, wie ein APO omnidirektionale Sound Ausgabe initialisiert wird.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-129">The following code shows how to initialize an APO to emit omnidirectional sound.</span></span> <span data-ttu-id="1bdb9-130">In diesem Beispiel wenden wir dieses Konzept auf den sich drehenden Würfels in die Windows Holographic-app-Vorlage.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-130">In this example, we apply this concept to the spinning cube from the Windows Holographic app template.</span></span> <span data-ttu-id="1bdb9-131">Die vollständige codeauflistung finden Sie unter [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).</span><span class="sxs-lookup"><span data-stu-id="1bdb9-131">For the complete code listing, see [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).</span></span>

<span data-ttu-id="1bdb9-132">**Fensters räumliche sound-Engine unterstützt nur 48 KB Samplerate für die Wiedergabe. Die meisten Middleware-Programme wie Unity, Audiodateien automatisch in das gewünschte Format konvertiert, aber wenn Sie auf niedrigeren Ebenen in die audio-System oder machen Ihre eigenen herumspielen starten, dies ist wichtig, daran zu denken Sie daran, Abstürze oder unerwünschte Verhalten wie zu verhindern HRTF Systemausfall.**</span><span class="sxs-lookup"><span data-stu-id="1bdb9-132">**Window's spatial sound engine only supports 48k samplerate for playback. Most middleware programs, like Unity, will automatically convert sound files into the desired format, but if you start tinkering at lower levels in the audio system or making your own, this is very important to remember to prevent crashes or undesired behaviour like HRTF system failure.**</span></span>

<span data-ttu-id="1bdb9-133">Zunächst müssen wir die APO zu initialisieren.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-133">First, we need to initialize the APO.</span></span> <span data-ttu-id="1bdb9-134">In unserem holographic Beispiel-app, behalten wir es uns dazu, sobald wir haben die **HolographicSpace**.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-134">In our holographic sample app, we choose to do this once we have the **HolographicSpace**.</span></span>

<span data-ttu-id="1bdb9-135">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span><span class="sxs-lookup"><span data-stu-id="1bdb9-135">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

<span data-ttu-id="1bdb9-136">Die Implementierung der Initialize-aus *OmnidirectionalSound.cpp*:</span><span class="sxs-lookup"><span data-stu-id="1bdb9-136">The implementation of Initialize, from *OmnidirectionalSound.cpp*:</span></span>

```
// Initializes an APO that emits sound equally in all directions.
HRESULT OmnidirectionalSound::Initialize( LPCWSTR filename )
{
    // _audioFile is of type AudioFileReader, which is defined in AudioFileReader.cpp.
    auto hr = _audioFile.Initialize( filename );

    ComPtr<IXAPO> xapo;
    if ( SUCCEEDED( hr ) )
    {
        // Passing in nullptr as the first arg for HrtfApoInit initializes the APO with defaults of
        // omnidirectional sound with natural distance decay behavior.
        // CreateHrtfApo fails with E_NOTIMPL on unsupported platforms.
        hr = CreateHrtfApo( nullptr, &xapo );
    }

    if ( SUCCEEDED( hr ) )
    {
        // _hrtfParams is of type ComPtr<IXAPOHrtfParameters>.
        hr = xapo.As( &_hrtfParams );
    }

    // Set the default environment.
    if ( SUCCEEDED( hr ) )
    {
        hr = _hrtfParams->SetEnvironment( HrtfEnvironment::Outdoors );
    }

    // Initialize an XAudio2 graph that hosts the HRTF xAPO.
    // The source voice is used to submit audio data and control playback.
    if ( SUCCEEDED( hr ) )
    {
        hr = SetupXAudio2( _audioFile.GetFormat(), xapo.Get(), &_xaudio2, &_sourceVoice );
    }

    // Submit audio data to the source voice.
    if ( SUCCEEDED( hr ) )
    {
        XAUDIO2_BUFFER buffer{ };
        buffer.AudioBytes = static_cast<UINT32>( _audioFile.GetSize() );
        buffer.pAudioData = _audioFile.GetData();
        buffer.LoopCount = XAUDIO2_LOOP_INFINITE;

        // _sourceVoice is of type IXAudio2SourceVoice*.
        hr = _sourceVoice->SubmitSourceBuffer( &buffer );
    }

    return hr;
}
```

<span data-ttu-id="1bdb9-137">Nachdem die APO für HRTF konfiguriert ist, rufen Sie [starten](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) auf Quelle Stimme, die die Wiedergabe der Audiodaten.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-137">After the APO is configured for HRTF, you call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span> <span data-ttu-id="1bdb9-138">In unserem Beispiel-app wählen wir es in eine Schleife platzieren, damit Sie fortfahren können, den Sound stammen aus dem Cube zu hören.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-138">In our sample app, we choose to put it on a loop so that you can continue to hear the sound coming from the cube.</span></span>

<span data-ttu-id="1bdb9-139">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span><span class="sxs-lookup"><span data-stu-id="1bdb9-139">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

<span data-ttu-id="1bdb9-140">Von *OmnidirectionalSound.cpp*:</span><span class="sxs-lookup"><span data-stu-id="1bdb9-140">From *OmnidirectionalSound.cpp*:</span></span>

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

<span data-ttu-id="1bdb9-141">Wenn wir den Frame zu aktualisieren, müssen wir nun die Hologramm Position relativ zu dem Gerät selbst zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-141">Now, whenever we update the frame, we need to update the hologram's position relative to the device itself.</span></span> <span data-ttu-id="1bdb9-142">Dies ist da HRTF Positionen immer relativ zum Anfang von des Benutzers, einschließlich des Head-Position und Ausrichtung ausgedrückt werden.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-142">This is because HRTF positions are always expressed relative to the user's head, including the head position and orientation.</span></span>

<span data-ttu-id="1bdb9-143">Zu diesem Zweck in einem HolographicSpace müssen wir eine Transformationsmatrix aus unserer SpatialStationaryFrameOfReference Koordinatensystem in einem Koordinatensystem zu erstellen, die auf dem Gerät selbst festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-143">To do this in a HolographicSpace, we need to construct a transform matrix from our SpatialStationaryFrameOfReference coordinate system to a coordinate system that is fixed to the device itself.</span></span>

<span data-ttu-id="1bdb9-144">From *HolographicHrtfAudioSampleMain::Update()*:</span><span class="sxs-lookup"><span data-stu-id="1bdb9-144">From *HolographicHrtfAudioSampleMain::Update()*:</span></span>

```
m_spinningCubeRenderer->Update(m_timer);

SpatialPointerPose^ currentPose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
if (currentPose != nullptr)
{
    // Use a coordinate system built from a pointer pose.
    SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
    if (pose != nullptr)
    {
        float3 headPosition = pose->Head->Position;
        float3 headUp = pose->Head->UpDirection;
        float3 headDirection = pose->Head->ForwardDirection;

        // To construct a rotation matrix, we need three vectors that are mutually orthogonal.
        // The first vector is the gaze vector.
        float3 negativeZAxis = normalize(headDirection);

        // The second vector should end up pointing away from the horizontal plane of the device.
        // We first guess by using the head "up" direction.
        float3 positiveYAxisGuess = normalize(headUp);

        // The third vector completes the set by being orthogonal to the other two.
        float3 positiveXAxis = normalize(cross(negativeZAxis, positiveYAxisGuess));

        // Now, we can correct our "up" vector guess by redetermining orthogonality.
        float3 positiveYAxis = normalize(cross(negativeZAxis, positiveXAxis));

        // The rotation matrix is formed as a standard basis rotation.
        float4x4 rotationTransform =
            {
            positiveXAxis.x, positiveYAxis.x, negativeZAxis.x, 0.f,
            positiveXAxis.y, positiveYAxis.y, negativeZAxis.y, 0.f,
            positiveXAxis.z, positiveYAxis.z, negativeZAxis.z, 0.f,
            0.f, 0.f, 0.f, 1.f,
            };

        // The translate transform can be constructed using the Windows::Foundation::Numerics API.
        float4x4 translationTransform = make_float4x4_translation(-headPosition);

        // Now, we have a basis transform from our spatial coordinate system to a device-relative
        // coordinate system.
        float4x4 coordinateSystemTransform = translationTransform * rotationTransform;

        // Reinterpret the cube position in the device's coordinate system.
        float3 cubeRelativeToHead = transform(m_spinningCubeRenderer->GetPosition(), coordinateSystemTransform);

        // Note that at (0, 0, 0) exactly, the HRTF audio will simply pass through audio. We can use a minimal offset
        // to simulate a zero distance when the hologram position vector is exactly at the device origin in order to
        // allow HRTF to continue functioning in this edge case.
        float distanceFromHologramToHead = length(cubeRelativeToHead);
        static const float distanceMin = 0.00001f;
        if (distanceFromHologramToHead < distanceMin)
        {
            cubeRelativeToHead = float3(0.f, distanceMin, 0.f);
        }

        // Position the spatial sound source on the hologram.
        m_omnidirectionalSound.OnUpdate(cubeRelativeToHead);

        // For debugging, it can be interesting to observe the distance in the debugger.
        /*
        std::wstring distanceString = L"Distance from hologram to head: ";
        distanceString += std::to_wstring(distanceFromHologramToHead);
        distanceString += L"\n";
        OutputDebugStringW(distanceString.c_str());
        */
    }
}
```

<span data-ttu-id="1bdb9-145">Die HRTF Position wird von der Hilfsklasse OmnidirectionalSound direkt auf den sound APO angewendet.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-145">The HRTF position is applied directly to the sound APO by the OmnidirectionalSound helper class.</span></span>

<span data-ttu-id="1bdb9-146">From *OmnidirectionalSound::OnUpdate*:</span><span class="sxs-lookup"><span data-stu-id="1bdb9-146">From *OmnidirectionalSound::OnUpdate*:</span></span>

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

<span data-ttu-id="1bdb9-147">Das ist alles!</span><span class="sxs-lookup"><span data-stu-id="1bdb9-147">That's it!</span></span> <span data-ttu-id="1bdb9-148">Lesen Sie weitere Informationen zu mit HRTF-Audio- und Windows Holographic Verwendungsmöglichkeiten weiter.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-148">Continue reading to learn more about what you can do with HRTF audio and Windows Holographic.</span></span>

### <a name="initialize-spatial-sound-for-a-directional-source"></a><span data-ttu-id="1bdb9-149">Initialisieren Sie räumliche Sound für eine direktionale Datenquelle</span><span class="sxs-lookup"><span data-stu-id="1bdb9-149">Initialize spatial sound for a directional source</span></span>

<span data-ttu-id="1bdb9-150">Einige Hologramme in der benutzerumgebung ausgeben, Sound, vor allem in eine Richtung.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-150">Some holograms in the user's surroundings emit sound mostly in one direction.</span></span> <span data-ttu-id="1bdb9-151">Dieses Muster sound heißt *Cardioid* , da es ein Cartoon Herz aussieht.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-151">This sound pattern is named *cardioid* because it looks like a cartoon heart.</span></span> <span data-ttu-id="1bdb9-152">Der folgende Code zeigt eine APO unidirektionale Ausgabe initialisieren sound.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-152">The following code shows how to initialize an APO to emit directional sound.</span></span> <span data-ttu-id="1bdb9-153">Die vollständige codeauflistung finden Sie unter [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .</span><span class="sxs-lookup"><span data-stu-id="1bdb9-153">For the complete code listing, see [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .</span></span>

<span data-ttu-id="1bdb9-154">Rufen Sie nach dem Konfigurieren der APO für HRTF [starten](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) auf Quelle Stimme, die die Wiedergabe der Audiodaten.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-154">After the APO is configured for HRTF, call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span>

```
// Initializes an APO that emits directional sound.
HRESULT CardioidSound::Initialize( LPCWSTR filename )
{
    // _audioFile is of type AudioFileReader, which is defined in AudioFileReader.cpp.
    auto hr = _audioFile.Initialize( filename );
    if ( SUCCEEDED( hr ) )
    {
        // Initialize with "Scaling" fully directional and "Order" with broad radiation pattern.
        // As the order goes higher, the cardioid directivity region becomes narrower.
        // Any direct path signal outside of the directivity region will be attenuated based on the scaling factor.
        // For example, if scaling is set to 1 (fully directional) the direct path signal outside of the directivity
        // region will be fully attenuated and only the reflections from the environment will be audible.
        hr = ConfigureApo( 1.0f, 4.0f );
    }
    return hr;
}

HRESULT CardioidSound::ConfigureApo( float scaling, float order )
{
    // Cardioid directivity configuration:
    // Directivity is specified at xAPO instance initialization and can't be changed per frame.
    // To change directivity, stop audio processing and reinitialize another APO instance with the new directivity.
    HrtfDirectivityCardioid cardioid;
    cardioid.directivity.type = HrtfDirectivityType::Cardioid;
    cardioid.directivity.scaling = scaling;
    cardioid.order = order;

    // APO intialization
    HrtfApoInit apoInit;
    apoInit.directivity = &cardioid.directivity;
    apoInit.distanceDecay = nullptr; // nullptr specifies natural distance decay behavior (simulates real world)

    // CreateHrtfApo fails with E_NOTIMPL on unsupported platforms.
    ComPtr<IXAPO> xapo;
    auto hr = CreateHrtfApo( &apoInit, &xapo );

    if ( SUCCEEDED( hr ) )
    {
        hr = xapo.As( &_hrtfParams );
    }

    // Set the initial environment.
    // Environment settings configure the "distance cues" used to compute the early and late reverberations.
    if ( SUCCEEDED( hr ) )
    {
        hr = _hrtfParams->SetEnvironment( _HrtfEnvironment::Outdoors );
    }

    // Initialize an XAudio2 graph that hosts the HRTF xAPO.
    // The source voice is used to submit audio data and control playback.
    if ( SUCCEEDED( hr ) )
    {
        hr = SetupXAudio2( _audioFile.GetFormat(), xapo.Get(), &_xaudio2, &_sourceVoice );
    }

    // Submit audio data to the source voice
    if ( SUCCEEDED( hr ) )
    {
        XAUDIO2_BUFFER buffer{ };
        buffer.AudioBytes = static_cast<UINT32>( _audioFile.GetSize() );
        buffer.pAudioData = _audioFile.GetData();
        buffer.LoopCount = XAUDIO2_LOOP_INFINITE;
        hr = _sourceVoice->SubmitSourceBuffer( &buffer );
    }

    return hr;
}
```

### <a name="implement-custom-decay"></a><span data-ttu-id="1bdb9-155">Implementieren von benutzerdefinierten decay</span><span class="sxs-lookup"><span data-stu-id="1bdb9-155">Implement custom decay</span></span>

<span data-ttu-id="1bdb9-156">Sie können die Rate überschreiben, an dem räumlicher Sound nicht mehr mit Abstand bzw. in welchem Abstand es schneidet vollständig.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-156">You can override the rate at which a spatial sound falls off with distance and/or at what distance it cuts off completely.</span></span> <span data-ttu-id="1bdb9-157">Um benutzerdefinierte Decay-Verhalten auf den spatial Sound zu implementieren, füllen Sie ein [HrtfDistanceDecay Struktur](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) und weisen sie Sie der **DistanceDecay** Feld eine [HrtfApoInit Struktur](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) vor der Übergabe an die [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) Funktion.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-157">To implement custom decay behavior on a spatial sound, populate an [HrtfDistanceDecay struct](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) and assign it to the **distanceDecay** field in an [HrtfApoInit struct](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) before passing it to the [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) function.</span></span>

<span data-ttu-id="1bdb9-158">Fügen Sie den folgenden Code der **initialisieren** Methode, die zuvor gezeigte, um benutzerdefinierte Decay-Verhalten anzugeben.</span><span class="sxs-lookup"><span data-stu-id="1bdb9-158">Add the following code to the **Initialize** method shown previously to specify custom decay behavior.</span></span> <span data-ttu-id="1bdb9-159">Die vollständige codeauflistung finden Sie unter [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).</span><span class="sxs-lookup"><span data-stu-id="1bdb9-159">For the complete code listing, see [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).</span></span>

```
HRESULT CustomDecaySound::Initialize( LPCWSTR filename )
{
    auto hr = _audioFile.Initialize( filename );

    ComPtr<IXAPO> xapo;
    if ( SUCCEEDED( hr ) )
    {
        HrtfDistanceDecay customDecay;
        customDecay.type = HrtfDistanceDecayType::CustomDecay;               // Custom decay behavior, we'll pass in the gain value on every frame.
        customDecay.maxGain = 0;                                             // 0dB max gain
        customDecay.minGain = -96.0f;                                        // -96dB min gain
        customDecay.unityGainDistance = HRTF_DEFAULT_UNITY_GAIN_DISTANCE;    // Default unity gain distance
        customDecay.cutoffDistance = HRTF_DEFAULT_CUTOFF_DISTANCE;           // Default cutoff distance

        // Setting the directivity to nullptr specifies omnidirectional sound.
        HrtfApoInit init;
        init.directivity = nullptr;
        init.distanceDecay = &customDecay;

        // CreateHrtfApo will fail with E_NOTIMPL on unsupported platforms.
        hr = CreateHrtfApo( &init, &xapo );
    }
...
}
```
