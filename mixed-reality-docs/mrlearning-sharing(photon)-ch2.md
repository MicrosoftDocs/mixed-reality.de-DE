**Vorbereitung von Unity für die Entwicklung** 

In dieser Lektion erfahren wir, wie zum Vorbereiten und Konfigurieren von Unity für die Entwicklung von Apps, wie z.B. das Mixed Reality-Toolkit importieren und Konfigurieren von Buildeinstellungen unsere Szene wird vorbereitet.

Ziele:

- Konfigurieren von Unity für app-Entwicklung

- Importieren des Mixed Reality-Toolkits

- Vorbereiten Sie Ihrer Projekt-Szene

### <a name="instructions"></a>Anweisungen

1. Herunterladen und speichern Sie die Mixed Reality-Toolkit Unity-Paket, indem Sie auf [hier.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC2.1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC2.1.unitypackage)
2. Klicken Sie in Unity auf das Menü "Ressourcen" auf Wählen Sie aus "Paket importieren", und klicken Sie auf "Benutzerdefinierte Package".

![Module3Chapter2step2im](images/module3chapter2step2im.PNG)

3. Wählen Sie das Unity-Paket, die, das Sie gerade heruntergeladen, über den Link in Schritt 1 bereitgestellt haben. Wenn das Popup-Fenster Importieren in Unity angezeigt wird, klicken Sie auf die Schaltfläche "Importieren", um Import zu starten. Importieren die MRTK kann mehrere Minuten dauern.

![Module3Chapter2step3im](images/module3chapter2step3im.PNG)

> Hinweis: Das heruntergeladene Paket werden im lokalen Ordner, in dem Sie die Datei gespeichert haben. In der Abbildung oben ist nicht darstellen, in dem Sie das Paket finden.

4. Erstellen Sie eine neue Szene (Dies kann erfolgen durch Klicken auf "File", und wählen "neue Szene"). Speichern Sie die Szene als "HLSharedProjectMain."

> Hinweis: wird möglicherweise ein Popupfenster angezeigt, die in der folgenden Abbildung ähneln. Jetzt klicken Sie einfach auf "No"
>
> ![Module3Chapter2note1im](images/module3chapter2note1im.PNG)

5. Klicken Sie unter "Mixed Reality-Toolkit" auf "Szene hinzufügen und konfigurieren."

![Module3Chapter2step5im](images/module3chapter2step5im.PNG)

6. Sobald dies abgeschlossen ist, wird eine neue Konfigurationsdatei angezeigt, bietet Ihnen die Möglichkeit, die das Profil anzupassen. Klicken Sie auf "kopieren und anpassen."

   ![Module3Chapter2step6ima](images/module3chapter2step6ima.PNG)

   ![Module3Chapter2step6imb](images/module3chapter2step6imb.PNG)

   ![Module3Chapter2step6imc](images/module3chapter2step6imc.PNG)

7. Scrollen Sie nach unten, und deaktivieren Sie die Option "Diagnostics-System aktivieren", wenn Sie das Diagnosefenster ausblenden möchten. Wir empfehlen die Diagnostics-Fenster, während der Entwicklung von Apps für die Leistungsüberwachung aktiviert, und sie während der Produktion oder Anwendung Demos zu deaktivieren. 

   ![Module3Chapter2step7ima](images/module3chapter2step7ima.PNG)

8. Öffnen Sie die Buildeinstellungen durch Drücken von STRG + UMSCHALT + B oder die Datei > Buildeinstellungen. Beachten Sie, dass das Programm derzeit unter der Plattform "PC, Mac und Linux-eigenständig" festgelegt ist. Legen Sie für die Entwicklung für HoloLens 2 die Plattform, die "universelle Windows-Plattform." Wählen Sie sie aus, und klicken Sie auf "switch Platform".![Module3Chapter2step8im](images/module3chapter2step8im.PNG)

9. Sobald der Vorgang abgeschlossen ist, klicken Sie auf das Kontrollkästchen "open Szenen hinzufügen". Kehren Sie jetzt den Inspektor-Zugriffsbereich und sicherstellen, dass das Kontrollkästchen rechts neben "virtual Reality unterstützt" (wie in der folgenden Abbildung gezeigt) aktiviert ist. Stellen Sie außerdem sicher, dass Sie das Kontrollkästchen neben "Szenen/HLSharedProjectMain" ebenfalls aktiviert ist, wie in der folgenden Abbildung dargestellt.![Module3Chapter2step9im](images/module3chapter2step9im.PNG)

10. Unter "Publishing Settings" im Abschnitt der Inspektor Bereich Scrollen Sie zu "Funktionen", und stellen Sie sicher, dass die folgenden Kontrollkästchen markiert sind:![Module3Chapter2step9imb](images/module3chapter2step9imb.PNG)

11. Importieren Sie das benutzerdefinierte Paket namens "SharingAssetCollection" heruntergeladen werden kann [hier.](https://github.com/microsoft/MixedRealityLearning/releases/download/Sharing_2/SharingAssetCollection.unitypackage) ![Module3Chapter2step12im](images/module3chapter2step11im.PNG)

12. Im Projektfenster, wechseln Sie nun zum Ordner "Prefabs", da in den nächsten Schritten Sie einige prefabs (Vorlagen) in der Szene implementieren werden. Klicken Sie im Ordner "Prefabs" klicken Sie, und ziehen Sie das Prefab, "DebugWindow" in der Hierarchie. Sobald Sie fertig sind, speichern Sie das Projekt (klicken Sie auf die Datei, klicken Sie dann speichern, oder drücken Sie STRG + S)

    ![Module3Chapter2step12im](images/module3chapter2step12im.PNG)

   > Hinweis: Sie werden feststellen, dass ein Popupfenster angezeigt, wenn Sie auf das Prefab klicken TMP Essentials gefragt. Klicken Sie auf "Import TMP Essentials", da sie benötigt werden. Wenn dieses Popupfenster angezeigt wird, müssen Sie möglicherweise das Prefab in Ihrer Hierarchie zu löschen, und ziehen es erneut in Ihrer Hierarchie aus, um mögliche Fehler in Bezug auf Text zu vermeiden.
   >
   > ![Module3Chapter2note2im](images/module3chapter2note2im.PNG)


## <a name="congratulations"></a>Herzlichen Glückwunsch!

Ihr Unity-Projekt ist jetzt für Photon bereit! In den nächsten Lektionen erstellen wir auf diese Szene und unsere Unity-Projekt für eine umfassende freigegebenen Umgebung.

[Nächste Lektion: Sharing(Photon) Lektion 3](mrlearning-sharing(photon)-ch3.md)

