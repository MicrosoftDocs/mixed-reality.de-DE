---
title: MR Eingabe 210 - Blicke
description: Führen Sie diese exemplarischen Vorgehensweise erfahren, die Details der Blicke Konzepte auf Unity, Visual Studio und HoloLens mit Codierung.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Holotoolkit, Mixedrealitytoolkit, Mixedrealitytoolkit-Unity Academy, Tutorial, Blicke
ms.openlocfilehash: 076314389ec5ed70347c26d50c6a993f55da0758
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993546"
---
>[!NOTE]
>In den Tutorials Mixed Reality Academy mit HoloLens entwickelt wurden (der 1. Generation) und Mixed Reality Immersive Headsets Bedenken.  Daher können wir, dass es ist wichtig, die in diesen Tutorials für Entwickler beizubehalten, die Informationen bei der Entwicklung für diese Geräte benötigen werden.  In diesen Tutorials werden **_nicht_** aktualisiert werden, mit der neuesten Toolsets oder Interaktionen für HoloLens 2 verwendet wird.  Sie werden zum Fortsetzen der Arbeit auf die unterstützten Geräte verwaltet werden. Es wird eine neue Reihe von Tutorials, die in der Zukunft ausgegeben wird, die Entwicklung für HoloLens 2 veranschaulichen vorhanden sein.  Dieser Hinweis wird mit einem Link zu dieser Tutorials aktualisiert werden, wenn sie bereitgestellt werden.

# <a name="mr-input-210-gaze"></a>MR Eingabe 210: Blickeingabe

[Bestaunen](gaze.md) ist die erste Form der Eingabe und zeigt die Absicht und Informationen des Benutzers. MR Eingabe 210 (auch bekannt als Projekt-Explorer) ist eine ausführliche Betrachtung Blicke bezogene Konzepte für die Windows Mixed Reality. Wir werden hinzufügen kontextbezogene Informationen zu den Cursor und Hologramme, voll ausschöpfen was Ihre app des Benutzers Blicke bekannt sind.

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

Wir haben eine benutzerfreundliche Astronautenausweis Hier können Sie die Blicke Konzepten vertraut zu machen. In [MR Grundlagen 101](holograms-101.md), einen einfachen Cursor, der gerade Ihre Blicke gefolgt werden musste. Heute haben wir einen Schritt weiter als die einfachen Cursor verschieben:

* Machen wir den Cursor und unsere Hologramme Blicke unterstützenden: beide ändern sich basierend auf, in denen der Benutzer sieht – oder, in denen der Benutzer ist *nicht* suchen. Dadurch werden sie Kontext berücksichtigen.
* Fügen wir Feedback zu unseren Cursor und Hologramme, Benutzern mehr Kontext auf was vorgesehen ist. Dieses Feedback kann es sich um Audio- und visuellen sein.
* Wir zeigen Ihnen die Zielgruppenadressierung anhand bestimmter Techniken, um die Benutzer, die kleinere Ziele erreichen können.
* Wir zeigen Ihnen die Aufmerksamkeit des Benutzers zu Ihrer Hologramme mit einem richtungsindikator zeichnen.
* Wir werden Sie die Portalwebsite Verfahren, um Ihre Hologramme mit dem Benutzer zu nutzen, wie sie in Ihrer Welt verschiebt.

>[!IMPORTANT]
>Die Videos in jeder der folgenden Kapitel eingebettet wurden mit einer älteren Version von Unity und dem Mixed Reality-Toolkit aufgezeichnet. Während die schrittweisen Anweisungen korrekt und aktuell sind, Sie möglicherweise Skripts und Visualisierungen in die entsprechenden Videos, die veraltet sind. Die Videos aus Gründen der Posterity bleiben, und es aber trotzdem anwenden, da die Konzepte behandelt.

## <a name="device-support"></a>Unterstützung von Geräten

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Immersive headsets</a></th>
</tr><tr>
<td>MR Eingabe 210: Blickeingabe</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Bevor Sie beginnen

