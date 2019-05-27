---
title: 'E-Mail-Einstellungen für Windows 10-Geräte in Microsoft Intune: Azure | Microsoft-Dokumentation'
description: Erstellen Sie ein E-Mail-Profil für die Gerätekonfiguration, die Exchange-Server verwendet und Attribute von Azure Active Directory abruft. Mit Microsoft Intune können Sie auch SSL aktivieren und E-Mails und Zeitpläne auf Windows 10-Geräten synchronisieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/29/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 87a48c677e122d93bb03508e18b86549b7fe285d
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66047989"
---
# <a name="email-profile-settings-for-devices-running-windows-10---intune"></a>E-Mail-Profileinstellungen für Windows 10-Geräte: Intune

Mit den E-Mail-Profileinstellungen können Sie die E-Mail-App auf Ihren Windows 10-Geräte konfigurieren.

- **E-Mail-Server:** Geben Sie den Hostnamen Ihres Exchange-Servers ein.
- **Kontoname:** Geben Sie den Anzeigenamen des E-Mail-Kontos ein. Dieser Name wird Benutzern auf ihren Geräten angezeigt.
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

## <a name="security-settings"></a>Sicherheitseinstellungen

- **SSL:** Verwenden Sie SSL-Kommunikation (Secure Sockets Layer) beim Senden und Empfangen von E-Mails sowie bei der Kommunikation mit dem Exchange-Server.

## <a name="synchronization-settings"></a>Synchronisierungseinstellungen

- **Anzahl der zu synchronisierenden E-Mails:** Wählen Sie die Anzahl an Tagen von E-Mails, die Sie synchronisieren möchten. Oder wählen Sie **Unbegrenzt**, um alle verfügbaren E-Mails zu synchronisieren.
- **Synchronisierungszeitplan:** Wählen Sie den zeitlichen Ablauf der Synchronisierung der Daten vom Exchange-Server aus. Außerdem können Sie **Bei Eintreffen von Nachrichten** wählen, wodurch Daten bei Eingang synchronisiert werden, oder **Manuell**, wodurch der Benutzer des Geräts die Synchronisierung von Hand starten muss.

## <a name="content-sync-settings"></a>Inhaltssynchronisierungseinstellungen

- **Zu synchronisierender Inhaltstyp:** Wählen Sie die Inhaltstypen aus, die auf Geräten synchronisiert werden sollen:
  - **Kontakte**
  - **Kalender**
  - **Aufgaben**

## <a name="next-steps"></a>Nächste Schritte
[Konfigurieren von E-Mail-Einstellungen in Intune](email-settings-configure.md)
