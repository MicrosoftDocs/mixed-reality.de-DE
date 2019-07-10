---
title: MR und Azure 307 - Machine-learning
description: Führen Sie diesen Kurs erfahren, wie Sie Azure Machine Learning Studio in einer mixed Reality-Anwendung zu implementieren.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Unity, Tutorials, api, für maschinelles lernen, ml, Machine Learning Studio, Hololens, immersive, vr
ms.openlocfilehash: 89d9758dedb6a2389644dda887bfadf5b28f6dd2
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694544"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

<br>

# <a name="mr-and-azure-307-machine-learning"></a>MR und Azure-307: Machine Learning

![Endprodukt-starten](images/AzureLabs-Lab7-0.png)

In diesem Kurs lernen Sie, wie Sie Machine Learning (ML)-Funktionen zu einer mixed Reality-Anwendung mit Azure Machine Learning Studio hinzufügen.

*Azure Machine Learning Studio* ist ein Microsoft-Dienst, der Entwickler mit Dateneingabe, Ausgabe, Vorbereitung und Visualisierung kann nützlich sein, eine große Anzahl von Machine Learning-Algorithmen, gewährt. Aus dieser Komponenten ist es dann möglich, ein predictive Analytics-Experiment entwickeln, iterativ durchlaufen und verwenden dieses Zugriffstokens zum Trainieren Ihres Modells. Folgende Training können machen Sie Ihr Modell operational innerhalb der Azure-Cloud, damit es dann neue Daten zu bewerten kann. Weitere Informationen finden Sie auf die [Azure Machine Learning Studio-Seite](https://azure.microsoft.com/en-au/services/machine-learning-studio/).

Nach Abschluss dieses Kurses, Sie müssen eine mixed Reality immersive Kopfhörer-Anwendung und werden haben gelernt, wie die folgenden Schritte ausführen:

1.  Geben Sie eine Tabelle mit Umsatzdaten, die für die *Azure Machine Learning Studio* -Portal und der Entwurf einen Algorithmus zur Vorhersage zukünftiger Umsätze beliebte Artike.
2.  Erstellen Sie eine **Unity-Projekt**, die empfangen und Interpretieren der Daten zur werbungsklickvorhersage aus dem ML-Dienst.
3.  Zeigen Sie die Predication-Daten visuell in der **Unity-Projekt**, über die am häufigsten verwendeten Elemente sales im Regal verstauben bereitstellen.

In Ihrer Anwendung obliegt es Ihnen, wie Sie die Ergebnisse in Ihr Design integrieren werden. Dieser Kurs erfahren Sie, wie Sie ein Azure-Dienst in Ihrem Unity-Projekt zu integrieren. Es ist Ihre Aufgabe, verwenden Sie das wissen, dass Sie aus diesem Kurs zum Verbessern Ihrer mixed Reality-Anwendung erhalten.

Dieser Kurs ist eine eigenständige Tutorials, das aller anderen Mixed Reality-Labs nicht direkt betroffen sind.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> MR und Azure-307: Machine Learning</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Während dieser Kurs in erster Linie für immersive Windows Mixed Reality (VR)-Headsets ausgerichtet ist, können Sie auch anwenden, was Sie in diesem Kurs, Microsoft HoloLens lernen. Wie Sie den Kurs halten, sehen Anmerkungen zu dieser Version auf Änderungen Sie möglicherweise zur Unterstützung von HoloLens einsetzen müssen. Wenn Sie HoloLens verwenden zu können, werden Sie einige Echo während der Sprachaufnahme feststellen.

## <a name="prerequisites"></a>Vorraussetzungen

> [!NOTE]
> In diesem Tutorial wurde für Entwickler mit Erfahrung mit Unity entwickelt und C#. Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Mai 2018) überprüft wurde. Sie können zur Verwendung der neuesten Software, wie in der [installieren Sie die Tools-Artikel](install-the-tools.md), obwohl es nicht davon ausgegangen werden soll, dass die Informationen in diesem Kurs perfekt was finden Sie in der neueren Software entspricht als die unten Angaben aufgeführten .

Es wird empfohlen, die folgende Hardware und Software für diesen Kurs:

- Eine Entwicklungs-PC [kompatibel mit Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) für immersive (VR) Kopfhörer-Entwicklung
- [Windows 10 Fall Creators Update (oder höher) mit der Entwicklermodus aktiviert ist](install-the-tools.md#installation-checklist)
- [Das neueste Windows 10-SDK](install-the-tools.md#installation-checklist)
- [Unity 2017.4](install-the-tools.md#installation-checklist)
- [Visual Studio 2017](install-the-tools.md#installation-checklist)
- Ein [immersive Windows Mixed Reality (VR)-Kopfhörer](immersive-headset-hardware-details.md) oder [Microsoft HoloLens](hololens-hardware-details.md) mit Entwicklermodus aktiviert ist
- Zugriff auf das Internet für die Einrichtung von Azure und ML-Datenabruf

## <a name="before-you-start"></a>Bevor Sie beginnen

Um zu vermeiden, bei der Probleme auftreten, die Erstellung dieses Projekts, es wird dringend empfohlen, dass Sie das Projekt in einem Ordner Stamm oder in der Nähe von Stamm in diesem Lernprogramm genannten erstellen (lange Ordnerpfade können dazu führen, dass Probleme, die zum Zeitpunkt der Erstellung). 

## <a name="chapter-1---azure-storage-account-setup"></a>Kapitel 1: Azure Storage-Konto

Um die Translator-API von Azure zu verwenden, müssen Sie so konfigurieren Sie eine Instanz des Diensts, der für Ihre Anwendung verfügbar gemacht werden.
1.  Melden Sie sich bei der [Azure-Portal](https://portal.azure.com).

    > [!NOTE]
    > Wenn Sie nicht bereits über ein Azure-Konto verfügen, müssen Sie eine erstellen. Wenn Sie dieses Tutorial in einer Situation Classroom bzw. Ihrer testumgebung folgen, bitten Sie Ihre "Instructor" oder eine der aufsichtsführenden für Hilfe beim Einrichten Ihres neuen Kontos.

2.  Sobald Sie angemeldet sind, klicken Sie auf **Speicherkonten** im linken Menü.

    ![Einrichtung von Azure Storage-Kontos](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > Das Wort **neu** wurden möglicherweise durch ersetzt **erstellen Sie eine Ressource**, in neueren-Portalen.

3.  Auf der **Speicherkonten** Registerkarte, klicken Sie auf **hinzufügen**.

    ![Einrichtung von Azure Storage-Kontos](images/AzureLabs-Lab7-2.png)

4.  In der **Create Storage Account** Bereich:

    1.  Fügen Sie eine **Namen** für Ihr Konto bedenken, dass dieses Feld akzeptiert nur Ziffern und Kleinbuchstaben zulässig.
    2.  Für **Bereitstellungsmodell** wählen **RM**.
    3.  Für **Kontoart**Option **Speicher (Allgemein v1)** .
    4.  Für **Leistung**Option **Standard**.
    5.  Für **Replikation** wählen **Read-Access-georedundanter Speicher (RA-GRS)** .
    6.  Lassen Sie **sichere Übertragung erforderlich** als **deaktiviert**.
    7.  Wählen Sie eine **Abonnement**.
    4. Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diesen Labs) unter einer allgemeinen Ressourcengruppe zu halten).

        > Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, bitte [finden Sie im Artikel der Resource-Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).
    
    5.  Bestimmen der **Speicherort** für Ihre Ressourcengruppe aus (Wenn Sie eine neue Ressourcengruppe erstellen). Der Speicherort würde idealerweise in der Region sein, in dem die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar.

5.  Sie müssen auch bestätigen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.

    ![Einrichtung von Azure Storage-Kontos](images/AzureLabs-Lab7-3.png)

6.  Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.

7.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Einrichtung von Azure Storage-Kontos](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a>Kapitel 2: Azure Machine Learning Studio

Verwenden der *Azure Machine Learning*, müssen Sie so konfigurieren Sie eine Instanz von Machine Learning-Dienst für Ihre Anwendung verfügbar gemacht werden.

1.  Klicken Sie im Azure-Portal auf **neu** in der oberen linken Ecke, und suchen Sie nach **Machine Learning Studio Workspace**, drücken Sie die **EINGABETASTE**.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  Die neue Seite bietet eine Beschreibung der **Machine Learning Studio Workspace** Service. Unten links der Aufforderung, klicken Sie auf die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.

3.  Nachdem Sie auf geklickt haben **erstellen**, ein Bereich wird angezeigt, in denen Sie einige Details zu den neuen bereitstellen müssen **Machine Learning Studio-Dienst**:

    1.  Fügen Sie Ihre bevorzugte **Arbeitsbereichsname** für diese Dienstinstanz.

    2.  Wählen Sie eine **Abonnement**.

    3. Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle der Azure Dienste im Zusammenhang mit einem einzelnen Projekt (z. B. z. B. diesen Labs) unter einer allgemeinen Ressourcengruppe zu halten). 

        > Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, bitte [finden Sie im Artikel der Resource-Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    4.  Bestimmen der **Speicherort** für Ihre Ressourcengruppe aus (Wenn Sie eine neue Ressourcengruppe erstellen). Der Speicherort würde idealerweise in der Region sein, in dem die Anwendung ausgeführt wird. Einige Azure-Ressourcen sind nur in bestimmten Regionen verfügbar. Sie sollten die gleiche Ressourcengruppe verwenden, die Sie zum Erstellen von Azure Storage im vorherigen Kapitel verwendet.

    5.  Für die **Speicherkonto** auf **vorhandene**klicken Sie auf das Dropdownmenü, und anschließend von dort aus, klicken Sie auf die **Speicherkonto** Sie im letzten Abschnitt erstellt haben.

    6.  Wählen Sie das entsprechende **Tarif des Arbeitsbereichs** für Sie aus dem Dropdownmenü aus.

    7.  In der **Web Service-Plan** auf **erstellen** **neue** fügen Sie dann einen Namen ein, in das Textfeld ein.

    8.  Von der **Web Service-Plan, den Tarif** wählen den Tarif Ihrer Wahl. Eine Entwicklungstests Ebene namens **DEVTEST Standard** sollte Ihnen kostenlos zur Verfügung.

    9.  Sie müssen auch bestätigen, dass Sie verstanden haben, den Bestimmungen und Bedingungen, die auf diesen Dienst angewendet.

    10. Klicken Sie auf **Erstellen**.

        ![Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.

5.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  Klicken Sie auf die Benachrichtigung, um Ihre neue Dienstinstanz zu untersuchen.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen.

8.  Auf der Seite angezeigt, unter der **zusätzliche Links** auf **starten Machine Learning Studio**, die im Browser leitet der **Machine Learning Studio** das Portal.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  Verwenden der **Anmeldung** Schaltfläche oben rechts oder in der Mitte, bei Ihrer Machine Learning Studio anmelden.

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a>Kapitel 3 – Machine Learning Studio: DataSet-setup

Eine der Methoden, mit denen Machine Learning-Algorithmen funktionieren basiert auf das vorhandene Dataset durch Analysieren der vorhandene Daten und anschließend versucht wird, um zukünftige Ergebnisse vorherzusagen. Dies bedeutet im Allgemeinen mehr vorhandenen Daten, die Ihre können, desto besser, findet der Algorithmus sich auf zukünftige Ergebnisse vorherzusagen.

Eine Beispiel für die Tabelle wird bereitgestellt, um Sie für diesen Kurs aufgerufen [ProductsTableCSV und kann hier heruntergeladen werden](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).

> [!IMPORTANT]
> Die oben genannten ZIP-Datei enthält sowohl die **ProductsTableCSV** und **.unitypackage**, müssen Sie in [Kapitel 6](#chapter-6---importing-the-mlproducts-unity-package). Dieses Paket wird auch in diesem Kapitel, obwohl der Csv-Datei getrennt bereitgestellt.

Dieses Beispiel-DataSet enthält einen Datensatz der meistverkauften Objekte auf einmal pro Stunde, der jeden Tag des Jahres 2017.
        
![Machine Learning Studio: DataSet-setup](images/AzureLabs-Lab7-11.png)

Zum Beispiel wurde auf 1 Tag von 2017, 13 Uhr (Stunde 13), der umsatzstärksten Artikel an: Salz und Pfeffer.

Dieses Beispiel für die Tabelle enthält die 9998 Einträge.

1.  Navigieren Sie wieder zum die **Machine Learning Studio** Portal, und fügen Sie diese Tabelle als eine **Dataset** für Ihre ML. Durch Klicken auf die **+ neu** -Schaltfläche in der unteren linken Ecke des Bildschirms.

    ![Machine Learning Studio: DataSet-setup](images/AzureLabs-Lab7-12.png)

2.  Ein Abschnitt wird im unteren Bereich, und klicken Sie in das Fenster angezeigt, dass es im Navigationsbereich auf der linken Seite. Klicken Sie auf **Dataset**, und nach rechts, und klicken Sie dann **From Local File**.

    ![Machine Learning Studio: DataSet-setup](images/AzureLabs-Lab7-13.png)

3.  Hochladen der neuen **Dataset** mit folgenden Schritten:

    1. Der Uploadfenster wird angezeigt, können Sie **Durchsuchen** der Festplatte für das neue Dataset.

        ![Machine Learning Studio: DataSet-setup](images/AzureLabs-Lab7-14.png)

    2.  Nachdem ausgewählt und im Fenster "Upload" Sichern, lassen Sie das Kontrollkästchen.

    3.  Geben Sie im Textfeld folgenden **ProductsTableCSV.csv** als Namen für das Dataset (wenn auch automatisch hinzugefügt werden soll).

    4.  Verwenden das Dropdownmenü für **Typ**Option **generische CSV-Datei mit einer Kopfzeile (.csv)** .

    5.  Drücken Sie die Teilstriche in der unteren rechten Rand des Fensters hochladen und die **Dataset** hochgeladen werden.

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a>Kapitel 4 – Machine Learning Studio: Das Experiment

Bevor Sie Ihre Machine learning-System erstellen können, müssen Sie beim Erstellen eines Experiments, um Ihre Theorie zu Ihren Daten zu überprüfen. Mit den Ergebnissen wissen Sie, ob Sie weitere Daten benötigen oder wenn keine Abhängigkeit zwischen den Daten und ein mögliches Ergebnis vorliegt.

So starten Sie ein Experiment zu erstellen:

1.  Klicken Sie erneut auf die **+ neu** in der unteren linken Rand der Seite auf die Schaltfläche, und klicken Sie dann auf **Experiment** > **Blank Experiment**.

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-15.png)

2.  Mit der ein leeres Experiment wird eine neue Seite angezeigt:

3.  Erweitern Sie im Bereich auf der linken Seite **Saved Datasets** > **Meine Datasets** , und ziehen Sie die **ProductsTableCSV** auf die **Experimentbereich**.

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-16.png)

4.  Erweitern Sie im Bereich auf der linken Seite **Datentransformation** > **Sample and Split**. Ziehen Sie dann die **Split Data** zum Element der **Experimentbereich**. Das Split-Datenelement wird das Dataset in zwei Teile aufgeteilt. Ein Teil verwenden Sie zum Trainieren von Machine Learning-Algorithmus. Im zweite Teil wird zum Auswerten der Genauigkeit des-Algorithmus generiert verwendet werden.

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-17.png)

5.  Bearbeiten Sie im rechten Bereich (während die Split-Daten, das Element im Zeichenbereich ausgewählt ist), die **Anteil der Zeilen im ersten Ausgabedatensatz** zu **0,7**. Dadurch werden die Daten in zwei Bereiche aufgeteilt, der erste Teil werden 70 % der Daten und der zweite Teil werden die verbleibenden 30 %. Um sicherzustellen, dass die Daten nach dem Zufallsprinzip aufgeteilt wird, stellen Sie sicher, dass die **zufällige Aufteilung** Kontrollkästchen aktiviert bleibt.

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-18.png)

6.  Ziehen Sie eine Verbindung aus der Basis der **ProductsTableCSV** Element auf der Leinwand und dem oberen Rand der Split-Datenelement. Wird die Elemente verbinden und senden die **ProductsTableCSV** Dataset-Ausgabe (Daten), die aufgeteilten Daten eingeben.  

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-19.png)

7.  In der **Experimente** auf der linken Seite im Bereich, erweitern Sie **Machine Learning** > **Train**. Ziehen Sie die **Train Model** Element, in den experimentbereich. Zeichenbereich sollte identisch aussehen der folgenden.

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-20.png)

8.  Von der ***unten links*** von der **Split Data** Element ziehen, eine Verbindung mit der **oben rechts** von der **Train Model** Element. Die erste Teilung von 70 % aus dem Dataset wird durch das Modell trainieren verwendet werden, den Algorithmus trainiert.

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-21.png)

