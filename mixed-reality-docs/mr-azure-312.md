---
title: Mr-und Azure 312-bot-Integration
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie einen bot mit Microsoft bot Framework V4 erstellen und bereitstellen und in einer gemischten Reality-Anwendung mit ihm kommunizieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Maschinelles sehen, hololens, immersive, VR, Microsoft bot Framework V4, Web-App-bot, bot Framework, Microsoft bot
ms.openlocfilehash: dc428f01a8333bf812fe03c59a46b7a2fa20df83
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438483"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.

# <a name="mr-and-azure-312-bot-integration"></a>Mr und Azure 312: bot-Integration

In diesem Kurs erfahren Sie, wie Sie mithilfe von Microsoft bot Framework V4 einen Bot erstellen und bereitstellen und über eine Windows Mixed Reality-Anwendung mit ihm kommunizieren. 

![](images/AzureLabs-Lab312-00.png)

Das **Microsoft bot Framework V4** ist ein Satz von APIs, die Entwicklern die Tools zum Erstellen einer erweiterbaren und skalierbaren bot-Anwendung zur Verfügung stellen. Weitere Informationen finden Sie auf der [Microsoft bot Framework-Seite](https://dev.botframework.com/) oder im [V4-git-Repository](https://github.com/Microsoft/botbuilder-dotnet/wiki).

Nachdem Sie diesen Kurs abgeschlossen haben, haben Sie eine Windows Mixed Reality-Anwendung erstellt, die Folgendes ausführen kann:

1. Verwenden Sie eine **Tap-Geste** , um den bot zu starten, der die Benutzer Stimme abhört.
2. Wenn der Benutzer etwas gesagt hat, versucht der bot, eine Antwort bereitzustellen.
3. Zeigen Sie die Bots-Antwort als Text an, der in der Nähe des bot in der Unity-Szene positioniert ist.

In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren. In diesem Kurs erfahren Sie, wie Sie einen Azure-Dienst in Ihr Unity-Projekt integrieren. Es ist Ihre Aufgabe, das wissen, das Sie aus diesem Kursgewinnen, zu nutzen, um ihre gemischte Reality-Anwendung zu verbessern.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> Mr und Azure 312: bot-Integration</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Dieser Kurs konzentriert sich in erster Linie auf hololens, aber Sie können auch das Erlernen, was Sie in diesem Kurs lernen, auf Windows Mixed Reality-(VR)-Headsets. Da immersive Headsets (VR) nicht über barrierefreie Kameras verfügen, benötigen Sie eine externe Kamera, die mit Ihrem PC verbunden ist. Wenn Sie den Kurs befolgen, finden Sie Hinweise zu allen Änderungen, die Sie möglicherweise für die Unterstützung von immersiven (VR)-Headsets verwenden müssen.

## <a name="prerequisites"></a>Voraussetzungen

> [!NOTE]
> Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen. Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Juli 2018). Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](install-the-tools.md) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt werden.

Für diesen Kurs empfehlen wir die folgende Hardware und Software:

