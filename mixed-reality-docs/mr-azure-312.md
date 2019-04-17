---
title: MR und Azure-312 - Bot-integration
description: Führen Sie diesen Kurs erfahren Sie, wie zum Erstellen und Bereitstellen von einem Bot mithilfe von Microsoft Bot Framework v4, und in einer mixed Reality-Anwendung mit ihm kommunizieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorials, api, maschinelles sehen, Hololens, immersive Vr, Microsoft Bot Framework, Version 4, Web-app-Bot, Bot Framework, Microsoft Bot
ms.openlocfilehash: b828aa4415103d280459bd2c666004c994b3e59d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604984"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

# <a name="mr-and-azure-312-bot-integration"></a>MR und Azure-312: Bot-integration

In diesem Kurs erfahren Sie, wie zum Erstellen und Bereitstellen von einem Bot mit dem Microsoft Bot Framework V4 und über eine Windows Mixed Reality-Anwendung mit ihm kommunizieren. 

![](images/AzureLabs-Lab312-00.png)

Die **Microsoft Bot Framework V4** ist ein Satz von APIs konzipiert, soll Entwicklern die Tools zum Erstellen einer Bot erweiterbares und skalierbares bieten Anwendung. Weitere Informationen finden Sie auf die [Microsoft Bot Framework-Seite](https://dev.botframework.com/) oder [V4-Git-Repository](https://github.com/Microsoft/botbuilder-dotnet/wiki).

Nach Abschluss dieses Kurses, werden Sie eine Windows Mixed Reality-Anwendung erstellt haben die können die folgenden Schritte ausführen:

1. Verwenden einer **Geste Tippen Sie auf** des Bots mit dem Lauschen auf der Stimme von Benutzer zu starten.
2. Wenn der Benutzer etwas gesagt hat, versucht den Bot, eine Antwort zurückgibt.
3. Anzeigen der Antwort des Bots als Text in der Nähe der Bot, in der Unity-Szene positioniert.

In Ihrer Anwendung obliegt es Ihnen, wie Sie die Ergebnisse in Ihr Design integrieren werden. Dieser Kurs erfahren Sie, wie Sie ein Azure-Dienst in Ihrem Unity-Projekt zu integrieren. Es ist Ihre Aufgabe, verwenden Sie das wissen, dass Sie aus diesem Kurs zum Verbessern Ihrer mixed Reality-Anwendung erhalten.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td> MR und Azure-312: Bot-integration</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Während dieser Kurs in erster Linie für HoloLens ausgerichtet ist, können Sie auch anwenden, was Sie in diesem Kurs, Faszinierende Windows Mixed Reality (VR)-Headsets lernen. Da immersive Headsets von (VR) nicht zugegriffen werden kann, Kameras verfügen, benötigen Sie eine externe Kamera, die mit dem PC verbunden. Wie Sie den Kurs halten, sehen Anmerkungen zu dieser Version Sie auf alle Änderungen, die Sie möglicherweise zur Unterstützung von immersive Headsets von (VR) einsetzen müssen.

## <a name="prerequisites"></a>Vorraussetzungen

> [!NOTE]
> In diesem Tutorial wurde für Entwickler mit Erfahrung mit Unity entwickelt und C#. Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Juli 2018) überprüft wurde. Sie können zur Verwendung der neuesten Software, wie in der [Installieren der Tools](install-the-tools.md) Artikel, obwohl es nicht davon ausgegangen werden soll, dass die Informationen in diesem Kurs perfekt entspricht was finden Sie in der neueren Software als aufgeführt ist unten.

Es wird empfohlen, die folgende Hardware und Software für diesen Kurs:

- Eine Entwicklungs-PC [kompatibel mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für immersive (VR) Kopfhörer-Entwicklung
- [Windows 10 Fall Creators Update (oder höher) mit der Entwicklermodus aktiviert ist](install-the-tools.md#installation-checklist)
- [Das neueste Windows 10-SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Ein [immersive Windows Mixed Reality (VR)-Kopfhörer](immersive-headset-hardware-details.md) oder [Microsoft HoloLens](hololens-hardware-details.md) mit Entwicklermodus aktiviert ist
- Zugriff auf das Internet für Azure, und klicken Sie zum Abrufen der Azure Bot. Weitere Informationen [folgen Sie diesem Link](https://dev.botframework.com/).

### <a name="before-you-start"></a>Bevor Sie beginnen

1.  Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung).
2.  Richten Sie ein und Testen Sie Ihre HoloLens. Bei Bedarf Unterstützung zum Einrichten Ihrer HoloLens, [stellen Sie sicher, dass die HoloLens-Setup-Artikel finden Sie unter](https://docs.microsoft.com/hololens/hololens-setup). 
3.  Es ist eine gute Idee, die Kalibrierung und Optimierung der Sensor ausführen, wenn Sie beginnen, eine neue HoloLens-app (manchmal ist es hilfreich, diese Aufgaben für jeden Benutzer) entwickeln. 

Um Hilfe zur Kalibrierung, befolgen Sie diese [Link zum Artikel HoloLens Kalibrierung](calibration.md#hololens).

Um Hilfe zur Optimierung der Sensor, befolgen Sie diese [Link zum Optimieren von HoloLens Sensor](sensor-tuning.md).

## <a name="chapter-1--create-the-bot-application"></a>Kapitel 1 – erstellen Sie die Bot-Anwendung

Der erste Schritt ist die Erstellung von Bots als lokale ASP.Net Core-Web-Anwendung. Sobald Sie fertig und getestet haben, veröffentlichen Sie es auf das Azure-Portal.

1.  Öffnen Sie Visual Studio. Erstellen ein neues Projekts wählen **ASP-NET-Core-Webanwendung** als Projekttyp (Sie finden es unter der Unterabschnitt .NET Core), und rufen sie **MyBot**. Klicken Sie auf **OK**.

2.  Im Fenster die Option erscheint **leere**. Außerdem stellen Sie sicher, dass das Ziel nastaven NA hodnotu **ASP-NET Core 2.0** und die Authentifizierung auf **keine Authentifizierung**. Klicken Sie auf **OK**.  

    ![Erstellen Sie die Bot-Anwendung](images/AzureLabs-Lab312-01.png)

3.  Die Lösung wird jetzt geöffnet. Mit der rechten Maustaste auf die Projektmappe **Mybot** in die **Projektmappen-Explorer** und klicken Sie auf **NuGet-Pakete für Projektmappe verwalten**. 

    ![Erstellen Sie die Bot-Anwendung](images/AzureLabs-Lab312-02.png)

4.  In der **Durchsuchen** Registerkarte, suchen Sie nach **Microsoft.Bot.Builder.Integration.AspNet.Core** (Stellen Sie sicher, dass **Vorabversion einschließen** aktiviert). Wählen Sie die Paketversion **4.0.1-Preview**, und aktivieren Sie die Project-Felder. Klicken Sie dann auf **installieren**. Sie haben nun die für die erforderlichen Bibliotheken installiert die **Bot Framework v4**. Schließen Sie die NuGet-Seite.

    ![Erstellen Sie die Bot-Anwendung](images/AzureLabs-Lab312-03.png)

5.  Mit der rechten Maustaste auf Ihre *Projekt*, **MyBot**in die **Projektmappen-Explorer** und klicken Sie auf **hinzufügen** **|** **Klasse**.

    ![Erstellen Sie die Bot-Anwendung](images/AzureLabs-Lab312-04.png)

6.  Nennen Sie die Klasse **MyBot** und klicken Sie auf **hinzufügen**.

    ![Erstellen Sie die Bot-Anwendung](images/AzureLabs-Lab312-05.png)

7.  Wiederholen Sie die vorherigen Punkt, um eine weitere Klasse namens erstellen **ConversationContext**. 

8.  Mit der rechten Maustaste auf **"Wwwroot"** in die **Projektmappen-Explorer** und klicken Sie auf **hinzufügen** **|** **neues Element**. Wählen Sie **HTML-Seite** (Sie finden es unter der Unterabschnitt Web). Nennen Sie die Datei **"default.HTML"**. Klicken Sie auf **Hinzufügen**.

    ![Erstellen Sie die Bot-Anwendung](images/AzureLabs-Lab312-06.png)

9.  Die Liste der Klassen / Objekte in der **Projektmappen-Explorer** sollte wie in der folgenden Abbildung aussehen.

    ![Erstellen Sie die Bot-Anwendung](images/AzureLabs-Lab312-07.png)

10. Doppelklicken Sie auf die **ConversationContext** Klasse. Diese Klasse ist zuständig für die mit den Variablen, die von den Bot verwendet, um den Kontext der Konversation zu verwalten. Diese Konversation Kontext-Werte werden in einer Instanz dieser Klasse verwaltet, da jede Instanz der **MyBot** Klasse wird jedes Mal eine Aktivität empfangen wird aktualisiert. Fügen Sie den folgenden Code zur Klasse hinzu:

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

11. Doppelklicken Sie auf die **MyBot** Klasse. Diese Klasse wird der Handler, die von einer eingehenden Aktivität aufgerufen wird, vom Kunden gehostet werden. In dieser Klasse fügen Sie den Code verwendet, um die Kommunikation zwischen den Bot und den Kunden zu erstellen. Wie bereits erwähnt, wird eine Instanz dieser Klasse jedes Mal initialisiert, die eine Aktivität empfangen wird. Fügen Sie dieser Klasse den folgenden Code hinzu:

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

12. Doppelklicken Sie auf die **Start** Klasse. Diese Klasse wird der Bot initialisiert werden. Fügen Sie den folgenden Code zur Klasse hinzu:

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

13. Öffnen der **Programm** Klassendatei, und überprüfen Sie, ob der Code identisch wie folgt:

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

14. Denken Sie daran, die Änderungen speichern, zu diesem Zweck zu wechseln **Datei** > **Alles speichern**, auf der Symbolleiste am oberen Rand der Visual Studio.

## <a name="chapter-2---create-the-azure-bot-service"></a>Kapitel 2: Erstellen der Azure Bot Service

Nun, dass Sie den Code für Ihren Bot erstellt haben, müssen Sie ihn in einer Instanz von Veröffentlichen der *Web-App-Bot* -Dienst auf dem Azure-Portal. In diesem Kapitel erfahren Sie, wie zum Erstellen und Konfigurieren der Bot Service in Azure und veröffentlichen Sie Ihren Code dann darauf.

1.  Melden Sie sich zunächst beim Azure-Portal (https://portal.azure.com). 

    1. Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen. Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.

2.  Sobald Sie angemeldet sind, klicken Sie auf **erstellen Sie eine Ressource** in der oberen linken Ecke, und suchen Sie nach *-Web-App-Bot*, und klicken Sie auf **EINGABETASTE**.

    ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-08.png)
 
3.  Die neue Seite bietet eine Beschreibung der *Web-App-Bot* Service. Unten links auf dieser Seite die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.

    ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-09.png)
 
4.  Nachdem Sie auf geklickt haben **erstellen**:

    1. Fügen Sie Ihre bevorzugte **Namen** für diese Dienstinstanz.
    2. Wählen Sie eine **Abonnement**.
    3. Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle zu bewahren, an die Azure-Dienste unter einer allgemeinen Ressourcengruppe mit einem einzelnen Projekt (z. B. z. B. diese Kurse) verknüpft ist).

        > Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, [führen Sie diesen Link](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)

    4. Bestimmen Sie den Speicherort für die Ressourcengruppe, (Wenn Sie eine neue Ressourcengruppe erstellen). Der Speicherort würde idealerweise in der Region sein, in dem die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.
    5. Wählen Sie die **Tarif** für Sie geeignet ist, ist dies die erste Zeit in die Erstellung einer *Web-App-Bot* -Dienst ein freier-Tarif (mit dem Namen F0) für Sie verfügbar sein sollen
    6. **App-Namen** kann einfach bleiben identisch mit der *botname*. 
    7. Lassen Sie die *Bot Vorlage* als **grundlegende (C#)**.
    8. *App Service-Plan/Standort* automatisch ausgefüllten für Ihr Konto hätte.
    9. Legen Sie die **Azure Storage** , dass Sie zum Hosten Ihren Bot verwenden möchten. Wenn Sie eine noch nicht, können Sie es hier erstellen.
    10. Sie müssen auch bestätigen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.
    11. Klicken Sie auf erstellen.
 
        ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-10.png)

5.  Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.

6.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-11.png) 
 
7.  Klicken Sie auf die Benachrichtigung, um Ihre neue Dienstinstanz zu untersuchen. 

    ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-12.png)
 
8. Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen. Sie werden für Ihre neue Azure-Dienstinstanz weitergeleitet. 

    ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-13.png)
 
9.  An diesem Punkt müssen Sie ein Feature namens einrichten **Direktverbindungen** auf Ihre Clientanwendung mit diesen Bot-Dienst kommunizieren kann. Klicken Sie auf **Kanäle**, klicken Sie dann in der **fügen Sie einen ausgewählten Kanal** an, klicken Sie im Abschnitt **Direktverbindungen konfigurieren Kanal**.

    ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-14.png)

