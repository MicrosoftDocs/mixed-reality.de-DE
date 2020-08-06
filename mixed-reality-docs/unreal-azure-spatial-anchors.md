---
title: Azure-Raumanker in Unreal
description: Übersicht über das Erstellen von Azure-Raumankern in der Unreal-Engine.
author: hferrone
services: azure-spatial-anchors
ms.author: v-haferr
ms.date: 07/01/2020
ms.topic: tutorial
ms.service: azure-spatial-anchors
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, Azure, Azure-Entwicklung, Raumanker, Mixed Reality, Entwicklung, Features, neues Projekt, Emulator, Dokumentation, Leitfäden, Hologramme, Spieleentwicklung
ms.openlocfilehash: c7189407bea4b38e7305f0dda7637b82d3325704
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87377283"
---
# <a name="azure-spatial-anchors-in-unreal"></a>Azure-Raumanker in Unreal

## <a name="overview"></a>Übersicht

Azure-Raumanker (Azure Spatial Anchors) sind ein Microsoft Mixed Reality-Dienst, mit dem Augmented Reality-Geräte Ankerpunkte in der physischen Welt ermitteln, teilen und speichern können. Die folgende Dokumentation enthält Anleitungen zum Integrieren des Azure Spatial Anchors-Diensts in ein Unreal-Projekt. Weitere Informationen finden Sie unter [-Dienst](https://azure.microsoft.com/services/spatial-anchors/).

> [!IMPORTANT]
> Lokale Anker werden auf dem Gerät gespeichert, während Azure-Raumanker in der Cloud gespeichert werden. Wenn Sie Ihre Anker lokal auf einem Gerät speichern möchten, verfügen wir über das Dokument [Lokale Raumanker](unreal-spatial-anchors.md), in dem Sie durch den Prozess geführt werden. Beachten Sie, dass Sie sowohl lokale als auch Azure-Anker im selben Projekt haben können, ohne dass Konflikte auftreten.

## <a name="prerequisites"></a>Voraussetzungen

Um diese Anleitung durchzuführen, stellen Sie sicher, dass Folgendes erfüllt ist:

- [Unreal, Version 4.25](https://www.unrealengine.com/get-now) oder höher, ist installiert.
- Eine [HoloLens 2-Projekt](unreal-uxt-ch1.md)einrichtung in Unreal ist vorhanden. 
- Sie haben die [Azure-Raumanker: Übersicht](https://docs.microsoft.com/azure/spatial-anchors/overview) gelesen.
- Grundkenntnisse in C++ und Unreal

## <a name="getting-azure-spatial-anchors-account-info"></a>Abrufen von Azure-Raumanker-Kontoinformationen

Bevor Sie Azure-Raumanker in Ihrem Projekt verwenden können, müssen Sie Folgendes erledigen:
* [Erstellen Sie eine Raumankerressource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource), und kopieren Sie die unten aufgeführten Kontofelder. Diese Werte werden verwendet, um Benutzer mit dem Konto Ihrer Anwendung zu authentifizieren:
    * **Konto-ID**
    * **Kontoschlüssel**

Weitere Informationen finden Sie unter [Azure-Raumanker: Authentifizierung](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp).

> [!NOTE]
> Azure-Raumanker in Unreal 4.25 unterstützen keine Azure AD-Authentifizierungstoken, aber Unterstützung für diese Funktionalität wird in einer späteren Version verfügbar sein.

## <a name="adding-azure-spatial-anchors-plugins"></a>Hinzufügen von Azure-Raumanker-Plug-Ins

Aktivieren Sie die Azure-Raumanker-Plug-Ins im Unreal-Editor wie folgt:
1. Klicken Sie auf **Bearbeiten > Plug-Ins**, und suchen Sie nach **AzureSpatialAnchors** sowie **AzureSpatialAnchorsForWMR**.
2. Aktivieren Sie das Kontrollkästchen **Aktiviert** für beide Plug-Ins, um den Zugriff auf die Azure-Raumanker-Blaupausenbibliotheken in Ihrer Anwendung zuzulassen.

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-01.png)

Starten Sie anschließend den Unreal-Editor neu, damit die Plug-In-Änderungen wirksam werden. Das Projekt ist jetzt für die Verwendung von Azure-Raumankern bereit.

## <a name="starting-a-spatial-anchors-session"></a>Starten einer Raumankersitzung
Eine Azure-Raumankersitzung ermöglicht Clientanwendungen die Kommunikation mit dem Azure Spatial Anchors-Dienst. Sie müssen eine Azure Spatial Anchors-Sitzung erstellen und starten, um Azure-Raumanker zu erstellen, zu speichern und zu teilen:

1. Öffnen Sie die Blaupause für den „Pawn“ (Bauer), den Sie in der Anwendung verwenden.
2. Fügen Sie zwei Zeichenfolgenvariablen für die **Konto-ID** und den **Kontoschlüssel** hinzu, und weisen Sie dann die entsprechenden Werte aus Ihrem Azure Spatial Anchors-Konto zu, um die Sitzung zu authentifizieren.

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-02.png)

Starten Sie eine Azure Spatial Anchors-Sitzung wie folgt:
1. Überprüfen Sie, ob eine **AR-Sitzung** in der HoloLens-Anwendung ausgeführt wird, da die Azure Spatial Anchors-Sitzung erst gestartet werden kann, wenn eine AR-Sitzung ausgeführt wird. Wenn Sie keine eingerichtet haben, [erstellen Sie eine AR-Sitzungsressource](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).
2. Fügen Sie das benutzerdefinierte Ereignis **-Sitzung starten** hinzu, und konfigurieren Sie es, wie im folgenden Screenshot gezeigt.
    * Beim Erstellen einer Sitzung wird die Sitzung nicht standardmäßig gestartet, sodass der Entwickler die Sitzung für die Authentifizierung beim Azure Spatial Anchors-Dienst konfigurieren kann.

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-03.png)

