---
title: Tutorials zu den ersten Schritten – 2 Initialisieren des Projekts und der ersten Anwendung
description: In diesem Kurs erfahren Sie, wie Sie die Azure-Gesichtserkennung in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: d3392df9bfad5938d71d3a01999be51834a98a5d
ms.sourcegitcommit: 87aca9c2b73b0e83cb70a46443dcdb08c3621005
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "77373446"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Initialisieren des Projekts und der ersten Anwendung

## <a name="overview"></a>Übersicht

<!-- TODO: Consider expanding to include summary of each tutorial in this tutorial series -->
In diesem ersten Tutorial lernen Sie einige der Funktionen kennen, die das <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality-Toolkit (MRTK)</a> bietet, starten Ihre erste Anwendung für das HoloLens 2-Gerät und stellen sie auf dem Gerät bereit.

## <a name="objectives"></a>Ziele

* Konfigurieren von Unity für die HoloLens-Entwicklung
* Importieren von Assets und Einrichten der Szene
* Visualisierung des Gittermodells für die Raumzuordnung, der Hand-Meshes und des Frameratenzählers

## <a name="prerequisites"></a>Voraussetzungen

* Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](install-the-tools.md) ist
* Windows 10 SDK (10.0.18362.0 oder höher)
* Grundlagenkenntnisse in der C#-Programmierung
* Ein für die [Entwicklung konfiguriertes](using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2019.2.X und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform

> [!IMPORTANT]
> Die empfohlene Unity-Version für diese Tutorialreihe ist Unity 2019.2.X. Diese übertrifft alle Versionsanforderungen oder -empfehlungen, die in den oben verlinkten Voraussetzungen angegeben sind.

## <a name="create-new-unity-project"></a>Erstellen eines neuen Unity-Projekts

Starten Sie **Unity Hub**, wählen Sie die Registerkarte **Projects** (Projekte) aus, und klicken Sie auf den **Abwärtspfeil** neben der Schaltfläche **New** (Neu):

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-1.png)

Wählen Sie die Unity-Version aus, die im Abschnitt [Voraussetzungen](#prerequisites) oben angegeben ist:

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-2.png)

Erstellen Sie im Fenster ein neues Projekt:

* Vergewissern Sie sich, dass **Templates** (Vorlagen) auf **3D** festgelegt ist
* Geben Sie einen passenden **Project Name** (Projektnamen) ein, z. B. _MRTK-Tutorials_
* Wählen Sie eine geeignete **Location** (Speicherort) zum Speichern Ihres Projekts, z. B. _D:\MixedRealityLearning_
* Klicken Sie auf die Schaltfläche **Create** (Erstellen), um das neue Unity-Projekt zu erstellen

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-3.png)

> [!CAUTION]
> Wenn Sie unter Windows arbeiten, müssen Sie den MAX_PATH-Grenzwert von 255 Zeichen beachten. Dieser Grenzwert gilt auch für Unity und kann zu Fehlern beim Kompilieren führen, wenn ein Dateipfad länger als 255 Zeichen ist. Daher empfiehlt es sich unbedingt, Ihr Unity-Projekt so nah wie möglich am Stamm des Laufwerks zu speichern.

Warten Sie, bis Unity das Projekt erstellt hat:

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-4.png)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Konfigurieren des Unity-Projekts für Windows Mixed Reality

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

In diesem Abschnitt wechseln Sie die Erstellungsplattform und aktivieren Virtual Reality sowie räumliche Wahrnehmung.

### <a name="1-switch-build-platform"></a>1. Wechseln der Buildplattform

Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-1.png)

Wählen Sie im Build Settings-Fenster **Universal Windows Platform** (Universelle Windows-Plattform) aus, und klicken Sie auf die Schaltfläche **Switch Platform** (Plattform wechseln):

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-2.png)

Warten Sie, bis Unity den Wechsel der Plattform abgeschlossen hat:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-3.png)

Wenn Unity den Plattformwechsel abgeschlossen hat, klicken Sie auf das rote **x**-Symbol, um das Build Settings-Fenster zu schließen:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-4.png)

### <a name="2-enable-virtual-reality"></a>2. Aktivieren von Virtual Reality

