---
title: Räumlicher Sound in DirectX
description: Fügen Sie Ihren Windows Mixed Reality-apps, die auf DirectX basieren, mithilfe der XAudio2-und xapo-Audiobibliotheken räumlichen Sound hinzu.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Spatial Sound, apps, XAudio2, Low-Level, xapo, Audio Library, Exemplarische Vorgehensweise, DirectX
ms.openlocfilehash: 04d8c43ab400eed4cec5cbd848af5b888cb66e4b
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63550434"
---
# <a name="spatial-sound-in-directx"></a><span data-ttu-id="10538-104">Räumlicher Sound in DirectX</span><span class="sxs-lookup"><span data-stu-id="10538-104">Spatial sound in DirectX</span></span>

<span data-ttu-id="10538-105">Fügen Sie Ihren Windows Mixed Reality-apps, die auf DirectX basieren, mithilfe der [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) -und [xapo](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) -Audiobibliotheken räumlichen Sound hinzu.</span><span class="sxs-lookup"><span data-stu-id="10538-105">Add spatial sound to your Windows Mixed Reality apps based on DirectX by using the [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) and [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) audio libraries.</span></span>

<span data-ttu-id="10538-106">In diesem Thema wird der Beispielcode von holographichrtf Audiosample verwendet.</span><span class="sxs-lookup"><span data-stu-id="10538-106">This topic uses sample code from the HolographicHRTFAudioSample.</span></span>

>[!NOTE]
><span data-ttu-id="10538-107">Die Code Ausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung C++von/CX anstelle von C + +17- C++kompatibler/WinRT, wie Sie in der [ C++ Holographic-Projektvorlage](creating-a-holographic-directx-project.md)verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="10538-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="10538-108">Die Konzepte sind äquivalent für ein C++/WinRT-Projekt, obwohl Sie den Code übersetzen müssen.</span><span class="sxs-lookup"><span data-stu-id="10538-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="overview-of-head-relative-spatial-sound"></a><span data-ttu-id="10538-109">Übersicht über das relative räumliche Audioton</span><span class="sxs-lookup"><span data-stu-id="10538-109">Overview of Head Relative Spatial Sound</span></span>

<span data-ttu-id="10538-110">Räumlicher Sound wird als ein **Audioverarbeitungs Objekt ("-")** implementiert, das einen **HRTF-Filter (Head Related Transfer Function)** verwendet, um einen normalen Audiostream zu *spatialisieren* .</span><span class="sxs-lookup"><span data-stu-id="10538-110">Spatial sound is implemented as an **audio processing object (APO)** that uses a **head related transfer function (HRTF)** filter to *spatialize* an ordinary audio stream.</span></span>

<span data-ttu-id="10538-111">Schließen Sie diese Header Dateien in "PCH. h" ein, um auf die audioapis zuzugreifen:</span><span class="sxs-lookup"><span data-stu-id="10538-111">Include these header files in pch.h to access the audio APIs:</span></span>
* <span data-ttu-id="10538-112">XAudio2. h</span><span class="sxs-lookup"><span data-stu-id="10538-112">XAudio2.h</span></span>
* <span data-ttu-id="10538-113">xapo. h</span><span class="sxs-lookup"><span data-stu-id="10538-113">xapo.h</span></span>
* <span data-ttu-id="10538-114">hrtfapoapi. h</span><span class="sxs-lookup"><span data-stu-id="10538-114">hrtfapoapi.h</span></span>

<span data-ttu-id="10538-115">So richten Sie räumlichen Ton ein:</span><span class="sxs-lookup"><span data-stu-id="10538-115">To set up spatial sound:</span></span>
1. <span data-ttu-id="10538-116">Aufrufen von " [kreatehrtfapo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) " zum Initialisieren eines neuen "APO" für HRTF-Audiodaten.</span><span class="sxs-lookup"><span data-stu-id="10538-116">Call [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) to initialize a new APO for HRTF audio.</span></span>
2. <span data-ttu-id="10538-117">Weisen Sie die [HRTF-Parameter](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) und die [HRTF-Umgebung](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) zu, um die akustischen Merkmale der räumlichen Audiodatei zu definieren.</span><span class="sxs-lookup"><span data-stu-id="10538-117">Assign the [HRTF parameters](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) and [HRTF environment](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) to define the acoustic characteristics of the spatial sound APO.</span></span>
3. <span data-ttu-id="10538-118">Richten Sie die XAudio2-Engine für die HRTF-Verarbeitung ein.</span><span class="sxs-lookup"><span data-stu-id="10538-118">Set up the XAudio2 engine for HRTF processing.</span></span>
4. <span data-ttu-id="10538-119">Erstellen Sie ein [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) -Objekt, und rufen Sie [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)auf</span><span class="sxs-lookup"><span data-stu-id="10538-119">Create an [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) object and call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).</span></span>

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a><span data-ttu-id="10538-120">Implementieren von HRTF und räumlichem Sound in Ihrer DirectX-App</span><span class="sxs-lookup"><span data-stu-id="10538-120">Implementing HRTF and spatial sound in your DirectX app</span></span>

