---
title: Mr und Azure 303-Natural Language Understanding (Luis)
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie Azure Language Understanding Intelligence Service (Luis) in einer Mixed Reality-Anwendung implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Language Understanding Intelligence Service, Luis, hololens, immersive, VR
ms.openlocfilehash: fb00fe9079e49a7ada507e7407ef45fa7eeb0d7e
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63555157"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a>Mr und Azure 303: Verständnis in natürlicher Sprache (Luis)

In diesem Kurs erfahren Sie, wie Sie Language Understanding mithilfe von Azure Cognitive Services mit dem Language Understanding-API in eine gemischte Reality-Anwendung integrieren.

![Lab-Ergebnis](images/AzureLabs-Lab3-000.png)

Bei *Language Understanding (Luis)* handelt es sich um einen Microsoft Azure Dienst, der Anwendungen die Möglichkeit bietet, die Bedeutung von Benutzereingaben zu machen, z. b. durch das Extrahieren der gewünschten Person in ihren eigenen Worten. Dies wird durch Machine Learning erreicht, das die Eingabeinformationen versteht und erfährt und dann mit detaillierten, relevanten Informationen Antworten kann. Weitere Informationen finden Sie auf der [Seite Azure Language Understanding (Luis)](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).

Nachdem Sie diesen Kurs abgeschlossen haben, verfügen Sie über eine gemischte Reality-Headset-Anwendung, die Folgendes ausführen kann:

1.  Erfassen Sie die Sprache für Benutzereingaben, indem Sie das Mikrofon verwenden, das dem immersiven Headset zugeordnet ist. 
2.  Senden Sie das erfasste Diktat an den *Azure-Language Understanding Intelligent Service* (*Luis*). 
3.  Achten Sie darauf, dass Luis aus den Sende Informationen Bedeutung hat, die analysiert werden, und versuchen Sie zu bestimmen, ob die Anforderung des Benutzers hergestellt werden soll.

Die Entwicklung umfasst das Erstellen einer APP, in der der Benutzer die Sprach-und/oder den Blick verwenden kann, um die Größe und die Farbe der Objekte in der Szene zu ändern. Die Verwendung von Bewegungs Controllern wird nicht abgedeckt.

In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren. In diesem Kurs erfahren Sie, wie Sie einen Azure-Dienst in Ihr Unity-Projekt integrieren. Es ist Ihre Aufgabe, das wissen, das Sie aus diesem Kursgewinnen, zu nutzen, um ihre gemischte Reality-Anwendung zu verbessern.

Seien Sie darauf vorbereitet, Luis mehrmals zu trainieren. Dies wird in [Kapitel 12](#chapter-12--improving-your-luis-service)behandelt. Wenn Luis schneller trainiert wurde, erhalten Sie bessere Ergebnisse.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>Mr und Azure 303: Verständnis in natürlicher Sprache (Luis)</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Dieser Kurs konzentriert sich in erster Linie auf Windows Mixed Reality immersive (VR)-Headsets, aber Sie können auch das, was Sie in diesem Kurs lernen, auf Microsoft hololens anwenden. Wenn Sie den Kurs befolgen, finden Sie Hinweise zu allen Änderungen, die Sie möglicherweise zur Unterstützung von hololens verwenden müssen. Wenn Sie hololens verwenden, bemerken Sie möglicherweise bei der sprach Erfassung einen Echo.

## <a name="prerequisites"></a>Vorraussetzungen

> [!NOTE]
> Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen. Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Mai 2018). Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](install-the-tools.md) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt sind.

Für diesen Kurs empfehlen wir die folgende Hardware und Software:

- Einen Entwicklungs-PC, der [mit der Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for Immersive (VR)-Headset-Entwicklung kompatibel ist
- [Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus](install-the-tools.md)
- [Das neueste Windows 10 SDK](install-the-tools.md)
- [Unity 2017,4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- Ein [Windows Mixed Reality-Headset (VR)](immersive-headset-hardware-details.md) oder [Microsoft hololens](hololens-hardware-details.md) mit aktiviertem Entwicklermodus
- Eine Reihe von Kopfhörern mit einem integrierten Mikrofon (wenn das Headset nicht über eine integrierte Mic-und-Sprech Anwendung verfügt)
- Internet Zugriff für Azure-Setup und Luis-Abruf

## <a name="before-you-start"></a>Bevor Sie beginnen

1.  Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen). 
2.  Damit Ihr Computer das Diktat aktivieren kann, wechseln Sie zu **Windows-Einstellungen > Datenschutz > Sprache, & eingeben,** und drücken Sie dann die Schaltfläche **Sprachdienste aktivieren und Vorschläge eingeben**.
3.  Der Code in diesem Tutorial ermöglicht Ihnen das Aufzeichnen der standardmäßigen **Mikrofon Geräte** , die auf Ihrem Computer festgelegt sind. Stellen Sie sicher, dass das standardmikrofon als das Mikrofon festgelegt ist, das Sie zum Erfassen Ihrer Stimme verwenden möchten.
4.  Wenn Ihr Headset über ein integriertes Mikrofon verfügt, stellen Sie sicher, dass die Option *"Wenn ich mein Headset verwende, zu Headset mic wechseln"* in den Einstellungen für das *gemischte Reality-Portal* aktiviert ist.

    ![Einrichten des immersiven Headsets](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a>Kapitel 1 – Einrichten des Azure-Portals

Wenn Sie den *Language Understanding* -Dienst in Azure verwenden möchten, müssen Sie eine Instanz des-Dienstanbieter konfigurieren, die für die Anwendung verfügbar gemacht wird.

1.  Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

    > [!NOTE]
    > Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen. Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.

2.  Wenn Sie angemeldet sind, klicken Sie in der oberen linken Ecke auf **neu** , suchen Sie nach *Language Understanding*, und drücken Sie die **Eingabe**Taste. 

    ![Erstellen einer Luis-Ressource](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > Das Wort **New** wurde möglicherweise durch **Create a Resource**in neueren Portalen ersetzt.
 
3.  Die neue Seite auf der rechten Seite enthält eine Beschreibung des Language Understanding Dienstanbieter. Klicken Sie unten links auf dieser Seite auf die Schaltfläche **Erstellen** , um eine Instanz dieses Dienstanbieter zu erstellen.

    ![Luis-Dienst Erstellung-rechtliche Hinweise](images/AzureLabs-Lab3-02.png)
 
4.  Nachdem Sie auf erstellen geklickt haben, klicken Sie auf:

    1. Fügen Sie den gewünschten **Namen** für diese Dienst Instanz ein.
    2. Wählen Sie ein **Abonnement**aus.
    3. Wählen Sie den für **Sie geeigneten Tarif** aus. Wenn Sie zum ersten Mal einen *Luis-Dienst*erstellen, sollte Ihnen ein Free-Tarif (mit dem Namen "F0") zur Verfügung stehen. Die kostenlose Zuweisung sollte für diesen Kurs mehr als ausreichend sein.
    4. Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** . Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Kursen) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern. 

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Bestimmen Sie den **Speicherort** für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen). Der Speicherort wäre idealerweise in der Region, in der die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.
    6. Außerdem müssen Sie bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.
    7. Wählen Sie **Erstellen** aus.

        ![Erstellen eines Luis-Dienstanbieter-Benutzereingabe](images/AzureLabs-Lab3-03.png)
 
5.  Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.
6.  Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt. 
 
    ![Neues Azure-Benachrichtigungs Image](images/AzureLabs-Lab3-04.png)

7.  Klicken Sie auf die Benachrichtigung, um die neue Dienst Instanz zu untersuchen.

    ![Benachrichtigung bei erfolgreicher Ressourcen Erstellung](images/AzureLabs-Lab3-05.png)
 
8.  Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen. Sie gelangen zu ihrer neuen Luis-Dienst Instanz. 
 
    ![Zugriff auf Luis-Schlüssel](images/AzureLabs-Lab3-06.png)

9.  In diesem Lernprogramm muss Ihre Anwendung Aufrufe an Ihren Dienst durchführen. Dies erfolgt über den Abonnement Schlüssel Ihres dienstanzschlüssels.
10. Navigieren Sie auf der Seite " *Schnellstart* " Ihres *Luis-API* -Diensts zum ersten Schritt, rufen Sie *Ihre Schlüssel*ab, und klicken Sie auf " **Schlüssel** " (Sie können dies auch erreichen, indem Sie auf die blauen Hyperlink-Schlüssel klicken, die sich im Navigationsmenü Dienste befinden, gekennzeichnet durch das Schlüsselsymbol). Dadurch werden die Dienst *Schlüssel*angezeigt.
11. Erstellen Sie eine Kopie von einem der angezeigten Schlüssel, da Sie dies später in Ihrem Projekt benötigen. 
12. Klicken Sie auf der Seite *Dienst* auf *Language Understanding Portal* , um zu der Webseite umgeleitet zu werden, die Sie zum Erstellen des neuen Dienstanbieter in der Luis-App verwenden. 

## <a name="chapter-2--the-language-understanding-portal"></a>Kapitel 2 – das Language Understanding-Portal

In diesem Abschnitt erfahren Sie, wie Sie eine Luis-App im Luis-Portal erstellen. 

> [!IMPORTANT]
> Beachten Sie, dass das Einrichten von *Entitäten*, *Intents*und *Äußerungen* in diesem Kapitel nur der erste Schritt beim Erstellen eines Luis-diengs ist: Sie müssen den Dienst auch mehrmals neu trainieren, um ihn genauer zu gestalten. Das erneute Trainieren Ihres Dienstanbieter wird im [letzten Kapitel](#chapter-12--improving-your-luis-service) dieses Kurses behandelt. Stellen Sie also sicher, dass Sie den Dienst fertiggestellt haben.

1.  Wenn Sie das *Language Understanding-Portal*erreicht haben, müssen Sie sich ggf. mit denselben Anmelde Informationen wie Ihre Azure-Portal anmelden, falls Sie dies noch nicht getan haben. 

    ![Luis-Anmeldeseite](images/AzureLabs-Lab3-07.png)
 
2.  Wenn Sie zum ersten Mal Luis verwenden, müssen Sie zum unteren Rand der Willkommensseite Scrollen, um die Schaltfläche " **Luis-app erstellen** " zu suchen und darauf zu klicken.

    ![Seite "Luis-app erstellen"](images/AzureLabs-Lab3-08.png)
 
3.  Klicken Sie nach der Anmeldung auf " **meine apps** " (wenn Sie sich derzeit nicht in diesem Abschnitt befinden). Klicken Sie dann auf **neue APP erstellen**.

    ![Luis-my Apps-Image](images/AzureLabs-Lab3-09.png)
 
4.  *Benennen*Sie Ihre APP.
5.  Wenn Ihre APP eine andere Sprache als Englisch verstehen soll, sollten Sie die *Kultur* in die entsprechende Sprache ändern.
6.  Hier können Sie auch eine *Beschreibung* ihrer neuen Luis-app hinzufügen.

    ![Luis: Erstellen einer neuen App](images/AzureLabs-Lab3-10.png)

7.  Wenn Sie auf " **done**" klicken, geben Sie die buildseite *ihrer* neuen *Luis* -Anwendung ein.
8.  Es gibt einige wichtige Konzepte, die Sie kennen sollten:

    -   *Intent*stellt die Methode dar, die nach einer Abfrage des Benutzers aufgerufen wird. Eine *Absicht* kann über eine oder mehrere *Entitäten*verfügen.
    -   Die *Entität*ist eine Komponente der Abfrage, die die für die *Absicht*relevanten Informationen beschreibt.
    -   *Äußerungen*sind Beispiele für Abfragen, die vom Entwickler bereitgestellt werden, mit denen Luis sich selbst trainiert.

Wenn diese Konzepte nicht ganz klar sind, machen Sie sich keine Sorgen, da dieser Kurs Sie in diesem Kapitel näher erläutern wird.

Zunächst erstellen Sie die *Entitäten* , die zum Erstellen dieses Kurses benötigt werden.

9.  Klicken Sie auf der linken Seite der Seite auf *Entitäten*, und klicken Sie dann auf **neue Entität erstellen**.

    ![Neue Entität erstellen](images/AzureLabs-Lab3-11.png)

10. Nennen Sie die neue Entitäts *Farbe*, legen Sie den Typ auf *Simple*fest, und drücken Sie dann auf **done**.

    ![Einfache Entitäts Farbe erstellen](images/AzureLabs-Lab3-12.png)
 
11. Wiederholen Sie diesen Vorgang, um drei (3) weitere einfache Entitäten namens zu erstellen:

    -   *Upsizing*
    -   *Verkleinern*
    -   *target*

Das Ergebnis sollte wie in der folgenden Abbildung aussehen:

![Ergebnis der Entitäts Erstellung](images/AzureLabs-Lab3-13.png)
 
An dieser Stelle können Sie mit dem Erstellen von *Intents*beginnen. 

> [!WARNING]
> Löschen Sie nicht die Absicht " **keine** ".

12. Klicken Sie auf der linken Seite der Seite auf **Intents**, und klicken Sie dann auf **Create New Intent**.

    ![Neue Intents erstellen](images/AzureLabs-Lab3-14.png)

13. Nennen Sie die neue *Intent* **changeobjectcolor**.

    > [!IMPORTANT]
    > Dieser *beabsichtigte Name wird* im Code weiter unten in diesem Kurs verwendet. verwenden Sie daher für optimale Ergebnisse den Namen genau wie angegeben.

Nachdem Sie den Namen bestätigt haben, werden Sie zur Intents-Seite weitergeleitet.

![Seite "Luis-Intents"](images/AzureLabs-Lab3-15.png)

Sie werden feststellen, dass es ein Textfeld gibt, in dem Sie aufgefordert werden, 5 oder mehr unterschiedliche *Äußerungen*einzugeben.

> [!NOTE]
> Luis konvertiert alle Äußerungen in Kleinbuchstaben.

14. Fügen Sie die folgende *Äußerung* in das Textfeld Top ein (aktuell mit dem *Texttyp etwa 5 Beispiele...* ), und drücken **Sie die Eingabe**Taste:

```
The color of the cylinder must be red
```

Sie werden feststellen, dass die neue *Äußerung* in einer Liste unterhalb von angezeigt wird.

Fügen Sie im Anschluss an denselben Prozess die folgenden sechs (6) Äußerungen ein:

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

Für jede Äußerung, die Sie erstellt haben, müssen Sie identifizieren, welche Wörter von Luis als Entitäten verwendet werden sollen. In diesem Beispiel müssen Sie alle Farben als *Farb* Entität und den gesamten möglichen Verweis auf ein Ziel als *Ziel* Entität bezeichnen.

15. Klicken Sie hierzu in der ersten Äußerung auf den Word- *Zylinder* , und wählen Sie *Ziel*aus.

    ![Erkennen von Ausdrucks Zielen](images/AzureLabs-Lab3-16.png)
 
16. Klicken Sie nun auf das *Rote* Wort in der ersten Äußerung, und wählen Sie *Farbe*aus.

    ![Identifizieren von Ausdrucks Entitäten](images/AzureLabs-Lab3-17.png)
 
17. Bezeichnen Sie auch die nächste Zeile, wobei *Cube* ein *Ziel*sein sollte und *schwarz* eine *Farbe*sein sollte. Beachten Sie auch die Verwendung der Wörter *' this '* , *' it '* und *' This Object '* , die wir bereitstellen, damit auch nicht spezifische Zieltypen verfügbar sind. 

18. Wiederholen Sie den obigen Prozess, bis alle Äußerungen über die gekennzeichneten Entitäten verfügen. Wenn Sie Hilfe benötigen, sehen Sie sich das folgende Bild an.

    > [!TIP]
    > Beim Auswählen von Wörtern, um Sie als Entitäten zu bezeichnen:
    > - Klicken Sie einfach auf die einzelnen Wörter.
    > - Für einen Satz von zwei oder mehr Wörtern klicken Sie am Anfang und dann am Ende der Menge.

    > [!NOTE]
    > Sie können die UMSCHALT Fläche *Tokens anzeigen* verwenden, um zwischen **Entitäten/Tokens anzuzeigen**.

19. Die Ergebnisse sollten wie in den folgenden Abbildungen dargestellt werden, die die **Entitäten/Tokens anzeigen**:

    ![Token & Entitäts Sichten](images/AzureLabs-Lab3-18.png)
  
20. Klicken Sie an dieser Stelle oben rechts auf der Seite auf die Schaltfläche **trainieren** , und warten Sie, bis der kleine Round-Indikator darauf Grün zeigt. Dies deutet darauf hin, dass Luis erfolgreich trainiert wurde, um diese Absicht zu erkennen.

    ![Train Luis](images/AzureLabs-Lab3-19.png)
 
21. Erstellen Sie als Übung eine neue Absicht namens **changeobjectsize**, indem Sie die Entitäten *target*, *Upsizing*und *verkleinern*verwenden.
22. Fügen Sie nach dem gleichen Prozess wie die vorherige Absicht die folgenden acht (8) Äußerungen für die *Größen* Änderung ein:

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. Das Ergebnis sollte wie in der folgenden Abbildung aussehen:

    ![Einrichten der changeobjectsize-Token/-Entitäten](images/AzureLabs-Lab3-20.png) 

24. Nachdem beide Intents, **changeobjectcolor** und **changeobjectsize**erstellt und trainiert wurden, klicken Sie oben auf der Seite auf die Schaltfläche **veröffentlichen** .

    ![Luis-Dienst veröffentlichen](images/AzureLabs-Lab3-21.png)

25. Auf der *Veröffentlichungs* Seite beenden und veröffentlichen Sie Ihre Luis-APP, damit Sie von Ihrem Code aus darauf zugreifen können.

    1. Legen Sie die Dropdown- *Veröffentlichung auf* **Production**fest.
    2. Legen Sie die *Zeitzone* auf die Zeitzone fest.
    3. Aktivieren Sie das Kontrollkästchen **alle vorhergesagten Intent-Ergebnisse einschließen**.
    4. Klicken Sie auf **in Produktions Slot veröffentlichen**.

        ![Veröffentlichungs Einstellungen](images/AzureLabs-Lab3-22.png)

26. Im Abschnitt *Ressourcen und Schlüssel*:

    1.  Wählen Sie die Region aus, die Sie für die Dienst Instanz im Azure-Portal festlegen.
    2.  Unten wird ein **Starter_Key** -Element angezeigt, das Sie ignorieren.
    3.  Klicken Sie auf **Schlüssel hinzufügen** , und fügen Sie den *Schlüssel* ein, den Sie beim Erstellen Ihrer Dienst Instanz im Azure-Portal abgerufen haben. Wenn Ihr Azure-und das Luis-Portal beim gleichen Benutzer angemeldet sind, erhalten Sie Dropdown Menüs für den Mandanten *Namen*, den *Abonnement Namen*und den *Schlüssel* , den Sie verwenden möchten (hat denselben Namen wie zuvor im Azure-Portal angegeben).

    > [!IMPORTANT] 
    > Nehmen Sie unter *Endpunkt*eine Kopie des Endpunkts an, der dem von Ihnen eingefügten Schlüssel entspricht, und verwenden Sie ihn bald in Ihrem Code.
 
## <a name="chapter-3--set-up-the-unity-project"></a>Kapitel 3 – Einrichten des Unity-Projekts

Im folgenden finden Sie eine typische Einrichtung für die Entwicklung mit gemischter Realität und eine gute Vorlage für andere Projekte.

1.  Öffnen Sie *Unity* , und klicken Sie auf **neu**. 

    ![Starten Sie ein neues Unity-Projekt.](images/AzureLabs-Lab3-24.png)

2.  Sie müssen nun einen Unity-Projektnamen angeben und **MR_LUIS**einfügen. Stellen Sie sicher, dass Projekttyp auf **3D**festgelegt ist. Legen Sie den Speicherort auf einen geeigneten **Speicherort** fest (denken Sie daran, dass die Stamm Verzeichnisse besser sind). Klicken Sie dann auf **Projekt erstellen**.

    ![Geben Sie Details für ein neues Unity-Projekt an.](images/AzureLabs-Lab3-25.png)
 
3.  Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist. Wechseln Sie zu Edit > Preferences (Einstellungen bearbeiten), und navigieren Sie dann im neuen Fenster zu **externe Tools**. Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**. Schließen Sie das Fenster " **Einstellungen** ".

    ![Skript-Editor-Einstellung aktualisieren.](images/AzureLabs-Lab3-26.png)
 
4.  Navigieren Sie als nächstes zu **Datei >** Buildeinstellungen, und schalten Sie die Plattform auf **universelle Windows-Plattform**, indem Sie auf die Schaltfläche **Plattform wechseln** klicken.

    ![Fenster "Buildeinstellungen", Plattform zu UWP wechseln.](images/AzureLabs-Lab3-27.png)
 
5.  Wechseln Sie zu **Datei > Build-Einstellungen** , und stellen Sie Folgendes sicher:

    1. Das **Zielgerät** ist auf **ein beliebiges Gerät** festgelegt.

        > Legen Sie für Microsoft hololens das **Zielgerät** auf *hololens*fest.

    2. Der Buildtyp ist auf **D3D** festgelegt.
    3. **SDK** ist auf **neueste installierte** Version festgelegt.
    4. **Visual Studio-Version** ist auf **neueste installierte** Version festgelegt.
    5. **Build und Run** sind auf **lokaler Computer** festgelegt.
    6. Speichern Sie die Szene, und fügen Sie Sie dem Build hinzu.

        1. Wählen Sie hierzu die Option **geöffnete Szenen hinzufügen**aus. Ein Fenster zum Speichern wird angezeigt.
        
            ![Klicken Sie auf Schaltfläche "Open Szenen](images/AzureLabs-Lab3-28.png)

        2. Erstellen Sie einen neuen Ordner für dieses und jede zukünftige Szene, und wählen Sie dann die Schaltfläche **neuer Ordner** aus, um einen neuen Ordner zu **erstellen.**

            ![Neuen Ordner "Skripts" erstellen](images/AzureLabs-Lab3-29.png)

        3. Öffnen Sie den neu erstellten Ordner **Szenen** , geben Sie im Feld *Dateiname*: Text **MR_LuisScene**ein, und klicken Sie dann auf **Speichern**.

            ![Benennen Sie neue Szene.](images/AzureLabs-Lab3-30.png)

    7. Die restlichen Einstellungen in denBuildeinstellungen sollten vorerst als Standard belassen werden.

6. Klicken Sie im Fenster Buildeinstellungen auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der *Inspektor* befindet. 

    ![Öffnen Sie die Player-Einstellungen.](images/AzureLabs-Lab3-31.png) 
 
7. In diesem Bereich müssen einige Einstellungen überprüft werden:

    1. Auf der Registerkarte **andere Einstellungen** :

        1. Die **Lauf Zeit Version der Skript** Erstellung muss **stabil** sein (.NET 3,5-Entsprechung).
        2. **Skript** -Back-End sollte **.net** sein
        3. **API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten

            ![Aktualisieren Sie andere Einstellungen.](images/AzureLabs-Lab3-32.png)
      
    2. Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:

        1. **Internet Client deklarieren**
        2. **Tritt**

            ![Veröffentlichungs Einstellungen werden aktualisiert.](images/AzureLabs-Lab3-33.png)

    3. Weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), **unterstützt Tick Virtual Reality**, stellen Sie sicher, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.

        ![Aktualisieren Sie die X R-Einstellungen.](images/AzureLabs-Lab3-34.png)

8.  Zurück in Buildeinstellungen: _Unity C#_  -Projekte sind nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen neben this. 
9.  Schließen Sie das Fenster mit den Buildeinstellungen.
10. Speichern Sie Ihre Szene und Ihr Projekt (**Datei > Speichern Sie Szenen/Dateien > Speichern**Sie das Projekt).

## <a name="chapter-4--create-the-scene"></a>Kapitel 4 – Erstellen der Szene

> [!IMPORTANT]
> Wenn Sie die *Unity-Setup* Komponente dieses Kurses überspringen und direkt mit dem Code fortfahren möchten, können Sie dieses [. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage)herunterladen, es als [benutzerdefiniertes Paket](https://docs.unity3d.com/Manual/AssetPackages.html)in Ihr Projekt importieren und dann aus [Kapitel 5](#chapter-5--create-the-microphonemanager-class)fortfahren. 

1.  Klicken Sie mit der rechten Maustaste in einen leeren Bereich des Bereichs *Hierarchie*, und fügen Sie unter **3D-Objekt**eine **Ebene**hinzu.

    ![Erstellen Sie eine Ebene.](images/AzureLabs-Lab3-35.png)

2.  Wenn Sie erneut mit der rechten Maustaste in der *Hierarchie* klicken, um weitere Objekte zu erstellen, ist das ausgewählte Objekt das übergeordnete Objekt des neuen Objekts, wenn Sie noch das letzte Objekt ausgewählt haben. Vermeiden Sie dieses Problem, indem Sie auf einen leeren Bereich innerhalb der Hierarchie klicken und dann mit der rechten Maustaste klicken.

3.  Wiederholen Sie das oben beschriebene Verfahren, um die folgenden Objekte hinzuzufügen:

    1. *SP*
    2. *Sechs*
    3. *Cube*
    4. *3D-Text*

4.  Die resultierende Szenen *Hierarchie* sollte wie in der folgenden Abbildung aussehen:

    ![Einrichtung der Szenen Hierarchie.](images/AzureLabs-Lab3-36.png)
 
5.  Klicken Sie mit der linken Maustaste auf die **Hauptkamera** , um Sie auszuwählen. im *Inspektor-Panel* sehen Sie das Kamera Objekt mit allen zugehörigen Komponenten.
6.  Klicken Sie auf die Schaltfläche **Komponente hinzufügen** , die sich amunteren Rand des inspektorbereichs befindet.

    ![Audioquelle hinzufügen](images/AzureLabs-Lab3-37.png)
 
7.  Suchen Sie nach der Komponente namens *Audioquelle*, wie oben gezeigt.
8.  Stellen Sie außerdem sicher, dass die *Transformations* Komponente der Hauptkamera auf (0, 0, 0) festgelegt ist. Klicken Sie hierzu auf das **Zahnrad** Symbol neben der *Transformations* Komponente der Kamera und dann auf **Zurücksetzen**. Die *Transformations* Komponente sollte dann wie folgt aussehen:

    1.  Die *Position* ist auf **0, 0, 0**(null) festgelegt.
    2.  *Drehung* ist auf **0, 0, 0**festgelegt.

    > [!NOTE] 
    > Für Microsoft hololens müssen Sie auch Folgendes ändern, das Teil der **Kamera** Komponente ist, die sich auf der **Hauptkamera**befindet:
    > - **Flags löschen:** Voll Tonfarbe.
    > - **Hintergrund** ' Black, Alpha 0 ' – hexadezimal Farbe: #00000000.

9.  Klicken Sie mit der linken Maustaste auf die **Ebene** , um Sie auszuwählen. Legen Sie im *Inspektor-Panel* die *Transformations* Komponente mit den folgenden Werten fest:

    |       | Transformation- *Position* |       |
    |:-----:|:----------------------:|:-----:|
    | **STUBEN** | **TEENIE**                  | **Z** |
    | 0     | -1                     | 0     |


10. Klicken Sie mit der linken Maustaste auf die **Kugel** , um Sie auszuwählen. Legen Sie im *Inspektor-Panel* die *Transformations* Komponente mit den folgenden Werten fest:

    |       | Transformation- *Position* |       |
    |:-----:|:----------------------:|:-----:|
    | **STUBEN** | **TEENIE**                  | **Z** |
    | 2     | 1                      | 2     |

11. Klicken Sie mit der linken Maustaste auf den **Zylinder** , um ihn auszuwählen. Legen Sie im *Inspektor-Panel* die *Transformations* Komponente mit den folgenden Werten fest:

    |       | Transformation- *Position* |       |
    |:-----:|:----------------------:|:-----:|
    | **STUBEN** | **TEENIE**                  | **Z** |
    | -2    | 1                      | 2     |

12. Klicken Sie mit der linken Maustaste auf den **Cube** , um ihn auszuwählen. Legen Sie im *Inspektor-Panel* die *Transformations* Komponente mit den folgenden Werten fest:

    |        | Transformation- *Position* |       |  \| |       | Transformation- *Drehung* |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | **STUBEN** | **TEENIE**                   | **Z** |  \| | **STUBEN** | **TEENIE**                  | **Z** |
    | 0     | 1                       | 4     |  \| | 45    | 45                     | 0     | 

13. Klicken Sie mit der linken Maustaste auf das **neue Text** Objekt, um es auszuwählen. Legen Sie im *Inspektor-Panel* die *Transformations* Komponente mit den folgenden Werten fest:

    |       | Transformation- *Position* |       |  \| |       | Transformieren: *skalieren* |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | **STUBEN** | **TEENIE**                  | **Z** |  \| | **STUBEN** | **TEENIE**               | **Z** |
    | -2    | 6                      | 9     |  \| | 0,1   | 0,1                 | 0,1   | 

14. Ändern Sie den **Schrift** Grad in der **texmesh** -Komponente in **50**.
15. Ändern Sie den *Namen* des **textmesh** -Objekts in den **Diktat Text**.

    ![3D-Text Objekt erstellen](images/AzureLabs-Lab3-38.png)
 
16. Ihre Hierarchie Panel-Struktur sollte nun wie folgt aussehen:

    ![textmesh in der Szene Ansicht](images/AzureLabs-Lab3-38b.png)


17. Die endgültige Szene sollte wie in der folgenden Abbildung aussehen:

    ![Die Szenen Ansicht.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a>Kapitel 5 – Erstellen der Klasse "mikrophonemanager"

Das erste Skript, das Sie erstellen, ist die Klasse " *mikrophonemanager* ". Danach erstellen Sie den *luismanager* *, die Behaviour* -Klasse und schließlich die Klasse " *Blick* " (Sie können all diese jetzt erstellen, obwohl Sie in jedem Kapitel behandelt wird).

Die Klasse " *mikrophonemanager* " ist für Folgendes zuständig:

-   Erkennen des Aufzeichnungs Geräts, das an das Headset oder den Computer angefügt ist (je nachdem, welches der Standard ist).
-   Erfassen Sie das Audiomaterial (Voice), und speichern Sie es als Zeichenfolge.
-   Nachdem die Stimme angehalten wurde, senden Sie die Diktat an die *luismanager* -Klasse. 

So erstellen Sie diese Klasse: 

1.  Klicken Sie im *Projekt Panel*mit der rechten Maustaste, und **Erstellen Sie > Ordner**. Nennen Sie die Ordner **Skripts**. 

    ![Erstellen Sie den Ordner Skripts.](images/AzureLabs-Lab3-40.png)
 
2.  Wenn Sie den Ordner **Skripts** erstellt haben, doppelklicken Sie darauf, um zu öffnen. Klicken Sie dann in diesem Ordner mit der rechten Maustaste auf, und **Erstellen Sie > C# Skript**. Nennen Sie das Skript " *mikrophonemanager*". 

3.  Doppelklicken Sie auf " *mikrophonemanager* ", um die Datei mit *Visual Studio*zu öffnen.
4.  Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  Fügen Sie dann die folgenden Variablen in der Klasse " *mikrophonemanager* " hinzu:

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  Der Code für die Methoden " *Awake ()* " und " *Start ()* " muss nun hinzugefügt werden. Diese werden aufgerufen, wenn die-Klasse initialisiert:

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  Nun benötigen Sie die Methode, die die APP verwendet, um die sprach Erfassung zu starten und anzuhalten, und Sie an die *luismanager* -Klasse weiterzuleiten, die Sie bald erstellen werden. 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  Fügen Sie einen *Diktat Handler* hinzu, der aufgerufen wird, wenn die Stimme angehalten wird. Diese Methode übergibt den Diktat Text an die *luismanager* -Klasse.

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > Löschen Sie die *Update ()* -Methode, da Sie von dieser Klasse nicht verwendet wird.

9.  Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.

    > [!NOTE]
    > An dieser Stelle bemerken Sie einen Fehler, der im *Konsolen Panel des Unity-Editors*angezeigt wird. Dies liegt daran, dass der Code auf die *luismanager* -Klasse verweist, die Sie im nächsten Kapitel erstellen werden.

## <a name="chapter-6--create-the-luismanager-class"></a>Kapitel 6 – Erstellen der luismanager-Klasse

Es ist an der Zeit, die *luismanager* -Klasse zu erstellen, die den Aufruf an den Azure Luis-Dienst durchführt. 

Der Zweck dieser Klasse besteht darin, den Diktat Text von der Klasse " *mikrophonemanager* " zu empfangen und an die zu analysierende *Azure-Language Understanding-API* zu senden.

Diese Klasse deserialisiert die *JSON* -Antwort und ruft die entsprechenden Methoden der Behaviour *-Klasse auf* , um eine Aktion zu initiieren.

So erstellen Sie diese Klasse: 

1.  Doppelklicken Sie auf den Ordner " **Scripts** ", um ihn zu öffnen. 
2.  Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf  **C# > Skript erstellen**. Benennen Sie das Skript mit " *luismanager*". 
3.  Doppelklicken Sie auf das Skript, um es in Visual Studio zu öffnen.
4.  Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Beginnen Sie mit dem Erstellen von drei Klassen **innerhalb** der Klasse " *luismanager* " (innerhalb derselben Skriptdatei oberhalb der Methode " *Start ()* "), die die deserialisierte JSON-Antwort von Azure darstellt.

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  Fügen Sie als nächstes die folgenden Variablen in der Klasse " *luismanager* " hinzu:
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  Stellen Sie sicher, dass Sie Ihren Luis-Endpunkt jetzt platzieren (über Ihr Luis-Portal).

8.  Code für die *Awa()* -Methode muss nun hinzugefügt werden. Diese Methode wird aufgerufen, wenn die-Klasse initialisiert:

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  Nun benötigen Sie die Methoden, die von dieser Anwendung verwendet werden, um die von *der Klasse "* -Klasse" empfangene Diktat an *Luis*zu senden und die Antwort zu empfangen und zu deserialisieren. 
10. Nachdem der Wert der Absicht und der zugeordneten Entitäten ermittelt wurden, werden Sie an die Instanz der Behaviour *-Klasse über* mittelt, um die beabsichtigte Aktion zu initiieren.

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. Erstellen Sie eine neue Methode mit dem Namen *analyseresponcelements ()* , mit der die resultierende *analysedquery* gelesen und die Entitäten bestimmt werden. Nachdem diese Entitäten ermittelt wurden, werden Sie an die Instanz der Behaviour- *Klasse zur* Verwendung in den Aktionen übermittelt.

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognised intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > Löschen Sie die Methoden " *Start ()* " und " *Update ()* ", da Sie von dieser Klasse nicht verwendet werden.

12. Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.

> [!NOTE]
> An diesem Punkt sehen Sie mehrere Fehler, die im *Konsolen Panel des Unity-Editors angezeigt*werden. Dies liegt daran, dass der Code auf die *Verhaltens* Klasse verweist, die Sie im nächsten Kapitel erstellen werden.

## <a name="chapter-7--create-the-behaviours-class"></a>Kapitel 7 – Erstellen der Verhaltens Klasse

Die *Verhaltens* Klasse löst die Aktionen mithilfe der von der *luismanager* -Klasse bereitgestellten Entitäten aus.

So erstellen Sie diese Klasse: 

1.  Doppelklicken Sie auf den Ordner " **Scripts** ", um ihn zu öffnen. 
2.  Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf  **C# > Skript erstellen**. Benennen Sie das Skript *Verhalten*. 
3.  Doppelklicken Sie auf das Skript, um es in *Visual Studio*zu öffnen.
4.  Fügen Sie dann die folgenden Variablen in der *Verhaltens* Klasse hinzu:

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  Fügen Sie den *Awa()* -Methoden Code hinzu. Diese Methode wird aufgerufen, wenn die-Klasse initialisiert:

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  Die folgenden Methoden werden von der *luismanager* -Klasse aufgerufen (die Sie zuvor erstellt haben), um zu bestimmen, welches Objekt das Ziel der Abfrage ist, und dann die entsprechende Aktion auslöst.

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  Fügen Sie die *findtarget ()* -Methode hinzu, um zu bestimmen, welches der *gameobjects* das Ziel der aktuellen Absicht ist. Diese Methode verwendet standardmäßig das als Ziel festgelegte *gameobject* , wenn in den Entitäten kein explizites Ziel definiert ist.

    ```csharp
        /// <summary>
        /// Determines which obejct reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > Löschen Sie die Methoden " *Start ()* " und " *Update ()* ", da Sie von dieser Klasse nicht verwendet werden.

8.  Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.

## <a name="chapter-8--create-the-gaze-class"></a>Kapitel 8 – Erstellen der "Blick"-Klasse

Die letzte Klasse, die Sie zum Durchführen dieser APP benötigen, ist die " *Gaze* "-Klasse. Diese Klasse aktualisiert den Verweis auf das *gameobject-Objekt* , das sich derzeit im visuellen Fokus des Benutzers befindet.

So erstellen Sie diese Klasse: 

1.  Doppelklicken Sie auf den Ordner " **Scripts** ", um ihn zu öffnen. 
2.  Klicken Sie mit der rechten Maustaste in den Ordner **Scripts** , und klicken Sie auf  **C# > Skript erstellen**. Benennen Sie das *Skript mit*dem Namen. 
3.  Doppelklicken Sie auf das Skript, um es in *Visual Studio*zu öffnen.
4.  Fügen Sie den folgenden Code für diese Klasse ein:

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  Stellen Sie sicher, dass Sie die Änderungen in *Visual Studio* speichern, bevor Sie zu *Unity*zurückkehren.

## <a name="chapter-9--completing-the-scene-setup"></a>Kapitel 9 – Abschließen der Szenen Einrichtung

1.  Um die Einrichtung der Szene abzuschließen, ziehen Sie jedes Skript, das Sie erstellt haben, aus dem Ordner Scripts auf das **Hauptkamera** Objekt im Bereich *Hierarchie*.
2.  Wählen Sie die **Hauptkamera** aus, und sehen Sie sich im *Inspektor-Panel*an, dass jedes angefügte Skript angezeigt werden sollte. Sie werden feststellen, dass für jedes Skript Parameter vorhanden sind, die noch festgelegt werden müssen.

    ![Die Kamera Verweis Ziele werden festgelegt.](images/AzureLabs-Lab3-41.png)

3.  Um diese Parameter korrekt festzulegen, befolgen Sie die folgenden Anweisungen:

    1. " *Mikrophonemanager*":

        - Ziehen Sie das **Diktat Text** Objekt aus dem Bereich *Hierarchie*in das Feld **Diktat Text** Parameter value.

    2. *Verhalten*im *Hierarchie Panel*:

        - Ziehen Sie das **Sphere** -Objekt in das Feld *Kugel* Verweis Ziel.
        - Ziehen Sie den **Zylinder** in das Feld *Zylinder* Verweis Ziel.
        - Ziehen Sie den **Cube** in das Feld *Cube* Reference Target.

    3. *Blick*:

        - Legen Sie die *Maximale Länge des Blicks* auf **300** fest (sofern nicht bereits geschehen). 

4.  Das Ergebnis sollte wie in der folgenden Abbildung aussehen:

    ![Die angezeigte Kamera Verweis Ziele werden angezeigt.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a>Kapitel 10 – Testen im Unity-Editor

Testen Sie, ob die Szenen Einrichtung ordnungsgemäß implementiert ist.

Stellen Sie Folgendes sicher:

-   Alle Skripts werden an das **Hauptkamera** Objekt angefügt. 
-   Alle Felder im Hauptbereich der *Kamera Inspektor* sind ordnungsgemäß zugewiesen.

1.  Klicken Sie im *Unity-Editor*auf die Schaltfläche wieder **Gabe** . Die APP sollte innerhalb des angefügten immersiven Headsets ausgeführt werden.

2.  Probieren Sie einige Äußerungen aus, z. b.:

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > Wenn in der Unity-Konsole eine Fehlermeldung angezeigt wird, dass das Standardaudiogerät geändert wird, funktioniert die Szene möglicherweise nicht wie erwartet. Der Grund hierfür ist die Art und Weise, wie das Mixed Reality-Portal mit integrierten Mikrofonen für Headsets umgeht, auf denen es sich befindet. Wenn dieser Fehler angezeigt wird, halten Sie die Szene einfach an, und starten Sie Sie erneut, und die Dinge sollten erwartungsgemäß funktionieren.

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a>Kapitel 11 – erstellen und querladen der UWP-Lösung

Nachdem Sie sichergestellt haben, dass die Anwendung im Unity-Editor funktioniert, können Sie erstellen und bereitstellen.

So erstellen Sie Folgendes:

1.  Speichern Sie die aktuelle Szene, indem Sie auf **Datei > Speichern**klicken.
2.  Wechseln Sie zu **Datei >** Buildeinstellungen.
3.  Aktivieren Sie das Feld mit dem Namen **Unity C# -Projekte** (nützlich zum Anzeigen und Debuggen des Codes, nachdem das UWP-Projekt erstellt wurde.
4.  Klicken Sie auf **offene Szenen hinzufügen**, und klicken Sie dann auf **Erstellen**.

    ![Fenster mit Buildeinstellungen](images/AzureLabs-Lab3-43.png)

4.  Sie werden aufgefordert, den Ordner auszuwählen, in dem Sie die Projekt Mappe erstellen möchten. 

5.  Erstellen Sie einen Ordner *BUILDS* , und erstellen Sie in diesem Ordner einen anderen Ordner mit einem entsprechenden Namen Ihrer Wahl. 
6.  Klicken Sie auf **Ordner auswählen** , um den Build an diesem Speicherort zu starten.
 
    ![Ordner Create Builds](images/AzureLabs-Lab3-44.png)
    ![Select Builds Folder](images/AzureLabs-Lab3-45.png)
 
7.  Nachdem die Erstellung von Unity abgeschlossen ist (Dies kann einige Zeit in Anspruch nehmen), sollte ein **Datei-Explorer** -Fenster am Speicherort des Builds geöffnet werden.

Zum Bereitstellen auf dem lokalen Computer:

1.  Öffnen Sie in *Visual Studio*die Projektmappendatei, die im [vorherigen Kapitel](#chapter-10--test-in-the-unity-editor)erstellt wurde.
2.  Wählen Sieauf der Projektmappenplattform die Option **x86**, **lokaler Computer**aus.
3.  Wählen Sie in der Projektmappenkonfiguration **Debuggen**.

    > Für Microsoft hololens ist es möglicherweise einfacher, dies auf den *Remote*Computer festzulegen, damit Sie nicht auf Ihren Computer über das Team verfügen. Allerdings müssen Sie auch die folgenden Schritte ausführen:
    > - Informieren Sie sich über die **IP-Adresse** ihrer hololens. Sie finden diese in den *Einstellungen > Netzwerk & Internet > Wi-Fi-> Erweiterte Optionen*; die IPv4-Adresse ist die Adresse, die Sie verwenden sollten. 
    > - Stellen Sie sicher, dass der **Entwicklermodus** **auf**dem in den *Einstellungen > Update & Sicherheits > für Entwickler*gefunden.

    ![App bereitstellen](images/AzureLabs-Lab3-46.png)
 
4.  Wechseln Sie zum **Menü Erstellen** , und klicken Sie auf **Lösung** bereitstellen, um die Anwendung auf Ihren Computer zu übertragen.
5.  Ihre APP sollte nun in der Liste der installierten apps angezeigt werden, damit Sie gestartet werden können.
6.  Nach dem Start werden Sie von der APP aufgefordert, den Zugriff auf das _Mikrofon_zu autorisieren. Verwenden Sie die *Bewegungs Controller*, die *Spracheingabe*oder die *Tastatur* , um die Schaltfläche **Ja** zu drücken. 

## <a name="chapter-12--improving-your-luis-service"></a>Kapitel 12 – verbessern Ihres Luis-Dienstanbieter

>[!IMPORTANT] 
> Dieses Kapitel ist äußerst wichtig und muss möglicherweise mehrmals interiert werden, da es zur Verbesserung der Genauigkeit ihres Luis-Dienstanbieter beiträgt: Stellen Sie sicher, dass Sie dies durchführen.

Um das von Luis bereitgestellte Maß an Verständnis zu verbessern, müssen Sie neue Äußerungen erfassen und diese zum erneuten trainieren ihrer Luis-App verwenden.

Beispielsweise haben Sie Luis trainiert, um "Zunahme" und "Upsize" zu verstehen, aber möchten Sie nicht, dass Ihre APP auch Wörter wie "vergrößern" versteht?

Nachdem Sie die Anwendung mehrmals verwendet haben, wird alles, was Sie bereits erwähnt haben, von Luis gesammelt und im Luis-Portal verfügbar sein.

1.  Wechseln Sie nach diesem [Link](https://www.luis.ai/home)zu ihrer Portal Anwendung, und melden Sie sich an.
2.  Wenn Sie mit ihren MS-Anmelde Informationen angemeldet sind, klicken Sie auf den *Namen Ihrer APP*.
3.  Klicken Sie Links auf der Seite auf die Schaltfläche **Endpunkt Äußerungen überprüfen** .

    ![Überprüfen von Äußerungen](images/AzureLabs-Lab3-47.png)
 
4.  Ihnen wird eine Liste der Äußerungen angezeigt, die von ihrer gemischten Reality-Anwendung an Luis gesendet wurden.

    ![Liste der Äußerungen](images/AzureLabs-Lab3-48.png)
 
Sie werden einige hervorgehobene *Entitäten*bemerken. 

Wenn Sie mit dem Mauszeiger auf jedes markierte Wort zeigen, können Sie jede Äußerung überprüfen und bestimmen, welche Entität korrekt erkannt wurde, welche Entitäten falsch sind und welche Entitäten übersehen werden.

Im obigen Beispiel wurde festgestellt, dass das Wort "Spear" als Ziel hervorgehoben wurde. es ist daher notwendig, den Fehler zu korrigieren, indem Sie mit der Maus auf das Wort zeigen und auf " **Bezeichnung entfernen**" klicken.

![Überprüfen,](images/AzureLabs-Lab3-49.png)
ob das Bezeichnungs Bild "Ausdrucks![](images/AzureLabs-Lab3-50.png)
 
5.  Wenn Sie Äußerungen gefunden haben, die vollständig falsch sind, können Sie Sie mithilfe der Schaltfläche **Löschen** auf der rechten Seite des Bildschirms löschen.

    ![Falsche Äußerungen löschen](images/AzureLabs-Lab3-51.png)

6.  Wenn Sie der Meinung sind, dass Luis die Äußerung ordnungsgemäß interpretiert hat, können Sie das Verständnis überprüfen, indem Sie die Schaltfläche **zur ausgerichteten Absicht hinzufügen** verwenden.

    ![Zu ausgerichtete Absicht hinzufügen](images/AzureLabs-Lab3-52.png)

7.  Nachdem Sie alle angezeigten Äußerungen sortiert haben, versuchen Sie, die Seite erneut zu laden, um festzustellen, ob weitere Informationen verfügbar sind.
8.  Es ist sehr wichtig, diesen Prozess so oft wie möglich zu wiederholen, um das Verständnis Ihrer Anwendungen zu verbessern. 

**Viel Spass!**

## <a name="your-finished-luis-integrated-application"></a>Ihre beendete Luis-integrierte Anwendung

Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die den Azure Language Understanding Intelligence-Dienst nutzt, um zu verstehen, was ein Benutzer sagt und welche Informationen Sie tun.

![Lab-Ergebnis](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a>Bonus Übungen

### <a name="exercise-1"></a>Übung 1

Wenn Sie diese Anwendung verwenden, werden Sie möglicherweise bemerken, dass Sie bei der Betrachtung des Floor-Objekts sehen, dass die Farbe geändert wird. Können Sie herausfinden, wie Sie Ihre Anwendung daran hindern, die Bodenfarbe zu ändern?

### <a name="exercise-2"></a>Übung 2

Erweitern Sie die Luis-und App-Funktionen, und fügen Sie zusätzliche Funktionen für Objekte in der Szene hinzu. Erstellen Sie z. b. neue Objekte auf dem Blickpunkt, je nachdem, was der Benutzer sagt, und können Sie diese Objekte mit den vorhandenen Befehlen neben den aktuellen Szenen Objekten verwenden. 
