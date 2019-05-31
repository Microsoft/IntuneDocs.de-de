---
title: Blockieren von Apps ohne moderne Authentifizierung in Intune
titleSuffix: Microsoft Intune
description: Erfahren Sie mehr über die App- sowie die moderne Authentifizierung (ADAL) mit Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/03/2019
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: conceptual
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9ca96f36f8813d80c7ebb07bfb3bd65f8aa0b392
ms.sourcegitcommit: 71314481e644025c005019b478b4cbeaf2390ea9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/05/2019
ms.locfileid: "59569102"
---
# <a name="block-apps-that-dont-use-modern-authentication-adal"></a>Blockieren von Apps, die keine moderne Authentifizierung verwenden (ADAL)

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Der App-basierte bedingte Zugriff mit App-Schutzrichtlinien hängt von Anwendungen ab, die die [moderne Authentifizierung](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) nutzen, bei der es sich um eine Implementierung von OAuth2 handelt. Die meisten aktuellen mobilen und desktopbasierten Office-Anwendungen nutzen die moderne Authentifizierung. Es gibt jedoch Apps von Drittanbietern oder ältere Office-Apps, die andere Authentifizierungsmethoden wie die Standardauthentifizierung und die formularbasierte Authentifizierung nutzen.

## <a name="block-access-to-apps"></a>Blockieren des App-Zugriffs

Verwenden Sie zum Blockieren des Zugriffs auf Apps, die keine moderne Authentifizierung verwenden, die App-Schutzrichtlinien von Intune, um den bedingten Zugriff zu implementieren. Weitere Informationen finden Sie unter [App-basierter bedingter Zugriff mit Intune](app-based-conditional-access-intune.md).

## <a name="additional-information"></a>Zusätzliche Informationen

Weitere Informationen zum bedingten Zugriff in Azure AD finden Sie in den folgenden Artikeln:
- [Was ist der bedingte Zugriff in Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)
- [Funktionsweise des App-basierten bedingten Zugriffs](app-based-conditional-access-intune.md#how-app-based-conditional-access-works)
- [How to: Block legacy authentication to Azure AD with conditional access (Vorgehensweise: Blockieren der Legacyauthentifizierung für Azure AD mit bedingtem Zugriff)](https://docs.microsoft.com/azure/active-directory/conditional-access/conditional-access-for-exo-and-spo).

## <a name="next-steps"></a>Nächste Schritte

- [App-basierter bedingter Zugriff mit Intune](app-based-conditional-access-intune.md)
