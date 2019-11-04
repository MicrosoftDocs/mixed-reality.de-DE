---
title: Mr-Eingabe 210-Blick
description: Befolgen Sie diese exemplarische Vorgehensweise, indem Sie Unity, Visual Studio und hololens verwenden, um die Details von Blick Konzepten zu erlernen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, Tutorial, Blick
ms.openlocfilehash: 8608701a1dd0a9a20aede1737d16d5af2e715f6b
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434683"
---
>[!NOTE]
>Die Mixed Reality Academy-Lernprogramme wurden mit hololens (1. Gen) und gemischten rekursiven Gedanken Köpfen entworfen.  Daher ist es wichtig, dass Sie diese Tutorials für Entwickler, die nach wie vor eine Anleitung für die Entwicklung für diese Geräte suchen, behalten.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für hololens 2 verwendet werden.  Sie werden verwaltet, um weiterhin auf den unterstützten Geräten arbeiten zu können. Es wurde [eine neue Reihe von Tutorials](mrlearning-base.md) für hololens 2 gepostet.

# <a name="mr-input-210-gaze"></a>Mr-Eingabe 210: Blick

Der [Blick](gaze-and-commit.md) ist die erste Form der Eingabe und zeigt die Absicht und das Bewusstsein des Benutzers an. Die Eingabe 210 (auch Projekt-Explorer genannt) ist ein tiefer Einblick in die im Blick zusammenhängenden Konzepte für Windows Mixed Reality. Wir werden dem Cursor und holograms kontextbezogene Informationen hinzufügen und dabei die Vorteile der APP im Überblick über den Benutzer in vollem Umfang nutzen.

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

Wir haben hier einen freundlichen Astronauten, der Sie beim Erlernen von Blick Konzepten unterstützt. In den [Grundlagen 101](holograms-101.md)hatten wir einen einfachen Cursor, der genau auf Ihren Blick folgt. Heute verschieben wir einen Schritt über den einfachen Cursor hinaus:

* Wir machen den Cursor und den holograms im Blick: Beide Änderungen ändern sich je nachdem, wo der Benutzer sucht oder wo der Benutzer *nicht* sucht. Dies macht Sie Kontext abhängig.
* Wir werden dem Cursor und holograms Feedback hinzufügen, um dem Benutzer mehr Kontext für das Ziel zu geben. Dieses Feedback kann ein Audiomaterial und ein visuelles Element sein.
* Wir zeigen Ihnen gezielte Verfahren, mit denen Benutzer kleinere Ziele erreichen können.
* Wir zeigen Ihnen, wie Sie die Aufmerksamkeit des Benutzers auf die Hologramme mit einem direktionalen Indikator zeichnen.
* Wir informieren Sie über Techniken, mit denen Sie Ihre Hologramme mit dem Benutzer übernehmen, wenn Sie sich in ihrer Welt bewegen.

>[!IMPORTANT]
>Die in den folgenden Kapiteln eingebetteten Videos wurden mit einer älteren Version von Unity und dem Mixed Reality Toolkit aufgezeichnet. Die Schritt-für-Schritt-Anweisungen sind genau und aktuell, aber es werden möglicherweise Skripts und Visualisierungen in den entsprechenden Videos angezeigt, die veraltet sind. Die Videos bleiben in der einwelt enthalten und werden weiterhin angewendet.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Natürlich</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>Mr-Eingabe 210: Blick</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Bevor Sie beginnen

### <a name="prerequisites"></a>Voraussetzungen

* Ein Windows 10-PC, der mit den richtigen [installierten Tools](install-the-tools.md)konfiguriert ist.
* Einige Grund C# Legende Programmiermöglichkeiten.
* Sie sollten die [Grundlagen von 101](holograms-101.md)abgeschlossen haben.
* Ein hololens-Gerät, das [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode)ist.

### <a name="project-files"></a>Projektdateien

* Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) , die für das Projekt erforderlich sind. Erfordert Unity 2017,2 oder höher.
* Deinstallieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht zugänglichen Speicherort.

>[!NOTE]
>Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).

### <a name="errata-and-notes"></a>Errata und Notizen

* In Visual Studio muss "nur eigenen Code" unter Extras-> Optionen-> Debuggen deaktiviert (deaktiviert) werden, um Breakpoints im Code zu erreichen.

## <a name="chapter-1---unity-setup"></a>Kapitel 1: Einrichtung von Unity

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a>Ziele

* Optimieren von Unity für die HoloLens-Entwicklung
* Importieren von Assets und Einrichten der Szene
* Anzeigen des Astronauten in den hololens.

### <a name="instructions"></a>Anweisungen

1. Starten Sie Unity.
2. Wählen Sie **Neues Projekt**aus.
3. Nennen Sie das Projekt **Model Explorer**.
4. Geben Sie Location als **den Ordner** Folder ein, den Sie zuvor nicht archiviert haben.
5. Stellen Sie sicher, dass das Projekt auf **3D** festgelegt ist.
6. Klicken Sie auf **Projekt erstellen**.

### <a name="unity-settings-for-hololens"></a>Unity-Einstellungen für hololens

Wir müssen Unity mitteilen, dass die zu exportierende App eine [immersive Ansicht](app-views.md) anstelle einer 2D-Ansicht erstellen sollte. Dies geschieht, indem hololens als Virtual Reality-Gerät hinzugefügt wird.

1. Wechseln Sie zu **Edit > Project Settings > Player**.
2. Wählen Sie im **Inspektor-Panel** für die Player Einstellungen das **Windows Store** -Symbol aus.
3. Erweitern Sie die Gruppe " **XR-Einstellungen** ".
4. Aktivieren Sie im Abschnitt " **Rendering** " das Kontrollkästchen " **Virtual Reality supported** ", um eine neue **Virtual Reality-sdsliste** hinzuzufügen.
5. Vergewissern Sie sich, dass **Windows Mixed Reality** in der Liste angezeigt wird. Wenn dies nicht der Grund ist, wählen Sie die Schaltfläche **+** unten in der Liste aus, und wählen Sie **Windows Holographic**aus.

Als nächstes müssen wir unser Skript-Back-End auf .net festlegen.

1. Wechseln Sie zu **Edit > Project Settings > Player** (möglicherweise noch im vorherigen Schritt).
2. Wählen Sie im **Inspektor-Panel** für die Player Einstellungen das **Windows Store** -Symbol aus.
3. Stellen Sie sicher, dass im Konfigurations Abschnitt **andere Einstellungen** das Skript für die **Skript** Erstellung auf **.net** festgelegt ist.

Zum Schluss aktualisieren wir unsere Qualitätseinstellungen, um eine schnelle Leistung in hololens zu erzielen.

1. Wechseln Sie zu **Edit > Project Settings > Quality**.
2. Klicken Sie in der **Standard** Zeile unter dem Windows Store-Symbol auf den Pfeil nach unten.
3. Wählen Sie für **Windows Store-Apps** **sehr niedrig** aus.

### <a name="import-project-assets"></a>Projekt Objekte importieren

1. Klicken Sie im **Projekt** Panel mit der rechten Maustaste auf den Ordner **Assets** .
2. Klicken Sie auf **Paket importieren > benutzerdefiniertes Paket**.
3. Navigieren Sie zu den Projektdateien, die Sie heruntergeladen haben, und klicken Sie auf **modelexplorer. unitypackage**.
4. Klicken Sie auf **Öffnen**.
5. Nachdem das Paket geladen wurde, klicken Sie auf die Schaltfläche **importieren** .

### <a name="setup-the-scene"></a>Einrichten der Szene

