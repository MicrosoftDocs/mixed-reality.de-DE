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
# <a name="hand-tracking"></a><span data-ttu-id="5b82e-104">Hand Nachverfolgung</span><span class="sxs-lookup"><span data-stu-id="5b82e-104">Hand Tracking</span></span>

<span data-ttu-id="5b82e-105">Das Hand Verfolgungssystem verwendet die Palmen und Finger einer Person als Eingabe für Unreal.</span><span class="sxs-lookup"><span data-stu-id="5b82e-105">The hand tracking system uses a person’s palms and fingers as input to Unreal.</span></span> <span data-ttu-id="5b82e-106">Ein Entwickler kann die Position und Drehung jedes Fingers, den gesamten Palmen und sogar Handgesten für die Verwendung in seinem eigenen Code erhalten.</span><span class="sxs-lookup"><span data-stu-id="5b82e-106">A developer can get every finger’s position and rotation, the entire palm, and even hand gestures to use in their own code.</span></span> 

## <a name="hand-pose"></a><span data-ttu-id="5b82e-107">Hand darstellen</span><span class="sxs-lookup"><span data-stu-id="5b82e-107">Hand Pose</span></span>

<span data-ttu-id="5b82e-108">Mithilfe der Hand Pose können Entwickler die Hände und Finger des aktiven Benutzers als Eingabe nachverfolgen.</span><span class="sxs-lookup"><span data-stu-id="5b82e-108">Using the hand pose, developers can track the hands and fingers of the active user as input.</span></span> <span data-ttu-id="5b82e-109">Dieses System wird sowohl über Blueprints als auch über C++ verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="5b82e-109">This system is exposed through both Blueprints and C++.</span></span> <span data-ttu-id="5b82e-110">Technische Details finden Sie in der entsprechenden WinRT-Klasse [Windows. perception. People. handpose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) diese Unreal-API stellt die Daten im Format von Unreal es Koordinatensystem bereit, und Ticks werden mit der Unreal-Engine synchronisiert.</span><span class="sxs-lookup"><span data-stu-id="5b82e-110">Technical details are in the corresponding WinRT class [Windows.Perception.People.HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) This Unreal API provides the data in the format of Unreal’s coordinate system and ticks are synchronised with the Unreal Engine.</span></span>

### <a name="enum"></a><span data-ttu-id="5b82e-111">Enum</span><span class="sxs-lookup"><span data-stu-id="5b82e-111">Enum</span></span>

<span data-ttu-id="5b82e-112">Ewmrhandkeypoint beschreibt die Knochen Hierarchie der Hand.</span><span class="sxs-lookup"><span data-stu-id="5b82e-112">EWMRHandKeypoint describes the Hand’s bone hierarchy.</span></span> 

<span data-ttu-id="5b82e-113">Karte</span><span class="sxs-lookup"><span data-stu-id="5b82e-113">Blueprint:</span></span>

![Hand-keypoint-BP](images/unreal/hand-keypoint-bp.png)
 
<span data-ttu-id="5b82e-115">C++:</span><span class="sxs-lookup"><span data-stu-id="5b82e-115">C++:</span></span>
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

<span data-ttu-id="5b82e-117">Die numerischen Werte finden Sie in der Tabelle [Windows. perception. People. handjointkind.](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)</span><span class="sxs-lookup"><span data-stu-id="5b82e-117">The numerical values can be found in the table [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)</span></span>
 
### <a name="functions"></a><span data-ttu-id="5b82e-118">Functions</span><span class="sxs-lookup"><span data-stu-id="5b82e-118">Functions</span></span>

<span data-ttu-id="5b82e-119">Um Hand Verfolgungs Funktionen in Blaupausen zu verwenden, öffnen Sie "Hand Tracking/Windows Mixed Reality".</span><span class="sxs-lookup"><span data-stu-id="5b82e-119">To use hand tracking functions in Blueprints, open "Hand Tracking/Windows Mixed Reality"</span></span>

![Hand Tracking-BP](images/unreal/hand-tracking-bp.png)

<span data-ttu-id="5b82e-121">Für C++-Funktionen schließen Sie "windowsmixedrealityhandtrackingfunctionlibrary. h" ein.</span><span class="sxs-lookup"><span data-stu-id="5b82e-121">For C++ functions, include "WindowsMixedRealityHandTrackingFunctionLibrary.h"</span></span>

<span data-ttu-id="5b82e-122">Übergeben</span><span class="sxs-lookup"><span data-stu-id="5b82e-122">BP:</span></span>

