---
title: QR-Code Nachverfolgung
description: Erfahren Sie, wie Sie QR-Codes auf hololens 2 erkennen.
author: dorreneb
ms.author: dobrown
ms.date: 05/15/2019
ms.topic: article
keywords: VR, LBE, Location based Entertainment, VR-Arkade, Arcade, immersive, QR, QR-Code, hololens2
ms.openlocfilehash: 736ab265db2145dd784c435e525059ed3a2fcbbb
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047160"
---
# <a name="qr-code-tracking"></a>QR-Code Nachverfolgung

Hololens 2 kann QR-Codes in der Umgebung um das Headset erkennen und ein Koordinatensystem an der realen Position jedes Codes einrichten.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Feature</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (1. Generation)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> QR-Code Erkennung</td><td style="text-align: center;">️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">Siehe Hinweis</td>
</tr>
</table>

>[!NOTE]
>Die Unterstützung von immersiven Windows Mixed Reality-Headsets auf Desktop-PCs wird derzeit nicht mit dem unten aufgeführten nuget-Paket unterstützt.  Bleiben Sie auf dem neuesten Stand der Desktop Unterstützung.

## <a name="getting-the-qr-package"></a>Erhalten des QR-Pakets
[Hier](https://github.com/dorreneb/mixed-reality/releases)können Sie ein nuget-Paket für die QR-Code Erkennung herunterladen.

Zukünftige Versionen dieses Pakets sind über das öffentliche nuget-Paketrepository verfügbar.

## <a name="detecting-qr-codes"></a>Erkennen von QR-Codes

### <a name="adding-the-webcam-capability"></a>Hinzufügen der Webcam-Funktion
Sie müssen die Funktion `webcam` ihrem Manifest hinzufügen, um QR-Codes zu erkennen. Diese Funktion ist erforderlich, da die Daten in erkannten Codes in der Benutzerumgebung möglicherweise vertrauliche Informationen enthalten.

Die Berechtigung kann durch Aufrufen `QRCodeWatcher.RequestAccessAsync()`von angefordert werden:

_C#:_
```cs
await QRCodeWatcher.RequestAccessAsync();
```

_C++:_
```cpp
co_await QRCodeWatcher.RequestAccessAsync();
```

Vor dem Erstellen eines qrcodewatcher-Objekts muss eine Berechtigung angefordert werden.

Obwohl die Erkennung von QR- `webcam` Code die Funktion erfordert, erfolgt die Erkennung mithilfe der Überwachungskameras des Geräts. Dies bietet einen umfassenderen Erkennungs FOV und eine bessere Akku Lebensdauer im Vergleich zur Erkennung mit der Photo/Video (PV)-Kamera des Geräts.

### <a name="detecting-qr-codes-in-unity"></a>Erkennen von QR-Codes in Unity

Sie können die QR-Code Erkennungs-API in Unity verwenden, ohne eine Abhängigkeit von mrtk zu treffen. Zu diesem Zweck müssen Sie folgende Schritte ausführen:

1. Erstellen Sie einen neuen Ordner im Ordner "Assets" Ihres Unity-Projekts mitden Namen-Plug-ins.
2. Kopieren Sie alle erforderlichen Dateien aus diesem Ordner in den lokalen Ordner "Plug-ins", den Sie soeben erstellt haben.

Es gibt eine Beispiel-Unity-APP, die ein Holographic-Quadrat über QR-Codes anzeigt, zusammen mit den zugehörigen Daten wie GUID, physischer Größe, timestamp und decodierten Daten. Diese APP befindet sich unter https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes.

### <a name="detecting-qr-codes-in-c"></a>Erkennen von QR-Codes inC++

>[!NOTE]
>Die C++ Code Ausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstelle von C + +17-kompatibler C++/WinRT, wie Sie in der [ C++ Holographic-Projektvorlage](creating-a-holographic-directx-project.md)verwendet werden. Die Konzepte sind äquivalent für ein C++/WinRT-Projekt, obwohl Sie den Code übersetzen müssen.

```
using namespace Microsoft.MixedReality.QR;

    public ref class QRListHelper sealed
    {
    public:
        QRListHelper()
        {

        }

        void setApp(SpatialStageManager* pStage)
        {
            m_pStage = pStage;
        }

        void SetUpQRCodes()
        {
            if (QRCodeWatcher::IsSupported())
            {
                auto operation = QRCodeWatcher::RequestAccessAsync();

                WeakReference weakThis(this);

                operation->Completed = ref new AsyncOperationCompletedHandler<QRCodeWatcherAccessStatus>(
                    [weakThis](IAsyncOperation< QRCodeWatcherAccessStatus>^ operaion, AsyncStatus status)
                {
                    QRListHelper^ QRListHelper = weakThis.Resolve<QRListHelper>();
                    if (status == AsyncStatus::Completed)
                    {
                        QRListHelper->InitializeQR( operaion->GetResults());
                    }
                }
                );
            }
        }

    private:
        void OnAddedQRCode(Object^, QRCodeAddedEventArgs ^args)
        {
            m_pStage->OnAddedQRCode(args);
        }
        void OnUpdatedQRCode(Object^, QRCodeUpdatedEventArgs ^args)
        {
            m_pStage->OnUpdatedQRCode(args);
        }
        void OnEnumerationComplete(Object^, Object^)
        {
            m_pStage->OnEnumerationComplete();
        }

        SpatialStageManager* m_pStage;
        QRCodeWatcher^ m_qrWatcher;



        void InitializeQR(QRCodeWatcherAccessStatus status)
        {
            if (status == QRCodeWatcherAccessStatus::Allowed)
            {
                m_qrWatcher = ref new QRCodeWatcher();

                m_qrWatcher->Added += ref new EventHandler<Object^, QRCodeAddedEventArgs^>(this, &QRListHelper::OnAddedQRCode);
                m_qrWatcher->Updated += ref new EventHandler<Object^, QRCodeUpdatedEventArgs^>(this, &QRListHelper::OnUpdatedQRCode);
                m_qrWatcher->EnumerationCompleted += ref new EventHandler<Object^, Object^>(this, &QRListHelper::OnEnumerationComplete);
                try
                {
                    m_qrWatcher->Start();
                }
                catch (...)
                {

                }
            }
            else
            {
                // Permission denied by system or user
                // Handle the failures
            }
        }
    }; 
```

## <a name="getting-the-coordinate-system-for-a-qr-code"></a>Erhalten des Koordinatensystems für einen QR-Code

Jeder erkannte QR-Code macht ein [räumliches Koordinatensystem](coordinate-systems.md) verfügbar, das mit dem QR-Code in der oberen linken Ecke des oberen linken Rands des schnell Erkennungs Quadrats ausgerichtet ist, wie unten gezeigt.  Wenn Sie das QR SDK direkt verwenden, zeigt die z-Achse auf das Papier (nicht angezeigt): bei der Konvertierung in Unity-Koordinaten verweist die z-Achse auf das Papier und wird von Links entfernt.

Das spatialcoordinatesystem eines QR-Codes wird angezeigt. Dieses Koordinatensystem kann von der Plattform abgerufen werden, indem Sie <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createcoordinatesystemfornode" target="_blank">spatialgraphinteroppreview:: createcoordinatesystemfornode</a> aufrufen und die spatialgraphnodeid des Codes übergeben.

![QR-Code Koordinatensystem](images/Qr-coordinatesystem.png) 

Für ein QRCode-Objekt zeigt der C++folgende/CX-Code, wie ein Rechteck erstellt und mithilfe des Koordinatensystems des QR-Codes platziert wird:

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> SpatialStageManager::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0, 0, 0 };
    vertices[1] = { width, 0, 0 };
    vertices[2] = { width, height, 0 };
    vertices[3] = { 0, height, 0 };

    return vertices;
}
```

Sie können die physische Größe zum Erstellen des QR-Rechtecks verwenden:

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

Das Koordinatensystem kann zum Zeichnen des QR-Codes oder zum Anfügen von holograms an den Speicherort verwendet werden:

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->SpatialGraphNodeId);
```

