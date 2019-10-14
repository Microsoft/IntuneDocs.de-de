---
title: E-Mail-Einstellungen für Android Enterprise in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen Sie ein E-Mail-Profil für die Gerätekonfiguration, das Exchange-Server verwendet und Attribute aus Azure Active Directory abruft. Aktivieren Sie SSL oder S/MIME, authentifizieren Sie Benutzer mit Zertifikaten oder Benutzername/Kennwort, und synchronisieren Sie E-Mails und Zeitpläne auf Geräten mit Android-Arbeitsprofil unter Verwendung von Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/07/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.reviewer: maholdaa
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 62fad2a881332470a6c3e95b7cdcab0403ba1839
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734660"
---
# <a name="android-enterprise-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Android Enterprise-Geräteeinstellungen zum Konfigurieren von E-Mail, Authentifizierung und Synchronisierung in Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

In diesem Artikel werden die verschiedenen E-Mail-Einstellungen aufgeführt und beschrieben, die Sie auf Android Enterprise-Geräten steuern können. Als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM) verwenden Sie diese Einstellungen, um einen E-Mail-Server zu konfigurieren, SSL zur Verschlüsselung von E-Mails zu nutzen und vieles mehr.

Als Intune-Administrator können Sie für Android Enterprise-Geräte im Arbeitsprofil E-Mail-Einstellungen erstellen und zuweisen.

Weitere Informationen zu E-Mail-Profilen in Intune finden Sie unter [Hinzufügen von E-Mail-Einstellungen für Geräte mit Intune](email-settings-configure.md).

## <a name="before-you-begin"></a>Vorbereitung

Erstellen Sie ein [Geräte Konfigurations Profil](email-settings-configure.md#create-a-device-profile) (Arbeitsprofil auswählen), oder erstellen Sie eine [App-Konfigurationsrichtlinie](../apps/app-configuration-policies-use-android.md).

## <a name="android-enterprise"></a>Android Enterprise

- **E-Mail-App:** Wählen Sie entweder **Gmail** oder **Nine Work** aus.
- **E-Mail-Server:** Der Hostname Ihres Exchange-Servers. Geben Sie beispielsweise `outlook.office365.com` ein.
- **Benutzernamensattribut aus AAD:** Dieser Name ist das Attribut, dass Intune aus Azure Active Directory (Azure AD) abruft. Intune generiert dynamisch den Benutzernamen, der von diesem Profil verwendet wird. Folgende Optionen sind verfügbar:

  - **Benutzerprinzipalname:** Ruft den Namen ab, z.B. `user1` oder `user1@contoso.com`
  - **Benutzername:** Ruft nur den Namen ab, z.B. `user1`

- **E-Mail-Adressenattribut aus AAD:** Dieser Name ist das E-Mail-Adressenattribut, dass Intune aus Azure AD abruft. Intune generiert dynamisch die E-Mail-Adresse, die von diesem Profil verwendet wird. Folgende Optionen sind verfügbar:
  - **Benutzerprinzipalname**: Der vollständige Prinzipalname, z.B. `user1@contoso.com` oder `user1`, wird als E-Mail-Adresse verwendet.
  - **Primäre SMTP-Adresse:** Verwendet die primäre SMTP-Adresse, z. B. `user1@contoso.com`, zum Anmelden bei Exchange.

- **Authentifizierungsmethode**: Wählen Sie entweder **Benutzername und Kennwort** oder **Zertifikate** als Authentifizierungsmethode aus, die vom E-Mail-Profil verwendet werden soll.
  - Wenn Sie **Zertifikat** auswählen, wählen Sie ein SCEP- oder PKCS-Clientzertifikatprofil aus, das Sie zur Authentifizierung der Exchange-Verbindung zuvor erstellt haben.
- **SSL**: Wählen Sie **Aktivieren** aus, um die SSL-Kommunikation (Secure Sockets Layer) beim Senden und Empfangen von E-Mails sowie bei der Kommunikation mit dem Exchange-Server zu verwenden.
- **Anzahl der zu synchronisierenden E-Mails:** Wählen Sie aus, welche Menge an E-Mails Sie synchronisieren möchten. Wählen Sie alternativ **Unbegrenzt** aus, um alle verfügbaren E-Mails zu synchronisieren.
- **Zu synchronisierender Inhaltstyp** (Nur Nine Work): Wählen Sie die Daten aus, die auf den Geräten synchronisiert werden sollen. Folgende Optionen sind verfügbar:
  - **Kontakte**: Wählen Sie **Aktivieren** aus, um Benutzern zu gestatten, Kontakte mit ihren Geräten zu synchronisieren.
  - **Kalender**: Wählen Sie **Aktivieren** aus, um Benutzern zu gestatten, den Kalender mit ihren Geräten zu synchronisieren.
  - **Aufgaben**: Wählen Sie **Aktivieren** aus, um Benutzern zu gestatten, beliebige Aufgaben mit ihren Geräten zu synchronisieren.

## <a name="next-steps"></a>Nächste Schritte

[Zuweisen von Profilen](device-profile-assign.md) und [Überwachen von Profilen](device-profile-monitor.md)

Sie können auch E-Mail-Profile erstellen für Geräte auf [Android Samsung Knox](email-settings-android.md), [iOS](email-settings-ios.md), [Windows 10 und höher](email-settings-windows-10.md) sowie [Windows Phone 8.1](email-settings-windows-phone-8-1.md).