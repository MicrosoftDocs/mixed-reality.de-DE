---
title: Räumliche Audiowiedergabe in Unreal
description: Übersicht zum Plug-In für räumliche Audiowiedergabe für die Unreal Engine.
author: hferrone
ms.author: v-haferr
ms.date: 06/15/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Streaming, Remoting, Mixed Reality, Entwicklung, erste Schritte, Features, neues Projekt, Emulator, Dokumentation, Leitfäden, Features, Hologramme, Spieleentwicklung
ms.openlocfilehash: 404aaec7b618e951ad69c02e7aaef80e42d31dbd
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85446797"
---
# <a name="spatial-audio-in-unreal"></a>Räumliche Audiowiedergabe in Unreal

## <a name="overview"></a>Übersicht

Anders als beim Sehen hören Menschen 360-Grad-Surroundsound. Räumliche Audiowiedergabe emuliert die Funktionsweise des menschlichen Hörens und stellt die Hinweise bereit, die zum Erkennen von Klangpositionen im Raum erforderlich sind. Wenn Sie Ihren Mixed Reality-Anwendungen räumliche Audiowiedergabe hinzufügen, steigern Sie den Grad des Eintauchens, das Ihre Benutzer erleben.  

Die erforderliche Verarbeitung für räumliche Audiowiedergabe in hoher Qualität ist komplex, daher besitzt HoloLens 2 dedizierte Hardware für die Verarbeitung dieser Klangobjekte.  Damit Sie auf diese Hardwareunterstützung bei der Verarbeitung zugreifen können, müssen Sie das **MicrosoftSpatialSound**-Plug-In in Ihrem Unreal-Projekt installieren. Dieser Artikel führt Sie durch die Installation und Konfiguration des Plug-Ins und weist Sie auf ausführlichere Ressourcen für die Verwendung von räumlicher Audiowiedergabe in der Unreal-Engine hin. 

## <a name="installing-the-microsoft-spatial-sound-plugin"></a>Installieren des Microsoft Spatial Sound-Plug-Ins 

Der erste Schritt beim Hinzufügen von Raumklang zu Ihrem Projekt ist die Installation des Microsoft Spatial Sound-Plug-Ins, das Sie hier finden können: 

1. Klicken Sie auf **Bearbeiten > Plug-Ins**, und suchen Sie im Suchfeld nach **MicrosoftSpatialSound**. 
2. Aktivieren Sie das Kontrollkästchen **Aktiviert** im **MicrosoftSpatialSound**-Plug-In. 
3. Starten Sie auf der Plug-Ins-Seite den Unreal Editor neu, indem Sie **Jetzt neu starten** auswählen. 

> [!NOTE]
> Wenn dies noch nicht geschehen ist, müssen Sie die Plug-Ins **Microsoft Windows Mixed Reality** und **HoloLens** installieren, indem Sie die Anweisungen im Abschnitt **[Initialisieren des Projekts](unreal-uxt-ch2.md)** unserer Reihe mit Unreal-Tutorials befolgen.

![Unreal Spatial Audio-Plug-In](images/unreal-spatial-audio-img-01.png)

Nach dem Neustart des Editors ist Ihr Projekt fertig eingerichtet.


## <a name="setting-the-spatialization-plugin-for-hololens-2-platform"></a>Festlegen des Raumklang-Plug-Ins für die HoloLens 2-Plattform
Die Konfiguration des Raumklang-Plug-Ins erfolgt auf Plattformbasis.  Sie können das Microsoft Spatial Sound-Plug-In für HoloLens 2 in folgender Weise aktivieren:
1. Wählen Sie **Bearbeiten > Projekteinstellungen**aus, scrollen Sie zu **Plattformen**, und klicken Sie auf **HoloLens**.
2. Erweitern Sie die **Audio**-Eigenschaften, und legen Sie das Feld **Spatialization Plugin** (Raumklang-Plug-In) auf **Microsoft Spatial Sound** fest.

![Raumklang-Plug-In für die HoloLens-Plattform](images/unreal-spatial-audio-img-02.png)

Wenn Sie die Vorschau Ihrer Anwendung im Unreal-Editor auf einem Desktop-PC ausführen möchten, müssen Sie die Schritte oben für die **Windows**-Plattform wiederholen:

![Raumklang-Plug-In für die Windows-Plattform](images/unreal-spatial-audio-img-05.png)

## <a name="enabling-spatial-audio-on-your-workstation"></a>Aktivieren von räumlicher Audiowiedergabe auf Ihrer Arbeitsstation
Die räumliche Audiowiedergabe ist in Desktopversionen von Windows standardmäßig deaktiviert. Sie können sie wie folgt aktivieren:
* Klicken Sie mit der rechten Maustaste auf das **Lautstärke**-Symbol in der Taskleiste. 
    + Wählen Sie **Raumklang -> Windows Sonic für Kopfhörer** aus, um die beste Darstellung des Höreindrucks mit HoloLens 2 zu erreichen.

