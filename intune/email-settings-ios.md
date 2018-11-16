---
title: E-Mail-Einstellungen für iOS-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Erstellen Sie ein E-Mail-Profil für die Gerätekonfiguration, die Exchange-Server verwendet und Attribute von Azure Active Directory abruft. Mit Microsoft Intune können Sie außerdem SSL aktivieren, Benutzer mit Zertifikaten oder Benutzername/Kennwort authentifizieren und E-Mails auf iOS-Geräten synchronisieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a6fd10ab6a1e9dd7249e2ae1d4bf558d190276ed
ms.sourcegitcommit: b0ee8626191961dc07f9f7f9d8e6a5fb09c63350
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51505877"
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

- **E-Mail-Adressattribut aus AAD:** Die Art der Generierung der E-Mail-Adresse für den Benutzer Wählen Sie **Benutzerprinzipalname** (`user1@contoso.com` oder `user1`) aus, um den vollständigen Benutzerprinzipalnamen als E-Mail-Adresse zu verwenden. Wählen Sie **Primäre SMTP-Adresse** (`user1@contoso.com`) aus, um die primäre SMTP-Adresse zum Anmelden bei Exchange zu verwenden.
- **Authentifizierungsmethode:** Wählen Sie entweder **Benutzername und Kennwort** oder **Zertifikate** als Authentifizierungsmethode aus, die vom E-Mail-Profil verwendet werden soll. Die mehrstufige Authentifizierung mit Azure wird nicht unterstützt.
  - Wenn Sie **Zertifikat** ausgewählt haben, wählen Sie ein zuvor erstelltes SCEP- oder PKCS-Clientzertifikatprofil aus, das zur Authentifizierung der Exchange-Verbindung verwendet werden soll.
- **SSL:** Mit der Option **Aktivieren** wird die SSL-Kommunikation (Secure Sockets Layer) beim Senden und Empfangen von E-Mails sowie bei der Kommunikation mit dem Exchange-Server verwendet.
- **OAuth:** Mit der Option **Aktivieren** wird Open Authorization (OAuth) beim Senden und Empfangen von E-Mails sowie bei der Kommunikation mit Exchange verwendet. Wenn Ihr OAuth-Server die zertifikatbasierte Authentifizierung verwendet, wählen Sie **Zertifikat** als **Authentifizierungsmethode** aus, und fügen Sie das Zertifikat dem Profil hinzu. Wählen Sie andernfalls **Benutzername und Kennwort** als **Authentifizierungsmethode** aus. Stellen Sie bei der Verwendung von OAuth Folgendes sicher:

  - Vergewissern Sie sich, dass Ihr E-Mail-Programm OAuth unterstützt, bevor Sie Ihren Benutzern dieses Profil zuordnen. Office 365 Exchange Online unterstützt OAuth. Lokale Exchange-Lösungen oder Lösungen von Partnern oder Drittanbietern unterstützen OAuth möglicherweise nicht. Lokale Exchange-Lösungen können für die moderne Authentifizierung verwendet werden. Weitere Informationen finden Sie im Blogbeitrag [Announcing Hybrid Modern Authentication for Exchange On-Premises (Ankündigung: Hybride moderne Authentifizierung für lokale Exchange-Lösungen)](https://blogs.technet.microsoft.com/exchange/2017/12/06/announcing-hybrid-modern-authentication-for-exchange-on-premises/).

    Wenn das E-Mail-Profil OAuth verwendet und der E-Mail-Dienst dies nicht unterstützt, funktioniert die Option **Kennwort erneut eingeben** nicht. Dadurch geschieht beispielsweise nichts, wenn der Benutzer in den Apple-Geräteeinstellungen **Kennwort erneut eingeben** auswählt.

  - Wenn OAuth aktiviert ist, steht den Benutzern eine moderne Authentifizierung bei der Anmeldung mit einem E-Mail-Konto zur Verfügung, die auch die mehrstufige Authentifizierung (Multi-Factor Authentication, MFA) unterstützt. 

  - Einige Organisationen deaktivieren den [Self-Service-Anwendungszugriff](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-self-service-access) für Endbenutzer. In diesem Szenario schlägt die Anmeldung mit moderner Authentifizierung möglicherweise fehl, bis ein Administrator die Unternehmens-App „iOS Accounts“ (iOS-Konten) erstellt und den Benutzern in Azure AD Zugriff auf diese App gewährt.

    Hierfür wird normalerweise im Bereich [Anwendungszugriff](https://docs.microsoft.com/azure/active-directory/user-help/active-directory-saas-access-panel-introduction) über das Feature **App hinzufügen** eine Anwendung hinzugefügt, für die **keine Genehmigung des Unternehmens** erforderlich ist. Weitere Informationen finden Sie unter [Zuweisen von Benutzern zu Anwendungen](https://docs.microsoft.com/azure/active-directory/manage-apps/ways-users-get-assigned-to-applications).

  > [!NOTE]
  > Wenn Sie OAuth aktivieren, geschieht Folgendes:  
  > 1. Geräte, die bereits als Zielgerät eingetragen sind, erhalten ein neues Profil.
  > 2. Endbenutzer werden erneut zur Eingabe ihrer Anmeldeinformationen aufgefordert.

- **S/MIME:** **Aktivieren Sie S/MIME**, um ausgehende E-Mails mit der S/MIME-Signatur zu senden. Wenn diese Option aktiviert ist, können Sie außerdem E-Mails an Empfänger verschlüsseln, die verschlüsselte E-Mails empfangen können, sowie empfangene E-Mails entschlüsseln.
  - Wenn Sie **Zertifikat** ausgewählt haben, wählen Sie ein vorhandenes PKCS-Clientzertifikatprofil aus, um die Exchange-Verbindung zu authentifizieren und/oder den E-Mail-Verkehr zu verschlüsseln.
- **Anzahl der zu synchronisierenden E-Mails:** Wählen Sie die Anzahl an Tagen von E-Mails, die Sie synchronisieren möchten. Oder wählen Sie **Unbegrenzt**, um alle verfügbaren E-Mails zu synchronisieren.
- **Verschieben von Nachrichten in andere E-Mail-Konten zulassen:** Mit der Option **Aktivieren** können Benutzer E-Mail-Nachrichten zwischen verschiedenen Konten verschieben, die auf ihrem Gerät konfiguriert sind.
- **E-Mail-Versand aus Anwendungen von Drittanbietern zulassen:** Mit der Option **Aktivieren** können Benutzer dieses Profil als Standardkonto für das Senden von E-Mails verwenden. Dadurch können Anwendungen von Drittanbietern E-Mails in der nativen E-Mail-App öffnen, um beispielsweise Dateien an E-Mails anzuhängen.
- **Kürzlich verwendete E-Mail-Adressen synchronisieren:** Wenn diese Option **aktiviert** ist, können Benutzer die Liste der E-Mail-Adressen, die vor Kurzem auf dem Gerät verwendet wurden, mit dem Server synchronisieren.

## <a name="next-steps"></a>Nächste Schritte
[Konfigurieren von E-Mail-Einstellungen in Intune](email-settings-configure.md)
