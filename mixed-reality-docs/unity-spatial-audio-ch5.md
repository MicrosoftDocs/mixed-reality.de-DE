---
title: Lernprogramme für räumliche Audiodaten-5. Verwenden von Reverb zum Hinzufügen von Abstand zu räumlichem Audio
description: Fügen Sie einen Hall Effekt hinzu, um den Sinn der Abstands Variation zu räumlichem Audiomaterial zu verbessern.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: Gemischte Realität, Unity, Tutorial, hololens2, räumliche Audiodaten
ms.openlocfilehash: abe78417dc231e6228d1942e03418ba699bc0938
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182737"
---
# <a name="using-reverb-to-add-distance-to-spatial-audio"></a>Verwenden von Reverb zum Hinzufügen von Abstand zu räumlichem Audio

## <a name="objectives"></a>Ziele
In den vorherigen Kapiteln haben wir den Sound spatialization hinzugefügt, um Ihnen einen Eindruck von der Richtung zu vermitteln. In diesem fünften Kapitel fügen wir einen "Reverb"-Effekt hinzu, um Klänge einen Eindruck von der Entfernung zu geben. Unsere Ziele lauten:
* Verbessern der erkannten Entfernung von Soundquellen durch Hinzufügen von Reverb
* Den erkannten Abstand des Sounds mithilfe der Entfernung des Listener zum – Hologramm Steuern

## <a name="add-a-mixer-group-and-a-reverb-effect"></a>Hinzufügen einer mischkeitsgruppe und eines einfügenden Effekts
In [Kapitel 2](unity-spatial-audio-ch2.md)haben wir einen Mixer hinzugefügt. Der Mixer enthält standardmäßig eine **Gruppe** namens **Master**. Da wir nur einen "Hall"-Effekt auf einige Sounds anwenden möchten, fügen wir eine zweite **Gruppe** für diese Sounds hinzu. Um eine **Gruppe**hinzuzufügen, klicken Sie mit der rechten Maustaste auf die **Master** Gruppe im **Audiomixer** und wählen untergeordnete **Gruppe hinzufügen**aus:

![Untergeordnete Gruppe hinzufügen](images/spatial-audio/add-child-group.png)

In diesem Beispiel haben wir die neue Gruppe "Raumeffekt" benannt.

Jede **Gruppe** hat einen eigenen Satz von Effekten. Fügen Sie der neuen Gruppe einen connectoreffekt hinzu, indem Sie in der neuen Gruppe auf **Hinzufügen** klicken, und wählen Sie **SFX-Hall**:

![SFX-Reverb hinzufügen](images/spatial-audio/add-sfx-reverb.png)

In der audioterminologie wird der ursprüngliche, nicht widerzuhallte _Audiopfad als trockener Pfad_bezeichnet, und die Audiodatei nach dem Filtern mit dem Hall Filter wird als _Nasser Pfad_bezeichnet. Beide Pfade werden an die Audioausgabe gesendet, und ihre relativen Stärken in dieser Mischung werden als _nass/trocken Mischung_bezeichnet. Die nasse/trockene Mischung wirkt sich stark auf den Sinn der Entfernung aus.

Der **SFX-Reverb umfasst Steuer** Elemente, mit denen die nasse/trockene Mischung innerhalb des Effekts angepasst wird. Da das **Microsoft spatializer** -Plug-in den trockenen Pfad behandelt, verwenden wir den **SFX-Reverb** nur für den nassen Pfad. Im **inspektorbereich** Ihres **SFX-einhall**:
* Legen Sie die Eigenschaft "Dry Level" auf die niedrigste Einstellung fest (-10000 MB).
* Legen Sie die Eigenschaft "Room" auf die höchste Einstellung (0 MB) fest.

Nachdem diese Änderungen vorgenommen wurden, sieht der **inspektorbereich** des **SFX-Reverb** wie folgt aus:

![SFX-Reverb-Eigenschaften](images/spatial-audio/sfx-reverb-properties.png)

Mit den anderen Einstellungen wird das Gefühl des simulierten Raums gesteuert. Die **verwahrzeit** bezieht sich insbesondere auf die wahrgenommene Raum Größe. 

