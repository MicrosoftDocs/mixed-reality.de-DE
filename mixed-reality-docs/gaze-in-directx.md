---
title: Kopf-und Augenblick in DirectX
description: Entwicklerhandbuch zur Verwendung von Head-Blick und Eye-Nachverfolgung in nativen DirectX-apps.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: Blick, Head-Blick, Head-Tracking, Eye Tracking, DirectX, Input, holograms
ms.openlocfilehash: edf20a621178d76bfc97477f9f9b2eca200f1318
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414412"
---
# <a name="head-and-eye-gaze-input-in-directx"></a>Eingaben für Head-und Eye-Blick in DirectX

In Windows Mixed Reality werden die Eingaben für Eye und Head-Blick verwendet, um zu bestimmen, was der Benutzer sieht. Dies kann verwendet werden, um primäre Eingabe Modelle, wie z. b. [Kopf-und Commit](gaze-and-commit.md), zu steuern und um Kontext für Interaktions Typen bereitzustellen. Es gibt zwei Arten von Blick Vektoren, die über die API verfügbar sind: Kopf-und Augenblick.  Beide werden als dreidimensionale Ray mit einem Ursprung und einer Richtung bereitgestellt. Anwendungen können dann in Ihre Szenen oder in der realen Welt integriert werden und bestimmen, was der Benutzer als Ziel verwendet.

Die Kopfzeile stellt die Richtung dar, in der der Benutzer den Kopf zeigt. Stellen Sie sich dies als Position und Vorwärtsrichtung des Geräts selbst vor, wobei die Position den Mittelpunkt zwischen den beiden anzeigen darstellt.  Der Head-Blick ist auf allen Geräten mit gemischter Realität verfügbar.

**Eye Eye** stellt die Richtung dar, in der die Augen des Benutzers suchen. Der Ursprung befindet sich zwischen den Augen des Benutzers.  Es ist auf Geräten mit gemischter Realität verfügbar, die ein Augen Verfolgungssystem enthalten.

Mit der [spatialpointerpose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) -API kann auf beide Kopf-und Augenwinkel Strahlen zugegriffen werden. Sie können einfach [spatialpointerpose:: trygetattimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) aufrufen, um ein neues spatialpointerpose-Objekt am angegebenen Zeitstempel und [Koordinatensystem](coordinate-systems-in-directx.md)zu empfangen. Diese spatialpointerpose enthält den Ursprung und die Richtung des Haupt Blicks. Außerdem enthält Sie einen Blick auf den Ursprung und die Richtung des Augenblicks, wenn die Augen Verfolgung verfügbar ist.

## <a name="using-head-gaze"></a>Verwenden des Haupt Blicks

Um auf den Kopf Blick zuzugreifen, rufen Sie zunächst [spatialpointerpose:: trygetattimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) auf, um ein neues spatialpointerpose-Objekt zu erhalten. Sie müssen die folgenden Parameter übergeben.
 - Ein [spatialcoordinatesystem](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem) , das das gewünschte Koordinatensystem für den Kopf Blick darstellt. Dies wird von der *CoordinateSystem* -Variablen im folgenden Code dargestellt. Weitere Informationen finden Sie im Entwicklerhandbuch zu [Koordinatensystemen](coordinate-systems-in-directx.md) .
 - Ein [Zeitstempel](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) , der die genaue Uhrzeit der angeforderten Kopfzeile darstellt.  In der Regel verwenden Sie einen Zeitstempel, der der Uhrzeit entspricht, zu der der aktuelle Frame angezeigt wird. Sie können diesen vorhergesagten Anzeigezeit Stempel von einem [holographicframevorhersage](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) -Objekt erhalten, das über den aktuellen [holographicframe](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)zugänglich ist.  Dieses holographicframevorhersage-Objekt wird durch die *Vorhersage* Variable im folgenden Code dargestellt.

 Sobald Sie über eine gültige spatialpointerpose verfügen, sind die Kopf-und Vorwärtsrichtung als Eigenschaften zugänglich.  Der folgende Code zeigt, wie Sie darauf zugreifen können.

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