9.  Wählen Sie die **Train Model** Element im Zeichenbereich, und klicken Sie in der **Eigenschaften** (auf der rechten Seite im Browserfenster) klicken Sie auf die **Spaltenauswahl starten** Schaltfläche.

10. In das Textfeld **Produkt** , und drücken Sie dann die **EINGABETASTE**, *Produkt* wird als eine Spalte festgelegt werden, um vorhersagen zu trainieren. Anschluss klicken Sie auf die **Tick** in der Ecke unten rechts, um das Dialogfeld "Auswahl" zu schließen.

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-22.png)

11. Sie sind dabei, zu trainieren einer **Mehrklassige logistische Regression** Algorithmus, um die Angaben zu Käufer vorherzusagen **Produkt** basierend auf der Stunde des Tages und dem Datum. Es ist nicht Gegenstand dieses Dokument wird erläutert, die Details der bereitgestellten Azure Machine Learning Studio, jedoch unterschiedlichen Algorithmen finden Sie mehr über die [Cheat Sheet für Machine Learning-Algorithmus](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)

12. Erweitern Sie im Experiment Elemente im Bereich mit auf der linken Seite **Machine Learning** > **Modell initialisieren** > **Klassifizierung**, und ziehen Sie die  **Mehrklassige logistische Regression** Element, an dem experimentbereich befindet.

