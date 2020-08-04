---
title: Azure-Cloudtutorials – 5. Integrieren von Azure Bot Service in LUIS
description: Schließen Sie diesen Kurs ab, um zu erfahren, wie Azure Bot Service und das Verstehen natürlicher Sprache innerhalb einer HoloLens 2-Anwendung implementiert werden können.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, HoloLens 2, Azure Bot Service, LUIS, natürliche Sprache, Unterhaltungs-Bot
ms.localizationpriority: high
ms.openlocfilehash: daf97cde1477a84c1776a069ec5b8d1a185b63cc
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376452"
---
# <a name="5-integrating-azure-bot-service"></a>5. Integrieren von Azure Bot Service

In diesem Tutorial erfahren Sie, wie Sie **Azure Bot Service** in der **HoloLens 2**-Demoanwendung verwenden, um Language Understanding (LUIS) hinzuzufügen, damit der Bot Benutzer bei der Suche nach **nachverfolgten Objekten** unterstützen kann. Dies ist ein zweiteiliges Tutorial, in dem Sie im ersten Teil den Bot mit [Bot Composer](https://docs.microsoft.com/composer/introduction) als codefreie Lösung erstellen und einen kurzen Blick auf die Azure-Funktion werfen, die den Bot mit den benötigten Daten versorgt. Im zweiten Teil verwenden Sie **BotManager (Skript)** im Unity-Projekt, um den gehosteten Bot Service zu nutzen.

## <a name="objectives"></a>Ziele

## <a name="part-1"></a>Teil 1:

* Grundlagen zu Azure Bot Service
* Erfahren Sie, wie Sie Bot Composer zum Erstellen eines Bots verwenden
* Erfahren Sie, wie Sie eine Azure-Funktion verwenden, um Daten aus Azure Storage bereitzustellen

## <a name="part-2"></a>Teil 2:

* Erfahren Sie, wie Sie die Szene einrichten, um Azure Bot Service in diesem Projekt zu verwenden
* Erfahren Sie, wie Sie Objekte im Gespräch mit dem Bot festlegen und suchen können

## <a name="understanding-azure-bot-service"></a>Grundlegendes zu Azure Bot Service

**Azure Bot Service** versetzt Entwickler in die Lage, intelligente Bots zu erstellen, die dank **LUIS** eine natürlichsprachige Konversation mit Benutzern führen können. Ein Unterhaltungs-Bot ist eine hervorragende Möglichkeit, die Optionen zu erweitern, wie ein Benutzer mit Ihrer Anwendung interagieren kann. Ein Bot kann als Wissensdatenbank mit einem [QnA Maker fungieren](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs), um eine anspruchsvolle Unterhaltung mit der Leistung von [Language Understanding (Luis)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp) zu führen.

Weitere Informationen zu [Azure Bot Service](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0).

## <a name="part-1---creating-the-bot"></a>Teil 1: Erstellen des Bots

Bevor Sie den Bot in der Unity-Anwendung verwenden können, müssen Sie ihn entwickeln, Daten für ihn bereitstellen und ihn in **Azure** hosten.
Das Ziel des Bots ist es, mitteilen zu können, wie viele *nachverfolgte Objekte* in der Datenbank gespeichert sind, ein *nachverfolgtes Objekt* anhand seines Namens zu finden und dem Benutzer einige grundlegende Informationen zu diesem Objekt mitzuteilen.

### <a name="a-quick-look-into-tracked-objects-azure-function"></a>Ein kurzer Blick auf die Azure-Funktion für nachverfolgte Objekte

Sie sind im Begriff, den Bot zu erstellen. Damit der Bot aber nutzbar wird, müssen Sie ihm eine Ressource zur Verfügung stellen, aus der er Daten pullen kann. Da der *Bot* in der Lage sein soll, die Anzahl der **nachverfolgten Objekte** zu zählen, bestimmte Objekte anhand ihres Namens zu finden und Details mitzuteilen, verwenden Sie eine einfache Azure-Funktion, die Zugriff auf den **Azure Table-Speicher** besitzt.

Laden Sie das Azure Functions-Projekt herunter: [Azure-Funktion für nachverfolgte Objekte](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureFunction_TrackedObjectsService.zip)

Diese Azure-Funktion verfügt über zwei Aktionen: **Count** (Anzahl) und **Find** (Suchen), die über grundlegende *HTTP* *GET*-Aufrufe aufgerufen werden können. Sie können den Code in **Visual Studio** untersuchen.

Weitere Informationen zu [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).

Die Funktion **Count** fragt aus **Table Storage** alle **TrackedObjects** aus der Tabelle ab. Dies ist ein sehr einfacher Vorgang. Die Funktion **Find** nimmt ihrerseits einen Abfrageparameter *name* aus der *GET*-Anforderung an, fragt **Table Storage** nach einem passenden **TrackedObject** ab und gibt dann ein DTO als JSON zurück.

Sie können diese **Azure-Funktion** direkt aus **Visual Studio** bereitstellen.
Hier finden Sie alle Informationen zur [Bereitstellung von Azure-Funktionen](https://docs.microsoft.com/azure/devops/pipelines/targets/azure-functions?view=azure-devops&tabs=dotnet-core%2Cyaml).

Nachdem Sie die Bereitstellung abgeschlossen haben, öffnen Sie im **Azure Portal** die entsprechende Ressource und klicken dann auf **Konfiguration**. Diese Option befindet sich unter dem Abschnitt *Einstellungen*. Dort müssen Sie unter **Anwendungseinstellungen** die *Verbindungszeichenfolge* für den **Azure Storage**-Speicher angeben, in dem die **nachverfolgten Objekte** gespeichert werden. Klicken Sie auf **Neue Anwendungseinstellung**, und verwenden Sie den folgenden Namen: **AzureStorageConnectionString**. Geben Sie als Wert die richtige *Verbindungszeichenfolge* an. Klicken Sie anschließend auf **Speichern**. Die **Azure-Funktion** ist nun bereit, den *Bot* mit Daten zu versorgen, den Sie im nächsten Schritt erstellen.

### <a name="creating-a-conversation-bot"></a>Erstellen eines Unterhaltungs-Bots

Es gibt mehrere Möglichkeiten, einen auf einem Bot Framework basierenden Unterhaltungs-Bot zu entwickeln. In dieser Lektion verwenden Sie die Desktopanwendung [Bot Framework Composer](https://docs.microsoft.com/composer/), bei der es sich um einen visuellen Designer handelt, der optimal für schnelle Entwicklung geeignet ist.

Sie können die neuesten Releases aus dem [GitHub-Repository](https://github.com/microsoft/BotFramework-Composer/releases) herunterladen. Die Anwendung ist für Windows, Mac und Linux verfügbar.

Nachdem **Bot Framework Composer** installiert wurde, starten Sie die Anwendung. Die folgende Benutzeroberfläche sollte angezeigt werden:

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-1.png)

Sie haben ein Bot Composer-Projekt vorbereitet, das die erforderlichen Dialoge und Trigger für dieses Tutorial bereitstellt.
Laden Sie das Projekt herunter: [Bot Framework Composer-Projekt](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/BotComposerProject_TrackedObjectsBot.zip)

Klicken Sie in der oberen Leiste auf **Öffnen**, und wählen Sie das heruntergeladene Bot Framework-Projekt aus, das **TrackedObjectsBot** heißt. Nachdem das Projekt vollständig geladen wurde, sollte das Projekt als bereit angezeigt werden.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-2.png)

Wir konzentrieren uns auf die linke Seite, auf der Sie den **Dialogbereich** sehen können. Hier befindet sich ein Dialog mit dem Namen **TrackedObjectsBot** unter dem mehrere **Trigger** angezeigt werden.

Weitere Informationen zum [Bot Framework-Konzept](https://docs.microsoft.com/composer/concept-dialog).

Diese Trigger führen folgende Aktionen aus:

#### <a name="greeting"></a>Greeting (Begrüßung)

Dies ist der Einstiegspunkt des Chat *Bots*, wenn ein *Benutzer* eine Unterhaltung einleitet.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-3.png)

#### <a name="askingforcount"></a>AskingForCount

Dieser Dialog wird ausgelöst, wenn der *Benutzer* darum bittet, alle **nachverfolgten Objekte** zu zählen.
Dies sind die Auslöserbegriffe:

>* count me all (alle zählen)
>* how many are stored (wie viele sind gespeichert?)

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-4.png)

Dank [LUIS](https://docs.microsoft.com/composer/how-to-use-luis) muss der *Benutzer* die Begriffe nicht genau so verwenden. Der *Benutzer* kann eine natürlichsprachige Unterhaltung führen.

In diesem Dialog kommuniziert der *Bot* auch mit der Azure-Funktion **Count**. Weitere Informationen dazu später.

#### <a name="unknown-intent"></a>Unknown Intent (unbekannte Absicht)

Dieser Dialog wird ausgelöst, wenn die Eingabe des *Benutzer* keine andere Triggerbedingung erfüllt und der Benutzer aufgefordert wird, seine Frage erneut zu stellen.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-5.png)

#### <a name="findentity"></a>FindEntity

Der letzte Dialog ist komplexer mit Verzweigungen und Speichern der Daten im Arbeitsspeicher des *Bots*.
Der Benutzer wird nach dem *Namen* des **nachverfolgten Objekts** gefragt, zu dem er weitere Informationen erhalten möchte, und es wird eine Abfrage der Azure-Funktion **Find** ausgeführt. Die Antwort wird verwendet, um die Unterhaltung fortzusetzen.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section4-step1-6.png)

