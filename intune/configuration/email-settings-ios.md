---
title: Konfigurieren von E-Mail-Einstellungen für iOS-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Sehen Sie sich eine Liste aller E-Mail-Einstellungen an, die Sie in Microsoft Intune konfigurieren und zu iOS-Geräten hinzufügen können, einschließlich der Verwendung von Exchange-Servern und dem Abrufen von Attributen aus Azure Active Directory. Mit Microsoft Intune können Sie außerdem SSL aktivieren, Benutzer mit Zertifikaten oder Benutzername bzw. Kennwort authentifizieren und E-Mails auf iOS-Geräten mithilfe von Gerätekonfigurationsprofilen synchronisieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/12/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 73de0ac94ff02e43fe73ca6357f6008ba71e3b93
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74390818"
---
# <a name="add-e-mail-settings-for-ios-devices-in-microsoft-intune"></a>Hinzufügen von E-Mail-Einstellungen für iOS-Geräte in Microsoft Intune

In Microsoft Intune können Sie E-Mails erstellen und konfigurieren, um eine Verbindung zu einem E-Mail-Server herzustellen, die Art der Benutzerauthentifizierung auszuwählen, S/MIME für die Verschlüsselung verwenden und vieles mehr.

In diesem Artikel werden alle E-Mail-Einstellungen aufgeführt und beschrieben, die für Geräte mit iOS verfügbar sind. Sie können ein Gerätekonfigurationsprofil erstellen, um diese E-Mail-Einstellungen auf Ihre iOS-Geräte zu übertragen oder darauf bereitzustellen.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie eine Gerätekonfigurationsprofil.](../email-settings-configure.md)

> [!NOTE]
> Diese Einstellungen sind für alle Registrierungs Typen verfügbar. Weitere Informationen zu den Registrierungs Typen finden Sie unter [IOS](../ios-enroll.md)-Registrierung.

## <a name="exchange-activesync-account-settings"></a>Einstellungen für Exchange ActiveSync-Konto

- **E-Mail-Server:** Geben Sie den Hostnamen Ihres Exchange-Servers ein.
- **Kontoname:** Geben Sie den Anzeigenamen des E-Mail-Kontos ein. Dieser Name wird Benutzern auf ihren Geräten angezeigt.
- **Benutzernamensattribut aus AAD:** Dieser Name ist das Attribut, dass Intune aus Azure Active Directory (AAD) abruft. Intune generiert dynamisch den Benutzernamen, der von diesem Profil verwendet wird. Folgende Optionen sind verfügbar:
  - **Benutzerprinzipalname:** Ruft den Namen ab, z.B. `user1` oder `user1@contoso.com`
  - **Primäre SMTP-Adresse:** Ruft den Namen im Format einer E-Mail-Adresse ab, z.B. `user1@contoso.com`
  - **SAM-Kontoname:** Erfordert die Domäne, z.B. `domain\user1` Geben Sie außerdem Folgendes ein:  
    - **Quelle des Benutzerdomänennamens:** Wählen Sie zwischen **AAD** oder **Benutzerdefiniert**.
      - **Aad**: Sie erhalten die Attribute aus Azure AD. Geben Sie außerdem Folgendes ein:
        - **Attribut des Benutzerdomänennamens aus AAD**: Rufen Sie entweder das Attribut **Vollständiger Domänenname** (`contoso.com`) oder das Attribut **NetBIOS-Name** (`contoso`) des Benutzers ab.

      - **Custom**: die Attribute werden von einem benutzerdefinierten Domänen Namen abgeleitet. Geben Sie außerdem Folgendes ein:
        - **Zu verwendender benutzerdefinierter Domänenname**: Geben Sie einen Wert ein, den Intune als Domänennamen verwenden kann, wie z. B. `contoso.com` oder `contoso`.

- **E-Mail-Adressattribut aus AAD:** Die Art der Generierung der E-Mail-Adresse für den Benutzer Folgende Optionen sind verfügbar:
  - **Benutzerprinzipalname**: Der vollständige Prinzipalname, z. B. `user1@contoso.com` oder `user1`, dieser wird als E-Mail-Adresse verwendet.
  - **Primäre SMTP-Adresse**: Wählen Sie die primäre SMTP-Adresse für die Anmeldung bei Exchange aus, z. B. `user1@contoso.com`.
