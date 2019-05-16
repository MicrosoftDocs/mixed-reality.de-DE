---
title: Haupt- und Eye Blicke in DirectX
description: Entwicklerhandbuch für die Verwendung von Head Blicke und Eye-tracking in systemeigenen DirectX-apps.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: Blicke, Head Blicke, Head, die nachverfolgung, Eye-tracking, Directx, Eingabe, Hologramme
ms.openlocfilehash: f9764132df0ca4ae2f02d8f9a5740530676eb4f5
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629613"
---
# <a name="head-and-eye-gaze-in-directx"></a>Haupt- und Eye Blicke in DirectX

In Windows Mixed Reality blickverlaufseingabe verwendet, um zu bestimmen, was der Benutzer ausgewertet wird. Dies kann verwendet werden, um die primäre Eingabe-Modelle, wie z. B. Laufwerk [bestaunen und committen Sie](gaze-and-commit.md), und auch um den Kontext für die Arten von Aktivitäten bereitzustellen. Es gibt zwei Arten von Blicke Vektoren, die über die API zur Verfügung: head Blicke und Eye Blicke.  Beide dienen als eine drei dimensionalen Chow mit einem Ursprung und Richtung. Anwendungen können dann Raycast in ihre Szenen oder der realen Welt und zu ermitteln, was der Benutzer abzielt.

**Head bestaunen** stellt die Richtung, die des Benutzers Head in gezeigt wird. Stellen Sie sich die Position und Vorwärts, von dem Gerät selbst, und zeigen Sie mit der Position die Mitte darstellt zwischen den zwei angezeigt.  Head Blicke steht auf allen Mixed Reality-Geräten zur Verfügung.

**Eye Blicke** stellt die Richtung, die der Benutzer die Augen zu suchen. Der Ursprung befindet sich zwischen dem Benutzer die Augen.  Es steht in Mixed Reality-Geräte, die eine Eye-tracking System enthalten.

Sowohl die Hauptknoten als auch die Augen Blicke Strahlung können Sie über die [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) API. Rufen Sie ganz einfach [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) erhalten Sie ein neues SpatialPointerPose-Objekt, auf dem angegebenen Zeitstempel und [Koordinatensystem](coordinate-systems-in-directx.md). Diese SpatialPointerPose enthält eine Head Blicke Ursprung und eine Richtung. Es enthält auch ein Auge Blicke Ursprung und die Richtung, wenn Eye-tracking verfügbar ist.

## <a name="using-head-gaze"></a>Head Blicke verwenden

Starten Sie den Zugriff auf die Head Blicke durch Aufrufen von [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) um ein neues SpatialPointerPose-Objekt zu erhalten. Sie müssen die folgenden Parameter zu übergeben.
 - Ein [SpatialCoordinateSystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) , die das gewünschte Koordinatensystem für den Hauptknoten Blicke darstellt. Wird dies durch die *Koordinatensystem* Variablen in den folgenden Code. Weitere Informationen finden Sie auf unserer [Koordinatensysteme](coordinate-systems-in-directx.md) -Entwicklerhandbuch.
 - Ein [Zeitstempel](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) , die die genaue Zeit von der angeforderten Head Haltung darstellt.  In der Regel verwenden Sie einen Zeitstempel, der bis zum Zeitpunkt entspricht, wenn der aktuelle Frame angezeigt werden. Erhalten Sie diesem Zeitstempel vorhergesagten Anzeige von einem [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) -Objekt, das über den aktuellen zugänglich ist [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).  Dieses Objekt HolographicFramePrediction wird dargestellt, durch die *Vorhersage* Variablen in den folgenden Code.

 Nachdem Sie eine gültige SpatialPointerPose haben, sind die Head-Position und eine vorwärts gerichtete als Eigenschaften zugegriffen werden kann.  Der folgende Code zeigt, wie darauf zugegriffen wird.

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head gaze
}
```

## <a name="using-eye-gaze"></a>Verwenden die Augen Blicke

Die Augen Blicke-API ist Head Blicke sehr ähnlich.  Dabei wird derselbe [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) -API, die ein Strahl bereitstellt, Ursprung und die Richtung, die Sie für Ihre Szene Raycast können.  Der einzige Unterschied ist, dass Sie explizit Eye-tracking vor der Verwendung von anfordern des Zugriffs aktivieren müssen.

### <a name="declaring-the-gaze-input-capability"></a>Deklarieren der *bestaunen Eingabe* Funktion

Klicken Sie mit der Doppelklicken auf die Appxmanifest-Datei im *Projektmappen-Explorer*.  Navigieren Sie dann auf die *Funktionen* Abschnitt, und überprüfen Sie die *bestaunen Eingabe* Funktion. 

![Eingabe Blicke-Funktion](images/gaze-input-capability.png)

Dadurch werden die folgenden Zeilen auf die *Paket* Abschnitt in der Appxmanifest-Datei:
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="requesting-access-to-gaze-input"></a>Anfordern des Zugriffs auf die Eingabe bestaunen
Wenn Ihre app gestartet wird, rufen Sie [EyesPose::RequestAccessAsync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) zum Anfordern des Zugriffs auf Eye-Überwachung. Das System fordert den Benutzer bei Bedarf, und zurückgeben [GazeInputAccessStatus::Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) nach Zugriff gewährt wurde. Dies ist ein asynchroner Aufruf, damit es ein wenig zusätzliche Verwaltung erfordert. Im folgende Beispiel startet einen getrennten Std:: Thread warten, das Ergebnis, die auf eine Membervariable namens gespeichert *M_isEyeTrackingEnabled*.

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::UI::Input;

std::thread requestAccessThread([this]()
{
    auto status = EyesPose::RequestAccessAsync().get();

    if (status == GazeInputAccessStatus::Allowed)
        m_isEyeTrackingEnabled = true;
    else
        m_isEyeTrackingEnabled = false;
});

requestAccessThread.detach();

```