Wenn das **nachverfolgte Objekt** nicht gefunden wird, wird der Benutzer darüber informiert, und die Unterhaltung wird beendet. Wenn das fragliche **nachverfolgte Objekt** gefunden wird, überprüft der Bot, welche Eigenschaften verfügbar sind, und meldet diese.

### <a name="adapting-the-bot"></a>Anpassen des Bots

Die Trigger **AskingForCount** und **FindEntity** müssen mit dem Back-End kommunizieren, d. h. Sie müssen die richtige URL der **Azure-Funktion** hinzufügen, die Sie zuvor bereitgestellt haben.

Klicken Sie im Dialogbereich auf **AskingForCount**, und suchen Sie die Aktion *HTTP-Anforderung senden*. Dort sehen Sie das Feld **URL**, das Sie in die richtige URL für den Endpunkt der Funktion **Count** ändern müssen.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section5-step1-1.png)

Suchen Sie schließlich nach dem Trigger **FindEntity** und der Aktion *HTTP-Anforderung senden*, und ändern Sie im Feld **URL** die URL in den Endpunkt der **Find**-Funktion.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section5-step1-2.png)

Nachdem alles festgelegt wurde, kann der Bot nun bereitgestellt werden. Da Sie Bot Framework Composer installiert haben, können Sie den Bot direkt von dort aus veröffentlichen.

