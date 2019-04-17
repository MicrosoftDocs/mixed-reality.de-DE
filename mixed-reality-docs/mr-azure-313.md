---
title: 'MR und Azure-313: IoT Hub-Dienst'
description: Führen Sie diesen Kurs erfahren, wie Sie Azure IoT Hub-Dienst auf einem virtuellen Computer unter Ubuntu 16.4 implementieren, und klicken Sie dann visualisieren Sie die Nachrichtendaten, die mithilfe von Microsoft HoloLens oder eine immersive (VR) Kopfhörer zu.
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: Azure, mixed Reality, Academy, Edge, Iot-Edge, Tutorial, api, Notification, Funktionen, Tabellen, immersive Hololens, Vr, Iot, VM, Ubuntu, Python
ms.openlocfilehash: 1ab7c48ac3cff1cb2283cadb171098af9e148628
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59593253"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

# <a name="mr-and-azure-313-iot-hub-service"></a>MR und Azure-313: IoT Hub-Dienst

![Kurs Ergebnis](images/AzureLabs-Lab313-00.png)

In diesem Kurs erfahren Sie, wie zum Implementieren einer **Azure IoT Hub-Dienst** auf einem virtuellen Computer das Betriebssystem die Ubuntu-16.4 ausgeführt. Ein **Azure Function-App** wird dann zum Empfangen von Nachrichten von Ihrem Ubuntu-VM verwendet werden, und speichern Sie das Ergebnis in eine **Azure-Tabellendienst**. Sie werden dann in der Lage sind, zeigen Sie diese Daten mithilfe **Power BI** für Microsoft HoloLens oder Kopfhörer für immersive (VR).

Der Inhalt dieses Kurses *gilt* auf IoT Edge-Geräten, obwohl in diesem Kurs, der Fokus werden in einer VM-Umgebung, damit kein Zugriff auf ein physisches edgegerät erforderlich ist.

Nach Abschluss dieses Kurses, lernen Sie Folgendes:

- Bereitstellen einer **IoT Edge-Modul** an einen virtuellen Computer (Ubuntu 16 OS), die Ihr IoT-Gerät darstellen wird.
- Hinzufügen einer **Azure Custom Vision Tensorflow-Modells** für das Edge-Modul, mit Code, der im Container gespeicherte Bilder analysiert wird.
- Richten Sie das Modul zum Senden der Nachricht der Analysis-Ergebnis zurück an Ihre **IoT Hub-Dienst**.
- Verwenden einer **Azure Function-App** zum Speichern der Nachricht in eine **Azure Table**.
- Richten Sie **Power BI** gespeicherten Nachrichten sammeln, und erstellen Sie einen Bericht.
- Visualisieren Sie Ihre IoT-Nachrichtendaten in **Power BI**.

Die Dienste, die Sie verwenden, umfassen:

- **Azure IoT-Hub** ist ein Microsoft Azure der Dienst ermöglicht es Entwicklern, verbinden, überwachen und Verwalten von IoT-Assets. Weitere Informationen finden Sie auf die [ **Azure IoT Hub-Dienst** Seite](https://azure.microsoft.com/en-au/services/iot-hub/).

- **Azure-Containerregistrierung** ist ein Microsoft Azure der Dienst ermöglicht Entwicklern das Speichern von containerimages für verschiedene Arten von Containern. Weitere Informationen finden Sie auf die [ **Azure Container Registry Service** Seite](https://azure.microsoft.com/en-au/services/container-registry/).

- **Azure-Funktions-App** ist ein Azure-Dienst von Microsoft, die Entwickler kleine Teile des Codes ausgeführt werden kann, "Funktionen", in Azure. Dadurch wird eine Möglichkeit zum Delegieren der Arbeit an Ihrer lokalen Anwendung, die viele Vorteile haben kann, anstatt die Cloud. **Azure Functions** unterstützt verschiedene Entwicklungssprachen, darunter C\#, F\#, Node.js, Java und PHP. Weitere Informationen finden Sie auf die [ **Azure Functions** Seite](https://docs.microsoft.com/azure/azure-functions/functions-overview).

- **Azure-Speicher: Tabellen** ist ein Microsoft Azure-Dienst, die Entwicklern das Speichern, strukturiert kann, nicht-SQL, Daten in der Cloud, somit problemlos eine beliebige Stelle. Der Dienst bietet ein schemalose Design, sodass für die Entwicklung von Tabellen, je nach Bedarf, und ist daher sehr flexibel. Weitere Informationen finden Sie auf die [ **Azure-Tabellen** Seite](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

In diesem Kurs erfahren Sie, wie zum Einrichten und verwenden Sie den IoT Hub-Dienst und stellen dann eine Antwort von einem Gerät bereitgestellten visuell dar. Sie werden sich entscheiden, ob Sie diese Konzepte zu einem benutzerdefinierten Setup für die IoT Hub-Dienst angewendet, die Sie erstellen.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td> MR und Azure-313: IoT Hub-Dienst</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Vorraussetzungen

Die aktuellsten Voraussetzungen für die Entwicklung mit gemischten Realität, einschließlich der mit dem Microsoft HoloLens finden Sie unter den [Installieren der Tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) Artikel.

> [!NOTE]
> In diesem Tutorial ist für Entwickler konzipiert, die grundlegende Erfahrung mit Python haben. Bedenken Sie dabei auch, dass die Voraussetzungen und schriftliche Anweisungen in diesem Dokument darstellen, was getestet und zum Zeitpunkt des Schreibens von (Juli 2018) überprüft wurde. Sie können zur Verwendung der neuesten Software, wie in der [Installieren der Tools](install-the-tools.md) jedoch nicht angenommen werden soll, dass die Informationen in diesem Kurs perfekt Angebote in neueren Software als die entspricht unten aufgeführten Artikel.

Die folgende Hardware und Software ist erforderlich:

- Windows 10 Fall Creators Update (oder höher), **Entwicklermodus aktiviert ist**

    > [!WARNING]
    > Sie können nicht mit Hyper-V unter Windows 10 Home Edition einen virtuellen Computer ausführen.

- Windows 10 SDK (neueste Version)
- Eine HoloLens **Entwicklermodus aktiviert ist**
- Visual Studio 2017.15.4 (nur auf dem Azure-Cloud-Explorer verwendet)
- Zugriff auf das Internet für Azure und IoT Hub-Dienst. Weitere Informationen führen Sie dies [Link zur Seite für IoT Hub-Dienst](https://azure.microsoft.com/en-au/services/iot-hub/)
- Machine Learning-Modellen. Wenn Sie Ihre eigenen kann jetzt Modell verwenden keine [können Sie das Modell bereitgestellt, die in diesem Kurs](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).
- **Hyper-V** Software auf Ihrem Entwicklungscomputer für Windows 10 aktiviert.
- Einen virtuellen Computer Ubuntu (16.4 oder 18.4), ausgeführt auf Ihrem Entwicklungscomputer oder Alternativ können Sie können sich auf einem separaten Computer unter Linux (Ubuntu 16.4 oder 18.4). Können weitere Informationen finden Sie Anleitungen zum Erstellen eines virtuellen Computers unter Windows mithilfe von Hyper-V in der ["Vorbereitungen" im Kapitel](#before-you-start). () https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).  



### <a name="before-you-start"></a>Bevor Sie beginnen

1. Richten Sie ein und Testen Sie Ihre HoloLens. Bei Bedarf Unterstützung zum Einrichten Ihrer HoloLens, [stellen Sie sicher, dass die HoloLens-Setup-Artikel finden Sie unter](https://docs.microsoft.com/hololens/hololens-setup).
2. Es ist eine gute Idee, führen Sie **Kalibrierung** und **Sensor Optimierung** Beginn (manchmal es kann helfen, diese Aufgaben für jeden Benutzer) eine neue HoloLens-app entwickeln.

Um Hilfe zur Kalibrierung, befolgen Sie diese [Link zum Artikel HoloLens Kalibrierung](calibration.md#hololens).

Um Hilfe zur Optimierung der Sensor, befolgen Sie diese [Link zum Optimieren von HoloLens Sensor](sensor-tuning.md).

3. Richten Sie Ihre **virtuellen Ubuntu-Computer** mit **Hyper-V**. Die folgenden Ressourcen helfen Ihnen mit dem Prozess.
    1.  Führen Sie zunächst diesen Link, um [Herunterladen der ISO-Datei für Ubuntu 16.04.4 LTS (Xenial Xerus)](http://au.releases.ubuntu.com/16.04/). Wählen Sie die **Desktopabbild für 64-Bit-PC (AMD64)**.
    2.  Stellen Sie sicher, dass **Hyper-V** auf Ihrem Windows 10-Computer aktiviert ist. Folgen Sie diesem Link, um Anleitungen auf [installieren und aktivieren Hyper-V unter Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).
    3.  Starten Sie die Hyper-V, und Erstellen einer neuen Ubuntu-VM. Sie können diesem Link folgen einem [Schritt-für-Schritt-Anleitung zum Erstellen eines virtuellen Computers mit Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine). Bei angeforderten **"Betriebssystem von startfähiger Imagedatei installieren"**, wählen die **Ubuntu ISO** haben Sie zuvor herunterladen.

    > [!NOTE]
    > Mithilfe von **Hyper-V-Schnellerfassung** wird nicht empfohlen.  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a>Kapitel 1: Abrufen des Custom Vision-Modells

In diesem Kurs haben Sie Zugriff auf eine [vorgefertigte Custom Vision-Modell](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) , der erkennt, Tastaturen und Mäusen aus Bildern. Wenn Sie diese verwenden, fahren Sie mit [Kapitel 2](#chapter-2---the-container-registry-service).

Allerdings können Sie folgende Schritte ausführen, wenn Sie Ihre eigenen Custom Vision-Modell verwenden möchten:

1. In Ihrer **Custom Vision Projekt** wechseln Sie zu der **Leistung** Registerkarte.

    > [!WARNING]
    > Verwenden Sie das Modell muss eine *compact* Domäne exportieren. Sie können Ihre Modelle Domäne in den Einstellungen für das Projekt ändern.

    ![Registerkarte "Leistung"](images/AzureLabs-Lab313-01.png)

2. Wählen Sie die **Iteration** Sie exportieren möchten und klicken auf **exportieren**. Es wird ein Blatt angezeigt.

    ![Blatt "Export"](images/AzureLabs-Lab313-02.png)

3. Klicken Sie auf dem Blatt auf **Docker-Datei**.

    ![Wählen Sie docker](images/AzureLabs-Lab313-03.png)

4. Klicken Sie auf **Linux** in der Dropdown-Menü, und klicken Sie dann auf **herunterladen**.

    ![Klicken Sie auf download](images/AzureLabs-Lab313-04.png)

5. Entzippen Sie den Inhalt aus. Sie werden später in diesem Kurs verwendet.

## <a name="chapter-2---the-container-registry-service"></a>Kapitel 2: der Container-Service-Registrierung

Die **-Containerregistrierungsdienst** ist das Repository, das zum Hosten Ihrer Container verwendet.

Die **IoT Hub-Dienst** , den Sie erstellen und verwenden Sie in diesem Kurs bezieht sich auf **-Containerregistrierungsdienst** zum Abrufen der Container in Ihrem Edge-Gerät bereitstellen.

1. Führen Sie zunächst diese [Link zum Azure-Portal](https://portal.azure.com/), und melden Sie sich mit Ihren Anmeldeinformationen.

2. Wechseln Sie zu **erstellen Sie eine Ressource** und suchen Sie nach **Containerregistrierung**.

    ![Container Registry-Instanz](images/AzureLabs-Lab313-05.png)

3. Klicken Sie auf **erstellen**.

    ![](images/AzureLabs-Lab313-06.png)

4. Legen Sie den Dienst Setupparameter:

    1. Fügen Sie einen Namen für Ihr Projekt, In diesem Beispiel die Hauptdateitabelle **IoTCRegistry**.

    2. Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, bereitzustellen und zu verwalten, Rechnungen für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle zu bewahren, an die Azure-Dienste unter einer allgemeinen Ressourcengruppe mit einem einzelnen Projekt (z. B. z. B. diese Kurse) verknüpft ist).

    3. Legen Sie den Speicherort des Diensts.

    4. Legen Sie **Administratorbenutzer** zu **aktivieren**.

    5. Legen Sie **SKU** zu **grundlegende**. 

    ![](images/AzureLabs-Lab313-07.png)

5. Klicken Sie auf **erstellen** und warten Sie, für die Dienste erstellt werden. 

6. Sobald eingeblendet, dass die Benachrichtigung darüber informiert Sie über die erfolgreiche Erstellung von der *Containerregistrierung*, klicken Sie auf **zu Ressource wechseln** Ihrer Dienst-Seite umgeleitet werden.

    ![](images/AzureLabs-Lab313-08.png)

7. In der *Containerregistrierung* Seite, klicken Sie auf **Zugriffsschlüssel**.

8. Notieren Sie sich (Sie können Ihr Editor verwenden) die folgenden Parameter:
    1. **Login Server**
    2. **Benutzername**
    3. **Kennwort**

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a>Kapitel 3 – IoT Hub-Dienst

Nachdem Sie die Erstellung und Einrichtung von nun an Ihre **IoT Hub-Dienst**.

1. Wenn nicht bereits angemeldet, melden Sie sich bei der [Azure-Portal](https://portal.azure.com).

2.  Sobald Sie angemeldet sind, klicken Sie auf **erstellen Sie eine Ressource** in der oberen linken Ecke, und suchen Sie nach **IoT Hub**, und klicken Sie auf **EINGABETASTE**.

 ![Suchen Sie nach dem Storage-Konto](images/AzureLabs-Lab313-10.png)

3.  Die neue Seite bietet eine Beschreibung der **Speicherkonto** Service. Unten links der Aufforderung, klicken Sie auf die **erstellen** Schaltfläche, um eine Instanz dieses Diensts erstellen.

    ![Storage-Instanz erstellen](images/AzureLabs-Lab313-11.png)

4.  Nachdem Sie auf geklickt haben **erstellen**, wird ein Panel angezeigt:

    1. Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, steuern den Zugriff, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle zu bewahren, an die Azure-Dienste unter einer allgemeinen Ressourcengruppe mit einem einzelnen Projekt (z. B. z. B. diese Kurse) verknüpft ist).

        > Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, befolgen Sie diese [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).


    2. Wählen Sie einen geeigneten **Speicherort** (verwenden Sie am gleichen Speicherort für alle Dienste, die Sie in diesem Kurs erstellen).

    3. Fügen Sie Ihre bevorzugte **Namen** für diese Dienstinstanz.    

5.  Klicken Sie auf den unteren Rand der Seite auf **weiter: Größe und Skalierung**.

    ![Storage-Instanz erstellen](images/AzureLabs-Lab313-12.png)

6.  Auf dieser Seite Wählen Sie Ihre **Tarif und Skalierung** (ist dies Ihre erste IoT Hub-Dienst-Instanz, ein freier-Tarif muss Ihnen zur Verfügung).  

7.  Klicken Sie auf **überprüfen + erstellen**.

    ![Storage-Instanz erstellen](images/AzureLabs-Lab313-13.png)

8.  Überprüfen Sie die Einstellungen, und klicken Sie auf **erstellen**.

    ![Storage-Instanz erstellen](images/AzureLabs-Lab313-14.png)

9. Sobald eingeblendet, dass die Benachrichtigung darüber informiert Sie über die erfolgreiche Erstellung der *IoT Hub* -Dienst, klicken Sie auf **zu Ressource wechseln** Ihrer Dienst-Seite umgeleitet werden.

    ![Storage-Instanz erstellen](images/AzureLabs-Lab313-15.png)

10. Der Seitenleiste links scrollen, bis Sie sehen *automatische Geräteverwaltung*, die auf **IoT Edge**.

    ![Storage-Instanz erstellen](images/AzureLabs-Lab313-16.png)

11. Klicken Sie im Fenster, das auf der rechten Seite angezeigt wird, auf **IoT Edge-Gerät hinzufügen**. Ein Blatt wird auf der rechten Seite angezeigt.

12. Geben Sie auf dem Blatt, das neue Gerät einen **Geräte-ID** (einen Namen Ihrer Wahl). Klicken Sie auf **speichern**. Die *primären* und *Sekundärschlüssel* automatisch generiert, wenn man **automatisch generieren** ausgewählt.

    ![Storage-Instanz erstellen](images/AzureLabs-Lab313-17.png)

13. Sie gelangen zurück auf die *IoT Edge-Geräte* Abschnitt, in dem das neue Gerät aufgeführt. Klicken Sie auf das neue Gerät (rot markiert, in der folgenden Abbildung). 

    ![Storage-Instanz erstellen](images/AzureLabs-Lab313-18.png)

14. Auf der *Gerätedetails* Seite, die angezeigt wird, erstellen Sie eine Kopie der **Verbindungszeichenfolge** (Primärschlüssel).

    ![Storage-Instanz erstellen](images/AzureLabs-Lab313-19.png)

15. Kehren Sie zurück zum Bereich auf der linken Seite, und klicken Sie auf *Richtlinien für gemeinsamen Zugriff*, um ihn zu öffnen. 

16. Klicken Sie auf der daraufhin angezeigten Dialogfeld auf **Iothubowner**, und ein Blatt wird angezeigt, die den rechten Rand des Bildschirms. 

17. Achten Sie darauf (in Ihrem Editor) des der **Verbindungszeichenfolge** (Primärschlüssel), für die spätere Verwendung beim Festlegen der *Verbindungszeichenfolge* auf Ihrem Gerät.

    ![Storage-Instanz erstellen](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a>Kapitel 4: Einrichten der Entwicklungsumgebung

Zum Erstellen und Bereitstellen von Modulen für *IoT Hub-Edge*, benötigen Sie die folgenden Komponenten auf Ihrem Entwicklungscomputer mit Windows 10 installiert:

1.  [Docker für Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), fordert Sie zum Erstellen eines Kontos ein, um das Herunterladen zu können. 

    [![Docker für Windows herunterladen](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)

    > [!IMPORTANT]
    > Erfordert Docker *Windows 10 PRO*, *Enterprise 14393*, oder *Windows Server 2016 RTM*, um auszuführen. Wenn Sie andere Versionen von Windows 10 ausgeführt werden, können Sie versuchen, installieren Docker mit der [Docker Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/).

2.  [Python 3.6](https://www.python.org/downloads/).

    [![Laden Sie Python 3.6 herunter.](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)

3.  [Visual Studio Code (auch bekannt als VS Code)](https://code.visualstudio.com/download).

    [![Herunterladen von Visual Studio Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)

Nach der Installation der oben genannten Software, müssen Sie den Computer neu starten.

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a>Kapitel 5: Einrichten der Ubuntu-Umgebung

Nachdem Sie verschieben können, um die Einrichtung Ihres Geräts **mit Ubuntu-Betriebssystem**. Folgenden Sie die Schritte, installieren Sie die erforderliche Software, um Ihre Container in Ihrem Board bereitzustellen:

> [!IMPORTANT]
> Sie sollten immer die terminal-Befehlen mit voranstellen **"sudo"** als Administrator ausführen. i.e:
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  Öffnen der **Ubuntu Terminal**, und verwenden Sie den folgenden Befehl, um installieren **Pip**:

    > [! Hinweis] Sie können öffnen *Terminal* ganz einfach über die Tastenkombination: **Ctrl + Alt + T**.

    ```bash
        sudo apt-get install python-pip
    ```

2.  In diesem Kapitel werden Sie möglicherweise aufgefordert, durch *Terminal*, für die Berechtigung zum Verwenden des Gerätespeichers und für Sie zur Eingabe **j/n** (Ja oder Nein), Typ **'y'**, und drücken Sie dann die **EINGABETASTE** Schlüssel, um zu akzeptieren.

3.  Wenn dieser Befehl abgeschlossen ist, verwenden Sie den folgenden Befehl zum Installieren **curl**:

    ```bash
        sudo apt install curl
    ```

4.  Einmal **Pip** und **curl** sind installiert sind, verwenden Sie den folgenden Befehl zum Installieren der **IoT Edge-Laufzeit**, dies ist erforderlich zum Bereitstellen und steuern die Module in Ihrem Board:

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. An diesem Punkt werden Sie aufgefordert, öffnen Sie die *Config-Datei der Common Language Runtime*, zum Einfügen der **Device Connection String**, die Sie notiert (in Ihrem Editor), beim Erstellen der **IoT Hub-Dienst**  ([in Schritt 14, Kapitel 3](#chapter-3---the-iot-hub-service)). Führen Sie die folgende Zeile, auf das Terminal aus, um diese Datei öffnen:

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. Die **config.yaml** Datei werden angezeigt, für die Bearbeitung bereit:

    > [!WARNING]
    > Wenn diese Datei geöffnet wird, kann es etwas verwirrend sein. Sie werden zur Textbearbeitung dieser Datei in die *Terminal* selbst. 

    1.  Verwenden Sie die Pfeiltasten auf der Tastatur, um einen Bildlauf nach unten (Sie benötigen Sie einen Bildlauf eine kleine Methode), erreicht der Zeile mit ":

        "**\<GERÄTEVERBINDUNGSZEICHENFOLGE HIER HINZUFÜGEN &GT;**".

    2. Ersetzen der Zeile **einschließlich der Klammern**, mit der **Device Connection String** Sie zuvor notiert haben.

7. Mit der Verbindungszeichenfolge vorhanden, auf der Tastatur, und drücken Sie die **STRG + X** Schlüssel zum Speichern der Datei. Werden sie aufgefordert zu bestätigen, indem Sie die Eingabe **Y**. Drücken Sie dann die **EINGABETASTE** Schlüssel, um zu bestätigen. Sie kehren zurück zu den regulären *Terminal*. 

8. Nachdem diese Befehle alle erfolgreich ausgeführt haben, Sie installiert die **IoT Edge-Runtime**. Nach der Initialisierung der Runtime wird auf eine eigene jedes Mal, die das Gerät eingeschaltet wird gestartet und wird im Hintergrund, warten auf Module für die Bereitstellung befinden die **IoT Hub-Dienst**.

9.  Führen Sie die folgende Befehlszeile zum Initialisieren der *IoT Edge-Runtime*:

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > Wenn Sie die yaml-Datei, oder das oben beschriebene Setup ändern, müssen Sie in diesem Fall führen Sie die obige Zeile für den Neustart innerhalb *Terminal*.

10. Überprüfen Sie die *IoT Edge-Runtime* Status, indem Sie die folgende Befehlszeile ausführen. Die Laufzeit sollte angezeigt werden, mit dem Status **Active (aktiv)** in grüner Schrift.

    ```bash
        sudo systemctl status iotedge
    ```

11. Drücken Sie die **STRG + C** Schlüssel, um die Seite "Status" beendet. Sie können überprüfen, ob die *IoT Edge-Runtime* geladen Container ordnungsgemäß durch den folgenden Befehl eingeben:

    ```bash
        sudo docker ps
    ```

12. Eine Liste mit Containern zwei (2) sollte angezeigt werden. Hierbei handelt es sich um die Standardmodule, die vom IoT Hub-Dienst (EdgeAgent und EdgeHub) automatisch erstellt werden. Nachdem Sie erstellen und Ihrer eigenen Module bereitstellen, werden sie in dieser Liste, darunter die Standardfarben angezeigt.

## <a name="chapter-6---install-the-extensions"></a>Kapitel 6: Installieren der Erweiterungen

> [!IMPORTANT]
> Den nächsten Kapiteln (6 bis 9) sind auf Ihrem Windows 10-Computer ausgeführt werden.

1. Open **Vscode**.

2. Klicken Sie auf die **Erweiterungen** (Quadrat) Schaltfläche auf der linken Leiste von VS Code zum Öffnen der **Erweiterungsbereich**.

3. Suchen Sie nach, und installieren Sie, die folgenden Erweiterungen (wie in der folgenden Abbildung gezeigt):

    1. Azure IoT Edge
    2. Azure IoT Toolkit
    3. Docker   

    ![Erstellen Sie Ihres Containers](images/AzureLabs-Lab313-24.png)

4. Nachdem die Erweiterungen installiert sind, schließen Sie und erneut öffnen Sie Visual Studio Code.

5. Klicken Sie mit Visual Studio Code einmal öffnen, navigieren Sie zu **anzeigen > integriertes Terminal**.

6. Installieren Sie jetzt **Cookiecutter**. Führen Sie im Terminal den folgenden Bash-Befehl aus:

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! Hinweis] Wenn Sie schwierigkeiten mit dem folgenden Befehl: 
    >1. Starten Sie VS Code und / oder auf dem Computer neu.
    >2. Es kann erforderlich sein, wechseln die **VS Code-Terminal** mit dem Sie verwenden bereits, installieren Python, d. h. **Powershell** (insbesondere im Fall, dass die Python-Umgebung bereits auf Ihrem Computer installiert wurde). Das Terminal geöffnet ist finden Sie im Dropdown-Menü auf der rechten Seite des Terminals.
     ![Erstellen Sie Ihres Containers](images/AzureLabs-Lab313-24b.png) 
    >3. Stellen Sie sicher, dass die **Python** Installationspfad wurde als **Umgebungsvariable** auf Ihrem Computer. Cookiecutter muss Teil der gleichen Pfad zum Speicherort. Führen Sie dies [Link, um weitere Informationen zu den Umgebungsvariablen](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx), 

7. Einmal **Cookiecutter** wurde installiert, sollten Sie Ihre Computer neu starten, damit **Cookiecutter** als einen Befehl innerhalb des Systems Umgebung erkannt wird.

## <a name="chapter-7---create-your-container-solution"></a>Kapitel 7: Erstellen einer containerlösung

An diesem Punkt müssen Sie den Container zu erstellen, mit dem Modul in mithilfe von Push übertragen werden die *Containerregistrierung*. Nachdem Sie Ihren Container mithilfe von Push übertragen haben, verwenden Sie die *IoT Hub-Edge* Service sie auf Ihrem Gerät bereitstellen, die ausgeführt wird die *IoT Edge-Laufzeit*.

1. Klicken Sie in Visual Studio Code auf **Ansicht > befehlspalette**.

2. Suchen Sie in der Palette, und führen Sie **Azure IoT Edge: Neues Iot Edge-Projektmappe**.

3. Navigieren Sie an einem Speicherort, in der Sie Ihre Lösung erstellen möchten. Drücken Sie die **EINGABETASTE** Schlüssel, um den Speicherort zu akzeptieren.

4. Geben Sie einen Namen zu Ihrer Projektmappe ein. Drücken Sie die **EINGABETASTE** Schlüssel, um Ihre angegebene Name zu bestätigen.

5. Jetzt werden Sie aufgefordert werden, wählen Sie die Vorlage-Framework für Ihre Lösung. Klicken Sie auf **Python-Modul**. Drücken Sie die **EINGABETASTE** Schlüssel, um diese Auswahl zu bestätigen.

6. Geben Sie einen Namen für Ihr Modul ein. Drücken Sie die **EINGABETASTE** Schlüssel, um den Namen Ihres Moduls zu bestätigen. Stellen Sie sicher, dass sich (mit Ihrem Editor) den Namen des Moduls, zu nutzen, da sie später verwendet wird.

7. Sie sehen eine vorgefertigte *Docker-Image-Repository* Adresse wird auf der Palette angezeigt. Es sieht so aus wie:

    **Localhost:5000/der Namen von IHREM Modul -**. 

8. Löschen **Localhost:5000**, und in seiner Stelle einfügen der *Containerregistrierung* **Anmeldeserver** Adresse, die Sie notiert, beim Erstellen haben der **Container Registrierungsdienst** ([in Schritt 8, Kapitel 2](#chapter-2---the-container-registry-service)). Drücken Sie die **EINGABETASTE** Schlüssel, um die Adresse zu bestätigen.

9. An diesem Punkt wird die Lösung, mit der Vorlage für Ihre Python-Modul erstellt und in die Struktur angezeigt der **Registerkarte "Durchsuchen"**, der VS Code auf der linken Seite des Bildschirms. Wenn die **Registerkarte "Durchsuchen"** ist nicht geöffnet ist, können Sie sie öffnen auf die oberste Schaltfläche klicken, in der Leiste auf der linken Seite.

    ![Erstellen Sie Ihres Containers](images/AzureLabs-Lab313-25.png)

10. Der letzte Schritt zum diesem Kapitel wird, klicken Sie auf, und Öffnen der **env-Datei**, innerhalb der **Registerkarte "Durchsuchen"**, und fügen Ihre *Containerregistrierung* **Benutzername** und **Kennwort**. Diese Datei wird von Git ignoriert, aber zur Erstellung wird der Container, legen Sie die Anmeldeinformationen den Zugriff auf die **-Containerregistrierungsdienst**.

    ![Erstellen Sie Ihres Containers](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a>Kapitel 8 – bearbeiten Ihre containerlösung

Sie werden jetzt die Container-Lösung, schließen, indem Sie die folgenden Dateien werden aktualisiert:

- *Main<span></span>py* Python-Skript.
- *requirements.txt*.
- *deployment.template.json*.
- *Dockerfile.amd64*

Erstellen Sie dann die *Images* Ordner ein, das Python-Skript für die prüfen, ob Bilder für den Abgleich Ihrer *Modell für benutzerdefiniertes maschinelles sehen*. Fügen Sie abschließend die *labels.txt* -Datei, um Hilfe, lesen Sie das Modell und die *model.pb* -Datei, die das Modell ist.

1. Klicken Sie mit Visual Studio Code öffnen, navigieren Sie zu Ihrem Ordner "Module", und suchen Sie für das Skript mit dem Namen **main<span></span>py**. Doppelklicken Sie auf diese Option, um ihn zu öffnen.

2. Löschen Sie den Inhalt der Datei, und fügen Sie den folgenden Code:

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  Öffnen Sie die Datei mit dem Namen **"Requirements.txt"**, und Ersetzen Sie den Inhalt durch Folgendes:

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  Öffnen Sie die Datei mit dem Namen **deployment.template.json**, und Ersetzen Sie den Inhalt nach der folgenden Richtlinie:

    1. Da Sie Ihre eigenen, eindeutige, JSON-Struktur besitzt, müssen Sie es von hand bearbeiten (statt ein Beispiel für das Kopieren). Um dies zu vereinfachen, verwenden Sie die folgenden Abbildung als Anleitung.
    2. Bereiche, die mit Ihrer, anders aussehen, aber die Sie **sollte nicht geändert werden gelb hervorgehoben werden**.
    3. **Abschnitte, die Sie benötigen, löschen, werden ein rot hervorgehoben.**
    4. Achten Sie darauf, dass Sie die richtigen Klammern zu löschen, und auch entfernen Sie, die Kommas.

        ![Erstellen Sie Ihres Containers](images/AzureLabs-Lab313-27.png)

    5. Der vollständige JSON-Code sollte wie in der folgenden Abbildung aussehen (jedoch mit Ihrer eindeutigen unterschieden: *Benutzername/Kennwort/Modul Name/Modulverweisen*):

        ![Erstellen Sie Ihres Containers](images/AzureLabs-Lab313-28.png)

5.  Öffnen Sie die Datei mit dem Namen **Dockerfile.amd64**, und Ersetzen Sie den Inhalt durch Folgendes:

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  Mit der rechten Maustaste auf den Ordner, unter **Module** (er weist den Namen, die Sie zuvor; angegeben im Beispiel weiter nach unten, es heißt *Pythonmodule*), und klicken Sie auf **neuer Ordner**. Nennen Sie den Ordner **Images**.

7.  Fügen Sie dem Ordner einige Images, die mit der Maus oder Tastatur. Diese werden die Bilder, die durch das Tensorflow-Modell analysiert werden sollen.

    > [!WARNING]
    > Wenn Sie Ihr eigenes Modell verwenden, müssen Sie so ändern Sie diese Option, um Ihre eigenen Modelle Daten widerzuspiegeln.

8.  Sie müssen nun zum Abrufen der **labels.txt** und **model.pb** Dateien aus dem Modellordner, die Sie vorherige heruntergeladen haben (oder aus Ihren eigenen erstellt **Custom Vision Service** ), in [Kapitel 1](#chapter-1---retrieve-the-custom-vision-model). Nachdem Sie die Dateien haben, platzieren Sie sie in der Projektmappe zusammen mit den anderen Dateien. Das Endergebnis sollte wie folgt aussehen:

    ![Erstellen Sie Ihres Containers](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a>Kapitel 9 - Paket der Projektmappe als container

1.  Sie können nun "packen" die Dateien als Container und per push an Ihre **Azure Container Registry**. In VS Code öffnen die *integriertes Terminal* (**anzeigen > integriertes Terminal / STRG + '**), und verwenden Sie die folgende Zeile für die Anmeldung bei **Docker** (ersetzen Sie die Werte von der Befehl mit den Anmeldeinformationen Ihrer **Azure Container Registry (ACR)**):

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. Mit der rechten Maustaste auf die Datei **deployment.template.json**, und klicken Sie auf **IoT Edge-Projektmappe erstellen**. Dieser Build-Vorgang dauert einige Zeit (abhängig von Ihrem Gerät), also warten darauf vorbereitet sein. Nach Abschluss des Buildprozesses eine **"Deployment.JSON"** Datei wird in einen neuen Ordner namens erstellt wurden **Config**.

    ![Bereitstellung erstellen](images/AzureLabs-Lab313-30.png)

3. Öffnen der **Befehlspalette** erneut, und suchen Sie nach **Azure: Melden Sie sich bei**. Befolgen Sie die Anweisungen, die mit Ihren Azure-Konto-Anmeldeinformationen ein, Visual Studio Code erhalten Sie eine Option aus, um *kopieren und öffnen Sie*, werden die des Gerätecodes Sie bald benötigen, und öffnet Ihren Standardbrowser für das Web kopiert. Wenn Sie aufgefordert, fügen Sie den Gerätecode, um Ihren Computer zu authentifizieren.

    ![Kopieren und öffnen](images/AzureLabs-Lab313-31.png)

4. Einmal signierte in Sie werden feststellen, auf den unteren Rand der *Durchsuchen* Bereich einen neuen Abschnitt namens **Azure IoT Hub-Geräte**. Klicken Sie auf diesen Bereich, um ihn zu erweitern.

    ![Edge-Gerät](images/AzureLabs-Lab313-32.png)

5. Wenn Ihr Gerät nicht hier ist, müssen Sie mit der rechten Maustaste *Azure IoT Hub-Geräte*, und klicken Sie dann auf **IoT Hub-Verbindungszeichenfolge festlegen**. Klicken Sie dann sehen Sie, dass die **Befehlspalette** (oben auf der Visual Studio Code), fordert Sie zur Eingabe Ihrer *Verbindungszeichenfolge*. Dies ist die *Verbindungszeichenfolge* Sie am Ende der notiert [Kapitel 3](#chapter-3---the-iot-hub-service). Drücken Sie die **EINGABETASTE** Schlüssel, nachdem Sie die Zeichenfolge in kopiert haben.    

6. Ihr Gerät sollte geladen und angezeigt werden. Mit der rechten Maustaste auf den Gerätenamen, und klicken Sie dann auf, **Bereitstellung erstellen, für die einzelnen Gerät**.

    ![Bereitstellung erstellen](images/AzureLabs-Lab313-33b.png)

7. Erhalten Sie eine *Datei-Explorer* dazu aufgefordert werden, in dem Sie wechseln können, die **Config** Ordner, und wählen Sie dann die **"Deployment.JSON"** Datei. Mit dieser Datei ausgewählt haben, klicken Sie auf die **Edge-Bereitstellungsmanifest wählen** Schaltfläche.

    ![Bereitstellung erstellen](images/AzureLabs-Lab313-34.png)

8. Sie haben an diesem Punkt angegeben Ihre **IoT Hub-Dienst** mit dem Manifest für die Bereitstellung Ihres Containers und als Modul aus Ihrer **Azure Container Registry**effektiv auf Ihrem Gerät bereitstellen.

9. Um die von Ihrem Gerät an IoT Hub gesendete Nachrichten anzuzeigen, mit der rechten Maustaste erneut auf den Namen des Geräts in der **Azure IoT Hub-Geräte** im Abschnitt der **Explorer** Bereich, und klicken Sie auf **Überwachung starten D2C-Nachricht**. Die vom Gerät gesendeten Nachrichten in der Visual Studio-Terminal angezeigt. Geduld, dieser Vorgang kann einige Zeit dauern. Finden Sie im nächste Kapitel für das Debuggen, und überprüfen, ob die Bereitstellung erfolgreich war.

Dieses Modul wird jetzt leicht zwischen dem die Bilder in der **Images** Ordner und analysieren Sie sie bei jeder Iteration. Dies ist natürlich nur ein Beispiel, wie Sie die grundlegende Machine Learning-Modell funktioniert in einer Umgebung der IoT Edge-Gerät abrufen. 

Um die Funktionalität dieses Beispiels zu erweitern, können Sie auf verschiedene Arten fortfahren. Eine Möglichkeit kann Code in den Container, einschließlich werden, die Fotos von einer Webcam, die auf dem Gerät verbunden ist erfasst, und speichert die Bilder im Ordner "Images". 

Eine weitere Möglichkeit konnte die Bilder aus dem IoT-Geräte in den Container kopieren. Eine praktische Möglichkeit, dies ist auf den folgenden Befehl in der IoT-Geräte-Terminal ausführen (z. B. eine kleine app konnte den Auftrag werden Wenn Sie den Vorgang zu automatisieren). Sie können mit diesem Befehl testen, indem Sie sie manuell ausführen, über den Speicherort des Ordners, in dem Ihre Dateien gespeichert werden:

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a>Kapitel 10 – IoT Edge-Laufzeit-Debuggen

Im folgenden finden Sie eine Liste von Befehlszeilen und Tipps, zum Überwachen und Debuggen von der messaging-Aktivität von der *IoT Edge-Runtime*, aus Ihrem **Ubuntu-Gerät**. 

- Überprüfen Sie die *IoT Edge-Runtime* Status durch Ausführen der folgenden Befehlszeile:

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > Denken Sie daran, drücken die **STRG + C**, um den Vorgang abzuschließen, Anzeigen des Status.

- Listet die Container, die derzeit bereitgestellt werden. Wenn die *IoT Hub-Dienst* Container wurde erfolgreich bereitgestellt. sie werden durch Ausführen der folgenden Befehlszeile angezeigt werden:

    ```bash
        sudo iotedge list
    ```

    Oder

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > Die oben genannten ist eine gute Möglichkeit zum Überprüfen, ob Ihr Modul erfolgreich bereitgestellt wurde, wie er in der Liste angezeigt wird. Andernfalls werden **nur** finden Sie unter den *EdgeHub* und *EdgeAgent*.

- Um die Protokolle der Code eines Containers zu anzuzeigen, führen Sie die folgende Befehlszeile ein:

    ```bash
        journalctl -u iotedge
    ```

**Hilfreiche Befehle zum Verwalten der IoT Edge-Runtime:**

-  So löschen Sie alle Container auf dem Host:

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  Zum Beenden der *IoT Edge-Runtime*:

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a>Kapitel 11: Erstellen der Tabellendienst 

Navigieren Sie zurück zu Ihrem Azure-Portal, in dem Sie eine Azure-Tabellen-Dienst, vom Erstellen einer Speicherressource erstellen.

1. Wenn nicht bereits angemeldet, melden Sie sich bei der [Azure-Portal](https://portal.azure.com).

2. Sobald Sie angemeldet sind, klicken Sie auf **erstellen Sie eine Ressource**, klicken Sie in der oberen linken Ecke, und suchen Sie nach **Speicherkonto**, und drücken Sie die **EINGABETASTE** Schlüssel, mit der Suche begonnen.

3. Wenn es angezeigt wurde, klicken Sie auf **Speicherkonto – Blob, Datei, Tabelle, Warteschlange** aus der Liste.

    ![Suchen Sie nach dem Storage-Konto](images/AzureLabs-Lab313-35.png)

4. Die neue Seite bietet eine Beschreibung der **Speicherkonto** Service. Unten links der Aufforderung, klicken Sie auf die **erstellen** Schaltfläche, um eine Instanz dieses Diensts erstellen.

    ![Storage-Instanz erstellen](images/AzureLabs-Lab313-36.png)

5. Nachdem Sie auf geklickt haben **erstellen**, wird ein Panel angezeigt:

    1. Fügen Sie Ihre bevorzugte **Namen** für diese Dienstinstanz (*müssen Kleinbuchstaben sein*).

    2. Für **Bereitstellungsmodell**, klicken Sie auf **RM**.

    3. Für **Kontoart**, klicken Sie im Dropdownmenü mit **Speicher (Allgemein v1)**.

    4. Klicken Sie auf einen geeigneten **Speicherort**.
    
    5. Für die **Replikation** Dropdown-Menü, klicken Sie auf **Read-Access-georedundanter Speicher (RA-GRS)**.

    6. Für **Leistung**, klicken Sie auf **Standard**.

    7. In der **sichere Übertragung erforderlich** auf **deaktiviert**.

    8. Von der **Abonnement** Dropdown-Menü, klicken Sie auf ein entsprechendes Abonnement.

    9. Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, bereitzustellen und zu verwalten, Rechnungen für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle zu bewahren, an die Azure-Dienste unter einer allgemeinen Ressourcengruppe mit einem einzelnen Projekt (z. B. z. B. diese Kurse) verknüpft ist).

        > Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, befolgen Sie diese [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. Lassen Sie **virtuelle Netzwerke** als **deaktiviert**, ist dies eine Option für Sie.

    11. Klicken Sie auf **Erstellen**.

        ![Geben Sie im Storage-details](images/AzureLabs-Lab313-37.png)

6. Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.

7. Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt. Klicken Sie auf die Benachrichtigungen an Ihre neue Dienstinstanz zu untersuchen.

    ![neue Speicher-Benachrichtigung](images/AzureLabs-Lab313-38.png)

8. Klicken Sie auf die **zu Ressource wechseln** Schaltfläche in die Benachrichtigung, und Sie gelangen auf Ihre neue Übersichtsseite für den Speicherdienst-Instanz.

    ![zu Ressource wechseln](images/AzureLabs-Lab313-39.png)

9. Klicken Sie auf der Seite "Übersicht" auf der rechten Seite auf **Tabellen**.
    
    ![Tabellen](images/AzureLabs-Lab313-40.png)

10. Bereich auf der rechten Seite wird geändert, um das Anzeigen der **Tabellendienst** Informationen, bei dem Sie eine neue Tabelle hinzufügen möchten. Durch Klicken auf die **+ Tabelle** Schaltfläche auf der linken oberen Ecke.

    ![Öffnen von Tabellen](images/AzureLabs-Lab313-41.png)

11. Eine neue Seite wird angezeigt, in dem Sie eingeben müssen, eine **Tabellenname**. Dies ist der Name, den Sie verwenden, um auf die Daten in Ihrer Anwendung in späteren Kapiteln (Erstellen von Funktionen-App und Power BI) verweisen. Fügen Sie **IoTMessages** als Name (Sie können Ihre eigenen auswählen Denken Sie bei einem späteren Zeitpunkt in diesem Dokument verwendet), und klicken Sie auf **OK**. 

12. Sobald die neue Tabelle erstellt wurde, Sie werden in finden Sie unter den **Tabellendienst** Seite (unten).

    ![neue Tabelle](images/AzureLabs-Lab313-42.png)  

13. Klicken Sie nun auf **Zugriffsschlüssel** und eine Kopie der **speicherkontonamen** und **Schlüssel** (mit dem Ihr Editor), verwenden Sie diese Werte später in diesem Kurs, beim Erstellen der **Azure Functions-App**.

    ![neue Tabelle](images/AzureLabs-Lab313-43.png) 

14. Verwenden den Bereich in diesem Fall auf der linken Seite einen Bildlauf zu der *Tabellendienst* aus, und klicken Sie auf **Tabellen** (oder **Tabellen durchsuchen**, in neueren Portalen) und eine Kopie der  **Tabelle URL** (mit dem Ihr Editor). Verwenden Sie diesen Wert später in diesem Kurs, beim Verknüpfen der Tabelle auf Ihre **Power BI** Anwendung.

    ![neue Tabelle](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a>Kapitel 12 – Abschließen der Azure-Tabelle

Nachdem Ihre **Tabellendienst** Storage-Konto eingerichtet haben, ist es Zeit zum Hinzufügen von Daten, die zum Speichern und Abrufen von Informationen verwendet wird. Die Bearbeitung Ihrer Tabellen kann über erfolgen **Visual Studio**.

1. Open **Visual Studio** (**nicht** Visual Studio-Code).

2. Klicken Sie im Menü auf **Ansicht > Cloud-Explorer**.

    ![Öffnen Sie den Cloud-explorer](images/AzureLabs-Lab313-45.png)

3. Die **Cloud-Explorer** öffnet als angedockte Element (Geduld, Laden von Zeit in Anspruch).

    > [!WARNING] 
    > Wenn das Abonnement, das Sie zum Erstellen verwendet Ihre *Speicherkonten* ist nicht sichtbar ist, sicherzustellen, dass Sie: 
    > - Angemeldet um dasselbe Konto wie diejenige aus, die Sie für das Azure-Portal verwendet.
    > - Ihr Abonnement aus der Account Management-Seite (möglicherweise müssen einen Filter aus den Einstellungen Ihres Kontos anwenden) ausgewählt:  
    >
    >   ![Suchen Sie nach Abonnement](images/AzureLabs-Lab313-46.png)

4. Ihre Azure-Cloud-Dienste werden angezeigt. Suchen **Speicherkonten** , und klicken Sie auf den Pfeil auf der linken Seite, um Ihre Konten zu erweitern.

    ![Öffnen Sie Storage-Konten](images/AzureLabs-Lab313-47.png)

5. Nach der Kategorie erweitert ist, das neu erstellte **Speicherkonto** verfügbar sein sollen. Klicken Sie auf den Pfeil auf der linken Seite des Speichers, und klicken Sie dann nach, die erweitert wird, finden **Tabellen** , und klicken Sie auf den Pfeil neben der, dass zum Anzeigen der **Tabelle** Sie im letzten Abschnitt erstellt haben. Doppelklicken Sie auf Ihre **Tabelle**.

6. Die Tabelle wird in der Mitte des Ihrer Visual Studio-Fenster geöffnet. Klicken Sie auf das Tabellensymbol "mit der **+** (plus) auf.

    ![neue Tabelle hinzufügen](images/AzureLabs-Lab313-48.png)

7. Ein Fenster wird aufgefordert wird angezeigt, Sie *Entität hinzufügen*. Erstellen Sie nur eine Entität, wenn es drei Eigenschaften hat. Sie werden feststellen, dass *PartitionKey* und *RowKey* werden soll, bereits bereitgestellt ist, als diese von der Tabelle verwendet werden, um Ihre Daten zu finden. 

    ![Partitions-und zeilenschlüssels](images/AzureLabs-Lab313-49.png)

8. Aktualisieren Sie die folgenden Werte ein:

    - Name: **PartitionKey**, Value: **PK_IoTMessages** 

    - Name: **RowKey**, Value: **RK_1_IoTMessages** 

9. Klicken Sie auf **Eigenschaft hinzufügen** (unten links in der die *Entität hinzufügen* Fenster), und fügen Sie die folgende Eigenschaft hinzu:

    - **MessageContent**, als eine *Zeichenfolge*, den Wert leer lassen.

10. Die Tabelle sollte in der folgenden Abbildung entsprechen:

    ![Fügen Sie die richtigen Werte](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > Der Grund, warum die Entität die Zahl 1 in der Zeilenschlüssel ist, da es sich bei hinzuzufügenden möglicherweise Nachrichten mehr anzeigt, sollten Sie wünschen, Experimentieren mit diesem Kurs.

11. Klicken Sie anschließend auf **OK**. Die Tabelle kann jetzt verwendet werden.

## <a name="chapter-13---create-an-azure-function-app"></a>Kapitel 13 – erstellen eine Azure-Funktions-App 

Ist es jetzt Zeit zum Erstellen einer *Azure Function-App*, wird aufgerufen, indem die *IoT Hub-Dienst* zum Speichern der *IoT Edge* Gerät-Nachrichten der **Tabelle** -Dienst, die Sie im vorherigen Kapitel erstellt haben.

Zunächst müssen Sie eine Datei zu erstellen, mit dem Ihre Azure-Funktion, die Bibliotheken zu laden, die Sie benötigen.

1.  Open **Editor** (drücken Sie die *Windows-Taste*, und geben *Editor*).

    ![Öffnen Sie Editor](images/AzureLabs-Lab313-51.png)

2.  Legen Sie mit dem Editor öffnen die folgende JSON-Struktur, in es. Sobald Sie dies getan haben, speichern Sie es auf Ihrem Desktop als **"Project.JSON"**. Diese Datei definiert die Bibliotheken, die Ihre Funktion verwenden werden. Wenn Sie NuGet verwendet haben, sieht er vertraut.
    
    > [!WARNING]
    > Es ist wichtig, dass die Benennung korrekt ist. Stellen Sie sicher, es ist **keine txt** Dateierweiterung. Finden Sie weiter unten als Referenz:
    >
    > ![JSON speichern](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  Melden Sie sich bei der [Azure-Portal](https://portal.azure.com).

4.  Sobald Sie angemeldet sind, klicken Sie auf **erstellen Sie eine Ressource** in der oberen linken Ecke, und suchen Sie nach **Funktions-App**, und drücken Sie die **EINGABETASTE** Schlüssel handelt, suchen. Klicken Sie auf *Funktions-App* aus den Ergebnissen aus, um ein neuer Bereich geöffnet.

    ![Suchen Sie nach der Funktions-app](images/AzureLabs-Lab313-53.png)

5.  Der nächste neue Bereich bietet eine Beschreibung der **Funktions-App** Service. Unten links von diesem Bereich, klicken Sie auf die **erstellen** Schaltfläche, um eine Zuordnung mit diesem Dienst zu erstellen.

    ![Funktionen-app-Instanz](images/AzureLabs-Lab313-54.png)

6.  Nachdem Sie auf geklickt haben **erstellen**, geben Sie Folgendes:

    1. Für **Anwendungsnamen**, fügen Sie dem gewünschten Namen für diese Dienstinstanz.

    2. Wählen Sie eine **Abonnement**.

    3. Wählen Sie der Tarif für Sie geeignet, ist dies das erste Mal erstellen eine **-Funktion von App Service**, freier-Tarif für Sie verfügbar sein sollen.

    4. Wählen Sie eine **Ressourcengruppe** oder ein neues erstellen. Eine Ressourcengruppe bietet eine Möglichkeit zum Überwachen, Steuern des Zugriffs, bereitzustellen und zu verwalten, Rechnungen für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle zu bewahren, an die Azure-Dienste unter einer allgemeinen Ressourcengruppe mit einem einzelnen Projekt (z. B. z. B. diese Kurse) verknüpft ist).

        > Wenn Sie, um weitere Informationen möchten zu Azure-Ressourcengruppen, befolgen Sie diese [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Für **OS**, Windows, klicken Sie auf, da dies die angezielte Plattform ist.

    6. Wählen Sie eine **Hostingplan** (in diesem Tutorial verwendet ein **Verbrauchstarif**.

    7. Wählen Sie eine **Speicherort** (Wählen Sie im vorherigen Schritt am gleichen Speicherort wie der Speicher, die Sie erstellt haben)

    8. Für die **Storage** Abschnitt **müssen Sie den Storage-Dienst, die Sie im vorherigen Schritt erstellt haben, auswählen**.

    9. Sie müssen keine *Application Insights* in dieser app können daher gerne bleibt bestehen **aus**.

    10. Klicken Sie auf **Erstellen**.

        ![neue Instanz erstellen](images/AzureLabs-Lab313-55.png)

7.  Nachdem Sie auf geklickt haben **erstellen**, müssen Sie warten, bis der Dienst erstellt werden, dies kann einen Moment dauern.

8.  Nachdem die Dienstinstanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![Neue Benachrichtigung](images/AzureLabs-Lab313-56.png)

9.  Klicken Sie auf auf die Benachrichtigung, sobald die Bereitstellung erfolgreich abgeschlossen wurde (Abschluss).

10. Klicken Sie auf die **zu Ressource wechseln** in der Benachrichtigung aus, um Ihre neue Dienstinstanz zu untersuchen. 

    ![zu Ressource wechseln](images/AzureLabs-Lab313-57.png)

11. Klicken Sie auf der linken Seite des neuen Bereichs, auf die **+** (Pluszeichen) Symbol neben dem *Funktionen*, um eine neue Funktion zu erstellen.

    ![Fügen Sie neue Funktion](images/AzureLabs-Lab313-58.png)

12. Klicken Sie im mittleren Bereich der **Funktion** Erstellung-Fenster wird angezeigt. Scrollen Sie weiter, und klicken Sie auf **benutzerdefinierte Funktion**.

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-59.png)

13. Bildlauf nach unten in der nächsten Seite, bis Sie gefunden **IoT Hub (Event Hub)**, klicken Sie dann darauf.

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-60.png)

14. In der **IoT Hub (Event Hub)** legen Sie auf dem Blatt der **Sprache** zu **C#** , und klicken Sie dann auf **neue**.

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-61.png)

15. Im Fenster, das angezeigt wird, stellen sicher, dass **IoT Hub** ausgewählt ist und den Namen des der *IoT Hub* Feld entspricht, durch den Namen des Ihre *IoT Hub-Dienst* , die Sie zuvor erstellt haben ([in Schritt 8, Kapitel 3](#chapter-3---the-iot-hub-service)). Klicken Sie dann auf die **wählen** Schaltfläche.

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-62.png)

16. Auf der **IoT Hub (Event Hub)** auf, klicken Sie auf dem Blatt **erstellen**.

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-63.png)

17. Sie werden auf der Funktions-Editor weitergeleitet.

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-64.png)

18. Löschen Sie der gesamte Code in diese zu, und Ersetzen Sie ihn durch Folgendes:

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. Ändern Sie die folgenden Variablen, damit sie auf die entsprechenden Werte entsprechen (**Tabelle** und **Storage** Werte aus [Schritt 11 und 13, bzw. der Kapitel 11](#chapter-11---create-table-service)), die finden Sie in Ihrem **Speicherkonto**:

    - **TableName**, durch den Namen Ihrer **Tabelle** befindet sich in Ihre **Speicherkonto**.
    - **TableURL**, durch die URL Ihrer **Tabelle** befindet sich in Ihre **Speicherkonto**.
    - **"storageaccountname"**, mit dem Namen des durch den Namen des entsprechenden Werts Ihrer **Speicherkonto** Name.
    - **"storageaccountkey"**, mit dem Schlüssel, die Sie erworben haben, in den Storage-Dienst, die Sie zuvor erstellt haben.

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-65.png)

20. Mit diesem Code, klicken Sie auf **speichern**.

21. Klicken Sie anschließend die **\<** Symbol auf der rechten Seite der Seite (Pfeil).

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-66.png)

22. Ein Panel wird in der rechten Seite schieben. In diesem Bereich, klicken Sie auf **hochladen**, und ein *Dateibrowser* wird angezeigt.

23. Navigieren Sie zu, und klicken Sie auf, die **"Project.JSON"** -Datei, die Sie in erstellt haben **Editor** zuvor, und klicken Sie dann auf die **öffnen** Schaltfläche. Diese Datei definiert die Bibliotheken, die Ihre Funktion verwendet werden.

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-67.png)

24. Wenn die Datei hochgeladen wurde, wird es im Bereich auf der rechten Seite angezeigt. Klicken sie auf, öffnen sie in der **Funktion** Editor. Es muss aussehen **genau** identisch mit der nächsten Abbildung.

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-68.png)

25. An diesem Punkt das wäre allerdings gut zum Testen der Funktion Ihrer Funktion zum Speichern der Nachricht auf Ihrer *Tabelle*. Klicken Sie auf der oberen rechten Seite des Fensters auf **Test**.

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-69.png)

26. Einfügen einer Nachricht auf der **Anforderungstext**, wie in der obigen Abbildung, und klicken Sie auf auf dargestellt **ausführen**. 

27. Die Funktion ausgeführt wird, den Ergebnisstatus anzeigen (Sie werden feststellen, die grüne **Status 202 Accepted**weiter oben die *Ausgabe* Fenster bezeichnet, es wurde ein erfolgreicher Aufruf):

    ![Ergebnis der Ausgabe](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a>Kapitel 14 – Anzeigen von aktiven Nachrichten

Wenn Sie jetzt Visual Studio öffnen (**nicht** Visual Studio Code), können Sie Ihre Nachricht Testergebnis visualisieren, wie es in gespeichert werden, die *MessageContent* Bereich Zeichenfolge.

![benutzerdefinierte Funktion](images/AzureLabs-Lab313-71.png)

Mit dem Tabellendienst und die Funktionen-App vorhanden, werden Ihr Ubuntu-Gerät-Nachrichten angezeigt, Ihre *IoTMessages* Tabelle. Wenn nicht bereits ausgeführt wird, starten Sie Ihr Gerät erneut, und die ergebnisnachrichten von Ihrem Gerät und Modul in der Tabelle anzeigen, über mithilfe von Visual Studio können *Cloud-Explorer*.

![Visualisieren von Daten](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a>Kapitel 15 – Power BI-Setup

Zum Visualisieren von Daten aus Ihrem IOT-Gerät Sie richtet **Power BI** (Desktopversion), zum Erfassen der Daten aus der *Tabelle* -Dienst, der Sie gerade erstellt haben. Die *HoloLens* Version von Power BI verwendet dann diese Daten, um die Ergebnisse zu visualisieren.

1.  Öffnen Sie den Microsoft Store für Windows 10, und suchen Sie nach **Power BI Desktop**.

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  Laden Sie die Anwendung. Sobald der Download abgeschlossen ist, öffnen Sie es aus.

3.  Melden Sie sich bei *Power BI* mit Ihrem **Microsoft 365-Konto**. Sie können an einen Browser, um sich registrieren umgeleitet werden. Sobald Sie angemeldet sind, wechseln Sie zurück zu Power BI-app, und melden Sie sich erneut.

4.  Klicken Sie auf **Datenabruf** , und klicken Sie dann auf **mehr...** .

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  Klicken Sie auf **Azure**, **Azure Table Storage**, klicken Sie dann auf **Connect**.

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  Werden Sie aufgefordert, fügen Sie der **adresa URL Tabulky** , die Sie zuvor erfasst ([in Schritt 13 der Kapitel 11](#chapter-11---create-table-service)), während der Erstellung Ihrer. Löschen Sie nach dem Einfügen der URL, die Teil des Pfads, die auf die Tabelle "Unterordner" (die IoTMessages, in diesem Kurs war). Das Endergebnis sollte sein, wie in der folgenden Abbildung angezeigt. Klicken Sie dann auf **OK**.

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  Werden Sie aufgefordert, fügen Sie der **Speicherschlüssel** , die Sie notiert haben ([in Schritt 11 des Kapitel 11](#chapter-11---create-table-service)) weiter oben beim Erstellen von Ihrem Tabellenspeicher. Klicken Sie dann auf **Connect**.

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. Ein **Bereich "Navigator"** angezeigt wird, aktivieren Sie das Kontrollkästchen neben der Tabelle aus, und klicken Sie auf **Load**.

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. Die Tabelle jetzt in Power BI geladen wurde, aber es erfordert, dass eine Abfrage aus, um die Werte darin anzuzeigen. Dazu, mit der Maustaste auf den Tabellennamen in der **Felder Bereich** auf der rechten Seite des Bildschirms. Klicken Sie dann auf **Abfrage bearbeiten**.

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. Ein **Power Query-Editor** wird als ein neues Fenster, das Anzeigen Ihrer Tabelle geöffnet. Klicken Sie auf das Wort **Datensatz** innerhalb der *Inhalt* -Spalte der Tabelle, um Ihre Inhalte zu visualisieren.

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. Klicken Sie auf **Into Tabelle**, an der oberen linken Ecke des Fensters. 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. Klicken Sie auf **schließen und übernehmen**.

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. Sobald es abgeschlossen ist, laden die Abfrage, in der **Felder Bereich**, auf der rechten Seite des Bildschirms, aktivieren Sie die Kontrollkästchen für die Parameter **Namen** und **Wert**zu Visualisieren der **MessageContent** Spalteninhalt.

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. Klicken Sie auf die **blaue Datenträgersymbol** am oben links im Fenster zum Speichern Ihrer Arbeit in einem Ordner Ihrer Wahl.

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. Sie können jetzt auf die Schaltfläche "Veröffentlichen" zum Hochladen von der Tabelle in Ihrem Arbeitsbereich klicken. Wenn Sie dazu aufgefordert werden, klicken Sie auf **Arbeitsbereich** , und klicken Sie auf *wählen*. Warten Sie, um das erfolgreiche Ergebnis der Übermittlung anzuzeigen.

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> Im folgende Kapitel ist bestimmte HoloLens. Powerbi ist zurzeit nicht zur Verfügung als immersive Anwendung, aber im Windows Mixed Reality-Portal (auch bekannt als Cliff House), die desktop-Version ausgeführt werden kann durch die Desktop-app.

## <a name="chapter-16---display-power-bi-data-on-hololens"></a>Kapitel 16 – zeigen Sie Power BI-Daten in HoloLens

1. Auf Ihre HoloLens, melden Sie sich bei der **Microsoft Store**, durch Tippen auf das Symbol in der Anwendungsliste den Eintrag.

    ![Power BI HL](images/AzureLabs-Lab313-87.png)

2. Suchen und laden die **Power BI** Anwendung.

    ![Power BI HL](images/AzureLabs-Lab313-88.png)

3. Starten Sie **Power BI** aus der Anwendungsliste. 

4. **Power BI** möglicherweise Fragen Sie sich anmelden, Ihr **Microsoft 365-Konto**.

5. Einmal sollte innerhalb der app der Arbeitsbereich wird standardmäßig angezeigt werden wie in der folgenden Abbildung dargestellt. Wenn, das nicht geschieht, klicken Sie einfach auf das Symbol für den Arbeitsbereich auf der linken Seite des Fensters.

    ![Power BI HL](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a>Ihre fertige Ihrer IoT Hub-Anwendung

Herzlichen Glückwunsch, Sie haben erfolgreich einen IoT Hub-Dienst, mit einem simulierten Virtual Machine-Edge-Gerät erstellt. Ihr Gerät kommunizieren kann, die Ergebnisse eines Machine learning-Modell in ein Azure-Tabellendienst, die von einer Azure-Funktionen-App, die in Power BI gelesen und in einer Microsoft HoloLens visualisiert bereitgestellt wird.
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a>Bonus-Übungen

### <a name="exercise-1"></a>Übung 1

Erweitern Sie die messaging-Struktur in der Tabelle gespeichert, und als Diagramm anzuzeigen. Sie möchten möglicherweise weitere Daten sammeln und speichern Sie sie in der gleichen Tabelle, zu einem späteren Zeitpunkt angezeigt werden soll.

### <a name="exercise-2"></a>Übung 2

Erstellen Sie eine weitere "Camera Capture"-Modul auf dem IoT-Board bereitgestellt werden, damit sie Images erfassen kann, durch die Kamera analysiert werden.