3. Konfigurieren Sie die Azure Spatial Anchors-Sitzung so, dass sie die **Konto-ID** und den **Kontoschlüssel** angibt.

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-04.png)

4. Starten Sie die Azure Spatial Anchors-Sitzung, was es der Anwendung ermöglicht, lokale Azure-Raumanker zu erstellen und aufzufinden.

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-05.png)

Es hat sich bewährt, die Azure-Raumankerressourcen in Ihrer Ereignisdiagramm-Blaupause zu bereinigen, wenn Sie den Dienst nicht mehr verwenden:

1. Beenden Sie die Azure Spatial Anchors-Sitzung. Die Sitzung wird nicht mehr ausgeführt, aber die zugehörigen Ressourcen sind weiterhin im Azure-Raumanker-Plug-In vorhanden.

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-06.png)

2. Zerstören Sie die Azure Spatial Anchors-Sitzung, um alle Azure Spatial Anchors-Sitzungsressourcen zu bereinigen, die im Azure-Raumanker-Plug-In noch bekannt sind.

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-07.png)

Ihre Ereignisdiagramm-Blaupause sollte wie im folgenden Screenshot aussehen:

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-08.png)


## <a name="creating-an-anchor"></a>Erstellen eines Ankers
Ein Azure-Raumanker stellt eine physische Weltpose im Augmented Reality-Anwendungsraum dar, der Augmented Reality-Inhalte an Orte in der physischen Welt bindet. Azure-Raumanker können auch von verschiedenen Benutzern gemeinsam genutzt werden. Dieses Teilen ermöglicht es, dass Augmented Reality-Inhalte, die auf verschiedenen Geräten gezeichnet werden, am selben Ort in der physischen Welt positioniert werden können. 

So erstellen Sie einen neuen Azure-Raumanker
1. Überprüfen Sie, ob eine Azure Spatial Anchors-Sitzung ausgeführt wird. Die Anwendung kann einen Azure-Raumanker nur erstellen oder speichern, wenn eine Azure Spatial Anchors-Sitzung ausgeführt wird.

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-09.png)

2. Erstellen Sie eine Unreal- **[Szenenkomponente](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** , oder rufen Sie eine ab, deren Ort gespeichert werden sollte. 
    * Im folgenden Bild wird die Komponente **Szenenkomponente, die einen Anker benötigt** als Variable verwendet. Eine Unreal-Szenenkomponente ist erforderlich, um eine Anwendungswelttransformation für ein [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) und einen Azure-Raumanker einzurichten.

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-10.png)

