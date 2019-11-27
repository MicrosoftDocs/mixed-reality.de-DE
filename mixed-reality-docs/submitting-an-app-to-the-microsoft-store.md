---
title: Senden einer APP an den Microsoft Store
description: In diesem Artikel erhalten Sie Tipps, wie Sie Ihre Mixed Reality-apps an die Microsoft Store übermitteln, einschließlich der Vorgehensweise zum Verpacken und Testen Ihrer APP und Tipps, um die Zertifizierung zu erhalten und die Auffindbarkeit Ihrer APP im Store zu unterstützen.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: APP, UWP, Übermittlung, Übermittlung, Filter, Metadaten, Systemanforderungen, Schlüsselwörter, Wack, Zertifizierung, Paket, AppX, Merchandising
ms.openlocfilehash: f2eb4093a2bea51d8c39b94d23777e426810981e
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539608"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>Senden einer APP an den Microsoft Store

Sowohl [hololens](hololens-hardware-details.md) als auch der Windows 10-PC, der Ihr [immersives Headset](immersive-headset-hardware-details.md) antreibt, werden universelle Windows-Plattform-apps ausgeführt. Unabhängig davon, ob Sie eine APP übermitteln, die hololens oder PCs unterstützt (oder beides), übermitteln Sie Ihre APP an die Microsoft Store über [Partner Center](https://partner.microsoft.com/dashboard).

Wenn Sie noch nicht über ein Partner Center-Entwicklerkonto verfügen, können Sie [sich noch heute anmelden](https://developer.microsoft.com/store/register).

## <a name="packaging-a-mixed-reality-app"></a>Verpacken einer Mixed Reality-App

### <a name="prepare-image-assets-included-in-the-appx"></a>Vorbereiten von Image Assets, die in AppX enthalten sind

Es gibt mehrere Bild Ressourcen, die für die AppX-Buildtools erforderlich sind, um Ihre Anwendung in ein AppX-Paket zu erstellen, das Sie an den Speicher senden Weitere Informationen zu den [Richtlinien für Kachel-und Symbol Ressourcen](https://msdn.microsoft.com/library/windows/apps/mt412102.aspx) finden Sie auf der MSDN-Website.

| Erforderliches Asset | Empfohlene Skalierung | Bild Format | Wo wird dieses angezeigt? | 
|----------|----------|----------|------------------|
| Quadratisches Logo 71x71 | Beliebig |  PNG | n. v. | 
| Quadratisches Logo 150x150 | 150x150 (100% Skala) oder 225 x 225 (150% Skalierung) | PNG | Start-Pins und alle apps (wenn 310x310 nicht bereitgestellt wird), Store-Suchvorschläge, Store-Listenseite, Store-durchsuchen, Store-Suche | 
|  Breites 310x150-Logo |  Beliebig  |  PNG  |  n. v. | 
|  Store-Logo |  75x75 (150% Skalierung)  |  PNG  |  Partner Center, Berichts-APP, Schreiben einer Überprüfung, meine Bibliothek | 
|  Begrüßungsbildschirm |  930x450 (150% Skalieren)  |  PNG  |  2D-App-Startfeld (Slate) | 

Es gibt auch einige empfohlene Ressourcen, die von hololens genutzt werden können.

| Empfohlene Assets | Empfohlene Skalierung | Wo wird dieses angezeigt? | 
|----------|----------|----------|
|  Quadratisches Logo 310x310 |  310x310 (150% Skalieren) |  Start-Pins und alle apps | 

### <a name="live-tile-requirements"></a>Live-Kachel Anforderungen

Im Startmenü von hololens wird das größte enthaltene quadratische Kachel Bild verwendet.

Möglicherweise haben einige apps, die von Microsoft veröffentlicht wurden, ein 3D-Start Programm für Ihre Anwendung. Entwickler können mithilfe [dieser Anweisungen](implementing-3d-app-launchers.md)ein 3D-Start Programm für Ihre APP hinzufügen.

### <a name="specifying-target-and-minimum-version-of-windows"></a>Angeben von Ziel-und Mindestversion von Windows

Wenn Ihre Mixed Reality-App Features enthält, die für eine bestimmte Version von Windows spezifisch sind, ist es wichtig, die Ziel-und mindestplattformversionen anzugeben, die ihre universelle Windows-Anwendung unterstützt.

**Dies gilt insbesondere für apps, die auf [Windows Mixed Reality-immersive Headsets](immersive-headset-hardware-details.md)abzielen, die mindestens das Windows 10 Fall Creators Update erfordern (10,0; Build 16299), um ordnungsgemäß zu funktionieren.**

Wenn Sie in Visual Studio ein neues universelles Windows-Projekt erstellen, werden Sie aufgefordert, die Ziel-und Mindestversion von Windows festzulegen. Sie können diese Einstellung auch für ein vorhandenes Projekt ändern, indem Sie im Menü "Projekt" die > Eigenschaften Ihres App-namens unten im Dropdown Menü <.

![Festlegen der Versionen der minimal-und Zielplattform in Visual Studio 2019](images/visual-studio-min-version-500px.png)<br>
Festlegen der Mindest-und Ziel Platt Form Versionen in Visual Studio

### <a name="specifying-target-device-families"></a>Angeben von Zielgeräte Familien

Windows Mixed Reality-Anwendungen (sowohl für [hololens](hololens-hardware-details.md) als auch für [immersive Headsets](immersive-headset-hardware-details.md)) sind Teil der universelle Windows-Plattform, sodass jedes app-Paket mit der [Zielgeräte Familie](https://msdn.microsoft.com/library/windows/apps/dn986903.aspx) "Windows. Universal" in hololens ausgeführt werden kann. Windows 10-PCs mit immersiven Headsets. Wenn Sie keine Zielgeräte Familie in Ihrem App-Manifest angeben, können Sie Ihre APP versehentlich auf unbeabsichtigten Windows 10-Geräten öffnen. Führen Sie die folgenden Schritte aus, um die gewünschte Windows 10-Gerätefamilie anzugeben, und überprüfen Sie dann, [ob die richtigen Gerätefamilien ausgewählt sind, wenn Sie das App-Paket in Partner Center hochladen, um Sie an den Store zu übermitteln.](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

Um dieses Feld in Visual Studio festzulegen, klicken Sie mit der rechten Maustaste auf "Package. appxmanifest", und wählen Sie "Code anzeigen", und suchen Sie nach dem Feld targetdevicefamily Name. Standardmäßig könnte es wie folgt aussehen:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Wenn Ihre APP für **hololens**erstellt wurde, können Sie sicherstellen, dass Sie nur auf hololens installiert wird, indem Sie die Zielgeräte Familie "Windows. Holographic" angeben. 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Wenn Ihre APP eine spezielle Funktionalität von **hololens 2** erfordert, wie z. b. die Überwachung von Nachrichten oder die Hand Verfolgung, können Sie sicherstellen, dass Sie auf Windows-Versionen 18362 oder höher ausgerichtet ist, indem Sie die Zielgeräte Familie "Windows. Holographic" und MinVersion 10.0.18362.0 angeben. 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.18362.0" MaxVersionTested="10.0.18362.0" />
</Dependencies>
```

Wenn Ihre APP für **Windows Mixed Reality-immersive Headsets**erstellt wurde, können Sie sicherstellen, dass Sie nur auf Windows 10-PCs mit dem Windows 10 Fall Creators Update installiert wird (erforderlich für Windows Mixed Reality), indem Sie die Zielgeräte Familie angeben. Windows. Desktop "und MinVersion von" 10.0.16299.0 ".

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

Wenn Ihre APP zum Schluss sowohl auf **hololens-als auch in Windows Mixed Reality-immersiven Headsets**ausgeführt werden soll, können Sie sicherstellen, dass die app nur für diese beiden Gerätefamilien verfügbar gemacht wird, und gleichzeitig sicherstellen, dass jedes Ziel die richtige minimale Windows-Version durch Einschließen einer Zeile für jede Zielgeräte Familie mit der jeweiligen MinVersion.

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Weitere Informationen zur Zielgruppe von Gerätefamilien finden Sie in der [Dokumentation zu targetdevicefamily UWP](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily).

### <a name="associate-app-with-the-store"></a>App mit Store verknüpfen

Wählen Sie im Menü Projekt in der Visual Studio-Projekt Mappe "Store > app mit dem Store verknüpfen" aus. Wenn Sie dies tun, können Sie Kauf-und Benachrichtigungs Szenarien in Ihrer APP testen. Wenn Sie Ihre APP mit dem Store verknüpfen, werden diese Werte in die APP-Manifest-Datei für das aktuelle Projekt auf dem lokalen Computer heruntergeladen:
* Anzeige Name des Pakets
* Paketname
* Herausgeber-ID
* Anzeige Name des Herausgebers
* Version

Wenn Sie die Standarddatei "Package. appxmanifest" überschreiben, indem Sie eine benutzerdefinierte XML-Datei für das Manifest erstellen, können Sie die APP nicht mit dem Store verknüpfen. Wenn Sie versuchen, dem Speicher eine benutzerdefinierte Manifest-Datei zuzuordnen, wird eine Fehlermeldung angezeigt.

### <a name="creating-an-upload-package"></a>Erstellen eines Uploadpakets

Befolgen Sie die Richtlinien unter [Verpacken von universellen Windows-Apps für Windows 10](https://msdn.microsoft.com/library/hh454036.aspx#Anchor_2).

Der letzte Schritt beim Erstellen eines Uploadpakets ist das Überprüfen des Pakets mit dem [zertifizierungskit für Windows-apps](#windows-app-certification-kit).

Wenn Sie einem vorhandenen Produkt, das auf anderen Windows 10-Gerätefamilien verfügbar ist, ein Paket speziell für hololens hinzufügen, möchten Sie auch erfahren, [wie sich Versionsnummern darauf auswirken können, welche Pakete an bestimmte Kunden übermittelt werden](https://msdn.microsoft.com/library/windows/apps/mt188602.aspx). [wie Pakete an verschiedene Betriebssysteme verteilt werden](https://msdn.microsoft.com/library/windows/apps/mt188601.aspx).

Die allgemeine Anleitung besteht darin, dass das Paket mit der höchsten Versionsnummer, das auf ein Gerät anwendbar ist, das Paket ist, das vom Speicher verteilt wird.

Wenn ein Windows. Universal-Paket und ein Windows. Holographic-Paket vorhanden sind und das Windows. Universal-Paket eine höhere Versionsnummer aufweist, wird ein hololens-Benutzer die höhere Versionsnummer Windows. Universal Package anstelle von Windows. Holographic herunterladen. Paketen. Es gibt mehrere Lösungen für dieses Problem:
1. Stellen Sie sicher, dass Ihre plattformspezifischen Pakete, wie z. b. Windows. Holographic, immer eine höhere Versionsnummer haben als ihre plattformunabhängigen Pakete wie Windows. Universal
2. Packen Sie apps nicht als Windows. Universal, wenn Sie auch plattformspezifische Pakete verwenden, und Verpacken Sie stattdessen das Windows. Universal-Paket für die spezifischen Plattformen, auf denen es verfügbar sein soll.

>[!NOTE]
> Zur Unterstützung Ihrer APP auf hololens (1. Gen) und hololen 2 müssen Sie zwei App-Pakete hochladen. eine, die x86 für hololens (1. Gen) enthält, und eine, die Arm oder ARM64 für hololens 2 enthält. 
> 
> Wenn Sie sowohl Arm als auch ARM64 in das Paket einschließen, wird die ARM64-Version auf hololens 2 verwendet. 

>[!NOTE]
> Sie können ein einzelnes Paket deklarieren, das auf mehrere Zielgeräte Familien anwendbar ist.

3. Erstellen Sie ein einzelnes Windows. Universal-Paket, das auf allen Plattformen funktioniert. Die Unterstützung für diese Lösung ist zurzeit nicht groß, sodass die oben genannten Lösungen empfohlen werden.

## <a name="testing-your-app"></a>Testen Ihrer App

### <a name="windows-app-certification-kit"></a>Zertifizierungskit für Windows-Apps

Wenn Sie App-Pakete erstellen, die über Visual Studio an Partner Center übermittelt werden sollen, werden Sie vom Assistenten zum Erstellen von App-Paketen aufgefordert, das zertifizierungskit für Windows-Apps für die erstellten Pakete auszuführen. Um einen reibungslosen Übermittlungs Prozess für den Speicher zu bieten, sollten Sie sicherstellen, dass das [zertifizierungskit für Windows-apps](https://msdn.microsoft.com/library/windows/apps/jj657973.aspx) auf dem lokalen Computer an Ihre APP weitergeleitet wird, bevor Sie Sie an den Speicher senden. Das Ausführen des zertifizierungskit für Windows-apps auf einem Remote hololens wird derzeit nicht unterstützt.

### <a name="run-on-all-targeted-device-families"></a>Auf allen Zielgeräte Familien ausführen

Mit der universellen Windows-Plattform können Sie eine einzelne Anwendung erstellen, die auf allen Windows 10-Gerätefamilien ausgeführt wird. Es ist jedoch nicht gewährleistet, dass universelle Windows-Apps nur für alle Gerätefamilien funktionieren. Bevor Sie Ihre APP auf hololens oder einer anderen Windows 10-Zielgeräte Familie verfügbar machen, ist es wichtig, dass Sie [die APP](testing-your-app-on-hololens.md) auf jeder dieser Gerätefamilien testen, um eine gute Leistung zu gewährleisten.

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>Übermitteln Ihrer Mixed Reality-APP an den Store

Wenn Sie eine Mixed Reality-App übermitteln, die auf einem Unity-Projekt basiert, sehen Sie sich dieses [Video](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) zuerst an.

Im Allgemeinen ist das Senden einer Windows Mixed Reality-APP, die auf hololens und/oder immersiven Headsets funktioniert, genauso wie das Übermitteln einer beliebigen UWP-APP an den Microsoft Store. Nachdem Sie [Ihre APP durch reservieren Ihres Namens erstellt](https://docs.microsoft.com/windows/uwp/publish/create-your-app-by-reserving-a-name)haben, sollten Sie der [Checkliste für die UWP-Übermittlung](https://docs.microsoft.com/windows/uwp/publish/app-submissions)folgen.

Eine der ersten Schritte ist die [Auswahl einer Kategorie und Unterkategorie](https://docs.microsoft.com/windows/uwp/publish/category-and-subcategory-table) für ihre gemischte Realität. Es ist wichtig, dass Sie **die genaueste Kategorie für Ihre App auswählen** , damit wir Ihre Anwendung in den richtigen Store-Kategorien bereitstellen und sicherstellen können, dass Sie mithilfe relevanter Such Abfragen angezeigt wird. Das **auflisten Ihres VR-Titels als Spiel führt nicht zu einer besseren verfügbar machung Ihrer APP** und kann verhindern, dass Sie in Kategorien angezeigt wird, die besser geeignet und weniger überfüllt sind.

Es gibt jedoch vier wichtige Bereiche im Übermittlungs Prozess, in denen Sie gemischte Reality-spezifische Auswahl treffen möchten:
1. Im Abschnitt **[Produkt Deklarationen](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** unter [Eigenschaften](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties).
2. Im Abschnitt " **[System Anforderungen](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** " unter " [Eigenschaften](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)".
3. Im Abschnitt **[Gerätefamilien Verfügbarkeit](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** unter [Pakete](https://docs.microsoft.com/windows/uwp/publish/upload-app-packages).
4. In einigen der Seiten Felder der **[Store-Auflistung](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** .

### <a name="mixed-reality-product-declarations"></a>Mixed Reality-Produkt Deklarationen

Auf der Seite **[Eigenschaften](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** des App-Übermittlungs Prozesses finden Sie im Abschnitt **[Produkt Deklarationen](https://docs.microsoft.com/windows/uwp/publish/app-declarations)** mehrere Optionen im Zusammenhang mit Mixed Reality.

![Mixed Reality-Produkt Deklarationen](images/product-declarations-900px.png)<br>
Mixed Reality-Produkt Deklarationen

Zuerst möchten Sie die Gerätetypen identifizieren, für die Ihre APP eine gemischte Realität bietet. Dadurch wird sichergestellt, dass Ihre APP in Windows Mixed Reality-Auflistungen im Store enthalten ist, und dass Sie für Benutzer, die den Store durchsuchen, nach dem Verbinden eines immersiven Headsets (oder beim Durchsuchen des Stores auf hololens) angezeigt werden.

Neben "Diese Darstellung ist für Windows Mixed Reality konzipiert auf:"
* Aktivieren Sie das Kontrollkästchen **PC** nur dann, wenn Ihre APP eine VR-Darstellung bietet, wenn ein immersives Headset mit dem PC des Benutzers verbunden ist. Aktivieren Sie dieses Kontrollkästchen, unabhängig davon, ob Ihre APP ausschließlich auf einem immersiven Headset ausgeführt wird oder ob es sich um ein Standard-PC-Spiel bzw. eine Standard-App handelt, das einen gemischten Reality-Modus und/oder Bonus Inhalt bietet, wenn ein Headset angeschlossen ist.
* Aktivieren Sie das Feld **hololens** nur dann, wenn Ihre APP in hololens eine holografische Darstellung bietet.
* Aktivieren Sie **beide** Kontrollkästchen, wenn Ihre APP eine gemischte Realität für beide Gerätetypen bietet, z. b. die [gemischte Reality Academy-app "Project Island"](mixed-reality-250.md) von Build 2017.

Wenn Sie oben "PC" ausgewählt haben, empfiehlt es sich, das Setup für die gemischte Realität (Aktivitäts Ebene) festzulegen. Dies gilt nur für Umgebungen mit gemischter Realität, die auf PCs ausgeführt werden, die mit immersiven Headsets verbunden sind, da gemischte Reality-apps auf hololens weltweit skaliert sind und der Benutzer während des Setups keine Grenze definiert.
* Wählen Sie "sitzend" und " **stehend** " aus, wenn Ihre APP mit der Absicht entworfen wurde, dass der Benutzer an einer Position bleibt (ein Beispiel wäre ein Spiel, bei dem Sie in einem Cockpit eines Flugzeugs sitzen).
* Wählen Sie **alle Erfahrungen** aus, wenn Ihre APP mit der Absicht entworfen wurde, dass der Benutzer innerhalb der Grenze, die er während des Setups definiert hat, herumläuft (ein Beispiel wäre ein Spiel, bei dem Sie gegen Angriffe gegen Angriffe durchlaufen haben).

### <a name="mixed-reality-system-requirements"></a>Systemanforderungen für gemischte Realität

Auf der **[Eigenschaften](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** Seite des App-Übermittlungs Vorgangs finden Sie im Abschnitt " **[System Anforderungen](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties#system-requirements)** " mehrere Optionen im Zusammenhang mit Mixed Reality.

![Systemanforderungen](images/system-reqs-800px.png)<br>
Systemanforderungen

In diesem Abschnitt identifizieren Sie die minimale (erforderliche) Hardware und die empfohlene (optionale) Hardware für Ihre Mixed Reality-app.

**Eingabe Hardware:**

Verwenden Sie die Kontrollkästchen, um potenziellen Kunden mitzuteilen, ob Ihre APP **Mikrofon** (für [Spracheingabe](voice-input.md)), **[Xbox-Controller oder Gamepad](hardware-accessories.md#bluetooth-gamepads)** und/oder **[Windows Mixed Reality Motion-Controller](motion-controllers.md)** unterstützt. Diese Informationen werden auf der Produktdetailseite Ihrer APP im Store angezeigt und helfen Ihnen, Ihre APP in die entsprechenden App-/spielauflistungen aufzunehmen (beispielsweise kann eine Sammlung für alle Spiele vorhanden sein, die Motion-Controller unterstützen).

Beachten Sie, dass Sie Kontrollkästchen für "Minimale Hardware" oder "Empfohlene Hardware" für Eingabetypen auswählen. 

Zum Beispiel: 
* Wenn das Spiel Bewegungs Controller erfordert, aber eine Spracheingabe über Mikrofon akzeptiert, aktivieren Sie das Kontrollkästchen "Minimale Hardware" neben "Windows Mixed Reality Motion Controllers", aber das Kontrollkästchen "Empfohlene Hardware" neben "Mikrofon". 
* Wenn Ihr Spiel entweder mit einem Xbox-Controller/Gamepad oder Bewegungs Controllern abgespielt werden kann, können Sie das Kontrollkästchen "Minimale Hardware" neben "Xbox Controller" oder "Gamepad" aktivieren und das Kontrollkästchen "Empfohlene Hardware" neben "Windows Mixed Reality Motion" aktivieren. Controller als Bewegungs Controller bieten wahrscheinlich eine Schritt-für-Schritt-Anleitung aus dem Gamepad.

**Immersives Headset für Windows Mixed Reality:**

Die Angabe, ob ein immersives Headset zur Verwendung Ihrer APP erforderlich ist oder optional ist, ist wichtig für Kundenzufriedenheit und Bildungseinrichtungen.

Wenn Ihre APP *nur* über ein immersives Headset verwendet werden kann, aktivieren Sie das Kontrollkästchen "Minimale Hardware" neben "Windows Mixed Reality-immersives Headset". Dies wird auf der Produktdetailseite Ihrer APP im Store als Warnung über der Schaltfläche "kaufen" angezeigt, sodass Kunden nicht glauben, dass Sie eine APP kaufen, die auf Ihrem PC funktioniert, wie eine herkömmliche Desktop-App.

Wenn Ihre APP auf dem Desktop wie eine herkömmliche PC-app ausgeführt wird, aber eine VR-Benutzer Darstellung bietet, wenn ein immersives Headset verbunden ist (unabhängig davon, ob der vollständige Inhalt Ihrer app verfügbar ist, oder nur ein Teil), aktivieren Sie das Kontrollkästchen "Empfohlene Hardware" neben "Windows Mixed Reality". immersives Headset. " Über der Schaltfläche kaufen auf der Produktdetailseite Ihrer APP wird keine Warnung angezeigt, wenn Ihre APP als herkömmliche Desktop-App fungiert, ohne dass ein immersives Headset angeschlossen ist.

**PC-Spezifikationen:**

Wenn Sie möchten, dass Ihre APP so viele Windows Mixed Reality-immersive Headset-Benutzer wie möglich erreicht, sollten Sie die PC-Spezifikationen für [Windows Mixed Reality-PCs mit integrierten Grafiken](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)als [Ziel](understanding-performance-for-mixed-reality.md) haben.

Unabhängig davon, ob Ihre Mixed Reality-APP die Mindestanforderungen für Windows Mixed Reality-PCs erfüllt oder eine bestimmte PC-Konfiguration erforderlich ist (z. b. die dedizierte GPU eines [Windows Mixed Reality Ultra-PCs](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)), sollten Sie angeben, dass mit den relevanten PC-Spezifikationen in die Spalte "Minimale Hardware".

Wenn Ihre Mixed Reality-App für eine bessere Leistung konzipiert ist oder Grafiken mit höherer Auflösung auf einer bestimmten PC-Konfiguration oder Grafikkarte anbieten soll, sollten Sie angeben, dass die entsprechenden PC-Spezifikationen in der Spalte "Empfohlene Hardware" angezeigt werden.

Dies gilt nur, wenn Ihre Mixed Reality-App ein immersives Headset verwendet, das mit einem PC verbunden ist. Wenn Ihre Mixed Reality-app nur auf hololens ausgeführt wird, müssen Sie keine PC-Spezifikationen angeben, da hololens nur eine Hardwarekonfiguration aufweist.

### <a name="device-family-availability"></a>Verfügbarkeit von Gerätefamilien

Wenn Sie Ihre APP in Visual Studio [ordnungsgemäß verpackt](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) haben, sollte diese auf der Seite Pakete des App-Übermittlungs Prozesses hochgeladen werden, und es wird eine Tabelle erstellt, in der die Gerätefamilien, denen Ihre APP zur Verfügung steht

![Verfügbarkeits Tabelle der Gerätefamilie](images/device-family-table-900px.png)<br>
Verfügbarkeits Tabelle der Gerätefamilie

Wenn Ihre Mixed Reality-App auf immersiven Headsets funktioniert, sollte mindestens "Windows 10 Desktop" in der Tabelle ausgewählt werden. Wenn Ihre Mixed Reality-App auf hololens funktioniert, sollte mindestens "Windows 10 Holographic" ausgewählt werden. Wenn Ihre APP sowohl in Windows Mixed Reality-Headset-Typen wie der [Mixed Reality Academy "Project Island"-App](mixed-reality-250.md)ausgeführt wird, sollten sowohl "Windows 10 Desktop" als auch "Windows 10 Holographic" ausgewählt werden.

>[!TIP]
>Viele Entwickler treten beim Hochladen des App-Pakets im Zusammenhang mit Konflikten zwischen dem Paket Manifest und ihren App-/Herausgeber-Kontoinformationen in Partner Center Fehler auf. Diese Fehler können häufig vermieden werden, indem Sie sich bei Visual Studio mit demselben Konto anmelden, das mit Ihrem Windows-Entwicklerkonto verknüpft ist (das Konto, das Sie zum Anmelden bei Partner Center verwenden). Wenn Sie dasselbe Konto verwenden, können Sie Ihre APP mit ihrer Identität in der Microsoft Store verknüpfen, bevor Sie Sie Verpacken.

![Ihre APP mit der Microsoft Store verknüpfen](images/associate-your-app-700px.png)<br>
Zuordnen der APP zum Microsoft Store in Visual Studio

### <a name="store-listing-page"></a>Store-Listenseite

Auf der Seite [Store-Auflistung](https://docs.microsoft.com/windows/uwp/publish/create-app-store-listings) des App-Übermittlungs Vorgangs können Sie nützliche Informationen zu ihrer Mixed Reality-app hinzufügen.

>[!IMPORTANT]
>Um sicherzustellen, dass Ihre APP ordnungsgemäß vom Store kategorisiert und für Windows Mixed Reality-Kunden auffindbar ist, sollten Sie **"Windows Mixed Reality"** als einen ihrer "Suchbegriffe" für die APP hinzufügen. (Sie können Suchbegriffe suchen, indem Sie die "freigegebenen Felder" erweitern. -Abschnitt).

![Windows Mixed Reality zu Suchbegriffen hinzufügen](images/search-terms-800px.png)<br>
Zu Suchbegriffen "Windows Mixed Reality" hinzufügen

## <a name="offering-a-free-trial-for-your-game-or-app"></a>Kostenlose Testversion für Ihr Spiel oder Ihre APP

Viele Consumer sind vor dem Erwerb eines Windows Mixed Reality-immersiven Headsets auf keine benutzerfreundliche Realität beschränkt. Sie wissen möglicherweise nicht, was von intensiven Spielen zu erwarten ist, und sind unter Umständen nicht mit Ihrem eigenen Komfort Schwellenwert vertraut. Viele Kunden können auch ein Windows Mixed Reality-immersives Headset auf PCs testen, die nicht als [Windows Mixed Reality-PCs](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)gebadelt sind. Aus diesen Gründen wird dringend empfohlen, eine [Kostenlose Testversion](https://docs.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#free-trial) für Ihre kostenpflichtige Mixed Reality-APP oder Ihr Spiel zu bieten.

## <a name="see-also"></a>Weitere Informationen:
* [Mixed Reality](mixed-reality.md)
* [Entwicklung – Übersicht](development.md)
* [App-Ansichten](app-views.md)
* [Grundlegendes zur Leistung für gemischte Realität](understanding-performance-for-mixed-reality.md)
* [Empfehlungen zur Leistung für Unity](performance-recommendations-for-unity.md)
* [Testen Ihrer App auf HoloLens](testing-your-app-on-hololens.md)
* [Windows Mixed Reality-Mindestanforderungen für die PC-Hardware Kompatibilität](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
