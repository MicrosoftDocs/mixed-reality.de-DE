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
# <a name="spatial-sound-in-directx"></a>Räumliche Sound in DirectX

Hinzufügen von räumlichen Sound zu Ihren Windows Mixed Reality-apps, die basierend auf DirectX verwenden die [XAudio2](https://msdn.microsoft.com/library/windows/desktop/hh405049.aspx) und [xAPO](https://msdn.microsoft.com/library/windows/desktop/ee415735.aspx) audio-Bibliotheken.

In diesem Thema wird Beispielcode von der HolographicHRTFAudioSample verwendet.

>[!NOTE]
>Die Codeausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstatt C ++ 17-kompatible C++"/ WinRT", wie in der [ C++ holographic Projektvorlage](creating-a-holographic-directx-project.md).  Die Konzepte sind Entsprechung für einen C++"/ WinRT"-Projekt, aber Sie benötigen, um den Code zu übersetzen.

## <a name="overview-of-head-relative-spatial-sound"></a>Übersicht über die Head Relative räumliche Sound

Räumliche Sound wird als implementiert eine **audio Verarbeitung des Objekts (APO)** , verwendet eine **Head bezogene Übertragungsfunktion (HRTF)** filtern, um *spatialize* gewöhnliche Audiodatenstrom.

Schließen Sie diese Headerdateien in "PCH.h", das Audio-APIs den Zugriff auf ein:
* XAudio2.h
* xapo.h
* hrtfapoapi.h

So richten Sie räumliche sound
1. Rufen Sie [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) zum Initialisieren einer neuen APO für HRTF-Audio.
2. Weisen Sie die [HRTF Parameter](https://msdn.microsoft.com/library/windows/desktop/mt186608.aspx) und [HRTF Umgebung](https://msdn.microsoft.com/library/windows/desktop/mt186604.aspx) den akustischen Merkmalen, der den räumlichen sound APO definieren.
3. Richten Sie die XAudio2-Engine zur Verarbeitung von HRTF.
4. Erstellen Sie eine [IXAudio2SourceVoice](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.aspx) Objekt, und rufen [starten](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx).

## <a name="implementing-hrtf-and-spatial-sound-in-your-directx-app"></a>Implementieren von HRTF und räumliche Sound in DirectX-Apps

Sie können eine Reihe von Effekten erzielen, durch Konfigurieren der HRTF APO mit verschiedenen Parametern und Umgebungen. Verwenden Sie den folgenden Code, um die Möglichkeiten zu untersuchen. Das Codebeispiel für die universelle Windows-Plattform hier herunterladen: [Sound Spatial-Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpatialSound)

Hilfstypen sind in diesen Dateien verfügbar:
* [AudioFileReader.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/AudioFileReader.cpp): Audio-Dateien mit Media Foundation geladen und die [IMFSourceReader-Schnittstelle](https://msdn.microsoft.com/library/windows/desktop/dd374655.aspx).
* [XAudio2Helpers.h](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/XAudio2Helpers.h): Implementiert die **SetupXAudio2** Funktion XAudio2 für die Verarbeitung von HRTF initialisiert werden.

### <a name="add-spatial-sound-for-an-omnidirectional-source"></a>Räumliche Sound für eine omnidirektionale Datenquelle hinzufügen

Einige Hologramme in der benutzerumgebung ausgeben Sound gleichmäßig in alle Richtungen. Der folgende Code zeigt, wie ein APO omnidirektionale Sound Ausgabe initialisiert wird. In diesem Beispiel wenden wir dieses Konzept auf den sich drehenden Würfels in die Windows Holographic-app-Vorlage. Die vollständige codeauflistung finden Sie unter [OmnidirectionalSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/OmnidirectionalSound.cpp).

**Fensters räumliche sound-Engine unterstützt nur 48 KB Samplerate für die Wiedergabe. Die meisten Middleware-Programme wie Unity, Audiodateien automatisch in das gewünschte Format konvertiert, aber wenn Sie auf niedrigeren Ebenen in die audio-System oder machen Ihre eigenen herumspielen starten, dies ist wichtig, daran zu denken Sie daran, Abstürze oder unerwünschte Verhalten wie zu verhindern HRTF Systemausfall.**

Zunächst müssen wir die APO zu initialisieren. In unserem holographic Beispiel-app, behalten wir es uns dazu, sobald wir haben die **HolographicSpace**.

From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:

```
// Spatial sound
auto hr = m_omnidirectionalSound.Initialize(L"assets//MonoSound.wav");
```

Die Implementierung der Initialize-aus *OmnidirectionalSound.cpp*:

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

Nachdem die APO für HRTF konfiguriert ist, rufen Sie [starten](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) auf Quelle Stimme, die die Wiedergabe der Audiodaten. In unserem Beispiel-app wählen wir es in eine Schleife platzieren, damit Sie fortfahren können, den Sound stammen aus dem Cube zu hören.

From *HolographicHrtfAudioSampleMain::SetHolographicSpace()*:

```
if (SUCCEEDED(hr))
{
    m_omnidirectionalSound.SetEnvironment(HrtfEnvironment::Small);
    m_omnidirectionalSound.OnUpdate(m_spinningCubeRenderer->GetPosition());
    m_omnidirectionalSound.Start();
}
```

Von *OmnidirectionalSound.cpp*:

```
HRESULT OmnidirectionalSound::Start()
{
    _lastTick = GetTickCount64();
    return _sourceVoice->Start();
}
```

Wenn wir den Frame zu aktualisieren, müssen wir nun die Hologramm Position relativ zu dem Gerät selbst zu aktualisieren. Dies ist da HRTF Positionen immer relativ zum Anfang von des Benutzers, einschließlich des Head-Position und Ausrichtung ausgedrückt werden.

Zu diesem Zweck in einem HolographicSpace müssen wir eine Transformationsmatrix aus unserer SpatialStationaryFrameOfReference Koordinatensystem in einem Koordinatensystem zu erstellen, die auf dem Gerät selbst festgelegt ist.

From *HolographicHrtfAudioSampleMain::Update()*:

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

Die HRTF Position wird von der Hilfsklasse OmnidirectionalSound direkt auf den sound APO angewendet.

From *OmnidirectionalSound::OnUpdate*:

```
HRESULT OmnidirectionalSound::OnUpdate(_In_ Numerics::float3 position)
{
    auto hrtfPosition = HrtfPosition{ position.x, position.y, position.z };
    return _hrtfParams->SetSourcePosition(&hrtfPosition);
}
```

Das ist alles! Lesen Sie weitere Informationen zu mit HRTF-Audio- und Windows Holographic Verwendungsmöglichkeiten weiter.

### <a name="initialize-spatial-sound-for-a-directional-source"></a>Initialisieren Sie räumliche Sound für eine direktionale Datenquelle

Einige Hologramme in der benutzerumgebung ausgeben, Sound, vor allem in eine Richtung. Dieses Muster sound heißt *Cardioid* , da es ein Cartoon Herz aussieht. Der folgende Code zeigt eine APO unidirektionale Ausgabe initialisieren sound. Die vollständige codeauflistung finden Sie unter [CardioidSound.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CardioidSound.cpp) .

Rufen Sie nach dem Konfigurieren der APO für HRTF [starten](https://msdn.microsoft.com/library/windows/desktop/microsoft.directx_sdk.ixaudio2sourcevoice.ixaudio2sourcevoice.start.aspx) auf Quelle Stimme, die die Wiedergabe der Audiodaten.

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

### <a name="implement-custom-decay"></a>Implementieren von benutzerdefinierten decay

Sie können die Rate überschreiben, an dem räumlicher Sound nicht mehr mit Abstand bzw. in welchem Abstand es schneidet vollständig. Um benutzerdefinierte Decay-Verhalten auf den spatial Sound zu implementieren, füllen Sie ein [HrtfDistanceDecay Struktur](https://msdn.microsoft.com/library/windows/desktop/mt186602.aspx) und weisen sie Sie der **DistanceDecay** Feld eine [HrtfApoInit Struktur](https://msdn.microsoft.com/library/windows/desktop/mt186597.aspx) vor der Übergabe an die [CreateHrtfApo](https://msdn.microsoft.com/library/windows/desktop/mt186596.aspx) Funktion.

Fügen Sie den folgenden Code der **initialisieren** Methode, die zuvor gezeigte, um benutzerdefinierte Decay-Verhalten anzugeben. Die vollständige codeauflistung finden Sie unter [CustomDecay.cpp](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpatialSound/cpp/CustomDecay.cpp).

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
