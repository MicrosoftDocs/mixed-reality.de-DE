---
title: Mr und Azure 301-Sprachübersetzung
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie die Azure-Textübersetzungs-API in einer Mixed Reality-Anwendung implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Translator Text, hololens, immersive, VR
ms.openlocfilehash: 012eb5522c866e9e0f1caf5e4024305af07e298c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438529"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.

<br>

# <a name="mr-and-azure-301-language-translation"></a>Mr und Azure 301: Sprachübersetzung

In diesem Kurs erfahren Sie, wie Sie mithilfe von Azure Cognitive Services Übersetzungsfunktionen zu einer gemischten Reality-Anwendung hinzufügen, mit der Textübersetzungs-API.

![Endgültiges Produkt](images/AzureLabs-Lab1-00.png)

Der Textübersetzungs-API ist ein Übersetzungsdienst, der nahezu in Echtzeit funktioniert. Der Dienst ist cloudbasiert, und mit einem Rest-API-Befehl kann eine APP die Übersetzungstechnologie für neuronale Computer verwenden, um Text in eine andere Sprache zu übersetzen. Weitere Informationen finden Sie auf der [Seite Azure Textübersetzungs-API](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).

Nach Abschluss dieses Kurses verfügen Sie über eine Mixed Reality-Anwendung, die Folgendes ausführen kann:

1.  Der Benutzer spricht in ein Mikrofon, das mit einem immersiven (VR)-Headset (oder dem integrierten Mikrofon von hololens) verbunden ist.
2.  Die APP erfasst die Diktat und sendet Sie an den Azure-Textübersetzungs-API.
3.  Das Übersetzungsergebnis wird in einer einfachen Benutzeroberflächen Gruppe in der Unity-Szene angezeigt.

In diesem Kurs erfahren Sie, wie Sie die Ergebnisse des Konvertierungs Dienstanbieter in einer Unity-basierten Beispielanwendung erhalten. Sie müssen diese Konzepte auf eine benutzerdefinierte Anwendung anwenden, die Sie möglicherweise aufbauen.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> Mr und Azure 301: Sprachübersetzung</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Dieser Kurs konzentriert sich in erster Linie auf Windows Mixed Reality immersive (VR)-Headsets, aber Sie können auch das, was Sie in diesem Kurs lernen, auf Microsoft hololens anwenden. Wenn Sie den Kurs befolgen, finden Sie Hinweise zu allen Änderungen, die Sie möglicherweise zur Unterstützung von hololens verwenden müssen. Wenn Sie hololens verwenden, bemerken Sie möglicherweise bei der sprach Erfassung einen Echo.

## <a name="prerequisites"></a>Voraussetzungen

> [!NOTE]
> Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen. Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Mai 2018). Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](install-the-tools.md) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt sind.

Für diesen Kurs empfehlen wir die folgende Hardware und Software:

- Einen Entwicklungs-PC, der [mit der Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for Immersive (VR)-Headset-Entwicklung kompatibel ist
- [Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus](install-the-tools.md#installation-checklist)
- [Das neueste Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Ein [Windows Mixed Reality-Headset (VR)](immersive-headset-hardware-details.md) oder [Microsoft hololens](hololens-hardware-details.md) mit aktiviertem Entwicklermodus
- Eine Reihe von Kopfhörern mit einem integrierten Mikrofon (wenn das Headset nicht über eine integrierte Mic-und-Sprech Anwendung verfügt)
- Internet Zugang für das Einrichten und Übersetzen von Azure

## <a name="before-you-start"></a>Bevor Sie beginnen

- Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).
- Der Code in diesem Tutorial ermöglicht es Ihnen, vom Standard Mikrofon Gerät, das mit Ihrem PC verbunden ist, aufzuzeichnen. Stellen Sie sicher, dass das standardmäßige Mikrofon-Gerät auf das Gerät festgelegt ist, das Sie zum Erfassen Ihrer Stimme verwenden möchten.
- Um dem PC das Schreiben von Diktat zu gestatten, wechseln Sie zu **Einstellungen > Datenschutz > Sprache, & eingeben,** und klicken Sie auf die Schaltfläche **Sprachdienste aktivieren und Vorschläge eingeben**.
- Wenn Sie ein Mikrofon und Kopfhörer verwenden, die mit dem Headset verbunden sind (bzw. in das Sie integriert sind), stellen Sie sicher, dass die Option "Wenn ich mein Headset trage, zu Headset mic wechseln" in den **Einstellungen > Gemischte Realität > Audio-und sprachsprache**aktiviert ist.

   ![Mixed Reality-Einstellungen](images/AzureLabs-Lab1-00-5.png)

   ![Mikrofon-Einstellung](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> Beachten Sie, dass bei der Entwicklung für ein immersives Headset für dieses Lab Geräte Probleme bei der Audioausgabe auftreten können. Dies liegt an einem Problem mit Unity, das in höheren Versionen von Unity (Unity 2018,2) behoben wird. Das Problem verhindert, dass Unity das standardmäßige Audioausgabegerät zur Laufzeit ändert. Stellen Sie sicher, dass Sie die oben genannten Schritte abgeschlossen haben, und schließen Sie den Editor, und öffnen Sie ihn erneut, wenn sich dieses Problem selbst darstellt.

## <a name="chapter-1--the-azure-portal"></a>Kapitel 1 – Azure-Portal

Um die Azure Translator-API zu verwenden, müssen Sie eine Instanz des-Dienstanbieter konfigurieren, die für die Anwendung verfügbar gemacht wird.

1.  Melden Sie sich beim [Azure-Portal](https://portal.azure.com)an.

    > [!NOTE]
    > Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen. Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.

2.  Wenn Sie angemeldet sind, klicken Sie in der oberen linken Ecke auf " **neu** ", und suchen Sie nach "Textübersetzungs-API". **Drücken Sie Eingabe**Taste.

    ![Neue Ressource](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > Das Wort **New** wurde möglicherweise durch **Create a Resource**in neueren Portalen ersetzt.

3.  Auf der neuen Seite wird eine Beschreibung des *Textübersetzungs-API* Dienstanbieter bereitgestellt. Klicken Sie unten links auf dieser Seite auf die Schaltfläche **Erstellen** , um eine Verknüpfung mit diesem Dienst zu erstellen.

    ![Erstellen Textübersetzungs-API Dienstanbieter](images/AzureLabs-Lab1-03.png)

4.  Nachdem Sie auf **Erstellen**geklickt haben, klicken Sie auf:

    1. Fügen Sie den gewünschten **Namen** für diese Dienst Instanz ein.
    2. Wählen Sie ein entsprechendes **Abonnement**aus.
    3. Wählen Sie den für **Sie geeigneten Tarif** aus. Wenn Sie zum ersten Mal einen *Textübersetzung Dienst*erstellen, sollte Ihnen ein Free-Tarif (mit dem Namen "F0") zur Verfügung stehen.
    4. Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** . Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Labs) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Bestimmen Sie den **Speicherort** für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen). Der Speicherort wäre idealerweise in der Region, in der die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.
    6. Außerdem müssen Sie bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.
    7. Wählen Sie **Erstellen** aus.

        ![Wählen Sie die Schaltfläche erstellen.](images/AzureLabs-Lab1-04.png)

5.  Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.
6.  Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt. 

    ![Benachrichtigung zur Azure-Dienst Erstellung](images/AzureLabs-Lab1-05.png)

7.  Klicken Sie auf die Benachrichtigung, um die neue Dienst Instanz zu untersuchen. 

    ![Wechseln Sie zum ressourcenpopup.](images/AzureLabs-Lab1-06.png)

8.  Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen. Sie gelangen zu ihrer neuen Textübersetzungs-API Dienst Instanz. 

    ![Textübersetzungs-API Dienst Seite](images/AzureLabs-Lab1-07.png)

9.  In diesem Lernprogramm muss Ihre Anwendung Aufrufe an Ihren Dienst durchführen. Dies erfolgt über den Abonnement Schlüssel Ihres dienstanzschlüssels. 
10. Navigieren Sie auf der Seite *Schnellstart* Ihres *Textübersetzung* Diensts zum ersten Schritt, rufen *Sie Ihre Schlüssel*ab, und klicken Sie auf **Schlüssel** (Sie können dies auch erreichen, indem Sie auf die blauen Hyperlink-Schlüssel im Navigationsmenü Dienste klicken. gekennzeichnet durch das Schlüsselsymbol). Dadurch werden die Dienst *Schlüssel*angezeigt.
11. Erstellen Sie eine Kopie von einem der angezeigten Schlüssel, da Sie dies später in Ihrem Projekt benötigen. 

## <a name="chapter-2--set-up-the-unity-project"></a>Kapitel 2 – Einrichten des Unity-Projekts

Richten Sie Ihr immersives Headset mit gemischter Realität ein und testen Sie es.

> [!NOTE]
> Für diesen Kurs benötigen Sie keine Bewegungs Controller. Wenn Sie Unterstützung bei der Einrichtung eines immersiven Headsets benötigen, führen Sie [die folgenden Schritte](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)aus.

Folgendes ist ein typisches Setup für die Entwicklung mit gemischter Realität und eine gute Vorlage für andere Projekte:

1.  Öffnen Sie *Unity* , und klicken Sie auf **neu**. 

    ![Starten Sie ein neues Unity-Projekt.](images/AzureLabs-Lab1-08.png)

2.  Sie müssen nun einen Unity-Projektnamen angeben. Fügen Sie **MR_Translation**ein. Stellen Sie sicher, dass Projekttyp auf **3D**festgelegt ist. Legen Sie den Speicherort auf einen geeigneten *Speicherort* fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind). Klicken Sie dann auf **Projekt erstellen**.

    ![Geben Sie Details für ein neues Unity-Projekt an.](images/AzureLabs-Lab1-09.png)

3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist. Wechseln Sie zu **Edit > Preferences (Einstellungen bearbeiten** ), und navigieren Sie dann im neuen Fenster zu **externe Tools**. Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**. Schließen Sie das Fenster " **Einstellungen** ".

    ![Skript-Editor-Einstellung aktualisieren.](images/AzureLabs-Lab1-10.png)

4.  Navigieren Sie als nächstes zu **Datei > Buildeinstellungen** , und schalten Sie die Plattform auf **universelle Windows-Plattform**, indem Sie auf die Schaltfläche **Plattform wechseln** klicken.

    ![Fenster "Buildeinstellungen", Plattform zu UWP wechseln.](images/AzureLabs-Lab1-11.png)

5.  Wechseln Sie zu **Datei > Build-Einstellungen** , und stellen Sie Folgendes sicher:

    1. Das **Zielgerät** ist auf **ein beliebiges Gerät**festgelegt.

        > Legen Sie für Microsoft hololens das **Zielgerät** auf *hololens*fest.

    2. Der **Buildtyp** ist auf **D3D** festgelegt.
    3. **SDK** ist auf **neueste installierte** Version festgelegt.
    4. **Visual Studio-Version** ist auf **neueste installierte** Version festgelegt.
    5. **Build und Run** sind auf **lokaler Computer** festgelegt.
    6. Speichern Sie die Szene, und fügen Sie Sie dem Build hinzu.

        1. Wählen Sie hierzu die Option **geöffnete Szenen hinzufügen**aus. Ein Fenster zum Speichern wird angezeigt.

            ![Klicken Sie auf Schaltfläche "Open Szenen](images/AzureLabs-Lab1-12.png)

        2. Erstellen Sie einen neuen Ordner für dieses und jede zukünftige Szene, und wählen Sie dann die Schaltfläche **neuer Ordner** aus, um einen neuen Ordner zu **erstellen.**

            ![Neuen Ordner "Skripts" erstellen](images/AzureLabs-Lab1-13.png)

        3. Öffnen Sie den neu erstellten Ordner **Szenen** , geben Sie im Feld *Dateiname*: Text **MR_TranslationScene**ein, und klicken Sie dann auf **Speichern**.

            ![Benennen Sie neue Szene.](images/AzureLabs-Lab1-14.png)

            > Beachten Sie, dass Sie Ihre Unity-Szenen im Ordner " *Assets* " speichern müssen, da Sie dem Unity-Projekt zugeordnet werden müssen. Das Erstellen eines Szenen Ordners (und anderer ähnlicher Ordner) ist eine typische Methode zum Strukturieren eines Unity-Projekts.

    7. Die restlichen Einstellungen in den *Buildeinstellungen*sollten vorerst als Standard belassen werden.

6. Klicken Sie im Fenster *Buildeinstellungen* auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der *Inspektor* befindet. 

    ![Öffnen Sie die Player-Einstellungen.](images/AzureLabs-Lab1-15.png)

7. In diesem Bereich müssen einige Einstellungen überprüft werden:

    1. Auf der Registerkarte **andere Einstellungen** :

        1. Die **Lauf Zeit Version der Skript** Erstellung muss **stabil** sein (.NET 3,5-Entsprechung).
        2. **Skript** -Back-End sollte **.net** sein
        3. **API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten

            ![Aktualisieren Sie andere Einstellungen.](images/AzureLabs-Lab1-16.png)
      
    2. Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:

        1. **Internet Client deklarieren**
        2. **Tritt**

            ![Veröffentlichungs Einstellungen werden aktualisiert.](images/AzureLabs-Lab1-17.png)

    3. Weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), **unterstützt Tick Virtual Reality**, stellen Sie sicher, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.

        ![Aktualisieren Sie die X R-Einstellungen.](images/AzureLabs-Lab1-18.png)

8.  Wieder in den **Buildeinstellungen**ist *Unity C# -Projekte* nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen neben this. 
9.  Schließen Sie das Fenster mit den Buildeinstellungen.
10. Speichern Sie Ihre Szene und Ihr Projekt (**Datei > Speichern Sie Szenen/Dateien > Speichern**Sie das Projekt).

## <a name="chapter-3--main-camera-setup"></a>Kapitel 3 – Hauptkamera Einrichtung

> [!IMPORTANT]
> Wenn Sie die *Unity-Setup* Komponente dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie [dieses. unitypackage herunterladen](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), es als [*benutzerdefiniertes Paket*](https://docs.unity3d.com/Manual/AssetPackages.html)in Ihr Projekt importieren und dann aus [Kapitel 5](#chapter-5--create-the-results-class)fortfahren. Sie müssen dennoch ein Unity-Projekt erstellen.

1.  Im *Hierarchie Panel*finden Sie ein Objekt mit dem Namen " **Main Camera**". dieses Objekt stellt den "Head"-Punkt dar, sobald Sie die Anwendung "in" haben.
2.  Wählen Sie mit dem Unity-Dashboard vor Ihnen das **Hauptkamera-gameobject**aus. Sie werden feststellen, dass im *Inspektor-Panel* (in der Regel auf der rechten Seite im Dashboard) die verschiedenen Komponenten dieses *gameobject*angezeigt werden, mit der *Transformation* am oberen Rand, gefolgt von der *Kamera*und einigen anderen Komponenten. Sie müssen die Transformation der Hauptkamera zurücksetzen, damit Sie ordnungsgemäß positioniert ist.
3.  Wählen Sie dazu das **Zahnrad** Symbol neben der *Transformations* Komponente der Kamera aus, und wählen Sie **Zurücksetzen**aus. 

    ![Setzen Sie die Hauptkamera Transformation zurück.](images/AzureLabs-Lab1-19.png)
 
4.  Die *Transformations* Komponente sollte dann wie folgt aussehen:

    1. Die *Position* ist auf **0, 0, 0** festgelegt.
    2. *Drehung* ist auf **0, 0, 0** festgelegt.
    3. Und die *Skala* ist auf **1, 1, 1** festgelegt.

        ![Transformations Informationen für Kamera](images/AzureLabs-Lab1-20.png)

5.  Wenn das **Hauptkamera** Objekt ausgewählt ist, sehen Sie sich die Schaltfläche **Komponente hinzufügen** am unteren Rand des *inspektorbereichs*an. 
6.  Wählen Sie diese Schaltfläche aus, und suchen Sie (entweder geben Sie *Audioquelle* in das Suchfeld ein, oder navigieren Sie in den Abschnitten) für die Komponente namens **Audioquelle** , wie unten dargestellt, und wählen Sie Sie aus.
7.  Der **Hauptkamera**wird eine *audioquellkomponente* hinzugefügt, wie unten gezeigt.

    ![Fügen Sie eine audioquellkomponente hinzu.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > Für Microsoft hololens müssen Sie auch die folgenden ändern, die Teil der **Kamera** Komponente auf der **Hauptkamera**sind:
    > - **Flags löschen:** Voll Tonfarbe.
    > - **Hintergrund** ' Black, Alpha 0 ' – hexadezimal Farbe: #00000000.

## <a name="chapter-4--setup-debug-canvas"></a>Kapitel 4 – Setup-Debug-Canvas

Zum Anzeigen der Eingabe und der Ausgabe der Übersetzung muss eine grundlegende Benutzeroberfläche erstellt werden. Für diesen Kurs erstellen Sie ein Canvas-UI-Objekt mit mehreren ' Text '-Objekten, um die Daten anzuzeigen.

1.  Klicken Sie mit der rechten Maustaste auf einen leeren Bereich des Bereichs *Hierarchie*, und fügen Sie unter **Benutzeroberfläche**eine **Canvas**hinzu.

    ![Hinzufügen eines neuen Canvas-UI-Objekts.](images/AzureLabs-Lab1-22.png)

2.  Wenn Sie das Canvas-Objekt ausgewählt haben, ändern Sie im *Inspektor-Panel* (innerhalb der Canvas-Komponente) den **Rendermodus** in den **Raum**. 
3.  Im nächsten Schritt ändern Sie die folgenden Parameter in der *Rect-Transformation des inspektorpanels*:

    1. *POS* -  **X** 0 **Y** 0 **Z** 40
    2. *Breite* -500
    3. *Höhe* -300
    4. *Skalieren* - **X** 0,13 **Y** 0,13 **Z** 0,13

        ![Aktualisieren Sie die Rect-Transformation für den Zeichenbereich.](images/AzureLabs-Lab1-23.png)
 
4.  Klicken Sie **mit der rechten** Maustaste auf den Zeichenbereich im *Hierarchie Panel*unter **UI**, und fügen Sie ein **Panel**hinzu. Dieser **Bereich** bietet einen Hintergrund für den Text, den Sie in der Szene anzeigen werden.
5.  Klicken Sie im *Hierarchie Panel*mit der rechten Maustaste **auf den Bereich** **, und**fügen Sie ein **Text Objekt**hinzu. Wiederholen Sie den gleichen Prozess, bis Sie insgesamt vier UI-Textobjekte erstellt haben (Hinweis: Wenn Sie das erste "Text"-Objekt ausgewählt haben, können Sie einfach **"Strg +** d" drücken, um es zu duplizieren, bis vier vorhanden sind). 
6.  Wählen Sie für jedes **Text Objekt**die Option aus, und verwenden Sie die folgenden Tabellen, um die Parameter im *Inspektor-Panel*festzulegen.

    1. Für die Komponente *Rect Transform* :

        | Name                   | Transformation- *Position*             | Breite      | Flugh    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | "Mikrophonestatus Label"  | **X** -80 **Y** 90 **Z** 0         | 300        | 30        |
        | Azureresponselabel     | **X** -80 **Y** 30 **Z** 0         | 300        | 30        |
        | "Ditationlabel"         | **X** -80 **Y** -30 **Z** 0        | 300        | 30        |
        | Translationresultlabel | **X** -80 **Y** -90 **Z** 0        | 300        | 30        |


    2. Für die **Text-Komponente (Skript)** :


        | Name                   | Text               | Schrift Grad    |
        |:----------------------:|:------------------:|:------------:|
        | "Mikrophonestatus Label"  | Mikrofon Status: | 20           |
        | Azureresponselabel     | Azure-Webantwort | 20           |
        | "Ditationlabel"         |   Sie haben soeben Folgendes gesagt:   | 20           |
        | Translationresultlabel |    Übersetzt    | 20           |

        ![Geben Sie die entsprechenden Werte für die Benutzeroberflächen Bezeichnungen ein.](images/AzureLabs-Lab1-24.png)

    3. Legen Sie außerdem den Schrift Schnitt auf **Fett**formatiert. Dadurch wird der Text leichter lesbar.

        ![Fett Schrift.](images/AzureLabs-Lab1-25.png)

7.  Erstellen Sie für jedes *UI-Textobjekt* , das in [Kapitel 5](#chapter-5--create-the-results-class)erstellt wurde, *ein neues unter* geordnetes UI- **Textobjekt**. Diese untergeordneten Elemente zeigen die Ausgabe der Anwendung an. Erstellen *Sie* untergeordnete Objekte, indem Sie mit der rechten Maustaste auf das gewünschte übergeordnete Element klicken (z. b. " *mikrophonestatus Label*"), **und wählen Sie**dann **Benutzeroberfläche**
8.  Wählen Sie für jedes dieser untergeordneten Elemente die Option aus, und verwenden Sie die folgenden Tabellen, um die Parameter im Inspektor-Panel festzulegen.

    1. Für die Komponente **Rect Transform** :

        | Name                  | Transformation- *Position* | Breite      | Flugh    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | "Mikrophonestatustext"  | X 0 Y-30 Z 0          | 300        | 30        |
        | Azureresponabtext     | X 0 Y-30 Z 0          | 300        | 30        |
        | "Ditationtext"         | X 0 Y-30 Z 0          | 300        | 30        |
        | Translationresulttext | X 0 Y-30 Z 0          | 300        | 30        |

    2. Für die **Text-Komponente (Skript)** :

        | Name                  | Text          | Schrift Grad    |
        |:---------------------:|:-------------:|:------------:|
        | "Mikrophonestatustext"  |      ??       | 20           |
        | Azureresponabtext     |      ??       | 20           |
        | "Ditationtext"         |      ??       | 20           |
        | Translationresulttext |      ??       | 20           |

9. Wählen Sie als nächstes die Option "Center" für jede Textkomponente aus:

    ![Text ausrichten.](images/AzureLabs-Lab1-26.png)

10. Um sicherzustellen, dass die Text Objekte der untergeordneten **Benutzeroberfläche** leicht lesbar sind, ändern Sie Ihre *Farbe*. Klicken Sie hierzu auf die Leiste neben *Farbe*(derzeit "schwarz"). 

    ![Geben Sie entsprechende Werte für die Textausgaben der Benutzeroberfläche ein.](images/AzureLabs-Lab1-27.png)
 
11. Ändern Sie dann im neuen, kleinen *Farb* Fenster die hexadezimale *Farbe* in: **0032eaff**

    ![Aktualisieren Sie Farbe in blau.](images/AzureLabs-Lab1-28.png)
 
12. Im folgenden sehen Sie, wie die **Benutzeroberfläche** aussehen sollte.
    1.  Im *Hierarchie Panel*:

        ![Hierarchie in der bereitgestellten-Struktur.](images/AzureLabs-Lab1-29.png)

    2.  In den *Szenen* -und *Spiel Ansichten*:

        ![Die Szenen-und Spiel Ansichten in derselben Struktur haben.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a>Kapitel 5 – Erstellen der Ergebnis Klasse

Das erste Skript, das Sie erstellen müssen, ist die *Ergebnis* Klasse, die für die Bereitstellung einer Möglichkeit zum Anzeigen der Ergebnisse der Übersetzung verantwortlich ist. Die-Klasse speichert und zeigt Folgendes an: 

- Das Antwort Ergebnis von Azure.
- Der Status des Mikrofons. 
- Das Ergebnis der diktierung (Voice-to-Text).
- Das Ergebnis der Übersetzung.

So erstellen Sie diese Klasse: 

1.  Klicken Sie mit der rechten Maustaste im *Projekt Panel*, und erstellen Sie dann **> Ordner**. Benennen Sie den Ordner mit **Skripts**. 
 
    ![Erstellen Sie den Ordner Skripts.](images/AzureLabs-Lab1-31.png)

    ![Öffnen Sie den Ordner Skripts.](images/AzureLabs-Lab1-32.png)
 
2.  Wenn Sie den Ordner **Skripts** erstellen, doppelklicken Sie darauf, um ihn zu öffnen. Klicken Sie dann in diesem Ordner mit der rechten Maustaste auf, und wählen **C#** Sie dann **> Skript erstellen** aus. Benennen Sie die *Ergebnisse*des Skripts. 

    ![Erstellen Sie das erste Skript.](images/AzureLabs-Lab1-33.png)
 
3.  Doppelklicken Sie auf das neue *Ergebnis* Skript, um es in **Visual Studio**zu öffnen.
4.  Fügen Sie die folgenden Namespaces ein:

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  Fügen Sie in der-Klasse die folgenden Variablen ein:

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  Fügen Sie dann die *Awa()* -Methode hinzu, die aufgerufen wird, wenn die-Klasse initialisiert wird. 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  Fügen Sie abschließend die Methoden hinzu, die für die Ausgabe der verschiedenen Ergebnisinformationen an die Benutzeroberfläche verantwortlich sind. 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.

## <a name="chapter-6--create-the-microphonemanager-class"></a>Kapitel 6 – Erstellen der Klasse " *mikrophonemanager* "

Die zweite Klasse, die Sie erstellen, ist der *Mikro phonemanager*.

Diese Klasse ist für Folgendes zuständig:

- Erkennen des Aufzeichnungs Geräts, das an das Headset oder den Computer angeschlossen ist (je nachdem, welches der Standard ist).
- Erfassen Sie das Audiomaterial (Voice), und speichern Sie es als Zeichenfolge.
- Nachdem die Stimme angehalten wurde, übermitteln Sie die Diktat an die Translator-Klasse.
- Hosten Sie eine Methode, die die sprach Erfassung bei Bedarf abbrechen kann.

So erstellen Sie diese Klasse: 
1.  Doppelklicken Sie auf den Ordner " **Scripts** ", um ihn zu öffnen. 
2.  Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf  **C# > Skript erstellen**. Nennen Sie das Skript " *mikrophonemanager*". 
3.  Doppelklicken Sie auf das neue Skript, um es in Visual Studio zu öffnen.
4.  Aktualisieren Sie die Namespaces, sodass Sie am Anfang der Klasse " *mikrophonemanager* " dem folgenden entsprechen:

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  Fügen Sie dann die folgenden Variablen in der Klasse " *mikrophonemanager* " hinzu:

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  Der Code für die Methoden " *Awake ()* " und " *Start ()* " muss nun hinzugefügt werden. Diese werden aufgerufen, wenn die-Klasse initialisiert:

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  Sie können die *Update ()* -Methode *Löschen* , da Sie von dieser Klasse nicht verwendet wird.
8.  Nun benötigen Sie die Methoden, die die APP verwendet, um die sprach Erfassung zu starten und anzuhalten, und Sie *an die* konvertiererklasse weiterzuleiten, die Sie bald erstellen werden. Kopieren Sie den folgenden Code, und fügen Sie ihn unterhalb der Methode " *Start ()* " ein.

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > Obwohl diese Anwendung diese Anwendung nicht nutzt, wurde auch die *stopcapturingaudio()* -Methode bereitgestellt, wenn Sie die Möglichkeit zum Beenden der Erfassung von Audiodaten in Ihrer Anwendung implementieren möchten.

9.  Nun müssen Sie einen Diktat Handler hinzufügen, der aufgerufen wird, wenn die Stimme angehalten wird. Diese Methode übergibt dann den vorgeschriebenen Text an die *Translator* -Klasse.

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. Stellen Sie sicher, dass Sie die Änderungen in Visual Studio speichern, bevor Sie zu Unity zurückkehren.

> [!WARNING]  
> An dieser Stelle bemerken Sie einen Fehler, der im Konsolen Panel des *Unity-Editors* angezeigt wird ("der Name ' Translator ' ist nicht vorhanden..."). Der Grund hierfür ist, dass der Code auf die *Translator* -Klasse verweist, die Sie im nächsten Kapitel erstellen werden.

## <a name="chapter-7--call-to-azure-and-translator-service"></a>Kapitel 7 – Anrufen von Azure und Translator-Dienst

Das letzte Skript, das Sie erstellen müssen, ist die *Translator* -Klasse. 

Diese Klasse ist für Folgendes zuständig:

-   Authentifizieren der APP mit *Azure*in Exchange für ein Authentifizierungs **Token**.
-   Verwenden Sie das **auth-Token** , um Text (der von der Klasse " *mikrophonemanager* " empfangen wird) zu übermitteln.
-   Empfangen Sie das übersetzte Ergebnis, und übergeben Sie es an die *Ergebnis* Klasse, um Sie in der Benutzeroberfläche zu visualisieren.

So erstellen Sie diese Klasse: 
1.  Wechseln Sie zum Ordner " **Scripts** ", den Sie zuvor erstellt haben. 
2.  Klicken Sie im **Projekt Panel**mit der rechten Maustaste, und **Erstellen Sie > C# Skript**. Ruft *den Skript*Konvertierer auf.
3.  Doppelklicken Sie auf das *neue* Konvertierungs Skript, um es in **Visual Studio**zu öffnen.
4.  Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Fügen Sie dann die folgenden Variablen in die *Translator* -Klasse ein:

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - Die Sprachen, die in die Sprachen-Aufzählung **eingefügt werden,** sind nur Beispiele. Wenn Sie möchten, können Sie weitere hinzufügen. die [API unterstützt mehr als 60 Sprachen](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (einschließlich Klingonischer Sprache).
    > - Es gibt eine [interaktive Seite, die die verfügbaren Sprachen abdeckt](https://www.microsoft.com/translator/business/languages/), aber beachten Sie, dass die Seite nur dann funktioniert, wenn die Website Sprache auf "" festgelegt ist (und die Microsoft-Website wahrscheinlich an Ihre native Sprache umgeleitet wird). Sie können die Website Sprache am unteren Rand der Seite oder durch Ändern der URL ändern.
    > - Der **authorizationkey** -Wert im obigen Code Ausschnitt muss der **Schlüssel** sein, den Sie erhalten haben, als Sie das *Azure-Textübersetzungs-API*abonniert haben. Dies wurde in [Kapitel 1](#chapter-1--the-azure-portal)beschrieben.

6.  Der Code für die Methoden " *Awake ()* " und " *Start ()* " muss nun hinzugefügt werden. 
7.  In diesem Fall ruft der Code *Azure* mithilfe des Autorisierungs Schlüssels auf, um ein *Token*abzurufen.

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > Das Token läuft nach 10 Minuten ab. Abhängig vom Szenario für Ihre APP müssen Sie möglicherweise den gleichen Coroutine-Rückruf mehrmals durchführen.

8.  Die Coroutine zum Abrufen des Tokens lautet wie folgt:

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > Wenn Sie den Namen der IEnumerator-Methode **getdekencoroutine ()** bearbeiten, müssen Sie die " *startcoroutine* "-und " *stopcoroutine* "-aufrufzeichenfolgen-Werte im obigen Code aktualisieren. Um eine bestimmte *Coroutine*zu verhindern, müssen Sie gemäß der [Unity-Dokumentation](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html)die Zeichen folgen Wert-Methode verwenden.

9.  Fügen Sie als nächstes das Coroutine-Objekt (mit einer "Support"-streammethode direkt unterhalb) hinzu, um die Übersetzung des von der Klasse " *mikrophonemanager* " empfangenen Texts zu erhalten. Dieser Code erstellt eine Abfrage Zeichenfolge, die an den *Azure-Textübersetzungs-API*gesendet werden soll, und verwendet dann die interne Unity unitywebrequest-Klasse, um einen get-Befehl mit der Abfrage Zeichenfolge an den Endpunkt zu senden. Das Ergebnis wird dann verwendet, um die Übersetzung im results-Objekt festzulegen. Der folgende Code zeigt die-Implementierung:

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.

## <a name="chapter-8--configure-the-unity-scene"></a>Kapitel 8 – Konfigurieren der Unity-Szene

1.  Klicken Sie im Unity-Editor auf die *Ergebnis* Klasse, und ziehen Sie Sie *aus* dem Ordner **Scripts** auf das **Hauptkamera** Objekt im Bereich *Hierarchie*.
2.  Klicken Sie auf die **Hauptkamera** , und sehen Sie sich den Bereich *Inspector*an. Sie werden feststellen, dass in der neu hinzugefügten *Skript* Komponente vier Felder mit leeren Werten vorhanden sind. Dies sind die Ausgabe Verweise auf die Eigenschaften im Code. 
3.  Ziehen Sie die entsprechenden **Text** Objekte aus dem Bereich *Hierarchie* in diese vier Slots, wie in der folgenden Abbildung dargestellt.

    ![Aktualisieren Sie die Ziel Verweise mit den angegebenen Werten.](images/AzureLabs-Lab1-34.png)
  
4.  Klicken und ziehen Sie anschließend die *Translator* -Klasse aus dem Ordner **Scripts** auf das **Hauptkamera** Objekt im Bereich *Hierarchie*. 
5.  Klicken und ziehen Sie dann die Klasse " *mikrophonemanager* " aus dem Ordner " **Scripts** " auf das **Hauptkamera** Objekt im *Hierarchie Panel*. 
6.  Klicken Sie abschließend auf die **Hauptkamera** , und sehen Sie sich den Bereich *Inspector*an. Sie werden feststellen, dass Sie in dem von ihnen gezogenen Skript zwei Dropdown Felder haben, die es Ihnen ermöglichen, die Sprachen festzulegen.
 
    ![Stellen Sie sicher, dass die beabsichtigten Übersetzungs Sprachen eingegeben werden.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a>Kapitel 9 – testen in gemischter Realität

An diesem Punkt müssen Sie testen, ob die Szene ordnungsgemäß implementiert wurde.

Stellen Sie Folgendes sicher:

- Alle in [Kapitel 1](#chapter-1--the-azure-portal) erwähnten Einstellungen sind richtig festgelegt. 
- Die Skripts " *results*", " *Translator*" und " *mikrophonemanager*" werden an das **Hauptkamera** Objekt angefügt. 
- Sie haben ihren *Azure Textübersetzungs-API* Service- **Schlüssel** *innerhalb der Variablen* " **authorizationkey** " innerhalb des Konvertierungs Skripts platziert.  
- Alle Felder im Hauptbereich der *Kamera Inspektor* sind ordnungsgemäß zugewiesen.
- Ihr Mikrofon funktioniert beim Ausführen Ihrer Szene (wenn nicht, überprüfen Sie, ob Ihr angefügtes Mikrofon das *Standard* Gerät ist, und dass Sie [es in Windows ordnungsgemäß eingerichtet](https://support.microsoft.com/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)haben).

Sie können das immersive Headset testen, indem Sie die **Wiedergabe** Schaltfläche im *Unity-Editor*drücken.
Die APP sollte über das angefügte immersive Headset funktionieren.

> [!WARNING]  
> Wenn in der Unity-Konsole eine Fehlermeldung angezeigt wird, dass das Standardaudiogerät geändert wird, funktioniert die Szene möglicherweise nicht wie erwartet. Der Grund hierfür ist die Art und Weise, wie das Mixed Reality-Portal mit integrierten Mikrofonen für Headsets umgeht, auf denen es sich befindet. Wenn dieser Fehler angezeigt wird, halten Sie die Szene einfach an, und starten Sie Sie erneut, und die Dinge sollten erwartungsgemäß funktionieren.

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a>Kapitel 10 – Erstellen der UWP-Lösung und querladen auf dem lokalen Computer

Alles, was für den Unity-Abschnitt dieses Projekts erforderlich ist, ist nun abgeschlossen, sodass es an der Zeit ist, Sie aus Unity zu erstellen.

1.  Navigieren Sie zu **Buildeinstellungen**: **Datei > Buildeinstellungen...**
2.  Klicken Sie im Fenster " **Buildeinstellungen** " auf " **Erstellen**".

    ![Erstellen Sie die Unity-Szene.](images/AzureLabs-Lab1-36.png)
  
3.  Wenn dies nicht bereits geschehen ist, Tick **Unity C# -Projekte**.
4.  Klicken Sie auf **Erstellen**. Unity startet ein *Datei-Explorer* -Fenster, in dem Sie einen Ordner erstellen und auswählen müssen, in dem die App erstellt wird. Erstellen Sie diesen Ordner jetzt, und nennen Sie ihn " *App*". Klicken Sie dann mit ausgewähltem *App* -Ordner auf **Ordner auswählen**. 
5.  Unity startet das Projekt in den *App* -Ordner. 
6.  Nachdem die Erstellung von Unity abgeschlossen ist (Dies kann einige Zeit in Anspruch nehmen), wird ein *Datei-Explorer* -Fenster am Speicherort des Builds geöffnet (überprüfen Sie die Taskleiste, da Sie möglicherweise nicht immer über Ihrem Fenster angezeigt wird, sondern Sie über das Hinzufügen eines neuen Fensters benachrichtigt).

## <a name="chapter-11--deploy-your-application"></a>Kapitel 11 – Bereitstellen der Anwendung

So stellen Sie die Anwendung bereit:

1.  Navigieren Sie zu Ihrem neuen Unity-Build ( *App* -Ordner), und öffnen Sie die Projektmappendatei mit *Visual Studio*.
2.  Wählen Sie in der Projektmappenkonfiguration **Debuggen**.
3.  Wählen Sie auf der Projektmappenplattform die Option **x86**, **lokaler Computer**aus. 

    > Für Microsoft hololens ist es möglicherweise einfacher, dies auf den *Remote*Computer festzulegen, damit Sie nicht auf Ihren Computer über das Team verfügen. Allerdings müssen Sie auch die folgenden Schritte ausführen:
    > - Informieren Sie sich über die **IP-Adresse** ihrer hololens. Sie finden diese in den *Einstellungen > Netzwerk & Internet > Wi-Fi-> Erweiterte Optionen*; die IPv4-Adresse ist die Adresse, die Sie verwenden sollten. 
    > - Stellen Sie sicher, dass der *Entwicklermodus* **auf**dem in den *Einstellungen > Update & Sicherheits > für Entwickler*gefunden.

    ![Stellen Sie die Lösung aus Visual Studio bereit.](images/AzureLabs-Lab1-37.png)
    
 
4.  Wechseln Sie zum **Menü Erstellen** , und klicken Sie auf Lösung bereitstellen, um die Anwendung per querladen auf Ihren PC zu **verlagern** .
5.  Ihre APP sollte nun in der Liste der installierten apps angezeigt werden, die gestartet werden können.
6.  Nach dem Start werden Sie von der APP aufgefordert, den Zugriff auf das Mikrofon zu autorisieren. Stellen Sie sicher, dass Sie auf **Ja** klicken.
7.  Jetzt können Sie mit der Übersetzung beginnen!

## <a name="your-finished-translation-text-api-application"></a>Die fertige Übersetzungs Text-API-Anwendung

Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die die Text-API von Azure Translation zum Konvertieren von Sprache in übersetzten Text nutzt.

![Endprodukt.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a>Bonus Übungen

### <a name="exercise-1"></a>Übung 1

Können Sie der APP Text-zu-Sprache-Funktionen hinzufügen, sodass der zurückgegebene Text gesprochen wird?

### <a name="exercise-2"></a>Übung 2

Ermöglicht es dem Benutzer, die Quell-und Ausgabesprachen ("from" und "to") innerhalb der APP selbst zu ändern, sodass die APP nicht jedes Mal neu erstellt werden muss, wenn Sie die Sprachen ändern möchten.
