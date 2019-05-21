---
title: MR und Azure-305 - Funktionen und Speicher
description: Führen Sie diesen Kurs, um zu erfahren, wie Sie Azure Storage und-Funktionen innerhalb einer mixed Reality-Anwendung zu implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorials, api, Funktionen, Speicher, Hololens, immersive Vr
ms.openlocfilehash: a828c7f0ac3016462f5c7e874545bf50a2db6771
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593545"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a>MR und Azure-305: Funktionen und Speicher

![Endprodukt-starten](images/AzureLabs-Lab5-00.png)

In diesem Kurs erfahren Sie, wie zum Erstellen und Verwenden von Azure Functions aus, und speichern Sie Daten mit einem Azure Storage-Ressource in einer mixed Reality-Anwendung.

*Azure Functions* ist ein Microsoft-Dienst, die Entwickler kleine Teile des Codes ausgeführt werden kann, "Funktionen", in Azure. Dadurch wird eine Möglichkeit zum Delegieren der Arbeit an Ihrer lokalen Anwendung, die viele Vorteile haben kann, anstatt die Cloud. *Azure Functions* unterstützt verschiedene Entwicklungssprachen, darunter C\#, F\#, Node.js, Java und PHP. Weitere Informationen finden Sie auf die [Azure Functions-Artikel](https://docs.microsoft.com/azure/azure-functions/functions-overview).

*Azure-Speicher* ist ein Microsoft-Cloud-Dienst, der ermöglicht es Entwicklern, die zum Speichern von Daten mit der Versicherung, dass es hoch verfügbar, sichere, permanenten, skalierbar und redundant ist. Dies bedeutet, dass Microsoft alle Wartung und kritische Probleme für Sie übernimmt. Weitere Informationen finden Sie auf die [Azure Storage-Artikel](https://docs.microsoft.com/azure/storage/common/storage-introduction).

Nach Abschluss dieses Kurses, verfügen Sie über ein mixed Reality immersive Kopfhörer Anwendung die können die folgenden Schritte ausführen:

1.  Ermöglicht dem Benutzer, die in einer Szene bestaunen.
2.  Das Erzeugen von Objekten, wenn der Benutzer auf ein 3D-Diagrammlayout "Button" gazes ausgelöst werden.
3.  Die erzeugten Objekte werden durch eine Azure-Funktion ausgewählt werden.
4.  Da jedes Objekt erzeugt wird, speichert die Anwendung den Objekttyp in einem *Azure File*befindet sich im *Azure Storage*.
5.  Beim Laden eines zweiten Mal die *Azure File* Daten abgerufen, und zur Wiedergabe erzeugenden Aktionen auf der vorherigen Instanz der Anwendung verwendet werden.

In Ihrer Anwendung obliegt es Ihnen, wie Sie die Ergebnisse in Ihr Design integrieren werden. Dieser Kurs erfahren Sie, wie Sie ein Azure-Dienst in Ihrem Unity-Projekt zu integrieren. Es ist Ihre Aufgabe, verwenden Sie das wissen, dass Sie aus diesem Kurs zum Verbessern Ihrer mixed Reality-Anwendung erhalten.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td>MR und Azure-305: Funktionen und Speicher</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Während dieser Kurs in erster Linie für immersive Windows Mixed Reality (VR)-Headsets ausgerichtet ist, können Sie auch anwenden, was Sie in diesem Kurs, Microsoft HoloLens lernen. Wie Sie den Kurs halten, sehen Anmerkungen zu dieser Version auf Änderungen Sie möglicherweise zur Unterstützung von HoloLens einsetzen müssen.

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
- Ein Abonnement für ein Azure-Konto zum Erstellen von Azure-Ressourcen
- Zugriff auf das Internet für den Abruf von Setup- und Azure

## <a name="before-you-start"></a>Bevor Sie beginnen

Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).

## <a name="chapter-1---the-azure-portal"></a>Kapitel 1: das Azure-Portal

Verwenden der **Azure Storage-Dienst**, Sie benötigen zum Erstellen und Konfigurieren einer **Speicherkonto** im Azure-Portal.

1.  Melden Sie sich bei der [Azure-Portal](https://portal.azure.com).

    > [!NOTE]
    > Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen. Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.

2.  Sobald Sie angemeldet sind, klicken Sie auf **neu** in der oberen linken Ecke, und suchen Sie nach *Speicherkonto*, und klicken Sie auf **EINGABETASTE**.

    ![Azure-Speicher-Suche](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > Das Wort **neu** wurden möglicherweise durch ersetzt **erstellen Sie eine Ressource**, in neueren-Portalen.

3.  Die neue Seite bietet eine Beschreibung der *Azure Storage-Konto* Service. Unten links der Aufforderung, wählen die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.

    ![Dienst erstellen](images/AzureLabs-Lab5-02.png)

4.  Nachdem Sie auf geklickt haben **erstellen**:

    1.  Fügen Sie eine *Namen* für Ihr Konto bedenken, dass dieses Feld akzeptiert nur Ziffern und Kleinbuchstaben zulässig.

    2.  Für *Bereitstellungsmodell*Option **RM**.

    3.  Für *Kontoart*Option **Speicher (Allgemein v1)**.

    4.  Bestimmen der *Speicherort* für Ihre Ressourcengruppe aus (Wenn Sie eine neue Ressourcengruppe erstellen). Der Speicherort würde idealerweise in der Region sein, in dem die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.

    5.  Für *Replikation* wählen **Read-Access-georedundanter Speicher (RA-GRS)**.

    6.  Für *Leistung*Option **Standard**.

    7.  Lassen Sie *sichere Übertragung erforderlich* als **deaktiviert**.

    8.  Wählen Sie eine *Abonnement*.

    9. Wählen Sie eine *Ressourcengruppe* oder ein neues erstellen. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diesen Labs) unter einer allgemeinen Ressourcengruppe zu halten). 

        > Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, bitte [finden Sie im Artikel der Resource-Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. Sie müssen auch bestätigen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.

    11. Wählen Sie **Erstellen** aus.

        ![Eingabe Dienstinformationen](images/AzureLabs-Lab5-03.png)

5.  Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.

6.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Neue Benachrichtigung im Azure-portal](images/AzureLabs-Lab5-04.png)