Der *qrcodewatcher:: qrcodeaddedhandler* könnte etwa wie folgt aussehen:

```cpp
void MyClass::OnAddedQRCode(Object ^sender, QRCodeWatcher::QRCodeAddedEventArgs ^args)
{
    std::vector<float3> qrVertices = CreateRectangle(args->Code->PhysicalSizeMeters, args->Code->PhysicalSizeMeters);
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem =  Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(args->Code->SpatialGraphNodeId);
    std::shared_ptr<SceneObject> m_qrShape =
        std::make_shared<SceneObject>(
            m_deviceResources,
            reinterpret_cast<std::vector<XMFLOAT3>&>(qrVertices),
            qrCodeIndices,
            qrAreaColor,
            qrCoordinateSystem);

    m_sceneController->AddSceneObject(m_qrShape);
}
```

## <a name="best-practices-for-qr-code-detection"></a>Bewährte Methoden für die Erkennung von QR-Codes

### <a name="quiet-zones-around-qr-codes"></a>Stille Zonen um QR-Codes

Um ordnungsgemäß gelesen zu werden, erfordern QR-Codes einen Rand um alle Seiten des Codes. Dieser Rand darf keine gedruckten Inhalte enthalten und sollte vier Module (ein einzelnes schwarzes Quadrat im Code) enthalten. 

