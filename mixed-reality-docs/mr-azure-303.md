---
title: MR und Azure 303 - natürlicher sprachverständnis (LUIS)
description: Führen Sie diesen Kurs erfahren, wie Sie Azure Language Understanding Intelligence Service (LUIS) innerhalb einer mixed Reality-Anwendung zu implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorials, api, Language Understanding Intelligence Service, Luis, Hololens, immersive vr
ms.openlocfilehash: fb00fe9079e49a7ada507e7407ef45fa7eeb0d7e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59595913"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a>MR und Azure 303: Verstehen natürlicher Sprache (LUIS)

In diesem Kurs lernen Sie, wie Sie Language Understanding in einer mixed Reality-Anwendung, die mithilfe von Azure Cognitive Services, mit dem Language Understanding-API zu integrieren.

![Lab-Ergebnis](images/AzureLabs-Lab3-000.png)

*Language Understanding (LUIS)* ist ein Microsoft Azure-Dienst, bietet Anwendungen die Möglichkeit, extrahieren, was eine Person, in ihren eigenen Worten sollten Bedeutung aus Benutzereingaben, z. B. vornehmen. Dies erfolgt über Machine Learning versteht und lernt die eingegebenen Informationen und können dann mit detaillierten Informationen relevant sind, Antworten. Weitere Informationen finden Sie auf die [Azure Language Understanding (LUIS) Seite](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).

Nach Abschluss dieses Kurses, verfügen Sie über ein mixed Reality immersive Kopfhörer Anwendung die können die folgenden Schritte ausführen:

1.  Erfassen Sie User input Sprache, die über das Mikrofon, die an die immersive Kopfhörer angeschlossen. 
2.  Senden Sie die erfassten Diktat der *Azure Language Understanding Intelligent Service* (*LUIS*). 
3.  Haben Sie die LUIS-extrahieren, d. h. von der Send-Informationen analysiert, und versucht zu bestimmen, dass die Absicht der Anforderung des Benutzers vorgenommen werden.

Entwicklung umfasst die Erstellung einer App, in denen der Benutzer Lage ist, verwenden und/oder bestaunen zum Ändern der Größe und die Farbe der Objekte in der Szene. Die Verwendung der Motion-Controller wird nicht behandelt werden.

In Ihrer Anwendung obliegt es Ihnen, wie Sie die Ergebnisse in Ihr Design integrieren werden. Dieser Kurs erfahren Sie, wie Sie ein Azure-Dienst in Ihrem Unity-Projekt zu integrieren. Es ist Ihre Aufgabe, verwenden Sie das wissen, dass Sie aus diesem Kurs zum Verbessern Ihrer mixed Reality-Anwendung erhalten.

