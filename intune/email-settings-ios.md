---
title: E-Mail-Einstellungen für iOS-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen Sie ein E-Mail-Profil für die Gerätekonfiguration, die Exchange-Server verwendet und Attribute von Azure Active Directory abruft. Mit Microsoft Intune können Sie außerdem SSL aktivieren, Benutzer mit Zertifikaten oder Benutzername/Kennwort authentifizieren und E-Mails auf iOS-Geräten synchronisieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2d27e90655e54051d73989202d2bc849a66208f5
ms.sourcegitcommit: 488be75cbee88455b33c68a3ec2acb864d461bf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "41910801"
---
# <a name="email-profile-settings-for-ios-devices---intune"></a>Einstellungen für das E-Mail-Profil für iOS-Geräte: Intune

Verwenden Sie die E-Mail-Profileinstellungen, um Ihre iOS-Geräte zu konfigurieren.

> [!IMPORTANT]
> Wir nehmen zurzeit einige Verbesserungen an dem in diesem Artikel beschriebenen S/MIME-Feature vor. Deshalb wurde das S/MIME-Feature in Intune vorübergehend entfernt. Nach der Veröffentlichung des Features werden wir diesen Hinweis entfernen.

## <a name="email-settings"></a>E-Mail-Einstellungen

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
- **Authentifizierungsmethode:** Wählen Sie entweder **Benutzername und Kennwort** oder **Zertifikate** als Authentifizierungsmethode aus, die vom E-Mail-Profil verwendet werden soll. Die mehrstufige Authentifizierung mit Azure wird nicht unterstützt.
  - Wenn Sie **Zertifikat** ausgewählt haben, wählen Sie ein zuvor erstelltes SCEP- oder PKCS-Clientzertifikatprofil aus, das zur Authentifizierung der Exchange-Verbindung verwendet werden soll.
- **SSL:** **Aktivieren** Sie die SSL-Kommunikation (Secure Sockets Layer) beim Senden und Empfangen von E-Mails sowie bei der Kommunikation mit dem Exchange-Server.
- **S/MIME:** **Aktivieren Sie S/MIME**, um ausgehende E-Mails mit der S/MIME-Signatur zu senden. Wenn diese Option aktiviert ist, können Sie außerdem E-Mails an Empfänger verschlüsseln, die verschlüsselte E-Mails empfangen können, sowie empfangene E-Mails entschlüsseln.
  - Wenn Sie **Zertifikat** ausgewählt haben, wählen Sie ein PKCS-Clientzertifikatprofil aus, das Sie zuvor zur Authentifizierung der Exchange-Verbindung erstellt haben, und bzw. oder verschlüsseln Sie Ihren E-Mail-Verkehr.
- **Anzahl der zu synchronisierenden E-Mails:** Wählen Sie die Anzahl an Tagen von E-Mails, die Sie synchronisieren möchten. Oder wählen Sie **Unbegrenzt**, um alle verfügbaren E-Mails zu synchronisieren.
- **Verschieben von Nachrichten in andere E-Mail-Konten zulassen:** Wenn Sie diese Option **aktivieren**, können Benutzer E-Mail-Nachrichten zwischen verschiedenen Konten verschieben, die auf ihrem Gerät konfiguriert sind.
- **E-Mail-Versand aus Drittanbieteranwendungen zulassen**: Wenn diese Option **aktiviert** ist, kann der Benutzer dieses Profil als Standardkonto für das Senden von E-Mails auswählen und zulassen, dass Drittanbieteranwendungen E-Mails in der nativen E-Mail-App öffnen, um beispielsweise Dateien an E-Mails anzuhängen.
- **Kürzlich verwendete E-Mail-Adressen synchronisieren:** Wenn diese Option **aktiviert** ist, können Benutzer die Liste der E-Mail-Adressen, die vor Kurzem auf dem Gerät verwendet wurden, mit dem Server synchronisieren.

## <a name="next-steps"></a>Nächste Schritte
[Konfigurieren von E-Mail-Einstellungen in Intune](email-settings-configure.md)
