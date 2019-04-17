---
title: Qr-Code, Nachverfolgen
description: Erfahren Sie mehr Informationen zum Aktivieren von QR-Code für Ihr Windows Mixed Reality immersive (VR) Kopfhörer, und implementieren Sie das Feature in Ihren VR-apps.
author: yoyozilla
ms.author: yoyoz
ms.date: 11/06/2018
ms.topic: article
keywords: vr, lbe, location based entertainment, vr arcade, arcade, immersive, qr, qr code
ms.openlocfilehash: b0f4480496c15f811979f76143acbd456d89e249
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605115"
---
# <a name="qr-code-tracking"></a>Qr-Code, Nachverfolgen

Qr-Code, die nachverfolgung wird in der Windows Mixed Reality-Treiber für immersive Headsets von (VR) implementiert. Durch das Aktivieren der QR-Code-nachverfolgung im Treiber Kopfhörer, den Kopfhörer sucht QR-Codes, und sie möchten apps gemeldet werden. Dieses Feature ist nur verfügbar, ab der [Windows 10 Oktober 2018 Update (auch bekannt als RS5)](release-notes-october-2018.md).

>[!NOTE]
>Die Codeausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstatt C ++ 17-kompatible C++"/ WinRT", wie in der [ C++ holographic Projektvorlage](creating-a-holographic-directx-project.md).  Die Konzepte sind Entsprechung für einen C++"/ WinRT"-Projekt, aber Sie benötigen, um den Code zu übersetzen.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Feature</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td> Qr-Code, Nachverfolgen</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="enabling-and-disabling-qr-code-tracking-for-your-headset"></a>Aktivieren und Deaktivieren von QR-code Überwachung für Ihre Kopfhörer
Hinweis: Dieser Abschnitt gilt nur für [Windows 10 Oktober 2018 Update (auch bekannt als RS5)](release-notes-october-2018.md). In 19-h-1-Builds oder höher müssen Sie nicht dazu.
Ob Sie entwickeln eine mixed Reality-app, die nachverfolgung von QR-Code nutzen, wird, oder Sie ein Kunde eine dieser apps sind, müssen Sie manuell aktivieren, QR-Code in Ihre Kopfhörer des Treibers nachverfolgen.

Um **QR-Code, Nachverfolgen von einschalten** für Ihre immersive (VR) Kopfhörer:

1. Schließen Sie die Mixed Reality-app auf Ihrem PC.
2. Trennen Sie die Kopfhörer von Ihrem PC.
3. Führen Sie das folgende Skript an der Eingabeaufforderung ein:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 1 /F`
4. Verbinden Sie Ihre Kopfhörer auf Ihren PC erneut.

Um **QR-Code, Nachverfolgen von deaktivieren** für Ihre immersive (VR) Kopfhörer:

1. Schließen Sie die Mixed Reality-app auf Ihrem PC.
2. Trennen Sie die Kopfhörer von Ihrem PC.
3. Führen Sie das folgende Skript an der Eingabeaufforderung ein:<br>
    `reg add "HKLM\SOFTWARE\Microsoft\HoloLensSensors" /v  EnableQRTrackerDefault /t REG_DWORD /d 0 /F`
4. Verbinden Sie Ihre Kopfhörer auf Ihren PC erneut. Dadurch wird jede ermittelte QR-Codes "nicht-gefunden werden."

## <a name="printing-codes"></a>Drucken-codes

Zuallererst die [für QR-Codes Spec](https://www.qrcode.com/en/howto/code.html) sagt, "Bereich Symbol QR-Code erfordert einen Rand oder der"stillen Zone"dazu verwendet werden. Der Rand ist eine klare Bereich auf ein Symbol, in dem nichts gedruckt wird. Qr-Code erfordert eine vier-Module bonustoken auf allen Seiten eines Symbols". Dies muss eine Breite auf jeder Seite der vier Mal die Größe eines Moduls - eine einzelne Schwarzes Quadrat im Code haben. Spec diese Seite enthält Hinweise zum Drucken des QR-Codes, und ermitteln, die den Bereich erforderlich, um eine bestimmte Größe QR-Code zu machen.

Derzeit ist die Erkennung von Qualität von QR-Code anfällig für unterschiedliche Beleuchtung und Hintergrund. Damit dies Beachten Sie Ihrer Beleuchtung aus, und drucken Sie den entsprechenden Code. Drucken Sie in einer Szene mit besonders hellen Beleuchtung einen Code, der auf einen grauen Hintergrund Schwarz ist. Unter einer Licht-Szene, Schwarz in Weiß funktioniert. Ebenso ist der Hintergrund auf den Code besonders dunkel, versuchen Sie es Schwarz auf Grau Code Wenn Ihre Erkennungsrate niedrig ist. Andernfalls ist der Hintergrund heller, sollte ein reguläre Code problemlos funktionieren.

## <a name="qrtracking-api"></a>QRTracking API

Die QRTracking-Plug-Ins macht die APIs für QR-Code, nachverfolgen. Um das Plug-in verwenden zu können, müssen Sie die folgenden Typen von verwenden die *QRCodesTrackerPlugin* Namespace.

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

## <a name="implementing-qr-code-tracking-in-unity"></a>Implementieren von QR-Code in Unity nachverfolgen

### <a name="sample-unity-scenes-in-mrtk-mixed-reality-toolkit"></a>Beispiel für Unity-Szenen in MRTK (Mixed Reality-Toolkit)

Sie finden ein Beispiel für die Verwendung der QR-Arbeitselementverfolgungs-API im Mixed Reality-Toolkit [GitHub-Website](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker).

MRTK verfügt über die erforderlichen Skripts Simpilify das Nachverfolgen der Nutzung QR implementiert. Alle erforderlichen Ressourcen zum Entwickeln von apps nachverfolgen QR befinden sich im Ordner "QRTracker". Es gibt zwei Szenen: die erste ist ein Beispiel einfach Details zu den QR-Codes angezeigt, wie sie erkannt werden, und die zweite zeigt, wie das Koordinatensystem, die angefügt werden, um den QR-Code zu verwenden, um Hologramme anzuzeigen.
Es gibt eine prefab "QRScanner" die im Hintergrund QRCodes verwenden alle die erforderlichen Scrips hinzugefügt. Das Skript QRCodeManager ist eine Singileton-Klasse, die implementiert die QRCode-API, die Sie ihn in die Szene Sie hinzufügen können. Die Skripts "AttachToQRCode" wird verwendet, können Sie den QR-Code Coodridnate Systemen Hologramme zuordnen, kann dieses Skript auf Ihrem Hologramme hinzugefügt werden. Die "SpatialGraphCoordinateSystem" veranschaulicht, wie das QRCode-Koordinatensystem. Diese Skripts können verwendet werden, wie in Ihrem Projekt im Hintergrund ist, oder Sie können schreiben, Ihre eigene direkt mithilfe des Plug-Ins wie oben beschrieben.

### <a name="implementing-qr-code-tracking-in-unity-without-mrtk"></a>Implementieren von QR-Code in Unity ohne MRTK nachverfolgen

Sie können auch den QR-Arbeitselementverfolgungs-API in Unity verwenden, ohne eine Abhängigkeit auf MRTK. Um die API zu verwenden, müssen Sie Ihr Projekt mit der folgenden Anweisung vorzubereiten:

1. Erstellen Sie einen neuen Ordner, in dem Ordner "Assets" Ihres Unity-Projekts mit dem Namen: "Plug-Ins".
2. Kopieren Sie alle erforderlichen Dateien aus [in diesem Ordner](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins) in den lokalen "Plug-Ins"-Ordner, die Sie gerade erstellt haben.
3. Können Sie den QR-nachverfolgung-Skripts in der [MRTK Ordner "Scripts"](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Scripts) oder Ihr eigenes schreiben.
Hinweis: Diese Plug-Ins sind nur für [Windows 10 Oktober 2018 Update (auch bekannt als RS5)](release-notes-october-2018.md) erstellt. Die Plug-Ins wird mit der nächsten Version von Windows aktualisiert werden. Die aktuelle Plug-Ins wurden experimentelle und funktionieren nicht bei zukünftigen Versionen von Windows. Neue Plug-Ins werden veröffentlicht, die aus der nächsten Version von Windows verwendet werden kann, und sie werden nicht rückwärts kompatibel und können nicht mehr mit RS5).

## <a name="implementing-qr-code-tracking-in-directx"></a>Implementieren von QR-Code in DirectX nachverfolgen

Um die QRTrackingPlugin in Visual Studio verwenden zu können, müssen Sie die .winmd Verweis von der QRTrackingPlugin hinzugefügt. Sie finden die [erforderlichen Dateien für die unterstützten Plattformen hier](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Preview/QRTracker/Plugins/WSA).

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

## <a name="getting-a-coordinate-system"></a>Abrufen von einem Koordinatensystem

Wir definieren ein rechten Koordinatensystem, die mit dem QR-Code auf der oberen linken Ecke des Quadrats Schnelle Erkennung in der oberen linken Ecke ausgerichtet. Das Koordinatensystem ist unten dargestellt. Die z-Achse in das Dokument (nicht gezeigt) zeigt, in Unity die z-Achse ist jedoch kein Papier und Linkshänder.

Eine SpatialCoordinateSystem wird definiert, die wie gezeigt ausgerichtet ist. Dieses Koordinatensystem abgerufen werden kann, von der Plattform, die mit der API *Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode*.

![Qr-Code-Koordinatensystem](images/Qr-coordinatesystem.png) 

Von QRCode ^-Objekt Code, der folgende Code zeigt, wie Sie ein Rechteck erstellt, und fügen Sie ihn in den QR-Koordinatensystem:

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

Sie können die physische Größe verwenden, um den QR-Rechteck zu erstellen:

```cpp
std::vector<float3> qrVertices = CreateRectangle(Code->PhysicalSizeMeters, Code->PhysicalSizeMeters); 
```

Zeichnen den QR-Code oder das Anfügen von Hologramme auf den Speicherort, kann das Koordinatensystem verwendet werden:

```cpp
Windows::Perception::Spatial::SpatialCoordinateSystem^ qrCoordinateSystem = Windows::Perception::Spatial::Preview::SpatialGraphInteropPreview::CreateCoordinateSystemForNode(Code->Id);
```

Vollständig zu entfernen und Ihre *QRCodesTrackerPlugin::QRCodeAddedHandler* kann etwa wie folgt aussehen:

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

## <a name="troubleshooting-and-faq"></a>Problembehandlung und häufig gestellte Fragen

**Allgemeine Problembehandlung**

* Wird Ihr PC mit Windows 10 Oktober 2018 aktualisieren?
* Haben Sie den Registrierungsschlüssel festgelegt? Neustart das Gerät anschließend?
* Ist die Version des QR-Code eine unterstützte Version? Aktuelle API unterstützt bis zu 20 für QR-Code-Version. Es wird empfohlen, Version 5 für die allgemeine Nutzung verwenden. 
* Sind Sie genug, um den QR-Code schließen? Je näher die Kamera ist den QR-Code, je höher der QR-Code-Version der API unterstützen kann.  

**Muss ich wie nah an den QR-Code erkannt werden?**

Dies hängt von der Größe des QR-Codes, und darüber Version ist. Für eine Version 1 QR-Code von 5 cm Seiten auf 25 cm Seiten variieren reicht die minimale Erkennung Entfernung von 0,15 Zähler zu 0,5 m ein. Die am weitesten entfernten entfernt, die diese aus erkannt werden können reicht von ca. 0.3 Meter für die kleineren QR-Code-Ziele 1,4-Zähler für die größeren. Für QR-Codes größer als, können Sie schätzen, die Erkennung von Entfernung für Größe steigt linear. Unsere Tracker funktioniert nicht mit QR-Codes mit Seiten kleiner als 5 cm.

**Tun Sie qr-Codes mit Logos?**

Qr-Codes mit Logos wurden nicht getestet und werden derzeit nicht unterstützt.

**Wie lösche ich QR-Codes aus meiner app, damit sie bleiben nicht?**

* Qr-Codes werden nur in der startsitzung beibehalten. Sobald Sie neu starten (oder neu des Treibers starten), werden sie durchgeführt und als neue Objekte nächsten erkannt werden.
* Verlauf der QR-Codes wird in der treibersitzung auf der Systemebene gespeichert, aber Sie können konfigurieren, dass Ihre app, um QR-Codes, die älter sind als die eines bestimmten Zeitstempels zu ignorieren, wenn Sie möchten. Derzeit unterstützt die API Verlauf löschen QR-Codes, wie die Daten mehrere apps interessiert sein könnten.

**Die Plug-Ins für RS5 und zukünftigen Versionen nicht kompatibel sind** RS5-Version des Plug-Ins funktioniert nur für RS5 und funktioniert nicht für zukünftige Versionen. Die Expermental-Plug-in mit der real-Plug-in ersetzt werden und sollte sein, dass wir in zukünftigen Versionen von Windows können.