> [!NOTE]
> Das Aktivieren von Virtual Reality betrifft auch Mixed Reality- und Augmented Reality-Headsets, da es sich auf das Aktivieren der stereoskopischen Funktionen bezieht, d. h. auf das Rendering unterschiedlicher Bilder für jedes Auge.

Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen...) aus, um das Fenster „Project Settings“ (Projekteinstellungen) zu öffnen:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-1.png)

Wählen Sie im Project Settings-Fenster **Player** > **XR Settings** (Player > XR-Einstellungen) aus, um die XR-Einstellungen zu erweitern:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-2.png)

Aktivieren Sie in den XR-Einstellungen das Kontrollkästchen **Virtual Reality Supported** (Virtual Reality-Unterstützung), um Virtual Reality zu aktivieren, klicken Sie dann auf das **+** -Symbol, und wählen Sie **Windows Mixed Reality** aus, um das Windows Mixed Reality SDK hinzuzufügen:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-3.png)

Warten Sie, bis Unity das SDK hinzugefügt hat:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-4.png)

Wenn Unity das Hinzufügen des SDK abgeschlossen hat, optimieren Sie die XR-Einstellungen wie folgt:

* Legen Sie das **Depth Format** (Tiefenformat) für Windows Mixed Reality auf **16-bit depth** (16-Bit Tiefe) fest
* Aktivieren Sie das Windows Mixed Reality-Kontrollkästchen **Enable Depth Sharing** (Freigeben der Tiefe aktivieren)
* Legen Sie den Stereo-**Rendering Mode\*** (Rendermodus) auf **Single Pass Instanced** (Single-Pass-Instanz) fest

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-5.png)

> [!TIP]
> Weitere Informationen zum Optimieren von Unity für Windows Mixed Reality finden Sie in der Dokumentation [Recommended settings for Unity](recommended-settings-for-unity.md) (Empfohlene Einstellungen für Unity).

### <a name="3-enable-spatial-perception"></a>3. Aktivieren der räumlichen Wahrnehmung

> [!NOTE]
> Die Funktion „Räumliche Wahrnehmung“ ermöglicht das Visualisieren des Gittermodells für die Raumzuordnung auf Windows Mixed Reality-Geräten.

Wählen Sie im Project Settings-Fenster (Projekteinstellungen) **Player** > **Publishing Settings** (Player > Veröffentlichungseinstellungen) aus, um die Veröffentlichungseinstellungen auszuklappen:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-1.png)

Scrollen Sie in den Veröffentlichungseinstellungen abwärts bis zum Abschnitt **Capabilities** (Funktionen), und aktivieren Sie das Kontrollkästchen **SpatialPerception** (Räumliche Wahrnehmung):

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-2.png)

<!-- TODO: Consider adding info about audio spatializer plugin setting -->

Schließen Sie das Project Settings-Fenster.

## <a name="import-textmesh-pro-essential-resources"></a>Importieren von TextMesh Pro Essential Resources

> [!NOTE]
> Wir importieren dieses Paket, da es von den Elementen der Benutzeroberfläche des Mixed Reality Toolkit benötigt wird.

Wählen Sie im Unity-Menü **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Fenster > TextMeshPro > TMP Essential Resources importieren) aus:

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-1.png)

Klicken Sie im Import Unity Package-Fenster (Unity-Paket importieren) auf die Schaltfläche **All** (Alle), um sicherzustellen, dass alle Assets ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Import** (Importieren), um die Assets zu importieren:

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-2.png)

## <a name="import-the-mixed-reality-toolkit"></a>Importieren des Mixed Reality-Toolkits

Laden Sie das benutzerdefinierte Unity-Paket herunter:

* [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.2.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage)

Wählen Sie im Unity-Menü **Assets** > **Import Package** > **Custom Package...** (Assets > Paket importieren > Benutzerdefiniertes Paket...) aus, um das Fenster zum Importieren von Paketen zu öffnen:

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-1.png)

Wählen Sie im Import package...-Fenster (Paket importieren...) das heruntergeladene **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage**-Paket aus, und klicken Sie auf die Schaltfläche **Open** (Öffnen):

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-2.png)

Klicken Sie im Import Unity Package-Fenster (Unity-Paket importieren) auf die Schaltfläche **All** (Alle), um sicherzustellen, dass alle Assets ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Import** (Importieren), um die Assets zu importieren:

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-3.png)

