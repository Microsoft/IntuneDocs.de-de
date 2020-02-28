---
title: Behandlung von Problemen bei der iOS/iPadOS-Geräteregistrierung in Microsoft Intune
titleSuffix: Microsoft Intune
description: Vorschläge zur Behandlung einiger der häufigsten Probleme beim Registrieren von iOS/iPadOS-Geräten in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/18/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a29fab4be6e2046b2c6757505001a7ba3455b8d6
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514318"
---
# <a name="troubleshoot-iosipados-device-enrollment-problems-in-microsoft-intune"></a>Behandeln von Problemen bei der iOS/iPadOS-Geräteregistrierung in Microsoft Intune

Dieser Artikel bietet Intune-Administratoren Unterstützung bei der Diagnose und Behandlung von Problemen bei der Registrierung von iOS/iPadOS-Geräten in Intune.

## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie mit der Problembehandlung beginnen, ist es wichtig, einige grundlegende Informationen zu sammeln. Diese Informationen können Ihnen helfen, das Problem besser zu verstehen und die Zeit für die Suche nach einer Lösung zu verkürzen.

Sammeln Sie die folgenden Informationen zum Problem:

- Wie lautet die genaue Fehlermeldung?
- Wo wird die Fehlermeldung angezeigt?
- Wann fing das Problem an? Hat die Registrierung jemals funktioniert?
- Auf welcher Plattform (Android, iOS/iPadOS, Windows) tritt das Problem auf?
- Wie viele Benutzer sind betroffen? Sind alle oder nur einige Benutzer betroffen?
- Wie viele Geräte sind betroffen? Sind alle oder nur einige Geräte betroffen?
- Welche MDM-Autorität wird verwendet?
- Wie wird die Registrierung durchgeführt? Wird BYOD (Bring Your Own Device) oder das Apple-Programm zur Geräteregistrierung (DEP) mit Registrierungsprofilen verwendet?

## <a name="error-messages"></a>Fehlermeldungen

### <a name="profile-installation-failed-a-network-error-has-occurred"></a>Fehler bei der Profilinstallation. Ein Netzwerkfehler ist aufgetreten.

**Ursache:** Es liegt ein nicht spezifiziertes Problem mit iOS/iPadOS auf dem Gerät vor.

#### <a name="resolution"></a>Lösung