10. Auf dieser Seite finden Sie die **geheime Schlüssel** Ihre Client-app für die Authentifizierung mit dem Bot ermöglichen. Klicken Sie auf die **anzeigen** Schaltfläche und kopieren Sie eines der angezeigten Schlüssel, da Sie dies später in Ihr Projekt benötigen. 

    ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a>Kapitel 3: Veröffentlichen des Bots mit dem Azure-Web-App-Bot-Dienst

Nun, dass Ihr Dienst bereit ist, müssen Sie Ihren Bot-Code, veröffentlichen, den Sie zuvor erstellt haben, um Ihre neu erstellte Web-App-Bot Service.

> [!NOTE] 
> Müssen Sie Ihren Bot mit dem Azure-Dienst veröffentlichen, jedes Mal, wenn Sie die Projektmappe für Bot ändern / code.

1.  Wechseln Sie zurück zu Visual Studio-Projektmappe, die Sie zuvor erstellt haben. 
2.  Mit der rechten Maustaste auf Ihre **MyBot** in-Projekt die **Projektmappen-Explorer**, klicken Sie dann auf **veröffentlichen**.

    ![Veröffentlichen Sie den Bot mit dem Azure-Web-App-Bot-Dienst](images/AzureLabs-Lab312-16.png)

3.  Auf der *Veröffentlichungsziel* auf **App Service**, klicken Sie dann **vorhandene auswählen**, klicken Sie schließlich auf **Profil erstellen** (möglicherweise müssen Sie Klicken Sie auf den Dropdownpfeil neben der *veröffentlichen* Schaltfläche, wenn dies nicht sichtbar ist).

    ![Veröffentlichen Sie den Bot mit dem Azure-Web-App-Bot-Dienst](images/AzureLabs-Lab312-17.png)