- Einen Entwicklungs-PC, der [mit der Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for Immersive (VR)-Headset-Entwicklung kompatibel ist
- [Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus](install-the-tools.md#installation-checklist)
- [Das neueste Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Ein [Windows Mixed Reality-Headset (VR)](immersive-headset-hardware-details.md) oder [Microsoft hololens](hololens-hardware-details.md) mit aktiviertem Entwicklermodus
- Internet Zugang für Azure und für den Azure-bot-Abruf. Weitere Informationen [finden Sie unter diesem Link](https://dev.botframework.com/).

### <a name="before-you-start"></a>Bevor Sie beginnen

1.  Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen).
2.  Richten Sie Ihre hololens ein, und testen Sie Sie. Wenn Sie Unterstützung für die Einrichtung ihrer hololens benötigen, [besuchen Sie den Artikel zum Einrichten von hololens](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Es empfiehlt sich, eine Kalibrierung und Sensor Optimierung durchzuführen, wenn Sie mit der Entwicklung einer neuen hololens-App beginnen (manchmal kann es hilfreich sein, diese Aufgaben für jeden Benutzer auszuführen). 

Hilfe zur Kalibrierung finden Sie unter diesem [Link zum Artikel zur hololens-Kalibrierung](calibration.md#hololens-2).

Hilfe zur Sensor Optimierung finden Sie unter diesem [Link zum Artikel zur Überwachung von hololens-Sensoren](sensor-tuning.md).

## <a name="chapter-1--create-the-bot-application"></a>Kapitel 1 – Erstellen der bot-Anwendung

Der erste Schritt besteht darin, den bot als lokale Webanwendung ASP.net Core zu erstellen. Nachdem Sie den Vorgang abgeschlossen und getestet haben, veröffentlichen Sie ihn im Azure-Portal.

1.  Öffnen Sie Visual Studio. Erstellen Sie ein neues Projekt, wählen Sie **ASP NET Core-Webanwendung** als Projekttyp aus (Sie finden Sie im unter Abschnitt .net Core) und nennen Sie **mybot**. Klicken Sie auf **OK**.

2.  Wählen Sie im angezeigten Fenster die Option **leer**aus. Stellen Sie außerdem sicher, dass das Ziel auf **ASP NET Core 2,0** festgelegt ist und die Authentifizierung auf **keine Authentifizierung**festgelegt ist. Klicken Sie auf **OK**.  

    ![Erstellen der bot-Anwendung](images/AzureLabs-Lab312-01.png)

3.  Die Projekt Mappe wird jetzt geöffnet. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf Projekt Mappe **mybot** , und klicken Sie auf **nuget-Pakete für**Projekt Mappe verwalten. 

    ![Erstellen der bot-Anwendung](images/AzureLabs-Lab312-02.png)

4.  Suchen Sie auf der Registerkarte **Durchsuchen** nach **Microsoft. bot. Builder. Integration. Aspnet. Core** (stellen Sie sicher, dass die **Vorabversion** aktiviert ist). Wählen Sie die Paketversion **4.0.1-Vorschau**aus, und klicken Sie auf die Projekt Felder. Klicken Sie dann auf **Installieren**. Sie haben nun die Bibliotheken installiert, die für **bot Framework V4**benötigt werden. Schließen Sie die Seite "nuget".

    ![Erstellen der bot-Anwendung](images/AzureLabs-Lab312-03.png)

5.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das *Projekt* **mybot**, und klicken Sie auf **|** **Klasse** **Hinzufügen** .

    ![Erstellen der bot-Anwendung](images/AzureLabs-Lab312-04.png)

6.  Benennen Sie die Klasse **mybot** , und klicken Sie auf **Hinzufügen**.

    ![Erstellen der bot-Anwendung](images/AzureLabs-Lab312-05.png)

7.  Wiederholen Sie den vorherigen Punkt, um eine weitere Klasse mit dem Namen " **Kontexts**" zu erstellen 

8.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf **wwwroot** , und klicken Sie auf **|** **Neues Element** **Hinzufügen** . Wählen Sie **HTML-Seite** aus (Sie finden Sie im unter Abschnitt Web). Nennen Sie die Datei **default. html**. Klicken Sie auf **Add**.

    ![Erstellen der bot-Anwendung](images/AzureLabs-Lab312-06.png)

9.  Die Liste der Klassen/Objekte in der **Projektmappen-Explorer** sollte wie in der folgenden Abbildung aussehen.

    ![Erstellen der bot-Anwendung](images/AzureLabs-Lab312-07.png)

10. Doppelklicken Sie auf die Klasse **conversationcontext** . Diese Klasse ist dafür verantwortlich, die Variablen beizubehalten, die vom bot verwendet werden, um den Konversations Kontext beizubehalten. Diese Konversations Kontext Werte werden in einer Instanz dieser Klasse verwaltet, da jede Instanz der **mybot** -Klasse jedes Mal aktualisiert wird, wenn eine Aktivität empfangen wird. Fügen Sie der-Klasse den folgenden Code hinzu:

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. Doppelklicken Sie auf die **mybot** -Klasse. Diese Klasse hostet die Handler, die von allen eingehenden Aktivitäten vom Kunden aufgerufen werden. In dieser Klasse fügen Sie den Code hinzu, der verwendet wird, um die Konversation zwischen dem bot und dem Kunden zu erstellen. Wie bereits erwähnt, wird eine Instanz dieser Klasse jedes Mal initialisiert, wenn eine Aktivität empfangen wird. Fügen Sie dieser Klasse den folgenden Code hinzu:

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. Doppelklicken Sie auf die **Startup** -Klasse. Diese Klasse initialisiert den bot. Fügen Sie der-Klasse den folgenden Code hinzu:

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. Öffnen Sie die **Programm** Klassendatei, und überprüfen Sie, ob der Code darin identisch mit folgendem ist:

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. Denken Sie daran, die Änderungen zu speichern. wechseln Sie hierzu in der Symbolleiste oben in Visual Studio zu **Datei** > **Alles speichern**.

## <a name="chapter-2---create-the-azure-bot-service"></a>Kapitel 2: Erstellen des Azure bot Service

Nachdem Sie den Code für den bot erstellt haben, müssen Sie ihn im Azure-Portal in einer Instanz des *webapp* -botdiensts veröffentlichen. In diesem Kapitel erfahren Sie, wie Sie den bot-Dienst in Azure erstellen und konfigurieren und dann Ihren Code darauf veröffentlichen.

1.  Melden Sie sich zunächst beim Azure-Portal an (https://portal.azure.com). 

    1. Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen. Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.

2.  Nachdem Sie angemeldet sind, klicken Sie in der oberen linken Ecke auf **Ressource erstellen** , suchen Sie nach *Web-App-bot*, und **drücken**Sie die EINGABETASTE.

    ![Erstellen der Azure bot Service](images/AzureLabs-Lab312-08.png)
 
3.  Auf der neuen Seite wird eine Beschreibung des *Web-App* -botdiensts bereitgestellt. Klicken Sie unten links auf dieser Seite auf die Schaltfläche **Erstellen** , um eine Verknüpfung mit diesem Dienst zu erstellen.

    ![Erstellen der Azure bot Service](images/AzureLabs-Lab312-09.png)
 
4.  Nachdem Sie auf **Erstellen**geklickt haben, klicken Sie auf:

    1. Fügen Sie den gewünschten **Namen** für diese Dienst Instanz ein.
    2. Wählen Sie ein **Abonnement**aus.
    3. Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** . Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Kursen) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie unter [diesem Link](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal) .

    4. Bestimmen Sie den Speicherort für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen). Der Speicherort wäre idealerweise in der Region, in der die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.
    5. Wählen Sie den für **Sie geeigneten Tarif** aus. Wenn Sie zum ersten Mal einen Web- *App-bot* -Dienst erstellen, sollte Ihnen ein Free-Tarif (mit dem Namen "F0") zur Verfügung stehen.
    6. Der **Name der APP** kann nur mit dem *botnamen*übereinstimmen. 
    7. Belassen Sie die *bot-Vorlage* als **Basic (C#)** .
    8. Der *App Service-Plan/Standort* muss für Ihr Konto automatisch ausgefüllt werden.
    9. Legen Sie die **Azure Storage** fest, die Sie zum Hosten des Bots verwenden möchten. Wenn Sie noch nicht über ein solches verfügen, können Sie es hier erstellen.
    10. Außerdem müssen Sie bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.
    11. Klicken Sie auf erstellen.
 
        ![Erstellen der Azure bot Service](images/AzureLabs-Lab312-10.png)

5.  Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.

6.  Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Erstellen der Azure bot Service](images/AzureLabs-Lab312-11.png) 
 
7.  Klicken Sie auf die Benachrichtigung, um die neue Dienst Instanz zu untersuchen. 

    ![Erstellen der Azure bot Service](images/AzureLabs-Lab312-12.png)
 
8. Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen. Sie gelangen zu ihrer neuen Azure-Dienst Instanz. 

    ![Erstellen der Azure bot Service](images/AzureLabs-Lab312-13.png)
 
9.  An diesem Punkt müssen Sie eine Funktion namens **Direct Line** einrichten, damit Ihre Client Anwendung mit diesem botdienst kommunizieren kann. Klicken Sie auf **Channels**, und klicken Sie dann im Abschnitt **Hinzufügen eines vorgestellten Kanals** auf **direkt linienchannel konfigurieren**.

    ![Erstellen der Azure bot Service](images/AzureLabs-Lab312-14.png)

10. Auf dieser Seite finden Sie die **geheimen Schlüssel** , mit denen sich Ihre Client-App bei dem bot authentifizieren kann. Klicken Sie auf die Schaltfläche **anzeigen** , und nehmen Sie eine Kopie einer der angezeigten Schlüssel auf, da Sie dies später in Ihrem Projekt benötigen. 

    ![Erstellen der Azure bot Service](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a>Kapitel 3 – Veröffentlichen des Bots für den Azure-Web-App-botdienst

Nachdem Ihr Dienst bereit ist, müssen Sie den von Ihnen zuvor erstellten botcode in ihren neu erstellten Web-App-botdienst veröffentlichen.

> [!NOTE] 
> Sie müssen ihren bot jedes Mal im Azure-Dienst veröffentlichen, wenn Sie Änderungen an der bot-Lösung/dem Code vornehmen.

1.  Wechseln Sie zurück zu Ihrer Visual Studio-Projekt Mappe, die Sie zuvor erstellt haben. 
2.  Klicken Sie mit der rechten Maustaste auf das Projekt **mybot** , und klicken Sie dann im **Projektmappen-Explorer**auf **veröffentlichen**.

    ![Veröffentlichen des Bots im Azure-Web-App-botdienst](images/AzureLabs-Lab312-16.png)

3.  Klicken Sie auf der Seite *Veröffentlichungsziel auswählen* auf **App Service**, wählen Sie dann **vorhandene**aus, klicken Sie schließlich auf **Profil erstellen** (möglicherweise müssen Sie neben der Schaltfläche *veröffentlichen* auf den Dropdown Pfeil klicken, wenn dies nicht angezeigt wird).

    ![Veröffentlichen des Bots im Azure-Web-App-botdienst](images/AzureLabs-Lab312-17.png)

4. Wenn Sie noch nicht bei Ihrem Microsoft-Konto angemeldet sind, müssen Sie dies hier tun.
5. Auf der Seite " **veröffentlichen** " müssen Sie das gleiche **Abonnement** festlegen, das Sie für die Erstellung des *Web-App* -botdiensts verwendet haben. Legen Sie dann die **Ansicht** als **Ressourcengruppe** fest, und wählen Sie in der Dropdown-Ordnerstruktur die **Ressourcengruppe** aus, die Sie zuvor erstellt haben. Klicken Sie auf **OK**. 

    ![Veröffentlichen des Bots im Azure-Web-App-botdienst](images/AzureLabs-Lab312-18.png)

6.  Klicken Sie jetzt auf die Schaltfläche "Publish" ( **veröffentlichen** ), und warten Sie, bis der bot veröffentlicht wird (es kann einige Minuten dauern).

    ![Veröffentlichen des Bots im Azure-Web-App-botdienst](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a>Kapitel 4 – Einrichten des Unity-Projekts

Folgendes ist eine typische Einrichtung für die Entwicklung mit gemischter Realität und ist daher eine gute Vorlage für andere Projekte.

1.  Öffnen Sie *Unity* , und klicken Sie auf **neu**. 

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-20.png)

2.  Sie müssen nun einen Unity-Projektnamen angeben. **Hololens-bot**einfügen. Stellen Sie sicher, dass die Projektvorlage auf **3D**festgelegt ist. Legen Sie den Speicherort auf einen geeigneten **Speicherort** fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind). Klicken Sie dann auf **Projekt erstellen**.

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-21.png)

3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist. Wechseln Sie zu **Edit > Preferences (Einstellungen bearbeiten** ), und navigieren Sie dann im neuen Fenster zu **externe Tools**. Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**. Schließen Sie das Fenster " **Einstellungen** ".

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-22.png)

4.  Navigieren Sie als nächstes zu **Datei > Buildeinstellungen** , wählen Sie **universelle Windows-Plattform**aus, und klicken Sie dann auf die Schaltfläche **Plattform wechseln** , um Ihre Auswahl zu übernehmen

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-23.png)

5.  In **Datei > Buildeinstellungen** , und stellen Sie Folgendes sicher:

    1.  **Zielgerät** ist auf **hololens** festgelegt

        > Legen Sie für die immersiven Headsets das **Zielgerät** auf *ein beliebiges Gerät*fest.

    2.  Der **Buildtyp** ist auf **D3D** festgelegt.

    3.  **SDK** ist auf **neueste installierte** Version festgelegt.

    4.  **Visual Studio-Version** ist auf **neueste installierte** Version festgelegt.

    5.  **Build und Run** sind auf **lokaler Computer** festgelegt.

    6.  Speichern Sie die Szene, und fügen Sie Sie dem Build hinzu. 

        1. Wählen Sie hierzu die Option **geöffnete Szenen hinzufügen**aus. Ein Fenster zum Speichern wird angezeigt.
        
            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-24.png)

        2. Erstellen Sie einen neuen Ordner für dieses und jede zukünftige Szene, und wählen Sie dann die Schaltfläche **neuer Ordner** aus, um einen neuen Ordner zu **erstellen.**

             ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-25.png)

        3. Öffnen Sie den neu erstellten Ordner **Szenen** , geben Sie im Feld *Dateiname*: Text **botscene**ein, und klicken Sie dann auf **Speichern**.

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-26.png)

    7. Die restlichen Einstellungen in den **Buildeinstellungen**sollten vorerst als Standard belassen werden.

