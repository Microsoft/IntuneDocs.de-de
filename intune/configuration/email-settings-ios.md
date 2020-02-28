---
title: Konfigurieren von E-Mail-Einstellungen für iOS/iPadOS-Geräte in Microsoft Intune – Azure | Microsoft-Dokumentation
description: Sehen Sie sich eine Liste aller E-Mail-Einstellungen an, die Sie in Microsoft Intune konfigurieren und zu iOS- und iPadOS-Geräten hinzufügen können, einschließlich der Verwendung von Exchange-Servern und dem Abrufen von Attributen aus Azure Active Directory. Mit Microsoft Intune können Sie außerdem SSL aktivieren, Benutzer mit Zertifikaten oder Benutzername bzw. per Kennwort authentifizieren und E-Mails auf iOS/iPadOS-Geräten mithilfe von Gerätekonfigurationsprofilen synchronisieren.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0ea06c50b1da237d4a822e80a8085b3b51913cec
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512805"
---
# <a name="add-e-mail-settings-for-ios-and-ipados-devices-in-microsoft-intune"></a>Hinzufügen von E-Mail-Einstellungen für iOS- und iPadOS-Geräte in Microsoft Intune

In Microsoft Intune können Sie E-Mails erstellen und konfigurieren, um eine Verbindung zu einem E-Mail-Server herzustellen, die Art der Benutzerauthentifizierung auszuwählen, S/MIME für die Verschlüsselung verwenden und vieles mehr.

In diesem Artikel werden alle E-Mail-Einstellungen aufgeführt und beschrieben, die für Geräte mit iOS/iPadOS verfügbar sind. Sie können ein Gerätekonfigurationsprofil erstellen, um diese E-Mail-Einstellungen auf Ihre iOS/iPadOS-Geräte zu übertragen oder darauf bereitzustellen.

## <a name="before-you-begin"></a>Vorbereitung

[Erstellen Sie eine Gerätekonfigurationsprofil.](../email-settings-configure.md)

> [!NOTE]
> Diese Einstellungen sind für alle Registrierungstypen verfügbar. Weitere Informationen zu den Registrierungstypen finden Sie unter [iOS/iPadOS-Registrierung](../ios-enroll.md).

## <a name="exchange-activesync-account-settings"></a>ActiveSync-Kontoeinstellungen

- **E-Mail-Server**: Geben Sie den Hostnamen Ihres Exchange-Servers ein.
- **Kontoname**: Geben Sie den Anzeigenamen des E-Mail-Kontos ein. Dieser Name wird Benutzern auf ihren Geräten angezeigt.
- **Benutzernamensattribut aus AAD**: Dieser Name ist das Attribut, dass Intune aus Azure Active Directory (AAD) abruft. Intune generiert dynamisch den Benutzernamen, der von diesem Profil verwendet wird. Folgende Optionen sind verfügbar:
  - **Benutzerprinzipalname**: Hiermit wird der Name abgerufen, z.B. `user1` oder `user1@contoso.com`.
  - **Primäre SMTP-Adresse**: Ruft den Namen im Format einer E-Mail-Adresse ab, z.B. `user1@contoso.com`.
  - **SAM-Kontoname**: Erfordert die Domäne, z.B. `domain\user1`. Geben Sie außerdem Folgendes ein:  
    - **Quelle für Benutzerdomänenname**: Wählen Sie zwischen **AAD** (Azure Active Directory) oder **Benutzerdefiniert**.
      - **AAD**: Attribute werden aus Azure AD abgerufen. Geben Sie außerdem Folgendes ein:
        - **Attribut für Benutzerdomänenname aus AAD**: Rufen Sie entweder das Attribut **Vollständiger Domänenname** (`contoso.com`) oder das Attribut **NetBIOS-Name** (`contoso`) des Benutzers ab.

      - **Benutzerdefiniert**: Die Attribute werden aus einem benutzerdefinierten Domänennamen abgeleitet. Geben Sie außerdem Folgendes ein:
        - **Zu verwendender benutzerdefinierter Domänenname**: Geben Sie einen Wert ein, den Intune als Domänennamen verwenden kann, z. B. `contoso.com` oder `contoso`.

