---
title: Kopf-und Augenblick in DirectX
description: Entwicklerhandbuch zur Verwendung von Head-Blick und Eye-Nachverfolgung in nativen DirectX-apps.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 05/09/2019
ms.topic: article
keywords: Augenblick, Haupt Blick, Head-Tracking, Eye Tracking, DirectX, Input, holograms
ms.openlocfilehash: 664657b9ab01530a608e31091823e828cc99d0cd
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926557"
---
# <a name="head-gaze-and-eye-gaze-input-in-directx"></a>Eingaben in den Kopf-und Augenblick in DirectX

In Windows Mixed Reality werden die Eingaben für Eye und Head-Blick verwendet, um zu bestimmen, was der Benutzer sieht. Dies kann verwendet werden, um primäre Eingabe Modelle, wie z. b. [Kopf-und Commit](gaze-and-commit.md), zu steuern und um Kontext für Interaktions Typen bereitzustellen. Es gibt zwei Arten von Blick Vektoren, die über die API bereitgestellt werden: Kopf-und Augenblick.  Beide werden als dreidimensionale Ray mit einem Ursprung und einer Richtung bereitgestellt. Anwendungen können dann in Ihre Szenen oder in der realen Welt integriert werden und bestimmen, was der Benutzer als Ziel verwendet.

Der **Kopf** zeilig stellt die Richtung dar, in der die Kopfzeile des Benutzers gezeigt wird. Stellen Sie sich dies als Position und Vorwärtsrichtung des Geräts selbst vor, wobei die Position den Mittelpunkt zwischen den beiden anzeigen darstellt. Der Haupt Blick ist auf allen Geräten mit gemischter Realität verfügbar.

Der Augen **Blick** stellt die Richtung dar, in der die Augen des Benutzers suchen. Der Ursprung befindet sich zwischen den Augen des Benutzers.  Es ist auf Geräten mit gemischter Realität verfügbar, die ein Augen Verfolgungssystem enthalten.

Mit der [spatialpointerpose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) -API ist sowohl der Kopf-als auch der Augenblick-Strahlen zugänglich. Sie können einfach [spatialpointerpose:: trygetattimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) aufrufen, um ein neues spatialpointerpose-Objekt am angegebenen Zeitstempel und [Koordinatensystem](coordinate-systems-in-directx.md)zu empfangen. Diese spatialpointerpose enthält den Ursprung und die Richtung des Haupt Blicks. Sie enthält außerdem einen Blick auf den Ursprung und die Richtung des Augenblicks, wenn die Augen Verfolgung verfügbar ist.

### <a name="device-support"></a>Unterstützung von Geräten
<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Funktion</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
</tr>
<tr>
     <td>Anvisieren mit dem Kopf</td>
     <td>✔️</td>
     <td>✔️</td>
     <td>✔️</td>
</tr>
<tr>
     <td>Augenblick</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="using-head-gaze"></a>Verwenden des Haupt Blicks

