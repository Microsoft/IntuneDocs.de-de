---
title: Blockieren von Apps ohne moderne Authentifizierung in Intune
titleSuffix: Microsoft Intune
description: Erfahren Sie, wie Sie über Microsoft Intune Apps blockieren können, die keine moderne Authentifizierung (ADAL) verwenden.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a651f926f8e8cc5beab80a70649c82677e0b2487
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2019
ms.locfileid: "55833051"
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>Blockieren von Apps, die keine moderne Authentifizierung verwenden (ADAL)

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Der App-basierte bedingte Zugriff mit App-Schutzrichtlinien hängt von Anwendungen ab, die die [moderne Authentifizierung](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) nutzen, bei der es sich um eine Implementierung von OAuth2 handelt. Die meisten aktuellen mobilen und desktopbasierten Office-Anwendungen nutzen die moderne Authentifizierung. Es gibt jedoch Apps von Drittanbietern oder ältere Office-Apps, die andere Authentifizierungsmethoden wie die Standardauthentifizierung und die formularbasierte Authentifizierung nutzen.

## <a name="block-apps"></a>Blockieren von Apps

Um den Zugriff auf Apps zu blockieren, die keine moderne Authentifizierung verwenden, empfehlen wir die folgenden Methoden:

- Richten Sie die Anspruchsregeln für Active Directory-Verbunddienste (ADFS) dahingehend ein, dass nicht moderne Authentifizierungsprotokolle blockiert werden. Detaillierte Anleitungen werden in Szenario 3 beschrieben: [Blockieren des gesamten Zugriffs auf Office 365, bis auf browserbasierte Anwendungen](https://technet.microsoft.com/library/dn592182.aspx).
- Verwenden Sie bei **Exchange und SharePoint Online** den bedingten Zugriff für Azure Active Directory, und verwenden Sie bei SharePoint Online das PowerShell-Cmdlet "Set-SPOTenant". Ausführliche Anweisungen finden Sie unter [Einrichten von SharePoint Online und Exchange Online für bedingten Zugriff mit Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication#legacy-authentication-protocols).


>[!IMPORTANT]
>Die App-basierte zertifikatbasierte Authentifizierung darf nicht mit der zertifikatbasierten Authentifizierung von Azure Active Directory (Azure AD) verwendet werden. Es darf immer jeweils nur eine Authentifizierungsmethode konfiguriert werden.

## <a name="next-steps"></a>Nächste Schritte

- [App-basierter bedingter Zugriff mit Intune](app-based-conditional-access-intune.md)
