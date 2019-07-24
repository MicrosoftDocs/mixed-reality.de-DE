---
title: Konten in hololens
description: Einrichten und Verwalten von Benutzerkonten auf hololens.
author: ''
ms.author: toddly
ms.date: 03/21/2018
ms.topic: article
keywords: Hololens, Benutzer, Konto, AAD, ADFS, Microsoft-Konto, MSA, Anmelde Informationen
ms.openlocfilehash: 14f43b08b6ccb396bcf39c4082c840c65ac78cf9
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516814"
---
# <a name="accounts-on-hololens"></a>Konten in hololens

Bei der anfänglichen Einrichtung von hololens müssen sich Benutzer mit dem Konto anmelden, das Sie auf dem Gerät verwenden möchten. Bei diesem Konto kann es sich entweder um einen Consumer-Microsoft-Konto oder um ein Enterprise-Konto handeln, das in Azure Active Directory (AAD) oder Active Directory-Verbunddienste (AD FS) (ADFS) konfiguriert wurde.

Bei der Anmeldung bei diesem Konto während des Setups wird ein Benutzerprofil auf dem Gerät erstellt, mit dem der Benutzer sich anmelden kann und für das alle apps Ihre Daten speichern. Dieses Konto bietet auch das einmalige Anmelden für apps wie z. b. Edge oder Skype über die Windows-Konto-Manager-APIs.

Wenn Sie sich bei einem Unternehmens-oder Unternehmens Konto auf dem Gerät anmelden, können Sie darüber hinaus auch die Richtlinie für die Verwaltung mobiler Geräte (MDM) anwenden, wenn Sie von Ihrem IT-Administrator konfiguriert wurde.

Wenn das Gerät neu gestartet oder aus dem Standbymodus wieder aufgenommen wird, werden die Anmelde Informationen für dieses Konto verwendet, um sich erneut anzumelden. Wenn die Option zum Erzwingen einer expliziten Anmeldung in den Einstellungen aktiviert ist, muss der Benutzer die Anmelde Informationen erneut eingeben. Jedes Mal, wenn das Gerät nach dem Empfang und der Anwendung eines Betriebssystemupdates neu gestartet wird, ist eine explizite Anmeldung erforderlich.

## <a name="multi-user-support"></a>Unterstützung für mehrere Benutzer

>[!NOTE]
>Die Unterstützung für mehrere Benutzer erfordert die kommerzielle Suite, da es sich hierbei um ein [Windows Holographic for Business](https://docs.microsoft.com/hololens/hololens-upgrade-enterprise) -Feature handelt.

Ab dem [Windows 10-Update vom April 2018](release-notes-april-2018.md)unterstützt hololens mehrere Benutzer innerhalb desselben Aad-Mandanten. Um dies zu verwenden, müssen Sie das Gerät anfänglich mit einem Konto einrichten, das zu Ihrer Organisation gehört. Anschließend können sich andere Benutzer desselben Mandanten über den Anmeldebildschirm beim Gerät anmelden oder indem Sie im Start Bereich auf die Benutzer Kachel tippen, um den vorhandenen Benutzer zu melden. 

Apps, die auf dem Gerät installiert sind, stehen allen anderen Benutzern zur Verfügung, Sie verfügen jedoch über eigene APP-Daten und-Einstellungen. Wenn Sie eine APP entfernen, wird Sie auch für alle anderen Benutzer entfernt. 

Sie können Gerätebenutzer vom Gerät entfernen, um Speicherplatz freizugeben, indem Sie zu Einstellungen > Konten > anderen Personen wechseln. Dadurch werden auch alle App-Daten anderer Benutzer vom Gerät entfernt. 

## <a name="linked-accounts"></a>Verknüpfte Konten

Innerhalb eines einzelnen Geräte Kontos können Benutzer zusätzliche Webkonto-Anmelde Informationen für den einfacheren Zugriff innerhalb von apps (z. b. den Store) oder für die Kombination des Zugriffs auf persönliche und geschäftliche Ressourcen, ähnlich der Desktop Version von Windows, verknüpfen. Wenn Sie sich auf diese Weise bei einem zusätzlichen Konto anmelden, werden die auf dem Gerät erstellten Benutzerdaten, z. b. Bilder oder Downloads, nicht getrennt. Sobald ein Konto mit einem Gerät verbunden ist, kann es von apps verwendet werden, um die Anmeldung bei jeder APP zu verringern.

## <a name="using-single-sign-on-within-an-app"></a>Verwenden des einmaligen Anmeldens innerhalb einer APP

Als App-Entwickler können Sie die Vorteile einer verbundenen Identität auf hololens mit den [Windows-Konto-Manager-APIs](https://msdn.microsoft.com/library/windows/apps/xaml/windows.security.authentication.web.core.aspx)nutzen, genauso wie auf anderen Windows-Geräten. Einige Codebeispiele für diese APIs sind [hier](http://go.microsoft.com/fwlink/p/?LinkId=620621)verfügbar.

Alle Konto Unterbrechungen, die möglicherweise auftreten, z. b. das Anfordern der Zustimmung von Benutzern für Kontoinformationen, die zweistufige Authentifizierung usw., müssen behandelt werden, wenn die APP ein Authentifizierungs Token anfordert.

Wenn Ihre APP einen bestimmten Kontotyp erfordert, der zuvor noch nicht verknüpft war, kann Ihre APP das System auffordern, den Benutzer zur Eingabe aufzufordern. Dadurch wird der Bereich "Kontoeinstellungen" als modales untergeordnetes Element der APP gestartet. Für 2D-apps wird dieses Fenster direkt über den Mittelpunkt Ihrer APP und für Unity-apps gerendert. Dadurch wird der Benutzer kurz aus der Holographic-App herausgenommen, sodass dieses untergeordnete Fenster gerendert werden kann. Das Anpassen der Befehle und Aktionen in diesem Bereich wird [hier](https://msdn.microsoft.com/library/windows/apps/windows.ui.applicationsettings.webaccountcommand.aspx)beschrieben.

## <a name="enterprise-and-other-authentication"></a>Enterprise und andere Authentifizierung

Wenn Ihre APP andere Arten der Authentifizierung verwendet (z. b. NTLM, Basic oder Kerberos), können Sie die Benutzer [Oberfläche von Windows](https://msdn.microsoft.com/library/windows/apps/windows.security.credentials.ui.aspx) -Anmelde Informationen verwenden, um die Anmelde Informationen des Benutzers zu erfassen, zu verarbeiten und zu speichern. Die Benutzeroberfläche für die Erfassung dieser Anmelde Informationen ähnelt anderen cloudgestützten Konto Interrupts und wird als untergeordnete App auf der 2D-App angezeigt, oder es wird eine Unity-App kurz angehalten, um die Benutzeroberfläche anzuzeigen.

## <a name="deprecated-apis"></a>Veraltete APIs

Ein Unterschied bei der Entwicklung von hololens vom Desktop ist, dass die [onlineidauthenticator](https://msdn.microsoft.com/library/windows/apps/windows.security.authentication.onlineid.onlineidauthenticator.aspx) -API nicht vollständig unterstützt wird. Obwohl ein Token zurückgegeben wird, wenn sich das primäre Konto in einem guten Zustand befindet, werden Unterbrechungen, wie z. b. die oben beschriebenen, keine Benutzeroberfläche für den Benutzer anzeigen und das Konto nicht ordnungsgemäß authentifizieren.

