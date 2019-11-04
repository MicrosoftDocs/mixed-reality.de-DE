---
title: Tutorials zu Azure Speech Services-1. Integrieren und Verwenden der Spracherkennung und-Aufzeichnung
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie das Azure Speech SDK in einer Mixed Reality-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens
ms.openlocfilehash: 4baef90f8e00e5da1063c708ae24d2057e0dc227
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438375"
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

> Hinweis: Stellen Sie sicher, dass die Vorlage auf "3D" festgelegt ist, wie in der Abbildung oben gezeigt.

2. Laden Sie das [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity-Paket herunter, und speichern Sie es in einem Ordner auf Ihrem PC. Importieren Sie das Paket in Ihr Unity-Projekt. Ausführliche Anweisungen hierzu finden Sie in der [Lektion 1 des Basismoduls](mrlearning-base-ch1.md). 

3. Laden Sie das Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) für das Unity-Ressourcenpaket herunter, und importieren Sie es. Importieren Sie das Sprach-SDK-Paket, indem Sie auf Objekte klicken, Paket importieren und dann benutzerdefiniertes Paket auswählen. Suchen Sie das zuvor heruntergeladene Sprach-SDK-Paket, und öffnen Sie es, um den Import Vorgang zu starten. 

![Module4Chapter1step3ima](images/module4chapter1step3ima.PNG)

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. Klicken Sie im nächsten Popup Fenster auf Importieren, um mit dem Importieren des Sprach-SDK-Pakets zu beginnen. Stellen Sie sicher, dass alle Elemente wie in der folgenden Abbildung dargestellt geprüft werden.

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)