<span data-ttu-id="10538-121">Sie können eine Vielzahl von Effekten erzielen, indem Sie den HRTF-APO mit unterschiedlichen Parametern und Umgebungen konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="10538-121">You can achieve a variety of effects by configuring the HRTF APO with different parameters and environments.</span></span> <span data-ttu-id="10538-122">Verwenden Sie den folgenden Code, um die Möglichkeiten zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="10538-122">Use the following code to explore the possibilities.</span></span> <span data-ttu-id="10538-123">Laden Sie das Beispiel für den universelle Windows-Plattform Code hier herunter: [Beispiel für räumliches Sound](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span><span class="sxs-lookup"><span data-stu-id="10538-123">Download the Universal Windows Platform code sample from here: [Spatial sound sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)</span></span>

<span data-ttu-id="10538-124">Hilfstypen sind in folgenden Dateien verfügbar:</span><span class="sxs-lookup"><span data-stu-id="10538-124">Helper types are available in these files:</span></span>
* <span data-ttu-id="10538-125">[AudioFileReader. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Lädt Audiodateien mithilfe von Media Foundation und der [IMF sourcereader-Schnittstelle](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).</span><span class="sxs-lookup"><span data-stu-id="10538-125">[AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Loads audio files by using Media Foundation and the [IMFSourceReader interface](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).</span></span>
* <span data-ttu-id="10538-126">[XAudio2Helpers. h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implementiert die **SetupXAudio2** -Funktion, um XAudio2 für die HRTF-Verarbeitung zu initialisieren.</span><span class="sxs-lookup"><span data-stu-id="10538-126">[XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implements the **SetupXAudio2** function to initialize XAudio2 for HRTF processing.</span></span>

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a><span data-ttu-id="10538-127">Räumlichen Ton für eine omnidirektionale Quelle hinzufügen</span><span class="sxs-lookup"><span data-stu-id="10538-127">Add spatial sound for an omnidirectional source</span></span>

<span data-ttu-id="10538-128">Einige holograms in der Benutzerumgebung geben Sound gleichmäßig in alle Richtungen aus.</span><span class="sxs-lookup"><span data-stu-id="10538-128">Some holograms in the user's surroundings emit sound equally in all directions.</span></span> <span data-ttu-id="10538-129">Der folgende Code zeigt, wie ein APO initialisiert wird, um omnidirektionalen Sound auszugeben.</span><span class="sxs-lookup"><span data-stu-id="10538-129">The following code shows how to initialize an APO to emit omnidirectional sound.</span></span> <span data-ttu-id="10538-130">In diesem Beispiel wenden wir dieses Konzept auf den drehenden Cube aus der Windows Holographic App-Vorlage an.</span><span class="sxs-lookup"><span data-stu-id="10538-130">In this example, we apply this concept to the spinning cube from the Windows Holographic app template.</span></span> <span data-ttu-id="10538-131">Das vollständige Codelisting finden Sie unter [omnidirectionalsound. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).</span><span class="sxs-lookup"><span data-stu-id="10538-131">For the complete code listing, see [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).</span></span>

<span data-ttu-id="10538-132">**Die räumliche Sound-Engine von Window unterstützt nur 48 KB für die Wiedergabe. Die meisten middlewareprogramme, wie z. b. unity, konvertieren Audiodateien automatisch in das gewünschte Format. Wenn Sie jedoch auf niedrigeren Ebenen im Audiosystem beginnen oder eigene erstellen, ist es sehr wichtig zu beachten, dass Abstürze oder unerwünschte Verhaltensweisen wie HRTF-Systemfehler.**</span><span class="sxs-lookup"><span data-stu-id="10538-132">**Window's spatial sound engine only supports 48k samplerate for playback. Most middleware programs, like Unity, will automatically convert sound files into the desired format, but if you start tinkering at lower levels in the audio system or making your own, this is very important to remember to prevent crashes or undesired behaviour like HRTF system failure.**</span></span>

<span data-ttu-id="10538-133">Zuerst muss der APO initialisiert werden.</span><span class="sxs-lookup"><span data-stu-id="10538-133">First, we need to initialize the APO.</span></span> <span data-ttu-id="10538-134">In unserer Holographic-Beispiel-App wählen wir dies aus, sobald der **holographicspace-Bereich**vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="10538-134">In our holographic sample app, we choose to do this once we have the **HolographicSpace**.</span></span>

<span data-ttu-id="10538-135">Aus *holographichrtf audiosamplemain:: Abort ()* :</span><span class="sxs-lookup"><span data-stu-id="10538-135">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

<span data-ttu-id="10538-136">Die Implementierung von Initialize von *omnidirectionalsound. cpp*:</span><span class="sxs-lookup"><span data-stu-id="10538-136">The implementation of Initialize, from *OmnidirectionalSound.cpp*:</span></span>

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

<span data-ttu-id="10538-137">Nachdem der APO für HRTF konfiguriert wurde, müssen Sie auf der Quell Stimme [starten](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) , um die Audiodatei wiederzugeben.</span><span class="sxs-lookup"><span data-stu-id="10538-137">After the APO is configured for HRTF, you call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span> <span data-ttu-id="10538-138">In unserer Beispiel-App legen wir fest, dass Sie in einer Schleife abgelegt wird, damit Sie den Sound des Cubes weiter hören können.</span><span class="sxs-lookup"><span data-stu-id="10538-138">In our sample app, we choose to put it on a loop so that you can continue to hear the sound coming from the cube.</span></span>

<span data-ttu-id="10538-139">Aus *holographichrtf audiosamplemain:: Abort ()* :</span><span class="sxs-lookup"><span data-stu-id="10538-139">From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:</span></span>

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

<span data-ttu-id="10538-140">Aus " *omnidirectionalsound. cpp*":</span><span class="sxs-lookup"><span data-stu-id="10538-140">From *OmnidirectionalSound.cpp*:</span></span>

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

<span data-ttu-id="10538-141">Wenn wir nun den Frame aktualisieren, müssen wir die Position des Hologramms relativ zum Gerät selbst aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="10538-141">Now, whenever we update the frame, we need to update the hologram's position relative to the device itself.</span></span> <span data-ttu-id="10538-142">Dies liegt daran, dass die HRTF-Positionen immer relativ zum Kopf des Benutzers ausgedrückt werden, einschließlich der Kopfposition und der Ausrichtung.</span><span class="sxs-lookup"><span data-stu-id="10538-142">This is because HRTF positions are always expressed relative to the user's head, including the head position and orientation.</span></span>

<span data-ttu-id="10538-143">Um dies in einem holographicspace zu tun, müssen wir eine Transformationsmatrix aus unserem spatialstationaryframeofreferenzierungssystem zu einem Koordinatensystem erstellen, das auf dem Gerät selbst fest liegt.</span><span class="sxs-lookup"><span data-stu-id="10538-143">To do this in a HolographicSpace, we need to construct a transform matrix from our SpatialStationaryFrameOfReference coordinate system to a coordinate system that is fixed to the device itself.</span></span>

<span data-ttu-id="10538-144">Von *holographichrtf audiosamplemain:: Update ()* :</span><span class="sxs-lookup"><span data-stu-id="10538-144">From *HolographicHrtfAudioSampleMain::Update()*:</span></span>

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

<span data-ttu-id="10538-145">Die HRTF-Position wird von der Hilfsklasse "omnidirectionalsound" direkt auf die Audiodatei angewendet.</span><span class="sxs-lookup"><span data-stu-id="10538-145">The HRTF position is applied directly to the sound APO by the OmnidirectionalSound helper class.</span></span>

<span data-ttu-id="10538-146">Aus *omnidirectionalsound:: OnUpdate*:</span><span class="sxs-lookup"><span data-stu-id="10538-146">From *OmnidirectionalSound::OnUpdate*:</span></span>

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

<span data-ttu-id="10538-147">Das ist alles!</span><span class="sxs-lookup"><span data-stu-id="10538-147">That's it!</span></span> <span data-ttu-id="10538-148">Lesen Sie weiter, um mehr darüber zu erfahren, was Sie mit HRTF-Audiodaten und Windows Holographic tun können.</span><span class="sxs-lookup"><span data-stu-id="10538-148">Continue reading to learn more about what you can do with HRTF audio and Windows Holographic.</span></span>

### <a name="initialize-spatial-sound-for-a-directional-source"></a><span data-ttu-id="10538-149">Räumlichen Ton für eine direktionale Quelle initialisieren</span><span class="sxs-lookup"><span data-stu-id="10538-149">Initialize spatial sound for a directional source</span></span>

<span data-ttu-id="10538-150">Einige holograms in der Benutzerumgebung geben einen Sound vor allem in einer Richtung aus.</span><span class="sxs-lookup"><span data-stu-id="10538-150">Some holograms in the user's surroundings emit sound mostly in one direction.</span></span> <span data-ttu-id="10538-151">Dieses Sound Muster hat den Namen " *karoid* ", da es wie ein Cartoon-Herz aussieht.</span><span class="sxs-lookup"><span data-stu-id="10538-151">This sound pattern is named *cardioid* because it looks like a cartoon heart.</span></span> <span data-ttu-id="10538-152">Der folgende Code zeigt, wie ein APO initialisiert wird, um einen direktionalen Sound auszugeben.</span><span class="sxs-lookup"><span data-stu-id="10538-152">The following code shows how to initialize an APO to emit directional sound.</span></span> <span data-ttu-id="10538-153">Das vollständige Codelisting finden Sie unter " [cardioidsound. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) ".</span><span class="sxs-lookup"><span data-stu-id="10538-153">For the complete code listing, see [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .</span></span>

<span data-ttu-id="10538-154">Nachdem der APO für HRTF konfiguriert wurde, müssen Sie auf der Quell Stimme [starten](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) , um die Audiodatei wiederzugeben.</span><span class="sxs-lookup"><span data-stu-id="10538-154">After the APO is configured for HRTF, call [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) on the source voice to play the audio.</span></span>

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

### <a name="implement-custom-decay"></a><span data-ttu-id="10538-155">Implementieren eines benutzerdefinierten Zerfalls</span><span class="sxs-lookup"><span data-stu-id="10538-155">Implement custom decay</span></span>

<span data-ttu-id="10538-156">Sie können die Rate, mit der ein räumlicher Sound entfernt wird, mit der Entfernung und/oder der Entfernung überschreiben, die vollständig abgeschnitten wird.</span><span class="sxs-lookup"><span data-stu-id="10538-156">You can override the rate at which a spatial sound falls off with distance and/or at what distance it cuts off completely.</span></span> <span data-ttu-id="10538-157">Wenn Sie ein benutzerdefiniertes Verhaltens Verhalten in einem räumlichen Sound implementieren möchten, füllen Sie eine [hrtfdistancedecay-Struktur](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) auf, und weisen Sie Sie dem Feld **distancedecay** in einer [hrtfapoinit-Struktur](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) zu, bevor Sie Sie an die Funktion " [kreatehrtfapo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) " übergeben</span><span class="sxs-lookup"><span data-stu-id="10538-157">To implement custom decay behavior on a spatial sound, populate an [HrtfDistanceDecay struct](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) and assign it to the **distanceDecay** field in an [HrtfApoInit struct](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) before passing it to the [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) function.</span></span>

<span data-ttu-id="10538-158">Fügen Sie der zuvor gezeigten **Initialize** -Methode den folgenden Code hinzu, um ein benutzerdefiniertes Verhaltens Verhalten anzugeben.</span><span class="sxs-lookup"><span data-stu-id="10538-158">Add the following code to the **Initialize** method shown previously to specify custom decay behavior.</span></span> <span data-ttu-id="10538-159">Das komplette Codelisting finden Sie unter [customdecay. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).</span><span class="sxs-lookup"><span data-stu-id="10538-159">For the complete code listing, see [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).</span></span>

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