![Unterstützt die Hand Überwachung von BP](images/unreal/supports-hand-tracking-bp.png)
 
<span data-ttu-id="5b82e-124">C++:</span><span class="sxs-lookup"><span data-stu-id="5b82e-124">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

<span data-ttu-id="5b82e-125">Gibt true zurück, wenn die Hand Verfolgung auf dem Gerät unterstützt wird, false, wenn die Hand Verfolgung nicht verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="5b82e-125">Returns true if hand tracking is supported on the device, false if hand tracking is not available.</span></span>

<span data-ttu-id="5b82e-126">Übergeben</span><span class="sxs-lookup"><span data-stu-id="5b82e-126">BP:</span></span>

![Hand Gelenk Transformation](images/unreal/get-hand-joint-transform.png)
 
<span data-ttu-id="5b82e-128">C++:</span><span class="sxs-lookup"><span data-stu-id="5b82e-128">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="5b82e-129">Diese Funktion gibt räumliche Daten von Hand zurück.</span><span class="sxs-lookup"><span data-stu-id="5b82e-129">This function returns spatial data of the hand.</span></span> <span data-ttu-id="5b82e-130">Die Daten werden in jedem Frame aktualisiert, und die zurückgegebenen Werte werden zwischengespeichert.</span><span class="sxs-lookup"><span data-stu-id="5b82e-130">The data updates every frame, inside a frame the returned values are cached.</span></span> <span data-ttu-id="5b82e-131">Es wird nicht empfohlen, aus Leistungsgründen eine hohe Logik für diese Funktion zu haben.</span><span class="sxs-lookup"><span data-stu-id="5b82e-131">It is not recommended to have heavy logic on this function for performance reasons.</span></span> 

* <span data-ttu-id="5b82e-132">**Hand** – Hand des Benutzers, kann Links oder rechts sein.</span><span class="sxs-lookup"><span data-stu-id="5b82e-132">**Hand** – hand of the user, may be left or right</span></span>
* <span data-ttu-id="5b82e-133">**Keypoint** – der Knochen der Hand.</span><span class="sxs-lookup"><span data-stu-id="5b82e-133">**Keypoint** – the bone of the hand.</span></span> 
* <span data-ttu-id="5b82e-134">**Transformation** – Koordinaten und Ausrichtung der Basis von Bone.</span><span class="sxs-lookup"><span data-stu-id="5b82e-134">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="5b82e-135">Um die Transformations Daten für das Ende eines Knochens zu erhalten, sollte die Basis des nächsten Bone angefordert werden.</span><span class="sxs-lookup"><span data-stu-id="5b82e-135">To get the transform data for the end of a bone, the base of the next bone should be requested.</span></span> <span data-ttu-id="5b82e-136">Ein spezieller Tip-Bone gibt das Ende der distal-Tabelle an.</span><span class="sxs-lookup"><span data-stu-id="5b82e-136">A special Tip bone gives end of distal.</span></span> 
* <span data-ttu-id="5b82e-137">**RADIUS** – Radius der Basis des Knochens.</span><span class="sxs-lookup"><span data-stu-id="5b82e-137">**Radius** — radius of the base of the bone.</span></span>
* <span data-ttu-id="5b82e-138">**Rückgabewert** – true, wenn der Rahmen dieses Frames nachverfolgt wird, false, wenn der Knochen nicht nachverfolgt wird.</span><span class="sxs-lookup"><span data-stu-id="5b82e-138">**Return Value** — true if the bone is tracked this frame, false if the bone is not tracked.</span></span>

## <a name="hand-live-link-animation"></a><span data-ttu-id="5b82e-139">Live Link Animation Hand</span><span class="sxs-lookup"><span data-stu-id="5b82e-139">Hand Live Link Animation</span></span>
<span data-ttu-id="5b82e-140">Hand stellen werden der Animation mithilfe des Live Link-Plug-ins ausgesetzt.</span><span class="sxs-lookup"><span data-stu-id="5b82e-140">Hand poses are exposed to Animation using the Live Link plugin.</span></span> <span data-ttu-id="5b82e-141">Die Plug-in-Dokumentation ist [hier](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)</span><span class="sxs-lookup"><span data-stu-id="5b82e-141">The plugin documentation is [here](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)</span></span>

