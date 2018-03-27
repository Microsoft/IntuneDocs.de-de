---
title: Blockieren von Apps ohne moderne Authentifizierung
description: ''
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 10/15/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 098b652c-01e0-45d1-a731-620b0d3dc7c1
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: a8e9ec3d5a8aaea266dff8be8c1c71ad19e74d2b
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>Blockieren von Apps, die keine moderne Authentifizierung verwenden (ADAL)

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Der App-bedingte Zugriff für mit App-Schutzrichtlinien hängt von Anwendungen ab, die die [moderne Authentifizierung](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) nutzen, bei der es sich um eine Implementierung von OAuth2 handelt. Die meisten mobilen Office-Anwendungen und Office-Anwendungen für den Desktop nutzen die moderne Authentifizierung. Es gibt jedoch Apps von Drittanbietern oder ältere Office-Apps, die andere Authentifizierungsmethoden wie die Standardauthentifizierung und die formularbasierte Authentifizierung nutzen.

Zum Blockieren dieser Apps wird Folgendes empfohlen:

* Richten Sie die Anspruchsregeln für Active Directory-Verbunddienste (ADFS) dahingehend ein, dass nicht moderne Authentifizierungsprotokolle blockiert werden. Detaillierte Anleitungen werden in Szenario 3 beschrieben: [Blockieren des gesamten Zugriffs auf Office 365, bis auf browserbasierte Anwendungen](https://technet.microsoft.com/library/dn592182.aspx).
* Für **SharePoint Online** deaktivieren Sie die Verwendung nicht moderner Authentifizierungsmethoden im SharePoint Online-Dienst. Verwenden Sie das PowerShell-Cmdlet [Set-SPOTenant](https://technet.microsoft.com/library/fp161390.aspx), um die Eigenschaft für ältere Authentifizierungsprotokolle auf „False“ festzulegen:

```
 Set-SPOTenant -LegacyAuthProtocolsEnabled $false

```


>[!IMPORTANT]
>App-basierte CA darf nicht mit der zertifikatbasierten Authentifizierung von Azure Active Directory (Azure AD) verwendet werden. Es darf immer jeweils nur eine Authentifizierungsmethode konfiguriert werden.

### <a name="see-also"></a>Weitere Informationen:
[Nur von Intune unterstützten Apps den Zugriff auf O365-Dienste erlauben](allow-policy-managed-apps-access-to-o365.md)