- **Authentifizierungsmethode**: Wählen Sie aus, wie sich Benutzer bei dem e-Mail-Server authentifizieren. Folgende Optionen sind verfügbar:
  - **Zertifikat**: Wählen Sie ein zuvor erstelltes SCEP- oder PKCS-Clientzertifikatprofil für die Authentifizierung der Exchange-Verbindung aus. Diese Option bietet die sicherste und nahtlose benutzerfreundliche Benutzer Leistung.
  - **Benutzername und Kennwort**: Benutzer werden aufgefordert, Ihren Benutzernamen und Ihr Kennwort einzugeben.
  - **Abgeleitete**Anmelde Informationen: Verwenden Sie ein Zertifikat, das von der Smartcard eines Benutzers abgeleitet ist. Weitere Informationen finden Sie unter [verwenden abgeleiteter Anmelde Informationen in Microsoft InTune](../protect/derived-credentials.md).

  >[!NOTE]
  > Die mehrstufige Authentifizierung mit Azure wird nicht unterstützt.
  
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

## <a name="exchange-activesync-profile-configuration"></a>Konfiguration von Exchange ActiveSync-Profilen

> [!IMPORTANT]
> Wenn Sie diese Einstellungen konfigurieren, wird ein neues Profil auf dem Gerät bereitgestellt, auch wenn ein vorhandenes e-Mail-Profil aktualisiert wird, das diese Einstellungen enthält. Benutzer werden aufgefordert, Ihr Kennwort für das Exchange ActiveSync-Konto einzugeben. Diese Einstellungen wirken sich auf die Eingabe des Kennworts aus.

- **Austauschen von Daten für die Synchronisierung**: Wählen Sie bei Verwendung von Exchange ActiveSync die Exchange-Dienste aus, die auf dem Gerät synchronisiert werden: Kalender, Kontakte, Erinnerungen, Notizen und e-Mail. Folgende Optionen sind verfügbar:
  - **Alle Daten** (Standard): die Synchronisierung ist für alle Dienste aktiviert.
  - **Nur e-Mail**: die Synchronisierung ist nur für e-Mail aktiviert. Die Synchronisierung ist für die anderen Dienste deaktiviert.
  - **Nur Kalender**: die Synchronisierung ist nur für Kalender aktiviert. Die Synchronisierung ist für die anderen Dienste deaktiviert.
  - **Nur Calendar und Contacts**: die Synchronisierung ist nur für Kalender und Kontakte aktiviert. Die Synchronisierung ist für die anderen Dienste deaktiviert.
  - **Nur Kontakte**: die Synchronisierung ist nur für Kontakte aktiviert. Die Synchronisierung ist für die anderen Dienste deaktiviert.

  Diese Funktion gilt für:  
  - iOS 13.0 und neuer
  - iOS 13.0 und höher

- **Benutzern das Ändern von Synchronisierungs Einstellungen gestatten**: Wählen Sie diese Option aus, wenn Benutzer die Exchange ActiveSync-Einstellungen für die Exchange-Dienste auf dem Gerät ändern können: Kalender, Kontakte, Erinnerungen, Notizen und e-Mail. Folgende Optionen sind verfügbar:

  - **Ja** (Standardeinstellung): Benutzer können das Synchronisierungs Verhalten aller Dienste ändern. Wenn Sie **Ja** auswählen, können *alle* Dienste geändert werden.
  - **Nein**: Benutzer können die Synchronisierungs Einstellungen aller Dienste nicht ändern. Wenn Sie **Nein** auswählen, werden Änderungen an *allen* Diensten blockiert.

  > [!TIP]
  > Wenn Sie die Einstellung für die **Exchange-Daten für die Synchronisierung** konfiguriert haben, um nur einige Dienste zu synchronisieren, wird empfohlen, für diese Einstellung **Nein** auszuwählen. Wenn Sie **Nein** auswählen, werden Benutzer daran gehindert, den Synchronisierungs Dienst zu ändern.

  Diese Funktion gilt für:  
  - iOS 13.0 und neuer
  - iOS 13.0 und höher

