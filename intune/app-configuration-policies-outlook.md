---
title: Outlook-Einstellungen für iOS- und Android-Geräte in Microsoft Intune
description: Erstellen Sie eine Konfigurationsrichtlinie, um Microsoft Outlook-Einstellungen festzulegen, die auf iOS- und Android-Geräten ausgeführt werden.
keywords: ''
author: Erikre
ms.author: erikre
ms.reviewer: smithre4
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 691029cc7b9fd8880c5440a84b95bbf2462920d6
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180322"
---
# <a name="microsoft-outlook-configuration-settings"></a>Microsoft Outlook-Konfigurationseinstellungen 

Verwenden Sie eine Konfigurationsrichtlinie, um Microsoft Outlook-Einstellungen festzulegen, die auf iOS- und Android-Geräten ausgeführt werden. 

Informationen zum Erstellen einer App-Konfigurationsrichtlinie für verwaltete iOS-Geräte finden Sie unter [Hinzufügen von App-Konfigurationsrichtlinien für verwaltete iOS-Geräte](app-configuration-policies-use-ios.md). Informationen zum Erstellen einer App-Konfigurationsrichtlinie für verwaltete Android-Geräte finden Sie unter [Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Android-Geräte](app-configuration-policies-use-android.md). 

## <a name="configuration-settings"></a>Konfigurationseinstellungen

Wenn Sie eine Konfigurationsrichtlinie in Intune hinzufügen, können Sie bestimmte Einstellungen zur Konfiguration von Microsoft Outlook festlegen. Im Bereich **Konfigurationseinstellungen** können Sie das E-Mail-Konto konfigurieren.

### <a name="basic-authentication-email-account-settings"></a>E-Mail-Konto-Einstellungen für die Standardauthentifizierung
Outlook für iOS und Android bietet Exchange-Administratoren die Möglichkeit, Kontokonfigurationen an ihre lokalen Benutzer zu übertragen, die die Standardauthentifizierung mit dem ActiveSync-Protokoll verwenden. Weitere Informationen finden Sie unter [Kontoeinrichtung in Outlook für iOS und Android mithilfe der Standardauthentifizierung](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/account-setup). Um die Konfiguration für die Kontoeinrichtung zu aktivieren, können Sie die folgenden Einstellungen konfigurieren:

- **E-Mail-Server**: Geben Sie den Hostnamen Ihres lokalen Exchange-Servers ein (z.B. „mail.contoso.com“).
- **E-Mail-Kontoname:** Geben Sie den Anzeigenamen des E-Mail-Kontos ein. Dieser Name wird Benutzern auf ihren Geräten angezeigt.
- **Benutzernamensattribut aus AAD:** Dieser Name ist das Attribut, dass Intune aus Azure Active Directory (Azure AD) abruft. Intune generiert dynamisch den Benutzernamen, der von diesem Profil verwendet wird. Diese Optionen umfassen Folgendes:
  - **Benutzerprinzipalname:** Ruft den Namen ab, z.B. `user1` oder `user1@contoso.com`
  - **Primäre SMTP-Adresse:** Ruft den Namen im Format einer E-Mail-Adresse ab, z.B. `user1@contoso.com`
- **E-Mail-Adressattribut aus AAD:** Die Art der Generierung der E-Mail-Adresse für den Benutzer Wählen Sie **Primäre SMTP-Adresse** (`user1@contoso.com`) aus, um die primäre SMTP-Adresse zum Anmelden bei Exchange zu verwenden. Verwenden Sie **Benutzerprinzipalname** (`user1@contoso.com` oder `user1`), um den vollständigen Benutzerprinzipalnamen als E-Mail-Adresse zu verwenden. Es wird empfohlen, die **Primäre SMTP-Adresse** auszuwählen.
- **Kontodomäne**: (Optional) Die Domäne des Kontos.

## <a name="next-steps"></a>Nächste Schritte
[Konfigurieren von E-Mail-Einstellungen in Intune](email-settings-configure.md)

