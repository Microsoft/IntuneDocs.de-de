---
title: Bei der Entwicklung - Microsoft Intune
titlesuffix: ''
description: Microsoft Intune-Funktionen in der Entwicklung
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/04/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c377a8558b1f318b4ddad735b6368a291e34516
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57756818"
---
# <a name="in-development-for-microsoft-intune---march-2019"></a>Bei der Entwicklung für Microsoft Intune – März 2019

Für Ihre Bereitschaft und planen, diese Seite enthält, die Intune UI aktualisiert und die features dieses Produkts, sind in der Entwicklung, aber noch nicht veröffentlicht wurden. Zusätzlich:

- Wenn wir davon ausgehen, dass Sie eine Aktion vor einer Änderung müssen, veröffentlichen wir kostenloses Office-Nachrichtencenter Post.
- Wenn eine Funktion wird entweder als Vorschau in der Produktion gestartet oder allgemein verfügbar ist, der featurebeschreibung wird verschieben außerhalb dieser Seite und auf die [neuerungen neue Seite](whats-new.md).
- Auf dieser Seite und die [neuerungen neue Seite](whats-new.md) in regelmäßigen Abständen aktualisiert werden. Überprüfen Sie, ob weitere Updates vorliegen.
- Finden Sie in der [M365 Roadmap](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) für strategische lieferleistungen und Zeitpläne.

> [!Note]
> Diese Elemente entsprechen Microsofts aktuelle Erwartungen über Intune-Funktionen, die in einer zukünftigen Version verfügbar. Datums- und einzelne Funktionen möglicherweise ändern. Nicht alle Elemente in der Entwicklung haben eine funktionsbeschreibung auf dieser Seite.