13. Verbinden Sie die Ausgabe, zwischen dem unteren Rand der **Mehrklassige logistische Regression**, mit der linken oberen Eingabe der **Train Model** Element.

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-23.png)

14. Erweitern Sie in der Experiment-Elemente im Bereich auf der linken Seite **Machine Learning** > **Bewertung**, und ziehen Sie die **Score Model** Element an der Leinwand.

15. Verbinden Sie die Ausgabe, zwischen dem unteren Rand der **Train Model**, mit der linken oberen Eingabe der **Score Model**.

16. Verbinden Sie die Ausgabe unten rechts von **Split Data**, mit der rechten oberen Eingabe der **Score Model** Element.

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-24.png)

17. In der Liste der **Experiment** Elemente im Bereich auf der linken Seite zu erweitern **Machine Learning** > **auswerten**, und ziehen Sie die **Evaluate Model** Element in den experimentbereich.

18. Verbinden Sie die Ausgabe aus dem **Score Model** mit der linken oberen Eingabe der **Evaluate Model**.

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-25.png)

19. Sie haben Ihr erstes Machine Learning-Experiment erstellt. Sie können jetzt speichern, und führen Sie das Experiment. Klicken Sie im Menü am unteren Rand der Seite klicken Sie auf die **speichern** Schaltfläche, um das Experiment speichern und dann auf **ausführen** an den Anfang des Experiments.

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-26.png)