1. Um einen Datenverlust in den folgenden Schritten zu verhindern (bei der Wiederherstellung von iOS/iPadOS werden alle Daten auf dem Gerät gelöscht), müssen Sie Ihre Daten sichern.
2. Versetzen Sie das Gerät in den Wiederherstellungsmodus, und stellen Sie es dann wieder her. Stellen Sie sicher, dass Sie es als neues Gerät einrichten. Weitere Informationen zum Wiederherstellen von iOS/iPadOS-Geräten finden Sie unter [https://support.apple.com/HT201263](https://support.apple.com/HT201263).
3. Registrieren Sie das Gerät erneut.

### <a name="profile-installation-failed-connection-to-the-server-could-not-be-established"></a>Fehler bei der Profilinstallation. Mit dem Server konnte keine Verbindung hergestellt werden.

**Ursache:** Ihr Intune-Mandant ist so konfiguriert, dass nur unternehmenseigene Geräte zugelassen werden. 

#### <a name="resolution"></a>Lösung
1. Melden Sie sich im Azure-Portal an.
2. Wählen Sie **Weitere Dienste** aus, suchen Sie nach Intune, und wählen Sie dann **Intune** aus.
3. Klicken Sie auf **Geräteregistrierung** > **Registrierungsbeschränkungen**.
4. Wählen Sie unter **Gerätetypbeschränkungen** die Beschränkung aus, die Sie festlegen möchten. Klicken Sie dann auf **Eigenschaften** > **Plattformen auswählen**, wählen Sie **Zulassen** für **iOS** aus, und klicken Sie dann auf **OK**.
5. Klicken Sie auf **Plattformen konfigurieren**, wählen Sie **Zulassen** für private iOS/iPadOS-Geräte aus, und klicken Sie dann auf **OK**.
6. Registrieren Sie das Gerät erneut.

**Ursache:** Die erforderlichen CNAME-Einträge in DNS sind nicht vorhanden.

#### <a name="resolution"></a>Lösung
Erstellen Sie CNAME DNS-Ressourceneinträge für die Domäne des Unternehmens. Wenn die Domäne Ihres Unternehmens beispielsweise contoso.com heißt, erstellen Sie in DNS einen CNAME-Eintrag, der EnterpriseEnrollment.contoso.com an EnterpriseEnrollment-s.manage.microsoft.com umleitet.

Obwohl das Erstellen eines CNAME-DNS-Eintrags optional ist, ist die Registrierung mit einem CNAME-Eintrag für den Benutzer leichter. Wenn kein CNAME-Eintrag für die Registrierung gefunden wurde, werden Benutzer aufgefordert, manuell den MDM-Servernamen „enrollment.manage.microsoft.com“ einzugeben.

Sind mehrere überprüfte Domänen vorhanden, erstellen Sie einen CNAME-Eintrag für jede Domäne. Die CNAME-Ressourceneinträge müssen die folgenden Informationen enthalten:

|TYP|Hostname|Verweist auf|TTL|
|------|------|------|------|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com|1 Stunde|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 Stunde|

Wenn Ihr Unternehmen mehrere Domänen für die Anmeldeinformationen der Benutzer verwendet, erstellen Sie CNAME-Einträge für jede Domäne.

> [!NOTE]
> Die Weitergabe von Änderungen an DNS-Einträgen kann bis zu 72 Stunden dauern. Sie können die DNS-Änderung in Intune erst überprüfen, wenn der DNS-Eintrag verteilt ist.

**Ursache:** Sie registrieren ein Gerät, das zuvor mit einem anderen Benutzerkonto registriert wurde, und der vorherige Benutzer wurde nicht ordnungsgemäß aus Intune entfernt.

#### <a name="resolution"></a>Lösung
1. Brechen Sie alle aktuellen Profilinstallationen ab.
2. Öffnen Sie [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com) in Safari.
3. Registrieren Sie das Gerät erneut.

> [!NOTE]
> Wenn die Registrierung weiterhin fehlschlägt, entfernen Sie Cookies in Safari (Cookies nicht blockieren), und registrieren Sie das Gerät erneut.

**Ursache:** Das Gerät ist bereits mit einem anderen MDM-Anbieter registriert.

#### <a name="resolution"></a>Lösung
1. Öffnen Sie auf dem iOS/iPadOS-Gerät **Einstellungen**, und wechseln Sie zu **Allgemein > Geräteverwaltung**.
2. Entfernen Sie alle vorhandenen Verwaltungsprofile.
3. Registrieren Sie das Gerät erneut.

**Ursache:** Der Benutzer, der das Gerät registrieren möchte, besitzt keine Microsoft Intune-Lizenz.

#### <a name="resolution"></a>Lösung
1. Wechseln Sie zum [Office 365 Admin Center](https://portal.office.com/adminportal/home#/homepage), und wählen Sie dann **Benutzer > Aktive Benutzer** aus.
2. Wählen Sie das Benutzerkonto aus, dem Sie eine Intune-Benutzerlizenz zuweisen möchten, und klicken Sie dann auf **Produktlizenzen > Bearbeiten**.
3. Legen Sie den Umschalter für die dem Benutzer zuzuweisende Lizenz auf **Ein** fest, und klicken Sie dann auf **Speichern**.
4. Registrieren Sie das Gerät erneut.

### <a name="this-service-is-not-supported-no-enrollment-policy"></a>Dieser Dienst wird nicht unterstützt. Keine Registrierungsrichtlinie.

**Ursache**: In Intune ist kein Apple-MDM-Push-Zertifikat konfiguriert, oder das Zertifikat ist ungültig. 

#### <a name="resolution"></a>Lösung

- Wenn das MDM-Push-Zertifikat nicht konfiguriert ist, führen Sie die Schritte unter [Anfordern eines Apple-MDM-Push-Zertifikats](apple-mdm-push-certificate-get.md#steps-to-get-your-certificate) aus.
- Wenn das MDM-Push-Zertifikat ungültig ist, führen Sie die Schritte unter [Erneuern des Apple-MDM-Push-Zertifikats](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate) aus.

### <a name="company-portal-temporarily-unavailable-the-company-portal-app-encountered-a-problem-if-the-problem-persists-contact-your-system-administrator"></a>Unternehmensportal vorübergehend nicht verfügbar. Bei der Unternehmensportal-App ist ein Problem aufgetreten. Wenden Sie sich an Ihren Systemadministrator, falls das Problem weiterhin besteht.

**Ursache:** Die Unternehmensportal-App ist veraltet oder beschädigt.

#### <a name="resolution"></a>Lösung
1. Entfernen Sie die Unternehmensportal-App von dem Gerät.
2. Laden Sie die **Microsoft Intune Unternehmensportal**-App aus dem **App Store** herunter, und installieren Sie diese.
3. Registrieren Sie das Gerät erneut.
 > [!NOTE]
    > Dieser Fehler kann auch auftreten, wenn der Benutzer versucht, mehr Geräte zu registrieren, als für die Geräteregistrierung zugelassen ist. Befolgen Sie die Lösungsschritte im nachstehenden Abschnitt **Gerätekapazität erreicht**, wenn das Problem so nicht gelöst werden kann.

### <a name="device-cap-reached"></a>Gerätekapazität erreicht

**Ursache:** Der Benutzer versucht, mehr Geräte zu registrieren, als im Limit für die Geräteregistrierung angegeben wurden.

#### <a name="resolution"></a>Lösung
1. Klicken Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) auf **Geräte** > **Alle Geräte**, und überprüfen Sie, wie viele Geräte der Benutzer registriert hat.
    > [!NOTE]
    > Weisen Sie den betroffenen Benutzer außerdem an, sich beim [Intune-Benutzerportal](https://portal.manage.microsoft.com/) anzumelden und die registrierten Geräte zu überprüfen. Es kann Geräte geben, die zwar im [Intune-Benutzerportal](https://portal.manage.microsoft.com/), nicht aber im [Intune-Verwaltungsportal](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview) angezeigt werden. Solche Geräte werden ebenfalls auf das Limit für die Geräteregistrierung angerechnet.
2. Klicken Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) auf **Geräte** > **Registrierungsbeschränkungen**, und überprüfen Sie das Limit für die Geräteregistrierung. Der Grenzwert ist standardmäßig auf 15 festgelegt. 
3. Wenn das Limit für die Geräteregistrierung erreicht wurde, entfernen Sie nicht benötigte Geräte, oder erhöhen Sie das Limit für die Geräteregistrierung. Da jedes registrierte Gerät eine Intune-Lizenz beansprucht, empfiehlt es sich, zunächst immer alle nicht benötigten Geräte zu entfernen.
4. Registrieren Sie das Gerät erneut.

### <a name="workplace-join-failed"></a>Workplace Join-Fehler

**Ursache:** Die Unternehmensportal-App ist veraltet oder beschädigt.  

#### <a name="resolution"></a>Lösung
1. Entfernen Sie die Unternehmensportal-App von dem Gerät.
2. Laden Sie die **Microsoft Intune Unternehmensportal**-App aus dem **App Store** herunter, und installieren Sie diese.
3. Registrieren Sie das Gerät erneut.

### <a name="user-license-type-invalid"></a>Ungültiger Benutzerlizenztyp

**Ursache:** Der Benutzer, der das Gerät registrieren möchte, besitzt keine gültige Intune-Lizenz.

#### <a name="resolution"></a>Lösung
1. Wechseln Sie zum [Microsoft 365 Admin Center](https://portal.office.com/adminportal/home#/homepage), und klicken Sie auf **Benutzer** > **Aktive Benutzer**.
2. Wählen Sie das betroffene Benutzerkonto aus, und klicken Sie auf **Produktlizenzen** > **Bearbeiten**.
3. Überprüfen Sie, ob diesem Benutzer eine gültige Intune-Lizenz zugewiesen ist.
4. Registrieren Sie das Gerät erneut.

### <a name="user-name-not-recognized-this-user-account-is-not-authorized-to-use-microsoft-intune-contact-your-system-administrator-if-you-think-you-have-received-this-message-in-error"></a>Benutzername nicht erkannt. Dieses Benutzerkonto ist nicht zur Verwendung von Microsoft Intune autorisiert. Wenden Sie sich an den Systemadministrator, wenn Sie der Ansicht sind, dass Sie diese Meldung fälschlicherweise erhalten haben.

**Ursache:** Der Benutzer, der das Gerät registrieren möchte, besitzt keine gültige Intune-Lizenz.

1. Wechseln Sie zum [Microsoft 365 Admin Center](https://portal.office.com/adminportal/home#/homepage), und klicken Sie auf **Benutzer** > **Aktive Benutzer**.
2. Wählen Sie das betroffene Benutzerkonto aus, und klicken Sie dann auf **Produktlizenzen** > **Bearbeiten**.
3. Überprüfen Sie, ob diesem Benutzer eine gültige Intune-Lizenz zugewiesen ist.
4. Registrieren Sie das Gerät erneut.

### <a name="profile-installation-failed-the-new-mdm-payload-does-not-match-the-old-payload"></a>Fehler bei der Profilinstallation. Die neue MDM-Nutzlast stimmt nicht mit der alten Nutzlast überein.

**Ursache:** Auf dem Geräte ist bereits ein Verwaltungsprofil installiert.

#### <a name="resolution"></a>Lösung

1. Öffnen Sie auf dem iOS/iPadOS-Gerät **Einstellungen**, und wechseln Sie zu **Allgemein** > **Geräteverwaltung**.
2. Tippen Sie auf das vorhandene Verwaltungsprofil und anschließend auf **Verwaltung entfernen**.
3. Registrieren Sie das Gerät erneut.

### <a name="noenrollmentpolicy"></a>NoEnrollmentPolicy

**Ursache:** Das APNs-Zertifikat (Apple Push Notification Service) fehlt, ist ungültig oder abgelaufen.

#### <a name="resolution"></a>Lösung
Überprüfen Sie, ob Intune ein gültiges APNs-Zertifikat hinzugefügt wurde. Weitere Informationen finden Sie unter [Einrichten der iOS/iPadOS-Registrierung](ios-enroll.md).

### <a name="accountnotonboarded"></a>AccountNotOnboarded

**Ursache:** Es liegt ein Problem mit dem APNs-Zertifikat (Apple Push Notification Service) vor, das in Intune konfiguriert wurde.

#### <a name="resolution"></a>Lösung
Erneuern Sie das APNs-Zertifikat, und registrieren Sie das Gerät erneut.

> [!IMPORTANT]
> Stellen Sie sicher, dass Sie das APNs-Zertifikat erneuern. Ersetzen Sie das APNs-Zertifikat nicht. Wenn Sie das Zertifikat ersetzen, müssen Sie alle iOS/iPadOS-Geräte erneut in Intune registrieren. 

- Informationen zum Erneuern des APNs-Zertifikats in einer eigenständigen Intune-Instanz finden Sie unter [Erneuern des Apple-MDM-Push-Zertifikats](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate).
- Informationen zum Erneuern des APNs-Zertifikats in Office 365 finden Sie unter [Erstellen eines APNs-Zertifikats für iOS/iPadOS-Geräte](https://support.office.com/article/Create-an-APNs-Certificate-for-iOS-devices-522b43f4-a2ff-46f6-962a-dd4f47e546a7).

### <a name="xpc_type_error-connection-invalid"></a>Ungültige XPC_TYPE_ERROR-Verbindung

Wenn Sie ein DEP-verwaltetes Gerät einschalten, dem ein Registrierungsprofil zugewiesen ist, tritt bei der Registrierung ein Fehler auf, und Sie erhalten die folgende Fehlermeldung:

```
asciidoc
mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" } }
iPhone mobileassetd[83] <Notice>: Client connection invalid (Connection invalid); terminating connection
iPhone com.apple.accessibility.AccessibilityUIServer(MobileAsset)[288] <Notice>: [MobileAssetError:29] Unable to copy asset information from https://mesu.apple.com/assets/ for asset type com.apple.MobileAsset.VoiceServices.CombinedVocalizerVoices
iPhone mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" }
```

**Ursache:** Zwischen dem Gerät und dem Apple-DEP-Dienst besteht ein Verbindungsproblem.

#### <a name="resolution"></a>Lösung
Beheben Sie das Verbindungsproblem, oder verwenden Sie eine andere Netzwerkverbindung, um das Gerät zu registrieren. Falls das Problem weiterhin besteht, müssen Sie sich möglicherweise auch an Apple wenden.


## <a name="other-issues"></a>Andere Probleme

### <a name="dep-enrollment-doesnt-start"></a>DEP-Registrierung wird nicht gestartet
Wenn Sie ein DEP-verwaltetes Gerät einschalten, dem ein Registrierungsprofil zugewiesen ist, wird der Vorgang zur Intune-Registrierung nicht eingeleitet.

**Ursache:** Das Registrierungsprofil wird erstellt, bevor das DEP-Token in Intune hochgeladen wird.

#### <a name="resolution"></a>Lösung

1. Bearbeiten Sie das Registrierungsprofil. Sie können Änderungen am Profil vornehmen. Der Zweck besteht darin, die Änderungszeit des Profils zu aktualisieren.
2. Synchronisieren von DEP-verwalteten Geräten: Klicken Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) auf **Geräte** > **iOS** > **iOS-Registrierung** > **Registrierungsprogrammtoken** > wählen Sie ein Token aus > **Jetzt synchronisieren**. Eine Synchronisierungsanforderung wird an Apple gesendet.

### <a name="dep-enrollment-stuck-at-user-login"></a>DEP-Registrierung bleibt bei Benutzeranmeldung stehen
Wenn Sie ein DEP-verwaltetes Gerät einschalten, dem ein Registrierungsprofil zugewiesen ist, wird die erste Einrichtung nach Eingabe der Anmeldeinformationen nicht fortgesetzt.

**Ursache:** Die mehrstufige Authentifizierung (Multi-Factor Authentication, MFA) ist aktiviert. Die mehrstufige Authentifizierung wird während der Registrierung auf DEP-Geräten aktuell nicht unterstützt.

#### <a name="resolution"></a>Lösung
Deaktivieren Sie die mehrstufige Authentifizierung, und registrieren Sie das Gerät erneut.


## <a name="next-steps"></a>Nächste Schritte

- [Behandlung von Problemen bei der Geräteregistrierung bei Intune](../troubleshoot-device-enrollment-in-intune.md)
- [Stellen Sie eine Frage im Intune-Forum](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Lesen Sie den Blog des Microsoft Intune-Supportteams.](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Lesen Sie den Blog zu Microsoft Enterprise Mobility + Security.](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
