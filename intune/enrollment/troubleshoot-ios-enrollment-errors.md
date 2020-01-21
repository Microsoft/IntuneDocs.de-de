---
title: Behandlung von Problemen bei der iOS-Geräteregistrierung in Microsoft Intune
titleSuffix: Microsoft Intune
description: Vorschläge zur Behebung einiger der am häufigsten auftretenden Probleme beim Registrieren von IOS-Geräten in InTune.
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
ms.openlocfilehash: 9bca046302b221b934d0802c0bf637aced2cec3f
ms.sourcegitcommit: 2506cdbfccefd42587a76f14ee50c3849dad1708
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885914"
---
# <a name="troubleshoot-ios-device-enrollment-problems-in-microsoft-intune"></a>Behandlung von Problemen bei der iOS-Geräteregistrierung in Microsoft Intune

In diesem Artikel werden InTune-Administratoren bei der Anmeldung von IOS-Geräten in InTune unterstützt.

## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie mit der Problembehandlung beginnen, ist es wichtig, einige grundlegende Informationen zu sammeln. Diese Informationen können Ihnen helfen, das Problem besser zu verstehen und die Zeit für die Suche nach einer Lösung zu verkürzen.

Sammeln Sie die folgenden Informationen zum Problem:

- Wie lautet die genaue Fehlermeldung?
- Wo wird die Fehlermeldung angezeigt?
- Wann fing das Problem an? Hat die Registrierung jemals funktioniert?
- Welche Plattform (Android, Ios, Windows) hat das Problem?
- Wie viele Benutzer sind betroffen? Sind alle Benutzer betroffen oder nur einige?
- Wie viele Geräte sind betroffen? Sind alle Geräte betroffen oder nur einige?
- Was ist die MDM-Autorität?
- Wie wird die Registrierung durchgeführt? Handelt es sich um ein "Bring your own Device" (BYOD) oder Apple Programm zur Geräteregistrierung (DEP) mit Registrierungs Profilen?

## <a name="error-messages"></a>Fehlermeldungen

### <a name="profile-installation-failed-a-network-error-has-occurred"></a>Fehler bei der Profilinstallation. Ein Netzwerkfehler ist aufgetreten.

**Ursache:** Es gibt ein nicht bestimmtes Problem mit IOS auf dem Gerät.

#### <a name="resolution"></a>Lösung

