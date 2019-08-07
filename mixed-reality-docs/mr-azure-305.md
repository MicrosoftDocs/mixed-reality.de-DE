---
title: Mr und Azure 305-Funktionen und Speicher
description: Arbeiten Sie diesen Kurs durch, um zu erfahren, wie Sie Azure Storage und Funktionen innerhalb einer gemischten Reality-Anwendung implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Funktionen, Speicher, hololens, immersive, VR
ms.openlocfilehash: 5f3d0c6990249bc32e4c0f55c72dd884c4c2214e
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694558"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a>Mr und Azure 305: Funktionen und Speicher

![Endgültiges Produkt-Start](images/AzureLabs-Lab5-00.png)

In diesem Kurs erfahren Sie, wie Sie Azure Functions und Daten mit einer Azure Storage Ressource in einer gemischten Reality-Anwendung erstellen und verwenden.

*Azure Functions* ist ein Microsoft-Dienst, der Entwicklern das Ausführen von kleinen Code Elementen ("Functions") in Azure ermöglicht. Dies bietet eine Möglichkeit zum Delegieren von Arbeit an die Cloud und nicht an Ihre lokale Anwendung, die viele Vorteile haben kann. *Azure Functions* unterstützt mehrere Entwicklungs Sprachen, wie\#z.\#b. C, F, Node. js, Java und PHP. Weitere Informationen finden Sie im [Artikel Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).

*Azure Storage* ist ein Microsoft-clouddienst, der es Entwicklern ermöglicht, Daten zu speichern, mit der Versicherung, dass Sie hoch verfügbar, sicher, dauerhaft, skalierbar und redundant ist. Dies bedeutet, dass Microsoft alle Wartungsarbeiten und kritischen Probleme für Sie behandelt. Weitere Informationen finden Sie im [Artikel Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-introduction).

Nachdem Sie diesen Kurs abgeschlossen haben, verfügen Sie über eine gemischte Reality-Headset-Anwendung, die Folgendes ausführen kann:

1.  Ermöglicht dem Benutzer das durchschauen einer Szene.
2.  Löst das Erzeugen von Objekten aus, wenn der Benutzer auf einer 3D-Schaltfläche ' ' geklickt hat.
3.  Die erzeugten Objekte werden von einer Azure-Funktion ausgewählt.
4.  Während jedes Objekt erzeugt wird, speichert die Anwendung den Objekttyp in einer *Azure-Datei*, die sich in *Azure Storage*befindet.
5.  Beim Laden eines zweiten Zeitraums werden die *Azure-Datei* Daten abgerufen und verwendet, um die erstellenden Aktionen aus der vorherigen Instanz der Anwendung wiederzugeben.

In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren. In diesem Kurs erfahren Sie, wie Sie einen Azure-Dienst in Ihr Unity-Projekt integrieren. Es ist Ihre Aufgabe, das wissen, das Sie aus diesem Kursgewinnen, zu nutzen, um ihre gemischte Reality-Anwendung zu verbessern.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>Mr und Azure 305: Funktionen und Speicher</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Dieser Kurs konzentriert sich in erster Linie auf Windows Mixed Reality immersive (VR)-Headsets, aber Sie können auch das, was Sie in diesem Kurs lernen, auf Microsoft hololens anwenden. Wenn Sie den Kurs befolgen, finden Sie Hinweise zu allen Änderungen, die Sie möglicherweise zur Unterstützung von hololens verwenden müssen.

## <a name="prerequisites"></a>Vorraussetzungen

> [!NOTE]
> Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen. Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Mai 2018). Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](install-the-tools.md) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt sind.

Für diesen Kurs empfehlen wir die folgende Hardware und Software:

- Einen Entwicklungs-PC, der [mit der Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for Immersive (VR)-Headset-Entwicklung kompatibel ist
- [Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus](install-the-tools.md#installation-checklist)
- [Das neueste Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Ein [Windows Mixed Reality-Headset (VR)](immersive-headset-hardware-details.md) oder [Microsoft hololens](hololens-hardware-details.md) mit aktiviertem Entwicklermodus
- Ein Abonnement für ein Azure-Konto zum Erstellen von Azure-Ressourcen
- Internet Zugriff für Azure-Setup und Datenabruf

## <a name="before-you-start"></a>Bevor Sie beginnen

Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).

## <a name="chapter-1---the-azure-portal"></a>Kapitel 1: Azure-Portal

Um den **Azure Storage-Dienst**zu verwenden, müssen Sie ein **Speicherkonto** in der Azure-Portal erstellen und konfigurieren.

1.  Melden Sie sich beim [Azure-Portal](https://portal.azure.com)an.

    > [!NOTE]
    > Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen. Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.

2.  Nachdem Sie angemeldet sind, klicken Sie in der oberen linken Ecke auf **neu** , suchen Sie nach *Speicherkonto*, und drücken Sie die **Eingabe**Taste.

    ![Azure Storage-Suche](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > Das Wort **New** wurde möglicherweise durch **Create a Resource**in neueren Portalen ersetzt.

3.  Auf der neuen Seite wird eine Beschreibung des *Azure Storage-Konto* Dienstanbieter bereitgestellt. Wählen Sie unten links in dieser Eingabeaufforderung die Schaltfläche **Erstellen** aus, um eine Verknüpfung mit diesem Dienst zu erstellen.

    ![Dienst erstellen](images/AzureLabs-Lab5-02.png)

4.  Nachdem Sie auf **Erstellen**geklickt haben, klicken Sie auf:

    1.  Fügen Sie einen *Namen* für Ihr Konto ein. Beachten Sie, dass dieses Feld nur Zahlen und Kleinbuchstaben akzeptiert.

    2.  Wählen Sie unter *Bereitstellungs Modell*die Option **Resource Manager**aus.

    3.  Wählen Sie unter *Kontoart*die Option **Speicher (universell, Version v1)** aus.

    4.  Bestimmen Sie den *Speicherort* für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen). Der Speicherort wäre idealerweise in der Region, in der die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.

    5.  Wählen Sie für die *Replikation* den **georedundanten Speicher mit Lesezugriff (RA-GRS)** aus.

    6.  Wählen Sie für *Leistung*die Option **Standard**aus.

    7.  Lassen Sie die Option " *sichere Übertragung erforderlich* " **deaktiviert**.

    8.  Wählen Sie ein *Abonnement*aus.

    9. Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue *Ressourcengruppe* . Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Labs) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern. 

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. Außerdem müssen Sie bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.

    11. Wählen Sie **Erstellen** aus.

        ![Eingabe Dienst Informationen](images/AzureLabs-Lab5-03.png)

5.  Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.

6.  Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![neue Benachrichtigung im Azure-Portal](images/AzureLabs-Lab5-04.png)

7.  Klicken Sie auf die Benachrichtigungen, um die neue Dienst Instanz zu untersuchen.

    ![Gehe zu Ressource](images/AzureLabs-Lab5-05.png)

8.  Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen. Sie gelangen zu ihrer neuen *Speicherkonto* -Dienst Instanz.

    ![Zugriffstasten](images/AzureLabs-Lab5-06.png)

9.  Klicken Sie auf *Zugriffsschlüssel*, um die Endpunkte für diesen Cloud-Dienst anzuzeigen. Verwenden Sie *Notepad* oder ähnliches, um einen Ihrer Schlüssel zur späteren Verwendung zu kopieren. Beachten Sie auch den Wert der *Verbindungs Zeichenfolge* , wie er in der *azureservices* -Klasse verwendet wird, die Sie später erstellen werden.

    ![Verbindungs Zeichenfolge kopieren](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a>Kapitel 2: Einrichten einer Azure-Funktion

Sie schreiben jetzt eine **Azure** - **Funktion** im Azure-Dienst.

Sie können eine **Azure-Funktion** verwenden, um nahezu alles zu tun, was Sie mit einer klassischen Funktion in Ihrem Code tun würden. der Unterschied besteht darin, dass jede Anwendung, die über Anmelde Informationen für den Zugriff auf Ihr Azure-Konto verfügt, auf diese Funktion zugreifen kann.

So erstellen Sie eine Azure-Funktion:

1.  Klicken Sie in Ihrem *Azure-Portal*in der oberen linken Ecke auf **neu** , suchen Sie nach *Funktionen-App*, und **drücken**Sie die EINGABETASTE.

    ![Erstellen einer Funktionen-App](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > Das Wort **New** wurde möglicherweise durch **Create a Resource**in neueren Portalen ersetzt.

2.  Auf der neuen Seite wird eine Beschreibung des *Azure-Funktionen-App* Dienstanbieter bereitgestellt. Wählen Sie unten links in dieser Eingabeaufforderung die Schaltfläche **Erstellen** aus, um eine Verknüpfung mit diesem Dienst zu erstellen.

    ![Funktions-APP-Informationen](images/AzureLabs-Lab5-09.png)

3.  Nachdem Sie auf **Erstellen**geklickt haben, klicken Sie auf:

    1.  Geben Sie einen *APP-Namen*an. Hier können nur Buchstaben und Ziffern verwendet werden (groß-oder Kleinbuchstaben sind zulässig).

    2.  Wählen Sie Ihr bevorzugtes *Abonnement*aus.

    3. Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue *Ressourcengruppe* . Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Labs) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern. 

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Wählen Sie für diese Übung *Windows* als ausgewähltes **Betriebssystem**aus.

    5.  Wählen Sie den *Verbrauchs Plan* für den **Hostingplan**aus.

    6.  Bestimmen Sie den *Speicherort* für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen). Der Speicherort wäre idealerweise in der Region, in der die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar. Wählen Sie die gleiche Region wie das Speicherkonto aus, um eine optimale Leistung zu erzielen.

    7.  Wählen Sie für *Speicher*die Option **vorhandene verwenden**aus, und suchen Sie dann mithilfe des Dropdown Menüs nach dem zuvor erstellten Speicher.

    8.  Lassen Sie für diese Übung *Application Insights* deaktiviert.

        ![Details der Eingabefunktionen-App](images/AzureLabs-Lab5-10.png)

4.  Klicken Sie auf die Schaltfläche **Erstellen**.

5.  Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.

6.  Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Benachrichtigung über das neue Azure-Portal](images/AzureLabs-Lab5-11.png)

7.  Klicken Sie auf die Benachrichtigungen, um die neue Dienst Instanz zu untersuchen. 

    ![Gehe zu Ressourcen Funktions-APP](images/AzureLabs-Lab5-12.png)

8.  Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen. Sie gelangen zu ihrer neuen *Funktionen-App* Dienst Instanz.

9.  Zeigen Sie im *Funktionen-App* Dashboard mit der Maus auf *Funktionen*, die sich im Bereich auf der linken Seite befinden, und klicken Sie dann auf das Symbol **+ (plus)** .

    ![neue Funktion erstellen](images/AzureLabs-Lab5-13.png)

10. Vergewissern Sie sich auf der nächsten Seite, dass **webhook + API** ausgewählt ist, und wählen Sie für *Sprache auswählen* die Option **CSharp**aus, da es sich hierbei um die für dieses Tutorial verwendete Sprache handelt. Klicken Sie abschließend auf die Schaltfläche **Diese Funktion erstellen** .

    ![webhook CSharp auswählen](images/AzureLabs-Lab5-14.png)

11. Sie sollten zur Codepage (Run. CSX) weitergeleitet werden. Klicken Sie auf der linken Seite auf die neu erstellte Funktion in der Liste der Funktionen, und klicken Sie dann auf der linken Seite auf die neu erstellte Funktion.

    ![neue Funktion öffnen](images/AzureLabs-Lab5-15.png)

12. Kopieren Sie den folgenden Code in die-Funktion. Diese Funktion gibt einfach eine zufällige Ganzzahl zwischen 0 und 2 zurück, wenn aufgerufen wird. Machen Sie sich keine Sorgen um den vorhandenen Code, und Sie können ihn über den Anfang einfügen.

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

15. Klicken Sie auf **Get Function URL** , und notieren Sie sich den angezeigten *Endpunkt* . Sie müssen Sie in die *azureservices* -Klasse einfügen, die Sie später in diesem Kurs erstellen werden.

    ![Get-Funktions Endpunkt](images/AzureLabs-Lab5-16.png)

    ![Get-Funktions Endpunkt](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a>Kapitel 3: Einrichten des Unity-Projekts

Folgendes ist eine typische Einrichtung für die Entwicklung mit gemischter Realität und ist daher eine gute Vorlage für andere Projekte.

Richten Sie Ihr immersives Headset mit gemischter Realität ein und testen Sie es.

> [!NOTE]
> Für diesen Kurs benötigen Sie **keine** Bewegungs Controller. Wenn Sie Unterstützung beim Einrichten des immersiven Headsets benötigen, [besuchen Sie den Artikel Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)-Einrichtung.

1.  Öffnen Sie Unity, und klicken Sie auf **neu**.

    ![neues Unity-Projekt erstellen](images/AzureLabs-Lab5-17.png)

2.  Sie müssen nun einen Unity-Projektnamen angeben. Fügen Sie **MR_Azure_Functions**ein. Stellen Sie sicher, dass Projekttyp auf **3D**festgelegt ist. Legen Sie den Speicherort auf einen geeigneten *Speicherort* fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind). Klicken Sie dann auf **Projekt erstellen**.

    ![neues Unity-Projekt benennen](images/AzureLabs-Lab5-18.png)

3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist. Wechseln Sie zu**Einstellungen** **Bearbeiten** > , und navigieren Sie dann im neuen Fenster zu **externe Tools**. Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**. Schließen Sie das Fenster " **Einstellungen** ".

    ![Festlegen von Visual Studio als Skript-Editor](images/AzureLabs-Lab5-19.png)

4.  Navigieren Sie als nächstes zu > dateibuildeinstellungen, und schalten Sie die Plattform auf **universelle Windows-Plattform**, indem Sie auf die Schaltfläche **Plattform wechseln** klicken.

    ![Plattform zu UWP wechseln](images/AzureLabs-Lab5-20.png)

5.  Wechseln Sie zu > dateibuildeinstellungen, und stellen Sie Folgendes sicher:

    1. Das **Zielgerät** ist auf **ein beliebiges Gerät**festgelegt.

        > Legen Sie für Microsoft hololens das **Zielgerät** auf *hololens*fest.

    2. Der Buildtyp ist auf **D3D** festgelegt.

    3. **SDK** ist auf **neueste installierte** Version festgelegt.

    4. **Visual Studio-Version** ist auf **neueste installierte** Version festgelegt.

    5. **Build und Run** sind auf **lokaler Computer** festgelegt.

    6. Speichern Sie die Szene, und fügen Sie Sie dem Build hinzu.

        1.  Wählen Sie hierzu die Option **geöffnete Szenen hinzufügen**aus. Ein Fenster zum Speichern wird angezeigt.

            ![Hinzufügen offener Szenen](images/AzureLabs-Lab5-21.png)

        2.  Erstellen Sie einen neuen Ordner für dieses und jede zukünftige Szene, und wählen Sie dann die Schaltfläche **neuer Ordner** aus, um einen neuen Ordner zu **erstellen.**

            ![Ordner "Create Szenen"](images/AzureLabs-Lab5-22.png)

        3.  Öffnen Sie den neu erstellten **Szenen** Ordner, geben Sie im Feld **Dateiname:** Text **functionsscene**ein, und klicken Sie dann auf **Speichern**.

            ![Functions-Szene speichern](images/AzureLabs-Lab5-23.png)

6.  Die restlichen Einstellungen in denBuildeinstellungen sollten vorerst als Standard belassen werden.

    ![Functions-Szene speichern](images/AzureLabs-Lab5-24.png)

7.  Klicken Sie im Fenster Buildeinstellungen auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der *Inspektor* befindet.

    ![Player Einstellungen in Inspektor](images/AzureLabs-Lab5-25.png)

8.  In diesem Bereich müssen einige Einstellungen überprüft werden:

    1.  Auf der Registerkarte **andere Einstellungen** :

        1.  Die CLR- **Lauf Zeit Version** sollte **experimentell** sein (.NET 4,6-Entsprechung), wodurch der Editor neu gestartet werden muss.
        2.  **Skript** -Back-End sollte **.net** sein
        3.  **API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten

    2.  Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:
        
        -  **Internet Client deklarieren**

            ![Festlegen von Funktionen](images/AzureLabs-Lab5-26.png)

    3.  Weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), **unterstützt Tick Virtual Reality**, stellen Sie sicher, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.

        ![XR-Einstellungen festlegen](images/AzureLabs-Lab5-27.png)

