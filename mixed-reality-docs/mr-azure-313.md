---
title: Mr und Azure 313-IOT Hub Service
description: In diesem Kurs erfahren Sie, wie Sie Azure IOT Hub-Dienst auf einem virtuellen Computer mit Ubuntu 16,4 implementieren und anschließend die Nachrichten Daten mithilfe von Microsoft hololens oder einem immersiven (VR)-Headset visualisieren.
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Edge, IOT Edge, Tutorial, API, Benachrichtigung, Funktionen, Tabellen, hololens, immersive, VR, IOT, virtueller Computer, Ubuntu, python
ms.openlocfilehash: 7f56c7931bb036d14ab3aa9156706b1f6247195c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437964"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es gibt eine neue Reihe von Tutorials, die in Zukunft veröffentlicht werden, um die Entwicklung für hololens 2 zu veranschaulichen.  Dieser Hinweis wird mit einem Link zu diesen Tutorials aktualisiert, wenn diese veröffentlicht werden.

# <a name="mr-and-azure-313-iot-hub-service"></a>Mr und Azure 313: IOT Hub-Dienst

![Kurs Ergebnis](images/AzureLabs-Lab313-00.png)

In diesem Kurs erfahren Sie, wie Sie eine **Azure IOT Hub Service** auf einem virtuellen Computer implementieren, auf dem das Betriebssystem Ubuntu 16,4 ausgeführt wird. Ein **Azure-Funktionen-App** wird dann zum Empfangen von Nachrichten von Ihrer Ubuntu-VM verwendet und speichert das Ergebnis in einem **Azure-Tabellen Speicherdienst**. Anschließend können Sie diese Daten mithilfe von **Power BI** auf dem Microsoft hololens oder im immersiven (VR)-Headset anzeigen.

Der Inhalt dieses Kurses gilt für IOT Edge Geräte, aber im Rahmen dieses *Kurses liegt der* Schwerpunkt auf der Umgebung eines virtuellen Computers, sodass der Zugriff auf ein physisches Edgegerät nicht erforderlich ist.

Wenn Sie diesen Kurs abschließen, lernen Sie Folgendes:

- Stellen Sie ein **IOT Edge Modul** auf einem virtuellen Computer (Ubuntu 16 OS) bereit, der ihr IOT-Gerät darstellt.
- Fügen Sie dem Edge-Modul ein **Azure Custom Vision tensorflow-Modell** mit Code hinzu, mit dem im Container gespeicherte Images analysiert werden.
- Richten Sie das Modul ein, um die Analyseergebnis Nachricht zurück an den **IOT Hub-Dienst**zu senden.
- Verwenden Sie eine **Azure-Funktionen-App** , um die Nachricht in einer Azure- **Tabelle**zu speichern.
- Richten Sie **Power BI** ein, um die gespeicherte Nachricht zu erfassen und einen Bericht zu erstellen.
- Visualisieren Sie Ihre IOT-Nachrichten Daten in **Power BI**.

Zu den Diensten, die Sie verwenden werden, gehören:

