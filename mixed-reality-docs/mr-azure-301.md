---
title: MR und Azure 301 - Übersetzung
description: Führen Sie diesen Kurs erfahren, wie Sie die Azure Textübersetzungs-API in einer mixed Reality-Anwendung zu implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorials, api, Translator-Text, Hololens, immersive vr
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59596315"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

<br>

# <a name="mr-and-azure-301-language-translation"></a>MR und Azure 301: Übersetzung von Sprachen

In diesem Kurs lernen Sie, wie eine mixed Reality-Anwendung mithilfe von Azure Cognitive Services, mit der Textübersetzungs-API beinhaltet hinzugefügt werden.

![Endprodukt](images/AzureLabs-Lab1-00.png)

Die Textübersetzungs-API ist eine Übersetzung Dienst, der nahezu in Echtzeit arbeitet. Der Dienst ist Cloud-basierte, und, über einen REST-API-Aufruf, eine app kann der maschinellen Übersetzung neuronale verwenden, um Text in eine andere Sprache übersetzen. Weitere Informationen finden Sie auf die [Textübersetzungs-API von Azure-Seite](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).

Nach Abschluss dieses Kurses verfügen Sie über ein mixed Reality-Anwendung die können die folgenden Schritte ausführen:

1.  Der Benutzer wird in ein Mikrofon an eine immersive (VR) Kopfhörer angeschlossen (oder das integrierte Mikrofon von HoloLens) sprechen.
2.  Die app wird das Diktieren erfassen und an den Azure Textübersetzungs-API senden.
3.  Die Verschiebung dazu wird in einer einfachen Benutzeroberfläche-Gruppe in der Unity-Szene angezeigt werden.

In diesem Kurs erfahren Sie, wie zum Abrufen der Ergebnisse von der Translator-Dienst in eine Unity-basierten Anwendung. Sie werden sich entscheiden, ob Sie diese Konzepte, die Sie erstellen eine benutzerdefinierte Anwendung zuweisen.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td> MR und Azure 301: Übersetzung von Sprachen</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Während dieser Kurs in erster Linie für immersive Windows Mixed Reality (VR)-Headsets ausgerichtet ist, können Sie auch anwenden, was Sie in diesem Kurs, Microsoft HoloLens lernen. Wie Sie den Kurs halten, sehen Anmerkungen zu dieser Version auf Änderungen Sie möglicherweise zur Unterstützung von HoloLens einsetzen müssen. Wenn Sie HoloLens verwenden zu können, werden Sie einige Echo während der Sprachaufnahme feststellen.

## <a name="prerequisites"></a>Vorraussetzungen

> [!NOTE]
> In diesem Tutorial wurde für Entwickler mit Erfahrung mit Unity entwickelt und C#. Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Mai 2018) überprüft wurde. Sie können zur Verwendung der neuesten Software, wie in der [Installieren der Tools](install-the-tools.md) Artikel, obwohl es nicht davon ausgegangen werden soll, dass die Informationen in diesem Kurs perfekt was finden Sie in der neueren Software entspricht als die unten Angaben aufgeführten .

Es wird empfohlen, die folgende Hardware und Software für diesen Kurs:

- Eine Entwicklungs-PC [kompatibel mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für immersive (VR) Kopfhörer-Entwicklung
- [Windows 10 Fall Creators Update (oder höher) mit der Entwicklermodus aktiviert ist](install-the-tools.md#installation-checklist)
- [Das neueste Windows 10-SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Ein [immersive Windows Mixed Reality (VR)-Kopfhörer](immersive-headset-hardware-details.md) oder [Microsoft HoloLens](hololens-hardware-details.md) mit Entwicklermodus aktiviert ist
- Eine Reihe von Kopfhörer mit ein eingebautes Mikrofon verfügen (wenn der Kopfhörer nicht über eine integrierte mic und die Lautsprecher verfügt)
- Zugriff auf das Internet für den Abruf von Azure-Setup und Übersetzung

## <a name="before-you-start"></a>Bevor Sie beginnen

- Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).
- Der Code in diesem Tutorial können Sie aus dem Mikrofon-Standardgerät, die mit dem PC verbundenes aufzeichnen. Stellen Sie sicher, dass das Mikrofon-Standardgerät an das Gerät festgelegt ist, die Sie verwenden, um Ihre Stimme erfassen möchten.
- Damit können Ihren PC Diktat zu aktivieren, wechseln Sie zu **Einstellungen > Datenschutz >-Sprache, Freihand & Eingabe** , und wählen Sie die Schaltfläche mit den **Aktivieren von Sprachdienste und Typisierung Vorschläge**.
- Wenn Sie ein Mikrofon und Kopfhörer angeschlossen, um (oder in integriert) verwenden Ihre Kopfhörer, stellen Sie sicher, dass die Option "Ich meine Kopfhörer wear, wechseln Sie zur Kopfhörer-mic" ist im aktiviert **Einstellungen > Mixed Reality > Audio- und Spracherkennung**.

   ![Mixed Reality-Einstellungen](images/AzureLabs-Lab1-00-5.png)

   ![Mikrofon-Einstellung](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> Denken Sie daran, dass wenn Sie für eine immersive Kopfhörer für diese Umgebung entwickeln, Audioausgabe Geräteprobleme auftreten können. Dies ist aufgrund eines Problems mit Unity, die in höheren Versionen von Unity (Unity 2018.2) behoben wird. Das Problem wird verhindert, dass Unity das Standard-Audioausgabegerät zur Laufzeit ändern. Können dies umgehen stellen Sie sicher, dass Sie die oben genannten Schritte abgeschlossen haben, und schließen und erneut im Editor öffnen, wenn dieses Problem selbst präsentiert.

## <a name="chapter-1--the-azure-portal"></a>Kapitel 1 – Azure-Portal

Um die Translator-API von Azure zu verwenden, müssen Sie so konfigurieren Sie eine Instanz des Diensts, der für Ihre Anwendung verfügbar gemacht werden.

1.  Melden Sie sich bei der [Azure-Portal](https://portal.azure.com).

    > [!NOTE]
    > Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen. Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.

2.  Sobald Sie angemeldet sind, klicken Sie auf **neu** in der oberen linken Ecke, und suchen Sie nach "Textübersetzungs-API". Wählen Sie **geben**.

    ![Neue Ressource](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > Das Wort **neu** wurden möglicherweise durch ersetzt **erstellen Sie eine Ressource**, in neueren-Portalen.

3.  Die neue Seite bietet eine Beschreibung der *Textübersetzungs-API* Service. Unten links auf dieser Seite die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.

    ![Translator-Text-API-Dienst erstellen](images/AzureLabs-Lab1-03.png)

4.  Nachdem Sie auf geklickt haben **erstellen**:

    1. Fügen Sie Ihre bevorzugte **Namen** für diese Dienstinstanz.
    2. Wählen Sie einen geeigneten **Abonnement**.
    3. Wählen Sie die **Tarif** für Sie geeignet ist, ist dies die erste Zeit in die Erstellung einer *Translator-Text-Dienst*, freier-Tarif (mit dem Namen F0) für Sie verfügbar sein sollen.
    4. Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle zu bewahren, an die Azure-Dienste unter einer allgemeinen Ressourcengruppe mit einem einzelnen Projekt (z. B. z. B. diesen Labs) verknüpft ist).

        > Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, bitte [finden Sie im Artikel der Resource-Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Bestimmen der **Speicherort** für Ihre Ressourcengruppe aus (Wenn Sie eine neue Ressourcengruppe erstellen). Der Speicherort würde idealerweise in der Region sein, in dem die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.
    6. Sie müssen auch bestätigen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.
    7. Wählen Sie **Erstellen** aus.

        ![Wählen Sie die Schaltfläche "erstellen".](images/AzureLabs-Lab1-04.png)

5.  Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.
6.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt. 

    ![Benachrichtigung über Azure Service-Erstellung](images/AzureLabs-Lab1-05.png)

7.  Klicken Sie auf die Benachrichtigung, um Ihre neue Dienstinstanz zu untersuchen. 

    ![Wechseln Sie zur Ressource Popup.](images/AzureLabs-Lab1-06.png)

8.  Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen. Sie werden auf die neue Instanz der Translator Text-API-Dienst weitergeleitet. 

    ![Translator-Text-API-Dienst-Seite](images/AzureLabs-Lab1-07.png)

9.  In diesem Tutorial müssen Ihre Anwendung Aufrufe an Ihren Dienst, was durch die Verwendung von Subscription-Key Ihres Diensts erfolgt. 
10. Aus der *Schnellstart* auf der Seite Ihrer *Textübersetzungs* -Dienst navigieren, mit dem ersten Schritt *nehmen Sie Ihre Schlüssel*, und klicken Sie auf **Schlüssel** (Sie können auch erreichen Sie dies, indem Sie auf den blauen Link Schlüssel befindet sich im Navigationsmenü Dienste durch ein Schlüsselsymbol gekennzeichnet). Dadurch wird angezeigt, den Dienst *Schlüssel*.
11. Erstellen Sie eine Kopie eines der angezeigten Schlüssel wird, da Sie dies später in Ihr Projekt benötigen. 

## <a name="chapter-2--set-up-the-unity-project"></a>Kapitel 2: Einrichten von Unity-Projekts

Richten Sie ein und Testen Sie Ihrer mixed Reality immersive Kopfhörer.

> [!NOTE]
> Sie benötigen für diesen Kurs nicht während der Übertragung Controller. Wenn Sie die Einrichtung einer immersive Kopfhörer unterstützen müssen, wenden Sie [gehen Sie folgendermaßen vor](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit mixed Reality und, daher ist eine gute Vorlage für andere Projekte:

1.  Open *Unity* , und klicken Sie auf **neu**. 

    ![Starten Sie die neues Unity-Projekt.](images/AzureLabs-Lab1-08.png)

2.  Sie müssen nun einen Namen für die Unity-Projekt bereitstellen. Fügen Sie **MR_Translation**. Stellen Sie sicher, dass der Projekttyp nastaven NA hodnotu **3D**. Legen Sie die *Speicherort* auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser). Klicken Sie auf **projekterstellung**.

    ![Die Details für die neue Unity-Projekt.](images/AzureLabs-Lab1-09.png)

3.  Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**. Wechseln Sie zu **Bearbeiten > Voreinstellungen** und navigieren Sie dann im neuen Fenster zu **externe Tools**. Änderung **externen Skript-Editors** zu **Visual Studio 2017**. Schließen der **Voreinstellungen** Fenster.

    ![Aktualisieren Sie die Skript-Editor-Einstellung.](images/AzureLabs-Lab1-10.png)

4.  Öffnen Sie als Nächstes **Datei > Buildeinstellungen** , und wechseln von der Plattform bereitgestellten **universelle Windows-Plattform**, durch Klicken auf die **Plattform wechseln** Schaltfläche.

    ![Fenster "Einstellungen", Switch-Plattform für die UWP zu erstellen.](images/AzureLabs-Lab1-11.png)

5.  Wechseln Sie zu **Datei > Buildeinstellungen** und stellen Sie sicher, dass:

    1. **Geräte** nastaven NA hodnotu **einem beliebigen Gerät**.

        > Legen Sie für Microsoft HoloLens, **Zielgerät** zu *HoloLens*.

    2. **Buildtyp** nastaven NA hodnotu **D3D**
    3. **SDK** nastaven NA hodnotu **zuletzt installierte**
    4. **Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**
    5. **Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**
    6. Die Szene speichern und mit dem Build hinzugefügt werden.

        1. Hierzu **öffnen Szenen hinzufügen**. Ein Speichern Fenster wird angezeigt.

            ![Klicken Sie auf, öffnen im Hintergrund-Schaltfläche "hinzufügen"](images/AzureLabs-Lab1-12.png)

        2. Erstellen einen neuen Ordner für, und alle zukünftigen, Szene, klicken Sie dann auf die **neuer Ordner** Schaltfläche zum Erstellen eines neuen Ordners, nennen Sie sie **Szenen**.

            ![Erstellen Sie neue Ordner "Scripts"](images/AzureLabs-Lab1-13.png)

        3. Öffnen Sie den neu erstellten **Szenen** Ordner, und klicken Sie dann in der *Dateiname*: Textfeld **MR_TranslationScene**, drücken Sie dann die **speichern**.

            ![Geben Sie neue Szene einen Namen zu.](images/AzureLabs-Lab1-14.png)

            > Beachten Sie, speichern Sie Ihre Unity-Szenen in den *Assets* Ordner, wie sie mit der Unity-Projekt verbunden sein müssen. Erstellen den Ordner im Hintergrund (und andere ähnliche Ordner), wird eine typische Möglichkeit Strukturieren eines Unity-Projekts ist.

    7. Die Einstellungen im verbleibenden *Buildeinstellungen*, sollte jetzt als Standard bleiben.

6. In der *Buildeinstellungen* Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dadurch wird den entsprechenden Bereich geöffnet, im Bereich, in dem die *Inspektor* befindet. 

    ![Öffnen der playereinstellungen.](images/AzureLabs-Lab1-15.png)

7. In diesem Bereich sind müssen einige Einstellungen überprüft werden:

    1. In der **Weitere Einstellungen** Registerkarte:

        1. **Scripting Runtime Version** muss **stabile** (.NET 3.5 entspricht).
        2. **Back-End-Scripting** muss **.NET**
        3. **API-Kompatibilitätsebene** muss **.NET 4.6**

            ![Andere Einstellungen zu aktualisieren.](images/AzureLabs-Lab1-16.png)
      
    2. In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:

        1. **InternetClient**
        2. **Microphone**

            ![Veröffentlichungseinstellungen werden aktualisiert.](images/AzureLabs-Lab1-17.png)

    3. Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality-SDK**  hinzugefügt wird.

        ![Aktualisieren Sie die X-R-Einstellungen.](images/AzureLabs-Lab1-18.png)

8.  Im **Buildeinstellungen**, *Unity C# Projekte* nicht mehr abgeblendet ist, aktivieren Sie das Kontrollkästchen neben dieser. 
9.  Schließen Sie das Fenster "erstellen".
10. Speichern Sie Ihre Szene und das Projekt (**Datei > Speichern SZENE / FILE > Speichern Projekt**).

## <a name="chapter-3--main-camera-setup"></a>Kapitel 3 – Main Camera-setup

> [!IMPORTANT]
> Wenn Sie, überspringen möchten der *Unity einrichten* -Komponente dieser Kurs, und weiterhin direkt in Code, gerne [Herunterladen dieser .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), importieren Sie es in Ihr Projekt als eine [ *Custom Package*](https://docs.unity3d.com/Manual/AssetPackages.html), und klicken Sie dann eine Fortsetzung [Kapitel 5](#chapter-5--create-the-results-class). Sie müssen immer noch ein Unity-Projekt zu erstellen.

1.  In der *Hierarchie Bereich*, sehen Sie ein Objekt namens **Main Camera**, diesem Objekt dargestellten Ihr "Head" Sicht aus, wenn Sie "in" Ihrer Anwendung sind.
2.  Wählen Sie im Unity-Dashboard vor Ihnen die **Main Camera "gameobject"**. Sie werden feststellen, dass die *Inspektor Bereich* (in der Regel nach rechts im Dashboard gefunden) zeigt die verschiedenen Komponenten, die *"gameobject"*, mit *transformieren* oben, gefolgt von *Kamera*, und einige andere Komponenten. Sie müssen die Transformation der Main-Kamera, zurücksetzen, damit sie richtig positioniert ist.
3.  Wählen Sie zu diesem Zweck die **Zahnradsymbol** Symbol neben der Kamera *transformieren* -Komponente, und wählen **zurücksetzen**. 

    ![Setzen Sie die Main Camera-Transformation zurück.](images/AzureLabs-Lab1-19.png)
 
4.  Die *transformieren* Komponente sollte dann wie folgt aussehen:

    1. Die *Position* nastaven NA hodnotu **0, 0, 0**
    2. *Drehung* nastaven NA hodnotu **0, 0, 0**
    3. Und *Skalierung* nastaven NA hodnotu **1, 1, 1**

        ![Transformieren Sie die Informationen für Kamera](images/AzureLabs-Lab1-20.png)

5.  Als Nächstes mit der **Main Camera** Objekt ausgewählt haben, finden Sie unter den **Komponente hinzufügen** Schaltfläche am Ende der *Inspektor Bereich*. 
6.  Klicken Sie auf diese Schaltfläche, und suchen (entweder durch das eingeben *Audio Source* in das Suchfeld ein, oder Navigieren in den Abschnitten) für die Komponente mit dem Namen **Audio Source** wie unten dargestellt, und wählen Sie ihn (drücken Sie die EINGABETASTE auf Außerdem funktioniert).
7.  Ein *Audio Source* Komponente hinzugefügt werden wird die **Main Camera**, wie unten dargestellt.

    ![Fügen Sie eine Audio Source-Komponente hinzu.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > Für Microsoft HoloLens, müssen Sie auch Folgendes ändern die sind Teil der **Kamera** -Komponente auf Ihre **Main Camera**:
    > - **Flags zu löschen:** Volltonfarbe entspricht.
    > - **Hintergrund** "Schwarz, Alpha 0" – Hex-Color: #00000000.

## <a name="chapter-4--setup-debug-canvas"></a>Kapitel 4 – Setup-Debug-Canvas

Um die Eingabe und Ausgabe der Übersetzung anzuzeigen, muss eine einfache Benutzeroberfläche erstellt werden. Für diesen Kurs erstellen Sie eine Canvas-UI-Objekt, mit mehreren 'Text'-Objekten, um die Daten anzuzeigen.

1.  Mit der rechten Maustaste in einen leeren Bereich des der *Hierarchie Bereich*unter **UI**, Hinzufügen einer **Canvas**.

    ![Fügen Sie neue Canvas-UI-Objekt hinzu.](images/AzureLabs-Lab1-22.png)

2.  Mit dem Canvas-Objekt, das ausgewählt ist, in der *Inspektor Bereich* (innerhalb der Komponente "Canvas"), ändern Sie **Rendermodus** zu **Raum der Welt**. 
3.  Als Nächstes ändern Sie die folgenden Parameter in der *Inspektor Bereichs Rect Transformation*:

    1. *POS* -  **X** 0 **Y** 0 **Z** 40
    2. *Breite* – 500
    3. *Höhe* – 300
    4. *Scale* - **X** 0.13 **Y** 0.13  **Z** 0.13

        ![Aktualisieren Sie die Rect-Transformation für die Canvas.](images/AzureLabs-Lab1-23.png)
 
4.  Klicken Sie mit der rechten Maustaste auf die **Canvas** in die *Hierarchie Bereich*unter **UI**, und fügen eine **Bereich**. Dies **Bereich** bieten einen Hintergrund auf den Text an, die Sie in der Szene anzeigen lassen.
5.  Klicken Sie mit der rechten Maustaste auf die **Bereich** in die *Hierarchie Bereich*unter **UI**, und fügen eine **Textobjekt**. Wiederholen Sie den gleichen Vorgang aus, bis Sie insgesamt vier Benutzeroberflächentext-Objekte erstellt haben (Hinweis: Wenn Sie das erste 'Text'-Objekt, das ausgewählt haben, können Sie einfach eine drücken **"Strg" + hatte "**, duplizieren, bevor Sie vier insgesamt haben). 
6.  Für jede **Textobjekt**, wählen Sie ihn, und verwenden Sie die folgenden Tabellen die Parameter fest, der *Inspector-Bereich*.

    1. Für die *Rect-Transformation* Komponente:

        | Name                   | Transformieren - *Position*             | Breite      | Höhe    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | MicrophoneStatusLabel  | **X** -80 **Y** 90 **Z** 0         | 300        | 30        |
        | AzureResponseLabel     | **X** -80 **Y** 30 **Z** 0         | 300        | 30        |
        | DictationLabel         | **X** -80 **Y** -30 **Z** 0        | 300        | 30        |
        | TranslationResultLabel | **X** -80 **Y** -90 **Z** 0        | 300        | 30        |


    2. Für die **Text (Skript)** Komponente:


        | Name                   | Text               | Schriftgrad    |
        |:----------------------:|:------------------:|:------------:|
        | MicrophoneStatusLabel  | Mikrofon-Status: | 20           |
        | AzureResponseLabel     | Azure-Web-Antwort | 20           |
        | DictationLabel         |   Sie gerade gesagt haben:   | 20           |
        | TranslationResultLabel |    Übersetzung:    | 20           |

        ![Geben Sie die entsprechenden Werte für die UI-Bezeichnungen.](images/AzureLabs-Lab1-24.png)

    3. Stellen Sie außerdem den Schriftschnitt **fett**. Dadurch wird den Text leichter lesbar zu machen.

        ![Fette Schriftart an.](images/AzureLabs-Lab1-25.png)

7.  Für jede *Benutzeroberflächentext Objekt* in erstellt [Kapitel 5](#chapter-5--create-the-results-class), erstellen Sie ein neues *untergeordneten* **Benutzeroberflächentext Objekt**. Diese untergeordneten Elemente werden die Ausgabe der Anwendung angezeigt. Erstellen Sie *untergeordneten* Objekte durch einen Rechtsklick auf die vorgesehene übergeordnete Element (z. B. *MicrophoneStatusLabel*) und wählen Sie dann **UI** und wählen Sie dann **Text**.
8.  Für jedes dieser untergeordneten Steuerelemente, wählen Sie ihn, und verwenden Sie die folgenden Tabellen die Parameter im Bereich Inspector fest.

    1. Für die **Rect-Transformation** Komponente:

        | Name                  | Transformieren - *Position* | Breite      | Höhe    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | MicrophoneStatusText  | X 0 Y -30 Z 0          | 300        | 30        |
        | AzureResponseText     | X 0 Y -30 Z 0          | 300        | 30        |
        | DictationText         | X 0 Y -30 Z 0          | 300        | 30        |
        | TranslationResultText | X 0 Y -30 Z 0          | 300        | 30        |

    2. Für die **Text (Skript)** Komponente:

        | Name                  | Text          | Schriftgrad    |
        |:---------------------:|:-------------:|:------------:|
        | MicrophoneStatusText  |      ??       | 20           |
        | AzureResponseText     |      ??       | 20           |
        | DictationText         |      ??       | 20           |
        | TranslationResultText |      ??       | 20           |

9. Wählen Sie dann die Option zur Ausrichtung "Centre" für jede Textkomponente ein:

    ![Ausrichten von Text.](images/AzureLabs-Lab1-26.png)

10. Um sicherzustellen, dass die **untergeordneten Benutzeroberflächentext** Objekte sind einfach zu lesen, ändern Sie ihre *Farbe*. Zu diesem Zweck klicken Sie auf der Leiste (derzeit "Schwarz") weiter, um *Farbe*. 

    ![Geben Sie die entsprechenden Werte für die UI-Text-Ausgaben.](images/AzureLabs-Lab1-27.png)
 
11. Klicken Sie auf das neue, kleine, *Farbe* Ändern der *Hexadezimalfarbe* auf: **0032EAFF**

    ![Aktualisieren Sie die Farbe Blau.](images/AzureLabs-Lab1-28.png)
 
12. Im folgenden finden Sie die **UI** aussehen sollte.
    1.  In der *Hierarchie Bereich*:

        ![Hierarchie in der angegebenen Struktur aufweisen.](images/AzureLabs-Lab1-29.png)

    2.  In der *Szene* und *Ansichten von Spielen*:

        ![Haben Sie die Szene und der Game-Ansichten in der gleichen Struktur.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a>Kapitel 5 – Erstellen der Ergebnisse-Klasse

Ist das erste Skript, das Sie erstellen müssen die *Ergebnisse* Klasse, die für die Bereitstellung einer Möglichkeit, die Ergebnisse der Übersetzung finden Sie unter verantwortlich ist. Die Klasse speichert, und es wird Folgendes angezeigt: 

- Das Ergebnis der Antwort von Azure.
- Der Status des Mikrofons. 
- Das Ergebnis der Spracheingaben (Sprache in Text).
- Das Ergebnis der Übersetzung.

Diese Klasse zu erstellen: 

1.  Mit der rechten Maustaste den *Projekt Bereich*, klicken Sie dann **erstellen > Ordner**. Nennen Sie den Ordner **Skripts**. 
 
    ![Erstellen Sie Ordner "Scripts" an.](images/AzureLabs-Lab1-31.png)

    ![Öffnen Sie den Ordner "Scripts" an.](images/AzureLabs-Lab1-32.png)
 
2.  Mit der **Skripts** Ordner erstellen, öffnen sie das Doppelklicken. In diesem Ordner, die mit der rechten Maustaste und wählen Sie dann **erstellen >** dann  **C# Skript**. Nennen Sie das Skript *Ergebnisse*. 

    ![Das erste Skript zu erstellen.](images/AzureLabs-Lab1-33.png)
 
3.  Doppelklicken Sie auf dem neuen *Ergebnisse* Skript öffnen Sie ihn mit **Visual Studio**.
4.  Fügen Sie die folgenden Namespaces ein:

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  Fügen Sie in der Klasse die folgenden Variablen:

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

6.  Fügen Sie dann die *Awake()* -Methode, die aufgerufen wird, wenn die Klasse initialisiert. 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  Schließlich fügen Sie die Methoden, die für die Ausgabe von des Ergebnissen Informationen auf der Benutzeroberfläche zuständig sind. 

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

8.  Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.

## <a name="chapter-6--create-the-microphonemanager-class"></a>Kapitel 6: Erstellen der *MicrophoneManager* Klasse

Die zweite Klasse, die Sie erstellen wollen ist die *MicrophoneManager*.

Diese Klasse ist zuständig für:

- Erkennen das Aufnahmegerät, die an den Kopfhörer oder die Computer, die (je nachdem, was der Standardeinstellung ist) angefügt.
- Das Audio (Sprache) und Diktat als Zeichenfolge zu speichern.
- Sobald die Stimme angehalten wurde, senden Sie die diktatfunktion, um die Translator-Klasse.
- Hosten Sie eine Methode, die der Sprachaufnahme kann bei Bedarf beenden.

Diese Klasse zu erstellen: 
1.  Klicken Sie mit der Doppelklicken auf die **Skripts** Ordner, um ihn zu öffnen. 
2.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen > C# Skript**. Nennen Sie das Skript *MicrophoneManager*. 
3.  Doppelklicken Sie auf das neue Skript aus, um ihn mit Visual Studio zu öffnen.
4.  Aktualisieren Sie die Namespaces, um Folgendes am Anfang entsprechen den *MicrophoneManager* Klasse:

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  Fügen Sie dann die folgenden Variablen in der *MicrophoneManager* Klasse:

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

6.  Code für die *Awake()* und *Start()* Methoden jetzt hinzugefügt werden muss. Diese werden aufgerufen, wenn die Klasse initialisiert:

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

7.  Sie können *löschen* der *Update()* Methode, da diese Klasse nicht verwendet wird.
8.  Jetzt Sie die Methoden, die die App zum Starten benötigen verwendet und Beenden der Sprachaufnahme und übergeben Sie sie an der *Translator* Klasse, die Sie in Kürze erstellen. Kopieren Sie den folgenden Code ein, und fügen Sie ihn unterhalb der *Start()* Methode.

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
    > Obwohl diese Anwendung nicht machen werden, verwenden die *StopCapturingAudio()* Methode auch bereitgestellt wurde, sollten Sie die Möglichkeit zum Anhalten, Erfassen von Audiodaten in Ihrer Anwendung implementieren möchten.

9.  Nun müssen Sie einen Diktat-Handler hinzuzufügen, die aufgerufen wird, wenn die Stimme wird beendet. Diese Methode übergibt den diktierten Text, klicken Sie dann die *Translator* Klasse.

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

10. Achten Sie darauf, dass Sie Ihre Änderungen vor der Rückgabe an Unity in Visual Studio zu speichern.

> [!WARNING]  
> An diesem Punkt werden Sie feststellen, einen Fehler angezeigt werden, der *Unity-Editor-Konsole* Bereich ("der Name"Translator"ist … nicht vorhanden"). Dies ist, da der Code verweist auf die *Translator* -Klasse, die Sie im nächsten Kapitel erstellen.

## <a name="chapter-7--call-to-azure-and-translator-service"></a>Kapitel 7 – Azure und die Translator-Dienst

Ist das letzte Skript Sie müssen die *Translator* Klasse. 

Diese Klasse ist zuständig für:

-   Die App mit Authentifizierung *Azure*, in exchange für eine **Authentifizierungstoken**.
-   Verwenden der **Authentifizierungstoken** zum Übermitteln von Text (Empfangen von der *MicrophoneManager* Klasse) übersetzt werden.
-   Das übersetzte Ergebnis zu erhalten und übergeben es an der *Ergebnisse* Klasse, um in der Benutzeroberfläche visuell dargestellt werden.

Zum Erstellen dieser Klasse: 
1.  Wechseln Sie zu der **Skripts** Ordner, die Sie zuvor erstellt haben. 
2.  Mit der rechten Maustaste den **Projekt Bereich**, **erstellen > C# Skript**. Rufen Sie das Skript *Translator*.
3.  Doppelklicken Sie auf dem neuen *Translator* Skript, um ihn zu öffnen **mit Visual Studio**.
4.  Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Klicken Sie dann fügen Sie die folgenden Variablen in der *Translator* Klasse:

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
    > - Die Sprachen, die in den Sprachen eingefügt **Enum** sind nur Beispiele. Können Sie mehr hinzufügen, wenn Sie möchten; die [-API unterstützt mehr als 60 Sprachen](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (einschließlich Klingonisch unterscheiden).
    > - Gibt es eine [interaktiver Seite, die für verfügbaren Sprachen](https://www.microsoft.com/translator/business/languages/), jedoch bedenken, dass die Seite wird nur angezeigt, funktionieren, wenn die Websitesprache festgelegt ist "En-us (und der Microsoft-Website, die wahrscheinlich Umleitung an Ihre Muttersprache ist). Sie können die Websitesprache am unteren Rand der Seite oder durch Ändern der URL ändern.
    > - Die **"authorizationkey"** Wert in der oben stehenden Codeausschnitt muss die **Schlüssel** Sie empfangen wird, wenn Sie abonniert die *Textübersetzungs-API von Azure*. Dies wurde im abgedeckt [Kapitel 1](#chapter-1--the-azure-portal).

6.  Code für die *Awake()* und *Start()* Methoden jetzt hinzugefügt werden muss. 
7.  In diesem Fall wird der Code einen Aufruf von stellen *Azure* verwenden die Autorisierung Schlüssel zum Abrufen einer *Token*.

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
    > Das Token läuft nach 10 Minuten. Je nach Szenario für Ihre app müssen Sie möglicherweise stellen die gleiche Coroutine mehrmals aufrufen.

8.  Die Coroutine aus, um das Token abzurufen, lautet wie folgt:

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
    > Wenn Sie den Namen der Methode des IEnumerator bearbeiten **GetTokenCoroutine()**, müssen Sie aktualisieren die *StartCoroutine* und *StopCoroutine* Zeichenfolgenwerte in den obigen Code aufrufen. [Gemäß der Unity-Dokumentation](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), um einen bestimmten beenden *Coroutine*, müssen Sie die Zeichenfolge-Value-Methode verwenden.

9.  Fügen Sie die Coroutine (mit einer "support" Stream-Methode direkt darunter) zum Abrufen der Übersetzung des Textes von empfangen die *MicrophoneManager* Klasse. Dieser Code erstellt eine Abfragezeichenfolge an die *Textübersetzungs-API von Azure*, und klicken Sie dann die internen Unity UnityWebRequest-Klasse verwendet, um die ein 'Get' Aufruf an den Endpunkt mit der Abfragezeichenfolge. Das Ergebnis wird dann verwendet, um die Übersetzung in Ihre "Results"-Objekt festzulegen. Der folgende Code zeigt die Implementierung:

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

10. Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.

## <a name="chapter-8--configure-the-unity-scene"></a>Kapitel 8 – konfigurieren die Unity-Szene

1.  Zurück im Unity-Editor, klicken Sie auf, und ziehen Sie die *Ergebnisse* Klasse *aus* der **Skripts** Ordner die **Main Camera** Objekt in der  *Hierarchie-Bereich*.
2.  Klicken Sie auf die **Main Camera** und sehen Sie sich die *Inspektor Bereich*. Sie werden feststellen, dass in der neu hinzugefügten *Skript* Komponente, es gibt vier Felder mit leeren Werten. Hierbei handelt es sich um die Ausgabe-Verweise auf die Eigenschaften im Code. 
3.  Ziehen Sie die entsprechende **Text** Objekte aus der *Hierarchie Bereich* für diese vier Slots, wie in der folgenden Abbildung dargestellt.

    ![Aktualisieren Sie Target-Verweise mit angegebenen Werten.](images/AzureLabs-Lab1-34.png)
  
4.  Als Nächstes klicken und ziehen Sie die *Translator* -Klasse aus der **Skripts** Ordner, um die **Main Camera** -Objekt in der *Hierarchie Bereich*. 
5.  Klicken Sie dann auf, und ziehen Sie die *MicrophoneManager* -Klasse aus der **Skripts** Ordner, um die **Main Camera** -Objekt in der *Hierarchie Bereich*. 
6.  Klicken Sie abschließend auf die **Main Camera** und sehen Sie sich die *Inspektor Bereich*. Beachten Sie, dass in das Skript, die, das Sie auf gezogen haben, stehen die beiden Dropdownfelder, die Sie festlegen, die Sprachen ermöglichen.
 
    ![Stellen Sie sicher, dass die beabsichtigte übersetzungssprachen eingegeben werden.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a>Kapitel 9 – Testen in mixed reality

An diesem Punkt müssen Sie testen, ob die Szene ordnungsgemäß implementiert wurde.

Stellen Sie Folgendes sicher:

- Alle Einstellungen, die im erwähnten [Kapitel 1](#chapter-1--the-azure-portal) ordnungsgemäß festgelegt sind. 
- Die *Ergebnisse*, *Translator*, und *MicrophoneManager*, Skripts werden angefügt, um die **Main Camera** Objekt. 
- Platziert haben Ihre *Textübersetzungs-API von Azure* Service **Schlüssel** innerhalb der **"authorizationkey"** Variablen innerhalb der *Translator* Skript.  
- Alle Felder in der *Kamera Inspector-Hauptbereich* ordnungsgemäß zugewiesen sind.
- Ihr Mikrofon arbeitet bei der Ausführung Ihrer Szene (nicht der Fall, überprüfen Sie, ob das angefügte Mikrofon ist die *Standard* Gerät, und dass Sie [richten sie sie ordnungsgemäß in Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).

Sie können die immersive Kopfhörer testen, indem Sie durch Drücken der **spielen** Schaltfläche der *Unity-Editor*.
Die App sollte über den angeschlossenen, immersive Kopfhörer funktionsfähig sein.

> [!WARNING]  
> Wenn einen Fehler in der Unity-Konsole zum Ändern der Standard-Audiogeräts angezeigt wird, funktioniert die Szene möglicherweise nicht wie erwartet. Dies ist aufgrund der Art, die das mixed Reality-Portal integrierte Mikrofone für Headsets behandelt, die sie verfügen. Wenn Sie diese Fehlermeldung angezeigt, einfach die Szene zu beenden und neu zu starten und als funktionieren sollte erwartet.

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a>Kapitel 10 – erstellen Sie die UWP-Projektmappe und das Sideloaden auf dem lokalen Computer

Alles, was Sie für den Unity-Abschnitt, der dieses Projekt wurde jetzt abgeschlossen daher ist es Zeit für die Erstellung von Unity.

1.  Navigieren Sie zu **Buildeinstellungen**: **Datei > Buildeinstellungen...**
2.  Von der **Buildeinstellungen** Fenster, klicken Sie auf **erstellen**.

    ![Die Unity-Szene zu erstellen.](images/AzureLabs-Lab1-36.png)
  
3.  Falls noch nicht geschehen, aktivieren Sie **Unity C# Projekte**.
4.  Klicken Sie auf **Erstellen**. Unity startet eine *Datei-Explorer* Fenster, in denen man erstellen, und wählen Sie einen Ordner zum Erstellen der app in. Erstellen Sie jetzt auf diesen Ordner, und nennen Sie es *App*. Klicken Sie dann mit der *App* Ordner ausgewählt haben, drücken Sie **Ordner auswählen**. 
5.  Erstellen Ihres Projekts zu Unity beginnt die *App* Ordner. 
6.  Einmal Unity wurde (es kann einige Zeit dauern) erstellen, öffnen ein *Datei-Explorer* Fenster am Speicherort des Builds (Überprüfen Sie Ihre Taskleiste aus, wie es unter Umständen nicht immer über Ihre Windows angezeigt und Sie über das Hinzufügen eines neuen benachrichtigt Fenster ").

## <a name="chapter-11--deploy-your-application"></a>Kapitel 11: Stellen Sie die Anwendung

Um die Anwendung bereitzustellen:

1.  Navigieren Sie zu Ihrem neuen Unity-Build (die *App* Ordner), und öffnen Sie die Projektmappendatei mit *Visual Studio*.
2.  In der Projektmappenkonfiguration Select **Debuggen**.
3.  Wählen Sie in der Plattform für die Projektmappe **X86**, **lokalen Computer**. 

    > Für die Microsoft HoloLens Umständen ist es einfacher, diese Einstellung auf *Remotecomputer*, sodass Sie nicht auf Ihren Computer angeschlossen sind. Allerdings müssen Sie auch die folgenden Schritte ausführen:
    > - Kennen der **IP-Adresse** von Ihrem HoloLens, die sich in befinden die *Einstellungen > Netzwerk und Internet > Wi-Fi > Erweiterte Optionen*; IPv4 ist die Adresse, die Sie verwenden sollten. 
    > - Stellen Sie sicher *Entwicklermodus* ist **auf**; gefunden in *Einstellungen > Update und Sicherheit > für Entwickler*.

    ![Die Lösung in Visual Studio bereit.](images/AzureLabs-Lab1-37.png)
    
 
4.  Wechseln Sie zu **Menü "Build"** und klicken Sie auf **Projektmappe bereitstellen** zum querladen der Anwendung auf Ihren PC.
5.  Ihre App sollte nun in der Liste der installierten apps, die zu startenden bereit angezeigt werden.
6.  Nachdem gestartet, werden Sie von die App aufgefordert, den Zugriff auf das Mikrofon autorisieren. Achten Sie darauf, klicken Sie auf die **Ja** Schaltfläche.
7.  Sie können nun damit beginnen, übersetzen.

## <a name="your-finished-translation-text-api-application"></a>Der fertigen Ausdrucksübersetzungs-Text-API-Anwendung

Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die die Übersetzung Text-API von Azure konvertieren Sprache in übersetzten Text nutzt.

![Das Endprodukt.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a>Bonus-Übungen

### <a name="exercise-1"></a>Übung 1

Können Sie die Sprachausgabe-Funktion auf die app hinzufügen, damit der zurückgegebene Text gesprochen wird?

### <a name="exercise-2"></a>Übung 2

Ermöglichen Sie es dem Benutzer, die Quelle und die Ausgabe-Sprachen ("from" und "to") innerhalb der app selbst ändern, damit die app nicht muss neu erstellt werden, jedes Mal, wenn Sie Sprachen ändern möchten.
