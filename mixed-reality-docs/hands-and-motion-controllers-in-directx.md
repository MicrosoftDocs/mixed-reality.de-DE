---
title: Praktische und Motion-Controllern in DirectX
description: Entwicklerhandbuch für die Verwendung von Hand nachverfolgen und während der Übertragung-Controllern in systemeigenen DirectX-apps.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/30/2019
ms.topic: article
keywords: praktische Motion-Controller "," Directx "," Input ","-Hologramme
ms.openlocfilehash: 08666c8c26cd4851c0c003a96a9e96d7a90228ac
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629643"
---
# <a name="hands-and-motion-controllers-in-directx"></a>Praktische und Motion-Controllern in DirectX

In Windows Mixed Reality, beide übergeben und [Motion-Controller](motion-controllers.md) Eingabe erfolgt über die die räumlichen Eingabe-APIs finden Sie in der [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) Namespace. Dadurch können Sie Baseler Ausschusses für häufig verwendete Aktionen wie **wählen** drückt die gleiche Weise wie für praktische und Motion-Controller.

## <a name="getting-started"></a>Erste Schritte

Zugriff auf räumliche Geben Sie in Windows Mixed Reality beginnen Sie mit der SpatialInteractionManager-Schnittstelle.  Sie können diese Schnittstelle zugreifen, durch den Aufruf [SpatialInteractionManager::GetForCurrentView](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview), in der Regel manchmal während des Starts der app.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

Die SpatialInteractionManagers Aufgabe besteht darin, geben Sie den Zugriff auf [SpatialInteractionSources](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource), die eine Quelle für die Eingabe darstellen.  Es gibt drei Arten von SpatialInteractionSources im System verfügbar.
* **Hand** erkannte Hand eines Benutzers darstellt. Verfügbare Quellen bieten verschiedene Funktionen, die basierend auf dem Gerät, von der grundlegenden Gesten für HoloLens bis hin zu vollständig angezeigte Seite, die workflowüberwachung HoloLens 2. 
* **Controller** einen gekoppelten Motion-Controller darstellt. Während der Übertragung Controller können es sich um eine Vielzahl von Funktionen bieten.  Zum Beispiel: Wählen Sie die Trigger, Menüschaltflächen, verstehen Schaltflächen, Touchpad und Thumbsticks.
* **Voice** des Benutzers Voice Schlüsselwörter System hat Vorträge darstellt. Beispielsweise wird dieser Quelle einfügen drücken, auf einer Option und freizugeben, wenn der Benutzer sagt "Select".

Pro-Frame Daten für eine Quelle entspricht der [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) Schnittstelle. Es gibt zwei Möglichkeiten zum Zugriff auf diese Daten, je nachdem, ob Sie ein ereignisgesteuertes oder abrufbasierten-Modell in Ihrer Anwendung verwenden möchten.

### <a name="event-driven-input"></a>Ereignisgesteuerte Eingabe
Die SpatialInteractionManager bietet es sich um eine Reihe von Ereignissen, denen Ihrer app überwachen kann.  Einige Beispiele hierfür sind [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) und [SourceUpdated](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated).

Der folgende Code z. B. verknüpft einen Ereignishandler namens MyApp::OnSourcePressed auf das Ereignis SourcePressed.  Dadurch kann es sich um Ihre app um drückt auf jede Art von Interaktion Quelle zu erkennen.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

Dieses Ereignis gedrückte wird zu Ihrer app asynchron zusammen mit den entsprechenden SpatialInteractionSourceState zum Zeitpunkt gesendet, drücken Sie die aufgetreten sind. Ihre app oder eine Spiele-Engine möglicherweise ausführen möchten sofort verarbeiten oder möglicherweise möchten die Daten in der Eingabe verarbeiten Routine in die Warteschlange. Hier ist eine Ereignishandlerfunktion für das SourcePressed-Ereignis, das zeigt, wie Sie überprüfen, ob die auswählen-Schaltfläche gedrückt wurde.

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

