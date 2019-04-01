---
title: E-Mail-Einstellungen für iOS-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Sehen Sie sich eine Liste aller E-Mail-Einstellungen an, die Sie in Microsoft Intune konfigurieren und zu iOS-Geräten hinzufügen können, einschließlich der Verwendung von Exchange-Servern und dem Abrufen von Attributen aus Azure Active Directory. Mit Microsoft Intune können Sie außerdem SSL aktivieren, Benutzer mit Zertifikaten oder Benutzername bzw. Kennwort authentifizieren und E-Mails auf iOS-Geräten mithilfe von Gerätekonfigurationsprofilen synchronisieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/11/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1cf1daf42d1dfcd8dd25304040e868581a056943
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566408"
---
# <a name="email-profile-settings-for-ios-devices-in-intune"></a>Einstellungen für das E-Mail-Profil für iOS-Geräte in Intune

In Microsoft Intune können Sie E-Mails erstellen und konfigurieren, um eine Verbindung zu einem E-Mail-Server herzustellen, die Art der Benutzerauthentifizierung auszuwählen, S/MIME für die Verschlüsselung verwenden und vieles mehr.

In diesem Artikel werden alle E-Mail-Einstellungen aufgeführt und beschrieben, die für Geräte mit iOS verfügbar sind. Sie können ein Gerätekonfigurationsprofil erstellen, um diese E-Mail-Einstellungen auf Ihre iOS-Geräte zu übertragen oder darauf bereitzustellen.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie eine Gerätekonfigurationsprofil.](email-settings-configure.md#create-a-device-profile)

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

- **S/MIME**: Mit der Option **S/MIME aktivieren** wird zugelassen, dass Benutzer E-Mails in der nativen iOS-E-Mail-Anwendung signieren und/oder verschlüsseln. 

  Wenn Sie S/MIME für eine E-Mail-Nachricht verwenden, bestätigen Sie die Authentizität des Absenders sowie die Integrität und Vertraulichkeit der Nachricht.

  - **S/MIME-Signatur aktiviert**: Bei Festlegung auf **Aktivieren** können Benutzer ausgehende E-Mails für das von Ihnen angegebene Konto digital signieren. Durch die Signatur können Benutzer, die Nachrichten empfangen, sicher sein, dass die Nachricht vom jeweiligen Absender stammt und nicht von jemandem, der vorgibt, der Absender zu sein. Wenn Sie **Deaktivieren** auswählen, können Benutzer Nachrichten nicht digital signieren.
    - **Einstellung Änderung durch Benutzer zulassen**: Wählen Sie **aktivieren** Benutzer S/MIME-Signatur Verhalten ändern können. Mit der Option **Deaktivieren** wird verhindert, dass Benutzer die von Ihnen konfigurierte Einstellung zum Erstellen einer S/MIME-Signatur ändern. Verfügbar in iOS 12 und höheren Versionen.

  - **S/MIME-Signaturzertifikat**: Wählen Sie ein vorhandenes PKCS- oder SCEP-Zertifikatprofil aus, das zum Signieren von E-Mail-Nachrichten verwendet wird.
    - **Einstellung Änderung durch Benutzer zulassen**: Wählen Sie **aktivieren** , dass Benutzer das Signaturzertifikat ändern können. Mit der Option **Deaktivieren** wird verhindert, dass Benutzer das Signaturzertifikat ändern. Benutzer sind somit gezwungen, das von Ihnen konfigurierte Zertifikat zu verwenden. Verfügbar in iOS 12 und höheren Versionen.

  - **Standardmäßig verschlüsseln**: **aktivieren** alle Nachrichten verschlüsselt, als das Standardverhalten. Mit der Option **Deaktivieren** werden nicht alle Nachrichten standardmäßig verschlüsselt.
    - **Einstellung Änderung durch Benutzer zulassen**: Wählen Sie **aktivieren** um Benutzern das Ändern des Standardverhaltens für die Verschlüsselung ermöglichen. Mit der Option **Deaktivieren** wird verhindert, dass Benutzer das Standardverhalten für die Verschlüsselung ändern, und Benutzer werden gezwungen, die von Ihnen konfigurierte Einstellung zu verwenden. Verfügbar in iOS 12 und höheren Versionen.

  - **Verschlüsselung pro Nachricht erzwingen**: Mit der Verschlüsselung pro Nachricht können Benutzer auswählen, welche E-Mails vor dem Senden verschlüsselt werden sollen. Wählen Sie **Aktivieren** aus, um beim Erstellen einer neuen E-Mail die Option zum Verschlüsseln pro Nachricht anzuzeigen. Die Benutzer können dann auswählen, ob sie die Verschlüsselung pro Nachricht ein- oder ausschalten möchten. Mit der Option **Deaktivieren** wird verhindert, dass die Option zum Verschlüsseln pro Nachricht angezeigt wird.

    Wenn die Einstellung **Standardmäßig verschlüsseln** aktiviert ist, ermöglicht die Aktivierung der Verschlüsselung pro Nachricht, dass Benutzer diese deaktivieren können. Wenn die Einstellung **Standardmäßig verschlüsseln** deaktiviert ist, ermöglicht die Aktivierung der Verschlüsselung pro Nachricht, dass Benutzer sich für die Verschlüsselung pro Nachricht entscheiden können.

  - **S/MIME-Verschlüsselungszertifikat**: Wählen Sie ein vorhandenes PKCS- oder SCEP-Zertifikatprofil aus, das zum Verschlüsseln von E-Mail-Nachrichten verwendet wird.
    - **Einstellung Änderung durch Benutzer zulassen**: Wählen Sie **aktivieren** , dass Benutzer das Verschlüsselungszertifikat ändern können. Mit der Option **Deaktivieren** wird verhindert, dass Benutzer das Verschlüsselungszertifikat ändern. Benutzer sind somit gezwungen, das von Ihnen konfigurierte Zertifikat zu verwenden. Verfügbar in iOS 12 und höheren Versionen.
- **Anzahl der zu synchronisierenden E-Mails:** Wählen Sie die Anzahl an Tagen von E-Mails, die Sie synchronisieren möchten. Oder wählen Sie **Unbegrenzt**, um alle verfügbaren E-Mails zu synchronisieren.
- **Verschieben von Nachrichten in andere E-Mail-Konten zulassen:** Mit der Option **Aktivieren** können Benutzer E-Mail-Nachrichten zwischen verschiedenen Konten verschieben, die auf ihrem Gerät konfiguriert sind.
- **E-Mail-Versand aus Anwendungen von Drittanbietern zulassen:** Mit der Option **Aktivieren** können Benutzer dieses Profil als Standardkonto für das Senden von E-Mails verwenden. Dadurch können Anwendungen von Drittanbietern E-Mails in der nativen E-Mail-App öffnen, um beispielsweise Dateien an E-Mails anzuhängen.
- **Kürzlich verwendete E-Mail-Adressen synchronisieren:** Wenn diese Option **aktiviert** ist, können Benutzer die Liste der E-Mail-Adressen, die vor Kurzem auf dem Gerät verwendet wurden, mit dem Server synchronisieren.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. Die nächsten Schritte sind das [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](device-profile-assign.md) und das [Überwachen von Geräteprofilen in Microsoft Intune](device-profile-monitor.md).

Konfigurieren Sie die E-Mail-Einstellungen auf [Android](email-settings-android.md)-, [Windows 10](email-settings-windows-10.md)- und [Windows Phone 8.1](email-settings-windows-phone-8-1.md)-Geräten.
