---
title: Hands-und Motion-Controller in DirectX
description: Entwicklerhandbuch zur Verwendung von Hand Verfolgungs-und Bewegungs Controllern in nativen DirectX-apps.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/30/2019
ms.topic: article
keywords: Hands, Motion Controllers, DirectX, Input, holograms
ms.openlocfilehash: 54eaacc3f0dccf728b5438c020a5efd7e0788251
ms.sourcegitcommit: 4081dc2356fec0ea3625f1d989689cfbbb3fcf5f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2019
ms.locfileid: "74203330"
---
# <a name="hands-and-motion-controllers-in-directx"></a>Hands-und Motion-Controller in DirectX

In der gemischten Realität von Windows werden sowohl Hand-als auch [Bewegungs Controller](motion-controllers.md) Eingaben über die räumlichen Eingabe-APIs behandelt, die sich im [Windows. UI. Input. Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) -Namespace befinden. Dadurch **haben Sie die** Möglichkeit, häufig gängige Aktionen zu behandeln, z. b

## <a name="getting-started"></a>Erste Schritte

Wenn Sie in Windows Mixed Reality auf räumliche Eingaben zugreifen möchten, beginnen Sie mit der spatialinteraktionmanager-Schnittstelle.  Sie können auf diese Schnittstelle zugreifen, indem Sie [spatialinteraktionmanager:: getforcurrentview](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview)aufrufen, in der Regel beim Starten der app.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

Die Aufgabe von spatialinteraktionmanager besteht darin, den Zugriff auf [spatialinteraktionsources](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource)bereitzustellen, die eine Quelle für Eingaben darstellen.  Im System sind drei Arten von spatialinteraktionsources verfügbar.
* **Hand** stellt die erkannte Hand eines Benutzers dar. Hand Quellen bieten verschiedene Features, die auf dem Gerät basieren, von grundlegenden Gesten auf hololens bis hin zur vollständigen manuellen Nachverfolgung auf hololens 2. 
* **Controller** stellt einen gekoppelten Bewegungs Controller dar. Bewegungs Controller können eine Vielzahl von Funktionen bieten.  Beispiel: Auswählen von Triggern, Menü Schaltflächen, Zieh Schaltflächen, Touchpads und fingerstäbchen.
* **Voice** repräsentiert die von einem Benutzer festgestellten sprach Schlüsselwörter. Beispielsweise fügt diese Quelle eine SELECT Press-und-Freigabe ein, wenn der Benutzer "Select" anzeigt.

Pro-Frame-Daten für eine Quelle werden von der [spatialinteraktionsourcestate](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) -Schnittstelle dargestellt. Es gibt zwei verschiedene Möglichkeiten, auf diese Daten zuzugreifen, je nachdem, ob Sie ein Ereignis gesteuertem oder Abruf basiertes Modell in der Anwendung verwenden möchten.

### <a name="event-driven-input"></a>Ereignisgesteuerte Eingabe
Der spatialinteraktionsmanager stellt eine Reihe von Ereignissen bereit, die Ihre APP überwachen kann.  Einige Beispiele hierfür sind " [sourcepressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)", " [sourcereleasing](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) " und " [sourceupveraltet](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated)".

Der folgende Code verknüpft z. b. einen Ereignishandler mit dem Namen MyApp:: onsourcepressed zum sourcepressed-Ereignis.  Dadurch kann Ihre APP auf jeder Art von Interaktions Quelle drückt erkennen.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

Dieses gedrückte Ereignis wird asynchron an die APP gesendet, zusammen mit dem entsprechenden spatialinteraktionsourcestate zu dem Zeitpunkt, zu dem der Druck erfolgt ist. Ihre APP-oder Spiel-Engine möchte möglicherweise einige Verarbeitungsvorgänge ausführen, oder Sie möchten die Ereignisdaten in der Eingabe Verarbeitungsroutine in eine Warteschlange stellen. Hier ist eine Ereignishandlerfunktion für das sourcepressed-Ereignis, das zeigt, wie Sie überprüfen, ob die Select-Schaltfläche gedrückt wurde.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