5. Laden Sie das Speech SDK Module Asset Pack herunter, das auch als lunarcom-Paket bekannt ist, indem Sie auf [diesen Link](https://github.com/microsoft/MixedRealityLearning/releases/tag/Speech_2)klicken. Das lunarcom-Asset-Paket ist eine Sammlung von Assets und Skripts, die für diese Lektion entwickelt wurden, um die praktische Verwendung des sprach-SDKs von Azure vorzustellen. Es handelt sich um ein Voice-Command-Terminal, das letztendlich eine Schnittstelle mit der Oberfläche [für die Mond](mrlearning-base-ch6.md) Modul Assembly bietet

6. Importieren Sie das lunarcom-Asset-Paket in Ihr Unity-Projekt, indem Sie ähnliche Schritte ausführen, die Sie zum Importieren des Mixed Reality Toolkit und Sprach-SDK ausgeführt haben
7. Konfigurieren Sie das Mixed Reality Toolkit (mrtk). Klicken Sie hierzu oben in Ihrem Fenster auf das Mixed Reality Toolkit-Panel, und wählen Sie dann zu Szene hinzufügen und konfigurieren aus.

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

![module4Chapter1step9ima](images/module4chapter1step9ima.PNG)

![module4Chapter1step9imb](images/module4chapter1step9imb.PNG)

8. In Ihrer Szene gibt es nun mehrere neue Elemente aus der mrtk. Speichern Sie Ihre Szene unter einem anderen Namen, indem Sie auf "Datei" und dann auf "Speichern unter" klicken und der Szene "Sprech Szene" benennen. 

> Hinweis: Wenn Sie nach dem Hinzufügen des mrtk zum Projekt in Ihrer Szene auf "Play" klicken und der Wiedergabemodus nicht in den Wiedergabemodus wechselt, müssen Sie Unity möglicherweise neu starten. 

9. Wenn das mixedrealitytoolkit-Objekt in Ihrer Hierarchie ausgewählt ist, klicken Sie im Inspektor-Panel auf Kopieren und anpassen.

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. Deaktivieren Sie außerdem im Inspektor-Panel (mit ausgewähltem mixedrealitytoolkit-Objekt in der Hierarchie) das Diagnosesystem, indem Sie das Kontrollkästchen rechts neben Diagnosesystem aktivieren deaktivieren.

![Module4Chapter1step9imd](images/module4chapter1step9imd.PNG)

11. Um Sprachbefehle zu aktivieren, wählen Sie das neu erstellte mrtk-Profil aus, das angepasst werden soll. In diesem Tutorial verwenden wir die Eingabe Sprachbefehle für die Spracherkennung und-Aufzeichnung. Mit dieser Einstellung können Sie das Eingabe Profil Klonen, um Änderungen an den Spracheinstellungen vorzunehmen.

![Module4Chapter1step11imb](images/module4chapter1step11imb.PNG)

![Module4Chapter1step11imd](images/module4chapter1step11imd.PNG)

12. Nachdem das Eingabe Profil geklont wurde, wechseln Sie zu Sprachbefehlen, und Klonen Sie die Sprachbefehle.

![Module4Chapter1step12imb](images/module4chapter1step12imb.PNG)

![Module4Chapter1step12imc](images/module4chapter1step12imc.PNG)

13. Wechseln Sie nun unter Sprachbefehle zu "Allgemeine Einstellungen", und legen Sie "Startverhalten" auf "manueller Start" fest.

![Module4Chapter1step13imb](images/module4chapter1step13imb.PNG)

14. Erweitern Sie im Projekt Panel den Ordner lunarcom, und ziehen Sie den Lunarcom_Base Prefab in ihre Hierarchie.

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

15. Wählen Sie das Lunarcom_Base-Objekt in der Hierarchie aus, und stellen Sie sicher, dass die Position auf x = 0, y = 0 und z = 0 festgelegt ist, und dass die Drehung auf x = 0, y = 0 und z = 0 festgelegt ist. Legen Sie Skalierung auf Read x = 0.008, y = 0.008 und z = 0,01 fest.

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

16. Klicken Sie auf Komponente hinzufügen, suchen Sie nach, und wählen Sie lunarcomcontroller aus. Dieses Skript ist in dem lunarcom-Asset Pack enthalten, das Sie in Schritt 6 importiert haben.

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

17. Zum Verbinden der Anwendung mit Azure Cognitive Services müssen Sie einen Abonnement Schlüssel (auch als API-Schlüssel bezeichnet) für den Sprachdienst eingeben. Befolgen Sie die [hier](https://docs.microsoft.com//azure/cognitive-services/speech-service/get-started) aufgeführten Anweisungen, um einen kostenlosen Abonnement Schlüssel zu erhalten. Nachdem Sie den Abonnement Schlüssel erhalten haben, geben Sie ihn in das Feld Sprachdienst-API-Schlüssel der lunarcomcontroller-Komponente im Inspektor-Panel ein, wie in der folgenden Abbildung dargestellt.

18. Geben Sie die Region, die Sie bei der Registrierung für den Abonnement Schlüssel ausgewählt haben, in das Feld Sprachdienst Region der Komponente lunarcomcontroller im Inspektor-Panel ein. Geben Sie beispielsweise für die Region "USA, Westen" in "westus" ein.

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

19. Erweitern Sie in der-Hierarchie das Lunarcom_Base-Objekt, indem Sie auf den Pfeil links neben dem Objekt klicken. Führen Sie dann die gleichen Schritte für das untergeordnete Objekt "Terminal" aus, wie in der folgenden Abbildung dargestellt.

20. Während Lunarcom_Base ausgewählt ist, klicken und ziehen Sie den Text "lunarcom-Text" aus der Hierarchie in den Ausgabe Text Slot in der Komponente "lunarcomcontroller" im Inspektor-Panel, wie in der folgenden Abbildung dargestellt.

21. Führen Sie das gleiche mit dem Terminal Objekt im Terminal Slot und dem Verbindungs Lichtobjekt zum Verbindungs Licht-Controller Slot aus.

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

22. Klicken Sie im Inspektor-Panel auf den Pfeil neben dem Abschnitt lunarcom-Schaltflächen des Skripts lunarcomcontroller, und ändern Sie die Größe in 3. Drücken Sie die EINGABETASTE oder zurück. Dies bewirkt, dass drei neue Element Felder angezeigt werden.

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

23. Erweitern Sie die Schaltflächen "lunarcom", indem Sie auf den Pfeil neben dem Pfeil in der Hierarchie klicken, und verwenden Sie denselben Prozess wie oben, und ziehen Sie die MIC-, Satelliten-und Rocket-gameobjects in den Verweis auf das Element 0, 1 und 2 in der Komponente "lunarcomcontroller" im Inspektor-Panel. 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

24. Wählen Sie das Lunarcom_Base-Objekt in Ihrer Hierarchie aus. Klicken Sie im Inspektor-Panel auf Komponente hinzufügen, suchen Sie nach und wählen Sie die Option lunarcomwakewordrecognizer aus.

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

25. Geben Sie im textslot reaktivieren den Text Terminal aktivieren ein. Geben Sie im textslot verwerfen den Namen Terminal Terminal ein.

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

### <a name="build-your-application-to-your-device"></a>Erstellen Ihrer Anwendung auf Ihrem Gerät

1. Öffnen Sie erneut das Fenster Buildeinstellungen, indem Sie zu Datei > Buildeinstellungen navigieren.

![Lesson1 Chapter5 Schritt 1](images/Lesson1Chapter5Step1.JPG)

2. Stellen Sie sicher, dass die Szene, die Sie testen möchten, in der Liste „Szenen in Build“ enthalten ist, indem Sie auf die Schaltfläche „Offene Szenen hinzufügen“ klicken.
3. Klicken Sie auf die Schaltfläche Player Einstellungen, und wechseln Sie zu Veröffentlichungs Einstellungen. Aktivieren Sie unter "Funktionen" Folgendes: Internet, Internet Client Server, privater Netzwerkclient Server, Mikrofon und räumliche Wahrnehmung.
4. Wechseln Sie in den gleichen Player Einstellungen zu "XR Settings", und wählen Sie die virtuelle Realität aus, die unterstützt wird.
5. Klicken Sie auf die Schaltfläche „Erstellen“, um den Buildprozess zu starten.

![Lesson1 Chapter5 Schritt 3](images/Lesson1Chapter5Step3.JPG)

6. Erstellen und benennen Sie einen neuen Ordner für Ihre Anwendung. In der folgenden Abbildung können Sie sehen, dass ein Ordner mit dem Namen „App“ erstellt wurde, der die Anwendung enthalten soll. Klicken Sie auf „Ordner auswählen“, um mit der Erstellung im neu erstellten Ordner zu beginnen. Nach Abschluss der Erstellung (des Buildvorgangs) können Sie in Unity das Fenster „Buildeinstellungen“ schließen. 

![Lesson1 Chapter5 Schritt 4](images/Lesson1Chapter5Step4.JPG)

> Hinweis: Wenn der Build fehlschlägt, versuchen Sie es erneut, oder starten Sie Unity neu, und erstellen Sie es erneut. Wenn ein Fehler wie "Fehler: CS0246 = der Typ-oder Namespace Name" XX "nicht gefunden werden konnte (fehlt eine using-Direktive oder ein Assemblyverweis?), müssen Sie möglicherweise das [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com//windows/downloads/windows-10-sdk>) installieren.

7. Öffnen Sie nach Abschluss des Buildvorgangs den neu erstellten Ordner, der Ihre neu erstellten Anwendungsdateien enthält. Doppelklicken Sie auf die Projektmappendatei ". sln", um die Projektmappendatei in Visual Studio zu öffnen.

> Hinweis: Stellen Sie sicher, dass Sie den neu erstellten Ordner (d. h. den Ordner "App") öffnen, wenn Sie die Benennungs Konventionen aus den vorherigen Schritten befolgen), da eine ähnlich benannte sln-Datei außerhalb des Ordners vorhanden ist, die nicht mit der SLN-Datei im Buildordner verwechselt werden muss. 

![Lektion1 Kapitel5 Schritt5](images/Lesson1Chapter5Step5.JPG)

> Hinweis: Wenn Sie von Visual Studio aufgefordert werden, neue Komponenten zu installieren, nehmen Sie sich einen Moment Zeit, um sicherzustellen, dass alle erforderlichen Komponenten installiert sind, wie auf [der Seite "Tools installieren"](install-the-tools.md) angegeben.

8. Schließen Sie das HoloLens 2-Gerät über das USB-Kabel an Ihren PC an. Bei diesen Lektionsanweisungen wird davon ausgegangen, dass Sie einen Test mit einem HoloLens 2-Gerät bereitstellen. Sie können die Bereitstellung aber auch auf dem [HoloLens 2-Emulator](using-the-hololens-emulator.md) vornehmen oder ein [App-Paket für das Querladen](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>) erstellen.
9. Stellen Sie vor dem Erstellen der App auf Ihrem Gerät sicher, dass sich das Gerät im Entwicklermodus befindet. Wenn das Ihre erste Bereitstellung auf dem HoloLens 2-Gerät ist, werden Sie möglicherweise von Visual Studio aufgefordert, Ihr HoloLens 2-Gerät mit einer PIN zu koppeln. Folgen Sie [diesen Anweisungen](https://docs.microsoft.com//windows/mixed-reality/using-visual-studio), wenn Sie den Entwicklermodus aktivieren oder das Gerät mit Visual Studio koppeln müssen.

10. Konfigurieren Sie Visual Studio für die Erstellung auf Ihrem HoloLens 2-Gerät, indem Sie die Konfiguration „Release“ und die Architektur „ARM“ auswählen.

![Lesson1 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)

11. Der letzte Schritt ist die Erstellung auf Ihrem Gerät durch Auswählen von „Debuggen“ > „Starten ohne Debuggen“. Wenn Sie „Starten ohne Debuggen" auswählen, wird die Anwendung sofort nach einem erfolgreichen Buildvorgang auf Ihrem Gerät gestartet, ohne dass jedoch Debuginformationen in Visual Studio angezeigt werden. Dies bedeutet auch, dass Sie das USB-Kabel entfernen können, während Ihre Anwendung auf Ihrem HoloLens 2-Gerät ausgeführt wird, ohne dass die Anwendung beendet wird. Sie können auch „Build“ > „Projektmappe bereitstellen“ auswählen, um die Anwendung auf Ihrem Gerät bereitzustellen, ohne dass sie automatisch gestartet wird.

![Lesson1 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben die Spracherkennung in Ihrer Anwendung mithilfe von Azure eingerichtet. Führen Sie die Anwendung aus, um sicherzustellen, dass alle Funktionen und Funktionen ordnungsgemäß funktionieren. Beginnen Sie mit der Verwendung des Wake-Worts, das Sie in Schritt 22 eingegeben haben, aktivieren Sie Terminal. Wählen Sie die Schaltfläche Mikrofon, um die Spracherkennung zu starten. Sprechen Sie. Sie sehen, dass Ihre Wörter im Terminal bei der Sprachübertragung überschrieben werden. Drücken Sie ein zweites Mal die Mikrofon Schaltfläche, um die Spracherkennung anzuhalten. Nehmen Sie an, Terminal schließen, um das lunarcom-Terminal auszublenden In der nächsten Lektion erfahren Sie, wie Sie mithilfe der Geräte gestützten Spracherkennung in Situationen, in denen das Sprach-SDK von Azure nicht verfügbar ist, dynamisch wechseln, weil die hololens 2 offline sind.

[Nächstes Tutorial: 2. Hinzufügen eines Offline Modus für die lokale Sprachübersetzung](mrlearning-speechSDK-ch2.md)