### <a name="prerequisites"></a>Vorraussetzungen

* Ein Windows 10-PCs mit dem richtigen konfiguriert [-Tools installiert](install-the-tools.md).
* Einige grundlegende C# Programmierkenntnisse.
* Sie sollten abgeschlossen haben [MR Grundlagen 101](holograms-101.md).
* Ein Gerät HoloLens [für die Entwicklung konfiguriert](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Projektdateien

* Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) vom Projekt erforderlich sind. Ist Unity 2017.2 oder höher erforderlich.
* Un-Archive die Dateien auf dem Desktop oder andere einfach auf den Speicherort zugreifen.

>[!NOTE]
>Wenn Sie vor dem Herunterladen, den Quellcode ansehen möchten es [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).

### <a name="errata-and-notes"></a>Fehler und Anmerkungen zu dieser Version

* "Nur eigenen Code" in Visual Studio muss sein Disabled (deaktiviert) unter Extras -> Optionen -> Debugging um Haltepunkte in Ihrem Code.

## <a name="chapter-1---unity-setup"></a>Kapitel 1: Unity-Setup

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a>Ziele

* Optimieren von Unity für die Entwicklung für HoloLens.
* Importieren von Objekten aus, und richten Sie die Szene.
* Zeigen Sie die Astronautenausweis, in die HoloLens.

### <a name="instructions"></a>Anweisungen

1. Starten Sie Unity.
2. Wählen Sie **neues Projekt**.
3. Nennen Sie das Projekt **ModelExplorer**.
4. Geben Sie den Speicherort als dem **bestaunen** Ordner Sie zuvor nicht archiviert.
5. Stellen Sie sicher, dass das Projekt nastaven NA hodnotu **3D**.
6. Klicken Sie auf **erstellen Projekt**.

### <a name="unity-settings-for-hololens"></a>Unity-Einstellungen für HoloLens

Wir müssen wissen, dass die app aus, es versucht wird, exportieren, zu erstellen, sollten Unity eine [immersive Ansicht](app-views.md) anstelle einer 2D-Ansicht. Zu diesem Zweck HoloLens als virtuelle Realität Gerät hinzufügen.

1. Wechseln Sie zu **Bearbeiten > Projekteinstellungen > Player**.
2. In der **Inspektor Bereich** Playereinstellungen, wählen Sie die **Windows Store** Symbol.
3. Erweitern Sie die **XR-Einstellungen** Gruppe.
4. In der **Rendern** aktivieren Sie im Abschnitt der **virtuelle Realität unterstützt** Kontrollkästchen zum Hinzufügen einer neuen **virtuelle Realität SDKs** Liste.
5. Überprüfen Sie, ob **Windows Mixed Reality** in der Liste angezeigt. Wenn nicht der Fall, wählen Sie die **+** Schaltfläche am unteren Rand der Liste aus, und wählen Sie **Windows Holographic**.

Als Nächstes müssen wir das Skript Back-End zu .NET festlegen.

1. Wechseln Sie zu **Bearbeiten > Projekteinstellungen > Player** (Sie können weiterhin haben dies aus dem vorherigen Schritt).
2. In der **Inspektor Bereich** Playereinstellungen, wählen Sie die **Windows Store** Symbol.
3. In der **Weitere Einstellungen** Konfiguration im Abschnitt, stellen Sie sicher, dass **Scripting Back-End-** nastaven NA hodnotu **.NET**

Zum Schluss aktualisieren wir unsere Qualität-Einstellungen, um eine hohe verarbeitungsleistung zu HoloLens zu erreichen.

1. Wechseln Sie zu **Bearbeiten > Projekteinstellungen > Qualität**.
2. Klicken Sie auf den nach unten zeigenden Pfeil in der **Standard** Zeile unter dem Windows Store-Symbol.
3. Wählen Sie **sehr niedrigen** für **Windows Store-Apps**.

### <a name="import-project-assets"></a>Importieren von Projektressourcen