Weitere Informationen zum [Veröffentlichen eines Bots aus Bot Composer](https://docs.microsoft.com/composer/how-to-publish-bot).

> [!TIP]
> Sie können mit dem Bot experimentieren, indem Sie weitere Triggerbegriffe, neue Antworten oder Unterhaltungsverzweigungen hinzufügen.

## <a name="part-2---putting-everything-together-in-unity"></a>Teil 2: Integrieren der einzelnen Komponenten in Unity

### <a name="preparing-the-scene"></a>Vorbereiten der Szene

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-1.png)

Verschieben Sie von dort das Prefab **ChatBotManager** in die Szenenhierarchie.

Nachdem Sie ChatBotManager der Szene hinzugefügt haben, klicken Sie auf die Komponente **Chat Bot Manager**.
Im Inspektor sehen Sie, dass es ein leeres Feld **Geheimer Schlüssel für Direktverbindung** gibt, das Sie ausfüllen müssen.

> [!TIP]
> Sie können den *geheimen Schlüssel* aus dem Azure-Portal abrufen, indem Sie nach der Ressource vom Typ **Bot Channels Registration** suchen, die Sie im ersten Teil dieses Tutorials erstellt haben.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-2.png)

Nun verbinden Sie das **ChatBotManager**-Objekt mit der **ChatBotController**-Komponente, die an das **ChatBotPanel**-Objekt angefügt ist. Wählen Sie in der Hierarchie das **ChatBotPanel**-Objekt aus. Es wird ein leeres Feld **Chat Bot Manager** angezeigt. Ziehen Sie das **ChatBotManager**-Objekt aus der Hierarchie in das leere Feld **Chat Bot Manager**.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-3.png)