Um auf den Kopf Blick zuzugreifen, rufen Sie zunächst [spatialpointerpose:: trygetattimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) auf, um ein neues spatialpointerpose-Objekt zu erhalten. Sie müssen die folgenden Parameter übergeben.
 - Ein [spatialcoordinatesystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) , das das gewünschte Koordinatensystem für den Haupt Blick darstellt. Dies wird von der *CoordinateSystem* -Variablen im folgenden Code dargestellt. Weitere Informationen finden Sie im Entwicklerhandbuch zu [Koordinatensystemen](coordinate-systems-in-directx.md) .
 - Ein [Zeitstempel](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframeprediction.timestamp#Windows_Graphics_Holographic_HolographicFramePrediction_Timestamp) , der die genaue Uhrzeit der angeforderten Kopfzeile darstellt.  In der Regel verwenden Sie einen Zeitstempel, der der Uhrzeit entspricht, zu der der aktuelle Frame angezeigt wird. Sie können diesen vorhergesagten Anzeigezeit Stempel von einem [holographicframevorhersage](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) -Objekt erhalten, das über den aktuellen [holographicframe](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)zugänglich ist.  Dieses holographicframevorhersage-Objekt wird durch die *Vorhersage* Variable im folgenden Code dargestellt.

 Sobald Sie über eine gültige spatialpointerpose verfügen, sind die Kopf-und Vorwärtsrichtung als Eigenschaften zugänglich.  Der folgende Code zeigt, wie Sie darauf zugreifen können.

 ```cpp
using namespace winrt::Windows::UI::Input::Spatial;
using namespace winrt::Windows::Foundation::Numerics;

SpatialPointerPose pointerPose = SpatialPointerPose::TryGetAtTimestamp(coordinateSystem, prediction.Timestamp());
if (pointerPose)
{
    float3 headPosition = pointerPose.Head().Position();
    float3 headForwardDirection = pointerPose.Head().ForwardDirection();

    // Do something with the head-gaze
}
```

## <a name="using-eye-gaze"></a>Verwenden des Augenblicks

Beachten Sie, dass die Benutzer bei der erstmaligen Verwendung des Geräts über eine [Eye-Tracking-benutzerkalibrierung](calibration.md) verfügen müssen. Die Eye-Eye-API ähnelt der Kopfzeile.
Dabei wird dieselbe [spatialpointerpose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) -API verwendet, die einen Strahl Ursprung und eine Richtung bereitstellt, die Sie für Ihre Szene bereitstellen können.  Der einzige Unterschied besteht darin, dass Sie die Eye-Nachverfolgung vor der Verwendung explizit aktivieren müssen. Hierfür müssen Sie zwei Schritte ausführen:
1. Fordern Sie die Benutzer Berechtigung zum Verwenden der Augen Verfolgung in Ihrer APP an.
2. Aktivieren Sie die Funktion "Blick auf Eingaben" in Ihrem Paket Manifest.

### <a name="requesting-access-to-eye-gaze-input"></a>Anfordern des Zugriffs auf die Eingabe des Augenblicks
Wenn Ihre APP gestartet wird, können Sie [eyespose:: requestaccessasync](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.requestaccessasync#Windows_Perception_People_EyesPose_RequestAccessAsync) aufrufen, um den Zugriff auf die Eye-Nachverfolgung anzufordern. Das System fordert den Benutzer bei Bedarf auf und gibt " [gazeinputaccessstatus:: Allowed](https://docs.microsoft.com//uwp/api/windows.ui.input.gazeinputaccessstatus) " zurück, nachdem der Zugriff gewährt wurde. Dabei handelt es sich um einen asynchronen-Befehl, der eine gewisse zusätzliche Verwaltung erfordert. Im folgenden Beispiel wird ein getrennter Std:: Thread aufgerufen, um auf das Ergebnis zu warten, das in einer Element Variablen mit dem Namen *m_isEyeTrackingEnabled*gespeichert wird.

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
Das Starten eines getrennten Threads ist nur eine Option für die Behandlung von asynchronen Aufrufen. Alternativ dazu können Sie die neue von [](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) C++/WinRT. unterstützte co_await Funktionalität verwenden.
Im folgenden finden Sie ein weiteres Beispiel für das Anfordern von Benutzerberechtigungen:
-   Mit eyespose:: IsSupported () kann die Anwendung das Berechtigungs Dialogfeld nur aufrufen, wenn ein Eye Tracker vorhanden ist.
-   Gazinput Access Status-m_gazeInputAccessStatus; Dadurch wird verhindert, dass die Berechtigungs Aufforderung immer wieder nach oben und wiederholt wird.

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

### <a name="getting-the-eye-gaze-ray"></a>Der Augenblick Strahl
Nachdem Sie den Zugriff auf das et erhalten haben, können Sie den Augenblick Strahl jedes Frame abrufen.
Rufen Sie das [spatialpointerpose](https://docs.microsoft.com//uwp/api/Windows.UI.Input.Spatial.SpatialPointerPose) -Attribut wie bei der Kopfzeile durch Aufrufen von [spatialpointerpose:: trygetattimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) mit einem gewünschten Zeitstempel und Koordinatensystem ab. Spatialpointerpose enthält ein [eyespose](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose) -Objekt über die [Augen](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.eyes) Eigenschaft. Dieser Wert ist nur ungleich NULL, wenn die Eye-Nachverfolgung aktiviert ist. Von dort aus können Sie überprüfen, ob der Benutzer auf dem Gerät über eine Eye Tracking-Kalibrierung verfügt, indem Sie [eyespose:: iscalibrationvalid](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid)aufrufen.  Verwenden Sie als nächstes die Eigenschaft " [Blick](https://docs.microsoft.com//uwp/api/windows.perception.people.eyespose.gaze#Windows_Perception_People_EyesPose_Gaze) ", um ein [spatialray](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialray) mit der Position und Richtung des Augenblicks zu erhalten. Die Eigenschaft "Blick" kann in manchen Fällen NULL sein. Achten Sie daher darauf, dies zu überprüfen. Dies kann vorkommen, wenn ein Benutzer mit einem kalibrierten Benutzer die Augen vorübergehend schließt.

Der folgende Code zeigt, wie Sie auf den Augenblick-Strahl zugreifen können.

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
            
            // Do something with the eye-gaze
        }
    }
}