So erstellen und speichern Sie einen Azure-Raumanker für eine Unreal-Szenenkomponente
1. Rufen Sie die [Pin-Komponente](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) für die Unreal-Szenenkomponente auf, und geben Sie die **Welttransformation** der Szenenkomponente als die Welttransformation an, die für den AR Pin verwendet wird.
    * Unreal verfolgt AR-Punkte im Anwendungsraum mithilfe von AR Pins, die zum Erstellen eines Azure-Raumankers verwendet werden. In Unreal entspricht ein AR Pin analog einem SpatialAnchor (Raumanker) auf HoloLens.

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-11.png)

2. Rufen Sie mithilfe des neu erstellten AR Pins **Cloudanker erstellen** auf.
    * „Cloudanker erstellen“ erstellt lokal einen Azure-Raumanker, aber nicht im Azure-Raumankerdienst. Parameter für den Azure-Raumanker, z. B. ein Ablaufdatum, können festgelegt werden, bevor der Azure-Raumanker mit dem Dienst erstellt wird.

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-12.png)

3. Legen Sie den Ablauf des Azure-Raumankers fest. Der Parameter „Lifetime“ (Lebensdauer) dieser Funktion ermöglicht es dem Entwickler, in Sekunden anzugeben, wie lange der Anker vom Dienst erhalten werden soll.
    * Eine Ablaufzeit von einer Woche würde beispielsweise einen Wert von 60 Sekunden × 60 Minuten x 24 Stunden x 7 Tage = 604.800 Sekunden erfordern.

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-13.png)

Nachdem Sie Ankerparameter festgelegt haben, deklarieren Sie den Anker als zum Speichern bereit. Im folgenden Beispiel wird der neu erstellte Azure-Raumanker zu einem Satz von Azure-Raumankern hinzugefügt, die gespeichert werden müssen. Dieser Satz wird als Variable für die Pawn-Blaupause deklariert.

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-14.png)

## <a name="saving-an-anchor"></a>Speichern eines Ankers

Nachdem Sie den Azure-Raumanker mit Ihren Parametern konfiguriert haben, rufen Sie **Cloudanker speichern** auf. „Cloudanker speichern“ deklariert den Anker im Azure Spatial Anchors-Dienst. Wenn der Aufruf von „Cloudanker speichern“ erfolgreich ist, steht der Azure-Raumanker anderen Benutzern des Azure Spatial Anchors-Diensts zur Verfügung.  

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-15.png)

> [!NOTE]
> „Cloudanker speichern“ ist eine asynchrone Funktion und kann nur für ein Spielthreadereignis wie **EventTick** aufgerufen werden. „Cloudanker speichern“ wird in benutzerdefinierten Blaupausenfunktionen möglicherweise nicht als verfügbare Blaupausenfunktion angezeigt. Es sollte jedoch im Blaupausen-Editor für das Pawn-Ereignisdiagramm verfügbar sein.

Im folgenden Beispiel wird der Azure-Raumanker während eines Eingabeereignisrückrufs in einem Satz gespeichert. Der Anker wird dann im EventTick gespeichert. Es kann mehrere Versuche benötigen, um einen Azure-Raumanker zu speichern, je nach der Menge von Raumdaten, die Ihre Azure Spatial Anchors-Sitzung erstellt hat. Aus diesem Grund empfiehlt es sich, zu überprüfen, ob der Speichernaufruf erfolgreich war.

Wenn der Anker nicht gespeichert wird, fügen Sie ihn erneut dem Satz von Ankern hinzu, die noch gespeichert werden müssen. Zukünftige EventTicks versuchen, den Anker zu speichern, bis er erfolgreich im Azure Spatial Anchors-Dienst gespeichert wird.

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-16.png)

Nachdem der Anker gespeichert wurde, können Sie die Transformation des AR Pins als Verweistransformation verwenden, um Inhalt in der Anwendung abzulegen. Andere Benutzer können diesen Anker erkennen und AR-Inhalt für verschiedene Geräte in der physischen Welt ausrichten.

## <a name="deleting-an-anchor"></a>Löschen eines Ankers

Sie können Anker aus dem Azure Spatial Anchors-Dienst löschen, indem Sie **Cloudanker löschen** aufrufen.

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-17.png)

> [!NOTE]
> „Cloudanker löschen“ ist eine latente Funktion und kann nur für ein Spielthreadereignis wie „EventTick“ aufgerufen werden. „Cloudanker löschen“ wird in benutzerdefinierten Blaupausenfunktionen möglicherweise nicht als verfügbare Blaupausenfunktion angezeigt. Es sollte jedoch im Blaupausen-Editor für das Pawn-Ereignisdiagramm verfügbar sein.