## <a name="exchange-activesync-email-settings"></a>Exchange ActiveSync-e-Mail-Einstellungen

- **S/MIME**: s/MIME verwendet e-Mail-Zertifikate, die durch signieren, verschlüsseln und entschlüsseln zusätzliche Sicherheit für Ihre e-Mail-Kommunikation bieten. Wenn Sie S/MIME für eine E-Mail-Nachricht verwenden, bestätigen Sie die Authentizität des Absenders sowie die Integrität und Vertraulichkeit der Nachricht.

  Folgende Optionen sind verfügbar:

  - **S/MIME deaktivieren** (Standard): verwendet kein s/MIME-e-Mail-Zertifikat, um e-Mails zu signieren, zu verschlüsseln oder zu entschlüsseln.
  - **S/MIME aktivieren**: Ermöglicht Benutzern das Signieren und/oder Verschlüsseln von E-Mails in der nativen iOS-E-Mail-Anwendung. Geben Sie außerdem Folgendes ein:

    - **S/MIME-Signierung aktiviert**: **Deaktivieren** (Standard) erlaubt Benutzern nicht, die Nachricht digital zu signieren. Eine Festlegung auf **Aktivieren** ermöglicht Benutzern das digitale Signieren ausgehender E-Mails für das von Ihnen angegebene Konto. Durch die Signatur können Benutzer, die Nachrichten empfangen, sicher sein, dass die Nachricht vom jeweiligen Absender stammt und nicht von jemandem, der vorgibt, der Absender zu sein.
      - **Ändern der Einstellung durch Benutzer zulassen**: **aktivieren** ermöglicht Benutzern das Ändern der Signierungs Optionen. **Deaktivieren** (Standard) verhindert, dass Benutzer die Signierung ändern, und erzwingt die Verwendung der von Ihnen konfigurierten Signierung durch Benutzer.
      - **Signatur Zertifikattyp**: Ihre Optionen:
        - **Nicht konfiguriert**: Diese Einstellung wird von InTune nicht aktualisiert oder geändert.
        - **Keine**: als Administrator erzwingen Sie kein bestimmtes Zertifikat. Wählen Sie diese Option aus, damit Benutzer ihr eigenes Zertifikat auswählen können.
        - **Abgeleitete**Anmelde Informationen: Verwenden Sie ein Zertifikat, das von der Smartcard eines Benutzers abgeleitet ist. Weitere Informationen finden Sie unter [verwenden abgeleiteter Anmelde Informationen in Microsoft InTune](../protect/derived-credentials.md).
        - **Zertifikate**: Wählen Sie ein vorhandenes PKCS- oder SCEP-Zertifikatprofil aus, das zum Signieren von E-Mail-Nachrichten verwendet wird.
      - **Einstellung Änderung durch Benutzer zulassen**: **aktivieren** ermöglicht es Benutzern, das Signaturzertifikat zu ändern. Eine Festlegung auf **Deaktivieren** (Standardeinstellung) verhindert, dass Benutzer das Signaturzertifikat ändern. Benutzer sind somit gezwungen, das von Ihnen konfigurierte Zertifikat zu verwenden.

        Diese Funktion gilt für:  
        - iOS 12 und höher
        - iPadOS 12 und höher

    - **Encrypt by default** (Standardmäßig verschlüsseln): Mit der Option **Aktivieren** werden alle Nachrichten standardmäßig verschlüsselt. Durch eine Festlegung auf **Deaktivieren** (Standardeinstellung) werden sämtliche Nachrichten standardmäßig nicht verschlüsselt.
      - **Benutzern das Ändern der Einstellung erlauben**: Wählen Sie **Aktivieren** aus, damit Benutzer das Standardverhalten für die Verschlüsselung ändern können. Eine Festlegung auf **Deaktivieren** verhindert, dass Benutzer das Standardverhalten für die Verschlüsselung ändern können. Benutzer müssen so die von Ihnen konfigurierte Einstellung verwenden.

        Diese Funktion gilt für:  
        - iOS 12 und höher
        - iPadOS 12 und höher

    - **Verschlüsselung pro Nachricht erzwingen**: Mit der Verschlüsselung pro Nachricht können Benutzer auswählen, welche E-Mails vor dem Senden verschlüsselt werden sollen.

      Durch eine Festlegung auf **Aktivieren** wird beim Erstellen einer neuen E-Mail die Option zum Verschlüsseln pro Nachricht angezeigt. Die Benutzer können daraufhin auswählen, ob sie die Verschlüsselung pro Nachricht ein- oder ausschalten möchten. Wenn außerdem die Einstellung **Standardmäßig verschlüsseln** aktiviert ist, ermöglicht die Aktivierung der Verschlüsselung pro Nachricht, dass Benutzer diese deaktivieren können.

      Mit der Option **Deaktivieren** (Standardeinstellung) wird verhindert, dass die Option zum Verschlüsseln pro Nachricht angezeigt wird. Wenn außerdem die Einstellung **Standardmäßig verschlüsseln** deaktiviert ist, ermöglicht die Aktivierung der Verschlüsselung pro Nachricht, dass Benutzer sich für die Verschlüsselung pro Nachricht entscheiden können.

      - **Verschlüsselungs Zertifikattyp**: Ihre Optionen:
        - **Nicht konfiguriert**: Diese Einstellung wird von InTune nicht aktualisiert oder geändert.
        - **Keine**: als Administrator erzwingen Sie kein bestimmtes Zertifikat. Wählen Sie diese Option aus, damit Benutzer ihr eigenes Zertifikat auswählen können.
        - **Abgeleitete**Anmelde Informationen: Verwenden Sie ein Zertifikat, das von der Smartcard eines Benutzers abgeleitet ist. Weitere Informationen finden Sie unter [verwenden abgeleiteter Anmelde Informationen in Microsoft InTune](../protect/derived-credentials.md).
        - **Zertifikate**: Wählen Sie ein vorhandenes PKCS- oder SCEP-Zertifikatprofil aus, das zum Signieren von E-Mail-Nachrichten verwendet wird.
      - **Benutzern das Ändern der Einstellung erlauben**: Wählen Sie **Aktivieren** aus, damit Benutzer das Verschlüsselungszertifikat ändern können. Mit der Option **Deaktivieren** (Standardeinstellung) wird verhindert, dass Benutzer das Verschlüsselungszertifikat ändern. Benutzer sind somit gezwungen, das von Ihnen konfigurierte Zertifikat zu verwenden.

        Diese Funktion gilt für:  
        - iOS 12 und höher
        - iPadOS 12 und höher