## <a name="using-eye-gaze"></a>Verwenden des Augenblicks

Die Eye-Blick-API ähnelt der Kopfzeile.  Dabei wird dieselbe [spatialpointerpose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) -API verwendet, die einen Strahl Ursprung und eine Richtung bereitstellt, die Sie für Ihre Szene bereitstellen können.  Der einzige Unterschied besteht darin, dass Sie die Eye-Nachverfolgung vor der Verwendung explizit aktivieren müssen. Hierfür müssen Sie zwei Schritte ausführen:
1. Fordern Sie die Benutzer Berechtigung zum Verwenden der Augen Verfolgung in Ihrer APP an.
2. Aktivieren Sie die Funktion "Blick auf Eingaben" in Ihrem Paket Manifest.

### <a name="requesting-access-to-gaze-input"></a>Anfordern des Zugriffs auf die Eingabe des Blicks
Wenn Ihre APP gestartet wird, können Sie [eyespose:: requestaccessasync](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) aufrufen, um den Zugriff auf die Eye-Nachverfolgung anzufordern. Das System fordert den Benutzer bei Bedarf auf und gibt " [gazeinputaccessstatus:: Allowed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.gazeinputaccessstatus) " zurück, nachdem der Zugriff gewährt wurde. Dabei handelt es sich um einen asynchronen-Befehl, der eine gewisse zusätzliche Verwaltung erfordert. Im folgenden Beispiel wird ein getrennter Std:: Thread aufgerufen, um auf das Ergebnis zu warten, das in einer Member-Variable mit dem Namen *m_isEyeTrackingEnabled*gespeichert wird.

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
Das Starten eines getrennten Threads ist nur eine Option für die Behandlung von asynchronen Aufrufen.  Alternativ könnten Sie die neue [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) -Funktionalität verwenden, die C++von/WinRT. unterstützt wird.
Im folgenden finden Sie ein weiteres Beispiel für das Anfordern von Benutzerberechtigungen:
-   Mit eyespose:: IsSupported () kann die Anwendung das Berechtigungs Dialogfeld nur aufrufen, wenn ein Eye Tracker vorhanden ist.
-   Gazinput Access Status m_gazeInputAccessStatus; Dadurch wird verhindert, dass die Berechtigungs Aufforderung immer wieder nach oben und wiederholt wird.

```cpp
GazeInputAccessStatus m_gazeInputAccessStatus; // This is to prevent popping up the permission prompt over and over again.

// This will trigger to show the permission prompt to the user.
// Ask for access if there is a corresponding device and registry flag did not disable it.
if (Windows::Perception::People::EyesPose::IsSupported() &&
   (m_gazeInputAccessStatus == GazeInputAccessStatus::Unspecified))
{ 
    Concurrency::create_task(Windows::Perception::People::EyesPose::RequestAccessAsync()).then(
    [this](GazeInputAccessStatus status)
    {
        // GazeInputAccessStatus::{Allowed, DeniedBySystem, DeniedByUser, Unspecified}
            m_gazeInputAccessStatus = status;
        
        // Let's be sure to not ask again.
        if(status == GazeInputAccessStatus::Unspecified)
        {
                m_gazeInputAccessStatus = GazeInputAccessStatus::DeniedBySystem;    
        }
    });
}

```


### <a name="declaring-the-gaze-input-capability"></a>Deklarieren der *Blick Eingabe* Funktion

Doppelklicken Sie in *Projektmappen-Explorer*auf die Datei appxmanifest.  Navigieren Sie dann zum Abschnitt " *Funktionen* ", und überprüfen Sie die Funktion " *Blick Eingaben* " 

![Blick Eingabe Funktion](images/gaze-input-capability.png)

Dadurch werden dem *Paket* Abschnitt in der appxmanifest-Datei die folgenden Zeilen hinzugefügt:
```xml
  <Capabilities>
    <DeviceCapability Name="gazeInput" />
  </Capabilities>
```

