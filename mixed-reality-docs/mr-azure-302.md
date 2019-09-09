---
title: Mr und Azure 302-Maschinelles Sehen
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie visuelle Inhalte in einem bereitgestellten Image mithilfe von Azure Maschinelles sehen in einer Mixed Reality-Anwendung erkennen.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Maschinelles sehen, hololens, immersive, VR
ms.openlocfilehash: 9cc526afdc36b8056afd61948fea5cf98015bb35
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047195"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.

<br>

# <a name="mr-and-azure-302-computer-vision"></a>Mr und Azure 302: Maschinelles Sehen

In diesem Kurs erfahren Sie, wie Sie visuelle Inhalte in einem bereitgestellten Image erkennen können, indem Sie die Funktionen von Azure Maschinelles sehen in einer Mixed Reality-Anwendung verwenden.

Erkennungsergebnisse werden als beschreibende Tags angezeigt. Sie können diesen Dienst verwenden, ohne ein Machine Learning-Modell trainieren zu müssen. Wenn für Ihre Implementierung ein Machine Learning-Modell trainiert werden muss, finden Sie weitere Informationen unter [Mr und Azure 302b](mr-azure-302b.md).

![Lab-Ergebnis](images/AzureLabs-Lab2-000.png)

Die Microsoft-Maschinelles sehen ist ein Satz von APIs, die Entwicklern die Bildverarbeitung und-Analyse (mit Rückgabe Informationen) zur Verfügung stellen, indem Sie erweiterte Algorithmen verwenden, die alle über die Cloud verfügen. Entwickler laden eine Bild-oder Bild-URL hoch, und die Microsoft Maschinelles Sehen-API-Algorithmen analysieren den visuellen Inhalt basierend auf den Eingaben, die der Benutzer ausgewählt hat. er kann dann Informationen zurückgeben, einschließlich, den Typ und die Qualität eines Bilds ermitteln und menschliche Gesichter erkennen. zurückgeben ihrer Koordinaten), Tagging oder Kategorisieren von Bildern. Weitere Informationen finden Sie auf der [Seite Azure Maschinelles Sehen-API](https://azure.microsoft.com/services/cognitive-services/computer-vision/).

Nachdem Sie diesen Kurs abgeschlossen haben, verfügen Sie über eine Mixed Reality hololens-Anwendung, die Folgendes ausführen kann:

1.  Mithilfe der TAP-Geste wird ein Bild von der Kamera der hololens aufgezeichnet.
2.  Das Image wird an den Azure Maschinelles Sehen-API-Dienst gesendet. 
3.  Die erkannten Objekte werden in einer einfachen Benutzeroberflächen Gruppe aufgelistet, die in der Unity-Szene positioniert ist.

In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren. In diesem Kurs erfahren Sie, wie Sie einen Azure-Dienst in Ihr Unity-Projekt integrieren. Es ist Ihre Aufgabe, das wissen, das Sie aus diesem Kursgewinnen, zu nutzen, um ihre gemischte Reality-Anwendung zu verbessern.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> Mr und Azure 302: Maschinelles Sehen</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Dieser Kurs konzentriert sich in erster Linie auf hololens, aber Sie können auch das Erlernen, was Sie in diesem Kurs lernen, auf Windows Mixed Reality-(VR)-Headsets. Da immersive Headsets (VR) nicht über barrierefreie Kameras verfügen, benötigen Sie eine externe Kamera, die mit Ihrem PC verbunden ist. Wenn Sie den Kurs befolgen, finden Sie Hinweise zu allen Änderungen, die Sie möglicherweise für die Unterstützung von immersiven (VR)-Headsets verwenden müssen.

## <a name="prerequisites"></a>Erforderliche Komponenten

> [!NOTE]
> Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen. Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Mai 2018). Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](install-the-tools.md) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt sind.

Für diesen Kurs empfehlen wir die folgende Hardware und Software:

