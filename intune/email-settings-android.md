---
title: Android-E-Mail-Einstellungen in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen Sie ein E-Mail-Profil für die Gerätekonfiguration, das Exchange-Server verwendet und Attribute aus Azure Active Directory abruft. Aktivieren Sie SSL oder S/MIME, authentifizieren Sie Benutzer mit Zertifikaten oder Benutzername/Kennwort, und synchronisieren Sie E-Mails und Zeitpläne auf Android-Samsung Knox-Geräten unter Verwendung von Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/15/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 53f1c95fdbdd9d779fb339e4820a3e7000573e60
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57236925"
---
# <a name="android-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Android-Geräteeinstellungen zum Konfigurieren von E-Mail, Authentifizierung und Synchronisierung in Intune

In diesem Artikel werden die verschiedenen E-Mail-Einstellungen aufgeführt und beschrieben, die Sie auf Android-Samsung Knox-Geräten in Intune steuern können. Als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM) verwenden Sie diese Einstellungen, um einen E-Mail-Server zu konfigurieren, SSL zur Verschlüsselung von E-Mails zu nutzen und vieles mehr.

Als Intune-Administrator können Sie für Android-Samsung Knox-Standardgeräte E-Mail-Einstellungen erstellen und zuweisen.

Weitere Informationen zu E-Mail-Profilen in Intune finden Sie unter [Hinzufügen von E-Mail-Einstellungen für Geräte mit Intune](email-settings-configure.md).

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein Profil für die Gerätekonfiguration.](email-settings-configure.md#create-a-device-profile)

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **E-Mail-Server**: Geben Sie den Hostnamen Ihres Exchange-Servers ein. Geben Sie beispielsweise `outlook.office365.com` ein.
- **Kontoname**: Geben Sie den Anzeigenamen des E-Mail-Kontos ein. Dieser Name wird Benutzern auf ihren Geräten angezeigt.
- **Benutzernamensattribut aus AAD**: Dieser Name ist das Attribut, das Intune aus Azure Active Directory (Azure AD) abruft. Intune generiert dynamisch den Benutzernamen, der von diesem Profil verwendet wird. Folgende Optionen sind verfügbar:
  - **Benutzerprinzipalname**: Hiermit wird der Name abgerufen, z.B. `user1` oder `user1@contoso.com`.
  - **Benutzername**: Hiermit wird nur der Name abgerufen, z.B. `user1`.
  - **SAM-Kontoname**: Erfordert die Domäne, z.B. `domain\user1`. Der SAM-Kontoname wird nur mit Android-Geräten verwendet.

    Geben Sie außerdem Folgendes ein:  
    - **Quelle für Benutzerdomänenname**: Wählen Sie zwischen **AAD** (Azure Active Directory) oder **Benutzerdefiniert**.

      Wenn Sie die Attribute von **AAD** abrufen möchten, geben Sie Folgendes ein:
      - **Attribut für Benutzerdomänenname aus AAD**: Rufen Sie entweder das Attribut **Vollständiger Domänenname** oder das Attribut **NetBIOS-Name** des Benutzers ab.

      Wenn Sie sich dazu entscheiden, die Attribute **Benutzerdefiniert** zu verwenden, geben Sie Folgendes ein:
      - **Zu verwendender benutzerdefinierter Domänenname**: Geben Sie einen Wert ein, den Intune als Domänennamen verwenden kann, z.B. `contoso.com` oder `contoso`.

- **Attribut für E-Mail-Adresse aus AAD**: Dieser Name ist das E-Mail-Attribut, dass Intune aus Azure AD abruft. Intune generiert dynamisch die E-Mail-Adresse, die von diesem Profil verwendet wird. Folgende Optionen sind verfügbar:
  - **Benutzerprinzipalname**:  Der vollständige Prinzipalname, z.B. `user1@contoso.com` oder `user1`, wird als E-Mail-Adresse verwendet.
  - **Primäre SMTP-Adresse**: Verwenden Sie die primäre SMTP-Adresse, z.B. `user1@contoso.com`, zum Anmelden bei Exchange.

- **Authentifizierungsmethode**: Wählen Sie entweder **Benutzername und Kennwort** oder **Zertifikat** als Authentifizierungsmethode aus, die vom E-Mail-Profil verwendet werden soll.
  - Wenn Sie **Zertifikat** auswählen, wählen Sie ein SCEP- oder PKCS-Clientzertifikatprofil aus, das Sie zur Authentifizierung der Exchange-Verbindung zuvor erstellt haben.

### <a name="security-settings"></a>Sicherheitseinstellungen

- **SSL**: Verwenden Sie die SSL-Kommunikation (Secure Sockets Layer) beim Senden und Empfangen von E-Mails sowie bei der Kommunikation mit dem Exchange-Server.
- **S/MIME**: Ausgehende E-Mails werden mithilfe von S/MIME-Verschlüsselung gesendet.
  - Wenn Sie **Zertifikat** auswählen, wählen Sie ein SCEP- oder PKCS-Clientzertifikatprofil aus, das Sie zur Authentifizierung der Exchange-Verbindung zuvor erstellt haben.

### <a name="synchronization-settings"></a>Synchronisierungseinstellungen

- **Menge an E-Mails für die Synchronisierung**: Geben Sie die Anzahl von Tagen an, für die E-Mails synchronisiert werden sollen, oder wählen Sie **Unbegrenzt** aus, um alle verfügbaren E-Mail-Nachrichten zu synchronisieren.
- **Synchronisierungszeitplan**: Wählen Sie den Zeitplan aus, nach dem Geräte mit Daten vom Exchange-Server synchronisiert werden. Sie können auch **Beim Erhalt von Nachrichten** auswählen, wobei die Daten sofort beim Eingang synchronisiert werden, oder **Manuell**, wobei der Benutzer des Geräts die Synchronisierung initiieren muss.

### <a name="content-sync-settings"></a>Inhaltssynchronisierungseinstellungen

- **Zu synchronisierender Inhaltstyp**: Wählen Sie die Inhaltstypen aus, die auf den Geräten synchronisiert werden sollen. Mit der Option **Nicht konfiguriert** wird diese Einstellung deaktiviert. Wenn ein Endbenutzer die Synchronisierung auf einem Gerät aktiviert, für das **Nicht konfiguriert** festgelegt ist, wird die Synchronisierung wieder deaktiviert, wenn das Gerät mit Intune synchronisiert wird, da die Richtlinie erneut angewendet wird. 

  Sie können folgende Inhalte synchronisieren:  
  - **Kontakte:** Wählen Sie **Aktivieren** aus, um Endbenutzern zu gestatten, Kontakte mit ihren Geräten zu synchronisieren.
  - **Kalender:** Wählen Sie **Aktivieren** aus, um Endbenutzern zu gestatten, den Kalender mit ihren Geräten zu synchronisieren.
  - **Aufgaben:** Wählen Sie **Aktivieren** aus, um Endbenutzern zu gestatten, beliebige Aufgaben mit ihren Geräten zu synchronisieren.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)

Sie können auch E-Mail-Profile erstellen für [Android Enterprise-Arbeitsprofile](email-settings-android-enterprise.md), [iOS](email-settings-ios.md), [Windows 10 und höher](email-settings-windows-10.md) sowie [Windows Phone 8.1](email-settings-windows-phone-8-1.md).