20. Sie sehen die **Status** des Experiments in der oberen rechten Rand des Zeichenbereichs. Warten Sie einige Augenblicke, bis das Experiment aus, um den Vorgang abzuschließen.

    > Wenn eine große (real World) Dataset vorhanden ist, ist es wahrscheinlich, dass das Experiment Stunden in Anspruch nehmen kann.

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-27.png)

21. Klicken Sie mit der rechten Maustaste auf die **Evaluate Model** Element im Zeichenbereich und von der Kontext-Menü zeigen Sie die Maus über **Auswertungsergebnisse**, und wählen Sie dann **Visualize**.

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-28.png)

22. Die Ergebnisse der Auswertung werden mit die vorhergesagten Ergebnisse im Vergleich zu den tatsächlichen Ergebnissen angezeigt. Dabei wird die 30 % des ursprünglichen Datasets, das zuvor, zum Auswerten des Modells geteilt wurde verwendet. Sie sehen, dass die Ergebnisse sind nicht toll, im Idealfall die höchste Anzahl in jeder Zeile haben würde das markierte Element in den Spalten sein.

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-29.png)

23. Schließen der **Ergebnisse**.

24. Um das neu trainierte Machine Learning-Modell zu verwenden, Sie sie als verfügbar machen müssen, eine **Webdienst**. Zu diesem Zweck klicken Sie auf die **Set Up Web Service** Menü Element im Menü am unteren Rand der Seite, und klicken Sie auf **Predictive Web Service**.

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-30.png)

25. Eine neue Registerkarte erstellt werden, und das trainingsmodell zusammengeführt, um den neuen Webdienst zu erstellen. 