Der obige Code überprüft nur die "Select" Press, die der primären Aktion auf dem Gerät entspricht. Beispiele hierfür sind ein AirTap für HoloLens oder das Abrufen des Triggers für einen Controller während der Übertragung.  'Select' drückt darstellen des Benutzers Absicht an, die – Hologramm aktiviert werden, die sie verwenden möchten.  Das SourcePressed-Ereignis wird ausgelöst, für eine Reihe von verschiedene Schaltflächen und Gesten, und Sie können überprüfen, dass andere Eigenschaften auf der SpatialInteractionSource für diese Fälle zu testen.

### <a name="polling-based-input"></a>Abrufbasierten Eingabe
Sie können auch SpatialInteractionManager verwenden, für den aktuellen Status der Eingabe jedes Bild abrufen.  Zu diesem Zweck rufen Sie ganz einfach [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) jeder Frame.  Diese Funktion gibt ein Array mit einer [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) für jede aktive [SpatialInteractionSource](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource). Dies bedeutet eine für jeden aktiven Motion-Controller, eine für jeden überwachten Hand und eine für Sprache, wenn ein Befehl "select" kürzlich uttered wurde. Sie können die Eigenschaften auf jeder SpatialInteractionSourceState auf Laufwerk Eingabe klicken Sie dann in Ihre Anwendung prüfen. 

Hier ist ein Beispiel für das Verwenden der Abrufmethode für die'select'-Aktion zu überprüfen. Beachten Sie, dass die *Vorhersage* Variable steht für eine [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) -Objekt, das aus abgerufen werden kann die [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).

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

Jede SpatialInteractionSource verfügt über eine ID, die Sie verwenden können, geben Sie die neue Datenquellen und die vorhandene Quellen von Frame zu Frame zu korrelieren.  Jedes Mal, wenn sie lassen, und geben Sie das Blickfeld, aber der Controller-IDs für die Dauer der Sitzung statisch bleiben, werden praktische eine neue ID zugewiesen.  Sie können die Ereignisse auf SpatialInteractionManager wie z. B. [SourceDetected](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected) und [SourceLost](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost), zur Reaktion Hand eingeben, oder lassen Sie das Gerät auf der Anzeige oder wenn während der Übertragung Controller sind aktiviert und deaktiviert oder sind gekoppelte/Ungepaarte.

### <a name="predicted-vs-historical-poses"></a>Im Vergleich zu historischen stellt vorhergesagt
Beachten Sie, dass GetDetectedSourcesAtTimestamp einen Timestampparameter. Dadurch können Sie Anforderungsstatus und Darstellen von Daten, die entweder vorhergesagt werden, oder historische, sodass Sie die räumliche Interaktionen mit anderen Quellen der Eingabe korrelieren. Z. B. das Handsymbol des Position im aktuellen Frame zu rendern, Sie können übergeben der vorhergesagten Zeitstempel, der durch die [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe). Dadurch kann es sich um das System, um die Position des Zeigers an das eng mit der gerenderte Frame-Ausgabe, die gefühlte Latenz minimieren Forward vorherzusagen.

Solche eine vorhergesagte Haltung ergibt jedoch keine ideale zeigen Chow mit einer Datenquelle für die Interaktion auf. Wenn eine Controller mit der Schaltfläche gedrückt wird, kann es beispielsweise bis zu 20 ms für das Ereignis über Bluetooth an das Betriebssystem Bubbling dauern. Nachdem ein Benutzer eine Geste für ein manuell ausführt, kann auf ähnliche Weise eine bestimmte Zeit verstreichen, bevor das System die Bewegung und Ihre app erkennt dann fragt Sie ab. Durch die Zeit Ihrer app führt eine Abfrage für eine statusänderung, verwendet die Haupt- und Hand ist Ziel, die Interaktion tatsächlich in der Vergangenheit aufgetreten sind. Wenn Sie abzielen, indem Sie Ihre aktuellen HolographicFrames Zeitstempel an GetDetectedSourcesAtTimestamp übergeben, wird der Haltung stattdessen weiterleiten vorhergesagt werden, die für die Zielgruppenadressierung Chow zum Zeitpunkt der Rahmen angezeigt wird, kann die mehr als 20 ms in der Zukunft liegen. Diese Haltung zukünftige eignet sich gut für *Rendering* die Interaktion-Quelle, aber auch unser Problem Zeit für *für* Interaktion, wie der Benutzer als Ziel, die in der Vergangenheit aufgetreten sind.

