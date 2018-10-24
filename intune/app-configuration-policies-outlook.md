---
title: Outlook-Einstellungen für iOS- und Android-Geräte in Microsoft Intune
description: Erstellen Sie eine Konfigurationsrichtlinie, um Microsoft Outlook-Einstellungen festzulegen, die auf iOS- und Android-Geräten ausgeführt werden.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7fc9f34bbd3d14ac4291582247b1e45169c2cccc
ms.sourcegitcommit: d92caead1d96151fea529c155bdd7b554a2ca5ac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/06/2018
ms.locfileid: "48828803"
---
# <a name="microsoft-outlook-configuration-settings"></a>Microsoft Outlook-Konfigurationseinstellungen 

Verwenden Sie eine Konfigurationsrichtlinie, um Microsoft Outlook-Einstellungen festzulegen, die auf iOS- und Android-Geräten ausgeführt werden. 

Informationen zum Erstellen einer App-Konfigurationsrichtlinie für verwaltete iOS-Geräte finden Sie unter [Hinzufügen von App-Konfigurationsrichtlinien für verwaltete iOS-Geräte](app-configuration-policies-use-ios.md). Informationen zum Erstellen einer App-Konfigurationsrichtlinie für verwaltete Android-Geräte finden Sie unter [Hinzufügen von App-Konfigurationsrichtlinien für verwaltete Android-Geräte](app-configuration-policies-use-android.md). 

## <a name="configuration-settings"></a>Konfigurationseinstellungen

Wenn Sie eine Konfigurationsrichtlinie in Intune hinzufügen, können Sie bestimmte Einstellungen zur Konfiguration von Microsoft Outlook festlegen. Im Bereich **Konfigurationseinstellungen** können Sie das E-Mail-Konto konfigurieren.

### <a name="email-account-settings"></a>Einstellungen des E-Mail-Kontos

Die folgenden Konfigurationseinstellungen gelten für Microsoft Outlook.

- **E-Mail-Server:** Geben Sie den Hostnamen Ihres Exchange-Servers ein.
- **E-Mail-Kontoname:** Geben Sie den Anzeigenamen des E-Mail-Kontos ein. Dieser Name wird Benutzern auf ihren Geräten angezeigt.
- **Benutzernamensattribut aus AAD:** Dieser Name ist das Attribut, dass Intune aus Azure Active Directory (AAD) abruft. Intune generiert dynamisch den Benutzernamen, der von diesem Profil verwendet wird. Folgende Optionen sind verfügbar:
  - **Benutzerprinzipalname:** Ruft den Namen ab, z.B. `user1` oder `user1@contoso.com`
  - **Primäre SMTP-Adresse:** Ruft den Namen im Format einer E-Mail-Adresse ab, z.B. `user1@contoso.com`
  - **SAM-Kontoname:** Erfordert die Domäne, z.B. `domain\user1`

    Geben Sie außerdem Folgendes ein:  
    - **Quelle des Benutzerdomänennamens:** Wählen Sie zwischen **AAD** oder **Benutzerdefiniert**.

      Wenn Sie die Attribute von **AAD** abrufen möchten, geben Sie Folgendes ein:
      - **Attribut des Benutzerdomänennames von AAD:** Rufen Sie entweder das Attribut **Full domain name** (vollständiger Domänenname) oder **NetBIOS name** (NetBIOS-Name) des Benutzers ab.

      Wenn Sie sich dazu entscheiden, die Attribute **Benutzerdefiniert** zu verwenden, geben Sie Folgendes ein:
      - **Zu verwendender benutzerdefinierter Domänenname:** Geben Sie einen Wert ein, den Intune als Domänennamen verwenden kann, wie z.B. `contoso.com` oder `contoso`

- **E-Mail-Adressattribut aus AAD:** Die Art der Generierung der E-Mail-Adresse für den Benutzer Wählen Sie **Primäre SMTP-Adresse** (`user1@contoso.com`) aus, um die primäre SMTP-Adresse zum Anmelden bei Exchange zu verwenden. Verwenden Sie **Benutzerprinzipalname** (`user1@contoso.com` oder `user1`), um den vollständigen Benutzerprinzipalnamen als E-Mail-Adresse zu verwenden.
- **Kontodomäne**: (Optional) Die Domäne des Kontos.

## <a name="next-steps"></a>Nächste Schritte
[Konfigurieren von E-Mail-Einstellungen in Intune](email-settings-configure.md)