Nun benötigen Sie eine Möglichkeit, **ChatBotPanel** zu öffnen, damit der Benutzer damit interagieren kann. Im Fenster „Szene“ haben Sie möglicherweise bemerkt, dass es eine Seitenschaltfläche *Chat Bot* für das **MainMenu**-Objekt gibt. Diese werden Sie zur Lösung dieses Problems verwenden.

Suchen Sie in der Hierarchie nach **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot**, und suchen Sie im Inspektor nach dem *ButtonConfigHelper*-Skript. Dort wird ein leerer Slot für den **OnClick ()** -Ereignisrückruf angezeigt. Ziehen Sie **ChatBotPanel** mithilfe von Drag & Drop in den Ereignisslot, navigieren Sie in der Dropdownliste zu *GameObject*, und wählen Sie dann im Untermenü *SetActive (bool)* aus, und aktivieren Sie das Kontrollkästchen.

![mr-learning-azure](images/mr-learning-azure/tutorial5-section6-step1-4.png)

Der Chat Bot kann nun über das Hauptmenü gestartet werden. Damit ist die Szene einsatzbereit.

### <a name="putting-the-bot-to-a-test"></a>Testen des Bots

#### <a name="asking-about-the-quantity-of-tracked-objects"></a>Frage zur Anzahl der nachverfolgten Objekte

Zuerst testen Sie den Bot, indem Sie fragen, wie viele **nachverfolgte Objekte** in der Datenbank gespeichert sind.

> [!NOTE]
> Dieses Mal müssen Sie die Anwendung aus HoloLens 2 ausführen, da Dienste wie *Text-zu-Sprache* möglicherweise nicht auf Ihrem System verfügbar sind.

Führen Sie die Anwendung auf HoloLens 2 aus, und klicken Sie neben dem Hauptmenü auf die Schaltfläche *Chat Bot*.
Der Bot begrüßt Sie. Fragen Sie nun **how many objects do we have?** (wie viele Objekte sind vorhanden?)
Der Bot sollten Ihnen die Anzahl mitteilen und die Unterhaltung beenden.

#### <a name="asking-about-a-tracked-object"></a>Frage zu einem nachverfolgten Objekt

Führen Sie die Anwendung nun erneut aus, und fordern Sie den Bot dieses Mal wie folgt auf: **find me a tracked object** (nachverfolgtes Objekt suchen). Der Bot fragt Sie nach dem Namen. Darauf sollten Sie mit „car“ (Auto) oder dem Namen eines anderen *nachverfolgten Objekts* antworten, von dem Sie wissen, dass es in der Datenbank vorhanden ist. Der Bot teilt Ihnen Details wie eine Beschreibung mit und informiert sie, ob ein räumlicher Anker zugewiesen ist.

> [!TIP]
> Testen Sie den Bot weiter, indem Sie nach einem **nachverfolgten Objekt** fragen, das nicht vorhanden ist. Beachten Sie, was der Bot antwortet.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, wie Azure Bot Framework verwendet werden kann, um über eine Unterhaltung in natürlicher Sprache mit der Anwendung zu interagieren. Sie haben gelernt, wie Sie Ihren eigenen Bot entwickeln und welche Komponenten für seine Ausführung erforderlich sind.

## <a name="conclusion"></a>Schlussbemerkung

Im Rahmen dieser Tutorialreihe haben Sie erfahren, wie **Azure Cloud Services** neue und interessante Features für Ihre Anwendung bereitstellen kann.
Sie können jetzt mit **Azure Storage** Daten und Bilder in der Cloud speichern, mit **Azure Custom Vision** Bilder zuordnen und ein Modell trainieren, mit **Azure Spatial Anchors** Objekte in einen lokalen Kontext bringen und mit **Azure Bot Framework powered by LUIS** einen Unterhaltungs-Bot für ein neues und natürliches Interaktionsmuster implementieren.
