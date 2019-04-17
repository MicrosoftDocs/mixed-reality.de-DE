---
title: MR und Azure-302 - maschinelles sehen
description: Führen Sie diesen Kurs Informationen zum visuellen Inhalten in einem bereitgestellten Image mithilfe von Azure-Computer Vision in einer mixed Reality-Anwendung zu erkennen.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorials, api, maschinelles sehen, Hololens, immersive vr
ms.openlocfilehash: 9d5288904dd6cae08a995ae40a31b00fea655776
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593381"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

<br>

# <a name="mr-and-azure-302-computer-vision"></a>MR und Azure 302: Maschinelles sehen

In diesem Kurs erfahren Sie wie zur Erkennung von visuellem Inhalt in einem bereitgestellten Image mithilfe von Azure-Computer Vision-Funktionen in einer mixed Reality-Anwendung.

Erkennungsergebnisse werden als beschreibende Tags angezeigt werden. Sie können diesen Dienst verwenden, ohne, um ein Machine learning-Modell zu trainieren. Wenn Ihre Implementierung erfordert das Trainieren von Machine Learning-Modellen, finden Sie unter [MR und Azure 302b](mr-azure-302b.md).

![Lab-Ergebnis](images/AzureLabs-Lab2-000.png)

Die Computer Vision von Microsoft ist ein Satz von APIs, die mithilfe von erweiterten Algorithmen, alles über die Cloud entwickelt, um Entwicklern bieten, bildverarbeitung und-Analyse (mit Informationen) zurück, an. Entwickler hochzuladen, ein Bild oder die Bild-URL und die Algorithmen für maschinelles sehen-API von Microsoft Computer Analysieren des visuellen Inhalts, auf Grundlage von Eingaben, die ausgewählten Benutzers aus, klicken Sie dann Informationen zurückgegeben werden kann, einschließlich, identifizieren den Typ und die Qualität eines Bilds, menschliche Gesichter (erkennen Zurückgeben von ihren Koordinaten), und kennzeichnen und Kategorisieren von Bildern. Weitere Informationen finden Sie auf die [Azure Computer Vision-API-Seite](https://azure.microsoft.com/services/cognitive-services/computer-vision/).

Nach Abschluss dieses Kurses, verfügen Sie über ein mixed Reality HoloLens-Anwendung, die für die folgenden Aufgaben werden können

1.  Verwenden die tippbewegung, wird die Kamera und die HoloLens ein Bild zu erfassen.
2.  Das Bild wird an der Azure-Computer Vision-API-Dienst gesendet werden. 
3.  Die Objekte, die erkannt werden in einer einfachen Benutzeroberfläche-Gruppe, die in der Unity-Szene positioniert aufgeführt.

In Ihrer Anwendung obliegt es Ihnen, wie Sie die Ergebnisse in Ihr Design integrieren werden. Dieser Kurs erfahren Sie, wie Sie ein Azure-Dienst in Ihrem Unity-Projekt zu integrieren. Es ist Ihre Aufgabe, verwenden Sie das wissen, dass Sie aus diesem Kurs zum Verbessern Ihrer mixed Reality-Anwendung erhalten.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td> MR und Azure 302: Maschinelles sehen</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Während dieser Kurs in erster Linie für HoloLens ausgerichtet ist, können Sie auch anwenden, was Sie in diesem Kurs, Faszinierende Windows Mixed Reality (VR)-Headsets lernen. Da immersive Headsets von (VR) nicht zugegriffen werden kann, Kameras verfügen, benötigen Sie eine externe Kamera, die mit dem PC verbunden. Wie Sie den Kurs halten, sehen Anmerkungen zu dieser Version Sie auf alle Änderungen, die Sie möglicherweise zur Unterstützung von immersive Headsets von (VR) einsetzen müssen.

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
- Eine Kamera, die Verbindung mit Ihrem PC (für immersive Kopfhörer Entwicklung)
- Zugriff auf das Internet für die Einrichtung von Azure und Computer Vision-API abrufen

## <a name="before-you-start"></a>Bevor Sie beginnen

1.  Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).
2.  Richten Sie ein und Testen Sie Ihre HoloLens. Bei Bedarf Unterstützung zum Einrichten Ihrer HoloLens, [stellen Sie sicher, dass die HoloLens-Setup-Artikel finden Sie unter](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Es ist eine gute Idee, die Kalibrierung und Optimierung der Sensor ausführen, wenn Sie beginnen, eine neue HoloLens-App (manchmal ist es hilfreich, diese Aufgaben für jeden Benutzer) entwickeln. 

Um Hilfe zur Kalibrierung, befolgen Sie diese [Link zum Artikel HoloLens Kalibrierung](calibration.md#hololens).

Um Hilfe zur Optimierung der Sensor, befolgen Sie diese [Link zum Optimieren von HoloLens Sensor](sensor-tuning.md).

## <a name="chapter-1--the-azure-portal"></a>Kapitel 1 – Azure-Portal

Verwenden der *Computer Vision-API* Service in Azure müssen Sie so konfigurieren Sie eine Instanz des Diensts, der für Ihre Anwendung verfügbar gemacht werden.

1.  Melden Sie sich zunächst auf die [Azure-Portal](https://portal.azure.com). 

    > [!NOTE]
    > Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen. Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.

2.  Sobald Sie angemeldet sind, klicken Sie auf **neu** in der oberen linken Ecke, und suchen Sie nach *Computer Vision-API*, und klicken Sie auf **EINGABETASTE**.

    ![Erstellen Sie eine neue Ressource in Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > Das Wort **neu** wurden möglicherweise durch ersetzt **erstellen Sie eine Ressource**, in neueren-Portalen.
 
3.  Die neue Seite bietet eine Beschreibung der *Computer Vision-API* Service. Unten links auf dieser Seite die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.

    ![Über das Computer Vision-API-Dienst](images/AzureLabs-Lab2-01.png)
 
4.  Nachdem Sie auf geklickt haben **erstellen**:

    1. Fügen Sie Ihre bevorzugte **Namen** für diese Dienstinstanz.
    2. Wählen Sie eine **Abonnement**.
    3. Wählen Sie die **Tarif** für Sie geeignet ist, ist dies die erste Zeit in die Erstellung einer *Computer Vision-API* -Dienst ein freier-Tarif (mit dem Namen F0) für Sie verfügbar sein sollen.
    4. Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diesen Labs) unter einer allgemeinen Ressourcengruppe zu halten). 

        > Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, bitte [finden Sie im Artikel der Resource-Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Bestimmen Sie den Speicherort für die Ressourcengruppe, (Wenn Sie eine neue Ressourcengruppe erstellen). Der Speicherort würde idealerweise in der Region sein, in dem die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.

    6. Sie müssen auch bestätigen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.
    7. Klicken Sie auf erstellen.

        ![Erstellen von Dienstinformationen](images/AzureLabs-Lab2-02.png)

5.  Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.
6.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Die neue Benachrichtigung für den neuen Dienst angezeigt.](images/AzureLabs-Lab2-03.png) 
 
7.  Klicken Sie auf die Benachrichtigung, um Ihre neue Dienstinstanz zu untersuchen. 

    ![Wählen Sie die Schaltfläche zu Ressource wechseln.](images/AzureLabs-Lab2-04.png)
 
8. Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen. Sie werden für Ihre neue Computer Vision-API-Dienstinstanz weitergeleitet. 

    ![Dem neuen Computer Vision-API-Dienst](images/AzureLabs-Lab2-05.png)
 
9.  In diesem Tutorial müssen Ihre Anwendung Aufrufe an Ihren Dienst, was durch die Verwendung von Subscription-Key Ihres Diensts erfolgt.
10. Von der *Schnellstart* Seite von Ihrer *Computer Vision-API* service, navigieren Sie zum ersten Schritt *nehmen Sie Ihre Schlüssel*, und klicken Sie auf **Schlüssel** ( auch erreichen dies Sie durch Klicken auf den blauen Link Schlüssel befindet sich im Navigationsmenü Dienste durch ein Schlüsselsymbol gekennzeichnet). Dadurch wird angezeigt, den Dienst *Schlüssel*.
11. Erstellen Sie eine Kopie eines der angezeigten Schlüssel wird, da Sie dies später in Ihr Projekt benötigen. 

12. Wechseln Sie zurück zu den *Schnellstart* Seite, und von dort Abrufen Ihres Endpunkts. Denken Sie möglicherweise Ihre unterschiedlich, abhängig von Ihrer Region (die, wenn es sich handelt, müssen Sie den Code später ändern). Erstellen Sie eine Kopie dieses Endpunkts für die spätere Verwendung:

    ![Dem neuen Computer Vision-API-Dienst](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > Sie können überprüfen, was die verschiedenen Endpunkte sind [hier](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa). 

## <a name="chapter-2--set-up-the-unity-project"></a>Kapitel 2: Einrichten von Unity-Projekts

Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit mixed Reality und daher ist eine gute Vorlage für andere Projekte.

1.  Open *Unity* , und klicken Sie auf **neu**. 

    ![Starten Sie die neues Unity-Projekt.](images/AzureLabs-Lab2-06.png)

2.  Sie müssen nun einen Namen für die Unity-Projekt bereitstellen. Fügen Sie **MR_ComputerVision**. Stellen Sie sicher, dass der Projekttyp nastaven NA hodnotu **3D**. Legen Sie die **Speicherort** auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser). Klicken Sie auf **projekterstellung**.

    ![Die Details für die neue Unity-Projekt.](images/AzureLabs-Lab2-07.png)

3.  Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**. Wechseln Sie zu **Bearbeiten > Voreinstellungen** und navigieren Sie dann im neuen Fenster zu **externe Tools**. Änderung **externen Skript-Editors** zu **Visual Studio 2017**. Schließen der **Voreinstellungen** Fenster.

    ![Aktualisieren Sie die Skript-Editor-Einstellung.](images/AzureLabs-Lab2-08.png)

4.  Öffnen Sie als Nächstes **Datei > Buildeinstellungen** , und wählen Sie **universelle Windows-Plattform**, klicken Sie dann auf die **Plattform wechseln** Schaltfläche, um Ihre Auswahl anzuwenden.

    ![Fenster "Einstellungen", Switch-Plattform für die UWP zu erstellen.](images/AzureLabs-Lab2-10.png)

5.  In der **Datei > Buildeinstellungen** und stellen Sie sicher, dass:

    1. **Geräte** nastaven NA hodnotu **HoloLens**

        > Legen Sie für die immersive Headsets, **Zielgerät** zu *einem beliebigen Gerät*.

    2. **Buildtyp** nastaven NA hodnotu **D3D**
    3. **SDK** nastaven NA hodnotu **zuletzt installierte**
    4. **Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**
    5. **Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**
    6. Die Szene speichern und mit dem Build hinzugefügt werden.

        1. Hierzu **öffnen Szenen hinzufügen**. Ein Speichern Fenster wird angezeigt.
        
            ![Klicken Sie auf, öffnen im Hintergrund-Schaltfläche "hinzufügen"](images/AzureLabs-Lab2-11.png)

        2. Erstellen einen neuen Ordner für, und alle zukünftigen, Szene, klicken Sie dann auf die **neuer Ordner** Schaltfläche zum Erstellen eines neuen Ordners, nennen Sie sie **Szenen**.

            ![Erstellen Sie neue Ordner "Scripts"](images/AzureLabs-Lab2-12.png)

        3. Öffnen Sie den neu erstellten **Szenen** Ordner, und klicken Sie dann in der *Dateiname*: Textfeld **MR_ComputerVisionScene**, klicken Sie dann auf **speichern** .

            ![Geben Sie neue Szene einen Namen zu.](images/AzureLabs-Lab2-13.png)

            > Beachten Sie, speichern Sie Ihre Unity-Szenen in den *Assets* Ordner, wie sie mit der Unity-Projekt verbunden sein müssen. Erstellen den Ordner im Hintergrund (und andere ähnliche Ordner), wird eine typische Möglichkeit Strukturieren eines Unity-Projekts ist.

    7. Die Einstellungen im verbleibenden *Buildeinstellungen*, sollte jetzt als Standard bleiben.

6. In der *Buildeinstellungen* Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dadurch wird den entsprechenden Bereich geöffnet, im Bereich, in dem die *Inspektor* befindet. 

    ![Öffnen der playereinstellungen.](images/AzureLabs-Lab2-14.png)

7. In diesem Bereich sind müssen einige Einstellungen überprüft werden:

    1. In der **Weitere Einstellungen** Registerkarte:

        1. **Scripting Runtime Version** muss **stabile** (.NET 3.5 entspricht).
        2. **Back-End-Scripting** muss **.NET**
        3. **API-Kompatibilitätsebene** muss **.NET 4.6**

            ![Andere Einstellungen zu aktualisieren.](images/AzureLabs-Lab2-15.png)
      
    2. In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:

        1. **InternetClient**
        2. **Webcam**

            ![Veröffentlichungseinstellungen werden aktualisiert.](images/AzureLabs-Lab2-16.png)

    3. Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality-SDK**  hinzugefügt wird.

        ![Aktualisieren Sie die X-R-Einstellungen.](images/AzureLabs-Lab2-17.png)

8.  Im *Buildeinstellungen* _Unity C#_  Projekte nicht mehr abgeblendet ist, aktivieren Sie das Kontrollkästchen neben dieser. 
9.  Schließen Sie das Fenster "erstellen".
10. Speichern Sie Ihre Szene und das Projekt (**Datei > Speichern SZENE / FILE > Speichern Projekt**).

## <a name="chapter-3--main-camera-setup"></a>Kapitel 3 – Main Camera-setup

> [!IMPORTANT]
> Wenn Sie, überspringen möchten die *Unity einrichten* -Komponente dieser Kurs, und direkt in Code fortsetzen, können Sie zum Herunterladen [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), importieren Sie es in Ihr Projekt als eine [benutzerdefinierten Paket ](https://docs.unity3d.com/Manual/AssetPackages.html), und klicken Sie dann eine Fortsetzung [Kapitel 5](#chapter-5--create-the-resultslabel-class).

1.  In der *Hierarchie Bereich*, wählen die **Main Camera**. 
2.  Wenn ausgewählt, Sie werden auf alle Komponenten finden Sie unter den **Main Camera** in die *Inspektor Bereich*.

    1. Die **Kameraobjekt** muss den Namen **Main Camera** (Beachten Sie die Rechtschreibung!)
    2. Die Main Camera **Tag** muss festgelegt werden, um **MainCamera** (Beachten Sie die Rechtschreibung!)
    3. Stellen Sie sicher, dass die **transformieren Position** nastaven NA hodnotu **0, 0, 0**
    4. Legen Sie **löschen Flags** zu **Volltonfarbe** (ignorieren Sie dies für immersive Kopfhörer).
    5. Legen Sie die **Hintergrund** Farbe der Kamera-Komponente auf **Schwarz, Alpha 0 (Hex-Code: #00000000)** (ignorieren Sie dies für immersive Kopfhörer).

        ![Aktualisieren Sie die Kamera-Komponenten.](images/AzureLabs-Lab2-18.png)
 
3.  Als Nächstes müssen Sie zum Erstellen eines einfachen "Cursor"-Objekts angefügt der **Main Camera**, dem gibt Hilfe, positionieren Sie die Image-Analyse bei die Anwendung ausgeführt wird. Dieser Cursor bestimmt den Mittelpunkt der Kamera-Fokus.

So erstellen Sie den Cursor auf:

1.  In der *Hierarchie Bereich*, mit der rechten Maustaste auf die **Main Camera**. Klicken Sie unter **3D-Objekt**, klicken Sie auf **Kugel**.

    ![Wählen Sie den Cursorobjekt.](images/AzureLabs-Lab2-19.png)
 
2.  Benennen Sie die **Kugel** zu **Cursor** (das Cursorobjekt doppelklicken oder drücken Sie die Schaltfläche "F2"-Tastatur bei ausgewähltem Objekt), und stellen Sie sicher, dass es sich als untergeordnetes Element des der **Main Camera**.

3.  In der *Hierarchie Bereich*, links, klicken Sie auf die **Cursor**. Mit dem Cursor ausgewählt haben, passen Sie die folgenden Variablen in der *Inspektor Bereich*:

    1. Legen Sie die *transformieren Position* zu **0, 0, 5**
    2. Legen Sie die *Skalierung* zu **0,02, 0,02, 0,02**

        ![Aktualisieren Sie die Transformation positionieren und skalieren.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>Kapitel 4 – Setup das Label-system

Nachdem Sie ein Image mit dem HoloLens Kamera erfasst haben, wird dieses Bild an gesendet werden Ihre *maschinelles sehen-API von Azure-Computer* -Dienstinstanz für die Analyse. 

Die Ergebnisse dieser Analyse werden eine Liste der erkannten Objekte mit dem Namen **Tags**. 

Sie werden Bezeichnungen (als eine 3D-Text im Raum) verwenden, zu diesen Tags an der Position, an dem das Foto aufgenommen wurde.

Die folgenden Schritte zeigen, wie Setup die **Bezeichnung** Objekt.

1.  Mit der rechten Maustaste an einer beliebigen Stelle in der Hierarchie im Panel (die Position spielt keine Rolle an diesem Punkt) unter **3D-Objekt**, Hinzufügen einer **3D-Text**. Nennen Sie sie **LabelText**.

    ![Erstellen Sie 3D Text-Objekt.](images/AzureLabs-Lab2-21.png)
 
2.  In der *Hierarchie Bereich*, links, klicken Sie auf die **LabelText**. Mit der **LabelText** ausgewählt haben, passen Sie die folgenden Variablen in der *Inspektor Bereich*:

    1. Legen Sie die **Position** zu **0,0,0**
    2. Legen Sie die **Skalierung** zu **0,01, 0,01, 0,01**
    3. In der Komponente **Text Mesh**:
    4. Ersetzen Sie den Text in **Text**, mit "..."        
    5. Legen Sie die **Anker** zu **Mitte zentriert**
    6. Legen Sie die **Ausrichtung** zu **Center**
    7. Legen Sie die **Tabulatorgröße** zu **4**
    8. Legen Sie die **Schriftgrad** zu **50**
    9. Legen Sie die **Farbe** zu **#FFFFFFFF**

    ![Textkomponente](images/AzureLabs-Lab2-21-5.png)

3.  Ziehen Sie die **LabelText-Element** aus der *Hierarchie Bereich*, in der *Ordner "Assets"* in in der *Projekt Bereich*. Dies veranlasst das **LabelText** eines Prefabs, damit die It in Code instanziiert werden kann.

    ![Erstellen eines prefabs des LabelText-Objekts.](images/AzureLabs-Lab2-22.png)
 
4.  Löschen Sie die **LabelText** aus der *Hierarchie Bereich*, sodass sie in der Szene Öffnen nicht angezeigt wird. Im aktuellen Zustand eines prefabs, die Sie auf für einzelne Instanzen aus Ihrem Ordner "Assets" aufgerufen werden, besteht keine Notwendigkeit, sie in der Szene zu halten. 
5.  Die Struktur der endgültige Objekt in der *Hierarchie Bereich* sollte wie in der folgenden Abbildung dargestellt:

    ![Letzte Struktur der Hierarchie-Bereich.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>Kapitel 5 – Erstellen der ResultsLabel-Klasse

Ist das erste Skript, das Sie erstellen müssen die *ResultsLabel* -Klasse, die für Folgendes verantwortlich ist: 

- Erstellen die Bezeichnungen in der entsprechenden Raum relativ zur Position der Kamera an.
- Die Tags aus der Wegfall Bild wird angezeigt.

Diese Klasse zu erstellen: 

1.  Mit der rechten Maustaste den *Projekt Bereich*, klicken Sie dann **erstellen > Ordner**. Nennen Sie den Ordner **Skripts**. 

    ![Erstellen Sie Ordner "Scripts" an.](images/AzureLabs-Lab2-24.png)

2.  Mit der **Skripts** Ordner erstellen, öffnen sie das Doppelklicken. In diesem Ordner, die mit der rechten Maustaste und wählen Sie dann **erstellen >** dann  **C# Skript**. Nennen Sie das Skript *ResultsLabel*. 

3.  Doppelklicken Sie auf dem neuen *ResultsLabel* Skript öffnen Sie ihn mit **Visual Studio**.

4.  Fügen Sie in der Klasse den folgenden Code in die *ResultsLabel* Klasse:

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

6.  Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.
7.  In der *Unity-Editor*, klicken Sie auf, und ziehen Sie die *ResultsLabel* -Klasse aus der **Skripts** Ordner, um die **Main Camera** Objekt in der  *Hierarchie-Bereich*.
8.  Klicken Sie auf die **Main Camera** und sehen Sie sich die *Inspektor Bereich*.

Sie werden feststellen, dass das Skript, das Sie gerade in die Kamera gezogen haben, zwei Felder stehen: **Cursor** und **Bezeichnung Prefab**.

9.  Ziehen Sie das Objekt mit dem Namen **Cursor** aus der *Hierarchie Bereich* im Slot mit dem Namen **Cursor**, wie in der folgenden Abbildung dargestellt.
10. Ziehen Sie das Objekt mit dem Namen **LabelText** aus der *Ordner "Assets"* in der *Projektfenster* im Slot mit dem Namen **Bezeichnung Prefab**, siehe die Die Abbildung unten. 

    ![Legen Sie die Referenz-Ziele in Unity.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>Kapitel 6: Erstellen der digitale Bilder-Klasse

Die nächste Klasse, die Sie erstellen wollen ist die *digitale Bilder* Klasse. Diese Klasse ist zuständig für:

-   Erfassen ein Bild verwenden der Kamera HoloLens und in den App-Ordner speichern.
-   Erfassen von Tap-Gesten des Benutzers.

Diese Klasse zu erstellen: 

1.  Wechseln Sie zu der **Skripts** Ordner, die Sie zuvor erstellt haben. 
2.  Mit der rechten Maustaste in den Ordner **erstellen > C# Skript**. Rufen Sie das Skript *digitale Bilder*. 
3.  Doppelklicken Sie auf dem neuen *digitale Bilder* Skript öffnen Sie ihn mit **Visual Studio**.
4.  Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  Klicken Sie dann fügen Sie die folgenden Variablen in der *digitale Bilder* Klasse, über die *Start()* Methode:

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
Die **TapsCount** Variable speichert die Anzahl der Tap-Aktionen, die vom Benutzer erfasst. Diese Zahl wird verwendet, bei der Benennung der Images, die erfasst werden.

6.  Code für *Awake()* und *Start()* Methoden jetzt hinzugefügt werden muss. Diese werden aufgerufen, wenn die Klasse initialisiert:

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

7.  Implementieren Sie einen Handler, der aufgerufen wird, wenn eine Tap-Bewegung erfolgt. 

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
 
Die *TapHandler()* Methode inkrementiert die Anzahl der abtaststellen, die vom Benutzer erfasst und die aktuelle Cursorposition verwendet, zu bestimmen, wo eine neue Bezeichnung zu positionieren.

Diese Methode ruft dann die *ExecuteImageCaptureAndAnalysis()* Methode damit beginnt, die Kernfunktionen der Anwendung.

8.  Sobald ein Image erfasst und gespeichert wurde, werden die folgenden Handler aufgerufen werden. Wenn der Vorgang erfolgreich ist, wird das Ergebnis übergeben, um die *VisionManager* (was noch zu erstellen) für die Analyse.

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
 
9.  Fügen Sie dann die Methode, die die Anwendung verwendet wird, starten den Prozess der abbilderfassung aus, und speichern Sie das Abbild hinzu.

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
> An diesem Punkt werden Sie feststellen, einen Fehler angezeigt werden, der *Unity-Editor-Konsole Bereich*. Dies ist, da der Code verweist auf die *VisionManager* Klasse, die im nächsten Kapitel erstellt wird.

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>Kapitel 7 – Aufruf von Azure und Bildanalyse

Ist das letzte Skript Sie müssen die *VisionManager* Klasse. 

Diese Klasse ist zuständig für:

-   Laden das neueste Image als ein Array von Bytes erfasst.
-   Senden das Bytearray, Ihre *maschinelles sehen-API von Azure-Computer* -Dienstinstanz für die Analyse.
-   Empfangen der Antwort als JSON-Zeichenfolge.
-   Die Antwort zu deserialisieren, und übergeben die resultierende Tags auf der *ResultsLabel* Klasse.
 
Diese Klasse zu erstellen:

1.  Klicken Sie mit der Doppelklicken auf die **Skripts** Ordner, um ihn zu öffnen. 
2.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen > C# Skript**. Nennen Sie das Skript *VisionManager*. 
3.  Doppelklicken Sie auf das neue Skript aus, um ihn mit Visual Studio zu öffnen.
4.  Aktualisieren Sie die Namespaces, um Folgendes am Anfang entsprechen den *VisionManager* Klasse:

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  Am Anfang Ihres Skripts *in* der *VisionManager* Klasse (über die *Start()* Methode), müssen Sie nun zwei *Klassen* , Stellt die deserialisierte JSON-Antwort von Azure dar:

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
    > Die *"TagData"* und *AnalysedObject* Klassen haben, müssen die *[System.Serializable]* Attribut hinzugefügt werden, vor der Deklaration mit der Unity deserialisiert werden können -Bibliotheken.

6.  In der Klasse VisionManager sollten Sie die folgenden Variablen hinzufügen:

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
    > Stellen Sie sicher, Sie fügen Ihre **Authentication Key** in die **"authorizationkey"** Variable. Sie haben angemerkt Ihre **Authentication Key** am Anfang dieses Kurses, [Kapitel 1](#chapter-1--the-azure-portal).

    > [!WARNING] 
    > Die **VisionAnalysisEndpoint** Variable unterscheiden sich von dem in diesem Beispiel angegeben. Die **West-USA** bezieht sich ausschließlich auf die Dienstinstanzen erstellt wurden, für die Region USA, Westen. Aktualisieren Sie mit Ihrem [Endpunkt-URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); hier sind einige Beispiele, könnte folgendermaßen aussehen:
    > - Europa, Westen: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Asien, Südosten: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Australien, Osten;: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  Code für Awake muss nun hinzugefügt werden. 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  Fügen Sie als Nächstes die Coroutine (mit der statischen Stream Methode darunter), die die Ergebnisse der Analyse des Bilds von erfasst zu erhalten, wird die *digitale Bilder* Klasse. 

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

9.  Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.
10. Zurück im Unity-Editor, klicken Sie auf, und ziehen Sie die *VisionManager* und *digitale Bilder* Klassen aus der **Skripts** Ordner die **Main Camera**-Objekt in der *Hierarchie Bereich*. 

## <a name="chapter-8--before-building"></a>Kapitel 8 – vor dem Erstellen

Zur Durchführung eine gründliche Tests der Anwendung werden Sie querladen möchten sie auf Ihre HoloLens benötigen.
Vor dem Ausführen, stellen Sie sicher, dass:

-   Alle Einstellungen, die im erwähnten [Kapitel 2](#chapter-2--set-up-the-unity-project) ordnungsgemäß festgelegt sind. 
-   Alle Skripts werden angefügt, um die **Main Camera** Objekt. 
-   Alle Felder in der *Kamera Inspector-Hauptbereich* ordnungsgemäß zugewiesen sind.
-   Stellen Sie sicher, Sie fügen Ihre **Authentication Key** in die **"authorizationkey"** Variable.
-   Stellen Sie sicher, dass Sie auch den Endpunkt, in aktiviert haben Ihre *VisionManager* Skript, und sie entspricht *Ihre* Region (in diesem Dokument wird *West-USA* standardmäßig).

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>Kapitel 9 – erstellen die UWP-Projektmappe, und Laden Sie die Anwendung
Alles, was Sie für den Unity-Abschnitt, der dieses Projekt wurde jetzt abgeschlossen daher ist es Zeit für die Erstellung von Unity.

1.  Navigieren Sie zu *Buildeinstellungen* - **Datei > Buildeinstellungen...**
2.  Von der *Buildeinstellungen* Fenster, klicken Sie auf **erstellen**.

    ![Erstellen der app von Unity](images/AzureLabs-Lab2-26.png)

3.  Falls noch nicht geschehen, aktivieren Sie **Unity C# Projekte**.
4.  Klicken Sie auf **Erstellen**. Unity startet eine *Datei-Explorer* Fenster, in denen man erstellen, und wählen Sie einen Ordner zum Erstellen der app in. Erstellen Sie jetzt auf diesen Ordner, und nennen Sie es *App*. Klicken Sie dann mit der *App* Ordner ausgewählt haben, drücken Sie **Ordner auswählen**. 
5.  Erstellen Ihres Projekts zu Unity beginnt die *App* Ordner. 
6.  Einmal Unity wurde (es kann einige Zeit dauern) erstellen, öffnen ein *Datei-Explorer* Fenster am Speicherort des Builds (Überprüfen Sie Ihre Taskleiste aus, wie es unter Umständen nicht immer über Ihre Windows angezeigt und Sie über das Hinzufügen eines neuen benachrichtigt Fenster ").

## <a name="chapter-10--deploy-to-hololens"></a>Kapitel 10 – bereitstellen, um HoloLens

Für HoloLens bereitstellen:

1.  Sie benötigen die IP-Adresse Ihrer HoloLens (für Remote bereitstellen), und um sicherzustellen, dass Ihre HoloLens befindet sich in **Entwicklermodus**. Gehen Sie dazu wie folgt vor:

    1. Während Ihre HoloLens steht, geteert, öffnen Sie die **Einstellungen**.
    2. Wechseln Sie zu **Netzwerk und Internet > Wi-Fi-> Erweiterte Optionen**
    3. Beachten Sie die **IPv4** Adresse.
    4. Navigieren Sie als Nächstes zurück zum **Einstellungen**, und klicken Sie dann **Update und Sicherheit > für Entwickler** 
    5. Festlegen des Entwicklermodus auf.

2.  Navigieren Sie zu Ihrem neuen Unity-Build (die *App* Ordner), und öffnen Sie die Projektmappendatei mit *Visual Studio*.
3.  In der Projektmappenkonfiguration Select **Debuggen**.
4.  Wählen Sie in der Plattform für die Projektmappe **X86**, **Remotecomputer**. 

    ![Die Lösung in Visual Studio bereit.](images/AzureLabs-Lab2-27.png)
 
5.  Wechseln Sie zu der **Menü "Build"** und klicken Sie auf **Projektmappe bereitstellen**, zum querladen der Anwendung in Ihrem HoloLens.
6.  Ihre App sollte nun in der Liste der installierten apps auf Ihre HoloLens, möchten Sie die gestartet werden, angezeigt werden.

> [!NOTE]
> Legen Sie zum Bereitstellen auf immersive Kopfhörer der **Projektmappenplattform** zu *lokalen Computer*, und legen Sie die **Konfiguration** zu *Debuggen*, mit *X86* als die **Plattform**. Klicken Sie dann bereitstellen, in der lokalen Computer, mit der **Menü "Build"**, wählen *Projektmappe bereitstellen*. 

## <a name="your-finished-computer-vision-api-application"></a>Der fertigen Anwendung für die Computer Vision-API

Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die nutzt das Computer Vision-API von Azure realen Objekte zu erkennen, und zeigen Gewissheit wie wir gesehen haben.

![Lab-Ergebnis](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>Bonus-Übungen

### <a name="exercise-1"></a>Übung 1

Wie Sie verwendet haben, der *Tags* Parameter (wie gezeigt in der *Endpunkt* innerhalb der *VisionManager*), erweitern Sie die app aus, um weitere Informationen zu ermitteln, sehen Sie sich Welche anderen Parameter haben Sie Zugriff auf [hier](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).

### <a name="exercise-2"></a>Übung 2

Anzuzeigen Sie die zurückgegebenen Azure Daten, auf eine Weise mehr conversational und besser lesbar, z. B. durch das Ausblenden der Zahlen. Als ob ein Bot für den Benutzer sprechen kann.
