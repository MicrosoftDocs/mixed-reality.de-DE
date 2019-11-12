---
title: Tutorials zu Azure Speech Services-1. Integrieren und Verwenden der Spracherkennung und-Aufzeichnung
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: defa33e56cfe4450a8d42855bd11dc23973dc401
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913402"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1. integrieren und Verwenden der Spracherkennung und-Aufzeichnung

In diesem Tutorial wird eine gemischte Reality-Anwendung erstellt, die die Verwendung des Azure Cognitive Services Speech SDK mit den hololens 2 untersucht. Wenn Sie diese tutorialreihe abgeschlossen haben, können Sie das Mikrofon Ihres Geräts verwenden, um Spracheingaben in Echtzeit zu übersetzen, Ihre Sprache in andere Sprachen übersetzen und die beabsichtigte Funktion des Speech SDK nutzen, um Sprachbefehle mithilfe von künstliche Intelligenz.

## <a name="objectives"></a>Ziele

- Erfahren Sie, wie Sie das Azure Speech SDK in eine hololens 2-Anwendung integrieren.
- Erfahren Sie, wie Sie Sprachbefehle verwenden.
- Informationen zur Verwendung von sprach-zu-Text-Funktionen

## <a name="instructions"></a>Anweisungen

### <a name="getting-started"></a>Erste Schritte