```

## <a name="fallback-when-eye-tracking-is-not-available"></a>Fallback, wenn die Augen Verfolgung nicht verfügbar ist
Wie in unserer Design Dokumentation für die [Augen Verfolgung](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available)erwähnt, sollten sowohl Designer als auch Entwickler wissen, dass es Instanzen geben kann, in denen Überwachungsdaten für Ihre APP möglicherweise nicht verfügbar sind.
Es gibt verschiedene Gründe dafür, dass ein Benutzer, der nicht gerade nicht gerade nicht gerade ist, den Zugriff der APP auf seine Überwachungsdaten oder einfach auf temporäre Störungen (wie z. b. smudges auf den hololens-Hypervisor oder das Haar Ausblenden der Augen des Benutzers) verweigert. Einige der APIs wurden bereits in diesem Dokument erwähnt. im folgenden finden Sie eine Übersicht darüber, wie Sie erkennen können, dass die Augen Verfolgung als Kurzübersicht verfügbar ist: 

* Überprüfen Sie, ob das System die Augen Verfolgung unterstützt. Wenden Sie die folgende *Methode*an: [Windows. perception. People. eyespose. IsSupported ()](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.issupported#Windows_Perception_People_EyesPose_IsSupported)

* Überprüfen Sie, ob der Benutzer auf eine Kalibrierung fest. Folgende *Eigenschaft*aufzurufen: [Windows. perception. People. eyespose. iscalibrationvalid](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose.iscalibrationvalid#Windows_Perception_People_EyesPose_IsCalibrationValid) 

* Überprüfen Sie, ob der Benutzer Ihre APP berechtigt hat, ihre Überwachungsdaten zu verwenden: Rufen Sie den aktuellen _"gazeinputaccessstatus"_ ab. Ein Beispiel hierfür finden Sie unter [anfordern des Zugriffs auf die Eingabe](https://docs.microsoft.com/windows/mixed-reality/gaze-in-directX#requesting-access-to-gaze-input).   

Darüber hinaus können Sie überprüfen, ob Ihre Augen Verfolgungs Daten nicht veraltet sind, indem Sie ein Timeout zwischen empfangenen Datenaktualisierungen für die Augen Verfolgung hinzufügen und andernfalls auf den Haupt Blick zurückgreifen, wie unten erläutert.  
Weitere Informationen finden Sie in unseren [Fall Back Entwurfs Überlegungen](eye-tracking.md#fallback-solutions-when-eye-tracking-is-not-available) .

<br>

## <a name="correlating-gaze-with-other-inputs"></a>Korrelieren von Blick mit anderen Eingaben
Manchmal stellen Sie möglicherweise fest, dass Sie eine [spatialpointerpose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) benötigen, die einem Ereignis in der Vergangenheit entspricht. Wenn der Benutzer beispielsweise eine Klimaanlage durchführt, möchte Ihre APP möglicherweise wissen, was Sie sich angeschaut haben. Zu diesem Zweck wäre die einfache Verwendung von [spatialpointerpose:: trygetattimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp) mit der vorhergesagten Frame Zeit aufgrund der Latenz zwischen der System Eingabe Verarbeitung und der Anzeigezeit ungenau. Wenn Sie den Augenblick für das anvisieren verwenden, werden die Augen darüber hinaus weiter bewegt, bevor eine Commit-Aktion abgeschlossen wird. Dabei handelt es sich weniger um ein Problem bei einer einfachen Luft tippen, aber es wird wichtiger, wenn Sie lange Sprachbefehle mit fast-Eye-Bewegungen kombinieren. Eine Möglichkeit zur Behandlung dieses Szenarios besteht darin, einen zusätzlichen aufzurufenden [spatialpointerpose:: trygetattimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose.trygetattimestamp)mithilfe eines historischen Zeitstempels zu erstellen, der dem Eingabe Ereignis entspricht.  

Bei Eingaben, die den spatialinteraktionmanager weiterleiten, gibt es jedoch eine einfachere Methode. Der [spatialinteraktionsourcestate](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) verfügt über seine eigene [trygetattimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) -Funktion. Der Aufruf von, der eine perfekt korrelierte [spatialpointerpose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerpose) ohne den "Guess work" bereitstellt. Weitere Informationen zum Arbeiten mit spatialinteraktionsourcestates finden Sie [in den Hand-und Bewegungs Controllern in der DirectX-](hands-and-motion-controllers-in-directx.md) Dokumentation.

<br>

## <a name="calibration"></a>Energie
Damit die Eye-Nachverfolgung ordnungsgemäß funktioniert, muss jeder Benutzer über eine [Eye Tracking-benutzerkalibrierung](calibration.md)verfügen. Dies ermöglicht es dem Gerät, das System für eine komfortablere und qualitativ hochwertige Anzeige für den Benutzer anzupassen und gleichzeitig eine genaue Eye-Nachverfolgung sicherzustellen. Entwickler müssen nichts auf Ihrem Ende durchführen, um die benutzerkalibrierung zu verwalten. Das System stellt sicher, dass der Benutzer in den folgenden Situationen aufgefordert wird, das Gerät zu kalibrieren:
* Der Benutzer verwendet das Gerät zum ersten Mal.
* Der Benutzer hat sich zuvor für den Kalibrierungsprozess entschieden.
* Der Kalibrierungsprozess war nicht erfolgreich, als der Benutzer das Gerät zum letzten Mal verwendet hat.

Entwickler sollten sicherstellen, dass Sie angemessene Unterstützung für Benutzer bereitstellen, für die die Augen Verfolgungs Daten möglicherweise nicht verfügbar sind. Erfahren Sie mehr über Überlegungen zu Fall Back-Lösungen bei der [Überwachung von hololens 2](eye-tracking.md).

<br>

## <a name="see-also"></a>Weitere Informationen
* [Kalibrierung](calibration.md)
* [Koordinatensysteme in DirectX](coordinate-systems-in-directx.md)
* [Blick auf hololens 2](eye-tracking.md)
* [Überblicks-und Commit-Eingabe Modell](gaze-and-commit.md)
* [Hände und Motion-Controller in DirectX](hands-and-motion-controllers-in-directx.md)
* [Spracheingabe in DirectX](voice-input-in-directx.md)
