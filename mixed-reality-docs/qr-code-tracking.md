---
title: QR-Code Nachverfolgung
description: Erfahren Sie, wie Sie die QR-Code Überwachung für Ihr Windows Mixed Reality-immersive-Headset (VR) aktivieren und das Feature in ihren VR-apps implementieren.
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: VR, LBE, Location based Entertainment, VR-Arkade, Arcade, immersive, QR, QR-Code
ms.openlocfilehash: 465056cf645a8b9dc9e0e2d3f9dacf887df67c52
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829986"
---
# <a name="qr-code-tracking"></a>QR-Code Nachverfolgung

Die QR-Code Überwachung wird in den Windows Mixed Reality Driver for Immersive (VR)-Headsets implementiert. Durch Aktivieren der QR-Code Protokollierung im Headset-Treiber scannt das Headset nach QR-Codes und wird an interessierte apps gemeldet. Diese Funktion ist nur ab dem [Windows 10-Update vom Oktober 2018 (auch bekannt als RS5)](release-notes-october-2018.md)verfügbar.

>[!NOTE]
>Die Code Ausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung C++von/CX anstelle von C + +17- C++kompatibler/WinRT, wie Sie in der [ C++ Holographic-Projektvorlage](creating-a-holographic-directx-project.md)verwendet werden.  Die Konzepte sind äquivalent für ein C++/WinRT-Projekt, obwohl Sie den Code übersetzen müssen.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Funktion</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>QR-Code Nachverfolgung</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a>Aktivieren und Deaktivieren der QR-Code-Nachverfolgung für Ihr Headset
Hinweis: Dieser Abschnitt gilt nur für [Windows 10-Update vom Oktober 2018 (auch bekannt als RS5)](release-notes-october-2018.md). Ab 19h1 müssen Sie dies nicht mehr tun.
Unabhängig davon, ob Sie eine Mixed Reality-App entwickeln, die die QR-Code-Nachverfolgung nutzt, oder Sie sind ein Kunde einer dieser apps, müssen Sie die QR-Code-Nachverfolgung manuell in den Treiber Ihres Headsets einschalten.

Um die **QR-Code** -Nachverfolgung für Ihr immersives (VR)-Headset zu aktivieren:

1. Schließen Sie die Mixed Reality-Portal-App auf Ihrem PC.
2. Entfernen Sie das Headset von Ihrem PC.
3. Führen Sie das folgende Skript an der Eingabeaufforderung aus:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. Verbinden Sie Ihr Headset erneut mit Ihrem PC.

Um die **QR-Code** -Nachverfolgung für Ihr immersives (VR)-Headset zu deaktivieren:

1. Schließen Sie die Mixed Reality-Portal-App auf Ihrem PC.
2. Entfernen Sie das Headset von Ihrem PC.
3. Führen Sie das folgende Skript an der Eingabeaufforderung aus:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. Verbinden Sie Ihr Headset erneut mit Ihrem PC. Dadurch werden alle ermittelten QR-Codes "nicht erstellbar".

## <a name="printing-codes"></a>Druck Codes

