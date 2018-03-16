---
title: "E-Mail-Einstellungen in Microsoft Intune für Android- und Android for Work-Geräte"
titleSuffix: 
description: "In diesem Artikel lernen Sie die Microsoft Intune-Einstellungen kennen, mit denen Sie E-Mail-Einstellungen für Android- und Android for Work-Geräte konfigurieren können."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a68607be7cbd84d5a9e9080d0a8608bce85edd22
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2018
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-android-and-android-for-work"></a>E-Mail-Profileinstellungen in Microsoft Intune für Geräte mit Android und Android für Work

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Als Intune-Administrator können Sie für folgende Android-Geräte E-Mail-Einstellungen erstellen und zuweisen:
- [Android – Samsung Knox Standard](#android-samsung-knox-standard-email-settings)
- [Android for Work](#android-for-work-email-settings)

## <a name="android-samsung-knox-standard-email-settings"></a>E-Mail-Einstellungen gemäß Android Samsung KNOX Standard
- **E-Mail-Server:** Der Hostname Ihres Exchange-Servers.
- **Kontoname** – Der Anzeigename für das E-Mail-Konto so, wie er den Benutzern auf ihren Geräten angezeigt wird.
- **Benutzernamensattribut aus AAD** – Dieser Name ist das Attribut in Active Directory (AD) oder Azure AD, der verwendet wird, um den Benutzername für dieses E-Mail-Profil zu generieren. Wählen Sie **Primäre SMTP-Adresse** aus, z.B. user1@contoso.com, oder **Benutzerprinzipalname**, z.B. „user1“ oder user1@contoso.com.
- **E-Mail-Adressattribut aus AAD:** Die Art der Generierung der E-Mail-Adresse für den Benutzer auf den einzelnen Geräten. Wählen Sie **Primäre SMTP-Adresse** aus, um die primäre SMTP-Adresse zum Anmelden bei Exchange zu verwenden. Verwenden Sie **Benutzerprinzipalname**, um den vollständigen Benutzerprinzipalnamen als E-Mail-Adresse zu verwenden.
- **Authentifizierungsmethode:** Wählen Sie entweder **Benutzername und Kennwort** oder **Zertifikate** als Authentifizierungsmethode aus, die vom E-Mail-Profil verwendet werden soll.
    - Wenn Sie **Zertifikat** ausgewählt haben, wählen Sie ein SCEP- oder PKCS-Clientzertifikatprofil aus, das Sie zur Authentifizierung der Exchange-Verbindung zuvor erstellt haben.

### <a name="security-settings"></a>Sicherheitseinstellungen

- **SSL:** Verwenden Sie SSL-Kommunikation (Secure Sockets Layer) beim Senden und Empfangen von E-Mails sowie bei der Kommunikation mit dem Exchange-Server.
- **S/MIME:** Ausgehende E-Mails werden mit S/MIME-Verschlüsselung gesendet.
    - Wenn Sie **Zertifikat** ausgewählt haben, wählen Sie ein SCEP- oder PKCS-Clientzertifikatprofil aus, das Sie zur Authentifizierung der Exchange-Verbindung zuvor erstellt haben.

### <a name="synchronization-settings"></a>Synchronisierungseinstellungen

- **Menge an E-Mails für die Synchronisierung:** Wählen Sie die Anzahl der Tage von E-Mails aus, die synchronisiert werden sollen, oder wählen Sie **Unbegrenzt** aus, um alle verfügbaren E-Mail-Nachrichten zu synchronisieren.
- **Synchronisierungszeitplan** – Wählen Sie den Zeitplan aus, nach dem Geräte mit Daten vom Exchange-Server synchronisiert werden. Sie können auch **Beim Erhalt von Nachrichten** auswählen, wobei die Daten sofort beim Eingang synchronisiert werden, oder **Manuell**, wobei der Benutzer des Geräts die Synchronisierung initiieren muss.

### <a name="content-sync-settings"></a>Inhaltssynchronisierungseinstellungen

- **Zu synchronisierender Inhaltstyp:** Wählen Sie die Inhaltstypen aus, die auf Geräten synchronisiert werden sollen:
    - **Kontakte**
    - **Kalender**
    - **Aufgaben**

## <a name="android-for-work-email-settings"></a>Android for Work-E-Mail-Einstellungen

- **E-Mail-App** – Wählen Sie entweder **Gmail** oder **Nine Work**
- **E-Mail-Server:** Der Hostname Ihres Exchange-Servers.
- **Benutzernamensattribut aus AAD**: Dieser Name ist das Attribut in Active Directory (AD) oder Azure AD, mit dem der Benutzername für dieses E-Mail-Profil generiert wird. Wählen Sie **Primäre SMTP-Adresse** aus, z.B. user1@contoso.com, oder **Benutzerprinzipalname**, z.B. „user1“ oder user1@contoso.com.
- **E-Mail-Adressattribut aus AAD:** Die Art der Generierung der E-Mail-Adresse für den Benutzer auf den einzelnen Geräten. Wählen Sie **Benutzerprinzipalname**, um den vollständigen Benutzerprinzipalnamen als E-Mail-Adresse bzw. **Benutzername** zu verwenden.
- **Authentifizierungsmethode:** Wählen Sie entweder **Benutzername und Kennwort** oder **Zertifikate** als Authentifizierungsmethode aus, die vom E-Mail-Profil verwendet werden soll.
    - Wenn Sie **Zertifikat** ausgewählt haben, wählen Sie ein SCEP- oder PKCS-Clientzertifikatprofil aus, das Sie zur Authentifizierung der Exchange-Verbindung zuvor erstellt haben.
- **SSL:** Verwenden Sie SSL-Kommunikation (Secure Sockets Layer) beim Senden und Empfangen von E-Mails sowie bei der Kommunikation mit dem Exchange-Server.
- **Menge an E-Mails für die Synchronisierung:** Wählen Sie die Anzahl der Tage von E-Mails aus, die synchronisiert werden sollen, oder wählen Sie **Unbegrenzt** aus, um alle verfügbaren E-Mail-Nachrichten zu synchronisieren.
- **Zu synchronisierender Inhaltstyp** (nur Nine Work) – Wählen Sie die Inhaltstypen aus, die auf Geräten synchronisiert werden sollen:
    - **Kontakte**
    - **Kalender**
    - **Aufgaben**