9.  Zurück in Buildeinstellungen: *Unity C# -Projekte* sind nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen neben this.

    ![Tick-c#-Projekte](images/AzureLabs-Lab5-28.png)

10.  Schließen Sie das Fenster mit den Buildeinstellungen.

11. Speichern Sie Ihre Szene und Ihr Projekt (**Datei** > **Speichern/Datei** > **speichern Projekt**).

## <a name="chapter-4---setup-main-camera"></a>Kapitel 4: Einrichten der Hauptkamera

> [!IMPORTANT]
> Wenn Sie die *Unity-Setup* Komponenten dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie [dieses. unitypackage herunterladen](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)und als [benutzerdefiniertes Paket](https://docs.unity3d.com/Manual/AssetPackages.html)in das Projekt importieren. Dies enthält auch die DLLs aus dem nächsten Kapitel. Fahren Sie nach dem Import aus [Kapitel 7](#chapter-7---create-the-azureservices-class)fort. 

1.  Im *Hierarchie Panel*finden Sie ein Objekt mit dem Namen " **Main Camera**". dieses Objekt stellt den "Head"-Punkt dar, sobald Sie die Anwendung "in" haben.

2.  Wählen Sie mit dem Unity-Dashboard vor Ihnen das **Hauptkamera-gameobject**aus. Sie werden feststellen, dass im *Inspektor-Panel* (in der Regel auf der rechten Seite im Dashboard) die verschiedenen Komponenten dieses *gameobject*angezeigt werden, mit der *Transformation* am oberen Rand, gefolgt von der *Kamera*und einigen anderen Komponenten. Sie müssen die Transformation der Hauptkamera zurücksetzen, damit Sie ordnungsgemäß positioniert ist.

3.  Wählen Sie dazu das **Zahnrad** Symbol neben der *Transformations* Komponente der Kamera aus, und klicken Sie auf **Zurücksetzen**.

    ![Transformation zurücksetzen](images/AzureLabs-Lab5-29.png)

4.  Aktualisieren Sie dann die **Transformations** Komponente so, dass Sie wie folgt aussieht:

    |         |    TRANSFORMATION-POSITION   |       |
    | :-----: | :-----------------------: | :----:|
    | **STUBEN**   | **TEENIE**                     | **Z** |
    | 0       | 1                         | 0     |    

    |       | TRANSFORMATION-DREHUNG |       |
    | :---: | :------------------: | :----:|
    | **STUBEN** | **TEENIE**                | **Z** |
    | 0     | 0                    | 0     |

    |       | TRANSFORMIEREN: SKALIEREN |       |
    | :---: | :---------------: | :---: |
    | **STUBEN** | **TEENIE**             | **Z** |
    | 1     | 1                 | 1     |

    ![Kamera Transformation festlegen](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a>Kapitel 5: Einrichten der Unity-Szene

1.  Klicken Sie mit der rechten Maustaste in einen leeren Bereich des Bereichs *Hierarchie*, und fügen Sie unter **3D-Objekt**eine **Ebene**hinzu.

    ![neue Ebene erstellen](images/AzureLabs-Lab5-31.png)

2.  Ändern Sie bei ausgewähltem **Plane** -Objekt im Inspektor- *Panel*die folgenden Parameter:

    |       | TRANSFORMATION-POSITION |       |
    | :---: | :------------------: | :---: |
    | **STUBEN** | **TEENIE**                | **Z** |
    | 0     | 0                    | 4     |

    |       | TRANSFORMIEREN: SKALIEREN |       |
    | :---: | :---------------: | :---: |
    | **STUBEN** | **TEENIE**             | **Z** |
    | 10    | 1                 | 10    |

    ![Festlegen der Position und Skala der Ebene](images/AzureLabs-Lab5-32.png)

    ![Szenen Ansicht der Ebene](images/AzureLabs-Lab5-33.png)

3.  Klicken Sie mit der rechten Maustaste in einen leeren Bereich des Bereichs *Hierarchie*, und fügen Sie unter **3D-Objekt**einen **Cube**hinzu.

    1.  Benennen Sie den Cube in " **gazebutton** " um (während der Cube ausgewählt ist, drücken Sie "F2").

    2.  Ändern Sie im *Inspektor-Panel*die folgenden Parameter:

        |       | TRANSFORMATION-POSITION |       |
        | :---: | :------------------: |:-----:|
        | **STUBEN** | **TEENIE**                | **Z** |
        | 0     | 3                    | 5     |


        ![Schaltflächen Transformation für den Blick festlegen](images/AzureLabs-Lab5-34.png)

        ![Ansicht "Ansicht" der Ansicht](images/AzureLabs-Lab5-35.png)

    3.  Klicken Sie auf die Dropdown Schaltfläche **Tag** , und klicken Sie auf **Tag hinzufügen** , um den Bereich *Tags & Ebenen*zu öffnen.

        ![neues Tag hinzufügen](images/AzureLabs-Lab5-36.png)

        ![Plus auswählen](images/AzureLabs-Lab5-37.png)

    4.  Wählen Sie die Schaltfläche **+ (plus)** aus, und geben Sie im Feld *neuer Tagname den Namen* " **gazebutton**" ein, und klicken Sie auf **Speichern**.

        ![neuer Tag benennen](images/AzureLabs-Lab5-38.png)

    5.  Klicken Sie im *Hierarchie Panel*auf das Objekt " **gazebutton** ", und weisen Sie im *Inspektor-Panel*das neu erstellte " **gazebutton** "-Tag zu.

        ![Schaltfläche "Blick" für den neuen Tag zuweisen](images/AzureLabs-Lab5-39.png)

4.  Klicken Sie mit der rechten Maustaste auf das **gazebutton** -Objekt im Bereich *Hierarchie*, und fügen Sie ein **leeres gameobject-Objekt** hinzu (das als unter *geordnetes Objekt hinzu* gefügt wird).

5.  Wählen Sie das neue Objekt aus, und benennen Sie es **shapespawnpoint**um.

    1.  Ändern Sie im *Inspektor-Panel*die folgenden Parameter:

        |       | TRANSFORMATION-POSITION |       |
        | :---: | :------------------: |:----: |
        | **STUBEN** |**TEENIE**                 | **Z** |
        | 0     | -1                   | 0     |

        ![Transformation für Erstellungspunkt aktualisieren](images/AzureLabs-Lab5-40.png)

        ![Szenen Ansicht des Shape-Spawn-Punkts](images/AzureLabs-Lab5-41.png)

6.  Als Nächstes erstellen Sie ein **3D-Text** Objekt, um Feedback zum Status des Azure-Dienstanbieter zu erhalten.

    Klicken Sie erneut mit der rechten Maustaste auf die **Schaltfläche** , und fügen Sie ein 3D- **Objekt** > **3D-Text** Objekt als untergeordnetes Element *hinzu.*

    ![Erstellen eines neuen 3D-Text Objekts](images/AzureLabs-Lab5-42.png)

7.  Benennen Sie das **3D-Text** Objekt in **azurestatustext**um.

8.  Ändern Sie die **azurestatustext** -Objekt Transformation wie folgt:

    |       | TRANSFORMATION-POSITION |       |
    | :---: | :------------------: | :---: |
    | **STUBEN** | **TEENIE**                | **Z** |
    | 0     | 0                    | -0,6  |

    |       | TRANSFORMIEREN: SKALIEREN |       |
    | :---: | :---------------: | :---: |
    | **STUBEN** | **TEENIE**             | **Z** |
    | 0,1   | 0,1               | 0,1   |


    > [!NOTE]
    > Machen Sie sich keine Sorgen, wenn Sie außerhalb der Mitte angezeigt werden, da dies korrigiert wird, wenn die folgende textmesh-Komponente aktualisiert wird.

9.  Ändern Sie die **textmesh** -Komponente entsprechend der folgenden:

    ![textmesh-Komponente festlegen](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > Die hier ausgewählte Farbe ist Hex-Farbe: **000000FF**, auch wenn Sie sich selbst entscheiden können, stellen Sie sicher, dass es lesbar ist.

10. Ihre Hierarchie Panel-Struktur sollte nun wie folgt aussehen:

    ![textmesh in der Szene Ansicht](images/AzureLabs-Lab5-43b.png)

10. Ihre Szene sollte nun wie folgt aussehen:

    ![textmesh in der Szene Ansicht](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a>Kapitel 6: Importieren von Azure Storage für Unity

Sie verwenden Azure Storage für Unity (das wiederum das .NET SDK für Azure nutzt). Weitere Informationen hierzu finden Sie im [Artikel Azure Storage für Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).

Zurzeit gibt es ein bekanntes Problem in Unity, das erfordert, dass Plug-ins nach dem Importieren neu konfiguriert werden. Diese Schritte (4-7 in diesem Abschnitt) werden nicht mehr benötigt, nachdem der Fehler behoben wurde.

Um das SDK in Ihr eigenes Projekt zu importieren, stellen Sie sicher, dass Sie das neueste [". unitypackage" aus GitHub](https://aka.ms/azstorage-unitysdk)heruntergeladen haben. Gehen Sie dann wie folgt vor:

1.  Fügen Sie die **. unitypackage** -Datei zu Unity hinzu, indem Sie die Menüoption **Assets** > **Import Package** > **Custom Package** verwenden.

2.  Im Feld " **Unity-Paket importieren** ", das angezeigt wird, können Sie unter **Plug** > -in-**Speicher**alles auswählen. Deaktivieren Sie alles andere, da es für diesen Kurs nicht benötigt wird.

    ![in Paket importieren](images/AzureLabs-Lab5-45.png)

3.  Klicken Sie auf die Schaltfläche **importieren** , um dem Projekt die Elemente hinzuzufügen.

4.  Wechseln Sie in der Projektansicht *unter Plug*-in zum Ordner *Speicher* , und wählen Sie *nur*die folgenden Plug-ins aus:

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft. WindowsAzure. Storage
    -   Newtonsoft.Json
    -   System.Spatial

        ![alle Plattformen deaktivieren](images/AzureLabs-Lab5-46.png)

5.  Wenn *Sie diese speziellen* Plug-Ins **ausgewählt haben,** deaktivieren Sie *eine beliebige Plattform* , deaktivieren Sie *wsaplayer* **, und klicken** Sie auf **anwenden**.

    ![Platt Form-DLLs anwenden](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > Wir markieren diese bestimmten Plug-ins, sodass Sie nur im Unity-Editor verwendet werden. Dies liegt daran, dass im WSA-Ordner verschiedene Versionen der gleichen Plug-ins vorhanden sind, die nach dem Exportieren des Projekts aus Unity verwendet werden.

6.  Wählen Sie im Ordner *Storage* -Plug-in nur die Option:

    -   Microsoft. Data. Services. Client

        !["nicht verarbeiten" für DLLs festlegen](images/AzureLabs-Lab5-48.png)

7.  Aktivieren Sie das Kontrollkästchen **nicht verarbeiten** unter *Platt Form Einstellungen* , und klicken Sie auf **anwenden**.

    ![keine Verarbeitung anwenden](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > Wir markieren dieses Plug-in "nicht verarbeiten", da das Unity-assemblypatcher Probleme beim Verarbeiten dieses Plug-ins hat. Das Plug-in funktioniert weiterhin, auch wenn es nicht verarbeitet wird.

## <a name="chapter-7---create-the-azureservices-class"></a>Kapitel 7: Erstellen der azureservices-Klasse

Die erste Klasse, die Sie erstellen, ist die *azureservices* -Klasse.

Die *azureservices* -Klasse ist für Folgendes zuständig:

-   Azure-Konto Anmelde Informationen werden gespeichert.

-   Der Azure-App-Funktion wird aufgerufen.

-   Hochladen und Herunterladen der Datendatei in Ihrem Azure-cloudspeicher.

So erstellen Sie diese Klasse:

1.  Klicken Sie mit der rechten Maustaste in den Ordner *Asset* , und klicken Sie im Projekt Panel auf**Ordner** **Erstellen** > . Benennen Sie den Ordner mit **Skripts**.

    ![neuen Ordner erstellen](images/AzureLabs-Lab5-50.png)

    ![callordnerskripts](images/AzureLabs-Lab5-51.png)

2.  Doppelklicken Sie auf den soeben erstellten Ordner, um ihn zu öffnen.

3.  Klicken Sie mit der rechten Maustaste in den Ordner, und **Erstellen**  >  **C#** Sie das Skript Nennen Sie das Skript *azureservices*.

4.  Doppelklicken Sie auf die neue Klasse *azureservices* , um Sie in *Visual Studio*zu öffnen.

5.  Fügen Sie am Anfang der *azureservices*die folgenden Namespaces hinzu:

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  Fügen Sie die folgenden Inspektor-Felder in der *azureservices* -Klasse hinzu:

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

7.  Fügen Sie dann die folgenden Element Variablen in der *azureservices* -Klasse hinzu:

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
    > Stellen Sie sicher, dass Sie die Werte für *Endpunkt* und *Verbindungs Zeichenfolge* durch die Werte aus Ihrem Azure-Speicher im Azure-Portal ersetzen.

8.  Der Code für die Methoden " *Awake ()* " und " *Start ()* " muss nun hinzugefügt werden. Diese Methoden werden aufgerufen, wenn die-Klasse initialisiert:

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
    > In einem [zukünftigen Kapitel](#chapter-10---completing-the-azureservices-class)wird der Code für *callazurefunctionfornextshape ()* ausgefüllt.

9.  Löschen Sie die *Update ()* -Methode, da Sie von dieser Klasse nicht verwendet wird.

10. Speichern Sie die Änderungen in Visual Studio, und kehren Sie dann zu Unity zurück.

11. Klicken und ziehen Sie die Klasse *azureservices* aus dem Ordner Scripts auf das Hauptkamera Objekt im Bereich *Hierarchie*.

12. Wählen Sie die Hauptkamera aus, und rufen Sie dann das untergeordnete **azurestatustext** -Objekt unter dem **gazebutton** -Objekt ab, und platzieren Sie es innerhalb des Felds **azurestatustext** -Verweis Ziel im *Inspektor*, um den Verweis auf das  *Azureservices* -Skript.

    ![Azure-Status-Text Verweis Ziel zuweisen](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a>Kapitel 8: Erstellen der shapefactory-Klasse

Das nächste Skript, das erstellt werden soll, ist die *shapefactory* -Klasse. Die Rolle dieser Klasse besteht darin, eine neue Form zu erstellen, wenn Sie angefordert wird, und einen Verlauf der Formen beizubehalten, die in einer Shape-Verlaufs *Liste*erstellt wurden. Jedes Mal, wenn eine Form erstellt wird, wird die Shape-Verlaufs *Liste* in der *azureservice* -Klasse aktualisiert und dann in Ihrem *Azure Storage*gespeichert. Wenn die Anwendung gestartet wird und eine gespeicherte Datei in der *Azure Storage*gefunden wird, wird die *Shape* -Verlaufs Liste abgerufen und wiedergegeben, wobei das **3D-Text** Objekt bereitstellt, ob die generierte Form aus Storage oder New ist.

So erstellen Sie diese Klasse:

1.  Wechseln Sie zum Ordner " **Scripts** ", den Sie zuvor erstellt haben.

2.  Klicken Sie mit der rechten Maustaste in den Ordner, und **Erstellen**  >  **C#** Sie das Skript Nennen Sie das Skript *shapefactory*.

3.  Doppelklicken Sie auf das neue *shapefactory* -Skript, um es in *Visual Studio*zu öffnen.

4.  Stellen Sie sicher, dass die *shapefactory* -Klasse die folgenden Namespaces umfasst:

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  Fügen Sie die unten gezeigten Variablen der *shapefactory* -Klasse hinzu, und ersetzen Sie die Funktionen " *Start ()* " und " *Awa()* " durch die folgenden:

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

6.  Die Methode " *kreateshape ()* " generiert die primitiven Formen basierend auf dem bereitgestellten *ganzzahligen* Parameter. Der boolesche Parameter wird verwendet, um anzugeben, ob die derzeit erstellte Form aus Storage oder New ist. Platzieren Sie den folgenden Code in der *shapefactory* -Klasse unter den vorherigen Methoden:

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

7.  Stellen Sie sicher, dass Sie die Änderungen in Visual Studio speichern, bevor Sie zu Unity zurückkehren.

8.  Klicken Sie im Unity-Editor auf die *shapefactory* -Klasse, und ziehen Sie Sie aus dem Ordner **Scripts** auf das **Hauptkamera** Objekt im *Hierarchie Panel*.

9. Wenn die Hauptkamera ausgewählt ist, sehen Sie, dass in der *shapefactory* -Skript Komponente der Verweis *Punkt* Verweis fehlt. Um dieses Problem zu beheben, ziehen Sie das **shapespawnpoint** -Objekt aus dem Bereich *Hierarchie* in das Referenz Ziel des-pullpunkts.

    ![Shape-Factory-Verweis Ziel festlegen](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a>Kapitel 9: Erstellen der "Blick"-Klasse

Das letzte Skript, das Sie erstellen müssen, ist die " *Gaze* "-Klasse.

Diese Klasse ist für das Erstellen eines **raycast** verantwortlich, der von der Hauptkamera projiziert wird, um zu erkennen, welches Objekt der Benutzer untersucht. In diesem Fall muss der raycast ermitteln, ob der Benutzer das **gazebutton** -Objekt in der Szene prüft und ein Verhalten auslöst.

So erstellen Sie diese Klasse:

1.  Wechseln Sie zum Ordner " **Scripts** ", den Sie zuvor erstellt haben.

2.  Klicken Sie im Projekt Panel mit der rechten Maustaste, und **Erstellen**  >  **C#** Sie ein Skript. Ruft den Skript *Blick*auf.

3.  Doppelklicken Sie auf das neue *Blick* Skript, um es in *Visual Studio* zu öffnen.

4.  Stellen Sie sicher, dass der folgende Namespace am Anfang des Skripts enthalten ist:

    ```csharp
        using UnityEngine;
    ```

5.  Fügen Sie dann die folgenden Variablen in der " *Blick* "-Klasse hinzu:

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
> Einige dieser Variablen können im *Editor*bearbeitet werden.

6.  Der Code für die Methoden " *Awake ()* " und " *Start ()* " muss nun hinzugefügt werden.

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

7.  Fügen Sie den folgenden Code hinzu, mit dem ein Cursor Objekt beim Start zusammen mit der *Update ()* -Methode erstellt wird, die die raycast-Methode ausgeführt wird, sowie den Speicherort für den booleschen Wert für die instanzaktivierung:

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

8. Fügen Sie als nächstes die *updateraycast ()* -Methode hinzu, die ein raycast-Projekt erstellt und das Treffer Ziel erkennt.

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

9. Fügen Sie abschließend die *resetfocusedobject ()* -Methode hinzu, die die aktuelle Farbe der gazebutton-Objekte umschalten und angibt, ob eine neue Form erstellt wird.

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

10.  Speichern Sie die Änderungen in Visual Studio, bevor Sie zu Unity zurückkehren.

11.  Klicken und ziehen Sie die Klasse " *Blick* " aus dem Ordner Scripts auf das **Hauptkamera** Objekt im Bereich *Hierarchie*.

## <a name="chapter-10---completing-the-azureservices-class"></a>Kapitel 10: vervollständigen der azureservices-Klasse

Wenn die anderen Skripts vorhanden sind, ist es jetzt möglich, die *azureservices* -Klasse *abzuschließen* . Dies wird durch Folgendes erreicht:

1.  Fügen Sie eine neue Methode mit dem Namen " *foratecloudidentityasync ()* " hinzu, um die Authentifizierungs Variablen einzurichten, die für die Kommunikation mit Azure erforderlich sind.

    > Mit dieser Methode wird auch überprüft, ob eine zuvor gespeicherte Datei mit der Form Liste vorhanden ist.
    >
    > **Wenn die Datei gefunden**wird, deaktiviert Sie den Benutzer *Blick*und löst die Form Erstellung gemäß dem Muster der Formen aus, wie Sie in der Azure Storage- **Datei**gespeichert werden. Der Benutzer kann dies sehen, da im **textmesh** abhängig vom Ursprung der Formen "Storage" oder "New" angezeigt wird.
    >
    > **Wenn keine Datei gefunden**wird, wird der *Blick*aktiviert, sodass der Benutzer bei der Betrachtung des **gazebutton** -Objekts in der Szene Formen erstellen kann.

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

2.  Der nächste Code Ausschnitt erfolgt innerhalb der Methode " *Start ()* ". Dabei wird ein-Rückruf an die Methode "Methode" von "| *atecloudidentityasync ()* " durchgeführt. Sie können Ihre aktuelle *Start ()* -Methode mit den folgenden Informationen kopieren:

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

3.  Geben Sie den Code für die Methode *callazurefunctionfornextshape ()* ein. Sie verwenden den zuvor erstellten *Azure-Funktionen-App* , um einen Form Index anzufordern. Nachdem die neue Form empfangen wurde, sendet diese Methode die Form an die *shapefactory* -Klasse, um die neue Form in der Szene zu erstellen. Verwenden Sie den folgenden Code, um den Text von *callazurefunctionfornextshape ()* abzuschließen.

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

4.  Fügen Sie eine Methode hinzu, um eine Zeichenfolge zu erstellen, indem Sie die in der Form Verlaufs Liste gespeicherten Ganzzahlen verketten und in Ihrer *Azure Storage Datei*speichern.

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

5.  Fügen Sie eine Methode hinzu, um den in der Datei gespeicherten Text in der *Azure Storage-Datei* abzurufen und in eine Liste zu *Deserialisieren* .

6.  Sobald dieser Vorgang abgeschlossen ist, aktiviert die Methode den Blick erneut, sodass der Benutzer der Szene weitere Formen hinzufügen kann.

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

7.  Speichern Sie die Änderungen in Visual Studio, bevor Sie zu Unity zurückkehren.

## <a name="chapter-11---build-the-uwp-solution"></a>Kapitel 11: Erstellen der UWP-Lösung

So beginnen Sie den Buildprozess:

1.  Wechseln Sie zu > dateibuildeinstellungen.

    ![Erstellen der APP](images/AzureLabs-Lab5-54.png)

2.  Klicken Sie auf **Erstellen**. Unity startet ein *Datei-Explorer* -Fenster, in dem Sie einen Ordner erstellen und auswählen müssen, in dem die App erstellt wird. Erstellen Sie diesen Ordner jetzt, und nennen Sie ihn " *App*". Klicken Sie dann mit ausgewähltem *App* -Ordner auf **Ordner auswählen**.

3.  Unity startet das Projekt in den *App* -Ordner.

4.  Nachdem die Erstellung von Unity abgeschlossen ist (Dies kann einige Zeit in Anspruch nehmen), wird ein *Datei-Explorer* -Fenster am Speicherort des Builds geöffnet (überprüfen Sie die Taskleiste, da Sie möglicherweise nicht immer über Ihrem Fenster angezeigt wird, sondern Sie über das Hinzufügen eines neuen Fensters benachrichtigt).

## <a name="chapter-12---deploying-your-application"></a>Kapitel 12: Bereitstellen der Anwendung

So stellen Sie die Anwendung bereit:

1.  Navigieren Sie zum *App* -Ordner, der im [letzten Kapitel](#chapter-11---build-the-uwp-solution)erstellt wurde. Es wird eine Datei mit dem Namen Ihrer Apps mit der Erweiterung ". sln" angezeigt, auf die Sie doppelklicken, um Sie in *Visual Studio*zu öffnen.

2.  Wählen Sieauf der Projektmappenplattform die Option **x86, lokaler Computer**aus.

3.  Wählen Sie in der Projektmappenkonfiguration **Debuggen**.

    > Für Microsoft hololens ist es möglicherweise einfacher, dies auf den *Remote*Computer festzulegen, damit Sie nicht auf Ihren Computer über das Team verfügen. Allerdings müssen Sie auch die folgenden Schritte ausführen:
    > - Informieren Sie sich über die **IP-Adresse** ihrer hololens. diese befindet sich in den **Einstellungen** > **Network &**  > Advanced**Wi-Fi** > **Advanced Options**. IPv4 ist die Adresse, die Sie verwenden sollten. 
    > - Stellen Sie sicher, dass der **Entwicklermodus** **auf**dem finden Sie unter **Einstellungen** > **Aktualisieren & Sicherheit** > **für Entwickler**.

    ![Lösung bereitstellen](images/AzureLabs-Lab5-55.png)

4.  Wechseln Sie zum Menü **Erstellen** , und klicken Sie auf **Lösung** bereitstellen, um die Anwendung auf Ihren Computer zu übertragen.

5.  Ihre APP sollte nun in der Liste der installierten apps angezeigt werden, die gestartet und getestet werden können.

## <a name="your-finished-azure-functions-and-storage-application"></a>Ihre fertiggestellte Azure Functions-und Speicher Anwendung

Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die sowohl die Azure Functions als auch die Azure Storage Dienste nutzt. Ihre APP kann auf gespeicherten Daten zeichnen und eine auf diesen Daten basierende Aktion bereitstellen.

![Endprodukt-Ende](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a>Bonus Übungen

### <a name="exercise-1"></a>Übung 1

Erstellen Sie einen zweiten Erstellungs Punkt, und notieren Sie den-Punkt, aus dem ein Objekt erstellt wurde. Wenn Sie die Datendatei laden, stellen Sie die Formen wieder her, die aus dem Speicherort der ursprünglichen Erstellung erstellt werden.

### <a name="exercise-2"></a>Übung 2

Erstellen Sie eine Möglichkeit, die APP neu zu starten, anstatt Sie jedes Mal erneut öffnen zu müssen. Das **Laden von Szenen** ist ein guter Ausgangspunkt. Erstellen Sie anschließend eine Möglichkeit, die gespeicherte Liste in *Azure Storage*zu löschen, damit Sie problemlos von der APP zurückgesetzt werden kann. 
