---
title: E-Mail-Einstellungen in Microsoft Intune für iOS-Geräte
titleSuffix: ''
description: In diesem Artikel lernen Sie die Microsoft Intune-Einstellungen kennen, mit denen Sie E-Mail-Einstellungen auf Geräten mit iOS konfigurieren können.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0912ec4fdc77b51903b4febd54f9d16972b867a8
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-ios"></a>E-Mail-Profileinstellungen in Microsoft Intune für Geräte mit iOS 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In diesem Artikel werden Ihnen die E-Mail-Profileinstellungen gezeigt, die Sie für Ihre iOS-Geräte konfigurieren können.

## <a name="email-settings"></a>E-Mail-Einstellungen

- **E-Mail-Server:** Der Hostname Ihres Exchange-Servers.
- **Kontoname** – Der Anzeigename für das E-Mail-Konto so, wie er den Benutzern auf ihren Geräten angezeigt wird.
- **Benutzernamensattribut aus AAD:** Das Attribut in Active Directory (AD) oder Azure AD, mit dem der Benutzername für dieses E-Mail-Profil generiert wird. Wählen Sie **Primäre SMTP-Adresse** aus, z.B. **user1@contoso.com**, oder **Benutzerprinzipalname**, z.B. **user1** oder **user1@contoso.com**.
- **E-Mail-Adressattribut aus AAD:** Die Art der Generierung der E-Mail-Adresse für den Benutzer auf den einzelnen Geräten. Wählen Sie **Primäre SMTP-Adresse** aus, um die primäre SMTP-Adresse zum Anmelden bei Exchange zu verwenden. Verwenden Sie **Benutzerprinzipalname** aus, um den vollständigen Benutzerprinzipalnamen als E-Mail-Adresse zu verwenden.
- **Authentifizierungsmethode:** Wählen Sie entweder **Benutzername und Kennwort** oder **Zertifikate** als Authentifizierungsmethode aus, die vom E-Mail-Profil verwendet werden soll. (**Hinweis**: Azure Multi-Factor Authentication wird nicht unterstützt.)
    - Wenn Sie **Zertifikat** ausgewählt haben, wählen Sie ein zuvor erstelltes SCEP- oder PKCS-Clientzertifikatprofil aus, das zur Authentifizierung der Exchange-Verbindung verwendet werden soll.
- **SSL:** Verwenden Sie SSL-Kommunikation (Secure Sockets Layer) beim Senden und Empfangen von E-Mails sowie bei der Kommunikation mit dem Exchange-Server.
- **S/MIME**: Ausgehende E-Mails werden mithilfe der S/MIME-Signatur gesendet.
    - Wenn Sie **Zertifikat** ausgewählt haben, wählen Sie ein zuvor erstelltes SCEP- oder PKCS-Clientzertifikatprofil aus, das zur Authentifizierung der Exchange-Verbindung verwendet werden soll.
    - Wenn Sie ein SCEP-Zertifikat wählen, stellen Sie sicher, dass ein gültiges PFX-Zertifikat (Personal Information Exchange) auf dem Gerät installiert ist.
- **Menge an E-Mails für die Synchronisierung:** Wählen Sie die Anzahl der Tage von E-Mails aus, die synchronisiert werden sollen, oder wählen Sie **Unbegrenzt** aus, um alle verfügbaren E-Mail-Nachrichten zu synchronisieren.
- **Verschieben von Nachrichten in andere E-Mail-Konten zulassen:** Hiermit können Benutzer E-Mail-Nachrichten zwischen verschiedenen Konten verschieben, die auf ihrem Gerät konfiguriert sind.
- **E-Mail-Versand aus Drittanbieteranwendungen zulassen**: Erlaubt dem Benutzer die Auswahl dieses Profils als das Standardkonto für das Senden von E-Mails und erlaubt Drittanbieteranwendungen das Öffnen von E-Mails in der nativen E-Mail-App, um beispielsweise Dateien an E-Mails anzuhängen.
- **Kürzlich verwendete E-Mail-Adressen synchronisieren:** Mit diesem Feature können Benutzer die Liste der E-Mail-Adressen, die vor Kurzem auf dem Gerät verwendet wurden, mit dem Server synchronisieren.