void MyApp::OnSourcePressed(SpatialInteractionManager const& sender, SpatialInteractionSourceEventArgs const& args)
{
    if (args.PressKind() == SpatialInteractionPressKind::Select)
    {
        // Select button was pressed, update app state
    }
}
```

Der obige Code überprüft nur die SELECT-Taste, die der primären Aktion auf dem Gerät entspricht. Beispiele hierfür sind die Durchführung einer airtap auf hololens oder das Abrufen des Auslösers auf einem Bewegungs Controller.  "Select"-Pressen stellen dar, dass die Absicht des Benutzers ist, das Hologramm zu aktivieren, auf das Sie abzielen  Das sourcepressed-Ereignis wird für eine Reihe unterschiedlicher Schaltflächen und Gesten ausgelöst, und Sie können andere Eigenschaften auf der spatialinteraktionsource überprüfen, um diese Fälle zu testen.

### <a name="polling-based-input"></a>Abruf basierte Eingabe
Sie können auch spatialinteraktionmanager verwenden, um den aktuellen Status der Eingabe jedes Frame abzufragen.  Um dies zu erreichen, nennen Sie einfach [getdetectedsourcesattimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) jeden Frame.  Diese Funktion gibt ein Array zurück, das eine [spatialinteraktionsourcestate](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) für jede aktive [spatialinteraktionsource](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource)enthält. Dies bedeutet, dass eine für jeden aktiven Motion-Controller, eine für jede verfolgte Hand und eine für die Sprache, wenn ein SELECT-Befehl vor kurzem ausgesprochen wurde. Sie können dann die Eigenschaften auf den einzelnen spatialinteraktionsourcestate-Objekten überprüfen, um Eingaben in Ihre Anwendung zu steuern. 

Im folgenden finden Sie ein Beispiel für die Überprüfung der SELECT-Aktion mithilfe der Abruf Methode. Beachten Sie, dass die *Vorhersage* Variable ein [holographicframevorhersage](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) -Objekt darstellt, das aus dem [holographicframe](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)abgerufen werden kann.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
auto sourceStates = m_spatialInteractionManager.GetDetectedSourcesAtTimestamp(prediction.Timestamp());

for (auto& sourceState : sourceStates)
{
    if (sourceState.IsSelectPressed())
    {
        // Select button is down, update app state
    }
}
```

Jede spatialinteraktionsource verfügt über eine ID, mit der Sie neue Quellen identifizieren und vorhandene Quellen von Frame zu Frame korrelieren können.  Den Händen wird immer dann eine neue ID zugewiesen, wenn Sie den FOV verlassen, während die Controller-IDs für die Dauer der Sitzung statisch bleiben.  Sie können die Ereignisse in spatialinteraktionmanager, wie z. b. [sourceerkannten](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected) und [sourcelost](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost), verwenden, um zu reagieren, wenn die Hände in die Ansicht des Geräts eingegeben oder verlassen werden oder wenn Bewegungs Controller eingeschaltet/ausgeschaltet sind oder gekoppelt bzw. nicht gekoppelt sind.

### <a name="predicted-vs-historical-poses"></a>Vorhergesagte und Vergangenheits darstellen
Beachten Sie, dass getdetectedsourcesattimestamp über einen Zeitstempel-Parameter verfügt. Dies ermöglicht es Ihnen, den Zustand anzufordern und die vorhergesagten oder Verlaufs Daten darzustellen, sodass Sie räumliche Interaktionen mit anderen Quellen der Eingabe korrelieren können. Wenn Sie z. b. die Position der Hand im aktuellen Frame rendern, können Sie den vorhergesagten Zeitstempel übergeben, der von [holographicframe](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)bereitgestellt wird. Dies ermöglicht es dem System, die Position der Hand an der gerenderten Frame Ausgabe zu weiterleiten und die erkannte Latenz zu minimieren.

Eine solche vorhergesagte Pose erzeugt jedoch keinen idealen Zeige-Ray für das Ziel einer Interaktions Quelle. Wenn z. b. eine Bewegungs Controller Schaltfläche gedrückt wird, kann es bis zu 20 ms dauern, bis das Ereignis durch Bluetooth bis zum Betriebssystem hochskalieren kann. Wenn ein Benutzer eine Handbewegung durchführt, kann es auch passieren, dass eine gewisse Zeit verstreichen kann, bevor das System die Geste erkennt, und die APP anschließend abruft. Wenn Ihre APP eine Zustandsänderung abruft, werden die Kopfzeile und die Hand zum Ziel der Interaktion verwendet, die tatsächlich in der Vergangenheit aufgetreten ist. Wenn Sie als Ziel verwenden, indem Sie den Zeitstempel Ihres aktuellen holographicframe-Werts an getdetectedsourcesattimestamp übergeben, wird die Pose stattdessen auf dem Ziel-Ray zum Zeitpunkt der Anzeige des Frames (in der Zukunft mehr als 20 ms) vorhergesagt. Diese zukünftige Darstellung eignet sich gut zum *Rendern* der Interaktions Quelle, aber sorgt für unser Zeitproblem *für die Interaktion* , da die Zielvorgabe des Benutzers in der Vergangenheit erfolgte.