Glücklicherweise die [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) und [SourceUpdated](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated) Ereignisse bieten die historischen [Zustand](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) zugeordnet jedes Eingabeereignis.  Dies schließt direkt den Verlaufsdaten Head "und" manuell ist, die über [TryGetPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose), zusammen mit einer historischen [Zeitstempel](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp) , die an andere APIs zur Korrelation mit diesem Ereignis übergeben werden können.

Daraus ergibt sich die folgenden bewährten Methoden beim Rendern und Ziele mit Hände und Controller alle Frames:
* Für **Hand/Controller Rendering** jeden Frame Ihre app sollte **Abruf** für die **Forward-vorhergesagt** jeder Quelle für die Interaktion des aktuellen Frames Photon Zeitpunkt darstellen.  Sie können für alle Interaktion Quellen abrufen, durch den Aufruf [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) jeden Frame, übergibt des vorhergesagten Zeitstempels von bereitgestellten [HolographicFrame::CurrentPrediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.currentprediction).
* Für **Hand/Controller als Ziel** anhand eines drücken oder die Version, sollte Ihre app behandeln, gedrückt/veröffentlicht **Ereignisse**, feinheiten beim Raycasting basierend auf den **historische** Haupt- oder manuell Haltung für Dieses Ereignis. Erhalten Sie diese für die Zielgruppenadressierung Chow durch Behandeln der [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed) oder [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) Ereignis Abrufen der [Zustand](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) Eigenschaft aus den Ereignisargumenten und dem anschließenden Aufrufen der [ TryGetPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) Methode.

## <a name="cross-device-input-properties"></a>Geräteübergreifende Eingabeeigenschaften
Die SpatialInteractionSource-API unterstützt die Controller und manuell Nachverfolgen von Systemen mit einer Vielzahl von Funktionen. Diese Funktionen sind häufig zwischen Gerät und Typen. Geben Sie z. B. manuell nachverfolgen und während der Übertragung Domänencontroller sowohl auf, eine Aktion "auswählen" und eine 3D-Position. Wo immer dies möglich ist, wird die API diese allgemeinen Funktionen die gleichen Eigenschaften für die SpatialInteractionSource zugeordnet.  Dies ermöglicht es Anwendungen leichter eine Vielzahl von Eingabetypen zu unterstützen. Die folgende Tabelle beschreibt die Eigenschaften, die unterstützt werden und wie sie über Eingabetypen vergleichen.