4. Wenn Sie nicht noch in Ihrem Microsoft Account angemeldet sind, müssen Sie nötig ist.
5. Auf der **veröffentlichen** Seite Sie sehen, Sie müssen die gleiche festlegen **Abonnement** , die Sie verwendet für die *Web-App-Bot* beim Erstellen des Diensts. Legen Sie dann die **Ansicht** als **Ressourcengruppe** und wählen Sie in der Dropdownliste Ordnerstruktur, die **Ressourcengruppe** Sie zuvor erstellt haben. Klicken Sie auf **OK**. 

    ![Veröffentlichen Sie den Bot mit dem Azure-Web-App-Bot-Dienst](images/AzureLabs-Lab312-18.png)

6.  Klicken Sie nun auf die **veröffentlichen** Schaltfläche, und warten Sie, bis der Bot veröffentlicht werden (es kann einige Minuten dauern).

    ![Veröffentlichen Sie den Bot mit dem Azure-Web-App-Bot-Dienst](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a>Kapitel 4: Einrichten von Unity-Projekts

Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit mixed Reality und daher ist eine gute Vorlage für andere Projekte.

1.  Open *Unity* , und klicken Sie auf **neu**. 

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-20.png)

2.  Sie müssen jetzt einen Unity-Projektnamen angeben. Fügen Sie **Hololens, Bot**. Stellen Sie sicher, dass die Projektvorlage nastaven NA hodnotu **3D**. Legen Sie die **Speicherort** auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser). Klicken Sie auf **projekterstellung**.

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-21.png)