- **Attribut für E-Mail-Adresse aus AAD**: Wählen Sie aus, wie die E-Mail-Adresse für den Benutzer generiert wird. Folgende Optionen sind verfügbar:
  - **Benutzerprinzipalname**: Der vollständige Prinzipalname, z. B. `user1@contoso.com` oder `user1`, wird als E-Mail-Adresse verwendet.
  - **Primäre SMTP-Adresse**: Verwenden Sie die primäre SMTP-Adresse, z. B. `user1@contoso.com`, für die Anmeldung bei Exchange.
- **Authentifizierungsmethode**: Wählen Sie aus, wie sich Benutzer beim E-Mail-Server authentifizieren. Folgende Optionen sind verfügbar:
  - **Zertifikat**: Wählen Sie ein zuvor erstelltes SCEP- oder PKCS-Clientzertifikatprofil für die Authentifizierung der Exchange-Verbindung aus. Diese Option bietet die höchste Sicherheit und ein nahtloses Benutzererlebnis.
  - **Benutzername und Kennwort**: Benutzer werden aufgefordert, Ihren Benutzernamen und Ihr Kennwort einzugeben.
  - **Abgeleitete Anmeldeinformationen**: Verwenden Sie ein Zertifikat, das von der Smartcard eines Benutzers abgeleitet ist. Weitere Informationen finden Sie unter [Verwenden abgeleiteter Anmeldeinformationen in Microsoft Intune](../protect/derived-credentials.md).

  >[!NOTE]
  > Die mehrstufige Authentifizierung mit Azure wird nicht unterstützt.
  
