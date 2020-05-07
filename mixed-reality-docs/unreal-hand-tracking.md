---
title: Hand Nachverfolgung in Unreal
description: Erläutert die Verwendung der Hand Verfolgung in Unreal
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, hololens, Hand Nachverfolgung
ms.openlocfilehash: 3f7f4dd1eb62cb707eaaf8632a2ba3c280a4ac31
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835443"
---
# <a name="hand-tracking"></a>Hand Nachverfolgung

Das Hand Verfolgungssystem verwendet die Palmen und Finger einer Person als Eingabe für Unreal. Ein Entwickler kann die Position und Drehung jedes Fingers, den gesamten Palmen und sogar Handgesten für die Verwendung in seinem eigenen Code erhalten. 

## <a name="hand-pose"></a>Hand darstellen

Mithilfe der Hand Pose können Entwickler die Hände und Finger des aktiven Benutzers als Eingabe nachverfolgen. Dieses System wird sowohl über Blueprints als auch über C++ verfügbar gemacht. Technische Details finden Sie in der entsprechenden WinRT-Klasse [Windows. perception. People. handpose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) diese Unreal-API stellt die Daten im Format von Unreal es Koordinatensystem bereit, und Ticks werden mit der Unreal-Engine synchronisiert.

### <a name="enum"></a>Enum

Ewmrhandkeypoint beschreibt die Knochen Hierarchie der Hand. 

Karte

![Hand-keypoint-BP](images/unreal/hand-keypoint-bp.png)
 
C++:
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

![Hand Gerüst](images/hand-skeleton.png)

Die numerischen Werte finden Sie in der Tabelle [Windows. perception. People. handjointkind.](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)
 
### <a name="functions"></a>Functions

Um Hand Verfolgungs Funktionen in Blaupausen zu verwenden, öffnen Sie "Hand Tracking/Windows Mixed Reality".

![Hand Tracking-BP](images/unreal/hand-tracking-bp.png)

Für C++-Funktionen schließen Sie "windowsmixedrealityhandtrackingfunctionlibrary. h" ein.

Übergeben

![Unterstützt die Hand Überwachung von BP](images/unreal/supports-hand-tracking-bp.png)
 
C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

Gibt true zurück, wenn die Hand Verfolgung auf dem Gerät unterstützt wird, false, wenn die Hand Verfolgung nicht verfügbar ist.

Übergeben

![Hand Gelenk Transformation](images/unreal/get-hand-joint-transform.png)
 
C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

Diese Funktion gibt räumliche Daten von Hand zurück. Die Daten werden in jedem Frame aktualisiert, und die zurückgegebenen Werte werden zwischengespeichert. Es wird nicht empfohlen, aus Leistungsgründen eine hohe Logik für diese Funktion zu haben. 

* **Hand** – Hand des Benutzers, kann Links oder rechts sein.
* **Keypoint** – der Knochen der Hand. 
* **Transformation** – Koordinaten und Ausrichtung der Basis von Bone. Um die Transformations Daten für das Ende eines Knochens zu erhalten, sollte die Basis des nächsten Bone angefordert werden. Ein spezieller Tip-Bone gibt das Ende der distal-Tabelle an. 
* **RADIUS** – Radius der Basis des Knochens.
* **Rückgabewert** – true, wenn der Rahmen dieses Frames nachverfolgt wird, false, wenn der Knochen nicht nachverfolgt wird.

## <a name="hand-live-link-animation"></a>Live Link Animation Hand
Hand stellen werden der Animation mithilfe des Live Link-Plug-ins ausgesetzt. Die Plug-in-Dokumentation ist [hier](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)

Wenn die Windows Mixed Reality-und Live Link-Plug-ins aktiviert sind, wechseln Sie zu **Window > Live Link** , um das Fenster Live Link-Editor zu öffnen. Klicken Sie auf die **Schaltfläche + Quelle** , und aktivieren Sie Windows Mixed Reality-Hand Verfolgungs Quelle