![Raumklang-Plug-In](images/unreal-spatial-audio-img-04.png)

> [!NOTE]
>Diese Einstellung ist nur erforderlich, wenn Sie beabsichtigen, das Projekt im Unreal-Editor zu testen.

## <a name="creating-attenuation-objects"></a>Erstellen von Dämpfungsobjekten
Nachdem Sie die erforderlichen Plug-Ins installiert und konfiguriert haben:
1. Suchen Sie nach einem Akteur **Ambient Sound** (Raumklang) im Fenster **Place Actors** (Akteure platzieren), und ziehen Sie ihn auf das **Szenenfenster**.

![Hinzufügen des Raumklang-Akteurs](images/unreal-spatial-audio-img-07.png)

2. Machen Sie den Akteur **Ambient Sound** (Raumklang) zu einem untergeordneten Element eines visuellen Elements in Ihrer Szene. 
    * Ein Raumklang-Akteur hat standardmäßig keine visuelle Darstellung, Sie hören also lediglich einen Klang von seiner Position in der Szene. Wenn Sie den Akteur an ein visuelles Element anfügen, können Sie ihn sehen und wie jedes andere Medienobjekt verschieben.

3.  Klicken Sie mit der rechen Maustaste auf den **Inhalts-Browser**, und wählen Sie **Create Advanced Asset -> Sounds -> Sound Attenuation** (Erweitertes Medienobjekt erstellen > Sounds > Klangdämpfung) aus:

![Erstellen eines Klangdämpfungs-Medienobjekts](images/unreal-spatial-audio-img-06.png)

4. Klicken Sie mit der rechten Maustaste auf das Medienobjekt **Sound Attenuation** (Klangdämpfung) im Fenster des **Inhalt-Browsers**, und wählen Sie die Option **Bearbeiten** aus, um das Eigenschaftenfenster anzuzeigen.
    * Ändern Sie die **Spatialization Method** (Raumklangverfahren) in **Binaural**.

![Festlegen des Raumklangverfahrens](images/unreal-spatial-audio-img-03.png)

5. Wählen Sie den Akteur **Ambient Sound** (Raumklang) aus, und scrollen Sie nach unten zum Abschnitt **Attenuation** (Dämpfung) im Bereich **Details**. 
    * Legen Sie die Einstellung **Attenuation Settings** (Dämpfungseinstellungen) auf das von Ihnen erstellte Medienobjekt **Sound Attenuation** (Klangdämpfung) fest.

![Festlegen der Dämpfungseinstellung](images/unreal-spatial-audio-img-08.png)

6. Legen Sie das **Klangmedienobjekt** fest, das Sie an den Raumklang-Akteur anfügen möchten, indem Sie die Eigenschaft **Sound** des Raumklang-Akteurs auf die zu verwendende SoundAsset-Datei festlegen.

![Festlegen des Klangmedienobjekts](images/unreal-spatial-audio-img-09.png)

> [!NOTE] 
> Die SoundAsset-Datei muss in Mono vorliegen, um mithilfe des Microsoft Spatial Sound-Plug-Ins mit Rauminformationen versehen zu werden. Sie können die Eigenschaften der Sounddatei anzeigen, indem Sie den Mauszeiger im Fenster des Inhalt-Browsers auf dem Medienobjekt ruhen lassen, wie im Screenshot unten dargestellt.

![Neues Klangdämpfungs-Medienobjekt](images/unreal-spatial-audio-img-10.png)

Nachdem all dies konfiguriert wurde, kann der Raumklang mithilfe der dedizierten Hardware-Abladungsunterstützung in HoloLens 2 mit Rauminformationen versehen werden.

## <a name="configuring-objects-for-spatialization"></a>Konfigurieren von Objekten für die räumliche Wiedergabe
Das Arbeiten mit Raumklang bedeutet, dass Sie dafür zuständig sind, wie sich der Klang in einer virtuellen Umgebung verhält. Der Hauptschwerpunkt liegt auf dem Erstellen von Klangobjekten, die lauter erscheinen, wenn der Benutzer sich in der Nähe befindet, und leiser, wenn der Benutzer weit weg ist. Dies wird als Klangdämpfung bezeichnet und erzeugt den Eindruck, als ob Klänge an einem festen Ort positioniert wären.

Alle Dämpfungsobjekte umfassen konfigurierbare Einstellungen für:
* Abstand
* Raumklang
* Luftabsorption
* Listenerfokus
* Nachhall-Send
* Okklusion

[Klangdämpfung in Unreal](https://docs.unrealengine.com/Engine/Audio/DistanceModelAttenuation/index.html) bietet zu jedem dieser Themen Details und spezifische Eigenheiten der Implementierung.


## <a name="see-also"></a>Siehe auch
* [Raumklang](https://docs.microsoft.com/windows/mixed-reality/spatial-sound)
* [Raumklangentwurf](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design)
* [MR räumlich 220: Raumklang](https://docs.microsoft.com/windows/mixed-reality/holograms-220)