1. Klicken Sie mit der rechten Maustaste auf die **Assets** Ordner in der **Projekt** Bereich.
2. Klicken Sie auf **Paket importieren > benutzerdefiniertes Paket**.
3. Navigieren Sie zu den Projektdateien, die Sie heruntergeladen haben, und klicken Sie auf **ModelExplorer.unitypackage**.
4. Klicken Sie auf **Öffnen**.
5. Nachdem das Paket geladen wird, klicken Sie auf die **Import** Schaltfläche.

### <a name="setup-the-scene"></a>Einrichten der Szene

1. Löschen Sie in der Hierarchie der **Main Camera**.
2. In der **HoloToolkit** Ordner die **Eingabe** Ordner öffnen Sie dann die **Prefabs** Ordner.
3. Drag & drop die **MixedRealityCameraParent** prefab aus der **Prefabs** Ordner in der **Hierarchie**.
4. Mit der rechten Maustaste die **gerichtetes Licht** in der Hierarchie, und wählen Sie **löschen**.
5. In der **Hologramme** Ordner Drag & drop die folgenden Ressourcen in das Stammverzeichnis der **Hierarchie**:
    * **AstroMan**
    * **Lights**
    * **SpaceAudioSource**
    * **SpaceBackground**
6. Starten Sie **spielen Modus** ▶ der Astronautenausweis anzeigen.
7. Klicken Sie auf **spielen Modus** ▶ erneut aus, um **beenden**.
8. In der **Hologramme** Ordner finden Sie die **Fitbox** Asset und ziehen Sie es in das Stammverzeichnis des der **Hierarchie**.
9. Wählen Sie die **Fitbox** in die **Hierarchie** Bereich.
10. Ziehen Sie die **AstroMan** Auflistung von der **Hierarchie** zu der **– Hologramm Auflistung** Eigenschaft der Fitbox in der **Inspector** Bereich.

### <a name="save-the-project"></a>Speichern Sie das Projekt

1. Speichern Sie die neue Szene: **Datei > Szene speichern unter**.
2. Klicken Sie auf **neuer Ordner** und nennen Sie den Ordner **Szenen**.
3. Nennen Sie die Datei "**ModelExplorer**", und speichern Sie ihn in das **Szenen** Ordner.

### <a name="build-the-project"></a>Erstellen Sie das Projekt

1. Wählen Sie in Unity **Datei > Buildeinstellungen**.
2. Klicken Sie auf **öffnen Szenen hinzufügen** die Szene hinzufügen.
3. Wählen Sie **universelle Windows-Plattform** in die **Plattform** aus, und klicken Sie auf **Plattform wechseln**.
4. Wenn Sie speziell für HoloLens entwickeln, legen Sie **Zielgerät** zu **HoloLens**. Andernfalls lassen Sie es auf **jedes Gerät**.
5. Stellen Sie sicher **Build Type** nastaven NA hodnotu **D3D** und **SDK** nastaven NA hodnotu **zuletzt installierte** (die sollte SDK 16299 oder höher sein).
6. Klicken Sie auf **Erstellen**.
7. Erstellen Sie eine **neuer Ordner** mit dem Namen "App".
8. Mausklick die **App** Ordner.
9. Drücken Sie **wählen Sie Ordner**.

Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.

1. Öffnen der **App** Ordner.
2. Öffnen der **ModelExplorer Visual Studio-Projektmappe**.

Wenn für HoloLens bereitstellen zu können:

1. Verwenden obere auf der Symbolleiste in Visual Studio, ändern Sie das Ziel vom Debugmodus in den **Version** und ARM, **X86**.
2. Klicken Sie auf den Dropdownpfeil neben der Schaltfläche mit den lokalen Computer, und wählen **Remotecomputer**.
3. Geben Sie **die HoloLens-Geräte-IP-Adresse** und legen Sie den Authentifizierungsmodus auf **universell (unverschlüsseltes Protokoll)**. Klicken Sie auf **Auswählen**. Wenn Sie Ihre IP-Adresse des Geräts nicht kennen, suchen Sie im **Einstellungen > Netzwerk und Internet > Erweiterte Optionen**.
4. Klicken Sie in der Menüleiste im oberen Bereich auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**. Ist dies beim ersten auf Ihrem Gerät bereitstellen, Sie müssen [verbinden Sie es mit Visual Studio](using-visual-studio.md#pairing-your-device-hololens).
5. Wenn die app bereitgestellt wurde, schließen die **Fitbox** mit eine **wählen Sie die Bewegung**.

Wenn eine immersive Kopfhörer bereitstellen:

1. Verwenden obere auf der Symbolleiste in Visual Studio, ändern Sie das Ziel vom Debugmodus in den **Version** und ARM, **X64**.
2. Stellen Sie sicher, dass das Bereitstellungsziel nastaven NA hodnotu **lokalen Computer**.
3. Klicken Sie in der Menüleiste im oberen Bereich auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**.
4. Wenn die app bereitgestellt wurde, schließen die **Fitbox** den Trigger ein Controller während der Übertragung zu ziehen.

## <a name="chapter-2---cursor-and-target-feedback"></a>Kapitel 2 – Cursor und Ziel-Feedback

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a>Ziele

* Cursor visueller Entwurf und das Verhalten.
* Cursor Blicke basierende Feedback.
* Blicke basierende – Hologramm Feedback.

Wir werden unsere Arbeit einige Entwurfsprinzipien, Cursor, d. h. als Grundlage für:

* Der Cursor ist immer vorhanden.
* Lassen Sie nicht den Cursor zu klein oder groß zu erhalten.
* Vermeiden Sie die Inhalte sitzt.

### <a name="instructions"></a>Anweisungen

1. In der **HoloToolkit\Input\Prefabs** Ordner finden Sie die **InputManager** Asset.
2. Drag & drop die **InputManager** auf die **Hierarchie**.
3. In der **HoloToolkit\Input\Prefabs** Ordner finden Sie die **Cursor** Asset.
4. Drag & drop die **Cursor** auf die **Hierarchie**.
5. Wählen Sie die **InputManager** -Objekt in der **Hierarchie**.
6. Ziehen Sie die **Cursor** -Objekt aus der **Hierarchie** in die InputManager des **SimpleSinglePointerSelector**des **Cursor** Feld auf der Ende der **Inspektor**.

![Einfache Einrichtung für einfache Zeiger-Auswahl](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a>Erstellen und bereitstellen

1. Erstellen Sie die app neu **Datei > Buildeinstellungen**.
2. Öffnen der **App-Ordner**.
3. Öffnen der **ModelExplorer Visual Studio-Projektmappe**.
4. Klicken Sie auf **Debuggen -> Starten ohne debugging** , oder drücken Sie **STRG + F5**.
5. Beachten Sie, wie der Cursor gezeichnet wird und wie es die Darstellung sich ändert, wenn er ggf. ein Hologramm berührt wird.

### <a name="instructions"></a>Anweisungen

1. In der **Hierarchie** erweitern Sie die **AstroMan**->**GEO_G**->**Back_Center** Objekt.
2. Klicken Sie mit der Doppelklicken auf **Interactible.cs** um es in Visual Studio zu öffnen.
3. Auskommentierung der Zeilen in der **IFocusable.OnFocusEnter()** und **IFocusable.OnFocusExit()** Rückrufe in **Interactible.cs**. Diese werden durch das Mixed Reality-Toolkit InputManager bezeichnet, liegt der Fokus (entweder durch Blicke oder Controller zeigen) eingibt und das spezifische "gameobject" "collider" beendet.

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
>Wir verwenden `EnableKeyword` und `DisableKeyword` oben. Um machen diese in Ihre eigene app mit Standard-Shader des Toolkits verwenden, müssen Sie folgen den [Unity-Richtlinien für den Zugriff auf Materialien über ein Skript](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html). In diesem Fall haben wir bereits enthalten die [drei Varianten von hervorgehobenen Material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) in den Ordner "Resources" (Suchen Sie nach den drei Materialien mit Hervorhebung im Namen) erforderlich sind.

### <a name="build-and-deploy"></a>Erstellen und bereitstellen

1. Wie zuvor, erstellen Sie das Projekt aus, und stellen in die HoloLens.
2. Beachten Sie, was geschieht, wenn ein Objekt die Blicke gedacht ist und wenn es nicht ist.

## <a name="chapter-3---targeting-techniques"></a>Kapitel 3 – Methoden für

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a>Ziele

* Erleichtern Sie es, Ziel-Hologramme.
* Stabilisieren Sie natürliche Head Verschiebungen.

### <a name="instructions"></a>Anweisungen

1. In der **Hierarchie** wählen die **InputManager** Objekt.
2. In der **Inspektor** Bereich, suchen Sie nach der **bestaunen Stabilisierung** Skript. Klicken Sie in Visual Studio, öffnen sie das, wenn Sie sich ansehen möchten.
    * Dieses Skript führt eine Iteration durch Beispiele von Raycast Daten und hilft dabei, Blicke des Benutzers, für die Ziel-Genauigkeit zu stabilisieren.
3. In der **Inspektor**, können Sie bearbeiten die **gespeicherten Stabilität Beispiele** Wert. Dieser Wert stellt die Anzahl der Samplings, denen an der Stabilisierung durchläuft den stabilisierten Wert zu berechnen.

## <a name="chapter-4---directional-indicator"></a>Kapitel 4 – richtungsindikator

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a>Ziele

* Hinzufügen einer richtungsindikator für den Cursor, um Hologramme zu finden.

### <a name="instructions"></a>Anweisungen

Wir verwenden wollen die **DirectionIndicator.cs** Datei die:

1. Zeigen Sie die richtungsindikator aus, wenn der Benutzer nicht auf die Hologramme gazing ist.
2. Blenden Sie die richtungsindikator aus, wenn der Benutzer auf die Hologramme gazing ist.
3. Aktualisieren Sie die richtungsindikator, um auf die Hologramme zu verweisen.

Los geht's.

1. Klicken Sie auf die **AstroMan** -Objekt in der **Hierarchie** Bereich und **klicken Sie auf den Pfeil** um ihn zu erweitern.
2. In der **Hierarchie** wählen die **DirectionalIndicator** Objekt unter **AstroMan**.
3. In der **Inspektor** Bereich, klicken Sie auf die **Add Component** Schaltfläche.
4. Geben Sie im Menü, in das Suchfeld **Indikator für die Verweisrichtung**. Wählen Sie das Suchergebnis.
5. In der **Hierarchie** Bereich drag und drop der **Cursor** -Objekt auf die **Cursor** -Eigenschaft in der **Inspektor**.
6. In der **Projekt** im Bereich der **Hologramme** Ordner Drag & Drop die **DirectionalIndicator** Medienobjekt, auf die **Richtungsindikator**-Eigenschaft in der **Inspektor**.
7. Erstellen und Bereitstellen der app.
8. Sehen Sie sich, wie das richtungsindikator-Objekt die Astronautenausweis finden kann.

## <a name="chapter-5---billboarding"></a>Kapitel 5 – Billboarding

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a>Ziele

* Mit der billboarding Hologramme immer zu Ihnen hin auftreten müssen.

Wir verwenden die **Billboard.cs** Datei zu einem "gameobject" ausgerichtet, dass es immer den Benutzer zeigt.

1. In der **Hierarchie** wählen die **AstroMan** Objekt.
2. In der **Inspektor** Bereich, klicken Sie auf die **Add Component** Schaltfläche.
3. Geben Sie im Menü, in das Suchfeld **Billboard**. Wählen Sie das Suchergebnis.
4. In der **Inspektor** legen Sie die **Pivot Achse** zu **Y**.
5. Probieren Sie es aus! Erstellen und Bereitstellen der app als vor.
6. Sehen Sie, wie Gesichter Sie stattdessen das Billboard unabhängig davon, wie Sie den Standpunkt ändern.
7. Löschen Sie das Skript aus dem **AstroMan** jetzt.

## <a name="chapter-6---tag-along"></a>Kapitel 6 – Tag-Along

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a>Ziele

* Verwenden Sie Tag-Along, um unsere Hologramme uns im Raum Folgen haben.

Wie wir zu diesem Problem arbeiten, müssen wir durch die folgenden Einschränkungen beim Entwurf geführt:

* Der Inhalt muss immer sofort ein Blick entsprechen.
* Inhalt darf nicht auf die Weise sein.
* Head-Sperren Inhalt ist unangenehm.

Die hier verwendete Lösung ist die Verwendung ein Ansatzes "Tag-along".

Ein Objekt Tag-along verlässt nie vollständig die Ansicht des Benutzers. Stellen Sie sich die einer Tag-along als ein Objekt des Benutzers Head von weiche Ränder hinzugefügt. Wenn der Benutzer bewegt, bleibt der Inhalt in einen Blick einfach, indem er auf den Rand der Ansicht ohne vollständig mit. Wenn der Benutzer auf das Objekt Tag-along gazes, erfolgt genauer an.

Wir verwenden wollen die **SimpleTagalong.cs** Datei die:

1. Bestimmt, ob das Tag-Along Objekt in dem kameragrenzen befindet.
2. Wenn dies nicht in der Frustums anzeigen, positionieren Sie die Tag-Along, teilweise in der Ansicht Frustums.
3. Positionieren Sie die Tag-Along, andernfalls zu einer Standard-Entfernung des Benutzers.

Zu diesem Zweck zunächst muss ändern wir die **Interactible.cs** Skript zum Aufrufen der **TagalongAction**.

1. Bearbeiten Sie **Interactible.cs** üben Sie nach Abschluss der Codierung 6.a (Aufheben der auskommentierung Zeilen 84 zu 87).

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

Die **InteractibleAction.cs** Skript zusammen mit **Interactible.cs** werden benutzerdefinierte Aktionen ausgeführt, wenn Sie auf Hologramme tippen. In diesem Fall verwenden wir eine speziell für Tag-along.

* In der **Skripts** Ordner, klicken Sie auf **TagalongAction.cs** Medienobjekt in Visual Studio zu öffnen.
* Führen Sie in dieser Übung Schreiben von Code aus oder ändern Sie ihn folgendermaßen:
  * Am oberen Rand der **Hierarchie**, in der Leiste Suchtyp **ChestButton_Center** , und wählen Sie das Ergebnis.
  * In der **Inspektor** Bereich, klicken Sie auf die **Add Component** Schaltfläche.
  * Geben Sie im Menü, in das Suchfeld **beigefügten Aktion**. Wählen Sie das Suchergebnis.
  * In **Hologramme** Ordner suchen der **beigefügten** Asset.
  * Wählen Sie die **ChestButton_Center** -Objekt in der **Hierarchie**. Drag & drop die **beigefügten** -Objekt aus der **Projekt** panel auf die **Inspektor** in die **Objekt um beigefügten** Eigenschaft.
  * Ziehen Sie die **beigefügten Aktion** -Objekt aus der **Inspektor** in die **Interactible Aktion** Feld der **Interactible** Skript.
* Klicken Sie mit der Doppelklicken auf die **TagalongAction** Skript, um es in Visual Studio zu öffnen.

![Interactible einrichten](images/holograms210-interactible.png)

Wir müssen die folgenden hinzufügen:

* Fügen Sie Funktionen für die PerformAction-Funktion im Skript TagalongAction (geerbt von InteractibleAction) hinzu.
* Fügen Sie die auf das Objekt gazed bei billboarding, und legen Sie die PowerPivot-Achse auf der XY.
* Fügen Sie einfach Tag-Along klicken Sie dann auf das Objekt hinzu.

Hier ist unsere Lösung aus **TagalongAction.cs**:

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
* Sehen Sie sich, wie der Inhalt die Mitte des Punkts Blicke, folgt jedoch nicht fortlaufend und ohne dass sie blockiert.