## <a name="configure-the-unity-project-for-the-mixed-reality-toolkit"></a>Konfigurieren des Unity-Projekts für das Mixed Reality-Toolkit

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

Nachdem das Paket importiert wurde, sollte das MRTK Project Configurator-Fenster (MRTK-Projektkonfiguration) angezeigt werden. Wenn das nicht der Fall ist, öffnen Sie es, indem Sie im Unity-Menü **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality-Toolkit > Hilfsprogramme > Unity-Projekt konfigurieren) auswählen.

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-1.png)

Erweitern Sie im MRTK Project Configurator-Fenster den Abschnitt **Modify Configurations** (Konfigurationen ändern), <u>deaktivieren</u> Sie das Kontrollkästchen **Enable MSBuild for Unity** (MSBuild für Unity aktivieren), achten Sie darauf, dass alle anderen Optionen aktiviert sind, und klicken Sie auf die Schaltfläche **Apply** (Übernehmen), um die Einstellungen zu übernehmen:

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-2.png)

> [!CAUTION]
> MSBuild für Unity unterstützt möglicherweise nicht alle verwenden SDKs, und die Deaktivierung nach der erstmaligen Aktivierung kann schwierig sein. Es wird daher dringend empfohlen, MSBuild für Unity nicht zu aktivieren.

## <a name="configure-the-mixed-reality-toolkit"></a>Konfigurieren des Mixed Reality-Toolkits
<!-- TODO: Consider renaming to 'Add the Mixed Reality Toolkit to the Unity scene' -->

Wählen Sie im Unity-Menü **Mixed Reality Toolkit** > **Add to Scene and Configure...** (Mixed Reality-Toolkit > Zu Szene hinzufügen und konfigurieren) aus, um Ihrer aktuellen Szene das Mixed Reality-Toolkit hinzuzufügen:

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-1.png)

Ändern Sie bei im Hierarchiefenster ausgewähltem MixedRealityToolkit-Objekt im Inspektorfenster das Konfigurationsprofil des Mixed Reality-Toolkits in **DefaultHoloLens2ConfigurationProfile**:

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-2.png)

Wählen Sie im Unity-Menü **File** > **Save As...** (Datei > Speichern unter...) aus, um das Save Scene-Fenster (Szene speichern) zu öffnen:

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-3.png)

Navigieren Sie im Save Scene-Fenster zum Ordner **Scenes** (Szenen), geben Sie Ihrer Szene einen passenden Namen, beispielsweise _Getting Started_ (Erste Schritte), und klicken Sie auf die Schaltfläche **Save** (Speichern), um die Szene zu speichern:

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-4.png)

## <a name="build-your-application-to-your-device"></a>Erstellen Ihrer Anwendung auf Ihrem Gerät

### <a name="1-build-the-unity-project"></a>1. Erstellen des Unity-Projekts

Wählen Sie im Unity-Menü **File** > **Build Settings...** (Datei > Buildeinstellungen...) aus, um das Fenster Build Settings (Buildeinstellungen) zu öffnen.

Klicken Sie im Build Settings-Fenster (Buildeinstellungen) auf die Schaltfläche **Add Open Scenes** (Geöffnete Szenen hinzufügen), um der Liste **Scenes In Build** (Szenen im Build) Ihre aktuelle Szene hinzuzufügen, und klicken Sie dann auf die Schaltfläche **Build** (Erstellen), um das Build Universal Windows Platform-Fenster (Erstellen für Universelle Windows-Plattform) zu öffnen:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-1.png)

Wählen Sie im Build Universal Windows Platform-Fenster einen passenden Speicherort aus, um Ihren Build zu speichern, beispielsweise _D:\MixedRealityLearning\Builds_, erstellen Sie einen neuen Ordner mit einem passenden Namen, z. B. _GettingStarted_, und klicken Sie dann auf die Schaltfläche **Select Folder** (Ordner auswählen), um den Buildvorgang zu starten:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-2.png)

Warten Sie, bis Unity den Buildvorgang abgeschlossen hat:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2. Erstellen und Bereitstellen der Anwendung

