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
ms.custom: intune-azure
ms.openlocfilehash: 24ed1a895dd3e4cad6111b40913b43fa9c6a3cec
ms.sourcegitcommit: 11bd3dbbc9dd762df7c6d20143f2171799712547
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2018
ms.locfileid: "48903521"
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