<span data-ttu-id="5b82e-142">Wenn die Windows Mixed Reality-und Live Link-Plug-ins aktiviert sind, wechseln Sie zu **Window > Live Link** , um das Fenster Live Link-Editor zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="5b82e-142">If the Windows Mixed Reality and Live Link plugins are enabled, go to **Window > Live Link** to open the Live Link editor window.</span></span> <span data-ttu-id="5b82e-143">Klicken Sie auf die **Schaltfläche + Quelle** , und aktivieren Sie Windows Mixed Reality-Hand Verfolgungs Quelle</span><span class="sxs-lookup"><span data-stu-id="5b82e-143">Click the **+ Source button** and enable Windows Mixed Reality Hand Tracking Source</span></span>

![Live Link Quelle](images/unreal/live-link-source.png)
 
<span data-ttu-id="5b82e-145">Nachdem Sie die Quelle aktiviert und ein beliebiges Animations Objekt geöffnet haben, hat die Registerkarte Vorschau Szene der Animation die folgenden zusätzlichen Optionen (Details finden Sie in der Live Link Dokumentation von Unreal), da sich das Plug-in in der Beta Version befindet, kann sich der Prozess später ändern.</span><span class="sxs-lookup"><span data-stu-id="5b82e-145">After you enable the source and open any animation asset, the Preview Scene tab of Animation will have the following additional options (the details are in Unreal’s Live Link documentation- as the plugin is in beta, the process may change later)</span></span>

![Live Link Animation](images/unreal/live-link-animation.png)
 
<span data-ttu-id="5b82e-147">Die Hand Animations Hierarchie ist die gleiche wie in ewmrhandkeypoint.</span><span class="sxs-lookup"><span data-stu-id="5b82e-147">The hand animation hierarchy is the same as in EWMRHandKeypoint.</span></span> <span data-ttu-id="5b82e-148">Die Animation kann mithilfe von windowsmixedrealityhandtrackinglebinkremapasset neu zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="5b82e-148">Animation can be retargeted using WindowsMixedRealityHandTrackingLiveLinkRemapAsset.</span></span> 

![Live Link Animation 2](images/unreal/live-link-animation2.png)
 
<span data-ttu-id="5b82e-150">Der Wert kann im Editor untergeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="5b82e-150">It can be subclassed in the editor</span></span>

![Live Link Neuzuordnung](images/unreal/live-link-remap.png)
 
## <a name="hand-mesh"></a><span data-ttu-id="5b82e-152">Hand Netz</span><span class="sxs-lookup"><span data-stu-id="5b82e-152">Hand Mesh</span></span>
<span data-ttu-id="5b82e-153">Mesh, das die Benutzer Hände darstellt.</span><span class="sxs-lookup"><span data-stu-id="5b82e-153">Mesh representing the user hands.</span></span> 

![Hand Netz](images/unreal/hand-mesh.png)
 
### <a name="how-to-enable-and-configure"></a><span data-ttu-id="5b82e-155">Vorgehensweise beim Aktivieren und konfigurieren</span><span class="sxs-lookup"><span data-stu-id="5b82e-155">How to enable and configure</span></span>

