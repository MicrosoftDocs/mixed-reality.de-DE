---
title: Übermitteln einer app an den Microsoft Store
description: Dieser Artikel enthält Tipps zur Ihrer mixed Reality-apps, die Microsoft Store, einschließlich Informationen zum Packen und Testen Sie Ihre app und Tipps zur Zertifizierung übergeben und bei der Auffindbarkeit Ihrer App in den Store übermitteln.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Uwp-App übermitteln, Übermittlung, Filter, Metadaten, Systemanforderungen, Schlüsselwörter, Wack, Zertifizierung, Paket, Appx, merchandising
ms.openlocfilehash: 4eb69fbaa22f4864305f09d5e1bf1c1860a0d31f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594572"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>Übermitteln einer app an den Microsoft Store

Beide [HoloLens](hololens-hardware-details.md) und die Windows 10-PCs Verbessern der Leistung Ihrer [immersive Kopfhörer](immersive-headset-hardware-details.md) apps der universellen Windows-Plattform ausführen. Ob Sie eine app, die HoloLens oder PC (oder beides) unterstützt senden können, müssen Sie Ihre app über den Microsoft Store-übermitteln [Partner Center](https://partner.microsoft.com/dashboard).

Wenn Sie bereits ein Partner Center-Developer-Konto haben, können Sie [registrieren Sie sich heute](https://developer.microsoft.com/store/register).

## <a name="packaging-a-mixed-reality-app"></a>Verpacken einer mixed Reality-app

### <a name="prepare-image-assets-included-in-the-appx"></a>Vorbereiten von Bildanlagen in die AppX-Datei enthalten

Es gibt mehrere Bildanlagen erforderlich, durch die AppX-Datei erstellen von Tools zum Erstellen der Anwendung in einem Appx-Paket an den Store übermitteln. Erfahren Sie mehr über [Richtlinien für die Kachel "und" Symbol-Objekte](https://msdn.microsoft.com/library/windows/apps/mt412102.aspx) auf MSDN.

| Erforderliche Asset | Empfohlene skalieren | Bildformat | Wo angezeigt dies? | 
|----------|----------|----------|------------------|
| Quadratisches Logo 71 x 71 | Beliebig |  PNG | Nicht zutreffend | 
| Quadratisches Logo 150 x 150 | 150 x 150 (100 %-Skalierung) oder 225 x 225 (150 % skalieren) | PNG | Starten von Pins und alle Apps (falls es sich um eine 310 x 310 nicht bereitgestellt wird), Store Suchvorschläge, Store Seite Auflistung Store durchsuchen, Store durchsuchen | 
|  Breites 310 x 150-Logo |  Beliebig  |  PNG  |  Nicht zutreffend | 
|  Store-Logo |  75 x 75 (150 % skalieren)  |  PNG  |  Partner Center, die Bericht-App, Schreiben Meine Bibliothek mit der Bezeichnung Rezension | 
|  Begrüßungsbildschirm |  930 x 450 (150 % skalieren)  |  PNG  |  Direct2D-app-Startprogramm (Slate-Objekt) | 

Es gibt auch einige empfohlene Ressourcen, die HoloLens nutzen können.

| Empfohlene Ressourcen | Empfohlene skalieren | Wo angezeigt dies? | 
|----------|----------|----------|
|  Quadratisches Logo 310 x 310 |  310 x 310 (150 % skalieren) |  Start-Pins und alle Apps | 

### <a name="live-tile-requirements"></a>Live-Kachel-Anforderungen

Klicken Sie im Menü Start auf HoloLens verwendet das größte enthalten quadratische Kachel-Bild.

Sie können sehen, dass einige von Microsoft veröffentlichten apps 3D Startprogramm für ihre Anwendung. Entwickler können für ihre app mithilfe ein 3D-Startprogramms hinzufügen [diese Anweisungen](implementing-3d-app-launchers.md).

### <a name="specifying-target-and-minimum-version-of-windows"></a>Angeben von Ziel und die Mindestversion von Windows

Wenn Ihre mixed Reality-app Funktionen, die spezifisch für eine bestimmte Version von Windows sind enthält, ist es wichtig, an den Ziel- und mindestplattformversionen aus, denen Ihre universelle Windows-Anwendung unterstützt werden.

**Dies gilt insbesondere für apps und [Windows Mixed Reality immersive Headsets](immersive-headset-hardware-details.md), was erfordern mindestens die Windows 10 Fall Creators Update (10.0; Build 16299) ordnungsgemäß funktioniert.**

Sie werden aufgefordert, Ziel und die Mindestversion von Windows festlegen, wenn Sie ein neues universelles Windows-Projekt in Visual Studio erstellen. Sie können auch diese Einstellung für ein vorhandenes Projekt im Menü "Projekt", klicken Sie dann "< Name Ihrer app > Eigenschaften" am unteren Rand der Dropdown-Menü ändern.

![Legen Sie Mindest- und Ziel-Plattformversionen in Visual Studio 2017](images/visual-studio-min-version-500px.png)<br>
Legen Sie Mindest- und Ziel-Plattformversionen in Visual Studio

### <a name="specifying-target-device-families"></a>Ziel-gerätefamilien angeben

Windows Mixed Reality-Anwendungen (für beide [HoloLens](hololens-hardware-details.md) und [immersive Headsets](immersive-headset-hardware-details.md)) sind Teil der universellen Windows-Plattform, sodass alle app-Paket mit einem [Ziel Gerätefamilie](https://msdn.microsoft.com/library/windows/apps/dn986903.aspx)"Windows.Universal" ist für HoloLens oder Windows 10-PCs mit immersive Headsets ausgeführt werden kann. Wenn Sie eine Ziel-Gerätefamilie nicht im app-Manifest angeben versehentlich Ihre bis zu unbeabsichtigten Windows 10-Geräte-app öffnen kann. Die folgenden Schritte an der vorgesehenen Familie der Windows 10-Gerät, und klicken Sie dann [überprüfen Sie, dass die richtigen gerätefamilien ausgewählt sind, beim Hochladen des Anwendungspakets im Partner Center an den Store übermitteln.](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store)

Zum Festlegen dieses Feld in Visual Studio klicken Sie mit der rechten Maustaste auf die Datei "Package.appxmanifest" Wählen Sie "Code anzeigen", und suchen Sie das Feld TargetDeviceFamily-Namen. Standardmäßig können sie wie folgt aussehen:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Wenn Ihre app erstellt wurde, für die **HoloLens**, können Sie sicherstellen, dass diese nur für HoloLens installiert ist, durch Angabe von "Windows.Holographic" eine Ziel-Gerätefamilie. 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Wenn Ihre app erstellt wurde, für die **Windows Mixed Reality immersive Headsets**, und Sie sicherstellen können, dass diese nur auf Windows 10-PCs mit Windows 10 Fall Creators Update (erforderlich für Windows Mixed Reality) installiert ist, durch Angeben eines Ziels Gerätefamilie "Windows.Desktop" und "MinVersion" von "10.0.16299.0".

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

Schließlich, wenn Ihre app auf beide ausgeführt werden soll **HoloLens und Windows Mixed Reality immersive Headsets**, Sie können sicherstellen, dass die app ist nur in an diese zwei gerätefamilien verfügbar gemacht und gleichzeitig sicherstellen jeweils die richtige abzielt Mindestversion Windows, indem Sie eine Zeile für jede Gerätefamilie Ziel, mit der jeweiligen "MinVersion" einschließen.

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Weitere Informationen finden Sie Informationen zu auf gerätefamilien durch Lesen der [TargetDeviceFamily-UWP-Dokumentation](https://docs.microsoft.com/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily).

### <a name="associate-app-with-the-store"></a>App mit dem Store verknüpfen

Wählen Sie im Menü Projekt in Visual Studio-Projektmappe "Store > zuordnen-App mit dem Store" aus. Wenn Sie dies tun, können Sie in Ihrer app Kauf-und Benachrichtigungsszenarien testen. Wenn Sie Ihre app mit dem Store zuordnen, werden diese Werte in die app-Manifestdatei für das aktuelle Projekt auf dem lokalen Computer heruntergeladen:
* Anzeigename des Pakets
* Paketname
* Herausgeber-ID
* Anzeigename des Herausgebers
* Version

Wenn Sie die Standarddatei "Package.appxmanifest" überschreiben, indem Sie eine benutzerdefinierte XML-Datei für das Manifest erstellen, können nicht Sie Ihre app mit dem Store zuordnen. Wenn Sie versuchen, eine benutzerdefinierte Manifestdatei mit dem Store verknüpfen, sehen Sie eine Fehlermeldung angezeigt.

### <a name="creating-an-upload-package"></a>Erstellen ein Paket zum Hochladen

Führen Sie die Richtlinien unter [Paketerstellung universelle Windows-apps für Windows 10](https://msdn.microsoft.com/library/hh454036.aspx#Anchor_2).

Im letzte Schritt erstellen Sie ein Paket zum Hochladen ist überprüft das Paket mit der [Windows App Certification Kit](#windows-app-certification-kit).

Wenn Sie ein Paket speziell für HoloLens zu einem vorhandenen Produkt, die für andere Windows 10-gerätefamilien verfügbar ist hinzufügen, sollten Sie auch Informationen [wie Versionsnummern welche Pakete auswirken werden für bestimmte Kunden übermittelt ](https://msdn.microsoft.com/library/windows/apps/mt188602.aspx), und [wie Pakete verteilt werden, um verschiedene Betriebssysteme](https://msdn.microsoft.com/library/windows/apps/mt188601.aspx).

Die grundsätzliche Empfehlung lautet, dass die höchste Anzahl Versionspaket, die auf einem Gerät gilt eine, die von der Store verteilt werden.

Wenn ein Windows.Universal-Paket und ein Windows.Holographic Paket vorhanden ist und das Paket Windows.Universal eine höhere Versionsnummer hat, wird ein HoloLens-Benutzer der höheren Anzahl Windows.Universal Versionspaket anstelle der Windows.Holographic herunterladen. das Paket. Es gibt mehrere Lösungen für dieses Problem:
1. Stellen Sie sicher Ihre Plattform bestimmte Pakete wie z. B. Windows.Holographic haben immer eine höhere Versionsnummer als Ihre Plattform betriebssystemagnostische Pakete wie z. B. Windows.Universal
2. Nicht über die Paket-apps als Windows.Universal führen Sie Wenn Plattform bestimmte Pakete - auch haben stattdessen das Windows.Universal-Paket für die jeweilige Plattform packen, verfügbar auf der gewünschten

>[!NOTE]
> Sie können ein einzelnes Paket mehrere Ziel-gerätefamilien für sein deklarieren.

3. Erstellen Sie ein einzelnes Windows.Universal-Paket, das auf allen Plattformen funktioniert. Unterstützung für dieses großartige ist zurzeit nicht damit die oben aufgeführten Lösungen zu empfehlen sind.

## <a name="testing-your-app"></a>Testen der app

### <a name="windows-app-certification-kit"></a>Zertifizierungskit für Windows-Apps

Bei der Erstellung von app-Pakete zum Einreichen beim Partner Center über Visual Studio fordert der Assistent für die App-Pakete erstellen Sie die Windows-Zertifizierungskit für Apps für die Pakete ausführen, die erstellt werden. Um eine reibungslose Übermittlungsprozess auf den Store zu haben, es wird empfohlen, zu überprüfen, ob die [testet Windows App Certification Kit](https://msdn.microsoft.com/library/windows/apps/jj657973.aspx) für Ihre app auf Ihrem lokalen Computer vor dem Einreichen der Store übergeben. Ausführen der Windows-Zertifizierungskit für Apps auf einem Remoteserver HoloLens wird derzeit nicht unterstützt.

### <a name="run-on-all-targeted-device-families"></a>Führen Sie auf allen entsprechenden gerätefamilien

Die universelle Windows-Plattform können Sie eine einzige Anwendung erstellen, die für alle von der Windows 10-gerätefamilien ausgeführt wird. Er garantiert jedoch nicht, dass nur universelle Windows-apps auf allen gerätefamilien funktioniert. Bevor Sie Ihre app HoloLens oder einer anderen Windows 10-Ziel Gerätefamilie zur Verfügung stellen möchten, ist es wichtig, die Sie [Testen der app](testing-your-app-on-hololens.md) auf allen diesen gerätefamilien, um sicherzustellen, dass eine gute Erfahrung.

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>Ihre mixed Reality-app auf den Store übermitteln

Wenn Sie eine mixed Reality-app, die in einem Unity-Projekt basiert übermitteln, finden Sie in diesem [video](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app) erste.

Im Allgemeinen ist ein senden eine Windows Mixed Reality-app, die für HoloLens und/oder immersive Headsets funktioniert genau wie alle UWP-app auf dem Microsoft Store übermitteln. Nachdem Sie haben [Ihre app erstellt, indem Sie ihren Namen reservieren](https://docs.microsoft.com/windows/uwp/publish/create-your-app-by-reserving-a-name), befolgen Sie die [Checkliste für die Übermittlung von UWP](https://docs.microsoft.com/windows/uwp/publish/app-submissions).

Einer der ersten Dinge, die Sie hierfür ist [wählen Sie eine Kategorie und Unterkategorie](https://docs.microsoft.com/windows/uwp/publish/category-and-subcategory-table) für Ihre mixed Reality-Umgebung. Es ist wichtig, die Sie **wählen Sie die genaueste Kategorie für Ihre app** , damit wir vermarkten Ihre Anwendung in den richtigen Store Kategorien und stellen Sie, es sicher mithilfe von Suchabfragen für relevante können. **Der Titel des VR auflisten, wie ein Spiel nicht besser Offenlegung für Ihre app führt** und kann verhindern, dass es in Kategorien, die weitere Anpassung sind und weniger hart umkämpften angezeigt.

Es gibt jedoch vier Hauptbereiche in der Übermittlungsprozess, in dem Sie mixed Reality-spezifischen Auswahl treffen sollten:
1. In der **[Produkt Deklarationen](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** unter Abschnitt [Eigenschaften](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties).
2. In der **[Systemanforderungen](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** unter Abschnitt [Eigenschaften](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties).
3. In der **[Familie geräteverfügbarkeit](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** unter Abschnitt [Pakete](https://docs.microsoft.com/windows/uwp/publish/upload-app-packages).
4. In einigen der der **[Store Angebotsseite](submitting-an-app-to-the-microsoft-store.md#store-listing-page)** Felder.

### <a name="mixed-reality-product-declarations"></a>Mixed Reality-Produkt-Deklarationen

Auf der **[Eigenschaften](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** Seite von der app-Übermittlungsprozess, finden Sie mehrere Optionen hinsichtlich Realität zu mixed Reality in die **[Produkt Deklarationen](https://docs.microsoft.com/windows/uwp/publish/app-declarations)** Abschnitt.

![Mixed Reality-Produkt-Deklarationen](images/product-declarations-900px.png)<br>
Mixed Reality-Produkt-Deklarationen

Zunächst sollten Sie die Gerätetypen zu identifizieren, für die Ihre app eine mixed Reality-Erfahrung bietet. Dadurch wird sichergestellt, dass Ihre app in Windows Mixed Reality-Auflistungen in den Store enthalten ist und dass es für Benutzer den Store durchsuchen, nach dem Herstellen einer Verbindung eine immersive Kopfhörer (oder beim Durchsuchen der Store für HoloLens) eingeblendet wird.

Neben "Diese Funktion ist für das Windows Mixed Reality auf:"
* Überprüfen Sie die **PC** Feld nur dann, wenn Ihre app eine VR-Erfahrung bietet, wenn eine immersive Kopfhörer mit Benutzer PCs verbunden ist. Sie sollten dieses Kontrollkästchen, ob es sich bei Ihrer app dient ausschließlich zur Ausführung in eine immersive Kopfhörer oder wenn es sich um eine standardmäßige PC-Spiel/app handelt, die ein mixed Reality-Modus bzw. Bonus Inhalte bietet, wenn Sie einen Kopfhörer angeschlossen ist.
* Überprüfen Sie die **HoloLens** Feld nur dann, wenn Ihre app eine holografischen Benutzeroberfläche bietet, wenn es auf HoloLens ausgeführt wird.
* Überprüfen Sie **sowohl** Kontrollkästchen, wenn Ihre app ein mixed Reality bietet experience auf beide Gerätetypen, wie z. B. die [Mixed Reality Academy "Projekt Insel" app](mixed-reality-250.md) ab Build 2017.

Wenn Sie "PC" oben ausgewählt haben, sollten Sie festzulegende "mixed Reality-Setup" (Aktivitätsstufe). Dies gilt nur, mixed Reality-Erlebnis, das auf PCs, die mit immersive Headsets, verbunden werden, da mixed Reality-apps für HoloLens weltweit einsetzbaren und der Benutzer keine Grenze während des Setups definieren ausgeführt.
* Wählen Sie **sitzen und ständigen** , wenn Ihre app mit der Absicht, die der Benutzer in eine Position entworfen wurde bleibt (ein Beispiel wäre ein Spiel, in dem sind Sie in ein Cockpit eines Flugzeugs sitzen).
* Wählen Sie **Ihren Erfahrungen** , wenn Ihre app mit der Absicht entworfen wurde, die der Benutzer innerhalb der Begrenzung des um führt er oder sie beim Setup definiert (ein Beispiel hierfür wäre eine Spiel Where für-Schritt-Seite und Duck Angriffe zu umgehen).

### <a name="mixed-reality-system-requirements"></a>Mixed Reality-Systemanforderungen

Auf der **[Eigenschaften](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties)** Seite von der app-Übermittlungsprozess, finden Sie mehrere Optionen hinsichtlich Realität zu mixed Reality in die **[Systemanforderungen](https://docs.microsoft.com/windows/uwp/publish/enter-app-properties#system-requirements)** Abschnitt.

![Systemanforderungen](images/system-reqs-800px.png)<br>
Systemanforderungen

In diesem Abschnitt werden Sie für Ihre mixed Reality-app (erforderlich) Hardware- und empfohlene (optional) Hardware identifizieren.

**Eingabe-Hardware:**

Mithilfe der Kontrollkästchen für potenziellen Kunden darüber zu informieren, wenn Ihre app unterstützt **Mikrofon** (für [voice-Eingabe](voice-input.md)), **[Xbox-Controller oder Gamepad](hardware-accessories.md#bluetooth-gamepads)**, und/oder  **[Windows Mixed Reality-Motion-Controller](motion-controllers.md)**. Diese Informationen werden in Ihrer app Produktdetailseite in den Store bereitgestellt werden und hilft Ihrer app, die in den entsprechenden app-Spiel eingeschlossen werden (z. B. eine Sammlung kann für alle Spiele, die während der Übertragung Controller unterstützen vorhanden).

Werden Sie zur Auswahl der Kontrollkästchen für "mindesthardwareanforderungen" oder "hardwareanforderungen" für Eingabetypen Bedacht. 

Zum Beispiel: 
* Wenn Ihr Spiel während der Übertragung Controller erfordert, jedoch Spracheingabe über das Mikrofon akzeptiert, wählen Sie "mindesthardwareanforderungen" Kontrollkästchen "Windows Mixed Reality-Motion-Controller", aber das Kontrollkästchen "hardwareanforderungen" neben "Mikrofon". 
* Wenn Ihr Spiel mit entweder ein Xbox-Controller/Gamepad Motion Controllern oder wiedergegeben werden kann, können Sie aktivieren Sie das Kontrollkästchen "mindesthardwareanforderungen" neben "Xbox-Controller oder Gamepad" und das Kontrollkästchen "hardwareanforderungen" neben "Windows Mixed Reality-Bewegung Controller"als Bewegung Controller werden wahrscheinlich eine Step-Up Erfahrung aus den Gamepad bieten.

**Immersive Windows Mixed Reality-Kopfhörer:**

Gibt an, ob eine immersive Kopfhörer erforderlich ist, um Ihre app verwenden, oder optional ist, ist entscheidend für Kundenzufriedenheit und -Schulung.

Wenn Ihre app kann *nur* , die über eine immersive Kopfhörer verwendet werden, aktivieren Sie das Kontrollkästchen "mindesthardwareanforderungen" neben "Windows Mixed Reality immersive Kopfhörer". Dies wird zugänglich gemacht werden auf Ihrer app Produktdetailseite im Store als Warnung über die Schaltfläche "kaufen", damit Kunden denken, dass sie eine app-Käufe sind, die auf ihren PC, wie eine herkömmliche desktop-app funktionieren.

Wenn Ihre app auf dem Desktop, wie eine herkömmliche PC-app ausgeführt, aber eine VR-Umgebung bietet, wenn eine immersive Kopfhörer verbunden ist (gibt an, ob der vollständige Inhalt der app verfügbar ist oder nur ein Teil), aktivieren Sie das Kontrollkästchen "hardwareanforderungen" neben "Windows Mixed Reality immersive Kopfhörer." Keine Warnung wird über die Schaltfläche "kaufen" in Ihrer app Produktdetailseite zugänglich gemacht werden, wenn die Funktionen Ihrer app als eine herkömmliche desktop-app ohne eine immersive Kopfhörer angeschlossen.

**PC-Spezifikationen:**

Wenn Sie Ihre app so viele Windows Mixed Reality immersive Kopfhörer Benutzer wie möglich zu erreichen möchten, sollten Sie zum [Ziel](understanding-performance-for-mixed-reality.md) die PC-Spezifikationen für [Windows Mixed Reality-PCs mit integrierter Grafikkarte](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

Gibt an, ob Ihre mixed Reality-app ist die Mindestanforderungen von Windows Mixed Reality-PC oder eine bestimmte PC-Konfiguration erfordert (wie die dedizierte GPU des eine [Windows Mixed Reality Ultra-PC](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), sollte Sie angeben, dass mit der entsprechenden In der Spalte "mindesthardwareanforderungen" PC-Spezifikationen.

Wenn Ihre mixed Reality-app ausgelegt ist, bieten eine bessere Leistung und bieten Grafiken mit höherer Auflösung, auf einem bestimmten PC-Konfiguration oder Grafikkarte verfügt, sollten Sie, die mit den relevanten Spezifikationen der PC in der Spalte "Empfohlene Hardware" angeben.

Dies gilt nur, wenn in Ihrer mixed Reality-app eine immersive Kopfhörer, die Verbindung mit einem PC verwendet. Wenn Ihrer mixed Reality-app nur auf HoloLens ausgeführt wird, müssen Sie nicht PC-Spezifikationen anzugeben, wie HoloLens nur eine Hardwarekonfiguration aufweist.

### <a name="device-family-availability"></a>Verfügbarkeit von Gerätefamilien

Wenn Sie haben [Ihrer-app ordnungsgemäß gepackt](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) in Visual Studio auf der Seite "Pakete" von der app-Übermittlungsprozess hochladen sollte eine Tabelle erstellen möchten, identifiziert die gerätefamilien, die Ihre Anwendung zur Verfügung kann.

![Familie Verfügbarkeit Gerätetabelle](images/device-family-table-900px.png)<br>
Familie Verfügbarkeit Gerätetabelle

Wenn Ihre mixed Reality-app für immersive Headsets aus, und klicken Sie dann auf funktioniert, muss mindestens "Windows 10-Desktop" in der Tabelle ausgewählt werden. Wenn Ihre mixed Reality-app funktioniert, HoloLens, und klicken Sie dann auf sollte mindestens "Windows 10 Holographic" ausgewählt werden. Wenn Ihre app bei beiden Windows Mixed Reality Kopfhörer ausgeführt wird, wie die [Mixed Reality Academy "Projekt Insel" app](mixed-reality-250.md), "Windows 10 Desktop" und "Windows 10 Holographic" ausgewählt werden sollen.

>[!TIP]
>Viele Entwickler wird Fehler auftreten, wenn Sie ihr app Paket, die im Zusammenhang mit der Konflikte zwischen der Paketmanifestdatei und Ihre app-Herausgeber-Kontoinformationen im Partner Center hochladen. Diese Fehler können häufig durch Anmelden bei Visual Studio, mit dem gleichen Konto verknüpft ist, mit dem Windows-Entwicklerkonto (diejenige, die Sie zum Anmelden verwenden, in Partner Center) vermieden werden. Wenn Sie das gleiche Konto verwenden, müssen Sie möglicherweise seine Identität in der Microsoft Store-Ihrer-app zuordnen, bevor Sie ihn verpacken.

![Ihre app mit dem Microsoft Store verknüpfen](images/associate-your-app-700px.png)<br>
Verknüpfen Sie Ihre app mit dem Microsoft Store in Visual Studio

### <a name="store-listing-page"></a>Store-Angebotsseite

Auf der [Store auflisten](https://docs.microsoft.com/windows/uwp/publish/create-app-store-listings) auf der Seite der app-Übermittlung zu verarbeiten, es gibt mehrere Bereiche können Sie nützliche Informationen zu Ihrer mixed Reality-app hinzufügen.

>[!IMPORTANT]
>Um sicherzustellen, dass Ihre app ordnungsgemäß kategorisiert nach den Store und Windows Mixed Reality-Kunden erkennbar gemacht, sollten Sie die hinzufügen **"Windows Mixed Reality"** als eine der "Suchbegriffe" für die app (finden Sie Suchbegriffe durch Erweitern "Freigegebene Felder" Abschnitt).

![Hinzufügen von Windows Mixed Reality um Begriffe zu suchen.](images/search-terms-800px.png)<br>
Fügen Sie "Windows Mixed Reality" um Begriffe zu suchen.

## <a name="offering-a-free-trial-for-your-game-or-app"></a>Bietet eine kostenlose Testversion für Ihre Spiele und Apps

Viele Kunden werden bis keine Erfahrung mit virtuelle Realität vor dem Kauf einer immersive Windows Mixed Reality-Kopfhörer begrenzt sein. Sie wissen möglicherweise nicht, was Sie erwartet, von Intensives Spiele und möglicherweise nicht vertraut sind, mit ihren eigenen Schwellenwert bequem in faszinierende Benutzeroberflächen. Viele Kunden können auch versuchen, eine immersive Windows Mixed Reality-Kopfhörer auf PCs, die als mit sind nicht [Windows Mixed Reality-PCs](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines). Aufgrund dieser Überlegungen, es wird dringend empfohlen Angebot empfiehlt eine [kostenlose Testversion](https://docs.microsoft.com/windows/uwp/publish/set-app-pricing-and-availability#free-trial) für Ihre kostenpflichtigen mixed Reality-app oder ein Spiel.

## <a name="see-also"></a>Siehe auch
* [Mixed Reality](mixed-reality.md)
* [Übersicht über die Entwicklung](development-overview.md)
* [App-Ansichten](app-views.md)
* [Grundlegendes zur Leistung für Mixed Reality](understanding-performance-for-mixed-reality.md)
* [Empfehlungen zur Leistung für Unity](performance-recommendations-for-unity.md)
* [Testen Ihrer app für HoloLens](testing-your-app-on-hololens.md)
* [Windows Mixed Reality minimale PC Kompatibilität an die hardwareempfehlungen](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
