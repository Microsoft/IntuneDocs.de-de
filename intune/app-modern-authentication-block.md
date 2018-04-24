---
title: Blockieren von Apps ohne moderne Authentifizierung in Intune
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie Apps blockieren können, die keine moderne Authentifizierung verwenden (ADAL).
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 796e64d40ce111edccf6cd6a6e97f1cadf2443e5
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>Blockieren von Apps, die keine moderne Authentifizierung verwenden (ADAL)

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Der App-bedingte Zugriff für mit App-Schutzrichtlinien hängt von Anwendungen ab, die die [moderne Authentifizierung](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) nutzen, bei der es sich um eine Implementierung von OAuth2 handelt. Die meisten mobilen Office-Anwendungen und Office-Anwendungen für den Desktop nutzen die moderne Authentifizierung. Es gibt jedoch Apps von Drittanbietern oder ältere Office-Apps, die andere Authentifizierungsmethoden wie die Standardauthentifizierung und die formularbasierte Authentifizierung nutzen.

Zum Blockieren des Zugriffs auf diese Apps wird Folgendes empfohlen:

* Richten Sie die Anspruchsregeln für Active Directory-Verbunddienste (ADFS) dahingehend ein, dass nicht moderne Authentifizierungsprotokolle blockiert werden. Detaillierte Anleitungen werden in Szenario 3 beschrieben: [Blockieren des gesamten Zugriffs auf Office 365, bis auf browserbasierte Anwendungen](https://technet.microsoft.com/library/dn592182.aspx).
* Für **SharePoint Online** deaktivieren Sie die Verwendung nicht moderner Authentifizierungsmethoden im SharePoint Online-Dienst. Verwenden Sie das PowerShell-Cmdlet [Set-SPOTenant](https://technet.microsoft.com/library/fp161390.aspx), um die Eigenschaft für ältere Authentifizierungsprotokolle auf „False“ festzulegen:

```
 Set-SPOTenant -LegacyAuthProtocolsEnabled $false
```


>[!IMPORTANT]
>Die App-basierte zertifikatbasierte Authentifizierung darf nicht mit der zertifikatbasierten Authentifizierung von Azure Active Directory (Azure AD) verwendet werden. Es darf immer jeweils nur eine Authentifizierungsmethode konfiguriert werden.

### <a name="see-also"></a>Siehe auch
[App-basierter bedingter Zugriff mit Intune](app-based-conditional-access-intune.md)