| Eigenschaft | Beschreibung | HoloLens-Gesten | Motion-Controller | Umrissene Händen|
|--- |--- |--- |--- |--- |
| [SpatialInteractionSource::**Händigkeit**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | Rechten oder linken / Controller. | Nicht unterstützt | Unterstützt | Unterstützt |
| [SpatialInteractionSourceState::**IsSelectPressed**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | Aktuellen Status der primären Schaltfläche. | Tippen Sie auf | Trigger | Gelockerte Air tippen (aufrechte verkleinern) |
| [SpatialInteractionSourceState::**IsGrasped**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | Aktuelle Zustand der Schaltfläche Ziehpunkte. | Nicht unterstützt | Ziehen Sie die Schaltfläche " | Zoomgesten oder geschlossenen manuell |
| [SpatialInteractionSourceState::**IsMenuPressed**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | Aktuellen Status der Menü-Schaltfläche.    | Nicht unterstützt | Menütaste | Nicht unterstützt |
| [SpatialInteractionSourceLocation::**Position**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | XYZ-Speicherort, der manuell oder durch Ziehpunkt Position auf dem Controller. | Palm-Speicherort | Ziehpunkt Haltung position | Palm-Speicherort |
| [SpatialInteractionSourceLocation::**Orientation**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | Die Quaternion, die die Ausrichtung der Hand oder des Ziehpunkts zur Größenänderung darstellt darstellen, auf dem Controller. | Nicht unterstützt | Ziehpunkt Haltung Ausrichtung | Palm-Ausrichtung |
| [SpatialPointerInteractionSourcePose::**Position**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | Der Ursprung des Strahls zeigen. | Nicht unterstützt | Unterstützt | Unterstützt |
| [SpatialPointerInteractionSourcePose::**ForwardDirection**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | Die Richtung des Strahls zeigen. | Nicht unterstützt | Unterstützt | Unterstützt |

Einige der oben genannten Eigenschaften sind nicht auf allen Geräten verfügbar, und die API bietet die Möglichkeit, dies zu testen. Sie können z. B. Überprüfen der [SpatialInteractionSource::IsGraspSupported](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported) Eigenschaft, um zu bestimmen, ob die Quelle eine Aktion verstehen.

### <a name="grip-pose-vs-pointing-pose"></a>Ziehpunkt Haltung im Vergleich zu zeigenden Haltung

Windows Mixed Reality unterstützt die Motion-Controller in einer Vielzahl von Formfaktoren.  Darüber hinaus wird die angezeigte Seite tracking-Systeme unterstützt.  Alle diese Systeme verfügen über unterschiedliche Beziehungen zwischen die Position des Zeigers und der natürliche "Weiterleiten" Richtung, die apps für verweist oder Rendreing Objekte des Benutzers verfügen verwendet werden soll.  Um all dies zu unterstützen, gibt es zwei Arten von 3D für beide Controller Hand, nachverfolgung und während der Übertragung angegeben ist.  Die erste ist Ziehpunkt Haltung, in der Hand-Position des Benutzers darstellt.  Die zweite handelt es sich um Haltung, verweist das ein zeigen Strahl von Hand oder Controller des Benutzers darstellt. Wenn Sie rendern möchten **des Benutzers manuell** oder **frei, die ein Objekt des Benutzers verfügen**, z. B. ein "sword" oder ein damoklesschwert, verwenden den Ziehpunkt Haltung. Wenn Sie möchten Raycast in den Controller bzw. die Hand, z. B. wenn der Benutzer ist **zeigen Sie auf der Benutzeroberfläche** , verwenden Sie die Haltung zeigen.

Sie können den Zugriff auf die **Ziehpunkt Haltung** über [SpatialInteractionSourceState::Properties::TryGetLocation(...) ](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).  Es ist wie folgt definiert:
* Die **fassen Sie Position**: Der Schwerpunkt Palm, wenn der Controller natürlich mit angepasst nach links oder rechts zentriert die Position in den Ziehpunkt.
* Die **fassen Sie die rechte Achse die Ausrichtung**: Wenn Sie Ihre Hand, um einen flachen 5 Finger Haltung bilden vollständig geöffnet haben, dem Strahl, der ist normal, zu Ihrem Palm (vorwärts vom linken Palm, rückwärts von rechts Palm)
* Die **fassen Sie die Ausrichtung, vorwärts gerichtete Achse**: Wenn Sie Ihre Hand schließen, teilweise (als ob den Controller enthält), der vom Strahl, der "forward" über die Tube gebildet, indem die Finger nicht-Thumb-Steuerelement zeigt.
* Die **fassen Sie die Ausrichtung des einrichten Achse**: Die nach-oben-Achse impliziert durch die rechts- und -Weiterleiten-Definitionen.

Sie können den Zugriff auf die **Zeiger Haltung** über [SpatialInteractionSourceState::Properties::TryGetLocation (...):: SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) oder [SpatialInteractionSourceState:: TryGetPointerPose (...):: TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).

## <a name="controller-specific-input-properties"></a>Controller-spezifische Eingabeeigenschaften
Für Controller verwendet hat die SpatialInteractionSource eine Controller-Eigenschaft, mit zusätzlichen Funktionen.
* **HasThumbstick:** Bei "true", hat der Controller eine Ministick an. Überprüfen Sie die [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) Eigenschaft der SpatialInteractionSourceState Ministick abrufen x und y-Werte (ThumbstickX und ThumbstickY) sowie ihren aktuellen Status (IsThumbstickPressed).
* **HasTouchpad:** Bei "true", hat der Controller Touchpads an. Überprüfen Sie die ControllerProperties-Eigenschaft, der die SpatialInteractionSourceState zum Abrufen der Touchpad x- und y Werte (TouchpadX und TouchpadY), und wissen, ob der Benutzer das Pad "" (IsTouchpadTouched) berührt, und wenn sie das Touchpad nach unten (drücken, werden IsTouchpadPressed).
* **SimpleHapticsController:** Die SimpleHapticsController-API für den Controller können Sie die Funktionen Haptics des Controllers zu überprüfen, und sie können außerdem zum Übermitteln von haptischem Feedback zu steuern.

Beachten Sie, dass der Bereich für Touchpad und Ministick-1 für beide Achsen auf 1 (von unten nach oben und von links nach rechts). Der Bereich für den analogen Trigger, die mithilfe der SpatialInteractionSourceState::SelectPressedValue-Eigenschaft zugegriffen wird, hat es sich um einen Bereich von 0 bis 1. Ein Wert von 1 korreliert mit IsSelectPressed ist gleich "true". Jeder andere Wert korreliert mit IsSelectPressed ist gleich "false".

## <a name="articulated-hand-tracking"></a>Umrissene manuell nachverfolgen
Die Windows Mixed Reality-API bietet vollständige Unterstützung für definierte manuell nachverfolgen, z. B. für HoloLens 2. Articulated manuell nachverfolgen kann verwendet werden, um die direkte Bearbeitung und Punkt-und-Commit-Eingabe-Modelle in Ihren Anwendungen implementieren. Sie können auch verwendet werden, vollständig benutzerdefinierte Aktivitäten erstellen.

### <a name="hand-skeleton"></a>Hand-Gerüst
Angezeigte Seite, die nachverfolgung bietet eine 25 joint Gerüst, das viele verschiedene Arten von Aktivitäten ermöglicht.  Das Gerüst enthält 5 Knoten für den Index/mittleren/Ring/kleinen Finger, 4 Joints für das Thumb-Steuerelement und 1 Handgelenk joint.  Das Handgelenk Joint dient als Basis der Hierarchie. Die folgende Abbildung veranschaulicht das Gerüst des Layouts.

![Hand-Gerüst](images/hand-skeleton.png)

In den meisten Fällen wird jede Verbindung mit dem Namen basierend auf Knochenarbeit, die es darstellt.  Da es sich um zwei Bones an jedem Joint, verwenden wir eine Konvention für die Benennung von jeder Verbindung basierend auf den untergeordneten Knochenarbeit an diesem Speicherort aus.  Untergeordnete Knochenarbeit wird als Knochenarbeit das. Handgelenk definiert.  Beispielsweise enthält der "Index nächsten" gemeinsame die Anfangsposition des nächsten Bones Index und die Ausrichtung des, Knochenarbeit.  Es sind nicht die Endposition des Bones enthalten.  Bei Bedarf, die erhalten sie von der nächsten in der Hierarchie, der "Index"Zwischenzertifizierungsstelle"gemeinsame joint Sie.

Zusätzlich zu den 25 hierarchischen Gelenken stellt das System eine Palm-Verbindung.  Legen Sie die gilt in der Regel nicht Teil der skeletal-Struktur.  Es dient nur als eine einfache Möglichkeit, das des Handsymbol des gesamten Position und Ausrichtung zu erhalten.

Die folgende Informationen werden für jede Verbindung bereitgestellt:

| Name | Beschreibung |
|--- |--- |
|Position | 3D-Position von der Verbindung, die in alle angeforderten Koordinatensystem verfügbar. |
|Ausrichtung | 3D-Orientierung des Bones, verfügbar in allen angeforderten Koordinatensystem. |
|Radius | Abstand und die Oberfläche der Skin an der gemeinsamen Position. Ist nützlich für die Optimierung der direkte Interaktionen oder Visualisierungen, die Finger Breite verwenden. |
|Genauigkeit | Stellt einen Hinweis auf eine Falls Ja: wie das System diese gemeinsam mit den Informationen fühlt. |

Sie können die Skelett Hand-Daten über eine Funktion zugreifen, auf die [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).  Die Funktion wird aufgerufen, [TryGetHandPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose), und gibt ein Objekt namens [HandPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose).  Wenn die Quelle angezeigte Hände nicht unterstützt, gibt diese Funktion null zurück.  Nachdem Sie eine HandPose haben, erhalten Sie aktuelle gemeinsame Daten durch den Aufruf [TryGetJoint](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__), durch den Namen des gemeinsamen Sie interessiert sind.  Die Daten werden zurückgegeben, als eine [JointPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.jointpose) Struktur.  Der folgende Code Ruft die Position des Tipps Zeigefinger ab. Die Variable *CurrentState* stellt eine Instanz der [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).

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

### <a name="hand-mesh"></a>Hand-Netz

Die angezeigte manuell nachverfolgen API ermöglicht ein vollständig verformbaren Dreieckgitter zur Hand.  Dieses Mesh kann in Echtzeit zusammen mit der Hand-Gerüst deformieren, und eignet sich für die Visualisierung als auch erweiterte Physik Techniken.  Für den Zugriff auf das Netz Hand, müssen Sie zuerst erstellen eine [HandMeshObserver](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver) Objekt durch Aufrufen von [TryCreateHandMeshObserverAsync](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync) auf die [SpatialInteractionSource](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource).  Dies muss nur einmal pro Quelle, in der Regel beim ersten erfolgen angezeigt.  Das bedeutet, dass es sich bei nennen Sie diese Funktion, um ein HandMeshObserver-Objekt erstellen, wenn eine Seite das Blickfeld erreicht.  Beachten Sie, dass dies eine Async-Funktion ist, müssen für den Umgang mit ein wenig Parallelität hier.  Sobald Sie verfügbar ist, kannst du das HandMeshObserver-Objekt für den Index-Puffer Dreieck durch Aufrufen von [GetTriangleIndices](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___).  Indizes ändern nicht Frame über Frames, damit Sie diese einmal abrufen und Zwischenspeichern für die Lebensdauer der Quelle.  Indizes werden in-wicklungsreihenfolge im Uhrzeigersinn angegeben.

Der folgende Code startet einen getrennten Std:: Thread um den Beobachter Netz zu erstellen und Indexpuffer extrahiert, sobald der Beobachter Mesh verfügbar ist.  Er beginnt mit einer Variablen namens *CurrentState*, dies ist eine Instanz von [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) eine nachverfolgte Hand darstellt.

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
Starten eines getrennten Threads ist nur eine Option für die Verarbeitung von asynchronen Aufrufe.  Alternativ können Sie die neue verwenden [Co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) von unterstützten Funktionen C++"/ WinRT".

Nachdem Sie ein Objekt HandMeshObserver haben, sollten Sie darum für die Dauer halten, die die entsprechenden SpatialInteractionSource aktiv ist.  Klicken Sie dann für jeden Frame, kannst du es für den aktuellen Vertexpuffer, das das Handsymbol durch den Aufruf darstellt [GetVertexStateForPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose) und übergeben Sie einen [HandPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose) -Instanz, der Haltung darstellt, wirklich Vertices, für.  Jeder Scheitelpunkt im Puffer hat eine Position und einer normalen.  Hier ist ein Beispiel für den aktuellen Satz von Vertices für ein Gitter manuell abrufen.  Wie zuvor, die *CurrentState* Variable stellt eine Instanz der [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).

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

Im Gegensatz zu Skelett Gelenken lässt die manuell Mesh-API nicht an einem Koordinatensystem für die Scheitelpunkte.  Stattdessen die [HandMeshVertexState](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshvertexstate) gibt das Koordinatensystem, die die Scheitelpunkte im bereitgestellt werden.  Anschließend können Sie eine Transformation Mesh abrufen, durch den Aufruf [TryGetTransformTo](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_) und Ihre gewünschte Koordinatensystem angeben.  Sie müssen diese Mesh-Transformation zu verwenden, sobald Sie mit den Scheitelpunkten arbeiten.  Dieser Ansatz reduziert die CPU-Auslastung, insbesondere dann, wenn Sie nur das Netz Rendering zu verwenden.

## <a name="gaze-and-commit-composite-gestures"></a>Bestaunen Sie und Committen Sie zusammengesetzte Gesten
Für Anwendungen, verwenden das Eingabemodell Blicke und Commits, insbesondere für HoloLens (der ersten Generation), die räumliche Eingabe-API bietet ein optionales [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) , verwendet werden kann, zusammengesetzte baut auf Gesten aktivieren die 'select' Ereignis.  Durch routing Interaktionen über die SpatialInteractionManager, ggf. ein Hologramm SpatialGestureRecognizer können Ereignisse tippen, halten, Bearbeitung und Navigation gleichmäßig über praktische, Sprach- und räumliche Eingabegeräte, erkennen Sie apps, ohne drückt behandeln zu müssen und manuell frei.

SpatialGestureRecognizer führt nur die minimale Mehrdeutigkeit zwischen den Satz von Aktionen, die Sie anfordern. Z. B., wenn Sie nur tippen anfordern, kann der Benutzer den Finger halten Sie solange wie sie und durch Tippen auf finden weiterhin statt. Wenn Sie anfordern, tippen Sie auf und enthalten Sie, die nach einer Sekunde von der Sie ihren Finger gedrückt halten, die Bewegung zu stehen stuft, und durch Tippen auf nicht mehr ausgeführt wird.

Um SpatialGestureRecognizer verwenden zu können, behandelt der SpatialInteractionManager des [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) Ereignis- und Ziehpunkte, die es auf die SpatialPointerPose verfügbar gemacht. Verwenden für die Überschneidung mit den Hologramme des Benutzers Head Blicke Strahl von diesem Haltung und Oberfläche, die in der Umgebung des Benutzers, um zu bestimmen, was der Benutzer beabsichtigt ist, für die Interaktion mit Gitter. Klicken Sie dann die SpatialInteraction weitergeleitet, in die Ereignisargumente, um das Ziel – Hologramm SpatialGestureRecognizer, mit dessen [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) Methode. Dies startet diese Interaktion nach Interpretation der [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) legen Sie für dieses Erkennungsmodul zum Zeitpunkt der Erstellung – oder durch [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).

Für HoloLens (der ersten Generation), Interaktionen und Gesten sollten im Allgemeinen ableiten, die für die Zielgruppenadressierung von Head Blicke des Benutzers, statt beim Rendern oder an die Hand, die Position direkt interagieren. Nachdem eine Aktivität gestartet wurde, können relative Bewegungen des Zeigers verwendet werden zur Steuerung der Bewegung wie bei der Manipulation oder die Bildschirmnavigation Bewegung.

## <a name="see-also"></a>Siehe auch
* [Haupt- und Eye Blicke in DirectX](gaze-in-directx.md)
* [Direkte Bearbeitung Eingabemodell](direct-manipulation.md)
* [Punkt-und-Commit-Eingabemodell](point-and-commit.md)
* [Blicke und Commit Eingabemodell](gaze-and-commit.md)
* [Motion-Controller](motion-controllers.md)