Glücklicherweise stellen die Ereignisse " [sourcepressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)", " [sourcereleasing](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) " und " [sourceupveralteten](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated) " den dem jeweiligen Eingabe Ereignis zugeordneten Verlaufs [Status](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) bereit.  Dies umfasst direkt die von [trygetpointerpose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)verfügbaren Verlaufs Daten und Handschrift stellen sowie einen historischen [Zeitstempel](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp) , den Sie an andere APIs übergeben können, um mit diesem Ereignis zu korrelieren.

Dies führt zu den folgenden bewährten Vorgehensweisen beim Rendern und als Ziel für die Verwendung von Händen und Controllern jedes Frames:
* Für das **Hand-/controllerrendering** der einzelnen Frames sollte Ihre APP die **Vorwärts Gesagte** Darstellung der einzelnen Interaktions Quellen in der Photonen Zeit des aktuellen Frames **Abfragen** .  Sie können alle Interaktions Quellen abrufen, indem Sie [getdetectedsourcesattimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) jedes Frame aufrufen und den von [holographicframe:: currentvorhersage](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.currentprediction)bereitgestellten vorhergesagten Zeitstempel übergeben.
* Für die Verwendung von **Hand/Controller** , die auf einen Press oder eine Freigabe abzielen, sollte Ihre APP gedrückte/freigegebene **Ereignisse**verarbeiten, und zwar basierend **auf der** Verlaufs Kopfzeile für dieses Ereignis. Sie erhalten diesen Ziel-Ray, indem Sie das [sourcepressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed) -oder [sourcereleasing](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) -Ereignis verarbeiten, die [State](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) -Eigenschaft von den Ereignis Argumenten abrufen und dann die [trygetpointerpose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) -Methode aufrufen.

## <a name="cross-device-input-properties"></a>Geräte übergreifende Eingabe Eigenschaften
Die spatialinteraktionsource-API unterstützt Controller und Hand Verfolgungs Systeme mit einer Vielzahl von Funktionen. Eine Reihe dieser Funktionen sind zwischen den Gerätetypen üblich. Beispielsweise stellen Hand Verfolgungs-und Bewegungs Controller eine SELECT-Aktion und eine 3D-Position bereit. Wenn möglich, ordnet die API diese gemeinsamen Funktionen denselben Eigenschaften auf der spatialinteraktionsource zu.  Dies ermöglicht es Anwendungen, eine breite Palette von Eingabetypen leichter zu unterstützen. In der folgenden Tabelle werden die Eigenschaften, die unterstützt werden, und deren Vergleich zwischen Eingabetypen beschrieben.

