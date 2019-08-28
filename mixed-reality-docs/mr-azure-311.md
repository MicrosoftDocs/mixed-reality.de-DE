---
title: Mr und Azure 311-Microsoft Graph
description: Machen Sie sich mit diesem Kurs vertraut, um zu erfahren, wie Sie Microsoft Graph nutzen und eine Verbindung mit den Daten herstellen, die die Produktivität innerhalb einer gemischten Reality-Anwendung steigern
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Microsoft Graph, hololens, immersive, VR
ms.openlocfilehash: 775971c4e4289d2dc963dfa2bf033192d9f3489e
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047205"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.

# <a name="mr-and-azure-311---microsoft-graph"></a>Mr und Azure 311-Microsoft Graph

In diesem Kurs erfahren Sie, wie Sie *Microsoft Graph* verwenden können, um sich mit der sicheren Authentifizierung in einer gemischten Reality-Anwendung bei Ihrem Microsoft-Konto anzumelden. Anschließend rufen Sie geplante Besprechungen in der Anwendungs Schnittstelle ab und zeigen Sie an.

![](images/AzureLabs-Lab311-00.png)

*Microsoft Graph* ist ein Satz von APIs, die für den Zugriff auf viele der Dienste von Microsoft entwickelt wurden. Microsoft beschreibt Microsoft Graph als Matrix von Ressourcen, die über Beziehungen verbunden sind, was bedeutet, dass eine Anwendung auf alle möglichen verbundenen Benutzerdaten zugreifen kann. Weitere Informationen finden Sie auf der [Seite Microsoft Graph](https://developer.microsoft.com/graph).

Die Entwicklung umfasst das Erstellen einer APP, in der der Benutzer aufgefordert wird, sich anzusehen und dann auf eine Kugel zu tippen, die den Benutzer auffordert, sich sicher bei einem Microsoft-Konto anzumelden. Nachdem Sie sich bei Ihrem Konto angemeldet haben, wird der Benutzer in der Lage sein, eine Liste der Besprechungen für den Tag anzuzeigen.

Nachdem Sie diesen Kurs abgeschlossen haben, verfügen Sie über eine Mixed Reality hololens-Anwendung, die Folgendes ausführen kann:

1.  Tippen Sie mithilfe der TAP-Geste auf ein Objekt, das den Benutzer auffordert, sich bei einem Microsoft-Konto anzumelden (durchlaufen der APP, um sich anzumelden, und dann wieder zurück in die APP).
2.  Zeigt eine Liste der Besprechungen an, die für den Tag geplant sind. 

In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren. In diesem Kurs erfahren Sie, wie Sie einen Azure-Dienst in Ihr Unity-Projekt integrieren. Es ist Ihre Aufgabe, das wissen, das Sie aus diesem Kursgewinnen, zu nutzen, um ihre gemischte Reality-Anwendung zu verbessern.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> Mr und Azure 311: Microsoft Graph</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>Erforderliche Komponenten

> [!NOTE]
> Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen. Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Juli 2018). Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](install-the-tools.md) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt werden.

Für diesen Kurs empfehlen wir die folgende Hardware und Software:

- Einen Entwicklungs-PC
- [Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus](install-the-tools.md#installation-checklist)
- [Das neueste Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Ein [Microsoft hololens](hololens-hardware-details.md) mit aktiviertem Entwicklermodus
- Internet Zugriff für Azure-Setup und Microsoft Graph Datenabruf
- Ein gültiges **Microsoft-Konto** (entweder persönlich oder Geschäfts-, Schul-oder unikonto)
- Einige Besprechungen, die für den aktuellen Tag geplant sind, mit demselben Microsoft-Konto

### <a name="before-you-start"></a>Bevor Sie beginnen

1.  Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).
2.  Richten Sie Ihre hololens ein, und testen Sie Sie. Wenn Sie Unterstützung für die Einrichtung ihrer hololens benötigen, [besuchen Sie den Artikel zum Einrichten von hololens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Es empfiehlt sich, eine Kalibrierung und Sensor Optimierung durchzuführen, wenn Sie mit der Entwicklung einer neuen hololens-App beginnen (manchmal kann es hilfreich sein, diese Aufgaben für jeden Benutzer auszuführen). 

Hilfe zur Kalibrierung finden Sie unter diesem [Link zum Artikel zur hololens-Kalibrierung](calibration.md#hololens-2).

Hilfe zur Sensor Optimierung finden Sie unter diesem [Link zum Artikel zur Überwachung von hololens-Sensoren](sensor-tuning.md).

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a>Kapitel 1: Erstellen der APP im Anwendungs Registrierungs Portal

Zunächst müssen Sie Ihre Anwendung im **Anwendungs Registrierungs Portal**erstellen und registrieren.

In diesem Kapitel finden Sie auch den Dienst Schlüssel, mit dem Sie Aufrufe an *Microsoft Graph* durchführen können, um auf Ihre Konto Inhalte zuzugreifen.

1.  Navigieren Sie zum [Microsoft-Anwendungs Registrierungs Portal](https://apps.dev.microsoft.com) , und melden Sie sich mit Ihrem Microsoft-Konto an. Nachdem Sie sich angemeldet haben, werden Sie zum **Anwendungs Registrierungs Portal**umgeleitet.

2.  Klicken Sie im Abschnitt **eigene Anwendungen** auf die Schaltfläche **app hinzufügen**.

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > Das **Anwendungs Registrierungs Portal** kann anders aussehen, je nachdem, ob Sie bereits mit *Microsoft Graph*gearbeitet haben. Die folgenden Screenshots zeigen diese verschiedenen Versionen an.

3.  Fügen Sie einen Namen für Ihre Anwendung hinzu, und klicken Sie auf **Erstellen**.

    ![](images/AzureLabs-Lab311-03.png)

4.  Nachdem die Anwendung erstellt wurde, werden Sie zur Hauptseite der Anwendung umgeleitet. Kopieren Sie die **Anwendungs-ID** , und stellen Sie sicher, dass Sie diesen Wert auf sichere Weise merken. Sie verwenden ihn bald in Ihrem Code.

    ![](images/AzureLabs-Lab311-04.png)

5.  Vergewissern Sie sich im Abschnitt **Plattformen** , dass **native Anwendung** angezeigt wird. Wenn Sie *nicht* auf **Plattform hinzufügen** klicken, wählen Sie **native Anwendung**aus.

    ![](images/AzureLabs-Lab311-05.png)

6.  Scrollen Sie auf der gleichen Seite nach unten, und im Abschnitt **Microsoft Graph Berechtigungen** müssen Sie zusätzliche Berechtigungen für die Anwendung hinzufügen. Klicken Sie neben **Delegierte Berechtigungen**auf **Hinzufügen** .

    ![](images/AzureLabs-Lab311-06.png)

7.  Da Sie möchten, dass Ihre Anwendung auf den Kalender des Benutzers zugreift, aktivieren Sie das Kontrollkästchen Calendar **. Read** , und klicken Sie auf **OK**.

    ![](images/AzureLabs-Lab311-07.png)

8.  Scrollen Sie nach unten, und klicken Sie auf die Schaltfläche **Speichern** .

    ![](images/AzureLabs-Lab311-08.png)

9.  Ihre Speicherung wird bestätigt, und Sie können sich vom **Anwendungs Registrierungs Portal**abmelden.

## <a name="chapter-2---set-up-the-unity-project"></a>Kapitel 2: Einrichten des Unity-Projekts

Folgendes ist eine typische Einrichtung für die Entwicklung mit gemischter Realität und ist daher eine gute Vorlage für andere Projekte.

1.  Öffnen Sie *Unity* , und klicken Sie auf **neu**.

    ![](images/AzureLabs-Lab311-09.png)

2.  Sie müssen einen Unity-Projektnamen angeben. Fügen Sie **msgraphmr**ein. Stellen Sie sicher, dass die Projektvorlage auf **3D**festgelegt ist. Legen Sie den Speicherort auf einen geeigneten **Speicherort** fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind). Klicken Sie dann auf **Projekt erstellen**.

    ![](images/AzureLabs-Lab311-10.png)

3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist. Wechseln Sie zu**Einstellungen** **Bearbeiten** > , und navigieren Sie dann im neuen Fenster zu **externe Tools**. Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**. Schließen Sie das Fenster " **Einstellungen** ".

    ![](images/AzureLabs-Lab311-11.png)

4.  Wechseln Sie zu > dateibuildeinstellungen, und wählen Sie **universelle Windows-Plattform**aus, und klicken Sie dann auf die Schaltfläche **Plattform wechseln** , um die Auswahl

    ![](images/AzureLabs-Lab311-12.png)

5.  Stellen Sie sicher, dass in den Einstellungen für die **Datei** > **Erstellung**Folgendes angezeigt wird:

    1. **Zielgerät** ist auf **hololens** festgelegt
    2. Der Buildtyp ist auf **D3D** festgelegt.
    3. **SDK** ist auf **neueste installierte** Version festgelegt.
    4. **Visual Studio-Version** ist auf **neueste installierte** Version festgelegt.
    5. **Build und Run** sind auf **lokaler Computer** festgelegt.
    6. Speichern Sie die Szene, und fügen Sie Sie dem Build hinzu.

        1. Wählen Sie hierzu die Option **geöffnete Szenen hinzufügen**aus. Ein Fenster zum Speichern wird angezeigt.

            ![](images/AzureLabs-Lab311-13.png)

        2. Erstellen Sie einen neuen Ordner für dieses und jede zukünftige Szene. Wählen Sie die Schaltfläche **neuer Ordner** aus, um einen neuen Ordner zu erstellen, und nennen Sie ihn **Szenen**.

            ![](images/AzureLabs-Lab311-14.png)

        3. Öffnen Sie den neu erstellten Ordner **Szenen** , geben Sie im Feld *Dateiname*: Text **MR_ComputerVisionScene**ein, und klicken Sie dann auf **Speichern**.

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > Beachten Sie, dass Sie Ihre Unity-Szenen im Ordner " *Assets* " speichern müssen, da Sie dem Unity-Projekt zugeordnet werden müssen. Das Erstellen eines Szenen Ordners (und anderer ähnlicher Ordner) ist eine typische Methode zum Strukturieren eines Unity-Projekts.

    7.  Die restlichen Einstellungen in denBuildeinstellungen sollten vorerst als Standard belassen werden.

6.  Klicken Sie im Fenster Buildeinstellungen auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der *Inspektor* befindet. 

    ![](images/AzureLabs-Lab311-16.png)

7. In diesem Bereich müssen einige Einstellungen überprüft werden:

    1. Auf der Registerkarte **andere Einstellungen** :

        1.  **Skript** Erstellung Die **Lauf Zeit Version** sollte **experimentell** sein (.NET 4,6-Entsprechung), wodurch der Editor neu gestartet werden muss.

        2. **Skript** -Back-End sollte **.net** sein

        3. **API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten

            ![](images/AzureLabs-Lab311-17.png)

    2.  Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:

        - **Internet Client deklarieren**

            ![](images/AzureLabs-Lab311-18.png)

    3.  Überprüfen Sie weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), ob **Virtual Reality unterstützt**wird, und vergewissern Sie sich, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.

        ![](images/AzureLabs-Lab311-19.png)

8.  Wieder inden Buildeinstellungen ist *Unity C# -Projekte* nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen neben diesem Kontrollkästchen.

9.  Schließen Sie das Fenster mit den Buildeinstellungen.

10.  Speichern Sie Ihre Szene und Ihr Projekt(**Datei** > **Speichern/**  > Speichern von Dateien).

## <a name="chapter-3---import-libraries-in-unity"></a>Kapitel 3: Importieren von Bibliotheken in Unity

> [!IMPORTANT]
> Wenn Sie die *Unity-Setup* Komponente dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie dieses [Azure-Mr-311. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage)herunterladen, es als [**benutzerdefiniertes Paket**](https://docs.unity3d.com/Manual/AssetPackages.html)in Ihr Projekt importieren und dann aus [Kapitel 5 fortfahren. ](#chapter-5---create-meetingsui-class).

Um *Microsoft Graph* in Unity verwenden zu können, müssen Sie die **Microsoft. Identity. Client** -dll verwenden. Es ist möglich, das Microsoft Graph SDK zu verwenden. Allerdings ist es erforderlich, dass ein nuget-Paket hinzugefügt wird, nachdem Sie das Unity-Projekt erstellt haben (d.h. das Bearbeiten des Projekts nach dem Build). Es ist einfacher, die erforderlichen DLLs direkt in Unity zu importieren.

> [!NOTE]
> Zurzeit gibt es ein bekanntes Problem in Unity, das erfordert, dass Plug-ins nach dem Importieren neu konfiguriert werden. Diese Schritte (4-7 in diesem Abschnitt) werden nicht mehr benötigt, nachdem der Fehler behoben wurde.

Wenn Sie *Microsoft Graph* in Ihr eigenes Projekt importieren möchten, [Laden Sie die Datei MSGraph_LabPlugins. zip herunter](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage). Dieses Paket wurde mit Versionen der Bibliotheken erstellt, die getestet wurden.

Wenn Sie mehr darüber erfahren möchten, wie Sie Ihrem Unity-Projekt benutzerdefinierte DLLs hinzufügen, [folgen Sie diesem Link](https://docs.unity3d.com/Manual/UsingDLL.html).

So importieren Sie das Paket:

1.  Fügen Sie das Unity-Paket Unity mithilfe der Menüoption **Assets** > **Import Package** > **Custom Package (benutzerdefiniertes Paket** importieren). Wählen Sie das soeben heruntergeladene Paket aus.

2.  Vergewissern Sie sich, dass im Feld **Unity-Paket importieren** , das angezeigt wird, alles unter (und einschließlich) Plug-ins ausgewählt ist.

    ![](images/AzureLabs-Lab311-20.png)

3.  Klicken Sie auf die Schaltfläche **importieren** , um dem Projekt die Elemente hinzuzufügen.

4.  Wechseln Sie im *Projekt Panel* unter Plug -in zum Ordner **MSGraph** , und wählen Sie das Plug-in mit dem Namen **Microsoft. Identity. Client**aus.

    ![](images/AzureLabs-Lab311-21.png)

5.  Wenn das *Plug* -in aktiviert ist, stellen Sie sicher, dass **alle Plattformen** deaktiviert sind, und stellen Sie sicher,dass **wsaplayer** ebenfalls deaktiviert ist. Dies dient nur zur Bestätigung, dass die Dateien ordnungsgemäß konfiguriert sind.

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > Wenn Sie diese Plug-ins markieren, werden Sie nur im Unity-Editor verwendet. Es gibt einen anderen Satz von DLLs im WSA-Ordner, der verwendet wird, nachdem das Projekt aus Unity als universelle Windows-Anwendung exportiert wurde.

6.  Im nächsten Schritt müssen Sie den Ordner " **WSA** " im Ordner " **MSGraph** " öffnen. Es wird eine Kopie derselben Datei angezeigt, die Sie soeben konfiguriert haben. Wählen Sie die Datei aus, und wählen Sie dann im Inspektor Folgendes aus:

    -   Stellen Sie sicher, dass **alle Plattformen** deaktiviert sind und **nur** **wsaplayer** **überprüft**wird.

    -   Stellen Sie sicher, dass **SDK** auf **UWP**und **Skript** -Back-End auf **dotnet** festgelegt ist.

    -   Stellen Sie sicher, dass **nicht verarbeiten** **aktiviert**ist.

        ![](images/AzureLabs-Lab311-23.png)

7.  Klicken Sie auf **Übernehmen**.

## <a name="chapter-4---camera-setup"></a>Kapitel 4: Kamera Einrichtung

In diesem Kapitel richten Sie die Hauptkamera Ihrer Szene ein:

1.  Wählen Sie im Bereich *Hierarchie*die **Hauptkamera**aus.

2.  Nachdem Sie diese Option ausgewählt haben, können Sie alle Komponenten der **Hauptkamera** im *Inspektor* -Panel sehen.

    1.  Das **Kamera Objekt** muss als **Hauptkamera** benannt werden (Beachten Sie die Schreibweise).

    2.  Das Hauptkamera **Kennzeichen** muss auf **maincamera** festgelegt sein (Beachten Sie die Schreibweise).

    3.  Stellen Sie sicher, dass die **Transformations Position** auf **0, 0, 0** festgelegt ist.

    4.  **Klartext** auf voll Tonfarbe festlegen

    5.  Legen Sie die **Hintergrundfarbe** der Kamera Komponente auf **schwarz, Alpha 0** (hexadezimal **Code: #00000000)** fest.

        ![](images/AzureLabs-Lab311-24.png)

3.  Die endgültige Objektstruktur im *Hierarchie Panel* sollte wie die in der folgenden Abbildung gezeigt aussehen:

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a>Kapitel 5: Erstellen der meetingsui-Klasse

Das erste Skript, das Sie erstellen müssen, ist " **meetingsui**", das für das Hosting und Auffüllen der Benutzeroberfläche der Anwendung zuständig ist (Begrüßungs Meldung, Anweisungen und Besprechungs Details).

So erstellen Sie diese Klasse:

1.  Klicken Sie im *Projekt Panel*mit der rechten Maustaste auf den Ordner **Objekte** , und wählen Sie dann**Ordner** **Erstellen** > aus. Benennen Sie den Ordner mit **Skripts**.

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  Öffnen Sie den Ordner Skripts, und klicken Sie dann in diesem Ordner mit der rechten Maustaste auf **C# Skript** **Erstellen**  >  . Benennen Sie das Skript mit " **meetingsui".**

    ![](images/AzureLabs-Lab311-28.png)

3.  Doppelklicken Sie auf das neue Skript " **meetingsui** ", um es in *Visual Studio*zu öffnen.

4.  Fügen Sie die folgenden Namespaces ein:

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  Fügen Sie in der-Klasse die folgenden Variablen ein:

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  Ersetzen Sie anschließend die Methode " **Start ()** ", und fügen Sie eine **Awa()** -Methode hinzu. Diese werden aufgerufen, wenn die-Klasse initialisiert:

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  Fügen Sie die Methoden hinzu, die für das Erstellen der *Besprechungen der Besprechungen* verantwortlich sind, und füllen Sie Sie mit den aktuellen Besprechungen

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. **Löschen** Sie die **Update ()** -Methode, und **Speichern Sie die Änderungen** in Visual Studio, bevor Sie zu Unity zurückkehren. 

## <a name="chapter-6---create-the-graph-class"></a>Kapitel 6: Erstellen der Graph-Klasse

Das nächste Skript, das erstellt werden soll, ist das **Graph** -Skript. Dieses Skript ist dafür verantwortlich, dass die Aufrufe zum Authentifizieren des Benutzers und zum Abrufen der geplanten Besprechungen für den aktuellen Tag aus dem Kalender des Benutzers durchführen.

So erstellen Sie diese Klasse:

1.  Doppelklicken Sie auf den Ordner **Skripts** , um ihn zu öffnen.

2.  Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf **C# Skript** **Erstellen**  >  . Benennen Sie das Skript **Diagramm**.

3.  Doppelklicken Sie auf das Skript, um es in Visual Studio zu öffnen.

4.  Fügen Sie die folgenden Namespaces ein:

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > Sie werden feststellen, dass Teile des Codes in diesem Skript mit [vorkompilierungs Direktiven](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html)umschlossen werden, um Probleme mit den Bibliotheken beim Erstellen der Visual Studio-Projekt Mappe zu vermeiden.

5.  Löschen Sie die Methoden " **Start ()** " und " **Update ()** ", da Sie nicht verwendet werden.

6.  Fügen Sie außerhalb der **Graph** -Klasse die folgenden Objekte ein, die zum Deserialisieren des JSON-Objekts erforderlich sind, das die täglichen geplanten Besprechungen darstellt:

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  Fügen Sie innerhalb der **Graph** -Klasse die folgenden Variablen hinzu:

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > Ändern Sie den **AppID** -Wert in die **App-ID** , die Sie in  **[Kapitel 1](#chapter-1---create-your-app-in-the-application-registration-portal), Schritt 4**notiert haben. Dieser Wert sollte mit dem übereinstimmen, der im **Anwendungs Registrierungs Portal** auf der Seite für die Anwendungs Registrierung angezeigt wird.

8.  Fügen Sie innerhalb der **Graph** -Klasse die Methoden **signinasync ()** und **aquiretokenasync ()** hinzu, die den Benutzer auffordern, die Anmelde Informationen einzufügen.

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successfull, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  Fügen Sie die folgenden beiden Methoden hinzu:

    1.  **Buildtodaycalendarendpoint ()** : erstellt den URI, der den Tag und die Zeitspanne angibt, in der die geplanten Besprechungen abgerufen werden.

    2.  **Listmeetingsasync ()** , die geplante Besprechungen von *Microsoft Graph*anfordert.

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. Sie haben nun das **Graph** -Skript abgeschlossen. **Speichern Sie die Änderungen** in Visual Studio, bevor Sie zu Unity zurückkehren.

## <a name="chapter-7---create-the-gazeinput-script"></a>Kapitel 7: Erstellen des gazeinput-Skripts

Nun erstellen Sie das " **gazeinput**". Diese Klasse verarbeitet und verfolgt den Blick des Benutzers, indem er einen **raycast** von der **Hauptkamera**verwendet und vorwärts projiziert.

So erstellen Sie das Skript:

1.  Doppelklicken Sie auf den Ordner **Skripts** , um ihn zu öffnen.

2.  Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf **C# Skript** **Erstellen**  >  . Nennen Sie das Skript " **gazeinput**".

3.  Doppelklicken Sie auf das Skript, um es in Visual Studio zu öffnen.

4.  Ändern Sie den Namespaces-Code so, dass er mit dem folgenden übereinstimmt, und fügen Sie das " **\[System.\]serialisierbare**"-Tag oberhalb Ihrer " **gazeinput** "-Klasse hinzu, damit es serialisiert werden kann:

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  Fügen Sie in der Klasse " **gazeinput** " die folgenden Variablen hinzu:

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  Fügen Sie die Methode " **kreatecursor ()** " hinzu, um den hololens-Cursor in der Szene zu erstellen, und rufen Sie die Methode über die Methode " **Start ()** " auf:

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  Die folgenden Methoden aktivieren den Gaze-raycast und verfolgen die Objekte mit Fokus.

    ```csharp
    /// <summary>
    /// Called every frame
    /// </summary>
    internal virtual void Update()
    {
        _gazeOrigin = Camera.main.transform.position;

        _gazeDirection = Camera.main.transform.forward;

        UpdateRaycast();
    }
    /// <summary>
    /// Reset the old focused object, stop the gaze timer, and send data if it
    /// is greater than one.
    /// </summary>
    private void ResetFocusedObject()
    {
        // Ensure the old focused object is not null.
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
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

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  **Speichern Sie die Änderungen** in Visual Studio, bevor Sie zu Unity zurückkehren.

## <a name="chapter-8---create-the-interactions-class"></a>Kapitel 8: Erstellen der Klasse "Interaktionen"

Sie müssen nun das **Interaktionen** -Skript erstellen, das für Folgendes zuständig ist:

-   Verarbeiten der **Tap** -Interaktion und des **Kamera Blicks**, mit dem der Benutzer mit der Anmelde Schaltfläche in der Szene interagieren kann.

-   Erstellen des Objekts "Schaltfläche" für die Anmeldung in der Szene, mit der der Benutzer interagieren soll.

So erstellen Sie das Skript:

1.  Doppelklicken Sie auf den Ordner **Skripts** , um ihn zu öffnen.

2.  Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf **C# Skript** **Erstellen**  >  . Benennen Sie das Skript mit **Interaktionen**.

3.  Doppelklicken Sie auf das Skript, um es in Visual Studio zu öffnen.

4.  Fügen Sie die folgenden Namespaces ein:

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  Ändern Sie die Vererbung der **Interaktions** Klasse von *monobehaviour* in **gazeinput**.

    ~~Interaktionen der öffentlichen Klasse: MonoBehaviour~~

    ```csharp
    public class Interactions : GazeInput
    ```

6.  Fügen Sie die folgende Variable in die **Interaktions** Klasse ein:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  Ersetzen Sie die **Start** -Methode. Beachten Sie, dass es sich um eine Überschreibungs Methode handelt, die die "Base"-Klasse "" als " " **Start ()** " wird aufgerufen, wenn die Klasse initialisiert, sich für die Eingabe Erkennung registriert und die Anmelde Schaltfläche in der Szene erstellt:

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  Fügen Sie die Methode " **kreatesigninbutton ()** " hinzu, mit der die Anmelde Schaltfläche in der Szene instanziiert wird, und legen Sie die zugehörigen Eigenschaften fest:

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  Fügen Sie die **GestureRecognizer_Tapped ()** -Methode hinzu, die für das *Tap* User-Ereignis antwortet.

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. **Löschen** Sie die **Update ()** -Methode, und **Speichern Sie Ihre Änderungen** in Visual Studio, bevor Sie zu Unity zurückkehren.

## <a name="chapter-9---set-up-the-script-references"></a>Kapitel 9: Einrichten der Skript Verweise

In diesem Kapitel müssen Sie das **Interaktionen** -Skript auf der **Hauptkamera**platzieren. Dieses Skript behandelt dann das Platzieren der anderen Skripts, wenn Sie es benötigen.

-  Ziehen Sie die Skript **Interaktionen** aus dem Ordner "Skripts" im *Projekt Panel*wie unten dargestellt auf das **Hauptkamera** Objekt.

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a>Kapitel 10: Einrichten des Tags

Der Code, der den Blick verarbeitet, verwendet das Tag **signinbutton** , um zu ermitteln, mit welchem Objekt der Benutzer interagieren soll, um sich bei *Microsoft Graph*anzumelden.

So erstellen Sie das Tag:

1.  Klicken Sie im Unity-Editor auf die **Hauptkamera** im *Hierarchie Panel*.

2.  Klicken Sie im Bereich *Inspector* auf das **maincamera** - *Tag* , um eine Dropdown Liste zu öffnen. Klicken Sie auf **Tag hinzufügen...**

    ![](images/AzureLabs-Lab311-30.png)

3.  Klicken Sie auf **+** die Schaltfläche.

    ![](images/AzureLabs-Lab311-31.png)

4.  Schreiben Sie den Tagnamen als **signinbutton** , und klicken Sie auf speichern.

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a>Kapitel 11: Erstellen des Unity-Projekts in UWP

Alles, was für den Unity-Abschnitt dieses Projekts erforderlich ist, ist nun abgeschlossen, sodass es an der Zeit ist, Sie aus Unity zu erstellen.

1.  Navigieren Sie zu *Buildeinstellungen* (**Datei*>*Erstellen von Einstellungen**).

    ![](images/AzureLabs-Lab311-33.png)

2.  Wenn dies nicht bereits geschehen ist, Tick Sie **\# Unity C-Projekte**.

3.  Klicken Sie auf **Erstellen**. Unity startet ein **Datei-Explorer** -Fenster, in dem Sie einen Ordner erstellen und auswählen müssen, in dem die App erstellt wird. Erstellen Sie diesen Ordner jetzt, und nennen Sie ihn " **App**". Klicken Sie dann mit ausgewähltem **App** -Ordner auf **Ordner auswählen**.

4.  Unity startet das Projekt in den **App** -Ordner.

5.  Nachdem die Erstellung von Unity abgeschlossen ist (Dies kann einige Zeit in Anspruch nehmen), wird ein **Datei-Explorer** -Fenster am Speicherort des Builds geöffnet (überprüfen Sie die Taskleiste, da Sie möglicherweise nicht immer über Ihrem Fenster angezeigt wird, sondern Sie über das Hinzufügen eines neuen Fensters benachrichtigt).

## <a name="chapter-12---deploy-to-hololens"></a>Kapitel 12: Bereitstellen in hololens

So stellen Sie auf hololens bereit:

1.  Sie benötigen die IP-Adresse Ihrer hololens (für die Remote Bereitstellung) und, um sicherzustellen, dass sich Ihre hololens im **Entwicklermodus befinden.** Gehen Sie dazu wie folgt vor:

    1.  Öffnen Sie die Einstellungen, während Sie die hololens- **Einstellungen**durch tragen.

    2.  Navigieren Sie zu **Netzwerk &**  > erweiterte**Wi-Fi** > -**Optionen** für das Internet.

    3.  Notieren Sie sich die **IPv4** -Adresse.

    4.  Navigieren Sie als nächstes wieder zu **Einstellungen**, und aktualisieren Sie die **& Sicherheit** > **für Entwickler** .

    5.  Legen Sie **den Entwicklermodus auf**fest.

2.  Navigieren Sie zu Ihrem neuen Unity-Build ( **App** -Ordner), und öffnen Sie die Projektmappendatei mit **Visual Studio**.

3.  Wählen Sie in der Projektmappenkonfiguration **Debuggen**.

4.  Wählen Sieauf der Projektmappenplattform die Option **x86, Remote Computer**aus. Sie werden aufgefordert, die **IP-Adresse** eines Remote Geräts (in diesem Fall die hololens) einzufügen, die Sie notiert haben.

    ![](images/AzureLabs-Lab311-34.png)

5.  Wechseln Sie zum Menü **Erstellen** , und klicken Sie auf **Lösung** bereitstellen, um die Anwendung auf die hololens quer zuladen.

6.  Ihre APP sollte nun in der Liste der installierten apps auf Ihren hololens angezeigt werden, die bereit sind, gestartet zu werden.

## <a name="your-microsoft-graph-hololens-application"></a>Ihre Microsoft Graph hololens-Anwendung

Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die die Microsoft Graph nutzt, um Benutzerkalender Daten zu lesen und anzuzeigen.

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a>Bonus Übungen

### <a name="exercise-1"></a>Übung 1

Verwenden Sie Microsoft Graph, um weitere Informationen zum Benutzer anzuzeigen.

-   Benutzer-e-Mail/Telefonnummer/Profilbild

### <a name="exercise-1"></a>Übung 1

Implementieren Sie das Voice-Steuerelement, um die Microsoft Graph-Benutzeroberfläche