Mehrmals zu trainieren von LUIS darauf vorbereitet sein, die finden Sie im [Kapitel 12](#chapter-12--improving-your-luis-service). Sie erzielen bessere Ergebnisse weitere Male, die LUIS trainiert wurde.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td>MR und Azure 303: Verstehen natürlicher Sprache (LUIS)</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Während dieser Kurs in erster Linie für immersive Windows Mixed Reality (VR)-Headsets ausgerichtet ist, können Sie auch anwenden, was Sie in diesem Kurs, Microsoft HoloLens lernen. Wie Sie den Kurs halten, sehen Anmerkungen zu dieser Version auf Änderungen Sie möglicherweise zur Unterstützung von HoloLens einsetzen müssen. Wenn Sie HoloLens verwenden zu können, werden Sie einige Echo während der Sprachaufnahme feststellen.

## <a name="prerequisites"></a>Vorraussetzungen

> [!NOTE]
> In diesem Tutorial wurde für Entwickler mit Erfahrung mit Unity entwickelt und C#. Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Mai 2018) überprüft wurde. Sie können zur Verwendung der neuesten Software, wie in der [Installieren der Tools](install-the-tools.md) Artikel, obwohl es nicht davon ausgegangen werden soll, dass die Informationen in diesem Kurs perfekt was finden Sie in der neueren Software entspricht als die unten Angaben aufgeführten .

Es wird empfohlen, die folgende Hardware und Software für diesen Kurs:

- Eine Entwicklungs-PC [kompatibel mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für immersive (VR) Kopfhörer-Entwicklung
- [Windows 10 Fall Creators Update (oder höher) mit der Entwicklermodus aktiviert ist](install-the-tools.md)
- [Das neueste Windows 10-SDK](install-the-tools.md)
- [Unity 2017.4](install-the-tools.md)
- [Visual Studio 2017](install-the-tools.md)
- Ein [immersive Windows Mixed Reality (VR)-Kopfhörer](immersive-headset-hardware-details.md) oder [Microsoft HoloLens](hololens-hardware-details.md) mit Entwicklermodus aktiviert ist
- Eine Reihe von Kopfhörer mit ein eingebautes Mikrofon verfügen (wenn der Kopfhörer nicht über eine integrierte mic und die Lautsprecher verfügt)
- Zugriff auf das Internet für die Einrichtung von Azure und Abrufen von LUIS

## <a name="before-you-start"></a>Bevor Sie beginnen

1.  Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung). 
2.  Damit können Ihre Computer, um Spracheingaben zu aktivieren, wechseln Sie zu **Windows-Einstellungen > Datenschutz >-Sprache, Freihand & Eingabe** , und drücken Sie auf die Schaltfläche **Aktivieren von Sprachdienste und Typisierung Vorschläge**.
3.  Der Code in diesem Tutorial können Sie zum Aufzeichnen von der **Mikrofon Standardgerät** auf Ihrem Computer festlegen. Stellen Sie sicher, dass das Mikrofon-Standardgerät als den festgelegt ist, die Sie verwenden, um Ihre Stimme erfassen möchten.
4.  Verfügt Ihre Kopfhörer ein eingebautes Mikrofon verfügen, stellen Sie sicher, dass die Option *"Ich meine Kopfhörer wear, wechseln Sie zur Kopfhörer-mic"* eingeschaltet ist, der *Mixed Reality-Portal* Einstellungen.

    ![Einrichten von immersive Kopfhörer](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a>Kapitel 1: Einrichten der Azure-Portal

Verwenden der *Language Understanding* Service in Azure müssen Sie so konfigurieren Sie eine Instanz des Diensts, der für Ihre Anwendung verfügbar gemacht werden.

1.  Melden Sie sich bei der [Azure-Portal](https://portal.azure.com).

    > [!NOTE]
    > Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen. Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.

2.  Sobald Sie angemeldet sind, klicken Sie auf **neu** in der oberen linken Ecke, und suchen Sie nach *Language Understanding*, und klicken Sie auf **EINGABETASTE**. 

    ![LUIS-Ressource erstellen](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > Das Wort **neu** wurden möglicherweise durch ersetzt **erstellen Sie eine Ressource**, in neueren-Portalen.
 
3.  Die neue Seite auf der rechten Seite stellt eine Beschreibung des Luis-Diensts bereit. Unten links auf dieser Seite die **erstellen** Schaltfläche, um eine Instanz dieses Diensts zu erstellen.

    ![Erstellung von LUIS-Dienst – rechtliche Hinweise](images/AzureLabs-Lab3-02.png)
 
4.  Nachdem Sie auf Erstellen geklickt haben:

    1. Fügen Sie Ihre bevorzugte **Namen** für diese Dienstinstanz.
    2. Wählen Sie eine **Abonnement**.
    3. Wählen Sie die **Tarif** für Sie geeignet ist, ist dies die erste Zeit in die Erstellung einer *LUIS Service*, freier-Tarif (mit dem Namen F0) für Sie verfügbar sein sollen. Die kostenlose Zuordnung sollte mehr als ausreichend, für diesen Kurs sein.
    4. Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diese Kurse) unter einer allgemeinen Ressourcengruppe zu halten). 

        > Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, bitte [finden Sie im Artikel der Resource-Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Bestimmen der **Speicherort** für Ihre Ressourcengruppe aus (Wenn Sie eine neue Ressourcengruppe erstellen). Der Speicherort würde idealerweise in der Region sein, in dem die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.
    6. Sie müssen auch bestätigen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.
    7. Wählen Sie **Erstellen** aus.

        ![Erstellen von LUIS-Dienst - Benutzereingabe](images/AzureLabs-Lab3-03.png)
 
5.  Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.
6.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt. 
 
    ![Neue Benachrichtigung zur Azure-image](images/AzureLabs-Lab3-04.png)

7.  Klicken Sie auf die Benachrichtigung, um Ihre neue Dienstinstanz zu untersuchen.

    ![Benachrichtigung zur Erstellung einer erfolgreichen Ressource](images/AzureLabs-Lab3-05.png)
 
8.  Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen. Sie werden auf die neue Instanz der LUIS-Dienst weitergeleitet. 
 
    ![Schlüssel für den Zugriff auf LUIS](images/AzureLabs-Lab3-06.png)

9.  In diesem Tutorial müssen Ihre Anwendung Aufrufe an Ihren Dienst, was durch die Verwendung von Subscription-Key Ihres Diensts erfolgt.
10. Von der *Schnellstart* Seite von Ihrer *LUIS API* service, navigieren Sie zum ersten Schritt *nehmen Sie Ihre Schlüssel*, und klicken Sie auf **Schlüssel** (Sie können auch erreichen Sie dies, indem Sie auf den blauen Link Schlüssel befindet sich im Navigationsmenü Dienste durch ein Schlüsselsymbol gekennzeichnet). Dadurch wird angezeigt, den Dienst *Schlüssel*.
11. Erstellen Sie eine Kopie eines der angezeigten Schlüssel wird, da Sie dies später in Ihr Projekt benötigen. 
12. In der *Service* Seite, klicken Sie auf *Language Understanding-Portal* zur Webseite umgeleitet werden, das Sie verwenden werden, um den neuen Dienst, in der LUIS-App zu erstellen. 

## <a name="chapter-2--the-language-understanding-portal"></a>Kapitel 2 – Language Understanding-Portal

In diesem Abschnitt lernen Sie, wie Sie einer LUIS-App auf das LUIS-Portal. 

> [!IMPORTANT]
> Beachten Sie, die Einrichtung der *Entitäten*, *Intents*, und *Äußerungen* in diesem Kapitel wird nur der erste Schritt bei der Erstellung von Ihrem LUIS-Dienst: Sie müssen auch Erneutes Trainieren von dem Dienst mehrere Male auf, also um genauer zu erleichtern. Das erneute trainieren Ihres Diensts finden Sie in der [letzte Kapitel](#chapter-12--improving-your-luis-service) dieses Kurses, also stellen Sie sicher, dass Sie die Schritte ausführen.

1.  Beim Erreichen der *Language Understanding-Portal*, müssen Sie möglicherweise die Anmeldung, wenn Sie noch nicht mit den gleichen Anmeldeinformationen wie Ihr Azure-Portal sind. 

    ![LUIS-Anmeldeseite](images/AzureLabs-Lab3-07.png)
 
2.  Ist dies zum ersten Mal LUIS verwenden, müssen Sie einen Bildlauf zum unteren Rand der Seite "Willkommen", um zu suchen, und klicken auf die **erstellen LUIS-app** Schaltfläche.

    ![LUIS-app-Seite erstellen](images/AzureLabs-Lab3-08.png)
 
3.  Sobald Sie angemeldet sind, klicken Sie auf **"Meine apps"** (Wenn Sie nicht in diesem Abschnitt, derzeit sind). Klicken Sie dann auf **neue Anwendung erstellen**.

    ![LUIS - Meine apps-image](images/AzureLabs-Lab3-09.png)
 
4.  Geben Sie Ihrer app eine *Namen*.
5.  Wenn Ihre app um zu eine anderen Sprache als Englisch zu verstehen, sollten Sie ändern die *Kultur* auf die entsprechende Sprache.
6.  Hier können Sie auch Hinzufügen einer *Beschreibung* für Ihre neue LUIS-Anwendung.

    ![LUIS - Erstellen einer neuen app](images/AzureLabs-Lab3-10.png)

7.  Sobald Sie drücken **Fertig**, geben ein die *erstellen* Ihre neue Seite *LUIS* Anwendung.
8.  Es gibt einige wichtige Konzepte, die hier zu verstehen:

    -   *Beabsichtigte*, stellt die Methode, die nach einer Abfrage vom Benutzer aufgerufen wird. Ein *Absicht* möglicherweise eine oder mehrere *ENTITÄTEN*.
    -   *Entität*, ist eine Komponente von der Abfrage, die beschreibt, Informationen zu den *Absicht*.
    -   *Äußerungen*, sind Beispiele für Abfragen, sofern vom Entwickler, LUIS verwenden wird, um sich selbst zu trainieren.

Wenn diese Konzepte nicht perfekt sind löschen, aber keine Sorge, wie in diesem Kurs klären diese weiter in diesem Kapitel.

Beginnen Sie mit dem Erstellen der *Entitäten* zum Erstellen dieses Kurses erforderlich sind.

9.  Klicken Sie auf der linken Seite der Seite auf *Entitäten*, klicken Sie dann auf **neue Entität erstellen**.

    ![Neue Entität erstellen](images/AzureLabs-Lab3-11.png)

10. Rufen Sie die neue Entität *Farbe*, legen Sie deren Typ auf *einfache*, drücken Sie dann die **Fertig**.

    ![Erstellen Sie einfache Entität - Farbe](images/AzureLabs-Lab3-12.png)
 
11. Wiederholen Sie diesen Vorgang, um drei (3) Weitere Simple Entities mit dem Namen zu erstellen:

    -   *upsize*
    -   *downsize*
    -   *target*

Das Ergebnis sollte wie folgt aussehen:

![Ergebnis der Erstellung von Entitäten](images/AzureLabs-Lab3-13.png)
 
An diesem Punkt können Sie beginnen, erstellen *Intents*. 

> [!WARNING]
> Löschen Sie nicht die **keine** Absicht.

12. Klicken Sie auf der linken Seite der Seite auf **Intents**, klicken Sie dann auf **erstellen neue Absicht**.

    ![Erstellen Sie neue intents](images/AzureLabs-Lab3-14.png)

13. Rufen Sie die neue *Absicht* **ChangeObjectColor**.

    > [!IMPORTANT]
    > Dies *Absicht* Name wird verwendet, in den Code weiter unten in diesem Kurs, also am besten verwenden Sie diesen Namen exakt wie angegeben.

Nachdem Sie den Namen, die, den Sie auf der Seite "Intents" weitergeleitet werden überprüfen.

![LUIS - Intent-Elemente-Seite](images/AzureLabs-Lab3-15.png)

Sie werden bemerken, dass es ein Textfeld mit dem Sie aufgefordert werden, zum Typ 5 oder mehr verschiedene *Äußerungen*.

> [!NOTE]
> LUIS konvertiert-Äußerungen alle in Kleinbuchstaben.

14. Fügen Sie die folgenden *Äußerung* im Textfeld für die oberen (derzeit mit dem Text *gebe Sie etwa 5-Beispiele* ), und drücken Sie die **EINGABETASTE**:

```
The color of the cylinder must be red
```

Sie werden feststellen, dass die neue *Äußerung* wird in einer Liste darunter angezeigt.

Fügen Sie nach dem gleichen Verfahren die folgenden sechs (6) Äußerungen ein:

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

Für jede Äußerung, die Sie erstellt haben, müssen Sie ermitteln, welche Wörter von LUIS als Entitäten verwendet werden soll. In diesem Beispiel müssen Sie alle Farben als Bezeichnung für eine *Farbe* Entität und alle möglichen Verweis zu einem Ziel als einen *Ziel* Entität.

15. Zu diesem Zweck klicken Sie auf das Wort auf *Zylinder* in der ersten Äußerung und *Ziel*.

    ![Identifizieren der Äußerung Ziele](images/AzureLabs-Lab3-16.png)
 
16. Klicken Sie nun auf das Wort *roten* in der ersten Äußerung und *Farbe*.

    ![Identifizieren von Äußerung Entitäten](images/AzureLabs-Lab3-17.png)
 
17. Die nächste Zeile darüber hinaus bezeichnen, in denen *Cube* muss eine *Ziel*, und *Schwarz* muss eine *Farbe*. Beachten Sie auch die Verwendung der Wörter *"this"*, *"it"*, und *"dieses Objekt"*, die, daher bieten wir sind auch nicht-spezifischen Zieltypen verfügbar zu sein. 

18. Wiederholen Sie den oben beschriebenen Prozess aus, bis alle Äußerungen die Entitäten, die mit der Bezeichnung haben. Finden Sie unter dem folgenden Bild aus, wenn Sie Hilfe benötigen.

    > [!TIP]
    > Wenn Sie Wörter werden als Entitäten geben als Bezeichnung auswählen:
    > - Für einzelne Wörter einfach darauf klicken.
    > - Klicken Sie auf eine Gruppe von mindestens zwei Wörtern am Anfang, und klicken Sie dann am Ende des Satzes.

    > [!NOTE]
    > Können Sie die *Token Ansicht* Umschaltfläche Wechsel zwischen **Entitäten / Token-Ansicht**!

19. Die Ergebnisse sollten wie in den Abbildungen unten dargestellt angezeigt, die **Entitäten / Token-Ansicht**:

    ![Token und Sichten von Entitäten](images/AzureLabs-Lab3-18.png)
  
20. An diesem Punkt drücken Sie die **Train** Schaltfläche in der oberen rechten Rand der Seite, und warten Sie darauf, um Grün für den kleinen round-Indikator. Dies bedeutet, dass es sich bei LUIS erkennt diese Absicht erfolgreich trainiert wurde.

    ![Trainieren von LUIS](images/AzureLabs-Lab3-19.png)
 
21. Als Übung für Sie erstellen eine neue Absicht namens **ChangeObjectSize**, mit den Entitäten *Ziel*, *Upsizing*, und *verkleinern*.
22. Fügen Sie die folgenden acht (8) Äußerungen für folgt demselben Prozess wie die vorheriger Absicht *Größe* ändern:

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

    ![Richten Sie die Token ChangeObjectSize / Entitäten](images/AzureLabs-Lab3-20.png) 

24. Nachdem beide Intents, **ChangeObjectColor** und **ChangeObjectSize**, erstellt wurden, und klicken Sie mit der trainiert, auf die **veröffentlichen** Schaltfläche oben auf der Seite.

    ![LUIS-Dienst veröffentlichen](images/AzureLabs-Lab3-21.png)

25. Auf der *veröffentlichen* Seite, die Sie abschließen und Ihrer LUIS-App veröffentlichen, sodass sie von Ihrem Code zugegriffen werden kann.

    1. Legen Sie die Dropdownliste unten *veröffentlichen,* als **Produktion**.
    2. Legen Sie die *Timezone* in die relevante Zeitzone.
    3. Aktivieren Sie das Kontrollkästchen **einschließen, die alle vorhergesagt beabsichtigte Ergebnisse**.
    4. Klicken Sie auf **Veröffentlichen in den Produktionsslot**.

        ![Veröffentlichungseinstellungen](images/AzureLabs-Lab3-22.png)

26. Im Abschnitt *Ressourcen und Schlüssel*:

    1.  Wählen Sie die Region, die Sie für die Dienstinstanz im Azure-Portal festlegen.
    2.  Sie sehen eine **Starter_Key** folgt, ignoriert.
    3.  Klicken Sie auf **-Schlüssel hinzufügen** und fügen Sie der *Schlüssel* , dass Sie bei der Erstellung der Dienstinstanz im Azure-Portal abgerufen haben. Wenn derselbe Benutzer von Azure und das LUIS-Portal angemeldet sind, erhalten Sie in den Dropdownmenüs für *Mandantenname*, *Abonnementname*, und die *Schlüssel* () verwenden möchten müssen den gleichen Namen, wie Sie sich zuvor im Azure-Portal bereitgestellt ist.

    > [!IMPORTANT] 
    > Darunter *Endpunkt*, kopieren Sie den Endpunkt, der den Schlüssel für Sie eingefügt haben, werden Sie es in Kürze in Ihrem Code verwenden.
 
## <a name="chapter-3--set-up-the-unity-project"></a>Kapitel 3 – Einrichten der Unity-Projekt

Im folgenden ist ein typischer Eigenschaftensatz für die Entwicklung mit dem mixed Reality und daher ist eine gute Vorlage für andere Projekte.

1.  Open *Unity* , und klicken Sie auf **neu**. 

    ![Starten Sie die neues Unity-Projekt.](images/AzureLabs-Lab3-24.png)

2.  Sie müssen nun zum Bereitstellen eines Namen Unity-Projekt einfügen **MR_LUIS**. Stellen Sie sicher, dass der Projekttyp nastaven NA hodnotu **3D**. Legen Sie die **Speicherort** auf etwas für Sie geeignet (Denken Sie daran, näher an Stammverzeichnisse ist besser). Klicken Sie auf **projekterstellung**.

    ![Die Details für die neue Unity-Projekt.](images/AzureLabs-Lab3-25.png)
 
3.  Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**. Wechseln Sie zum Bearbeiten > Voreinstellungen und navigieren Sie dann im neuen Fenster zu **externe Tools**. Änderung **externen Skript-Editors** zu **Visual Studio 2017**. Schließen der **Voreinstellungen** Fenster.

    ![Aktualisieren Sie die Skript-Editor-Einstellung.](images/AzureLabs-Lab3-26.png)
 
4.  Öffnen Sie als Nächstes **Datei > Buildeinstellungen** , und wechseln von der Plattform bereitgestellten **universelle Windows-Plattform**, durch Klicken auf die **Plattform wechseln** Schaltfläche.

    ![Fenster "Einstellungen", Switch-Plattform für die UWP zu erstellen.](images/AzureLabs-Lab3-27.png)
 
5.  Wechseln Sie zu **Datei > Buildeinstellungen** und stellen Sie sicher, dass:

    1. **Geräte** nastaven NA hodnotu **einem beliebigen Gerät**

        > Legen Sie für die Microsoft HoloLens **Zielgerät** zu *HoloLens*.

    2. **Buildtyp** nastaven NA hodnotu **D3D**
    3. **SDK** nastaven NA hodnotu **zuletzt installierte**
    4. **Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**
    5. **Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**
    6. Die Szene speichern und mit dem Build hinzugefügt werden.

        1. Hierzu **öffnen Szenen hinzufügen**. Ein Speichern Fenster wird angezeigt.
        
            ![Klicken Sie auf, öffnen im Hintergrund-Schaltfläche "hinzufügen"](images/AzureLabs-Lab3-28.png)

        2. Erstellen einen neuen Ordner für, und alle zukünftigen, Szene, klicken Sie dann auf die **neuer Ordner** Schaltfläche zum Erstellen eines neuen Ordners, nennen Sie sie **Szenen**.

            ![Erstellen Sie neue Ordner "Scripts"](images/AzureLabs-Lab3-29.png)

        3. Öffnen Sie den neu erstellten **Szenen** Ordner, und klicken Sie dann in der *Dateiname*: Textfeld **MR_LuisScene**, drücken Sie dann die **speichern**.

            ![Geben Sie neue Szene einen Namen zu.](images/AzureLabs-Lab3-30.png)

    7. Die Einstellungen im verbleibenden *Buildeinstellungen*, sollte jetzt als Standard bleiben.

6. In der *Buildeinstellungen* Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dadurch wird den entsprechenden Bereich geöffnet, im Bereich, in dem die *Inspektor* befindet. 

    ![Öffnen der playereinstellungen.](images/AzureLabs-Lab3-31.png) 
 
7. In diesem Bereich sind müssen einige Einstellungen überprüft werden:

    1. In der **Weitere Einstellungen** Registerkarte:

        1. **Scripting Runtime Version** muss **stabile** (.NET 3.5 entspricht).
        2. **Back-End-Scripting** muss **.NET**
        3. **API-Kompatibilitätsebene** muss **.NET 4.6**

            ![Andere Einstellungen zu aktualisieren.](images/AzureLabs-Lab3-32.png)
      
    2. In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:

        1. **InternetClient**
        2. **Microphone**

            ![Veröffentlichungseinstellungen werden aktualisiert.](images/AzureLabs-Lab3-33.png)

    3. Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality-SDK**  hinzugefügt wird.

        ![Aktualisieren Sie die X-R-Einstellungen.](images/AzureLabs-Lab3-34.png)

8.  Im *Buildeinstellungen* _Unity C#_  Projekte nicht mehr abgeblendet ist, aktivieren Sie das Kontrollkästchen neben dieser. 
9.  Schließen Sie das Fenster "erstellen".
10. Speichern Sie Ihre Szene und das Projekt (**Datei > Speichern SZENE / FILE > Speichern Projekt**).

## <a name="chapter-4--create-the-scene"></a>Kapitel 4 – Erstellen der Szene

> [!IMPORTANT]
> Wenn Sie, überspringen möchten die *Unity einrichten* -Komponente dieser Kurs, und direkt in Code fortsetzen, können Sie zum Herunterladen [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), importieren Sie es in Ihr Projekt als eine [benutzerdefinierten Paket ](https://docs.unity3d.com/Manual/AssetPackages.html), und klicken Sie dann eine Fortsetzung [Kapitel 5](#chapter-5--create-the-microphonemanager-class). 

1.  Mit der rechten Maustaste in einen leeren Bereich des der *Hierarchie Bereich*unter **3D-Objekt**, Hinzufügen einer **Ebene**.

    ![Erstellen Sie eine Ebene.](images/AzureLabs-Lab3-35.png)

2.  Beachten Sie, wenn Sie mit der rechten Maustaste innerhalb der *Hierarchie* erneut um weitere Objekte, erstellen Sie immer noch das letzte Objekt ausgewählt haben, das ausgewählte Objekt wird das übergeordnete Element des neuen Objekts. Vermeiden Sie dies mit der linken Maustaste in einen leeren Bereich innerhalb der Hierarchie, und klicken Sie dann mit der rechten Maustaste.

3.  Wiederholen Sie das oben stehende Verfahren, um die folgenden Objekte hinzuzufügen:

    1. *Kugel*
    2. *Cylinder*
    3. *Cube*
    4. *3D Text*

4.  Der resultierende Szene *Hierarchie* sollte wie in der folgenden Abbildung:

    ![Einrichtung der Szene-Hierarchie.](images/AzureLabs-Lab3-36.png)
 
5.  Links klicken Sie auf die **Main Camera** um diese Option auswählen, sehen Sie sich die *Inspector-Bereich* sehen Sie die Kamera-Objekt mit allen der zugehörigen Komponenten.
6.  Klicken Sie auf die **Add Component** Schaltfläche am Ende der *Inspektor Bereich*.

    ![Hinzufügen von Audio-Quelle](images/AzureLabs-Lab3-37.png)
 
7.  Suchen Sie nach der Komponente mit dem Namen *Audio Source*, wie oben gezeigt.
8.  Stellen Sie außerdem sicher, dass die *transformieren* Komponente von der Main-Kamera, (0,0,0) festgelegt ist, wird dies erreichen Sie durch Drücken der **Zahnradsymbol** Symbol neben der Kamera *transformieren* Komponente auswählen und **zurücksetzen**. Die *transformieren* Komponente sollte dann wie folgt aussehen:

    1.  *Position* nastaven NA hodnotu **0, 0, 0**.
    2.  *Drehung* nastaven NA hodnotu **0, 0, 0**.

    > [!NOTE] 
    > Für die Microsoft HoloLens, müssen Sie auch Folgendes ein, ändern die sind Teil der **Kamera** -Komponente, die auf Ihre **Main Camera**:
    > - **Flags zu löschen:** Volltonfarbe entspricht.
    > - **Hintergrund** "Schwarz, Alpha 0" – Hex-Color: #00000000.

9.  Klicken Sie mit der Links auf die **Ebene** um es auszuwählen. In der *Inspektor Bereich* legen Sie die *transformieren* Komponente mit den folgenden Werten:

    |       | Transformieren - *Position* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | 0     | -1                     | 0     |


10. Klicken Sie mit der Links auf die **Kugel** um es auszuwählen. In der *Inspektor Bereich* legen Sie die *transformieren* Komponente mit den folgenden Werten:

    |       | Transformieren - *Position* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | 2     | 1                      | 2     |

11. Klicken Sie mit der Links auf die **Zylinder** um es auszuwählen. In der *Inspektor Bereich* legen Sie die *transformieren* Komponente mit den folgenden Werten:

    |       | Transformieren - *Position* |       |
    |:-----:|:----------------------:|:-----:|
    | **X** | **Y**                  | **Z** |
    | -2    | 1                      | 2     |

12. Klicken Sie mit der Links auf die **Cube** um es auszuwählen. In der *Inspektor Bereich* legen Sie die *transformieren* Komponente mit den folgenden Werten:

    |        | Transformieren - *Position* |       |  \| |       | Transformieren - *Drehung* |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | **X** | **Y**                   | **Z** |  \| | **X** | **Y**                  | **Z** |
    | 0     | 1                       | 4     |  \| | 45    | 45                     | 0     | 

13. Klicken Sie mit der Links auf die **neuen Text** Objekt, um es auszuwählen. In der *Inspektor Bereich* legen Sie die *transformieren* Komponente mit den folgenden Werten:

    |       | Transformieren - *Position* |       |  \| |       | Transformieren - *skalieren* |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | **X** | **Y**                  | **Z** |  \| | **X** | **Y**               | **Z** |
    | -2    | 6                      | 9     |  \| | 0.1   | 0.1                 | 0.1   | 

14. Änderung **Schriftgrad** in die **Text Mesh** Komponente **50**.
15. Ändern der *Namen* von der **Text Mesh** -Objekt **Diktat Text**.

    ![3D-Objekt Text erstellen](images/AzureLabs-Lab3-38.png)
 
16. Die Struktur der Hierarchie Bereich sollte jetzt wie folgt aussehen:

    ![mesh-Text in der Szenenansicht](images/AzureLabs-Lab3-38b.png)


17. Die endgültige Szene sollte wie folgt aussehen:

    ![Die Szenenansicht.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a>Kapitel 5 – Erstellen der MicrophoneManager-Klasse

Das erste Skript, das Sie erstellen wollen ist die *MicrophoneManager* Klasse. Anschluss erstellen Sie die *LuisManager*, *Verhalten* -Klasse, und zuletzt die *bestaunen* Klasse (gerne alle diese jetzt zu erstellen, wenn es Sie behandelt werden erreichen Sie jedes Kapitel).

Die *MicrophoneManager* -Klasse ist verantwortlich für:

-   Erkennen das Aufnahmegerät, die an den Kopfhörer oder die Computer, die (je nachdem, was der Standardwert ist) angefügt.
-   Das Audio (Sprache) und Diktat als Zeichenfolge zu speichern.
-   Nachdem die Stimme angehalten wurde, senden Sie die diktatfunktion, um die *LuisManager* Klasse. 

Diese Klasse zu erstellen: 

1.  Mit der rechten Maustaste den *Projekt Bereich*, **erstellen > Ordner**. Rufen Sie den Ordner **Skripts**. 

    ![Erstellen Sie Ordner "Scripts" an.](images/AzureLabs-Lab3-40.png)
 
2.  Mit der **Skripts** Ordner erstellt haben, doppelklicken klicken Sie darauf, zu öffnen. Klicken Sie dann in diesem Ordner mit der rechten Maustaste, **erstellen > C# Skript**. Nennen Sie das Skript *MicrophoneManager*. 

3.  Klicken Sie mit der Doppelklicken auf *MicrophoneManager* , öffnen Sie ihn mit *Visual Studio*.
4.  Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  Klicken Sie dann fügen Sie die folgenden Variablen in der *MicrophoneManager* Klasse:

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  Code für *Awake()* und *Start()* Methoden jetzt hinzugefügt werden muss. Diese werden aufgerufen, wenn die Klasse initialisiert:

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
 
7.  Jetzt Sie die Methode, die die App zum Starten benötigen verwendet und Beenden der Sprachaufnahme und übergeben Sie sie an der *LuisManager* Klasse, die Sie in Kürze erstellen. 

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

8.  Hinzufügen einer *Diktat Handler* , wenn die Stimme hält aufgerufen. Diese Methode übergibt den Diktat Text, der die *LuisManager* Klasse.

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
    > Löschen der *Update()* Methode, da diese Klasse nicht verwendet wird.

9.  Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.

    > [!NOTE]
    > An diesem Punkt werden Sie feststellen, einen Fehler angezeigt werden, der *Unity-Editor-Konsole Bereich*. Dies ist, da der Code verweist auf die *LuisManager* Klasse, die im nächsten Kapitel erstellt wird.

## <a name="chapter-6--create-the-luismanager-class"></a>Kapitel 6: Erstellen der LUISManager-Klasse

Es ist Zeit für die Sie erstellen die *LuisManager* -Klasse, die den Anruf an den Azure LUIS-Dienst wird. 

Der Zweck dieser Klasse wird zum Empfangen von des Diktatmodus Texts aus der *MicrophoneManager* Klasse und sendet diese an die *Azure Language Understanding-API* analysiert werden.

Diese Klasse deserialisiert die *JSON* Antwort, und rufen Sie die entsprechenden Methoden der der *Verhalten* Klasse um eine Aktion auszulösen.

Diese Klasse zu erstellen: 

1.  Klicken Sie mit der Doppelklicken auf die **Skripts** Ordner, um ihn zu öffnen. 
2.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen > C# Skript**. Nennen Sie das Skript *LuisManager*. 
3.  Doppelklicken Sie auf das Skript aus, um ihn mit Visual Studio zu öffnen.
4.  Fügen Sie am Anfang der Datei die folgenden Namespaces hinzu:

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  Werden zunächst erstellen Sie drei Klassen **in** der *LuisManager* Klasse (innerhalb derselben Skriptdatei, über die *Start()* Methode), wird das deserialisierte darstellen JSON-Antwort von Azure.

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

6.  Fügen Sie die folgenden Variablen in der *LuisManager* Klasse:
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  Stellen Sie sicher, platzieren Sie Ihr LUIS-Dienstendpunkt im (die müssen Sie von Ihrem LUIS-Portal).

8.  Code für die *Awake()* Methode muss jetzt hinzugefügt werden. Diese Methode wird aufgerufen, wenn die Klasse initialisiert:

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  Jetzt Sie diese Anwendung verwendet wird benötigen, um das Diktieren von empfangenen senden die Methoden der *MicrophoneManager* -Klasse *LUIS*, empfangen und Deserialisieren die Antwort. 
10. Wenn der Wert der Absicht und zugehörigen Entitäten ermittelt wurde, werden sie mit der Instanz von übergeben die *Verhalten* Klasse, um die beabsichtigte Aktion auslösen.

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
 
11. Erstellen Sie eine neue Methode namens *AnalyseResponseElements()* liest, die die resultierende *AnalysedQuery* und ermitteln Sie die Entitäten. Nachdem diese Entitäten ermittelt wurden, werden sie mit der Instanz von übergeben die *Verhalten* Klasse, um in den Aktionen verwenden.

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
    > Löschen der *Start()* und *Update()* Methoden, da diese Klasse nicht verwendet wird.

12. Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.

> [!NOTE]
> An diesem Punkt werden Sie feststellen, mehrere Fehler angezeigt werden, der *Unity-Editor-Konsole Bereich*. Dies ist, da der Code verweist auf die *Verhalten* Klasse, die im nächsten Kapitel erstellt wird.

## <a name="chapter-7--create-the-behaviours-class"></a>Kapitel 7 – Erstellen der Verhalten-Klasse

Die *Verhalten* Klasse löst die Aktionen, die mit den Entitäten, die bereitgestellt werden, indem die *LuisManager* Klasse.

Diese Klasse zu erstellen: 

1.  Klicken Sie mit der Doppelklicken auf die **Skripts** Ordner, um ihn zu öffnen. 
2.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen > C# Skript**. Nennen Sie das Skript *Verhalten*. 
3.  Klicken Sie mit der Doppelklicken auf das Skript aus, um sie zu öffnen *Visual Studio*.
4.  Klicken Sie dann fügen Sie die folgenden Variablen in der *Verhalten* Klasse:

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  Hinzufügen der *Awake()* Methodencode. Diese Methode wird aufgerufen, wenn die Klasse initialisiert:

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  Die folgenden Methoden werden aufgerufen, indem die *LuisManager* Klasse (die Sie zuvor erstellt haben), um zu bestimmen, welches Objekt das Ziel der Abfrage ist, und lösen Sie dann auf die entsprechende Aktion aus.

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
 
7.  Hinzufügen der *FindTarget()* Methode, um zu bestimmen, welche die *"gameobjects"* ist das Ziel des aktuellen Intent. Diese Methode wird standardmäßig das Ziel der *"gameobject"* wird "gazed", wenn keine explizite Ziel in den Entitäten definiert ist.

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
    > Löschen der *Start()* und *Update()* Methoden, da diese Klasse nicht verwendet wird.

8.  Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.

## <a name="chapter-8--create-the-gaze-class"></a>Kapitel 8 – erstellen Sie die Blicke-Klasse

Ist die letzte Klasse, die Sie zum Abschließen dieser app müssen die *bestaunen* Klasse. Diese Klasse aktualisiert den Verweis auf die *"gameobject"* derzeit in der visuellen Fokus des Benutzers.

Zum Erstellen dieser Klasse: 

1.  Klicken Sie mit der Doppelklicken auf die **Skripts** Ordner, um ihn zu öffnen. 
2.  Klicken Sie auf auf die **Skripts** Ordner, klicken Sie auf **erstellen > C# Skript**. Nennen Sie das Skript *bestaunen*. 
3.  Klicken Sie mit der Doppelklicken auf das Skript aus, um sie zu öffnen *Visual Studio*.
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
 
5.  Achten Sie darauf, dass Sie zum Speichern der Änderungen in *Visual Studio* vor der Rückgabe an *Unity*.

## <a name="chapter-9--completing-the-scene-setup"></a>Kapitel 9 – der Szene Einrichtung

1.  Ziehen Sie zum Abschließen der Installation von der Szene jedes Skript, das Sie aus dem Ordner "Scripts", erstellt haben die **Main Camera** -Objekt in der *Hierarchie Bereich*.
2.  Wählen Sie die **Main Camera** und sehen Sie sich die *Inspektor Bereich*, Sie sollten jedes Skript angezeigt, die Sie hinzugefügt haben, und Sie werden feststellen, dass es Parameter für jedes Skript, die noch festgelegt werden.

    ![Das Festlegen der Kamera-Verweis-Ziele.](images/AzureLabs-Lab3-41.png)

3.  Um diese Parameter richtig festzulegen, gehen Sie wie folgt vor:

    1. *MicrophoneManager*:

        - Von der *Hierarchie Bereich*, ziehen Sie die **Diktat Text** -Objekt in der **Diktat Text** im Wertefeld des Parameters.

    2. *Verhalten*, aus der *Hierarchie Bereich*:

        - Ziehen Sie die **Kugel** -Objekt in der *Kugel* Sie im Verweis-Ziel.
        - Ziehen Sie die **Zylinder** in die *Zylinder* Sie im Verweis-Ziel.
        - Ziehen Sie die **Cube** in die *Cube* Sie im Verweis-Ziel.

    3. *Bestaunen*:

        - Legen Sie die *bestaunen maximaler Abstand* zu **300** (sofern es nicht bereits der Fall ist). 

4.  Das Ergebnis sollte wie folgt aussehen:

    ![Anzeigen der Ziele der Kamera-Verweis, jetzt festgelegt werden.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a>Kapitel 10 – Test im Unity-Editor

Testen Sie, dass die Szene Einrichtung ordnungsgemäß implementiert wird.

Stellen Sie Folgendes sicher:

-   Alle Skripts werden angefügt, um die **Main Camera** Objekt. 
-   Alle Felder in der *Kamera Inspector-Hauptbereich* ordnungsgemäß zugewiesen sind.

1.  Drücken Sie die **spielen** Schaltfläche der *Unity-Editor*. Die App muss innerhalb der angeschlossenen, immersive Kopfhörer ausgeführt werden.

2.  Probieren Sie einige äußerungen, z. B. ein:

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > Wenn einen Fehler in der Unity-Konsole zum Ändern der Standard-Audiogeräts angezeigt wird, funktioniert die Szene möglicherweise nicht wie erwartet. Dies ist aufgrund der Art, die das mixed Reality-Portal integrierte Mikrofone für Headsets behandelt, die sie verfügen. Wenn Sie diese Fehlermeldung angezeigt, einfach die Szene zu beenden und neu zu starten und als funktionieren sollte erwartet.

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a>Kapitel 11 – Build herunter, und Laden Sie die UWP-Lösung

Nachdem Sie sichergestellt haben, dass die Anwendung im Unity-Editor ausgeführt wird, können Sie zum Erstellen und bereitstellen.

So erstellen Sie:

1.  Speichern Sie durch Klicken auf die aktuelle Szene **Datei > Speichern**.
2.  Wechseln Sie zu **Datei > Buildeinstellungen**.
3.  Aktivieren Sie das Kontrollkästchen namens **Unity C# Projekte** (nützlich für das Anzeigen und Debuggen von Code aus, nachdem das UWP-Projekt erstellt wurde.
4.  Klicken Sie auf **öffnen Szenen hinzufügen**, klicken Sie dann auf **erstellen**.

    ![Fenster "Einstellungen" erstellen](images/AzureLabs-Lab3-43.png)

4.  Sie werden aufgefordert werden, um den Ordner auszuwählen, in dem Sie die Projektmappe erstellen möchten. 

5.  Erstellen Sie eine *erstellt* Ordner, und erstellen Sie einen anderen Ordner in diesem Ordner mit einem entsprechenden Namen Ihrer Wahl. 
6.  Klicken Sie auf **Ordner auswählen** um den Build an diesem Speicherort zu beginnen.
 
    ![Erstellen Sie Ordner "Builds"](images/AzureLabs-Lab3-44.png)
    ![wählen erstellt Ordner](images/AzureLabs-Lab3-45.png)
 
7.  Nachdem Unity die erstellen (es kann einige Zeit dauern) abgeschlossen ist, sollten sie zu öffnen eine **Datei-Explorer** Fenster am Speicherort des Builds.

So stellen Sie auf dem lokalen Computer bereit:

1.  In *Visual Studio*, öffnen Sie die Projektmappendatei, die in der Erstellung der [vorhergehenden Kapitel](#chapter-10--test-in-the-unity-editor).
2.  In der **Projektmappenplattform**Option **X86**, **lokalen Computer**.
3.  In der **Projektmappenkonfiguration** wählen **Debuggen**.

    > Für die Microsoft HoloLens Umständen ist es einfacher, diese Einstellung auf *Remotecomputer*, sodass Sie nicht auf Ihren Computer angeschlossen sind. Allerdings müssen Sie auch die folgenden Schritte ausführen:
    > - Kennen der **IP-Adresse** von Ihrem HoloLens, die sich in befinden die *Einstellungen > Netzwerk und Internet > Wi-Fi > Erweiterte Optionen*; IPv4 ist die Adresse, die Sie verwenden sollten. 
    > - Stellen Sie sicher **Entwicklermodus** ist **auf**; gefunden in *Einstellungen > Update und Sicherheit > für Entwickler*.

    ![Bereitstellen der App](images/AzureLabs-Lab3-46.png)
 
4.  Wechseln Sie zu der **Menü "Build"** und klicken Sie auf **Projektmappe bereitstellen** zum querladen der Anwendung auf Ihrem Computer.
5.  Ihre App sollte nun in der Liste der installierten apps, die zu startenden bereit angezeigt werden.
6.  Nachdem gestartet, die App fordert Sie zum Autorisieren des Zugriffs auf die _Mikrofon_. Verwenden der *Motion-Controller*, oder *Spracheingabe*, oder die *Tastatur* , drücken die **Ja** Schaltfläche. 

## <a name="chapter-12--improving-your-luis-service"></a>Kapitel 12 – verbessern Ihr LUIS-Dienst

>[!IMPORTANT] 
> In diesem Kapitel ist außerordentlich wichtig, und möglicherweise zu durchlaufen, die auf mehrere Male auf, werden müssen, verhindern die Genauigkeit des LUIS-Diensts zu verbessern: Stellen Sie sicher, diese durchführen.

Um den Grad des Verständnisses zu, die von LUIS bereitgestellte zu verbessern, müssen Sie neue äußerungen erfassen und diese verwenden, um Ihrem LUIS-App erneut zu trainieren.

Beispielsweise können Sie trainiert haben, LUIS, verstehen "Increase" und "Upsizing", aber empfehlenswert Sie nicht Ihrer app Wörter wie "Vergrößern" auch wichtig zu wissen?

Sobald Sie Ihre Anwendung einige Male verwendet haben, werden alle Elemente, die Sie gesagt haben, die von LUIS gesammelt und in das LUIS-PORTAL verfügbar.

1.  Wechseln Sie zu Ihrem portalanwendung dieses [LINK](https://www.luis.ai/home), und anmelden.
2.  Wenn Sie sich mit Ihren MS Credentials angemeldet sind, klicken Sie auf Ihre *Anwendungsnamen*.
3.  Klicken Sie auf die **überprüfen Sie die Endpunkt-äußerungen** Schaltfläche auf der linken Seite der Seite.

    ![Überprüfen Sie die Äußerungen](images/AzureLabs-Lab3-47.png)
 
4.  Ihnen wird eine Liste von Äußerungen angezeigt werden, die von Ihrer mixed Reality-Anwendung zu LUIS gesendet wurden.

    ![Liste von Äußerungen](images/AzureLabs-Lab3-48.png)
 
Sie sehen einige hervorgehobene *Entitäten*. 

Durch jedes markierten Worts mit der Maus, können jede Äußerung überprüfen und bestimmen, welche die Entität wurde erkannt richtig, die Entitäten falsch sind und welche die Entitäten werden ausgelassen.

Im obigen Beispiel ergab, dass das Wort "Spear" als Ziel, daher wurden hervorgehoben hatte es notwendig, korrigieren Sie die Fehler, was durchgeführt wird, indem Sie mit dem Mauszeiger auf das Wort mit der Maus und auf **Remove Label**.

![Überprüfen Sie die äußerungen](images/AzureLabs-Lab3-49.png)
![Bezeichnungsbilds entfernen](images/AzureLabs-Lab3-50.png)
 
5.  Wenn Sie Äußerungen, die völlig falsch sind finden, können Sie sie löschen mit der **löschen** Schaltfläche auf der rechten Seite des Bildschirms.

    ![Löschen Sie die falsche äußerungen](images/AzureLabs-Lab3-51.png)

6.  Oder wenn Sie glauben, dass LUIS korrekt der Äußerung interpretiert hat, können Sie ihn besser verstehen zu überprüfen, indem Sie mit der **hinzufügen, ausgerichtet Absicht** Schaltfläche.

    ![Ausgerichtete Intent hinzufügen](images/AzureLabs-Lab3-52.png)

7.  Nachdem Sie alle angezeigten Äußerungen sortiert haben, versuchen Sie es aus, und Laden Sie die Seite, um festzustellen, ob mehr verfügbar sind.
8.  Es ist sehr wichtig, diesen Vorgang so oft wie möglich, verbessern Ihre Kenntnisse der Anwendung zu wiederholen. 

**Viel Spass!**

## <a name="your-finished-luis-integrated-application"></a>Der fertigen LUIS integrierten Anwendung

Herzlichen Glückwunsch, Sie eine mixed Reality-app, die nutzt Azure Language Understanding Intelligence Service, um zu verstehen, was ein Benutzer angezeigt wird, und Nutzen dieser Informationen erstellt.

![Lab-Ergebnis](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a>Bonus-Übungen

### <a name="exercise-1"></a>Übung 1

Bei der Verwendung dieser Anwendungsprogramms können Sie feststellen, dass wenn Sie sich das Objekt Bodenfläche bestaunen und bitten Sie dessen Farbe zu ändern, wird es dies tun. Können Sie Sie, wie Sie Ihrer Anwendung ändern der Farbe Floor arbeiten?

### <a name="exercise-2"></a>Übung 2

Versuchen Sie es erweitern die LUIS und App-Funktionen, zusätzliche Funktionen für Objekte in der Szene hinzugefügt; als Beispiel erstellen Sie neue Objekte an die Blicke Trefferpunkts, je nachdem was der Benutzer, sagt aus, und klicken Sie dann in der Lage, diese Objekte zusammen mit der aktuellen szeneobjekte, mit den vorhandenen Befehlen verwenden. 