- **Anzahl der zu synchronisierenden E-Mails:** Wählen Sie die Anzahl an Tagen von E-Mails, die Sie synchronisieren möchten. Oder wählen Sie **Unbegrenzt**, um alle verfügbaren E-Mails zu synchronisieren.
- **Verschieben von Nachrichten in andere E-Mail-Konten zulassen**: Durch Festlegung der Option auf **Aktivieren** (Standardeinstellung) können Benutzer E-Mail-Nachrichten zwischen verschiedenen Konten verschieben, die auf ihrem Gerät konfiguriert sind.
- **E-Mail-Versand aus Anwendungen von Drittanbietern zulassen**: Durch Festlegung der Option auf **Aktivieren** (Standardeinstellung) können Benutzer dieses Profil als Standardkonto für das Senden von E-Mails verwenden. Dadurch können Anwendungen von Drittanbietern E-Mails in der nativen E-Mail-App öffnen, um beispielsweise Dateien an E-Mails anzuhängen.
- **Kürzlich verwendete E-Mail-Adressen synchronisieren**: Durch Festlegung der Option auf **Aktivieren** können Benutzer die Liste der vor Kurzem auf dem Gerät verwendeten E-Mail-Adressen mit dem Server synchronisieren.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. Die nächsten Schritte sind das [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](../device-profile-assign.md) und das [Überwachen von Geräteprofilen in Microsoft Intune](../device-profile-monitor.md).

Konfigurieren von e-Mail-Einstellungen für [Android](../email-settings-android.md)-, [Android Enterprise](../email-settings-android-enterprise.md)-, [Windows 10](email-settings-windows-10.md)-und [Windows Phone 8,1](email-settings-windows-phone-8-1.md) -Geräte
