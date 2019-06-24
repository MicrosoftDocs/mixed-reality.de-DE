# <a name="speech-sdk-learning-module"></a>Spracherkennungs-SDK-Learning-Modul

In diesem Tutorial erstellen Sie eine Mixed Reality-Anwendung, die die Verwendung von Azure Cognitive Services Speech SDK mit dem HoloLens 2 untersucht. Wenn in dieser tutorialreihe abgeschlossen ist, werden Sie verwenden Ihre Gerätemikrofon Spracherkennung in Echtzeit zu transkribieren und übersetzen die Spracherkennung in andere Sprachen nutzen die Speech SDK beabsichtigte Funktion mit Sprachbefehle verstehen künstliche Intelligenz.

Ziele:

- Erfahren Sie, wie das Azure-Spracherkennungs-SDK in eine HoloLens-2-Anwendung zu integrieren.
- Erfahren Sie, wie Sie mithilfe von Sprachbefehlen
- Informationen Sie zum Verwenden von Sprache-zu-Text-Funktionen

## <a name="instructions"></a>Anweisungen

### <a name="getting-started"></a>Erste Schritte

1. Starten Sie Unity aus, und Erstellen eines neuen Projekts. Geben Sie den Namen des Projekts "Speech SDK Lernmodul." Wählen Sie einen Speicherort, an die Ihr Projekt zu speichern. Klicken Sie dann auf "Create Project".

![Module2Chapter3step1im](images/module4chapter1step1im.PNG)

> Hinweis: Stellen Sie sicher, dass die Vorlage "3D" festgelegt ist, wie in der Abbildung oben gezeigt.

2. Herunterladen der [Mixed Reality-Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.unitypackage) Unity-Paket, und speichern Sie es in einem Ordner auf Ihrem PC. Importieren Sie das Paket in Ihr Unity-Projekt ein. Ausführliche Anleitungen hierzu finden Sie unter [Basismodul Lektion 1](mrlearning-base-ch1.md). 

