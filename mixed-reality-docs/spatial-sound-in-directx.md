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
# <a name="spatial-sound-in-directx"></a>Räumlicher Sound in DirectX

Fügen Sie Ihren Windows Mixed Reality-apps, die auf DirectX basieren, mithilfe der [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) -und [xapo](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) -Audiobibliotheken räumlichen Sound hinzu.

In diesem Thema wird der Beispielcode von holographichrtf Audiosample verwendet.

>[!NOTE]
>Die Code Ausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung C++von/CX anstelle von C + +17- C++kompatibler/WinRT, wie Sie in der [ C++ Holographic-Projektvorlage](creating-a-holographic-directx-project.md)verwendet werden.  Die Konzepte sind äquivalent für ein C++/WinRT-Projekt, obwohl Sie den Code übersetzen müssen.

## <a name="overview-of-head-relative-spatial-sound"></a>Übersicht über das relative räumliche Audioton

Räumlicher Sound wird als ein **Audioverarbeitungs Objekt ("-")** implementiert, das einen **HRTF-Filter (Head Related Transfer Function)** verwendet, um einen normalen Audiostream zu *spatialisieren* .

Schließen Sie diese Header Dateien in "PCH. h" ein, um auf die audioapis zuzugreifen:
* XAudio2. h
* xapo. h
* hrtfapoapi. h

So richten Sie räumlichen Ton ein:
1. Aufrufen von " [kreatehrtfapo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) " zum Initialisieren eines neuen "APO" für HRTF-Audiodaten.
2. Weisen Sie die [HRTF-Parameter](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) und die [HRTF-Umgebung](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) zu, um die akustischen Merkmale der räumlichen Audiodatei zu definieren.
3. Richten Sie die XAudio2-Engine für die HRTF-Verarbeitung ein.
4. Erstellen Sie ein [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) -Objekt, und rufen Sie [Start](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx)auf

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a>Implementieren von HRTF und räumlichem Sound in Ihrer DirectX-App

Sie können eine Vielzahl von Effekten erzielen, indem Sie den HRTF-APO mit unterschiedlichen Parametern und Umgebungen konfigurieren. Verwenden Sie den folgenden Code, um die Möglichkeiten zu untersuchen. Laden Sie das Beispiel für den universelle Windows-Plattform Code hier herunter: [Beispiel für räumliches Sound](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)

Hilfstypen sind in folgenden Dateien verfügbar:
* [AudioFileReader. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Lädt Audiodateien mithilfe von Media Foundation und der [IMF sourcereader-Schnittstelle](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).
* [XAudio2Helpers. h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implementiert die **SetupXAudio2** -Funktion, um XAudio2 für die HRTF-Verarbeitung zu initialisieren.

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a>Räumlichen Ton für eine omnidirektionale Quelle hinzufügen

Einige holograms in der Benutzerumgebung geben Sound gleichmäßig in alle Richtungen aus. Der folgende Code zeigt, wie ein APO initialisiert wird, um omnidirektionalen Sound auszugeben. In diesem Beispiel wenden wir dieses Konzept auf den drehenden Cube aus der Windows Holographic App-Vorlage an. Das vollständige Codelisting finden Sie unter [omnidirectionalsound. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).

**Die räumliche Sound-Engine von Window unterstützt nur 48 KB für die Wiedergabe. Die meisten middlewareprogramme, wie z. b. unity, konvertieren Audiodateien automatisch in das gewünschte Format. Wenn Sie jedoch auf niedrigeren Ebenen im Audiosystem beginnen oder eigene erstellen, ist es sehr wichtig zu beachten, dass Abstürze oder unerwünschte Verhaltensweisen wie HRTF-Systemfehler.**

Zuerst muss der APO initialisiert werden. In unserer Holographic-Beispiel-App wählen wir dies aus, sobald der **holographicspace-Bereich**vorhanden ist.

Aus *holographichrtf audiosamplemain:: Abort ()* :

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

Die Implementierung von Initialize von *omnidirectionalsound. cpp*:

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

Nachdem der APO für HRTF konfiguriert wurde, müssen Sie auf der Quell Stimme [starten](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) , um die Audiodatei wiederzugeben. In unserer Beispiel-App legen wir fest, dass Sie in einer Schleife abgelegt wird, damit Sie den Sound des Cubes weiter hören können.

Aus *holographichrtf audiosamplemain:: Abort ()* :

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

Aus " *omnidirectionalsound. cpp*":

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

Wenn wir nun den Frame aktualisieren, müssen wir die Position des Hologramms relativ zum Gerät selbst aktualisieren. Dies liegt daran, dass die HRTF-Positionen immer relativ zum Kopf des Benutzers ausgedrückt werden, einschließlich der Kopfposition und der Ausrichtung.

Um dies in einem holographicspace zu tun, müssen wir eine Transformationsmatrix aus unserem spatialstationaryframeofreferenzierungssystem zu einem Koordinatensystem erstellen, das auf dem Gerät selbst fest liegt.

Von *holographichrtf audiosamplemain:: Update ()* :

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

Die HRTF-Position wird von der Hilfsklasse "omnidirectionalsound" direkt auf die Audiodatei angewendet.

Aus *omnidirectionalsound:: OnUpdate*:

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

Das ist alles! Lesen Sie weiter, um mehr darüber zu erfahren, was Sie mit HRTF-Audiodaten und Windows Holographic tun können.

### <a name="initialize-spatial-sound-for-a-directional-source"></a>Räumlichen Ton für eine direktionale Quelle initialisieren

Einige holograms in der Benutzerumgebung geben einen Sound vor allem in einer Richtung aus. Dieses Sound Muster hat den Namen " *karoid* ", da es wie ein Cartoon-Herz aussieht. Der folgende Code zeigt, wie ein APO initialisiert wird, um einen direktionalen Sound auszugeben. Das vollständige Codelisting finden Sie unter " [cardioidsound. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) ".

Nachdem der APO für HRTF konfiguriert wurde, müssen Sie auf der Quell Stimme [starten](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) , um die Audiodatei wiederzugeben.

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

### <a name="implement-custom-decay"></a>Implementieren eines benutzerdefinierten Zerfalls

Sie können die Rate, mit der ein räumlicher Sound entfernt wird, mit der Entfernung und/oder der Entfernung überschreiben, die vollständig abgeschnitten wird. Wenn Sie ein benutzerdefiniertes Verhaltens Verhalten in einem räumlichen Sound implementieren möchten, füllen Sie eine [hrtfdistancedecay-Struktur](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) auf, und weisen Sie Sie dem Feld **distancedecay** in einer [hrtfapoinit-Struktur](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) zu, bevor Sie Sie an die Funktion " [kreatehrtfapo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) " übergeben

Fügen Sie der zuvor gezeigten **Initialize** -Methode den folgenden Code hinzu, um ein benutzerdefiniertes Verhaltens Verhalten anzugeben. Das komplette Codelisting finden Sie unter [customdecay. cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).

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