- Einen Entwicklungs-PC, der [mit der Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for Immersive (VR)-Headset-Entwicklung kompatibel ist
- [Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus](install-the-tools.md#installation-checklist)
- [Das neueste Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Ein [Windows Mixed Reality-Headset (VR)](immersive-headset-hardware-details.md) oder [Microsoft hololens](hololens-hardware-details.md) mit aktiviertem Entwicklermodus
- Eine Kamera, die mit Ihrem PC verbunden ist (für die immersive Headset-Entwicklung)
- Internet Zugriff für Azure-Setup und Maschinelles Sehen-API-Abruf

## <a name="before-you-start"></a>Bevor Sie beginnen

1.  Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).
2.  Richten Sie Ihre hololens ein, und testen Sie Sie. Wenn Sie Unterstützung für die Einrichtung ihrer hololens benötigen, [besuchen Sie den Artikel zum Einrichten von hololens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Es empfiehlt sich, eine Kalibrierung und Sensor Optimierung durchzuführen, wenn Sie mit der Entwicklung einer neuen hololens-App beginnen (manchmal kann es hilfreich sein, diese Aufgaben für jeden Benutzer auszuführen). 

Hilfe zur Kalibrierung finden Sie unter diesem [Link zum Artikel zur hololens-Kalibrierung](calibration.md#hololens-2).

Hilfe zur Sensor Optimierung finden Sie unter diesem [Link zum Artikel zur Überwachung von hololens-Sensoren](sensor-tuning.md).

## <a name="chapter-1--the-azure-portal"></a>Kapitel 1 – Azure-Portal

Wenn Sie den *Maschinelles Sehen-API* -Dienst in Azure verwenden möchten, müssen Sie eine Instanz des-Dienstanbieter konfigurieren, die für die Anwendung verfügbar gemacht wird.

1.  Melden Sie sich zunächst beim [Azure-Portal](https://portal.azure.com)an. 

    > [!NOTE]
    > Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen. Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.

2.  Wenn Sie angemeldet sind, klicken Sie in der oberen linken Ecke auf **neu** , suchen Sie nach *Maschinelles Sehen-API*, und drücken Sie die **Eingabe**Taste.

    ![Erstellen einer neuen Ressource in Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > Das Wort **New** wurde möglicherweise durch **Create a Resource**in neueren Portalen ersetzt.
 
3.  Auf der neuen Seite wird eine Beschreibung des *Maschinelles Sehen-API* Dienstanbieter bereitgestellt. Klicken Sie unten links auf dieser Seite auf die Schaltfläche **Erstellen** , um eine Verknüpfung mit diesem Dienst zu erstellen.

    ![Informationen zum Maschinelles Sehen-API-Dienst](images/AzureLabs-Lab2-01.png)
 
4.  Nachdem Sie auf **Erstellen**geklickt haben, klicken Sie auf:

    1. Fügen Sie den gewünschten **Namen** für diese Dienst Instanz ein.
    2. Wählen Sie ein **Abonnement**aus.
    3. Wählen Sie den für **Sie geeigneten Tarif** aus. Wenn Sie zum ersten Mal einen *Maschinelles Sehen-API* Dienst erstellen, sollte Ihnen ein Free-Tarif (mit dem Namen "F0") zur Verfügung stehen.
    4. Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** . Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Labs) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern. 

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Bestimmen Sie den Speicherort für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen). Der Speicherort wäre idealerweise in der Region, in der die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.

    6. Außerdem müssen Sie bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.
    7. Klicken Sie auf erstellen.

        ![Informationen zur Dienst Erstellung](images/AzureLabs-Lab2-02.png)

5.  Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.
6.  Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Anzeigen der neuen Benachrichtigung für den neuen Dienst](images/AzureLabs-Lab2-03.png) 
 
7.  Klicken Sie auf die Benachrichtigung, um die neue Dienst Instanz zu untersuchen. 

    ![Wählen Sie die Schaltfläche Gehe zu Ressource aus.](images/AzureLabs-Lab2-04.png)
 
8. Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen. Sie gelangen zu ihrer neuen Maschinelles Sehen-API Dienst Instanz. 

    ![Ihre neue Maschinelles Sehen-API-Dienst](images/AzureLabs-Lab2-05.png)
 
9.  In diesem Lernprogramm muss Ihre Anwendung Aufrufe an Ihren Dienst durchführen. Dies erfolgt über den Abonnement Schlüssel Ihres dienstanzschlüssels.
10. Navigieren Sie auf der Seite " *Schnellstart* " Ihres *Maschinelles Sehen-API* Diensts zum ersten Schritt, rufen Sie *Ihre Schlüssel*ab, und klicken Sie auf " **Schlüssel** " (Sie können dies auch erreichen, indem Sie auf die blauen Hyperlink-Schlüssel im Navigationsmenü "Dienste" klicken. gekennzeichnet durch das Schlüsselsymbol). Dadurch werden die Dienst *Schlüssel*angezeigt.
11. Erstellen Sie eine Kopie von einem der angezeigten Schlüssel, da Sie dies später in Ihrem Projekt benötigen. 

12. Wechseln Sie zurück zur Seite *Schnellstart* , und rufen Sie den Endpunkt ab. Beachten Sie, dass Sie je nach Region unterschiedlich sein können (wenn dies der Fall ist, müssen Sie später eine Änderung an Ihrem Code vornehmen). Erstellen Sie für die spätere Verwendung eine Kopie dieses Endpunkts:

    ![Ihre neue Maschinelles Sehen-API-Dienst](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > Sie können überprüfen, [worum es sich](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)bei den verschiedenen Endpunkten handelt. 

## <a name="chapter-2--set-up-the-unity-project"></a>Kapitel 2 – Einrichten des Unity-Projekts

Folgendes ist eine typische Einrichtung für die Entwicklung mit gemischter Realität und ist daher eine gute Vorlage für andere Projekte.

1.  Öffnen Sie *Unity* , und klicken Sie auf **neu**. 

    ![Starten Sie ein neues Unity-Projekt.](images/AzureLabs-Lab2-06.png)

2.  Sie müssen nun einen Unity-Projektnamen angeben. Fügen Sie **MR_ComputerVision**ein. Stellen Sie sicher, dass Projekttyp auf **3D**festgelegt ist. Legen Sie den Speicherort auf einen geeigneten **Speicherort** fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind). Klicken Sie dann auf **Projekt erstellen**.

    ![Geben Sie Details für ein neues Unity-Projekt an.](images/AzureLabs-Lab2-07.png)

3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist. Wechseln Sie zu **Edit > Preferences (Einstellungen bearbeiten** ), und navigieren Sie dann im neuen Fenster zu **externe Tools**. Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**. Schließen Sie das Fenster " **Einstellungen** ".

    ![Skript-Editor-Einstellung aktualisieren.](images/AzureLabs-Lab2-08.png)

4.  Navigieren Sie als nächstes zu **Datei > Buildeinstellungen** , wählen Sie **universelle Windows-Plattform**aus, und klicken Sie dann auf die Schaltfläche **Plattform wechseln** , um Ihre Auswahl zu übernehmen

    ![Fenster "Buildeinstellungen", Plattform zu UWP wechseln.](images/AzureLabs-Lab2-10.png)

5.  In **Datei > Buildeinstellungen** , und stellen Sie Folgendes sicher:

    1. **Zielgerät** ist auf **hololens** festgelegt

        > Legen Sie für die immersiven Headsets das **Zielgerät** auf *ein beliebiges Gerät*fest.

    2. Der **Buildtyp** ist auf **D3D** festgelegt.
    3. **SDK** ist auf **neueste installierte** Version festgelegt.
    4. **Visual Studio-Version** ist auf **neueste installierte** Version festgelegt.
    5. **Build und Run** sind auf **lokaler Computer** festgelegt.
    6. Speichern Sie die Szene, und fügen Sie Sie dem Build hinzu.

        1. Wählen Sie hierzu die Option **geöffnete Szenen hinzufügen**aus. Ein Fenster zum Speichern wird angezeigt.
        
            ![Klicken Sie auf Schaltfläche "Open Szenen](images/AzureLabs-Lab2-11.png)

        2. Erstellen Sie einen neuen Ordner für dieses und jede zukünftige Szene, und wählen Sie dann die Schaltfläche **neuer Ordner** aus, um einen neuen Ordner zu **erstellen.**

            ![Neuen Ordner "Skripts" erstellen](images/AzureLabs-Lab2-12.png)

        3. Öffnen Sie den neu erstellten Ordner **Szenen** , geben Sie im Feld *Dateiname*: Text **MR_ComputerVisionScene**ein, und klicken Sie dann auf **Speichern**.

            ![Benennen Sie neue Szene.](images/AzureLabs-Lab2-13.png)

            > Beachten Sie, dass Sie Ihre Unity-Szenen im Ordner " *Assets* " speichern müssen, da Sie dem Unity-Projekt zugeordnet werden müssen. Das Erstellen eines Szenen Ordners (und anderer ähnlicher Ordner) ist eine typische Methode zum Strukturieren eines Unity-Projekts.

    7. Die restlichen Einstellungen in den *Buildeinstellungen*sollten vorerst als Standard belassen werden.

6. Klicken Sie im Fenster *Buildeinstellungen* auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der *Inspektor* befindet. 

    ![Öffnen Sie die Player-Einstellungen.](images/AzureLabs-Lab2-14.png)

7. In diesem Bereich müssen einige Einstellungen überprüft werden:

    1. Auf der Registerkarte **andere Einstellungen** :

        1. Die **Lauf Zeit Version der Skript** Erstellung muss **stabil** sein (.NET 3,5-Entsprechung).
        2. **Skript** -Back-End sollte **.net** sein
        3. **API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten

            ![Aktualisieren Sie andere Einstellungen.](images/AzureLabs-Lab2-15.png)
      
    2. Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:

        1. **Internet Client deklarieren**
        2. **Webcam**

            ![Veröffentlichungs Einstellungen werden aktualisiert.](images/AzureLabs-Lab2-16.png)

    3. Weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), **unterstützt Tick Virtual Reality**, stellen Sie sicher, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.

        ![Aktualisieren Sie die X R-Einstellungen.](images/AzureLabs-Lab2-17.png)

8.  Zurück in *Buildeinstellungen* : _Unity C#_  -Projekte sind nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen neben this. 
9.  Schließen Sie das Fenster mit den Buildeinstellungen.
10. Speichern Sie Ihre Szene und Ihr Projekt (**Datei > Speichern Sie Szenen/Dateien > Speichern**Sie das Projekt).

## <a name="chapter-3--main-camera-setup"></a>Kapitel 3 – Hauptkamera Einrichtung

> [!IMPORTANT]
> Wenn Sie die *Unity-Setup* Komponente dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie dieses [. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage)herunterladen, es als [benutzerdefiniertes Paket](https://docs.unity3d.com/Manual/AssetPackages.html)in Ihr Projekt importieren und dann aus [Kapitel 5](#chapter-5--create-the-resultslabel-class)fortfahren.

1.  Wählen Sie im Bereich *Hierarchie*die **Hauptkamera**aus. 
2.  Nachdem Sie diese Option ausgewählt haben, können Sie alle Komponenten der **Hauptkamera** im *Inspektor-Panel*sehen.

    1. Das **Kamera Objekt** muss als **Hauptkamera** benannt werden (Beachten Sie die Schreibweise).
    2. Das Hauptkamera **Kennzeichen** muss auf **maincamera** festgelegt sein (Beachten Sie die Schreibweise).
    3. Stellen Sie sicher, dass die **Transformations Position** auf **0, 0, 0** festgelegt ist.
    4. Legen Sie **klar Flags** auf voll **Tonfarbe** fest (diese Einstellung wird für immersives Headset ignoriert).
    5. Legen Sie die **Hintergrund** Farbe der Kamera Komponente auf **schwarz, Alpha 0 (Hexadezimal Code: #00000000)** fest (Dies wird für das immersive Headset ignoriert).

        ![Aktualisieren Sie die Kamerakomponenten.](images/AzureLabs-Lab2-18.png)
 
3.  Als nächstes müssen Sie ein einfaches "Cursor"-Objekt erstellen, das an die **Hauptkamera**angeschlossen ist. Dadurch können Sie die Ausgabe der Bildanalyse beim Ausführen der Anwendung positionieren. Mit diesem Cursor wird der Mittelpunkt des Kamerafokus bestimmt.

So erstellen Sie den Cursor:

1.  Klicken Sie im *Hierarchie Panel*mit der rechten Maustaste auf die **Hauptkamera**. Klicken Sie unter **3D-Objekt**auf **Kugel**.

    ![Wählen Sie das Cursor Objekt aus.](images/AzureLabs-Lab2-19.png)
 
2.  Benennen Sie die **Kugel** in den **Cursor** um (Doppelklicken Sie auf das Cursor Objekt, oder drücken Sie die Tastenkombination "F2", wenn das Objekt ausgewählt ist), und stellen Sie sicher, dass Sie sich als untergeordnetes Element der **Hauptkamera**befindet

3.  Klicken Sie im *Hierarchie Panel*mit der linken Maustaste auf den **Cursor**. Wenn der Cursor ausgewählt ist, passen Sie die folgenden Variablen im *Inspektor-Panel*an:

    1. Legen Sie die *Transformations Position* auf **0, 0, 5** fest.
    2. Legen Sie die *Skala* auf **0,02, 0,02, 0,02**

        ![Aktualisieren der Transformations Position und-Skalierung.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>Kapitel 4 – Einrichten des Bezeichnungs Systems

Nachdem Sie ein Bild mit der Kamera hololens erfasst haben, wird dieses Abbild zur Analyse an Ihre *Azure Maschinelles Sehen-API* -Dienst Instanz gesendet. 

Die Ergebnisse dieser Analyse stellen eine Liste bekannter Objekte dar, die als **Tags**bezeichnet werden. 

Sie verwenden Bezeichnungen (als 3D-Text im Raum), um diese Tags an der Stelle anzuzeigen, an der das Foto entnommen wurde.

In den folgenden Schritten wird gezeigt, wie Sie das **Label** -Objekt einrichten.

1.  Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im Hierarchie Panel (der Standort ist an diesem Punkt nicht wichtig), und fügen Sie unter **3D-Objekt**einen **3D-Text**hinzu. Nennen Sie es **LabelText**.

    ![3D-Text Objekt erstellen.](images/AzureLabs-Lab2-21.png)
 
2.  Klicken Sie im *Hierarchie Panel*mit der linken Maustaste auf das **LabelText**-Element. Passen Sie bei ausgewähltem **LabelText** die folgenden Variablen im *Inspektor-Panel*an:

    1. Legen Sie die **Position** auf **0, 0, 0** fest.
    2. Legen Sie die **Skala** auf **0,01, 0,01, 0,01**
    3. Im **textmesh**der Komponente:
    4. Ersetzen Sie den gesamten Text im **Text**durch "..."        
    5. Legen Sie den **Anker** auf das **mittlere Zentrum** fest.
    6. Festlegen der **Ausrichtung** auf **zentrieren**
    7. Legen Sie die **Tabstopp Größe** auf **4** fest.
    8. Legen Sie den **Schrift** Grad auf **50** fest.
    9. Legen Sie die **Farbe** auf **#FFFFFFFF**

    ![Text Komponente](images/AzureLabs-Lab2-21-5.png)

3.  Ziehen Sie den **LabelText** aus dem Bereich *Hierarchie*in den *Ordner Asset*innerhalb des *Projekt Panels*. Dadurch wird der **LabelText** zu einem präfab, damit er im Code instanziiert werden kann.

    ![Erstellen Sie eine vorfab des LabelText-Objekts.](images/AzureLabs-Lab2-22.png)
 
4.  Sie sollten das **LabelText** -Element aus dem *Hierarchie Panel*löschen, damit es nicht in der öffnenden Szene angezeigt wird. Da es sich nun um eine vorfab handelt, die Sie für einzelne Instanzen aus dem Ordner "Assets" abrufen, ist es nicht erforderlich, Sie in der Szene zu behalten. 
5.  Die endgültige Objektstruktur im *Hierarchie Panel* sollte wie die in der folgenden Abbildung gezeigt aussehen:

    ![Endgültige Struktur des Hierarchie Bereichs.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>Kapitel 5 – Erstellen der resultorlabel-Klasse

Das erste Skript, das Sie erstellen müssen, ist die Klasse " *resulttlabel* ", die für Folgendes zuständig ist: 

- Erstellen der Bezeichnungen im entsprechenden Raum, relativ zur Position der Kamera.
- Anzeigen der Tags aus der Bild anaysis

So erstellen Sie diese Klasse: 

1.  Klicken Sie mit der rechten Maustaste im *Projekt Panel*, und erstellen Sie dann **> Ordner**. Benennen Sie den Ordner mit **Skripts**. 

    ![Erstellen Sie den Ordner Skripts.](images/AzureLabs-Lab2-24.png)

2.  Wenn Sie den Ordner **Skripts** erstellen, doppelklicken Sie darauf, um ihn zu öffnen. Klicken Sie dann in diesem Ordner mit der rechten Maustaste auf, und wählen **C#** Sie dann **> Skript erstellen** aus. Nennen Sie das Skript " *ResultLabel*". 

3.  Doppelklicken Sie auf das neue *resulttlabel* -Skript, um es in **Visual Studio**zu öffnen.

4.  Fügen Sie in der-Klasse den folgenden Code in die *resultorlabel* -Klasse ein:

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.
7.  Klicken Sie im *Unity-Editor*auf die *resultslabel* -Klasse, und ziehen Sie Sie aus dem Ordner **Scripts** auf das **Hauptkamera** Objekt im Bereich *Hierarchie*.
8.  Klicken Sie auf die **Hauptkamera** , und sehen Sie sich den Bereich *Inspector*an.

Sie werden feststellen, dass Sie aus dem soeben in die Kamera gezogenen Skript zwei Felder haben: **Cursor** -und Bezeichnungs **präfab**.

9.  Ziehen Sie das Objekt **Cursor** aus dem Bereich *Hierarchie* in den Slot mit dem Namen **Cursor**, wie in der folgenden Abbildung dargestellt.
10. Ziehen Sie das Objekt " **LabelText** " aus dem *Ordner "Assets* " im *Projekt Panel* in den Slot mit dem Namen " **Label Prefab**", wie in der folgenden Abbildung dargestellt. 

    ![Legen Sie die Verweis Ziele innerhalb von Unity fest.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>Kapitel 6 – Erstellen der imagecapture-Klasse

Die nächste Klasse, die Sie erstellen, ist die *imagecapture* -Klasse. Diese Klasse ist für Folgendes zuständig:

-   Erfassen eines Bilds mithilfe der hololens-Kamera und speichern im App-Ordner.
-   Das Erfassen von TAP-Gesten vom Benutzer.

So erstellen Sie diese Klasse: 

1.  Wechseln Sie zum Ordner " **Scripts** ", den Sie zuvor erstellt haben. 
2.  Klicken Sie mit der rechten Maustaste in den Ordner, und **Erstellen Sie > C# Skript**. Nennen Sie das Skript *imagecapture*. 
3.  Doppelklicken Sie auf das neue *imagecapture* -Skript, um es in **Visual Studio**zu öffnen.
4.  Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  Fügen Sie dann die folgenden Variablen in der *imagecapture* -Klasse oberhalb der *Start ()* -Methode hinzu:

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
Die Variable **tapscount** speichert die Anzahl der vom Benutzer erfassten Tap-Gesten. Diese Zahl wird bei der Benennung der aufgezeichneten Bilder verwendet.

6.  Der Code für die Methoden " *Awake ()* " und " *Start ()* " muss nun hinzugefügt werden. Diese werden aufgerufen, wenn die-Klasse initialisiert:

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  Implementieren Sie einen Handler, der aufgerufen wird, wenn eine Tap-Geste auftritt. 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
Die *taphandler ()* -Methode erhöht die Anzahl der vom Benutzer erfassten Abzweigungen und verwendet die aktuelle Cursor Position, um zu bestimmen, wo eine neue Bezeichnung positioniert werden soll.

Diese Methode ruft dann die *executeimagecaptureandanalysis ()* -Methode auf, um die Kernfunktionen dieser Anwendung zu beginnen.

8.  Nachdem ein Bild aufgezeichnet und gespeichert wurde, werden die folgenden Handler aufgerufen. Wenn der Prozess erfolgreich ist, wird das Ergebnis an den *visionmanager* (den Sie noch erstellen) für die Analyse übermittelt.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  Fügen Sie dann die-Methode hinzu, die die Anwendung verwendet, um den Bild Aufzeichnungsprozess zu starten und das Abbild zu speichern.

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> An dieser Stelle bemerken Sie einen Fehler, der im *Konsolen Panel des Unity-Editors*angezeigt wird. Dies liegt daran, dass der Code auf die Klasse " *visionmanager* " verweist, die Sie im nächsten Kapitel erstellen werden.

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>Kapitel 7 – Aufrufe von Azure und Image Analyse

Das letzte Skript, das Sie erstellen müssen, ist die Klasse " *visionmanager* ". 

Diese Klasse ist für Folgendes zuständig:

-   Das letzte als Bytearray erfasste Bild wird geladen.
-   Das Bytearray wird zur Analyse an Ihre *Azure Maschinelles Sehen-API* -Dienst Instanz gesendet.
-   Die Antwort wird als JSON-Zeichenfolge empfangen.
-   Deserialisieren der Antwort und übergeben der resultierenden Tags an die *ResultLabel* -Klasse.
 
So erstellen Sie diese Klasse:

1.  Doppelklicken Sie auf den Ordner " **Scripts** ", um ihn zu öffnen. 
2.  Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf  **C# > Skript erstellen**. Nennen Sie das Skript " *visionmanager*". 
3.  Doppelklicken Sie auf das neue Skript, um es in Visual Studio zu öffnen.
4.  Aktualisieren Sie die Namespaces so, dass Sie am Anfang der Klasse " *visionmanager* " wie folgt lauten:

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  Am Anfang des Skripts in der Klasse " *visionmanager* " (oberhalb der Methode " *Start ()* ") müssen Sie nun zwei *Klassen* *erstellen, die* die deserialisierte JSON-Antwort von Azure darstellen:

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > Der " *TagData* "-Klasse und der *analysedobject* -Klasse muss das *[System. serialisierbare]* -Attribut vor der Deklaration hinzugefügt werden, damit Sie mit den Unity-Bibliotheken deserialisiert werden kann.

6.  Fügen Sie in der Klasse "visionmanager" die folgenden Variablen hinzu:

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > Stellen Sie sicher, dass Sie den Authentifizierungs **Schlüssel** in die **authorizationkey** -Variable einfügen. Sie haben den Authentifizierungs **Schlüssel** zu Beginn dieses Kurses notiert, [Kapitel 1](#chapter-1--the-azure-portal).

    > [!WARNING] 
    > Die " **visionanalysisendpoint** "-Variable kann sich von der in diesem Beispiel angegebenen unterscheiden. **USA, Westen** bezieht sich strikt auf Dienst Instanzen, die für die Region "USA, Westen" erstellt wurden. Aktualisieren Sie dies mit der [Endpunkt-URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa). Im folgenden finden Sie einige Beispiele dafür, wie Sie aussehen können:
    > - Europa, Westen:`https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Südostasien:`https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Australien, Osten:`https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  Der Code für "awado" muss nun hinzugefügt werden. 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  Fügen Sie als nächstes die Coroutine (mit der statischen streammethode darunter) hinzu, die die Ergebnisse der Analyse des Bilds erhält, das von der *imagecapture* -Klasse erfasst wird. 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.
10. Klicken Sie im Unity-Editor auf die Klassen " *visionmanager* " und " *imagecapture* ", und ziehen Sie Sie aus dem Ordner " **Scripts** " in das **Hauptkamera** Objekt im *Hierarchie Panel*. 

## <a name="chapter-8--before-building"></a>Kapitel 8 – vor dem Aufbau

Um eine gründliche Test Ihrer Anwendung durchzuführen, müssen Sie Sie auf Ihre hololens querladen.
Bevor Sie vorgehen, stellen Sie Folgendes sicher:

-   Alle in [Kapitel 2](#chapter-2--set-up-the-unity-project) erwähnten Einstellungen sind richtig festgelegt. 
-   Alle Skripts werden an das **Hauptkamera** Objekt angefügt. 
-   Alle Felder im Hauptbereich der *Kamera Inspektor* sind ordnungsgemäß zugewiesen.
-   Stellen Sie sicher, dass Sie den Authentifizierungs **Schlüssel** in die **authorizationkey** -Variable einfügen.
-   Stellen Sie sicher, dass Sie auch ihren Endpunkt in Ihrem " *visionmanager* "-Skript geprüft haben und dass es sich an *ihrer* Region anpasst (standardmäßig verwendet dieses Dokument " *USA, Westen* ").

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>Kapitel 9 – Erstellen der UWP-Lösung und querladen der Anwendung
Alles, was für den Unity-Abschnitt dieses Projekts erforderlich ist, ist nun abgeschlossen, sodass es an der Zeit ist, Sie aus Unity zu erstellen.

1.  Navigieren Sie zu -  *buildeinstellungs***Datei > Buildeinstellungen...**
2.  Klicken Sie im Fenster " *Buildeinstellungen* " auf " **Erstellen**".

    ![Entwickeln der APP aus Unity](images/AzureLabs-Lab2-26.png)

3.  Wenn dies nicht bereits geschehen ist, Tick **Unity C# -Projekte**.
4.  Klicken Sie auf **Erstellen**. Unity startet ein *Datei-Explorer* -Fenster, in dem Sie einen Ordner erstellen und auswählen müssen, in dem die App erstellt wird. Erstellen Sie diesen Ordner jetzt, und nennen Sie ihn " *App*". Klicken Sie dann mit ausgewähltem *App* -Ordner auf **Ordner auswählen**. 
5.  Unity startet das Projekt in den *App* -Ordner. 
6.  Nachdem die Erstellung von Unity abgeschlossen ist (Dies kann einige Zeit in Anspruch nehmen), wird ein *Datei-Explorer* -Fenster am Speicherort des Builds geöffnet (überprüfen Sie die Taskleiste, da Sie möglicherweise nicht immer über Ihrem Fenster angezeigt wird, sondern Sie über das Hinzufügen eines neuen Fensters benachrichtigt).

## <a name="chapter-10--deploy-to-hololens"></a>Kapitel 10 – bereitstellen in hololens

So stellen Sie auf hololens bereit:

1.  Sie benötigen die IP-Adresse Ihrer hololens (für die Remote Bereitstellung) und, um sicherzustellen, dass sich Ihre hololens im **Entwicklermodus**befinden. Gehen Sie dazu wie folgt vor:

    1. Öffnen Sie die Einstellungen, während Sie die hololens- **Einstellungen**durch tragen.
    2. Navigieren Sie zu **Netzwerk & Internet > Wi-Fi > Erweiterte Optionen**
    3. Notieren Sie sich die **IPv4** -Adresse.
    4. Navigieren Sie als nächstes wieder zu **Einstellungen**, und aktualisieren Sie dann **& Sicherheits > für Entwickler** . 
    5. Legen Sie den Entwicklermodus auf fest.

2.  Navigieren Sie zu Ihrem neuen Unity-Build ( *App* -Ordner), und öffnen Sie die Projektmappendatei mit *Visual Studio*.
3.  Wählen Sie in der Projektmappenkonfiguration **Debuggen**.
4.  Wählen Sie auf der Projektmappenplattform die Option **x86**, **Remote Computer**aus. 

    ![Stellen Sie die Lösung aus Visual Studio bereit.](images/AzureLabs-Lab2-27.png)
 
5.  Wechseln Sie zum **Menü Erstellen** , und klicken Sie auf **Lösung**bereitstellen, um die Anwendung auf die hololens quer zuladen.
6.  Ihre APP sollte nun in der Liste der installierten apps auf Ihren hololens angezeigt werden, die bereit sind, gestartet zu werden.

> [!NOTE]
> Legen Sie für die Bereitstellung auf dem immersiven Headset die Projektmappenplattform auf *lokaler Computer*fest, und legen Sie die **Konfiguration** auf *Debuggen*und *x86* als **Plattform**fest. Stellen Sie dann auf dem lokalen Computer bereit, indem Sie im **Menü Erstellen**die Option *Lösung*bereitstellen auswählen. 

## <a name="your-finished-computer-vision-api-application"></a>Ihre fertiggestellte Maschinelles Sehen-API Anwendung

Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die die Azure-Maschinelles Sehen-API nutzt, um reale Objekte zu erkennen, und zeigen Ihnen das Vertrauen an, was Sie gesehen haben.

![Lab-Ergebnis](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>Bonus Übungen

### <a name="exercise-1"></a>Übung 1

Ebenso wie Sie den Parameter " *Tags* " (wie in dem *Endpunkt* , der innerhalb von " *visionmanager*" verwendet wird) verwendet haben, erweitern Sie die APP, um weitere Informationen zu erkennen. Werfen Sie einen Blick auf die anderen Parameter, auf die Sie [hier](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)zugreifen können.

### <a name="exercise-2"></a>Übung 2

Zeigen Sie die zurückgegebenen Azure-Daten in einer besser lesbaren und lesbaren Weise an, und verbergen Sie die Zahlen vielleicht. So, als ob ein bot für den Benutzer sprechen könnte.
