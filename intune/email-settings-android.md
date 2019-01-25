---
title: E-Mail-Einstellungen für Android und Android Enterprise in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen Sie ein E-Mail-Profil für die Gerätekonfiguration, das Exchange-Server verwendet und Attribute aus Azure Active Directory abruft. Aktivieren Sie SSL oder S/MIME, authentifizieren Sie Benutzer mit Zertifikaten oder Benutzername/Kennwort, und synchronisieren Sie E-Mails und Zeitpläne auf Android-Geräten und Geräten mit Android-Arbeitsprofil unter Verwendung von Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/15/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: b96363d679a6f09327bf9a1b46421e786d1956a8
ms.sourcegitcommit: 912aee714432c4a1e8efeee253ca2be4f972adaa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2019
ms.locfileid: "54316881"
---
# <a name="android-and-android-enterprise-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Android- und Android Enterprise-Geräteeinstellungen zum Konfigurieren von E-Mail, Authentifizierung und Synchronisierung in Intune

In diesem Artikel werden die verschiedenen E-Mail-Einstellungen aufgeführt und beschrieben, die Sie auf Android- und Android Enterprise-Geräten steuern können. Als Bestandteil Ihrer Lösung für die mobile Geräteverwaltung (Mobile Device Management, MDM) verwenden Sie diese Einstellungen, um einen E-Mail-Server zu konfigurieren, SSL zur Verschlüsselung von E-Mails zu nutzen und vieles mehr.

Als Intune-Administrator können Sie für folgende Android-Geräte E-Mail-Einstellungen erstellen und zuweisen:

- Android Samsung Knox Standard
- Android Enterprise

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie ein Profil für die Gerätekonfiguration.](email-settings-configure.md)

## <a name="android-samsung-knox"></a>Android (Samsung Knox)

- **E-Mail-Server**: Geben Sie den Hostnamen Ihres Exchange-Servers ein.
- **Kontoname**: Geben Sie den Anzeigenamen des E-Mail-Kontos ein. Dieser Name wird Benutzern auf ihren Geräten angezeigt.
- **Benutzernamensattribut aus AAD**: Dieser Name ist das Attribut, dass Intune aus Azure Active Directory (AAD) abruft. Intune generiert dynamisch den Benutzernamen, der von diesem Profil verwendet wird. Folgende Optionen sind verfügbar:
  - **Benutzerprinzipalname**: Hiermit wird der Name abgerufen, z.B. `user1` oder `user1@contoso.com`.
  - **Benutzername**: Hiermit wird nur der Name abgerufen, z.B. `user1`.
  - **SAM-Kontoname**: Erfordert die Domäne, z.B. `domain\user1`. Der SAM-Kontoname kann nur mit Android-Geräten verwendet werden. Android Enterprise wird nicht unterstützt.

    Geben Sie außerdem Folgendes ein:  
    - **Quelle für Benutzerdomänenname**: Wählen Sie zwischen **AAD** (Azure Active Directory) oder **Benutzerdefiniert**.

      Wenn Sie die Attribute von **AAD** abrufen möchten, geben Sie Folgendes ein:
      - **Attribut für Benutzerdomänenname aus AAD**: Rufen Sie entweder das Attribut **Vollständiger Domänenname** oder das Attribut **NetBIOS-Name** des Benutzers ab.

      Wenn Sie sich dazu entscheiden, die Attribute **Benutzerdefiniert** zu verwenden, geben Sie Folgendes ein:
      - **Zu verwendender benutzerdefinierter Domänenname**: Geben Sie einen Wert ein, den Intune als Domänennamen verwenden kann, z.B. `contoso.com` oder `contoso`.

- **Attribut für E-Mail-Adresse aus AAD**: Wählen Sie aus, wie die E-Mail-Adresse für den Benutzer generiert wird. Wählen Sie **Primäre SMTP-Adresse** (`user1@contoso.com`) aus, um die primäre SMTP-Adresse zum Anmelden bei Exchange zu verwenden. Verwenden Sie **Benutzerprinzipalname** (`user1@contoso.com` oder `user1`), um den vollständigen Benutzerprinzipalnamen als E-Mail-Adresse zu verwenden.

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
  - **Kontakte**
  - **Kalender**
  - **Aufgaben**

## <a name="android-enterprise"></a>Android Enterprise

- **E-Mail-App**: Wählen Sie entweder **Gmail** oder **Nine Work** aus.
- **E-Mail-Server**: Der Hostname Ihres Exchange-Servers.
- **Benutzernamensattribut aus AAD**: Dieser Name ist das Attribut in Active Directory (AD) oder Azure AD, das verwendet wird, um den Benutzernamen für dieses E-Mail-Profil zu generieren. Wählen Sie **Primäre SMTP-Adresse** aus, z.B. user1@contoso.com, oder **Benutzerprinzipalname**, z.B. „user1“ oder user1@contoso.com.
- **Attribut für E-Mail-Adresse aus AAD**: Vorgehensweise beim Generieren der E-Mail-Adresse für den Benutzer auf den einzelnen Geräten. Wählen Sie **Benutzerprinzipalname**, um den vollständigen Benutzerprinzipalnamen als E-Mail-Adresse bzw. **Benutzername** zu verwenden.
- **Authentifizierungsmethode**: Wählen Sie entweder **Benutzername und Kennwort** oder **Zertifikat** als Authentifizierungsmethode aus, die vom E-Mail-Profil verwendet werden soll.
  - Wenn Sie **Zertifikat** ausgewählt haben, wählen Sie ein SCEP- oder PKCS-Clientzertifikatprofil aus, das Sie zur Authentifizierung der Exchange-Verbindung zuvor erstellt haben.
- **SSL**: Verwenden Sie die SSL-Kommunikation (Secure Sockets Layer) beim Senden und Empfangen von E-Mails sowie bei der Kommunikation mit dem Exchange-Server.
- **Menge an E-Mails für die Synchronisierung**: Geben Sie die Anzahl von Tagen an, für die E-Mails synchronisiert werden sollen, oder wählen Sie **Unbegrenzt** aus, um alle verfügbaren E-Mail-Nachrichten zu synchronisieren.
- **Zu synchronisierender Inhaltstyp** (nur Nine Work): Wählen Sie die Inhaltstypen aus, die auf den Geräten synchronisiert werden sollen. Mit der Option **Nicht konfiguriert** wird diese Einstellung deaktiviert. Wenn ein Endbenutzer die Synchronisierung auf einem Gerät aktiviert, für das **Nicht konfiguriert** festgelegt ist, wird die Synchronisierung wieder deaktiviert, wenn das Gerät mit Intune synchronisiert wird, da die Richtlinie erneut angewendet wird. 

  Sie können folgende Inhalte synchronisieren: 
  - **Kontakte**
  - **Kalender**
  - **Aufgaben**

## <a name="next-steps"></a>Nächste Schritte
[Konfigurieren von E-Mail-Einstellungen in Intune](email-settings-configure.md)