### <a name="getting-the-eye-gaze-ray"></a>Der Eye-Blick Strahl
Nachdem Sie den Zugriff auf das et erhalten haben, können Sie den Augenblick Strahl jedes Frame abrufen.  Rufen Sie das [spatialpointerpose](https://docs.microsoft.com/en-us/uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) -Attribut wie bei Head-Blick durch Aufrufen von [spatialpointerpose:: trygetattimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) mit einem gewünschten Zeitstempel und Koordinatensystem ab. Spatialpointerpose enthält ein [eyespose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose) -Objekt über die [Augen](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) Eigenschaft. Dieser Wert ist nur ungleich NULL, wenn die Eye-Nachverfolgung aktiviert ist. Von dort aus können Sie überprüfen, ob der Benutzer auf dem Gerät über eine Eye Tracking-Kalibrierung verfügt, indem Sie [eyespose:: iscalibrationvalid](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)aufrufen.  Verwenden Sie als nächstes die Eigenschaft " [Blick](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) ", um ein [spatialray](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialray) zu erhalten, das die Position und Richtung des Augenblicks zusammen hängelt. Die Eigenschaft "Blick" kann in manchen Fällen NULL sein. Achten Sie daher darauf, dies zu überprüfen. Dies kann vorkommen, wenn ein Benutzer mit einem kalibrierten Benutzer die Augen vorübergehend schließt.

Der folgende Code zeigt, wie Sie auf den Augenblick-Ray zugreifen können.

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

## <a name="correlating-gaze-with-other-inputs"></a>Korrelieren von Blick mit anderen Eingaben

Manchmal stellen Sie möglicherweise fest, dass Sie eine [spatialpointerpose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) benötigen, die einem Ereignis in der Vergangenheit entspricht. Wenn der Benutzer beispielsweise eine Klimaanlage durchführt, möchte Ihre APP möglicherweise wissen, was Sie sich angeschaut haben. Zu diesem Zweck wäre die einfache Verwendung von [spatialpointerpose:: trygetattimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) mit der vorhergesagten Frame Zeit aufgrund der Latenz zwischen der System Eingabe Verarbeitung und der Anzeigezeit ungenau. Wenn Sie den Augenblick für das anvisieren verwenden, werden die Augen darüber hinaus weiter bewegt, bevor eine Commit-Aktion abgeschlossen wird. Dabei handelt es sich weniger um ein Problem bei einer einfachen Luft tippen, aber es wird wichtiger, wenn Sie lange Sprachbefehle mit fast-Eye-Bewegungen kombinieren. Eine Möglichkeit zur Behandlung dieses Szenarios besteht darin, einen zusätzlichen aufzurufenden [spatialpointerpose:: trygetattimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)mithilfe eines historischen Zeitstempels zu erstellen, der dem Eingabe Ereignis entspricht.  

Bei Eingaben, die den spatialinteraktionmanager weiterleiten, gibt es jedoch eine einfachere Methode. Der [spatialinteraktionsourcestate](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) verfügt über seine eigene [trygetattimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) -Funktion. Der Aufruf von, der eine perfekt korrelierte [spatialpointerpose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerpose) ohne den "Guess work" bereitstellt. Weitere Informationen zum Arbeiten mit spatialinteraktionsourcestates finden Sie [in den Hand-und Bewegungs Controllern in der DirectX-](hands-and-motion-controllers-in-directx.md) Dokumentation.

## <a name="see-also"></a>Siehe auch
* [Kopf-und Commit-Eingabe Modell](gaze-and-commit.md)
* [Blick auf hololens 2](eye-tracking.md)
* [Koordinatensysteme in DirectX](coordinate-systems-in-directx.md)
* [Spracheingabe in DirectX](voice-input-in-directx.md)
* [Hände und Motion-Controller in DirectX](hands-and-motion-controllers-in-directx.md)