1. Starten Sie Unity, und erstellen Sie ein neues Projekt. Geben Sie das Lern Modul Project Name Speech SDK ein. Wählen Sie einen Speicherort für das Projekt aus. Klicken Sie dann auf Projekt erstellen.

    ![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

    >[!NOTE]
    >Stellen Sie sicher, dass die Vorlage auf 3D festgelegt ist, wie in der Abbildung oben gezeigt.

2. Laden Sie das [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [Foundation-Paketversion 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) herunter, und speichern Sie es in einem Ordner auf Ihrem PC. Importieren Sie das Paket in Ihr Unity-Projekt. Ausführliche Anweisungen dazu finden Sie in den Tutorials zu den ersten Schritten ( [Lektion 2). Initialisieren Ihres Projekts und der ersten Anwendung](mrlearning-base-ch1.md).

3. Laden Sie das Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) für das Unity-Ressourcenpaket herunter, und importieren Sie es. Importieren Sie das Sprach-SDK-Paket, indem Sie auf Objekte klicken, Paket importieren und dann benutzerdefiniertes Paket auswählen. Suchen Sie das zuvor heruntergeladene Sprach-SDK-Paket, und öffnen Sie es, um den Import Vorgang zu starten.

    ![mrlearning-Speech-CH1-1-step3a. png](images/mrlearning-speech-ch1-1-step3a.png)

    ![mrlearning-Speech-CH1-1-step3b. png](images/mrlearning-speech-ch1-1-step3b.png)

4. Klicken Sie im nächsten Popup Fenster auf Importieren, um mit dem Importieren des Sprach-SDK-Pakets zu beginnen. Stellen Sie sicher, dass alle Elemente wie in der folgenden Abbildung dargestellt geprüft werden.

    ![mrlearning-Speech-CH1-1-step4. png](images/mrlearning-speech-ch1-1-step4.png)

5. Laden Sie das Speech SDK Module Asset Pack herunter, das auch als lunarcom-Paket bekannt ist, indem Sie auf [diesen Link](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2)klicken. Das lunarcom-Asset-Paket ist eine Sammlung von Assets und Skripts, die für diese Lektion entwickelt wurden, um die praktische Verwendung des sprach-SDKs von Azure vorzustellen. Es handelt sich um ein Voice-Command-Terminal, das letztendlich eine Schnittstelle mit der in den Lernprogrammen "Getting Started" entwickelten Oberfläche für die Mond Modul Assembly bietet [. Erstellen einer Beispielanwendung für ein Mond Modul](mrlearning-base-ch6.md)

6. Importieren Sie das lunarcom-Asset-Paket in Ihr Unity-Projekt, indem Sie ähnliche Schritte ausführen, die Sie zum Importieren des Mixed Reality Toolkit und Sprach-SDK ausgeführt haben

7. Konfigurieren Sie das Mixed Reality Toolkit (mrtk).

    Klicken Sie hierzu oben in Ihrem Fenster auf das Mixed Reality Toolkit-Panel, und wählen Sie dann zu Szene hinzufügen und konfigurieren aus.

    ![mrlearning-Speech-CH1-1-step7a. png](images/mrlearning-speech-ch1-1-step7a.png)

    Wählen Sie im angezeigten Popup Fenster die Option DefaultHoloLens2ConfigurationProfile aus, um es als aktives Profil für das Mixed Reality Toolkit festzulegen.

    ![mrlearning-Speech-CH1-1-step7b. png](images/mrlearning-speech-ch1-1-step7b.png)

8. In Ihrer Szene gibt es nun mehrere neue Elemente aus der mrtk. Speichern Sie Ihre Szene unter einem anderen Namen, indem Sie auf "Datei" und dann auf "Speichern unter" klicken und der Szene "Sprech Szene" benennen.

    >[!NOTE]
    >Wenn Sie nach dem Hinzufügen des mrtk zum Projekt nach dem Hinzufügen des mrtk in Ihrer Szene spielen und nicht in den Wiedergabemodus wechseln, müssen Sie Unity möglicherweise neu starten.

9. Wenn das mixedrealitytoolkit-Objekt in ihrer Szenen Hierarchie ausgewählt ist, klicken Sie im Inspektor-Panel auf Kopieren & anpassen, um das Popup Profil zu öffnen. Geben Sie im Popup Profil-Popup Fenster einen passenden Namen für das benutzerdefinierte Profil ein, z. b. benutzerdefinierte HoloLens2ConfigurationProfile, und klicken Sie dann auf Klonen, um das benutzerdefinierte Konfigurations Profil zu erstellen und als aktives Profil festzulegen.

    ![mrlearning-Speech-CH1-1-step9. png](images/mrlearning-speech-ch1-1-step9.png)

10. Deaktivieren Sie außerdem im Inspektor-Panel (mit ausgewähltem mixedrealitytoolkit-Objekt in der Hierarchie) das Diagnosesystem, indem Sie das Kontrollkästchen rechts neben Diagnosesystem aktivieren deaktivieren.

    ![mrlearning-Speech-CH1-1-step10. png](images/mrlearning-speech-ch1-1-step10.png)

11. In diesem Tutorial verwenden wir die Eingabe Sprachbefehle für die Spracherkennung und-Aufzeichnung. Mit dieser Einstellung können Sie das Eingabe Profil Klonen, um Änderungen an den Spracheinstellungen vorzunehmen.

    Wenn das mixedrealitytoolkit-Objekt in ihrer Szenen Hierarchie noch ausgewählt ist, klicken Sie im Inspektor-Panel auf die Schaltfläche kleiner Klon, um das Popup Profil zu öffnen. Geben Sie im Popup Profil-Popup Fenster einen passenden Namen für das benutzerdefinierte Profil ein, z. b. benutzerdefiniertes HoloLens2InputSystemProfile, und klicken Sie dann auf Klonen, um das benutzerdefinierte Eingabe Systemprofil zu erstellen und als aktives Profil festzulegen.

    ![mrlearning-Speech-CH1-1-step11. png](images/mrlearning-speech-ch1-1-step11.png)

12. Nachdem das Eingabe Profil geklont wurde, erweitern Sie den Sprachabschnitt, und befolgen Sie den gleichen Prozess wie im vorherigen Schritt, um das Profil für Sprachbefehle zu klonen.

    ![mrlearning-Speech-CH1-1-step12. png](images/mrlearning-speech-ch1-1-step12.png)

13. Wechseln Sie im Abschnitt "Sprache" zu "Allgemeine Einstellungen", und ändern Sie das Startverhalten in "manuell starten"

    ![mrlearning-Speech-CH1-1-step13. png](images/mrlearning-speech-ch1-1-step13.png)

14. Erweitern Sie im Projekt Panel den Ordner lunarcom, und ziehen Sie den Lunarcom_Base Prefab in Ihre Szenen Hierarchie.

    ![mrlearning-Speech-CH1-1-step14. png](images/mrlearning-speech-ch1-1-step14.png)

15. Wählen Sie das Lunarcom_Base Objekt in der Hierarchie aus, und stellen Sie sicher, dass die Position auf x = 0, y = 0 und z = 0 festgelegt ist, und dass die Drehung auf x = 0, y = 0 und z = 0 festgelegt ist. Legen Sie Skalierung auf Read x = 0.008, y = 0.008 und z = 0,01 fest.

    ![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. Klicken Sie auf Komponente hinzufügen, suchen Sie nach dem lunarcom-Controller. Dieses Skript ist in dem lunarcom-Asset Pack enthalten, das Sie in Schritt 6 importiert haben.

    ![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. Zum Verbinden der Anwendung mit Azure Cognitive Services müssen Sie einen Abonnement Schlüssel (auch als API-Schlüssel bezeichnet) für den Sprachdienst eingeben. Befolgen Sie die [hier](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) aufgeführten Anweisungen, um einen kostenlosen Abonnement Schlüssel zu erhalten. Nachdem Sie den Abonnement Schlüssel erhalten haben, geben Sie ihn in das Feld Sprachdienst-API-Schlüssel der lunarcomcontroller-Komponente im Inspektor-Panel ein, wie in der folgenden Abbildung dargestellt.

18. Geben Sie die Region, die Sie bei der Registrierung für den Abonnement Schlüssel ausgewählt haben, in das Feld Sprachdienst Region der Komponente lunarcomcontroller im Inspektor-Panel ein. Beispiel: für die Region "USA, Westen" geben Sie "westus" ein.

    ![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. Erweitern Sie in der-Hierarchie das Lunarcom_Base Objekt, indem Sie auf den Pfeil auf der linken Seite klicken. Führen Sie dann die gleichen Schritte für das untergeordnete Objekt "Terminal" aus, wie in der folgenden Abbildung dargestellt.

20. Wenn Lunarcom_Base ausgewählt ist, klicken Sie auf den Text "lunarcom-Text", und ziehen Sie ihn aus der Hierarchie in den Ausgabe Text Slot der Komponente "lunarcomcontroller" im Inspektor-Panel, wie in der folgenden Abbildung dargestellt

21. Führen Sie das gleiche mit dem Terminal Objekt im Terminal Slot und dem Verbindungs Lichtobjekt zum Verbindungs Licht-Controller Slot aus.

    ![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. Klicken Sie im Inspektor-Panel auf den Pfeil neben dem Abschnitt lunarcom-Schaltflächen des Skripts lunarcomcontroller, und ändern Sie die Größe in 3. Drücken Sie die EINGABETASTE oder zurück. Dies bewirkt, dass drei neue Element Felder angezeigt werden.

    ![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. Erweitern Sie die Schaltflächen "lunarcom", indem Sie auf den Pfeil neben dem Pfeil in der Hierarchie klicken, und verwenden Sie denselben Prozess wie oben, und ziehen Sie die MIC-, Satelliten-und Rocket-gameobjects in den Verweis auf das Element 0, 1 und 2 in der Komponente "lunarcomcontroller" im Inspektor-Panel.

    ![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. Wählen Sie das Lunarcom_Base "-Objekt in der Hierarchie aus. Klicken Sie im Inspektor-Panel auf Komponente hinzufügen, und suchen Sie nach der lunarcom-Spracherkennung. Wiederholen Sie dieselben Schritte, um lunarcom Wake-Word-Erkennungs Modul hinzuzufügen.

    ![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. Geben Sie im textslot reaktivieren den Text Terminal aktivieren ein. Geben Sie im textslot verwerfen den Namen Terminal Terminal ein.

    ![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

### <a name="build-your-application-to-your-device"></a>Erstellen Ihrer Anwendung auf Ihrem Gerät

1. Öffnen Sie erneut das Fenster Buildeinstellungen, indem Sie zu Datei > Buildeinstellungen navigieren.

    ![Images/mrlearning-Speech-CH1-2-Schritt 1](images/mrlearning-speach-ch1-2-step1.jpg)

2. Stellen Sie sicher, dass die Szene, die Sie testen möchten, in der Liste „Szenen in Build“ enthalten ist, indem Sie auf die Schaltfläche „Offene Szenen hinzufügen“ klicken.

3. Klicken Sie auf die Schaltfläche Player Einstellungen, und wechseln Sie zu Veröffentlichungs Einstellungen. Aktivieren Sie unter "Funktionen" Folgendes: Internet, Internet Client Server, privater Netzwerkclient Server, Mikrofon und räumliche Wahrnehmung.

4. Wechseln Sie in den gleichen Player Einstellungen zu "XR Settings", und wählen Sie die virtuelle Realität aus, die unterstützt wird.

5. Klicken Sie auf die Schaltfläche „Erstellen“, um den Buildprozess zu starten.

    ![mrlearning-Speech-CH1-2-Schritt 5](images/mrlearning-speach-ch1-2-step5.jpg)

6. Erstellen und benennen Sie einen neuen Ordner für Ihre Anwendung. In der folgenden Abbildung können Sie sehen, dass ein Ordner mit dem Namen „App“ erstellt wurde, der die Anwendung enthalten soll. Klicken Sie auf „Ordner auswählen“, um mit der Erstellung im neu erstellten Ordner zu beginnen. Nach Abschluss der Erstellung (des Buildvorgangs) können Sie in Unity das Fenster „Buildeinstellungen“ schließen.

    ![mrlearning-Speech-CH1-2-Schritt 6](images/mrlearning-speach-ch1-2-step6.jpg)

    >[!NOTE]
    >Wenn der Vorgang fehlschlägt, wiederholen Sie den Buildvorgang, oder starten Sie Unity neu, und wiederholen Sie dann den Buildvorgang. Wenn ein Fehler wie "Fehler: CS0246 = der Typ-oder Namespace Name" XX "nicht gefunden werden konnte (fehlt eine using-Direktive oder ein Assemblyverweis?), müssen Sie möglicherweise das [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>) installieren.

7. Öffnen Sie nach Abschluss des Buildvorgangs den neu erstellten Ordner, der Ihre neu erstellten Anwendungsdateien enthält. Doppelklicken Sie auf die Projektmappendatei ". sln", um die Projektmappendatei in Visual Studio zu öffnen.

    >[!NOTE]
    >Achten Sie darauf, dass Sie den neu erstellten Ordner öffnen (also den Ordner „App“, wenn Sie die Namenskonventionen in den vorherigen Schritten befolgt haben), weil außerhalb dieses Ordners noch eine SLN-Datei mit einem ähnlichen Namen vorhanden ist, die nicht mit der SLN-Datei im Buildordner verwechselt werden darf. 

    ![mrlearning-Speech-CH1-2-STEP7](images/mrlearning-speach-ch1-2-step7.jpg)

    >[!NOTE]
    >Wenn Sie von Visual Studio zur Installation neuer Komponenten aufgefordert werden, nehmen Sie sich einen Moment Zeit, um zu überprüfen, ob alle erforderlichen Komponenten (wie auf der Seite [Installieren der Tools](install-the-tools.md) angegeben) installiert sind.

8. Schließen Sie das HoloLens 2-Gerät über das USB-Kabel an Ihren PC an. Bei diesen Lektionsanweisungen wird davon ausgegangen, dass Sie einen Test mit einem HoloLens 2-Gerät bereitstellen. Sie können die Bereitstellung aber auch auf dem [HoloLens 2-Emulator](using-the-hololens-emulator.md) vornehmen oder ein [App-Paket für das Querladen](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>) erstellen.

9. Stellen Sie vor dem Erstellen der App auf Ihrem Gerät sicher, dass sich das Gerät im Entwicklermodus befindet. Wenn das Ihre erste Bereitstellung auf dem HoloLens 2-Gerät ist, werden Sie möglicherweise von Visual Studio aufgefordert, Ihr HoloLens 2-Gerät mit einer PIN zu koppeln. Folgen Sie [diesen Anweisungen](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio), wenn Sie den Entwicklermodus aktivieren oder das Gerät mit Visual Studio koppeln müssen.

10. Konfigurieren Sie Visual Studio für die Erstellung auf Ihrem HoloLens 2-Gerät, indem Sie die Konfiguration „Release“ und die Architektur „ARM“ auswählen.

    ![mrlearning-Speech-CH1-2-step10](images/mrlearning-speach-ch1-2-step10.jpg)

11. Der letzte Schritt ist die Erstellung auf Ihrem Gerät durch Auswählen von „Debuggen“ > „Starten ohne Debuggen“. Wenn Sie „Starten ohne Debuggen" auswählen, wird die Anwendung sofort nach einem erfolgreichen Buildvorgang auf Ihrem Gerät gestartet, ohne dass jedoch Debuginformationen in Visual Studio angezeigt werden. Dies bedeutet auch, dass Sie das USB-Kabel entfernen können, während Ihre Anwendung auf Ihrem HoloLens 2-Gerät ausgeführt wird, ohne dass die Anwendung beendet wird. Sie können auch „Build“ > „Projektmappe bereitstellen“ auswählen, um die Anwendung auf Ihrem Gerät bereitzustellen, ohne dass sie automatisch gestartet wird.

    ![mrlearning-Speech-CH1-2-step11. JPG](images/mrlearning-speach-ch1-2-step11.jpg)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben die Spracherkennung in Ihrer Anwendung mithilfe von Azure eingerichtet. Führen Sie die Anwendung aus, um sicherzustellen, dass alle Funktionen und Funktionen ordnungsgemäß funktionieren. Beginnen Sie mit der Verwendung des Wake-Worts, das Sie in Schritt 22 eingegeben haben, aktivieren Sie Terminal. Wählen Sie die Schaltfläche Mikrofon, um die Spracherkennung zu starten. Sprechen Sie. Sie sehen, dass Ihre Wörter im Terminal bei der Sprachübertragung überschrieben werden. Drücken Sie ein zweites Mal die Mikrofon Schaltfläche, um die Spracherkennung anzuhalten. Nehmen Sie an, Terminal schließen, um das lunarcom-Terminal auszublenden In der nächsten Lektion erfahren Sie, wie Sie mithilfe der Geräte gestützten Spracherkennung in Situationen, in denen das Sprach-SDK von Azure nicht verfügbar ist, dynamisch wechseln, weil die hololens 2 offline sind.

[Nächstes Tutorial: 2. Hinzufügen eines Offline Modus für die lokale Sprachübersetzung](mrlearning-speechSDK-ch2.md)
