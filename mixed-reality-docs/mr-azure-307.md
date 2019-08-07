---
title: Mr und Azure 307-Machine Learning
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie Azure Machine Learning Studio in einer Mixed Reality-Anwendung implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, Tutorial, API, Machine Learning, ml, Machine Learning Studio, hololens, immersive, VR
ms.openlocfilehash: 89d9758dedb6a2389644dda887bfadf5b28f6dd2
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694544"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.

<br>

# <a name="mr-and-azure-307-machine-learning"></a>Mr und Azure 307: Machine Learning

![Endgültiges Produkt-Start](images/AzureLabs-Lab7-0.png)

In diesem Kurs erfahren Sie, wie Sie mithilfe von Azure Machine Learning Studio Machine Learning (ml)-Funktionen zu einer gemischten Reality-Anwendung hinzufügen.

*Azure Machine Learning Studio* ist ein Microsoft-Dienst, der Entwicklern eine große Anzahl von Machine Learning-Algorithmen bereitstellt, die Ihnen bei der Eingabe, Ausgabe, Vorbereitung und Visualisierung von Daten helfen können. Aus diesen Komponenten ist es dann möglich, ein Predictive Analytics Experiment zu entwickeln, zu durchlaufen und es zum Trainieren des Modells zu verwenden. Im Anschluss an die Schulung können Sie das Modell in der Azure-Cloud funktionstüchtig machen, damit es neue Daten bewerten kann. Weitere Informationen finden Sie auf der [Seite Azure Machine Learning Studio](https://azure.microsoft.com/en-au/services/machine-learning-studio/).

Nachdem Sie diesen Kurs abgeschlossen haben, verfügen Sie über eine gemischte Reality-Headset-Anwendung, die die folgenden Aktionen durchführt:

1.  Stellen Sie eine Tabelle mit Umsatzdaten für das *Azure Machine Learning Studio* Portal bereit, und entwerfen Sie einen Algorithmus, um zukünftige Umsätze beliebter Artikel vorherzusagen.
2.  Erstellen Sie ein **Unity-Projekt**, das Vorhersagedaten vom ml-Dienst empfangen und interpretieren kann.
3.  Zeigen Sie die prädikationsdaten visuell im **Unity-Projekt**an, indem Sie die beliebtesten Verkaufs Elemente in einem Regal bereitstellen.

In Ihrer Anwendung liegt es an Ihnen, wie Sie die Ergebnisse in Ihren Entwurf integrieren. In diesem Kurs erfahren Sie, wie Sie einen Azure-Dienst in Ihr Unity-Projekt integrieren. Es ist Ihre Aufgabe, das wissen, das Sie aus diesem Kursgewinnen, zu nutzen, um ihre gemischte Reality-Anwendung zu verbessern.

Dieser Kurs ist ein eigenständiges Tutorial, das sich nicht direkt mit anderen Mixed Reality-Labs befasst.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> Mr und Azure 307: Machine Learning</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Dieser Kurs konzentriert sich in erster Linie auf Windows Mixed Reality immersive (VR)-Headsets, aber Sie können auch das, was Sie in diesem Kurs lernen, auf Microsoft hololens anwenden. Wenn Sie den Kurs befolgen, finden Sie Hinweise zu allen Änderungen, die Sie möglicherweise zur Unterstützung von hololens verwenden müssen. Wenn Sie hololens verwenden, bemerken Sie möglicherweise bei der sprach Erfassung einen Echo.

## <a name="prerequisites"></a>Vorraussetzungen

> [!NOTE]
> Dieses Tutorial richtet sich an Entwickler, die über grundlegende Kenntnisse in C#Unity und verfügen. Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Mai 2018). Sie können die neueste Software verwenden, die im [Artikel Installieren der Tools](install-the-tools.md)aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt sind.

Für diesen Kurs empfehlen wir die folgende Hardware und Software:

- Einen Entwicklungs-PC, der [mit der Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for Immersive (VR)-Headset-Entwicklung kompatibel ist
- [Windows 10 Fall Creators Update (oder höher) mit aktiviertem Entwicklermodus](install-the-tools.md#installation-checklist)
- [Das neueste Windows 10 SDK](install-the-tools.md#installation-checklist)
- [Unity 2017,4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Ein [Windows Mixed Reality-Headset (VR)](immersive-headset-hardware-details.md) oder [Microsoft hololens](hololens-hardware-details.md) mit aktiviertem Entwicklermodus
- Internet Zugriff für Azure-Setup und ml-Datenabruf

## <a name="before-you-start"></a>Bevor Sie beginnen

Um Probleme zu vermeiden, die beim Erstellen dieses Projekts auftreten, wird dringend empfohlen, dass Sie das in diesem Tutorial erwähnte Projekt in einem Stamm Ordner oder in einem Ordner mit einem Stamm Ordner erstellen (lange Ordner Pfade können zur Buildzeit Probleme verursachen). 

## <a name="chapter-1---azure-storage-account-setup"></a>Kapitel 1: Einrichten des Azure Storage Kontos

Um die Azure Translator-API zu verwenden, müssen Sie eine Instanz des-Dienstanbieter konfigurieren, die für die Anwendung verfügbar gemacht wird.
1.  Melden Sie sich beim [Azure-Portal](https://portal.azure.com)an.

    > [!NOTE]
    > Wenn Sie noch nicht über ein Azure-Konto verfügen, müssen Sie eines erstellen. Wenn Sie dieses Tutorial in einer Classroom-oder Lab-Situation befolgen, bitten Sie Ihren Dozenten oder einen der Proctors, Hilfe beim Einrichten Ihres neuen Kontos zu erhalten.

2.  Wenn Sie angemeldet sind, klicken Sie im linken Menü auf **Speicher Konten** .

    ![Einrichten des Azure Storage Kontos](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > Das Wort **New** wurde möglicherweise durch **Create a Resource**in neueren Portalen ersetzt.

3.  Klicken Sie auf der Registerkarte **Speicher Konten** auf **Hinzufügen**.

    ![Einrichten des Azure Storage Kontos](images/AzureLabs-Lab7-2.png)

4.  Im Bereich **Speicherkonto erstellen** :

    1.  Fügen Sie einen **Namen** für Ihr Konto ein. Beachten Sie, dass dieses Feld nur Zahlen und Kleinbuchstaben akzeptiert.
    2.  Wählen Sie **unter Bereitstellungs Modell** die Option **Resource Manager**aus.
    3.  Wählen Sie unter **Kontoart**die Option **Speicher (universell, Version v1)** aus.
    4.  Wählen Sie für **Leistung**die Option **Standard**aus.
    5.  Wählen Sie für die **Replikation** den **georedundanten Speicher mit Lesezugriff (RA-GRS)** aus.
    6.  Lassen Sie die Option " **sichere Übertragung erforderlich** " **deaktiviert**.
    7.  Wählen Sie ein **Abonnement**aus.
    4. Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** . Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Labs) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).
    
    5.  Bestimmen Sie den **Speicherort** für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen). Der Speicherort wäre idealerweise in der Region, in der die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.

5.  Außerdem müssen Sie bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.

    ![Einrichten des Azure Storage Kontos](images/AzureLabs-Lab7-3.png)

6.  Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.

7.  Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Einrichten des Azure Storage Kontos](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a>Kapitel 2: der Azure Machine Learning Studio

Um das *Azure Machine Learning*verwenden zu können, müssen Sie eine Instanz des Machine Learning Dienstanbieter konfigurieren, die für die Anwendung verfügbar gemacht wird.

1.  Klicken Sie im Azure-Portal in der oberen linken Ecke auf " **neu** ", und suchen Sie nach **Machine Learning Studio Arbeitsbereich**, und drücken **Sie die Eingabe**Taste.

    ![Der Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  Auf der neuen Seite wird eine Beschreibung des **Machine Learning Studio Arbeits** Bereichs Dienstanbieter bereitgestellt. Klicken Sie unten links in dieser Eingabeaufforderung auf die Schaltfläche **Erstellen** , um eine Verknüpfung mit diesem Dienst zu erstellen.

3.  Nachdem Sie auf **Erstellen**geklickt haben, wird ein Panel angezeigt, in dem Sie einige Details über den neuen **Machine Learning Studio Dienst**angeben müssen:

    1.  Fügen Sie den gewünschten **Arbeitsbereichs Namen** für diese Dienst Instanz ein.

    2.  Wählen Sie ein **Abonnement**aus.

    3. Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** . Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Labs) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern. 

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie [im Artikel Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Bestimmen Sie den **Speicherort** für Ihre Ressourcengruppe (wenn Sie eine neue Ressourcengruppe erstellen). Der Speicherort wäre idealerweise in der Region, in der die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar. Sie sollten die gleiche Ressourcengruppe verwenden, die Sie zum Erstellen des Azure Storage im vorherigen Kapitel verwendet haben.

    5.  Klicken Sie im Bereich **Speicherkonto** auf **vorhandene verwenden**, klicken Sie dann auf das Dropdown Menü, und klicken Sie dann auf das **Speicherkonto** , das Sie im letzten Kapitel erstellt haben.

    6.  Wählen Sie im Dropdown Menü den entsprechenden Tarif des **Arbeits** Bereichs für Sie aus.

    7.  Klicken Sie im Abschnitt **Webdienst Plan** auf neu **Erstellen** **, und** fügen Sie dann einen Namen für die Datei in das Textfeld ein.

    8.  Wählen Sie im Abschnitt **Tarif des Webdienst** Tarifs den Tarif Ihrer Wahl aus. Eine Entwicklungs Test Ebene mit dem Namen **devtest Standard** sollte Ihnen kostenlos zur Verfügung stehen.

    9.  Außerdem müssen Sie bestätigen, dass Sie die auf diesen Dienst angewendeten Geschäftsbedingungen verstanden haben.

    10. Klicken Sie auf **Erstellen**.

        ![Der Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.

5.  Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Der Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  Klicken Sie auf die Benachrichtigung, um die neue Dienst Instanz zu untersuchen.

    ![Der Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen.

8.  Klicken Sie auf der angezeigten Seite im Abschnitt **zusätzliche Links** auf **Machine Learning Studio starten**, um den Browser zum **Machine Learning Studio** Portal zu leiten.

    ![Der Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  Verwenden Sie die Schaltfläche **Anmelden** oben rechts oder in der Mitte, um sich bei Ihrem Machine Learning Studio anzumelden.

    ![Der Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a>Kapitel 3: der Machine Learning Studio: DataSet-Setup

Eine der Möglichkeiten Machine Learning Algorithmen besteht darin, vorhandene Daten zu analysieren und dann basierend auf dem vorhandenen DataSet zu versuchen, zukünftige Ergebnisse vorherzusagen. Dies bedeutet im Allgemeinen, dass die vorhandenen Daten, umso besser der Algorithmus ist, um zukünftige Ergebnisse vorherzusagen.

Sie erhalten für diesen Kurs eine Beispiel Tabelle mit dem Namen [productstablecsv und können hier heruntergeladen werden](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).

> [!IMPORTANT]
> Die obige ZIP-Datei enthält sowohl **productstablecsv** als auch das **. unitypackage**, das Sie in [Kapitel 6](#chapter-6---importing-the-mlproducts-unity-package)benötigen. Dieses Paket wird auch in diesem Kapitel bereitgestellt, jedoch getrennt von der CSV-Datei.

Dieses Beispiel DataSet enthält einen Datensatz der am besten verkauften Objekte für jede Stunde des Jahres 2017.
        
![Der Machine Learning Studio: DataSet-Setup](images/AzureLabs-Lab7-11.png)

Beispielsweise war am Tag 1 von 2017 bei 1 Uhr (Stunde 13) das am besten verkaufte Element Salt und Pepper.

Diese Beispiel Tabelle enthält 9998 Einträge.

1.  Wechseln Sie zurück zum **Machine Learning Studio** -Portal, und fügen Sie diese Tabelle als **DataSet** für Ihr ml hinzu. Klicken Sie hierzu auf die Schaltfläche **+ neu** in der unteren linken Ecke des Bildschirms.

    ![Der Machine Learning Studio: DataSet-Setup](images/AzureLabs-Lab7-12.png)

2.  Ein Abschnitt wird von unten nach oben angezeigt, und darin befindet sich auf der linken Seite ein Navigations Panel. Klicken Sie dann auf das **DataSet**, und klicken Sie dann auf die **lokale Datei**.

    ![Der Machine Learning Studio: DataSet-Setup](images/AzureLabs-Lab7-13.png)

3.  Laden Sie das neue **DataSet** hoch, indem Sie die folgenden Schritte ausführen:

    1. Das Fenster hochladen wird angezeigt, in dem Sie die Festplatte nach dem neuen DataSet **Durchsuchen** können.

        ![Der Machine Learning Studio: DataSet-Setup](images/AzureLabs-Lab7-14.png)

    2.  Wenn Sie diese Option ausgewählt haben und wieder im Fenster Upload angezeigt werden, lassen Sie das Kontrollkästchen deaktiviert.

    3.  Geben Sie im Textfeld unten den Namen **productstablecsv. CSV** als Namen für das Dataset ein (wird jedoch automatisch hinzugefügt).

    4.  Wählen Sie im Dropdown Menü für **Typ**die Option **generische CSV-Datei mit einem Header (. CSV)** aus.

    5.  Drücken Sie unten rechts im Uploadfenster den Tick, und das **DataSet** wird hochgeladen.

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a>Kapitel 4: der Machine Learning Studio: Das Experiment

Bevor Sie Ihr Machine Learning-System erstellen können, müssen Sie ein Experiment erstellen, um Ihre Theorie zu Ihren Daten zu überprüfen. Mit den Ergebnissen wissen Sie, ob Sie mehr Daten benötigen, oder ob es keine Korrelation zwischen den Daten und einem möglichen Ergebnis gibt.

So beginnen Sie mit dem Erstellen eines Experiments:

1.  Klicken Sie erneut auf die Schaltfläche **+ neu** unten links auf der Seite, und klicken Sie dann auf **Experiment** > **leeres Experiment**.

    ![Der Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-15.png)

2.  Eine neue Seite wird mit einem leeren Experiment angezeigt:

3.  Erweitern Sie im linken Bereich **gespeicherte Datasets** > **meine Datasets** , und ziehen Sie **productstablecsv** auf den **Experiment**Bereich.

    ![Der Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-16.png)

4.  Erweitern Sie im Panel auf der linken Seite die Option **Data Transformation** > **Sample und Split**. Ziehen Sie dann das Element **Split Data** in in den **Experiment**Bereich. Mit dem Split Data-Element wird das Dataset in zwei Teile aufgeteilt. Ein Teil, der zum Trainieren des Machine Learning-Algorithmus verwendet wird. Der zweite Teil wird verwendet, um die Genauigkeit des generierten Algorithmus auszuwerten.

    ![Der Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-17.png)

5.  Im rechten Bereich (während das geteilte Datenelement auf der Canvas ausgewählt ist), bearbeiten Sie den **Bruchteil der Zeilen im ersten Ausgabe DataSet** in **0,7**. Dadurch werden die Daten in zwei Teile aufgeteilt, der erste Teil ist 70% der Daten und der zweite Teil die verbleibenden 30%. Vergewissern Sie sich, dass die Daten nach dem Zufallsprinzip aufgeteilt werden.

    ![Der Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-18.png)

6.  Ziehen Sie eine Verbindung von der Basis des Elements **productstablecsv** in der Canvas an den oberen Rand des Elements Split Data. Dadurch werden die Elemente verbunden, und die Ausgabe des Datasets **productstablecsv** (die Daten) wird an die unterteilte Dateneingabe gesendet.  

    ![Der Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-19.png)

7.  Erweitern Sie im Bereich **Experimente** auf der linken Seite **Machine Learning** > **trainieren**. Ziehen Sie das Element **Train Model** in den Experiment Bereich. Der Canvas sollte wie unten dargestellt aussehen.

    ![Der Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-20.png)

8.  Ziehen Sie ***unten links*** im Element " **Split Data** " eine Verbindung mit der **rechten oberen** Ecke des Moduls " **Train Model** ". Die erste 70%-Aufteilung aus dem DataSet wird vom Train-Modell zum Trainieren des Algorithmus verwendet.

    ![Der Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-21.png)

9.  Wählen Sie das **Modellelement trainieren** im Zeichenbereich aus, und klicken Sie im **Eigenschaften** Panel (auf der rechten Seite Ihres Browserfensters) auf die Schaltfläche **Launch Column Selector** .

10. Geben Sie im Textfeld **Product** ein, und drücken Sie dann die **Eingabe**Taste. *Product* wird als Spalte zum Trainieren von Vorhersagen festgelegt. Klicken Sie anschließend auf den **Tick** in der unteren rechten Ecke, um das Auswahl Dialogfeld zu schließen.

    ![Der Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-22.png)

11. Sie trainieren einen **MultiClass Logistic Regression** -Algorithmus, um das am häufigsten verkaufte **Produkt** basierend auf der Tageszeit und dem Datum vorherzusagen. Es geht über den Rahmen dieses Dokuments hinaus, die Details der verschiedenen Algorithmen zu erläutern, die von der Azure Machine Learning Studio bereitgestellt werden. Sie können jedoch weitere Informationen aus dem [Machine Learning algorithmusspickzettel](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)

12. Erweitern Sie im Bereich Experiment Elemente auf der linken Seite **Machine Learning** > **Modell** > **Klassifizierung**initialisieren, und ziehen Sie das Element für die **mehr klassige logistische Regression** in den Experiment Bereich.

13. Verbinden Sie die Ausgabe vom Ende der **mehr klassigen logistischen Regression**mit der Eingabe oben links des **Train Model** -Elements.

    ![Der Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-23.png)

14. Erweitern Sie in der Liste der Experiment Elemente im Panel auf der linken Seite **Machine Learning** > **Score**, und ziehen Sie das **Score Model** -Element auf den Zeichenbereich.

15. Verbinden Sie die Ausgabe vom unteren Rand des Trainings **Modells**mit der oberen linken Eingabe des Bewertungs **Modells**.

16. Verbinden Sie die untere rechte Ausgabe von **Split Data**mit der oberen rechten Eingabe des **Score Model** -Elements.

    ![Der Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-24.png)

17. Erweitern Sie in der Liste der **Experiment** Elemente im Panel auf der linken Seite **Machine Learning** > **Auswerten**, und ziehen Sie das **Modellelement auswerten** auf den Zeichenbereich.

18. Verbinden Sie die Ausgabe des Bewertungs **Modells** mit der oberen linken Eingabe des **evaluatormodells**.

    ![Der Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-25.png)

19. Sie haben ihr erstes Machine Learning Experiment erstellt. Sie können das Experiment jetzt speichern und ausführen. Klicken Sie im Menü unten auf der Seite auf die Schaltfläche **Speichern** , um das Experiment zu speichern, und klicken Sie dann auf **Ausführen** , um das Experiment zu starten.

    ![Der Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-26.png)

20. Sie können den **Status** des Experiments in der oberen rechten Ecke der Canvas sehen. Warten Sie einen Moment, bis das Experiment abgeschlossen ist.

    > Wenn Sie über ein großes Dataset (Real World) verfügen, ist es wahrscheinlich, dass das Experiment mehrere Stunden dauern kann.

    ![Der Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-27.png)

21. Klicken Sie mit der rechten Maustaste auf das **Modellelement auswerten** im Zeichenbereich, und zeigen Sie im Kontextmenü auf **Auswertungs Ergebnisse**, und wählen Sie dann **visualisieren**aus.

    ![Der Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-28.png)

22. Die Auswertungs Ergebnisse werden angezeigt, die die vorhergesagten Ergebnisse im Vergleich zu den tatsächlichen Ergebnissen anzeigen. Dabei werden die 30% des ursprünglichen Datasets, das zuvor geteilt wurde, zum Auswerten des Modells verwendet. Sie sehen, dass die Ergebnisse nicht groß sind. Idealerweise haben Sie in jeder Zeile die höchste Zahl, die das markierte Element in den Spalten ist.

    ![Der Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-29.png)

23. Schließen Sie die **Ergebnisse**.

24. Um das neu trainierte Machine Learning Modell zu verwenden, müssen Sie es als **Webdienst**verfügbar machen. Klicken Sie hierzu im Menü unten auf der Seite auf das Menü Element **Set Up Web Service** , und klicken Sie auf **Predictive Web Service**.

    ![Der Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-30.png)

25. Es wird eine neue Registerkarte erstellt, und das Train-Modell wird zusammengeführt, um den neuen Webdienst zu erstellen. 

26. Klicken Sie im Menü unten auf der Seite auf **Speichern**, und klicken Sie dann auf **Ausführen**. Der Status wird in der oberen rechten Ecke des Experiment Bereichs angezeigt.

    ![Der Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-31.png)

27. Nachdem die Ausführung abgeschlossen ist, wird unten auf der Seite die Schaltfläche " **Webdienst** bereitstellen" angezeigt. Sie können den Webdienst bereitstellen. Klicken Sie im Menü unten auf der Seite auf **Webdienst** bereitstellen (klassisch).

    ![Der Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-32.png)

    > In Ihrem Browser werden Sie möglicherweise aufgefordert, ein Popup zuzulassen, das Sie **zulassen**sollten. Sie müssen jedoch möglicherweise erneut den **Webdienst** bereitstellen verwenden, wenn die Seite bereitstellen nicht angezeigt wird. 

28. Nachdem das Experiment erstellt wurde, werden Sie zu einer Dashboardseite umgeleitet, auf der Sie Ihren **API-Schlüssel** anzeigen können. Kopieren Sie die Datei in einen Editor für den Moment. Sie benötigen Sie in Ihrem Code sehr bald. Nachdem Sie Ihren API-Schlüssel notiert haben, klicken Sie auf die Schaltfläche " **Anforderung/Antwort** " im Abschnitt " **Standard Endpunkt** " unterhalb des Schlüssels.

    ![Der Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > Wenn Sie auf dieser Seite auf "testen" klicken, können Sie Eingabedaten eingeben und die Ausgabe anzeigen. Geben Sie den **Tag** und die **Stunde**ein. Lassen Sie den **Produkt** Eintrag leer. Klicken Sie dann auf die Schaltfläche **bestätigen** . Die Ausgabe am unteren Rand der Seite zeigt den JSON-Code, der die Wahrscheinlichkeit für die einzelnen Produkte darstellt.

29. Es wird eine neue Webseite geöffnet, auf der die Anweisungen und einige Beispiele zur Anforderungs Struktur angezeigt werden, die für die Machine Learning Studio erforderlich ist. Kopieren Sie den auf dieser Seite angezeigten **Anforderungs-URI** in den Editor.

    ![Der Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-34.png)

Sie haben jetzt ein Machine Learning-System erstellt, das das wahrscheinlichste Produkt bereitstellt, das auf der Grundlage von Verlaufs Daten zu verkaufen ist, die mit der Tageszeit und dem Tag des Jahrs korreliert sind.

Um den Webdienst aufzurufen, benötigen Sie die URL für den Dienst Endpunkt und einen API-Schlüssel für den Dienst. Klicken Sie im oberen Menü auf die Registerkarte **Verbrauch** .

Auf der Seite " **Verbrauchs** Informationen" werden die Informationen angezeigt, die Sie benötigen, um den Webdienst aus Ihrem Code aufzurufen. Erstellen Sie eine Kopie des **Primärschlüssels** und der **Anforderungs Antwort-** URL. Sie benötigen diese im nächsten Kapitel.

## <a name="chapter-5---setting-up-the-unity-project"></a>Kapitel 5: Einrichten des Unity-Projekts

Richten Sie Ihr immersives Headset mit gemischter Realität ein und testen Sie es.

> [!NOTE]
>  Für diesen Kurs benötigen Sie **keine** Bewegungs Controller. Wenn Sie Unterstützung beim Einrichten des immersiven Headsets benötigen, klicken Sie [hier](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Öffnen Sie **Unity** , und erstellen Sie ein neues Unity-Projekt namens **\_"machinelearning".** Stellen Sie sicher, dass Projekttyp auf **3D**festgelegt ist.

2.  Wenn Unity geöffnet ist, sollten Sie überprüfen, dass der Standard **Skript-Editor** auf **Visual Studio**festgelegt ist. Wechseln Sie zu**Einstellungen** **Bearbeiten** > , und navigieren Sie dann im neuen Fenster zu **externe Tools**. Ändern Sie den **Editor für externe Skripts** in **Visual Studio 2017**. Schließen Sie das Fenster " **Einstellungen** ".

3.  Navigieren Sie als nächstes zu > dateibuildeinstellungen, und schalten Sie die Plattform auf **universelle Windows-Plattform**, indem Sie auf die Schaltfläche ***Plattform wechseln*** klicken.

4.  Stellen Sie außerdem Folgendes sicher:

    1.  Das **Zielgerät** ist auf **ein beliebiges Gerät**festgelegt.

        > Legen Sie für Microsoft hololens das **Zielgerät** auf *hololens*fest.

    2.  Der Buildtyp ist auf **D3D**festgelegt.

    3.  **SDK** ist auf **zuletzt installiert**festgelegt.

    4.  Die **Visual Studio-Version** ist auf die **neueste installierte**Version festgelegt.

    5.  **Build und Run** sind auf **lokaler Computer**festgelegt.

    6.  Machen Sie sich keine Gedanken über das Einrichten von **Szenen** , da diese später bereitgestellt werden.

    7.  Die restlichen Einstellungen sollten vorerst als Standard belassen werden.

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab7-35.png)

5.  Klicken Sie im Fenster Buildeinstellungen auf die Schaltfläche **Player Einstellungen** . Dadurch wird der entsprechende Bereich in dem Bereich geöffnet, in dem sich der **Inspektor** befindet. 

6. In diesem Bereich müssen einige Einstellungen überprüft werden:

    1.  Auf der Registerkarte **andere Einstellungen** :

        1.  **Skript** Erstellung Die **Lauf Zeit Version** sollte **experimentell** sein (.NET 4,6-Entsprechung).

        2. **Skript** -Back-End sollte ***.net*** sein

        3. **API-Kompatibilitäts Grad** sollte **.NET 4,6** lauten

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab7-36.png)

    2.  Überprüfen Sie auf der Registerkarte **Veröffentlichungs Einstellungen** unter **Funktionen**Folgendes:

        - **Internet Client deklarieren**

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab7-37.png)

    3.  Weiter unten im Bereich in den **XR-Einstellungen** (siehe **Veröffentlichungs Einstellungen**), **unterstützt Tick Virtual Reality**, wird sichergestellt, dass das **Windows Mixed Reality SDK** hinzugefügt wurde.

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab7-38.png)

    

6.  Zurück in Buildeinstellungen: *Unity C#*  -Projekte sind nicht mehr abgeblendet. Aktivieren Sie das Kontrollkästchen neben this. 

7.  Schließen Sie das Fenster mit den Buildeinstellungen.

8.  Speichern Sie Ihr Projekt (**Datei > Projekt speichern**).

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a>Kapitel 6: Importieren des Unity-Pakets "mlproducts"

Für diesen Kurs müssen Sie ein Unity-Ressourcenpaket mit dem Namen " [**Azure-Mr-307. unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage)" herunterladen. Dieses Paket ist vollständig in einer Szene, bei der alle Objekte in dieser vorerstellt wurden, sodass Sie sich darauf konzentrieren können, alles zu funktionieren. Das **shelbkeeper** -Skript wird bereitgestellt, enthält jedoch nur die öffentlichen Variablen für den Zweck der Struktur der Szenen Einrichtung. Sie müssen alle anderen Abschnitte durchführen. 

So importieren Sie das Paket:

1.  Klicken Sie oben auf dem Bildschirm mit dem Unity-Dashboard auf **Assets** , und klicken Sie dann auf **Import Package, Custom Package**.

    ![Importieren des Unity-Pakets mlproducts](images/AzureLabs-Lab7-39.png)

2.  Wählen Sie mit der Dateiauswahl das Paket **Azure-Mr-307. unitypackage** aus, und klicken Sie auf **Öffnen**.

3.  Eine Liste der Komponenten für dieses Asset wird angezeigt. Bestätigen Sie den Import, indem Sie auf **importieren**klicken.

    ![Importieren des Unity-Pakets mlproducts](images/AzureLabs-Lab7-40.png)

4.  Nachdem der Import abgeschlossen ist, werden Sie feststellen, dass einige neue Ordner im Unity- **Projekt Panel**angezeigt werden. Dabei handelt es sich um die 3D-Modelle und die jeweiligen Materialien, die Teil der vorgefertigten Szene sind, an der Sie arbeiten werden. In diesem Kurs schreiben Sie den Großteil des Codes.

    ![Importieren des Unity-Pakets mlproducts](images/AzureLabs-Lab7-41.png)

5.  Klicken Sie im **Projekt Panel** Ordner auf den Ordner **Szenen** , und doppelklicken Sie auf die Szene in ( **MR_MachineLearningScene**). Die Szene wird geöffnet (siehe Abbildung unten). Wenn die roten Diamanten fehlen, klicken Sie einfach auf die **Gizmos** -Schaltfläche oben rechts im **Spiel**Bereich.

    ![Importieren des Unity-Pakets mlproducts](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a>Kapitel 7: Überprüfen der DLLs in Unity

Um die Verwendung von JSON-Bibliotheken (die für die Serialisierung und Deserialisierung verwendet wird) zu nutzen, wurde eine newtonsoft-dll mit dem Paket implementiert, das Sie in integriert haben. Die Bibliothek sollte über die richtige Konfiguration verfügen, obwohl Sie überprüft werden muss (insbesondere, wenn Probleme mit dem Code nicht funktionieren). 

Gehen Sie hierzu wie folgt vor:

-  Klicken Sie mit der linken Maustaste auf die newtonsoft-Datei im Ordner Plug-ins, und sehen Sie sich den Bereich **Inspector**an. Stellen Sie sicher, dass **jede Plattform** getickt ist. Wechseln Sie zur **Registerkarte UWP** , und stellen Sie sicher, dass die Option **nicht verarbeiten nicht** angezeigt wird.

    ![Importieren der DLLs in Unity](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a>Kapitel 8: Erstellen der Shelf Keeper-Klasse

Die **shelskeeper** -Klasse hostet Methoden, die die Benutzeroberfläche und die in der Szene erzeugten Produkte steuern.

Als Teil des importierten Pakets erhalten Sie diese Klasse, obwohl sie unvollständig ist. Nun ist es an der Zeit, diese Klasse abzuschließen:

1.  Doppelklicken Sie auf das **shelfkeeper** -Skript im Ordner " **Scripts** ", um es mit **Visual Studio 2017**zu öffnen.

2.  Ersetzen Sie den gesamten Code, der im Skript vorhanden ist, durch den folgenden Code, der das Datum und die Uhrzeit festlegt und eine-Methode zum Anzeigen eines Produkts aufweist.

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  Stellen Sie sicher, dass Sie die Änderungen in **Visual Studio** speichern, bevor Sie zu **Unity**zurückkehren.

4.  Überprüfen Sie im Unity-Editor, ob die **shelbkeeper** -Klasse wie folgt aussieht:

    ![Erstellen der Shelf Keeper-Klasse](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > Wenn das Skript nicht über die Verweis Ziele ( *z. &* # 160; & # 160; & # 160; & # 160; & # 160; & # 160; & # 160; & # 160; a. Weitere Erläuterungen finden Sie unten:
    > 
    > 1.  Öffnen Sie das Element für das Erzeugen von **Punkten** innerhalb des **shelfkeeper** -Komponenten Skripts, indem Sie darauf klicken. Es wird ein unter Abschnitt mit dem Namen **size**angezeigt, der die Größe des Arrays angibt. Geben Sie **3** in das Textfeld neben **Größe** ein, und drücken **Sie die Eingabe**Taste, und es werden drei Slots unterhalb von erstellt.
    > 2. Erweitern Sie in der **Hierarchie** das **Zeitanzeige** Objekt (indem Sie mit der linken Maustaste auf den Pfeil daneben klicken). Klicken Sie dann in der **Hierarchie**auf die ***Hauptkamera*** , damit der **Inspektor** seine Informationen anzeigt.
    > 3. Wählen Sie im **Hierarchie Panel**die **Hauptkamera** aus. Ziehen Sie **die Datums** -und **Uhrzeit** Objekte aus dem Bereich **Hierarchie** in die **Text** Slots **Date Text** und Time innerhalb des **Inspektors** der **Hauptkamera** der **shelfkeeper** -Komponente.
    > 4. Ziehen Sie die-erstellungspunkte aus dem **Hierarchie Panel** (unterhalb des *Shelf* -Objekts) auf die **drei** **Element** Verweis Ziele unterhalb des-Elements des- **Punkt** Arrays, wie in der Abbildung dargestellt.
    > 
    >     ![Erstellen der Shelf Keeper-Klasse](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a>Kapitel 9: Erstellen der productvorhersage-Klasse

Die nächste Klasse, die Sie erstellen, ist die **productvorhersage** -Klasse.

Diese Klasse ist für Folgendes zuständig:

-   Abfragen der **Machine Learning Dienst** Instanz, die das aktuelle Datum und die Uhrzeit bereitstellt.

-   Deserialisieren der JSON-Antwort in verwendbare Daten.

-   Interpretieren der Daten, Abrufen der drei empfohlenen Produkte.

-   Aufrufen der **shelfkeeper** -Klassen Methoden, um die Daten in der Szene anzuzeigen.

So erstellen Sie diese Klasse:

1.  Wechseln Sie im **Projekt Panel**zum Ordner **Scripts** .

2.  Klicken Sie mit der rechten Maustaste in den Ordner, und **Erstellen**  >  **C#** Sie das Skript Nennen Sie das Skript **productvorhersage**.

3.  Doppelklicken Sie auf das neue **productvorhersage** -Skript, um es mit **Visual Studio 2017**zu öffnen.

4.  Wenn das Dialogfeld **Datei Änderung erkannt** angezeigt wird, klicken Sie auf * Projekt Mappe neu**Laden**.

5.  Fügen Sie am Anfang der productvorhersage-Klasse die folgenden Namespaces hinzu:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  Fügen Sie innerhalb der **productvorhersage** -Klasse die folgenden beiden Objekte ein, die aus einer Reihe von geschachtelten Klassen bestehen. Diese Klassen werden zum Serialisieren und Deserialisieren des JSON-Code für den Machine Learning-Dienst verwendet.

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  Fügen Sie dann die folgenden Variablen oberhalb des vorherigen Codes hinzu (sodass sich der JSON-bezogene Code am Ende des Skripts befindet, unter dem gesamten anderen Code und nicht mehr):

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > Stellen Sie sicher, dass Sie den **Primärschlüssel** und den **Anforderungs Antwort-Endpunkt**aus dem Machine Learning-Portal in die Variablen hier einfügen. Die folgenden Bilder zeigen, wo Sie den Schlüssel und den Endpunkt von übernommen hätten. 
    >  
    > ![Der Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Der Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-53-2.png)

8.  Fügen Sie diesen Code in die Methode " **Start ()** " ein. Die Methode " **Start ()** " wird aufgerufen, wenn die Klasse initialisiert:

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  Im folgenden finden Sie die-Methode, die das Datum und die Uhrzeit von Windows erfasst und in ein Format konvertiert, das unser Machine Learning Experiment zum Vergleichen mit den in der Tabelle gespeicherten Daten verwenden kann.

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. Sie können die **Update ()** -Methode **Löschen** , da Sie von dieser Klasse nicht verwendet wird.

11. Fügen Sie die folgende Methode hinzu, die das aktuelle Datum und die aktuelle Uhrzeit an den Machine Learning-Endpunkt kommuniziert und eine Antwort im JSON-Format empfängt.

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialise the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. Fügen Sie die folgende Methode hinzu, die für das Deserialisieren der JSON-Antwort zuständig ist, und das Ergebnis der Deserialisierung an die **shelfkeeper** -Klasse zu übermitteln. Bei diesem Ergebnis handelt es sich um die Namen der drei Elemente, die zum aktuellen Datum und zur aktuellen Uhrzeit am häufigsten verkauft werden. Fügen Sie den folgenden Code in die **productvorhersage** -Klasse ein, unterhalb der vorherigen Methode.

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. Speichern Sie **Visual Studio** , und wechseln Sie zurück zu **Unity**.

14. Ziehen Sie das **productvorhersage** -Klassen Skript aus dem **Skript** Ordner auf das **Hauptkamera** Objekt.

15. Speichern Sie Ihre Szene-und Projekt **Datei** >  > , und speichern Sie das**Projekt**in der Szene.

## <a name="chapter-10---build-the-uwp-solution"></a>Kapitel 10: Erstellen der UWP-Lösung

Nun ist es an der Zeit, das Projekt als UWP-Lösung zu erstellen, damit es als eigenständige Anwendung ausgeführt werden kann.

So erstellen Sie Folgendes:

1.  Speichern Sie die aktuelle Szene, indem Sie auf **Datei** > **Speichern Szenen**klicken.

2.  Gehe zudateibuildeinstellungen > 

3.  Aktivieren Sie das Kontroll **Kästchen C# Unity-Projekte** (Dies ist wichtig, da es Ihnen ermöglicht, die Klassen zu bearbeiten, nachdem der Build abgeschlossen wurde).

4.  Klicken Sie auf **offene Szenen hinzufügen**.

5.  Klicken Sie auf **Erstellen**.

    ![Erstellen der UWP-Lösung](images/AzureLabs-Lab7-54.png)

6.  Sie werden aufgefordert, den Ordner auszuwählen, in dem Sie die Projekt Mappe erstellen möchten.

7.  Erstellen Sie einen Ordner **BUILDS** , und erstellen Sie in diesem Ordner einen anderen Ordner mit einem entsprechenden Namen Ihrer Wahl.

8.  Klicken Sie auf den neuen Ordner, und klicken Sie dann auf **Ordner auswählen**, um den Build an diesem Speicherort zu starten.

    ![Erstellen der UWP-Lösung](images/AzureLabs-Lab7-55.png)

    ![Erstellen der UWP-Lösung](images/AzureLabs-Lab7-56.png)

9.  Nachdem die Erstellung von Unity abgeschlossen ist (Dies kann einige Zeit in Anspruch nehmen), wird ein **Datei-Explorer** -Fenster am Speicherort des Builds geöffnet (überprüfen Sie die Taskleiste, da Sie möglicherweise nicht immer über Ihrem Fenster angezeigt wird, sondern Sie über das Hinzufügen eines neuen Fensters benachrichtigt).

## <a name="chapter-11---deploy-your-application"></a>Kapitel 11: Bereitstellen der Anwendung

So stellen Sie die Anwendung bereit:

1.  Navigieren Sie zu Ihrem neuen Unity-Build ( **App** -Ordner), und öffnen Sie die Projektmappendatei mit **Visual Studio**.

2.  Wenn Visual Studio geöffnet ist, müssen Sie die nuget-Pakete wiederherstellen, indem Sie mit der rechten Maustaste auf Projektmappen-Explorer die MachineLearningLab_Build-Projekt Mappe Klicken (auf der rechten Seite von Visual Studio) und dann auf nuget-Pakete wiederherstellen klicken:

    ![NuGet-Pakete hinzufügen](images/AzureLabs-Lab7-57.png)

3.  Wählen Sie in der Projektmappenkonfiguration **Debuggen**.

4.  Wählen Sie auf der Projektmappenplattform die Option **x86**, **lokaler Computer**aus. 

    > Für Microsoft hololens ist es möglicherweise einfacher, dies auf den *Remote*Computer festzulegen, damit Sie nicht auf Ihren Computer über das Team verfügen. Allerdings müssen Sie auch die folgenden Schritte ausführen:
    > - Informieren Sie sich über die **IP-Adresse** ihrer hololens. Sie finden diese in den *Einstellungen > Netzwerk & Internet > Wi-Fi-> Erweiterte Optionen*; die IPv4-Adresse ist die Adresse, die Sie verwenden sollten. 
    > - Stellen Sie sicher, dass der **Entwicklermodus** **auf**dem in den *Einstellungen > Update & Sicherheits > für Entwickler*gefunden.

    ![NuGet-Pakete hinzufügen](images/AzureLabs-Lab7-58.png)

5.  Wechseln Sie zum **Menü Erstellen** , und klicken Sie auf Lösung bereitstellen, um die Anwendung per querladen auf Ihren PC zu **verlagern** .

6.  Ihre APP sollte nun in der Liste der installierten apps angezeigt werden, die gestartet werden können.

Wenn Sie die Mixed Reality-Anwendung ausführen, wird die Bench angezeigt, die in ihrer Unity-Szene eingerichtet wurde. von der Initialisierung werden die in Azure eingerichteten Daten abgerufen. Die Daten werden in Ihrer Anwendung deserialisiert, und die drei wichtigsten Ergebnisse für das aktuelle Datum und die aktuelle Uhrzeit werden visuell bereitgestellt, wie drei Modelle auf der Bench.


## <a name="your-finished-machine-learning-application"></a>Ihre fertiggestellte Machine Learning Anwendung
 
Herzlichen Glückwunsch, Sie haben eine Mixed Reality-App erstellt, die die Azure Machine Learning nutzt, um Daten Vorhersagen zu treffen und in Ihrer Szene anzuzeigen.

![NuGet-Pakete hinzufügen](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a>Trainiert

**Übung 1**

Experimentieren Sie mit der Sortierreihenfolge Ihrer Anwendung, und lassen Sie die drei untersten Vorhersagen im Regal anzeigen, da diese Daten möglicherweise auch nützlich sind.

**Übung 2**

Die Verwendung von **Azure-Tabellen** füllt eine neue Tabelle mit Wetterinformationen auf und erstellt mithilfe der Daten ein neues Experiment.