**RSS-Feed**: Lassen Sie sich benachrichtigen, wenn diese Seite aktualisiert wird, indem Sie die folgende URL kopieren und in Ihren Feedreader einfügen: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`.


<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune im Azure-Portal


<!-- 1903 start-->

### <a name="encryption-report-----2351538---"></a>Verschlüsselung-Bericht  <!-- 2351538 -->
Sie müssen einen neuen Bericht für die Verschlüsselung zu verwenden, um Details zu den Verschlüsselungsstatus Ihrer Geräte anzeigen können. Verfügbaren Details enthalten eine Geräte-TPM-Version, Verschlüsselung Bereitschaft und Status, Fehlerberichterstattung und mehr.  

### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-----2351547----"></a>Zugriff auf BitLocker-Wiederherstellungsschlüssel vom Intune-portal  <!-- 2351547  -->
Fügen wir einen neuen Einstiegspunkt auf Geräten, hinzu, in dem Sie Informationen aus Azure Active Directory (AAD) zum BitLocker-Schlüssel-ID und die BitLocker-Wiederherstellungsschlüssel anzeigen können.

### <a name="scope-tags-for-app-configuration-policies---2371891---"></a>Bereichsmarkierungen für app-Konfigurationsrichtlinien <!--2371891 -->
Sie werden eine bereichsmarkierung einer app-Konfigurationsrichtlinie hinzufügen, damit nur Personen mit Rollen, die auch zugewiesen, bereichsmarkierung auf die app-Konfigurationsrichtlinie zugreifen können. Die app-Konfigurationsrichtlinie kann nur speziell für Programmentwickler konzipiert oder apps, die die gleichen bereichsmarkierung zugewiesen zugeordnet sind.

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522---"></a>Zuweisen von Autopilot-Profilen zur virtuellen Gruppe „Alle Geräte“ <!--2715522 -->
Sie können Autopilot-Profile zur virtuellen Gruppe „Alle Geräte“ zuweisen. Wählen Sie dazu **Geräteregistrierung** > **Windows-Registrierung** > **Bereitstellungsprofile** aus. Wählen Sie dann ein Profil > **Zuweisungen** > und unter **Zuweisen zu** wählen Sie **Alle Geräte** aus. Weitere Informationen zu Autopilot-Profilen finden Sie unter [Registrieren von Windows-Geräten mit Windows Autopilot](enrollment-autopilot.md).

### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523----"></a>Installieren Sie verfügbarer apps, die mithilfe der Unternehmensportal-app nach dem Massenimport von Windows-Registrierung <!-- 2751523  -->
Windows-Geräte, die mit Intune registriert [Windows-massenregistrierung](windows-bulk-enroll.md) (Bereitstellung von Paketen) kann die Unternehmensportal-app verwenden, um verfügbare apps zu installieren. Weitere Informationen über die Unternehmensportal-app finden Sie unter [manuell hinzufügen der Unternehmensportal-App für Windows 10](store-apps-company-portal-app.md) und [Vorgehensweise: Konfigurieren von Microsoft Intune-Unternehmensportal-app](company-portal-app.md).

### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430---"></a>Bereichsmarkierungen für iOS-app-bereitstellungsprofile <!--2934430 -->
Sie werden eine bereichsmarkierung ein Bereitstellungsprofil für iOS-app hinzufügen, damit nur Personen mit Rollen, die auch zugewiesen, bereichsmarkierung produktionsbereitstellungsprofil erstellen, die iOS-app zugreifen können. 

### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477----"></a>Office-Bereitstellungstool (ODT) XML für Office ProPlus Bereitstellung <!-- 3192477  -->
Sie müssen Office-Bereitstellungstool (ODT) XML angeben, wenn Sie eine Instanz von Office Professional Plus in der Intune-Verwaltungskonsole erstellen können. Dadurch können mehr anpassbarkeit, wenn die vorhandenen Intune UI-Optionen nicht Ihren Bedürfnissen entsprechen. 

###  <a name="block-users-from-scanning-for-windows-updates-------3316758------"></a>Suche nach Windows Updates den Benutzer blockieren    <!-- 3316758    -->
Wir fügen eine neue Windows-updatering festlegen, dass Sie verwenden können, die Benutzer aus der Suche nach Updates von Windows verhindert. Diese Einstellung nicht in das Portal verfügbar, aber Sie können mithilfe der Graph-API von Intune konfiguriert werden.

### <a name="windows-update-notifications-----3316782---"></a>Windows Update-Benachrichtigungen  <!-- 3316782 -->
Wir fügen Unterstützung an den Windows Update Ring Konfigurationen sodass Sie die Windows Update-Benachrichtigungen konfigurieren, die den Benutzern angezeigt werden können. Diese Einstellung nicht in das Portal verfügbar, aber Sie können mithilfe der Graph-API von Intune konfiguriert werden.

### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>Änderungen an der Unternehmensportal-App-Registrierung für Benutzer von iOS-12-Geräte <!--3448635 -->  
Unternehmensportal-App für iOS wird aktualisiert, die app Registrierung Bildschirme und Schritte zur Angleichung an der MDM-Registrierung Änderungen, die in Apple iOS 12.2 veröffentlicht. Der aktualisierte Workflow wird jetzt auffordern, Benutzer:

- Ermöglichen Sie Safari öffnen Sie die Unternehmensportal-Website (über Safari) und das verwaltungsprofil vor der Rückgabe an den Unternehmensportal-app herunterladen. 
- Öffnen Sie die Einstellungen-app, um das verwaltungsprofil auf seinem Gerät zu installieren.
- Gibt zurück, schließen Sie die Registrierung der Unternehmensportal-app.  

Weitere Informationen dazu, wie Sie diese Änderungen vorbereiten können, finden Sie unter den [Microsoft Tech Community Post](https://techcommunity.microsoft.com/). In der Zwischenzeit um neue Registrierungen für iOS im Unternehmensportal zu unterstützen, wurden aktualisiert die Schritte im [Registrieren von iOS-Geräts bei Intune](https://docs.microsoft.com/en-us/intune/ios-enroll). Diese Docs-Änderungen werden nach der Veröffentlichung des Apple iOS-Version 12.2 live. 

### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202-------"></a>Unterstützung für zusätzliche Connectors auf der Statusseite von Mandanten <!-- 3617202     -->
Der Mandantenstatus wird für die Seitenanzeige Statusinformationen für zusätzliche Connectors, z.B. *Windows Defender Advanced Threat Protection* (ATP) und andere Mobile Threat Defense-Connectors.

### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917---"></a>Intune gewähren schreibgeschützten Zugriff auf einige Azure Active Directory-Rollen <!-- 3637917 -->
Wir werden erteilt werden, dass Intune nur Zugriff auf die folgenden Azure AD-Rollen lesen. Mit Azure AD-Rollen gewährt Berechtigungen Vorrang vor Berechtigungen, die mit Intune rollenbasierte Zugriffssteuerung (RBAC) gewährt.

Lesen Sie nur den Zugriff auf Intune-Überwachungsdaten an:

- Complianceadministrator
- Complianceadministrator-Daten

Schreibgeschützten Zugriff auf alle Intune-Daten:

- Sicherheitsadministrator
- Sicherheits-Operator
- Sicherheitsleseberechtigter
- Globale Reader

### <a name="easier-access-to-diagnostic-settings------3804627-----"></a>Einfacher Zugriff auf die Diagnoseeinstellungen für   <!-- 3804627   -->
Fügen wir eine neue Option zum die **Überwachungsprotokolle** auf dem Blatt jeder in jeder Überwachungsprotokoll arbeitsauslastung in der Intune-Verwaltungskonsole, die Sie verwenden können, um direkt zu öffnen der *Diagnoseeinstellungen* Seite.

### <a name="create-and-use-device-configuration-profiles-on-android-zebra-devices-in-intune----3895244----"></a>Erstellen und Verwenden von Profilen für die Gerätekonfiguration unter Android Zebra-Geräte in Intune <!-- 3895244  -->
Intune unterstützt die Konfiguration von Android Zebra-Geräten. Insbesondere müssen Sie Lage sein: 

- Erstellen ein gerätekonfigurationsprofils aus, und wenden Sie Einstellungen für Android Zebra-Geräte mithilfe von Mobility-Erweiterungen (MX) Profilen, die vom StageNow (**Gerätekonfiguration** > **Profile**  >  **Profil erstellen** > **Android** für Plattform).

Gilt für:  
- Android

<!-- 1901 start -->

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>Bereitstellung von online lizenzierten Apps im Microsoft Store für Unternehmen <!-- 1672660  -->
Sie können die erforderlichen, online lizenzierten Microsoft Store für Unternehmen-Apps im Gerätekontext zuweisen. Wenn Sie eine Microsoft Store für Unternehmen-App auf diese Weise bereitstellen, kann die App für alle Benutzer auf dem Gerät installiert werden. Dies gilt nur für Windows 10 RS4-Desktopgeräte und höher. Die Option zur Installation im Gerätekontext ist auf der Seite für die Zuweisung von Client-Apps für online lizenzierte Microsoft Store für Unternehmen-Apps verfügbar.

## <a name="notices"></a>Benachrichtigungen

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Siehe auch
Details zu aktuellen Entwicklungen finden Sie unter [Neuheiten in Microsoft Intune](whats-new.md).