- **SSL**: Mit der Option **Aktivieren** wird die SSL-Kommunikation (Secure Sockets Layer) beim Senden und Empfangen von E-Mails sowie bei der Kommunikation mit dem Exchange-Server verwendet.
- **OAuth**: Mit der Option **Aktivieren** wird Open Authorization (OAuth) beim Senden und Empfangen von E-Mails sowie bei der Kommunikation mit Exchange verwendet. Wenn Ihr OAuth-Server die zertifikatbasierte Authentifizierung verwendet, wählen Sie **Zertifikat** als **Authentifizierungsmethode** aus, und fügen Sie das Zertifikat dem Profil hinzu. Wählen Sie andernfalls **Benutzername und Kennwort** als **Authentifizierungsmethode** aus. Stellen Sie bei der Verwendung von OAuth Folgendes sicher:

  - Vergewissern Sie sich, dass Ihr E-Mail-Programm OAuth unterstützt, bevor Sie Ihren Benutzern dieses Profil zuordnen. Office 365 Exchange Online unterstützt OAuth. Lokale Exchange-Lösungen oder Lösungen von Partnern oder Drittanbietern unterstützen OAuth möglicherweise nicht. Lokale Exchange-Lösungen können für die moderne Authentifizierung verwendet werden. Weitere Informationen finden Sie im Blogbeitrag [Announcing Hybrid Modern Authentication for Exchange On-Premises (Ankündigung: Hybride moderne Authentifizierung für lokale Exchange-Lösungen)](https://blogs.technet.microsoft.com/exchange/2017/12/06/announcing-hybrid-modern-authentication-for-exchange-on-premises/).

    Wenn das E-Mail-Profil OAuth verwendet und der E-Mail-Dienst dies nicht unterstützt, funktioniert die Option **Kennwort erneut eingeben** nicht. Dadurch geschieht beispielsweise nichts, wenn der Benutzer in den Apple-Geräteeinstellungen **Kennwort erneut eingeben** auswählt.

  - Wenn OAuth aktiviert ist, steht den Benutzern eine moderne Authentifizierung bei der Anmeldung mit einem E-Mail-Konto zur Verfügung, die auch die mehrstufige Authentifizierung (Multi-Factor Authentication, MFA) unterstützt. 

  - Einige Organisationen deaktivieren den [Self-Service-Anwendungszugriff](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-self-service-access) für Endbenutzer. In diesem Szenario schlägt die Anmeldung mit moderner Authentifizierung möglicherweise fehl, bis ein Administrator die Unternehmens-App „iOS Accounts“ (iOS-Konten) erstellt und den Benutzern in Azure AD Zugriff auf diese App gewährt.

    Hierfür wird normalerweise im Panel [Anwendungszugriff](https://docs.microsoft.com/azure/active-directory/user-help/active-directory-saas-access-panel-introduction) über das Feature **App hinzufügen** eine Anwendung hinzugefügt, für die **keine Genehmigung des Unternehmens** erforderlich ist. Weitere Informationen finden Sie unter [Zuweisen von Benutzern zu Anwendungen](https://docs.microsoft.com/azure/active-directory/manage-apps/ways-users-get-assigned-to-applications).

  > [!NOTE]
  > Wenn Sie OAuth aktivieren, geschieht Folgendes:  
  > 1. Geräte, die bereits als Zielgerät eingetragen sind, erhalten ein neues Profil.
  > 2. Endbenutzer werden erneut zur Eingabe ihrer Anmeldeinformationen aufgefordert.

## <a name="exchange-activesync-profile-configuration"></a>Konfiguration von Exchange ActiveSync-Profilen

> [!IMPORTANT]
> Durch das Konfigurieren dieser Einstellungen wird ein neues Profil für das Gerät bereitgestellt, selbst wenn ein vorhandenes E-Mail-Profil aktualisiert wird, um diese Einstellungen einzuschließen. Benutzer werden aufgefordert, das Kennwort für ihr Exchange ActiveSync-Konto einzugeben. Diese Einstellungen werden wirksam, wenn das Kennwort eingegeben wird.

- **Zu synchronisierende Exchange-Daten**: Wählen Sie bei Verwendung von Exchange ActiveSync die Exchange-Dienste aus, die auf dem Gerät synchronisiert werden: Kalender, Kontakte, Erinnerungen, Notizen und E-Mail. Folgende Optionen sind verfügbar:
  - **Alle Daten** (Standardeinstellung): die Synchronisierung ist für alle Dienste aktiviert.
  - **Nur E-Mail**: Die Synchronisierung ist nur für E-Mails aktiviert. Für die weiteren Dienste ist die Synchronisierung deaktiviert.
  - **Nur Kalender**: Die Synchronisierung ist nur für den Kalender aktiviert. Für die weiteren Dienste ist die Synchronisierung deaktiviert.
  - **Nur Kalender und Kontakte**: Die Synchronisierung ist nur für Kalender und Kontakte aktiviert. Für die weiteren Dienste ist die Synchronisierung deaktiviert.
  - **Nur Kontakte**: Die Synchronisierung ist nur für die Kontakte aktiviert. Für die weiteren Dienste ist die Synchronisierung deaktiviert.

  Diese Funktion gilt für:  
  - iOS 13.0 und neuer
  - iOS 13.0 und höher

- **Benutzern das Ändern der Synchronisierungseinstellungen gestatten**: Wählen Sie aus, ob Benutzer die Exchange ActiveSync-Einstellungen für die Exchange-Dienste auf dem Gerät ändern können: Kalender, Kontakte, Erinnerungen, Notizen und E-Mail. Folgende Optionen sind verfügbar:

  - **Ja** (Standardeinstellung): Benutzer können das Synchronisierungsverhalten aller Dienste ändern. Wenn Sie **Ja** auswählen, können *alle* Dienste geändert werden.
  - **Nein**: Benutzer können die Synchronisierungseinstellungen aller Dienste nicht ändern. Wenn Sie **Nein** auswählen, werden Änderungen an *allen* Diensten blockiert.

  > [!TIP]
  > Wenn Sie die Einstellung **Zu synchronisierende Exchange-Daten** so konfiguriert haben, dass nur einige Dienste synchronisiert werden, wird die Auswahl **Nein** für diese Einstellung empfohlen. Durch die Auswahl von **Nein** werden Benutzer daran gehindert, den synchronisierten Exchange-Dienst zu ändern.

  Diese Funktion gilt für:  
  - iOS 13.0 und neuer
  - iOS 13.0 und höher

## <a name="exchange-activesync-email-settings"></a>E-Mail-Einstellungen für Exchange ActiveSync

- **S/MIME**: S/MIME verwendet E-Mail-Zertifikate und bietet durch Signaturen, Verschlüsselung und Entschlüsselung zusätzliche Sicherheit für Ihre E-Mail-Kommunikation. Wenn Sie S/MIME für eine E-Mail-Nachricht verwenden, bestätigen Sie die Authentizität des Absenders sowie die Integrität und Vertraulichkeit der Nachricht.

  Folgende Optionen sind verfügbar:

  - **S/MIME deaktivieren** (Standardeinstellung): Es wird kein S/MIME-E-Mail-Zertifikat zum Signieren, Verschlüsseln oder Entschlüsseln von E-Mails verwendet.
  - **S/MIME aktivieren**: Ermöglicht Benutzern das Signieren und/oder Verschlüsseln von E-Mails in der nativen iOS/iPadOS-E-Mail-Anwendung. Geben Sie außerdem Folgendes ein:

    - **S/MIME-Signierung aktiviert**: Bei Auswahl von **Deaktivieren** (Standardeinstellung) können Benutzer Nachrichten nicht digital signieren. Eine Festlegung auf **Aktivieren** ermöglicht Benutzern das digitale Signieren ausgehender E-Mails für das von Ihnen angegebene Konto. Durch die Signatur können Benutzer, die Nachrichten empfangen, sicher sein, dass die Nachricht vom jeweiligen Absender stammt und nicht von jemandem, der vorgibt, der Absender zu sein.
      - **Benutzern das Ändern der Einstellung erlauben**: Bei Auswahl von **Aktivieren** können Benutzer das Standardverhalten für die Verschlüsselung ändern. **Deaktivieren** (Standardeinstellung) verhindert, dass Benutzer die Signatur ändern. Benutzer sind somit gezwungen, die von Ihnen konfigurierte Signatur zu verwenden.
      - **Signaturzertifikattyp**: Mögliche Optionen:
        - **Nicht konfiguriert:** Diese Einstellung wird von Intune nicht geändert oder aktualisiert.
        - **Keine**: Als Administrator erzwingen Sie kein bestimmtes Zertifikat. Wählen Sie diese Option aus, damit Benutzer ihr eigenes Zertifikat auswählen können.
        - **Abgeleitete Anmeldeinformationen**: Verwenden Sie ein Zertifikat, das von der Smartcard eines Benutzers abgeleitet ist. Weitere Informationen finden Sie unter [Verwenden abgeleiteter Anmeldeinformationen in Microsoft Intune](../protect/derived-credentials.md).
        - **Zertifikate:** Wählen Sie ein vorhandenes PKCS- oder SCEP-Zertifikatprofil aus, das zum Signieren von E-Mail-Nachrichten verwendet wird.
      - **Benutzern das Ändern der Einstellung erlauben**: Bei Auswahl von **Aktivieren** können Benutzer das Signaturzertifikat ändern. Eine Festlegung auf **Deaktivieren** (Standardeinstellung) verhindert, dass Benutzer das Signaturzertifikat ändern. Benutzer sind somit gezwungen, das von Ihnen konfigurierte Zertifikat zu verwenden.

        Diese Funktion gilt für:  
        - iOS 12 und höher
        - iPadOS 12 und höher

    - **Standardmäßig verschlüsseln**: Mit der Option **Aktivieren** werden alle Nachrichten standardmäßig verschlüsselt. Durch eine Festlegung auf **Deaktivieren** (Standardeinstellung) werden sämtliche Nachrichten standardmäßig nicht verschlüsselt.
      - **Benutzer das Ändern der Einstellung erlauben**: Bei Auswahl von **Aktivieren** können Benutzer das Standardverhalten für die Verschlüsselung ändern. Eine Festlegung auf **Deaktivieren** verhindert, dass Benutzer das Standardverhalten für die Verschlüsselung ändern können. Benutzer müssen so die von Ihnen konfigurierte Einstellung verwenden.

        Diese Funktion gilt für:  
        - iOS 12 und höher
        - iPadOS 12 und höher

    - **Force per-message encryption (Verschlüsselung pro Nachricht erzwingen)** : Die Verschlüsselung pro Nachricht ermöglicht es dem Benutzer, vor dem Senden auszuwählen, welche E-Mails verschlüsselt werden sollen.

      Durch eine Festlegung auf **Aktivieren** wird beim Erstellen einer neuen E-Mail die Option zum Verschlüsseln pro Nachricht angezeigt. Die Benutzer können daraufhin auswählen, ob sie die Verschlüsselung pro Nachricht ein- oder ausschalten möchten. Wenn außerdem die Einstellung **Standardmäßig verschlüsseln** aktiviert ist, ermöglicht die Aktivierung der Verschlüsselung pro Nachricht, dass Benutzer diese deaktivieren können.

      Mit der Option **Deaktivieren** (Standardeinstellung) wird verhindert, dass die Option zum Verschlüsseln pro Nachricht angezeigt wird. Wenn außerdem die Einstellung **Standardmäßig verschlüsseln** deaktiviert ist, ermöglicht die Aktivierung der Verschlüsselung pro Nachricht, dass Benutzer sich für die Verschlüsselung pro Nachricht entscheiden können.

      - **Verschlüsselungszertifikattyp**: Mögliche Optionen:
        - **Nicht konfiguriert:** Diese Einstellung wird von Intune nicht geändert oder aktualisiert.
        - **Keine**: Als Administrator erzwingen Sie kein bestimmtes Zertifikat. Wählen Sie diese Option aus, damit Benutzer ihr eigenes Zertifikat auswählen können.
        - **Abgeleitete Anmeldeinformationen**: Verwenden Sie ein Zertifikat, das von der Smartcard eines Benutzers abgeleitet ist. Weitere Informationen finden Sie unter [Verwenden abgeleiteter Anmeldeinformationen in Microsoft Intune](../protect/derived-credentials.md).
        - **Zertifikate:** Wählen Sie ein vorhandenes PKCS- oder SCEP-Zertifikatprofil aus, das zum Signieren von E-Mail-Nachrichten verwendet wird.
      - **Benutzer das Ändern der Einstellung erlauben**: Bei Auswahl von **Aktivieren** können Benutzer das Verschlüsselungszertifikat ändern. Mit der Option **Deaktivieren** (Standardeinstellung) wird verhindert, dass Benutzer das Verschlüsselungszertifikat ändern. Benutzer sind somit gezwungen, das von Ihnen konfigurierte Zertifikat zu verwenden.

        Diese Funktion gilt für:  
        - iOS 12 und höher
        - iPadOS 12 und höher

- **Menge an E-Mails für die Synchronisierung**: Wählen Sie die Anzahl der Tage aus, für die E-Mails synchronisiert werden sollen. Oder wählen Sie **Unbegrenzt**, um alle verfügbaren E-Mails zu synchronisieren.
- **Verschieben von Nachrichten in andere E-Mail-Konten zulassen**: Die Option **Aktivieren** (Standardeinstellung) ermöglicht es Benutzern, E-Mail-Nachrichten zwischen verschiedenen Konten zu verschieben, die sie auf ihren Geräten konfiguriert haben.
- **E-Mail-Versand aus Anwendungen von Drittanbietern zulassen**: Durch Festlegung der Option auf **Aktivieren** (Standardeinstellung) können Benutzer dieses Profil als Standardkonto für das Senden von E-Mails verwenden. Dadurch können Anwendungen von Drittanbietern E-Mails in der nativen E-Mail-App öffnen, um beispielsweise Dateien an E-Mails anzuhängen.
- **Kürzlich verwendete E-Mail-Adressen synchronisieren**: Durch Festlegung der Option auf **Aktivieren** (Standardeinstellung) können Benutzer die Liste der vor Kurzem auf dem Gerät verwendeten E-Mail-Adressen mit dem Server synchronisieren.

## <a name="next-steps"></a>Nächste Schritte

Das Profil ist nun erstellt, führt aber noch keine Aktionen durch. Die nächsten Schritte sind das [Zuweisen von Benutzer- und Geräteprofilen in Microsoft Intune](../device-profile-assign.md) und das [Überwachen von Geräteprofilen in Microsoft Intune](../device-profile-monitor.md).

Konfigurieren Sie die E-Mail-Einstellungen für [Android](../email-settings-android.md)-, [Android Enterprise](../email-settings-android-enterprise.md), [Windows 10](email-settings-windows-10.md)- und [Windows Phone 8.1](email-settings-windows-phone-8-1.md)-Geräte.