26. Klicken Sie im Menü am unteren Rand der Seite auf **speichern**, klicken Sie dann auf **ausführen**. Sie sehen, dass den Status aktualisiert, in der Ecke oben rechts neben dem experimentbereich befindet.

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-31.png)

27. Nachdem sie ausgeführt, wurde eine **Deploy Web Service** Schaltfläche am unteren Rand der Seite angezeigt. Sie können den Webdienst bereitstellen. Klicken Sie auf **Deploy Web Service** (klassisch) im Menü am unteren Rand der Seite.

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-32.png)

    > Ihrem Browser unter Umständen aufgefordert, um ein Popup, ermöglichen das sollten Sie **ermöglichen**, müssen Sie unter Umständen, drücken **Deploy Web Service** erneut, wenn die Seite "Deploy" nicht angezeigt wird. 

28. Nach dem Erstellen des Experiments gelangen Sie zu einer **Dashboard** Seite, in dem Sie müssen, Ihre **API-Schlüssel** angezeigt. Kopieren Sie sie in einen Editor für den Moment, benötigen Sie es in Ihrem Code sehr bald. Wenn Sie Ihren API-Schlüssel notiert haben, klicken Sie auf die **ANFORDERUNGS-/Antwort** Schaltfläche der **Default Endpoint** Abschnitt unter dem Schlüssel.

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > Wenn Sie Tests auf dieser Seite klicken, werden Sie Lage, Daten einzugeben, und die Ausgabe anzuzeigen. Geben Sie die **Tag** und **Stunde**. Lassen Sie die **Produkt** Eintrag leer. Klicken Sie dann auf die **bestätigen** Schaltfläche. Die Ausgabe am unteren Rand der Seite zeigt den JSON-Code, der die Wahrscheinlichkeit, dass jedes Produkt werden die Wahl darstellt.

29. Eine neue Webseite wird, geöffnet und zeigt die Anweisungen und Beispiele, über die Anforderung-Struktur, die erforderlich sind, indem das Machine Learning Studio. Kopieren der **Anforderungs-URI** auf dieser Seite in Ihrem Editor angezeigt.

    ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-34.png)

Sie haben jetzt ein Machine learning-System, das zeigt das wahrscheinlichste Produkt verkauft werden gemäß Erwerb Verlaufsdaten, die Korrelation mit der Uhrzeit und den Tag des Jahres erstellt werden.

Um den Webdienst aufrufen zu können, benötigen Sie die URL für den Dienstendpunkt und einen API-Schlüssel für den Dienst. Klicken Sie auf die **Consume** Registerkarte im oberen Menü aus.

Die **Verbrauch** Seite "Info" zeigt die Informationen, die Sie benötigen zum Aufrufen des Webdiensts aus Ihrem Code. Kopieren Sie die **Primärschlüssel** und **Anforderung / Antwort** URL. Sie benötigen diese im nächsten Kapitel.

## <a name="chapter-5---setting-up-the-unity-project"></a>Kapitel 5 – Einrichten des Unity-Projekts

Richten Sie ein und Testen Sie Ihrer Mixed Reality Kopfhörer Immersive.

> [!NOTE]
>  Sie **nicht** Motion-Controller für dieses Kurses erforderlich. Wenn Sie die Einrichtung der Immersive Kopfhörer unterstützen müssen, klicken Sie auf [hier](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Open **Unity** , und erstellen Sie ein neues Unity-Projekt namens **MR\_MachineLearning.** Stellen Sie sicher, dass der Projekttyp nastaven NA hodnotu **3D**.

2.  Mit Unity geöffnet, es prüfen, ob der Standardwert ist **Skript-Editor** nastaven NA hodnotu **Visual Studio**. Wechseln Sie zu **bearbeiten** > **Voreinstellungen** und navigieren Sie dann im neuen Fenster zu **externe Tools**. Änderung **externen Skript-Editors** zu **Visual Studio 2017**. Schließen der **Voreinstellungen** Fenster.

3.  Öffnen Sie als Nächstes **Datei** > **Buildeinstellungen** , und wechseln von der Plattform bereitgestellten **universelle Windows-Plattform**, durch Klicken auf die ***Plattform wechseln***  Schaltfläche.

4.  Außerdem stellen Sie sicher, dass:

    1.  **Geräte** nastaven NA hodnotu **einem beliebigen Gerät**.

        > Legen Sie für die Microsoft HoloLens **Zielgerät** zu *HoloLens*.

    2.  **Buildtyp** nastaven NA hodnotu **D3D**.

    3.  **SDK** nastaven NA hodnotu **zuletzt installierte**.

    4.  **Visual Studio-Version** nastaven NA hodnotu **zuletzt installierte**.

    5.  **Erstellen und ausführen** nastaven NA hodnotu **lokalen Computer**.

    6.  Aber keine Sorge, über das Einrichten von **Szenen** jetzt, da diese später bereitgestellt werden.

    7.  Die übrigen Einstellungen sollte jetzt als Standard bleiben.

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab7-35.png)

5.  In der **Buildeinstellungen** Fenster, klicken Sie auf der **Playereinstellungen** Schaltfläche, dadurch wird den entsprechenden Bereich geöffnet, im Bereich, in dem die **Inspektor** befindet. 

