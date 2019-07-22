---
title: 'MR und Azure-311: Microsoft Graph'
description: Führen Sie diesen Kurs erfahren Sie, wie Microsoft Graph nutzen, und verbinden Sie die Daten, die Produktivität, innerhalb einer mixed Reality-Anwendung steuert.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorials, api, Microsoft Graph, Hololens, immersive vr
ms.openlocfilehash: 04c72a7ef7724cfcc27867f7f003c171a6f7851f
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694527"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

# <a name="mr-and-azure-311---microsoft-graph"></a>MR und Azure-311: Microsoft Graph

In diesem Kurs erfahren Sie, wie mit *Microsoft Graph* zur Anmeldung bei Ihrem Microsoft-Konto mithilfe der sicheren Authentifizierung innerhalb einer mixed Reality-Anwendung. Sie werden dann abrufen und Ihre geplanten Besprechungen in der Benutzeroberfläche der Anwendung.

![](images/AzureLabs-Lab311-00.png)

*Microsoft Graph* ist ein Satz von APIs, um Zugriff auf viele der Dienste von Microsoft. Microsoft beschreibt Microsoft Graph als einen Überblick über die Ressourcen, die über Beziehungen verbunden, was bedeutet, dass sie eine Anwendung auf alle Arten von verbundenen Benutzer zugreifen kann. Weitere Informationen finden Sie auf die [Seite der Microsoft Graph](https://developer.microsoft.com/graph).

Entwicklung umfasst die Erstellung einer App, in denen der Benutzer angewiesen wird, bestaunen an, und tippen Sie dann auf einer Kugel, die fordert den Benutzer sicher bei einem Microsoft-Konto anmelden. Wenn Sie auf ihr Konto angemeldet sind, wird der Benutzer können Sie eine Liste von Besprechungen geplant für den Tag sein.

Nach Abschluss dieses Kurses, verfügen Sie über ein mixed Reality HoloLens-Anwendung, die für die folgenden Aufgaben werden können

1.  Verwenden die tippbewegung, tippen Sie auf ein Objekt, das wird der Benutzer aufgefordert, melden Sie sich bei einem Microsoft Account (außerhalb der app zum Melden Sie sich, und klicken Sie dann wieder in die app verschieben).
2.  Anzeigen einer Liste von Besprechungen geplant für den Tag. 

In Ihrer Anwendung obliegt es Ihnen, wie Sie die Ergebnisse in Ihr Design integrieren werden. Dieser Kurs erfahren Sie, wie Sie ein Azure-Dienst in Ihrem Unity-Projekt zu integrieren. Es ist Ihre Aufgabe, verwenden Sie das wissen, dass Sie aus diesem Kurs zum Verbessern Ihrer mixed Reality-Anwendung erhalten.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> MR und Azure-311: Microsoft Graph</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>Vorraussetzungen

> [!NOTE]
> In diesem Tutorial wurde für Entwickler mit Erfahrung mit Unity entwickelt und C#. Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Juli 2018) überprüft wurde. Sie können zur Verwendung der neuesten Software, wie in der [Installieren der Tools](install-the-tools.md) Artikel, obwohl es nicht davon ausgegangen werden soll, dass die Informationen in diesem Kurs perfekt entspricht was finden Sie in der neueren Software als aufgeführt ist unten.

Es wird empfohlen, die folgende Hardware und Software für diesen Kurs:

- Eine Entwicklungs-PC
- [Windows 10 Fall Creators Update (oder höher) mit der Entwicklermodus aktiviert ist](install-the-tools.md#installation-checklist)
- [Das neueste Windows 10-SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Ein [Microsoft HoloLens](hololens-hardware-details.md) mit Entwicklermodus aktiviert ist
- Zugriff auf das Internet für die Einrichtung von Azure und Microsoft Graph-Datenabruf
- Ein gültiger **Microsoft Account** (persönliche oder Geschäfts-oder schulkonten)
- Einige-Besprechungen geplant für den aktuellen Tag, mit dem gleichen Microsoft-Account

### <a name="before-you-start"></a>Bevor Sie beginnen

1.  Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).
2.  Richten Sie ein und Testen Sie Ihre HoloLens. Bei Bedarf Unterstützung zum Einrichten Ihrer HoloLens, [stellen Sie sicher, dass die HoloLens-Setup-Artikel finden Sie unter](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Es ist eine gute Idee, die Kalibrierung und Optimierung der Sensor ausführen, wenn Sie beginnen, eine neue HoloLens-App (manchmal ist es hilfreich, diese Aufgaben für jeden Benutzer) entwickeln. 

Um Hilfe zur Kalibrierung, befolgen Sie diese [Link zum Artikel HoloLens Kalibrierung](calibration.md#hololens).

Um Hilfe zur Optimierung der Sensor, befolgen Sie diese [Link zum Optimieren von HoloLens Sensor](sensor-tuning.md).

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a>Kapitel 1: Erstellen Ihrer app in App-Registrierungsportal

Zunächst müssen Sie zum Erstellen und registrieren Ihre Anwendung in der **App-Registrierungsportal**.

In diesem Kapitel finden Sie außerdem den Dienstschlüssel, die Sie aufrufen können *Microsoft Graph* Zugriff auf Ihre Konto-Inhalte.

1.  Navigieren Sie zu der [Microsoft-Anwendungsregistrierungsportal](https://apps.dev.microsoft.com) und melden Sie sich mit Ihrem Microsoft Account. Nachdem Sie sich angemeldet haben, werden Sie umgeleitet die **App-Registrierungsportal**.

2.  In der **meiner Anwendungen** Abschnitt, klicken Sie auf die Schaltfläche mit den **fügen Sie eine app**.

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > Die **App-Registrierungsportal** sehen variieren, je nachdem, ob Sie zuvor mit gearbeitet haben *Microsoft Graph*. Die folgenden Screenshots dieser verschiedenen Versionen anzuzeigen.

3.  Fügen Sie einen Namen für Ihre Anwendung und klicken Sie auf **erstellen**.

    ![](images/AzureLabs-Lab311-03.png)

4.  Nachdem die Anwendung erstellt wurde, werden Sie auf der Hauptseite der Anwendung weitergeleitet werden. Kopieren der **Anwendungs-Id** und stellen Sie sicher, dass dieser Wert an einem sicheren Ort zu beachten, da Sie es in Kürze in Ihrem Code.

    ![](images/AzureLabs-Lab311-04.png)

5.  In der **Plattformen** Abschnitt, stellen Sie sicher, dass **systemeigene Anwendung** wird angezeigt. Wenn *nicht* klicken Sie auf **Plattform hinzufügen** , und wählen Sie **systemeigene Anwendung**.

    ![](images/AzureLabs-Lab311-05.png)

6.  Führen Sie einen Bildlauf nach unten aus, in der gleichen Seite und im Abschnitt **Microsoft Graph-Berechtigungen** Sie benötigen zusätzliche Berechtigungen für die Anwendung hinzuzufügen. Klicken Sie auf **hinzufügen** neben **delegierte Berechtigungen**.

    ![](images/AzureLabs-Lab311-06.png)

7.  Da Sie Ihre Anwendung auf den Kalender des Benutzers zugreifen möchten, aktivieren Sie das Kontrollkästchen, die Namen **Calendars.Read** , und klicken Sie auf **OK**.

    ![](images/AzureLabs-Lab311-07.png)

8.  Scrollen Sie nach unten, und klicken Sie auf die **speichern** Schaltfläche.

    ![](images/AzureLabs-Lab311-08.png)

9.  Ihre speichern bestätigt, und Sie können melden Sie sich vom die **App-Registrierungsportal**.

## <a name="chapter-2---set-up-the-unity-project"></a>Kapitel 2: Einrichten von Unity-Projekts

Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit mixed Reality und daher ist eine gute Vorlage für andere Projekte.

1.  Open *Unity* , und klicken Sie auf **neu**.

    ![](images/AzureLabs-Lab311-09.png)

2.  Sie müssen den Namen eines Unity-Projekts angeben. Fügen Sie **MSGraphMR**. Stellen Sie sicher, dass die Projektvorlage nastaven NA hodnotu **3D**. Legen Sie die **Speicherort** auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser). Klicken Sie auf **projekterstellung**.

    ![](images/AzureLabs-Lab311-10.png)

3.  Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**. Wechseln Sie zu **bearbeiten** > **Voreinstellungen** und navigieren Sie dann im neuen Fenster zu **externe Tools**. Änderung **externen Skript-Editors** zu **Visual Studio 2017**. Schließen der **Voreinstellungen** Fenster.

    ![](images/AzureLabs-Lab311-11.png)

4.  Wechseln Sie zu **Datei** > **Buildeinstellungen** , und wählen Sie **universelle Windows-Plattform**, klicken Sie dann auf die **Plattform wechseln** Schaltfläche, um Ihre Auswahl anzuwenden.

    ![](images/AzureLabs-Lab311-12.png)

5.  In der **Datei** > **Buildeinstellungen**, stellen Sie sicher, dass:

    1. **Geräte** nastaven NA hodnotu **HoloLens**
    2. **Buildtyp** nastaven NA hodnotu **D3D**
    3. **SDK** nastaven NA hodnotu **zuletzt installierte**
    4. **Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**
    5. **Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**
    6. Die Szene speichern und mit dem Build hinzugefügt werden.

        1. Hierzu **öffnen Szenen hinzufügen**. Ein Speichern Fenster wird angezeigt.

            ![](images/AzureLabs-Lab311-13.png)

        2. Erstellen Sie einen neuen Ordner für, und alle zukünftigen, Szene ein. Wählen Sie die **neuer Ordner** Schaltfläche zum Erstellen eines neuen Ordners, nennen Sie sie **Szenen**.

            ![](images/AzureLabs-Lab311-14.png)

        3. Öffnen Sie den neu erstellten **Szenen** Ordner, und klicken Sie dann in der *Dateiname*: Textfeld **MR_ComputerVisionScene**, klicken Sie dann auf **speichern** .

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > Beachten Sie, speichern Sie Ihre Unity-Szenen in den *Assets* Ordner, wie sie mit der Unity-Projekt verbunden sein müssen. Erstellen den Ordner im Hintergrund (und andere ähnliche Ordner), wird eine typische Möglichkeit Strukturieren eines Unity-Projekts ist.

    7.  Die Einstellungen im verbleibenden *Buildeinstellungen*, sollte jetzt als Standard bleiben.

6.  In der *Buildeinstellungen* Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dadurch wird den entsprechenden Bereich geöffnet, im Bereich, in dem die *Inspektor* befindet. 

    ![](images/AzureLabs-Lab311-16.png)

7. In diesem Bereich sind müssen einige Einstellungen überprüft werden:

    1. In der **Weitere Einstellungen** Registerkarte:

        1.  **Scripting** **Laufzeitversion** muss **experimentell** (.NET 4.6 entspricht), löst der Editor neu starten müssen.

        2. **Back-End-Scripting** muss **.NET**

        3. **API-Kompatibilitätsebene** muss **.NET 4.6**

            ![](images/AzureLabs-Lab311-17.png)

    2.  In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:

        - **InternetClient**

            ![](images/AzureLabs-Lab311-18.png)

    3.  Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), überprüfen Sie **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality SDK** hinzugefügt wird.

        ![](images/AzureLabs-Lab311-19.png)

8.  Im *Buildeinstellungen*, *Unity C# Projekte* nicht mehr abgeblendet ist, aktivieren Sie das Kontrollkästchen neben dieser.

9.  Schließen der *Buildeinstellungen* Fenster.

10.  Speichern Sie Ihre Szene und das Projekt (**Datei** > **SZENEN speichern / FILE** > **Projekt speichern**).

## <a name="chapter-3---import-libraries-in-unity"></a>Kapitel 3: Importieren von Bibliotheken in Unity

> [!IMPORTANT]
> Wenn Sie, überspringen Sie möchten die *Unity einrichten* -Komponente dieser Kurs, und direkt in Code fortsetzen, können Sie zum Herunterladen [Azure-MR-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), importieren Sie es in Ihr Projekt als eine [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), und klicken Sie dann eine Fortsetzung [Kapitel 5](#chapter-5---create-meetingsui-class).

Verwendung von *Microsoft Graph* in Unity, Sie müssen, verwenden die **Microsoft.Identity.Client** DLL. Es ist möglich, die Microsoft Graph SDK verwenden, allerdings muss das Hinzufügen von NuGet-Paket nach dem Erstellen des Unity-Projekts (d. h. die nach der Erstellung des Projekts bearbeiten). Es wird einfacher, importieren die benötigten DLLs direkt in Unity angesehen.

> [!NOTE]
> Es befindet sich derzeit ein bekanntes Problem in Unity-Plug-Ins neu konfiguriert werden, nach dem Import erfordert. Diese Schritte (4 bis 7 in diesem Abschnitt) ist nicht mehr erforderlich, nachdem der Fehler behoben wurde.

So importieren Sie *Microsoft Graph* in Ihrem eigenen Projekt [Laden Sie die Datei MSGraph_LabPlugins.zip](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage). Dieses Paket wurde mit den Versionen der Bibliotheken erstellt, die getestet wurden.

Wenn Sie weitere Informationen zum Hinzufügen von benutzerdefinierten DLLs zu Ihres Unity-Projekts möchten [folgen Sie diesem Link](https://docs.unity3d.com/Manual/UsingDLL.html).

Zum Importieren des Pakets:

1.  Hinzufügen des Unity-Pakets zu Unity mit der **Assets** > **Paket importieren** > **Custom Package** Menüoption. Wählen Sie das Paket, das Sie gerade heruntergeladen haben.

2.  In der **Unity-Paket importieren** , ruft Sie Vergewissern Sie sich, alles, was unter (und einschließlich) **-Plug-Ins** ausgewählt ist.

    ![](images/AzureLabs-Lab311-20.png)

3.  Klicken Sie auf die **Import** , um die Elemente zu Ihrem Projekt hinzuzufügen.

4.  Wechseln Sie zu der **MSGraph** Unterordner **-Plug-Ins** in die *Projektbereich* , und wählen Sie das Plug-in **Microsoft.Identity.Client**.

    ![](images/AzureLabs-Lab311-21.png)

5.  Mit der *-Plug-Ins* ausgewählt haben, stellen sicher, dass **Any Platform** deaktiviert ist, und klicken Sie dann sicher, dass **WSAPlayer** auch deaktiviert ist, und klicken Sie dann **übernehmen**. Dies ist, um sich zu vergewissern, dass die Dateien richtig konfiguriert sind.

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > Markieren diese-Plug-Ins konfiguriert sie nur im Unity-Editor verwendet werden. Es gibt ein anderen Satz von DLLs im Ordner "WSA" das verwendet werden soll, nachdem das Projekt aus Unity als universelle Windows-Anwendung exportiert werden.

6.  Als Nächstes müssen Sie zum Öffnen der **WSA** Ordner, der innerhalb der **MSGraph** Ordner. Daraufhin wird eine Kopie der gleichen Datei, die Sie gerade konfiguriert haben. Wählen Sie die Datei, und klicken Sie dann im Inspektor:

    -   sicherstellen, dass **Any Platform** ist **deaktiviert**, und dass **nur** **WSAPlayer** ist **überprüft**.

    -   Stellen Sie sicher **SDK** nastaven NA hodnotu **UWP**, und **Scripting Back-End-** nastaven NA hodnotu **Dot Net**

    -   Sicherstellen, dass **nicht verarbeiten** ist **überprüft**.

        ![](images/AzureLabs-Lab311-23.png)

7.  Klicken Sie auf **Übernehmen**.

## <a name="chapter-4---camera-setup"></a>Kapitel 4 – Kamerasetup

Während der in diesem Kapitel werden Sie der Main Kamera und Ihrer Szene einrichten:

1.  In der *Hierarchie Bereich*, wählen die **Main Camera**.

2.  Wenn ausgewählt, Sie werden auf alle Komponenten finden Sie unter den **Main Camera** in die *Inspektor* Bereich.

    1.  Die **Kameraobjekt** muss den Namen **Main Camera** (Beachten Sie die Rechtschreibung!)

    2.  Die Main Camera **Tag** muss festgelegt werden, um **MainCamera** (Beachten Sie die Rechtschreibung!)

    3.  Stellen Sie sicher, dass die **transformieren Position** nastaven NA hodnotu **0, 0, 0**

    4.  Legen Sie **Kennzeichnungen löschen** zu **Volltonfarbe**

    5.  Legen Sie die **Hintergrundfarbe** der Kamera-Komponente auf **Schwarz, Alpha 0** **(Hex-Code: #00000000)**

        ![](images/AzureLabs-Lab311-24.png)

3.  Die Struktur der endgültige Objekt in der *Hierarchie Bereich* sollte wie in der folgenden Abbildung dargestellt:

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a>Kapitel 5: Erstellen Sie MeetingsUI-Klasse

Ist das erste Skript, das Sie erstellen müssen **MeetingsUI**, die zum Hosten und Auffüllen der Benutzeroberfläche der Anwendung (Begrüßungsnachricht, Anweisungen und die Details der Besprechungen) verantwortlich ist.

Diese Klasse zu erstellen:

1.  Mit der rechten Maustaste auf die **Assets** Ordner in der *Projektfenster*, und wählen Sie dann **erstellen** > **Ordner**. Nennen Sie den Ordner **Skripts**.

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  Öffnen der **Skripts** Ordner klicken Sie dann in diesem Ordner mit der rechten Maustaste, **erstellen**  >   **C# Skript**. Nennen Sie das Skript **MeetingsUI.**

    ![](images/AzureLabs-Lab311-28.png)

3.  Doppelklicken Sie auf die neue **MeetingsUI** Skript öffnen Sie ihn mit *Visual Studio*.

4.  Fügen Sie die folgenden Namespaces ein:

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  Fügen Sie in der Klasse die folgenden Variablen:

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

6.  Ersetzen Sie dann die **Start()** Methode und Hinzufügen einer **Awake()** Methode. Diese werden aufgerufen, wenn die Klasse initialisiert:

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

7.  Fügen Sie die Methoden, die verantwortlich für das Erstellen der *Besprechungen UI* und füllen sie mit den aktuellen treffen, wenn angefordert:

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

8. **Löschen Sie** der **Update()** -Methode und **speichern Sie Ihre Änderungen** in Visual Studio vor der Rückgabe an Unity. 

## <a name="chapter-6---create-the-graph-class"></a>Kapitel 6: Erstellen Sie die Graph-Klasse

Ist das nächste Skript zum Erstellen der **Graph** Skript. Dieses Skript ist dafür verantwortlich, dass die Aufrufe an den Benutzer authentifizieren und Abrufen der geplanten Besprechungen für den aktuellen Tag aus den Kalender des Benutzers.

Diese Klasse zu erstellen:

1.  Doppelklicken Sie auf die **Skripts** Ordner, um ihn zu öffnen.

2.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen**  >   **C# Skript**. Nennen Sie das Skript **Graph**.

3.  Doppelklicken Sie auf das Skript aus, um ihn mit Visual Studio zu öffnen.

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
    > Sie werden feststellen, dass Teile des Codes in diesem Skript umbrochen werden [Vorkompilieren Direktiven](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), dies ist zur Vermeidung von Problemen mit den Bibliotheken, beim Erstellen der Projektmappe in Visual Studio.

5.  Löschen der **Start()** und **Update()** Methoden, wie sie nicht verwendet werden.

6.  Außerhalb der **Graph** Klasse, legen Sie die folgenden Objekte, die beim Deserialisieren des JSON-Objekts zurück, der täglichen geplanten Besprechungen darstellt erforderlich sind:

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

7.  In der **Graph** -Klasse verwenden, fügen Sie die folgenden Variablen:

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
    > Ändern der **AppId** Wert der **App-Id** , die Sie notiert haben, im  **[Kapitel 1](#chapter-1---create-your-app-in-the-application-registration-portal), Schritt 4**. Dieser Wert sollte identisch, die angezeigt wird, der **App-Registrierungsportal** in Ihre Seite für die anwendungsregistrierung.

8.  In der **Graph** Klasse, fügen Sie die Methoden **SignInAsync()** und **AquireTokenAsync()** , aufgefordert, die den Benutzer, die Anmeldeinformationen einzufügen.

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

9.  Fügen Sie die folgenden zwei Methoden:

    1.  **BuildTodayCalendarEndpoint()** , welche builds den URI angeben, den Tag und die Zeitspanne, in dem die geplanten Besprechungen werden abgerufen.

    2.  **ListMeetingsAsync()** , die Anforderungen aus geplanten Besprechungen *Microsoft Graph*.

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

10. Sie haben jetzt die **Graph** Skript. **Speichern Sie Ihre Änderungen** in Visual Studio vor der Rückgabe in Unity.

## <a name="chapter-7---create-the-gazeinput-script"></a>Kapitel 7: Erstellen Sie das Skript GazeInput

Erstellen Sie jetzt die **GazeInput**. Diese Klasse behandelt, und verfolgt des Benutzers Blicke, mit einem **Raycast** aus der **Main Camera**, projizieren weiterleiten.

So erstellen Sie das Skript:

1.  Doppelklicken Sie auf die **Skripts** Ordner, um ihn zu öffnen.

2.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen**  >   **C# Skript**. Nennen Sie das Skript **GazeInput**.

3.  Doppelklicken Sie auf das Skript aus, um ihn mit Visual Studio zu öffnen.

4.  Ändern Sie den Code Namespaces entsprechend folgendermaßen, sowie das Hinzufügen der " **\[System.Serializable\]** " Tag, die oben genannten Ihre **GazeInput** Klasse, sodass sie serialisiert werden kann:

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  In der **GazeInput** -Klasse verwenden, fügen Sie die folgenden Variablen:

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

6.  Hinzufügen der **CreateCursor()** Methode, um die HoloLens-Cursor in der Szene erstellt, und rufen die Methode aus der **Start()** Methode:

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

7.  Die folgenden Methoden ermöglichen die Blicke Raycast und Nachverfolgen der fokussierten Objekte.

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

8.  **Speichern Sie Ihre Änderungen** in Visual Studio vor der Rückgabe in Unity.

## <a name="chapter-8---create-the-interactions-class"></a>Kapitel 8 – erstellen Sie die Interaktionen-Klasse

Sie müssen nun zum Erstellen der **Interaktionen** Skripts, die dafür verantwortlich ist:

-   Behandeln der **Tippen Sie auf** Interaktion und die **Kamera bestaunen**, wodurch den Benutzer für die Interaktion mit der Anmeldung "Button" in der Szene.

-   Erstellen das Protokoll in "Button"-Objekt in der Szene für den Benutzer für die Interaktion mit ein.

So erstellen Sie das Skript:

1.  Doppelklicken Sie auf die **Skripts** Ordner, um ihn zu öffnen.

2.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen**  >   **C# Skript**. Nennen Sie das Skript **Interaktionen**.

3.  Doppelklicken Sie auf das Skript aus, um ihn mit Visual Studio zu öffnen.

4.  Fügen Sie die folgenden Namespaces ein:

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  Ändern Sie die Vererbung von der **Interaktion** -Klasse aus *"monobehaviour"* zu **GazeInput**.

    ~~öffentliche Klasse Interaktionen: MonoBehaviour~~

    ```csharp
    public class Interactions : GazeInput
    ```

6.  In der **Interaktion** Klasse einfügen der folgenden Variablen:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  Ersetzen Sie die **starten** Methode; Beachten Sie, dass es eine Überschreibungsmethode, der Methode der "base" Blicke-Klasse aufruft, ist. **Start()** wird aufgerufen, wenn die Klasse initialisiert die Registrierung für die Eingabe verwendet, und erstellen die Anmeldung, *Schaltfläche* in der Szene:

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

8.  Hinzufügen der **CreateSignInButton()** -Methode, die die Anmeldung instanziiert *Schaltfläche* in der Szene und seine Eigenschaften festlegen:

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

9.  Hinzufügen der **GestureRecognizer_Tapped()** -Methode, die werden für reagieren die *Tippen Sie auf* Benutzerereignis.

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

10. **Löschen Sie** der **Update()** -Methode, und klicken Sie dann **speichern Sie Ihre Änderungen** in Visual Studio vor der Rückgabe an Unity.

## <a name="chapter-9---set-up-the-script-references"></a>Kapitel 9: Einrichten der Skriptverweise

In diesem Kapitel es erforderlich, die **Interaktionen** Skript auf die **Main Camera**. Dieses Skript behandelt platzieren den anderen Skripts, in denen sie sein müssen.

-  Von der **Skripts** Ordner in der *Projektfenster*, ziehen Sie das Skript **Interaktionen** auf die **Main Camera** -Objekts, wie unten abgebildet.

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a>Kapitel 10 – das Tag einrichten

Der Code zum Verarbeiten der Blicke wird Nutzen des Tags **SignInButton** Objekt Identifizieren der Benutzer interagieren wird, um sich anzumelden *Microsoft Graph*.

So erstellen Sie das Tag:

1.  Klicken Sie im Unity-Editor auf die **Main Camera** in die *Hierarchie Bereich*.

2.  In der *Inspektor Bereich* klicken Sie auf die **MainCamera** *Tag* , das eine Dropdown-Liste zu öffnen. Klicken Sie auf **Tag hinzufügen...**

    ![](images/AzureLabs-Lab311-30.png)

3.  Klicken Sie auf die **+** Schaltfläche.

    ![](images/AzureLabs-Lab311-31.png)

4.  Schreiben Sie den Namen des Tags als **SignInButton** , und klicken Sie auf Speichern.

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a>Kapitel 11: Erstellen Sie das Unity-Projekt auf UWP

Alles, was Sie für den Unity-Abschnitt, der dieses Projekt wurde jetzt abgeschlossen daher ist es Zeit für die Erstellung von Unity.

1.  Navigieren Sie zu *Buildeinstellungen* (**Datei* >* Erstellen von Einstellungen**).

    ![](images/AzureLabs-Lab311-33.png)

2.  Falls noch nicht geschehen, aktivieren Sie **Unity C\# Projekte**.

3.  Klicken Sie auf **Erstellen**. Unity startet eine **Datei-Explorer** Fenster, in denen man erstellen, und wählen Sie einen Ordner zum Erstellen der app in. Erstellen Sie jetzt auf diesen Ordner, und nennen Sie es **App**. Klicken Sie dann mit der **App** Ordner ausgewählt haben, klicken Sie auf **Ordner auswählen**.

4.  Erstellen Ihres Projekts zu Unity beginnt die **App** Ordner.

5.  Einmal Unity wurde (es kann einige Zeit dauern) erstellen, öffnen ein **Datei-Explorer** Fenster am Speicherort des Builds (Überprüfen Sie Ihre Taskleiste aus, wie es unter Umständen nicht immer über Ihre Windows angezeigt und Sie über das Hinzufügen eines neuen benachrichtigt Fenster ").

## <a name="chapter-12---deploy-to-hololens"></a>Kapitel 12 – bereitstellen, um HoloLens

Für HoloLens bereitstellen:

1.  Sie benötigen die IP-Adresse Ihrer HoloLens (für Remote bereitstellen), und um sicherzustellen, dass Ihre HoloLens befindet sich in **Entwicklermodus.** Gehen Sie dazu wie folgt vor:

    1.  Während Ihre HoloLens steht, geteert, öffnen Sie die **Einstellungen**.

    2.  Wechseln Sie zu **Netzwerk und Internet** > **Wi-Fi** > **erweiterte Optionen**

    3.  Beachten Sie die **IPv4** Adresse.

    4.  Navigieren Sie als Nächstes zurück zum **Einstellungen**, und klicken Sie dann **Update und Sicherheit** > **für Entwickler**

    5.  Legen Sie **Entwicklermodus auf**.

2.  Navigieren Sie zu Ihrem neuen Unity-Build (die **App** Ordner), und öffnen Sie die Projektmappendatei mit **Visual Studio**.

3.  In der **Projektmappenkonfiguration** wählen **Debuggen**.

4.  In der **Projektmappenplattform**Option **X86, Remotecomputer**. Werden Sie aufgefordert, fügen Sie der **IP-Adresse** von einem Remotegerät (die HoloLens, in diesem Fall, den Sie notiert haben).

    ![](images/AzureLabs-Lab311-34.png)

5.  Wechseln Sie zu **erstellen** Menü, und klicken Sie auf **Projektmappe bereitstellen** zum querladen der Anwendung in Ihrem HoloLens.

6.  Ihre app sollte nun in der Liste der installierten apps auf Ihre HoloLens, möchten Sie die gestartet werden, angezeigt werden.

## <a name="your-microsoft-graph-hololens-application"></a>Die Microsoft Graph HoloLens-Anwendung

Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die Microsoft Graph zum Lesen und Anzeigen von Benutzer Kalenderdaten nutzt.

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a>Bonus-Übungen

### <a name="exercise-1"></a>Übung 1

Verwenden Sie Microsoft Graph, um weitere Informationen über den Benutzer anzuzeigen.

-   Benutzer-e- / Telefonnummer / profile-Bild

### <a name="exercise-1"></a>Übung 1

Implementieren Sie die Sprach-Steuerelement, um die Benutzeroberfläche von Microsoft Graph zu navigieren.
