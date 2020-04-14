---
title: Einrichten einer sicheren Verbindung mit Holographic Remoting
description: Auf dieser Seite wird erläutert, wie Sie eine sichere verschlüsselte Verbindung herstellen, wenn Sie Holographic Remoting verwenden.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Hololens, Remoting, Holographic Remoting
ms.openlocfilehash: 4006a317ed2ecfd7a1e67336a80a4e536d45e554
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278228"
---
# <a name="establishing-a-secure-connection-with-holographic-remoting"></a>Einrichten einer sicheren Verbindung mit Holographic Remoting

>[!IMPORTANT]
>Diese Anleitung gilt speziell für Holographic-Remoting auf hololens 2.

Auf dieser Seite wird erläutert, wie Sie eine sichere verschlüsselte Verbindung herstellen, wenn Sie Holographic Remoting verwenden.

Beim Streamen von Inhalten auf hololens 2 über ein unsicheres Netzwerk, wie z. b. ein offenes WiFi oder das Internet, wird dringend empfohlen, eine verschlüsselte Verbindung zu verwenden.

>[!IMPORTANT]
>Auch wenn eine vertrauenswürdige lokale WLAN-Verbindung verwendet wird, sollte eine verschlüsselte Verbindung berücksichtigt werden.

Um eine verschlüsselte Verbindung verwenden zu können, müssen Sie sowohl einen [benutzerdefinierten Player](holographic-remoting-create-player.md) als auch eine [benutzerdefinierte Remote-app](holographic-remoting-create-host.md)implementieren.

Die Verschlüsselung wird mithilfe der zugrunde liegenden Platt Form-TLS-Implementierung erreicht.

## <a name="basics-of-an-encrypted-connection"></a>Grundlagen einer verschlüsselten Verbindung

Die folgenden Objekte müssen implementiert werden, um einen Zertifikat Austausch zuzulassen.

>[!TIP]
>Das Implementieren von WinRT-Schnittstellen kann C++mithilfe von/WinRT. problemlos erfolgen. Im Kapitel " [Autoren C++-APIs mit/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) " wird dies ausführlich beschrieben.

>[!IMPORTANT]
>Der ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` im nuget-Paket enthält eine ausführliche Dokumentation für die API, die sich auf sichere Verbindungen bezieht.

1) Ein Zertifikat Objekt, das die ```ICertificate```-Schnittstelle implementieren muss.

    * Gibt den binären Inhalt des PFX-Zertifikats über die ```GetCertificatePfx```-Methode zurück. Identisch mit dem binären Inhalt einer PFX-Datei.
    * Gibt den Namen des Zertifikat Antragstellers über ```GetSubjectName```zurück.
    * Geben Sie das PFX-Kennwort über ```GetPfxPassword```zurück. Gibt eine leere Zeichenfolge für ein ungeschütztes PFX zurück.

2) Ein Zertifikat Anbieter, der die ```ICertificateProvider```-Schnittstelle implementiert, die ein Zertifikat bereitstellt, wenn die ```GetCertificate```-Methode angefordert wird

3) Ein zertifikatvalidator, das die ```ICertificateValidator```-Schnittstelle implementiert. Seine Aufgabe besteht darin, eingehende Zertifikate zu überprüfen.
    * Die ```PerformSystemValidation```-Methode sollte ```true``` zurückgeben, wenn die zugrunde liegende Plattform die eingehende Zertifikatskette überprüfen soll, andernfalls ```false```.
    * ```ValidateCertificate``` wird vom Client Kontext aufgerufen, um die Validierung eines Zertifikats anzufordern. Diese Methode akzeptiert die Zertifikat Kette (mit dem ersten Zertifikat, das das Zertifikat des Antragstellers ist), den Namen des Servers, mit dem die Verbindung hergestellt wird, und gibt an, ob eine Sperr Überprüfung erzwungen werden soll. Das Ergebnis der Systemvalidierung wird bereitgestellt, wenn die Validierung durch das zugrunde liegende System angefordert wurde. Um die Verarbeitung von ```CertificateValidated``` mit dem entsprechenden Ergebnis fortzusetzen, oder ```Cancel```, um die Validierung abzubrechen, muss für die übergebenen ```ICertificateValidationCallback```aufgerufen werden.

Außerdem müssen die folgenden Objekte implementiert werden, um den Austausch eines sicheren Tokens zuzulassen.

1) Ein Authentifizierungs Anbieter, der die ```IAuthenticationProvider```-Schnittstelle implementiert. Die ```GetToken```-Methode wird vom Client Kontext aufgerufen, um ein Token für die Client Authentifizierung anzufordern. Um den Vorgang fortzusetzen ```TokenReceived```, um das Authentifizierungs Token bereitzustellen und den Verbindungsprozess fortzusetzen, oder ```Cancel```, um den Vorgang abzubrechen, muss für die übergebenen ```IAuthenticationProviderCallback```aufgerufen werden.
2) Ein Authentifizierungs Empfänger, der die ```IAuthenticationReceiver```-Schnittstelle implementiert. Seine Aufgabe besteht darin, eingehende Token zu validieren.
    * Die ```GetRealm```-Methode sollte den Namen des Authentifizierungs Bereichs zurückgeben.
    * Die ```ValidateToken```-Methode wird vom Server-Netzwerk Kontext aufgerufen, um die Validierung eines Client Authentifizierungs Tokens anzufordern. Um den Vorgang fortzusetzen, führen Sie ```ValidationCompleted``` aus, um den Abschluss der Validierung zu signalisieren, oder ```Cancel```, um die Client Verbindung abzulehnen. Die Client Verbindung wird basierend auf dem an ```ValidationCompleted```übergebenen Validierungs Ergebnis zugelassen oder abgelehnt. 

Nachdem diese Objekte implementiert wurden ```ListenSecure``` muss anstelle von ```Listen``` und ```ConnectSecure``` anstelle der ```Connect``` im Remote Kontext und im Player Kontext aufgerufen werden. ```ListenSecure``` erfordert einen zusätzlichen Zertifikat Anbieter und Authentifizierungs Empfänger über ```Listen```. ```ConnectSecure``` erfordert einen zusätzlichen Authentifizierungs Anbieter und ein zertifikatvalidator über ```Connect```.

## <a name="see-also"></a>Weitere Informationen
* [Schreiben einer Holographic Remoting-Remote-app](holographic-remoting-create-host.md)
* [Schreiben einer benutzerdefinierten Holographic Remoting Player-App](holographic-remoting-create-player.md)
* [Problembehandlung und Einschränkungen für Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Holographic Remoting-Software – Lizenzbedingungen](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Datenschutzbestimmungen von Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