1. Um Datenverluste in den folgenden Schritten zu vermeiden (durch Wiederherstellen von IOS werden alle Daten auf dem Gerät gelöscht), müssen Sie sicherstellen, dass Sie die Daten sichern.
2. Versetzen Sie das Gerät in den Wiederherstellungs Modus, und Wiederherstellen Sie es. Stellen Sie sicher, dass Sie es als neues Gerät einrichten. Weitere Informationen zum Wiederherstellen von IOS-Geräten finden Sie unter [https://support.apple.com/HT201263](https://support.apple.com/HT201263).
3. Registrieren Sie das Gerät erneut.

### <a name="profile-installation-failed-connection-to-the-server-could-not-be-established"></a>Fehler bei der Profilinstallation. Mit dem Server konnte keine Verbindung hergestellt werden.

**Ursache:** Ihr InTune-Mandant ist so konfiguriert, dass nur unternehmenseigene Geräte zugelassen werden. 

#### <a name="resolution"></a>Lösung
1. Melden Sie sich im Azure-Portal an.
2. Wählen Sie **Weitere Dienste** aus, suchen Sie nach Intune, und wählen Sie dann **Intune** aus.
3. Klicken Sie auf **Geräteregistrierung** > **Registrierungsbeschränkungen**.
4. Wählen Sie unter **Gerätetyp Einschränkungen**die Einschränkung aus, die Sie > **Eigenschaften** festlegen möchten > **Plattformen auswählen** > Wählen Sie für **IOS** **zulassen** aus, und klicken Sie dann auf **OK**.
5. Wählen Sie **Plattformen konfigurieren**aus, wählen Sie für private IOS-Geräte **zulassen** aus, und klicken Sie dann auf **OK**.
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

**Ursache:** Sie registrieren ein Gerät, das zuvor mit einem anderen Benutzerkonto registriert wurde, und der vorherige Benutzer wurde nicht ordnungsgemäß aus InTune entfernt.

#### <a name="resolution"></a>Lösung
1. Alle aktuellen Profile werden abgebrochen.
2. Öffnen Sie [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com) in Safari.
3. Registrieren Sie das Gerät erneut.

> [!NOTE]
> Wenn die Registrierung weiterhin fehlschlägt, entfernen Sie Cookies in Safari (Cookies nicht blockieren), und registrieren Sie das Gerät erneut.

**Ursache:** Das Gerät ist bereits bei einem anderen MDM-Anbieter registriert.

#### <a name="resolution"></a>Lösung
1. Öffnen Sie die **Einstellungen** auf dem IOS-Gerät, und wechseln Sie zu **Allgemein > Geräteverwaltung**.
2. Entfernen Sie alle vorhandenen Verwaltungs Profile.
3. Registrieren Sie das Gerät erneut.

**Ursache:** Der Benutzer, der versucht, das Gerät zu registrieren, verfügt über keine Microsoft InTune Lizenz.

#### <a name="resolution"></a>Lösung
1. Wechseln Sie zum [Office 365 Admin Center](https://portal.office.com/adminportal/home#/homepage), und wählen Sie dann **Benutzer > aktive Benutzer**aus.
2. Wählen Sie das Benutzerkonto aus, dem Sie eine Intune-Benutzerlizenz zuweisen möchten, und klicken Sie dann auf **Produktlizenzen > Bearbeiten**.
3. Wechseln Sie für die Lizenz, die Sie diesem Benutzer zuweisen möchten, zur Position **an** , und wählen Sie dann **Speichern**aus.
4. Registrieren Sie das Gerät erneut.

### <a name="this-service-is-not-supported-no-enrollment-policy"></a>Dieser Dienst wird nicht unterstützt. Keine Registrierungsrichtlinie.

**Ursache**: ein Apple-MDM-Push-Zertifikat ist in InTune nicht konfiguriert, oder das Zertifikat ist ungültig. 

#### <a name="resolution"></a>Lösung

- Wenn das MDM-Push-Zertifikat nicht konfiguriert ist, führen Sie die Schritte unter anfordern [eines Apple-MDM-Push-Zertifikats](apple-mdm-push-certificate-get.md#steps-to-get-your-certificate)aus.
- Wenn das MDM-Push-Zertifikat ungültig ist, führen Sie die Schritte unter [Erneuern des Apple-MDM-Push-Zertifikats](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate)aus.

### <a name="company-portal-temporarily-unavailable-the-company-portal-app-encountered-a-problem-if-the-problem-persists-contact-your-system-administrator"></a>Unternehmensportal vorübergehend nicht verfügbar. Bei der Unternehmensportal-APP ist ein Problem aufgetreten. Wenden Sie sich an Ihren Systemadministrator, falls das Problem weiterhin besteht.

**Ursache:** Die Unternehmensportal APP ist veraltet oder beschädigt.

#### <a name="resolution"></a>Lösung
1. Entfernen Sie die Unternehmensportal-App von dem Gerät.
2. Laden Sie die **Microsoft Intune Unternehmensportal**-App aus dem **App Store** herunter, und installieren Sie diese.
3. Registrieren Sie das Gerät erneut.
 > [!NOTE]
    > Dieser Fehler kann auch auftreten, wenn der Benutzer versucht, mehr Geräte zu registrieren, als die Geräteregistrierung für zulassen konfiguriert ist. Befolgen Sie die Lösungsschritte für die Geräte Abdeckung, die unten **erreicht** sind, wenn diese Schritte das Problem nicht beheben.

### <a name="device-cap-reached"></a>Gerätekapazität erreicht

**Ursache:** Der Benutzer versucht, mehr Geräte als das Registrierungs Limit für Geräte zu registrieren.

#### <a name="resolution"></a>Lösung
1. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431)die Option **Geräte** > **alle Geräte**aus, und überprüfen Sie die Anzahl der Geräte, die der Benutzer registriert hat.
    > [!NOTE]
    > Außerdem sollten Sie den betroffenen Benutzer beim [InTune-Benutzer Portal](https://portal.manage.microsoft.com/) anmelden und Geräte überprüfen, die registriert wurden. Möglicherweise befinden sich Geräte, die im [InTune-Benutzer Portal](https://portal.manage.microsoft.com/) angezeigt werden, aber nicht im [InTune-Verwaltungs Portal](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview). diese Geräte zählen auch zu dem Grenzwert für die Geräteregistrierung.
2. Wählen Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431)die Option **Geräte** > Registrierungs **Beschränkungen** > Überprüfen Sie den Grenzwert für die Geräteregistrierung. Der Grenzwert ist standardmäßig auf 15 festgelegt. 
3. Wenn die Anzahl der registrierten Geräte den Grenzwert erreicht hat, entfernen Sie unnötige Geräte, oder erhöhen Sie den Grenzwert für die Geräteregistrierung. Da jedes registrierte Gerät eine InTune-Lizenz beansprucht, empfiehlt es sich, dass Sie immer unnötige Geräte zuerst entfernen.
4. Registrieren Sie das Gerät erneut.

### <a name="workplace-join-failed"></a>Workplace Join fehlgeschlagen

**Ursache:** Die Unternehmensportal APP ist veraltet oder beschädigt.  

#### <a name="resolution"></a>Lösung
1. Entfernen Sie die Unternehmensportal-App von dem Gerät.
2. Laden Sie die **Microsoft Intune Unternehmensportal**-App aus dem **App Store** herunter, und installieren Sie diese.
3. Registrieren Sie das Gerät erneut.

### <a name="user-license-type-invalid"></a>Ungültiger Benutzer Lizenztyp.

**Ursache:** Der Benutzer, der versucht, das Gerät zu registrieren, verfügt über keine gültige InTune-Lizenz.

#### <a name="resolution"></a>Lösung
1. Wechseln Sie zum [Microsoft 365 Admin Center](https://portal.office.com/adminportal/home#/homepage), und wählen Sie dann **Benutzer** > **aktive Benutzer**aus.
2. Wählen Sie das betroffene Benutzerkonto aus, > **Produktlizenzen** > **Bearbeiten**.
3. Überprüfen Sie, ob diesem Benutzer eine gültige InTune-Lizenz zugewiesen ist.
4. Registrieren Sie das Gerät erneut.

### <a name="user-name-not-recognized-this-user-account-is-not-authorized-to-use-microsoft-intune-contact-your-system-administrator-if-you-think-you-have-received-this-message-in-error"></a>Benutzername nicht erkannt. Dieses Benutzerkonto ist nicht für die Verwendung von Microsoft InTune autorisiert. Wenden Sie sich an den Systemadministrator, wenn Sie der Ansicht sind, dass Sie diese Meldung fehlerhaft erhalten haben

**Ursache:** Der Benutzer, der versucht, das Gerät zu registrieren, verfügt über keine gültige InTune-Lizenz.

1. Wechseln Sie zum [Microsoft 365 Admin Center](https://portal.office.com/adminportal/home#/homepage), und wählen Sie dann **Benutzer** > **aktive Benutzer**aus.
2. Wählen Sie das betroffene Benutzerkonto aus, und wählen Sie dann **Product licenses** > **Edit**aus.
3. Überprüfen Sie, ob diesem Benutzer eine gültige InTune-Lizenz zugewiesen ist.
4. Registrieren Sie das Gerät erneut.

### <a name="profile-installation-failed-the-new-mdm-payload-does-not-match-the-old-payload"></a>Fehler bei der Profilinstallation. Die neue MDM-Nutzlast stimmt nicht mit der alten Nutzlast überein.

**Ursache:** Ein Verwaltungs Profil ist bereits auf dem Gerät installiert.

#### <a name="resolution"></a>Lösung

1. Öffnen Sie die **Einstellungen** auf dem IOS-Gerät > **Allgemeine** > **Geräteverwaltung**.
2. Tippen Sie auf das vorhandene Verwaltungs Profil, und tippen Sie auf **Verwaltung entfernen**.
3. Registrieren Sie das Gerät erneut.

### <a name="noenrollmentpolicy"></a>NoEnrollmentPolicy

**Ursache:** Das APNs-Zertifikat (Apple Push Notification Service) fehlt, ist ungültig oder abgelaufen.

#### <a name="resolution"></a>Lösung
Überprüfen Sie, ob InTune ein gültiges APNs-Zertifikat hinzugefügt wurde. Weitere Informationen finden Sie unter [Einrichten der IOS](ios-enroll.md)-Registrierung.

### <a name="accountnotonboarded"></a>AccountNotOnboarded

**Ursache:** Es liegt ein Problem mit dem APNs-Zertifikat (Apple Push Notification Service) vor, das in InTune konfiguriert wurde.

#### <a name="resolution"></a>Lösung
Erneuern Sie das APNs-Zertifikat, und registrieren Sie das Gerät erneut.

> [!IMPORTANT]
> Stellen Sie sicher, dass Sie das APNs-Zertifikat erneuern. Ersetzen Sie das APNs-Zertifikat nicht. Wenn Sie das Zertifikat ersetzen, müssen Sie alle IOS-Geräte in InTune erneut registrieren. 

- Informationen zum Erneuern des APNs-Zertifikats in InTune Standalone finden Sie unter [Erneuern des Apple-MDM-Push-Zertifikats](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate).
- Informationen zum Erneuern des APNs-Zertifikats in Office 365 finden Sie unter [Erstellen eines APNs-Zertifikats für IOS-Geräte](https://support.office.com/article/Create-an-APNs-Certificate-for-iOS-devices-522b43f4-a2ff-46f6-962a-dd4f47e546a7).

### <a name="xpc_type_error-connection-invalid"></a>XPC_TYPE_ERROR Verbindung ist ungültig.

Wenn Sie ein DEP-verwaltetes Gerät einschalten, dem ein Anmeldungs Profil zugewiesen ist, tritt bei der Registrierung ein Fehler auf, und Sie erhalten die folgende Fehlermeldung:

```
asciidoc
mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" } }
iPhone mobileassetd[83] <Notice>: Client connection invalid (Connection invalid); terminating connection
iPhone com.apple.accessibility.AccessibilityUIServer(MobileAsset)[288] <Notice>: [MobileAssetError:29] Unable to copy asset information from https://mesu.apple.com/assets/ for asset type com.apple.MobileAsset.VoiceServices.CombinedVocalizerVoices
iPhone mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" }
```

**Ursache:** Zwischen dem Gerät und dem Apple-DEP-Dienst besteht ein Verbindungsproblem.

#### <a name="resolution"></a>Lösung
Beheben Sie das Verbindungsproblem, oder verwenden Sie eine andere Netzwerkverbindung, um das Gerät zu registrieren. Wenn das Problem weiterhin besteht, müssen Sie sich möglicherweise auch an Apple wenden.


## <a name="other-issues"></a>Andere Probleme

### <a name="dep-enrollment-doesnt-start"></a>DEP-Registrierung wird nicht gestartet.
Wenn Sie ein DEP-verwaltetes Gerät einschalten, dem ein Registrierungs Profil zugewiesen ist, wird der InTune-Registrierungsprozess nicht initiiert.

**Ursache:** Das Registrierungs Profil wird erstellt, bevor das DEP-Token in InTune hochgeladen wird.

#### <a name="resolution"></a>Lösung

1. Bearbeiten Sie das Registrierungs Profil. Sie können Änderungen am Profil vornehmen. Der Zweck besteht darin, die Änderungszeit des Profils zu aktualisieren.
2. Synchronisieren von DEP-verwalteten Geräten: Klicken Sie im [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431) auf **Geräte** > **iOS** > **iOS-Registrierung** > **Registrierungsprogrammtoken** > wählen Sie ein Token aus > **Jetzt synchronisieren**. Eine Synchronisierungsanforderung wird an Apple gesendet.

### <a name="dep-enrollment-stuck-at-user-login"></a>DEP-Registrierung bei Benutzeranmeldung hängen
Wenn Sie ein DEP-verwaltetes Gerät einschalten, dem ein Registrierungs Profil zugewiesen ist, wird das erste Setup nach der Eingabe der Anmelde Informationen geklemmt.

**Ursache:** Die mehrstufige Authentifizierung (Multi-Factor Authentication, MFA) ist aktiviert. MFA funktioniert derzeit nicht während der Registrierung auf DEP-Geräten.

#### <a name="resolution"></a>Lösung
Deaktivieren Sie die MFA, und registrieren Sie das Gerät erneut.

## <a name="next-steps"></a>Nächste Schritte

- [Behandlung von Problemen bei der Geräteregistrierung bei Intune](../troubleshoot-device-enrollment-in-intune.md)
- [Stellen Sie eine Frage im Intune-Forum](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Lesen Sie den Blog des Microsoft Intune-Supportteams.](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Lesen Sie den Blog zu Microsoft Enterprise Mobility + Security.](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
