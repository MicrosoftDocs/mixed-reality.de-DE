---
title: Räumliche Entwurf
description: Räumliche Sound ist ein leistungsstarkes Tool zum Immersion, Barrierefreiheit und UX-Entwurf in mixed Reality-Anwendungen.
author: joekellyms
ms.author: joekelly
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, räumliche Ton, Entwurf, Stil
ms.openlocfilehash: c758037300392d9365c16933677fb0f026976c2a
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750307"
---
# <a name="spatial-sound-design"></a>Räumliche Entwurf

Räumliche Sound ist ein leistungsstarkes Tool zum Immersion, Barrierefreiheit und UX-Entwurf in mixed Reality-Anwendungen.

Wenn Sie jemals gespielt haben [Marco Poloshirt](https://en.wikipedia.org/wiki/Marco_Polo_(game)), oder jemand Ihr Telefon, um Hilfe rufen Sie gefunden, die Sie kennen bereits die Bedeutung der räumlichen Sound. Sound Hinweise verwendet zum Suchen der Objekte, Aufsehen abrufen oder erhalten einen besseren Überblick über die Umgebung in unseren Alltag. Verhält sich desto genauer Ihrer app Sound, wie in der realen Welt, die weitere überzeugend und sich an, dass Ihre virtuellen Welt ist.

<br>

> [!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

## <a name="device-support"></a>Unterstützung von Geräten

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Funktion</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></td>
    </tr>
     <tr>
        <td>Räumliche Entwurf</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>


## <a name="four-key-things-spatial-sound-does-for-mixed-reality-development"></a>Vier wichtige Faktoren, die räumlichen Sound für mixed Reality-Entwicklung ist.

Standardmäßig werden Sounds in Stereo wiedergegeben. Dies bedeutet, dass keine räumlichen Position, der Sound wiedergegeben wird, damit der Benutzer nicht weiß, wo der Sound stammt. Räumliche Sound führt vier wichtige Aspekte für die Entwicklung von mixed Reality:

**Erden**

Ohne Ton nicht mehr virtuelle Objekte effektiv vorhanden sein, wenn wir unseren Kopf Ihnen aktivieren. Sie möchten in der Lage, diese Objekte zu hören, selbst wenn Sie nicht sichtbar, und können sie eine beliebige Stelle auf Sie suchen möchten, wie echte Objekte. Genau wie virtuelle Objekte visuell an die Hand geben werden um mit der realen Welt in blend müssen, müssen sie auch akustisch an die Hand geben werden. Räumliche Sound wie nahtlos der realen Welt-audio-Umgebung mit der digital-audio-Umgebung.

**Benutzereingriff**

Sie können nicht in mixed Reality-Umgebungen davon aus, in denen der Benutzer sieht und erwarten, dass sie etwas sehen, die Sie in der ganzen Welt visuell zu platzieren. Aber Benutzer können einen Sound wiedergeben, auch wenn das Objekt, das Abspielen des Audios dahinter ist immer hören. Benutzer werden verwendet, mit dem ihre Aufmerksamkeit, die nach Ihrem Klang - gezeichnet instinctually gehen wir auf ein Objekt, das wir erfahren Sie, um uns herum. Wenn Sie die Blicke Ihres Benutzers zu einer bestimmten Stelle, anstatt einen Pfeil, zeigen Sie diese visuell Sound platzieren, in diesem Standort eine sehr natürlichen und schnelle Möglichkeit, beraten weiterleiten möchten.

**Immersion**

Wenn Objekte verschieben oder in Konflikt stehen, können wir in der Regel die Interaktionen zwischen Materialien hören. Wenn also Ihre Objekte denselben laut vornehmen, die in der Praxis würden, ist ein Maß an Immersion verloren gehen – z. B. einen problematische Film mit dem Volume ganz nach unten ansehen. Alle Sounds in der realen Welt stammen aus einer bestimmten Stelle im Adressraum: auf, wenn wir unsere Mal "Kopf" aktivieren, wir hören, dass die Änderung der, in denen diese Sounds relativ zu unserer Ohren stammen und wir können den Speicherort der Sound auf diese Weise nachverfolgen. Spatialized Sounds bilden zusammen die "Verhalten" einer vor Ort über die wir sehen können.

**Entwerfen für**

In den meisten herkömmlichen interaktiven Benutzeroberflächen sind Interaktionen klingt wie Soundeffekte Benutzeroberfläche in standard Mono oder Stereo wiedergegeben. Aber da alles, was in mixed Reality im 3D-Raum – einschließlich der UI - vorhanden ist wird diese Objekte von spatialized Sounds profitieren. Wenn wir eine Schaltfläche in der realen Welt drücken, wird diese Schaltfläche der Klang, die, den wir hören, stammt. Durch spatializing Interaktion Sounds, bieten wir erneut eine natürlicheren und realistische Benutzeroberfläche.

## <a name="best-practices-when-using-spatial-sound"></a>Bewährte Methoden bei Verwendung des räumlichen sound

**Echte Sounds besser funktionieren als synthetischen oder unnatürlichen sounds**

Je vertrauter ist für Ihre Benutzer mit einem Typ des Sounds, die weitere tatsächlichen, die sie beibehalten, und desto einfacher wird werden in ihrer Umgebung gefunden. Eine menschliche Stimme, z. B. wird ein Sound sehr häufig, und Ihre Benutzer werden Suchen Sie ihn nur so schnell wie eine Person im Raum kommuniziert werden.

**Erwartung Vorrang vor simulation**

Wenn Sie auf einen Sound von einer bestimmten Richtung werden verwendet, werden Ihre Aufmerksamkeit in diese Richtung unabhängig von der räumlichen Hinweise geführt. Z. B. in den meisten Fällen, die wir hören, Vögel sind sie über uns. Abspielen des Audios von einem Bird in den meisten Fällen bewirkt den Benutzer zum Nachschlagen, auch, wenn Sie den Sound darunter platzieren. Dies ist in der Regel verwirrend, und es wird empfohlen, die Arbeit mit den Erwartungen, wie diese anstatt dagegen sinnvoller nutzen zu können.

**Die meisten Sounds sollten spatialized werden**

Wie bereits erwähnt, alles in Mixed Reality vorhanden ist, im 3D-Raum – Ihre Sounds sollte auch. Sogar Musik kann manchmal von Spatialization, profitieren, insbesondere dann, wenn es sich um ein Menü oder eine andere Benutzeroberfläche verknüpft ist.

**Vermeiden Sie unsichtbar korrekturemitter ab**

Da wir bedingte wurde haben Sounds ansehen, die wir, um uns herum hören, kann es sein, eine unnatürliche und sogar unnerving Erfahrung, um einen Sound zu suchen, der keine visual tätig ist. Sounds in der Praxis nicht leeren Bereich stammen, also nicht sicher sein, wenn ein audio Emitter innerhalb der Umgebung des Benutzers sofortige platziert wird, dass es auch zu sehen.

**Vermeiden Sie räumliche Maskierung**

Räumliche Sound basiert auf sehr subtil akustischen Hinweise, die durch andere Sounds überfordert sein können. Stellen Sie Stereo Musik oder ambient Sounds haben, sicher, dass sie niedrig genug ist, in der Mischung, Platz für die Details Ihrer spatialized Sounds, die den Benutzern ermöglicht, diese leicht gefunden, und bleiben klingt realistischer und natürliche sind.

## <a name="general-concepts-to-keep-in-mind-when-using-spatial-sound"></a>Allgemeine Konzepte zu bedenken, wenn räumliche Sound verwenden

**Räumliche Sound ist eine simulation**

Räumliche Sound am häufigsten verwendet ist, das einen Sound scheint, als wären sie von einem physischen oder virtuellen Objekt in der ganzen Welt ausgehen ist. Daher anfertigen spatialized Sound am sinnvollsten, die diese Objekte stammen.

Beachten Sie, dass die wahrgenommene Genauigkeit von räumlichen sound bedeutet, die ein Sound unbedingt aus der Mitte eines Objekts, der die Differenz ausgeben darf nicht bemerkbar, abhängig von der Größe des Objekts und Entfernung des Benutzers. Mit kleinen-Objekten wird der Mittelpunkt des Objekts in der Regel ausreichend. Bei größeren Objekten sollten Sie einen sound korrekturemitter oder mehrere korrekturemitter ab, an der bestimmten Stelle innerhalb des Objekts, die den Klang erstellt werden soll.

**Normalisieren Sie alle sounds**

Abstand Dämpfung erfolgt schnell in die erste Verbrauchseinheit des Benutzers, "", wie in der realen Welt. Alle Audiodateien um physisch genau Abstand Attenuation, und gewährleistet, dass ein Sound beteiligen normalisiert werden sollen. wenn mehrere-Zähler sofort (falls zutreffend). Das räumliche audio-Modul behandelt die Attenuation erforderlich, um einen Sound "fühlen", wie in einer bestimmten Entfernung (mit einer Kombination aus Attenuation und "Abstand Hinweise") ist, und alle Attenuation anwenden, Ihre Auswirkungen reduzieren können kann. Außerhalb von simuliert ein echtes Objekt, der ersten Verfall von distance *räumliche Sound* Sounds werden wahrscheinlich mehr als ausreichend für eine richtige Mischung aus Ihrem Audio.

**Ermittlung und Benutzer-Schnittstellen**

Wenn Audiohinweise verwenden, um die Aufmerksamkeit des Benutzers über ihre aktuelle Ansicht zu leiten, sollte der Sound akustische und in der Mischung, über keine Stereo-Audiodaten und anderen spatialized Sounds die aus der direktionalen audiohinweis abgelenkt werden möglicherweise deutlich. Sounds und Musik, die einem Element der Benutzeroberfläche (z. B. ein Menü) zugeordnet sind, sollte der sound Emitter dieses Objekt zugeordnet werden. Stereo und anderen nicht-Positionsargumenten audio wiedergeben können stellen spatialized Elemente für Benutzer schwierig zu finden (siehe oben: Vermeiden Sie räumliche Maskierung).

**Verwenden von räumlichen Sound über standard 3D Sound so weit wie möglich**

In mixed Reality, für die optimale Ergebnisse zu erzielen sollten 3D, Audio über räumliche Sound statt über ältere 3D, audio Technologien erreicht werden. Im Allgemeinen ist die verbesserte Spatialization der kleine CPU-Aufwand über standard-3D-sound. Standard-3D-Audio kann verwendet werden, für die mit niedriger Priorität Sounds, Sounds, die spatialized, aber nicht unbedingt auf ein Objekt physisch oder virtuell gebunden und Objekte, die der Benutzer nie für die Interaktion mit der app suchen muss.

## <a name="see-also"></a>Siehe auch
* [Raumklang](spatial-sound.md)
* [Räumliche Abbildung](spatial-mapping.md)