Im folgenden Beispiel ist der Anker für das Löschen in einem benutzerdefinierten Eingabeereignis gekennzeichnet. Der Löschvorgang wird dann bei EventTick versucht. Wenn das Löschen des Ankers fehlschlägt, fügen Sie den Azure-Raumanker dem Satz von Ankern hinzu, die zum Löschen gekennzeichnet sind, und versuchen Sie es noch mal mit späteren EventTicks.

Ihre Ereignisdiagramm-Blaupause sollte jetzt wie im folgenden Screenshot aussehen:

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-18.png)


## <a name="locating-pre-existing-anchors"></a>Auffinden bereits vorhandener Anker

Zusätzlich zum Erstellen von Azure-Raumankern können Sie mit dem Azure Spatial Anchors-Dienst von Peers erstellte Anker erkennen:

1. Rufen Sie einen Azure-Raumankerbezeichner für den Anker ab, den Sie erkennen möchten.
    * Ein Ankerbezeichner kann für einen Anker abgerufen werden, der von demselben Gerät in einer früheren Azure Spatial Anchors-Sitzung erstellt wurde. Er kann außerdem von Peergeräten erstellt und geteilt werden, die mit dem Azure Spatial Anchors-Dienst interagieren.

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-24.png)

2. Fügen Sie Ihrer Pawn-Blaupause eine **AzureSpatialAnchorsEvent**-Komponente hinzu.
    * Mit dieser Komponente können Sie verschiedene Azure-Raumankerereignisse abonnieren, z. B. Ereignisse, die aufgerufen werden, wenn Azure-Raumanker aufgefunden werden.

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-19.png)

3. Abonnieren Sie den **Delegaten für gefundene ASAAnchor** für die **AzureSpatialAnchorsEvent**-Komponente.
    * Der Delegat teilt der Anwendung mit, wenn neue Anker gefunden wurden, die dem Azure Spatial Anchors-Konto zugeordnet sind.
    * Mit dem Ereignisrückruf werden für Azure-Raumanker, die von Peers mit der Azure Spatial Anchors-Sitzung erstellt wurden, standardmäßig keine AR Pins erstellt. Um einen AR Pin für den erkannten Azure-Raumanker zu erstellen, können Entwickler **ARPin um Azure Cloud-Raumanker erstellen** aufrufen.

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-20.png)

Zum Auffinden von Azure-Raumankern, die von Peers mithilfe des Azure Spatial Anchors-Diensts Dienstanbieter erstellt wurden, muss die Anwendung einen **Azure-Raumanker-Watcher** erstellen:
1. Überprüfen Sie, ob eine Azure Spatial Anchors-Sitzung ausgeführt wird.
2. Erstellen Sie ein **AzureSpatialAnchorsLocateCriteria**.
    * Sie können verschiedene Standortparameter angeben, z. B. die Entfernung vom Benutzer oder die Entfernung von einem anderen Anker.
3. Declare Sie Ihren gewünschten Azure-Raumankerbezeichner im **AzureSpatialAnchorsLocateCritieria**.
4. Rufen Sie **Watcher erstellen** auf.

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-21.png)

Die Anwendung beginnt nun, nach Azure-Raumankern zu suchen, die dem Azure Spatial Anchors-Dienst bekannt sind, was bedeutet, dass Benutzer von Peers erstellte Azure-Raumanker auffinden können.

Nachdem Sie den Azure-Raumanker gefunden haben, rufen Sie **Watcher beenden** auf, um den Azure-Raumanker-Watcher zu beenden und Watcherressourcen zu bereinigen.

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-22.png)

Ihre endgültige Ereignisdiagramm-Blaupause sollte jetzt wie im folgenden Screenshot aussehen:

![Raumanker-Plug-Ins](images/asa-unreal/unreal-spatial-anchors-img-23.png)


## <a name="next-steps"></a>Nächste Schritte
* [Lokale Raumanker](unreal-spatial-anchors.md)
* [Raumanker-Dokumentation](https://docs.microsoft.com/azure/spatial-anchors/)
* [Raumankerfunktionen](https://azure.microsoft.com/services/spatial-anchors/#features)
* [Richtlinien für eine effektive Ankererfahrung](https://docs.microsoft.com/azure/spatial-anchors/concepts/guidelines-effective-anchor-experiences)