<span data-ttu-id="5b82e-156">Entwickler können den direkten Zugriff auf Hand Netze für Ihre eigenen Zwecke erhalten.</span><span class="sxs-lookup"><span data-stu-id="5b82e-156">Developers can get direct access to hand meshes for their own purposes.</span></span> <span data-ttu-id="5b82e-157">Dieser Zugriff muss in arsessionconfig: AR Settings (> World Mapping-> Mesh-Daten aus der nach verfolgten Geometrie generiert werden.</span><span class="sxs-lookup"><span data-stu-id="5b82e-157">This access must be enabled in ARSessionConfig: AR Settings -> World Mapping -> Generate Mesh Data from Tracked Geometry.</span></span> 

<span data-ttu-id="5b82e-158">Im folgenden sind die Standardparameter für Meshes aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="5b82e-158">Here are the default parameters for meshes:</span></span>

1.  <span data-ttu-id="5b82e-159">Netzdaten für Okklusion verwenden</span><span class="sxs-lookup"><span data-stu-id="5b82e-159">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="5b82e-160">Konflikt für Mesh-Daten generieren</span><span class="sxs-lookup"><span data-stu-id="5b82e-160">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="5b82e-161">Navigations Gitter für Mesh-Daten generieren</span><span class="sxs-lookup"><span data-stu-id="5b82e-161">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="5b82e-162">Gitternetz Daten in Wireframe Renderingparameter – Debug</span><span class="sxs-lookup"><span data-stu-id="5b82e-162">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="5b82e-163">Für Projekte mit gemischter Realität werden diese Parameterwerte als die Standardwerte für die räumliche Zuordnung und die Hand gitterwerte verwendet.</span><span class="sxs-lookup"><span data-stu-id="5b82e-163">For mixed reality projects, these parameter values will be used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="5b82e-164">Entwickler können Sie in BP oder Code für ein bestimmtes Mesh ändern.</span><span class="sxs-lookup"><span data-stu-id="5b82e-164">Developers can change them in BP or code for any particular mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="5b82e-165">C++-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="5b82e-165">C++ API Reference</span></span> 
```cpp
enum class EARObjectClassification : uint8
{
// other types 
    HandMesh,
};
```

<span data-ttu-id="5b82e-166">Dieser Wert ist das Hand Mesh unter allen nachverfolgbare-Objekten.</span><span class="sxs-lookup"><span data-stu-id="5b82e-166">This value is the hand mesh among all trackable objects.</span></span>

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

<span data-ttu-id="5b82e-167">Diese Delegaten werden aufgerufen, wenn das System ein nachverfolgbare-Objekt erkennt, einschließlich eines Hand Netzes.</span><span class="sxs-lookup"><span data-stu-id="5b82e-167">These delegates are called when the system detects any trackable object, including a hand mesh.</span></span> 
```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```
<span data-ttu-id="5b82e-168">Handler für die Delegaten sollten die folgende Signatur aufweisen:</span><span class="sxs-lookup"><span data-stu-id="5b82e-168">Handlers to the delegates should have the following signature:</span></span>
```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

<span data-ttu-id="5b82e-169">Auf Mesh-Daten kann über zugegriffen werden.`UARTrackedGeometry::GetUnderlyingMesh`</span><span class="sxs-lookup"><span data-stu-id="5b82e-169">Mesh data can be accessed by `UARTrackedGeometry::GetUnderlyingMesh`</span></span>

### <a name="blueprint-api-reference"></a><span data-ttu-id="5b82e-170">Referenz zur Blueprint-API</span><span class="sxs-lookup"><span data-stu-id="5b82e-170">Blueprint API Reference</span></span>

<span data-ttu-id="5b82e-171">Entwickler sollten einer Blueprint-Actor-Komponente eine "AR trackable notify"-Komponente hinzufügen</span><span class="sxs-lookup"><span data-stu-id="5b82e-171">Developers should add an AR Trackable Notify Component to a Blueprint actor</span></span>

![Meldung zu einem darstellbaren Element](images/unreal/ar-trackable-notify.png)
 
<span data-ttu-id="5b82e-173">Wechseln Sie dann zu den Details der Komponente.</span><span class="sxs-lookup"><span data-stu-id="5b82e-173">Then go to the component’s details</span></span> 

![Artrackable Benachrichtigen 2](images/unreal/ar-trackable-notify2.png)
 
<span data-ttu-id="5b82e-175">Und überschreiben Sie die überwachte Geometrie zum Hinzufügen/Aktualisieren/entfernen mit Code wie dem folgenden:</span><span class="sxs-lookup"><span data-stu-id="5b82e-175">And overwrite On Add/Update/Remove Tracked Geometry with code like the below:</span></span>

![Bei der über sichtbaren Benachrichtigung](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a><span data-ttu-id="5b82e-177">Hand Strahlen</span><span class="sxs-lookup"><span data-stu-id="5b82e-177">Hand Rays</span></span>

<span data-ttu-id="5b82e-178">Entwickler können einen Hand Strahl als Zeigegerät verwenden.</span><span class="sxs-lookup"><span data-stu-id="5b82e-178">Developers can use a hand ray as a pointing device.</span></span> <span data-ttu-id="5b82e-179">Das System ist in C++ und Blueprint verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5b82e-179">The system is available in C++ and Blueprint.</span></span> <span data-ttu-id="5b82e-180">Technisch gesehen macht es [Windows. UI. Input. Spatial. spatialpointerinteraktionsourcepose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5b82e-180">Technically it exposes [Windows.UI.Input.Spatial.SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose)</span></span>

<span data-ttu-id="5b82e-181">Es ist wichtig zu erwähnen, dass die Ergebnisse aller Funktionen jeden Frame ändern, dass Sie alle aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="5b82e-181">It’s important to mention that since the results of all the functions changes every frame, they are all made callable.</span></span> <span data-ttu-id="5b82e-182">Weitere Informationen zu reinen vs-Funktionen oder Aufruf baren [Funktionen finden Sie](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure) unter</span><span class="sxs-lookup"><span data-stu-id="5b82e-182">For more information about pure vs impure or callable functions, see [that](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span></span>

<span data-ttu-id="5b82e-183">Für Blueprint öffnen Sie "Windows Mixed Reality HMD"</span><span class="sxs-lookup"><span data-stu-id="5b82e-183">For Blueprint open “Windows Mixed Reality HMD”</span></span>

![Hand Strahlen-BP](images/unreal/hand-rays-bp.png)
 
<span data-ttu-id="5b82e-185">Für C++ include "windowsmixedrealityfunctionlibrary. h".</span><span class="sxs-lookup"><span data-stu-id="5b82e-185">For C++ include "WindowsMixedRealityFunctionLibrary.h"</span></span>

### <a name="enum"></a><span data-ttu-id="5b82e-186">Enum</span><span class="sxs-lookup"><span data-stu-id="5b82e-186">Enum</span></span>

![Eingabe Controller-Schaltflächen](images/unreal/input-controller-buttons.png)
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```
* <span data-ttu-id="5b82e-188">**Select** -– User hat das Select-Ereignis ausgelöst, das in hololens 2 von airtap oder Gaze und Commit ausgelöst werden kann.</span><span class="sxs-lookup"><span data-stu-id="5b82e-188">**Select** -– User triggered Select event, which can be triggered in HoloLens 2 by airtap or gaze and commit.</span></span> <span data-ttu-id="5b82e-189">Eine andere Möglichkeit, dieses Ereignis zu initiieren, besteht darin, "Select" zu sagen.</span><span class="sxs-lookup"><span data-stu-id="5b82e-189">Another way to trigger this event is to say “Select”.</span></span> 
* <span data-ttu-id="5b82e-190">**Grasp** – vom Benutzer ausgelöstes Ereignis zum Erfassen von Ereignissen, das in hololens 2 ausgelöst wird, indem die Finger des Benutzers in einem Hologram geschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="5b82e-190">**Grasp** -– User triggered Grasp event, which is triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span> 
```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```
* <span data-ttu-id="5b82e-191">**Notverfolgt** – die Hand ist nicht sichtbar.</span><span class="sxs-lookup"><span data-stu-id="5b82e-191">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="5b82e-192">Nach **verfolgte** –: die Hand ist vollständig nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="5b82e-192">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="5b82e-193">Struktur</span><span class="sxs-lookup"><span data-stu-id="5b82e-193">Struct</span></span>

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
* <span data-ttu-id="5b82e-195">**Ursprung** – Ursprung der Hand</span><span class="sxs-lookup"><span data-stu-id="5b82e-195">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="5b82e-196">**Richtung** – Richtung der Hand</span><span class="sxs-lookup"><span data-stu-id="5b82e-196">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="5b82e-197">**Up** – Up Vector of the Hand</span><span class="sxs-lookup"><span data-stu-id="5b82e-197">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="5b82e-198">**Ausrichtung** – Ausrichtung Quaternion</span><span class="sxs-lookup"><span data-stu-id="5b82e-198">**Orientation** – orientation quaternion</span></span> 
* <span data-ttu-id="5b82e-199">**Überwachungs Status** – aktueller Überwachungs Status</span><span class="sxs-lookup"><span data-stu-id="5b82e-199">**Tracking Status** – current tracking status</span></span>

### <a name="functions"></a><span data-ttu-id="5b82e-200">Functions</span><span class="sxs-lookup"><span data-stu-id="5b82e-200">Functions</span></span>

<span data-ttu-id="5b82e-201">Alle Funktionen sollten für die kontinuierliche Überwachung in jedem Frame aufgerufen werden können.</span><span class="sxs-lookup"><span data-stu-id="5b82e-201">All the functions should be callable on every frame for continuous monitoring.</span></span> 

![Informationen zum Darstellen von Zeigern](images/unreal/get-pointer-pose-info.png)
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```
<span data-ttu-id="5b82e-203">Die-Funktion gibt die vollständigen Informationen über die Richtung des Hand Strahl in diesem Frame zurück.</span><span class="sxs-lookup"><span data-stu-id="5b82e-203">The function returns the full information about the hand ray direction in this frame.</span></span> 

![Erfasste BP](images/unreal/is-grasped-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
<span data-ttu-id="5b82e-205">Gibt "true" zurück, wenn die Hand in diesem Frame erfasst wird.</span><span class="sxs-lookup"><span data-stu-id="5b82e-205">Returns true if the hand is grasped in this frame.</span></span> 

![Ist SELECT-Taste für BP](images/unreal/is-select-pressed-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```
<span data-ttu-id="5b82e-207">Gibt true zurück, wenn der Benutzer SELECT in diesem Frame ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="5b82e-207">Returns true if the user triggered Select in this frame.</span></span>

![Ist Schaltfläche, auf die ein](images/unreal/is-button-clicked-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```
<span data-ttu-id="5b82e-209">Gibt true zurück, wenn das Ereignis bzw. die Schaltfläche in diesem Frame ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="5b82e-209">Returns true if the event/button is triggered in this frame.</span></span>

![Controller-Überwachungs Status-BP erhalten](images/unreal/get-controller-tracking-status-bp.png)
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
<span data-ttu-id="5b82e-211">Gibt den verfolgungsstatus in diesem Frame zurück.</span><span class="sxs-lookup"><span data-stu-id="5b82e-211">Returns the tracking status in this frame.</span></span>

## <a name="gestures"></a><span data-ttu-id="5b82e-212">Gesten</span><span class="sxs-lookup"><span data-stu-id="5b82e-212">Gestures</span></span>

<span data-ttu-id="5b82e-213">Die hololens 2 können räumliche Gesten nachverfolgen.</span><span class="sxs-lookup"><span data-stu-id="5b82e-213">The Hololens 2 can track spatial gestures.</span></span> <span data-ttu-id="5b82e-214">Details zu diesen Gesten finden Entwickler darin, dass Sie von Entwicklern als Eingabe für ihre gemischte Reality-Anwendung [erfasst werden können](https://docs.microsoft.com/hololens/hololens2-basic-usage) .</span><span class="sxs-lookup"><span data-stu-id="5b82e-214">Details about these gestures are [here](https://docs.microsoft.com/hololens/hololens2-basic-usage) A developer can capture them as input to their mixed reality application.</span></span> 

<span data-ttu-id="5b82e-215">Die C++-Funktion befindet sich in "windowsmixedrealityspatialinputfunctionlibrary. h".</span><span class="sxs-lookup"><span data-stu-id="5b82e-215">The C++ function is in "WindowsMixedRealitySpatialInputFunctionLibrary.h"</span></span>

<span data-ttu-id="5b82e-216">Die Blueprint-Funktion befindet sich in der räumlichen Eingabe von Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="5b82e-216">The Blueprint function is in Windows Mixed Reality Spatial Input</span></span>

![Erfassungs Gesten](images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="5b82e-218">Enum</span><span class="sxs-lookup"><span data-stu-id="5b82e-218">Enum</span></span>

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
<span data-ttu-id="5b82e-220">Diese Aufzählung beschreibt die Gesten räumlicher Achsen.</span><span class="sxs-lookup"><span data-stu-id="5b82e-220">This enum describes spatial axis gestures.</span></span> <span data-ttu-id="5b82e-221">Weitere Informationen finden Sie [hier](holograms-211.md) .</span><span class="sxs-lookup"><span data-stu-id="5b82e-221">You can read about them [here](holograms-211.md)</span></span>

### <a name="function"></a><span data-ttu-id="5b82e-222">Funktion</span><span class="sxs-lookup"><span data-stu-id="5b82e-222">Function</span></span>

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
<span data-ttu-id="5b82e-224">Die-Funktion aktiviert und deaktiviert die Erfassung von Gesten.</span><span class="sxs-lookup"><span data-stu-id="5b82e-224">The function enables and disables capturing of gestures.</span></span> <span data-ttu-id="5b82e-225">Die aktivierten Gesten lösen Eingabeereignisse aus.</span><span class="sxs-lookup"><span data-stu-id="5b82e-225">The enabled gestures fire input events.</span></span> <span data-ttu-id="5b82e-226">Sie gibt true zurück, wenn das Aktivieren der Gesten Erfassung erfolgreich war, und false, wenn ein Fehler vorliegt.</span><span class="sxs-lookup"><span data-stu-id="5b82e-226">It returns true if enabling gesture capture succeeded and false if there's an error.</span></span>
<span data-ttu-id="5b82e-227">Schlüsselereignisse</span><span class="sxs-lookup"><span data-stu-id="5b82e-227">Key Events</span></span>

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
<span data-ttu-id="5b82e-230">Wenn die Geste aktiviert ist, beginnt das Auslösen der Ereignisse.</span><span class="sxs-lookup"><span data-stu-id="5b82e-230">If the gesture is enabled, the events begin firing.</span></span> 