| Eigenschaft | Beschreibung | Bewegungen von hololens (1. Gen) | Motion-Controller | Handgelenk|
|--- |--- |--- |--- |--- |
| [Spatialinteraktionsource::**hängkeit**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | Rechts oder Links/Controller. | Nicht unterstützt | Unterstützt | Unterstützt |
| [Spatialinteraktionsourcestate::**isselectpressed**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | Aktueller Zustand der primären Schaltfläche. | Luft tippen | Trigger | Gelockerte Luft tippen (Aufrufe) |
| [Spatialinteraktionsourcestate::**isfasste**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | Aktueller Status der Schaltfläche "übernehmen". | Nicht unterstützt | Schaltfläche "" | Ein-oder geschlossene Hand Zeiger |
| [Spatialinteraktionsourcestate::**ismenupressed**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | Aktueller Zustand der Menü Schaltfläche.    | Nicht unterstützt | Menü Schaltfläche | Nicht unterstützt |
| [Spatialinteraktionsourcelokation::**Position**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | XYZ-Speicherort der Hand-oder Ziehpunkt Position auf dem Controller. | Palmen Standort | Position der Zieh Punktposition | Palmen Standort |
| [Spatialinteraktionsourcelokation::**Orientation**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | Die Quaternion, die die Ausrichtung der Hand oder des Zieh Punkts auf dem Controller darstellt. | Nicht unterstützt | Ziehpunkt Ausrichtung | Palmen Ausrichtung |
| [Spatialpointerinteraktionsourcepose::**Position**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | Ursprung des zeigenden Strahl. | Nicht unterstützt | Unterstützt | Unterstützt |
| [Spatialpointerinteraktionsourcepose::**forwarddirection**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | Richtung des zeigenden Strahls. | Nicht unterstützt | Unterstützt | Unterstützt |

Einige der oben aufgeführten Eigenschaften sind auf allen Geräten nicht verfügbar, und die API bietet eine Möglichkeit, um dies zu testen. Beispielsweise können Sie die Eigenschaft [spatialinteraktionsource:: isgrasp unterstützt](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported) überprüfen, um zu bestimmen, ob die Quelle eine vergrauaktion bereitstellt.

### <a name="grip-pose-vs-pointing-pose"></a>Ziehpunkt im Vergleich zu Zeige darstellen

Windows Mixed Reality unterstützt Bewegungs Controller in einer Vielzahl von Formfaktoren.  Sie unterstützt auch die Systeme für die Nachverfolgung von Hand  Alle diese Systeme verfügen über unterschiedliche Beziehungen zwischen der Handposition und der natürlichen Vorwärtsrichtung, die apps zum zeigen oder Rendern von Objekten in der Hand verwenden sollten.  Um dies zu unterstützen, gibt es zwei Arten von 3D-Posen, die sowohl für die Hand Verfolgung als auch für Bewegungs Controller bereitgestellt werden.  Der erste ist Ziehpunkt, der die Position des Benutzers darstellt.  Die zweite zeigt eine Darstellung, die ein zeigendes Strahl darstellt, das aus der Hand oder dem Controller des Benutzers stammt. Wenn Sie also **die Hand des Benutzers** oder ein Objekt, das **in der Hand des Benutzers gehalten**wird (z. b. ein Schwert oder eine Waffe), wiedergeben möchten, verwenden Sie die Ziehpunkt-Pose. Wenn Sie einen raycast von Controller oder Hand durchführen möchten, z. b. wenn der Benutzer auf die Benutzer **Oberfläche zeigt** , verwenden Sie die Zeige Pose.

Sie können auf die Ziehpunkt- **Pose** über [spatialinteraktionsourcestate zugreifen::P roperties:: trygetlocation (...)](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).  Es wird wie folgt definiert:
* Die Zieh **Punktposition**: der Palmen Schwerpunkt bei der natürlichen Aufbewahrung des Controllers, nach links oder rechts, um die Position im Ziehpunkt zu zentrieren.
* Die **Rechte Achse**der Ziehpunkt Ausrichtung: Wenn Sie Ihre Hand vollständig geöffnet haben, um eine flache 5-Finger-Darstellung zu bilden, ist das Strahl-Ray, das normal ist (vorwärts von links nach links, rückwärts von rechter Palme).
* Die **Forward-Achse**der Ziehpunkt Ausrichtung: Wenn Sie die Hand teilweise schließen (wie beim Halten des Controllers), wird der Strahl, der durch das durch ihre nicht-Thumb-Finger formatierte Rohr auf "Vorwärts" zeigt.
* Die **aufwärts Achse**der Ziehpunkt Ausrichtung: die aufwärts Achse, die durch die Rechte-und vorwärts Definitionen impliziert wird.

Sie können auf die **Zeiger Pose** über [spatialinteraktionsourcestate zugreifen::P roperties:: trygetlocation (...):: sourcepointerpose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) oder [spatialinteraktionsourcestate:: trygetpointerpose (...):: trygetinteraktionsourcepose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).

## <a name="controller-specific-input-properties"></a>Controller spezifische Eingabe Eigenschaften
Für Controller verfügt spatialinteraktionsource über eine Controller Eigenschaft mit zusätzlichen Funktionen.
* **Hasthumbstick:** True gibt an, dass der Controller über einen Finger Stick verfügt. Überprüfen Sie die [controllerproperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) -Eigenschaft des spatialinteraction SourceState-Objekts, um die x-und y-Werte des Finger Anrufs (thumbstickx und thumbthumb) sowie den gedrückten Zustand (isthumbstickpressed) abzurufen.
* **Hastouchpad:** True gibt an, dass der Controller über einen Touchpad verfügt. Überprüfen Sie die controllerproperties-Eigenschaft von spatialinteraction SourceState, um die Touchpad x-und y-Werte (touchpadx und touchpady) abzurufen und um zu ermitteln, ob der Benutzer den Pad berührt (istouchpadtoud) und ob er das Touchpad nach unten drückt ( Istouchpadpressed).
* **Simplehapticscontroller:** Die simplehapticscontroller-API für den Controller ermöglicht es Ihnen, die Haptik Funktionen des Controllers zu überprüfen. Außerdem können Sie das haptische Feedback steuern.

Beachten Sie, dass der Bereich für Touchpad und Ministick für beide Achsen-1 bis 1 ist (von unten nach oben und von links nach rechts). Der Bereich für den analogen-Auslösers, auf den mit der spatialinteraktionsourcestate:: selectpressedvalue-Eigenschaft zugegriffen wird, weist einen Bereich von 0 bis 1 auf. Der Wert 1 korreliert mit isselectpressed, das gleich true ist. alle anderen Werte korrelieren mit isselectpressed, das gleich false ist.

## <a name="articulated-hand-tracking"></a>Handgelenk Verfolgung
Die Windows Mixed Reality-API bietet vollständige Unterstützung für die Weitergabe von Handgelenk, z. b. auf hololens 2. Die Handschrift Nachverfolgung kann verwendet werden, um direkte Manipulations-und Punkt-und Commit-Eingabe Modelle in Ihren Anwendungen zu implementieren. Sie kann auch zum Erstellen vollständig benutzerdefinierter Interaktionen verwendet werden.

### <a name="hand-skeleton"></a>Hand Gerüst
Die gemischte Nachverfolgung bietet ein 25-Gerüst Gerüst, das viele verschiedene Arten von Interaktionen ermöglicht.  Das Gerüst bietet fünf Gelenke für den Index/den Mittelwert bzw. Ring/kleine Finger, vier Gelenke für den Ziehpunkt und 1 Gelenk Gelenk.  Das gemischte Gelenk fungiert als Basis der Hierarchie. Das folgende Bild veranschaulicht das Layout des Skeleton.

![Hand Gerüst](images/hand-skeleton.png)

In den meisten Fällen wird jedes Joint auf der Grundlage des von ihm dargestellten Knochens benannt.  Da bei jedem Joint zwei gedankenfelder vorhanden sind, verwenden wir eine Konvention, die jedes Joint-Element auf der Grundlage des untergeordneten knotes an diesem Speicherort zu benennen.  Der untergeordnete Knochen ist als der Knochen weiter vom Handgelenk definiert.  Beispielsweise enthält die Zusammenstellung "Index proximal" die Anfangsposition des Index "proximal" und die Ausrichtung dieses Knochens.  Die Endposition des-Knochens ist nicht enthalten.  Wenn Sie diese benötigen, erhalten Sie diese vom nächsten gemeinsamen Zusammenhang in der Hierarchie, dem "Index Intermediate"-Joint.

Zusätzlich zu den 25 hierarchischen Gelenken bietet das System eine Palmen Verbindung.  Die Palme wird in der Regel nicht als Teil der Skelettstruktur betrachtet.  Sie wird nur als bequeme Möglichkeit zur Verfügung gestellt, um die allgemeine Position und Ausrichtung der Hand zu erhalten.

Die folgenden Informationen werden für jedes Joint bereitgestellt:

| Name | Beschreibung |
|--- |--- |
|Position | 3D-Position des gemeinsamen, in jedem angeforderten Koordinatensystem verfügbar. |
|Ausrichtung | 3D-Ausrichtung des in jedem angeforderten Koordinatensystem verfügbaren knotes. |
|Radius | Abstand zur Oberfläche der Skin an der gemeinsamen Position. Nützlich für das optimieren direkter Interaktionen oder Visualisierungen, die auf der fingerbreite basieren. |
|Genauigkeit | Gibt Aufschluss darüber, wie sicher das System über diese gemeinsamen Informationen verfügt. |

Sie können auf die Hand Skeleton-Daten über eine Funktion auf dem [spatialinteraktionsourcestate](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)zugreifen.  Die Funktion heißt [trygethandpose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose)und gibt ein Objekt mit dem Namen [handpose](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose)zurück.  Wenn die Quelle keine Handgelenk Zeichen unterstützt, gibt diese Funktion NULL zurück.  Sobald Sie über eine Hand Pose verfügen, können Sie aktuelle gemeinsame Daten abrufen, indem Sie [trygetjoint](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__)mit dem Namen der zusammenhängenden aufrufen, an der Sie interessiert sind.  Die Daten werden als [jointpose](https://docs.microsoft.com//uwp/api/windows.perception.people.jointpose) -Struktur zurückgegeben.  Der folgende Code Ruft die Position des Finger Abbilds für den Index ab. Die Variable *CurrentState* stellt eine Instanz von [spatialinteraktionsourcestate](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)dar.

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::Foundation::Numerics;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    JointPose joint;
    if (handPose.TryGetJoint(desiredCoordinateSystem, HandJointKind::IndexTip, joint))
    {
        float3 indexTipPosition = joint.Position;

        // Do something with the index tip position
    }
}
```

### <a name="hand-mesh"></a>Hand Netz

Die API für die Nachverfolgung von Handschriften ermöglicht ein vollständig zu entformbares Dreieck-Mesh-Mesh.  Dieses Mesh kann sich zusammen mit dem Hand Gerüst in Echtzeit deformen und eignet sich für die Visualisierung sowie erweiterte Physik Techniken.  Um auf das Hand Mesh zuzugreifen, müssen Sie zuerst ein [handmeshobserver](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver) -Objekt erstellen, indem Sie [trycreatehandmeshobserverasync](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync) auf der [spatialinteraktionsource](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource)aufrufen.  Dies muss nur einmal pro Quelle erfolgen, normalerweise wenn Sie das erste Mal sehen.  Das heißt, Sie rufen diese Funktion auf, um ein handmeshobserver-Objekt zu erstellen, wenn eine Hand in den FOV gelangt.  Beachten Sie, dass es sich hierbei um eine asynchrone Funktion handelt, sodass Sie hier ein bisschen Parallelität behandeln müssen.  Sobald Sie verfügbar sind, können Sie das handmeshobserver-Objekt für den Dreiecks Index Puffer durch Aufrufen von [gettriangleindices](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___)Abfragen.  Indizes ändern den Frame nicht über Frame, sodass Sie diese einmal erhalten und für die Lebensdauer der Quelle Zwischenspeichern können.  Indizes werden in der Reihenfolge im Uhrzeigersinn bereitgestellt.

Der folgende Code startet einen getrennten Std:: Thread, um den Mesh-Beobachter zu erstellen, und extrahiert den Index Puffer, sobald der Mesh-Beobachter verfügbar ist.  Sie beginnt mit einer Variablen namens *CurrentState*, bei der es sich um eine Instanz von [spatialinteraktionsourcestate](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) handelt, die eine nach verfolgte Hand darstellt.

```cpp
using namespace Windows::Perception::People;

std::thread createObserverThread([this, currentState]()
{
    HandMeshObserver newHandMeshObserver = currentState.Source().TryCreateHandMeshObserverAsync().get();
    if (newHandMeshObserver)
    {
        unsigned indexCount = newHandMeshObserver.TriangleIndexCount();
        vector<unsigned short> indices(indexCount);
        newHandMeshObserver.GetTriangleIndices(indices);

        // Save the indices and handMeshObserver for later use - and use a mutex to synchronize access if needed!
     }
});
createObserverThread.detach();
```
Das Starten eines getrennten Threads ist nur eine Option für die Behandlung von asynchronen Aufrufen.  Alternativ dazu können Sie die neue von [](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) C++/WinRT. unterstützte co_await Funktionalität verwenden.

Wenn Sie über ein handmeshobserver-Objekt verfügen, sollten Sie es für die Dauer aufbewahren, in der die zugehörige spatialinteraktionsource aktiv ist.  Anschließend können Sie den einzelnen Frame aufrufen, um den aktuellen Vertex-Puffer zu Fragen, der die Hand darstellt, indem Sie [getvertexstateforpose](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose) aufrufen und eine [handpose](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose) -Instanz übergeben, die die Darstellung darstellt, für die Sie Vertices wünschen.  Jeder Scheitelpunkt im Puffer hat eine Position und einen normalen.  Im folgenden finden Sie ein Beispiel dafür, wie Sie den aktuellen Satz von Scheitel Punkten für ein Hand Mesh erhalten.  Ebenso wie zuvor stellt die *CurrentState* -Variable eine Instanz von [spatialinteraktionsourcestate](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)dar.

```cpp
using namespace winrt::Windows::Perception::People;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    std::vector<HandMeshVertex> vertices(handMeshObserver.VertexCount());
    auto vertexState = handMeshObserver.GetVertexStateForPose(handPose);
    vertexState.GetVertices(vertices);

    auto meshTransform = vertexState.CoordinateSystem().TryGetTransformTo(desiredCoordinateSystem);
    if (meshTransform != nullptr)
    {
        // Do something with the vertices and mesh transform, along with the indices that you saved earlier
    }
}
```

Im Gegensatz zu Skelett Gelenken lässt die Hand Mesh-API nicht zu, dass Sie ein Koordinatensystem für die Scheitel Punkte angeben.  Stattdessen gibt der [handmeshvertexstate](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshvertexstate) das Koordinatensystem an, in dem die Vertices bereitgestellt werden.  Sie können dann eine Mesh-Transformation abrufen, indem Sie [trygettransformto](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_) aufrufen und das gewünschte Koordinatensystem angeben.  Sie müssen diese Mesh-Transformation verwenden, wenn Sie mit den Scheitel Punkten arbeiten.  Dieser Ansatz reduziert den CPU-Overhead, insbesondere dann, wenn Sie nur das Mesh für renderingzwecke verwenden.

## <a name="gaze-and-commit-composite-gestures"></a>Zusammengesetzte Gesten durchschauen und Commit
Für Anwendungen, die das "Blick-und Commit"-Eingabe Modell verwenden, insbesondere in hololens (erste Generation), bietet die räumliche Eingabe-API einen optionalen [spatialgesturerecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) , der verwendet werden kann, um zusammengesetzte Gesten zu aktivieren, die auf dem "Select"-Ereignis basieren.  Durch die Weiterleitung von Interaktionen zwischen spatialinteraktionmanager und dem spatialgesturerecognizer eines holograms können apps Tap-, Hold-, Bearbeitungs-und Navigations Ereignisse gleichmäßig über die Hand-, sprach-und räumliche Eingabegeräte hinweg erkennen, ohne dass die Pressen behandelt werden müssen. und werden manuell freigegeben.

Spatialgesturerecognizer führt nur die minimale Eindeutigkeit zwischen dem Satz von Gesten aus, den Sie anfordern. Wenn Sie z. b. "nur tippen" anfordern, kann der Benutzer den Finger so lange herunterhalten, wie er aussieht, und es tritt immer noch ein tippen auf. Wenn Sie sowohl Tippen als auch halten anfordern, wird die Stift Bewegung nach ungefähr einer Sekunde angehalten, und es wird kein Tippen mehr angezeigt.

Wenn Sie spatialgesturerecognizer verwenden möchten, behandeln Sie das [interaktionerkannte](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) -Ereignis von spatialinteraktionmanager, und rufen Sie das dort verfügbare spatialpointerpose-Element ab. Verwenden Sie den Head-Gaze-Strahl des Benutzers aus dieser Pose, um sich mit den Hologrammen und Oberflächen Netzen in der Benutzerumgebung auszutauschen, um zu bestimmen, mit welchem Benutzer interagiert werden soll. Leiten Sie dann die spatialinteraktion in den Ereignis Argumenten an den spatialgesturerecognizer des Ziel-Hologramms weiter, indem Sie die zugehörige [captureinteraktions](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) -Methode verwenden. Dies beginnt mit der Interpretation dieser Interaktion gemäß der [spatialgesturesettings-Einstellung](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) , die bei der Erstellungszeit für diese Erkennung festgelegt wurde, oder durch [trysetgesturesettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).

Bei hololens (erste Generation) sollten Interaktionen und Gesten im Allgemeinen die Zielvorgabe von der Kopfzeile des Benutzers ableiten, anstatt zu versuchen, direkt an der Position der Hand zu arbeiten. Nachdem eine Interaktion begonnen hat, können relative Bewegungen der Hand verwendet werden, um die Bewegung zu steuern, wie bei der Manipulation oder Navigation.

## <a name="see-also"></a>Weitere Informationen
* [Anvisieren mit dem Kopf und mit den Augen in DirectX](gaze-in-directx.md)
* [Eingabe Modell für direkte Manipulation](direct-manipulation.md)
* [Punkt-und Commit-Eingabe Modell](point-and-commit.md)
* [Überblicks-und Commit-Eingabe Modell](gaze-and-commit.md)
* [Motion-Controller](motion-controllers.md)