3.  Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**. Wechseln Sie zu **Bearbeiten > Voreinstellungen** und navigieren Sie dann im neuen Fenster zu **externe Tools**. Änderung **externen Skript-Editors** zu **Visual Studio 2017**. Schließen der **Voreinstellungen** Fenster.

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-22.png)

4.  Öffnen Sie als Nächstes **Datei > Buildeinstellungen** , und wählen Sie **universelle Windows-Plattform**, klicken Sie dann auf die **Plattform wechseln** Schaltfläche, um Ihre Auswahl anzuwenden.

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-23.png)

5.  In der **Datei > Buildeinstellungen** und stellen Sie sicher, dass:

    1.  **Geräte** nastaven NA hodnotu **Hololens**

        > Legen Sie für die immersive Headsets, **Zielgerät** zu *einem beliebigen Gerät*.

    2.  **Buildtyp** nastaven NA hodnotu **D3D**

    3.  **SDK** nastaven NA hodnotu **zuletzt installierte**

    4.  **Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**

    5.  **Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**

    6.  Die Szene speichern und mit dem Build hinzugefügt werden. 

        1. Hierzu **öffnen Szenen hinzufügen**. Ein Speichern Fenster wird angezeigt.
        
            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-24.png)

        2. Erstellen einen neuen Ordner für, und alle zukünftigen, Szene, klicken Sie dann auf die **neuer Ordner** Schaltfläche zum Erstellen eines neuen Ordners, nennen Sie sie **Szenen**.

             ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-25.png)

        3. Öffnen Sie den neu erstellten **Szenen** Ordner, und klicken Sie dann in der *Dateiname*: Textfeld **BotScene**, klicken Sie dann auf **speichern**.

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-26.png)

    7. Die Einstellungen im verbleibenden **Buildeinstellungen**, sollte jetzt als Standard bleiben.

6. In der *Buildeinstellungen* Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dadurch wird den entsprechenden Bereich geöffnet, im Bereich, in dem die *Inspektor* befindet. 

    ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-27.png)

7. In diesem Bereich sind müssen einige Einstellungen überprüft werden:

    1. In der **Weitere Einstellungen** Registerkarte:

        1. **Scripting Runtime Version** muss **experimentell (NET 4.6 Äquivalent)**; das Ändern dieser Eigenschaft erfordert einen Neustart des Editors.
        2. **Back-End-Scripting** muss **.NET**
        3. **API-Kompatibilitätsebene** muss **.NET 4.6**

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-28.png)
      
    2. In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:

        - **InternetClient**
        - **Microphone**

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-29.png)

    3. Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality-SDK**  hinzugefügt wird.

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab312-30.png)

8.  Im *Buildeinstellungen* _Unity C#_  Projekte nicht mehr abgeblendet ist, aktivieren Sie das Kontrollkästchen neben dieser. 
9.  Schließen Sie das Fenster "erstellen".
10. Speichern Sie Ihre Szene und das Projekt (**Datei > SZENE speichern / FILE > Projekt speichern**).


## <a name="chapter-5--camera-setup"></a>Kapitel 5 – kamerasetup