Die [QR-Spezifikation](https://www.qrcode.com/en/howto/code.html) enthält weitere Informationen zu stillen Zonen.

### <a name="lighting-and-backdrop"></a>Beleuchtung und Hintergrund
Die Qualität der QR-Code Erkennung ist anfällig für die unterschiedliche Beleuchtung und den Hintergrund. 

Drucken Sie in einer Szene mit besonders heller Beleuchtung einen Code, der in einem grauen Hintergrund schwarz ist. Andernfalls drucken Sie einen schwarzen QR-Code in einem weißen Hintergrund.

Wenn der Hintergrund des Codes besonders dunkel ist, versuchen Sie es mit einem grauen Code, wenn die Erkennungsrate niedrig ist. Wenn die Kulisse relativ hell ist, sollte ein regulärer Code einwandfrei funktionieren.

### <a name="size-of-qr-codes"></a>Größe der QR-Codes
Windows Mixed Reality-Geräte funktionieren nicht mit QR-Codes mit Seiten, die kleiner als 5 cm sind.

Bei QR-Codes zwischen 5 und 10 cm-Längen Seiten müssen Sie den Code relativ nah sehen. Außerdem dauert es länger, bis Codes mit dieser Größe erkannt werden. 

Die genaue Zeit zum Erkennen von Codes hängt nicht nur von der Größe der QR-Codes ab, sondern von der Entfernung des Codes. Wenn Sie sich näher an den Code bewegen, können Probleme mit der Größe abgeglichen werden.

### <a name="distance-and-angular-position-from-the-qr-code"></a>Entfernung und Winkelposition aus dem QR-Code
Die Überwachungskameras können nur eine bestimmte Detailebene erkennen. Bei wirklich kleinen Codes-< 10cm auf den Seiten müssen Sie ziemlich nah sein. Bei einem QR-Code der Version 1, der zwischen 10 und 25 cm breit ist, reicht der minimale Erkennungsabstand zwischen 0,15 und 0,5 Meter. 

Der Erkennungsabstand für die Größe erhöht sich linear. 

Die QR-Erkennung funktioniert mit einem Bereich von Winkeln + = 45deg. Dadurch wird sichergestellt, dass die richtige Lösung für die Erkennung des Codes vorhanden ist.

### <a name="qr-codes-with-logos"></a>QR-Codes mit Logos
QR-Codes mit Logos wurden nicht getestet und werden zurzeit nicht unterstützt.

### <a name="managing-qr-code-data"></a>Verwalten von QR-Codedaten
Windows Mixed Reality-Geräte erkennen QR-Codes auf der Systemebene des Treibers. Wenn das Gerät neu gestartet wird, sind die erkannten QR-Codes verschwunden und werden als neue Objekte das nächste Mal wiedererkannt.

Es wird empfohlen, die APP so zu konfigurieren, dass Sie QR-Codes ignoriert, die älter sind als ein bestimmter Zeitstempel Derzeit unterstützt die API das Löschen von QR-Code Verläufen nicht.

### <a name="qr-code-placement-in-a-space"></a>QR-Code Platzierung in einem Leerzeichen
Empfehlungen dazu, wo und wie QR-Codes platziert werden, finden Sie unter [Überlegungen zur Umgebung für hololens](environment-considerations-for-hololens.md).

## <a name="qr-api-reference"></a>QR-API-Referenz

```cs
namespace Microsoft.MixedReality.QR
{
    /// <summary>
    /// Represents a detected QR code.
    /// </remarks>
    public class QRCode
    {
        /// <summary>
        /// Unique id that identifies this QR code for this session.
        /// </summary>
        public Guid Id { get; }

        /// <summary>
        /// Spatial graph node id for this QR code to create a coordinate system.
        /// </summary>
        public Guid SpatialGraphNodeId { get; }

        /// <summary>
        /// Version of this QR code. Version 1-40 are regular QR codes and 41-44 are Micro QR code formats 1-4.
        /// </summary>
        public VersionInfo Version { get; }

        /// <summary>
        /// Physical width and height of this QR code in meters.
        /// </summary>
        public float PhysicalSideLength { get; }

        /// <summary>
        /// Decoded QR code data.
        /// </summary>
        public String Data { get; }

        /// <summary>
        /// Size of the RawData of this QR code.
        /// </summary>
        public UInt32 RawDataSize { get; }

        /// <summary>
        /// Gets the error-corrected raw data bytes.
        /// Used when the platform is unable to decode the code's format,
        /// allowing your app to decode as needed.
        /// </summary>
        public void GetRawData(byte[] buffer);

        /// <summary>
        /// The last detected time in 100ns QPC ticks.
        /// </summary>
        public System.TimeSpan SystemRelativeLastDetectedTime { get; }

        /// <summary>
        /// The last detected time.
        /// </summary>
        public System.DateTimeOffset LastDetectedTime { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Added event.
    /// </summary>
    public class QRCodeAddedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was added
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Removed event.
    /// </summary>
    public class QRCodeRemovedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was removed.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Event arguments for a QRCodeWatcher's Updated event.
    /// </summary>
    public class QRCodeUpdatedEventArgs
    {
        /// <summary>
        /// Gets the QR Code that was updated.
        /// </summary>
        public QRCode Code { get; }
    }

    /// <summary>
    /// Represents the status of an access request for QR code detection.
    /// </summary>
    public enum QRCodeWatcherAccessStatus
    {
        /// <summary>
        /// The system has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedBySystem = 0,
        /// <summary>
        /// The app has not declared the webcam capability in its manifest.
        /// </summary>
        NotDeclaredByApp = 1,
        /// <summary>
        /// The user has denied permission for the app to detect QR codes.
        /// </summary>
        DeniedByUser = 2,
        /// <summary>
        /// A user prompt is required to get permission to detect QR codes.
        /// </summary>
        UserPromptRequired = 3,
        /// <summary>
        /// The user has given permission to detect QR codes.
        /// </summary>
        Allowed = 4,
    }

    /// <summary>
    /// Detects QR codes in the user's environment.
    /// </summary>
    public class QRCodeWatcher
    {
        /// <summary>
        /// Gets whether QR code detection is supported on the current device.
        /// </summary>
        public static bool IsSupported();

        /// <summary>
        /// Request user consent before using QR code detection.
        /// </summary>
        public static IAsyncOperation<QRCodeWatcherAccessStatus> RequestAccessAsync();

        /// <summary>
        /// Constructs a new QRCodeWatcher.
        /// </summary>
        public QRCodeWatcher();

        /// <summary>
        /// Starts detecting QR codes.
        /// </summary>
        /// <remarks>
        /// Start should only be called once RequestAccessAsync has succeeded.
        /// Start should not be called if QR code detection is not supported.
        /// Check that IsSupported returns true before calling Start.
        /// </remarks>
        public void Start();

        /// <summary>
        /// Stops detecting QR codes.
        /// </summary>
        public void Stop();

        /// <summary>
        /// Get the list of QR codes detected.
        /// </summary>
        /// <remarks>
        /// </remarks>
        public IList<QRCode> GetList();

        /// <summary>
        /// Event representing the addition of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeAddedEventArgs> Added;

        /// <summary>
        /// Event representing the removal of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeRemovedEventArgs> Removed;

        /// <summary>
        /// Event representing the update of a QR Code.
        /// </summary>
        public event EventHandler<QRCodeUpdatedEventArgs> Updated;

        /// <summary>
        /// Event representing the enumeration of QR Codes completing after a Start call.
        /// </summary>
        public event EventHandler<Object> EnumerationCompleted;
    }

    /// <summary>
    /// Version info for QR codes, including Micro QR codes.
    /// </summary>
    public enum VersionInfo
    {
        QR1 = 1,
        QR2 = 2,
        QR3 = 3,
        QR4 = 4,
        QR5 = 5,
        QR6 = 6,
        QR7 = 7,
        QR8 = 8,
        QR9 = 9,
        QR10 = 10,
        QR11 = 11,
        QR12 = 12,
        QR13 = 13,
        QR14 = 14,
        QR15 = 15,
        QR16 = 16,
        QR17 = 17,
        QR18 = 18,
        QR19 = 19,
        QR20 = 20,
        QR21 = 21,
        QR22 = 22,
        QR23 = 23,
        QR24 = 24,
        QR25 = 25,
        QR26 = 26,
        QR27 = 27,
        QR28 = 28,
        QR29 = 29,
        QR30 = 30,
        QR31 = 31,
        QR32 = 32,
        QR33 = 33,
        QR34 = 34,
        QR35 = 35,
        QR36 = 36,
        QR37 = 37,
        QR38 = 38,
        QR39 = 39,
        QR40 = 40,
        MicroQRM1 = 41,
        MicroQRM2 = 42,
        MicroQRM3 = 43,
        MicroQRM4 = 44,
    }
}
```

## <a name="see-also"></a>Siehe auch
* [Koordinatensysteme](coordinate-systems.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>