- **Azure IOT Hub** ist ein Microsoft Azure Dienst, mit dem Entwickler IOT-Assets verbinden, überwachen und verwalten können. Weitere Informationen finden Sie auf der [Seite **Azure IOT Hub-Dienst** ](https://azure.microsoft.com/services/iot-hub/).

- **Azure Container Registry** ist ein Microsoft Azure Dienst, der Entwicklern das Speichern von Container Images für verschiedene Containertypen ermöglicht. Weitere Informationen finden Sie auf der [Seite **Azure Container Registry-Dienst** ](https://azure.microsoft.com/services/container-registry/).

- Bei **Azure Funktionen-App** handelt es sich um einen Microsoft Azure Dienst, der es Entwicklern ermöglicht, in Azure kleine Code Elemente, "Functions", auszuführen. Dies bietet eine Möglichkeit zum Delegieren von Arbeit an die Cloud und nicht an Ihre lokale Anwendung, die viele Vorteile haben kann. **Azure Functions** unterstützt mehrere Entwicklungs Sprachen, wie z. b. C\#, F\#, Node. js, Java und PHP. Weitere Informationen finden Sie auf der [Seite **Azure Functions** ](https://docs.microsoft.com/azure/azure-functions/functions-overview).

- **Azure Storage: Tabellen** sind ein Microsoft Azure Dienst, mit dem Entwickler strukturierte, nicht-SQL-Daten in der Cloud speichern können, sodass Sie überall problemlos zugänglich sind. Der Dienst verfügt über einen Schema losen Entwurf, der die Weiterentwicklung von Tabellen nach Bedarf ermöglicht und daher sehr flexibel ist. Weitere Informationen finden Sie auf der Seite mit den [ **Azure-Tabellen** .](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

In diesem Kurs erfahren Sie, wie Sie den IOT Hub-Dienst einrichten und verwenden und dann eine Antwort visualisieren, die von einem Gerät bereitgestellt wird. Sie müssen diese Konzepte auf eine benutzerdefinierte IOT Hub Service-Einrichtung anwenden, die Sie möglicherweise erstellen.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td> Mr und Azure 313: IOT Hub-Dienst</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Voraussetzungen

Aktuelle Voraussetzungen für die Entwicklung mit gemischter Realität, einschließlich der Microsoft hololens, finden Sie im Artikel [Installieren der Tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) .

> [!NOTE]
> Dieses Lernprogramm ist für Entwickler konzipiert, die über die grundlegende Verwendung von python verfügen. Beachten Sie auch, dass die Voraussetzungen und Anweisungen in diesem Dokument darstellen, was zum Zeitpunkt des Schreibens getestet und überprüft wurde (Juli 2018). Sie können die neueste Software verwenden, die im Artikel [Installieren der Tools](install-the-tools.md) aufgeführt ist. es sollte jedoch nicht davon ausgegangen werden, dass die Informationen in diesem Kurs genau mit den Informationen in neueren Software vergleichen, als im folgenden aufgeführt sind.

Folgende Hardware und Software ist erforderlich:

- Windows 10 Fall Creators Update (oder höher), **Entwicklermodus aktiviert**

    > [!WARNING]
    > Es ist nicht möglich, einen virtuellen Computer mit Hyper-V unter Windows 10 Home Edition auszuführen.

- Windows 10 SDK (neueste Version)
- Hololens, **Entwicklermodus aktiviert**
- Visual Studio 2017.15.4 (nur für den Zugriff auf die Azure-Cloud-Explorer verwendet)
- Internet Zugriff für Azure und für IOT Hub-Dienst. Weitere Informationen finden Sie [unter diesem Link zur IOT Hub Dienst Seite](https://azure.microsoft.com/services/iot-hub/) .
- Ein Machine Learning-Modell. Wenn Sie nicht über ein eigenes Modell verfügen, [können Sie das mit diesem Kurs bereitgestellte Modell verwenden](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).
- Auf Ihrem Windows 10-Entwicklungs Computer ist **Hyper-V-** Software aktiviert.
- Ein virtueller Computer, auf dem Ubuntu (16,4 oder 18,4) ausgeführt wird und der auf dem Entwicklungs Computer ausgeführt wird. Alternativ können Sie einen separaten Computer mit Linux (Ubuntu 16,4 oder 18,4) verwenden. Weitere Informationen zum Erstellen eines virtuellen Computers unter Windows mit Hyper-V finden Sie im [Kapitel "bevor Sie beginnen"](#before-you-start). (https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).  



### <a name="before-you-start"></a>Bevor Sie beginnen

1. Richten Sie Ihre hololens ein, und testen Sie Sie. Wenn Sie Unterstützung für die Einrichtung ihrer hololens benötigen, [besuchen Sie den Artikel zum Einrichten von hololens](https://docs.microsoft.com/hololens/hololens-setup).
2. Es empfiehlt sich, eine **Kalibrierung** und **Sensor** Optimierung durchzuführen, wenn Sie mit der Entwicklung einer neuen hololens-App beginnen (manchmal kann es hilfreich sein, diese Aufgaben für jeden Benutzer auszuführen).

Hilfe zur Kalibrierung finden Sie unter diesem [Link zum Artikel zur hololens-Kalibrierung](calibration.md#hololens-2).

Hilfe zur Sensor Optimierung finden Sie unter diesem [Link zum Artikel zur Überwachung von hololens-Sensoren](sensor-tuning.md).

3. Richten Sie Ihren **virtuellen Ubuntu-Computer** mithilfe von **Hyper-V**ein. Die folgenden Ressourcen helfen Ihnen bei diesem Vorgang.
    1.  Befolgen Sie zuerst den folgenden Link, um die ISO-Datei von [Ubuntu 16.04.4 LTS (xenial Xerus) herunterzuladen](https://au.releases.ubuntu.com/16.04/). Wählen Sie das **amd64-Desktop Image (64-Bit-PC)** aus.
    2.  Stellen Sie sicher, dass **Hyper-V** auf Ihrem Windows 10-Computer aktiviert ist. Unter diesem Link finden Sie Anleitungen zum [Installieren und Aktivieren von Hyper-V unter Windows 10](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).
    3.  Starten Sie Hyper-V, und erstellen Sie einen neuen virtuellen Ubuntu-Computer. Unter diesem Link finden Sie eine Schritt-für- [Schritt-Anleitung zum Erstellen eines virtuellen Computers mit Hyper-V](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine). Wenn Sie die **Option "Betriebssystem von einer Start baren Image Datei installieren"** angefordert haben, wählen Sie die zuvor heruntergeladene **Ubuntu-ISO** -Datei aus.

    > [!NOTE]
    > Die Verwendung von **Hyper-V Quick Create** ist nicht empfehlenswert.  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a>Kapitel 1: Abrufen des Custom Vision Modells

In diesem Kurs haben Sie Zugriff auf ein [vorgefertigter Custom Vision Modell](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) , das Tastaturen und Mäuse von Bildern erkennt. Wenn Sie diese verwenden, fahren Sie mit [Kapitel 2](#chapter-2---the-container-registry-service)fort.

Sie können jedoch die folgenden Schritte ausführen, wenn Sie Ihr eigenes Custom Vision Modell verwenden möchten:

1. Wechseln Sie in Ihrem **Custom Vision Projekt** zur Registerkarte **Leistung** .

    > [!WARNING]
    > Ihr Modell muss eine *kompakte* Domäne verwenden, um das Modell zu exportieren. Sie können die Modell Domäne in den Einstellungen für Ihr Projekt ändern.

    ![Registerkarte Leistung](images/AzureLabs-Lab313-01.png)

2. Wählen Sie die **Iterationen** aus, die Sie exportieren möchten, und klicken Sie auf **exportieren**. Ein Blatt wird angezeigt.

    ![Blatt "Exportieren"](images/AzureLabs-Lab313-02.png)

3. Klicken Sie auf dem Blatt auf **docker-Datei**.

    ![docker auswählen](images/AzureLabs-Lab313-03.png)

4. Klicken Sie im Dropdown Menü auf **Linux** , und klicken Sie dann auf **herunterladen**.

    ![Auf herunterladen klicken](images/AzureLabs-Lab313-04.png)

5. Entzippen Sie den Inhalt. Sie werden Sie später in diesem Kurs verwenden.

## <a name="chapter-2---the-container-registry-service"></a>Kapitel 2: der Container Registry-Dienst

Der **Container Registry-Dienst** ist das Repository, das zum Hosten Ihrer Container verwendet wird.

Der **IOT Hub-Dienst** , den Sie in diesem Kurs erstellen und verwenden, bezieht sich auf **Container Registry Dienst** , um die Container zu erhalten, die auf Ihrem Edge-Gerät bereitgestellt werden sollen.

1. Befolgen Sie zuerst [den Link zum Azure-Portal](https://portal.azure.com/), und melden Sie sich mit Ihren Anmelde Informationen an.

2. Wechseln Sie zu **Ressource erstellen** , und suchen Sie nach **Container Registry**.

    ![Container Registrierung](images/AzureLabs-Lab313-05.png)

3. Klicken Sie auf **Erstellen**.

    ![](images/AzureLabs-Lab313-06.png)

4. Legen Sie die Dienst Setup Parameter fest:

    1. Fügen Sie einen Namen für das Projekt ein. in diesem Beispiel wird er als " **iotcregistry**" bezeichnet.

    2. Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** . Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Kursen) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.

    3. Legen Sie den Speicherort des Dienstanbieter fest.

    4. Legen Sie **Administrator Benutzer** auf **aktivieren**fest.

    5. Legen Sie **SKU** auf **Basic**fest. 

    ![](images/AzureLabs-Lab313-07.png)

5. Klicken Sie auf **Erstellen** , und warten Sie, bis die Dienste erstellt wurden. 

6. Sobald die Benachrichtigung angezeigt wird, dass die *Container Registry*erfolgreich erstellt wurde, klicken Sie auf **zu Ressource** wechseln, um zur Seite des Diensts umgeleitet zu gelangen.

    ![](images/AzureLabs-Lab313-08.png)

7. Klicken Sie auf der Seite *Container Registry* Dienst auf **Zugriffsschlüssel**.

8. Notieren Sie sich (Sie können den Editor verwenden) der folgenden Parameter:
    1. **Anmelde Server**
    2. **Username**
    3. **Kennwort**

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a>Kapitel 3: der IOT Hub-Dienst

Nun beginnen Sie mit der Erstellung und Einrichtung Ihres **IOT Hub Dienstanbieter**.

1. Wenn Sie noch nicht angemeldet sind, melden Sie sich beim [Azure-Portal](https://portal.azure.com)an.

2.  Nachdem Sie sich angemeldet haben, klicken Sie in der oberen linken Ecke auf **Ressource erstellen** , suchen Sie nach **IOT Hub**, und drücken Sie die **Eingabe**Taste.

 ![Suchen nach Speicherkonto](images/AzureLabs-Lab313-10.png)

3.  Auf der neuen Seite wird eine Beschreibung des **Speicherkonto** Dienstanbieter bereitgestellt. Klicken Sie unten links in dieser Eingabeaufforderung auf die Schaltfläche **Erstellen** , um eine Instanz dieses Dienstanbieter zu erstellen.

    ![Speicher Instanz erstellen](images/AzureLabs-Lab313-11.png)

4.  Nachdem Sie auf **Erstellen**geklickt haben, wird ein Panel angezeigt:

    1. Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** . Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Kursen) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie unter diesem [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).


    2. Wählen Sie einen geeigneten **Speicherort** aus (verwenden Sie den gleichen Speicherort für alle Dienste, die Sie in diesem Kurs erstellen).

    3. Fügen Sie den gewünschten **Namen** für diese Dienst Instanz ein.    

5.  Klicken Sie am unteren Rand der Seite auf weiter **: Größe und Skalierung**.

    ![Speicher Instanz erstellen](images/AzureLabs-Lab313-12.png)

6.  Wählen Sie auf dieser Seite die **Preis-und Skalierungs** Ebene aus (wenn es sich um Ihre erste IOT Hub Dienst Instanz handelt, sollte Ihnen ein Free-Tarif zur Verfügung stehen).  

7.  Klicken Sie auf **überprüfen und erstellen**.

    ![Speicher Instanz erstellen](images/AzureLabs-Lab313-13.png)

8.  Überprüfen Sie die Einstellungen, und klicken Sie auf **Erstellen**.

    ![Speicher Instanz erstellen](images/AzureLabs-Lab313-14.png)

9. Sobald die Benachrichtigung angezeigt wird, dass Sie die erfolgreiche Erstellung des *IOT Hub* Diensts erhalten hat, klicken Sie auf **zu Ressource** wechseln, um zur Seite des Diensts umgeleitet zu gelangen.

    ![Speicher Instanz erstellen](images/AzureLabs-Lab313-15.png)

10. Scrollen Sie auf der linken Seite nach links, bis die *Automatische Geräteverwaltung*angezeigt wird, und klicken Sie auf **IOT Edge**.

    ![Speicher Instanz erstellen](images/AzureLabs-Lab313-16.png)

11. Klicken Sie im Fenster, das rechts angezeigt wird, auf **IOT Edge Gerät hinzufügen**. Auf der rechten Seite wird ein Blatt angezeigt.

12. Geben Sie auf dem Blatt das neue Gerät als **Geräte-ID** (Name Ihrer Wahl) an. Klicken Sie dann auf **Speichern**. Der *primäre* und der *sekundäre Schlüssel* werden automatisch generiert, wenn Sie die **Automatische Generierung** von aktivierten durchführen.

    ![Speicher Instanz erstellen](images/AzureLabs-Lab313-17.png)

13. Navigieren Sie zurück zum Abschnitt *IOT Edge Geräte* , in dem Ihr neues Gerät aufgeführt wird. Klicken Sie auf das neue Gerät (in der Abbildung unten rot dargestellt). 

    ![Speicher Instanz erstellen](images/AzureLabs-Lab313-18.png)

14. Erstellen Sie auf der angezeigten Seite *Geräte Details* eine Kopie der **Verbindungs Zeichenfolge** (Primärschlüssel).

    ![Speicher Instanz erstellen](images/AzureLabs-Lab313-19.png)

15. Wechseln Sie zurück zum Bereich auf der linken Seite, und klicken Sie auf SAS- *Richtlinien*, um ihn zu öffnen. 

16. Klicken Sie auf der Seite, die angezeigt wird, auf **iothubowner**, und rechts neben dem Bildschirm wird ein Blatt angezeigt. 

17. Notieren Sie sich (in Ihrem Editor) die **Verbindungs Zeichenfolge** (Primärschlüssel) für die spätere Verwendung beim Festlegen der *Verbindungs Zeichenfolge* auf Ihr Gerät.

    ![Speicher Instanz erstellen](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a>Kapitel 4: Einrichten der Entwicklungsumgebung

Zum Erstellen und Bereitstellen von Modulen für *IOT Hub Edge*müssen die folgenden Komponenten auf dem Entwicklungs Computer installiert sein, auf dem Windows 10 ausgeführt wird:

1.  [Docker für Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows)werden Sie aufgefordert, ein Konto zu erstellen, das heruntergeladen werden kann. 

    [![herunterladen von Docker für Windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)

    > [!IMPORTANT]
    > Docker erfordert, dass *Windows 10 pro*, *Enterprise 14393*oder *Windows Server 2016 RTM*ausgeführt wird. Wenn Sie andere Versionen von Windows 10 ausführen, können Sie versuchen, docker mithilfe der [docker-Toolbox](https://docs.docker.com/toolbox/toolbox_install_windows/)zu installieren.

2.  [Python 3,6](https://www.python.org/downloads/).

    [![herunterladen von Python 3,6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)

3.  [Visual Studio Code (auch bekannt als vs Code)](https://code.visualstudio.com/download).

    [![herunterladen vs Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)

Nach der Installation der oben erwähnten Software müssen Sie den Computer neu starten.

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a>Kapitel 5: Einrichten der Ubuntu-Umgebung

Nun können Sie mit dem Einrichten Ihres Geräts fortfahren, auf dem **Ubuntu OS ausgeführt**wird. Führen Sie die folgenden Schritte aus, um die erforderliche Software zu installieren, um Ihre Container auf Ihrem Board bereitzustellen:

> [!IMPORTANT]
> Sie sollten den Terminal Befehlen vor dem Ausführen von **sudo** immer als Administrator Benutzer vorangestellt sein. d
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  Öffnen Sie das **Ubuntu-Terminal**, und installieren Sie **PIP**mit dem folgenden Befehl:

    > [! Hinweis] Sie können das *Terminal* problemlos mit der Tastenkombination öffnen: **STRG + ALT + T**.

    ```bash
        sudo apt-get install python-pip
    ```

2.  In diesem Kapitel werden Sie ggf. vom *Terminal*aufgefordert, die Berechtigung zur Verwendung Ihres Geräte Speichers zu erhalten, und Sie können **y/n** (yes oder No) eingeben, geben Sie **"y"** ein, und drücken Sie dann die **Eingabe** Taste, um zu akzeptieren.

3.  Nachdem dieser Befehl abgeschlossen ist, verwenden Sie den folgenden Befehl zum Installieren von **curl**:

    ```bash
        sudo apt install curl
    ```

4.  Verwenden Sie nach der Installation von **PIP** und **curl** den folgenden Befehl, um die **IOT Edge Runtime**zu installieren. Dies ist erforderlich, um die Module auf Ihrem Board bereitzustellen und zu steuern:

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

5. An diesem Punkt werden Sie aufgefordert, die *Lauf Zeit Konfigurationsdatei*zu öffnen, um die **Geräte Verbindungs Zeichenfolge**einzufügen, die Sie im Editor notiert haben (in Ihrem Editor), wenn Sie den **IOT Hub-Dienst** erstellen (in[Schritt 14 von Kapitel 3](#chapter-3---the-iot-hub-service)). Führen Sie die folgende Zeile im Terminal aus, um diese Datei zu öffnen:

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. Die Datei " **config. YAML** " wird angezeigt und kann nun bearbeitet werden:

    > [!WARNING]
    > Wenn diese Datei geöffnet wird, kann Sie etwas verwirrend sein. Sie werden diese Datei im *Terminal* selbst bearbeiten. 

    1.  Verwenden Sie die Pfeiltasten auf der Tastatur, um einen Bildlauf nach unten durchführen (Sie müssen einen Bildlauf nach unten durchführen), um die Zeile zu erreichen, die Folgendes enthält:

        " **\<>" Geräte Verbindungs Zeichenfolge hinzufügen**".

    2. Ersatz Linie, **einschließlich der Klammern**, mit der **Geräte Verbindungs Zeichenfolge** , die Sie zuvor notiert haben.

7. Drücken Sie Ihre Verbindungs Zeichenfolge, und drücken Sie auf der Tastatur die Tastenkombination **STRG + X** , um die Datei zu speichern. Sie werden zur Bestätigung aufgefordert, indem Sie **Y**eingeben. Drücken Sie dann die **Eingabe** Taste, um dies zu bestätigen. Sie kehren zum regulären *Terminal*zurück. 

8. Nachdem diese Befehle erfolgreich ausgeführt wurden, haben Sie die **IOT Edge Runtime**installiert. Nachdem die Laufzeit initialisiert wurde, wird Sie jedes Mal, wenn das Gerät eingeschaltet ist, auf dem neuesten Stand, und es wird auf die Bereitstellung der Module aus dem **IOT Hub-Dienst**gewartet.

9.  Führen Sie die folgende Befehlszeile aus, um die *IOT Edge Runtime*zu initialisieren:

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > Wenn Sie Änderungen an der YAML-Datei oder an der oben beschriebenen Einrichtung vornehmen, müssen Sie die oben angegebene Neustart Zeile im *Terminal*erneut ausführen.

10. Überprüfen Sie den Lauf Zeit Status der *IOT Edge* , indem Sie die folgende Befehlszeile ausführen. Die Laufzeit sollte mit dem Status " **aktiv" (wird ausgeführt)** in grünem Text angezeigt werden.

    ```bash
        sudo systemctl status iotedge
    ```

11. Drücken Sie die Tastenkombination **STRG + C** , um die Statusseite zu beenden. Durch Eingabe des folgenden Befehls können Sie überprüfen, ob die *IOT Edge Runtime* die Container ordnungsgemäß durchläuft:

    ```bash
        sudo docker ps
    ```

12. Eine Liste mit zwei (2) Containern sollte angezeigt werden. Dies sind die Standardmodule, die automatisch vom IOT Hub-Dienst (edgeagent und edgehub) erstellt werden. Nachdem Sie Ihre eigenen Module erstellt und bereitgestellt haben, werden Sie in dieser Liste unterhalb der Standardwerte angezeigt.

## <a name="chapter-6---install-the-extensions"></a>Kapitel 6: Installieren der Erweiterungen

> [!IMPORTANT]
> Die nächsten Kapitel (6-9) müssen auf Ihrem Windows 10-Computer ausgeführt werden.

1. Öffnen Sie **vs Code**.

2. Klicken Sie in der linken Leiste vs Code auf die Schaltfläche **Erweiterungen** (Quadrat), um den Bereich **Erweiterungen**zu öffnen.

3. Suchen Sie nach den folgenden Erweiterungen (wie in der Abbildung unten gezeigt), und installieren Sie Sie:

    1. Azure IoT Edge
    2. Azure IOT-Toolkit
    3. Docker   

    ![Erstellen des Containers](images/AzureLabs-Lab313-24.png)

4. Nachdem Sie die Erweiterungen installiert haben, schließen Sie vs Code, und öffnen Sie es erneut.

5. Wenn vs Code noch einmal geöffnet ist, navigieren Sie zu > **integriertes Terminal** **anzeigen** .

6. Sie installieren nun **cookiecutter**. Führen Sie im Terminal den folgenden bash-Befehl aus:

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! Hinweis], wenn Sie Probleme mit diesem Befehl haben: 
    >1. Starten Sie vs Code und/oder den Computer neu.
    >2. Möglicherweise ist es erforderlich, das **vs Code Terminal** auf das zu ändern, das Sie zum Installieren von Python verwendet haben, d. h. **PowerShell** (insbesondere für den Fall, dass die python-Umgebung bereits auf Ihrem Computer installiert wurde). Wenn das Terminal geöffnet ist, finden Sie das Dropdown Menü auf der rechten Seite des Terminals.
     ![Erstellen des Containers](images/AzureLabs-Lab313-24b.png) 
    >3. Stellen Sie sicher, dass der **python** -Installationspfad als **Umgebungs Variable** auf dem Computer hinzugefügt wird. Cookiecutter sollte Teil desselben Standort Pfads sein. [Weitere Informationen zu Umgebungsvariablen](https://msdn.microsoft.com/library/windows/desktop/ms682653(v=vs.85).aspx)finden Sie unter diesem Link. 

7. Nachdem die Installation von **cookiecutter** abgeschlossen ist, sollten Sie den Computer neu starten, damit **cookiecutter** in der Umgebung Ihres Systems als Befehl erkannt wird.

## <a name="chapter-7---create-your-container-solution"></a>Kapitel 7: Erstellen der Containerlösung

An diesem Punkt müssen Sie den Container mit dem-Modul erstellen, damit er in die *Container Registry*übermittelt werden kann. Nachdem Sie den Container per Pushvorgang übermittelt haben, verwenden Sie den *IOT Hub Edge* -Dienst, um ihn auf Ihrem Gerät bereitzustellen, auf dem die *IOT Edge Laufzeit*ausgeführt wird.

1. Klicken Sie in vs Code auf **Ansicht** > **Befehls Palette**.

2. Suchen Sie in der Palette nach **Azure IOT Edge: neue IOT Edge-Lösung**, und führen Sie Sie aus.

3. Navigieren Sie zu einem Speicherort, an dem Sie die Projekt Mappe erstellen möchten. Drücken **Sie die Eingabe** Taste, um den Speicherort zu akzeptieren.

4. Nennen Sie die Projekt Mappe. Drücken **Sie die Eingabe** Taste, um den angegebenen Namen zu bestätigen.

5. Nun werden Sie aufgefordert, das Vorlagen Framework für Ihre Lösung auszuwählen. Klicken Sie auf **Python-Modul**. Drücken **Sie die Eingabe** Taste, um diese Auswahl zu bestätigen.

6. Benennen Sie Ihr Modul. Drücken **Sie die Eingabe** Taste, um den Namen des Moduls zu bestätigen. Stellen Sie sicher, dass Sie einen Hinweis (mit Ihrem Editor) des Modulnamens verwenden, da er später verwendet wird.

7. Sie werden feststellen, dass in der Palette eine vorgefertigte *docker-imagerepository* -Adresse angezeigt wird. Dies sieht wie folgt aus:

    **localhost: 5000/-der Name Ihres Moduls**. 

8. Löschen Sie **localhost: 5000**, und fügen Sie dort die *Container Registry* **Anmelde Server** Adresse ein, die Sie beim Erstellen des **Container Registry Diensts** notiert haben ([in Schritt 8 von Kapitel 2](#chapter-2---the-container-registry-service)). Drücken **Sie die Eingabe** Taste, um die Adresse zu bestätigen.

9. An diesem Punkt wird die Projekt Mappe, die die Vorlage für das Python-Modul enthält, erstellt, und die Struktur wird auf der **Registerkarte**"Durchsuchen" der vs Code auf der linken Seite des Bildschirms angezeigt. Wenn die **Registerkarte** "Durchsuchen" nicht geöffnet ist, können Sie Sie öffnen, indem Sie in der Leiste auf der linken Seite auf die oberste Schaltfläche klicken.

    ![Erstellen des Containers](images/AzureLabs-Lab313-25.png)

10. Der letzte Schritt in diesem Kapitel besteht darin, auf die Datei " **. ATV**" auf der **Registerkarte**"Durchsuchen" zu klicken und Sie zu öffnen und Ihre *Container Registry* **Benutzername** und **Kennwort**hinzuzufügen. Diese Datei wird von git ignoriert, aber beim Aufbau des Containers werden die Anmelde Informationen für den Zugriff auf den **Container Registry Dienst**von festgelegt.

    ![Erstellen des Containers](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a>Kapitel 8: Bearbeiten der Containerlösung

Sie vervollständigen nun die Containerlösung, indem Sie die folgenden Dateien aktualisieren:

- *Main<span></span>. py* Python-Skript.
- " *Requirements. txt*".
- " *Deployment. Template. JSON*".
- *Dockerfile. amd64*

Anschließend erstellen Sie den Ordner *Images* , der vom Python-Skript verwendet wird, um zu überprüfen, ob Bilder mit Ihrem *Custom Vision Modell*abgeglichen werden. Schließlich fügen Sie die Datei " *Labels. txt* " hinzu, um das Modell zu lesen, und die Datei " *Model. PB* ", die das Modell ist.

1. Wenn vs Code geöffnet ist, navigieren Sie zu Ihrem Modul Ordner, und suchen Sie nach dem Skript mit dem Namen **<span></span>Main. py**. Doppelklicken Sie, um es zu öffnen.

2. Löschen Sie den Inhalt der Datei, und fügen Sie den folgenden Code ein:

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

3.  Öffnen Sie die Datei " **Requirements. txt**", und ersetzen Sie deren Inhalt durch Folgendes:

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  Öffnen Sie die Datei " **Deployment. Template. JSON**", und ersetzen Sie deren Inhalt nach der folgenden Richtlinie:

    1. Da Sie über eine eigene, eindeutige JSON-Struktur verfügen, müssen Sie Sie manuell bearbeiten (anstatt ein Beispiel zu kopieren). Um dies zu erleichtern, verwenden Sie das folgende Bild als Leitfaden.
    2. Bereiche, die sich von Ihnen unterscheiden, aber **nicht geändert werden sollten, sind gelb hervorgehoben**.
    3. **Abschnitte, die Sie löschen müssen, sind hervorgehoben.**
    4. Achten Sie darauf, die richtigen Klammern zu löschen, und entfernen Sie auch die Kommas.

        ![Erstellen des Containers](images/AzureLabs-Lab313-27.png)

    5. Der abgeschlossene JSON-Code sollte wie in der folgenden Abbildung aussehen (jedoch mit ihren eindeutigen unterschieden: *Benutzername/Kennwort/Modulname/Modul Verweise*):

        ![Erstellen des Containers](images/AzureLabs-Lab313-28.png)

5.  Öffnen Sie die Datei **dockerfile. amd64**, und ersetzen Sie den Inhalt durch Folgendes:

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

6.  Klicken Sie mit der rechten Maustaste auf den Ordner unterhalb der **Module** (er enthält den Namen, den Sie zuvor angegeben haben. im Beispiel weiter unten wird er als " *Pythonmodule*" bezeichnet), und klicken Sie auf " **neuer Ordner**". Nennen Sie den Ordner **Images**.

7.  Fügen Sie im Ordner einige Bilder hinzu, die Maus oder Tastatur enthalten. Dabei handelt es sich um die Bilder, die vom tensorflow-Modell analysiert werden.

    > [!WARNING]
    > Wenn Sie ein eigenes Modell verwenden, müssen Sie es ändern, um Ihre eigenen Modelldaten widerzuspiegeln.

8.  Sie müssen nun die Dateien " **Labels. txt** " und **"Model. PB** " aus dem Ordner "Model" abrufen, den Sie zuvor heruntergeladen (oder aus Ihrem eigenen **Custom Vision Service**erstellt haben), in [Kapitel 1](#chapter-1---retrieve-the-custom-vision-model). Wenn Sie über die Dateien verfügen, platzieren Sie sie zusammen mit den anderen Dateien in der Projekt Mappe. Das Endergebnis sollte wie in der folgenden Abbildung aussehen:

    ![Erstellen des Containers](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a>Kapitel 9: Verpacken der Projekt Mappe als Container

1.  Sie sind jetzt bereit, Ihre Dateien als Container zu verpacken und per Push an Ihre **Azure Container Registry**zu übersetzen. Öffnen Sie in vs Code das *integrierte Terminal* (**anzeigen** > **integriertes Terminal** oder **STRG**+ **\`** ), und verwenden Sie die folgende Zeile, um sich bei **docker** anzumelden (ersetzen Sie die Werte des Befehls durch). die Anmelde Informationen Ihres **Azure Container Registry (ACR)** ):

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. Klicken Sie mit der rechten Maustaste auf die Datei **Deployment. Template. JSON**, und klicken Sie auf IOT Edge Projekt Mappe **Erstellen**. Dieser Buildprozess dauert einige Zeit (abhängig von Ihrem Gerät) und sollte daher darauf warten, gewartet zu werden. Nachdem der Buildprozess abgeschlossen ist, wurde eine Datei " **Deployment. JSON** " in einem neuen Ordner mit dem Namen " **config**" erstellt.

    ![Bereitstellung erstellen](images/AzureLabs-Lab313-30.png)

3. Öffnen Sie die **Befehls Palette** erneut, und suchen Sie nach **Azure: Anmelden**. Befolgen Sie die Anweisungen unter Verwendung der Anmelde Informationen Ihres Azure-Kontos. VS Code wird Ihnen eine Option zum *Kopieren und öffnen*zur Verfügung gestellt, die den Geräte Code kopiert, den Sie in Kürze benötigen, und den Standard Webbrowser öffnen. Wenn Sie gefragt werden, fügen Sie den Geräte Code ein, um den Computer zu authentifizieren.

    ![Kopieren und öffnen](images/AzureLabs-Lab313-31.png)

4. Nachdem Sie sich angemeldet haben, werden Sie am unteren Rand des Bereichs " *erkunden* " einen neuen Abschnitt mit dem Namen " **Azure IOT Hub Geräte**" bemerken. Klicken Sie auf diesen Abschnitt, um ihn zu erweitern.

    ![Edge-Gerät](images/AzureLabs-Lab313-32.png)

5. Wenn Ihr Gerät hier nicht angezeigt wird, klicken Sie mit der rechten Maustaste auf *Azure IOT Hub Geräte*, und klicken Sie dann auf **IOT Hub Verbindungs Zeichenfolge festlegen**. Dann sehen Sie, dass Sie in der **Befehls Palette** (oben in vs Code) aufgefordert werden, die *Verbindungs Zeichenfolge*einzugeben. Dies ist die *Verbindungs Zeichenfolge* , die Sie am Ende von [Kapitel 3](#chapter-3---the-iot-hub-service)notiert haben. Drücken Sie die **Eingabe** Taste, nachdem Sie die Zeichenfolge in kopiert haben.    

6. Ihr Gerät sollte geladen werden und angezeigt werden. Klicken Sie mit der rechten Maustaste auf den Gerätenamen, und klicken Sie dann auf **Bereitstellung für einzelnes Gerät erstellen**.

    ![Bereitstellung erstellen](images/AzureLabs-Lab313-33b.png)

7. Sie erhalten eine *Datei-Explorer* -Eingabeaufforderung, in der Sie zum Ordner " **config** " navigieren und dann die Datei " **Deployment. JSON** " auswählen können. Wenn diese Datei ausgewählt ist, klicken Sie auf die Schaltfläche **Edge-Bereitstellungs Manifest auswählen** .

    ![Bereitstellung erstellen](images/AzureLabs-Lab313-34.png)

8. An diesem Punkt haben Sie Ihren **IOT Hub Dienst** mit dem Manifest bereitgestellt, um den Container, als Modul, von Ihrer **Azure Container Registry**bereitzustellen und effektiv auf Ihrem Gerät bereitzustellen.

9. Um die Nachrichten anzuzeigen, die vom Gerät an den IOT Hub gesendet werden, klicken Sie mit der rechten Maustaste erneut auf den Gerätenamen im Bereich **Azure IOT Hub Geräte** im Bereich **Explorer** , und klicken Sie auf **Überwachung D2C Meldung starten**. Die von Ihrem Gerät gesendeten Nachrichten sollten im vs-Terminal angezeigt werden. Seien Sie geduldig, da dies einige Zeit in Anspruch nehmen kann. Weitere Informationen zum Debuggen und zum Überprüfen, ob die Bereitstellung erfolgreich war

Dieses Modul durchläuft nun zwischen den Bildern im Ordner " **Images** " und analysiert sie mit jeder Iterationen. Dies ist offensichtlich nur ein Beispiel dafür, wie Sie das grundlegende Machine Learning-Modell für eine IOT Edge Geräte Umgebung einsetzen können. 

Um die Funktionalität dieses Beispiels zu erweitern, können Sie auf verschiedene Weise fortfahren. Eine Möglichkeit besteht darin, Code in den Container einzubeziehen, der Fotos von einer mit dem Gerät verbundenen Webcam erfasst und die Bilder im Ordner Images speichert. 

Eine andere Möglichkeit besteht darin, die Images vom IOT-Gerät in den Container zu kopieren. Eine praktische Möglichkeit besteht darin, den folgenden Befehl im IOT-Geräte Terminal auszuführen (möglicherweise könnte eine kleine APP den Auftrag ausführen, wenn Sie den Prozess automatisieren möchten). Sie können diesen Befehl testen, indem Sie ihn manuell aus dem Ordner Speicherort ausführen, in dem die Dateien gespeichert sind:

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a>Kapitel 10: Debuggen der IOT Edge Laufzeit

Im folgenden finden Sie eine Liste mit Befehlszeilen und Tipps, die Sie beim Überwachen und Debuggen der Messaging Aktivität der *IOT Edge Runtime*von Ihrem **Ubuntu-Gerät**aus unterstützen. 

- Überprüfen Sie den Lauf Zeit Status der *IOT Edge* , indem Sie die folgende Befehlszeile ausführen:

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > Drücken Sie **STRG + C**, um die Anzeige des Status abzuschließen.

- Listet die Container auf, die zurzeit bereitgestellt werden. Wenn der *IOT Hub-Dienst* die Container erfolgreich bereitgestellt hat, werden diese angezeigt, indem Sie die folgende Befehlszeile ausführen:

    ```bash
        sudo iotedge list
    ```

    Oder

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > Das obige ist eine gute Möglichkeit, um zu überprüfen, ob das Modul erfolgreich bereitgestellt wurde, da es in der Liste angezeigt wird. Andernfalls werden **nur** *edgehub* und *edgeagent*angezeigt.

- Um die Code Protokolle eines Containers anzuzeigen, führen Sie die folgende Befehlszeile aus:

    ```bash
        journalctl -u iotedge
    ```

**Nützliche Befehle zum Verwalten der IOT Edge Laufzeit:**

-  So löschen Sie alle Container auf dem Host:

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  So verhindern Sie die *IOT Edge Laufzeit*:

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a>Kapitel 11: Erstellen eines Tabellen Dienstanbieter 

Navigieren Sie zurück zu Ihrem Azure-Portal, in dem Sie einen Azure Tables-Dienst erstellen, indem Sie eine Speicher Ressource erstellen.

1. Wenn Sie noch nicht angemeldet sind, melden Sie sich beim [Azure-Portal](https://portal.azure.com)an.

2. Nachdem Sie sich angemeldet haben, klicken Sie in der oberen linken Ecke auf **Ressource erstellen**, suchen Sie nach **Speicherkonto**, und drücken **Sie die Eingabe** Taste, um die Suche zu starten.

3. Wenn die Datei angezeigt wird, klicken Sie auf **Speicherkonto-BLOB, Datei, Tabelle, Warteschlange** aus der Liste.

    ![Suchen nach Speicherkonto](images/AzureLabs-Lab313-35.png)

4. Auf der neuen Seite wird eine Beschreibung des **Speicherkonto** Dienstanbieter bereitgestellt. Klicken Sie unten links in dieser Eingabeaufforderung auf die Schaltfläche **Erstellen** , um eine Instanz dieses Dienstanbieter zu erstellen.

    ![Speicher Instanz erstellen](images/AzureLabs-Lab313-36.png)

5. Nachdem Sie auf **Erstellen**geklickt haben, wird ein Panel angezeigt:

    1. Fügen Sie den gewünschten **Namen** für diese Dienst Instanz ein (*nur klein*Buchstaben).

    2. Klicken Sie unter **Bereitstellungs Modell**auf **Ressourcen-Manager**.

    3. Klicken Sie unter **Kontoart**im Dropdown Menü auf **Speicher (universell v1)** .

    4. Klicken Sie auf einen geeigneten **Speicherort**.
    
    5. Klicken Sie im Dropdown Menü **Replikation** auf **georedundanten Speicher mit Lesezugriff (RA-GRS)** .

    6. Klicken Sie für die **Leistung**auf **Standard**.

    7. Klicken Sie im Abschnitt **Secure Transfer required** auf **deaktiviert**.

    8. Klicken Sie im Dropdown Menü **Abonnement** auf ein entsprechendes Abonnement.

    9. Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** . Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Kursen) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie unter diesem [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    10. Lassen Sie **virtuelle Netzwerke** **deaktiviert**, wenn dies eine Option für Sie ist.

    11. Klicken Sie auf **Erstellen**.

        ![Speicher Details ausfüllen](images/AzureLabs-Lab313-37.png)

6. Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.

7. Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt. Klicken Sie auf die Benachrichtigungen, um die neue Dienst Instanz zu untersuchen.

    ![neue Speicher Benachrichtigung](images/AzureLabs-Lab313-38.png)

8. Klicken Sie in der Benachrichtigung auf die Schaltfläche **zum Ressourcen** Wechsel, und Sie gelangen zur Übersichtsseite der neuen Speicherdienst Instanz.

    ![Gehe zu Ressource](images/AzureLabs-Lab313-39.png)

9. Klicken Sie auf der Seite Übersicht auf die Rechte Seite, und klicken Sie auf **Tabellen**.
    
    ![Spielern](images/AzureLabs-Lab313-40.png)

10. Der Bereich auf der rechten Seite ändert sich, um die **Tabellen Dienst** Informationen anzuzeigen, in denen Sie eine neue Tabelle hinzufügen müssen. Klicken Sie hierzu auf die Schaltfläche **+ Table** in der linken oberen Ecke.

    ![Öffnen von Tabellen](images/AzureLabs-Lab313-41.png)

11. Es wird eine neue Seite angezeigt, auf der Sie einen **Tabellennamen**eingeben müssen. Dies ist der Name, den Sie in späteren Kapiteln (Erstellen von Funktionen-APP und Power BI) verwenden, um auf die Daten in Ihrer Anwendung zu verweisen. Fügen Sie **iotmessages** als Name ein. (Sie können sich auch selbst merken, wenn Sie es später in diesem Dokument verwenden), und klicken Sie auf **OK**. 

12. Nachdem die neue Tabelle erstellt wurde, können Sie Sie auf der Seite **Tabellen Dienst** (unten) sehen.

    ![neue Tabelle erstellt](images/AzureLabs-Lab313-42.png)  

13. Klicken Sie nun auf **Zugriffsschlüssel** , und nehmen Sie eine Kopie des **Speicherkonto namens** und- **Schlüssels** auf (mithilfe Ihres Notepad). Sie verwenden diese Werte später in diesem Kurs, wenn Sie die **Azure-Funktionen-App**erstellen.

    ![neue Tabelle erstellt](images/AzureLabs-Lab313-43.png) 

14. Scrollen Sie im Bereich auf der linken Seite zum Abschnitt *Tabellen Dienst* , und klicken Sie auf **Tabellen** (oder Tabellen in neueren Portalen **Durchsuchen**), und erstellen Sie eine Kopie der **Tabellen-URL** (mit Ihrem Editor). Sie verwenden diesen Wert später in diesem Kurs, wenn Sie Ihre Tabelle mit Ihrer **Power BI** Anwendung verknüpfen.

    ![neue Tabelle erstellt](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a>Kapitel 12: Abschließen der Azure-Tabelle

Nachdem Sie das Speicher **Dienst** -Speicherkonto eingerichtet haben, ist es an der Zeit, Daten hinzuzufügen, die zum Speichern und Abrufen von Informationen verwendet werden. Die Bearbeitung der Tabellen kann über **Visual Studio**erfolgen.

1. Öffnen Sie **Visual Studio** (**nicht** Visual Studio Code).

2. Klicken Sie im Menü auf > **Cloud-Explorer** **anzeigen** .

    ![Cloud-Explorer öffnen](images/AzureLabs-Lab313-45.png)

3. Der **Cloud-Explorer** wird als angedocktes Element geöffnet (als "Patient", da der Ladevorgang Zeit in Anspruch nehmen kann).

    > [!WARNING] 
    > Wenn das Abonnement, das Sie zum Erstellen Ihrer *Speicher Konten* verwendet haben, nicht sichtbar ist, stellen Sie Folgendes sicher: 
    > - Sie sind beim gleichen Konto angemeldet, das Sie für das Azure-Portal verwendet haben.
    > - Wählen Sie auf der Seite "Kontoverwaltung" Ihr Abonnement aus (möglicherweise müssen Sie einen Filter aus Ihren Kontoeinstellungen anwenden):  
    >
    >   ![Abonnement suchen](images/AzureLabs-Lab313-46.png)

4. Ihre Azure-Clouddienste werden angezeigt. Suchen Sie nach **Speicher Konten** , und klicken Sie auf den Pfeil auf der linken Seite, um Ihre Konten zu erweitern.

    ![Öffnen von Speicher Konten](images/AzureLabs-Lab313-47.png)

5. Nach der Erweiterung sollte Ihr neu erstelltes **Speicherkonto** verfügbar sein. Klicken Sie auf den Pfeil links neben dem Speicher, und wählen Sie dann nach dem Erweitern der Tabelle **Tabellen** aus, und klicken Sie auf den Pfeil daneben, um die **Tabelle** anzuzeigen, die Sie im letzten Kapitel erstellt haben. Doppelklicken Sie auf die **Tabelle**.

6. Ihre Tabelle wird in der Mitte Ihres Visual Studio-Fensters geöffnet. Klicken Sie auf das Symboltabelle mit dem **+** (plus).

    ![neue Tabelle hinzufügen](images/AzureLabs-Lab313-48.png)

7. Ein Fenster wird angezeigt, in dem Sie aufgefordert werden, *Entitäten hinzuzufügen*. Sie erstellen nur eine Entität, Sie verfügen jedoch über drei Eigenschaften. Sie werden feststellen, dass *PartitionKey* und *RowKey* bereits bereitgestellt werden, da diese von der Tabelle zum Suchen Ihrer Daten verwendet werden. 

    ![Partitions-und Zeilen Schlüssel](images/AzureLabs-Lab313-49.png)

8. Aktualisieren Sie die folgenden Werte:

    - Name: **PartitionKey**, Wert: **PK_IoTMessages** 

    - Name: **RowKey**, Wert: **RK_1_IoTMessages** 

9. Klicken Sie dann auf **Eigenschaft hinzufügen** (unten links im Fenster *Entität hinzufügen* ), und fügen Sie die folgende Eigenschaft hinzu:

    - Bei **messagecontent**wird als *Zeichen*Folge der Wert leer gelassen.

10. Die Tabelle sollte der Tabelle in der folgenden Abbildung entsprechen:

    ![korrekte Werte hinzufügen](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > Der Grund, warum die Entität die Zahl 1 im Zeilen Schlüssel hat, liegt daran, dass Sie möglicherweise weitere Nachrichten hinzufügen möchten, sollten Sie mit diesem Kurs weiter experimentieren.

11. Klicken Sie anschließend auf **OK**. Die Tabelle ist jetzt zur Verwendung bereit.

## <a name="chapter-13---create-an-azure-function-app"></a>Kapitel 13: Erstellen eines Azure-Funktionen-App 

Nun ist es an der Zeit, eine *Azure-Funktionen-App*zu erstellen, die vom *IOT Hub-Dienst* aufgerufen wird, um die *IOT Edge* Geräte Nachrichten im **Tabellen** Dienst zu speichern, die Sie im vorherigen Kapitel erstellt haben.

Zunächst müssen Sie eine Datei erstellen, die es ihrer Azure-Funktion ermöglicht, die benötigten Bibliotheken zu laden.

1.  Öffnen Sie **Editor** (drücken Sie die *Windows-Taste*, und geben Sie *Editor*ein).

    ![Editor öffnen](images/AzureLabs-Lab313-51.png)

2.  Fügen Sie bei geöffneter Notepad die JSON-Struktur unten ein. Wenn Sie dies abgeschlossen haben, speichern Sie es auf Ihrem Desktop als " **Project. JSON**". Diese Datei definiert die Bibliotheken, die von ihrer Funktion verwendet werden. Wenn Sie nuget verwendet haben, wird es vertraut aussehen.
    
    > [!WARNING]
    > Es ist wichtig, dass die Benennung korrekt ist. Stellen Sie sicher, dass die Dateierweiterung **txt nicht** vorhanden ist. Weitere Informationen finden Sie weiter unten:
    >
    > ![JSON-Speicherung](images/AzureLabs-Lab313-52.png)

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

3.  Melden Sie sich beim [Azure-Portal](https://portal.azure.com)an.

4.  Wenn Sie angemeldet sind, klicken Sie in der oberen linken Ecke auf **Ressource erstellen** , suchen Sie nach **Funktionen-App**, und drücken Sie die **Eingabe** Taste, um zu suchen. Klicken Sie in den Ergebnissen auf *Funktionen-App* , um einen neuen Bereich zu öffnen.

    ![nach Funktionen-App suchen](images/AzureLabs-Lab313-53.png)

5.  Im neuen Panel wird eine Beschreibung des **Funktionen-App** Dienstanbieter bereitgestellt. Klicken Sie unten links in diesem Bereich auf die Schaltfläche **Erstellen** , um eine Verknüpfung mit diesem Dienst zu erstellen.

    ![Funktionen-app-Instanz](images/AzureLabs-Lab313-54.png)

6.  Nachdem Sie auf **Erstellen**geklickt haben, geben Sie Folgendes ein:

    1. Fügen Sie für **App-Name**den gewünschten Namen für diese Dienst Instanz ein.

    2. Wählen Sie ein **Abonnement**aus.

    3. Wählen Sie den für Sie geeigneten Tarif aus. Wenn Sie zum ersten Mal einen **Funktionen-App Dienst**erstellen, sollte Ihnen ein Free-Tarif zur Verfügung stehen.

    4. Wählen Sie eine Ressourcengruppe aus, oder erstellen Sie eine neue **Ressourcengruppe** . Eine Ressourcengruppe bietet eine Möglichkeit zum überwachen, Steuern des Zugriffs, bereitstellen und Verwalten der Abrechnung für eine Sammlung von Azure-Ressourcen. Es wird empfohlen, alle Azure-Dienste, die einem einzelnen Projekt (z. b. diesen Kursen) zugeordnet sind, in einer gemeinsamen Ressourcengruppe zu speichern.

        > Weitere Informationen zu Azure-Ressourcengruppen finden Sie unter diesem [Link zum Verwalten einer Ressourcengruppe](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).

    5. Klicken Sie für **Betriebssystem**auf Windows, da dies die beabsichtigte Plattform ist.

    6. Wählen Sie einen **Hostingplan** aus (in diesem Tutorial wird ein **Verbrauchs Plan**verwendet.)

    7. Wählen Sie einen **Standort** aus (Wählen Sie den gleichen Speicherort wie für den Speicher aus, den Sie im vorherigen Schritt erstellt haben).

    8. Im Abschnitt **Speicher** **müssen Sie den Speicherdienst auswählen, den Sie im vorherigen Schritt erstellt**haben.

    9. Sie benötigen keine *Application Insights* in dieser APP, sodass Sie Sie nicht mehr **Deaktivieren**können.

    10. Klicken Sie auf **Erstellen**.

        ![neue Instanz erstellen](images/AzureLabs-Lab313-55.png)

7.  Nachdem Sie auf **Erstellen**geklickt haben, müssen Sie warten, bis der Dienst erstellt wurde. dieser Vorgang kann einige Minuten in Anspruch nehmen.

8.  Nachdem die Dienst Instanz erstellt wurde, wird im Portal eine Benachrichtigung angezeigt.

    ![neue Benachrichtigung](images/AzureLabs-Lab313-56.png)

9.  Nachdem die Bereitstellung erfolgreich abgeschlossen wurde, klicken Sie auf die Benachrichtigung.

10. Klicken Sie in der Benachrichtigung auf die Schaltfläche **Gehe zu Ressource** , um die neue Dienst Instanz zu untersuchen. 

    ![Gehe zu Ressource](images/AzureLabs-Lab313-57.png)

11. Klicken Sie auf der linken Seite des neuen Panels auf das Symbol **+** (plus) neben *Functions*, um eine neue Funktion zu erstellen.

    ![neue Funktion hinzufügen](images/AzureLabs-Lab313-58.png)

12. Im mittleren Bereich wird das Fenster für die **Funktions** Erstellung angezeigt. Scrollen Sie nach unten, und klicken Sie auf **benutzerdefinierte Funktion**.

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-59.png)

13. Scrollen Sie auf der nächsten Seite nach unten, bis Sie **IOT Hub (Event Hub)** gefunden haben, und klicken Sie dann darauf.

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-60.png)

14. Legen Sie auf dem Blatt **IOT Hub (Event Hub)** die **Sprache** auf **C#** fest, und klicken Sie dann auf **neu**.

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-61.png)

15. Stellen Sie im Fenster, das angezeigt wird, sicher, dass **IOT Hub** ausgewählt ist und der Name des *IOT Hub* Felds mit dem Namen des *IOT Hub Dienstanbieter* übereinstimmt, den Sie zuvor erstellt haben ([in Schritt 8 von Kapitel 3](#chapter-3---the-iot-hub-service)). Klicken Sie dann auf die Schaltfläche **auswählen** .

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-62.png)

16. Klicken Sie auf dem Blatt **IOT Hub (Event Hub)** auf **Erstellen**.

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-63.png)

17. Sie werden zum Funktions-Editor umgeleitet.

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-64.png)

18. Löschen Sie den gesamten Code, und ersetzen Sie ihn durch Folgendes:

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

19. Ändern Sie die folgenden Variablen, damit Sie den entsprechenden Werten entsprechen (**Tabellen** -und **Speicher** Werte aus [Schritt 11 und 13 bzw. in Kapitel 11](#chapter-11---create-table-service)), die Sie in Ihrem **Speicherkonto**finden:

    - **TableName**, mit dem Namen der **Tabelle** in Ihrem **Speicherkonto**.
    - **tableurl**, wobei sich die URL Ihrer **Tabelle** in Ihrem **Speicherkonto**befindet.
    - **storageaccountname**, mit dem Namen des Werts, der dem Namen Ihres **Speicherkonto** namens entspricht.
    - **storageaccountkey**mit dem Schlüssel, den Sie im zuvor erstellten Speicherdienst abgerufen haben.

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-65.png)

20. Klicken Sie mit dem Code auf **Speichern**.

21. Klicken Sie anschließend auf der rechten Seite der Seite auf das Symbol **\<** (Pfeil).

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-66.png)

22. Ein Panel wird von rechts nach rechts angezeigt. Klicken Sie in diesem Bereich auf **hochladen**, und ein *Datei Browser* wird angezeigt.

23. Navigieren Sie zu, und klicken Sie auf die Datei **Project. JSON** , die Sie **zuvor im** Editor erstellt haben, und klicken Sie dann auf die Schaltfläche **Öffnen** . Diese Datei definiert die Bibliotheken, die von ihrer Funktion verwendet werden.

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-67.png)

24. Wenn die Datei hochgeladen wurde, wird Sie im Panel auf der rechten Seite angezeigt. Wenn Sie darauf klicken, wird es im **Funktions** -Editor geöffnet. Es muss **genau** wie das nächste Bild aussehen.

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-68.png)

25. An diesem Punkt wäre es gut, die Funktion ihrer Funktion zu testen, um die Nachricht in der *Tabelle*zu speichern. Klicken Sie oben rechts im Fenster auf **Test**.

    ![benutzerdefinierte Funktion](images/AzureLabs-Lab313-69.png)

26. Fügen Sie eine Meldung in den **Anforderungs Text**ein, wie in der obigen Abbildung gezeigt, und klicken Sie auf **Ausführen**. 

27. Die Funktion wird ausgeführt und zeigt den Ergebnis Status an (Sie werden feststellen, dass der grüne **Status 202 akzeptiert**wurde, oberhalb des *Ausgabe* Fensters, was bedeutet, dass es sich um einen erfolgreichen Rückruf handelt):

    ![Ausgabe Ergebnis](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a>Kapitel 14: Anzeigen von aktiven Nachrichten

Wenn Sie Visual Studio (**nicht** Visual Studio Code) öffnen, können Sie das Testnachrichten Ergebnis visualisieren, da es im Bereich der *messagecontent* -Zeichenfolge gespeichert wird.

![benutzerdefinierte Funktion](images/AzureLabs-Lab313-71.png)

Wenn der Tabellen Dienst und der Funktionen-app vorhanden sind, werden Ihre Ubuntu-Geräte Meldungen in der Tabelle " *iotmessages* " angezeigt. Wenn Sie nicht bereits ausgeführt werden, starten Sie das Gerät erneut, und Sie können die Ergebnismeldungen von Ihrem Gerät und Modul innerhalb Ihrer Tabelle mithilfe von Visual Studio *Cloud-Explorer*anzeigen.

![Visualisieren von Daten](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a>Kapitel 15: Power BI-Setup

Zum Visualisieren der Daten von Ihrem IOT-Gerät richten Sie **Power BI** (Desktop Version) ein, um die Daten aus dem *Tabellen* Speicherdienst zu erfassen, den Sie soeben erstellt haben. Die *hololens* -Version von Power BI verwendet diese Daten dann, um das Ergebnis visuell darzustellen.

1.  Öffnen Sie die Microsoft Store unter Windows 10, und suchen Sie nach **Power BI Desktop**.

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  Laden Sie die Anwendung herunter. Nachdem der Download abgeschlossen ist, öffnen Sie ihn.

3.  Melden Sie sich mit Ihrem **Microsoft 365 Konto**bei *Power BI* an. Sie werden möglicherweise zu einem Browser umgeleitet, um sich zu registrieren. Nachdem Sie sich angemeldet haben, wechseln Sie zurück zur Power BI-APP, und melden Sie sich erneut an.

4.  Klicken Sie auf **Daten erhalten** , und klicken Sie dann auf **Weitere...** .

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  Klicken Sie auf **Azure**, **Azure Table Storage**, und klicken Sie dann auf **verbinden**.

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  Sie werden aufgefordert, die Tabellen- **URL** einzufügen, die Sie zuvor gesammelt haben ([in Schritt 13 von Kapitel 11](#chapter-11---create-table-service)), während Sie den Tabellen Speicherdienst erstellen. Nachdem Sie die URL eingefügt haben, löschen Sie den Teil des Pfads, der sich auf die Tabelle "Unterordner" bezieht (in diesem Kurs iotmessages). Das Endergebnis sollte wie in der folgenden Abbildung angezeigt werden. Klicken Sie dann auf **OK**.

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  Wenn Sie Ihre Table Storage erstellen, werden Sie aufgefordert, den von Ihnen notierten **Speicher Schlüssel** ([in Schritt 11 von Kapitel 11](#chapter-11---create-table-service)) hinzufügen. Klicken Sie dann auf **verbinden**.

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. Ein **Navigator Panel** wird angezeigt, und klicken Sie auf das Kontrollkästchen neben der Tabelle, und klicken Sie auf **Laden**.

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. Die Tabelle wurde nun auf Power BI geladen, erfordert jedoch eine Abfrage, um die darin angezeigten Werte anzuzeigen. Klicken Sie hierzu mit der rechten Maustaste auf den Tabellennamen, der sich im **Bereich Felder** auf der rechten Seite des Bildschirms befindet. Klicken Sie dann auf **Abfrage bearbeiten**.

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. Ein **Power Query-Editor** wird als neues Fenster geöffnet, in dem die Tabelle angezeigt wird. Klicken Sie in der *Inhalts* Spalte der Tabelle auf den Word- **Datensatz** , um den gespeicherten Inhalt visuell darzustellen.

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. Klicken Sie oben links im Fenster auf die **Tabelle**. 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. Klicken Sie auf **Schließen, & anwenden**.

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. Nachdem das Laden der Abfrage abgeschlossen ist, können Sie im **Bereich Felder**auf der rechten Seite des Bildschirms die Felder mit den Parametern **Name** und **Wert**versehen, um den Inhalt der **messagecontent** -Spalte visuell darzustellen.

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. Klicken Sie oben links im Fenster auf das blaue Datenträger **Symbol** , um die Arbeit in einem Ordner Ihrer Wahl zu speichern.

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. Sie können jetzt auf die Schaltfläche "veröffentlichen" klicken, um die Tabelle in Ihren Arbeitsbereich hochzuladen. Wenn Sie dazu aufgefordert werden, klicken Sie auf **Arbeitsbereich** und dann auf *auswählen* Warten Sie, bis das erfolgreiche Ergebnis der Übermittlung angezeigt wird.

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> Das folgende Kapitel ist hololens-spezifisch. Power BI derzeit nicht als immersive Anwendung verfügbar ist, können Sie die Desktop Version jedoch im Windows Mixed Reality-Portal (auch als "Klippe House" bezeichnet) über die Desktop-App ausführen.

## <a name="chapter-16---display-power-bi-data-on-hololens"></a>Kapitel 16: Anzeigen von Power BI Daten in hololens

1. Melden Sie sich auf Ihren hololens beim **Microsoft Store**an, indem Sie auf das zugehörige Symbol in der Anwendungsliste tippen.

    ![Power BI Hl](images/AzureLabs-Lab313-87.png)

2. Suchen Sie die **Power BI** Anwendung, und laden Sie Sie herunter.

    ![Power BI Hl](images/AzureLabs-Lab313-88.png)

3. Starten Sie **Power BI** aus der Anwendungsliste. 

4. **Power BI** werden Sie möglicherweise aufgefordert, sich bei Ihrem **Microsoft 365 Konto**anzumelden.

5. In der APP sollte der Arbeitsbereich standardmäßig angezeigt werden, wie in der folgenden Abbildung dargestellt. Wenn dies nicht der Fall ist, klicken Sie einfach auf das Arbeitsbereichs Symbol auf der linken Seite des Fensters.

    ![Power BI Hl](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a>Ihre IOT Hub Anwendung ist abgeschlossen.

Herzlichen Glückwunsch, Sie haben erfolgreich einen IOT Hub-Dienst mit einem simulierten VM Edge-Gerät erstellt. Ihr Gerät kann die Ergebnisse eines Machine Learning-Modells an einen Azure-Tabellen Dienst übermitteln, der von einem Azure-Funktionen-APP, der in Power BI gelesen und in einem Microsoft hololens visualisiert ist, ermöglicht wird.
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a>Bonus Übungen

### <a name="exercise-1"></a>Übung 1

Erweitern Sie die in der Tabelle gespeicherte Messaging Struktur, und zeigen Sie Sie als Diagramm an. Möglicherweise möchten Sie weitere Daten sammeln und in derselben Tabelle speichern, damit Sie später angezeigt werden.

### <a name="exercise-2"></a>Übung 2

Erstellen Sie ein zusätzliches Modul für die Kamera Erfassung, das auf dem IOT-Board bereitgestellt werden soll, damit es Bilder über die zu analysierende Kamera erfassen kann.