6. In diesem Bereich sind müssen einige Einstellungen überprüft werden:

    1.  In der **Weitere Einstellungen** Registerkarte:

        1.  **Scripting** **Laufzeitversion** muss **experimentell** (.NET 4.6 Äquivalent)

        2. **Back-End-Scripting** muss ***.NET***

        3. **API-Kompatibilitätsebene** muss **.NET 4.6**

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab7-36.png)

    2.  In der **Veröffentlichungseinstellungen** Registerkarte **Funktionen**, überprüfen:

        - **InternetClient**

            ![Einrichten des Unity-Projekts](images/AzureLabs-Lab7-37.png)

    3.  Weiter unten im Bereich mit in **XR-Einstellungen** (finden Sie unten **Veröffentlichungseinstellungen**), Teilstriche **virtuelle Realität unterstützt**, stellen Sie sicher, dass die **Windows Mixed Reality-SDK**  wird hinzugefügt

        ![Einrichten des Unity-Projekts](images/AzureLabs-Lab7-38.png)

    

6.  Im **Buildeinstellungen** *Unity C#*  Projekte nicht mehr abgeblendet ist, aktivieren Sie das Kontrollkästchen neben dieser. 

7.  Schließen Sie das Fenster "erstellen".

8.  Speichern Sie das Projekt (**Datei > Speichern Projekt**).

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a>Kapitel 6: Importieren des MLProducts Unity-Pakets

Für diesen Kurs, müssen Sie ein Unity Asset-Paket namens herunterladen [ **Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage). Dieses Paket ist mit einer Szene mit allen Objekten in das vordefinierte, daher können Sie sich auf die erste es alles funktioniert. Die **ShelfKeeper** Skript angegeben wird, enthält jedoch nur die öffentlichen Variablen, für die Szene-Setup-Struktur. Sie müssen Sie alle anderen Abschnitte. 

Um dieses Paket zu importieren:

1.  Mit dem Sie Unity-Dashboard, klicken Sie auf **Assets** klicken Sie dann im Menü am oberen Rand des Bildschirms auf **Import Package, das benutzerdefinierte Paket**.

    ![Importieren des MLProducts Unity-Pakets](images/AzureLabs-Lab7-39.png)

2.  Verwenden Sie die Dateiauswahl zum Auswählen der **Azure-MR-307.unitypackage** packen, und klicken Sie auf **öffnen**.

3.  Eine Liste der Komponenten für dieses Medienobjekt wird Ihnen angezeigt werden. Bestätigen Sie den Import, indem Sie auf **importieren**.

    ![Importieren des MLProducts Unity-Pakets](images/AzureLabs-Lab7-40.png)

4.  Sobald er abgeschlossen ist, importieren, werden Sie sehen, dass einige neue Ordner in Ihrem Unity Anmeldeinformationsdialogfeld **Projektfenster**. Dies sind die-3D-Modelle und die jeweiligen Materialien, die Teil der Szene vorgefertigte, an denen Sie arbeiten werden. Schreiben Sie den Großteil des Codes in diesem Kurs.

    ![Importieren des MLProducts Unity-Pakets](images/AzureLabs-Lab7-41.png)

