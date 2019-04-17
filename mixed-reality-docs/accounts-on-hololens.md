---
title: Konten in HoloLens
description: Informationen zum Einrichten und Verwalten von Benutzerkonten für HoloLens.
author: ''
ms.author: toddly
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Benutzer, Konto, Aad, Adfs, Microsoft-Konto, Msa, Anmeldeinformationen
ms.openlocfilehash: 14f43b08b6ccb396bcf39c4082c840c65ac78cf9
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/12/2019
ms.locfileid: "59594157"
---
# <a name="accounts-on-hololens"></a>Konten in HoloLens

Während des anfangssetups, HoloLens müssen Benutzer sich anmelden, die sie auf dem Gerät verwenden möchten. Ein Consumer-Microsoft-Konto oder ein Enterprise-Konto an, die in Azure Active Directory (AAD) oder Active Directory Federation Services (ADFS) konfiguriert wurde, kann dieses Konto sein.

Anmelden bei diesem Konto während des Setups erstellt ein Benutzerprofil auf dem Gerät die der Benutzer, um verwenden können Anmelde-, und für welche apps alle ihre Daten gespeichert werden. Dieses Konto bietet auch einmaliges Anmelden für apps wie Microsoft Edge oder Skype über die Windows-Konto-Manager-APIs.

Darüber hinaus kann beim Anmelden bei einem Unternehmen oder Organisations-Konto auf dem Gerät sie auch Richtlinien (Mobile Device Management, MDM) gelten, wenn von Ihrem IT-Administrator konfiguriert

Wenn das Gerät wird neu gestartet oder fortgesetzt, aus dem Standbymodus wird, werden die Anmeldeinformationen für dieses Konto verwendet, sich erneut anmelden. Wenn die Option, die eine explizite Anmeldung erzwingen, die in den Einstellungen aktiviert ist, die Benutzer müssen ihre Anmeldeinformationen erneut eingeben. Jedes Mal, wenn das Gerät neu gestartet wird, nach dem empfangen und ein Betriebssystemupdate anwenden, ist eine explizite Anmeldung erforderlich.

## <a name="multi-user-support"></a>Unterstützung für mehrere Benutzer

>[!NOTE]
>Unterstützung für mehrere Benutzer benötigt die Commercial Suite, da dies eine [Windows Holographic for Business](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise) Feature.

Beginnend mit der [Windows 10 April 2018 Update](release-notes-april-2018.md), HoloLens unterstützt mehrere Benutzer im gleichen AAD-Mandanten. Verwendung dieses müssen Sie das Gerät zunächst mit einem Konto einrichten, die in Ihrer Organisation gehört. Anschließend werden andere Benutzer aus dem gleichen Mandanten können sich auf dem Gerät aus dem Anmeldebildschirm oder durch Tippen auf die Benutzerkachel "auf das Bedienfeld" Start "zum Abmelden des vorhandenen Benutzers. 

Auf dem Gerät installierten Apps werden alle anderen Benutzern zur Verfügung, aber jede hat ihre eigenen app-Daten und Einstellungen. Entfernen einer app wird auch für alle anderen Benutzer jedoch entfernt. 

Sie können Benutzer von Geräten entfernen, von dem Gerät, Speicherplatz freizugeben, indem Sie auf Einstellungen > Konten > andere Personen. Dies auch entfernt all die anderen Benutzer app-Daten vom Gerät. 

## <a name="linked-accounts"></a>Verknüpfte Konten

In einem einzelnen Gerät-Konto können Benutzer zusätzliche Web-Kontoanmeldeinformationen für den einfacheren Zugriff innerhalb von apps (z. B. die Store) verknüpfen oder den Zugriff auf persönliche und geschäftliche Ressourcen, ähnlich wie die Desktopversion von Windows zu kombinieren. Auf diese Weise ein weiteres Konto anmelden, trennt die Daten auf dem Gerät, z. B. Bilder erstellt nicht oder downloads. Apps können vornehmen, nachdem ein Konto mit einem Gerät verbunden ist, verwenden mit Ihrer Erlaubnis, um zu reduzieren, melden Sie sich bei jeder app einzeln müssen.

## <a name="using-single-sign-on-within-an-app"></a>Verwenden von SSO in einer app

Als app-Entwickler, profitieren Sie von müssen ein verbundenes Identitäts für HoloLens, mit der [Windows-Konto-Manager-APIs](https://msdn.microsoft.com/library/windows/apps/xaml/windows.security.authentication.web.core.aspx)genau wie für andere Windows-Geräte verwenden. Einige Codebeispiele für diese APIs stehen [hier](http://go.microsoft.com/fwlink/p/?LinkId=620621).

Konto-Interrupts, die auftreten können, z. B. anfordernden Benutzers zustimmen Kontoinformationen, zweistufige Authentifizierung usw. muss verarbeitet werden, wenn die app einen Authentifizierungstoken anfordert.

Wenn Ihre app ein bestimmtes Konto, die zuvor noch nicht verknüpft wurden benötigt, kann Ihrer app das System fordert den Benutzer auf eine hinzufügen lassen. Dadurch wird der Bereich "abfrageeinstellungen Konto" als untergeordnetes modales Ihrer-App gestartet wird ausgelöst. Direct2D-apps in diesem Fenster wird gerendert, direkt über dem Mittelpunkt, die Ihrer App und für Unity-apps, kurz gelangen die Benutzer Ihrer app holographic, damit diesem untergeordneten Fenster gerendert werden kann. Anpassen von Befehlen und Aktionen in diesem Bereich finden Sie [hier](https://msdn.microsoft.com/library/windows/apps/windows.ui.applicationsettings.webaccountcommand.aspx).

## <a name="enterprise-and-other-authentication"></a>Unternehmen und andere Authentifizierung

Wenn Ihre app stellt andere Arten von Authentifizierung verwenden, z. B. NTLM, Basic oder Kerberos, können Sie [UI für Windows-Anmeldeinformationen](https://msdn.microsoft.com/library/windows/apps/windows.security.credentials.ui.aspx) um erfassen, verarbeiten und speichern Sie die Anmeldeinformationen des Benutzers. Die benutzererfahrung für das Sammeln von diese Anmeldeinformationen ähnelt anderen Konto Interrupts für cloudbasierte und erscheinen als untergeordnete app zusätzlich zu Ihrem Direct2D-app oder kurz anhalten eine Unity-app, um die Benutzeroberfläche anzuzeigen.

## <a name="deprecated-apis"></a>Nicht mehr unterstützte APIs

Ein Unterschied für die Entwicklung für HoloLens Desktop besteht darin, die [OnlineIDAuthenticator](https://msdn.microsoft.com/library/windows/apps/windows.security.authentication.onlineid.onlineidauthenticator.aspx) API wird nicht vollständig unterstützt. Zwar wird, dass ein Token zurückgegeben ist das primäre Konto in gut stehende, unterbricht, z. B. den oben genannten keine Benutzeroberfläche für den Benutzer anzeigt werden und nicht das Konto ordnungsgemäß zu authentifizieren.

