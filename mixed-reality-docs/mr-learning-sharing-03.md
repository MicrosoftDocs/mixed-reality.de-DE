---
title: 'Tutorials zu Mehrbenutzerfunktionen: 3 Verbinden mehrerer Benutzer'
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie freigegebene Mehrbenutzerumgebungen innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 5937b581e92ffc5a13b55574ffd8a0ca7c4bca40
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376392"
---
# <a name="3-connecting-multiple-users"></a>3. Verbinden mehrerer Benutzer

In diesem Tutorial lernen Sie, wie Sie mehrere Benutzer im Rahmen einer freigegebenen Live-Benutzererfahrung verbinden. Am Ende des Tutorials können Sie die App auf mehreren Geräten ausführen, und jedem Benutzer wird der bewegte Avatar anderer Benutzer in Echtzeit angezeigt.

## <a name="objectives"></a>Ziele

* Erlernen des Verbindens mehrerer Benutzer in einer freigegebenen Umgebung

## <a name="preparing-the-scene"></a>Vorbereiten der Szene

In diesem Abschnitt bereiten Sie die Szene vor, indem Sie einige der Tutorial-Prefabs hinzufügen.

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs**, klicken Sie auf die folgenden Prefabs, und ziehen Sie sie dann in das Hierarchiefenster, um sie Ihrer Szene hinzuzufügen:

* **NetworkLobby**-Prefab
* **SharedPlayground**-Prefab

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs**, klicken Sie auf das folgende Prefab, und ziehen Sie es in das Hierarchiefenster, um es Ihrer Szene hinzuzufügen:

* **DebugWindow**-Prefab

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a>Erstellen des Benutzerprefabs

In diesem Abschnitt erstellen Sie ein Prefab, das verwendet wird, um auf der freigegebenen Benutzeroberfläche die Benutzer darzustellen.

### <a name="1-create-and-configure-the-user"></a>1. Erstellen und Konfigurieren des Benutzers

Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf einen leeren Bereich, wählen Sie **Create Empty** (Leer erstellen) aus, um Ihrer Szene ein leeres Objekt hinzuzufügen, benennen Sie das Objekt **PhotonUser**, und konfigurieren Sie es folgendermaßen:

* Vergewissern Sie sich, dass die **Transformationsposition** auf X = 0, Y = 0, Z = 0 festgelegt ist:

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-1.png)

Wählen Sie im Hierarchiefenster das **PhotonUser**-Objekt aus, und verwenden Sie dann im Inspektor-Fenster die Schaltfläche **Add Component** (Komponente hinzufügen), um dem PhotonUser-Objekt die Komponente **Photon User (Script)** hinzuzufügen:

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-2.png)

Verwenden Sie im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um dem PhotonUser-Objekt die Komponente **Generic Net Sync (Script)** hinzuzufügen, und konfigurieren Sie sie wie folgt:

* Aktivieren Sie das Kontrollkästchen **Is User** (Ist Benutzer)

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-3.png)

Verwenden Sie im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um dem PhotonUser-Objekt die Komponente **Photon View (Script)** hinzuzufügen, und konfigurieren Sie sie wie folgt:

* Weisen Sie die Komponente **Generic Net Sync (Script)** dem Feld **Observed Components** (Beobachtete Komponenten) zu.

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-4.png)

### <a name="2-create-the-avatar"></a>2. Erstellen des Avatars

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Materials**, um nach den MRTK-Materialien zu suchen.

Klicken Sie dann im Hierarchiefenster mit der rechten Maustaste auf das **PhotonUser**-Objekt, wählen Sie **3D Object** > **Sphere** (3D-Objekt > Kugel) aus, um ein Kugelobjekt als untergeordnetes Objekt des PhotonUser-Objekts zu erstellen, und konfigurieren Sie es folgendermaßen:

* Vergewissern Sie sich, dass die **Transformationsposition** auf X = 0, Y = 0, Z = 0 festgelegt ist
* Ändern Sie den **Transformationsmaßstab** auf eine passende Größe beispielsweise X = 0,15, Y = 0,15, Z = 0,15
* Weisen Sie dem Feld „MeshRenderer > Materials > **Element 0**“ das Material **MRTK_Standard_White** zu.

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step2-1.png)

### <a name="3-create-the-prefab"></a>3. Erstellen der Prefab

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources**:

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-1.png)

**Klicken und ziehen** Sie bei noch ausgewähltem Ordner „Resources“ das **PhotonUser**-Objekt aus dem Hierarchiefenster in den **Resources**-Ordner, um aus dem PhotonUser-Objekt ein Prefab zu machen:

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-2.png)

Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf das **PhotonUser**-Objekt, und wählen Sie **Löschen** aus, um es aus der Szene zu entfernen:

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a>Konfigurieren von PUN zum Instanziieren des Benutzerprefabs

In diesem Abschnitt konfigurieren Sie das Projekt für die Verwendung des PhotonUser-Prefabs, das Sie im vorherigen Abschnitt erstellt haben.

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources**.

Klappen Sie im Hierarchiefenster das **NetworkLobby**-Objekt auf, wählen Sie das untergeordnete Objekt **NetworkRoom** aus, und suchen Sie dann im Inspektorfenster die Komponente **Photon Room (Script)** , um sie wie folgt zu konfigurieren:

* Weisen Sie das **PhotonUser**-Prefab aus dem Ordner „Resources“ dem **Photon User Prefab**-Feld zu

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a>Ausprobieren der Benutzeroberfläche mit mehreren Benutzern

Wenn Sie das Unity-Projekt jetzt für Ihr HoloLens-Gerät erstellen und bereitstellen und zurück in Unity in den Spielmodus wechseln, während die App auf Ihrem HoloLens-Gerät ausgeführt wird, sehen Sie, wie sich der HoloLens-Benutzeravatar bewegt, wenn Sie Ihren Kopf (HoloLens) bewegen:

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer App auf dem HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

> [!CAUTION]
> Die App muss eine Verbindung mit Photon herstellen, achten Sie also darauf, dass Ihr Computer/Gerät mit dem Internet verbunden ist.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben Ihr Projekt erfolgreich so konfiguriert, dass es mehreren Benutzern ermöglicht, Verbindungen mit der gleichen Benutzeroberfläche herzustellen und die Bewegungen der anderen Teilnehmer zu sehen. Im nächsten Tutorial implementieren Sie die Funktionalität zum Teilen der Bewegungen von Objekten unter mehreren Geräten.

[Nächstes Tutorial: 4. Freigeben von Objektbewegungen für mehrere Benutzer](mr-learning-sharing-04.md)