5.  In der **Projektfenster** Ordner, klicken Sie auf die **Szenen** Ordner und doppelklicken klicken Sie auf die Szene in (namens **MR_MachineLearningScene**). Die Szene wird geöffnet (siehe Abbildung unten). Wenn die roten Rauten fehlt, klicken Sie einfach auf die **Gizmos** oben die Schaltfläche rechts von der **Spiel Bereich**.

    ![Importieren des MLProducts Unity-Pakets](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a>Kapitel 7 – überprüfen die DLLs in Unity

Um die Verwendung der JSON-Bibliotheken (verwendet für die Serialisierung und Deserialisierung) nutzen zu können, wurde ein Newtonsoft-DLL mit dem Paket implementiert, die Sie in weitergeleitet. Die Bibliothek sollten die ordnungsgemäße Konfiguration verfügen, wäre es prüfen, ob (insbesondere, wenn Sie Probleme mit Code nicht funktioniert haben). 

Gehen Sie hierzu wie folgt vor:

-  Klicken Sie auf die Newtonsoft-Datei in den Ordner "Plug-Ins" aus, und sehen Sie sich die **Inspektor Bereich**. Stellen Sie sicher, dass **Any Platform** ist. Wechseln Sie zu der **UWP Registerkarte** und vergewissern Sie sich außerdem **nicht verarbeiten** ist.

    ![Importieren die DLLs in Unity](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a>Kapitel 8 – erstellen Sie die ShelfKeeper-Klasse

Die **ShelfKeeper** Klasse hostet, Methoden, die die Benutzeroberfläche und die Produkte, die in der Szene erzeugt steuern.

Als Teil des importierten Paket werden Sie diese Klasse stellt erhalten haben, obwohl dies nicht zutrifft. Jetzt ist es Zeit zum Abschließen dieser Klasse:

1.  Einen Doppelklick auf die **ShelfKeeper** Skript zu erstellen, in der **Skripts** Ordner, öffnen Sie ihn mit **Visual Studio 2017**.

2.  Der gesamte Code in das Skript mit den folgenden Code, der legt das Datum und die und verfügt über eine Methode zum Anzeigen eines Produkts vorhandene zu ersetzen.

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

3.  Achten Sie darauf, dass Sie zum Speichern der Änderungen in **Visual Studio** vor der Rückgabe an **Unity**.

4.  Zurück im Unity-Editor, überprüfen Sie, ob die **ShelfKeeper** Klasse sieht wie der unten:

    ![Erstellen Sie die ShelfKeeper-Klasse](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > Wenn das Skript keinen Verweis Ziele (d. h. *Datum (Text-Mesh)* ), ziehen Sie einfach die entsprechenden Objekte in der **Hierarchie Bereich**, in die Zielfelder. Finden Sie weiter unten erläutert, bei Bedarf:
    > 
    > 1.  Öffnen der **Spawn Punkt** im array der **ShelfKeeper** Komponentenskript, indem sie mit der linken Maustaste. Ein Unterbereich angezeigt namens **Größe**, die die Größe des Arrays angibt. Typ **3** in das Textfeld neben **Größe** , und drücken Sie **EINGABETASTE**, und unter drei Slots erstellt werden.
    > 2. In der **Hierarchie** erweitern Sie die **Zeitanzeige** Objekt (durch den Pfeil neben dem mit der linken Maustaste). Klicken Sie dann auf die ***Main Camera*** innerhalb der **Hierarchie**, sodass die **Inspektor** zeigt die Informationen.
    > 3. Wählen Sie die **Hauptkamera** in die **Hierarchie Bereich**. Ziehen Sie die **Datum** und **Zeit** Objekte aus der **Hierarchie Bereich** auf die **-Textformat** und **Wenn Text** Slots innerhalb der **Inspektor** von der **Main Camera** in die **ShelfKeeper** Komponente.
    > 4. Ziehen Sie die **Spawn Punkte** aus der **Hierarchie Bereich** (unter der *Regal* Objekt), die **3** **Element**verweisen Ziele unterhalb der **Spawn Punkt** array, da in der Abbildung dargestellt.
    > 
    >     ![Erstellen Sie die ShelfKeeper-Klasse](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a>Kapitel 9 – erstellen Sie die ProductPrediction-Klasse

Die nächste Klasse, die Sie erstellen wollen ist die **ProductPrediction** Klasse.

Diese Klasse ist zuständig für:

-   Abfragen der **Machine Learning-Dienst** Instanz, die das aktuelle Datum und eine Uhrzeit angeben.

-   Deserialisiert die JSON-Antwort in nutzbare Daten.

-   Interpretieren von Daten, die 3 empfohlene Produkte abrufen.

-   Aufrufen der **ShelfKeeper** -Klassenmethoden, um die Daten in der Szene anzuzeigen.

Diese Klasse zu erstellen:

1.  Wechseln Sie zu der **Skripts** Ordner, in der **Projektfenster**.

2.  Mit der rechten Maustaste in den Ordner **erstellen**  >   **C# Skript**. Rufen Sie das Skript **ProductPrediction**.

3.  Doppelklicken Sie auf dem neuen **ProductPrediction** Skript öffnen Sie ihn mit **Visual Studio 2017**.

4.  Wenn die **Datei Dateiänderung festgestellt** Dialogfeld erscheint, klicken Sie auf ***Projektmappe erneut laden**.

5.  Fügen Sie am oberen Rand der ProductPrediction-Klasse die folgenden Namespaces hinzu:

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

6.  In der **ProductPrediction** Klasse fügen Sie die folgenden zwei Objekte, die sich aus einer Reihe von geschachtelten Klassen zusammensetzen. Diese Klassen werden zum Serialisieren und Deserialisieren des JSON-Codes für die Machine Learning-Dienst verwendet.

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

7.  Fügen Sie dann die folgenden Variablen über dem vorherigen Code, (sodass der JSON-Code im Zusammenhang, dass Code unten auf der das Skript unter allen anderen Code, und aus dem Weg ist):

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
    > Achten Sie darauf, fügen Sie der **Primärschlüssel** und **Anforderung / Antwort-Endpunkt**, aus der Machine Learning-Portal, in der Variablen hier. Die unterhalb des Images angezeigt, in dem Sie den Schlüssel und Endpunkt von erforderlich gewesen wäre. 
    >  
    > ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Machine Learning Studio: Das Experiment](images/AzureLabs-Lab7-53-2.png)

8.  Fügen Sie diesen Code innerhalb der **Start()** Methode. Die **Start()** Methode wird aufgerufen, wenn die Klasse initialisiert:

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

9.  Im folgenden finden die Methode, die erfasst das Datum und Uhrzeit von Windows und konvertiert es in ein Format, die von unseren Machine Learning-Experiment verwenden können, mit den in der Tabelle gespeicherten Daten verglichen werden soll.

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

10. Sie können **löschen** der **Update()** Methode, da diese Klasse nicht verwendet wird.

11. Fügen Sie die folgende Methode wird das aktuelle Datum und die Uhrzeit an den Machine Learning-Endpunkt zu kommunizieren, und erhalten eine Antwort im JSON-Format hinzu.

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

12. Fügen Sie die folgende Methode, die verantwortlich für das Deserialisieren der JSON-Antwort und das Ergebnis der Deserialisierung in der Kommunikation ist die **ShelfKeeper** Klasse. Dieses Ergebnis werden die Namen der drei Elemente vorhergesagt, dass Sie um am meisten am aktuellen Datum und Uhrzeit zu verkaufen. Fügen Sie den folgenden Code in die **ProductPrediction** -Klasse, unter der vorherigen Methode.

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

13. Speichern Sie **Visual Studio** und navigieren Sie wieder zum **Unity**.

14. Ziehen Sie die **ProductPrediction** Klasse-Skript aus der **Skript** Ordner, auf die **Main Camera** Objekt.

15. Speichern Sie Ihre Szene und das Projekt **Datei** > **Szenendatei speichern** > **Projekt speichern**.

## <a name="chapter-10---build-the-uwp-solution"></a>Kapitel 10 – erstellen Sie die UWP-Projektmappe

Es ist nun Zeit, Ihr Projekt als UWP-Lösung zu erstellen, damit es als eigenständige Anwendung ausgeführt werden kann.

So erstellen Sie:

1.  Speichern Sie durch Klicken auf die aktuelle Szene **Datei** > **speichern Szenen**.

2.  Wechseln Sie zu **Datei** > **Buildeinstellungen**

3.  Aktivieren Sie das Kontrollkästchen namens **Unity C# Projekte** (Dies ist wichtig, da er kann Sie die Klassen zu bearbeiten, nachdem der Build abgeschlossen ist).

4.  Klicken Sie auf **Hinzufügen von Open Szenen**,

5.  Klicken Sie auf **Erstellen**.

    ![Erstellen Sie die UWP-Projektmappe](images/AzureLabs-Lab7-54.png)

6.  Sie werden aufgefordert werden, um den Ordner auszuwählen, in dem Sie die Projektmappe erstellen möchten.

7.  Erstellen Sie eine **erstellt** Ordner, und erstellen Sie einen anderen Ordner in diesem Ordner mit einem entsprechenden Namen Ihrer Wahl.

8.  Klicken Sie auf den neuen Ordner, und klicken Sie dann auf **Ordner auswählen**, um den Build an diesem Speicherort zu beginnen.

    ![Erstellen Sie die UWP-Projektmappe](images/AzureLabs-Lab7-55.png)

    ![Erstellen Sie die UWP-Projektmappe](images/AzureLabs-Lab7-56.png)

9.  Einmal Unity wurde (es kann einige Zeit dauern) erstellen, öffnen ein **Datei-Explorer** Fenster am Speicherort des Builds (Überprüfen Sie Ihre Taskleiste aus, wie es unter Umständen nicht immer über Ihre Windows angezeigt und Sie über das Hinzufügen eines neuen benachrichtigt Fenster ").

## <a name="chapter-11---deploy-your-application"></a>Kapitel 11 – Ihre Anwendung bereitstellen.

Um die Anwendung bereitzustellen:

1.  Navigieren Sie zu Ihrem neuen Unity-Build (die **App** Ordner), und öffnen Sie die Projektmappendatei mit **Visual Studio**.

2.  Mit Visual Studio öffnen müssen Sie NuGet-Pakete wiederherstellen, die ausgeführt werden kann, mit der rechten Maustaste in der Projektmappe MachineLearningLab_Build Projektmappen-Explorer (rechts neben Visual Studio gefunden), und klicken Sie dann auf NuGet-Pakete wiederherstellen:

    ![NuGet-Pakete hinzufügen](images/AzureLabs-Lab7-57.png)

3.  In der Projektmappenkonfiguration Select **Debuggen**.

4.  Wählen Sie in der Plattform für die Projektmappe **X86**, **lokalen Computer**. 

    > Für die Microsoft HoloLens Umständen ist es einfacher, diese Einstellung auf *Remotecomputer*, sodass Sie nicht auf Ihren Computer angeschlossen sind. Allerdings müssen Sie auch die folgenden Schritte ausführen:
    > - Kennen der **IP-Adresse** von Ihrem HoloLens, die sich in befinden die *Einstellungen > Netzwerk und Internet > Wi-Fi > Erweiterte Optionen*; IPv4 ist die Adresse, die Sie verwenden sollten. 
    > - Stellen Sie sicher **Entwicklermodus** ist **auf**; gefunden in *Einstellungen > Update und Sicherheit > für Entwickler*.

    ![NuGet-Pakete hinzufügen](images/AzureLabs-Lab7-58.png)

5.  Wechseln Sie zu **Menü "Build"** und klicken Sie auf **Projektmappe bereitstellen** zum querladen der Anwendung auf Ihren PC.

6.  Ihre App sollte nun in der Liste der installierten apps, die zu startenden bereit angezeigt werden.

Wenn Sie die Mixed Reality-Anwendung ausführen, sehen Sie die Bench, die in Ihrer Unity-Szene eingerichtet wurde, und von Initialisierung, die Daten, die Sie in Azure eingerichtet werden abgerufen. Deserialisiert die Daten in Ihrer Anwendung, und die ersten drei Ergebnisse für Ihre aktuellen Datum und Uhrzeit werden als drei Modelle für die Bench visuell bereitgestellt werden.


## <a name="your-finished-machine-learning-application"></a>Der fertigen Machine Learning-Anwendung
 
Herzlichen Glückwunsch, Sie erstellt haben, eine mixed Reality-app, die Azure Machine Learning Daten Vorhersagen machen, und zeigen Sie es in Ihrer Szene nutzt.

![NuGet-Pakete hinzufügen](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a>Übung

**Übung 1**

Experimentieren Sie mit der Sortierreihenfolge nach Ihrer Anwendung, und haben Sie die drei unteren Vorhersagen im Regal, angezeigt werden, wie diese Daten möglicherweise auch Interesse sein könnte.

**Übung 2**

Mithilfe von **Azure-Tabellen** eine neue Tabelle mit Wetterdaten füllen, und erstellen Sie ein neues Experiment unter Verwendung der Daten.