![Live Link Quelle](images/unreal/live-link-source.png)
 
Nachdem Sie die Quelle aktiviert und ein beliebiges Animations Objekt geöffnet haben, hat die Registerkarte Vorschau Szene der Animation die folgenden zusätzlichen Optionen (Details finden Sie in der Live Link Dokumentation von Unreal), da sich das Plug-in in der Beta Version befindet, kann sich der Prozess später ändern.

![Live Link Animation](images/unreal/live-link-animation.png)
 
Die Hand Animations Hierarchie ist die gleiche wie in ewmrhandkeypoint. Die Animation kann mithilfe von windowsmixedrealityhandtrackinglebinkremapasset neu zugewiesen werden. 

![Live Link Animation 2](images/unreal/live-link-animation2.png)
 
Der Wert kann im Editor untergeordnet werden.

![Live Link Neuzuordnung](images/unreal/live-link-remap.png)
 
## <a name="hand-mesh"></a>Hand Netz
Mesh, das die Benutzer Hände darstellt. 

![Hand Netz](images/unreal/hand-mesh.png)
 
### <a name="how-to-enable-and-configure"></a>Vorgehensweise beim Aktivieren und konfigurieren

Entwickler können den direkten Zugriff auf Hand Netze für Ihre eigenen Zwecke erhalten. Dieser Zugriff muss in arsessionconfig: AR Settings (> World Mapping-> Mesh-Daten aus der nach verfolgten Geometrie generiert werden. 

Im folgenden sind die Standardparameter für Meshes aufgeführt:

1.  Netzdaten für Okklusion verwenden
2.  Konflikt für Mesh-Daten generieren
3.  Navigations Gitter für Mesh-Daten generieren
4.  Gitternetz Daten in Wireframe Renderingparameter – Debug

Für Projekte mit gemischter Realität werden diese Parameterwerte als die Standardwerte für die räumliche Zuordnung und die Hand gitterwerte verwendet. Entwickler können Sie in BP oder Code für ein bestimmtes Mesh ändern.

### <a name="c-api-reference"></a>C++-API-Referenz 
```cpp
enum class EARObjectClassification : uint8
{
// other types 
    HandMesh,
};
```

Dieser Wert ist das Hand Mesh unter allen nachverfolgbare-Objekten.

```cpp
class FARSupportInterface 
{
public:
// other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

Diese Delegaten werden aufgerufen, wenn das System ein nachverfolgbare-Objekt erkennt, einschließlich eines Hand Netzes. 
```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```
Handler für die Delegaten sollten die folgende Signatur aufweisen:
```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

Auf Mesh-Daten kann über zugegriffen werden.`UARTrackedGeometry::GetUnderlyingMesh`

### <a name="blueprint-api-reference"></a>Referenz zur Blueprint-API

Entwickler sollten einer Blueprint-Actor-Komponente eine "AR trackable notify"-Komponente hinzufügen

![Meldung zu einem darstellbaren Element](images/unreal/ar-trackable-notify.png)
 
Wechseln Sie dann zu den Details der Komponente. 

![Artrackable Benachrichtigen 2](images/unreal/ar-trackable-notify2.png)
 
Und überschreiben Sie die überwachte Geometrie zum Hinzufügen/Aktualisieren/entfernen mit Code wie dem folgenden:

![Bei der über sichtbaren Benachrichtigung](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a>Hand Strahlen

Entwickler können einen Hand Strahl als Zeigegerät verwenden. Das System ist in C++ und Blueprint verfügbar. Technisch gesehen macht es [Windows. UI. Input. Spatial. spatialpointerinteraktionsourcepose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) verfügbar.

Es ist wichtig zu erwähnen, dass die Ergebnisse aller Funktionen jeden Frame ändern, dass Sie alle aufgerufen werden. Weitere Informationen zu reinen vs-Funktionen oder Aufruf baren [Funktionen finden Sie](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure) unter

Für Blueprint öffnen Sie "Windows Mixed Reality HMD"

![Hand Strahlen-BP](images/unreal/hand-rays-bp.png)
 
Für C++ include "windowsmixedrealityfunctionlibrary. h".

### <a name="enum"></a>Enum

![Eingabe Controller-Schaltflächen](images/unreal/input-controller-buttons.png)
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```
* **Select** -– User hat das Select-Ereignis ausgelöst, das in hololens 2 von airtap oder Gaze und Commit ausgelöst werden kann. Eine andere Möglichkeit, dieses Ereignis zu initiieren, besteht darin, "Select" zu sagen. 
* **Grasp** – vom Benutzer ausgelöstes Ereignis zum Erfassen von Ereignissen, das in hololens 2 ausgelöst wird, indem die Finger des Benutzers in einem Hologram geschlossen werden. 
```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```
* **Notverfolgt** – die Hand ist nicht sichtbar.
* Nach **verfolgte** –: die Hand ist vollständig nachverfolgt.

### <a name="struct"></a>Struktur

![Zeiger stellen Informationen BP dar](images/unreal/pointer-pose-info-bp.png)
```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```
* **Ursprung** – Ursprung der Hand
* **Richtung** – Richtung der Hand
* **Up** – Up Vector of the Hand
* **Ausrichtung** – Ausrichtung Quaternion 
* **Überwachungs Status** – aktueller Überwachungs Status

### <a name="functions"></a>Functions

Alle Funktionen sollten für die kontinuierliche Überwachung in jedem Frame aufgerufen werden können. 

![Informationen zum Darstellen von Zeigern](images/unreal/get-pointer-pose-info.png)
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```
Die-Funktion gibt die vollständigen Informationen über die Richtung des Hand Strahl in diesem Frame zurück. 

![Erfasste BP](images/unreal/is-grasped-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
Gibt "true" zurück, wenn die Hand in diesem Frame erfasst wird. 

![Ist SELECT-Taste für BP](images/unreal/is-select-pressed-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```
Gibt true zurück, wenn der Benutzer SELECT in diesem Frame ausgelöst hat.

![Ist Schaltfläche, auf die ein](images/unreal/is-button-clicked-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```
Gibt true zurück, wenn das Ereignis bzw. die Schaltfläche in diesem Frame ausgelöst wird.

![Controller-Überwachungs Status-BP erhalten](images/unreal/get-controller-tracking-status-bp.png)
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
Gibt den verfolgungsstatus in diesem Frame zurück.

## <a name="gestures"></a>Gesten

Die hololens 2 können räumliche Gesten nachverfolgen. Details zu diesen Gesten finden Entwickler darin, dass Sie von Entwicklern als Eingabe für ihre gemischte Reality-Anwendung [erfasst werden können](https://docs.microsoft.com/hololens/hololens2-basic-usage) . 

Die C++-Funktion befindet sich in "windowsmixedrealityspatialinputfunctionlibrary. h".

Die Blueprint-Funktion befindet sich in der räumlichen Eingabe von Windows Mixed Reality.

![Erfassungs Gesten](images/unreal/capture-gestures.png)

### <a name="enum"></a>Enum

![Gesten-Typ](images/unreal/gesture-type.png)
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```
Diese Aufzählung beschreibt die Gesten räumlicher Achsen. Weitere Informationen finden Sie [hier](holograms-211.md) .

### <a name="function"></a>Funktion

![Erfassungs Gesten BP](images/unreal/capture-gestures-bp.png)
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```
Die-Funktion aktiviert und deaktiviert die Erfassung von Gesten. Die aktivierten Gesten lösen Eingabeereignisse aus. Sie gibt true zurück, wenn das Aktivieren der Gesten Erfassung erfolgreich war, und false, wenn ein Fehler vorliegt.
Schlüsselereignisse

![Schlüsselereignisse](images/unreal/key-events.png)

![Schlüsselereignisse 2](images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```
Wenn die Geste aktiviert ist, beginnt das Auslösen der Ereignisse. 