Vor allem bedeutet die [Spezifikation für QR-Codes, dass](https://www.qrcode.com/en/howto/code.html) der QR-Code Symbol Bereich einen Rand oder eine "Stille Zone" für die Verwendung benötigt. Der Rand ist ein klarer Bereich um ein Symbol, in dem nichts gedruckt wird. Der QR-Code erfordert einen vier-Module-breiten Rand an allen Seiten eines Symbols. " Dies muss auf jeder Seite eine Breite von vier Mal der Größe eines Moduls aufweisen, einem einzelnen schwarzen Quadrat im Code. Die Seite "Spezifikationen" enthält Ratschläge zum Drucken von QR-Codes und zum Ermitteln des Bereichs, der zum Erstellen eines QR-Codes mit einer bestimmten Größe erforderlich ist.

Derzeit ist die Qualität der QR-Code Erkennung anfällig für die unterschiedliche Beleuchtung und den Hintergrund. Um dies zu bekämpfen, notieren Sie sich Ihre Beleuchtung, und Drucken Sie den entsprechenden Code. Drucken Sie in einer Szene mit besonders heller Beleuchtung einen Code, der in einem grauen Hintergrund schwarz ist. In einer Low-Light-Szene ist schwarz bei White Works. Wenn der Hintergrund des Codes besonders dunkel ist, sollten Sie auch eine schwarz mit grauem Code ausprobieren, wenn die Erkennungsrate niedrig ist. Andernfalls sollte ein regulärer Code einwandfrei funktionieren, wenn der Hintergrund heller ist.

## <a name="qrtracking-api"></a>Qrtracking-API

Das qrtracking-Plug-in macht die APIs für die QR-Code Überwachung verfügbar. Um das Plug-in zu verwenden, müssen Sie die folgenden Typen aus dem *qrcodestrackerplugin* -Namespace verwenden.

```cs
 // QRTracker plugin namespace
 namespace QRCodesTrackerPlugin
 {
    // Encapsulates information about a labeled QR code element.
    public class QRCode
    {        
        // Unique id that identifies this QR code for this session.
        public Guid Id { get; private set; }
           
        // Version of this QR code.
        public Int32 Version { get; private set; }
        
        // PhysicalSizeMeters of this QR code.
        public float PhysicalSizeMeters { get; private set; }
        
        // QR code Data.
        public string Code { get; private set; }
        
        // QR code DataStream this is the error corrected data stream
        public Byte[] CodeStream { get; private set; }
        
        // QR code last detected QPC ticks.
        public Int64 LastDetectedQPCTicks { get; private set; }
    };
    
    // The type of a QR Code added event.
    public class QRCodeAddedEventArgs
    {   
        // Gets the QR Code that was added
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code removed event.
    public class QRCodeRemovedEventArgs
    {
        // Gets the QR Code that was removed.
        public QRCode Code { get; private set; }
    };
    
    // The type of a QR Code updated event.
    public class QRCodeUpdatedEventArgs
    {
        // Gets the QR Code that was updated.
        public QRCode Code { get; private set; }
    };
    
    // A callback for handling the QR Code added event.
    public delegate void QRCodeAddedHandler(QRCodeAddedEventArgs args);
    
    // A callback for handling the QR Code removed event.
    public delegate void QRCodeRemovedHandler(QRCodeRemovedEventArgs args);
    
    // A callback for handling the QR Code updated event.
    public delegate void QRCodeUpdatedHandler(QRCodeUpdatedEventArgs args);
    
    // Enumerates the possible results of a start of QRTracker.
    public enum QRTrackerStartResult
    {
        // The start has succeeded.
        Success = 0,
        
        //  The currently no device is connected.
        DeviceNotConnected = 1,
        
        // The QRTracking Feature is not supported by the current HMD driver
        // systems
        FeatureNotSupported = 2,
        
        // The access is denide. Administrator needs to enable QR tracker feature.
        AccessDenied = 3,
    };
    
    // QRTracker
    public class QRTracker
    {
        // Constructs a new QRTracker.
        public QRTracker(){}
        
        // Gets the QRTracker.
        public static QRTracker Get()
        {
            return new QRTracker();
        }
        
        // Start the QRTracker. Returns QRTrackerStartResult.
        public QRTrackerStartResult Start()
        {
            throw new NotImplementedException();
        }
        
        // Stops tracking QR codes.
        public void Stop() {}

        // Not Implemented
        Windows.Foundation.Collections.IVector<QRCode> GetList() { throw new NotImplementedException(); }
        
        // Event representing the addition of a QR Code.
        public event QRCodeAddedHandler Added = delegate { };
        
        // Event representing the removal of a QR Code.
        public event QRCodeRemovedHandler Removed = delegate { };
        
        // Event representing the update of a QR Code.
        public event QRCodeUpdatedHandler Updated = delegate { };
    };
}
```

## <a name="implementing-qr-code-tracking-in-unity"></a>Implementieren der QR-Code-Nachverfolgung in Unity

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a>Beispiel für Unity-Szenen in mrtk (Mixed Reality Toolkit)

Ein Beispiel für die Verwendung der QR-Überwachungs-API finden Sie auf der [GitHub-Website](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker)des Mixed Reality-Toolkits.

Mrtk hat die benötigten Skripts implementiert, um die Verwendung der QR-Nachverfolgung zu vereinfachen. Alle erforderlichen Assets zum Entwickeln von QR-nach Verfolgungs-apps befinden sich im Ordner "qrtracker". Es gibt zwei Szenen: das erste ist ein Beispiel für die einfache Anzeige der Details der QR-Codes, wenn Sie erkannt werden. das zweite Beispiel zeigt, wie das Koordinatensystem, das mit dem QR-Code verknüpft ist, zum Anzeigen von holograms verwendet werden kann.
Es gibt eine Prefab "qrscanner", bei der alle notwendigen Skripts zu den Kulissen hinzugefügt wurden, um qrcodes zu verwenden. Das Skript "qrcodemanager" ist eine Singleton-Klasse, die die QRCode-API implementiert. Diese muss Ihrer Szene hinzugefügt werden. Das Skript "attachdeqrcode" wird verwendet, um Hologramme an die QR-Code Koordinatensysteme anzufügen. dieses Skript kann jedem ihrer holograms hinzugefügt werden. Das "spatialgraphcoordinatesystem" zeigt, wie das QRCode-Koordinatensystem verwendet wird. Diese Skripts können unverändert in Ihren Projekt Kulissen verwendet werden, oder Sie können Ihre eigenen Skripts direkt mithilfe des Plug-ins schreiben, wie oben beschrieben.

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a>Implementieren der QR-Code-Nachverfolgung in Unity ohne mrtk

Sie können auch die QR-nach Verfolgungs-API in Unity verwenden, ohne eine Abhängigkeit von mrtk zu treffen. Um die API zu verwenden, müssen Sie das Projekt mit der folgenden Anweisung vorbereiten:

1. Erstellen Sie im Ordner "Assets" Ihres Unity-Projekts einen neuen Ordner mit dem folgenden Namen: "Plug-ins".
2. Kopieren Sie alle erforderlichen Dateien aus [diesem Ordner](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) in den lokalen Ordner "Plug-ins", den Sie soeben erstellt haben.
3. Sie können die QR-nach Verfolgungs Skripts im [Ordner "mrtk Scripts](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) " verwenden oder eigene schreiben.
Hinweis: Diese Plug-ins sind nur für [Windows 10-Updates vom Oktober 2018 (auch bekannt als RS5)](release-notes-october-2018.md) . Die Plug-ins werden mit der nächsten Windows-Version aktualisiert. Die aktuellen Plug-ins waren experimentell und funktionieren nicht für zukünftige Versionen von Windows. Neue Plug-ins werden veröffentlicht, die in der nächsten Windows-Version verwendet werden können, und Sie sind nicht abwärts kompatibel und funktionieren nicht mit RS5).

## <a name="implementing-qr-code-tracking-in-directx"></a>Implementieren der QR-Code-Nachverfolgung in DirectX

Um das qrtrackingplugin in Visual Studio verwenden zu können, müssen Sie der Datei ". winmd" einen Verweis auf das qrtrackingplugin hinzufügen. Die [erforderlichen Dateien für die unterstützten Plattformen](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA)finden Sie hier.

```cpp
// MyClass.h
public ref class MyClass
{
    private:
      QRCodesTrackerPlugin::QRTracker^ m_qrtracker;
      // Handlers
      void OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args);
      void OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args);
      void OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args);
    ..
};
```

```cpp
// MyClass.cpp
MyClass::MyClass()
{
    // Create the tracker and register the callbacks
    m_qrtracker = ref new QRCodesTrackerPlugin::QRTracker();
    m_qrtracker->Added += ref new QRCodesTrackerPlugin::QRCodeAddedHandler(this, &OnAddedQRCode);
    m_qrtracker->Updated += ref new QRCodesTrackerPlugin::QRCodeUpdatedHandler(this, &OnUpdatedQRCode);
    m_qrtracker->Removed += ref new QRCodesTrackerPlugin::QRCodeRemovedHandler(this, &QOnRemovedQRCode);

    // Start the tracker
    if (m_qrtracker->Start() != QRCodesTrackerPlugin::QRTrackerStartResult::Success)
    {
      // Handle the failure
      // It can fail for multiple reasons and can be handled properly 
    }
}

void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    // use args->Code add to own list  
}

void MyClass::OnUpdatedQRCode(QRCodesTrackerPlugin::QRCodeUpdatedEventArgs ^args)
{
    // use args->Code update the existing one with the new one in own list 
}

void MyClass::OnRemovedQRCode(QRCodesTrackerPlugin::QRCodeRemovedEventArgs ^args)
{
    // use args->Code remove from own list.
}
```

## <a name="getting-a-coordinate-system"></a>Erhalten eines Koordinatensystems

Wir definieren ein richtiges Koordinatensystem, das mit dem QR-Code in der oberen linken Ecke des Quadrats für schnelle Erkennung in der oberen linken Ecke ausgerichtet ist. Das Koordinatensystem ist unten dargestellt. Die z-Achse zeigt auf das Papier (nicht dargestellt), aber in Unity ist die z-Achse nicht aus dem Papier und von Links.

Ein spatialcoordinatesystem ist definiert, das wie gezeigt ausgerichtet ist. Dieses Koordinatensystem kann von der Plattform mithilfe der API-Fenster abgerufen werden *::P erception:: Spatial::P Review:: spatialgraphinteroppreview:: foratecoordinatesystemfornode*.

![QR-Code Koordinatensystem](images/Qr-coordinatesystem.png) 

Im Code-Objekt von QRCode ^ zeigt der folgende Code, wie ein Rechteck erstellt und in das QR-Koordinatensystem eingefügt wird:

```cpp
// Creates a 2D rectangle in the x-y plane, with the specified properties.
std::vector<float3> SpatialStageManager::CreateRectangle(float width, float height)
{
    std::vector<float3> vertices(4);

    vertices[0] = { 0,  0, 0 };
    vertices[1] = { width,  0, 0 };
    vertices[2] = { width,  height, 0 };
    vertices[3] = { 0,  height, 0 };

    return vertices;
}
```

Sie können die physische Größe zum Erstellen des QR-Rechtecks verwenden:

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

Das Koordinatensystem kann zum Zeichnen des QR-Codes oder zum Anfügen von holograms an den Speicherort verwendet werden:

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

Ihr *qrcodestrackerplugin:: qrcodeaddedhandler* könnte etwa wie folgt aussehen:

```cpp
void MyClass::OnAddedQRCode(QRCodesTrackerPlugin::QRCodeAddedEventArgs ^args)
{
    std::vector<float3> qrVertices = CreateRectangle(args->Code->PhysicalSizeMeters, args->Code->PhysicalSizeMeters);
    std::vector<unsigned short> qrCodeIndices = TriangulatePoints(qrVertices);
    XMFLOAT3 qrAreaColor = XMFLOAT3(DirectX::Colors::Aqua);

    Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem =  Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(args->Code->Id);
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

## <a name="troubleshooting-and-faq"></a>Problembehandlung und FAQ

**Allgemeine Problembehandlung**

* Führt der PC das Windows 10-Update vom Oktober 2018 aus?
* Haben Sie den Schlüssel "reg" festgelegt? Sie das Gerät später neu starten?
* Ist die QR-Code Version eine unterstützte Version? Die aktuelle API unterstützt bis zu QR-Code Version 20. Wir empfehlen die Verwendung von Version 5 für die allgemeine Verwendung. 
* Sind Sie für den QR-Code fast ausreichend? Je näher die Kamera an dem QR-Code liegt, desto höher ist die QR-Code Version, die von der API unterstützt werden kann.  

**Wie nah muss ich auf den QR-Code sein, um ihn zu erkennen?**

Dies hängt von der Größe des QR-Codes und von der Version ab. Bei einem QR-Code der Version 1, der zwischen 5 cm-Seiten und 25 cm-Seiten variiert, liegt der Abstand der minimalen Erkennung zwischen 0,15 und 0,5 Meter. Die am weitesten entfernten Werte können von ungefähr 0,3 Meter für die kleineren QR-codeziele auf 1,4 Meter für die größere festgestellt werden. Bei QR-Codes, die größer als dieser Wert sind, können Sie schätzen: der Erkennungsabstand für die Größe erhöht sich linear. Unsere Tracker funktioniert nicht mit QR-Codes, die kleiner als 5 cm sind.

**Funktionieren QR-Codes mit Logos?**

QR-Codes mit Logos wurden nicht getestet und werden zurzeit nicht unterstützt.

**Gewusst wie die QR-Codes aus meiner app löschen, damit Sie nicht persistent gespeichert werden?**

* QR-Codes werden nur in der Start Sitzung beibehalten. Sobald Sie den Treiber neu starten (oder neu starten), werden diese nach dem nächsten Mal als neue Objekte erkannt.
* Der QR-Code Verlauf wird auf der Systemebene in der Treiber Sitzung gespeichert, aber Sie können Ihre APP so konfigurieren, dass Sie QR-Codes ignoriert, die älter als ein bestimmter Zeitstempel sind, wenn Sie möchten. Derzeit unterstützt die API das Löschen von QR-Code Verläufen, da mehrere Apps möglicherweise an den Daten interessiert sind.

**Die Plug-Ins für RS5 und zukünftige Versionen können nicht komprimiert werden** . RS5 Version des Plug-ins funktioniert nur für RS5 und kann für zukünftige Versionen nicht verwendet werden. Das expermentelle Plug-in wird durch das echte Plug-in ersetzt und sollte in zukünftigen Versionen von Windows verwendet werden.