Wenn der Buildvorgang abgeschlossen ist, fordert Unity den Windows Datei-Explorer auf, den Speicherort zu öffnen, in dem Sie den Build gespeichert haben. Navigieren Sie zum Ordner, und doppelklicken Sie auf die Projektmappendatei, um sie in Visual Studio zu öffnen:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-1.png)

> [!NOTE]
> Wenn Sie von Visual Studio zur Installation neuer Komponenten aufgefordert werden, nehmen Sie sich einen Moment Zeit, um zu überprüfen, ob alle erforderlichen Komponenten (wie in der Dokumentation [Installieren der Tools](install-the-tools.md) angegeben) installiert sind.

Konfigurieren Sie Visual Studio für HoloLens 2, indem Sie die **Master**- oder **Release**-Konfiguration, die **ARM**-Architektur und **Gerät** als Ziel auswählen:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-2.png)

Verbinden Sie Ihre HoloLens 2 mit Ihrem Computer.

> [!IMPORTANT]
> Bevor Sie den Build für Ihr Gerät erstellen, muss das Gerät in den Entwicklermodus versetzt und mit Ihrem Entwicklungscomputer gekoppelt werden. Sie können beide Schritte ausführen, indem Sie [diese Anweisungen](using-visual-studio.md) befolgen.

Der letzte Schritt ist die Erstellung und Bereitstellung auf Ihrem Gerät durch Auswählen von **Debuggen** > **Starten ohne Debuggen**:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-3.png)

Bei diesen Anweisungen wird davon ausgegangen, dass Sie auf einem HoloLens 2-Gerät bereitstellen. Sie können die Bereitstellung aber auch auf dem [HoloLens 2-Emulator](using-the-hololens-emulator.md) vornehmen oder ein [App-Paket für das Querladen](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>) erstellen.

Wenn Sie „Starten ohne Debuggen“ auswählen, wird die Anwendung sofort nach einem erfolgreichen Buildvorgang auf Ihrem Gerät gestartet, ohne dass jedoch der Debugger gestartet und Debuginformationen in Visual Studio angezeigt werden. Dies bedeutet auch, dass Sie das USB-Kabel entfernen können, während Ihre Anwendung auf Ihrem HoloLens 2-Gerät ausgeführt wird, ohne dass die Anwendung beendet wird.

Um die Anwendung auf Ihrem Gerät bereitzustellen, ohne dass sie automatisch gestartet wird, können Sie „Build“ > „Projektmappe bereitstellen“ auswählen.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

<!-- TODO: Consider cleanup and adding in app screenshots -->
Sie haben jetzt Ihre erste HoloLens 2-Anwendung bereitgestellt. Während Sie sich in ihr bewegen, sollten Sie ein Gittermodell für die Raumzuordnung sehen, das alle Oberflächen bedeckt, die von der HoloLens 2 erkannt wurden. Darüber hinaus sollten Sie Indikatoren auf Ihren Händen und Fingern für die Handverfolgung und einen Frameratenzähler zum Überwachen der Anwendungsleistung sehen. Dies sind nur einige der grundlegenden Elemente, die standardmäßig im Mixed Reality-Toolkit enthalten sind. In den folgenden Tutorials fügen Sie Ihrer Szene mehr Inhalte und Interaktivität hinzu, sodass Sie alle Funktionen der HoloLens 2 und des Mixed Reality-Toolkits umfassend erkunden können.

> [!NOTE]
> Möglicherweise fällt Ihnen in der App die Diagnoseprofilerstellung auf. Sie können sie mithilfe des Sprachbefehls **Toogle Diagnostics** (Diagnose ein-/ausschalten) ein- und ausblenden. Es wird jedoch im Allgemeinen empfohlen, die Profilerstellung während der Entwicklung jederzeit sichtbar zu lassen, um sehen zu können, wann sich Änderungen an der App möglicherweise negativ auf die Leistung auswirken. Beispielsweise sollte eine HoloLens 2-Anwendung [durchgängig mit 60 BpS](understanding-performance-for-mixed-reality.md) ausgeführt werden.

[Nächstes Tutorial: 3. Erstellen der Benutzeroberfläche und Konfigurieren des Mixed Reality-Toolkits](mrlearning-base-ch2.md)