1. Löschen Sie die **Hauptkamera**in der-Hierarchie.
2. Öffnen Sie im Ordner **holotoolkit** den **Eingabe** Ordner, und öffnen Sie dann den Ordner **Prefabs** .
3. Ziehen Sie die vorfab **mixedrealitycameraparent** aus dem Ordner **Prefabs** in die **Hierarchie**.
4. Klicken Sie mit der rechten Maustaste auf den **direktionalen Licht** in der Hierarchie, **und wählen**
5. Ziehen Sie im **holograms** -Ordner die folgenden Objekte per Drag & amp; Drop in den Stamm der **Hierarchie**:
    * **Astroman**
    * **Such**
    * **Spaceaudiosource**
    * **Spacebackground**
6. Starten Sie den **Wiedergabemodus** ▶, um den Astronaut anzuzeigen.
7. Klicken Sie erneut auf **Wiedergabemodus** ▶, um zu **verhindern**.
8. Suchen Sie im Ordner **holograms** das **fitbox** -Asset, und ziehen Sie es in den Stamm der **Hierarchie**.
9. Wählen Sie im Bereich **Hierarchie** die Option **fitbox** aus.
10. Ziehen Sie die **Astroman** -Auflistung aus der **Hierarchie** in die **Hologram** -Auflistungs Eigenschaft von "fitbox" im **Inspektor** -Panel.

### <a name="save-the-project"></a>Speichern Sie das Projekt.

1. Speichern Sie die neue Szene: **File > Szene speichern**unter.
2. Klicken Sie auf **neuer Ordner** , und benennen Sie die Ordner **Szenen**.
3. Benennen Sie die Datei "**Model Explorer**", und speichern Sie Sie im Ordner **Szenen** .

### <a name="build-the-project"></a>Erstellen des Projekts

1. Wählen Sie in Unity **Datei > Buildeinstellungen**aus.
2. Klicken Sie auf **offene Szenen hinzufügen** , um die Szene hinzuzufügen.
3. Wählen Sie in der Liste **Plattform** **universelle Windows-Plattform** aus, und klicken Sie auf **Plattform wechseln**.
4. Wenn Sie speziell für hololens entwickeln, legen Sie **Zielgerät** auf **hololens**fest. Andernfalls sollten Sie es auf **jedem Gerät**belassen.
5. Stellen Sie sicher, dass der **Buildtyp** auf **D3D** und das **SDK** auf **Latest installiert** festgelegt ist (was SDK 16299 oder höher sein sollte).
6. Klicken Sie auf **Erstellen**.
7. Erstellen Sie einen **neuen Ordner** mit dem Namen "App".
8. Klicken Sie einfach auf den **App** -Ordner.
9. Drücken **Sie Ordner auswählen**.

Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.

1. Öffnen Sie den **App** -Ordner.
2. Öffnen Sie die Visual Studio-Projekt Mappe **Model Explorer**.

Bei der Bereitstellung in hololens:

1. Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x86**.
2. Klicken Sie auf den Dropdown Pfeil neben der Schaltfläche lokaler Computer, und wählen Sie **Remote Computer**aus.
3. Geben Sie **die IP-Adresse des hololens-Geräts** ein, und legen Sie den Authentifizierungsmodus auf **Universal (unverschlüsseltes Protokoll)** Klicken Sie auf **Auswählen**. Wenn Sie die IP-Adresse Ihres Geräts nicht kennen, suchen Sie unter **Einstellungen > Netzwerk & Internet > Erweiterte Optionen**.
4. Klicken Sie in der oberen Menüleiste auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**. Wenn Sie die Bereitstellung auf Ihrem Gerät zum ersten Mal durchführt, müssen Sie [es mit Visual Studio](using-visual-studio.md#pairing-your-device)koppeln.
5. Wenn die APP bereitgestellt wurde, schließen Sie das **fitbox** -Gerät mit einer **Auswahl Bewegung**ab.

Bei der Bereitstellung auf einem immersiven Headset:

1. Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x64**.
2. Stellen Sie sicher, dass das Bereitstellungs Ziel auf **lokaler Computer**festgelegt ist.
3. Klicken Sie in der oberen Menüleiste auf **Debuggen-> Starten ohne Debugging** , oder drücken Sie **STRG + F5**.
4. Wenn die APP bereitgestellt wurde, schließen Sie die Funktion **, indem Sie den-** Typ auf einen Bewegungs Controller ziehen.

## <a name="chapter-2---cursor-and-target-feedback"></a>Kapitel 2: Cursor-und Ziel Feedback

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a>Ziele

* Visueller Entwurf und Verhalten des Cursors.
* Zeiger basiertes Cursor Feedback.
* Auf Blick basierendes – Hologramm-Feedback.

Wir werden unsere Arbeit auf einige Grundsätze von Cursor Entwürfen basieren, nämlich:

* Der Cursor ist immer vorhanden.
* Lassen Sie den Cursor nicht zu klein oder groß werden.
* Vermeiden Sie das Blockieren von Inhalt.

### <a name="instructions"></a>Anweisungen

1. Suchen Sie im Ordner **holotoolkit\input\prefabs** nach dem **InputManager** -Objekt.
2. Ziehen Sie den **InputManager** in die **Hierarchie**.
3. Suchen Sie im Ordner **holotoolkit\input\prefabs** nach dem **Cursor** Medienobjekt.
4. Ziehen Sie den **Cursor** per Drag & Drop in die **Hierarchie**.
5. Wählen Sie das **InputManager** -Objekt in der **Hierarchie**aus.
6. Ziehen Sie das **Cursor** Objekt aus der **Hierarchie** in das **Cursor** Feld " **simplesinglepointerselector**" von InputManager am unteren Rand des **Inspektors**.

![Einfache Einrichtung von einzelzeigerselektor](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a>Erstellen und bereitstellen

1. Erstellen Sie die APP aus dem **Datei > den Buildeinstellungen**neu.
2. Öffnen Sie den **app-Ordner**.
3. Öffnen Sie die Visual Studio-Projekt Mappe **Model Explorer**.
4. Klicken Sie auf **Debuggen > Starten ohne Debugging** , oder drücken Sie **STRG + F5**.
5. Beobachten Sie, wie der Cursor gezeichnet wird, und wie sich die Darstellung ändert, wenn Sie ein Hologram berührt.

### <a name="instructions"></a>Anweisungen

1. Erweitern Sie im Bereich **Hierarchie** das Objekt **Astroman**->**GEO_G**->**Back_Center** .
2. Doppelklicken Sie auf **Interactible.cs** , um es in Visual Studio zu öffnen.
3. Heben Sie die Auskommentierung der Zeilen in den Rückrufe **ifocverwendbare. onfocusenter ()** und **ifocverwendbare. onfocusexit ()** in **Interactible.cs**auf. Diese werden vom InputManager des Mixed Reality-Toolkits aufgerufen, wenn der Fokus (entweder durch den Blick oder durch den Controller) in den Konflikt des jeweiligen gameobject-Objekts wechselt und diesen verlässt.

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
>Wir verwenden `EnableKeyword` und `DisableKeyword` weiter oben. Um diese in ihrer eigenen App mit dem Standard-Shader des Toolkits zu nutzen, müssen Sie die [Unity-Richtlinien für den Zugriff auf Materialien per Skript](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html)befolgen. In diesem Fall haben wir bereits die [drei Varianten von hervorgehobenem Material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) in den Ressourcen Ordner eingefügt (suchen Sie nach den drei Materialien, deren Name hervorgehoben ist).

### <a name="build-and-deploy"></a>Erstellen und bereitstellen

1. Erstellen Sie wie zuvor das Projekt, und stellen Sie es auf den hololens bereit.
2. Beobachten Sie, was geschieht, wenn der Blick auf ein Objekt gerichtet ist, und wenn es nicht.

## <a name="chapter-3---targeting-techniques"></a>Kapitel 3: Ziel Technologien

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a>Ziele

* Vereinfachen Sie das Ziel von holograms.
* Stabilisiert natürliche Head-Bewegungen.

### <a name="instructions"></a>Anweisungen

1. Wählen Sie im Bereich **Hierarchie** das Objekt **InputManager** aus.
2. Suchen Sie im **Inspektor** -Panel nach dem Skript für den **Blick-Stabilisator** . Klicken Sie auf die Datei, um Sie in Visual Studio zu öffnen, wenn Sie ein Bild sehen möchten.
    * Dieses Skript durchläuft Beispiele von raycast-Daten und trägt dazu bei, den Blick des Benutzers auf die Genauigkeit der Genauigkeit zu stabilisieren.
3. Im **Inspektor**können Sie den Wert für **gespeicherte Stabilitäts Beispiele** bearbeiten. Dieser Wert stellt die Anzahl der Samplings dar, die der-Stabilisator durchläuft, um den stabilisierten Wert zu berechnen.

## <a name="chapter-4---directional-indicator"></a>Kapitel 4: direktionaler Indikator

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a>Ziele

* Fügen Sie einen direktionalen Indikator für den Cursor hinzu, um Hologramme zu finden.

### <a name="instructions"></a>Anweisungen

Wir verwenden die Datei **DirectionIndicator.cs** , um Folgendes zu tun:

1. Zeigen Sie den direktionalen Indikator an, wenn der Benutzer nicht mit den holograms-Vorgängen.
2. Blenden Sie den direktionalen Indikator aus, wenn der Benutzer bei den holograms einen Blick anzeigt.
3. Aktualisieren Sie den direktionalen Indikator, sodass er auf die holograms zeigt.

Los geht's.

1. Klicken Sie im **Hierarchie** Panel auf das **Astroman** -Objekt, und klicken Sie auf **den Pfeil** , um es zu erweitern.
2. Wählen Sie im Bereich **Hierarchie** das **directionalindicator** -Objekt unter **Astroman**aus.
3. Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .
4. Geben Sie im Menü den Suchfeld- **Richtungsindikator**ein. Wählen Sie das Suchergebnis aus.
5. Ziehen Sie im Bereich **Hierarchie** das **Cursor** Objekt per Drag & Drop auf die **Cursor** -Eigenschaft des **Inspektors**.
6. Ziehen Sie im **Projekt** Panel im Ordner **holograms** das **directionalindicator** -Asset per Drag & Drop auf die **direktionale Indikator** Eigenschaft im **Inspektor**.
7. Erstellen und Bereitstellen der app.
8. Sehen Sie, wie das direktionale Indikator Objekt Ihnen hilft, den Astronaut zu finden.

## <a name="chapter-5---billboarding"></a>Kapitel 5: Abrechnung

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a>Ziele

* Verwenden Sie das-Abrechnungs Board, um holograms immer für Sie zu verwenden.

Wir verwenden die Datei **Billboard.cs** , um ein gameobject-Objekt so zu speichern, dass es dem Benutzer jederzeit zusteht.

1. Wählen Sie im Bereich **Hierarchie** das Objekt **Astroman** aus.
2. Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .
3. Geben Sie im Menü im Suchfeld den Suchbegriff **ein.** Wählen Sie das Suchergebnis aus.
4. Legen Sie im **Inspektor** die **pivotachse** auf **Y**fest.
5. Probieren Sie es aus! Erstellen und stellen Sie die APP wie zuvor bereit.
6. Sehen Sie sich an, wie das Billboard-Objekt Ihnen unabhängig von der Änderung des Standpunkts steht.
7. Löschen Sie das Skript für den Moment aus dem **Astroman** .

## <a name="chapter-6---tag-along"></a>Kapitel 6: tagparallel

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a>Ziele

* Verwenden Sie Tag-Along, damit unsere Hologramme um den Raum herum stehen.

Wir arbeiten an diesem Problem, indem wir die folgenden Entwurfs Einschränkungen beachten:

* Der Inhalt sollte immer auf einen Blick entfernt werden.
* Der Inhalt sollte nicht auf dem Wege stehen.
* Der Inhalt der Kopf Sperre ist unbequem.

Die hier verwendete Lösung ist die Verwendung eines "tagbasierten" Ansatzes.

Ein tagansichts Objekt verlässt die Ansicht des Benutzers niemals vollständig. Sie können sich ein Tag als ein Objekt vorstellen, das an den Kopf des Benutzers durch Gummibänder angehängt ist. Wenn der Benutzer sich bewegt, bleibt der Inhalt in einem einfachen Blick, indem er an den Rand der Ansicht bewegt wird, ohne dass er vollständig verlässt. Wenn der Benutzer in Richtung des tagbasierten Objekts zeigt, wird es vollständig in die Ansicht integriert.

Wir verwenden die Datei **SimpleTagalong.cs** , um Folgendes zu tun:

1. Bestimmt, ob sich das Tag-entlang-Objekt innerhalb der Kamera Begrenzungen befindet.
2. Wenn nicht in der Ansicht "Frustum" angezeigt wird, positionieren Sie das Tag-entlang auf teilweise innerhalb der Ansicht "Frustum".
3. Positionieren Sie andernfalls das Tag-parallel zu einem Standardabstand vom Benutzer.

Zu diesem Zweck müssen wir zuerst das **Interactible.cs** -Skript ändern, um die **Tagalong-Aktion**aufzurufen.

1. Bearbeiten Sie **Interactible.cs** , indem Sie die Codierungs Übung 6. a abschließen (auskommentieren von Zeilen 84 bis 87).

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

Das **InteractibleAction.cs** -Skript in Kombination mit **Interactible.cs** führt benutzerdefinierte Aktionen aus, wenn Sie auf holograms tippen. In diesem Fall verwenden wir eine speziell für das Tag.

* Klicken Sie im Ordner **Scripts** auf **TagalongAction.cs** Asset, um es in Visual Studio zu öffnen.
* Führen Sie die Codierungs Übung aus, oder ändern Sie Sie in Folgendes:
  * Geben Sie oben in der **Hierarchie**in der Suchleiste **ChestButton_Center** ein, und wählen Sie das Ergebnis aus.
  * Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .
  * Geben Sie im Menü in das Suchfeld **Tagalong Action**ein. Wählen Sie das Suchergebnis aus.
  * Suchen Sie im Ordner **holograms** das **Tagalong** Asset.
  * Wählen Sie das **ChestButton_Center** -Objekt in der **Hierarchie**aus. Ziehen Sie das **Tagalong** -Objekt per Drag & amp; Drop aus dem **Projekt** Panel auf den **Inspektor** in die Eigenschaft **Objekt zu tagparallel** .
  * Ziehen Sie das **Tagalong-Aktions** Objekt aus dem **Inspektor** in das **interable-Aktions** Feld des **interfähigen** Skripts.
* Doppelklicken Sie auf das Skript **tagalongaction** , um es in Visual Studio zu öffnen.

![Interacable-Einrichtung](images/holograms210-interactible.png)

Wir müssen Folgendes hinzufügen:

* Fügen Sie der Funktion "PerformAction" im tagalongaction-Skript (geerbt von interactibleaction) Funktionalität hinzu.
* Fügen Sie dem Objekt "gazed-on" einen fakboardingvorgang hinzu, und legen Sie die pivotachse auf XY fest
* Fügen Sie dann dem-Objekt eine einfache tagverbindung hinzu.

Hier ist unsere Lösung, von **TagalongAction.cs**:

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* Probieren Sie es aus! Erstellen und Bereitstellen der app.
* Sehen Sie sich an, wie der Inhalt der Mitte des Blick Punkts folgt, aber nicht kontinuierlich und ohne Blockierung.