Starten eines getrennten Threads ist nur eine Option für die Verarbeitung von asynchronen Aufrufe.  Alternativ können Sie die neue verwenden [Co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) von unterstützten Funktionen C++"/ WinRT".

### <a name="getting-the-eye-gaze-ray"></a>Die Augen Blicke Chow abrufen

Nachdem Sie den Zugriff auf ET erhalten haben, können Sie dem Auge Blicke Strahl jeder Frame erfasst.  Genau wie bei Head Blicke, erhalten die [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) durch Aufrufen von [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) mit einem gewünschten Zeitstempel und der Koordinatensystem. Die SpatialPointerPose enthält ein [EyesPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) -Objekt über die [Augen](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) Eigenschaft. Dies ist nicht Null nur, wenn Eye-tracking aktiviert ist. Von dort aus können Sie überprüfen, ob der Benutzer auf dem Gerät ein blickbewegungsregistrierung Kalibrierung durch den Aufruf hat [EyesPose::IsCalibrationValid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid).  Verwenden Sie als Nächstes die [bestaunen](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) -Eigenschaft zum Abrufen der eine [SpatialRay](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) Contianing Auge bestaunen, Position und die Richtung. Die Blicke-Eigenschaft kann auch null sein, daher sollten Sie unbedingt dafür. Dies kann ist treten auf, wenn ein kalibrierten Benutzer vorübergehend ihren Augen Wirklichkeit schließt.

Der folgende Code zeigt, wie auf den Auge Blicke Strahl zugegriffen wird.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    if (pointerPose.Eyes() && pointerPose.Eyes().IsCalibrationValid())
    {
        if (pointerPose.Eyes().Gaze())
        {
            auto spatialRay = pointerPose.Eyes().Gaze().Value();
            float3 eyeGazeOrigin = spatialRay.Origin;
            float3 eyeGazeDirection = spatialRay.Direction;
            
            // Do something with the eye gaze
        }
    }
}

```

## <a name="correlating-gaze-with-other-inputs"></a>Korrelieren von Blicke mit anderen Eingaben

Manchmal können möglicherweise müssen Sie eine [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) , die mit einem Ereignis in der Vergangenheit entspricht. Z. B. wenn ein Air Tippen Sie auf der Benutzer ausführt, möchten Ihre app wissen, wonach sie gesucht haben, an. Zu diesem Zweck verwenden Sie einfach [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) mit den vorhergesagten Frame Zeit wäre ungenaue aufgrund der Latenz zwischen System Eingabeverarbeitung und anzeigen.

Eine Möglichkeit zum Behandeln dieses Szenarios ist, stellen einen zusätzlichen Aufruf [SpatialPointerPose::TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp), mit einem historischen Zeitstempel, der das Eingabeereignis entspricht.  Für die Eingabe, die über die SpatialInteractionManager weiterleitet, ist jedoch eine einfachere Methode. Die [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) hat seine eigenen [TryGetAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) Funktion. Aufrufen, die perfekt korrelierte bereitstellen [SpatialPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) ohne Frage. Weitere Informationen zum Arbeiten mit SpatialInteractionSourceStates sehen Sie sich die [Hände und Motion-Controller in DirectX](hands-and-motion-controllers-in-directx.md) Dokumentation.

## <a name="see-also"></a>Siehe auch
* [Praktische und Motion-Controllern in DirectX](hands-and-motion-controllers-in-directx.md)
* [Koordinatensysteme in DirectX](coordinate-systems-in-directx.md)
* [Blicke und Commit Eingabemodell](gaze-and-commit.md)