6. Klicken Sie im Fenster *Buildeinstellungen* auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der *Inspektor* befindet. 

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-27.png)

7. In diesem Bereich müssen einige Einstellungen überprüft werden:

    1. Auf der Registerkarte **andere Einstellungen** :

        1. Die **Skript Lauf Zeit Version** sollte **experimentell sein (NET 4,6-Entsprechung)** ; Wenn Sie dies ändern, muss der Editor neu gestartet werden.
        2. **Skript** -Back-End sollte **.net** sein
        3. **API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-28.png)
      
    2. Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:

        - **Internet Client deklarieren**
        - **Tritt**

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-29.png)

    3. Weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), **unterstützt Tick Virtual Reality**, stellen Sie sicher, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-30.png)

8.  Zurück in *Buildeinstellungen* : _Unity C#_  -Projekte sind nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen neben this. 
9.  Schließen Sie das Fenster mit den Buildeinstellungen.
10. Speichern Sie Ihre Szene und Ihr Projekt (**Datei > Speichern Sie Szenen/Dateien > Speichern**Sie das Projekt).


## <a name="chapter-5--camera-setup"></a>Kapitel 5 – Kamera Einrichtung

> [!IMPORTANT]
> Wenn Sie die *Unity-Setup* Komponente dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie dieses [Azure-Mr-312-Package. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage)herunterladen, es als [**benutzerdefiniertes Paket**](https://docs.unity3d.com/Manual/AssetPackages.html)in das Projekt importieren und dann fortfahren [. Kapitel 7](#chapter-8--create-the-botobjects-class).

1.  Wählen Sie im Bereich *Hierarchie*die **Hauptkamera**aus. 
2.  Nachdem Sie diese Option ausgewählt haben, können Sie alle Komponenten der **Hauptkamera** im *Inspektor-Panel*sehen.

    1. Das **Kamera Objekt** muss als **Hauptkamera** benannt werden (Beachten Sie die Schreibweise).
    2. Das Hauptkamera **Kennzeichen** muss auf **maincamera** festgelegt sein (Beachten Sie die Schreibweise).
    3. Stellen Sie sicher, dass die **Transformations Position** auf **0, 0, 0** festgelegt ist.
    4. Legen Sie **klar Flags** auf voll **Tonfarbe**fest.
    5. Legen Sie die **Hintergrund** Farbe der Kamera Komponente auf **schwarz, Alpha 0 (Hexadezimal Code: #00000000)** fest.

    ![Kamera-Setup](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a>Kapitel 6 – Importieren der newtonsoft-Bibliothek

Zum Deserialisieren und Serialisieren von Objekten, die empfangen und an den bot-Dienst gesendet werden, müssen Sie die **newtonsoft** -Bibliothek herunterladen. Sie finden eine [kompatible Version, die bereits mit der richtigen Unity-Ordnerstruktur organisiert](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage)ist. 

Verwenden Sie das Unity-Paket, das in diesem Kurs verwendet wurde, um die newtonsoft-Bibliothek in Ihr Projekt zu importieren.

1.  Fügen Sie das *. unitypackage* zu Unity hinzu, indem Sie die Menüoption **Assets** >  > **benutzerdefiniertes Paket** **importieren** verwenden.

    ![Importieren der newtonsoft-Bibliothek](images/AzureLabs-Lab312-34.png)

2.  Vergewissern Sie sich, dass im Feld **Unity-Paket importieren** , das angezeigt wird, alles unter (und **einschließlich) Plug** -ins ausgewählt ist.

    ![Importieren der newtonsoft-Bibliothek](images/AzureLabs-Lab312-35.png)

3.  Klicken Sie auf die Schaltfläche **importieren** , um dem Projekt die Elemente hinzuzufügen.

4.  Wechseln Sie in der Projekt **Ansicht in den** Ordner **Newton Soft** unter Plug-in, und wählen Sie das newtonsoft-Plug-in aus.

    ![](images/AzureLabs-Lab312-35b.png)

5.  Vergewissern **Sie sich**, dass die Option "newtonsoft" ausgewählt **ist, und stellen**Sie sicher, dass **alle Plattformen** deaktiviert sind. Stellen Sie dann **sicher, dass** **wsaplayer** ebenfalls deaktiviert ist Dies dient nur zur Bestätigung, dass die Dateien ordnungsgemäß konfiguriert sind.

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > Wenn Sie diese Plug-ins markieren, werden Sie nur im Unity-Editor verwendet. Im WSA-Ordner gibt es eine andere Gruppe, die verwendet wird, nachdem das Projekt aus Unity exportiert wurde.

6.  Als nächstes müssen Sie den Ordner " **WSA** " im Ordner " **newtonsoft** " öffnen. Es wird eine Kopie derselben Datei angezeigt, die Sie soeben konfiguriert haben. Wählen Sie die Datei aus, und vergewissern Sie sich dann im Inspektor, dass
    -   **Jede Plattform** ist **deaktiviert** . 
    -   **nur** **wsaplayer** ist **aktiviert** .
    -   "Nicht **verarbeiten** " ist **aktiviert**

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a>Kapitel 7 – Erstellen des bottag

1.  Erstellen Sie ein neues **tagobjekt** mit dem Namen **bottag**. Wählen Sie die Hauptkamera in der Szene aus. Klicken Sie im Inspektor-Panel auf das Dropdown Menü Tag. Klicken Sie auf **Tag hinzufügen**.

    ![Kamera-Setup](images/AzureLabs-Lab312-32.png)
 
2.  Klicken Sie auf das Symbol **+** . Nennen Sie das neue **Tag** als **bottag**, *Speichern*.

    ![Kamera-Setup](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> Wenden Sie das **bottag** **nicht** auf die Hauptkamera an. Wenn Sie dies versehentlich abgeschlossen haben, stellen Sie sicher, dass Sie das Hauptkamera-Tag wieder in " *maincamera*" ändern.

## <a name="chapter-8--create-the-botobjects-class"></a>Kapitel 8 – Erstellen der botobjects-Klasse

Das erste Skript, das Sie erstellen müssen, ist die **botobjects** -Klasse, bei der es sich um eine leere Klasse handelt, die erstellt wird, sodass eine Reihe von anderen Klassen Objekten innerhalb desselben Skripts gespeichert und von anderen Skripts in der Szene aufgerufen werden kann.

Bei der Erstellung dieser Klasse handelt es sich lediglich um eine architektonische Wahl. diese Objekte könnten stattdessen in dem bot-Skript gehostet werden, das Sie später in diesem Kurs erstellen werden.

So erstellen Sie diese Klasse: 

1.  Klicken Sie mit der rechten Maustaste im *Projekt Panel*, und erstellen Sie dann **> Ordner**. Benennen Sie den Ordner mit **Skripts**. 

    ![Erstellen Sie den Ordner Skripts.](images/AzureLabs-Lab312-36.png)

2.  Doppelklicken Sie auf den Ordner **Scripts** , um ihn zu öffnen. Klicken Sie dann in diesem Ordner mit der rechten Maustaste auf, und wählen Sie  **C# > Skript erstellen**aus. Benennen Sie das Skript mit dem Namen **botobjects**. 

3.  Doppelklicken Sie auf das neue **botobjects** -Skript, um es in **Visual Studio**zu öffnen.

4.  Löschen Sie den Inhalt des Skripts, und ersetzen Sie ihn durch den folgenden Code:

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.

## <a name="chapter-9--create-the-gazeinput-class"></a>Kapitel 9 – Erstellen der Klasse "gazeinput"

Die nächste Klasse, die Sie erstellen, ist die " **gazeinput** "-Klasse. Diese Klasse ist für Folgendes zuständig:

- Erstellen eines Cursors, der den *Blick* des Players darstellt.
- Erkennen von Objekten, die vom Blickpunkt des Players erreicht werden, und Speichern eines Verweises auf erkannte Objekte.

So erstellen Sie diese Klasse: 

1.  Wechseln Sie zum Ordner " **Scripts** ", den Sie zuvor erstellt haben. 
2.  Klicken Sie mit der rechten Maustaste in den Ordner, und **Erstellen Sie > C# Skript**. Nennen Sie das Skript " **gazeinput**". 
3.  Doppelklicken Sie auf das neue **gazeinput** -Skript, um es in **Visual Studio**zu öffnen.
4.  Fügen Sie die folgende Zeile rechts oben in den Klassennamen ein:

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  Fügen Sie dann die folgenden Variablen in der Klasse " **gazeinput** " oberhalb der Methode " **Start ()** " hinzu:

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

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

6.  Code für die Methode " **Start ()** " sollte hinzugefügt werden. Dies wird aufgerufen, wenn die-Klasse initialisiert:

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  Implementieren Sie eine Methode, die den Cursor Cursor instanziieren und einrichten soll: 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  Implementieren Sie die Methoden, die den raycast von der Hauptkamera einrichten, und verfolgen Sie das aktuelle fokussierte Objekt.

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
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
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
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.

## <a name="chapter-10--create-the-bot-class"></a>Kapitel 10 – Erstellen der bot-Klasse

Das Skript, das Sie jetzt erstellen, wird als **bot**bezeichnet. Dies ist die Kern Klasse Ihrer Anwendung, die gespeichert wird: 

- Ihre Web-App-botanmelde Informationen
- Die Methode, die die User Voice-Befehle sammelt.
- Die erforderliche Methode zum Initiieren von Konversationen mit dem Web-App-bot 
- Die erforderliche Methode zum Senden von Nachrichten an Ihren Web-App-bot 

Um Nachrichten an den botdienst zu senden, erstellt die **sendmessageybot ()** -Coroutine eine-Aktivität, bei der es sich um ein Objekt handelt, das vom bot Framework als vom Benutzer gesendete Daten erkannt wird. 
 
So erstellen Sie diese Klasse: 

1. Doppelklicken Sie auf den Ordner **Skripts** , um ihn zu öffnen. 
2. Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf  **C# > Skript erstellen**. Benennen Sie den Skript- **bot**. 
3. Doppelklicken Sie auf das neue Skript, um es in Visual Studio zu öffnen.
4. Aktualisieren Sie die Namespaces so, dass Sie am Anfang der **bot** -Klasse wie folgt lauten:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. Fügen Sie innerhalb der **bot** -Klasse die folgenden Variablen hinzu:

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > Stellen Sie sicher, dass Sie Ihren botsecret- **Schlüssel** in die **botsecret** -Variable einfügen. Sie haben ihren **botsecret-Schlüssel** zu Beginn dieses Kurses in  **[Kapitel 2](#chapter-2---create-the-azure-bot-service), Schritt 10**notiert.

7. Der Code für " **Awa()** " und " **Start ()** " muss nun hinzugefügt werden. 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. Fügen Sie die beiden Handler hinzu, die von den Sprach Bibliotheken aufgerufen werden, wenn die sprach Erfassung beginnt und endet. Der " *diktationerkenzer* " hält die Erfassung der Benutzer Stimme automatisch an, wenn der Benutzer seine Sprache stoppt.

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. Der folgende Handler sammelt das Ergebnis der User Voice-Eingabe und ruft die Coroutine auf, die für das Senden der Nachricht an den Web-App-botdienst zuständig ist.

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. Die folgende Coroutine wird aufgerufen, um eine Konversation mit dem bot zu beginnen. Sie werden feststellen, dass nach Abschluss des Konversations Aufrufes die **sendmessagetocoroutine ()** aufruft, indem eine Reihe von Parametern übergeben wird, die festlegen, dass die Aktivität als leere Nachricht an den botdienst gesendet werden soll. Dadurch wird der botdienst aufgefordert, den Dialog zu initiieren.

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. Die folgende Coroutine wird aufgerufen, um die Aktivität zu erstellen, die an den bot-Dienst gesendet werden soll. 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. Die folgende Coroutine wird aufgerufen, um nach dem Senden einer Aktivität an den bot-Dienst eine Antwort anzufordern. 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. Die letzte Methode, die dieser Klasse hinzugefügt werden soll, ist erforderlich, um die Meldung in der Szene anzuzeigen:

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > In der Unity-Editor-Konsole wird möglicherweise ein Fehler angezeigt, in dem die **sceneorganisator** -Klasse fehlt. Ignorieren Sie diese Meldung, da Sie diese Klasse später in diesem Tutorial erstellen.

14.  Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.

## <a name="chapter-11--create-the-interactions-class"></a>Kapitel 11 – Erstellen der Klasse "Interaktionen"

Die Klasse, die Sie jetzt erstellen, wird als **Interaktionen**bezeichnet. Diese Klasse wird zum Erkennen der hololens-Tap-Eingaben vom Benutzer verwendet. 

Wenn der Benutzer während der Betrachtung des *bot* -Objekts in der Szene tippt und der bot bereit ist, auf Spracheingaben zu lauschen, ändert sich das bot-Objekt in **rot** und beginnt mit dem lauschen auf Spracheingaben. 

Diese Klasse erbt von der Klasse " **gazeinput** " und kann daher auf die Methode " **Start ()** " und Variablen aus dieser Klasse verweisen, die durch die Verwendung von " **Base**" bezeichnet wird. 
 
So erstellen Sie diese Klasse:

1.  Doppelklicken Sie auf den Ordner **Skripts** , um ihn zu öffnen. 
2.  Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf  **C# > Skript erstellen**. Benennen Sie das Skript mit **Interaktionen**. 
3.  Doppelklicken Sie auf das neue Skript, um es in Visual Studio zu öffnen.
4.  Aktualisieren Sie die Namespaces und die Klassen Vererbung so, dass Sie am Anfang der Klasse **Interaktionen** mit der folgenden übereinstimmen:

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  Fügen Sie innerhalb der **Interaktionen** -Klasse die folgende Variable hinzu:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  Fügen Sie dann die Methode " **Start ()** " hinzu:

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  Fügen Sie den Handler hinzu, der ausgelöst wird, wenn der Benutzer die Tap-Geste vor der hololens-Kamera ausführt.

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.

## <a name="chapter-12--create-the-sceneorganiser-class"></a>Kapitel 12 – Erstellen der sceneorganisator-Klasse

Die letzte in dieser Übungseinheit erforderliche Klasse heißt **sceneorganisator**. Diese Klasse wird die Szene Programm gesteuert einrichten, indem der Hauptkamera Komponenten und Skripts hinzugefügt werden und die entsprechenden Objekte in der Szene erstellt werden.
 
So erstellen Sie diese Klasse:

1.  Doppelklicken Sie auf den Ordner **Skripts** , um ihn zu öffnen. 
2.  Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf  **C# > Skript erstellen**. Nennen Sie das Skript **sceneorganisator**. 
3.  Doppelklicken Sie auf das neue Skript, um es in Visual Studio zu öffnen.
4.  Fügen Sie innerhalb der **sceneorganisator** -Klasse die folgenden Variablen hinzu:

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  Fügen Sie dann die Methoden " **Awa()** " und " **Start ()** " hinzu:

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  Fügen Sie die folgende Methode hinzu, die für das Erstellen des bot-Objekts in der Szene und das Einrichten der Parameter und Komponenten zuständig ist:

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  Fügen Sie die folgende Methode hinzu, die für die Erstellung des UI-Objekts in der Szene zuständig ist und die Antworten vom bot darstellt:

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.
9.  Ziehen Sie im Unity-Editor das Skript " **sceneorganisator** " aus dem Ordner "Scripts" auf die Hauptkamera. Die Szene-Organisator-Komponente sollte nun auf dem Hauptkamera Objekt angezeigt werden, wie in der folgenden Abbildung dargestellt.

    ![Erstellen der Azure bot Service](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a>Kapitel 13 – vor dem Aufbau

Um eine gründliche Test Ihrer Anwendung durchzuführen, müssen Sie Sie auf Ihre hololens querladen.
Bevor Sie vorgehen, stellen Sie Folgendes sicher:

-   Alle in [**Kapitel 4**](#chapter-4--set-up-the-unity-project) erwähnten Einstellungen sind richtig festgelegt. 
-   Das Skript **sceneorganisator** ist an das **Hauptkamera** Objekt angefügt. 
-   Stellen Sie in der **bot** -Klasse sicher, dass Sie Ihren botsecret- **Schlüssel** in die **botsecret** -Variable eingefügt haben.

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a>Kapitel 14 – erstellen und Sideload auf die hololens

Alles, was für den Unity-Abschnitt dieses Projekts erforderlich ist, ist nun abgeschlossen, sodass es an der Zeit ist, Sie aus Unity zu erstellen.

1.  Navigieren Sie zu **Buildeinstellungen**, **Datei > Buildeinstellungen...** .
2.  Klicken Sie im Fenster " **Buildeinstellungen** " auf " **Erstellen**".

    ![Entwickeln der APP aus Unity](images/AzureLabs-Lab312-38.png)

3.  Wenn dies nicht bereits geschehen ist, Tick **Unity C# -Projekte**.
4.  Klicken Sie auf **Erstellen**. Unity startet ein **Datei-Explorer** -Fenster, in dem Sie einen Ordner erstellen und auswählen müssen, in dem die App erstellt wird. Erstellen Sie diesen Ordner jetzt, und nennen Sie ihn " **App**". Klicken Sie dann mit ausgewähltem **App** -Ordner auf **Ordner auswählen**. 
5.  Unity startet das Projekt in den **App** -Ordner. 
6.  Nachdem die Erstellung von Unity abgeschlossen ist (Dies kann einige Zeit in Anspruch nehmen), wird ein **Datei-Explorer** -Fenster am Speicherort des Builds geöffnet (überprüfen Sie die Taskleiste, da Sie möglicherweise nicht immer über Ihrem Fenster angezeigt wird, sondern Sie über das Hinzufügen eines neuen Fensters benachrichtigt).

## <a name="chapter-15--deploy-to-hololens"></a>Kapitel 15 – bereitstellen in hololens

So stellen Sie auf hololens bereit:

1.  Sie benötigen die IP-Adresse Ihrer hololens (für die Remote Bereitstellung) und, um sicherzustellen, dass sich Ihre hololens im **Entwicklermodus**befinden. Gehen Sie dazu wie folgt vor:

    1. Öffnen Sie die Einstellungen, während Sie die hololens- **Einstellungen**durch tragen.
    2. Navigieren Sie zu **Netzwerk & Internet > Wi-Fi > Erweiterte Optionen**
    3. Notieren Sie sich die **IPv4** -Adresse.
    4. Navigieren Sie als nächstes wieder zu **Einstellungen**, und aktualisieren Sie dann **& Sicherheits > für Entwickler** . 
    5. Legen Sie den Entwicklermodus auf fest.

2.  Navigieren Sie zu Ihrem neuen Unity-Build ( **App** -Ordner), und öffnen Sie die Projektmappendatei mit **Visual Studio**.
3.  Wählen Sie in der Projektmappenkonfiguration **Debuggen**.
4.  Wählen Sie auf der Projektmappenplattform die Option **x86**, **Remote Computer**aus. 

    ![Stellen Sie die Lösung aus Visual Studio bereit.](images/AzureLabs-Lab312-39.png)
 
5.  Wechseln Sie zum **Menü Erstellen** , und klicken Sie auf **Lösung**bereitstellen, um die Anwendung auf die hololens quer zuladen.
6.  Ihre APP sollte nun in der Liste der installierten apps auf Ihren hololens angezeigt werden, die bereit sind, gestartet zu werden.

    > [!NOTE]
    > Legen Sie für die Bereitstellung auf dem immersiven Headset die Projektmappenplattform auf *lokaler Computer*fest, und legen Sie die **Konfiguration** auf *Debuggen*und *x86* als **Plattform**fest. Stellen Sie dann auf dem lokalen Computer bereit, indem Sie im **Menü Erstellen**die Option *Lösung*bereitstellen auswählen. 

## <a name="chapter-16--using-the-application-on-the-hololens"></a>Kapitel 16 – verwenden der Anwendung auf den hololens

- Nachdem Sie die Anwendung gestartet haben, sehen Sie den bot als blaue Kugel vor Ihnen.

- Verwenden Sie die **Tap-Geste** , während Sie die Kugel in der Kugel betrachten, um eine Konversation zu initiieren. 
 
- Warten Sie, bis die Konversation gestartet wird (die Benutzeroberfläche zeigt eine Meldung an, wenn dies geschieht). Nachdem Sie die einführende Nachricht vom bot erhalten haben, tippen Sie erneut auf den bot, damit Sie rot wird und mit der Überwachung ihrer Stimme beginnt. 

- Wenn Sie nicht mehr sprechen, sendet Ihre Anwendung Ihre Nachricht an den bot, und Sie erhalten umgehend eine Antwort, die in der Benutzeroberfläche angezeigt wird. 

- Wiederholen Sie den Vorgang, um weitere Nachrichten an Ihren bot zu senden (Sie müssen jedes Mal tippen, wenn Sie eine Nachricht übertragen möchten).

Diese Konversation veranschaulicht, wie der bot Informationen (ihren Namen) beibehalten und gleichzeitig bekannte Informationen bereitstellen kann (z. b. die Elemente, die gestockt sind).

#### <a name="some-questions-to-ask-the-bot"></a>Einige Fragen, um den bot zu Fragen:

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a>Ihre fertige Web-App-bot-Anwendung (v4)

Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die den Azure-Web-App-bot, Microsoft bot Framework V4, nutzt.

![Endgültiges Produkt](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a>Bonus Übungen

### <a name="exercise-1"></a>Übung 1

Die Konversations Struktur in dieser Übungseinheit ist sehr einfach. Verwenden Sie Microsoft Luis, um den bot-Funktionen für natürliche Sprache zu verwenden.

### <a name="exercise-2"></a>Übung 2

Dieses Beispiel umfasst nicht das Beenden einer Konversation und das Neustarten einer neuen Konversation. Um die bot-Funktion abzuschließen, versuchen Sie, den Abschluss der Konversation zu implementieren.
