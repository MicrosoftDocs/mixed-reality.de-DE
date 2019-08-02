---
title: Einrichten einer sicheren Verbindung mit Holographic Remoting
description: Auf dieser Seite wird erläutert, wie Sie eine sichere verschlüsselte Verbindung herstellen, wenn Sie Holographic Remoting verwenden.
author: bethau
ms.author: bethau
ms.date: 08/01/2019
ms.topic: article
keywords: Hololens, Remoting, Holographic Remoting
ms.openlocfilehash: 5bc039d7a1e500f577c4a30d2d082b718a45a8b4
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718074"
---
# <a name="establishing-a-secure-connection-with-holographic-remoting"></a>Einrichten einer sicheren Verbindung mit Holographic Remoting

>[!IMPORTANT]
>Diese Anleitung gilt speziell für Holographic-Remoting auf hololens 2.

Auf dieser Seite wird erläutert, wie Sie eine sichere verschlüsselte Verbindung herstellen, wenn Sie Holographic Remoting verwenden.

Beim Streamen von Inhalten auf hololens 2 über ein unsicheres Netzwerk, wie z. b. ein offenes WiFi oder das Internet, wird dringend empfohlen, eine verschlüsselte Verbindung zu verwenden.

>[!IMPORTANT]
>Auch wenn eine vertrauenswürdige lokale WLAN-Verbindung verwendet wird, sollte eine verschlüsselte Verbindung berücksichtigt werden.

Um eine verschlüsselte Verbindung verwenden zu können, müssen Sie sowohl einen [benutzerdefinierten Player](holographic-remoting-create-player.md) als auch eine [Benutzerdefinierte Host-App](holographic-remoting-create-host.md)implementieren.

Die Verschlüsselung wird mithilfe der zugrunde liegenden Platt Form-TLS-Implementierung erreicht.

## <a name="basics-of-an-encrypted-connection"></a>Grundlagen einer verschlüsselten Verbindung

Die folgenden Objekte müssen implementiert werden, um einen Zertifikat Austausch zuzulassen.

>[!TIP]
>Das Implementieren von WinRT-Schnittstellen kann C++mithilfe von/WinRT. problemlos erfolgen. Im Kapitel " [Autoren C++-APIs mit/WinRT](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/author-apis) " wird dies ausführlich beschrieben.

>[!IMPORTANT]
>Der ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` im nuget-Paket enthält eine ausführliche Dokumentation für die API, die sich auf sichere Verbindungen bezieht.

1) Ein Zertifikat Objekt, das die ```ICertificate``` -Schnittstelle implementieren muss.

    * Gibt den binären Inhalt des PFX-Zertifikats über die ```GetCertificatePfx``` -Methode zurück. Identisch mit dem binären Inhalt einer PFX-Datei.
    * Geben Sie den Namen des Zertifikat ```GetSubjectName```Antragstellers durch zurück.
    * Geben Sie das PFX- ```GetPfxPassword```Kennwort durch zurück. Gibt eine leere Zeichenfolge für ein ungeschütztes PFX zurück.

2) Ein Zertifikat Anbieter, der ```ICertificateProvider``` die-Schnittstelle implementiert, die ein Zertifikat ```GetCertificate``` bereitstellt, wenn Sie über die-Methode

3) Ein zertifikatvalidator, ```ICertificateValidator``` der die-Schnittstelle implementiert Seine Aufgabe besteht darin, eingehende Zertifikate zu überprüfen.
    * Die ```PerformSystemValidation``` -Methode sollte ```true``` zurückgeben, wenn die zugrunde liegende Plattform die eingehende ```false``` Zertifikatskette überprüfen soll, andernfalls.
    * ```ValidateCertificate```wird vom Client Kontext aufgerufen, um die Validierung eines Zertifikats anzufordern. Diese Methode akzeptiert die Zertifikat Kette (mit dem ersten Zertifikat, das das Zertifikat des Antragstellers ist), den Namen des Servers, mit dem die Verbindung hergestellt wird, und gibt an, ob eine Sperr Überprüfung erzwungen werden soll. Das Ergebnis der Systemvalidierung wird bereitgestellt, wenn die Validierung durch das zugrunde liegende System angefordert wurde. Um die Verarbeitung entweder ```CertificateValidated``` mit dem entsprechenden Ergebnis fort ```Cancel``` zusetzen oder die Validierung abzubrechen, muss für die ```ICertificateValidationCallback```übergebenen aufgerufen werden.

Außerdem müssen die folgenden Objekte implementiert werden, um den Austausch eines sicheren Tokens zuzulassen.

1) Ein Authentifizierungs Anbieter, der ```IAuthenticationProvider``` die-Schnittstelle implementiert. Die zugehörige-Methode wird vom Client Kontext aufgerufen, um ein Token für die Client Authentifizierung anzufordern. ```GetToken``` Um weiterhin ```TokenReceived``` das Authentifizierungs Token bereitzustellen und den Verbindungsprozess fortzusetzen oder ```Cancel``` abzubrechen, muss der Prozess für die übergebenen ```IAuthenticationProviderCallback```aufgerufen werden.
2) Ein Authentifizierungs Empfänger, der ```IAuthenticationReceiver``` die-Schnittstelle implementiert. Seine Aufgabe besteht darin, eingehende Token zu validieren.
    * Die ```GetRealm``` Methode sollte den Namen des Authentifizierungs Bereichs zurückgeben.
    * Die ```ValidateToken``` -Methode wird vom Server-Netzwerk Kontext aufgerufen, um die Validierung eines Client Authentifizierungs Tokens anzufordern. Um den Vorgang fort ```ValidationCompleted``` zusetzen, wird entweder aufgerufen, um ```Cancel``` den Abschluss der Validierung zu signalisieren oder die Client Verbindung abzulehnen. Die Client Verbindung wird basierend auf dem an ```ValidationCompleted```übergebenen Validierungs Ergebnis zugelassen oder abgelehnt. 

Nachdem ```ListenSecure``` diese Objekte implementiert wurden, muss anstelle von ```Listen``` und ```ConnectSecure``` anstelle von ```Connect``` für den Remote Kontext bzw. den Player Kontext aufgerufen werden. ```ListenSecure```erfordert einen zusätzlichen Zertifikat Anbieter und Authentifizierungs Empfänger über ```Listen```. ```ConnectSecure```erfordert einen zusätzlichen Authentifizierungs Anbieter und ein zertifikatvalidator ```Connect```.

## <a name="see-also"></a>Siehe auch
* [Schreiben einer Holographic Remoting-Host-App](holographic-remoting-create-host.md)
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](holographic-remoting-create-player.md)
* [Problembehandlung und Einschränkungen für Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Software Lizenzbedingungen für Holographic Remoting](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzbestimmungen von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)