> [!IMPORTANT]
> Wenn Sie, überspringen Sie möchten die *Unity einrichten* -Komponente dieser Kurs, und direkt in Code fortsetzen, können Sie zum Herunterladen [Azure-MR-312-Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), importieren Sie es in Ihr Projekt als eine [ **Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), und klicken Sie dann eine Fortsetzung [Kapitel 7](#chapter-7-–-create-the-botobjects-class).

1.  In der *Hierarchie Bereich*, wählen die **Main Camera**. 
2.  Wenn ausgewählt, Sie werden auf alle Komponenten finden Sie unter den **Main Camera** in die *Inspektor Bereich*.

    1. Die **Kameraobjekt** muss den Namen **Main Camera** (Beachten Sie die Schreibweise)
    2. Die Main Camera **Tag** muss festgelegt werden, um **MainCamera** (Beachten Sie die Schreibweise)
    3. Stellen Sie sicher, dass die **transformieren Position** nastaven NA hodnotu **0, 0, 0**
    4. Legen Sie **Kennzeichnungen löschen** zu **Volltonfarbe**.
    5. Legen Sie die **Hintergrund** Farbe der Kamera-Komponente auf **Schwarz, Alpha 0 (Hex-Code: #00000000)**

    ![Kamera-Setup](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a>Kapitel 6 – Import die Newtonsoft-Bibliothek

Können Sie deserialisieren und Serialisieren von Objekten, die empfangen und an den Bot-Dienst gesendet, die Sie herunterladen müssen die **Newtonsoft** Bibliothek. Sehen Sie eine [kompatible Version, die bereits mit der richtigen Unity Ordnerstruktur hier organisiert](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage). 

Um die Newtonsoft-Bibliothek in Ihr Projekt zu importieren, verwenden Sie das Unity-Paket, das in diesem Kurs stammt.

1.  Hinzufügen der *.unitypackage* in Unity mithilfe der **Assets** > **Paket importieren** > **Custom Package** Option des Menüs.

    ![Importieren Sie die Newtonsoft-Bibliothek](images/AzureLabs-Lab312-34.png)

2.  In der **Unity-Paket importieren** , ruft Sie Vergewissern Sie sich, alles, was unter (und einschließlich) **-Plug-Ins** ausgewählt ist.

    ![Importieren Sie die Newtonsoft-Bibliothek](images/AzureLabs-Lab312-35.png)

3.  Klicken Sie auf die **Import** , um die Elemente zu Ihrem Projekt hinzuzufügen.

4.  Wechseln Sie zu der **Newtonsoft** Unterordner **-Plug-Ins** in der Projektansicht und die Newtonsoft-Plug-in.

    ![](images/AzureLabs-Lab312-35b.png)

5.  Die Newtonsoft-Plug-in ausgewählt haben, stellen Sie sicher, dass **Any Platform** ist **deaktiviert**, klicken Sie dann sicher, dass **WSAPlayer** auch **deaktiviert**, Klicken Sie dann auf **übernehmen**. Dies ist, um sich zu vergewissern, dass die Dateien richtig konfiguriert sind.

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > Markieren diese-Plug-Ins konfiguriert sie nur im Unity-Editor verwendet werden. Es gibt ein anderen Satz von ihnen im Ordner "WSA" das verwendet werden soll, nachdem das Projekt aus Unity exportiert werden.

6.  Als Nächstes müssen Sie zum Öffnen der **WSA** Ordner, der innerhalb der **Newtonsoft** Ordner. Daraufhin wird eine Kopie der gleichen Datei, die Sie gerade konfiguriert haben. Wählen Sie die Datei, und klicken Sie dann im Inspector sicher, dass
    -   **Jede Plattform** ist **deaktiviert** 
    -   **nur** **WSAPlayer** ist **aktiviert**
    -   **Nicht verarbeiten** ist **aktiviert**

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a>Kapitel 7 – Erstellen der BotTag

1.  Erstellen Sie ein neues **Tag** Objekt mit dem Namen **BotTag**. Wählen Sie die Main-Kamera in der Szene. Klicken Sie auf das Tag-Dropdown-Menü in den Bereich der Eigenschaftenanalyse. Klicken Sie auf **Tag hinzufügen**.

    ![Kamera-Setup](images/AzureLabs-Lab312-32.png)
 
2.  Klicken Sie auf die **+** Symbol. Benennen Sie den neuen **Tag** als **BotTag**, *speichern*.

    ![Kamera-Setup](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> **Nicht** gelten die **BotTag** bis zur Kamera Main. Wenn Sie versehentlich dies getan haben, stellen Sie sicher, so ändern Sie den Tag an Main Camera *MainCamera*.

## <a name="chapter-8--create-the-botobjects-class"></a>Kapitel 8 – Erstellen der BotObjects-Klasse

Ist das erste Skript, das Sie erstellen müssen die **BotObjects** -Klasse, die eine leere Klasse erstellt, sodass eine Reihe von anderen Klassenobjekten innerhalb des gleichen Skripts gespeichert werden kann, und klicken Sie nach anderen Skripts in der Szene zugegriffen wird.

Die Erstellung von dieser Klasse ist ausschließlich eine architektonische Option, diese Objekte können stattdessen im Bot-Skript, das Sie später in diesem Kurs erstellen gehostet werden.

Diese Klasse zu erstellen: 

1.  Mit der rechten Maustaste den *Projektfenster*, klicken Sie dann **erstellen > Ordner**. Nennen Sie den Ordner **Skripts**. 

    ![Erstellen Sie Ordner "Scripts" an.](images/AzureLabs-Lab312-36.png)

2.  Doppelklicken Sie auf die **Skripts** Ordner aus, um ihn zu öffnen. In diesem Ordner, die mit der rechten Maustaste und wählen Sie dann **erstellen > C# Skript**. Nennen Sie das Skript **BotObjects**. 

3.  Doppelklicken Sie auf die neue **BotObjects** Skript öffnen Sie ihn mit **Visual Studio**.

4.  Löschen Sie den Inhalt des Skripts aus, und Ersetzen Sie ihn durch den folgenden Code:

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

6.  Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.

## <a name="chapter-9--create-the-gazeinput-class"></a>Kapitel 9: Erstellen der GazeInput-Klasse

Die nächste Klasse, die Sie erstellen wollen ist die **GazeInput** Klasse. Diese Klasse ist zuständig für:

- Erstellen eines Cursors, der darstellt der *bestaunen* des Spielers.
- Erkennen von Objekten, die durch die Blicke des Players erreicht, und verweisen auf erkannte Objekte.

Diese Klasse zu erstellen: 

1.  Wechseln Sie zu der **Skripts** Ordner, die Sie zuvor erstellt haben. 
2.  Mit der rechten Maustaste in den Ordner **erstellen > C# Skript**. Rufen Sie das Skript **GazeInput**. 
3.  Doppelklicken Sie auf die neue **GazeInput** Skript öffnen Sie ihn mit **Visual Studio**.
4.  Fügen Sie die folgende Zeile oben rechts auf den Namen der Klasse:

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  Klicken Sie dann fügen Sie die folgenden Variablen in der **GazeInput** Klasse, über die **Start()** Methode:

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

6.  Code für **Start()** Methode hinzugefügt werden sollen. Dies wird aufgerufen, wenn die Klasse initialisiert:

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

7.  Implementieren Sie eine Methode, die instanziiert und den Cursor Blicke einrichten: 

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

8.  Implementieren Sie die Methoden, die werden die Raycast von der Main-Kamera eingerichtet und werden mitverfolgen fokussierte Objekt.

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
 
9.  Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.

## <a name="chapter-10--create-the-bot-class"></a>Kapitel 10 – Erstellen der Bot-Klasse

Das Skript, das Sie erstellen wollen nun heißt **Bot**. Dies ist die Hauptklasse der Anwendung, die sie speichert: 

- Ihre Web-App-Bot-Anmeldeinformationen
- Die Methode, die die User Voice-Befehle erfasst.
- Die zum Initiieren Konversationen mit Ihrer Web-App-Bot-Methode 
- Die zum Senden von Nachrichten an Ihre Web-App-Bot-Methode 

Zum Senden von Nachrichten an den Bot-Dienst, der **SendMessageToBot()** Coroutine erstellen eine Aktivität, die ein Objekt, das von Bot Framework erkannt werden, wie Daten, die vom Benutzer gesendet wird. 
 
Diese Klasse zu erstellen: 

1. Doppelklicken Sie auf die **Skripts** Ordner, um ihn zu öffnen. 
2. Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen > C# Skript**. Nennen Sie das Skript **Bot**. 
3. Doppelklicken Sie auf das neue Skript aus, um ihn mit Visual Studio zu öffnen.
4. Aktualisieren Sie die Namespaces, um Folgendes am Anfang entsprechen den **Bot** Klasse:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. In der **Bot** Klasse fügen Sie die folgenden Variablen hinzu:

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
    > Stellen Sie sicher, Sie fügen Ihre **Bot Geheimschlüssel** in die **BotSecret** Variable. Sie haben angemerkt Ihre **Bot Geheimschlüssel** am Anfang des diesem Kurs in  **[Kapitel 2](#chapter-2---create-the-azure-bot-service), Schritt 10**.

7. Code für **Awake()** und **Start()** jetzt hinzugefügt werden muss. 

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

8. Fügen Sie den zwei Handler, die von Sprachbibliotheken aufgerufen werden, wenn Sprachaufnahme beginnt und endet. Die *DictationRecognizer* wird automatisch beendet, die Stimme des Benutzers erfassen, wenn der Benutzer die Spracheingabe beendet.

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

1. Der folgende Handler das Ergebnis der Spracheingabe des Benutzers erfasst und die Coroutine verantwortlich für das Senden der Nachricht an die Web-App-Bot-Dienst aufruft.

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

10. Die folgende Coroutine wird aufgerufen, um eine Konversation mit dem Bot zu beginnen. Sie werden feststellen, sobald der Konversation-Aufruf abgeschlossen ist, aufgerufen wird die **SendMessageToCoroutine()** durch eine Reihe von Parametern, die die Aktivität, die an der Bot Service als eine leere Nachricht gesendet werden festgelegt, wird übergeben. Dies erfolgt, um fordert der Bot Service, um das Dialogfeld zu initiieren.

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

11. Die folgende Coroutine wird aufgerufen, um erstellen die Aktivität, die an den Bot-Dienst gesendet werden. 

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

12. Die folgende Coroutine wird aufgerufen, um eine Antwort nach dem Senden einer Aktivitäts mit dem Bot-Dienst anzufordern. 

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

13. Die letzte Methode dieser Klasse hinzugefügt werden, ist erforderlich, die Nachricht in der Szene angezeigt:

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
    > Sie möglicherweise ein Fehler in der Unity-Editor-Konsole über fehlende finden Sie unter den **SceneOrganiser** Klasse. Ignorieren Sie diese, wie Sie diese Klasse später in diesem Tutorial erstellen.

14.  Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.

## <a name="chapter-11--create-the-interactions-class"></a>Kapitel 11: Erstellen der Interaktionen-Klasse

Die Klasse, die Sie erstellen wollen nun heißt **Interaktionen**. Diese Klasse wird verwendet, um die HoloLens Tippen Sie auf Eingabe vom Benutzer zu erkennen. 

Wenn der Benutzer tippt, bei der Suche auf die *Bot* -Objekt in der Szene, und der Bot ist bereit zum Abhören von Spracheingaben, die Bot-Objekt ändert die Farbe an, die **roten** und Spracheingaben lauscht. 

Diese Klasse erbt von der **GazeInput** Klasse, und kann daher auf die **Start()** -Methode und Variablen von dieser Klasse, gekennzeichnet durch die Verwendung von **Basis**. 
 
Diese Klasse zu erstellen:

1.  Doppelklicken Sie auf die **Skripts** Ordner, um ihn zu öffnen. 
2.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen > C# Skript**. Nennen Sie das Skript **Interaktionen**. 
3.  Doppelklicken Sie auf das neue Skript aus, um ihn mit Visual Studio zu öffnen.
4.  Aktualisieren Sie die Namespaces und die klassenvererbung mit dem folgenden, am oberen Rand identisch sein der **Interaktionen** Klasse:

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  In der **Interaktionen** Klasse fügen Sie die folgende Variable hinzu:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  Fügen Sie dann die **Start()** Methode:

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

7.  Hinzufügen des ereignishandlers, der ausgelöst wird, wenn der Benutzer die tippbewegung vor der Kamera HoloLens ausführt.

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

8. Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.

## <a name="chapter-12--create-the-sceneorganiser-class"></a>Kapitel 12 – Erstellen der SceneOrganiser-Klasse

Die letzte Klasse erforderlich, die in dieser Übung wird aufgerufen, **SceneOrganiser**. Diese Klasse wird die Szene programmgesteuert eingerichtet, von dem Main Camera-Komponenten und Skripts hinzufügen und erstellen die entsprechenden Objekte in der Szene.
 
Diese Klasse zu erstellen:

1.  Doppelklicken Sie auf die **Skripts** Ordner, um ihn zu öffnen. 
2.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen > C# Skript**. Nennen Sie das Skript **SceneOrganiser**. 
3.  Doppelklicken Sie auf das neue Skript aus, um ihn mit Visual Studio zu öffnen.
4.  In der **SceneOrganiser** Klasse fügen Sie die folgenden Variablen hinzu:

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

6.  Fügen Sie dann die **Awake()** und **Start()** Methoden:

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

7.  Fügen Sie die folgende Methode, die verantwortlich für die Bot-Objekt in der Szene erstellt und die Parameter und Komponenten einrichten:

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

7.  Fügen Sie die folgende Methode, die dafür verantwortlich, erstellen das UI-Objekt in der Szene, die Antworten von den Bot darstellt:

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

8.  Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.
9.  Im Unity-Editor, ziehen Sie die **SceneOrganiser** Skript aus dem Ordner Scripts der Main-Kamera. Die Szene Organiser für Komponente sollte jetzt in der Main Camera-Objekts angezeigt werden, wie in der folgenden Abbildung dargestellt.

    ![Erstellen der Azure Bot Service](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a>Kapitel 13 – vor dem Erstellen

Zur Durchführung eine gründliche Tests der Anwendung werden Sie querladen möchten sie auf Ihre HoloLens benötigen.
Vor dem Ausführen, stellen Sie sicher, dass:

-   Alle Einstellungen, die bereits erwähnt, der [ **Kapitel 4** ](#Chapter-4-–-Set-up-the-unity-project) ordnungsgemäß festgelegt sind. 
-   Das Skript **SceneOrganiser** angefügt ist die **Main Camera** Objekt. 
-   In der **Bot** Klasse, stellen Sie sicher, dass Sie eingefügt haben Ihre **Bot Geheimschlüssel** in die **BotSecret** Variable.

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a>Kapitel 14 – erstellen und per sideload übertragen, um die HoloLens

Alles, was Sie für den Unity-Abschnitt, der dieses Projekt wurde jetzt abgeschlossen daher ist es Zeit für die Erstellung von Unity.

1.  Navigieren Sie zu **Buildeinstellungen**, **Datei > Buildeinstellungen...** .
2.  Von der **Buildeinstellungen** Fenster, klicken Sie auf **erstellen**.

    ![Erstellen der app von Unity](images/AzureLabs-Lab312-38.png)

3.  Falls noch nicht geschehen, aktivieren Sie **Unity C# Projekte**.
4.  Klicken Sie auf **Erstellen**. Unity startet eine **Datei-Explorer** Fenster, in denen man erstellen, und wählen Sie einen Ordner zum Erstellen der app in. Erstellen Sie jetzt auf diesen Ordner, und nennen Sie es **App**. Klicken Sie dann mit der **App** Ordner ausgewählt haben, klicken Sie auf **Ordner auswählen**. 
5.  Erstellen Ihres Projekts zu Unity beginnt die **App** Ordner. 
6.  Einmal Unity wurde (es kann einige Zeit dauern) erstellen, öffnen ein **Datei-Explorer** Fenster am Speicherort des Builds (Überprüfen Sie Ihre Taskleiste aus, wie es unter Umständen nicht immer über Ihre Windows angezeigt und Sie über das Hinzufügen eines neuen benachrichtigt Fenster ").

## <a name="chapter-15--deploy-to-hololens"></a>Kapitel 15 – bereitstellen, um HoloLens

Für HoloLens bereitstellen:

1.  Sie benötigen die IP-Adresse Ihrer HoloLens (für Remote bereitstellen), und um sicherzustellen, dass Ihre HoloLens befindet sich in **Entwicklermodus**. Gehen Sie dazu wie folgt vor:

    1. Während Ihre HoloLens steht, geteert, öffnen Sie die **Einstellungen**.
    2. Wechseln Sie zu **Netzwerk und Internet > Wi-Fi-> Erweiterte Optionen**
    3. Beachten Sie die **IPv4** Adresse.
    4. Navigieren Sie als Nächstes zurück zum **Einstellungen**, und klicken Sie dann **Update und Sicherheit > für Entwickler** 
    5. Festlegen des Entwicklermodus auf.

2.  Navigieren Sie zu Ihrem neuen Unity-Build (die **App** Ordner), und öffnen Sie die Projektmappendatei mit **Visual Studio**.
3.  In der **Projektmappenkonfiguration** wählen **Debuggen**.
4.  In der **Projektmappenplattform**Option **X86**, **Remotecomputer**. 

    ![Die Lösung in Visual Studio bereit.](images/AzureLabs-Lab312-39.png)
 
5.  Wechseln Sie zu der **Menü "Build"** und klicken Sie auf **Projektmappe bereitstellen**, zum querladen der Anwendung in Ihrem HoloLens.
6.  Ihre app sollte nun in der Liste der installierten apps auf Ihre HoloLens, möchten Sie die gestartet werden, angezeigt werden.

    > [!NOTE]
    > Legen Sie zum Bereitstellen auf immersive Kopfhörer der **Projektmappenplattform** zu *lokalen Computer*, und legen Sie die **Konfiguration** zu *Debuggen*, mit *X86* als die **Plattform**. Klicken Sie dann bereitstellen, in der lokalen Computer, mit der **Menü "Build"**, wählen *Projektmappe bereitstellen*. 

## <a name="chapter-16--using-the-application-on-the-hololens"></a>Kapitel 16 – mithilfe der Anwendung auf die HoloLens

- Nachdem Sie die Anwendung gestartet haben, sehen Sie den Bot als eine blaue Kugel vor Ihnen.

- Verwenden der **tippen Geste** während Sie auf der Kugel eine Konversation initiieren gazing sind. 
 
- Warten Sie, bis die Konversation zu starten (die Benutzeroberfläche wird eine Meldung angezeigt, wenn dies geschieht). Wenn Sie die einleitende Meldung vom Bot erhalten haben, tippen Sie erneut auf den Bot damit beginnen, Ihre Meinung hören und rot angezeigt wird. 

- Nachdem Sie die Kommunikation beenden, Ihre Anwendung sendet die Nachricht an den Bot, und erhalten Sie umgehend eine Antwort, die in der Benutzeroberfläche angezeigt werden. 

- Wiederholen Sie den Vorgang, um Ihrem bot weitere Nachrichten senden (Sie müssen jedes Mal, die Sie Sen eine Nachricht möchten, tippen Sie auf).

Diese Konversation wird veranschaulicht, wie der Bot Informationen (Ihr Name), beibehalten kann, während zugleich die bekannten Informationen (z. B. die Elemente, die auf Lager sind).

#### <a name="some-questions-to-ask-the-bot"></a>Einige Fragen zu den Bot Fragen:

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a>Der fertigen Anwendung für die Web-App-Bot (v4)

Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die nutzt die Azure-Web-App-Bot, Microsoft Bot Framework v4.

![Endprodukt](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a>Bonus-Übungen

### <a name="exercise-1"></a>Übung 1

Die Struktur der Konversation in dieser Übung ist sehr einfach. Nutzen Sie Microsoft LUIS, um Ihren Bot Möglichkeiten der natürlichen Sprache Grundlegendes zu ermöglichen.

### <a name="exercise-2"></a>Übung 2

In diesem Beispiel enthält keine, eine Konversation zu beenden und neu zu starten eine neue Ressourcengruppe. Machen Sie die Bot-Funktion abgeschlossen ist, versuchen, schließen Sie sich dem Gespräch zu implementieren.