3. Herunterladen und importieren Sie das Azure [Speech SDK](https://aka.ms/csspeech/unitypackage) für Unity Asset-Paket. Importieren Sie das Speech SDK-Paket durch Klicken auf "Ressourcen", "Paket importieren," Wählen Sie dann auf "benutzerdefinierte Package" auswählen Ermitteln Sie die zuvor heruntergeladene Speech SDK-Paket aus, und öffnen Sie sie um den Importvorgang zu starten. 

![Module4Chapter1step3im](images/module4chapter1step3im.PNG)

4. Klicken Sie im nächsten Popup-Fenster auf "Import" zum Importieren von dem Speech SDK-Paket. Stellen Sie sicher, dass alle Elemente aktiviert sind, wie in der folgenden Abbildung dargestellt.

![Module4Chapter1step4im](images/module4chapter1step4im.PNG)


5. Herunterladen der [Lunarcom](https://github.com/levilais/Speech-SDK-Module/raw/master/Speech SDK Module/Lunarcom.unitypackage) Asset-Paket. Das Lunarcom-Asset-Paket ist eine Sammlung von Ressourcen und Skripts, die für diese Lektion Reihe entwickelt, eine praktische Verwendung von Azure Speech SDK zu veranschaulichen. Es ist ein Voice-Command-Terminal, letztendlich mit der die Mondkalender Modul Assembly Erfahrung in entwickelt werden die [Base Modul Tutorial.](mrlearning-base-ch6.md)
6. Importieren Sie das Lunarcom Asset-Paket in Ihr Unity-Projekt, indem Sie ähnliche Schritte, die Sie vorgenommen haben, um die Mixed Reality-Toolkit und dem Speech SDK zu importieren.
7. Konfigurieren Sie die Mixed Reality-Toolkits (MRTK). Zu diesem Zweck klicken Sie auf den Bereich "Mixed Reality-Toolkit" in der oberen Rand des Fensters, und wählen Sie dann auf "Hinzufügen der Szene" und "konfigurieren".

![Module4Chapter1step7im](images/module4chapter1step7im.PNG)

8. Die Szene wird nun mehrere neue Elemente aus der MRTK enthalten. Speichern Sie Ihre Szene unter einem anderen Namen durch Klicken auf "File" "Speichern unter" klicken Sie dann, und nennen Sie die Szene "SpeechScene" an. 

   > Hinweis: Wenn Sie die entsprechende Schaltfläche in der Szene drücken, nachdem Sie die MRTK zu Ihrem Projekt hinzufügen und sie nicht den Modus "Wiedergabe" eingeben, müssen Sie Unity neu zu starten. 

9. Klicken Sie mit dem "MixedRealityToolkit"-Objekt, das in der Hierarchie ausgewählt ist auf "kopieren und Anpassen von" in den Bereich der Eigenschaftenanalyse.

![Module4Chapter1step9im](images/module4chapter1step9im.PNG)

10. Auch im Bereich Inspector (mit dem "MixedRealityToolkit"-Objekt, das in der Hierarchie ausgewählt ist), indem Sie das Kontrollkästchen rechts neben "Aktivieren der Diagnose-System". deaktivieren Sie das Diagnostics-system

![Module4Chapter1step10im](images/module4chapter1step10im.PNG)

11. Klicken Sie im Projektpanel erweitern Sie den Ordner "Lunarcom", und ziehen Sie das Prefab "Lunarcom_Base" in Ihrer Hierarchie.

![Module4Chapter1step11im](images/module4chapter1step11im.PNG)

12. Wählen Sie das Objekt "Lunarcom_Base" in Ihrer Hierarchie und stellen Sie sicher, dass die Position, auf x festgelegt ist = 0, y = 0 und Z = 0, sowie die Drehung, legen Sie auf X = 0, y = 0 und Z = 0. Die Skalierungsgruppe lesen X = 0,008 Dollar, y = 0,008-Dollar und Z = 0,01.

![Module4Chapter1step12im](images/module4chapter1step12im.PNG)

13. Klicken Sie auf "Komponente hinzufügen", und suchen Sie nach, und wählen Sie "LunarcomController." Dieses Skript ist in der Lunarcom ressourcenpaket enthalten, die Sie in Schritt 6 importiert.

![Module4Chapter1step13im](images/module4chapter1step13im.PNG)

14. Um die app mit Azure Cognitive Services verbinden zu können, müssen Sie einen "Subscription-Key" auch bekannt als "API-Key" für den Dienst der Sprache eingeben. Befolgen Sie die Anweisungen unter [diesen Link](https://docs.microsoft.com/en-us/azure/cognitive-services/speech-service/get-started) um ein kostenloses Abonnement-Schlüssel zu erhalten. Nachdem Sie den Abonnementschlüssel erhalten haben, geben Sie ihn in das Feld "Speech-Dienst-API-Key" der Komponente "LunarcomController" im Bereich mit den Inspektor wie in der folgenden Abbildung dargestellt.

15. Geben Sie die Region, die Sie ausgewählt haben, wenn Sie für den Abonnementschlüssel in das Feld "Speech Service-Region", der im Bedienfeld "Inspector" Komponente "LunarcomController" registriert haben.

![Module4Chapter1step15im](images/module4chapter1step15im.PNG)

16. Klicken Sie in Ihrer Hierarchie erweitern Sie das Objekt "Lunarcom_Base" durch Klicken auf den Pfeil, um die links von ihm, und Gleiches gilt für das untergeordnete Objekt, "Terminaldienste", wie in der folgenden Abbildung dargestellt.

17. Wenn "Lunarcom_Base" ausgewählt ist, klicken Sie, und ziehen Sie "Lunarcom Text" aus der Hierarchie im Slot "Ausgabetext" in der Komponente "LunarcomController" im Bereich mit den Inspektor, wie in der folgenden Abbildung dargestellt.
18. Führen Sie dieselben Schritte mit dem Objekt "Terminalserver" nun in den Slot "Terminaldienste" und das Objekt "Verbindung Light" im Slot "Verbindung Light-Controller".

![Module4Chapter1step18im](images/module4chapter1step18im.PNG)

19. Klicken Sie auf den Pfeil neben "Lunarcom Schaltflächen"-Abschnitt des Skripts "LunarcomController" in den Bereich der Eigenschaftenanalyse, und Ändern der Größe nach 3, und drücken Sie die EINGABETASTE oder die Return-Taste auf der Tastatur. Dadurch werden drei neue "Element"-Felder angezeigt werden.

![Module4Chapter1step19im](images/module4chapter1step19im.PNG)

20. Erweitern Sie die "Lunarcom Schaltflächen" durch Klicken auf den Pfeil daneben in Ihrer Hierarchie Drag & Drop, verwenden die gleiche Vorgehensweise wie oben beschrieben, die Mic Satelliten und Rocket "gameobjects", 0, 1 und 2 Elementverweise bzw. in der "LunarcomController"-Komponente in der Bereich der Eigenschaftenanalyse. 

![Module4Chapter1step18im](images/module4chapter1step20im.PNG)

21. Wählen Sie das "Lunarcom_Base"-Objekt, in der Hierarchie. Klicken Sie auf "Komponente hinzufügen" im Bedienfeld "Inspector", und suchen Sie nach, und wählen Sie "LunarcomWakeWordRecognizer."

![Module4Chapter1step18im](images/module4chapter1step21im.PNG)

22. Geben Sie in den Slot "Wake Wort" "Aktivieren von Terminal". Darüber hinaus im Slot "Wort schließen", geben Sie in "Verwerfen Terminal".

![Module4Chapter1step18im](images/module4chapter1step22im.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben in Ihrer Anwendung, mit der Azure Spracherkennung eingerichtet! Führen Sie die Anwendung aus, um sicherzustellen, dass alle Funktionen ordnungsgemäß funktionieren. Beginnen Sie mit der Aktivierung Wort, die Sie in Schritt 22, "Aktivieren-Terminal." eingegeben Wählen Sie dann die Schaltfläche "Mikrofon", starten Sie die Spracherkennung und beginnen, sprechen. Sie sehen, die Wörter im Terminal transkribiert, wie Sie sprechen. Drücken Sie die Schaltfläche "Mikrofon" ein zweites Mal, um die Spracherkennung zu beenden. Nehmen wir an "Terminal schließen", um das Terminal Lunarcom auszublenden. In der nächsten Lektion erfahren wir, wie dynamisch wechseln Sie zur Verwendung von Gerät-gestützte Spracherkennung für Situationen, in dem Azure Sprach-SDKS nicht aufgrund der HoloLens-2, die offline verfügbar ist.

[Nächste Lektion: Speech SDK Lektion 2](mrlearning-speechSDK-ch2.md)