## <a name="enable-reverb-on-the-video-playback"></a>Aktivieren von "Reverb" für die Videowiedergabe
Zum Aktivieren von "Reverb" in einer Audioquelle müssen zwei Schritte ausgeführt werden:
* Leiten Sie die **Audioquelle** an die entsprechende **Gruppe** weiter.
* Festlegen des **Microsoft spatializer** -Plug-ins, um Audioinformationen zur Verarbeitung an die **Gruppe** zu übergeben

In den folgenden Schritten wird das Skript angepasst, um das Audiorouting zu steuern, und es wird ein mit dem **Microsoft spatializer** -Plug-in bereitgestelltes Steuerelement Skript zum Übertragen von Daten in den Reverb angehängt.

Klicken Sie im Bereich **Inspector** für **das**Vierfache auf **Komponente hinzufügen** , und fügen Sie das Raumeffekt-Skript auf **Sende Ebene** hinzu:

![Skript für Sende Ebene hinzufügen](images/spatial-audio/add-send-level-script.png)

> [!NOTE]
> Es sei denn, Sie aktivieren das Feature " **Sende Ebene für raumeffekte** " des **Microsoft spatializer** -Plug-ins, es sendet keine Audiodaten an die Unity-Audioengine zur Auswirkung der Verarbeitung.

Die Bereichs Effekt-Komponente der **Sende Ebene** enthält ein Graph-Steuerelement, mit dem die Audioebene festgelegt wird, die für die Verarbeitung von Reverb an die Unity-Audioengine Klicken und ziehen Sie die Kurve nach unten, um die Ebene auf ungefähr-30dB festzulegen:

![Hall Kurve anpassen](images/spatial-audio/adjust-reverb-curve.png)

Entfernen Sie dann die Auskommentierung der vier kommentierten Zeilen im **spatializeonoff** -Skript. Das Skript sieht nun wie folgt aus:
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    public AudioMixerGroup RoomEffectGroup;
    public AudioMixerGroup MasterGroup;

    private AudioSource m_SourceObject;
    private bool m_IsSpatialized;
    private TMPro.TextMeshPro m_TextMeshPro;

    public void Start()
    {
        m_SourceObject = gameObject.GetComponent<AudioSource>();
        m_TextMeshPro = ButtonTextObject.GetComponent<TMPro.TextMeshPro>();
        SetSpatialized();
    }

    public void SwapSpatialization()
    {
        if (m_IsSpatialized)
        {
            SetStereo();
        }
        else
        {
            SetSpatialized();
        }
    }

    private void SetSpatialized()
    {
        m_IsSpatialized = true;
        m_SourceObject.spatialBlend = 1;
        m_TextMeshPro.SetText("Set Stereo");
        m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

Durch das Auskommentieren dieser Zeilen werden dem **inspektorbereich** für das Skript zwei Eigenschaften hinzugefügt. Um diese festzulegen, legen Sie im Bereich **Inspector** der Komponente **spatialize on off** des **Quad**:
* Legen Sie die Eigenschaft " **Raumeffekt** " auf Ihre neue Platz Effekt-mischkeitsgruppe fest.
* Festlegen der **Master Group** -Eigenschaft auf die Master-Mixer-Gruppe

Nachdem diese Änderungen vorgenommen wurden, sieht die Eigenschaft **spatialize on off** wie folgt aus:

![Spatialize on off (erweitert)](images/spatial-audio/spatialize-on-off-extended.png)

## <a name="next-steps"></a>Nächste Schritte

Testen Sie Ihre APP auf einem hololens 2 oder im Unity-Editor. Wenn Sie nun die Schaltfläche in der APP zum Aktivieren der Spatialisierung berühren, leitet das Skript die Audiodatei an die Raumeffekt Gruppe weiter, um den Code hinzuzufügen. Beim Wechsel zu Stereo wird das Audiomaterial an die Master Gruppe weitergeleitet, und es wird vermieden, dass das Hinzufügen von Reverb erfolgt.

Sie haben die Lernprogramme "hololens 2 Spatial audiotutorial" für Unity abgeschlossen. Gratulation!