7.  Klicken Sie auf die Benachrichtigungen an Ihre neue Dienstinstanz zu untersuchen.

    ![zu Ressource wechseln](images/AzureLabs-Lab5-05.png)

8.  Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen. Sie gelangen in die neue *Speicherkonto* Dienstinstanz.

    ![Zugriffstasten](images/AzureLabs-Lab5-06.png)

9.  Klicken Sie auf *Zugriffsschlüssel*, um die Endpunkte für diesen Cloud-Dienst anzuzeigen. Verwenden Sie *Editor* oder eine ähnliche Kopie einen Ihrer Schlüssel zur späteren Verwendung. Beachten Sie außerdem die *Verbindungszeichenfolge* -Wert fest, wie er in verwendet werden, wird die *AzureServices* -Klasse, die Sie später erstellen.

    ![Verbindungszeichenfolge kopieren](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a>Kapitel 2: Einrichten einer Azure-Funktion

Schreiben Sie jetzt eine **Azure** **Funktion** im Azure-Dienst.

Sie können eine **Azure-Funktion** nahezu alles tun, die Sie mit einer klassischen-Funktion in Ihrem Code, den Unterschied ausführen würden, dass diese Funktion von jeder Anwendung zugegriffen werden kann, die Anmeldeinformationen zum Zugriff auf Ihr Azure-Konto verfügt.

So erstellen Sie eine Azure-Funktion

1.  Aus Ihrem *Azure-Portal*, klicken Sie auf **neu** in der oberen linken Ecke, und suchen Sie nach *Funktions-App*, und klicken Sie auf **EINGABETASTE**.

    ![Erstellen von Funktionen-app](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > Das Wort **neu** wurden möglicherweise durch ersetzt **erstellen Sie eine Ressource**, in neueren-Portalen.

2.  Die neue Seite bietet eine Beschreibung der *Azure Function-App* Service. Unten links der Aufforderung, wählen die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.

    ![Funktion-app-info](images/AzureLabs-Lab5-09.png)

3.  Nachdem Sie auf geklickt haben **erstellen**:

    1.  Geben Sie eine *Anwendungsnamen*. Nur Buchstaben und Zahlen können hier verwendet werden (entweder Groß-/Kleinschreibung ist zulässig).

    2.  Wählen Sie die bevorzugte *Abonnement*.

    3. Wählen Sie eine *Ressourcengruppe* oder ein neues erstellen. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diesen Labs) unter einer allgemeinen Ressourcengruppe zu halten). 

        > Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, bitte [finden Sie im Artikel der Resource-Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Wählen Sie für diese Übung *Windows* als das ausgewählte **OS**.

    5.  Wählen Sie *Verbrauchsplan* für die **Hostingplan**.

    6.  Bestimmen der *Speicherort* für Ihre Ressourcengruppe aus (Wenn Sie eine neue Ressourcengruppe erstellen). Der Speicherort würde idealerweise in der Region sein, in dem die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar. Wählen Sie für eine optimale Leistung der gleichen Region wie das Speicherkonto aus.

    7.  Für *Storage*Option **vorhandene**, und klicken Sie dann mit dem Dropdown-Menü, Ihre zuvor erstellten speicherkontonamen finden.

    8.  Lassen Sie *Application Insights* für diese Übung deaktiviert.

        ![Eingabefunktion app-details](images/AzureLabs-Lab5-10.png)

4.  Klicken Sie auf die Schaltfläche **Erstellen**.

5.  Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.

6.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![neue Azure-portalbenachrichtigungen](images/AzureLabs-Lab5-11.png)

7.  Klicken Sie auf die Benachrichtigungen an Ihre neue Dienstinstanz zu untersuchen. 

    ![Wechseln Sie zur Ressource Funktions-app](images/AzureLabs-Lab5-12.png)

8.  Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen. Sie gelangen in die neue *Funktions-App* Dienstinstanz.

9.  Auf der *Funktions-App* Dashboard den Mauszeiger auf *Funktionen*, innerhalb des Bereichs auf der linken Seite gefunden, und klicken Sie dann auf die **+ (plus)** Symbol.

    ![Erstellen Sie neue Funktion](images/AzureLabs-Lab5-13.png)

10. Vergewissern Sie sich auf der nächsten Seite **Webhook + API** ausgewählt ist, und für *wählen Sie eine Sprache,* wählen **CSharp**, wie dies mit der Sprache, die für dieses Tutorial verwendet werden. Klicken Sie abschließend auf die **diese Funktion erstellen** Schaltfläche.

    ![Wählen Sie Hook-Csharp web](images/AzureLabs-Lab5-14.png)

11. Sie sind, um den Code Seite ("Run.csx"), wenn nicht jedoch für die neu erstellte Funktion in der Liste der Funktionen innerhalb des Bereichs auf der linken Seite klicken.

    ![Öffnen Sie die neue Funktion](images/AzureLabs-Lab5-15.png)

12. Kopieren Sie den folgenden Code in Ihrer Funktion. Diese Funktion gibt einfach eine zufällige ganze Zahl zwischen 0 und 2, die beim Aufruf zurück. Gedanken um den vorhandenen Code, fügen Sie oberhalb des Zertifikats können nicht.

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. Wählen Sie **Speichern**.

14. Das Ergebnis sollte wie in der folgenden Abbildung aussehen.

15. Klicken Sie auf **Funktions-URL abrufen** und notieren Sie sich die *Endpunkt* angezeigt. Sie benötigen, fügen Sie ihn in das *AzureServices* -Klasse, die Sie weiter unten in diesem Kurs erstellen.

    ![Rufen Sie Funktionsendpunkt](images/AzureLabs-Lab5-16.png)

    ![Rufen Sie Funktionsendpunkt](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a>Kapitel 3 – Einrichten des Unity-Projekts

Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit Mixed Reality und daher ist eine gute Vorlage für andere Projekte.

Richten Sie ein und Testen Sie Ihrer mixed Reality immersive Kopfhörer.

> [!NOTE]
> Sie **nicht** Motion-Controller für dieses Kurses erforderlich. Wenn Sie die Einrichtung der immersive Kopfhörer unterstützen müssen, wenden Sie [finden Sie auf die gemischte Realität Artikel richten](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Öffnen von Unity, und klicken Sie auf **neu**.

    ![Erstellen der neuen Unity-Projekt](images/AzureLabs-Lab5-17.png)

2.  Sie müssen nun einen Namen für die Unity-Projekt bereitstellen. Fügen Sie **MR_Azure_Functions**. Stellen Sie sicher, dass der Projekttyp nastaven NA hodnotu **3D**. Legen Sie die *Speicherort* auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser). Klicken Sie auf **projekterstellung**.

    ![Benennen Sie neue Unity-Projekt](images/AzureLabs-Lab5-18.png)

3.  Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**. Wechseln Sie zu **bearbeiten* > *Voreinstellungen** und navigieren Sie dann im neuen Fenster zu **externe Tools**. Änderung **externen Skript-Editors** zu **Visual Studio 2017**. Schließen der **Voreinstellungen** Fenster.

    ![Satz von visual Studio als Skript-editor](images/AzureLabs-Lab5-19.png)

4.  Öffnen Sie als Nächstes **Datei > Buildeinstellungen** , und wechseln von der Plattform bereitgestellten **universelle Windows-Plattform**, durch Klicken auf die **Plattform wechseln** Schaltfläche.

    ![Plattform für die Uwp wechseln](images/AzureLabs-Lab5-20.png)

5.  Wechseln Sie zu **Datei > Buildeinstellungen** und stellen Sie sicher, dass:

    1. **Geräte** nastaven NA hodnotu **einem beliebigen Gerät**.

        > Legen Sie für Microsoft HoloLens, **Zielgerät** zu *HoloLens*.

    2. **Buildtyp** nastaven NA hodnotu **D3D**

    3. **SDK** nastaven NA hodnotu **zuletzt installierte**

    4. **Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**

    5. **Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**

    6. Die Szene speichern und mit dem Build hinzugefügt werden.

        1.  Hierzu **öffnen Szenen hinzufügen**. Ein Speichern Fenster wird angezeigt.

            ![Hinzufügen von öffnen-Szenen](images/AzureLabs-Lab5-21.png)

        2.  Erstellen einen neuen Ordner für, und alle zukünftigen, Szene, klicken Sie dann auf die **neuer Ordner** Schaltfläche zum Erstellen eines neuen Ordners, nennen Sie sie **Szenen**.

            ![Erstellen Sie im Hintergrund-Ordner](images/AzureLabs-Lab5-22.png)

        3.  Öffnen Sie den neu erstellten **Szenen** Ordner, und klicken Sie dann in der **Dateiname:** Textfeld **FunctionsScene**, drücken Sie dann die **speichern**.

            ![Functions-Szene speichern](images/AzureLabs-Lab5-23.png)

6.  Die Einstellungen im verbleibenden **Buildeinstellungen**, sollte jetzt als Standard bleiben.

    ![Functions-Szene speichern](images/AzureLabs-Lab5-24.png)

7.  In der *Buildeinstellungen* Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dadurch wird den entsprechenden Bereich geöffnet, im Bereich, in dem die *Inspektor* befindet.

    ![Player-Einstellungen im Inspektor](images/AzureLabs-Lab5-25.png)

8.  In diesem Bereich sind müssen einige Einstellungen überprüft werden:

    1.  In der **Weitere Einstellungen** Registerkarte:

        1.  **Scripting Runtime Version** muss **experimentell** (.NET 4.6 entspricht), löst der Editor neu starten müssen.
        2.  **Back-End-Scripting** muss **.NET**
        3.  **API-Kompatibilitätsebene** muss **.NET 4.6**

    2.  In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:
        
        -  **InternetClient**

            ![Set-Funktionen](images/AzureLabs-Lab5-26.png)

    3.  Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality SDK** hinzugefügt wird.

        ![Einstellungen der Set-XR](images/AzureLabs-Lab5-27.png)

9.  Im *Buildeinstellungen* *Unity C# Projekte* nicht mehr abgeblendet ist, aktivieren Sie das Kontrollkästchen neben dieser.

    ![Teilstriche c#-Projekte](images/AzureLabs-Lab5-28.png)

10.  Schließen Sie das Fenster "erstellen".

11. Speichern Sie Ihre Szene und das Projekt (**Datei > Speichern SZENE / FILE > Speichern Projekt**).

## <a name="chapter-4---setup-main-camera"></a>Kapitel 4: Einrichtung Hauptkamera

> [!IMPORTANT]
> Wenn Sie, überspringen möchten die *Unity einrichten* Komponenten dieses Kurs, und direkt in Code fortfahren, können Sie [Herunterladen dieser .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage), und importieren Sie es in Ihr Projekt als eine [benutzerdefinierte Paket](https://docs.unity3d.com/Manual/AssetPackages.html). Dies wird auch die DLLs aus dem nächsten Kapitel enthalten. Ist eine Fortsetzung nach dem Import, [Kapitel 7](#chapter-7---create-the-azureservices-class). 

1.  In der *Hierarchie Bereich*, sehen Sie ein Objekt namens **Main Camera**, diesem Objekt dargestellten Ihr "Head" Sicht aus, wenn Sie "in" Ihrer Anwendung sind.

2.  Wählen Sie im Unity-Dashboard vor Ihnen die **Main Camera "gameobject"**. Sie werden feststellen, dass die *Inspektor Bereich* (in der Regel nach rechts im Dashboard gefunden) zeigt die verschiedenen Komponenten, die *"gameobject"*, mit *transformieren* oben, gefolgt von *Kamera*, und einige andere Komponenten. Sie müssen die Transformation der Main-Kamera, zurücksetzen, damit sie richtig positioniert ist.

3.  Wählen Sie zu diesem Zweck die **Zahnradsymbol** Symbol neben der Kamera *transformieren* Komponente, und wählen **zurücksetzen**.

    ![Transformation zurücksetzen](images/AzureLabs-Lab5-29.png)

4.  Aktualisieren Sie dann die **transformieren** Komponente, die wie folgt aussehen:

    |         |    TRANSFORM - POSITION   |       |
    | :-----: | :-----------------------: | :----:|
    | **X**   | **Y**                     | **Z** |
    | 0       | 1                         | 0     |    

    |       | TRANSFORM - DREHUNG |       |
    | :---: | :------------------: | :----:|
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 0     |

    |       | TRANSFORM - SKALIERUNG |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 1     | 1                 | 1     |

    ![Set-Kamera-Transformation](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a>Kapitel 5: Einrichten der Unity-Szene

1.  Mit der rechten Maustaste in einen leeren Bereich des der *Hierarchie Bereich*unter **3D-Objekt**, Hinzufügen einer **Ebene**.

    ![Erstellen Sie neue Ebene](images/AzureLabs-Lab5-31.png)

2.  Mit der **Ebene** Objekt ausgewählt haben, ändern Sie die folgenden Parameter in der *Inspektor Bereich*:

    |       | TRANSFORM - POSITION |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | 4     |

    |       | TRANSFORM - SKALIERUNG |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 10    | 1                 | 10    |

    ![Set-Ebene transformationsposition und-Skalierung](images/AzureLabs-Lab5-32.png)

    ![Szenenansicht Ebene](images/AzureLabs-Lab5-33.png)

3.  Mit der rechten Maustaste in einen leeren Bereich des der *Hierarchie Bereich*unter **3D-Objekt**, Hinzufügen einer **Cube**.

    1.  Benennen Sie den Cube zu **GazeButton** (mit dem Cube ausgewählt haben, drücken Sie "F2").

    2.  Ändern Sie die folgenden Parameter in der *Inspektor Bereich*:

        |       | TRANSFORM - POSITION |       |
        | :---: | :------------------: |:-----:|
        | **X** | **Y**                | **Z** |
        | 0     | 3                    | 5     |


        ![Set Blicke Schaltfläche Transformation](images/AzureLabs-Lab5-34.png)

        ![Schaltfläche Szenenansicht bestaunen](images/AzureLabs-Lab5-35.png)

    3.  Klicken Sie auf die **Tag** Dropdown-Schaltfläche, und klicken Sie auf **Tag hinzufügen** zum Öffnen der *Tags und im Bereich*.

        ![Neues Tag hinzufügen](images/AzureLabs-Lab5-36.png)

        ![Select plus](images/AzureLabs-Lab5-37.png)

    4.  Wählen Sie die **+ (plus)** Schaltfläche, und klicken Sie in der *neue Tagnamen* Feld **GazeButton**, und drücken Sie **speichern**.

        ![Neues Tag Name](images/AzureLabs-Lab5-38.png)

    5.  Klicken Sie auf die **GazeButton** -Objekt in der *Hierarchie Bereich*, und klicken Sie in der *Inspektor Bereich*, weisen Sie den neu erstellten **GazeButton** Tag.

        ![Weisen Sie das neue Tag Blicke-Schaltfläche](images/AzureLabs-Lab5-39.png)

4.  Mit der rechten Maustaste auf die **GazeButton** Objekt, in der *Hierarchie Bereich*, und fügen ein **leeres "gameobject"** (das wird als hinzugefügt eine *untergeordneten* -Objekt).

5.  Wählen Sie das neue Objekt, und benennen Sie sie **ShapeSpawnPoint**.

    1.  Ändern Sie die folgenden Parameter in der *Inspektor Bereich*:

        |       | TRANSFORM - POSITION |       |
        | :---: | :------------------: |:----: |
        | **X** |**Y**                 | **Z** |
        | 0     | -1                   | 0     |

        ![Aktualisieren Sie die Form Spawn Punkt Transformation](images/AzureLabs-Lab5-40.png)

        ![Form Spawn Szenenansicht](images/AzureLabs-Lab5-41.png)

6.  Als Nächstes erstellen Sie eine **3D-Text** Objekt, das Feedback zu den Status des Azure-Diensts.

    Klicken Sie mit der rechten Maustaste auf die **GazeButton** in der Hierarchie im Bereich erneut aus, und fügen eine **3D-Objekt > 3D-Text** als Objekt ein *untergeordneten*.

    ![Erstellen Sie neue 3D-Text-Objekt](images/AzureLabs-Lab5-42.png)

7.  Benennen Sie die **3D-Text** -Objekt **AzureStatusText**.

8.  Ändern der **AzureStatusText** -Objekt Transformation wie folgt:

    |       | TRANSFORM - POSITION |       |
    | :---: | :------------------: | :---: |
    | **X** | **Y**                | **Z** |
    | 0     | 0                    | -0.6  |

    |       | TRANSFORM - SKALIERUNG |       |
    | :---: | :---------------: | :---: |
    | **X** | **Y**             | **Z** |
    | 0.1   | 0.1               | 0.1   |


    > [!NOTE]
    > Aber keine Sorge, wenn sie off-Center, scheint, wie dies bei behoben werden die folgenden Text Mesh Komponente aktualisiert wird.

9.  Ändern der **Text Mesh** Komponente entsprechend der unten:

    ![Set Text Mesh-Komponente](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > Die ausgewählte Farbe hier ist Hexadezimalfarbe: **000000FF (Schwarz)**, jedoch können Sie Ihre eigenen auswählen, nur sicherzustellen, dass er gelesen.

10. Die Struktur der Hierarchie Bereich sollte jetzt wie folgt aussehen:

    ![mesh-Text in der Szenenansicht](images/AzureLabs-Lab5-43b.png)

10. Die Szene sollte jetzt wie folgt aussehen:

    ![mesh-Text in der Szenenansicht](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a>Kapitel 6: Importieren von Azure-Speicher für Unity

Verwenden Sie Azure Storage für Unity (die wiederum nutzt das .net SDK für Azure). Weitere Informationen finden Sie unter den [Azure Storage für Unity-Artikel](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).

Es befindet sich derzeit ein bekanntes Problem in Unity-Plug-Ins neu konfiguriert werden, nach dem Import erfordert. Diese Schritte (4 bis 7 in diesem Abschnitt) ist nicht mehr erforderlich, nachdem der Fehler behoben wurde.

Um das SDK in Ihr eigenes Projekt zu importieren, stellen Sie sicher, dass Sie heruntergeladen haben, die neueste Version [".unitypackage" von GitHub](https://aka.ms/azstorage-unitysdk). Führen Sie anschließend folgende Schritte aus:

1.  Hinzufügen der **.unitypackage** Datei in Unity mithilfe der **Assets > Paket importieren > benutzerdefiniertes Paket** Option des Menüs.

2.  In der **Unity-Paket importieren** Feld angezeigt, alles unter können Sie auswählen **-Plug-Ins* > *Storage**. Deaktivieren Sie alles andere, da sie für diesen Kurs nicht benötigt wird.

    ![Paket importieren](images/AzureLabs-Lab5-45.png)

3.  Klicken Sie auf die **Import** , um die Elemente zu Ihrem Projekt hinzuzufügen.

4.  Wechseln Sie zu der *Storage* Unterordner *-Plug-Ins*in der Projektansicht, und wählen Sie die folgenden Plug-Ins *nur*:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

        ![Deaktivieren Sie jede Plattform](images/AzureLabs-Lab5-46.png)

5.  Mit *bestimmte Plug-Ins* ausgewählt, **deaktivieren** *Any Platform* und **deaktivieren** *WSAPlayer* Klicken Sie dann auf **übernehmen**.

    ![Anwenden von Plattform-dlls](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > Wir markieren diese bestimmten Plug-Ins, die nur im Unity-Editor verwendet werden. Dies ist, da es gibt verschiedene Versionen der gleichen Plug-Ins in das WSA-Ordner, der verwendet wird und nachdem das Projekt aus Unity exportiert werden.

6.  In der *Storage* -Plug-in-Ordner, wählen Sie nur:

    -   Microsoft.Data.Services.Client

        ![Gruppe nicht für DLL-Dateien verarbeiten](images/AzureLabs-Lab5-48.png)

7.  Überprüfen Sie die **Don't Prozess** Feld *Plattformeinstellungen* , und klicken Sie auf **übernehmen**.

    ![keine Verarbeitung anwenden](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > Wir werden dieses Plug-in "Nicht verarbeiten" markieren, da die Unity-Assembly-Patcher schwierigkeiten beim Verarbeiten dieses Plug-in ist. Das Plug-in funktioniert weiterhin, auch wenn sie nicht verarbeitet wurde.

## <a name="chapter-7---create-the-azureservices-class"></a>Kapitel 7: Erstellen Sie die AzureServices-Klasse

Die erste Klasse, die Sie erstellen wollen ist die *AzureServices* Klasse.

Die *AzureServices* Klasse ist zuständig für:

-   Das Speichern von Anmeldeinformationen für Azure-Konto.

-   Aufrufen von Ihrer Azure-App-Funktion.

-   Der Upload und Download von der Datendatei in Ihrem Azure-Cloudspeicher.

Zum Erstellen dieser Klasse:

1.  Mit der rechten Maustaste den *Asset* Ordner befindet sich im Projektfenster **erstellen > Ordner**. Nennen Sie den Ordner **Skripts**.

    ![neuen Ordner erstellen](images/AzureLabs-Lab5-50.png)

    ![Rufen Sie die Ordner - Skripts](images/AzureLabs-Lab5-51.png)

2.  Doppelklicken Sie auf den Ordner, der gerade erstellt haben, um ihn zu öffnen.

3.  Mit der rechten Maustaste in den Ordner **erstellen > C# Skript**. Rufen Sie das Skript *AzureServices*.

4.  Doppelklicken Sie auf dem neuen *AzureServices* Klasse, öffnen Sie ihn mit *Visual Studio*.

5.  Fügen Sie die folgenden Namespaces am Anfang der *AzureServices*:

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  Fügen Sie die folgenden Inspektor-Felder in der *AzureServices* Klasse:

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  Fügen Sie dann die folgenden Membervariablen in der *AzureServices* Klasse:

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > Stellen Sie sicher, dass Sie ersetzen die *Endpunkt* und *Verbindungszeichenfolge* durch die Werte aus Ihrem Azure-Speicher finden Sie im Azure-Portal

8.  Code für *Awake()* und *Start()* Methoden jetzt hinzugefügt werden muss. Diese Methoden werden aufgerufen, wenn die Klasse initialisiert:

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > Wir werden Geben Sie den Code für *CallAzureFunctionForNextShape()* in eine [zukünftige Kapitel](#chapter-10---completing-the-AzureServices-class).

9.  Löschen der *Update()* Methode, da diese Klasse nicht verwendet wird.

10. Speichern Sie die Änderungen in Visual Studio, und klicken Sie dann zurück zu Unity.

11. Klicken Sie auf, und ziehen Sie die *AzureServices* Klasse aus dem Ordner Scripts, um die Main Camera-Objekts in der *Hierarchie Bereich*.

12. Wählen Sie die Main Camera, und ziehen Sie die **AzureStatusText** untergeordnetes Objekt aus, unter der **GazeButton** Objekt aus, und platzieren Sie sie in der **AzureStatusText** Verweisziel Feld, in der *Inspektor*, geben Sie den Verweis auf die *AzureServices* Skript.

    ![Weisen Sie Azure-Status Text Verweisziel](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a>Kapitel 8 – erstellen Sie die ShapeFactory-Klasse

Das nächste Skript zu erstellen, wird die *ShapeFactory* Klasse. Die Rolle von dieser Klasse besteht darin, während der Erstellung einer neuen Form angefordert, und Speichern eines Verlaufs der Formen in erstellt eine *Form Verlaufsliste*. Jedes Mal ein Shape erstellt wird, die *Form Verlaufsliste* wird aktualisiert, der *AzureService* Klasse, und klicken Sie dann in gespeichert Ihre *Azure Storage*. Beim Starten der Anwendung, wenn eine gespeicherte Datei, in gefunden wird Ihre *Azure Storage*, *Form Verlaufsliste* abgerufen und wiedergegeben, mit der **3D-Text** mit Gibt an, ob die generierte Form aus dem Speicher oder neuer ist.

Diese Klasse zu erstellen:

1.  Wechseln Sie zu der **Skripts** Ordner, die Sie zuvor erstellt haben.

2.  Mit der rechten Maustaste in den Ordner **erstellen > C# Skript**. Rufen Sie das Skript *ShapeFactory*.

3.  Doppelklicken Sie auf dem neuen *ShapeFactory* Skript öffnen Sie ihn mit *Visual Studio*.

4.  Stellen Sie sicher die *ShapeFactory* Klasse enthält die folgenden Namespaces:

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  Fügen Sie die folgenden Variablen das *ShapeFactory* Klasse, und Ersetzen Sie die *Start()* und *Awake()* Funktionen mit den folgenden:

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  Die *CreateShape()* Methode generiert, die primitiven Formen auf Grundlage der bereitgestellten *Ganzzahl* Parameter. Der boolesche Parameter wird verwendet, um anzugeben, ob die gerade erstellte Form aus dem Speicher oder neuen. Platzieren Sie den folgenden Code in Ihre *ShapeFactory* -Klasse, unter der vorherigen Methoden:

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  Achten Sie darauf, dass Sie Ihre Änderungen vor der Rückgabe an Unity in Visual Studio zu speichern.

8.  Zurück in die Unity-Editor zu klicken und ziehen Sie die *ShapeFactory* -Klasse aus der **Skripts** Ordner, um die **Main Camera** -Objekt in der *Hierarchie Bereich*.

9. Mit der Main-Kamera, die ausgewählt werden Sie feststellen der *ShapeFactory* Skriptkomponente fehlt die *Spawn Punkt* Verweis. Um dies zu beheben, ziehen Sie die **ShapeSpawnPoint** -Objekt aus der *Hierarchie Bereich* auf die **Spawn Punkt** Verweisziel.

    ![Verweisziel Factory "Form" Gruppe](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a>Kapitel 9 – erstellen Sie die Blicke-Klasse

Ist das letzte Skript Sie müssen die *bestaunen* Klasse.

Diese Klasse ist zuständig für das Erstellen einer **Raycast** , wird von der Main-Kamera, welches Objekt erkannt, wird der Benutzer betrachten, vorwärts projiziert werden. In diesem Fall müssen die Raycast um festzustellen, ob der Benutzer ansieht der **GazeButton** Objekt in der Szene, und lösen Sie ein Verhalten.

Zum Erstellen dieser Klasse:

1.  Wechseln Sie zu der **Skripts** Ordner, die Sie zuvor erstellt haben.

2.  Mit der rechten Maustaste im Projektpanel, **erstellen > C# Skript**. Rufen Sie das Skript *bestaunen*.

3.  Doppelklicken Sie auf dem neuen *bestaunen* Skript öffnen Sie ihn mit *Visual Studio.*

4.  Stellen Sie sicher, dass es sich bei der folgende Namespace am Anfang des Skripts enthalten ist:

    ```csharp
        using UnityEngine;
    ```

5.  Klicken Sie dann fügen Sie die folgenden Variablen in der *bestaunen* Klasse:

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> Einige dieser Variablen kann bearbeitet werden, in der *Editor*.

6.  Code für die *Awake()* und *Start()* Methoden jetzt hinzugefügt werden muss.

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  Fügen Sie folgenden Code, der zusammen mit einem Cursor-Objekt am Anfang, erstellt die *Update()* -Methode, die ausgeführt wird, die Raycast-Methode, sowie, in dem der GazeEnabled boolesche ein-/ausgeschaltet wird:

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. Als Nächstes fügen die *UpdateRaycast()* Methode, dem Projekt eine Raycast und das Trefferanzahl-Ziel zu erkennen.

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;

                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. Abschließend fügen die *ResetFocusedObject()* -Methode, die umschalten wird die GazeButton Objekte aktuelle Farbe, der angibt, ob er eine neue Form oder nicht erstellt.

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  Speichern Sie die Änderungen in Visual Studio vor der Rückgabe in Unity.

11.  Klicken und ziehen Sie die *bestaunen* Klasse aus dem Ordner Scripts, um die **Main Camera** -Objekt in der *Hierarchie Bereich*.

## <a name="chapter-10---completing-the-azureservices-class"></a>Kapitel 10 – Abschließen der AzureServices-Klasse

Mit den anderen Skripts vorhanden, ist es jetzt möglich, *vollständige* der *AzureServices* Klasse. Dies wird durch erreicht werden:

1.  Hinzufügen einer neuen Methode mit dem Namen *CreateCloudIdentityAsync()*, um die Authentifizierung-Variablen, die erforderlich sind, für die Kommunikation mit Azure einzurichten.

    > Diese Methode überprüft auch das Vorhandensein einer zuvor gespeicherte Datei mit der Form-Liste.
    >
    > **Wenn die Datei gefunden wird**, wird es den Benutzer deaktiviert *bestaunen*, und die Form erstellen, nach dem Muster von Formen, die ausgelöst werden, da in gespeichert der **Azure Storage-Datei**. Der Benutzer dies sehen, wie die **Text Mesh** bieten anzeigen "Storage" oder "New", abhängig vom Ursprung Formen.
    >
    > **Wenn keine Datei gefunden wird**, können sie die *bestaunen*, aktivieren den Benutzer aus, um Formen zu erstellen, bei Betrachtung der **GazeButton** Objekts in der Szene.

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  Der nächste Codeausschnitt ist innerhalb der *Start()* Methode, bei dem ein Aufruf an vorgenommen werden, die *CreateCloudIdentityAsync()* Methode. Gerne über Ihre aktuellen kopieren *Start()* -Methode, mit der folgenden:

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  Geben Sie den Code für die Methode *CallAzureFunctionForNextShape()*. Verwenden Sie das zuvor erstellte *Azure Function-App* einen Index der Form "anfordern. Sobald die neue Form empfangen wird, sendet diese Methode die Form, um die *ShapeFactory* Klasse, um die neue Form in der Szene zu erstellen. Verwenden Sie den folgenden Code zum Abschließen des Texts der *CallAzureFunctionForNextShape()*.

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  Fügen Sie eine Methode zum Erstellen von einer Zeichenfolge, durch die Verkettung von ganzen Zahlen gespeichert, in der Verlaufsliste Form, und speichern es in Ihrer *Azure Storage File*.

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  Fügen Sie eine Methode zum Abrufen des Texts in der Datei im Verzeichnis gespeicherten Ihre *Azure Storage File* und *Deserialisieren* ihn in eine Liste.

6.  Sobald der Vorgang abgeschlossen ist, aktiviert erneut die Methode die Blicke, damit der Benutzer weitere Formen der Szene hinzugefügt werden kann.

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  Speichern Sie die Änderungen in Visual Studio vor der Rückgabe in Unity.

## <a name="chapter-11---build-the-uwp-solution"></a>Kapitel 11: Erstellen Sie die UWP-Projektmappe

Um den Buildprozess zu starten:

1.  Wechseln Sie zu **Datei > Buildeinstellungen**.

    ![Erstellen Sie die app](images/AzureLabs-Lab5-54.png)

2.  Klicken Sie auf **Erstellen**. Unity startet eine *Datei-Explorer* Fenster, in denen man erstellen, und wählen Sie einen Ordner zum Erstellen der app in. Erstellen Sie jetzt auf diesen Ordner, und nennen Sie es *App*. Klicken Sie dann mit der *App* Ordner ausgewählt haben, drücken Sie **Ordner auswählen**.

3.  Erstellen Ihres Projekts zu Unity beginnt die *App* Ordner.

4.  Einmal Unity wurde (es kann einige Zeit dauern) erstellen, öffnen ein *Datei-Explorer* Fenster am Speicherort des Builds (Überprüfen Sie Ihre Taskleiste aus, wie es unter Umständen nicht immer über Ihre Windows angezeigt und Sie über das Hinzufügen eines neuen benachrichtigt Fenster ").

## <a name="chapter-12---deploying-your-application"></a>Kapitel 12: Bereitstellen der Anwendung

Um die Anwendung bereitzustellen:

1.  Navigieren Sie zu der *App* Ordner, der erstellt wurde die [letzte Kapitel](#chapter-11---build-the-uwp-solution). Sehen Sie eine Datei durch den Namen der apps mit der Erweiterung ".sln", die Sie doppelklicken, sollten Sie so öffnen Sie sie in *Visual Studio*.

2.  In der **Projektmappenplattform**Option **X86, lokalen Computer**.

3.  In der **Projektmappenkonfiguration** wählen **Debuggen**.

    > Für die Microsoft HoloLens Umständen ist es einfacher, diese Einstellung auf *Remotecomputer*, sodass Sie nicht auf Ihren Computer angeschlossen sind. Allerdings müssen Sie auch die folgenden Schritte ausführen:
    > - Kennen der **IP-Adresse** von Ihrem HoloLens, die sich in befinden die *Einstellungen > Netzwerk und Internet > Wi-Fi > Erweiterte Optionen*; IPv4 ist die Adresse, die Sie verwenden sollten. 
    > - Stellen Sie sicher **Entwicklermodus** ist **auf**; gefunden in *Einstellungen > Update und Sicherheit > für Entwickler*.

    ![Bereitstellen der Lösung](images/AzureLabs-Lab5-55.png)

4.  Wechseln Sie zu der **erstellen** Menü, und klicken Sie auf **Projektmappe bereitstellen** zum querladen der Anwendung auf Ihrem Computer.

5.  Ihre App sollte nun angezeigt werden, in der Liste der installierten apps, die gestartet und getestet werden können.

## <a name="your-finished-azure-functions-and-storage-application"></a>Die fertige Azure Functions und Storage-Anwendung

Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die sowohl die Azure Functions und Azure Storage-Dienste nutzt. Ihre app wird in der Lage gespeicherten Daten, und geben Sie eine Aktion, die auf Basis dieser Daten.

![Endprodukt-Ende](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a>Bonus-Übungen

### <a name="exercise-1"></a>Übung 1

Erstellen Sie eine zweite erzeugen, Punkt und Datensatz, der Zeitpunkt zu erzeugen, die über ein Objekt erstellt wurde. Wenn Sie die Datei laden, Wiedergeben von Formen erzeugt wird, von dem Speicherort, die, den Sie erstellt wurden.

### <a name="exercise-2"></a>Übung 2

Erstellen Sie eine Möglichkeit zum Starten der app, anstatt ihn jedes Mal erneut öffnen. **Laden Szenen** ist ein guter Platz, um zu starten. Anschließend erstellen Sie eine Möglichkeit zum Löschen der gespeicherten Liste *Azure Storage*, sodass sie problemlos von Ihrer app zurückgesetzt werden kann. 
